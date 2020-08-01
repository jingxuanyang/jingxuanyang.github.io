---
layout: post
title:  "VB源代码|PDF转高清PNG"
date:   2020-02-09
categories: vb-sourcecode
tags: vb-sourcecode pdf2png high-resulotion
author: Jingxuan Yang
---

* content
{:toc}

## 引言

昨天发布PDF转SVG、PNG、Word等格式的Java源代码，[文章见这里](https://mp.weixin.qq.com/s/WKqohl0WpDhoHO821lxuww)。有位读者留言说PDF转PNG用PhotoShop画质更高，这是当然的，我曾经也使用过PS将PDF的每一页都转换为PNG图片，但是只能手动一张一张的转换。

PS低级自动化可以录制动作，然后将重复性的操作交给软件，但是录制动作的方法在这里似乎并不适用。PS的高级自动化可以调用PS提供的API编写JavaScript或VBScript脚本，遂前往Adobe官网

>https://www.adobe.com/devnet/photoshop/scripting.html

下载脚本手册。我打算使用Visual Studio进行VB编程，故下载了以下两个文件

- photoshop-cc-scripting-guide-2019
- photoshop-cc-vbs-ref-2019

第一个是脚本手册，第二个是VBScript的类参考手册。大体上研读一遍这两本手册，只看我需要用到的部分，便可以开工敲代码了。






## VB图形界面设计

图形界面的说明部分需包含程序名称，程序简介，作者、版本以及使用方法等。输入参数包含PS读取PDF使用的分辨率ppi值与导出PNG文件时的压缩值（0到9的整数），默认设置分别为300与3。据导出结果观察，此配置导出速度较快且画质很高，基本可以满足一般需求。最后还需要添加一个触发转换动作的按钮，整体UI设计如下图。嗯，我知道它并不漂亮，但是它很实用呀！


![](https://imgkr.cn-bj.ufileos.com/b4d4c9fc-ab42-41b9-8b29-b88db4c26203.png)



## VB代码编写

第一次写VB代码，边写边搜索各种变量的定义方法、各种对象都有哪些内置方法可以调用，发现这些方法与其他语言还是有一些区别的，比如Java里有一些很方便的方法在VB里就没有，但通过几个方法的组合还是可以实现所需功能的。废话不多说，直接上代码，编写不规范之处还请读者指正！

```vbnet
Public Class Form1

    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles psLayer.Click

        ' open ps
        Dim appRef
        appRef = CreateObject("Photoshop.Application")

        'Remember unit settings and set to values expected by this script
        Dim originalRulerUnits
        originalRulerUnits = appRef.Preferences.RulerUnits
        appRef.Preferences.RulerUnits = 1 'value of 1 = psPixels

        ' close present open files
        Do While appRef.Documents.Count
            appRef.ActiveDocument.Close(2)
        Loop

        ' obtain the file location
        Dim docNameRef
        Dim index
        Dim docPathRef
        docNameRef = appRef.OpenDialog()        
        index = InStrRev(docNameRef(0), "\")
        docPathRef = Microsoft.VisualBasic.Left(docNameRef(0), index)

        ' set options when openning the pdf document
        Dim pdfOpenOptionsRef
        pdfOpenOptionsRef = CreateObject("Photoshop.PDFOpenOptions")
        pdfOpenOptionsRef.AntiAlias = True
        pdfOpenOptionsRef.CropPage = 1
        pdfOpenOptionsRef.Mode = 2 ' psOpenRGB
        pdfOpenOptionsRef.Resolution = Int(TextBoxPPI.Text)
        pdfOpenOptionsRef.SuppressWarnings = True

        ' read pdf pages one by one
        Dim check = True
        Dim page = 1

        Do While check
            Try
                pdfOpenOptionsRef.Page = page
                appRef.Open(docNameRef(0), pdfOpenOptionsRef)
                page = page + 1
            Catch ex As Exception
                check = False
            End Try
        Loop

        ' set png saving options
        Dim pngSaveOptions = CreateObject("Photoshop.PNGSaveOptions")

        pngSaveOptions.Compression = Int(TextBoxCompression.Text)

        ' save pdf as individual png
        Do While appRef.Documents.Count
            Dim savePath = docPathRef & appRef.ActiveDocument.Name
            savePath = Microsoft.VisualBasic.Left(savePath, Len(savePath) - 4)
            appRef.ActiveDocument.SaveAs(savePath, pngSaveOptions, True, 2)
            appRef.ActiveDocument.Close(2)
        Loop

        'Restore unit setting
        appRef.Preferences.RulerUnits = originalRulerUnits

    End Sub

End Class

```

## 运行示例

运行程序，点击“Convert”，程序会自动唤起PhotoShop软件，并打开选择文件对话框，

![](https://imgkr.cn-bj.ufileos.com/3cf6da88-2d66-4bce-ac21-a60e7dfe6ba4.png)

选择需要转换为PDF文件，点击确定，程序自动将该PDF文件导入PS，而后会出现选择PDF文件的对话框，这个小bug还没有解决，直接关闭即可。

![](https://imgkr.cn-bj.ufileos.com/535bfedb-acac-49f7-a30d-c8add4594fa9.png)

而后程序自动将每一页PDF转化为PNG文件，并关闭打开的PDF文件，这些PNG文件保存在与PDF文件相同路径的文件夹内。截取一张转换后的PNG图片作为示例，希望微信不要压缩画质~~
![](https://imgkr.cn-bj.ufileos.com/ff132696-647b-46a6-81d0-81b4a4ba7f4e.png)

## 程序发布

考虑到大部分读者可能并没有VB的编译环境，将本项目发布为可执行程序，现已上传到百度网盘，链接如下

> https://pan.baidu.com/s/1sLwHuLNuHqX_vkpgIAJcVg 

提取码

> m02y

该文件夹包含两个文件

- PhotoShopOperation.exe
- setup.exe

可以直接运行第一个程序，也可运行第二个安装程序将程序安装到电脑里，再运行。有两点需要额外说明

- 本程序是在.net 4.0版本中构建的，如果电脑里没有这个版本的.net框架则可能无法运行程序（我也没试过）
- 安装的PS不能是特别精简的绿色破解版，这种版本一般都会丢失一些功能，可能会导致本程序无法通过com接口调用PS

## 后记

读者一个评论就又干了一天，PDF文件的格式转换问题总算有了一个比较满意的结果。大道至简，Happy Programing!

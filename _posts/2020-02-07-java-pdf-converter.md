---
layout: post
title:  "Java源代码|PDF格式转换"
date:   2020-02-07
categories: java-sourcecode
tags: java-sourcecode pdf-converter
author: Jingxuan Yang
---

* content
{:toc}

## 引言

最近在github上看到有项目把 $\LaTeX{}$ 生成的PDF文件转换为SVG文件，然后将这些SVG文件嵌入一个个网页，就这样一个 $\LaTeX{}$ 说明文档的网站就做好了。将PDF文件转换为位图总会失真，但SVG文件是矢量格式的图片，可以放大很多倍观看，遂萌生了将PDF文件转换为SVG文件的想法。网络上大多数PDF转换软件或在线转换网站要么不支持要么限制页数、有水印，看到有博客介绍可以用Java编程实现，便着手准备开干！







## Java简介

Java是由Sun Microsystems公司于1995年5月推出的Java面向对象程序设计语言和Java平台的总称，由James Gosling和同事们共同研发，并在1995年正式推出。

Java分为三个体系：

- JavaSE (J2SE)：Java 2 Platform Standard Edition，Java平台标准版
- JavaEE (J2EE)：Java 2 Platform Enterprise Edition，Java平台企业版
- JavaME (J2ME)：Java 2 Platform Micro Edition，Java平台微型版

Java需要运行在JVM虚拟机上，这里涉及到三个概念

- JVM：Java Virtual Machine，Java虚拟机，它是整个java实现跨平台的最核心的部分，所有的java程序会首先被编译为`.class`的类文件，这种类文件可以在虚拟机上执行，也就是说class并不直接与机器的操作系统相对应，而是经过虚拟机间接与操作系统交互，由虚拟机将程序解释给本地系统执行。JVM的主要工作是解释自己的指令集（即字节码）到CPU的指令集或对应的系统调用，保护用户免被恶意程序骚扰。
- JRE：Java Runtime Environment，Java运行环境。光有JVM还不能让class文件执行，因为在解释class的时候JVM需要调用解释所需要的类库lib，可以认为 JRE = JVM + 类库。
- JDK：Java Development Kit，Java开发工具包，包含JRE和其他开发Java程序所需的文件。JDK下载之后，包含四个文件夹：bin、include、lib、jre，
  - bin，包含很多程序，最主要的是 `javac.exe` 与 `java.exe`，前者负责编译`.java`源代码生成`.class`文件，后者运行`.class`文件。
  - include，包含Java和JVM交互用的头文件
  - lib，类库，其他人写好的可以直接调用的jar程序包
  - jre，Java运行环境


## Java安装与配置

在windows 10平台进行Java JDK下载安装，首先前往官网

>https://www.oracle.com/technetwork/java/javase/downloads/index.html

下载Java JDK，建议下载8u241版本或者其他JDK 8的版本，JDK 8是目前本地开发和生产环境中使用最多的Java JDK版本。

安装完成后设置环境变量

1. JAVA_HOME
>C:\ProgramFile\Java\jdk-12.0.1
2. PATH
>%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin;
3. CLASS_PATH
>.;%JAVA_HOME%\lib;%JAVA_HOME%\lib\tools.jar;

注：注意CLASS_PATH最前面的那个点不要漏掉

**验证安装配置是否成功**：键盘按`win` + `r`调出运行，输入 `cmd` 调出命令行窗口，或者直接搜索command进入命令行，然后在命令行中输入`java -version`，输出java版本信息则配置成功。

## IDEA 安装

IntelliJ IDEA 是编写java代码最推荐的IDE，在官网

>https://www.jetbrains.com/idea/

可以下载，推荐下载ultimate版本。官网下载速度一般比较慢，网站

>http://www.xue51.com/soft/20053.html

提供了2019.1版本的百度网盘链接以及注册码，按照提示安装完成即可使用。


## PDF格式转换

### 引言

Java编程进行PDF转换的操作需要使用工具：Free Spire.PDF for Java（免费版），商业版需要付费，这个jar包可以通过maven安装。首先新建maven工程，需要填写的名称随便填写即可，然后在`pom.xml`文件中配置Maven仓库路径

```xml
<repositories>
        <repository>
            <id>com.e-iceblue</id>
            <name>e-iceblue</name>
            <url>http://repo.e-iceblue.com/nexus/content/groups/public/</url>
        </repository>
</repositories>
```
然后，在`pom.xml`文件中指定Free Spire.PDF for Java的Maven依赖

```xml
<dependencies>
    <dependency>
        <groupId> e-iceblue </groupId>
        <artifactId>spire.pdf.free</artifactId>
        <version>2.6.3</version>
    </dependency>
</dependencies>
```

配置完成后，在IDEA中，点击”Import Changes”即可导入jar包。

### 预处理

由于使用的是免费版本，该类包有转换页数为10页的限制，故需要先利用Adobe Acrobat Pro将要转换的PDF文件按照10页一个子文档进行**拆分**，具体操作如下：

![](https://imgkr.cn-bj.ufileos.com/0349099c-b53a-44f9-ae3e-d48605c11a2a.png)

拆分为多个子文档之后，需要编写一个方法读取这些PDF文件。

### 读取文件夹中全部PDF文档

拆分的多个子文档需要全部读取，然后循环处理各个子文档，读取指定路径文件夹下所有PDF文件的Java源代码如下：

```java
import java.io.File;
import java.util.List;

public class FileFinder {
    /*
     * 寻找指定目录下，具有指定后缀名的所有文件
     *
     * @param filenameSuffix : 文件后缀名
     * @param currentDirUsed : 当前使用的文件目录
     * @param currentFilenameList ：当前文件名称的列表
     */
    public void findFiles(String filenameSuffix, String currentDirUsed,
                          List<String> currentFilenameList) {

        File dir = new File(currentDirUsed);

        if (!dir.exists() || !dir.isDirectory()) {
            return;
        }

        for (File file : dir.listFiles()) {

            if (file.isDirectory()) {
                //如果目录则递归继续遍历
                findFiles(filenameSuffix,file.getAbsolutePath(), currentFilenameList);
            } else {
                //如果不是目录，那么判断文件后缀名是否符合
                if (file.getAbsolutePath().endsWith(filenameSuffix)) {
                    currentFilenameList.add(file.getAbsolutePath());
                }
            }
        }
    }
}
```

### PDF转SVG

PDF转SVG的Java源代码如下：

```java
/*
 * PDF2SVG.java
 * 将PDF文件转换为SVG图片
 */

import com.spire.pdf.*;
import java.util.ArrayList;
import java.util.List;

public class PDF2SVG {

    public static void main(String[] args) {

        FileFinder finder = new FileFinder();

        List<String> filenameList = new ArrayList<String>();

        // 文件后缀名
        String filenameSuffix = ".pdf";

        // 待转换PDF文件存储位置
        String currentDirUsed = "C:\\Users\\Jingxuan.Yang\\IdeaProjects\\SpireDemo";

        finder.findFiles(filenameSuffix, currentDirUsed, filenameList);

        // 进行文件转换，并将转化后的文件存储在原位置
        for (String filename : filenameList) {
            System.out.println("Processing: " + filename);
            PdfDocument pdf = new PdfDocument(filename);
            filename = filename.substring(0, filename.length()-4) + ".svg";
            pdf.saveToFile(filename, FileFormat.SVG);
        }
    }
}
```

**转换结果**示例：

![](https://imgkr.cn-bj.ufileos.com/ad11d779-1356-43fc-8661-68b611acddd3.svg)

此处为将SVG图片直接嵌入本网页中，在浏览器中打开本篇推送，可以放大查看以上图片。
























## 附录

以下为使用Java编程实现PDF到其他文件类别的转换，然而这些功能在Adobe Acrobat Pro中都已经可以实现，并不推荐用下述代码进行转换。以下是为了学习Java代码编写而写，有兴趣的读者也可以运行看。

### PDF转Word

PDF转Word的Java源代码如下：

```java
/*
 * PDF2Word.java
 * 将PDF文件转换为Word文档
 */

import com.spire.pdf.*;
import java.util.ArrayList;
import java.util.List;

public class PDF2Word {

    public static void main(String[] args) {

        FileFinder finder = new FileFinder();

        List<String> filenameList = new ArrayList<String>();

        // 文件后缀名
        String filenameSuffix = ".pdf";

        // 待转换PDF文件存储位置
        String currentDirUsed = "C:\\Users\\Jingxuan.Yang\\IdeaProjects\\SpireDemo";

        finder.findFiles(filenameSuffix, currentDirUsed, filenameList);

        // 进行文件转换，并将转化后的文件存储在原位置
        for (String filename : filenameList) {
            System.out.println("Processing: " + filename);
            PdfDocument pdf = new PdfDocument(filename);
            filename = filename.substring(0, filename.length()-4) + ".docx";
            pdf.saveToFile(filename, FileFormat.DOCX);
        }
    }
}
```

### PDF转HTML

PDF转HTML的Java源代码如下：

```java
/*
 * PDF2HTML.java
 * 将PDF文件转换为html网页文档，通过svg拼接的方式
 */

import com.spire.pdf.FileFormat;
import com.spire.pdf.PdfDocument;
import java.util.ArrayList;
import java.util.List;

public class PDF2HTML {

    public static void main(String[] args) {

        FileFinder finder = new FileFinder();

        List<String> filenameList = new ArrayList<String>();

        // 文件后缀名
        String filenameSuffix = ".pdf";

        // 待转换PDF文件存储位置
        String currentDirUsed = "C:\\Users\\Jingxuan.Yang\\IdeaProjects\\SpireDemo";

        finder.findFiles(filenameSuffix, currentDirUsed, filenameList);

        // 进行文件转换，并将转化后的文件存储在原位置
        for (String filename : filenameList) {
            System.out.println("Processing: " + filename);
            PdfDocument pdf = new PdfDocument(filename);
            filename = filename.substring(0, filename.length()-4) + ".html";
            pdf.saveToFile(filename, FileFormat.HTML);
        }
    }
}
```

### PDF转图片

PDF转图片的Java源代码如下，推荐转换为png文件，画质还差强人意。

```java
/*
 * PDF2Image.java
 * 将PDF文件转换图片，格式可以为png, jpg, jpeg, bmp, tiff, gif, emf等
 */

import com.spire.pdf.*;
import javax.imageio.ImageIO;
import java.awt.image.BufferedImage;
import java.io.File;
import java.io.IOException;
import java.util.ArrayList;
import java.util.List;

public class PDF2Image {
    public static void main(String[] args) throws IOException {

        FileFinder finder = new FileFinder();

        List<String> filenameList = new ArrayList<String>();

        // 文件后缀名
        String filenameSuffix = ".pdf";

        // 待转换PDF文件存储位置
        String currentDirUsed = "C:\\Users\\Jingxuan.Yang\\IdeaProjects\\SpireDemo";

        finder.findFiles(filenameSuffix, currentDirUsed, filenameList);

        // 进行文件转换，并将转化后的文件存储在原位置
        for (String filename : filenameList) {
            System.out.println("Processing: " + filename);
            PdfDocument pdf = new PdfDocument(filename);

            BufferedImage image;

            for(int i = 0; i < pdf.getPages().getCount(); i++){
                image = pdf.saveAsImage(i);

                // 格式更改
                String filenameImage = filename.substring(0, filename.length()-4) + String.format("-%d.png", i);
                System.out.println(filenameImage);
                File file = new File(filenameImage);

                // 格式更改
                ImageIO.write(image, "png", file);
            }

            pdf.close();
        }
    }
}
```

### PDF转XPS

PDF转XPS的Java源代码如下：

```java
/*
 * PDF2XPS.java
 * 将PDF文件转换为xps
 */

import com.spire.pdf.FileFormat;
import com.spire.pdf.PdfDocument;
import java.util.ArrayList;
import java.util.List;

public class PDF2XPS {

    public static void main(String[] args) {

        FileFinder finder = new FileFinder();

        List<String> filenameList = new ArrayList<String>();

        // 文件后缀名
        String filenameSuffix = ".pdf";

        // 待转换PDF文件存储位置
        String currentDirUsed = "C:\\Users\\Jingxuan.Yang\\IdeaProjects\\SpireDemo";

        finder.findFiles(filenameSuffix, currentDirUsed, filenameList);

        // 进行文件转换，并将转化后的文件存储在原位置
        for (String filename : filenameList) {
            System.out.println("Processing: " + filename);
            PdfDocument pdf = new PdfDocument(filename);
            filename = filename.substring(0, filename.length()-4) + ".xps";
            pdf.saveToFile(filename, FileFormat.XPS);
        }
    }
}

```

### PDF转PDF/A

PDF/X、PDF/E 和 PDF/A 标准是由国际标准化组织 (ISO) 定义的。PDF/X 标准应用于图形内容交换；PDF/E 标准应用于工程文档的交互式交换；PDF/A 标准应用于电子文档的**长期归档**。

PDF转PDF/A格式的Java源代码如下：

```java
/*
 * PDF2PDFA.java
 * 将PDF文件转换为符合PDF/A格式的文件
 */

import com.spire.pdf.*;
import com.spire.pdf.graphics.PdfMargins;
import java.awt.geom.Dimension2D;
import java.util.ArrayList;
import java.util.List;

public class PDF2PDFA {
    public static void main(String[] args) {

        FileFinder finder = new FileFinder();

        List<String> filenameList = new ArrayList<String>();

        // 文件后缀名
        String filenameSuffix = ".pdf";

        // 待转换PDF文件存储位置
        String currentDirUsed = "C:\\Users\\Jingxuan.Yang\\IdeaProjects\\SpireDemo";

        finder.findFiles(filenameSuffix, currentDirUsed, filenameList);

        // 进行文件转换，并将转化后的文件存储在原位置
        for (String filename : filenameList) {
            System.out.println("Processing: " + filename);
            PdfDocument pdf = new PdfDocument(filename);

            // 转换为Pdf_A_1_B格式
            PdfNewDocument newDoc = new PdfNewDocument();
            newDoc.setConformance(PdfConformanceLevel.Pdf_A_1_B);
            PdfPageBase page;
            for (int i = 0; i < pdf.getPages().getCount(); i++) {
                page = pdf.getPages().get(i);
                Dimension2D size = page.getSize();
                PdfPageBase p = newDoc.getPages().add(size, new PdfMargins(0));
                page.createTemplate().draw(p, 0, 0);
            }

            // 重命名文件
            filename = filename.substring(0, filename.length()-4) + "PDFA.pdf";

            // 保存结果文件
            newDoc.save(filename);
            newDoc.close();
        }
    }
}
```

## 后记

偶然萌生的一个把PDF转换为SVG的想法，促使我简单接触了Java这门编程语言。学的语言越多，越发现他们的编程思想都很相似，只不过是同一种思想（面向对象 + 面向过程）用不同的语法规则实现而已。大道至简，Happy Programing!

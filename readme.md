# THIS PROJECT IS DEAD

https://dotblogs.com.tw/yc421206/2012/04/30/71911 [C#.NET] 使用 7-zip 解壓縮檔案

https://www.itread01.com/articles/1498675086.html SevenZipSharp的入門教程（包含如何加密壓縮，解密壓縮）

http://www.aspphp.online/bianchen/dnet/cxiapu/cxprm/201701/192624.html  C#:SevenZipSharp使用7z.dll來進行壓縮與解壓縮

Please use this actively maintained fork: https://github.com/squid-box/SevenZipSharp

-------------------------------------------------------------
This is a fork from Codeplex original project.

Here are the main differences:
* VS 2015 project
* .Net 4.5 instead of 2.0
* only .Net 4.5 works (no Mobile or Mono compat, but if you do a PR, ...)
* has a nuget package https://www.nuget.org/packages/SevenZipSharp.Net45/
* CI with appveyor [![Build status](https://ci.appveyor.com/api/projects/status/vf1xn8e9lqxnpwm8?svg=true)](https://ci.appveyor.com/project/tomap/sevenzipsharp)

ToDo:
* Convert Console Tests into real Unit tests (MSTest or NUnit or XUnit)

-------------------------------------------------------------

Project Description
Managed 7-zip library written in C# that provides data (self-)extraction and compression (all 7-zip formats are supported). It wraps 7z.dll or any compatible one and makes use of LZMA SDK.

General
SevenZipSharp is an open source wrapper for 7-zip released under LGPL v3.0. It exploits the native 7zip dynamic link library through its COM interface and exports classes to work with various file archives. The project appeared as an improvement of http://www.codeproject.com/KB/DLL/cs_interface_7zip.aspx. It supports .NET and Windows Mobile .NET Compact.

The solution consists of SevenZipSharp library itself, console, WinForms and WPF test applications and the documentation. All are built with Microsoft Visual Studio 2008 or 2010 and under .NET 2.0 (up to 4.0).
Sandcastle is used to build the library documentation.
SevenZipSharp uses JetBrains ReSharper to maintain the quality of the code and NDepend to collect code statistics and audit the whole project. Special thanks to SciTech Software for .NET Memory Profiler.

Check SVN for the latest version of SevenZipSharp.

Quick start
SevenZipSharp exports three main classes - SevenZipExtractor, SevenZipCompressor and SevenZipSfx.
SevenZipExtractor is a 7-zip unpacking front-end, it allows either to extract archives or LZMA-compressed byte arrays.
SevenZipCompressor is a 7-zip pack ingfront-end, it allows either to compress archives or byte arrays.
SevenZipSfx is a special class to create self-extracting archives. It uses the embedded sfx module by Oleg Scherbakov .
LzmaEncodeStream/LzmaDecodeStream are special fully managed classes derived from Stream to store data compressed with LZMA and extract it.
See SevenZipTest/Program.cs for simple code examples; SevenZipTestForms is the GUI demo application.
You may find useful the SevenZipSharp documentation provided in CHM format. On Windows XP SP2 or later or Vista unblock the file to view it correctly.

Native libraries
SevenZipSharp requires a 7-zip native library to function. You can specify the path to a 7-zip dll (7z.dll, 7za.dll, etc.) in LibraryManager.cs at compile time, your app.config or via SetLibraryPath() method at runtime. <Path to SevenZipSharp.dll> + "7z.dll" is the default path. For 64-bit systems, you must use the 64-bit versions of those libraries.
7-zip ships with 7z.dll, which is used for all archive operations (usually it is "Program Files\7-Zip\7z.dll"). 7za.dll is a light version of 7z.dll, it supports only 7zip archives. You may even build your own library with formats you want from 7-zip sources. SevenZipSharp will work with them all.

Main features
Encryption and passwords are supported.
Since the 0.26 release, archive properties are supported.
Since the 0.28 release, multi-threading is supported.
Since the 0.29 release, streaming is supported.
Since the 0.41 release, you can specify the compression level and method.
Since the 0.50 release, archive volumes are supported.
Since the 0.51 release, archive updates are supported (0.52 - ModifyArchive). You must use the most recent 7z.dll (v>=9.04) for this feature.
Since the 0.61 release, Windows Mobile ARM platforms are supported.
Since the 0.62 release, extraction from SFX archives, as well as some other formats with embedded archives is supported.

Extraction is supported from any archive format in InArchiveFormat - such as 7-zip itself, zip, rar or cab and the format is automatically guessed by the archive signature (since the 0.43 release).
You can compress streams, files or whole directories in OutArchiveFormat - 7-zip, Xz, Zip, GZip, BZip2 and Tar.
Please note that GZip and BZip2 compresses only one file at a tme.

SevenZipSharpMobile (SevenZipSharp for Windows Mobile) does not differ much from its big brother. See the difference table below.

Self-extracting archives
SevenZipSfx appeared in the 0.42 release. It supports custom sfx modules. The most powerful one is embedded in the assembly, the other lie in SevenZip/sfx directory. Apart from usual sfx, you can make even small installations with the help of SfxSettings scenarios. Refer to the "configuration file parameters" for the complete command list.

Advanced work with SevenZipCompressor
SevenZipCompressor.CustomParameters is a special property to set compression switches, compatible with command line switches of 7z.exe. The complete list of those switches is in 7-zip.chm of 7-Zip installation. For example, to turn on multi-threaded compression, code
<SevenZipCompressor Instance>.CustomParameters.Add("mt", "on");
For the complete switches list, refer to SevenZipDoc.chm in the 7-zip installation.

Conditional compilation symbols
Since the 0.50 release, compilation symbols are supported: UNMANAGED, COMPRESS, SFX, LZMA_STREAM.
UNMANAGED allows the main COM part of SevenZipSharp to be built.
COMPRESS allows the compression classes to be built.
SFX allows the sfx classes to be built.
LZMA_STREAM allows LzmaEncodeStream/LzmaDecodeStream to be built.
CS4 enables features of C# 4 in Visual Studio 2010.

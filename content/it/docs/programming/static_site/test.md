---
weight: 510
title: "Hugo"
description: "A fast and flexible static site generator built in Go!"
icon: edit_note
date: 2022-11-22T12:36:15+00:00
lastmod: 2022-11-22T12:36:15+00:00
draft: false
images: []
---

> ##### Install Hugo on Windows.

### Editions

Hugo is available in three editions: standard, extended, and extended/deploy. While the standard edition provides core functionality, the extended and extended/deploy editions offer advanced features.

{{< table "table-hover table-responsive" >}}
| Feature | Extended Edition | Extended/Deploy Edition |
|---------|--------|--------|
| Encode to the WebP format when [processing images](https://gohugo.io/content-management/image-processing/ "processing images"). You can decode WebP images with any edition. |  ✔️  |  ✔️ |
| [Transpile Sass to CSS](https://gohugo.io/hugo-pipes/transpile-sass-to-css/ "Transpile Sass to CSS") using the embedded LibSass transpiler. You can use the [Dart Sass](https://gohugo.io/hugo-pipes/transpile-sass-to-css/#dart-sass "Dart Sass") with any edition. |  ✔️  |  ✔️ |  
| Deploy your site directly to a Google Cloud Storage bucket, an AWS S3 bucket, or an Azure Storage container. See [details](https://gohugo.io/hosting-and-deployment/hugo-deploy/ "details"). |  ✖️  |  ✔️ | 
{{< /table >}}

> ##### We recommend that you install the extended edition.
 
### Package Managers
Free and open-source package managers for Windows to install the extended edition of Hugo:

{{< tabs tabTotal="3">}}
{{% tab tabName="Chocolatey" %}}

```cmd
choco install hugo-extended
```

{{% /tab %}}
{{% tab tabName="Scoop" %}}

```cmd
scoop install hugo-extended
```

{{% /tab %}}
{{% tab tabName="Winget" %}}

```cmd
winget install Hugo.Hugo.Extended
```

{{% /tab %}}
{{< /tabs >}}

### Prebuilt binaries

{{% alert icon="♦️" context="light" %}}
Prebuilt binaries are available for a variety of operating systems and architectures. Visit the [latest release](https://github.com/gohugoio/hugo/releases/latest) page, and scroll down to the Assets section.

1. Download the archive for the desired edition, operating system, and architecture
2. Extract the archive
3. Move the executable to the desired directory
4. Add this directory to the PATH environment variable
5. Verify that you have execute permission on the file

Please consult your operating system documentation if you need help setting file permissions or modifying your PATH environment variable.
If you do not see a prebuilt binary for the desired edition, operating system, and architecture, install Hugo using one of the methods described below.
{{% /alert %}}

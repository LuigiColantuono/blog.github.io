---
weight: 510
title: "Hugo"
description: "Hugo SSG"
icon: manage_accounts
date: 2022-11-22T12:36:15+00:00
lastmod: 2022-11-22T12:36:15+00:00
draft: false
images: []
---

> ##### Personally I think Hugo is great.
> ##### It is very fast, safe, portable and you can easily deploy it on Github or Cloudflare pages, VPS etc ...

### Editions

Hugo is available in two editions: standard and extended. With the extended edition you can:

1. Encode to the WebP format when [processing images](https://gohugo.io/content-management/image-processing/ "processing images"). You can decode WebP images with either edition.
2. [Transpile Sass to CSS](https://gohugo.io/hugo-pipes/transpile-sass-to-css/ "Transpile Sass to CSS") using the embedded LibSass transpiler. The extended edition is not required to use the [Dart Sass](https://gohugo.io/hugo-pipes/transpile-sass-to-css/#dart-sass "Dart Sass") transpiler.

> ##### We recommend that you install the extended edition.
 
### Installation

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

Prebuilt binaries are available for a variety of operating systems and architectures. Visit the latest release page, and scroll down to the Assets section.

    Download the archive for the desired edition, operating system, and architecture
    Extract the archive
    Move the executable to the desired directory
    Add this directory to the PATH environment variable
    Verify that you have execute permission on the file

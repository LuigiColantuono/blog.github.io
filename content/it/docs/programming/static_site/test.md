---
weight: 510
title: "Hugo"
description: "Un generatore di siti statici veloce e flessibile creato in Go!"
icon: edit_note
date: 2022-11-22T12:36:15+00:00
lastmod: 2022-11-22T12:36:15+00:00
draft: false
images: []
---

> ##### Installa Hugo su Windows.

### Edizioni

Hugo è disponibile in tre edizioni: standard, extended ed extended/deploy. Mentre l'edizione standard fornisce funzionalità di base, le edizioni extended ed extended/deploy offrono funzionalità avanzate.

{{< table "table-hover table-responsive" >}}
| Feature | Extended Edition | Extended/Deploy Edition |
|---------|--------|--------|
| Encode to the WebP format when [processing images](https://gohugo.io/content-management/image-processing/ "processing images"). You can decode WebP images with any edition. |  ✔️  |  ✔️ |
| [Transpile Sass to CSS](https://gohugo.io/hugo-pipes/transpile-sass-to-css/ "Transpile Sass to CSS") using the embedded LibSass transpiler. You can use the [Dart Sass](https://gohugo.io/hugo-pipes/transpile-sass-to-css/#dart-sass "Dart Sass") with any edition. |  ✔️  |  ✔️ |  
| Deploy your site directly to a Google Cloud Storage bucket, an AWS S3 bucket, or an Azure Storage container. See [details](https://gohugo.io/hosting-and-deployment/hugo-deploy/ "details"). |  ✖️  |  ✔️ | 
{{< /table >}}

> ##### Ti consigliamo di installare l'extended edition.
 
### Package Managers
Package managers free e open-source per Windows per l'installazione di Hugo extended edition:

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
Prebuilt binaries disponibili per varie architetture e sistemi operativi. Visita la pagina [latest release](https://github.com/gohugoio/hugo/releases/latest), e scrolla giú nella sezione **Asset**.

1. Download l'archivio per l'edizione, il sistema operativo e l'architettura desiderata
2. Estrai l'archivio
3. Sposta l'archivio nella directory desiderata
4. Aggiungi la directory nel PATH delle variabili d'ambiente
5. Verifica di avere l'autorizzazione per eseguire il file

Consulta la documentazione del tuo sistema operativo se hai bisogno di aiuto per impostare le autorizzazioni del file o modificare la variabile di ambiente PATH.
{{% /alert %}}

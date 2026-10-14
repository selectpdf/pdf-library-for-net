<p align="center">
  <a href="https://selectpdf.com">
    <img src="images/logos/selectpdf-logo-h128-amberbg.png" alt="SelectPdf" height="128">
  </a>
</p>

<h1 align="center">SelectPdf Library for .NET</h1>

<p align="center">
  The all-in-one PDF toolkit for .NET — convert HTML to PDF, create and edit PDF documents, and render web pages to images, from any .NET application.
</p>

<p align="center">
  <a href="https://www.nuget.org/packages/Select.Pdf.NetCore/"><img src="https://img.shields.io/nuget/v/Select.Pdf.NetCore.svg?label=Select.Pdf.NetCore" alt="NuGet"></a>
  <a href="https://www.nuget.org/packages/Select.HtmlToPdf.NetCore/"><img src="https://img.shields.io/nuget/v/Select.HtmlToPdf.NetCore.svg?label=Select.HtmlToPdf.NetCore%20(free)" alt="NuGet"></a>
  <a href="https://www.nuget.org/packages/SelectPdf.Universal/"><img src="https://img.shields.io/nuget/v/SelectPdf.Universal.svg?label=SelectPdf.Universal%20(cross-platform)" alt="NuGet"></a>
  <a href="https://selectpdf.com/html-to-pdf-converter-for-net/"><img src="https://img.shields.io/badge/website-selectpdf.com-f59e0b" alt="Website"></a>
</p>

<p align="center">
  <strong>Latest release: v26.5</strong> — accessible PDF from real web pages, text search in every script, and SelectPdf.Universal 26.5 with a remote engine, tables of contents and token signing.
</p>

---

## Overview

**SelectPdf for .NET** is a powerful, easy-to-use library that lets you generate, manipulate
and render PDF documents directly from your .NET code — no external dependencies, no print
drivers, no server-side software to install. It is trusted in production by thousands of
developers for invoices, reports, statements, tickets, contracts and any other
document-generation workload.

The flagship feature is a best-in-class **HTML to PDF** converter that renders modern HTML5,
CSS3 and JavaScript with full fidelity, but the library also includes a complete PDF object
model so you can build documents from scratch, merge and split files, fill forms, add security,
stamp templates and more.

## New: SelectPdf.Universal for Windows, Linux and macOS

This repository covers the **classic** SelectPdf library for Windows. Since version 26.4 the family also
includes **[SelectPdf.Universal](https://selectpdf.com/pdf-library-cross-platform/)**, our flagship: the
SelectPdf API you already know, running on **Windows (x64, x86), Linux (x64, ARM64) and macOS on Apple
Silicon**, on .NET 8 and .NET 10, and in Docker with nothing to apt-get. 82% of the classic public API
carries over unchanged apart from the namespace, which is `SelectPdf.Universal`; the migration topic in
the documentation lists every change.

SelectPdf.Universal is also where new features land first: Word to PDF, redaction, signature
validation, PDF/A-4 and PDF/UA-2 since 26.4, and in **26.5**:

- a **remote engine** container (`ghcr.io/selectpdf/engine`), so applications on Alpine Linux and other
  musl-based systems convert too;
- **one package per platform** (`SelectPdf.Universal.Windows`, `.Linux`, `.Linux.Arm64`, `.MacOS`);
- **tables of contents with page numbers** and **HTML forms converted to fillable PDF fields**;
- **signing with keys the library never sees**: certificate store, USB tokens, smart cards and HSMs
  (PKCS#11), key services in one or two steps, and **long-term validation** (PAdES B-LT);
- **PDF/A-1a, PDF/A-2a and PDF/A-2u**, and faster parallel conversions.

```powershell
dotnet add package SelectPdf.Universal.Linux              # the library and the Linux x64 engine
```

The classic library continues to be maintained, with .NET Framework 2.0 support and all four rendering
engines. **One license covers both.**

## What's new in v26.5

- ♿ **Accessible PDF from real web pages.** Tagged (PDF/UA-1) and PDF/A-3a conversions of real-world
  pages now pass validation: decorative paint is marked as an artifact, content is attached to the element
  it belongs to, and grouping elements hold their content the way the standard requires. Checked with
  [veraPDF](https://verapdf.org/) on GitHub, the W3C home page and Wikipedia in English, Chinese, Arabic,
  Hebrew and Japanese, with the Chromium and Blink engines.
- 🖼️ An HTML `<figure>` is tagged as the picture it holds, with the picture's alternate text and its
  caption.
- 🔎 **Text search in every script.** `PdfToText.Search` finds text in Cyrillic, Chinese, Japanese,
  Korean, Hindi, Thai, Arabic and Hebrew, and right-to-left terms typed in reading order.
- 🔤 Arabic words are extracted whole, and extracted text no longer carries invisible bidi embedding
  characters.
- 🔗 With the Chromium and Blink engines, very long anchor names (headings in Japanese, for example) are
  renamed so PDF/A accepts them, and links to anchors a page does not define no longer point anywhere.
- 🌐 With the Chromium engine, a page that navigates while it is being printed converts instead of failing.

v26.4 added **ZUGFeRD / Factur-X electronic invoices**, custom XMP metadata, Chromium 154 and much faster
saving of large documents. v26.3 added **accessible (tagged) PDF / PDF/UA-1** and **PDF/A-3** (levels b, u
and a).

> Accessible (tagged) PDF, PDF/A-3 and electronic invoices are features of the **commercial** library
> (not the free Community Edition). Accessible PDF and PDF/A-3 output use the **Chromium** or **Blink**
> rendering engine.

## Editions

SelectPdf ships as several NuGet product lines, all built from the same engine:

| Edition | Package | What you get |
|---|---|---|
| **Select.Pdf** | [`Select.Pdf`](https://www.nuget.org/packages/Select.Pdf/) | Full commercial library — HTML→PDF, PDF creation, merge/split, security, forms, digital signatures, accessible (tagged) PDF / PDF/UA-1, PDF/A-3, PDF→text/image, and more. |
| **Select.HtmlToPdf** *(Free Community Edition)* | [`Select.HtmlToPdf`](https://www.nuget.org/packages/Select.HtmlToPdf/) | Free HTML→PDF converter. Same rendering quality as the commercial edition, limited to 5 pages per document. |
| **SelectPdf.Extras** | [`Select.Pdf.Extras`](https://www.nuget.org/packages/Select.Pdf.Extras/) | Optional add-on with a modern AcroForms manager and PDF compressor. |
| **SelectPdf.Universal** *(cross-platform)* | [`SelectPdf.Universal`](https://www.nuget.org/packages/SelectPdf.Universal/) | The cross-platform flagship for Windows, Linux and macOS on Apple Silicon (or anywhere through the remote engine), plus Word to PDF, redaction, signature validation, token and HSM signing, long-term validation, PDF/A-4 and PDF/UA-2. |
| **SelectPdf.HtmlToPdf.Universal** *(Free Community Edition, cross-platform)* | [`SelectPdf.HtmlToPdf.Universal`](https://www.nuget.org/packages/SelectPdf.HtmlToPdf.Universal/) | Free cross-platform HTML→PDF converter, limited to 5 pages per document. |

## Features

- 🌐 **HTML to PDF** — convert any URL or raw HTML string to a pixel-perfect PDF.
- 🖼️ **HTML to Image** — render web pages to PNG/JPG.
- 📄 **PDF creation** — build documents from text, images, shapes, tables and templates.
- 🔗 **Web element mapping** — map HTML DOM elements to their exact position on the generated PDF page (for links, bookmarks, overlays).
- 📑 **Headers & footers**, page numbering, table of contents and internal links.
- 🔀 **Merge & split**, stamp, resize and reorganize existing PDFs.
- 🔎 **PDF to text and image** — extract and search text in any script *(v26.5)*, render pages to images.
- 🔒 **Security** — encryption, passwords and permissions.
- 🖊️ **AcroForms** — create and fill PDF form fields; digital signatures.
- ♿ **Accessible (tagged) PDF** — PDF/UA-1 with logical structure tree, reading order and alt text *(v26.3)*.
- 🗄️ **Compliance** — PDF/A-3 (levels b, u, a) *(v26.3)*, PDF/A and PDF/X for archiving and graphics exchange.
- 🧾 **Electronic invoices** — ZUGFeRD / Factur-X, including EN 16931 and XRechnung *(v26.4)*.
- 📐 Full control over page size, orientation, margins, scaling and CSS media type.
- 🔐 Authentication, custom HTTP headers, cookies, POST data and proxy support for the converter.

## Rendering engines

The HTML→PDF converter can render with several engines, selectable per conversion via
`HtmlToPdfOptions.RenderingEngine`:

| Engine | Description |
|---|---|
| **WebKit** | Default engine, embedded — no extra files to deploy. |
| **WebKit Restricted** | WebKit variant for restricted-permission / limited-trust hosting environments. |
| **Blink** | Standalone Chromium driven over CDP (modern .NET targets). |
| **Chromium** | Chromium Embedded Framework (CEF) backend for the latest rendering features. |

> WebKit, WebKit Restricted and Chromium run on every supported framework (from .NET Framework 2.0 up).
> The **Blink** engine requires .NET Framework 4.6.1 or later (.NET Core and .NET 5–10).
> Blink and Chromium require an additional runtime NuGet package (see Installation below).

## Supported platforms

- **.NET Framework** 2.0, 4.0, 4.6.1, 4.7.2
- **.NET Standard 2.0** / .NET Core / .NET 5+
- **Windows** x86 and x64

For **Linux** (x64, ARM64), **macOS on Apple Silicon** and **Docker**, use
[SelectPdf.Universal](https://selectpdf.com/pdf-library-cross-platform/) (.NET 8 and .NET 10, plus
.NET Standard 2.0).

## Installation

Install from NuGet. Pick the package that matches your target runtime and architecture.

**.NET (Core / 5+ / Standard 2.0):**

```powershell
# Commercial — full library
Install-Package Select.Pdf.NetCore           # AnyCPU / x86
Install-Package Select.Pdf.NetCore.x64       # x64

# Free Community Edition (HTML to PDF only)
Install-Package Select.HtmlToPdf.NetCore
```

**.NET Framework:**

```powershell
Install-Package Select.Pdf                   # AnyCPU / x86
Install-Package Select.Pdf.x64               # x64

Install-Package Select.HtmlToPdf             # Free Community Edition
```

**Optional engine runtimes** (only if you select the Blink or Chromium engine):

```powershell
Install-Package Select.Pdf.NetCore.Blink
Install-Package Select.Pdf.NetCore.Chromium.Windows
```

## Quick start

### Convert a URL to PDF

```csharp
using SelectPdf;

// Create the converter
HtmlToPdf converter = new HtmlToPdf();

// Convert a web page
PdfDocument doc = converter.ConvertUrl("https://selectpdf.com");

// Save and close
doc.Save("output.pdf");
doc.Close();
```

### Convert an HTML string to PDF

```csharp
using SelectPdf;

HtmlToPdf converter = new HtmlToPdf();

string html = "<h1>Hello, PDF!</h1><p>Generated with SelectPdf for .NET.</p>";
PdfDocument doc = converter.ConvertHtmlString(html);

doc.Save("hello.pdf");
doc.Close();
```

### Customize the output

```csharp
using SelectPdf;

HtmlToPdf converter = new HtmlToPdf();

// Page setup
converter.Options.PdfPageSize        = PdfPageSize.A4;
converter.Options.PdfPageOrientation = PdfPageOrientation.Portrait;
converter.Options.MarginTop          = 20;
converter.Options.MarginBottom       = 20;

// Rendering
converter.Options.WebPageWidth = 1024;
converter.Options.RenderingEngine = RenderingEngine.Chromium;

PdfDocument doc = converter.ConvertUrl("https://selectpdf.com");
doc.Save("custom.pdf");
doc.Close();
```

### Render a web page to an image

```csharp
using SelectPdf;

HtmlToImage converter = new HtmlToImage();
System.Drawing.Image image = converter.ConvertUrl("https://selectpdf.com");
image.Save("page.png");
```

## Documentation & samples

- 📖 **Online documentation:** https://selectpdf.com/pdf-library-classic/ (Community Edition: https://selectpdf.com/html-to-pdf/docs-classic/)
- 🧪 **Live demo (C#):** https://selectpdf.com/demo/ (Community Edition: https://selectpdf.com/html-to-pdf/demo/)
- 🏠 **Product page:** https://selectpdf.com/pdf-library-for-net/
- ⬇️ **Downloads & free trial:** https://selectpdf.com/downloads/
- 🐧 **SelectPdf.Universal (cross-platform):** https://selectpdf.com/pdf-library-cross-platform/ (documentation: https://selectpdf.com/pdf-library/)

## Licensing

- **Select.HtmlToPdf** is a free Community Edition (HTML→PDF, capped at 5 pages per document).
- **Select.Pdf** is a commercial product. A free trial is available, and a license key unlocks
  the full feature set with no page limits or watermarks. Licenses are perpetual and per developer,
  and **one license covers both the classic library and SelectPdf.Universal**. See the
  [pricing page](https://selectpdf.com/pricing/) for details.

## Support

For questions, bug reports and feature requests, visit [selectpdf.com](https://selectpdf.com)
or open an issue in this repository.

---

<p align="center">© SelectPdf — <a href="https://selectpdf.com">selectpdf.com</a></p>

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
  <a href="https://selectpdf.com/html-to-pdf-converter-for-net/"><img src="https://img.shields.io/badge/website-selectpdf.com-f59e0b" alt="Website"></a>
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

## Editions

SelectPdf ships as several NuGet product lines, all built from the same engine:

| Edition | Package | What you get |
|---|---|---|
| **Select.Pdf** | [`Select.Pdf`](https://www.nuget.org/packages/Select.Pdf/) | Full commercial library — HTML→PDF, PDF creation, merge/split, security, forms, digital signatures, PDF→text/image, and more. |
| **Select.HtmlToPdf** *(Free Community Edition)* | [`Select.HtmlToPdf`](https://www.nuget.org/packages/Select.HtmlToPdf/) | Free HTML→PDF converter. Same rendering quality as the commercial edition, limited to 5 pages per document. |
| **SelectPdf.Extras** | [`Select.Pdf.Extras`](https://www.nuget.org/packages/Select.Pdf.Extras/) | Optional add-on with a modern AcroForms manager and PDF compressor. |

## Features

- 🌐 **HTML to PDF** — convert any URL or raw HTML string to a pixel-perfect PDF.
- 🖼️ **HTML to Image** — render web pages to PNG/JPG.
- 📄 **PDF creation** — build documents from text, images, shapes, tables and templates.
- 🔗 **Web element mapping** — map HTML DOM elements to their exact position on the generated PDF page (for links, bookmarks, overlays).
- 📑 **Headers & footers**, page numbering, table of contents and internal links.
- 🔀 **Merge & split**, stamp, resize and reorganize existing PDFs.
- 🔒 **Security** — encryption, passwords and permissions.
- 🖊️ **AcroForms** — create and fill PDF form fields; digital signatures.
- 📐 Full control over page size, orientation, margins, scaling and CSS media type.
- 🔐 Authentication, custom HTTP headers, cookies, POST data and proxy support for the converter.

## Rendering engines

The HTML→PDF converter can render with several engines, selectable per conversion via
`HtmlToPdfOptions.RenderingEngine`:

| Engine | Description |
|---|---|
| **WebKit** | Default engine, embedded — no extra files to deploy. |
| **Blink** | Standalone Chromium driven over CDP (modern .NET targets). |
| **Chromium** | Chromium Embedded Framework (CEF) backend for the latest rendering features. |

> Blink and Chromium require an additional runtime NuGet package (see Installation below).

## Supported platforms

- **.NET Framework** 2.0, 4.0, 4.6.1, 4.7.2
- **.NET Standard 2.0** / .NET Core / .NET 5+
- **Windows** x86 and x64

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

- 📖 **Online documentation:** https://selectpdf.com/html-to-pdf/docs/
- 🧪 **Live demo (C# / VB.NET):** https://selectpdf.com/html-to-pdf/demo/
- 🏠 **Product page:** https://selectpdf.com/html-to-pdf-converter-for-net/
- ⬇️ **Downloads & free trial:** https://selectpdf.com/downloads/

## Licensing

- **Select.HtmlToPdf** is a free Community Edition (HTML→PDF, capped at 5 pages per document).
- **Select.Pdf** is a commercial product. A free trial is available, and a license key unlocks
  the full feature set with no page limits or watermarks. See the
  [website](https://selectpdf.com/html-to-pdf-converter-for-net/) for licensing details.

## Support

For questions, bug reports and feature requests, visit [selectpdf.com](https://selectpdf.com)
or open an issue in this repository.

---

<p align="center">© SelectPdf — <a href="https://selectpdf.com">selectpdf.com</a></p>

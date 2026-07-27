# BeBold

**Hello, Bold You** — a browser-based tool that distills bold/emphasized text and headings from an HTML document into a navigable slide-show carousel.

## Overview

BeBold (a.k.a. "Bold U") extracts `<em>`, `<strong>`, and `<h1>` elements from an HTML file you upload, then presents each extracted snippet as a slide in a [Slick Carousel](https://github.com/kenwheeler/slick/) slideshow. The carousel state is encoded into the URL query string so you can **bookmark** a specific set of slides and return to it later. It also includes a file uploader (Uppy) for saving carousels to a server.

Use it to prepare for a speech, study for an exam, or quickly orient yourself to a long online document by reading only the key bolded points.

## Prerequisites

- A modern web browser with JavaScript enabled.
- Internet access (the page loads jQuery, Slick Carousel, and Uppy from CDNs).

## Setup

```bash
git clone https://github.com/biofol/BeBold.git
cd BeBold
```

No build step required. Open `index.html` in a browser, or serve locally:

```bash
python3 -m http.server 8000
# visit http://localhost:8000/
```

## How to Run / Use

1. Open `index.html` in a browser.
2. Click the file input ("Read an htmlfile to extract the bold ideas") and select an HTML file.
3. The tool extracts all `<em>`, `<strong>`, and `<h1>` text and builds a carousel.
4. Navigate slides using the carousel arrows/dots.
5. **Bookmark the page** to save the current carousel — the slide content is stored in the URL query string.
6. The extracted text also appears in the textarea for copy/paste.

## Project Structure

```
BeBold/
├── README.md       # This file
└── index.html      # The complete BeBold application (HTML + CSS + JS)
```

## Notes

- The carousel content is encoded in the URL via `?` + HTML `<div>` markup; very large documents may exceed URL length limits.
- The Uppy uploader posts to `https://peec.biz/BB/upload.php` (an external endpoint).
- The related repo [BB](https://github.com/biofool/BB) contains a Python (BeautifulSoup) command-line version of the same concept.

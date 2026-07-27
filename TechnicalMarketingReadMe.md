# Technical Marketing Summary — BeBold

## One-Line Positioning

A zero-install browser tool that turns any HTML document's bold text and headings into a bookmarkable slide-show carousel for fast skimming and study.

## Target Users / Personas

- **Students** preparing for exams who want to quickly review the key points of long online documents.
- **Public speakers / presenters** distilling a document down to its bolded ideas for speech prep.
- **Researchers / readers** who need to orient themselves in lengthy HTML content by reading only emphasized text.

## Key Features (Grounded in Code)

- **HTML bold-text extraction** — uses a JavaScript regex (`<(em|strong|h1)>(.*?)<\/\1>`) to pull emphasized text and headings from uploaded HTML files.
- **Slick Carousel slideshow** — paired nav + main carousels (`slider-nav` / `slider-for`) with center mode, dots, arrows, and fade transitions.
- **Bookmarkable carousels** — slide content is encoded into the URL query string so the current carousel can be saved as a browser bookmark and restored later.
- **File upload via Uppy** — drag-and-drop dashboard (Uppy.js) with TUS upload endpoint for saving carousels server-side.
- **Extracted text output** — all bolded snippets are displayed in a textarea for easy copy/paste.
- **Client-side only** — file reading via `FileReader` API; no server processing required for extraction.

## Technical Differentiators

- **URL-as-state** — the entire carousel is serialized into the URL, making bookmarks a zero-backend persistence mechanism.
- **Dual carousel pattern** — thumbnail navigation carousel synced with a full-slide display carousel via Slick's `asNavFor` option.
- **Regex-driven extraction** — configurable tag list (`em|strong|h1`) makes it easy to adjust which elements are extracted.
- **No build step** — single static HTML file with CDN-loaded libraries; works by simply opening the file.

## Use Cases

- Skimming a long web article by reading only its bold/heading text as slides.
- Creating a quick study deck from an online textbook chapter.
- Preparing talking points from a lengthy report or transcript.
- Saving curated slide sets as bookmarks for later review.

## Benefits / Value Proposition

- **Speed** — turn any HTML document into a slide deck in seconds, no manual copy-paste.
- **No installation** — works in any browser; just open the HTML file.
- **Portable state** — bookmarks carry the full carousel; no account or database needed.
- **Flexible** — adjust the regex tags to extract any set of HTML elements.

## Tech Stack

- **Frontend**: HTML5, CSS3, vanilla JavaScript
- **Libraries**: jQuery 3.4.1, Slick Carousel 1.8.1, Uppy 1.4.0 (with TUS uploader)
- **File handling**: FileReader API
- **Persistence**: URL query string / browser bookmarks

## Known Limitations

- Carousel content stored in the URL may exceed browser URL-length limits for large documents.
- Depends on external CDNs for jQuery, Slick, and Uppy; no offline support.
- The Uppy upload endpoint (`peec.biz/BB/upload.php`) is an external dependency that may not always be available.
- Extraction is limited to `<em>`, `<strong>`, and `<h1>` tags by default; other heading levels (`h2`–`h6`) are not included.
- No automated tests.

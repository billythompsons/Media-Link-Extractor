# Media Link Extractor

Media Link Extractor is an open-source browser extension for collecting the media used on a webpage and downloading it as one ZIP, similar to the media bundles Apple Newsroom provides for product announcements.

It finds images, video, audio, CSS background images, and streaming playlist links. Processing happens in the browser. There is no account, analytics, tracking, or server upload.

> **Project status:** Early MVP. The initial Manifest V3 extension can scan the active page, normalize and de-duplicate URLs, filter results, and build a client-side ZIP. Network-level capture, broader browser support, and a polished release are planned.

## Features

- Scan DOM media attributes, `srcset`, poster images, CSS backgrounds, links, and Resource Timing entries
- Normalize relative URLs and remove duplicates
- Filter by media type and search by URL
- Select assets and download them as one ZIP
- Include a plain-text URL manifest and a report for assets blocked by cross-origin rules or expired URLs
- Use minimal browser permissions and keep processing local

## Tech stack

- **Browser platform:** Chrome/Edge Manifest V3
- **Language:** JavaScript for the MVP, with a planned TypeScript migration as the codebase grows
- **Extraction:** An injected page scanner reads DOM media attributes, computed CSS backgrounds, and the Resource Timing API
- **ZIP generation:** JSZip runs locally in the extension popup
- **Testing:** Manual fixture-page testing today; unit tests for URL normalization, classification, and CSS parsing are next
- **CI:** A GitHub Actions validation and release-packaging workflow is planned

## Try the MVP

1. Download or clone the repository.
2. Open `chrome://extensions` (or `edge://extensions`).
3. Turn on Developer mode.
4. Choose **Load unpacked** and select this repository folder.
5. Open a page, click the extension, and choose **Scan page**.

## Limits

Some media cannot be downloaded because a site blocks cross-origin requests, a signed URL has expired, or media is DRM protected. Media Link Extractor reports failed downloads and includes discovered links in the ZIP. It does not bypass access controls or DRM.

## Roadmap

- TypeScript modules and automated tests
- Optional network-level capture for HLS (`.m3u8`) and DASH (`.mpd`) manifests
- Firefox support
- Thumbnails, file-size metadata, and advanced sorting
- Reproducible release ZIPs through GitHub Actions

## Contributing

Issues and pull requests are welcome. Please read [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md) before participating.

## License

MIT

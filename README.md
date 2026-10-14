# PPTXtractor

PPTXtractor is a single-file browser utility for pulling embedded
images and videos out of a PowerPoint deck.

## Quick Start

1. Open the live tool at https://seegree.github.io/pptx-tractor/, or open
   `index.html` locally in a current browser such as Chrome, Edge, or Safari.
2. Drop in a `.pptx` file.
3. The deck is analyzed automatically. Changing the resolution re-runs it.
4. Review the image/video list and warnings.
5. Click **Download ZIP**.

The ZIP contains:

- Original embedded image files
- Original embedded video files
- `ppt-media-report.html`
- `ppt-media-report.csv`

Media that needs review is prefixed in the ZIP:

- `LOW_RES__` means the media is below the expected source size.
- `CHECK_SIZE__` means the extractor could not confidently read dimensions, or
  the file is a duplicate worth reviewing.

## Resolution Checks

The tool compares every image and video against an expected source size. The
default is `1920 x 1080`. If either dimension is smaller than that expected
size, the media is marked `LOW_RES__`.

PowerPoint placement is still shown in the report as context, but it does not
decide whether an item passes. A small logo, screenshot, or icon can still be
flagged if its original file is below the expected source size.

## Privacy

The deck is processed locally in the browser. It is not uploaded anywhere and
does not use an external service.

## MVP Limits

- The tool is built for `.pptx` files, not legacy `.ppt`.
- It relies on modern browser ZIP decompression support.
- Embedded files under `ppt/media` are extracted.
- Externally linked media is reported but cannot be extracted from the `.pptx`.
- Video dimensions are detected for common browser-readable formats, especially
  MP4/MOV. WMV and other older formats may be marked `CHECK_SIZE__`.
- EMF/WMF vector images are extracted but may be marked `CHECK_SIZE__` because
  browser-readable pixel dimensions are not always available.

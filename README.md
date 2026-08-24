# Text Paragraph Viewer and Editor

A standalone, privacy-focused browser utility for displaying text as separate readable segments. The editor variant can create blank documents, edit text, record numbered modification notes, import basic text from `.docx` files, and read segments aloud through the browser's speech-synthesis interface.

## Licence

This project is licensed under the MIT Licence. See `LICENSE` for the complete licence text.

## Main files

- `readwrite_paragraph_viewer_v2.html`: stable read-only viewer.
- `text_paragraph_editor_v2.html`: expanded editor, tracked-notes, DOCX import, blank documents, and text-to-speech.
- `paragraph-editor-icon.png`: optional repository artwork. The editor embeds the icon internally and does not require the PNG at runtime.
- `AI-DISCLOSURE.md`: disclosure of AI assistance used during development.

## Features

- Opens common plain-text and Markdown-like files.
- Imports paragraph text from modern Word `.docx` files.
- Creates new blank documents.
- Direct editing and tracked modification-note modes.
- Custom literal or regular-expression separators.
- Browser speech synthesis with voice and rate selection.
- Optional filtering for voices reported by the browser as local.
- Saves edited text or a standalone HTML copy.
- Entirely client-side, with no document upload or analytics.
- Normal browser scrolling for long documents.

## Use

1. Open the HTML file in a current desktop browser.
2. Open a file or choose **New blank document**.
3. Select the segmentation rule.
4. Choose an editing mode.
5. Click a text segment to select the starting point for speech.
6. Save the result as a new text or HTML file.

## Segmentation

The editor can separate text using blank lines, every non-empty line, likely headings and symbol rules, groups of sentences, a custom literal string, or a custom JavaScript regular expression.

Custom regular expressions are entered without surrounding `/` characters. For example, `^={3,}$` separates lines containing three or more equals signs.

## Word document support

DOCX import extracts text from the main Word document body and converts Word paragraphs into text paragraphs. It does not preserve page layout, styles, images, tables, tracked changes, footnotes, headers, comments, or other advanced Word features. The source Word file is never overwritten. Legacy `.doc` files are not supported.

DOCX processing is local. It uses browser ZIP decompression support, which is most reliable in current Chromium-based browsers such as Microsoft Edge and Google Chrome.

## Speech

Speech uses the Web Speech API exposed by the browser. Available voices depend on the operating system and browser. Voices labelled `[local]` are reported by the browser as device-based voices. Other voices may use an online service. Select **Show local voices only** when offline or local-only operation is important.

Long documents are spoken one displayed segment at a time. The current segment is highlighted and scrolled into view. Playback can be paused, resumed, or stopped.

## Privacy

Files are processed in browser memory. This project contains no server, analytics, document upload, or external runtime dependency. Speech privacy depends on the selected operating-system/browser voice, so use a voice labelled `[local]` when local processing is required.

## Limitations

- DOCX support is text extraction, not full Word rendering.
- Legacy `.doc`, PDF, and ebook files are not supported.
- Imported text is assumed to be UTF-8.
- Speech behaviour and voice availability vary by browser and operating system.
- Tracked notes operate at segment level, not individual keystroke level.
- Browsers normally download a new file rather than overwrite the source.

## Contributing

Issues and pull requests are welcome. Compatibility reports should include operating system, browser version, accessibility software version, selected segmentation mode, and a small non-sensitive sample where possible.

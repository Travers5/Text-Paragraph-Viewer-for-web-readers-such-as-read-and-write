# Text Paragraph Viewer

A standalone browser-based accessibility helper for opening plain-text and Markdown documents and displaying them as individually addressable HTML segments. It was created to help reading tools such as Read&Write target a paragraph or section instead of automatically treating the entire file as one continuous block.

## Files

- `readwrite_paragraph_viewer_v2.html`: the original read-only paragraph viewer.
- `text_paragraph_editor.html`: the separate viewer/editor variant with direct and tracked-note editing.
- `paragraph-editor-icon.png`: optional repository artwork. The editor already contains the icon internally, so this PNG is not required when running the HTML file.

## Features

- Opens `.txt`, `.md`, `.markdown`, `.log`, `.csv`, `.tsv`, `.rst`, `.asc`, and comparable plain-text files.
- Runs entirely inside the browser. Documents are not uploaded to a server.
- Handles long documents using ordinary browser scrolling.
- Provides several paragraph-detection strategies:
  - blank lines;
  - every non-empty line;
  - wrapped paragraphs;
  - likely headings;
  - repeated separators such as `====`, `----`, and `++++`;
  - combined detection;
  - sentence groups.
- Provides alternative HTML structures so users can test which structure works best with their reading or accessibility software.
- Remembers the selected options in browser `localStorage`.
- Displays loading success, errors, file size, character count, and segment count.

## Using the viewer

1. Download the HTML file.
2. Open it in a current desktop browser.
3. Choose a local text or Markdown document.
4. Select a paragraph-detection method.
5. Select an HTML structure.
6. Hover over or focus an individual displayed segment using the preferred accessibility tool.
7. If the reading behaviour is not ideal, try another HTML structure or paragraph-detection method.

## Editor variant

The separate editor provides three modes:

### View only

Displays the document without allowing changes.

### Direct editing

Allows each segment to be edited in place. Saving exports the edited text without an audit appendix.

### Tracked modification notes

Allows editing in place while assigning a number to every changed segment. The exported text contains a matching marker beside the changed passage and a **Modification Notes** list at the end containing the original and revised text.

The tracked mode records changes at the segment level rather than recording every individual keystroke. If a changed segment is restored exactly to its original text, its modification record is removed.

## Saving

The editor can export:

- an edited `.txt` file; or
- a standalone `.html` copy.

Web browsers do not normally overwrite the source file directly. Exported files are therefore downloaded as new files, protecting the original document.

## Privacy

All processing is local to the browser. The application has no server component, analytics, tracking code, or external runtime dependencies.

## Accessibility notes

Results may vary between browsers, Read&Write versions, screen readers, and operating-system accessibility settings. The alternative HTML structures are experimental options intended to make practical compatibility testing easier.

## Limitations

- The application reads text-based formats, not Word documents, PDFs, or binary ebook formats.
- Markdown is treated as text. It is not rendered as a complete Markdown webpage.
- Character encoding is assumed to be UTF-8.
- Very large files may take longer to segment and render depending on the browser and computer.
- Tracked modification notes operate at paragraph or segment level, not at word-processing revision level.

## Running locally

No installation or web server is required. Double-click the HTML file or use **Open with** and select a browser.

## Contributing

Bug reports, compatibility results, and improvements are welcome through GitHub issues or pull requests. Reports are most useful when they include the browser version, operating system, accessibility tool version, selected segmentation mode, selected HTML structure, and a small non-sensitive sample document.

## Licence

Before publishing, add the licence you want to use. The MIT Licence is a common option for small open-source utilities, but no licence should be assumed until a `LICENSE` file is included in the repository.

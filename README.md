# Colab-XML-Parser-for-the-KJV-Bible-PCE-1900

A Python script designed for Google Colab that parses the [1900 KJV OSIS XML file from open-bibles](https://github.com/seven1m/open-bibles/blob/master/eng-kjv.osis.xml) and provides a user interface to format specific chapters and verses for easy copying and pasting.

## Description

This tool was created to solve the problem of tedious manual reformatting when copying Bible text (specifically the King James Version) for use in web content (like Substack) or narration scripts. Standard copy/paste often introduces unwanted line breaks and spacing issues, while manual correction is time-consuming.

This script fetches the KJV OSIS XML, parses it, and uses `ipywidgets` within a Google Colab notebook to create a UI. Users can select a book, chapter, and specific verses (or ranges), choose formatting options, and generate clean, ready-to-use text.

## Motivation

The original need arose from preparing Bible chapter narrations for a website using an animated character. A specific text-to-speech voice used for narrating Psalms was being discontinued, creating a deadline to generate as many narrations as possible. The inconsistent formatting from existing Bible software was a major bottleneck, prompting the creation of this automated formatting tool.

## Features

*   **Simple UI in Google Colab:** No local setup required beyond a Google account.
*   **Fetches KJV XML:** Downloads the specified OSIS XML file automatically.
*   **Book Selection:** Dropdown menu populated with all books found in the XML.
*   **Chapter Selection:** Dropdown menu dynamically updated based on the selected book.
*   **Flexible Verse Selection:**
    *   Select `all` verses.
    *   Select a single verse (e.g., `5`).
    *   Select a range (e.g., `1-10`).
    *   Select specific verses and ranges combined (e.g., `1, 3, 5-8, 12`).
*   **Formatting Options:**
    *   **Include Title:** Checkbox to optionally add "Book Chapter" (e.g., "Psalms 23") at the beginning.
    *   **Italics Style:** Choose how KJV added words (marked by `<transChange>` in the XML) are formatted:
        *   Markdown (`*italic*`)
        *   HTML (`<i>italic</i>`)
        *   Plain (remove italics)
    *   **Verse Separator:** Choose whether verses are separated by a blank line or a single newline.
*   **Formatted Output:** Displays the final text in a large text area, ready for copying.

## Requirements

*   A Google Account (for using Google Colab).
*   Internet connection (to download the XML and run Colab).
*   No external Python libraries need to be installed *within* the Colab environment; the script uses standard libraries (`requests`, `xml.etree.ElementTree`) and `ipywidgets` (which is pre-installed).

## How to Use

1.  Open Google Colab (<https://colab.research.google.com/>).
2.  Create a new notebook (File -> New notebook).
3.  Copy the entire Python script (`.py` file or the code block provided).
4.  Paste the code into a single cell in the Colab notebook.
5.  Run the cell (Click the Play button ▶️ or use Shift+Enter).
6.  The UI widgets will appear below the cell.
7.  **Click the "Load & Process XML" button.** Wait for the status message to change to "Status: Ready...". This might take several seconds as it downloads and parses the ~10MB XML file. Check the small output box below the button for processing details or errors.
8.  Use the dropdowns for "Book" and "Chapter".
9.  Enter the desired verses in the "Verses" text field.
10. Select your preferred formatting options using the checkboxes and radio buttons.
11. Click the "Generate" button.
12. The formatted text will appear in the "Output" text area. Select and copy the text as needed.

## Configuration Notes

The script includes configuration variables near the top:

*   `BIBLE_XML_URL`: The URL of the OSIS XML file.
*   `BOOK_ID_ATTR`, `CHAPTER_ID_ATTR`, `VERSE_ID_ATTR`: These specify which XML attributes are used to identify books, chapter markers, and verse markers. They are currently set based on the specific structure of the linked `eng-kjv.osis.xml` file. Modifying these might allow the script to work with other OSIS files, but compatibility is not guaranteed without potential code changes to the parsing logic (`fetch_and_populate_data_v8`).

## License

This project is licensed under the **MIT License**. See the `LICENSE` file for details. You are free to use, modify, and distribute this code, provided you include the original copyright notice and license file.

## Acknowledgements

*   The KJV OSIS XML file is sourced from the [open-bibles repository by seven1m](https://github.com/seven1m/open-bibles).
*   Designed by [Ivan](https://www.getivan.com), Made for [KJV Cards](https://www.kjv.cards).

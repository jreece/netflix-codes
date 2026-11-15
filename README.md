# Netflix Genre Code Browser

A single-page website for browsing Netflix genre codes. Search or filter to a category, open it on Netflix in a new tab, or copy its code.

No build step, no dependencies, no backend. It's one HTML file.

## Features

- **Search** by category name, group, or code
- **Filter** by group (Movies, Horror, TV shows, and so on)
- **Open ↗** launches `https://www.netflix.com/browse/genre/<code>` in a new tab
- **Copy** puts the code on your clipboard, with a "Copied ✓" confirmation
- Responsive layout, with automatic light and dark mode

## Usage

Open `netflix-codes.html` in any modern browser. You can double-click the file; there is nothing to install or serve.

To open a category, you need to be signed in to Netflix in the same browser.

## Adding or editing categories

All data lives in the `DATA` object at the top of the `<script>` block. Each group is a key, and each category is a `[name, code]` pair:

```js
const DATA = {
  "Movies": [
    ["Action & Adventure", 1365],
    ["Comedies", 6548]
  ],
  "My favorites": [
    ["Recently Added", 1592210]
  ]
};
```

- Add a new group by adding a new key. It appears automatically as a filter chip.
- Categories are sorted alphabetically within each group.
- Codes should be numeric.

## How it works

Netflix organizes its catalog with numeric genre IDs. Visiting `netflix.com/browse/genre/<code>` while signed in takes you to that category's page. This site is a searchable index of those IDs with a shortcut button for each one.

Copying uses the Clipboard API, with a fallback for browsers or contexts where it's unavailable.

## Notes

- Codes can vary by region, and a code that works in one country may return an error in another because of licensing.
- Netflix doesn't verify third-party code lists, and codes can be added or retired over time, so a code may stop working.
- This site collects no data, makes no network requests of its own, and stores nothing in your browser.

## Disclaimer

This is an independent project and is not affiliated with, endorsed by, or sponsored by Netflix. "Netflix" is a trademark of Netflix, Inc.

## License

Released under the [MIT License](LICENSE).

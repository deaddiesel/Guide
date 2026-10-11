# Themes &amp; Cursor Reference

Everything related to theming, chapter backgrounds and custom cursors: the full theme JSON schema, the color format, the cursor file format, and the priority chains.

- [Theme JSON Schema](#theme-json-schema)
- [Chapter Background](#chapter-background)
- [Color Format](#color-format)
- [Custom Cursors](#custom-cursors)
- [Icon &amp; Cursor URL Loading](#icon--cursor-url-loading)

---

## Theme JSON Schema

Every UI element is themeable via JSON. Custom themes live in `config/guide/themes/` — copy the template below, tweak the colors, and save it as a new file (for example, `my_theme.json`).

Two dedicated colors control both the Ctrl+F panel and the full-text overlay: `searchHighlightColor` (all matches) and `searchHighlightCurrentColor` (active match). Built-in palettes ship with tuned defaults per theme.

Each theme can also define its own **chapter background** — a solid color or an image that acts as a default for every book using this theme (see [Chapter Background](#chapter-background) for the full priority chain).

```jsonc
📄 Example standard.json (config/guide/themes/standard.json):

{
  "id": "standard", // unique theme identifier
  "displayName": "guide.theme.standard", // display name (plain string or translation key)
  "chapterBackground": { // optional chapter background override
    "type": "color", // "color" or "image"
    "value": "0x0A0A0A", // RGB color (0xRRGGBB) when type = "color"
    "alpha": 230 // 0 = transparent, 255 = opaque
  },
  "colors": {

    // ===== General UI =====
    "panelBackgroundColor": "0xCC1A1A1A", // panels background (book pages, side menus)
    "panelHeaderBackgroundColor": "0xCC111111", // panel header background
    "borderColor": "0xFF4A4A4A", // default border for panels and windows
    "borderFocusedColor": "0xFF00D0FF", // focused element border
    "textColor": "0xFFFFFF", // primary text color
    "textSecondaryColor": "0x888888", // secondary text
    "scrollbarTrackColor": "0x55111111", // scrollbar track background
    "scrollbarThumbColor": "0xFF8B8B8B", // scrollbar thumb
    "buttonColor": "0xFF2A2A2A", // default button
    "buttonHoverColor": "0xFF3A3A3A", // button on hover
    "buttonDisabledColor": "0xFF1A1A1A", // disabled button

    // ===== Input Fields =====
    "editBoxBackgroundColor": "0xFF000000", // input field background
    "editBoxBorderColor": "0xFFA0A0A0", // input field border
    "editBoxBorderFocusedColor": "0xFFFFFFFF", // input field border on focus
    "editBoxTextColor": "0xFFFFFF", // input field text

    // ===== Search Highlight (Ctrl+F + Full-Text Overlay) =====
    "searchHighlightColor": "0x80FFEB3B", // all match highlights
    "searchHighlightCurrentColor": "0xC0FF9800", // currently active match

    // ===== Media Player =====
    "mediaFrameOuterColor": "0xFF2D2D2D", // media outer frame
    "mediaFrameInnerColor": "0xFF4A4A4A", // media inner frame
    "mediaBackgroundColor": "0xFF000000", // playback area background
    "mediaControlPanelColor": "0xCC000000", // control panel background
    "mediaTextColor": "0xFFAAAAAA", // media player text
    "mediaErrorTextColor": "0xFFFF5555", // error text
    "mediaTimeTextColor": "0xFFCCCCCC", // playback time text
    "progressBarTrackColor": "0xFF555555", // progress bar track background
    "progressBarFillColor": "0xFF00D0FF", // progress bar fill
    "progressBarThumbColor": "0xFFFFFFFF", // progress bar thumb
    "progressBarThumbOutlineColor": "0xFF000000", // progress bar thumb outline

    // ===== Inline Elements =====
    "spoilerTitleColor": "0xFFAA00", // spoiler title
    "inlineItemBackgroundColor": "0x550A0A0A", // inline item background
    "inlineItemBorderColor": "0x25FFFFFF", // inline item border
    "inlineItemTextColor": "0xFFAAAAAA", // inline item text
    "soundButtonBackgroundColor": "0xFF2E2E2E", // sound button background
    "soundButtonBorderColor": "0xFF5A5A5A", // sound button border
    "soundButtonTextColor": "0xFFFFFF", // sound button text
    "questStrikethroughColor": "0x77777777", // strikethrough quest text

    // ===== Tables =====
    "tableHeaderBackgroundColor": "0xFF222222", // table header background
    "tableHeaderTextColor": "0xFFAA00", // table header text
    "tableRowBackgroundColor": "0x11000000", // alternating row background
    "tableBorderColor": "0xFF3A3A3A", // table borders
    "tableCellTextColor": "0xFFFFFF", // table cell text
    "dividerColor": "0xFF3A3A3A", // block dividers

    // ===== Video Title =====
    "videoTitleBackgroundColor": "0xCC2D2D2D", // video title panel background
    "videoTitleBorderColor": "0xFF5A5A5A", // video title panel border
    "videoTitleTextColor": "0xFFFFFF", // video title text

    // ===== Warnings & Toasts =====
    "warningTextColor": "0xFF5555", // primary warning text
    "warningTextSecondaryColor": "0xFFAAAAAA", // secondary warning text
    "toastBackgroundColor": "0xD0101215", // toast notification background
    "toastTextColor": "0xFFFFFF", // toast notification text

    // ===== Structure Panel =====
    "structureFrameColor": "0x4000FFFF", // 3D structure preview frame
    "structureTabActiveBackgroundColor": "0xFF555555", // active tab background
    "structureTabInactiveBackgroundColor": "0xFF222222", // inactive tab background
    "structureTabActiveTextColor": "0x00FFCC", // active tab text
    "structureTabInactiveTextColor": "0x888888", // inactive tab text
    "structureLayerTextColor": "0x55FF55", // structure layer label

    // ===== Placement Projector =====
    "projectorPanelBackgroundColor": "0xD0101215", // projector panel background
    "projectorPanelBorderColor": "0x4000D0FF", // projector panel border
    "projectorTitleTextColor": "0x00D0FF", // projector panel title
    "projectorButtonBackgroundColor": "0x15FFFFFF", // default button background
    "projectorButtonHoverBackgroundColor": "0x3000D0FF", // button background on hover
    "projectorButtonBorderColor": "0x25FFFFFF", // default button border
    "projectorButtonHoverBorderColor": "0xFF00D0FF", // button border on hover
    "projectorButtonTextColor": "0xBBBBBB", // button text
    "projectorButtonHoverTextColor": "0xFFFFFF", // button text on hover
    "projectorDoneButtonHoverBackgroundColor": "0x3000FF55", // "Done" button background on hover
    "projectorDoneButtonHoverBorderColor": "0xFF00FF55", // "Done" button border on hover
    "projectorCancelButtonHoverBackgroundColor": "0x30FF2244", // "Cancel" button background on hover
    "projectorCancelButtonHoverBorderColor": "0xFFFF2244", // "Cancel" button border on hover
    "projectorHudTextColor": "0xFFFFFF" // projector HUD hint text
  }
}
```

---

## Chapter Background

Backgrounds can be set in two places, and they work by priority chain:

1. **Player customization** (`customization.json.background.<book>`) — set in the in-game Background tab. Wins over the theme.
2. **Theme default** (`theme.chapterBackground`) — set by the theme author. Used for any book using this theme if the player has no override.
3. **Built-in default** — blur on NeoForge, gradient overlay on Forge.

### Setting a default from a theme

Add a `chapterBackground` block to your theme JSON to give every book using this theme a default background. Three source types are supported:

```jsonc
// Solid color with alpha (0 = transparent, 255 = opaque)
"chapterBackground": {
  "type": "color",
  "value": "0x1A0F2E",
  "alpha": 230
}

// Local or server-side image (resolved against the current book folder)
"chapterBackground": {
  "type": "image",
  "path": "textures/bg/my_bg.png"
}

// Direct URL (downloaded in background, cached on disk)
"chapterBackground": {
  "type": "image",
  "path": "https://example.com/background.jpg"
}
```

> **Note:** Omit `chapterBackground` entirely to keep the built-in default. URL images appear with a short delay on first load; subsequent openings use the cache. Supports PNG, JPEG, BMP and GIF (first frame).

### Player override

Players can override the theme background per book through **Interface Customization → Background**. Three modes are available:

- **Color** — HSV picker + alpha slider + hex input + live preview.
- **File** — pick an image from `config/guide/user/backgrounds/`.
- **URL** — download an image from any HTTP(S) link; cached after Apply.

The override is stored in `config/guide/user/customization.json` as `background.<book>` and always takes priority over the theme default. Pressing **Reset** in the Background tab clears the override and returns to the theme background.

### Where backgrounds are stored

| Source | Location |
|---|---|
| Local file (via File mode) | `config/guide/user/backgrounds/` |
| URL (via URL mode) | `config/guide/cache/media/` (auto-managed) |
| Theme default (local image) | `<book_folder>/textures/bg/<file>.png` |
| Theme default (server image) | Same path, resolved against the server-side book folder |

---

## Color Format

Colors are written in `0xAARRGGBB` format:

| Channel | Range | Description |
|---|---|---|
| `AA` | `00` – `FF` | Alpha channel (transparency). `FF` = fully opaque, `00` = fully transparent |
| `RR` | `00` – `FF` | Red channel |
| `GG` | `00` – `FF` | Green channel |
| `BB` | `00` – `FF` | Blue channel |

> **Tip:** Set alpha below `FF` (e.g. `80`) to make panels semi-transparent.

---

## Custom Cursors

A book can force its own cursor, ignoring the player's choice. Five optional fields in `book.json`:

```json
{
  "cursor": "crosshair.png",
  "cursor_selector": "arrow.png",
  "cursor_diary": "pen.png",
  "cursor_scale": 2,
  "cursor_hotspot": "center"
}
```

| Field | Description |
|---|---|
| `cursor` | Cursor for the main book screen (`GuideScreen`) |
| `cursor_selector` | Cursor for the book selector screen |
| `cursor_diary` | Cursor for the diary |
| `cursor_scale` | `1`–`4`, or `0` (do not force, use UI) |
| `cursor_hotspot` | `"center"` or `"x,y"` (e.g. `"8,8"`). Empty = use UI |

The filename is just the name, no path and no `user:` prefix. The mod looks for it in `config/guide/user/cursors/`. Supported: PNG, JPG, JPEG, BMP.

### Priority chain

When opening book `X`, the system walks this chain:

1. `book.json(X).cursor` — if set, used.
2. `customization.json` → `cursor.X` — the player's choice for this book.
3. `customization.json` → `cursor._global` — the global player choice.
4. Standard Minecraft cursor.

Same for `cursor_selector` (selector) and `cursor_diary` (diary). Scale and hotspot use the same chain.

### Storage folder

Cursor files live in `config/guide/user/cursors/`. Filename can be anything. Extensions: `.png`, `.jpg`, `.jpeg`, `.bmp`. Canvas size can be anything — the cursor is not cropped or resized automatically. If the image is bigger than needed, use the scale.

### Scale &amp; hotspot

Open **Interface Customization → Cursor**. The `[1×]` button cycles scale: `1× → 2× → 3× → 4× → 1×`. Scaling uses **nearest-neighbor** — pixels stay crisp, no blurring. The setting is saved per book.

The tab has a `[X] Center` checkbox:

- On — the click point is placed at the center automatically.
- Off — you can enter X and Y in pixels of the original image.

Values are saved on the fly — nothing is lost when the screen closes.

### Technical notes

- **Rendering:** native GLFW — the cursor is registered when the screen opens and freed when it closes.
- **Isolation:** if the file is missing — standard cursor, no crash.
- **Hotspot:** for large scales, coordinates are multiplied automatically so the click point matches the visual position.
- **Leaks:** cursor is destroyed via `glfwDestroyCursor` in the screen's `removed()`.

---

## Icon &amp; Cursor URL Loading

Both the Icon and Cursor tabs in the in-game customization editor ship with a URL field and a **Download** button.

1. Paste a direct image link (`https://...`). The link must point to a file, not to a viewer page.
2. Press **Download**. The file is downloaded into the matching user folder and applied immediately.
3. The filename will be `url_<hash>.png` — the system will not download the same image twice.

All formats supported by `MediaDownloadManager` work: PNG, JPG, JPEG, GIF, BMP.

> **Important:** the server must return the raw image bytes. Viewer pages (e.g. `imgur.com/xxxx` without `i.` and without an extension) do not work — those return HTML, and the mod will say "Not an image". For Imgur, use a link like `https://i.imgur.com/xxxx.png`.

### Where do downloaded files land?

| Tab | Folder |
|---|---|
| Icon | `config/guide/user/icons/` |
| Cursor | `config/guide/user/cursors/` |
| Background | `config/guide/user/backgrounds/` |

Files are permanent — they are not re-downloaded on every game start. Deleting a file from disk removes it from the tab on next **Refresh**.

# Merge Request: Telegram Direct Uploader, Dynamic Quality Picker, Merging Phase Badge & System Enhancements

## Summary

This merge request introduces the **Telegram Direct Uploader & Leech Bot module**, **Dynamic YouTube Quality Picker**, **Explicit Merging Phase Badge with Smooth ETA**, **Quick Header Bandwidth Control**, **Interactive Clipboard Detection Toast**, and **System Dependency Auto-Detection** into OmniGet.

---

## 🚀 Key Highlights & Added Features

### 📲 1. Telegram Direct Uploader & Leech Bot (`feat(telegram)`)
- **Dual Authentication Modes**: Upload media via **User Session** (active MTProto session) or **Bot Token** (`123456:ABC-DEF...`).
- **Chat ID & Username Normalization**: Seamlessly handles numeric Chat IDs (`123456789`, `-100123456789`), `@channel_usernames`, and `https://t.me/` links.
- **Media Mode Selector**: Upload as **Video (Streamable)**, **Document / File** (raw uncompressed), or **Audio Track**, with automatic extension matching.
- **Custom Filename & Extension Editor**: Rename files or change format extensions before uploading.
- **Custom Thumbnail Picker**: Select custom cover artwork (`.jpg`/`.png`) from disk.
- **Telegram Limits & Auto-Chunking**: Supports **Free Tier (2.0 GB max)** and **Premium Tier (4.0 GB max)** presets with automatic chunking preview for large files.
- **Action Button**: Direct **"Send to Telegram"** action button on completed items in `Downloads` page.
- **Smart Error Diagnostics**: Translates raw Telegram API errors into actionable steps (e.g. *bot not started by user*, *bot not added as admin*, *chat not found*, *50MB Bot API limit*).

### 🎬 2. Dynamic YouTube Quality Picker (`feat(omnibox)`)
- Dynamically extracts available heights from real yt-dlp format data (`4K 2160p`, `2K 1440p`, `1080p`, `720p`, `480p`, `360p`, `Audio only`).
- Automatically hides resolutions higher than what the video possesses.

### ⚡ 3. Merging Phase Indicator & Smooth ETA (`feat(downloads)`)
- Detects `[Merger]`, `[ffmpeg]`, `[FixupM3u8]`, and `[VideoConvertor]` stdout lines from yt-dlp to show a clear `"Merging audio & video..."` status badge instead of hanging at ~99%.
- Displays styled ETA badge (`ETA ~3m 20s`) alongside download speed counter.

### 🚀 4. Header Bandwidth Control / Speed Limiter (`feat(settings)`)
- Quick Bandwidth Control dropdown (*Unlimited, 1 MB/s, 2 MB/s, 5 MB/s, 10 MB/s*) directly in the Downloads page header bar, passing `--limit-rate` to yt-dlp.

### 📋 5. Interactive Clipboard Detection Toast (`feat(clipboard)`)
- Interactive toast notification when a video link is detected on clipboard, prefilling the omnibox and navigating to home view in one click.

### 🔧 6. System Dependency Detection (`feat(settings)`)
- Detects system-installed `yt-dlp`, `FFmpeg`, and `PDFium` binaries with source badges (`PATH`, `Managed`, `Flatpak`) and absolute executable paths in Settings.

### 📂 7. Open Folder Action Button (`feat(downloads)`)
- One-click folder reveal button (`reveal_file`) on completed items.

---

## 📜 Git Commit Log

```text
e0a82890 style(telegram): UX polish, focus-visible outline rings, ESC listener, and mobile responsiveness
cd726f0f feat(telegram): smart Telegram API error translation for bot start & channel admin issues
b50c63e7 feat(telegram): SendAs mode selector and edge case guards for Telegram Leech Bot
865a96d6 feat(telegram): Telegram Direct Uploader & Leech Bot module
e052eab6 feat(clipboard): interactive toast banner when video link detected on clipboard
0917ff5e feat(settings): quick speed limiter controls in downloads header and settings
11bb7125 feat(downloads): explicit merging phase badge and smooth ETA display
267fc21d fix(i18n): remove UTF-8 BOM from locale files for clean JSON parsing
deeadf5f feat(downloads): add open folder button for completed items
23849540 feat(settings): system dependency detection and source indicator
62936711 feat(omnibox): dynamic quality pills from real yt-dlp format data
914fb754 fix: restore scrolling on downloads page
```

---

## 🧪 Verification & Testing

- ✅ **Locale JSON Validation**: All 10 locale files verified for valid JSON syntax and 100% key presence.
- ✅ **TypeScript Type Safety**: All i18n keys and TS types checked without errors.
- ✅ **Real-world Edge Case Testing**: Verified Chat ID normalization, SendAs auto-detection, Bot Token regex validation, and Free/Premium chunk math.

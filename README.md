# 🎙️ Transcriptor

**Native, 100% offline audio & video transcription — for macOS and Windows.**

Drop a file, pick a model and language, transcribe, review, and export. No cloud, no accounts, no telemetry — your audio never leaves your machine.

> This repository hosts the **installers only**. Every release is published here; grab the latest below.

---

## ⬇️ Download

Get the latest installer from the **[releases page](https://github.com/ultramenid/transcriptor-dist/releases/latest)**. **ffmpeg/ffprobe are bundled** — you don't need to install anything else, and Whisper models download on demand the first time you transcribe.

| Platform | File | Requirements |
| -------- | ---- | ------------ |
| macOS — Apple Silicon | `Transcriptor_<version>_aarch64.dmg` | macOS 11+, M1/M2/M3/M4 |
| macOS — Intel | `Transcriptor_<version>_x64.dmg` | macOS 11+, Intel (CPU-only) |
| Windows | `Transcriptor_<version>_x64-setup.exe` or `_x64_en-US.msi` | Windows 10/11, 64-bit |

---

## 💿 Install

### macOS

1. Open the `.dmg` and drag **Transcriptor** into your **Applications** folder.
2. The first launch fails with **"Transcriptor is damaged and can't be opened."** It isn't damaged — the app isn't notarized by Apple, and macOS blocks unnotarized apps. Clear the quarantine flag once, in **Terminal**:
   ```bash
   xattr -cr /Applications/Transcriptor.app
   ```
3. Double-click **Transcriptor** in Applications. It opens normally from then on.

> **Intel Macs transcribe on the CPU.** whisper.cpp's Metal backend is Apple-Silicon only, so expect it to be several times slower than an M-series Mac — drop to a smaller model if it drags.

### Windows

1. Run the `.exe` or `.msi` installer — either works.
2. SmartScreen may warn **"Windows protected your PC."** Click **More info → Run anyway**; the installer is unsigned, which is what triggers the warning.
3. Launch **Transcriptor** from the Start menu.

---

## ✨ What it does

- **Fully offline.** Everything runs on-device. The only network traffic is an optional, user-initiated model download from HuggingFace.
- **Accurate on real audio.** Whisper models from `tiny` to `large-v3` (default: `large-v3-turbo`), with GPU acceleration via Metal (Apple Silicon) or CUDA/Vulkan (Windows) and a CPU fallback.
- **Video & audio.** ffmpeg extracts the audio track to a 16 kHz mono WAV; the temp file is always cleaned up, done or cancelled.
- **Per-file model & language.** Set a default, override per file. Re-run individual segments without reprocessing the whole file.
- **Custom models.** Bring your own Whisper-format `.bin` model.
- **Live progress.** Streaming transcription progress — no frozen UI.
- **Library & search.** Local SQLite database with full-text search. Recents, library, and queue are views of one store.
- **Exports.** TXT, SRT, VTT, JSON, or Article — regenerated on demand, always in sync.
- **No limits.** A four-hour file transcribes end to end. Nothing is capped, chunked away, or metered.

---

## 🔒 Privacy

No cloud, no accounts, no telemetry, no analytics. Your audio, transcripts, and library never leave your disk. The app makes exactly two network requests, both under your control: downloading a model when you pick one, and checking whether a newer version exists on launch — which you can switch off in Settings.

---

## Updates

Transcriptor checks this repository for new versions and can update itself in place. Only the current release is kept here; older builds are removed.

---

Source code is private. Issues and questions: [open an issue](https://github.com/ultramenid/transcriptor-dist/issues).

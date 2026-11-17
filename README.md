# PDF PLUS — PDF Maker Plus

**PDF PLUS** (`com.pdfplus.maker`) is a native Android PDF studio crafted with **Kotlin**, **Jetpack Compose**, and **Material 3**, featuring a luxury dark obsidian glassmorphism interface, smooth animations, bilingual **English & Bengali (বাংলা)** localization, and real offline PDF processing.

## Key Features

### 12 Real On-Device PDF Tools
1. **Image to PDF** — Zero-permission Android Photo Picker, photo reordering, A4 / Letter / Fit sizing, margins, and orientation.
2. **Text to PDF** — Bilingual English & Bengali text editor with multi-page pagination, font sizing, mono mode, and paper themes.
3. **Merge PDF** — Combine multiple PDFs from your Vault or device storage in any custom order via Apache PDFBox.
4. **Split PDF** — Tap individual page thumbnails, specify page ranges (`1-3, 5`), or split every *N* pages.
5. **Compress PDF** — Three smart DPI/JPEG compression presets with exact before/after size comparison.
6. **PDF Scanner** — Live CameraX document viewfinder with flash toggle, zero-permission gallery fallback, Magic Color / Crisp B&W / Grayscale filters, and 90° rotation.
7. **PDF Viewer** — High-resolution `PdfRenderer` viewing, pinch-to-zoom, page scrubber, and Night Reading invert mode.
8. **PDF Editor** — Rotate individual pages 90°, reorder pages, and delete pages with real PDFBox persistence.
9. **PDF to Image** — Export selected PDF pages to lossless PNG or JPEG directly to `Pictures/PDF PLUS` via `MediaStore`.
10. **Word to PDF** — Native OOXML `.docx` (`word/document.xml`) and `.txt`/`.md` parser with editable preview and styled PDF export.
11. **Add Signature** — Smooth vector drawing pad with ink color selection, page picker, and placement/size controls.
12. **Add Watermark** — English & Bengali custom watermark stamping with opacity, angle, color, size, and Center/Tiled/Footer modes.

### File Vault & Settings
- **My Files & Favorites** — Room-backed private PDF vault with search, category filters, rename, delete confirmation, `FileProvider` sharing, and Storage Access Framework (SAF) export/download.
- **Themes & Languages** — Obsidian Dark / Platinum Light modes, 3 accent themes (Obsidian Violet, Sapphire Cyan, Royal Gold), and instant English / বাংলা switching persisted via DataStore.

## Project Structure
```
app/src/main/java/com/example/
├── PdfPlusApplication.kt        # PDFBox & Room initialization
├── MainActivity.kt              # Edge-to-edge Compose host & Navigation Compose
├── navigation/Routes.kt         # @Serializable type-safe destinations
├── localization/AppStrings.kt   # Bilingual English & Bengali strings
├── data/
│   ├── local/                   # Room Entity, DAO, AppDatabase
│   ├── pdf/PdfEngine.kt         # Native PdfDocument, PdfRenderer, PDFBox & DOCX engine
│   ├── prefs/SettingsRepository.kt
│   └── repository/PdfRepository.kt
├── viewmodel/MainViewModel.kt   # StateFlow reactive state management
└── ui/
    ├── theme/                   # Color, Type (bundled Google Fonts), Theme
    ├── components/              # Glassmorphism cards, Aurora BG, Floating Bottom Bar
    └── screens/                 # Splash, Home, Tools, Files, Settings & 12 tool screens
```

## Google Play Store Readiness
- **Application ID**: `com.pdfplus.maker`
- **Target / Compile SDK**: API 36 (`minSdk = 24`)
- **Minimal Permissions**: Uses Android Photo Picker & Storage Access Framework (`OpenDocument` / `CreateDocument`) with zero broad storage permissions (`READ_EXTERNAL_STORAGE` / `READ_MEDIA_IMAGES` omitted). `CAMERA` permission is requested at runtime only for live document scanning.
- **Adaptive Icon**: Custom adaptive launcher icon + all density PNGs (`mdpi`–`xxxhdpi`).
- **Release Bundle**: Build signed Android App Bundle via `./gradlew bundleRelease` or `gradle :app:bundleRelease` (configured with ProGuard/R8 rules in `app/proguard-rules.pro`).

## Build & Test
```bash
gradle :app:assembleDebug
gradle :app:testDebugUnitTest
```


## Build a debug APK with GitHub Actions

1. Upload the **contents** of this project folder to the root of your GitHub repository (do not upload only the ZIP file).
2. Confirm that `settings.gradle.kts`, `gradlew`, `gradle/`, and `app/` are visible at the repository root.
3. Open **Actions** → **Build PDF Plus APK** (or **Build Android APK**) → **Run workflow**.
4. When the run succeeds, open the run and download the `PDF-PLUS-debug-apk` artifact.

The workflow installs Android SDK Platform 36 and Build Tools 36.0.0, uses JDK 17 and the Gradle 9.3.1 wrapper, creates a temporary debug keystore, and uploads the debug APK. A successful workflow run is required before an APK is available.

# Compositor (macOS 14+ Port)

> [!NOTE]
> **About this fork:** This is a fork of [Robbie Tilton's Compositor](https://github.com/robbietilton/Compositor), backported and adapted to run natively on **macOS 14.6+ (Sonoma)** as well as macOS 15+ (Sequoia). The upstream version requires macOS 26.5+. This fork adapts macOS 15-exclusive APIs (such as window placement APIs) and adds localization support.

---

Adobe Photoshop costs too much and tools like GIMP don’t feel familiar enough for me to stay in flow. That’s why Compositor was built.

The goal was to create a full-featured image editor that is completely free and open source. If you use Photoshop for compositing and post-processing, Compositor is built around that workflow — with the tools needed to create a pixel-perfect final image.

Because it’s open source, you can download the Xcode project and add, remove, or modify any feature to fit your workflow.

## Changes in this Fork

- **macOS 14+ Compatibility:** Backported deployment target to macOS 14.6 (Sonoma) by replacing macOS 15-only SwiftUI/AppKit APIs with backwards-compatible implementations.
- **Localization:** Added multi-language support (including Simplified Chinese `zh-Hans`).
- **UI & Compatibility Tweaks:** Ensured stable operation across macOS 14 and macOS 15.

## Features

### Layers
- Layers and folders, with blend modes and opacity
- Layer masks: paint, fill, invert, blur and feather them; link or unlink them to transform a mask on its own
- Clipping masks and folder masks
- Adjustment layers: Hue/Saturation, Levels, Curves, Exposure, Gradient Map and Grain
- Merge Down, Merge Layers and Merge Group (⌘E)
- Duplicate, rename inline, reorder and nest by drag and drop; Option-drag to duplicate
- Drag layers between open projects

### Transform
- Non-destructive move, scale, rotate and flip — images keep their full resolution however small you make them
- Free distort (⌘-drag a handle), with Shift to lock to an axis
- Transform several layers, or a whole folder, together
- Snapping to canvas and layer edges and centers, with guides
- Exact values for position, size, scale and angle, stepped with the arrow keys
- Flip Layer and Flip Canvas, horizontal and vertical

### Selections
- Rectangle and Ellipse Marquee, Freehand and Polygonal Lasso, and Magic Wand
- Add to and subtract from selections, move the outline, or move and duplicate the pixels inside
- Load a layer's pixels or a mask as a selection
- Content-Aware Fill, which can also extend an image past its edges

### Painting and retouching
- Brush with size, hardness and opacity, and Shift for straight lines
- Spot Healing Brush (content-aware)
- Clone Stamp, aligned or not, sampling one layer or all of them
- Blur tool, on pixels or masks
- Gradient tool and Shape tool (rectangles, rounded rectangles and ellipses)
- Type tool (T): inline multiline editing in draggable, resizable paragraph boxes; font, size, color, alignment and spacing in the tool header; transform text and use it as a clipping mask
- Eyedropper and a full color picker

### Adjustments and filters
- Levels (with Auto), Curves, Hue/Saturation, Exposure, Gradient Map, Grain and Invert
- Gaussian Blur and Motion Blur that spread past a layer's edges
- Add Noise, Lens Correction and Remove Background
- Live previews, limited to the selection when there is one

### Canvas and files
- Multiple projects in tabs
- Crop with snapping, and Option for symmetric cropping
- Canvas Size and Image Size
- Sharp high-quality downsampling when zoomed out, and a pixel grid when zoomed in
- Import JPEG, PNG, HEIC and TIFF — including dropped screenshots and images from other apps
- Export JPEG with a live preview (⇧⌥⌘S); Copy Merged
- Photoshop-style keyboard shortcuts throughout

## Requirements

- **macOS:** macOS 14.6 (Sonoma) or later
- **Xcode:** Xcode 15.0+ or Xcode 16+ (to build from source)

## Building

1. Clone this repository:
   ```bash
   git clone https://github.com/Assim-Genshi/Compositor-for-14-.git
   ```
2. Open `Compositor.xcodeproj` in Xcode.
3. Select the **Compositor** scheme and choose **My Mac** as the destination.
4. Press `⌘R` to build and run.

## Releasing

`scripts/release.sh` builds a Release version, signs it with Developer ID, notarizes and staples it, and packages it into `dist/Compositor-<version>.dmg`.

It needs, all kept outside this repository:

- a **Developer ID Application** certificate in the login keychain
- notarization credentials saved with `xcrun notarytool store-credentials "compositor-notary" …`
- [`create-dmg`](https://github.com/create-dmg/create-dmg) (`brew install create-dmg`)

## Credits & Upstream

- Original project and concept by **[Robbie Tilton](https://github.com/robbietilton)** ([robbietilton/Compositor](https://github.com/robbietilton/Compositor)).
- macOS 14 backport and enhancements maintained by [Assim Genshi](https://github.com/Assim-Genshi).

## License

MIT — see [LICENSE](LICENSE).

<p align="center">
  <img src="https://raw.githubusercontent.com/lmo-shed/lmo/main/assets/icon.svg" width="80" alt="LMO" />
</p>

<h1 align="center">LMO</h1>
<p align="center"><strong>Label Management & Operations</strong></p>
<p align="center">Desktop image annotation tool for computer vision</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Linux%20%7C%20Windows-blue" alt="Platform" />
  <img src="https://img.shields.io/badge/Electron-41-47848F?logo=electron&logoColor=white" alt="Electron" />
  <img src="https://img.shields.io/github/v/release/lmo-shed/lmo?include_prereleases&label=Release" alt="Release" />
  <img src="https://img.shields.io/badge/License-Non--Commercial-orange" alt="License" />
</p>

<p align="center">
  <a href="https://github.com/lmo-shed/lmo/releases"><strong>Download</strong></a>
</p>

---

## Overview

LMO is a lightweight desktop labeling tool built with Electron. Create bounding boxes, polygons, and keypoints with skeleton — import and export in COCO, CVAT, and YOLO formats.

---

## Features

### Annotation
| Tool | Description |
|------|-------------|
| **BBox** | Click & drag, resize handles, arrow key nudge |
| **Polygon** | Vertex placement, edge insert, right-click delete |
| **Keypoint** | Per-class templates with skeleton, multi-select drag |
| **SAM** | Interactive point-click segmentation (NVIDIA GPU) |

### Workflow
- Undo / Redo (`Ctrl+Z` / `Ctrl+Y`)
- Copy / Paste with offset (`Ctrl+C` / `Ctrl+V`)
- Multi-select (`Ctrl+Click`, `Shift+Click`)
- Label lock — prevent accidental edits (`L`)
- Image tags — Notion-style multi-select with auto-complete

### Data
- **Project → Dataset** structure with roles (train / val / test)
- **Import**: COCO, CVAT XML, YOLO, images, video frames
- **Export**: COCO, CVAT XML, YOLO → `annotations/` folder
- Move images between datasets with labels
- Filesystem sync detection

### UI
- Dark / Light / System theme
- Canvas background color (adjustable)
- Customizable keyboard shortcuts
- Statistics dashboard (class distribution, progress, tags)
- Tag-based image filtering

---

## Download

Get the latest build from [**Releases**](https://github.com/lmo-shed/lmo/releases).

| Platform | File | Note |
|----------|------|------|
| Linux | `.deb` | Ubuntu / Debian |
| Windows | `.exe` | NSIS installer |

---

## Quick Start

1. **Download & install** from Releases
2. **Create a project** — select a folder
3. **Create a dataset** — give it a name
4. **Import images** — drag & drop, import from folder, or extract video frames
5. **Start labeling** — click an image to open the annotation view

---

## SAM Interactive Setup

Point-click segmentation powered by ONNX Runtime. Requires **NVIDIA GPU + CUDA**.

### Prepare model

Download SAM ONNX models (e.g. from [HuggingFace](https://huggingface.co/models?search=sam2+onnx)) and zip them:

```
sam_models.zip
├── vision_encoder_fp16.onnx
├── vision_encoder_fp16.onnx_data
├── prompt_encoder_mask_decoder_fp16.onnx
└── prompt_encoder_mask_decoder_fp16.onnx_data
```

### Load in LMO

**Settings** → **SAM Interactive** → **모델 업로드 (.zip)** → select zip → done.

Press **C** in labeling view to activate SAM mode.

> SAM will not work on CPU-only or Mac environments.

---

## Keyboard Shortcuts

All shortcuts are customizable in **Settings**.

| Key | Action | Key | Action |
|-----|--------|-----|--------|
| `V` | Select | `Ctrl+Z` | Undo |
| `B` | BBox / Polygon | `Ctrl+Y` | Redo |
| `K` | Keypoint | `Ctrl+C/V` | Copy / Paste |
| `C` | SAM | `Ctrl+A` | Select all |
| `H` | Toggle labels | `Delete` | Delete selected |
| `T` | Toggle names | `Arrow` | Move 1px |
| `L` | Lock label | `Shift+Arrow` | Move 10px |
| `F` | Fit to screen | `Space+Drag` | Pan |
| `G` | Image list | `Scroll` | Zoom |

---

## Supported Formats

| | Import | Export |
|---|--------|--------|
| **COCO** | `*.json` + images | `annotations/coco.json` |
| **CVAT** | `annotations.xml` + images | `annotations/annotations.xml` |
| **YOLO** | `data.yaml` + images/labels | `annotations/labels/*.txt` + `data.yaml` |
| **Image** | jpg, png, bmp, webp | — |
| **Video** | mp4, avi, mov, mkv, webm | frame extraction via ffmpeg |

Keypoint data is preserved across all formats.

---

## Requirements

| Feature | Requires |
|---------|----------|
| Labeling | Nothing — works offline |
| SAM Interactive | NVIDIA GPU + CUDA driver |
| Auto Labeling | Docker |
| Video frames | ffmpeg |

---

## License

This software is distributed under a **non-commercial license**.

- Free to use, modify, and distribute
- Selling the software itself or commercial redistribution is prohibited
- Outputs produced using the software (e.g. labeled data) may be used commercially

See [LICENSE](LICENSE) for details.

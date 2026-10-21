# ProShow-Converter
An open-source software to convert Photodex ProShow Producer (.psh) projects into PTE AV Studio (.pte), FilmCraft (.fcproj), NCH VideoPad Professional (.vpj) and other NLE formats.

# About the project

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python Version](https://img.shields.io/badge/python-3.10%2B-blue.svg)](https://www.python.org/)

**ProShow-Converter** is an open-source Python tool and graphical utility designed to parse, convert, and migrate legacy Photodex **ProShow Producer** (`.psh`) project files into modern, active slideshow and non-linear editing (NLE) project formats—such as **PTE AV Studio Pro** (`.pte`), **FilmCraft** (`.fcproj`), **NCH VideoPad Professional** (`.vpj`) and so on.

Following the shutdown of Photodex activation servers, many creators were left unable to easily run or edit their long-standing `.psh` projects without costly recurring subscriptions. **ProShow-Converter** solves this by providing a clean, standalone, and free solution to keep your slideshow projects fully editable.

---

## Key Features

- **Full Project Parsing:** Reads key structures from `.psh` project files, including slides, image/video paths, audio tracks, keyframes, transitions, and timing.
- **Multi-Format Export:** Extensible plugin system to export `.psh` data into multiple target NLE project formats.
- **Cross-Platform & Lightweight:** Built in pure Python, running seamlessly on Windows, macOS, and Linux.
- **User-Friendly GUI & CLI:** Features an intuitive graphical interface for batch converting projects, alongside a command-line interface for automation.
- **Open-Source & Lifetime Free:** Released under the MIT License—no subscriptions, no telemetry, no lock-in.

---

## Supported Formats

| Format | File Extension | Status | Description |
| :--- | :--- | :--- | :--- |
| **ProShow Producer** | `.psh` | **Input** | Legacy Photodex project files |
| **PTE AV Studio Pro** | `.pte` | **Output** | Full keyframe, slide, and audio structure mapping |
| **FilmCraft** | `.fcproj` | **Output** | Native XML/JSON project format export |
| **Generic NLE (EDL/XML)** | `.xml` / `.edl` | *Planned* | Broad compatibility for DaVinci Resolve / Premiere |

---

## System Architecture

**ProShow-Converter** follows a modular **Model-View-Controller (MVC)** design with an **Intermediate Representation (IR)** layer to ensure decoupled parsing and multi-target exporting:

```
┌─────────────────────────┐
│   ProShow Project File  │
│        (*.psh)          │
└────────────┬────────────┘
             │
             ▼
┌─────────────────────────┐
│       PSH Parser        │ ── Extracts slides, timing, keyframes, audio
└────────────┬────────────┘
             │
             ▼
┌─────────────────────────┐
│  Intermediate Rep. (IR) │ ── Normalized data model (Python Object Model)
└────────────┬────────────┘
             │
      ┌──────┴────────────────────────┐
      │                               │
      ▼                               ▼
┌──────────────┐             ┌────────────────┐
│ PTE Generator│             │ FilmCraft Gen. │
│   (*.pte)    │             │   (*.fcproj)   │
└──────────────┘             └────────────────┘
```

---

## Getting Started

### Prerequisites

- **Python 3.10** or higher
- **Git**

### Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/YourUsername/ProShow-Converter.git
   cd ProShow-Converter
   ```

2. **Create a virtual environment (recommended):**
   ```bash
   python -m venv venv
   # On Windows:
   venv\Scripts\activate
   # On macOS/Linux:
   source venv/bin/activate
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

---

## Usage

### Launching the Graphical Interface (GUI)

To start the user-friendly conversion window:

```bash
python -m proshow_converter.gui
```

### Using the Command Line Interface (CLI)

To convert a single `.psh` file directly from the terminal:

```bash
# Convert to PTE AV Studio
python main.py convert path/to/project.psh --target pte --output path/to/project.pte

# Convert to FilmCraft
python main.py convert path/to/project.psh --target filmcraft --output path/to/project.fcproj
```

---

## Project Structure

```text
ProShow-Converter/
├── proshow_converter/
│   ├── __init__.py
│   ├── parser.py          # PSH text file parser
│   ├── models.py          # Intermediate Representation (IR) data classes
│   ├── generators/        # Export plugins for target formats
│   │   ├── __init__.py
│   │   ├── pte_gen.py     # Generator for PTE AV Studio (.pte)
│   │   └── fc_gen.py      # Generator for FilmCraft (.fcproj)
│   └── gui/               # GUI application modules
│       ├── __init__.py
│       └── app.py
├── tests/                 # Unit tests and sample files
├── main.py                # CLI Entry point
├── requirements.txt
├── LICENSE
└── README.md
```

---

## Contributing

Contributions are very welcome! Whether you want to add a new target export plugin, improve the `.psh` parsing logic, or polish the user interface:

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request


## Just two cents...

I know how I work: if you find this project useful and/or you are an orphan of ProShow Producer desperately looking for a way to get your projects back onto a timeline ready for editing, please let me know! 

The key to everything is motivation — if the project doesn't generate interest, it's very easy for it to remain incomplete.

---

## License

Distributed under the **MIT License**. See `LICENSE` for more information.

**NFC Card Reader**

A clean, simple, cross-platform Python app for reading NFC cards and managing card data.

**What this project is**: A lightweight desktop utility that reads NFC card data (via supported readers), displays card details, and helps export or manage card info. The project is packaged into a standalone executable for distribution (see the `build/` and `dist/` folders).

**Contents**
- **Description:** What the app does and who it's for.
- **Quick Start:** Run a prebuilt executable or run from source.
- **Build:** How to create distributable packages (PyInstaller).
- **Usage:** Screenshots, CLI and GUI usage examples.
- **Troubleshooting:** Common issues and fixes.
- **Contributing & Code Structure:** How to help and where important files live.
- **License & Contact:** Licensing and ways to reach the maintainer.

---

**Description**

- **Purpose:** Read NFC card identifiers and metadata using a USB NFC reader, and provide a simple UI/CLI to view and export card data.
- **Audience:** Makers, security researchers, and developers who need a quick desktop NFC utility.

**Features**

- **Read card UID** and basic card info.
- **Export** card data as CSV/JSON (manual export flow).
- **Standalone builds** available in `dist/` (Windows `.exe`).
- Minimal external dependencies so packaging is straightforward.

**Quick Start**

Run the packaged executable (Windows):

```bash
# from the project's `dist` folder
./app.exe
```

Run from source (recommended for development):

```bash
python -m venv .venv
source .venv/Scripts/activate  # Windows (Git Bash / bash.exe)
pip install -r requirements.txt  # if a requirements file is present
python src/app.py
```

If `requirements.txt` is not present, install the typical packages manually (example):

```bash
pip install pyserial nfcpy pyinstaller
```

**Build (create a standalone executable)**

This repo includes an `app.spec` used by PyInstaller. To build a Windows executable:

```bash
pip install pyinstaller
# using the spec (keeps icon and packaging options preserved)
pyinstaller app.spec
# or build a one-file executable
pyinstaller --onefile --windowed src/app.py
```

The built artifacts will appear in `dist/` (for example `dist/app.exe`). The `build/` folder contains PyInstaller build metadata.

**Project Layout**

- `src/` — application source code (primary entry: `src/app.py`).
- `app.spec` — PyInstaller spec used to build the executable.
- `build/` — intermediate files created by the packager.
- `dist/` — packaged distributable(s) (look here for `app.exe`).
- `convert_icon.py` — helper for converting icons for packaging.
- `LICENCE` — project license file.

**Usage & Examples**

- GUI: Launch the app and follow on-screen instructions to read a card.
- CLI (if supported): `python src/app.py --help` for options (some builds may provide flags for export).

Example: Exporting card data (pseudo example):

```bash
# read and export card data as JSON
python src/app.py --export card-data.json
```

**Troubleshooting**

- No reader detected: Ensure drivers for your NFC reader are installed and the device is connected. Check `Device Manager` (Windows) or `lsusb` (Linux).
- Permission errors (Linux/macOS): You may need to run with elevated privileges or adjust udev rules.
- Executable won't start on Windows: Confirm required VC++ redistributables are present. Try launching from a terminal to see errors.

**Contributing**

Contributions are welcome. Recommended steps:

1. Fork the repo and create a feature branch.
2. Add tests for new functionality (if applicable).
3. Open a pull request with a clear description of changes.

Key files to look at:

- `src/app.py` — main application logic.
- `convert_icon.py` — icon conversion utility used before packaging.
- `app.spec` — PyInstaller configuration for packaging.

**Security & Privacy**

This tool reads identifying information from NFC cards (UID). Treat collected data responsibly and follow local laws and policies regarding card access and privacy.

**License**

See `LICENCE` in the repository root for license details.

**Contact & Support**

If you need help, file an issue or contact the maintainer. For quick questions, open a new issue titled `Support: <short description>` and include environment details (OS, reader model, Python version).

---

If you'd like, I can:

- Expand the **Usage** section with screenshots or GIFs.
- Add a `requirements.txt` or `pyproject.toml` (I can detect imports and generate one).
- Create a short `CONTRIBUTING.md` and a `CHANGELOG.md` template.

Tell me which of the above you'd like next.


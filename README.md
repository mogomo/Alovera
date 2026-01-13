# Vera – Vertica SQL Client for Windows

**Installer-only repository for Vera**  
Current Windows installer: `Vera-Setup-1.2.43.exe`

---

## Overview

Vera is a lightweight desktop **SQL client and schema browser for Vertica** on Windows, built with Electron and React.

It is designed to make day‑to‑day Vertica work faster and more comfortable:

- Run ad‑hoc SQL queries using Vertica’s `vsql` command‑line client.
- Browse schemas, tables, views and columns in a tree view.
- Open multiple SQL workspaces (tabs), each with its own editor and results.
- Save and reload workspaces to `.vera_ws` files on disk.
- Visualize column value distributions and explore data interactively.

If you just want to use Vera, download the installer from this repository and follow the steps below.

---

## Features

- **Vertica‑focused SQL client**
  - Uses your existing **Vertica client** (`vsql.exe`) under the hood.
  - Simple configuration for host/database/user/password in the Settings dialog.
  - Designed specifically for Windows + Vertica workflows.

- **Smart SQL editor**
  - Multi‑tab SQL editor with syntax highlighting.
  - Insert fully‑qualified names from the schema tree directly into the editor.
  - Zoom and resize panels like a familiar code editor.

- **Schema browser**
  - Tree view of **schemas, tables, views and columns**.
  - Context actions (e.g. “Sample select”) to quickly inspect table contents.
  - Right‑click options on schema items to generate and run helper queries.

- **Workspaces**
  - Open and manage multiple SQL workspaces (tabs).
  - Save the current set of tabs, SQL and connection metadata into `.vera_ws` files.
  - Reload saved workspaces later to pick up exactly where you left off.

- **Data visualization**
  - Column distribution graphs using ECharts: see value → count distributions for a selected column.
  - Interactive chart features: tooltips, zoom, scroll, and export to PNG.
  - “Graph” actions from the schema tree to quickly visualize distributions.

- **Experimental AI assistant (optional)**
  - Conversational side drawer that can suggest SQL based on your current context (active tab, highlighted tables, etc.).
  - Designed to work with **local models** (no hard dependency on cloud APIs); can be disabled if you prefer not to use it.
  - Generated SQL is shown for review and must be explicitly approved before execution.

- **Polished Windows experience**
  - Desktop shortcuts and Start Menu entry.
  - Dark/light appearance, zoom controls, and clear view/layout options.

---

## System Requirements

**Operating System**

- Windows 10 (64‑bit) or Windows 11 (64‑bit)  
  (Both Home and Pro editions are good.)

**Vertica**

- Vertica client tools for Windows installed (so `vsql.exe` is available).
  - Typical default path:  
    `C:\Program Files\Vertica Systems\VSQL64\vsql.exe`
  - Vera uses this Vertica client executable to connect and run queries.
  - Vertica server version 24.x and above, (Vertica DB server on any OS, for Vera to connect to).

**Hardware (recommended)**

- CPU: Dual‑core 64‑bit processor or better.
- RAM: 16 GB or more (32 or 64 GB if working with large result sets and AI features).
- Disk: At least 500 MB free (for the app, logs, workspace files and cache).
- Display: 1280×720 or higher resolution.

**Other**

- Internet connection is **not required** for basic use against your Vertica instance.
- Some optional AI/assistant features may be more resource‑intensive (CPU/RAM).

> You do **not** need Node.js or any build tools to run Vera from this installer.  
> Those are only required for development and are not part of this binary‑only distribution.

---

## Download

The current Windows installer is:

- `Vera-Setup-1.2.43.exe`

To download from GitHub:

1. Go to the **Code** tab of this repository.
2. Locate `Vera-Setup-1.2.43.exe` in the file list.
3. Click the filename.
4. Click **Download** (or **View raw**) to save it to your machine.

In the future, installers may also be published under **Releases**.

---

## Installation

1. **Download the installer**

   - Save `Vera-Setup-1.2.43.exe` to a folder on your Windows machine (e.g. `Downloads`).

2. **(Optional) Verify the download**

   - See [Checksums & Verification](#checksums--verification) if you want to validate integrity.

3. **Run the installer**

   - Double‑click `Vera-Setup-1.2.43.exe`.
   - If Windows SmartScreen shows a warning:
     - Verify that the installer came from this official GitHub repository.
     - Click **More info → Run anyway** if you trust the publisher.

4. **Setup wizard**

   - Choose the installation folder (or accept the default).
   - Choose whether to create shortcuts.
   - Click **Install** and wait for the installation to complete.

5. **Launch Vera**

   - Use the Desktop shortcut,
   - Or the Start Menu shortcut,
   - Or run `Vera` from the installation folder.

---

## First Run & Configuration

On the first run, Vera expects to find `vsql.exe` (Vertica client) and basic connection settings.

1. **Configure Vertica client path**

   - Open **Settings** in Vera (top bar).
   - Set **Vertica client (vsql.exe) path**:
     - Example: `C:\Program Files\Vertica Systems\VSQL64\vsql.exe`
   - If Vera cannot find `vsql.exe`, queries will fail until this is configured.

2. **Configure connection**

   In Settings, configure:

   - **Host** – Vertica host or IP.
   - **Database** – Target Vertica database.
   - **User** – Username for the connection.
   - **Password** – Password for the connection (stored locally).
   - Optional: default schema or other connection options, if available.

3. **Configure local files folder**

   - Set the **Vera local files folder**:
     - This is where Vera stores `.vera_ws` workspace files and related user data.
   - Choose a location that is backed up or under version control if desired.

4. **Test the connection**

   - Open a new tab.
   - Run a simple query like `SELECT 1;`.
   - Confirm that you see results in the bottom panel.

---

## Typical Workflow

1. **Create a workspace**
   - Open Vera; a default tab is created.
   - Write your SQL in the editor.

2. **Browse schemas**
   - Use the schema tree on the left to explore schemas, tables, views and columns.
   - Double‑click or right‑click items to insert fully‑qualified names into the editor.

3. **Run queries**
   - Execute SQL and inspect the result grid.
   - Use multiple tabs to separate experiments, reports or environments.

4. **Save your session**
   - Save your current tabs and SQL into a `.vera_ws` workspace file.
   - Later, open the same `.vera_ws` file to restore the session.

5. **Visualize data**
   - From the schema tree (or context menu), trigger a **Graph / Visualize** action on a column.
   - View a horizontal bar chart of value distributions (value → count).
   - Zoom, scroll and export charts as PNG images.

6. **(Optional) AI assistant**
   - Open the AI drawer to ask questions or request SQL suggestions based on your current database context.
   - Review the suggested SQL; choose to append, replace or run it.
   - All AI‑generated SQL requires explicit approval before execution.

---

## Updates

- **Current version:** `1.2.43`
- **Installer filename:** `Vera-Setup-1.2.43.exe`

When a new version is released:

- The version number in this README and the installer filename will be updated.
- A new installer will be published in this repository (and/or under Releases).
- Changes will be recorded in the [Changelog](#changelog).

To update Vera:

1. Download the latest `Vera-Setup-<version>.exe`.
2. Run the installer.
3. Install over your existing Vera installation (your settings and workspaces are preserved).

---

## Checksums & Verification

To verify that the installer has not been corrupted or tampered with, you can compare its SHA‑256 checksum with the value below.

**Vera-Setup-1.2.43.exe**

- SHA‑256: `f367c28a49413c3731e07e13ecf1bdf3b5cf678f3a6f9de9a30e6ead7a923455`

### How to verify on Windows (PowerShell)

1. Open **PowerShell**.
2. Navigate to the folder where you saved the installer.
3. Run:

   ```powershell
   Get-FileHash .\Vera-Setup-1.2.43.exe -Algorithm SHA256
   ```

4. Confirm that the `Hash` value matches the SHA‑256 value listed above.

---

## Security & Privacy

- Vera communicates with your **Vertica** databases via `vsql.exe` using the host/database/user/password you configure.
- All workspace files (`.vera_ws`) and local settings are stored on your machine.
- Vera does **not** require cloud services to function as a SQL client and schema browser.
- Optional AI features use local models and/or local context; they can be disabled if you do not wish to use them.

If you have additional internal security or privacy policies, please review and validate Vera within your environment before rolling it out broadly.

---

## No Source Code in This Repository

This is a **binary distribution repository**.

- ✅ Contains:
  - `Vera-Setup-1.2.43.exe` (Windows installer)
  - This `README.md` and any related documentation.

Vera is currently distributed as a **closed‑source** application.

---

## Known Issues & Limitations

- **Vertica client required**
  - Vera relies on `vsql.exe`. It will not work if the Vertica client tools are not installed or not configured correctly.

- **Windows‑only**
  - Vera is built for Windows 10/11 (64‑bit).

- **Large result sets**
  - Very large queries may use significant memory and take time to render in the UI.
  - Consider limiting result sets with `LIMIT` or using aggregate queries where possible.

- **SmartScreen / antivirus warnings**
  - New or rarely‑seen executables can trigger warnings from Windows or antivirus tools.
  - If you downloaded `Vera-Setup-1.2.41.exe` from this repository and trust the publisher, it should be safe to allow.

---

## Troubleshooting

**Installer does not start**

- Right‑click `Vera-Setup-1.2.43.exe` and choose **Run as administrator**.
- Check whether your antivirus has quarantined the file and restore it if appropriate.

**SmartScreen or security warning**

- Confirm the file was downloaded from this repository.
- Click **More info → Run anyway** only if you trust the publisher.

**Vera cannot connect to Vertica**

- Ensure the Vertica client tools are installed.
- Verify the `vsql.exe` path in Vera’s Settings.
- Confirm host/database/user/password are correct.
- Try running the equivalent command directly in a terminal to see if there are server‑side issues.

**Vera does not launch**

- Reboot Windows and try again.
- Reinstall Vera using the latest installer.
- Check Windows Event Viewer and antivirus logs for blocked processes.

---

## Changelog

### 1.2.43

- Refresh Schema tree bug fix.
- Updated to the latest Vera desktop build.
- Improved schema browsing and workspace handling.
- Refined data visualization behavior for column distributions.
- General stability and performance improvements.

> Earlier versions and more detailed internal notes may be tracked elsewhere; this section focuses on public installer releases.

---

## License & Disclaimer

- **Application license:** Proprietary – all rights reserved.
- **Development:** Vera was developed by **Maya Goldberg**, with the assistance of **AI tools** during design and implementation.
- **Warranty disclaimer:** Vera and its installer are provided **“as is”**, **without warranties of any kind**, either express or implied, including but not limited to implied warranties of merchantability, fitness for a particular purpose, and non‑infringement. You assume all responsibility and risk for your use of the software.
- **Brands and trademarks:** All names, brands, logos and products mentioned in this document, including **“Vertica”** and the **Vertica client `vsql.exe`**, are the property of their respective owners. Vertica and the Vertica logo are trademarks or registered trademarks of **OpenText** and/or its affiliates.
- **Vertica licensing:** Vera is a separate, third‑party SQL client and does **not** include a Vertica license. To use Vertica in production, you must obtain a valid Vertica license. For licensing information, you can contact **Sivan Tziring** (Vertica / OpenText) via **LinkedIn**.

---

## Acknowledgements

Vera is built using AI, several open‑source tools and libraries, including (but not limited to):

- Electron and React for the desktop UI.
- ECharts for charts and column distribution graphs.
- Monaco Editor for the SQL editing experience.
- Additional graph and visualization libraries for network and geospatial views.
- Various supporting NPM packages.

Special thanks to everyone who has tested and provided feedback on Vera.

---

Thank you for using Vera!

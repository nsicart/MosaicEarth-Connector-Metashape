# MosaicEarth-Connector-Metashape

Agisoft Metashape Pro 2.x plugin & headless CLI to export and synchronize Orthomosaics, DEM/DSM, .laz Dense Point Clouds, 3D Models & PDF reports to MosaicEarth 4D Surveys.

## Releases & Ready-to-Install Downloads (`v0.3.0`)

- [`MosaicEarth-metashape-0.3.0.zip`](https://github.com/nsicart/MosaicEarth-Connector-Metashape/releases/download/v0.3.0/MosaicEarth-metashape-0.3.0.zip)
- Also available directly from [MosaicEarth Desktop & Connectors (`app.mosaicearth.app/en/Desktop`)](https://app.mosaicearth.app/en/Desktop).

## Cloud & Local Workstation Endpoints

Every MosaicEarth connector speaks the open **MosaicEarth Synchronization Protocol v1** (chunked `4 MiB` resumable uploads + end-to-end `SHA-256` verification) and can connect to:

- **MosaicEarth Cloud** (default): `https://app.mosaicearth.app`
- **MosaicEarth Desktop (Local Workstation)**: `http://127.0.0.1:19771` (set `MOSAICEARTH_URL=http://127.0.0.1:19771` or select the endpoint in the connector UI).

## Usage & Setup

Download `MosaicEarth-metashape-0.3.0.zip` and extract its contents (`mosaicearth_metashape_startup.py` and the `mosaicearth_metashape/` folder) into your Agisoft Metashape Professional `scripts/` directory:

- **Windows**: `%LOCALAPPDATA%\Agisoft\Metashape Pro\scripts`
- **Linux**: `~/.local/share/Agisoft/Metashape Pro/scripts`
- **macOS**: `~/Library/Application Support/Agisoft/Metashape Pro/scripts`

Restart Metashape Professional (2.0 / 2.1 / 2.2+) and open **MosaicEarth → Synchronize Chunk or 4D Survey…**:

- Exports **Orthomosaic** (BigTIFF/LZW GeoTIFF), **DEM / DSM** (GeoTIFF tagged as `elevation` so MosaicEarth's Cut/Fill Stockpile Volume and 4D $\Delta V$ engine work immediately), **Dense Point Cloud** (`.laz`), **3D Textured Model** (`.glb` or bundled `.obj.zip`), **Processing Report** (`.pdf`) and optional source photographs.
- Pre-fills the **4D Capture Date (`YYYY-MM-DD`)** from aligned camera EXIF timestamps and lets you route the chunk directly into an existing MyEarth Project or create a new one.
- **Pull Selected Project into New Chunk…** downloads verified Cloud assets and creates a new Metashape chunk with restored photographs, point clouds and meshes.
- Supports batch headless execution via `metashape -r`:

```bash
metashape -r -c "from mosaicearth_metashape.plugin import run_headless_metashape; run_headless_metashape(['--psx', 'site.psx', '--email', 'you@example.com', '--password', '***', '--survey-date', '2026-11-12'])"
```

## License

Released under **GNU Affero General Public License v3.0 or later (`AGPL-3.0-or-later`)** — see [`LICENSE`](./LICENSE).

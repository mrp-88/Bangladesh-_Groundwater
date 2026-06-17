# Bangladesh Groundwater Monitor 💧

Satellite-based groundwater storage monitoring dashboard for all **64 districts of Bangladesh**, built on NASA **GRACE / GRACE-FO** total water storage anomalies and **GLDAS-2.2 CLSM** land-surface model outputs (2003–2026).

**Live dashboard:** https://raunaqpreetom88.github.io/GW-Monitor-Bangladesh/

---

## Overview

The dashboard derives a per-district groundwater storage (GWS) anomaly from a satellite water-balance decomposition and validates the resulting depletion trends against in-situ Bangladesh Water Development Board (BWDB) well observations.

The core water balance is:

```
ΔGWS = ΔTWS − ΔSM − ΔSWE − ΔCAN − ΔSW
```

where all terms are in mm equivalent water height, ΔTWS is the GRACE/GRACE-FO anomaly, and the land-surface components (soil moisture, snow water equivalent, canopy, surface water) are differenced from a 2004–2009 baseline using GLDAS Noah/CLSM monthly composites.

Trends are reported as a **Sen's slope** (mm·yr⁻¹), with **Mann–Kendall** significance testing and **OLS regression** for comparison.

## Features

- Interactive Leaflet choropleth of all 64 districts (FAO GAUL Admin Level 2)
- Per-district storage trend, Sen's slope, Mann–Kendall, and OLS statistics
- Satellite-vs-well validation comparing GRACE/GLDAS storage trends to BWDB Depth-Below-Ground-Level (DBGL) records
- Embedded Google Earth Engine reproduction script
- Documented methodology, equations, and data provenance

## Data Sources

| Component | Dataset |
|---|---|
| Total water storage (TWS) | NASA/JPL GRACE CSR RL06 Mascon v02 |
| Land surface | NASA GLDAS-2.2 CLSM v2.5 GRACE-DA |
| Administrative boundaries | FAO GAUL 2015, Level 2 |
| Well validation | BWDB Hydroinformatics & Flood Forecasting Circle, Dhaka |

## Usage

This is a single-file static dashboard. To run locally:

```bash
git clone https://github.com/raunaqpreetom88/GW-Monitor-Bangladesh.git
cd GW-Monitor-Bangladesh
# open index.html in a browser, or serve it:
python3 -m http.server 8000
# then visit http://localhost:8000
```

To deploy via GitHub Pages, enable Pages on the `main` branch (root) in the repository settings.

## Reproducing the Analysis

The full Google Earth Engine script used to derive the per-district trends is embedded in the dashboard and available in the [Code Editor](https://code.earthengine.google.com/). It computes monthly GLDAS composites, the baseline-differenced water balance, and exports per-district Sen's-slope trends to CSV.

## Author

**Mashiyat Raunaq Preetom**
Junior Research Fellow, SPARRSO · B.Sc. Environmental Science, Bangladesh University of Professionals (BUP)

## License

Released under the [MIT License](LICENSE).

## Acknowledgments

NASA JPL (GRACE/GRACE-FO), NASA GES DISC (GLDAS), FAO (GAUL), and the Bangladesh Water Development Board (BWDB).

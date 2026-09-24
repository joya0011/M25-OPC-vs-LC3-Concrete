# M25 OPC vs LC3-50 — Comparative Mix Design & Sustainability Assessment

IS 10262:2019-based mix design of an M25 concrete with ordinary Portland cement (OPC), and an equal-binder
limestone calcined clay cement (LC3-50) counterpart, compared on mix proportions, embodied CO₂ and binder cost.
Strength is **not** measured; published data are reviewed and kept separate from the calculations.

## Key results (per m³ of concrete)

| | OPC | LC3-50 |
|---|---|---|
| Binder / water | 413 / 186 kg | 413 / 186 kg |
| Clinker | 392 kg | 207 kg |
| Fine / coarse aggregate | 638 / 1128 kg | 625 / 1105 kg |
| Mix ratio (binder : FA : CA), w/b | 1 : 1.54 : 2.73, 0.45 | 1 : 1.51 : 2.68, 0.45 |
| Embodied CO₂ (ground-to-gate) | 346 kg CO₂-eq | 236 kg CO₂-eq (**−32%**) |
| Binder raw-material cost | ₹2,391 | ₹1,412–1,660 (**−31% to −41%**) |

## Repository structure

```
Report/M25_OPC_LC3_Report.pdf     6-page technical report
Calculations/mix_design.xlsx      formula-driven workbook (edit blue cells on 'Inputs'; everything recalculates)
Data/emission_factors.csv         CO₂ factors (Pillai et al. 2019, Table 3)
Data/material_rates.csv           input prices (Joseph & Bishnoi, IIT Delhi)
Data/literature_strength.csv      secondary strength/CO₂ data
Figures/*.png                     all report figures
scripts/calc.py                   single source of truth for every number
scripts/make_figures.py           regenerates Figures/
scripts/make_workbook.py          regenerates the Excel workbook
scripts/make_report.py            regenerates the PDF report
References/references.md          full reference list with links
```

## Reproduce

```bash
pip install matplotlib openpyxl reportlab pillow
python scripts/calc.py          # prints all results, writes Data/*.csv
python scripts/make_figures.py
python scripts/make_workbook.py
python scripts/make_report.py
```

## Method in brief

1. **OPC mix** — f′ck = 25 + 1.65×4 = 31.6 MPa; w/c 0.45 (≤ 0.50, IS 456 moderate exposure); water 186 kg/m³
   (IS 10262 Table 4); cement 413 kg/m³; 2% air; CA volume fraction 0.63 (IS 10262 Table 5, corrected for w/c).
2. **LC3 mix** — same binder mass split 50:30:15:5 (clinker : calcined clay : limestone : gypsum); aggregate volume
   corrected for the blended binder's lower specific gravity (2.86) so yield stays 1 m³.
3. **CO₂** — ground-to-gate factors from an Indian LCA (IIT Madras). Scenario A uses cement-level factors (main result);
   Scenario B rebuilds the binder factor from constituents (upper bound, −43% at binder level).
4. **Cost** — binder raw materials only, using Indian input prices from an IIT Delhi economic analysis of LC3 (2016).

## Limitations

Assumed specific gravities; no trial batches or cube tests; transport, superplasticiser and grinding energy excluded
from the cost; 2016 prices. Equal binder does not guarantee equal strength — trial mixes are the next step.

## Author

Mantasha Siddiqui - B.Tech Civil Engineering, NIT Srinagar

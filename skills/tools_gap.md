# Tools gap: software the ALMA papers use vs what Quasar can call

Built 2026-10-28 from `catalog/software.parquet` (1,591 non-held-out papers whose methods cards passed evidence
verification) and a name search over Quasar's code (`core/`, `integrations/`, `services/`, `adapters/`,
`capabilities/`, `skills/`, `ui-pro/api/`, requirements files). Full table: `stats/tools_gap.csv` (166 packages
named in >= 4 papers). "Named in Quasar" only means the name appears in the code; it does not prove a working tool
(for example `sextractor`, `ciao` and `fast` match unrelated text). Paper counts are distinct papers naming the
package in their software inventory, so they undercount packages used without being named.

## What Quasar already covers

CASA (1,220 papers, 77% of the corpus) through the CASA tool pack; astropy, scipy, matplotlib, photutils,
spectral-cube, Splatalogue/CDMS line catalogs, CARTA (viewer only).

## Ranked gaps worth wrapping (Python, pip-installable, scriptable)

| Rank | Package | Papers | What the papers use it for | Skill that needs it |
|---|---|---|---|---|
| 1 | emcee | 177 | MCMC for every kind of model fit (disks, SEDs, lenses, kinematics) | uv-plane-fitting, sed-fitting, keplerian-disk-kinematics, lens-modelling |
| 2 | RADEX (spectralradex / ndradex) | 86 | non-LTE line ratios, density and temperature | non-lte-excitation |
| 3 | RADMC-3D (radmc3dPy) | 94 | dust/line radiative transfer models | radiative-transfer-modelling |
| 4 | APLpy | 51 | publication maps (low value as an agent tool) | - |
| 5 | uvmultifit | 37 | parametric fits in the uv plane | uv-plane-fitting |
| 6 | galario | 31 | fast visibility sampling of model images | uv-plane-fitting, disk-substructure-profiles |
| 7 | 3DBarolo (pyBBarolo) | 29 | tilted-ring fits of galaxy cubes | galaxy-3d-kinematics |
| 8 | bettermoments | 27 | robust moment maps / line centroids | moment-maps, keplerian-disk-kinematics |
| 9 | astrodendro | 25 | dendrogram core/clump extraction | core-extraction-cmf, gmc-decomposition-virial |
| 10 | lmfit / mpfit | 18 / 22 | least-squares line and profile fitting | many |
| 11 | statcont | 18 | continuum level in line-rich cubes | continuum-subtraction |
| 12 | vis_sample | 17 | sampling model cubes at the observed uv points | uv-plane-fitting |
| 13 | pyspeckit | 15 | spectral line fitting (incl. hyperfine) | line-identification, rotational-diagram-lte |
| 14 | GoFish | 15 | stacking disk spectra along Keplerian velocity | keplerian-disk-kinematics, stacking |
| 15 | linmix | 14 | regression with censored data | star-formation-laws |
| 16 | eddy | 13 | disk rotation-map fits | keplerian-disk-kinematics |
| 17 | KinMS | 11-14 | forward models of gas kinematics (SMBH masses) | smbh-gas-dynamics |
| 18 | frank | 11 | non-parametric 1D visibility fits of disks | disk-substructure-profiles |
| 19 | dynesty | 9 | nested sampling | uv-plane-fitting, sed-fitting |
| - | Qubefit | 1 | 3D cube fitting of high-z galaxies (the gap behind the CosmicCoder Neeleman task) | galaxy-3d-kinematics |

Qubefit has only one paper in the verified set, so by paper count it is low; it stays on the list because a
benchmark task depends on it.

## Gaps that are heavy, licensed or non-Python (wrap only if a task needs them)

GILDAS/CLASS (121), MIRIAD (108), AIPS (66), GALFIT (49), MAGPHYS (43), CIGALE (35), LIME (35), HIPE (34),
XSPEC (30), MCFOST (25), DALI (24), Cloudy (23), IRAF (22), EAZY (20), Starburst99 (18), CASSIS (18), WEEDS (15),
PHANTOM (15), XCLASS (13), MADCUBA (12). Most are other facilities' reduction packages (HIPE, CIAO, XSPEC, IRAF,
JWST pipeline) or GUI/legacy suites; for ALMA work the CASA path already covers what MIRIAD/AIPS/GILDAS did.

## Recommendation

1. A small "fitting" tool pack: emcee + dynesty + lmfit behind one model-fitting interface (largest reach).
2. A "visibility modelling" pack: galario + vis_sample + uvmultifit + frank.
3. A "line excitation" pack: RADEX (spectralradex) + pyspeckit + statcont.
4. A "kinematics" pack: bettermoments + eddy + GoFish + 3DBarolo + KinMS (+ Qubefit for the benchmark task).
5. astrodendro for core/clump extraction.
Each skill in this folder names the steps these tools would serve.

# Non-LTE excitation: grid and setup values by paper

Every row is taken from the evidence pack's "Key parameters" and "Assumptions" lines for this technique.
Blank cells mean the pack does not state the value for that paper.

## RADEX / LVG grids for CO SLEDs and CO + [CI]

| Bibcode | T_kin | n(H2) (cm-3) | N/dv or other column axis | Fixed inputs |
|---|---|---|---|---|
| 2017ApJ...835..174S | 10-300 K, 1 K steps | 1e2-1e7 | N(H2) 1e20.5-1e23.5 cm-2 | expanding sphere, dv = 200 km/s, T_bg 2.73 K, [CO]/[H2] = 3e-4; two-phase grid T_warm 10-800 K at n_warm 1e2, 1e3, 1e4 |
| 2019MNRAS.486.2366M | 10-1000 K | 1e2-1e6 | dv/dr 1e2-1e6 m/s/pc | 0.1 dex steps; x_CO = x_C ~ 1e-4; K_vir >= 1; 5% (CO 2-1) and 10% (others) calibration error |
| 2020A&A...643A..89P | 3-400 K | 1e2-1e5 | N_CO/dv 1e15-1e20 | 40 log steps each (64000 models); Z_CO = 1e-4; LTE H2 OPR; Yang2010 rates |
| 2024A&A...686A..47M | T_CMB-1e3 K | 10^1.5-10^7.5 | N_CO/dv 10^14.5-10^19.5; dv/dr 0.1-1000 km/s/pc | H2 sole partner, OPR 3, X_CO/(dv/dr) = 1e-5 |
| 2020ApJ...902..109B | 10-200 K | 10-1e7 | [CO]/[H2](dv/dr)^-1 1e-3-1e-7; r_eff 1-1e4 pc | ~1e6 models per galaxy; prior excluding a ladder peak beyond CO(7-6) |
| 2020MNRAS.493.3744F | 10-400 K | 1e2-1e7 | N_CO fixed 1e16 (QSO), 1e17 (companion) | widths 300 and 850 km/s; spherical; H2 only; CMB at z = 2.84 |
| 2019ApJ...873...50D | T_CMB-300 K | 10-1e6 | N_CO/dv 1e14-1e19 | flat priors; tau < 100; T_bg = 2.73(1+z) K |
| 2016ApJ...821..112K | 10-400 K, 10 K steps (linear) | 1e3-1e8 | N_CO 1e14-1e19, 0.1 dex steps | dv = 100 km/s; uniform sphere; chi2_red <= 1.5 accepted |
| 2017A&A...608A..38O | 10-200 K (log 0.043) | 1e2-1e7 (log 0.167) | N(12CO) 5e15-1e20 (log 0.5) | width 100 km/s; T_bg 2.73 K; 12CO/13CO = 100 |
| 2018ApJ...868...95M | 5-6300 K | 10-1e7 | N_CO 1e12-1e22 | filling factor 1e-5-1; T_bg 2.73 K; FWHM 150 km/s; [CO/H2] = 1e-4 |
| 2020ApJ...898...75I | 50, 100, 200, 300, 500 K | 1e3, 1e4, 1e5 | N_CO/dV 3e16, 1e17, 3e17; [C0]/[CO] 1, 3, 10 | [CO]/[H2] = 1e-4; T_bg 2.73 K; [CO]/[13CO] = 40 |
| 2020A&A...641A.155V | | | [CO/H2]/(dv/dr) = 1e-5 km-1 s pc | line width 50 km/s; [CI]/H2 = 3e-5; OPR 3 |
| 2014ApJ...785..149S | 12-300 K | 10-1e6 | N_CO/dv 1e15-1e19; 12CO/13CO 10-1e4 | T_CMB ~ 11 K; 15% added uncertainty on ratios (not identified as calibration); tau < 100; virialized K_vir prior, cutoff not stated |

## Dense-gas and other molecular tracers

| Bibcode | Species | T_kin | n(H2) (cm-3) | Column / other | Fixed inputs |
|---|---|---|---|---|---|
| 2025A&A...696A..31G | HCNH+ | 50-500 K | 1e2-1e7 | N 1e13-1e17 cm-2 | emcee 20 walkers, 4500 steps; OPR 0.25; filling 1 |
| 2021A&A...645A..45C | HCN, HCO+, HNC | T_CMB-1e3 K | 1e3-1e7 | N/dv fixed 1e14 | T_bg 10.9 K; single component; expanding sphere |
| 2019PASJ...71...68K | HCN, HCO+ and others | 10-600 K | log 2-7 | log N(H2) 20-25; [HCN]/[HCO+] 1-10 | widths 330, 120, 140 km/s; spherical; T_bg 2.73 K; [CO]/[H2] = 6e-5, [HCO+]/[H2] = 8e-9 |
| 2024A&A...689A..64B | S-bearing species | limited to rate range | 1e3-1e8 | N 5e12-1e18 cm-2; size 0.1"-150" | semi-infinite slab; OPR 3; 15% calibration error |
| 2024ApJ...969..143I | para-H2CO | free | free | N free; filling factor < 1 | flat log priors |
| 2025A&A...693A.101T | H2CO | 10-200 K, step 10 | log 5-12, step 0.1 | N = 1e12 (grid) or 1e14 (ratios) | width 1 km/s; E_up <= 300 K; A >= 1e-6 |
| 2026A&A...707A.120H | CH3CN, H2CO, CH3OH | free | fixed from C17O | N free | E/A = 1; OPR 3 (H2CO); T_bg 2.73 K; dv = 0.6 km/s |
| 2020MNRAS.498L..87B | CH3OH | 80-180 K | 3e6-2e8 | N 3e16-4e19 cm-2; size free | spherical; A/E = 1; FWHM 3.5 km/s |
| 2015A&A...581A..85P | SO | 50-500 K | 1e5-1e7 | | X_CO = 1e-4 for abundances |
| 2019A&A...632A.101T | SiO, H2CO, HCN | 75-700 K | 1e4-1e6 | | dv = 10 km/s |
| 2015ApJ...803...60S | 13CO, HCO+ | 5-300 K or 5-400 K | 1e2-1e5 or 1e3-1e7 | | uniform sphere; [CO]/[H2] = 1e-4, [CO]/[13CO] = 70 |
| 2018ApJ...856...97S | CO, HCO+ | 5-500 K | 1e2-1e7 | | dV = 50 km/s; T_bg 2.73 K |
| 2019A&A...623A..68T | HCO+ (absorption) | 10-130 K | 10-1e7 | | HCO+ abundance 3e-9 to 2e-8 |
| 2017MNRAS.469.3347M | SiO, CO | grid | n_coll = 1e6 adopted | | H2 partner; d = 50 kpc; minor species at T_kin = 40 K |
| 2018ApJ...864..133T | CS | 10-150 K (prior) | log 4-10 | log N 9-14 | pyradex grid 40 per axis; emcee 256 walkers; slab; thermal OPR |
| 2014ApJ...796..131O | SO | free | free | X/(dv/dr) free | static sphere escape probability; chi2 < 10 accepted |
| 2020ApJ...889L...4L | CO, HCO+ (absorption) | 100 K fixed | free | N_CO, N_HCO+ free | |
| 2014ApJ...795...28B | HCO+ (absorption) | 60 K | grid | | width 10 km/s; T_bg 2.73 K; X(HCO+) = 1e-7 |

## Electron- or radiation-dominated gas (debris disks, comets, ejecta)

| Bibcode | Target | Setup |
|---|---|---|
| 2016MNRAS.460.2933M | HD 181327 CO | RADMC-3D; n_e0 1e-2-1e7 cm-3 (radiation-dominated to LTE); T_k half to twice T_dust (50 K) |
| 2018ApJ...861...72C | beta Pic C I | pythonradex uniform sphere, electrons from C ionisation; b = 0.57 km/s; 3D models at T_kin = 75 K |
| 2015MNRAS.447.3936M | Fomalhaut CO | levels to j = 24; T_k 10-150 K; colliders H2 (primordial) or e- and H2O (secondary) |
| 2020ApJ...898..146M | Vega | T_kin 10-250 K, full range of electron densities |
| 2019ApJ...870L..26C | comet ISON | modified LIME, 5000-cell Delaunay grid, v_exp 1.1 km/s, T_kin 145 K from CH3OH |
| 2025NatAs...9.1476C | comet 12P | x_ne = 0.2; collision cross-section with H2O 5e-14 cm^2 (the pack writes cm-2, a dimensional slip: a cross-section is an area) |
| 2025ApJ...986L..22R | comet C/2014 UN271 | SUBLIMED transfer model with T_kin 4 K for CO; separately, an H2CO-CO collision cross-section of 5e-14 cm^2 used in a thermalization approximation, not as a SUBLIMED input (pack writes cm-2) |
| 2013ApJ...778L..25C | IRC+10216 | ro-vibrational rates = rotational rates / 100 |

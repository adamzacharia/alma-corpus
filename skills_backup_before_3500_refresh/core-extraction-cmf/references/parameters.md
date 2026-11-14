# Per-paper extraction settings (core-extraction-cmf)

Taken from the evidence pack's "Key parameters" and excerpt lines (a few details from single cards, marked
"card"). Thresholds are in units of the map rms unless a flux is given. Only papers that extract cores or
dense-gas clumps are listed; CO cloud decomposition is in `alma-gmc-decomposition-virial`.

## astrodendro

| Bibcode | Map | min_value | min_delta | min_npix | Notes |
|---|---|---|---|---|---|
| 2020ApJ...890...76N | 3 mm continuum | 3 sigma | 1 sigma | 1 beam | Run alongside clumpfind; clumpfind kept as fiducial |
| 2018ApJ...853..160C | 1.3 mm continuum | 4 sigma (fiducial) | 1 sigma | 0.5 beam | 3 sigma gives 125 cores instead of 76 |
| 2020ApJ...894L..14L | 1.3 mm, CMZ clouds | 4 sigma | 1 sigma | 1 beam | Non-PB-corrected image for finding; 30% PB cut |
| 2020ApJS..251...14H | 1.3 mm SMA (CMZoom), MJy/sr | 3 x global noise | global low noise | ~0.5 beam | Leaves pruned: peak > 6 sigma (robust) or > 4 sigma, mean > 2 sigma local rms |
| 2025ApJ...994..233Y | 3 mm / 1.3 mm high-res | 3 sigma | 1.5 sigma | 15 px | Visual selection by three coauthors, then dendrogram |
| 2020ApJ...896..110L | 3 mm continuum | 3 sigma | 1 sigma | 40 px ("approximately the synthesized beam area", card) | Properties from CASA imfit; extra > 5 sigma sources added (card) |
| 2017MNRAS.464L..31H | ALMA+ACA continuum | 3 sigma | 1 sigma | 60 px | Too few cores for a robust CMF |
| 2018ApJ...856..147O | ALMA+ACA 3 mm | 3 sigma | 1 sigma steps | "3 x theta_beam" (ambiguous, unresolved) | Leaves must also be > 3 sigma in 12m data |
| 2024A&A...690A.185W | ALMAGAL 1.3 mm | 5 sigma | 5 sigma | beam area | kappa 0.899 cm2/g, gas-to-dust 150 (card) |
| 2025ApJ...990...80K | JCMT 850 um (ALMA minor) | 50 mJy/beam (5 sigma) | 30 mJy/beam (3 sigma) | 5 px | 2D Gaussian to each leaf |
| 2024MNRAS.527.5895D | 1.16 mm continuum | 0.5 mJy/beam | 0.2 mJy/beam | 2 beams | Check on a clumpfind decomposition |
| 2023MNRAS.526.4402B | 865 um continuum; H13CO+ cube | 0.5 mJy/beam (cont.); 3 sigma (cube) | 0.2 mJy/beam; 1 sigma | 74 px (cube) | Mean gas temperature 54 K for masses |
| 2020ApJ...896...35J | 1.2 mm | 2 sigma | 1 sigma | not stated | Free-free not removed |
| 2021ApJ...907L..15S | combined ACA+12m, uv-tapered | 4 sigma (card) | 2 sigma (card) | not stated | Tapers 100-200 klambda tested, 150 adopted (card) |
| 2019ApJ...871..185L | 1000 au continuum, PB-uncorrected | 2 sigma (card) | 5 sigma (card) | 25 px (min area) | Catalog edited by hand; edits subjective |

### How the SKILL.md counts were made

Counted by hand from the table above (one entry per paper; the cube settings of 2023MNRAS.526.4402B count
for that paper, its continuum run is absolute flux only).

- `min_value`: 3 sigma (7) = 2020ApJ...890...76N, 2020ApJS..251...14H, 2025ApJ...994..233Y,
  2020ApJ...896..110L, 2017MNRAS.464L..31H, 2018ApJ...856..147O, 2023MNRAS.526.4402B; 4 sigma (3) =
  2018ApJ...853..160C, 2020ApJ...894L..14L, 2021ApJ...907L..15S (card); 5 sigma (2) = 2024A&A...690A.185W,
  2025ApJ...990...80K; 2 sigma (2) = 2020ApJ...896...35J, 2019ApJ...871..185L (card); absolute only (1) =
  2024MNRAS.527.5895D.
- `min_delta`: 1 sigma (8) = 2020ApJ...890...76N, 2018ApJ...853..160C, 2020ApJ...894L..14L,
  2020ApJ...896..110L, 2017MNRAS.464L..31H, 2018ApJ...856..147O, 2023MNRAS.526.4402B, 2020ApJ...896...35J;
  1.5 sigma (1) = 2025ApJ...994..233Y; 2 sigma (1) = 2021ApJ...907L..15S (card); 3 sigma (1) =
  2025ApJ...990...80K; 5 sigma (2) = 2024A&A...690A.185W, 2019ApJ...871..185L (card); global noise (1) =
  2020ApJS..251...14H; absolute only (1) = 2024MNRAS.527.5895D.
- `min_npix` in beam areas: 1 beam (3) = 2020ApJ...890...76N, 2020ApJ...894L..14L, 2024A&A...690A.185W;
  ~0.5 beam (2) = 2018ApJ...853..160C, 2020ApJS..251...14H; 2 beams (1) = 2024MNRAS.527.5895D;
  ambiguous (1) = 2018ApJ...856..147O.
- `min_npix` as fixed pixels (6): 5 px 2025ApJ...990...80K, 15 px 2025ApJ...994..233Y, 25 px
  2019ApJ...871..185L, 40 px 2020ApJ...896..110L (about one beam per its card, not reclassified), 60 px
  2017MNRAS.464L..31H, 74 px (cube voxels) 2023MNRAS.526.4402B.
- Not counted (CO or galaxy structures): 2024ApJ...969..143I (1 beam area = 14 px, used only as a
  conversion example), 2024MNRAS.534..683Z, 2024PASA...41...76Z, 2017ApJ...849...90S, 2024ApJ...966...51G,
  2024ApJ...964..166K, 2026ApJ..1003...68Y, 2026ApJ..1003..231W.

## clumpfind and other finders

| Bibcode | Tool | Settings | Notes |
|---|---|---|---|
| 2016ApJ...833..209O | Clumpfind | 2 sigma threshold and step; keep peaks > 5 sigma | 48 cores; cumulative CMF 1.6 +/- 0.7 |
| 2020ApJ...890...76N | Clumpfind | Tlow 3 sigma, dT 2 sigma, Smin 1 beam | Radius = geometric mean of semi-axes |
| 2018ApJ...853..160C | clumpfind | Delta 3 sigma, Smin 0.5 beam | 83 cores; true slope 0.64 +/- 0.13 |
| 2019MNRAS.483.1624B | Starlink CUPID ClumpFind | lowest 3 rms, spacing 2 rms, fwhm = 0, minpix 56-61 | No background subtraction; visual check |
| 2019ApJ...872..121U | clumpfind (3D, l-b-v) | 2 sigma level and step (0.32 K) | Reject < 3 px at >= 3 sigma, < 2 channels, R < 0.035 pc |
| 2024MNRAS.527.5895D | clumpfind (IDL) | absolute levels 0.03 and 0.055 x 10.4 mJy/beam | astrodendro as independent check |
| 2014A&A...569A..11S | 2D CLUMPFIND | not stated | Flux within 5 sigma; deconvolved diameter at 50% contour |
| 2016PASJ...68L...7T | clumpfind | not stated | 18 clumps at 340 GHz |
| 2019ApJ...884...48C | getsources + CASA imfit | parameters not stated | Keep converged Gaussian fits; 81 cores |
| 2018A&A...616L..10F | getimages + getsources | defaults; max structure size 2" | getimages v2.171128, getsources v1.140127 (card) |
| 2018A&A...618L...5N | getsources v1.140127 (card) | configuration not given (card) | PPMAP temperatures (card) |
| 2017A&A...600A.141K | gaussclumps (CUPID 2.0) | threshold 3 rms; median filter 10" | Filter 7.5-15" tested |
| 2020A&A...635A...2S | SExtractor | parameters beyond thresholds not stated | Completeness 2 Msun |

clumpfind level/step counts in SKILL.md cover the first six rows only: 2 sigma / 2 sigma (2) =
2016ApJ...833..209O, 2019ApJ...872..121U; 3 sigma / 2 sigma (2) = 2020ApJ...890...76N, 2019MNRAS.483.1624B;
step 3 sigma with level not stated (1) = 2018ApJ...853..160C; absolute levels (1) = 2024MNRAS.527.5895D.
Settings from non-core uses are excluded: 8 sigma / 4 sigma for GMCs in 2017PASJ...69...18T, 3 sigma / 1
sigma for the companion line search in 2018PASJ...70...36I, 2 sigma / 2 sigma on a lensed CO cube in
2017A&A...604A.117C.

## Completeness and CMF fits

| Bibcode | Completeness method | Limit | CMF fit | Result (native convention) |
|---|---|---|---|---|
| 2018ApJ...853..160C | 10 beam-shaped artificial cores per run, 30 repeats (card); flux and number corrections | fit above 0.8 Msun | chi2 in log space, 5 bins/dex, Poisson errors | dN/dlogM: alpha 1.24 +/- 0.17 (true), 1.11 +/- 0.20 (raw) |
| 2020ApJ...894L..14L | artificial cores, astrodendro recovery | 20 km/s cloud, 90%: ~2 Msun (30% PB selection), ~5 Msun (> 5 sigma) | plfit MLE, KS lower bound | dN/dlogM: alpha 1.00-1.07, lower bound ~5 Msun |
| 2020ApJ...890...76N | none; 3 sigma mass sensitivity only | 0.7-1.4 Msun (sensitivity) | MLE on eCDF | dN/dM: -1.33 +/- 0.15 (90% CI -1.58 to -1.08); dN/dlogM equivalent -0.33 |
| 2020A&A...635A...2S | Monte Carlo | 2 Msun | power law dN/dlnM, method not stated | dN/dlnM: -1.1 +/- 0.02; -0.7 to -1.46 under random T |
| 2019MNRAS.483.1624B | 600 beam-sized Gaussians per bin, logistic fit | per field | not in pack | N_corr = N / f |
| 2020ApJS..251...14H | point sources via simobserve + tclean | 95% at 80 Msun (robust), ~50 Msun | none | Td = 20 K for the completeness masses only; catalog masses use Herschel Td |
| 2025ApJ...994..233Y | injected 2D Gaussians, same dendrogram | 0.25 / 0.20 mJy at 3 mm | none (masses are lower limits) | |
| 2026A&A...705A.100E | catalog completeness (card) | 90% flux 0.95 mJy = 0.13 / 0.37 Msun at 3.5 / 6 kpc (card) | not in pack | Ncore may be lower limits |
| 2016ApJ...833..209O | not stated | | cumulative N(>M), Poisson uncertainties sqrt(N), 2.4-14 Msun | N(>M): 1.6 +/- 0.7 |
| 2019ApJ...872..121U | not stated | > 450 Msun (H13CO+) | single power law, chi2/dof, binning not stated | dN/dM: 1.48 +/- 0.14 (dN/dlogM 0.48); C34S 1.15 (0.15); Orion A 2.3 for comparison |

Counts in SKILL.md: injection completeness (5) = the 2018ApJ...853..160C (card), 2020ApJ...894L..14L,
2019MNRAS.483.1624B, 2020ApJS..251...14H, 2025ApJ...994..233Y rows. CMF fit: MLE (2) =
2020ApJ...890...76N, 2020ApJ...894L..14L; binned chi2 (1) = 2018ApJ...853..160C; cumulative LSQ (1) =
2016ApJ...833..209O; method not stated (2) = 2020A&A...635A...2S, 2019ApJ...872..121U. Logarithmic-form
slopes (4) = 2018ApJ...853..160C, 2020ApJ...894L..14L, 2020A&A...635A...2S, 2016ApJ...833..209O; dN/dM
form (2) = 2019ApJ...872..121U, 2020ApJ...890...76N.

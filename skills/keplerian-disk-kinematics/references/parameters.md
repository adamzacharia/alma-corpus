# Parameter table: keplerian-disk-kinematics (full version)

Companion to `../SKILL.md`. "Typical value" is the value most often reported in the evidence pack lines, not an
independently validated default. "Supporting pack entries" is my count of distinct bibcodes in the pack's
parameter, assumption and excerpt lines that state the setting (a grep over those lines, not a paper-level
prevalence). Pack: 447 papers, 2012-2026. Many tagged papers use a Keplerian mask or Keplerian-shifted stacking for
chemistry and never fit a mass, so imaging rows include them; fitting rows mostly come from mass or geometry fits.

## Imaging and spectral setup

| Parameter | Typical value (reported settings) | Range seen | Supporting pack entries | Examples |
|---|---|---|---|---|
| Channel width | 0.1 km/s for 12CO disk cubes | 26 m/s instrumental width to 1.7 km/s | 28 | 2016ApJ...823L..18H (0.1), 2025ApJ...989....1Z (0.1 12CO, 0.2 others), 2025ApJ...989....3D, 2018ApJ...868..113T (0.16), 2024ApJ...967...68H (0.2), 2024ApJ...964..190L (0.20-0.43 per line), 2017ApJ...851..132C (0.4), 2026A&A...705A.201B (26 m/s instrumental width), 2024ApJ...975...72B (0.9 and 1.7) |
| Channel spacing vs resolution | state both | spacing half the resolution | 1 | 2024ApJ...966...63Y (13CN spacing 0.34 km/s, "half the velocity resolution") |
| Spectral resampling of stacked spectra | finer than data for line-centre fits | 40 m/s, 16x finer | 1 | 2019Natur.574..378T |
| Briggs robust | 0.5 (16 of 23 bibcodes that state a robust value, some among several values) | -1 to 2, natural | 23 robust + 3 natural | 0.5: 2026A&A...705A.202M, 2018ApJ...864..133T, 2024ApJ...972...88L, 2025ApJ...984L..18T, 2024RAA....24g5017M; 1.0: 2024ApJ...976..258K, 2026A&A...705A..49Z; 0.6: 2021A&A...648A..19W; 0.3: 2026MNRAS.545f2150S; 0.0 (also tested -2 and 2): 2024A&A...682A..55M; 0.5 or 2: 2026A&A...705A.198M; natural: 2018ApJ...868..113T, 2013ApJ...774...16R, weak lines in 2024ApJ...976..258K |
| Keplerian mask smoothing / padding | Gaussian kernel | sigma 0.7"; 0.5-1.25 beams | 2 | 2013ApJ...774...16R (0.7"), 2025NatAs...9.1486L (0.5, 1.25, 0.75 beam per isotopologue, "chosen by visual inspection") |
| Keplerian mask line width | power law in radius | V0 0.22-0.25 km/s at 100 au, q 0.3; dV0 500 m/s | 2 | 2021ApJ...911..150P, 2023ApJ...956..135W |

## Geometry, distance and emission surface

| Parameter | Typical value (reported settings) | Range seen | Supporting pack entries | Examples |
|---|---|---|---|---|
| Inclination | fixed from continuum or literature | prior, or free in forward models and some eddy fits | 17 fixed | fixed: 2020ApJ...891...48H, 2025ApJ...986L..11S (49.9 deg), 2019A&A...625A.118K (51.7 deg), 2021A&A...650A..59B (27 deg), 2019ApJ...884L..56T (5.8 deg), 2024A&A...692A.155K (i, PA, centre from continuum); Gaussian prior 46.7 +- 0.1 deg: 2019Natur.574..378T; free: 2016ApJ...829....6W, 2017ApJ...846L..26W, 2018ApJ...864..133T, 2026A&A...705A.201B |
| Distance | Gaia (DR2 in older papers, DR3 in newer) | 59 pc to 6.7 kpc | 6 Gaia + many fixed literature values | 2018ApJ...862L...2F (59 pc), 2021A&A...648A..19W (162 pc), 2017ApJ...844..158S (131/119/140 pc), 2024ApJ...967...15K (2.38 and 1.7 kpc), 2021A&A...650A.142M (6.7 kpc); Gaia DR2 2020ApJ...895..109F; Gaia DR3 2026A&A...705A..49Z; cloud distances from Zucker et al. 2026A&A...710A.140M |
| Emission surface, 12CO conical | psi ~13-15 deg (z/r = tan psi ~0.23-0.27) | 13.1-15 deg | 2 | 2018ApJ...868..113T (psi 13.1 deg), 2013ApJ...774...16R (~15 deg) |
| Emission surface, flared power law | z = z0 (r/1")^psi, psi an exponent | HCO+ z0 0.127", psi 0.81; 12CO and HCO+ z0 0.33", psi 0.76; 12CO Z0 265 mas, phi 1.29 | 3 | 2020ApJ...891...48H (HCO+, z/r = 0.127 at r = 1"), 2021AJ....162...99F (PDS 70, used for masks), 2019Natur.574..378T (two-power-law surface, 10 free parameters) |
| Emission surface, exponentially tapered | z0 (r/1")^psi exp(-(r/r_taper)^q_taper) | front and back sides | 3 | 2024A&A...682A..55M, 2026MNRAS.552g1700S, 2025A&A...694A.108P |
| Emission surface, assumed ratio | z/r = 0.13 | 0.13-0.4 | 2 | 2023PASJ...75..424O (0.13), 2025NatAs...9.1486L (0.4 for a water-line mask) |
| Emission surface, thin / midplane | geometrically thin | n/a | 31 (thin, flat or midplane) | 2018A&A...616A.100Y, 2019ApJ...880...69Y, 2021A&A...650A..59B (height "could not precisely constrain"), 2026A&A...705A.202M (elevated fits gave heights consistent with zero), 2024A&A...692A.155K (upper and lower surfaces indistinguishable) |
| PA convention | state it | north to redshifted or blueshifted major axis | 2 | 2024A&A...687A.311A (to the blueshifted semi-major axis), 2020ApJ...901...71S (PA_red) |

## Fitting and sampling

| Parameter | Typical value (reported settings) | Range seen | Supporting pack entries | Examples |
|---|---|---|---|---|
| Fitted radial range | outside the inner few beams | 0.065-0.7" to 0.26-3.75" | 8 | 2020ApJ...891...48H (0.2-2"), 2024ApJ...974..102S (0.33-1.4"), 2019ApJ...884L..56T (0.26-3.75"), 2025NatAs...9.1672Y (0.065-0.7"), 2025ApJ...994...98F (inner ~5 beams excluded), 2021A&A...650A..59B (inner 100 au discarded), 2020ApJ...905...89Y (r > 0.5" for a 0.45" beam) |
| Annulus width (rotation curve, stacking) | 1/4 beam | 1/5 beam to 2x beam minor axis; 4 au; 0.02-0.05" | 13 | 2018ApJ...868..113T, 2019Natur.574..378T (25 mas, ~1/4 beam), 2021ApJS..257....6G, 2024ApJ...965..147B, 2026A&A...705A.202M (20% of beam), 2023A&A...675A.131T (2x minor axis, step 1x), 2018ApJ...864..133T (4 au), 2024ApJ...970..153A (0.05"), 2026A&A...705A.201B (0.02") |
| Pixels in the likelihood | spatially independent | at least a beam FWHM apart | 1 | 2019Natur.574..378T |
| Velocity-map S/N cut | 5 sigma | 2.5-5 sigma | 4 | 2017ApJ...840...60B, 2024MNRAS.534.2904C, 2026A&A...705A.201B (peak < 5 sigma masked), 2020MNRAS.493L.108B (2.5) |
| Surface-extraction S/N clip | per tracer | 5.0 (12CO), 3.5 (13CO), 3.0 (CS) | 1 | 2025ApJ...984L..10G (disksurf, 5 iterations) |
| Sampler walkers / steps / burn-in | see examples | walkers 16-1000, steps 300-40,000, burn-in 50-80,000 | 17 | 2020ApJ...891...48H (48/3500/500), 2021A&A...648A..19W (200/5000 burn + 5000), 2019Natur.574..378T (64/10,000 burn + 10,000), 2025ApJ...994...98F (32/1000/300 for M*), 2025ApJ...994..214T (200, burn-in >= 1000), 2026A&A...705A..49Z (90, 250 burn), 2024A&A...687A.311A (256/40,000/6300), 2026MNRAS.552g1700S (230, burn-in 80,000 for 12CO), 2019ApJ...878..113H (1000 walkers), 2026ApJ..1003...64Y (100/15,000/2000) |
| Convergence rule | rarely stated | see examples | 4 | 2026A&A...705A..49Z (median change < 5% over last 500 steps), 2025ApJ...994..214T (slope of mean and median log M* < 1% over last 1000 steps, card), 2019ApJ...874..136S (autocorrelation ~1000 steps; walkers with chi2 - chi2min > 44 discarded), 2026A&A...705A.201B (visual) |
| M* prior | broad uniform | U(0,5) Msun; 0.1-2 Msun; 5-15 Msun massive; Gaussian 1.5 +- 0.15 | 5 | 2025ApJ...994...98F, 2019ApJ...884L..56T, 2019A&A...622A.206M, 2020MNRAS.491.1335R; walkers seeded from a Chabrier IMF in 2025ApJ...994..214T (card) |
| Inclination and distance priors | geometric on i, Gaussian on d | d ~ N(145, 20) pc; Gaussian in Gaia parallax | 2 | 2016ApJ...818..156C (sin(i)/2 prior on i, card), 2025ApJ...994..214T (parallax Gaussian of width 2 log(2) sigma_Gaia, card) |
| Stacking grid | M* step 0.1 Msun, i step 5 deg | M* 0.1-3, PA 0-355, i 5-85, v_sys step 0.1 km/s | 1 | 2018A&A...616A.100Y |
| Model grid (debris CO) | 5 parameters | M* 0.9-3.0 step 0.3, i 25-39 step 2 | 1 | 2013ApJ...776...77K |
| Channel and uv exclusions | exclude envelope or cloud ranges | velocity windows; uv < 100-200 klambda | 4 | 2024A&A...687A.308S (3.25-5.5 km/s for A; uv < 100 klambda for B, < 200 for W), 2019ApJ...883...22C (4.0-7.5 km/s, card), 2026A&A...705A..49Z (cloud ranges excluded from the likelihood, card), 2019ApJ...884...42S (channels near cloud v_sys ignored) |
| PV mean-position intensity threshold | 5 sigma | 5 sigma | 3 | 2017ApJ...849...56A, 2023ApJ...958...98F (filtered-out channels also excluded), 2019Sci...366...90A |
| PV power-law index | 0.5 (Keplerian) | fitted 0.50-0.53; outer ~1.2; ~1 for infall plus rotation | 4 | 2017ApJ...849...56A (0.50, outer 1.22), 2015ApJ...812...27A (0.53), 2024A&A...690A..46S (fixed 0.5), 2024ApJ...966...32E (p ~0.5 vs ~1) |

## Disk structure in forward models

| Parameter | Typical value (reported settings) | Range seen | Supporting pack entries | Examples |
|---|---|---|---|---|
| Gas structure | X_CO 1e-4, mu 2.37 | gamma fixed at 1 or fitted | 11 | X_CO/mu: 2017ApJ...846L..26W, 2018ApJ...854..130W, 2015ApJ...813...99F, 2025ApJ...994..214T, 2019ApJ...874..136S; gamma = 1 fixed: 2019ApJ...883...22C, 2015ApJ...798...85P, 2016ApJ...823L..18H, 2020ApJ...895..109F, 2015ApJ...806..154C, 2020ApJ...900....7H; gamma fitted: 2017ApJ...846L..26W, 2018ApJ...854..130W, 2024A&A...687A.308S |
| Isotopologue abundance | per paper | C17O = CO/2240 | 1 | 2024A&A...687A.308S |
| Temperature exponent q range | [0,1] | widened to [0,2] when walkers pile at q = 1 | 1 | 2025ApJ...994..214T |
| Turbulent broadening xi / v_turb | 0.01 km/s | n/a | 2 | 2016ApJ...823L..18H (xi), 2017NatAs...1E.130Z (v_turb) |
| Other line-width parameters (not interchangeable) | as defined per paper | see examples | 5 | 2013ApJ...776...77K (intrinsic line width 0.1 km/s), 2015ApJ...798...85P (b = 50 m/s), 2018A&A...616A..34H (micro-turbulence ~0.5 km/s), 2018A&A...614A.113H (turbulence 1 km/s, AGB), 2026A&A...705A..49Z (purely thermal, card) |

Line widths: the pack mixes turbulent xi, intrinsic line width, Doppler b and "turbulence" without a common
convention. Before comparing values, check whether each is a sigma, a Doppler b (sqrt(2) sigma) or a FWHM and
whether thermal broadening is included (general practice).

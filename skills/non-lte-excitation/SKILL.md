---
name: alma-non-lte-excitation
description: "Constrain gas kinetic temperature, H2 (or electron) density, column density and beam filling from ALMA line intensities or line ratios with non-LTE escape-probability codes (RADEX and its Python wrappers such as SpectralRadex, pyradex, ndRADEX; LVG codes), using chi2 grids, MCMC or nested sampling, and turn the result into abundances, masses or alpha_CO. Use when you have several transitions of a species whose levels may be sub-thermally populated (count independent observables against free parameters first; a single ratio cannot fix T_kin, n(H2), N/dv and filling factor together), when a CO/[CI] SLED or a dense-gas line set needs T_kin and n(H2), when debris-disk or cometary gas is excited by electrons or radiation, when absorption lines need excitation against the CMB or a bright continuum, or when checking someone else's RADEX/LVG result. Built from 370 ALMA papers (2012-2026)."
---

# Non-LTE excitation modelling (RADEX, LVG)

Fits a single-zone non-LTE model (statistical equilibrium plus an escape-probability or large velocity
gradient treatment of line trapping) to a set of line intensities or ratios to get T_kin, n(H2), N/dv and
sometimes a filling factor. The mistakes that matter most: (1) quoting a best-fit T_kin and n(H2) from a few
lines when the two are degenerate; many authors say the grid only gives trends or bounds
(2019MNRAS.486.2366M, 2021A&A...645A..45C, 2020A&A...641A.155V, 2024ApJ...972..147C), and H2CO temperatures
"can vary significantly depending on the assumed models and n(H2)" (2024ApJ...963..163I); (2) forming line
ratios from data with different beams, uv coverage or missing flux, which can change a ratio by a factor of 5
(ALMA 1.0 versus APEX 0.2 for the same DCO+ ratio in 2018A&A...617A.120M); (3) collision rates used outside
their temperature range or borrowed from another molecule without carrying that uncertainty
(2013ApJ...770..142N, 2020A&A...644A.133H, 2019ApJ...871..170M, 2025A&A...699A..70H).

> Always report: code and version, molecular data file and its source (LAMDA or new rates), collision
> partners and the H2 ortho/para ratio (separately from any molecular ortho/para or A/E ratio), geometry
> (expanding sphere, uniform sphere, slab), T_bg and any extra radiation field, line width or dv/dr, grid
> ranges and spacing, the priors for grids as well as samplers (and any reweighting when marginalizing),
> sampler settings and convergence evidence, how calibration error, correlated noise and upper limits enter
> the likelihood, how T_kin outside the rate tables is handled, and how the uncertainty interval was defined.

## When to use

- Several transitions of one species with different critical densities: fit T_kin, n(H2), N with RADEX,
  after counting independent observables against free parameters (a ratio cancels a common filling factor,
  and optically thin ratios do not fix the absolute column; four CO lines constrain only a few parameters in
  2017ApJ...835..174S; 3-4 CS lines per region "limits the reliability" in 2020MNRAS.496.5308S) (CO SLEDs in
  galaxies: 2017ApJ...835..174S, 2020A&A...643A..89P, 2024ApJ...971..176H; dense-gas tracers:
  2023ApJ...950...75I, 2021A&A...645A..45C, 2025A&A...696A..31G).
- A dedicated thermometer: para-H2CO line ratios (2024ApJ...969..143I, 2025A&A...693A.101T; per pixel with
  ndRADEX in 2024ApJ...963..163I), para-H2CS 7-6 ratios, nearly independent of n and N at n >~ 1e7 cm-3
  (2020ApJ...901...62L), the CH3CN K-ladder with n(H2) fixed from another tracer (2026A&A...707A.120H),
  many CH3OH lines (2020MNRAS.498L..87B), SO lines (2014ApJ...796..131O).
- One line, but you need to know how far the LTE column could be off: run RADEX over a plausible density
  and temperature range and report the spread (my recommendation, general practice). Example of the effect:
  for SO in the HH 212 jet, RADEX constrained by SO ratios and intensities at fixed n = 3e5 cm-3 gave columns
  a factor 2 (T_K = 500 K) to 4 (T_K = 50 K) above the LTE optically thin case (2015A&A...581A..85P).
- Low-density or electron-dominated gas: debris-disk CO and C I with electrons as colliders
  (2016MNRAS.460.2933M, 2018ApJ...861...72C, 2015MNRAS.447.3936M, 2020ApJ...905..122H), comae with H2O and
  electron collisions (2019ApJ...870L..26C, 2025NatAs...9.1476C), diffuse absorbing gas where T_ex sits near
  T_CMB (2020ApJ...889L...4L, 2014ApJ...795...28B); absorption needs its own branch (step 2b).
- Absorption against a quasar or AGN: RADEX to test whether collisions push T_ex above T_CMB before using
  T_ex as a CMB thermometer (HCO+ was dropped for that reason in 2026ApJ..1000..141K), or to fit n(H2) and
  T_bg together (2025ApJ...989...83B).
- Turning an excitation solution into gas mass or alpha_CO: alpha_CO(1-0) 0.2 to 0.5 in the NGC 1614 ring,
  scaling as 3e-4/[CO]/[H2] (2017ApJ...835..174S), 0.4 in a lensed merger (2019MNRAS.486.2366M),
  alpha_CO(3-2) 0.3 to 0.7 in a CMZ (2026ApJ..1003..231W), per-pixel alpha_CO in the Antennae with a factor
  ~3 model uncertainty (2024ApJ...971..176H). These values carry the adopted CO abundance. [CI] masses need
  the excitation factor Q_21 from the LVG solution (2024A&A...689A..67G).
- Testing whether observed rotational temperatures are sub-thermal: run RADEX grids, fit a rotation diagram
  to the model fluxes and compare T_rot with T_kin (2025A&A...693A.101T).

## When not to use

| Situation | Use instead |
|---|---|
| Density far above the critical densities, so the lines are thermalized; RADEX itself shows no density dependence (thermalized above 1e8 cm-3 in 2019ApJ...880...69Y; ratios density independent above 1e7 cm-3 in 2020A&A...633A...7V; LTE justified at n ~ 1e8 cm-3 in 2024ESC.....8..665M and at 2e7 cm-3 in 2024NewA..10902199M) | The `rotational-diagram-lte` skill (rotation diagrams, LTE synthetic spectra) |
| Many lines of a complex organic in a hot core, where you need T_rot and N_tot and not n(H2) | `rotational-diagram-lte`; use non-LTE only as a check on one species (2020MNRAS.498L..87B used LVG for CH3OH, then rotation diagrams for other iCOMs at T_rot = 100 K; 2025ApJ...991...59B went non-LTE only when the LTE fit was unsatisfactory) |
| Overlapping hyperfine components (CN, HCN, N2H+) | RADEX does not treat line overlap, so restrict the fit to resolved components (2021A&A...646A..59R) or use a code with hyperfine transfer (MOLLIE in 2024MNRAS.532L..36R) |
| Resolved disk, envelope or circumstellar shell with strong T and n gradients, fit in the uv plane or channel by channel | The `radiative-transfer-modelling` skill (LIME, RATRAN, RADMC-3D forward models: 2017A&A...605A..21C, 2013Sci...341..630Q, 2015ApJ...813..128Q, 2016MNRAS.460.2933M) |
| Only one transition and no independent density or temperature | Label any LTE column as conditional on LTE (a T_ex range does not validate LTE) and give excitation-dependent bounds: one CO line left the mass uncertain over two orders of magnitude (2019AJ....157..117M); Fomalhaut CO mass limits were computed across collider densities, with the radiation-dominated case as the strict limit (2015MNRAS.447.3936M); brightness cannot be turned into density with one line (2017ApJ...842L..24A) |
| Abundance profiles or chemical ages | The `chemical-modelling` skill; RADEX only sets the excitation (coupled UCLCHEM+RADEX fits in 2020MNRAS.496.5308S, 2026A&A...712A.201J) |
| Converting CO luminosity to mass with a fixed alpha_CO | The `gas-mass-co-conversion` skill |

## Steps

1. **Decide that non-LTE is needed.** Goal: know whether the lines can be sub-thermal. Method: compare the
   expected density with the lines' critical densities (general practice: n_crit = A_ul / sum of C_ul;
   optically thick lines thermalize at lower density). Papers quote them per line: 1.0e3 to 1.7e4 cm-3 at
   100 K for HCNH+ 2-1 to 5-4 (2025A&A...696A..31G), about 1e4 (J=2-1) to 5e6 cm-3 (J=8-7) at 20-30 K
   (2025ApJ...985...84L), effective values for dense-gas tracers (2017MNRAS.466...49J). A common sequence is
   LTE first, then RADEX on the same regions (2020A&A...644A..59K, through CASSIS); LTE columns can also set
   the non-LTE priors (2024A&A...686A..31B, 2022A&A...667A.131B).
2. **Measure intensities on matched data.** Goal: ratios that compare the same gas. Method: same velocity
   resolution, beam and aperture for every line (0.28 km/s, 0.96"x0.73", 0.75" box in 2014ApJ...796..131O);
   convert Jy/beam to K before RADEX (2018A&A...617A.120M); say whether integrated (2025A&A...696A..31G) or
   peak intensities are used. Check missing flux per line: flux lost above 4.6" (2017ApJ...835..174S);
   differential missing flux could raise H2CS ratios by up to 22% (2020ApJ...901...62L); 12m+7m versus
   12m+7m+TP temperatures agreed on average (ratio 1.04) but ranged 0.19-6.52 per pixel (2024ApJ...963..163I).
   Before reading a flux deficit as weak excitation, check continuum opacity, oversubtraction and line
   absorption (2025A&A...693A.101T; region fluxes highly uncertain because of absorption in
   2015ApJ...801...63M). Typical software: CASA.
2b. **Absorption lines (branch).** State the covering factor and the continuum the sightline sees (f_c = 1
   assumed and listed as a limitation in 2020A&A...637A...7M; f_c unconstrained without saturation in
   2026ApJ..1000..141K). Check that compared lines were observed together when the background varies
   (non-simultaneous data in 2020A&A...637A...7M; bands nine months apart in 2026ApJ..1000..141K; two visits
   averaged in 2021A&A...652A...5M). Set T_bg to the CMB at the absorber redshift (5.14 K at z = 0.89 in
   2020A&A...637A...7M; T_rot = T_CMB for polar species in 2014A&A...566A.112M) or fit it
   (2025ApJ...989...83B). Expect one-sided results: density an upper and column a lower bound
   (2014ApJ...795...28B); n(H2) > 1100 cm-3 and T_bg > 45 K because the contours did not close
   (2025ApJ...989...83B).
3. **Pick molecular data and colliders.** Goal: rate coefficients that cover your T_kin. Method: LAMDA
   files (2018A&A...617A.120M, 2014ApJ...785..149S, 2020MNRAS.496.5308S). H2 is the usual sole partner
   (2020A&A...644A..59K, 2023ApJ...950...75I, 2024A&A...686A..47M); some rate sets exist only for para-H2
   (2024ApJ...966...63Y, 2022A&A...664A.171V). Electrons for debris disks and comae (2016MNRAS.460.2933M,
   2020ApJ...898..146M, 2025NatAs...9.1476C); they dominate only above ~0.01 of the CO, C, C+ and O density
   (2020ApJ...905..122H). When rates are missing, papers borrow or scale them: HCO+ rates for N2H+
   (2019ApJ...882..160Q, 2020A&A...644A.133H), He rates scaled to H2 by 1.363-1.4 (2020MNRAS.492.1180R,
   2024ApJ...977...38B), H2 rates for H2O or CO collisions in comae (2020NatAs...4..861C), SiS-H2 rates for
   AlCl (2021A&A...655A..80D); more in `references/parameters.md`. New rates were computed with MOLSCAT
   for HCNH+ (2025A&A...696A..31G). Write down which rates are borrowed and how T_kin outside the table is
   treated (2025A&A...699A..70H clamped it to the nearest table temperature, 3-250 K for CH3OH and 10-300 K
   for H2CO; 2024A&A...689A..64B limited the grid to the rate range).
4. **Fix the non-fitted inputs.** Goal: an explicit, defensible setup. Method: the CMB part of T_bg is
   2.73 K locally and 2.73(1+z) K at redshift (2019ApJ...873...50D; 10.9 K in 2021A&A...645A..45C; 18.135 K
   at z = 5.655 in 2021ApJ...907...62R). Then decide whether other radiation matters, which the CMB alone
   does not represent: a ~350 K background from the continuum brightness (2025ApJ...995..211I); 2.73 K "may
   be inappropriate" at an AGN (2020MNRAS.496.5308S); CMB, stellar and dust radiation for Fomalhaut CO
   (2015MNRAS.447.3936M); dust continuum excitation of C2H (2025A&A...696A.100G); a 700 K blackbody IR field
   for AlCl (2021A&A...655A..80D). For radiation-dominated gas (debris disks, comae) use a code that takes
   the frequency-dependent field (the `radiative-transfer-modelling` skill). Line width from the measured
   spectra (2024A&A...689A..64B; average per region in 2019PASJ...71...68K). Geometry had negligible impact in
   2020MNRAS.496.5308S and 2025ApJ...989...83B, but test it. For LVG codes, X/(dv/dr) is an object-specific
   choice: fit it or justify it (dv/dr fitted over 1e2-1e6 m/s/pc in 2019MNRAS.486.2366M; [CO]/[H2](dv/dr)^-1
   1e-3 to 1e-7 in 2020ApJ...902..109B; dv/dr from each cloud's linewidth and radius in 2023ApJ...958...53S;
   X(CO)/(dv/dr) reported as one degenerate quantity in 2024ApJ...969..102N); 1e-5 km-1 s pc is an adopted
   assumption in several galaxy studies (2020A&A...641A.155V, 2024A&A...686A..47M, 2021ApJ...907...62R).
5. **Run the grid or sampler.** Goal: a likelihood over T_kin, n(H2), N/dv (plus filling factor when lines
   are diluted). Method: a chi2 grid over RADEX models is the most frequent phrasing. My count of the pack's
   fitting-method aggregate (42 step-level entries, not deduplicated by paper): 19 grid searches (chi2,
   log-ratio or grid-Bayesian), 5 MCMC (3 for an excitation fit), 4 least squares, 6 by-eye or manual; it
   does not show what most of the 370 papers did. At least 14 papers state walkers, MCMC or emcee (my count
   of parameter lines and excerpts). Spacing is mixed, often linear in T_kin and log in n and N (40 log steps
   per axis in 2020A&A...643A..89P; T_kin in 10 K steps with N_CO in 0.1 dex steps in 2016ApJ...821..112K).
   Samplers: emcee (2025A&A...696A..31G, 2026A&A...707A.120H), with chain length set from the autocorrelation
   time (100 tau, 5 tau burn-in, 19,000 effective samples in 2023ApJ...950...75I); UltraNest nested sampling
   with SpectralRadex (2024A&A...686A..31B); grid Bayesian PDFs (2024ApJ...971..176H); a hierarchical model
   across regions (2026A&A...712A.201J). More grids and sampler settings in `references/parameters.md`.
   Iteration counts are not convergence evidence: show mixing and enough effective samples (the cards flag
   convergence diagnostics as missing for 2025A&A...696A..31G, and walker initialization and convergence
   checks for 2020ApJ...892...99C). State priors for grids too: 2020A&A...643A..89P reweighted the grid to
   get uniform priors on derived quantities; 2024ApJ...969..143I tried flat linear and flat log priors on the
   filling factor; 2018ApJ...864..133T reran with a linear instead of log prior on the Mach number. Test any
   prior that moves the answer. Add flux calibration error in quadrature (5% for CO 2-1 and 10% for other
   lines in 2019MNRAS.486.2366M; 15% in 2024A&A...689A..64B), or fit a bounded flux-scale factor per band,
   which carries the correlation between lines sharing a calibration (up to 5% for Band 5 or J=2-1 and 10%
   for Bands 6-7 in 2023ApJ...950...75I and 2023ApJ...954..148I); 2014ApJ...785..149S added a 15% ratio
   uncertainty without calling it calibration. A line shared by two ratios also correlates their errors
   (general practice): use a covariance or fit intensities rather than ratios. For resolved fits, model
   correlated noise: independent beams and adjacent-channel correlation (2016MNRAS.460.2933M); sigma x sqrt(2)
   when the channel width is half the velocity resolution (2024ApJ...966...63Y); Gaussian-process noise
   (celerite), correlated annuli within a beam and uncorrected beam smear in the inner 90-100 au
   (2018ApJ...864..133T). Include upper limits in the likelihood (an erf term in 2020A&A...643A..89P).
6. **Constrain the degeneracies.** Goal: exclude solutions you can argue are unphysical for this object,
   stated as conditional modelling assumptions. Method: tau < 100 (2014ApJ...785..149S,
   2019ApJ...873...50D, 2017A&A...604A...2S); K_vir >= 1 (2019MNRAS.486.2366M; gridded 1-100 in
   2024A&A...689A..67G; 2014ApJ...785..149S used a virialized K_vir prior but its card lists the cutoff as
   not stated); gas mass below the dynamical mass and column length below the region size
   (2013ApJ...777..126S, 2022PASJ...74.1429T); filling factor <= 1 (2024ApJ...969..143I); dust-based density
   to rule out low-density solutions (2024ApJ...968L..11G); a T ceiling from the CO rotational temperature
   (2020MNRAS.496.5308S); n(H2) fixed from another tracer (2026A&A...707A.120H) or because of the T-n
   degeneracy (2018MNRAS.475..448T; four parameters could not be fit together in 2020ApJ...905..122H);
   T_kin fixed where other species set it (2017MNRAS.469.3347M). If one phase does not fit, fix a cold phase
   from outer gas and fit a warm one (2017ApJ...835..174S) or compare one-component, two-component and
   turbulent (log-normal density) models (2021ApJ...921...97J, 2019ApJ...880....2W). Reject a secondary mode
   only with a stated physical reason (a > 1000 K solution in 2024A&A...689A..67G).
7. **Derive the science quantity.** Goal: abundance, mass or conversion factor. Method: X = N/N(H2) with a
   stated reference abundance (X_CO = 1e-4 in 2015A&A...581A..85P). Mass of the tracer molecule:
   M = f Omega N d^2 m (2017MNRAS.469.3347M), where Omega is the beam (or aperture) solid angle, f the
   filling factor of the emission within it, N the column of the emitting gas from the fit (source-averaged;
   if your N is already beam-averaged drop f, or dilution is counted twice), d the distance and m the mass of
   one molecule; this gives the SiO or CO mass, not the gas mass. For total gas, divide the tracer column by
   its abundance and multiply by the mass per H2 including helium, e.g. 1.4 m_H2 N(C17O)/X(C17O) times the
   beam area for the HH 212 disk (2015A&A...581A..85P); helium factors 1.36 (2025ApJ...991...53C,
   2024A&A...689A..67G) and 1.4 (2015A&A...581A..85P) both appear, so say which. alpha_CO from the RADEX
   N(H2) and the CO luminosity (2017ApJ...835..174S): keep the abundance scaling (0.2-0.5 scales as
   3e-4/[CO]/[H2]), state the CO transition and units, and propagate or bracket the abundance (x_CO is the
   largest alpha_CO uncertainty in 2017ApJ...840....8S and cannot be constrained by the modelling in
   2024ApJ...971..176H; [CO]/[H2] from 8e-6 to 6.5e-4 is adopted across the pack). For [CI], take Q_21 from
   the LVG posterior and test its extremes (the upper Q_21 lowered the tail H2 mass by ~30% in
   2024A&A...689A..67G). Report marginalized 16th/84th percentiles (2025A&A...696A..31G) or chi2 confidence
   ranges (90% in 2017ApJ...835..174S; min chi2_r + 2.30 for two parameters in 2021A&A...652A...5M).
8. **Validate.** See Verification checks.

## Parameter defaults and ranges

Counts are my own counts of distinct bibcodes in the pack's parameter and assumption lines (354 papers have
such lines); regex-based counts are marked as approximate. Full grid list in `references/parameters.md`.

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| T_kin grid | log or linear, from ~10 K (or T_CMB) to a few 100 K | mostly 3-400 K up to T_CMB-1000 K; 50-500 K for warm tracers; one grid to 6300 K (2018ApJ...868...95M) | ~50 state a range (regex count) | 2017ApJ...835..174S (10-300 K), 2020A&A...643A..89P (3-400 K), 2024A&A...686A..47M (T_CMB-1e3 K), 2025A&A...696A..31G (50-500 K), 2024ApJ...963..163I (580 values, 10-300 K) |
| n(H2) grid | 1e2 to 1e7 cm-3 | 10-1e6 (SLEDs) up to 1e5-1e12 (disks, hot cores) | many (regex count ~80, includes non-grid densities) | 2017ApJ...835..174S, 2023ApJ...950...75I, 2014ApJ...785..149S, 2025A&A...693A.101T, 2024ApJ...966...63Y (1e6-1e12) |
| N_CO/dv (CO grids) | 1e14-1e20 cm-2 (km/s)-1, log steps | 1e14-1e20; fixed 2.5e16 in 2020ApJ...898...61I | 8: 2014ApJ...785..149S, 2019ApJ...873...50D, 2020A&A...643A..89P, 2024A&A...686A..47M, 2020ApJ...898...75I, 2020ApJ...898...61I, 2019ApJ...880....2W, 2024ApJ...971..176H | see count column |
| N_CO (column, CO grids) | log steps | 1e12-1e22 cm-2; fixed 1e16 and 1e17 in 2020MNRAS.493.3744F | 8: 2016ApJ...821..112K, 2017A&A...608A..38O, 2018ApJ...868...95M, 2020MNRAS.493.3744F, 2013ApJ...777..126S, 2021MNRAS.500.5500B, 2023ApJ...942...25F, 2026ApJ...997L..19Q | see count column |
| N (dense-gas tracers) | fixed or free | N/dv fixed 1e14 for HCN, HCO+, HNC (2021A&A...645A..45C); N_HCO+ fixed 1e16 cm-2 (2023ApJ...950...75I); free with log priors 1e12-1e18 (2024A&A...688A.130H) | many | see examples |
| T_bg | CMB: 2.73 K, or 2.73(1+z) K at redshift | CMB 2.7-2.73 K locally to 18-19 K at z ~ 6 (2021ApJ...907...62R, 2022PASJ...74.1429T); non-CMB 10 or 100 K (2017ApJ...837...60B), 15.5 K (2020A&A...641A.124L), ~350 K continuum (2025ApJ...995..211I), fitted 30-300 K (2025ApJ...989...83B) | ~60 mention a background or CMB (regex count) | 2019ApJ...873...50D, 2021A&A...645A..45C, 2020A&A...637A...7M |
| Geometry | uniform/static sphere or expanding sphere (LVG) | also slab (semi-infinite or thin) | ~21 expanding sphere or LVG, 7 slab (regex counts); spherical mentions also include non-RADEX models | 2017ApJ...835..174S, 2023ApJ...950...75I, 2018ApJ...864..133T, 2024A&A...689A..64B |
| H2 ortho/para (collider) | 3 | thermal/LTE OPR; 0.25 (2025A&A...696A..31G); temperature-dependent with a 1e-3 floor (2018A&A...617A.120M, 2017A&A...605A..21C); para-H2 only | 28 stated for H2 (my count): 15 at 3, 5 thermal, 2 T-dependent, 1 at 0.25, 4 para-H2 only, 1 ignored (2021A&A...646A..72H); ambiguous (2019ApJ...875...96N, 2017A&A...602A..42K, 2025A&A...698A.261B) not counted | at 3: 2024A&A...686A..47M, 2020A&A...644A..59K, 2024ApJ...977...38B, 2026ApJ...997L..19Q; thermal: 2020A&A...643A..89P, 2018ApJ...864..133T, 2024ApJ...967..164X; para only: 2021A&A...652A...5M, 2024ApJ...966...63Y |
| Molecular ortho/para (emitter) | 3 | 1 or 3 tested for c-C3H2 (2021ApJ...911...29C) | 8 | H2CO and CH2CO (2026A&A...707A.120H), c-C3H2 (2018A&A...617A.120M), H2O (2013ApJ...770..142N), H2S and H2CO (2025A&A...703A.282R); para-H2CO lines only, so none needed (2024ApJ...969..143I) |
| A/E or E/A ratio | 1 | A and E columns fitted separately (2024A&A...688A.130H, 2021A&A...652A...5M) | 10 at 1 | CH3OH (2020MNRAS.498L..87B, 2026A&A...707A.120H, 2025ApJ...991...59B, 2022A&A...664A.171V), CH3CN (2015ApJ...814..143A) |
| [CO]/[H2] | 1e-4 | 8e-6 to 6.5e-4 | about 30 at 1e-4 (regex count); 3e-4 or 3.2e-4 in at least 6 | 2015A&A...581A..85P, 2020ApJ...898...75I; 3e-4 in 2017ApJ...835..174S and 2024ApJ...971..176H; 6e-5 in 2019PASJ...71...68K; 1.6e-5 in 2023ApJ...958...53S |
| Line width | measured average per region | 0.14 km/s (disks) to 850 km/s (QSO host) | many | 2024A&A...689A..64B, 2018A&A...617A..28S, 2020MNRAS.493.3744F |
| Filling factor | 1, or free and <= 1 | 1e-5 to 1; theta_S^2/(theta_MB^2 + theta_S^2) from a source size (2025A&A...699A..70H) | ~30 mention filling or dilution | 2020A&A...644A..59K, 2024ApJ...969..143I, 2024ApJ...971..176H (0.05-1 grid), 2014ApJ...796L..15S |
| Calibration error | 10-15% in quadrature, or a fitted scale factor | 5-15% | 9 identified as calibration: 2019MNRAS.486.2366M (5%, 10%), 2024A&A...689A..64B, 2016ApJ...831..101B, 2025A&A...698A.261B (15%), 2013ApJ...770..142N, 2022MNRAS.515..543C, 2019ApJ...886...51C (10%); fitted scale up to 5-10% in 2023ApJ...950...75I, 2023ApJ...954..148I | other added terms not called calibration: 15% on ratios (2014ApJ...785..149S), 20% ratio error (2019ApJ...872..200H), 20% on CO intensities (2026A&A...711A.159M) |
| Optical depth prior | tau < 100 | 0-100 | 6 | 2014ApJ...785..149S, 2019ApJ...873...50D, 2017A&A...604A...2S, 2017ApJ...840....8S, 2013ApJ...777..126S, 2020MNRAS.496.5243H |
| MCMC | emcee, 16/50/84 percentiles | 8-256 walkers (8 = 4x two free parameters for CH3CN in 2026A&A...707A.120H; 200 in the LTE cube fit of 2020ApJ...892...99C); chain length from autocorrelation time in 3 | 8 with stated settings (one an LTE cube fit) | 2025A&A...696A..31G, 2026A&A...707A.120H, 2018ApJ...864..133T, 2023ApJ...950...75I, 2025ApJ...991L...6T, 2024ApJ...967..164X, 2022A&A...667A.131B |

## Software

Counts are the pack's aggregate of matched analysis steps naming each code (not distinct papers; the
aggregate lists codes named in 2 or more steps); I dropped entries from clearly off-topic papers
(KINICH-PAKAL for a stellar chromosphere, cprops and clumpfind).

| Code | Steps naming it | Used for |
|---|---|---|
| RADEX | 231 (plus SpectralRadex 17, pyradex 8, ndRADEX 3, pythonradex 3, myRadex 3) | single-zone escape probability grids; the default (2017ApJ...835..174S, 2025A&A...696A..31G). SpectralRadex with emcee (2026A&A...707A.120H, 2022A&A...667A.131B) or UltraNest (2024A&A...686A..31B); ndRADEX for per-pixel H2CO grids (2024ApJ...963..163I); pythonradex for electron-excited C I/C II in debris disks (2018ApJ...861...72C); pyradex grids interpolated in emcee (2018ApJ...864..133T); myRadex for LVG SLEDs (2019MNRAS.486.2366M, 2024A&A...689A..67G) |
| LIME | 33 | 3D non-LTE line transfer: full radiative transfer differing by at most a factor 1.2 from the simpler models in 2018ApJ...861...72C; synthetic fluxes within ~10% of observed, checking a RADEX solution, in 2021MNRAS.500.5500B; an LTE/non-LTE check of an LTE cube model (LTE flux 1.3x the LIME non-LTE flux) in 2020ApJ...892...99C, which is not a RADEX comparison; comae (2019ApJ...870L..26C, 2020NatAs...4..861C) |
| RATRAN | 22 | 1D/2D disk and envelope models fit on visibilities (2013Sci...341..630Q, 2015ApJ...813..128Q) |
| emcee | 20 (corner 3) | posterior sampling over RADEX grids |
| UltraNest | 4 | nested sampling with SpectralRadex (2024A&A...686A..31B) |
| CASA | 16 | imaging and spectrum extraction before modelling |
| CASSIS | 10 | chi2 grids wrapping LTE and RADEX models (2020A&A...644A..59K); MCMC inside CASSIS (2019MNRAS.483.2014H) |
| LAMDA | 9 (plus "LAMDA database" 4) | molecular data files (2014ApJ...785..149S, 2020MNRAS.496.5308S) |
| lmfit, MPFIT, SciPy | 6, 3, 3 | least-squares fits (Levenberg-Marquardt via MPFIT in PySpecKit in 2021A&A...646A..59R) |
| RADMC-3D, DALI | 5, 5 | non-LTE disk models with electron colliders (2016MNRAS.460.2933M); densities from a DALI model (2025A&A...693A.101T) |
| Other LVG and non-LTE codes | GRELVG 5, SUBLIME 4, MOLLIE 3, ALI 3, XCLASS 3, authors' LVG code 2, TORUS 2 | e.g. CH3OH LVG grid (2020MNRAS.498L..87B); comae (SUBLIME in 2024PSJ.....5..221C); HCN hyperfine (MOLLIE in 2024MNRAS.532L..36R); own LVG code checked against RADEX (2020ApJ...905..122H); 3D tests (2019MNRAS.485.2457H) |
| Coupled chemistry and others | UCLCHEM 2, Teng et al. multiline Bayesian code 2, MOLSCAT 2, SHAPE/shapemol 3/2, PDR Toolbox | chemistry-constrained SLEDs (2020MNRAS.496.5308S); per-pixel CO/13CO grids (2024ApJ...971..176H); new rates (2025A&A...696A..31G); AGB shells (2018A&A...612L..11S); PDR follow-up (2017ApJ...835..174S) |

## Pitfalls

- **T-n degeneracy.** Few lines leave T_kin and n(H2) correlated: "poorly constrained and correlated"
  (2019MNRAS.486.2366M), "highly degenerate" (2020A&A...641A.155V, 2024ApJ...972..147C); four CO lines
  constrain few parameters (2017ApJ...835..174S); HCNH+ gave densities but weak temperatures
  (2025A&A...696A..31G); T_kin, n and line width stayed poorly constrained by MCMC at most resolutions
  (2022A&A...667A.131B); CS stayed poorly constrained with the source size fixed (2024A&A...689A..64B).
- **Grid edges and one-sided answers.** RADEX temperature upper bounds were unconstrained
  (2020MNRAS.496.5308S); pixels at the 300 K grid edge are lower limits (2024ApJ...963..163I). Thermometer
  errors grow with T: ~100 K at an H2CO ratio of 0.4, five times that at 0.2 (2024ApJ...963..163I); > 25%
  above 500 K for H2CS (2020ApJ...901...62L); H2CO errors underestimated above 80 K (2024ApJ...977...37N).
- **Optically thick lines.** Thick SO gave T_kin but no density or abundance (2014ApJ...796..131O); thick
  HCN gives lower-limit abundances (2019A&A...632A.101T); high optical depth can break the simple LVG
  approximation (2020ApJ...905..122H).
- **Single component for multi-phase gas.** No single model fit the stacked SPT spectrum (min chi2 = 10.4
  for 3 dof, 2014ApJ...785..149S); one component was inadequate for ULIRGs (2024A&A...686A..47M) and missed
  a z = 6.3 quasar SLED shape (2019ApJ...880....2W); RADEX assumes one homogeneous medium in which all lines
  sample the same gas (2020ApJ...898...75I, 2014A&A...570A..28V).
- **SLED without its peak.** If the CO SLED peak is not observed the LVG solution is not constrained
  (2019A&A...628A..23A).
- **Borrowed, truncated or clamped rates.** HDO rates stop at 450 K, so the highest lines could not be
  modelled (2013ApJ...770..142N); N2H+ with HCO+ rates gives a factor 3-5 density uncertainty
  (2020A&A...644A.133H); rate uncertainties up to 50% were left out of the errors (2019ApJ...871..170M);
  T_kin beyond the table was clamped (2025A&A...699A..70H); no state-to-state rates for CO, C and C+
  collisions (2020ApJ...905..122H).
- **Neglected colliders, pumping and overlap.** No electron or H collisions (2020A&A...644A..59K;
  2016A&A...590A.127W treats its density as a proxy for that reason); infrared pumping not considered or
  only partly included (2014A&A...570A..28V, 2015ApJ...814..143A); vibrational pumping excluded
  (2013ApJ...770..142N); RADEX does not treat hyperfine line overlap (2021A&A...646A..59R).
- **Beam dilution.** Set to 1 for simplicity (2025A&A...696A..31G, 2020A&A...644A..59K), but unresolved
  emission makes columns too low (2025A&A...693A.101T). Temperature and filling factor were highly
  correlated (2020ApJ...905..122H); a J-dependent filling factor was not fitted because it would weaken the
  other constraints (2020MNRAS.496.5308S); forcing 13CO to share the CO filling factor may underestimate its
  T_ex (2024ApJ...971..176H).
- **Errors too small.** Formal errors exclude systematics from fixed parameters (2026A&A...707A.120H),
  calibration (2020ApJ...892...99C) and model choice (2020A&A...644A..59K, 2021A&A...655A..80D); H2CS
  errors are intensity-fit errors only (2020ApJ...901...62L); errors in a 4D RADEX space were "not
  straightforward to define" (2021A&A...652A...5M).
- **Tracers at different resolution.** A factor-four beam difference stopped a quantitative NH3 versus H2CO
  temperature comparison (2024ApJ...977...37N); several ratios used degraded data (2014A&A...570A..28V).
- **Lensing.** Differential magnification biases SLED ratios; model apparent and intrinsic ratios
  separately (2019ApJ...873...50D; not accounted in 2014ApJ...785..149S; assumed negligible in
  2022PASJ...74.1429T).
- **What the cards rarely state.** Grid ranges and steps, RADEX background and line width, sampler
  convergence and the likelihood form are often missing (cards for 2015A&A...581A..85P,
  2024ApJ...969..143I, 2020MNRAS.493.3744F, 2018A&A...617A.120M). The pack's not-stated aggregate is
  dominated by imaging settings: CASA version (29), line-free channels for continuum subtraction (16 plus
  many variants), self-calibration intervals (11), flux scale uncertainty (10). State all of these.

## Verification checks

What papers did:

- Reconstruct the best-fit SLED or ratios and overplot the data (2017ApJ...835..174S, 2020A&A...643A..89P,
  which flags the one line it misses); draw predicted intensities from the 16-84 percentile posterior
  (2024A&A...688A.130H).
- Compare predicted with observed fluxes line by line: the predicted [CI] flux of the CO+[CI] SLED model
  against the observed value (2019MNRAS.486.2366M; [CI] was part of the modelled SLED, so this is not a
  held-out test). A true held-out line is stronger (my recommendation).
- Forward-model the solution with a full transfer code: LIME within a factor 1.2 (2018ApJ...861...72C) or
  fluxes within ~10% (2021MNRAS.500.5500B); check an own LVG code against RADEX (2020ApJ...905..122H).
- Compare with LTE: RADEX columns 2-4x the LTE thin value (2015A&A...581A..85P); LTE within ~20%
  (2024ApJ...969..143I); T_Radex slightly above T_LTE in almost all cores (2024ApJ...963..163I); in an LTE
  cube fit, LTE flux 1.3x the LIME non-LTE flux (2020ApJ...892...99C).
- Check sensitivity to fixed inputs: line width 3.0 or 4.0 km/s (2020MNRAS.498L..87B); T_kin 10-300 K
  changing T_ex and N by < 1% (2020ApJ...889L...4L); T_R within 10% over 1e6-1e12 cm-3 and 100-500 K
  (2018A&A...612L..11S); source size +-50% (2018ApJ...861...72C); collision rates x2 changing intensities
  by a few percent (2019ApJ...870L..26C) or x0.1-10 changing HCN production by 2% (2020NatAs...4..861C);
  density and column across the observed core range (2024ApJ...963..163I); geometry (2020MNRAS.496.5308S);
  12C/13C (2014A&A...570A..28V); alternative abundances (2019PASJ...71...68K).
- Recover known inputs from mock data (22 mock SLEDs in 2014ApJ...785..149S).
- Compare marginalizations of the same grid (2024ApJ...969..143I; 1D PDF median versus 1DMax in
  2024ApJ...971..176H), and two independent ratios of one species (2020ApJ...901...62L).
- Confirm the fitted lines are optically thin where you assume so (RADEX tau <~ 1 in 2020ApJ...889...43Z;
  in 2020MNRAS.498L..87B, predicted opacities 0.3-0.5 for methyl formate and ~0.2 for ethanol in the
  rotational-diagram stage, not for the methanol lines of the LVG fit).
- Cross-check with independent data or tracers: APEX ratio (2018A&A...617A.120M), earlier CH3CN
  temperatures (2026A&A...707A.120H), IR-based G0 (2017ApJ...835..174S), three gas-mass estimates for
  alpha_CO (2021ApJ...921...97J), whether one density reconciles NH3 and H2CO temperatures (only four
  clouds did in 2024ApJ...977...37N).

What a careful referee adds:

- Show the full 2D posterior or chi2 surface in T_kin versus n(H2), not only a best fit.
- Confirm that the best fit is not on a grid edge and that the rate files cover the fitted T_kin.
- Confirm the line ratios use matched beams and the same recovered scales, and that continuum opacity,
  continuum subtraction and absorption cannot explain a flux deficit.
- Propagate calibration error (with its correlations) and the borrowed-rate uncertainty into the quoted
  intervals.
- For MCMC or nested sampling, ask for convergence evidence (mixing, effective sample size, stability across
  runs), not just walker and step counts.
- Check that free parameters do not outnumber independent observables; report unidentifiable quantities as
  bounds.

## Source cards

Full list in `references/sources.md` (370 papers). Most informative for this technique:

- 2017ApJ...835..174S (single- and two-phase RADEX on a resolved CO SLED, PDR follow-up)
- 2020A&A...643A..89P (64000-model RADEX grid, Bayesian with upper limits)
- 2024ApJ...971..176H (per-pixel 5D grid Bayesian alpha_CO, x_CO dependence)
- 2023ApJ...950...75I (HCN/HCO+ ratios, emcee with autocorrelation-based chains, fitted flux scales)
- 2025A&A...696A..31G (new rates with MOLSCAT, RADEX + emcee)
- 2026A&A...707A.120H (density fixed from C17O, CH3CN T_kin with SpectralRadex + emcee)
- 2024ApJ...963..163I (per-pixel H2CO thermometer, grid-edge lower limits, missing-flux test)
- 2020ApJ...901...62L (H2CS thermometer, differential missing flux, opacity check)
- 2014ApJ...785..149S (tau and K_vir priors, mock recovery test)
- 2019ApJ...873...50D (CMB at redshift, lensing-corrected ratios)
- 2019MNRAS.486.2366M (myRadex LVG, calibration error, K_vir >= 1, [CI] flux comparison)
- 2024A&A...689A..67G (MyRadex [n, T, K_vir] MCMC, Q_21 for [CI] masses)
- 2018ApJ...864..133T (pyradex grid in emcee, resolved disk annuli, correlated noise)
- 2020MNRAS.496.5308S (CS SLEDs, geometry test, filling factor, UCLCHEM coupling)
- 2021A&A...646A..59R (CN hyperfine with RADEX, line-overlap limit)
- 2015A&A...581A..85P (non-LTE versus LTE columns)
- 2018ApJ...861...72C (electron-excited C I with pythonradex, LIME check)
- 2020ApJ...905..122H (debris-disk CO with H2 or electron colliders, fixed density)
- 2025ApJ...989...83B (absorption: n(H2) and T_bg grid, lower limits)
- 2020A&A...644A..59K (CASSIS LTE then RADEX, admitted systematics)
- 2018A&A...617A.120M (DCO+ ratios, ALMA versus APEX)

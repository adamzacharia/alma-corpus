---
name: alma-non-lte-excitation
description: "Constrain gas kinetic temperature, H2 (or electron) density, column density and beam filling from ALMA line intensities or line ratios with non-LTE escape-probability codes (RADEX and its Python wrappers, LVG codes), using chi2 grids or MCMC, and turn the result into abundances, masses or alpha_CO. Use when you have several transitions of a species whose levels may be sub-thermally populated (count independent observables against free parameters first; a single ratio cannot fix T_kin, n(H2), N/dv and filling factor together), when a CO/[CI] SLED or a dense-gas line set needs T_kin and n(H2), when debris-disk or cometary gas is excited by electrons or radiation, or when checking someone else's RADEX/LVG result. Built from 154 ALMA papers (2012-2026)."
---

# Non-LTE excitation modelling (RADEX, LVG)

Fits a single-zone non-LTE model (statistical equilibrium plus an escape-probability or large velocity
gradient treatment of line trapping) to a set of line intensities or ratios to get T_kin, n(H2), N/dv and
sometimes a filling factor. The mistakes that matter most: (1) quoting a best-fit T_kin and n(H2) from a few
lines when the two are degenerate; many authors say the grid only gives trends or bounds
(2019MNRAS.486.2366M, 2021A&A...645A..45C, 2020A&A...641A.155V, 2024ApJ...972..147C); (2) forming line ratios
from data with different beams, uv coverage or missing flux, which can change a ratio by a factor of 5
(ALMA 1.0 versus APEX 0.2 for the same DCO+ ratio in 2018A&A...617A.120M); (3) collision rates used outside
their temperature range or borrowed from another molecule without carrying that uncertainty
(2013ApJ...770..142N, 2020A&A...644A.133H, 2019ApJ...871..170M).

> Always report: code and version, molecular data file and its source (LAMDA or new rates), collision
> partners and the H2 ortho/para ratio (separately from any molecular ortho/para or A/E ratio), geometry
> (expanding sphere, uniform sphere, slab), T_bg and any extra radiation field, line width or dv/dr, grid
> ranges and spacing, the priors for grids as well as samplers (and any reweighting when marginalizing),
> sampler settings and convergence evidence, how calibration error, correlated noise and upper limits enter
> the likelihood, and how the uncertainty interval was defined.

## When to use

- Several transitions of one species with different critical densities: fit T_kin, n(H2), N with RADEX,
  after counting independent observables against free parameters (a ratio cancels a common filling factor,
  and optically thin ratios do not fix the absolute column; four CO lines constrain only a few parameters in
  2017ApJ...835..174S) (CO SLEDs in galaxies: 2017ApJ...835..174S, 2020A&A...643A..89P, 2020MNRAS.493.3744F; dense-gas tracers:
  2019PASJ...71...68K, 2021A&A...645A..45C, 2025A&A...696A..31G).
- A dedicated thermometer: para-H2CO line ratios (2024ApJ...969..143I, 2025A&A...693A.101T), the CH3CN
  K-ladder with n(H2) fixed from another tracer (2026A&A...707A.120H), many CH3OH lines
  (2020MNRAS.498L..87B), SO lines (2014ApJ...796..131O).
- One line, but you need to know how far the LTE column could be off: run RADEX over a plausible density
  and temperature range and report the spread (my recommendation, general practice). Example of the effect:
  for SO in the HH 212 jet, RADEX constrained by SO ratios and intensities at fixed n = 3e5 cm-3 gave columns
  a factor 2 (T_K = 500 K) to 4 (T_K = 50 K) above the LTE optically thin case (2015A&A...581A..85P).
- Low-density or electron-dominated gas: debris-disk CO and C I with electrons as colliders
  (2016MNRAS.460.2933M, 2018ApJ...861...72C, 2015MNRAS.447.3936M), comae with H2O and electron collisions
  (2019ApJ...870L..26C, 2025NatAs...9.1476C), diffuse absorbing gas where T_ex sits near T_CMB
  (2020ApJ...889L...4L, 2014ApJ...795...28B); absorption needs its own branch (step 2b).
- Turning an excitation solution into gas mass or alpha_CO: alpha_CO(1-0) 0.2 to 0.5 in the NGC 1614 ring,
  scaling as 3e-4/[CO]/[H2] (2017ApJ...835..174S), 0.4 in a lensed merger (2019MNRAS.486.2366M),
  alpha_CO(3-2) 0.3 to 0.7 in a CMZ (2026ApJ..1003..231W). These values carry the adopted CO abundance.
- Testing whether observed rotational temperatures are sub-thermal: run RADEX grids, fit a rotation diagram
  to the model fluxes and compare T_rot with T_kin (2025A&A...693A.101T).

## When not to use

| Situation | Use instead |
|---|---|
| Density far above the critical densities, so the lines are thermalized; RADEX itself shows no density dependence (thermalized above 1e8 cm-3 in 2019ApJ...880...69Y; LTE justified at n ~ 1e8 cm-3 in 2024ESC.....8..665M) | The `rotational-diagram-lte` skill (rotation diagrams, LTE synthetic spectra) |
| Many lines of a complex organic in a hot core, where you need T_rot and N_tot and not n(H2) | `rotational-diagram-lte`; use non-LTE only as a check on one species (2020MNRAS.498L..87B used LVG for CH3OH, then rotation diagrams for other iCOMs at T_rot = 100 K) |
| Resolved disk, envelope or circumstellar shell with strong T and n gradients, fit in the uv plane or channel by channel | The `radiative-transfer-modelling` skill (LIME, RATRAN, RADMC-3D forward models: 2017A&A...605A..21C, 2013Sci...341..630Q, 2015ApJ...813..128Q, 2016MNRAS.460.2933M) |
| Only one transition and no independent density or temperature | Label any LTE column as conditional on LTE (a T_ex range does not validate LTE) and give excitation-dependent bounds: one CO line left the mass uncertain over two orders of magnitude (2019AJ....157..117M); Fomalhaut CO mass limits were computed across collider densities, with the radiation-dominated case as the strict limit (2015MNRAS.447.3936M); brightness cannot be turned into density with one line (2017ApJ...842L..24A) |
| Abundance profiles or chemical ages | The `chemical-modelling` skill; RADEX only sets the excitation |
| Converting CO luminosity to mass with a fixed alpha_CO | The `gas-mass-co-conversion` skill |

## Steps

1. **Decide that non-LTE is needed.** Goal: know whether the lines can be sub-thermal. Method: compare the
   expected density with the lines' critical densities (general practice: n_crit = A_ul / sum of C_ul;
   optically thick lines thermalize at lower density). Papers quote them for the specific lines, e.g.
   1.0e3 to 1.7e4 cm-3 at 100 K for HCNH+ 2-1 to 5-4 (2025A&A...696A..31G); effective critical densities for
   dense-gas tracers (2017MNRAS.466...49J). A common sequence is LTE first, then RADEX on the same regions
   (2020A&A...644A..59K, through CASSIS).
2. **Measure intensities on matched data.** Goal: ratios that compare the same gas. Method: put every line
   on the same velocity resolution and beam, and measure in the same aperture (SO lines resampled to
   0.28 km/s, convolved to 0.96"x0.73", measured in a 0.75" box in 2014ApJ...796..131O); convert Jy/beam
   to K before RADEX (2018A&A...617A.120M). Integrated intensities (2025A&A...696A..31G) or peak ratios
   are both used; say which. Check missing flux per line (2017ApJ...835..174S notes flux lost on scales above
   4.6"; 2015ApJ...803...60S notes missing flux for some lines). Before reading a flux deficit as weak
   excitation, check continuum opacity, continuum oversubtraction and line absorption: continuum
   oversubtraction or blocking may reduce line flux (2025A&A...693A.101T); region fluxes were highly
   uncertain because of absorption (2015ApJ...801...63M). Typical software: CASA for imaging and extraction.
2b. **Absorption lines (branch).** Goal: columns and conditions from absorption against a continuum.
   Method: state the covering factor and the continuum the line of sight sees (f_c = 1 was assumed and listed
   as a limitation in 2020A&A...637A...7M); check whether lines compared were observed at the same time when
   the background source varies (non-simultaneous observations and variability in 2020A&A...637A...7M); set
   T_bg to the CMB at the absorber redshift (5.14 K at z = 0.89 in 2020A&A...637A...7M; T_rot = T_CMB for
   polar species in 2014A&A...566A.112M); expect one-sided results and report them as bounds (density an
   upper bound and column a lower bound in 2014ApJ...795...28B).
3. **Pick molecular data and colliders.** Goal: rate coefficients that cover your T_kin. Method: LAMDA
   files (2018A&A...617A.120M, 2014ApJ...785..149S, 2019PASJ...71...68K). H2 is the usual sole partner
   (2020A&A...644A..59K, 2020MNRAS.493.3744F, 2024A&A...686A..47M); electrons for debris disks and comae
   (2016MNRAS.460.2933M, 2020ApJ...898..146M, 2025NatAs...9.1476C). When rates are missing, papers borrow
   or scale them: HCO+ rates for N2H+ (2019ApJ...882..160Q, 2020A&A...644A.133H), N2H+ and HCN rates for
   N2D+ and DCN (2017A&A...606A.125S), SiS-H2 rates for AlCl (2021A&A...655A..80D), He rates scaled by
   1.385 or 1.4 to H2 (2020MNRAS.492.1180R), rates extrapolated as sqrt(T) above 140 K
   (2015ApJ...814..143A), CS 7-6 as proxy for C34S (2020ApJ...889...43Z). New rates were computed with
   MOLSCAT for HCNH+ (2025A&A...696A..31G). Write down which rates are borrowed.
4. **Fix the non-fitted inputs.** Goal: an explicit, defensible model setup. Method: the CMB part of T_bg
   is 2.73 K locally and 2.73(1+z) K at redshift (2019ApJ...873...50D; 10.9 K in 2021A&A...645A..45C; 5.14 K
   at z = 0.89 in 2020A&A...637A...7M). Then decide whether other radiation matters, which a single T_bg
   cannot represent: the Fomalhaut CO model includes CMB, stellar and dust radiation (2015MNRAS.447.3936M);
   the Orion Bar C2H model includes dust continuum excitation (2025A&A...696A.100G); AlCl was modelled with
   a 700 K blackbody IR field (2021A&A...655A..80D). For radiation-dominated gas (debris disks, comae) use a
   code that takes the frequency-dependent field (the `radiative-transfer-modelling` skill when needed).
   Line width from the measured spectra (2024A&A...689A..64B, 2019PASJ...71...68K used the average width per
   region). Geometry and ortho/para ratio: see the parameter table. For LVG codes, X/(dv/dr) is an
   object-specific choice: fit it or justify it (dv/dr fitted over 1e2-1e6 m/s/pc in 2019MNRAS.486.2366M;
   [CO]/[H2](dv/dr)^-1 1e-3 to 1e-7 in 2020ApJ...902..109B; abundance per velocity gradient 10^-11.33 to
   10^-7.67 km-1 s pc in 2015ApJ...801...63M); two galaxy studies adopted 1e-5 km-1 s pc as an assumption
   (2020A&A...641A.155V, 2024A&A...686A..47M).
5. **Run the grid or sampler.** Goal: a likelihood over T_kin, n(H2), N/dv (plus filling factor when lines
   are diluted). Method: a chi2 grid over RADEX models is the most frequent phrasing. My count of the pack's
   fitting-method aggregate (43 step-level entries, not deduplicated by paper): 19 describe a chi2 grid,
   7 name MCMC/emcee (from at most 5 papers, one of them an LTE cube fit in 2020ApJ...892...99C and one a
   hyperfine fit in 2026A&A...707A.120H), the rest are least squares, by-eye or unstated. This does not show
   what most of the 154 papers did. Spacing is mixed: often linear in T_kin and logarithmic in n and N.
   Grid examples: 40 log steps per axis, 64000 models (2020A&A...643A..89P); 0.1 dex steps in all axes
   (2019MNRAS.486.2366M); T_kin in 10 K steps with N_CO in 0.1 dex steps (2016ApJ...821..112K); T_kin in
   10 K steps with log n in 0.1 steps (2025A&A...693A.101T). MCMC examples: emcee with 20 walkers and 4500
   steps after burn-in (2025A&A...696A..31G); walkers = 4x free parameters, 2000 burn-in + 3000 steps
   (2026A&A...707A.120H); a pyradex grid interpolated inside emcee (2018ApJ...864..133T). Iteration counts
   are not convergence evidence: show mixing and enough effective samples (the cards flag convergence
   diagnostics as missing for 2025A&A...696A..31G and initial walker positions and convergence checks as
   missing for 2020ApJ...892...99C). State priors for grids too: 2020A&A...643A..89P reweighted the grid
   to get uniform priors on derived quantities; 2024ApJ...969..143I tried flat linear and flat log priors on
   the filling factor; 2018ApJ...864..133T reran with a linear instead of log prior on the Mach number. Test
   any prior that moves the answer. Add flux calibration error in quadrature (5% for CO 2-1 and 10% for
   other lines in 2019MNRAS.486.2366M; 15% in 2024A&A...689A..64B); 2014ApJ...785..149S added a 15%
   uncertainty to its line ratios without calling it calibration. A calibration error shared by lines from
   the same band or observation, and a line shared by two ratios, make the errors correlated (general
   practice): use a covariance or a shared scale parameter rather than independent terms. For resolved fits,
   model correlated noise: 2016MNRAS.460.2933M accounted for the number of independent beams and adjacent
   channel correlation; 2018ApJ...864..133T used Gaussian-process noise (celerite), noted that neighbouring
   annuli are correlated within a beam, and did not correct beam smear (affecting the inner 90-100 au).
   Include upper limits in the likelihood (an erf term in 2020A&A...643A..89P).
6. **Constrain the degeneracies.** Goal: exclude solutions you can argue are unphysical for this object,
   and state each restriction as a conditional modelling assumption. Method: priors tau < 100
   (2014ApJ...785..149S, 2019ApJ...873...50D, 2017A&A...604A...2S); a virial restriction K_vir >= 1
   (2019MNRAS.486.2366M; 2014ApJ...785..149S used a virialized K_vir prior but its card lists the cutoff as
   not stated); filling factor <= 1 (2024ApJ...969..143I, 2017A&A...604A...2S); fix n(H2) from
   another tracer to free T_kin (2026A&A...707A.120H) or fix density because of the T-n degeneracy
   (2018MNRAS.475..448T); fix T_kin where other species set it (40 K for SN 1987A minor species in
   2017MNRAS.469.3347M). If one phase does not fit, fix a cold phase from outer gas and fit a warm phase
   (2017ApJ...835..174S).
7. **Derive the science quantity.** Goal: abundance, mass or conversion factor. Method: X = N/N(H2) with a
   stated reference abundance (X_CO = 1e-4 in 2015A&A...581A..85P). Mass of the tracer molecule:
   M = f Omega N d^2 m (2017MNRAS.469.3347M), where Omega is the beam (or aperture) solid angle, f the
   filling factor of the emission within it, N the column of the emitting gas from the fit (source-averaged;
   if your N is already beam-averaged drop f, or dilution is counted twice), d the distance and m the mass of
   one molecule; this gives the SiO or CO mass, not the gas mass. For total gas, divide the tracer column by
   its abundance and multiply by the mass per H2 including helium, e.g. 1.4 m_H2 N(C17O)/X(C17O) times the
   beam area for the HH 212 disk (2015A&A...581A..85P); helium factors 1.36 (2025ApJ...991...53C) and 1.4
   (2015A&A...581A..85P) both appear, so say which. alpha_CO from the RADEX N(H2) and the CO luminosity
   (2017ApJ...835..174S): keep the abundance scaling (its 0.2-0.5 scales as 3e-4/[CO]/[H2]), state the CO
   transition and units, and propagate or bracket the abundance uncertainty (x_CO is the largest alpha_CO
   uncertainty in 2017ApJ...840....8S; [CO]/[H2] from 8e-6 to 6.5e-4 is adopted across the pack).
   Report marginalized 16th/84th percentiles (2025A&A...696A..31G) or chi2 confidence ranges
   (90% in 2017ApJ...835..174S).
8. **Validate.** See Verification checks.

## Parameter defaults and ranges

Counts are my own counts of distinct bibcodes in the pack's parameter and assumption lines; full grid
list in `references/parameters.md`.

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| T_kin grid | log or linear, from ~10 K (or T_CMB) to a few 100 K | mostly 3-400 K up to T_CMB-1000 K; 50-500 K for warm tracers; one grid to 6300 K (2018ApJ...868...95M) | 20+ with stated ranges | 2017ApJ...835..174S (10-300 K), 2020A&A...643A..89P (3-400 K), 2024A&A...686A..47M (T_CMB-1e3 K), 2025A&A...696A..31G (50-500 K) |
| n(H2) grid | 1e2 to 1e7 cm-3 | 10-1e6 (SLEDs) up to 1e5-1e12 (disks) | 20+ | 2017ApJ...835..174S, 2019PASJ...71...68K, 2014ApJ...785..149S, 2025A&A...693A.101T |
| N_CO/dv (CO grids) | 1e14-1e20 cm-2 (km/s)-1, log steps | 1e14-1e20; fixed 2.5e16 in 2020ApJ...898...61I | 6: 2014ApJ...785..149S, 2019ApJ...873...50D, 2020A&A...643A..89P, 2024A&A...686A..47M, 2020ApJ...898...75I, 2020ApJ...898...61I | see count column |
| N_CO (column, CO grids) | log steps | 1e12-1e22 cm-2; fixed 1e16 and 1e17 in 2020MNRAS.493.3744F | 4: 2016ApJ...821..112K, 2017A&A...608A..38O, 2018ApJ...868...95M, 2020MNRAS.493.3744F | see count column |
| N/dv (dense-gas tracers) | fixed | 1e14 cm-2 (km/s)-1 for HCN, HCO+, HNC | 1 | 2021A&A...645A..45C |
| T_bg | CMB: 2.73 K, or 2.73(1+z) K at redshift | CMB 2.7-2.73 K locally to 10.9-11 K at z ~ 3; non-CMB backgrounds 10 or 100 K (2017ApJ...837...60B); extra stellar, dust or IR fields in 2015MNRAS.447.3936M, 2025A&A...696A.100G, 2021A&A...655A..80D | 25 mention background or CMB (my count of distinct bibcodes in parameter and assumption lines) | 2019ApJ...873...50D, 2021A&A...645A..45C, 2020A&A...637A...7M |
| Geometry | expanding sphere (LVG) or uniform sphere | also slab, static sphere | 18 spherical, 3 slab | 2017ApJ...835..174S, 2015ApJ...803...60S, 2018ApJ...864..133T, 2024A&A...689A..64B |
| H2 ortho/para (collider) | 3 | thermal/LTE OPR (2020A&A...643A..89P, 2018ApJ...864..133T); 0.25 (2025A&A...696A..31G); lower limit 1e-3 (2018A&A...617A.120M) | 11 stated for H2: 7 at 3, 2 thermal, 1 at 0.25, 1 lower limit (my count; ambiguous whether H2 or molecule in 2017A&A...605A..21C, 2019ApJ...875...96N, 2017A&A...602A..42K, not counted) | at 3: 2024A&A...686A..47M, 2020A&A...644A..59K, 2024A&A...689A..64B, 2020A&A...637A...7M, 2021A&A...655A..80D, 2020A&A...633A..13D, 2020A&A...641A.155V |
| Molecular ortho/para (emitter) | 3 | | 4 | H2CO and CH2CO (2026A&A...707A.120H), c-C3H2 (2018A&A...617A.120M), H2O (2013ApJ...770..142N), H2CO (2013ApJ...777...85N); para-H2CO lines only, so none needed (2024ApJ...969..143I) |
| A/E or E/A ratio | 1 | | 3 | CH3OH (2020MNRAS.498L..87B, 2026A&A...707A.120H), CH3CN (2015ApJ...814..143A) |
| [CO]/[H2] | 1e-4 | 8e-6 to 6.5e-4 | about 13 at 1e-4 | 2015A&A...581A..85P, 2020ApJ...898...75I; 3e-4 in 2017ApJ...835..174S; 6e-5 in 2019PASJ...71...68K |
| Line width | measured average per region | 0.14 km/s (disks) to 850 km/s (QSO host) | many | 2024A&A...689A..64B, 2018A&A...617A..28S, 2020MNRAS.493.3744F |
| Filling factor | 1, or free and <= 1 | 1e-5 to 1 | 9 mention filling or dilution | 2020A&A...644A..59K, 2024ApJ...969..143I, 2018ApJ...868...95M |
| Calibration error | 10-15% added in quadrature | 5-15% | 4 identified as calibration: 2019MNRAS.486.2366M (5%, 10%), 2024A&A...689A..64B (15%), 2013ApJ...770..142N (10%), 2016ApJ...831..101B (15%) | other added terms not called calibration: 15% on ratios (2014ApJ...785..149S), 20% ratio error (2019ApJ...872..200H) |
| Optical depth prior | tau < 100 | 0-100 | 4 | 2014ApJ...785..149S, 2019ApJ...873...50D, 2017A&A...604A...2S, 2017ApJ...840....8S |
| MCMC | emcee, 16/50/84 percentiles | 8-256 walkers (8 = 4x two free parameters for CH3CN in 2026A&A...707A.120H; 200 in the LTE cube fit of 2020ApJ...892...99C) | 4 with stated settings (one an LTE cube fit) | 2025A&A...696A..31G, 2026A&A...707A.120H, 2018ApJ...864..133T, 2020ApJ...892...99C |

## Software

Counts are the pack's aggregate of matched analysis steps naming each code (not distinct papers); I dropped
entries from clearly off-topic papers (KINICH-PAKAL for a stellar chromosphere, cprops and clumpfind).

| Code | Steps naming it | Used for |
|---|---|---|
| RADEX | 87 (plus pythonradex 3, SpectralRadex 3, pyradex 2, myRadex 1) | single-zone escape probability grids; the default (2017ApJ...835..174S, 2025A&A...696A..31G). pythonradex for electron-excited C I/C II in debris disks (2018ApJ...861...72C); SpectralRadex with emcee (2026A&A...707A.120H); pyradex grids interpolated in emcee (2018ApJ...864..133T); myRadex for an LVG SLED (2019MNRAS.486.2366M) |
| LIME | 15 | 3D non-LTE line transfer: full radiative transfer differing by at most a factor 1.2 from the simpler models in 2018ApJ...861...72C; an LTE/non-LTE check of an LTE cube model (LTE flux 1.3x the LIME non-LTE flux) in 2020ApJ...892...99C, which is not a RADEX comparison; comae (2019ApJ...870L..26C) |
| RATRAN | 10 | 1D/2D disk and envelope models fit on visibilities (2013Sci...341..630Q, 2015ApJ...813..128Q) |
| emcee | 7 (corner 1) | posterior sampling over RADEX grids |
| CASA | 9 | imaging and spectrum extraction before modelling |
| CASSIS | 3 | chi2 grids wrapping LTE and RADEX models (2020A&A...644A..59K) |
| LAMDA | 3 named, more implied | molecular data files (2014ApJ...785..149S, 2019PASJ...71...68K) |
| RADMC-3D / RADMC | 3 / 2 | non-LTE disk models with electron colliders (2016MNRAS.460.2933M) |
| Other LVG codes | MADEX 2, MOLLIE 2, ALI 2, GRELVG 1, Ceccarelli LVG 1 | e.g. CH3OH LVG grid (2020MNRAS.498L..87B) |
| Others | SHAPE/shapemol 3/2, TORUS 1, mcp 1, SUBLIMED 1, MOLSCAT 1, PDR Toolbox 1 | morpho-kinematic shells, 3D tests (2019MNRAS.485.2457H), AGB shells (2018A&A...612L..11S), comets (2025ApJ...986L..22R), new rates (2025A&A...696A..31G), PDR follow-up (2017ApJ...835..174S) |

## Pitfalls

- **T-n degeneracy.** Few lines leave T_kin and n(H2) correlated; authors call the parameters "poorly
  constrained and correlated" (2019MNRAS.486.2366M), "highly degenerate" (2020A&A...641A.155V,
  2024ApJ...972..147C), or report only trends. With four CO lines only a few parameters can be constrained
  (2017ApJ...835..174S). HCNH+ gave densities but weak temperatures (2025A&A...696A..31G), and CS results
  stayed poorly constrained with the source size fixed (2024A&A...689A..64B).
- **Optically thick lines.** Thick SO gave T_kin but no density or abundance (2014ApJ...796..131O); thick
  HCN gives lower-limit abundances (2019A&A...632A.101T).
- **Single component for multi-phase gas.** No single model fit the stacked SPT spectrum (min chi2 = 10.4
  for 3 dof, 2014ApJ...785..149S); single-component LVG was inadequate for ULIRGs (2024A&A...686A..47M);
  RADEX assumes one homogeneous medium (2020ApJ...898...75I).
- **SLED without its peak.** If the CO SLED peak is not observed the LVG solution is not constrained
  (2019A&A...628A..23A).
- **Borrowed or truncated rates.** HDO rates stop at 450 K, so the highest lines could not be modelled
  (2013ApJ...770..142N); N2H+ with HCO+ rates gives a factor 3-5 density uncertainty
  (2020A&A...644A.133H); rate uncertainties up to 50% were left out of the errors (2019ApJ...871..170M);
  collision rates unknown for SN 1987A CO (2013ApJ...773L..34K).
- **Neglected colliders and pumping.** No electron or H collisions (2020A&A...644A..59K); infrared pumping
  only partly included (2015ApJ...814..143A); vibrational pumping excluded (2013ApJ...770..142N).
- **Beam dilution set to 1.** Common for simplicity (2025A&A...696A..31G, 2020A&A...644A..59K), but
  unresolved emission makes columns too low (2025A&A...693A.101T).
- **Errors too small.** Formal errors exclude systematics from fixed parameters (2026A&A...707A.120H),
  calibration (2020ApJ...892...99C) and model choice (2020A&A...644A..59K, 2021A&A...655A..80D).
- **Lensing.** Differential magnification biases SLED ratios; model apparent and intrinsic ratios
  separately (2019ApJ...873...50D; not accounted in 2014ApJ...785..149S).
- **What the cards rarely state.** Grid ranges and steps, RADEX background and line width, and the
  likelihood form are often missing (cards for 2015A&A...581A..85P, 2024ApJ...969..143I,
  2020MNRAS.493.3744F, 2025A&A...693A.101T). The pack's not-stated aggregate is dominated by imaging
  settings: CASA version (19), line-free channels for continuum subtraction (13 plus variants), flux scale
  uncertainty (7). State all of these.

## Verification checks

What papers did:

- Reconstruct the best-fit SLED or ratios and overplot the data (2017ApJ...835..174S,
  2020A&A...643A..89P, which flags the one line it misses).
- Compare predicted with observed fluxes line by line: the predicted [CI] flux of the CO+[CI] SLED model
  against the observed value (2019MNRAS.486.2366M; [CI] was part of the modelled SLED, so this is not a
  held-out test). A true held-out line is stronger (my recommendation).
- Compare with LTE: RADEX columns 2-4x the LTE thin value (2015A&A...581A..85P); LTE within ~20%
  (2024ApJ...969..143I); in an LTE cube fit, LTE flux 1.3x the LIME non-LTE flux (2020ApJ...892...99C).
- Check sensitivity to fixed inputs: line width 3.0 or 4.0 km/s (2020MNRAS.498L..87B); T_kin 10-300 K
  changing T_ex and N by < 1% (2020ApJ...889L...4L); T_R within 10% over 1e6-1e12 cm-3 and 100-500 K
  (2018A&A...612L..11S); source size +-50% (2018ApJ...861...72C); collision rates x2 changing intensities
  by a few percent (2019ApJ...870L..26C); alternative abundances (2019PASJ...71...68K).
- Recover known inputs from mock data (22 mock SLEDs in 2014ApJ...785..149S).
- Use different marginalizations of the same grid and see whether T_kin agrees (2024ApJ...969..143I).
- Confirm the fitted lines are optically thin where you assume so (RADEX tau <~ 1 in 2020ApJ...889...43Z;
  in 2020MNRAS.498L..87B, predicted opacities 0.3-0.5 for methyl formate and ~0.2 for ethanol in the
  rotational-diagram stage, not for the methanol lines of the LVG fit).
- Cross-check with independent data or tracers: APEX ratio (2018A&A...617A.120M), earlier CH3CN
  temperatures (2026A&A...707A.120H), IR-based G0 (2017ApJ...835..174S).

What a careful referee adds:

- Show the full 2D posterior or chi2 surface in T_kin versus n(H2), not only a best fit.
- Confirm that the best fit is not on a grid edge and that the rate files cover the fitted T_kin.
- Confirm the line ratios use matched beams and the same recovered scales, and that continuum opacity,
  continuum subtraction and absorption cannot explain a flux deficit.
- Propagate calibration error (with its correlations) and the borrowed-rate uncertainty into the quoted
  intervals.
- For MCMC, ask for convergence evidence (mixing, effective sample size, stability across runs), not just
  walker and step counts.
- Check that free parameters do not outnumber independent observables; report unidentifiable quantities as
  bounds.

## Source cards

Full list in `references/sources.md` (154 papers). Most informative for this technique:

- 2017ApJ...835..174S (single- and two-phase RADEX on a resolved CO SLED, PDR follow-up)
- 2020A&A...643A..89P (64000-model RADEX grid, Bayesian with upper limits)
- 2025A&A...696A..31G (new rates with MOLSCAT, RADEX + emcee)
- 2026A&A...707A.120H (density fixed from C17O, CH3CN T_kin with SpectralRadex + emcee)
- 2024ApJ...969..143I (para-H2CO thermometer, filling factor <= 1)
- 2014ApJ...785..149S (tau and K_vir priors, mock recovery test)
- 2019ApJ...873...50D (CMB at redshift, lensing-corrected ratios)
- 2019MNRAS.486.2366M (myRadex LVG, calibration error, K_vir >= 1, [CI] flux comparison)
- 2018ApJ...864..133T (pyradex grid in emcee, resolved disk annuli)
- 2025A&A...693A.101T (sub-thermal excitation test)
- 2015A&A...581A..85P (non-LTE versus LTE columns)
- 2014ApJ...796..131O (matched resolution, chi2 < 10 acceptance)
- 2018ApJ...861...72C (electron-excited C I with pythonradex, LIME check)
- 2016MNRAS.460.2933M (electron density from radiation-dominated to LTE)
- 2019ApJ...870L..26C (cometary non-LTE with LIME, rate sensitivity)
- 2017MNRAS.469.3347M (SiO and CO masses from RADEX ratio contours)
- 2019PASJ...71...68K (10-ratio RADEX grid for dense-gas tracers)
- 2020A&A...644A..59K (CASSIS LTE then RADEX, admitted systematics)
- 2021A&A...645A..45C (z ~ 3 dense-gas LVG, degeneracies)
- 2018A&A...617A.120M (DCO+ ratios, ALMA versus APEX)

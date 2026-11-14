# Review task: an ALMA agent skill against its evidence pack

You are reviewing a skill file (SKILL.md, plus an optional parameters table) that another model wrote from the
EVIDENCE PACK below. The pack is built from methods cards of published ALMA papers; every quote in it was
mechanically verified against the paper text. The skill will be given to research agents that analyse ALMA data,
so wrong defaults or misattributed practice cause real errors. You have no file access: everything you need is in
this message.

Check, in this order:

1. **Attribution.** Every number, range, default, software attribution and "papers do X" claim that cites
   bibcodes: does the pack support it for those bibcodes? Flag claims the pack contradicts, claims cited to a paper
   whose pack entry says something else, and counts that do not match the pack aggregates.
2. **Unsupported practice.** Statements presented as literature practice with no support in the pack. (General
   background marked as general practice is fine if it is correct.)
3. **Scientific correctness.** Wrong formulas, wrong units, wrong CASA task/parameter names or semantics, unsafe
   advice, or a recommendation that contradicts the evidence.
4. **Omissions.** Important pitfalls, assumptions or validation checks that are clearly present in the pack (for
   example in "Limitations the authors admit" or "Settings cards flag as needed but not stated") but missing from
   the skill.
5. **Usability.** Anything an agent would misread or could not act on.

Output format (Markdown, nothing else):

```
# Codex review: <slug>
VERDICT: CLEAN | FIX
## Findings
- SR-01 | high|medium|low | <attribution|unsupported|science|omission|usability> | <the claim, quoted briefly> | <problem, citing the pack line or bibcode> | <concrete fix>
- SR-02 | ...
## Notes
<at most 5 lines: overall quality, anything the writer should know>
```

Use `VERDICT: CLEAN` only when there are no high or medium findings. Be specific and terse; do not restate the
skill. Do not invent pack content: when you say the pack contradicts a claim, cite the pack line.

=== SKILL.md (absorption-lines) ===
---
name: alma-absorption-lines
description: "Measure molecular absorption lines against bright continuum sources (quasars, AGN cores, lensed starbursts, Galactic background sources, protostellar or stellar continua) in ALMA data: extract and normalize spectra, derive optical depth and covering factor, fit velocity components, convert to column densities and abundances, and run blind absorber searches. Use when a task involves tau = -ln(S/S_cont), absorption against a continuum, covering factors, intervening or associated molecular absorbers, or checking whether an absorption feature is real. Built from 18 ALMA papers (2014-2025); evidence is thin, see the warnings inside."
---

# Molecular absorption against continuum sources

Absorption spectroscopy measures the line-of-sight optical depth of foreground gas against a compact continuum
background: tau(v) = -ln(S_obs(v)/S_cont). Its strength is sensitivity to cold, low-density gas that emission misses;
its weakness is that every derived column depends on the covering factor, excitation temperature and saturation.
The two mistakes that matter most: (1) assuming covering factor 1 and an optically thin line, then reporting columns
as measurements when they are lower limits; (2) trusting a weak feature that is really a bandpass or telluric
artifact (the M87 CO(2-1) re-examination, 2025ApJ...990...66K, exists because of this).

> **Evidence warning.** The pack has 18 papers. By my count of the pack lines, 2 are off-topic (2020ApJS..247...61F
> is rest-UV absorption-line redshifts for ALPINE; 2025ApJ...984L..15P is exoALMA CO channel maps), and 3 more use
> optical/UV or 21 cm absorption with ALMA only for emission or limits (2016ApJ...820L..39N, 2018ApJ...856L..12N,
> 2018A&A...620A.119D). That leaves about 13-14 papers doing ALMA mm/submm absorption. Most aggregate counts below are
> 1. Treat the defaults as "what one or two papers did", not as community consensus.

## When to use

- A bright compact continuum source sits behind (or inside) molecular gas: blazar/quasar sightlines through the Milky
  Way (2018A&A...617A..54L, 2017A&A...600A..48G, 2019A&A...622A..26G), radio-loud AGN cores in their own hosts
  (2019MNRAS.485..229R, 2020MNRAS.496..364R, 2025ApJ...990...66K), intervening lensing galaxies
  (2014A&A...566L...6M), lensed high-z starbursts (2017Natur.548..430F, 2020ApJ...905...85S), Galactic Center
  hot cores (2017A&A...605L...6T), protostellar dust cores (2019ApJ...872..196S) or evolved-star clumps
  (2019A&A...627A.114K).
- You need column densities or abundance ratios of species hard to see in emission (CH+, H2Cl+, CF+, HOC+, COMs in
  diffuse gas).
- You want a blind census of intervening absorbers across many calibrator spectra (2019MNRAS.490.1220K, ALMACAL).
- You need to decide whether a reported absorption feature is real (2025ApJ...990...66K).

## When not to use

| Situation | Use instead |
|---|---|
| Gas seen only in emission, no compact background continuum | moment maps, rotational-diagram or non-LTE emission analysis |
| Rest-UV/optical interstellar absorption (Lya, metal lines) | optical Voigt fitting (e.g. FITLYMAN/MIDAS in 2018A&A...620A.119D, linetools MCMC in 2018ApJ...856L..12N); not an ALMA technique |
| Continuum is extended and gas fills the beam unevenly, and you need masses | resolved emission plus a CO-to-H2 conversion; absorption gives only pencil-beam columns |
| Many lines, full excitation analysis needed | rotational diagram / LTE or non-LTE modelling skills, with absorption as one input |
| Kinematic substructure in disks | channel-map kinematics (2025ApJ...984L..15P is in this pack only by regex) |

## Steps

### 1. Choose the background and check the data first
- Goal: a continuum bright enough that the line rms in tau units is useful. Published backgrounds include a
  0.59 Jy blazar (2017A&A...600A..48G) and a 1.66 Jy AGN core (2025ApJ...990...66K).
- Blind searches use ALMA calibrator data (2019MNRAS.490.1220K); the card does not list the project/EB set, so
  record your own.
- Before any science, inspect the bandpass calibrator spectrum and atmospheric transmission at the line frequency.
  2025ApJ...990...66K re-examined whether the M87 CO(2-1) absorption was an artifact of bandpass calibration and
  telluric contamination; its second epoch gave only tau_21 <~ 0.019 against tau_21 ~ 0.05 in the first.

### 2. Extract the spectrum at the continuum source
Papers use one of four extractions:

| Extraction | Papers |
|---|---|
| Pixel of peak continuum flux in pipeline cubes | 2018A&A...617A..54L, 2017A&A...600A..48G |
| Region the size of the synthesized beam FWHM, centred on the source, channel maps at full resolution | 2020MNRAS.496..364R |
| Peak pixel or weighted average of bright pixels, smoothed to 1 km/s | 2019A&A...622A..26G |
| Fixed central region (0.77 x 0.59 arcsec) in CARTA | 2025ApJ...990...66K |
| Visibility fit of point sources with fixed relative positions, free fluxes per channel (lensed images) | 2014A&A...566L...6M (uvmultifit) |

- For extended or multiple-image backgrounds, fit in the uv plane (2014A&A...566L...6M) rather than reading one
  pixel, so each image gets its own spectrum.
- For sources off the phase centre, correct for primary beam attenuation (2017A&A...605L...6T).
- Recommendation: use peak pixel for an unresolved point source, a beam-sized region when S/N matters, uv-plane
  fitting when the background is lensed or blended.

### 3. Normalize by the continuum
- Divide the spectrum by the continuum in the same spectral window (2018A&A...617A..54L, 2019A&A...622A..26G).
- Or take the continuum level from the line fit itself (Gaussian fit returns continuum, line-centre flux, centre
  velocity and width; 2025ApJ...990...66K).
- Do not continuum-subtract the cube before you have measured S_cont; tau needs the absolute continuum level.
- If continuum is taken from line-contaminated channels, the noise is underestimated (2019A&A...627A.114K).
- The cards rarely state the line-free channels or how the continuum level was fitted; record yours.

### 4. Separate emission from absorption (when both are present)
- Fit emission and absorption Gaussians simultaneously (2017Natur.548..430F).
- Or fit and subtract the emission line while masking absorption channels, then fit the absorption
  (2019MNRAS.485..229R). That paper scanned the mask limits (about -55 +/- 10 to +5 +/- 10 km/s) and kept the range
  whose unmasked residual gave the lowest reduced chi2 against a flat line.
- With limited bandwidth, redshifted P Cygni emission may fall outside the band and cap the measured outflow
  velocity (2020ApJ...905...85S).

### 5. Compute optical depth and fit components
- tau(v) = ln(S_cont / S_obs(v)) (2025ApJ...990...66K, 2019MNRAS.485..229R). This equals the true tau only for
  covering factor 1 and negligible excitation temperature relative to the background brightness (general practice).
- Fit Gaussian components in velocity: triple Gaussian for Hydra-A CO(2-1) (2019MNRAS.485..229R), giving a peak
  tau of 0.88 and FWHM 4.4 km/s for its region A; simultaneous Gaussians with peak tau 0.25-1.2 for CH+ in lensed
  SMGs (2017Natur.548..430F).
- Uncertainties: Monte Carlo with 100000 simulated spectra (2019MNRAS.485..229R), bootstrap to capture parameter
  correlations (2017Natur.548..430F). The cards do not give the bootstrap implementation.
- Hyperfine structure (HCN, H2Cl+) must be modelled with its relative weights; the cards for 2018A&A...617A..54L,
  2017A&A...600A..48G and 2014A&A...566L...6M flag this treatment as not stated.

### 6. Constrain the covering factor
- f_c < 1 means the observed depth underestimates tau. Papers handle it three ways:
  - assume f_c = 1 and call tau a lower limit (2019MNRAS.485..229R; 2020MNRAS.496..364R notes covering factors give
    lower limits on tau);
  - assume a uniform screen over a background of known size r_SMG (2017Natur.548..430F);
  - constrain f_c per lensed image from the data: 0.3 < f_c < 1.0 toward the PKS 1830-211 NE image
    (2014A&A...566L...6M).
- A saturated line with a flat bottom above zero flux is the usual evidence that f_c < 1 (general practice).

### 7. Convert tau to column density
- Linear-regime formula for a single line, e.g. N(CH+) = 3e12 cm^-2 * tau_0 * (dv_abs / 1 km/s)
  (2017Natur.548..430F). Assumes optically thin, ground-state population; the authors say N(CH+) may be a lower
  limit because of saturation and coarse velocity resolution.
- LTE with one excitation temperature for all species, modelled with CASSIS: best Tex = 52 K (3 sigma 37-67 K) for
  VY CMa clump C (2019A&A...627A.114K).
- Rotation diagram in LTE with optically thin foreground layer against the continuum; Trot fixed at 200 K where no
  diagram fit was possible (2019ApJ...872..196S). Those authors treat Trot as upper limits and columns as lower
  limits because low-Eu lines may be optically thick; e.g. N(CH3OH) >= 1.14e17 cm^-2 in IRAS 4A1.
- Excitation temperatures from optically thin LTE can be contradicted by the data (2020MNRAS.496..364R); treat them
  as approximations.
- Record the partition functions, Einstein A values and database; several cards flag these as not stated
  (2019MNRAS.485..229R, 2020MNRAS.496..364R).

### 8. Convert to H2 and abundances
- Ratios to H2 tracers: HCO+, HOC+, CF+ against CH, HF and other H2 proxies (2019A&A...622A..26G); HCO+ absorption
  as dark-gas tracer where CO emission is absent (2018A&A...617A..54L, 2017A&A...600A..48G).
- N(CO)/N(H2) is not constant over a large range of H2 columns (2019MNRAS.490.1220K).
- H2 can be underestimated (clumpy gas, coarse HF resolution), which inflates abundances (2017A&A...605L...6T).
- In the Galactic center, absolute abundances could not be set because H2-tracer abundances are not established
  there (2019A&A...622A..26G).
- Masses from absorption carry order-of-magnitude uncertainty from X-factor and F_ul (2019MNRAS.485..229R).

### 9. Blind searches for intervening absorbers
- 2019MNRAS.490.1220K: smooth each spectrum with kernels from 10 to 190 km/s in 10 km/s steps; flag candidates at
  5 sigma in two consecutive channels; reject edge channels, Galactic lines, artifacts, atmospheric lines and
  implausible redshifts; identify with Splatalogue.
- Lensing magnification bias of background quasars remains a systematic for absorber statistics (2019MNRAS.490.1220K).

### 10. Spatially resolved absorption in lensed sources
- 2020ApJ...905...85S: fit the lens on continuum visibilities (SIE plus shear and multipoles, pixellated source with
  gradient regularization, MCMC; ripples and visilens), then apply the lens to OH 119 um absorption velocity ranges.
  Visibilities were time-averaged unless a binned visibility would span more than 10 m in uv. Regularization
  strength maximized the Bayesian evidence, iterated with the MCMC.

## Parameter defaults and ranges

Counts are my count of pack lines, not a pack aggregate (the pack's "key parameters" list has one entry per paper).

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Spectrum extraction | peak continuum pixel | peak pixel, beam-sized region, fixed box, uv point-source fit | 6 | 2018A&A...617A..54L, 2017A&A...600A..48G, 2020MNRAS.496..364R, 2014A&A...566L...6M |
| Continuum normalization | divide by continuum in same SPW | same-SPW continuum, continuum from line fit | 3 | 2019A&A...622A..26G, 2025ApJ...990...66K |
| Spectral smoothing | 1 km/s | 1 km/s; 10-190 km/s kernels for blind search | 2 | 2019A&A...622A..26G, 2019MNRAS.490.1220K |
| tau definition | ln(S_cont/S_obs) | same | 2 | 2025ApJ...990...66K, 2019MNRAS.485..229R |
| Covering factor | 1 (lower limit on tau) | 1, uniform screen, 0.3-1.0 constrained | 4 | 2019MNRAS.485..229R, 2017Natur.548..430F, 2014A&A...566L...6M |
| Line profile | Gaussian components | 1-3 Gaussians per line; simultaneous emission+absorption | 3 | 2019MNRAS.485..229R, 2017Natur.548..430F, 2025ApJ...990...66K |
| Fit uncertainties | Monte Carlo or bootstrap | 1e5 simulated spectra; bootstrap | 2 | 2019MNRAS.485..229R, 2017Natur.548..430F |
| Excitation | LTE, single Tex | Tex = 52 K (37-67 K); Trot fixed 200 K if unconstrained | 2 | 2019A&A...627A.114K, 2019ApJ...872..196S |
| Detection threshold (blind) | 5 sigma in 2 consecutive channels | single setting | 1 | 2019MNRAS.490.1220K |
| Emission mask (emission+absorption) | scanned, lowest reduced chi2 | -55 +/- 10 to +5 +/- 10 km/s | 1 | 2019MNRAS.485..229R |
| Measured peak tau | none | 0.019 (limit) to 1.2 | 3 | 2025ApJ...990...66K, 2019MNRAS.485..229R, 2017Natur.548..430F |

## Software

From the pack aggregate "software named in the matched steps" (each is 1-3 papers; no tool dominates):

| Software | Pack count | Used for |
|---|---|---|
| CASA | 3 (one is off-topic 2025ApJ...984L..15P) | imaging and spectral extraction (2020MNRAS.496..364R, 2019A&A...622A..26G) |
| ALMA pipeline | 1 | cubes used directly for peak-pixel spectra (2017A&A...600A..48G) |
| GILDAS | 1 | spectrum handling alongside CASA (2019A&A...622A..26G) |
| CARTA | 1 | region extraction and Gaussian fit (2025ApJ...990...66K) |
| uvmultifit | 1 | per-image spectra by uv-plane point-source fits (2014A&A...566L...6M) |
| CASSIS | 1 | LTE absorption modelling (2019A&A...627A.114K) |
| Splatalogue | 1 | line identification in blind search (2019MNRAS.490.1220K) |
| ripples, visilens | 1 | lens modelling of absorbing source (2020ApJ...905...85S) |
| FITLYMAN/MIDAS, linetools, AIPS | 1 each | optical Voigt fits and GMRT 21 cm, not ALMA absorption (2018A&A...620A.119D, 2018ApJ...856L..12N) |
| SpecPro | 1 | off-topic (2020ApJS..247...61F) |

The cards rarely name the fitting code for Gaussian absorption components or the tau-to-N calculation; Weeds
(GILDAS) fitting is mentioned for 2017A&A...605L...6T only as a not-stated item.

## Pitfalls

- **Covering factor and saturation turn columns into limits.** f_c = 1 gives lower limits on tau
  (2019MNRAS.485..229R, 2020MNRAS.496..364R); saturation and coarse velocity resolution make N(CH+) lower limits
  (2017Natur.548..430F); optically thick low-Eu lines make Trot upper limits and N lower limits (2019ApJ...872..196S).
  Report limits as limits.
- **Covering factor of a lensed image is poorly known** (0.3 < f_c < 1.0, 2014A&A...566L...6M); non-detection in
  the weaker image gives only a limit on an isotopic ratio.
- **Spurious absorption.** Bandpass calibration and telluric features can mimic absorption, and the continuum level
  changed by about 45% between epochs in 2025ApJ...990...66K, possibly from flux-scale errors.
- **Underestimated noise** when continuum is measured from line-rich channels (2019A&A...627A.114K).
- **LTE single-Tex assumption** can be contradicted by the data (2020MNRAS.496..364R); results of absorption LTE
  models are not unique when the model has many free parameters (2019A&A...627A.114K).
- **H2 reference columns** are uncertain: N(CO)/N(H2) varies (2019MNRAS.490.1220K), H2 may be underestimated
  (2017A&A...605L...6T), and H2 tracers are uncalibrated in the CMZ (2019A&A...622A..26G).
- **Location along the sightline** is ambiguous for Galactic gas at velocities where the velocity field is not
  known (2017A&A...600A..48G); velocities are only line-of-sight motions (2019MNRAS.485..229R).
- **Bandwidth limits** hide redshifted P Cygni emission and cap vmax; S/N-dependent outflow classification can
  miss weak outflows (2020ApJ...905...85S).
- **Settings papers omit**, from the pack's not-stated aggregate: self-calibration solution intervals (3 cards),
  flux scale uncertainty (3), line-free channels and continuum subtraction (2 plus several variants), image and cell
  size (2), integration velocity ranges for tau integrals (1), how tau was computed including saturation and noise
  (1), HCN hyperfine treatment (1), partition function and Aul values (1). State all of these in your own work.

## Verification checks

What papers did (each is a single paper in the pack):
- Re-ran the analysis on a second epoch and compared continuum level and tau (2025ApJ...990...66K); looked for
  absorption variability over two years (2020MNRAS.496..364R).
- Chose the emission/absorption mask by minimizing reduced chi2 of the residual baseline (2019MNRAS.485..229R).
- Lens models: deviance information criterion, negative-bowl check at >= 10% of peak, mock point sources across
  the source plane recovered to about 25% (2020ApJ...905...85S).
- Blind search: rejected edge, Galactic, artifact and atmospheric candidates before accepting absorbers
  (2019MNRAS.490.1220K).
- Compared absorber kinematics with the host disk rotation curve to place the gas (2016ApJ...820L..39N).

What a careful referee adds (general practice, not shown in the pack):
- Overlay the bandpass calibrator spectrum and the atmospheric transmission model at the line frequency.
- Show that the absorption sits at the continuum peak and scales with continuum brightness, not with position.
- Check that the line bottom is above zero flux (saturation plus f_c < 1) and quote tau as a limit if not resolved.
- Compare at least two lines of the same species or isotopologues to test saturation.
- State Tex, partition function source, f_c and the velocity integration range used for every column density.

## Source cards

Full list: `references/sources.md`. Most informative for this technique:

- 2019MNRAS.485..229R (emission removal, triple-Gaussian, Monte Carlo errors, f_c = 1)
- 2025ApJ...990...66K (tau definition, artifact test across epochs)
- 2017Natur.548..430F (simultaneous fit, N(CH+) formula, bootstrap)
- 2014A&A...566L...6M (uv-plane per-image spectra, covering factor)
- 2019MNRAS.490.1220K (blind absorber search)
- 2020MNRAS.496..364R (multi-line survey, beam-sized extraction, variability)
- 2019A&A...622A..26G (continuum division, 1 km/s smoothing, H2 tracers)
- 2018A&A...617A..54L (peak-pixel extraction, dark gas)
- 2017A&A...600A..48G (peak-pixel extraction, bulge sightline)
- 2019ApJ...872..196S (rotation diagram for absorbing COMs, limits)
- 2019A&A...627A.114K (CASSIS LTE absorption model)
- 2017A&A...605L...6T (COMs in diffuse clouds, primary-beam correction)
- 2020ApJ...905...85S (lensed OH absorption, lens modelling tests)
- 2016ApJ...820L..39N (absorber-host comparison)

=== EVIDENCE PACK (absorption-lines) ===
# Evidence pack: Molecular absorption against continuum sources (`absorption-lines`)

Scope: absorption spectroscopy, column densities from optical depth, covering factors

Built from 18 non-held-out ALMA papers whose methods cards passed mechanical evidence verification (every quote below is verbatim from the paper). Years 2014-2025.
Matcher (regex over analysis steps): `absorption (?:line|spectr|feature|compon)|optical depth (?:of|in) (?:the )?absorption|against (?:the )?(?:bright )?(?:continuum|quasar|blazar)`
Tagging is by regex, so a few papers may be off-topic: ignore those.

## Aggregates over all papers

### Science fields
- astrochemistry: 9
- high_z_galaxies: 6
- milky_way_ism: 5
- agn_and_quasars: 5
- nearby_galaxies: 5
- galaxy_clusters_and_sz: 1
- evolved_stars: 1
- star_formation: 1
- transients: 1
- protoplanetary_disks: 1
- exoplanets: 1
- other: 1

### Software named in the matched steps
- casa: 3
- specpro: 1
- cassis: 1
- carta: 1
- fitlyman/midas: 1
- uvmultifit: 1
- linetools: 1
- aips: 1
- gildas: 1
- visilens: 1
- ripples: 1
- splatalogue: 1
- alma pipeline: 1

### Fitting methods (most common phrasings)
- Gaussian fits; bootstrap uncertainties: 1
- chi2 minimization to template; chi2(z) converted to p(z) and combined: 1
- Monte Carlo with 100000 simulated spectra: 1
- Best agreement found at Tex = 52 K (3 sigma 37–67 K): 1
- Gaussian fit (details not stated): 1
- MCMC Voigt profile fitting; priors not stated: 1
- MCMC for lens potential; iterative regularization/MCMC; priors not stated: 1

### Validation checks used
- Duplicate Keck/DEIMOS and VUDS spectra compared; redshifts agree within 280 km/s for most: 1
- [O II] from MOSFIRE for one galaxy agrees with [C II] redshift: 1
- Agreement with Heintz et al. 2018: 1
- Compared CLEAN, continuum-subtracted and regularized maximum likelihood images: 1
- Metallicity consistent with previous measurement: 1
- Deviance information criterion, negative-bowl check (>=10% of peak), mock point-source tests across source plane (recov…: 1

### Key parameters and settings (bibcode: value)
- 2017Natur.548..430F: N(CH+)=3e12 cm-2 tau_0 dv_abs
- 2020ApJS..247...61F: Continuum: 4th-order polynomial fit to spectrum smoothed with 5 A box kernel
- 2020ApJS..247...61F: Requires z_IS+wind from at least three absorption lines and no -99 flag
- 2019MNRAS.485..229R: Mask limits scanned between -55±10 and +5±10 km/s; choose lowest reduced chi2 of flat-line fit
- 2019ApJ...872..196S: Trot assumed 200 K where no diagram fit
- 2018ApJ...856L..12N: six components fit to Ni II 1741/1751; assumed 20 km/s FWHM Gaussian for 21 cm
- 2020ApJ...905...85S: visibilities averaged temporally unless binned visibility spans >10 m in uv


### Assumptions (bibcode: value)
- 2017Natur.548..430F: absorbing screen uniformly covers background source of radius r_SMG
- 2019MNRAS.485..229R: Filling factor of 1 (lower limit on tau); tau_a = ln(I0/Iobs) equals tau
- 2019A&A...627A.114K: Single excitation temperature for all species, LTE
- 2019ApJ...872..196S: LTE, single Trot
- 2016ApJ...820L..39N: covering fraction <10%, representative H2 column, gas within 20 kpc sphere
- 2020ApJ...905...85S: Regularization strength set by maximizing Bayesian evidence for fixed lens parameters, iterated


### Limitations the authors admit
- 2017Natur.548..430F: Coarse velocity resolution; N(CH+) may be lower limits due to possible saturation
- 2017Natur.548..430F: Sample size is small
- 2018A&A...617A..54L: Planck CO maps are masked near some sightlines; weak CO detections may be missed
- 2020ApJS..247...61F: Spitzer blending can overestimate stellar masses; about one-third have contaminated Spitzer photometry
- 2020ApJS..247...61F: f-factor is the largest uncertainty in the Halpha measurement
- 2019MNRAS.485..229R: Mass may differ by up to an order of magnitude due to X-factor and F_ul uncertainty
- 2019MNRAS.485..229R: Filling factor of 1 gives lower limit on tau; velocities are only apparent line-of-sight motions
- 2019A&A...627A.114K: Model is not unique, has >40 free parameters, ignores substructure; masses may be overestimated
- 2019A&A...627A.114K: Continuum noise underestimated by line-contaminated continuum approach
- 2019ApJ...872..196S: Rotation temperatures are upper limits and column densities lower limits because low-Eu lines may be optically thick; large uncertainty in 13CH3OH columns; assumed 200 K
- 2025ApJ...990...66K: Continuum flux differs by ~45% between epochs; possible unnoticed flux scaling errors
- 2016ApJ...820L..39N: Higher-resolution data would be needed to confirm absence of substructure; dynamical mass is a lower limit
- 2025ApJ...984L..15P: Classification is subjective and inclination-biased
- 2025ApJ...984L..15P: Vertically isothermal assumption is a major limitation
- 2020MNRAS.496..364R: Tex assumes optically thin LTE, which the results contradict; covering factors give lower limits on tau
- 2017A&A...605L...6T: Methanol abundances may be overestimated because H2 may be underestimated due to clumpiness and coarse HF resolution
- 2014A&A...566L...6M: NE covering factor poorly known (0.3<fc<1.0); NE H2(37)Cl+ not detected, only a lower limit on the ratio.
- 2018ApJ...856L..12N: L_TIR has large systematic uncertainty because beta and T_dust are unconstrained by a single continuum point
- 2019A&A...622A..26G: CF+ and C3H+ lines are weak and contaminated; Galactic center abundances cannot be determined absolutely
- 2020ApJ...905...85S: Limited ALMA bandwidth prevents detection of redshifted P Cygni emission and caps vmax
- 2020ApJ...905...85S: Conservative classification is S/N dependent and may exclude weak outflows
- 2019MNRAS.490.1220K: Lensing magnification bias of background quasars remains a systematic issue
- 2019MNRAS.490.1220K: Conversion N(CO) to N(H2) is uncertain and not constant
- 2017A&A...600A..48G: Gas along -190 to -150 km/s cannot be precisely located along the line of sight; metallicity variations affect results.

### Settings cards flag as needed but not stated
- self-calibration solution intervals: 3
- flux scale uncertainty: 3
- line-free channels and continuum subtraction method: 2
- image size and cell size: 2
- line-free channels and continuum subtraction method for cubes: 1
- imaging task, cell size, image size, masks, cleaning depth: 1
- lens modelling code and details: 1
- bootstrap implementation for line fits: 1
- specific alpha value adopted: 1
- values of f_h2 and n_50 per source used in table 2: 1
- imaging parameters (weighting, cell, deconvolver) of the pipeline products: 1
- pipeline/casa version: 1
- spectral window setup and line-free channels used for continuum: 1
- integration velocity ranges for tau integrals: 1
- how optical depth was computed (saturation, noise handling): 1
- observing times, configurations, calibrators: 1
- hcn hyperfine treatment for n(hcn): 1
- details of pseudo-voigt hi fits: 1
- the alma data reduction and [c ii] line fitting are entirely deferred to bethermin et al. 2020; no …: 1
- the final catalogs are hosted at an author web page; the exact catalog contents are needed to repro…: 1
- mophongo/sextractor/lephare configuration beyond listed parameters (e.g. lephare redshift handling …: 1
- selection of galaxies in the ssfr stacks and number per bin not given: 1
- exact hst pointings and drizzle parameters beyond pixel scale: 1
- tclean parameters (weighting, robust, cell, image size, masking): 1
- line-free channels for continuum subtraction: 1
- flux calibrator and flux scale uncertainty: 1
- whether pipeline or manual calibration: 1
- exact extraction regions (circle radii/positions) for spectra: 1
- continuum flux measurement method: 1
- partition function and aul values used: 1
- pixel/beam used for moment maps and clipping: 1
- line-free channel ranges used for continuum fit: 1
- self-calibration solution intervals and reference models: 1
- image size and cell size, deconvolution masks, clean thresholds: 1
- procedure and values of positional shifts applied to each dataset: 1
- sma calibration details and relative weights used: 1
- full radmc-3d model parameter files and the chosen model among ~1000: 1
- gaussian fit software and procedure for flux errors: 1
- pipeline run details for the alma data: 1
- line-free channels used for continuum fitting/subtraction: 1

## Paper excerpts (18 of 18, chosen for detail and spread over fields/years)

### 2017Natur.548..430F: Large turbulent reservoirs of cold molecular gas around high-redshift starburst galaxies (2017; high_z_galaxies, astrochemistry; observational_alma_primary)
- question: What do CH+(1-0) emission and absorption lines reveal about shocks, turbulence and gas reservoirs around lensed z~2.5 starburst galaxies, and about feedback?
- step 2: Fit emission and absorption line profiles
  - method: simultaneous fit of emission and absorption Gaussians; tau_0 and N(CH+) derived [Methods 3 - Exploitation of the CH+ lin…: "Fits have been performed simultaneously on the emission and absorption lines"]
  - parameter: N(CH+)=3e12 cm-2 tau_0 dv_abs [Methods 3 - Exploitation of the CH+ lin…: "$$N({\rm CH^+})=3\times10^{12}{\,{\rm cm}^{-2}}\ \tau_0 \,(\Delta v_{\rm abs}/1\hbox{\,km\,s$^{-1}$})$$"]
  - assumption: absorbing screen uniformly covers background source of radius r_SMG [Methods 3 - Exploitation of the CH+ lin…: "of the background source assumed to be uniformly covered by the absorbing screen"]
  - fitting: Gaussian fits; bootstrap uncertainties [Methods 3 - Exploitation of the CH+ lin…: "have been evaluated with the bootstrap method to take into account the correlation between these parameters"]
- result: Peak absorption optical depth = 0.25-1.2 ± not stated dimensionless [abstract: "are large, in the range 0.25–1.2 (see Methods, Table 2)"]
- result: CH+ emission FWHM (Eyelash) = 1301 ± 112 km/s [Table 2: "| Eyelash | 30$\pm$53 | 1301$\pm$112 |"]
- limitation (authors): Coarse velocity resolution; N(CH+) may be lower limits due to possible saturation [Methods 3 - Exploitation of the CH+ lin…: "The estimated values of $N({\rm CH^+})$ could therefore be lower limits"]
- limitation (authors): Sample size is small [abstract: "Although the sample size is still small"]
- not stated (card): Line-free channels and continuum subtraction method for cubes; Imaging task, cell size, image size, masks, cleaning depth; Self-calibration solution intervals; Lens modelling code and details; Bootstrap implementation for line fits; Specific alpha value adopted; Values of f_H2 and n_50 per source used in Table 2; Flux scale uncertainty

### 2018A&A...617A..54L: Molecular gas and dark neutral medium in the outskirts of Chamaeleon (2018; milky_way_ism; observational_alma_primary)
- question: Can molecular gas, traced by HCO+ absorption, be detected in the outskirts of Chamaeleon where DNM was inferred but CO emission was not detected, and does it account for the DNM?
- step 1: Extract absorption spectra
  - method: Extract spectra at the peak continuum pixel from continuum-subtracted pipeline cubes and divide by continuum flux in that spectral window [2.1 New ALMA absorption measurements an…: "Spectra were extracted from the continuum-subtracted pipeline-processed data cubes at the pixel of peak continuum flux in the continuum map made from the spectral window containing each line"]
- limitation (authors): Planck CO maps are masked near some sightlines; weak CO detections may be missed [2.4 CO emission: "the Planck CO maps have been hashed over small regions in the immediate vicinity of several of our sightlines"]
- not stated (card): Imaging parameters (weighting, cell, deconvolver) of the pipeline products; Pipeline/CASA version; Spectral window setup and line-free channels used for continuum; Integration velocity ranges for tau integrals; How optical depth was computed (saturation, noise handling); Observing times, configurations, calibrators; HCN hyperfine treatment for N(HCN); Details of pseudo-Voigt HI fits

### 2020ApJS..247...61F: The ALPINE-ALMA [C II] Survey: Multiwavelength Ancillary Data and Basic Physical Measurements (2020; high_z_galaxies; large_program_or_survey)
- question: What are the ancillary multi-wavelength data and basic physical properties (stellar mass, SFR, UV luminosity, UV slope, Halpha, velocity offsets) of the ALPINE galaxies, and is the sample representative of 4<z<6 galaxies?
- step 2: Measure absorption-line redshifts and Ly-alpha properties
  - method: Cross-correlate Shapley06 template to absorption lines in five windows by chi2 minimization within +-600 km/s of a SpecPro prior redshift; combine PDFs; errors from 200 perturbations [2.4.1 Measurements: "The errors on these redshifts are derived by repeating this measurement $200$ times, thereby perturbing the fluxes according to a Gaussian error distribution"]
  - software: SpecPro
  - parameter: Continuum: 4th-order polynomial fit to spectrum smoothed with 5 A box kernel [2.4.1 Measurements: "The model is derived by fitting a 4$^{\rm th}$-order polynomial to the spectrum, which is smoothed by a $5\,{\textrm \AA}$ box kernel."]
  - fitting: chi2 minimization to template; chi2(z) converted to p(z) and combined [2.4.1 Measurements: "For each galaxy, the so obtained $\chi^2(z)$ distribution is then converted into a probability density function $p(z)$ for each of the windows."]
  - validation: Duplicate Keck/DEIMOS and VUDS spectra compared; redshifts agree within 280 km/s for most [2.1 Spectroscopic selection of ALPINE g…: "The redshifts are consistent within $280\,{\rm km\,s^{-1}}$ and we do not find any systematic offsets between the two observations"]
- step 3: Compute velocity offsets relative to [C II] and stack spectra by sSFR
  - method: Velocity differences from redshifts; median stacks in the [C II] rest frame for low (<4 Gyr^-1) and high (>5 Gyr^-1) sSFR [2.4.2 Velocity Offsets with respect to …: "namely low ($<4\,{\rm Gyr^{-1}}$) and high ($>5\,{\rm Gyr^{-1}}$) sSFR, in their corresponding rest-frames defined by the systemic redshift"]
  - parameter: Requires z_IS+wind from at least three absorption lines and no -99 flag [2.4.2 Velocity Offsets with respect to …: "we require that $z_{\rm IS + wind}$ is measured from at least three absorption lines"]
  - validation: [O II] from MOSFIRE for one galaxy agrees with [C II] redshift [2.4.3 How well does [C II] trace system…: "The position of the line agrees perfectly with the [C II] redshift derived from ALMA"]
- result: Ly-alpha vs IS+wind absorption velocity offset (median) = 386 ± +257/-279 km/s [2.4.2 Velocity Offsets with respect to …: "We find a median offset on the order of $386^{+257}_{-279}\,{\rm km\,s^{-1}}$"]
- result: IS+wind absorption offset from [C II] systemic = -227 ± +168/-206 km/s [2.4.2 Velocity Offsets with respect to …: "For the former we find an offset of $-227^{+168}_{-206}\,{\rm km\,s^{-1}}$"]
- result: Ly-alpha offset from [C II] systemic = 184 ± +201/-215 km/s [2.4.2 Velocity Offsets with respect to …: "for the latter we find $184^{+201}_{-215}\,{\rm km\,s^{-1}}$"]
- result: Absorption-line blueshift in high-sSFR stack = 300-400 ± not stated km/s [2.4.2 Velocity Offsets with respect to …: "in the high sSFR stack the lines are significantly blue shifted by $300-400\,{\rm km\,s^{-1}}$"]
- limitation (authors): Spitzer blending can overestimate stellar masses; about one-third have contaminated Spitzer photometry [4.1.1 Fitting Method: "In total, one-third of the galaxies have contaminated Spitzer photometry to some degree."]
- limitation (authors): f-factor is the largest uncertainty in the Halpha measurement [4.4 Measurement of Halpha emission: "The $f$-factor is the largest uncertainty in this measurement method"]
- not stated (card): The ALMA data reduction and [C II] line fitting are entirely deferred to Bethermin et al. 2020; no calibration or imaging settings given here; The final catalogs are hosted at an author web page; the exact catalog contents are needed to reproduce numbers; Mophongo/SExtractor/LePhare configuration beyond listed parameters (e.g. LePhare redshift handling is fixed to spectroscopic z but not explicit…

### 2019MNRAS.485..229R: Deep and narrow CO absorption revealing molecular clouds in the Hydra-A brightest cluster galaxy (2019; galaxy_clusters_and_sz, agn_and_quasars, nearby_galaxies; observational_alma_primary)
- question: Are there cold molecular gas clouds along the line of sight to the Hydra-A mm-continuum core, and what are their kinematics, temperature and column densities (as a test of chaotic cold accretion)?
- step 3: Remove emission and fit absorption features
  - method: Fit and subtract a Gaussian emission line excluding absorption channels (about -48 to -1 km/s), then triple-Gaussian fit via Monte Carlo [6 Cold, Clumpy Gas Clouds: "We find that a triple-Gaussian line provides the best fit to the absorption features"]
  - parameter: Mask limits scanned between -55±10 and +5±10 km/s; choose lowest reduced chi2 of flat-line fit [6 Cold, Clumpy Gas Clouds: "The selected range produces a spectrum with the lowest $\chi^{2}_{\nu}$ value when the non-masked region is fitted to a flat line after the removal of the emission."]
  - assumption: Filling factor of 1 (lower limit on tau); tau_a = ln(I0/Iobs) equals tau [6 Cold, Clumpy Gas Clouds: "We assume a filling factor of 1, so our calculations provide a lower limit on the optical depths of the absorbing regions."]
  - fitting: Monte Carlo with 100000 simulated spectra [6 Cold, Clumpy Gas Clouds: "we estimate the properties of these emission lines using an appropriately modified version of the Monte Carlo method"]
- result: Peak CO(2-1) optical depth, region A = 0.88 ± +0.06/-0.06 dimensionless [Table 2: "| A | -42.8 $^{+0.1}_{-0.1}$ | -33$^{+2}_{-2}$ | 4.4 $^{+0.3}_{-0.3}$ | 0.88$^{+0.06}_{-0.06}$ |"]
- result: Region A FWHM = 4.4 ± +0.3/-0.3 km/s [Table 2: "| A | -42.8 $^{+0.1}_{-0.1}$ | -33$^{+2}_{-2}$ | 4.4 $^{+0.3}_{-0.3}$ | 0.88$^{+0.06}_{-0.06}$ |"]
- limitation (authors): Mass may differ by up to an order of magnitude due to X-factor and F_ul uncertainty [5 Molecular Gas Mass of the Disc: "the molecular mass may differ from the estimated values by as much as an order of magnitude"]
- limitation (authors): Filling factor of 1 gives lower limit on tau; velocities are only apparent line-of-sight motions [6 Cold, Clumpy Gas Clouds: "these are simply apparent motions along the line-of-sight"]
- not stated (card): tclean parameters (weighting, robust, cell, image size, masking); line-free channels for continuum subtraction; flux calibrator and flux scale uncertainty; whether pipeline or manual calibration; exact extraction regions (circle radii/positions) for spectra; continuum flux measurement method; partition function and Aul values used; pixel/beam used for moment maps and clipping

### 2019A&A...627A.114K: Massive dust clumps in the envelope of the red supergiant VY Canis Majoris (2019; evolved_stars; observational_alma_primary)
- question: What is the structure and dust mass of the dusty clumps in the inner envelope of VY CMa, and was their mass underestimated in earlier studies?
- step 5: Absorption spectrum of clump C
  - method: LTE simulation of absorption lines with single Tex [3.4 Resolved observations of clump C: "We simulated the absorption components assuming LTE conditions and using CASSIS"]
  - software: CASSIS
  - assumption: Single excitation temperature for all species, LTE [3.4 Resolved observations of clump C: "Single excitation temperature was assumed for all species"]
  - fitting: Best agreement found at Tex = 52 K (3 sigma 37–67 K) [3.4 Resolved observations of clump C: "best agreement with observations was found at $T_{\rm ex}$=52 K (3$\sigma$ range of 37–67 K)"]
- result: Excitation temperature of absorbing gas toward C = 52 ± 3 sigma range 37–67 K K [3.4 Resolved observations of clump C: "best agreement with observations was found at $T_{\rm ex}$=52 K (3$\sigma$ range of 37–67 K)"]
- limitation (authors): Model is not unique, has >40 free parameters, ignores substructure; masses may be overestimated [7 Discussion and conclusions: "our masses can be largely overestimated, mainly because the model ignores unresolved substructure within the dusty clumps and dust opacity is essentially unknown"]
- limitation (authors): Continuum noise underestimated by line-contaminated continuum approach [2 Observations: "In this approach, we took advantage of the continuum flux underlying the numerous spectral lines but underestimate the real noise in the data."]
- not stated (card): Line-free channel ranges used for continuum fit; Self-calibration solution intervals and reference models; Image size and cell size, deconvolution masks, clean thresholds; Procedure and values of positional shifts applied to each dataset; SMA calibration details and relative weights used; Full RADMC-3D model parameter files and the chosen model among ~1000; Gaussian fit software and procedure for…

### 2019ApJ...872..196S: Implications of a Hot Atmosphere/Corino from ALMA Observations toward NGC 1333 IRAS 4A1 (2019; star_formation, astrochemistry; observational_alma_primary)
- question: Do the protostellar binary cores IRAS 4A1 and 4A2 host complex organic molecules, and what do the continuum opacity and COM absorption/emission imply for the nature of A1?
- step 5: Derive Trot and column densities
  - method: Rotation diagram, LTE; for A1 absorption (Scenario I) optically thin foreground layer against continuum background [3.3 Gas temperatures: "we assume that most, if not all, of the observed transitions in A1 are optically thin and there is no saturation in absorption."]
  - parameter: Trot assumed 200 K where no diagram fit [3.3 Gas temperatures: "for molecules where do not have any estimation of rotational temperature, we choose the temperature to be 200 K"]
  - assumption: LTE, single Trot [3.3 Gas temperatures: "characterized by a single (rotation) temperature T$_{ex} =$ T$_{rot}$, if its excitation is assumed in local thermodynamic equilibrium (LTE)"]
- result: Trot 13CH3OH in A2 / CH3CHO in A2 = 375.13 / 261.31 ± 270.02 / 10.79 K [3.3 Gas temperatures: "we obtained rotation temperatures of 375.13$\pm$270.02 K and 261.31$\pm$10.79 K for $^{13}$CH$_3$OH and the CH$_3$CHO, respectively."]
- result: Trot CH3OH / 13CH3OH in A1 = 140.39 / 58.94 ± 6.63 / 3.74 K [3.3 Gas temperatures: "rotation temperatures for CH$_3$OH and $^{13}$CH$_3$OH are 140.39$\pm$6.63 K and 58.94$\pm$ 3.74 K, respectively."]
- result: CH3OH column density in A1 = >= 1.14e17 ± 0.17e17 cm^-2 [Table 3: "$\leq 140.39 \pm 6.63$ K | $\geq (1.14 \pm 0.17)\times 10^{17}$"]
- limitation (authors): Rotation temperatures are upper limits and column densities lower limits because low-Eu lines may be optically thick; large uncertainty in 13CH3OH columns; assumed 200 K [3.3 Gas temperatures: "These temperatures should be taken as upper limits though, as their corresponding lower E$_u$ lines are possibly optically thick."]
- not stated (card): Line-free channels used for continuum fitting/subtraction; Image size, cell size, deconvolver, masks and clean thresholds; Flux, bandpass and phase calibrators; Integration velocity ranges for moment maps; Partition functions and line strengths used in rotation diagrams; Details of how 2D Gaussian fits and stacking were done; Whether self-calibration was applied

### 2025ApJ...990...66K: Reexamination of the CO Absorption Line in the M87 Nucleus (2025; agn_and_quasars, nearby_galaxies; archival_reuse)
- question: Is the CO(2–1) absorption line reported toward the M87 nucleus in archival ALMA data real, or an artifact of bandpass calibration and telluric contamination?
- step 2: Extract nuclear spectra and fit absorption
  - method: Spectrum from central region 0.77x0.59 arcsec; Gaussian fit of absorption; tau = ln(Scont/Sobs) [3.1 TC (2015-06-15): "From the Gaussian fit, we obtain the continuum flux level, the flux at the line center, the line center velocity, and the line width"]
  - software: CARTA
  - fitting: Gaussian fit (details not stated) [Results, TC (2015-06-15): "From the Gaussian fit, we obtain the continuum flux level, the flux at the line center, the line center velocity, and the line width as"]
- result: TC continuum flux (original calibration) = 1.660 ± not stated Jy [3.1 TC (2015-06-15): "we obtain the continuum flux level, the flux at the line center, the line center velocity, and the line width as $1.660~{\rm Jy}$"]
- result: TC optical depth tau_21 (original) = 0.05 ± not stated dimensionless [3.1 TC (2015-06-15): "In case of TC, we have $\tau_{21,\rm TC}\simeq 0.05$."]
- result: TE optical depth upper limit = 0.0190 ± not stated dimensionless [3.2 TE (2015-08-16): "$\tau_{21,{\rm TE}}\lesssim 0.0190$"]
- limitation (authors): Continuum flux differs by ~45% between epochs; possible unnoticed flux scaling errors [3.2 TE (2015-08-16): "However, there may be some unnoticed flux scaling errors which could cause such an apparent variability."]
- not stated (card): Exact recipe for re-running bandpass calibration without removing the telluric feature (CASA commands, channels flagged or interpolated); Whether the archive calibration scripts or the README were used directly; Line-free channels and continuum subtraction method; Image size and cell size; Spectral window layout and frequency setup; Details of the Tsys and atmospheric transmission analysis; Deriv…

### 2018A&A...620A.119D: X-shooter and ALMA spectroscopy of GRB 161023A. A study of metals and molecules in the line of sight towards a luminous GRB (2018; transients, astrochemistry, high_z_galaxies; multi_facility_alma_minor)
- question: Use the GRB 161023A afterglow as a background source to study the host environment, molecular content (via ALMA mm spectroscopy) and intervening systems along the line of sight.
- step 3: Voigt-fit host absorption lines and derive metallicity
  - method: Voigt profile fits of X-shooter lines [3.3.3: "We fit the absorption lines of the host complex with Voigt profiles using the FITLYMAN environment in Midas"]
  - software: FITLYMAN/MIDAS
  - validation: Agreement with Heintz et al. 2018 [3.3.3: "are in good agreement with (cite: hei18) who used the same data set but a different Voigt-profile fitting code"]
- result: [Zn/H] = -1.11 ± 0.07 dex [3.3.3: "\[Zn/H\] $=-1.11\pm0.07$"]
- not stated (card): tclean parameters (cell, image size, masking, deconvolver) not given; Spectral rms and line width used to derive the 3.9 km/s optical-depth limit; How continuum was normalised for optical depth; Flux scale uncertainty; Line-free channels and continuum handling; Velocity width Delta V assumed for CO/HCO+ lines

### 2016ApJ...820L..39N: First Connection between Cold Gas in Emission and Absorption: CO Emission from a Galaxy-Quasar Pair (2016; nearby_galaxies, agn_and_quasars; observational_alma_primary)
- question: Does the z = 0.101 galaxy toward PKS 0439-433 emit CO(1-0), and does the molecular absorption toward the quasar arise from its molecular disk or from its CGM?
- step 5: Compare emission with absorption
  - method: Compare absorption component velocities to disk rotation curve and extrapolate surface density to sightline [4.2: "we can calculate the rotational velocity needed to produce the velocity shifts seen in the absorption components."]
  - assumption: covering fraction <10%, representative H2 column, gas within 20 kpc sphere [4.4: "(iii) only gas within a sphere of 20 kpc of the galaxy is considered."]
- result: molecular gas in absorbing component = ≲1e5 ± not stated Msun [4.4: "the absorbing molecular component contains ≲ 10 [5] M ⊙ of gas"]
- limitation (authors): Higher-resolution data would be needed to confirm absence of substructure; dynamical mass is a lower limit [4.1: "although higher- resolution data would be required to confirm this"]
- not stated (card): CASA version; cell size and image size; clean threshold, masks and iterations; continuum subtraction and line-free channels; self-calibration solution intervals; MCMC priors, chain length, step sizes and likelihood; on-source time, number of antennas, baselines; how R_D and the 10 kpc disk radius were derived; exact CO line luminosity conversion details; how the SFR of 1.5 was adopted vs 0.53

### 2025ApJ...984L..15P: exoALMA. X. Channel Maps Reveal Complex <SUP>12</SUP>CO Abundance Distributions and a Variety of Kinematic Structures with Evidence for Embedded Planets (2025; protoplanetary_disks, astrochemistry, exoplanets; large_program_or_survey)
- question: What kinematic substructures and CO abundance distributions appear in individual 12CO J=3-2 channel maps of the 15 exoALMA disks, and are they consistent with embedded planets?
- step 1: Reimage cubes and inspect channel maps
  - method: Reimaged exoALMA visibilities at several resolutions and binnings without continuum subtraction, and checked against continuum-subtracted maps and regularized maximum likelihood imaging [Observations and Imaging: "we imaged all the channel maps without continuum subtraction, and checked that the detected kinematic deviations are also present in the corresponding continuum-subtracted maps."]
  - software: CASA
  - validation: Compared CLEAN, continuum-subtracted and regularized maximum likelihood images [Observations and Imaging: "confirming that the detections presented here are not artifacts of the imaging process."]
- limitation (authors): Classification is subjective and inclination-biased [A Variety of Kinematic Substructures: "Our classification is subjective, and some sources clearly exhibit multiple types of substructures."]
- limitation (authors): Vertically isothermal assumption is a major limitation [Discussion: "One major limitation of our models is the assumption of a vertically isothermal profile in phantom."]
- not stated (card): Weighting schemes (robust, taper) and exact channel binning for each disk's reimaged cubes; Which channels are shown for each disk; Exact dynamite fitting setup and uncertainties; Criteria for the visual classification; Beam and noise for the Figure 6 cubes; Planet-wake projection details; Specific depletion factor grid values; Number of mcfost photons and grid setup

### 2020MNRAS.496..364R: A molecular absorption line survey towards the AGN of Hydra-A (2020; nearby_galaxies, agn_and_quasars, astrochemistry; observational_alma_primary)
- question: What molecular species and cloud properties are revealed by multi-line molecular absorption against the Hydra-A AGN, and does the absorption vary over two years?
- step 1: Extract absorption spectra
  - method: Channel maps at maximal spectral resolution; spectra extracted from a beam-sized region at the continuum source [2 Observations and target lines: "All are extracted from a region centered on the continuum source with a size equal to the synthesized beam’s FHWM."]
  - software: CASA
- limitation (authors): Tex assumes optically thin LTE, which the results contradict; covering factors give lower limits on tau [4.1 Excitation temperature estimates: "the values should only be treated as approximations"]
- not stated (card): tclean/imaging parameters (weighting, robust, cell, image size, continuum subtraction, line-free channels); Continuum RMS used and how continuum level extracted; Flux calibrators and flux scale uncertainty; Partition functions, Einstein A values and spectroscopic database used; How the 2016 and 2018 data were matched in resolution for variability test; Exact fitting algorithm/software for Gaussia…

### 2017A&A...605L...6T: Complex organic molecules in diffuse clouds along the line of sight to Sagittarius B2 (2017; astrochemistry, milky_way_ism; archival_reuse)
- question: Do complex organic molecules exist in diffuse molecular clouds along the line of sight to Sgr B2(N), and is their composition similar to the z = 0.89 absorber?
- step 1: Extract K4 absorption spectra
  - method: Use EMoCA calibrated data, primary-beam corrected spectra toward K4 [Observations and analysis method: "We corrected the spectra for the primary beam attenuation."]
- limitation (authors): Methanol abundances may be overestimated because H2 may be underestimated due to clumpiness and coarse HF resolution [Discussion: "it may be that the abundances we obtain are overestimated due to an underestimate of the H$_2$ column density"]
- not stated (card): CASA version and imaging parameters (in EMoCA paper); Spectral extraction position/aperture at K4; Fitting algorithm and uncertainty estimation for Weeds fits; Detection criteria and how upper limits were defined; Continuum level/handling for absorption optical depth; Uncertainties for column densities

### 2014A&A...566L...6M: Detection of chloronium and measurement of the <SUP>35</SUP>Cl/<SUP>37</SUP>Cl isotopic ratio at z = 0.89 toward PKS 1830-211 (2014; nearby_galaxies, astrochemistry; observational_alma_primary)
- question: Is chloronium (H2Cl+) detectable in the z=0.89 absorber toward PKS 1830-211, and what is the 35Cl/37Cl isotopic ratio at that look-back time?
- step 1: Extract absorption spectra per lensed image
  - method: Model visibilities with two point sources with fixed relative positions and free flux densities [Data: "by modelling the visibilities with two point-like sources where the relative positions were fixed and the flux densities left as free parameters."]
  - software: uvmultifit
- result: H2(35)Cl+ FWHM SW = 32 ± 1 km/s [Column densities and abundances: "wider (FWHM=32$\pm$1 km s$^{-1}$)"]
- limitation (authors): NE covering factor poorly known (0.3<fc<1.0); NE H2(37)Cl+ not detected, only a lower limit on the ratio. [Column densities and abundances: "Note that the covering factor is not well known toward the NE image, but the ALMA data suggest 0.3$<$$f_c$$<$1.0."]
- not stated (card): Calibration pipeline, CASA version, calibrators (all deferred to Paper I); Continuum normalization and uvmultifit settings; Velocity range for integrated opacity; Monte Carlo procedure details and initial Gaussian parameters; Hanning smoothing procedure and relative hyperfine weights used

### 2018ApJ...856L..12N: Molecular Emission from a Galaxy Associated with a z ∼ 2.2 Damped Lyα Absorber (2018; high_z_galaxies, other; observational_alma_primary)
- question: Is a high-metallicity z~2.2 DLA toward QSO B1228-113 associated with a molecular gas-rich galaxy, and what is the multi-phase nature of the absorbing gas?
- step 5: Fit absorption lines and HI 21cm spin temperature
  - method: MCMC Voigt fitting of UVES metal lines with tied components; GMRT 21 cm optical depth limit and covering factor [2.1 UVES Observations: "a Monte Carlo Markov Chain Voigt profile fitting routine publicly available in the LINETOOLS"]
  - software: LINETOOLS, AIPS
  - parameter: six components fit to Ni II 1741/1751; assumed 20 km/s FWHM Gaussian for 21 cm [2.4 GMRT Observations: "assuming a Gaussian line profile with a FWHM of 20 km s$^{-1}$"]
  - fitting: MCMC Voigt profile fitting; priors not stated [UVES Observations: "refitted the metal lines using a Monte Carlo Markov Chain Voigt profile fitting routine publicly available in the LINETOOLS [^1] package"]
  - validation: Metallicity consistent with previous measurement [2.1 UVES Observations: "consistent with the previous measurement"]
- result: Spin temperature lower limit = 1895 x (f/0.93) ± 3 sigma limit K [2.4 GMRT Observations: "The $3\sigma$ lower limit to the DLA spin temperature is then $T_{\rm s} > 1895 \times (f/0.93)$ K."]
- result: DLA metallicity [M/H] = -0.27 ± 0.10 dex [2.1 UVES Observations: "resulting in an updated metallicity of ${\rm [M/H]} = -0.27 \pm 0.10$"]
- limitation (authors): L_TIR has large systematic uncertainty because beta and T_dust are unconstrained by a single continuum point [3.1 Galaxy Properties: "This estimate has a large systematic uncertainty ($\sim$0.6 dex) because both $\beta$ and $\text{T}_{\text{dust}}$ are not constrained by the single dust continuum measurement."]
- not stated (card): ALMA/CASA and pipeline versions; Line-free channels and continuum subtraction method; Image size and cell size; Self-calibration solution intervals; Method of fitting the CO line and extracting flux (aperture or Gaussian); Flux scale uncertainty; SINFONI aperture and narrow-band widths; Details of SFR-TIR dust correction calibration

### 2019A&A...622A..26G: Molecular ion abundances in the diffuse ISM: CF<SUP>+</SUP>, HCO<SUP>+</SUP>, HOC<SUP>+</SUP>, and C<SUB>3</SUB>H<SUP>+</SUP> (2019; milky_way_ism, astrochemistry; observational_alma_primary)
- question: Can HCO+, HOC+ and CF+ (and C3H+) absorption serve as probes of diffuse molecular hydrogen, and what are their abundances relative to H2 and implications for chemistry?
- step 1: Extract absorption spectra
  - method: Spectra extracted at continuum peak or weighted average of bright pixels, divided by continuum, smoothed to 1 km/s [ALMA observations: "The absorption spectra have been obtained by dividing the observed spectra by the continuum intensity in the same band."]
  - software: CASA, GILDAS
- limitation (authors): CF+ and C3H+ lines are weak and contaminated; Galactic center abundances cannot be determined absolutely [Summary and conclusions: "Absolute abundances cannot be determined in the central molecular zone because the relative abundances of the usual H$_2$-tracers (CH, HF, etc) have not been established in this region"]
- not stated (card): CASA version and calibration/imaging parameters (weighting, cell, masks); Exact line-free channels / continuum level choice per window; Pixels and weights used for averaged spectra; Herschel HF/H2O/CH spectra reduction and velocity alignment; Uncertainty estimation for column densities and fit errors; Parameter values (x_C, f(H2), T) used in chemical model figures

### 2020ApJ...905...85S: Ubiquitous Molecular Outflows in z &gt; 4 Massive, Dusty Galaxies. I. Sample Overview and Clumpy Structure in Molecular Outflows on 500 pc Scales (2020; high_z_galaxies; observational_alma_primary)
- question: How common are molecular outflows (traced by OH 119 um absorption) in z>4 lensed dusty star-forming galaxies, and what is their spatial structure on ~500 pc scales?
- step 4: Lens model continuum and reconstruct OH absorption components
  - method: Pixellated visibility-space lens modeling with SIE (+shear, multipoles) and gradient regularization; lens parameters from continuum then applied to OH velocity ranges [3.3 Lens Modeling Methods and Tests: "We fit for the lensing potential using a Markov Chain Monte Carlo (MCMC) sampling algorithm."]
  - software: ripples, visilens
  - parameter: visibilities averaged temporally unless binned visibility spans >10 m in uv [3.3 Lens Modeling Methods and Tests: "which we average temporally unless doing so would cause a binned visibility to span more than 10m in the $uv$ plane"]
  - assumption: Regularization strength set by maximizing Bayesian evidence for fixed lens parameters, iterated [3.3 Lens Modeling Methods and Tests: "The best-fit strength of the regularization is determined by maximizing the Bayesian evidence given a fixed set of parameters for the lensing potential."]
  - fitting: MCMC for lens potential; iterative regularization/MCMC; priors not stated [3.3 Lens Modeling Methods and Tests: "we perform an iterative process of fitting for the regularization strength, MCMC fitting for the lens parameters, and re-fitting for the regularization strength until all parameters have converged."]
  - validation: Deviance information criterion, negative-bowl check (>=10% of peak), mock point-source tests across source plane (recover fluxes to ~25%) [3.3.1 Model Selection and Tests: "This final test shows that even these weak signals are recoverable to $\approx$25% accuracy."]
- limitation (authors): Limited ALMA bandwidth prevents detection of redshifted P Cygni emission and caps vmax [4.1 Molecular Outflow Detection Rate: "our ability to detect redshifted emission as in the classic P Cygni profile is limited due to the small ALMA bandwidth"]
- limitation (authors): Conservative classification is S/N dependent and may exclude weak outflows [3.2 Molecular Outflow Classification: "This definition has the drawback of being signal-to-noise dependent, which may exclude weak outflows"]
- not stated (card): CASA version and pipeline versions per cycle; Line-free channel ranges and continuum-subtraction method for each source; Cell size, image size, clean masks and exact tclean parameters; Self-calibration solution intervals per source and exact flux/bandpass/phase calibrators; MCMC settings (sampler, priors, chain lengths) for lens models; visilens/ripples configuration; Pixel grid sizes in source a…

### 2019MNRAS.490.1220K: ALMACAL - VI. Molecular gas mass density across cosmic time via a blind search for intervening molecular absorbers (2019; high_z_galaxies, agn_and_quasars, milky_way_ism; large_program_or_survey)
- question: What is the cosmic molecular gas mass density and CO column density distribution, constrained via a blind search for intervening CO absorbers towards ALMA calibrators?
- step 2: blind absorption line search
  - method: 5 sigma threshold in two consecutive channels after smoothing with kernels 10-190 km/s; remove edge, Galactic, artefact, atmospheric and implausible-redshift candidates [3.1: "We use a range of smoothing kernels between 10 and 190 $\rm km\, s^{-1}$ in steps of 10 $\rm km\, s^{-1}$."]
  - software: SPLATALOGUE
- limitation (authors): Lensing magnification bias of background quasars remains a systematic issue [4: "the uncertainties introduced by lensing of the background quasar by the foreground absorber will remain a systematic issue"]
- limitation (authors): Conversion N(CO) to N(H2) is uncertain and not constant [3.2: "the column density ratio of $N({\rm CO})/ N(\mbox{H}_2)$ over a large range of H$_2$ column densities is not constant"]
- not stated (card): ALMA project list and exact execution blocks used; Butterworth filter order and implementation; Exact noise estimation per spectrum; Software versions and code for spectrum extraction; Redshift lists of the 622 calibrators; Details of the rho(H2) scaling of Zwaan2006 functional form

### 2017A&A...600A..48G: ALMA hints at the existence of an unseen reservoir of diffuse molecular gas in the Galactic bulge (2017; milky_way_ism, astrochemistry; observational_alma_primary)
- question: Why is mm-wave molecular absorption seen at -200 to -140 km/s toward B1741-312, away from bulge regions with prominent CO emission, and does it trace an unseen reservoir of molecular gas in the bulge?
- step 1: Extract ALMA absorption spectra
  - method: Spectra extracted from pipeline cubes at the pixel of peak continuum flux [2.1 ALMA absorption measurements: "Spectra were extracted from the final data cubes at the pixel of peak continuum flux."]
  - software: ALMA pipeline
- result: Continuum flux of B1741-312 = 0.59 ± not stated Jy [2.1 ALMA absorption measurements: "The continuum flux was 0.59 Jy"]
- limitation (authors): Gas along -190 to -150 km/s cannot be precisely located along the line of sight; metallicity variations affect results. [4 Summary: "cannot be precisely located along the line of sight owing to imprecise knowledge of the bar-like inner-galaxy velocity field"]
- not stated (card): Pipeline/CASA version and calibrators; Imaging parameters (weighting, cell, beam) of the cubes; Continuum normalization and baseline fitting for optical depth; Velocity ranges and integration details beyond Table 1; Excitation/hyperfine treatment for HCN; Derivation details of n_100 I_UV values; Exact procedure for inverting E(J-K) vs distance modulus

## All papers in this technique

- 2014A&A...566L...6M (2014): Detection of chloronium and measurement of the <SUP>35</SUP>Cl/<SUP>37</SUP>Cl isotopic ratio at z = 0.89 toward PKS 1830-211
- 2016ApJ...820L..39N (2016): First Connection between Cold Gas in Emission and Absorption: CO Emission from a Galaxy-Quasar Pair
- 2017A&A...600A..48G (2017): ALMA hints at the existence of an unseen reservoir of diffuse molecular gas in the Galactic bulge
- 2017A&A...605L...6T (2017): Complex organic molecules in diffuse clouds along the line of sight to Sagittarius B2
- 2017Natur.548..430F (2017): Large turbulent reservoirs of cold molecular gas around high-redshift starburst galaxies
- 2018A&A...617A..54L (2018): Molecular gas and dark neutral medium in the outskirts of Chamaeleon
- 2018A&A...620A.119D (2018): X-shooter and ALMA spectroscopy of GRB 161023A. A study of metals and molecules in the line of sight towards a luminous GRB
- 2018ApJ...856L..12N (2018): Molecular Emission from a Galaxy Associated with a z ∼ 2.2 Damped Lyα Absorber
- 2019A&A...622A..26G (2019): Molecular ion abundances in the diffuse ISM: CF<SUP>+</SUP>, HCO<SUP>+</SUP>, HOC<SUP>+</SUP>, and C<SUB>3</SUB>H<SUP>+</SUP>
- 2019A&A...627A.114K (2019): Massive dust clumps in the envelope of the red supergiant VY Canis Majoris
- 2019ApJ...872..196S (2019): Implications of a Hot Atmosphere/Corino from ALMA Observations toward NGC 1333 IRAS 4A1
- 2019MNRAS.485..229R (2019): Deep and narrow CO absorption revealing molecular clouds in the Hydra-A brightest cluster galaxy
- 2019MNRAS.490.1220K (2019): ALMACAL - VI. Molecular gas mass density across cosmic time via a blind search for intervening molecular absorbers
- 2020ApJ...905...85S (2020): Ubiquitous Molecular Outflows in z &gt; 4 Massive, Dusty Galaxies. I. Sample Overview and Clumpy Structure in Molecular Outflows on 500 pc …
- 2020ApJS..247...61F (2020): The ALPINE-ALMA [C II] Survey: Multiwavelength Ancillary Data and Basic Physical Measurements
- 2020MNRAS.496..364R (2020): A molecular absorption line survey towards the AGN of Hydra-A
- 2025ApJ...984L..15P (2025): exoALMA. X. Channel Maps Reveal Complex <SUP>12</SUP>CO Abundance Distributions and a Variety of Kinematic Structures with Evidence for Emb…
- 2025ApJ...990...66K (2025): Reexamination of the CO Absorption Line in the M87 Nucleus

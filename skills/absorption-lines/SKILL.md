---
name: alma-absorption-lines
description: "Measure molecular absorption lines against bright continuum sources (quasars, AGN cores, lensed starbursts, Galactic background sources, protostellar or stellar continua) in ALMA data: extract and normalize spectra, derive optical depth and covering factor, fit velocity components, convert to column densities and abundances, and run blind absorber searches. Use when a task involves tau = -ln(S/S_cont), absorption against a continuum, covering factors, intervening or associated molecular absorbers, or checking whether an absorption feature is real. Built from 18 ALMA papers (2014-2025); evidence is thin, see the warnings inside."
---

# Molecular absorption against continuum sources

Absorption spectroscopy measures the line-of-sight optical depth of foreground gas against a compact continuum
background: tau(v) = -ln(R(v)), where R is the transmission (R = S_obs/S_cont for total-flux spectra, R = 1 +
S_line/S_cont for continuum-subtracted spectra). Its strength is sensitivity to cold, low-density gas that emission misses;
its weakness is that every derived column depends on the covering factor, excitation temperature and saturation.
The two mistakes that matter most: (1) assuming covering factor 1 and ignoring saturation, then reporting columns
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
Papers use one of five extractions:

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
- Normalize by the continuum measured in the spectral window that contains the line: 2018A&A...617A..54L extracted
  from continuum-subtracted pipeline cubes and divided by the peak continuum flux from the continuum map of that
  window. 2019A&A...622A..26G divided by "the continuum intensity in the same band"; its card flags the exact
  continuum choice per window as not stated. Using the line's own window is a recommendation, not a shown consensus.
- Or take the continuum level from the line fit itself (Gaussian fit returns continuum, line-centre flux, centre
  velocity and width; 2025ApJ...990...66K).
- Know which kind of spectrum you have before normalizing (general practice):
  - total-flux spectrum S_obs: transmission R = S_obs/S_cont;
  - continuum-subtracted spectrum S_line (negative in absorption): R = 1 + S_line/S_cont.
  Dividing a continuum-subtracted residual by S_cont gives R - 1, not R, and its logarithm is meaningless.
- Either way tau needs the absolute continuum level, so measure S_cont (from a continuum map or line-free channels)
  before or alongside any continuum subtraction.
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
- tau(v) = ln(S_cont / S_obs(v)) on total-flux spectra (2025ApJ...990...66K, 2019MNRAS.485..229R); in general
  tau(v) = -ln R(v) with R defined as in step 3. This equals the true tau only for covering factor 1 and negligible
  excitation temperature relative to the background brightness (general practice).
- Where R <= 0 or R is within the noise of zero (saturated or noise-dominated channels), tau is undefined: quote a
  lower limit on tau from the noise (e.g. R < 3 sigma_R gives tau > -ln(3 sigma_R)), not a value (general practice).
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
- With partial coverage and negligible line emission, R = 1 - f_c + f_c exp(-tau), so
  tau = -ln(1 - (1 - R)/f_c) (general practice). It is defined only for 1 - R < f_c; the line depth 1 - R sets a lower
  limit f_c >= 1 - R_min. Propagate the f_c range (e.g. 0.3-1.0 for 2014A&A...566L...6M) into tau and column limits
  rather than quoting the f_c = 1 value alone.
- Residual flux at line centre is not on its own evidence for f_c < 1: ordinary unsaturated absorption also leaves
  residual flux, and unresolved velocity structure or emission filling can mimic it. Infer partial coverage only
  with independent evidence of saturation, such as isotopologue or multi-line ratios or hyperfine ratios that
  imply large tau while the line bottom stays flat above zero (general practice; the pack shows no paper using a
  specific diagnostic).

### 7. Convert tau to column density
- Column proportional to integrated optical depth for a single line, e.g. N(CH+) = 3e12 cm^-2 * tau_0 *
  (dv_abs / 1 km/s) (2017Natur.548..430F, peak tau 0.25-1.2). This relation holds for the true integrated tau
  whether or not the line is thin; the optically thin approximation enters only when tau is read from the flux
  decrement. The authors say N(CH+) may be a lower limit because of possible saturation and coarse velocity
  resolution. The excitation assumption behind the coefficient (all molecules in the lower level) is general
  background; the card does not state it.
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
- Ratios to H2 tracers: HCO+, HOC+, CF+ against CH, HF and other H2 proxies (2019A&A...622A..26G). Its authors note
  the CF+ and C3H+ lines are weak and contaminated: assess blends and deblend, or report qualified limits, before
  deriving those columns and ratios.
- HCO+ absorption as dark-gas tracer where CO emission is undetected (2018A&A...617A..54L, 2017A&A...600A..48G).
  "Undetected" is not "absent": 2018A&A...617A..54L notes the Planck CO maps are masked near some sightlines and weak
  CO may be missed. Check CO map masks, sensitivity and coverage at each sightline before calling gas dark.
- N(CO)/N(H2) is not constant over a large range of H2 columns (2019MNRAS.490.1220K).
- H2 can be underestimated (clumpy gas, coarse HF resolution), which inflates abundances (2017A&A...605L...6T).
- In the Galactic center, absolute abundances could not be set because H2-tracer abundances are not established
  there (2019A&A...622A..26G).
- Masses from absorption carry order-of-magnitude uncertainty from X-factor and F_ul (2019MNRAS.485..229R).

### 9. Blind searches for intervening absorbers
- 2019MNRAS.490.1220K: smooth each spectrum with kernels from 10 to 190 km/s in 10 km/s steps; flag candidates at
  5 sigma in two consecutive channels; reject edge channels, Galactic lines, artifacts, atmospheric lines and
  implausible redshifts; identify with Splatalogue. The card flags the Butterworth filter order and implementation
  and the exact per-spectrum noise estimation as not stated, and those set what "5 sigma" means. Document the
  filter you apply, and estimate the noise after smoothing at each kernel scale, accounting for channel
  correlations (Hanning smoothing, kernel overlap) (recommendation).
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
| Continuum normalization | divide by continuum of the line's SPW | same-SPW continuum map, "same band" continuum, continuum from line fit | 3 | 2018A&A...617A..54L, 2019A&A...622A..26G, 2025ApJ...990...66K |
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
  absorption variability over two years (2020MNRAS.496..364R). Its card flags how the 2016 and 2018 data were
  matched in resolution as not stated: before calling a difference variability, match angular and spectral
  resolution and use the same extraction region and continuum definition at both epochs.
- Chose the emission/absorption mask by minimizing reduced chi2 of the residual baseline (2019MNRAS.485..229R).
- Lens models: deviance information criterion, negative-bowl check at >= 10% of peak, mock point sources across
  the source plane recovered to about 25% (2020ApJ...905...85S).
- Blind search: rejected edge, Galactic, artifact and atmospheric candidates before accepting absorbers
  (2019MNRAS.490.1220K).
- Compared absorber kinematics with the host disk rotation curve to place the gas (2016ApJ...820L..39N).

What a careful referee adds (general practice, not shown in the pack):
- Overlay the bandpass calibrator spectrum and the atmospheric transmission model at the line frequency.
- Show that the absorption overlaps the background continuum and survives changes in imaging and extraction
  (region size, uv-plane versus image-plane). Normalized absorption may legitimately vary across a resolved
  background, as in the clumpy OH reconstruction of 2020ApJ...905...85S.
- Where the line bottom approaches zero or flattens, quote tau as a lower limit; do not read residual flux as
  f_c < 1 without independent saturation evidence (step 6).
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

# Dust properties across the CO snowline in the HD 163296 disk from ALMA and VLA observations

`2016A&A...588A.112G` | Astronomy and Astrophysics 2016 | first author: Guidi, G. | arXiv: 1601.07542 | DOI: 10.1051/0004-6361/201527516

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: Does grain growth vary radially in the HD 163296 disk, and is there evidence of enhanced growth or dust structure across the CO snowline (~90 AU)?  
  > "Our goal is to study grain growth in the well-studied disk of the young, intermediate mass star HD 163296 where dust processing has already been observed, and to look for evidence of growth by ice condensation across the CO snowline" (abstract)
- Target **HD 163296 (MWC 275)**: coordinates Hipparcos J1991.25: 17:56:21.293, -21:57:21.527  
  > "a bright and isolated object at a distance of $122^{+17}_{-13}$ parsec" (Introduction); "We use 44$\degree$ for the disk inclination and 133$\degree$ for the disk position angle" (3.1 Continuum maps); z/distance 122 (+17/-13) pc  
  > "a bright and isolated object at a distance of $122^{+17}_{-13}$ parsec" (Introduction); "We use 44$\degree$ for the disk inclination and 133$\degree$ for the disk position angle" (3.1 Continuum maps); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.000010.SV
- bands: ALMA Band 6 and Band 7; VLA Ka (and C) band  
  > "ALMA B7 | 0.85 | 352.9" (Table 1)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: ALMA (19-21 antennas) and VLA  
  > "using a set of configurations comprising 20, 21 and 19 antennas, respectively" (2.1 ALMA Observations)
- configurations: _not stated_
- baselines: Band 6: 20 to 400 m  
  > "the baselines ranged from 20 to 400 meters, corresponding to spatial scales of 1600 AU to 80 AU" (2.1 ALMA Observations)
- angular resolution: B7 0.57x0.37 arcsec; B6 0.74x0.60 arcsec  
  > "0.57''\times0.37''" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: rms 0.18 mJy/beam (B7), 0.37 mJy/beam (B6)  
  > "a rms of 0.18 mJy/beam" (2.1 ALMA Observations)
- time on source: Band 6: 1.4 h; Band 7: 2.3 h  
  > "The total integration time was 3.14 hours (1.4 hours on the science source)" (2.1 ALMA Observations); "with 2.3 hours on the science target" (2.1 ALMA Observations)
- observing dates: Band 6: 2012 June 9, 23, July 7; Band 7: 2012 June 9, 11, 22; VLA Ka 2011 May-June  
  > "Band 6 observations were performed on 2012 June 9, June 23, and July 7" (2.1 ALMA Observations)
- pi or archival as stated: ALMA Science Verification data  
  > "were part of the ALMA Science Verification Program" (2.1 ALMA Observations)
- Line: DCO+ 5-4 (360.160 GHz)
- Other facility **VLA (Disks@EVLA, AC982)**: Ka-band 30.5/37.5 GHz continuum and C-band  
  > "as part of the Disks@EVLA project (AC982) in 2011 May and June" (2.2 VLA Observations)
- External data: CO snowline at 90 AU from N2H+ emission  
  > "located very close to the CO snowline at 90 AU as measured by who resolved the N$_2$H$^+$ emission in this disk with ALMA" (5.2) [from Qi et al. 2015]
- External data: Ks-band polarized light ring  
  > "An analogous excess ring was found in the images of scattered light from HD 163296 taken with VLT/NACO" (5.2) [from Garufi et al. 2014]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.1.0  
  > "Data calibration was performed using version 4.1.0 of the Common Astronomy Software Application (CASA)" (2.1 ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: B6: Juno, Neptune, Mars; B7: Juno, Neptune  
  > "The flux density calibrator for the three execution blocks were Juno, Neptune and Mars respectively" (2.1 ALMA Observations)
- flux scale uncertainty: 10% calibration error  
  > "We include a calibration error of 10% in the measurements of the flux densities." (3.1 Continuum maps)
- self calibration: applied using line-free channels (Band 6)  
  > "self calibration was applied making use of the line-free channels" (2.1 ALMA Observations)

### Imaging

- task: CLEAN  
  > "obtained with the task CLEAN applying a robust weighting with Briggs parameter 0.5" (2.1 ALMA Observations)
- deconvolver: _not stated_
- weighting robust: Band 7: Briggs robust 0.5; Band 6 robust (value not given)  
  > "obtained with the task CLEAN applying a robust weighting with Briggs parameter 0.5" (2.1 ALMA Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: matched circular beams 0.5" (B7-VLA) and 0.6" (B7-B6)  
  > "with a circular beam of 0.5$^{\prime\prime}$" (3.6 Spectral index profiles)
- final beam: B7 0.57x0.37; B6 0.74x0.60  
  > "achieving a synthesized beam of $0.57"\times 0.37"$" (2.1 ALMA Observations)
- final rms: 0.18 mJy/beam B7; 0.37 B6  
  > "a rms of 0.18 mJy/beam" (2.1 ALMA Observations)

### Inherited from earlier work

- Visibility fitting scheme for two-layer disk MCMC  
  > "using the fitting scheme described by to which we refer for the analysis details" (4 Modeling results) [from not given in text (likely Tazzari et al.)]
- Dust composition fractions adapted from earlier work  
  > "given by the following fractional abundances adapted from : 5.4% astronomical silicates" (4 Modeling results) [from not given in text]

### Not stated but needed to reproduce (our reading)

- Band 6 robust value and CLEAN threshold/masks
- Line-free channel selection and self-calibration solints
- Flux scale handling for Band 6/7
- MCMC priors, burn-in and convergence
- Dust opacity data/optical constants
- Model stellar parameters and temperature setup details
- Polynomial fit radial range and binning

## Analysis recipe

1. **Image continuum**: CLEAN of line-free channels of ALMA B6/B7, VLA images  
  > "Imaging of the continuum emission of HD 163296 was performed excluding the above-mentioned lines" (2.1 ALMA Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit radial excess along major axis**: 3rd-degree polynomial plus Gaussian fit to B7 major axis profile  
  > "we fitted a combination of a 3rd degree polynomial plus a gaussian curve to our flux density profile" (3.4)
   - parameter: inclination 44 deg, PA 133 deg  
  > "We use 44$\degree$ for the disk inclination and 133$\degree$ for the disk position angle" (3.1 Continuum maps)
   - fitting: least-squares  
  > "Best fit parameters, with associated standard deviations, obtained from the least-square interpolation of the data along the major axis using a 3rd degree polynomial" (Excess emission at 850 $\mu$m)
   - validation: compared with direct visibility fit  
  > "An independent analysis of this excess, obtained from modeling the visibilities directly, is shown in Section 4." (3.4)
3. **Spectral index and beta profiles**: Matched-beam images, ratio of intensities; beta from alpha-2 or with Planck correction using model T(r)  
  > "the power-law dependence of the dust opacity, $\beta$, can be derived as $\beta = \alpha - 2$" (3.6 Spectral index profiles)
   - parameter: VLA maps with 0.3 mJy point source subtracted  
  > "produced subtracting a point source at the centre of the system with a flux density of 0.3 mJy from the calibrated visibilities" (3.6 Spectral index profiles)
   - assumption: optically thin, 10% calibration error per flux  
  > "we used a 10% calibration error for each flux" (3.6 Spectral index profiles)
   - fitting: _not stated_
   - validation: optical depth tau estimated from Tb/T_model  
  > "estimate the optical depth $\tau$ of the emission as $\tau \simeq -ln(1-T_b/T_{model})$" (3.6 Spectral index profiles)
4. **Visibility-domain two-layer disk fit**: two-layer model with and without Gaussian ring, Mie opacities, fit to 850um visibilities  
  > "we have performed a direct fit of the interferometric data (i.e., the visibilities)" (4 Modeling results)
   - software: affine-invariant MCMC ensemble sampler
   - parameter: R0=10 AU, 500 chains  
  > "obtained running a MCMC with 500 chains" (4 Modeling results)
   - assumption: dust-to-gas 0.01; q=3 midplane amax=0.8(R/10AU)^-1.025 mm  
  > "we assume a constant dust to gas mass ratio $\zeta = 0.01$" (4 Modeling results)
   - fitting: Bayesian affine-invariant MCMC; priors not stated  
  > "The modeling methodology is based on a Bayesian approach and employs an affine-invariant Markov Chain Monte Carlo (MCMC) ensemble sampler" (4 Modeling results)
   - validation: chi2_red compared 1.853 vs 1.830  
  > "The best-fit model ($\chi^2_{\mathrm{red}}=$1.830)" (Modeling results)

## Software

- **CASA** 4.1.0: ALMA calibration, CLEAN imaging, VLA reduction  
  > "Data calibration was performed using version 4.1.0 of the Common Astronomy Software Application (CASA)" (2.1 ALMA Observations)
- **VLA Calibration Pipeline (modified)** : VLA Ka-band calibration  
  > "using a modified version of the VLA Calibration Pipeline" (2.2 VLA Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Band 7 integrated flux density | 2.13 | 0.02 | Jy | 1 | $F_{850\mu m}=2.13\pm 0.02$ Jy |
| Band 6 flux density | 0.59 | 0.06 | Jy | 1 | $F_{1.3mm}=0.59\pm 0.06$ Jy |
| Excess Gaussian center | 106 | 4 | AU | 2 | centered at about (106 $\pm$ 4) AU |
| Excess FWHM | 71 | 18 | AU | 2 | full width at half maximum (FWHM) of (71 $\pm$ 18) AU |
| Ring peak radius from visibility fit | 96 | 1 | AU | 4 | ${R_p=(96\pm 1)\,}$ AU |
| Ring FWHM from visibility fit | 58 | 3 | AU | 4 | FWHM=$2\sqrt{2\ln 2}\cdot \sigma_p\approx (58 \pm 3)$ AU |
| Free-free power-law index | -0.19 | 0.11 | dimensionless | 0 | $F_\nu\propto\nu^{-0.19\pm 0.11}$ |

## Qualitative findings

- Beta decreases toward center to <=1, indicating large grains (>=1 mm) inside ~100 AU; no beta feature at snowline at 70 AU resolution  
  > "the dust opacity spectral index varies with radius and decreases towards the center to values $\leq$1" (Summary)

## Claim tuples

- H: Grain sizes vary radially in the disk | E: Spectral index profiles from matched ALMA/VLA images | R: alpha rises from ~2.5 to ~3.5 at 150 AU; beta<1 beyond 50 AU | F: Large grains inside, ISM-like grains outside | **supported**
- H: A continuum excess exists near the CO snowline | E: Major-axis profile fit and visibility modeling at 850 um | R: Gaussian ring at ~96-106 AU, unresolved | F: Excess confirmed and not purely a surface feature | **supported**
- H: Grain growth is locally enhanced at the CO snowline | E: beta(r) across snowline | R: no features at ~0.6" resolution | F: Cannot be concluded; smooth alternative equally consistent | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Dust trapping in zonal flows or vortices as alternative to snowline origin  
  > "particles are trapped by zonal flows or by vortices" (5.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Band 6 and VLA data lack resolution/sensitivity to probe spectral index at the excess  
  > "The lack of sensitivity or angular resolution in the VLA and ALMA Band 6 data do not allow us to probe the spectral index of the excess detected in Band 7." (5.2)
- Caveat (inferred, ours): Excess width depends on pixel size and tolerance choices
- Caveat (inferred, ours): DCO+ result tentative at low S/N
- Caveat (inferred, ours): Rayleigh-Jeans and optically thin assumptions marginal in outer Band 7
- Caveat (inferred, ours): Opacity model dependent grain sizes

## Reproducibility

- Data public (paper): ALMA Science Verification data publicly available  
  > "The ALMA Science Verification data can be found at:" (footnote 1)
- Products in archive: _not stated_
- Missing: Fit priors and MCMC configuration
- Missing: Exact imaging parameters for B6, VLA
- Missing: Model code/opacity inputs
- Data volume (inferred): ~tens of GB (ALMA SV B6/B7 plus VLA)
- Score (inferred): 5/5, Public data and main steps described, but modeling inherited and key imaging/fit settings missing.
- Rediscovery candidate: no, Modeling relies on unreleased code and inherited details; VLA data need separate retrieval.

## Links

- Method: Tazzari et al. 2015 (cite: Tazzari2015) (likely visibility-fitting scheme (inferred))
- Companion: Qi et al. 2015 (CO snowline from N2H+)
- Companion: Garufi et al. 2014 (Ks-band polarized ring)
- Related: Disks@EVLA
- Related: ALMA Science Verification

## Checks

```json
{
 "quotes": 61,
 "quotes_ok": 61,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.0.000010.SV"
 ],
 "obscore_codes_not_in_card": [
  "2011.0.00001.SV"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 45,
  "rate": 0.643
 },
 "evidence_ok": true
}
```

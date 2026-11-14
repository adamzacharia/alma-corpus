# GRB 110715A: the peculiar multiwavelength evolution of the first afterglow detected by ALMA

`2017MNRAS.464.4624S` | Monthly Notices of the Royal Astronomical Society 2017 | first author: Sánchez-Ramírez, R. | arXiv: 1610.01844 | DOI: 10.1093/mnras/stw2608

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: transients
- Question: What are the physical parameters of the jet and environment of GRB 110715A, constrained by broadband afterglow modelling of 17-band follow-up including the first ALMA GRB afterglow observation?  
  > "The broadband afterglow emission is modelled with synchrotron radiation using a numerical algorithm and we determine the best fit parameters using Bayesian inference" (abstract)
- Target **GRB 110715A**: coordinates RA(J2000) = 15h 50m 44.05s, Dec.(J2000) = -46d 14' 06.5'' (ALMA centroid)  
  > "The centroid of the afterglow is located at RA(J2000) = 15$h$ 50$m$ 44.05$s$ and Dec.(J2000) = -46$^{\circ}$ 14$\ensuremath{'}$ 06.5$''$" (Submm afterglow observations); "The spectrum shows weak absorption features at a redshift $z$ = 0.8225" (abstract); z/distance z = 0.8225  
  > "The centroid of the afterglow is located at RA(J2000) = 15$h$ 50$m$ 44.05$s$ and Dec.(J2000) = -46$^{\circ}$ 14$\ensuremath{'}$ 06.5$''$" (Submm afterglow observations); "The spectrum shows weak absorption features at a redshift $z$ = 0.8225" (abstract); distance from X-shooter absorption lines  
  > "The centroid of the afterglow is located at RA(J2000) = 15$h$ 50$m$ 44.05$s$ and Dec.(J2000) = -46$^{\circ}$ 14$\ensuremath{'}$ 06.5$''$" (Submm afterglow observations); "The spectrum shows weak absorption features at a redshift $z$ = 0.8225" (abstract)

## Data provenance

- ALMA projects: 2011.0.00001.E
- bands: 345 GHz  
  > "yielding a detection with a flux density of 4.9 $\pm$ 0.6 mJy at 345 GHz" (Submm afterglow observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: only 7 antennas  
  > "they were carried out making use of only 7 antennas during 25 mins on source" (Submm afterglow observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.3" x 0.1" at PA 76 deg  
  > "with a synthesized beam size of 0.3$''$ $\times$ 0.1$''$ at a position angle of 76 degrees" (Submm afterglow observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 25 mins  
  > "they were carried out making use of only 7 antennas during 25 mins on source" (Submm afterglow observations)
- observing dates: July 19 2011, 02:50 UT (3.57 days after burst)  
  > "The ALMA observations began on July 19 at 02:50 UT (3.57 days after the burst)" (Submm afterglow observations)
- pi or archival as stated: _not stated_
- Other facility **Swift (BAT, XRT, UVOT)**: gamma-ray, X-ray and UV/optical light curves  
  > "The *Swift* Ultra-Violet/Optical Telescope (cite: 2005SSRv..120...95R) began settled observations of the field of GRB 110715A 100$s$ after the trigger" (UVOT imaging)
- Other facility **GROND (MPG 2.2m)**: optical/NIR photometry  
  > "We obtained follow-up observations of the optical/NIR afterglow of GRB 110715A with the seven-channel imager GROND" (GROND imaging)
- Other facility **APEX/LABOCA**: 345 GHz submm detection  
  > "Using these observations we discovered a bright submm counterpart at 10.4 $\pm$ 2.4 mJy" (Submm afterglow observations)
- Other facility **ATCA**: radio 5-44 GHz light curves  
  > "This GRB was monitored at 44, 18, 9, and 5 GHz for up to 75 days post-burst" (Radio afterglow observations)
- Other facility **VLT/X-shooter and FORS2**: afterglow spectrum and host imaging  
  > "An object is detected close to the afterglow position at a magnitude of 26.40 $\pm$ 0.36 mag." (Host galaxy imaging)
- External data: Galactic reddening E(B-V) = 0.52 mag  
  > "later $E(B-V)$ = 0.52 mag following (cite: 2011ApJ...737..103S). We adopted the latest value." (UV/Optical/NIR afterglow observations) [from (cite: 2011ApJ...737..103S)]
- External data: Composite GRB afterglow spectrum equivalent widths  
  > "Equivalents widths measured on the composite GRB afterglow spectrum (cite: 2011ApJ...727...73C)." (Table 4) [from (cite: 2011ApJ...727...73C)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Afterglow numerical model  
  > "The afterglow emission was modeled with the numerical code of (cite: 2006ApJ...647.1238J)." (Model and fitting description) [from (cite: 2006ApJ...647.1238J)]
- Line strength parameter prescription  
  > "Following the prescription of (cite: 2012A&A...548A..11D), we obtain a line strength parameter for GRB 110715A of LSP = -0.83 $\pm$ 0.47" (Spectral absorption lines of the optical afterglow) [from (cite: 2012A&A...548A..11D)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, CASA version, flux calibrator and imaging details
- How the 4.9 mJy ALMA flux was measured (inherited from De Ugarte Postigo 2012)
- Full photometric table is only online
- MultiNest settings (live points, tolerance)
- Likelihood form and systematic error treatment

## Analysis recipe

1. **Fit broadband afterglow with numerical forward-shock model**: Numerical top-hat jet forward-shock model with energy injection or wind termination shock, fitted with Bayesian inference to X-ray, UV/optical/NIR, submm and radio data  
  > "The best fit model parameters are found using Bayesian inference using the MultiNest tool (cite: 2009MNRAS.398.1601F)." (Model and fitting description)
   - software: MultiNest
   - parameter: Flat (uniform/log-uniform) priors on all parameters except Galactic reddening (Gaussian, mu=0.56, sigma=0.04)  
  > "(c) $\mu$ = 0.56, $\sigma$ = 0.04" (Table 5)
   - parameter: UVOT UV filters and u band excluded in best fits  
  > "We excluded the upper limits from the UV filters of UVOT as well as observations using its $u$-band filter" (Model and fitting description)
   - assumption: SMC-like host extinction curve  
  > "we also determine the host dust extinction in the fit, which we assume follows an SMC-like extinction curve" (Model and fitting description)
   - fitting: MultiNest Bayesian inference; models CM, WM, TS compared via evidence and reduced chi2  
  > "We chose three different types of models that we expect have this behaviour" (Model and fitting description)
   - validation: Grid of 36 fits with different data cuts; none statistically good  
  > "However, none of them is either a statistically good fit or can fully explain the temporary flux increase at $\sim$0.3 days." (The best fit)

## Software

- **MultiNest** : Bayesian parameter estimation  
  > "The best fit model parameters are found using Bayesian inference using the MultiNest tool (cite: 2009MNRAS.398.1601F)." (Model and fitting description)
- **MIRIAD** : ATCA data reduction  
  > "The data were reduced using standard procedures in MIRIAD (cite: 1995ASPC...77..433S)." (Radio afterglow observations)
- **HEADAS** 6.10: UVOT analysis pipeline  
  > "The analysis pipeline used software HEADAS 6.10 and UVOT calibration 20111031." (UVOT imaging)
- **SExtractor** : background modelling in GROND images  
  > "we used SExtractor (cite: 1996A&AS..117..393B) for background modeling" (GROND imaging)
- **X-shooter pipeline** 2.0.0: spectral reduction  
  > "We processed the spectra using version 2.0.0 of the X-shooter data reduction pipeline" (Optical/nIR afterglow spectra)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA 345 GHz flux density | 4.9 | 0.6 | mJy | 0 | yielding a detection with a flux density of 4.9 $\pm$ 0.6 mJy at 345 GHz |
| Redshift | 0.8225 | 0.0001 | dimensionless | 0 | at a common redshift of 0.8225 $\pm$ 0.0001 |
| Host offset from ALMA position | 0.21 (1.56 kpc) | 0.03 arcsec; 0.19 kpc | arcsec | 0 | The centroid is offset by 0.21 $\pm$ 0.03 $''$ with respect to the ALMA position, which at the redshift of GRB 110715A corresponds to 1.56 $\pm$ 0.19 kpc. |
| TS model electron index p | 1.8148 | 0.0041 | dimensionless | 1 | $1.8148 \pm 0.0041$ |

## Qualitative findings

- The TS (wind termination shock) model is the preferred, but none of the models gives a statistically acceptable fit  
  > "none of the models is able to get a statistically acceptable fit" (Conclusions)

## Claim tuples

- H: Can forward-shock models with energy injection or termination shock explain the 17-band afterglow? | E: MultiNest fits of CM, WM and TS models to broadband data | R: reduced chi2 of 5.5-7.3; TS best | F: Models describe the general behaviour but not all data | **refuted**
- H: Is the host a low-ionisation, low-column dwarf environment? | E: X-shooter absorption line analysis and deep FORS2 imaging | R: LSP = -0.83, M = -18.2 mag host | F: Small faint dwarf host | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Reverse shock and double-jet models tested; neither improves fit  
  > "We therefore conclude that a double jet model is not appropriate for this case." (Appendix)
- How they decided it was enough: _not stated_
- Limitation (authors): Poor temporal sampling limits constraints  
  > "This shows the need for better broadband sampling and more complex models" (Conclusions)
- Caveat (inferred, ours): ALMA data processing is not described
- Caveat (inferred, ours): Chi2 values are huge so posterior uncertainties are unrealistically small
- Caveat (inferred, ours): Forward-shock only model

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA flux extraction details
- Missing: Full light-curve table only online
- Missing: Afterglow code of Jóhannesson 2006 not stated as public
- Data volume (inferred): <10 GB for ALMA; other data small
- Score (inferred): 3/5, Light-curve modelling is described, but ALMA processing is deferred and model code is not released.
- Rediscovery candidate: no, The ALMA part is minor and the recipe is incomplete.

## Links

- Method: (cite: 2006ApJ...647.1238J) (afterglow numerical code)
- Method: (cite: 2009MNRAS.398.1601F) (MultiNest)
- Companion: (cite: 2012A&A...538A..44D) (ALMA/submm GRB afterglow sample and ALMA detection)
- Related: APEX 087.F-9301(A)
- Related: VLT 087.A-0055(C)

## Checks

```json
{
 "quotes": 43,
 "quotes_ok": 43,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 32,
  "rate": 0.485
 },
 "evidence_ok": true
}
```

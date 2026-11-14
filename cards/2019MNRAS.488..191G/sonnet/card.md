# ALMA observations of A0620-00: fresh clues on the nature of quiescent black hole X-ray binary jets

`2019MNRAS.488..191G` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Gallo, Elena | arXiv: 1906.04299 | DOI: 10.1093/mnras/stz1634

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: stellar_physics, milky_way_ism
- Question: Is the sub-mm/mm spectrum of the quiescent black hole X-ray binary A0620-00 optically thin, or is its jet emission highly variable, and what does this imply for the jet spectral extent?  
  > "These results suggest either an optically thin sub-mm synchrotron spectrum, or highly variable sub-mm jet emission on month timescales." (abstract)
- Target **A0620-00**: coordinates _not stated_; z/distance 1.06±0.12 kpc  
  > "At $L_{\rm X}$$\simeq 10^{-9}$ $L_{\rm Edd}$, and $1.06\pm0.12$ kpc distance (cite: cantrell10)" (Introduction); distance from Cantrell et al. 2010  
  > "At $L_{\rm X}$$\simeq 10^{-9}$ $L_{\rm Edd}$, and $1.06\pm0.12$ kpc distance (cite: cantrell10)" (Introduction)

## Data provenance

- ALMA projects: 2016.1.00773.S
- bands: Band 3 (98 GHz) and Band 6 (233 GHz) continuum  
  > "Continuum observations in Band 3 at 98 GHz and Band 6 at 233 GHz were taken" (2.1 ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: Band 3: 15-1039 m (46 antennas); Band 6: 15-491 m (48 antennas)  
  > "with 46 antennas, with baselines spanning the range 15 m to 1039 m" (2.1 ALMA)
- angular resolution: Band 3 1.25"x1.10" PA 89.0 deg; Band 6 0.86"x0.77" PA -71.3 deg  
  > "For the Band 6 data the synthesized beam is $0.86\ensuremath{''} \times 0.77\ensuremath{''}$ at a position angle of $-71.3\ensuremath{^\circ}$" (2.1 ALMA)
- max recoverable scale: _not stated_
- sensitivity: rms 6.9 uJy/beam (Band 3); 8.2 uJy/beam (Band 6)  
  > "with an rms noise of $8.2~\mu{\rm Jy~beam}^{-1}$" (2.1 ALMA)
- time on source: Band 3: 1.1 hr; Band 6: 2.15 hr  
  > "for 2.15 hr" (2.1 ALMA)
- observing dates: Band 3: 12 and 14 Nov 2016; Band 6: 20 and 21 Dec 2016  
  > "The Band 6 data were taken on the 20th and 21st December 2016" (2.1 ALMA)
- pi or archival as stated: PI Gallo, project 2016.1.00773.S  
  > "(P.I. Gallo)" (2.1 ALMA)
- Other facility **VLA**: X-band 8-12 GHz radio flux densities, 13 observations Sep 2017-Jan 2018 (program 17B-233)  
  > "We measured flux densities of $12.9\pm1.5$ and $14.2 \pm 1.8$ $\mu$Jy bm$^{-1}$ at 8.9 and 10.8 GHz, respectively." (2.2 VLA)
- Other facility **SMARTS 1.3 m (ANDICAM)**: optical/NIR photometry, simultaneous with ALMA Band 6  
  > "A0620–00 is routinely monitored at optical and near-IR (NIR) frequencies with the dual-channel imager ANDICAM on the SMARTS 1.3 m telescope" (2.3 SMARTS)
- External data: Earlier SEDs (2003-2005 VLA, SMARTS, Chandra, Spitzer; 2013 VLA and SMARTS) for comparison  
  > "red open triangles correspond to the 2003-2005 campaign reported by Gallo et al. (2007; VLA, SMARTS and *Chandra*)" (3.1) [from Gallo et al. 2007; Dincer et al. 2018 (cite: dincer18); Muno (cite: muno)]
- External data: Color excess E(B-V)=0.30±0.05  
  > "the color excess $E(B-V)=0.30\pm 0.05$ (Cantrell et al. 2010)" (2.3 SMARTS) [from Cantrell et al. 2010]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline script provided by ALMA staff, run in CASA  
  > "The data were calibrated using $\texttt{CASA}$ (cite: McMullin_ea_2007) using the pipeline script provided by ALMA staff." (2.1 ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0750+1231 (flux), J0641-0320 (phase)  
  > "the quasars J0750+1231 and J0641-0320 were used for flux and phase calibration, respectively" (2.1 ALMA)
- flux scale uncertainty: 5% Band 3, 10% Band 6  
  > "Absolute flux calibration adds a systematic uncertainties of 5 per cent for Band 3 and 10 per cent for Band 6" (2.1 ALMA)
- self calibration: none; insufficient signal  
  > "there was insufficient signal to perform self-calibration" (2.1 ALMA)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The data were imaged using natural weighting to maximize sensitivity" (2.1 ALMA)
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
- final beam: 1.25"x1.10" (Band 3); 0.86"x0.77" (Band 6)  
  > "achieving a beam size of $1.25\ensuremath{''} \times 1.10\ensuremath{''}$" (2.1 ALMA)
- final rms: 6.9 and 8.2 uJy/beam  
  > "a root mean square (rms) noise of $6.9~\mu{\rm Jy~beam}^{-1}$" (2.1 ALMA)

### Inherited from earlier work

- SMARTS data reduction follows standard procedures  
  > "Data presented here were reduced following standard procedures described in (cite: dincer18)" (2.3 SMARTS) [from (cite: dincer18)]

### Not stated but needed to reproduce (our reading)

- CASA version used for ALMA pipeline
- Image size, cell size, and tclean parameters
- Target coordinates
- emcee priors, walkers, steps
- Spectral window frequencies and bandwidths
- Whether archive pipeline products were used as delivered

## Analysis recipe

1. **calibrate and image ALMA continuum**: ALMA pipeline calibration, no self-cal, natural-weighted imaging  
  > "The data were imaged using natural weighting to maximize sensitivity" (2.1 ALMA)
   - software: CASA
   - fitting: _not stated_
   - validation: Phase decorrelation test: reran pipeline treating three phase-calibrator scans as target; peak within 5%  
  > "This confirms that phase decorrelation as a function of time was $<$5 per cent during the Band 6 observations." (2.1 ALMA)
2. **measure integrated flux densities**: Fit 2D Gaussian with beam properties to continuum images, flux and position free  
  > "The integrated flux densities were measured by fitting a 2D Gaussian with the same properties as the synthesized beam to the continuum images" (2.1 ALMA)
   - software: emcee
   - fitting: Affine-invariant MCMC ensemble sampler; 16th-84th percentiles for uncertainty  
  > "Posterior distributions were sampled using an affine invariant Markov chain Monte Carlo ensemble sampler" (2.1 ALMA)
   - validation: _not stated_
3. **compute spectral index and compare with multiwavelength SEDs**: Two-point 98-233 GHz index; compare with VLA, SMARTS and earlier campaigns  
  > "with $\alpha={-0.56\pm 0.47}$ (3$\sigma$ C.L.) over the 98–233 GHz frequency interval" (3.1)
   - assumption: Distance 1.06 kpc; E(B-V)=0.30  
  > "the color excess $E(B-V)=0.30\pm 0.05$ (Cantrell et al. 2010)" (2.3 SMARTS)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** v5.1.1 for VLA; ALMA version not stated: ALMA pipeline calibration and VLA processing  
  > "Data were processed using CASA v5.1.1" (2.2 VLA)
- **emcee** : MCMC flux fitting  
  > "`emcee` (cite: Foreman-Mackey_ea_2013)" (2.1 ALMA)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Band 3 (98 GHz) flux density | 44 | 7 | uJy | 2 | yielding a robust detection in Band 3, at $44 \pm 7~\mu{\rm Jy}$ |
| Band 6 (233 GHz) flux density | 20 | 8 | uJy | 2 | a marginally significant detection in band 6, at $20 \pm 8~\mu{\rm Jy}$ |
| ALMA spectral index 98-233 GHz | -0.56 | 0.47 (3 sigma) | dimensionless | 3 | $\alpha={-0.56\pm 0.47}$ (3$\sigma$ C.L.) |
| VLA flux density at 8.9 GHz | 12.9 | 1.5 | uJy/beam | 0 | $12.9\pm1.5$ and $14.2 \pm 1.8$ $\mu$Jy bm$^{-1}$ at 8.9 and 10.8 GHz |

## Qualitative findings

- At ALMA epochs A0620-00 was less active in optical-IR than during earlier campaigns suggesting a flat-spectrum jet  
  > "A0620–00 was somewhat less active than during other published multi-wavelength campaigns" (3.1)

## Claim tuples

- H: Is the mm spectrum optically thin or is the jet variable? | E: Dual-band ALMA continuum 40 days apart with SMARTS and VLA context | R: 44±7 uJy at 98 GHz, 20±8 uJy at 233 GHz | F: Either an optically thin spectrum or factor >=2 variability over a month; variability more likely | **partially**
- H: Do BH XRB jets vary strongly across Eddington ratios? | E: Combine ALMA with results from V404 Cyg and Cyg X-1 | R: High variability in all | F: Consistent with internal shock model | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Observations not simultaneous across radio, mm and IR; no firm conclusions  
  > "no firm conclusions can be drawn based upon on the dual band ALMA observations" (3.2)
- Caveat (inferred, ours): Marginal Band 6 detection (2.5 sigma)
- Caveat (inferred, ours): Non-simultaneous Band 3 and 6 limits spectral inference
- Caveat (inferred, ours): Interpretation largely speculative

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters beyond natural weighting
- Missing: Coordinates and CASA version
- Missing: MCMC setup
- Data volume (inferred): ~20-50 GB raw
- Score (inferred): 3/5, Public project code and simple recipe, but imaging and fit details are sparse.
- Rediscovery candidate: no, Recipe incomplete and the main results are two faint flux densities with limited detail.

## Links

- Companion: Dincer et al. 2018 (cite: dincer18) (previous SED campaign and SMARTS reduction)
- Related: VLA 17B-233

## Checks

```json
{
 "quotes": 40,
 "quotes_ok": 40,
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
  "facts": 62,
  "stated": 32,
  "rate": 0.516
 },
 "evidence_ok": true
}
```

# JWST detection of a supernova associated with GRB 221009A without an r-process signature

`2024NatAs...8..774B` | Nature Astronomy 2024 | first author: Blanchard, Peter K. | arXiv: 2308.14197 | DOI: 10.1038/s41550-024-02237-4

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: transients, star_formation
- Question: Is there a supernova associated with GRB 221009A, does it show r-process enrichment, and what is the host galaxy environment (JWST NIRSpec/NIRCam; ALMA used to constrain the afterglow)?  
  > "These observations provide the first clear detection of a SN associated with this extreme event and enable the first search for $r$-process emission in a nebular phase spectrum of a GRB-SN." (Introduction)
- Target **GRB 221009A**: coordinates RA 19h13m03.50s, Dec +19d46m24.3s  
  > "on 9 October 2022 at a relatively nearby redshift of $z=0.151$ (cite: Malesani2023)" (Introduction); "a position of R.A.$=$19h13m03.50s and decl.$=$19$^\circ$46$^\prime$24.3$^{\prime\prime}$ with an uncertainty of $0.1^{\prime\prime}$ in each coordinate" (5.4 ALMA Observations); z/distance z = 0.151  
  > "on 9 October 2022 at a relatively nearby redshift of $z=0.151$ (cite: Malesani2023)" (Introduction); "a position of R.A.$=$19h13m03.50s and decl.$=$19$^\circ$46$^\prime$24.3$^{\prime\prime}$ with an uncertainty of $0.1^{\prime\prime}$ in each coordinate" (5.4 ALMA Observations); distance from Malesani et al. 2023  
  > "on 9 October 2022 at a relatively nearby redshift of $z=0.151$ (cite: Malesani2023)" (Introduction); "a position of R.A.$=$19h13m03.50s and decl.$=$19$^\circ$46$^\prime$24.3$^{\prime\prime}$ with an uncertainty of $0.1^{\prime\prime}$ in each coordinate" (5.4 ALMA Observations)

## Data provenance

- ALMA projects: 2022.1.01433.T
- bands: two 4 GHz base-bands centered at 91.5 and 103.5 GHz (mean 97.5 GHz)  
  > "Both observations utilized two 4 GHz wide base-bands centered at 91.5 and 103.5 GHz, respectively" (5.4 ALMA Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 01 March 2023 and 11 April 2023  
  > "we obtained two additional epochs with the same program on 01 March 2023 at a mean time of 15:41 UT and on 11 April 2023 at a mean time of 07:55 UT" (5.4 ALMA Observations)
- pi or archival as stated: Program PI Laskar; the authors obtained two additional epochs  
  > "through program 2022.1.01433.T (PI: Laskar)" (5.4 ALMA Observations)
- Other facility **JWST NIRSpec**: Late-time G140M/G235M spectrum (program 2784) and archival PRISM spectrum (program 2782)  
  > "Spectra were taken with the S200A1 fixed slit and the medium resolution gratings G140M/F100LP and G235M/F170LP, yielding wavelength coverage from $\sim1-3$ $\mu$m." (5.2.1 Late-Time NIRSpec Observations)
- Other facility **JWST NIRCam**: Imaging in F115W, F200W, F277W, F444W  
  > "We obtain imaging of GRB 221009A with the Near Infrared Camera (NIRCam) using the F115W, F200W, F277W, and F444W filters on 22 April 2023" (5.1 Imaging Observations and Photometry)
- Other facility **JWST MIRI**: Archival LRS spectrum from program 2782  
  > "The MIRI spectrum was taken in the low-resolution spectroscopy (LRS) mode with the P750L disperser." (5.2.4 Archival NIRSpec/MIRI Observations)
- Other facility **Swift/XRT**: X-ray afterglow flux density at the NIRSpec epoch  
  > "We downloaded the count-rate light curve of the X-ray afterglow of GRB 221009A from the *Swift*/XRT website" (5.5 Swift/XRT Observations)
- External data: Previous ALMA 97.5 GHz afterglow measurements and XRT spectral parameters (N_H, photon index)  
  > "Using the spectral parameters presented in (cite: Laskar2023)" (5.5 Swift/XRT Observations) [from (cite: Laskar2023)]
- External data: SN 1998bw +51 d NIR spectrum used as SN template  
  > "we use the $+51$ day spectrum of SN 1998bw as this is the latest available NIR spectrum of another GRB-SN (cite: Patat2001)" (2.1 Isolating the SN Signal) [from (cite: Patat2001)]
- Simulation/model as data: r-process enriched SN models (MHD and collapsar cases) from Siegel et al. 2019 compared to the spectrum  
  > "we compare our NIRSpec spectrum, with various assumptions about the afterglow contribution, to $r$-process enriched SN models from (cite: siegel2019)" (2.3 No Signs of r-Process Enrichment)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: ALMA: pipeline-processed science-ready data products used  
  > "is clearly detected in the pipeline-processed science-ready data products in the first of the two epochs" (5.4 ALMA Observations)
- flux calibrator: _not stated_
- flux scale uncertainty: 5% systematic flux calibration uncertainty  
  > "(including a 5% systematic flux calibration uncertainty)" (5.4 ALMA Observations)
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

- X-ray spectral parameters (N_H, photon index) used to convert XRT count rate  
  > "Using the spectral parameters presented in (cite: Laskar2023)" (5.5 Swift/XRT Observations) [from (cite: Laskar2023)]

### Not stated but needed to reproduce (our reading)

- ALMA CASA version and pipeline version
- ALMA flux calibrator and imaging parameters (weighting, cell, size)
- imfit region and fitting details
- ALMA array configuration, integration time, and beam

## Analysis recipe

1. **ALMA afterglow photometry**: Point-source flux fit with imfit on pipeline-processed images at two epochs  
  > "We performed photometry using `imfit` in the Common Astronomy Software Applications (CASA; (cite: CASA2022))" (5.4 ALMA Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Extrapolate mm flux to NIRSpec epoch and build ALMA-XRT power law**: Fit decline rate using the previous ALMA point, extrapolate to 194 d, and compute spectral index to the XRT flux  
  > "implying an extrapolated mm-band flux density of $(99\pm23)\,\mu$Jy at the time of the NIRSPEC observations (194 days, observer frame)" (5.4 ALMA Observations)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : imfit photometry of ALMA afterglow  
  > "We performed photometry using `imfit` in the Common Astronomy Software Applications (CASA; (cite: CASA2022))" (5.4 ALMA Observations)
- **emcee** : MCMC fit of early-time spectrum for dust extinction  
  > "using a Markov-chain Monte Carlo sampler implemented in `emcee` (cite: foreman2013emcee)" (5.6 Constraints on Foreground Dust)
- **GALFIT** : host galaxy Sérsic modeling of NIRCam images  
  > "we first model the host galaxy contribution using the galaxy profile fitting code GALFIT (cite: Peng2010)" (5.1 Imaging Observations and Photometry)
- **Prospector** : host galaxy SED fitting  
  > "We use `Prospector` (cite: prospector), a Bayesian galaxy SED-fitting code to simultaneously fit the global host galaxy photometry and spectroscopy." (5.8 Host Galaxy Modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA 97.5 GHz flux density, epoch 1 (143.65 d) | 163 | 22 | uJy | 1 | find a best-fit flux density in the two epochs of $(163\pm22)\,\mu$Jy and $(104\pm23)\,\mu$Jy |
| ALMA 97.5 GHz flux density, epoch 2 (183.78 d) | 104 | 23 | uJy | 1 | find a best-fit flux density in the two epochs of $(163\pm22)\,\mu$Jy and $(104\pm23)\,\mu$Jy |
| mm-band temporal decline index | -1.54 | 0.08 | dimensionless | 2 | $\alpha_{\rm mm}=-1.54\pm0.08$ |
| ALMA-XRT spectral index | 0.63 | 0.03 | dimensionless | 2 | $\beta_{\rm ALMA-XRT}=0.63\pm0.03$ |
| 56Ni mass (with gamma-ray leakage) | 0.09 | not stated | Msun | 0 | we find $M_{\rm Ni}\approx 0.09$ M$_{\odot}$ |

## Qualitative findings

- No r-process signature; the spectrum is well fit by a SN 1998bw-like SN plus a power-law afterglow  
  > "the SN produced a modest amount ($\approx0.09$ M$_\odot$) of radioactive $^{56}$Ni with no obvious signs of $r$-process nucleosynthesis." (Conclusions)

## Claim tuples

- H: A SN accompanies GRB 221009A and the ALMA-XRT power law gives the afterglow | E: Compare the JWST spectrum with the ALMA-XRT power law and with afterglow+SN fits | R: The ALMA-XRT power law falls below the data at NIR wavelengths; the best-fit afterglow+SN 1998bw template fits well | F: A SN is detected, ~30% fainter than SN 1998bw, and the ALMA-XRT power law does not capture the NIR afterglow | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): The afterglow/SN decomposition is uncertain and affects the Ni mass  
  > "Of course, assuming a different afterglow contribution in our spectrum will affect the estimated mass." (2.2)
- Caveat (inferred, ours): ALMA is a minor constraint with only ~5 sigma detections and a large extrapolation uncertainty

## Reproducibility

- Data public (paper): JWST data public on MAST; ALMA program not stated as public  
  > "The JWST data analyzed in this work associated with programs 2784 and 2782 are publicly available on the MAST archive." (Data availability)
- Products in archive: _not stated_
- Missing: ALMA imaging parameters and CASA version
- Missing: extraction region for imfit
- Data volume (inferred): ~ few GB for the two ALMA epochs
- Score (inferred): 3/5, The ALMA part is simple and partly specified, but its details are sparse and the data are under a .T program, so public release is unclear.
- Rediscovery candidate: no, The ALMA recipe is incomplete and the main results rest on JWST data.

## Links

- Companion: (cite: Laskar2023) (Earlier ALMA epochs of the same program)
- Companion: (cite: levanboat) (Early JWST observations of GRB 221009A)

## Checks

```json
{
 "quotes": 37,
 "quotes_ok": 37,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 63,
  "stated": 26,
  "rate": 0.413
 },
 "evidence_ok": true
}
```

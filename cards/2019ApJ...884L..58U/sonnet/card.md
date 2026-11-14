# First Detection of Radio Linear Polarization in a Gamma-Ray Burst Afterglow

`2019ApJ...884L..58U` | The Astrophysical Journal Letters 2019 | first author: Urata, Yuji | arXiv: 1904.08111 | DOI: 10.3847/2041-8213/ab48f3

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: transients
- Question: Is the millimeter-band linear polarization of the GRB 171205A afterglow detectable, and does its low degree imply Faraday depolarization by non-accelerated electrons?  
  > "Here, we report the first detection of radio polarization of a GRB afterglow through observing low-luminosity GRB 171205A, and discuss implications for the Faraday depolarization model." (Introduction)
- Target **GRB 171205A**: coordinates _not stated_; z/distance z = 0.0368  
  > "announced a redshift of $z =$ 0.0368." (Introduction); distance from VLT spectroscopy (Izzo et al. 2017 GCN)  
  > "announced a redshift of $z =$ 0.0368." (Introduction)

## Data provenance

- ALMA projects: 2017.1.00801.T
- bands: ALMA Band 3 (97.5 GHz) polarimetry; ACA Band 7 (345 GHz)  
  > "using the linear polarization mode at Band 3 (representative frequency of 97.5 GHz) on 10 and 16 December 2017." (ALMA)
- frequencies and spectral setup: four SPWs at 90.5, 92.5, 102.5, 104.5 GHz, 1.75 GHz bandwidth each  
  > "The correlator processed four spectral windows (SPWs) centered at 90.5, 92.5, 102.5, and 104.5 GHz with a bandwidth of 1.75 GHz each." (ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: ALMA 10 and 16 Dec 2017; ACA 10, 12, 16 Dec 2017  
  > "The Atacama Compact Array (ACA) observations were executed on 10, 12, and 16 December 2017 at 345 GHz (Band 7)" (ALMA)
- pi or archival as stated: _not stated_
- Other facility **SMA**: 230 and 345 GHz flux monitoring  
  > "Intensive total flux monitoring was made using the Submillimeter Array (SMA) at 230 GHz starting 6 December 2017 with a total of six epochs." (SMA)
- Other facility **VLA**: 5-16 GHz total fluxes on 9 Dec 2017  
  > "The Very Large Array (VLA) made total flux measurements for the afterglow on 9 December 2017" (VLA)
- External data: Compilation of 84 optical afterglow polarization measurements for 13 GRBs  
  > "there are 84 polarimetric measurements for optical afterglows (i.e. excluding measurements for early-time reverse shock components that show high values) among 13 GRBs" (Faraday depolarization effect) [from Covino & Gotz 2016 (cite: 12)]

## Processing

### Calibration

- pipeline or manual: Raw data reduced at EA-ARC with CASA; polarization calibration with J1256-0547  
  > "The raw data were reduced at the East Asian ALMA Regional Center (EA-ARC) using CASA (version 5.1.1)." (ALMA)
- casa version: CASA 5.1.1  
  > "The raw data were reduced at the East Asian ALMA Regional Center (EA-ARC) using CASA (version 5.1.1)." (ALMA)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1127-1857 (bandpass and flux); J1130-1149 phase  
  > "The bandpass and flux were calibrated using observations of J1127-1857, and J1130-1149 was used for the phase calibration." (ALMA)
- flux scale uncertainty: _not stated_
- self calibration: amplitude and phase self-cal with infinite and then 30 s solution intervals  
  > "self-calibration both amplitude and phase with infinite and then 30s solution intervals" (ALMA)

### Imaging

- task: _not stated_
- deconvolver: iterative CLEAN, up to 15000 iterations, threshold 0.02 mJy  
  > "The Stokes $I, Q,$ and $U$ maps were CLEANed up to 15000 of CLEAN iterations with threshold of 0.02 mJy" (ALMA)
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

- Absolute polarization angle accuracy of 0.3 deg  
  > "slightly larger than the absolute accuracy of $0.3^{\circ}$(cite: nagai)." (ALMA) [from (cite: nagai)]

### Not stated but needed to reproduce (our reading)

- Weighting/robust, cell and image size
- Mask used in CLEAN
- Polarization calibration details and leakage handling
- Target coordinates and ALMA array configuration
- Fitting method for afterglow model and error treatment of P.A.
- Time on source

## Analysis recipe

1. **Image Stokes I, Q, U**: CLEAN with self-calibration on full band and per-SPW  
  > "we generated additional Stokes maps using the individual SPWs" (ALMA)
   - software: CASA
   - fitting: _not stated_
   - validation: Phase calibrator polarization stability <0.02%  
  > "we confirm that the stability of linear polarization degree is $<0.02$%" (ALMA)
2. **Derive polarization degree and position angle**: P=100 sqrt(Q^2+U^2)/I; P.A.=1/2 arctan(U/Q) via atan2  
  > "The $atan2$ function in the python math module which returns a numeric value between $-\pi$ and $\pi$, was used to calculate the polarization position angle." (ALMA)
   - software: Python
   - fitting: _not stated_
   - validation: _not stated_
3. **Model afterglow SED and light curve**: Granot & Sari 2002 forward shock with jet-break factor [1+(t/t_j)]^-3/4  
  > "we adopt the flux formula of (cite: 22) multiplied by the geometrical flux reduction factor $[1+(t/t_{j})]^{-3/4}$" (Afterglow modeling)
   - assumption: ISM environment, slow cooling  
  > "Alternatively, we find that the ISM environment case can well fit it." (Afterglow modeling)
   - fitting: _not stated_
   - validation: Computed X-ray light curve does not overwhelm the observed one  
  > "For these values we calculated X-ray light curve, which does not overwhelm the observed one." (Afterglow modeling)
4. **Test Faraday depolarization**: Compare observed P with model P0 sin(tau/2)/(tau/2) for non-accelerated electron fraction f  
  > "the polarization degree is given by $P_0 \sin(\tilde{\tau}_V/2)/(\tilde{\tau}_V/2)$" (Faraday depolarization effect)
   - parameter: P0 = 1%, 0.5%, 10%  
  > "For the case of $P_{0} = 0.5\%$ (Figure [3](#polspec)b), $1/f \sim 10$ is still required." (Faraday depolarization effect)
   - assumption: Tangled magnetic field in random cells  
  > "the magnetic field in the shocked region has been assumed to be tangled on hydrodynamic scales" (Faraday depolarization effect)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.1.1: ALMA/ACA reduction, imaging, self-calibration; SMA flux measurements; VLA  
  > "The raw data were reduced at the East Asian ALMA Regional Center (EA-ARC) using CASA (version 5.1.1)." (ALMA)
- **Miriad** : SMA imaging  
  > "were then imaged using Miriad software (cite: 31)" (SMA)
- **MIR** : SMA flagging and calibration  
  > "The data were flagged and calibrated with the MIR data-reduction package using standard procedures" (SMA)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Band 3 linear polarization degree (5.2 d) | 0.27 | 0.04 | % | 2 | yield a polarization degree of $0.27 \pm 0.04\%$ (including systematic error). |
| Band 3 polarization position angle | -71.3 | 3.3 | deg | 2 | 0.27$\pm$0.04     / $-$71.3$\pm$3.3 |
| Polarization upper limit at 11.2 d | <0.27 | 3 sigma | % | 2 | we measured the corresponding deep upper limit of the polarization degree ($<0.27\%$, 3$\sigma$ significance) |
| 230 GHz decay index early (t<4 d) | -0.30 | 0.07 | dimensionless | 0 | $\alpha
= -0.30 \pm 0.07$ for $t\lesssim4$ days |
| Required 1/f for P0=1% | ~12 | not stated | dimensionless | 4 | $1/f \sim 12\;(E_{\rm iso}/2\times10^{50} {\rm erg})^{-5/4} |

## Qualitative findings

- P.A. varies with wavelength by at least 20 degrees across Band 3; constant or linear in lambda^2 fits are poor  
  > "We tried to fit the P.A. data including the upper limit (cite: 28) with constant or linear function of squared wavelength, but did not obtain a good fit" (Polarization)

## Claim tuples

- H: Millimeter polarization of a GRB afterglow is detectable | E: ALMA Band 3 full-polarization observations of GRB 171205A | R: P = 0.27±0.04% at 5.2 days | F: First radio polarization detection of a GRB afterglow | **supported**
- H: Faraday depolarization by non-accelerated electrons explains the low polarization | E: Compare with depolarization model assuming optical-like P0 | R: 1/f ~ 10-60 required for P0 0.5-10%, but P0~0.33% needs none | F: Possible, implying ~10x larger energy; not unique | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Wind environment rejected for the shallow decay; ISM fits  
  > "Alternatively, we find that the ISM environment case can well fit it." (Afterglow modeling)
- How they decided it was enough: _not stated_
- Limitation (authors): Non-simultaneous multi-wavelength polarimetry limits conclusions  
  > "Although the (semi-) simulataneous measurments in multiple wavelengths are required" (Faraday depolarization effect)
- Caveat (inferred, ours): Intrinsic optical polarization unmeasured, so P0 is assumed
- Caveat (inferred, ours): Low-significance polarization near the leakage/systematic floor
- Caveat (inferred, ours): Model fit lacks stated fitting procedure or uncertainties

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging weighting and masks
- Missing: Polarization calibration specifics
- Missing: Afterglow fit procedure
- Data volume (inferred): ~50-100 GB for ALMA Band 3 polarization plus ACA
- Score (inferred): 3/5, Calibration sources and CASA version are given, but imaging parameters and fit procedures are missing.
- Rediscovery candidate: no, The data public status is not stated and imaging and modeling details are incomplete.

## Links

- Method: Granot & Sari 2002 (cite: 22) (Afterglow synchrotron spectrum formula)
- Method: Toma, Ioka & Nakamura 2008 (cite: 9) (Faraday depolarization model)

## Checks

```json
{
 "quotes": 39,
 "quotes_ok": 39,
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
  "facts": 68,
  "stated": 30,
  "rate": 0.441
 },
 "evidence_ok": true
}
```

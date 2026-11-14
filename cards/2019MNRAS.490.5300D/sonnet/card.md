# Investigating the multiwavelength behaviour of the flat spectrum radio quasar CTA 102 during 2013-2017

`2019MNRAS.490.5300D` | Monthly Notices of the Royal Astronomical Society 2019 | first author: D'Ammando, F. | arXiv: 1910.03609 | DOI: 10.1093/mnras/stz2792

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: agn_and_quasars
- Question: How do the flux and spectral variability and the cross-band correlations of CTA 102 from radio to gamma rays during 2013–2017 fit the geometrical (Doppler factor/viewing angle) model?  
  > "to study flux and spectral variability and the correlation between flux changes at different wavelengths." (abstract)
- Target **CTA 102 (4C +11.69)**: coordinates _not stated_; z/distance z = 1.037  
  > "CTA 102 (also known as 4C $+$11.69) is an FSRQ at redshift $z = 1.037$ (cite: schmidt65)." (Introduction); distance from Schmidt 1965 (cite: schmidt65)  
  > "CTA 102 (also known as 4C $+$11.69) is an FSRQ at redshift $z = 1.037$ (cite: schmidt65)." (Introduction)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 3 (91 and 103 GHz)  
  > "We also added the ALMA data collected at 91 and 103 GHz (Band 3) during 2013–2017" (Optical-to-radio observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2013–2017  
  > "We also added the ALMA data collected at 91 and 103 GHz (Band 3) during 2013–2017" (Optical-to-radio observations)
- pi or archival as stated: _not stated_
- Other facility **Fermi-LAT**: gamma-ray light curves and spectra, 0.1–300 GeV  
  > "The LAT data used in this paper were collected from 2013 January 1 (MJD 56293) to 2017 February 9 (MJD 57793)." (Fermi-LAT Data: analysis and results)
- Other facility **Swift (XRT, UVOT)**: X-ray and optical-UV data  
  > "carried out 73 observations of CTA 102 between 2013 March 24 (MJD 56436) and 2017 January 18 (MJD 57771)" (Swift data)
- Other facility **OVRO 40-m**: 15 GHz light curve  
  > "the OVRO 40-Meter Telescope has observed CTA 102 at 15 GHz regularly since the beginning of 2009" (Optical-to-radio observations)
- Other facility **REM**: near-IR J,H,K ToO photometry  
  > "observations performed by REM (cite: zerbi01; covino04), a robotic telescope located at the ESO Cerro La Silla observatory (Chile)" (Optical-to-radio observations)
- Other facility **WEBT**: optical, near-IR and radio data  
  > "Optical-to-radio GASP-WEBT data collected in 2013–2017 have been presented in (cite: rai17)." (Optical-to-radio observations)
- External data: WEBT optical-to-radio data set 2013–2017  
  > "Optical-to-radio GASP-WEBT data collected in 2013–2017 have been presented in (cite: rai17)." (Optical-to-radio observations) [from Raiteri et al. 2017 (cite: rai17)]
- External data: UVOT count-rate-to-flux conversion factors and Galactic extinction  
  > "obtained by folding the quantities of interest with the source spectrum and effective areas of UVOT filters and are reported in (cite: lar16)." (Swift data) [from Larionov et al. 2016 (cite: lar16)]

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

- Thermal emission (disc, BLR) subtraction in UVOT data  
  > "we also subtracted the thermal emission contribution due to the accretion disc and BLR according to the model by (cite: raiteri14)." (Swift data) [from (cite: raiteri14)]
- Geometrical model with Gamma=20 and theta_max=9 deg  
  > "$\delta_{\rm min}=3.7$ is obtained by assuming a bulk Lorentz factor $\Gamma=20$ and a maximum jet viewing angle $\theta_{\rm max}=9$ deg (cite: rai17)" (7 Geometrical model) [from Raiteri et al. 2017 (cite: rai17)]

### Not stated but needed to reproduce (our reading)

- ALMA project codes, calibrator flux scale and processing (data taken from the ALMA calibrator catalogue)
- Exact ALMA flux values or the catalogue query
- Exact Fermi source model files and the FL8Y list used

## Analysis recipe

1. **Fermi-LAT light curves**: Binned maximum-likelihood with gtlike, log-parabola spectrum, 30-d, 5-d, 1-d and 12-h bins  
  > "The spectral analysis was performed with the instrument response functions `P8R2_SOURCE_V6` using a binned maximum-likelihood method implemented in the Science tool `gtlike`." (Fermi-LAT Data)
   - software: ScienceTools, gtlike
   - fitting: _not stated_
   - validation: _not stated_
2. **Cross-correlation of bands**: DCF with 1000 Monte Carlo flux redistribution/random subset selection simulations  
  > "We determine the uncertainty in this result by performing 1000 Monte Carlo simulations according to the “flux redistribution/random subset selection” technique" (5 Multifrequency flux variability)
   - fitting: _not stated_
   - validation: _not stated_
3. **Doppler factor and viewing angle from splines**: Cubic spline through variable-binned light curves, delta(t)=delta_min (F_spline/F_min)^(1/(2+alpha))  
  > "we modelled the optical long-term trend with a cubic spline interpolation through the data binned with a variable time interval" (7 Geometrical model)
   - assumption: Gamma=20, theta_max=9 deg, alpha=1.7 in R band  
  > "$\alpha=1.7$ is the spectral index in the $R$ band" (7 Geometrical model)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **ScienceTools** v11r5p3: Fermi-LAT analysis  
  > "The analysis was performed with the `ScienceTools` software package version v11r5p3." (Fermi-LAT Data)
- **HEAsoft** v6.22: Swift XRT and UVOT processing  
  > "by using the `HEAsoft` package (v6.22)" (Swift data)
- **xrtpipeline** v0.13.3: XRT data processing  
  > "`xrtpipeline v0.13.3`" (Swift data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Peak gamma-ray daily flux on 2016 Dec 28 | 2158 | 63 | 1e-8 ph cm^-2 s^-1 | 1 | A peak flux of (2158 $\pm$ 63)$\times$10$^{-8}$ ph cm$^{-2}$ s$^{-1}$ |
| DCF peak gamma/optical in high-activity period | 0.94 | not stated | dimensionless | 2 | the DCF shows again a main peak compatible with no time lag, with DCF$_p$ = 0.94 |
| Gamma-optical linear fit slope during outburst | 1.00 | not stated | dimensionless | 3 | we obtain a linear fit with slope equal to 1.00 and linear Pearson correlation coefficient equal to 0.90 |
| 103 GHz variability amplitude | 4.3 | not stated | dimensionless | 0 | / 103 GHz / 1.63$\times$10$^{-12}$ (MJD 56837) / 6.93$\times$10$^{-12}$ (MJD 57649) / 4.3 / |

## Qualitative findings


## Claim tuples

- H: Gamma-ray and optical emission come from the same jet region and are linearly correlated | E: DCF and linear fit between gamma-ray and R-band fluxes | R: No lag, DCF peak 0.94, slope 1.00 in outburst | F: Consistent with the geometrical Doppler factor model | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Caveat (inferred, ours): ALMA data play a minor role and are taken from the calibrator catalogue
- Caveat (inferred, ours): Model support is largely qualitative

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA fluxes and processing details
- Data volume (inferred): small (light curves)
- Score (inferred): 2/5, ALMA is only a minor input taken from a catalogue and details are absent.
- Rediscovery candidate: no, ALMA data are minor and not described.

## Links

- Companion: Raiteri et al. 2017 (cite: rai17) (original WEBT data and geometrical model)
- Related: WEBT/GASP

## Checks

```json
{
 "quotes": 27,
 "quotes_ok": 27,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 65,
  "stated": 21,
  "rate": 0.323
 },
 "evidence_ok": true
}
```

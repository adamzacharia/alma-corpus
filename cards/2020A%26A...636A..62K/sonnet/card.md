# Investigating the connection between γ-ray activity and the relativistic jet in 3C 273 during 2015-2019

`2020A&A...636A..62K` | Astronomy and Astrophysics 2020 | first author: Kim, Dae-Won | arXiv: 2003.05659 | DOI: 10.1051/0004-6361/202037474

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: agn_and_quasars
- Question: What is the origin of the 2015-2019 gamma-ray outbursts of 3C 273 and how do they connect to the parsec-scale jet?  
  > "We aim at constraining the origin of the $\gamma$-ray outbursts towards 3C 273 and investigate their connection to the parsec-scale jet." (abstract)
- Target **3C 273**: coordinates _not stated_; z/distance z = 0.158  
  > "corresponding to an angular scale of 2.71 pc/mas at the redshift of 3C 273, $z=0.158$ (cite: strauss1992)." (1 Introduction); distance from strauss1992  
  > "corresponding to an angular scale of 2.71 pc/mas at the redshift of 3C 273, $z=0.158$ (cite: strauss1992)." (1 Introduction)

## Data provenance

- ALMA projects: _none stated_
- bands: ALMA Band 3 (84-116 GHz), mostly 91 and 103 GHz  
  > "The flux data were obtained at ALMA band 3 (84–116 GHz), with the majority of them have been taken at 91 and 103 GHz." (2.2 ALMA Band 3)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2015 January to 2018 December  
  > "spanning from 2015 January to 2018 December" (2.2 ALMA Band 3)
- pi or archival as stated: _not stated_
- Other facility **Fermi-LAT**: Pass 8 gamma-ray light curves and photon indices, 0.1-300 GeV  
  > "We analyze Pass 8 $\gamma$-ray data obtained by the *Fermi*-LAT (cite: atwood2009)." (2.1 Fermi-LAT)
- Other facility **VLBA (VLBA-BU-BLAZAR)**: 43 GHz monthly images, polarization and Gaussian component models  
  > "We used fully calibrated data for 3C 273, available publicly" (2.3 VLBA 43 GHz)
- External data: ALMA Band 3 flux light curve of 3C 273 (calibrator monitoring)  
  > "Further details of the observations can be found in (cite: bonato2018)." (2.2 ALMA Band 3) [from Bonato et al. 2018 (cite: bonato2018)]
- External data: CLEANed model components for 43 GHz fluxes  
  > "We also use the CLEANed model components provided by the BU group in their website" (2.3 VLBA 43 GHz) [from VLBA-BU-BLAZAR (cite: jorstad2017)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: VLBA data fully calibrated, public; ALMA light curve taken from calibrator catalogue  
  > "We used fully calibrated data for 3C 273, available publicly" (2.3 VLBA 43 GHz)
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

- ALMA observation details  
  > "Further details of the observations can be found in (cite: bonato2018)." (2.2 ALMA Band 3) [from (cite: bonato2018)]
- VLBA-BU-BLAZAR data description  
  > "A full description of the VLBA-BU-BLAZAR data can be found in (cite: jorstad2017)." (2.3 VLBA 43 GHz) [from (cite: jorstad2017)]
- Polarization maps made similar to earlier work  
  > "We further produce linear polarization maps similar to (cite: kim2018d) for all epochs." (2.3 VLBA 43 GHz) [from (cite: kim2018d)]

### Not stated but needed to reproduce (our reading)

- ALMA flux calibration and which calibrators/frequencies per epoch
- Exact ALMA light-curve data table
- Fermi-LAT spectral-fit details beyond the standard recipe
- Gaussian model-fit parameters (in an appendix not in the text)

## Analysis recipe

1. **Build gamma-ray light curves**: Unbinned likelihood analysis with 30-day, 7-day and 1-day bins, power-law model  
  > "As binning intervals for the $\gamma$-ray light curves, we select 30 and 7 days for the full time range (i.e., 2015–2019), and one day for flaring periods" (2.1 Fermi-LAT)
   - software: ScienceTools
   - parameter: ROI 15x15 deg; zmax=90 deg; upper limits for TS<9 or dF/F>0.5  
  > "We defined a region of interest (ROI) of $15^{\circ} \times 15^{\circ}$ centered at 3C 273" (2.1 Fermi-LAT)
   - fitting: _not stated_
   - validation: _not stated_
2. **Correlate ALMA 3 mm and gamma-ray light curves**: Discrete correlation function with Gaussian fit to the peak; Pearson significance following Rani et al. 2013a  
  > "We employ the discrete correlation function (DCF; (cite: edelson1988)) to investigate the relationship between $\gamma$-ray and radio emission." (3.3 Correlation)
   - parameter: DCF time steps 12 d (weekly) and 33 d (monthly)  
  > "We therefore use time steps of 12 and 33 days for the DCF analysis for the weekly and monthly binned $\gamma$-ray fluxes, respectively." (3.3 Correlation)
   - fitting: Gaussian fit to DCF  
  > "To determine height and location of a DCF peak, we fit a Gaussian function defined as $DCF(t) = a\,\times$ exp$\left[-(t-c)^{2}/2w^{2}\right]$ to the DCF durve" (Correlation between the radio and $\gamma$-ray light curves)
   - validation: Varied DCF binning; repeated for 2015-2017 subset  
  > "However, the time delays found from Gaussian fits are only weakly affected by the binning of the DCF" (3.3 Correlation)
3. **Analyze 43 GHz VLBA jet structure**: Circular Gaussian components fitted in visibility domain; polarization maps; proper motions of the peak  
  > "the structure of the jet was represented by a number of two-dimensional circular Gaussians fitted to the visibility domain." (3.4 Parsec-scale jet)
   - software: Difmap
   - parameter: 10% flux accuracy; position error ~1/10 beam; polarization threshold 9 sigma  
  > "We consider a conservative accuracy of flux densities of 10%." (2.3 VLBA 43 GHz)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **Fermi ScienceTools** v11r5p3: gamma-ray likelihood analysis  
  > "we optimize the background model using the ScienceTools (`v11r5p3`)" (2.1 Fermi-LAT)
- **Difmap** : imaging of VLBA data  
  > "Data are imaged with the software package `Difmap` (cite: shepherd1997)." (2.3 VLBA 43 GHz)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| DCF time lag, LAT 7d vs ALMA | -105 | 4 | days | 2 | $c$ (days) / $-105\pm4$ / $-112\pm6$ |
| DCF time lag, LAT 30d vs ALMA | -112 | 6 | days | 2 | $c$ (days) / $-105\pm4$ / $-112\pm6$ |
| Flux-index transition flux (monthly) | 1.03e-7 | not stated | ph cm^-2 s^-1 | 1 | different trends above and below a flux of about $1.03\times10^{-7}$ ph cm$^{-2}$ s$^{-1}$ |
| Apparent speed after 2016 outburst | ~6.0 c | not stated | c | 3 | The proper motion of this displacement is about 0.59 mas/year which corresponds to an apparent speed of $\sim$6.0 $c$ |
| S1 brightness temperature peak | 2.3e12 | not stated | K | 3 | $S1$ reaches $2.3\times10^{12}$ K |

## Qualitative findings

- Gamma-ray outbursts coincide with flares of stationary components (core, S1, S2) and polarized knots, supporting a parsec-scale origin  
  > "Our results support a parsec-scale origin for the observed $\gamma$-ray elevated activity, suggesting association with standing shocks in the jet." (abstract)

## Claim tuples

- H: Gamma-ray and mm radio emission are correlated | E: DCF between Fermi-LAT and ALMA 3 mm light curves | R: Radio lags gamma-rays by 105-112 d, r_p 0.48-0.67, >99% significance | F: Significant correlation, dominated by 2015-2017 flares | **supported**
- H: Gamma-ray outbursts originate in the parsec-scale jet | E: 43 GHz VLBA component and polarization analysis near outbursts | R: Flares of core/S1/S2 and polarized knots near both outbursts | F: Association with standing shocks and propagating disturbances | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: BLR as seed-photon source disfavored at S1/S2 distances  
  > "disfavors the BLR as the source of seed photons" (4.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Photon index uncertainties too large for quantitative analysis  
  > "Overall, the uncertainties of the photon indices are too large for a meaningful quantitative analysis." (3.2)
- Caveat (inferred, ours): Single-source, few-outburst statistics; lag significance not simulation-based
- Caveat (inferred, ours): Core opacity/core shift ambiguity unresolved

## Reproducibility

- Data public (paper): Fermi and VLBA-BU-BLAZAR data public; ALMA calibrator data via catalogue  
  > "This work makes use of public Fermi data obtained from *Fermi* Science Support Center (FSSC)." (Acknowledgements)
- Products in archive: _not stated_
- Missing: ALMA light curve table details
- Missing: Appendix Gaussian component parameters
- Data volume (inferred): <10 GB (light curves plus public VLBA uv-data)
- Score (inferred): 3/5, Public data and a fairly clear recipe, but ALMA part is a calibrator light curve and several choices are inherited.
- Rediscovery candidate: yes, Public data, DCF lag numerics are reproducible.

## Links

- Method: Edelson & Krolik 1988 (DCF method)
- Method: Rani et al. 2013a (DCF significance)
- Companion: Bonato et al. 2018 (ALMA calibrator light curves)
- Companion: Lisakov et al. 2017 (earlier 3C 273 VLBI study)
- Related: VLBA-BU-BLAZAR
- Related: ALMA Calibrator Catalogue

## Checks

```json
{
 "quotes": 35,
 "quotes_ok": 35,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2011.0.00001.CAL"
 ],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 27,
  "rate": 0.403
 },
 "evidence_ok": true
}
```

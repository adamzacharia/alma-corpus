# Probing UV-sensitive Pathways for CN and HCN Formation in Protoplanetary Disks with the Hubble Space Telescope

`2020AJ....159..168A` | The Astronomical Journal 2020 | first author: Arulanantham, Nicole | arXiv: 2002.09058 | DOI: 10.3847/1538-3881/ab789a

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: How do UV radiation field tracers measured with HST (Lya, FUV continuum, C II], UV-H2) relate to sub-mm CN and 14 micron HCN emission in disks?  
  > "In an effort to understand the relationship between photocatalyzing UV radiation fields and gas emission observed at infrared and sub-mm wavelengths" (abstract)
- Target **RU Lupi, RY Lupi, MY Lupi, Sz 68, J1608-3070 (Lupus) plus 14 Taurus-Auriga disks**: coordinates _not stated_; z/distance d ~ 160 pc (Lupus); 154-159 pc per target in Table 1  
  > "Our sample consists of five young stars with circumstellar disks in the nearby ($d \sim 160$ pc; (cite: Gaia)) Lupus cloud complex" (2.1 A Sample of Young Disks in the Lupus Complex); distance from Gaia (cite: Gaia)  
  > "Our sample consists of five young stars with circumstellar disks in the nearby ($d \sim 160$ pc; (cite: Gaia)) Lupus cloud complex" (2.1 A Sample of Young Disks in the Lupus Complex)

## Data provenance

- ALMA projects: 2013.1.00220.S
- bands: CN detected in ALMA Band 7 (Lupus, from literature)  
  > "CN, which has been detected in ALMA Band 7 observations of a large sample of disks in the Lupus clouds (cite: vanTerwisga2019)" (3 Results)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CN N=3-2, J=7/2-5/2 (Lupus); N=2-1, J=5/2-3/2 (Taurus) (not stated)
- Other facility **HST COS and STIS**: UV spectra: Lya (reconstructed), FUV continuum, C II], UV-H2  
  > "All five systems were observed with the *Hubble Space Telescope (HST)*, using both the Cosmic Origins Spectrograph (COS; (cite: Green2012)) and the Space Telescope Imaging Spectrograph" (2.2 Observations)
- Other facility **Spitzer IRS (CASSIS)**: 14 micron HCN fluxes  
  > "The data were retrieved from the Combined Atlas of Sources with Spitzer IRS Spectra (CASSIS; (cite: Lebouteiller2011; Lebouteiller2015))" (2.2 Observations)
- Other facility **SMA and IRAM 30m**: literature sub-mm CN fluxes for Taurus disks  
  > "The data were acquired with the SMA (cite: Oberg2010; Oberg2011), the IRAM 30-m telescope (cite: Guilloteau2013), and ALMA (cite: vanTerwisga2019)" (2.2 Observations)
- External data: Lupus CN fluxes from ALMA survey (aperture photometry)  
  > "with (cite: vanTerwisga2019) using aperture photometry" (2.2 Observations) [from (cite: vanTerwisga2019)]
- External data: Taurus CN fluxes from IRAM and SMA  
  > "The data were acquired with the SMA (cite: Oberg2010; Oberg2011), the IRAM 30-m telescope (cite: Guilloteau2013)" (2.2 Observations) [from (cite: Guilloteau2013; Oberg2010; Oberg2011)]
- External data: Stellar and disk properties of targets  
  > "Table [1](#stellar_props) lists the properties of each target from (cite: Alcala2017), including stellar mass, disk inclination, and visual extinction" (2.1 A Sample of Young Disks in the Lupus Complex) [from (cite: Alcala2017)]

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

- CN 2-1/3-2 flux ratio of 1.6 used to convert Lupus fluxes  
  > "we adopted the methodology of (cite: vanTerwisga2019) and used the ratio" (2.2 Observations) [from (cite: vanTerwisga2019)]
- SED stitching and FUV continuum extrapolation to 912 A  
  > "stitched together to produce a SED for each system using the methods outlined in (cite: France2014) and (cite: Arulanantham2018)" (2.2 Observations) [from (cite: France2014; Arulanantham2018)]
- Lya reconstruction from fluorescent H2  
  > "we use the method from (cite: Schindhelm2012) to reconstruct the Ly$\alpha$ profiles" (3.2 Ly$\alpha$ as a Regulator of Disk Chemistry) [from (cite: Schindhelm2012)]

### Not stated but needed to reproduce (our reading)

- Exact ALMA CN fluxes and uncertainties per target (taken from van Terwisga 2019)
- Which statistic and software computed Spearman correlations and p-values
- Prior bounds and walker steps for Lya MCMC

## Analysis recipe

1. **Measure UV tracers and normalize**: Stitch HST spectra, extrapolate FUV continuum with 2nd-order polynomial, measure C II], UV-H2, and normalize each by total UV luminosity  
  > "we divide the individual UV components by the total UV luminosity $\left(L_{UV, total} \right)$" (2.5 Normalized UV Luminosities)
   - fitting: _not stated_
   - validation: _not stated_
2. **Reconstruct Lya**: Fit Lya profile model to H2 progression fluxes with MCMC  
  > "Posterior distributions for the model parameters were constructed using MCMC sampling (cite: ForemanMackey2013)" (3.2)
   - software: emcee
   - fitting: _not stated_
   - validation: _not stated_
3. **Correlate UV tracers with CN and HCN**: Spearman rank correlations  
  > "We report a significant positive correlation between the FUV and IR HCN fluxes $\left( \rho = 0.64; p = 0.01 \right)$" (3.1)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **emcee** : MCMC for Lya profile and H2 radiative transfer fits  
  > "uncertainties on the best-fit models were estimated using MCMC re-sampling (cite: ForemanMackey2013)" (4.2)
- **Astropy** : general analysis  
  > "This research made use of Astropy" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Spearman correlation FUV vs HCN | 0.64 (p=0.01) | not stated | dimensionless | 3 | $\rho = 0.64; p = 0.01$ |
| Spearman correlation FUV vs CN | -0.6 (p=0.02) | not stated | dimensionless | 3 | $\rho = -0.6; p = 0.02$ |
| Spearman correlation C II] vs HCN | 0.82 (p=0.0005) | not stated | dimensionless | 3 | $\rho = 0.82; p = 0.0005$ |

## Qualitative findings


## Claim tuples


## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Caveat (inferred, ours): Small sample, heterogeneous CN data
- Caveat (inferred, ours): Non-simultaneous observations

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Literature CN fluxes must be obtained from the cited papers
- Data volume (inferred): small (<1 GB for HST/Spitzer spectra)
- Score (inferred): 3/5, Mostly literature ALMA fluxes; HST analysis described moderately.
- Rediscovery candidate: no, ALMA role is minor and CN fluxes come from literature.

## Links

- Related: DSHARP

## Checks

```json
{
 "quotes": 24,
 "quotes_ok": 24,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 63,
  "stated": 18,
  "rate": 0.286
 },
 "evidence_ok": true
}
```

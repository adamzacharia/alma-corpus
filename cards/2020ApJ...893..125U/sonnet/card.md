# Scattering-induced Intensity Reduction: Large Mass Content with Small Grains in the Inner Region of the TW Hya disk

`2020ApJ...893..125U` | The Astrophysical Journal 2020 | first author: Ueda, Takahiro | arXiv: 2003.09353 | DOI: 10.3847/1538-4357/ab8223

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: Does dust scattering reduce the observed mm continuum intensity in the inner (<~10 au) TW Hya disk, and what dust mass and grain size does this imply?  
  > "We investigate whether the dust scattering indeed reduces the observed continuum intensity by comparing the ALMA archival data of the TW Hya disk" (abstract)
- Target **TW Hya**: coordinates _not stated_; z/distance ≈ 60 pc  
  > "for the distance of the target from the Earth ($\approx$ 60 pc, (cite: Gaia2016))" (2.2 SED analysis); distance from Gaia (cite: Gaia2016)  
  > "for the distance of the target from the Earth ($\approx$ 60 pc, (cite: Gaia2016))" (2.2 SED analysis)

## Data provenance

- ALMA projects: 2016.1.00229.S, 2012.1.00422.S, 2015.A.00005.S, 2013.1.00114.S, 2015.1.00308.S, 2015.1.00686.S, 2016.1.00311.S, 2016.1.00440.S, 2016.1.00464.S, 2016.1.00629.S, 2016.1.01495.S
- bands: Band 3, 4, 6, 7, 9 continuum  
  > "we analyze the public images of the continuum emission of the TW Hya disk at Band 3, 4, 6, 7, and 9 taken with ALMA" (2.1 ALMA data and analysis)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.43x0.27, 0.088x0.062, 0.075x0.055, 0.036x0.029, 0.38x0.23 arcsec for Band 3, 4, 6, 7, 9  
  > "$0.43\times0.27$, $0.088\times0.062$, $0.075\times0.055$, $0.036\times0.029$ and $0.38\times0.23$ arcsec for Band 3, 4, 6, 7 and 9, respectively" (2.1 ALMA data and analysis)
- max recoverable scale: 5.0, 18, 12, 8.8, 5.1 arcsec for Band 3, 4, 6, 7, 9  
  > "The maximum recoverable scale of the obtained data is 5.0, 18, 12, 8.8 and 5.1 arcsec for Band 3, 4, 6, 7 and 9, respectively." (2.1 ALMA data and analysis)
- sensitivity: Noise at image centre 1.1, 0.24, 0.12, 0.091, 0.025 mJy/beam for B9, B7, B6, B4, B3  
  > "|   453.5 (B9)    |     499      |     1.1      |  $\pm99.8$   |" (Table 1)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- External data: Band 4 and 6 continuum images  
  > "The Band 4 and 6 images are adopted from (cite: Tsukagoshi2016), and the Band 7 image is from (cite: Tsukagoshi2019)." (2.1 ALMA data and analysis) [from (cite: Tsukagoshi2016)]
- External data: Band 7 continuum image  
  > "The Band 4 and 6 images are adopted from (cite: Tsukagoshi2016), and the Band 7 image is from (cite: Tsukagoshi2019)." (2.1 ALMA data and analysis) [from (cite: Tsukagoshi2019)]
- External data: DSHARP dust optical constants  
  > "we use the DSHARP dust optical constants published in (cite: Birnstiel2018)" (3.2 Radiative transfer setup) [from (cite: Birnstiel2018)]
- External data: Disk inclination 7 deg  
  > "The disk inclination is set to be $7^{\circ}$ based on (cite: Qi2004)." (3.2 Radiative transfer setup) [from (cite: Qi2004)]
- External data: Gas surface density from 13C18O J=3-2  
  > "has been estimated by using observations of the ${\rm ^{13}C^{18}O} \, J=3-2$ line emission" (4.3 Disk masses) [from (cite: Zhang2017)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline scripts for flagging, bandpass, gain, flux scaling; then self-calibration  
  > "The initial flagging of the visibilities and the calibrations for the bandpass characteristics, complex gain, and flux scaling were performed using the pipeline scripts provided by ALMA." (2.1 ALMA data and analysis)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1037-2934 (Band 3,4,6,9; also J1107-4449 for some Band 7); Pallas (B6), Titan (B9)  
  > "| 9 | 2012.1.00422.S | 1 | J1037-2934, (Titan) |" (Table 3)
- flux scale uncertainty: 5% Band 3, 4; 10% Band 6, 7; 20% Band 9 (official); more conservative 10/10/10/15/20% tested  
  > "The uncertainty in the absolute intensity is set to be 5% for Band 3 and 4, 10% for Band 6 and 7 and 20% for Band 9." (Table 1); "we set the uncertainty as 10% for Band 3, 4 and 6, 15% for Band 7 and 20% for Band 9" (Time variability of calibrator fluxes)
- self calibration: Applied to Band 3 and 9 data  
  > "After that, self-calibration was applied for the data set." (2.1 ALMA data and analysis)

### Imaging

- task: CLEAN in CASA  
  > "After flagging the bad data, the corrected data were concatenated and imaged by CLEAN." (2.1 ALMA data and analysis)
- deconvolver: _not stated_
- weighting robust: Briggs robust 0.8 (Band 3), 0.5 (Band 9)  
  > "Briggs weighting with a robust parameter of 0.8 for Band 3 and 0.5 for Band 9" (2.1 ALMA data and analysis)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Band 4, 6, 7, 9 images re-convolved to Band 3 beam 0.43x0.27 arcsec (26x16 au)  
  > "the observed images at Band 4, 6, 7 and 9 are re-convolved with the beam size of Band 3 observation ($0.43\times0.27$ arcsec)" (2.2 SED analysis)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Calibration and imaging of Band 4, 6, 7 images  
  > "For the detailed calibration process of Band 4, 6 and 7 images, we refer readers to (cite: Tsukagoshi2016) and (cite: Tsukagoshi2019)." (2.1 ALMA data and analysis) [from (cite: Tsukagoshi2016); (cite: Tsukagoshi2019)]

### Not stated but needed to reproduce (our reading)

- Stellar luminosity/heating setup and how T10 is imposed in RADMC-3D (photon numbers, grid)
- CASA version and pipeline version
- Self-calibration parameters and CLEAN settings for Band 3 and 9 (masks, thresholds, cell size)
- Exact Band 3 and 9 execution blocks used
- Fit procedure: models compared by eye, no quantitative statistic
- Gas scale height and treatment of vertical temperature structure

## Analysis recipe

1. **Image Band 3 and 9 continuum and gather Band 4, 6, 7 images**: Pipeline calibration, CLEAN with Briggs weighting, self-calibration; other bands taken from published images  
  > "The CLEAN map was created by adopting Briggs weighting with a robust parameter of 0.8 for Band 3 and 0.5 for Band 9." (2.1 ALMA data and analysis)
   - software: CASA
   - fitting: _not stated_
   - validation: Calibrator flux time variability checked (Appendix)  
  > "In Appendix [6](#sec:ap1), we examined the time variation of the flux density of the amplitude calibrators to see the actual uncertainty." (2.2 SED analysis)
2. **Measure central-intensity SED at common resolution**: Convolve all images to Band 3 beam and read central intensity; compute spectral indices  
  > "The intensities at the center of the re-convolved images at each band are shown in Figure [2](#fig:sed-inside) and summarized in Table [1](#table:1)." (2.2 SED analysis)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Radiative transfer models with and without scattering**: RADMC-3D Monte Carlo with Mie opacities, power-law dust size distribution, Sigma_d ∝ r^-0.5, T ∝ r^-0.4; simulated images convolved with beam; vary T10, tau10, a_max  
  > "radiative transfer simulations are performed with the Monte Carlo radiative transfer code RADMC-3D (cite: RADMC)." (3.2 Radiative transfer setup)
   - software: RADMC-3D
   - parameter: Dust size distribution 0.1 µm to a_max, index 3.5; disk from 1 to 50 au; h_d=0.63 (r/10 au)^1.1 au  
  > "The dust size distribution is assumed to be a power-law distribution ranging from 0.1 ${\rm \mu m}$ to $a_{\rm max}$ with the power-law index of 3.5." (3.2 Radiative transfer setup)
   - assumption: Compact spherical grains, density 1.675 g cm^-3; inclination 7 deg; DSHARP opacity  
  > "The dust grains are assumed to be spherical compact grains with the material density of 1.675 ${\rm g~cm^{-3}}$." (3.2 Radiative transfer setup)
   - fitting: Manual comparison of model grids to SED; tau10 set to match Band 3 intensity  
  > "the disk mass (i.e., $\tau_{10}$) is set for each temperature model so that the observed intensity at Band 3 is reproduced" (3.3 Step 1)
   - validation: Test with larger flux uncertainties  
  > "We clearly see that the model with 300 ${\rm \mu m}$-sized grains is still the best to reproduce the observed intensity profile." (Time variability of calibrator fluxes)
4. **Derive dust mass and implications**: Convert tau10 to surface density with kappa_B3; integrate within 10 au; Toomre Q and fragmentation alpha estimates  
  > "the inner region ($<10$ au) of the TW Hya disk has a total dust mass of $150M_{\oplus}$" (4.3 Disk masses)
   - assumption: kappa_abs(Band 3)=9.2e-2 cm2/g; T=30 K; stellar mass 0.8 Msun  
  > "The DSHARP opacity we use has an absorption opacity of $9.2\times10^{-2}\,{\rm cm^{2}\,g^{-1}}$ at the wavelength of Band 3" (4.1 Dependence on the opacity model)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration and imaging of Band 3 and 9 data  
  > "The observed visibilities were reduced and calibrated using the Common Astronomical Software Application (CASA) package (cite: McMullin2007)." (2.1 ALMA data and analysis)
- **RADMC-3D** : Monte Carlo radiative transfer models  
  > "radiative transfer simulations are performed with the Monte Carlo radiative transfer code RADMC-3D (cite: RADMC)." (3.2 Radiative transfer setup)
- **Bohren-Huffman Mie code** : Mueller matrices/opacities  
  > "the Müeller matrices are calculated using the Mie theory, specifically Bohren-Huffman program (cite: Bohren1983)" (3.2 Radiative transfer setup)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Central intensity Band 3 | 15.1 | ±0.755 | mJy/beam | 2 | /   3064 (B3)    /     15.1     /    0.025     /  $\pm0.755$  / |
| Spectral index Band 6-7 | ≈1.4 | not stated | dimensionless | 2 | The spectral index between Band 6 and 7 is $\approx 1.4$ which is significantly lower than 2. |
| Spectral index Band 6-9 | ≈1.6 | not stated | dimensionless | 2 | the spectral index between Band 6 and 9 is $\approx1.6$ |
| Best model with scattering: tau10, T10, a_max | 0.95, 30 K, ~300 µm | not stated | dimensionless, K, µm | 3 | The optical depth is determined as $\tau_{10}=0.95$ since the disk is marginally optically thin at Band 3. |
| Best no-scattering model: tau10, T10 | 2.2, 22 K | not stated | dimensionless, K | 3 | except for the model with $\tau_{10}=2.2$ and $T_{10}=22$ K |
| Dust surface density at 10 au | 10 | not stated | g cm^-2 | 4 | meaning that the dust surface density needs to be $10\,{\rm g\,cm^{-2}}$ at 10 au |
| Scattering intensity reduction at Band 7 | ~35% | not stated | % | 3 | reduces the intensity at those bands by $\sim$ 35% |
| Dust mass within 10 au | 150 | not stated | Earth masses | 4 | the inner region ($<10$ au) of the TW Hya disk has a total dust mass of $150M_{\oplus}$ |
| Dust-to-gas ratio at 10 au (vs Zhang2017 gas) | 0.4 | not stated | dimensionless | 4 | the dust-to-gas mass ratio is 0.4 at 10 au |

## Qualitative findings

- Model with scattering and 300 µm grains reproduces the SED dip at Band 7; no-scattering model is also consistent within flux errors, leaving a degeneracy.  
  > "Although the model with scattering well reproduces the observed millimeter SED, the model without scattering is also consistent with the observations within the errors in the absolute intensities." (4.6 Solving a degeneracy between models with and without scattering)

## Claim tuples

- H: Dust scattering reduces observed mm intensity in the inner TW Hya disk | E: Multi-band SED at common beam compared with RADMC-3D models with and without scattering | R: Scattering model with 300 µm grains fits; Band 7 intensity reduced ~35% | F: Scattering can hide large dust mass; Sigma_d ~10 g/cm2 at 10 au, 26x previous estimate | **supported**
- H: Scattering is required to explain the SED | E: No-scattering models with varied temperature | R: Only T10=22 K, tau10=2.2 fits, within errors | F: Degeneracy remains; Band 10 could break it | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Carbonaceous (cosmic carbon) dust rejected because its flat albedo cannot make the Band 7 dip  
  > "It indicates that the cosmic carbon dust might not account for the observed intensity profile of the inner region of the TW Hya disk which has a dip at Band 7." (4.1 Dependence on the opacity model)
- How they decided it was enough: _not stated_
- Limitation (authors): Flux calibration uncertainties may be larger than official values; absolute opacity is uncertain.  
  > "We confirmed that the actual uncertainty might be potentially larger than the official value but has little impact on our conclusion." (2.2 SED analysis)
- Caveat (inferred, ours): No quantitative goodness-of-fit; models compared by eye on a coarse grid
- Caveat (inferred, ours): Results depend on DSHARP opacity and fixed temperature/density profiles
- Caveat (inferred, ours): Central pixel intensity mixes emission out to ~10 au at 20 au resolution

## Reproducibility

- Data public (paper): Public ALMA archival images/data  
  > "we downloaded the product images provided by ALMA from the ALMA data archive system" (2.1 ALMA data and analysis)
- Products in archive: _not stated_
- Missing: CASA version
- Missing: Band 4/6/7 images from Tsukagoshi papers' processing
- Missing: RADMC-3D setup details (stellar spectrum, photon counts)
- Data volume (inferred): ~50-200 GB for raw archival data; ~1 GB if product images used
- Score (inferred): 3/5, Public data and clear model parameters, but processing details and heating setup are missing and comparison is by eye.
- Rediscovery candidate: no, Recipe incomplete (imaging inherited, heating setup unstated) and fit is qualitative.

## Links

- Method: (cite: Birnstiel2018) (DSHARP opacities)
- Method: (cite: Tsukagoshi2016) (Band 4 and 6 calibration/imaging)
- Companion: (cite: Tsukagoshi2019) (Band 7 image)
- Companion: (cite: Liu2019) (scattering explanation for low spectral index)
- Related: DSHARP

## Checks

```json
{
 "quotes": 61,
 "quotes_ok": 61,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 11,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 37,
  "rate": 0.529
 },
 "evidence_ok": true
}
```

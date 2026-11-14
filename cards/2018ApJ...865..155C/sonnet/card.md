# Constraining Gas-phase Carbon, Oxygen, and Nitrogen in the IM Lup Protoplanetary Disk

`2018ApJ...865..155C` | The Astrophysical Journal 2018 | first author: Cleeves, L. Ilsedore | arXiv: 1808.10682 | DOI: 10.3847/1538-4357/aade96

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: What are the gas-phase C/O and N/O ratios in the warm molecular layer of the IM Lup disk, as constrained by C2H, HCN and H13CN emission?  
  > "we explore what C/O and N/O abundance ratios are required in the disk’s warm molecular layer to reproduce the observed C$_2$H, HCN, and HC$^{13}$N line intensities." (Introduction)
- Target **IM Lup**: coordinates _not stated_; z/distance 161 pc  
  > "The simulations assume a fixed distance of 161 pc (cite: gaia), and a fixed inclination of the disk midplane of $48^\circ$ (cite: cleeves2016im)." (3.3 Model - Observation Comparison); distance from Gaia DR1 (cite: gaia)  
  > "The simulations assume a fixed distance of 161 pc (cite: gaia), and a fixed inclination of the disk midplane of $48^\circ$ (cite: cleeves2016im)." (3.3 Model - Observation Comparison)

## Data provenance

- ALMA projects: 2015.1.00964.S, 2013.1.00226.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: H13CN: 3.6 mJy/beam per channel in 0.5 km/s channels (non-detection)  
  > "the H$^{13}$CN $J=3-2$ line was not detected at a per channel RMS of 3.6 mJy per beam in 0.5 km s$^{-1}$ channels" (2.1 ALMA Observations and Data Reduction)
- time on source: 12 minutes on source, 41 antennae (C2H)  
  > "on 01 May 2016 with 41 antennae for 12 minutes on source." (2.1 ALMA Observations and Data Reduction)
- observing dates: 01 May 2016 (C2H)  
  > "on 01 May 2016 with 41 antennae for 12 minutes on source." (2.1 ALMA Observations and Data Reduction)
- pi or archival as stated: C2H: Cycle 3 program (PI: Öberg); HCN and H13CN archival from earlier survey  
  > "IM Lup was observed as part of a survey of nitrogen isotope chemistry and deuterium chemistry presented in (cite: guzman2017) and (cite: huang2017), respectively." (2.1 ALMA Observations and Data Reduction)
- Line: C2H N=3-2, J=5/2-3/2 F=2-1 and F=3-2 pair (262.067 and 262.065 GHz)
- Line: C2H N=3-2, J=7/2-5/2 F=3-2 and F=4-3 pair (262.006 and 262.004 GHz)
- Line: HCN J=3-2 (not stated)
- Line: H13CN J=3-2 (not stated)
- Other facility **Swift**: UVM2 flux density of IM Lup used to normalize the UV template  
  > "we use the UV spectral template of TW Hya normalized to the observed *Swift* UVM2 flux density from IM Lup" (3.1 Disk Physical Model)
- External data: Disk physical structure (surface density, scale height, dust mass 0.0017 Msun, mm edge 313 AU) and CO depletion  
  > "We use the underlying disk structure derived in (cite: cleeves2016im), which we summarize here." (3.1 Disk Physical Model) [from (cite: cleeves2016im)]
- External data: Integrated X-ray luminosity 4.3e30 erg/s  
  > "normalized to the observed integrated X-ray luminosity provided in (cite: gunther2010) of $4.3\times10^{30}$ erg s$^{-1}$." (3.1 Disk Physical Model) [from (cite: gunther2010)]
- External data: HCN and H13CN J=3-2 ALMA data  
  > "The observations of HCN $J=3-2$ and H$^{13}$CN $J=3-2$ are presented in (cite: huang2017) (cite: guzman2017) and are not reproduced here." (2.1 ALMA Observations and Data Reduction) [from (cite: huang2017); (cite: guzman2017)]
- External data: 12C/13C = 70  
  > "assume an isotope ratio of $\rm ^{12}C/^{13}C=70$ (cite: prantzos1996)" (3.2 Chemical Modeling Procedure) [from (cite: prantzos1996)]
- External data: Water ice abundance 8e-5 per H  
  > "$\chi({\rm H_2O_{ice}}) = 8\times10^{-5}$ per H (cite: boogert2015)" (3.2.2 Model abundances) [from (cite: boogert2015)]
- Simulation/model as data: Grid of 27 chemical models (9 C/O x 3 cosmic-ray rates) post-processed with LIME  
  > "The total model grid size is nine values of C/O and three values of $\zeta_{\rm CR}$ for 27 models total." (3.3 Model - Observation Comparison)

## Processing

### Calibration

- pipeline or manual: Calibrated by ALMA/NAASC staff  
  > "The observations were calibrated by ALMA/NAASC staff using J1517-2422 for the bandpass, J1610-3958 for the phase and amplitude, and Titan for the flux calibration." (2.1 ALMA Observations and Data Reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan  
  > "J1517-2422 for the bandpass, J1610-3958 for the phase and amplitude, and Titan for the flux calibration." (2.1 ALMA Observations and Data Reduction)
- flux scale uncertainty: 10%  
  > "Uncertainties are quadrature combined RMS scatter and 10% calibration uncertainty." (Table 1)
- self calibration: One round of phase self-cal on in-window continuum, 30 s solint, polarizations averaged  
  > "For the self-calibration, we use a solution interval of 30 seconds and average both polarizations." (2.1 ALMA Observations and Data Reduction)

### Imaging

- task: CASA 4.7 clean  
  > "Images are generated using CASA 4.7 (cite: mcmullin2007) and the clean task." (2.1 ALMA Observations and Data Reduction)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: 1 arcsec taper for moment-0/channel maps  
  > "Figure [1](#fig:allchannel) shows velocity-averaged channel maps and moment-0 maps tapered to 1” to improve signal to noise." (2.1 ALMA Observations and Data Reduction)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uv-plane subtraction of continuum estimated from line-free channels in same spectral window  
  > "The continuum is estimated from line-free channels within the same spectral window, which is then subtracted in the $uv$-plane" (2.1 ALMA Observations and Data Reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Disk physical structure, temperature, stellar parameters, external field  
  > "We use the underlying disk structure derived in (cite: cleeves2016im), which we summarize here." (3.1 Disk Physical Model) [from (cite: cleeves2016im)]
- Chemical code  
  > "using a time-evolving gas-grain model first presented in (cite: fogel2011) and updated and expanded in (cite: cleeves2014par)." (3.2 Chemical Modeling Procedure) [from (cite: fogel2011); (cite: cleeves2014par)]
- Cosmic-ray ionization rate model values  
  > "“Solar System minimum” (ssm; $\zeta_{\rm CR}=1.3\times10^{-18}$ s$^{-1}$ per H$_2$) from (cite: cleeves2013a)." (3.2 Chemical Modeling Procedure) [from (cite: cleeves2013a)]

### Not stated but needed to reproduce (our reading)

- clean parameters (weighting, robust, cell, image size, mask, channel width) for C2H
- line-free channel ranges
- spectral setup and array configuration of C2H and archival HCN/H13CN data
- target coordinates
- visibility weighting and chi2 details, uv-range
- full chemical network and disk model files
- LIME settings (photon number, grid points)
- how the HCN archival data were calibrated

## Analysis recipe

1. **Calibrate, self-calibrate and image C2H data**: Staff calibration, one round of phase self-cal, uv continuum subtraction, clean imaging, moment-0 maps and aperture-integrated fluxes  
  > "We performed one additional round of phase self-calibration using the continuum within the spectral window containing the line." (2.1 ALMA Observations and Data Reduction)
   - software: CASA
   - parameter: 4 arcsec circular aperture for disk-integrated flux  
  > "integrated within a 4” radius circular aperture" (2.1 ALMA Observations and Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Run chemical models over C/O and cosmic-ray grid**: Time-evolving gas-grain chemistry on fixed disk structure, varying initial C/O and zeta_CR; N2 reduced for N depletion  
  > "The simulations are run over 0.5 Myr, corresponding to the lower age limit of IM Lup." (3.2 Chemical Modeling Procedure)
   - software: gas-grain chemical code
   - parameter: zeta_CR = 1e-20, 2e-19, 1.3e-18 s^-1; 9 C/O values  
  > "“T Tauri minimum modulation” (ttm; $\zeta_{\rm CR}=1.0\times10^{-20}$ s$^{-1}$ per H$_2$)" (3.2 Chemical Modeling Procedure)
   - assumption: CO abundance 7e-6 per H; N 7.5e-5 per H fiducial  
  > "we require there to be sufficient elemental C and O to be able to produce a CO abundance of $7\times10^{-6}$, but not excess." (3.2.2 Model abundances)
   - fitting: _not stated_
   - validation: Tested different carriers of C, N, O give similar abundances within a few percent  
  > "achieve similar output abundances in the warm molecular layer ($z/r\gtrsim0.2$) to within a few percent." (3.2.2 Model abundances)
3. **Simulate line emission and compare to visibilities**: Non-LTE LIME radiative transfer, sampled at observed uv with vis_sample, chi2 comparison  
  > "we compare the $\chi^2$ between the observed and simulated continuum subtracted visibilities." (3.3 Model - Observation Comparison)
   - software: LIME, vis_sample
   - parameter: Turbulent velocity 100 m/s; emission limited to 500 AU; 40x oversampled spectral resolution  
  > "a fixed turbulent velocity of 100 m s$^{-1}$." (3.3 Model - Observation Comparison)
   - assumption: distance 161 pc, inclination 48 deg, Keplerian around 1 Msun  
  > "The input gas velocities include Keplerian rotation around a solar mass star" (3.3 Model - Observation Comparison)
   - fitting: _not stated_
   - validation: Compared HCN and H13CN non-detection for consistency  
  > "C/O of $\gtrsim1$ predicts *detectable* H$^{13}$CN $J=3-2$ image-plane emission, regardless of cosmic ray ionization rate, inconsistent with observations." (4.2 Fits to C2H Observations)
4. **Constrain nitrogen depletion**: At C/O=0.81 reduce N2 abundance and compare HCN chi2  
  > "Taking bulk $\rm C/O=0.81$ from Section [4.2](#c2hfit), we reduce the nitrogen abundance from the fiducial value" (4.3 Fits to HCN and H13CN Observations)
   - software: LIME
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7: Imaging with clean  
  > "Images are generated using CASA 4.7 (cite: mcmullin2007) and the clean task." (2.1 ALMA Observations and Data Reduction)
- **LIME** 1.8: Non-LTE radiative transfer  
  > "using the non-LTE radiative transfer code LIME v1.8" (3.3 Model - Observation Comparison)
- **vis_sample** : Sampling model channel maps at observed uv points  
  > "the `vis_sample` package (cite: loomis2018)[^2] is used to sample the LIME channel maps at the same spatial frequencies as were observed" (3.3 Model - Observation Comparison)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| C2H J=5/2-3/2 blended pair flux | 0.56 | 0.08 | Jy km/s | 1 | / $J=\sfrac{5}{2} - \sfrac{3}{2}$ $F=2-1$ / 262.067 /    $0.56  \pm 0.08$    / |
| C2H J=7/2-5/2 blended pair flux | 0.76 | 0.11 | Jy km/s | 1 | / $J=\sfrac{7}{2} - \sfrac{5}{2}$ $F=3-2$ / 262.006 /     $0.76\pm 0.11$     / |
| Best-fit bulk C/O (both pairs) | 0.81 | not stated | dimensionless | 3 | Combining both line pairs favors the $\rm C/O=0.81$ model. |
| Water ice depletion factor | 50 | not stated | dimensionless | 3 | This C/O ratio corresponds to a water ice depletion factor of $50\times$ |
| Nitrogen depletion (allowed at high zeta_CR) | 0 to 4 | not stated | dimensionless | 4 | favors anywhere between no and $4\times$ reduction in bulk nitrogen. |
| Gas-phase N/O | ~10 | not stated | dimensionless | 4 | The N/O ratio on the other hand is $\gg 1$ throughout the disk atmosphere, and $\sim 10$ |

## Qualitative findings

- C2H is insensitive to the cosmic ray ionization rate, but strongly sensitive to C/O  
  > "C$_2$H is essentially unaffected by the cosmic ray ionization rate for the three model values considered." (4.1 Chemical Model Results)
- Model C2H high-velocity emission is weaker than observed, suggesting more carbon in the inner disk  
  > "The high velocity emission of C$_2$H is weaker in the models than in the data." (5.2 Gas-phase C/O and N/O constraints)

## Claim tuples

- H: Is the C/O ratio in IM Lup's molecular layer super-solar? | E: Fit C2H visibilities with grid of chemical models | R: C/O ~0.81 best fit | F: Oxygen is depleted via water ice sequestration; C/O above solar | **supported**
- H: Is nitrogen depleted like CO? | E: Reduce N2 in models and compare to HCN/H13CN | R: Best fit has no N depletion | F: N remains largely unprocessed; abundance variations rather than gas mass deficit | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: C/O >~1 rejected because H13CN would be detectable  
  > "C/O of $\gtrsim1$ predicts *detectable* H$^{13}$CN $J=3-2$ image-plane emission" (4.2 Fits to C2H Observations)
- How they decided it was enough: _not stated_
- Limitation (authors): No radial/vertical abundance variation fit given S/N; cannot exclude some missing gas mass  
  > "Given the signal to noise of the C$_2$H data, we did not attempt to radially or vertically vary the carbon, oxygen, and nitrogen abundances spatially in our fitting" (5.2 Gas-phase C/O and N/O constraints)
- Caveat (inferred, ours): No uncertainties on best-fit C/O; coarse 9-point grid
- Caveat (inferred, ours): Fixed physical structure and temperature; model degeneracies with disk structure
- Caveat (inferred, ours): Coarse C/O sampling and no marginalization
- Caveat (inferred, ours): Only 12 min of C2H data

## Reproducibility

- Data public (paper): ALMA project codes given  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00964.S and ADS/JAO.ALMA#2013.1.00226.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Proprietary-ish chemical code and disk model files not released
- Missing: Imaging parameters
- Missing: Grid chi2 values
- Data volume (inferred): ~10-30 GB
- Score (inferred): 3/5, Data public and approach clear, but custom chemical code, imaging parameters and fitting details are missing.
- Rediscovery candidate: no, Needs unreleased chemical model and disk structure from prior paper.

## Links

- Method: (cite: fogel2011) (Chemical model)
- Method: (cite: brinch2010) (LIME)
- Method: (cite: loomis2018) (vis_sample)
- Companion: (cite: cleeves2016im) (Disk structure and CO constraints)
- Companion: (cite: huang2017) (HCN/H13CN observations)
- Companion: (cite: guzman2017) (HCN/H13CN observations)

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 43,
  "rate": 0.558
 },
 "evidence_ok": true
}
```

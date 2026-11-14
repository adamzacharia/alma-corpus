# ALMA Observations of Molecular Absorption in the Gravitational Lens PMN 0134-0931 at z = 0.7645

`2018ApJ...864...73W` | The Astrophysical Journal 2018 | first author: Wiklind, Tommy | arXiv: 1804.05377 | DOI: 10.3847/1538-4357/aad4ac

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: Do the lensing galaxies of PMN 0134-0931 at z=0.7645 show CO and HCO+ J=2-1 absorption along different lensed lines of sight, and what do the kinematics and column densities reveal about the molecular gas?  
  > "The CO J=2–1 and HCO$^+$ J=2–1 lines are seen in absorption along two different lines of sight to lensed images of the background QSO." (abstract)
- Target **PMN 0134-0931**: coordinates A-C component 01:34:35.668 -09:31:02.909 (J2000, from Table)  
  > "The lens itself has not been reliably detected as it is overpowered by the glare of the background, $z_s$=2.2 QSO" (3 The Gravitational Lens PMN 0134-0931); "A–C & 90.09 & 01:34:35.668 & -09:31:02.909" (Table 3); z/distance lens z=0.7645; background QSO z_s=2.2  
  > "The lens itself has not been reliably detected as it is overpowered by the glare of the background, $z_s$=2.2 QSO" (3 The Gravitational Lens PMN 0134-0931); "A–C & 90.09 & 01:34:35.668 & -09:31:02.909" (Table 3); distance from Absorption redshift; z_s from Gregg et al. 2002; Winn & Keeton 2003  
  > "The lens itself has not been reliably detected as it is overpowered by the glare of the background, $z_s$=2.2 QSO" (3 The Gravitational Lens PMN 0134-0931); "A–C & 90.09 & 01:34:35.668 & -09:31:02.909" (Table 3)

## Data provenance

- ALMA projects: 2015.1.00582.S
- bands: Band 3 (CO J=2-1) and Band 4 (HCO+ J=2-1)  
  > "redshifted into ALMA bands 3 and 4, respectively (hereafter B3 and B4)" (2 Observations)
- frequencies and spectral setup: Two 1.875 GHz basebands per band, 1920 channels, 976.563 kHz; plus two 2 GHz continuum basebands with 128 channels; high-res centered at 101.007 and 130.276 GHz  
  > "For each band we used two basebands of width 1.875 GHz and 1920 channels giving a spectral resolution of 976.563 kHz." (2 Observations)
- continuum bandwidth: ~4 GHz combined, centered 91 GHz (B3) and 140 GHz (B4)  
  > "each with a combined bandwidth of $\sim$4 GHz" (2 Observations)
- arrays: _not stated_
- configurations: _not stated_
- baselines: Longest baseline 3.14 km (B3), 2.48 km (B4)  
  > "The longest baseline was 2.48 km, with a nominal angular resolution of 0$\,.\!\!^{\prime\prime}$28." (2 Observations)
- angular resolution: nominal 0.35" (B3), 0.28" (B4); best continuum 0.24"x0.18" at 140 GHz uniform  
  > "The highest angular resolution (0$\,.\!\!^{\prime\prime}$24$\times$0$\,.\!\!^{\prime\prime}$18) is obtained at 140 GHz using uniform weighting" (4.1 Millimeter Continuum)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: ~52 min (B3), ~67 min (B4)  
  > "The total on-source time for the B4 observation was $\sim$67 minutes." (2 Observations)
- observing dates: 2016 Sept 9 (B4), Sept 17 and 19 (B3); Cycle 3  
  > "September 9 (B4), September 17 and 19 (B3), 2016 under ALMA Cycle 3 project 2015.1.00582.S" (2 Observations)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (not stated)
- Line: HCO+ J=2-1 (not stated)
- Line: HCN J=2-1 (177.263 GHz)
- Line: HNC J=2-1 (181.325 GHz)
- External data: Radio continuum component positions and flux densities (15 GHz, spectral index -0.69) used for lens comparison and covering factors  
  > "The location and relative flux levels are taken from Winn & Keeton (2003)." (4.1 Millimeter Continuum) [from Winn & Keeton (2003)]
- External data: OH 1667 MHz 4-component Gaussian fit and HI 21cm profile  
  > "Kanekar et al. (2012) provide a 4-component Gaussian fit to their OH 1667 MHz spectrum" (5.2 Column Density) [from Kanekar et al. (2012)]
- External data: Lens model with two galaxies of similar mass  
  > "The two lensing galaxies, called Gal-N and Gal-S in Keeton & Winn (2003), are of similar mass" (3 The Gravitational Lens PMN 0134-0931) [from Keeton & Winn (2003)]

## Processing

### Calibration

- pipeline or manual: CASA, standard procedures  
  > "The data reduction and calibration was done with the CASA[^3] package following standard procedures." (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0006-0623 (also bandpass), bootstrapped to Solar system objects  
  > "The bright quasar J0006-0623 was used as both bandpass and flux calibrator." (2 Observations)
- flux scale uncertainty: better than ~10%  
  > "The overall flux accuracy is better than $\sim$10% in both B3 and B4." (2 Observations)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5 for spectral cubes; uniform for highest-resolution continuum  
  > "The data cubes used for extracting the spectra were cleaned using Briggs weighting with the robustness set to 0.5." (4.2 Molecular Absorption)
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

- Lens component designation and positions follow Winn & Keeton (2003)  
  > "We use the same designation of the lens components as in Winn & Keeton (2003)." (footnote 4) [from Winn & Keeton (2003)]

### Not stated but needed to reproduce (our reading)

- CASA version
- Phase calibrator and bandpass details beyond names; flagging
- Continuum subtraction / how continuum level in line cubes was determined
- Cell and image size, clean threshold, masking
- Restoring beam sizes of cubes
- Initial guesses and fitting code for Gaussian fits
- Excitation temperature Tx used for column densities
- Rest frequencies of CO and HCO+ used

## Analysis recipe

1. **Image continuum**: Continuum images from continuum basebands; component fluxes and positions tabulated  
  > "The continuum data was used to construct images of the PMN 0134-0931 system." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared positions and flux ratios with radio images of Winn & Keeton (2003)  
  > "Overall, the flux ratios seen at radio frequencies are consistent with our results at millimeter wavelengths" (4.1 Millimeter Continuum)
2. **Extract absorption spectra and fit Gaussians**: Spectra extracted with aperture equal to restoring beam toward A-C and D from Briggs cubes; Gaussian fits  
  > "We used an aperture with the same size as the restoring beam to extract spectra towards the continuum images A-C and D in PMN 0134-0931." (4.2 Molecular Absorption)
   - software: CASA
   - parameter: Briggs robust 0.5; 3 Gaussians for D, 2 for A-C  
  > "The A-C component only requires two Gaussian components to give a good fit." (4.2 Molecular Absorption)
   - fitting: Non-linear Gaussian fit; errors from covariance matrix  
  > "The error estimates of the Gaussian components are derived from the covariance matrix of the non-linear fit." (Table 4)
   - validation: Velocity difference estimated three ways, consistent  
  > "All of these estimates are consistent with each other within the errors" (4.2 Molecular Absorption)
3. **Derive opacity and column densities**: tau = -ln(1-F); LTE column density from integrated opacity  
  > "The observed opacity can be directly derived from the normalized flux $F(\nu)$ shown in Fig. [3](#fig:molabs) as $\tau_{\nu_{obs}} = -\ln{(1 - F(\nu))}$." (4.2 Molecular Absorption)
   - assumption: Covering factor f_c = 1 (lower limits); LTE  
  > "Assuming that $f_{c} = 1$ and consequently, $\tau_{\nu} = \tau_{\nu_{obs}}$" (4.2 Molecular Absorption)
   - fitting: _not stated_
   - validation: _not stated_
4. **CO emission upper limit**: 1.0" aperture spectrum binned to 13.4 km/s; 5 sigma limit on H2 mass  
  > "No emission was detected and assuming a velocity width of 200 km s$^{-1}$ the 5$\sigma$ upper limit to the molecular mass is $3.5 \times 10^{9}$ M$_{\odot}$." (4.3 Molecular Emission)
   - assumption: alpha = 4.6 Msun (km/s pc^2)^-1  
  > "We used $\alpha = 4.6$ M$_{\odot}$ (km s$^{-1}$ pc$^2$)$^{-1}$ for the conversion between CO luminosity and H$_2$ mass." (4.3 Molecular Emission)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Data reduction, calibration and imaging  
  > "The data reduction and calibration was done with the CASA[^3] package following standard procedures." (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Velocity difference between A-C and D absorption | 215 | 8 | km/s | 2 | we adopt $\Delta$v = 215$\pm8$ km s$^{-1}$ |
| CO column density toward D | 2.40e17 | 0.24e17 | cm^-2 | 3 | / D / 4.48 / 0.013 / 70.26 $\pm$ 6.96 / $2.40 \pm 0.24 \times 10^{17}$ / |
| CO column density toward A-C | 1.80e16 | 0.41e16 | cm^-2 | 3 | / CO(J=2-1) / A–C / 4.48 / 0.017 / 5.25 $\pm$ 1.20 / $1.80 \pm 0.41 \times 10^{16}$ / |
| HCO+ column density toward D | 1.73e14 | 0.16e14 | cm^-2 | 3 | / D / 5.79 / 0.070 / 35.14 $\pm$ 3.21 / $1.73 \pm 0.16 \times 10^{14}$ / |
| HCO+ column density toward A-C | 3.55e13 | 0.32e13 | cm^-2 | 3 | / A–C / 5.79 / 0.036 / 7.20 $\pm$ 0.65 / $3.55 \pm 0.32 \times 10^{13}$ / |
| N_CO/N_HCO+ ratio A-C and D | ~500 (A-C), ~1500 (D) | not stated | dimensionless | 3 | The ratio of $N_{CO}/N_{HCO^+}$ is $\sim$500 towards the A-C component and $\sim$1500 towards the D component. |
| Average mm spectral index | -1.6 | not stated | dimensionless | 1 | The average spectral index is $\alpha = -1.6$ |
| 5 sigma upper limit on molecular mass | 3.5e9 | not stated | Msun | 4 | the 5$\sigma$ upper limit to the molecular mass is $3.5 \times 10^{9}$ M$_{\odot}$ |

## Qualitative findings

- CO and HCO+ absorption toward D is unusually strong, suggesting dense molecular gas; widths suggest inclined disk with flat rotation curve  
  > "It is plausible that the second line of sight probes denser molecular gas than what is normally the case for absorption." (abstract)

## Claim tuples

- H: Do both lensed sightlines show molecular absorption with a velocity offset? | E: Extract CO and HCO+ spectra toward A-C and D and fit Gaussians | R: Offset 215±8 km/s; widths ~200 km/s | F: Possible rotation of a lensing galaxy, though interaction may disturb kinematics | **partially**
- H: Is the gas along D typical diffuse gas? | E: Compute column densities and ratios | R: N_CO/N_HCO+ ~1500 vs ~500 for A-C | F: D probes denser molecular gas | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Briggs robust 0.5 maximizes sensitivity while still separating continuum components  
  > "but is necessary to maximize the sensitivity while still retaining sufficient angular resolution to separate the continuum components" (4.2 Molecular Absorption)
- Alternative: Uniform weighting for spectra rejected as too noisy  
  > "A uniform weighting produced noisy spectral data" (4.2 Molecular Absorption)
- How they decided it was enough: _not stated_
- Limitation (authors): Lens galaxy location and orientation unknown, limiting interpretation  
  > "The interpretation is currently hampered by the lack of accurate information on the location and orientation of the lensing galaxies." (5.2 Column Density)
- Caveat (inferred, ours): Covering factor assumed unity; N_CO/N_HCO+ may reflect f_c<1
- Caveat (inferred, ours): Excitation temperature for column densities not stated
- Caveat (inferred, ours): Continuum level taken from line basebands; method unclear

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: CASA version
- Missing: Imaging parameters
- Missing: Tx and rest frequencies for column densities
- Data volume (inferred): ~50-100 GB
- Score (inferred): 3/5, Public ALMA project and clear recipe, but many processing and imaging details unstated.
- Rediscovery candidate: yes, Public data, simple spectra, numeric results in tables.

## Links

- Companion: Kanekar et al. 2005 (Earlier HI, OH and HCO+ observations of the same lens)
- Companion: Winn & Keeton (2003) (Radio continuum of lens components)

## Checks

```json
{
 "quotes": 54,
 "quotes_ok": 54,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 34,
  "rate": 0.515
 },
 "evidence_ok": true
}
```

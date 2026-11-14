# The Flared Gas Structure of the Transitional Disk around Sz 91

`2019ApJ...871....5T` | The Astrophysical Journal 2019 | first author: Tsukagoshi, Takashi | arXiv: 1811.12036 | DOI: 10.3847/1538-4357/aaf4f1

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Can the twin-line pattern in the CO channel maps of the Sz 91 transitional disk be explained by a flared gas disk combined with a dust ring, and is CO depleted in the cold midplane?  
  > "We perform the radiative transfer calculations using RADMC-3D, to check whether the twin-line pattern can be reproduced under the assumption that the flared gas disk has a power-law form for the column density and $T_\mathrm{gas}=T_\mathrm{dust}$." (abstract)
- Target **Sz 91**: coordinates _not stated_; z/distance 158 pc  
  > "In this paper, we adopt a distance of 158 pc." (Introduction); "the distance to the source is measured to be 156–160 pc based on the GAIA data release 2" (Introduction); distance from Gaia DR2 (Bailer-Jones et al. 2018)  
  > "In this paper, we adopt a distance of 158 pc." (Introduction); "the distance to the source is measured to be 156–160 pc based on the GAIA data release 2" (Introduction)

## Data provenance

- ALMA projects: 2012.1.00761.S
- bands: Band 7 (350 GHz)  
  > "The band 7 receiver system was employed to detect the continuum emissions at band 7 (350 GHz)" (Observation)
- frequencies and spectral setup: 4 SPWs; two line SPWs of 117.188 MHz bandwidth, 30.518 kHz channels (~0.05 km/s); two continuum SPWs of 1.875 GHz each  
  > "the bandwidth and the channel spacing were 117.188 MHz and 30.518 kHz, respectively, which correspond to a velocity resolution of $\sim0.05$ km s$^{-1}$." (Observation)
- continuum bandwidth: 3.75 GHz total  
  > "with a bandwidth of 1.875 GHz each, resulting in a total bandwidth of 3.75 GHz" (Observation)
- arrays: _not stated_
- configurations: C34-7(6), 42 antennae  
  > "42 antennae were operated, and the antenna configuration was C34-7(6), resulting in a maximum baseline length of $\sim$1.6 km." (Observation)
- baselines: _not stated_
- angular resolution: 0.134''x0.104'', restored to 0.14'' circular beam  
  > "The resolution of the CLEAN image achieved was $0.134\ensuremath{''}\times0.104\ensuremath{''}$" (Observation)
- max recoverable scale: _not stated_
- sensitivity: continuum 61.2 uJy/beam; CO 6.0 and HCO+ 6.7 mJy/beam (0.2 km/s channels)  
  > "The rms noise levels of the CLEAN images were 6.0 and 6.7 mJy beam$^{-1}$ for CO and HCO$^{+}$, respectively." (Observation)
- time on source: 34 min per execution block, 1.5 h total (three EBs)  
  > "The total integration time for the execution blocks was 34 min each, i.e., 1.5 h in total." (Observation)
- observing dates: July 20 and 21, 2015  
  > "were conducted on July 20 and 21, 2015." (Observation)
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (345.796 GHz)
- Line: HCO+ J=4-3 (356.734 GHz)
- Other facility **Subaru (Ks-band scattered light image from earlier work)**: Ks band image overlaid on continuum  
  > "superposed on the $K_s$ band ($\lambda=2.15\ensuremath{\mu}m$) scattered light image obtained by (cite: bib:tsukagoshi2014)" (3.1 Band 7 Continuum Emission)
- External data: Stellar mass/radius/Teff from Siess evolutionary tracks, with Gaia distance  
  > "using the stellar evolutional tracks of (cite: bib:siess2000)" (Introduction) [from (cite: bib:siess2000)]
- External data: Dust opacity table  
  > "The dust opacity used in our calculations follows that of (cite: bib:aikawa2006)" (4.1.1 Model Setup) [from (cite: bib:aikawa2006)]
- External data: Turbulent velocity broadening 120 m/s  
  > "fixed to be 120 m s$^{-1}$, according to (cite: bib:canovas2015)" (4.1.1 Model Setup) [from (cite: bib:canovas2015)]
- External data: Molecular abundances CO 1e-4, HCO+ 1e-9  
  > "Those are $10^{-4}$ and $10^{-9}$ for CO and HCO$^{+}$, respectively (cite: bib:qi2011; bib:salter2011)." (4.1.1 Model Setup) [from (cite: bib:qi2011; bib:salter2011)]

## Processing

### Calibration

- pipeline or manual: Reduction script provided by ALMA, run in CASA  
  > "The raw data were calibrated with the reduction script provided by ALMA." (Observation)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Pallas (flux), J1517-2422 (bandpass), J1610-3958 (gain)  
  > "The calibrators of the bandpass character and the absolute flux scale were J1517-2422 and Pallas, respectively." (Observation)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0  
  > "The continuum image was reconstructed by the CLEAN algorithm with the Briggs weighting of a robust parameter of 0." (Observation)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: [0, 0.12, 0.36] arcsec  
  > "We also employed the multiscale CLEAN with scale parameters of \[0, 0.12, 0.36\] arcsec" (Observation)
- continuum subtraction: Visibility-domain subtraction of continuum made from line-free channels  
  > "The visibilities of the line emissions were obtained by subtracting the continuum visibilities." (Observation)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.14'' circular  
  > "The CLEAN images were restored to have the same resolution as in the continuum map, i.e., the beamsize of $0.14\ensuremath{''}$." (Observation)
- final rms: 61.2 uJy/beam continuum  
  > "The rms noise level of the image was measured to be 61.2 $\mu$Jy beam$^{-1}$." (Observation)

### Inherited from earlier work

- Ring visibility fitting with uvfits as done previously  
  > "using the *uvfits* task installed on the *MIRIAD* software, as (cite: bib:canovas2016) has done." (3.1 Band 7 Continuum Emission) [from (cite: bib:canovas2016)]
- Gas temperature profile used for scale height estimate  
  > "If we adopt the temperature distribution in (cite: bib:tsukagoshi2014), $h_\mathrm{g}$ is estimated to be 13.2 au at 95 au radius." (4.1.1 Model Setup) [from (cite: bib:tsukagoshi2014)]

### Not stated but needed to reproduce (our reading)

- Image size and cell size
- Line-free channels used for continuum
- Clean threshold and masks
- CASA version
- Image-domain details of the model-to-data comparison (simobserve parameters, integration times)
- Number of ring-fit parameters/initial values in uvfits
- Grain-size bins and other RADMC-3D settings (grid, wavelengths)

## Analysis recipe

1. **Calibrate and image continuum and lines**: ALMA script calibration in CASA; multiscale CLEAN continuum and continuum-subtracted line cubes at 0.2 km/s  
  > "The line emissions were imaged using the multiscale CLEAN algorithm with the same scale parameters as for the continuum image." (Observation)
   - software: CASA
   - parameter: robust = 0; scales [0, 0.12, 0.36] arcsec; 0.14'' restoring beam  
  > "The continuum image was reconstructed by the CLEAN algorithm with the Briggs weighting of a robust parameter of 0." (Observation)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure dust ring geometry**: Visibility fit with ring model (uvfits in MIRIAD) for axes, PA, inclination; Gaussian fit to radial profiles for ring width  
  > "we performed a visibility fitting with a ring distribution using the *uvfits* task installed on the *MIRIAD* software" (3.1 Band 7 Continuum Emission)
   - software: MIRIAD
   - assumption: Gaussian ring emission for beam deconvolution  
  > "If we assume that the inferred emissions of the dust ring have a gaussian distribution, the beam-deconvolved widths along the major and minor axes" (3.1 Band 7 Continuum Emission)
   - fitting: Least-squares Gaussian fit to radial profiles  
  > "Those widths are determined from the least-squares fitting with a Gaussian function" (3.1 Band 7 Continuum Emission)
   - validation: Compared with Canovas et al. 2016  
  > "The position and inclination angles are comparable to but slightly different from those derived in (cite: bib:canovas2016)" (3.1 Band 7 Continuum Emission)
3. **Characterize line emission**: Channel maps and moment maps (>5 sigma CO, >4 sigma HCO+); inner gas radius from maximum velocities assuming Keplerian rotation  
  > "We made moment maps of the CO emission created by using the $>5\sigma$ data in the channel maps" (3.2 CO(3–2) Emission)
   - assumption: Keplerian rotation, inclination 49 deg  
  > "Assuming that the gas disk is inclined by $49\ensuremath{^\circ}$ from face-on and is undergoing Keplerian rotation" (3.2 CO(3–2) Emission)
   - fitting: _not stated_
   - validation: _not stated_
4. **Radiative transfer disk model with dust ring and flared gas disk**: Thermal Monte Carlo (1e9 photons) for temperature, then LTE line RT with Tgas=Tdust; mock observation via simobserve and clean with same imaging parameters; compare channel maps to data  
  > "the modeled images for the continuum, CO(3–2) and HCO$^{+}$(4–3), were reprocessed to produce similar visibility samplings to the observed one using the *simobserve* task." (4.1.2 Radiative Transfer Calculation and Mock Observation)
   - software: RADMC-3D, CASA
   - parameter: r_pk=95 au, sigma_r=10 au, Sigma_d,0=1.84e-2 g cm^-2, h_d=9.8 au, a_max=1 mm, gas Sigma ~ r^-1 for 8-320 au, h_g=13.2 au (r/95 au)^1.25, gas-to-dust 100  
  > "We set $r_\mathrm{pk}$ and $\sigma_\mathrm{r}$ to 95 au and 10 au, respectively, based on our continuum image" (4.1.1 Model Setup)
   - assumption: Gas-to-dust mass ratio 100; CO abundance 1e-4; HCO+ 1e-9; turbulence 120 m/s; LTE  
  > "we assume that the disk is in local thermodynamic equilibrium and the gas temperature is the same as the dust temperature" (4.1.1 Model Setup)
   - fitting: No formal fit; the authors state the calculation is not a complete fit  
  > "Note that this calculation is not aimed at a complete fitting to the emission." (4. Front and Rear Surfaces of the CO Disk)
   - validation: Visual comparison of model and observed channel maps  
  > "we compare the CO channel maps obtained by our calculations to the observed ones on the same intensity scale" (4.1.3 Result Overview)
5. **Parameter dependence tests**: Vary CO depletion (1e-2, 1e-4, ~0 below 20 K), h_d, turbulent width (40, 80, 240 m/s), and R_in (16, 24 au) and compare channel maps  
  > "we also ran the radiative transfer calculations under the assumption that the CO molecules are depleted by a factor of 10$^{-2}$, 10$^{-4}$ and $\sim0$" (4.1.4 Parameter Dependence)
   - software: RADMC-3D
   - fitting: _not stated_
   - validation: _not stated_
6. **Upper limit on hot inner component**: 3 sigma continuum upper limit converted to dust mass assuming T=180 K and kappa=2.8 cm^2/g  
  > "the dust mass opacity at the observed frequency is 2.8 cm$^2$ g$^{-1}$ (cite: bib:aikawa2006)" (4.2 No Detection of the Hot Component)
   - assumption: Temperature 180 K in cavity  
  > "Adopting that the typical temperature in the cavity is 180 K" (4.2 No Detection of the Hot Component)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration, imaging, simobserve, clean  
  > "The visibility data were reduced and calibrated using the Common Astronomical Software Application (CASA) package" (Observation)
- **MIRIAD** : uvfits ring visibility fitting  
  > "using the *uvfits* task installed on the *MIRIAD* software" (3.1 Band 7 Continuum Emission)
- **RADMC-3D** : Thermal Monte Carlo and line radiative transfer  
  > "we performed radiative transfer calculations using RADMC-3D" (4. Front and Rear Surfaces of the CO Disk)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum total flux density (>3 sigma) | 45.2 | 0.5 | mJy | 2 | The total flux density above $3\sigma$ is measured to be $45.2\pm0.5$ mJy |
| Ring inclination | 49.7 | 0.2 | deg | 2 | The inclination angle $i$ is estimated from the aspect ratio to be $49.7\ensuremath{^\circ}\pm0.2\ensuremath{^\circ}$. |
| Ring position angle | 18.1 | 0.2 | deg | 2 | a position angle of $18.1\ensuremath{^\circ}\pm0.2\ensuremath{^\circ}$ |
| Beam-deconvolved ring widths (major, minor) | 24.6 and 23.7 | not stated | au | 2 | corresponding to 24.6 and 23.7 au, respectively |
| CO(3-2) integrated intensity | 7.6 | 0.1 | Jy km/s | 3 | The total integrated intensity of the CO(3–2) emission is measured to be 7.6$\pm$0.1 Jy km s$^{-1}$ |
| HCO+(4-3) integrated intensity | 3.3 | 0.1 | Jy km/s | 3 | The total integrated intensity is measured to be 3.3$\pm$0.1 Jy km s$^{-1}$. |
| Gas disk inner radius | ~8 | not stated | au | 3 | the maximum velocities of $-0.2$ and $6.6$ km s$^{-1}$ indicate that the gas disk extends to an inner radius of $\sim$8 au. |
| Hot component dust mass 3 sigma upper limit | ~4e-3 | not stated | Earth masses | 6 | is equivalent to a dust mass of $\sim$4 $\times 10^{-3}~M_\ensuremath{\oplus}$ |

## Qualitative findings

- A twin-line pattern appears in the CO channel maps (1.8–4.6 km/s) but not in HCO+.  
  > "We find in the channel maps of the CO emission that there are twin-line patterns showing the front and rear sides of a flared disk, while there are none in the HCO$^{+}$ emission." (Summary)

## Claim tuples

- H: The CO twin-line pattern arises from a flared gas disk with a cold midplane shadowed by the dust ring. | E: RADMC-3D thermal Monte Carlo and LTE line RT, mock-observed and compared with ALMA CO channel maps. | R: Model reproduces the twin-line pattern qualitatively despite differences in distribution and intensity. | F: The dust ring creates a vertical temperature gradient that explains the twin-line pattern. | **supported**
- H: CO is heavily depleted in the cold midplane. | E: Models with CO depletion factors 1e-2, 1e-4 and ~0 below 20 K compared with data. | R: Heavy depletion makes the twin lines symmetric, unlike observed. | F: Heavy CO depletion is unlikely; cold CO absorbs rear emission. | **supported**
- H: The dust ring is geometrically thin. | E: Compare Gaussian FWHM widths along major and minor axes. | R: Widths are similar (0.209'' and 0.205''), rather than differing by cos i. | F: The ring is not geometrically thin, tentatively because it is only marginally resolved. | **partially**
- H: A hot inner dust component exists in the cavity. | E: Search for continuum emission in the inner hole. | R: No emission above 3 sigma (61.2 uJy/beam). | F: No counterpart detected; any hot component must lie within ~2 au in the gas-depleted region. | **partially**

## Reasoning

- Why this data: Higher resolution and sensitivity than earlier ALMA data were needed to resolve the ring width and gas disk.  
  > "the resolution of the previous ALMA observation is comparable to the width of the dust ring and the sensitivity of the observation is insufficient to determine the structure of the gas disk in detail." (Introduction)
- Why this method: _not stated_
- Alternative: Lower scale height h_d dust rings give a narrower twin-line separation, closer to observations, but are inconsistent with the continuum data.  
  > "In contrast to the molecular line emissions, there is some inconsistency in the band 7 continuum data for the lower $h_\mathrm{d}$ cases." (4.1.4 Parameter Dependence)
- How they decided it was enough: _not stated_
- Limitation (authors): The ring width is comparable to the beam, so the estimates are tentative; the model is not a full fit and the HCO+ pattern is not reproduced.  
  > "Note that the estimates are tentative because the width of the dust ring is comparable to the beamsize." (4.1.4 Parameter Dependence)
- Caveat (inferred, ours): Qualitative visual comparison only; no quantitative goodness-of-fit or parameter degeneracy exploration
- Caveat (inferred, ours): CO emission at 4-7 km/s contaminated by the cloud
- Caveat (inferred, ours): Gas-to-dust ratio and abundance assumptions drive the HCO+ mismatch
- Caveat (inferred, ours): Ring width measurement is marginally resolved

## Reproducibility

- Data public (paper): Data identified by ALMA project 2012.1.00761.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00761.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version
- Missing: Exact clean parameters (image/cell size, masks, thresholds)
- Missing: Full RADMC-3D grid and setup, simobserve configuration
- Data volume (inferred): Tens of GB (three EBs, Band 7, high spectral resolution)
- Score (inferred): 3/5, Data public and the imaging and model parameters are largely given, but the model comparison is qualitative and several details are missing.
- Rediscovery candidate: no, The main result is a qualitative model-to-data comparison, although the ring parameters and fluxes are numeric.

## Links

- Method: (cite: bib:canovas2016) (Ring visibility fitting approach)
- Method: (cite: bib:aikawa2006) (Dust opacity)
- Companion: (cite: bib:tsukagoshi2014) (Earlier SMA/Subaru observations and hot component)
- Companion: (cite: bib:canovas2015) (Earlier ALMA observations)

## Checks

```json
{
 "quotes": 67,
 "quotes_ok": 67,
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
  "facts": 80,
  "stated": 49,
  "rate": 0.613
 },
 "evidence_ok": true
}
```

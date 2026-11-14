# Unlocking the secrets of the midplane gas and dust distribution in the young hybrid disc HD 141569

`2018A&A...615L..10M` | Astronomy and Astrophysics 2018 | first author: Miley, J. M. | arXiv: 1805.02476 | DOI: 10.1051/0004-6361/201833381

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, debris_disks
- Question: What are the mass and spatial structure of the gas and dust in the midplane of the hybrid disc HD 141569, and how does it compare with debris, hybrid and protoplanetary discs?  
  > "This work aims to place the mass and spatial structure of the disc midplane in the context of the debris, hybrid and protoplanetary discs." (abstract)
- Target **HD 141569**: coordinates _not stated_; z/distance 111±1 pc  
  > "a B9-A0 type, 5 Myr old pre-main sequence Herbig star at a GAIA distance of 111$\pm$1 pc" (Introduction); distance from GAIA (Lindegren2016Gaia1)  
  > "a B9-A0 type, 5 Myr old pre-main sequence Herbig star at a GAIA distance of 111$\pm$1 pc" (Introduction)

## Data provenance

- ALMA projects: 2015.1.01600.S
- bands: Band 6 (1.3 mm)  
  > "Our ALMA observations in Band 6 were taken on 2016, May 16" (Observations and Results)
- frequencies and spectral setup: velocity resolution 0.166 km/s (13CO), 0.333 km/s (C18O)  
  > "The velocity resolution is 0.166 km/s for $^{13}$CO and 0.333 km/s for C$^{18}$O" (Observations and Results)
- continuum bandwidth: 4 GHz  
  > "The total effective continuum bandwidth was 4 GHz." (Observations and Results)
- arrays: 39 antennas of 12 m  
  > "39 antennas of 12 m diameter were employed" (Observations and Results)
- configurations: _not stated_
- baselines: 16 m to 640 m  
  > "providing baseline lengths ranging from 16 m to 640 m" (Observations and Results)
- angular resolution: 0.65" (72 au) continuum; 0.71" (79 au) 13CO and C18O  
  > "This produced a synthesized beam size of 0$\ensuremath{''}$65 (72 au) for the continuum and 0$\ensuremath{''}$71 (79 au) for $^{13}$CO and C$^{18}$O." (Observations and Results)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2016 May 16  
  > "Our ALMA observations in Band 6 were taken on 2016, May 16" (Observations and Results)
- pi or archival as stated: PI Panić  
  > "(PI Panić, ID 2015.1.01600.S)" (Observations and Results)
- Line: 13CO J=2-1 (not stated)
- Line: C18O 2-1 (not stated)
- Other facility **ALMA 12CO(3-2) (White et al. 2016)**: published 12CO(3-2) data used for optical depth  
  > "In the analysis of our data we use the available $^{12}$CO(3-2) data published in (cite: White2016ALMADISK)." (footnote 2)
- External data: 12CO(3-2) data, PA=-9 deg and inclination=55 deg  
  > "we adopt the values of the $^{12}$CO disc, PA=-9$^{\circ}$ and inclination=55$^{\circ}$ (cite: White2016ALMADISK)" (Observations and Results) [from (cite: White2016ALMADISK)]
- External data: dust opacity 1.15 cm2/g for mm grains  
  > "an opacity, $\kappa_\nu$, corresponding to mm size grains of 1.15 cm$^{2}$g$^{-1}$ (cite: Draine2006OnDisks)" (Discussion) [from (cite: Draine2006OnDisks)]
- External data: VLA flux of 54 μJy used for free-free extrapolation  
  > "we extrapolate from VLA flux of 54 $\mu$Jy (cite: MacGregor2016CONSTRAINTSDISKS)" (Discussion) [from (cite: MacGregor2016CONSTRAINTSDISKS)]
- External data: ISM abundances 12CO/13CO=77, 12CO/H2=1e-4  
  > "assume ISM abundances of $^{12}$CO/$^{13}$CO = 77 and $^{12}$CO/H$_2$=10$^{-4}$ (cite: Wilson1994AbundancesMedium)" (Discussion) [from (cite: Wilson1994AbundancesMedium)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline  
  > "The data were flagged and calibrated following the ALMA-pipeline data reduction." (Observations and Results)
- casa version: CASA 4.7.1  
  > "Using CASA 4.7.1, we subtracted the continuum emission in the uv-space." (Observations and Results)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (bandpass J1550+0527, phase J1733-1304)  
  > "Titan was used as the flux calibrator, J1550+0527 and J1733-1304 were used as the bandpass and phase calibrators respectively." (Observations and Results)
- flux scale uncertainty: 15%  
  > "the uncertainties correspond to a $\pm$15% flux calibration uncertainty applied to all ALMA observations" (Discussion)
- self calibration: _not stated_

### Imaging

- task: clean algorithm  
  > "Images were created using the clean algorithm (cite: Rau2011AInterferometry)" (Observations and Results)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "we adopt natural weighting to prioritise the collection of signal" (Observations and Results)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: in uv-space  
  > "we subtracted the continuum emission in the uv-space" (Observations and Results)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 12CO and 13CO convolved with 13CO synthesized beam for optical depth  
  > "We convolve both the $^{12}$CO and $^{13}$CO images with the synthesized beam of the $^{13}$CO image" (Gas emission)
- final beam: _not stated_
- final rms: continuum 0.11 mJy/beam; 13CO 0.04 and C18O 0.03 Jy km/s/beam  
  > "Rms noise level in the continuum image is 0.11 mJy/beam, and in the $^{13}$CO and C$^{18}$O channel maps rms was 0.04 and 0.03 Jy km/s/beam respectively." (Observations and Results)

### Inherited from earlier work

- optical depth method from 12CO/13CO ratio  
  > "following the method used in, e.g. (cite: Schwarz2016THEISOTOPOLOGUES)" (Gas emission) [from (cite: Schwarz2016THEISOTOPOLOGUES)]
- velocity range for 13CO integrated map taken from 12CO  
  > "over the known range of velocities in which $^{12}$CO is seen (cite: Flaherty2016RESOLVEDDISK; White2016ALMADISK)" (Observations and Results) [from (cite: Flaherty2016RESOLVEDDISK; White2016ALMADISK)]

### Not stated but needed to reproduce (our reading)

- Spectral windows and rest frequencies
- Clean threshold, mask, image size and cell size
- Velocity range and integration limits for 13CO moment map
- Line-free channels for continuum subtraction
- Exact 13CO integrated flux and 12CO(3-2) data processing
- Excitation/partition treatment used in gas mass formula
- Details of noise-curve regions

## Analysis recipe

1. **Calibrate and image continuum and CO lines**: ALMA pipeline calibration, uv continuum subtraction, clean with natural weighting  
  > "The data were flagged and calibrated following the ALMA-pipeline data reduction." (Observations and Results)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Radial profiles**: Azimuthal averaging in radial bins after deprojection with 12CO disc PA and inclination; noise from emission-free regions  
  > "We perform azimuthal averaging in radial bins of 0$\ensuremath{''}$12 for the $^{13}$CO and 1.3mm maps, and 0$\ensuremath{''}$15 for $^{12}$CO." (Observations and Results)
   - parameter: bins 0.12" (13CO, 1.3 mm), 0.15" (12CO)  
  > "radial bins of 0$\ensuremath{''}$12 for the $^{13}$CO and 1.3mm maps, and 0$\ensuremath{''}$15 for $^{12}$CO" (Observations and Results)
   - assumption: PA=-9 deg, inclination=55 deg  
  > "PA=-9$^{\circ}$ and inclination=55$^{\circ}$" (Observations and Results)
   - fitting: _not stated_
   - validation: noise curves from azimuthally averaged emission-free regions  
  > "This method is more robust than simply taking the variation in an elliptical bin and does not rely on any predefined disc models." (Observations and Results)
3. **Minimum dust masses**: Optically thin M=F d^2/(kappa B(T))  
  > "$M_{dust}= \frac{F_\nu~d^2}{\kappa_\nu~B_\nu(T)}$" (Dust emission)
   - assumption: T=20 K, kappa=1.15 cm2/g, d=111 pc, all emission thermal  
  > "taking a midplane disc temperature of 20 K, an opacity, $\kappa_\nu$, corresponding to mm size grains of 1.15 cm$^{2}$g$^{-1}$" (Dust emission)
   - fitting: _not stated_
   - validation: free-free contribution estimated by extrapolating VLA flux, ~3%  
  > "the free-free flux at 1.3mm would be just 3% of the total integrated flux we measure" (Dust emission)
4. **12CO optical depth**: Ratio of 12CO(2-1) (scaled from 3-2 with RADEX ratio 1.08) to 13CO(2-1)  
  > "using a $^{12}$CO(2-1)/$^{12}$CO(3-2) ratio (1.08) obtained from the RADEX online tool for the disc temperature of 50K" (Gas emission)
   - software: RADEX
   - assumption: same excitation temperature; optical depth ratio 77  
  > "Under the assumption that both lines have the same excitation temperature" (Gas emission)
   - fitting: _not stated_
   - validation: _not stated_
5. **Gas mass from 13CO and C18O limit**: Optically thin line-flux mass formula with ISM abundances  
  > "we derive a lower limit on the mass of the gas disc using" (Gas emission)
   - assumption: T=20 K, 12CO/13CO=77, 12CO/H2=1e-4  
  > "We take the midplane temperature to be 20K and assume ISM abundances of $^{12}$CO/$^{13}$CO = 77 and $^{12}$CO/H$_2$=10$^{-4}$" (Gas emission)
   - fitting: _not stated_
   - validation: compared to literature gas masses  
  > "Our minimum mass is two orders of magnitude larger than that calculated using the same method but with $^{12}$CO as the mass tracer" (Gas emission)

## Software

- **CASA** 4.7.1: continuum subtraction and clean imaging  
  > "Using CASA 4.7.1, we subtracted the continuum emission in the uv-space." (Observations and Results)
- **RADEX** : 12CO(2-1)/(3-2) ratio  
  > "obtained from the RADEX online tool for the disc temperature of 50K" (Gas emission)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| mm ring radius | 220 | ±10 | au | 2 | a ring of millimetre emission at 220$\pm$10 au |
| ring minimum dust mass | 0.13 | ±0.02 | Earth masses | 3 | The minimum dust mass of the ring is 0.13$\pm$0.02 M$_{\oplus}$ |
| central unresolved minimum dust mass | 1.2 | ±0.2 | Earth masses | 3 | a minimum of 1.2$\pm$0.2 M$_{\oplus}$ of dust |
| gas mass from 13CO | 6.0e-4 | ±0.9e-4 | Msun | 5 | (6.0$\pm$0.9) $\times 10^{-4}~$M$_\odot$ |
| 12CO optical depth range | 3 to 45 | not stated | dimensionless | 4 | $\tau_{^{12}\rm CO}$ ranges from 3 to 45 |
| unresolved continuum flux | 1.7 | not stated | mJy | 1 | an unresolved point source of 1.7 mJy is detected |
| C18O-based gas mass upper estimate | 1.4e-4 | not stated | Msun | 5 | yielding a total gas mass estimate of 1.4$\times$10$^{-4}$ M$_\odot$ |

## Qualitative findings

- 13CO is strongly asymmetric, peaking at 1.1" at PA -33 deg  
  > "The $^{13}$CO emission is strongly asymmetrical" (Gas emission)

## Claim tuples

- H: Does optically thin 13CO give a higher gas mass than 12CO? | E: Derive gas mass from 13CO and compare with 12CO estimate | R: 6.0e-4 Msun vs ~4.5e-6 Msun | F: 12CO is optically thick and underestimates gas mass | **supported**
- H: Is there a mm dust ring and what is its relation to the gas? | E: Azimuthally averaged 1.3 mm profile | R: Ring at 220±10 au, coincident with the gas outer extent | F: mm ring lies interior to the 234 au scattered light ring | **supported**
- H: Is the central mm emission thermal? | E: Extrapolate VLA flux with free-free slope | R: free-free ~3% of flux | F: emission predominantly thermal | **supported**
- H: Is C18O depleted? | E: C18O non-detection limit vs 13CO | R: flux ratio 31 vs ISM 8 | F: C18O under-abundant, likely isotope-selective photodissociation | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: natural weighting chosen to prioritise signal given no prior knowledge of distribution  
  > "as we have no a priori knowledge of the distribution of $^{13}$CO or indeed of the dust emission, we adopt natural weighting" (Observations and Results)
- Alternative: Free-free origin of central flux considered; found small  
  > "An alternative explanation for the origin of this flux may be free-free emission" (Dust emission)
- How they decided it was enough: _not stated_
- Limitation (authors): Masses depend on assumed temperature; CO depletion would lower gas mass  
  > "Sequestration of CO into icy bodies or conversion into more complex molecules can reduce gas-phase CO in the disc" (Gas emission)
- Caveat (inferred, ours): Fixed 20 K for gas and dust drives masses strongly
- Caveat (inferred, ours): 12CO inclination/PA used for asymmetric 13CO deprojection
- Caveat (inferred, ours): 13CO only a 6 sigma detection
- Caveat (inferred, ours): Natural weighting at 0.7" limits ring resolution

## Reproducibility

- Data public (paper): project ID given; public status not stated  
  > "(PI Panić, ID 2015.1.01600.S)" (Observations and Results)
- Products in archive: _not stated_
- Missing: Clean parameters and masks
- Missing: Integration velocity range
- Missing: 12CO(3-2) data from White et al. 2016
- Missing: Exact fluxes feeding mass formulae
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Short letter with project ID and basic setup, but imaging parameters and integration ranges are missing.
- Rediscovery candidate: yes, ALMA project is likely public, the recipe is simple and results are numeric, though some parameters are unstated.

## Links

- Method: (cite: Schwarz2016THEISOTOPOLOGUES) (optical depth method)
- Companion: (cite: White2016ALMADISK) (12CO(3-2) data and disc geometry)
- Companion: (cite: White2018ExtendedALMA) (independent detection of continuum ring)

## Checks

```json
{
 "quotes": 62,
 "quotes_ok": 62,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 47,
  "rate": 0.627
 },
 "evidence_ok": true
}
```

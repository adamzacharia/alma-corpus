# Gas filaments of the cosmic web located around active galaxies in a protocluster

`2019Sci...366...97U` | Science 2019 | first author: Umehata, H. | arXiv: 1910.01324 | DOI: 10.1126/science.aaw5949

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: Do MUSE Lyman-alpha observations reveal megaparsec-scale gas filaments in the SSA 22 proto-cluster, and can the surrounding SMGs and AGNs power them?  
  > "We report the detection of rest-frame ultraviolet Lyman-α radiation from multiple filaments extending more than one megaparsec between galaxies within the SSA 22 proto-cluster at a redshift of 3.1." (abstract)
- Target **ADF 22 / SSA 22 proto-cluster core**: coordinates (22h17m34.0s, +00d17m00s)  
  > "The approximate 2′ × 3′ field centered at (α, δ) =" (S2 Target Information); "This produces a physical scale of 7.6 kpc arcsec -1 at z=3.09." (S1 Cosmology); z/distance z=3.09  
  > "The approximate 2′ × 3′ field centered at (α, δ) =" (S2 Target Information); "This produces a physical scale of 7.6 kpc arcsec -1 at z=3.09." (S1 Cosmology); distance from spectroscopic redshifts (CO, [OIII]) and earlier SSA 22 work  
  > "The approximate 2′ × 3′ field centered at (α, δ) =" (S2 Target Information); "This produces a physical scale of 7.6 kpc arcsec -1 at z=3.09." (S1 Cosmology)

## Data provenance

- ALMA projects: 2015.1.00212.S, 2016.1.00543.S, 2013.1.00162.S
- bands: Band 3 (CO J=3-2 at z~3.09); 1.1 mm continuum from earlier ADF 22 map  
  > "We observed the majority of the region of ADF 22 using ALMA band 3" (S5 ALMA Band3 Data and Analysis)
- frequencies and spectral setup: 4 spectral windows, 1.875 GHz bandwidth, 977 kHz resolution, centres 85.04, 86.87, 97.03, 98.87 GHz  
  > "The four spectral windows had central frequencies of 85.04 GHz, 86.87 GHz, 97.03 GHz, and 98.87 GHz" (S5 ALMA Band3 Data and Analysis)
- continuum bandwidth: _not stated_
- arrays: 12-m antennas, 36-44 antennas  
  > "using between 36 and 44 of the 12-m antennas" (S5 ALMA Band3 Data and Analysis)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.93 x 0.80 arcsec, PA -54 deg at 84.5 GHz  
  > "The effective beam size is 0. "93 × 0. "80 with position angle of −54" (S5 ALMA Band3 Data and Analysis)
- max recoverable scale: _not stated_
- sensitivity: ~89 uJy/beam (1 sigma) at 84-86 GHz  
  > "The data cube has an r.m.s. level of ~89 `μ` Jy beam -1 (1𝜎) at the phase-tracking center" (S5 ALMA Band3 Data and Analysis)
- time on source: 13.9 hours in 19 execution blocks  
  > "the total on

source time was 13.9 hours" (S5 ALMA Band3 Data and Analysis)
- observing dates: 2016 (July 21-Aug 19 and May 7-July 4)  
  > "from July 21st to August

19th, 2016, and from May 7th to July 4th, 2016" (S5 ALMA Band3 Data and Analysis)
- pi or archival as stated: PI H. Umehata  
  > "PI. H. Umehata" (S5 ALMA Band3 Data and Analysis)
- Line: CO J=3-2 (345.796 GHz)
- Other facility **VLT/MUSE**: Lyman-alpha cube of 6-pointing mosaic  
  > "we acquired 6 adjacent fields with a

2 × 3 pattern" (S4 MUSE Observations, Data Reduction, and Analysis)
- Other facility **Subaru/Suprime-Cam**: NB497 narrow-band image  
  > "using the NB497 filter to trace Ly α emission at z~3.09" (S3 Suprime-Cam Data Reduction and Analysis)
- Other facility **Keck/MOSFIRE**: K-band redshifts of SMGs  
  > "We use the Multi-Object Spectrometer for

Infra-Red Exploration (MOSFIRE) ( _47_ ) on the Keck-I telescope" (S6 MOSFIRE Data and Analysis)
- Other facility **Chandra**: X-ray AGN identification  
  > "The ADF 22 field is fully covered by a deep _Chandra_ X-ray survey" (S2 Target Information)
- External data: ADF 22 1.1 mm map and SMG catalogue (rms 60 uJy/beam, 0.7 arcsec)  
  > "has a typical r.m.s. (root mean square) level of 60 `μ` Jy beam -1 with 0".7" (S2 Target Information) [from (cite: 32)]
- External data: Chandra X-ray source catalogue  
  > "In total, 19 X-ray" (S2 Target Information) [from (cite: 34)]

## Processing

### Calibration

- pipeline or manual: standard CASA pipeline  
  > "The calibration and flagging were carried out with a standard CASA pipeline." (S5 ALMA Band3 Data and Analysis)
- casa version: CASA 4.7.0, 4.7.2, 5.1.0  
  > "Common Astronomy Software Application ( CASA ) versions

4.7.0, 4.7.2, and 5.1.0" (S5 ALMA Band3 Data and Analysis)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Pallas, PKS J2148+0657, PKS 2230+11, Titan  
  > "To set the absolute flux scale, Pallas, J PKS J2148+0657, PKS 2230+11, and

Titan were observed." (S5 ALMA Band3 Data and Analysis)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean, mosaic gridder  
  > "using the CASA task tclean, adopting natural weighting and mosaic gridder mode" (S5 ALMA Band3 Data and Analysis)
- deconvolver: _not stated_
- weighting robust: natural  
  > "using the CASA task tclean, adopting natural weighting and mosaic gridder mode" (S5 ALMA Band3 Data and Analysis)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: imcontsub  
  > "Continuum components

were subtracted using IMCONTSUB ." (S5 ALMA Band3 Data and Analysis)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.93 x 0.80 arcsec  
  > "The effective beam size is 0. "93 × 0. "80 with position angle of −54" (S5 ALMA Band3 Data and Analysis)
- final rms: ~89 uJy/beam, 100 km/s channels  
  > "Combining the 19 EBs produced a cube with a velocity resolution of 100 km s -1 for each spectral window" (S5 ALMA Band3 Data and Analysis)

### Inherited from earlier work

- SMG SFR from SED template fitting as in earlier ADF 22 work  
  > "the SFR was

calculated from SED template fitting as in previous work ( _21_ )" (S10 Ionizing Luminosity Estimate) [from (cite: 21)]
- Over-density estimates use published methods  
  > "The over-densities of SMGs and X-ray AGNs are estimated using published methods ( _21_ )." (S8 Over-densities of SMGs and X-ray AGNs) [from (cite: 21)]

### Not stated but needed to reproduce (our reading)

- Image size, cell size, and continuum/line-free channels for the Band 3 cubes
- Primary-beam-correction details and mosaic mask
- Which execution blocks belong to which CASA version
- Flux calibrator used per execution block
- Redshift-fitting details such as the line window
- Ly-alpha fluxes, filament extraction and radiative transfer details are outside the ALMA data

## Analysis recipe

1. **Image Band 3 cubes**: Combine 19 EBs, tclean natural weighting, mosaic, 100 km/s channels, imcontsub  
  > "Combining the 19 EBs produced a cube with a velocity resolution of 100 km s -1 for each spectral window" (S5 ALMA Band3 Data and Analysis)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure CO(3-2) redshifts of SMGs**: Extract 1D spectra in 2 arcsec aperture at each CO peak; fit single Gaussian  
  > "A single Gaussian model was fitted to each line to determine the redshifts, listed in Table S2." (S5 ALMA Band3 Data and Analysis)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.0, 4.7.2, 5.1.0: ALMA calibration and imaging  
  > "The ALMA data were reduced using the Common Astronomy Software Application ( CASA ) versions" (S5 ALMA Band3 Data and Analysis)
- **CubExtractor** v.1.8: MUSE sky subtraction, PSF subtraction, 3D Lyα extraction  
  > "we used the CUBEXTRACTOR package (v.1.8)" (S4 MUSE Observations, Data Reduction, and Analysis)
- **SExtractor** v2.5.0: extended Lyα structures in Suprime-Cam image  
  > "using SEXTRACTOR (v2.5.0; _39_ )" (S3 Suprime-Cam Data Reduction and Analysis)
- **CLOUDY** : radiative transfer slab models  
  > "We run radiative transfer calculations with the CLOUDY software" (S9 Radiative Transfer Calculation)
- **ESO MUSE pipeline** v2.4.1: basic MUSE reduction  
  > "We used the standard ESO MUSE pipeline (v2.4.1)" (S4 MUSE Observations, Data Reduction, and Analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA Band 3 cube rms | 89 | not stated | uJy/beam | 1 | The data cube has an r.m.s. level of ~89 `μ` Jy beam -1 (1𝜎) |
| SMGs with CO detections | 14 of 17 | not stated | count | 2 | We detected CO emission from 14 of the 17 SMGs observed. |
| Total SMG SFR in field | ~6900 | not stated | Msun/yr | 0 | or a

total SFR ~6900 𝑀 ⊙ yr -1 in the field |
| Required enhancement of ionizing field over UVB | >12 | not stated | dimensionless | 0 | an enhanced radiation field (> 12 × the UVB) in optically thick gas would match the observed surface brightness |
| Filament gas mass | ~10^12 | order of magnitude | Msun | 0 | the mass of hydrogen is calculated to

be of the order of ~10 [12] 𝑀 ⊙ |

## Qualitative findings

- Lyα filaments >1 Mpc trace the distribution of SMGs and X-ray AGNs in position and velocity.  
  > "Intense star formation and supermassive black-hole activity is occurring

within the galaxies embedded in these structures" (abstract)

## Claim tuples

- H: Extended Lyα filaments exist in the SSA 22 core | E: MUSE mosaic plus Suprime-Cam narrow-band | R: Two main filaments >1 Mpc, SB >~3e-19 erg/s/cm2/arcsec2 | F: Megaparsec-scale gas filaments detected | **supported**
- H: SMGs and AGNs can power the Lyα emission | E: CLOUDY slabs and ionizing photon budget with ALMA/Keck redshifts | R: Qion ~1e57 s^-1 vs required ~1e55 s^-1 at 1% escape | F: Active galaxies can ionize the filaments | **supported**

## Reasoning

- Why this data: Dusty SMGs are faint in the UV, so CO lines give systemic redshifts  
  > "Dust extinction makes it challenging to detect rest-frame UV emission lines from SMGs" (S5 ALMA Band3 Data and Analysis)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Hydrogen mass is an order-of-magnitude estimate depending on unknown filling factor and thickness.  
  > "an estimate that bears substantial uncertainty due to the unknown thickness" (S11 Hydrogen Mass Estimate)
- Caveat (inferred, ours): Photon budget uses a crude 250 kpc distance and 1% escape fraction
- Caveat (inferred, ours): Constant-density slab model is simplistic
- Caveat (inferred, ours): Lyα resonant scattering complicates kinematic interpretation

## Reproducibility

- Data public (paper): ALMA data in archive under the three programmes  
  > "the ALMA data through the archive" (Data and materials availability)
- Products in archive: _not stated_
- Missing: Imaging parameters for Band 3 cubes
- Missing: Line fitting windows
- Missing: MUSE reduction parameters beyond those given
- Data volume (inferred): ~100s of GB for ALMA Band 3 mosaic (19 EBs); MUSE additional
- Score (inferred): 3/5, ALMA part is brief; main results rely on MUSE, which is public but not ALMA.
- Rediscovery candidate: no, ALMA role is redshift measurement; imaging details are missing and main results come from MUSE.

## Links

- Method: (cite: 14,42) CubExtractor method (3D Lyα extraction)
- Companion: (cite: 21,32,33) ADF 22 papers (1.1 mm map and SMG catalogue)
- Related: ALMA Deep Field in SSA 22 (ADF 22)
- Related: Chandra Deep Protocluster Survey

## Checks

```json
{
 "quotes": 54,
 "quotes_ok": 54,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 64,
  "stated": 39,
  "rate": 0.609
 },
 "evidence_ok": true
}
```

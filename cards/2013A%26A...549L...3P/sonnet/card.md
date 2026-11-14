# Warm water deuterium fractionation in IRAS 16293-2422. The high-resolution ALMA and SMA view

`2013A&A...549L...3P` | Astronomy and Astrophysics 2013 | first author: Persson, M. V. | arXiv: 1211.6605 | DOI: 10.1051/0004-6361/201220638

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: astrochemistry, star_formation
- Question: What is the water deuterium fractionation (HDO/H2O) and excitation temperature in the warm inner gas of the protostellar binary IRAS 16293-2422?  
  > "To measure the water deuterium fractionation in the warm gas of the deeply-embedded protostellar binary IRAS 16293-2422." (abstract)
- Target **IRAS 16293-2422**: coordinates 16h32m22.7s, -24d28m32.5s (J2000), mosaic center  
  > "$\alpha = 16^\mathrm{h} 32^\mathrm{m} 22$$.\!\!^{\mathrm{s}}$$7$, $\delta = -24\ensuremath{^\circ}28^{\prime}32.5\ensuremath{''}$ (J2000)" (Observations); "located 120 pc away in the LDN 1689N cloud in the $\rho$ Ophiucus star-forming region (cite: knude98; loinard08)" (Introduction); z/distance 120 pc  
  > "$\alpha = 16^\mathrm{h} 32^\mathrm{m} 22$$.\!\!^{\mathrm{s}}$$7$, $\delta = -24\ensuremath{^\circ}28^{\prime}32.5\ensuremath{''}$ (J2000)" (Observations); "located 120 pc away in the LDN 1689N cloud in the $\rho$ Ophiucus star-forming region (cite: knude98; loinard08)" (Introduction); distance from (cite: knude98; loinard08)  
  > "$\alpha = 16^\mathrm{h} 32^\mathrm{m} 22$$.\!\!^{\mathrm{s}}$$7$, $\delta = -24\ensuremath{^\circ}28^{\prime}32.5\ensuremath{''}$ (J2000)" (Observations); "located 120 pc away in the LDN 1689N cloud in the $\rho$ Ophiucus star-forming region (cite: knude98; loinard08)" (Introduction)

## Data provenance

- ALMA projects: 2011.0.00007.SV
- bands: ~690 GHz with ALMA (SMA at 230 GHz)  
  > "were carried out at 690 GHz with ALMA and 230 GHz with the SMA" (Observations)
- frequencies and spectral setup: Baseband centered at 691.299 GHz, 1.875 GHz bandwidth, 0.923 MHz (0.4 km/s) resolution  
  > "One of the basebands was centered at 691.299 GHz with a bandwidth of 1.875 GHz and a spectral resolution of 0.923 MHz (0.4 km s$^{-1}$)" (Observations)
- continuum bandwidth: _not stated_
- arrays: 13 antennas, seven-pointing mosaic  
  > "IRAS 16293-2422 was observed with 13 antennas on April 16 and 17, 2012 in a seven pointing mosaic" (Observations)
- configurations: _not stated_
- baselines: 26 to 402 m (62 to 945 kλ)  
  > "The observations cover projected baselines from 26 to 402 m (62 to 945 k$\lambda$)." (Observations)
- angular resolution: 0.17"x0.29" beam at 692 GHz  
  > "$0.17\ensuremath{''}\times0.29\ensuremath{''}$ (109.8$^\circ$)" (Table 2)
- max recoverable scale: _not stated_
- sensitivity: RMS 82 mJy/beam/channel at 692 GHz  
  > "0.40 | 82" (Table 2)
- time on source: _not stated_
- observing dates: April 16 and 17, 2012  
  > "observed with 13 antennas on April 16 and 17, 2012" (Observations)
- pi or archival as stated: ALMA Science Verification data  
  > "The science verification data are available as calibrated *uv*-data sets, which were used in our analysis." (Observations)
- Line: H2(18)O 5_{3,2}-4_{4,1} (692.07914 GHz)
- Line: H2(18)O (SMA) 3_{1,3}-2_{2,0} (203.40752 GHz)
- Line: HDO (SMA) 3_{1,2}-2_{2,1} (225.89672 GHz)
- Other facility **SMA**: 203 GHz H2(18)O and 225 GHz HDO lines  
  > "The lower-lying excited H$_2^{18}$O $3_{1,3}-2_{2,0}$ transition at 203.4075 GHz was observed with the SMA on May 1, 2011" (Observations)
- External data: SMA HDO 225.89672 GHz observations  
  > "we utilized SMA observations of the HDO $3_{1,2}-2_{2,1}$ line at 225.89672 GHz from the SMA (cite: jorgensen11)" (Observations) [from (cite: jorgensen11)]
- External data: 16O/18O = 560 in local ISM  
  > "the isotopic abundance ratio of $^{16}$O/$^{18}$O is 560 in the local interstellar medium (cite: wilson94)" (Discussion) [from (cite: wilson94)]

## Processing

### Calibration

- pipeline or manual: ALMA SV calibrated uv-data used; SMA calibrated with MIR  
  > "The science verification data are available as calibrated *uv*-data sets, which were used in our analysis." (Observations); "The raw data calibration followed the standard recipes using the MIR package (cite: qi08)" (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Yes, calibrated SV uv-data  
  > "The science verification data are available as calibrated *uv*-data sets, which were used in our analysis." (Observations)
- flux calibrator: Juno (amplitude); 1924-292 and 3c279 bandpass; 1625-254 and nrao530 phase  
  > "the asteroid Juno for the amplitude, and the quasars 1625-254 and nrao530 for the phase" (Observations)
- flux scale uncertainty: 20% calibration uncertainty  
  > "the 20% calibration uncertainty in intensity is not included" (Table 1)
- self calibration: _not stated_

### Imaging

- task: Imaged with CASA  
  > "The calibrated data were imaged using the CASA software package (cite: mcmullin07)." (Observations)
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
- smoothing: Gaussian kernel of 1" for one spectrum of source A  
  > "the spectrum after smoothing with a Gaussian kernel of 1$''$ size" (Results)
- final beam: 0.17"x0.29" (PA 109.8°)  
  > "$0.17\ensuremath{''}\times0.29\ensuremath{''}$ (109.8$^\circ$)" (Table 2)
- final rms: 82 mJy/beam/channel  
  > "0.40 | 82" (Table 2)

### Inherited from earlier work

- SMA HDO observation details  
  > "For further information about those observations we refer to (cite: jorgensen11)." (Observations) [from (cite: jorgensen11)]
- Tex of 300 K tested, from earlier work  
  > "Increasing the excitation temperature to 300 K (cite: jorgensen12) increases the ratio" (Discussion) [from (cite: jorgensen12)]

### Not stated but needed to reproduce (our reading)

- Weighting/robust, cell and image size, deconvolver, masking and clean parameters
- Continuum subtraction method and line-free channels for ALMA
- Details of ALMA SV data version and CASA version
- Partition function and spectroscopic constants used for LTE
- Exact column density equations and the beam-dilution correction
- Fit method for Tex

## Analysis recipe

1. **Image and fit line intensities**: Gaussian fits to spectra, uv-plane (203, 225 GHz) or elliptical image-plane (692 GHz) fits to integrated maps  
  > "integrated intensities deduced from circular Gaussian fits in the *uv*-plane (203 and 225 GHz) or an elliptical Gaussian fit in image plane (692 GHz)" (Table 1)
   - software: CASA, MIRIAD
   - fitting: _not stated_
   - validation: Line identification with JPL and CDMS via Splatalogue  
  > "The lines were identified using the JPL and CDMS catalogs through the Splatalogue compilation" (Results)
2. **Derive excitation temperature of H2(18)O**: Scale 203 GHz intensity to 692 GHz source size and compare the two H2(18)O lines  
  > "Scaling the 203 GHz H$_2^{18}$O intensities to the 692 GHz source size gives an excitation temperature of $T_\mathrm{ex}=124\pm 12$ K" (Discussion)
   - assumption: LTE; 203 and 225 GHz emission has same extent as 692 GHz  
  > "we assume LTE conditions and that the emission at 203 and 225 GHz has the same extent as in the 692 GHz observations" (Discussion)
   - fitting: _not stated_
   - validation: Halving 692 GHz intensity gives Tex=107±9 K  
  > "Halving the intensity of the 692 GHz line causes a drop to $T_\mathrm{ex}=107\pm 9$ K." (Discussion)
3. **Column densities and HDO/H2O**: HDO column density from 225 GHz line at Tex=124 K corrected for beam dilution; H2O column from H2(18)O with 16O/18O=560  
  > "The gas-phase H$_2$O column density is $5.3\times 10^{20}$ cm$^{-2}$ assuming the same as for HDO and that the isotopic abundance ratio of $^{16}$O/$^{18}$O is 560" (Discussion)
   - assumption: 20% uncertainty in column densities from flux calibration  
  > "Assuming an uncertainty of about 20% for the column densities, originating in the flux calibration" (Discussion)
   - fitting: _not stated_
   - validation: Tested Tex = 80 K and 300 K; ratio changes little  
  > "The conclusions in this paper do not change over this wide interval in $T_\mathrm{ex}$." (Discussion)

## Software

- **CASA** : Imaging of ALMA calibrated data  
  > "The calibrated data were imaged using the CASA software package (cite: mcmullin07)." (Observations)
- **MIR** : SMA raw data calibration  
  > "The raw data calibration followed the standard recipes using the MIR package (cite: qi08)" (Observations)
- **MIRIAD** : Continuum subtraction of SMA data  
  > "then MIRIAD (cite: sault95) was used to subtract the continuum" (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| H2(18)O excitation temperature | 124 | ±12 | K | 2 | $T_\mathrm{ex}=124\pm 12$ K for H$_2^{18}$O |
| HDO column density | 4.8e17 | ~20% | cm^-2 | 3 | The estimated HDO column density is $4.8\times 10^{17}$ cm$^{-2}$ |
| H2O column density | 5.3e20 | ~20% | cm^-2 | 3 | The gas-phase H$_2$O column density is $5.3\times 10^{20}$ cm$^{-2}$ |
| HDO/H2O | 9.2e-4 | ±2.6e-4 | dimensionless | 3 | the best estimate of the HDO/H$_2$O ratio is $(9.2\pm 2.6)\times 10^{-4}$ |
| 692 GHz H2(18)O intensity, A1 | 3.4 | ±0.6 | Jy km/s | 1 | 3 (A1) / $0.2\times0.4\, (13\ensuremath{^\circ})$ /   $3.4\pm0.6$ |

## Qualitative findings

- 692 GHz H2(18)O seen in absorption toward source B, slightly red-shifted, indicative of infall  
  > "The red-shifted absorption detected toward source B is indicative of infall." (abstract)

## Claim tuples

- H: Warm inner-envelope HDO/H2O is high as suggested by single-dish models | E: ALMA and SMA H2(18)O and HDO lines, LTE analysis | R: HDO/H2O=(9.2±2.6)e-4 | F: Ratio is much lower than previous warm-gas estimates and close to comets and Earth's oceans | **supported**
- H: Water is hot near protostar | E: Two H2(18)O lines | R: Tex=124±12 K | F: Consistent with ice evaporation | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Interferometry avoids reliance on envelope models needed for single-dish data  
  > "High angular resolution millimeter wavelength aperture synthesis observations offer a possibility to circumvent this issue." (Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): 692 GHz line toward A may be blended, so Tex is an upper limit; if HDO is more extended the ratio is an upper limit  
  > "If the 692 GHz line is indeed blended, it would imply that the intensity estimate, and also the excitation temperature, are upper limits." (Discussion)
- Caveat (inferred, ours): Tex from only two lines with different beams and assumed same source size
- Caveat (inferred, ours): Possible blending and velocity offset at 692 GHz
- Caveat (inferred, ours): HDO and H2O from different instruments and resolutions
- Caveat (inferred, ours): LTE assumed

## Reproducibility

- Data public (paper): ALMA SV data public  
  > "The science verification data are available as calibrated *uv*-data sets, which were used in our analysis." (Observations)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: SMA data access
- Missing: Column density formalism details
- Data volume (inferred): ~10-30 GB (SV band 9 mosaic, calibrated uv-data)
- Score (inferred): 3/5, Data public but imaging and LTE details missing; SMA data from other work.
- Rediscovery candidate: no, Imaging and column-density recipe are incomplete and the result also depends on SMA data.

## Links

- Companion: (cite: persson12a) (Extended survey of H2(18)O and HDO emission)
- Companion: (cite: jorgensen11) (SMA HDO observations)
- Related: ALMA Science Verification

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
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
  "facts": 64,
  "stated": 40,
  "rate": 0.625
 },
 "evidence_ok": true
}
```

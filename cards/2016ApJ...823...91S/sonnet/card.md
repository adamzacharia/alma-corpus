# The Radial Distribution of H<SUB>2</SUB> and CO in TW Hya as Revealed by Resolved ALMA Observations of CO Isotopologues

`2016ApJ...823...91S` | The Astrophysical Journal 2016 | first author: Schwarz, Kamber R. | arXiv: 1603.08520 | DOI: 10.3847/0004-637X/823/2/91

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: What are the radial gas temperature, H2 surface density and CO abundance in the TW Hya disk, and where are the CO snowlines?  
  > "which allow us to derive radial gas temperature and gas surface density profiles, as well as map the CO abundance as a function of radius." (abstract)
- Target **TW Hya**: coordinates _not stated_; z/distance 54±6 pc  
  > "we present resolved observations of the TW Hya disk ($d=54\pm6$ pc)" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00422.S
- bands: Band 9 and Band 7  
  > "ALMA observations of TW Hya were obtained in Band 9 on March 12, 2014 with 27 antennas and in Band 7 on May 14, 2015 with 37 antennas." (2 Observations and Data Reduction)
- frequencies and spectral setup: 4 SPWs per band; Band 7 SPW1/2 122.070 kHz resolution, 468.75 MHz bandwidth; Band 9 SPW1/2 244.141 kHz, 937.5 MHz  
  > "Observations in both bands utilized 4 spectral windows (SPWs)." (2 Observations and Data Reduction); "was 244.141 kHz and the total bandwidth was 937.5 MHz." (2 Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15-414 m (Band 9); 21-545 m (Band 7)  
  > "The baseline coverage was 15-414 m for the Band 9 observations and 21-545 m for those in Band 7." (2 Observations and Data Reduction)
- angular resolution: Band 7 beam ~0.5"x0.3"; 13CO 6-5 ~0.4"x0.2"; C18O 6-5 ~0.5"x0.3"  
  > "The restoring beam for the Band 7 observations had FWHM dimensions of $\sim 0.5\ensuremath{''} \times 0.3\ensuremath{''}$ (P.A. 88$^{\circ}$)" (2 Observations and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: RMS per 0.1 km/s channel: 9.2 (13CO 3-2), 12 (C18O 3-2), 56 (13CO 6-5), 77 (C18O 6-5) mJy/beam  
  > "are 9.2 mJy beam$^{-1}$ for $^{13}$CO 3-2, 12 mJy beam$^{-1}$ for C$^{18}$O 3-2, 56 mJy beam$^{-1}$ for $^{13}$CO 6-5, and 77 mJy beam$^{-1}$ for C$^{18}$O 6-5" (2 Observations and Data Reduction)
- time on source: _not stated_
- observing dates: March 12, 2014 (Band 9); May 14, 2015 (Band 7)  
  > "ALMA observations of TW Hya were obtained in Band 9 on March 12, 2014 with 27 antennas and in Band 7 on May 14, 2015 with 37 antennas." (2 Observations and Data Reduction)
- pi or archival as stated: _not stated_
- Line: 13CO 3-2 (not stated)
- Line: C18O 3-2 (not stated)
- Line: 13CO 6-5 (not stated)
- Line: C18O 6-5 (not stated)
- Other facility **Herschel (HD 1-0 detection)**: Unresolved HD J=1-0 detection used to scale H2 surface density  
  > "detected the HD J=1-0 ($E_u = 128$ K) line towards the 3-10 Myr old transition disk TW Hya" (Introduction)
- External data: HD 1-0 detection (total gas mass >0.05 Msun)  
  > "Using the HD detection (cite: Bergin13) find the total gas mass in the TW Hya disk to be $> 0.05~\mbox{M$_\odot$}$" (Introduction) [from (cite: Bergin13)]
- External data: Small-dust surface density profile Sigma ∝ R^-1/2  
  > "follows the surface density profile of the small ($r<100\ \ensuremath{\mu}m$) dust as fit by (cite: Menu14) i.e., $\Sigma \propto R^{-1/2}$" (3.2 The H2 Surface Density Distribution) [from (cite: Menu14)]
- External data: HD/H2 = 3e-5  
  > "an abundance ratio of HD/H$_2$$= 3\mbox{${} \times 10^{-5}$}$ (cite: Linsky98)" (3.2 The H2 Surface Density Distribution) [from (cite: Linsky98)]
- External data: Model midplane gas temperature of TW Hya  
  > "we use the midplane gas temperature from the TW Hya model of (cite: Cleeves15)" (4.3 The CO snowline and Outer Ring) [from (cite: Cleeves15)]

## Processing

### Calibration

- pipeline or manual: Initial reduction by ALMA/NAASC staff, standard procedures  
  > "Initial data reduction was carried out by ALMA/NAASC staff using standard procedures." (2 Observations and Data Reduction)
- casa version: CASA 4.6.12  
  > "were carried out for the spectral windows containing the science targets using CASA 4.6.12." (2 Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (flux), J1037-2934 (phase), J1256-057 (bandpass)  
  > "On both dates Titan was used for amplitude and flux calibration, while phase calibration and bandpass calibration were carried out on J1037-2934 and J1256-057 respectively." (2 Observations and Data Reduction)
- flux scale uncertainty: _not stated_
- self calibration: Phase and amplitude self-cal on science SPWs; separate per SPW for Band 9  
  > "phase and amplitude self-calibration were carried out for the spectral windows containing the science targets" (2 Observations and Data Reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust 0.5 for 3-2 lines; natural for 6-5  
  > "Briggs weighting with the robustness parameter set to 0.5 was used for the $^{13}$CO and C$^{18}$O 3-2 transitions; natural weighting was used for the $^{13}$CO and C$^{18}$O 6-5 emission." (2 Observations and Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Manual CLEAN mask per line SPW  
  > "A CLEAN mask was manually generated individually for each spectral window with line emission." (2 Observations and Data Reduction)
- multiscale scales: _not stated_
- continuum subtraction: Applied per SPW using line-free channels  
  > "Continuum subtraction was employed for each spectral window using the line free channels for all observations." (2 Observations and Data Reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Inclination ~7 deg  
  > "nearly face-on disk ($i\sim7\mbox{$^{\circ}$}$ (cite: Qi04))" (Introduction) [from (cite: Qi04)]
- 13CO/C18O = 8 ISM ratio  
  > "assumed to be $^{13}$CO/C$^{18}$O = 8 based on ISM abundances (cite: Wilson99)" (3.1 Gas Temperature) [from (cite: Wilson99)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for continuum subtraction
- Self-calibration solution intervals and reference antenna
- CLEAN mask shapes and thresholds, image size, cell size
- Deprojection geometry (PA, center) for azimuthal averaging
- Rest frequencies, Einstein A and partition constants used
- Exact HD 1-0 flux and uncertainty adopted
- Stellar mass/binding energy details for snowline calculation beyond text

## Analysis recipe

1. **Image and integrate CO isotopologue emission**: CLEAN imaging, moment-0 by summing emission above 2 sigma per channel; deprojected azimuthal averages  
  > "Integrated emission maps were made by summing the emission above 2$\sigma$ from each channel." (2 Observations and Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive optical depth**: Pixel-by-pixel 13CO/C18O intensity ratio with abundance ratio 8 to solve for tau  
  > "The optical depth of the $^{13}$CO lines are determined by taking the ratio of the $^{13}$CO and C$^{18}$O emission in each transition on a pixel-by-pixel basis." (3.1 Gas Temperature)
   - assumption: Tex ratio ~1; 13CO/C18O = 8  
  > "$T_{ex,^{13}\mathrm{CO}}/T_{ex,\mathrm{C^{18}O}}$ is expected to be close to unity, effectively canceling." (3.1 Gas Temperature)
   - fitting: _not stated_
   - validation: _not stated_
3. **Gas kinetic temperature**: Optically thick 13CO peak brightness converted to T_K assuming LTE, beam-filling; per pixel then azimuthally averaged; average of 3-2 and 6-5  
  > "For our data the temperature was calculated for each pixel before taking the azimuthal average" (3.1 Gas Temperature)
   - assumption: LTE, emission fills beam  
  > "assuming the emission fills the beam, as is reasonable for resolved emission." (3.1 Gas Temperature)
   - fitting: _not stated_
   - validation: _not stated_
4. **H2 surface density from HD**: Compute HD 1-0 emission in radial bins from temperature profile and scale uniform factor to match unresolved HD detection  
  > "This yields a scaling factor of 73 for the average temperature profile." (3.2 The H2 Surface Density Distribution)
   - parameter: Sigma ∝ R^-1/2 over 3.1-61.7 AU  
  > "in the range $3.1\,\mathrm{AU}\leq R \leq 61.7\, \mathrm{AU}$ and zero elsewhere." (3.2 The H2 Surface Density Distribution)
   - assumption: HD/H2 = 3e-5; H2 follows small dust surface density  
  > "assuming H$_2$ has the same surface density as the small dust grains and an abundance ratio of HD/H$_2$$= 3\mbox{${} \times 10^{-5}$}$" (3.2 The H2 Surface Density Distribution)
   - fitting: _not stated_
   - validation: Alternative surface density profiles (Andrews12 sA, Cleeves15) tested  
  > "we find that the surface density of the warm gas varies by less than a factor of three for $R=1-40$ AU." (4.1 The H2 Surface Density)
5. **CO surface density and abundance**: Upper-state column densities from optically thin C18O (and outer 13CO 6-5), corrected for partition function using T profile; divide by H2  
  > "we correct for the fractional population not in the J=6 or J=3 states using our average $^{13}$CO temperature profile" (3.3 CO Surface Density & Abundance)
   - assumption: linear rotator partition function  
  > "the partition function, $Q$, approximated for a linear rotator" (3.3 CO Surface Density & Abundance)
   - fitting: _not stated_
   - validation: Compared with Nomura15 C18O surface density; isotopologue self-shielding check  
  > "Our CO surface density is similar to the (cite: Nomura15) surface density derived solely from C$^{18}$O 3-2" (3.3 CO Surface Density & Abundance)
6. **Midplane CO snowline**: Balance adsorption and desorption with scale height from C18O temperature, M*=0.8 Msun, E_B/k~960 K, midplane T from Cleeves15 model  
  > "we calculate a midplane CO snowline radius in the range $R = 17-23$ AU." (4.3 The CO snowline and Outer Ring)
   - parameter: N = 1e15 sites per cm2; f~1  
  > "$N = \mbox{$10^{15}$}$ is the number of absorption sites per cm$^2$" (4.3 The CO snowline and Outer Ring)
   - assumption: gas and dust temperatures equal; M*=0.8 Msun  
  > "assuming the gas and dust temperatures are the same" (4.3 The CO snowline and Outer Ring)
   - fitting: _not stated_
   - validation: Binding energy compared with laboratory measurements  
  > "This derived binding energy is consistent with laboratory measurements of CO binding to a primarily CO ice surface" (4.3 The CO snowline and Outer Ring)

## Software

- **CASA** 4.6.12: self-calibration, continuum subtraction and imaging  
  > "were carried out for the spectral windows containing the science targets using CASA 4.6.12." (2 Observations and Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Warm gas surface density normalization at 10 AU | 4.7 | +3.0/-2.9 | g cm^-2 | 4 | $\Sigma_{warm\,gas} = 4.7^{+3.0} _{-2.9}\mathrm{\,g\, cm^{-2}}\left(\frac{R}{10\,\mathrm{AU}}\right)^{-1/2}$ |
| Scaling factor to match HD | 73 | not stated | dimensionless | 4 | This yields a scaling factor of 73 for the average temperature profile. |
| Warm gas mass inside 61.7 AU (average T) | 5.6e-3 | range 2.1e-3 to 9.3e-3 | Msun | 4 | the total warm gas mass inside of 61.7 AU is $5.6\mbox{${} \times 10^{-3}$}~\mbox{M$_\odot$}$ assuming our average temperature profile. |
| Maximum CO abundance X(CO) | 2.5e-6 | not stated | dimensionless | 5 | $X(\mathrm{CO})$ never rises above $2.5\mbox{${} \times 10^{-6}$}$ assuming the average $^{13}$CO temperature profile. |
| CO freeze-out temperature | <21 | not stated | K | 3 | constrains the freeze-out temperature of CO in the warm molecular layer to $< 21$ K. |
| Midplane CO snowline radius | 17-23 | not stated | AU | 6 | constrain the midplane CO snowline to 17-23 AU. |
| Outer ring radius | 0.97 arcsec (53 AU); gap at 0.70 arcsec (38 AU) | not stated | arcsec/AU | 1 | The average radius of the gap and the ring are $0.70\ensuremath{''}$ (38 AU) and $0.97\ensuremath{''}$ (53 AU) respectivley |
| CO binding energy E_B/k | ~960 | not stated | K | 6 | suggests $E_{B}/k\sim960$ K. |

## Qualitative findings

- CO is depleted by about two orders of magnitude from 10-60 AU; CO returning inside the surface snowline is insufficient to explain it.  
  > "We find that CO is depleted by two orders of magnitude from $R=10-60$ AU" (abstract)

## Claim tuples

- H: Is CO depleted relative to H2 in TW Hya across the disk? | E: Combine CO isotopologue-derived temperature and CO column with HD-scaled H2 surface density | R: X(CO) of order 1e-6, never above 2.5e-6 | F: Gas-phase carbon is globally depleted and not returned inside the snowline | **supported**
- H: Can resolved 13CO temperatures constrain the warm H2 surface density? | E: Scale HD 1-0 model emission to the Herschel detection using measured T | R: Sigma = 4.7 g cm^-2 (R/10 AU)^-1/2 | F: Warm gas mass is a lower limit consistent with Bergin13 | **supported**
- H: Where is the CO snowline and is there an outer CO ring? | E: Temperature plateau and CO surface density profiles; snowline balance with model midplane T | R: Surface snowline ~30 AU; ring peak at ~53 AU; midplane snowline 17-23 AU | F: CO ring seen for the first time; midplane snowline model dependent | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Isotopologue-specific photodissociation and HD self-shielding cannot fully explain low CO abundance  
  > "Thus, self-shielding of HD cannot explain the low CO abundance." (4.2 The Missing Carbon)
- How they decided it was enough: _not stated_
- Limitation (authors): Midplane snowline result is model dependent.  
  > "We stress that this result is model dependent." (4.3 The CO snowline and Outer Ring)
- Limitation (authors): Ring not seen in 6-5 data, possibly due to sensitivity.  
  > "This feature is not seen in the 6-5 data, though this may be due to insufficient sensitivity." (3 Data Analysis)
- Caveat (inferred, ours): Temperature uses single-peak brightness; beam dilution and LTE assumptions are untested
- Caveat (inferred, ours): Ring significance in C18O is only 2.6 sigma at the minimum
- Caveat (inferred, ours): Result depends on a single unresolved HD flux and the assumed R^-1/2 profile
- Caveat (inferred, ours): Uncertainties are bracketing limits, not statistical errors

## Reproducibility

- Data public (paper): ALMA project 2012.1.00422.S acknowledged  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00422.S." (Summary)
- Products in archive: _not stated_
- Missing: Self-cal and imaging details
- Missing: Deprojection geometry
- Missing: Adopted HD flux
- Missing: Exact radial binning and scripts
- Data volume (inferred): ~50-150 GB raw for two bands
- Score (inferred): 3/5, Public data and clear equations, but self-calibration, masks, geometry and HD flux details missing.
- Rediscovery candidate: no, Recipe depends on unstated details and external HD flux and models.

## Links

- Companion: (cite: Nomura15) (Independent resolved C18O 3-2 observations of TW Hya)
- Companion: (cite: Bergin13) (HD 1-0 detection used for gas mass)

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
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 44,
  "rate": 0.55
 },
 "evidence_ok": true
}
```

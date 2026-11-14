# Massive Molecular Gas Flows in the A1664 Brightest Cluster Galaxy

`2014ApJ...784...78R` | The Astrophysical Journal 2014 | first author: Russell, H. R. | arXiv: 1309.0014 | DOI: 10.1088/0004-637X/784/1/78

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: galaxy_clusters_and_sz, nearby_galaxies
- Question: What are the mass, kinematics and origin (inflow, outflow or merger) of the molecular gas in the Abell 1664 BCG?  
  > "we calculate the molecular gas masses of these flows and consider their possible origins including mergers, inflow settling into a disk and outflow." (Discussion)
- Target **Abell 1664 BCG**: coordinates _not stated_; z/distance z=0.128 (2.3 kpc/arcsec)  
  > "1\rm\; arcsec$ corresponds to a physical scale of $2.3\rm\; kpc$ at the redshift $z=0.128$ of the BCG" (Introduction); distance from Allen92; Pimbblet06 emission-line redshift, accurate to ~100 km/s  
  > "1\rm\; arcsec$ corresponds to a physical scale of $2.3\rm\; kpc$ at the redshift $z=0.128$ of the BCG" (Introduction)

## Data provenance

- ALMA projects: 2011.0.00374.S
- bands: Band 3 and Band 7  
  > "observed with the band 3 and the band 7 receivers on ALMA as a Cycle 0 Early Science program" (Data reduction)
- frequencies and spectral setup: 12CO(1-0) at 102.2 GHz (B3 USB), 12CO(3-2) at 306.7 GHz (B7 USB); 4 spws of 1.875 GHz; 0.488 MHz channels  
  > "Each spectral window had a bandwidth of $1.875\rm\; GHz$ and two spectral windows were set in each sideband" (Data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: extended, baselines out to 400 m, ~16 12m antennas  
  > "On average sixteen 12m antennas were used in the extended configuration with baselines out to $400\rm\; m$." (Data reduction)
- baselines: _not stated_
- angular resolution: 1.4x1.1 arcsec (CO 1-0); 0.55x0.39 arcsec (CO 3-2)  
  > "synthesized beam of $1.4\ensuremath{''}\times1.1\ensuremath{''}$ with PA $-79.1^{\circ}$ at CO(1-0)" (Data reduction)
- max recoverable scale: _not stated_
- sensitivity: rms 0.5 mJy (40 km/s chan) CO(1-0); 1.5 mJy (30 km/s chan) CO(3-2)  
  > "The rms noise in the line free channels was $0.5\rm\; mJy$ for $40\hbox{$\rm\; km\rm\; s^{-1}\,$}$ channels at CO(1-0)" (Data reduction)
- time on source: two 25 min obs in band 3; two 35 min obs in band 7  
  > "two 25 min observations in band 3 on March 27th and April 7th 2012 and in two 35 min observations in band 7" (Data reduction)
- observing dates: 27 March and 7 April 2012 (B3); 28 March 2012 (B7)  
  > "on March 27th and April 7th 2012 and in two 35 min observations in band 7 on March 28th 2012" (Data reduction)
- pi or archival as stated: _not stated_
- Line: 12CO J=1-0 (115.27 GHz)
- Line: 12CO J=3-2 (345.80 GHz)
- External data: U-band star formation rate ~20 Msun/yr  
  > "determine a star formation rate of $\sim20\hbox{$\hbox{$\rm\thinspace M_{\odot}$}\rm\; yr^{-1}\,$}$" (Discussion) [from Kirkpatrick09]
- External data: Infrared SFR 15 Msun/yr  
  > "the infrared star formation rate, $SFR_{\rm IR}=15\hbox{$\hbox{$\rm\thinspace M_{\odot}$}\rm\; yr^{-1}\,$}$ ((cite: ODea08))" (Discussion) [from ODea08]
- External data: FUV luminosity 1.7e43 erg/s  
  > "$L_{\rm UV} = 1.7\times10^{43}\hbox{$\rm\; erg\rm\; s^{-1}\,$}$ ((cite: ODea10))" (Discussion) [from ODea10]

## Processing

### Calibration

- pipeline or manual: CASA following ALMA support team processing scripts  
  > "following the detailed processing scripts provided by the ALMA science support team" (Data reduction)
- casa version: CASA 3.3  
  > "using the CASA software (version 3.3;" (Data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Mars (flux); 3C 279 (bandpass); J1246-257 phase  
  > "observations of Mars provided absolute flux calibration" (Data reduction)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN  
  > "reconstructed using the CASA task CLEAN" (Data reduction)
- deconvolver: _not stated_
- weighting robust: Briggs, robust 0.5  
  > "assuming Briggs weighting with a robustness parameter of 0.5" (Data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: simple polygon mask per channel  
  > "with a simple polygon mask applied to each channel" (Data reduction)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: integrated intensities corrected for primary beam response  
  > "The integrated line intensities have been corrected for the primary beam response." (Table 1)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.4x1.1 arcsec PA -79.1 (CO1-0); 0.55x0.39 arcsec PA -81.4 (CO3-2)  
  > "$0.55\ensuremath{''}\times0.39\ensuremath{''}$ with PA $-81.4^{\circ}$ at CO(3-2)" (Data reduction)
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum subtraction method/order
- Image size, cell size, clean threshold and iterations
- Channel binning used for spectra
- Spectral extraction details and baseline fitting
- Flux calibration uncertainty
- Pixel/region definitions for clumps A, B and HVS sub-regions
- PV slice widths
- Luminosity distance value used

## Analysis recipe

1. **Calibrate and image cubes and continuum**: CASA calibration with ALMA scripts; CLEAN cubes of continuum-subtracted data, Briggs robust 0.5, polygon masks; continuum from line-free channels  
  > "Images of the continuum emission were also produced with CLEAN by averaging channels free of any line emission." (Data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract spectra and fit line components**: Spectra from 6x6 arcsec (CO1-0) and 3x3 arcsec (CO3-2) regions fitted with two Gaussians  
  > "These spectral profiles were each fitted with two Gaussian components using the package MPFIT" (3.1)
   - software: MPFIT
   - fitting: two-Gaussian least squares; chi2/dof reported  
  > "100/94" (Table 1)
   - validation: larger 6x6 arcsec region at CO(3-2) gave consistent total flux  
  > "A larger $6\times6\rm\; arcsec$ region at CO(3-2) produces a consistent total flux but a significantly noisier spectrum." (3.1)
3. **Make moment maps and PV diagrams**: Integrated intensity maps over velocity ranges; PV cuts along PA 77 deg (systemic) and 120 deg (HVS), PA from 2D Gaussian fit  
  > "A two-dimensional Gaussian was fitted to the integrated intensity maps of the BCG systemic component to determine this best fit PA" (3.2)
   - fitting: _not stated_
   - validation: PA consistent between CO(1-0) and CO(3-2)  
  > "this was found to be consistent at both CO(1-0) and CO(3-2) within the error" (3.2)
4. **Derive molecular gas masses**: M_mol = 1.05e4 X_CO /(1+z) S_CO dv D_L^2 from CO(1-0) intensities  
  > "we calculated the molecular gas mass" (4.1)
   - assumption: Galactic X_CO = 2e20 cm-2 (K km/s)-1; z=0.128; H0=70, Om=0.3, OL=0.7  
  > "Under the assumption of the Galactic value $\rm X_{CO}=2\times 10^{20}" (4.1)
   - fitting: _not stated_
   - validation: Schmidt-Kennicutt placement and subsolar metallicity argue Galactic X_CO reasonable  
  > "Therefore, we argue that the Galactic $\rm X_{CO}$ value is likely to be reasonable." (4.1)
5. **Assess origin (merger, inflow, outflow) via energetics and Toomre Q**: Compare outflow energy with radiation pressure, supernova and AGN mechanical power; Toomre Q for putative disk  
  > "Mechanical winds from supernovae are therefore insufficient to accelerate the molecular gas." (4.4.1)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 3.3: calibration and imaging (CLEAN)  
  > "calibrated using the CASA software (version 3.3;" (Data reduction)
- **MPFIT** : two-Gaussian fits to spectra  
  > "fitted with two Gaussian components using the package MPFIT" (3.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total molecular gas mass | 1.1e10 | 0.1e10 | Msun | 4 | The total CO mass in the BCG is then $(1.1\pm0.1)\times 10^{10} |
| HVS mass | 5.0e9 | 0.7e9 | Msun | 4 | $1.5\pm0.2$ / $8.2\pm0.8$ / $170\pm20$ / $-568\pm8$ / $5.0\pm0.7$ |
| Systemic component mass | 5.7e9 | 1.0e9 | Msun | 4 | $M_{\rm disk} =
(5.7\pm1.0)\times 10^9 |
| Total CO(1-0) integrated intensity | 3.2 | 0.4 | Jy km/s | 2 | The total CO(1-0) integrated intensity of $3.2\pm0.4 |
| HVS velocity shift CO(1-0) | -568 | 8 | km/s | 2 | $-568\pm8$ |
| Continuum flux band 3 | 2.5 | 0.2 | mJy | 1 | with flux $2.5\pm0.2\rm\; mJy$ in band 3 |
| Continuum flux band 7 | 1.1 | 0.1 | mJy | 1 | $1.1\pm0.1\rm\; mJy$ in band 7 |

## Qualitative findings

- Systemic component shows smooth velocity gradient consistent with solid-body rotation but highly asymmetric  
  > "the mass and velocity structure are highly asymmetric and could indicate an inflow of gas in the process of forming a relaxed disk" (Conclusions)

## Claim tuples

- H: The BCG hosts massive molecular gas flows | E: ALMA CO(1-0) and CO(3-2) spectra and maps | R: Two components, systemic and HVS at -570 km/s, each ~5e9 Msun | F: Two massive molecular gas flows | **supported**
- H: HVS is an AGN-driven outflow | E: Energetics compared with radiation, supernovae and AGN power | R: Outflow needs ~35% of AGN mechanical energy; radiation and SNe insufficient | F: Outflow most likely AGN-driven, though inflow cannot be excluded | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Merger origin considered unlikely  
  > "A merger origin for the high velocity system is possible but we consider it unlikely." (Conclusions)
- How they decided it was enough: _not stated_
- Limitation (authors): Cannot tell whether gas lies in front of or behind the BCG  
  > "we cannot distinguish between an inflow of gas located behind the BCG and an outflow of gas located in front of the BCG." (4.4)
- Caveat (inferred, ours): X_CO assumed Galactic; masses scale with it
- Caveat (inferred, ours): Interferometer may resolve out flux (half of IRAM flux)
- Caveat (inferred, ours): Inflow vs outflow ambiguous without absorption
- Caveat (inferred, ours): Outflow age and AGN power uncertain by an order of magnitude

## Reproducibility

- Data public (paper): ALMA Cycle 0 data acknowledged with project ID  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00374.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Line-free channel ranges
- Missing: Image and cell sizes, clean threshold
- Missing: Region definitions for clumps
- Data volume (inferred): ~10-30 GB
- Score (inferred): 3/5, Simple recipe, public Cycle 0 data, but imaging and extraction details are sparse.
- Rediscovery candidate: yes, Public data, simple recipe, numeric Gaussian-fit and mass results.

## Links

- Companion: McNamara et al. submitted (Abell 1835 ALMA molecular outflow)

## Checks

```json
{
 "quotes": 50,
 "quotes_ok": 50,
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
  "facts": 67,
  "stated": 37,
  "rate": 0.552
 },
 "evidence_ok": true
}
```

# ALMA Observations of a Misaligned Binary Protoplanetary Disk System in Orion

`2014ApJ...796..120W` | The Astrophysical Journal 2014 | first author: Williams, Jonathan P. | arXiv: 1410.3570 | DOI: 10.1088/0004-637X/796/2/120

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Are the disks in the wide binary 253-1536 (V2434 Ori) aligned, and what do their kinematics say about the stellar masses and binary formation?  
  > "These data allow us to examine disk masses, kinematics, and chemistry, as well as constrain the masses of their central stars." (Introduction)
- Target **253-1536 (V2434 Ori) A and B**: coordinates A: 05:35:25.30 -05:15:35.40; B: 05:35:25.23 -05:15:35.69  
  > "corresponding to 440 AU at our assumed distance to Orion of 400 pc" (Introduction); "| 253-1536A | 05:35:25.30 | -05:15:35.40 |" (Table 1); z/distance 400 pc (assumed)  
  > "corresponding to 440 AU at our assumed distance to Orion of 400 pc" (Introduction); "| 253-1536A | 05:35:25.30 | -05:15:35.40 |" (Table 1); distance from Sandstrom et al. 2007; Menten et al. 2007  
  > "corresponding to 440 AU at our assumed distance to Orion of 400 pc" (Introduction); "| 253-1536A | 05:35:25.30 | -05:15:35.40 |" (Table 1)

## Data provenance

- ALMA projects: 2011.0.00028.S
- bands: 856 um (350.5 GHz) continuum; lower and upper sidebands  
  > "the $856\,\mu$m (350.5 GHz) continuum" (Observations)
- frequencies and spectral setup: Hanning smoothed, 488.28 kHz channels, ~0.42 km/s  
  > "The Hanning smoothed spectral resolution of these data is $d\nu = 488.28$ kHz corresponding to velocity channels of $dv \simeq 0.42$ ${\rm km~s^{-1}}$." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.5 arcsec  
  > "The resolution of the continuum and line maps, $\sim 0.5\ensuremath{''}$" (Observations)
- max recoverable scale: 5 arcsec  
  > "less than the maximum recoverable scale of $5''$ so no emission is resolved out" (Observations)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Cycle 0 Orion proplyd study of Mann et al. 2014 (fifth field)  
  > "Cycle 0 (project 2011.0.00028.S) study of the Orion proplyds by (cite: 2014ApJ...784...82M)" (Observations)
- Line: CO 3-2 (not stated)
- Line: CS 7-6 (not stated)
- Line: HCO+ 4-3 (not stated)
- Line: HCN 4-3 (not stated)
- Other facility **HST**: Optical image and silhouette disk size for inclination  
  > "based on the $0.6\ensuremath{''}\times 1.4\ensuremath{''}$ size of the optical shadow" (Analysis of HCO$^+$ data)
- External data: X-Shooter spectral types of components (F/G for A, M2 for B), masses 2.5-4 Msun and 0.4 Msun  
  > "The lack of prominent absorption lines led them to conclude that the star is heavily veiled and is spectral type F or G." (Analysis of HCO$^+$ data) [from (cite: 2011ApJ...739L...8R)]
- External data: Optical shadow size of silhouette disk used for inclination of A  
  > "based on the $0.6\ensuremath{''}\times 1.4\ensuremath{''}$ size of the optical shadow" (Analysis of HCO$^+$ data) [from (cite: 2005AJ....129..382S)]
- External data: Continuum-based disk masses and flux calibration error of 10%  
  > "The error due to flux calibration is estimated to be about 10% (cite: 2014ApJ...784...82M)." (Results) [from (cite: 2014ApJ...784...82M)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~10%  
  > "The error due to flux calibration is estimated to be about 10% (cite: 2014ApJ...784...82M)." (Results)
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

- Data acquisition and reduction  
  > "wherein the details of the data acquisition and reduction can be found" (Observations) [from (cite: 2014ApJ...784...82M)]
- Fitting elliptical gaussians to channel maps  
  > "we fit elliptical gaussians to the channel maps as in (cite: 2012Natur.492...83T)" (Analysis of HCO$^+$ data) [from (cite: 2012Natur.492...83T)]
- Angle between rotation axes formula  
  > "as in (cite: 2014Natur.511..567J)" (Analysis of HCO$^+$ data) [from (cite: 2014Natur.511..567J)]

### Not stated but needed to reproduce (our reading)

- Calibration, CASA version, imaging parameters (robust, cell, masking), continuum subtraction and line-free channels (all deferred to Mann et al. 2014)
- Rest frequencies and velocity range used for moment maps
- How the cloud CO contamination and the overlap between disks were handled in flux measurement
- Aperture or region used for integrated fluxes
- Details of the Keplerian curve comparison in Fig 5 (which channels, how radius defined)
- Assumed temperature and opacity for disk masses

## Analysis recipe

1. **Make moment and channel maps**: Continuum, integrated and first-moment maps of four lines; channel maps of HCO+ 4-3  
  > "The first moment (intensity weighted mean velocity) of each line is shown in the right panels of Figure" (Moment Maps)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit centroids and disk position angles**: Elliptical Gaussian fits to channel maps, linear fits to centroids to get PA  
  > "Through linear fits to the positions of the centroids, we determine the projected rotational planes of the two disks." (Analysis of HCO$^+$ data)
   - parameter: Velocity channels binned by 2 for independent points  
  > "we binned the velocity channels by 2 to provide independent points for the purpose of making the linear fits." (Footnote 1)
   - fitting: Linear fits to centroid positions  
  > "Through linear fits to the positions of the centroids, we determine the projected rotational planes of the two disks." (Analysis of HCO$^+$ data)
   - validation: _not stated_
3. **Derive true angle between disk axes**: Dot-product formula with i_A=65±5 deg, i_B unknown, sin(i) prior, posterior mean and std  
  > "For random orientations, the probability of a particular inclination is proportional to the sine of the inclination" (Analysis of HCO$^+$ data)
   - assumption: Random orientation prior for i_B; i_A from optical shadow  
  > "Using this as a prior, and without attempting to fit the observations further" (Analysis of HCO$^+$ data)
   - fitting: _not stated_
   - validation: _not stated_
4. **Estimate stellar masses from rotation**: Compare position-velocity offsets to Keplerian profile; lower limit for B from velocity gradient  
  > "to provide a rough estimate of the central stellar mass." (Analysis of HCO$^+$ data)
   - assumption: i_A=65 deg; distance 400 pc  
  > "With a well constrained inclination, $i_{\rm A}=65^\circ$, as discussed above, we infer $M_*\sim 3.5\,M_\odot$." (Analysis of HCO$^+$ data)
   - fitting: No detailed model; data insufficient  
  > "The resolution and signal-to-noise ratio of the data are insufficient to attempt a more detailed model and more rigorous fitting" (Analysis of HCO$^+$ data)
   - validation: Compared with X-Shooter spectral types and Hillenbrand 1997 catalog  
  > "The moderately high stellar mass for this optically faint star is consistent with the X-Shooter ultraviolet-optical-infrared spectrum" (Analysis of HCO$^+$ data)

## Software

- **Astropy** : Acknowledged as used in the work  
  > "This work made use of Astropy, a community-developed core Python package for Astronomy" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Position angle of A | 69.7 | 1.4 | deg | 2 | $PA_{\rm A}=69.7\pm 1.4^\circ$ and $PA_{\rm B}=136\pm 15^\circ$ |
| Position angle of B | 136 | 15 | deg | 2 | $PA_{\rm A}=69.7\pm 1.4^\circ$ and $PA_{\rm B}=136\pm 15^\circ$ |
| Angle between disk rotation axes | 72 | 20 | deg | 3 | $\Delta = 72^\circ\pm 20^\circ$ |
| Stellar mass of A | ~3.5 | not stated | Msun | 4 | we infer $M_*\sim 3.5\,M_\odot$ |
| Stellar mass of B lower limit | >~0.2/sin^2 i_B | not stated | Msun | 4 | $M_* \gtrsim 0.2\,M_\odot/\sin^2\,i_{\rm B}$ |
| Systemic velocities A and B | 10.55 and 10.85 | ~0.1 | km/s | 2 | $v_{\rm sys}=10.55$ and 10.85 ${\rm km~s^{-1}}$ respectively, with errors of about 0.1 |
| Continuum flux A / B | 0.163 / 0.061 | ~10% | Jy | 1 | / Continuum$^{a}$   /   0.163   /   0.061   / Jy             / |
| HCO+ 4-3 flux A / B | 10.5 / 2.7 | ~30% | Jy km/s | 1 | / HCO$^+$ 4–3$^{c}$ /   10.5    /    2.7    / Jy km s$^{-1}$ / |
| Disk masses A / B | 0.074 / 0.028 | not stated | Msun | 0 | we estimate disk masses of $0.074\,M_\odot$ and $0.028\,M_\odot$ for sources 253-1536A and B respectively |

## Qualitative findings

- Both disks have strong CO, HCO+, HCN emission; CS detected only in A; line-to-continuum ratios similar  
  > "The line-to-continuum ratios are similar for the two disks in each of the lines." (abstract)

## Claim tuples

- H: Are the disks of the wide binary misaligned? | E: Measured velocity gradient PAs in HCO+ and computed true angle with inclination prior | R: Delta = 72±20 deg | F: System did not form from a single rigidly rotating structure; turbulence or dynamical interactions act on small scales | **supported**
- H: Do disk kinematics give stellar masses consistent with spectroscopy? | E: Keplerian comparison for A, gradient lower limit for B | R: M_A~3.5 Msun, M_B>~0.2/sin^2 i Msun | F: Consistent with spectral types; mass ratio ~9 | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: HCO+ chosen for best S/N and low cloud confusion  
  > "We use the HCO$^+$ data to analyze the velocity structure in more detail as they provide the best combination of high signal-to-noise ratio and low cloud confusion." (Moment Maps)
- How they decided it was enough: _not stated_
- Limitation (authors): Resolution and S/N insufficient for detailed modeling; CO fluxes unreliable due to cloud confusion; B inclination unknown  
  > "The CO fluxes are unreliable measures of the true disk emission due to the aforementioned cloud confusion." (Results)
- Caveat (inferred, ours): Mass estimate is rough, no uncertainty given
- Caveat (inferred, ours): Misalignment relies on a sin(i) prior for B
- Caveat (inferred, ours): Possible cloud contamination and outflow contribution in kinematics

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Full calibration and imaging recipe (in Mann et al. 2014)
- Missing: Details of centroid fits and Keplerian comparison
- Data volume (inferred): ~10-50 GB for the Cycle 0 dataset
- Score (inferred): 3/5, Data from a single archival project with simple analysis, but processing is deferred to another paper and key steps are loosely described.
- Rediscovery candidate: no, Data are likely public but the recipe is incomplete and the mass estimate is rough.

## Links

- Method: (cite: 2014ApJ...784...82M) (Data acquisition and reduction)
- Method: (cite: 2014Natur.511..567J) (Angle between rotation axes formula)
- Method: (cite: 2012Natur.492...83T) (Centroid fitting of channel maps)
- Companion: (cite: 2014ApJ...784...82M) (Same ALMA Cycle 0 Orion proplyd dataset, continuum dust masses)
- Companion: (cite: 2009ApJ...699L..55M) (SMA discovery of the two disks)
- Related: ALMA Cycle 0 Orion proplyd study

## Checks

```json
{
 "quotes": 51,
 "quotes_ok": 51,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 31,
  "rate": 0.456
 },
 "evidence_ok": true
}
```

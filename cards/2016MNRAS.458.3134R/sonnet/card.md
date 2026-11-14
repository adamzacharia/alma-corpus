# ALMA observations of cold molecular gas filaments trailing rising radio bubbles in PKS 0745-191

`2016MNRAS.458.3134R` | Monthly Notices of the Royal Astronomical Society 2016 | first author: Russell, H. R. | arXiv: 1602.05962 | DOI: 10.1093/mnras/stw409

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: galaxy_clusters_and_sz, nearby_galaxies
- Question: What are the distribution, kinematics and origin of the cold molecular gas in the PKS 0745-191 BCG, and is it lifted by radio bubbles, cooled in situ, or inflowing?  
  > "The ALMA observations now resolve the spatial and velocity structure of the cold molecular gas structures at the centre of the BCG revealing extended filaments trailing the two buoyant radio bubbles." (1 Introduction)
- Target **PKS 0745-191 BCG**: coordinates RA 07:47:31.32, Dec -19:17:39.97 (J2000)  
  > "The observations were centred on the nucleus of PKS 0745-191 (RA 07:47:31.32, Dec -19:17:39.97, J2000)" (2 Data reduction); "at the central galaxy’s redshift ($z=0.1028$; (cite: Hunstead78)) 1 arcsec corresponds to $1.9\rm\; kpc$" (1 Introduction); z/distance z = 0.1028; 1 arcsec = 1.9 kpc (H0=70)  
  > "The observations were centred on the nucleus of PKS 0745-191 (RA 07:47:31.32, Dec -19:17:39.97, J2000)" (2 Data reduction); "at the central galaxy’s redshift ($z=0.1028$; (cite: Hunstead78)) 1 arcsec corresponds to $1.9\rm\; kpc$" (1 Introduction); distance from Hunstead78 redshift from optical emission lines  
  > "The observations were centred on the nucleus of PKS 0745-191 (RA 07:47:31.32, Dec -19:17:39.97, J2000)" (2 Data reduction); "at the central galaxy’s redshift ($z=0.1028$; (cite: Hunstead78)) 1 arcsec corresponds to $1.9\rm\; kpc$" (1 Introduction)

## Data provenance

- ALMA projects: 2012.1.00837.S
- bands: Band 3 (CO(1-0)) and Band 7 (CO(3-2)), Cycle 1  
  > "to cover the CO(1-0) line at $104.53\rm\; GHz$ in band 3 and the CO(3-2) line at $313.56\rm\; GHz$ in band 7" (2 Data reduction)
- frequencies and spectral setup: FDM, 1.875 GHz bandwidth, 488.3 kHz resolution, channels binned; extra baseband for continuum  
  > "The frequency division correlator mode was used with a $1.875\rm\; GHz$ bandwidth and frequency resolution of $488.3\rm\; kHz$" (2 Data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 20-560 m at CO(1-0); 34-1100 m at CO(3-2); 32-36 antennas  
  > "The observations utilised $32-36$ antennas with baselines of $20-560\rm\; m$ at CO(1-0) and a more extended configuration with baselines of $34-1100\rm\; m$ at CO(3-2)." (2 Data reduction)
- angular resolution: 1.6''x1.2'' (PA 79.7°) at CO(1-0); 0.27''x0.19'' (PA 78.3°) at CO(3-2)  
  > "This provided a synthesized beam of $1.6\ensuremath{''}\times1.2\ensuremath{''}$ with a position angle (P.A.) of $79.7^{\circ}$ at CO(1-0)" (2 Data reduction)
- max recoverable scale: _not stated_
- sensitivity: rms 0.6 mJy (CO(1-0)) and 1 mJy (CO(3-2)) per 10 km/s channel  
  > "The rms noise in the line-free channels was $0.6\rm\; mJy$ at CO(1-0) and $1\rm\; mJy$ at CO(3-2) for $10\hbox{$\rm\; km\rm\; s^{-1}\,$}$ channels." (2 Data reduction)
- time on source: two 8 min Band 3 observations; one 25 min Band 7 observation  
  > "The data were taken in two 8 minute observations in band 3 on 2014 April 26 and 27 and in a 25 minute observation in band 7 on 2014 August 19." (2 Data reduction)
- observing dates: 2014 Apr 26-27 (Band 3); 2014 Aug 19 (Band 7)  
  > "on 2014 April 26 and 27 and in a 25 minute observation in band 7 on 2014 August 19" (2 Data reduction)
- pi or archival as stated: PI McNamara  
  > "(ID = 2012.1.00837.S; PI McNamara)" (2 Data reduction)
- Line: CO J=1-0 (115.27 GHz)
- Line: CO J=3-2 (345.80 GHz)
- Other facility **HST**: FUV (F140LP) and F555W images for star formation and dust lanes  
  > "HST FUV observations show a clear UV excess at the centre of the BCG extending to the W of the nucleus" (3.6 Star formation in the BCG)
- Other facility **Chandra**: X-ray cavities and hot gas properties (via Sanders14)  
  > "located to the N and SE in *Chandra* observations" (4.4 Molecular gas clouds lifted by radio bubbles?)
- Other facility **VLA 14.9 GHz**: radio nucleus and W extension (Baum91)  
  > "The VLA $14.9\rm\; GHz$ observation with a resolution of $\sim0.15\ensuremath{''}$ shows a bright nucleus" (4.4 Molecular gas clouds lifted by radio bubbles?)
- External data: IRAM 30m CO(1-0) flux 1.8±0.4 Jy km/s and single-dish mass  
  > "IRAM $30\rm\; m$ single dish signal of $1.8\pm0.4\hbox{$\rm\; Jy\rm\; km\rm\; s^{-1}\,$}$ ((cite: Salome03))" (3.1 Gas distribution) [from (cite: Salome03)]
- External data: X-ray cooling rate 270±90 Msun/yr, hot gas pressure, g, metallicity  
  > "the X-ray cooling rate of $270\pm90\hbox{$\hbox{$\rm\thinspace M_{\odot}$}\rm\; yr^{-1}\,$}$ determined from XMM-RGS spectroscopy ((cite: Sanders14))" (4.1 Origin of the molecular gas) [from (cite: Sanders14)]
- External data: K-band effective radius 9.5 arcsec from 2MASS  
  > "estimated from the K-band effective radius of $9.5\rm\; arcsec$ given by the 2MASS extended source catalogue" (4.2 free-fall) [from (cite: Skrutskie06)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline reduction scripts plus additional self-calibration  
  > "using the ALMA pipeline reduction scripts and additional self-calibration significantly improved the image quality" (2 Data reduction)
- casa version: CASA 4.2.2  
  > "The observations were calibrated in CASA version 4.2.2 ((cite: McMullin07))" (2 Data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: applied; details not given  
  > "additional self-calibration significantly improved the image quality" (2 Data reduction)

### Imaging

- task: _not stated_
- deconvolver: CLEAN with Briggs weighting  
  > "The continuum-subtracted images were reconstructed using CLEAN and various Briggs weightings were explored" (2 Data reduction)
- weighting robust: robust 0.5 for CO(1-0); robust 2 for CO(3-2)  
  > "A robustness parameter of 0.5 was used for the CO(1-0) cube and a value of 2 was used to maximise the signal-to-noise in the CO(3-2) cube." (2 Data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum-subtracted cubes; continuum from line-free channels  
  > "Images of the continuum emission were also produced by averaging channels free of any line emission." (2 Data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: CO(3-2) convolved to the CO(1-0) beam for line ratios; 10 km/s channels  
  > "The CO(3-2) dataset was convolved with a 2D Gaussian to match the CO(1-0) synthesized beam" (3.2 Line ratio)
- final beam: 1.6''x1.2'' (CO 1-0); 0.27''x0.19'' (CO 3-2)  
  > "$0.27\ensuremath{''}\times0.19\ensuremath{''}$ with a P.A. of $78.3^{\circ}$ at CO(3-2)" (2 Data reduction)
- final rms: 0.6 mJy (CO 1-0), 1 mJy (CO 3-2) per 10 km/s  
  > "The rms noise in the line-free channels was $0.6\rm\; mJy$ at CO(1-0)" (2 Data reduction)

### Inherited from earlier work

- Hernquist potential free-fall model  
  > "Following (cite: Lim08), we assume a Hernquist model for the gravitational potential of an elliptical galaxy" (4.2 free-fall) [from (cite: Lim08)]
- Filament column and surface density for magnetic support  
  > "Following (cite: Fabian08), for a radial filament the lengthwise column density" (4.5 Forming molecular gas) [from (cite: Fabian08)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for continuum subtraction
- Self-calibration solution intervals and number of iterations
- Clean masks, thresholds, image size and cell size
- Flux calibrator and flux scale uncertainty
- Channel binning applied to each cube
- Distance/luminosity distance value used in mass formula
- Exact region definitions for filaments (beyond figures)

## Analysis recipe

1. **Calibrate and image**: ALMA pipeline calibration in CASA, self-calibration, CLEAN continuum-subtracted cubes with Briggs weighting  
  > "The observations were calibrated in CASA version 4.2.2 ((cite: McMullin07)) using the ALMA pipeline reduction scripts" (2 Data reduction)
   - software: CASA
   - parameter: robust 0.5 (Band 3), 2 (Band 7); 10 km/s channels  
  > "A robustness parameter of 0.5 was used for the CO(1-0) cube and a value of 2 was used" (2 Data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit total spectra**: Single Gaussian fit to spectra from 6''x6'' (CO 1-0) and 4''x4'' (CO 3-2) regions, corrected for primary beam and instrumental broadening  
  > "Each spectrum was fitted with a single Gaussian component using the package MPFIT" (3.1 Gas distribution)
   - software: MPFIT
   - fitting: Gaussian least-squares (chi2/dof reported)  
  > "Total | 1079/1061" (Table 1)
   - validation: Larger regions give consistent fluxes; comparison with IRAM 30m flux  
  > "Larger regions produce consistent total fluxes but significantly noisier spectra." (3.1 Gas distribution)
3. **Line ratios**: Convolve CO(3-2) to CO(1-0) beam, fit integrated intensities in K km/s in matched regions, ratio  
  > "the integrated intensities (in $\hbox{$\rm\; K\rm\; km\rm\; s^{-1}\,$}$) were determined from spectral fitting to each dataset using matching CO(1-0) beam-sized regions" (3.2 Line ratio)
   - software: MPFIT
   - assumption: optically thick, thermalized CO gives excitation temperature  
  > "Assuming that the CO emission is optically thick and the gas is thermalized, the line ratios indicate an excitation temperature of $20-30\rm\; K$." (3.2 Line ratio)
   - fitting: _not stated_
   - validation: _not stated_
4. **Velocity maps**: Fit one or two Gaussians to beam-sized spectra at each pixel; require 3 sigma detection via Monte Carlo  
  > "we required at least $3\sigma$ significance for the detection of a line determined using Monte Carlo simulations" (3.3 Velocity structure)
   - software: MPFIT
   - assumption: systemic velocity from optical emission lines (z=0.1028)  
  > "our conclusions on the velocity structure of the molecular gas depend on the redshift from the emission line gas" (1 Introduction)
   - fitting: 1 or 2 Gaussian components  
  > "These spectra were fitted with one or two Gaussian components using MPFIT" (3.3 Velocity structure)
   - validation: _not stated_
5. **PV cuts**: Position-velocity cuts along each CO(3-2) filament, summed across 0.2-0.3 arcsec width  
  > "which summed the line emission across the width of each filament ($0.2-0.3\rm\; arcsec$)" (3.4 Velocity profiles)
   - fitting: _not stated_
   - validation: _not stated_
6. **Molecular gas mass**: M_mol from CO(1-0) integrated intensity with Galactic X_CO  
  > "The molecular gas mass can be calculated from the integrated CO(1-0) intensity ($S_{\mathrm{CO}}\Delta\nu$) under the assumption of a Galactic CO-to-H$_2$ conversion factor" (3.5 Molecular gas mass)
   - assumption: X_CO = 2e20 cm^-2 (K km/s)^-1; filament masses assume CO(1-0) and CO(3-2) distributed similarly  
  > "where $X_{\mathrm{CO}}=2\times10^{20}\hbox{$\hbox{$\rm\; cm^{-2}\,$}(\rm\; K\hbox{$\rm\; km\rm\; s^{-1}\,$})^{-1}$}$ in the Milky Way disk" (3.5 Molecular gas mass)
   - fitting: _not stated_
   - validation: Discussed X_CO uncertainty (factor of a few) does not alter conclusions  
  > "Our conclusions are not qualitatively altered by the estimated factor of a few uncertainty." (3.5 Molecular gas mass)
7. **Free-fall comparison**: Hernquist-potential free-fall velocity vs radius, varying inclination  
  > "the inclination is the main parameter that can be altered to match the velocity structure" (4.2 free-fall)
   - parameter: scale radius 10 kpc; total mass ~2e12 Msun (X-ray) or 1.8e13 (lensing)  
  > "The scale radius of $10\rm\; kpc$ was estimated from the K-band effective radius of $9.5\rm\; arcsec$" (4.2 free-fall)
   - fitting: _not stated_
   - validation: Both mass estimates considered  
  > "We have considered both estimates of the total mass in our analysis." (4.2 free-fall)

## Software

- **CASA** 4.2.2: calibration and imaging  
  > "The observations were calibrated in CASA version 4.2.2" (2 Data reduction)
- **MPFIT** : Gaussian fitting of spectra  
  > "fitted with a single Gaussian component using the package MPFIT" (3.1 Gas distribution)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total molecular gas mass | 4.6e9 | ±0.3e9 | Msun | 6 | the total molecular gas mass is $(4.6\pm0.3)\times10^9\hbox{$\rm\thinspace M_{\odot}$}$ |
| Total CO(1-0) integrated intensity | 2.2 | ±0.1 | Jy km/s | 2 | Total / 1079/1061 / $2.2\pm0.1$ |
| Total CO(3-2) integrated intensity | 18.6 | ±1.4 | Jy km/s | 2 | Total / 350/357 / $18.6\pm1.4$ |
| CO(3-2)/CO(1-0) line ratio, BCG centre | 0.81 | ±0.05 | dimensionless | 3 | CO(3-2)/CO(1-0)$=0.81\pm0.05$ |
| CO(3-2)/CO(1-0) line ratio, SW filament | 0.53 | ±0.07 | dimensionless | 3 | CO(3-2)/CO(1-0)$=0.53\pm0.07$ |
| Continuum flux at 103.8 GHz | 9.30 | ±0.04 | mJy | 1 | flux $9.30\pm0.04\rm\; mJy$ at $103.8\rm\; GHz$ |
| Continuum flux at 314.8 GHz | 4.6 | ±0.2 | mJy | 1 | $4.6\pm0.2\rm\; mJy$ at $314.8\rm\; GHz$ |
| SE filament mass | ~1.9e9 | not stated | Msun | 6 | The SE filament is likely the most massive with $\sim1.9\times10^{9}\hbox{$\rm\thinspace M_{\odot}$}$. |
| Required magnetic field strength | ~400 | not stated | microG | 0 | The corresponding magnetic field strength $B\sim400\hbox{$\rm\thinspace {\mu}\mathrm{G}$}$ |

## Qualitative findings

- Molecular gas lies in three filaments (N, SE, SW) of 3-5 kpc, with velocities within ±100 km/s and FWHM below the stellar velocity dispersion  
  > "The velocities of the molecular clouds in the filaments are low, lying within $\pm100\hbox{$\rm\; km\rm\; s^{-1}\,$}$ of the galaxy’s systemic velocity." (abstract)

## Claim tuples

- H: Are the filaments free-falling cooling gas or a merger remnant? | E: Compared observed velocity gradients with Hernquist free-fall models | R: Observed gradients require orientation <20° from plane of sky; free-fall would give ~250 km/s | F: Velocities inconsistent with free-fall or merger origin | **supported**
- H: Were the filaments lifted by radio bubbles? | E: Compared filament positions to X-ray cavities and energetics | R: N and SE filaments (60-70% of gas) lie under cavities; direct uplift needs very high coupling | F: Likely formed in the updraft by in situ cooling of lifted gas rather than direct uplift | **partially**
- H: Are the filaments long-lived? | E: Estimated dynamical ages and required magnetic pressure | R: Dynamical ages 1-2e7 yr; B~400 microG needed | F: Filaments transient unless magnetically supported | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Briggs weighting explored per band; robust 2 chosen to maximise S/N in CO(3-2)  
  > "a value of 2 was used to maximise the signal-to-noise in the CO(3-2) cube" (2 Data reduction)
- Alternative: Merger/ram pressure stripping and free-fall inflow rejected; lower X_CO considered but not supported  
  > "Mergers between the BCG and donor galaxies are likely rare due to the dearth of gas-rich galaxies at the centres of rich clusters" (4.1 Origin of the molecular gas)
- How they decided it was enough: _not stated_
- Limitation (authors): Systemic velocity from emission lines may be offset from the stellar potential; line-of-sight location unconstrained  
  > "it is difficult to constrain the physical location of the structure along the line of sight." (3.1 Gas distribution)
- Limitation (authors): X_CO uncertain by a factor of a few  
  > "the Galactic conversion factor is not expected or observed to be universal" (3.5 Molecular gas mass)
- Caveat (inferred, ours): Mass depends strongly on the assumed Galactic X_CO
- Caveat (inferred, ours): Filament widths unresolved so magnetic pressure is a lower limit
- Caveat (inferred, ours): Systemic velocity from emission lines rather than stars
- Caveat (inferred, ours): Inclination and line-of-sight geometry unconstrained

## Reproducibility

- Data public (paper): Data acknowledged as ALMA project 2012.1.00837.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA 2012.1.00837.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Self-calibration parameters
- Missing: Clean masks and image/cell sizes
- Missing: Line-free channel ranges
- Missing: Region definitions for spectral extraction in filaments
- Missing: Luminosity distance used
- Data volume (inferred): ~20-50 GB raw for the two Cycle 1 execution sets
- Score (inferred): 6/5, Public data and a fairly clear recipe with key numbers, but imaging and self-calibration details are missing.
- Rediscovery candidate: yes, Public data, simple Gaussian fits and mass formula, numeric results such as the 4.6e9 Msun mass and line ratios.

## Links

- Method: (cite: Lim08) (Hernquist free-fall model)
- Method: (cite: Fabian08) (magnetic support of filaments)
- Companion: (cite: Sanders14) (X-ray analysis of PKS 0745-191)
- Companion: (cite: McNamara14) (ALMA molecular outflow in A1835)
- Related: 2MASS extended source catalogue

## Checks

```json
{
 "quotes": 73,
 "quotes_ok": 73,
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
  "facts": 83,
  "stated": 54,
  "rate": 0.651
 },
 "evidence_ok": true
}
```

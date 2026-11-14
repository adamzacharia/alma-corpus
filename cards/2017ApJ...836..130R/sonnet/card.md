# Alma Observations of Massive Molecular Gas Filaments Encasing Radio Bubbles in the Phoenix Cluster

`2017ApJ...836..130R` | The Astrophysical Journal 2017 | first author: Russell, H. R. | arXiv: 1611.00017 | DOI: 10.3847/1538-4357/836/1/130

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: galaxy_clusters_and_sz, nearby_galaxies
- Question: How is the molecular gas in the Phoenix cluster central galaxy distributed and moving relative to the radio bubbles, and is it consistent with free-fall?  
  > "Here we present new ALMA observations of the CO(3-2) emission from the molecular gas in the central galaxy of the Phoenix cluster." (Introduction)
- Target **Phoenix cluster BCG (SPT-CLJ2344-4243)**: coordinates continuum source RA 23:44:43.902, Dec -42:43:12.53  
  > "At the redshift of the Phoenix cluster $z=0.596$ ((cite: Ruel14); (cite: McDonald15)), 1 arcsec corresponds to $6.75\rm\; kpc$." (Introduction); "An unresolved central continuum source was detected at RA 23:44:43.902, Dec -42:43:12.53" (3.4 AGN continuum); z/distance z = 0.596; 1 arcsec = 6.75 kpc  
  > "At the redshift of the Phoenix cluster $z=0.596$ ((cite: Ruel14); (cite: McDonald15)), 1 arcsec corresponds to $6.75\rm\; kpc$." (Introduction); "An unresolved central continuum source was detected at RA 23:44:43.902, Dec -42:43:12.53" (3.4 AGN continuum); distance from Ruel14; McDonald15  
  > "At the redshift of the Phoenix cluster $z=0.596$ ((cite: Ruel14); (cite: McDonald15)), 1 arcsec corresponds to $6.75\rm\; kpc$." (Introduction); "An unresolved central continuum source was detected at RA 23:44:43.902, Dec -42:43:12.53" (3.4 AGN continuum)

## Data provenance

- ALMA projects: 2013.1.01302.S
- bands: CO(3-2) at 216.66 GHz plus continuum basebands at 219.5, 230.5, 232.5 GHz  
  > "simultaneously covering the CO(3-2) line at $216.66\rm\; GHz$ and the sub-mm continuum emission in three additional basebands at 219.5, 230.5 and $232.5\rm\; GHz$" (Data reduction)
- frequencies and spectral setup: 1.875 GHz bandwidth, 7812 kHz resolution, binned to 12 km/s  
  > "with a $1.875\rm\; GHz$ bandwidth and frequency resolution of $7812\rm\; kHz$" (Data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 20-650 m, 35 antennas  
  > "The observations utilised 35 antennas with baselines of $20-650\rm\; m$." (Data reduction)
- angular resolution: 0.60 x 0.56 arcsec, P.A. -37.9 deg (line cube)  
  > "synthesized beam of $0.60\rm\; arcsec\times0.56\rm\; arcsec$ with P.A. $=-37.9\deg$" (Data reduction)
- max recoverable scale: _not stated_
- sensitivity: 0.3 mJy/beam per 12 km/s channel; continuum 0.019 mJy/beam  
  > "The rms noise in the line-free channels was $0.3\hbox{$\rm\; mJy{\rm /beam}$}$ at CO(3-2) for $12\hbox{$\rm\; km\rm\; s^{-1}\,$}$ channels." (Data reduction)
- time on source: 58.5 min, nine ~6 min observations  
  > "The total time on source was $58.5\min$ split into nine $\sim6\min$ observations" (Data reduction)
- observing dates: 15 and 16 June 2014 (Cycle 2)  
  > "was observed by ALMA on 15 and 16 June 2014 (Cycle 2" (Data reduction)
- pi or archival as stated: PI McDonald  
  > "(Cycle 2, ID 2013.1.01302.S; PI McDonald)" (Data reduction)
- Line: CO 3-2 (216.66 GHz (observed))
- Other facility **Chandra**: X-ray cavities and hot atmosphere profile for mass modelling  
  > "The filaments are draped around the rims of two large X-ray cavities (Fig. [2](#fig:filimg), left) detected in deep *Chandra* X-ray observations" (Results)
- Other facility **SMA**: earlier CO(3-2) flux and continuum for comparison  
  > "the integrated intensity measured by the SMA of $5.3\pm1.4\hbox{$\rm\; Jy\rm\; km\rm\; s^{-1}\,$}$" (Results)
- External data: Chandra X-ray cavity properties and cavity enthalpy  
  > "the cavity enthalpy was estimated as $4.4-6.7\times10^{59}\rm\; erg$" (Discussion) [from McDonald15]
- External data: Effective radius ~17 kpc from HST imaging  
  > "determine an effective radius of $\sim17\rm\; kpc$ from HST imaging in five photometric bands" (Discussion) [from McDonald12]
- External data: Ionized gas [OIII] velocity structure  
  > "The strong velocity gradients in the molecular gas are comparable to those observed for the warm ionized gas ((cite: McDonald14))." (Results) [from McDonald14]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline reduction scripts  
  > "The observations were calibrated in CASA version 4.3.1 ((cite: McMullin07)) using the ALMA pipeline reduction scripts." (Data reduction)
- casa version: CASA 4.3.1  
  > "The observations were calibrated in CASA version 4.3.1" (Data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: phase calibrator quasar J2357-5311 also used for bandpass and flux  
  > "This bright quasar was also observed for bandpass and flux calibration." (Data reduction)
- flux scale uncertainty: _not stated_
- self calibration: Tried; no significant improvement  
  > "Additional self-calibration did not produce significant improvement in the image quality." (Data reduction)

### Imaging

- task: CLEAN and UVCONTSUB  
  > "Continuum-subtracted data cubes were generated using CLEAN and UVCONTSUB." (Data reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The final data cube used natural weighting" (Data reduction)
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
- final beam: 0.60x0.56 arcsec PA -37.9 deg (cube); continuum 0.59x0.53 arcsec PA -48.7 deg  
  > "the synthesized beam was $0.59\rm\; arcsec\times0.53\rm\; arcsec$ with P.A. $=-48.7\deg$" (Data reduction)
- final rms: 0.3 mJy/beam per 12 km/s channel; continuum 0.019 mJy/beam  
  > "An image of the continuum emission with an rms noise of $0.019\hbox{$\rm\; mJy{\rm /beam}$}$" (Data reduction)

### Inherited from earlier work

- Free-fall Hernquist potential model approach  
  > "Following (cite: Lim08), we assume a Hernquist model for the gravitational potential of the central galaxy" (Discussion) [from Lim08]
- XCO = 0.4e20 for starburst  
  > "We therefore assume $X_{\mathrm{CO}}=0.4\times10^{20}\hbox{$\hbox{$\rm\; cm^{-2}\,$}(\rm\; K\hbox{$\rm\; km\rm\; s^{-1}\,$})^{-1}$}$ ((cite: Downes98))" (3.3 Molecular gas mass) [from Downes98]
- CO(3-2)/CO(1-0) ~0.8  
  > "a line ratio CO(3-2)/CO(1-0) $\sim0.8$ ((cite: Edge01; Russell16))" (3.3 Molecular gas mass) [from Edge01; Russell16]

### Not stated but needed to reproduce (our reading)

- Line-free channels for continuum subtraction and continuum fit order
- CLEAN threshold, mask, cell and image size
- Exact regions for filaments and hybrid spatial/spectral flux separation
- Initial guesses and bounds for MPFIT component fits and how components are assigned
- Hernquist model inputs per filament (initial radius, inclination grid details)
- Luminosity distance value used in mass calculation

## Analysis recipe

1. **Calibrate and image CO(3-2) cube and continuum**: CASA pipeline calibration, CLEAN with natural weighting, UVCONTSUB, 12 km/s channels  
  > "Continuum-subtracted data cubes were generated using CLEAN and UVCONTSUB." (Data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: Different weightings compared; no major differences  
  > "Different weightings were explored to determine the optimum for imaging." (Data reduction)
2. **Fit total spectrum**: Three Gaussian components fitted to spectrum from 6x6 arcsec region  
  > "The total spectrum was fitted with three Gaussian components using the package MPFIT" (Molecular gas morphology)
   - software: MPFIT
   - fitting: MPFIT least squares, 3 Gaussians  
  > "The total spectrum was fitted with three Gaussian components using the package MPFIT" (Molecular gas morphology)
   - validation: _not stated_
3. **Map velocity and FWHM per pixel**: Beam-sized region spectra fitted with 1-3 Gaussians, 3 sigma detection from 1000 Monte Carlo simulations  
  > "We required at least $3\sigma$ significance for the detection of an emission line in each region based on 1000 Monte Carlo simulations of the spectrum." (Velocity structure)
   - software: MPFIT
   - fitting: MPFIT  
  > "The extracted spectra were fitted with MPFIT using one, two or three Gaussian components." (Velocity structure)
   - validation: _not stated_
4. **Derive molecular gas masses**: Mass from integrated CO intensity with XCO and line ratio  
  > "the total molecular gas mass can be inferred from the integrated CO intensity" (3.3 Molecular gas mass)
   - assumption: XCO=0.4e20 cm^-2 (K km/s)^-1; CO(3-2)/CO(1-0)~0.8  
  > "We therefore assume $X_{\mathrm{CO}}=0.4\times10^{20}\hbox{$\hbox{$\rm\; cm^{-2}\,$}(\rm\; K\hbox{$\rm\; km\rm\; s^{-1}\,$})^{-1}$}$ ((cite: Downes98))" (3.3 Molecular gas mass)
   - fitting: _not stated_
   - validation: Compared with SMA flux and McDonald14 mass  
  > "Note also that (cite: McDonald14) assume a line ratio CO(3-2)/CO(1-0) $\sim0.5$, which produces a similar molecular gas mass" (3.3 Molecular gas mass)
5. **Compare PV diagram with Hernquist free-fall**: Free-fall velocity in Hernquist potential with NFW-derived total mass, several inclinations, initial velocity 250 km/s  
  > "all models used $250\hbox{$\rm\; km\rm\; s^{-1}\,$}$. The initial radius was selected to match each model to the outermost region of the appropriate filament." (Discussion)
   - software: XSPEC
   - assumption: Hydrostatic spherical atmosphere; Re ~17 kpc, a=9.4 kpc  
  > "The scale radius is therefore estimated at $9.4\rm\; kpc$." (Discussion)
   - fitting: NFWMASS model fit in XSPEC to Chandra annular spectra  
  > "the NFWMASS model ((cite: Nulsen10)) in XSPEC (version 12.9.0; (cite: Arnaud96))" (Discussion)
   - validation: M500 consistent with Y_SZ and Y_X scaling  
  > "This is consistent with the mass determined from scaling relations with $Y_{\mathrm{SZ}}$ ((cite: Williamson11))" (Discussion)

## Software

- **CASA** 4.3.1: calibration and imaging  
  > "The observations were calibrated in CASA version 4.3.1" (Data reduction)
- **MPFIT** : Gaussian fitting of spectra  
  > "fitted with three Gaussian components using the package MPFIT" (Molecular gas morphology)
- **XSPEC** 12.9.0: NFWMASS fit to Chandra spectra  
  > "the NFWMASS model ((cite: Nulsen10)) in XSPEC (version 12.9.0; (cite: Arnaud96))" (Discussion)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total CO(3-2) integrated intensity | 8.9 | 1.5 | Jy km/s | 2 | For the integrated CO(3-2) intensity of $8.9\pm1.5\hbox{$\rm\; Jy\rm\; km\rm\; s^{-1}\,$}$ |
| Total molecular gas mass | 2.1e10 | 0.3e10 | Msun | 4 | the total molecular gas mass is $2.1\pm0.3\times10^{10}\hbox{$\rm\thinspace M_{\odot}$}$ |
| Central peak gas mass | 1.0e10 | 0.2e10 | Msun | 4 | has a molecular gas mass of $1.0\pm0.2\times10^{10}\hbox{$\rm\thinspace M_{\odot}$}$ |
| AGN continuum flux at 225.09 GHz | 2.5 | 0.1 | mJy | 1 | with a flux of $2.5\pm0.1\rm\; mJy$ at $225.09\rm\; GHz$ |
| Main component FWHM | 450 | 80 | km/s | 2 | / Total / 198/141 / 1 / $5.3\pm1.0$ / $11.0\pm1.0$ / $450\pm80$ / $20\pm50$ / |
| Galaxy total mass within ~50 kpc | ~2e13 | not stated | Msun | 5 | We therefore estimate a galaxy total mass of $\sim2\times10^{13}\hbox{$\rm\thinspace M_{\odot}$}$ within a radius of $\sim50\rm\; kpc$. |

## Qualitative findings

- Filaments 10-20 kpc long lie along rims of X-ray cavities with smooth velocity gradients and narrow FWHM  
  > "The smooth velocity gradients and narrow line widths along each filament reveal massive, ordered molecular gas flows around each bubble" (abstract)

## Claim tuples

- H: Molecular gas is spatially coupled to radio bubbles | E: CO(3-2) mapping compared with Chandra cavities | R: Filaments drape around cavity rims; ~half of flux is in filaments | F: Bubbles shape the cold gas | **supported**
- H: Filament kinematics are consistent with free-fall | E: PV diagrams vs Hernquist free-fall models | R: Only inclinations <15 deg match | F: Velocities inconsistent with free-fall | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Merger origin of gas rejected as requiring multiple gas-rich donors  
  > "An alternative merger origin for such a substantial mass of molecular gas would require multiple gas-rich donor galaxies" (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): XCO uncertainty raises mass uncertainty to a factor of a few  
  > "The uncertainty on the $X_{\mathrm{CO}}$ factor increases the uncertainty on the molecular gas masses to roughly a factor of a few." (3.3 Molecular gas mass)
- Caveat (inferred, ours): Inflow vs outflow not distinguished
- Caveat (inferred, ours): Filament flux fractions rely on subjective hybrid separation
- Caveat (inferred, ours): Free-fall test depends on assumed mass and degenerate inclination

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters beyond weighting
- Missing: Region definitions
- Missing: Hernquist model script
- Data volume (inferred): ~10-30 GB raw single-pointing dataset
- Score (inferred): 3/5, Public data and clear outline but many parameters missing.
- Rediscovery candidate: yes, Public archival dataset, numeric results (flux, mass), moderately complete recipe.

## Links

- Method: Lim08 (Hernquist free-fall model)
- Method: Nulsen10 (NFWMASS model)
- Companion: McDonald14 (earlier SMA and IFU data of same target)
- Companion: McDonald15 (Chandra analysis of cavities)
- Related: SPT

## Checks

```json
{
 "quotes": 61,
 "quotes_ok": 61,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 47,
  "rate": 0.635
 },
 "evidence_ok": true
}
```

# Close entrainment of massive molecular gas flows by radio bubbles in the central galaxy of Abell 1795

`2017MNRAS.472.4024R` | Monthly Notices of the Royal Astronomical Society 2017 | first author: Russell, H. R. | arXiv: 1708.08935 | DOI: 10.1093/mnras/stx2255

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: galaxy_clusters_and_sz, agn_and_quasars, nearby_galaxies
- Question: How does the molecular gas in the Abell 1795 central galaxy relate morphologically and kinematically to the radio bubbles, and can the gas be entrained by them?  
  > "By resolving the spatial and velocity structure of the molecular filaments, we investigate the interactions between the cold gas and the expanding radio bubbles." (Introduction)
- Target **Abell 1795 central galaxy (4C 26.42)**: coordinates RA 13:48:52.495, Dec +26:35:34.32 (continuum point source)  
  > "Stellar absorption measurements for the central galaxy give a redshift $z=0.06326$" (Data reduction); "located at RA 13:48:52.495 and Dec +26:35:34.32" (Nuclear continuum); z/distance z=0.06326; 1 arcsec = 1.22 kpc  
  > "Stellar absorption measurements for the central galaxy give a redshift $z=0.06326$" (Data reduction); "located at RA 13:48:52.495 and Dec +26:35:34.32" (Nuclear continuum); distance from stellar absorption redshift; LCDM H0=70, OmegaM=0.27, OmegaL=0.73  
  > "Stellar absorption measurements for the central galaxy give a redshift $z=0.06326$" (Data reduction); "located at RA 13:48:52.495 and Dec +26:35:34.32" (Nuclear continuum)

## Data provenance

- ALMA projects: 2015.1.00623.S
- bands: Band 6  
  > "observed with the ALMA $12\rm\; m$ array using the Band 6 receiver" (Data reduction)
- frequencies and spectral setup: One window on CO(2-1) at 216.822 GHz; continuum windows at 218.791, 232.491, 234.491 GHz; 1.875 GHz bandwidth, 977 kHz resolution, binned to 10 km/s  
  > "One spectral window covered the CO(2-1) emission line at $216.822\rm\; GHz$ and three additional windows were used to image the sub-mm continuum emission" (Data reduction); "The velocity channels were later binned to a resolution of $10\hbox{$\rm\; km\rm\; s^{-1}\,$}$ for the analysis." (Data reduction)
- continuum bandwidth: _not stated_
- arrays: 12 m array, 38 antennas  
  > "thirty-eight $12\rm\; m$ antennas were available for each observation" (Data reduction)
- configurations: _not stated_
- baselines: 15-704 m  
  > "The baselines ranged from $15-704\rm\; m$" (Data reduction)
- angular resolution: 0.8 x 0.6 arcsec, PA -15.3 deg (cube, natural weighting)  
  > "The final cube had a synthesized beam of $0.8\rm\; arcsec\times0.6\rm\; arcsec$ with a position angle P.A.$=-15.3\deg$ for natural weighting." (Data reduction)
- max recoverable scale: _not stated_
- sensitivity: 0.64 mJy/beam in 10 km/s channels; continuum rms 0.026 mJy/beam  
  > "The rms noise in $10\hbox{$\rm\; km\rm\; s^{-1}\,$}$ channels was $0.64\hbox{$\rm\; mJy{\rm\thinspace beam^{-1}}$}$." (Data reduction)
- time on source: 72 min  
  > "a total time on source of $72\min$ divided equally between 11 and 14 June 2016" (Data reduction)
- observing dates: 11 and 14 June 2016  
  > "a total time on source of $72\min$ divided equally between 11 and 14 June 2016" (Data reduction)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (216.822 GHz (observed-frame window as stated))
- Other facility **Chandra**: X-ray image of hot atmosphere and cavities  
  > "the *Chandra* X-ray image of the hot atmosphere, which shows bright cool gas blobs and depressions coincident with the radio lobes" (Results)
- Other facility **HST**: FUV and broad-band dust images  
  > "overlaid on the HST FUV image of the recent star formation" (Results)
- Other facility **MMTF**: Halpha imaging  
  > "The seeing for the MMTF H$\alpha$ observation was $0.7\rm\; arcsec$" (Dust and optical line emission)
- Other facility **VLA**: 5 GHz radio lobe map  
  > "radio lobes detected at $5\rm\; GHz$ with the VLA" (Results)
- External data: Single-dish IRAM 30m CO flux and CO(2-1)/CO(1-0)=0.8 line ratio  
  > "brightness line ratio of CO(2-1)/CO(1-0)$=0.8$ measured for Abell 1795 in single dish observations" (Molecular gas mass) [from (cite: Salome03)]
- External data: VLA 22 GHz nuclear flux 4.6±0.3 mJy  
  > "nuclear flux measurement at $22\rm\; GHz$ of $4.6\pm0.3\rm\; mJy$" (Nuclear continuum) [from (cite: Liuzzo09)]
- External data: Gravitational potential (NFW) and cooling/free-fall time ratios  
  > "Based on the gravitational potential for the central galaxy in Abell 1795 determined by (cite: Hogan17)" (Discussion) [from (cite: Hogan17)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline reduction scripts  
  > "calibrated in CASA version 4.5.3 ((cite: McMullin07)) with the ALMA pipeline reduction scripts" (Data reduction)
- casa version: CASA 4.5.3  
  > "calibrated in CASA version 4.5.3" (Data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (bandpass: J1229+0203; phase: J1333+2725)  
  > "J1229+0203 and Titan were observed for bandpass and flux calibration." (Data reduction)
- flux scale uncertainty: _not stated_
- self calibration: Not applied; no significant noise reduction  
  > "Self-calibration was not found to produce a significant reduction in the image rms noise." (Data reduction)

### Imaging

- task: CLEAN on continuum-subtracted visibilities  
  > "The calibrated continuum-subtracted visibilities were then imaged and deconvolved with the CLEAN algorithm." (Data reduction)
- deconvolver: _not stated_
- weighting robust: Natural for cube; Briggs robust=0.5 for continuum  
  > "The continuum image was generated using Briggs weighting with robust$=0.5$." (Data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: UVCONTSUB using line-free channels  
  > "The continuum emission was determined from line-free channels and subtracted from visibilities using the task UVCONTSUB." (Data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: Continuum 0.6 x 0.5 arcsec, PA -8.0 deg  
  > "The synthesized beam in this image was $0.6\rm\; arcsec\times0.5\rm\; arcsec$ with P.A.$=-8.0\deg$." (Data reduction)
- final rms: 0.64 mJy/beam (10 km/s); continuum 0.026 mJy/beam  
  > "An image of the continuum emission with rms of $0.026\hbox{$\rm\; mJy{\rm\thinspace beam^{-1}}$}$ was produced" (Data reduction)

### Inherited from earlier work

- Redshift/systemic velocity from stellar absorption measurements  
  > "Stellar absorption measurements for the central galaxy give a redshift $z=0.06326$" (Data reduction) [from (cite: Hill88; Hu85; Hill93; Anton93)]
- Galactic XCO and CO-to-H2 mass formula assumption  
  > "We therefore assume a Milky Way factor of $X_{\mathrm{CO}}=2\times10^{20}" (Molecular gas mass) [from (cite: Solomon87; Solomon05)]

### Not stated but needed to reproduce (our reading)

- CLEAN threshold, mask, niter, cell and image size
- Line-free channel ranges for UVCONTSUB
- Primary-beam correction method and instrumental-broadening correction details
- Spectral-fit initial guesses and the Monte Carlo procedure for the 3-sigma detection
- Exact regions for N/S filament and centre spectra and PV apertures
- Luminosity distance used in the mass formula
- Whether the cube was binned before or after imaging

## Analysis recipe

1. **Calibrate and image CO(2-1) cube and continuum**: ALMA pipeline calibration, UVCONTSUB, CLEAN with natural weighting; continuum from line-free channels  
  > "The calibrated continuum-subtracted visibilities were then imaged and deconvolved with the CLEAN algorithm." (Data reduction)
   - software: CASA
   - parameter: 10 km/s channels; natural weighting; continuum Briggs robust=0.5  
  > "natural weighting was selected to give the highest signal-to-noise in the extended filaments" (Data reduction)
   - fitting: _not stated_
   - validation: Different weightings compared; self-calibration tested  
  > "Different weightings were investigated to determine the optimum for imaging" (Data reduction)
2. **Fit integrated spectra of regions**: Two-Gaussian fit to total spectrum and regional spectra  
  > "The total spectrum was fitted with two Gaussian components using the spectral fitting package MPFIT" (Molecular gas morphology: entrainment)
   - software: MPFIT
   - parameter: Total region 4x14 arcsec  
  > "extracted from a $4\rm\; arcsec\times14\rm\; arcsec$ region" (Molecular gas morphology: entrainment)
   - fitting: MPFIT least-squares, chi2/dof reported  
  > "The total spectrum was fitted with two Gaussian components using the spectral fitting package MPFIT" (Results, Molecular gas morphology: entrainment)
   - validation: _not stated_
3. **Map multiple velocity components**: Fit 1-3 Gaussians per beam-sized spectrum at each pixel; 3 sigma detection from 5000 Monte Carlo simulations  
  > "At least $3\sigma$ significance, based on 5000 Monte Carlo simulations of the spectrum, was required for the detection of a velocity component in each region." (Multiple velocity components)
   - software: MPFIT
   - fitting: MPFIT Gaussians  
  > "Each extracted spectrum was fitted with one, two or three Gaussian components using the spectral fitting code MPFIT." (Multiple velocity components)
   - validation: Monte Carlo significance  
  > "At least $3\sigma$ significance, based on 5000 Monte Carlo simulations of the spectrum, was required for the detection of a velocity component in each region." (Multiple velocity components)
4. **Measure velocity gradient along N filament**: PV diagram; 2D Gaussian fits to channel maps projected along filament; linear fit v=ax+b  
  > "We fit the resulting velocity profile with a linear model $v=ax+b$" (Position-velocity diagrams)
   - parameter: Channels -100 to -250 km/s; collision regions excluded  
  > "A two-dimensional Gaussian provides a reasonable fit to the velocity channels from $-100$ to $-250\hbox{$\rm\; km\rm\; s^{-1}\,$}$" (Position-velocity diagrams)
   - assumption: Gradient not corrected for inclination  
  > "Whilst the measured gradient does not account for the inclination of the gas flow" (Position-velocity diagrams)
   - fitting: Linear fit  
  > "We fit the resulting velocity profile with a linear model $v=ax+b$, where $v$ is the velocity ($\hbox{$\rm\; km\rm\; s^{-1}\,$}$) and $x$ is the distance along the filament (kpc)." (Position-velocity diagrams)
   - validation: _not stated_
5. **Nuclear continuum and spectral index**: Point-source flux at 225.76 GHz combined with 22 GHz flux  
  > "we determine a flat spectral index for the core of $\alpha=-0.16\pm0.06$" (Nuclear continuum)
   - fitting: _not stated_
   - validation: _not stated_
6. **Derive molecular gas mass**: M_mol from CO(2-1) intensity via CO(2-1)/CO(1-0)=0.8 and Galactic XCO  
  > "From the total integrated CO(2-1) intensity of $13.1\pm0.6\hbox{$\rm\; Jy\rm\; km\rm\; s^{-1}\,$}$, the molecular gas mass is $3.3\pm0.2\times10^9\hbox{$\rm\thinspace M_{\odot}$}$." (Molecular gas mass)
   - assumption: XCO=2e20 cm^-2 (K km/s)^-1, factor of a few uncertainty  
  > "We therefore assume a Milky Way factor of $X_{\mathrm{CO}}=2\times10^{20}" (Molecular gas mass)
   - fitting: _not stated_
   - validation: _not stated_
7. **Energy budget of uplift**: Compare 4PV cavity energy with potential plus kinetic energy of lifted gas  
  > "Therefore, the total energy in the outflow is $E_{\mathrm{out}}\sim7\times10^{57}\rm\; erg$" (Direct uplift of molecular gas clouds)
   - assumption: Prolate spheroid cavity; Hogan17 potential  
  > "Assuming a prolate spheroid, the semi-major and minor axes of the X-ray cavity" (Direct uplift of molecular gas clouds)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.5.3: calibration, UVCONTSUB, CLEAN imaging  
  > "calibrated in CASA version 4.5.3" (Data reduction)
- **MPFIT** : Gaussian fitting of spectra  
  > "fitted with one, two or three Gaussian components using the spectral fitting code MPFIT" (Multiple velocity components)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total CO(2-1) integrated intensity | 13.1 | 0.6 | Jy km/s | 2 | The total integrated intensity is $13.1\pm0.6\hbox{$\rm\; Jy\rm\; km\rm\; s^{-1}\,$}$ |
| Total molecular gas mass (Galactic XCO) | 3.3e9 (text); 3.2e9 (abstract) | 0.2e9 | Msun | 6 | the total molecular gas mass is $3.2\pm0.2\times10^{9}\hbox{$\rm\thinspace M_{\odot}$}$ |
| N filament velocity gradient a | -35.5 | 0.9 | km/s/kpc | 4 | $a=-35.5\pm0.9\hbox{$\hbox{$\rm\; km\rm\; s^{-1}\,$}\rm\; kpc^{-1}\,$}$ |
| Nuclear continuum flux at 225.76 GHz | 3.2 | 0.2 | mJy | 5 | nuclear point source of $3.2\pm0.2\rm\; mJy$ at $225.76\rm\; GHz$ |
| Core spectral index | -0.16 | 0.06 | dimensionless | 5 | $\alpha=-0.16\pm0.06$ |
| Total outflow energy | ~7e57 | not stated | erg | 7 | $E_{\mathrm{out}}\sim7\times10^{57}\rm\; erg$ |

## Qualitative findings

- Molecular filaments lie exclusively around outer edges of radio lobes with smooth velocity gradients and narrow dispersions, indicating entrainment.  
  > "The close spatial association with the radio lobes, ordered velocity gradients and narrow velocity dispersions show that the filaments are gas flows entrained by the expanding radio bubbles." (Discussion)

## Claim tuples

- H: Are the molecular filaments gas flows entrained by the radio bubbles? | E: Mapped CO(2-1) morphology and velocity versus radio lobes | R: Filaments wrap lobe edges with smooth gradients to -370 km/s and narrow dispersions | F: Filaments are entrained by expanding radio bubbles | **supported**
- H: Can the N bubble directly lift the molecular gas? | E: Energy budget comparing cavity 4PV with gas energy | R: E_out ~7e57 erg exceeds E_cav ~3e57 erg | F: Direct uplift needs infeasibly efficient coupling | **supported**
- H: Does stimulated feedback explain the gas? | E: Compare hot gas cooling and uplifted mass with molecular mass | R: Plausible but requires multiple bubble generations | F: Stimulated cooling of lifted low entropy gas is a plausible model | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Natural weighting chosen for highest S/N in extended filaments  
  > "natural weighting was selected to give the highest signal-to-noise in the extended filaments" (Data reduction)
- Alternative: Ram pressure stripping disfavoured by narrow filament width and association with lobes  
  > "disfavors ram pressure stripping of this cold gas from the galaxy" (Velocity structure: gas flows)
- How they decided it was enough: _not stated_
- Limitation (authors): Some extended emission resolved out (~70% of single-dish flux recovered)  
  > "Given the extent of the ionized gas nebula, it is likely that some extended structure has been resolved out." (Molecular gas morphology: entrainment)
- Limitation (authors): XCO uncertain by a factor of a few; line-of-sight location of filaments ambiguous  
  > "and estimate a factor of a few uncertainty" (Molecular gas mass)
- Caveat (inferred, ours): Mass depends on assumed Galactic XCO and a single-dish line ratio
- Caveat (inferred, ours): Inclination unknown so velocities and energies are projected
- Caveat (inferred, ours): Energy estimates rely on cavity geometry with unknown line-of-sight extent

## Reproducibility

- Data public (paper): ALMA project code acknowledged; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA 2015.1.00623.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CLEAN parameters
- Missing: Line-free channel ranges
- Missing: Region definitions
- Missing: Auxiliary Chandra/HST/VLA data processing
- Data volume (inferred): ~20-50 GB raw for two 12m execution blocks
- Score (inferred): 3/5, Data and main steps are described, but imaging parameters and regions are missing; key masses are numeric.
- Rediscovery candidate: yes, Single project code, simple pipeline-calibrated imaging, and numeric results (flux, mass, velocity gradient).

## Links

- Companion: (cite: Russell16; Russell17) (Similar ALMA studies of molecular filaments around radio bubbles)
- Companion: (cite: Salome04) (Earlier IRAM interferometric CO observations)

## Checks

```json
{
 "quotes": 72,
 "quotes_ok": 72,
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
  "facts": 85,
  "stated": 56,
  "rate": 0.659
 },
 "evidence_ok": true
}
```

# The Dust and Molecular Gas in the Brightest Cluster Galaxy in MACS 1931.8-2635

`2019ApJ...879..103F` | The Astrophysical Journal 2019 | first author: Fogarty, Kevin | arXiv: 1905.01377 | DOI: 10.3847/1538-4357/ab22a4

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: galaxy_clusters_and_sz, nearby_galaxies
- Question: What are the amount, distribution, kinematics and excitation of the molecular gas and dust in the BCG of the cool-core cluster MACS 1931, and how do they relate to the AGN, star formation and the ICM?  
  > "characterize the spatial distribution, energetics, and kinematics of the dust and molecular gas, and their relationship to the ICM, during episodes of intense starburst activity and AGN feedback." (1 Introduction)
- Target **MACS 1931.8-2635 BCG**: coordinates _not stated_; z/distance z = 0.3525  
  > "1$''$ subtends 4.962 kpc at the spectroscopic redshift of the BCG in MACS 1931, $z = 0.3525$." (1 Introduction); distance from VLT/MUSE spectrum, 10 optical emission lines (z = 0.35248 ± 0.00004)  
  > "1$''$ subtends 4.962 kpc at the spectroscopic redshift of the BCG in MACS 1931, $z = 0.3525$." (1 Introduction)

## Data provenance

- ALMA projects: 2016.1.00784.S, 2017.1.01205.S
- bands: Bands 3, 6, 7 (12 m and ACA for 6 and 7)  
  > "Our ALMA Bands 6 and 7 observations, including Atacama Compact Array (ACA) observations, were obtained in cycle 5" (2.1 ALMA Observations)
- frequencies and spectral setup: Band 3 SPWs at 85.3, 87.0, 97.0, 99.0 GHz; Band 6 at 239.5, 241.5, 255.5, 257.5 GHz; Band 7 at 339.5, 341.4, 351.5, 353.5 GHz  
  > "We configured our Band 3 spectral windows (SPWs) to center on sky frequencies of 85.3 GHz, 87.0 GHz, 97.0 GHz, and 99.0 GHz." (2.1 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: Band 3 15-3700 m; Band 6 15-500 m; Band 7 15-314 m  
  > "which yielded a 15-3700 m baseline range and a 13366 s total integration time" (2.1 ALMA Observations)
- angular resolution: _not stated_
- max recoverable scale: 18.8'' (Band 3), 20.4'' (Band 6), 14.6'' (Band 7)  
  > "Combining these observations yielded a $0.81\ensuremath{''}$ minimum possible synthesized beam and a $14.6\ensuremath{''}$ largest recoverable angular scale." (2.1 ALMA Observations)
- sensitivity: _not stated_
- time on source: Band 3 13366 s; Band 6 726 s (12 m) + 1724 s (ACA); Band 7 2722 s (12 m) + 6804 s (ACA)  
  > "The on-source time for the 12 m array and ACA observations were 2722 s and 6804 s, respectively." (2.1 ALMA Observations)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO 1-0 (not stated)
- Line: CO 3-2 (not stated)
- Line: CO 4-3 (partial coverage) (not stated)
- Other facility **HST (CLASH)**: 16-band photometry, UV knots and Halpha+[NII] maps  
  > "We use the 16 bands of *HST* photometry for the MACS J1931.8-2635 BCG" (2.2 HST Data)
- Other facility **VLT/MUSE**: optical redshift of BCG  
  > "derived by us from 10 optical emission lines found in a VLT/MUSE spectrum" (Footnote 1)
- Other facility **Gaia DR2**: HST astrometric cross-match  
  > "we cross-matched our *HST* astrometry to entries from the Gaia DR2 catalog" (3.2 Astrometric Alignment Accuracy)
- External data: ICM temperature 4.78±0.64 keV, cooling rate, entropy and X-ray cavities  
  > "substantially colder than the $4.78\pm0.64$ keV temperature of the ICM plasma around the multiphase tail" (5.2) [from (cite: 2011Ehlert_MACS1931)]
- External data: SFR, burst duration and dust mass of the BCG  
  > "the SFR = $240^{+197}_{-70}$ M$_{\odot}$ yr$^{-1}$ and we constrained the duration of the starburst to be $74^{+145}_{-30}$ Myr" (5) [from (cite: 2017Fogarty_CLASH)]
- External data: CO SLED comparison samples (SMG, ULIRG averages)  
  > "The SMG (blue points) and local ULIRG averages (grey points) are derived from the samples studied in (cite: 2015Daddi_CO)" (5.1) [from (cite: 2015Daddi_CO)]
- Simulation/model as data: Simulated BCG velocity dispersion distributions smoothed to ALMA-like resolution  
  > "alongside predictions for simulated BCGs with conditions similar to MACS 1931 when the simulated data is smoothed" (4.1 CO Line Emission)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline-calibrated measurement sets regenerated  
  > "After regenerating the pipeline-calibrated measurement sets, we used the task `concat`" (3.1)
- casa version: CASA 4.7.2 (cycle 4); CASA 5.1.1-5 (cycle 5)  
  > "Cycle 4 observations were reduced using the CASA software package version 4.7.2 (pipeline r39732)" (3.1)
- pipeline version: r39732 (cycle 4); r40896 (cycle 5)  
  > "cycle 5 observations were reduced using CASA version 5.1.1-5 (pipeline version r40896)" (3.1)
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10% absolute calibration accuracy term  
  > "Uncertainties in integrated fluxes include a 10% absolute calibration accuracy term." (Table 2)
- self calibration: _not stated_

### Imaging

- task: clean (MFS for continuum; velocity mode for lines)  
  > "using the multi-frequency synthesis (MFS) mode of the `clean` task" (3.1)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The visibilities were naturally weighted, and the image pixel size was $0.075\ensuremath{''}$." (3.1)
- uv taper: 1.5'' uv-taper for CO(1-0) and CO(3-2)  
  > "We also re-ran imaging for CO(1-0) and CO(3-2) using a $1.5\ensuremath{''}$ *uv*-taper" (4.1)
- cell size: 0.075''  
  > "using natural weighting, a $0.075\ensuremath{''}$ pixel size, and a velocity channel width of 25 km s$^{-1}$" (3.1)
- image size: _not stated_
- masking: interactive clean masks  
  > "We produced clean masks using `clean` in interactive mode to identify regions with significant source emission." (3.1)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub on line-free channels  
  > "used the task `uvcontsub` to generate the continuum data from the line-free spectral channels" (3.1)
- line free channels: _not stated_
- primary beam correction: applied to all images  
  > "All images or image cubes used in our scientific analysis have been primary beam corrected." (3.1)
- array combination: _not stated_
- smoothing: imsmooth with targetres=True to common beam  
  > "smoothed using `imsmooth` with `targetres` = True" (3.1)
- final beam: 0.82''x0.53'' (B3), 0.87''x0.72'' (B6), 0.94''x0.78'' (B7)  
  > "The achieved synthesized beams for Band 3, Band 6, and Band 7 are 0.82$''$$\times$0.53$''$, 0.87$''$$\times$0.72$''$, and 0.94$''$$\times$0.78$''$." (3.1)
- final rms: Band 6 rms 0.020 mJy/beam; Band 3 3-sigma limit 0.023 mJy/beam  
  > "which is well below the RMS noise of 0.020 mJy/beam" (4.2)

### Inherited from earlier work

- X_CO = 0.4e20 adopted for consistency with Phoenix cluster  
  > "We adopted the value $X_{CO} = 0.4\times 10^{20} \frac{\textrm{cm}^{-2}}{\textrm{K km s}^{-1}}$ for starbursts and ULIRGs used in (cite: 2016Russell_Phoenix)" (4.1) [from (cite: 2016Russell_Phoenix)]
- Greybody model with beta range 1.6±0.38  
  > "(cite: 2012Casey_Dust) measured $\beta = 1.6\pm0.38$ for a sample of ULIRGs" (4.2) [from (cite: 2012Casey_Dust)]
- HST reduced dataset  
  > "the reduced dataset is described in (cite: 2015Fogarty_CLASH; 2017Fogarty_CLASH)" (2.2 HST Data) [from (cite: 2015Fogarty_CLASH; 2017Fogarty_CLASH)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for uvcontsub
- Clean threshold and iteration counts, mask definitions
- Taper parameters beyond 1.5'' and common-beam sizes
- Phase center/coordinates and flux/bandpass calibrators
- Lorentzian fitting method and priors, and how spectra regions are defined
- Region definitions for dust flux ratios and temperature-limit derivation method
- Rest frequencies used and velocity reference
- Simulated BCG data source for velocity dispersion comparison

## Analysis recipe

1. **Calibrate and prepare data**: Regenerate pipeline calibration, concat per band, uvcontsub  
  > "we used the task `concat` to concatenate the calibrated measurement sets at each band" (3.1)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Image continuum and cubes; remove AGN point source**: clean MFS continuum; fitcomponents Gaussian point-source fit and subtraction; line cubes at 25 km/s  
  > "we subtracted the point source in each band using the image arithmetic task `fitcomponents` to fit a Gaussian model to the point source" (3.1)
   - software: CASA
   - fitting: _not stated_
   - validation: Band 6 and 7 point source fluxes agree (4.19 vs 4.28 mJy)  
  > "The point source flux at Band 6 is $4.19\pm0.42$ mJy, roughly equal to the $4.28\pm 0.43$ mJy measured in Band 7" (3.1)
3. **Fit CO line spectra and compute gas mass**: Lorentzian profile fits to integrated spectra and knots; M_mol from CO(1-0) flux  
  > "Spatially integrated flux from the emission lines were fit to Lorentzian profiles" (4.1)
   - assumption: X_CO = 0.4e20 cm^-2/(K km/s)  
  > "We adopted the value $X_{CO} = 0.4\times 10^{20} \frac{\textrm{cm}^{-2}}{\textrm{K km s}^{-1}}$" (4.1)
   - fitting: _not stated_
   - validation: Tapered fluxes consistent with untapered  
  > "Total fluxes in the *uv*-tapered images are consistent with the un-tapered images." (4.1)
4. **CO line ratios and SLED**: R_ij brightness-temperature ratios, global and pixel map of R31 where S/N>=3  
  > "we map $R_{31}$ in all pixels where the value of $R_{31}/\sigma_{R_{31}} \geq 3$" (5.1)
   - fitting: _not stated_
   - validation: _not stated_
5. **Constrain dust temperature**: Band7/Band6 flux ratio vs greybody with CMB correction, as function of T_d and beta  
  > "The contour plot in Figure [7](#fig:TBeta_Analysis) shows the predicted values of the flux ratio as a function of $T_d$ and $\beta$." (4.2)
   - parameter: lambda_0 = 200 um; rest wavelengths 640 and 892 um  
  > "$\lambda_{0} \equiv 200$ $\mu$m" (4.2)
   - assumption: beta 1.22-1.98 (1.6±0.38); T_CMB = 3.69 K; power-law term neglected  
  > "where $T_{CMB} = 2.73\left(1+z\right) = 3.69$ K" (4.2)
   - fitting: _not stated_
   - validation: Checked free-free/synchrotron contamination using Band 3 and SFR relation  
  > "implying that any contamination by extended free-free or synchrotron emission in our dust images is below the RMS noise in Bands 6 and 7." (4.2)

## Software

- **CASA** 4.7.2 and 5.1.1-5: calibration, concat, uvcontsub, clean, imsmooth, fitcomponents  
  > "Cycle 4 observations were reduced using the CASA software package version 4.7.2 (pipeline r39732)" (3.1)
- **APLpy** : plotting  
  > "This research made use of APLpy, an open-source plotting package for Python" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Molecular gas mass | 1.9e10 | ±0.3e10 | Msun | 3 | $1.9 \pm 0.3 \times 10^{10}$ M$_{\odot}$ of molecular gas |
| CO(1-0) flux | 3.45 | 0.47 | Jy km/s | 3 | the CO(1-0) line has an integrated flux of $3.45 \pm 0.47$ Jy km s$^{-1}$ |
| CO(3-2) flux | 29.0 | 2.8 | Jy km/s | 3 | the CO(3-2) line has a flux of $29.0 \pm 2.8$ Jy km s$^{-1}$ |
| CO(4-3) flux | 33.7 | 3.5 | Jy km/s | 3 | the CO(4-3) line has a flux of $33.7 \pm 3.5$ Jy km s$^{-1}$ |
| R31 | 0.93 | 0.16 | dimensionless | 4 | $R_{31} = 0.93\pm0.16$ and $R_{41} = 0.61\pm0.10$ |
| R41 | 0.61 | 0.10 | dimensionless | 4 | $R_{31} = 0.93\pm0.16$ and $R_{41} = 0.61\pm0.10$ |
| Band 7/Band 6 flux ratio, Regions 1-3 | 1.25, 3.29, 1.29 | 0.53, 0.99, 0.33 | dimensionless | 5 | The Band 7 to Band 6 flux ratios for these regions are $1.25\pm0.53$, $3.29\pm0.99$, and $1.29\pm0.33$, respectively. |
| Tail dust temperature (beta=1.6±0.38) | 5.0 < T_d < 21.9 | not stated | K | 5 | we find that $5.0 < T_d < 21.9$ K for $\beta = 1.6\pm0.38$ |
| Molecular gas depletion time | ~80 | not stated | Myr | 3 | imply the molecular gas has a depletion time of $\sim 80$ Myr |

## Qualitative findings

- CO is in diffuse and compact components extending ~30 kpc NW, tracing UV knots and Halpha filaments; tail offset ~300 km/s.  
  > "extend from the BCG center out to $\sim30$ kpc to the northwest, tracing the UV knots and H$\alpha$ filaments observed by *HST*." (abstract)

## Claim tuples

- H: Does the BCG host a very large molecular gas reservoir? | E: CO(1-0) flux converted with X_CO=0.4e20 | R: 1.9±0.3e10 Msun | F: Among the largest cool-core BCG reservoirs, comparable to Phoenix | **supported**
- H: Is the molecular tail jet-driven? | E: Compare morphology with X-ray cavities | R: Tail orthogonal to east-west cavities | F: Tail likely infalling, aftermath of outburst, not concurrent uplift | **partially**
- H: What excites the CO? | E: R31, R41 and SLED comparison | R: R31~0.93, R41~0.61 | F: Combination of star formation and AGN-related processes | **partially**
- H: Is there very cold dust in the tail? | E: Band7/Band6 ratio with CMB-corrected greybody | R: T_d <~ 10 K in some regions | F: Dust too cold to interact directly with ~4.8 keV ICM | **supported**

## Reasoning

- Why this data: CLASH data identified MACS 1931 as a candidate with elevated feedback and star formation  
  > "We have used these data to identify the cluster MACS 1931.8-2635 as an interesting candidate" (1 Introduction)
- Why this method: _not stated_
- Alternative: Free-free/synchrotron origin of Band 6/7 extended emission rejected via Band 3 limits  
  > "We checked to ensure that the emission features we observe are not due to free-free emission or a faint, extended synchrotron source." (4.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Dust temperature only reliable for very cold dust (<~30 K) from two ALMA bands  
  > "we can only reliably derive the temperature of very cold $T_{d} \lesssim 30$ K dust from the ALMA data alone" (4.2)
- Caveat (inferred, ours): Dust temperature from a single flux ratio is degenerate with beta
- Caveat (inferred, ours): Gas mass depends strongly on X_CO (factor ~5)
- Caveat (inferred, ours): Low-S/N CO(4-3) with partial coverage
- Caveat (inferred, ours): Lorentzian rather than Gaussian fits unjustified

## Reproducibility

- Data public (paper): Project IDs given in acknowledgements  
  > "This paper makes use of the following ALMA datasets: ADS/JAO.ALMA#2016.1.00784.S and ADS/JAO.ALMA#2017.1.01205.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Line-free channel ranges
- Missing: Clean thresholds and masks
- Missing: Region apertures and fit procedures
- Missing: Simulated BCG dataset
- Data volume (inferred): ~100-300 GB raw across three bands including ACA
- Score (inferred): 3/5, Archive data and standard CASA steps, but many imaging and fitting details are unstated.
- Rediscovery candidate: yes, Data are public, the recipe is mostly standard, and results are numeric (line fluxes, gas mass, flux ratios).

## Links

- Method: (cite: 2012Casey_Dust) (Greybody dust model)
- Method: (cite: 2013Bolatto_XCO) (CO-to-H2 mass relation)
- Companion: (cite: 2017Fogarty_CLASH) (HST-based SFR, dust mass and burst duration)
- Companion: (cite: 2015Fogarty_CLASH) (HST reduced dataset and Halpha map)
- Related: CLASH

## Checks

```json
{
 "quotes": 69,
 "quotes_ok": 69,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 50,
  "rate": 0.658
 },
 "evidence_ok": true
}
```

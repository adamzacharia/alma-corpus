# "Beads-on-a-string" Star Formation Tied to One of the Most Powerful Active Galactic Nucleus Outbursts Observed in a Cool-core Galaxy Cluster

`2024ApJ...963....1O` | The Astrophysical Journal 2024 | first author: Omoruyi, Osase | arXiv: 2312.06762 | DOI: 10.3847/1538-4357/ad1101

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: galaxy_clusters_and_sz, star_formation, agn_and_quasars
- Question: How do the cooling ICM, an AGN outburst, the warm ionized gas, cold molecular gas and the 'beads on a string' star formation relate in the merging cool-core cluster SDSS 1531?  
  > "the galaxy cluster SDSS J1531+3414 ($z=0.335$) offers an excellent laboratory to study the interplay between mergers, AGN feedback, and star formation." (Introduction)
- Target **SDSS J1531+3414 (SDSS 1531) cluster BCGs**: coordinates _not stated_; z/distance z = 0.335; D_A = 984.4 Mpc; D_L = 1756.1 Mpc  
  > "In this cosmology, 1$''$ corresponds to 4.773 kpc at the redshift of the southern BCG ($z = 0.335$), where the associated angular size and luminosity distances are 984.4 and 1756.1 Mpc" (Introduction); distance from redshift of the southern BCG (SDSS spectroscopy, Tremblay et al. 2014); H0=70, Om=0.27, OL=0.73  
  > "In this cosmology, 1$''$ corresponds to 4.773 kpc at the redshift of the southern BCG ($z = 0.335$), where the associated angular size and luminosity distances are 984.4 and 1756.1 Mpc" (Introduction)

## Data provenance

- ALMA projects: 2015.1.01426.S
- bands: Band 6  
  > "ALMA observed the center of SDSS 1531 in Band 6 as part of ALMA Cycle 3" (2.4 ALMA)
- frequencies and spectral setup: One SPW at 259.02322 GHz for 12CO(3-2); three 1875 MHz SPWs at rest 347.1, 327.075, 324.405 GHz for continuum  
  > "Three 1875 MHz spectral windows, centered at rest frequencies of 347.1, 327.075, and 324.405 GHz, were also used to detect line-free continuum." (2.4 ALMA)
- continuum bandwidth: _not stated_
- arrays: Compact and Extended configurations  
  > "Compact, Extended" (Table 1)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.53'' x 0.33'' (2.51 x 1.59 kpc), PA = -1.15 deg  
  > "a $0.53\ensuremath{''} \times 0.33\ensuremath{''}$ (2.51 kpc $\times$ 1.59 kpc) synthesized beam at position angle = $-1.15^{\circ}$" (2.4 ALMA)
- max recoverable scale: ~17'' (~80 kpc)  
  > "this array configuration is only sensitive to emission on scales up to $\sim 17$$''$ ($\sim 80$ kpc)" (2.4 ALMA)
- sensitivity: 0.22 mJy/beam per 20 km/s channel  
  > "rms sensitivity and angular resolution of 0.22 mJy beam$^{-1}$ per 20 km s$^{-1}$ channel" (2.4 ALMA)
- time on source: 105 minutes  
  > "The total integration time on source was 105 minutes." (2.4 ALMA)
- observing dates: 22-27 April 2016 and 8-13 September 2016 (two scheduling blocks)  
  > "across two scheduling blocks between 22-27 April 2016 and 8-13 September 2016" (2.4 ALMA)
- pi or archival as stated: PI G. Tremblay, Cycle 3 program  
  > "ALMA Program ID: 2015.1.01426.S; PI: G. Tremblay" (2.4 ALMA)
- Line: 12CO J=3-2 (345.8 GHz)
- Other facility **Chandra ACIS-S**: X-ray imaging/spectra of ICM (122.2 ks, 65 ks after cleaning)  
  > "for a total of 122.2 ks (62.73 and 59.46 ks, respectively)" (2.1 Chandra X-ray Observations)
- Other facility **LOFAR LoTSS-DR2**: 144 MHz diffuse radio emission  
  > "The second LoTSS data release (LoTSS-DR2) provided a public high-resolution 6$''$ mosaic of the pointing P233+35" (2.2 Radio Surveys)
- Other facility **VLA/EVLA**: 1.4-1.5 GHz images (B, C, D arrays)  
  > "The VLA has observed SDSS 1531 over multiple epochs." (2.2 Radio Surveys)
- Other facility **Gemini North GMOS-N IFU**: warm ionized gas emission-line maps  
  > "the GMOS-N instrument on the ground-based Gemini North telescope observed the SDSS 1531 BCGs in IFU-R mode" (2.3 GMOS-N)
- Other facility **HST**: NUV/optical imaging of young stellar superclusters  
  > "Young stellar component" (Table 1)
- External data: Systemic redshift z = 0.3350 ± 0.0002 of southern BCG  
  > "used archival SDSS spectroscopy centered on the southern BCG’s nucleus to pin the stellar redshift to $z = 0.3350 \pm 0.0002$" (2.5 Adopting a Systemic Velocity) [from (cite: tremblay_30_2014)]
- External data: Strong-lensing mass profile of the cluster  
  > "The strong-lensing analysis yields a cylindrical mass of $M(<R_E) = 2.32 \pm 0.01 \times 10^{13} M_\odot$" (3.1.4 Cooling and Free-fall Timescales) [from (cite: sharon_mass_2014)]
- External data: Empirical dust opacity kappa_500um = 0.051 m^2/kg, beta = 1.8  
  > "$\kappa_{500 \mu\mathrm{m}} = 0.051$ m$^2$ kg$^{−1}$, and $\beta = 1.8$" (3.4.4 Undetected Continuum) [from (cite: clark_empirical_2016)]

## Processing

### Calibration

- pipeline or manual: ALMA automated pipeline reduction script  
  > "The raw ALMA visibilities were processed into calibrated measurement sets using the ALMA automated pipeline reduction script in CASA version 6.2.1.7." (2.4 ALMA)
- casa version: CASA 6.2.1.7  
  > "ALMA automated pipeline reduction script in CASA version 6.2.1.7" (2.4 ALMA)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN algorithm (CASA)  
  > "The calibrated visibilities were then imaged and deconvolved with the CLEAN algorithm." (2.4 ALMA)
- deconvolver: _not stated_
- weighting robust: natural weighting adopted (Briggs tested, robust value not given)  
  > "we determined that the natural-weighted 20 km s$^{-1}$ cube without uv-tapering provided the optimal setup" (2.4 ALMA)
- uv taper: none (0.6-1.2'' tapers tested)  
  > "uv-tapering ($0.6\ensuremath{''}$, $0.8\ensuremath{''}$, $1.0\ensuremath{''}$, and $1.2\ensuremath{''}$)" (2.4 ALMA)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: moment maps made from continuum-subtracted cube (method not given)  
  > "The moment maps were created from the continuum-subtracted, calibrated spectral cube" (2.4 ALMA)
- line free channels: _not stated_
- primary beam correction: PBCOR=TRUE  
  > "All CO(3-2) fluxes and line widths reported are corrected for the response of the primary beam (PBCOR=TRUE)." (2.4 ALMA)
- array combination: _not stated_
- smoothing: top-hat 2 channels, Savitzky-Golay order 0, spatial smoothing 2.6 pixels, clip at S/N<3.5  
  > "we spectrally smoothed the data with a top-hat kernel 2 channels wide, applied a Savitzky-Golay filter using a polynomial of order 0, spatially smoothed the data by 2.6 pixels" (2.4 ALMA)
- final beam: 0.53'' x 0.33'' at PA -1.15 deg  
  > "a $0.53\ensuremath{''} \times 0.33\ensuremath{''}$ (2.51 kpc $\times$ 1.59 kpc) synthesized beam" (2.4 ALMA)
- final rms: 0.22 mJy/beam per 20 km/s channel  
  > "0.22 mJy beam$^{-1}$ per 20 km s$^{-1}$ channel" (2.4 ALMA)

### Inherited from earlier work

- Moment maps via quadratic-fit method of bettermoments  
  > "which applies a quadratic fit to the spectral data (cite: teague_robust_2018)" (2.4 ALMA) [from (cite: teague_robust_2018)]
- Molecular mass relation and CO(3-2)/CO(1-0) ratio  
  > "Assuming a CO(3-2)/CO(1-0) line ratio of $\sim0.8$ (cite: edge_detection_2001), we estimate the mass of the molecular H$_2$ nebula by following the relation reviewed by (cite: bolatto_co–h2_2013)" (3.4.3 Mass Distribution) [from (cite: edge_detection_2001); (cite: bolatto_co–h2_2013)]
- Hybrid X-ray/radio cavity power method  
  > "Using the hybrid X-ray-radio method put forward in (cite: timmerman_measuring_2022)" (4.1.4) [from (cite: timmerman_measuring_2022)]

### Not stated but needed to reproduce (our reading)

- Briggs robust value tested
- Line-free channels and order used for continuum subtraction
- clean threshold, mask, niter, cell and image size
- Which of the Compact/Extended execution blocks were combined in the final cube
- Aperture definition and four-Gaussian fit initial guesses for spectrum
- Rest frequency/velocity frame used for channel binning
- Whether archive pipeline products were used or the pipeline was re-run
- Exact definition of the 2-sigma continuum upper-limit and region

## Analysis recipe

1. **Image the CO(3-2) cube**: Pipeline calibration then CLEAN, testing weighting, channel width and uv-taper  
  > "After testing multiple configurations of weightings (natural and Briggs), binning (10, 20, 40, and 80 km s$^{-1}$ channels), and uv-tapering" (2.4 ALMA)
   - software: CASA
   - parameter: natural weighting, 20 km/s channels, no taper  
  > "the natural-weighted 20 km s$^{-1}$ cube without uv-tapering provided the optimal setup, recovering the most emission and maximizing sensitivity" (2.4 ALMA)
   - fitting: _not stated_
   - validation: Compared setups for emission recovered and sensitivity  
  > "recovering the most emission and maximizing sensitivity" (2.4 ALMA)
2. **Make moment maps**: bettermoments quadratic fit after smoothing and S/N clipping  
  > "constructed using the Python package BETTERMOMENTS, which applies a quadratic fit to the spectral data" (2.4 ALMA)
   - software: bettermoments
   - parameter: clip S/N < 3.5 sigma  
  > "applied a sigma clip to all pixels with S/N $< 3.5\sigma$" (2.4 ALMA)
   - assumption: systemic velocity cz = 100,430 km/s (southern nucleus, z=0.3350)  
  > "we adopt a systemic velocity of $cz = 100,430 \text{ km s}^{-1}$" (2.5 Adopting a Systemic Velocity)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive molecular gas mass**: Fit four-component Gaussian to aperture spectrum, convert integral to H2 mass with CO-to-H2 factor  
  > "we fit a four-component Gaussian line to the CO (3-2) spectrum extracted from an elliptical aperture containing all $\geq 3\sigma$ emission" (3.4.3 Mass Distribution)
   - software: pyspeckit
   - parameter: CO(3-2)/CO(1-0)=0.8; D_L=1767 Mpc  
  > "$D_L$ is its luminosity distance (1767 Mpc in our adopted cosmology)" (3.4.3 Mass Distribution)
   - assumption: X_CO = Milky Way disk value 2e20 cm^-2 (K km/s)^-1, ~30% uncertainty  
  > "$X_{\mathrm{CO}} = X_{\mathrm{CO,~MW}} = 2 \times 10^{20}$ cm $\left(\mathrm{K~km~s}^{-1}\right)^{-1}$" (3.4.3 Mass Distribution)
   - fitting: four-component Gaussian, -690 to 900 km/s; sampler/priors not stated  
  > "The fit, from -690 km s$^{-1}$ to 900 km s$^{-1}$, yielded an emission integral of $\sim 1.7 \pm 0.3$ Jy km s$^{-1}$." (3.4.3 Mass Distribution)
   - validation: Compared integrals across binnings and weightings (0.88-2.5 Jy km/s natural)  
  > "With natural weighting, we obtain integrals ranging from $0.88 - 2.5$ Jy km s$^{-1}$ depending on the different binning selected" (3.4.3 Mass Distribution)
4. **Constrain continuum and dust mass**: 2-sigma continuum upper limit converted to dust mass via modified blackbody  
  > "we modeled the emission $S_\nu$ as a modified blackbody using the following equation" (3.4.4 Undetected Continuum)
   - parameter: beta = 1.8, kappa_500um = 0.051 m^2/kg  
  > "$\kappa_{500 \mu\mathrm{m}} = 0.051$ m$^2$ kg$^{−1}$, and $\beta = 1.8$" (3.4.4 Undetected Continuum)
   - assumption: dust temperature 25 K  
  > "Assuming a dust temperature of 25 K (cite: davis_wisdom_2017)" (3.4.4 Undetected Continuum)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compare CO with Halpha and test free-fall and ram-pressure scenarios**: Reproject ALMA maps onto GMOS grid for velocity difference; Hernquist free-fall model on PV diagram; ram-pressure separation timescale  
  > "Using the REPROJECT module from the ASTROPY package, the ALMA maps were resampled onto GMOS pixel grids." (3.4.5 Comparison with the Warm Ionized Gas)
   - software: astropy
   - parameter: free-fall: inclination 72 deg, v_ICM +600 km/s, drop height 16 kpc  
  > "The trajectory assumes an inclination angle of 72$^\circ$ and $v_{ICM}$ of $+600$ km s$^{-1}$." (4.1.4)
   - assumption: Hernquist potential, M ~1e13 Msun within 30 kpc  
  > "The BCGs’ total mass interior to 30 kpc is $\sim 10^{13} M_\odot$ (cite: sharon_mass_2014)." (4.1.4)
   - fitting: _not stated_
   - validation: Free-fall model qualitatively reproduces PV velocity gradient  
  > "This simple gravitational free-fall model broadly reproduces the observed velocity gradient and velocities spanned by the molecular gas" (4.1.4)

## Software

- **CASA** 6.2.1.7 (ALMA); 5.1.0 (VLA): ALMA pipeline calibration and imaging; VLA reduction  
  > "ALMA automated pipeline reduction script in CASA version 6.2.1.7" (2.4 ALMA)
- **bettermoments** : CO(3-2) moment maps  
  > "constructed using the Python package BETTERMOMENTS" (2.4 ALMA)
- **CIAO** v4.13: Chandra reduction  
  > "we used CIAO v4.13" (2.1 Chandra X-ray Observations)
- **ClusterPyXT** : X-ray temperature, pressure, entropy maps  
  > "we used the automated Python pipeline CLUSTERPYXT" (2.1 Chandra X-ray Observations)
- **PyParadise** : GMOS stellar/gas decomposition  
  > "we decoupled and modeled the stellar and gas components of the galaxy using the package PYPARADISE" (2.3 GMOS-N)
- **pPXF** : GMOS emission-line fitting  
  > "Using the publicly available penalized pixel-fitting (pPXF) code" (2.3 GMOS-N)
- **AIPS** 31DEC23: VLA B/D-array calibration and imaging  
  > "Astronomical Image Processing System (AIPS) version 31DEC23" (2.2 Radio Surveys)
- **XSPEC** : ICM spectral fitting with PHABS*APEC  
  > "to a PHABS\*APEC model in XSPEC" (2.1 Chandra X-ray Observations)
- **astropy** : reprojecting ALMA maps to GMOS grid  
  > "Using the REPROJECT module from the ASTROPY package" (3.4.5 Comparison with the Warm Ionized Gas)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(3-2) integrated flux | 1.7 | 0.3 | Jy km/s | 3 | yielded an emission integral of $\sim 1.7 \pm 0.3$ Jy km s$^{-1}$ |
| Molecular H2 gas mass | 3.7e10 | 0.7e10 | Msun | 3 | these results give a $H_2$ gas mass of $(3.7 \pm 0.7) \times 10^{10}\text{ M}_\odot$ |
| Dust mass upper limit | 3.7e8 | not stated | Msun | 4 | we obtain a maximum dust mass of $3.7 \times 10^8$ M$_\odot$ |
| Continuum 2-sigma upper limit | 4.87e-4 | not stated | mJy/beam | 4 | we place $2\sigma$ upper limits of $4.87 \times10^{-4}$ mJy beam$^{-1}$ on the continuum |
| Halpha star formation rate (uncorrected) | 0.60 | 0.009 | Msun/yr | 0 | we use Equation (2) in (cite: kennicutt_global_1998) to obtain a total SFR of $0.60 \pm 0.009$ M$_\odot$ yr$^{-1}$ |
| Cavity enthalpy | ~1e61 | not stated | erg | 0 | we obtain a cavity enthalpy of $\sim 1 \times 10^{61}$ erg |
| Spectral index of Source C | -1.7 | 0.4 | dimensionless | 0 | C- Central avocado-shaped source |
| CO velocity offset from southern BCG | ~+700 | not stated | km/s | 2 | significantly redshifted by $\sim +700$ km s$^{-1}$ with respect to the stellar velocity of the southern BCG |

## Qualitative findings

- CO(3-2) gas is offset by ~1-3 kpc from the young stellar superclusters and comoves with the Halpha gas within ~160 km/s  
  > "it is offset from the young stars by $\sim 1{-}3$ kpc" (abstract)

## Claim tuples

- H: The molecular gas is spatially coincident with the young stellar superclusters | E: Compare ALMA CO(3-2) maps with HST NUV and GMOS Halpha | R: CO is offset by ~1-3 kpc, mostly to the east/southeast | F: Molecular gas is offset from the young stars, attributed to ICM motions/ram pressure | **supported**
- H: The multiphase gas originated from low-entropy gas uplifted by an old AGN cavity | E: Combine Chandra, LOFAR and ALMA/GMOS kinematics and energetics | R: 4pV ~1e61 erg cavity; ~1e10 Msun redshifted cold gas | F: Gas likely cooled in the wake of the rising cavity and is falling back | **partially**
- H: Cold and warm gas are co-moving | E: Velocity difference map of CO and Halpha | R: Differences within ±160 km/s | F: Phases likely co-moving | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Gas captured from gas-rich galaxies or native to BCGs; judged less likely  
  > "Of all the scenarios proposed, we find this to be the least likely." (4.3.2)
- How they decided it was enough: _not stated_
- Limitation (authors): X_CO uncertainty may overestimate molecular mass by a factor of a few  
  > "we may overestimate the total molecular mass by a factor of a few" (3.4.3 Mass Distribution)
- Limitation (authors): Chandra data too shallow to resolve cavity  
  > "the current X-ray data is too shallow to resolve" (3.1.1)
- Caveat (inferred, ours): Mass depends strongly on binning/weighting (1.9-6.5e10 natural; up to 100e9 Briggs)
- Caveat (inferred, ours): Single-dish-free interferometric data may resolve out flux
- Caveat (inferred, ours): Radio relic interpretation rests on two flux points

## Reproducibility

- Data public (paper): ALMA data acknowledged by ADS/JAO.ALMA project code; analysis code on GitHub  
  > "ALMA (data from ADS/JAO.ALMA#2015.1.01426.S)" (Acknowledgments)
- Products in archive: _not stated_
- Code: Python codes/notebooks publicly available at github.com/osaseo/Beads2023_Code  
  > "All Python codes/Jupyter Notebooks used and created to analyze the data are publicly available in an online repository." (2 Observations and Data Reduction)
- Missing: clean parameters and masks
- Missing: continuum subtraction channels
- Missing: spectrum extraction aperture
- Missing: Briggs robust value
- Data volume (inferred): ~20-50 GB raw ALMA data for one project
- Score (inferred): 3/5, Public data and code, but imaging parameters are only partly given.
- Rediscovery candidate: yes, Public ALMA data, numeric mass and flux results, and a mostly specified recipe.

## Links

- Method: (cite: teague_robust_2018) (bettermoments moment maps)
- Method: (cite: bolatto_co–h2_2013) (CO-to-H2 mass relation)
- Companion: (cite: tremblay_30_2014) (Initial Letter on SDSS 1531: redshift and SFR)
- Companion: (cite: sharon_mass_2014) (Strong-lensing mass model)
- Related: LoTSS-DR2
- Related: HST strong-lensing program (HST-GO-13003)

## Checks

```json
{
 "quotes": 80,
 "quotes_ok": 80,
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
  "facts": 92,
  "stated": 66,
  "rate": 0.717
 },
 "evidence_ok": true
}
```

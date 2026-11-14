# Molecular Gas Along a Bright Hα Filament in 2A 0335+096 Revealed by ALMA

`2016ApJ...832..148V` | The Astrophysical Journal 2016 | first author: Vantyghem, A. N. | arXiv: 1610.00716 | DOI: 10.3847/0004-637X/832/2/148

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: galaxy_clusters_and_sz, nearby_galaxies
- Question: What is the distribution, kinematics and origin of the molecular gas in the 2A 0335+096 BCG and its Halpha filament?  
  > "The ALMA observations presented here resolve the spatial and velocity structure of the molecular gas within the BCG, revealing a striking correlation between molecular gas and the H$\alpha$ filament." (1 Introduction)
- Target **2A 0335+096 BCG**: coordinates RA 03:38:40.50, Dec +09:58:12.3  
  > "The brightest cluster galaxy (BCG) in the 2A 0335+096 galaxy cluster (RA: 03:38:40.50, Dec: +09:58:12.3)" (2 Observations and Data Reduction); "the angular scale is $1\ensuremath{''} = 700\rm\; pc$ and the luminosity distance is $150\rm\; Mpc$." (1 Introduction); z/distance z=0.0346; D_L=150 Mpc  
  > "The brightest cluster galaxy (BCG) in the 2A 0335+096 galaxy cluster (RA: 03:38:40.50, Dec: +09:58:12.3)" (2 Observations and Data Reduction); "the angular scale is $1\ensuremath{''} = 700\rm\; pc$ and the luminosity distance is $150\rm\; Mpc$." (1 Introduction); distance from redshift from McNamara et al. 1990 (stellar absorption), H0=70 cosmology  
  > "The brightest cluster galaxy (BCG) in the 2A 0335+096 galaxy cluster (RA: 03:38:40.50, Dec: +09:58:12.3)" (2 Observations and Data Reduction); "the angular scale is $1\ensuremath{''} = 700\rm\; pc$ and the luminosity distance is $150\rm\; Mpc$." (1 Introduction)

## Data provenance

- ALMA projects: 2012.1.00837.S
- bands: Band 3 (CO 1-0) and Band 7 (CO 3-2)  
  > "The CO(1-0) observation was divided into two blocks, which were observed in band 3" (2 Observations and Data Reduction)
- frequencies and spectral setup: centred at 111.394 GHz and 334.169 GHz; 488.281 kHz (1.31 km/s) resolution over 1.875 GHz  
  > "centred at $111.394\rm\; GHz$ and $334.169\rm\; GHz$ to cover the CO(1-0) and CO(3-2) lines." (2 Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 17-716 m and 12-280 m (CO 1-0); 19-915 m (CO 3-2)  
  > "The observation used 34 antennas with baselines of $19-915\rm\; m$" (2 Observations and Data Reduction)
- angular resolution: 1.3''x0.92'' CO(1-0); 0.39''x0.23'' CO(3-2)  
  > "The resulting images had a synthesized beam of $1.3''\times 0.92''$ (PA $-34.5^{\circ}$) at CO(1-0)" (2 Observations and Data Reduction)
- max recoverable scale: ~11'' at CO(1-0), ~3'' at CO(3-2)  
  > "Missing short spacings will filter out emission on spatial scales larger than $\sim11''$ at CO(1-0) and $\sim3''$ at CO(3-2)." (2 Observations and Data Reduction)
- sensitivity: _not stated_
- time on source: 35 min per CO(1-0) block; 30 min CO(3-2)  
  > "Both observations had an on-source integration time of 35 minutes." (2 Observations and Data Reduction)
- observing dates: 22 Jul 2014, 08 Mar 2015 (CO 1-0); 12 Aug 2014 (CO 3-2)  
  > "on August 12, 2014" (2 Observations and Data Reduction)
- pi or archival as stated: _not stated_
- Line: CO J=1-0 (not stated)
- Line: CO J=3-2 (not stated)
- Other facility **HST WFPC2 F606W**: archival optical image for dust extinction mapping  
  > "The calibrated HST WFPC2 F606W image was obtained from the Hubble Legacy Archive." (3.5 Spatial Correlation with Dust Extinction)
- Other facility **Chandra**: X-ray imaging comparison  
  > "*Chandra* imaging of 2A 0335+096, shown in Fig. [14](#fig:xray), reveals a series of X-ray cavities" (4.2.1 Cooling Stimulated by the AGN)
- External data: Halpha nebula image  
  > "Fig. [13](#fig:halpha) shows the H$\alpha$ nebula from (cite: donahue07) overlaid with contours of the CO(1-0) emission." (3.6 Spatial Correlation with X-ray and Halpha Filaments) [from (cite: donahue07)]
- External data: IRAM 30m CO(1-0) flux 11.4±1.1 Jy km/s  
  > "$11.4\pm1.1\hbox{$\rm\; Jy\rm\; km\rm\; s^{-1}\,$}$; (cite: edge01)" (3.1 Distribution of Molecular Gas) [from (cite: edge01)]
- External data: cluster total mass within 30 kpc 2.1e12 Msun  
  > "the total mass interior to $30\rm\; kpc$ is $2.1\ensuremath{\times 10^{12}}\hbox{$\rm\thinspace M_{\odot}$}$" (4.3.2 Clouds in Gravitational Free-fall) [from (cite: main15)]

## Processing

### Calibration

- pipeline or manual: automatic pipeline scripts, plus phase self-cal on nuclear continuum  
  > "The observations were primarily calibrated in CASA version 4.4.0 (cite: casa) using the automatic pipeline scripts." (2 Observations and Data Reduction)
- casa version: CASA 4.4.0  
  > "calibrated in CASA version 4.4.0" (2 Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: phase self-cal on nuclear continuum improved CO(1-0) S/N by 1.2; not possible at CO(3-2)  
  > "Additional phase self-calibration on the nuclear continuum improved the signal-to-noise of the CO(1-0) observation by a factor of $1.2$." (2 Observations and Data Reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs weighting of 2  
  > "Images of line emission were reconstructed using CLEAN with a Briggs weighting of 2." (2 Observations and Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: none applied to CO(3-2)  
  > "No continuum subtraction was applied to the CO(3-2) observation" (2 Observations and Data Reduction)
- line free channels: _not stated_
- primary beam correction: maps and spectra corrected for primary beam response  
  > "The maps have been corrected for the response of the primary beam" (3.1 Distribution of Molecular Gas)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.3''x0.92'' PA -34.5 deg; 0.39''x0.23'' PA -50.0 deg  
  > "$0.39''\times 0.23''$ (PA $-50.0^{\circ}$) at CO(3-2)" (2 Observations and Data Reduction)
- final rms: 0.56 mJy/beam (CO 1-0), 0.61 mJy/beam (CO 3-2) in 20 km/s channels  
  > "The rms noise in $20\hbox{$\rm\; km\rm\; s^{-1}\,$}$ line-free channels was $0.56\rm\; mJy~{\rm beam}^{-1}$ and $0.61\rm\; mJy~{\rm beam}^{-1}$" (2 Observations and Data Reduction)

### Inherited from earlier work

- Gaussian-component significance tested by Monte Carlo  
  > "The significance of the line was tested using a Monte Carlo analysis following the prescription of (cite: protassov02)" (3.3 Velocity Distribution) [from (cite: protassov02)]
- Hernquist-profile free-fall model  
  > "Following (cite: lim08), we assume that the gravitational potential can be modelled by a Hernquist profile" (4.3.2 Clouds in Gravitational Free-fall) [from (cite: lim08)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges used for continuum imaging
- Image size, cell size, clean masks and threshold
- Whether the 2015 CO(1-0) execution was fully excluded from the imaged cube (yes, but flux scale details not given)
- Priors/initial guesses for LMFIT Gaussian fits and number-of-component selection details
- Hernquist model free-fall parameters beyond inclination 25 deg and offset -200 km/s
- Spatial regions' exact box definitions beyond figures

## Analysis recipe

1. **Calibrate and image**: CASA pipeline calibration, phase self-cal, CLEAN with Briggs weighting 2; 2015 CO(1-0) block excluded  
  > "We therefore do not include this observation in our analysis." (2 Observations and Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract and fit spectra**: Spectra from regions fitted with one to three Gaussians, corrected for primary beam and binning broadening  
  > "Spectral fitting throughout this work used the LMFIT [^1] package with one to three Gaussian components, as necessary." (3.1 Distribution of Molecular Gas)
   - software: LMFIT
   - fitting: Gaussian least-squares, chi2/dof reported  
  > "Spectral fitting throughout this work used the LMFIT [^1] package with one to three Gaussian components, as necessary." (3.1 Distribution of Molecular Gas)
   - validation: Comparison of total flux with OVRO and IRAM 30m  
  > "This flux constitutes $43\pm7~\%$ of the IRAM 30m flux" (3.1 Distribution of Molecular Gas)
3. **Derive molecular gas masses**: Convert CO(1-0) flux with Galactic X_CO; CO(3-2) via flux ratio 7  
  > "We therefore adopt a factor of 7 difference between the two integrated fluxes" (3.2 Molecular Gas Mass)
   - assumption: X_CO = 2e-20 cm^-2 (K km/s)^-1; D_L = 150 Mpc  
  > "We assume a Galactic CO-to-H$_2$ conversion factor, $X_{\rm CO, gal} = 2\ensuremath{\times 10^{-20}}" (3.2 Molecular Gas Mass)
   - fitting: _not stated_
   - validation: _not stated_
4. **Velocity maps and PV diagrams**: Per-pixel single then second Gaussian fits (2 sigma detection); PV slices of set widths  
  > "Each spectrum was fit with a single Gaussian component." (3.3 Velocity Distribution)
   - fitting: Monte Carlo significance test  
  > "The significance of the line was tested using a Monte Carlo analysis following the prescription of (cite: protassov02), with detections requiring a $2\sigma$ significance." (3.3 Velocity Distribution)
   - validation: _not stated_
5. **Dust extinction map from HST**: Core-Sersic model of BCG plus Sersic companion fitted with Galfit-M; I/I0 converted to tau, N_H and dust mass  
  > "we model the 2D distribution of stellar light using the galaxy-fitting code Galfit-M" (3.5 Spatial Correlation with Dust Extinction)
   - software: Galfit-M, IRAF
   - assumption: Galactic V-band extinction curve, N_H = 2.05e21 tau_V  
  > "through $N_H = 2.05\ensuremath{\times 10^{21}} \tau_V \hbox{$\rm\; cm^2\,$}$" (3.5 Spatial Correlation with Dust Extinction)
   - fitting: _not stated_
   - validation: regions confirmed by eye  
  > "These regions were confirmed by eye in the original image." (3.5 Spatial Correlation with Dust Extinction)
6. **Free-fall model of filament**: Hernquist potential infall compared to PV diagram  
  > "assuming an inclination angle of $25^{\circ}$ and a velocity offset of $-200\hbox{$\rm\; km\rm\; s^{-1}\,$}$" (4.3.2 Clouds in Gravitational Free-fall)
   - assumption: scale length 7.4 kpc from 2MASS R_e; total mass from Main et al. 2015 NFW  
  > "Taking an effective radius of $19.24\ensuremath{''}$ ($13.47\rm\; kpc$) from the 2MASS K-band catalog, the corresponding scale length is $7.4\rm\; kpc$." (4.3.2 Clouds in Gravitational Free-fall)
   - fitting: _not stated_
   - validation: compared with PV data; not definitive  
  > "differences between the data and the model prevent any definitive conclusions about the gas undergoing free-fall from being drawn" (4.3.2 Clouds in Gravitational Free-fall)

## Software

- **CASA** 4.4.0: calibration and imaging  
  > "calibrated in CASA version 4.4.0" (2 Observations and Data Reduction)
- **LMFIT** : Gaussian spectral fitting  
  > "Spectral fitting throughout this work used the LMFIT" (3.1 Distribution of Molecular Gas)
- **Galfit-M** : 2D optical fitting of BCG and companion  
  > "using the galaxy-fitting code Galfit-M" (3.5 Spatial Correlation with Dust Extinction)
- **IRAF** : Synphot band transformation and ellipse isophotes  
  > "in the IRAF tool Synphot" (3.5 Spatial Correlation with Dust Extinction)
- **APLpy** : plotting  
  > "This research made use of APLpy, an open-source plotting package for Python" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total molecular gas mass | 1.13e9 | ±0.15e9 | Msun | 3 | corresponds to a molecular gas mass of $1.13\pm0.15\ensuremath{\times 10^{9}}\hbox{$\rm\thinspace M_{\odot}$}$ |
| Filament molecular gas mass | 7.8e8 | ±0.9e8 | Msun | 3 | $7.8\pm0.9\ensuremath{\times 10^{8}}\hbox{$\rm\thinspace M_{\odot}$}$ is contained in the elongated filament |
| BCG molecular gas mass | 3.2e8 | ±0.4e8 | Msun | 3 | The central molecular gas component accounts for $3.2\pm0.4\ensuremath{\times 10^{8}}\hbox{$\rm\thinspace M_{\odot}$}$ |
| Total CO(1-0) flux | 4.8 | ±0.6 | Jy km/s | 2 | The total CO(1-0) flux recovered by these observations is $4.8\pm0.6\hbox{$\rm\; Jy\rm\; km\rm\; s^{-1}\,$}$ |
| CO(3-2)/CO(1-0) flux ratio | 7.2 | ±1.4 | dimensionless | 3 | ${\rm CO(3-2)/CO(1-0)}=7.2\pm1.4$ |
| Nuclear continuum flux at 109.84 GHz (July 2014) | 6.854 | ±0.044 | mJy | 1 | the nuclear continuum flux is $6.854\pm0.044\rm\; mJy$ in the July 2014 observation |
| Continuum spectral index | 1.61 | ±0.27 | dimensionless | 1 | is $\alpha=1.61\pm0.27$ |
| Filament gas-to-dust ratio | 66 | not stated | dimensionless | 5 | the local gas-to-dust ratio is $66$ |
| Total dust mass in table | 173 | ±8 | 1e5 Msun | 5 | Total /  /  /  /  /  / $173\pm8$ |

## Qualitative findings

- CO emission is co-spatial with the Halpha filament and dust extinction  
  > "The CO emission is co-spatial with a $10^4\rm\; K$ emission-line nebula and soft X-rays from 0.5 keV gas" (abstract)

## Claim tuples

- H: Is the nuclear gas a rotating disk? | E: CO(1-0) and CO(3-2) maps, spectra, PV diagrams | R: two blueshifted clumps south and redshifted clumps toward companion | F: interaction with companion <20 Myr ago disrupted pre-existing gas | **partially**
- H: Did the filament gas cool from the ICM? | E: compare CO with Halpha, 0.5 keV X-ray, dust | R: co-spatial emission; cooling time 25-100 Myr | F: gas cooled from low entropy ICM lifted by cavity | **supported**
- H: Is the filament infalling or outflowing? | E: PV diagram and Hernquist free-fall model | R: velocity gradient consistent with free-fall but model has degeneracies | F: cannot distinguish inflow from outflow | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Ram pressure stripping and cooling wake considered; stimulated cooling favoured  
  > "we favour stimulated cooling throughout the remainder of our discussion" (4.2.4 Summary: Cooling Origin)
- How they decided it was enough: _not stated_
- Limitation (authors): Only 43% of single-dish flux recovered; missing short spacings  
  > "implying that over half of the molecular gas is undetected in our observations" (3.1 Distribution of Molecular Gas)
- Caveat (inferred, ours): Galactic X_CO and fixed CO(3-2)/CO(1-0)=7 dominate mass uncertainty
- Caveat (inferred, ours): Free-fall model has too many free parameters
- Caveat (inferred, ours): Briggs weighting value 2 is atypical and unexplained
- Caveat (inferred, ours): Missing flux affects mass and filament comparisons

## Reproducibility

- Data public (paper): ALMA program 2012.1.00837.S acknowledged  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA 2012.1.00837.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Clean parameters (mask, threshold, image size, cell)
- Missing: Line-free channel selection
- Missing: Exact region boxes for spectra
- Missing: Free-fall model parameters
- Data volume (inferred): ~50-100 GB raw
- Score (inferred): 3/5, Data public and simple methods, but imaging and region details are incomplete.
- Rediscovery candidate: yes, Public data, numeric masses and Gaussian fits are redoable.

## Links

- Method: (cite: protassov02) (Monte Carlo line significance test)
- Method: (cite: lim08) (free-fall model)
- Companion: (cite: almaPKS0745) (similar ALMA BCG filament results)
- Companion: (cite: almaA1835) (similar ALMA BCG outflow)

## Checks

```json
{
 "quotes": 68,
 "quotes_ok": 68,
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
  "facts": 79,
  "stated": 49,
  "rate": 0.62
 },
 "evidence_ok": true
}
```

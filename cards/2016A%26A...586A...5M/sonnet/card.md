# A detailed view of the gas shell around R Sculptoris with ALMA

`2016A&A...586A...5M` | Astronomy and Astrophysics 2016 | first author: Maercker, M. | arXiv: 1512.01350 | DOI: 10.1051/0004-6361/201527128

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars
- Question: What are the mass and temperature of the gas shell around R Scl, and how did the mass-loss rate evolve during and after the thermal pulse?  
  > "We aim to determine the physical properties of the detached gas shell around R Sculptoris, in particular the shell mass and temperature, and to constrain the evolution of the mass-loss rate during and after a thermal pulse." (abstract)
- Target **R Sculptoris (R Scl)**: coordinates _not stated_; z/distance 370 pc  
  > "We will use 370 pc throughout this paper, noting the high uncertainty in this value." (2.1 R Sculptoris); distance from Knapp et al. 2003; Whitelock et al. 2008 (adopted, highly uncertain)  
  > "We will use 370 pc throughout this paper, noting the high uncertainty in this value." (2.1 R Sculptoris)

## Data provenance

- ALMA projects: 2011.0.00131.S
- bands: Band 3 (CO 1-0), Band 6 (CO 2-1), Band 7 (CO 3-2)  
  > "The main target of the observations were the $^{12}\rm{CO}(1-0)$ line in Band 3, the $^{12}\rm{CO}(2-1)$ line in Band 6, and the $^{12}\rm{CO}(3-2)$ line in Band 7." (2.2 ALMA early science observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Cycle 0 compact configuration of the main array, pointed mosaics; no ACA  
  > "R Scl was observed during ALMA Cycle 0 using the compact configuration of the main array." (2.2 ALMA early science observations)
- baselines: _not stated_
- angular resolution: 3.8''x2.8'' (1-0), 2.1''x1.7'' (2-1), 1.6''x1.2'' (3-2)  
  > "| $^{12}\rm{CO}(2-1)$ | 2.1$''$ $\times$ 1.7$''$ | 11$''$ | 1.0 | 6.4 |" (Table 1)
- max recoverable scale: 18'' (1-0), 11'' (2-1), 7'' (3-2)  
  > "| $^{12}\rm{CO}(3-2)$ | 1.6$''$ $\times$ 1.2$''$ | 7$''$ | 0.5 | 16.0 |" (Table 1)
- sensitivity: rms 7.3, 6.4, 16.0 mJy/beam for 1-0, 2-1, 3-2  
  > "| $^{12}\rm{CO}(1-0)$ | 3.8$''$ $\times$ 2.8$''$ | 18$''$ | 1.5 | 7.3 |" (Table 1)
- time on source: 64 min (Band 3), 90 min (Band 6), 155 min (Band 7)  
  > "| 7             | 1875.0  | 0.488      | 45            | 155            | 3c454.3        | Neptune  | 331.17:$^{13}$CO(3–2)       |   |" (Table 1 (setup))
- observing dates: Band 3: Jan 23-25 2012; Band 6: Oct 1 2011; Band 7: Oct 3-19 2011  
  > "Observations of the $^{12}\rm{CO}(2-1)$ emission line at 230.54 GHz were carried out on Oct 1 2011." (2.2 ALMA early science observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=1-0 (115.27 GHz)
- Line: 12CO J=2-1 (230.54 GHz)
- Line: 12CO J=3-2 (345.80 GHz)
- Other facility **APEX**: New OTF maps of CO(2-1) and CO(3-2) single-dish spectra  
  > "For the $^{12}\rm{CO}(2-1)$ and $^{12}\rm{CO}(3-2)$ transitions we observed two on-the-fly (OTF) maps with APEX." (2.3 Single-dish observations)
- Other facility **SEST and IRAM 30m**: CO(1-0) single-dish spectra from earlier work  
  > "For the $^{12}\rm{CO}(1-0)$ transition we use spectra from the Swedish-ESO submillimeter telescope (cite: olofssonetal1996) and the IRAM 30m telescope (cite: olofssonetal1993a)." (2.3 Single-dish observations)
- External data: Shell radius 19.5'' and width 2'' from dust-scattered light  
  > "The radius and width of the shell were measured with high precision in images of dust scattered, stellar light, to be 19.5$''$$\pm$0.5$''$ and 2$''$$\pm$1$''$" (2.1 R Sculptoris) [from (cite: olofssonetal2010; maerckeretal2014)]
- External data: 12CO abundance 4.3e-4 relative to H2  
  > "We assume a fractional abundance of $^{12}$CO of f($^{12}$CO)=$4.3\times10^{-4}$ relative to H$_2$ (cite: olofssonetal1993a)." (3.2 The shell emission) [from (cite: olofssonetal1993a)]
- External data: Present-day mass-loss rate ~3e-7 Msun/yr from HCN models  
  > "The present-day mass-loss rate is estimated to be $\approx$3$\times10^{-7}$ $M_{\odot}$ yr$^{-1}$ based on HCN models (cite: schoieretal2005)." (3.3 The recent evolution of the stellar wind) [from (cite: schoieretal2005)]

## Processing

### Calibration

- pipeline or manual: Data re-reduced with CASA python scripts; SBs calibrated separately then combined  
  > "The delivered data was re-reduced to improve the data quality using version 4.1 of the Common Astronomy Software Application (*CASA*), making use of python scripts to automate the calibration process." (2.2 ALMA early science observations)
- casa version: CASA 4.1  
  > "using version 4.1 of the Common Astronomy Software Application (*CASA*)" (2.2 ALMA early science observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto (Band 3), Neptune (Bands 6, 7)  
  > "| 3             | 937.5   | 0.244      | 7             | 64             | J0522-364      | Callisto | 101.5: continuum            |   |" (Table 1 (setup))
- flux scale uncertainty: ≈10-20%  
  > "The absolute calibration uncertainty is $\approx$10-20%." (Table 1)
- self calibration: _not stated_

### Imaging

- task: CLEAN  
  > "imaging of the CO emission lines was carried out with the CLEAN algorithm using natural weighting and binning the spectra." (2.2 ALMA early science observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "imaging of the CO emission lines was carried out with the CLEAN algorithm using natural weighting and binning the spectra." (2.2 ALMA early science observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Iterative masks with decreasing CLEAN thresholds  
  > "The complex structures of the CO envelope were masked in an iterative procedure with decreasing thresholds in CLEAN." (2.2 ALMA early science observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Smoothed to 4'' and 1.5 km/s for shell extraction; imsmooth to SD beams for comparison  
  > "we smoothed the images to a spatial resolution of 4$''$ and a velocity resolution of 1.5 km s$^{-1}$." (3.2 The shell emission)
- final beam: _not stated_
- final rms: 7.3, 6.4, 16.0 mJy/beam  
  > "the rms is measured in line-free channels in the final reduced images." (Table 1)

### Inherited from earlier work

- Shell radius and expansion velocity used for extraction (19.5'', 14.3 km/s)  
  > "assuming a shell-radius of 19.5$''$ and an expansion velocity of 14.3 km s$^{-1}$ (cite: maerckeretal2012; maerckeretal2014)." (3.2 The shell emission) [from (cite: maerckeretal2012; maerckeretal2014)]
- Fractional abundance profile exponent a=2.5  
  > "and a=2.5 (cite: mamonetal1988)" (3.3 The recent evolution of the stellar wind) [from (cite: mamonetal1988)]
- Radiative transfer code (1D Monte Carlo)  
  > "we calculated a grid of 1-dimensional radiative transfer models based on the monte-carlo technique (cite: schoierco2001)." (3.2 The shell emission) [from (cite: schoierco2001)]

### Not stated but needed to reproduce (our reading)

- Phase and other calibrator details, flagging and bandpass solutions
- Exact CLEAN thresholds, cell and image size
- Channel binning and line-free channels
- Molecular data (collisional rates) used in radiative transfer
- Details of shell subtraction normalisation and how SD data beam-matched
- Treatment of ALMA flux scale across SBs
- Model grid for the CSE fits (how the fit was chosen)

## Analysis recipe

1. **Compare ALMA with single-dish to quantify missing flux**: Smooth ALMA cubes to SD beams with imsmooth and compare spectra to SD spectra  
  > "Figure [4](#f:sdspec) shows a comparison of observed SD spectra with the equivalent ALMA spectra extracted from maps that were smoothed to the same respective beams using the task *imsmooth* in *CASA*." (2.4 Interferometer vs. single-dish observations and extended emission)
   - software: CASA
   - fitting: _not stated_
   - validation: Toy CASA simulations of shell, spiral and extended discs reproduce observed images qualitatively  
  > "Simulations in *CASA*, using the ALMA Cycle 0 compact configuration in the three bands, show that the observed features can indeed be explained" (2.4 Interferometer vs. single-dish observations and extended emission)
2. **Extract shell spectra**: Extract ring of width ±3'' centred on shell radius in channel maps smoothed to 4'' and 1.5 km/s  
  > "the shell emission is extracted from a ring with width $\pm$3$''$ centred on the shell." (3.2 The shell emission)
   - software: CASA
   - parameter: shell radius 19.5'', v_exp 14.3 km/s  
  > "assuming a shell-radius of 19.5$''$ and an expansion velocity of 14.3 km s$^{-1}$" (3.2 The shell emission)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit shell mass and temperature**: Grid of 1D Monte Carlo radiative transfer models, chi2 minimisation on integrated intensities of all transitions  
  > "For each model we determine the best-fit model (Fig. [6](#f:shellspec)) by minimising the $\chi^2$ value" (3.2 The shell emission)
   - software: Monte Carlo radiative transfer code (Schöier & Olofsson 2001)
   - parameter: masses 2.5e-3 to 4.75e-3 Msun step 0.25e-3; T 10-290 K step 20 K; Gaussian shell FWHM 2''  
  > "The grid is calculated for shell-masses between $2.5\times10^{-3}$ $M_{\odot}$ to $4.75\times10^{-3}$ $M_{\odot}$ in steps of $0.25\times10^{-3}$ $M_{\odot}$ and temperatures between 10 K to 290 K in steps of 20 K." (3.2 The shell emission)
   - assumption: f(12CO)=4.3e-4, constant temperature, 20% observational uncertainty, distance 370 pc  
  > "The temperature is assumed to be constant throughout the shell." (3.2 The shell emission)
   - fitting: chi2 minimisation over grid, sigma=20%  
  > "$\sigma_{\rm{obs,i}}$ is the uncertainty in the observation is assumed to be 20%" (3.2 The shell emission)
   - validation: Compared with Olofsson et al. 2015 results from SD and CI  
  > "using essentially independent methods (interferometry vs. SD observations and an independent consistency check with CI observations)" (3.2 The shell emission)
4. **Model CSE mass-loss from shell-subtracted SD spectra**: Convolve best-fit shell model with SD beams, subtract from SD spectra, model residual with constant mass-loss rate radiative transfer  
  > "we convolved the best-fit model of the shell with the SD beams of the respective transitions (Fig. [7](#f:sdsub), top), and subtract it from the SD observations." (3.3 The recent evolution of the stellar wind)
   - software: Monte Carlo radiative transfer code (Schöier & Olofsson 2001)
   - parameter: a=2.5; T_kin power law beta=-0.85; R0 = 3 stellar radii; velocity 3 to 14.3 km/s  
  > "The velocity increases gradually from 3 km s$^{-1}$ to 14.3 km s$^{-1}$" (3.3 The recent evolution of the stellar wind)
   - assumption: Constant mass-loss rate, 1/r^2 density, black-body Teff 2300 K, L 5200 Lsun  
  > "Assuming a constant mass-loss rate results in a 1/$r^2$ density distribution." (3.3 The recent evolution of the stellar wind)
   - fitting: Manual fit to SD spectra; model degenerate  
  > "Finally, the models are very degenerate between the chosen mass-loss rate, half-abundance radius, temperature profile, and velocity profile." (3.3 The recent evolution of the stellar wind)
   - validation: Emitting region sizes consistent with ALMA/SD limits  
  > "These results are consistent with the limits set by the ALMA and SD data" (3.3 The recent evolution of the stellar wind)

## Software

- **CASA** 4.1: Calibration, CLEAN imaging, imsmooth, simulations  
  > "using version 4.1 of the Common Astronomy Software Application (*CASA*)" (2.2 ALMA early science observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Shell mass | 4.5e-3 | ±1.5e-3 | Msun | 3 | The best-fit model gives a shell-mass of $(4.5\pm1.5)\times10^{-3}$ $M_{\odot}$ at a temperature of 50$^{+200}_{-20}$ K. |
| Shell temperature | 50 | +200/-20 | K | 3 | at a temperature of 50$^{+200}_{-20}$ K |
| Mass-loss rate during shell creation | 2.3e-5 | +1.7/-1.3 e-5 | Msun/yr | 3 | leads to a mass-loss rate of $(2.3^{+1.7}_{-1.3})\times10^{-5}$ $M_{\odot}$ yr$^{-1}$ during the creation of the shell. |
| Average post-pulse mass-loss rate | 1.6e-5 | not stated | Msun/yr | 4 | using a mass-loss rate of 1.6$\times10^{-5}$ $M_{\odot}$ yr$^{-1}$ and a half-abundance radius of 7.2$''$. |
| Recent mass-loss rate (IRAM CO 1-0, APEX CO 3-2) | 3.5e-6 | not stated | Msun/yr | 4 | a mass-loss rate of 3.5$\times10^{-6}$ $M_{\odot}$ yr$^{-1}$ |
| Total mass lost since last TP | 0.03 | not stated | Msun | 0 | the total mass lost by R Scl since the onset of the most recent TP is 0.03 $M_{\odot}$. |

## Qualitative findings

- The shell is entirely filled with gas, not detached  
  > "Extended emission from $^{12}$CO reaching out to the shell means that the shell is in fact not detached, but instead filled with significant amounts of molecular gas." (2.4 Interferometer vs. single-dish observations and extended emission)
- An additional high-velocity component (±18 km/s) is centred on the star, origin unclear  
  > "However, it is not clear what the origin of this higher-velocity component is." (3.4 An additional velocity component)

## Claim tuples

- H: Is the CO shell around R Scl detached? | E: Compared multi-scale ALMA CO data to SD spectra and toy simulations | R: Extended CO emission fills the shell; CO(1-0) extends almost to the shell | F: The shell is filled, not detached | **supported**
- H: Shell mass and temperature | E: Radiative transfer chi2 grid fit to ALMA shell spectra | R: 4.5e-3 Msun at 50 K | F: Consistent with SD-based estimates | **supported**
- H: Post-pulse mass-loss declines sharply | E: Modelled shell-subtracted SD spectra | R: Average 1.6e-5 Msun/yr over ~2100 yr | F: Decline is slower than models; total mass lost 0.03 Msun, ~4x classical | **partially**

## Reasoning

- Why this data: Resolve shell from inner CSE emission with high spatial resolution  
  > "The spatial resolution of the ALMA data allows us to separate the detached shell emission from the extended emission inside the shell." (abstract)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Cycle 0 lacks ACA, so extended flux is lost; mass-loss modelling degenerate  
  > "The loss of extended flux in the current ALMA data prevents using these observations to effectively constrain the mass-loss rate evolution" (3.3 The recent evolution of the stellar wind)
- Limitation (authors): Distance very uncertain  
  > "Current distance estimates are very uncertain, ranging from 266 pc" (2.1 R Sculptoris)
- Caveat (inferred, ours): Constant-mass-loss, smooth 1D models applied to a clumpy, spiral CSE
- Caveat (inferred, ours): 12CO abundance assumed; shell mass is a lower limit
- Caveat (inferred, ours): Uncertainties on mass-loss rates not given for the CSE fit
- Caveat (inferred, ours): Distance uncertainty scales masses and rates

## Reproducibility

- Data public (paper): ALMA Cycle 0 project cited; SD data from literature and APEX  
  > "This paper makes use of ALMA data from project no. ADS/ JAO.ALMA#2011.0.00131.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Radiative transfer model inputs and molecular data
- Missing: APEX and SEST/IRAM spectra
- Missing: CLEAN parameters
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Public Cycle 0 data and clear modelling grid, but CLEAN and CSE fit details are lacking.
- Rediscovery candidate: no, Requires SD spectra and a specific RT code; CSE fit is not fully specified.

## Links

- Method: (cite: schoierco2001) (1D Monte Carlo radiative transfer code)
- Companion: (cite: maerckeretal2012) (Earlier CO(3-2) ALMA analysis of spiral and hydrodynamics)
- Companion: (cite: maerckeretal2014) (Dust-scattered light shell properties)
- Related: ALMA Cycle 2 follow-up of R Scl

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
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 48,
  "rate": 0.658
 },
 "evidence_ok": true
}
```

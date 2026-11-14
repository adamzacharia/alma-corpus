# Hints of Disk Substructure in the First Brown Dwarf with a Dynamical Mass Constraint

`2025ApJ...986L..11S` | The Astrophysical Journal Letters 2025 | first author: Santamaría-Miranda, Alejandro | arXiv: 2505.08107 | DOI: 10.3847/2041-8213/add71f

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Does the disk of the brown dwarf 2M0444 show Keplerian rotation (giving a dynamical mass), radial drift, and dust substructure at high resolution?  
  > "The line emission traces a Keplerian disk, allowing us to derive a dynamical mass between 0.043 - 0.092 M${_{\odot}}$ for the central object." (abstract)
- Target **2MASS J04442713+2512164 (2M0444)**: coordinates _not stated_; z/distance ~140 pc  
  > "it is an M7.25 spectral type and a Class II source (cite: Luhman10) located in Taurus at a distance of $\sim$140 pc" (Introduction); distance from Galli et al. 2018 (cite: Galli18-2)  
  > "it is an M7.25 spectral type and a Class II source (cite: Luhman10) located in Taurus at a distance of $\sim$140 pc" (Introduction)

## Data provenance

- ALMA projects: 2023.1.00158.S
- bands: Band 7 (0.89 mm)  
  > "2M0444 was observed with the ALMA 12-meter array in Band 7" (2 Observation and data reduction)
- frequencies and spectral setup: Basebands at 331.362, 333.320, 343.362 GHz (1.36-1.41 km/s resolution); 12CO(3-2) baseband at 345.796 GHz (0.42 km/s); 1.875 GHz per baseband  
  > "The fourth baseband was tuned to the $^{12}$CO (3-2) line at 345.796 GHz, with a spectral resolution of 0.42 km s$^{-1}$." (2 Observation and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-8 (three dates Oct-Nov 2023) and C43-5 (May 2024)  
  > "Observations using the long baseline configuration (C43-8) were carried out on three dates between October and November 2023, followed by an additional observation in May 2024 using the shorter baseline configuration C43-5." (2 Observation and data reduction)
- baselines: 15-8547 m  
  > "| 13 Oct 2023 | C43-8 | 91-8547 | 44 | 33 | 0.8 |" (Table (observing log))
- angular resolution: 0.046" continuum (~6.4 au); ~0.062" 12CO  
  > "The angular resolution of the continuum maps is 0$\hbox{$.\!\!^{\prime\prime}$}$046 (equivalent to $\sim$6.4 au at a distance of 140 pc)" (2 Observation and data reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 2.01 h long baseline; 0.71 h short baseline  
  > "The total on-source integration time was 2.01 hours for the long-baseline observations and 0.71 hours for the short-baseline configuration." (2 Observation and data reduction)
- observing dates: 12 Oct, 13 Oct, 2 Nov 2023; 30 May 2024  
  > "| 30 May 2024 | C43-5 | 15-1261 | 45 | 38 | 0.7 | J0423-0120, J0423-0120, J0438+3004 | J0440+2728 |" (Table (observing log))
- pi or archival as stated: Own program, PI A. Santamaría-Miranda  
  > "as part of project 2023.1.00158.S (PI: A. Santamaría-Miranda)" (2 Observation and data reduction)
- Line: 12CO 3-2 (345.796 GHz)
- Line: 13CO 3-2 (330.58 GHz)
- External data: Distance ~140 pc used for conversions and EDDY  
  > "we assumed a distance of $\sim$ 140 pc (cite: Galli18-2)" (3.1 Disk rotation in the image plane) [from (cite: Galli18-2)]
- External data: Disk mass 1.3±0.2 MJup from earlier ALMA data, compared with own revisit  
  > "(cite: Riccietal14-1) reported a disk mass of $1.3 \pm 0.2$ M${\text{Jup}}$" (4.1 Substellar Mass of 2M0444) [from (cite: Riccietal14-1)]
- External data: Effective temperature 2838±50 K and Baraffe evolutionary tracks used to test dynamical mass  
  > "while the observed effective temperature of 2M0444 is 2838 $\pm$ 50 K (cite: Luhman04-1)" (Discussion, Substellar Mass of 2M0444) [from (cite: Luhman04-1); (cite: Baraffe15-1)]

## Processing

### Calibration

- pipeline or manual: Standard ALMA pipeline, then self-calibration  
  > "The data calibration followed the standard ALMA pipeline procedures." (2 Observation and data reduction)
- casa version: CASA 6.5.4.9  
  > "we applied self-calibration using version 6.5.4.9 of the Common Astronomy Software Application (CASA) package" (2 Observation and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10% in Band 7  
  > "The accuracy of the flux calibration in Band 7 is estimated to be 10$\%$ (cite: Francis2020)." (2 Observation and data reduction)
- self calibration: 5 phase-only iterations on short-baseline data; joint 8 phase-only + 1 phase-amplitude iterations  
  > "we combined both long- and short-baseline data for joint self-calibration, performing eight phase-only iterations followed by one phase-amplitude iteration." (2 Observation and data reduction)

### Imaging

- task: tclean  
  > "`TCLEAN` was used to generate continuum and line images, with continuum subtraction applied beforehand." (2 Observation and data reduction)
- deconvolver: multiscale  
  > "we employed the `tclean` task in CASA with multiscale deconvolver, using scales of \[0, 8, 15, 30\] pixels" (3.3 Fitting of the visibilities for the continuum)
- weighting robust: Continuum robust 0.5; 12CO and 13CO robust 2  
  > "A Briggs robust parameter of 0.5 was selected for the continuum image to balance sensitivity and resolution, while a robust parameter of 2 was used for the $^{12}$CO and $^{13}$CO emission lines" (2 Observation and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Central circular mask 0.3" radius, cleaned to 1σ  
  > "iterating down to a $1\sigma$ threshold with a central circular mask of $0.3{^{\prime\prime}}$ in radius" (3.3 Fitting of the visibilities for the continuum)
- multiscale scales: [0, 8, 15, 30] pixels  
  > "using scales of \[0, 8, 15, 30\] pixels" (3.3 Fitting of the visibilities for the continuum)
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Applied before extracting physical properties  
  > "Before extracting physical properties from the images, a primary beam correction was applied." (2 Observation and data reduction)
- array combination: C43-8 and C43-5 combined for joint self-calibration and imaging  
  > "we combined both long- and short-baseline data for joint self-calibration" (2 Observation and data reduction)
- smoothing: _not stated_
- final beam: 12CO robust 2: 0.071x0.054"  
  > "| 345.796 | $^{12}$CO | 3–2 | 2 | 0.071$\times$0.054 | 7.20 |" (Table (line summary))
- final rms: 12CO rms = 2 mJy/beam  
  > "with a s/n exceeding 3$\sigma$ (rms = 2 mJy/beam)" (3.1 Disk rotation in the image plane)

### Inherited from earlier work

- 12CO visibility fitting follows procedure of Kurtovic & Pinilla for MHO 6  
  > "We fit the visibilities of the $^{12}$CO emission following a similar procedure to that of (cite: kurtovic2024) in MHO 6." (3.2 Fitting of the visibilities for the 12CO line emission) [from (cite: kurtovic2024)]
- Bootstrap uncertainty approach for frank profile  
  > "we followed a bootstrapping approach similar to (cite: Carvalho2024)" (3.3 Fitting of the visibilities for the continuum) [from (cite: Carvalho2024)]
- Rout defined by 2σ contour, similar to Andrews 2021  
  > "$R_\mathrm{out}$ is defined by the $2\sigma$ contour in the robust 0.5 image (similarly to (cite: Andrews2021))" (3.3 Fitting of the visibilities for the continuum) [from (cite: Andrews2021)]
- Optical depth procedure  
  > "we applied the procedure outlined by (cite: Huang2018), which was also used in (cite: Facchini19)" (Temperature and optical depth profile) [from (cite: Huang2018); (cite: Facchini19)]
- Planet mass from gap via empirical relations  
  > "(cite: Lodato2019) established empirical relationships between gap properties and the maximum potential planet mass responsible for carving the gap" (4.3 Maximum possible planet mass carving the gap) [from (cite: Lodato2019)]

### Not stated but needed to reproduce (our reading)

- Self-calibration solution intervals for each iteration
- Line-free channels and continuum-subtraction method/order
- Cell size and image size
- Flagged channel ranges and reference antenna
- Priors ranges and parameter list for 12CO two-layer visibility model and code used
- galario prior bounds and initial positions
- Keplerian mask parameters and EDDY settings (radial range, fitting method)
- Which 12CO velocity channels/cleaning thresholds for the moment maps
- Frank-fit gap/ring location extraction method

## Analysis recipe

1. **Calibrate and self-calibrate data**: Standard pipeline, align executions with fixvis/fixplanets, phase self-cal on short baselines then joint, applied to continuum and line  
  > "we aligned the emission peaks using the tasks FIXVIS and FIXPLANETS." (2 Observation and data reduction)
   - software: CASA
   - parameter: S/N of emission peak improved from 42 to 114  
  > "we improved the signal-to-noise (s/n) of the emission peak by 271$\%$ (from 42 to 114)" (2 Observation and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Dynamical mass from image-plane moment maps**: bettermoments moment 0/1 maps, EDDY fit iterated, Keplerian mask, final EDDY fit on masked moment 1  
  > "The final refinement of the central mass was then achieved using `EDDY` once more, applying the Keplerian mask to the moment 1 map." (3.1 Disk rotation in the image plane)
   - software: EDDY, bettermoments
   - parameter: Inclination fixed at 49.9 deg  
  > "The inclination was fixed using the value derived in Section [3.3](#sec:p10_cont_fit) which is 49.9 deg" (3.1 Disk rotation in the image plane)
   - assumption: Distance ~140 pc  
  > "we assumed a distance of $\sim$ 140 pc (cite: Galli18-2)" (3.1 Disk rotation in the image plane)
   - fitting: Iterated EDDY fits until parameters converged; corner plot of posteriors  
  > "We performed multiple iterations of `EDDY` until the parameters converged." (3.1 Disk rotation in the image plane)
   - validation: Compared with visibility-plane mass  
  > "We derived the dynamical mass of 2M0444 using two different methodologies: fitting in the image plane with `EDDY`(Section [3.1](#sec:p10_SLAM)) with a value of $0.043^{+0.003}_{-0.002}\,M_{\odot}$" (Discussion, Substellar Mass of 2M0444)
3. **Dynamical mass from 12CO visibility fitting**: Channel-by-channel visibilities, 30 channels, two emitting layers (front and back), MCMC  
  > "The brightness model cube considered two emitting layers to recreate the $^{12}$CO emission: A front and back emitting layer, each one with its own independent height and temperature profile." (3.2 Fitting of the visibilities for the 12CO line emission)
   - parameter: 192 walkers, flat priors, converged after ~10^4 steps, then 10^4 more  
  > "with 192 walkers (equal to eight times the number of free parameters), and a flat prior for all the parameters" (3.2 Fitting of the visibilities for the 12CO line emission)
   - assumption: Back layer not farther from midplane than front layer  
  > "The only additional condition imposed on the model was that the back layer could not be at a larger distance from the midplane than the front layer." (3.2 Fitting of the visibilities for the 12CO line emission)
   - fitting: MCMC, flat priors; uncertainties from walker dispersion (3σ for mass)  
  > "The uncertainty for each parameter is measured from the dispersion of the walkers." (3.2 Fitting of the visibilities for the 12CO line emission)
   - validation: Residual image after model subtraction; geometry consistent with continuum  
  > "we find consistent solutions of inclination and position angle to those from the continuum" (3.2 Fitting of the visibilities for the 12CO line emission)
4. **Parametric continuum fit for geometry**: After uvsub of external source, galario fit of central Gaussian plus Gaussian ring, MCMC  
  > "we applied the code `galario`(cite: Tazzari2018) to perform a parametric fit which was solely aimed at retrieving the disk’s geometrical parameters" (3.3 Fitting of the visibilities for the continuum)
   - software: galario, emcee, CASA
   - parameter: 100 walkers, 10000 steps  
  > "results of the `galario` fit run using 100 walkers and 10000 steps" (galario fit)
   - fitting: chi2 minimisation, emcee MCMC, uniform priors, f0 and f1 sampled logarithmically  
  > "Uniform priors were employed, with the intensity normalization factors $f0$ and $f1$ sampled logarithmically." (3.3 Fitting of the visibilities for the continuum)
   - validation: _not stated_
5. **Non-parametric radial profile**: frank Fourier-Bessel fit of deprojected visibilities with galario geometry; 500-run bootstrap for uncertainties  
  > "We ran the `frank` fit 500 times, randomly varying the geometrical parameters ($i$, PA, $\Delta$RA, and $\Delta$Dec)" (3.3 Fitting of the visibilities for the continuum)
   - software: frankenstein
   - parameter: alpha=1.20, w_smooth=1e-3, N=400, Rmax=4 Rout  
  > "we selected conservative values of $\alpha=1.20$ and $w_\mathrm{smooth}=10^{-3}$, along with $N = 400$ and $R_\mathrm{max} = 4\,R_\mathrm{out}$" (3.3 Fitting of the visibilities for the continuum)
   - fitting: Gaussian-process regularised Fourier-Bessel series; 1 deg sigma on i and PA, 1/3 beam major axis on offsets  
  > "We used a standard deviation of 1 deg for $i$ and PA, and 1/3 of the synthesized beam’s major axis for the positional offsets" (3.3 Fitting of the visibilities for the continuum)
   - validation: Model comparison: Gaussian vs Gaussian+ring with AIC and BIC; frank log-likelihood difference  
  > "The Gaussian+Ring model is strongly favored by the AIC ($\Delta\text{AIC}=-24.4$)" (Statistical comparison of dust substructure models)
6. **Measure gas and dust disk sizes**: Cumulative flux radii R68, R90, R95 from image plane and visibility fits  
  > "We defined the radii $R_{68}$, $R_{90}$, and $R_{95}$ as the distances within which 68%, 90%, and 95% of the total flux is enclosed, respectively." (3.4 Size of disk: gas vs dust)
   - fitting: _not stated_
   - validation: Compared image plane vs visibility plane  
  > "with gas-to-dust size ratios ranging from 6 to 8 in the visibilities, compared to 2 to 2.7 in the image plane" (Size of disk: gas vs dust)
7. **Estimate disk mass, optical depth and planet mass**: Disk mass from continuum flux; optical depth from temperature profile; planet mass from Hill radius with gap width and k=4-8  
  > "where k is a constant ranging from 4 to 8 depending on the disk parameters" (Discussion, Maximum possible planet mass carving the gap)
   - parameter: flaring angle 0.02  
  > "$\varphi$ represents the flaring angle, which we set to 0.02" (Temperature and optical depth profile)
   - assumption: kappa=2 cm2/g, T~12 K, dust-to-gas 100 for disk mass  
  > "dust opacity of $\kappa\nu = 2$ cm$^2$/g, temperature of $\sim$12 K, and a dust-to-gas ratio of 100" (4.1 Substellar Mass of 2M0444)
   - assumption: Low viscosity (alpha<0.01), one planet per gap  
  > "the disks have low viscosity (with $\alpha < 0.01$)" (4.3 Maximum possible planet mass carving the gap)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 6.5.4.9: Self-calibration, fixvis/fixplanets, uvsub, tclean imaging  
  > "we applied self-calibration using version 6.5.4.9 of the Common Astronomy Software Application (CASA) package" (2 Observation and data reduction)
- **EDDY** : Dynamical mass from moment-1 map  
  > "To derive the dynamical mass of the central object, we employed `EDDY`(Extracting Disk Dynamics)" (3.1 Disk rotation in the image plane)
- **bettermoments** : Moment maps and Keplerian masking  
  > "We used the `bettermoments` package (cite: bettermoments) to generate zeroth and first-order moment maps" (3.1 Disk rotation in the image plane)
- **galario** : Parametric visibility fit  
  > "First, we applied the code `galario`(cite: Tazzari2018) to perform a parametric fit" (3.3 Fitting of the visibilities for the continuum)
- **emcee** : MCMC sampling of galario fit  
  > "sampling the parameter space with an MCMC approach using the `emcee` package" (3.3 Fitting of the visibilities for the continuum)
- **frankenstein** : Non-parametric radial brightness profile  
  > "we used the obtained geometrical parameters as inputs for a second visibility fitting with the code `frankenstein`" (3.3 Fitting of the visibilities for the continuum)
- **astropy** : Listed in Software section  
  > "astropy (cite: astropy1; astropy2), EDDY (cite: eddy), (cite: bettermoments), frankenstein (cite: Jennings2022)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dynamical mass (EDDY) | 0.043 | +0.003/-0.002 | Msun | 2 | This process yielded a central mass for 2M0444 of 0.043$^{+0.003}_{-0.002}$M$_{\odot}$ |
| Dynamical mass (12CO visibility fit) | 0.092 | +0.019/-0.007 (3σ) | Msun | 3 | we obtain $M_\star=0.092_{-0.007}^{+0.019}$ M$_{\odot}$ |
| Disk inclination (galario) | 49.9 | ±0.5 | deg | 4 | /  Inclination   /       $49.9_{-0.5}^{+0.5}$ deg       / |
| Gap radius | 98.1 | +4.2/-8.4 | mas | 5 | our best fit shows a gap and a ring at 98.1$^{+4.2}_{-8.4}$ mas ($\sim$14 au) and 116.0$^{+4.2}_{-4.8}$ mas ($\sim$16 au), respectively |
| Ring radius | 116.0 | +4.2/-4.8 | mas | 5 | 116.0$^{+4.2}_{-4.8}$ mas ($\sim$16 au), respectively |
| Gap-to-dust R68 ratio of gas/dust (visibility plane) | 7.7 (R68), 7.8 (R90), 6.3 (R95) | not stated | dimensionless | 6 | /  / Ratio / 7.7 / 7.8 / 6.3 / |
| Dust R68 image plane | 0.121 | ±0.001 | arcsec | 6 | / plane / Dust / 0.121 $\pm$ 0.001 / 0.144 $\pm$ 0.002 / 0.149 $\pm$ 0.002 / |
| Planet mass range | 0.3-7.7 | not stated | Earth masses | 7 | the planet able to carve that gap would have an estimated mass between 0.3 and 7.7 M$_{\oplus}$, assuming k values of 4 and 8 |
| Disk mass | 1.36 | ±0.2 | MJup | 7 | we derived a similar but slightly higher disk mass of $1.36 \pm 0.2$ M$_{\text{Jup}}$ |
| Delta AIC (ring vs Gaussian) | -24.4 | not stated | dimensionless | 5 | The Gaussian+Ring model is strongly favored by the AIC ($\Delta\text{AIC}=-24.4$) |
| Delta BIC (ring vs Gaussian) | +11.8 | not stated | dimensionless | 5 | The BIC favors the simpler Gaussian model ($\Delta\text{BIC}=+11.8$) |

## Qualitative findings

- Dust disk is optically thick within ~0.05" (~7 au)  
  > "The optical depth profile indicates that the disk is optically thick within a radius of ${\sim}$0.05 arcsec (${\sim}$7 au)." (Temperature and optical depth profile)

## Claim tuples

- H: Does 12CO trace a Keplerian disk allowing a dynamical mass for 2M0444? | E: EDDY moment-map fit and 12CO visibility-plane model | R: 0.043 (EDDY) and 0.092 Msun (visibility) | F: Mass 0.043-0.092 Msun; may be near the substellar boundary | **partially**
- H: Is there annular dust substructure in the disk? | E: galario and frank visibility fits, AIC/BIC comparison | R: Faint ring near 0.11" recovered; AIC favours ring, BIC does not; CLEAN image shows none | F: Tentative gap and ring | **partially**
- H: Is radial drift efficient in the BD disk? | E: Gas and dust R68/R90/R95 from visibilities | R: Gas-to-dust size ratio 6.3-7.8 | F: Consistent with efficient radial drift and a dust trap | **supported**
- H: What planet could carve the gap? | E: Hill-radius relation with gap width and k=4-8 | R: 0.3-7.7 Earth masses | F: Earth-like planet consistent with core accretion | **partially**

## Reasoning

- Why this data: C43-5 added to recover extended emission filtered by C43-8  
  > "C43-5 complemented it by recovering any extended emission filtered out in C43-8." (2 Observation and data reduction)
- Why this method: frank retrieves sub-beam features without a parametric model  
  > "The primary advantage of `frank` is its ability to retrieve sub-beam resolution features in the dust continuum emission while leveraging the full data sensitivity" (3.3 Fitting of the visibilities for the continuum)
- Alternative: Symmetric disk with sharp outer edge could also produce negative visibilities; non-axisymmetric structure possible  
  > "although a symmetric disk with a sharp outer edge could also produce negative visibilities." (3.3 Fitting of the visibilities for the continuum)
- How they decided it was enough: _not stated_
- Limitation (authors): Low S/N; EDDY ignores beam convolution; visibility mass inconsistent with Teff  
  > "EDDY` does not take the beam convolution into account, which may result in smaller stellar mass" (4.1 Substellar Mass of 2M0444)
- Limitation (authors): Substructure tentative; BIC prefers no ring  
  > "the evidence for the additional substructure is less compelling under BIC" (Statistical comparison of dust substructure models)
- Caveat (inferred, ours): Two dynamical masses differ by factor >2; no resolution of which is correct
- Caveat (inferred, ours): Ring evidence is model-dependent and absent in CLEAN image
- Caveat (inferred, ours): Planet mass from Hill radius relies on wide k range and low viscosity assumption
- Caveat (inferred, ours): Gas/dust size ratio from different methods differ strongly (2-2.7 vs 6-8)

## Reproducibility

- Data public (paper): ALMA acknowledgement of project 2023.1.00158.S; no explicit public statement  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA$\#$2023.1.00158.S" (Summary)
- Products in archive: _not stated_
- Code: Keplerian mask code at GitHub link given; no analysis scripts released  
  > "<https://github.com/richteague/keplerian_mask>" (footnote)
- Missing: Self-cal solution intervals
- Missing: 12CO visibility model parameterisation and code
- Missing: Line-free channels and cell/image size
- Missing: galario prior bounds
- Data volume (inferred): ~100-300 GB raw for four executions across C43-8 and C43-5 in Band 7
- Score (inferred): 3/5, Data are from a single project and main steps are described with key numbers, but many imaging, self-cal and fitting settings are missing and the 12CO model code is not named.
- Rediscovery candidate: no, Recipe lacks self-calibration and 12CO model details and the main substructure result is tentative and model-dependent.

## Links

- Method: Jennings et al. 2020 (cite: Jennings2020) (frankenstein method)
- Method: Tazzari et al. 2018 (cite: Tazzari2018) (galario code)
- Method: Teague 2019 (cite: eddy) (EDDY)
- Method: Kurtovic & Pinilla 2024 (cite: kurtovic2024) (12CO visibility fitting)
- Companion: Ricci et al. 2014 (cite: Riccietal14-1) (earlier disk mass of 2M0444)
- Companion: Testi et al. 2016 (cite: Testi2016) (earlier lower-resolution dust size)

## Checks

```json
{
 "quotes": 91,
 "quotes_ok": 91,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 94,
  "stated": 72,
  "rate": 0.766
 },
 "evidence_ok": true
}
```

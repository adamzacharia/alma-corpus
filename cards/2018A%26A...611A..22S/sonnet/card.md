# Jekyll &amp; Hyde: quiescence and extreme obscuration in a pair of massive galaxies 1.5 Gyr after the Big Bang

`2018A&A...611A..22S` | Astronomy and Astrophysics 2018 | first author: Schreiber, C. | arXiv: 1709.03505 | DOI: 10.1051/0004-6361/201731917

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What produces the sub-millimeter emission near the quiescent galaxy ZF-COSMOS-20115 (Jekyll): obscured star formation in it, or a separate galaxy (Hyde)? What are the properties of each?  
  > "We show here that this sub-millimeter emission is produced by another massive ( M ∗ ∼ 10 11 M ⊙ ), compact ( r 1/2 = 0.67 ± 0.14 kpc) and extremely obscured galaxy ( A V ∼ 3.5)" (abstract)
- Target **Jekyll (ZF-COSMOS-20115) and Hyde**: coordinates Jekyll (HST position): RA 150.06146 deg, Dec 2.378683 deg  
  > "The pointing was centered on the Hubble Space Telescope ( HST ) position of Jekyll : α = 150.06146 ◦ , δ = 2.378683 ◦ ." (2.1 Overview of ALMA observations and flux extraction); "We found the systemic redshift of [C ii] is z = 3.7087 ± 0.0004, while the Balmer lines of Jekyll are at z = 3.7174 ± 0.0009." (2.5 Rotating disk model); z/distance Jekyll z=3.7174±0.0009; Hyde z=3.7087±0.0004  
  > "The pointing was centered on the Hubble Space Telescope ( HST ) position of Jekyll : α = 150.06146 ◦ , δ = 2.378683 ◦ ." (2.1 Overview of ALMA observations and flux extraction); "We found the systemic redshift of [C ii] is z = 3.7087 ± 0.0004, while the Balmer lines of Jekyll are at z = 3.7174 ± 0.0009." (2.5 Rotating disk model); distance from Jekyll: MOSFIRE Balmer lines; Hyde: ALMA [C II]  
  > "The pointing was centered on the Hubble Space Telescope ( HST ) position of Jekyll : α = 150.06146 ◦ , δ = 2.378683 ◦ ." (2.1 Overview of ALMA observations and flux extraction); "We found the systemic redshift of [C ii] is z = 3.7087 ± 0.0004, while the Balmer lines of Jekyll are at z = 3.7174 ± 0.0009." (2.5 Rotating disk model)

## Data provenance

- ALMA projects: 2015.A.00026.S, 2013.1.01292.S, 2013.1.00034.S, 2013.1.00118.S, 2013.1.00151.S, 2015.1.00137.S, 2015.1.00379.S, 2015.1.01074.S
- bands: Band 8 (403 GHz, 744 µm) new data; Band 7 (338 GHz, 888 µm) earlier data  
  > "The new ALMA data were obtained in band 8 with a single spectral tuning at 403 GHz (744 µm)" (2.1 Overview of ALMA observations and flux extraction)
- frequencies and spectral setup: Line cube 401.2–404.7 GHz (centered on [CII]); continuum-only cube 413.0–416.5 GHz  
  > "the first centered on the expected frequency of the [C ii] line (401.2 to 404.7 GHz), and the second at higher frequencies which only measure the continuum level (413.0 to 416.5 GHz)" (2.1 Overview of ALMA observations and flux extraction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.52×0.42″ (natural weighting); Band 7: 1.1×0.7″  
  > "with a beam size of 0.52×0.42 ′′ (natural weighting)" (2.1 Overview of ALMA observations and flux extraction)
- max recoverable scale: _not stated_
- sensitivity: Band 7 noise 0.25 mJy (1σ)  
  > "the resulting noise level reached 0.25 mJy (1σ)" (2. Dust continuum and [C ii] emission)
- time on source: 1.2 hours (Band 8); 1.5 minutes (Band 7)  
  > "The on-source observing time was 1.2" (2.1 Overview of ALMA observations and flux extraction)
- observing dates: Band 8 delivered early 2017  
  > "were delivered in early 2017 as part of the Director’s Discretionary Time (DDT) program" (2.1 Overview of ALMA observations and flux extraction)
- pi or archival as stated: _not stated_
- Line: [C II] 158 µm fine structure (1900.5369 GHz)
- Other facility **HST**: F160W imaging, de-blending and astrometry  
  > "with GALFIT (Peng et al. 2002) on the Hub- ble F160W image" (3.1 Photometry)
- Other facility **Spitzer IRAC/MIPS, Herschel, SCUBA2**: near-/far-IR photometry  
  > "The far-IR photometry toward the Jekyll + Hyde system was re-extracted from Spitzer MIPS and Herschel imaging" (2.3 Fluxes and spatial profiles)
- Other facility **Keck MOSFIRE**: spectrum of Jekyll (Balmer lines)  
  > "Bottom left: MOSFIRE spectrum of Jekyll (binned to 6.5 Å resolution)." (Figure 1 caption)
- External data: SCUBA2 450 µm flux of the system  
  > "The SCUBA2 450 µm flux was taken from Simpson et al. (2017)" (2.3 Fluxes and spatial profiles) [from Simpson et al. (2017)]
- External data: Jekyll HST size and mass profile (r1/2)  
  > "From Straatman et al. (2015), 68% confidence interval." (Table 1) [from Straatman et al. (2015)]
- External data: Jekyll Balmer-line redshift and MOSFIRE spectrum  
  > "In Glazebrook et al. (2017) we reported the spectroscopic identification of the most distant quiescent galaxy known to date" (1. Introduction) [from Glazebrook et al. (2017)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: No cleaning; dirty images and dirty beam used as PSF  
  > "We did not perform any cleaning on these cubes, and thus used the dirty images throughout this analysis with the dirty beam as pointspread function." (2.1 Overview of ALMA observations and flux extraction)
- weighting robust: natural weighting  
  > "with a beam size of 0.52×0.42 ′′ (natural weighting)" (2.1 Overview of ALMA observations and flux extraction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum image made by masking [CII] channels, subtracted from cube  
  > "We then subtracted the continuum map from the spectral cube and fit the [C ii] emission with a rotating disk model" (2.1 Overview of ALMA observations and flux extraction)
- line free channels: _not stated_
- primary beam correction: not applied for noise estimation  
  > "using the RMS of the pixels away from the source (without applying the primary-beam correction)" (2.1 Overview of ALMA observations and flux extraction)
- array combination: _not stated_
- smoothing: every three frequency channels binned  
  > "We binned the flux of every three frequency channels to eliminate correlated noise between nearby channels" (2.1 Overview of ALMA observations and flux extraction)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Far-IR photometry extraction method  
  > "following a method standard to deep fields (Elbaz et al. 2011)" (2.3 Fluxes and spatial profiles) [from Elbaz et al. 2011]
- Dust SED model (three parameters, Galliano dust library)  
  > "We modeled the 24–890 µm photometry with the simple dust model presented in Schreiber et al. (2017a)" (2.4 Far-IR photometry and modeling) [from Schreiber et al. (2017a)]
- Gas-to-dust ratio calibration  
  > "In Schreiber et al. (2016), we have calibrated the gas-to-dust ratio (δ GDR ) of our adopted dust library" (4.5.1 Estimating the efficiency) [from Schreiber et al. (2016)]
- [CII]–CO(1-0) correlation and alpha_CO  
  > "we can use the empirical [C ii]–CO(1-0) correlation derived for z = 2 galaxies in Gullberg et al. (2015) and α CO = 2" (4.5.1 Estimating the efficiency) [from Gullberg et al. (2015); Swinbank et al. 2011]

### Not stated but needed to reproduce (our reading)

- Exact CASA version and calibration (pipeline or manual) of the Band 8 and archival data
- Flux calibrator and flux-scale uncertainty
- Array configuration/baselines and spectral resolution
- Channel ranges masked as [CII] for the continuum image
- imfit initial guesses and image/cell size
- Exact selection list of the 71/76 archival COSMOS ALMA sources
- SED fit details, grid files and FAST++ version (code described only in a future paper)

## Analysis recipe

1. **Verify ALMA–HST/VISTA astrometry**: _not stated_
   - fitting: _not stated_
   - validation: local sample of six galaxies within 5′ consistent  
  > "which are consistent with the previous values thus imply no significant variation across the field" (2.2 ALMA astrometry)
2. **Fit continuum size and flux**: imfit exponential disk fit to dirty image using dirty beam as PSF (no PSF normalization); cross-checked in uv plane  
  > "We used `imfit` [2] v1.5 (Erwin 2015) to model the dust continuum emission, assuming an exponential disk profile (Hodge et al. 2016) and Gaussian noise." (2.3 Fluxes and spatial profiles)
   - software: imfit, uvmodelfit, uvmultifit
   - fitting: Uncertainties from imfit on simulated noise maps with injected source  
  > "The uncertainties were then determined from the standard deviation of the best fits among all simulated data sets." (2.3 Fluxes and spatial profiles)
   - validation: uvmodelfit/uvmultifit give similar results  
  > "and found similar results." (2.3 Fluxes and spatial profiles)
3. **Model far-IR SED**: Fit 24–890 µm photometry with Schreiber 2017a templates, chi2 grid in Tdust, 5000 perturbation realizations  
  > "Uncertainties on all parameters were then computed by randomly perturbing the photometry within the error bars and re-doing the fit 5000 times." (2.4 Far-IR photometry and modeling)
   - parameter: L_IR/L_8 fixed to 8  
  > "we fixed L IR / L 8 = 8" (2.4 Far-IR photometry and modeling)
   - assumption: Jekyll Tdust uniform 20–35 K  
  > "We considered T dust ranging from 20 K (as observed in z = 2 quiescent galaxies; Gobat et al. 2017) to 35 K" (2.4 Far-IR photometry and modeling)
   - fitting: chi2 minimization over Tdust  
  > "Varying the dust temperature, we adjusted the infrared luminosity to best fit the observed data, and chose as best fit the dust temperature leading to the smallest reduced χ [2] ." (2.4 Far-IR photometry and modeling)
   - validation: Excluding SPIRE gives similar Tdust; GN20 template rescaling gives similar L_IR  
  > "Excluding the SPIRE fluxes, which are notoriously difficult to measure, we obtained a similar T dust = 32" (2.4 Far-IR photometry and modeling)
4. **Fit [CII] kinematics**: Inclined thin rotating disk model fit to continuum-subtracted cube with Levenberg-Marquardt; errors from simulated cubes  
  > "The model best-fitting the observations was determined using a Levenberg-Marquardt minimization, assuming Gaussian statistics" (2.5 Rotating disk model)
   - software: GBKFIT
   - parameter: Disk centroid fixed to dust continuum; parameter ranges h, i, PA, I0, vsys, sigma_v, rt, vt  
  > "We fixed the centroid of the disk to that of the dust continuum, and varied the scale length" (2.5 Rotating disk model)
   - fitting: Levenberg-Marquardt  
  > "The model best-fitting the observations was determined using a Levenberg-Marquardt minimization, assuming Gaussian statistics" (2.5 Rotating disk model)
   - validation: Monte Carlo simulated cubes for confidence intervals  
  > "we created a set of simulated cubes by perturbing the best-fitting model with Gaussian noise, convolved them with the dirty beam, and applied the same fitting procedure" (2.5 Rotating disk model)
5. **De-blend optical/IR photometry**: GALFIT modeling of galaxies within 15″ on HST F160W; Hyde assumed ALMA dust profile; linear fit of models in other bands; Monte Carlo errors  
  > "we assumed instead the disk profile obtained by modeling its dust emission" (3.1 Photometry)
   - software: GALFIT
   - fitting: linear combination of models plus constant background  
  > "fit the images as a linear combination of all these models plus a constant background (fluxes were allowed to be negative)." (3.1 Photometry)
   - validation: Residuals with flux ratio fixed to 0/50/100% are poor; free-centroid fits recover ALMA position  
  > "The residuals obtained by fixing the flux ratio of Jekyll and Hyde to 0, 50 and 100% are shown in Fig. 7, and clearly show that either of these assumptions provides a poor fit" (3.1 Photometry)
6. **SED modeling of stellar population**: FAST++ grid of double-tau SFHs with BC03, Calzetti, solar metallicity, L_IR Gaussian prior; 90% intervals from delta chi2<2.71  
  > "confidence intervals were derived from the minimum and maximum values allowed in the volume of the grid with χ 2 − χ 2 min < 2.71" (3.2.2 The grid)
   - software: FAST++
   - parameter: About 2 million models; AV 0–6 mag  
  > "A total of about 2 million models were generated" (3.2.2 The grid)
   - assumption: Uniform dust screen, energy balance, no emission lines  
  > "it assumes a uniform attenuation ( _A_ V ) for the whole galaxy. This implies that dust is screening all stars uniformly, regardless of their age" (3.2.1 Description of the code and key assumptions)
   - fitting: chi2 grid  
  > "confidence intervals were derived from the minimum and maximum values allowed in the volume of the grid with χ [2] − χ [2] min [<] [2][.][71 (i.e., these are 90% confidence intervals;]" (3.2.2 The grid)
   - validation: 1000 Monte Carlo cross-check; Appendix A simulated bursty SFHs recovered 90%/95%  
  > "We found that 90% and 95% of the simulated SFHs were correctly recovered for A V = 0.5 and 3.5 mag, respectively" (Appendix A)
7. **Estimate gas mass and star-formation efficiency**: Gas mass from dust mass with gas-to-dust ratio and from [CII] luminosity with CO relation; inverse-variance average; efficiency eps_rot and eps_ff  
  > "Averaging these two independent estimates with inverse variance weighting" (4.5.1 Estimating the efficiency)
   - assumption: Solar metallicity with factor two uncertainty; alpha_CO = 2  
  > "In all the following calculations we assumed solar metallicity, with an uncertainty of a factor two." (4.5.1 Estimating the efficiency)
   - fitting: _not stated_
   - validation: two independent gas estimates agree  
  > "This mass should only include the molecular hydrogen, but it is nevertheless consistent with the dust-based value." (4.5.1 Estimating the efficiency)

## Software

- **CASA** : generating dirty spectral cubes; uvmodelfit  
  > "We generated two spectral cubes in CASA" (2.1 Overview of ALMA observations and flux extraction)
- **imfit** v1.5: continuum size/flux modeling  
  > "We used `imfit` [2] v1.5 (Erwin 2015) to model the dust continuum emission" (2.3 Fluxes and spatial profiles)
- **uvmultifit** : uv-plane cross-check  
  > "both uvmodelfit and uvmultifit (Martí-Vidal et al. 2014)" (2.3 Fluxes and spatial profiles)
- **GBKFIT** : rotating disk fit of [CII] cube  
  > "we modeled the continuum-subtracted spectral cube with an inclined thin disk model using `GBKFIT` [3] (Bekiaris et al. 2016)." (2.5 Rotating disk model)
- **GALFIT** : de-blending HST/IRAC  
  > "with GALFIT (Peng et al. 2002)" (3.1 Photometry)
- **FAST++** : SED fitting with arbitrary SFH  
  > "The photometry of both objects was modeled using FAST++" (3.2.1 Description of the code and key assumptions)
- **phy++** : most numerical analysis  
  > "Most of the numerical analysis conducted in this work has been performed using phy++" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Hyde 744 µm continuum flux | 2.31 | 0.14 | mJy | 2 | S 744 µm = 2.31 ± 0.14 mJy |
| Jekyll–Hyde projected offset | 0.426 (3.05 kpc) | 0.015″ / 0.11 kpc | arcsec | 2 | This corresponds to a projected distance of 0.426 ± 0.015 ′′, i.e., 3.05 ± 0.11 kpc. |
| Hyde dust half-light radius | 0.67 | 0.14 | kpc | 2 | At z = 3.7, this corresponds to 0.67 ± 0.14 kpc. |
| Hyde Tdust | 31 | +3/-4 | K | 3 | We found a dust temperature of T dust = 31 |
| Jekyll SFR_IR upper limit | <13 | 3σ | Msun/yr | 3 | a 3σ upper limit of SFR IR < 13 M ⊙ /yr |
| Hyde [CII] redshift | 3.7087 | 0.0004 | dimensionless | 4 | z = 3.7087 ± 0.0004 |
| Velocity offset Jekyll–Hyde | 549 | 60 | km/s | 4 | The corresponding proper velocity difference is 549 ± 60 km/s |
| [CII] line flux | 1.85 | 0.22 | Jy km/s | 4 | S [C ii] = 1.85 ± 0.22 Jy.km/s |
| L[CII] | 8.4e8 | 1.0e8 | Lsun | 4 | L [C ii] = (8.4 ± 1.0) × 10 8 L ⊙ |
| Dynamical mass of Hyde | 1.3e11 | +1.2/-0.8 | Msun | 4 | M dyn = 1.3 |
| Hyde gas mass | 3.6e10 | +4.3/-1.9 | Msun | 7 | we finally obtained a gas mass of M gas = |
| Hyde current SFR upper limit (90%) | <119 | not stated | Msun/yr | 6 | we constrained the current SFR of Hyde to be less than 119 M ⊙ /yr at 90% confidence |
| Hyde H-[4.5] colour | 5.1 | 0.8 | mag | 5 | H − [4.5] = 5.1 ± 0.8 |

## Qualitative findings

- Hyde is a separate, compact, dusty galaxy with rotating-disk [CII], not part of Jekyll  
  > "We thus conclude that Jekyll and Hyde are indeed two separate galaxies" (4.2 Hyde is a separate galaxy)

## Claim tuples

- H: The sub-mm emission comes from obscured star formation within Jekyll | E: Deep Band 8 imaging, astrometry tests, [CII] kinematics, IRAC de-blending | R: Dust is offset by 0.43″ with 10^-4 chance probability; [CII] offset by 549±60 km/s; no dust at Jekyll (SFR<13) | F: Emission is from a separate galaxy Hyde; Jekyll is truly quiescent | **supported**
- H: Hyde has quenched or is quenching | E: SED modeling, compactness, [CII]/FIR toy model | R: SFR<120 Msun/yr, compact size, low [CII]/FIR | F: Quenching is favored but ongoing star formation not excluded | **partially**
- H: Hyde has a large gas reservoir despite low SFR | E: Gas mass from dust and [CII] | R: Mgas = 3.6e10 Msun, Sigma_gas ~1e4 Msun/pc^2 | F: Low star-formation efficiency; quenching did not expel gas | **supported**

## Reasoning

- Why this data: Deeper, higher-resolution imaging centered on [CII] to find the origin of the faint offset emission and confirm redshift  
  > "we proposed to re-observe this system with better sensitivities and angular resolution, and sought to detect the [C ii] line to confirm the redshift." (2. Dust continuum and [C ii] emission)
- Why this method: _not stated_
- Alternative: Two dispersion-dominated merging components could mimic the double-horn profile; cannot be excluded without higher S/N  
  > "Ruling out this possibility would require a spectrum with a higher S / N than we have here." (4.2 Hyde is a separate galaxy)
- How they decided it was enough: _not stated_
- Limitation (authors): Dust temperature and dust mass poorly constrained; Hyde SED/SFH constraints loose; Hyde metallicity unknown  
  > "the coverage of the dust SED at high and low frequency would need to be improved." (2.4 Far-IR photometry and modeling)
- Caveat (inferred, ours): Dirty images used without deconvolution; sidelobe effects not discussed
- Caveat (inferred, ours): Toy [CII] model relies on z=0 calibration and 0.2 dex scatter
- Caveat (inferred, ours): Gas mass relies on assumed metallicity, gas-to-dust ratio and alpha_CO
- Caveat (inferred, ours): Uniform-screen SED model may bias SFH and mass

## Reproducibility

- Data public (paper): ALMA data identified by project codes; archive used for comparison sample  
  > "we have retrieved from the ALMA archive" (2.2 ALMA astrometry)
- Products in archive: _not stated_
- Code: FAST++ and gbkfit linked on GitHub; FAST++ to be described in a separate paper  
  > "4 https://github.com/cschreib/fastpp" (3.2.1 Description of the code and key assumptions)
- Missing: Calibration/CASA version
- Missing: Archival sample list and selection
- Missing: Ancillary photometry catalogs (ZFOURGE, HST, IRAC)
- Missing: imfit and GBKFIT run settings
- Data volume (inferred): ~20-50 GB for the Band 8 DDT data plus archival Band 6/7 data for the astrometry check
- Score (inferred): 5/5, ALMA data are identified and the dirty-image methods are described, but calibration details are missing and the SED analysis needs external multiwavelength data and the unreleased FAST++ description.
- Rediscovery candidate: no, The full results depend on non-ALMA photometry and a SED code; the ALMA-only part lacks calibration details.

## Links

- Method: Schreiber et al. (2017a) (dust SED model)
- Method: Bekiaris et al. (2016) (GBKFIT)
- Method: Erwin (2015) (imfit)
- Companion: Glazebrook et al. (2017) (discovery of Jekyll)
- Companion: Simpson et al. (2017) (concurrent analysis of the same system)
- Related: ZFOURGE
- Related: COSMOS
- Related: MOSEL

## Checks

```json
{
 "quotes": 91,
 "quotes_ok": 91,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 8,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 91,
  "stated": 62,
  "rate": 0.681
 },
 "evidence_ok": true
}
```

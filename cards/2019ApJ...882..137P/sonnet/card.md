# The ALMA Spectroscopic Survey in the HUDF: the Molecular Gas Content of Galaxies and Tensions with IllustrisTNG and the Santa Cruz SAM

`2019ApJ...882..137P` | The Astrophysical Journal 2019 | first author: Popping, Gergö | arXiv: 1903.09158 | DOI: 10.3847/1538-4357/ab30f2

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: high_z_galaxies, cosmology
- Question: Do IllustrisTNG and the Santa Cruz SAM reproduce the H2 content of galaxies measured by ASPECS (H2 mass vs stellar mass, H2 mass function, H2 cosmic density), after accounting for sensitivity limits and field-to-field variance?  
  > "We will specifically try to quantify the success of these different galaxy formation evolution models in reproducing the observations by accounting for sensitivity limits, field-to-field variance effects, and systematic theoretical uncertainties." (Introduction)
- Target **Hubble Ultra Deep Field (ASPECS 3 mm survey area)**: coordinates _not stated_; z/distance CO lines at z<0.37, 1.01<z<1.74, z>2.01  
  > "The 3 mm campaign discussed here scanned a contiguous area of $\sim4.6$ arcmin$^2$ in the frequency range 84–115 GHz" (3 ASPECS survey overview); distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00324.L
- bands: 3 mm scan, 84–115 GHz (the 1.2 mm scan is not used here)  
  > "The 3 mm campaign discussed here scanned a contiguous area of $\sim4.6$ arcmin$^2$ in the frequency range 84–115 GHz" (3 ASPECS survey overview)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: line-search cube beam ≈1.75'' x 1.49''; spectra extracted from cube smoothed to ~3.5''  
  > "The line-search is performed in a cube with a synthesized beam of $\approx 1.75'' \times 1.49''$." (3 ASPECS survey overview)
- max recoverable scale: _not stated_
- sensitivity: 5-sigma luminosity floor ~2e9 K km/s pc^2 (200 km/s line width) at z>1  
  > "of $\sim 2\times10^9$ K km s$^{-1}$ pc$^2$ (assuming a line width of 200 km s$^{-2}$) at virtually any redshift $z>1$" (3 ASPECS survey overview)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=1-0 to 4-3 (via redshift coverage) (not stated)
- Other facility **MUSE HUDF survey**: redshift catalog used to identify lines  
  > "in particular the redshift catalog provided by the MUSE HUDF survey ((cite: Bacon2017), (cite: Inami2017))" (3 ASPECS survey overview)
- Other facility **COLDZ (JVLA)**: comparison CO(1-0) H2 mass function and cosmic density  
  > "we compare the model predictions to the results from ASPECS, as well as the results from the COLDZ survey at $z\sim2.6$" (4.2 The evolution of the H2 mass function)
- External data: ASPECS line detections, luminosities, volumes, mass functions and cosmic density  
  > "Details of this analysis are presented in (cite: Decarli2019) and (cite: Boogaard2019)." (3 ASPECS survey overview) [from (cite: Decarli2019); (cite: Gonzalez2019); (cite: Boogaard2019)]
- External data: z=0 observed H2 masses of galaxies  
  > "the predictions are compared to observed H$_2$ masses of galaxies from (cite: Saintonge2017) at $z=0$" (4.1.2 Mocked results) [from (cite: Saintonge2017)]
- External data: PHIBBS compilation of H2 masses at higher z  
  > "a compilation presented in (cite: Tacconi2018) as a part of the PHIBBS (IRAM Plateau de Bure HIgh-z Blue Sequence Survey) survey" (4.1.2 Mocked results) [from (cite: Tacconi2018)]
- External data: z=0 H2 mass functions  
  > "The mass functions at $z=0$ are compared to observations taken from from (cite: Keres2003), (cite: Obreschkow2009), (cite: Boselli2014), and (cite: Saintonge2017)." (4.2 The evolution of the H2 mass function) [from Keres2003; Obreschkow2009; Boselli2014; Saintonge2017]
- Simulation/model as data: IllustrisTNG TNG100 (~100 Mpc)^3 simulation and Santa Cruz SAM on Bolshoi merger trees, with H2 recipes GK, K13, BR  
  > "In this paper we use and analyze the TNG100 simulation, a $\sim$(100 Mpc$)^3$ cosmological volume simulated with the code AREPO" (2.1 IllustrisTNG)

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

- SC SAM model parameters same as SPT15 except alpha_rh=2.6 and kappa_AGN=3.0e-3  
  > "The model parameters adopted in this work are the same as in SPT15, except for $\alpha_{\rm rh} = 2.6$" (2.2 Santa Cruz semi-analytic model) [from SPT15 (cite: Somerville2015)]
- ASPECS line identification, luminosities and CO SLED treatment  
  > "The line luminosities are then transformed into corresponding CO(1-0) luminosities based on the (cite: Daddi2015) CO SLED template" (3 ASPECS survey overview) [from (cite: Decarli2019); (cite: Daddi2015)]
- SC SAM metallicity and H2 floors  
  > "Following PST14 and SPT15, we adopt a metallicity floor of $Z=10^{-3}\,$Z$_\odot$ and a floor for the fraction of molecular hydrogen of $f_{\rm mol}=10^{-4}$." (2.5 Metallicity and molecular hydrogen fraction floor in the SC SAM) [from PST14 and SPT15]

### Not stated but needed to reproduce (our reading)

- Exact ASPECS catalog values (line luminosities, redshifts, mass-function points) are taken from companion papers; they are not tabulated here
- Code and settings used to post-process TNG100 (cell selection, subhalo handling) are not given
- How mass functions were binned and how the 1000 random cones were placed, beyond the stated number
- Cosmology parameters are only said to be consistent with Planck 2016
- Stellar-mass cuts and the SFR main-sequence selection at z=0 are only partly specified

## Analysis recipe

1. **Compute H2 fractions for model galaxies**: Apply the GK (main), K13 and BR H2 partitioning recipes to TNG100 gas cells and to SC SAM annuli  
  > "In this paper we present predictions for the H$_2$ properties of galaxies by adopting three different molecular hydrogen fraction recipes." (2.3 Molecular hydrogen fraction recipes)
   - software: AREPO, SC SAM
   - parameter: TNG100 f_H=0.76; T_SF=1000 K; Sigma_SFR,MW=0.004 Msun/yr/kpc^2  
  > "we simply assume a hydrogen fraction for the gas cells of $f_{\rm H} = 0.76$." (2.1.1 Gas surface density)
   - assumption: Dust abundance D_MW = Z/Zsun  
  > "is assumed to be equal to the gas-phase metallicity expressed in solar units, i.e., $D_{\rm MW} = Z/Z_\odot$" (2.1.1 Dust)
   - fitting: _not stated_
   - validation: Compared the three recipes with each other; differences minimal  
  > "Given the minimal deviations in the medians between the different H$_2$ partitioning recipes, we will show from now on only predictions by the GK partitioning method" (4.1.1 Inherent results)
2. **Define galaxy H2 mass and apply the ASPECS selection**: Use 'Grav' and 3.5 arcsec apertures ('In2Rad' at z=0); apply an ASPECS CO sensitivity cut for 200 km/s lines  
  > "The second only accounts for the H$_2$ mass of cells that are within a circular aperture with a diameter corresponding to 3.5 arcsec on the sky" (2.4 The H2 mass of a galaxy in IllustrisTNG)
   - parameter: ASPECS sensitive to H2 ~1e9 Msun at z=0.29 and ~1e10, 2e10, 3e10 Msun at z≈1.43, 2.61, 3.8  
  > "ASPECS is sensitive to sources with an H$_2$ mass of $\sim 10^9\rm\rm{M}_\odot$ at $z=0.29$ and $\sim 10^{10},\,2\times 10^{10},\,$and $3\times10^{10}\,\rm{M}_\odot$" (4.1.2 Mocked results)
   - assumption: alpha_CO = 3.6 Msun/(K km/s pc^2); line width 200 km/s  
  > "we adopt the same CO excitation conditions and CO–to–H$_2$ conversion factor as ASPECS, $\alpha_{\rm CO} =
    3.6\,\rm{M}_\odot/(\rm{K}\,\rm{km/s}\,\rm{pc}^{2})$, and assume a CO line-width of 200 km/s." (Footnote 2)
   - fitting: _not stated_
   - validation: _not stated_
3. **Quantify field-to-field variance**: Compute mass function and cosmic density in 1000 random cones matching the ASPECS volume at each redshift  
  > "in 1000 randomly selected cones through the simulated volume that capture a volume corresponding to the actual volume probed by ASPECS at the given redshifts" (4.2.1 Field-to-field variance effects on the H2 mass function)
   - fitting: _not stated_
   - validation: _not stated_
4. **Test alternative alpha_CO values**: Redo comparisons with alpha_CO = 2.0 and 0.8  
  > "We show the H$_2$ mass of galaxies as a function of stellar mass when varying the CO–to–H$_2$ conversion factor" (5.1.2 The CO–to–H2 conversion factor and CO excitation conditions)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **AREPO** : moving-mesh code underlying IllustrisTNG  
  > "IllustrisTNG is a cosmological, large-scale gravity+magnetohydrodynamical simulation based on the moving mesh code AREPO" (1 Introduction)
- **ROCKSTAR** : halo finding in the Bolshoi merger trees for the SC SAM  
  > "Dark matter haloes were identified using the ROCKSTAR algorithm" (2.2 Santa Cruz semi-analytic model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| H2 mass of z>1 galaxies predicted vs observed (alpha_CO=3.6) | factor 2–3 lower | not stated | dimensionless | 2 | the H$_2$ mass of $z>1$ galaxies predicted by the models as a function of their stellar mass is a factor of 2–3 lower than observed |
| Reduction in H2 cosmic density from applying ASPECS limit at z=1 | factor of three | not stated | dimensionless | 2 | the H$_2$ cosmic density is a factor of three (an order of magnitude) lower at $z=1$ ($z>2$) |
| alpha_CO range alleviating tension | 2.0–0.8 | not stated | Msun/(K km/s pc^2) | 4 | can be alleviated by adopting a CO–to–H$_2$ conversion factor in the range $\alpha_{\rm CO} =
2.0 - 0.8\,\rm{M}_\odot/(\rm{K}\,\rm{km/s}\,\rm{pc}^{2})$ |
| Fraction of TNG realizations reproducing ASPECS rho(H2) at z~1.43 | up to 2.5% | not stated | percent | 3 | only up to 2.5% of the realizations drawn from IllustrisTNG reproduce the ASPECS observations |

## Qualitative findings

- Systematic uncertainty between the H2 partitioning recipes is minimal  
  > "The systematic uncertainty between different H$_2$ partitioning recipes for predictions of the H$_2$ mass of galaxies, the H$_2$ mass function, and the H$_2$ cosmic density of the Universe is minimal." (6 Summary & Conclusions)

## Claim tuples

- H: Do the models produce enough H2 per stellar mass at z>1? | E: Compare model H2–M* relations with ASPECS and PHIBBS using the ASPECS selection | R: Models are 2–3 times lower; many detections lie outside the 2-sigma scatter | F: Models underpredict H2 at z>1 for alpha_CO=3.6 | **supported**
- H: Do the models reproduce the cosmic H2 density once selection and variance are included? | E: Cosmic density in 1000 ASPECS-volume cones with sensitivity limits | R: TNG in tension; SC SAM only just agrees | F: Predicted cosmic densities appear too low | **partially**
- H: Can a different alpha_CO resolve the tension? | E: Repeat comparisons with alpha_CO=2.0 and 0.8 | R: Better agreement, but 0.8 is unrealistic and overpredicts z=0 H2 | F: alpha_CO~2 plausibly alleviates much of the tension | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Model predictions allow estimating selection functions and field-to-field variance for ASPECS  
  > "Theoretical models can be used to estimate limitations in the observations (e.g., field-to-field variance, selection functions)" (1 Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): ASPECS covers only 4.6 arcmin^2, so field-to-field variance is large  
  > "it is by far not large enough to overcome significant uncertainties due to field-to-field variance" (5.2 Field-to-field variance and selection effects for ASPECS)
- Caveat (inferred, ours): Fixed 200 km/s line width simplifies the selection function
- Caveat (inferred, ours): Fixed f_H=0.76 and Jeans-length surface densities in TNG are crude
- Caveat (inferred, ours): Observed ASPECS H2 values depend on assumed CO SLED and alpha_CO, so the tension is partly observational

## Reproducibility

- Data public (paper): ALMA data cited by program ID; no public-release statement  
  > "This Paper makes use of the ALMA data ADS/JAO.ALMA#2016.1.00324.L." (Acknowledgments)
- Products in archive: _not stated_
- Missing: ASPECS catalogs from companion papers (some were 'submitted')
- Missing: TNG post-processing code
- Missing: SC SAM code
- Data volume (inferred): Small if using published ASPECS catalogs; TNG100 snapshots are large (hundreds of GB to TB)
- Score (inferred): 3/5, Models and ASPECS catalog quantities are described but depend on companion papers and unreleased code.
- Rediscovery candidate: no, Main results come from simulations and an SAM, not from reprocessing ALMA data, and no code is released.

## Links

- Method: (cite: Decarli2019) (ASPECS 3 mm line search results, luminosity functions and volumes)
- Method: (cite: Gonzalez2019) (ASPECS line catalog, fidelity and completeness)
- Companion: (cite: Boogaard2019) (ASPECS line identification and counterparts)
- Companion: (cite: Diemer2019) (Detailed z=0 comparison of TNG H2 with observations)
- Related: ASPECS
- Related: COLDZ
- Related: PHIBBS
- Related: IllustrisTNG
- Related: MUSE HUDF

## Checks

```json
{
 "quotes": 40,
 "quotes_ok": 40,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 30,
  "rate": 0.411
 },
 "evidence_ok": true
}
```

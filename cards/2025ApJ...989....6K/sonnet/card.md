# The ALMA Survey of Gas Evolution of PROtoplanetary Disks (AGE-PRO). VI. Comparison of Dust Evolution Models to AGE-PRO Observations

`2025ApJ...989....6K` | The Astrophysical Journal 2025 | first author: Kurtovic, Nicolás T. | arXiv: 2506.10740 | DOI: 10.3847/1538-4357/add1d0

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks
- Question: Can dust evolution models (with or without dust traps, viscous gas evolution) reproduce the gas masses, 1.3 mm fluxes, sizes and spectral indices of the AGE-PRO disk sample, and do the data favor dust traps?  
  > "aiming to investigate if any observational trend can favor or exclude the presence of dust traps." (abstract)
- Target **AGE-PRO sample (30 disks in Ophiuchus, Lupus, Upper Sco)**: coordinates _not stated_; z/distance distances from inverse Gaia DR3 parallax  
  > "has allowed for the measurement of the gas mass and size in a sample of 30 disks three different star forming regions (SFRs)" (1 Introduction); distance from Gaia DR3 (cite: gaia2021edr3)  
  > "has allowed for the measurement of the gas mass and size in a sample of 30 disks three different star forming regions (SFRs)" (1 Introduction)

## Data provenance

- ALMA projects: 2021.1.00128.L
- bands: Band 6 (1.3 mm) and Band 7 (1.05 mm)  
  > "The dual-band setup of the AGE-PRO observations (Band 6 and Band 7 at 1.3-1.05 mm)" (3.4 Spectral index)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: average 0.25'' (1.3 mm setup) and 0.8'' (1.05 mm setup) as stated  
  > "The AGE-PRO observations have an average angular resolution of $0.25''$ and $0.8''$ in the 1.3 mm and 1.05 mm setups" (Appendix)
- max recoverable scale: _not stated_
- sensitivity: about 25 uJy/beam  
  > "normalized to match a sensitivity of $25\,\mu\text{Jy}/\text{beam}$, comparable to AGE-PRO" (Appendix)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **Gaia DR3**: parallax distances to the stars  
  > "measured as the inverse of the parallax from Gaia DR3" (3.2 Dust mass comparison)
- External data: AGE-PRO gas masses  
  > "When comparing against $M_{\rm gas}$ derived from (cite: AGEPRO_V_gasmasses)" (3.1 Gas mass evolution) [from (cite: AGEPRO_V_gasmasses)]
- External data: AGE-PRO dust masses and millimeter fluxes  
  > "The dust content of the AGE-PRO disks was calculated directly from the measured millimeter fluxes, and they are presented in (cite: AGEPRO_I_overview)" (3.2 Dust mass comparison) [from (cite: AGEPRO_I_overview); (cite: AGEPRO_II_Ophiuchus); (cite: AGEPRO_III_Lupus); (cite: AGEPRO_IV_UpperSco)]
- External data: AGE-PRO dust disk sizes from visibility modeling  
  > "the AGE-PRO disk sizes were obtained using visibility modeling (cite: AGEPRO_X_dust_disks)" (2 Dust model) [from (cite: AGEPRO_X_dust_disks)]
- External data: Stellar masses and ages of the sources  
  > "The full discussion about the estimation of $M_\star$ and age is given in (cite: AGEPRO_I_overview)" (3 Results) [from (cite: AGEPRO_I_overview)]
- Simulation/model as data: Grid of DustPy models (M*=0.25-1.0 Msun, Mdisk/M*=0.01/0.05/0.1, rc=15-120 au, Agap=0/1/4, alpha0=1e-4/1e-3, eps0=0.01/0.05), 3 groups of 144 disks saved at 9 ages, with RADMC-3D at 5 ages  
  > "Each of these three groups has 144 disks, which result from choosing the different $M_\star$, $M_{\text{disk}}$, $R_{\rm c}$, and $A_{\rm gap}$." (2.4 Numerical grid)

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

- AGE-PRO stellar mass and age estimates  
  > "we refer the reader to that work for a detailed description." (3 Results) [from (cite: AGEPRO_I_overview)]
- Dust mass opacity and temperature convention (kappa=2.3 (nu/230GHz)^0.4 cm2/g, T=20 K)  
  > "as in (cite: andrews2013). For the temperature, a constant $T=20\,$K is used for consistency with the literature (cite: Ansdell2016)." (3.2 Dust mass comparison) [from (cite: andrews2013); (cite: Ansdell2016)]
- Disk radius containing 90% of flux measured as in AGE-PRO  
  > "We calculated the $R_{90\%,cont}$ from the synthetic observations similarly to the AGE-PRO observations (cite: AGEPRO_XI_gas_disk_sizes)." (Appendix) [from (cite: AGEPRO_XI_gas_disk_sizes)]

### Not stated but needed to reproduce (our reading)

- Numerical AGE-PRO observed values (fluxes, radii, gas masses, spectral indices per source) are not tabulated; they must be taken from companion papers
- Stellar-mass to model matching of observed sources and any tolerance on how a source is deemed consistent with a model
- Exact RADMC-3D inclination/distance settings and flux scaling of images to observed distance
- Procedure used to determine total flux and R90 from the model images in the main comparison
- Model snapshot data are not released

## Analysis recipe

1. **Simulate gas and dust evolution**: 1D DustPy with Lynden-Bell self-similar initial profile, alpha-bump traps, stellar irradiation temperature, run to 10 Myr  
  > "we used the 1D dust evolution code `Dustpy`" (2 Dust model)
   - software: DustPy
   - parameter: rin=5 au, rout=500 au, nr=250; mass grid 1e-12 to 3e6 g, nm=134; vfrag=10 m/s; rho_s=1.6 g/cm3  
  > "The standard radial grid of the simulations goes from $r_\textrm{in} = \SI{5}{au}$ to $r_\textrm{out} = \SI{500}{au}$ with $n_r = 250$ logarithmically spaced grid cells." (2.4 Numerical grid)
   - assumption: Constant alpha in space and time; no back-reaction, photoevaporation or MHD winds; static traps  
  > "our approach does not include mechanisms such as photoevaporation or MHD winds" (2.2 Initial conditions)
   - fitting: _not stated_
   - validation: _not stated_
2. **Radiative transfer to 1.05 and 1.3 mm images**: RADMC-3D on 30 resampled grain species with Ricci2010 opacities from OpTool, vertical Gaussian hydrostatic dust, two-step Monte Carlo  
  > "First, we ran a Monte Carlo simulation to obtain the dust temperature for every grain species, using $n_\textrm{phot} = 10^7$ photon packages." (2.5 Radiative Transfer)
   - software: RADMC-3D, OpTool
   - parameter: images with nphot=2e5, isotropic scattering; ages 0.5, 1, 2, 5, 10 Myr; 19440 models  
  > "This implies a total of 19440 radiative transfer models ($5\times3888$)." (2.5 Radiative Transfer)
   - assumption: Dust composition 10% silicate, 20% carbon, 30% water ice, 40% vacuum  
  > "10% Silicate (cite: Draine2003), 20% Carbon (cite: Zubko1996), 30% water ice (cite: warren&brandt08), and 40% vacuum." (2.5 Radiative Transfer)
   - fitting: _not stated_
   - validation: Scattering variations verified to be well below 10% of total flux  
  > "we verified the flux variations were well below 10% of the total flux." (2.5 Radiative Transfer)
3. **Compare models with AGE-PRO observables**: Compare Mgas, Mpebble vs Mdust, 1.3 mm flux, R90 and spectral index of models to AGE-PRO by age group  
  > "The Ophiuchus sources are compared to our simulations at 0.5 Myr. The Lupus sources are compared to the simulations at 1 Myr and 2 Myr." (3 Results)
   - parameter: Mpebble = mass in grains 0.1 mm-10 cm; R90 = radius containing 90% of flux; alpha_mm from B6 and B7 fluxes  
  > "measured by adding the mass content in particles of sizes ranging from $0.1$ mm to $10$ cm" (3.2 Dust mass comparison)
   - assumption: Optically thin emission, T=20 K for observed dust masses  
  > "it is assumed that the emission is optically thin" (3.2 Dust mass comparison)
   - fitting: _not stated_
   - validation: Synthetic observations with beam convolution and noise tested R90 recovery, robust for disks larger than about three beams  
  > "proves robust for bright disks which are larger than approximately three times the angular resolution of the image" (Appendix)

## Software

- **DustPy** 0.5.6: gas and dust evolution  
  > "Version 0.5.6 was used for this work." (footnote 1)
- **RADMC-3D** : radiative transfer to produce continuum images  
  > "we used the radiative transfer code `RADMC-3D`" (2 Dust model)
- **OpTool** : dust opacities  
  > "To obtain the dust opacities, we use the code `OpTool`" (2.5 Radiative Transfer)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total DustPy snapshots | 3888 | not stated | snapshots | 1 | thus resulting in 3888 different snapshots of the disks evolution. |
| Spectral index range in Upper Sco | 1.9-3.2 | not stated | dimensionless | 3 | A large dispersion in the values of spectral indices is also observed in Upper Sco, ranging between 1.9-3.2 |
| Observed Mgas spread in Ophiuchus | ~3 orders of magnitude | not stated | dex | 3 | the measured $M_{\rm gas}$ from observations spans $\sim3$ orders of magnitude in Ophiuchus |

## Qualitative findings

- Models with weak or strong traps match observed dust masses, fluxes and sizes better than no-trap models  
  > "allows us to exclude disks with no pressure traps as the dominant population in the observations of AGE-PRO" (4.2)

## Claim tuples

- H: Viscous evolution with constant alpha explains observed gas masses | E: Compare no-trap model Mgas to AGE-PRO Mgas | R: Observed range is wider; lowest Ophiuchus masses are 2 orders below models; about half of Lupus and Upper Sco agree | F: Additional mechanisms (winds, photoevaporation, external effects) are needed | **refuted**
- H: Dust traps are needed to explain dust fluxes and sizes | E: Compare 1.3 mm flux and R90 of model grids to AGE-PRO | R: Most disks consistent with weak or strong traps | F: Traps favored at ages above 1 Myr | **supported**
- H: Spectral indices indicate unresolved traps | E: Compare alpha_mm from models and observations | R: Large spread 2-4 only reproduced with traps | F: Supports weak or strong traps | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Models were not tailored to individual disks; constant alpha; static traps; simple scattering  
  > "Simulations that are tailored to the properties of each disks will be part of a future publication." (2.3 Parameter Space)
- Caveat (inferred, ours): Comparison is qualitative, with no statistical fit
- Caveat (inferred, ours): Result depends strongly on the Ricci2010 opacity choice
- Caveat (inferred, ours): Observations only partly used as data in this paper

## Reproducibility

- Data public (paper): DustPy publicly available; ALMA data used via companion papers  
  > "`DustPy` is available on [github.com/stammler/DustPy](https://github.com/stammler/DustPy)." (footnote 1)
- Products in archive: _not stated_
- Missing: Observed AGE-PRO measurements table
- Missing: Model output files and scripts
- Missing: RADMC-3D viewing setup
- Data volume (inferred): Simulations only; observed values from companion papers (negligible)
- Score (inferred): 3/5, Model parameters and codes are well specified, but no observational data reduction is involved and the observed values and comparison are from companion papers.
- Rediscovery candidate: no, Results are mostly qualitative model-data comparisons; ALMA data reduction not performed here.

## Links

- Method: (cite: Stammler2022_Dustpy) (DustPy code)
- Method: (cite: AGEPRO_X_dust_disks) (visibility modeling of dust disks)
- Companion: (cite: AGEPRO_I_overview) (AGE-PRO overview)
- Companion: (cite: AGEPRO_V_gasmasses) (gas masses)
- Companion: (cite: AGEPRO_VII_population) (population/MHD winds analysis)
- Related: AGE-PRO

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
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 32,
  "rate": 0.444
 },
 "evidence_ok": true
}
```

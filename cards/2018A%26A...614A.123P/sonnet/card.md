# The physical and chemical structure of Sagittarius B2. III. Radiative transfer simulations of the hot core Sgr B2(M) for methyl cyanide

`2018A&A...614A.123P` | Astronomy and Astrophysics 2018 | first author: Pols, S. | arXiv: 1802.09231 | DOI: 10.1051/0004-6361/201732498

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry, milky_way_ism
- Question: Reconstruct the CH3CN abundance field, gas temperature distribution and velocity field of the hot core Sgr B2(M) by 3D radiative transfer modeling of ALMA CH3CN lines  
  > "We aim at reconstructing the CH$_3$CN abundance field and investigating the gas temperature distribution as well as the velocity field." (abstract)
- Target **Sgr B2(M)**: coordinates RA 17h47m20.157s, Dec -28d23m04.53s (J2000, phase center)  
  > "with the phase center at $\alpha(J2000)=17^\textrm{h}47^\textrm{m}20^\textrm{s}.157$, $\delta(J2000)=-28^\circ 23' 04.53\ensuremath{''}$" (2 Observations); "which has a distance of 8.34$\pm$0.16 kpc from the Sun (cite: reid2014)" (1 Introduction); z/distance Galactic center distance 8.34±0.16 kpc  
  > "with the phase center at $\alpha(J2000)=17^\textrm{h}47^\textrm{m}20^\textrm{s}.157$, $\delta(J2000)=-28^\circ 23' 04.53\ensuremath{''}$" (2 Observations); "which has a distance of 8.34$\pm$0.16 kpc from the Sun (cite: reid2014)" (1 Introduction); distance from Reid et al. 2014  
  > "with the phase center at $\alpha(J2000)=17^\textrm{h}47^\textrm{m}20^\textrm{s}.157$, $\delta(J2000)=-28^\circ 23' 04.53\ensuremath{''}$" (2 Observations); "which has a distance of 8.34$\pm$0.16 kpc from the Sun (cite: reid2014)" (1 Introduction)

## Data provenance

- ALMA projects: 2013.1.00332.S
- bands: Band 6, 211-275 GHz spectral scan  
  > "The observations were done in the spectral scan mode surveying the whole ALMA band 6 from 211 to 275 GHz." (2 Observations)
- frequencies and spectral setup: Spectral resolution 0.5-0.7 km/s across band  
  > "The achieved spectral resolution is 0.5–0.7 km s$^{-1}$ across the full frequency band." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 30 m to 650 m; 34 and 36 antennas  
  > "The configuration used 34 and 36 antennas, with extended baselines in the range between 30 m and 650 m." (2 Observations)
- angular resolution: 0.4''-0.8''; cubes restored with 0.7'' circular beam  
  > "The resulting data cubes used in this project were restored with a circular Gaussian beam of $0.7\ensuremath{''}$." (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: June 2014 and June 2015 (Cycle 2)  
  > "conducted using ALMA during its Cycle 2 in June 2014 and June 2015" (2 Observations)
- pi or archival as stated: _not stated_
- Line: CH3CN J=12-11 K=0-6 (ground state) (220.747261-220.594423 GHz)
- Line: CH3CN J=13-12 and J=14-13 K-ladders (239.137916 and 257.527384 GHz (K=0))
- Line: CH3CN v8=1 12_1-11_-1 (221.625828 GHz)
- Line: 13CH3CN J=13-12 K=0-7 (232.234188 GHz (K=0))
- External data: Physical model of Sgr B2 (dense cores, stars, HII regions) from continuum modeling  
  > "The model used in this paper is based on the three-dimensional physical model of Sgr B2 developed in Paper I." (5 The physical model) [from Schmiedeke et al. 2016 (Paper I) (cite: schmiedeke2016)]
- External data: ALMA continuum maps (242 GHz) and source list  
  > "compared with the ALMA continuum emission (black contour; from Paper II)" (3 Observational results) [from Sánchez-Monge et al. 2017 (Paper II) (cite: sanchez-monge2017a)]
- External data: CH3CN spectroscopic data (energies, frequencies, Einstein A) from CDMS and JPL  
  > "were taken from the CDMS (Cologne Database for Molecular Spectroscopy) catalog (cite: mueller2005; endres2016)" (4.1 Modeling CH3CN with RADMC-3D) [from CDMS (cite: mueller2005; endres2016); JPL (cite: picket1998)]
- External data: Collisional rate coefficients at 100 K for critical density  
  > "collisional rate coefficients at 100 K from the LAMDA (Leiden Atomic and Molecular DAtabase; (cite: schoeier2005)) database" (4.1 Modeling CH3CN with RADMC-3D) [from Schöier et al. 2005 (cite: schoeier2005)]
- External data: 12C/13C ratio ~20 at the Galactic center  
  > "studies of the isotope ratio $^{12}$C/$^{13}$C at the galactic center determined values of $\sim$20 (cite: wilson1994)" (6.7 Isotopologue) [from Wilson & Rood 1994 (cite: wilson1994)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.4.0  
  > "Calibration and imaging were performed in CASA[^1] version 4.4.0." (2 Observations)
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
- array combination: Model cubes sampled with the ALMA uv-coverage, then imaged with same parameters as the observations  
  > "In a second step, we image the synthetic data cubes with the same imaging parameters used for the observational ALMA data." (4.2 Post-processing with CASA)
- smoothing: _not stated_
- final beam: 0.7'' circular Gaussian  
  > "restored with a circular Gaussian beam of $0.7\ensuremath{''}$" (2 Observations)
- final rms: _not stated_

### Inherited from earlier work

- Calibration, observational details and imaging  
  > "Further information on the calibration, observational details and imaging can be found in Paper II." (2 Observations) [from Paper II (cite: sanchez-monge2017a)]
- Pandora framework and RADMC-3D grid/AMR setup  
  > "A detailed description of the framework Pandora and the RADMC-3D code can be found in Paper I and (cite: dullemond2012)." (4 Modeling procedure) [from Paper I (cite: schmiedeke2016)]
- Stars, HII regions and dense cores unchanged from Paper I  
  > "All other constituents of the model, i.e. stars, H II regions, dense cores, introduced in Paper I remain unchanged." (5.1 The physical model) [from Paper I (cite: schmiedeke2016)]

### Not stated but needed to reproduce (our reading)

- Pandora code availability and version
- CASA imaging parameters (weighting, robust, cleaning, cell/image size) used for the cubes
- Continuum subtraction method and line-free channels
- Dust opacity law and gas-to-dust ratio from Paper I
- Procedure/metric for judging model-observation agreement (visual only; no fit statistics)
- Exact temperature increments for gas-temperature test runs (not legible)
- Numeric values lost in conversion (temperatures, velocities)

## Analysis recipe

1. **Inspect CH3CN data and compare with continuum**: Peak intensity maps, spectra at selected positions, comparison to 242 GHz continuum  
  > "The middle panels of Fig. [1](#fig:observations) show the Sgr B2(M) peak intensity maps of three CH$_3$CN lines compared with the ALMA continuum emission" (3 Observational results)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Build 3D model with CH3CN abundance and velocity fields**: Superposition of modified Plummer cores plus 'molecular centers' with local abundance factors; density-weighted core velocities; turbulent plus thermal line width  
  > "the molecular density $n(\mbox{CH$_3$CN})_j$ in a cell $j$ is given by" (5.2 Molecular density and velocity field)
   - software: Pandora
   - parameter: Each core described by 10 parameters (position, dz, scales, exponent, H2 and CH3CN central density, velocity)  
  > "Each core and molecular center is described by 10 parameters" (5.3 Parametrization of the molecular density field)
   - assumption: Molecular centers have low H2 density so continuum is unchanged  
  > "These molecular centers are diffuse in dust (H$_2$ density), in order to make sure that the continuum remains unchanged" (5.3 Parametrization of the molecular density field)
   - fitting: Manual iterative adjustment of model parameters; no sampler  
  > "This cycle is iterated to increase the consistency of the simulated images with the observational maps." (4.2 Post-processing with CASA)
   - validation: 13CH3CN morphology checked for opacity effects  
  > "The same morphology is retrieved for the isotopologue than for the main species." (5.3 Parametrization of the molecular density field)
3. **Radiative transfer: dust temperature and LTE line emission**: RADMC-3D with AMR grid, Monte Carlo dust temperature, LTE level populations, Tgas = Tdust  
  > "(ii) the gas temperature equals the dust temperature, which is a valid assumption in high-density regions like those found towards Sgr B2(M)." (4.1 Modeling CH3CN with RADMC-3D)
   - software: RADMC-3D, Pandora
   - parameter: Cubic grid 1 pc side, max density difference between cells 10%, min cell 100 au, ~10^7 cells  
  > "This configuration results into a minimum cell size of 100 au and roughly $10^{7}$ final cells." (4.1 Modeling CH3CN with RADMC-3D)
   - assumption: LTE valid as critical density ~1e6 cm-3 versus 4e7-5e8 cm-3  
  > "For all transitions the critical density is on the order of $\sim$$10^{6}$ cm$^{-3}$." (4.1 Modeling CH3CN with RADMC-3D)
   - fitting: _not stated_
   - validation: _not stated_
4. **Post-process model cubes to ALMA observables**: Sample simulated cubes with ALMA uv-coverage and image in CASA  
  > "The routine uses the *uv*-coverage of the ALMA observations to sample the simulated data cubes." (4.2 Post-processing with CASA)
   - software: CASA
   - fitting: _not stated_
   - validation: Visual comparison of moment-0 maps, radial profiles and spectra  
  > "the post-processed synthetic data can be (visually) compared to the observational data searching for deviations" (4.2 Post-processing with CASA)
5. **Test gas temperature with vibrationally excited line and central-region absorption**: Compare v8=1 transition with model; run models with raised gas temperature; XCLASS fit of central absorption  
  > "we produce different models in which the gas temperature is increased compared to the dust temperature" (6.3 Temperature distribution)
   - software: RADMC-3D, XCLASS
   - fitting: _not stated_
   - validation: _not stated_
6. **Isotopologue check**: Model 13CH3CN with 12C/13C = 20 and compare moment maps and spectra  
  > "We used an isotopologue ratio of $^{12}$CH$_3$CN/$^{13}$CH$_3$CN=20 in order to obtain a fit of the isotopologue transitions." (6.7 Isotopologue)
   - software: RADMC-3D
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **Pandora** : 3D radiative transfer toolbox for model setup  
  > "We use the radiative transfer tool box Pandora (presented in Paper I)" (4 Modeling procedure)
- **RADMC-3D** : Dust temperature and line radiative transfer  
  > "which in one of its implementations can use the radiative transfer code RADMC-3D to model the CH$_3$CN line transitions" (4 Modeling procedure)
- **CASA** 4.4.0: Calibration, imaging, and post-processing of simulated cubes  
  > "Calibration and imaging were performed in CASA[^1] version 4.4.0." (2 Observations)
- **XCLASS** : Identify blending lines; fit central absorption spectrum  
  > "The blending lines were identified using the software package XCLASS ( cite : moeller2017 )" (6.2 Spectra of the main isotopologue)
- **MIRIAD** : Original Pandora post-processing (replaced by CASA here)  
  > "In the original version of Pandora the post-processing is done with the software package MIRIAD." (Footnote 2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Relative CH3CN abundance range, north | 4e-11 to 2e-8 (average 1.1e-9) | not stated | relative to H2 | 3 | For the northern region the relative abundance ranges from 4$\times 10^{-11}$ to 2$\times 10^{-8}$ with an averaged value of 1.1$\times 10^{-9}$. |
| Relative CH3CN abundance range, south | 2e-10 to 5e-7 (average 9.0e-8) | not stated | relative to H2 | 3 | In the southern region the relative abundance ranges from 2$\times 10^{-10}$ to 5$\times 10^{-7}$ with an averaged value of 9.0$\times 10^{-8}$. |
| Power-law exponent of abundance vs H2 density | -0.92 | not stated | dimensionless | 3 | The relative abundance of CH$_3$CN decreases with increasing density according to a power law with an exponent of $-0.92$. |
| Isotopologue ratio 12CH3CN/13CH3CN adopted | 20 | not stated | dimensionless | 6 | We used an isotopologue ratio of $^{12}$CH$_3$CN/$^{13}$CH$_3$CN=20 |
| Critical density of CH3CN J=12-11 | ~1e6 | not stated | cm^-3 | 3 | For all transitions the critical density is on the order of $\sim$$10^{6}$ cm$^{-3}$. |
| Central continuum brightness temperature | about 180 K | not stated | K | 1 | which at the depicted frequency is about 180 K |

## Qualitative findings

- CH3CN emission is more extended than continuum and peaks away from continuum cores; abundance is lower at centers of dense hot cores  
  > "we find that the relative abundance of CH$_3$CN is lower at the center of the very dense and hot cores" (abstract)
- Velocity gradient from north (blue-shifted) to south (red-shifted)  
  > "Southern regions are clearly red-shifted with respect to the northern regions." (6.5 Core velocities and turbulent line width)
- Central absorption is caused by bright dust continuum, not HII regions; model fails to reproduce the central spectra  
  > "the physical model presented in this paper is not able to reproduce the complex spectra at the center of Sgr B2(M)." (6.6 CH3CN features at the central region)

## Claim tuples

- H: Can the CH3CN emission be reproduced with a Plummer-core abundance field on the Paper I model? | E: RADMC-3D LTE modeling with added molecular centers, compared in moment maps and spectra | R: General morphology and low-K lines reproduced; higher K lines blended or underestimated | F: Morphology reproduced by superposed Plummer-like cores with molecular centers | **supported**
- H: Is the gas temperature equal to the dust temperature? | E: Compared v8=1 line with models having raised gas temperature | R: Vibrationally excited line underestimated in some cores | F: Gas temperature is partly underestimated, not drastically | **partially**
- H: Does CH3CN abundance correlate with density and temperature? | E: Pixel histograms of abundance versus H2 density and temperature | R: Abundance decreases with density (power law -0.92) and temperature | F: Chemical processes destroy CH3CN in the densest, hottest regions | **supported**
- H: Can the central absorption be modeled? | E: Tested envelope and shell models plus XCLASS fit | R: No model reproduced all features | F: Central temperature distribution or spherical symmetry assumption likely inadequate | **refuted**

## Reasoning

- Why this data: _not stated_
- Why this method: Account for line emission using a physical model from continuum, with uv-sampled comparison to ALMA  
  > "This ensures that the post-processed files filter out and recover the same emission and spatial scales detectable in the observations." (4.2 Post-processing with CASA)
- Alternative: Envelope and shell CH3CN models for central absorption were tried and rejected  
  > "the model with a CH$_3$CN abundance of $10^{-7}$ in the envelope produces also absorption features in the northern and southern regions" (6.6 CH3CN features at the central region)
- How they decided it was enough: _not stated_
- Limitation (authors): Molecular centers are not unique nor necessarily real  
  > "there is no unique set of MCs that can reproduce the observations." (Footnote 4)
- Limitation (authors): Line blending not modeled  
  > "Taking the blending into account would require detailed radiative transfer modeling of all species, which is way beyond the scope of this paper." (6.2 Spectra of the main isotopologue)
- Caveat (inferred, ours): Manual visual fitting without uncertainties or goodness-of-fit
- Caveat (inferred, ours): Abundances degenerate with the assumed H2 density model and Tgas=Tdust
- Caveat (inferred, ours): LTE assumed; radiative pumping possible
- Caveat (inferred, ours): Spherical symmetric cores; non-unique molecular centers

## Reproducibility

- Data public (paper): ALMA project 2013.1.00332.S acknowledged as data source  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00332.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Pandora code and version
- Missing: Imaging parameters from Paper II
- Missing: Full Paper I model details
- Missing: Several numeric values lost in the text
- Data volume (inferred): Large (full band 6 spectral scan, hundreds of GB raw); only selected cubes needed
- Score (inferred): 3/5, Data public and model parameters tabulated, but Pandora and imaging details are inherited or not provided, and fitting is manual.
- Rediscovery candidate: no, Recipe depends on unreleased Pandora code and manual visual tuning.

## Links

- Method: Schmiedeke et al. 2016 (cite: schmiedeke2016) (Pandora and physical model (Paper I))
- Method: Sánchez-Monge et al. 2017 (cite: sanchez-monge2017a) (ALMA calibration, imaging, continuum (Paper II))
- Companion: Sánchez-Monge et al. 2017 (cite: sanchez-monge2017a) (Continuum of same ALMA data)
- Related: Sgr B2(N) modeling (future work)

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
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
  "facts": 84,
  "stated": 46,
  "rate": 0.548
 },
 "evidence_ok": true
}
```

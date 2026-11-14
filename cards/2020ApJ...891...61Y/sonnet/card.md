# Constraining the Infalling Envelope Models of Embedded Protostars: BHR 71 and Its Hot Corino

`2020ApJ...891...61Y` | The Astrophysical Journal 2020 | first author: Yang, Yao-Lun | arXiv: 2002.01478 | DOI: 10.3847/1538-4357/ab7201

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: Can a TSC infalling envelope model (3D non-LTE radiative transfer) reproduce the infall signatures in optically thick lines toward BHR 71 IRS1, and what do the COM emission reveal about the inner region (hot corino, rotation)?  
  > "In this study, ALMA data are used to constrain the infall kinematics toward BHR 71, and survey the emission of COMs." (Introduction)
- Target **BHR 71 IRS1**: coordinates RA 12h01m36.4988s, Dec -65d08m49.3819s  
  > "BHR 71 is a Bok globule near the Southern Coalsack at 200 pc" (Introduction); "12$^{\rm h}$01$^{\rm m}$36s4988 $\pm$0s0001" (Table 2); z/distance 200 pc  
  > "BHR 71 is a Bok globule near the Southern Coalsack at 200 pc" (Introduction); "12$^{\rm h}$01$^{\rm m}$36s4988 $\pm$0s0001" (Table 2); distance from Seidensticker & Schmidt-Kaler 1989; Straizys et al. 1994  
  > "BHR 71 is a Bok globule near the Southern Coalsack at 200 pc" (Introduction); "12$^{\rm h}$01$^{\rm m}$36s4988 $\pm$0s0001" (Table 2)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 7  
  > "by ALMA with 45 12-m antennas and the Band 7 receiver in the C40-4 configuration" (2 Observations)
- frequencies and spectral setup: Four spectral windows of 1920 channels; three of 234.38 MHz (0.122 MHz resolution), H13CN window 468.75 MHz (0.244 MHz)  
  > "The ALMA Correlator was configured to have four spectral windows, each with 1920 channels." (2 Observations); "while the H$^{13}$CN$J = 4\rightarrow 3$ window has 468.75 MHz ($\sim$400 km s$^{-1}$) and 0.244 MHz (0.2 km s$^{-1}$) resolution." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-4  
  > "the Band 7 receiver in the C40-4 configuration" (2 Observations)
- baselines: projected 12.1-631.3 m  
  > "The minimum and maximum projected baselines were 12.1 m and 631.3 m, respectively" (2 Observations)
- angular resolution: 0.39" x 0.27" (78x54 au)  
  > "The resulting synthesized beam is 0.39$''$$\times$0.27$''$, corresponding to 78$\times$54 au at the distance of BHR 71 (200 pc)." (2.1 Data Reduction)
- max recoverable scale: ~3"  
  > "with a maximum recoverable scale of $\sim$3$''$, most of the extended emission is resolved out." (3.1 Continuum)
- sensitivity: Continuum rms 0.904 mJy/beam; line rms 13, 14, 12, 8 mJy/beam  
  > "the root-mean-square (RMS) noise reaches 0.904 mJy beam$^{-1}$ for the continuum." (2.1 Data Reduction)
- time on source: _not stated_
- observing dates: 2016 November 18  
  > "on November 18 2016 by ALMA" (2 Observations)
- pi or archival as stated: PI: Y.-L. Yang  
  > "Project 2016.0.00391S (PI: Y.-L. Yang)" (2 Observations)
- Line: HCN J=4-3 (354.505473 GHz)
- Line: HCO+ J=4-3 (356.734242 GHz)
- Line: CS J=7-6 (342.882857 GHz)
- Line: H13CN J=4-3 (345.339756 GHz)
- Other facility **Herschel**: Far-infrared spectra constraining the Y17 envelope model  
  > "using primarily the *Herschel* spectra along with archival *Spitzer* spectra and photometry" (Introduction)
- Other facility **APEX**: Archival HCO+ J=3-2 single-dish spectrum for comparison  
  > "compared with the archival APEX observation, which has a 23$''$3 beam" (6.5 Comparison to the Single-dish Observations)
- External data: Best-fit TSC envelope continuum model of BHR 71 (Y17): age, sound speed, rotation, inclination 130 deg, cavity  
  > "The main parameters for the Y17 model of the TSC envelope are sound speed, rotational speed, and age, which are 0.37 km s$^{-1}$, 5${} \times 10^{-13}$ rad s$^{-1}$, and 34 000 years, respectively." (4.2.2 The Radiative Transfer Model) [from Yang et al. 2017 (cite: 2017ApJ...835..259Y)]
- External data: Source velocity -4.45 km/s from NH3 spectra  
  > "The source velocity is $-$4.45 km s$^{-1}$, measured from the NH$_{3}$ spectra in (cite: 1997ApJ...476..781B)." (3.2.1 Intensity Maps) [from (cite: 1997ApJ...476..781B)]
- External data: Turbulence velocity 0.34 km/s and T=13 K from ammonia  
  > "we decrease the turbulence velocity from 0.34 km s$^{-1}$, derived in Y17 based on the ammonia observations by (cite: 1995MNRAS.276.1067B)" (4.3.2 Turbulence Velocity) [from (cite: 1995MNRAS.276.1067B)]
- External data: Spectroscopic line data from CDMS and JPL  
  > "The spectroscopic data are taken from the Cologne Database of Molecular Spectroscopy (CDMS;" (5.2 Line Identification) [from (cite: 2001A&A...370L..49M; 1998JQSRT..60..883P)]
- External data: Dust opacity at 356 GHz, 1.86 cm2/g  
  > "$\kappa_{\text{356\,GHz}}$ is the dust opacity at 356 GHz, 1.86 cm$^{2}$ g$^{-1}$" (3.1 Continuum) [from Ossenkopf & Henning 1994 (cite: 1994A&A...291..943O)]

## Processing

### Calibration

- pipeline or manual: ALMA Pipeline plus further self-calibration  
  > "The data were reduced by the ALMA Pipeline, version 38366 with the Common Astronomy Software Applications (CASA) version 4.7.0-1" (2.1 Data Reduction)
- casa version: 4.7.0-1 (pipeline), 4.7.2 (self-cal), 5.1.1 (imaging)  
  > "We further performed self-calibration with the CASA version 4.7.2, and the imaging was performed with CASA version 5.1.1." (2.1 Data Reduction)
- pipeline version: 38366  
  > "ALMA Pipeline, version 38366" (2.1 Data Reduction)
- archive products used as is: _not stated_
- flux calibrator: J1107-4449  
  > "The flux calibration source was J1107$-$4449, which has a flux uncertainty of 10%." (2 Observations)
- flux scale uncertainty: 10%  
  > "The calibration uncertainty is 10%." (2.1 Data Reduction)
- self calibration: Phase (solint inf to int) and amplitude (inf); S/N 222 to 819; applied to continuum and lines  
  > "For the phase calibration, we gradually reduce the solution interval from `‘inf’` to `‘int’` to ensure the quality of the calibration solution." (2.1 Data Reduction); "The S/N of the continuum source increases from 222 to 819 after the self-calibration." (2.1 Data Reduction)

### Imaging

- task: tclean (CASA 5.1.1)  
  > "We perform the imaging with CASA version 5.1.1 to use the `tclean` task" (2.1 Data Reduction)
- deconvolver: Högbom  
  > "Using the “Högbom” method for deconvolution" (2.1 Data Reduction)
- weighting robust: briggs, robust = 0.5  
  > "the “briggs” weighting with a robust parameter of 0.5" (2.1 Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: auto-thresh mask; threshold 45 mJy (3x pipeline rms); mask resolution 0.5"  
  > "we use the “auto-thresh” method for selecting the source emission for deconvolutions in the `tclean` process with a flux threshold of 45 mJy" (2.1 Data Reduction)
- multiscale scales: _not stated_
- continuum subtraction: Image-plane with imcontsub (continuum kept in cubes during cleaning)  
  > "The lowest flux in the spectra should approximate the continuum emission, which is removed in the image plane using the CASA `imcontsub` task." (2.1 Data Reduction)
- line free channels: Visually selected; continuum from 11% of channels (876 of 7680)  
  > "The continuum comes from 11% of channels (876 of 7680) after the flagging." (2.1 Data Reduction)
- primary beam correction: Applied to continuum and line cubes  
  > "Then the primary beam correction applies to the image cubes for both the continuum and lines." (2.1 Data Reduction)
- array combination: _not stated_
- smoothing: COM spectra smoothed to 1 km/s  
  > "smoothed to 1 km s$^{-1}$ to optimize the line detectability" (5 Complex Organic Molecules)
- final beam: 0.39" x 0.27"  
  > "The resulting synthesized beam is 0.39$''$$\times$0.27$''$" (2.1 Data Reduction)
- final rms: Line rms 13, 14, 12, 8 mJy/beam (HCN, HCO+, CS, H13CN)  
  > "The RMS noise reaches 13 mJy beam$^{-1}$, 14 mJy beam$^{-1}$, 12 mJy beam$^{-1}$, and 8 mJy beam$^{-1}$" (2.1 Data Reduction)

### Inherited from earlier work

- Keeping continuum in cubes until line imaging to avoid artifacts  
  > "similar to the procedures in (cite: 2015ApJ...814...22E)" (2.1 Data Reduction) [from Evans et al. 2015 (cite: 2015ApJ...814...22E)]
- TSC envelope model with cavities and disk, other parameters taken from best-fitting dust model  
  > "With all other parameters taken from the best-fitting dust model, the abundances of the molecules are the main free parameters in this study." (4.2.2 The Radiative Transfer Model) [from Yang et al. 2017 (cite: 2017ApJ...835..259Y)]
- Gas temperature set to dust temperature with external heating correction below 10 K  
  > "then apply an external heating correction when $T_\text{dust}<10$ K, following the model in (cite: 2004ApJ...614..252Y)." (4.2.2 The Radiative Transfer Model) [from Young et al. 2004 (cite: 2004ApJ...614..252Y)]
- Line identification criteria  
  > "To confirm identifications, we observe the following guidelines in (cite: 2005ApJ...619..914S)" (5.2 Line Identification) [from Snyder et al. 2005 (cite: 2005ApJ...619..914S)]
- Initial abundance profile parameters from chemical modeling  
  > "we set the initial parameters with the insights of the chemical modeling in (cite: 2004ApJ...617..360L)" (4.2.4 Constraining the Abundance Profile) [from Lee et al. 2004 (cite: 2004ApJ...617..360L)]

### Not stated but needed to reproduce (our reading)

- Self-calibration solution intervals beyond 'inf'/'int', number of iterations, and reference antenna
- Exact line-free channel ranges per spectral window
- Image size and cell size for tclean
- Number of clean iterations and spectral (chan) binning in cubes
- Full LIME-AID code (not released) and LIME settings (e.g., collision rate files)
- Exact simobserve/simanalyze configuration used to sample models
- XCLASS fit settings (source size, priors, optimization algorithm)
- Abundance grid values for the final best-fit selection (manual, by eye)

## Analysis recipe

1. **Measure continuum and dust mass**: 2D Gaussian fit with imfit; optically thin dust mass with mass-weighted dust temperature  
  > "fitted with a 2D Gaussian profile using the CASA `imfit` task" (3.1 Continuum)
   - software: CASA
   - parameter: kappa(356 GHz)=1.86 cm2/g; T_dust=148 K; gas-to-dust 100  
  > "we use a mass-weighted temperature of 148 K (Equation 8, (cite: 2008A&A...487..993K)) as the dust temperature" (3.1 Continuum)
   - assumption: Optically thin dust, d=200 pc, gas-to-dust ratio 100  
  > "suggesting a gas mass of 2.3$\pm$0.01 M$_{\odot}$ with a gas-to-dust ratio of 100" (3.1 Continuum)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract line spectra and identify infall signature**: Spectra from continuum-sized region (0.52"x0.39") using specflux; linear baseline fit to line-free channels; search for red-shifted absorption below continuum  
  > "We use the CASA `specflux` task to calculate the mean intensity, and fit the baseline for the second time." (4.1 The Infall Signature)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Model infall line profiles with 3D radiative transfer**: Y17 TSC envelope model; LIME non-LTE level populations; LIME-AID ray tracing with central continuum source; ALMA uv sampling with simobserve/simanalyze; parameterized abundance profiles tuned manually  
  > "We employ the Line Modeling Engine (cite: 2010A&A...523A..25B) to obtain the molecular level populations and then post-process the model with a customized ray-tracing code to include a central continuum source." (4.2.2 The Radiative Transfer Model)
   - software: LIME, LIME-AID, HYPERION, CASA
   - parameter: 50 000 LIME grid points in 30 000 au sphere, minimum scale 1 au; zero abundance in cavities  
  > "We set up the LIME model with 50 000 grid points distributed in a spherical envelope of 30 000 au according to the density profile." (4.2.2 The Radiative Transfer Model)
   - parameter: 54-model drop-function grid tested and rejected; parameterized profile with Xout, Xevap, radii, af=2, ap=-2  
  > "We explore the parameter space using 54 models" (4.2.4 Constraining the Abundance Profile)
   - assumption: Gas temperature = dust temperature above 10 K; H13CN abundance = HCN/77 initially  
  > "The abundance of H$^{13}$CN follows the abundance of HCN divided by the isotope ratio of 77" (4.2.4 Constraining the Abundance Profile)
   - fitting: Manual search by eye for best-fitting abundance profile; no sampler  
  > "Then we manually search for the best-fitting abundance profile while exploring the effect of each parameter." (4.2.4 Constraining the Abundance Profile)
   - validation: Compared with PV diagrams and offset spectra; APEX HCO+ 3-2 comparison  
  > "Figure [21](#fig:infall_pv) shows the PV diagrams of the observations and the best-fitting models." (6.1 An Observational Test of the Best-fitting Infall Kinematics)
4. **Derive envelope age and turbulence**: Grid of ages 10 000-15 000 yr compared with peak velocity difference <Δv> for CS line; turbulence lowered to 0.25 km/s  
  > "we run a grid of models whose ages ranging from 10 000 to 15 000 years with 1000 years increment" (4.3.1 The Implied Protostellar Age)
   - software: LIME-AID
   - parameter: Uncertainty threshold = spectral resolution 0.1 km/s  
  > "If we take the spectral resolution, 0.1 km s$^{-1}$ as a threshold for the uncertainty, the derived age is 12 000$\pm$2000 years." (4.3.1 The Implied Protostellar Age)
   - fitting: _not stated_
   - validation: _not stated_
5. **Identify COM lines and derive column densities**: SPLATALOGUE and XCLASS LTE modelling with CDMS/JPL data; Tex and column density fitted for species with multiple lines, otherwise Tex=100 K  
  > "For each line, we search the transitions with a maximum upper energy of 1000 K, and test if the corresponding species produces spectra consistent with the observations using XCLASS" (5.2 Line Identification)
   - software: XCLASS, SPLATALOGUE, CLASS, CASA
   - parameter: Trial Tex 100 K, line width 3.5 km/s; line fitting with Gaussians in CLASS  
  > "assuming a typical model of an excitation temperature of 100 K and a line width of 3.5 km s$^{-1}$" (5.2 Line Identification)
   - assumption: No interaction between emission of different molecules; N(H2) 1.7e23 cm-2 from envelope model  
  > "The emission of each molecule does not interact with those of others." (5.2 Line Identification)
   - fitting: XCLASS LTE spectra optimized to observations; optically thick lines excluded  
  > "We further exclude possible optically thick emission from the optimization" (5.2 Line Identification)
   - validation: Three Snyder criteria: rest frequency, frequency agreement, relative intensity  
  > "*Relative intensity*: After a transition is assigned, the relative strengths of all other transitions for the identified molecules need to match with the observation." (5.2 Line Identification)
6. **Test Keplerian disk for COM and HCN/H13CN kinematics**: Analytic Keplerian disk PV model convolved with beam; r^-2 or uniform brightness; eyeball tuning  
  > "The PV diagrmas are first tested against a simple model of a Keplerian rotating disk." (6.2 A Compact Rotational Structure Traced by COMs)
   - parameter: M=0.15 Msun, inclination 130 deg, line width 1 km/s, rin=15 au, rout=50 au  
  > "The maximum velocity in the PV diagram determines the inner radius of the disk, 15 au, while the maximum spatial extent constrains the outer radius of the disk, 50 au." (6.2 A Compact Rotational Structure Traced by COMs)
   - assumption: COM emission optically thin  
  > "Assuming that the emission of COMs is optically thin due to their low column density" (6.2 A Compact Rotational Structure Traced by COMs)
   - fitting: Optimization by eye  
  > "The optimization is done by eyes." (6.3 The Origin of the High Velocity Emission in the HCN and H13CN lines: Disks or Outflows?)
   - validation: _not stated_

## Software

- **CASA** 4.7.0-1 / 4.7.2 / 5.1.1: Pipeline calibration, self-calibration, tclean imaging, imfit, specflux, imcontsub, simobserve/simanalyze  
  > "We perform the imaging with CASA version 5.1.1 to use the `tclean` task" (2.1 Data Reduction)
- **LIME** : Non-LTE level populations  
  > "LIME iteratively solves the equation of radiation transport assuming non-local thermodynamical equilibrium (non-LTE)" (4.2.2 The Radiative Transfer Model)
- **LIME-AID** : Ray tracing with a central continuum source (developed for this study)  
  > "we developed a ray-tracing package, LIME-AID (LIME-Additional Intensity Decoder), to include continuum sources in our model" (4.2.2 The Radiative Transfer Model)
- **HYPERION** : Continuum radiative transfer used to build Y17 envelope model  
  > "Using HYPERION (cite: 2011A&A...536A..79R), Y17 constrains the parameters of the 2D axisymmetric TSC envelope model" (4.2.2 The Radiative Transfer Model)
- **XCLASS** : Line identification and LTE fitting of COMs  
  > "We use SPLATALOGUE[^1] and XCLASS (cite: 2017A&A...598A...7M) to identify the lines" (5.2 Line Identification)
- **CLASS** : Gaussian line fitting of spectra  
  > "Table [5](#tbl:line_fitting) shows the line fitting results using CLASS" (Line Fitting Results of the ALMA Spectra)
- **CGAL** 4.12: Voronoi tessellation in LIME-AID  
  > "which is efficiently and robustly constructed with the Computational Geometry Algorithms Library (cite: cgal_2018)" (4.2.2 The Radiative Transfer Model)
- **spectral-cube** : Listed in software section  
  > "spectral-cube (cite: 2016ascl.soft09017R)" (Software)
- **astropy** : Listed in software section  
  > "astropy (cite: 2013A&A...558A..33A; 2018AJ....156..123A)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum integrated flux | 1.129 | 0.006 | Jy | 1 | / Integrated flux            / 1.129 $\pm$0.006 Jy |
| Continuum deconvolved size | 349.5 x 278.9 mas (70 x 56 au) | 3.6, 2.7 mas | mas | 1 | / Semi-major axis FWHM       / 349.5$\pm$3.6 mas |
| Optically thin dust mass | 2.3e-2 | 1.2e-4 | Msun | 1 | The optically thin dust mass is 2.3${} \times 10^{-2}$$\pm$1.2${} \times 10^{-4}$ M$_{\odot}$ |
| Model-derived envelope age | 12 000 | 2000 (abstract: 3000) | years | 4 | the derived age is 12 000$\pm$2000 years. |
| Total infalling gas mass | 0.15 | 0.04 | Msun | 4 | the total infalling gas mass becomes 0.15$\pm$0.04 M$_\odot$ |
| Turbulence velocity (best fit) | 0.25 | not stated | km/s | 4 | to 0.25 km s$^{-1}$ (Figure [17](#fig:vturb)) |
| Red-shift of absorption center, HCN and HCO+ | 0.17 and 0.14 | not stated | km/s | 2 | center* at 0.17 km s$^{-1}$ and 0.14 km s$^{-1}$, respectively |
| CH3OH column density (Tex=100 K) | 2.4e18 | not stated | cm-2 | 5 | / Methanol                   / CH$_{3}$OH $v_{t}=0$        / 1                       / 100$^{a}$           / 2.4${} \times 10^{18}$ |
| CH3OCHO v=0 column density | 4.4e16 | not stated | cm-2 | 5 | / Methyl formate             / CH$_{3}$OCHO $v=0$          / 4                       / 100                 / 4.4${} \times 10^{16}$ |
| Keplerian disk radii from COM PV | 15 to 50 | not stated | au | 6 | The maximum velocity in the PV diagram determines the inner radius of the disk, 15 au, while the maximum spatial extent constrains the outer radius of the disk, 50 au. |
| Best-fit centrifugal radius | 0.6 | not stated | au | 3 | / $R_\text{cen}$                                   / Centrifugal radius                                                     / 0.6 au$^{a}$ |

## Qualitative findings

- HCO+ and HCN show red-shifted absorption below the continuum, an unambiguous infall signature.  
  > "Both the HCN $J = 4\rightarrow 3$ and HCO$^{+}$ $J = 4\rightarrow 3$ lines show red-shifted absorptions below the continuum, which is an unambiguous signature of infall." (4.1 The Infall Signature)
- CS modelling requires two evaporation zones; the model fails to reproduce H13CN and HCN high-velocity wings.  
  > "fails to reproduce the broad high velocity emission seen in the HCN $J = 4\rightarrow 3$ line" (7 Conclusions)

## Claim tuples

- H: A slowly rotating TSC infalling envelope reproduces the infall line profiles | E: 3D non-LTE radiative transfer with LIME/LIME-AID vs ALMA spectra toward the continuum | R: HCO+, CS and low-velocity HCN reproduced with age 12 000 yr | F: Inside-out collapse envelope with younger age than SED-derived explains the infall | **partially**
- H: BHR 71 IRS1 harbors a hot corino | E: Line survey and XCLASS identification of COMs | R: Eight COM species plus SO2, H2CS, HCN v2=1 within ~100 au | F: BHR 71 has a hot corino | **supported**
- H: An unresolved Keplerian disk exists in the inner 50 au | E: Compare COM PV diagrams with analytic Keplerian disk | R: 15-50 au Keplerian disk gives similar PV diagrams | F: Hint of unresolved Keplerian disk; resolution too low to constrain | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Optically thick lines viewed with a small beam against the continuum give unambiguous infall; 3D RT needed for cavities and inclination  
  > "it provides an unambiguous signature of infall." (Introduction)
- Alternative: Drop-function abundance profile rejected as too inflexible for the ALMA spectra  
  > "Our experiments suggest that the drop function fails to provide the required flexibility to model the high resolution ALMA spectra." (4.2.4 Constraining the Abundance Profile)
- How they decided it was enough: _not stated_
- Limitation (authors): Model cannot reproduce high-velocity HCN wings and H13CN; resolution cannot constrain the disk  
  > "however, our observations cannot constrain the properties of the disk." (7 Conclusions)
- Caveat (inferred, ours): Abundance profiles tuned by eye with no formal fit or posterior, so age uncertainty is only a spectral-resolution threshold
- Caveat (inferred, ours): Age 12 000 yr is driven mostly by the CS line; HCO+/HCN only bound it below 20 000 yr
- Caveat (inferred, ours): Required 12C/13C of 3 for H13CN is unphysical, indicating model inadequacy
- Caveat (inferred, ours): Single-epoch single-setting data; COM identifications blended and some tentative
- Caveat (inferred, ours): LIME-AID code not publicly released

## Reproducibility

- Data public (paper): ALMA data acknowledged by project code  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.0.00391.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: LIME-AID code
- Missing: Y17 model input files
- Missing: Exact self-calibration and flagging parameters
- Missing: Final abundance grid choices
- Data volume (inferred): ~20-50 GB raw (single Band 7 execution, 4 spws)
- Score (inferred): 4/5, Data and imaging settings mostly given, but radiative transfer code is unreleased and fits were done by eye.
- Rediscovery candidate: no, Main results depend on custom unreleased RT code and manual fitting; only the continuum and COM parts are easily redone.

## Links

- Method: Yang et al. 2017 (cite: 2017ApJ...835..259Y) (Source of the TSC envelope continuum model)
- Method: Evans et al. 2015 (cite: 2015ApJ...814...22E) (Imaging procedure and infall modeling approach)
- Method: Lee et al. 2004 (cite: 2004ApJ...617..360L) (Chemo-dynamical abundance profiles)
- Companion: Tobin et al. 2019 (cite: 2019ApJ...870...81T) (ALMA 13CO/C18O observations of BHR 71)

## Checks

```json
{
 "quotes": 101,
 "quotes_ok": 101,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2016.1.00391.S"
 ],
 "codes_printed_but_missing": [
  "2016.0.00391.S"
 ],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 96,
  "stated": 77,
  "rate": 0.802
 },
 "evidence_ok": true
}
```

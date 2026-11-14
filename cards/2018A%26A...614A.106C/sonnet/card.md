# Probing midplane CO abundance and gas temperature with DCO<SUP>+</SUP> in the protoplanetary disk around HD 169142

`2018A&A...614A.106C` | Astronomy and Astrophysics 2018 | first author: Carney, M. T. | arXiv: 1802.09280 | DOI: 10.1051/0004-6361/201732384

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Which midplane conditions (gas temperature, CO abundance) are probed by DCO+ J=3-2 emission in the HD 169142 disk, and how sensitive are the DCO+ formation pathways to them?  
  > "This work aims to understand which midplane conditions are probed by the DCO$^+$ emission in the disk around the Herbig Ae star HD 169142." (abstract)
- Target **HD 169142**: coordinates RA 18h24m29.776s, Dec -29d46m50.000s (J2000)  
  > "HD 169142 (J2000: R.A. = 18$^{\rm{h}}$24$^{\rm{m}}$29.776$^{\rm{s}}$, DEC = –29$^\circ$46$\ensuremath{'}$50.000$\ensuremath{''}$)" (2 Observations and Reduction); "Recent distance measurements by Gaia put the system at a distance of $d = 117 \pm 4$ pc (cite: Gaia2016)." (1 Introduction); z/distance 117 +/- 4 pc  
  > "HD 169142 (J2000: R.A. = 18$^{\rm{h}}$24$^{\rm{m}}$29.776$^{\rm{s}}$, DEC = –29$^\circ$46$\ensuremath{'}$50.000$\ensuremath{''}$)" (2 Observations and Reduction); "Recent distance measurements by Gaia put the system at a distance of $d = 117 \pm 4$ pc (cite: Gaia2016)." (1 Introduction); distance from Gaia (Gaia2016)  
  > "HD 169142 (J2000: R.A. = 18$^{\rm{h}}$24$^{\rm{m}}$29.776$^{\rm{s}}$, DEC = –29$^\circ$46$\ensuremath{'}$50.000$\ensuremath{''}$)" (2 Observations and Reduction); "Recent distance measurements by Gaia put the system at a distance of $d = 117 \pm 4$ pc (cite: Gaia2016)." (1 Introduction)

## Data provenance

- ALMA projects: 2013.1.00592.S
- bands: Band 6 (211–275 GHz)  
  > "was observed with ALMA in band 6 (211–275 GHz) with 35 antennas on 2015 August 30" (2 Observations and Reduction)
- frequencies and spectral setup: DCO+ 3-2 in lower sideband, 61.0 kHz (0.084 km/s) resolution; also 1.3 mm continuum, 12CO, 13CO, C18O 2-1  
  > "The DCO$^+$ $J=3-2$ line at 216.1128 GHz was observed in the lower sideband and had a frequency (velocity) resolution of 61.0 kHz (0.084 km s$^{-1}$ )." (2 Observations and Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 13 – 1445 m | 10 – 1120 kλ  
  > "Baselines | 13 – 1445 m \| 10 – 1120 k${\rm \lambda}$" (Table 1)
- angular resolution: 0.37'' x 0.23'' (PA -74.8 deg), natural weighting  
  > "Synthesized beam \[FWHM\] | $0.37\ensuremath{''} \times 0.23\ensuremath{''}$" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: rms 6 mJy/beam per channel (0.085 km/s)  
  > "rms noise \[mJy beam$^{-1}$\] | 6" (Table 1)
- time on source: _not stated_
- observing dates: 2015 August 30  
  > "Date Observed | 2015 August 30" (Table 1)
- pi or archival as stated: _not stated_
- Line: DCO+ J=3-2 (216.11258 GHz)
- Other facility **VLT/SPHERE**: J-band polarized intensity radial profile (from Pohl et al. 2017) for comparison  
  > "The polarized intensity data is from VLT/SPHERE, with the radial profile obtained after azimuthally averaging the deprojection of the $r^2$-scaled $J$-band $Q_\phi$ image" (3.1 Radial distribution of DCO+)
- External data: Fiducial DALI physical disk structure constrained by 1.3 mm continuum and 12CO, 13CO, C18O 2-1  
  > "The initial physical structure of the HD 169142 disk is adopted from (cite: Fedele2017a)" (4 Modeling DCO+ emission) [from (cite: Fedele2017a)]
- External data: VLT/SPHERE J-band polarized intensity image  
  > "normalizing to the maximum brightness of the inner ring (cite: Pohl2017)" (3.1 Radial distribution of DCO+) [from (cite: Pohl2017)]
- External data: Partition function, E_u and Sij mu^2 for DCO+  
  > "are taken from the CDMS database (cite: Muller2005)" (3.2 Column density) [from (cite: Muller2005)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.3.1  
  > "Data reduction was performed with version 4.3.1 of the Common Astronomy Software Applications (cite: McMullin2007)." (2 Observations and Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10%  
  > "Flux calibration accuracy is taken to be 10%." (Table 1)
- self calibration: Self-calibrated, continuum-subtracted CLEAN image used; details in Fedele et al. 2017a  
  > "The spectrum shown in Figure 1 was extracted from the original self-calibrated, continuum-subtracted CLEAN image." (3 Results)

### Imaging

- task: CASA CLEAN  
  > "Images were created using the CASA task CLEAN, with natural weighting for the lines to enhance sensitivity." (2 Observations and Reduction)
- deconvolver: _not stated_
- weighting robust: natural  
  > "Weighting | natural" (Table 1)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Keplerian mask in RA, Dec, velocity for M*=1.65 Msun; improved moment-0 S/N from 5 to 15  
  > "Applying the Keplerian mask improved the signal-to-noise ratio of the integrated intensity image by a factor of three, from 5 to 15." (3 Results)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.37'' x 0.23'', PA -74.8 deg  
  > "imaged at $0.37\ensuremath{''} \times 0.23\ensuremath{''}$ \[$43\times27$ AU at 117 pc\] spatial resolution, with beam P.A. = –74.8$^{\circ}$" (3 Results)
- final rms: 6 mJy/beam per channel  
  > "rms noise \[mJy beam$^{-1}$\] | 6" (Table 1)

### Inherited from earlier work

- Calibration, self-calibration and continuum subtraction done as in Fedele et al. 2017a  
  > "The data used in this work were reduced in the same manner as (cite: Fedele2017a). See their paper for further details on calibration, self-calibration, and continuum subtraction." (2 Observations and Reduction) [from (cite: Fedele2017a)]
- Keplerian masking technique  
  > "a mask in right ascension, declination, and velocity was applied to the original image cube data, following (cite: Carney2017) and (cite: Salinas2017)." (3 Results) [from (cite: Carney2017); (cite: Salinas2017)]
- Fiducial DALI disk model parameters  
  > "For a full description and table of values including the parameter ranges and best-fit parameters of their fiducial DALI model, see Section 5.2, Figure 5, and Table 2 of their paper." (4.1 Fiducial physical structure) [from (cite: Fedele2017a)]
- DCO+ CHEMNET chemical network  
  > "See Section 4.1, Table 1, and subsection 4.2.3 in their paper for a full description of the chemical network" (4.3 Parameterized models) [from (cite: Murillo2015)]
- LTE column density formula  
  > "Following the formula used by (cite: Remijan2003) and (cite: Miao1995) for optically thin emission in local thermodynamic equilibrium (LTE)" (3.2 Column density) [from (cite: Remijan2003); (cite: Miao1995)]

### Not stated but needed to reproduce (our reading)

- Calibrator names, pipeline vs manual calibration and self-cal parameters (deferred to Fedele et al. 2017a)
- Image size, cell size, clean threshold/iterations and mask for CLEAN
- Line-free channels and continuum subtraction details
- Velocity-width tolerance used in Keplerian mask
- Inclination/PA-dependent details of vis_sample use and LIME setup beyond 30000 grid points
- Full optimized DALI small-grain parameters and PAH settings are only partly tabulated
- Numerical radial profile data for model fitting; fit metric for choosing best model not given (visual comparison)

## Analysis recipe

1. **Image DCO+ and extract spectrum/moment maps**: CLEAN with natural weighting; Keplerian mask; moment 0 over 5.4–8.8 km/s; moment 1 with 3.5 sigma clip; spectrum over 1.75'' radius circle  
  > "the spectrum was extracted from the image cube after applying the Keplerian mask and integrated over the velocity range 5.4 – 8.8 km s$^{-1}$." (3 Results)
   - software: CASA
   - parameter: Keplerian mask with M = 1.65 Msun  
  > "assumed to be Keplerian around a central stellar mass of $M = 1.65 \ M_{\odot}$" (3 Results)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive radial intensity profile**: Mean intensity in azimuthally-averaged elliptical annuli (i=13 deg, PA=5 deg), 0.1'' bins; errors = std of pixels / sqrt(number of beams)  
  > "Errors are calculated as the standard deviation of the pixel intensity contained within each annulus divided by the square root of the number of beams." (3.1 Radial distribution of DCO+)
   - fitting: _not stated_
   - validation: _not stated_
3. **LTE column density and abundance**: Optically thin LTE formula for Tex=25, 50, 75 K, emitting area 3''x3'', disk mass 1.9e-2 Msun; radial version uses DALI midplane gas temperature  
  > "We explore excitation temperatures of 25, 50, and 75 K, which cover the range of expected DCO$^+$ emitting regions" (3.2 Column density)
   - assumption: Optically thin, LTE, gas mass primarily H2  
  > "Assuming the total disk mass is primarily molecular hydrogen, we can estimate the total number of H$_2$ molecules" (3.2 Column density)
   - fitting: _not stated_
   - validation: _not stated_
4. **Optimize DALI physical structure**: Modify Fedele+2017 DALI model by adding small grains in gap and beyond 83 AU, hot inner dust at 0.2 AU, PAH reduced to 1% beyond 83 AU  
  > "The PAH abundance in our optimized model was therefore set equal to the ISM abundance for $r \leq 83$ AU and set to 1% with respect to the ISM abundance for $r > 83$ AU" (7 Model details)
   - software: DALI
   - assumption: Gas-to-dust ratio 80, Rc=100 AU, Teff=8400 K  
  > "Input for DALI consists of a blackbody radiation field with $T_{\rm eff}$ = 8400 K" (4.1 Fiducial physical structure)
   - fitting: _not stated_
   - validation: SED fit maintained and CO isotopologue profiles within ~10% of previous fits  
  > "Fits to the $^{12}$CO, $^{13}$CO, and C$^{18}$O radial intensity profiles remain consistent with the previous fits from (cite: Fedele2017a) to within 10%." (7 Model details)
5. **Parameterized DCO+ chemistry**: Run steady-state DCO+ CHEMNET per (r,z) cell; alter only r>83 AU, z/r<0.1; five scenarios (high CO, low CO, cold, shadowed cold, shadowed cold + CO depletion); constant warm DCO+ abundance for 30–70 K  
  > "Five parameterized model scenarios are tested: a disk with high midplane CO abundance, a disk with low midplane CO abundance, a cold disk, a shadowed cold disk, and a shadowed cold disk including CO depletion." (4.3 Parameterized models)
   - software: DCO+ CHEMNET
   - parameter: X_HD = 1e-5; zeta_cr = 1.26e-17 s^-1  
  > "The cosmic ray ionization rate of H$_2$ is set to $\zeta_{\rm cr} = 1.26 \times 10^{-17}$ s$^{-1}$." (4.3 Parameterized models)
   - parameter: Grid search: outer boundary 100–140 AU in 10 AU steps; temperature drop 3–10 K in 1 K steps; CO depletion factors 2, 5, 10  
  > "CO depletion factors of two, five, and ten are tested, with a factor of five resulting in the right amount of DCO$^+$ emission." (4.5 CO abundance vs. gas temperature)
   - assumption: Warm abundance tuned to match 40–70 AU intensity  
  > "The constant abundance component from 30–70 K is tuned so that the model radial profile matches the intensity of the observed DCO$^+$ emission from 40–70 AU" (4.5 CO abundance vs. gas temperature)
   - fitting: Manual grid comparison of model and observed radial profiles; no sampler  
  > "Fits to the radial intensity profile of the data are used to evaluate the model parameters." (4.3 Parameterized models)
   - validation: Tested cosmic-ray ionization rate and H2 ortho/para ratio sensitivity  
  > "but our overall conclusions remain unchanged." (4.5 CO abundance vs. gas temperature)
6. **Synthetic observations of models**: LIME in LTE with 30000 grid points; vis_sample on observed uv coordinates; CLEAN natural weighting; same moment-0 range and annuli  
  > "LIME was run in LTE with 30000 grid points to create synthetic images of the DCO$^+$ $J=3-2$ transition." (4.3 Parameterized models)
   - software: LIME, vis_sample, CASA
   - fitting: _not stated_
   - validation: Channel maps and residuals compared in appendix  
  > "Channel maps in Figure 10 show the residuals of the model subtracted from the data in each velocity channel." (8 Channel maps)

## Software

- **CASA** 4.3.1: Data reduction and CLEAN imaging of data and models  
  > "Data reduction was performed with version 4.3.1 of the Common Astronomy Software Applications" (2 Observations and Reduction)
- **DALI** : Thermo-chemical disk physical structure  
  > "We use the thermo-chemical code Dust And LInes (cite: Bruderer2012; Bruderer2013) to obtain the physical disk structure." (4.1 Fiducial physical structure)
- **DCO+ CHEMNET** : Steady-state DCO+ chemistry via cold fractionation  
  > "using the steady-state, analytic chemical code (hereafter DCO+ CHEMNET) from (cite: Murillo2015)" (4.3 Parameterized models)
- **LIME** : Synthetic DCO+ 3-2 image cubes  
  > "LIME was run in LTE with 30000 grid points to create synthetic images of the DCO$^+$ $J=3-2$ transition." (4.3 Parameterized models)
- **vis_sample** : Sampling model images at observed uv coordinates  
  > "sampled in the $uv$ plane using the PYTHON `vis_sample`[^1] routine" (4.3 Parameterized models)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total integrated DCO+ 3-2 line flux | 730 | 73 | mJy km/s | 1 | Integrated flux$^{a}$ \[mJy km s$^{-1}$\] / 730$\pm$73 |
| DCO+ line FWHM | 1.76 | not stated | km/s | 1 | FWHM \[km s$^{-1}$\] / 1.76 |
| Disk-averaged DCO+ column density (Tex 25/50/75 K) | 3.7e11 / 4.8e11 / 6.3e11 | not stated | cm^-2 | 3 | / 50 / $4.8 \times 10^{11}$ / $1.9 \times 10^{-2}$ / $1.2 \times 10^{-12}$ / |
| Disk-averaged N(DCO+)/N(H2) (Tex 25/50/75 K) | 9.0e-13 / 1.2e-12 / 1.5e-12 | not stated | dimensionless | 3 | / 25 / $3.7 \times 10^{11}$ / $1.9 \times 10^{-2}$ / $9.0 \times 10^{-13}$ / |
| Peak of DCO+ radial profile | ~100 | not stated | AU | 2 | DCO$^+$ extends out to $\sim$230 AU and peaks at a radius of $\sim$100 AU |
| Warm DCO+ constant abundance (30–70 K) | 2.0e-12 | not stated | dimensionless | 5 | This gives $X({\rm DCO^+_{warm}})$ = $2.0 \times 10^{-12}$ |
| Best-fit temperature drop 83–120 AU (z/r<0.1) | 8 | not stated | K | 5 | with a $T = T_{\rm gas} - 8$ K region with a factor of five CO depletion from $r = 83 - 120$ AU, and a $T = T_{\rm gas} - 2$ K region for $r > 120$ AU |
| Best-fit CO depletion factor 83–120 AU | 5 | not stated | dimensionless | 5 | The CO abundance is reduced by a factor of five between $r = 83-120$ AU. |
| Radial DCO+ abundance beyond ~50 AU | 1–5e-12 | not stated | dimensionless | 3 | the abundance increases with radius by a factor of about 5 with values ranging from $1-5 \times 10^{-12}$ |

## Qualitative findings

- DCO+ shows a ring from ~50–230 AU extending beyond the mm continuum, an inner warm component at <30 AU and a tentative bump at ~200 AU  
  > "DCO$^+$ has a broad, ring-like morphology over radii $\sim$50 – 230 AU in the disk around HD 169142" (6 Conclusions)

## Claim tuples

- H: Do changes to midplane CO abundance alone or gas temperature alone reproduce the DCO+ profile? | E: Parameterized DCO+ CHEMNET models with high/low CO and cold disk variants, compared to observed radial profile | R: 10x CO changes alter DCO+ by only factor 2–3; 2 K cooling helps but fails 80–140 AU | F: Both a colder and CO-depleted midplane are needed to fit the profile | **supported**
- H: Does the 100 AU DCO+ peak trace CO freeze-out beyond the mm grains? | E: Best-fit shadowed cold, CO-depleted model | R: Cold region 83–120 AU with -8 K and CO x0.2 recovers the peak | F: DCO+ traces cold, CO-freeze-out midplane beyond mm grains | **supported**
- H: Relative contribution of warm and cold pathways | E: Constant warm abundance 30–70 K plus cold network | R: Cold >85% at r>83 AU; warm >80% at r<83 AU | F: Warm pathway dominates inside 83 AU but cannot explain emission within ~30 AU | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Parameterized steady-state chemistry used to isolate temperature and CO effects that DALI couples self-consistently  
  > "making it difficult to isolate and explore individual parameters that may affect DCO$^+$ emission" (4.3 Parameterized models)
- Alternative: Higher cosmic-ray ionization (10x) gives emission comparable to the cold disk model; thermal H2 o/p ratio over/under-produces DCO+  
  > "An increase in $\zeta_{\rm cr}$ of one order of magnitude results in DCO$^{+}$ emission comparable to the cold disk model" (4.5 CO abundance vs. gas temperature)
- How they decided it was enough: _not stated_
- Limitation (authors): Warm pathway approximated with constant abundance; exact temperature drop and CO depletion depend on ionization and o/p ratio  
  > "The complexity of hydrocarbon cation chemistry on which the warm deuterium fractionation pathway depends introduces large uncertainties in the results of even basic chemical networks." (4.5 CO abundance vs. gas temperature)
- Caveat (inferred, ours): Best fit chosen by eye with no quantitative goodness-of-fit or uncertainties on model parameters
- Caveat (inferred, ours): Degeneracy between temperature, CO depletion, ionization and o/p ratio
- Caveat (inferred, ours): LTE assumption and steady state chemistry; micron-grain distribution in the DALI model is ad hoc
- Caveat (inferred, ours): Warm component tuned at 40–70 AU then used for comparison

## Reproducibility

- Data public (paper): Project code given; ALMA data (project 2013.1.00592.S) cited  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA# 2013.1.00592.S." (Acknowledgements)
- Products in archive: _not stated_
- Code: vis_sample publicly available on GitHub  
  > "`vis_sample` is publicly available at <https://github.com/AstroChem/vis_sample>" (footnote)
- Missing: DALI and DCO+ CHEMNET configuration files and the optimized model grids
- Missing: Detailed calibration (in Fedele et al. 2017a)
- Missing: CLEAN parameters
- Missing: Measured radial profile values
- Data volume (inferred): ~10-50 GB raw MS for one Band 6 execution
- Score (inferred): 3/5, Public data and clear model scenarios, but heavy reliance on Fedele+2017 and unreleased DALI/chemnet models, with visual fits only.
- Rediscovery candidate: no, Main results depend on custom thermo-chemical modelling inputs not fully specified.

## Links

- Method: (cite: Murillo2015) (DCO+ CHEMNET chemical network)
- Method: (cite: Bruderer2012) (DALI code)
- Method: (cite: Brinch2010) (LIME radiative transfer)
- Companion: (cite: Fedele2017a) (Same ALMA data, calibration and fiducial DALI model)
- Companion: (cite: Macias2017) (Brief analysis of the same C18O and DCO+ data)

## Checks

```json
{
 "quotes": 72,
 "quotes_ok": 72,
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
  "facts": 85,
  "stated": 54,
  "rate": 0.635
 },
 "evidence_ok": true
}
```

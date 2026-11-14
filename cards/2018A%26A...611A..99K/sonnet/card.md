# The evolution of young HII regions. I. Continuum emission and internal dynamics

`2018A&A...611A..99K` | Astronomy and Astrophysics 2018 | first author: Klaassen, P. D. | arXiv: - | DOI: 10.1051/0004-6361/201731727

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: How do the ionised gas (H29α) and molecular gas dynamics on both sides of the ionisation boundary in young HC/UC H II regions relate, and is there evidence of infall onto the H II region?  
  > "This study of the dynamics of the gas on both sides of these ionisation boundaries in very young H II regions aims to quantify the relationship between the H II regions and their immediate environments." (abstract)
- Target **Nine RMS H II regions (G302.02, G302.48, G309.89, G330.28, G332.77, G336.98, G337.63, G337.84, G339.11)**: coordinates Pointing centres in Table 1, e.g. G302.02+00.25 12:43:31.52 −62:36:13.6  
  > "G302.02+00.25 12:43:31.52 −62:36:13.6 −37.1 0.61 0.58 28.38 0.15" (Table 1); "the distances with their associated uncertainties are computed using the Reid et al. (2016) rotation model." (2. Observations); z/distance 3-5.5 kpc (e.g. 4.26±0.98 kpc for G302.02)  
  > "G302.02+00.25 12:43:31.52 −62:36:13.6 −37.1 0.61 0.58 28.38 0.15" (Table 1); "the distances with their associated uncertainties are computed using the Reid et al. (2016) rotation model." (2. Observations); distance from Reid et al. (2016) rotation model  
  > "G302.02+00.25 12:43:31.52 −62:36:13.6 −37.1 0.61 0.58 28.38 0.15" (Table 1); "the distances with their associated uncertainties are computed using the Reid et al. (2016) rotation model." (2. Observations)

## Data provenance

- ALMA projects: 2013.1.00327.S
- bands: Band 6 (~250 GHz, 1.2 mm)  
  > "∼ Band 6 observations ( 250 GHz, or a wavelength of 1.2 mm)." (2. Observations)
- frequencies and spectral setup: 6 SPWs: CH3CN (257.403, 257.127 GHz), H29α 256.302 GHz, CS 244.936, SO2 242.998 and 241.616 GHz; ~0.26-0.30 km/s resolution  
  > "3 256.302 H29α 1920 274.1 0.258" (Table 3)
- continuum bandwidth: _not stated_
- arrays: ACA plus 12 m array in two configurations (compact, extended)  
  > "Each group was observed with the atacama compact array (ACA) and in two configurations with the 12 m baseline array (one compact, one extended)" (2. Observations)
- configurations: _not stated_
- baselines: 15 m to ~784 m  
  > "covering baseline lengths from 15 m to ∼784 m." (2. Observations)
- angular resolution: ~0.5-0.7'' (G339.11: 1.68''x1.11'')  
  > "G339.11+00.15 16:42:59.58 −45:49:43.6 −78.2 1.68 1.11 −84.79 0.51" (Table 1)
- max recoverable scale: comparable to the primary beam (26'')  
  > "The largest angular scale to which our observations were sensitive was comparable to our primary beam" (A.1 Combining multi-configuration datasets)
- sensitivity: continuum rms 0.12-0.51 mJy/beam  
  > "G337.63−00.08 16:38:19.02 −47:4:50.7 −56.5 0.61 0.46 90.00 0.12" (Table 1)
- time on source: 1-9 min per execution  
  > "X230 9 J1254–6111 J1427–4206 J1107–448 2015-06-04 784 21.4" (Table A.1)
- observing dates: 2014-06 to 2015-06  
  > "X2474 4 J1254–6111 J1107–4449 Callisto 2015-01-15 349 15.1" (Table A.1)
- pi or archival as stated: PI P. Klaassen project data  
  > "The ALMA data presented here (from project 2013.1.00327.S, PI: P. Klaassen)" (2. Observations)
- Line: H29α n=29 RRL (256.302 GHz)
- Line: CS J=5-4 (244.936 GHz)
- Line: CH3CN J=12-11 k-ladder (257.403/257.127 GHz)
- Other facility **ATCA/VLA**: 5 GHz and 8.6 GHz radio continuum and spectral indices  
  > "targeted high-resolution (∼1 ′′ ) radio continuum observations made with the ATCA and VLA" (2. Observations)
- Other facility **ATLASGAL**: 350 GHz maps for sample selection and flux comparison  
  > "We used the ATLASGAL submm emission maps to refine our sample" (2. Observations)
- External data: 5 GHz radio fluxes, spectral indices, clump masses, luminosities (recalculated)  
  > "The masses and bolometric luminosities are recalculated from the values given in Urquhart et al. (2014) using the updated source distance" (2. Observations) [from Urquhart et al. (2007, 2009, 2014)]
- External data: Peters et al. RADMC-3D infalling H II region model, rerun for H29α  
  > "Model taken from Peters et al. (2012) and rerun for the H29α transition." (Figure 10 caption) [from Peters et al. (2012)]
- Simulation/model as data: RADMC-3D non-LTE infalling H II region RRL model (Peters et al. 2012) rerun for H29α  
  > "We reran their models for infalling gas as traced by H29α." (3.3 Models of ionised gas)

## Processing

### Calibration

- pipeline or manual: Manual reduction (not ALMA pipeline)  
  > "all of the data were manually reduced (i.e. not using the ALMA pipeline) in CASA 4.2.2" (2. Observations)
- casa version: CASA 4.2.2  
  > "all of the data were manually reduced (i.e. not using the ALMA pipeline) in CASA 4.2.2" (2. Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto, Titan, Ceres, Mars, J1613-586 per execution (Table A.1)  
  > "X2ade 4 J1617–5848 J1617–5848 Ceres 2015-01-03 349 15.1" (Table A.1)
- flux scale uncertainty: _not stated_
- self calibration: Phase-only self-cal; amplitude self-cal omitted; not possible for G332.77 highest resolution  
  > "which was done in phase only. Additional amplitude self-calibration was found to not improve the signal-to-noise ratio, and was therefore omitted." (2. Observations)

### Imaging

- task: clean command on concatenated configurations  
  > "This single concatenated dataset was then Fourier transformed into the image plane using the clean command." (A.1 Combining multi-configuration datasets)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Continuum clipped at 3σ for Fellwalker  
  > "The final multi-configuration continuum images were clipped at 3σ (with σ given in Table 1)" (3.1.3 Core boundaries and masses)
- multiscale scales: _not stated_
- continuum subtraction: continuum from line-free portions, split with uvcontsub  
  > "The continuum emission was derived from the line free portions of each spectral window and then split out for each science target (using uvcontsub )" (2. Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Concatenate ACA and 12 m configurations; ACA needed for continuum (80% flux in 12 m only for G302.02), not for H29α  
  > "in the 12 m only dataset, we recover only 80% of the flux present in the full (i.e. including ACA) dataset." (A.2 Continuum emission)
- smoothing: _not stated_
- final beam: 0.61-0.71'' x 0.46-0.62'' (G339.11 1.68''x1.11'')  
  > "G330.28+00.49 16:03:43.28 −51:51:45.6 −93.5 0.71 0.53 87.19 0.13" (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- Distances from Reid et al. rotation model; RMS sample properties  
  > "the distances with their associated uncertainties are computed using the Reid et al. (2016) rotation model." (2. Observations) [from Reid et al. (2016); Urquhart et al. (2013)]
- Core mass equation from Hildebrand (1983) Eq. 6  
  > "using Eq. (6) of Hildebrand (1983)" (3.1.3 Core boundaries and masses) [from Hildebrand (1983)]
- Electron density limit via pressure broadening relation  
  > "an upper limit on the electron density is derived via (Brocklehurst & Seaton 1972)" (3.2.2 Derived H II region properties) [from Brocklehurst & Seaton (1972)]

### Not stated but needed to reproduce (our reading)

- Clean weighting/robust, cell size, image size, deconvolver and thresholds
- Line-free channel ranges and self-cal solution intervals
- Dust grain size, Q_ν/opacity law and exact emissivity used in Eq. 1
- Fellwalker configuration parameters
- XCLASS fit initial values, priors and fitted frequency ranges
- Mask/threshold for moment maps and H29α extraction region
- Flux scale uncertainty

## Analysis recipe

1. **Combine configurations and image continuum**: Concatenate line-free averaged continuum from ACA and 12 m data, image with clean  
  > "the relevant (i.e. line free) channels were averaged together to speed processing, and then the measurement sets from the individual array configurations were concatenated together." (A.1 Combining multi-configuration datasets)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared 12 m-only with 12 m+ACA flux and ATLASGAL 350 GHz fluxes  
  > "we recovered all of the flux in these regions with our observations, taking into account the different frequencies of the observations." (A.1 Combining multi-configuration datasets)
2. **Free-free subtraction at 256 GHz**: Extrapolate radio spectral index to 256 GHz and subtract from observed flux to get dust  
  > "Subtracting that value from the observed emission results in the thermal dust component of the emission from each region" (3.1.2 Radio continuum and SED analysis)
   - fitting: _not stated_
   - validation: _not stated_
3. **Identify cores and derive masses**: Fellwalker watershed on 3σ clipped continuum; masses from optically thin dust emission at 20, 50, 100 K  
  > "we used the Fellwalker package (Berry 2015), which uses a watershed algorithm to determine the edges of the boundaries between cores" (3.1.3 Core boundaries and masses)
   - software: Fellwalker
   - assumption: Gas-to-dust ratio 100; thermal dust emission; temperatures 20/50/100 K, 70 K for dust masses in Table 5  
  > "the gas to dust mass ratio (assumed to be 100; e.g. Draine 2004)" (3.1.3 Core boundaries and masses)
   - fitting: _not stated_
   - validation: _not stated_
4. **Core separations and Jeans lengths**: Minimum spanning tree separations compared to thermal and turbulent Jeans lengths using XCLASS CH3CCH T and density  
  > "we determined the spacing between cores using the algorithms available in astroML" (3.1.4 Core separation and Jeans lengths)
   - software: astroML
   - assumption: mean molecular mass 2.8 mH; spherical symmetry; n~1e7 cm-3  
  > "m is the mean molecular mass of the gas (set here to 2.8* m H , Kauffmann et al. 2008)" (3.1.4 Core separation and Jeans lengths)
   - fitting: _not stated_
   - validation: _not stated_
5. **Separate H29α from molecular blends**: LTE XCLASS (XCLASSMapFit) fit of CH3CCH etc. plus H29α added to database; then Gaussian decomposition  
  > "we used the LTE version of XCLASS (version 1.2) to fit our spectra" (B.1 XCLASS modelling)
   - software: XCLASS, pyspeckit, spectral-cube
   - fitting: Gaussian fits constrained by CH3CCH properties; XCLASS fit statistic chi2  
  > "These properties were used to constrain subsequent Gaussian fits to the individual components of each species" (B.2 Gaussian fitting and spectrum extraction)
   - validation: Residuals inspected; fitting H29α simultaneously avoids absorption artefacts  
  > "in not fitting the H29α emission, the resulting spectra (after having removed the poorly fit molecules) had large absorption features" (B.1 XCLASS modelling)
6. **Fit H29α line and derive H II region properties**: Gaussian and Voigt fits of area-averaged spectra; thermal width gives Te upper limit; pressure broadening limit gives ne; mass from volume  
  > "we performed both Gaussian and Voigt profile fitting and find our data are best fit by Gaussian profiles alone" (3.2 Ionised gas)
   - software: pyspeckit
   - assumption: line width purely thermal; spherical symmetry  
  > "If we assume that the Gaussian line width is purely thermal, we can derive an upper limit to the electron temperature" (3.2.2 Derived H II region properties)
   - fitting: Gaussian/Voigt profile fits  
  > "For our H29α observations we performed both Gaussian and Voigt profile fitting and find our data are best fit by Gaussian profiles alone" (3.2 Ionised gas)
   - validation: _not stated_
7. **Velocity gradients and comparison to infall model**: Moment 0/1 maps of H29α and CS compared qualitatively with Peters et al. RADMC-3D infall model  
  > "A qualitative comparisons to our data then suggests that the bullseye patterns we see in G302.02 and G336.98 are indicative of infall motions" (3.3 Models of ionised gas)
   - software: RADMC-3D
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2.2: manual calibration, self-calibration, clean imaging  
  > "all of the data were manually reduced (i.e. not using the ALMA pipeline) in CASA 4.2.2" (2. Observations)
- **Fellwalker** : core identification  
  > "we used the Fellwalker package (Berry 2015)" (3.1.3 Core boundaries and masses)
- **astroML** : minimum spanning tree core separations  
  > "using the algorithms available in astroML (VanderPlas et al. 2012)" (3.1.4 Core separation and Jeans lengths)
- **XCLASS** 1.2: LTE fitting of molecular lines blended with H29α  
  > "we used the LTE version of XCLASS (version 1.2) to fit our spectra" (B.1 XCLASS modelling)
- **pyspeckit** : Gaussian component fitting  
  > "With the individual Gaussians computed (using pyspeckit and spectralcube )" (B.2 Gaussian fitting and spectrum extraction)
- **spectralcube** : cube handling for Gaussian separation  
  > "With the individual Gaussians computed (using pyspeckit and spectralcube )" (B.2 Gaussian fitting and spectrum extraction)
- **RADMC-3D** : infalling H II region RRL model rerun for H29α  
  > "Peters et al. (2012) implemented the modelling of RRL line profiles detectable at JVLA and ALMA wavelengths into RADMC-3D" (3.3 Models of ionised gas)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| H29α detections | 6 of 9 | not stated | regions | 6 | H29α was detected in a total of six out of nine of our H II regions. |
| Electron density upper limit | <5e7 | not stated | cm-3 | 6 | constrains the electron densities in these regions to be less than 5 × 10 7 cm −3 . |
| Infall velocity shift edge to centre | ~7 to 10 | not stated | km/s | 7 | the velocity shifts from the edges to the centres of these H II regions range from ∼ 7 to 10 km s −1 , respectively. |
| Velocity gradients | 300-500 | not stated | km/s/pc | 7 | correspond to velocity gradients of 300–500 km s −1 pc −1 . |
| H29α line width G302.02 | 11.4 | 0.2 | km/s | 6 | G302.02 9.7 ± 0.1 –46.0 ± 0.2 –37.1 11.4 ± 0.2 |
| Thermal Jeans length | ~2000 | not stated | au | 4 | This gives thermal Jeans lengths of ∼2000 au in each region |
| Mass sensitivity | 1e-2 Msun; 3.6e21 cm-2 | not stated | Msun; cm-2 | 3 | we are sensitive to masses and column densities at the 10 −2 M ⊙, or 3.6 × 10 21 cm −2 limits, respectively. |

## Qualitative findings

- G302.02 and G336.98 show bulls-eye H29α velocity patterns consistent with infalling ionised gas; G330.28 and G337.63 are cometary with CS wrapping around.  
  > "those defined spatially as cometary (G330.28 and G337.63), and those defined by their bulls-eye dynamics (G302.02, G336.98, and potentially G339.11) indicative of infalling motions." (4. Conclusions)

## Claim tuples

- H: Do young H II regions show ionised gas infall? | E: H29α moment maps compared to Peters et al. (2012) infall model | R: Bulls-eye redshifted-centre velocity patterns in G302.02 and G336.98 | F: Consistent with infall onto the H II region, possible late-stage accretion | **partially**
- H: Is fragmentation governed by thermal or turbulent Jeans length? | E: Fellwalker cores, MST separations vs Jeans lengths | R: Thermal Jeans length resolved in 8 regions; separations exceed it | F: Separations more consistent with thermal Jeans lengths using precursor densities | **partially**
- H: Does pressure broadening constrain densities? | E: Gaussian vs Voigt fits of H29α | R: No pressure broadening detected | F: ne upper limits ~1e7 cm-3, consistent with still hyper-compact | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Manual reduction to ensure proper weighting when combining configurations  
  > "To ensure proper weighting of the different configurations when combining datasets, all of the data were manually reduced" (2. Observations)
- Alternative: Ionised jet scenario disfavoured relative to optically thin thermal emission, based on L8GHz-Lbol relation  
  > "we favour the optically thin scenario over the ionised jet because of the relationship between the 8 GHz and IR luminosities of these targets." (3.1.2 Radio continuum and SED analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): Core mass uncertainties 30-50%, possibly factor 2-3  
  > "we estimate a measurement uncertainty in the mass of ∼30–50 per cent, while other systematics could be pushing the formal uncertainties to a factor of 2–3." (2. Observations)
- Limitation (authors): Cannot break degeneracy between champagne flow and moving H II region  
  > "From the current data, we cannot break this degeneracy." (3.4.2 Comparison to CS emission)
- Caveat (inferred, ours): Infall interpretation rests on qualitative comparison with one model
- Caveat (inferred, ours): Small sample; G339.11 low resolution
- Caveat (inferred, ours): Blend subtraction depends on XCLASS fit with a dummy partition function
- Caveat (inferred, ours): Contraction vs infall distinction not testable with single epoch

## Reproducibility

- Data public (paper): Project 2013.1.00327.S cited; Table A.2 at CDS  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00327.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Clean parameters (weighting, cell, threshold)
- Missing: Fellwalker parameters
- Missing: XCLASS fit setup
- Missing: Dust opacity details
- Data volume (inferred): ~100-300 GB raw for 3 array configs over 9 targets and 6 SPWs
- Score (inferred): 5/5, Data and general workflow are given, but imaging and fitting parameters are largely missing; results partly qualitative.
- Rediscovery candidate: no, Key results are qualitative morphology/velocity patterns and imaging recipe is incomplete.

## Links

- Method: Peters et al. (2012) (RADMC-3D RRL infall model)
- Method: Möller et al. (2017) (XCLASS)
- Method: Berry (2015) (Fellwalker)
- Companion: Klaassen et al., in prep. (molecular environments)
- Companion: van der Tak et al., in prep. (chemistry)
- Related: RMS survey
- Related: ATLASGAL

## Checks

```json
{
 "quotes": 76,
 "quotes_ok": 76,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 58,
  "rate": 0.674
 },
 "evidence_ok": true
}
```

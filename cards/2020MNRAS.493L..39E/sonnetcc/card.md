# The ALMaQUEST survey - III. Scatter in the resolved star-forming main sequence is primarily due to variations in star formation efficiency

`2020MNRAS.493L..39E` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Ellison, Sara L. | arXiv: 1911.11887 | DOI: 10.1093/mnrasl/slz179

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type large_program_or_survey

## Science

- Fields: nearby_galaxies, star_formation
- Question: Which spaxel-level parameters drive the absolute star formation rate surface density and its scatter around the resolved star forming main sequence (gas fraction vs star formation efficiency)?  
  > "we investigate the parameters that correlate with variations in star formation rates on kpc scales" (abstract); "driven primarily by changes in star formation efficiency (SFE), with variations in gas fraction playing a secondary role" (abstract)
- Target **34 ALMaQUEST galaxies (of 46 in the survey) selected from MaNGA**: coordinates _not stated_; z/distance median z = 0.03  
  > "0.3 kpc at the median redshift of the sample, $z$=0.03" (2 Data); "In total, 11,478 spaxels in 34 galaxies fulfill all of the above criteria." (2 Data); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.01225.S, 2017.1.01093.S, 2018.1.00558.S, 2018.1.00541.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: FWHM ~2.5 arcsec, matched across galaxies  
  > "followed up with Atacama Large Millimeter Array (ALMA) CO (1-0) observations that are matched in spatial resolution" (2 Data); "0.5 arcsec in size, sampling the 2.5 arcsec resolution" (3 Results)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO 1-0 (not stated)
- Other facility **MaNGA (SDSS, Apache Point Observatory) IFU survey, DR15 with PIPE3D**: Stellar mass surface densities, H-alpha and other emission line fluxes, metallicities, SFR surface densities, and the ~1.2 million control spaxels  
  > "selected from the Mapping Nearby Galaxies at Apache Point Observatory (MaNGA; Bundy et al. 2015) survey" (2 Data); "taken from the public MaNGA Data Release 15 (DR15) data cubes, as processed by PIPE3D (Sánchez et al. 2016)" (2 Data)
- Other facility **NASA Sloan Atlas**: Sersic fit axial ratio used to de-project galactocentric radii and for inclination cut  
  > "using the Sersic fit axial ratio from the NASA Sloan Atlas" (2 Data)
- External data: MaNGA DR15 stellar mass surface density, emission line maps from PIPE3D  
  > "taken from the public MaNGA Data Release 15 (DR15) data cubes, as processed by PIPE3D (Sánchez et al. 2016)" (2 Data) [from Sánchez et al. 2016]
- External data: Star-forming spaxel classification criterion  
  > "Only spaxels classified as star-forming according to the diagnostic criterion of Kauffmann et al. (2003)" (2 Data) [from Kauffmann et al. (2003)]
- External data: O3N2 metallicity calibration  
  > "Gas-phase metallicities (O/H) are determined using the O3N2 calibration of Marino et al. (2013)" (2 Data) [from Marino et al. (2013)]
- External data: Milky Way extinction curve for Balmer decrement correction  
  > "and a Milky Way extinction curve (Cardelli, Clayton & Mathis 1989)" (2 Data) [from Cardelli, Clayton & Mathis 1989]

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
- cell size: 0.5 arcsec pixels (same grid as MaNGA maps)  
  > "mapped to the same grids of 0.5 arcsec pixels" (2 Data)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: FWHM ~2.5 arcsec (matched resolution)  
  > "0.5 arcsec in size, sampling the 2.5 arcsec resolution" (3 Results)
- final rms: _not stated_

### Inherited from earlier work

- ALMA observations, data reduction and molecular gas maps  
  > "A full description of the ALMA observations, data reduction and molecular gas maps, which typically extend to 1-2 R/R$_e$, are presented in Lin et al. (in prep)." (2 Data) [from Lin et al. (in prep)]
- Definition of spaxel offsets from control spaxels  
  > "we follow Ellison et al. (2018, 2019) and compute a series of offsets from a set of control spaxels" (2 Data) [from Ellison et al. (2018, 2019)]
- ANN architecture  
  > "adopting an identical architecture as in Bluck et al. (2019b)" (3 Results) [from Bluck et al. (2019b)]
- Improvement over random (IOR) statistic definition  
  > "improvement over random (IOR) statistic (defined in Bluck et al. 2019a)" (3 Results) [from Bluck et al. 2019a]

### Not stated but needed to reproduce (our reading)

- ALMA bands, array configurations, spectral setups, integration times and observing dates for the four projects
- CASA version, calibration and imaging recipe, and how the CO moment maps were made (clean parameters, masking, continuum subtraction)
- How the 2.5 arcsec resolution matching was done (tapering or convolution) and the CO map noise/S/N definition
- CO(1-0) to Sigma_H2 conversion details beyond alpha_CO (e.g. whether helium is included, inclination correction method)
- ANN architecture details (layers, nodes, activation, solver, hyperparameters, random seeds) are only given by reference to Bluck et al. 2019b
- Exact IOR formula and how 'random variable' baseline is generated
- Which galaxies of the 46 are the 34 retained, and the MaNGA plate-IFU IDs
- Whether the ALMaQUEST CO maps are publicly available (the survey paper is 'in prep')
- Number of control spaxels that satisfy the matching criteria per spaxel and handling of spaxels without matches

## Analysis recipe

1. **Build the spaxel sample**: Select MaNGA-matched ALMaQUEST galaxies and spaxels by S/N, star-forming classification, Halpha EW, minimum stellar mass surface density and inclination cuts  
  > "Only spaxels classified as star-forming according to the diagnostic criterion of Kauffmann et al. (2003)" (2 Data); "we require the galaxy inclination to be less than 70 degrees" (2 Data); "In total, 11,478 spaxels in 34 galaxies fulfill all of the above criteria." (2 Data)
   - parameter: CO line intensity S/N > 3  
  > "with a requirement that the S/N of the CO line intensity exceeds 3" (2 Data)
   - parameter: minimum log Sigma_star > 7 Msun kpc^-2  
  > "with a minimum log $\Sigma_{\star}$ $>$ 7 M$_{\odot}$ kpc$^{-2}$ imposed" (2 Data)
   - parameter: inclination < 70 degrees, removing 12 galaxies  
  > "which removes 12 galaxies from the full ALMaQUEST sample" (2 Data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive Sigma_H2, Sigma_SFR, Sigma_star and O/H maps**: CO luminosity converted to Sigma_H2 with constant alpha_CO; Sigma_SFR from extinction-corrected Halpha; O/H from O3N2; Sigma_star from PIPE3D; surface densities inclination corrected  
  > "CO luminosities are converted to molecular gas surface densities" (2 Data); "are computed from H$\alpha$ luminosities, a technique that has been shown to reproduce the UV and IR SFRs well in IFU data (Catalan-Torrecilla et al. 2015)" (2 Data); "All surface densities in this paper are inclination corrected." (2 Data)
   - software: PIPE3D
   - parameter: alpha_CO = 4.3 Msun pc^-2 (K km s^-1)^-1  
  > "via a constant conversion factor $\alpha_{CO}$ = 4.3 M$_{\odot}$ pc$^{-2}$ (K km s$^{-1}$)$^{-1}$" (2 Data)
   - assumption: Constant alpha_CO  
  > "via a constant conversion factor" (2 Data)
   - assumption: Milky Way extinction curve and intrinsic Halpha/Hbeta = 2.85  
  > "and a Milky Way extinction curve (Cardelli, Clayton & Mathis 1989)" (2 Data)
   - fitting: _not stated_
   - validation: Halpha SFR technique cited as reproducing UV and IR SFRs in IFU data  
  > "a technique that has been shown to reproduce the UV and IR SFRs well in IFU data (Catalan-Torrecilla et al. 2015)" (2 Data)
3. **Compute offsets from control spaxels**: Compute Delta Sigma_SFR relative to the rSFMS of ~1.2 million MaNGA DR15 star-forming spaxels, and Delta SFE and Delta f_H2 relative to control spaxels with normal SFRs matched in several parameters  
  > "of all ($\sim$ 1.2 million) star forming spaxels in the MaNGA DR15 at fixed $\Sigma_{\star}$ (matched within 0.1 dex)" (2 Data); "that are matched in $\Sigma_{\rm H_2}$ (within 0.1 dex), $R/R_e$ (within 0.1 $R/R_e$), O/H (within 0.1 dex) and total stellar mass (within 0.1 dex)" (2 Data); "that are matched in $\Sigma_{\star}$ (within 0.1 dex), $R/R_e$ (within 0.1 $R/R_e$), O/H (with 0.1 dex) and total stellar mass (within 0.1 dex)" (2 Data)
   - parameter: Control matching tolerance 0.1 dex (0.1 R/Re for radius); normal SFR defined as -0.5 < Delta Sigma_SFR < 0.5  
  > "relative to a set of control spaxels with normal SFRs ($-0.5 <$ $\Delta \Sigma_{\rm SFR}$ $<0.5$)" (2 Data)
   - assumption: Matching in O/H and R/Re mitigates metallicity- and radius-dependent alpha_CO variations  
  > "Matching in O/H and $R/R_e$ mitigates metallicity and radius dependent $\alpha_{CO}$ variations" (2 Data)
   - fitting: _not stated_
   - validation: _not stated_
4. **Rank parameters by Pearson correlation**: Pearson correlation coefficient between each of six spaxel-based variables and Sigma_SFR or Delta Sigma_SFR  
  > "we perform a simple correlation assessment in which we compute the Pearson correlation coefficient" (3 Results); "we quantify $\rho$ for $\Sigma_{\star}$, $\Sigma_{\rm H_2}$, $f_{\rm H_2}$, SFE, $\Delta$SFE and $\Delta f_{\rm H_2}$" (3 Results)
   - fitting: _not stated_
   - validation: Compared with ANN ranking  
  > "the results of the correlation analysis are in good qualitative agreement with the ranks obtained from the more complex ANN approach" (3 Results)
5. **Rank parameters with an artificial neural network**: Non-linear regression with an ANN (MLPregresser), same six inputs, performance quantified by improvement over random (IOR)  
  > "we perform a non-linear regression with an artificial neural network (ANN), utilising MLPregresser from the scikit-learn package (Pedregosa et al. 2011)" (3 Results); "Briefly, the mean square error of the network-predicted values to the truth values are computed in each case, and the improvement in performance over a random variable is quantified." (3 Results)
   - software: scikit-learn
   - parameter: Five random training samples containing 50% of the data, validated on the remainder  
  > "we train on five randomly selected input samples (containing 50% of the data) and validate on the remainder of the sample in each case" (3 Results)
   - fitting: MLP regression with identical architecture to Bluck et al. (2019b); targets Sigma_SFR or Delta Sigma_SFR; loss/optimizer not stated  
  > "adopting an identical architecture as in Bluck et al. (2019b)" (3 Results)
   - validation: Stability tested over five random training samples, typical variance ~1%  
  > "To test the stability of the network" (3 Results); "with a typical variance of only $\sim$ 1%" (3 Results)
6. **Repeat ANN for spaxels on and above the rSFMS**: Split spaxels into on-main-sequence and above-main-sequence subsets and repeat ANN regression  
  > "We repeated our ANN regression analysis separating spaxels into those on ($-0.5 <$ $\Delta \Sigma_{\rm SFR}$ $<0.5$) and above ($\Delta \Sigma_{\rm SFR}$$>$ 0.5) the rSFMS" (3 Results)
   - software: scikit-learn
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **scikit-learn (MLPregresser)** : ANN non-linear regression ranking of parameters  
  > "utilising MLPregresser from the scikit-learn package (Pedregosa et al. 2011)" (3 Results)
- **PIPE3D** : Processing of MaNGA DR15 cubes to stellar mass and emission line maps  
  > "as processed by PIPE3D (Sánchez et al. 2016)" (2 Data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of star-forming spaxels in final sample | 11,478 | not stated | spaxels | 1 | In total, 11,478 spaxels in 34 galaxies fulfill all of the above criteria. |
| Number of galaxies in final sample | 34 | not stated | galaxies | 1 | In total, 11,478 spaxels in 34 galaxies fulfill all of the above criteria. |
| Galaxies removed by inclination cut | 12 | not stated | galaxies | 1 | which removes 12 galaxies from the full ALMaQUEST sample |
| Constant CO-to-H2 conversion factor adopted | 4.3 | not stated | Msun pc^-2 (K km s^-1)^-1 | 2 | via a constant conversion factor $\alpha_{CO}$ = 4.3 M$_{\odot}$ pc$^{-2}$ (K km s$^{-1}$)$^{-1}$ |
| Typical ANN variance across five training samples | ~1% | not stated | percent | 5 | with a typical variance of only $\sim$ 1% |

## Qualitative findings

- Sigma_SFR is mainly predicted by Sigma_H2, with Delta SFE and Sigma_star as equally important secondary variables  
  > "the single most important variable in predicting a spaxel’s $\Sigma_{\rm SFR}$ (of those we have tested) is $\Sigma_{\rm H_2}$" (3 Results); "play equally important secondary roles" (3 Results)
- Delta Sigma_SFR is driven most by Delta SFE, with a secondary dependence on f_H2; Sigma_H2 plays a minor role  
  > "Instead, $\Delta$SFE is found to be the most important parameter for driving $\Sigma_{\rm SFR}$ away from the rSFMS, with a secondary dependence on $f_{\rm H_2}$" (3 Results)

## Claim tuples

- H: What sets the absolute star formation rate surface density on kpc scales | E: Pearson correlations and ANN ranking of six spaxel-based variables as predictors of Sigma_SFR | R: Sigma_H2 is the top predictor, with Sigma_star and Delta SFE secondary | F: Absolute Sigma_SFR is primarily regulated by molecular gas surface density, consistent with an extended Kennicutt-Schmidt relation | **supported**
- H: Whether scatter around the resolved star forming main sequence is due to gas fraction or star formation efficiency | E: Same correlation and ANN ranking with Delta Sigma_SFR as target | R: Delta SFE is the best predictor, with a weaker dependence on f_H2 | F: Scatter in the rSFMS is primarily due to variations in SFE, with gas fraction secondary | **supported**
- H: Whether the SFE dependence holds both on and above the rSFMS | E: ANN regression repeated separately for spaxels on and above the rSFMS | R: Delta SFE remains the top predictor in both subsets | F: Delta SFE drives Delta Sigma_SFR both within and above the rSFMS | **supported**
- H: Whether the constant alpha_CO assumption affects the conclusion | E: Qualitative argument on how a lower alpha_CO in enhanced spaxels would change Delta SFE and Delta f_H2 (no variable alpha_CO run) | R: A variable conversion factor would strengthen the Delta SFE correlation and weaken the Delta f_H2 correlation | F: The conclusion would only be strengthened with a variable conversion factor | **partially**

## Reasoning

- Why this data: Broad range of global galaxy properties gives a broad range of local Sigma_SFR  
  > "making it an ideal sample for investigating the mechanisms that regulate star formation" (1 Introduction)
- Why this method: ANN added to correlations because it can recognize more complex patterns  
  > "which has the benefit of being able to recognize more complex patterns in the data" (3 Results)
- How they decided it was enough: Stability of ANN checked with five random 50% training samples  
  > "To test the stability of the network, we train on five randomly selected input samples (containing 50% of the data) and validate on the remainder of the sample in each case." (3 Results)
- Limitation (authors): Sample is not representative in mass or volume, so no fit to the rSFMS is reported  
  > "it is not a representative (e.g. in mass or volume) sample" (3 Results)
- Limitation (authors): Constant alpha_CO adopted although it is likely lower in spaxels with enhanced Delta Sigma_SFR  
  > "Throughout this work we have adopted a constant" (4 Summary and Discussion)
- Limitation (authors): Dense molecular gas is not included  
  > "a potentially important omission in our study is the role of dense molecular gas" (4 Summary and Discussion)
- Caveat (inferred, ours): Spaxels at 2.5 arcsec resolution are spatially correlated, so effective sample is much smaller than 11,478
- Caveat (inferred, ours): Delta SFE and Sigma_SFR/Sigma_H2 share Sigma_H2 and alpha_CO, so correlation with Delta Sigma_SFR may be partly built in by construction
- Caveat (inferred, ours): Delta Sigma_SFR also uses Sigma_SFR, which enters Delta SFE, giving correlated variables
- Caveat (inferred, ours): No uncertainties on correlation coefficients or IOR values are stated in the text
- Caveat (inferred, ours): Galaxy-to-galaxy clustering of spaxels is not accounted for in the train/validation split

## Reproducibility

- Data public (paper): MaNGA DR15 cubes stated as public; ALMA CO maps described only in a paper in preparation  
  > "taken from the public MaNGA Data Release 15 (DR15) data cubes" (2 Data)
- Products in archive: _not stated_
- Missing: ALMA observing and reduction details (deferred to Lin et al. in prep)
- Missing: ANN hyperparameters and seeds
- Missing: Numeric values of correlation coefficients and IOR (only shown in figures)
- Missing: List of the 34 galaxies
- Data volume (inferred): Raw ALMA data for four projects, likely tens to a few hundred GB; the derived CO maps and MaNGA DR15 cubes for 34 galaxies are a few GB
- Score (inferred): 2/5, MaNGA data are public but the ALMA CO maps and reduction are deferred to a paper in preparation, ANN details are by reference, and the key results are shown only in figures without numbers.
- Rediscovery candidate: no, Recipe for the ALMA maps is not given and main results are rankings in figures, not numeric values.

## Links

- Method: Lin et al. (in prep) (Full description of ALMaQUEST ALMA observations, reduction and molecular gas maps)
- Method: Ellison et al. (2018, 2019) (Definition of offsets from control spaxels)
- Method: Bluck et al. (2019a, 2019b) (ANN architecture and IOR statistic)
- Method: Sánchez et al. 2016 (PIPE3D processing of MaNGA cubes)
- Companion: Lin et al. (2019) (ALMaQUEST analysis of galaxies on the star forming main sequence and the rSFMS origin)
- Companion: Ellison et al. (2019) (ALMaQUEST analysis of galaxies above the star forming main sequence)
- Related: ALMaQUEST
- Related: MaNGA

## Checks

```json
{
 "quotes": 75,
 "quotes_ok": 75,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 87,
  "stated": 45,
  "rate": 0.517
 },
 "evidence_ok": true
}
```

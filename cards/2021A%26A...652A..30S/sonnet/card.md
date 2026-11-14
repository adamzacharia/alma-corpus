# The emergence of passive galaxies in the early Universe

`2021A&A...652A..30S` | Astronomy and Astrophysics 2021 | first author: Santini, P. | arXiv: 2011.10584 | DOI: 10.1051/0004-6361/202039738

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type archival_reuse

## Science

- Fields: high_z_galaxies
- Question: Are photometrically selected z>3 passive galaxy candidates in CANDELS truly passive (checked with archival ALMA sub-mm), and what are the stellar mass function and mass density of passive galaxies at 3<z<5?  
  > "In the present work, we first confirm the passive nature of these candidates adopting the method presented in S19 and taking advantage of the richer ALMA archive" (1 Introduction); "We then analyse the emergence and mass growth of this peculiar class of galaxies by means of two powerful statistical tools: the Stellar Mass Function (SMF) and the Stellar Mass Density (SMD)." (1 Introduction)
- Target **102 passive galaxy candidates at z>3 in CANDELS (101 at 3<z<5); 53 in ALMA-accessible fields GOODS-S, UDS, COSMOS**: coordinates not stated (see Table B.1 of Merlin et al. 2019)  
  > "Out of the five CANDELS fields, only three are accessible by ALMA (GOODS-S, UDS and COSMOS). This reduces the number of candidates over which the validation method can be attempted to 53." (3.1 ALMA archival observations); z/distance 3<z<5 (photometric redshifts)  
  > "Out of the five CANDELS fields, only three are accessible by ALMA (GOODS-S, UDS and COSMOS). This reduces the number of candidates over which the validation method can be attempted to 53." (3.1 ALMA archival observations); distance from latest CANDELS photo-z estimates (Kodra et al. in prep.)  
  > "Out of the five CANDELS fields, only three are accessible by ALMA (GOODS-S, UDS and COSMOS). This reduces the number of candidates over which the validation method can be attempted to 53." (3.1 ALMA archival observations)

## Data provenance

- ALMA projects: 2012.1.00869.S, 2012.1.00173.S, 2013.1.00718.S, 2013.1.01292.S, 2013.1.00118.S, 2015.1.00242.S, 2015.1.00543.S, 2015.1.01074.S, 2015.1.00098.S, 2015.1.00870.S, 2015.1.00379.S, 2015.1.01495.S, 2016.1.01079.S
- bands: Band 6 and 7 used (Band 3 and 4 not used)  
  > "A search in the ALMA archive returned observations in Band 6 and 7 for 41 of them." (3.1 ALMA archival observations); "Band 3 and 4 observations, available for a fraction of the sources, give less stringent constraints and have not been used." (3.1 ALMA archival observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: >=0.6 arcsec images  
  > "We produced images with $\geq$0.6 arcsec spatial resolution using “natural” weightings and $uv$-tapers when needed." (3.1 ALMA archival observations)
- max recoverable scale: >1.5 arcsec (0.75 arcsec in a couple of cases)  
  > "the maximum recoverable scale is $>$1.5 arcsec (0.75 arcsec in a couple of cases)." (3.1 ALMA archival observations)
- sensitivity: median 0.17 mJy (Band 6), 0.25 mJy (Band 7)  
  > "The achieved median sensitivity is 0.17 mJy in Band 6 and 0.25 mJy in Band 7" (3.1 ALMA archival observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: archival data from many programs  
  > "We used ALMA archival observations to confirm the passive nature of our candidates." (3 Confirmation of the passive nature of the candidates from their sub-mm emission)
- Other facility **HST CANDELS**: multiwavelength photometry and catalogues for candidate selection and stellar masses  
  > "it has observed the distant Universe with the WFC3 and ACS cameras." (2 The data set and sample selection)
- Other facility **Herschel (PACS/SPIRE)**: FIR catalogues and stacking; no flux above noise  
  > "We did not measure any flux above the noise level in any of the five fields individually nor in the combination of them." (3 Confirmation of the passive nature of the candidates from their sub-mm emission)
- Other facility **Spitzer IRAC**: mid-IR photometry (reprocessed with T-PHOT)  
  > "all four channels were re-processed using T-PHOT" (2 The data set and sample selection)
- External data: Passive galaxy candidate sample at z>3 in five CANDELS fields  
  > "The present work is based on the $z>3$ passive galaxy sample selected by M19 in the five CANDELS fields." (2.1 The selection of high-z passive candidates) [from Merlin et al. 2019 (cite: merlin19)]
- External data: Main Sequence of star-forming galaxies from HST Frontier Fields  
  > "compared with the observed (i.e. not corrected for the Eddington bias) MS inferred from HST Frontier Field data by (cite: santini17)" (3.2.2 Statistical validation of sample) [from (cite: santini17)]
- External data: Photometric redshifts from latest CANDELS estimates  
  > "We adopted the photometric redshifts from the latest CANDELS estimates (cite: kodraphd19), to be presented in Kodra et al. (in prep.)." (2 The data set and sample selection) [from (cite: kodraphd19)]
- External data: IR SED templates (Michalowski10 reference, Pope08, Elbaz11, CE01, DH02, Schreiber18, Magdis21)  
  > "We considered the average SMG SEDs of (cite: michalowski10) and (cite: pope08), the two average SEDs fitted by (cite: elbaz11) for Main Sequence and starburst galaxies" (3.2 Method) [from (cite: michalowski10); (cite: pope08); (cite: elbaz11); (cite: ce01); (cite: dh02); (cite: schreiber18); (cite: magdis21)]
- Simulation/model as data: Comparison models: PANDA semi-analytic model, IllustrisTNG100/300, EAGLE, SIMBA  
  > "one semi-analytic model (the PANDA model, (cite: menci14)) and four hydrodynamic simulations" (6.2 Comparison with theoretical predictions)

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
- weighting robust: natural weighting with uv-tapers when needed  
  > "using “natural” weightings and $uv$-tapers when needed." (3.1 ALMA archival observations)
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

- ALMA validation analysis (flux measurement, uncertainty, SFR, validation tests) follows S19  
  > "extended the very same analysis described in S19 to the entire CANDELS sample of high-$z$ passive candidates." (3 Confirmation of the passive nature of the candidates from their sub-mm emission) [from Santini et al. 2019 (cite: santini19)]
- Passive selection via top-hat SFH SED fitting  
  > "Candidates have been identified by means of an *ad-hoc* developed SED fitting technique, fully described in (cite: merlin18)." (2.1 The selection of high-z passive candidates) [from (cite: merlin18)]
- Stepwise SMF method  
  > "we adopted the procedure presented in (cite: castellano10b) (Sect. 6.2.2)." (4 Determination of the galaxy Stellar Mass Function (SMF)) [from (cite: castellano10b)]
- Model stellar mass/SFR apertures as in M19  
  > "We adopted the very same stellar masses and SFR as in our previous work (M19)" (6.2.2 The selection of model passive galaxies) [from Merlin et al. 2019]

### Not stated but needed to reproduce (our reading)

- ALMA project-to-source mapping and which program provided each measurement
- Calibration/CASA version and whether pipeline products were used
- Exact uv-taper values and cleaning parameters per dataset
- Kodra photo-z catalogue (in prep.) and ASTRODEEP Herschel catalogues (in prep.)
- Bin edges and simulation inputs for stepwise SMF code
- Schechter fitting method details (sampler, priors)
- Candidate positions (in M19 Table B.1)

## Analysis recipe

1. **Measure ALMA fluxes of candidates**: Read pixel value at source position in natural-weighted tapered maps; uncertainty from std of pixels with similar coverage; max within beam if >3 sigma, mean within beam if undetected; weighted average of repeated observations  
  > "The sub-mm flux was read directly on the map (in units of Jy beam$^{-1}$) as the value of the pixel at the position of the source." (3.1 ALMA archival observations)
   - assumption: Sources unresolved  
  > "In this way, we could assume that sources are unresolved (see justification and references in S19)" (3.1 ALMA archival observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Convert sub-mm flux to SFR limits**: Fit IR templates (Michalowski10 reference); L_IR 3-1100 um converted with Kennicutt & Evans 2012 calibration adjusted to Salpeter  
  > "We converted the inferred total infrared luminosity between 3 and 1100 $\mu$m adopting the calibration of (cite: kennicutt12), adjusted to a Salpeter IMF using their conversion factor." (3.2 Method)
   - parameter: Schreiber18 templates with Td=25 K and Td=40-50 K; R_SB=1  
  > "We assumed $R_{SB} =$SFR$/$SFR$_{MS} = 1$." (3.2 Method)
   - assumption: Salpeter IMF; H0=70, Om=0.3, OL=0.7  
  > "($H_0 = 70$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_M = 0.3$, and $\Omega_\Lambda = 0.7$)" (1 Introduction)
   - fitting: _not stated_
   - validation: Results compared across IR templates  
  > "we note that our conclusions are solid against the choice of the IR templates." (3.2 Method)
3. **Validate candidates individually and statistically**: Compare ALMA 3 sigma SFR limits vs redshift with plausible (P>5%) star-forming optical solutions refit with free z; stack; compare with Main Sequence  
  > "we compared the SFR inferred from ALMA data, or in most cases the 3$\sigma$ limits on the SFR, as a function of redshift to any plausible" (3.2.1 Validation of individual candidates)
   - fitting: _not stated_
   - validation: 61% individually confirmed at 3 sigma; sample statistically consistent with passive  
  > "we could validate the passive classification for 61% of the candidates observed by ALMA at a 3$\sigma$ confidence level." (3.3 Conclusions)
4. **Compute stepwise SMF and SMD, fit Schechter functions**: Stepwise method with simulations per field to build transfer function; cosmic variance from QUICKCV reduced by sqrt(5); Schechter fits; SMD integrated 1e10-1e13 Msun  
  > "Finally, Schechter functions have been fitted to the stepwise points and uncertainties." (4 Determination of the galaxy Stellar Mass Function (SMF))
   - software: QUICKCV
   - parameter: alpha fixed to lowest-bin best fit at z>3.5  
  > "at $z>3.5$ we fixed the value of slope $\alpha$ to its best fit value in the lowest redshift bin." (5 The SMF and the Stellar Mass Density)
   - fitting: _not stated_
   - validation: Stepwise agrees with 1/Vmax of Grazian15 on GOODS-S; AGN exclusion does not change results  
  > "we verified that the SMF computed with the stepwise approach on the GOODS-S sample, using the very same photometric catalogue, redshifts and sample selections of (cite: grazian15), nicely agrees" (4 Determination of the galaxy Stellar Mass Function (SMF))

## Software

- **QUICKCV** : cosmic variance errors  
  > "Cosmic variance has been added using the QUICKCV code of (cite: moster11)." (4 Determination of the galaxy Stellar Mass Function (SMF))
- **T-PHOT** : reprocessing IRAC photometry  
  > "all four channels were re-processed using T-PHOT" (2 The data set and sample selection)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median ALMA sensitivity Band 6 | 0.17 | not stated | mJy | 1 | The achieved median sensitivity is 0.17 mJy in Band 6 and 0.25 mJy in Band 7 |
| Median limiting SFR | ~43 | semi-interquartile ~15 | Msun/yr | 2 | The median limiting SFR is $\sim$43 M$_\odot$/yr ($\sim$55 M$_\odot$/yr at $z>4$) |
| Fraction individually confirmed passive | 61 | not stated | percent | 3 | For 61% of the observed candidates (including the only detected source), ALMA constraints predict a SFR that, at any redshift, is below the optical solution |
| GOODSS-3973 S870um | 0.74 | 0.18 | mJy | 1 | GOODSS-3973, $S_{870\mu m}=0.74\pm0.18$ mJy |
| Schechter log M* (3.0-3.5) | 11.23 | 0.38 | log Msun | 4 | / 3.0 - 3.5 / 58 / -0.81 $\pm$ 0.52 / 11.23 $\pm$ 0.38 / -4.44 $\pm$ 0.35 / 6.74$^{+0.39}_{-0.34}$ / |
| Schechter log M* (4.0-5.0) | 10.55 | 0.22 | log Msun | 4 | / 4.0 - 5.0 / 12 / -0.81 / 10.55 $\pm$ 0.22 / -4.52 $\pm$ 0.30 / 5.90$^{+0.33}_{-0.43}$ / |
| Passive SMD increase z~5 to z~3 | factor of 7 | not stated | dimensionless | 4 | An increase in the SMD of passive galaxies by a factor of 7 from $z\sim 5$ to $z\sim 3$ is observed. |
| Passive fraction of SMD | 20-25% at z~3; ~5% at z>4 | not stated | percent | 4 | 20-25% of the total mass assembled by redshift $\sim$3 is accounted for by passive galaxies, while this fraction reduces to $\sim$5% at $z>4$. |

## Qualitative findings

- No significant ALMA detection even in stacks; sample consistent with being passive on average  
  > "No significant detection is found even after stacking all observations in the same Band" (3.1 ALMA archival observations)

## Claim tuples

- H: The photometrically selected z>3 candidates are truly passive | E: Archival ALMA Band 6/7 fluxes converted to SFR limits and compared to optical star-forming solutions and the Main Sequence | R: 61% individually confirmed at 3 sigma; none rejected; sample on average passive | F: The selection technique is reliable | **supported**
- H: Passive galaxies emerge around z~4 | E: Stepwise SMF and SMD of passive galaxies in three redshift bins | R: Strong evolution of M* beyond z~4; passive fraction >50% at high mass for z<4 but few percent at z>4 | F: Epoch of passivization of massive galaxies near z~4 | **supported**
- H: Models reproduce observed high-z passive SMF | E: Compare SMF, passive fraction and SMD with PANDA, TNG100/300, EAGLE, SIMBA | R: No model matches over entire mass and redshift range | F: Incomplete understanding of quenching physics | **supported**

## Reasoning

- Why this data: Herschel stacking too shallow to reject mild SFR, so ALMA used  
  > "is not sufficient to reject mild levels of SFR in these galaxies. For this reason we opted for ALMA data to confirm the passive solutions of our candidates." (3 Confirmation of the passive nature of the candidates from their sub-mm emission)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA data not deep enough to confirm or reject 39% of observed candidates; SFR depends on IR template  
  > "Since the available ALMA data is not deep enough to draw any conclusion for 39% of the observed candidates" (3.2.2 Statistical validation of sample)
- Caveat (inferred, ours): ALMA covers only 41 of 101 candidates; assumed representative of unobserved ones
- Caveat (inferred, ours): Fluxes read at pixel positions assuming unresolved sources
- Caveat (inferred, ours): Large template systematics in SFR
- Caveat (inferred, ours): SMF depends on simulations tuned to the selection; AGN included

## Reproducibility

- Data public (paper): ALMA archival data used  
  > "A search in the ALMA archive returned observations in Band 6 and 7 for 41 of them." (3.1 ALMA archival observations)
- Products in archive: _not stated_
- Missing: ALMA calibration/imaging details
- Missing: Kodra photo-z and ASTRODEEP catalogues in prep.
- Missing: SMF simulation code and binning details
- Data volume (inferred): ~100-300 GB across 13 archival projects (ALMA part only)
- Score (inferred): 3/5, Public ALMA data and tabulated results, but imaging details deferred to S19 and key catalogues unpublished.
- Rediscovery candidate: no, Recipe for ALMA photometry is incomplete here and inherited from S19; SMF requires custom simulations.

## Links

- Method: Santini et al. 2019 (cite: santini19) (ALMA validation method)
- Method: Merlin et al. 2018 (cite: merlin18) (passive selection technique)
- Method: (cite: castellano10b) (stepwise SMF method)
- Companion: Merlin et al. 2019 (cite: merlin19) (source of passive candidate sample)
- Related: CANDELS
- Related: HUGS
- Related: Herschel PEP/GOODS-Herschel/HerMES
- Related: JADES
- Related: Euclid
- Related: Roman

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 13,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 39,
  "rate": 0.52
 },
 "evidence_ok": true
}
```

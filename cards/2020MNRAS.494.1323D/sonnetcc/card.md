# An ALMA view of SO and SO<SUB>2</SUB> around oxygen-rich AGB stars

`2020MNRAS.494.1323D` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Danilovich, T. | arXiv: 2003.04334 | DOI: 10.1093/mnras/staa693

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, astrochemistry
- Question: Spatial distribution and radial abundance distributions of SO and SO2 (and isotopologues) around the low mass-loss rate R Dor and high mass-loss rate IK Tau, derived from ALMA maps and a radiative transfer model  
  > "The emphasis in this paper is on the spatial distribution of the sulphur oxides, SO and SO$_2$, towards R Dor and IK Tau" (Introduction); "the determination of the abundance distributions with a radiative transfer model" (Introduction)
- Target **R Dor**: coordinates _not stated_; z/distance 59 pc  
  > "Distance, $D$ | pc | 265 | 59" (Table 3); distance from _not stated_
- Target **IK Tau**: coordinates _not stated_; z/distance 265 pc  
  > "Distance, $D$ | pc | 265 | 59" (Table 3); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00166.S
- bands: Band 7  
  > "The spectral line survey in Band 7 of R Dor and IK Tau between $335-362$ GHz" (2 Observations)
- frequencies and spectral setup: 335-362 GHz spectral line survey  
  > "The spectral line survey in Band 7 of R Dor and IK Tau between $335-362$ GHz" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 0.04-1.6 km  
  > "The interferometer baselines of $0.04-1.6$ km allowed for imaging of structures" (2 Observations)
- angular resolution: ~150 mas; restoring beam 150 mas (R Dor), 170 mas (IK Tau)  
  > "an angular resolution of $\sim150$ mas" (2 Observations); "which is almost half the size of the 150 mas restoring beam" (2.1 SO); "much smaller than the 170 mas restoring beam" (2.1 SO)
- max recoverable scale: 2 arcsec  
  > "and angular scales of up to 2$''$" (2 Observations); "scales approaching the largest angular scale imageable (2$''$)" (2 Observations)
- sensitivity: channel rms 3-9 mJy (IK Tau), 2.7-5.7 mJy (R Dor), varying between spectral windows  
  > "For IK Tau this sensitivity range was 3–9 mJy and for R Dor it was 2.7–5.7 mJy" (2 Observations)
- time on source: _not stated_
- observing dates: August and September 2015  
  > "in August and September of 2015 (proposal 2013.1.00166.S, PI: L. Decin)" (2 Observations)
- pi or archival as stated: Survey of Decin2018 (proposal 2013.1.00166.S, PI L. Decin), reanalysed here  
  > "(proposal 2013.1.00166.S, PI: L. Decin)" (2 Observations); "This paper makes use of the following ALMA data: ADS/JAO.ALMA2013.0.00166.S." (Acknowledgements)
- Line: SO 8_8 -> 7_7, v=0 (344.3106 GHz)
- Line: 34SO 8_8 -> 7_7 (337.5801 GHz)
- Line: SO2 20_{1,19} -> 19_{2,18} (338.6119 GHz)
- Line: SO (ground and v=1 lines) 8 ground-state and 3 v=1 transitions (336.5533-346.5285 GHz (v=0))
- Other facility **APEX**: Single-dish SO and SO2 lines used to check for flux resolved out by ALMA and to constrain the abundance model  
  > "The single antenna observations allow us to compare the total flux recovered by ALMA with that observed by APEX" (2.1 SO); "Based on observations with the Atacama Pathfinder EXperiment (APEX) telescope under programme IDs O-097.F-9318 and O-098.F-9305." (Acknowledgements)
- Other facility **Herschel/HIFI**: SO and SO2 lines (from Danilovich2016) included in the IK Tau and R Dor modelling  
  > "We also include the HIFI lines presented in (cite: Danilovich2016)" (3.2.1 SO analysis)
- External data: SO and SO2 abundance-distribution parameters and mass-loss rates/stellar parameters used as the starting model  
  > "as are the parameters of the molecular models found by (cite: Danilovich2016)" (3 Modelling and analysis) [from Danilovich2016]
- External data: Line lists, level energies and Einstein A coefficients for line identification and the S18O model  
  > "From the line lists provided by the Cologne Database for Molecular Spectroscopy (cite: Muller2001; Muller2005; Endres2016)" (2.1.1 Isotopologues of SO); "with level energies and Einstein A coefficients taken from CDMS" (3.1.3 Isotopologues) [from Muller2001; Muller2005; Endres2016 (CDMS)]
- External data: CO expansion velocity of IK Tau (17.5 km/s)  
  > "the expansion velocity of 17.5 km s$^{-1}$ found from single dish observations of CO (cite: Maercker2016)" (2.2.4 IK Tau) [from Maercker2016]
- External data: Rotating disc around R Dor used to interpret the inner-region emission  
  > "the result of (cite: Homan2018) of a rotating disc around R Dor, close to the star" (3.1.1 SO analysis) [from Homan2018]
- Simulation/model as data: Chemical models of a clumpy outflow and stellar UV photons from Van de Sande et al. compared with the observed abundance profiles  
  > "Updated chemical models from (cite: Van-de-Sande2018b) and (cite: Van-de-Sande2019) consider, in addition to the usual reactions, the effects of a clumpy circumstellar medium" (4.1.3 Results from chemical modelling)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: absolute flux scale uncertain by up to 10%  
  > "As a result of the data reduction, the absolute flux scale is uncertain by up to 10% but the relative flux scale and astrometry for each star is very well registered for all species" (2 Observations)
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
- final beam: restoring beam 150 mas (R Dor), 170 mas (IK Tau)  
  > "which is almost half the size of the 150 mas restoring beam" (2.1 SO); "much smaller than the 170 mas restoring beam" (2.1 SO)
- final rms: _not stated_

### Inherited from earlier work

- Data reduction and channel rms noise per spectral window  
  > "The channel $\sigma$ rms noise varied between spectral windows, as explained in (cite: Decin2018)." (2 Observations) [from Decin2018]
- 1D radiative transfer modelling procedure  
  > "The modelling we perform in this section uses the same procedure as (cite: Danilovich2016) with modifications discussed in the text as relevant." (3 Modelling and analysis) [from Danilovich2016]
- Comparison of observed and modelled radial profiles  
  > "compared observed and modelled radial profiles as described in (cite: Brunner2018)" (3.2.1 SO analysis) [from Brunner2018]
- S18O radiative transfer model method (as for 34SO)  
  > "we ran a radiative transfer model of S$^{18}$O, using a similar method as that used by (cite: Danilovich2016) for $^{34}$SO" (3.1.3 Isotopologues) [from Danilovich2016]
- Treatment of uncertainties in the azimuthally averaged radial profile  
  > "which are taken into account in the error bars (cite: Decin2018)" (3.2.1 SO analysis) [from Decin2018]

### Not stated but needed to reproduce (our reading)

- Calibration route (pipeline or manual), CASA version and calibrators; all deferred to Decin2018
- Imaging task, weighting/robust, cell and image size, deconvolver, masks and cleaning threshold
- Continuum subtraction method and line-free channels
- Velocity resolution and integration limits used for integrated line fluxes and isotopologue ratios
- How the uncertainties on the isotopologue ratios were computed
- Name and version of the 1D accelerated lambda iteration code, and the molecular data (collisional rates) used for SO and SO2
- Goodness-of-fit measure and search range used to fit the IK Tau abundance profile; the SO fits to R Dor appear to be by eye
- Which SO2 lines went into the IK Tau uv-stack and the stacking tool
- Source of the Table 3 stellar parameters (luminosity, temperature, distances)
- APEX data reduction and the absolute APEX calibration for the flux comparison
- Ray-tracing settings for model lines

## Analysis recipe

1. **Extract 1D spectra and identify lines**: Spectra extracted in circular apertures centred on the continuum peak (R Dor 75, 300 mas and 1 arcsec radii; IK Tau 80, 320 and 800 mas); lines identified against CDMS line lists and checked with channel maps  
  > "we refer to an aperture size, which is the size of a circular region, centred on the continuum peak, for which the spectrum has been extracted." (2 Observations); "extracted for apertures with small (75 mas), intermediate (300 mas) and large (1$''$) radii" (3.1.1 SO analysis)
   - parameter: IK Tau SO aperture radii 80, 320 and 800 mas  
  > "extracted with small (80 mas), intermediate (320 mas) and large (800 mas) aperture radii" (3.2.1 SO analysis)
   - fitting: _not stated_
   - validation: Overlapping TiO2 contribution to 33SO judged small from channel-map morphology  
  > "examining the channel maps, the emission at that frequency has more morphological similarities with the other isotopic species of SO than with other TiO$_2$ lines" (2.1.1 Isotopologues of SO)
2. **Check for flux resolved out by comparing ALMA with APEX**: Compare ALMA spectra with APEX spectra of the same lines, both in Jy  
  > "The single antenna observations allow us to compare the total flux recovered by ALMA with that observed by APEX" (2.1 SO)
   - assumption: APEX flux uncertainty ~20%  
  > "the APEX uncertainty is $\sim20\%$" (2.1 SO)
   - fitting: _not stated_
   - validation: Most SO2 flux towards IK Tau resolved out; little or none for SO (8_8-7_7) towards IK Tau  
  > "most of the flux has been resolved out and less than 3% of the flux has been recovered by ALMA" (2.2.4 IK Tau)
3. **Model R Dor SO and SO2 emission with the 1D radiative transfer model and refine it**: Start from the Danilovich2016 model, then decrease the inner radius, add inner turbulent velocity and an overdense region, compared with ALMA spectra in three apertures  
  > "We use a one-dimensional accelerated lambda iteration model, which assumes a spherically symmetric CSE with a smoothly accelerating wind." (3 Modelling and analysis)
   - software: one-dimensional accelerated lambda iteration model
   - parameter: inner radius 6e13 cm  
  > "Decreasing the inner radius to $6\times10^{13}$ cm" (3.1.1 SO analysis)
   - parameter: inner turbulent velocity 11 km/s decreasing to 1 km/s  
  > "Inner turbulent velocities of 11 km s$^{-1}$ (decreasing to 1 km s$^{-1}$ in the outer regions" (3.1.1 SO analysis)
   - parameter: H2 density increased by a factor of 8 between ~3 and 4 R*  
  > "a density increase by a factor of 8 between $\sim 3~R_*$ and $4~R_*$" (3.1.1 SO analysis)
   - assumption: Spherically symmetric CSE; distance 59 pc  
  > "We use a one-dimensional accelerated lambda iteration model, which assumes a spherically symmetric CSE with a smoothly accelerating wind." (3 Modelling and analysis); "Distance, $D$ | pc | 265 | 59" (Table 3)
   - fitting: _not stated_
   - validation: Model lines compared with ALMA spectra for three aperture sizes; unable to reproduce small-aperture shape and v=1 intensity at once with a 1D model  
  > "Ultimately, we were unable to simultaneously reproduce the shape of the spectral lines taken for the smallest aperture and the intensities of the $v=1$ lines using a 1D model." (3.1.1 SO analysis)
4. **Derive S isotopic ratios in R Dor from line ratios**: Ratios of integrated fluxes of lines with the same quantum numbers, corrected by the squared frequency ratio  
  > "it is possible to derive abundance ratios directly from optically thin emission lines (assuming no flux has been resolved out)" (3.1.3 Isotopologues); "where $I$ is the integrated line flux and $\nu$ are the frequencies of the transition for each isotopologue" (3.1.3 Isotopologues)
   - parameter: Lines with the same quantum numbers for SO and SO2, excluding overlapping lines  
  > "Using lines with the same quantum numbers for both SO and SO$_2$ (and excluding lines that participate in overlaps)" (3.1.3 Isotopologues)
   - assumption: SO is a good indicator of S isotope abundances; optically thin lines; no flux resolved out  
  > "assuming that SO is a good indicator of S isotope abundances" (3.1.3 Isotopologues)
   - fitting: _not stated_
   - validation: 32S/34S agrees with 21.6+/-8.5 from Danilovich2016  
  > "which is in agreement with the result found by (cite: Danilovich2016) of $21.6\pm8.5$" (3.1.3 Isotopologues)
5. **Constrain S18O abundance in R Dor**: Radiative transfer model of S18O with a Gaussian abundance distribution and the SO e-folding radius, treating tentative and non-detected lines as upper limits  
  > "we ran a radiative transfer model of S$^{18}$O, using a similar method as that used by (cite: Danilovich2016) for $^{34}$SO" (3.1.3 Isotopologues)
   - software: one-dimensional accelerated lambda iteration model
   - parameter: rotational levels up to N=30, v=0, data from CDMS  
  > "We use rotational levels up to $N=30$ and for $v=0$, with level energies and Einstein A coefficients taken from CDMS" (3.1.3 Isotopologues)
   - assumption: Gaussian abundance distribution with the e-folding radius found for SO by Danilovich2016  
  > "Using a Gaussian abundance distribution and the same $e$-folding radius as (cite: Danilovich2016) found for SO" (3.1.3 Isotopologues)
   - fitting: _not stated_
   - validation: Ratio agrees with 315 from H2O isotopologues (Danilovich2017)  
  > "which is in good agreement with the result of 315 found through the analysis of" (3.1.3 Isotopologues)
6. **Fit the radial SO abundance distribution of IK Tau**: Azimuthally averaged radial profile of SO (8_8-7_7) from the zeroth moment map compared with 1D model; abundance profile with constant inner abundance, a step up, and a Gaussian decline  
  > "we extracted an azimuthally averaged radial profile for SO ($8_8\to 7_7$) from the zeroth moment map of the ALMA data" (3.2.1 SO analysis); "we used a model with a constant inner abundance, $f_0$, with a step up in abundance to $f_1$ at some radius, $R_1$, then a Gaussian decline with some $e$-folding radius, $R_e$." (3.2.1 SO analysis)
   - software: one-dimensional accelerated lambda iteration model
   - parameter: ALMA, HIFI and APEX SO lines used together; ALMA sets f0, single dish constrains the outer Gaussian  
  > "it is apparent the observations with ALMA largely determine the value of $f_0$, but the single antenna observations are needed to constrain the outer Gaussian portion of the radial abundance profile" (3.2.1 SO analysis)
   - assumption: Spherically symmetric model; distance 265 pc  
  > "As expected our spherically symmetric model cannot reproduce some of the asymmetries seen in the line profiles" (3.2.1 SO analysis); "Distance, $D$ | pc | 265 | 59" (Table 3)
   - fitting: Adjusted by comparison with ALMA radial profile; uncertainties for a 90% confidence interval; sampler and priors not stated  
  > "where the uncertainties are given for a 90% confidence interval" (3.2.1 SO analysis)
   - validation: Alternative Re twice as large fits ALMA equally but over-predicts low-energy single-dish lines by about a factor of two  
  > "In that case, however, the low-energy single dish lines are over-predicted by a factor of approximately two." (3.2.1 SO analysis)
7. **Search for extended SO2 emission towards IK Tau by uv stacking**: Stack in the uv-plane the v=0 most-favoured SO2 lines without overlaps and with J<30; compare full-resolution and short-baseline-weighted spectra  
  > "we attempted to better see this extended emission by stacking, in the uv-plane, most of the $v=0$ SO$_2$ lines" (3.2.2 SO2 analysis); "we included all the SO$_2$ lines detected towards IK Tau that did not participate in overlaps, were not closely adjacent to any other lines, and had $J<30$" (3.2.2 SO2 analysis)
   - parameter: Higher weighting to shorter baselines in the second stack  
  > "the spectrum resulting from giving higher weightings to the shorter baselines to increase sensitivity to large-scale flux" (3.2.2 SO2 analysis)
   - fitting: _not stated_
   - validation: Stack shows the broad component at the 17.5 km/s expansion velocity; most extended emission still not discernible  
  > "Unfortunately, the majority of the extended emission is still not discernible in the stacked channel maps" (3.2.2 SO2 analysis)
8. **Derive S isotopic ratios in IK Tau from SO lines**: Line-ratio method as for R Dor  
  > "we advise caution when interpreting the following isotopologue ratios that we calculate from the ALMA data" (3.2.3 Isotopologues)
   - fitting: _not stated_
   - validation: Two 32S ratios agree within uncertainties with SiS results of Danilovich2019  
  > "The two ratios involving $^{32}$S agree within the uncertainties with the results found by (cite: Danilovich2019) from SiS towards IK Tau" (3.2.3 Isotopologues)
9. **Compare observed SO and SO2 distributions with chemical models**: Qualitative comparison with Van de Sande clumpy-outflow chemical models  
  > "the models predict an SO$_2$ abundance profile reminiscent of the observationally-derived SO abundance profile shape" (4.1.3 Results from chemical modelling)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **one-dimensional accelerated lambda iteration radiative transfer model** : Modelling SO and SO2 abundance distributions and line profiles for R Dor and IK Tau  
  > "We use a one-dimensional accelerated lambda iteration model, which assumes a spherically symmetric CSE with a smoothly accelerating wind." (3 Modelling and analysis)
- **CDMS** : Line lists, level energies, Einstein A coefficients and predicted line intensities  
  > "From the line lists provided by the Cologne Database for Molecular Spectroscopy (cite: Muller2001; Muller2005; Endres2016)" (2.1.1 Isotopologues of SO)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 32S/33S in R Dor (from SO) | 68 | 22 | dimensionless | 4 | we find $^{32}$S/$^{33}$S $=68\pm22$ |
| 32S/34S in R Dor | 18.5 | 5.8 | dimensionless | 4 | $^{32}$S/$^{34}$S $=18.5\pm5.8$ |
| 33S/34S in R Dor | 0.17 | 0.02 | dimensionless | 4 | we find $^{33}$S/$^{34}$S $=0.17\pm0.02$ |
| Peak S18O abundance in R Dor (upper limit) | <= 2e-8 | 0.5e-8 | relative to H2 | 5 | we find a peak S$^{18}$O abundance $\leq(2\pm0.5)\times10^{-8}$ relative to H$_2$ |
| SO/S18O abundance ratio in R Dor (lower limit) | >= 335 | 84 | dimensionless | 5 | we find $\geq 335\pm 84$ |
| IK Tau SO inner abundance f0 | 4.1e-7 | not stated | relative to H2 | 6 | $f_0= 4.1\times 10^{-7}$ |
| IK Tau SO step radius R1 | 5e15 | not stated | cm | 6 | $R_1= 5\times 10^{15}$ cm |
| IK Tau SO abundance after step f1 | 2.2e-6 | 0.4e-6 (90% confidence interval) | relative to H2 | 6 | $f_1= (2.2\pm0.4)\times 10^{-6}$ |
| IK Tau SO e-folding radius Re | 1.3e16 | 0.3e16 (90% confidence interval) | cm | 6 | $R_e= (1.3\pm0.3)\times 10^{16}$ cm |
| 32SO/33SO in IK Tau | 241 | 185 | dimensionless | 8 | For $^{32}$SO/$^{33}$SO we find $241\pm185$ |
| 32SO/34SO in IK Tau | ~42 | not stated | dimensionless | 8 | for $^{32}$SO/$^{34}$SO we find $\sim42$ |
| 33SO/34SO in IK Tau | ~0.1 | not stated | dimensionless | 8 | for $^{33}$SO/$^{34}$SO we find $\sim0.1$ |
| Fraction of IK Tau SO2 (5_3,3-4_2,2) flux recovered by ALMA | < 3 | not stated | percent | 2 | less than 3% of the flux has been recovered by ALMA |
| Model under-prediction of R Dor SO2 lines | ~30 | not stated | percent | 3 | the model consistently under-predicting the ALMA lines by around 30% |

## Qualitative findings

- SO and SO2 are co-located and trace the same wind structures in R Dor  
  > "The spatially resolved observations show us that the two sulphur oxides are co-located towards R Dor and trace out the same wind structures in the circumstellar envelope (CSE)." (abstract)
- Lower-energy SO2 lines in R Dor are more extended while higher-energy lines are more confined  
  > "the lower energy lines have more extended emission while the higher energy lines exhibit more confined emission" (2.2.3 R Dor)
- Most favoured SO2 transitions are detected except those from very high excitation levels  
  > "We find that all of the most favoured transitions are detected, except for those from levels with very high excitation energies" (2.2.1 Overview)

## Claim tuples

- H: Are SO and SO2 co-located in the low mass-loss rate star R Dor? | E: Compared channel maps and contours of SO (8_8-7_7) and SO2 (20_1,19-19_2,18) from ALMA | R: SO2 traces out similar structures to SO, SO emission appearing a little more extended | F: The two sulphur oxides are co-located and trace the same wind structures in R Dor | **supported**
- H: Do the earlier single-dish 1D abundance models reproduce the ALMA SO and SO2 emission in R Dor? | E: Compared the Danilovich2016 Gaussian-abundance model and refinements with ALMA spectra in three apertures | R: Good agreement for most lines; wings and v=1 lines need a high inner turbulent velocity and overdensity | F: Gaussian abundance centred on the star works for much of the emission; higher-energy emission supports a rotating inner region | **supported**
- H: Is the SO abundance distribution in the high mass-loss rate star IK Tau shell-like? | E: Fitted a step plus Gaussian abundance profile to the ALMA radial profile together with HIFI and APEX lines | R: Best fit f0 = 4.1e-7, R1 = 5e15 cm, f1 = 2.2e-6, Re = 1.3e16 cm | F: The SO distribution is shell-like with the peak not centred on the star | **supported**
- H: Does SO2 around IK Tau follow a shell-like distribution similar to SO? | E: Compared the compact SO2 emission with the SO emission, the uv-stack and chemical models | R: Most SO2 flux resolved out; ALMA cannot test the distribution shape | F: A shell-like SO2 distribution is compatible with the data but not confirmed | **partially**
- H: Are the S isotopic ratios in R Dor consistent with solar values? | E: Line ratios of SO isotopologues from ALMA spectra | R: 32S/34S = 18.5+/-5.8, 33S/34S = 0.17+/-0.02, 32S/33S = 68+/-22 | F: 32S/34S and 33S/34S are close to solar, 32S/33S about half of solar; metallicity close to solar | **partially**
- H: Can SO observations serve as a secondary diagnostic of mass-loss rate? | E: Compared SO abundance distributions of the low and high mass-loss rate stars | R: Gaussian centred on the star for R Dor versus shell-like for IK Tau | F: SO abundance distributions differ significantly between low and high mass-loss rate stars | **supported**

## Reasoning

- Why this data: No earlier spatially resolved comparison of SO and SO2 for low and high mass-loss rate AGB stars  
  > "Until recently, there were no spatially resolved observations comparing SO and SO$_2$ towards low and high mass-loss rate AGB stars." (1 Introduction)
- Why this method: Reuse the single-dish 1D model to confirm and refine earlier abundance results with ALMA  
  > "we ought to be able to confirm and possibly refine those earlier single-dish results" (3 Modelling and analysis)
- Alternative: Adjusting the Gaussian shell abundance distribution of Danilovich2016 for IK Tau was rejected in favour of a step plus Gaussian profile, as it is hard to do precisely against ALMA radial profiles  
  > "Rather than adjusting the Gaussian shell radial abundance distribution used by (cite: Danilovich2016), which is difficult to do in a precise manner when comparing with ALMA radial profiles" (3.2.1 SO analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): Most SO2 flux towards IK Tau is resolved out  
  > "most of the flux has been resolved out and less than 3% of the flux has been recovered by ALMA" (2.2.4 IK Tau)
- Limitation (authors): Spherically symmetric 1D model cannot reproduce asymmetries and disc effects  
  > "our spherically symmetric model cannot reproduce some of the asymmetries seen in the line profiles" (3.2.1 SO analysis)
- Limitation (authors): IK Tau isotopologue ratios should be treated with caution  
  > "we advise caution when interpreting the following isotopologue ratios that we calculate from the ALMA data" (3.2.3 Isotopologues)
- Caveat (inferred, ours): Imaging and calibration are entirely delegated to Decin2018, so the ALMA reduction cannot be checked from this paper
- Caveat (inferred, ours): Model fits appear to be by eye, with no stated goodness-of-fit measure or priors
- Caveat (inferred, ours): Isotopologue ratios assume optically thin SO lines and no resolved-out flux, which the paper itself questions for some lines
- Caveat (inferred, ours): The paper cites an ALMA band 6 flux uncertainty for Band 7 data, an apparent inconsistency
- Caveat (inferred, ours): Radiative transfer code is not named, hindering replication

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA calibration and imaging recipe (from Decin2018)
- Missing: Name, version and inputs of the radiative transfer code and molecular data
- Missing: Fit procedure and goodness-of-fit for the abundance profiles
- Missing: Integration ranges and uncertainty method for isotopologue ratios
- Data volume (inferred): Likely tens of GB of calibrated Band 7 line-survey data for two targets (27 GHz coverage, 0.04-1.6 km baselines)
- Score (inferred): 2/5, ALMA project is identified and presumably in the archive, but calibration, imaging and the modelling code are not given in this paper; results are numeric but depend on an unnamed model and earlier papers.
- Rediscovery candidate: no, Imaging settings and the radiative transfer code are not given here, so the recipe is incomplete.

## Links

- Method: Decin2018 (Spectral line survey, data reduction and noise)
- Method: Danilovich2016 (1D radiative transfer modelling procedure and prior SO/SO2 models)
- Method: Brunner2018 (Comparison of observed and modelled radial profiles)
- Companion: Danilovich2019 (CS, SiS and NS analysis from the same ALMA dataset)
- Companion: Homan2018 (Rotating disc around R Dor)
- Companion: Van-de-Sande2018b; Van-de-Sande2019 (Chemical models compared with the abundance profiles)
- Related: ALMA spectral line survey 2013.1.00166.S of R Dor and IK Tau (PI L. Decin)

## Checks

```json
{
 "quotes": 110,
 "quotes_ok": 110,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 107,
  "stated": 67,
  "rate": 0.626
 },
 "evidence_ok": true
}
```

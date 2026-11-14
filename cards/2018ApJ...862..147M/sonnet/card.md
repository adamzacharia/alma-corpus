# Resolved Star Formation Efficiency in the Antennae Galaxies

`2018ApJ...862..147M` | The Astrophysical Journal 2018 | first author: Matthews, Allison M. | arXiv: 1805.12039 | DOI: 10.3847/1538-4357/aac958

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies, star_formation
- Question: What is the ratio of stellar to gas mass (instantaneous mass ratio, IMR, equal to SFE at t=0) for regions and clusters in the Antennae, and how does it depend on age, CO surface brightness and extinction?  
  > "We use Atacama Large Millimeter Array CO(3-2) observations in conjunction with optical observations from the _Hubble_ _Space_ _Telescope_ to determine the ratio of stellar to gas mass for regions in the Antennae Galaxies." (abstract)
- Target **Antennae galaxies (NGC 4038/39), overlap region**: coordinates _not stated_; z/distance d ~ 22 Mpc  
  > "The close distance to the Antennae galaxies ( _d_ _∼_ 22 Mpc, Schweizer et al. 2008)" (1.2 The Antennae); distance from Schweizer et al. 2008  
  > "The close distance to the Antennae galaxies ( _d_ _∼_ 22 Mpc, Schweizer et al. 2008)" (1.2 The Antennae)

## Data provenance

- ALMA projects: 2011.0.00876.S
- bands: CO(3-2), Cycle 0  
  > "We utilize previously attained ALMA CO(3-2) Cycle 0 data of the Antennae overlap region (Figure 1)." (2.1 ALMA Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: 13 point mosaic, extended configuration (~400 m maximum baseline), no short or zero spacings  
  > "a 13 point mosaic was obtained with the “extended” configuration ( _∼_ 400 m maximum) covering the overlap region between the two interacting galaxies." (2.1 ALMA Observations); "These data did not contain short or zero spacings" (2.1 ALMA Observations)
- baselines: _not stated_
- angular resolution: 0.56'' x 0.43'' (59 x 45 pc)  
  > "angular resolution FWHM of 0 _[′′]_ _._ 56 _×_ 0 _[′′]_ _._ 43, equivalent to (59 _×_ 45 pc)" (2.1 ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: rms 3.3 mJy/beam from line-free channels  
  > "The rms of this data cube was determined to be 3.3 mJy/beam using line-free channels." (2.1 ALMA Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Previously obtained data first presented in Whitmore et al. (2014)  
  > "data were first presented in Whitmore et al. (2014), and detailed information on the configuration and calibration of such data is given in that work." (2.1. ALMA Observations)
- Line: CO J=3-2 (not stated)
- Other facility **HST/ACS**: F435W, F550M, F814W images and cluster catalog (Whitmore et al. 2010) with ages, masses, E(B-V)  
  > "We retrieved _Hubble_ _Space_ _Telescope_ images of the the Antennae galaxies (NGC 4038/4039) using the Advanced Camera for Surveys (ACS) from the Hubble Legacy Archive." (2.2 HST Observations)
- External data: Cluster catalog: ages, masses, I-band magnitudes, E(B-V), 50 Most Luminous/Massive tables  
  > "clusters from the “50 Most Luminous” and “50 Most Massive” tables (Tables 6 and 7 of that paper) with ages _<_ 10 [8] years were identified" (3. Determination of the IMR) [from Whitmore et al. 2010]
- External data: CO-to-H2 conversion factor 4.3 Msun (K km/s pc2)^-1  
  > "the CO-to-H 2 conversion factor is 4 _._ 3 M _⊙_ (K km s _[−]_ [1] pc [2] ) _[−]_ [1] (Bolatto et al. 2013)." (2.4 Calculation of Gas Mass from CO Emission) [from Bolatto et al. 2013]
- External data: CO(1-0) ~ 2 x CO(3-2)  
  > "We adopt CO(J=1 _−_ 0) _∼_ 2 _×_ CO(J=3 _−_ 2)" (2.4 Calculation of Gas Mass from CO Emission) [from Wilson et al. (2008); Ueda et al. (2012)]
- Simulation/model as data: Starburst99 models of M/L_I vs age (rejected as non-robust) and used to bound M/L uncertainty  
  > "we generated Starburst99 models for the I-band mass-to-light ratio, M _/L_ _I_" (2.3 Determining Mass-to-light ratios)

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
- cell size: 0.08'' pixels (moment-0 map)  
  > "corresponding to 0 _[′′]_ _._ 08 pixels" (2.4 Calculation of Gas Mass from CO Emission)
- image size: _not stated_
- masking: CO moment-0 masked at >55 K km/s (5 sigma, sigma~11 K km/s)  
  > "We then created a mask of the CO map that only included locations of emission greater than 55 K km/s." (4.1 WVT binning algorithm)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.56'' x 0.43''  
  > "angular resolution FWHM of 0 _[′′]_ _._ 56 _×_ 0 _[′′]_ _._ 43" (2.1 ALMA Observations)
- final rms: 3.3 mJy/beam (cube)  
  > "The rms of this data cube was determined to be 3.3 mJy/beam using line-free channels." (2.1 ALMA Observations)

### Inherited from earlier work

- ALMA configuration, calibration and imaging of the data  
  > "detailed information on the configuration and calibration of such data is given in that work." (2.1 ALMA Observations) [from Whitmore et al. (2014)]
- HST image registration  
  > "The registration of the HST optical images was done following the methods of Brogan et al. (2010)." (2.2 HST Observations) [from Brogan et al. (2010)]
- Cluster selection CI > 1.52  
  > "As in Whitmore et al. (2010) we consider sources with _CI_ _>_ 1 _._ 52 to be clusters" (2.2 HST Observations) [from Whitmore et al. (2010)]
- WVT binning algorithm adapted from Diehl & Statler and Cappellari & Copin  
  > "We made use of the WVT binning algorithm by Diehl & Statler (2006), which is a generalization of the algorithm developed in Cappellari & Copin (2003)." (4.1 WVT binning algorithm) [from Diehl & Statler (2006); Cappellari & Copin (2003)]

### Not stated but needed to reproduce (our reading)

- Imaging parameters of the CO cube (weighting, robust, cleaning, channel width, velocity range) are only in Whitmore et al. 2014
- Moment-0 creation details (velocity range, clipping)
- Implementation/code of the adapted WVT algorithm and its parameters
- Exact aperture centers and the list of clusters used
- Absolute flux calibration uncertainty of the ALMA data
- How extinction and aperture corrections of the Whitmore catalog were applied per cluster

## Analysis recipe

1. **Gas mass from CO(3-2)**: Sum moment-0 emission in aperture/bin, convert to CO luminosity, scale CO(3-2) to CO(1-0), apply alpha_CO: M_mol = 2 alpha_CO L_CO  
  > "_M_ _mol_ = 2 _α_ CO _L_ CO _._ (1)" (2.4 Calculation of Gas Mass from CO Emission)
   - parameter: 8.5 pc/pixel, 72.6 pc^2/pixel^2  
  > "We then converted the the summed CO(J=3 _−_ 2) emission in a region with units K km s _[−]_ [1] pixel [2] to a CO luminosity by multiplying this total by the conversion factor 72.6 pc [2] /pixel [2] ." (2.4 Calculation of Gas Mass from CO Emission)
   - assumption: Milky Way metallicity, alpha_CO = 4.3, d = 22 Mpc  
  > "We assume a Milky Way metallicity for the Antennae galaxies." (2.4 Calculation of Gas Mass from CO Emission)
   - fitting: _not stated_
   - validation: SGMC total masses compared with Wilson et al. 2003, within factor ~2  
  > "These values are within a factor of _∼_ 2 with previous mass estimates of Wilson et al. (2003)" (5.1 SGMC Masses and averaged IMRs)
2. **Stellar mass in 25 and 50 pc apertures around clusters**: Take mass per e-/s from each cluster (F814W, with Whitmore extinction and aperture corrections) and apply to total F814W emission in the aperture  
  > "These values of stellar mass per _e_ _[−]_ /s derived from a specific cluster were then applied to the total F814W emission for a given aperture to determine the enclosed stellar mass." (3. Determination of the IMR)
   - parameter: Clusters from 50 Most Luminous/Massive tables, age <10^8 yr, within ALMA footprint; apertures 25 and 50 pc  
  > "This process was carried out for circular apertures of both 25 pc and 50 pc" (3. Determination of the IMR)
   - assumption: Diffuse light has same M/L as nearest cluster; uncertainty factor 2.5  
  > "we adopt the factor of 2.5 as the uncertainty in inferring the mass-to-light ratio of an aperture based on the age of the star cluster(s) present." (3. Determination of the IMR)
   - fitting: _not stated_
   - validation: _not stated_
3. **WVT tessellation of CO moment-0 map**: Adapted weighted Voronoi tessellation accreting pixels until target CO luminosity L_target reached, on map masked to 5 sigma  
  > "We adapted this algorithm such that pixels are accreted to bins until a limiting luminosity level ( _L_ target ) is reached." (4.1 WVT binning algorithm)
   - software: CASA, WVT binning (Diehl & Statler)
   - parameter: L_target = 3.6, 7.3, 14.5 x 10^5 K km/s pc^2  
  > "3 _._ 6 _×_ 10 [5] K km/s pc [2],
7 _._ 3 _×_ 10 [5] K km/s pc [2], and 14 _._ 5 _×_ 10 [5] K km/s pc [2]" (4.1 WVT binning algorithm)
   - fitting: _not stated_
   - validation: Repeated with 2 and 3 sigma thresholds; no significant change in trend  
  > "We repeated all procedures using a 2 _σ_ and 3 _σ_ threshold for the CO emission" (5.3 Star Formation Efficiency from CO map)
4. **Stellar mass in WVT bins and IMR**: Sum F814W flux per bin, convert with PHOTFLAM to absolute I magnitude, correct for extinction (A_V=3.1E(B-V), A814≈0.6 A_V), convert to mass with median cluster M/L; IMR = Mstars/(Mstars+Mgas)  
  > "We converted the reddening values to extinctions at 814 nm using _A_ _V_ = 3 _._ 1 _E_ ( _B_ _−_ _V_ )" (4.2 Calculating stellar mass in WVT bins)
   - parameter: PHOTFLAM 7.07236e-20; f_vega = 1.134e-9  
  > "Taking the PHOTFLAM keyword from the image header as 7 _._ 07236 _×_ 10 _[−]_ [20] ergs/cm [2] / [˚] A/ _e_ _[−]_" (4.2 Calculating stellar mass in WVT bins)
   - assumption: Gas mass error 20%  
  > "we assume a nominal error in the gas mass of 20%" (4.3 Errors in the IMR)
   - fitting: _not stated_
   - validation: Error propagation gives ~20% fractional IMR error for much of parameter space  
  > "results in fractional errors in the IMR around _∼_ 20% for much of parameter space." (4.3 Errors in the IMR)

## Software

- **CASA** : rms of CO moment-0 map in isolated patches  
  > "The rms of the CO moment0-map was calculated with CASA in isolated patches of the map" (4.1 WVT binning algorithm)
- **IRAF (DAOFIND)** : construction of the HST cluster catalogs (Whitmore et al. 2010)  
  > "Catalogs of clusters and their optical properties in the Antennae were constructed from the _F_ 550 _M_ image using DAOFIND in IRAF" (2.2 HST Observations)
- **Starburst99** : model M/L_I vs age; bounding M/L uncertainty  
  > "we generated Starburst99 models for the I-band mass-to-light ratio" (2.3 Determining Mass-to-light ratios)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total gas mass SGMC 1 | 7.8e8 | not stated | Msun | 1 | the total gas mass is approximately 7 _._ 8 _×_ 10 [8] M _⊙_, 6 _._ 3 _×_ 10 [8] M _⊙_, and 6 _._ 6 _×_ 10 [8] M _⊙_ |
| Total gas mass SGMC 2 | 6.3e8 | not stated | Msun | 1 | the total gas mass is approximately 7 _._ 8 _×_ 10 [8] M _⊙_, 6 _._ 3 _×_ 10 [8] M _⊙_, and 6 _._ 6 _×_ 10 [8] M _⊙_ |
| Total gas mass SGMC 3 | 6.6e8 | not stated | Msun | 1 | the total gas mass is approximately 7 _._ 8 _×_ 10 [8] M _⊙_, 6 _._ 3 _×_ 10 [8] M _⊙_, and 6 _._ 6 _×_ 10 [8] M _⊙_ |
| Mean IMR of WVT bins | 2.4 | not stated | percent | 4 | with the mean of the distribution being 2 _._ 4 % (see Figure 8) |
| Averaged IMR in SGMCs 1, 2, 3 | 0.2%, 0.3%, 0.3% | not stated | percent | 4 | The averaged IMRs are 0.2%, 0.3%, and 0.3% for SGMCs 1, 2, and 3, respectively. |
| IMR of cluster 18848 in 25 and 50 pc apertures | 23% and 21% | not stated | percent | 2 | Centering the measurement on the stellar cluster yields an IMR of 23% and 21% for the 25 pc and 50 pc apertures, respectively. |
| Mean fraction of light from cluster in WVT bin | 11 | not stated | percent | 4 | the mean fraction of light than can be attributed to the cluster is 11% |

## Qualitative findings

- Aperture-centered IMR increases with cluster age; CO-centered WVT IMR decreases with age, attributed to selection bias and line-of-sight contamination  
  > "This resulted in a monotonically increasing trend of IMR with age" (7. Conclusions)
- IMR shows strong dependence on extinction but not on CO surface density  
  > "There is no observed dependence of IMR( _t_ ) on surface density, but a strong dependence on extinction." (7. Conclusions)

## Claim tuples

- H: Do few clusters have SFE>0.2, implying few remain bound? | E: IMR in 25/50 pc apertures and WVT bins | R: Only ~8 clusters with IMR>10%; 2/5 youngest massive clusters have IMR≳0.5 | F: Only a small fraction of clusters likely remain bound | **supported**
- H: How fast is CO cleared around clusters? | E: IMR vs age in apertures | R: Some clusters cleared by 10^6.7 yr, majority by 10^7.5 yr | F: Rapid gas clearing | **supported**
- H: Does IMR depend on CO surface brightness or extinction? | E: IMR vs bin surface density and A814 | R: No correlation with surface density; clear increase with extinction | F: Extinction traces evolutionary state | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: WVT chosen as objective, adaptive binning following CO emission rather than by-eye regions or Cartesian grid  
  > "we believe this introduces biases due to the subjective opinions of differing authors" (4. Determination of the IMR)
- Alternative: Starburst99 and ensemble-median M/L approaches rejected; Cartesian grid and standard Voronoi tessellation rejected  
  > "we found that this method was not robust." (2.3 Determining Mass-to-light ratios)
- How they decided it was enough: _not stated_
- Limitation (authors): Stellar mass of youngest clusters underestimated owing to dust; line-of-sight contamination; no formal errors possible  
  > "Complicated and unknown uncertainties in both the stellar and gas mass calculations make estimating formal errors on the resulting IMR nearly impossible." (4.3 Errors in the IMR)
- Caveat (inferred, ours): Single CO(3-2)-to-CO(1-0) factor and Galactic alpha_CO may be wrong for a merger
- Caveat (inferred, ours): Gas association with clusters is unconstrained in projection
- Caveat (inferred, ours): Cluster-by-cluster M/L assumption with small samples
- Caveat (inferred, ours): No short spacings may resolve out diffuse gas

## Reproducibility

- Data public (paper): ALMA Cycle 0 data acknowledged by project code; HST from Hubble Legacy Archive  
  > "from the Hubble Legacy Archive" (2.2 HST Observations)
- Products in archive: _not stated_
- Missing: Imaging recipe in Whitmore et al. 2014
- Missing: Adapted WVT code
- Missing: Cluster catalog values from Whitmore et al. 2010
- Data volume (inferred): ~10-50 GB for Cycle 0 raw data; small if using calibrated cube
- Score (inferred): 3/5, Public data and clear mass recipe, but the cube production, WVT code and catalog details rely on other papers.
- Rediscovery candidate: no, Depends on external catalogs and an unreleased adapted algorithm; results are somewhat numeric but not fully specified.

## Links

- Method: Diehl & Statler (2006) (WVT binning algorithm)
- Method: Cappellari & Copin (2003) (Voronoi binning basis)
- Companion: Whitmore et al. (2014) (Original ALMA data presentation)
- Companion: Whitmore et al. (2010) (HST cluster catalog)

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
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
  "facts": 78,
  "stated": 44,
  "rate": 0.564
 },
 "evidence_ok": true
}
```

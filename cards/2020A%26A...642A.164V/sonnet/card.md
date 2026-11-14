# Observations of edge-on protoplanetary disks with ALMA. I. Results from continuum data

`2020A&A...642A.164V` | Astronomy and Astrophysics 2020 | first author: Villenave, M. | arXiv: 2008.06518 | DOI: 10.1051/0004-6361/202038087

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: How large are vertical settling and radial drift of millimeter dust in protoplanetary disks, studied directly through the edge-on view of 12 HST-selected edge-on disks?  
  > "We aim to study vertical settling and radial drift of dust in protoplanetary disks from a different perspective: an edge-on view." (abstract)
- Target **12 edge-on disks (Tau 042021, HH 30, IRAS 04302, HK Tau B, HV Tau C, IRAS 04200, Haro 6-5B, IRAS 04158, Oph 163131, ESO-Halpha 569, ESO-Halpha 574, HH 48 NE)**: coordinates given per source in the stellar-parameters table (e.g. Tau 042021: 04 20 21.4 +28 13 49.2, J2000)  
  > "For our targets, we decided to adopt the average distance of the parent star-forming regions instead; 140 pc for the sources in Taurus and Ophiuchus" (2.1 Target selection); "192 pc for those in Chamaeleon I" (2.1 Target selection); z/distance 140 pc (Taurus, Ophiuchus); 192 pc (Cha I)  
  > "For our targets, we decided to adopt the average distance of the parent star-forming regions instead; 140 pc for the sources in Taurus and Ophiuchus" (2.1 Target selection); "192 pc for those in Chamaeleon I" (2.1 Target selection); distance from average distance of the parent star-forming regions (Kenyon 2008; Ortiz-Leon 2018; Canovas 2019; Dzib 2018)  
  > "For our targets, we decided to adopt the average distance of the parent star-forming regions instead; 140 pc for the sources in Taurus and Ophiuchus" (2.1 Target selection); "192 pc for those in Chamaeleon I" (2.1 Target selection)

## Data provenance

- ALMA projects: 2016.1.00460.S, 2013.1.01175.S, 2016.1.01505.S, 2016.1.00771.S
- bands: Band 7 (0.89 mm), Band 4 (2.06 mm), archival Band 6 (1.33 mm) for some  
  > "supplemented with archival band 6 data (1.33 mm) where available" (abstract)
- frequencies and spectral setup: Band 7 continuum geometric mean 336.8 GHz; Band 4 145.0 GHz; Band 6 (Tau 042021, Oph 163131) 224.4 GHz  
  > "the continuum data which has a geometric mean frequency of 336.8 GHz (0.89 mm)" (2.2.1 Band 7 survey); "with a geometric mean frequency of 145.0 GHz (2.06 mm)" (2.2.2 Band 4 survey); "leading to a geometric mean frequency of 224.4 GHz (1.34 mm)" (2.3.2 ALMA observations of Tau 042021 and Oph 163131)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Compact and extended configurations, C40-3 to C40-8/9 (see observation table)  
  > "| Survey Tau$^a$ | 7 | 24/11/2016 | C40-4 | 15 m$-$0.7 km | 43 | 1.1 | 4.7 | 2016.1.00460.S |" (Table 1 (obs))
- baselines: _not stated_
- angular resolution: Taurus survey typical beams ~0.11"x0.07" (band 7) and ~0.11"x0.04" (band 4); other sources 0.23x0.13" to 0.48x0.30"  
  > "this leads to typical beam sizes of about 0.11$''$$\times$0.07$''$in band 7 and about 0.11$''$$\times$0.04$''$in band 4" (2.4 ALMA imaging)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (Band 7; not analysed here) (345.796 GHz)
- Other facility **HST (and some ground-based NIR images)**: Optical/NIR scattered-light images used for sample selection and comparison of sizes  
  > "confirmed as edge-on disks (hereafter EOD) according to their optical or near-infrared HST scattered-light images" (2.1 Target selection)
- External data: Band 6 reduction/data of HH 30  
  > "The observational setup and data reduction of the band 6 observations are presented in (cite: Louvet_2018)." (2.3.1 ALMA observations of HH 30) [from (cite: Louvet_2018)]
- External data: Dynamical stellar masses from CO and spectral types  
  > "Thus, we report dynamical stellar masses estimated from CO emission." (2.1 Target selection) [from (cite: Luhman_2007; Luhman_2010)]
- External data: Literature (sub)millimeter fluxes for global spectral indices  
  > "Using the continuum fluxes from our survey and (sub)millimeter fluxes from the literature, we estimate the global millimeter spectral index" (3.3 Estimation of spectral indices) [from not stated in text (references said to be given below)]
- Simulation/model as data: MCFOST toy radiative transfer disk models (settled/non-settled, high/low mass) at 75-90 deg, imaged with CASA simulator at the data uv-coverage  
  > "we constructed several toy disk models and performed radiative transfer with the MCFOST code (cite: Pinte_2006; Pinte_2009) to produce synthetic images for comparison with the data" (4 Discussion)

## Processing

### Calibration

- pipeline or manual: Pipeline for compact configurations and band 4; manual calibration for extended band 7 Taurus data  
  > "The raw data of the extended configuration observations of the Taurus sources was manually calibrated, using CASA version 5.1." (2.2.1 Band 7 survey)
- casa version: CASA 4.3, 4.7, 5.1 depending on execution  
  > "We calibrated the raw data of the compact array executions using the pipeline from CASA package version 4.7." (2.2.1 Band 7 survey)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10%  
  > "We use 10% error values throughout Table 1, which correspond to the typical flux calibration errors of ALMA" (3.1)
- self calibration: Applied to highest S/N sources (band 7: Tau 042021, IRAS 04302, HK Tau B, Haro 6-5B; band 6: Tau 042021, Oph 163131; band 4: HH 30)  
  > "We applied self-calibration on the sources with the highest signal-to-noise ratio (on at least one array configuration)." (2.4 ALMA imaging)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5 (except HH 30 band 6)  
  > "We constructed the images from the calibrated visibilities with a Briggs robust weighting parameter of 0.5" (2.4 ALMA imaging)
- uv taper: Same uvrange plus uvtaper for common-resolution band 4/7 maps  
  > "we first re-imaged each source using the same `uvrange` and applying a `uvtaper` to limit the effect of flux filtering and of different uvcoverage" (2.4 ALMA imaging)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Compact and extended configurations combined (except IRAS 04158 band 7 compact only)  
  > "the images were generated by combining the visibilities from the compact and extended configurations" (2.4 ALMA imaging)
- smoothing: CASA imsmooth to identical beam in both bands  
  > "to obtain exactly the same angular resolution between both bands, we used the `imsmooth` CASA task" (2.4 ALMA imaging)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- HH 30 band 6 data reduction/imaging taken from earlier paper  
  > "except for the band 6 of HH 30 for which we used the reduction presented in (cite: Louvet_2018)" (2.4 ALMA imaging) [from (cite: Louvet_2018)]
- Dust mass formula with T=20 K, kappa=3.4 cm2/g  
  > "We use typical values of $T_\mathrm{dust}$ = 20 K and $\kappa_\nu=3.4$ cm$^2\,$g$^{-1}$, as in (cite: Ansdell_2016)" (4.3.1) [from (cite: Ansdell_2016)]
- Millimeter dust scale height 0.7 au at 100 au in settled model, following HL Tau  
  > "Following the results from (cite: Pinte_2016) for HL Tau" (4 Discussion) [from (cite: Pinte_2016)]

### Not stated but needed to reproduce (our reading)

- Self-calibration solution intervals and number of rounds per source
- Clean mask, threshold, deconvolver, cell and image size
- Exact uvrange and uvtaper values for common-resolution maps
- Radiative transfer model parameters (surface density exponent, grain size distribution, stellar parameters) not fully given
- Literature fluxes and references used for global spectral indices
- Aperture shapes for flux measurements
- Phase calibrators per execution

## Analysis recipe

1. **Calibrate and image continuum**: Pipeline or manual calibration; Briggs robust 0.5 imaging combining configurations; self-calibration for high S/N sources  
  > "We constructed the images from the calibrated visibilities with a Briggs robust weighting parameter of 0.5" (2.4 ALMA imaging)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared band 7 fluxes from compact vs combined data, consistent within 10%  
  > "We checked that the integrated fluxes recovered using the compact configuration band 7 observations or both compact and extended configurations jointly are consistent within 10%." (3.1)
2. **Align band 4 and band 7 images**: Gaussian centroid fits, then align to common center with fixplanets (fixuvw=True)  
  > "We aligned the band 4 and band 7 observations using the `fixplanets` task in CASA" (2.5)
   - software: CASA
   - assumption: Offsets between bands in edge-on disks should remain minimal compared to the beam  
  > "Because models of edge-on disks also show that offsets between bands should remain minimal compared to the beam size" (2.5)
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure fluxes and brightness temperatures**: Integrate flux to 3 sigma in elliptical apertures; T_B maps from equal-resolution maps without Rayleigh-Jeans approximation  
  > "The total continuum flux density of each source is measured by integrating the signal, down to the 3$\sigma$ noise level, within elliptical apertures tailored to each source." (3.1)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
4. **Measure radial and vertical extents**: Major-axis cuts, size at 3 sigma fraction of peak, Delta r/r between 80% and 20% of peak; minor-axis cuts fit with Gaussians, deconvolved by the beam  
  > "we measure the fractional range of radius over which the millimeter emission decreases from 80% to 20% of the peak emission, called $\Delta r / r$" (3.2.1 Size estimations)
   - assumption: Gaussian profiles for deconvolution of minor axis  
  > "we also deconvolve the minor axis sizes by the beam, assuming that both profiles are Gaussian" (3.2.2)
   - fitting: Gaussian fits to minor axis profiles  
  > "We measure the minor axis sizes by fitting Gaussians to the generated profiles" (3.2.2)
   - validation: Checked FWHM instead of 3 sigma gives similar conclusions  
  > "We verified that using the FWHM of the cut profiles instead of the 3$\sigma$ levels yields similar conclusions." (3.2.1 Size estimations)
5. **Spectral indices**: Least-squares fit of photometry 800 um-3.3 mm; pixel-by-pixel band 4/7 maps via immath with 5 sigma cut  
  > "We use a least-squares fit of all photometric points between 800 $\mu$m and 3.3 mm." (3.3)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
6. **Compare with radiative transfer toy models**: MCFOST models with/without settling, high/low dust mass, imaged with CASA simulator using data uv-coverage  
  > "produced synthetic images using the CASA simulator with the same uv-coverage as our band 7 (resp. band 4) data" (4 Discussion)
   - software: MCFOST, CASA
   - parameter: Mdust = 1e-3 Msun (HM), 5e-5 Msun (LM); h_1mm = 0.7 au at 100 au (settled), 10 au (non-settled); outer radius 140 au; d=140 pc  
  > "We use $M_\mathrm{dust}=1\cdot10^{-3}\,M_\odot$ for high mass disk models (HM), and $M_\mathrm{dust}=5\cdot10^{-5}\,M_\odot$ for low mass models (LM)." (4 Discussion)
   - assumption: Settling profile of Fromang & Nelson 2009; maximum grain size 3 mm  
  > "because large grains are included (maximum grain size is 3 mm)" (4.3.2)
   - fitting: _not stated_
   - validation: _not stated_
7. **Dust mass lower limits**: Optically thin M=F d^2/(kappa B(T))  
  > "$M_\mathrm{dust}=F_\nu d^2 / \kappa_\nu B_\nu(T_\mathrm{dust})$" (4.3.1)
   - parameter: T=20 K, kappa=3.4 cm2/g  
  > "We use typical values of $T_\mathrm{dust}$ = 20 K and $\kappa_\nu=3.4$ cm$^2\,$g$^{-1}$" (4.3.1)
   - assumption: Optically thin, isothermal emission  
  > "we assume optically thin and isothermal dust emission at sub-millimeter wavelengths" (4.3.1)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.3, 4.7, 5.1: Calibration, imaging, imsmooth, fixplanets, immath, simulator  
  > "we used the `imsmooth` CASA task" (2.4 ALMA imaging)
- **MCFOST** : Radiative transfer toy models  
  > "performed radiative transfer with the MCFOST code" (4 Discussion)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median integrated spectral index | 2.5 | 0.3 | dimensionless | 5 | The median spectral index of the edge-on disks in our study, $\bar{\alpha}_{mm}=2.5\pm0.3$ |
| Band 7 radial size larger than band 4 (four disks) | 12 | not stated | percent | 4 | these sources have band 7 major axis size on average 12% larger than that of the band 4 |
| Tau 042021 band 7/band 4 vertical extent ratio | 1.5 | not stated | dimensionless | 4 | For this disk, the band 7 appears about 1.5 times more extended vertically than the band 4. |
| Mean peak T_B band 7 of three best resolved sources | 10.6 | not stated | K | 3 | We estimate a mean peak brightness temperature of 10.6 K for the three best resolved sources in band 7 |
| Dust grain-size exponent of vertical extent in Tau 042021 | ~0.5 | not stated | dimensionless | 4 | $m = -\log(S_{d, b7}/S_{d, b4}) / \log(a_{b7} / a_{b4}) \sim 0.5$ |
| Mean dust mass lower limit for 6 disks inclined >75 deg | 25 | not stated | Earth masses | 7 | we find a mean dust mass of about 25 M$_\oplus$ for the 6 edge-on disks more inclined than 75$^\circ$ |

## Qualitative findings

- Millimeter emission is more compact than scattered light vertically and radially in most disks.  
  > "All sources are found much less extended vertically in the millimeter than in scattered light" (3.4)
- IRAS 04302, the only Class I object, shows flaring in the millimeter.  
  > "The high resolution band 4 disk image of IRAS 04302shows evidence of flaring" (4.5.3 (IRAS 04302))

## Claim tuples

- H: Millimeter grains in edge-on disks are vertically settled | E: Compare ALMA minor-axis extents and radial profiles with MCFOST models with and without settling | R: At least three disks require a small mm scale height of a few au at 100 au; non-settled high-mass model is ruled out | F: Large grains are significantly vertically settled | **supported**
- H: Size-dependent settling occurs in Tau 042021 | E: Compare band 7 and band 4 minor axis sizes | R: Band 7 ~1.5 times more extended vertically than band 4; opacity alone gives ~1.1 | F: Grain-size-dependent settling, consistent with m~0.5 | **supported**
- H: Radial drift produces smaller millimeter than scattered-light disks and band 4 smaller than band 7 | E: Compare sizes across bands and with scattered light; compare with Birnstiel & Andrews 2014 model | R: Four disks 12% larger in band 7; three have identical extents with sharp edges; drift model predicts larger differences | F: Drift occurs but is slowed, likely by pressure traps | **partially**
- H: Edge-on disks are optically thick | E: Brightness temperatures, spectral indices, models | R: Peak T_B mostly <=10 K; alpha_mm <=3 for all, median 2.5 | F: Emission is at least partly optically thick, tracing cold outer midplane | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Non-settled high-mass model ruled out because no dark lane or vertical asymmetry observed  
  > "This configuration (NS-HM) can be ruled out." (4.1.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Astrometric accuracy insufficient to confirm shifts between bands  
  > "the astrometric accuracy of our observations is not sufficient to confirm any significant motion or shift of the sources between the two bands" (2.5)
- Limitation (authors): Minor-axis size is not an equivalent dust scale height measure  
  > "the minor axis size is related but is not a measurement of an equivalent ”dust scale height” at a given radius" (footnote 3)
- Caveat (inferred, ours): Toy models are not fitted to individual sources; scale heights are inferred qualitatively
- Caveat (inferred, ours): Minor-axis sizes limited by resolution and beam deconvolution assuming Gaussians
- Caveat (inferred, ours): Scattered-light sizes may be underestimated
- Caveat (inferred, ours): Size errors are 1/10 beam, not statistical

## Reproducibility

- Data public (paper): Project codes given; ALMA data acknowledged by ADS/JAO.ALMA codes  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00460.S, ADS/JAO.ALMA#2016.1.01505.S, ADS/JAO.ALMA#2016.1.00771.S and ADS/JAO.ALMA#2013.1.01175.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Clean parameters and self-calibration details
- Missing: Literature fluxes for spectral indices
- Missing: Full MCFOST model parameter files
- Data volume (inferred): ~200-500 GB raw for four projects
- Score (inferred): 3/5, Data public and measurements well described, but imaging, self-cal and model details are incomplete.
- Rediscovery candidate: no, Recipe incomplete for imaging/self-cal and the modelling part is not numerically fitted.

## Links

- Method: (cite: Louvet_2018) (HH 30 band 6 reduction)
- Method: (cite: Birnstiel_2014) (analytic radial drift model compared with the data)
- Companion: Flores et al., in prep (Oph 163131 line emission)
- Companion: Ragusa et al., in prep (IRAS 04158 binary analysis)
- Companion: Wolff et al., in prep (Oph 163131 dust modelling)
- Companion: Angelo et al., in prep (biases in edge-on disk detection)
- Related: DSHARP (comparison of brightness temperatures)

## Checks

```json
{
 "quotes": 69,
 "quotes_ok": 69,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 85,
  "stated": 48,
  "rate": 0.565
 },
 "evidence_ok": true
}
```

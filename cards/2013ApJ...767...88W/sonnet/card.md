# ALMA Redshifts of Millimeter-selected Galaxies from the SPT Survey: The Redshift Distribution of Dusty Star-forming Galaxies

`2013ApJ...767...88W` | The Astrophysical Journal 2013 | first author: Weiß, A. | arXiv: 1303.2726 | DOI: 10.1088/0004-637X/767/1/88

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What is the redshift distribution of strongly lensed, mm-selected SPT dusty star-forming galaxies, measured through a blind ALMA 3 mm CO line survey, and how does lensing and selection bias affect it?  
  > "We discuss the effect of gravitational lensing on the redshift distribution and compare our measured redshift distribution to that of models in the literature." (abstract)
- Target **26 SPT-selected lensed DSFGs (e.g. SPT0103-45 ... SPT2147-50)**: coordinates ALMA 3 mm continuum positions listed in Table 1 (e.g. SPT0103-45: 01:03:11.50 -45:38:53.9)  
  > "SPT0103-45 | SPT-S J010312-4538.8 | 01:03:11.50 | -45:38:53.9" (Table 1); z/distance Line-derived redshifts z=2.01 to 5.70 (Table 2)  
  > "SPT0103-45 | SPT-S J010312-4538.8 | 01:03:11.50 | -45:38:53.9" (Table 1); distance from ALMA 3 mm CO/CI line detections, plus additional spectroscopy or photometry for ambiguous cases  
  > "SPT0103-45 | SPT-S J010312-4538.8 | 01:03:11.50 | -45:38:53.9" (Table 1)

## Data provenance

- ALMA projects: 2011.0.00957.S
- bands: Band 3 (84-116 GHz)  
  > "nearly the entire bandwidth of the Band 3 (84$-$116 GHz) receiver" (2 Observations)
- frequencies and spectral setup: Five tunings, 7.5 GHz each, covering 84.2-114.9 GHz; two 3.75 GHz sidebands, each with two 1.875 GHz spectral windows  
  > "Each tuning covers 7.5 GHz in two 3.75 GHz wide sidebands, each of which is covered by two 1.875 GHz spectral windows in the ALMA correlator." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: 14-17 antennas  
  > "The observations employed between 14 and 17 antennas in different sessions" (2 Observations)
- configurations: Cycle 0 early science compact array configuration  
  > "The ALMA observations were carried out in 2011 November and 2012 January in the Cycle 0 early science compact array configuration." (2 Observations)
- baselines: _not stated_
- angular resolution: 7''x5'' to 5''x3'' (FWHM)  
  > "resulted in typical synthesized beams of 7$''\times$5$''$ to 5$''\times$3$''$ (FWHM) from the low- to high-frequency ends of the band" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: 2 mJy/beam per 19.5 MHz channel (1.4 in the overlap range); continuum 70 uJy/beam  
  > "The typical noise per channel is 2 mJy beam$^{-1}$ across the band and 1.4 mJy beam$^{-1}$ between 96.0 and 102.8 GHz where two tunings overlap." (2 Observations); "Continuum images generated from the full bandwidth have typical noise levels of 70 $\mu$Jy beam$^{-1}$." (2 Observations)
- time on source: ~120 s per tuning, ~10 min per source total  
  > "Each target was observed for $\sim
120$ seconds in each tuning, or roughly 10 minutes per source in total, not including overheads." (2 Observations)
- observing dates: 2011 November and 2012 January  
  > "The ALMA observations were carried out in 2011 November and 2012 January" (2 Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 to 7-6 (and 1-0 at low z) (not stated)
- Line: [CI] 1-0 (not stated)
- Other facility **SPT**: 1.4 and 2 mm survey selection and photometry  
  > "Sources were selected from the first 1300 deg$^2$ of the now complete 2500 deg$^2$ SPT-SZ survey" (2 Observations)
- Other facility **APEX LABOCA**: 870 um photometry  
  > "We used the LABOCA instruments at APEX to obtain 870 imaging." (Supplementary Far-Infrared Photometry)
- Other facility **Herschel-SPIRE**: 250, 350, 500 um photometry  
  > "*Herschel*-SPIRE maps at 250, 350, and 500 $\mu$m were observed as part of program OT2_jvieira_5." (Supplementary Far-Infrared Photometry)
- Other facility **APEX FLASH / Z-Spec, ATCA, SMA, VLT FORS**: Follow-up spectroscopy ([CII], CO(1-0), CO(7-6), CIV) to break redshift degeneracy  
  > "For five of the sources in our sample for which we have detected only a single line in our 3 mm scan, we determine the redshift using additional mm/submm or optical spectroscopy." (3.1 Additional spectroscopic observations)
- External data: Redshifts for two SPT sources (SPT0538-50, SPT2332-53) added to the sample  
  > "ZSpec/VLT from (cite: greve12); no ALMA data" (Table 2) [from (cite: greve12)]
- External data: Redshift distribution of radio-identified DSFGs for comparison  
  > "radio identified DSFGs which have a significantly lower mean redshift of $\bar z$=2.3" (4.3 The redshift distribution) [from (cite: chapman05; wardlow11)]
- External data: Model dn/dz predictions  
  > "We compare our measured d$n$/d$z$ with four recent models in Figure [10](#Fig:NZ) (*right*)" (4.4 Comparison to models) [from (cite: bethermin12b; lacey10; benson12b; hayward12)]
- Simulation/model as data: Lensing probability vs redshift from halo-population models, used for lensing-bias analysis  
  > "calculated from the models of (cite: hezaveh11) and (cite: hezaveh12b), which use gravitational lensing by a realistic population of intervening halos" (4.2 Redshift biases due to gravitational lensing)

## Processing

### Calibration

- pipeline or manual: Processed with CASA; details not given  
  > "The data were processed using the Common Astronomy Software Application package (cite: mcmullin07; petry12)." (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Mars, Uranus, Neptune, Callisto or Ganymede; passband/phase from nearby quasars  
  > "Flux calibration was performed on planets (Mars, Uranus, or Neptune) or Jupiter’s moons (Callisto or Ganymede), with passband and phase calibration determined from nearby quasars." (2 Observations)
- flux scale uncertainty: 10% absolute calibration for ALMA in SED fits  
  > "an absolute calibration uncertainty of $10\%$ for SPIRE, $15\%$ for LABOCA, $10\%$ for SPT, and $10\%$ for ALMA" (Supplementary Far-Infrared Photometry)
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
- smoothing: Cubes with 19.5 MHz channel width (~50-65 km/s)  
  > "Calibrated data cubes were constructed with a channel width of 19.5 MHz ($\sim50-65$ kms$^{-1}$ for the highest and lowest observing frequency)." (2 Observations)
- final beam: _not stated_
- final rms: 2 mJy/beam per channel; 70 uJy/beam continuum  
  > "Continuum images generated from the full bandwidth have typical noise levels of 70 $\mu$Jy beam$^{-1}$." (2 Observations)

### Inherited from earlier work

- Greybody SED fit (beta=2, optically thin/thick transition 100 um, exclude lambda_rest<50 um)  
  > "For the fitting of the thermal dust continuum we have used the method described in (cite: greve12)" (3.2 Ambiguous cases) [from (cite: greve12)]
- LABOCA observing strategy and data processing  
  > "The observing strategy and data processing are described in (cite: greve12)." (Supplementary Far-Infrared Photometry) [from (cite: greve12)]
- Selection details, flux de-boosting  
  > "the details of which can be found in (cite: vieira10) and (cite: crawford10)" (2 Observations) [from (cite: vieira10; crawford10)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration/imaging task parameters (weighting, cleaning, masks)
- Line-free channels and continuum subtraction method
- Line detection/integration procedure and SNR>5 criteria details
- Gaussian line-fit procedure for redshift uncertainties
- Calibrator names per session
- Exact probability calculation for dust temperature/redshift options
- Intrinsic dn/dz and size-evolution lensing model parameters
- How dn/dz uncertainties and chi2 were computed

## Analysis recipe

1. **Detect continuum and lines**: Build cubes and continuum images; identify line features with integrated SNR>5  
  > "we detect 44 line features with line integrated ${\rm SNR}>5$ in our survey" (3 Results)
   - software: CASA
   - parameter: 19.5 MHz channels  
  > "Calibrated data cubes were constructed with a channel width of 19.5 MHz" (2 Observations)
   - fitting: Gaussian fits to line profiles for redshift uncertainties  
  > "Uncertainties for the redshifts are based on Gaussian fits to the line profiles." (3 Results)
   - validation: _not stated_
2. **Derive redshifts from line identification**: Unique solution from multiple lines; for single lines use additional spectroscopy or SED dust temperature priors  
  > "In this case, a unique redshift solution can be derived from the ALMA 3 mm spectral scans alone." (3 Results)
   - parameter: Retain dust temperatures with probability >10%  
  > "We retain only dust temperatures with probabilities $>$10%" (3.2 Ambiguous cases)
   - assumption: Greybody beta=2, T_dust distribution of known-z sample (mean 37.2+-8.2 K) as prior  
  > "For these sources we find a mean of T$_{\rm dust}$=37.2$\pm$8.2 K and no apparent trend with redshift" (3.2 Ambiguous cases)
   - fitting: Greybody fit with dust luminosity and T_dust free  
  > "where the only free parameters are the dust luminosity and the dust temperature, T$_{\rm dust}$" (3.2 Ambiguous cases)
   - validation: Confirmation with APEX [CII], ATCA, SMA, Z-Spec, VLT for five sources  
  > "The identification of the 98 GHz line as CO(3–2) is confirmed with a CO(1–0) detection using the Australia Telescope Compact Array" (Supplementary redshift information)
3. **Assess selection and lensing biases**: Compare lensing probability and size-evolution scenarios for lensed vs unlensed dn/dz  
  > "we compare an assumed intrinsic redshift distribution to the model distribution of strongly lensed sources" (4.2 Redshift biases due to gravitational lensing)
   - assumption: Average magnification 15  
  > "Adopting an average magnification of $\bar \mu=15$ for the sources studied here" (4.3 The redshift distribution)
   - fitting: _not stated_
   - validation: _not stated_
4. **Build dn/dz and compare with models**: Bin most probable redshifts of 28 sources; compute chi2 against four models with z<1.5 removed  
  > "removing sources at $z$$<$$1.5$ from the models to mimic the strong lensing selection" (4.4 Comparison to models)
   - fitting: chi2 over five redshift bins  
  > "give the $\chi^2$ for each model for the five redshift bins" (4.4 Comparison to models)
   - validation: _not stated_

## Software

- **CASA** : Data processing  
  > "The data were processed using the Common Astronomy Software Application package" (2 Observations)
- **HIPE** v9.0: Herschel SPIRE map reduction  
  > "standard reduction pipeline HIPE v9.0" (Supplementary Far-Infrared Photometry)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean redshift of sample | 3.5 | not stated | dimensionless | 4 | The resulting mean redshift of our sample is $\bar z$=3.5. |
| Lines detected | 44 | not stated | lines | 1 | In total, we detect 44 line features with line integrated ${\rm SNR}>5$ in our survey |
| Detection rate (sources with lines) | 23 of 26 (~90%) | not stated | dimensionless | 1 | We find one or more spectral features in 23 sources yielding a $\sim$$90\%$ detection rate for this survey |
| Mean dust temperature of known-z sample | 37.2 | 8.2 | K | 2 | For these sources we find a mean of T$_{\rm dust}$=37.2$\pm$8.2 K |
| dn/dz in 3.5-4.5 | 0.32 | 0.11 | dimensionless | 4 | / $3.5-4.5$ /         /   9   /          /   0.32    /          / 0.11  / |
| chi2 Bethermin12b model | 1.9 | not stated | dimensionless | 4 | giving a $\chi^2$ of 1.9 across five redshift bins |
| chi2 Benson12b model | 39.8 | not stated | dimensionless | 4 | The $\chi ^2$ between this model and our measurement across the five redshift bins is 39.8. |

## Qualitative findings

- SPT lensed DSFGs have much higher redshifts than radio-identified DSFGs; previous radio-based surveys likely missed >=50% of DSFGs at z>3  
  > "have missed a large fraction ($\ge50$%) of the DSFG population at redshifts $z$$>$3" (5 Summary and Conclusion)

## Claim tuples

- H: Can ALMA 3 mm scans blindly yield redshifts for SPT lensed DSFGs? | E: Spectral scan of 26 sources with five tunings | R: Lines found in 23 sources; 12 with multiple lines | F: High detection rate gives secure redshifts for ~70% | **supported**
- H: SPT DSFGs have a higher redshift distribution than radio-identified DSFGs | E: Compared dn/dz of 28 sources to Chapman et al. | R: Mean z=3.5 vs 2.3 | F: Radio-identified surveys biased low | **supported**
- H: Lensing is not the dominant cause of the dn/dz difference | E: Compared size-evolution scenarios for lensed vs unlensed distributions | R: Differences <~20% at z=2-4 unless extreme size evolution | F: Lensing unlikely to dominate | **partially**
- H: Galaxy formation models can reproduce the measured dn/dz | E: chi2 comparison with four models | R: Bethermin and Hayward match; Benson fails | F: dn/dz discriminates between models | **supported**

## Reasoning

- Why this data: Lensed SPT sources allow CO redshifts with early ALMA  
  > "The magnification of the SPT sources by intervening mass (cite: hezaveh13) has allowed us to obtain these results in the early science phase of ALMA" (5 Summary and Conclusion)
- Why this method: _not stated_
- Alternative: Alternative line IDs (e.g. CO(2-1), CO(5-4)) rejected via T_dust or missing companion lines  
  > "CO(2–1) at $z$=1.007 can be excluded as it would imply T$_{\rm dust}$=13 K." (Supplementary information)
- How they decided it was enough: _not stated_
- Limitation (authors): Eight ambiguous redshifts hamper determination of the distribution shape; small sample  
  > "The determination of the shape of our redshift distribution is currently hampered by the eight ambiguous redshifts." (4.3 The redshift distribution)
- Limitation (authors): Dust temperatures not physical; lensing size-evolution bias cannot be excluded  
  > "the “temperatures” should not be interpreted as physical temperatures" (3.2 Ambiguous cases)
- Caveat (inferred, ours): Redshift distribution depends on assumed T_dust prior for ambiguous sources
- Caveat (inferred, ours): Sample not flux-limited complete due to pointing groups
- Caveat (inferred, ours): Selection vetoes (IRAS, SUMSS) may bias against low-z
- Caveat (inferred, ours): dn/dz errors presumably Poisson, not stated

## Reproducibility

- Data public (paper): ALMA data identified by project code 2011.0.00957.S; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00957.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Calibration and imaging parameters
- Missing: Line-finding procedure
- Missing: Probability computation for T_dust-redshift options
- Missing: Lensing model inputs
- Data volume (inferred): ~tens of GB for Cycle 0 compact data on 26 sources
- Score (inferred): 3/5, Public Cycle 0 data and a clear logic, but processing and line-finding details are sparse.
- Rediscovery candidate: no, Line identification involves non-public follow-up data and unstated procedures, though ALMA data are archival.

## Links

- Method: (cite: greve12) (SED fitting method and LABOCA processing)
- Companion: (cite: vieira13) (Lensing nature of the sources)
- Companion: (cite: hezaveh13) (Lens modeling)
- Related: SPT-SZ survey
- Related: H-ATLAS

## Checks

```json
{
 "quotes": 64,
 "quotes_ok": 64,
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
  "facts": 76,
  "stated": 48,
  "rate": 0.632
 },
 "evidence_ok": true
}
```

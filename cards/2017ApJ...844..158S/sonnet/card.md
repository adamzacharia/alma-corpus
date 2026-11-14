# Dynamical Masses of Low-mass Stars in the Taurus and Ophiuchus Star-forming Regions

`2017ApJ...844..158S` | The Astrophysical Journal 2017 | first author: Simon, M. | arXiv: 1706.03505 | DOI: 10.3847/1538-4357/aa78f1

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation, stellar_physics
- Question: What are the dynamical masses of low-mass PMS stars from disk rotation, and how do they compare with PMS evolutionary models?  
  > "We find 8 stars with masses in the range 0.09 to 1.1 M$_\odot$  that agree well with the current generation of PMS evolutionary models." (abstract)
- Target **L1495 Taurus stars (CY Tau, FP Tau, CX Tau, IP Tau, FM Tau)**: coordinates _not stated_; z/distance 131 pc  
  > "Three stars in L1495 in Taurus have VLBA parallaxes placing its average distance at $131.4\pm 2.4$ pc" (2.1 ALMA Cycle 2: Taurus and Ophiuchus); distance from VLBA parallaxes (Torres et al. 2012)  
  > "Three stars in L1495 in Taurus have VLBA parallaxes placing its average distance at $131.4\pm 2.4$ pc" (2.1 ALMA Cycle 2: Taurus and Ophiuchus)
- Target **L1688 Ophiuchus stars (GSS 26, GSS 39, YLW16C, ROXs 25, YLW 58, Flying Saucer)**: coordinates _not stated_; z/distance 119 pc  
  > "We use their average, $119.4\pm 4.6$ pc for the distance to L1688." (2.1 ALMA Cycle 2: Taurus and Ophiuchus); distance from average of two VLBA parallaxes (Loinard et al. 2008)  
  > "We use their average, $119.4\pm 4.6$ pc for the distance to L1688." (2.1 ALMA Cycle 2: Taurus and Ophiuchus)
- Target **Akeson & Jensen Taurus binaries (14 disks)**: coordinates _not stated_; z/distance 140 pc (GK Tau 131 pc, HO Tau 161 pc)  
  > "Most of the stars in their sample are distributed over the Taurus SFR; we consider 140 pc as their distance." (2.2 ALMA Cycle 0: Taurus); distance from Taurus average; association with L1495 / L1529  
  > "Most of the stars in their sample are distributed over the Taurus SFR; we consider 140 pc as their distance." (2.2 ALMA Cycle 0: Taurus)

## Data provenance

- ALMA projects: 2013.2.00163.S, 2011.0.00150.S, 2013.2.00426.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Oph 0.6x0.4''; Taurus 0.25x0.21''; Cycle 0 CO 2-1 0.85x0.50''  
  > "a higher angular resolution $0.25'' \times 0.21''$ at PA $180^\circ$" (3.1 Observations)
- max recoverable scale: _not stated_
- sensitivity: ~7 mJy/beam (0.6 K) Oph at 0.2 km/s; ~3 K Taurus  
  > "The typical noise is $\sim 7$ mJy/beam (about 0.6 K in brightness) at 0.2 km s$^{-1}$ spectral resolution." (3.1 Observations)
- time on source: _not stated_
- observing dates: Ophiuchus 23 May 2015; Taurus 19 Sept 2015  
  > "The Ophiuchus targets were observed on May 23, 2015" (3.1 Observations)
- pi or archival as stated: Own Cycle 2 program plus archival Akeson & Jensen Cycle 0 and Boehler data  
  > "We also used archival data from (cite: Akeson+Jensen_2014)’s ALMA program" (1 Introduction)
- Line: CO J=2-1 (not stated)
- Line: H2CO 3_13-2_12 (not stated)
- Line: CN N=2-1 (not stated)
- Line: CO J=3-2 (not stated)
- External data: Spectral types, Teff and luminosities of Taurus stars  
  > "Andrews et al. (2013)" (Table 1) [from Andrews et al. 2013; Herczeg & Hillenbrand 2014]
- External data: Ophiuchus stellar parameters  
  > "the stellar parameters are from (cite: Ricci+etal_2010) and (cite: Najita+etal_2015)" (2.1 ALMA Cycle 2: Taurus and Ophiuchus) [from Ricci et al. 2010; Najita et al. 2015]
- External data: BHAC15 evolutionary models  
  > "The figures use evolutionary models calculated by (cite: Baraffe+etal_2015)." (4.1) [from Baraffe et al. 2015]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline in CASA 4.2.2 (Cycle 2); CASA 3.4 for Cycle 0  
  > "We calibrated the data using the ALMA pipeline in the CASA software package (Version 4.2.2)" (3.1 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: Flux scale not reliable; continuum flux not reported  
  > "Quoting reliable uncertainties would imply a proper flux scale calibration which is not reliable in our data set." (3.1 Observations)
- self calibration: Phase-only self-cal from continuum applied to line data  
  > "phase-only self-calibration solutions were derived from the continuum and applied to the spectral line tables." (3.1 Observations)

### Imaging

- task: cvel for LSRK; export via UVFITS to GILDAS  
  > "applied doppler correction using the “cvel” task to transform the data in the LSRK frame." (3.1 Observations)
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
- smoothing: Smoothed to 0.2 km/s spectral resolution  
  > "All data were smoothed to 0.2 km s$^{-1}$ spectral resolution." (3.1 Observations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- DiskFit analysis done exactly as in earlier work  
  > "We analyzed the data for disk parameters using the *DiskFit* tool (cite: Pietu+etal_2007) exactly as in our earlier work (cite: Guilloteau+etal_2014)" (3.2 Analysis) [from Pietu et al. 2007; Guilloteau et al. 2014]

### Not stated but needed to reproduce (our reading)

- Fixed scale height and fixed disk parameter values (T0, q, p, H0, h) per source
- Velocity ranges masked for cloud contamination
- Imaging parameters for GILDAS (weighting, cell, size)
- Stellar coordinates and exact configurations
- Continuum-subtraction details

## Analysis recipe

1. **Calibrate and prepare data**: ALMA pipeline in CASA, cvel to LSRK, export to GILDAS, phase-only self-cal, smooth to 0.2 km/s  
  > "Data were then exported through UVFITS format to the GILDAS package for imaging and data analysis." (3.1 Observations)
   - software: CASA, GILDAS
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit Keplerian disk models in uv plane**: DiskFit truncated power-law flared disk with Keplerian velocity; M*=R0 V0^2/G  
  > "we derive the stellar mass $M_* = R_0 V_0^2 /G$, where $G$ is the gravitational constant." (Method of analysis)
   - software: DiskFit
   - parameter: R_in = 0.1 au; scale height fixed  
  > "$R_{in}$ is set to a small value (0.1 au), and the scale height is kept fixed in the process." (Method of analysis)
   - assumption: Distances 131 pc (L1495), 119 pc (L1688), 140 pc Taurus average  
  > "We assumed that the entire sample is associated with L1495 at its distance of 131 pc (Col. 3)." (3.2 Analysis)
   - fitting: chi2 minimization with modified Levenberg-Marquardt; errors from covariance matrix  
  > "minimized using a modified Levenberg-Marquardt method, and the errorbars are derived from the covariance matrix." (Method of analysis)
   - validation: MCMC in several cases; consistency between continuum and line inclinations, repeated observations and lines  
  > "The validity of the errorbars was further assessed by running Monte Carlo Markov Chain (MCMC) in several cases" (Method of analysis)
3. **Compare masses with evolutionary tracks on HRD**: Place stars on HRD / L/M^2 diagram with BHAC15 and F16 tracks; error ellipse distance to track of measured mass; derive ages  
  > "We estimate the level of agreement by the distance in the HRD plane between the error ellipse and the evolutionary track corresponding to the measured absolute mass." (4.1)
   - assumption: Tracks have no uncertainty  
  > "This approach assumes that the tracks have no uncertainty" (4.1)
   - fitting: _not stated_
   - validation: Compared BHAC15 with F16 non-magnetic models  
  > "Given the similarity of the F16 and BHAC15 models we will continue to apply the BHAC15 models to our mass measurements." (4.1)

## Software

- **CASA** 4.2.2 (Cycle 2); 3.4 (Cycle 0): Calibration and cvel  
  > "We processed data for both lines as above using CASA 3.4 software" (3.1 Observations)
- **GILDAS** : Imaging and data analysis  
  > "exported through UVFITS format to the GILDAS package for imaging and data analysis" (3.1 Observations)
- **DiskFit** : Disk model fitting in uv plane  
  > "We analyzed the data for disk parameters using the *DiskFit* tool" (3.2 Analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CY Tau mass | 0.31 | 0.02 | Msun | 2 | CY Tau        / 131  / CO, CN        / $7.27\pm0.03$   / $30\pm2$     / $32\pm1$     / $290\pm10$ / $0.31\pm0.02$ |
| GSS 26 mass | 1.51 | 0.02 | Msun | 2 | $325\pm5$  / $1.51\pm0.02$ |
| YLW 58 mass | 0.09 | 0.01 | Msun | 2 | $130\pm3$  / $0.09\pm0.01$ |
| Flying Saucer mass | 0.58 | 0.01 | Msun | 2 | $200\pm7$  / $0.58\pm0.01$ |
| FV Tau A mass | 2.30 | 0.17 | Msun | 2 | $57\pm2$   / $2.30\pm0.17$ |
| HK Tau A inclination | 51 | 2 | deg | 2 | $i_{A, line}=51\pm 2^\circ$ |

## Qualitative findings

- CN emission in L1688 heavily contaminated by molecular cloud absorption except Flying Saucer  
  > "the N=2-1 line emission is heavily contaminated by apparent absorption from the molecular cloud, except for the Flying Saucer" (5.4)

## Claim tuples

- H: Do PMS evolutionary models agree with absolute dynamical masses? | E: Compare measured masses with BHAC15/F16 tracks on HRDs | R: 8 stars agree within 1 sigma over 0.09-1.1 Msun at ages <3 MY | F: Models agree well where Teff reliable; discrepancies likely due to Teff | **supported**
- H: Are the large masses in the AJ14 sample consistent with their L and Teff? | E: Measure masses and plot on L/M^2 diagram | R: 7 stars have too-small L/M^2 | F: Likely unresolved binaries or multiples | **partially**
- H: Are L1688 stars younger than Taurus stars? | E: HRD positions with BHAC15 | R: Taurus 1-3 MY; L1688 <1 MY | F: Ophiuchus younger | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Cloud contamination limits CO and CN usability; Teff uncertainties limit comparison  
  > "A very serious obstacle for mass determination by the rotation of the host star’s circumstellar disk is contamination of the disk line emission by molecular clouds along the line of sight." (5.4)
- Caveat (inferred, ours): Distance uncertainty not propagated into masses
- Caveat (inferred, ours): Fits rely on fixed scale height and assumed disk model
- Caveat (inferred, ours): No imaging parameters given

## Reproducibility

- Data public (paper): Archival data (AJ14) reprocessed; project codes listed  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00150.S," (Acknowledgments)
- Products in archive: _not stated_
- Missing: Per-source fixed disk parameters and masks
- Missing: GILDAS imaging settings
- Missing: Teff/L uncertainty private communications
- Data volume (inferred): ~100-300 GB raw across three projects
- Score (inferred): 5/5, Data public and method named, but fitting setup details and the inherited DiskFit recipe are only partly given.
- Rediscovery candidate: no, Recipe depends on earlier papers and unstated fit settings.

## Links

- Method: Pietu et al. 2007 (DiskFit)
- Method: Guilloteau et al. 2014 (analysis procedure followed)
- Companion: Akeson & Jensen 2014 (source of Cycle 0 data)

## Checks

```json
{
 "quotes": 52,
 "quotes_ok": 52,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2013.2.00163.S",
  "2013.2.00426.S"
 ],
 "obscore_codes_not_in_card": [
  "2013.1.00163.S",
  "2013.1.00426.S"
 ],
 "codes_printed_but_missing": [
  "2012.2.00163.S"
 ],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 35,
  "rate": 0.5
 },
 "evidence_ok": true
}
```

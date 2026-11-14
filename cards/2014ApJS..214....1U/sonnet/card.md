# Cold Molecular Gas in Merger Remnants. I. Formation of Molecular Gas Disks

`2014ApJS..214....1U` | The Astrophysical Journal Supplement Series 2014 | first author: Ueda, Junko | arXiv: 1407.6873 | DOI: 10.1088/0067-0049/214/1/1

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies
- Question: Do merger remnants host rotating molecular gas disks, how large are they relative to the stellar component, and is this consistent with simulations of gas-rich mergers?  
  > "In order to check this theoretical prediction and to investigate the evolution of galaxies after a merging event, we have conducted a $^{12}$CO imaging study of merger remnants in the local Universe" (1 Introduction)
- Target **37 optically-selected merger remnants (drawn from Rothberg & Joseph 2004), e.g. NGC 34, Arp 230, NGC 3256, NGC 7252**: coordinates listed per source in Table 1 (J2000)  
  > "Our sample is drawn from the merger remnant sample studied by (cite: Rothberg04), which is a large-scale observational study of 51 merger remnants in the local Universe ($<$ 200 Mpc)." (2 Sample Sources); z/distance luminosity distances 13.6-182.1 Mpc (Table 1); H0 = 73 km/s/Mpc  
  > "Our sample is drawn from the merger remnant sample studied by (cite: Rothberg04), which is a large-scale observational study of 51 merger remnants in the local Universe ($<$ 200 Mpc)." (2 Sample Sources); distance from derived from systemic velocity with LCDM, Omega_M=0.3, Omega_L=0.7, H0=73  
  > "Our sample is drawn from the merger remnant sample studied by (cite: Rothberg04), which is a large-scale observational study of 51 merger remnants in the local Universe ($<$ 200 Mpc)." (2 Sample Sources)

## Data provenance

- ALMA projects: 2011.0.00099.S, 2011.0.00002.SV
- bands: CO(1-0) at ~115 GHz (Band 3, 3 mm continuum)  
  > "The $^{12}$CO ($J$ = 1–0) observations for 20 galaxies (see Table [2](#tab:t2)) were carried out during the ALMA Cycle 0 period." (4.1 Interferometric Observations with ALMA)
- frequencies and spectral setup: four spectral windows, each 1.875 GHz bandwidth, 488 kHz resolution  
  > "The correlator was configured to have four spectral windows, each with 1.875 GHz bandwidth and 488 kHz frequency resolution." (4.1 Interferometric Observations with ALMA)
- continuum bandwidth: _not stated_
- arrays: 16-24 12 m antennas  
  > "The number of 12 m antennas was 16 – 24 depending on observation." (4.1 Interferometric Observations with ALMA)
- configurations: compact for Arp 230, AM 0956-282, NGC 7727; extended for the other 17  
  > "We used the compact configuration for the three nearby galaxies (Arp 230, AM 0956-282, and NGC 7727) and the extended configuration for the other 17 galaxies to achieve $\lesssim$ 1 kpc spatial resolution." (4.1 Interferometric Observations with ALMA)
- baselines: _not stated_
- angular resolution: 1.2'' to 4.1'' (robust=0.5)  
  > "The synthesized beam sizes range between 1.2$''$ and 4.1$''$ by adopting briggs weighting of the visibilities (robust = 0.5)." (4.1 Interferometric Observations with ALMA)
- max recoverable scale: _not stated_
- sensitivity: rms 1.78-5.26 mJy/beam at 20 km/s  
  > "The achieved rms noise levels in the velocity resolution of 20 km s$^{-1}$ are 1.78 – 5.26 mJy beam$^{-1}$." (4.1 Interferometric Observations with ALMA)
- time on source: _not stated_
- observing dates: Cycle 0, Nov 2011 - July 2012  
  > "| 4 | NGC 455 | CO (1–0) | ALMA | 20 | 2.07 | 2.07 | 1.58 $\times$ 1.23 | July 2012 |" (Table 2)
- pi or archival as stated: _not stated_
- Line: 12CO J=1-0 (ALMA, CARMA, PdBI, NRO), 2-1 (SMA), 3-2 (SMA) (not stated)
- Other facility **SMA**: CO(2-1) for five galaxies (new data) plus archival  
  > "The $^{12}$CO ($J$ = 2–1) observations for five galaxies (NGC 828, UGC 2238, UGC 9829, NGC 6052, and UGC 10675) were carried out using the SMA in June and October 2011." (4.2 SMA)
- Other facility **CARMA**: CO(1-0) for UGC 6 and UGC 4079  
  > "The $^{12}$CO ($J$ = 1–0) observations for two galaxies (UGC 6 and UGC 4079) were carried out using the CARMA in January and February 2011." (4.3 CARMA)
- Other facility **NRO 45 m**: single-dish CO(1-0) for total flux and gas mass  
  > "The $^{12}$CO ($J$ = 1–0) observations were carried out using the NRO 45 m telescope for 10 galaxies (see Table [5](#tab:t5)) during 2011 – 2012." (4.5 Single-dish)
- Other facility **PdBI**: archival CO(1-0) for NGC 2782 and NGC 4441  
  > "two galaxies (NGC 2782 and NGC 4441) were observed using the PdBI (cite: Hunt08; Jutte10)" (4.4 Archival Interferometric Data)
- External data: Optical/K-band sample properties (R_eff, Sersic index, K magnitude) used to define sample and size ratios  
  > "We estimate the ratio of $R_{80}$ to the $K$-band effective radius ($R_{\rm eff}$; Table [1](#tab:t1))" (5.3 Comparison) [from (cite: Rothberg04)]
- External data: Archival SMA CO data for seven galaxies  
  > "seven galaxies (see Table [3](#tab:t3)) were observed using the SMA (cite: Wilson08)" (4.4 Archival Interferometric Data) [from (cite: Wilson08)]
- External data: Archival single-dish CO(1-0) data for 16 galaxies  
  > "In addition, we gather archival single-dish CO (1–0) data for 16 galaxies." (4.5 Single-dish) [from (cite: Mirabel90; Casoli92; Sanders91; Young95; Zhu99 etc.)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 5% ALMA; 20% SMA and CARMA  
  > "The uncertainty of flux calibration is 5 %." (4.1 Interferometric Observations with ALMA)
- self calibration: _not stated_

### Imaging

- task: CASA (ALMA); MIRIAD (SMA, CARMA)  
  > "We imaged the calibrated visibility data using the Common Astronomy Software Applications package (CASA)." (4.1 Interferometric Observations with ALMA)
- deconvolver: _not stated_
- weighting robust: briggs robust = 0.5 (ALMA); natural (SMA, CARMA)  
  > "The synthesized beam sizes range between 1.2$''$ and 4.1$''$ by adopting briggs weighting of the visibilities (robust = 0.5)." (4.1 Interferometric Observations with ALMA)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum maps made from line-free channels  
  > "In addition, we made the continuum maps using the line free channels." (4.1 Interferometric Observations with ALMA)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: cube smoothed spatially and in velocity, clipped at 1.5 sigma (ALMA Cycle 0), 5 sigma (NGC 3256), 2 sigma (others) per channel  
  > "The cleaned image cube was smoothed both spatially and in velocity and then this cube was clipped at the 1.5 $\sigma$ level per channel for 20 galaxies observed with ALMA (Cycle 0)" (5.1 Distribution and Kinematics)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- SMA archival CO data (NGC 1614, NGC 2623, UGC 5101, UGC 8058, Arp 193) taken as published  
  > "| 9 | NGC 1614 | CO (2–1) | SMA | 40 | 11.2 | 15.8 | 3.67 $\times$ 3.33 | (cite: Wilson08) |" (Table 3) [from (cite: Wilson08)]
- Gas mass equations for CO luminosity  
  > "The molecular gas mass ($M_{\rm H_{2}}$) is estimated from the CO integrated intensity using the following two equations (cite: Carilli13; Casey14)" (4.6 Molecular Gas Mass) [from (cite: Carilli13; Casey14)]
- alpha_CO = 4.8 for L_FIR<1e11, 0.8 for U/LIRGs  
  > "using the conversion factor of $\alpha_{\rm CO}$ = 4.8 (cite: Solomon91), and we use $\alpha_{\rm CO}$ = 0.8 (cite: Downes98) for the 14 U/LIRGs." (4.6 Molecular Gas Mass) [from (cite: Solomon91; Downes98)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges and CASA imaging parameters (cell, image size, clean threshold, masks) per galaxy
- CASA/pipeline version and calibrators used for ALMA Cycle 0 calibration
- Exact smoothing kernels used in AIPS MOMNT
- Details of GAL ring fitting (ring widths, fixed parameters)
- How R_CO (maximum extent) was defined numerically
- Which SMA/CARMA project codes and calibration details

## Analysis recipe

1. **Image CO cubes and 3 mm continuum**: CASA imaging of ALMA data (briggs robust 0.5); MIRIAD for SMA/CARMA; continuum from line-free channels  
  > "We imaged the calibrated visibility data using the Common Astronomy Software Applications package (CASA)." (4.1 Interferometric Observations with ALMA)
   - software: CASA, MIRIAD
   - parameter: velocity resolution 20 km/s for ALMA  
  > "The achieved rms noise levels in the velocity resolution of 20 km s$^{-1}$ are 1.78 – 5.26 mJy beam$^{-1}$." (4.1 Interferometric Observations with ALMA)
   - fitting: _not stated_
   - validation: _not stated_
2. **Make moment maps and velocity fields**: smooth and clip cube with AIPS MOMNT  
  > "They were made by smoothing and clipping the intensity using the AIPS task, MOMNT." (5.1 Distribution and Kinematics)
   - software: AIPS
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit rotating disk to velocity fields**: tilted concentric ring models fitted with AIPS GAL, center fixed at K-band peak  
  > "We fit tilted concentric ring models to the velocity field using least-squares fitting routine for the kinematical parameters and a default convergence condition." (6.1 Molecular Gas Disks)
   - software: AIPS GAL
   - assumption: gas rotates around the K-band emission peak  
  > "The galactic center is defined by the emission peak of the $K$-band image (RJ04), and we assume that the molecular gas rotates around the galactic center." (6.1 Molecular Gas Disks)
   - fitting: least-squares  
  > "We fit tilted concentric ring models to the velocity field using least-squares fitting routine" (6.1 Molecular Gas Disks)
   - validation: fit converged for 24/30; PV diagrams along kinematic major axis  
  > "The fitting routine converged for 24 out of the 30 galaxies." (6.1 Molecular Gas Disks)
4. **Derive molecular gas masses**: L'CO from integrated flux, M_H2 = alpha_CO L_CO; high-J converted with ratio 0.5  
  > "we convert the high-$J$ CO luminosity into the CO (1–0) luminosity, assuming that the CO (3–2)/CO (1–0) and the CO (2–1)/CO (1–0) brightness temperature ratio is 0.5" (4.6 Molecular Gas Mass)
   - assumption: alpha_CO = 4.8 (L_FIR<1e11) or 0.8 (U/LIRGs)  
  > "using the conversion factor of $\alpha_{\rm CO}$ = 4.8 (cite: Solomon91), and we use $\alpha_{\rm CO}$ = 0.8 (cite: Downes98) for the 14 U/LIRGs." (4.6 Molecular Gas Mass)
   - fitting: _not stated_
   - validation: compared interferometric vs single-dish masses and recovered flux  
  > "We estimate the recovered flux for 18 galaxies, comparing the flux of the same CO transition in the same region measured from the interferometric maps with the single-dish spectra." (4.3 Single-dish)
5. **Measure gas disk sizes and compare to stellar size**: R_CO and R_80 (80% of CO flux) from integrated intensity maps, corrected for PA and inclination for Type A; ratio R_80/R_eff  
  > "$R_{\rm CO}$ is the radius from the galactic center that encloses the maximum extent of the molecular gas disk, and $R_{80}$ is the radius from the galactic center which contains 80 % of the total CO flux." (6.2 The Extent of the Molecular Gas)
   - fitting: _not stated_
   - validation: checked radii against 1-sigma mass sensitivity for correlation  
  > "The absence of an obvious systematic correlation allows us to argue that the detection limit does not strongly affect the observed size of the molecular gas." (6.2 The Extent of the Molecular Gas)

## Software

- **CASA** : imaging ALMA visibilities  
  > "We imaged the calibrated visibility data using the Common Astronomy Software Applications package (CASA)." (4.1 Interferometric Observations with ALMA)
- **MIRIAD** : SMA and CARMA imaging  
  > "Data inspection and imaging were carried out using the MIRIAD package." (4.3 CARMA)
- **MIR** : SMA data inspection  
  > "Data inspection was carried out using the IDL-based SMA calibration tool MIR" (4.2 SMA)
- **AIPS (MOMNT, GAL)** : moment maps and ring kinematic fits  
  > "we apply a fitting program (AIPS’s task GAL) to the CO velocity fields of the 30 galaxies detected in the CO line." (6.1 Molecular Gas Disks)
- **NEWSTAR** : NRO 45 m data reduction  
  > "Data reduction was carried out using the AIPS-based NRO calibration tool NEWSTAR." (4.5 Single-dish)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| fraction of detected sources with rotating gas disks | 80% (24/30) | not stated | percent | 3 | we find that 80 % (24/30) of the sample show kinematical signatures of rotating molecular gas disks |
| molecular gas disk size R_CO range | 1.1 to 9.3 | not stated | kpc | 5 | The sizes of the molecular gas disks ($R_{\rm CO}$) vary significantly from 1.1 kpc to 9.3 kpc with an average of 3.5$\pm$2.3 kpc. |
| average R_80 | 1.5 | 0.8 | kpc | 5 | the average $R_{80}$ of the molecular gas disks is 1.5$\pm$0.8 kpc |
| fraction of disks more compact than K-band R_eff | 54% (13/24) | not stated | percent | 5 | We find that the molecular gas disks in 54 % (13/24) of the sources are more compact than the $K$-band effective radius. |
| R_80 of Milky Way | 8.5 | 0.5 | kpc | 5 | we find that $R_{\rm 80, MW}$ is 8.5$\pm$0.5 kpc |
| sources with PV peaks offset from centre | 18/24 | not stated | count | 3 | The PV diagrams reveal that the emission peaks are clearly shifted from the galactic centers in 18/24 galaxies |
| molecular gas mass range | 1e7 to 1e11 | not stated | Msun | 4 | The molecular gas mass in the sample of merger remnants ranges between 10$^{7}$ $M_{\ensuremath{\odot}}$ and 10$^{11}$ $M_{\ensuremath{\odot}}$. |
| 3 mm continuum detections | 14 of 21 ALMA galaxies; fluxes 0.54-27.5 mJy | not stated | mJy | 1 | The 3 mm continuum emission was detected in 14 out of 21 galaxies observed using ALMA. |

## Qualitative findings

- Both compact and extended molecular gas disks are common in merger remnants; no remnant has a gas disk less concentrated than the Milky Way's  
  > "There is no merger remnant in the present sample which has a less concentrated molecular gas disk than the gas disk in the Milky Way." (6.2 The Extent of the Molecular Gas)

## Claim tuples

- H: Do merger remnants commonly host rotating molecular gas disks? | E: Ring-model fits to CO velocity fields of 30 detected remnants | R: 24/30 fit successfully; 18/24 show PV peak offsets | F: Rotating disks (incl. rings) are common in remnants | **supported**
- H: Are gas disks compact or extended relative to the stellar component? | E: Compare R_80 to K-band R_eff | R: 54% compact, 46% extended | F: Both populations exist, consistent with simulations that mergers can produce early- and late-type galaxies | **supported**
- H: Does gas disk size depend on FIR luminosity (starburst/AGN activity)? | E: Compare R_ratio vs L_FIR | R: no relation | F: Extended disk formation is unrelated to starburst/AGN activity | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Exponential disk fits mostly failed, so R_CO and R_80 were used  
  > "We chose this method because most of our attempts to fit an exponential disk were unsuccessful." (6.2 The Extent of the Molecular Gas)
- Alternative: Exponential disk fits to radial profiles were unsuccessful  
  > "We chose this method because most of our attempts to fit an exponential disk were unsuccessful." (6.2 The Extent of the Molecular Gas)
- How they decided it was enough: _not stated_
- Limitation (authors): Assumed uniform CO line ratio and alpha_CO give uncertain masses; interferometric masses sometimes exceed single-dish  
  > "We use a uniform line ratio for all sources, but there is an uncertainty in this assumed line ratio" (4.6 Molecular Gas Mass)
- Caveat (inferred, ours): Mixed CO transitions (1-0, 2-1, 3-2) and resolutions may bias R_80
- Caveat (inferred, ours): Heterogeneous beam sizes (up to 7.6'') against kpc-scale disks; missing flux in interferometric maps
- Caveat (inferred, ours): Fixed K-band center and low inclination fits give uncertain kinematics
- Caveat (inferred, ours): Fractions 54%/46% have small-number uncertainties not quantified

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: CO data products of 17 remnants to be released on a website  
  > "The CO data products of 17 merger remnants which we observed will be publicly released on the website" (7 Summary)
- Missing: Per-source CASA imaging scripts and calibration details
- Missing: SMA/CARMA project codes
- Missing: Archive SMA data (PI Wang, PI Aalto) access details
- Data volume (inferred): ~100-300 GB for ALMA Cycle 0 raw data of 20 sources plus SV
- Score (inferred): 3/5, ALMA project codes are given and analysis is simple, but imaging and fitting details are sparse and many data are non-ALMA.
- Rediscovery candidate: no, Data partly non-public and processing details incomplete, though the main results are numeric.

## Links

- Method: (cite: Rothberg04) (Parent sample, K-band R_eff and Sersic indices)
- Companion: Ueda et al., in prep. (Paper II) (Molecular gas mass and comparison with early/late-type galaxies)
- Related: Rothberg & Joseph 2004 merger remnant sample

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 48,
  "rate": 0.608
 },
 "evidence_ok": true
}
```

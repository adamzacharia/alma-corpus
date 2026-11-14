# The JCMT Transient Survey: An Extraordinary Submillimeter Flare in the T Tauri Binary System JW 566

`2019ApJ...871...72M` | The Astrophysical Journal 2019 | first author: Mairs, Steve | arXiv: 1812.00016 | DOI: 10.3847/1538-4357/aaf3b1

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, protoplanetary_disks
- Question: Is the extraordinary submillimetre brightening of JW 566 seen by JCMT SCUBA-2 a short-lived non-thermal stellar flare, and how luminous is it?  
  > "In this paper, we present the detection of a submillimeter-wavelength outburst from the YSO JW 566 in Orion, discovered in our the JCMT-Transient sub-mm monitoring program of nearby star-forming regions" (Introduction)
- Target **JW 566**: coordinates RA, Dec = 5:35:17.94, -5:16:11 (J2000)  
  > "the T Tauri binary system JW 566 (R.A., Decl. = 5:35:17.94,$-5$:16:11, J2000)" (Summary); "We adopt a distance of 389 pc to JW 566 due to its proximity with the Orion Nebula Cluster." (5 Discussion, footnote 5); z/distance 389 pc  
  > "the T Tauri binary system JW 566 (R.A., Decl. = 5:35:17.94,$-5$:16:11, J2000)" (Summary); "We adopt a distance of 389 pc to JW 566 due to its proximity with the Orion Nebula Cluster." (5 Discussion, footnote 5); distance from Adopted from Kounkel et al. 2018 (VLBA and Gaia DR2), based on proximity to the Orion Nebula Cluster  
  > "the T Tauri binary system JW 566 (R.A., Decl. = 5:35:17.94,$-5$:16:11, J2000)" (Summary); "We adopt a distance of 389 pc to JW 566 due to its proximity with the Orion Nebula Cluster." (5 Discussion, footnote 5)

## Data provenance

- ALMA projects: 2015.1.00669.S
- bands: 3 mm continuum (ALMA); SCUBA-2 450 and 850 um  
  > "The source is detected in a 3 $\mathrm{\:mm}$ continuum image obtained by ALMA on 2015-12-26" (5.1 Previous Observations of JW 566)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: SCUBA-2 beams 9.8'' (450 um) and 14.6'' (850 um)  
  > "with beam sizes of $9.8\ensuremath{''}$ and $14.6\ensuremath{''}$, respectively" (2.1 SCUBA-2 Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: SCUBA-2 flare observation 31.12 min integration  
  > "within the 31.12 minute integration of 2016-11-26" (4.3 Minute to Minute Variability at 850 um)
- observing dates: ALMA 3 mm continuum observed 2015-12-26; SCUBA-2 flare epoch 2016-11-26  
  > "The source is detected in a 3 $\mathrm{\:mm}$ continuum image obtained by ALMA on 2015-12-26" (5.1 Previous Observations of JW 566)
- pi or archival as stated: ALMA data from Hacar et al. 2018, used as archival  
  > "((cite: hacar2018); see Figure [6](#fig:ALMA))" (5.1 Previous Observations of JW 566)
- Other facility **JCMT SCUBA-2 (Transient Survey, M16AL001)**: Simultaneous 450 and 850 um monitoring that detected the flare  
  > "Each region is observed with SCUBA-2 (cite: holland2013) at 450 $\mu$m$\,$ and 850 $\mu$m$\,$ simultaneously" (2.1 SCUBA-2 Observations)
- Other facility **JCMT Gould Belt Survey**: 2011 SCUBA-2 co-add non-detection and HARP 12CO map  
  > "The source is also not detected in the co-add of the SCUBA-2 images obtained by the JCMT Gould Belt Survey" (4.1 Detecting the flare at 850 um)
- External data: ALMA 3 mm flux of 0.6 mJy for JW 566 (SNR 5.7)  
  > "The 3 mm flux is measured to be $0.6 \mathrm{\:mJy}$, yielding a SNR of 5.7." (5.1 Previous Observations of JW 566) [from (cite: hacar2018)]
- External data: Stellar radius 2.5 Rsun, K7+M1.5 binary, 0.86'' separation  
  > "Constraining the angular scale to a stellar radius of $R_{\star} = 2.5\mathrm{\:R}_{\odot}$ (cite: daemgen2012)" (5.2 The Nature of JW 566's Flare) [from (cite: daemgen2012)]
- External data: Disk spectral index ~2.3  
  > "a spectral index of $\sim2.3$ (cite: ricci2010)" (5.1 Previous Observations of JW 566) [from (cite: ricci2010)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10% at 850 um; 15% at 450 um, combined to 21% for JW 566 with negative-bowl uncertainty  
  > "We adopt the JCMT standard flux uncertainty value of $10\%$ for 850 $\mu$m$\,$ observations" (2.2 Data Reduction and Flux Uncertainties)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 2'' pixels at 450 um, 3'' pixels at 850 um  
  > "The images are constructed using $2\ensuremath{''}$ pixels at 450 $\mu$m$\,$ and $3\ensuremath{''}$ pixels at 850 $\mu$m." (2.1 SCUBA-2 Observations)
- image size: _not stated_
- masking: External mask adjusted to include JW 566; spatial filter suppressing scales >200''  
  > "The external mask was therefore adjusted to include the bright event associated with JW 566 and the data reduction was re-run for all epochs" (2.2 Data Reduction and Flux Uncertainties)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Gaussian kernels FWHM 4'' (450 um) and 6'' (850 um)  
  > "the images are smoothed with Gaussian kernels with FWHM values of $4\ensuremath{''}$ and $6\ensuremath{''}$ at 450 $\mu$m$\,$ and 850 $\mu$m" (Footnote 1)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- JCMT Transient Survey reduction and calibration (reduction R3, no relative flux calibration)  
  > "(reduction *R3* with no relative flux calibration applied[^1])" (2.2 Data Reduction and Flux Uncertainties) [from Mairs et al. 2017 (cite: mairs2017)]
- Source detection method (FellWalker via PICARD)  
  > "Following the methods of (cite: johnstone2018)" (3 Searching for Variability of Faint Sources) [from (cite: johnstone2018)]
- ALMA data reduction and 3 mm flux  
  > "((cite: hacar2018); see Figure [6](#fig:ALMA))" (5.1 Previous Observations of JW 566) [from (cite: hacar2018)]

### Not stated but needed to reproduce (our reading)

- ALMA data processing, CASA version, imaging parameters and how the 0.6 mJy flux was measured
- ALMA array configuration, beam and rms
- Exact FellWalker parameters
- Details of the mask used in re-reduction
- Time boundaries of the nine sub-integrations
- Identity of the 5 non-varying comparison sources

## Analysis recipe

1. **Reduce SCUBA-2 data and make residual maps**: Iterative map-making with stringent spatial filter and adjusted mask; subtract co-add of other epochs from the flare epoch  
  > "all Transient Survey epochs, excluding 2016-11-26 (the date of the flare event), were then co-added and subtracted from the 2016-11-26 data" (2.2 Data Reduction and Flux Uncertainties)
   - software: SMURF, Starlink
   - fitting: _not stated_
   - validation: _not stated_
2. **Detect the candidate transient**: Run source detection on each epoch and compare with the co-add catalogue  
  > "we compare the catalogues generated for each epoch with the catalogue generated for the co-add and identify sources that appeared in individual observations" (3 Searching for Variability of Faint Sources)
   - software: PICARD, FellWalker
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure fluxes and minute-scale light curve**: 2D Gaussian fit to residual maps at both wavelengths; raw data split into nine intervals  
  > "is fit with a 2-dimensional Gaussian profile to measure the source peak" (4.3 Minute to Minute Variability at 850 um)
   - fitting: 2D Gaussian  
  > "A 2-dimensional Gaussian profile fit to the residual 450 $\mu$m$\,$ image yields a source peak of $500\pm107\mathrm{\:mJy\:beam}^{-1}$" (Detecting the flare at 450 μm)
   - validation: Compared with 5 non-varying sources (std 9.7% vs 23.2% for JW 566)  
  > "The average standard deviation of the non-varying sources is 9.7%." (4.3 Minute to Minute Variability at 850 um)
4. **Derive spectral index, luminosity and brightness temperature**: Two-point spectral index; Tb from change in flux over light crossing time; luminosity at 389 pc  
  > "This results in a brightness temperature of $T_{b} \sim 6\times10^{4}\mathrm{\:K}$ and a light crossing distance of 3.3 AU." (5.2 The Nature of JW 566's Flare)
   - assumption: Distance 389 pc; stellar radius 2.5 Rsun for upper Tb limit  
  > "$D$ is the distance to the source (389 pc)" (5.2 The Nature of JW 566's Flare)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **SMURF** : SCUBA-2 iterative map-making  
  > "The data reduction was carried out using the iterative map-making software" (2.2 Data Reduction and Flux Uncertainties)
- **Starlink** : Reduction package including SMURF and PICARD  
  > "starlink (cite: currie2014)" (Software)
- **PICARD** : Running source detection (FellWalker)  
  > "found in ’s package (cite: sun265)" (3 Searching for Variability of Faint Sources)
- **astropy** : Listed in software  
  > "astropy (cite: astropy), matplotlib (cite: matplotlib), aplpy (cite: aplpy)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 850 um flux averaged over observation | 466 | 47 | mJy/beam | 3 | $466\pm47\mathrm{\:mJy\:beam}^{-1}$ at 850 $\mu$m |
| 450 um flux averaged over observation | 500 | 107 | mJy/beam | 3 | $500\pm107\mathrm{\:mJy\:beam}^{-1}$ at 450 $\mu$m |
| Spectral index 450-850 um | 0.11 | 0.49 | dimensionless | 4 | of $\alpha = 0.11\pm0.49$ over these wavelengths |
| Radio luminosity at 850 um | 8e19 | not stated | erg/s/Hz | 4 | corresponds to a radio luminosity of $L_\nu= 8\times10^{19}\mathrm{\:erg\:s^{-1}\:Hz^{-1} }$ |
| Brightness temperature (light crossing) | 6e4 | not stated | K | 4 | $T_{b} \sim 6\times10^{4}\mathrm{\:K}$ |
| ALMA 3 mm flux (from Hacar et al.) | 0.6 | not stated | mJy | 0 | The 3 mm flux is measured to be $0.6 \mathrm{\:mJy}$, yielding a SNR of 5.7. |
| Initial and final 850 um peak in light curve | 773 to 400 | not stated | mJy/beam | 3 | with an initial peak of $773\mathrm{\:mJy\:beam}^{-1}$ that drops to $400\mathrm{\:mJy\:beam}^{-1}$ by the end of the observation |

## Qualitative findings

- Possibly the most luminous known YSO flare and the first coronal flare discovered at sub-mm wavelengths  
  > "The event may be the most luminous known flare associated with a young stellar object and is also the first coronal flare discovered at sub-mm wavelengths." (abstract)

## Claim tuples

- H: The JW 566 sub-mm brightening is a short-lived, non-thermal flare | E: Light curve in nine sub-intervals, 2-band spectral index, brightness temperature | R: Flux fell from 773 to 400 mJy/beam in 31 min; alpha = 0.11; Tb > 6e4 K | F: Gyrosynchrotron/synchrotron emission from magnetic reconnection | **supported**
- H: The flare is exceptionally luminous compared with other YSO flares | E: Compared Lnu at 850 um with GMR-A at 86 GHz | R: 8e19 vs 3e19 erg/s/Hz, about an order of magnitude greater in nuLnu | F: Possibly the most luminous YSO flare known | **partially**
- H: The quiescent emission of JW 566 is faint | E: Used ALMA 3 mm flux and extrapolated to 850 um | R: 3 mm flux of 0.6 mJy implies a disk 850 um flux of ~10 mJy | F: The flare is hundreds of times brighter than quiescent emission | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Reprocessed accretion luminosity through thermal dust emission ruled out by short decay timescale  
  > "The short timescale for the decay of the flare rules out reprocessed accretion luminosity through thermal dust emission in the envelope" (Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): True flare timescale unknown; no simultaneous data at other wavelengths; no polarimetry  
  > "The true timescale of the flare remains unknown, as there are no data available at other wavelengths during the time of our observation." (Summary)
- Caveat (inferred, ours): Single event; the 450 um detection is only SNR 6
- Caveat (inferred, ours): Brightness temperature range spans five orders of magnitude
- Caveat (inferred, ours): ALMA data play only a minor, quiescent-flux role
- Caveat (inferred, ours): Possible CO(3-2) contamination of the 850 um band argued negligible using a coarse map

## Reproducibility

- Data public (paper): ALMA data identified by project code; JCMT data from archive (target OMC2-3)  
  > "The target identifier in the JCMT archive is OMC2-3." (Table 1 notes)
- Products in archive: _not stated_
- Missing: Exact mask and map-making configuration
- Missing: ALMA flux measurement details
- Missing: Sub-interval boundaries
- Data volume (inferred): SCUBA-2 raw data for ~20 epochs (tens of GB); ALMA 3 mm small (a few GB)
- Score (inferred): 3/5, SCUBA-2 recipe is partly described but depends on Starlink and prior-paper settings; ALMA part is minor and not described.
- Rediscovery candidate: no, Main data are JCMT, ALMA is a minor ancillary measurement, and reduction details are missing.

## Links

- Method: Mairs et al. 2017 (cite: mairs2017) (JCMT Transient Survey data reduction and calibration)
- Method: Johnstone et al. 2018 (cite: johnstone2018) (Source detection and variability method)
- Companion: Herczeg et al. 2017 (cite: herczeg2017) (JCMT Transient Survey overview)
- Companion: Hacar et al. 2018 (cite: hacar2018) (Source of ALMA 3 mm data)
- Related: JCMT Transient Survey (M16AL001)
- Related: JCMT Gould Belt Survey

## Checks

```json
{
 "quotes": 52,
 "quotes_ok": 52,
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
  "facts": 71,
  "stated": 36,
  "rate": 0.507
 },
 "evidence_ok": true
}
```

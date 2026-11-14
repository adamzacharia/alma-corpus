# ALMA and VLA Observations: Evidence for Ongoing Low-mass Star Formation near Sgr A*

`2017MNRAS.467..922Y` | Monthly Notices of the Royal Astronomical Society 2017 | first author: Yusef-Zadeh, F. | arXiv: 1701.05939 | DOI: 10.1093/mnras/stx142

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: milky_way_ism, star_formation, protoplanetary_disks
- Question: Do proplyd candidates near Sgr A* detected with the VLA have mm dust counterparts, and what disk masses do they imply for low-mass star formation near Sgr A*?  
  > "ALMA observations presented here are motivated to search for cool dust emission from circumstellar disk candidates and establish their proplyd nature" (Introduction)
- Target **Proplyd candidates NE of Sgr A***: coordinates Table 1: RA 17h45m41.09-41.27s, Dec -29d00m24.7-25.9s (J2000)  
  > "Low-mass stars at the Galactic center distance of 8 kpc are too faint, too far and highly extincted" (Introduction); "cluster of proplyd candidates located about 20$''$ NE of Sgr A\*" (Observations and Data Reduction); z/distance 8 kpc  
  > "Low-mass stars at the Galactic center distance of 8 kpc are too faint, too far and highly extincted" (Introduction); "cluster of proplyd candidates located about 20$''$ NE of Sgr A\*" (Observations and Data Reduction); distance from assumed Galactic center distance  
  > "Low-mass stars at the Galactic center distance of 8 kpc are too faint, too far and highly extincted" (Introduction); "cluster of proplyd candidates located about 20$''$ NE of Sgr A\*" (Observations and Data Reduction)

## Data provenance

- ALMA projects: 2011.0.00887.S, 2015.A.00021.S
- bands: _not stated_
- frequencies and spectral setup: 230 GHz: two spws centered 218.3 and 238.0 GHz, 1.87 GHz wide each; 100 GHz archival: 4 spws of 2 GHz  
  > "The ALMA 230 GHz data consisted of two spectral windows centered on 218.3 and 238.0 GHz, each 1.87 GHz wide." (Observations and Data Reduction); "The 100 GHz dataset contains contained 4 spectral windows of 2 GHz bandwidth." (Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: 100 GHz: nineteen 12-m antennas  
  > "observed on May 18, 2012 with nineteen 12-m antennas" (Observations and Data Reduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 230 GHz July 18: 0.36''x0.25''; 100 GHz beam 1.58''x1.31''  
  > "The July 18 data which has a higher spatial resolution ($0.36''\times0.25''$) than the July 12 data are presented here." (Observations and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: 100 GHz image 0.6 mJy/beam  
  > "The final sensitivity in the 100 GHz image presented here is  0.6 mJy/beam" (Observations and Data Reduction)
- time on source: _not stated_
- observing dates: 2016 July 12 and 18 (230 GHz); 2012 May 18 (100 GHz)  
  > "Observations were obtained on July 12 and July 18, 2016, as part of the director’s discretionary time" (Observations and Data Reduction)
- pi or archival as stated: 2016 data from director's discretionary time; 100 GHz from Cycle 0 archive  
  > "We also used calibrated ALMA archival data at 100 GHz from Cycle 0" (Observations and Data Reduction)
- Other facility **VLA**: B-configuration Ka/Q-band (44, 34 GHz) continuum on same days as ALMA  
  > "Radio continuum observations were carried out with the VLA in its B configuration on the same days that ALMA observations took place." (Observations and Data Reduction)
- External data: Dust temperature 90-105 K at proplyd locations  
  > "Lau et al. (2013) derive a dust temperature at the location of proplyd candidates ranging between 90 and 105K" (Results) [from Lau et al. 2013]
- External data: Proplyd candidate list (names P7, P8 etc.) and 34 GHz detections  
  > "five individual sources that are identified as proplyd candidates (Yusef-Zadeh et al. 2015a)" (Results) [from Yusef-Zadeh et al. 2015a]

## Processing

### Calibration

- pipeline or manual: Editing and calibration done with OBIT  
  > "The editing and calibration of the data was carried out by OBIT (Cotton 2008)" (Observations and Data Reduction)
- casa version: CASA 4.5.3 (100 GHz imaging)  
  > "using CASA version 4.5.3" (Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: 230 GHz: 1744-3116 assumed 0.26 Jy at 234 GHz; 100 GHz: Neptune and Titan  
  > "Initial amplitude and phase calibration was based on 1744-3116 with an assumed flux density of 0.26 Jy at 234 GHz." (Observations and Data Reduction); "Neptune and Titan were used for flux calibration" (Observations and Data Reduction)
- flux scale uncertainty: _not stated_
- self calibration: Phase self-cal then amp+phase used at 230 GHz; adds amplitude uncertainty; 100 GHz phase and amp self-cal  
  > "Phase self calibration followed by amplitude and phase calibration was used to reveal the low level emission but adds uncertainty to the overall amplitude gain calibration." (Observations and Data Reduction)

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
- array combination: All spectral windows averaged before imaging  
  > "before all the spectral windows were averaged prior to constructing final images" (Observations and Data Reduction)
- smoothing: _not stated_
- final beam: 226 GHz 0.42''x0.35'' PA 80 deg; 100 GHz 1.58''x1.31'' PA -87.5 deg  
  > "Convolved to the resolution of the 226 GHz image ($0.^{\prime\prime}42\times0.^{\prime\prime}35$, PA = $80^\circ$)" (Table 1)
- final rms: 0.6 mJy/beam at 100 GHz  
  > "The final sensitivity in the 100 GHz image presented here is  0.6 mJy/beam" (Observations and Data Reduction)

### Inherited from earlier work

- Disk mass method (optically thin dust, Orion/NGC 2024 approach)  
  > "We follow Mann et al’s (2014, 2015) approach to estimating proplyd masses in the Orion nebula and NGC 2024 clusters" (Results) [from Mann et al. 2014, 2015 (cite: mann14)]

### Not stated but needed to reproduce (our reading)

- Imaging task, weighting/robust, cell and image size, deconvolver for 226 GHz and 100 GHz images
- Details of OBIT self-calibration solution intervals
- How Gaussian fits were done and how uncertainties derived
- Whether 44 GHz flux 46 GHz vs 44 GHz in scaling is intended
- Detailed ALMA calibration of July 12 vs 18 data and project code of 226 GHz data (only in acknowledgement)
- VLA calibration/imaging software and parameters

## Analysis recipe

1. **Calibrate and image ALMA 226 GHz and VLA data**: OBIT calibration with self-calibration, spectral windows averaged; VLA 44 GHz convolved to the 226 GHz resolution  
  > "The editing and calibration of the data was carried out by OBIT (Cotton 2008)" (Observations and Data Reduction)
   - software: OBIT
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure peak fluxes of five sources**: Gaussian fits at 44 and 226 GHz  
  > "Table 1 shows the parameters of Gaussian fits to five individual sources that are identified as proplyd candidates" (Results)
   - fitting: Gaussian fits  
  > "Table 1 shows the parameters of Gaussian fits to five individual sources that are identified as proplyd candidates" (Results)
   - validation: _not stated_
3. **Subtract free-free to get dust flux**: Scale 44 GHz flux by 0.76 and subtract from 226 GHz flux  
  > "the bremsstrahlung flux at 226 GHz is 0.76 times the 46 GHz flux" (Results)
   - assumption: 44 GHz emission optically thin bremsstrahlung, Te = 8000 K, no dust contamination  
  > "we assume that the 44 GHz fluxes are dominated by optically-thin bremsstrahlung with electron temperature 8000 K" (Results)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive disk masses**: M = d^2 F_dust / (kappa B(Td)), optically thin  
  > "where $d=8$ kpc is the distance to the Galactic center, $\kappa_\nu$ is the dust grain opacity at 0.856 mm" (Results)
   - parameter: kappa = 0.068 cm^2/g, Td = 100 K, d = 8 kpc  
  > "We set $\kappa_\nu = 
0.068\,\mathrm{cm}^{2}\,\mathrm{g}^{-1}$, twice that adopted by Mann et al. (2014)" (Results)
   - assumption: Opacity doubled for twice-solar metallicity; Td=100 K  
  > "to account for the twice solar metallicity at the Galactic center" (Results)
   - fitting: _not stated_
   - validation: Optical depth correction for uniform disk (300 AU)^2 adds at most 10%; mass vs Td explored  
  > "We see that optical depth effects add at most 10% to the derived disk mass but are typically far smaller." (Results)

## Software

- **OBIT** : ALMA editing and calibration  
  > "The editing and calibration of the data was carried out by OBIT (Cotton 2008)" (Observations and Data Reduction)
- **CASA** 4.5.3: Imaging the 100 GHz archival continuum  
  > "using CASA version 4.5.3" (Observations and Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk mass source 1 | 0.029 | 0.015 | Msun | 4 | / 1 / 41.0856 / 25.930 / 0.71$\pm$0.12 / 1.49$\pm$0.47 / 0.95$\pm0.48$ / 0.029$\pm0.015$ / P7$^c$ / |
| Disk mass source 2 | 0.050 | 0.014 | Msun | 4 | / 2 / 41.1013 / 25.780 / 1.14$\pm$0.11 / 2.52$\pm$0.46 / 1.66$\pm0.47$ / 0.050$\pm0.014$ / P8$^b$ / |
| Disk mass source 3 | 0.050 | 0.014 | Msun | 4 | / 3 / 41.2688 / 25.507 / 0.68$\pm$0.12 / 2.16$\pm$0.46 / 1.65$\pm0.47$ / 0.050$\pm$0.014 / P28$^b$ / |
| Disk mass source 4 | 0.032 | 0.014 | Msun | 4 | / 4 / 41.2691 / 24.659 / 0.76$\pm$0.12 / 1.62$\pm$0.47 / 1.05$\pm0.48$ / 0.032$\pm$0.014 / P26$^b$ / |
| Disk mass source 5 (2-sigma upper limit) | <0.045 | not stated | Msun | 4 | / 5 / 41.2584 / 24.961 / 0.87$\pm$0.11 / 0.98$\pm$0.49 / 0.32$\pm0.50$ / $<$0.045 / P26$^b$ / |
| Dust flux source 2 at 226 GHz | 1.66 | 0.47 | mJy | 3 | / 2 / 41.1013 / 25.780 / 1.14$\pm$0.11 / 2.52$\pm$0.46 / 1.66$\pm0.47$ / |

## Qualitative findings

- Five 44 GHz proplyd candidates have 226 GHz counterparts; most have 100 GHz counterparts, though resolution is too poor to separate individual sources  
  > "There are at least five 44 GHz continuum sources that have 226 GHz counterparts." (Results)

## Claim tuples

- H: Radio proplyd candidates near Sgr A* host cool dust disks | E: ALMA 226 GHz continuum of VLA-detected candidates; free-free subtracted | R: Dust flux 0.3-1.7 mJy; masses 0.03-0.05 Msun for four sources | F: Disks consistent with masses in other star forming sites, supporting ongoing low-mass star formation near Sgr A* | **supported**
- H: Optical depth biases the masses | E: Uniform-disk optical depth correction for source 4 | R: At most 10% increase | F: Optically thin assumption adequate | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Follow Mann et al. approach with Td=100 K appropriate to inner parsec heated by UV  
  > "We adopt $T_d = 100$ K, representative of the inner parsec of the Galaxy" (Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Considerable uncertainty; 0.4'' beam may contain residual cloud material; mass inversely proportional to kappa and Td  
  > "There is considerable uncertainty in these estimates." (Results)
- Limitation (authors): Census incomplete due to extended emission  
  > "The census of proplyds is incomplete due to extended emission and confusing sources dominating the eastern and northern arms of the mini-spiral." (Discussion)
- Caveat (inferred, ours): Dust vs free-free separation relies on 44 GHz flux scaling; 226 GHz fluxes are only about 2-3 sigma
- Caveat (inferred, ours): Possible contamination from cloud dust and mini-spiral emission
- Caveat (inferred, ours): Opacity and Td assumptions drive mass; disks are only marginal detections
- Caveat (inferred, ours): Source 5 listed with the same name as source 4 in Table 1

## Reproducibility

- Data public (paper): 100 GHz data are archival Cycle 0; 2016 data DDT, acknowledged project 2015.A.00021.S  
  > "This paper makes use of the following ALMA data: 2015.A.00021.S (Principal Investigator Gunther Witzel)" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: OBIT scripts
- Missing: VLA reduction details
- Data volume (inferred): tens of GB
- Score (inferred): 3/5, Simple mass calculation with stated equations and parameters, but imaging and fitting details missing.
- Rediscovery candidate: no, Imaging and flux extraction details are not given, and the 226 GHz data are from a DDT campaign processed with OBIT.

## Links

- Method: Mann et al. 2014, 2015 (disk mass approach)
- Companion: Yusef-Zadeh et al. 2015a (cite: 2015ApJ...801L..26Y) (VLA detection of proplyd candidates)
- Related: ALMA/VLA Sgr A* multi-wavelength flux variability campaign

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 37,
  "rate": 0.552
 },
 "evidence_ok": true
}
```

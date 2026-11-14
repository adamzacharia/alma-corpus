# On the multiplicity of ALMA Compact Array counterparts of far-infrared bright quasars

`2018MNRAS.480.4974H` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Hatziminaoglou, E. | arXiv: 1809.00856 | DOI: 10.1093/mnras/sty2073

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: Are the Herschel/SPIRE far-infrared fluxes of FIR-bright z=2-4 SDSS quasars from single sub-mm sources or from multiple counterparts, and what does this imply for major mergers as triggers?  
  > "The goals of this study are to a) determine whether one or more components lie within the *Herschel*/SPIRE beam and b) address the implications of the derived multiplicities" (1 Introduction)
- Target **28 SDSS/Herschel quasars (e.g. J000746, J233600)**: coordinates listed per source in Table (SDSS and SPIRE RA/Dec)  
  > "We selected a random sub-sample of 28 quasars among the brightest 500 $\mu$m   emitters (S$_{500} \ge 10$ mJy) at $z>2$" (2 sample); z/distance z = 2.07-4.1 (SDSS redshifts)  
  > "We selected a random sub-sample of 28 quasars among the brightest 500 $\mu$m   emitters (S$_{500} \ge 10$ mJy) at $z>2$" (2 sample); distance from SDSS spectroscopic redshifts (P16 sample)  
  > "We selected a random sub-sample of 28 quasars among the brightest 500 $\mu$m   emitters (S$_{500} \ge 10$ mJy) at $z>2$" (2 sample)

## Data provenance

- ALMA projects: 2016.2.00060.S, 2011.1.00539.S
- bands: Band 7, 870 um continuum  
  > "using recent ALMA band 7 continuum observations carried out with the Atacama Compact Array (ACA)" (1 Introduction)
- frequencies and spectral setup: single continuum setup at representative frequency 350 GHz  
  > "in single continuum spectral setup at a representative frequency of 350 GHz" (3 The ACA data)
- continuum bandwidth: _not stated_
- arrays: ACA (Atacama Compact Array)  
  > "ALMA Atacama Compact Array (ACA) 870 $\mu$m   continuum maps" (abstract)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: synthesised beams ~4.3" x 3.0"  
  > "synthesised beams $\sim$4$.\!\!^{\prime\prime}$3 $\times$ 3$.\!\!^{\prime\prime}$0" (3 The ACA data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 36 to 43 minutes per SB  
  > "with on time on source ranging from 36 to 43 minutes" (3 The ACA data)
- observing dates: 4-29 July 2017  
  > "between July 4 and 29, 2017" (3 The ACA data)
- pi or archival as stated: PI Hatziminaoglou (2016.2.00060.S)  
  > "project 2016.2.00060.S (PI: Hatziminaoglou)" (3 The ACA data)
- Other facility **Herschel/SPIRE**: 250/350/500 um fluxes and coordinates  
  > "individual detections in all three SPIRE bands (250, 350 and 500 $\mu$m)" (2 sample)
- Other facility **SDSS, UKIDSS, VHS, WISE, GAIA**: optical/NIR/MIR positions and cutouts  
  > "we checked the SDSS coordinates against GAIA and UKIDSS" (4.1 Astrometry)
- External data: SPIRE fluxes, SED-fit LAGN, LFIR, SFRs of quasar sample  
  > "Based on the SED-fitting presented in P16, their L$_{\textrm {FIR}}$ lie between 10$^{12.8}$ and 10$^{13.8}$ L$_{\odot}$" (2 sample) [from (cite: pitchford16)]
- External data: ALMA 0.45" band 7 maps of SMGs from archive, degraded for comparison  
  > "we degraded ALMA band 7 continuum maps of sub-millimetre galaxies (SMGs) at 0$.\!\!^{\prime\prime}$45 from (cite: bussmann15)" (4.3) [from (cite: bussmann15)]
- External data: SCUBA sub-mm source counts  
  > "The density of SCUBA sources at 850 $\mu$m   is reported in Tab. 16 of (cite: scott06)" (5.1) [from (cite: scott06)]
- Simulation/model as data: Simulated Gaussian point-source pairs (1-5" separation, flux ratios 1:1-3:1, 0.5" FWHM, primary ~8 mJy) smoothed to ACA resolution  
  > "we produced a series of simulated point-like (Gaussian) pairs, with relative distances between 1$\\ \\ ^{\prime\prime}$  and 5$\\ \\ ^{\prime\prime}$  flux ratios between 1:1 and 3:1" (4.3)

## Processing

### Calibration

- pipeline or manual: Re-calibrated and re-imaged with the ALMA pipeline  
  > "We re-calibrated and re-imaged the data using the pipeline in CASA version 5.1" (3 The ACA data)
- casa version: CASA 4.7.2 (delivered), CASA 5.1 (re-processing)  
  > "The delivered data were pipeline-reduced using CASA version 4.7.2." (3 The ACA data)
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
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: final images primary-beam corrected  
  > "The final images were corrected for the primary beam" (3 The ACA data)
- array combination: _not stated_
- smoothing: imsmooth to 4.3" x 3.0", PA 85 deg for Bussmann comparison  
  > "assuming a beam of 4$.\!\!^{\prime\prime}$3 $\times$ 3$.\!\!^{\prime\prime}$0 with a position angle (PA) of 85 degrees" (4.3)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- SEDs, LFIR, SFRs, LAGN, MBH computed as in P16  
  > "all these quantities have been calculated for the master sample of 513 quasars as described in P16" (2 sample) [from (cite: pitchford16)]

### Not stated but needed to reproduce (our reading)

- imaging parameters (tclean weighting, robust, cell, size, deconvolution)
- source extraction method for fluxes and positions (fitting vs peak)
- how rms/detection significance was computed
- how beam-subtraction residual fitting was implemented
- self-calibration or flux scale uncertainty
- SFR/flux conversion used

## Analysis recipe

1. **Recalibrate and image ACA data**: Re-ran ALMA pipeline with QA flag files, antenna position corrections and flux.csv; primary-beam corrected  
  > "using the flagging files, antenna position corrections and flux files (flux.csv) provided by the ALMA observatory quality assurance process" (3 The ACA data)
   - software: CASA 5.1
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify ACA counterparts within SPIRE beam**: Search within 11" of SPIRE coordinates; primary = unique or closest counterpart; compare with SDSS/SPIRE positions  
  > "we look for counterparts within (18$\\ \\ ^{\prime\prime}$/2)+2$\\ \\ ^{\prime\prime}$= 11$\\ \\ ^{\prime\prime}$  from the SPIRE coordinates" (4 Results)
   - fitting: _not stated_
   - validation: SDSS coordinates checked against GAIA and UKIDSS  
  > "we checked the SDSS coordinates against GAIA and UKIDSS" (4.1 Astrometry)
3. **Test detectability of hidden companions**: Simulate point-source pairs, smooth to ACA beam, fit beam to primary and inspect residuals; apply same to real maps and to degraded Bussmann maps  
  > "We then fit with the ACA beam to the primary (brightest and centred) component on each image and look for residuals at the position of the secondary (fainter) component." (4.3)
   - software: CASA imsmooth
   - fitting: _not stated_
   - validation: Degraded HXMM01 still showed residual at S_res/S_tot=0.05  
  > "albeit with S$_{\rm res}$/S$_{\rm tot}$=0.05" (4.3)

## Software

- **CASA** 4.7.2 / 5.1: pipeline reduction, re-imaging, imsmooth  
  > "We re-calibrated and re-imaged the data using the pipeline in CASA version 5.1" (3 The ACA data)
- **TOPCAT** : table processing  
  > "This work makes use of TOPCAT" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Quasars with unique ACA counterpart within 11" | 19 of 28 | not stated | sources | 2 | Of the 28 SDSS quasars, 19 have unique ALMA counterparts, while six and three sources have a second and third counterparts within 11 |
| Lowest detection significance (J233456) | 3.5 | not stated | sigma | 2 | Source J233456, the source with the lowest ACA detection level, is detected at 3.5$\sigma$. |
| J233600 hidden-companion residual fraction | 0.27 | not stated | dimensionless | 3 | S$_{\rm res}$/S$_{\rm tot}$=0.27 at a distance of 2$.\!\!^{\prime\prime}$5 |
| Mean ACA offsets for six objects from SDSS and SPIRE | 3.59 and 1.62 | not stated | arcsec | 2 | mean offsets for those six objects of 3$.\!\!^{\prime\prime}$59 and 1$.\!\!^{\prime\prime}$62 |

## Qualitative findings

- Secondary counterparts not visible in SDSS/UKIDSS images; nature unknown  
  > "none of the secondary counterparts are visible in the SDSS or UKIDSS images" (4.2)

## Claim tuples

- H: FIR-bright quasars' SPIRE flux is frequently split among multiple sources | E: ACA 870um imaging of 28 quasars | R: 19/28 unique counterparts; 9 multiple (~30%) | F: sub-mm emission mostly from single sources, lower multiplicity than Bussmann15 | **supported**
- H: Quasars are triggered by early-stage mergers | E: Beam-limit simulations and multiplicity rate | R: companions within 2-3" excluded for isolated sources | F: early-stage mergers unlikely the main trigger | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Coarse ACA resolution cannot resolve pairs closer than 2-3"; physical association unproven  
  > "Sub-arcsec resolution observations are absolutely essential" (5.4)
- Caveat (inferred, ours): Multiplicity defined by 25% flux threshold and small sample
- Caveat (inferred, ours): Chance alignments not excluded without redshifts
- Caveat (inferred, ours): Simulations idealised point sources

## Reproducibility

- Data public (paper): ALMA archive data cited with project codes  
  > "ADS/JAO.ALMA#2016.2.00060.S and ADS/JAO.ALMA#2011.1.00539.S" (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters and source-extraction recipe
- Missing: Flux error method
- Data volume (inferred): small, ~tens of GB (28 ACA continuum fields)
- Score (inferred): 3/5, Public data and simple analysis but imaging and extraction details missing.
- Rediscovery candidate: yes, Data public, results are counts and fluxes in tables; recipe moderately complete.

## Links

- Companion: (cite: pitchford16) (Parent quasar sample and SED fits)
- Related: HerMES
- Related: HeLMS
- Related: HerS

## Checks

```json
{
 "quotes": 41,
 "quotes_ok": 41,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.1.00539.S"
 ],
 "obscore_codes_not_in_card": [
  "2011.0.00539.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 63,
  "stated": 32,
  "rate": 0.508
 },
 "evidence_ok": true
}
```

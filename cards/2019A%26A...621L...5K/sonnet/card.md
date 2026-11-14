# MUSE-AO view of the starburst-AGN connection: NGC 7130

`2019A&A...621L...5K` | Astronomy and Astrophysics 2019 | first author: Knapen, J. H. | arXiv: 1812.00809 | DOI: 10.1051/0004-6361/201834669

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: What does the first AO-assisted MUSE NFM view of the composite AGN-starburst galaxy NGC 7130 reveal about its circumnuclear structure, line ratios and kinematics?  
  > "In this Letter, we present the first results from the science verification phase of MUSE-NFM (narrow field mode)" (Introduction)
- Target **NGC 7130 (IC 5135)**: coordinates _not stated_; z/distance 65.5 Mpc (1" = 318 pc); radial velocity 4799 km/s  
  > "a peculiar Sa (cite: deVaucouleurs1991) galaxy at a distance of 65.5 Mpc (so $1^{\prime\prime}$ corresponds to 318 pc)" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00524.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.20"x0.14" (ALMA CO(6-5))  
  > "the ALMA CO(6-5) data with a $0.20\ensuremath{''}\times0.14\ensuremath{''}$ resolution from (cite: Zhao2016)" (2.2 HST and ALMA data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO 6-5 (not stated)
- Other facility **VLT/MUSE NFM with GALACSI AO**: Primary IFU data, ~0.15" resolution  
  > "We used the MUSE integral field spectrograph on the VLT in its newly commissioned NFM in conjunction with GALACSI" (2.1 MUSE NFM AO)
- Other facility **HST WFPC3 F555W**: Archival optical image for comparison  
  > "an archival WFPC3 F555W *HST* image, 600 s deep (6 different exposures)" (2.2 HST and ALMA data)
- Other facility **Gaia DR2**: Astrometric calibration of HST and MUSE  
  > "We calibrated the astrometry for the *HST* and the MUSE data by comparing the position of SF knots with their coordinates in the Gaia DR2" (2.2 HST and ALMA data)
- External data: ALMA CO(6-5) data of NGC 7130 at 0.20"x0.14"  
  > "the ALMA CO(6-5) data with a $0.20\ensuremath{''}\times0.14\ensuremath{''}$ resolution from (cite: Zhao2016)" (2.2 HST and ALMA data) [from (cite: Zhao2016)]
- External data: Galaxy radial velocity 4799 km/s  
  > "We adopted as radial velocity of the galaxy the value of 4799 km s$^{-1}$ from Zhao et al. (2016)." (2.1 MUSE NFM AO) [from Zhao et al. (2016)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: ALMA data used as published by Zhao et al. 2016; no astrometric calibration needed  
  > "The ALMA data have good astrometry, so no calibration was required for those." (2.2 HST and ALMA data)
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
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- MUSE spectral extraction procedure  
  > "we followed the procedure in Comerón et al. (2019, submitted), based on that used for MaNGA" (2.1 MUSE NFM AO) [from Comerón et al. (2019, submitted)]
- eta parameter for diagnostic diagram mapping  
  > "using the parameter $\eta$ as introduced by Erroz-Ferrer et al. (2019, submitted)" (3 Results) [from Erroz-Ferrer et al. (2019, submitted)]
- Ring size measurement methodology  
  > "whose size we measure here following the methodology of (cite: Comeron2014)" (4.1 Nuclear disc) [from (cite: Comeron2014)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration and imaging details (all deferred to Zhao et al. 2016)
- How the ALMA moment maps were made and overlaid
- The CO(6-5) flux or other measured values from ALMA
- Dust and extinction details used for ALMA comparison

## Analysis recipe


## Software

- **MUSE pipeline** 2.5.2: MUSE data reduction under ESO REFLEX  
  > "The resulting data were reduced using v. 2.5.2 of the MUSE pipeline (cite: Weilbacher2012) under the ESO REFLEX interface" (2.1 MUSE NFM AO)
- **pPXF** : Stellar and emission-line fitting  
  > "We fitted the stellar component in the spectra obtained from the ST using `pPXF` (cite: Cappellari2004; Cappellari2017)." (2.1 MUSE NFM AO)
- **Voronoi binning** : Spatial Voronoi tessellations  
  > "produced two spatial Voronoi binnings using the software by (cite: Cappellari2003)" (2.1 MUSE NFM AO)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Radius of the star-forming ring | 0.58 | not stated | arcsec (185 pc) | 0 | a ring configuration with a radius of $0.58\ensuremath{''}$ (185 pc; outlined in Fig. [1](#fig1)) |
| MUSE spatial resolution | ~0.15 | not stated | arcsec | 0 | The spatial resolution of our MUSE data is around $0.15\ensuremath{''}$. |

## Qualitative findings

- A plume of AGN-like emission and high velocity dispersion extends NW from the nucleus, interpreted as an outflow with no counterpart in CO(6-5).  
  > "The plume towards the NW does not have a counterpart in either UV, optical, or IR imaging (cite: Gonzalez_Delgado1998; Davies2014), nor in CO(6-5) (cite: Zhao2016)." (4.2 Outflow plume)

## Claim tuples

- H: AO-assisted MUSE NFM reveals new structure in the circumnuclear region of NGC 7130 | E: MUSE NFM IFU observations, emission-line fitting, diagnostic diagrams, kinematic maps | R: A ~0.2" radius kinematically decoupled nuclear disc and a ~640 pc AGN-like plume were found | F: Two discoveries: a tiny decoupled nuclear disc and an AGN-driven outflow plume | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: The nuclear velocity feature may be a jet-connected structure rather than a disc, though the two interpretations are compatible.  
  > "although an alternative interpretation as a tiny nuclear disc rotating in a different plane from the host galaxy would not be at odds with the jet explanation." (4.1 Nuclear disc)
- How they decided it was enough: _not stated_
- Limitation (authors): Absolute flux calibration may change with a pipeline update.  
  > "This update may affect the absolute flux calibration, so we warn that the values given here may have to be updated later." (Footnote 2)
- Caveat (inferred, ours): ALMA is only a comparison dataset; no new ALMA analysis is done
- Caveat (inferred, ours): Plume interpreted as a jet without independent confirmation
- Caveat (inferred, ours): The conclusions text says NE while the main text says NW

## Reproducibility

- Data public (paper): ALMA data are archival/literature; MUSE from ESO programme 60.A-9493(A)  
  > "We use additional data from the literature" (2.2 HST and ALMA data)
- Products in archive: _not stated_
- Missing: ALMA reduction details
- Missing: Comerón et al. 2019 procedure details
- Data volume (inferred): ~10s of GB for MUSE; ALMA CO(6-5) ~ few GB
- Score (inferred): 2/5, ALMA role is minimal; the ALMA data are used only as a literature comparison and no ALMA processing is described.
- Rediscovery candidate: no, The main results are MUSE-based and qualitative; the ALMA role is minor.

## Links

- Method: Zhao et al. 2016 (cite: Zhao2016) (Source of the ALMA CO(6-5) data)
- Companion: Comerón et al. 2019, submitted (Spectral extraction procedure)
- Companion: Erroz-Ferrer et al. 2019, submitted (eta parameter definition)
- Related: MUSE Atlas of Disks

## Checks

```json
{
 "quotes": 26,
 "quotes_ok": 26,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 2,
 "numeric_problems": 0,
 "fill": {
  "facts": 57,
  "stated": 19,
  "rate": 0.333
 },
 "evidence_ok": true
}
```

# Discovery of 22 GHz Water Masers in the Serpens South Region

`2021AJ....162...68O` | The Astronomical Journal 2021 | first author: Ortiz-León, Gisela N. | arXiv: 2105.11747 | DOI: 10.3847/1538-3881/ac052c

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation
- Question: Do low-mass protostars in Serpens South host 22 GHz H2O masers, where do the masers arise, and how does maser emission relate to bolometric luminosity?  
  > "We detect for the first time H$_2$O masers in the Serpens South region that are found to be associated to three Class 0–Class I objects" (abstract)
- Target **Serpens South (CARMA-6, CARMA-7, SSTgbs J1829053–014156, SSTgbs J1830177–021211)**: coordinates CARMA-7 18:30:04.12 -02:03:02.6; CARMA-6 18:30:03.54 -02:03:08.4  
  > "Thus, in the present study we adopt the distance from the VLBI measurement of $436.0\pm9.2$ pc." (Introduction); z/distance 436.0±9.2 pc  
  > "Thus, in the present study we adopt the distance from the VLBI measurement of $436.0\pm9.2$ pc." (Introduction); distance from VLBI parallaxes (Ortiz-León 2017)  
  > "Thus, in the present study we adopt the distance from the VLBI measurement of $436.0\pm9.2$ pc." (Introduction)

## Data provenance

- ALMA projects: 2012.1.00769.S, 2015.1.00283.S
- bands: _not stated_
- frequencies and spectral setup: CARMA-6 ALMA continuum at 347 GHz (Appendix Fig. 13, CARMA-6)  
  > "the dust disk detected in the ALMA continuum map at 347 GHz shown in Fig. [13](#fig:alma-cont-347) of Appendix [6](#sec:appendix)." (3.2 VLBA detected sources)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: H2O 6_{1,6}-5_{2,3} (22,235.080 MHz)
- Other facility **VLA**: 22 GHz H2O maser survey of 48 fields plus 22.9 GHz continuum (program 18B-230)  
  > "under program 18B-230" (2.1 VLA observations)
- Other facility **VLBA**: Multi-epoch 22.2 GHz maser follow-up (program BO061)  
  > "These observations were conducted between March and November, 2020 as part of program BO061" (2.2 VLBA observations)
- External data: ALMA CO(2-1) outflow of CARMA-7/CARMA-6 used for comparison with maser positions  
  > "The water maser detected with the VLA toward CARMA-7 is found at the very base of the CO ($J$=2–1) molecular outflow (see Fig. [3](#fig:outflows)) traced by ALMA (cite: Plunkett_2015)." (Results, VLA detected sources with H$_2$O emission) [from (cite: Plunkett_2015)]
- External data: Bolometric luminosities of 162 YSOs  
  > "Extinction corrected bolometric luminosities are available for the 162 stars of the catalog by (cite: Dunham_2015)" (4 Discussion) [from (cite: Dunham_2015)]

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

### Not stated but needed to reproduce (our reading)

- Reduction details and ALMA project provenance for the 347 GHz CARMA-6 continuum map (not given; ALMA data are not processed in this paper)
- Which ALMA project produced the 347 GHz map and CO(3-2) map

## Analysis recipe


## Software

- **CASA** 5.4.1: VLA calibration pipeline, tclean imaging, uvcontsub, imfit (VLA)  
  > "Common Astronomy Software Applications (CASA, version 5.4.1) package using the VLA pipeline" (2.1 VLA observations)
- **AIPS** : VLBA calibration and jmfit spot fitting  
  > "Data calibration was performed with the Astronomical Imaging System (AIPS; (cite: Greisen2003))" (2.2 VLBA observations)
- **ParselTongue** : scripting interface to AIPS  
  > "using the ParselTongue scripting interface (cite: Kettenis2006)" (2.2 VLBA observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Bolometric luminosity threshold for water masers | ≈10 | not stated | L_sun | 0 | Figure [9](#fig:lbol) suggests that there is a bolometric luminosity threshold of $L_{\rm Bol}\approx10~L_\odot$ to excite water maser emission. |
| New radio continuum detections at 22 GHz | 11 | not stated | sources | 0 | Therefore, we are reporting 6+5=11 new radio continuum detections. |
| Offset of CARMA-6 masers from ALMA 347 GHz continuum peak | 50 mas (≈22 au) | ALMA astrometric accuracy about 9 mas | mas | 0 | have a significatn offset of 50 mas ($\approx22$ au) with respect to the continuum peak |

## Qualitative findings

- Masers in the three Class 0–I sources lie at the base of outflows and are likely shock-excited; SSTgbs J1830177–021211 is likely a background AGB star.  
  > "suggest that SSTgbs J1830177–021211 is most likely a background AGB star" (Conclusions)

## Claim tuples

- H: Water masers exist in Serpens South protostars | E: VLA 22 GHz survey of 48 fields, VLBA follow-up | R: Masers in CARMA-7, CARMA-6, SSTgbs J1829053–014156, SSTgbs J1830177–021211 | F: First detection of H2O masers in the region | **supported**
- H: A luminosity threshold exists for maser hosting | E: Compare L_Bol distributions of hosts and 162 YSOs | R: Threshold ≈10 L_sun | F: Suggested threshold, but variability may hide lower-luminosity masers | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Rotating protostellar jet for CARMA-6 velocity gradient disfavoured since jet perpendicular to ALMA disk (PA 172°) differs from maser filament (≈130°).  
  > "This seems to work against a rotating protostellar jet as the explanation for the observed maser velocity gradient." (3.2 VLBA detected sources)
- How they decided it was enough: _not stated_
- Limitation (authors): VLBA time baseline too short for kinematics; parallax not constrained.  
  > "covering a time baseline too short to investigate the internal kinematics of the masers." (3.2 VLBA detected sources)
- Caveat (inferred, ours): ALMA is used only for comparison images; no ALMA processing described
- Caveat (inferred, ours): Luminosity threshold based on only 4 maser hosts and variable masers

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA data processing details for the 347 GHz map
- Data volume (inferred): ALMA part small (~tens of GB); VLA/VLBA data separate
- Score (inferred): 2/5, ALMA is a minor comparison and no ALMA reduction is described.
- Rediscovery candidate: no, Main results come from VLA/VLBA, not ALMA.

## Links

- Companion: (cite: Plunkett_2015) (ALMA CO(2-1) outflow of CARMA-7/6)

## Checks

```json
{
 "quotes": 25,
 "quotes_ok": 25,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 53,
  "stated": 15,
  "rate": 0.283
 },
 "evidence_ok": true
}
```

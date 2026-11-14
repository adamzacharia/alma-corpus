# Seeds of Life in Space (SOLIS). VII. Discovery of a cold dense methanol blob toward the L1521F VeLLO system

`2020A&A...635A.189F` | Astronomy and Astrophysics 2020 | first author: Favre, C. | arXiv: 2002.07004 | DOI: 10.1051/0004-6361/201937297

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, astrochemistry
- Question: What is the molecular complexity of the L1521F VeLLO, and what is the nature of the methanol emission blob found NE of the protostar?  
  > "we present new interferometric observations of L1521F carried out with NOEMA (Northern Extended Millimetre Array) to investigate the molecular complexity of its identified VeLLO." (Introduction)
- Target **L1521F**: coordinates 04h28m38.99s +26d51m35.6s (J2000)  
  > "toward L1521F (${\rm \alpha_{2000} = 04^h28^m38.99^s, \delta_{2000} = 26\ensuremath{^\circ}51\ensuremath{'}35.6\ensuremath{''}}$)" (Observations and data reduction); "corresponding to a 950 au size at a distance of 136 pc" (Distribution of the methanol emission); z/distance 136 pc  
  > "toward L1521F (${\rm \alpha_{2000} = 04^h28^m38.99^s, \delta_{2000} = 26\ensuremath{^\circ}51\ensuremath{'}35.6\ensuremath{''}}$)" (Observations and data reduction); "corresponding to a 950 au size at a distance of 136 pc" (Distribution of the methanol emission); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00239.S, 2015.1.00340.S
- bands: _not stated_
- frequencies and spectral setup: Narrowband 39 kHz (0.12 km/s) at 96.7 GHz; WideX 95.85-99.45 GHz at 1950 kHz  
  > "the spectral range of WideX was 95.85–99.45 GHz" (Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: NOEMA (main data); ALMA 12m array for the archival CS 5-4 data  
  > "Early Cycle 0 data performed with a 12m array" (Distribution of the CS and SO emission)
- configurations: NOEMA C and D  
  > "carried out in C and D configurations between September 2016 and January 2017" (Observations and data reduction)
- baselines: _not stated_
- angular resolution: NOEMA synthesized beam 2.72" x 2.37", PA 29 deg  
  > "the synthesized beam was 2.72$\ensuremath{''}$ $\times$ 2.37$\ensuremath{''}$ at a position angle 29$\ensuremath{^\circ}$" (Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: September 2016 to January 2017 (NOEMA)  
  > "between September 2016 and January 2017" (Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: CH3OH A+ 2(0,2)-1(0,1) (96.741375 GHz)
- Line: CH3OH E2 2(1,2)-1(1,1) (96.739362 GHz)
- Line: CS 2-1 (97980.9533 MHz)
- Line: CS 5-4 (244935.5565 MHz)
- Other facility **IRAM-30m**: On-the-fly 3 mm maps used to recover extended emission and merged with NOEMA  
  > "we also make use of IRAM-30m observations for recovering the most extended emission." (IRAM-30m Observations)
- Other facility **ALMA**: Archival CS 5-4 (Cycle 0) and Cycle 3 0.87 mm continuum map  
  > "CS (5–4) has also been mapped and detected with ALMA toward L1521F" (Distribution of the CS and SO emission)
- External data: Cycle 3 0.87 mm continuum data provided by K. Tokuda  
  > "The ALMA Cycle 3 continuum data were kindly given to us by K. Tokuda." (footnote 3) [from Tokuda:2017; Tokuda:2018]
- External data: CS-H2 collisional rates for 10-300 K  
  > "We used the collisional rates of CS with H$_2$ calculated by (cite: Lique:2006) for temperatures in the range from 10 to 300 K." (Carbon monosulfide) [from (cite: Lique:2006)]

## Processing

### Calibration

- pipeline or manual: NOEMA calibrated with CLIC (GILDAS, July 2018 version)  
  > "The calibration, imaging and cleaning of the NOEMA data were performed using the CLIC and MAPPING packages of the GILDAS" (Data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: MWC34 (1.03 Jy) for NOEMA absolute flux  
  > "The absolute flux calibration was performed via observation of the quasar MWC34 (1.03 Jy)." (NOEMA Observations)
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
- primary beam correction: Images corrected for primary beam attenuation  
  > "We note that the images have been corrected for primary beam attenuation." (Data reduction)
- array combination: NOEMA merged with IRAM-30m using a GILDAS-MAPPING routine  
  > "we merged the 30m with the NOEMA data via the use of a routine in the GILDAS-MAPPING package." (Missing flux and Data merging)
- smoothing: _not stated_
- final beam: 2.8" x 2.4", PA 29 deg, pixel 0.53"  
  > "The synthesized beam of the combined data cube is 2.8$^{\prime\prime}$ $\times$ 2.4$^{\prime\prime}$ at a position angle of 29$^{\ensuremath{^\circ}}$" (Missing flux and Data merging)
- final rms: 4 to 15 mJy/beam  
  > "The rms of the resulting spectral data cubes varies from 4 to 15 mJy/beam." (Missing flux and Data merging)

### Inherited from earlier work

- Cycle 3 ALMA data reduction details  
  > "For further details on the data reduction, see (cite: Tokuda:2017; Tokuda:2018)" (Continuum emission) [from (cite: Tokuda:2017; Tokuda:2018)]

### Not stated but needed to reproduce (our reading)

- Weighting and cleaning parameters for the NOEMA imaging
- Procedure and scaling for the 30m-NOEMA merge
- ALMA Cycle 0 CS 5-4 reduction details
- LTE and RADEX input parameters and grids
- Continuum subtraction and line-free channels

## Analysis recipe

1. **Estimate missing flux**: Convolved NOEMA data to the 30m beam and compared peak intensities  
  > "we estimate that more than 80$\%$ of the methanol emission is resolved out." (Missing flux and Data merging)
   - software: GILDAS
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit line profiles**: Gaussian fits of CH3OH and CS spectra  
  > "We present in Table [\[tab3\]](#tab3) the results from the Gaussian line fitting carried out within the cassis software." (Methanol)
   - software: CASSIS
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive gas density and temperature from CS**: LTE then non-LTE RADEX with CS 2-1 and 5-4  
  > "We then, assuming a linewidth of about 3 km s$^{-1}$, used non-LTE radiative transfer modelling using Radex" (Carbon monosulfide)
   - software: CASSIS, MADCUBA, RADEX
   - assumption: linewidth about 3 km/s  
  > "assuming a linewidth of about 3 km s$^{-1}$" (Carbon monosulfide)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive methanol Tex and column density**: Simple LTE modelling of the two detected lines plus the E1 upper limit  
  > "We performed a simple LTE radiative transfer modelling on the two CH$_3$OH detected transitions as well as on the upper limit" (Methanol)
   - software: CASSIS
   - assumption: LTE justified by n(H2)>10^7 cm^-3  
  > "the methanol lines are most likely in LTE" (Methanol)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **GILDAS (CLIC, MAPPING, CLASS)** July 2018: Calibration, imaging, merging, 30m reduction  
  > "Regarding the single dish data, the reduction has been performed with the GILDAS-CLASS package." (Data reduction)
- **CASSIS** : Gaussian line fitting, line identification, LTE and RADEX  
  > "We carefully checked the line identification using the cassis software and the CDMS and JPL databases." (Unidentified transition)
- **MADCUBA** : LTE analysis of CS  
  > "We first performed a LTE analysis using both cassis and madcuba" (Carbon monosulfide)
- **RADEX** : Non-LTE CS modelling  
  > "used non-LTE radiative transfer modelling using Radex (cite: van-der-Tak:2007) within cassis" (Carbon monosulfide)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Methanol excitation temperature | 10 | ±2 | K | 4 | found an excitation temperature range of (10$\pm$2) K and a column density of (1.3$\pm$0.2)$\times$10$^{13}$ cm$^{-2}$ |
| Methanol column density | 1.3e13 | ±0.2e13 | cm^-2 | 4 | (1.3$\pm$0.2)$\times$10$^{13}$ cm$^{-2}$ |
| Blob size | 7 arcsec (950 au) | not stated | arcsec | 0 | The source size is about 7$^{\prime\prime}$, corresponding to a 950 au size at a distance of 136 pc |
| Fraction of methanol emission resolved out | >80 | not stated | percent | 1 | more than 80$\%$ of the methanol emission is resolved out |
| Blob H2 density | >1e7 | not stated | cm^-3 | 3 | The minimum T$_{k}$ is about 15 K with N(CS)=1.8 10$^{12}$ cm$^{-2}$ and n(H$_2$)\>10$^7$ cm$^{-3}$. |

## Qualitative findings

- Methanol blob is about 1000 au NE of the protostar, coincides with no continuum source, and lies at the intersection of cold filaments  
  > "Surprisingly, this position is not associated with any of the 3 MMS sources." (Distribution of the methanol emission)

## Claim tuples

- H: What is the nature of the methanol blob? | E: NOEMA plus 30m methanol maps, CS 2-1 and 5-4 radiative transfer, LTE methanol | R: Tex about 10 K, n(H2)>1e7 cm^-3, compact (~1000 au) | F: Either a recent shock-induced cold dense blob or a cold dense fragment | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Vinyl alcohol rejected as the U-line identification because only one transition is detected  
  > "this species can then be dismissed on the basis that one transition only has been detected." (Unidentified transition)
- How they decided it was enough: _not stated_
- Limitation (authors): The two scenarios cannot be distinguished with the present data  
  > "Further observations are needed to distinguish between the two scenarios." (Conclusions)
- Caveat (inferred, ours): CS 2-1 and 5-4 have very different spectral resolutions and beams, so the density estimate is uncertain
- Caveat (inferred, ours): LTE for methanol is assumed, and the E1 line is only marginally detected

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: NOEMA data are IRAM project L15AA, whose public status is not stated
- Missing: Merging and imaging parameters
- Data volume (inferred): NOEMA and 30m data plus ALMA archival cubes; tens of GB
- Score (inferred): 2/5, The main data are NOEMA, the ALMA role is minor, and imaging and radiative-transfer details are missing.
- Rediscovery candidate: no, The main data are NOEMA and 30m, with incomplete recipe details.

## Links

- Method: Ceccarelli:2017 (SOLIS program description)
- Companion: Punanova:2018 (SOLIS NOEMA study of the L1544 methanol peak)
- Related: SOLIS
- Related: CALYPSO

## Checks

```json
{
 "quotes": 48,
 "quotes_ok": 48,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 32,
  "rate": 0.464
 },
 "evidence_ok": true
}
```

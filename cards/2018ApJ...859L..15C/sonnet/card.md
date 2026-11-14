# Interferometric Imaging of Titan’s HC<SUB>3</SUB>N, H<SUP>13</SUP>CCCN, and HCCC<SUP>15</SUP>N

`2018ApJ...859L..15C` | The Astrophysical Journal Letters 2018 | first author: Cordiner, M. A. | arXiv: 1805.04416 | DOI: 10.3847/2041-8213/aac38d

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: solar_system, astrochemistry
- Question: What are the spatial distributions of HC3N and its 13C and 15N isotopologues in Titan's atmosphere, and what is the 14N/15N ratio in HC3N?  
  > "we present the first maps of Titan’s $^{13}$C and $^{15}$N isotopologues of the cyanoacetylene molecule (HC$_3$N), obtained using spatially resolved data from the Atacama Large Millimeter/submillimeter Array (ALMA)." (Introduction)
- Target **Titan**: coordinates _not stated_; z/distance 9.26 au from Earth  
  > "which was 9.26 au from Earth at the time of observation." (Observations); distance from _not stated_

## Data provenance

- ALMA projects: 2016.A.00014.S
- bands: Band 7  
  > "The Band 7 receiver was used" (Observations)
- frequencies and spectral setup: 342.5-346.1 GHz and 354.2-356.1 GHz, 976 kHz resolution  
  > "configured to observe the frequency ranges 342.5-346.1 GHz and 354.2-356.1 GHz at moderate spectral resolution (976 kHz)" (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.23''x0.17''  
  > "The resulting angular resolution was $0.23''\times0.17''$ from a Gaussian fit to the point-spread function." (Observations)
- max recoverable scale: _not stated_
- sensitivity: RMS ≈4 mJy/beam  
  > "resulting in an RMS noise of $\approx4$ mJy beam$^{-1}$" (Observations)
- time on source: 18 min, 46 antennas  
  > "The total on-source observing time for Titan was 18 min, with 46 antennas online" (Observations)
- observing dates: 2017-05-08  
  > "Observations of Titan were obtained using ALMA on 2017-05-08" (Observations)
- pi or archival as stated: Director's Discretionary Time program  
  > "as part of the Director’s Discretionary Time program 2016.A.00014.S" (Observations)
- Line: HC3N J=39-38, v=0 (354697.463 MHz)
- Line: HC3N J=39-38, v7=1e (355566.254 MHz)
- Line: H13CCCN J=39-38 (343737.400 MHz)
- Line: HCCC15N J=39-38 (344385.348 MHz)
- External data: Titan 12C/13C average 88.6±0.8 (adopted HC3N/H13CCCN = 89)  
  > "are all consistent with the (error-weighted) average value of $88.6\pm0.8$." (Results) [from (cite: bez14)]
- External data: Spectroscopic line identification via CDMS catalogue  
  > "were identified using the CDMS catalogue (cite: mul01), based on the laboratory frequencies of (cite: tho00; tho01)." (Results) [from (cite: mul01); (cite: tho00; tho01)]

## Processing

### Calibration

- pipeline or manual: Automated JAO pipeline scripts  
  > "using the automated pipeline scripts supplied by the Joint ALMA Observatory (cite: shi15)" (Observations)
- casa version: CASA 5.1  
  > "Data were flagged and calibrated in CASA 5.1 (cite: jae08)" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1733-1304  
  > "Flux calibration was performed with respect to the quasar J1733-1304" (Observations)
- flux scale uncertainty: about 5%  
  > "is expected to be accurate to within about 5%" (Observations)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: Clark clean  
  > "performed using the `Clark clean` algorithm with natural visibility weighting" (Observations)
- weighting robust: natural  
  > "natural visibility weighting" (Observations)
- uv taper: _not stated_
- cell size: 0.025''  
  > "a pixel size of $0.025''$" (Observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: low-order polynomial fits to spectral regions adjacent to detected lines  
  > "Titan’s continuum flux was subtracted using low-order polynomial fits to the spectral regions adjacent to our detected lines." (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.23''x0.17''  
  > "The resulting angular resolution was $0.23''\times0.17''$" (Observations)
- final rms: ≈4 mJy/beam  
  > "RMS noise of $\approx4$ mJy beam$^{-1}$" (Observations)

### Inherited from earlier work

- Assumed 12C/13C of Titan gases applies to HC3N  
  > "we use the known atmospheric $^{12}$C/$^{13}$C ratio (assumed to apply to HC$_3$N)" (Results) [from (cite: bez14)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for continuum polynomial fit and polynomial order
- Exact clean mask and iterations
- Method/aperture for integrated line fluxes (Table 1) and polar peak ratios
- Pipeline version
- Phase-center tracking ephemeris details
- Channel ranges for moment maps

## Analysis recipe

1. **Calibrate and image**: Pipeline calibration, Titan rest-frame regrid, continuum subtraction, Clark clean with natural weighting  
  > "The spectral axis was transformed to Titan’s rest frame and regridded to a 976 kHz channel width." (Observations)
   - software: CASA
   - parameter: pixel 0.025'', flux threshold 8 mJy  
  > "a pixel size of $0.025''$ and a flux threshold of 8 mJy" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Map and measure line fluxes**: Moment maps integrated over line extent (central 5 channels for HC3N v=0 and v7=1); compare S/N polar peaks  
  > "Only the central 5 spectral channels were included for HC$_3$N $v=0$ and $v_7=1$ to facilitate intercomparison of their maps" (Results)
   - assumption: LTE for Boltzmann comparison of v=0 and v7=1  
  > "(assuming local thermodynamic equilibrium; LTE)" (Results)
   - fitting: _not stated_
   - validation: v7=1 vs v=0 ratio used to diagnose optical depth  
  > "this discrepancy is probably due to a very high optical depth of the $v=0$ line in a compact region near the south pole" (Results)
3. **Derive HC3N/HCCC15N ratio**: Ratio of H13CCCN to HCCC15N line fluxes times assumed 12C/13C of 89  
  > "Adopting a value H$^{12}$C$_3$$^{14}$N/H$^{13}$C$^{12}$C$_2$$^{14}$N = 89, the ratio of our observed H$^{13}$CCCN and HCCC$^{15}$N line fluxes ($0.75\pm0.16$) implies a $^{14}$N/$^{15}$N ratio of $67\pm14$" (Results)
   - assumption: HC3N/H13CCCN equals bulk 12C/13C; partition functions, A, Eu identical within 0.2%  
  > "The use of this method for Titan’s HC$_3$N rests on the assumption that the HC$_3$N/H$^{13}$CCCN ratio is the same as the bulk $^{12}$C/$^{13}$C ratio" (Results)
   - fitting: _not stated_
   - validation: Compared with HCN ratios and photochemical models  
  > "Our value for $^{14}$N/$^{15}$N in HC$_3$N is consistent with the average of the prior HCN measurements: $69.3\pm3.4$" (Discussion)

## Software

- **CASA** 5.1: Flagging, calibration, imaging  
  > "Data were flagged and calibrated in CASA 5.1 (cite: jae08)" (Observations)
- **CDMS** : Line identification  
  > "were identified using the CDMS catalogue (cite: mul01)" (Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HC3N/HCCC15N (14N/15N in HC3N) | 67 | ±14 | dimensionless | 3 | implies an HC$_3$N/HCCC$^{15}$N ratio of $67\pm14$ |
| H13CCCN/HCCC15N flux ratio | 0.75 | ±0.16 | dimensionless | 3 | line fluxes ($0.75\pm0.16$) |
| S/N polar peak ratio v7=1 | 5.7 | ±0.3 | dimensionless | 2 | The ratio of S to N polar peaks for $v_7=1$ is $5.7\pm0.3$ |
| S/N polar peak ratio v=0 | 1.6 | ±0.1 | dimensionless | 2 | for $v=0$ the ratio is only $1.6\pm0.1$ |
| H13CCCN line flux | 35.5 | ±5.9 | Jy kHz | 2 | / H$^{13}$CCCN / $J=39-38$ / 343737.400 / 3.250 / 79 / 330.0 / $35.5\pm5.9$ / |
| HCCC15N line flux | 47.3 | ±6.6 | Jy kHz | 2 | / HCCC$^{15}$N / $J=39-38$ / 344385.348 / 3.254 / 79 / 330.6 / $47.3\pm6.6$ / |

## Qualitative findings

- H13CCCN and HCCC15N emission detected only in compact region over the south pole  
  > "emission from the $^{13}$C and $^{15}$N isotopologues was only detected within a compact region over the south pole" (Results)

## Claim tuples

- H: Is HC3N enriched in 15N relative to N2? | E: Ratio of H13CCCN to HCCC15N fluxes with assumed 12C/13C = 89 | R: HC3N/HCCC15N = 67±14 | F: Significant 15N enrichment versus N2 (167), supporting photochemical fractionation | **supported**
- H: Has the HC3N distribution shifted toward the south pole since 2015? | E: Compared S/N peak ratio in v7=1 map with 2015 ALMA data | R: Ratio increased from 3.1 to 5.7 | F: Consistent with photolytic loss in the north and transport to the winter pole | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: HC3N v=0 and v7=1 lines rejected for abundance retrieval because of opacity and temperature/non-LTE sensitivity  
  > "The high opacity of the HC$_3$N $J=39-38,\,v=0$ line rules out its use for deriving an accurate abundance over the south pole" (Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Ratio not accurate enough to distinguish models; 12C/13C in HC3N uncertain, true ratio could be as low as 43  
  > "limited accuracy of the prior $^{12}$C/$^{13}$C measurement in HC$_3$N (cite: jen08) means that the true HC$_3$N/HCCC$^{15}$N ratio could be as low as 43" (Discussion)
- Caveat (inferred, ours): Result depends on assumed 12C/13C = 89 for HC3N
- Caveat (inferred, ours): Flux extraction method and uncertainties not described
- Caveat (inferred, ours): Single short observation, low S/N of isotopologue lines
- Caveat (inferred, ours): Unexplained 0.06'' pointing offset corrected

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Flux extraction aperture/method
- Missing: Continuum fit line-free channels
- Missing: Clean mask details
- Data volume (inferred): ~20-50 GB raw
- Score (inferred): 3/5, Data from a single DDT project and simple recipe, but flux extraction and several settings are unspecified and public status is not stated.
- Rediscovery candidate: no, Public status of data not stated in paper, and flux measurement recipe is incomplete.

## Links

- Companion: (cite: lai17) (2015 April ALMA observations of HC3N used for comparison)
- Companion: (cite: mol16) (Prior ALMA HCN 14N/15N measurement)

## Checks

```json
{
 "quotes": 49,
 "quotes_ok": 49,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 63,
  "stated": 35,
  "rate": 0.556
 },
 "evidence_ok": true
}
```

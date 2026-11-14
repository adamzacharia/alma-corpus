# Jets in Low-Mass Protostars

`2025Univ...11..333D` | Universe 2025 | first author: Dutta, Somnath | arXiv: 2510.12475 | DOI: 10.3390/universe11100333

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation
- Question: Review of what ALMA and JWST observations reveal about protostellar jets and outflows (launching, morphology, shocks, chemistry, rotation, episodicity, jet-accretion link)  
  > "In this review, we describe recent advances in the study of protostellar jets using observations from the ALMA and JWST telescopes." (Introduction)
- Target **G203.21-11.20W2**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **G209.55-19.68S2 (HOPS 10)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2018.1.00302.S
- bands: 1.3 mm continuum (Figure 1 example)  
  > "The protostar, embedded within a dense envelope traced by 1.3 mm continuum emission, is located at the origin point where the two outflow lobes diverge." (Introduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: ALMA project 2018.1.00302.S (PI: Tie Liu), raw data from the ALMA archive  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.00302.S (PI: Tie Liu)." (Acknowledgments)
- Line: SiO not stated (not stated)
- Line: CO not stated (not stated)
- Other facility **JWST**: JWST GO Cycle 1 observations (Proposal ID 1854, PI Melissa McClure) from MAST, used for infrared jet/outflow figures  
  > "These observations are associated with JWST GO Cycle 1 (Proposal ID: 1854; PI: Melissa McClure)." (Acknowledgments)
- External data: Figures are built from data of the lead authors cited in each Figure  
  > "This review article has utilized the data from the lead authors cited in each Figure." (Data Availability) [from lead authors cited in each Figure (individual citations not given in the text)]
- External data: SiO jet quasi-periodic recurrence times of ~20-175 years  
  > "with inferred recurrence times of $\sim$20–175 years (cite: 2024AJ....167...72D)." (Episodic Nature and Their Origin) [from Dutta et al. 2024 (cite: 2024AJ....167...72D)]
- External data: Nearly half of protostars with SiO jets appear monopolar at millimeter wavelengths  
  > "Yet nearly half of protostars with SiO jets appear monopolar at millimeter wavelengths (cite: 2024AJ....167...72D)." (Monopolarity Nature) [from Dutta et al. 2024 (cite: 2024AJ....167...72D)]

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

- Source and values of the jet mass-loss rates and accretion rates plotted in Figure 5 (literature compilation not identified in the text)
- How the log-log fits were done (sampler, priors, likelihood, treatment of upper limits and uncertainties)
- Which sources count as molecular jets versus T Tauri stars in the fit
- Whether the slope values are the author's own fit or taken from earlier work
- ALMA calibration, imaging and line settings for the Figure 1 data of project 2018.1.00302.S (spectral setup, SiO and CO transitions, beam, rms, robust, self-calibration)
- Source coordinates and distances for G203.21-11.20W2 and G209.55-19.68S2

## Analysis recipe

1. **fit jet mass-loss rate versus accretion rate**: Molecular-jet sources and T Tauri stars fitted separately with a logarithmic (power-law) relation between jet mass-loss rate and accretion rate  
  > "The two groups have been fitted separately with a logarithmic relation:" (Physical Parameters)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.4: plotting and analyses (as stated for CASA, Astropy and matplotlib together)  
  > "the author(s) used CASA 5.4 (cite: 2007ASPC..376..127M), Astropy (cite: 2013A&A...558A..33A), matplotlib (cite: 2007CSE.....9...90H) for the purposes of plotting and analyses." (Acknowledgments)
- **Astropy** : plotting and analyses (as stated for CASA, Astropy and matplotlib together)  
  > "the author(s) used CASA 5.4 (cite: 2007ASPC..376..127M), Astropy (cite: 2013A&A...558A..33A), matplotlib (cite: 2007CSE.....9...90H) for the purposes of plotting and analyses." (Acknowledgments)
- **matplotlib** : plotting and analyses (as stated for CASA, Astropy and matplotlib together)  
  > "the author(s) used CASA 5.4 (cite: 2007ASPC..376..127M), Astropy (cite: 2013A&A...558A..33A), matplotlib (cite: 2007CSE.....9...90H) for the purposes of plotting and analyses." (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Slope alpha of jet mass-loss rate vs accretion rate, molecular jets | ~0.40 | not stated | dimensionless | 1 | The molecular jets show relatively shallow slopes ($\alpha$$\sim$0.40) compared to T Tauri stars ($\alpha$$\sim$0.57). |
| Slope alpha of jet mass-loss rate vs accretion rate, T Tauri stars | ~0.57 | not stated | dimensionless | 1 | The molecular jets show relatively shallow slopes ($\alpha$$\sim$0.40) compared to T Tauri stars ($\alpha$$\sim$0.57). |

## Qualitative findings

- Protostellar jets are traced by SiO within a wide-angle CO outflow cavity around a continuum-embedded protostar (G203.21-11.20W2 example)  
  > "A narrow, collimated jet, traced by SiO emission, is observed along the flow axis, within a wide-angle bipolar outflow cavity delineated by CO emission." (Introduction)
- Episodicity shows no clear dependence on luminosity  
  > "the episodicities do not show any clear dependence on luminosity, most likely because luminosity alone does not reliably trace evolutionary status." (Episodic Nature and Their Origin)

## Claim tuples

- H: Does the dependence of jet mass-loss rate on accretion rate differ between young molecular-jet sources and T Tauri stars? | E: Separate logarithmic fits of jet mass-loss rate versus accretion rate for the two groups | R: Slope ~0.40 for molecular jets versus ~0.57 for T Tauri stars | F: Younger objects accrete at higher rates but eject a smaller fraction of that mass; relative mass-loss efficiency increases toward the T Tauri stage | **supported**
- H: Can extinction explain the high incidence of monopolar protostellar jets? | E: Compare SiO jet monopolarity at millimeter wavelengths with expected extinction effects | R: Nearly half of protostars with SiO jets appear monopolar at millimeter wavelengths | F: Extinction alone cannot explain it, suggesting intrinsic launching asymmetries | **supported**
- H: Does jet episodicity depend on protostellar luminosity? | E: Compare episodicity timescales with bolometric luminosity and envelope mass (Figure 6) | R: No clear dependence on luminosity; relation to envelope mass is not straightforward | F: Luminosity alone does not reliably trace evolutionary status; correlations remain weak or statistically inconclusive | **partially**
- H: Can observations discriminate between X-wind, disk-wind and stellar-wind launching models? | E: Review of recent ALMA and JWST observations of jets and outflows | R: Signatures of the models often overlap and no single model explains the diversity of observations | F: The launching mechanism is not yet disentangled | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Distinguishing launching models observationally is hard because signatures overlap  
  > "However, distinguishing between these models observationally remains challenging, as signatures often overlap." (Launching Models)
- Caveat (inferred, ours): This is a review; the only original ALMA product is an illustrative Figure 1 and the only analysis is a log-log fit whose data, sampler and uncertainties are not described
- Caveat (inferred, ours): Slope values are given without uncertainties or sample definition
- Caveat (inferred, ours): Most numbers are quoted from Dutta et al. 2024 rather than derived here

## Reproducibility

- Data public (paper): Raw ALMA data on the ALMA archive as 2018.1.00302.S; JWST data in MAST  
  > "The raw ALMA data is available on the ALMA archive as: ADS/JAO.ALMA#2018.1.00302.S." (Data Availability)
- Products in archive: _not stated_
- Missing: Compilation of jet mass-loss and accretion rates behind Figure 5
- Missing: Fitting procedure and uncertainties for the slopes
- Missing: ALMA processing and imaging settings for the Figure 1 data
- Data volume (inferred): Unknown; one ALMA project (2018.1.00302.S), only a single illustrative image used, so small if reproduced for Figure 1 only
- Score (inferred): 1/5, Review article with ALMA data used only for one illustrative figure; no processing or analysis recipe is given.
- Rediscovery candidate: no, Review paper: ALMA data are minor, the recipe is not given and the main results are literature syntheses.

## Links

- Companion: Dutta et al. 2024 (cite: 2024AJ....167...72D) (Source of the SiO jet survey results (jet velocities, monopolarity fraction, recurrence times) used throughout the review)
- Related: ALMASOP (acknowledged for access to ALMA data)

## Checks

```json
{
 "quotes": 30,
 "quotes_ok": 30,
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
  "facts": 59,
  "stated": 15,
  "rate": 0.254
 },
 "evidence_ok": true
}
```

# Exploring molecular complexity with ALMA (EMoCA): Alkanethiols and alkanols in Sagittarius B2(N2)

`2016A&A...587A..92M` | Astronomy and Astrophysics 2016 | first author: Müller, Holger S. P. | arXiv: 1512.05301 | DOI: 10.1051/0004-6361/201527470

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: astrochemistry, star_formation, milky_way_ism
- Question: What are the relative abundances of alkanethiols and alkanols in the hot core Sgr B2(N2), and can a new chemical network with alkanethiol reactions explain them?  
  > "We want to know the relative abundances of alkanethiols and alkanols in the Galactic Center source Sagittarius B2(N2), the northern hot molecular core in Sgr B2(N)" (abstract)
- Target **Sgr B2(N2)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00017.S, 2012.1.00012.S
- bands: 3 mm  
  > "additional observations at longer wavelengths may be more promising than more sensitive observations at 3 mm" (Discussion)
- frequencies and spectral setup: Spectral line survey 84-111 GHz in Cycle 0; extra Cycle 1 setup extends to 114.4 GHz  
  > "An additional setup in Cycle 1 extended the frequency range to 114.4 GHz." (Introduction)
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
- Line: CH3OH, 13CH3OH, CH3 18OH multiple rotational lines, vt=0-3 (not stated)
- Line: C2H5OH and 13C isotopologs many rotational lines (not stated)
- Line: CH3SH ground and vt=1 lines (not stated)
- Line: C2H5SH, n- and i-C3H7OH upper limits only (not stated)
- External data: CDMS catalog entries for 13CH3OH, CH3 18OH, 13C-ethanol, CH3SH, n-propanol  
  > "The spectroscopic line data were taken from the CDMS catalog" (2.1 Methanol) [from (cite: CDMS_1; CDMS_2)]
- External data: JPL catalog entries for CH3OH and C2H5OH  
  > "We used the JPL catalog" (2.1 Methanol) [from (cite: JPL-catalog_1998)]
- External data: Orion KL and G327.3-0.6 column density ratios for comparison  
  > "Orion KL data from (cite: EtSH_lab_Orion-KL_2014)." (Table 8) [from (cite: EtSH_lab_Orion-KL_2014; CH3SH_etc_G327_2000)]

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

### Inherited from earlier work

- Observations, data reduction and LTE analysis method described in companion paper  
  > "A detailed account of the observations, reduction, and analysis method of the full data set is reported in a companion paper (cite: deuterated_SgrB2N2_2015)." (3 Observations and data reduction) [from (cite: deuterated_SgrB2N2_2015)]
- Chemical network extended from earlier network  
  > "we incorporate a new set of reactions into the network presented by (cite: i-PrCN_det_2014)" (5 Astrochemical modeling) [from (cite: i-PrCN_det_2014)]
- Initial chemical composition of model  
  > "The initial chemical compositions used in the model follow those of (cite: 3steps2heaven_2013)." (5 Astrochemical modeling) [from (cite: 3steps2heaven_2013)]

### Not stated but needed to reproduce (our reading)

- Array configurations, beam, rms, spectral resolution, calibration and imaging parameters (only in companion paper)
- Source coordinates and distance/systemic velocity
- How source sizes were fitted and LTE fitting software (not named)
- Line widths and velocity offsets per species beyond table values
- Chemical network file and full reaction rates

## Analysis recipe

1. **Update spectroscopic predictions**: Test sign changes of ethanol dipole components against ALMA and lab spectrum; refit ethanethiol parameters with reduced axis system  
  > "We changed the signs of the dipole moment components from (cite: EtOH_rot_2008) one at a time relative to $\mu_b$ of the *anti* conformer." (2.3 Ethanol)
   - software: SPFIT
   - fitting: _not stated_
   - validation: Comparison with ALMA spectrum and a laboratory ethanol spectrum  
  > "we inspected a laboratory spectrum of ethanol in the 3 mm wavelength region taken at the Universität zu Köln for educational purposes." (2.3 Ethanol)
2. **LTE modelling and column densities**: LTE synthetic spectra per molecule with source size, Trot, linewidth; population diagrams; upper limits as 3 sigma models  
  > "Our LTE model thus assumes a source size of $1.4\ensuremath{''}$ and a rotational temperature of 160 K." (4.1 Methanol)
   - parameter: Linewidth 5.4 km/s; Trot 150-180 K  
  > "| C$_2$H$_5$OH$^\star$ | d | 168 | 1.3 | 150 | 2.0 (18) | 1.24 | 5.4 | 0.0 | 1 |" (Table of column densities)
   - assumption: Partition function corrections for conformers and vibrational states  
  > "the ground state partition function needs to be increased by a factor of 1.24" (2.3 Ethanol)
   - fitting: _not stated_
   - validation: Visual comparison of synthetic and observed spectra  
  > "The fit is good for most lines of all three isotopologs" (4.1 Methanol)
3. **Astrochemical modelling of alkanethiols**: Gas-grain kinetics with cold collapse then warm-up 8-400 K, new thiol reactions  
  > "using the kinetics model MAGICKAL (cite: 3steps2heaven_2013)" (5 Astrochemical modeling)
   - software: MAGICKAL
   - parameter: nH = 2e8 cm-3, min dust T 8 K, sulfur abundance 8e-8  
  > "a standard, depleted sulfur abundance of $8 \times 10^{-8}$ is used" (5 Astrochemical modeling)
   - assumption: CH3SH binding energy same as methanol (5534 K); C2H5SH 6230 K  
  > "In the case of C$_2$H$_5$SH, a binding energy of 6230 K is used" (5 Astrochemical modeling)
   - fitting: _not stated_
   - validation: Modeled peak abundance ratios compared with observed column density ratios  
  > "A modeled ratio of CH$_3$SH/C$_2$H$_5$SH = 3.1 is obtained, compared with the observed value of $>21$." (5.2 Discussion of modeling)

## Software

- **MAGICKAL** : Gas-grain chemical kinetics modeling  
  > "using the kinetics model MAGICKAL (cite: 3steps2heaven_2013)" (5 Astrochemical modeling)
- **CDMS** : Spectroscopic catalog  
  > "The spectroscopic line data were taken from the CDMS catalog" (2.1 Methanol)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 12C/13C ratio in methanol and ethanol | ~25 | not stated | dimensionless | 2 | The $^{12}$C/$^{13}$C ratio is $\sim$25 for both molecules. |
| 16O/18O ratio | ~180 | not stated | dimensionless | 2 | with a $^{16}$O/$^{18}$O ratio of $\sim$180 |
| CH3OH column density | 4.0e19 | not stated | cm^-2 | 2 | / CH$_3$OH, $\varv=0$$^\star$ / d / 41 / 1.4 / 160 / 4.0 (19) / 1.00 / 5.4 / $-$0.5 / 1 / |
| C2H5OH column density | 2.0e18 | not stated | cm^-2 | 2 | / C$_2$H$_5$OH$^\star$ / d / 168 / 1.3 / 150 / 2.0 (18) / 1.24 / 5.4 / 0.0 / 1 / |
| CH3SH column density | 3.4e17 | not stated | cm^-2 | 2 | / CH$_3$SH, $\varv=0$$^\star$ / d / 12 / 1.4 / 180 / 3.4 (17) / 1.00 / 5.4 / $-$0.5 / 1 / |
| C2H5SH column density upper limit | <1.6e16 | 3 sigma | cm^-2 | 2 | / *gauche*-C$_2$H$_5$SH / n / 0 / 1.4 / 180 / $<$ 1.6 (16) / 1.95 / 5.4 / $-$0.5 / $-$ / |
| CH3SH/C2H5SH ratio observed | >~21 | lower limit | dimensionless | 2 | The ratios CH$_3$SH to C$_2$H$_5$SH and C$_2$H$_5$OH to C$_2$H$_5$SH are $\gtrsim 21$ and $\gtrsim 125$, respectively. |
| Modeled CH3SH/C2H5SH | 3.1 | not stated | dimensionless | 3 | The modeled ratio CH$_3$SH/C$_2$H$_5$SH = 3.1 is lower than the observed value of $\gtrsim 21$ |
| CH3OH rotation temperature from population diagram | 150.8 | 1.7 | K | 2 | / CH$_3$OH / $\varv=0$, $\varv_{\rm t}=1$, $\varv_{\rm t}=2$ / 150.8 (1.7) / |

## Qualitative findings

- Ratios involving methanol, ethanol and methanethiol in Sgr B2(N2) are similar to Orion KL, but those involving ethanethiol differ, suggesting the Orion KL ethanethiol detection is uncertain.  
  > "those involving ethanethiol are significantly different and suggest that the detection of ethanethiol reported toward Orion KL is rather uncertain." (Conclusion)

## Claim tuples

- H: Is ethanethiol present in Sgr B2(N2) at the level reported for Orion KL? | E: LTE modeling of ALMA 3 mm survey for thiol and alkanol lines | R: No secure ethanethiol lines; CH3SH/C2H5SH >~21 vs 5 in Orion KL | F: Orion KL ethanethiol detection is uncertain | **partially**
- H: Can ethanol intensity discrepancies be resolved? | E: Change dipole component signs and compare to ALMA and lab spectra | R: Sign change of mu_a (or mu_c) of gauche conformer removes overly strong predicted lines | F: Proposed change in relative signs of dipole components | **supported**
- H: Does the new grain-surface network reproduce observed alkanethiol ratios? | E: MAGICKAL warm-up model with new thiol reactions | R: Modeled CH3SH/C2H5SH=3.1 vs >21 observed; CH3OH/CH3SH too high | F: Model cannot yet predict accurate column densities | **partially**

## Reasoning

- Why this data: Reduced line confusion toward Sgr B2(N2) thanks to spatial resolution and narrower lines  
  > "we observed reduced line confusion toward the weaker source Sgr B2(N2) caused not only by the spatial separation of the two sources, but also by narrower lines." (Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Model not accurate enough, particularly for CH3SH, to support or dismiss the Orion KL ethanethiol detection  
  > "Unfortunately, our model calculations are not accurate enough, in particular for CH$_3$SH, to support or dismiss the reported C$_2$H$_5$SH detection in Orion KL." (Discussion)
- Caveat (inferred, ours): Observational setup and LTE method are entirely in a companion paper
- Caveat (inferred, ours): Single-component LTE with fixed source size and linewidth; upper limits depend on assumed parameters
- Caveat (inferred, ours): Ethanol sign change not tested outside 3 mm
- Caveat (inferred, ours): Model comparison uses peak abundances rather than column densities

## Reproducibility

- Data public (paper): Interferometric data available in ALMA archive  
  > "The interferometric data are available in the ALMA archive at https://almascience.eso.org/aq/." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Reduction and imaging details (companion paper)
- Missing: LTE fitting code and exact line lists/fit setup
- Missing: Chemical network files
- Data volume (inferred): ~100s of GB (Cycle 0/1 3 mm spectral scan)
- Score (inferred): 3/5, Data public and results numeric, but reduction and LTE method deferred to a companion paper.
- Rediscovery candidate: no, Recipe depends on companion paper and unnamed LTE tooling.

## Links

- Method: (cite: deuterated_SgrB2N2_2015) (Full description of observations, reduction and analysis method)
- Companion: (cite: i-PrCN_det_2014) (First EMoCA result and chemical network basis)
- Related: EMoCA
- Related: PRIMOS
- Related: IRAM 30 m Sgr B2 survey

## Checks

```json
{
 "quotes": 44,
 "quotes_ok": 44,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 25,
  "rate": 0.379
 },
 "evidence_ok": true
}
```

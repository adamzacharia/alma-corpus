# The interstellar medium in young supernova remnants: key to the production of cosmic X-rays and <inline-formula id="IEq1"><mml:math><mml:mi>γ</mml:mi></mml:math></inline-formula>-rays

`2021Ap&SS.366...58S` | Astrophysics and Space Science 2021 | first author: Sano, Hidetoshi | arXiv: 2106.00708 | DOI: 10.1007/s10509-021-03960-4

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: milky_way_ism, star_formation, other
- Question: How does the clumpy ISM in young SNRs (RX J1713.7-3946, RCW 86) relate to nonthermal X-ray and gamma-ray emission, and what does this imply for the origin of gamma-rays?  
  > "We find that shock–cloud interactions provide a viable explanation for the spatial correlation between the X-rays and ISM." (abstract)
- Target **RX J1713.7-3946**: coordinates _not stated_; z/distance smaller distance (~1 kpc) favored over ~6 kpc  
  > "it has been established that RXJ1713 is a young SNR aged 1600 yr, which was historically recorded" (3.1 Distance determination: nonthermal X-rays and the interacting ISM); distance from CO/X-ray correlation, NANTEN and Suzaku (cite: 2003PASJ...55L..61F; 2005ApJ...631..947M)  
  > "it has been established that RXJ1713 is a young SNR aged 1600 yr, which was historically recorded" (3.1 Distance determination: nonthermal X-rays and the interacting ISM)
- Target **RCW 86**: coordinates (l, b) = (315.4, -2.3)  
  > "The distance has been determined to be $\sim$2.5 kpc using several methods" (4.1 X-rays and the ISM); z/distance ~2.5 kpc  
  > "The distance has been determined to be $\sim$2.5 kpc using several methods" (4.1 X-rays and the ISM); distance from (cite: 1969AJ.....74..879W; 1996A&A...315..243R; 2013MNRAS.435..910H)  
  > "The distance has been determined to be $\sim$2.5 kpc using several methods" (4.1 X-rays and the ISM)

## Data provenance

- ALMA projects: 2013.1.01042.S, 2015.1.01130.S, 2015.1.01232.S, 2017.1.01363.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.02 pc resolution (CO, RX J1713 NW shell)  
  > "obtained high-resolution CO observations (with $\sim$0.02 pc resolution) toward the northwestern shell of RXJ1713" (3.2 Detailed correspondence between X-rays and ISM clumps)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO not stated (not stated)
- Other facility **Chandra**: synchrotron X-ray contours and proper motions  
  > "ALMA CO intensities superposed on *Chandra* synchrotron X-ray contours" (3.2 Detailed correspondence between X-rays and ISM clumps)
- Other facility **Suzaku**: X-ray data compared with CO  
  > "A comparison of the *Suzaku* X-ray data with the CO image revealed details of the interaction" (3.2 Detailed correspondence between X-rays and ISM clumps)
- Other facility **H.E.S.S.**: TeV gamma-ray data  
  > "the TeV $\gamma$-rays observed using H.E.S.S." (3.5.1 ISM–$\gamma$-ray correspondence)
- Other facility **NANTEN**: CO maps at 2.6 arcmin  
  > "2.6 arcmin resolution CO maps obtained with the NANTEN 4-m telescope" (3.1 Distance determination: nonthermal X-rays and the interacting ISM)
- External data: ALMA CO observations of RXJ1713 NW shell, molecular cloudlets of radii ~0.03–0.05 pc  
  > "The authors found dozens of tiny clumps, with typical radii of $\sim$0.03–0.05 pc (referred to as *molecular cloudlets*)." (3.2 Detailed correspondence between X-rays and ISM clumps) [from (cite: 2020ApJ...904L..24S)]
- Simulation/model as data: MHD simulations of shock–cloud interaction (initial B 6 μG amplified to >100 μG; shock 3000 km/s)  
  > "amplified to 100 $\mu$G or higher from its initial value of 6 $\mu$G" (3.3 Simulations of shock-cloud interactions)

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

- ALMA CO data and cloudlet analysis taken from earlier paper  
  > "Most recently, (cite: 2020ApJ...904L..24S) obtained high-resolution CO observations" (3.2 Detailed correspondence between X-rays and ISM clumps) [from (cite: 2020ApJ...904L..24S)]

### Not stated but needed to reproduce (our reading)

- Which ALMA project codes map to which figure (RXJ1713 vs Magellanic SNRs)
- ALMA observing setup, calibration and imaging parameters
- Any reprocessing performed for review figures

## Analysis recipe


## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Cosmic-ray energy in RX J1713 (conventional estimate) | ~10^48 | not stated | erg | 0 | to be $\sim$$10^{48}$ erg, which corresponds to 0.1% of the total energy of a typical supernova explosion |
| Cosmic-ray proton penetration depth into cores | ~0.1 | not stated | pc | 0 | cosmic-ray protons can penetrate on the order of 0.1 pc into the surface layers of the cores |

## Qualitative findings

- X-ray bright spots anticorrelate with ISM clouds/cloudlets at sub-pc scales while correlating at pc scales  
  > "X-ray bright spots (or filaments) are anti-correlated with the ISM clouds/cloudlets at small-scales (sub-pc scales)" (6 Summary and Future Prospects)

## Claim tuples

- H: Can a clumpy ISM explain the hard GeV gamma-ray spectrum of RXJ1713 in a hadronic scenario? | E: Review of MHD shock–cloud simulations and cosmic-ray penetration depth models | R: Penetration-depth-limited interactions give Gamma_GeV ~1.5 | F: Hadronic scenario with clumpy ISM explains the hard spectrum equally well as leptonic | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Current gamma-ray pc-scale resolution too low to resolve ISM–gamma-ray correspondence  
  > "The current pc-scale resolution of $\gamma$-ray observations is too low to resolve this correspondence." (abstract)
- Caveat (inferred, ours): Review paper; no new ALMA reduction, results rely on cited works
- Caveat (inferred, ours): ALMA project codes listed only in acknowledgments

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: All ALMA processing details; paper is a review
- Data volume (inferred): not applicable (review)
- Score (inferred): 1/5, Review with no ALMA methods or recipe.
- Rediscovery candidate: no, Review; no reproducible analysis.

## Links

- Companion: (cite: 2020ApJ...904L..24S) (ALMA CO observations of RXJ1713 NW shell)

## Checks

```json
{
 "quotes": 26,
 "quotes_ok": 26,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2015.1.01195.S",
  "2017.1.01406.S"
 ],
 "codes_printed_but_missing": [
  "2015.1.01195.S",
  "2017.1.01406.S"
 ],
 "numeric_results": 2,
 "numeric_problems": 0,
 "fill": {
  "facts": 55,
  "stated": 16,
  "rate": 0.291
 },
 "evidence_ok": true
}
```

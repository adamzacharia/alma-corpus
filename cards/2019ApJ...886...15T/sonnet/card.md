# An ALMA View of Molecular Filaments in the Large Magellanic Cloud. II. An Early Stage of High-mass Star Formation Embedded at Colliding Clouds in N159W-South

`2019ApJ...886...15T` | The Astrophysical Journal 2019 | first author: Tokuda, Kazuki | arXiv: 1811.04400 | DOI: 10.3847/1538-4357/ab48ff

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, nearby_galaxies
- Question: What is the filament and protostar structure of the N159W-South clump at 0.07 pc resolution, and does a cloud-cloud collision trigger the high-mass star formation?  
  > "We propose a new scenario in which the supersonically colliding gas flow triggers the formation of both the massive filament and protostars." (abstract)
- Target **N159W-South clump (LMC)**: coordinates 5h39m41.0s, -69d46m06.0s (J2000)  
  > "The observations of N159W-South centered at ($\alpha_{\rm J2000.0}$, $\delta_{\rm J2000.0}$) = (5$^{\rm h}$39$^{\rm m}$41.0s, $-$69$^\circ$46$'$06.0$''$)" (2 Observations); "the close distance, $\sim$50 kpc (cite: Schaefer08; de14)" (Introduction); z/distance ~50 kpc  
  > "The observations of N159W-South centered at ($\alpha_{\rm J2000.0}$, $\delta_{\rm J2000.0}$) = (5$^{\rm h}$39$^{\rm m}$41.0s, $-$69$^\circ$46$'$06.0$''$)" (2 Observations); "the close distance, $\sim$50 kpc (cite: Schaefer08; de14)" (Introduction); distance from Schaefer08; de Grijs et al. 2014  
  > "The observations of N159W-South centered at ($\alpha_{\rm J2000.0}$, $\delta_{\rm J2000.0}$) = (5$^{\rm h}$39$^{\rm m}$41.0s, $-$69$^\circ$46$'$06.0$''$)" (2 Observations); "the close distance, $\sim$50 kpc (cite: Schaefer08; de14)" (Introduction)

## Data provenance

- ALMA projects: 2016.1.01173.S, 2012.1.00554.S
- bands: Band 6 (211–275 GHz)  
  > "We carried out ALMA Cycle 4 Band 6 (211–275 GHz) observations toward the N159W with the main array 12 m antennas." (2 Observations)
- frequencies and spectral setup: three spectral windows for 12CO, 13CO, C18O (2-1), 58.6 MHz bandwidth; 30.6 kHz resolution for 12CO, 61.0 kHz for the others  
  > "The frequency resolutions were 30.6 kHz for $^{12}$CO ($J$ = 2–1) and 61.0 kHz for the others." (2 Observations)
- continuum bandwidth: two spectral windows, aggregated 3.75 GHz  
  > "We used two spectral windows for the continuum observations with the aggregated bandwidth of 3.75 GHz." (2 Observations)
- arrays: 12 m main array  
  > "observations toward the N159W with the main array 12 m antennas" (2 Observations)
- configurations: _not stated_
- baselines: 14 to 1940 m  
  > "The projected baseline length ranges from 14 to 1940 m." (2 Observations)
- angular resolution: continuum 0.26'' x 0.23''; 13CO 0.29'' x 0.25''  
  > "The synthesized beams of the continuum and the $^{13}$CO ($J$ = 2–1) observations are 0.26$''$ $\times$ 0.23$''$ and 0.29$''$ $\times$ 0.25$''$, respectively." (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: line ~4.5 mJy/beam (~1.5 K) at 0.2 km/s; continuum ~0.027 mJy/beam  
  > "$\sim$4.5 mJy beam$^{-1}$ ($\sim$1.5 K) at a velocity resolution of 0.2 km s$^{-1}$ and $\sim$0.027 mJy beam$^{-1}$" (2 Observations)
- time on source: _not stated_
- observing dates: 2016 November to 2017 July  
  > "were carried out between 2016 November and 2017 July" (2 Observations)
- pi or archival as stated: Cycle 4 project P.I. Y. Fukui  
  > "ALMA Cycle 4 (P.I.: Y. Fukui #2016.1.01173.S)" (Introduction)
- Line: 12CO J=2-1 (not stated)
- Line: 13CO J=2-1 (not stated)
- Line: C18O J=2-1 (not stated)
- Other facility **ALMA Cycle 1 (2012.1.00554.S)**: lower-resolution (~1'') comparison data  
  > "our previous ALMA Cycle 1 observations ((cite: Fukui15), hereafter Paper I) with an angular resolution of $\sim$1$''$" (Introduction)
- External data: NIR source catalog (#121, #123) used to identify counterparts of MMS-1 and MMS-2  
  > "The positions of MMS-1 and MMS-2 correspond to near-infrared (NIR) sources, #121 and #123, respectively (cite: Testor06)." (3.1) [from Testor06]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 5.0.0  
  > "The data were processed with the CASA (Common Astronomy Software Application) package (cite: McMullin07) version 5.0.0." (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: Cycle 4 fluxes ~20% lower than Cycle 1, attributed to calibration error  
  > "the discrepancies are supposed to be mainly caused by the calibration error instead of the missing flux" (2 Observations)
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "We used the `tclean` task in the imaging process with the `multi-scale` deconvolver to recover the extended emission." (2 Observations)
- deconvolver: multi-scale  
  > "We used the `tclean` task in the imaging process with the `multi-scale` deconvolver to recover the extended emission." (2 Observations)
- weighting robust: Briggs, robust = 0.5  
  > "we applied the Briggs weighting with the robust parameter of 0.5" (2 Observations)
- uv taper: _not stated_
- cell size: 0.07''  
  > "The imaging grid and velocity channels were 0.07$''$ and 0.2 km s$^{-1}$, respectively" (2 Observations)
- image size: _not stated_
- masking: auto-multithresh  
  > "We used the `auto-multithresh` procedure in `tclean` to select the emission mask in the dirty and residual images." (2 Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: continuum 0.26'' x 0.23''; 13CO 0.29'' x 0.25''  
  > "The synthesized beams of the continuum and the $^{13}$CO ($J$ = 2–1) observations are 0.26$''$ $\times$ 0.23$''$ and 0.29$''$ $\times$ 0.25$''$, respectively." (2 Observations)
- final rms: line ~4.5 mJy/beam at 0.2 km/s; continuum ~0.027 mJy/beam  
  > "$\sim$4.5 mJy beam$^{-1}$ ($\sim$1.5 K) at a velocity resolution of 0.2 km s$^{-1}$ and $\sim$0.027 mJy beam$^{-1}$" (2 Observations)

### Inherited from earlier work

- Dust opacity, dust-to-gas ratio and temperature assumptions follow earlier work  
  > "(see, (cite: Oss94); (cite: Herrera13); (cite: Gordon14); Paper I)" (3.1) [from Oss94; Herrera13; Gordon14; Paper I (cite: Fukui15)]
- DisPerSE filament-finding procedure detailed in companion paper  
  > "(see also the detailed procedure in FTS19)" (3.2) [from FTS19 (cite: Fukui19)]
- Outflow force procedure and XCO/ratio assumptions  
  > "We calculated the outflow force ($F_{\rm CO}$) by using the procedure in (cite: Beuther02b)." (3.1) [from (cite: Beuther02b)]

### Not stated but needed to reproduce (our reading)

- Calibration pipeline/manual and calibrator details
- Line-free channels and continuum subtraction method
- Multiscale scales and clean thresholds
- Calibration/flux calibrator used
- Outflow velocity cut thresholds for each lobe and integration regions
- Excitation temperature and abundance used for 13CO column density
- DisPerSE parameters (persistence threshold)
- Region definitions (white dashed contours) for flux and mass

## Analysis recipe

1. **image continuum and CO cubes**: tclean multiscale with auto-multithresh, Briggs weighting  
  > "We used the `tclean` task in the imaging process with the `multi-scale` deconvolver to recover the extended emission." (2 Observations)
   - software: CASA
   - parameter: robust 0.5; 0.07'' pixels; 0.2 km/s channels  
  > "we applied the Briggs weighting with the robust parameter of 0.5" (2 Observations)
   - fitting: _not stated_
   - validation: Compared Cycle 4 flux with Cycle 1 and single-dish; ~20% lower, no significant missing flux  
  > "The total fluxes of the $^{12}$CO, $^{13}$CO, and the 1.3 mm continuum data of the Cycle 4 were $\sim$20% lower than those of the Cycle 1." (2 Observations)
2. **derive continuum clump masses and filament properties**: Gas mass from 1.3 mm dust emission; Gaussian fit to filament cross sections for width; line mass = mass/length  
  > "We performed the Gaussian fitting to the cross section taken along the filament crest." (3.1)
   - assumption: kappa 1.3mm = 1 cm2/g, dust-to-gas 3.5e-3, Td = 20 K  
  > "1 cm$^{2}$ g$^{-1}$, 3.5 $\times$ 10$^{-3}$, and 20 K, respectively" (3.1)
   - fitting: Gaussian fit to cross section  
  > "We performed the Gaussian fitting to the cross section taken along the filament crest." (Results: A dense filamentary cloud traced by the 1.3 mm dust-continuum emission associated with molecular outflows)
   - validation: Total mass consistent with Paper I  
  > "which is consistent with the previous estimate (Paper I)" (3.1)
3. **identify outflows and derive parameters**: Identify high-velocity 12CO wings by eye, extract lobe maps; derive mass, dynamical time, outflow force  
  > "we searched high-velocity emission more than 10 km s$^{-1}$ apart from the systemic velocity ($\sim$236 km s$^{-1}$) by eye" (3.1)
   - assumption: XCO = 7e20 cm-2 (K km/s)-1, 12CO(2-1)/(1-0)=1.0, inclination 30–70 deg  
  > "$X_{\rm CO}$ = 7 $\times$ 10$^{20}$ cm$^{-2}$ (K km s$^{-1}$) and the $^{12}$CO ($J$ = 2–1)/$^{12}$CO ($J$ = 1–0) ratio = 1.0" (3.1)
   - fitting: _not stated_
   - validation: F_CO vs core mass compared with Galactic massive protostars  
  > "roughly follow those seen at massive protostellar sources in the Galaxy (cite: Beuther02b)" (3.1)
4. **analyze 13CO filaments and kinematics**: 13CO column density assuming LTE; DisPerSE filament search in PPV; velocity-sliced maps and PV diagrams  
  > "The $``$DisPerSE$"$ (cite: Sousbie11) algorithm was applied to the $^{13}$CO cube data to search the connecting structures" (3.2)
   - software: DisPerSE
   - assumption: LTE  
  > "We calculated the column densities using the $^{13}$CO ($J$ = 2–1) data assuming the local thermo-dynamical equilibrium." (3.2)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.0.0: calibration/imaging with tclean  
  > "The data were processed with the CASA (Common Astronomy Software Application) package (cite: McMullin07) version 5.0.0." (2 Observations)
- **DisPerSE** : filament identification in 13CO PPV cube  
  > "The $``$DisPerSE$"$ (cite: Sousbie11) algorithm was applied to the $^{13}$CO cube data" (3.2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total filament mass above 3 sigma | ~4e3 | not stated | Msun | 2 | The total mass of the filamentary structure traced by the continuum above the 3$\sigma$ detection is $\sim$4 $\times$ 10$^3$ $M_{\odot}$ |
| Filament crest length | ~1.7 | not stated | pc | 2 | The length of the filament crests is $\sim$1.7 pc. |
| Filament FWHM width | ~0.14 | not stated | pc | 2 | The averaged width (FWHM) of the filament is $\sim$0.14 pc. |
| Filament line mass | ~2e3 | not stated | Msun/pc | 2 | The resultant line mass (=total mass/length) of the filament is $\sim$2 $\times$ 10$^3$ $M_{\odot}$ pc$^{-1}$. |
| MMS-1 mass | 2.1e2 | not stated | Msun | 2 | MMS-1 / 5$^{\rm h}$39$^{\rm m}$41.97s / -69$^\circ$46$'$12.05$''$ / 1.5 / 0.82 / 1.2 $\times$ 10$^{24}$ / 2.1 $\times$ 10$^{2}$ / 121 |
| Virial line mass | 1.3e3 | not stated | Msun/pc | 4 | is calculated to be 1.3 $\times$ 10$^{3}$ $M_{\odot}$ pc$^{-1}$ |
| 13CO velocity dispersion | ~1.7 | not stated | km/s | 4 | The typical velocity dispersion ($\sigma_{\rm v}$) of the N159W-South clump is $\sim$1.7 km s$^{-1}$ in $^{13}$CO |
| Outflow dynamical times | ~1e3–2.5e4 | inclination 30–70 deg range | yr | 3 | MMS-1 / Blue lobe$^{\rm c}$ / 7.2 / 0.13 / 14.5 / 223–227 / 5.1–25 $\times$ 10$^{3}$ |

## Qualitative findings

- Hub-filamentary structure resolved; four continuum peaks MMS-1 to 4 with outflows plus a new outflow candidate YSO-SN  
  > "We have identified a new bipolar outflow source embedded at a $^{13}$CO filament" (Summary)

## Claim tuples

- H: Massive filament and protostars formed by a cloud-cloud collision | E: 13CO velocity maps and PV diagrams, outflow dynamical times | R: Complementary blue/red 13CO distributions, V-shaped PV features, outflow dynamical times ~1e4 yr | F: Colliding flows likely triggered both filament and protostar formation | **supported**
- H: Multiple protostars are embedded in the massive filament | E: 12CO high-velocity wings and 1.3 mm continuum | R: At least five protostellar sources with outflows | F: Early-stage multiple high-mass star formation | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Global hierarchical collapse disfavoured; magnetic/turbulent stabilization disfavoured  
  > "we suggest that the turbulent and magnetic pressure may not stabilize the filament" (4.1)
- How they decided it was enough: _not stated_
- Limitation (authors): MMS-1 and 2 outflow lobes merged at current resolution; YSO-SN has no continuum detection  
  > "Especially for the blue component, it is hard to separate the individual components." (3.1)
- Caveat (inferred, ours): Cloud-collision evidence is qualitative and could be mimicked by other kinematics
- Caveat (inferred, ours): Outflow identification done by eye
- Caveat (inferred, ours): 20% flux discrepancy between cycles unresolved

## Reproducibility

- Data public (paper): Project codes cited in acknowledgments  
  > "This paper makes use of the following ALMA data: ADS/ JAO.ALMA#2012.1.00554.S and #2016.1.01173.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Line-free channels and multiscale settings
- Missing: DisPerSE parameters and 13CO LTE inputs
- Missing: Outflow velocity boundaries per lobe
- Data volume (inferred): ~100-300 GB
- Score (inferred): 4/5, Imaging settings are mostly given, but several analysis details are missing and the outflow identification is manual.
- Rediscovery candidate: no, Key analysis steps are manual or unspecified, and the main conclusions are qualitative.

## Links

- Method: Beuther02b (outflow parameter procedure)
- Method: Sousbie11 (DisPerSE filament finder)
- Companion: Fukui19 (FTS19) (N159E-Papillon region, same project)
- Companion: Fukui15 (Paper I) (Cycle 1 observations of N159W)

## Checks

```json
{
 "quotes": 64,
 "quotes_ok": 64,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 45,
  "rate": 0.652
 },
 "evidence_ok": true
}
```

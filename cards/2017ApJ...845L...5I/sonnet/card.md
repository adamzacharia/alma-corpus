# On the Disappearance of a Cold Molecular Torus around the Low-luminosity Active Galactic Nucleus of NGC 1097

`2017ApJ...845L...5I` | The Astrophysical Journal Letters 2017 | first author: Izumi, T. | arXiv: 1707.05806 | DOI: 10.3847/2041-8213/aa808f

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, nearby_galaxies
- Question: Does the low-luminosity AGN of NGC 1097 host a compact, dense cold molecular torus like that in NGC 1068, and is its torus geometrically thinner?  
  > "a comparison of observed torus properties of this LLAGN with those of luminous Seyferts such as NGC 1068" (Introduction)
- Target **NGC 1097**: coordinates RA 02h46m18.9755s, Dec -30d16m29.02s (J2000, 350 GHz peak)  
  > "The 350 GHz continuum emission peaks at $\alpha_{\rm J2000.0}$ = 02$^{\rm h}$46$^{\rm m}$18$^{\rm s}$.9755" (2.1 Continuum emission); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00126.S, 2012.1.00187.S
- bands: Band 7  
  > "using the band 7 receiver (ID #2015.1.00126.S)" (Observations)
- frequencies and spectral setup: four spectral windows of 1.875 GHz each; one covers CO(3-2)  
  > "One of the four spectral windows (each with a width of 1.875 GHz) was used to fully cover the CO(3–2) emission line." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15.1 m to 3.1 km (cycle 3); 15.1 m to 1.6 km (cycle 1)  
  > "The projected baselines ranged from 15.1 m to 3.1 km" (Observations)
- angular resolution: 0.17 x 0.11 arcsec (combined CO cube)  
  > "0$''$.17 $\times$ 0$''$.11 (P.A. = 88$\ensuremath{^\circ}$.8) for the combined CO(3–2) cube" (Observations)
- max recoverable scale: ~7 arcsec  
  > "resulting in a maximum recoverable scale of $\sim 7\ensuremath{''}$" (Observations)
- sensitivity: 0.84 mJy/beam (CO cube, 10 km/s); 45-72 uJy/beam cycle 3 continuum; 70-110 uJy/beam cycle 1 continuum  
  > "0.84 mJy beam$^{-1}$ for the combined CO(3–2) cube (velocity resolution $dV$ = 10 km s$^{-1}$)" (Observations)
- time on source: 2.8 h cycle 3; 4.0 h combined  
  > "The total on-source time of the combined cube is 4.0 h." (Observations)
- observing dates: September 2016 (cycle 3)  
  > "in September 2016, with a total on-source time of 2.8 h" (Observations)
- pi or archival as stated: _not stated_
- Line: CO J=3-2 (345.796 GHz)
- Other facility **APEX**: 18 arcsec aperture CO(3-2) flux for comparison of recovered flux  
  > "we lost $\sim 75\%$ of the CO(3–2) flux as compared to the 18$\ensuremath{''}$ aperture Atacama Pathfinder EXperiment (APEX) telescope" (Observations)
- External data: CO(3-2)/CO(1-0) brightness temperature ratio 2.33 +/- 0.44  
  > "CO(3–2)/CO(1–0) brightness temperature ratio of 2.33 $\pm$ 0.44" (4 Discussion) [from (cite: 2012ApJ...747...90H)]
- External data: NIR H2 kinematic data (Vrot, sigma) used as initial guesses and comparison  
  > "estimated by the dynamical modeling of the NIR H$_2$ emission (cite: 2009ApJ...696..448H) were adopted as our initial guesses" (4 Discussion) [from (cite: 2009ApJ...696..448H)]
- External data: Xco = 0.5e20 cm-2 (K km/s)-1  
  > "By assuming a CO-to-H$_2$ conversion factor ($X_{\rm CO}$) of 0.5 $\times$ 10$^{20}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$" (4 Discussion) [from (cite: 2014A&A...567A.125G)]

## Processing

### Calibration

- pipeline or manual: standard manner in CASA  
  > "The reduction and calibration were conducted with CASA version 4.7" (Observations)
- casa version: CASA 4.7  
  > "CASA version 4.7" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~10%  
  > "The adopted absolute flux uncertainty was $\sim 10\%$ according to the ALMA Cycle 3 Proposer’s Guide" (Observations)
- self calibration: _not stated_

### Imaging

- task: CLEAN  
  > "reconstructed using the `CLEAN` task with Briggs weighting (robust = 0.5)" (Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "Briggs weighting (robust = 0.5)" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: in uv-plane, individually per execution  
  > "Continuum emission was subtracted individually from each execution data in the $uv$-plane." (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: cycle 3 and cycle 1 visibilities combined  
  > "we combined cycle 3 and cycle 1 visibilities" (Observations)
- smoothing: _not stated_
- final beam: 0.17 x 0.11 arcsec, PA 88.8 deg  
  > "0$''$.17 $\times$ 0$''$.11 (P.A. = 88$\ensuremath{^\circ}$.8) for the combined CO(3–2) cube" (Observations)
- final rms: 0.84 mJy/beam at 10 km/s  
  > "0.84 mJy beam$^{-1}$ for the combined CO(3–2) cube" (Observations)

### Inherited from earlier work

- Dust mass estimation method  
  > "Following the method in §3 of (cite: 2016ApJ...823L..12G), we estimated a mass of corresponding cold dust" (2.1 Continuum emission) [from (cite: 2016ApJ...823L..12G)]
- Subtracting a 2D rotation map to reveal non-circular motions  
  > "those can be revealed by subtracting the 2-dimensional rotation map from the observed data (cite: 2016ApJ...823...68S)" (4 Discussion) [from (cite: 2016ApJ...823...68S)]

### Not stated but needed to reproduce (our reading)

- Number of channels and line-free channels for continuum subtraction
- CLEAN threshold, masks, cell and image size
- Which executions/continuum windows were used per continuum map
- 3DBarolo parameter settings (mask, weighting, fit type, ring fitting order)
- Spectral-resolution smoothing procedure for MODEL-2
- Distance to NGC 1097 and adopted pc/arcsec scale
- Details of the uvfit fit
- Hatziminaoglou et al. in prep. results used for BH mass and synchrotron interpretation

## Analysis recipe

1. **Image combined cubes and continuum**: CLEAN with Briggs weighting on cycle 3 plus cycle 1 visibilities after uv continuum subtraction  
  > "All images presented in this paper were reconstructed using the `CLEAN` task with Briggs weighting (robust = 0.5)." (Observations)
   - software: CASA, MIRIAD
   - parameter: robust = 0.5  
  > "Briggs weighting (robust = 0.5)" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Test continuum size and variability**: Gaussian fit to visibilities with uvfit; compare flux per execution within r<~9 pc  
  > "A Gaussian fit to the visibilities with the MIRIAD task `uvfit` revealed that this emission was unresolved at our $\sim 7$ pc resolution." (2.1 Continuum emission)
   - software: MIRIAD
   - fitting: Gaussian in uv-plane  
  > "A Gaussian fit to the visibilities with the MIRIAD task `uvfit` revealed that this emission was unresolved at our $\sim 7$ pc resolution." (Result: Continuum emission)
   - validation: Variability exceeds flux uncertainty and simultaneous CO flux is constant  
  > "the simultaneously observed CO(3–2) flux remained almost constant over the executions" (2.1 Continuum emission)
3. **Upper limit on cold dust mass**: Modified blackbody applied to lowest continuum flux (0.25 +/- 0.08 mJy)  
  > "An upper limit on thermal dust emission then comes from our *lowest* continuum flux, i.e., 0.25 $\pm$ 0.08 mJy." (2.1 Continuum emission)
   - assumption: beta = 2, kappa_352GHz = 0.0865 m2/kg, Tdust = 150 K  
  > "A dust temperature of 150 K was assumed" (2.1 Continuum emission)
   - fitting: _not stated_
   - validation: Lowering Tdust by 50% raises Mdust by ~50%  
  > "If we decrease the dust temperature by 50%, $M_{\rm dust}$ is accordingly increased by $\sim 50$%" (2.1 Continuum emission)
4. **H2 mass and column density at AGN position**: Convert CO(3-2) intensity in one beam to CO(1-0) with r31 then apply Xco  
  > "was converted to that of CO(1–0) by using a CO(3–2)/CO(1–0) brightness temperature ratio of 2.33 $\pm$ 0.44" (4 Discussion)
   - parameter: beam 0.17 x 0.14 arcsec at AGN position  
  > "a single beam (0$''$.17 $\times$ 0$''$.14, P.A. = 88$\ensuremath{^\circ}$.8) placed at the AGN position" (4 Discussion)
   - assumption: Xco = 0.5e20 cm-2 (K km/s)-1  
  > "0.5 $\times$ 10$^{20}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$" (4 Discussion)
   - fitting: _not stated_
   - validation: Compared with NGC 1068 where Xco-based and dust-based masses agree  
  > "agrees fairy well for the molecular torus of NGC 1068" (4 Discussion)
5. **Tilted-ring kinematic modeling**: 3DBarolo tilted-ring fits with 19 rings of 0.05 arcsec; Vrot, sigma, i, PA free; MODEL-1 full resolution, MODEL-2 spectral resolution matched to NIR H2  
  > "We modeled 19 concentric rings of $\Delta r$ = 0$\ensuremath{''}$.05 from the center." (4 Discussion)
   - software: 3DBarolo
   - parameter: Vsys = 1254 km/s, center at AGN position  
  > "Our initial fits indicated a dynamical center as the AGN position, $V_{\rm sys}$ as 1254 km s$^{-1}$." (4 Discussion)
   - assumption: sigma/Vrot as proxy for disk aspect ratio under vertical hydrostatic equilibrium  
  > "A $\sigma/V_{\rm rot}$ is often used as a proxy of the aspect ratio of a disk under the vertical hydrostatic equilibrium." (Footnote 2)
   - fitting: Initial guesses from NIR H2 modeling; sampler/priors not stated  
  > "The $V_{\rm rot}$ and $\sigma$ estimated by the dynamical modeling of the NIR H$_2$ emission (cite: 2009ApJ...696..448H) were adopted as our initial guesses for the CO(3–2) modeling." (Discussion on the torus and summary)
   - validation: PVDs overlaid on data; comparison with NIR H2 Vrot and sigma  
  > "show the position velocity diagrams (PVDs) along the global kinematic major and minor axes, overlaid on the observed data" (4 Discussion)

## Software

- **CASA** 4.7: reduction, calibration and CLEAN imaging  
  > "The reduction and calibration were conducted with CASA version 4.7" (Observations)
- **MIRIAD** : further analysis of combined cubes, uvfit  
  > "Our combined cubes were further analyzed with MIRIAD" (Observations)
- **3DBarolo** : tilted-ring fits to velocity and dispersion maps  
  > "we fitted tilted-rings to these observed maps with the $^{\rm 3D}$Barolo code" (4 Discussion)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean 350 GHz continuum flux (central r<~9 pc) | 1.3 | not stated | mJy | 2 | factor $\sim 2-5$ around the mean = 1.3 mJy |
| Lowest continuum flux | 0.25 | 0.08 | mJy | 2 | 0.25 $\pm$ 0.08 mJy |
| Cold dust mass upper limit | <530 | 30 | Msun | 3 | $M_{\rm dust}$ $<$ 530 $\pm$ 30 $M_\Sun$ |
| CO(3-2) integrated intensity at AGN | 2.04 | 0.21 | Jy/beam km/s | 4 | 2.04 $\pm$ 0.21 Jy beam$^{-1}$ km s$^{-1}$ |
| M_H2 in beam at AGN | 5.4e4 | 0.4e4 | Msun | 4 | $M_{\rm H_2}$ = (5.4 $\pm$ 0.4) $\times$ 10$^4$ $M_\Sun$ |
| N_H2 | 1.9e22 | 0.4e22 | cm-2 | 4 | $N_{\rm H_2}$ = (1.9 $\pm$ 0.4) $\times$ 10$^{22}$ cm$^{-2}$ |
| Systemic velocity | 1254 | not stated | km/s | 5 | $V_{\rm sys}$ as 1254 km s$^{-1}$ |
| Kinematic PA | ~118 | not stated | deg | 5 | kinematic P.A. $\simeq 118\ensuremath{^\circ}$ |
| sigma/Vrot at r<10 pc (MODEL-1) | <~0.65 | not stated | dimensionless | 5 | at the central $r < 10$ pc ($\lesssim 0.65$; MODEL-1) |
| Torus scale height at r=7 pc | ~4.5 | not stated | pc | 5 | is then $\sim 4.5$ pc at $r = 7$ pc |

## Qualitative findings

- No distinct compact molecular torus is seen in CO(3-2) at the AGN position; the AGN is offset ~10 pc from the CO arc.  
  > "a distinctive and compact molecular torus is missing at the AGN position of NGC 1097 in this CO(3–2) map" (2.2 CO(3–2) emission)
- The 350 GHz continuum is time-variable and unresolved, likely dominated by synchrotron emission.  
  > "the band 7 continuum is dominated by this time-varying component" (2.1 Continuum emission)

## Claim tuples

- H: A NGC 1068-like dense compact cold torus exists in NGC 1097 | E: CO(3-2) and continuum mapping at ~10 pc | R: No compact torus; the gas mass is a factor >~2-3 lower than NGC 1068 | F: There is less torus gas in this LLAGN | **supported**
- H: The cold gas layer is thinner than the hot NIR H2 gas | E: 3DBarolo modeling of CO velocity field and comparison with NIR H2 | R: CO sigma/Vrot is smaller than NIR H2 at r<~20 pc | F: Cold gas lies in a thinner layer; the torus is thinner than in NGC 1068 | **partially**

## Reasoning

- Why this data: A low-luminosity AGN where thick tori may be deficient due to insufficient energy input.  
  > "where thick tori may be *deficient* due to insufficient energy input" (Introduction)
- Why this method: _not stated_
- Alternative: High gas excitation at the center was rejected as the cause of the missing torus, since HCN(4-3) shows a similar distribution.  
  > "This is not due to too high gas excitation conditions at the center as we find a similar distribution in an HCN(4–3) integrated intensity map" (2.2 CO(3–2) emission)
- How they decided it was enough: _not stated_
- Limitation (authors): Xco has ~0.3 dex uncertainty not included, and absolute difference in gas dynamics is poorly constrained at the center.  
  > "A $\sim 0.3$ dex uncertainty of this $X_{\rm CO}$ is not considered here." (Footnote 1)
- Caveat (inferred, ours): Xco and r31 are taken from other scales and may not hold for the nucleus
- Caveat (inferred, ours): Kinematic result depends strongly on spectral resolution (MODEL-1 vs MODEL-2)
- Caveat (inferred, ours): Single-object comparison with NGC 1068 via literature values
- Caveat (inferred, ours): Key supporting results are in preparation papers

## Reproducibility

- Data public (paper): ALMA data identified by project codes; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00126.S and #2012.1.00187.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Clean parameters and masks
- Missing: 3DBarolo configuration
- Missing: Smoothing procedure for MODEL-2
- Missing: Adopted distance
- Data volume (inferred): ~100-300 GB raw for two projects
- Score (inferred): 3/5, Public data and named tools, but imaging and Barolo settings are sparse.
- Rediscovery candidate: no, Recipe incomplete for kinematic modeling and key parameters are unstated.

## Links

- Method: (cite: 2015MNRAS.451.3021D) (3DBarolo)
- Method: (cite: 2016ApJ...823L..12G) (dust mass method)
- Companion: Hatziminaoglou et al. (in prep.) (cycle 1 data, black hole mass and SED modeling)
- Companion: Kohno et al. (in prep.) (HCN(4-3) map)

## Checks

```json
{
 "quotes": 67,
 "quotes_ok": 67,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 51,
  "rate": 0.662
 },
 "evidence_ok": true
}
```

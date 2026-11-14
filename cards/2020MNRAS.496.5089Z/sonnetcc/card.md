# The Ophiuchus DIsc Survey Employing ALMA (ODISEA) - II. The effect of stellar multiplicity on disc properties

`2020MNRAS.496.5089Z` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Zurlo, Alice | arXiv: 2006.16259 | DOI: 10.1093/mnras/staa1886

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, protoplanetary_disks
- Question: How does stellar multiplicity (companions found with NIR adaptive optics imaging) affect the dust mass and size of circumstellar discs in Ophiuchus?  
  > "One of the main objectives of ODISEA is to study the dependence of disc properties on stellar multiplicity." (Introduction)
- Target **ODISEA sample of circumstellar discs in the Ophiuchus molecular cloud (289 objects; 164 observed in NIR AO)**: coordinates _not stated_; z/distance 140 pc assumed for dust masses; per-system distances used for projected separations  
  > "The projected separation of the companion in au was calculated for each target assuming the distances for each system listed in (cite: 2019ApJ...875L...9W)." (Results and discussion); "This conversion from observed mm flux to dust mass assumes a distance of 140 pc, a dust temperature of 20K" (Results and discussion); distance from per-system distances listed in (cite: 2019ApJ...875L...9W)  
  > "The projected separation of the companion in au was calculated for each target assuming the distances for each system listed in (cite: 2019ApJ...875L...9W)." (Results and discussion); "This conversion from observed mm flux to dust mass assumes a distance of 140 pc, a dust temperature of 20K" (Results and discussion)

## Data provenance

- ALMA projects: 2016.1.00545.S
- bands: 1.3 mm  
  > "Combining our results with the ODISEA ALMA 1.3 mm data, archival NIR AO data and multiplicity information from the literature" (Summary and conclusion)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Sample A: C40-5; Sample B: C40-3  
  > "which consists of 147 targets observed under the Cycle-4 ALMA programme 2016.1.00545.S, with the antennas configuration C40-5." (ALMA 1.3 mm data); "these 142 other objects were observed with a different antennas configuration (C40-3 array), under the same program." (ALMA 1.3 mm data)
- baselines: _not stated_
- angular resolution: Sample A: 0.28" x 0.19"; Sample B: ~0.98" x 0.74"  
  > "For this sample the typical rms is of $\sim 0.15$ mJy/beam with a synthesized beam of 0.28$''$$\times$0.19$''$." (ALMA 1.3 mm data); "For sample B, the sensitivity is $\sim 0.2$ mJy/beam, the beam size is $\sim$ 0.98$''$$\times$0.74$''$." (ALMA 1.3 mm data)
- max recoverable scale: _not stated_
- sensitivity: Sample A: ~0.15 mJy/beam rms; Sample B: ~0.2 mJy/beam  
  > "For this sample the typical rms is of $\sim 0.15$ mJy/beam with a synthesized beam of 0.28$''$$\times$0.19$''$." (ALMA 1.3 mm data); "For sample B, the sensitivity is $\sim 0.2$ mJy/beam, the beam size is $\sim$ 0.98$''$$\times$0.74$''$." (ALMA 1.3 mm data)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **VLT/NACO**: L' AO imaging of 70 stars (88 observed in total); companion detection, separations, flux ratios  
  > "The observations with NACO were carried out from April 8 to April 11, 2017 (4 half nights), program 099.C-0465 (PI: Zurlo)." (VLT/NACO)
- Other facility **Keck/NIRC2**: L' AO imaging of 51 stars; companion detection, separations, flux ratios  
  > "Observations with Keck/NIRC2 were carried out during the nights from the 8 to the 10 June 2017 (3 half nights), program GN-2017A-Q-29 (PI: Williams)." (Keck/NIRC2)
- Other facility **ESO and Keck archives**: Archival NIR data for 13 sample objects; all found to be single stars  
  > "We found 13 objects of our sample in the ESO and Keck archives." (Archive data); "In conclusion, all the stars with archival data are single stars." (Archive data)
- External data: ALMA 1.3 mm fluxes (Sample B) and system distances used for dust masses and projected separations  
  > "we multiplied the millimeter flux in mJy (cite: 2019ApJ...875L...9W) by 0.58" (Results and discussion); "assuming the distances for each system listed in (cite: 2019ApJ...875L...9W)" (Results and discussion) [from (cite: 2019ApJ...875L...9W)]
- External data: Literature multiplicity information for ODISEA stars  
  > "(cite: 2009ApJ...696L..84C) collected multiplicity information for 349 stars in nearby star-forming regions, including 73 objects that are part of the ODISEA sample." (The ODISEA Sample and literature data) [from (cite: 2009ApJ...696L..84C); (cite: 2013ApJ...762..100C); (cite: 2015ApJ...813...83C); (cite: 2017ApJ...851...83C); (cite: 2018AJ....155..109S)]
- External data: L' magnitude derived from 2MASS K using colours for different spectral types  
  > "using the color for the different spectral types as in (cite: 2015A&A...574A..78S)" (Results and discussion) [from (cite: 2015A&A...574A..78S)]
- External data: Individual K-band extinction values for 20 multiple systems  
  > "Individual extinction values are listed in (cite: 2020AJ....159..282E) for 20 of the multiple systems." (Results and discussion) [from (cite: 2020AJ....159..282E)]
- Simulation/model as data: AMES-COND evolutionary models used to convert absolute magnitude to companion mass  
  > "To convert the absolute magnitude into mass we used the AMES-COND evolutionary models by (cite: 2001ApJ...556..357A)." (Results and discussion)

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
- final beam: Sample A 0.28" x 0.19"; Sample B ~0.98" x 0.74"  
  > "For this sample the typical rms is of $\sim 0.15$ mJy/beam with a synthesized beam of 0.28$''$$\times$0.19$''$." (ALMA 1.3 mm data); "For sample B, the sensitivity is $\sim 0.2$ mJy/beam, the beam size is $\sim$ 0.98$''$$\times$0.74$''$." (ALMA 1.3 mm data)
- final rms: Sample A ~0.15 mJy/beam; Sample B ~0.2 mJy/beam  
  > "For this sample the typical rms is of $\sim 0.15$ mJy/beam with a synthesized beam of 0.28$''$$\times$0.19$''$." (ALMA 1.3 mm data); "For sample B, the sensitivity is $\sim 0.2$ mJy/beam, the beam size is $\sim$ 0.98$''$$\times$0.74$''$." (ALMA 1.3 mm data)

### Inherited from earlier work

- ALMA data reduction and presentation for Sample A  
  > "For the ALMA data reduction and presentation we refer the reader to paper I (cite: 2019MNRAS.482..698C) for Sample A" (ALMA 1.3 mm data) [from paper I (cite: 2019MNRAS.482..698C)]
- ALMA data reduction and presentation for Sample B  
  > "For Sample B we refer the reader to (cite: 2019ApJ...875L...9W)" (ALMA 1.3 mm data) [from (cite: 2019ApJ...875L...9W)]
- Flux-to-dust-mass conversion factor of 0.58 Earth masses per mJy  
  > "we multiplied the millimeter flux in mJy (cite: 2019ApJ...875L...9W) by 0.58 (cite: 1990AJ.....99..924B; 2005ApJ...631.1134A; 2019MNRAS.482..698C)." (Results and discussion) [from (cite: 1990AJ.....99..924B; 2005ApJ...631.1134A; 2019MNRAS.482..698C)]
- Identification of the multiple systems detected in the millimeter  
  > "Multiple systems were identified and presented in (cite: 2019MNRAS.482..698C): one triple system and 11 binaries were detected in the millimeter." (ALMA 1.3 mm data) [from (cite: 2019MNRAS.482..698C)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration and imaging recipe (CASA version, robust, cleaning, masking) for both samples; deferred to Paper I and Williams et al. 2019
- ALMA flux measurements and disc sizes (semi-major axes) for each source; only available via cited tables
- Parameters of the VIP high-pass filter and bad-pixel removal
- How NIR flux ratios and companion positions were measured (aperture or PSF fitting, uncertainties)
- Spectral types and stellar masses of the ODISEA targets (deferred to Ruiz-Rodriguez et al. in prep.)
- Lifelines estimator settings and how sources with no IR excess were handled in the Kaplan-Meier fits
- Exact definition of per-system versus per-star mass and how the 5 categories were assigned for each source

## Analysis recipe

1. **Reduce NIR AO images**: Background subtraction between the two exposures, flat-fielding, recentring, bad-pixel removal and high-pass spatial filtering; final image is the mean of the recentred frames  
  > "The raw data, two exposures per star, were background subtracted one from the other, flat-fielded, then recentered to have the target in the center of the detector." (VLT/NACO); "Finally, in order to reduce the effects of atmospheric turbulences on the images, a high-pass spatial filter has been used." (VLT/NACO)
   - software: VIP
   - parameter: NACO: L' filter, N90C10 AO configuration, exposure 0.16-0.17 s, two exposures of 200 NDIT each  
  > "For each star we took two exposures (of 200 NDIT[^3] each), where the star fell in two different quadrants of the detector to permit a quasi-simultaneous subtraction of the background." (VLT/NACO)
   - parameter: NACO pixel scale 0.02712 arcsec/pixel; NIRC2 pixel scale 0.009942 arcsec/pixel  
  > "The pixel scale of the NACO detector is 0.02712 arcsec/pixel." (VLT/NACO); "The pixel scale of the NIRC2 detector is 0.009942 arcsec/pixel" (Keck/NIRC2)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure companion separation, position angle and flux ratios**: Astrometry referenced to the ALMA centroid of the primary (the disc with highest flux); separation in au from per-system distances; NIR and mm flux ratios tabulated  
  > "To calibrate the astrometric position of the central star we adopted the coordinates given by the ALMA centroid of the primary star" (VLT/NACO); "For each binary system we calculated the position of the companion and its flux ratio with respect to the primary." (Results and discussion)
   - assumption: Primary is assumed to be the disc with highest flux  
  > "The primary was assumed to be the disc with highest flux." (VLT/NACO)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive companion masses**: 2MASS K magnitudes converted to L' with spectral-type colours, corrected for K-band extinction, converted to mass with AMES-COND models  
  > "To calculate the mass we used the 2MASS K band photometry, available for all the primaries, then we derived the L$^{\prime}$ magnitude using the color for the different spectral types as in (cite: 2015A&A...574A..78S)." (Results and discussion); "To convert the absolute magnitude into mass we used the AMES-COND evolutionary models by (cite: 2001ApJ...556..357A)." (Results and discussion)
   - assumption: Extinction in K band taken into account  
  > "Extinction in K band has also been taken into account." (Results and discussion)
   - fitting: _not stated_
   - validation: Primary of GY92 367 shows no brown-dwarf features in its IR spectrum, suggesting possible background contamination  
  > "However, we note that the IR spectrum of the primary does not show the features expected in a brown dwarf" (Results and discussion)
4. **Convert mm flux to disc dust mass**: Dust mass in Earth masses = millimeter flux in mJy multiplied by 0.58  
  > "we multiplied the millimeter flux in mJy (cite: 2019ApJ...875L...9W) by 0.58" (Results and discussion)
   - assumption: Distance of 140 pc and dust temperature of 20 K  
  > "This conversion from observed mm flux to dust mass assumes a distance of 140 pc, a dust temperature of 20K" (Results and discussion)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compare dust mass distributions by multiplicity category**: Sample split into five categories; cumulative distributions with Kaplan-Meier product estimator to handle non-detections  
  > "we divided the sample into five categories: single objects, multiple discs where all components are detected and resolved by ALMA, multiple systems unresolved by ALMA, binaries where one or both the components are not detected in the mm, and binaries without IR excess." (Results and discussion); "For non-detections, we used the Kaplan-Meier (KM) product estimator." (Results and discussion)
   - software: lifelines
   - assumption: For resolved multiple discs the system mass is the sum of the components; per-star mass is the system mass divided by two  
  > "In the case where each component is resolved, the total mass of the system is the sum of the mass of each component." (Results and discussion); "In the latter case, the total disc dust mass are divided by two." (Results and discussion)
   - fitting: _not stated_
   - validation: _not stated_
6. **Relate disc mass and size to projected separation**: Dust mass and disc semi-major axis plotted against projected separation between primary and companion  
  > "show the correlation between the dust mass and the size of the disc as a function of the projected separation between the primary and the companion." (Results and discussion)
   - fitting: _not stated_
   - validation: Deconvolved sizes below the beam are only possible for high signal-to-noise detections and must be interpreted with caution  
  > "However, we emphasize that the deconvolved disc sizes must be interpreted with caution." (Results and discussion)

## Software

- **VIP** : Reduction of NACO and NIRC2 NIR AO images  
  > "The data were reduced with the python Vortex Image Processing" (VLT/NACO)
- **lifelines** : Kaplan-Meier cumulative distribution functions of dust mass for each category  
  > "The python package lifelines (cite: 2019JOSS....4.1317D) was used to estimate the cumulative distribution functions for each category" (Results and discussion)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| New binary systems detected | 20 | not stated | systems | 2 | We detect 20 new binary systems and one new triple system. |
| NIR-ODISEA stars observed in NIR AO for the first time | 147 | not stated | stars | 1 | The NIR-ODISEA survey consists of 147 stars observed in NIR AO imaging for the first time |
| Companions in the sub-stellar regime | 9 (30-50 MJup) | not stated | MJup | 3 | Nine companions are in the sub-stellar regime (30-50 M$_{\mathrm{Jup}}$). |
| Mass of GY92 367 b (C5_090b) | 14 | not stated | MJup | 3 | One object, GY92 367 b (C5_090b), is in the planetary regime (14 M$_{\mathrm{Jup}}$) |
| Multiplicity occurrence rate of ODISEA | 18% (43/236) | not stated | percent | 2 | The total number of multiple systems of ODISEA is 43, so the occurrence rate is 18% (43/236). |
| Occurrence rate of visual binaries among diskless Ophiuchus stars | 30% | not stated | percent | 2 | the ocurrence rate of visual binaries in the diskless stars in Ophiuchus is 30$\%$ |
| Maximum disc dust mass in multiple systems vs single stars | ~50 (multiples) vs 200 (singles) | not stated | Earth masses | 5 | Discs in multiple systems reach a maximum total dust mass of $\sim$ 50 M$_{\oplus}$, while discs in single stars can reach a dust mass of 200 M$_{\oplus}$. |
| Projected separation above which discs with masses above 10 Earth masses are found | ~110 | not stated | au | 6 | Discs with masses above 10 M$_{\oplus}$ are found only around binaries with projected separations larger than $\sim$ 110 au. |
| NACO and NIRC2 contrast limits (companion flux fainter than primary) | NACO ~50 times; NIRC2 ~100 times | not stated | flux ratio | 1 | in general companions with a flux 50 times fainter than the primary are detected.; allowing the detection of companions 100 times fainter than the primary. |

## Qualitative findings

- Discs around primaries tend to be more massive than discs around companions  
  > "Primary stars tend to have more massive discs than secondaries." (Summary and conclusion)
- Effect of visual binaries is weak in the general disc population because most Ophiuchus discs are small and low-mass  
  > "However, since most discs in Ophiuchus are very small and low-mass, the effect of visual binaries is relatively weak in the general disc population." (abstract)

## Claim tuples

- H: Stellar companions limit the maximum dust mass of circumstellar discs | E: NIR AO multiplicity survey of ODISEA targets combined with ALMA 1.3 mm fluxes converted to dust masses, with Kaplan-Meier cumulative distributions by category | R: Single and multiple systems have similar distributions up to 50 Earth masses; masses up to 200 Earth masses occur only around single stars | F: Discs in multiple systems reach lower maximum dust masses than discs around single stars | **supported**
- H: Disc mass and size depend on the projected separation of the companion | E: Dust mass and disc semi-major axis versus projected separation for resolved binaries | R: Massive, big discs are found only around wide binaries (>100 au); unresolved low-mass discs are in close binaries below 150 au | F: Close companions truncate discs while wide companions have little effect | **supported**
- H: Visual binaries strongly affect the general disc population of Ophiuchus | E: Comparison of dust mass and size distributions of singles and multiples across the full ODISEA sample | R: Differences appear only in the tails of the distributions | F: The effect of visual binaries is weak for the general, mostly small and low-mass, disc population | **partially**
- H: NIR AO imaging of ODISEA discs reveals previously unknown companions including sub-stellar ones | E: L' band NACO and NIRC2 imaging of 147 new targets plus revisits of known binaries | R: 20 new binaries and one triple detected; 9 companions of 30-50 MJup | F: The visual multiplicity of ODISEA is 18%, likely a lower bound | **supported**

## Reasoning

- Why this data: NACO and NIRC2 chosen for efficiency with short exposures and small overheads  
  > "These two instruments were chosen for their efficiency in taking short exposures with small overheads." (Observations and data reduction)
- Why this method: N90C10 AO configuration chosen for stable AO on faint targets  
  > "Given the faintness of our targets, we chose the AO configuration N90C10 which provides NAOS with 90% of the stars light and the detector with the remaining 10%." (VLT/NACO)
- How they decided it was enough: _not stated_
- Limitation (authors): Observed multiplicity rate is biased because only members with discs are included  
  > "Notice that this rate is biased by the fact that, in ODISEA, only Ophiuchus members with discs are included." (Results and discussion)
- Limitation (authors): Multiplicity census incomplete for separations below 10 au and for diskless stars  
  > "the multiplicity census in Ophiuchus is very incomplete for separations smaller than 10 au and for diskless stars." (Results and discussion)
- Limitation (authors): Deconvolved disc sizes below the beam must be interpreted with caution  
  > "However, we emphasize that the deconvolved disc sizes must be interpreted with caution." (Results and discussion)
- Limitation (authors): 29 targets too faint for NIR AO and excluded from statistics  
  > "Therefore, they are not observable in NIR with the current AO-imaging instruments from the ground." (The ODISEA Sample and literature data)
- Caveat (inferred, ours): Dust masses use a single flux conversion (0.58 Earth masses per mJy at 140 pc, 20 K) for all stellar masses and no optical depth correction
- Caveat (inferred, ours): Two ALMA samples have very different resolution and sensitivity, so categories mix detection biases
- Caveat (inferred, ours): Companion flux ratio detection thresholds were not quantified per target
- Caveat (inferred, ours): Stellar mass dependence of disc mass is not controlled when comparing singles and binaries

## Reproducibility

- Data public (paper): Data underlying the article are in the article and its online supplementary material  
  > "The data underlying this article are available in the article and in its online supplementary material." (Data availability)
- Products in archive: _not stated_
- Missing: Per-source ALMA fluxes and disc sizes (in cited Williams et al. 2019 and Paper I)
- Missing: VIP reduction parameters
- Missing: Companion photometry method
- Missing: Spectral types and extinctions for all targets
- Data volume (inferred): Small for the NIR images; the ALMA part uses published fluxes (ALMA ODISEA Cycle-4 continuum, tens of GB if re-imaged)
- Score (inferred): 3/5, Observing programs and project code are given, the dust-mass recipe is simple, and the binary table is printed, but ALMA reduction is deferred to other papers and the NIR companion photometry and filter settings are not given.
- Rediscovery candidate: no, ALMA reduction and source fluxes live in other papers, and the main results are mostly counts and distribution comparisons rather than fitted numeric values.

## Links

- Method: (cite: 2019MNRAS.482..698C) (Paper I: ALMA data reduction and presentation for Sample A and multiple-system identification)
- Method: (cite: 2019ApJ...875L...9W) (ALMA Sample B reduction, fluxes and distances)
- Method: (cite: 2017AJ....154....7G) (VIP package used for NIR AO reduction)
- Companion: Ruiz-Rodriguez et al. (in prep) (Spectral types and stellar masses of all ODISEA targets)
- Related: ODISEA (Ophiuchus Disc Survey Employing ALMA)

## Checks

```json
{
 "quotes": 78,
 "quotes_ok": 78,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 1,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 87,
  "stated": 46,
  "rate": 0.529
 },
 "evidence_ok": true
}
```

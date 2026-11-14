# Internal Structures of Molecular Clouds in the LMC Revealed by ALMA

`2018ApJ...867..166S` | The Astrophysical Journal 2018 | first author: Sawada, Tsuyoshi | arXiv: 1812.06001 | DOI: 10.3847/1538-4357/aae395

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation, milky_way_ism
- Question: How do the internal structures of LMC GMCs vary from quiescent to actively star-forming clouds, characterized by the brightness distribution function and index?  
  > "This paper aims to bridge the gap between these two extremes, clouds with very active star formation and those in the quiescent phase, and investigate the evolutionary trend." (Introduction)
- Target **GMC 2**: coordinates 4h47m35s, -67d13m00s (J2000)  
  > "| 2      | $4^{\rm h} 47^{\rm m} 35^{\rm s}$ | $-67\ensuremath{^\circ} 13\ensuremath{'} 00\ensuremath{''}$ |" (Table 2); z/distance _not stated_; distance from _not stated_
- Target **GMC 55**: coordinates 5h07m45s, -68d59m30s (J2000)  
  > "| 55     | $5^{\rm h} 07^{\rm m} 45^{\rm s}$ | $-68\ensuremath{^\circ} 59\ensuremath{'} 30\ensuremath{''}$ |" (Table 2); z/distance _not stated_; distance from _not stated_
- Target **GMC 197**: coordinates 5h39m50s, -70d07m00s (J2000)  
  > "| 197    | $5^{\rm h} 39^{\rm m} 50^{\rm s}$ | $-70\ensuremath{^\circ} 07\ensuremath{'} 00\ensuremath{''}$ |" (Table 2); z/distance _not stated_; distance from _not stated_
- Target **GMC 216**: coordinates 5h44m35s, -69d26m00s (J2000)  
  > "| 216    | $5^{\rm h} 44^{\rm m} 35^{\rm s}$ | $-69\ensuremath{^\circ} 26\ensuremath{'} 00\ensuremath{''}$ |" (Table 2); z/distance _not stated_; distance from _not stated_
- Target **GMC 225**: coordinates 5h47m20s, -70d41m30s (J2000)  
  > "| 225    | $5^{\rm h} 47^{\rm m} 20^{\rm s}$ | $-70\ensuremath{^\circ} 41\ensuremath{'} 30\ensuremath{''}$ |" (Table 2); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00641.S
- bands: Band 3  
  > "The target five GMCs were observed with ALMA using the Band 3 receivers" (3 Observations)
- frequencies and spectral setup: 469 MHz wide, 3840-channel window (244 kHz = 0.64 km/s) at CO J=1-0; three 2 GHz low-resolution continuum windows  
  > "A 469 MHz wide, 3840-channel, dual-polarization spectral window ($244\;{\rm kHz}= 0.64\;{\rm km\,s^{-1}}$ resolution) was placed at the frequency of the CO $J=1\mbox{--}0$ line" (3 Observations)
- continuum bandwidth: _not stated_
- arrays: ALMA 12 m, 7 m (ACA), Total Power  
  > "we combine and jointly deconvolve the data from the ALMA 12 m, 7 m, and Total-Power (TP) arrays." (Introduction)
- configurations: _not stated_
- baselines: 12 m: 14-450 m; 7 m: 7-35 m  
  > "the $u\mbox{--}v$ distance typically ranged from 14 to 450 m" (3 Observations); "7–35 m, respectively" (3 Observations)
- angular resolution: convolution beams 2.2-2.6 arcsec, smoothed to 3.0 arcsec (0.73 pc)  
  > "we smoothed the maps to a common $3.0\ensuremath{''}$ resolution (0.73 pc) along both the major and minor axes of the beams." (4 Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: 0.47-0.67 K (45-66 mJy/beam) at 1 km/s  
  > "at which the sensitivity ranges between 0.47 and 0.67 K (45–66 ${\rm mJy\,beam^{-1}}$)" (4 Data Reduction)
- time on source: 12 m: ~540 s per object (20 s/pointing); 7 m: ~1000 s; TP: ~60 min per antenna  
  > "The total on-source integration time per object was typically 540 s (20 s per mosaic pointing)" (3 Observations); "The typical total on-source time (per antenna) and $T_{\rm sys}$ were 60 minutes and 140 K, respectively." (3 Observations)
- observing dates: 12 m: 2013 Dec; 7 m: 2013 Nov-Dec and 2014 Apr; TP: 2015 May-Jun  
  > "were made in 2013 December." (3 Observations); "The TP array observations were carried out in 2015 May and June" (3 Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=1-0 (115.271 GHz)
- Other facility **Mopra**: CO J=1-0 map at 45 arcsec for comparison contours  
  > "contours from the Mopra CO $J=1\mbox{--}0$ integrated intensity (cite: wong2011)" (5 Results)
- Other facility **Spitzer**: 8 um fluxes and color images  
  > "calculated from the *Spitzer Space Telescope* 8 $\ensuremath{\mu}m$ images (cite: meixner2006)" (2.1 Considerations)
- Other facility **NANTEN**: GMC catalog and CO masses  
  > "which consists of 272 clouds in the LMC from the $^{12}{\rm CO}$ $J=1\mbox{--}0$ survey with the NANTEN 4 m telescope" (2 Target Selections)
- External data: GMC radius, CO mass and types from NANTEN catalog  
  > "$^{a}$ From the NANTEN survey (cite: fukui2008)" (Table 1) [from (cite: fukui2008)]
- External data: YSO counts from Seale et al.  
  > "The number of “probable” YSOs (cite: seale2014) within 30 and 45 pc radii" (Table 1) [from (cite: seale2014)]
- External data: Dust temperatures  
  > "$^{d}$ (cite: gordon2014)" (Table 1) [from (cite: gordon2014)]

## Processing

### Calibration

- pipeline or manual: Delivered data calibrated by observatory with CASA; statwt applied  
  > "were delivered by the observatory and were calibrated using the Common Astronomy Software Applications (cite: mcmullin2007)." (4 Data Reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Uranus or J0519-4546 (12 m); solar system object or J0519-4546 (7 m); 3C 279 for TP gains  
  > "Either Uranus or the radio galaxy J0519$-$4546, whose flux was monitored by the observatory, was observed in each execution as the flux calibrator." (3 Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: Miriad mossdi2 (image-based clean) after invert  
  > "We ran the `mossdi2` task for image-based clean." (4 Data Reduction)
- deconvolver: 4 million iterations, gain 0.05; residual scaling of Jorsater & van Moorsel  
  > "We set the number of iterations to 4 million and the `gain` parameter to 0.05." (4 Data Reduction)
- weighting robust: natural weighting  
  > "inverted to dirty map and beam with the natural weighting" (4 Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: TP spectral baselines removed by straight-line fits to emission-free channels  
  > "We subtracted spectral baselines from the delivered TP map by fitting straight lines to emission-free channels." (4 Data Reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: TP converted to visibilities with TP2VIS, joint deconvolution with 12m+7m; TP weight from TP map rms  
  > "We adopted the TP weight that corresponds to the rms noise in the TP map." (4 Data Reduction)
- smoothing: common 3.0 arcsec; 1 km/s channels (2 km/s for BDF)  
  > "We use a velocity channel spacing of $1\;{\rm km\,s^{-1}}$" (4 Data Reduction)
- final beam: _not stated_
- final rms: 0.46-0.67 K at 3"x3"x1 km/s  
  > "$^{a}$ At $3\ensuremath{''} \times 3\ensuremath{''} \times 1\;{\rm km\,s^{-1}}$ resolution" (Table 2)

### Inherited from earlier work

- TP2VIS procedure for combining TP and interferometer data  
  > "This procedure is discussed and tested in depth in our previous paper (cite: koda2011)." (4 Data Reduction) [from (cite: koda2011)]
- BDI brightness thresholds (3,5,10,inf) K  
  > "the same brightness thresholds used for the MW analysis in (cite: sawada2012)" (6.1) [from (cite: sawada2012)]
- Residual scaling scheme  
  > "we used the residual scaling scheme of (cite: Jorsater1995)." (4 Data Reduction) [from (cite: Jorsater1995)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for TP baseline fitting
- Clean masks/threshold and cell/image size
- Exact TP2VIS parameters and weights
- Which execution blocks used which flux calibrators
- Noise/pixel selection for BDI calculation (e.g. masking, handling of edges)
- Distance to LMC used for pc conversion

## Analysis recipe

1. **Calibrate and prepare data**: Observatory-calibrated data; TP baseline subtraction; statwt reweighting of 12 and 7 m visibilities  
  > "We also applied the correction for the weights of 12 and 7 m visibilities with the `statwt` task in CASA" (4 Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Joint deconvolution of 12m+7m+TP**: TP map converted to visibilities via TP2VIS, combined in uv space, Miriad invert and mossdi2 clean with residual scaling, smoothed to 3"  
  > "We combined the 12 m, 7 m, and TP data in $u$–$v$ space and deconvolved them jointly." (4 Data Reduction)
   - software: CASA, TP2VIS, Miriad
   - parameter: 4 million iterations, gain 0.05, natural weighting  
  > "We set the number of iterations to 4 million and the `gain` parameter to 0.05." (4 Data Reduction)
   - fitting: _not stated_
   - validation: Flux consistency with TP map addressed by residual scaling  
  > "It is often a problem that the flux of the cleaned map is not consistent with that of the TP map." (4 Data Reduction)
3. **Derive cloud masses**: CO luminosity converted to H2 mass in ALMA FoV  
  > "We adopt a CO-to-${\rm H_2}$ conversion factor of $7\times 10^{20}\;{\rm cm^{-2}\,(K\,km\,s^{-1})^{-1}}$ (cite: fukui2008)." (5 Results)
   - assumption: X_CO = 7e20 cm^-2 (K km/s)^-1  
  > "We adopt a CO-to-${\rm H_2}$ conversion factor of $7\times 10^{20}\;{\rm cm^{-2}\,(K\,km\,s^{-1})^{-1}}$ (cite: fukui2008)." (5 Results)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compute BDF and BDI**: Histogram of pixel brightness in position-position-velocity at 2 km/s resolution; BDI = log10 of flux ratio of bright (10 K-inf) to faint (3-5 K) pixels  
  > "we adopt $(T_0, T_1, T_2, T_3) = (3, 5, 10, \infty)$ \[K\]" (6.1); "The data are smoothed to a $2\;{\rm km\,s^{-1}}$ velocity resolution to achieve better sensitivity." (6.1)
   - fitting: _not stated_
   - validation: Compared to MW BDFs smoothed to 0.7 pc  
  > "the spatial scales are smoothed to match the 0.7 pc resolution of this LMC study" (6.1)

## Software

- **CASA** : Calibration, statwt, TP2VIS platform  
  > "were calibrated using the Common Astronomy Software Applications (cite: mcmullin2007)." (4 Data Reduction)
- **Miriad** : Imaging/deconvolution (mossdi2)  
  > "we used the Multichannel Image Reconstruction, Image Analysis, and Display (Miriad) software package (cite: sault1995), instead of CASA." (4 Data Reduction)
- **TP2VIS** : Convert TP map to visibilities  
  > "We converted the TP map into visibilities by using the Total Power to Visibilities (TP2VIS) package" (4 Data Reduction)
- **Astropy** : Acknowledged as used in the research  
  > "This research made use of Astropy, a community-developed core Python package for Astronomy" (Acknowledgments)
- **Montage** : Acknowledged as used in the research  
  > "This research made use of Montage." (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| BDI GMC 55 | -0.92 | not stated | dimensionless | 4 | / 55     / $5^{\rm h} 07^{\rm m} 45^{\rm s}$ / $-68\ensuremath{^\circ} 59\ensuremath{'} 30\ensuremath{''}$ / 0.54      / 1.4                            / 0.3                / $-0.92$   / |
| BDI GMC 197 | -1.50 | not stated | dimensionless | 4 | / 197    / $5^{\rm h} 39^{\rm m} 50^{\rm s}$ / $-70\ensuremath{^\circ} 07\ensuremath{'} 00\ensuremath{''}$ / 0.57      / 4.7                            / 0.05               / $-1.50$   / |
| BDI GMC 216 | -0.83 | not stated | dimensionless | 4 | / 216    / $5^{\rm h} 44^{\rm m} 35^{\rm s}$ / $-69\ensuremath{^\circ} 26\ensuremath{'} 00\ensuremath{''}$ / 0.47      / 4.9                            / 0.2                / $-0.83$   / |
| BDI GMC 225 | -1.55 | not stated | dimensionless | 4 | / 225    / $5^{\rm h} 47^{\rm m} 20^{\rm s}$ / $-70\ensuremath{^\circ} 41\ensuremath{'} 30\ensuremath{''}$ / 0.67      / 1.1                            / 0.1                / $-1.55$   / |
| BDI GMC 2 | -infinity (no gas >10 K) | not stated | dimensionless | 4 | Its BDI is very low ($-\infty$; meaning no gas with high brightness $>10$ K). |
| CO masses within ALMA fields | 1.1 to 4.9 x 10^5 | not stated | Msun | 3 | The masses within the ALMA fields range between 1.1 and $4.9 \times 10^5 M_\ensuremath{\odot}$; 5–30% of the total GMC masses in the NANTEN catalog. |

## Qualitative findings

- Four star-forming GMCs show clumps and filaments; the quiescent GMC 2 is diffuse and featureless, similar to MW inter-arm gas.  
  > "The quiescent GMC shows a relatively diffuse, extended emission distribution without prominent clumps or filaments." (abstract)

## Claim tuples

- H: Quiescent LMC GMCs are less structured than star-forming GMCs | E: ALMA 12m+7m+TP CO(1-0) imaging at 0.7 pc and BDF/BDI analysis of five GMCs | R: GMC 2 has BDI -inf; other four have BDI -1.55 to -0.83 | F: Structure correlates with star-formation activity, analogous to MW arm/inter-arm | **supported**
- H: GMCs follow an evolutionary sequence from unstructured to structured | E: Combine five GMCs with literature ALMA studies | R: Qualitatively similar trend in other ALMA clouds | F: Tentative evolutionary trend | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Miriad used because CASA clean uses one dirty beam for a whole mosaic, causing flux divergence and stripes  
  > "The `clean` and `tclean` tasks in CASA (as of version 5.3) use only one dirty beam for a whole mosaic in their minor cycles, while it varies across the mosaic." (4 Data Reduction)
- Alternative: CASA clean/tclean rejected for imaging  
  > "Therefore, we could not use CASA for imaging." (4 Data Reduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Sample small and classification uncertain; FoVs not centered on 45 arcsec peaks; trend tentative  
  > "Therefore, our ALMA FoVs are not optimal in terms of the peak positions in the $45\ensuremath{''}$ resolution maps." (2.1 Considerations)
- Caveat (inferred, ours): No uncertainties on BDI or masses
- Caveat (inferred, ours): Five clouds only; no statistical test
- Caveat (inferred, ours): BDI depends on noise and thresholds, with pixel-based X_CO assumption
- Caveat (inferred, ours): Environmental factors (SGS) confound the trend

## Reproducibility

- Data public (paper): ALMA project data acknowledged via ADS/JAO.ALMA#2012.1.00641.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00641.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Clean masks and image parameters
- Missing: TP2VIS settings
- Missing: BDI pixel selection details
- Data volume (inferred): ~50-150 GB raw for five 27-pointing mosaics across 12m/7m/TP
- Score (inferred): 3/5, Data public and software named, but several imaging parameters and BDI details unstated and no code released.
- Rediscovery candidate: no, Combination imaging with Miriad/TP2VIS is complex and key parameters missing, though BDI results are numeric.

## Links

- Method: Koda et al. 2011 (cite: koda2011) (TP2VIS combination procedure)
- Method: Sawada et al. 2012 (cite: sawada2012) (BDF/BDI definition)
- Companion: Wong et al. 2017 (cite: wong2017) (ALMA study of a quiescent LMC cloud)
- Related: NANTEN LMC survey
- Related: MAGMA Mopra survey
- Related: Spitzer SAGE

## Checks

```json
{
 "quotes": 65,
 "quotes_ok": 65,
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
  "facts": 86,
  "stated": 50,
  "rate": 0.581
 },
 "evidence_ok": true
}
```

# ALMA deep field in SSA22: Survey design and source catalog of a 20 arcmin<SUP>2</SUP> survey at 1.1 mm

`2018PASJ...70...65U` | Publications of the Astronomical Society of Japan 2018 | first author: Umehata, Hideki | arXiv: 1804.08842 | DOI: 10.1093/pasj/psy065

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, galaxy_clusters_and_sz
- Question: Does the z=3.09 SSA22 proto-cluster show enhanced dust-obscured star formation, as seen in 1.1 mm source number counts over a 20 arcmin^2 ALMA map, relative to blank fields?  
  > "The cumulative number counts show a factor 3–5$\times$ excess compared to blank fields." (abstract)
- Target **SSA22 proto-cluster field (ADF22B)**: coordinates Tiles a/b/c centred at 22h17m27.4s, 22h17m22.0s, 22h17m16.7s, +00d17m00s  
  > "The central coordinates of the three tiles are ($\alpha$,$\delta$) = (22$^{\rm h}$17$^{\rm m}$27.4$^{\rm s}$, $+00^\circ17^\prime00^{\prime\prime}$)" (3 Observations); "SSA22 contains a remarkable proto-cluster at $z=3.09$" (abstract); z/distance z=3.09 (proto-cluster)  
  > "The central coordinates of the three tiles are ($\alpha$,$\delta$) = (22$^{\rm h}$17$^{\rm m}$27.4$^{\rm s}$, $+00^\circ17^\prime00^{\prime\prime}$)" (3 Observations); "SSA22 contains a remarkable proto-cluster at $z=3.09$" (abstract); distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00580.S, 2013.1.00162.S
- bands: Band 6 (1.1 mm), central 263 GHz (1.14 mm)  
  > "at 1.1 mm (band 6)" (Summary); "The central observing frequency of 263 GHz (1.14 mm)" (2.2 Observations)
- frequencies and spectral setup: TDM mode; four SPWs at 254.0, 256.0, 270.0, 272.0 GHz; 1.875 GHz each, 15.6 MHz channels  
  > "The central frequencies of the four spectral windows were 254.0, 256.0, 270.0 and 272.0 GHz, respectively." (2.2 Observations)
- continuum bandwidth: _not stated_
- arrays: 42–43 12m antennas  
  > "with 42–43 available 12m antennas in the C40-5 configuration" (2.2 Observations)
- configurations: C40-5  
  > "with 42–43 available 12m antennas in the C40-5 configuration" (2.2 Observations)
- baselines: maximum baseline 2.6 km  
  > "the maximum baseline, 2.6 km, was much longer than we originally requested" (2.2 Observations)
- angular resolution: 0.26x0.20 arcsec untapered; 0.53x0.52 arcsec tapered  
  > "The resulting synthesized beam size is $0.53^{\prime\prime}\times0.52^{\prime\prime}$ (P.A. $-54$ deg)." (2.3 Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: 1 sigma 73 uJy/beam typical  
  > "The typical 1$\sigma$ depth measured over a large central area of the map is 73 $\mu$Jy beam$^{-1}$." (2.3 Data Reduction)
- time on source: 399 min on source; 11.3 h total; 1 min per pointing  
  > "The exposure time per pointing was 1 min so that the total amount of on-source time was 399 min." (2.2 Observations)
- observing dates: 2017 July 8–12  
  > "Each observation was executed on 2017 July 8–12" (2.2 Observations)
- pi or archival as stated: Cycle 4 PI Umehata (new); ADF22A from Cycle 2 earlier observations, combined  
  > "Through our new ALMA Cycle 4 project (# 2016.1.00580.S, PI. Umehata)" (2.1 Survey Design)
- Line: 12CO J=9-8 (coverage at z~3.09) (1036.912 GHz)
- Other facility **AzTEC/ASTE**: 1.1 mm single-dish map compared with ALMA  
  > "we compare the ALMA view from ADF22 with that of the AzTEC/ASTE map" (4.3)
- Other facility **Keck/MOSFIRE**: K-band spectroscopic redshifts for ADF22B sources  
  > "our recent $K$-band spectroscopy taken with Keck/MOSFIRE (H. Umehata et al. in preparation)" (3.3)
- External data: ADF22A source catalog and number counts  
  > "ADF22A source counts are from (cite: 2017ApJ...835...98U)." (4.1) [from (cite: 2017ApJ...835...98U)]
- External data: Blank-field counts used for double power-law fit  
  > "we focus the counts from (cite: 2016ApJ...833...68A), (cite: 2016ApJ...822...36O), and (cite: 2016PASJ...68...36H)" (4.1) [from (cite: 2016ApJ...833...68A); (cite: 2016ApJ...822...36O); (cite: 2016PASJ...68...36H); (cite: 2015ApJ...807..128S); (cite: 2013MNRAS.432....2K)]
- External data: SED template set for flux to LIR conversion  
  > "using a template set of spectral energy distribution (SED) for ALMA-identified SMGs ((cite: 2017ApJ...840...78D))" (3.3) [from (cite: 2017ApJ...840...78D)]
- External data: DRG selection catalog  
  > "DRGs ($J-K>1.4$ and $K<24$; (cite: 2013ApJ...778..170K))" (4.3) [from (cite: 2013ApJ...778..170K)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline in CASA  
  > "The calibration process was carried out using the casa version of the ALMA pipeline (Pipeline-Cycle4-R2-B) for each tile." (2.3 Data Reduction)
- casa version: CASA 5.1.1 (imaging)  
  > "using the task tclean with the casa version 5.1.1" (2.3 Data Reduction)
- pipeline version: Pipeline-Cycle4-R2-B  
  > "The calibration process was carried out using the casa version of the ALMA pipeline (Pipeline-Cycle4-R2-B) for each tile." (2.3 Data Reduction)
- archive products used as is: _not stated_
- flux calibrator: J2226+0052 (flux scale); bandpass J2148+0657  
  > "The absolute flux density scale was set using the quasar, J2226+0052. The bandpass calibration was performed using J2148+0657." (2.2 Observations)
- flux scale uncertainty: within 10%, not included in analyses  
  > "The absolute flux density accuracy is evaluated to be within 10%." (2.2 Observations)
- self calibration: _not stated_

### Imaging

- task: tclean, mosaic gridder  
  > "by setting the gridder mode to “mosaic” and the deconvolver to “hogbom”" (2.3 Data Reduction)
- deconvolver: hogbom  
  > "by setting the gridder mode to “mosaic” and the deconvolver to “hogbom”" (2.3 Data Reduction)
- weighting robust: natural weighting  
  > "create a single “dirty” map with natural weighting" (2.3 Data Reduction)
- uv taper: uvtaper = 0.5 arcsec  
  > "we adopted the taper parameter, “uvtaper = 0.5 arcsec”" (2.3 Data Reduction)
- cell size: 0.1 arcsec pixels  
  > "since each pixel is $0.1^{\prime\prime}\times0.1^{\prime\prime}$ in size" (3.1)
- image size: _not stated_
- masking: clean to 3 sigma with tight clean box around each 5 sigma source  
  > "we repeated the clean process down to 3$\sigma$, putting a tight clean box around each 5$\sigma$ source" (2.3 Data Reduction)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: region with attenuation <30% is 13 arcmin^2  
  > "The survey area where attenuation of the primary beam is less than 30% is 13 arcmin$^2$." (2.3 Data Reduction)
- array combination: _not stated_
- smoothing: time averaging to 10.296 s; ADF22B map smoothed to 1 arcsec for stacking  
  > "the data were averaged in time with a sampling of 10.296 s" (2.3 Data Reduction)
- final beam: 0.53"x0.52" (PA -54 deg)  
  > "The resulting synthesized beam size is $0.53^{\prime\prime}\times0.52^{\prime\prime}$ (P.A. $-54$ deg)." (2.3 Data Reduction)
- final rms: 73 uJy/beam  
  > "The typical 1$\sigma$ depth measured over a large central area of the map is 73 $\mu$Jy beam$^{-1}$." (2.3 Data Reduction)

### Inherited from earlier work

- Source extraction with aegean as in previous survey  
  > "aegean v2.0b191 ((cite: 2012MNRAS.422.1812H)) as was the case with our previous survey ((cite: 2017ApJ...835...98U))" (3.1) [from (cite: 2017ApJ...835...98U)]
- Completeness and flux boosting simulation recipe  
  > "following the recipe described in (cite: 2016PASJ...68...36H) and B. Hatsukade et al. (2018, in preparation)" (3.2) [from (cite: 2016PASJ...68...36H); B. Hatsukade et al. 2018 in prep]
- Number counts calculation recipe and flux bins  
  > "We calculated the cumulative number counts and errors with a recipe presented in (cite: 2016PASJ...68...36H) and B. Hatsukade et al., in preparation." (4.1) [from (cite: 2016PASJ...68...36H)]

### Not stated but needed to reproduce (our reading)

- CASA tclean parameters: image size, mosaic phase centre, niter, exact clean threshold and mask
- Whether ADF22A and ADF22B were combined in uv or only catalog level
- Aegean detection and fitting parameters beyond S/N=4 (seed/flood thresholds)
- Flux bins and the exact bootstrap procedure for counts
- Details of the AzTEC deboosting and source list
- Archive-calibration scripts for ADF22A Cycle 2 data
- Stacking aperture and positions (Ks catalog) and exact imfit settings

## Analysis recipe

1. **Calibrate and image the mosaic**: ALMA pipeline calibration per tile; combine uv data; tclean with natural weighting, mosaic gridder, hogbom, uvtaper 0.5 arcsec  
  > "The $u v$ data for each pointing for all the three tiles was first combined into a single $u v$ dataset." (2.3 Data Reduction)
   - software: CASA, tclean
   - parameter: uvtaper = 0.5 arcsec  
  > "we adopted the taper parameter, “uvtaper = 0.5 arcsec”" (2.3 Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract sources**: bane sensitivity map with 3 sigma clipping in 100x100 pixel boxes; aegean peaks above S/N=4; negative peaks used to set 5 sigma threshold  
  > "Using aegean, we extracted both positive and negative peaks above S/N=4." (3.1)
   - software: Aegean, BANE
   - parameter: S/N>5 adopted; 17 sources, 1 negative peak  
  > "Consequently 17 sources are found above S/N=5." (3.1)
   - fitting: _not stated_
   - validation: Compared positive and negative peak counts  
  > "Since the number of negative peaks above the equivalent threshold is just one, we adopt these 17 sources as secure detections." (3.1)
3. **Completeness and flux boosting**: Inject mock Gaussian sources (FWHM 0.1-0.5", S/N 3-10), 1000 per S/N bin, re-extract with aegean  
  > "The mock sources are injected into the image map prior to primary beam correction, 1000 times for each SNR bin." (3.2)
   - software: Aegean
   - parameter: recovered if >4 sigma and within 1.0 arcsec  
  > "if it is detected with a certain level of significance ($>4\sigma$) at a position close to the originally injected mock source ($<1.0^{\prime\prime}$)" (3.2)
   - fitting: _not stated_
   - validation: _not stated_
4. **Measure flux and size**: 2D Gaussian fits with imfit on primary-beam-corrected map; sizes from non-tapered map; bootstrap 95% CI for median  
  > "we performed two-dimensional Gaussian fitting using the imfit task of casa on the map that was applied for the correction of the primary beam response" (3.3)
   - software: CASA imfit
   - assumption: IR luminosity from Danielson et al. SMG SED templates at z=3.09; Chabrier IMF; cosmology Om=0.3, OL=0.7, H0=70  
  > "(or SFR$_{\rm IR}=80_{-40}^{+30}$ – $1040_{-460}^{+340}$ $M_\odot$ yr$^{-1}$ for a Chabrier IMF" (3.3)
   - fitting: _not stated_
   - validation: _not stated_
5. **Cumulative number counts and blank-field comparison**: Counts corrected for completeness and boosting, bootstrap errors, combined with ADF22A weighted by area; compared with double power-law fit to blank-field counts  
  > "The effect of the completeness and flux boosting is corrected on the basis of our simulation" (4.1)
   - assumption: Fluxes scaled to 1.1 mm with modified blackbody, beta=1.5, T=35 K, z=2.5  
  > "assuming a modified black body with spectral index ($\beta$) 1.5, dust temperature 35 K, and $z=2.5$, if needed" (4.1)
   - fitting: Double power law N(>S)=N'/S'[(S/S')^alpha+(S/S')^beta]^-1 fitted to blank-field counts  
  > "these counts are fitted to a double-power law function of the form" (4.1)
   - validation: _not stated_
6. **Compare to AzTEC and stack DRGs**: Compare ALMA flux sums within AzTEC beam to deboosted AzTEC flux; stack 67 undetected DRGs at Ks positions on map smoothed to 1 arcsec, imfit for flux  
  > "We stacked the remaining 67 DRGs at their *Ks*-band positions on the ALMA maps, calculating the average flux density." (4.3)
   - software: CASA imfit
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.1.1 (imaging); pipeline Cycle4-R2-B: calibration, tclean imaging, imfit  
  > "Data reduction was performed using the Common Astronomy Software Application (casa)." (2.3 Data Reduction)
- **Aegean (incl. bane)** v2.0b191: source finding and noise map  
  > "aegean v2.0b191 ((cite: 2012MNRAS.422.1812H))" (3.1)
- **APLpy** : plotting  
  > "This research made use of APLpy, an open-source plotting package for Python" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Typical 1 sigma depth | 73 | not stated | uJy/beam | 1 | The typical 1$\sigma$ depth measured over a large central area of the map is 73 $\mu$Jy beam$^{-1}$. |
| ADF22B sources at S/N>5 | 17 | not stated | sources | 2 | Consequently 17 sources are found above S/N=5. |
| Total ADF22 sources | 35 | not stated | sources | 2 | making a total of 35 ALMA sources in ADF22 |
| Completeness at S/N=5 | ~55 | not stated | percent | 3 | At SNR=5, which is the detection threshold, the completeness is estimated to be $\sim$55%. |
| Flux boosting at S/N~5 | ~20 | not stated | percent | 3 | Sources with SNR$\sim$5 may suffer from $\approx$20% artificial increase of flux density |
| Median deconvolved major axis | 0.27 | +0.05/-0.12 (95% bootstrap) | arcsec | 4 | The median deconvolved major axis is $0.27_{-0.12}^{+0.05}$ arcsec |
| Blank-field double power-law fit | N'=220, S'=4.8 mJy, alpha=10.1, beta=1.7 | ±40, ±0.2, ±1.7, ±0.1 | deg^-2, mJy, dimensionless | 5 | $N'=220\pm40$ deg$^{-2}$, $S'=4.8\pm0.2$ mJy, $\alpha=10.1\pm1.7$, and $\beta=1.7\pm0.1$ |
| Median S_ALMA/S_AzTEC | 0.70 | +0.11/-0.10 | dimensionless | 6 | The median, $S^{\rm ALMA}/S^{\rm AzTEC} =0.70_{-0.10}^{+0.11}$, is well below unity. |
| Stacked DRG flux density | 0.13 | 0.02 | mJy | 6 | $S_{\rm 1.1mm}=0.13\pm0.02$ mJy, on average |

## Qualitative findings

- None of the ADF22B SMGs have a secure X-ray counterpart, unlike ADF22A.  
  > "none of ADF22B SMGs have a secure X-ray counterpart" (4.2)

## Claim tuples

- H: Proto-cluster has elevated dust-obscured star formation relative to blank fields | E: Cumulative 1.1 mm counts over 20 arcmin^2 compared with blank-field fit | R: Factor 3–5 excess at 0.4–2.5 mJy | F: Over-abundance of dusty galaxies on ~10 comoving Mpc scale | **supported**
- H: ALMA resolves single-dish AzTEC sources into multiple SMGs | E: Compared ALMA SMGs with AzTEC sources | R: 5 of 8 AzTEC sources show multiplicity; summed ALMA flux ratio 0.70 | F: Multiplicity is significant and additional faint components contribute | **supported**
- H: Undetected DRGs account for missing AzTEC flux | E: Stacked 67 DRGs | R: 0.13±0.02 mJy average | F: Can account for part (~30%) of missing flux | **partially**

## Reasoning

- Why this data: Frequency matched to earlier AzTEC survey and same setup as ADF22A for combination  
  > "We note that the frequency set-ups are exactly the same as those in ADF22A, which allows us to combine the two datasets relatively easily." (2.2 Observations)
- Why this method: _not stated_
- Alternative: Candidates at S/N 4.5–5 not used because negative detections are equal or more numerous  
  > "There is an equivalent or larger number of negative detections in this SNR range and therefore we do not use them in following discussion." (3.1)
- How they decided it was enough: _not stated_
- Limitation (authors): SMG redshifts mostly unknown; association with proto-cluster unconfirmed  
  > "Although the accurate redshift of ADF22 SMGs are mostly unknown, two of them have $z_{\rm spec}=3.09$" (4.1)
- Limitation (authors): Angular resolution not uniform; map insensitive to faint extended emission  
  > "We note that our intrinsic angular resolutions are not exactly uniform across ADF22" (2.3 Data Reduction)
- Caveat (inferred, ours): Proto-cluster membership of most SMGs is assumed, not measured
- Caveat (inferred, ours): Blank-field comparison depends on heterogeneous literature counts and flux scaling assumptions
- Caveat (inferred, ours): Number-count errors from small samples; cosmic variance not assessed
- Caveat (inferred, ours): Tapering choice affects point-source sensitivity and ADF22A/B homogeneity

## Reproducibility

- Data public (paper): Project codes listed in acknowledgements; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00162.S, ADS/JAO.ALMA#2016.1.00580.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Full tclean parameters (imsize, niter, threshold)
- Missing: Counts flux bins and ADF22A-linked processing
- Missing: Hatsukade et al. in-preparation recipe
- Missing: Keck redshifts in preparation
- Missing: AzTEC catalog details
- Data volume (inferred): ~100–300 GB raw for the 2016.1.00580.S nine EBs plus Cycle 2 data
- Score (inferred): 3/5, Main imaging and extraction recipe given, but several parameters and companion recipes missing; counts rely on literature.
- Rediscovery candidate: yes, Data are archival ALMA projects and key results (source count, S/N, flux) are numeric, though some imaging parameters are missing.

## Links

- Method: (cite: 2016PASJ...68...36H) (Completeness, flux boosting and number-count recipe)
- Method: (cite: 2012MNRAS.422.1812H) (Aegean source finder)
- Companion: (cite: 2017ApJ...835...98U) (ADF22A survey and catalog)
- Companion: (cite: 2015ApJ...815L...8U) (First ADF22 ALMA survey of the proto-cluster)
- Related: ADF22A (2013.1.00162.S)
- Related: AzTEC/ASTE SSA22 survey
- Related: ALESS
- Related: ALMACAL

## Checks

```json
{
 "quotes": 78,
 "quotes_ok": 78,
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
  "facts": 82,
  "stated": 59,
  "rate": 0.72
 },
 "evidence_ok": true
}
```

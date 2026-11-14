# ALMA Deep Field in SSA22: Source Catalog and Number Counts

`2017ApJ...835...98U` | The Astrophysical Journal 2017 | first author: Umehata, Hideki | arXiv: 1611.09857 | DOI: 10.3847/1538-4357/835/1/98

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, star_formation
- Question: What 1.1 mm sources and number counts does a deep contiguous ALMA mosaic reveal in the core of the z=3.09 SSA22 protocluster, and how do they relate to AzTEC sources and the protocluster?  
  > "Here we present the full catalog of the ALMA SMGs and the comprehensive results in terms of mm properties unveiled by ALMA." (1 Introduction)
- Target **ADF22 (SSA22 protocluster core)**: coordinates RA 22h17m34.0s, Dec +00d17m00s (J2000)  
  > "centered at $\alpha = 22^{\rm h}17^{\rm m}34^{s}.0$, $\delta = + 00^\circ 17^\prime 00^{\prime\prime}$ (J2000) at 1.1 mm" (2.1 Field Selection); z/distance z=3.09  
  > "centered at $\alpha = 22^{\rm h}17^{\rm m}34^{s}.0$, $\delta = + 00^\circ 17^\prime 00^{\prime\prime}$ (J2000) at 1.1 mm" (2.1 Field Selection); distance from spectroscopic redshifts of protocluster members from the literature  
  > "centered at $\alpha = 22^{\rm h}17^{\rm m}34^{s}.0$, $\delta = + 00^\circ 17^\prime 00^{\prime\prime}$ (J2000) at 1.1 mm" (2.1 Field Selection)

## Data provenance

- ALMA projects: 2013.1.00162.S
- bands: Band 6, 1.1 mm  
  > "using ALMA Band 6 in cycle 2" (2.1 Field Selection)
- frequencies and spectral setup: central 263 GHz; TDM; four 1.875 GHz spws at 254.0, 256.0, 270.0, 272.0 GHz; 15.6 MHz channels  
  > "The central frequencies of the four spectral windows are 254.0, 256.0, 270.0, and 272.0 GHz." (2.2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C34-4 (2014), C32-2 (2015)  
  > "in the C34-4 configuration (longest baseline 650 m)" (2.2 Observations)
- baselines: _not stated_
- angular resolution: 1.16x1.02 arcsec (FULL/LORES, tapered); 0.70x0.59 arcsec (DEEP/HIRES)  
  > "The second map has a synthesized beam of $0.^{\prime\prime}70\times0.^{\prime\prime}59$" (2.3 Data Reduction and Imaging)
- max recoverable scale: _not stated_
- sensitivity: median 1sigma 75 uJy/beam (FULL/LORES), 60 uJy/beam (DEEP/HIRES)  
  > "with a median value of 75 $\mu$Jy beam$^{-1}$" (2.3 Data Reduction and Imaging)
- time on source: total 386 min on source  
  > "a total on-source time of 386 min" (2.2 Observations)
- observing dates: 2014 June 6-10 and 2015 April 4, 5, 13  
  > "The first run was conducted on 2014 June 6–10" (2.2 Observations)
- pi or archival as stated: PI H. Umehata, cycle 2  
  > "Program ID. 2013.1.00162.S, PI. H. Umehata" (2.1 Field Selection)
- Line: 12CO 9-8 (1036.912 GHz)
- Other facility **AzTEC/ASTE**: 1.1 mm single-dish map and source list for comparison  
  > "The AzTEC/ASTE survey of SSA22 by (cite: 2009Natur.459...61T) and (cite: 2014MNRAS.440.3462U) presented a 1.1 mm image of ADF22." (4.1.1)
- External data: AzTEC source IDs and flux densities  
  > "Flux density of AzTEC source ((cite: 2014MNRAS.440.3462U))" (Table 2) [from (cite: 2014MNRAS.440.3462U)]
- External data: Spectroscopic redshifts for some SMGs  
  > "d; $^{12}$CO(3-2) ((cite: 2013MNRAS.429.3047B), see also (cite: 2005MNRAS.359.1165G), (cite: 2005ApJ...622..772C))" (Table 2) [from (cite: 2013MNRAS.429.3047B)]
- External data: SMA 860um flux density of ADF22.1 (12.2+-2.3 mJy)  
  > "Tamura et al. reported the 860$\mu$m flux density of ADF22.1, $S_{\rm 860\mu m}=12.2\pm2.3$ mJy" (4.1.1) [from (cite: 2010ApJ...724.1270T)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline  
  > "The calibration and imaging was performed using casa version 4.2.2 of the ALMA pipeline and casa version 4.5.0, respectively." (2.3 Data Reduction and Imaging)
- casa version: CASA 4.2.2 (calibration), 4.5.0 (imaging)  
  > "casa version 4.2.2 of the ALMA pipeline and casa version 4.5.0, respectively" (2.3 Data Reduction and Imaging)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J2148+0657 (2014); Uranus and Neptune (2015)  
  > "The absolute flux scale was set using J2148+0657 (for the 2014 run) and Uranus and Neptune (for the 2015 run)." (2.2 Observations)
- flux scale uncertainty: within 20%, not included in analyses  
  > "We estimate that the absolute flux accuracy is within 20%." (2.2 Observations)
- self calibration: _not stated_

### Imaging

- task: CASA clean, imager mode mosaic, natural weighting  
  > "create a single “dirty” map with natural weighting, by setting the imager mode to “mosaic”" (2.3 Data Reduction and Imaging)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: outertaper = 120 klambda for FULL/LORES; none for DEEP/HIRES  
  > "adopting the taper parameter, outertaper = 120 k$\lambda$" (2.3 Data Reduction and Imaging)
- cell size: _not stated_
- image size: _not stated_
- masking: clean to 1.5 sigma with 1"x1" boxes around each 5 sigma source  
  > "we repeated the clean process down to 1.5$\sigma$, putting a tight clean box ($1^{\prime\prime}\times1^{\prime\prime}$ in size) around each 5$\sigma$ source" (2.3 Data Reduction and Imaging)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: effective area where primary beam coverage >50%: 7.0 arcmin2 (FULL/LORES), 5.8 (DEEP/HIRES)  
  > "the area in the map within which the primary beam coverage is greater than 50%" (2.3 Data Reduction and Imaging)
- array combination: uv data of all pointings/SBs combined into a single uv dataset  
  > "The $u v$-data for individual pointings were first combined into a single $u v$–data set." (2.3 Data Reduction and Imaging)
- smoothing: _not stated_
- final beam: 1.16"x1.02" PA -80 (FULL/LORES); 0.70"x0.59" PA -80 (DEEP/HIRES)  
  > "The resulting synthesized beam is $1.^{\prime\prime}16\times1.^{\prime\prime}02$ in size (P.A. $= -80$ deg)." (2.3 Data Reduction and Imaging)
- final rms: 1sigma 52-170 uJy/beam, median 75 (FULL/LORES); 50-129, median 60 (DEEP/HIRES)  
  > "range of 1$\sigma$ depth of 52 – 170 $\mu$Jy beam$^{-1}$ with a median value of 75 $\mu$Jy beam$^{-1}$" (2.3 Data Reduction and Imaging)

### Inherited from earlier work

- Clean-box procedure  
  > "in a manner similar to that reported by (cite: 2013ApJ...768...91H)" (2.3 Data Reduction and Imaging) [from (cite: 2013ApJ...768...91H)]
- Completeness/boosting simulation method  
  > "We briefly describe the method below (for more detail, see (cite: 2016PASJ...68...36H))." (3.2 Completeness and Flux boosting) [from (cite: 2016PASJ...68...36H)]
- Number counts and errors computed the same way  
  > "We calculated the number counts and associated errors in the same way as (cite: 2016PASJ...68...36H)." (4.3 Number Counts) [from (cite: 2016PASJ...68...36H)]
- L_IR from SED templates  
  > "We estimated $L_{\rm IR}$ \[8-1000 $\mu$m\] using SED templates of well-studied starburst galaxies" (4.2) [from (cite: 2015ApJ...815L...8U)]
- Sigma_SFR uses SFR halved  
  > "the SFR divided by a factor of two, following (cite: 2015ApJ...799...81S)" (4.2) [from (cite: 2015ApJ...799...81S)]

### Not stated but needed to reproduce (our reading)

- aegean detection parameters beyond the 3.5 sigma threshold
- exact clean parameters (niter, cell, image size, mosaic gridder)
- which SEDs templates and exact weights for L_IR
- injected model source count per trial and details of the model profile
- Poisson/completeness correction procedure details for number counts
- line-free channels used for continuum

## Analysis recipe

1. **Image the mosaic**: Combine uv data, clean with mosaic mode; tapered FULL/LORES map (fields 1-103) and untapered DEEP/HIRES map (fields 1-80)  
  > "we first created a 1$^{\prime\prime}$-tapered map for the entire field (i.e., fields 1–103)" (2.3 Data Reduction and Imaging)
   - software: CASA
   - parameter: outertaper = 120 klambda; clean to 1.5 sigma  
  > "adopting the taper parameter, outertaper = 120 k$\lambda$" (2.3 Data Reduction and Imaging)
   - fitting: _not stated_
   - validation: _not stated_
2. **Make sensitivity map**: rms per 0.1" pixel from surrounding 100x100 pixels on map before primary beam correction  
  > "calculating the rms for each $0.^{\prime\prime}1\times0.^{\prime\prime}1$ pixel using the surrounding $100\times100$ pixels" (2.3 Data Reduction and Imaging)
   - software: AIPS rmsd
   - fitting: _not stated_
   - validation: _not stated_
3. **Extract sources**: Find positive sources above 3.5 sigma with aegean; negative sources counted to estimate spurious fraction; adopt >5 sigma  
  > "was used to extract positive sources above 3.5$\sigma$." (3.1 Source Extraction and Characterization)
   - software: aegean
   - parameter: 5 sigma detection limit; 17 FULL/LORES + 1 DEEP/HIRES-only source  
  > "Therefore in total 18 sources were detected at SNR$>5$." (3.1 Source Extraction and Characterization)
   - fitting: _not stated_
   - validation: No negative sources above 5 sigma; Gaussian statistics give <1 spurious peak  
  > "There were no negative sources above 5$\sigma$, while we found seven negative ones with 4–4.6$\sigma$." (3.1 Source Extraction and Characterization)
4. **Measure flux densities**: imfit Gaussian fits on primary-beam-corrected map; integrated flux adopted unless lower than peak  
  > "The flux densities of the detected sources were measured with the imfit task of casa, using the map after correction for the primary beam attenuation." (3.1 Source Extraction and Characterization)
   - software: CASA imfit
   - fitting: 2D Gaussian fit  
  > "Two-dimensional Gaussian fits to the ALMA SMGs in the image plane using the DEEP/HIRES map suggest that ADF22 sources are generally resolved." (Size measurement and star formation rate surface density)
   - validation: FULL/LORES vs DEEP/HIRES flux ratio 0.96  
  > "$S^{\rm FULL}/S^{\rm DEEP}=0.96^{+0.00}_{-0.02}$" (3.1 Source Extraction and Characterization)
5. **Completeness and flux boosting**: Inject model sources (scaled synthesized beam) at 0.02-0.6 mJy, re-extract, 1000 repeats per bin; recovery within 1" at >=4 sigma  
  > "the procedures are repeated 1000 times for each flux density bin ($\Delta S=$0.02 mJy)" (3.2 Completeness and Flux boosting)
   - fitting: _not stated_
   - validation: Boosting negligible for >5 sigma  
  > "The results show that the effect is negligible if we consider only those sources detected at $>5\sigma$." (3.2 Completeness and Flux boosting)
6. **Compare with AzTEC**: Sum ALMA >=5 sigma fluxes within 30" AzTEC beam vs deboosted AzTEC flux; also convolve ALMA map with 30" Gaussian  
  > "we calculate the sum of the flux densities of the SMGs with $\ge5\sigma$ within the FWHM of the AzTEC beam" (4.1.1)
   - fitting: _not stated_
   - validation: _not stated_
7. **Measure sizes and SFR surface density**: 2D Gaussian fits on DEEP/HIRES map for SNR>10 sources; L_IR from SED templates; SFR via Kennicutt calibration (Kroupa IMF); Sigma_SFR with SFR/2  
  > "Two-dimensional Gaussian fits to the ALMA SMGs in the image plane using the DEEP/HIRES map suggest that ADF22 sources are generally resolved." (4.2)
   - software: CASA imfit
   - assumption: z=3.0 for ADF22.2 and ADF22.5 lacking zspec  
  > "we assume $z=3.0$ (a median value for AzTEC sources; (cite: 2012ApJS..200...10S))" (4.2)
   - fitting: _not stated_
   - validation: Compared with literature SMG sizes  
  > "The size distribution in ADF22 is generally consistent with previous measurements for SMGs in other fields" (4.2)
8. **Number counts**: Differential and cumulative counts of 17 SMGs >5 sigma (FULL/LORES), completeness-corrected, and for 7 non-z=3.09 SMGs; cumulative field counts fit to a double power law with literature counts  
  > "we utilized only the 17 SMGs detected with SNR $> 5\sigma$ in the FULL/LORES map." (4.3 Number Counts)
   - assumption: Literature counts scaled to 1.1 mm with modified blackbody beta=1.5, T=35 K, z=2.5  
  > "spectral index of $\beta$ = 1.5, dust temperature of 35 K" (4.3 Number Counts)
   - fitting: double power law N(>S)=N'/S'[(S/S')^alpha+(S/S')^beta]^-1; fitting algorithm not stated  
  > "are fitted to a double-power law function of the form, $N(>S)=N'/S' [(S/S')^\alpha+(S/S')^\beta]^{-1}$, which yields the best-fit parameters" (Number Counts)
   - validation: Poisson errors (Gehrels 1986); compared with other ALMA counts  
  > "The errors are 1$\sigma$ Poisson errors ((cite: 1986ApJ...303..336G))." (Table 4)

## Software

- **CASA** 4.2.2 (pipeline calibration), 4.5.0 (imaging): calibration, imaging, imfit flux/size  
  > "Data reduction was performed using the Common Astronomy Software Application (casa" (2.3 Data Reduction and Imaging)
- **aegean** v1.9.5-56: source extraction  
  > "A source-finding algorithm, aegean v1.9.5-56 ((cite: 2012MNRAS.422.1812H)), was used to extract positive sources above 3.5$\sigma$." (3.1 Source Extraction and Characterization)
- **AIPS** : rmsd task for sensitivity map  
  > "A sensitivity map was constructed utilizing an aips ((cite: 2003ASSL..285..109G)) task, rmsd" (2.3 Data Reduction and Imaging)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of robust ALMA sources (SNR>5) | 18 | not stated | sources | 3 | Therefore in total 18 sources were detected at SNR$>5$. |
| Median size of nine brightest SMGs (FWHM) | 0.32 | +0.13/-0.06 | arcsec | 7 | the median value for the nine SMGs is $0^{\prime\prime}.32^{+0^{\prime\prime}.13}_{-0^{\prime\prime}.06}$ |
| Median physical size | 2.4 | +1.0/-0.4 | kpc | 7 | $2.4^{+1.0}_{-0.4}$ physical kpc at $z=3.09$ |
| Median Sigma_SFR | 50 | not stated | Msun/yr/kpc^2 | 7 | The median value is $\Sigma_{\rm SFR}$=50 $M_\odot$ yr$^{-1}$ kpc$^{-2}$ |
| Flux ratio ALMA/AzTEC for AzTEC1 | 0.64 | 0.05 | dimensionless | 6 | $S^{\rm ALMA}$/$S^{\rm AzTEC}=0.64\pm0.05$ |
| Double power-law fit N' | 200 | 30 | deg^-2 | 8 | $N'=200\pm30$ deg$^{-2}$, $S'=4.9\pm0.2$ mJy, $\alpha=10.4\pm1.6$, and $\beta=1.9\pm0.1$ |
| Completeness at SNR=5 | ~90% | not stated | percent | 5 | The completeness of our source extraction is $\sim70$% at SNR=4 and rises to $\sim90$% at SNR=5. |
| Cumulative counts N(>0.40 mJy), all 17 SMGs | 9.8 | +5.1/-2.2 | 10^3 deg^-2 | 8 | / 0.40            / 17            / $9.8^{+5.1}_{-2.2}$ |

## Qualitative findings

- Three AzTEC sources resolve into eight ALMA SMGs; ten of 18 SMGs lie at z~3.09  
  > "In summary, three AzTEC sources are resolved into eight ALMA SMGs." (4.1.1)
- No SMGs have LAE/LBG counterparts; five of ten K-band selected galaxies detected  
  > "In contrast, five out of ten K-band selected galaxies are securely detected by ALMA." (3.3 Source Catalog)

## Claim tuples

- H: Do single-dish AzTEC sources break into multiple SMGs in the protocluster core? | E: Compare ALMA catalog to AzTEC map | R: Three AzTEC sources correspond to eight ALMA SMGs; AzTEC1 flux ratio 0.64 | F: Multiple physically associated SMGs make up single-dish sources in dense environments | **supported**
- H: Are protocluster SMGs sizes different from field SMGs? | E: Gaussian size fits to nine SNR>10 SMGs | R: Median 0.32 arcsec (2.4 kpc) | F: Consistent with other SMGs; no environmental difference | **supported**
- H: Does the protocluster boost 1.1 mm number counts? | E: Counts with all 17 SMGs vs excluding z=3.09 members | R: Counts ~4-5 times higher at S>1 mJy; field-only counts agree with unbiased ALMA counts | F: Excess due to protocluster members | **supported**

## Reasoning

- Why this data: Band 6 at 263 GHz chosen to match AzTEC 270 GHz and need fewer pointings than Band 7  
  > "allows direct comparison with the flux densities of sources from our AzTEC/ASTE and ALMA surveys" (2.2 Observations)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Absolute flux uncertainty (20%) not included; missing fainter/diffuse emission for AzTEC1; seven sources lack zspec so field counts are conservative  
  > "This uncertainty in the absolute flux calibration is not included in the following analyses and discussions." (2.2 Observations)
- Caveat (inferred, ours): Counts from only 7 arcmin2 in a single overdense field have large cosmic-variance and Poisson uncertainty
- Caveat (inferred, ours): Field counts rely on incomplete redshift information
- Caveat (inferred, ours): Mixed-resolution data combined with tapering may bias flux of extended sources

## Reproducibility

- Data public (paper): Program 2013.1.00162.S cited; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00162.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Detailed clean parameters
- Missing: aegean settings
- Missing: SED template details for L_IR
- Missing: Redshifts from unpublished works (Umehata et al., Hayatsu et al. in prep)
- Data volume (inferred): ~100-300 GB raw for 9 SBs, 103-pointing mosaic
- Score (inferred): 3/5, Data identified and main steps described, but several imaging and extraction parameters and unpublished redshifts are missing.
- Rediscovery candidate: yes, ALMA project code given, recipe largely described, results numeric (source catalog, counts, sizes).

## Links

- Method: (cite: 2016PASJ...68...36H) (Completeness and number counts method)
- Method: (cite: 2012MNRAS.422.1812H) (aegean source finder)
- Companion: (cite: 2015ApJ...815L...8U) (Earlier ADF22 results on nine SMGs and X-ray AGN)
- Companion: Hayatsu et al. (in preparation) (Line search in ADF22)
- Related: AzTEC/ASTE SSA22 survey
- Related: ALESS

## Checks

```json
{
 "quotes": 73,
 "quotes_ok": 73,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 59,
  "rate": 0.686
 },
 "evidence_ok": true
}
```

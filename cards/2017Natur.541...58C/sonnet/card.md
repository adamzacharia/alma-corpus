# A direct localization of a fast radio burst and its host

`2017Natur.541...58C` | Nature 2017 | first author: Chatterjee, S. | arXiv: 1701.01098 | DOI: 10.1038/nature20797

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: transients, other
- Question: Where does the repeating FRB 121102 originate, and what are its host and persistent counterpart? ALMA was used to constrain 230 GHz emission and hence host star formation.  
  > "Here we report the sub-arcsecond localization of FRB 121102, the only known repeating burst source" (abstract)
- Target **FRB 121102**: coordinates RA 05h31m58.70s, Dec +33d08m52.5s (J2000)  
  > "the average J2000 position of the burst source is right ascension $\alpha = 05\ensuremath{^{\mathrm{h}}}31\ensuremath{^{\mathrm{m}}}58.70\ensuremath{^{\mathrm{s}}}$, declination $\delta = +33\ensuremath{^\circ}08\ensuremath{^{\prime}}52.5\ensuremath{^{\prime\prime}}$" (main text); "The maximum redshift, for $\rm DM_{\rm host} = 0$, is $z_{\rm FRB} \lesssim 0.32$, corresponding to a maximum luminosity distance of 1.7 Gpc." (main text); z/distance z <~ 0.32 (upper limit; max luminosity distance 1.7 Gpc)  
  > "the average J2000 position of the burst source is right ascension $\alpha = 05\ensuremath{^{\mathrm{h}}}31\ensuremath{^{\mathrm{m}}}58.70\ensuremath{^{\mathrm{s}}}$, declination $\delta = +33\ensuremath{^\circ}08\ensuremath{^{\prime}}52.5\ensuremath{^{\prime\prime}}$" (main text); "The maximum redshift, for $\rm DM_{\rm host} = 0$, is $z_{\rm FRB} \lesssim 0.32$, corresponding to a maximum luminosity distance of 1.7 Gpc." (main text); distance from Inferred from dispersion measure (NE2001 and IGM contributions)  
  > "the average J2000 position of the burst source is right ascension $\alpha = 05\ensuremath{^{\mathrm{h}}}31\ensuremath{^{\mathrm{m}}}58.70\ensuremath{^{\mathrm{s}}}$, declination $\delta = +33\ensuremath{^\circ}08\ensuremath{^{\prime}}52.5\ensuremath{^{\prime\prime}}$" (main text); "The maximum redshift, for $\rm DM_{\rm host} = 0$, is $z_{\rm FRB} \lesssim 0.32$, corresponding to a maximum luminosity distance of 1.7 Gpc." (main text)

## Data provenance

- ALMA projects: 2015.A.00025.S
- bands: Band 6, 220-240 GHz  
  > "using Band 6 and covering 8 GHz of bandwidth in the range $220-240$ GHz (with 2-MHz channels)" (Methods)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: 38 antennas, C40-6  
  > "We used 38 antennas in the C40-6 configuration, yielding a resolution of 0.32$^{\prime\prime}$$\times$ 0.13$^{\prime\prime}$." (Methods)
- baselines: _not stated_
- angular resolution: 0.32" x 0.13"  
  > "yielding a resolution of 0.32$^{\prime\prime}$$\times$ 0.13$^{\prime\prime}$" (Methods)
- max recoverable scale: _not stated_
- sensitivity: 17 uJy/beam rms  
  > "The image RMS noise level was 17 $\mu$Jy beam$^{-1}$ and did not reveal any significant sources." (Methods)
- time on source: _not stated_
- observing dates: 2016 Sep 15  
  > "The Atacama Large Millimeter and Submillimeter Array (ALMA) observed on 2016 Sep 15" (Methods)
- pi or archival as stated: _not stated_
- Other facility **VLA**: Burst localization, persistent source imaging 1-26 GHz  
  > "We also acquired VLA imaging data covering a contiguous frequency range from 1 to 26 GHz." (Methods)
- Other facility **Arecibo**: Simultaneous burst detections at 1.15-1.73 GHz  
  > "Arecibo observations used the L-wide receiver, which provides a frequency range of $1.15-1.73$ GHz." (Methods)
- Other facility **EVN and VLBA**: Milliarcsecond size limits of the persistent source  
  > "very long baseline radio interferometry yields an angular size less than 1.7 milliarcseconds" (abstract)
- Other facility **Gemini and Keck**: Optical counterpart  
  > "A counterpart to FRB 121102 is detected in archival Keck image at $R_\mathrm{AB}=24.9\pm0.1$ mag" (Methods)
- Other facility **XMM-Newton and Chandra**: X-ray non-detection limits  
  > "we place a 5$\sigma$ limit of $5\times10^{-15}$ erg s$^{-1}$ cm$^{-2}$ at 0.5–10 keV" (Methods)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline in CASA, provided by the observatory  
  > "Calibration and imaging was provided by the ALMA observatory, and done using CASA via the ALMA pipeline." (Methods)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Observatory-provided calibration and imaging  
  > "Calibration and imaging was provided by the ALMA observatory" (Methods)
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
- final beam: 0.32" x 0.13"  
  > "yielding a resolution of 0.32$^{\prime\prime}$$\times$ 0.13$^{\prime\prime}$" (Methods)
- final rms: 17 uJy/beam  
  > "The image RMS noise level was 17 $\mu$Jy beam$^{-1}$" (Methods)

### Not stated but needed to reproduce (our reading)

- ALMA flux and bandpass calibrators
- CASA/pipeline version
- Weighting/robust, cell size, image size, continuum channel selection
- Exact ALMA position used for the upper limit
- Conversion from the 51 uJy limit to the SFR (luminosity scaling details)

## Analysis recipe

1. **Image the ALMA 230 GHz field and set an upper limit**: Pipeline-calibrated and imaged data checked for sources; no significant source found  
  > "The image RMS noise level was 17 $\mu$Jy beam$^{-1}$ and did not reveal any significant sources." (Methods)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Convert flux limit to host star formation rate**: Carilli & Yun relation applied to the 3 sigma limit across z = 0.01 to 0.32  
  > "For our ALMA 3$\sigma$ upper limit of 51 $\mu$Jy and a sub-mm spectral index of 4, we estimate the star formation rate(cite: cy99)" (main text)
   - assumption: sub-mm spectral index of 4  
  > "a sub-mm spectral index of 4" (main text)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : ALMA calibration/imaging via the pipeline; VLA imaging  
  > "done using CASA via the ALMA pipeline" (Methods)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA 230 GHz image rms | 17 | not stated | uJy/beam | 1 | The image RMS noise level was 17 $\mu$Jy beam$^{-1}$ |
| ALMA 3-sigma upper limit | 51 | not stated | uJy | 1 | For our ALMA 3$\sigma$ upper limit of 51 $\mu$Jy |
| Host SFR upper limit | 0.06 to 19 (z = 0.01 to 0.32) | not stated | Msun/yr | 2 | less than 0.06 to 19 M$_\odot$ yr$^{-1}$ for redshifts $z$ ranging from 0.01 to 0.32 |

## Qualitative findings

- ALMA non-detection implies a low host star formation rate.  
  > "The faint optical detection and the non-detection at 230 GHz with ALMA imply a low star formation rate from any host galaxy." (main text)

## Claim tuples

- H: Is the FRB hosted in a prominent star-forming galaxy? | E: ALMA Band 6 imaging at the burst position | R: No source; 3 sigma < 51 uJy gives SFR < 0.06-19 Msun/yr | F: Host has low star formation; a prominent star-forming host is disfavoured | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Caveat (inferred, ours): SFR upper limit depends on the assumed sub-mm spectral index and the DM-derived redshift range

## Reproducibility

- Data public (paper): Data available from public archives under listed project codes  
  > "The observational data presented here are available from public archives under the following project codes." (Data availability)
- Products in archive: _not stated_
- Code: Notebooks for the burst position analysis at github.com/caseyjlaw/FRB121102; realfast, RTPipe, SDMPy  
  > "Computational notebooks for reproducing the burst position analysis are at <http://github.com/caseyjlaw/FRB121102>." (Code availability)
- Missing: ALMA calibrators and CASA version
- Missing: SFR conversion details
- Data volume (inferred): ~10-50 GB for the ALMA part
- Score (inferred): 3/5, ALMA part is a simple pipeline image with a non-detection; details are sparse, but data are public.
- Rediscovery candidate: no, The ALMA result is only a non-detection with sparse processing details; the main results rely on non-ALMA data.

## Links

- Companion: Spitler et al. 2016 (cite: ssh+16a) (Original Arecibo detection and localization of FRB 121102)
- Related: realfast

## Checks

```json
{
 "quotes": 35,
 "quotes_ok": 35,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 58,
  "stated": 25,
  "rate": 0.431
 },
 "evidence_ok": true
}
```

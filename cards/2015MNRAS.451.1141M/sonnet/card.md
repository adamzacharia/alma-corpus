# The ALMA Patchy Deep Survey: a blind search for [C II] emitters at z ∼ 4.5

`2015MNRAS.451.1141M` | Monthly Notices of the Royal Astronomical Society 2015 | first author: Matsuda, Y. | arXiv: 1505.02244 | DOI: 10.1093/mnras/stv1044

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies, cosmology
- Question: Are there blindly detectable [C II] emitters at z~4.5 in ALMA Cycle 0 band 7 archival data, and what limits does this place on the [C II] luminosity function?  
  > "In order to obtain better constraint to the [C II] luminosity function at $z>4$, we carried out a blind search for [C II] emitters at $z\sim 4.5$ using ALMA Cycle 0 archival data." (Introduction)
- Target **243 fields from 8 Cycle 0 projects (NGC1614, SBS0335-052, COSMOS, GRBs, NGC1097, NGC1433, ECDFS, VV114)**: coordinates _not stated_; z/distance [C II] redshift range z=4.28-4.76  
  > "The total number of fields is 243 and the total on-source exposure time is 19.2 hours." (abstract); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00020.S, 2011.0.00039.S, 2011.0.00097.S, 2011.0.00101.S, 2011.0.00108.S, 2011.0.00208.S, 2011.0.00294.S, 2011.0.00467.S
- bands: Band 7, 330-360 GHz  
  > "we searched Cycle 0 Projects covering $330-360$ GHz (in band 7)" (Data and Results)
- frequencies and spectral setup: 7.5 GHz FDM (0.98 MHz) or 8 GHz TDM (31.2 MHz) channels  
  > "the data with 8 GHz bandwidth were taken with continuum mode (TDM mode, the spectral resolution is 31.2 MHz or $\sim$27 km s$^{-1}$)" (Data and Results)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: synthesised beam 0.4-3.8 arcsec  
  > "the synthesised beam size ranges from $0''.4-3''.8$" (Data and Results)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 19.2 hours total  
  > "The total on-source exposure time of the data is 19.2 hours." (Data and Results)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: [C II] 2P3/2 -> 2P1/2 (1900.5469 GHz)
- External data: [C II] line widths of 27 z>4 galaxies/QSOs used to choose spectral binning  
  > "Figure 1 show a distribution of the [C II] velocity width (FWHM) of 27 [C II]-detected galaxies/QSOs at $z>4$" (Data and Results) [from literature compilation (cite: 2011ApJ...740...63C; 2010A&A...519L...1W; 2012MNRAS.427.1066S)]
- External data: z~4 UV luminosity function  
  > "we plot the [C II] luminosity function expected from the $z\sim 4$ UV luminosity function from (cite: 2006ApJ...653..988Y)" (Discussions and Summary) [from (cite: 2006ApJ...653..988Y)]
- External data: SFR/L[CII] calibration log SFR = -8.52 + 1.18 log L[CII]  
  > "log$SFR$(M$_{\ensuremath{\odot}}$ yr$^{-1}$) $=  -8.52 + 1.18\times$log$L_{\rm [C\,{\sevensize II}]} (L_{\odot})$, by (cite: 2014arXiv1402.4075D)" (Discussions and Summary) [from (cite: 2014arXiv1402.4075D)]
- Simulation/model as data: [C II] luminosity function at z=4 from numerical simulation  
  > "We also compared with the [C II] luminosity function at $z=4$ predicted from a numerical simulation (cite: 2014PASJ...66...70O)" (Discussions and Summary)

## Processing

### Calibration

- pipeline or manual: archive-provided calibration; phase calibrator checked with clean against calibrator database  
  > "the derived flux density is consistent with the flux densities listed in the ALMA calibrator database" (Data and Results)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: archive calibrated data used, no re-calibration  
  > "We used the calibrated data product provided by the archive, without any additional re-calibration of the data." (Data and Results)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: clean  
  > "We used clean to construct data cubes with natural weighting to maximise the sensitivity." (Data and Results)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We used clean to construct data cubes with natural weighting to maximise the sensitivity." (Data and Results)
- uv taper: _not stated_
- cell size: 0.2 arcsec  
  > "We adopted a pixel size of $0''.2$" (Data and Results)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub using line-free parts of the targets  
  > "We used uvcontsub to subtract the continuum from the visibilities using line-free parts of the original targets with the multiple spectral windows." (Data and Results)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: cubes binned to 50, 100, 300, 500 km/s  
  > "we made data cubes with four different spectral resolutions (50, 100, 300, and 500 km s$^{-1}$)" (Data and Results)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Recalibrated data used by Swinbank et al. for the ECDFS SMG test  
  > "Based on the data re-calibrated by (cite: 2013ApJ...768...91H), (cite: 2012MNRAS.427.1066S) detected the $z=4.4$ [C II] emission lines" (Data and Results) [from (cite: 2013ApJ...768...91H)]

### Not stated but needed to reproduce (our reading)

- Exact line-free channel ranges for uvcontsub and continuum fit order
- CASA version
- clean mask/threshold and iterations
- How candidate peaks were searched (peak finder, per-channel vs cube-wide) and how channels were binned
- Survey-volume calculation details (primary beam cutoff, redshift coverage per field)
- Treatment of channels excluded for high noise and original-target lines (which ones)

## Analysis recipe

1. **Select and obtain archival data**: Searched Cycle 0 band 7 projects covering 330-360 GHz with published extragalactic results; used archive calibrated products  
  > "We collected 8 extra-galactic projects from which initial results have been already published." (Data and Results)
   - software: CASA
   - fitting: _not stated_
   - validation: Imaged phase calibrators to confirm flux and unresolved point-source  
  > "We confirmed that the phase calibrator is detected as a spatially un-resolved source at the phase centre" (Data and Results)
2. **Continuum subtraction and cube imaging**: uvcontsub then clean with natural weighting at four velocity resolutions  
  > "We used clean to construct data cubes with natural weighting to maximise the sensitivity." (Data and Results)
   - software: CASA
   - parameter: pixel 0.2 arcsec; Δv = 50, 100, 300, 500 km/s  
  > "We adopted a pixel size of $0''.2$" (Data and Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Blind line search**: Normalise flux by per-channel rms and search for peaks above 6 sigma; none found  
  > "The flux is normalised by using the rms of each binned channel." (Data and Results)
   - parameter: detection threshold 6 sigma  
  > "Therefore we set a threshold of 6-$\sigma$ for our line detection conservatively." (Data and Results)
   - fitting: Flux distributions fitted with Gaussian  
  > "The overall shapes of the normalised flux distributions are well fitted with a Gaussian" (Data and Results)
   - validation: Recovered the two known z=4.4 SMG [C II] lines (ALESS 65.1 at 6.2 sigma, ALESS 61.1 at 3.8 sigma)  
  > "we detected the emission line at 6.2-$\sigma$ from ALESS 65.1" (Data and Results)
4. **Derive luminosity function upper limits**: Survey volume vs depth with primary beam correction; 1-sigma Poisson upper limits (Gehrels 1986); compare with UV-LF and simulation predictions  
  > "The 1-$\sigma$ confidence upper limits on the space densities of [C II] emitters are calculated using Poisson statistics" (Data and Results)
   - assumption: emitters spatially unresolved; A_UV=1; SFR=1.2e-28 L_UV; cosmology H0=72, Om=0.27, OL=0.73  
  > "We assume that line emitters are spatially unresolved in the data cubes." (Data and Results)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : continuum subtraction (uvcontsub) and imaging (clean)  
  > "We used the ALMA data reduction package CASA" (Data and Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| New line emitters above 6 sigma | 0 | not stated | count | 3 | In this search, we could not detect any line emitters above the 6-$\sigma$ significance level. |
| ALESS 65.1 [C II] significance recovered | 6.2 | not stated | sigma | 3 | we detected the emission line at 6.2-$\sigma$ from ALESS 65.1 |
| ALESS 65.1 L[CII] | 2.9e9 | 0.5e9 | Lsun | 3 | $L_{\rm [C\,{\sevensize II}]} = 2.9 \pm 0.5 \times 10^{9} L_{\odot}$ |
| Candidates at 5.5 sigma threshold | 6 | not stated | count | 3 | If we adopt a detection threshold of 5.5-$\sigma$, we could detect 6 emitter candidates. |
| Upper limit on number density at L=1e9 Lsun, 300 km/s | <6.7e-3 | 1 sigma | cMpc^-3 | 4 | $2.8 \times 10^{2}$ / $<6.7 \times 10^{-3}$ |

## Qualitative findings

- Upper limits are at least 2 orders of magnitude above LFs expected from UV LF or simulations.  
  > "These limits are at least 2 orders of magnitude larger than the [C II] luminosity functions expected from the $z \sim 4$ UV luminosity function or from numerical simulation." (abstract)

## Claim tuples

- H: Blind [C II] emitters at z~4.5 can be found in Cycle 0 archival band 7 data | E: Search of continuum-subtracted cubes at four velocity resolutions over 243 fields | R: No new emitters above 6 sigma | F: Only upper limits on the [C II] LF at z~4.5 over 1e8-1e10 Lsun, too shallow to constrain models | **supported**
- H: Cycle 1+2 archival data could constrain the [C II] LF | E: Extrapolation of depth/volume to future data | R: Expected to reach predicted LF | F: An ALMA Patchy Deep Survey is feasible | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Spectral binning chosen from observed [C II] widths of high-z sources (median ~300 km/s, 90% within 50-500)  
  > "The 90 per cent of the sample are distributed in the range of $50-500$ km s$^{-1}$." (Data and Results)
- Alternative: 5.5 sigma threshold rejected as too aggressive given negative-tail noise  
  > "the 5.5-$\sigma$ detection threshold may be too aggressive to detect real source." (Discussions and Summary)
- How they decided it was enough: _not stated_
- Limitation (authors): Extended [C II] emitters much larger than the beam could be missed  
  > "we potentially miss spatially extended [C II] emitter whose size is much larger than the synthesised beam size." (Data and Results)
- Caveat (inferred, ours): Low completeness: no injection-recovery tests beyond two known sources
- Caveat (inferred, ours): Other lines (CO, [O III]) could contaminate but candidates were not followed up
- Caveat (inferred, ours): Highly heterogeneous data and beams without a systematic completeness correction

## Reproducibility

- Data public (paper): Data from ALMA science archive  
  > "before we downloaded the data from the archive" (Data and Results)
- Products in archive: _not stated_
- Missing: CASA version
- Missing: line-free channel selection
- Missing: peak-finding algorithm details
- Missing: survey volume calculation specifics
- Data volume (inferred): ~100s GB to ~1 TB of calibrated measurement sets for 8 projects
- Score (inferred): 3/5, Public data and simple procedure, but search algorithm and volume calculation details are missing.
- Rediscovery candidate: no, Main result is a null detection with partial recipe; search and volume details unstated.

## Links

- Method: (cite: 1986ApJ...303..336G) (Poisson upper limits for non-detections)
- Companion: (cite: 2012MNRAS.427.1066S) (Earlier serendipitous [C II] detection in two z=4.4 SMGs, used as test)
- Related: ALMA Patchy Deep Survey (proposed)

## Checks

```json
{
 "quotes": 51,
 "quotes_ok": 51,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 8,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 34,
  "rate": 0.507
 },
 "evidence_ok": true
}
```

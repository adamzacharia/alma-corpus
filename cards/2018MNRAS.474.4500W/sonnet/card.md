# ALMA and VLA observations of the HD 141569 system

`2018MNRAS.474.4500W` | Monthly Notices of the Royal Astronomical Society 2018 | first author: White, Jacob Aaron | arXiv: 1711.07489 | DOI: 10.1093/mnras/stx3098

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks, stellar_physics
- Question: Is the shallow mm spectral index of the HD 141569 disc real, or is the 9 mm flux contaminated by stellar emission? What is the origin and variability of the 9 mm emission from HD 141569A, B and C?  
  > "suggesting strong non-disc emission is affecting the inferred grain properties." (abstract)
- Target **HD 141569 (A, B, C)**: coordinates RA = 15 h 49 min 57.73 s, Dec = -03 55 16.62 (J2000)  
  > "The observations were centred on HD 141569A using J2000 coordinates RA = 15 h 49 min 57.73 s and $\delta = -03^{\circ} 55' 16.62''$." (Observations); "we adopt the *Gaia* parallactic distance of $111\pm5$ pc (cite: gaia)" (Introduction); z/distance 111±5 pc  
  > "The observations were centred on HD 141569A using J2000 coordinates RA = 15 h 49 min 57.73 s and $\delta = -03^{\circ} 55' 16.62''$." (Observations); "we adopt the *Gaia* parallactic distance of $111\pm5$ pc (cite: gaia)" (Introduction); distance from Gaia parallax  
  > "The observations were centred on HD 141569A using J2000 coordinates RA = 15 h 49 min 57.73 s and $\delta = -03^{\circ} 55' 16.62''$." (Observations); "we adopt the *Gaia* parallactic distance of $111\pm5$ pc (cite: gaia)" (Introduction)

## Data provenance

- ALMA projects: 2013.1.00883.S
- bands: ALMA Band 3 (2.9 mm) archival; VLA Ka band (9 mm)  
  > "Ceres was originally selected as a flux calibrator but the ALMA Pipeline quality assurance (QA) suggested to use the quasar J1550+05, as it is a more reliable calibrator for Band 3 wavelengths." (Observations, Archival Data)
- frequencies and spectral setup: ALMA: 3 spectral windows of 2000 MHz centred at 98.24, 100.04, 108.14 GHz; VLA: 4x2048 MHz basebands at 30, 32, 34, 36 GHz  
  > "Three different spectral windows were used with 2000 MHz bandpasses at rest frequencies centred at 98.24, 100.04, and 108.14 GHz." (Archival Data); "The correlator setup used $4\times2048$ MHz basebands with rest frequency centres at 30, 32, 34, and 36 GHz." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: ALMA 15 to 1547 m, 44 antennas  
  > "Data were taken with 44 antennas with baselines ranging from 15 to 1547 m." (Archival Data)
- angular resolution: ALMA 2.9 mm beam 0.69x0.52 arcsec, PA 56 deg  
  > "The size of the resulting synthesized beam is $0.69 \times 0.52$ arcsec$^{2}$ at a position angle of 56$^{\circ}$" (Archival Data)
- max recoverable scale: _not stated_
- sensitivity: ALMA 24 uJy/beam  
  > "The observations achieve a sensitivity of $24~\mu \rm Jy~beam^{-1}$." (Archival Data)
- time on source: ALMA 1.24 hr (one EB)  
  > "The total integration time for the successful EB was 1.24 hr." (Archival Data)
- observing dates: ALMA 2015 August 8  
  > "These observations were made in two execution blocks (EBs) on 2015 August 8$^{\rm th}$" (Archival Data)
- pi or archival as stated: ALMA 2.9 mm data archival, unpublished  
  > "We also present archival ALMA 2.9 mm observations that to our knowledge are not yet published." (Archival Data)
- Other facility **VLA 16A (VLA/2015-06-140)**: New 9 mm B-configuration continuum, 1.15 hr on source, beam 0.29x0.21 arcsec  
  > "Observations were taken during the VLA Semester 16A (project ID VLA/2015-06-140) using the Ka band (9 mm) in the B antenna configuration with 27 antennas." (Observations)
- Other facility **VLA 14A**: Archival 9 mm D-configuration data, re-analysed  
  > "we take this data from the VLA archive so that we can perform additional analysis of the observations." (Archival Data)
- Other facility **SMA**: 870 um flux and beam from literature  
  > "We take ALMA and SMA 870 $\mu$m flux and beam size values from literature (cite: white; flaherty)." (Archival Data)
- External data: ALMA 870 um flux 3800±500 uJy, peak 1740 uJy/beam, beam 0.42x0.34  
  > "| ALMA | 0.87 | $3800\pm500$ | $1740$ | $0.42\times0.34$ | $-61.1^{\circ}$ | Y | (cite: white) |" (Table 2) [from (cite: white)]
- External data: SMA 870 um flux 8200±2400 uJy  
  > "| SMA | 0.87 | $8200\pm2400$ | $4100$ | $1.66\times1.16$ | $-82.2^{\circ}$ | N | (cite: flaherty) |" (Table 2) [from (cite: flaherty)]
- External data: VLA 14A combined flux of B and C: 51±5 uJy  
  > "we use $51 \pm 5~ \rm\mu Jy$ reported by (cite: macgregor)" (UV Modelling) [from (cite: macgregor)]
- External data: Dust opacity index beta_s = 1.8±0.2  
  > "where $\beta_{s} = 1.8\pm0.2$ is a power law index for the dust opacity (cite: draine)" (Millimetre Spectral Index of the Disc) [from (cite: draine)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline for ALMA and VLA  
  > "Data were reduced using CASA 4.5.0 (cite: casa_reference) pipeline" (Archival Data)
- casa version: CASA 4.5.0  
  > "Data were reduced using the Common Astronomy Software Applications (CASA 4.5.0) pipeline" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: VLA: 3C286; ALMA: J1550+05 (quasar, instead of Ceres)  
  > "J1331+305 (3C286) was used as a flux calibration source." (Observations); "the ALMA Pipeline quality assurance (QA) suggested to use the quasar J1550+05" (Archival Data)
- flux scale uncertainty: 5% for VLA; 10% for ALMA  
  > "a 5% flux calibration uncertainty" (UV Modelling); "Including an absolute flux uncertainty of 10%" (ALMA Data)
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN  
  > "cleaned using CASA’s *CLEAN* algorithm down to a threshold of $\frac{1}{2}~ \sigma_{\rm rms}$" (Archival Data)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The image was generated using natural weighting" (Archival Data)
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
- final beam: VLA 16A 0.29x0.21 arcsec PA 21.6; ALMA 0.69x0.52 arcsec PA 56  
  > "The size of the synthesized beam is $0.29 \times 0.21$ arcsec$^{2}$ at a position angle of 21.6$^{\circ}$." (Observations)
- final rms: VLA 16A 4.7 uJy/beam; ALMA 24 uJy/beam  
  > "sensitivity of $4.7~\mu \rm Jy~beam^{-1}$" (Observations)

### Inherited from earlier work

- VLA 14A calibration procedure  
  > "calibrated with CASA 4.5.0 pipeline (cite: casa_reference) in the procedure described in (cite: macgregor)" (Archival Data) [from (cite: macgregor)]
- Grain size distribution formalism relating alpha_mm to q  
  > "Adopting the methods of (cite: dalessio), (cite: ricci), (cite: macgregor), and (cite: white_fom)" (Millimetre Spectral Index of the Disc) [from (cite: dalessio); (cite: ricci); (cite: macgregor); (cite: white_fom)]

### Not stated but needed to reproduce (our reading)

- Dust temperature used to compute alpha_pl
- Fitting method and uncertainty treatment for alpha_mm from two points
- Starting parameters for uvmodelfit
- Whether VLA data were rebinned or flagged beyond pipeline
- Frequencies used to scale 870 um peak to 9 mm
- Time chunk handling and flagging for light curves
- Stellar radii used in brightness temperature calculation (only partly given)

## Analysis recipe

1. **Image continuum**: CLEAN with natural weighting to 0.5 sigma threshold  
  > "using natural weighting and cleaned using CASA’s *CLEAN* algorithm down to a threshold of $\frac{1}{2}~ \sigma_{\rm rms}$" (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit fluxes and positions in the uv plane**: uvmodelfit point source for VLA; flat-intensity disc for ALMA  
  > "we use a disc with a flat intensity profile (instead of point source) to model the visibilties with the CASA task *uvmodelfit*" (UV Modelling)
   - software: CASA uvmodelfit
   - parameter: Uncertainties: sigma_rms plus 5% (VLA) or 10% (ALMA) calibration, in quadrature  
  > "The uncertainties represent the $\sigma_{\rm rms}$ and a 5% flux calibration uncertainty, added in quadrature." (UV Modelling)
   - fitting: Iterative chi-squared minimisation  
  > "The algorithm converges on the minimum $\chi^{2}$ iteratively." (UV Modelling)
   - validation: Compared with dirty-image peak fluxes and with MacGregor et al. VLA 14A value  
  > "The results are consistent with the peak flux densities per beam as measured directly from the dirty image" (UV Modelling)
3. **Derive mm spectral index and grain size slope q**: Power-law fit F_nu ∝ nu^alpha between 870 um and 2.9 mm; q = (alpha_mm - alpha_pl)/beta_s + 3  
  > "q = \frac{\alpha_{mm} - \alpha_{pl}}{\beta_{s}} + 3," (Millimetre Spectral Index of the Disc)
   - assumption: beta_s = 1.8±0.2  
  > "where $\beta_{s} = 1.8\pm0.2$ is a power law index for the dust opacity (cite: draine)" (Millimetre Spectral Index of the Disc)
   - fitting: _not stated_
   - validation: Compared with Dohnanyi collisional cascade q≈3.5  
  > "a (cite: dohnanyi) collisional cascade will have $q\approx 3.5$" (Millimetre Spectral Index of the Disc)
4. **Time-series variability and brightness temperatures**: Split data into ~5 min chunks, uvmodelfit each, compute brightness temperature from flux and stellar radius  
  > "These points were generated by splitting out the data into $\sim5$ min chunks." (Origin of the 9 mm Emission)
   - software: CASA uvmodelfit
   - assumption: HD 141569A radius ~1.5 Rsun; M dwarf radius ~ R_Jupiter  
  > "taking a stellar radius of$~\sim1.5$ R$_{\odot}$" (Origin of the 9 mm Emission)
   - fitting: _not stated_
   - validation: Correlation of A and B variability, Pearson ~0.69, suggests systematics  
  > "(Pearson correlation coefficient of $\sim0.69$)" (Origin of the 9 mm Emission)

## Software

- **CASA** 4.5.0: Calibration pipeline, CLEAN imaging, uvmodelfit  
  > "Data were reduced using the Common Astronomy Software Applications (CASA 4.5.0) pipeline" (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| VLA 16A flux HD 141569A | 52±5 (53±5 in Sect. 3) | 5 | uJy | 2 | a $52\pm 5~\mu$Jy point source at the location of HD 141569A |
| VLA 16A flux HD 141569B | 149 | 9 | uJy | 2 | The best fit flux is $149 \pm 9~ \rm\mu Jy$ |
| VLA 14A flux HD 141569A (reanalysed) | 82 | 6 | uJy | 2 | We find a flux of $82 \pm 6~ \rm\mu Jy$ and $53\pm 5~\rm \mu Jy$ for VLA 14A and VLA 16A |
| ALMA 2.9 mm flux | 420 | 50 | uJy | 2 | we find a total flux of $420\pm 50~\mu$Jy |
| alpha_mm (ALMA 870 um and 2.9 mm) | 1.81 | 0.20 | dimensionless | 3 | we find $\alpha_{\rm mm} = 1.81\pm 0.20$ |
| grain size slope q | 2.95 | 0.11 | dimensionless | 3 | This would correspond to a $q = 2.95\pm 0.11$ |
| 3 sigma upper limit on disc intensity at 9 mm | ≲15 | not stated | uJy/beam | 2 | $3\sigma$ upper limit on the intensity of the disc’s inner edge to be $\lesssim 15~ \mu \rm Jy~beam^{-1}$ at 9 mm |
| Brightness temperature HD 141569A | ~5e6 | not stated | K | 4 | it would imply a brightness temperature of $\sim 5 \times 10^{6}$ K |
| Brightness temperature HD 141569B | 6e8 | not stated | K | 4 | we find brightness temperatures of $6\times10^{8}$ K and $< 2\times10^{7}$ K, respectively |

## Qualitative findings

- HD 141569A 9 mm flux lies within SED-predicted central clearing and shows potential variability  
  > "the detected flux is contained within the SED-inferred central clearing of the disc" (abstract)

## Claim tuples

- H: The warm disc has an anomalously shallow spectral index (alpha=1.63) | E: New VLA 16A 9 mm observations plus archival ALMA 2.9 mm | R: alpha_mm=1.81±0.20 from ALMA only; 9 mm flux is point-like and lower | F: Previous index is too shallow; 9 mm emission is contaminated by non-disc emission | **supported**
- H: The M dwarf companions emit variable mm/cm emission | E: Time-series uvmodelfit of VLA 16A and comparison with VLA 14A | R: B flux 149 uJy, ranging 90 to 220 uJy | F: B is strongly variable with Tb ~6e8 K | **supported**
- H: HD 141569A itself is variable at 9 mm | E: Time series and epoch comparison | R: Variability seen but correlated with B | F: Potential variability, partly systematic | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Flat disc model for ALMA because beam is comparable to disc size  
  > "The archival ALMA 2.9 mm observations have a synthesized beam that is only slightly smaller than the warm disc." (ALMA Data)
- How they decided it was enough: _not stated_
- Limitation (authors): No VLA disc detection, so cm spectral index is unconstrained  
  > "it is difficult to make firm conclusions regarding the true spectral index of the warm disc at cm wavelengths" (The Warm Dust Disc)
- Caveat (inferred, ours): alpha_mm from only two ALMA points with flux-scale uncertainties
- Caveat (inferred, ours): Single VLA epoch only; variability claims rely on 5-min chunks with low S/N
- Caveat (inferred, ours): Reduced chi2 of 3.9-5.7 indicates poor fits
- Caveat (inferred, ours): Inconsistent A flux (52 vs 53 uJy)

## Reproducibility

- Data public (paper): ALMA data from archive; VLA 14A from VLA archive  
  > "The 2.9 mm ALMA data were taken from the ALMA archive (ID 2013.1.00883)." (Archival Data)
- Products in archive: _not stated_
- Missing: Dust temperature for alpha_pl
- Missing: uvmodelfit starting values
- Missing: Flagging details
- Data volume (inferred): ~10-50 GB (one ALMA Band 3 EB plus two small VLA datasets)
- Score (inferred): 4/5, Public data, standard CASA tools and simple recipe; some parameters unspecified.
- Rediscovery candidate: yes, Public ALMA and VLA data, simple uvmodelfit recipe, numeric fluxes and indices.

## Links

- Method: (cite: macgregor) (VLA 14A calibration and spectral-index framework)
- Companion: (cite: white) (ALMA 870 um observations of HD 141569)
- Related: MESAS

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 45,
  "rate": 0.643
 },
 "evidence_ok": true
}
```

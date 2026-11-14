# Kiloparsec-scale gaseous clumps and star formation at z = 5-7

`2018MNRAS.478.1170C` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Carniani, S. | arXiv: 1712.03985 | DOI: 10.1093/mnras/sty1088

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies
- Question: How does the [CII] morphology of normal z=5-7 star-forming galaxies relate to the UV counterpart, and what does this imply for the L[CII]-SFR and Sigma[CII]-Sigma_SFR relations?  
  > "The goal of this paper is to assess the connection between \[Cii\] and SFR in the early Universe by taking into account the multi-clump morphology of galaxies at $z>5$" (Introduction)
- Target **29 star-forming galaxies at 5<z<7.2 (e.g. HZ1-HZ10, CR7, Himiko, WMH5, BDF2203)**: coordinates RA/Dec in Table 1 (e.g. BDF2203 336.958, -35.1472)  
  > "BDF2203 | 336.958 | -35.1472" (Table 1); z/distance z from Lyα, e.g. BDF2203 z=6.12; [CII] z=6.1224  
  > "BDF2203 | 336.958 | -35.1472" (Table 1); distance from Lyα redshifts; cosmology Planck 2016  
  > "BDF2203 | 336.958 | -35.1472" (Table 1)

## Data provenance

- ALMA projects: 2015.1.01105.S, 2012.1.00719.S, 2011.0.00115.S, 2013.1.00815.S
- bands: Band 6 (new data)  
  > "were observed with ALMA in band 6 during Cycle 3 and Cycle 4" (Additional ALMA data - observation and data reduction)
- frequencies and spectral setup: 4 SPWs, ~30 MHz (~35 km/s) resolution, 1.875 GHz bandwidth, one on [CII]  
  > "we used four spectral windows (SPWs) set up in frequency division mode with a spectral resolution of $\sim$30 MHz ($\sim35$ km/s) and bandwidth of 1.875 GHz." (Additional ALMA data - observation and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: semi-compact array, 0.3'' to 0.8'' resolution  
  > "ALMA observations were carried out with a semi-compact array configuration with angular resolutions ranging from 0.3$''$ and 0.8$''$." (Additional ALMA data - observation and data reduction)
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 0.1-0.8 h per target  
  > "total on source integration time of 0.1-0.8 h with a precipitable water vapour of 0.4-1.4 mm" (Additional ALMA data - observation and data reduction)
- observing dates: _not stated_
- pi or archival as stated: new data PI Pentericci (Cycles 3 and 4); rest archival  
  > "observed with ALMA in Cycles 3 and 4 (P.I. Pentericci)" (2.2 Additional new ALMA data)
- Line: [CII] 158 um fine-structure line (not stated)
- Other facility **HST and VISTA**: NIR (rest-frame UV) images  
  > "we have also used Hubble Space Telescope (*HST*) and Visible and Infrared Survey Telescope for Astronomy (VISTA) NIR observations" (2.1 Archival data)
- Other facility **GAIA DR1 / AllWISE**: astrometric reference for registration  
  > "we have matched the NIR foreground sources and ALMA phase calibrators to either GAIA Data Release 1 catalogue" (2.1 Archival data)
- External data: Local L[CII]-SFR relation  
  > "The green line illustrates the local relation obtained by (cite: De-Looze:2014)" (4 L[CII]-SFR) [from (cite: De-Looze:2014)]
- External data: Local Sigma[CII]-Sigma_SFR relation  
  > "We also show the local relation by (cite: Herrera-Camus:2015) and its dispersion." (6.2 Surface brightness) [from (cite: Herrera-Camus:2015)]
- External data: Lyα EWs and metallicities, HST UV images  
  > "We note that (cite: Faisst:2017a) estimated a metallicity of 12+log(O/H)$>$8.5 for HZ10 and HZ9" (6.2 Surface brightness) [from (cite: Faisst:2017a)]

## Processing

### Calibration

- pipeline or manual: new data calibrated with CASA; archival following prior works  
  > "For these objects, ALMA observations have been calibrated following the prescriptions presented in previous works." (2.1 Archival data)
- casa version: CASA v4.5.2  
  > "ALMA observations were calibrated by using CASA software version v4.5.2" (Additional ALMA data - observation and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "Continuum and data cube images were obtained by using the CASA task clean and natural weighting." (Additional ALMA data - observation and data reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "Continuum and data cube images were obtained by using the CASA task clean and natural weighting." (Additional ALMA data - observation and data reduction)
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

- Calibration of archival ALMA data  
  > "ALMA observations have been calibrated following the prescriptions presented in previous works." (2.1 Archival data) [from previous works (Table 1 refs)]
- SFR calibrations  
  > "by adopting the calibrations presented in (cite: Kennicutt:2012)" (2.3 SFR estimates) [from (cite: Kennicutt:2012)]
- IGM correction of Lyα EW  
  > "by following the prescription given by (cite: Harikane:2017)" (5 Lyα EW) [from (cite: Harikane:2017)]

### Not stated but needed to reproduce (our reading)

- Imaging and calibration details for archival datasets (robust, tapers, beam)
- Channel widths and velocity ranges for channel maps and clump separation
- Procedure and uncertainties for astrometric shifts per source
- How the UV luminosity and Lyα EW for each source were obtained
- Fitting method for linear fits and dispersion error
- Aperture used for continuum/flux extraction

## Analysis recipe

1. **Register ALMA and NIR images**: Align using serendipitous continuum sources, or GAIA/AllWISE-matched calibrators; shifts of 0.1''-0.25'' applied to NIR images  
  > "We therefore applied the astrometric shifts, which span a range between 0.1$''$ and 0.25$''$, to the NIR images." (2.1 Archival data)
   - assumption: mm emission of serendipitous sources cospatial with NIR  
  > "by assuming that the millimetre emission of these sources is cospatial to the near-infrared map" (2.1 Archival data)
   - fitting: _not stated_
   - validation: Consistency between multiple serendipitous sources and GAIA offsets  
  > "we have checked that the estimated astrometric offset is consistent with those obtained by aligning NIR foreground sources and ALMA phase calibrators" (2.1 Archival data)
2. **Derive FIR luminosity and SFR**: Greybody from single continuum point; SFR_UV and SFR_FIR from Kennicutt & Evans calibrations  
  > "We thus assume T$_{\rm d}$ = 30K and $\beta$ = 1.5" (2.3 SFR estimates)
   - assumption: Td=30 K, beta=1.5; total SFR ~ SFR_UV unless continuum detected  
  > "we assume total ${\rm SFR \approx SFR_{\rm UV}}$ with no dust correction for those galaxies without continuum detection." (2.3 SFR estimates)
   - fitting: _not stated_
   - validation: _not stated_
3. **Channel-map kinematic deblending and size measurement**: Extract channel maps at velocities relative to galaxy redshift; fit 2D elliptical Gaussian to maps, accounting for resolution  
  > "We also estimate the size of the various UV and \[Cii\] emission by fitting a 2D elliptical Gaussian profile to emission maps" (2.3 SFR estimates)
   - fitting: 2D elliptical Gaussian  
  > "We also estimate the size of the various UV and \[Cii\] emission by fitting a 2D elliptical Gaussian profile to emission maps and by taking into account the angular resolution of the observations." (2.3 SFR estimates and morphology analysis)
   - validation: UV clump positions compared with [CII] peaks  
  > "The location of the individual rest-frame UV clumps is consistent with the peak positions of the \[Cii\] emission extracted at different velocities" (3 Multi-components systems)
4. **Compare L[CII]-SFR with local relation and quantify dispersion and Lyα EW trend**: Offset dLog[CII] from De Looze relation per component; dispersion; linear fit vs log EW(Lyα)  
  > "for each galaxy we calculate the offset from the relation as $\Delta$Log(\[Cii\])=Log(\[Cii\])-Log(\[Cii\]$_{\rm expect-local}$)" (4 L[CII]-SFR)
   - fitting: linear fit, method not stated  
  > "A linear fit gives" (5 The relation between Ly$\alpha$ EW and [Cii] emission)
   - validation: _not stated_
5. **Sigma[CII]-Sigma_SFR relation and size comparison**: Surface brightness and SFR density from half-light radii; fit relation  
  > "we can estimate the \[Cii\] surface brightness and SFR surface density of each sub-component" (6.2 Surface brightness)
   - fitting: _not stated_
   - validation: UV images smoothed to test whether UV extent recovers [CII] extent  
  > "even by smoothing the UV images in the deepest observations available to us, we still do not recover the extension observed in \[Cii\]" (6.1 Spatial extension)

## Software

- **CASA** v4.5.2: calibration and imaging (clean) of new data  
  > "ALMA observations were calibrated by using CASA software version v4.5.2" (Additional ALMA data - observation and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| L[CII]-SFR dispersion | 0.48 | 0.07 | dex | 4 | it has a dispersion of 0.48$\pm$0.07 dex |
| BDF2203 [CII] redshift | 6.1224 | 0.0005 | dimensionless | 0 | $z_{\rm [CII]}=6.1224\pm0.0005$ |
| BDF2203 L[CII] | 12.5e7 | 2.5e7 | Lsun | 0 | L$_{\rm[CII]}$$=(12.5\pm2.5)\times10^{7}$ L$_{\odot}$ at z=6.12 |
| BDF2203 FWHM | 150 | 50 | km/s | 0 | we estimate a FWHM=$150\pm50$ km/s |
| Slope of dlog[CII] vs log EW(Lyα) | -0.44 | 0.15 | dimensionless | 4 | (0.55\pm0.20)-(0.44\pm0.15)\log(EW(Ly\alpha)) |
| Sigma relation slope | 0.63 | 0.11 | dimensionless | 5 | (0.63\pm0.11)\times(\log(\Sigma_{\rm [CII]})-(25\pm6) |
| Multi-clump galaxies | 9 of 21 [CII]-detected | not stated | count | 3 | We have found a clear multi-clump morphology in nine out of 21 $z>5$ galaxies having \[Cii\] detections |

## Qualitative findings

- [CII] generally much more extended than UV emission; most [CII] not tied to primary UV component  
  > "The morphological analysis also reveals that \[Cii\] emission is generally much more extended than the UV emission." (abstract)

## Claim tuples

- H: Accounting for clumps changes the high-z L[CII]-SFR relation | E: Split multi-component systems and compare each with the De Looze relation | R: No offset; dispersion 0.48±0.07 dex | F: Consistent with local relation but about twice the scatter | **supported**
- H: Deviation depends on Lyα EW | E: Linear fit of offset vs EW | R: slope -0.44±0.15, dispersion 0.25 dex | F: Weak anti-correlation | **partially**
- H: High-z galaxies follow the local Sigma[CII]-Sigma_SFR relation | E: Compare surface brightness with Herrera-Camus relation | R: Most below the local relation | F: Low Sigma[CII] due to extended [CII] | **refuted**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Lensed systems and unconfirmed candidates excluded  
  > "The sample does not include lensed systems" (2.1 Archival data)
- How they decided it was enough: Sample limited to SFR≲100 Msun/yr, unlensed, spectroscopically confirmed  
  > "We limit our sample to those systems with SFR $\lesssim 100$ M$_{\odot}$ yr$^{-1}$" (2.1 Archival data)
- Limitation (authors): Low angular resolution and sensitivity insufficient for morphology of BDF2203  
  > "The low angular resolution and sensitivity of current observations are not sufficient to assess the morphology of the FIR line emission." (2.2 Additional new ALMA data)
- Caveat (inferred, ours): Heterogeneous archival data and resolutions may bias clump detection and sizes
- Caveat (inferred, ours): Single-band continuum with assumed Td, beta gives uncertain FIR (0.6 dex)
- Caveat (inferred, ours): Marginal ~3.5 sigma clumps
- Caveat (inferred, ours): Dispersion includes upper limits; method not described
- Caveat (inferred, ours): Many components' UV counterparts are undetected

## Reproducibility

- Data public (paper): Data retrievable from ALMA archive  
  > "which can be retrieved from the ALMA data archive" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Per-dataset imaging parameters
- Missing: Clump definitions and channel ranges
- Missing: HST/VISTA images and UV measurements details
- Missing: Fitting procedures
- Data volume (inferred): ~100-300 GB across ~10 projects
- Score (inferred): 3/5, Public data and clear sample, but archival re-analysis and clump extraction are loosely specified.
- Rediscovery candidate: no, Recipe is incomplete (imaging parameters, clump decomposition, UV data inputs).

## Links

- Companion: (cite: Carniani:2017a) (Earlier [CII]/[OIII] analysis of offsets for BDF3299/BDF512)
- Related: CANDELSz7

## Checks

```json
{
 "quotes": 55,
 "quotes_ok": 55,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2012.1.00033.S",
  "2012.1.00523.S",
  "2012.A.00040.S",
  "2013.1.00433.S",
  "2015.1.00834.S",
  "2016.1.01240.S"
 ],
 "codes_printed_but_missing": [
  "2012.1.00033.S",
  "2012.1.00523.S",
  "2012.A.00040.S",
  "2013.A.00433.S",
  "2015.1.00834.S",
  "2015.1.01240.S",
  "2016.1.01240.S"
 ],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 39,
  "rate": 0.542
 },
 "evidence_ok": true
}
```

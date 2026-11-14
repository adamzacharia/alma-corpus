# The 2014 ALMA Long Baseline Campaign: Observations of the Strongly Lensed Submillimeter Galaxy HATLAS J090311.6+003906 at z = 3.042

`2015ApJ...808L...4A` | The Astrophysical Journal Letters 2015 | first author: ALMA Partnership | arXiv: 1503.02652 | DOI: 10.1088/2041-8205/808/1/L4

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What do very high resolution ALMA long-baseline continuum, CO and H2O observations reveal about the lensed submillimeter galaxy SDP.81 at z=3.042, including emission at the lens centre?  
  > "We present initial results of very high resolution Atacama Large Millimeter/submillimeter Array (ALMA) observations of the $z$=3.042 gravitationally lensed submillimeter galaxy HATLAS J090311.6+003906 (SDP.81)." (abstract)
- Target **HATLAS J090311.6+003906 (SDP.81)**: coordinates phase center 09h03m11.61s +00d39m06.7s (J2000)  
  > "NE10 determined that SDP.81 is a background source at $z$=3.042 that is being lensed by a foreground elliptical galaxy at $z$=0.299." (1 Introduction); "The phase center was 09$^{h}$03$^{m}$11$^{s}$.61 $+$00${\ensuremath{^\circ}}$39${\ensuremath{'}}$06${\ensuremath{''}}$.7 (J2000)." (Data reduction details); z/distance z=3.042 (source); z=0.299 (lens)  
  > "NE10 determined that SDP.81 is a background source at $z$=3.042 that is being lensed by a foreground elliptical galaxy at $z$=0.299." (1 Introduction); "The phase center was 09$^{h}$03$^{m}$11$^{s}$.61 $+$00${\ensuremath{^\circ}}$39${\ensuremath{'}}$06${\ensuremath{''}}$.7 (J2000)." (Data reduction details); distance from Negrello et al. 2010 (NE10), CO spectroscopic redshifts  
  > "NE10 determined that SDP.81 is a background source at $z$=3.042 that is being lensed by a foreground elliptical galaxy at $z$=0.299." (1 Introduction); "The phase center was 09$^{h}$03$^{m}$11$^{s}$.61 $+$00${\ensuremath{^\circ}}$39${\ensuremath{'}}$06${\ensuremath{''}}$.7 (J2000)." (Data reduction details)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 4 (~2 mm), Band 6 (~1.3 mm), Band 7 (~1.0 mm)  
  > "Observations were carried out in Band 4 ($\sim$2 mm), Band 6 ($\sim$1.3 mm) and Band 7 ($\sim$1.0 mm)." (2 Observations and Data Reduction)
- frequencies and spectral setup: Per band 7.5 GHz split into 4 spws: three 15.6 MHz continuum spws and one line spw  
  > "the total available 7.5 GHz bandwidth was divided into four spectral windows (spws): three 15.6 MHz channel width spws" (2 Observations and Data Reduction)
- continuum bandwidth: ~7 GHz  
  > "Continuum images were integrated over a bandwidth of $\sim$7 GHz" (Data reduction details)
- arrays: _not stated_
- configurations: _not stated_
- baselines: ~15 m to 15 km  
  > "baseline lengths ranged from $\sim$15 m to 15 km." (2 Observations and Data Reduction)
- angular resolution: 23-60 mas continuum; ~170 mas CO (tapered); ~0.9" H2O  
  > "The resulting synthesized beam sizes range from $\sim$23–60 mas." (2 Observations and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 5.9, 4.4 and 5.6 hours in Bands 4, 6, 7  
  > "The total on-source integration times were 5.9, 4.4 and 5.6 hours in Bands 4, 6, and 7, respectively." (2 Observations and Data Reduction)
- observing dates: 2014 October  
  > "were carried out in 2014 October as part of the 2014 ALMA Long Baseline Campaign" (2 Observations and Data Reduction)
- pi or archival as stated: _not stated_
- Line: CO J=5-4 (576.267 GHz)
- Line: CO J=8-7 (921.799 GHz)
- Line: CO J=10-9 (1151.985 GHz)
- Line: H2O 2_02-1_11 (987.927 GHz)
- External data: PdBI CO 5-4 and H2O fluxes, 244 GHz continuum 27±1.2 mJy for comparison  
  > "PdBI 244 GHz value (27$\pm$1.2 mJy; OM13)" (3.1 Dust continuum emission) [from Omont et al. 2013 (cite: Omont2013)]
- External data: Unmagnified IR luminosity and SED; muL_IR=5.4e13 Lsun  
  > "Taking the total IR luminosity $\mu$L$_{IR}=$5.4$\times$10$^{13}$ L$_{\odot}$ (uncorrected for magnification) from NE14" (3.2.3 CO line ratios) [from Negrello et al. 2014 (NE14)]
- External data: CO J=1-0 value of 1.1 Jy km/s  
  > "Taking the CO $J$=1-0 value of 1.1 Jy km s$^{-1}$ from (cite: Frayer2011)" (3.2.3 CO line ratios) [from (cite: Frayer2011)]
- External data: 1.4 GHz FIRST flux density 0.61 mJy  
  > "the 1.4 GHz FIRST flux density (0.61 mJy)" (3.1.1 Detection of continuum emission at the central position of the foreground lens) [from FIRST survey (no citation key given)]

## Processing

### Calibration

- pipeline or manual: CASA, procedure in scripts on ALMA Science Portal  
  > "The procedure is described in the scripts available on the ALMA Science Portal" (2 Observations and Data Reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0825+0309 and J0854+2006 (or J0750+1231 or J1058+0133 in a few cases)  
  > "Bandpass and flux calibration were performed using observations of the quasars J0825+0309 and J0854+2006 (or in a few cases J0750+1231 or J1058+0133), respectively" (Data reduction details)
- flux scale uncertainty: 5%  
  > "Values do not include 5% absolute flux calibration uncertainty." (Table 1)
- self calibration: None; insufficient S/N on longest baselines  
  > "None of the data were self-calibrated, since our attempts to perform self-calibration showed that there was insufficient signal-to-noise on the longest baseline antennas." (2 Observations and Data Reduction)

### Imaging

- task: _not stated_
- deconvolver: multi-scale CLEAN, multi-frequency synthesis, nterms=1  
  > "produced using multi-frequency synthesis, a *robust*=1 weighting of the visibilities, and *nterms*=1." (Data reduction details)
- weighting robust: robust = 1  
  > "Imaging was carried out using a *robust*=1 weighting of the visibilities." (2 Observations and Data Reduction)
- uv taper: CO and continuum-for-lines tapered to 1000 kλ; H2O to 200 kλ  
  > "it was necessary to taper the CO line $uv$ data to 1000 k$\lambda$" (2 Observations and Data Reduction)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: 0, 5, 15 (0, 5, 15, 45 in Band 4)  
  > "with scales of 0, 5 and 15 for both the continuum and spectral line imaging (0, 5, 15 and 45 in Band 4)" (Data reduction details)
- continuum subtraction: spectral line data continuum subtracted  
  > "All the spectral line data were continuum subtracted" (2 Observations and Data Reduction)
- line free channels: _not stated_
- primary beam correction: not applied (<5% effect)  
  > "the images have not been corrected for the effect of primary beam attenuation." (Data reduction details)
- array combination: _not stated_
- smoothing: CO smoothed to common 0.2" resolution for measurements  
  > "images that had first been smoothed to the same resolution (0.2$''$)" (3.2.1 Properties of the CO images)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Array configuration, tunings and correlator setup details  
  > "Other details of the observations, tunings and correlator setup are given in AL15 and Appendix [5](#details)." (2 Observations and Data Reduction) [from ALMA Partnership, Fomalont et al. 2015a (AL15)]

### Not stated but needed to reproduce (our reading)

- CASA version
- Image sizes and cell sizes
- Mask definitions used in CLEAN and cleaning thresholds
- Line-free channels for continuum subtraction
- Exact aperture/polygon definitions for flux measurement
- Exact tapering recipe for Band 6&7 spectral index map

## Analysis recipe

1. **Calibrate and image continuum**: Standard CASA reduction with scripts from ALMA Science Portal; multi-scale multi-frequency synthesis CLEAN, robust=1, no self-calibration  
  > "The data were reduced using the Common Astronomy Software Application package" (2 Observations and Data Reduction)
   - software: CASA
   - parameter: robust=1; scales 0,5,15  
  > "with scales of 0, 5 and 15 for both the continuum and spectral line imaging" (Data reduction details)
   - fitting: _not stated_
   - validation: Compared fluxes with PdBI and SMA/SED values  
  > "The 1.0, 1.14, 1.3 and 2.0 mm flux densities are consistent with the SED of the background source presented by NE14." (3.1 Dust continuum emission)
2. **Measure continuum fluxes**: Integrated flux in apertures on tapered images; peaks from high-resolution images  
  > "These were computed within apertures that matched the spatial extent of the continuum emission in each band using the tapered images." (3.1 Dust continuum emission)
   - fitting: _not stated_
   - validation: _not stated_
3. **Spectral index maps and lens-centre index**: Band 6&7 index image from data tapered to 1000 kλ, pixels <4σ masked; lens-core index from 151, 236, 290 GHz and 1.4 GHz flux  
  > "Pixels $<$4$\sigma$ have been masked." (3.1.2 Spectral index)
   - fitting: _not stated_
   - validation: _not stated_
4. **Extract and fit CO and H2O spectra, line ratios**: Spatially integrate over polygon on S/N>3 moment-0 images, Gaussian fits, derive line ratios and L_IR/L'CO  
  > "The CO parameters derived from Gaussian fits are given in Table" (3.2.1 Properties of the CO images)
   - parameter: CO channels 21 km/s; H2O channels 10.5 km/s  
  > "The CO data were binned spectrally into channels 21 km s$^{-1}$ wide." (2 Observations and Data Reduction)
   - assumption: Cosmology H0=67, Om=0.32, OL=0.68  
  > "we adopt a cosmology with $H_{0}$=67 km s$^{-1}$ Mpc$^{-1}$, $\Omega_{m}$=0.32, $\Omega_{\Lambda}$=0.68" (1 Introduction)
   - fitting: Gaussian profile fits (details not stated)  
  > "The CO parameters derived from Gaussian fits are given in Table" (Results, Properties of the CO images)
   - validation: Compared with PdBI CO 5-4 and H2O values  
  > "The ALMA integrated intensity and spectral profile are in good agreement with the PdBI value" (3.3 Water emission)

## Software

- **CASA** : Data reduction and imaging  
  > "The data were reduced using the Common Astronomy Software Application package" (2 Observations and Data Reduction)
- **Astropy** : Acknowledged as used in the research  
  > "This research made use of Astropy, a community-developed core Python package for Astronomy" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Highest continuum angular resolution | 23 | not stated | mas | 1 | at unprecedented angular resolutions as fine as 23 milliarcseconds (mas) |
| Total continuum flux density, 236 GHz | 26.3 | ±1.3 | mJy | 2 | / 6 / 236 / Total / ... / 10 / 39$\times$30 (20) / 26.3$\pm$1.3 / 21 / |
| Total continuum flux density, 290 GHz | 37.7 | ±1.5 | mJy | 2 | / 7 / 290 / Total / ... / 9 / 31$\times$23 (16) / 37.7$\pm$1.5 / 21 / |
| Total continuum flux density, 151 GHz | 3.5 | ±0.1 | mJy | 2 | / 4 / 151 / Total / ... / 8 / 56$\times$50 (18) / 3.5$\pm$0.1 / 11 / |
| Spectral index of lens-centre emission (1.4-290 GHz) | -0.49 | ±0.13 | dimensionless | 3 | is $-$0.49$\pm$0.13, which implies that the majority of the emission we have detected originates from the core of the foreground elliptical galaxy |
| Mean Band 6-7 spectral index in unmasked regions | 2.34 | ±0.61 | dimensionless | 3 | The mean spectral index in the unmasked regions is 2.34$\pm$0.61 |
| CO line ratio r85 | 0.5 | ±0.1 | dimensionless | 4 | $r_{85}$=0.5$\pm$0.1, $r_{108}$=0.2$\pm$0.1 and $r_{105}$=0.1$\pm$0.1 |
| L_IR/L'CO for CO 5-4 | 346 | ±62 | Lsun (K km/s pc^2)^-1 | 4 | the ratio L$_{IR}$/L$'_{CO}$ is 346$\pm$62 L$_{\odot}$(K km s$^{-1}$pc$^{2})^{-1}$ for CO $J$=5-4 |
| H2O/CO(8-7) line ratio | 0.2 | ±0.1 | dimensionless | 4 | We find an H$_{\rm 2}$O/CO $J$=8-7 line ratio, $I_{H_{2}O}$/$I_{CO}$ of 0.2$\pm$0.1. |

## Qualitative findings

- CO emission traces the arcs but morphologies differ between CO transitions and from continuum  
  > "found to broadly trace the gravitational arc structures but with differing morphologies between the CO transitions and compared to the dust continuum" (abstract)

## Claim tuples

- H: Can ALMA long baselines resolve the lensed SMG consistently with previous fluxes? | E: Continuum imaging at 151, 236, 290 GHz with baselines to 15 km | R: Beams as fine as 23 mas; fluxes consistent with PdBI/SMA | F: Fluxes remain consistent despite large resolution increase | **supported**
- H: Is the central lens continuum emission from an AGN in the lens? | E: Flux at lens position in three bands plus FIRST 1.4 GHz | R: Spectral index -0.49±0.13 | F: Emission consistent with the core of the foreground lensing galaxy | **partially**
- H: Can H2O be detected at higher resolution? | E: Tapered H2O image from short baselines | R: Emission clearly detected in E arc at ~0.9" | F: Most resolved thermal H2O detection in an extragalactic source | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: robust=1 weighting critical due to lack of 200-500 m baseline coverage  
  > "the use of robust weighting (*robust*=1) was critical for achieving acceptable image quality" (2 Observations and Data Reduction)
- Alternative: nterms=2 combined Band 6&7 imaging rejected as S/N too low; tapered image approach used  
  > "The SNR of the full-resolution $uv$ data was found to be too low for the algorithm to determine the spectral index" (Data reduction details)
- How they decided it was enough: _not stated_
- Limitation (authors): Differential lensing cannot be quantified without detailed lens modelling, which is beyond scope  
  > "Without detailed modeling, any effect from differential magnification cannot be quantified" (4 Discussion)
- Caveat (inferred, ours): No lens modelling, so arc fluxes are magnified and differential magnification is unaddressed
- Caveat (inferred, ours): Central-source AGN interpretation relies on a non-simultaneous FIRST flux
- Caveat (inferred, ours): Aperture flux definitions are subjective

## Reproducibility

- Data public (paper): Data publicly available from the ALMA Science Portal  
  > "These data are publicly available from the ALMA Science Portal" (2 Observations and Data Reduction)
- Products in archive: _not stated_
- Code: Reduction scripts available on ALMA Science Portal  
  > "The procedure is described in the scripts available on the ALMA Science Portal" (2 Observations and Data Reduction)
- Missing: CASA version
- Missing: Image/cell sizes and masks
- Missing: Line-free channel selection
- Data volume (inferred): Large, likely hundreds of GB to ~1 TB raw across 3 bands with 9-12 executions each
- Score (inferred): 3/5, Public data and scripts exist with robust, taper and scales stated, but CASA version, masks and apertures are missing.
- Rediscovery candidate: yes, Public SV data, scripts, and mostly numeric flux and line results; recipe mostly specified.

## Links

- Method: Cornwell 2008 (cite: Cornwell2008) (Multi-scale CLEAN)
- Method: Rau & Cornwell 2011 (cite: Rau+Cornwell2011) (nterms=2 multi-term imaging)
- Companion: ALMA Partnership, Fomalont et al. 2015a (cite: Alma2015a) (Campaign description and observation details)
- Related: 2014 ALMA Long Baseline Campaign Science Verification
- Related: H-ATLAS

## Checks

```json
{
 "quotes": 65,
 "quotes_ok": 65,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00016.SV"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 45,
  "rate": 0.652
 },
 "evidence_ok": true
}
```

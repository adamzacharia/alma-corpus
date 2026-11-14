# [C II] Line Emission in Massive Star-forming Galaxies at z = 4.7

`2012ApJ...752L..30W` | The Astrophysical Journal Letters 2012 | first author: Wagg, J. | arXiv: 1205.3498 | DOI: 10.1088/2041-8205/752/2/L30

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: What are the [CII] line and 340 GHz dust continuum properties of the quasar host, the SMG and a faint companion in BR1202-0725 at z=4.7, and how do their [CII]/FIR ratios compare with other high-z systems?  
  > "In this work, we present observations of the thermal dust continuum and redshifted [CII] line emission in the quasar host galaxy, BR1202-0725 at $z = 4.7$" (Introduction)
- Target **BR1202-0725 (North SMG, South quasar host, SW companion)**: coordinates _not stated_; z/distance z = 4.7 (z_[CII] = 4.6906 North, 4.6943 South)  
  > "These are separated by 3.8$''$ (25 kpc) in the North-West direction" (Introduction); "| BR1202-0725 North | 18.8$\pm$2.8 | 4.6906 | 722$\pm$12 | 14.7$\pm$2.2 | 10.0$\pm$1.5 | $8.3\pm1.2$ |" (Table 1); distance from [CII] Gaussian fits in this paper  
  > "These are separated by 3.8$''$ (25 kpc) in the North-West direction" (Introduction); "| BR1202-0725 North | 18.8$\pm$2.8 | 4.6906 | 722$\pm$12 | 14.7$\pm$2.2 | 10.0$\pm$1.5 | $8.3\pm1.2$ |" (Table 1)

## Data provenance

- ALMA projects: 2011.0.00006.SV
- bands: Band 7, 335 GHz  
  > "The BR1202-0725 system was observed at 335 GHz (Band 7) with 17 12-m diameter antennas" (Observations)
- frequencies and spectral setup: 4 spectral windows of 1.875 GHz (7.5 GHz total); channel spacing 15.6 MHz (~14 km/s) at 334.96 GHz  
  > "The total bandwidth of these observations was 7.5 GHz, divided into four spectral windows of width 1.875 GHz." (Observations); "The correlator channel spacing was 15.6 MHz, corresponding to $\sim$14 km s$^{-1}$ at the observed frequency of 334.96 GHz." (Observations)
- continuum bandwidth: _not stated_
- arrays: 17 12-m antennas, science verification  
  > "17 12-m diameter antennas of the Atacama Large Millimeter/submillimeter Array as part of science verification on January 16, 2012" (Observations)
- configurations: mostly compact, two antennas on longer baselines  
  > "Most of the antennas were in a compact configuration with two antennas on longer baselines" (Observations)
- baselines: maximum ~350 m  
  > "providing a maximum baseline length of $\sim$350-m" (Observations)
- angular resolution: 1.30'' x 0.86''  
  > "The synthesized beamsize of the 340 GHz continuum observations is $1.30'' \times 0.86''$" (Results and analysis)
- max recoverable scale: _not stated_
- sensitivity: continuum 0.2 mJy/beam at 340 GHz; channel rms 2.0 mJy/beam at ~28 km/s  
  > "which results in a 340 GHz continuum sensitivity of 0.2 mJy per beam" (Observations); "the channel rms is 2.0 mJy per beam" (Observations)
- time on source: 25 minutes  
  > "The total on-source observing time was 25 minutes" (Observations)
- observing dates: January 16, 2012  
  > "as part of science verification on January 16, 2012" (Observations)
- pi or archival as stated: _not stated_
- Line: [CII] 157.7 micron fine structure line (1900.539 GHz)
- Other facility **HST (ACS F775W, WFPC2 F814W, NIC2 F160W)**: Optical/NIR images for overlay and counterpart identification  
  > "Figure 2 shows this thermal dust continuum emission overlaid on the *HST* ACS F775W, WFPC2 F814W and NIC2 F160W images." (Results and analysis)
- External data: FIR luminosities of North (1.2e13 Lsun) and South (2.6e13 Lsun)  
  > "For the quasar and the SMG we adopt the FIR luminosity estimates of Iono et al. (2006)" (Results and analysis) [from Iono et al. (2006)]
- External data: 1.4 GHz 3-sigma upper limit of 48 uJy for SW source  
  > "BR1202-0725 SW is not detected in the 1.4 GHz observations of Carilli et al. (2002), implying a 3-$\sigma$ upper-limit of 48 $\mu$Jy at 1.4 GHz." (Results and analysis) [from Carilli et al. (2002)]
- External data: SCUBA 850 um flux 42 +/- 2 mJy for comparison  
  > "$S_{850\mu m} = 42\pm 2$ mJy; McMahon et al. 1999" (Results and analysis) [from McMahon et al. 1999]

## Processing

### Calibration

- pipeline or manual: Manual CASA analysis; data lack Tsys and WVR corrections  
  > "The data presented here lack measurements of system temperature and water vapor radiometer correction" (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan sets scale; 3C279 gain calibrator at 17 Jy  
  > "The flux density scale was derived using observations of Titan. We derive a flux density of 17 Jy for the complex gain calibrator, 3C279" (Observations)
- flux scale uncertainty: 15%  
  > "We estimate this uncertainty to be 15% and include this in our measured flux densities and integrated intensities." (Observations)
- self calibration: Amplitude and phase self-cal with 3 min solution interval on line-free emission  
  > "Amplitude and phase self-calibration were done using a 3 min averaging time for complex gain solutions" (Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: UV-plane continuum model from last three spectral windows subtracted from first window  
  > "A UV plane model for the continuum emission is derived from these spectral windows and subtracted from the first window." (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: resampled to ~28 km/s  
  > "After continuum subtraction and resampling to $\sim$28 km s$^{-1}$ resolution" (Observations)
- final beam: 1.30'' x 0.86''  
  > "The synthesized beamsize of the 340 GHz continuum observations is $1.30'' \times 0.86''$" (Results and analysis)
- final rms: 0.2 mJy/beam continuum; 2.0 mJy/beam per channel  
  > "the channel rms is 2.0 mJy per beam" (Observations)

### Inherited from earlier work

- L_FIR for North and South adopted from Iono et al. fits with Yun & Carilli templates  
  > "who fit the FIR-to-radio observations using the templates of Yun & Carilli (2002)" (Results and analysis) [from Iono et al. (2006)]
- Line luminosity definition  
  > "Following the definition of line luminosity (see Solomon & Vanden Bout 2005)" (Results and analysis) [from Solomon & Vanden Bout 2005]

### Not stated but needed to reproduce (our reading)

- Image size, cell size, weighting/robust, deconvolver, masking and clean threshold
- Line-free channels and the continuum-fit order used for subtraction
- Which spectral window contains [CII] and the spectral axis/velocity reference
- Self-calibration reference model and iteration details
- Spectral extraction aperture (peak pixel or region)
- Flux and positions of Gaussian-fit components and fit software
- Exact L_FIR calculation from 340 GHz flux (integration of modified blackbody, CMB correction)
- Data are SV; reduction scripts not given

## Analysis recipe

1. **Calibrate and self-calibrate**: Flux scale from Titan, gain and bandpass from 3C279, then amplitude and phase self-calibration  
  > "The spectral bandpass shape was also measured using 3C279." (Observations)
   - software: CASA
   - parameter: 3 min self-cal solution interval; 7 min calibration cycle  
  > "A 7 min calibration cycle was used" (Observations)
   - assumption: 3C279 flux 17 Jy with 15% uncertainty  
  > "We derive a flux density of 17 Jy for the complex gain calibrator, 3C279" (Observations)
   - fitting: _not stated_
   - validation: Flux scale checked against earlier full-calibration observations of 14 Jan 2012  
  > "these observations were used to verify the flux scale of the data presented here." (Observations)
2. **Make continuum map and measure continuum flux densities**: Image last three spectral windows; Gaussian fitting in image plane  
  > "Gaussian fitting of the continuum emission in the image plane suggests that neither of these sources is resolved." (Results and analysis)
   - software: CASA
   - fitting: Image-plane Gaussian fits  
  > "Gaussian fitting of the continuum emission in the image plane" (Results and analysis)
   - validation: Total 43 mJy agrees with SCUBA 850 um 42 mJy  
  > "in excellent agreement with the previous $\sim$14$''$ resolution 850 $\mu$m SCUBA observations" (Results and analysis)
3. **Extract [CII] spectra and fit Gaussians**: Spectra extracted at continuum peak positions from continuum-subtracted cubes; Gaussian fits for z, FWHM and integrated flux  
  > "From the spectral line data cubes we extract spectra at the positions of peak intensity in the submm image." (Results and analysis)
   - software: CASA
   - fitting: Gaussian line profile fit  
  > "We fit Gaussian line profiles to the two detected [CII] lines and the results are given in Table 1." (Results and analysis)
   - validation: Compared with CO line widths and SMA [CII] of Iono et al.  
  > "The [CII] linewidth and redshift of BR1202-0725 North are in agreement with the previous SMA observations of Iono et al. (2006)." (Results and analysis)
4. **Derive L_FIR and L_[CII]/L_FIR**: Adopt Iono et al. L_FIR for North and South, checked with greybody scaling; SW scaled by flux density ratio; compute L_[CII] from line flux  
  > "we scale down the luminosities of the two bright sources by the ratio of the flux densities, implying $L_{\rm FIR} \sim 10^{12}$ L$_{\odot}$" (Results and analysis)
   - assumption: beta = 1.5; dust T = 35 K (SMG), 60 K (quasar); cosmology (0.73, 0.27, 0.71)  
  > "assuming $\beta = 1.5$ with dust temperatures of 35 K for the SMG (e.g. Kovacs et al. 2006) and 60 K for the quasar" (Results and analysis)
   - fitting: _not stated_
   - validation: Reproduces combined 350 um flux density of the pair  
  > "simultaneously reproduce the combined 350 $\mu$m flux density of the pair (Benford et al. 1999)" (Results and analysis)

## Software

- **CASA** : Data analysis  
  > "Data analyis was performed using the *CASA* software package" (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| L_[CII] North | 10.0 | 1.5 | 1e9 Lsun | 4 | / BR1202-0725 North / 18.8$\pm$2.8 / 4.6906 / 722$\pm$12 / 14.7$\pm$2.2 / 10.0$\pm$1.5 / $8.3\pm1.2$ / |
| L_[CII] South | 6.5 | 1.0 | 1e9 Lsun | 4 | / BR1202-0725 South / 18.0$\pm$2.7 / 4.6943 / 328$\pm$6 / 9.6$\pm$1.5 / 6.5$\pm$1.0 / $2.5\pm0.4$ / |
| L_[CII]/L_FIR North | 8.3e-4 | 1.2e-4 | dimensionless | 4 | $L_{\rm [CII]}/L_{\rm FIR} = (8.3\pm 1.2)\times 10^{-4}$ for the starburst SMG to the North |
| L_[CII]/L_FIR South | 2.5e-4 | 0.4e-4 | dimensionless | 4 | $L_{\rm [CII]}/L_{\rm FIR} = (2.5\pm 0.4)\times 10^{-4}$ for the quasar host galaxy |
| S_340GHz North / South / SW | 18.8 / 18.0 / 1.9 | 2.8 / 2.7 / 0.3 | mJy | 2 | / BR1202-0725 SW / 1.9$\pm$0.3 / \- / \- / \- / \- / \- / |
| [CII] FWHM North / South | 722 / 328 | 12 / 6 | km/s | 3 | / BR1202-0725 North / 18.8$\pm$2.8 / 4.6906 / 722$\pm$12 / 14.7$\pm$2.2 / 10.0$\pm$1.5 / $8.3\pm1.2$ / |
| Total 340 GHz flux density | 43 | 6 | mJy | 2 | The total 340 GHz flux density of the system is $43\pm 6$ mJy (including calibration uncertainties) |

## Qualitative findings

- Tentative broad positive-velocity [CII] wing in the quasar, possibly a single-sided outflow  
  > "however a low intensity, broad line width extension is seen toward positive velocities." (Discussion)

## Claim tuples

- H: Is [CII]/FIR lower in the quasar host than in the starburst SMG? | E: Measure [CII] and 340 GHz continuum in both components and combine with L_FIR | R: Ratios 8.3e-4 (SMG) and 2.5e-4 (quasar) | F: Consistent with lower ratios in quasars than starbursts | **supported**
- H: Is there an overdensity of massive IR-luminous galaxies around BR1202-0725? | E: Continuum detection of a third source and comparison with SMG number density | R: Two SMG-like galaxies within 25 kpc; faint third source detected | F: Significant overdensity at z=4.7 | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Lack of Tsys and WVR in the data adds 15% flux uncertainty; SW redshift unknown; outflow needs higher resolution  
  > "Some uncertainty in the flux density of 3C279 is present due to the lack of system temperature measurements with these data." (Observations)
- Caveat (inferred, ours): L_FIR mostly adopted from literature with assumed dust temperatures
- Caveat (inferred, ours): Single 25-minute SV dataset without Tsys/WVR
- Caveat (inferred, ours): Overdensity claim rests on SW source with unknown redshift

## Reproducibility

- Data public (paper): Science verification data cited via ADS/JAO.ALMA#2011.0.00006.SV  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00006.SV." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Line-free channel selection
- Missing: Details of the missing-Tsys calibration handling
- Missing: L_FIR computation details
- Data volume (inferred): ~ few GB (single 25 min SV execution)
- Score (inferred): 3/5, Public SV data and simple analysis, but imaging and calibration details are sparse and the data lack Tsys/WVR.
- Rediscovery candidate: no, Recipe lacks key imaging and calibration details and the data have nonstandard calibration.

## Links

- Companion: Iono et al. (2006) (Previous SMA continuum/[CII] observations and FIR luminosities)
- Related: ALMA Science Verification

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 43,
  "rate": 0.642
 },
 "evidence_ok": true
}
```

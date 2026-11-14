# Searching for the 380 GHz H<SUB>2</SUB>O emission from the high-z lensed quasi-stellar object MG J0414+0534

`2019PASJ...71...57K` | Publications of the Astronomical Society of Japan 2019 | first author: Kuo, Cheng-Yu | arXiv: 1901.04745 | DOI: 10.1093/pasj/psz032

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: Can the 380 GHz (and 336 GHz) H2O maser/line emission be detected from the lensed QSO MG J0414+0534 at z=2.639, and what does its flux ratio anomaly imply about its origin?  
  > "In this work, we aim to search for the submillimeter water maser emissions from the lensed quasar MG J0414+0532 with the Atacama Large Millimeter/submillimeter Array (ALMA)." (Introduction)
- Target **MG J0414+0534**: coordinates 04h14m37.7699s, +05d34m42.407s (ICRS, phase center)  
  > "The phase center was $\alpha$ = 04$^{\rm h}$14$^{\rm m}$37$^{\rm s}$.7699, $\delta$ = $+$05$^{\circ}$34$^{\prime}$42$^{\prime\prime}\mkern-1.2mu$.407 (ICRS)." (2.2 ALMA Observations); "Using the luminosity distance of 22197 Mpc for MG J0414$+$0534" (3.1 Continuum Emissions); z/distance z = 2.639; luminosity distance 22197 Mpc  
  > "The phase center was $\alpha$ = 04$^{\rm h}$14$^{\rm m}$37$^{\rm s}$.7699, $\delta$ = $+$05$^{\circ}$34$^{\prime}$42$^{\prime\prime}\mkern-1.2mu$.407 (ICRS)." (2.2 ALMA Observations); "Using the luminosity distance of 22197 Mpc for MG J0414$+$0534" (3.1 Continuum Emissions); distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.00316.S
- bands: Band 3  
  > "The observations of MG J0414+0534 were conducted with ALMA at Band 3 with four execution blocks" (2.2 ALMA Observations)
- frequencies and spectral setup: 4 spws centered 92.396, 93.977, 104.479, 106.081 GHz; spw 27 and 25 0.938 GHz with 1920 channels; spw 23 and 19 2 GHz with 128 channels  
  > "Spw 27 and 25 have a bandwidth of 0.938 GHz with 1920 channels within each band." (2.2 ALMA Observations); "Spw 23 and 19 have a bandwidth of 2 GHz with 128 channels in each band." (2.2 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: 45 antennas in first three executions, 44 in last  
  > "The number of antenna involved in the observations is 45 in the first three executions and 44 in the last execution." (2.2 ALMA Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: continuum 0.35x0.22 arcsec; line 0.64x0.38 arcsec  
  > "The resulting size of the synthesis beam is 0$^{\prime\prime}\mkern-1.2mu$.64$\times$0$^{\prime\prime}\mkern-1.2mu$.38, with PA of $-$61$^{\circ}$." (2.3 Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: continuum 1sigma 0.036 mJy; line 0.45 mJy per 0.97708 MHz channel  
  > "The 1$\sigma$ noise per 0.97708 MHz channel is 0.45 mJy." (2.3 Data Reduction)
- time on source: total observing time incl. calibration and overheads 3.96 hours  
  > "The total observing time including calibration and overheads is 3.96 hours." (2.2 ALMA Observations)
- observing dates: 2017 December 13-18, four execution blocks  
  > "four execution blocks taken between 2017 December 13 and 2017 December 18" (2.2 ALMA Observations)
- pi or archival as stated: _not stated_
- Line: H2O 380 GHz maser line (380.19737 GHz)
- Line: H2O 336 GHz line (336.22794 GHz)
- External data: Magnification factors (13.1 for A1; 27.9 total for A1+A2)  
  > "a magnification factor of 13.1 for the A1 component (see the supplementary information provided by Implellizzeri et al. 2008)" (3.1 Continuum Emissions) [from Impellizzeri et al. 2008]
- External data: Lens galaxy G and object X positions from CASTLES  
  > "The positions of the gravitational lenses G and X taken from the CASTLES survey" (Table 1) [from CASTLES survey]

## Processing

### Calibration

- pipeline or manual: CASA; flagging then amplitude/bandpass with J0423-0120, phase with J0427+0457  
  > "the amplitude and bandpass calibrations of the visibility data were carried out with the calibrator J0423$-$0120." (2.3 Data Reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: phase-only on all four spws  
  > "we performed self-calibration (phase-only) on the visibility data for all four spectral windows" (2.3 Data Reduction)

### Imaging

- task: CASA tclean; uvcontsub for continuum subtraction  
  > "we conduct continuum and spectral-line imaging with the CASA task $TCLEAN$." (2.3 Data Reduction)
- deconvolver: _not stated_
- weighting robust: uniform for continuum; natural for line  
  > "we adopt natural weighting for the spectral line imaging to achieve the highest sensitivity for detection." (2.3 Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: spw 25: 104.02-104.20 and 104.75-104.95 GHz; spw 27: 91.95-92.15 and 92.65-92.85 GHz  
  > "using channels with frequencies ranging from 104.02$\sim$104.20 GHz and 104.75$\sim$104.95 GHz as the baseline channels." (2.3 Data Reduction)
- primary beam correction: not applied  
  > "we do not perform primary beam correction for our images" (2.3 Data Reduction)
- array combination: _not stated_
- smoothing: Hanning smoothing over 7 channels for spectrum  
  > "after Hanning smoothing over 7 channels is 0.30 mJy" (3.2.2 The Line Spectra)
- final beam: continuum 0.35x0.22 arcsec PA -67 deg  
  > "The resulting synthesis beam is 0$^{\prime\prime}\mkern-1.2mu$.35$\times$0$^{\prime\prime}\mkern-1.2mu$.22" (2.3 Data Reduction)
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- tclean cell size, image size, niter/threshold, masks
- CASA version
- Flux scale of calibrators and flux uncertainty
- Self-calibration solution intervals and reference antenna
- Lens model optimizer/sampler details and priors widths
- Positions and magnifications of hypothetical maser clumps
- Spectral-line cube channel width/velocity frame for moment 0

## Analysis recipe

1. **Measure continuum positions, fluxes and spectral index**: Fit elliptical Gaussians to the four lensed spots in uniform-weighted continuum images; fit power law f=f0 nu^alpha  
  > "we fit elliptical Gaussians to these spots." (3.1 Continuum Emissions)
   - software: CASA
   - fitting: _not stated_
   - validation: Positions compared with 22 GHz VLA positions  
  > "These positions are consistent with those measured at 22 GHz by Katz, Moore, & Hewitt (1997) with the VLA." (3.1 Continuum Emissions)
2. **Detect and characterize 380 GHz line**: Continuum-subtract in uv, make MOM0 map between 104.2 and 104.75 GHz, extract spectrum from A1+A2, Gaussian fit  
  > "we integrate the data cube (with continuum removed) along the frequency axis between 104.2 GHz and 104.75 GHz" (3.2.1 The Integrated Intensity Map)
   - software: CASA
   - fitting: Gaussian profile fit to spectrum  
  > "By fitting a Gaussian profile to the spectrum, we obtained a full width at half maximum (FWHM) of $\sim$290 km s$^{-1}$" (3.2.2 The Line Spectra)
   - validation: Argued against residual bandpass via A1/A2 flux ratio, bandpass solutions, and phase calibrator spectra  
  > "by examining the bandpass solutions for different antennas from the calibration process, we do not see a characteristic bandpass shape as seen in Figure 2" (4 Discussion)
3. **Lens modelling to explain flux ratio anomaly**: SIE(G)+SIS(X)+external shear fit to four image positions and A1, A2 continuum fluxes; multi-clump source model for line  
  > "Our model of SIE(G)+SIS(X)+shear for the system fits well to the observed images and fluxes, with a reduced $\chi^2$ of 1.0." (4.2 Lens Modeling)
   - software: Glee
   - fitting: Priors on G and X centroids from observed light; uniform priors on other parameters  
  > "We adopt a prior on the centroids of G and X based on the observed light distribution (listed in Table 1), and uniform prior on the other parameters." (4.2 Lens Modeling)
   - validation: _not stated_

## Software

- **CASA** : calibration, tclean imaging, uvcontsub  
  > "We performed data reduction of the ALMA data with the Common Astronomy Software Application Package (CASA; McMullin et al. 2007)." (2.3 Data Reduction)
- **Glee** : gravitational lens modeling  
  > "We model the lens system with Glee, a lensing software developed by A. Halkola and S. H. Suyu" (4.2 Lens Modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum spectral index | -1.51 | 0.02 | dimensionless | 1 | Averaging these measurements gives a best estimate of $\alpha$ $=$ $-$1.51$\pm$0.02. |
| 380 GHz line FWHM | ~290 | not stated | km/s | 2 | we obtained a full width at half maximum (FWHM) of $\sim$290 km s$^{-1}$ (with relativistic correction) |
| 380 GHz line peak flux | ~0.8 | not stated | mJy | 2 | a peak flux of $\sim$0.8 mJy |
| Line isotropic luminosity | ~5400000 | not stated | Lsun | 2 | we get a total isotropic (unlensed) luminosity $L_{\rm H_{2}O}$(380 GHz) of $\sim$5400000 $L_{\odot}$ |
| A2/A1 flux ratio, line vs continuum | 1.2 (line) vs 0.8 (continuum) | not stated | dimensionless | 2 | the flux ratio between the A1 and A2 line component (A2/A1 $=$ 1.2) is different from what we see in the continuum image (A2/A1 $=$ 0.8) |
| 336 GHz line 3-sigma upper limit | 1.0 | not stated | mJy | 2 | we can place a 3-$\sigma$ upper limit of the 336 GHz line to be 1.0 mJy |
| Lower-limit SFR if SNe explain continuum | ~10^9 | not stated | Msun/yr | 0 | the inferred lower limit of the starformation rate is $\sim$10$^{9}$ $M_{\odot}$ yr$^{-1}$ |

## Qualitative findings

- Continuum is likely jet synchrotron; supernovae cannot account for it  
  > "we can conclude that SNe cannot account for the majority of the observed radio emission from MG J0414$+$0534" (3.1 Continuum Emissions)

## Claim tuples

- H: The 380 GHz H2O line is detectable from MG J0414+0534 | E: Band 3 ALMA spectral line imaging of spw 25 | R: Weak 2-3 sigma broad features, MOM0 emission at A1 and A2 | F: Tentative detection of 380 GHz line | **partially**
- H: 336 GHz line detectable | E: spw 27 spectrum | R: no detection, 3 sigma limit 1.0 mJy | F: Non-detection | **supported**
- H: Line flux ratio anomaly arises from spatially displaced emitting regions | E: SIE+SIS+shear lens model with multiple source clumps | R: Clumps ~1.5 kpc displaced produce images only in A2 | F: Line emission from two or three locations | **partially**

## Reasoning

- Why this data: 380 GHz back-bone maser line predicted brighter than 22 GHz and redshifted into ALMA Band 3  
  > "the strength of the 380 GHz maser line can be brighter than the 22 GHz one by a factor of 10$-$1000" (2.1 Line Selection)
- Why this method: _not stated_
- Alternative: Residual bandpass continuum rejected as origin of broad profile  
  > "the residual bandpass should be negligible after averaging the entire dataset" (4 Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Detection is tentative and low S/N; line may be partly thermal  
  > "we want to emphasize that our current detection is still tentative." (4 Discussion)
- Caveat (inferred, ours): Detection at 2-3 sigma; baseline channels were changed after seeing the data, risking continuum-subtraction artifacts
- Caveat (inferred, ours): Lens model with free source clumps is unconstrained by the data
- Caveat (inferred, ours): Bandwidth of ~1 GHz barely exceeds line width

## Reproducibility

- Data public (paper): ALMA project data acknowledged but public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.0.00316.S." (Acknowledgement)
- Products in archive: _not stated_
- Missing: tclean parameters
- Missing: CASA version
- Missing: lens model parameter table values for clumps
- Data volume (inferred): ~50-100 GB raw
- Score (inferred): 3/5, Calibrators, channel ranges and weighting given, but imaging parameters and lens fit details are missing.
- Rediscovery candidate: no, Tentative low-S/N result with incomplete imaging recipe.

## Links

- Method: Gray et al. 2016 (Maser line strength predictions)
- Companion: Impellizzeri et al. 2008 (22 GHz maser discovery and lensing magnifications)
- Related: CASTLES

## Checks

```json
{
 "quotes": 51,
 "quotes_ok": 51,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2017.0.00316.S"
 ],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 59,
  "stated": 34,
  "rate": 0.576
 },
 "evidence_ok": true
}
```

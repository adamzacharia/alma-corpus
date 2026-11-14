# An Active Galactic Nucleus in the Antennae Galaxies?

`2026ApJ..1004..126K` | The Astrophysical Journal 2026 | first author: Komugi, Shinya | arXiv: 2605.21879 | DOI: 10.3847/1538-4357/ae707d

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: Does the Antennae merger host an AGN, as revealed by 100 GHz time variability of compact sources S3 and S4 in NGC 4039?  
  > "We examine the time variability of these two sources using their power spectrum." (abstract)
- Target **Antennae galaxies (NGC 4038/4039), sources S3 and S4**: coordinates S3: 12:01:53.555 -18:53:09.22; S4: 12:01:53.516 -18:53:10.20  
  > "The Antennae galaxies (NGC 4038/4039) lie at a distance of 22 Mpc (cite: Schweizer08)" (1 Introduction); "| S4 | 12:01:53.516 | -18:53:10.20 | 0.5 | $0.157\pm 0.014$ | Point source |" (Table 1); z/distance 22 Mpc  
  > "The Antennae galaxies (NGC 4038/4039) lie at a distance of 22 Mpc (cite: Schweizer08)" (1 Introduction); "| S4 | 12:01:53.516 | -18:53:10.20 | 0.5 | $0.157\pm 0.014$ | Point source |" (Table 1); distance from Schweizer08  
  > "The Antennae galaxies (NGC 4038/4039) lie at a distance of 22 Mpc (cite: Schweizer08)" (1 Introduction); "| S4 | 12:01:53.516 | -18:53:10.20 | 0.5 | $0.157\pm 0.014$ | Point source |" (Table 1)

## Data provenance

- ALMA projects: 2022.A.00032.S
- bands: Band 3 (~100 GHz)  
  > "under good weather conditions for Band 3" (2 Observations and Data Processing)
- frequencies and spectral setup: 4 spws of 1.875 GHz at 114.64195, 112.77718, 102.63664, 100.77188 GHz  
  > "The central frequency of each spw is tuned to 114.64195 GHz, 112.77718 GHz, 102.63664 GHz, and 100.77188 GHz" (2 Observations and Data Processing)
- continuum bandwidth: _not stated_
- arrays: ALMA 12m array  
  > "The data were obtained at the ALMA 12m array" (2 Observations and Data Processing)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: combined 0.10x0.087 arcsec; uniform 0.045x0.039 arcsec  
  > "The resulting beam size was $0^{\prime \prime}.045\times 0^{\prime \prime}.039$" (2.2 uniform image)
- max recoverable scale: 1.06-3.35 arcsec across EBs  
  > "the maximum recoverable scale (MRS) of the observations is larger than the aperture" (2.5 Photometry)
- sensitivity: combined rms 2.1 uJy; uniform 17 uJy  
  > "The r.m.s. noise level was $2.1~\mathrm{\mu Jy}$." (2.1 combined image)
- time on source: 40.3 hours total  
  > "resulting in a total on-source time of 40.3 hours" (2 Observations and Data Processing)
- observing dates: 2023 Sep 5 to Nov 23, 52 EBs  
  > "The observations were conducted between 2023 September 5th and November 23rd" (2 Observations and Data Processing)
- pi or archival as stated: _not stated_
- Line: 12CO J=1-0 (not stated)
- Other facility **JWST NIRCam/MIRI**: 1.15, 3.35, 7.70 um images  
  > "JWST NIRCAM and MIRI images at $1.15~\mathrm{\mu m}$, $3.35~\mathrm{\mu m}$ and $7.70~\mathrm{\mu m}$" (2.6 Ancillary Data)
- Other facility **VLA**: 4 and 6 cm fluxes of S3/S4 from literature  
  > "Low resolution ($\sim 1^{\prime \prime}$) observations (cite: Neff2000) at 4 cm and 6 cm detected sources" (3.3)
- External data: VLA 4 and 6 cm fluxes of S3 and S4  
  > "In Table 5 of (cite: Neff2000), the coordinates of the first and second row of Region 1:2 correspond to S4 and S3" (3.3) [from Neff2000]
- External data: Positions of S1-S9 and earlier ALMA fluxes  
  > "known sources S1a, S1b, S2, S3, S4 and S7 (cite: He2022)" (2.2 uniform image) [from He2022]
- External data: Chandra ULX #29 position and LX  
  > "The X-ray (0.1-10 keV) luminosity of this source is $L_X = 10^{39.57}\ \mathrm{erg\ s^{-1}}$ (cite: Poutanen2013)" (4.1) [from Poutanen2013]

## Processing

### Calibration

- pipeline or manual: Calibrated MS provided by observatory  
  > "The calibrated data (Measurement Sets) were provided by the observatory, and imaged using CASA version 6.5.2–26." (2 Observations and Data Processing)
- casa version: CASA 6.5.2-26  
  > "imaged using CASA version 6.5.2–26" (2 Observations and Data Processing)
- pipeline version: _not stated_
- archive products used as is: observatory-calibrated data and QA2 clean masks  
  > "We used clean masks provided by the observatory as part of the QA2 assessment" (2.1 combined image)
- flux calibrator: _not stated_
- flux scale uncertainty: 5% adopted  
  > "we apply a conservative absolute flux uncertainty of $5\%$ for the analyses presented in this paper" (2.4 Flux Calibration)
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "The images were created by using the CASA task *tclean* with *weighting=uniform*" (2.2 uniform image)
- deconvolver: _not stated_
- weighting robust: Briggs robust=0.5 (combined, individual); uniform for uniform image  
  > "Imaging was done with the Briggs weighting (robust parameter=0.5)" (2.1 combined image)
- uv taper: _not stated_
- cell size: 1/3 of synthesized beam (individual images)  
  > "The pixel size of each image was set to be $\frac{1}{3}$ of the synthesized beam size." (2.3 individual image)
- image size: _not stated_
- masking: QA2 auto-mask for combined; 0.1 arcsec circles on sources for uniform  
  > "user defined masks that were centered on known sources S1a, S1b, S2, S3, S4 and S7" (2.2 uniform image)
- multiscale scales: _not stated_
- continuum subtraction: detected emission lines masked, all spws used  
  > "All spws were used, with any detected emission lines masked out." (2.1 combined image)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.10x0.087 arcsec PA -75.6 (combined)  
  > "a beam size of $0^{\prime \prime}.10\times 0^{\prime \prime}.087$ with a position angle of $-75.6$ deg." (2.1 combined image)
- final rms: 2.1 uJy combined; 17 uJy uniform  
  > "Cleaning was stopped at 1$\times$ the r.m.s. noise level of $17~\mathrm{\mu Jy}$." (2.2 uniform image)

### Inherited from earlier work

- CO image made with PHANGS-ALMA pipeline  
  > "we show the CO emission image created using the PHANGS-ALMA pipeline (cite: Leroy21)" (2 Observations and Data Processing) [from Leroy21]
- Source definitions S1-S9  
  > "Sources S1 to S9 from (cite: He2022) overlap with the images presented here." (3.1) [from He2022]

### Not stated but needed to reproduce (our reading)

- Line-free channel/line mask definitions
- tclean niter, image size, scales
- Power-spectrum/Fourier algorithm and normalization details
- Photometry code used
- CO imaging parameters (Saito et al., in prep)
- Self-calibration not mentioned

## Analysis recipe

1. **Image continuum**: tclean combined, uniform and per-EB images  
  > "we imaged all EBs separately to search for time variability." (2.3 individual image)
   - software: CASA
   - parameter: robust 0.5; per-EB cleaned to 1 rms  
  > "cleaned down to the 1$\times$ r.m.s. noise level" (2.3 individual image)
   - fitting: _not stated_
   - validation: _not stated_
2. **Check flux calibration stability**: uvmodelfit point source fit to phase calibrator per EB  
  > "we fit the visibility of the phase calibrator with a point source model for each EB using CASA task *uvmodelfit*" (2.4 Flux Calibration)
   - software: CASA
   - fitting: _not stated_
   - validation: F100/F112 stable within 1%  
  > "is stable to within $1\%$" (2.4 Flux Calibration)
3. **Aperture photometry**: fixed 0.5 arcsec aperture in per-EB images; error = noise x sqrt(N beams) plus 5% in quadrature  
  > "we choose an aperture diameter of $0^{\prime \prime}.5$ throughout all executions to measure the flux in individual images" (2.5 Photometry)
   - fitting: _not stated_
   - validation: _not stated_
4. **Size and spectral index**: 2D Gaussian fits in uniform image; per-spw fluxes; cm-mm slope with VLA  
  > "A two-dimensional Gaussian fit to the uniform image of S4 gives a FWHM" (3.2)
   - assumption: spectral index does not change with time  
  > "under the assumption that the spectral index does not change with time" (3.3)
   - fitting: _not stated_
   - validation: _not stated_
5. **Power spectrum of light curves**: Fourier transform of normalized fluxes; bootstrap 1000 realizations; compared with constant-flux simulation and beam-size power spectrum  
  > "Such realizations of the light curve and power spectrum were created 1000 times." (3.4)
   - parameter: frequency resolution ~3 days  
  > "The frequency resolution ($\sim 3$ days) was determined by the average of the time between epochs." (3.4)
   - assumption: normally distributed per-EB errors  
  > "assuming that the uncertainty at each EB is normally distributed" (3.4)
   - fitting: _not stated_
   - validation: peaks coincident with beam-size peaks rejected as systematics  
  > "we regard that flux correlated with the beam is a sign of systematics in the observation." (3.4)
6. **Assess emission origin**: compare luminosity, brightness temperature, spectral slope with dust, free-free, SNR, microquasar, AGN mm-X-ray relation  
  > "We finally assess whether S3 and S4 are consistent with an AGN." (4.2)
   - assumption: dust kappa 0.37 m2/kg at 250um, beta=2, T=30 K; Galactic CO-to-H2 2e20  
  > "dust emissivity index of 2, and a dust temperature of 30 K" (4.2)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 6.5.2-26: imaging, uvmodelfit  
  > "imaged using CASA version 6.5.2–26" (2 Observations and Data Processing)
- **PHANGS-ALMA pipeline** : CO image  
  > "CO emission image created using the PHANGS-ALMA pipeline (cite: Leroy21)" (2 Observations and Data Processing)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| S4 variability timescale | 13 | ±3 | days | 5 | We find a notable peak at $0.074\ \mathrm{day^{-1}}$ ($13\pm 3$ days) |
| S4 peak significance | 5.6 | not stated | dimensionless | 5 | The peak deviates from the source with constant flux by $\rm{SN}=5.6$ |
| S3 3 mm flux | 0.153 | 0.013 | mJy | 3 | $0.153\pm 0.013$ |
| S4 3 mm flux | 0.157 | 0.014 | mJy | 3 | $0.157\pm 0.014$ |
| cm-mm slope S4 | -0.33 | 0.04 | dimensionless | 4 | $\alpha^{\mathrm{cm-mm}}_\mathrm{S4}\sim -0.33\pm 0.04$ |
| S4 100 GHz luminosity | 9.1e36 | not stated | erg/s | 6 | $8.8\times 10^{36}\ \mathrm{erg\ s^{-1}}$ and $9.1\times 10^{36}\ \mathrm{erg\ s^{-1}}$ for S3 and S4 |
| S4 brightness temperature lower limit (size<0.01 pc) | 1.3e6 | not stated | K | 6 | we obtain a lower limit for the brightness temperature of $1.3\times 10^6\ \mathrm{K}$ |
| S4 uniform-image flux | 117 | 34 | uJy | 4 | a flux of $117\pm 34~\mathrm{\mu Jy}$ |

## Qualitative findings

- Most 100 GHz sources are extended and tied to star-forming regions; S3 and S4 are compact.  
  > "Most 100 GHz detections in the Antennae are spatially extended and associated with star forming regions" (abstract)

## Claim tuples

- H: S4 is time variable at 100 GHz | E: Power spectrum of 52-epoch light curve with bootstrap and beam-size check | R: Peak at 13±3 days, SN=5.6 | F: Emitting region <0.01 pc | **supported**
- H: S3 is variable | E: Same power spectrum analysis | R: No robust peaks | F: S3 not variable; YMC or AGN possible | **supported**
- H: S4 is an AGN | E: Compare luminosity, Tb, variability, X-ray with candidate origins | R: Excludes dust, SNR, XRB, YMC; hard X-ray non-detection | F: S4 is a strong AGN candidate, possibly Compton-thick | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Free-free/YMC, dust, SNR, microquasar origins rejected for S4  
  > "we cannot attribute the millimeter flux of S3 or S4 to X-ray binary systems." (4.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Spectral shape uncertain with narrow frequency range and large errors  
  > "the large flux uncertainties do not allow for any robust conclusions regarding the SED" (Conclusion)
- Caveat (inferred, ours): Power spectrum on uneven, noisy sampling; 13 d peak may be affected by beam-size systematics
- Caveat (inferred, ours): Photometric noise ~28% per epoch
- Caveat (inferred, ours): AGN claim rests on indirect arguments
- Caveat (inferred, ours): No pipeline code released

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Observatory-calibrated MS provided  
  > "The calibrated data (Measurement Sets) were provided by the observatory" (2 Observations and Data Processing)
- Missing: Power spectrum code and normalization
- Missing: Mask files, niter, image size
- Missing: Exact photometry procedure
- Data volume (inferred): Large: 52 EBs, several TB raw
- Score (inferred): 3/5, Data public and recipe fairly clear, but power spectrum and photometry details are thin and the data volume is large.
- Rediscovery candidate: no, Large dataset and incomplete variability-analysis details.

## Links

- Method: Leroy21 (PHANGS-ALMA pipeline)
- Companion: He2022 (Earlier ALMA study of Antennae clusters, source definitions)
- Companion: Saito et al., in preparation (CO emission details)
- Related: ALMA Cycle 9 observatory filler project

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
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 49,
  "rate": 0.628
 },
 "evidence_ok": true
}
```

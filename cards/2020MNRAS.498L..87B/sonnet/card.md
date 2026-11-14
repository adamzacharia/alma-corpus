# FAUST I. The hot corino at the heart of the prototypical Class I protostar L1551 IRS5

`2020MNRAS.498L..87B` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Bianchi, E. | arXiv: 2007.10275 | DOI: 10.1093/mnrasl/slaa130

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: astrochemistry, star_formation
- Question: Does the Class I protostar L1551 IRS5 host a hot corino, and how do its iCOM abundances compare with Class 0 hot corinos?  
  > "This study focuses on iCOM lines and aims at discovering and studying its hot corino(s)." (Introduction)
- Target **L1551 IRS5**: coordinates RA 04h31m34.14s, Dec +18d08m05.10s (J2000)  
  > "L1551 IRS5 is located in Taurus (cite: Strom1976) at a distance of (141$\pm$7) pc (cite: Zucker2019)" (The L1551 IRS5 source); "The observations were centered at $\alpha_{\rm J2000}$ = 04$^{\rm h}$ 31$^{\rm m}$ 34.14s, $\delta_{\rm J2000}$ = +18$\ensuremath{^\circ}$ 08$\ensuremath{'}$ 05.10$''$." (Observations); z/distance 141±7 pc  
  > "L1551 IRS5 is located in Taurus (cite: Strom1976) at a distance of (141$\pm$7) pc (cite: Zucker2019)" (The L1551 IRS5 source); "The observations were centered at $\alpha_{\rm J2000}$ = 04$^{\rm h}$ 31$^{\rm m}$ 34.14s, $\delta_{\rm J2000}$ = +18$\ensuremath{^\circ}$ 08$\ensuremath{'}$ 05.10$''$." (Observations); distance from Zucker2019  
  > "L1551 IRS5 is located in Taurus (cite: Strom1976) at a distance of (141$\pm$7) pc (cite: Zucker2019)" (The L1551 IRS5 source); "The observations were centered at $\alpha_{\rm J2000}$ = 04$^{\rm h}$ 31$^{\rm m}$ 34.14s, $\delta_{\rm J2000}$ = +18$\ensuremath{^\circ}$ 08$\ensuremath{'}$ 05.10$''$." (Observations)

## Data provenance

- ALMA projects: 2018.1.01205.L
- bands: _not stated_
- frequencies and spectral setup: Analysed spectral window 232.8–234.7 GHz, 488 kHz channels (0.63 km/s)  
  > "The analysed spectral window (232.8–234.7 GHz) was observed using spectral channels of 488 kHz (0.63 km s$^{-1}$)." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-5  
  > "The data here exploited were acquired on 2018 October 25 using the C43-5 antenna configuration, with baselines between 15 m and 1.4 km." (Observations)
- baselines: 15 m to 1.4 km  
  > "using the C43-5 antenna configuration, with baselines between 15 m and 1.4 km." (Observations)
- angular resolution: 0.37″×0.31″ (PA=39°)  
  > "has a synthesized beam of 0.37$''$$\times$0.31$''$ (PA=39$^{\circ}$)" (Observations)
- max recoverable scale: _not stated_
- sensitivity: 1 mJy/beam rms in a 0.6 km/s channel  
  > "an r.m.s. noise of 1 mJy beam$^{-1}$ in an 0.6 km s$^{-1}$ channel, as expected" (Observations)
- time on source: _not stated_
- observing dates: 2018 October 25  
  > "The data here exploited were acquired on 2018 October 25" (Observations)
- pi or archival as stated: FAUST Large Program data  
  > "L1551 IRS5 was observed with ALMA (FAUST Large Program 2018.1.01205.L)." (Observations)
- Line: CH3OH 5(4,2)–6(3,3) E etc. (234.6985 GHz)
- Line: 13CH3OH 5(1,5)–4(1,4) A (234.0116 GHz)
- External data: CH3OH-A/E collisional coefficients with para-H2  
  > "We used the collisional coefficients of CH$_{\rm 3}$OH-A and CH$_{\rm 3}$OH-E with para-H$_{\rm 2}$ computed between 10 and 200 K for the first 256 levels of each species (cite: Rabli2010)" (Column densities and physical parameters) [from (cite: Rabli2010), BASECOL (cite: Dubernet2013)]
- External data: 12C/13C ratio of 60  
  > "a $^{12}$C/$^{13}$C ratio equal to 60 (cite: Milam2005)" (Column densities and physical parameters) [from (cite: Milam2005)]
- External data: Distance 141±7 pc  
  > "at a distance of (141$\pm$7) pc (cite: Zucker2019)" (The L1551 IRS5 source) [from (cite: Zucker2019)]

## Processing

### Calibration

- pipeline or manual: ALMA calibration pipeline within CASA plus extra Tsys and spectral normalization routine  
  > "The data were calibrated using the ALMA calibration pipeline within CASA (cite: McMullin2007) and we included an additional calibration routine to correct for the T$_{\rm sys}$ and spectral data normalization" (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0423-0120 (bandpass and flux); J0510+1800 phase  
  > "The quasar J0423-0120 was used as bandpass and flux calibrator, J0510+1800 as phase calibrator." (Observations)
- flux scale uncertainty: 10% (plus 10% baseline error)  
  > "We estimate the absolute flux calibration uncertainty of 10% and an additional error of 10% for the spectra baseline determination." (Observations)
- self calibration: Self-calibrated on line-free continuum channels, including continuum spectral index corrections  
  > "The data were self-calibrated using carefully-determined line-free continuum channels, including corrections for the continuum spectral index" (Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.4  
  > "made using a Briggs robust parameter of 0.4" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum model subtracted from visibilities before imaging  
  > "the continuum model was then subtracted from the visibilities prior to imaging the line data" (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.37″×0.31″ (PA=39°)  
  > "has a synthesized beam of 0.37$''$$\times$0.31$''$ (PA=39$^{\circ}$)" (Observations)
- final rms: 1 mJy/beam per 0.6 km/s channel  
  > "an r.m.s. noise of 1 mJy beam$^{-1}$ in an 0.6 km s$^{-1}$ channel" (Observations)

### Inherited from earlier work

- Additional Tsys and spectral normalization calibration routine  
  > "https://help.almascience.org/index.php?/Knowledgebase/Article/View/419; Moellenbrock et al. (in preparation)." (Observations) [from Moellenbrock et al. (in preparation)]
- LVG code used for non-LTE analysis  
  > "via the Large Velocity Gradient (LVG) code by (cite: Ceccarelli2003)" (Column densities and physical parameters) [from (cite: Ceccarelli2003)]

### Not stated but needed to reproduce (our reading)

- Cell size, image size and imaging task parameters
- Line-free channels and self-calibration solution intervals
- Mask and deconvolution settings
- Rotational diagram fitting details and line widths for non-methanol species
- Spatial extraction regions and positions of P1-P8 beyond the figure

## Analysis recipe

1. **Calibrate, self-calibrate and image line cube**: ALMA pipeline in CASA, extra Tsys/normalization, self-cal on line-free continuum, continuum subtraction, imaging with robust 0.4  
  > "The resulting continuum-subtracted line-cube, made using a Briggs robust parameter of 0.4" (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Map continuum and line emission and extract spectra**: 2D Gaussian fit of continuum; moment 0 maps; spectra extracted in single pixels at positions P1-P8  
  > "The deconvolved source size, derived from a 2D Gaussian fit of the emission, is around 0.4$''$, similar to the beam size." (Results)
   - software: GILDAS
   - fitting: 2D Gaussian  
  > "derived from a 2D Gaussian fit of the emission" (Results)
   - validation: _not stated_
3. **Non-LTE LVG analysis of methanol**: Grid of >=10^4 LVG models fit simultaneously to CH3OH-A, CH3OH-E and 13CH3OH-A lines (Eup<200 K); free: N, nH2, Tkin, size  
  > "We found the solution with the lowest $\chi^2$ by simultaneously fitting the CH$_{\rm 3}$OH-A, CH$_{\rm 3}$OH-E and $^{13}$CH$_{\rm 3}$OH-A lines" (Column densities and physical parameters)
   - software: LVG code (Ceccarelli2003)
   - parameter: N 3e16–4e19 cm-2, nH2 3e6–2e8 cm-3, Tkin 80–180 K  
  > "an H$_{\rm 2}$ number density (n$_{\rm H_2}$) from 3$\times$10$^{6}$ to 2$\times$10$^{8}$ cm$^{-3}$, and a gas temperature (T$_{\rm kin}$) from 80 to 180 K" (Column densities and physical parameters)
   - assumption: Spherical geometry, A/E=1, 12C/13C=60, FWHM 3.5 km/s, collisional excitation only  
  > "We assumed a spherical geometry (cite: de_jong_hydrostatic_1980), a CH$_3$OH-A/CH$_3$OH-E ratio equal to 1" (Column densities and physical parameters)
   - fitting: chi2 minimization on grid  
  > "We found the solution with the lowest $\chi^2$" (Column densities and physical parameters)
   - validation: Results unchanged for FWHM 3.0 or 4.0 km/s  
  > "The results do not change if we assume a line FWHM of 3.0 or 4.0 km s$^{-1}$" (Column densities and physical parameters)
4. **Rotational diagram column densities of other iCOMs**: Rotational diagram with source size 0.15″; Trot=100 K assumed for HCOOCH3 and CH3CH2OH  
  > "we used the Rotational Diagram analysis to estimate their column densities, assuming a source size of 0.15$''$ as derived from the methanol analysis" (Column densities and physical parameters)
   - assumption: Trot = 100 K from methanol LVG for methyl formate and ethanol  
  > "we assumed a rotational temperature of 100 K, based on the methanol LVG analysis" (Column densities and physical parameters)
   - fitting: _not stated_
   - validation: Predicted opacities 0.3–0.5 (methyl formate) and ~0.2 (ethanol), so optically thin  
  > "the predicted opacity is around 0.3–0.5 for the methyl formate lines and $\sim$0.2 for the ethanol lines" (Column densities and physical parameters)

## Software

- **CASA** : Calibration pipeline and spectral line imaging  
  > "Spectral line imaging was performed with the CASA package, while the data analysis was performed using the IRAM-GILDAS package." (Observations)
- **GILDAS** : Data analysis  
  > "the data analysis was performed using the IRAM-GILDAS package" (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Gas temperature (methanol) | 100 | ±10 | K | 3 | The temperature is (100$\pm$10) K |
| H2 density | >=1.5e8 | 1σ lower limit | cm-3 | 3 | the density is $\geq1.5\times$10$^{8}$ cm$^{-3}$ at 1$\sigma$ confidence level |
| CH3OH-A column density (best fit) | 1e19 | >=0.5e19 within 1σ | cm-2 | 3 | The best fit is obtained with N$_{\rm CH_3OH-A}$ = 1$\times$10$^{19}$ cm$^{-2}$ and a size of 0.15$''$ (21 au). |
| Emitting size | 0.15 (21 au) | not stated | arcsec | 3 | a size of 0.15$''$ (21 au) |
| CH2DOH Trot | 88 | ±9 | K | 4 | we derive a rotational temperature of 88$\pm$9 K and a column density (64$\pm$11)$\times10^{16}$ cm$^{-2}$ |
| HCOOCH3 column density | 33e16 | ±2e16 | cm-2 | 4 | (33$\pm$2)$\times10^{16}$ and (149$\pm$13)$\times10^{15}$ cm$^{-2}$, for methyl formate and ethanol |
| CH3CH2OH column density | 149e15 | ±13e15 | cm-2 | 4 | (33$\pm$2)$\times10^{16}$ and (149$\pm$13)$\times10^{15}$ cm$^{-2}$, for methyl formate and ethanol |

## Qualitative findings

- Methanol lines are double-peaked toward N and S, suggesting a rotating inner envelope or disk  
  > "This velocity pattern, perpendicularly to the jet axis, could be due to either a rotating inner envelope or a disk." (Results)

## Claim tuples

- H: L1551 IRS5 hosts a hot corino | E: Detect iCOM lines and run non-LTE methanol analysis | R: T~100 K, n>=1.5e8 cm-3, size ~10 au radius, many iCOMs detected | F: IRS5 N is a hot corino; S possibly a second | **supported**
- H: Class I hot corinos chemically differ from Class 0 | E: Compare methyl formate and ethanol abundances relative to methanol | R: Abundances compatible with Class 0 and SVS13-A | F: Little chemical evolution from Class 0 to I | **supported**
- H: Methanol deuteration can be measured | E: Non-LTE analysis of CH3OH and 13CH3OH | R: All lines optically thick | F: Deuteration not reliably measurable | **refuted**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Emission unresolved; cannot distinguish envelope from disk; S hot corino needs higher resolution  
  > "Unfortunately, since the emission is not resolved, it is impossible to discriminate between the two possibilities." (Results)
- Caveat (inferred, ours): Single spectral window and single position analysed
- Caveat (inferred, ours): Abundance ratios rely on lower-limit methanol column
- Caveat (inferred, ours): Assumed Trot of 100 K for two species
- Caveat (inferred, ours): Size from spherical filling-factor assumption

## Reproducibility

- Data public (paper): Raw data to be public after proprietary period  
  > "The raw data will be available on the ALMA archive at the end of the proprietary period (ADS/JAO.ALMA#2018.1.01205.L)." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters beyond robust
- Missing: Self-calibration details
- Missing: Unpublished Tsys/normalization routine
- Data volume (inferred): ~50-100 GB raw
- Score (inferred): 4/5, Data from a public Large Program with a clear LVG recipe, but imaging and fitting details are sparse.
- Rediscovery candidate: no, Recipe is partial; imaging and rotational diagram details are missing and the LVG code is not public.

## Links

- Method: (cite: Ceccarelli2003) (LVG code)
- Related: FAUST ALMA Large Program

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
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
  "stated": 40,
  "rate": 0.597
 },
 "evidence_ok": true
}
```

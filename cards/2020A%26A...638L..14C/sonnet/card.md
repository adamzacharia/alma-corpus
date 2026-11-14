# The atomic gas of star-forming galaxies at z ∼ 0.05 as revealed by the Five-hundred-meter Aperture Spherical Radio Telescope

`2020A&A...638L..14C` | Astronomy and Astrophysics 2020 | first author: Cheng, Cheng | arXiv: 2006.04812 | DOI: 10.1051/0004-6361/202038483

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies
- Question: What is the atomic gas (HI) content and dynamics of four z~0.05 VALES star-forming galaxies observed with FAST, compared with their ALMA CO(1-0) data?  
  > "we aim to study the atomic gas content, via the Hi  21 cm emission line, in low-$z$ star formation galaxies taken from the Valparaíso ALMA/APEX Line Emission Survey (VALES)." (abstract)
- Target **HATLASJ083601.5+002617 (GAMA 214184)**: coordinates _not stated_; z/distance z_spec = 0.0332  
  > "| 214184 | 0.0332 |" (Table 2); distance from _not stated_
- Target **HATLASJ085346.4+001252 (GAMA 600024)**: coordinates _not stated_; z/distance z_spec = 0.0504  
  > "| 600024 | 0.0504 |" (Table 2); distance from _not stated_
- Target **HATLASJ085340.7+013348 (GAMA 323855)**: coordinates _not stated_; z/distance z_spec = 0.0410  
  > "| 323855 | 0.0410 |" (Table 2); distance from _not stated_
- Target **HATLASJ085112.9+010342 (GAMA 371789)**: coordinates _not stated_; z/distance z_spec = 0.0266  
  > "| 371789 | 0.0266 |" (Table 2); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00530.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=1-0 (not stated)
- Other facility **FAST**: New HI 21 cm spectra with the 19-beam L-band receiver (central beam), ON-OFF tracking  
  > "We were allocated 10 hours in L-band with the 19-Beam receiver during the FAST Commissioning Phase" (2.2 Observation setup and calibration)
- Other facility **ALFALFA (Arecibo)**: Archival HI spectrum for one target for comparison  
  > "we include one source with ALFALFA measurements (HATLASJ083601.5+002617) to check consistency and the relative performance of the FAST telescope." (2.1 Sample selection)
- Other facility **APEX**: CO(2-1) observations of VALES galaxies  
  > "(cite: Cheng2018), respectively." (2.1 Sample selection)
- External data: CO(1-0) luminosities, line widths and dynamical masses from ALMA/VALES  
  > "In (cite: Molina2019), we presented a dynamical analysis to 39 VALES galaxies using the spatial extension of the CO($J=1-0$) emission." (4.3 Dynamical masses) [from (cite: Molina2019); (cite: Villanueva2017)]
- External data: Stellar mass, radius and photometry from GAMA structure catalogue and H-ATLAS catalogue  
  > "We adopt the stellar mass, radius and the photometry from GAMA galaxy structure catalogue (cite: Kelvin2012) and $H$-ATLAS catalogue (cite: 2016MNRAS.462.3146V)." (4.2 The Hi gas mass) [from (cite: Kelvin2012); (cite: 2016MNRAS.462.3146V)]
- External data: ALFALFA HI flux and FWHM for HATLASJ083601.5+002617  
  > "The integrated flux of the Arecibo spectrum given in (cite: Haynes2018) is $1.68 \pm 0.14$ mJy km s$^{-1}$" (4.1 Comparison with a previous ALFALFA result) [from (cite: Haynes2018)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
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
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- FAST noise-diode flux calibration and 14.86 K/Jy conversion  
  > "We adopt a 14.86 K Jy$^{-1}$ conversion factor, which has an accuracy of the order of 10% (cite: Jiang2020)." (6 Data reduction) [from (cite: Jiang2020)]
- HI radius from HI mass relation  
  > "the $R_{\rm H\textsc{i}}$ can be estimated from $M _{\rm H\textsc{i}}$ using the relation derived by (cite: 2016MNRAS.460.2143W)." (4.3 Dynamical masses) [from (cite: 2016MNRAS.460.2143W)]
- HI inclination assumed equal to Ks-band inclination  
  > "if we assume the Ks band image and Hi have a similar inclination angle (cite: Molina2019)" (4.3 Dynamical masses) [from (cite: Molina2019)]

### Not stated but needed to reproduce (our reading)

- ALMA CO(1-0) calibration and imaging details (all from earlier papers)
- Inclination values and HI radii used per galaxy
- H2 mass conversion (alpha_CO) for baryon mass
- Baseline fit and RFI flagging details
- Distances used for HI mass

## Analysis recipe

1. **Reduce and calibrate FAST ON-OFF spectra**: Noise-diode calibration, inverse-variance weighted mean of ON and OFF spectra, ON-OFF, sinusoid+linear baseline fit, LSR correction, polarisations combined  
  > "We subtract the baseline using model-fit based on a sinusoidal plus a linear function" (6 Data reduction)
   - parameter: 14.86 K/Jy conversion; 10 min chunks; baseline fitted 1372-1376 MHz  
  > "The data is reduced in chunks of 10 min." (6 Data reduction)
   - fitting: _not stated_
   - validation: Compared with ALFALFA spectrum and checked two polarisations  
  > "We do not find significant differences in polarisation" (6 Data reduction)
2. **Measure HI flux and mass**: Resample to 20 km/s channels, sum channels within FWZI; M_HI = 2.35e5 D^2/(1+z) integral S dV; upper limit 5 x rms x 300 W300  
  > "derive the integrated Hi flux by summing over the velocity channels within Full Width at Zero Intensity (FWZI)" (3 Results)
   - assumption: 10% flux calibration uncertainty  
  > "the $10\% \times \rm flux$ would account for the uncertainty of the flux calibration" (3 Results)
   - fitting: _not stated_
   - validation: Consistency with ALFALFA and with empirical HI mass relations  
  > "This indicates a reasonable flux calibration for the FAST 19-beam receiver in this commissioning phase experiment." (4.1 Comparison with a previous ALFALFA result)
3. **Estimate HI dynamical mass**: M_dyn = (FWHM/2/sin theta)^2 R_HI / G with R_HI from HI mass-size relation  
  > "$M_{\rm dyn}^{\rm H\textsc{i}} = ({\rm FWHM/2/\sin \theta})^2 R_{\rm H\textsc{i}} / G$" (4.3 Dynamical masses)
   - assumption: HI inclination equals Ks-band inclination  
  > "We do not have inclination information of the Hi gas." (4.3 Dynamical masses)
   - fitting: _not stated_
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| rms at 1.7 km/s for 5 min ON (GAMA 214184) | 2.61 | not stated | mJy/beam | 1 | / HATLASJ083601.5+002617 / 214184 / 5 / 2.61 / |
| HI flux GAMA 214184 | 1696.5 | 188.1 | mJy km/s | 2 | 1696.5 $\pm$ 188.1 |
| log M_HI GAMA 600024 | 9.96 | 0.11 | Msun | 2 | / 600024 / 0.0504 / 9.96 $\pm$ 0.11 / |
| log M_dyn^HI GAMA 214184 | 11.96 | 0.05 | Msun | 3 | 11.96 $\pm$ 0.05 |

## Qualitative findings

- HI and CO(1-0) line profiles are similar in width.  
  > "We find that the CO($J=1-0$) and Hi emission line profiles are similar." (abstract)

## Claim tuples

- H: FAST commissioning data give HI fluxes consistent with ALFALFA | E: Compared FAST and ALFALFA spectrum of HATLASJ083601.5+002617 | R: Flux and FWHM consistent | F: FAST flux calibration is reasonable and sensitivity is comparable to ALFALFA with 5 min | **supported**
- H: HI traces more dark-matter-dominated mass than CO | E: Compared HI dynamical mass with baryon and CO dynamical mass | R: M_dyn^HI about an order of magnitude above baryon mass | F: HI traces the dark matter halo | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): rms does not decrease as 1/sqrt(t), possibly pointing jitter or weak interference in commissioning  
  > "The rms declines with the on-target integration time, but not in the manner of $\propto 1/\sqrt{t}$" (3 Results)
- Caveat (inferred, ours): HI dynamical mass relies on assumed inclination and statistical HI radius
- Caveat (inferred, ours): Only four galaxies; unresolved single-dish HI
- Caveat (inferred, ours): ALMA data used only via earlier papers

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: FAST raw data access
- Missing: ALMA CO reduction details
- Missing: per-galaxy inclinations and HI radii
- Data volume (inferred): FAST spectra ~ GB; ALMA CO cubes not reprocessed
- Score (inferred): 2/5, ALMA role minor, FAST data not clearly public, key inputs inherited.
- Rediscovery candidate: no, Main data are FAST observations not stated to be public; ALMA is minor.

## Links

- Method: (cite: Jiang2020) (FAST performance and calibration)
- Companion: (cite: Villanueva2017) (VALES ALMA CO(1-0) data)
- Companion: (cite: Molina2019) (CO dynamical analysis)
- Related: VALES
- Related: ALFALFA
- Related: H-ATLAS
- Related: GAMA

## Checks

```json
{
 "quotes": 33,
 "quotes_ok": 33,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 24,
  "rate": 0.32
 },
 "evidence_ok": true
}
```

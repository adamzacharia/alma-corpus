# Detection of extragalactic CF<SUP>+</SUP> toward PKS 1830-211. Chemical differentiation in the absorbing gas

`2016A&A...589L...5M` | Astronomy and Astrophysics 2016 | first author: Muller, S. | arXiv: 1604.00414 | DOI: 10.1051/0004-6361/201628494

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, astrochemistry, milky_way_ism
- Question: Is CF+ present in the z=0.89 molecular absorber toward PKS 1830-211, what is its abundance, and how does its line profile compare with other species?  
  > "Recently, H$_2$Cl$^+$ was detected in the z=0.89 molecular absorber toward the lensed blazar PKS 1830$-$211 ((cite: mul14b)), making it a good case to search for other halogen-bearing species." (Introduction)
- Target **PKS 1830-211 (lensed blazar, z=0.89 absorber; SW and NE images)**: coordinates _not stated_; z/distance z_abs=0.88582 (absorber)  
  > "The observations of the CF$^+$ J=2-1 line, redshifted to 108.8 GHz at z$_{abs}$=0.88582 (heliocentric frame)" (Observations); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.01099.S, 2011.0.00405.S
- bands: _not stated_
- frequencies and spectral setup: 4 spectral windows of 1.875 GHz, 3840 channels of 0.488 MHz, ~2.6 km/s after Hanning smoothing; CF+ 2-1 at 108.8 GHz  
  > "The correlator was configured with four different spectral windows of 1.875 GHz, each counting 3840 channels separated by 0.488 MHz" (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.75'' x 0.55''  
  > "with a synthesized beam of 0.75$''$$\times$0.55$''$ (Briggs weighting with robust parameter set to 0.5)" (Observations)
- max recoverable scale: _not stated_
- sensitivity: NE rms ~0.001 of continuum per 2.6 km/s channel; opacity uncertainty 0.003 (1 sigma)  
  > "down to a rms of $\sim$0.001 of the continuum level per 2.6 km s$^{-1}$ channel" (Results and discussion)
- time on source: two execution blocks of 6 minutes on source  
  > "Two execution blocks of 6 minutes on source were observed." (Observations)
- observing dates: 2014 August 27, ALMA Early Science Cycle 2  
  > "were taken during the ALMA Early Science Cycle 2 phase on 2014 August 27th." (Observations)
- pi or archival as stated: _not stated_
- Line: CF+ J=2-1 (205.17052 GHz)
- Line: HCO+, HCN, HNC, HOC+, c-C3H2, SO, CH3OH various (HCO+ 2-1 etc.) (177.26-205.79 GHz)
- External data: Line frequencies and molecular data from CDMS  
  > "Frequencies and molecular data are taken from the Cologne Database for Molecular Spectroscopy ((cite: mul01))." (Table 1) [from (cite: mul01)]
- External data: H2 column density 2e22 cm-2 toward SW  
  > "With a H$_2$ column density of 2$\times$10$^{22}$ cm$^{-2}$ ((cite: mul14a))" (Results and discussion) [from (cite: mul14a)]
- External data: 2012 ALMA Cycle 0 spectra for comparison  
  > "we compare the new spectra obtained in 2014 with those of the same lines observed in 2012 ((cite: mul14a), ALMA Cycle 0 data)" (Results and discussion) [from (cite: mul14a)]
- External data: CMB temperature 5.14 K at z=0.89  
  > "Hence their rotation temperature is equal to 5.14 K, the CMB temperature at z=0.89 ((cite: mul13))." (Introduction) [from (cite: mul13)]

## Processing

### Calibration

- pipeline or manual: CASA, standard procedure  
  > "The data calibration was done within the CASA[^1] package, following a standard procedure." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: bandpass J1924-292; gain J1832-2039 (no flux calibrator stated)  
  > "The bandpass response of the antennas was calibrated from observations of the bright quasar J 1924$-$292." (Observations)
- flux scale uncertainty: _not stated_
- self calibration: self-calibration on the bright continuum of PKS 1830-211  
  > "We further improved the data quality using self-calibration on the bright continuum of PKS 1830$-$211." (Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "Briggs weighting with robust parameter set to 0.5" (Observations)
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
- final beam: 0.75'' x 0.55''  
  > "with a synthesized beam of 0.75$''$$\times$0.55$''$" (Observations)
- final rms: _not stated_

### Inherited from earlier work

- Spectral extraction with UVMULTIFIT two-point-source model fitting  
  > "using the CASA-python task UVMULTIFIT ((cite: mar14)) to fit a model of two point sources to the visibilities" (Observations) [from (cite: mar14)]
- CF+ formation/destruction chemistry and ~1% prediction  
  > "in agreement with predictions from (cite: neu09)" (Results and discussion) [from (cite: neu09)]

### Not stated but needed to reproduce (our reading)

- Number of antennas/array configuration and baselines
- Flux calibrator and flux scale
- Self-calibration solution intervals
- Image size, cell size, and CLEAN parameters
- Details of UVMULTIFIT fit (start positions, flux ratios)
- Continuum normalization procedure
- Archival data details for 2011.0.00405.S (2012 spectra) reprocessing

## Analysis recipe

1. **Extract spectra of both lensed images**: Fit two-point-source model to visibilities with UVMULTIFIT  
  > "The spectra were extracted toward both lensed images of PKS 1830$-$211, using the CASA-python task UVMULTIFIT ((cite: mar14))" (Observations)
   - software: CASA, UVMULTIFIT
   - fitting: _not stated_
   - validation: Images resolved in CLEAN maps (1'' separation vs 0.75''x0.55'' beam)  
  > "We note that the two lensed images of PKS 1830$-$211, 1$''$ apart, were clearly spatially resolved" (Observations)
2. **Integrated opacity and column density**: Integrate opacity over -20 to +20 km/s, convert with alpha assuming excitation coupled to CMB  
  > "By integrating over the line between $-$20 kms to +20 km s$^{-1}$ and assuming thermal equilibrium with CMB photons, we find a total CF$^+$ column density of 5.5$\times$10$^{12}$ cm$^{-2}$." (Results and discussion)
   - assumption: Tex = 5.14 K (CMB at z=0.89); hyperfine splitting neglected; optically thin  
  > "calculated under the assumption that the rotational excitation is coupled with the cosmic microwave background temperature, 5.14 K at z=0.89" (Table 1)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fractional abundance and fluorine fraction**: Divide by N(H2)=2e22 cm-2; compare with cosmic fluorine abundance; steady-state CF+/HF ratio from rate coefficients  
  > "this corresponds to an averaged fractional abundance \[CF$^+$\]/\[H$_2$\] of $\sim$3$\times$10$^{-10}$." (Results and discussion)
   - assumption: Fluorine abundance in absorber similar to cosmic; T=100 K; [e]≈[C+]  
  > "Assuming that the fluorine abundance is similar in the absorbing clouds of the z=0.89 galaxy" (Results and discussion)
   - fitting: _not stated_
   - validation: Compared with Galactic W49 CF+/HF ratio 0.010-0.025  
  > "the abundance ratio \[CF$^+$\]/\[HF\] is in the range 0.010–0.025 for various velocity components" (Results and discussion)

## Software

- **CASA** : calibration, self-calibration, CLEAN imaging  
  > "The data calibration was done within the CASA[^1] package, following a standard procedure." (Observations)
- **UVMULTIFIT** : two-point-source visibility fitting to extract spectra  
  > "using the CASA-python task UVMULTIFIT ((cite: mar14))" (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CF+ total column density (SW) | 5.5e12 | not stated | cm^-2 | 2 | / CF$^+$ (2-1) / 205.17052 / 108.796 / 4.9 / 2.0 / 1.13 / 26.2 / 0.21 / 5.5 / |
| CF+ integrated opacity (-20 to +20 km/s) | 0.21 | 0.003 (1 sigma) | km/s | 2 | The associated uncertainty is of 0.003 at 1$\sigma$. |
| [CF+]/[H2] | ~3e-10 | not stated | dimensionless | 3 | averaged fractional abundance \[CF$^+$\]/\[H$_2$\] of $\sim$3$\times$10$^{-10}$ |
| Fraction of fluorine in CF+ | ~1% | not stated | percent | 3 | we conclude that only $\sim$1% of the interstellar fluorine is captured in CF$^+$ |
| Continuum covering factor | ~94% | not stated | percent | 0 | yielding $f_c$$\sim$94% |
| CF+ line FWHM | ~15 | not stated | km/s | 0 | much narrower than the absorption line width ($\sim$15 km s$^{-1}$, FWHM) |
| Predicted [CF+]/[HF] at T=100 K | ~7% | factor 2-3 in coefficient | percent | 3 | gives the ratio \[CF+\]/\[HF\]$\sim$7% |

## Qualitative findings

- CF+ not detected toward NE image, where gas is more atomic and diffuse  
  > "CF$^+$ is not detected toward the NE image" (Results and discussion)
- CF+ profile peaks on red wing (+5 km/s), anti-correlated with CH3OH, closest to [C I]  
  > "it is \[C I\] which has the closest line profile to CF$^+$" (Results and discussion)

## Claim tuples

- H: Is CF+ present in the z=0.89 absorber? | E: ALMA band 3 absorption spectroscopy toward PKS 1830-211 | R: CF+ 2-1 absorption detected toward SW, up to ~1.5% of continuum | F: First extragalactic CF+ detection | **supported**
- H: Does CF+ trace the same gas as other species? | E: Compare line profiles within same tuning and with 2012 data | R: CF+ profile differs from others, anti-correlated with CH3OH | F: Chemical differentiation in the absorbing gas | **supported**
- H: Does CF+ abundance agree with fluorine chemistry predictions? | E: Column density divided by N(H2) and compared with cosmic F | R: ~3e-10; ~1% of F | F: HF is main fluorine reservoir, consistent with models | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: 13CN N=1-0 at z=0 as alternative identification rejected (expected narrow, hyperfine pattern, very weak)  
  > "except $^{13}$CN N=1-0 at z=0, but we would expect 1) the line to be very narrow" (Results and discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Only one CF+ transition; k_f unmeasured so coefficient uncertain by factor 2-3  
  > "Therefore, the coefficient 0.138 may have an uncertainty of a factor of 2–3." (Results and discussion)
- Caveat (inferred, ours): Column density uncertainty not given; depends on assumed CMB excitation
- Caveat (inferred, ours): Fluorine abundance assumed cosmic in a z=0.89 galaxy
- Caveat (inferred, ours): Covering factor and time variability may affect opacity
- Caveat (inferred, ours): Short observation, single epoch

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Antenna configuration, flux calibrator, self-cal parameters, UVMULTIFIT settings, continuum normalization
- Data volume (inferred): ~10-30 GB raw (two 6-min execution blocks)
- Score (inferred): 3/5, Short paper, public ALMA data with project codes, simple numeric chain, but processing details sparse.
- Rediscovery candidate: yes, Public ALMA data, short recipe (extract spectrum, integrate opacity, compute column), numeric results.

## Links

- Method: (cite: mar14) (UVMULTIFIT visibility fitting)
- Companion: (cite: mul14a) (2012 ALMA Cycle 0 spectra and N(H2))
- Companion: (cite: kaw16) (HF detection toward same absorber)

## Checks

```json
{
 "quotes": 46,
 "quotes_ok": 46,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 31,
  "rate": 0.47
 },
 "evidence_ok": true
}
```

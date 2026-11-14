# ALMA observations of molecular absorption in four directions toward the Galactic bulge

`2018A&A...610A..49L` | Astronomy and Astrophysics 2018 | first author: Liszt, H. | arXiv: 1712.03916 | DOI: 10.1051/0004-6361/201731983

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: milky_way_ism, astrochemistry
- Question: Can diffuse molecular gas in the Galactic bulge be detected in absorption toward other mm-wave continuum sources, and how do its chemistry, kinematics and 12C/13C compare with disk and CMZ gas?  
  > "We aimed to test whether molecular gas in the bulge could also be detected toward the three other, sufficiently strong mm-wave continuum sources seen toward the bulge at |b| < 3 o ." (abstract)
- Target **J1713-3418, J1717-3341, J1733-3722, J1744-3116**: coordinates J1744: l,b = 357.863, -0.997 (Table 1); J1713: 351.705, +2.787; J1717: 352.733, +2.391; J1733: 351.818, -2.889  
  > "J1744-3116 357.863, −0.997 0.33 0.32 1.46 0.90 1.20 1.93 3.13 0.62 2.14" (Table 1); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00132.S
- bands: _not stated_
- frequencies and spectral setup: 1919 channels spaced 61.13 kHz (0.205 km/s at HCO+; 0.187 km/s at CS(2-1)); channel spacing is half the spectral resolution; lines in 87-98 GHz  
  > "Each spectrum consisted of 1919 semi-independent channels spaced 61.13 kHz corresponding to 0.205 km s −1 at the 89.189 GHz rest frequency of HCO + or 0.187 km s −1 for CS(2-1)" (2.1 New ALMA absorption measurements)
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
- Line: HCO+ J=1-0 (89.189 GHz)
- Line: CS J=2-1 (97.981 GHz)
- Line: H13CO+, HCN, C2H J=1-0 (not stated)
- Other facility **GASS III**: 21 cm HI emission spectra  
  > "we compare our HCO + spectra with Galactic All-Sky Survey (GASS) III λ21 cm H I emission spectra" (2.2 Other data)
- External data: HI absorption profiles toward J1717 and J1744  
  > "we use the H I absorption profiles of Dickey et al. (1983)" (2.2 Other data) [from Dickey et al. (1983)]
- External data: Local-cloud CS, HCN, HCO+ and C2H absorption measurements for comparison  
  > "We also use the CS and HCN absorption profiles for local clouds from Lucas & Liszt (2002) and Liszt & Lucas (2001), respectively" (2.2 Other data) [from Lucas & Liszt (2002); Liszt & Lucas (2001); Lucas & Liszt (2000)]
- External data: K-band extinction A_K from 3-D bulge extinction map  
  > "the 3-D IR extinction map of the Galactic bulge of Schultheis et al. (2014)" (2.3 Extinction) [from Schultheis et al. (2014)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline-processed data products delivered 2017 February  
  > "whose pipeline data products were delivered in 2017 February" (2.1 New ALMA absorption measurements)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Spectra extracted from continuum-subtracted pipeline cubes  
  > "extracted from the continuum-subtracted pipeline-processed data cubes" (2.1 New ALMA absorption measurements)
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
- continuum subtraction: done in pipeline; spectra taken at pixel of peak continuum and divided by continuum flux  
  > "at the pixel of peak continuum flux in the continuum map made from each spectral window, and divided by the continuum flux in the continuum map at that pixel." (2.1 New ALMA absorption measurements)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Bulge geometry, galactocentric radii and HI column density context for J1744  
  > "As discussed in Gerin & Liszt (2017), especially their Table 1 and Fig. 4" (4.1.1 Strucure and kinematics) [from Gerin & Liszt (2017)]

### Not stated but needed to reproduce (our reading)

- Observing dates, array configuration, beam and time on source
- CASA/pipeline version
- Imaging weighting and cube parameters
- Continuum rms and per-channel noise values
- HCO+ abundance relative to H2 justification (3e-9) is not explained
- Velocity ranges and baselines used for integration were chosen by eye

## Analysis recipe

1. **Extract absorption spectra**: Spectra taken at peak continuum pixel from continuum-subtracted cubes and divided by continuum  
  > "divided by the continuum flux in the continuum map at that pixel." (2.1 New ALMA absorption measurements)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive HCO+ and H13CO+ column densities and isotopic ratios**: Integrate optical depths in limit of no excitation above CMB; Monte Carlo for errors  
  > "estimated using the measured rms line/continuum ratios in absorption-free regions in channel-by-channel Monte Carlo simulations of the observed profile taken as the expectation value." (3.1 12C/13C in the disk gas)
   - parameter: N(HCO+) = 1.10e12 cm-2 ∫τdv; N(H13CO+) = 1.135e12 cm-2 ∫τdv  
  > "N(HCO + ) = 1.10 × 10 12 cm −2 [ �] τ dv and N(H 13 CO + ) = 1.135 × 10 12 cm −2 [ �] τ dv" (3.1 12C/13C in the disk gas)
   - assumption: dipole moment 3.92 Debye  
  > "for a molecular dipole moment of 3.92 Debye" (3.1 12C/13C in the disk gas)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive H2 and HI column densities and molecular fractions**: N(H2)=N(HCO+)/3e-9; optical-depth-corrected N(HI) from Eq. 1 with Dickey HI absorption  
  > "e N(H 2 ) = N(HCO + )/3 × 10 −9" (Table 1)
   - assumption: HCO+/H2 abundance 3e-9; R0 = 8500 pc  
  > "R 0 = 8500 pc" (Table 1)
   - fitting: _not stated_
   - validation: _not stated_
4. **Gaussian decomposition of HCN, CS and HI profiles**: Gaussian components fit to line profiles; CS fit subtracted to integrate remainder over HCN components  
  > "we decomposed the line profiles of HCN and CS into gaussian components as shown in Tables 4-5." (4.1.2 Chemical comparisons in the bulge gas)
   - fitting: _not stated_
   - validation: Compared with local gas regression lines of Lucas & Liszt  
  > "The regression line is a power law of slope 0.85 fit to the existing data for clouds seen locally" (Fig. 6 caption)
5. **Limit HI spin temperature of self-absorbing gas**: Solve two radiative transfer equations for foreground/background spin temperatures using HI absorption and emission  
  > "can be solved for the spin temperatures of the foreground and background gases as functions of the value of τ fg ." (3.2 H I spin temperature)
   - fitting: _not stated_
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| N(HCO+)/N(H13CO+) toward J1717 disk | 58 | ±9 | dimensionless | 2 | J1717 -25..10 7.002(0.027) 0.117(0.018) 7.70(0.03) 58 ± 9 |
| N(HCO+)/N(H13CO+) toward J1744 disk | 64 | ±4 | dimensionless | 2 | J1744 -33..13 21.852(0.056) 0.333(0.023) 24.03(0.06) 64 ± 4 |
| N(HCO+)/N(H13CO+) bulge gas toward J1744 | >51 (3σ) | not stated | dimensionless | 2 | N(HCO + )/N(H 13 CO + ) > 51 (3σ) for the bulge gas toward J1744 |
| HI self-absorbing component optical depth toward J1744 | 0.686 | ±0.081 | dimensionless | 5 | τ fg = 0.686 ± 0.081 corresponding to T sp, fg = 16.2(+8.0, −10.2) K |
| Spin temperature of foreground self-absorbing HI | 16.2 | +8.0/-10.2 | K | 5 | T sp, fg = 16.2(+8.0, −10.2) K |
| 2N(H2) 3 kpc arm toward J1717 | 6.4e19 | ±1.8e19 | cm-2 | 3 | 2N(H 2 ) = 6.4 ± 1.8 × 10 19 cm −2, or f H 2 ≈ 0.24 |
| 2N(H2) far-side 3 kpc arm toward J1744 | 7.3e19 | ±1.2e19 | cm-2 | 3 | 2N(H 2 ) = 7.3 ± 1.2 × 10 19 cm −2, ie, the gas is ≈ 48% molecular. |

## Qualitative findings

- No molecular absorption from deep bulge gas toward J1713, J1717, J1733; 3 kpc arm absorption newly detected toward J1717 and J1744  
  > "absorption from the 3 kpc arm was newly detected toward J1717 and J1744." (abstract)

## Claim tuples

- H: Bulge molecular gas can be detected toward other mm-wave continuum sources | E: ALMA absorption toward three additional sources | R: No deep-bulge molecular absorption; none toward J1717 despite HI emission | F: Only J1744 shows bulge molecular absorption | **refuted**
- H: Bulge gas toward J1744 resembles disk gas rather than CMZ gas | E: Compared HCO+, HCN, C2H, CS column densities and 12C/13C | R: Ratios similar to local gas; HCO+/H13CO+ > 51 vs 20-25 in CMZ | F: Bulge gas is disk-like, not 13C-enhanced | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): HI spin temperature result limited by noise in old HI absorption profile and spans dark to diffuse gas temperatures  
  > "The precision of the present result is limited by the noise level in the rather old absorption profile of Dickey et al. (1983)." (3.2 H I spin temperature)
- Caveat (inferred, ours): Abundance HCO+/H2 = 3e-9 assumed uniformly for bulge and disk
- Caveat (inferred, ours): Only one bulge sightline, so generalization is weak
- Caveat (inferred, ours): Optical depth saturation in HCO+ affects ratios
- Caveat (inferred, ours): Beam/continuum-source structure effects not discussed

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Pipeline products delivered; project code given  
  > "whose pipeline data products were delivered in 2017 February." (2.1 New ALMA absorption measurements)
- Missing: Observing/array details and noise levels
- Missing: Integration velocity limits beyond Table 2 and Gaussian fitting procedure details
- Missing: Comparison data from earlier papers
- Data volume (inferred): ~10-50 GB (four sources, several spectral windows, pipeline products)
- Score (inferred): 6/5, Simple pipeline-product spectra and clear formulae, but observation setup and fitting details are thin.
- Rediscovery candidate: yes, Data from a project that is likely public, simple recipe, numeric ratios and column densities.

## Links

- Companion: Gerin & Liszt (2017) (Original discovery of bulge absorption toward J1744)
- Companion: Riquelme et al. (2017) (Spectral scan of J1744 absorption)
- Related: GASS

## Checks

```json
{
 "quotes": 37,
 "quotes_ok": 37,
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
  "facts": 68,
  "stated": 23,
  "rate": 0.338
 },
 "evidence_ok": true
}
```

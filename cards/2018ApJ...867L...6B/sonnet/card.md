# Evidence for the First Extragalactic Hydrogen Recombination Line Maser in NGC 253

`2018ApJ...867L...6B` | The Astrophysical Journal Letters 2018 | first author: Báez-Rubio, Alejandro | arXiv: 1810.07213 | DOI: 10.3847/2041-8213/aae825

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies, star_formation
- Question: Is there hydrogen recombination line maser emission (H26α) in the nuclear starburst of NGC 253, identifiable via the H30α/H26α recombination line spectral index?  
  > "We present the first detection of extragalactic hydrogen recombination line maser emission in the H26α transition toward the inner 13.5 pc nuclear region of the starburst galaxy NGC 253 using ALMA data." (abstract)
- Target **NGC 253 nucleus (sources 10, 10NE, 11, 13)**: coordinates Source 10: 00:47:33.155 -25:17:17.12 (J2000); 10NE: 00:47:33.168 -25:17:16.89; 11: 00:47:33.172 -25:17:17.42; 13: 00:47:33.193 -25:17:16.77  
  > "Located at a distance of 3.5 ± 0.2 Mpc (Mouhcine et al. 2005; Rekola et al. 2005)" (1. INTRODUCTION); "10NE 00:47:33.168 -25:17:16.89" (Table 1); z/distance 3.5 ± 0.2 Mpc  
  > "Located at a distance of 3.5 ± 0.2 Mpc (Mouhcine et al. 2005; Rekola et al. 2005)" (1. INTRODUCTION); "10NE 00:47:33.168 -25:17:16.89" (Table 1); distance from Mouhcine et al. 2005; Rekola et al. 2005  
  > "Located at a distance of 3.5 ± 0.2 Mpc (Mouhcine et al. 2005; Rekola et al. 2005)" (1. INTRODUCTION); "10NE 00:47:33.168 -25:17:16.89" (Table 1)

## Data provenance

- ALMA projects: 2013.1.00191.S, 2015.1.00274.S, 2015.1.01133.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: better than ~0.35 arcsec; H26α cube original 0.23''; H30α 0.303'' x 0.248'' PA -75.5 deg  
  > "We have used ALMA archival data with angular resolutions higher than ∼ 0.35 arcsec" (2. DATA REDUCTION AND RESULTS); "i.e. 0. [′′] 303 × 0. [′′] 248" (3. CONSTRAINING THE IONIZED STRUCTURE)
- max recoverable scale: _not stated_
- sensitivity: 0.46–0.60 mJy/beam at 231.90 and 353.62 GHz in 30 km/s channels  
  > "sensitivities of 0.46–0.60 mJy beam [−][1] (at 231.90 and 353.62 GHz respectively) at a velocity resolution of 30 km s [−][1]" (2. DATA REDUCTION AND RESULTS)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: archival data  
  > "We have used ALMA archival data" (2. DATA REDUCTION AND RESULTS)
- Line: H H30α (231.90 GHz)
- Line: H H26α (353.62 GHz)
- External data: Continuum source positions/identifications (sources 10, 11, 13) in NGC 253 nucleus  
  > "toward the continuum sources reported by Leroy et al. (2018)." (2. DATA REDUCTION AND RESULTS) [from Leroy et al. (2018)]
- External data: MWC349A H30α flux ~30 Jy and RLSI 3.3  
  > "a RLSI of 3.3 (Thum et al. 1994)" (3.2. Comparison with galactic RL masers.) [from Thum et al. 1994]
- External data: Monoceros R2-IRS2 RLSI ≈ 1.81  
  > "shows α L ≈ 1.81 (Jim´enez-Serra et al. 2013)" (3.2. Comparison with galactic RL masers.) [from Jiménez-Serra et al. 2013]
- Simulation/model as data: MORELI 3D radiative transfer models of isothermal ionized wind (mass-loss 5e-5 Msun/yr, Te 6000 K, v 30 km/s) giving continuum and RL spectral indices vs b_d  
  > "We have used the MORELI code (B´aez-Rubio et al. 2013) to take into account both the continuum and RL opacity effects." (Figure 3)

## Processing

### Calibration

- pipeline or manual: standard CASA calibration with modified pipeline scripts  
  > "Data calibration and imaging were carried out in the standard manner with the CASA package" (2. DATA REDUCTION AND RESULTS)
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
- continuum subtraction: local continuum, zero or first order polynomials, in MADCUBA  
  > "In order to subtract the local continuum (with zero or first order polynomials)" (2. DATA REDUCTION AND RESULTS)
- line free channels: identified with the STATCONT method  
  > "we have identified the free line channels of our regions with the help of the Statcont Method" (2. DATA REDUCTION AND RESULTS)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: H26α cube smoothed to H30α resolution 0.303'' x 0.248''  
  > "spatially smoothed to match the resolution of the H30α cube" (3. CONSTRAINING THE IONIZED STRUCTURE)
- final beam: _not stated_
- final rms: 0.45 mJy (H30α) and 0.60 mJy (H26α); continuum 1 mJy  
  > "(0.45 and 0.60 mJy for the H30α and H26α cubes respectively)" (Figure 1)

### Inherited from earlier work

- Statcont method for continuum determination  
  > "Statcont Method (S´anchez-Monge et al. 2018)" (2. DATA REDUCTION AND RESULTS) [from Sánchez-Monge et al. 2018]
- MADCUBA usage  
  > "(see, e.g. Mart´ın-Dom´enech et al. 2017)" (2. DATA REDUCTION AND RESULTS) [from Martín-Doménech et al. 2017]

### Not stated but needed to reproduce (our reading)

- Which archival datasets (EBs, spectral windows) supply H30α vs H26α
- CASA/pipeline version
- Imaging weighting, robust, cell/image size, deconvolver
- Line-free channel ranges and polynomial order per source
- Flux calibrators and flux scale uncertainty
- Self-calibration
- Beam-matching/convolution procedure details
- Primary beam correction

## Analysis recipe

1. **Calibrate and image cubes**: Standard CASA pipeline scripts modified to image whole spectral ranges  
  > "The pipeline reduction scripts were modified to image the whole spectral ranges." (2. DATA REDUCTION AND RESULTS)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Subtract continuum**: Identify line-free channels with STATCONT, subtract local continuum in MADCUBA  
  > "The continuum subtraction and spectral analysis of the H26α and H30α RL cubes were done with the MADCUBA software" (2. DATA REDUCTION AND RESULTS)
   - software: STATCONT, MADCUBA
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure RL profiles and fit Gaussians**: Gaussian fits to line profiles toward each source (Table 1); H26α smoothed to H30α beam; integrate over FWHM region from 2D Gaussian fits  
  > "The RLSIs were measured integrating the RL emission over the regions defined by their FWHM sizes derived from bidimensional Gaussian fits" (3. CONSTRAINING THE IONIZED STRUCTURE)
   - software: MADCUBA
   - fitting: Gaussian line fits; uncertainties include baseline fit  
  > "Uncertainties of the integrated line intensities are estimated taking into account the uncertainties introduced by the baseline fit." (Table 1)
   - validation: _not stated_
4. **Derive RL spectral index and compare with models**: RLSI from velocity-integrated intensities of H30α and H26α, compared to MORELI model predictions vs b_d; maser if αL > ~2.0±0.1  
  > "A measured value for the RLSI, α L, larger than ≈ 2.0 ± 0.1 would indicate RL maser emission" (2.1. Recombination Lines Spectral Indices)
   - software: MORELI
   - parameter: mass-loss 5e-5 Msun/yr, Te 6000 K, expansion velocity 30 km/s  
  > "an electron temperature of 6000 K and an expansion velocity of 30 km s [−][1]" (Figure 3)
   - assumption: Isothermal ionized wind with Ne ∝ r^-b_d; Te up to 12000 K considered  
  > "For the case of an isothermal ionized wind with an electron density, N e, that decreases with a power-law function" (2.1. Recombination Lines Spectral Indices)
   - fitting: _not stated_
   - validation: Confidence of maser via error propagation (1.7 sigma, ~90%)  
  > "our measured RLSI would indicate maser emission with a confidence level of about a 90% (1.7 sigma-level)" (3.1. Recombination line masers toward sources 10 and 10NE)
5. **Estimate number of MWC349A-like winds and ionizing photon rate**: Scale MWC349A H30α flux (~30 Jy at 1620 pc) to 3.5 Mpc; Lyman continuum rate from LTE line-to-continuum ratio ~125 km/s  
  > "∼ 700 MWC349A-like ionized winds are required to explain the measured intensity of the H26α line in 10NE" (3.2. Comparison with galactic RL masers.)
   - assumption: Te 6000 K, LTE optically thin H30α  
  > "Assuming an electron temperature of 6000 K and LTE emission for the H30α RL" (4. REVEALING THE EVOLUTION OF YOUNG SUPER STAR CLUSTERS)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration and imaging  
  > "Data calibration and imaging were carried out in the standard manner with the CASA package" (2. DATA REDUCTION AND RESULTS)
- **MADCUBA** : continuum subtraction and spectral analysis  
  > "The continuum subtraction and spectral analysis of the H26α and H30α RL cubes were done with the MADCUBA software" (2. DATA REDUCTION AND RESULTS)
- **STATCONT** : identify line-free channels  
  > "we have identified the free line channels of our regions with the help of the Statcont Method" (2. DATA REDUCTION AND RESULTS)
- **MORELI** : 3D radiative transfer models of RL and continuum spectral indices  
  > "We have used the MORELI code (B´aez-Rubio et al. 2013)" (Figure 3)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| RLSI source 10 | 2.15 | 0.69 | dimensionless | 4 | 2.15 ± 0.69 |
| RLSI source 10NE (one channel 260-290 km/s) | 2.91 | 0.83 | dimensionless | 4 | we measure a RLSI of α L = 2.91 ± 0.83 |
| RLSI source 10NE (Gaussian fits) | 1.80 | 0.57 | dimensionless | 4 | 1.80 ± 0.57, 2.91 ± 0.83 |
| RLSI source 11 | 1.1 | 0.59 | dimensionless | 4 | 1.1 ± 0.59 |
| RLSI source 13 | 1.0 | 1.3 | dimensionless | 4 | 1.0 ± 1.3 |
| 10NE H26α integrated intensity (260-290 km/s) | 145 | 18 | mJy km/s | 3 | 145 ± 18 and 43 ± 14 mJy km s [−][1] for the H26α and H30α RLs |
| Number of MWC349A-like winds needed in 10NE | ~700 | not stated | dimensionless | 5 | ∼ 700 MWC349A-like ionized winds are required |
| Lyman continuum rate per source | ≳ 3e51 | not stated | s^-1 | 5 | the Lyman continuum production rate required to maintain the ionization would be ≳ 3 · 10 [51] s [−][1] toward all our sources |

## Qualitative findings

- Sources 11 and 13 are optically thin and more evolved; sources 10 and 10NE are optically thicker and younger SSCs near the putative AGN  
  > "the outermost sources 11 and 13 seem to be the most evolved (since they are optically thin)" (4. REVEALING THE EVOLUTION OF YOUNG SUPER STAR CLUSTERS)

## Claim tuples

- H: H26α maser emission exists in NGC 253's nucleus | E: Measure H30α/H26α RLSI toward compact sources and compare with LTE model limits | R: αL = 2.15±0.69 (source 10) and 2.91±0.83 (10NE) exceed the LTE limit ~2 | F: Evidence for the first extragalactic RL maser, about 90% confidence for 10NE | **partially**
- H: The maser arises from stellar winds like MWC349A | E: Scale MWC349A flux to NGC 253 distance | R: ~700 MWC349A-like winds needed | F: Maser emission from hundreds of MWC349A-like ionized winds in an SSC | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Continuum is dominated by dust and mixed emission so RLSI is used instead  
  > "Therefore, the continuum maps cannot be used to infer the bremsstrahlung SED at the frequencies of the H30α and H26α RLs." (2.1. Recombination Lines Spectral Indices)
- Alternative: LTE emission with steep density gradient b_d=3 could barely be consistent at 1 sigma, but judged extreme  
  > "Only for the case of b d = 3, the RLSI would be barely consistent with LTE emission at a 1 sigma-level." (3.1. Recombination line masers toward sources 10 and 10NE)
- How they decided it was enough: _not stated_
- Limitation (authors): For source 10, LTE with b_d>2 cannot be ruled out given H30α uncertainties  
  > "given the uncertainties in the H30α detection, we cannot rule out that emission is under LTE conditions" (3.1. Recombination line masers toward sources 10 and 10NE)
- Caveat (inferred, ours): Maser significance only ~1.7 sigma and for 10NE based on one channel without baseline uncertainty
- Caveat (inferred, ours): Different beams and calibration systematics between two bands not discussed
- Caveat (inferred, ours): Dust/continuum subtraction uncertainty affects the weak H30α
- Caveat (inferred, ours): Lines are broad so maser claim lacks narrow features

## Reproducibility

- Data public (paper): ALMA archival data  
  > "We have used ALMA archival data" (2. DATA REDUCTION AND RESULTS)
- Products in archive: _not stated_
- Missing: Exact datasets/spectral windows and CASA version
- Missing: Imaging parameters
- Missing: Line-free channels and baseline polynomial choice per source
- Missing: MORELI code availability
- Data volume (inferred): ~100-300 GB raw for the band 6 and 7 archival datasets
- Score (inferred): 3/5, Public data and a simple measurement, but imaging and processing parameters are not given.
- Rediscovery candidate: no, Recipe lacks imaging details and MORELI modeling is not reproducible from the paper alone.

## Links

- Method: Sánchez-Monge et al. 2018 (STATCONT continuum determination)
- Method: Báez-Rubio et al. 2013 (MORELI RL radiative transfer code)
- Companion: Leroy et al. 2018 (continuum source catalogue in NGC 253)

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2015.1.01133.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 37,
  "rate": 0.5
 },
 "evidence_ok": true
}
```

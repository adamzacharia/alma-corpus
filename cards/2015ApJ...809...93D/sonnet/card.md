# Observational Signatures of Planets in Protoplanetary Disks I. Gaps Opened by Single and Multiple Young Planets in Disks

`2015ApJ...809...93D` | The Astrophysical Journal 2015 | first author: Dong, Ruobing | arXiv: 1411.6063 | DOI: 10.1088/0004-637X/809/1/93

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks
- Question: Are gaps opened by one or several planets in protoplanetary disks broadly consistent with observed gaps/cavities in transitional disks at NIR and mm wavelengths?  
  > "aim at answering this basic question: are they broadly consistent with some observed gaps in disks?" (1 Introduction)
- Target **HL Tau (qualitative comparison only)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00015.SV
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
- External data: ALMA image of the HL Tau disk used for qualitative comparison with model mm image  
  > "A comparison between the model mm image and the observation of HL Tau is shown in Figure [\[fig:comparison\]](#fig:comparison)." (4.2 An HL-Tau-Like System with Multiple Separate Gaps and Rings) [from ALMA Partnership, et al. 2015 (cite: brogan15)]
- External data: Observed NIR gap contrasts for RX J1604.3-2130, HD 142527, SAO 206462, PDS 70  
  > "RX J1604.3-2130 | $3.6\pm0.5$ | (cite: mayama12)" (Table 4) [from (cite: mayama12); (cite: canovas13); (cite: garufi13); (cite: hashimoto12)]
- Simulation/model as data: Five FARGO 2D gas+1 mm dust hydro models (1x0.2MJ, 1x1MJ, 4x1MJ, 4x2MJ, 3x0.2MJ) fed into Whitney MCRT code to make H-band and ALMA band 7 (870 um) model images  
  > "In total we carry out five simulations." (2.1 Hydrodynamical Gas+Dust Simulations)

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

- Hydro model setups largely adopted from Zhu et al. 2011  
  > "Hydrodynamical model setups are largely adopted from (cite: zhu11), and are briefly summarized here." (2.1 Hydrodynamical Gas+Dust Simulations) [from (cite: zhu11)]
- MCRT disk setup adopted from Dong et al. 2012 (cavity paper)  
  > "The disk setup is largely adopted from (cite: dong12cavity)." (2.2 Monte Carlo Radiative Transfer Simulations) [from (cite: dong12cavity)]
- Dust fluid implementation in FARGO  
  > "using the FARGO code (cite: masset00) with a newly implemented dust fluid (cite: zhu12)" (2.1 Hydrodynamical Gas+Dust Simulations) [from (cite: masset00); (cite: zhu12)]

### Not stated but needed to reproduce (our reading)

- Whitney MCRT code version and input parameter files
- Hydro floor value for big-grain surface density
- Stellar luminosity
- Inclined-image azimuthal averaging details

## Analysis recipe

1. **2D two-fluid hydro simulations**: FARGO with dust fluid, planets on fixed circular orbits, no accretion, alpha=0.001, 256x256 cells, 1-500 AU  
  > "The simulations have 256 grid cells in both radial (1-500 AU) and azimuthal ($2\pi$) directions." (2.1 Hydrodynamical Gas+Dust Simulations)
   - software: FARGO
   - parameter: 1 mm particles; initial dust-to-gas 0.9%; T = 221 (r/AU)^-1/2 K; 1 Msun star  
  > "We further assume a radial temperature distribution $T = 221 (r/{\rm AU})^{-1/2}$ K" (2.1 Hydrodynamical Gas+Dust Simulations)
   - assumption: Schmidt number Sc=1; Epstein drag; no dust feedback  
  > "No feedback from the dust on the gas is considered since gas-to-dust mass ratio is always much larger than 1 in our simulations." (2.1 Hydrodynamical Gas+Dust Simulations)
   - fitting: _not stated_
   - validation: _not stated_
2. **3D MCRT imaging**: Map 2D densities to 3D with Gaussian vertical profiles and settling, run Whitney MCRT with 4 billion photon packages to get H-band and 870 um images  
  > "All simulations are run with 4 billion photon packages." (2.2 Monte Carlo Radiative Transfer Simulations)
   - software: Whitney MCRT code
   - parameter: Small grains Sigma_sg = 0.1% Sigma_g; big grains 0.9-1.1 mm  
  > "We set $\Sigma_{\rm sg}=0.1\%~\Sigma_{\rm g}$" (2.2 Monte Carlo Radiative Transfer Simulations)
   - assumption: Distance 140 pc  
  > "The source is assumed to be at a distance of 140 pc from earth." (2.2 Monte Carlo Radiative Transfer Simulations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Convolve and measure gaps**: Convolve with Gaussian PSF (0.04'' H band; 0.1'' ALMA B7; 0.035'' for 3x0.2MJ), measure gap edges at half peak and contrasts from azimuthal averages  
  > "convolved images at ALMA band 7 are produced by convolving the raw images by a Gaussian kernel with a FWHM of $0.1\ensuremath{''}$" (2.2 Monte Carlo Radiative Transfer Simulations)
   - fitting: _not stated_
   - validation: Qualitative comparison of gap contrasts and sizes with published observations  
  > "Nevertheless, our models show promising agreement with observations." (4.1.2 Gap Depth)

## Software

- **FARGO** : 2D gas+dust hydrodynamics  
  > "using the FARGO code (cite: masset00)" (2.1 Hydrodynamical Gas+Dust Simulations)
- **Whitney MCRT code** : 3D Monte Carlo radiative transfer images and SEDs  
  > "We carry out 3D MCRT simulations using the code developed by (cite: whitney13)." (2.2 Monte Carlo Radiative Transfer Simulations)
- **bhmie (Bohren & Huffman, modified by Draine)** : grain opacity, albedo, scattering  
  > "calculated using the routine developed by (cite: bohren83)" (2.2 Monte Carlo Radiative Transfer Simulations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Big-grain gap density contrast, models with Mp>=1MJ | >~1e9 | lower limit (hard floor) | dimensionless | 1 | $\gtrsim10^9$ |
| H-band convolved gap contrast, Mp>=1MJ models | 3-6 | not stated | dimensionless | 3 | At $H$ band, $\zeta_{\rm image,conv}$ are only around 3-6 for all models with $M_{\rm p}\geq1M_{\rm J}$ |
| mm convolved gap contrast, Mp>=1MJ models | ~100-1600 | not stated | dimensionless | 3 | comparing with $\sim100-1600$ at mm wavelengths |
| NIR gap width: 1x1MJ vs 4x1MJ | ~10 AU vs ~22 AU | not stated | AU | 3 | the gap opened by a one $M_{\rm J}$ planet at 30 AU is only $\sim$10 AU wide, while a $\sim$22 AU gap is opened by four 1 $M_{\rm J}$ planets |
| HL Tau-like model mm gap contrasts (inner to outer) | 1.5, 3.8, 1.8 | not stated | dimensionless | 3 | are 1.5, 3.8, and 1.8 from the innermost to the outermost gaps |

## Qualitative findings

- Planet-induced spiral arms are more apparent at NIR than at mm; inner-disk shadowing makes a circular gap appear off-center in inclined scattered-light images  
  > "When viewed at a moderate inclination angle, a physically circular on-centered gap could appear to be off-centered from the star due to shadowing." (abstract)

## Claim tuples

- H: Can a single low-mass planet produce a mm gap with no NIR gap? | E: Model 1x0.2MJ hydro+MCRT | R: mm gap contrast ~10; H-band contrast 1.02 | F: Consistent with transitional disks missing a NIR cavity | **supported**
- H: Do multiple planets open wide common gaps matching observed gap sizes and contrasts? | E: 4-planet models compared to published NIR gap contrasts | R: H-band contrast 3.5 and 6.0 vs observed ~3.3-4.2 | F: Planet gap scenario is promising | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): No instrumental effects/noise, no planet accretion or migration, no dust evolution; absolute intensities are only references  
  > "absolute values of $\Sigma_{\rm sg}$ and $\Sigma_{\rm bg}$ and the resulting absolute intensities of the images should be taken as references only" (2.2 Monte Carlo Radiative Transfer Simulations)
- Caveat (inferred, ours): Comparison with ALMA is only qualitative; no synthetic visibilities
- Caveat (inferred, ours): Results depend on assumed dust ratios and alpha

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Full Whitney code configuration
- Missing: Hydro floor and exact initial conditions
- Data volume (inferred): No ALMA data processed; simulations only
- Score (inferred): 3/5, Simulation setup largely described but relies on inherited setups and external codes; ALMA data not analysed.
- Rediscovery candidate: no, Theory paper; ALMA data only for qualitative comparison.

## Links

- Method: (cite: whitney13) (MCRT code)
- Method: (cite: zhu12) (two-fluid FARGO dust implementation)
- Companion: (cite: dong12cavity) (disk setup for MCRT)
- Related: ALMA HL Tau Science Verification (2011.0.00015.SV)

## Checks

```json
{
 "quotes": 29,
 "quotes_ok": 29,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 20,
  "rate": 0.299
 },
 "evidence_ok": true
}
```

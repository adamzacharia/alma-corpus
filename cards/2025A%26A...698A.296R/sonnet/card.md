# The impact of spiral arms on the star formation life cycle

`2025A&A...698A.296R` | Astronomy and Astrophysics 2025 | first author: Romanelli, Andrea | arXiv: 2505.10908 | DOI: 10.1051/0004-6361/202553895

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type archival_reuse

## Science

- Fields: nearby_galaxies, star_formation
- Question: Do spiral arms change cloud lifetimes, feedback timescales, region separation and integrated star formation efficiency compared with inter-arm regions?  
  > "We present here the cloud lifetimes, the duration of star formation, and the spatial distribution of star-forming regions in spiral arms and inter-arm regions of a sub-sample of 22 spiral galaxies" (1 Introduction)
- Target **22 PHANGS spiral galaxies (e.g. NGC 4321, NGC 628, NGC 1097)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00650.S, 2013.1.01161.S, 2015.1.00925.S, 2015.1.00956.S, 2017.1.00886.L
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: TP+7 m+12 m  
  > "The maps have been collected combining the extended and compact ALMA arrays (TP+7 m+12 m arrays)" (2.2 Molecular gas tracer)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~1 arcsec (~80-150 pc)  
  > "have a resolution of $\sim$1$''$, which translates into GMC-scale resolution ($\sim$80-150 pc)" (2.2 Molecular gas tracer)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (not stated)
- Other facility **PHANGS-Halpha (du Pont 2.5 m, MPG-ESO 2.2 m WFI)**: Continuum-subtracted narrow-band Halpha maps as SFR tracer  
  > "we use the continuum-subtracted narrow-band H$\alpha$ imaging from PHANGS–H$\alpha$ (Razza et al. in prep.)" (2.3 Star formation tracer)
- Other facility **Spitzer IRAC 3.6 um**: Basis of environmental masks  
  > "These environmental masks were constructed based on Spitzer IRAC $3.6~\mu$m observations, with a resolution of 1.7$''$." (2.4 Environmental masks)
- Other facility **GALEX and WISE W4**: Global SFR maps  
  > "we use SFR maps built from a combination of multi-wavelength observations from the Galaxy Evolution Explorer (GALEX) in the far-UV and the Wide-field Infrared Survey Explorer (WISE) W4 band" (2.5.1 Global star formation rate maps)
- External data: Environmental masks (spiral arm/inter-arm)  
  > "based on the environmental masks established by (cite: querejeta21)" (2.4 Environmental masks) [from (cite: querejeta21)]
- External data: PHANGS-MUSE metallicity maps  
  > "we use the PHANGS two-dimensional metallicity distribution (cite: williams22)." (2.5.2 Metallicity maps) [from (cite: williams22)]
- External data: Metallicity gradients for NGC 1097, 2997, 5248, 6744  
  > "we use the metallicity gradients measured by (cite: pilyugin14) when available" (2.5.2 Metallicity maps) [from (cite: pilyugin14)]
- External data: Previous cloud lifetime results updated  
  > "we also updated the results from (cite: kim22)" (3 Method) [from (cite: kim22)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Public PHANGS-ALMA moment-0 maps used  
  > "we use the public release version of the PHANGS–ALMA CO(2–1) (cite: Leroy2021a) moment-0 maps" (2.2 Molecular gas tracer)
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
- masking: 'broad' masking scheme, native resolution moment-0  
  > "moment-0 maps with the ’broad’ masking scheme at native resolution" (2.2 Molecular gas tracer)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: TP+7 m+12 m  
  > "(TP+7 m+12 m arrays)" (2.2 Molecular gas tracer)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Sample selection criteria and main input parameters  
  > "This selection follows the same criteria as in (cite: kim22)" (2.1 Sample selection) [from (cite: kim22)]
- HEISENBERG input parameters  
  > "For each galaxy, the main input parameters are listed in Table 1 of (cite: kim22)." (3 Method) [from (cite: kim22)]
- alpha_CO prescription  
  > "we adopt a metallicity-dependent $\alpha_{\rm CO}$ conversion factor, following (cite: sun20)" (2.5.3 alpha_CO conversion factor maps) [from (cite: sun20)]
- Diffuse emission filtering  
  > "filtering the large-scale emission from both CO(2-1) and H$\alpha$ maps using the method presented in (cite: hygate19)" (3 Method) [from (cite: hygate19)]

### Not stated but needed to reproduce (our reading)

- Galaxy distances and inclinations used
- Exact Gaussian kernel radii for enlarged arm masks
- Default HEISENBERG parameters not listed
- Halpha maps are unpublished (Razza et al. in prep.)
- Pixel-level SFR map construction details

## Analysis recipe

1. **Build CO and Halpha maps with environment masks and metallicity**: Mask maps into arms and inter-arms; compute CO-weighted metallicity and t_star,ref per environment  
  > "we applied the environmental masks to the metallicity maps, and we computed $t_{\rm star, ref}$ pixel by pixel." (3 Method)
   - assumption: R21 = 0.65; alpha_CO = 4.35 Z^-1.6; 50% error on alpha_CO/R21  
  > "where $R_{21} = 0.65$ is the CO(2–1)-to-CO(1–0) line ratio" (2.5.3 alpha_CO conversion factor maps)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive cloud lifecycle timescales**: Identify peaks, measure gas-to-SFR flux ratio in apertures, fit with HEISENBERG, iteratively filter diffuse emission  
  > "we first identified emission peaks in gas (here CO(2-1) emission) and SFR tracer (here H$\alpha$ emission) maps using the CLUMPFIND algorithm" (3 Method)
   - software: HEISENBERG, CLUMPFIND
   - parameter: apertures up to ~3000 pc; filter at n_lambda >~ 10; iterate until lambda stable for four iterations; mask width >= 1 kpc  
  > "until the derived separation scale $\lambda$ did not vary for four successive iterations." (3 Method)
   - fitting: Analytical function with three parameters (two timescales and separation length)  
  > "fitted by an analytical function that depends on three independent parameters" (3 Method)
   - validation: Slightly changing mask size gives similar results  
  > "Slightly increasing or decreasing the size of the masks leads to similar measurements of the cloud lifetime, feedback timescale, and $\lambda$." (3 Method)
3. **Compute integrated SFE**: eps_SF = t_CO / t_dep^comp using compact gas and unfiltered SFR  
  > "we calculated the integrated SFE per cloud as" (4.4 Star formation efficiency)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compare arms vs inter-arms statistically**: k-sample Anderson-Darling and paired Wilcoxon signed-rank tests  
  > "by conducting a k-sample Anderson-Darling (AD) test." (4 Results)
   - software: STATMODELS
   - fitting: KDE with Gaussian kernel for distributions  
  > "The distributions were estimated using a Kernel Density Estimation algorithm, with a Gaussian kernel" (4 Results)
   - validation: _not stated_

## Software

- **HEISENBERG** : Cloud life cycle statistical analysis  
  > "our analysis method implemented in the HEISENBERG code" (3 Method)
- **CLUMPFIND** : Peak identification  
  > "using the CLUMPFIND algorithm (cite: williams94)" (3 Method)
- **STATMODELS** : Kernel density estimation  
  > "provided by the Python module STATMODELS" (4 Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| AD test p-value, t_CO arms vs inter-arms | 0.52 | not stated | dimensionless | 4 | / $p$-value / 0.52 / 0.21 / 0.006 / 0.012 / |
| AD test p-value, lambda | 0.006 | not stated | dimensionless | 4 | / $p$-value / 0.52 / 0.21 / 0.006 / 0.012 / |
| Median lambda in spiral arms | ~175 | not stated | pc | 2 | with a median of ${\sim} 175$ pc |
| Median lambda in inter-arms | ~250 | not stated | pc | 2 | with a higher median (${\sim}250$ pc) |
| Median eps_SF arms | 2.9 | not stated | % | 3 | spiral arms having $[25,50,75]^{\rm th}$ percentiles of $[2.2,2.9,4.5]\%$ |
| Median eps_SF inter-arms | 3.8 | not stated | % | 3 | inter-arms have percentiles equal to $[3.3,3.8,6.6]\%$ |
| Cloud lifetime range | 5 to 40 | not stated | Myr | 2 | fall within the range 5 to 40 Myr |

## Qualitative findings

- Spiral arms collect gas but do not obviously trigger star formation  
  > "these observations do not provide evidence for a strong role of spiral arms in the star formation process in galaxies." (Discussion)

## Claim tuples

- H: Cloud lifetimes differ between arms and inter-arms | E: HEISENBERG on masked maps of 22 galaxies, AD and Wilcoxon tests | R: AD p=0.52, Wilcoxon p=0.85 | F: Clouds live equally long in both environments | **supported**
- H: Region separation differs between environments | E: Compare lambda | R: Arms median ~175 pc vs inter-arm ~250 pc | F: Regions are more closely packed in arms | **supported**
- H: Spiral arms enhance integrated SFE | E: Compare eps_SF | R: Inter-arms slightly higher (AD p~0.012) | F: SFE slightly lower in arms | **refuted**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Upper limits for lambda and t_fb in many arms; alpha_CO and R21 may differ between environments; diffuse ionised gas leakage may bias inter-arm SFE  
  > "systematic differences in the conversion factors $R_{21}$ or $\alpha_{\rm CO}$ between arms and inter-arm could affect this result" (4.4 Star formation efficiency)
- Caveat (inferred, ours): Upper limits used as values in statistical tests
- Caveat (inferred, ours): No extinction correction for Halpha
- Caveat (inferred, ours): Visually tuned mask enlargement
- Caveat (inferred, ours): Only 22 galaxies with small-number statistics

## Reproducibility

- Data public (paper): PHANGS-ALMA CO maps are public release; Halpha unpublished  
  > "we use the public release version of the PHANGS–ALMA CO(2–1)" (2.2 Molecular gas tracer)
- Products in archive: _not stated_
- Code: HEISENBERG is public on GitHub  
  > "has been provided as a publicly available framework in the form of the HEISENBERG code" (3 Method)
- Missing: Halpha maps (Razza et al. in prep.)
- Missing: Per-galaxy HEISENBERG inputs in Kim et al. 2022
- Missing: Galaxy distances and inclinations
- Data volume (inferred): ~ few GB of moment maps
- Score (inferred): 3/5, Public CO maps and public code, but Halpha maps and many inputs are inherited or unpublished.
- Rediscovery candidate: no, Halpha data not yet public and inputs inherited from Kim et al. 2022.

## Links

- Method: (cite: kruijssen18) (HEISENBERG method)
- Method: (cite: kim22) (Sample and inputs)
- Method: (cite: hygate19) (Diffuse emission filtering)
- Companion: (cite: querejeta21) (Environmental masks)
- Companion: (cite: Leroy2021a) (PHANGS-ALMA CO data)
- Related: PHANGS-ALMA
- Related: PHANGS-MUSE
- Related: PHANGS-Halpha

## Checks

```json
{
 "quotes": 50,
 "quotes_ok": 50,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 5,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 33,
  "rate": 0.446
 },
 "evidence_ok": true
}
```

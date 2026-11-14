# Star Formation Efficiency per Free-fall Time in nearby Galaxies

`2018ApJ...861L..18U` | The Astrophysical Journal Letters 2018 | first author: Utomo, Dyas | arXiv: 1806.11121 | DOI: 10.3847/2041-8213/aacf8f

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation
- Question: What is the star formation efficiency per free-fall time (eps_ff) in nearby galaxies, from GMC-scale CO maps combined with molecular gas depletion times?  
  > "we estimate the gravitational free-fall time at 60 to 120 pc resolution, and contrast this with the local molecular gas depletion time to estimate $\epsilon_{\rm ff}$." (abstract)
- Target **PHANGS-ALMA sample (11 galaxies) plus M31, M33, M51**: coordinates _not stated_; z/distance 0.8-17.6 Mpc (Table 2)  
  > "We estimate molecular gas surface density from PHANGS-ALMA CO (2–1) data for $11$ targets and archival CO data for M31 (cite: CALDUPRIMO16), M33 (cite: DRUARD14), and M51 (cite: SCHINNER13)." (2.1 Molecular Gas); "Aliases for NGC 224, NGC 598, and NGC 5194 are M31, M33, and M51, respectively." (Table 2); distance from not stated in text; EDD (Tully09) and HyperLeda acknowledged  
  > "We estimate molecular gas surface density from PHANGS-ALMA CO (2–1) data for $11$ targets and archival CO data for M31 (cite: CALDUPRIMO16), M33 (cite: DRUARD14), and M51 (cite: SCHINNER13)." (2.1 Molecular Gas); "Aliases for NGC 224, NGC 598, and NGC 5194 are M31, M33, and M51, respectively." (Table 2)

## Data provenance

- ALMA projects: 2013.1.00925.S, 2011.1.00650.S, 2013.1.00956.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: ALMA 12m, 7m and total power  
  > "PHANGS-ALMA uses ALMA’s 12m, 7m, and total power antennas to map CO (2–1) emission" (2.1 Molecular Gas)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: native 1-1.5 arcsec, ~60-120 pc  
  > "at native angular resolution of $1-1.5\ensuremath{''}$. This translates to native physical resolutions of $\sim~60{-}120$ pc" (2.1 Molecular Gas)
- max recoverable scale: sensitive to all spatial scales (ACA + total power)  
  > "we expect these maps to be sensitive to emission at all spatial scales." (2.1 Molecular Gas)
- sensitivity: rms ~0.1 K per 2.5 km/s channel  
  > "the CO data cubes have rms noise of $\sim0.1$ K per $2.5$ km s$^{-1}$ channel." (2.1 Molecular Gas)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (not stated)
- Other facility **WISE/unWISE**: 12 and 22 micron maps for SFR  
  > "The WISE maps are derived from the unWISE reprocessing of (cite: LANG14)." (2.2 Recent Star Formation)
- Other facility **GALEX**: FUV and NUV maps for SFR  
  > "The GALEX maps are coadded, convolved, background subtracted maps constructed from the full-mission GALEX archive" (2.2 Recent Star Formation)
- Other facility **Spitzer 3.6 micron**: stellar mass surface density  
  > "dust-corrected *Spitzer* $3.6\ensuremath{\mu}m$ maps produced by (cite: QUEREJETA15)" (3.3 Thickness of the Molecular Gas Layer)
- Other facility **VLT-MUSE**: metallicities for NGC 1672, 3627, 4535  
  > "K. Kreckel et al. in preparation based on new VLT-MUSE observations" (2.1 Molecular Gas)
- External data: CO surface brightness, line-width, masking, completeness  
  > "where the CO surface brightness and line-width have been calculated by (cite: SUN18)." (2.1 Molecular Gas) [from (cite: SUN18)]
- External data: Archival CO maps of M31  
  > "archival CO data for M31 (cite: CALDUPRIMO16)" (2.1 Molecular Gas) [from (cite: CALDUPRIMO16)]
- External data: Archival CO map of M33  
  > "M33 (cite: DRUARD14)" (2.1 Molecular Gas) [from (cite: DRUARD14)]
- External data: Archival CO map of M51 (PAWS)  
  > "M51 (cite: SCHINNER13)" (2.1 Molecular Gas) [from (cite: SCHINNER13)]
- External data: Metallicities compiled  
  > "We use metallicities compiled by (cite: PILYUGIN04)" (2.1 Molecular Gas) [from (cite: PILYUGIN04); (cite: RS08); (cite: CROXALL15)]
- External data: Stellar mass maps from Spitzer 3.6 micron  
  > "dust-corrected *Spitzer* $3.6\ensuremath{\mu}m$ maps produced by (cite: QUEREJETA15)" (3.3 Thickness of the Molecular Gas Layer) [from (cite: QUEREJETA15)]
- External data: SFR calibration coefficients K  
  > "(cite: KENNICUTT12; JARRETT13)" (2.2 Recent Star Formation) [from (cite: KENNICUTT12; JARRETT13)]

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
- smoothing: CO maps convolved to 60, 80, 100, 120 pc and 1.3 kpc round Gaussian beams  
  > "Here, $\Sigma_{\rm mol, 1.3 kpc}$ is the convolved $\Sigma_{\rm mol}$ at 1.3 kpc FWHM to match the resolution of $\Sigma_{\rm SFR, 1.3 kpc}$ maps." (3.1 Molecular Gas Depletion Time)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Sample selection, observing strategy, reduction of PHANGS-ALMA  
  > "The sample selection, observing strategy, reduction, and properties of the full $74$ galaxies in PHANGS-ALMA survey is presented in A. K. Leroy et al. (in preparation)." (2.1 Molecular Gas) [from A. K. Leroy et al. (in preparation)]
- Masking, map construction, completeness  
  > "See that paper for a detailed presentation of masking, map construction, and completeness." (2.1 Molecular Gas) [from (cite: SUN18)]
- SFR maps from WISE and GALEX  
  > "We derive the star formation rate (SFR) surface density, $\Sigma_{\rm SFR}$, from WISE infrared and GALEX UV maps (A. K. Leroy et al. in preparation)." (2.2 Recent Star Formation) [from A. K. Leroy et al. (in preparation)]
- Metallicity-dependent alpha_CO prescription  
  > "We calculate the metallicity-dependent $\alpha_{\rm CO}$ following the prescription of (cite: BOLATTO13)." (2.1 Molecular Gas) [from (cite: BOLATTO13)]
- Hydrostatic H formula  
  > "following (cite: OSTRIKER10)." (3.3 Thickness of the Molecular Gas Layer) [from (cite: OSTRIKER10)]

### Not stated but needed to reproduce (our reading)

- Exact PHANGS-ALMA calibration/imaging pipeline and CASA version
- Which projects map to which galaxies
- Completeness correction function f_C(C) tabulated form
- Details of the convolution kernel for deconvolving beams to target resolutions
- Exact SFR map processing, which galaxies use WISE 3.4 micron stellar masses
- Spearman correlation details

## Analysis recipe

1. **CO to molecular gas surface density**: Convert CO integrated intensity with fixed alpha_CO and inclination correction  
  > "We adopt a fixed CO(2–1)-to-H$_2$ conversion factor $\alpha_{\rm CO}^{2-1} = 6.2$ M$_\odot$ pc$^{-2}$ (K km s$^{-1}$)$^{-1}$." (2.1 Molecular Gas)
   - parameter: alpha_CO(2-1)=6.2; alpha_CO(1-0)=4.35 for M31 and M51  
  > "For those we use $\alpha_{\rm CO}^{1-0} = 4.35$ M$_\odot$ pc$^{-2}$ (K km s$^{-1}$)$^{-1}$ with no line ratio term." (2.1 Molecular Gas)
   - assumption: CO(2-1)/CO(1-0) = 0.7  
  > "with a typical CO(2–1)/CO(1–0) line ratio of 0.7" (2.1 Molecular Gas)
   - fitting: _not stated_
   - validation: Metallicity-dependent alpha_CO tested  
  > "We explore the effect of a metallicity-dependent $\alpha_{\rm CO}$ on our results for these cases." (2.1 Molecular Gas)
2. **SFR surface density and depletion time at 1.3 kpc**: Sigma_SFR = K I_nu with FUV+22um benchmark; tau_dep = Sigma_mol/Sigma_SFR at 1.3 kpc  
  > "We use hybrid tracers by adding the SFR derived from each choice of UV and IR band, and adopt SFR(FUV+22$\mu$m) as a benchmark." (2.2 Recent Star Formation)
   - parameter: K=1.04e-1 (FUV), 1.04e-1 (NUV), 3.77e-3 (12um), 2.97e-3 (24um)  
  > "$K=1.04 \times 10^{-1}$, $1.04 \times 10^{-1}$, $3.77 \times 10^{-3}$, and $2.97 \times 10^{-3}$ for FUV, NUV, 12$\mu$m, and 24$\mu$m bands, respectively" (2.2 Recent Star Formation)
   - fitting: _not stated_
   - validation: NUV and 12um tested as alternatives  
  > "we test the effect of using NUV instead of FUV and using 12$\mu$m instead of 22$\mu$m." (2.2 Recent Star Formation)
3. **Free-fall time at 60-120 pc**: tau_ff = sqrt(3 pi H /(32 G Sigma_mol)) with rho = Sigma_mol/H  
  > "we combine our measured, high physical resolutions ($60{-}120$ pc) $\Sigma_{\rm mol}$ with an estimate of the line-of-sight depth through the molecular gas layer, $H$" (3.2 Molecular Gas Free Fall Time)
   - parameter: Default H = 100 pc; alternatives hydrostatic (h*=300 pc, M/L=0.5; median H 122 pc) and virial cloud (alpha_vir~2; median H 116 pc)  
  > "*Fixed $H=100$ pc.* This is roughly the diameter of a large molecular cloud" (3.3 Thickness of the Molecular Gas Layer)
   - fitting: _not stated_
   - validation: Compare eps_ff across three H prescriptions  
  > "We calculate $H$ using each method above and compare the resulting $\epsilon_{\rm ff}$ to estimate the systematic uncertainty associated with estimating $H$." (3.3 Thickness of the Molecular Gas Layer)
4. **Combine scales**: Mass-weighted mean of tau_ff^-1 within each 1.3 kpc beam via convolution  
  > "we calculate the mass-weighted average of $\tau_{\rm ff}$ within each $1.3$ kpc region of a galaxy." (3.4 Combining Scales)
   - assumption: <tau_ff>^-1 ≈ <tau_ff^-1>  
  > "Hereby, we assume that $\left<\tau_{\rm ff, 60 pc}\right>_{\rm 1.3 kpc}^{-1} \approx \left<\tau_{\rm ff, 60 pc}^{-1}\right>_{\rm 1.3 kpc}$." (3.4 Combining Scales)
   - fitting: _not stated_
   - validation: Differs from Leroy17 approach by ~7% in tau_ff  
  > "with the mean $\left<\mbox{$\tau_{\rm ff}$}_{\rm ,60pc}\right>_{\rm 1.3 kpc}$ differing by only $\sim 7\%$." (3.4 Combining Scales)
5. **Incompleteness correction and eps_ff**: Monte Carlo of lognormal Sigma_mol distribution gives f_C(C); eps_ff = <tau_ff>/tau_dep  
  > "We randomly draw $10^6$ samples from a lognormal distribution designed to simulate the true distribution of mass as a function of $\Sigma_{\rm mol}$" (3.6 Correction for Incompleteness)
   - parameter: lognormal width 0.5 dex, 10^6 samples  
  > "These model distributions have $1\sigma$ width of $0.5$ dex." (3.6 Correction for Incompleteness)
   - fitting: _not stated_
   - validation: Systematics explored by varying SFR tracer, H, completeness, alpha_CO, resolution  
  > "where we vary our adopted SFR tracer, the line-of-sight depth, completeness correction, the CO-to-H$_2$ conversion factor, and linear resolution." (4.1 Uncertainties)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median eps_ff at 120 pc | 0.7% | 16-84%: 0.4-1.1% | percent | 5 | we find median $\mbox{$\epsilon_{\rm ff}$}\approx 0.7\%$ across all lines-of-sight in $14$ galaxies |
| Median eps_ff with equal galaxy weighting | 0.8% | not stated | percent | 5 | then $\mbox{$\epsilon_{\rm ff}$}\approx 0.8\%$ |
| Median eps_ff at 60 pc | 0.63% | 16-84%: 0.40-1.00% | percent | 5 | Median of $\left<\epsilon_{\rm ff}\right>$     / $0.63\%$ |
| Galaxy-to-galaxy eps_ff range | 0.3-2.6% | not stated | percent | 5 | with the median $\epsilon_{\rm ff}$ ranging from $0.3\%$ to $2.6\%$ |
| Median tau_dep at 120 pc | 1.69 | 16-84%: 1.11-2.35 | Gyr | 2 | Median of $\tau_{\rm dep}$ \[Gyr\]                               / 1.72       / 1.72       / 1.77       / 1.69 |
| Median tau_ff at 120 pc | 11.79 | 16-84%: 7.57-15.59 | Myr | 4 | Median of $\left<\tau_{\rm ff}\right>$ \[Myr\]                   / 11.16      / 12.68      / 12.54      / 11.79 |
| Spearman correlation eps_ff vs stellar mass (excl. M31) | -0.75 | not stated | dimensionless | 5 | (Spearman rank correlation coefficient, $r_s \approx -0.75$) |
| Systematic uncertainty on eps_ff | ~0.1 | not stated | dex | 5 | systematic effects can shift $\epsilon_{\rm ff}$ by $\sim 0.1$ dex. |

## Qualitative findings

- eps_ff mildly increases with coarser resolution (~0.1 dex from 60 to 120 pc)  
  > "changing the resolution from 60 to 120 pc increases $\epsilon_{\rm ff}$ by $\sim 0.1$ dex." (4.1 Uncertainties)
- M51 has the lowest eps_ff in the sample  
  > "M51 has the lowest $\epsilon_{\rm ff}$ of any galaxy in our sample." (4.2 Comparison to Previous Studies)

## Claim tuples

- H: What is the typical eps_ff across nearby galaxies? | E: tau_ff from 60-120 pc CO maps vs tau_dep at 1.3 kpc, 14 galaxies | R: median eps_ff ≈ 0.7%, 16-84%: 0.4-1.1% | F: eps_ff is low, ~1% or below, consistent with theory | **supported**
- H: Does eps_ff vary between galaxies? | E: per-galaxy medians at 120 pc | R: 0.3-2.6% range; higher in low-mass galaxies | F: eps_ff anti-correlates with stellar mass, partly explained by metallicity-dependent alpha_CO | **partially**
- H: How large are systematics? | E: vary SFR tracer, H, completeness, alpha_CO, resolution | R: shifts ≲0.1 dex | F: systematics dominated by H and SFR tracer | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Surface density at high resolution relates to mean volume density, giving tau_ff directly  
  > "These observations recover the surface density of molecular gas at high physical resolution, which is closely related to the mean volume density." (1 Introduction)
- Alternative: Hydrostatic-equilibrium and virial-cloud estimates of H  
  > "We explore three approaches:" (3.3 Thickness of the Molecular Gas Layer)
- How they decided it was enough: _not stated_
- Limitation (authors): Low-mass galaxy measurements subject to biases; central alpha_CO variation deferred  
  > "though we caution that both measurements are subject to biases in low mass galaxies." (abstract)
- Caveat (inferred, ours): Fixed H=100 pc dominates the result
- Caveat (inferred, ours): tau_dep at 1.3 kpc mixed with 60-120 pc tau_ff
- Caveat (inferred, ours): Fixed alpha_CO and line ratio
- Caveat (inferred, ours): No formal statistical uncertainty propagation

## Reproducibility

- Data public (paper): ALMA project codes acknowledged  
  > "This Letter makes use of the following ALMA data: ADS/JAO.ALMA #2013.1.00925.S #2011.1.00650.S, and #2013.1.00956.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: PHANGS-ALMA reduction and map products (in preparation papers)
- Missing: Sun et al. 2018 masks and completeness
- Missing: SFR maps
- Data volume (inferred): ~100s GB raw; processed maps small
- Score (inferred): 3/5, Recipe is clear and numeric, but depends on unreleased PHANGS maps and companion papers.
- Rediscovery candidate: no, Depends on processed maps and SFR products from papers in preparation.

## Links

- Method: (cite: SUN18) (CO maps, masking, completeness)
- Method: (cite: LEROY17) (Similar eps_ff method in M51)
- Companion: A. K. Leroy et al. (in preparation) (PHANGS-ALMA survey and SFR maps)
- Related: PHANGS-ALMA
- Related: PAWS

## Checks

```json
{
 "quotes": 64,
 "quotes_ok": 64,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2013.1.00925.S",
  "2011.1.00650.S",
  "2013.1.00956.S"
 ],
 "obscore_codes_not_in_card": [
  "2012.1.00650.S",
  "2015.1.00925.S",
  "2015.1.00956.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 84,
  "stated": 46,
  "rate": 0.548
 },
 "evidence_ok": true
}
```

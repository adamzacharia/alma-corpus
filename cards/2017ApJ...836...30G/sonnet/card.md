# Nitrogen Fractionation in Protoplanetary Disks from the H<SUP>13</SUP>CN/HC<SUP>15</SUP>N Ratio

`2017ApJ...836...30G` | The Astrophysical Journal 2017 | first author: Guzmán, V. V. | arXiv: 1701.07510 | DOI: 10.3847/1538-4357/836/1/30

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: What are the disk-averaged and radially resolved 14N/15N ratios in HCN in protoplanetary disks, and do they match comets and the cold ISM or show signs of in-disk fractionation?  
  > "With ALMA it is for the first time possible to directly measure $\mathrm{^{14}N/^{15}N}$ ratios in common molecules during assembly of planetary systems." (abstract)
- Target **AS 209**: coordinates _not stated_; z/distance 126 pc  
  > "| AS 209    | 126       | K5        | 1.6       | 0.9                | 1.5                | 51" (Table 2); distance from Table reproduced from huang2017  
  > "| AS 209    | 126       | K5        | 1.6       | 0.9                | 1.5                | 51" (Table 2)
- Target **IM Lup**: coordinates _not stated_; z/distance 161 pc  
  > "| IM Lup    | 161       | M0        | 1         | 1.0" (Table 2); distance from Table reproduced from huang2017  
  > "| IM Lup    | 161       | M0        | 1         | 1.0" (Table 2)
- Target **LkCa 15**: coordinates _not stated_; z/distance 140 pc  
  > "| LkCa 15   | 140       | K3        | 3-5" (Table 2); distance from Table reproduced from huang2017  
  > "| LkCa 15   | 140       | K3        | 3-5" (Table 2)
- Target **V4046 Sgr**: coordinates _not stated_; z/distance 72 pc  
  > "| V4046 Sgr | 72        | K5,K7     | 24" (Table 2); distance from Table reproduced from huang2017  
  > "| V4046 Sgr | 72        | K5,K7     | 24" (Table 2)
- Target **MWC 480**: coordinates _not stated_; z/distance 142 pc  
  > "| MWC 480   | 142       | A4        | 7" (Table 2); distance from Table reproduced from huang2017  
  > "| MWC 480   | 142       | A4        | 7" (Table 2)
- Target **HD 163296**: coordinates _not stated_; z/distance 122 pc  
  > "| HD 163296 | 122       | A1        | 4" (Table 2); distance from Table reproduced from huang2017  
  > "| HD 163296 | 122       | A1        | 4" (Table 2)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 6, two spectral settings at 1.1 and 1.4 mm  
  > "The Band 6 observations included two spectral settings, at 1.1 and 1.4 mm." (Observations and data reduction)
- frequencies and spectral setup: HCN isotopologues in two 59 MHz spectral windows with 61 kHz channels (1.1 mm setting); CO isotopologues in three windows (1.4 mm)  
  > "The HCN isotopologue lines were covered by two spectral windows of 59 MHz bandwidth and 61 kHz channel width in the 1.1 mm spectral setting." (Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 18 to 650 m  
  > "with baseline lengths spanning between 18 and 650 m" (Observations and data reduction)
- angular resolution: ~0.5 arcsec  
  > "We have presented ALMA observations at $\sim0''.5$ angular resolution" (Conclusions)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 20 min on average  
  > "The total on-source time was 20 min, on average." (Observations and data reduction)
- observing dates: between 2014 and 2015 (Cycle 2)  
  > "the Band 6 observations were carried-out between 2014 and 2015" (Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: H13CN J=3-2 (259.0118 GHz)
- Line: HC15N J=3-2 (258.1571 GHz)
- External data: Stellar and disk properties (distance, mass, inclination, PA, v_LSR etc.)  
  > "Note: Table reproduced from (cite: huang2017), where a complete list of references is given." (Table 2) [from (cite: huang2017)]
- External data: DCN/HCN ratios for comparison with 14N/15N  
  > "compares it with DCN/HCN ratios derived by (cite: huang2017)" (Sample statistics) [from (cite: huang2017)]

## Processing

### Calibration

- pipeline or manual: Calibrated by ALMA staff with standard procedures  
  > "The data calibration was performed by the ALMA staff using standard procedures." (Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan for about half the observations, or a quasar  
  > "The absolute flux scale was derived by observing Titan for about half the observations, or a quasar." (Observations and data reduction)
- flux scale uncertainty: _not stated_
- self calibration: Self-calibration on continuum; solutions per spw for AS 209, LkCa 15, MWC 480, V4046 Sgr, on averaged spws for IM Lup and HD 163296  
  > "The self-calibration solutions were derived on individual spectral windows when possible (AS 209, LkCa 15, MWC 480 and V4046 Sgr) and on averaged spectral windows for the weaker sources (IM Lup and HD 163296)" (Observations and data reduction)

### Imaging

- task: CLEAN in CASA with Briggs weighting  
  > "using the CLEAN algorithm with Briggs weighting" (Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: H13CN robust 1.0 (IM Lup 2.0); HC15N robust 2.0 (V4046 Sgr and MWC 480 1.0); CO isotopologues 0.5  
  > "The robust parameter was set to 1.0 for $\mathrm{H^{13}CN}$, except for IM Lup where we used a value of 2.0." (Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Elliptical masks from disk inclination and PA, centered on continuum centroid, same for all channels; Keplerian mask for CO  
  > "we created elliptical masks, same for all channels, centered on the dust continuum centroid, using the disk inclination and position angle" (Observations and data reduction)
- multiscale scales: _not stated_
- continuum subtraction: Continuum subtracted from visibilities  
  > "The continuum was then subtracted from the visibilities to produce the spectral line cubes." (Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Regridded to 0.5 km/s resolution (0.2 km/s for V4046 Sgr modeling)  
  > "The HCN isotopologue data was regridded to a spectral resolution of $0.5\ensuremath{\mathrm{\,km\,s^{-1}}}$ for the full sample." (Observations and data reduction)
- final beam: e.g. V4046 Sgr H13CN 0.60x0.48 arcsec, PA 87.3  
  > "| V4046 Sgr | $0.60\times 0.48$ | $87.3$" (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- Detailed observation description (calibration, setup)  
  > "The observations are described in detail by (cite: huang2017)." (Observations and data reduction) [from (cite: huang2017)]
- Disk physical structure model parametrization  
  > "based on the model described in (cite: rosenfeld2013)" (Disk physical structure) [from (cite: rosenfeld2013)]
- Gas temperature parametrization  
  > "following (cite: dartois2003)" (Disk physical structure) [from (cite: dartois2003)]

### Not stated but needed to reproduce (our reading)

- Self-calibration solution intervals and reference spws
- Line-free channels and continuum-subtraction fit order
- Cell size, image size, clean threshold, niter
- Which quasars were bandpass/phase calibrators
- Flux extraction velocity range and mask radii per source
- MCMC walkers, steps and burn-in
- Flux calibration uncertainty

## Analysis recipe

1. **Image H13CN and HC15N cubes**: Self-calibrate on continuum, subtract continuum, CLEAN with Briggs weighting and elliptical masks  
  > "The clean images were obtained by deconvolving the visibilities in CASA, using the CLEAN algorithm with Briggs weighting." (Observations and data reduction)
   - software: CASA
   - parameter: 0.5 km/s channels; robust 1.0 or 2.0  
  > "For $\mathrm{HC^{15}N}$ the robust parameter was set to 2.0 to improve the signal-to-noise ratio" (Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure disk-integrated line fluxes**: Integrate unclipped moment-zero maps within elliptical mask; uncertainty from same mask at random signal-free positions  
  > "The uncertainty in the flux was estimated by simulating integrated flux measurements from signal free regions using the same elliptical mask but centered at random positions." (Sample statistics)
   - parameter: Detection: Keplerian emission in at least three channels at 3 sigma  
  > "emission consistent with the expected Keplerian rotation of the disk is observed in at least three channels at a $3\sigma$ level" (Sample statistics)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive 14N/15N from flux ratios**: Flux ratio converted to abundance ratio assuming LTE, optically thin, then multiplied by 12C/13C  
  > "We compute the $\ensuremath{\mathrm{H^{13}CN}}/\ensuremath{\mathrm{HC^{15}N}}$ abundance ratio in the LTE case and for $\ensuremath{T_\ensuremath{\mathrm{ex}}}=15$ K." (Sample statistics)
   - parameter: 12C/13C = 70 with 30% uncertainty; Tex = 15 K  
  > "we adopt an isotopic ratio of $\ensuremath{\mathrm{^{12}C/^{13}C}}=70$" (Sample statistics)
   - assumption: Lines optically thin, co-spatial, in LTE  
  > "line emission is expected to be optically thin, arise in the same region and this region is dense enough for the molecular rotational population to be in LTE" (Sample statistics)
   - fitting: _not stated_
   - validation: Tex of 100 K changes abundances by <1%  
  > "a higher excitation temperature of 100 K changes the inferred abundances by less than 1%" (Sample statistics)
4. **Build V4046 Sgr disk structure model**: Parametric dust surface density and scale height; RADMC-3D dust temperature; parametrized gas temperature; hydrostatic gas density  
  > "the radiative transfer code RADMC-3D (cite: dullemond2012) was then used to compute the dust temperature throughout the disk." (Disk physical structure)
   - software: RADMC-3D, OpacityTool
   - parameter: Table 3 parameters: H10=0.4 AU, h=1.25, Sigma_c=0.226 g/cm2, r_c=75 AU, r_cav=3 AU, T10=200 K, q_atm=0.8, delta=2  
  > "| Dust surface density | $\Sigma_c$     | 0.226 g cm$^{-2}$ |" (Table 3)
   - assumption: Gas-to-dust ratio of 100  
  > "we assume a vertically integrated gas-to-dust ratio at each radii of 100" (Disk physical structure)
   - fitting: _not stated_
   - validation: Reproduces 12CO, 13CO and C18O emission  
  > "This model reproduces the main features of the $^{12}$CO, $^{13}$CO and C$^{18}$O emission" (Disk physical structure)
5. **Fit H13CN and HC15N abundance profiles in V4046 Sgr**: Power-law abundance X0(r/100 AU)^alpha with R_out=100 AU; model visibilities via vis_sample compared in uv plane; MCMC  
  > "The likelihood function is then computed in the $u-v$ plane, by computing the weighted difference between model and observations" (Abundance fitting)
   - software: vis_sample, emcee, RADMC-3D, LIME
   - parameter: 0.2 km/s resolution, 60 channels; flat priors -3<alpha<2 and 1e-20<X<1e-8  
  > "we included a flat prior for the power-law index $-3<\alpha<2$, and for the molecular abundance $10^{-20}<X_{100}<10^{-8}$" (Abundance fitting)
   - assumption: LTE level populations; disk structure fixed  
  > "The disk physical structure, that is the gas density and temperature, are fixed in the line fitting." (Abundance fitting)
   - fitting: emcee MCMC, flat priors, likelihood on real and imaginary visibilities  
  > "We sample the posterior distribution with the MCMC method implemented in the `e`mcee package" (Abundance fitting)
   - validation: Non-LTE check with LIME; R_out 200 AU gives same result; residual channels  
  > "We checked that non-LTE effects are not important for these lines using the non-LTE radiative transfer code LIME" (Abundance fitting)

## Software

- **CASA** : Imaging/CLEAN  
  > "deconvolving the visibilities in CASA" (Observations and data reduction)
- **RADMC-3D** : Dust temperature and level populations  
  > "the radiative transfer code RADMC-3D (cite: dullemond2012) was then used to compute the dust temperature" (Disk physical structure)
- **OpacityTool** : Dust opacities (DIANA)  
  > "computed using the `O`pacityTool[^1] from the DIANA project" (Disk physical structure)
- **vis_sample** : Sampling model on observed uv points  
  > "We use the `v`is_sample Python package" (Abundance fitting)
- **emcee** : MCMC posterior sampling  
  > "MCMC method implemented in the `e`mcee package" (Abundance fitting)
- **LIME** : Non-LTE check  
  > "using the non-LTE radiative transfer code LIME (cite: brinch2010)" (Abundance fitting)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| H13CN flux V4046 Sgr | 1098 | 35 | mJy km/s | 2 | / V4046 Sgr / $1098\pm 35$ / $670\pm 26$ / $1.6\pm 0.1$ / $115\pm 35$ / |
| 14N/15N AS 209 | 156 | 71 | dimensionless | 3 | / AS 209 / $175\pm 25$ / $79\pm 23$ / $2.2\pm 0.7$ / $156\pm 71$ / |
| 14N/15N LkCa 15 | 83 | 32 | dimensionless | 3 | / LkCa 15 / $120\pm 20$ / $101\pm 18$ / $1.2\pm 0.3$ / $83 \pm 32$ / |
| 14N/15N V4046 Sgr | 115 | 35 | dimensionless | 3 | / V4046 Sgr / $1098\pm 35$ / $670\pm 26$ / $1.6\pm 0.1$ / $115\pm 35$ / |
| 14N/15N MWC 480 | 123 | 45 | dimensionless | 3 | / MWC 480 / $132\pm 13$ / $75\pm 13$ / $1.8\pm 0.3$ / $123\pm 45$ / |
| 14N/15N HD 163296 | 142 | 59 | dimensionless | 3 | / HD 163296 / $177\pm 23$ / $87\pm 21$ / $2.0\pm 0.6$ / $142\pm 59$ / |
| H13CN abundance fit X0 and alpha, V4046 Sgr | X0=8.94e-13, alpha=-0.69 | 0.30e-13, 0.03 | relative to total H; dimensionless | 5 | $X_0=8.94\pm0.30\times10^{-13}$ and $\alpha=-0.69\pm0.03$ for $\mathrm{H^{13}CN}$ |
| HC15N abundance fit X0 and alpha, V4046 Sgr | X0=3.37e-13, alpha=-1.08 | 0.19e-13, 0.04 | relative to total H; dimensionless | 5 | $X_0=3.37\pm0.19\times10^{-13}$ and $\alpha=-1.08\pm0.04$ for $\mathrm{HC^{15}N}$ |
| 14N/15N in V4046 Sgr at 10 and 50 AU | 76 and 142 | 25 and 47 | dimensionless | 5 | we infer an abundance $\mathrm{^{14}N/^{15}N}$ ratio of $76\pm25$ and $142\pm47$, at 10 and 50 AU respectively |

## Qualitative findings

- H13CN detected in 5/6 disks; HC15N weakly detected in AS 209 and LkCa 15; neither detected in IM Lup  
  > "$\mathrm{HC^{15}N}$ is clearly detected toward V4046 Sgr, MWC 480 and HD 163296, weakly detected toward AS 209 and LkCa 15, and not detected toward IM Lup." (Sample statistics)

## Claim tuples

- H: Disk-averaged HCN 14N/15N is comet-like and independent of stellar type or disk structure | E: H13CN/HC15N flux ratios in six disks with 12C/13C=70 | R: 14N/15N of 83-156 in 5 disks, no systematic differences | F: Disk-averaged fractionation is similar to comets and cold ISM, consistent with inheritance | **supported**
- H: Nitrogen and hydrogen fractionation correlate if from cold pathway | E: Compare 14N/15N with DCN/HCN from huang2017 | R: No correlation | F: Cold ion-molecule fractionation does not alone set the ratio | **partially**
- H: 14N/15N varies radially in V4046 Sgr | E: Abundance profile fitting with emcee | R: 14N/15N 76 at 10 AU, 142 at 50 AU | F: Tentative evidence of selective photodissociation in inner disk | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: H13CN used as proxy because HCN may be optically thick  
  > "Because the HCN lines may be optically thick, we use the $\mathrm{H^{13}CN}$ line as a proxy of HCN to derive the $\mathrm{^{14}N/^{15}N}$ ratio." (Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Spread in 14N/15N small compared to errors; trends may be washed out; ratio beyond 60 AU uncertain  
  > "We note that the spread in $\mathrm{^{14}N/^{15}N}$ is small compared to the errors and we cannot rule out that there is a trend that is washed out by the noise." (Sample statistics)
- Caveat (inferred, ours): Constant 12C/13C=70 assumed for all disks
- Caveat (inferred, ours): LTE with fixed Tex=15 K and optically thin assumption
- Caveat (inferred, ours): Radial result rests on one disk with fixed physical model
- Caveat (inferred, ours): Flux calibration errors excluded from uncertainties

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Full self-cal and imaging parameters
- Missing: MCMC run settings
- Missing: Calibrator names and per-source mask radii
- Data volume (inferred): ~50-100 GB raw for six disks
- Score (inferred): 3/5, Public ALMA data and clear flux-ratio method; imaging and MCMC details partly missing and heavy reliance on huang2017.
- Rediscovery candidate: yes, Data are from an archival Cycle 2 project, the flux-ratio recipe is simple, and the results are numeric.

## Links

- Method: (cite: huang2017) (Detailed observation description and the same data)
- Method: (cite: rosenfeld2013) (Disk structure model)
- Companion: (cite: guzman2015) (First H13CN/HC15N measurement in MWC 480)
- Companion: (cite: oberg2015a) (DCO+ in IM Lup from same data)
- Companion: (cite: oberg2015b) (CH3CN in MWC 480 from same data)
- Related: ADS/JAO.ALMA#2013.1.00226

## Checks

```json
{
 "quotes": 74,
 "quotes_ok": 74,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2013.1.00226.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 94,
  "stated": 59,
  "rate": 0.628
 },
 "evidence_ok": true
}
```

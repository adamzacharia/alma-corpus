# Constraints on the Cosmic-Ray Ionization Rate in the z ∼ 2.3 Lensed Galaxies SMM J2135-0102 and SDP 17b from Observations of OH<SUP>+</SUP> and H<SUB>2</SUB>O<SUP>+</SUP>

`2018ApJ...865..127I` | The Astrophysical Journal 2018 | first author: Indriolo, Nick | arXiv: 1808.04852 | DOI: 10.3847/1538-4357/aad7b3

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, astrochemistry
- Question: What are the cosmic-ray ionization rates in lensed z~2.3 SMGs, inferred from OH+ and H2O+ absorption combined with a chemical model?  
  > "Our goal is to infer the cosmic-ray ionization rate in SMGs at $z\sim2.3$ to better understand the impact of prolific star formation on the gas reservoirs in these massive galaxies" (Introduction)
- Target **SMM J2135-0102 (Eyelash)**: coordinates _not stated_; z/distance z = 2.3259  
  > "| Eyelash | SMM J2135$-$0102 | 2.3259 | S10 |" (Table 1); distance from S10 (cite: swinbank2010)  
  > "| Eyelash | SMM J2135$-$0102 | 2.3259 | S10 |" (Table 1)
- Target **SDP 17b**: coordinates _not stated_; z/distance z = 2.3051  
  > "| SDP 17b | H-ATLAS J090302.9$-$014127 | 2.3051 | L12 |" (Table 1); distance from L12 (cite: lupu2012)  
  > "| SDP 17b | H-ATLAS J090302.9$-$014127 | 2.3051 | L12 |" (Table 1)

## Data provenance

- ALMA projects: 2016.1.00285.S, 2012.1.00175.S, 2013.1.00569.S
- bands: Band 7  
  > "are shifted down to frequencies covered by band 7 of ALMA." (Target Selection)
- frequencies and spectral setup: H2O+ 1139 GHz: three basebands, one window each, ~3000 km/s coverage; OH+ 1033 GHz: 2 basebands in upper sideband, 2500-3000 km/s; 31.25 MHz resolution (~30 km/s)  
  > "A frequency resolution of 31.25 MHz provides velocity resolution of about 30 km s$^{-1}$." (Execution)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: OH+ in SMM J2135-0102: 0.18"x0.14"  
  > "the small synthesized beam used for the OH$^+$ observations (0.18$''$$\times$0.14$''$)" (Resulting Spectra)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: SDP 17b H2O+ 1481 s; SMM J2135 H2O+ 1451 s; SMM J2135 OH+ 3568 s; SDP 17b OH+ 1965 s  
  > "SDP 17b was observed for 1481 s on 2016 Nov 26 targeting H$_2$O$^+$" (Execution)
- observing dates: 2016 Nov 26, 2017 Apr 14, 2014 Aug 19, 2015 Jun 15  
  > "SMM J2135$-$0102 was observed for 3568 s on 2014 Aug 19 targeting OH$^+$" (Execution)
- pi or archival as stated: _not stated_
- Line: OH+ N=1-0, J=1-1 hyperfine complex (1033 GHz (strongest 1033118.6 MHz))
- Line: o-H2O+ 1_11-0_00 hyperfine complex (1139 GHz (strongest 1139667.9 MHz))
- External data: CH+ column densities N(CH+)=(8.3±1.4)e14 and (4.7±1.9)e14 cm^-2 for SMM J2135-0102 and SDP 17b  
  > "are reported as $N({\rm CH}^+)=(8.3\pm1.4)\times10^{14}$ cm$^{-2}$ and $N({\rm CH}^+)=(4.7\pm1.9)\times10^{14}$ cm$^{-2}$, respectively" (5.2 Ionization Rates) [from Falgarone et al. 2017 (cite: falgarone2017)]
- External data: Mean X(CH+)=7.6e-9 with range 2e-9 to 2e-8  
  > "is about $X({\rm CH}^+)=7.6\times10^{-9}$ (cite: godard2014)" (5.2 Ionization Rates) [from (cite: godard2014)]
- External data: f_H2 = 0.053±0.026  
  > "We adopt the mean value of $f_{\rm H_2}=0.053\pm0.026$ reported by (cite: indriolo2015oxy)" (5.2 Ionization Rates) [from (cite: indriolo2015oxy)]
- External data: Chemical model grid of OH+ and H2O+ column densities  
  > "We thus choose to employ the chemical models presented in (cite: neufeld2017)" (5.2 Ionization Rates) [from Neufeld & Wolfire 2017 (cite: neufeld2017)]
- Simulation/model as data: Plane-parallel slab chemical models (Neufeld & Wolfire 2017) with Z=Zsun, nH=50 cm^-3, chi_UV=0.1-1000, 0.0003<=A_V<=8 mag, 9e-19<=zeta_H<=9e-15 s^-1  
  > "we run the suite of chemical models using $\chi_{\rm UV}$=0.1, 1, 10, 100, and 1000" (5.2 Ionization Rates)

## Processing

### Calibration

- pipeline or manual: Calibration by NRAO staff using standard procedures  
  > "All data calibration was performed by NRAO staff using standard procedures to produce calibrated measurement sets." (Data Reduction)
- casa version: CASA 5.0.0 (post-calibration processing)  
  > "Further processing starting from those products was done with CASA version 5.0.0." (Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (SMM J2135 H2O+); J1058+0133 (SDP 17b); J2148+0657 (SMM J2135 OH+)  
  > "J2232+1143 as the bandpass calibrator, and Titan as the flux calibrator." (Execution)
- flux scale uncertainty: _not stated_
- self calibration: One round of phase-only self-cal on absorption-free continuum for all except OH+ in SMM J2135-0102  
  > "One round of phase-only self-calibration using absorption-free portions of the continuum was applied to all observations (except for that covering OH$^+$ in SMM J2135$-$0102)" (Data Reduction)

### Imaging

- task: CASA clean  
  > "Measurement sets were imaged via the `clean` task in CASA" (Data Reduction)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "utilizing the Briggs weighting scheme with a robust parameter of 0.5" (Data Reduction)
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

- Chemical network and model framework  
  > "The analysis of (cite: neufeld2017), first presented by (cite: hollenbach2012), utilizes a chemical network designed specifically to focus on processes important to oxygen chemistry" (5.2 Ionization Rates) [from (cite: hollenbach2012); (cite: neufeld2017)]
- Use CH+ to estimate N(H)  
  > "The recent observations of CH$^+$ absorption in these galaxies are likely the best tracer of the same gas component giving rise to OH$^+$ and H$_2$O$^+$ absorption (cite: gerin2016)." (5.2 Ionization Rates) [from (cite: gerin2016)]

### Not stated but needed to reproduce (our reading)

- Cell size, image size, and channel width/spectral grid of the cubes
- Clean threshold, masks, number of iterations
- Self-calibration solution interval and continuum selection
- Exact sub-region definitions (NW1-8, SE1-8, N/E/S/W) as apertures
- Moving-average window for continuum normalization
- Line-free region used for noise estimate
- Model grid files and interpolation method for inferring zeta_H
- Resulting zeta_H values per region (only ranges stated)

## Analysis recipe

1. **Image cubes and extract spectra**: Clean with Briggs weighting, make PPV cubes; extract spectra from full source and sub-regions with CASA Viewer Spectral Profile Tool  
  > "Spectra of the target galaxies were extracted from the data cubes using the Spectral Profile Tool within CASA Viewer." (Data Reduction)
   - software: CASA
   - parameter: robust = 0.5  
  > "a robust parameter of 0.5" (Data Reduction)
   - fitting: _not stated_
   - validation: Mirrored NW/SE regions agree within noise  
  > "the OH$^+$ and H$_2$O$^+$ absorption line profiles for the mirrored regions agree with each other within the noise levels" (Resulting Spectra)
2. **Optical depth and column density**: Normalize by moving average, tau=-ln(transmission), integrate over velocity ranges, convert to N via ground-state relation with constants 4.87e12 (1033 GHz) and 4.18e12 (1139 GHz)  
  > "This is done by dividing the spectra by a moving average that was interpolated across velocities showing absorption or narrow emission." (5.1 Column Densities)
   - assumption: All hyperfine components at same frequency; CMB at z=2.3 (~9 K) does not populate excited states; H2O+ ortho-to-para = 3:1  
  > "The *ortho*-to-*para* ratio expected based solely on statistical weights is 3:1, and we assume this value" (5.1 Column Densities)
   - fitting: _not stated_
   - validation: Uncertainties from continuum standard deviation propagated per channel; columns may be lower limits if absorption saturated  
  > "Still, it is possible that these are only lower limits if saturated absorption is masked by the above effects." (5.1 Column Densities)
3. **Estimate N(H) from CH+**: N(H)=(1-f_H2) N(CH+)/X(CH+) with limiting X(CH+) values 2e-9 and 2e-8  
  > "Uncertainties are dominated by the scatter in $X({\rm CH}^+)$ as we adopt the limiting values of $2\times10^{-9}$ and $2\times10^{-8}$ in our analysis." (5.2 Ionization Rates)
   - assumption: X(CH+)=7.6e-9 (solar-neighborhood mean), f_H2=0.053  
  > "We adopt the mean value of $f_{\rm H_2}=0.053\pm0.026$" (5.2 Ionization Rates)
   - fitting: _not stated_
   - validation: _not stated_
4. **Infer zeta_H from chemical model grids**: Compare observed log N(OH+)/N(H) and N(OH+)/N(H2O+) to contours of constant zeta_H/n50 in model grids for several chi_UV/n50  
  > "we plot contours of constant $\zeta_{\rm H}/n_{50}$ in the parameter space $\log_{10}[N({\rm OH}^+)/N({\rm H})]$ vs. $N({\rm OH}^+)/N({\rm H_2O}^+)$" (5.2 Ionization Rates)
   - parameter: Z=Zsun, nH=50 cm^-3, chi_UV 0.1-1000  
  > "so we use the chemical models with $Z=Z_\ensuremath{\odot}$ in our analysis" (5.2 Ionization Rates)
   - assumption: Metallicity solar; absorption arises in extended low-density halo  
  > "Metallicities in submillimeter galaxies at $z\sim2$ have been estimated to be roughly solar" (5.2 Ionization Rates)
   - fitting: _not stated_
   - validation: Compared with Galactic diffuse clouds and earlier zeta estimates  
  > "occupy the same location in $\log_{10}[N({\rm OH}^+)/N({\rm H})]$ vs. $N({\rm OH}^+)/N({\rm H_2O}^+)$ parameter space as Galactic diffuse clouds" (6 Discussion)

## Software

- **CASA** 5.0.0: Imaging (clean), self-calibration, spectral extraction with Viewer  
  > "Further processing starting from those products was done with CASA version 5.0.0." (Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| N(OH+) SMM J2135-0102 Full | 12.88 | 0.17 | 1e14 cm^-2 | 2 | / Full / \[$-$220, 610\] / 264.6$\pm$3.5 / 69.3$\pm$1.8 / 12.88$\pm$0.17 / 3.86$\pm$0.10 / 3.33$\pm$0.10 / |
| N(H2O+) SMM J2135-0102 Full | 3.86 | 0.10 | 1e14 cm^-2 | 2 | / Full / \[$-$220, 610\] / 264.6$\pm$3.5 / 69.3$\pm$1.8 / 12.88$\pm$0.17 / 3.86$\pm$0.10 / 3.33$\pm$0.10 / |
| N(OH+) SDP 17b Full | 16.53 | 0.18 | 1e14 cm^-2 | 2 | / Full / \[$-$755, 235\] / 339.6$\pm$3.8 / 22.8$\pm$2.6 / 16.53$\pm$0.18 / 1.27$\pm$0.14 / 13.00$\pm$1.49 / |
| N(H2O+) SDP 17b Full | 1.27 | 0.14 | 1e14 cm^-2 | 2 | / Full / \[$-$755, 235\] / 339.6$\pm$3.8 / 22.8$\pm$2.6 / 16.53$\pm$0.18 / 1.27$\pm$0.14 / 13.00$\pm$1.49 / |
| N(H) SMM J2135-0102 | 1.0e23 | +3.6/-0.7 e23 | cm^-2 | 3 | $N({\rm H})=(1.0^{+3.6}_{-0.7})\times10^{23}$ cm$^{-2}$ |
| N(H) SDP 17b | 5.9e22 | +25/-4.5 e22 | cm^-2 | 3 | $N({\rm H})=(5.9^{+25}_{-4.5})\times10^{22}$ cm$^{-2}$ |
| zeta_H in extended halos | 1e-16 to 1e-14 | not stated | s^-1 | 4 | cosmic-ray ionization rates on the order of 10$^{-16}$–10$^{-14}$ s$^{-1}$ in the extended gaseous halos |

## Qualitative findings

- OH+ and H2O+ absorption profiles vary with position and show velocity gradients in SMM J2135-0102 consistent with rotation; none in SDP 17b  
  > "shifting to larger velocities with increasing distance from the critical curve." (Resulting Spectra)

## Claim tuples

- H: OH+ and H2O+ are detectable in absorption in z~2.3 lensed SMGs with ALMA | E: Band 7 observations of both galaxies | R: Both molecules detected in both galaxies | F: Absorption traces extended halo gas | **supported**
- H: Cosmic-ray ionization rates in SMG halos can be constrained | E: Column densities with chemical models and N(H) from CH+ | R: zeta_H ~1e-16 to 1e-14 s^-1 | F: Rates in compact star-forming regions likely orders of magnitude higher | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Analytic steady-state expressions invalid at high zeta and require unconstrained parameters, so full chemical models used  
  > "removing the need to adopt unconstrained values of $x_e$ and $\epsilon$." (5.2 Ionization Rates)
- Alternative: Analytic steady-state expressions rejected  
  > "those expressions are only valid over a limited range of physical conditions" (5.2 Ionization Rates)
- How they decided it was enough: _not stated_
- Limitation (authors): Column densities may be lower limits due to saturation; N(H) highly uncertain; mismatched beams  
  > "any estimate of the hydrogen column density from CH$^+$ will be highly uncertain" (5.2 Ionization Rates)
- Caveat (inferred, ours): N(H) from CH+ with Galactic X(CH+) is very uncertain
- Caveat (inferred, ours): Final zeta_H rests on poorly known UV field and density
- Caveat (inferred, ours): Beam mismatch between OH+, H2O+ and CH+
- Caveat (inferred, ours): Quantitative zeta_H per region not tabulated

## Reproducibility

- Data public (paper): Archival ALMA data cited by project code  
  > "Observations covering the 1033 GHz transition in both target galaxies are publicly available in the ALMA archive." (Target Selection)
- Products in archive: _not stated_
- Missing: Neufeld & Wolfire model grids
- Missing: Sub-region aperture definitions
- Missing: Imaging cell/size/threshold
- Data volume (inferred): ~10-50 GB for three ALMA projects
- Score (inferred): 3/5, Data are public and column density steps are described, but model grids, apertures and imaging details are missing and zeta_H is read graphically.
- Rediscovery candidate: no, Column densities are reproducible, but the main zeta_H result relies on external model grids and graphical reading.

## Links

- Method: Neufeld & Wolfire 2017 (cite: neufeld2017) (Chemical model grid)
- Method: Hollenbach et al. 2012 (cite: hollenbach2012) (Chemical network)
- Companion: Falgarone et al. 2017 (cite: falgarone2017) (CH+ absorption in same galaxies)
- Related: H-ATLAS

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 41,
  "rate": 0.554
 },
 "evidence_ok": true
}
```

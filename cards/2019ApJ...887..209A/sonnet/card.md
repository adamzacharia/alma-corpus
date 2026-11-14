# Protostellar Evolution in Serpens Main: Possible Origin of Disk-size Diversity

`2019ApJ...887..209A` | The Astrophysical Journal 2019 | first author: Aso, Yusuke | arXiv: 1910.13665 | DOI: 10.3847/1538-4357/ab5284

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks
- Question: How does protostellar evolution in Serpens Main relate to the diversity of protoplanetary disk sizes seen at the T Tauri stage?  
  > "In order to study the relation between protostellar evolution and the size diversity of protoplanetary disks in the T Tauri phase, we observed the star forming cluster Serpens Main" (1 Introduction)
- Target **Serpens Main (SMM2, SMM4, SMM9/S68N, SMM11)**: coordinates SMM2: 18h30m00.72s, +01d13m01.40s (J2000); other field centers in Table 1  
  > "The distance to Serpens Main is 429 pc (cite: dzib11)." (1 Introduction); "$18^{\rm h}30^{\rm m}00.72s$, $01\ensuremath{^\circ} 13\ensuremath{'} 01.40\ensuremath{''}$ (SMM2)" (Table 1); z/distance 429 pc  
  > "The distance to Serpens Main is 429 pc (cite: dzib11)." (1 Introduction); "$18^{\rm h}30^{\rm m}00.72s$, $01\ensuremath{^\circ} 13\ensuremath{'} 01.40\ensuremath{''}$ (SMM2)" (Table 1); distance from Dzib et al. 2011 (cite: dzib11)  
  > "The distance to Serpens Main is 429 pc (cite: dzib11)." (1 Introduction); "$18^{\rm h}30^{\rm m}00.72s$, $01\ensuremath{^\circ} 13\ensuremath{'} 01.40\ensuremath{''}$ (SMM2)" (Table 1)

## Data provenance

- ALMA projects: 2015.1.01478.S
- bands: Band 6 (1.3 mm)  
  > "The precision of absolute flux is $\sim 10$% at Band 6 of ALMA." (2 ALMA Observations)
- frequencies and spectral setup: 12CO 3840 ch/117 MHz; C18O 1920 ch/59 MHz; SO 960 ch/59 MHz; continuum windows 216-218 and 232-234 GHz  
  > "Two other spectral windows covering 216-218 GHz and 232-234 GHz were assigned to the continuum emission." (2 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: 12 m antennas, 37 and 39 per day  
  > "The numbers of 12 m antennas were 37 and 39 in the first and the second days, respectively" (2 ALMA Observations)
- configurations: _not stated_
- baselines: 15 - 613 m (11 - 460 kλ)  
  > "15 - 613 m (11 - 460 k$\lambda$)" (Table 1)
- angular resolution: ~0.55'' (240 au)  
  > "at an angular resolution of $\sim 0.55\ensuremath{''}$ (240 au)" (abstract)
- max recoverable scale: ~50% flux missed for Gaussian of FWHM 8.0'' (3400 au)  
  > "if observed emission is a Gaussian component with a FWHM of $8.0\ensuremath{''}$ (3400 au), $\sim 50$% of its flux is missed." (2 ALMA Observations)
- sensitivity: rms 0.1 (continuum), 3 (12CO), 7 (SO), 10 (C18O) mJy/beam  
  > "| rms noise level (${\rm mJy~beam^{-1}}$) | 0.1                                                                       | 3                                                                         | 7                                                                         | 10" (Table 1)
- time on source: 4.5 and 9.0 min per field on days 1 and 2; SMM4 4.5 and 10.5 min  
  > "On-source observing time for each field of view except SMM4 was 4.5 and 9.0 min in the first and the second days, respectively; that for SMM4 was 4.5 and 10.5 min, respectively." (2 ALMA Observations)
- observing dates: 2016 May 19 and 21 (Cycle 3)  
  > "We observed five regions, highlighted by the cyan circles in Figure 1, in Serpens Main using ALMA in Cycle 3 on 2016 May 19 and 21." (2 ALMA Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.538 GHz)
- Line: SO JN=6_5-5_4 (219.949 GHz)
- Line: C18O J=2-1 (219.560 GHz)
- Other facility **Spitzer, Herschel, CSO, JCMT, CARMA**: Archival fluxes for SEDs of S68Nb1 and S68Nc1  
  > "The SEDs were constructed from archival data of Spitzer IRAC (3.6, 4.5, 5.8, and 8.0 $\ensuremath{\mu}m$), Spitzer MIPS 24 $\ensuremath{\mu}m$, Herschel PACS 70 $\ensuremath{\mu}m$" (3.4 SED)
- External data: Lbol, Tbol, Class for most sources (Spitzer)  
  > "cited from (cite: dunh15; aso17a; aso18), or derived in Section 3.4" (Table 2) [from (cite: dunh15; aso17a; aso18)]
- External data: 3 mm CARMA flux densities of S68Nb and S68Nc  
  > "the SEDs also includes the 3 mm flux densities of S68Nb and S68Nc measured with CARMA (cite: leek14)" (3.4 SED) [from (cite: leek14)]
- External data: C18O abundance of 6-9e-8 in Serpens Main for comparison  
  > "Compared to the C$^{18}$O abundance in Serpens Main of 6-$9\times10^{-8}$ at $\sim 15\ensuremath{''}$ ($\sim 6400$ au) scales" (4.3 C18O Abundance) [from (cite: du-ca10)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.7.0 (calibration)  
  > "the CASA version for the calibration procedure is 4.7.0" (2 ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan  
  > "Amplitude calibrator                    | Titan" (Table 1)
- flux scale uncertainty: ~10% at Band 6  
  > "The precision of absolute flux is $\sim 10$% at Band 6 of ALMA." (2 ALMA Observations)
- self calibration: SMM11 and SMM4 fields only; phase-only with 3-scan (~18 s) solint, then amplitude+phase; rms improved ~2x; tables applied to lines  
  > "Only the phase was calibrated first with the solution interval of 3 scans ($\sim 18$s). Then, using the derived table, the amplitude and the phase were calibrated together." (2 ALMA Observations)

### Imaging

- task: CASA clean  
  > "The visibilities were Fourier transformed and CLEANed with a Briggs robust parameter of 0.0 and a threshold of 3$\sigma$ for all the lines and continuum data." (2 ALMA Observations)
- deconvolver: Multi-scale CLEAN, point sources or Gaussians of FWHM ~1.5''  
  > "Multi-scale CLEAN was adopted, where CLEAN components were point sources or Gaussian sources with a FWHM of $\sim 1.5\ensuremath{''}$." (2 ALMA Observations)
- weighting robust: Briggs robust = 0.0  
  > "CLEANed with a Briggs robust parameter of 0.0" (2 ALMA Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Applied before flux measurements  
  > "were measured within the $3\sigma$ contours enclosing each source after primary beam correction" (3.1 Group 1)
- array combination: _not stated_
- smoothing: Channel binning 32 (12CO), 2 (C18O), 4 (SO): 1.27, 0.083, 0.33 km/s  
  > "When maps are generated, 32, 2, and 4 channels are binned for the $^{12}$CO, C$^{18}$O, and SO lines" (2 ALMA Observations)
- final beam: Continuum 0.57''x0.46'' (PA -86 deg)  
  > "$0.57\ensuremath{''}\times 0.46\ensuremath{''}\ (-86\ensuremath{^\circ})$" (Table 1)
- final rms: 0.1 mJy/beam continuum  
  > "| rms noise level (${\rm mJy~beam^{-1}}$) | 0.1" (Table 1)

### Inherited from earlier work

- SED flux/upper-limit method and Tbol, Lbol, Lsmm calculation  
  > "Our method to derive fluxes and upper limits, and then calculate $T_{\rm bol}$, $L_{\rm bol}$, and $L_{\rm smm}$ is explained by (cite: aso18) in more detail." (3.4 SED) [from (cite: aso18)]
- Wind-driven-shell fitting method for outflow inclination  
  > "We follow the method described in Appendix A of (cite: yen17)" (4.1 Outflows) [from (cite: yen17)]
- SMM4 and SMM11 results previously reported; SMM4B inclination adopted  
  > "$i$ and its uncertainty of the SMM4B outflow are adopted from (cite: aso18)" (4.1 Outflows) [from (cite: aso18)]

### Not stated but needed to reproduce (our reading)

- Image sizes and cell sizes
- Line-free channels and continuum subtraction method for lines
- CASA version used for imaging (only calibration version given)
- Mask definitions for clean
- How the 1.3 mm continuum was extracted from line-free windows
- Priors and walker/step settings for emcee
- How the optical-depth estimates for SMM11 and S68Nb1 were derived
- Flux-correction details for blended SED fluxes

## Analysis recipe

1. **Image continuum and lines, self-calibrate two fields**: CASA clean with Briggs robust 0, multiscale, 3 sigma threshold; self-cal on SMM11 and SMM4  
  > "The visibilities were Fourier transformed and CLEANed with a Briggs robust parameter of 0.0 and a threshold of 3$\sigma$ for all the lines and continuum data." (2 ALMA Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Self-cal kept only where rms improved significantly  
  > "We did not adopt the self-calibrated results for the other three fields because the rms noise level was not improved significantly in those fields." (2 ALMA Observations)
2. **Measure continuum and C18O source properties**: 2D Gaussian fits for positions and deconvolved sizes; peak and total flux within 3 sigma contours after primary beam correction; uncertainty sigma_i*sqrt(4*Omega)  
  > "the uncertainty of each flux density was calculated from the rms noise level of intensity $\sigma _i$ in the unit of Jy beam$^{-1}$ and the integrated area $\Omega$ in the unit of beam as $\sigma_i\sqrt{4\Omega}$" (3.1 Group 1)
   - fitting: 2D Gaussian; double-component for S68Nc3/S68Nc4  
  > "the fitting was simultaneously done using a double-component 2D Gaussian function" (3.2 Group 2)
   - validation: _not stated_
3. **Outflow morphology and dynamical time**: Intensity-weighted PA, length, opening angle from CLEAN-deconvolved 12CO moment 0 maps (5 sigma cutoff); intensity-weighted velocity; tau_dyn = r/v  
  > "the $^{12}$CO moment 0 maps were deconvolved in the way of CLEAN: finding peaks in a moment 0 map, recording the peaks as “CLEAN components", subtracting beam (Gaussian) functions from the moment 0 map, and then repeating these down to a $5\sigma$ cutoff." (4.1 Outflows)
   - assumption: Systemic velocities from C18O Gaussian fits; S68Nb1 assumed same as S68Nc1  
  > "The systemic velocity of S68Nb1 was assumed to be the same as that of S68Nc1 since the C$^{18}$O line is not detected in S68Nb1." (4.1 Outflows)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit outflow inclination**: Wind-driven-shell model fit to binarized moment 0 maps and PV diagrams (5 sigma)  
  > "the $^{12}$CO moment 0 maps and $^{12}$CO position-velocity (PV) diagrams are fitted with the wind-driven-shell model (cite: shu91; lee00)" (4.1 Outflows)
   - software: emcee
   - parameter: Low-velocity ranges filled with emission, e.g. 6-10 km/s in S68N  
  > "6 - 10 ${\rm km~s^{-1}}$ in S68N, 4 - 9${\rm km~s^{-1}}$ in S68Nb1" (4.1 Outflows)
   - fitting: MCMC with emcee; log likelihood -chi^2/2; uncertainties from 5th and 95th percentiles  
  > "The log likelihood is $-\chi ^{2} /2$, where $\chi^2$ is the sum of squared differences between the model and the observations (i.e., unity or zero)." (4.1 Outflows)
   - validation: SMM4B excluded since single shell inappropriate  
  > "Our single shell model is not appropriate to fit such a complex velocity structure." (4.1 Outflows)
5. **Jeans stability of Group 2**: Continuum peak to H2 column and central density (Gaussian line-of-sight profile), then Jeans length  
  > "the H$_2$ column density is converted to the central number density $n_{\rm H_2}$ by assuming a Gaussian density profile along the line of sight" (4.2 Jeans Stability)
   - assumption: kappa(850um)=0.035 cm2/g, beta=1, T=10 K, mu=2.37  
  > "We adopt a dust opacity coefficient of $\kappa (850\ \ensuremath{\mu}m) = 0.035\ {\rm cm}^2\,{\rm g}^{-1}$ (cite: an.wi05), an opacity index, $\beta=1$, and a temperature of 10 K" (4.2 Jeans Stability)
   - fitting: _not stated_
   - validation: Sensitivity to beta, temperature, flux error tested  
  > "If the temperature is relatively high as prestellar sources, $\sim 15$ K, the density is two times lower, and the ratio is $\sim 40\%$ lower." (4.2 Jeans Stability)
6. **C18O fractional abundance**: From continuum and C18O integrated intensity at continuum peak, optically thin, LTE  
  > "calculated from the 1.3 mm continuum intensity and the C$^{18}$O integrated intensity at the continuum peak position, assuming both are optically thin" (4.3 C18O Abundance)
   - assumption: T=20 K for Groups 1 and 3, 10 K for Group 2; SMM4A excluded  
  > "The temperature is assumed to be 20 K for the protostellar sources (Group 1 and 3) (cite: leek14) and 10 K for the prestellar sources (Group 2)" (4.3 C18O Abundance)
   - fitting: _not stated_
   - validation: Optical-depth correction factors (~1.5 and ~1.2) do not change trends  
  > "These factors, however, do not change overall trends of data points in Figure 9." (4.3 C18O Abundance)
7. **SED classification of S68Nb1 and S68Nc1**: Build SEDs from archival IR/submm plus ALMA and CARMA; compute Tbol, Lbol/Lsmm  
  > "their upper limits of $T_{\rm bol}\lesssim 60$ K and luminosity ratio $L_{\rm bol} / L_{\rm smm}\lesssim 13$ indicate that both S68Nb1 and S68Nc1 are Class 0 protostars" (3.4 SED)
   - fitting: _not stated_
   - validation: _not stated_
8. **Group 3 gas mass estimates**: Mass from 1.3 mm flux density  
  > "where $\kappa(1.3\ {\rm mm}) = 0.023\ {\rm cm^2\,g^{-1}}$ and $T_{\rm dust} = 20$ K are assumed" (5.2 Group 3)
   - assumption: kappa(1.3 mm)=0.023 cm2/g, Tdust=20 K  
  > "$\kappa(1.3\ {\rm mm}) = 0.023\ {\rm cm^2\,g^{-1}}$ and $T_{\rm dust} = 20$ K are assumed" (5.2 Group 3)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.0 (calibration): Calibration, imaging, self-calibration (clean, gaincal, applycal)  
  > "All imaging was carried out with Common Astronomical Software Applications (CASA)" (2 ALMA Observations)
- **emcee** : MCMC fit of outflow shell model  
  > "The Markov chain Monte Carlo method is used through an open source, *emcee* (cite: fore13)." (4.1 Outflows)
- **MIRIAD** : Listed in software section; use not described  
  > "CASA (cite: mcmu07), MIRIAD (cite: saul95)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of 1.3 mm continuum sources detected | 16 | not stated | sources | 2 | Sixteen sources were detected in the 1.3 mm continuum in our ALMA observations. |
| SMM4A 1.3 mm peak intensity | 196.4 | 0.1 | mJy/beam | 2 | SMM4A  / 196.4$\pm$0.1              / 492$\pm$1 |
| SMM4A 1.3 mm total flux | 492 | 1 | mJy | 2 | 196.4$\pm$0.1              / 492$\pm$1 |
| Outflow dynamical time S68N red lobe (not inclination-corrected) | 3380 | 290 | yr | 3 | \- (red) / 133.0$\pm$0.5 / 4280$\pm$60 / 32.1$\pm$0.2 / 6.0$\pm$0.5 / 3380$\pm$290 / 83.4$^{+0.1}_{-0.5}$ |
| SMM11 red outflow inclination | 88.0 | +0.1/-0.2 | deg | 4 | SMM11 (blue) / 82.4$\pm$0.2 / 4020$\pm$60 / 11.1$\pm$0.5 / 5.9$\pm$0.3 / 3230$\pm$170 / 81.0$^{+0.1}_{-0.3}$ /
/ \- (red) / -109.1$\pm$0.2 / 4430$\pm$50 / 9.6$\pm$0.3 / 4.2$\pm$0.4 / 5000$\pm$480 / 88.0$^{+0.1}_{-0.2}$ |
| Group 2 central density | ~1e8 | not stated | cm^-3 | 5 | The central densities of the Group 2 members are typically $\sim 10^8\ {\rm cm}^{-3}$ |
| Group 3 gas mass range | 0.006-0.045 | not stated | Msun | 8 | This range corresponds to the gas-mass range from 0.045 down to 0.006 $M_{\ensuremath{\odot}}$ |
| S68Nb1 and S68Nc1 Tbol upper limit | <=60 | not stated | K | 7 | $T_{\rm bol}\lesssim 60$ K and luminosity ratio $L_{\rm bol} / L_{\rm smm}\lesssim 13$ |

## Qualitative findings

- C18O abundances in pre- and protostellar cores are 10-100 times lower than the larger-scale value  
  > "the calculated abundances of the pre- and proto-stellar cores are 10-100 times lower." (4.3 C18O Abundance)

## Claim tuples

- H: Class 0 Group 1 sources show evolutionary differences | E: Scored outflow dynamical time, SO distribution, C18O abundance, continuum morphology | R: SMM4B and S68N score 6; SMM11 and S68Nb1 score 0 | F: Evolutionary trends exist within Class 0 | **supported**
- H: Group 2 are prestellar | E: Jeans analysis from continuum density | R: FWHM/lambda_Jeans around unity; densities ~1e8 cm^-3 | F: Marginally Jeans unstable prestellar sources | **supported**
- H: Small disks form in Class 0/I from envelope dissipation | E: Group 3 continuum sizes, masses, compact CO outflows | R: Point-like continuum, r<~60 au, masses >10x lower than Group 1 | F: Group 3 may be precursors of small T Tauri disks | **partially**

## Reasoning

- Why this data: Serpens Main has high protostar density and protostellar fraction, suggesting active disk formation  
  > "it has a high number density of protostars and a high protostellar fraction (cite: li19)" (1 Introduction)
- Why this method: _not stated_
- Alternative: Proto-brown-dwarf origin of Group 3 rejected based on luminosities  
  > "However, the Group 3 members are not proto-brown dwarfs" (5.3)
- How they decided it was enough: _not stated_
- Limitation (authors): Small number of sampling points for the outflow trend  
  > "Although the number of the sampling points is small, the points in Figure 7 seem to show a hint of trend." (4.1 Outflows)
- Limitation (authors): Unclear whether envelope size differences are due to evolution or intrinsic differences  
  > "it is not clear only from the present data whether these two mechanisms are due to protostellar evolution or intrinsic differences" (5.1.3)
- Caveat (inferred, ours): Evolutionary scoring is ad hoc with arbitrary thresholds (500 yr, 1e-9)
- Caveat (inferred, ours): Interferometric filtering affects envelope sizes and C18O abundances
- Caveat (inferred, ours): Single temperature assumptions drive densities and abundances
- Caveat (inferred, ours): Group 3 mass sensitivity limits disk size inference

## Reproducibility

- Data public (paper): ALMA project 2015.1.01478.S acknowledged  
  > "This paper makes use of the following ALMA data: ADS / JAO.ALMA2015.1.01478.S (P.I. Y. Aso)." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging cell/image size and masks
- Missing: Line-free channel choices
- Missing: Inclination-fit priors and sampler settings
- Missing: Exact SED flux extraction from archival data
- Data volume (inferred): ~50-100 GB raw
- Score (inferred): 3/5, Data public and main settings given but many imaging and fitting details missing; results are numeric but source-specific.
- Rediscovery candidate: no, Key imaging and fitting details missing and heavily reliant on earlier papers.

## Links

- Method: Yen et al. 2017 (cite: yen17) (Outflow shell-model fitting method)
- Method: Aso et al. 2018 (cite: aso18) (SED and Tbol/Lbol method; SMM4 analysis)
- Companion: Aso et al. 2017 (cite: aso17a) (SMM11 results from same data)
- Companion: Aso et al. 2018 (cite: aso18) (SMM4 results from same data)
- Related: DSHARP
- Related: ODISEA

## Checks

```json
{
 "quotes": 78,
 "quotes_ok": 78,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 1,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 59,
  "rate": 0.686
 },
 "evidence_ok": true
}
```

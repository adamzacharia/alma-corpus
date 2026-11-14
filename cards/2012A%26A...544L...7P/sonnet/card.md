# The first ALMA view of IRAS 16293-2422. Direct detection of infall onto source B and high-resolution kinematics of source A

`2012A&A...544L...7P` | Astronomy and Astrophysics 2012 | first author: Pineda, J. E. | arXiv: 1206.5215 | DOI: 10.1051/0004-6361/201219589

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: What are the infall and rotation kinematics of gas toward the two protostellar components of the proto-binary IRAS 16293-2422?  
  > "We focus on the kinematical properties of a proto-binary to study the infall and rotation of gas towards its two protostellar components." (abstract)
- Target **IRAS 16293-2422 (sources A and B)**: coordinates A: 16:32:22.873 -24:28:36.50; B: 16:32:22.623 -24:28:32.49 (J2000)  
  > "It is located in the nearby $\rho$ Ophiuchi star-forming region, at a distance of $\sim$120 pc" (1 Introduction); "| IRAS16293 A | 16:32:22.873 | -24:28:36.50  |" (Table 2); "| IRAS16293 B | 16:32:22.623 | -24:28:32.49  |" (Table 2); z/distance ~120 pc  
  > "It is located in the nearby $\rho$ Ophiuchi star-forming region, at a distance of $\sim$120 pc" (1 Introduction); "| IRAS16293 A | 16:32:22.873 | -24:28:36.50  |" (Table 2); "| IRAS16293 B | 16:32:22.623 | -24:28:32.49  |" (Table 2); distance from Knude & Hog 1998; Loinard et al. 2008  
  > "It is located in the nearby $\rho$ Ophiuchi star-forming region, at a distance of $\sim$120 pc" (1 Introduction); "| IRAS16293 A | 16:32:22.873 | -24:28:36.50  |" (Table 2); "| IRAS16293 B | 16:32:22.623 | -24:28:32.49  |" (Table 2)

## Data provenance

- ALMA projects: 2011.0.00007.SV
- bands: Band 6  
  > "I16293 was observed on August 16-18, 2011 in ALMA band 6 as part of the ALMA Science Verification effort" (2 Data)
- frequencies and spectral setup: one baseband centered on 220.182 GHz, 61 kHz channels, 234.375 MHz bandwidth; two-field mosaic  
  > "using one baseband centered on 220.182 GHz, with a channel width of 61 kHz and bandwidth of 234.375 MHz." (2 Data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 16 antennas, longest baseline 220 m  
  > "The use of 16 antennas with a longest baseline of 220-m results in maps with a synthesized beam size 2.2$''$$\times$1.0$''$ at 220 GHz." (2 Data)
- angular resolution: 2.2"x1.0" (cube); 1.9"x0.9" (continuum)  
  > "results in maps with a synthesized beam size 2.2$''$$\times$1.0$''$ at 220 GHz." (2 Data)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 3.6 mJy/beam; line rms ~4.5 mJy/beam per 120 kHz channel  
  > "The resulting rms in the line-free channels of the spectral cube is $\sim$4.5 m$\rm Jy\,beam^{-1}$ per 120 kHz-channel" (2 Data)
- time on source: 5.4 hours  
  > "yielding a total on-source observing time of 5.4 hours" (2 Data)
- observing dates: August 16-18, 2011  
  > "I16293 was observed on August 16-18, 2011 in ALMA band 6" (2 Data)
- pi or archival as stated: ALMA Science Verification data  
  > "as part of the ALMA Science Verification effort" (2 Data)
- Line: CH3OCHO-E 17(4,13)-16(4,12) (220.166888 GHz)
- Line: CH3OCHO-A 17(4,13)-16(4,12) (220.190285 GHz)
- Line: H2CCO 11(1,11)-10(1,10) (220.17757 GHz)
- External data: Dust opacity per dust mass kappa_1.3mm = 0.86 cm2/g  
  > "a dust opacity per dust mass ($\kappa_{1.3~mm}$) of 0.86 cm$^{2}$ g$^{-1}$ (cite: OH94)" (3.1 Continuum emission and molecular complexity) [from Ossenkopf & Henning 1994 (cite: OH94)]

## Processing

### Calibration

- pipeline or manual: Own calibration of the uncalibrated released data in CASA  
  > "The uncalibrated dataset was released, together with spectrally averaged, low-resolution calibrated images" (2 Data)
- casa version: CASA 3.3.0  
  > "We calibrated and imaged the original interferometric data with the CASA[^3] software version 3.3.0." (2 Data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune, Butler-JPL-Horizons 2010 model; bandpass J1924-292; gain J1625-254  
  > "Absolute flux calibration was performed using the CASA Butler-JPL-Horizons 2010 model applied to Neptune observations" (2 Data)
- flux scale uncertainty: ±10–15%  
  > "which results in an estimated flux uncertainty of $\pm$10–15%" (2 Data)
- self calibration: Self-cal on continuum (rms lowered by factor 3), applied to spectral data  
  > "we performed self-calibration on the continuum data which lowered the rms noise in the continuum map by a factor of three" (2 Data)

### Imaging

- task: _not stated_
- deconvolver: Clark CLEAN  
  > "and then CLEANed using the Clark algorithm" (2 Data)
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum removed from visibilities  
  > "The continuum was removed from the visibilities to produce the spectral cube" (2 Data)
- line free channels: 220.103-220.112 GHz for continuum  
  > "The continuum image was produced by using line-free channels between 220.103 and 220.112 GHz" (2 Data)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Binned to 120 kHz (Hanning smoothing, 0.16 km/s)  
  > "The calibrated measurement set was spectrally binned to a channel spacing of 120 kHz (Hanning smoothing, 0.16 ${\rm km\, s^{-1}}$ resolution)" (2 Data)
- final beam: Continuum 1.9"x0.9"  
  > "with a 1.9$''$$\times$0.9$''$ beam" (2 Data)
- final rms: Continuum 3.6 mJy/beam; cube ~4.5 mJy/beam/channel  
  > "final rms noise level of 3.6 m$\rm Jy\,beam^{-1}$" (2 Data)

### Inherited from earlier work

- Two-slab infall line profile model  
  > "Here we used the simple two-slab model described by (cite: Myers_1996-Line_Profile_Model_Infall) with the modification introduced by (cite: DiFrancesco_2001-NGC1333IRAS4_dynamics)" (3.2 Evidence for Infalling gas toward source B) [from Myers et al. 1996 (cite: Myers_1996-Line_Profile_Model_Infall); Di Francesco et al. 2001 (cite: DiFrancesco_2001-NGC1333IRAS4_dynamics)]
- Beam filling fraction Phi = 0.3  
  > "was set to 0.3 to use the same value as (cite: DiFrancesco_2001-NGC1333IRAS4_dynamics)" (A The two-layer model) [from Di Francesco et al. 2001 (cite: DiFrancesco_2001-NGC1333IRAS4_dynamics)]

### Not stated but needed to reproduce (our reading)

- Clean masks, threshold, image size and cell size
- Weighting/robust and primary-beam correction for the mosaic
- Self-calibration solution intervals and number of iterations
- Channel ranges used for continuum subtraction fit
- Exact region and fitting velocity range for line profiles
- Procedure for the PV cut and the 0.53 Msun mass derivation
- Temperature assumed for source masses beyond the 30 K in the formula

## Analysis recipe

1. **Calibrate and image data**: CASA calibration, Hanning smoothing/binning, Clark CLEAN, continuum self-calibration applied to cube  
  > "we applied the self-calibration derived from the continuum emission to the spectral data" (2 Data)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Estimate continuum masses**: Optically thin dust mass from 1.3 mm flux over 10-sigma region  
  > "where we assumed optically thin emission and a dust opacity per dust mass ($\kappa_{1.3~mm}$) of 0.86 cm$^{2}$ g$^{-1}$ (cite: OH94) and a gas-to-dust ratio of 100." (3.1 Continuum emission and molecular complexity)
   - assumption: optically thin, gas-to-dust 100, kappa 0.86 cm2/g, T=30 K in formula  
  > "a gas-to-dust ratio of 100" (3.1 Continuum emission and molecular complexity)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit inverse P-Cygni profiles toward B**: Two-layer model chi2 fit of Vin, tau0, sigma_v, Tr; fixed VLSR=3.4, Tc=20 K, Tf=3 K, Phi=0.3  
  > "The $\chi^{2}$ was minimized using the `mpfitfun` procedure (cite: IDL_MPFIT)" (A The two-layer model)
   - software: IDL MPFIT
   - parameter: Tf fixed at 3 K; Phi = 0.3; VLSR = 3.4 km/s  
  > "The following parameters are kept fixed: $V_{LSR}=3.4\,{\ensuremath{{\rm km\, s^{-1}}}}$, $T_c=20$ K, $T_f=3$ K, and $\Phi=0.3$." (Table 1 notes)
   - assumption: Blue excess not fitted; fit constrained by absorption  
  > "The blue excess in the line profiles is not fitted, and therefore the fit is mostly constrained by the absorption feature" (3.2 Evidence for Infalling gas toward source B)
   - fitting: chi2 minimization with mpfitfun  
  > "The $\chi^{2}$ was minimized using the `mpfitfun` procedure (cite: IDL_MPFIT)" (A The two-layer model)
   - validation: Tested higher Phi and Tc: Vin and sigma_v unchanged  
  > "Therefore our results are robust to the value of $\Phi$ and $T_{c}$ used." (A The two-layer model)
4. **Derive infall rate**: Free-fall spherical estimate Mdot = 3 Vin^3/(2G)  
  > "\dot{M}_{infall}= \frac{3 V_{in}^{3}}{2G} = 4.5 \times 10^{-5} \left(\frac{V_{in}}{0.5\,{\ensuremath{{\rm km\, s^{-1}}}}}\right)^{3}" (3.2 Evidence for Infalling gas toward source B)
   - assumption: spherical symmetry, free-fall, mu=2.3  
  > "$\mu$ is mean molecular weight of the gas (2.3)" (3.2 Evidence for Infalling gas toward source B)
   - fitting: _not stated_
   - validation: _not stated_
5. **Velocity maps and PV diagrams**: Intensity-weighted velocity maps and PV cuts for source A to infer rotation  
  > "The position velocity (PV) diagrams for source A (along the direction shown in Fig. [5](#fig-w-line)) are consistent with rotation of a disk" (3.3 Velocity maps)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 3.3.0: calibration and imaging  
  > "We calibrated and imaged the original interferometric data with the CASA[^3] software version 3.3.0." (2 Data)
- **MPFIT (mpfitfun, IDL)** : chi2 minimization of line profile model  
  > "The $\chi^{2}$ was minimized using the `mpfitfun` procedure (cite: IDL_MPFIT)" (A The two-layer model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total continuum flux, source A | 1.30 | 0.11 | Jy | 2 | for sources A and B is 1.30$\pm$0.11 and 1.06$\pm$0.15 Jy, respectively |
| Total continuum flux, source B | 1.06 | 0.15 | Jy | 2 | for sources A and B is 1.30$\pm$0.11 and 1.06$\pm$0.15 Jy, respectively |
| Mass from continuum, A and B | 0.21 (A), 0.26 (B) | not stated | Msun | 2 | which implies a mass of 0.21 and 0.26 $M_{\odot}$ for sources A and B, respectively |
| Infall velocity Vin (CH3OCHO-A) | 0.49 | 0.02 | km/s | 3 | / CH$_3$OCHO-A / 46$\pm$3 / 0.45$\pm$0.04 / 0.49$\pm$0.02 / 0.31$\pm$0.01 / |
| Infall rate onto B | 4.5e-5 | not stated | Msun/yr | 4 | derive an infall rate of $4.5\times 10^{-5}$$M_{\odot}\,{\rm yr^{-1}}$ |
| Velocity variation across source A | ~5.5 | not stated | km/s | 5 | with a velocity variation of $\sim$5.5 ${\rm km\, s^{-1}}$ across the extent of the molecular emission |
| Central mass of A from rotation | 0.53 | not stated | Msun | 5 | generated by a central object of 0.53$M_{\odot}$ |

## Qualitative findings

- About 50 molecular transitions detected toward the two continuum sources  
  > "many ($\sim$50) molecular transitions are detected toward the two continuum sources" (3.1 Continuum emission and molecular complexity)

## Claim tuples

- H: Is there infall onto source B? | E: Fit two-layer model to inverse P-Cygni profiles in three lines | R: Vin ~0.5 km/s; infall rate ~4.5e-5 Msun/yr | F: Infall detected in B, ruling out T Tauri nature | **supported**
- H: Does source A show rotation? | E: Velocity maps and PV diagrams | R: ~5.5 km/s gradient | F: Consistent with near edge-on rotation, though a close binary is not excluded | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Absorption from ambient cloud/envelope rejected since complex organics trace hot corino  
  > "Therefore, we can rule out the absorption from the ambient cloud or ambient envelope" (4 Discussion and conclusion)
- How they decided it was enough: _not stated_
- Limitation (authors): Model has more parameters than can be constrained due to degeneracies  
  > "the two-layer model contains more parameters than can be fully constrained because of degeneracies in the model" (3.2 Evidence for Infalling gas toward source B)
- Caveat (inferred, ours): Infall rate relies on free-fall and uniform-sphere assumptions
- Caveat (inferred, ours): Fixed Phi, Tc, Tf arbitrary; Tr and tau0 degenerate
- Caveat (inferred, ours): Rotation inference limited by beam; binary alternative open

## Reproducibility

- Data public (paper): Public since April 2012  
  > "is publicly available since April 2012" (2 Data)
- Products in archive: _not stated_
- Missing: Clean parameters and self-cal settings
- Missing: PV cut geometry and mass derivation details
- Data volume (inferred): ~tens of GB
- Score (inferred): 3/5, Public SV data and clear model, but imaging and self-cal parameters are missing.
- Rediscovery candidate: yes, Public data, explicit model with fixed parameters, numeric results in Table 1.

## Links

- Method: Myers et al. 1996 (cite: Myers_1996-Line_Profile_Model_Infall) (Two-slab model)
- Method: Di Francesco et al. 2001 (cite: DiFrancesco_2001-NGC1333IRAS4_dynamics) (Continuum modification of model)
- Companion: Jorgensen et al. 2011 (cite: Jorgensen_2011-SMA_IRAS16293) (SMA comparison of same spectral range)
- Related: ALMA Science Verification

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
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
  "facts": 70,
  "stated": 43,
  "rate": 0.614
 },
 "evidence_ok": true
}
```

# Detection of CO and HCN in Pluto's atmosphere with ALMA

`2017Icar..286..289L` | Icarus 2017 | first author: Lellouch, E. | arXiv: 1606.03293 | DOI: 10.1016/j.icarus.2016.10.013

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: solar_system
- Question: Detect CO and HCN (and search for HC3N, HC15N) in Pluto's atmosphere with ALMA and constrain the CO abundance, the thermal structure and the HCN distribution.  
  > "In this paper, we report on searches for CO, HCN and HC$_3$N in Pluto’s atmosphere with ALMA, leading to the strong confirmation of CO and the first detection of HCN." (Introduction)
- Target **Pluto (and Charon)**: coordinates _not stated_; z/distance 31.958 AU (Jun 12), 31.952 AU (Jun 13) geocentric  
  > "2015-Jun-12 | 04:15–05:55 | 31.958 | 157 | 0.70" (Table 2); distance from geometric parameters in Table 2 (source not stated)  
  > "2015-Jun-12 | 04:15–05:55 | 31.958 | 157 | 0.70" (Table 2)

## Data provenance

- ALMA projects: 2013.1.00446.S
- bands: Band 7 (~350 GHz)  
  > "Observations reported here were taken in Band 7, near 350 GHz." (Observations and data reduction)
- frequencies and spectral setup: One TDM continuum window (354-356 GHz) and three FDM line windows: CO(3-2) at 0.141 MHz, HCN(4-3) at 0.282 MHz, HC15N(4-3) at 0.488 MHz  
  > "1 | 345.598–345.832 | 0.141 | CO(3-2); 345.796" (Table 1); "2 | 354.380–354.849 | 0.282 | HCN(4-3); 354.505" (Table 1)
- continuum bandwidth: _not stated_
- arrays: 12-m array, 39 antennas  
  > "There were 39 operating antennas in the array, in the C36-7 configuration." (Observations and data reduction)
- configurations: C36-7  
  > "There were 39 operating antennas in the array, in the C36-7 configuration." (Observations and data reduction)
- baselines: max ~800 m  
  > "which has a maximum antenna separation of $\sim$ 800 m" (Observations and data reduction)
- angular resolution: ~0.35 arcsec  
  > "yielded at these frequencies a $\sim$0.35$^{\prime\prime}$ resolution (i.e., 8100 km at Pluto’s distance)" (Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: rms 3.28 mJy (CO, 141 kHz), 2.85 mJy (HCN, 282 kHz), 1.88 mJy (HC15N, 488 kHz)  
  > "With 1-$\sigma$ rms residuals of 3.28 mJy and 2.85 mJy, this gives a S/N detection of 19 for CO and 35 for HCN at the peak." (Data assessment)
- time on source: ~55 min on Pluto/Charon per date (1 h 40 min total)  
  > "On each date, the entire observation took 1 hour 40 minutes, of which about 55 minutes were on Pluto/Charon." (Observations and data reduction)
- observing dates: June 12 and June 13, 2015  
  > "The observations were undertaken on two separate dates, June 12 and June 13, 2015." (Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: CO 3-2 (345.796 GHz)
- Line: HCN 4-3 (354.505 GHz)
- Line: HC3N 38-37 and 39-38 (345.609 and 354.697 GHz)
- Line: HC15N 4-3 (344.200 GHz)
- Other facility **New Horizons (Alice, REX)**: Temperature profile and N2/CH4 line-of-sight columns used as a priori and for consistency tests  
  > "Fig. 11 compares the Alice LOS data (as shown in (cite: gladstone16), and kindly provided to us by J. Kammer) to models." (5.1.1 New Horizons/Alice)
- Other facility **Stellar occultations (VLT/NaCO 2012 July 18)**: Occultation temperature profiles and lightcurve for comparison  
  > "in practice, we used the high S/N 2012 July 18 occultation observed with VLT/NaCO." (5.1.2 Stellar occultations)
- External data: A priori temperature profile from stellar occultations  
  > "We started with the nominal temperature profile derived from stellar occultations by (cite: dias15)." (4.1.2 Results) [from (cite: dias15)]
- External data: New Horizons standard temperature profile (Alice + REX) used as a priori  
  > "the "standard" profile derived from New Horizons (cite: gladstone16), which combines results from Alice (above 200 km) and REX (below 60 km)" (4.1.2 Results) [from (cite: gladstone16)]
- External data: HCN vapor pressure law  
  > "using for that purpose the HCN vapor pressure vs temperature dependence provided by (cite: fray09)" (4.2.2 HCN initial fits) [from (cite: fray09)]
- External data: Line parameters for CO and HCN including hyperfine structure  
  > "Line opacities for CO and HCN were calculated using line parameters from the Cologne database (cite: muller01), including the hyperfine structure for HCN." (4 Modelling and analysis) [from (cite: muller01)]
- External data: N2 collisional broadening coefficients  
  > "Collisional broadening by N$_2$ were taken from (cite: koshelev09), (cite: priem00) and (cite: yang08)" (4 Modelling and analysis) [from (cite: koshelev09), (cite: priem00), (cite: yang08)]
- External data: HCN(4-3) collisional excitation coefficient by He  
  > "an excitation coefficient of 9$\times$10$^{-12}$ cm$^3$s$^{-1}$ for HCN(4-3) by He (cite: dumouchel10)" (4 Modelling and analysis) [from (cite: dumouchel10)]
- External data: Titan flux density model used for absolute flux scale  
  > "using a standard model for Titan (cite: butler12)" (Observations and data reduction) [from (cite: butler12)]
- Simulation/model as data: Preliminary HCN profile from coupled photochemical-microphysical model (Lavvas et al., in prep.), rescaled by 1/2 and compared with the ALMA HCN line  
  > "Testing it against the ALMA observations indicates that a good agreement is obtained by uniformly dividing the calculated HCN mixing ratio in the model by 2." (5.3 HCN profile)

## Processing

### Calibration

- pipeline or manual: Initial calibration provided by the ALMA observatory in CASA; then self-calibration in AIPS  
  > "Initial calibration of the data was provided by the ALMA observatory, and done in the CASA reduction package, version 4.3.1 (cite: muders14)." (Observations and data reduction)
- casa version: CASA 4.3.1  
  > "done in the CASA reduction package, version 4.3.1" (Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (bandpass/delay J1924-2914; phase J1911-2006)  
  > "We observed the calibrator J1924-2914 to calibrate bandpass and delay, and Titan for absolute flux density calibration." (Observations and data reduction)
- flux scale uncertainty: 5%  
  > "The expected overall flux density scale accuracy is 5%, using a standard model for Titan" (Observations and data reduction)
- self calibration: Phase self-cal on continuum window with solution intervals of 5, 2, 1 min; solutions applied to line windows  
  > "We did this iteratively with solution intervals of 5, 2, and 1 minute." (Observations and data reduction)

### Imaging

- task: Spectra obtained by averaging continuum-subtracted visibilities per channel (no image); Doppler correction with fixplanets() and cvel()  
  > "Finally, averaging continuum-subtracted visibilities for each spectral channel yielded the spectra in each of the target lines." (Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Visibility-domain subtraction using average of channels far outside the line (continuum 18.2 mJy CO, 18.9 mJy HCN)  
  > "We did this in the visibility domain, using an average of spectral channels that were far outside the line emission region (cite: vanlange90)." (Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: ~0.35 arcsec HPBW  
  > "the beam ($\sim$0.35" HPBW), convolution effects amount to a typical 10 % flux loss." (Observations and data reduction)
- final rms: _not stated_

### Inherited from earlier work

- Continuum subtraction technique  
  > "using an average of spectral channels that were far outside the line emission region (cite: vanlange90)" (Observations and data reduction) [from (cite: vanlange90)]
- Temperature retrieval algorithm (constrained, regularized inversion)  
  > "we used a constrained and regularized algorithm following methods detailed in (cite: conrath98) and (cite: rodgers00)" (4.1.1 Method) [from (cite: conrath98), (cite: rodgers00), (cite: fouchet16)]
- Diffusion model formalism for CH4-N2  
  > "using the formalism of (cite: yelle06) for two gases in comparable abundance" (5.1.1 New Horizons/Alice) [from (cite: yelle06)]
- Continuum measurements to be described in a future publication  
  > "Continuum measurements have been briefly presented (cite: butler15) and will be described in detail in a future publication." (Observations and data reduction) [from (cite: butler15)]

### Not stated but needed to reproduce (our reading)

- The radiative transfer and inversion code is custom and not released; reproduction requires reimplementation.
- Which channels were treated as line-free and the AIPS imaging parameters for the continuum self-calibration (weighting, cell size) are not given.
- Calibration scheduling-block names or pipeline script versions and flagging are not specified.
- Exact a priori temperature profiles (mixed profile weights, correlation matrix details) and error covariance values are not tabulated.
- Pluto position and ephemeris used for fixplanets are not stated.
- Lavvas et al. HCN model profile is unpublished.

## Analysis recipe

1. **Calibrate and prepare visibilities**: ALMA-provided CASA calibration, Doppler correction with fixplanets and cvel, then AIPS self-calibration on continuum window applied to line windows  
  > "This correction was done with the CASA tasks *fixplanets()* and *cvel()*." (Observations and data reduction)
   - software: CASA, AIPS
   - parameter: Self-cal solution intervals 5, 2, 1 min  
  > "We did this iteratively with solution intervals of 5, 2, and 1 minute." (Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract continuum-subtracted line spectra**: Visibility-domain continuum subtraction, then average visibilities per channel to obtain spectra; average June 12 and 13  
  > "Data from the two days were therefore averaged for further analysis." (Data assessment)
   - software: AIPS
   - assumption: Spectra represent central pointing flux; ~10% flux loss from beam convolution  
  > "convolution effects amount to a typical 10 % flux loss." (Observations and data reduction)
   - fitting: Gaussian fits of CO line for day-to-day comparison  
  > "gaussian fits of the CO line indicate peak contrasts of 58.1 and 62.8 mJy for June 12 and 13, respectively" (Data assessment)
   - validation: Two dates consistent within 1 sigma  
  > "Data from the two different days do not show significant differences." (Data assessment)
3. **Retrieve CO mole fraction and temperature profile**: Spherical-geometry LTE radiative transfer model (181 layers, 0-1300 km) convolved with 0.35" beam; iterative regularized optimal-estimation inversion with fixed-CO and free-CO runs and several a priori profiles  
  > "The model covers the 0-1300 km altitude range by means of 181 layers, with an altitude-varying layer thickness." (4 Modelling and analysis)
   - software: custom radiative transfer code
   - parameter: Surface pressure 12 μbar nominal (10, 14 tested); CO uniformly mixed; correlation length = scale height; convergence when fit rms constant within 1%  
  > "Iterations were performed until convergence – defined by the constancy of the fit quality (rms between observations and models) within 1 % from an iteration to the next one – was reached." (4.1.1 Method)
   - assumption: LTE; molecular mass 27.94; surface radius 1190 km; Fresnel surface with dielectric constant 3.5  
  > "Emission from the surface was calculated by using a Fresnel-emission model with a dielectric constant of 3.5" (4 Modelling and analysis)
   - fitting: Optimal-estimation (Conrath/Rodgers) with alpha set by equalling traces of alpha K S K^T and E  
  > "an optimum choice of $\alpha$ (in terms of stability and rapidity of the algorithm) was achieved by equalling the traces of the $\alpha$**KSK$^T$** and **E** matrices." (4.1.1 Method)
   - validation: Reduced chi2 ~0.95; averaging kernels; tests of a priori, surface pressure and ±5% calibration  
  > "the best fit corresponded to a reduced $\chi^2$ of $\sim$0.95 over a $\pm$15 MHz interval centered on the CO(3-2) line frequency" (4.1.1 Method)
4. **Constrain HCN vertical distribution**: Manual fits with parametrized HCN profiles (uniform, saturated, step, two-component) and inversion retrievals using the CO-derived nominal temperature profile; test warm-layer solutions  
  > "At this stage, we obtained an optimum manual fit of the HCN spectrum (solid light blue line in Fig. 6) with a two-component HCN distribution" (4.2.2 HCN initial fits)
   - software: custom radiative transfer code
   - parameter: Saturation from Fray & Schmitt vapor pressure; nominal profile has 106 K stratopause  
  > "calculated as saturated HCN for the adopted temperature profile (with a 106 K stratopause)" (4.2.2 HCN initial fits)
   - assumption: Warm-layer tests required HCN at saturation everywhere  
  > "requiring that HCN is at saturation throughout the atmosphere." (4.2.4 Evidence for HCN supersaturation)
   - fitting: Manual fits plus optimal-estimation retrievals with several a priori HCN profiles  
  > "Similar HCN profiles are returned for various a priori values of the HCN mole fraction" (4.2.3 HCN retrievals)
   - validation: Averaging kernels; consistency test against New Horizons/Alice CH4/N2 LOS columns and occultation lightcurve  
  > "We conclude that alternate solutions with an HCN profile at saturation, while not excluded from the sole point-of-view of the ALMA data, are not viable" (5.1.1 New Horizons/Alice)
5. **Upper limits on HC15N and HC3N**: Scale the best-fit HCN model by constant isotope ratio or assume HC3N has the HCN distribution; compare with non-detections at 2 sigma  
  > "Using our best fit HCN model (light blue line from Fig. 6) and scaling it by a vertically constant isotopic ratio factor" (4.3 HC15N and HC3N upper limits)
   - software: custom radiative transfer code
   - assumption: HC3N has same vertical distribution as HCN  
  > "Assuming here for simplicity that HC$_{3}$N has the same distribution as our best fit HCN model" (4.3 HC15N and HC3N upper limits)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.3.1: Initial calibration; fixplanets and cvel Doppler correction  
  > "This correction was done with the CASA tasks *fixplanets()* and *cvel()*." (Observations and data reduction)
- **AIPS** : Self-calibration, continuum subtraction and spectrum extraction  
  > "At this point we exported the data from CASA and continued the data reduction in the AIPS package" (Observations and data reduction)
- **Custom radiative transfer and inversion code** : Spherical-geometry radiative transfer and retrievals  
  > "we developed our own radiative transfer code, fully accounting for the spherical geometry" (4 Modelling and analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(3-2) peak S/N (averaged) | 19 | not stated | dimensionless | 2 | this gives a S/N detection of 19 for CO and 35 for HCN at the peak |
| CO mole fraction at 12 μbar | 515 | ±40 | ppm | 3 | We conclude that the CO mole fraction in Pluto’s atmosphere is 515 $\pm$ 40 ppm for p$_{surf}$ = 12 $\mu$bar |
| CO surface-referred column density at 12 μbar | 0.100 | ±0.008 | cm-am | 3 | (2.69$\pm$0.21)$\times$10$^{18}$ mol cm$^{-2}$ (0.100$\pm$0.008 cm-am) for p$_{surf}$ = 12 $\mu$bar |
| Temperature at 300 km | 70 | ±2 | K | 3 | with a best determined temperature of 70$\pm$2 K at 300 km |
| HCN column density | 1.6e14 | ±0.4e14 | cm^-2 | 4 | The HCN column is (1.6$\pm$0.4)$\times$10$^{14}$ cm$^{-2}$ |
| HCN mole fraction near 800 km | 4e-5 | not stated | dimensionless | 4 | a best determined value of 4$\times$10$^{-5}$ near 800 km |
| HC3N column upper limit | <2e13 | not stated | cm^-2 | 5 | corresponding to a maximum HC$_{3}$N column density of 2$\times$10$^{13}$ cm$^{-2}$ (Fig. 10) |
| HC14N/HC15N lower limit (2 sigma) | 125 | not stated | dimensionless | 5 | implies a lower limit of the HC$^{14}$N / HC$^{15}$N ratio equal to 125 at 2$\sigma$ confidence level |
| HCN surface-referred net production rate | ~2e7 | not stated | cm^-2 s^-1 | 4 | This suggests a surface-referred net column production rate of $\sim$2$\times$10$^{7}$ cm$^{-2}$s$^{-1}$. |

## Qualitative findings

- HCN hyperfine satellite lines detected; CO and HCN lines have large limb-emission contribution  
  > "directly implies that a significant fraction of the emission originates from limb viewing" (Data assessment)

## Claim tuples

- H: Is CO present in Pluto's atmosphere and at what abundance? | E: Band 7 ALMA CO(3-2) spectrum and radiative transfer inversion | R: CO mole fraction 515±40 ppm at 12 μbar | F: CO confirmed; much improved abundance, favoring ideal solid solution | **supported**
- H: What is the upper-atmosphere temperature structure? | E: Inversion of CO line with multiple a priori profiles | R: 70±2 K at 300 km with a mesosphere above the stratopause | F: Colder than occultation-derived 81±6 K, in agreement with Alice | **supported**
- H: Is HCN present, and how is it distributed? | E: Fits and retrievals of HCN(4-3) main and satellite lines | R: HCN mole fraction >1.5e-5 above 450 km, 4e-5 near 800 km, plus 1e-8–1e-7 in lower 100 km | F: HCN highly supersaturated (7-8 orders of magnitude) in the upper atmosphere | **supported**
- H: Can HCN cooling explain the cold upper atmosphere? | E: Radiative-conductive calculations with several HCN profiles | R: Observed HCN would require 20-200 times more to reach ~70 K | F: HCN cooling insufficient; heat budget unexplained | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Nitriles have strong rotational lines well suited to mm/submm searches  
  > "nitriles exhibit strong rotational lines and are thus well suited to mm/submm searches" (Introduction)
- Alternative: Warm (92-98 K) upper layer allowing saturated HCN: consistent with ALMA but rejected using Alice CH4/N2 data  
  > "alternate solutions with an HCN profile at saturation, while not excluded from the sole point-of-view of the ALMA data, are not viable" (5.1.1 New Horizons/Alice)
- How they decided it was enough: _not stated_
- Limitation (authors): Lower mesosphere and stratopause temperatures are more uncertain, and the HCN vertical distribution is not unique given moderate optical thickness  
  > "the lower mesosphere and stratopause temperatures must be considered as more uncertain." (5.1.2 Stellar occultations)
- Limitation (authors): Spatial resolution insufficient to resolve surface  
  > "This is sufficient to separate the emission of Pluto from Charon, but not enough to provide spatial resolution on the surface of these bodies." (Observations and data reduction)
- Caveat (inferred, ours): Disk-integrated, unresolved data make temperature and HCN profiles degenerate and dependent on a priori.
- Caveat (inferred, ours): CO abundance depends strongly on surface pressure (scales as p^-1.9).
- Caveat (inferred, ours): Custom code unreleased; LTE assumed for HCN to ~1150 km.
- Caveat (inferred, ours): Day-side only; comparison with occultations assumes no temporal/spatial variation.

## Reproducibility

- Data public (paper): ALMA program 2013.1.00446.S named; public availability not explicitly stated  
  > "This paper is based on ALMA program 2013.1.00446.S." (Acknowledgements)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: Radiative transfer/inversion code
- Missing: A priori profile details and the 'mixed' profile
- Missing: AIPS imaging and line-free channel selection
- Missing: Lavvas et al. HCN model profile
- Missing: Alice LOS data provided privately
- Data volume (inferred): ~10-50 GB (two ~1.7 h execution blocks, Band 7, four spectral windows)
- Score (inferred): 3/5, Data identified and calibration/analysis described in good detail, but the custom retrieval code and several settings are unavailable.
- Rediscovery candidate: no, Main results depend on a custom radiative transfer and inversion code and unstated a priori choices, so the recipe is not complete enough to redo.

## Links

- Method: (cite: conrath98); (cite: rodgers00); (cite: fouchet16) (Inversion formalism used for temperature retrieval)
- Method: (cite: vanlange90) (Visibility-domain continuum subtraction)
- Companion: (cite: gladstone16) (New Horizons atmosphere results used as a priori and comparison)
- Companion: (cite: dias15) (Occultation temperature profile used as a priori)
- Companion: (cite: butler15) (Continuum measurements from the same ALMA data)
- Related: New Horizons
- Related: ALMA program 2013.1.00446.S

## Checks

```json
{
 "quotes": 82,
 "quotes_ok": 82,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 87,
  "stated": 61,
  "rate": 0.701
 },
 "evidence_ok": true
}
```

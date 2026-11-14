# The Slow Ionized Wind and Rotating Disklike System that are Associated with the High-mass Young Stellar Object G345.4938+01.4677

`2014ApJ...796..117G` | The Astrophysical Journal 2014 | first author: Guzmán, Andrés E. | arXiv: 1410.0233 | DOI: 10.1088/0004-637X/796/2/117

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: Is the ionized gas around the high-mass YSO G345.49+1.47 a slow photo-ionized wind rather than a fast jet, as probed by 3 mm continuum and hydrogen recombination lines, and do sulfur-bearing molecules trace a rotating disklike core?  
  > "The set of observations toward G345.4938+01.4677 are consistent with it being a young high-mass star associated with a slow photo-ionized wind." (abstract)
- Target **G345.4938+01.4677 (in IRAS 16562-3959)**: coordinates RA 16h59m41.63s, Dec -40d03m43.61s (J2000)  
  > "we adopt a distance to IRAS 16562$-$3959 of 1.7 kpc (cite: Lopez2011AA)." (1 Introduction); "The phase center of the array was R.A.$=16^{\rm h}59^{\rm m}$41.63s, decl.$=-$40$^\circ$03$'$43.61$''$ (J2000)" (2 Observations); z/distance 1.7 kpc  
  > "we adopt a distance to IRAS 16562$-$3959 of 1.7 kpc (cite: Lopez2011AA)." (1 Introduction); "The phase center of the array was R.A.$=16^{\rm h}59^{\rm m}$41.63s, decl.$=-$40$^\circ$03$'$43.61$''$ (J2000)" (2 Observations); distance from Lopez2011AA  
  > "we adopt a distance to IRAS 16562$-$3959 of 1.7 kpc (cite: Lopez2011AA)." (1 Introduction); "The phase center of the array was R.A.$=16^{\rm h}59^{\rm m}$41.63s, decl.$=-$40$^\circ$03$'$43.61$''$ (J2000)" (2 Observations)

## Data provenance

- ALMA projects: 2011.0.00351.S
- bands: Band 3 (3 mm)  
  > "We observed G345.49+1.47 for $\sim$188 minutes on-source in Band-3, which covers the 3 mm atmospheric window, in 5 scheduling blocks." (2 Observations)
- frequencies and spectral setup: 4 SpWs of 1.875 GHz, 3840 channels of 488 kHz, centered 85.4, 87.2, 97.6, 99.3 GHz; ~3.0 km/s effective resolution  
  > "Each SpW consisted of 3840 channels of 488 kHz width and were centered at 85.4, 87.2, 97.6, and 99.3 GHz." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: 12-m antennas, 17 (two SBs) and 25 (three SBs)  
  > "Two scheduling blocks were observed with 17 12-m antennas, and the other three with 25." (2 Observations)
- configurations: Cycle 0 extended array, baselines 21-453 m  
  > "during Cycle 0 using the extended array configuration (longest and shortest baselines 453 and 21 m, respectively)" (2 Observations)
- baselines: _not stated_
- angular resolution: typically 2.3" x 1.3", PA 97 deg  
  > "which was typically $2.3\ensuremath{''}\times1.3\ensuremath{''}$ with a position angle of 97$^\circ$" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: continuum ~50 uJy/beam; lines 1-2 mJy/beam per channel  
  > "The noise level achieved in the continuum maps for each SpW was typically 50 $\mu$Jy beam$^{-1}$" (2 Observations)
- time on source: ~188 minutes  
  > "We observed G345.49+1.47 for $\sim$188 minutes on-source" (2 Observations)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: H40alpha recombination (99022.95 MHz)
- Line: H42alpha recombination (85688.39 MHz)
- Line: H50beta recombination (86846.96 MHz)
- Line: SO2 8(3,5)-9(2,8) (86639.088 MHz)
- Line: SO J_N=4_5-4_4 (100029.64 MHz)
- Other facility **ATCA**: 8.6 GHz and other cm continuum of the jet and lobes (from earlier work)  
  > "overlaid with contours at 8.6 GHz emission" (4.2 The ionized jet observed at 92 GHz)
- External data: Centimeter continuum jet/lobe fluxes and spectral index below 10 GHz (0.85+-0.15), inclination ~45 deg, momentum rate  
  > "The inclination angle $i$ was estimated as $\sim45$$^\circ$ by (cite: Guzman2010ApJ), based on the appearance of the 2 $\mu$m image of the inner cavity" (4.4.1 Collimated ionized jet model) [from (cite: Guzman2010ApJ)]
- External data: Distance 1.7 kpc  
  > "we adopt a distance to IRAS 16562$-$3959 of 1.7 kpc (cite: Lopez2011AA)." (1 Introduction) [from (cite: Lopez2011AA)]
- External data: Line frequencies and Eu from JPL and CDMS via Splatalogue  
  > "obtained from the JPL (cite: Pickett1998JQSRT) and CDMS (cite: Muller2001AA) databases consulted through the Splatalogue" (3.3 Sulfuretted molecules) [from (cite: Pickett1998JQSRT; Muller2001AA; Remijan2007AAS)]

## Processing

### Calibration

- pipeline or manual: Recalibrated with CASA  
  > "We recalibrated the data using the Common Astronomy Software Applications (CASA) (cite: Petry2012ASPC)." (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune and Titan (Butler-JPL-Horizons 2012 model); bandpass J1924-292, 3C279; gain J1717-337  
  > "The sources Neptune and Titan were used as flux calibrators,[^2] J1924$-$292 and 3C279 were used as bandpass calibrators, and J1717$-$337 was used as a gain calibrator." (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: one additional phase self-calibration iteration  
  > "which allowed us to perform an additional phase self-calibration iteration." (2 Observations)

### Imaging

- task: CASA clean  
  > "deconvolved using the `clean` task within CASA" (2 Observations)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0  
  > "robust parameter $=0$" (2 Observations)
- uv taper: _not stated_
- cell size: 0.3" x 0.3"  
  > "The pixel size used was $0.3\ensuremath{''}\times0.3\ensuremath{''}$ in all cases." (2 Observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub after masking lines by visual inspection  
  > "This continuum was subtracted from the visibility data using the CASA task ` uvcontsub`." (2 Observations)
- line free channels: _not stated_
- primary beam correction: fluxes corrected for primary beam response  
  > "Fluxes are corrected for primary beam response." (Table 2)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: ~50 uJy/beam continuum; 1-2 mJy/beam per channel  
  > "achieving noise levels of 1-2 mJy beam$^{-1}$" (2 Observations)

### Inherited from earlier work

- Jet source position, inclination, momentum rate and lobe naming taken from earlier work  
  > "Following the (cite: Guzman2010ApJ) naming convention, the two outermost lobes are referred to as outer-east (O-E) and outer-west (O-W) lobes" (4.2 The ionized jet observed at 92 GHz) [from (cite: Guzman2010ApJ)]
- Jet model parameterization  
  > "A useful parameterization of the jet structure is given in (cite: Reynolds1986ApJ)." (4.4.1 Collimated ionized jet model) [from (cite: Reynolds1986ApJ)]
- Weighted least-squares fitting procedure  
  > "obtained by weighted least-squares (or $\chi^2$) minimization using the procedure described in (cite: Lampton1976ApJ)" (3.1 Continuum emission) [from (cite: Lampton1976ApJ)]
- Dynamical mass formula  
  > "simplified version of Equation (1) from (cite: Franco-Hernandez2009ApJ)" (4.5.3 Dynamics of the molecular emission) [from (cite: Franco-Hernandez2009ApJ)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges used for continuum fitting and uvcontsub
- Clean masks, thresholds and iteration counts
- Self-calibration solution interval
- Hanning smoothing details
- Exact CASA version
- Box/aperture used to extract HRL spectra at peak
- Fit optimizer for Voigt and SET models
- Pixel/channel selection for PV diagram and moment maps (clipping)
- Cm-wavelength flux data used for 1-100 GHz spectrum

## Analysis recipe

1. **Recalibrate and image continuum and cubes**: CASA recalibration, phase self-cal, clean with robust 0, uvcontsub  
  > "Maps were generated by Fourier transformation of the robust-weighted visibilities (cite: Briggs1995PhD), robust parameter $=0$, and deconvolved using the `clean` task within CASA." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Noise comparable to theoretical sensitivity from the ALMA Observing Tool  
  > "The continuum and spectral cube noise levels attained are comparable to the theoretical sensitivity calculated using the ALMA Observing Tool" (2 Observations)
2. **Measure continuum sources and spectral indices**: maxfit peak positions, imfit 2D Gaussians for sources 10 and 13, box-integrated fluxes, weighted least-squares spectral index  
  > "The coordinates correspond to the position of the emission peak determined by using the CASA function `maxfit`, except for Sources 10 and 13, for which we fit two 2-D Gaussians using the CASA task ` imfit`." (3.1 Continuum emission)
   - software: CASA
   - parameter: detection threshold 0.75 mJy; boxes of two times beam size; flux uncertainty 2 sigma ~0.1 mJy  
  > "we integrated the flux density within boxes of two times the size of the beam" (3.1 Continuum emission)
   - fitting: chi2 minimization (Lampton et al. 1976)  
  > "Best-fit spectral indexes and their uncertainties were obtained by weighted least-squares (or $\chi^2$) minimization using the procedure described in (cite: Lampton1976ApJ)." (3.1 Continuum emission)
   - validation: _not stated_
3. **Fit Voigt profiles to HRLs and derive electron density**: Joint chi2 minimization of Voigt functions over three HRLs between -80 and 100 km/s with shared T; Gaussian width 0.22 sqrt(T); Ne from Griem/Walmsley relation  
  > "the second sum runs over the channels ($v_i$) between the $V_{\rm LSR}$ limits $V_l=-80$ and $V_m=100$ km s$^{-1}$." (4.3.1 Voigt profile fitting)
   - parameter: sigma = 1 mJy per channel; T fixed at 7000 K after fit  
  > "we fixed the value of the temperature of the ionized gas as $T=7000$ K" (4.3.1 Voigt profile fitting)
   - assumption: Te = 7000 K  
  > "Assuming $T_{e} = 7000$ K for the three lines." (Table 5)
   - fitting: Weighted least squares, 10 free parameters  
  > "The free parameters of the Voigt model are 10, while for two independent Gaussians per HRL they are 18." (4.3.1 Voigt profile fitting)
   - validation: Akaike information criterion vs single/double Gaussians  
  > "performs better than single or double Gaussian models evaluated by a heuristic visual assessment and according to the quantitative Akaike information criterion" (4.3.1 Voigt profile fitting)
4. **Model continuum and HRLs with ionized wind model**: Reynolds-type isothermal power-law jet model; LTE line flux from integral over continuum opacity  
  > "under assumptions of isothermality and local thermodynamic equilibrium (LTE), is derived in appendix" (4.4.2 Model prediction for HRLs)
   - parameter: i=45 deg, r0=100 AU, S100GHz=120.6 mJy, alpha_op=0.92, T0=7000 K; conical eps=1, theta0=0.33, Ne0=2.19e7 cm-3  
  > "$\epsilon=1$&,~~\theta_0=0.33,~~N_{e,0}=2.19\times10^7~\text{cm}^{-3}\quad\text{(conical wind),}" (4.4.2 Model prediction for HRLs)
   - assumption: Hydrogen only, constant ionization fraction, isothermal, negligible bulk motions  
  > "We assume that the ionized gas consists only of hydrogen, with a constant ionization fraction." (4.4.1 Collimated ionized jet model)
   - fitting: Parameters chosen heuristically to match flux and shape; not formal fit  
  > "The selection of particular parameters is heuristic and starts with what is considered the simplest choice." (4.4.1 Collimated ionized jet model)
   - validation: Compared predicted line profiles with data; LTE justified by densities vs critical density  
  > "We find that the predicted flux level and shape of the lines are consistent with the data" (4.4.2 Model prediction for HRLs)
5. **Excitation temperatures of sulfur species**: Boltzmann diagram with optically thin single excitation temperature models, two-component fit for SO2 and 34SO; opacity from 32SO/34SO ratios  
  > "the addition of two independent SET models can reproduce well the emission of SO$_2$ and $^{34}$SO." (4.5.2 Excitation temperatures)
   - parameter: line fluxes within 5"x5" box, V -30 to 0 km/s; uncertainty 15 mJy km/s  
  > "with typical uncertainties of 15 mJy km s$^{-1}$" (4.5.2 Excitation temperatures)
   - assumption: d=1.7 kpc; [32S/34S]=22.5; rate coefficient 1e-11 cm3/s for high-energy SO2  
  > "we assume them equal to $10^{-11}$ cm$^{3}$ s$^{-1}$" (4.5.2 Excitation temperatures)
   - fitting: _not stated_
   - validation: SO lines not used in fit; opacity-corrected SO consistent with SET model  
  > "We emphasize that the SO lines were not used to derive the SET model (dashed lines)." (4.5.2 Excitation temperatures)
6. **Dynamical mass of rotating core**: PV diagram of SO2 8(3,5)-9(2,8) perpendicular to jet; 50% contour size and velocity breadth in simplified Franco-Hernandez formula  
  > "From the 50% contour of the PV diagram shown in Figure [\[fig-pv\]](#fig-pv), we estimate $\Delta\Theta=2.5\ensuremath{''}$ and $\Delta V=8~\mbox{km~s$^{-1}$}$." (4.5.3 Dynamics of the molecular emission)
   - parameter: theta_b=1.7", d=1.7 kpc, i=45 deg  
  > "Using a distance of 1.7 kpc, $\theta_b= 1.7\ensuremath{''}$, and an inclination of 45$^\circ$" (4.5.3 Dynamics of the molecular emission)
   - assumption: Centrifugal support against central mass  
  > "we assume that the disklike structure is centrifugally supported against the gravity of a central mass" (4.5.3 Dynamics of the molecular emission)
   - fitting: _not stated_
   - validation: Same result with SO2 7(3,5)-8(2,6)  
  > "We obtain the same results using instead the SO$_2$ $7_{3,5}\rightarrow 8_{2,6}$ transition." (4.5.3 Dynamics of the molecular emission)

## Software

- **CASA** : Recalibration, clean imaging, uvcontsub, maxfit, imfit  
  > "We recalibrated the data using the Common Astronomy Software Applications (CASA) (cite: Petry2012ASPC)." (2 Observations)
- **ALMA Observing Tool** : Theoretical sensitivity  
  > "theoretical sensitivity calculated using the ALMA Observing Tool" (2 Observations)
- **Splatalogue** : Line frequencies and energies (JPL, CDMS)  
  > "consulted through the Splatalogue[^4] (cite: Remijan2007AAS)" (3.3 Sulfuretted molecules)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Source 10 flux density at 85.4 GHz | 103.8 | 0.90 | mJy | 2 | / 10$^{b}$ / 16 59 41.63                    / $-$40 03 43.6              / 103.8(0.90) / 105.7(1.0) / 118.5(1.1)  / 120.8(1.2)  / 1.01(0.1)   / 0.0        / |
| In-band spectral index of Source 10 | 1.01 | 0.1 | dimensionless | 2 | / 10$^{b}$ / 16 59 41.63                    / $-$40 03 43.6              / 103.8(0.90) / 105.7(1.0) / 118.5(1.1)  / 120.8(1.2)  / 1.01(0.1)   / 0.0        / |
| 1-100 GHz spectral index of jet | 0.92 | 0.01 | dimensionless | 2 | power law in frequency with an spectral index of $0.92\pm0.01$ over the entire frequency range |
| Dust flux of Source 10 at 92 GHz | ~11 | not stated | mJy | 2 | we find that the flux attributable to dust is $\sim11$ mJy at 92 GHz, that is, $\sim$10% of the total flux |
| Voigt Lorentzian HWHM H40alpha | 18.6 | 1.0 | km/s | 3 | / H40$\alpha$ / $41.4\pm0.8$ / $-14.8\pm0.5$ / $18.6\pm1.0$  /     $9.7\pm0.5$     / |
| Electron density from H40alpha | 9.7e7 | 0.5e7 | cm^-3 | 3 | / H40$\alpha$ / $41.4\pm0.8$ / $-14.8\pm0.5$ / $18.6\pm1.0$  /     $9.7\pm0.5$     / |
| Characteristic electron density | 5e7 | not stated | cm^-3 | 3 | We find a characteristic value for the electron density of $5\times10^7$ cm$^{-3}$. |
| Best-fit gas temperature (free) | 2000 | +6000/-1000 | K | 3 | Our best-fit model indicates that this temperature is $T=2000^{+6000}_{-1000}$ K. |
| Warm and hot SET temperatures | 140 and 35 | +60/-20 and +25/-20 | K | 5 | with temperatures of $140^{+60}_{-20}$ and $35^{+25}_{-20}$ K, respectively |
| Dynamical mass | 56 | not stated | Msun | 6 | we derive a dynamical mass of $56\mbox{$\,M_{\ensuremath{\odot}}$}$. |
| Size of rotating core | 3000 | not stated | AU | 6 | is $3000$ AU |

## Qualitative findings

- HRL profiles are Voigt with Lorentzian wings, signature of Stark broadening  
  > "The HRLs exhibit Voigt profiles, a strong signature of Stark broadening." (abstract)
- SO, 34SO, SO2 low-energy lines show a velocity gradient perpendicular to the jet; OCS and CS do not  
  > "The molecular core exhibits a velocity gradient perpendicular to the jet-axis, which we interpret as evidence of rotation." (abstract)

## Claim tuples

- H: Can a slow ionized wind in LTE explain the continuum and HRLs without high-velocity gas? | E: Modeled the 1-100 GHz continuum and the three HRLs with an isothermal conical wind model | R: Predicted line fluxes and shapes consistent with data with Ne0 ~2e7 cm-3 at 100 AU | F: No high-velocity ionized component needed | **supported**
- H: Do HRL wings arise from Stark broadening? | E: Voigt fits to H40a, H42a, H50b | R: Lorentzian HWHM 18-20 km/s; Ne ~5e7 cm-3 | F: Wings imply pressure broadening | **supported**
- H: Do sulfur oxides trace a rotating disklike core? | E: Moment maps and PV diagram of SO, SO2 | R: Velocity gradient perpendicular to jet; dynamical mass 56 Msun in ~3000 AU | F: Rotating compact core aligned with jet; likely multiple companions | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: HRLs probe velocity of ionized gas directly, which was previously assumed from lobe proper motions  
  > "The dominant assumption in the literature has been that the velocity of the ionized gas within the jet is similar to that of the lobes." (1 Introduction)
- Alternative: High-velocity outflowing gas producing the wings was disfavored because a Lorentz-like symmetric shape would be fortuitous and no red/blue peak shift >0.2" was found  
  > "It would be fortuitous, however, if the ionized wings produced by entraining ambient gas had a Lorentz-like and a symmetric shape." (4.6 Gentle photo-ionized wind)
- How they decided it was enough: _not stated_
- Limitation (authors): Model parameters not tightly constrained; selection heuristic  
  > "The most important caveat associated with the model is that the data constraints on the parameters are not tight." (4.4.1 Collimated ionized jet model)
- Limitation (authors): Spectral resolution gives only two samples per FWHM so line profile modeling not attempted  
  > "This sampling is too scarce to attempt a detailed modeling of the line profiles." (3.3 Sulfuretted molecules)
- Caveat (inferred, ours): Dynamical mass from 2.5" source size with 1.7" beam is very uncertain; assumes 45 deg inclination from IR
- Caveat (inferred, ours): Model parameter degeneracy; Voigt width ratio of alpha/beta inconsistent with single density
- Caveat (inferred, ours): Distance uncertain (1.7 vs 2.4 kpc)
- Caveat (inferred, ours): Fitting uncertainties not from MCMC, no priors

## Reproducibility

- Data public (paper): Reduced datasets, continuum and cubes on Dataverse  
  > "Fully reduced datasets, continuum, and spectral cubes are publicly available through the Dataverse.[^3]" (2 Observations)
- Products in archive: _not stated_
- Missing: Cm-wavelength flux densities for 1-100 GHz SED
- Missing: Clean parameters and line-free channels
- Missing: Exact CASA version
- Data volume (inferred): ~10-50 GB raw (Cycle 0, 5 SBs); small if using released cubes
- Score (inferred): 3/5, Public data and detailed equations, but imaging details and model fitting are partly heuristic and some inputs come from earlier work.
- Rediscovery candidate: yes, Public Cycle 0 data and released products; main results (Voigt widths, densities, dynamical mass) are numeric with described recipe.

## Links

- Method: (cite: Reynolds1986ApJ) (Jet model parameterization)
- Method: (cite: Gordon2002ASSL) (HRL formulae and Gaussian width relation)
- Method: (cite: Franco-Hernandez2009ApJ) (Dynamical mass equation)
- Companion: (cite: Guzman2010ApJ) (Earlier cm continuum jet and lobes of G345.49+1.47)
- Companion: (cite: Guzman2011ApJ) (Molecular outflow and infall in the region)

## Checks

```json
{
 "quotes": 85,
 "quotes_ok": 85,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 61,
  "rate": 0.709
 },
 "evidence_ok": true
}
```

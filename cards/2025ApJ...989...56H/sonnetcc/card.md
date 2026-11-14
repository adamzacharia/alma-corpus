# ALMASOP. A Rotating Feature Rich in Complex Organic Molecules in a Protostellar Core

`2025ApJ...989...56H` | The Astrophysical Journal 2025 | first author: Hsu, Shih-Ying | arXiv: 2506.15140 | DOI: 10.3847/1538-4357/ade7fc

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: Do complex organic molecules in the protostellar core G192.12-11.10 trace a rotating feature (ring or inner disk), and what heating and origin explain it  
  > "We report the discovery of a rotating feature enriched in COMs, including CH$_3$OH, CH$_3$CHO, and NH$_2$CHO, in the protostellar core G192.12-11.10." (abstract)
- Target **G192.12-11.10**: coordinates 05h32m19s +12d49m40s  
  > "G192.12-11.10 (05$^\mathrm{h}$32$^\mathrm{m}$19$^\mathrm{s}$ +12$\ensuremath{^\circ}$49$\hbox{$^\prime$}$40$\hbox{$^{\prime\prime}$}$)" (1 Introduction); "Given a distance of 445 pc (cite: 2011Lombardi_2MASS_extinction_IV)" (3.2 Kinematics); z/distance 445 pc  
  > "G192.12-11.10 (05$^\mathrm{h}$32$^\mathrm{m}$19$^\mathrm{s}$ +12$\ensuremath{^\circ}$49$\hbox{$^\prime$}$40$\hbox{$^{\prime\prime}$}$)" (1 Introduction); "Given a distance of 445 pc (cite: 2011Lombardi_2MASS_extinction_IV)" (3.2 Kinematics); distance from Lombardi et al. 2011 (cite: 2011Lombardi_2MASS_extinction_IV), lambda-Orionis cloud  
  > "G192.12-11.10 (05$^\mathrm{h}$32$^\mathrm{m}$19$^\mathrm{s}$ +12$\ensuremath{^\circ}$49$\hbox{$^\prime$}$40$\hbox{$^{\prime\prime}$}$)" (1 Introduction); "Given a distance of 445 pc (cite: 2011Lombardi_2MASS_extinction_IV)" (3.2 Kinematics)

## Data provenance

- ALMA projects: 2018.1.00302.S
- bands: Band 6 (1.3 mm or 230 GHz)  
  > "in Band 6 (1.3 mm or 230 GHz) with the combination of both 12-m array (configurations C43–5 and C43–2) and 7-m array" (2 Observations)
- frequencies and spectral setup: four spectral windows centered at 216.6, 218.9, 231.0, 233.0 GHz; 1.129 MHz resolution (1.4 km/s at 230 GHz)  
  > "The four spectral windows centered at 216.6, 218.9, 231.0, and 233.0 GHz have a uniform bandwidth of 1,875 MHz with a spectral resolution of 1.129 MHz" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: 12-m array and 7-m array (ACA)  
  > "with the combination of both 12-m array (configurations C43–5 and C43–2) and 7-m array (also known as the Atacama Compact Array, ACA, or Morita Array)" (2 Observations)
- configurations: 12-m C43-5 and C43-2  
  > "12-m array (configurations C43–5 and C43–2)" (2 Observations)
- baselines: 6 to 965 klambda  
  > "The projected baselines ranged from 6 to 965 k$\lambda$" (2 Observations)
- angular resolution: ~0.42 arcsec  
  > "The resulting angular resolution was $\sim$ 0$.\!\!^{\prime\prime}$42" (2 Observations)
- max recoverable scale: approximately 26 arcsec  
  > "the resulting maximum recoverable scale was approximately 26$^{\prime\prime}$" (2 Observations)
- sensitivity: ~0.43 mJy/beam (0.10 K) full-band continuum; ~3.5 mJy/beam (0.84 K) per channel  
  > "The sensitivities of the image reach $\sim$0.43 mJy beam$^{-1}$ (0.10 K) and $\sim$3.5 mJy beam$^{-1}$ (0.84 K) for the full–band continuum and each channel, respectively." (2 Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Cycle 6 program 2018.1.00302.S, PI Tie Liu (ALMASOP)  
  > "the ALMA Cycle 6 program #2018.1.00302.S, (PI: Tie Liu)" (2 Observations)
- Line: CO J=2-1 (230538 MHz)
- Line: C18O J=2-1 (219560 MHz)
- Line: CH3OH 5(1,4)-4(2,4) (targeted for PV); several other transitions stacked (not stated)
- Line: CH3CHO, HNCO, NH2CHO, H2CO, DCN, H2S, OCS multiple transitions listed in the molecular table (not stated)
- Other facility **WISE, AKARI, JCMT SCUBA**: Photometry from 3.4 to 850 micron for SED fitting, taken from Dutta et al. 2020  
  > "The covered wavelength ranges from 3.4 $\mu$m to 850 $\mu$m." (4.3 Spectral Energy Distribution (SED) Fitting)
- External data: SED photometric data points (WISE, AKARI, SCUBA)  
  > "with the photometric datapoints collected from (cite: 2020Dutta_ALMASOP)" (4.3 Spectral Energy Distribution (SED) Fitting) [from (cite: 2020Dutta_ALMASOP)]
- External data: Distance 445 pc  
  > "Given a distance of 445 pc (cite: 2011Lombardi_2MASS_extinction_IV)" (3.2 Kinematics) [from (cite: 2011Lombardi_2MASS_extinction_IV)]
- External data: CH3OH relative abundance X = 1e-6 in image synthesis  
  > "a relative abundance $X$ of $10^{-6}$ (cite: 2015Boogert_ice_review)" (4.4 Image Synthesis) [from (cite: 2015Boogert_ice_review)]
- External data: Bolometric temperature Tbol = 44 +/- 15 K  
  > "calculated by (cite: 2020Dutta_ALMASOP)" (5.2 Comparisons with the COM-rich Disks and Implications) [from (cite: 2020Dutta_ALMASOP)]
- Simulation/model as data: HOCHUNK YSO model grid used to compute SEDs and temperature maps; SPARX LTE synthetic cubes  
  > "The tool used for calculating the SEDs of the YSO model grid is" (4.3 Spectral Energy Distribution (SED) Fitting); "We adopted the temperature maps exported by" (4.4 Image Synthesis)

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

- task: tclean in CASA  
  > "in CASA (cite: casa:2022) with a robust value of 0.5." (2 Observations)
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "with a robust value of 0.5." (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12-m and 7-m data combined  
  > "with the combination of both 12-m array (configurations C43–5 and C43–2) and 7-m array" (2 Observations)
- smoothing: _not stated_
- final beam: ~0.42 arcsec  
  > "The resulting angular resolution was $\sim$ 0$.\!\!^{\prime\prime}$42" (2 Observations)
- final rms: ~0.43 mJy/beam continuum; ~3.5 mJy/beam per channel  
  > "for the full–band continuum and each channel, respectively." (2 Observations)

### Inherited from earlier work

- ALMASOP observational/survey details  
  > "For more details on the ALMASOP project, please refer to (cite: 2020Dutta_ALMASOP)." (2 Observations) [from (cite: 2020Dutta_ALMASOP)]
- SED scaling factor s from 0.90 to 1.10  
  > "we additionally incorporated a scaling factor ($s$) ranging from 0.90 to 1.10 from (cite: 2016Furlan_HOPS)" (4.3 Spectral Energy Distribution (SED) Fitting) [from (cite: 2016Furlan_HOPS)]
- chi-squared goodness-of-fit method for SED  
  > "we adopted the method from (cite: 2007Robitaille_sedfitter)" (4.3 Spectral Energy Distribution (SED) Fitting) [from (cite: 2007Robitaille_sedfitter)]
- Dust grain models for disk, outflow and envelope  
  > "and “r400_ice095” (cite: 2003Whitney_HOCHUNK_II) for the envelope, following (cite: 2013_Whitney_HOCHUNK)." (4.3 Spectral Energy Distribution (SED) Fitting) [from (cite: 2013_Whitney_HOCHUNK); (cite: 2002Wood_dust); (cite: 1994Kim_dust); (cite: 2003Whitney_HOCHUNK_II)]
- Outflow cavity modelled as radially expanding shell driven by a wide-angle wind  
  > "The molecular CO outflow cavity was modeled as a radially expanding shell driven by an underlying wide-angle wind (cite: 2000Lee_jet_wind_model)." (4.1 Outflow Cavity) [from (cite: 2000Lee_jet_wind_model)]
- Ulrich-Cassen-Moosman (UCM) envelope model adopted  
  > "In this study, we adopt the former." (4.2 Envelope-disk System) [from (cite: 1976Ulrich_CMU; 1981Cassen_CMU; 2004Mendoza_UCM)]

### Not stated but needed to reproduce (our reading)

- CASA version and whether the ALMA pipeline or manual calibration was used (only a CASA citation is given)
- Continuum subtraction method and line-free channels
- tclean deconvolver, masks, thresholds, niter, cell and image size, weighting of 12m+7m combination
- Self-calibration and flux calibrator and flux scale uncertainty
- Width and exact position angle of PV cuts and how velocity boundary / characteristic PV points were measured
- Procedure and transitions used for stacking each molecule
- HOCHUNK model grid details not in Table (inclination fixed? fixed parameter files), and SPARX settings (grid, microturbulence, beam convolution)
- How XCLASS was used (it is listed in Software but no use is described)
- Measured photometric extraction aperture for SED fitting is in Dutta et al. 2020, not here
- Fitted-parameter uncertainties for best-fit R_C, M_cen, cavity parameters

## Analysis recipe

1. **Image the ALMA data**: CLEAN imaging with tclean, robust 0.5  
  > "in CASA (cite: casa:2022) with a robust value of 0.5." (2 Observations)
   - software: CASA, tclean
   - parameter: robust = 0.5  
  > "with a robust value of 0.5." (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract moment maps and PV diagrams of CO, C18O, CH3OH and other molecules**: PV diagrams across the outflow axis (major axis of the continuum); stacking multiple transitions per molecule  
  > "To look at the kinematics of the envelope-disk system, we extracted position-velocity (PV) diagrams across the outflow axis" (3.2 Kinematics); "we stacked the flux densities to improve the signal-to-noise ratio." (3.3 Molecular Diagnostics)
   - software: CASA, CARTA
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive ring radius vs stellar mass from the linear CH3OH PV slope**: Keplerian ring, edge-on, disk mass much smaller than stellar mass; M_* = 3.56 Msun (R_ring/100 au)^3  
  > "Assuming that the disk mass is much smaller than the stellar mass and an edge-on geometry" (3.2 Kinematics)
   - parameter: distance 445 pc  
  > "Given a distance of 445 pc (cite: 2011Lombardi_2MASS_extinction_IV)" (3.2 Kinematics)
   - assumption: Edge-on Keplerian ring, disk mass much smaller than stellar mass  
  > "Assuming that the disk mass is much smaller than the stellar mass and an edge-on geometry" (3.2 Kinematics)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit outflow inclination, velocity factor and cavity wall shape from CO**: chi-squared minimisation of selected characteristic CO PV points; cavity wall parameters from maximum summed gradient of the moment-0 map over sampled b_cav and a_cav  
  > "We fit the outflow model parameters by minimizing the $\chi^2$ value at each $\Delta v$ of the selected characteristic points" (4.1 Outflow Cavity); "We computed the sum of the gradient map values along paths defined by a set of cavity walls" (4.1 Outflow Cavity)
   - parameter: b_cav sampled 1.00, 1.25, 1.50, 1.75; a_cav set so R spans 1 to 2 arcsec at z=3 arcsec  
  > "For each value of $b_\mathrm{cav}$, $a_\mathrm{cav}$ was chosen such that the radius $R$ spans from 1$^{\prime\prime}$to 2$^{\prime\prime}$at a height of $z=3\hbox{$^{\prime\prime}$}$" (4.1 Outflow Cavity)
   - assumption: distance 445 pc; system treated as purely edge-on after the fit  
  > "In the following, we ignore this tiny inclination and assume that the system is purely edge-on." (4.1 Outflow Cavity)
   - fitting: chi-squared minimisation (grid)  
  > "We fit the outflow model parameters by minimizing the $\chi^2$ value" (4.1 Outflow Cavity)
   - validation: _not stated_
5. **Fit envelope-disk (UCM) centrifugal radius and central mass from C18O PV**: fit velocity boundaries of C18O PV diagram with UCM envelope plus Keplerian disk, varying R_C and M_cen, minimising chi-squared  
  > "We then fit the envelope model by minimizing the $\chi^2$-value between the modeled and observed velocity boundaries." (4.2 Envelope-disk System)
   - assumption: C18O emission dominated by the extended envelope  
  > "We assumed that the C$^{18}$O emission is dominated by the extended envelope" (4.2 Envelope-disk System)
   - fitting: chi-squared minimisation  
  > "by minimizing the $\chi^2$-value between the modeled and observed velocity boundaries." (4.2 Envelope-disk System)
   - validation: Modelled PV curve compared by eye with the C18O PV diagram  
  > "the modeled PV diagram (magenta curve) is well-matching the shape of the C$^{18}$O PV diagram." (4.2 Envelope-disk System)
6. **SED fitting with HOCHUNK model grid to get stellar and accretion parameters**: HOCHUNK grid over T_star, r_star, mass infall rate, disk mass, disk accretion rate with central mass fixed; best chi-squared in log space with scaling factor s  
  > "To evaluate the goodness of fit, we adopted the method from (cite: 2007Robitaille_sedfitter), calculating the $\chi^2$ value between the observed and modeled photometric data points in logarithmic space." (4.3 Spectral Energy Distribution (SED) Fitting)
   - software: HOCHUNK
   - parameter: scaling factor s 0.90 to 1.10  
  > "we additionally incorporated a scaling factor ($s$) ranging from 0.90 to 1.10" (4.3 Spectral Energy Distribution (SED) Fitting)
   - assumption: Inner radii of disk and envelope set to the dust sublimation radius  
  > "The inner radii of both the disk and envelope were set to the dust sublimation radius" (4.3 Spectral Energy Distribution (SED) Fitting)
   - fitting: grid search with chi-squared ranking (Robitaille et al. 2007 method)  
  > "We then ranked the combinations of YSO models and scaling factor ($s$) based on their $\chi^2$ values" (4.3 Spectral Energy Distribution (SED) Fitting)
   - validation: Best-fit SED overlaid on the observations  
  > "shows the corresponding SED overlaid with the observations." (4.3 Spectral Energy Distribution (SED) Fitting)
7. **Synthesise CH3OH image cubes for ring, shell, ring+shell and inner-disk heating models**: LTE radiative transfer on HOCHUNK temperature maps with added localized heating (100 K) at 60-80 au, or inside 70 au, comparing synthetic PV diagrams with observed  
  > "we introduced a localized heating effect within the disk at radii between 60 and 80 au, raising the temperature for 100 K." (4.4 Image Synthesis)
   - software: SPARX, HOCHUNK
   - parameter: CH3OH relative abundance 1e-6; E_u = 45 K for the 5(1,4)-4(2,4) line  
  > "a relative abundance $X$ of $10^{-6}$ (cite: 2015Boogert_ice_review)" (4.4 Image Synthesis); "has an upper energy level of 45 K." (4.4 Image Synthesis)
   - assumption: LTE; gas-phase CH3OH from thermal desorption above 100 K  
  > "assuming local-thermodynamic-equilibrium (LTE) and a relative abundance $X$ of $10^{-6}$" (4.4 Image Synthesis); "Following the assumption that the gas-phase CH$_3$OH molecules are thermally desorbed, a temperature of 100 K was required to reach this abundance." (4.4 Image Synthesis)
   - fitting: _not stated_
   - validation: Qualitative comparison of simulated and observed PV diagrams  
  > "the “ring” model exhibits a clear velocity gradient, closely matching our observations." (4.4 Image Synthesis)

## Software

- **CASA** : tclean imaging  
  > "in CASA (cite: casa:2022) with a robust value of 0.5." (2 Observations)
- **tclean** : Imaging with robust 0.5  
  > "in CASA (cite: casa:2022) with a robust value of 0.5." (2 Observations)
- **HOCHUNK** : Computing SEDs and temperature profiles of the YSO model grid  
  > "generates the density profile, computes the temperature profile, and produces the SEDs for the YSO models." (4.3 Spectral Energy Distribution (SED) Fitting)
- **SPARX** : Synthetic image cubes assuming LTE  
  > "(Simulation Package for Astronomical Radiative Xfer) to produce synthetic image cubes with the density, velocity, and temperature" (4.4 Image Synthesis)
- **CARTA** : _not stated_
- **XCLASS** : _not stated_
- **Astropy** : _not stated_

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Outflow inclination | 93 | not stated | deg | 4 | The angle of inclination of $93^{\circ}$ suggests that the system is nearly edge-on |
| Outflow velocity factor | 1.7 | not stated | km au^-1 s^-1 | 4 | $\Tilde{v}=1.7$ km au$^{-1}$s$^{-1}$ |
| Cavity wall exponent b_cav and factor a_cav | b_cav = 1.25, a_cav = 0.4 | not stated | dimensionless | 4 | The best-fit values, having the maximum sum, are $b_\mathrm{cav}$$=1.25$ with $a_\mathrm{cav}$$=0.4$ |
| Centrifugal radius R_C | 145 | not stated | au | 5 | The best-fit parameters obtained are $R_C=145~\mathrm{au}$ and $M_\mathrm{cen}=1.50~M_\odot$. |
| Central mass M_cen | 1.50 | not stated | Msun | 5 | The best-fit parameters obtained are $R_C=145~\mathrm{au}$ and $M_\mathrm{cen}=1.50~M_\odot$. |
| Stellar mass M_* from SED fit | 1.30 | not stated | Msun | 6 | The derived stellar mass is $M_\mathrm{cen} - M_\mathrm{disk} = 1.30 M_\odot$ |
| Disk mass M_disk | 0.20 | not stated | Msun | 6 | Despite the disk mass (0.20 $M_\odot$) is not much smaller than the stellar mass (1.30 $M_\odot$) |
| Best-fit stellar temperature and radius | T_star = 7000 K, r_star = 2 Rsun | not stated | K; Rsun | 6 | The combination of sampled parameters having minimum $\chi^2$ value is: $T_\mathrm{\star}$$=7000$ K, $r_\mathrm{\star}$$=2$$R_\odot$, |
| Size (radius) of the COM-rich rotating feature | around 71 | less than 5 au | au | 3 | the estimated COM-rich feature size is around 71 au, within the disk size.; the uncertainty to the estimated size is less than 5 au. |

## Qualitative findings

- CH3OH, CH3CHO, HNCO and NH2CHO show linear PV diagrams with similar slopes; H2CO, H2S, OCS and DCN show a different kinematic signature  
  > "These molecules all display linear distributions in the PV diagrams haveing similar slopes." (3.3 Molecular Diagnostics)
- Ring and inner-disk models both reproduce the linear PV pattern; shell and ring+shell do not  
  > "Overall, the “inndisk” model produces results very similar to those of the “ring” model" (4.4 Image Synthesis)

## Claim tuples

- H: CH3OH and other COMs trace a rotating feature distinct from the envelope | E: PV diagrams of C18O and CH3OH and other molecules across the continuum major axis | R: CH3OH PV is linear with a larger maximum velocity than C18O; CH3CHO, HNCO, NH2CHO show similar slopes | F: A COM-rich rotating feature exists and is also enriched in CH3CHO, HNCO and NH2CHO | **supported**
- H: The COM-rich feature lies within the disk | E: Keplerian ring size from PV slope plus stellar mass from SED fitting, compared with centrifugal radius from C18O fit | R: Feature size around 71 au versus modeled disk radius 145 au | F: The COM-rich feature is within or near the disk boundary | **supported**
- H: Thermal desorption by the central protostar alone can explain the CH3OH emission | E: SPARX LTE image synthesis with shell, ring, ring+shell and inner-disk heated regions | R: The shell model gives two-peaked PV unlike observed; ring and inner-disk models (with added 100 K heating) match the linear gradient | F: Additional heating (warm ring or warm inner disk) is required | **partially**
- H: OCS and H2S trace different radii consistent with H2S being an OCS precursor | E: Compare PV diagrams of H2CO-like molecules | R: OCS shows larger velocity at small offsets than H2S | F: OCS resides closer to the protostar than H2S, tentatively | **partially**

## Reasoning

- Why this data: The core was previously identified as a source of warm COM emission in ALMASOP  
  > "This protostellar core was previously identified as a source of warm COM emission in the ALMA Survey of Orion PGCCs (ALMASOP) project" (1 Introduction)
- Why this method: Gas-phase CH3OH needs about 100 K but the HOCHUNK structure lacked a warm region near 70 au due to disk shadowing, so localized heating was added  
  > "the imported physical structure did not include a sufficiently warm feature at radius $\sim70$ au due to the disk shadowing effect" (4.4 Image Synthesis)
- Alternative: Three CH3OH spatial models (ring, shell, ring+shell) and an inner-disk heating variant were tested; shell and ring+shell disagreed with observations  
  > "We tested three spatial distribution models, where CH$_3$OH was assumed to reside either exclusively in the warm ring" (4.4 Image Synthesis)
- Alternative: Simplified 2D envelope model (Sakai et al. 2014) was not adopted; UCM model used instead  
  > "In this study, we adopt the former." (4.2 Envelope-disk System)
- How they decided it was enough: _not stated_
- Limitation (authors): Limited spatial and spectral resolution prevents detailed examination of variations among molecules  
  > "However, the limited spatial and spectral resolution prevents a more detailed examination of potential variations." (5.3 Molecular Diagnostics and Implications)
- Limitation (authors): Remaining discrepancies between models and observations need a more refined disk model and chemical simulation  
  > "A more refined disk model and chemical simulation will be necessary to further address these discrepancies." (4.4 Image Synthesis)
- Caveat (inferred, ours): Disk size and stellar mass rest on assuming C18O perfectly traces the envelope; the authors note the ring radius (~70 au) is about half the modeled disk radius
- Caveat (inferred, ours): No uncertainties given on most best-fit parameters; model fits are coarse grids
- Caveat (inferred, ours): Image synthesis is qualitative (visual PV comparison), no quantitative fit statistic
- Caveat (inferred, ours): COM-rich feature is only marginally resolved at 0.42 arcsec (~190 au at 445 pc); ring vs unresolved disk is degenerate
- Caveat (inferred, ours): Added 100 K heating at 60-80 au and abundance 1e-6 are ad hoc assumptions

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Calibration/pipeline details and CASA version
- Missing: Continuum subtraction and imaging parameters beyond robust 0.5
- Missing: PV extraction details and characteristic-point selection
- Missing: SPARX and HOCHUNK input settings and the model grid files
- Missing: Stacking procedure for multiple transitions
- Data volume (inferred): Not stated; Cycle 6 12-m C43-5/C43-2 plus ACA Band 6 for one target, likely tens of GB of raw data
- Score (inferred): 3/5, Project code and key numeric fit results are given and the modeling equations are explicit, but calibration, imaging and PV-extraction details are missing and the SPARX/HOCHUNK set-ups are not fully specified
- Rediscovery candidate: no, Public status of the data is not stated in the paper and imaging, PV extraction and radiative-transfer settings are incomplete; main model comparison is qualitative

## Links

- Method: Dutta et al. 2020 (cite: 2020Dutta_ALMASOP) (ALMASOP survey description and SED photometry)
- Method: Lee et al. 2000 (cite: 2000Lee_jet_wind_model) (Wide-angle wind model for the CO outflow cavity)
- Method: Whitney et al. 2003 (cite: 2003Whitney_HOCHUNK_I; 2003Whitney_HOCHUNK_II) (HOCHUNK radiative transfer code)
- Method: Robitaille et al. 2007 (cite: 2007Robitaille_sedfitter) (SED fitting chi-squared method)
- Companion: Hsu et al. 2020, 2022 (cite: 2020Hsu_ALMASOP; 2022Hsu_ALMASOP) (Earlier ALMASOP COM detection in this core)
- Companion: Lee et al. 2022 (cite: 2022Lee_HH212_stratification) (HH 212 comparison source)
- Related: ALMASOP (ALMA Survey of Orion PGCCs)

## Checks

```json
{
 "quotes": 93,
 "quotes_ok": 93,
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
  "facts": 99,
  "stated": 65,
  "rate": 0.657
 },
 "evidence_ok": true
}
```

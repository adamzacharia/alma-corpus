# An Extremely Young Protostellar Core, MMS 1/OMC-3: Episodic Mass Ejection History Traced by the Micro SiO Jet

`2024ApJ...964...48T` | The Astrophysical Journal 2024 | first author: Takahashi, Satoko | arXiv: 2401.13204 | DOI: 10.3847/1538-4357/ad2268

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Does the OMC-3 source MMS 1 host a protostar, and what do its compact CO outflow and SiO jet reveal about its age and episodic mass ejection history?  
  > "Our detection of the molecular outflow and jet is the first direct evidence that MMS 1 already hosts a protostar." (abstract)
- Target **MMS 1 (OMC-3)**: coordinates RA 05h35m18.03s, Dec -05d00m17.770s (J2000, phase center)  
  > "The phase center was set toward the location of the millimeter source, MMS 1: R.A. (J2000) = 5$^h$35$^m$18$^s$.03, decl. (J2000) =${-}$05$^{\circ}$00$'$17$\ensuremath{''}$.770." (2 OBSERVATIONS AND DATA REDUCTION); "(OMC-3 region; $d$=393 pc by (cite: Tobin2020)[^1])" (1 Introduction); z/distance 393 pc  
  > "The phase center was set toward the location of the millimeter source, MMS 1: R.A. (J2000) = 5$^h$35$^m$18$^s$.03, decl. (J2000) =${-}$05$^{\circ}$00$'$17$\ensuremath{''}$.770." (2 OBSERVATIONS AND DATA REDUCTION); "(OMC-3 region; $d$=393 pc by (cite: Tobin2020)[^1])" (1 Introduction); distance from Tobin et al. 2020 (Gaia DR2)  
  > "The phase center was set toward the location of the millimeter source, MMS 1: R.A. (J2000) = 5$^h$35$^m$18$^s$.03, decl. (J2000) =${-}$05$^{\circ}$00$'$17$\ensuremath{''}$.770." (2 OBSERVATIONS AND DATA REDUCTION); "(OMC-3 region; $d$=393 pc by (cite: Tobin2020)[^1])" (1 Introduction)

## Data provenance

- ALMA projects: 2015.1.00341.S
- bands: Band 6 (1.3 mm)  
  > "using the 1.3 mm band (Band 6)" (2 OBSERVATIONS AND DATA REDUCTION)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 454 MHz effective (line-free channels)  
  > "Line free channels corresponding to the effective band width of 454 MHz are allocated for imaging the continuum data." (2 OBSERVATIONS AND DATA REDUCTION)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 8.5–239 kλ (low res); 8.9–2416 kλ (high res)  
  > "Projected baseline ranges (k$\lambda$) | 8.9 – 2416 | 8.5 – 239" (Table 1)
- angular resolution: CO 0.18x0.15 arcsec, SiO 0.21x0.17 arcsec, continuum 0.19x0.16 arcsec (high res)  
  > "Synthesized beam size of the SiO (5–4) images (arcsec) | 0.21$\times$0.17 (p.a.=-27deg.) | 1.6$\times$0.9 (p.a.=-78deg.)" (Table 1)
- max recoverable scale: ~2.0 arcsec (high res); ~9.8 arcsec (low res)  
  > "Maximum recoverable size (arcsec) | $\sim$2.0 | $\sim$9.8" (Table 1)
- sensitivity: continuum rms 0.24 mJy/beam (high res); CO 2.7, SiO 1.8 mJy/beam km/s in 5 km/s channels  
  > "RMS noise level of the continuum images (mJy beam$^{-1}$) | 0.24 | 0.55" (Table 1)
- time on source: 16 min (high res, ~40 antennas); 4 min (low res, 48 antennas)  
  > "Total on-source time is about 16 minutes with $\sim$40 antennas (high-angular resolution) and 4 minutes with 48 antennas (low-angular resolution)." (2 OBSERVATIONS AND DATA REDUCTION)
- observing dates: 2016-01-29 (low res); 2016-09-18 and 19 (high res)  
  > "The ALMA observations were made in Cycle 3, 2016 January 29 (low angular resolution) and 2016 September 18 and 19 (high angular resolution)" (2 OBSERVATIONS AND DATA REDUCTION)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (230.535 GHz)
- Line: SiO J=5-4 (217.102 GHz (listed LSB setup))
- Other facility **JCMT/SCUBA-2 (JCMT Transient Survey)**: 850 um light curve over ~8 years  
  > "The observations cover late 2015 through mid-2023, almost eight years of roughly monthly cadence." (4.3 Episodic Mass Ejection and Accretion)
- External data: Inclination of 45 deg from dust-disk axis ratio, used for dynamical timescales  
  > "Here, we adopt $i=45^{\circ}$, estimated from the axis ratio of the dust disk by (cite: Liu2023)." (3.4.1 Outflow and Jet Dynamical Timescales) [from (cite: Liu2023)]
- External data: Dust opacity 0.011 cm2/g at 1.3 mm  
  > "${\kappa}_{\rm{1.3mm}}$ = 0.011 cm$^2$ g$^{-1}$ from the dust coagulation model of the MRN (cite: mathis1977) with thin ice mantles at a number density of 10$^{8}$ cm$^{-3}$ (cite: ossenkopf1994)" (3.1 The 1.3 mm Continuum Emission) [from (cite: ossenkopf1994)]
- External data: Distance 393 pc to OMC-3  
  > "d$ = 393 pc (distance to the OMC-3 region measured from the $Gaia$ DR2 data; (cite: Tobin2020; McBride2019; Gaia2018))" (3.1 The 1.3 mm Continuum Emission) [from (cite: Tobin2020)]
- External data: JCMT 850 um light curve of MMS 1 and flux calibration uncertainty <2%  
  > "For bright sources, such as MMS 1, the relative flux calibration uncertainty between epochs is better than 2% (cite: Mairs2017)." (4.3 Episodic Mass Ejection and Accretion) [from (cite: Herczeg2017); (cite: Mairs2017)]
- Simulation/model as data: Core-collapse resistive MHD simulation of Machida & Basu 2019 (1.7 Msun core, B0=4.5e-5 G, Omega0=1.1e-13 rad/s), snapshots at 200.21, 200.58, 201.69 yr after protostar formation, compared to PV diagram  
  > "The data in Figure [8](#fig:f8) were taken from the core collapse simulation performed by (cite: machida2019)." (4.1 Comparison between Observation and Simulation)

## Processing

### Calibration

- pipeline or manual: standard ALMA data reduction  
  > "version 4.6.0 and version 4.7.0 were used as the standard ALMA data reduction for the low- and high-angular resolution data sets, respectively." (2 OBSERVATIONS AND DATA REDUCTION)
- casa version: CASA 4.6.0 (low res), 4.7.0 (high res)  
  > "version 4.6.0 and version 4.7.0 were used as the standard ALMA data reduction for the low- and high-angular resolution data sets, respectively." (2 OBSERVATIONS AND DATA REDUCTION)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0510+1800, J0522-3627 (high res); J0522-3627 (low res)  
  > "Flux calibrators | J0510+1800,J0522-3627 | J0522-3627" (Table 1)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean  
  > "After calibration, the CLEANed images were made using the CASA task “`tclean`”." (2 OBSERVATIONS AND DATA REDUCTION)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "The Briggs weighting with robust parameter of 0.5 were used for the final images." (2 OBSERVATIONS AND DATA REDUCTION)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: cubes with 5.0 km/s velocity width  
  > "The velocity width of 5.0 km s$^{-1}$ was used in order to produce the CO and SiO image cubes both for high- and low-angular resolution data sets." (2 OBSERVATIONS AND DATA REDUCTION)
- final beam: CO 0.18x0.15 (p.a.=-18), SiO 0.21x0.17 (p.a.=-27), continuum 0.19x0.16 (p.a.=-25) arcsec  
  > "Synthesized beam size of the continuum images (arcsec) | 0.19$\times$0.16 (p.a.=-25deg.) | 1.6$\times$0.9 (p.a.=-77deg.)" (Table 1)
- final rms: continuum 0.24 mJy/beam; CO 2.7 and SiO 1.8 mJy/beam km/s (high res)  
  > "RMS noise level of the continuum images (mJy beam$^{-1}$) | 0.24 | 0.55" (Table 1)

### Inherited from earlier work

- Disk inclination of 45 deg adopted from dust-disk axis ratio  
  > "Here, we adopt $i=45^{\circ}$, estimated from the axis ratio of the dust disk by (cite: Liu2023)." (3.4.1 Outflow and Jet Dynamical Timescales) [from (cite: Liu2023)]
- Jet precession parametric 3D spiral model  
  > "as described by(cite: Schutzer2022) and originally based on (cite: Raga1993) and (cite: Masciadri2002)" (3.5 Jet Precession) [from (cite: Schutzer2022)]
- Systemic velocity of 11 km/s from optically thin lines in OMC-3  
  > "The systemic velocity of 11 km s$^{-1}$ is adopted for the system, which is determined from the optically thin molecular lines in the OMC-3 region" (3 RESULTS) [from (cite: takahashi2009; matsushita2019; morii2021)]

### Not stated but needed to reproduce (our reading)

- Exact line-free channel ranges for continuum and any continuum subtraction method
- Image size, cell size, masking, clean threshold and deconvolver for tclean
- Self-calibration usage, flux scale uncertainty
- Method for deriving PV-diagram cuts, moment-map thresholds and knot positions/velocities
- Bandpass/flux standard model and flux density values for calibrators
- JCMT light-curve reduction details

## Analysis recipe

1. **Image continuum and line cubes**: tclean with Briggs weighting on high- and low-resolution data; compare line flux between them to check missing flux  
  > "Thus, there is no significant missing flux in the high angular resolution data set." (3.2 CO and SiO Line Profiles)
   - software: CASA, tclean
   - parameter: robust 0.5; 5 km/s channels  
  > "The Briggs weighting with robust parameter of 0.5 were used for the final images." (2 OBSERVATIONS AND DATA REDUCTION)
   - fitting: _not stated_
   - validation: Missing-flux comparison between low- and high-resolution CO and SiO images  
  > "The comparisons show that the fluxes obtained from the two data sets are almost the same." (3.2 CO and SiO Line Profiles)
2. **Fit continuum structure and estimate disk mass**: Two-component 2D Gaussian fit to high-resolution continuum; mass from optically thin dust emission equation  
  > "we performed two-component two dimensional (2D) Gaussian fitting on the high-angular resolution image." (3.1 The 1.3 mm Continuum Emission)
   - parameter: Td = 30–100 K; kappa(1.3mm)=0.011 cm2/g; d=393 pc  
  > "$T_{\rm{dust}}$ = 30 K – 100 K (e.g., (cite: nomura2005); (cite: tomida2017))" (3.1 The 1.3 mm Continuum Emission)
   - assumption: Gas-to-dust mass ratio of 100; thermal dust emission dominates; compact component traces disk with inclination from axis ratio  
  > "Here, a gas-to-dust mass ratio of 100 is assumed." (3.1 The 1.3 mm Continuum Emission)
   - fitting: _not stated_
   - validation: Residual <5.6% of peak; compared with Liu et al. 2023 fit  
  > "The residual level of the fitting result is less than 5.6% with respect to the observed peak flux" (3.1 The 1.3 mm Continuum Emission)
3. **Measure outflow and jet morphology, PV diagrams, velocities**: Moment maps and PV diagram cut along outflow axis p.a. = -137 deg from CO and SiO cubes  
  > "Figure [5](#fig:f5) presents the position-velocity diagram (PV-diagram) obtained from the CO (2–1) and SiO (5–4) data cubes cut along the outflow axis (p.a. = -137$^{\circ}$)." (3.3 Outflow and Jet)
   - fitting: _not stated_
   - validation: _not stated_
4. **Estimate dynamical timescales**: t_dyn = (l_obs/v_obs)(cos i / sin i) for jet, outflow and knots  
  > "t_{\rm{dyn}} = \left(\frac{l_{\rm obs}}{v_{\rm obs}}\right)\left(\frac{\cos i}{\sin i}\right)" (3.4.1 Outflow and Jet Dynamical Timescales)
   - parameter: i = 45 deg  
  > "Here, we adopt $i=45^{\circ}$, estimated from the axis ratio of the dust disk by (cite: Liu2023)." (3.4.1 Outflow and Jet Dynamical Timescales)
   - assumption: Outflow extends to the bow-shock locations  
  > "we assume that the outflow emission is extended up to the locations of the bow-shocks" (3.4.1 Outflow and Jet Dynamical Timescales)
   - fitting: _not stated_
   - validation: Using i=53 deg changes timescales by a factor ~1.4  
  > "This introduces the timescale estimations of a factor of $\sim$1.4 longer than the current estimations." (3.4.1 Outflow and Jet Dynamical Timescales)
5. **Fit jet precession**: 3D spiral parametric model fit by eye to northern and southern jets separately  
  > "the other parameters of the jet position angle $\lambda$, $\beta$, and the phase angle $\phi$ were fitted simultaneously by eye." (3.5 Jet Precession)
   - assumption: Inclination 45 deg  
  > "We adopted the inclination angle of the jet as 45$^{\circ}$" (3.5 Jet Precession)
   - fitting: By eye, no sampler  
  > "were fitted simultaneously by eye." (3.5 Jet Precession)
   - validation: _not stated_
6. **Compare PV diagram with MHD simulation and JCMT light curve**: Qualitative comparison with Machida & Basu 2019 PV diagrams; inspect 850 um light curve for bursts  
  > "We thus can not quantitatively compare the observation with the simulation." (4.1 Comparison between Observation and Simulation)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.6.0 and 4.7.0: Calibration and tclean imaging  
  > "version 4.6.0 and version 4.7.0 were used as the standard ALMA data reduction for the low- and high-angular resolution data sets, respectively." (2 OBSERVATIONS AND DATA REDUCTION)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Compact continuum component flux density | 12 | 0.51 | mJy | 2 | 9.4$\pm$0.25 / 12 $\pm$ 0.51 |
| Extended continuum component flux density | 96 | 6.2 | mJy | 2 | 1.1$\pm$0.073 / 96 $\pm$ 6.2 |
| Compact component mass | 0.0051–0.020 | not stated | Msun | 2 | $M_{\rm{H_2(comp.)}}{\sim}$0.0051–0.020 $M_{\odot}$ |
| Disk inclination from compact axis ratio | ~53 | not stated | deg | 2 | an inclination angle of the disk ($i$) is estimated to be ${\sim}53^{\circ}$ using the axis ratio |
| Jet dynamical timescale (blue/red) | 66 / 55 | not stated | yr | 4 | the jet dynamical timescale is estimated to be 66 yr (blue-shifted jet) and 55 yr (red-shifted jet), respectively. |
| Outflow dynamical timescale (blue/red) | 350 / 660 | not stated | yr | 4 | the outflow dynamical timescales are estimated to be 350 yr (blue-shifted side) and 660 yr (red-shifted side), respectively. |
| Knot dynamical timescales K1–K4 | 5, 18, 45, 53 | not stated | yr | 4 | which are 5 yr (K1), 18 yr (K2), 45 yr (K3), and 53 yr (K4) |
| Precession parameters (north/south) lambda | 7.8 / 6.8 | not stated | arcsec | 5 | North / 7.8 / 62 / 7.0 / 234 / 174 |
| Precession period (north/south) | 234 / 138 | not stated | yr | 5 | South / 6.8 / 92 / 8.0 / 138 / 180 |
| JCMT 850 um flux decline rate | ~0.5 | not stated | % per year | 6 | There is, however, a distinct $\sim$ 0.5% per year gradual decline in the brightness |

## Qualitative findings

- SiO jet wiggles with an S-shape and contains a chain of knots; PV diagram shows Hubble-like linear velocity increase  
  > "The SiO jet wiggles and displays a chain of knots." (abstract)

## Claim tuples

- H: MMS 1 already hosts a protostar | E: ALMA CO(2-1) and SiO(5-4) imaging at ~0.2 arcsec | R: Compact CO outflow and SiO jet detected | F: MMS 1 is an extremely young Class 0 protostar | **supported**
- H: The jet shows episodic mass ejection | E: Compare SiO PV diagram and knots with core-collapse MHD simulation | R: Multiple spine structures with Hubble-like flow resemble the simulation qualitatively | F: Multiple mass ejection events explain the observed PV structure | **partially**
- H: Recent accretion burst accompanies the ejection | E: Inspect JCMT 850 um light curve for 8 years | R: No dramatic change, weak decline | F: No clear burst within last 8 years | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Binary orbital motion and tidal interaction as origin of wiggle rejected in favour of precession from core rotation–magnetic field misalignment  
  > "Thus, we can exclude the tidal interaction scenario." (3.5 Jet Precession)
- How they decided it was enough: _not stated_
- Limitation (authors): Simulation cannot be quantitatively compared; observations only sensitive to timescales longer than ~5 yr  
  > "our observations are only sensitive to the timescale longer than $\sim$5 years." (4.3 Episodic Mass Ejection and Accretion)
- Caveat (inferred, ours): Jet precession fit is done by eye with no uncertainties
- Caveat (inferred, ours): Inclination uncertain (45 vs 53 deg) shifts timescales by ~1.4
- Caveat (inferred, ours): Simulation comparison is qualitative only
- Caveat (inferred, ours): Dust temperature range 30-100 K gives factor ~4 mass range

## Reproducibility

- Data public (paper): Project 2015.1.00341.S acknowledged; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00341.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Image size/cell/mask/threshold
- Missing: Line-free channels
- Missing: Knot and PV extraction details
- Missing: JCMT light curve data
- Data volume (inferred): ~20-50 GB raw
- Score (inferred): 3/5, Basic imaging parameters given and data archival, but moment/PV extraction and many settings unstated; precession fit by eye.
- Rediscovery candidate: yes, Data from a single ALMA project; numeric results (Gaussian fits, timescales) can be redone with stated recipe.

## Links

- Method: (cite: Schutzer2022) (Jet precession parametric model)
- Companion: (cite: Liu2023) (Polarization continuum analysis of MMS 1 giving disk inclination)
- Related: JCMT Transient Survey
- Related: HOPS

## Checks

```json
{
 "quotes": 70,
 "quotes_ok": 70,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 50,
  "rate": 0.625
 },
 "evidence_ok": true
}
```

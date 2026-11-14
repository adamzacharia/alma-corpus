# ALMA Observations of Orion Source I at 350 and 660 GHz

`2016ApJ...833..219P` | The Astrophysical Journal 2016 | first author: Plambeck, R. L. | arXiv: 1608.00996 | DOI: 10.3847/1538-4357/833/2/219

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: What is the nature of the continuum emission from Orion Source I (hypercompact HII region, H- free-free, or dust), and what is its central mass and disk structure?  
  > "In this paper we present the results of 0.2$''$ resolution ALMA observations of SrcI that were designed to determine the nature of its continuum emission and further constrain its mass." (INTRODUCTION)
- Target **Orion Source I (SrcI)**: coordinates 05h35m14.514s, -05d22m30.56s (pointing center)  
  > "The pointing center was $05^{\rm h}35^{\rm m}14.514s$, $-5\ensuremath{^\circ}22\ensuremath{'}30.56\ensuremath{''}$." (OBSERVATIONS AND DATA REDUCTION); "The Kleinmann-Low Nebula in Orion, at a distance of 415 pc (cite: Menten2007; Kim2008)" (INTRODUCTION); z/distance 415 pc  
  > "The pointing center was $05^{\rm h}35^{\rm m}14.514s$, $-5\ensuremath{^\circ}22\ensuremath{'}30.56\ensuremath{''}$." (OBSERVATIONS AND DATA REDUCTION); "The Kleinmann-Low Nebula in Orion, at a distance of 415 pc (cite: Menten2007; Kim2008)" (INTRODUCTION); distance from Menten2007; Kim2008  
  > "The pointing center was $05^{\rm h}35^{\rm m}14.514s$, $-5\ensuremath{^\circ}22\ensuremath{'}30.56\ensuremath{''}$." (OBSERVATIONS AND DATA REDUCTION); "The Kleinmann-Low Nebula in Orion, at a distance of 415 pc (cite: Menten2007; Kim2008)" (INTRODUCTION)

## Data provenance

- ALMA projects: 2012.1.00123.S
- bands: Band 7 and Band 9 (350 and 660 GHz)  
  > "For Band 7, spectral window 0 was centered at 353.623 GHz, the frequency of the H26$\alpha$ recombination line; for Band 9, spectral window 0 was centered close to 662.404 GHz" (OBSERVATIONS AND DATA REDUCTION)
- frequencies and spectral setup: 4 spectral windows, 3840 x 0.488 MHz channels x 2 pol, Frequency Division Mode; B7 spw 352.7-354.6, 354.5-356.4, 340.6-342.4, 342.4-344.3 GHz; B9 661.3-663.2, 663.2-665.1, 665.9-667.8, 649.3-651.2 GHz  
  > "The correlator was set up in the Frequency Division Mode, with $3840 \times 0.488$ MHz channels $\times$ 2 polarizations in each of 4 spectral windows." (OBSERVATIONS AND DATA REDUCTION)
- continuum bandwidth: _not stated_
- arrays: 31 antennas (Band 7), 28 antennas (Band 9)  
  > "| no. of antennas     | 31                   | 28                   |" (Table 1)
- configurations: _not stated_
- baselines: B7 31-733 m (35-860 kλ); B9 19-630 m (40-1390 kλ)  
  > "| uvrange             | 31–733 m            | 19–630 m             |" (Table 1)
- angular resolution: better than 0.25'' requested; ~0.2''; synthesized beams 0.25x0.18'' (349 GHz), 0.16x0.12'' (661 GHz)  
  > "An angular resolution of better than 0.25$''$ was requested in order to cleanly resolve SrcI from the adjacent Orion hot core." (OBSERVATIONS AND DATA REDUCTION)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: Band 7 24 min; Band 9 15.6 min  
  > "| on-source time      | 24 min               | 15.6 min             |" (Table 1)
- observing dates: 2014-07-26 (Band 7); 2014-07-06 (Band 9)  
  > "| date                | 2014-07-26           | 2014-07-06           |" (Table 1)
- pi or archival as stated: _not stated_
- Line: H26α hydrogen recombination (353.6228 GHz)
- Line: H21α hydrogen recombination (662.4042 GHz)
- Line: 29SiO J=8-7 v=0 (342.981 GHz)
- Line: SiO J=15-14 v=0 (650.956 GHz)
- Other facility **CARMA**: 229 GHz A+B array continuum data (2009 and 2011), combined here  
  > "we combine the A and B array data to match the spatial frequency range of the ALMA data as closely as possible." (2.3 229 GHz CARMA Data)
- External data: 43 GHz VLA source parameters and proper motions of SrcI  
  > "$^{b}$ (cite: Goddi2011)." (Table 2) [from (cite: Goddi2011)]
- External data: Continuum flux densities 4-690 GHz compilation for the SED  
  > "The remaining data are from the compilation in Table 2 in (cite: Plambeck2013), supplemented by recent VLA (cite: Rivilla2015; Forbrich2016) and ALMA (cite: Hirota2015; Hirota2016) results." (5.1 Continuum Spectral Energy Distribution) [from (cite: Plambeck2013; Rivilla2015; Forbrich2016; Hirota2015; Hirota2016)]
- External data: Dust opacities (Ossenkopf & Henning) and extrapolation to 43 GHz  
  > "We follow the procedure used by (cite: Chandler2005) to estimate the mass opacity of dust $\kappa_{\rm 43\,GHz}$" (5.4 Dust?) [from (cite: Chandler2005; Ossenkopf1994)]

## Processing

### Calibration

- pipeline or manual: ALMA-supplied scripts with CASA, then Miriad  
  > "The raw visibility data were calibrated using ALMA-supplied scripts and the CASA software package." (2 OBSERVATIONS AND DATA REDUCTION)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ±10% Band 7, ±15% Band 9, ±15% CARMA 230 GHz  
  > "absolute calibration uncertainties of $\pm~10$% for Band7 and $\pm$ 15% for Band 9, as given by the ALMA Cycle 1 Technical Handbook" (3 CONTINUUM IMAGES)
- self calibration: Two iterations phase-only, CLEAN components >3σ as model, solint 6.05 s; no amplitude self-cal  
  > "Two iterations of phase-only self-calibration were then applied to the data." (2.2 Self-Calibration); "The self-calibration interval was chosen to be 6.05 secs, equal to the integration time." (2.2 Self-Calibration)

### Imaging

- task: Miriad CLEAN and MAXEN; imfit and uvfit for size fits  
  > "The images on the left were deconvolved with `CLEAN`, those on the right with a maximum entropy algorithm (`Miriad` task `MAXEN`)." (3 CONTINUUM IMAGES)
- deconvolver: _not stated_
- weighting robust: Briggs robust=0  
  > "Data were weighted using Briggs `robust=0`." (2.2 Self-Calibration)
- uv taper: continuum: baselines >250 kλ; line images >100 kλ; Band 9 channel maps >300 kλ  
  > "omitting visibility data from projected baselines shorter than 250 k$\lambda$ (corresponding to a fringe spacing of 0.82$''$)" (2.2 Self-Calibration); "using baselines $>100$ k$\lambda$ and `robust=0` weighting." (4 SPECTRAL LINES)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: Identified from scalar-averaged visibility spectrum, then adjusted after inspecting preliminary channel images  
  > "We identified such channels by plotting the *scalar* average of the interferometric visibility data." (2.1 Identifying Line-Free Channels)
- primary beam correction: _not stated_
- array combination: 4 spectral windows combined with multifrequency synthesis  
  > "The channel-averaged visibilities for the 4 separate spectral windows were combined using multifrequency synthesis to avoid bandwidth smearing at the edge of the images." (3 CONTINUUM IMAGES)
- smoothing: Hanning-smoothed to 1.7 km/s  
  > "These spectra have been Hanning-smoothed to an effective velocity resolution of 1.7 $\rm km~s^{-1}$." (4 SPECTRAL LINES)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- CARMA calibration details  
  > "Details of the CARMA calibrations may be found in (cite: Plambeck2013)" (2.3 229 GHz CARMA Data) [from (cite: Plambeck2013)]
- Rotation-curve model similar to that of Hirota et al.  
  > "we simulated these rotation curves using a model similar to the one used by (cite: Hirota2014)." (4.5 Central Mass Estimate) [from (cite: Hirota2014)]
- Dust opacity procedure  
  > "We follow the procedure used by (cite: Chandler2005) to estimate the mass opacity of dust" (5.4 Dust?) [from (cite: Chandler2005)]

### Not stated but needed to reproduce (our reading)

- Exact list of line-contaminated channels per spectral window
- Number of CLEAN iterations, cell size, image size, masks
- CASA version and calibrator names
- Self-cal reference model details beyond 3σ components
- MAXEN noise level values
- Ring model details beyond outer radius, inner radius, linewidth (temperature/density irrelevant, fit procedure)
- Rotation-curve fitting criterion (visual match, no formal fit)

## Analysis recipe

1. **Calibrate and import data**: ALMA scripts in CASA, export to FITS, import to Miriad  
  > "The calibrated CASA measurement sets then were written out in FITS format and imported into `Miriad`" (2 OBSERVATIONS AND DATA REDUCTION)
   - software: CASA, Miriad
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify line-free channels and self-calibrate**: Scalar-averaged visibility spectra; phase-only self-cal on >250 kλ continuum images  
  > "The images were deconvolved with the `CLEAN` algorithm, then self-calibrated using `CLEAN` components stronger than 3$\sigma$ as a source model." (2.2 Self-Calibration)
   - software: Miriad
   - parameter: solint 6.05 s, two iterations  
  > "Two iterations of phase-only self-calibration were then applied to the data." (2.2 Self-Calibration)
   - fitting: _not stated_
   - validation: Compared antenna phase corrections between 4 spws; spw flux densities within 3% of mean  
  > "For both Band 7 and Band 9, the flux density in each of the 4 spectral windows was within 3% of the mean" (2.2 Self-Calibration)
3. **Measure continuum size and flux**: Gaussian (and disk) fits to central 0.8'' of CLEAN and MAXEN images plus uvfit; average of three methods  
  > "Therefore, in Table [\[tab:gfits\]](#tab:gfits) we give the average of the sizes obtained with these 3 methods; uncertainties are estimated from the scatter in the results." (3 CONTINUUM IMAGES)
   - software: Miriad imfit, Miriad uvfit, Miriad MAXEN
   - fitting: Elliptical Gaussian least-squares fits; residual rms compared  
  > "We judged the quality of each fit from the rms noise in this box after subtracting the model image." (3 CONTINUUM IMAGES)
   - validation: Gaussian vs disk model residuals compared  
  > "There was little difference in the residual noise between Gaussian and disk models" (3 CONTINUUM IMAGES)
4. **Search for recombination lines and set upper limit**: Spectra in 0.2''x0.2'' box; compare channels in 5<VLSR<23 km/s with continuum  
  > "all channels within this velocity range have line + continuum flux densities that are $<~1.05~\times$ the mean continuum level." (4.1 Hydrogen Recombination Lines)
   - software: Miriad
   - assumption: Te=8000 K, linewidth 50 km/s, path length 100 AU  
  > "For $\nu=662.4$ GHz, $T_e=8000$ K, and $\Delta \nu_{\rm kHz} = 1.1 \times 10^5$ ($\Delta v=50$ $\rm km~s^{-1}$)" (5.2 An Optically Thick Hypercompact HII Region?)
   - fitting: _not stated_
   - validation: Neighboring SO2 line profiles overlaid to show similar shapes  
  > "The spectra of two neighboring lines, the 16(7,9)-16(6,10) and 14(7,7)-14(6,8) transitions, are overlaid" (4.1 Hydrogen Recombination Lines)
5. **Estimate central mass from rotation curves**: Channel centroids from 2D Gaussian fits projected on midplane, compared with Keplerian ring model  
  > "The model assumes optically thin emission from gas in Keplerian rotation around a central point mass." (4.5 Central Mass Estimate)
   - software: Miriad
   - parameter: outer radius 50 AU, inner radius 20 AU, turbulent linewidth 4 km/s, PA 142 deg  
  > "A turbulent linewidth of 4 $\rm km~s^{-1}$ was assumed." (4.5 Central Mass Estimate)
   - assumption: Edge-on, uniform temperature and density ring  
  > "The gas has uniform temperature and density, and is confined to a ring that is viewed exactly edge-on." (4.5 Central Mass Estimate)
   - fitting: Grid of masses and inner radii compared with data by eye  
  > "We modeled the rotation curves for a range of central masses and inner radii." (4.5 Central Mass Estimate)
   - validation: Consistent with SiO maser mass; inclination <20 deg changes mass <10%  
  > "an estimated central mass of 5-7 $\hbox{M}_\odot$ is consistent with that derived by (cite: Matthews2010) from high resolution SiO maser maps." (4.5 Central Mass Estimate)
6. **SO2 rotational diagram**: Optically thin LTE rotational diagram of 16 SO2 lines using integrated intensity over 5-20 km/s  
  > "A rotational diagram analysis (cite: Blake1987) assumes that the lines are optically thin, that they originate in the same column of gas, and that the rotational energy ladders are in local thermodynamic equilibrium." (4.7 Excitation Temperature Analysis)
   - parameter: Q(500 K)=15611 from CDMS  
  > "we have taken $Q(500~K) = 15611$, the combined partition function for the v=0 and v2=1 vibrational states" (4.7 Excitation Temperature Analysis)
   - assumption: v=0 and v2=1 ladders thermalized at same temperature  
  > "so we will assume that the v=0 and v2=1 rotational ladders are thermalized at the same temperature." (4.7 Excitation Temperature Analysis)
   - fitting: Straight line in ln(Nu/gu) vs Eu; fit not formally described  
  > "A plot of natural log of $N_u/g_u$ against $E_u$ should produce a straight line with slope $1/T_{\rm ex}$ and intercept $N(SO_2)/Q(T_{ex})$" (4.7 Excitation Temperature Analysis)
   - validation: _not stated_
7. **Derive disk mass from optically thick dust**: Require tau(43 GHz)>=1 with Chandler et al. mass opacity; D~100 AU  
  > "Then we find n$_{\rm H} \gtrsim 3.2\times 10^{10}$ cm$^{-3}$, and a disk mass $\gtrsim$0.02 $\hbox{M}_\odot$." (5.4 Dust?)
   - assumption: gas-to-dust 100, beta=1.1 (coagulated grains) or 2 (small grains), mu=1.36  
  > "Extrapolating to 43 GHz assuming $\beta$ = 1.1, and using a gas-to-dust mass ratio of 100" (5.4 Dust?)
   - fitting: _not stated_
   - validation: Upper limit from SiO maser quenching density <1e11 cm^-3  
  > "It’s also unlikely that gas densities exceed 10$^{11}$ cm$^{-3}$ on the disk surface" (5.4 Dust?)

## Software

- **CASA** : initial calibration with ALMA-supplied scripts  
  > "The raw visibility data were calibrated using ALMA-supplied scripts and the CASA software package." (2 OBSERVATIONS AND DATA REDUCTION)
- **Miriad** : all further processing: imaging, CLEAN, MAXEN, self-cal, imfit, uvfit  
  > "All further processing was done with `Miriad`." (2 OBSERVATIONS AND DATA REDUCTION)
- **Splatalogue** : line identification  
  > "often a feature matches 5 or 10 candidate transitions in the Splatalogue spectral line database" (4 SPECTRAL LINES)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Deconvolved size at 349 GHz | 0.24 x 0.07 | ±0.03 x ±0.06 | arcsec | 3 | / 349 / $0.25 \times 0.18$, $66\ensuremath{^\circ}$ / 05 35 14.5152 / -05 22 30.564 / 2014.6 / $790 \pm 80$ / $0.24 \pm 0.03 \times 0.07 \pm 0.06$ / $140 \pm 1$ / |
| Flux density at 349 GHz | 790 | ±80 | mJy | 3 | / 349 / $0.25 \times 0.18$, $66\ensuremath{^\circ}$ / 05 35 14.5152 / -05 22 30.564 / 2014.6 / $790 \pm 80$ / |
| Flux density at 661 GHz | 3455 | ±520 | mJy | 3 | / 661 / $0.16 \times 0.12$, $-50\ensuremath{^\circ}$ / 05 35 14.5129 / -05 22 30.576 / 2014.5 / $3455 \pm 520$ / |
| Flux density at 229 GHz (CARMA A+B) | 330 | ±50 | mJy | 3 | The 229 GHz flux density in Table [\[tab:gfits\]](#tab:gfits), $330\pm50$ mJy, is larger than the value $310\pm45$ mJy |
| Recombination line upper limit | <1.05 x continuum (line+continuum) | not stated | dimensionless | 4 | all channels within this velocity range have line + continuum flux densities that are $<~1.05~\times$ the mean continuum level. |
| Central mass | 5-7 | not stated | Msun | 5 | Central masses of 5-7 $\hbox{M}_\odot$ matched the data best |
| SO2 excitation temperature | 500 | not stated | K | 6 | The slope of the dashed line corresponds to an excitation temperature of 500 K |
| SO2 column density | 2e17 | not stated | cm^-2 | 6 | the intercept corresponds to an SO$_2$ column density N(SO$_2$) = $2\times10^{17}$ cm$^{-2}$ |
| Peak brightness temperature of continuum | ~480-500 | not stated | K | 3 | a 0.23$''$ $\times$ 0.07$''$ FWHM Gaussian source with a peak brightness temperature of 480 K |
| Minimum dust disk mass (optically thick at 43 GHz) | >=0.02 | not stated | Msun | 7 | Then we find n$_{\rm H} \gtrsim 3.2\times 10^{10}$ cm$^{-3}$, and a disk mass $\gtrsim$0.02 $\hbox{M}_\odot$. |
| Free-free optical depth lower limit | >3 | not stated | dimensionless | 4 | implies a free-free continuum opacity $\tau_{\rm ff} > 3$. |

## Qualitative findings

- Lines with EU<500 K appear in blueshifted absorption; EU>500 K in emission symmetric about VLSR=5 km/s  
  > "Lines with upper energy levels E$_{\rm U} > 500$ K appear in emission and are symmetric about the source’s LSR velocity of 5 $\rm km~s^{-1}$" (abstract)

## Claim tuples

- H: SrcI is a hypercompact HII region | E: Search for H26α and H21α recombination lines | R: No detection; line <5% of continuum | F: Free-free from an HII region ruled out; would need star more luminous than all of KL | **supported**
- H: Continuum arises from optically thick dust | E: Size and flux measured at 229-661 GHz; SED fit to nu^2 | R: ~0.23x0.07'' source, Tb~500 K, nu^2 to ~350 GHz | F: Optically thick ~500 K dust, disk mass 0.02-0.2 Msun | **supported**
- H: SrcI mass is ≳20 Msun as required by dynamical ejection | E: Keplerian ring model of line centroid rotation curves | R: 5-7 Msun best match | F: Dynamical decay model difficult to reconcile with low mass and 100 AU disk | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Scalar visibility averages used to find line-free channels in chemically rich Orion  
  > "a challenging task for a chemically rich region such as Orion" (2.1 Identifying Line-Free Channels)
- Alternative: Electron-neutral (H-) free-free rejected above ~200 GHz as needing implausible disk mass or temperature  
  > "electron-neutral free-free emission cannot be a significant source of opacity at frequencies higher than $\sim$200 GHz." (5.3 Electron-Neutral Free-Free Emission?)
- How they decided it was enough: _not stated_
- Limitation (authors): Minor axis poorly constrained since source is narrower than beams; centroid method idealized  
  > "SrcI is considerably narrower than the synthesized beams, so our measurements of the minor axis are particularly uncertain." (3 CONTINUUM IMAGES); "Of course the model is highly idealized" (4.5 Central Mass Estimate)
- Caveat (inferred, ours): Rotation-curve mass fit is by-eye with idealized edge-on ring; no formal uncertainties
- Caveat (inferred, ours): Disk mass strongly depends on assumed opacity and gas-to-dust ratio
- Caveat (inferred, ours): Minor axis deconvolved size differs by factor ~2 among methods
- Caveat (inferred, ours): Snapshot data with poor short-spacing coverage

## Reproducibility

- Data public (paper): ALMA project 2012.1.00123.S acknowledged; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00123.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Line-free channel lists
- Missing: CLEAN parameters (cell, image size, iterations, masks)
- Missing: CARMA data access/calibration
- Missing: Rotation-curve fit details
- Data volume (inferred): ~20-50 GB for two short ALMA execution blocks (raw), plus CARMA data
- Score (inferred): 3/5, Data and software (Miriad) identified and recipe broadly described, but key parameters and channel lists missing; mass and disk estimates rely on by-eye model and assumptions.
- Rediscovery candidate: no, Mass fit and line channel selection are not specified well enough for exact numeric redo, and CARMA data are needed.

## Links

- Method: (cite: Plambeck2013) (Earlier CARMA 229 GHz SrcI analysis and calibration)
- Method: (cite: Hirota2014) (Rotation-curve model followed)
- Method: (cite: Chandler2005) (Dust mass opacity procedure)
- Companion: (cite: Hirota2015) (ALMA observations of SrcI SED)
- Companion: (cite: Goddi2011) (VLA 43 GHz data and proper motions)
- Related: CARMA Orion observations
- Related: ALMA Band 6 science verification Orion-KL data

## Checks

```json
{
 "quotes": 83,
 "quotes_ok": 83,
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
  "facts": 84,
  "stated": 57,
  "rate": 0.679
 },
 "evidence_ok": true
}
```

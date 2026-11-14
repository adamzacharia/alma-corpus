# Spatially resolved star formation relation in two HI-rich galaxies with central post-starburst signature

`2017A&A...600A..80K` | Astronomy and Astrophysics 2017 | first author: Klitsch, Anne | arXiv: 1611.07672 | DOI: 10.1051/0004-6361/201527922

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation
- Question: Is the star formation activity of two HI-rich E+A-centre dwarf galaxies consistent with disc galaxies or a transition phase, and how does the SF relation scatter depend on scale?  
  > "The goal is to determine whether the SF activity of these galaxies is consistent with the activity seen in normal spiral galaxies, or if it shows signs of a transition towards another evolutionary phase." (Introduction)
- Target **ESO534-G001 (GalA)**: coordinates RA 22:36:06.69, Dec -26:18:51.5 (J2000)  
  > "The distance to these galaxies is 20 Mpc for GalA and 31 Mpc for GalB" (Introduction); "22:36:06.69" (Table 1); z/distance 20 Mpc (Vsys 1407 km/s)  
  > "The distance to these galaxies is 20 Mpc for GalA and 31 Mpc for GalB" (Introduction); "22:36:06.69" (Table 1); distance from not stated (H0 = 70 km/s/Mpc assumed)  
  > "The distance to these galaxies is 20 Mpc for GalA and 31 Mpc for GalB" (Introduction); "22:36:06.69" (Table 1)
- Target **2dFGRS S833Z022 (GalB)**: coordinates RA 04:14:37.41, Dec -22:48:25.1 (J2000)  
  > "The distance to these galaxies is 20 Mpc for GalA and 31 Mpc for GalB" (Introduction); "04:14:37.41" (Table 1); z/distance 31 Mpc (Vsys 2194 km/s)  
  > "The distance to these galaxies is 20 Mpc for GalA and 31 Mpc for GalB" (Introduction); "04:14:37.41" (Table 1); distance from not stated (H0 = 70 km/s/Mpc assumed)  
  > "The distance to these galaxies is 20 Mpc for GalA and 31 Mpc for GalB" (Introduction); "04:14:37.41" (Table 1)

## Data provenance

- ALMA projects: 2012.1.00293.S
- bands: Band 3 (Cycle 1), CO(1-0)  
  > "ALMA Cycle 1 observations in Band 3 were obtained" (2.2 CO(1-0) observations)
- frequencies and spectral setup: four basebands; one at 2.5 km/s resolution on CO, three low-resolution  
  > "one with a velocity resolution of 2.5 km s$^{-1}$ centred on the expected CO line, and the other three in low-resolution mode at lower frequencies" (2.2 CO(1-0) observations)
- continuum bandwidth: _not stated_
- arrays: 32 antennas available, 5 flagged  
  > "For these observations, 32 antennas were available, but 5 of these had to be flagged during the data reduction procedure." (2.2 CO(1-0) observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 3 arcsec  
  > "to obtain a spatial resolution of 3 arcsec" (2.2 CO(1-0) observations)
- max recoverable scale: ~20 arcsec  
  > "The largest observable scale with the array configuration we used is $\sim$20$''$." (2.2 CO(1-0) observations)
- sensitivity: ~1.5 mJy/beam per 10 km/s  
  > "The measured r.m.s. noise level is $\sim$1.5 mJy beam$^{-1}$ per 10 km s$^{-1}$." (2.2 CO(1-0) observations)
- time on source: 100 min GalA, 40 min GalB  
  > "The total on-source integration times were 100 minutes for GalA and 40 minutes for GalB." (2.2 CO(1-0) observations)
- observing dates: GalA 13.12.2013 and 23.03.2014; GalB 17.12.2013  
  > "ALMA | CO(1-0) | 13.12.2013 | 3100 s" (Table 2)
- pi or archival as stated: _not stated_
- Line: CO J=1-0 (115.27 GHz)
- Other facility **VLA (BnA, CnB)**: HI 21 cm cubes at ~4 arcsec  
  > "we observed the two galaxies in the HI 21 cm emission line using the VLA in its hybrid BnA and CnB configurations" (2.1 HI 21cm line observations)
- Other facility **WiFeS IFU (2.3m SSO)**: optical IFU cubes for Halpha, metallicity, stellar mass, stellar sigma (from Pracy et al. 2014)  
  > "The target galaxies were observed on 2012 November 12 using the Wide Field Spectrograph (WiFeS)." (2.3 Integral field spectra)
- Other facility **GALEX**: NUV images, used only for contours/colour, not in analysis  
  > "We did not use the GALEX data for our further analysis because of a lack of a solid estimate of dust extinction." (1 Introduction)
- External data: Single-dish HI fluxes, HI masses, stellar masses, E+A identification  
  > "M$_{\rm HI}$ is the total hydrogen mass (all four determined by (cite: zwaan2013cold)" (Table notes (Table of galaxy properties, Introduction)) [from (cite: zwaan2013cold)]
- External data: Reduced, flux-calibrated optical IFU cubes  
  > "we use the fully reduced and flux-calibrated data cubes from (cite: pracy2014integral)" (2.3 Integral field spectra) [from (cite: pracy2014integral)]
- External data: Comparison samples for the atomic SK relation (spirals, LITTLE THINGS, LMC, ultra-faint dwarfs)  
  > "a sample of spatially resolved local spiral galaxies compiled by (cite: bigiel2008star), disc-average values from local dwarf galaxies from the LITTLE THINGS Survey (cite: zhang2012hipower)" (4 Star formation rate prediction) [from (cite: bigiel2008star); (cite: zhang2012hipower); (cite: stavley-smith2003new); (cite: roychowdhury2015spatially)]
- External data: L_CO vs M_B relation for spirals and dwarfs  
  > "we compare the upper limits in L$_{\rm CO}$ with a literature sample of normal spirals and dwarf galaxies from (cite: schruba2012low)" (3.2 Molecular hydrogen) [from (cite: schruba2012low)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: ALMA: monitored unresolved targets (unnamed); VLA: 3C147  
  > "The absolute flux scale was obtained through observing unresolved targets whose flux scale is regularly monitored by the ALMA observatory." (2.2 CO(1-0) observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5  
  > "a ’robust’ weighting scheme with a Briggs parameter of 0.5" (2.2 CO(1-0) observations)
- uv taper: slight tapering of longest baselines  
  > "Cubes were made using a slight tapering of the longest baseline data" (2.2 CO(1-0) observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: CO cube velocity resolution 10 km/s  
  > "The velocity resolution of the cubes was set at 10 km s$^{-1}$." (2.2 CO(1-0) observations)
- final beam: _not stated_
- final rms: ~1.5 mJy/beam per 10 km/s  
  > "The measured r.m.s. noise level is $\sim$1.5 mJy beam$^{-1}$ per 10 km s$^{-1}$." (2.2 CO(1-0) observations)

### Inherited from earlier work

- Four-step tilted-ring parameter fixing procedure  
  > "We subsequently fix the parameters in a four-step procedure following (cite: noordermeer2007mass)." (3.1 Neutral hydrogen) [from (cite: noordermeer2007mass)]
- KL14 model parameters adopted  
  > "For the KL principle predictions, we adopt the parameters given in (cite: kruijssen2014uncertainty)." (4.1) [from (cite: kruijssen2014uncertainty)]
- HI surface density conversion with helium factor 1.36  
  > "deprojecting and including a factor of 1.36 to account for the presence of helium (cite: leroy2008star)" (3.1 Neutral hydrogen) [from (cite: leroy2008star)]

### Not stated but needed to reproduce (our reading)

- CASA version and pipeline used for ALMA calibration and imaging
- ALMA flux calibrator names and calibration details
- CO cube clean parameters (deconvolver, mask, threshold, cell/image size, taper value)
- ALMA array configuration and baselines
- Measured CO beam and exact cube velocity range
- Whether 60 offset spectra use the same mask
- Tilted-ring ROTCUR initial values and ring widths
- Pipeline for Halpha flux map extraction and extinction correction details
- Fitted KL14 parameter values in text (only in figure legend)

## Analysis recipe

1. **Calibrate and image HI and CO data**: CASA calibration, continuum subtraction, multiscale clean with Briggs 0.5  
  > "The imaging was done using the standard clean algorithm. The multi-scale option was used" (2.1 HI 21cm line observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **HI maps and rotation curves**: Moment maps with masks from 25 arcsec-smoothed CnB cubes (2 sigma), 3 sigma cut; tilted-ring fits with ROTCUR  
  > "we use the tilted ring model of (cite: begeman1989hi)" (3.1 Neutral hydrogen)
   - software: GIPSY ROTCUR
   - fitting: tilted ring model  
  > "To determine the deprojected rotation curves, we use the tilted ring model of (cite: begeman1989hi), which describes a galaxy as a set of concentric rings" (Analysis and results, Neutral hydrogen)
   - validation: residual velocity field mean deviation (0±3) km/s GalA, (1±7) km/s GalB  
  > "The mean deviation is (0 $\pm$ 3) km s$^{-1}$ for GalA and (1 $\pm$ 7) km s$^{-1}$ for GalB." (3.1 Neutral hydrogen)
3. **CO upper limit by stacking**: De-rotate CO cubes using HI velocities, stack where Sigma_HI > 1 Msun/pc2, sum over ±HI dispersion, error from 60 velocity-offset repeats  
  > "The uncertainty on the flux measurement is calculated by repeating the same exercise 60 times, but each time offsetting the central velocity by at most 300 km s$^{-1}$." (3.2 Molecular hydrogen)
   - assumption: alpha_CO ≈ 70 Msun/(K km/s pc2) for 12+log(O/H)=8.2  
  > "we estimate that $\alpha_{\rm CO} \approx 70 \; \si{M}_{\odot}\si{(K \; km \; s^{-1} \; pc^2)^{-1}}$ is an appropriate conversion factor" (3.2 Molecular hydrogen)
   - fitting: _not stated_
   - validation: compared with Schruba et al. 2012 L_CO–M_B  
  > "Finally, we compare the upper limits in L$_{\rm CO}$ with a literature sample of normal spirals and dwarf galaxies from (cite: schruba2012low), shown in Fig. [3](#FigCompSchruba)." (Analysis and results, Molecular hydrogen)
4. **Metallicity and stellar properties from IFU**: R23 and N2 metallicity after ppxf stellar subtraction and Calzetti de-reddening; Bell et al. M/L for stellar mass surface density  
  > "we determine the gas metallicity with the R23 method" (3.2 Molecular hydrogen)
   - software: ppxf
   - fitting: ppxf with MILES  
  > "we determine the stellar velocity dispersions with ppxf (cite: cappellari2004parametric) and the MILES library" (Analysis and results, Integral field spectra)
   - validation: _not stated_
5. **Halpha SFR and pressure-based SFR prediction**: Murphy et al. 2011 Halpha calibration; Blitz & Rosolowsky pressure law compared with observed Halpha/NUV  
  > "We use the empirical law determined by (cite: blitz2006role) with the updated values from (cite: leroy2008star)" (4 Star formation rate prediction)
   - fitting: _not stated_
   - validation: _not stated_
6. **Fit scale dependence of scatter with KL14 model**: Top-hat convolution at increasing aperture sizes, scatter of log(L_HI/L_Halpha), least-squares fit of KL14 model with weights = inverse errors  
  > "We attempt to constrain the free parameters by performing a least-squares fit of the KL14 model to the data, where the weights are the inverse errors of the observed scatter." (4.1)
   - software: KL14 principle code
   - parameter: t_star fixed to 6 Myr; t_gas fixed 25 Myr or free  
  > "we fix $t_{\rm star}$ to a value of 6 Myr because we use H$\alpha$ to trace the SF" (4.1)
   - fitting: least squares, 2- and 3-parameter fits  
  > "We attempt to constrain the free parameters by performing a least-squares fit of the KL14 model to the data, where the weights are the inverse errors of the observed scatter." (Understanding the scale-dependence of the star formation relation)
   - validation: parameters strongly correlated (>0.7)  
  > "the parameters are strongly correlated, with correlation coefficients larger than 0.7" (Understanding the scale-dependence of the star formation relation)

## Software

- **CASA** 4.2.2: VLA calibration and imaging (ALMA reduction said to be with CASA)  
  > "Common Astronomy Software Applications (CASA 4.2.2) software package" (2.1 HI 21cm line observations)
- **GIPSY (ROTCUR)** : tilted-ring rotation curves  
  > "we use the GIPSY task ROTCUR" (3.1 Neutral hydrogen)
- **ppxf** : stellar template fitting and stellar velocity dispersion  
  > "fitting and removing an optimal template from the MILES library (cite: sanchez-blazquez2006medium) with `ppxf`" (3.2 Molecular hydrogen)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO luminosity upper limit GalA (3 sigma) | <1.9e4 | not stated | K km/s pc^2 | 3 | $<$1.9 |
| CO luminosity upper limit GalB (3 sigma) | <4.6e4 | not stated | K km/s pc^2 | 3 | $<$4.6 |
| H2 mass upper limit GalA / GalB | 1.3e6 / 3.3e6 | not stated | Msun | 3 | 1.3 $\times10^6$ M$_{\ensuremath{\odot}}$ (GalA) and $3.3 \times 10^6$ M$_{\ensuremath{\odot}}$ (GalB) |
| HI mass GalA | 10.1e8 | 0.2e8 | Msun | 2 | $M_{\si{HI}}$ = (10.1 $\pm$ 0.2) $\times10^8$M$_{\ensuremath{\odot}}$ (GalA) |
| HI mass GalB | 11.3e8 | 0.6e8 | Msun | 2 | $M_{\si{HI}}$ = (11.3 $\pm$ 0.6) $\times10^8$ M$_{\ensuremath{\odot}}$ (GalB) |
| Max rotation velocity GalA / GalB | 69 / 75 | 3 / 13 | km/s | 2 | (69 $\pm$ 3) km s$^{-1}$ (GalA) and (75 $\pm$ 13) km s$^{-1}$ (GalB) |
| Halpha SFR GalA / GalB | 0.07 / 0.3 | not stated | Msun/yr | 5 | integrated SFRs of 0.07 M$_{\odot}$ yr$^-1$ for GalA and 0.3 M$_{\odot}$ yr$^-1$ for GalB |
| Molecular depletion time GalA / GalB | 18 / 11 | not stated | Myr | 5 | the corresponding gas depletion times $t_{\rm depl}$ are 18 Myr and 11 Myr |
| Adopted gas metallicity | 12+log(O/H)=8.2 | not stated | dex | 4 | we adopt $12 + \log(\text{O}/\text{H}) = 8.2$ for this paper |

## Qualitative findings

- HI is smoothly distributed in regularly rotating discs; CO not detected.  
  > "We find regularly rotating HI gas that is smoothly distributed across the entire disc. The CO(1-0) emission line is not detected for either of the two galaxies." (abstract)

## Claim tuples

- H: Pressure-based SF law predicts local SFR in HI-dominated regions | E: Compare predicted SFR maps with Halpha/NUV | R: Predicted and observed peaks are at different positions | F: Law applies only globally, not at cloud scale | **supported**
- H: Molecular gas is abundant enough to fuel SF | E: Stacked ALMA CO(1-0) upper limits | R: M(H2) < 1.3e6 and 3.3e6 Msun; t_depl ≲ 20 Myr | F: Short depletion times, highly uncertain due to alpha_CO | **partially**
- H: Scatter in atomic SF relation increases at small scales as predicted by KL14 | E: Fit KL14 model to scatter vs aperture size | R: Observations agree with predictions | F: Scale dependence consistent with incomplete sampling of HI clouds and SF regions | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA data insensitive to scales >~20 arcsec; confirmation with single-dish needed  
  > "These upper limits are only valid for molecular hydrogen structures on angular scales smaller than $\sim$20$''$ or $\sim$2 kpc." (Summary)
- Caveat (inferred, ours): alpha_CO and metallicity are highly uncertain (8.13 to 8.81)
- Caveat (inferred, ours): Only two galaxies; KL14 fit parameters degenerate
- Caveat (inferred, ours): Non-detection gives only upper limits

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA CASA version and imaging parameters
- Missing: KL14 fitted parameter values
- Missing: Pracy et al. IFU cubes and Halpha maps
- Data volume (inferred): ~10-50 GB for ALMA; VLA additional
- Score (inferred): 3/5, Project code given and recipe for stacking fairly clear, but ALMA processing details and IFU data missing; results are non-detection limits.
- Rediscovery candidate: no, ALMA result is an upper limit and depends on external IFU data and unstated imaging details.

## Links

- Method: (cite: kruijssen2014uncertainty) (Uncertainty principle model for scale-dependent SF scatter)
- Method: (cite: begeman1989hi) (Tilted ring model)
- Companion: (cite: zwaan2013cold) (Sample selection and single-dish HI)
- Companion: (cite: pracy2014integral) (Optical IFU observations)
- Related: LITTLE THINGS
- Related: THINGS

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
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 49,
  "rate": 0.605
 },
 "evidence_ok": true
}
```

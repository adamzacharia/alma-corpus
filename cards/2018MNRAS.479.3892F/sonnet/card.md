# The complex jet- and bar-perturbed kinematics in NGC 3393 as revealed with ALMA and GEMINI-GMOS/IFU

`2018MNRAS.479.3892F` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Finlez, Carolina | arXiv: 1806.02756 | DOI: 10.1093/mnras/sty1555

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: How do radio jets and bars perturb the molecular and ionised gas kinematics in the Seyfert 2 galaxy NGC 3393, and is there evidence for a secondary SMBH?  
  > "In this work we analyse the bar- and jet- induced perturbations on the molecular and ionised gas in NGC 3393 using new data from ALMA (CO J:2-1) and GEMINI-GMOS/IFU" (Introduction)
- Target **NGC 3393**: coordinates _not stated_; z/distance z = 0.012442 (optical); 52 Mpc luminosity distance  
  > "at an estimated redshift of 0.012442 (optical), or 0.012509 (from the 21 cm line) which corresponds to a luminosity distance of $52$ Mpc and a scale of $0.25$ kpc/arcsec, assuming $H_{o} = 73$ km s$^{-1}$ Mpc$^{-1}$." (Introduction); distance from redshift with H0 = 73 km/s/Mpc  
  > "at an estimated redshift of 0.012442 (optical), or 0.012509 (from the 21 cm line) which corresponds to a luminosity distance of $52$ Mpc and a scale of $0.25$ kpc/arcsec, assuming $H_{o} = 73$ km s$^{-1}$ Mpc$^{-1}$." (Introduction)

## Data provenance

- ALMA projects: 2015.1.00086.S
- bands: _not stated_
- frequencies and spectral setup: Four 1.875 GHz spws: CO 2-1 (2.5 km/s channels), TDM continuum at 232.538 GHz, CS 5-4, TDM continuum at 246.936 GHz  
  > "Four basebands (spw’s) were used: each set to an effective bandwidth of 1.875 GHz." (2.2 ALMA: CO J:2-1)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.56'' (143 pc) in abstract  
  > "at 0.56$''$ (143 pc) spatial and 5 km/s spectral resolution" (abstract)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: ~26 min with 41 antennas  
  > "Forty one antennas were used and the total integration time on NGC 3393 was $\sim$26 min." (2.2 ALMA: CO J:2-1)
- observing dates: May 3, 2016  
  > "NGC 3393 was observed on May 3, 2016" (2.2 ALMA: CO J:2-1)
- pi or archival as stated: Project 2015.1.00086.S (P.I. Nagar)  
  > "as part of Project 2015.1.00086.S (P.I. Nagar)" (2.2 ALMA: CO J:2-1)
- Line: CO J=2-1 (230.538 GHz)
- Line: CS J=5-4 (244.935 GHz)
- Other facility **Gemini South GMOS-IFU**: Optical IFU spectra for stellar and ionised gas kinematics  
  > "The observations were obtained with the Integral Field Unit of the Gemini Multi Object Spectrograph" (2.1 GEMINI-GMOS/IFU)
- Other facility **HST**: F606W image used for structure map  
  > "overlaid on an HST F606W image to which we applied an unsharp-mask filter" (3.3 Molecular gas)
- External data: VLA 8.4 GHz radio map and fluxes  
  > "observed in the VLA 8.4 GHz data (cite: koss2015)" (3.3 Molecular gas) [from (cite: koss2015)]
- External data: Large-scale bar ellipticity 0.15 and PA 160 deg  
  > "to the values obtained for the large-scale bar by (cite: jungwiert1997)" (4.2.1 Large-scale bar) [from (cite: jungwiert1997)]

## Processing

### Calibration

- pipeline or manual: Manual, mostly following the ALMA-provided calibration script  
  > "mostly followed the calibration script provided by the ALMA observatory (the CASA calibration pipeline was not available at the time of the release of this dataset)" (2.2 ALMA: CO J:2-1)
- casa version: CASA 4.7  
  > "Data were calibrated and imaged using CASA version 4.7" (2.2 ALMA: CO J:2-1)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: No flux calibrator observed; phase calibrator J1037-2934 set to 602 mJy at 235.7 GHz  
  > "flux calibration was performed by setting the flux of the phase calibrator J1037-2934 to 602 mJy at 235.7 GHz" (2.2 ALMA: CO J:2-1)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Continuum robust=2 (natural); CO cube (a) robust=0.2; cube (b) natural  
  > "a higher spatial and spectral resolution cube, made using ’Briggs weighting’ with robust=0.2" (2.2 ALMA: CO J:2-1)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum subtracted in uv-data before line imaging; continuum from line-free channels  
  > "The continuum-subtracted $uv$-data were then used to image the CO J:2-1 line." (2.2 ALMA: CO J:2-1)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Cube (b): 4-channel spectral averaging to 10 km/s  
  > "made using ’natural’ weighting, and 4-channel spectral averaging" (2.2 ALMA: CO J:2-1)
- final beam: Cube (a) 0.58'' x 0.5'' PA -72; cube (b) 0.73'' x 0.62'' PA 86; continuum 0.71'' x 0.61'' PA 85  
  > "This datacube has a synthesised beam with major (minor axis) of 0.58$''$ (0.5$''$) with a beam PA of $-$72$^{\circ}$" (2.2 ALMA: CO J:2-1)
- final rms: Cube (a) 0.7 mJy/beam per 2.5 km/s; cube (b) 0.45 mJy/beam per 10 km/s; continuum 0.023 mJy/beam  
  > "an r.m.s. noise of 0.7 mJy/beam per 2.5 km/s channel" (2.2 ALMA: CO J:2-1)

### Inherited from earlier work

- GMOS data reduction procedure  
  > "The data processing was performed using tasks from the GEMINI.GMOS package for IRAF, following (cite: lena2014)." (2.1 GEMINI-GMOS/IFU) [from (cite: lena2014)]
- Outflow mass and rate method  
  > "following (cite: lena2015)" (4.1.1 Jet driven outflow) [from (cite: lena2015)]
- Harmonic decomposition bar formalism  
  > "we have applied the harmonic decomposition formalism described in (cite: sfdz1997) and (cite: wong2004)" (4.2 Bar perturbations) [from (cite: sfdz1997); (cite: wong2004)]

### Not stated but needed to reproduce (our reading)

- Line-free channels for continuum
- CLEAN threshold, masks, cell and image size
- Moment map clipping thresholds
- Fit uncertainties for rotation and bar models
- Calibration script details and flagging
- Spatial binning of the CO field for model fitting
- Per-parameter best-fit damping and pattern speed for the large-scale bar

## Analysis recipe

1. **Calibrate and image ALMA data**: Manual CASA calibration with phase calibrator flux scale; continuum and CO cubes imaged  
  > "flux calibration was performed by setting the flux of the phase calibrator J1037-2934 to 602 mJy at 235.7 GHz" (2.2 ALMA: CO J:2-1)
   - software: CASA
   - parameter: robust=0.2 and natural cubes  
  > "made using ’Briggs weighting’ with robust=0.2" (2.2 ALMA: CO J:2-1)
   - fitting: _not stated_
   - validation: Phase calibrator flux compared to 630 mJy measured 12 days later  
  > "The ALMA calibrator database shows that this source had a measured flux of 630 mJy when observed 12 days later" (2.2 ALMA: CO J:2-1)
2. **Fit outer CO velocity field with exponential disk**: Least-squares fit of exponential disk rotation model to CO velocity field  
  > "We perform a least-square minimization (using the MPFIT2DFUN routine in IDL) to obtain the parameters that best fit the observed CO J:2-1 velocity field" (3.3 Molecular gas)
   - software: MPFIT2DFUN
   - parameter: PA fixed 40 deg, i fixed 25 deg, -26 km/s offset from systemic  
  > "we thus fix the major axis PA to $40 \degree$" (3.3 Molecular gas)
   - assumption: Infinitesimally thin disk, inclination 25 deg  
  > "For this model we assume an infinitesimally thin disk" (3.3 Molecular gas)
   - fitting: Least-squares, free r_d and M_d  
  > "For the free parameters $r_{d}$ and $M_{d}$, the mass and scale length of the disk respectively" (3.3 Molecular gas)
   - validation: Compared with HST-based values of Lasker et al.  
  > "the values obtained by the HST light distribution modelling of (cite: lasker2016) are $r_{d} = 1.38$ kpc" (3.3 Molecular gas)
3. **Fit bar perturbation models to CO velocity field**: Harmonic decomposition models with free damping and pattern speed; large-scale bar outside 5'' and nuclear bar inside  
  > "we build bar perturbation models for the nuclear bar" (4.2.2 Nuclear bar)
   - software: MPFIT2DFUN
   - parameter: Large bar epsilon=0.15, PA=160 deg fixed; nuclear bar free lambda, Omega_p, epsilon within ranges  
  > "Typical ranges were assumed for the free parameters: $0.15 < \lambda < 0.4$, $0.1 < \epsilon < 0.8$, $10 < \Omega_{p} < 200$ km/s/kpc." (4.2.2 Nuclear bar)
   - assumption: Linear epicycle theory, weak bar, nuclear bar decoupled from large-scale bar  
  > "it is only valid for weak bars" (4.2 Bar perturbations)
   - fitting: Least-squares  
  > "by using the same least-square minimization routine as explained above" (4.2.1 Large-scale bar)
   - validation: Compared with minor-axis pv diagram  
  > "we compare the model with data extracted along the minor axis in the pv-diagram" (4.2.1 Large-scale bar)

## Software

- **CASA** 4.7: ALMA calibration and imaging  
  > "Data were calibrated and imaged using CASA version 4.7" (2.2 ALMA: CO J:2-1)
- **pPXF** 5.2.1: Stellar kinematics  
  > "penalised pixel-fitting (pPXF v5.2.1) routine" (3.1 Stellar kinematics)
- **MPFIT2DFUN** : Least-squares fits of rotation and bar models  
  > "We perform a least-square minimization using the IDL routine MPFIT2DFUN" (3.1 Stellar kinematics)
- **PROFIT** : Gaussian emission line fitting  
  > "custom IDL routine based on the routine PROFIT" (3.2 Ionised gas)
- **IRAF GEMINI.GMOS** : GMOS data reduction  
  > "tasks from the GEMINI.GMOS package for IRAF" (2.1 GEMINI-GMOS/IFU)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA 239 GHz continuum rms | 0.023 | not stated | mJy/beam | 1 | the r.m.s. noise is 0.023 mJy/beam |
| Exponential disk scale length r_d | 1 | not stated | kpc | 2 | $r_{d} = 1$kpc and $M_{d} = 2.7 \times 10^{10}$ M$_{\odot}$ |
| Exponential disk mass M_d | 2.7e10 | not stated | Msun | 2 | $r_{d} = 1$kpc and $M_{d} = 2.7 \times 10^{10}$ M$_{\odot}$ |
| Nuclear bar pattern speed | 73 | not stated | km/s/kpc | 3 | $\lambda = 0.1$, $\Omega_{p} = 73$ km/s/kpc and $\epsilon = 0.35$ |
| SE feature molecular mass | 5.4e7 | not stated | Msun | 0 | M(H$_{2}$) = 5.4 $\times 10^{7}$ M$_{\odot}$, assuming $\alpha_{CO} = 4.6$ |
| Equatorial outflow rate | 0.24 | not stated | Msun/yr | 0 | The estimated equatorial outflow rate, under these assumptions, is $\dot M = 0.24$ M$_{\odot}/$yr. |
| 230 GHz nuclear continuum flux | 0.2 | not stated | mJy | 1 | The 230 GHz total fluxes are 0.2 mJy for the nuclear source |

## Qualitative findings

- Ionised gas shows narrow, broad redshifted and broad blueshifted components, interpreted as rotation, jet-driven outflow and equatorial outflow  
  > "we interpret this as an equatorial outflow." (abstract)

## Claim tuples

- H: Are the inner CO kinematics explained by bar perturbations? | E: Fit bar-perturbation models to inner and outer CO velocity fields | R: Nuclear bar model reproduces the SE gradient; single m=2 mode fails globally | F: Inner kinematics dominated by nuclear bar perturbations and bar interaction | **supported**
- H: Is there a secondary SMBH? | E: Search ionised and CO kinematics and continuum at posited position | R: No clear kinematic or continuum source | F: No evidence, but cannot rule out | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Secondary SMBH nuclear disk for SE CO gradient; disfavoured as it would need a special geometry  
  > "Simpler explanations, such as the nuclear bar perturbations are thus favoured by us." (4.3 SMBH)
- How they decided it was enough: _not stated_
- Limitation (authors): Sparse CO filling factor limits the analysis  
  > "The primary limitation in the analysis above is the sparse filling factor of CO velocities over the FOV." (4.2.1 Large-scale bar)
- Caveat (inferred, ours): Flux scale from calibrator value, no flux calibrator observed
- Caveat (inferred, ours): Bar models are toy models with fixed PA and inclination
- Caveat (inferred, ours): No uncertainties on fitted parameters

## Reproducibility

- Data public (paper): Project code given; ALMA data acknowledged via ADS/JAO  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA# 2015.1.00086.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Custom IDL routines not released
- Missing: Imaging parameters such as masks and thresholds
- Missing: Bar model code details
- Data volume (inferred): ~10-30 GB raw single-execution Band 6 data
- Score (inferred): 3/5, Data public and imaging described, but custom IDL code and model fit details are not given.
- Rediscovery candidate: no, Key results depend on custom models and GMOS data, with incomplete fit specifications.

## Links

- Method: (cite: wong2004) (Harmonic decomposition bar model formalism)
- Companion: (cite: koss2015) (VLA radio and Chandra data on NGC 3393)

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
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
  "facts": 72,
  "stated": 45,
  "rate": 0.625
 },
 "evidence_ok": true
}
```

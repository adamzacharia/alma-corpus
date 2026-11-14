# High-resolution ALMA observations of SDP.81. I. The innermost mass profile of the lensing elliptical galaxy probed by 30 milli-arcsecond images

`2015PASJ...67...72T` | Publications of the Astronomical Society of Japan 2015 | first author: Tamura, Yoichi | arXiv: 1503.07605 | DOI: 10.1093/pasj/psv040

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: What is the innermost mass profile and central SMBH mass of the foreground elliptical lensing SDP.81, derived from lens modeling of 30 mas ALMA images?  
  > "Here we present a detailed modeling of a mass profile of the $z = 0.2999$ elliptical galaxy, which is the foreground galaxy in the galaxy–galaxy lensing system H-ATLAS J090311.6+003906 (SDP.81)" (1 Introduction)
- Target **SDP.81 (H-ATLAS J090311.6+003906) and lens SDSS J0903**: coordinates SDSS J090311.57+003906.5 (lens)  
  > "The foreground elliptical galaxy is identified in the Sloan Digital Sky Survey (SDSS) as SDSS J090311.57+003906.5 (hereafter SDSS J0903) with a spectroscopic redshift of $z = 0.2999 \pm 0.0002$ (cite: Negrello14)." (1 Introduction); z/distance lens z = 0.2999; source z = 3.042  
  > "The foreground elliptical galaxy is identified in the Sloan Digital Sky Survey (SDSS) as SDSS J090311.57+003906.5 (hereafter SDSS J0903) with a spectroscopic redshift of $z = 0.2999 \pm 0.0002$ (cite: Negrello14)." (1 Introduction); distance from Negrello14 (lens spectroscopic redshift)  
  > "The foreground elliptical galaxy is identified in the Sloan Digital Sky Survey (SDSS) as SDSS J090311.57+003906.5 (hereafter SDSS J0903) with a spectroscopic redshift of $z = 0.2999 \pm 0.0002$ (cite: Negrello14)." (1 Introduction)

## Data provenance

- ALMA projects: 2011.0.00016.SV
- bands: 1.0, 1.3 and 2.0 mm  
  > "The ALMA data at wavelengths of 1.0, 1.3 and 2.0 mm were obtained during the long baseline campaign of Science Verification" (2.1 ALMA observations and images)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 23×31 mas (1.0 mm), 30×39 mas (1.3 mm), 54×60 mas (2.0 mm)  
  > "$23 \times 31$ mas (PA = 15$\ensuremath{^\circ}$), $30 \times 39$ mas (PA = 20$\ensuremath{^\circ}$) and $54 \times 60$ mas (PA = 18$\ensuremath{^\circ}$)" (2.1 ALMA observations and images)
- max recoverable scale: _not stated_
- sensitivity: rms 10, 10, 9 µJy/beam  
  > "with r.m.s. noise level of 10, 10, and 9 $\mu$Jy beam$^{-1}$, respectively" (2.1 ALMA observations and images)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO 5-4, 8-7, 10-9 (not stated)
- Other facility **HST/WFC3 F160W**: Archival 1.6 µm image for stellar light profile and lens-galaxy deblending  
  > "We retrieve the archival HST image (proposal ID: 12194, (cite: Negrello14)) taken with the Wide Field Camera 3 (WFC3) at 1.6 $\ensuremath{\mu}m$ (F160W, *H* band)." (2.2 Hubble images)
- Other facility **SDSS DR12**: Catalog for HST astrometric calibration  
  > "We calibrate the coordinates of the WFC3 image using the catalog data from the SDSS Data Release 12" (2.2 Hubble images)
- External data: Total 1.0-mm flux 37.7 ± 1.5 mJy  
  > "total flux ($37.7 \pm 1.5$ mJy, (cite: Vlahkis15))" (4 Discussions and conclusions) [from Vlahkis15]
- External data: FIRST 20 cm flux of central source 1.21 ± 0.16 mJy  
  > "$S_\mathrm{20cm} = 1.21 \pm 0.16$ mJy beam$^{-1}$, (cite: Becker95)" (2.1 ALMA observations and images) [from Becker95]
- External data: Cluster at z=0.306, richness ~21, from SDSS cluster catalog  
  > "We examine the SDSS cluster catalog of (cite: Oguri14) and find a cluster of galaxies at $z = 0.306$ with the richness of $\sim 21$" (3.1 Methods and results) [from Oguri14]

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

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: CO images uv-tapered to ≃170 mas  
  > "The CO images are $uv$-tapered to $\simeq 170$ mas in order to increase the sensitivity to extended structure." (2.1 ALMA observations and images)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA observation and calibration details  
  > "Details of the observations are given in (cite: Vlahkis15) and (cite: Fomalont15)." (2.1 ALMA observations and images) [from Vlahkis15; Fomalont15]
- Two-Sérsic deblending procedure for HST  
  > "Following the procedure adopted by (cite: Negrello14), two Sérsic profiles are simultaneously fitted to the HST image." (2.2 Hubble images) [from Negrello14]

### Not stated but needed to reproduce (our reading)

- ALMA imaging/calibration settings (tclean parameters, robust, CASA version) are deferred to other papers
- Exact positions and fluxes of the 46 identified knots
- Initial parameter values and MCMC settings (chain length, priors) for GLAFIC
- Fixed reference position of the non-thermal source
- Mass-to-light ratio uncertainty treatment

## Analysis recipe

1. **Identify the central non-thermal source**: Compare 1.0–2.0 mm spectral index and extrapolation to 20 cm FIRST flux; check for lines  
  > "The power-law spectral index from 1.0 mm to 20 cm is $\alpha = -0.64 \pm 0.01$" (2.1 ALMA observations and images)
   - fitting: _not stated_
   - validation: _not stated_
2. **Deblend HST stellar light**: Two Sérsic fit to HST F160W image  
  > "We use the GALFIT software (Version 3.0.5, (cite: Peng10)) to deblend the stellar light in SDP.81 from SDSS J0903." (2.2 Hubble images)
   - software: GALFIT
   - fitting: _not stated_
   - validation: _not stated_
3. **Identify multiple images of knots**: Match continuum peaks with similar CO profiles, then use an initial model to find counter-images of 1.0-mm knots within ~50 mas  
  > "The knots within $\simeq 50$ mas from the predicted positions are identified as the counter-images, resulting in identifications of 46 images." (3.1 Methods and results)
   - software: GLAFIC
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit lens mass model**: Isothermal ellipsoid with core, external shear, third-order and (4,2) multipole perturbations fit to image positions with MCMC errors  
  > "We then refine the mass model by adding the higher-order perturbations (the number of independent parameters is 12) and fitting all of the identified multiple images." (3.1 Methods and results)
   - software: GLAFIC
   - parameter: Position uncertainty 20 mas; 100–200 mas for 10 blended knots; 130–200 mas for HST images; N_DOF = 88  
  > "The positional uncertainty of the knots used for optimization is set to 20 mas" (3.1 Methods and results)
   - assumption: Flat universe Ωm=0.26, ΩΛ=0.74, H0=72  
  > "we assume a flat universe with $\Omega_\mathrm{m} = 0.26$, $\Omega_{\Lambda} = 0.74$, and $H_0 = 72$ km s$^{-1}$ Mpc$^{-1}$" (1 Introduction)
   - fitting: Chi-square minimization with MCMC for 68% intervals  
  > "the $1\sigma$ confidence intervals are computed by Marcov-chain Monte Carlo simulations" (3.1 Methods and results)
   - validation: Compared with independent ALMA (Rybak15, Dye15) and HST (Dye14) models  
  > "The best-fit parameters of the isothermal ellipsoid and external shear are in good agreement with those independently obtained using the same ALMA images" (3.1 Methods and results)
5. **Compare lens mass profile with stellar light**: Convergence profile vs HST profile scaled by M/L = 2, lens model smoothed by HST PSF  
  > "the stellar surface mass is scaled using a fiducial mass-to-light ratio of $2~M_{\solar}~L_{\solar}^{-1}$" (3.2 Mass profile of SDSS J0903)
   - assumption: M/L = 2 Msun/Lsun at ~1 µm  
  > "which is a typical value for local massive ellipticals" (3.2 Mass profile of SDSS J0903)
   - fitting: _not stated_
   - validation: _not stated_
6. **Constrain SMBH mass from central image non-detection**: Add point mass 1e7–1e9 Msun with r_core fixed to 150 mas; compute S_cent/S_tot vs M_BH; compare with 3σ limit  
  > "A point mass with $M_\mathrm{BH} = 10^7$ to $10^9\,M_{\Sol}$ is placed at the position of the AGN and $r_\mathrm{core}$ is fixed to the stellar core radius of $150$ mas" (4 Discussions and conclusions)
   - software: GLAFIC
   - fitting: _not stated_
   - validation: Compared with M_BH–sigma relation of Kormendy13  
  > "using the local correlation (cite: Kormendy13) is $M_\mathrm{BH} = (1 \pm 0.1) \times 10^9$ $M_{\Sol}$" (4 Discussions and conclusions)

## Software

- **GLAFIC** : Lens modeling  
  > "We use the GLAFIC software (cite: Oguri10)[^2] to reproduce the lensed image using an isothermal ellipsoid with a flat core." (3.1 Methods and results)
- **GALFIT** 3.0.5: Deblending stellar light in HST image  
  > "We use the GALFIT software (Version 3.0.5, (cite: Peng10)) to deblend the stellar light in SDP.81 from SDSS J0903." (2.2 Hubble images)
- **IRAF** : Astrometric fit of HST image to SDSS  
  > "We use 46 SDSS objects located in the WFC3 image to derive the astrometric fit using IRAF." (2.2 Hubble images)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Core radius of isothermal ellipsoid | 48 | +169/-28 | mas | 4 | $r_\mathrm{core} = 48 ^{+169}_{-28}$ mas |
| Velocity dispersion | 265 | +15/-4 | km/s | 4 | $\sigma_v = 265 ^{+15}_{-4}$ km s$^{-1}$ |
| Position angle of ellipsoid | 11 | 13 | deg | 4 | $\theta_e = 11 \pm 13 \ensuremath{^\circ}$ |
| Total magnification | ~22 | not stated | dimensionless | 4 | the total magnification factor is expected to be $\mu_\mathrm{g} \sim 22$ |
| Lens-model chi2 | 3.45 | not stated | dimensionless | 4 | ($\chi^2 = 3.45$) |
| Lower limit on BH mass (r_core=150 mas) | > 3e8 | not stated | Msun | 6 | the ALMA non-detection places a constraint to the black hole mass of $M_\mathrm{BH} > 3 \times 10^8\,M_{\Sol}$ |
| BH mass from M–sigma | 1e9 | 0.1e9 | Msun | 6 | $M_\mathrm{BH} = (1 \pm 0.1) \times 10^9$ $M_{\Sol}$ |
| Spectral index 1.0 mm to 20 cm | -0.64 | 0.01 | dimensionless | 1 | $\alpha = -0.64 \pm 0.01$ |

## Qualitative findings

- Lensed source consists of ~35 clumps of ≲100 pc in a ~2 kpc disk  
  > "The observed images are reproduced by 35 $\lesssim 100$-pc-sized knots embedded in an extended ($\simeq 2$ kpc) disk." (3.1 Methods and results)

## Claim tuples

- H: Is the inner 1 kpc of the lens dominated by luminous matter? | E: Compared lens-model convergence with HST stellar profile scaled by M/L=2 | R: Core radii consistent within 1σ and position angles consistent | F: Baryons dominate the inner 1 kpc | **supported**
- H: Is the central non-thermal source an AGN at the lens centre? | E: Compared mass centroid with the non-thermal source position | R: Offset within ≃30 mas | F: AGN sits at the potential bottom | **supported**
- H: Does the missing central image require a massive SMBH? | E: Added point mass and compared central image flux with ALMA upper limit | R: M_BH > 3e8 Msun | F: Consistent with M–sigma prediction | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Full-resolution images allow higher-order perturbations and robust identification of multiple features  
  > "we prefer to use the full resolution ALMA images (up to 23 mas), which allows us to (1) accurately model higher-order perturbations" (4 Discussions and conclusions)
- Alternative: Clumps not coherent among bands rejected as phase calibration artifacts  
  > "they are likely to be artifacts due to phase calibration residuals" (2.1 ALMA observations and images)
- How they decided it was enough: _not stated_
- Limitation (authors): Core radius and velocity dispersion highly degenerate; BH mass and core radius degenerate  
  > "Note that the core radius ($r_\mathrm{core}$) and velocity dispersion ($\sigma_v$) of the isothermal ellipsoid are highly degenerate." (3.1 Methods and results)
- Caveat (inferred, ours): Manual knot identification may bias the model
- Caveat (inferred, ours): Magnification uncertain and model-dependent
- Caveat (inferred, ours): Assumed M/L=2 drives the baryon-dominance conclusion
- Caveat (inferred, ours): Only ALMA derived products, no calibration description

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Data from Science Verification project 2011.0.00016.SV; GLAFIC model posted online  
  > "The GLAFIC model of SDP.81 is available at http://www.ioa.s.u-tokyo.ac.jp/%7Eytamura/SDP81/." (Footnote 4)
- Code: GLAFIC model files released online  
  > "The GLAFIC model of SDP.81 is available at http://www.ioa.s.u-tokyo.ac.jp/%7Eytamura/SDP81/." (Footnote 4)
- Missing: Calibrated ALMA images/CASA imaging parameters
- Missing: Knot catalog with positions
- Missing: MCMC configuration
- Data volume (inferred): Large (long-baseline SV data, hundreds of GB raw); the calibrated images are smaller
- Score (inferred): 3/5, Public SV data and GLAFIC model released, but imaging and knot selection are not documented here.
- Rediscovery candidate: no, Knot identification is manual and imaging details are deferred to other papers.

## Links

- Method: Oguri10 (GLAFIC lens modeling software)
- Method: Peng10 (GALFIT)
- Companion: Vlahkis15 (SV long-baseline observations of SDP.81)
- Companion: Fomalont15 (Long baseline campaign)
- Companion: Hatsukade15 (Paper II on source structure)
- Companion: Rybak15 (Independent lens model with ALMA)
- Companion: Wong15 (Independent lens model)
- Related: H-ATLAS
- Related: ALMA Science Verification long baseline campaign

## Checks

```json
{
 "quotes": 50,
 "quotes_ok": 50,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 36,
  "rate": 0.462
 },
 "evidence_ok": true
}
```

# ALMA Resolves the Properties of Star-forming Regions in a Dense Gas Disk at z ∼ 3

`2015ApJ...806L..17S` | The Astrophysical Journal Letters 2015 | first author: Swinbank, A. M. | arXiv: 1505.05148 | DOI: 10.1088/2041-8205/806/1/L17

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type archival_reuse

## Science

- Fields: high_z_galaxies, star_formation
- Question: Do star-forming regions in the dense gas disk of lensed galaxy SDP 81 follow local GMC scaling relations (Larson's relations), and what ISM pressure explains any offsets?  
  > "To test whether the scaling relations that govern the structure of local GMCs are valid in the dense and rapidly evolving ISM of high-redshift, gas-rich galaxies" (Introduction)
- Target **SDP 81 (H-ATLAS lensed SMG)**: coordinates _not stated_; z/distance z = 3.042 (lens at z ~ 0.299)  
  > "a star-forming galaxy at $z$ = 3.042 whose image has been gravitationally lensed by a factor 15.8 $\pm$ 0.7$\times$ by a massive, foreground ($z\sim$ 0.299) galaxy (cite: Dye15)" (Introduction); distance from Negrello10 (H-ATLAS identification); Negrello14 for the lens  
  > "a star-forming galaxy at $z$ = 3.042 whose image has been gravitationally lensed by a factor 15.8 $\pm$ 0.7$\times$ by a massive, foreground ($z\sim$ 0.299) galaxy (cite: Dye15)" (Introduction)

## Data provenance

- ALMA projects: 2011.0.00016.SV
- bands: Band 7 (1.0 mm) continuum; 12CO(5-4) and 2.1 mm continuum at lower frequency  
  > "the ALMA Band 7 (1.0 mm) continuum observations have a resolution of 31 $\times$ 23 mas and reach a 1-$\sigma$ depth of 11 $\mu$Jy / beam." (Observations and Source Plane Reconstruction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: long baseline configuration, up to 15 km  
  > "Observations of SDP 81 with ALMA in its long baseline configuration (up to 15 km) were taken in 2014 October." (Observations and Source Plane Reconstruction)
- baselines: _not stated_
- angular resolution: 31 x 23 mas (1.0 mm); 56 x 50 mas (2.1 mm / CO(5-4))  
  > "reaching a resolution of 56 $\times$ 50 mas." (Observations and Source Plane Reconstruction)
- max recoverable scale: _not stated_
- sensitivity: 1-sigma 11 uJy/beam at 1.0 mm  
  > "reach a 1-$\sigma$ depth of 11 $\mu$Jy / beam." (Observations and Source Plane Reconstruction)
- time on source: _not stated_
- observing dates: 2014 October  
  > "were taken in 2014 October." (Observations and Source Plane Reconstruction)
- pi or archival as stated: _not stated_
- Line: 12CO 5-4 (not stated)
- Other facility **HST**: JH-band imaging used in the lens model  
  > "using both the ALMA sub-mm and *Hubble Space Telescope; (HST)* imaging (cite: Rybak15)." (Observations and Source Plane Reconstruction)
- External data: Lens model, magnification, source-plane CO(5-4) velocity field, gas masses, CO(1-0)/CO(5-4) ratios  
  > "Using the lens modeling from (cite: Dye15), we reconstruct the source-plane morphology of SDP 81 at 1.0 mm and 2.1 mm" (Analysis & Discussion) [from (cite: Dye15)]
- External data: Stellar mass of SDP 81  
  > "M$_{\star}$ = (6.6$^{+2.6}_{-1.9}$) $\times$ 10$^{10}$ M$_{\odot}$ (cite: Negrello14)" (Analysis & Discussion) [from (cite: Negrello14)]
- External data: Local GMC comparison data  
  > "compiled from observations of the Milky-Way disk and other quiescent galaxies; (cite: Bolatto06)" (Analysis & Discussion) [from (cite: Bolatto06)]
- External data: SMM J2135-0102 clump properties  
  > "a star-forming galaxy at $z$ = 2.32 where similar measurements have been made (cite: Swinbank11)" (Analysis & Discussion) [from (cite: Swinbank11)]

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
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA observations and data reduction  
  > "These observations and reduction are described by (cite: Vlahakis15)." (Observations and Source Plane Reconstruction) [from (cite: Vlahakis15)]
- Lens model and source-plane reconstruction  
  > "Using the lens modeling from (cite: Dye15), we reconstruct the source-plane morphology" (Analysis & Discussion) [from (cite: Dye15)]
- Beam-corrected velocity dispersion map method  
  > "using the beam-corrected velocity dispersion map for the velocity dispersions; (cite: Davies11)" (Analysis & Discussion) [from (cite: Davies11)]
- Pressure-dependent Larson relations  
  > "Following (cite: Elmegreen89), the velocity-dispersion–size and mass-size relations can be cast as:" (Analysis & Discussion) [from (cite: Elmegreen89)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration/imaging details (deferred to Vlahakis15)
- Source-plane reconstruction code and lens model parameters
- Velocity dispersion map construction and clump sigma extraction details
- Local background definition for the 5-sigma clump criterion
- Gaussian fit procedure and PSF deconvolution for sizes
- Sigma_gas and the gas mass used in the Q and pressure calculations

## Analysis recipe

1. **Reconstruct source-plane images**: Use Dye15 lens model to reconstruct 1.0 mm and 2.1 mm morphology; measure source-plane PSF from beams reconstructed on a grid of image-plane positions  
  > "To measure the source-plane point spread function (PSF) we reconstruct the beam in a grid of positions in the image plane" (Analysis & Discussion)
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify star-forming clumps**: Select regions 5-sigma above local background in the 1.0 mm image; cross-check with clumpfind  
  > "we also use the clumpfind algorithm (cite: Williams94), which isolates clumps A–D, although misses clump E." (Analysis & Discussion)
   - software: clumpfind
   - fitting: _not stated_
   - validation: Conclusions do not change if clump E is excluded  
  > "none of our conclusions significantly change if we include / exclude region E from the analysis below." (Analysis & Discussion)
3. **Disk dynamics, Toomre Q and Jeans length**: Disk model of the CO(5-4) velocity field gives inclination and Mdyn; Q = sigma_r kappa / (pi G Sigma_gas); L_J = pi sigma_r^2 / 8 G Sigma_gas  
  > "L$_{\rm J}$ = $\pi\sigma_{\rm r}^2/8 G \Sigma_{\rm gas}$" (Analysis & Discussion)
   - parameter: kappa = a Vmax/R with a = sqrt3; sigma_r = 30–35 km/s; Sigma_gas = 4±1e9 Msun kpc^2  
  > "$\sigma_{\rm r}$ = 30–35 km s$^{-1}$ we estimate L$_{\rm J}$ = 130$_{-60}^{+200}$ pc." (Analysis & Discussion)
   - fitting: _not stated_
   - validation: _not stated_
4. **Clump sizes, dispersions and gas masses**: Gaussian fits to the sub-mm profile and a 5-sigma contour area for size, deconvolved for PSF; CO(5-4) luminosity with the r54 ratio for mass; compare with M_dyn = C sigma^2 R / G  
  > "M$_{\rm dyn}$ = $C\sigma^2$ R/$G$ with $C$ = 5 – as approriate for a uniform density sphere" (Analysis & Discussion)
   - fitting: _not stated_
   - validation: Mdyn/MCO = 1.5±0.5  
  > "M$_{\rm dyn}$ / M$_{\rm CO}$ = 1.5 $\pm$ 0.5)." (Analysis & Discussion)
5. **ISM pressure and comparison with Larson's relations**: Mid-plane hydrostatic pressure from gas and stellar surface densities; compare clump properties with GMCs using Elmegreen89 pressure-dependent relations  
  > "In a rotating gas disk, the mid-plane hydrostatic pressure is given by:" (Analysis & Discussion)
   - assumption: Mstar <~ 3e10 Msun upper limit; sigma_gas/sigma_star ~ 1 (varied 0.5–2)  
  > "We also assume that the velocity dispersion of the gas and stars are comparable, $\sigma_{\rm gas}$ / $\sigma_{\star}\sim$ 1" (Analysis & Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **clumpfind** : Independent identification of clumps  
  > "we also use the clumpfind algorithm (cite: Williams94)" (Analysis & Discussion)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Inclination-corrected rotation speed | 320 | 20 | km/s | 3 | $v_{\rm rot}$ = 320 $\pm$ 20 km s$^{-1}$ |
| Dynamical mass within 1.5 kpc | 3.5e10 | 1.0e10 | Msun | 3 | M$_{\rm dyn}$ = (3.5 $\pm$ 1.0) $\times$ 10$^{10}$ M$_{\odot}$ within a radius of 1.5 kpc |
| Toomre Q | 0.30 | 0.10 | dimensionless | 3 | $Q$ = 0.30 $\pm$ 0.10 |
| Jeans length | 130 | +200/-60 | pc | 3 | L$_{\rm J}$ = 130$_{-60}^{+200}$ pc |
| Disk inclination | 40 | 5 | deg | 3 | inclination of $\theta$ = 40 $\pm$ 5$^\circ$ |
| Clump FWHM sizes | 170–310 | not stated | pc | 4 | FWHM = 170–310 pc |
| Clump gas masses | 1–5e8 | not stated | Msun | 4 | M$_{\rm gas,clumps}$ = 1–5 $\times$ 10$^{8}$ M$_{\odot}$ |
| Mid-plane hydrostatic pressure P_tot/k_B | 40e7 | +30/-20 e7 | K cm^-3 | 5 | $40_{-20}^{+30}$ $\times$ 10$^{7}$ K cm$^{-3}$ |
| Source-plane PSF FWHM | ~60 | not stated | pc | 1 | the source-plane PSF has a FWHM $\sim$ 60 pc |

## Qualitative findings

- Clump velocity dispersions are ~4x larger than GMCs at fixed size and masses ~10x higher, similar to the Galactic Center and other extreme environments  
  > "appear to be $\sim$ 4$\times$ larger than those of GMCs in quiescent environments" (Analysis & Discussion)

## Claim tuples

- H: The SDP 81 gas disk is rotating and gravitationally unstable | E: Source-plane CO(5-4) kinematics and Toomre analysis | R: Q = 0.30±0.10, Mdyn = 3.5e10 Msun, vrot = 320 km/s | F: The disk is gas rich and unstable and fragments on a ~130 pc Jeans scale | **supported**
- H: Star-forming regions at z~3 follow local Larson relations | E: Measure size, line width and luminosity of five clumps and compare with GMC data | R: Dispersion ~4x higher, mass ~10x higher at fixed size | F: They are offset, plausibly due to high ISM pressure of ~1e4 times the Milky Way | **supported**

## Reasoning

- Why this data: Lensing plus long baselines give ~50–100 pc source-plane resolution needed to resolve GMC-scale regions  
  > "The combination of long-baselines, together with gravitational lensing means we are able to resolve the largest giant molecular clouds" (Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): The pressure estimate has considerable uncertainty  
  > "although we caution this value has considerable uncertainty" (Analysis & Discussion)
- Caveat (inferred, ours): Pressure offset prediction (10x) differs from the observed 4x
- Caveat (inferred, ours): Only five clumps, with one not recovered by clumpfind
- Caveat (inferred, ours): Lens-model systematics propagate into sizes and masses
- Caveat (inferred, ours): Stellar mass upper limit is ad hoc

## Reproducibility

- Data public (paper): Data from ALMA Science Verification program 2011.0.00016.SV  
  > "This paper uses data from ALMA program ADS/JAO.ALMA#2011.0.00016.SV." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Lens model and reconstruction code/parameters from Dye15
- Missing: Calibration and imaging details (in Vlahakis15)
- Missing: Clump measurement details
- Data volume (inferred): tens of GB (long-baseline SV data)
- Score (inferred): 3/5, Public data and clear formulas, but the lens model and processing are inherited and the clump measurement details are sparse.
- Rediscovery candidate: no, The recipe relies on external lens modelling and the clump extraction details are not given.

## Links

- Method: (cite: Vlahakis15) (ALMA observations and reduction)
- Method: (cite: Dye15) (Lens model and gas masses)
- Companion: (cite: Dye15) (Lens model and source properties)
- Related: ALMA Long Baseline Campaign / Science Verification
- Related: H-ATLAS

## Checks

```json
{
 "quotes": 46,
 "quotes_ok": 46,
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
  "facts": 72,
  "stated": 31,
  "rate": 0.431
 },
 "evidence_ok": true
}
```

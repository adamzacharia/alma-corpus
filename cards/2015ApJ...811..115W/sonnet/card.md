# The Innermost Mass Distribution of the Gravitational Lens SDP.81 from ALMA Observations

`2015ApJ...811..115W` | The Astrophysical Journal 2015 | first author: Wong, Kenneth C. | arXiv: 1503.05558 | DOI: 10.1088/0004-637X/811/2/115

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: Can the non-detection of the demagnified central image of lens SDP.81 in ALMA long-baseline CO maps constrain the lens galaxy's inner mass profile and SMBH mass?  
  > "We use the CO maps to determine the flux limit of the central image excluding the AGN continuum." (abstract)
- Target **SDP.81 (H-ATLAS J090311.6+003906)**: coordinates lens center 09:03:11.572 +00:39:06.54 (J2000)  
  > "SDP.81 is a massive elliptical galaxy at $z = 0.2999$ lensing a background dusty star-forming galaxy at $z = 3.042$ into four multiple images" (1 Introduction); z/distance lens z = 0.2999; source z = 3.042  
  > "SDP.81 is a massive elliptical galaxy at $z = 0.2999$ lensing a background dusty star-forming galaxy at $z = 3.042$ into four multiple images" (1 Introduction); distance from (cite: negrello2010; negrello2014)  
  > "SDP.81 is a massive elliptical galaxy at $z = 0.2999$ lensing a background dusty star-forming galaxy at $z = 3.042$ into four multiple images" (1 Introduction)

## Data provenance

- ALMA projects: 2011.0.00016.SV
- bands: Band 4 (151 GHz), Band 6 (236 GHz), Band 7 (290 GHz), 6+7 (268 GHz)  
  > "We use archival images of the CO lines and the Bands 4 (151 GHz) and 6+7 (268 GHz) continuum" (2.1 ALMA Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.13-0.20'' beams (e.g. 0.182''x0.143'' for CO 5-4) with 1000 kλ taper  
  > "$0.182\ensuremath{''} \times 0.143\ensuremath{''}, 57.3^{\circ}$ for CO $J$=5-4" (2.1 ALMA Data)
- max recoverable scale: _not stated_
- sensitivity: rms 0.0166 / 0.0194 / 0.0214 Jy/beam km/s for CO 5-4/8-7/10-9; 0.0115, 0.0200, 0.0193 mJy/beam for Bands 4/6/7  
  > "0.0166 Jy beam$^{-1}$ km s$^{-1}$ for CO $J$=5-4, 0.0194 Jy beam$^{-1}$ km s$^{-1}$ for CO $J$=8-7" (2.1 ALMA Data)
- time on source: _not stated_
- observing dates: October 2014, 2014 ALMA Long Baseline Campaign (Science Verification)  
  > "ALMA Science Verification observations of SDP.81 were taken in October 2014 as part of the 2014 ALMA Long Baseline Campaign." (2.1 ALMA Data)
- pi or archival as stated: _not stated_
- Line: CO J=5-4 (not stated)
- Line: CO J=8-7 (not stated)
- Line: CO J=10-9 (not stated)
- Other facility **HST WFC3**: Archival F110W and F160W imaging to model lens light and core radius  
  > "We use archival *Hubble Space Telescope* (*HST*) Wide Field Camera 3 (WFC3) imaging of SDP.81 to model the light distribution of the lens galaxy and constrain its core radius." (2.2 HST Data)
- External data: Priors on most lens mass parameters from HST/WFC3 lens model  
  > "The prior $Q(\boldsymbol{\eta})$ in equation ([\[eq:posterior\]](#eq:posterior)) on most of the parameters are taken from (cite: dye2014) based on the *HST*/WFC3 data" (3.3.1 Cored Elliptical Power-Law Model) [from (cite: dye2014)]
- External data: Gaussian prior on NFW scale radius  
  > "From the results of (cite: gavazzi2007), which are based on the Sloan Lens ACS Survey" (3.3.2 Composite Model) [from (cite: gavazzi2007)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Archival calibrated uv data and archival tapered images used  
  > "we created $1000 k\lambda uv$ tapered images from the archival calibrated $uv$ data in the same manner as the other $1000 k\lambda uv$ tapered images" (2.1 ALMA Data)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: 1000 kλ  
  > "CLEANed with the $1000 k\lambda uv$ tapering" (2.1 ALMA Data)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: CO maps are continuum-subtracted  
  > "The use of continuum-subtracted CO fluxes ensure that they originate from the lensed background source" (3.1 Constraints From the Multiple Images)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA observation details and the archival tapered images  
  > "Details of the observations are described in (cite: alma2015)." (2.1 ALMA Data) [from (cite: alma2015)]
- Lens model priors from HST  
  > "are taken from (cite: dye2014) based on the *HST*/WFC3 data" (3.3.1 Cored Elliptical Power-Law Model) [from (cite: dye2014)]

### Not stated but needed to reproduce (our reading)

- CLEAN parameters (weighting, robust, deconvolver, mask) for archival images
- CO line velocity ranges and line-free channels for continuum subtraction
- Exact archival image products used
- Glee code availability and MCMC sampler details/burn-in
- Rest frequencies of lines
- How the E region and flux-extraction apertures were defined

## Analysis recipe

1. **Measure image fluxes and flux limit of central image**: Fluxes in regions A-E from CO and continuum maps; uncertainty is rms times sqrt(number of beams)  
  > "Uncertainties on the fluxes in these regions are the background rms multiplied by the square root of the number of beams in the region." (3.1 Constraints From the Multiple Images)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit lens light to HST**: Two cored elliptical power-law profiles with shared centroid fit to 87x87 pixel region excluding lensed images; with and without point source  
  > "We fit the lens light with the sum of two cored elliptical power-law profiles" (3.2 Light Fitting to HST Data)
   - software: Glee, DrizzlePac
   - fitting: Chi-square fits  
  > "The double power-law plus point source fit has $\chi^{2} \approx 1500$ in F110W and $\chi^{2} \approx 2300$ in F160W" (Light Fitting to HST Data)
   - validation: Compared with Sersic and double Sersic fits and both bands  
  > "We test a Sérsic profile fit, but find that it is disfavored in the fitting region" (3.2 Light Fitting to HST Data)
3. **Fit lens mass models to image positions**: Cored power-law (R_core 0.08'' or 0.15'' priors) and composite stellar+NFW models, plus SMBH point mass and external shear, using positions of three source features  
  > "We try two models for the mass distribution of the lens galaxy: a cored elliptical power-law mass distribution, and a composite model with separate stellar and dark matter components." (3.3 Lens Mass Modeling)
   - software: Glee
   - parameter: MCMC chain length 5x10^5  
  > "we first sample $L_{\rm pos}\times Q$ via MCMC of chain length $5\times10^5$, and then weight these samples by $L_{\rm flux}$" (3.3 Lens Mass Modeling)
   - assumption: SMBH at mass centroid; uniform prior on log M_BH [6.5, 9.5]  
  > "We assume that the SMBH is located at the center of the mass distribution and adopt a uniform prior on its logarithmic mass" (3.3.1 Cored Elliptical Power-Law Model)
   - fitting: MCMC, position likelihood Gaussian  
  > "In practice, we first sample $L_{\rm pos}\times Q$ via MCMC of chain length $5\times10^5$, and then weight these samples by $L_{\rm flux}$." (Lens Mass Modeling)
   - validation: rms image offset ~0.015'' for power-law models  
  > "we can reproduce the observed image positions with an rms offset between the observed and predicted image positions of $\sim 0.015\ensuremath{''}$" (4.1 Lens Modeling Results)
4. **Constrain SMBH mass from central image non-detection**: Weight samples by Gaussian non-detection likelihood on predicted flux of E = flux of D times mu_E/mu_D, for CO 5-4, 8-7, 10-9; mu ratio from mock three-clump source  
  > "predicted flux density of image E that is obtained by multiplying the observed integrated flux density of image D with the modeled magnification ratio $\mu_{E}/\mu_{D}$" (3.3 Lens Mass Modeling)
   - software: Glee
   - fitting: _not stated_
   - validation: Results unaffected by 30-40% source size uncertainty and by satellite galaxy  
  > "Additional tests show that our results are unaffected by moderate ($\sim 30-40$%) uncertainties in the assumed source sizes." (3.3 Lens Mass Modeling)

## Software

- **Glee** : Lens modeling  
  > "Our lens modeling is performed with Glee, a software developed by S. H. Suyu and A. Halkola" (3 Lens Modeling)
- **DrizzlePac** : HST data reduction  
  > "The data are reduced using DrizzlePac (cite: gonzaga2012)" (2.2 HST Data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Core radius w1 (two power-law) | 0.08 | 0.01 | arcsec | 2 | We constrain $w_1$ to be $0.08 \pm 0.01\ensuremath{''}$ ($\approx 356$ pc) for the two power-law model |
| Core radius w1 (with point source) | 0.15 | 0.01 | arcsec | 2 | $0.15 \pm 0.01\ensuremath{''}$ ($\approx 668$ pc) for the two power-law model plus a point source |
| Stellar M/L | 1.1 | +0.1/-0.1 | Msun/Lsun | 3 | The predicted stellar mass-to-light (M/L) ratio is $1.1^{+0.1}_{-0.1}~\mathrm{M}_{\odot}~\mathrm{L}_{\odot}^{-1}$ |
| log(M_BH/Msun) preferred (R_core=0.15'') | >~8.5 | not stated | dex | 4 | a black hole mass of $\mathrm{\log(M_{BH}/M_{\odot})} \gtrsim 8.5$ is preferred |
| Dark matter fraction within Einstein radius | ~50 | not stated | percent | 3 | The dark matter fraction within the Einstein radius is $\sim50$% |

## Qualitative findings

- Central compact emission has flat SED, so it is AGN emission rather than central image; no central image in any CO line  
  > "Its flat SED (see Section [3](#sec:model)) indicates that it is not the central image, but rather low-level AGN emission from the lens galaxy" (2.1 ALMA Data)

## Claim tuples

- H: Does the CO non-detection of the central image constrain SMBH mass? | E: Lens models weighted by non-detection likelihood | R: Only the R_core=0.15'' power-law model gives a sharp rise at log M_BH ~8.5; others unconstrained | F: M_BH >~ 10^8.5 Msun preferred for large-core model | **partially**
- H: Can deeper observations improve constraints? | E: Hypothetical 3x higher S/N | R: Constraints strengthen | F: Deeper observations would help | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: CO fluxes chosen since continuum-subtracted so free of lens-galaxy AGN contamination  
  > "We use the CO flux densities because there is no contamination from the AGN of the lens galaxy after the continuum subtraction." (3.3 Lens Mass Modeling)
- Alternative: Sérsic fit disfavored; two power-law preferred  
  > "We prefer the two power-law model, as it is easier to determine a core radius ($w_{1}$)" (3.2 Light Fitting to HST Data)
- How they decided it was enough: _not stated_
- Limitation (authors): Fluxes of A, B, C not used owing to differential magnification (~30-50%)  
  > "we do not use the fluxes of these images as constraints due to the high uncertainty from differential magnification" (3.1 Constraints From the Multiple Images)
- Caveat (inferred, ours): Result depends strongly on the assumed R_core prior
- Caveat (inferred, ours): Only three source features used; flux-based inference relies on image D alone
- Caveat (inferred, ours): Archival tapered images with unspecified imaging parameters

## Reproducibility

- Data public (paper): Archival ALMA SV and HST data  
  > "We use archival images of the CO lines" (2.1 ALMA Data)
- Products in archive: _not stated_
- Missing: Glee code availability
- Missing: CLEAN parameters
- Missing: Exact aperture definitions
- Data volume (inferred): ~tens of GB (ALMA SV long-baseline) plus small HST images
- Score (inferred): 3/5, Public data and clear likelihood, but proprietary-ish Glee code and missing imaging details.
- Rediscovery candidate: no, Requires Glee lens modeling code not stated as available.

## Links

- Method: (cite: suyu2010; suyu2012) (Glee lens modeling code)
- Companion: (cite: alma2015) (ALMA SV observations of SDP.81)
- Companion: (cite: rybak2015) (Independent visibility-space lens model)
- Companion: (cite: tamura2015) (Independent analysis of SDP.81)
- Related: 2014 ALMA Long Baseline Campaign
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
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 34,
  "rate": 0.507
 },
 "evidence_ok": true
}
```

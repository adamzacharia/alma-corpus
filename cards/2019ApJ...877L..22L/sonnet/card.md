# The Anomalously Low (Sub)Millimeter Spectral Indices of Some Protoplanetary Disks May Be Explained By Dust Self-scattering

`2019ApJ...877L..22L` | The Astrophysical Journal Letters 2019 | first author: Liu, Hauyu Baobab | arXiv: 1904.00333 | DOI: 10.3847/2041-8213/ab1f8e

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: Can dust self-scattering with high, wavelength-increasing albedo explain anomalously low (<2.0) mm spectral indices in the inner TW Hya disk, and what maximum grain sizes does it imply?  
  > "if the albedo is high and is increasing with frequency, it is possible to reproduce such anomalously low spectral indices when the emission source is optically thick." (abstract)
- Target **TW Hya**: coordinates _not stated_; z/distance 0.085 arcsec ~ 5.1 AU (about 60 pc implied)  
  > "along the major axis (P.A.=155$^{\circ}$, see (cite: Qi2004ApJ; Andrews2012ApJ)) of TW Hya" (2.1 Millimeter spectral index from TW Hya); "0$''$.085 ($\sim$5.1 AU) circular beams" (4 Reproducing ALMA measurements); distance from Gaia mentioned (Gaia2016, Gaia2018); not explicit  
  > "along the major axis (P.A.=155$^{\circ}$, see (cite: Qi2004ApJ; Andrews2012ApJ)) of TW Hya" (2.1 Millimeter spectral index from TW Hya); "0$''$.085 ($\sim$5.1 AU) circular beams" (4 Reproducing ALMA measurements)

## Data provenance

- ALMA projects: 2015.A.00005.S, 2013.1.00114.S
- bands: Band 4 (~145 GHz) and Band 6 (~233 GHz)  
  > "The ALMA Band 4 ($\sim$145 GHz) and Band 6 ($\sim$233 GHz) data" (2.1 Millimeter spectral index from TW Hya)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Band 6 0.075x0.064 arcsec; Band 4 0.081x0.058 arcsec; smoothed to 0.085 arcsec  
  > "the Band 4 image achieved a $\theta_{\mbox{\scriptsize maj}}\times\theta_{\mbox{\scriptsize min}}$$=$0$''$.081$\times$0$''$.058 synthesized beam" (4 Reproducing ALMA measurements)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival; PIs Tsukagoshi (2015.A.00005.S) and Öberg (2013.1.00114.S)  
  > "The archival ALMA Band 4 and 6 data were re-calibrated and phase self-calibrated" (4 Reproducing ALMA measurements)
- Other facility **Gaia**: Distance to TW Hya (cited)  
  > "protoplanetary disk, TW Hya (cite: Gaia2016A&A; Gaia2018A&A)" (Introduction)
- External data: DSHARP dust optical constants and thin-slab analytic radiative transfer solution  
  > "This work adopted the default DSHARP dust optical constants published in (cite: Birnstiel2018)" (2.2 Estimating maximum grain sizes) [from (cite: Birnstiel2018)]
- External data: Midplane dust temperature models 22 K and 28 K x (R/10 AU)^-0.4  
  > "the $T_{\mbox{\scriptsize dust}}(R)$=22 \[K\]$\times$(R/10 \[AU\])$^{-0.4}$ and 28 \[K\]$\times$(R/10 \[AU\])$^{-0.4}$ midplane dust temperature profile models" (2.2 Estimating maximum grain sizes) [from (cite: Andrews2012ApJ; Andrews2016ApJ)]

## Processing

### Calibration

- pipeline or manual: Re-calibrated and phase self-calibrated following Tsukagoshi et al. 2016 Section 2  
  > "re-calibrated and phase self-calibrated following the strategy outlined in Section 2 of (cite: Tsukagoshi2016)" (4 Reproducing ALMA measurements)
- casa version: CASA v5.4.0  
  > "using the CASA software package v5.4.0 (cite: McMullin2007)" (4 Reproducing ALMA measurements)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: phase self-calibration  
  > "re-calibrated and phase self-calibrated" (4 Reproducing ALMA measurements)

### Imaging

- task: _not stated_
- deconvolver: MFS with nterm=1, no multiscale clean; bands imaged separately  
  > "this work employed *nterm*=1 in MFS and did not employ multiscale clean" (4 Reproducing ALMA measurements)
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: CASA uvcontsub  
  > "The continuum data were derived using the CASA-`uvcontsub` task." (4 Reproducing ALMA measurements)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Smoothed to 0.085 arcsec (~5.1 AU) circular beams  
  > "these images were smoothed to have 0$''$.085 ($\sim$5.1 AU) circular beams" (4 Reproducing ALMA measurements)
- final beam: _not stated_
- final rms: Band 6 23 uJy/beam; Band 4 14 uJy/beam  
  > "a 23 $\mu$Jy beam$^{-1}$ root-mean-square (RMS) noise level" (4 Reproducing ALMA measurements)

### Inherited from earlier work

- Calibration and self-calibration strategy  
  > "following the strategy outlined in Section 2 of (cite: Tsukagoshi2016)" (4 Reproducing ALMA measurements) [from (cite: Tsukagoshi2016)]
- Dust temperature profile models shown for comparison  
  > "Following (cite: Tsukagoshi2016), the top panel of Figure [1](#fig:profiles) also presents" (2.2 Estimating maximum grain sizes) [from (cite: Tsukagoshi2016)]

### Not stated but needed to reproduce (our reading)

- Weighting/robust, cell and image size, masks, clean threshold
- Line-free channels and self-cal solints
- Flux calibrators and flux scale uncertainty
- Uncertainties on Tbr and alpha profiles and whether uv ranges were matched
- MCMC likelihood form and error model
- Adopted distance to TW Hya
- Dust composition fractions in DSHARP opacities
- Number of RADMC-3D photons and grid size

## Analysis recipe

1. **Reproduce Band 4/6 continuum images**: Recalibrate, self-calibrate, uvcontsub, MFS imaging per band, smooth to common beam  
  > "The Band 4 and Band 6 continuum data were imaged separately, using the multi-frequency synthesis (MFS) method." (4 Reproducing ALMA measurements)
   - software: CASA
   - parameter: nterm=1; no multiscale; common 0.085 arcsec beam  
  > "this work employed *nterm*=1 in MFS and did not employ multiscale clean" (4 Reproducing ALMA measurements)
   - fitting: _not stated_
   - validation: Compared with Tsukagoshi et al. 2016 profiles; low alpha reproduced  
  > "The anomalously low (i.e., $<$2.0) $\alpha$ values were reproduced in the inner $\sim$10 AU radii." (2.1 Millimeter spectral index from TW Hya)
2. **Extract Tbr and alpha profiles along the major axis**: Thin slice along major axis P.A.=155 deg, no azimuthal averaging  
  > "this work did not perform azimuthal averaging to avoid smearing the weakly resolved azimuthal asymmetry" (2.1 Millimeter spectral index from TW Hya)
   - fitting: _not stated_
   - validation: _not stated_
3. **Compute dust opacities**: Mie theory with Henyey-Greenstein, DSHARP constants, size-averaged kappa_abs and effective kappa_sca  
  > "the Mie theory and the Henyey-Greenstein scattering approximation" (2.2 Estimating maximum grain sizes)
   - parameter: q=3.5, amin=1e-4 mm, amax variable  
  > "a power-law grain size distribution with a power-law index $q=$3.5, a minimum grain size $a_{\mbox{\scriptsize min}}=$10$^{-4}$ mm" (2.2 Estimating maximum grain sizes)
   - assumption: Spherical compact grains; no ice-free opacity  
  > "evaluated based on an assumption of spherical compact grains" (2.2 Estimating maximum grain sizes)
   - fitting: _not stated_
   - validation: Qualitatively similar to Kataoka et al. 2015  
  > "which appears qualitatively similar to what was presented in the independent work of (cite: Kataoka2015ApJ)" (2.2 Estimating maximum grain sizes)
4. **Fit Tdust and amax per offset with MCMC**: Fit Tbr profiles with optically thick isothermal face-on thin slab model of Birnstiel+2018  
  > "optically thick ($\tau\gg$1), isothermal and face-on thin dust slab model adopted here" (2.2 Estimating maximum grain sizes)
   - software: emcee
   - parameter: 100 walkers, 500 steps, first 100 discarded, start Tdust=20 K, amax=0.1 mm  
  > "The walkers were iterated with 500 steps assuming flat priors; in the end, the results from the first 100 steps were discarded." (2.2 Estimating maximum grain sizes)
   - assumption: Flat priors; optically thick slab  
  > "The walkers were iterated with 500 steps assuming flat priors" (2.2 Estimating maximum grain sizes)
   - fitting: MCMC with flat priors; converged within offsets [-10,10] AU except center  
  > "These fittings achieved good convergence in the offset range of \[-10, 10\] AU except at the central location" (2.2 Estimating maximum grain sizes)
   - validation: Corner plot at 4.1 AU offset  
  > "Figure [4](#fig:corner) shows the corner plot produced from the MCMC fittings at the 4.1 AU offset as an example of the convergence." (2.2 Estimating maximum grain sizes)
5. **Test thin-slab approximation with 3D radiative transfer**: RADMC-3D disk models with and without scattering at 232.990 and 144.988 GHz, pole-on  
  > "we derived the pole-on view of the disk at 232.990 GHz and 144.988 GHz" (2.2 Estimating maximum grain sizes)
   - software: RADMC-3D
   - parameter: Sigma_g=4e3 (r/AU)^-0.5; h=0.05 r^1.1; dust-to-gas 0.01; amax=0.1 mm; T=50 K (r/10AU)^-0.4; cavity inside 1 AU; inner 3.2 AU masked  
  > "We assumed a constant 0.01 dust-to-gas mass ratio, and assumed a constant $a_{\mbox{\scriptsize max}}$ $=$0.1 mm." (2.2 Estimating maximum grain sizes)
   - assumption: Imposed temperature profile rather than computed  
  > "instead of evaluating dust temperature based on radiative transfer, we used the assumed radial temperature profile" (2.2 Estimating maximum grain sizes)
   - fitting: _not stated_
   - validation: With scattering alpha converges below 2.0; without, to 2.0  
  > "in the case without switching on scattering, $\alpha$ converges to 2.0 in the innermost, high optical depth region" (2.2 Estimating maximum grain sizes)

## Software

- **CASA** 5.4.0: Recalibration, self-calibration, uvcontsub, imaging  
  > "using the CASA software package v5.4.0 (cite: McMullin2007)" (4 Reproducing ALMA measurements)
- **emcee** : MCMC fitting of Tdust and amax  
  > "emcee (cite: Foreman-Mackey2013PASP)" (Software)
- **RADMC-3D** : 3D radiative transfer tests with/without scattering  
  > "carried out simple three dimensional radiative transfer simulations using the RADMC-3D code" (2.2 Estimating maximum grain sizes)
- **Numpy** : listed in software section  
  > "Numpy (cite: VanDerWalt2011)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Derived amax range | decreases from ~100 um to ~20 um with radius | systematic, not quantified | um | 4 | Values of the derived $a_{\mbox{\scriptsize max}}$ radially decrease from $\sim$100 $\mu$m to $\sim$20 $\mu$m. |
| Band 6 synthesized beam and rms | 0.075x0.064 arcsec, 23 uJy/beam | not stated | arcsec; uJy/beam | 1 | a 23 $\mu$Jy beam$^{-1}$ root-mean-square (RMS) noise level |
| Band 4 synthesized beam and rms | 0.081x0.058 arcsec, 14 uJy/beam | not stated | arcsec; uJy/beam | 1 | a 14 $\mu$Jy beam$^{-1}$ RMS noise level |
| Numerical error on alpha in RADMC-3D images inside ~3 AU | ~±0.02 | not stated | dimensionless | 5 | which can lead to $\sim\pm$0.02 errors of the derived spectral indices |

## Qualitative findings

- Fitted Tdust is radially decreasing and everywhere higher than observed Tbr  
  > "Results from the MCMC fittings show radially decreasing $T_{\mbox{\scriptsize dust}}$, which is everywhere higher than the observed $T_{\mbox{\scriptsize br}}$" (2.2 Estimating maximum grain sizes)

## Claim tuples

- H: Dust scattering can produce alpha<2 in optically thick emission | E: Analytic slab SEDs for varying amax and 3D RADMC-3D models with/without scattering | R: alpha<2 reproduced for amax~0.1 mm; alpha converges to 2.0 without scattering | F: Self-scattering can explain anomalously low alpha | **supported**
- H: Scattering-based amax in TW Hya is consistent with polarimetric amax | E: MCMC fit of Tbr profiles | R: amax ~20-100 um | F: No tension with polarimetry-derived sizes | **supported**

## Reasoning

- Why this data: Bands 4 and 6 have high optical depth and are both in the Rayleigh-Jeans limit  
  > "These two bands are ideal for the present science purpose due to the sufficiently high dust optical depths" (2.1 Millimeter spectral index from TW Hya)
- Why this method: _not stated_
- Alternative: Foreground obscured hot dust and free-free emission rejected for face-on Class II disks  
  > "the explanation of foreground obscured hot dust cannot be applied to the Class II protoplanetary disks which are observed in face-on projection" (Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Dominant errors are systematic from opacity uncertainties and not assessed; poor MCMC convergence outside ±10 AU and at center  
  > "The dominant errors of the derived $T_{\mbox{\scriptsize dust}}$ and $a_{\mbox{\scriptsize max}}$ are systematic" (2.2 Estimating maximum grain sizes)
- Caveat (inferred, ours): No uncertainties on Tbr/alpha and no absolute flux-scale error budget
- Caveat (inferred, ours): Single object; thin isothermal slab simplification
- Caveat (inferred, ours): Opacity model dependence not explored
- Caveat (inferred, ours): Degeneracy of Tdust and amax not quantified

## Reproducibility

- Data public (paper): Archival ALMA projects used  
  > "The archival ALMA Band 4 and 6 data were re-calibrated" (4 Reproducing ALMA measurements)
- Products in archive: _not stated_
- Missing: Imaging parameters (weighting, masks, cell size)
- Missing: Calibration details deferred to Tsukagoshi+2016
- Missing: MCMC likelihood and uncertainties
- Missing: RADMC-3D setup details
- Data volume (inferred): ~50-100 GB raw for the two projects
- Score (inferred): 5/5, Public data and software named, but imaging and fitting details are sparse and calibration is deferred to another paper.
- Rediscovery candidate: no, Recipe is incomplete (imaging and likelihood details missing) and results are mostly profiles without tabulated numbers.

## Links

- Method: (cite: Birnstiel2018) (Opacities and analytic thin-slab scattering solution)
- Method: (cite: Tsukagoshi2016) (Calibration strategy and original TW Hya alpha profile)
- Companion: (cite: Huang2018) (Independent TW Hya low alpha measurement)
- Companion: (cite: Dent2019) (Low alpha in HD 163296)
- Related: DSHARP

## Checks

```json
{
 "quotes": 55,
 "quotes_ok": 55,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2012.1.00422.S",
  "2015.1.00005.S"
 ],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 44,
  "rate": 0.571
 },
 "evidence_ok": true
}
```

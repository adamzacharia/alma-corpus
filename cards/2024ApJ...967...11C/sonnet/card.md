# TEMPLATES: Characterization of a Merger in the Dusty Lensing SPT0418─47 System

`2024ApJ...967...11C` | The Astrophysical Journal 2024 | first author: Cathey, Jared | arXiv: 2307.10115 | DOI: 10.3847/1538-4357/ad33c9

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: Is the lensed dusty galaxy SPT0418-47 isolated or interacting with a companion, and how do the stellar masses and star formation of the two galaxies compare to the main sequence?  
  > "We combine JWST imaging and ALMA \[C II\] data and investigate the environment of this system to discern whether this system is isolated or is dynamically interacting." (Introduction)
- Target **SPT0418-47**: coordinates _not stated_; z/distance z = 4.225 (lensed by a foreground elliptical at z = 0.263)  
  > "a strongly-lensed, dusty star-forming galaxy at redshift $z=4.225$ and an associated multiply-imaged companion" (abstract); "Originally discovered as a submillimeter source by the South Pole Telescope (cite: vieira2013Natur.495..344V)" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.01374.S, 2016.1.01499.S
- bands: _not stated_
- frequencies and spectral setup: [CII] centered in the upper sideband; lower sideband gives continuum  
  > "centering the \[C II\] line in the upper sideband, while the lower sideband provides continuum data" (2.2 ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: individual blocks 0.02-0.15 arcsec; final beam 93 mas x 97 mas with 50 mas taper  
  > "The final synthesized beam size was 93 mas $\times$ 97 mas" (2.2 ALMA); "span a wide range in spatial resolution from 0.02$^{\prime\prime}$ to 0.15$^{\prime\prime}$" (2.2 ALMA)
- max recoverable scale: _not stated_
- sensitivity: 0.20 mJy/beam in 50 km/s channels of the [CII] cube  
  > "reaching a sensitivity of 0.20 mJy/beam in 50 $\rm{km\,s}^{-1}$ channels of the \[C II\] cube" (2.2 ALMA)
- time on source: 4.9 hours total between both projects  
  > "The total on-source time between both projects was 4.9 hours." (2.2 ALMA)
- observing dates: _not stated_
- pi or archival as stated: Projects with PIs Hezaveh and Litke  
  > "projects 2016.1.01374.S (PI: Hezaveh) and 2016.1.01499.S (PI: Litke)" (2.2 ALMA)
- Line: [C II] 158 micron fine-structure line (not stated)
- Other facility **JWST NIRCam and MIRI**: Imaging 1.15-21 micron (F115W-F2100W) for stellar light, lens and SED modeling  
  > "Imaging was taken with filters spanning wavelengths from 1.15 $\mu$m to 21 $\mu$m" (2.1 JWST)
- External data: 100 micron-3 mm FIR/submm photometry (SPT, LABOCA, Herschel, ALMA) used in SED fits  
  > "also provides 100 $\mu$m $-$ 3 mm SPT, LABOCA, Herschel/SPIRE, ALMA, and Herschel/PACS data for SPT0418$-$47." (4.2 Stellar Mass Ratios) [from Reuter et al. 2020 (cite: reuter2020ApJ...902...78R)]

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

- task: tclean in CASA, joint imaging of both projects  
  > "We jointly imaged the data (accounting for the different phase centers and frequency setups of the two projects) using `tclean` in the CASA software package" (2.2 ALMA)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: 50 mas external taper  
  > "applying a 50 mas external taper in the $uv$-plane" (2.2 ALMA)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uv-plane, linear frequency dependence, excluding frequencies with significant [CII] emission  
  > "We performed a continuum subtraction in the $uv$ plane assuming a linear frequency dependence of the continuum emission" (2.2 ALMA)
- line free channels: _not stated_
- primary beam correction: applied at the position of the lens  
  > "after correcting for the primary beam response at the position of the lens" (2.2 ALMA)
- array combination: _not stated_
- smoothing: 50 km/s spectral resolution for the line cube  
  > "with a spectral resolution of 50 $\rm{km\,s}^{-1}$" (2.2 ALMA)
- final beam: 93 mas x 97 mas  
  > "The final synthesized beam size was 93 mas $\times$ 97 mas" (2.2 ALMA)
- final rms: 0.20 mJy/beam per 50 km/s channel  
  > "reaching a sensitivity of 0.20 mJy/beam in 50 $\rm{km\,s}^{-1}$ channels" (2.2 ALMA)

### Inherited from earlier work

- Full JWST data reduction described in a separate paper  
  > "Rigby et al. 2023 (in prep) describes in detail the data reduction process for TEMPLATES." (2.1 JWST) [from Rigby et al. 2023 (in prep)]
- Metallicity prior for SPT0418B from NIRSpec analysis  
  > "based upon the NIRSpec analysis of Birkin et al. (in prep)" (4.2 Stellar Mass Ratios) [from Birkin et al. (in prep)]

### Not stated but needed to reproduce (our reading)

- tclean parameters: weighting/robust, deconvolver, cell and image size, masks, niter/threshold
- line-free channel ranges for continuum subtraction
- CASA version and calibration/self-calibration details of the ALMA data
- how the [CII] velocity offset (-56 km/s) was measured
- the 96% flux fraction method for SPT0418A
- SED fitting priors beyond metallicity, burst parameters and photometric apertures

## Analysis recipe

1. **Subtract the foreground lens light**: Fit Sersic bulge plus exponential disk in F150W, then fit other bands with fixed shape parameters  
  > "We use GALFIT (cite: peng2002AJ....124..266P; peng2010AJ....139.2097P) to fit a Sérsic bulge to the foreground lens at the wavelength of the F150W bandpass" (3.1 The Multiply-Imaged Companion)
   - software: GALFIT, WebbPSF
   - fitting: _not stated_
   - validation: _not stated_
2. **Source plane reconstruction and lens model**: SIE plus external shear, Sersic source, multi-band fit in F277W-F770W, with shapelets added  
  > "we use a Singular Isothermal Ellipsoid (SIE) with external shear." (4.1 Source Plane Reconstruction and Kinematics)
   - software: lenstronomy, emcee
   - fitting: Particle Swarm Optimization pre-sampling, then emcee MCMC run to convergence  
  > "We then use this approximate solution to seed the Markov Chain Monte Carlo (MCMC) sampler `emcee`" (4.1 Source Plane Reconstruction and Kinematics)
   - validation: Cross-check with backwards ray tracing of F277W, F356W, F444W using the lens model  
  > "This approach provides an alternative to the joint parametric - shapelet fitting" (4.1 Source Plane Reconstruction and Kinematics)
3. **Derive magnifications and photometry**: Magnifications from 100 random MCMC draws; fixed-aperture photometry  
  > "The uncertainties on the magnifications are derived from 100 random draws of the MCMC" (4.2 Stellar Mass Ratios)
   - fitting: _not stated_
   - validation: _not stated_
4. **SED fitting for stellar masses and SFRs**: cigale (parametric exponential SFH plus burst, Bruzual & Charlot) and prospector (non-parametric SFH, FSPS), Chabrier IMF  
  > "We use both cigale (cite: boquien2019A&A...622A.103B) and prospector (cite: johnson2021ApJS..254...22J) to fit the SEDs." (4.2 Stellar Mass Ratios)
   - software: cigale, prospector, FSPS
   - parameter: Metallicity for SPT0418A between 80% and 125% of solar  
  > "we apply a prior that the metallicity must be between 80% and 125% of solar" (4.2 Stellar Mass Ratios)
   - assumption: Chabrier IMF  
  > "For both codes we assume a Chabrier IMF" (4.2 Stellar Mass Ratios)
   - fitting: Dirichlet prior on mass per time bin in prospector; min chi2 model for cigale  
  > "we allow a non-parametric SFH with a Dirichlet prior on the mass formed per time bin" (4.2 Stellar Mass Ratios)
   - validation: Consistent results when the SFH is required to be the same in both codes  
  > "We verified that if we require the SFH to be the same in both codes, then the two codes give consistent results." (4.2 Stellar Mass Ratios)

## Software

- **CASA** : tclean imaging of ALMA data  
  > "using `tclean` in the CASA software package" (2.2 ALMA)
- **GALFIT** : foreground lens light subtraction  
  > "We use GALFIT" (3.1 The Multiply-Imaged Companion)
- **lenstronomy** : lens modeling and source reconstruction  
  > "We perform source plane reconstruction using LENSTRONOMY" (4.1 Source Plane Reconstruction and Kinematics)
- **emcee** : MCMC sampling of lens model  
  > "seed the Markov Chain Monte Carlo (MCMC) sampler `emcee`" (4.1 Source Plane Reconstruction and Kinematics)
- **cigale** : SED fitting and photometric redshifts  
  > "We use both cigale" (4.2 Stellar Mass Ratios)
- **prospector** : SED fitting  
  > "and prospector (cite: johnson2021ApJS..254...22J) to fit the SEDs" (4.2 Stellar Mass Ratios)
- **WebbPSF** 1.0.1.dev126+g6d83a9d: simulated PSFs for JWST filters  
  > "generated a simulated point spread function (PSF) for each filter for the date of observation using WebbPSF version 1.0.1.dev126+g6d83a9d" (2.1 JWST)
- **JWST pipeline** 1.8.2 (NIRCam), 1.9.5dev (MIRI): JWST image reduction  
  > "run through the JWST pipeline (Version 1.8.2)" (2.1 JWST)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Projected physical separation of SPT0418A and B | 4.42 | 0.05 | kpc | 2 | the projected physical separation between the centers of the two galaxies is $4.42\pm 0.05$ kpc |
| Total magnification SPT0418A | 29.5 | 1.2 | dimensionless | 3 | $\mu=29.5\pm1.2$ and $\mu=4.2\pm 0.9$ for SPT0418A and SPT0418B |
| Total magnification SPT0418B | 4.2 | 0.9 | dimensionless | 3 | $\mu=29.5\pm1.2$ and $\mu=4.2\pm 0.9$ for SPT0418A and SPT0418B |
| Stellar mass ratio A/B (cigale) | 4.5 | 1.0 | dimensionless | 4 | $4.5\pm 1.0$ for cigale and $4.2^{+1.9}_{-1.6}$ for prospector |
| Stellar mass ratio A/B (prospector) | 4.2 | +1.9/-1.6 | dimensionless | 4 | $4.5\pm 1.0$ for cigale and $4.2^{+1.9}_{-1.6}$ for prospector |
| Mean [CII] velocity of SPT0418B images relative to A | -56 | not stated | km/s | 0 | Both images of SPT0418B have consistent mean relative velocities of approximately $-56$ km s$^{-1}$. |
| SPT0418A stellar mass (prospector, magnification corrected) | 3.4e10 | +1.4/-1.4e10 | Msun | 4 | $M_\star=3.4^{+1.4}_{-1.4}\times10^{10}$ M$_\odot$ from prospector, or $M_\star=1.5\pm0.6\times10^{10}$ M$_\odot$ from cigale |
| Fraction of FIR flux in SPT0418A | 96 | 2 | % | 3 | we measure that $96\pm 2$% of the flux is associated with SPT0418A |

## Qualitative findings

- Extended structure near SPT0418A is suggestive of a tidal feature  
  > "extended structure associated with SPT0418A in the lensing reconstruction that is suggestive of a tidal feature" (abstract)
- Both galaxies are consistent with the main sequence, so the merger has not elevated star formation  
  > "this ongoing interaction has not noticeably elevated the star formation levels" (abstract)

## Claim tuples

- H: SPT0418B is physically associated with SPT0418A and the system is a merger | E: ALMA [CII] at the companion positions plus a lens model source reconstruction | R: [CII] at about -56 km/s; 4.42 kpc projected separation | F: SPT0418B lies at the same redshift, forming an ongoing minor merger | **supported**
- H: The stellar mass ratio indicates a minor merger | E: cigale and prospector SED fits with magnification correction | R: ratios 4.5 and 4.2 | F: About 4:1 minor merger | **supported**
- H: The merger elevates star formation | E: Compare sSFR to the main sequence | R: sSFR consistent with the main sequence | F: No elevated sSFR | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: A 50 mas taper balances resolution and sensitivity and matches NIRCam resolution  
  > "offers a reasonable compromise between spatial resolution and sensitivity and is well-matched to the resolution of the NIRCam imaging" (2.2 ALMA)
- How they decided it was enough: _not stated_
- Limitation (authors): Lens light subtraction was done separately from lens modeling, which hindered modeling with background noise  
  > "it would be prudent to perform the lens light subtraction within the software used to conduct the lens modeling" (4.1 Source Plane Reconstruction and Kinematics)
- Limitation (authors): Constraints on SPT0418B are less robust owing to limited photometric detections  
  > "The constraints on SPT0418B are less robust due to the more limited set of photometric detections" (4.2 Stellar Mass Ratios)
- Caveat (inferred, ours): Stellar masses differ by 2-4x between codes owing to the SFH assumptions
- Caveat (inferred, ours): Only one FIR point constrains SPT0418B
- Caveat (inferred, ours): Merger inference rests on a projected separation and a velocity offset of about -56 km/s only
- Caveat (inferred, ours): Lens model uncertainties are likely underestimated, with lens light subtracted separately

## Reproducibility

- Data public (paper): Acknowledgments cite ALMA project codes and JWST data from MAST  
  > "The data were obtained from the Mikulski Archive for Space Telescopes at the Space Telescope Science Institute" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Detailed tclean parameters
- Missing: Exact aperture definitions and cigale/prospector priors
- Missing: Birkin et al. and Rigby et al. companion data
- Data volume (inferred): ALMA ~50-200 GB raw for 4.9 h of data at multiple configurations; JWST images ~ a few GB
- Score (inferred): 3/5, Data are public and the methods are named, but many parameters are not stated and the JWST reduction is deferred to other papers.
- Rediscovery candidate: no, The JWST-centered, multi-step pipeline is under-specified and the ALMA part is minor.

## Links

- Method: Rigby et al. 2023 (in prep) (TEMPLATES JWST data reduction)
- Companion: Peng et al. 2022 (cite: peng2022arXiv221016968P) (Independent report of the companion)
- Companion: Rizzo et al. 2020 (cite: rizzo2020Natur.584..201R) (ALMA kinematics of SPT0418-47)
- Related: TEMPLATES JWST ERS 1355

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 42,
  "rate": 0.575
 },
 "evidence_ok": true
}
```

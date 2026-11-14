# Herschel-ATLAS and ALMA. HATLAS J142935.3-002836, a lensed major merger at redshift 1.027

`2014A&A...568A..92M` | Astronomy and Astrophysics 2014 | first author: Messias, Hugo | arXiv: 1406.4859 | DOI: 10.1051/0004-6361/201424410

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Confirm the lensing hypothesis for H1429-0028, model the background source's morphology and dynamics, and provide a full physical characterisation.  
  > "Gathering a rich, multi-wavelength dataset, we aim to confirm the lensing hypothesis and model the background source’s morphology and dynamics, as well as to provide a full physical characterisation." (abstract)
- Target **HATLAS J142935.3-002836 (H1429-0028)**: coordinates _not stated_; z/distance background z=1.027, foreground z=0.218  
  > "The background source (at $z_{\rm sp}=1.027$) is magnified by a factor of $\mu\sim8-10$ depending on wavelength." (abstract); distance from Z-Spec/CARMA/ALMA CO lines (background); Gemini GMOS-S spectroscopy (foreground)  
  > "The background source (at $z_{\rm sp}=1.027$) is magnified by a factor of $\mu\sim8-10$ depending on wavelength." (abstract)

## Data provenance

- ALMA projects: 2011.0.00476.S
- bands: Band 3 (107 GHz) and Band 6 (234 GHz)  
  > "Band 3 (centred at 107 GHz) and Band 6 (234 GHz) — were observed during shared-risk time (Cycle 0)" (2.8 ALMA)
- frequencies and spectral setup: Four FDM spectral windows per band, 1.875 GHz bandwidth, 0.488 MHz channels  
  > "All spectral windows (four in each set-up) were set in frequency division mode (FDM) with a 1.875-GHz bandwidth (0.488 MHz channel width)" (2.8 ALMA)
- continuum bandwidth: _not stated_
- arrays: 12 m array, Cycle 0 extended configuration  
  > "with 16 antennas in the Cycle-0 ‘extended configuration’" (2.8.1 Band 3)
- configurations: _not stated_
- baselines: Band 3: ~20-450 m; Band 6: max ~400 m  
  > "with baselines between $\sim$20 m and $\sim$450 m" (2.8.1 Band 3); "(maximum baseline of $\sim$400 m)" (2.8.2 Band 6)
- angular resolution: Band 3 ~1.88''x1.25'' (natural); Band 6 ~0.81''x0.58'' (natural)  
  > "allowed the source to be imaged at a resolution of $\sim$0.81$''$$\times$0.58$''$ (natural weighting)" (2.8.2 Band 6)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: about 30 min in each band  
  > "The total on-source integration time was about 30 min in each band." (2.8 ALMA)
- observing dates: Band 3: 2012 May 9 and July 28; Band 6: 2012 April 23  
  > "The Band-6 science goal was executed on 2012 April 23" (2.8.2 Band 6)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.538 GHz)
- Line: 12CO J=4-3 (461.041 GHz)
- Line: CI 3P1-3P0 (492.161 GHz)
- Line: CS J=10-9 (489.751 GHz)
- Other facility **Z-Spec/APEX**: CO(4-3) and CO(5-4) detections, redshift 1.026  
  > "The two reliably-detected lines are identified as CO (J:4$\to$3) and CO (J:5$\to$4), yielding a redshift of 1.026$\pm$0.002 for the background source." (3.3 Z-SPEC on APEX)
- Other facility **CARMA**: CO(2-1) detection and z=1.0271  
  > "implying an improved redshift estimate (in comparison to that obtained from Z-SPEC) of $z=1.0271\pm0.0002$" (3.4 CARMA)
- Other facility **HST WFC3 F110W**: near-IR high-resolution imaging  
  > "The total exposure time was 252 s." (2.3 Hubble Space Telescope F110W)
- Other facility **Keck NIRC2 LGSAO**: H and Ks imaging  
  > "We obtained 15 useful 80-s exposures in $K_{\rm s}$ and 10 useful 120-s exposures in $H$." (2.4 Keck Telescope Adaptive Optics)
- Other facility **JVLA**: 7 GHz continuum, 0.4''x0.3'' beam  
  > "the resulting map has a $0.4'' \times 0.3''$ fwhm synthesised beam and an r.m.s. noise level of 10 $\mu$Jy beam$^{-1}$" (2.6 Jansky Very Large Array 7 GHz)
- Other facility **Herschel H-ATLAS, Spitzer IRAC, WISE, SDSS, VIKING, IRAM MAMBO-2, Gemini GMOS-S**: multi-wavelength photometry and foreground redshift  
  > "we obtained $ugriz$ (SDSS), $ZYHJK_{\rm s}$ (VIKING), 3.4–22 $\mu$m (WISE), and 100–500 $\mu$m (*H*-ATLAS) photometry" (2.9 Data from wide-field surveys)
- External data: Alternative lens model (SIE, galfit+gravlens) for comparison  
  > "An alternative approach to the procedure just presented is described in (cite: Calanog14), where galfit and gravlens (cite: Keeton01) are used iteratively to model the lens in the near-IR observed-frame." (4.1.1 Lens characterisation) [from (cite: Calanog14)]
- External data: SED models for extreme star-forming systems used in magphys  
  > "for the background source, we have adopted the models presented in that same work, which are better suited for more extreme star-forming systems." (4.2 Foreground and background SEDs) [from (cite: Rowlands14)]

## Processing

### Calibration

- pipeline or manual: Initial calibration by ALMA operations team; team checked and reprocessed with Butler-JPL-Horizons 2012 models, in CASA  
  > "Our team checked the phase and amplitude steps of the calibration, and re-processed the data taking into account the new Butler-JPL-Horizons 2012 models." (2.8 ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (flux), J1256-057 (3C 279) bandpass, J1408-078 phase  
  > "Titan was used as a flux calibrator and J1256$-$057 (3C 279) as a bandpass calibrator." (2.8 ALMA)
- flux scale uncertainty: _not stated_
- self calibration: One phase self-cal run on Band 6 using CO(4-3) map  
  > "One self-calibration run was done using the CO (J:4$\to$3) map in order to further correct phase-delays on this dataset" (2.8.2 Band 6)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting (also uniform quoted); Briggs robust=0 for JVLA only  
  > "(natural weighting) or $\sim$1.57$''$$\times$1.12$''$ (uniform weighting)" (2.8.1 Band 3)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum images made from line-free channels; effective 5.0 GHz (B3) and 4.7 GHz (B6)  
  > "we then created a higher signal-to-noise continuum map by combining all line-free channels to obtain effective bandwidths of 5.0 GHz and 4.7 GHz in bands 3 and 6, respectively." (3.6 ALMA: continuum emission)
- line free channels: _not stated_
- primary beam correction: not needed; source ~2'' within primary beam  
  > "so no relative flux corrections are required across the field" (2.8.1 Band 3)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Lens modelling code (enhanced semi-linear inversion)  
  > "Our analysis is done with the enhanced version of the semi-linear inversion (SLI) method algorithm originally derived by (cite: Warren03) and described in (cite: Dye14)." (4.1.1 Lens characterisation) [from (cite: Warren03); (cite: Dye14)]
- Herschel data reduction and source extraction  
  > "The SPIRE data reduction is described in (cite: Pascale11), while source extraction and flux density estimation are described in (cite: Rigby11)." (2.1 Source Selection) [from (cite: Pascale11); (cite: Rigby11)]
- ISM mass from submm continuum  
  > "(cite: Scoville14) propose an empirical approach to estimate total ISM gas mass ($M_{\rm H\,I}+M_{\rm H_2}$) based on submm continuum emission." (4.4 Molecular gas) [from (cite: Scoville14)]

### Not stated but needed to reproduce (our reading)

- tclean/clean parameters (deconvolver, threshold, cell, image size, masks)
- robust/taper details and line-free channel ranges
- Self-calibration solution interval and reference
- CASA version
- Lens model priors, regularisation and source-plane pixel scale
- Moment-map velocity ranges and clipping
- MAGPHYS modified code with upper limits not public

## Analysis recipe

1. **Image ALMA lines and continuum**: Imaged with natural weighting; moment maps; continuum from line-free channels  
  > "Continuum-only images were made individually for each spectral window (in each band) after discarding channels with line emission from the transitions presented above." (3.6 ALMA: continuum emission)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared ALMA line flux with Z-Spec and CARMA  
  > "We would like to highlight the flux density agreement between ALMA observations and those of Z-SPEC and CARMA." (3.5 ALMA Data: Line emission)
2. **Lens model fit**: SLI simultaneous fit of CO(4-3) moment-0 and 7 GHz maps with elliptical power-law mass profile, no external shear  
  > "the images given as input are the velocity-integrated CO(4$\to$3) line map and the 7-GHz continuum map." (4.1.1 Lens characterisation)
   - software: SLI code
   - fitting: _not stated_
   - validation: Fraction of >2 sigma residuals 0.2% (7 GHz) and 0.5% (CO)  
  > "we measure a fraction of $>2\sigma$ residuals of 0.2% and 0.5% for the 7 GHz and CO (J:4$\to$3) data respectively." (4.1.1 Lens characterisation)
3. **Source-plane reconstruction and dynamics**: Apply best-fit lens model to CO(4-3) cube; dynamical mass via isotropic virial estimator; r1/2 from moment minimisation and bootstrapping  
  > "The uncertainties were found via bootstrapping, i.e., the pixel flux values were shifted within $\pm$r.m.s., and $r_{1/2}$, $x_c$, and $y_c$ were recomputed for a total of 10,000 iterations." (4.1.3 Source dynamical analysis)
   - fitting: _not stated_
   - validation: _not stated_
4. **SED fitting of foreground and background**: magphys flux PDFs after galfit foreground removal, extinction scenarios and demagnification; emcee modified blackbody fits  
  > "Given the lack of spatially resolved photometry, we avoid working with best-fit solutions and consider instead flux probability distribution functions (PDFs)." (4.2 Foreground and background SEDs)
   - software: magphys, galfit, emcee
   - parameter: limits: beta<3, T<100 K observed-frame, lambda0<2000 um  
  > "it was necessary to limit $\beta$ below 3, the temperature to observed-frame 100 K, and, in the optically-thick case, $\lambda_0$ below observed-frame 2000 $\mu$m." (4.2 Foreground and background SEDs)
   - assumption: Chabrier IMF; H0=70, Om=0.3, OL=0.7  
  > "H$_{0} = 70$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_{M} = 0.3$, $\Omega_{\Lambda} = 0.7$, and a Chabrier initial mass function." (1 Introduction)
   - fitting: emcee affine invariant MCMC; priors beyond parameter limits not stated  
  > "using an affine invariant Markov chain Monte Carlo method (cite: Foreman12)" (4.2 Foreground and background SEDs)
   - validation: _not stated_
5. **Gas mass and depletion time**: Scoville14 relation using 1.28 mm flux; CO and CI limits for H2  
  > "the estimated intrinsic ISM gas mass is $M_{\rm ISM} = 4.6\pm1.7\times 10^{10}\,{\rm M_\ensuremath{\odot}}$" (4.4 Molecular gas)
   - assumption: Xco thin ~0.449 (T=35.9 K, [CO/H2]=1e-4) lower limit; Xco=5 upper limit  
  > "an upper limit may be estimated assuming $X_{\rm CO}=5$" (4.4 Molecular gas)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : ALMA data processing  
  > "Data processing was done using CASA" (2.8 ALMA)
- **MIRIAD** : CARMA data processing  
  > "The MIRIAD package was used for data processing and analysis." (2.7 CARMA)
- **galfit** : foreground/background flux separation  
  > "we have used galfit (cite: Peng10) to fit and estimate foreground and background fluxes" (3.7 Multi-wavelength photometry)
- **magphys** : SED fitting  
  > "we utilise the magphys software (cite: daCunha08)" (4.2 Foreground and background SEDs)
- **emcee** : modified blackbody fits  
  > "using an affine invariant Markov chain Monte Carlo method (cite: Foreman12)" (4.2 Foreground and background SEDs)
- **IRAF** : Gemini spectroscopy reduction  
  > "We processed the data using standard IRAF GMOS-S reduction routines." (2.2 Optical spectroscopy)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Lens Einstein radius | 2.18 | +0.19/-0.27 | kpc | 2 | $\theta_{\rm E}=2.18_{-0.27}^{+0.19}\,$kpc |
| Magnification mu_TOT CO(4-3) | 9.7 | 0.7 | dimensionless | 3 | ALMA CO (J:4$\to$3) / $9.7\pm0.7$ |
| Dynamical mass of NS component | 5.8e10 | 1.7e10 | Msun | 3 | the dynamical mass to be $5.8\pm1.7\times10^{10}\,$M$_\odot$ |
| Background SFR | 394 | +91/-88 | Msun/yr | 4 | 394$_{-88}^{+91}$ |
| ISM gas mass | 4.6e10 | 1.7e10 | Msun | 5 | $M_{\rm ISM} = 4.6\pm1.7\times 10^{10}\,{\rm M_\ensuremath{\odot}}$ |
| Depletion time | 117 | 51 | Myr | 5 | $\tau_{\rm SF}=M_{\rm ISM}/{\rm SFR}=117_{-51}^{+51}\,$Myr |
| Merger mass ratio | 1:2.8 | +1.8/-1.5 | dimensionless | 5 | 1:2.8$_{-1.5}^{+1.8}$ intermediate-to-major merger at $z=1.027$ |
| CO(4-3) integrated flux total | 43.9 | 3.7 | Jy km/s | 1 | 43.9$\pm$3.7 |
| Millimetre spectral index B3-B6 | 3.29 | 0.40 | dimensionless | 1 | $\beta=3.29\pm0.40$ |

## Qualitative findings

- Foreground edge-on disk with near-complete Einstein ring; background is a merger of two components with a tidal tail resembling the Antennae.  
  > "It is comprised of two components and a tens of kpc long tidal tail resembling the Antennæ merger." (abstract)

## Claim tuples

- H: Is H1429-0028 a gravitationally lensed system and what is the background source like? | E: Joint SLI lens modelling of CO(4-3) and 7 GHz maps; source-plane reconstructions at several wavelengths | R: Einstein radius 2.18 kpc, mu~8-10, two components at ~80 deg | F: Lensed background major merger | **supported**
- H: Is the system a major merger? | E: Compare CO dynamical mass of NS component to SED-derived total mass | R: Mass ratio 1:2.8 | F: Intermediate-to-major merger | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Variability, micro-lensing and non-standard halo scenarios for the knot brightness discrepancy dismissed or not addressed; variability ruled out by similar JVLA/ALMA morphology  
  > "we can safely assume variability is not responsible for the discrepant multi-wavelength morphology" (4.1 Lens model)
- How they decided it was enough: _not stated_
- Limitation (authors): Knot C in rest-frame optical poorly fitted by the lens model  
  > "Still, the fit is poor." (4.1.2 Source-plane reconstruction)
- Caveat (inferred, ours): Dynamical mass from isotropic virial estimator on a disturbed system with half-light radius from pixel moments is crude
- Caveat (inferred, ours): Merger ratio relies on subtraction of SED mass and an assumed dark-matter fraction
- Caveat (inferred, ours): Gas mass depends on uncertain Xco and Scoville14 calibration

## Reproducibility

- Data public (paper): ALMA project 2011.0.00476.S cited; public status not stated  
  > "H1429$-$0028 was observed by ALMA as part of the project 2011.0.00476.S (ALMA Cycle 0; P.I. G. Orellana)." (ALMA)
- Products in archive: _not stated_
- Missing: Detailed CASA imaging parameters
- Missing: SLI code and priors
- Missing: Modified magphys code with upper limits
- Missing: Calibrated photometry for non-ALMA data
- Data volume (inferred): ~50-100 GB for two ALMA Cycle 0 execution sets (raw)
- Score (inferred): 3/5, ALMA data identified, but imaging and lens-modelling settings largely unstated and relies on non-public code.
- Rediscovery candidate: no, Imaging parameters and custom lens code are not given, so the recipe is incomplete.

## Links

- Method: (cite: Warren03); (cite: Dye14) (SLI lens modelling)
- Method: (cite: daCunha08) (magphys SED code)
- Method: (cite: Scoville14) (ISM mass relation)
- Companion: (cite: Calanog14) (independent lens model of the same system)
- Related: H-ATLAS
- Related: GAMA 15-hr field

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
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
  "stated": 48,
  "rate": 0.593
 },
 "evidence_ok": true
}
```

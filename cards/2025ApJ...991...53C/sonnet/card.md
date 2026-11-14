# HerS-3: An Exceptional Einstein Cross Reveals a Massive Dark Matter Halo

`2025ApJ...991...53C` | The Astrophysical Journal 2025 | first author: Cox, P. | arXiv: 2509.14983 | DOI: 10.3847/1538-4357/adf204

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, cosmology
- Question: What is the lensing configuration of the HerS-3 Einstein cross (with a fifth central image), and does it require a massive dark matter halo in the lensing galaxy group?  
  > "Lens models that only include the four visible galaxies are unable to reproduce the properties of HerS-3." (abstract)
- Target **HerS-3**: coordinates SW image 01:27:54.01 +00:49:37.1 (J2000, from ALMA centroids)  
  > "HerS-3, a dusty star-forming galaxy at $z_{\rm spec} = 3.0607$" (abstract); "| SW    | 01:27:54.01 | 00:49:37.1 |" (Table 1); z/distance z_spec = 3.0607  
  > "HerS-3, a dusty star-forming galaxy at $z_{\rm spec} = 3.0607$" (abstract); "| SW    | 01:27:54.01 | 00:49:37.1 |" (Table 1); distance from CO(3-2) and (5-4) in z-GAL survey (Cox2023)  
  > "HerS-3, a dusty star-forming galaxy at $z_{\rm spec} = 3.0607$" (abstract); "| SW    | 01:27:54.01 | 00:49:37.1 |" (Table 1)

## Data provenance

- ALMA projects: 2022.1.00145.S
- bands: ALMA Band 7 (1 mm), 291.8 GHz  
  > "The source was observed at 291.8 GHz for a total on-source time of $\sim$3.0 min" (2.2 ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 7.875 GHz with 4 GHz sideband separation  
  > "covering a bandwidth of 7.875 GHz with a 4 GHz sideband separation" (2.2 ALMA)
- arrays: _not stated_
- configurations: C43-6  
  > "a system temperature $\rm T_{sys}=91~K$ in configuration C43-6" (2.2 ALMA)
- baselines: _not stated_
- angular resolution: 0.12'' x 0.10'' (robust = 2.0)  
  > "yielding an angular resolution of $0.12\ensuremath{''} \times 0.10\ensuremath{''}$ using a $\rm robust = 2.0$ weighting" (2.2 ALMA)
- max recoverable scale: _not stated_
- sensitivity: 63 uJy/beam (1 sigma) continuum  
  > "a continuum sensitivity of $\rm 63~\mu Jy \, beam^{-1}$ (1$\sigma$)" (2.2 ALMA)
- time on source: ~3.0 min  
  > "The source was observed at 291.8 GHz for a total on-source time of $\sim$3.0 min" (2.2 ALMA)
- observing dates: 2023 June 1  
  > "The observations were done on 2023 June 1." (2.2 ALMA)
- pi or archival as stated: Cycle 9 project, P.I. T. Bakx  
  > "ALMA Cycle 9 project ADS/JAO.ALMA 2022.1.00145.S (P.I.: T. Bakx)" (2.2 ALMA)
- Line: 12CO 9-8 (1036.912 GHz)
- Line: OH+ 1_1-0_1 (1033.118 GHz)
- Other facility **NOEMA**: 1-mm lines (CO(9-8), H2O, OH+) and continuum, resolving the five images  
  > "We used NOEMA to target high-frequency molecular lines in HerS-3, redshifted into the 1-mm band." (2.1 NOEMA)
- Other facility **VLA**: 6 GHz radio continuum  
  > "We observed the radio continuum emission of HerS-3 using the NSF’s Karl G. Jansky Very Large Array (VLA)" (2.3 VLA)
- Other facility **HST WFC3 F110W**: near-IR imaging of the foreground lensing group  
  > "The observations were performed using the wide-YJ filter *F110W* of the Wide Field Camera 3 (WFC3) IR channel." (2.4 HST imaging)
- Other facility **Subaru/HSC and SDSS**: optical photometry of lensing galaxies  
  > "we used stacked SDSS and Subaru/HSC observations" (2.5 Subaru and SDSS imaging)
- External data: Herschel and z-GAL continuum flux densities  
  > "Together with the *Herschel* and $z$-GAL continuum flux densities (cite: Ismail2023)" (3.3 Continuum SED) [from (cite: Ismail2023)]
- External data: 12CO(3-2) and (5-4) line fluxes  
  > "$J$=5$-$4 and 3$-$2 (cite: Cox2023)" (5.1.1) [from (cite: Cox2023)]
- External data: CO(1-0) flux 0.71±0.08 Jy km/s  
  > "$J$=1$-$0 ($0.71\pm0.08 \, \rm Jy \, km s^{-1}$; Prajapati et al. in prep)" (5.1.1) [from Prajapati et al. in prep.]

## Processing

### Calibration

- pipeline or manual: Reduced and imaged with CASA  
  > "The ALMA data were reduced and imaged using the Common Astronomy Software Application[^1] (CASA v6.5.4.9)" (2.2 ALMA)
- casa version: CASA v6.5.4.9  
  > "(CASA v6.5.4.9)" (2.2 ALMA)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: additional 10% error in quadrature  
  > "an additional 10% error was added in quadrature to account for calibration errors" (2.2 ALMA)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust = 2.0  
  > "using a $\rm robust = 2.0$ weighting" (2.2 ALMA)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: fluxes from primary-beam corrected fields  
  > "extracted from the primary-beam corrected fields" (2.2 ALMA)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.12'' x 0.10''  
  > "yielding an angular resolution of $0.12\ensuremath{''} \times 0.10\ensuremath{''}$" (2.2 ALMA)
- final rms: 63 uJy/beam  
  > "a continuum sensitivity of $\rm 63~\mu Jy \, beam^{-1}$ (1$\sigma$)" (2.2 ALMA)

### Inherited from earlier work

- HST data re-reduction, PSF, noise map, mask  
  > "Details on the observations, data reduction, and computation of the background, noise map, source mask, and PSF are provided in (cite: Borsato2024)." (2.4 HST imaging) [from (cite: Borsato2024)]
- Noise scaling technique for correlated noise in pixsrc  
  > "adopt the noise scaling technique of (cite: Riechers2008) to account for spatially correlated noise (cite: Sharon2019)" (Appendix 8.2) [from (cite: Riechers2008); (cite: Sharon2019)]
- LVG MCMC RADEX implementation  
  > "using the Markov chain Monte Carlo (MCMC) implementation of RADEX (cite: vanderTak2007), as presented in (cite: Yang2017)" (Appendix 9) [from (cite: Yang2017)]

### Not stated but needed to reproduce (our reading)

- ALMA calibrator flux values, flux calibrator name and self-calibration use
- CLEAN threshold, cell size, image size and deconvolver for ALMA continuum
- Priors and MCMC sampler settings for lens model
- Regularization strength in pixsrc
- SED fit priors and sampler for MBB
- LVG priors on component sizes and temperatures
- Magnification adopted for the intrinsic properties beyond mu~18

## Analysis recipe

1. **Measure continuum flux densities of five images**: Aperture photometry on primary-beam corrected ALMA map, apertures extend two beams beyond 2 sigma contours  
  > "using apertures that fit all of the continuum emission and extend two beams beyond the $2 \sigma$ contours" (2.2 ALMA)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit molecular lines**: Simultaneous single-Gaussian fits to lines with linear continuum, anchoring OH+ velocity and width together and emission lines together  
  > "we simultaneously fitted each of the molecular emission and absorption lines with a single Gaussian component and the underlying continuum with a linear curve" (3.4)
   - software: scipy curve_fit
   - fitting: curve_fit least squares  
  > "Using the `curve_fit` procedure" (3.4)
   - validation: _not stated_
3. **Fit dust SED**: Optically thin and general-form modified black body fits with CMB correction  
  > "a single-temperature modified black-body (MBB) in the optically-thin approximation and a MBB model in its general form" (3.3)
   - assumption: kappa renormalization of Draine2014; synchrotron S ∝ nu^-0.8 and free-free nu^-0.1  
  > "We adopt the $\kappa_\nu$ re-normalization by (cite: draine2014)." (3.3)
   - fitting: _not stated_
   - validation: _not stated_
4. **Lens modeling: point images then pixel-based source reconstruction**: Two-stage: point-source modeling with four SIE galaxies plus shear (with and without a fifth cored-isothermal or NFW halo), then pixsrc reconstruction on ALMA 292 GHz data  
  > "we conducted the lens modeling in a two-stage approach." (4)
   - software: lensmodel, pixsrc
   - parameter: position uncertainty 0.03''; Einstein radius lognormal priors 0.1 dex; shape priors 0.20 (mild) or 0.05 (strong); shear 0.00±0.05  
  > "We assumed position uncertainties of $0.03\ensuremath{''}$." (Appendix 8.1)
   - parameter: pixsrc noise increased to 80 uJy/beam  
  > "increasing the noise level in *pixsrc* to $\rm 80 \, \mu Jy/beam$ provides the best balance between goodness of fit and regularization" (Appendix 8.2)
   - assumption: All galaxies and halo at the same redshift z~1  
  > "The additional mass component is assumed to lie at the same redshift as the four visible galaxies." (4)
   - fitting: MCMC posteriors; chi^2 minimization with priors  
  > "| G1     | $11.85$      | $11.99_{-0.15}^{+0.08}$ |" (Table 3)
   - validation: Compared model image peaks, shapes and orientations to observed ALMA images; rms offset <0.02''  
  > "with a rms offset between the observed and model brightness peaks of better than $0.02\ensuremath{''}$" (4)
5. **Derive molecular gas properties**: Two-component LVG (RADEX+emcee) fit to CO SLED; L'CO and M_H2 from CO(1-0) with alpha_CO  
  > "we used a two-excitation component model, assigning different parameters to each of the components" (5.1.1)
   - software: RADEX, emcee
   - assumption: alpha_CO = 3 Msun/(K km/s pc^2) x 1.36 for helium  
  > "we multiply it by the usual factor of 1.36 to account for the helium contribution" (5.1.1)
   - fitting: emcee MCMC  
  > "the code *emcee* is adopted to perform the MCMC calculation" (Appendix 9)
   - validation: _not stated_

## Software

- **CASA** 6.5.4.9: ALMA and VLA reduction and imaging  
  > "CASA v6.5.4.9" (2.2 ALMA)
- **GILDAS** : NOEMA calibration, mapping and analysis  
  > "The data were calibrated, averaged in polarization, mapped, and analyzed in the GILDAS software package." (2.1 NOEMA)
- **lensmodel** : lens modeling  
  > "using the *lensmodel* package (cite: Keeton2001)" (4)
- **pixsrc** : pixel-based source reconstruction  
  > "pixel-based source reconstruction code *pixsrc*" (4)
- **PyAutoGalaxy** : surface-brightness modelling of lens galaxies  
  > "We performed the surface brightness modeling using PyAutoGalaxy" (Appendix 7)
- **bagpipes** : SED fitting of lensing galaxies  
  > "We fit the lenses’ spectral energy distribution (SED) using the `bagpipes` code" (Appendix 7)
- **photutils** : source detection, deblending, background  
  > "We used the `detect_sources` `photutils` task" (Appendix 7)
- **RADEX** : LVG CO SLED modelling  
  > "we derived a Large Velocity Gradient (LVG) radiative transfer model for the CO spectral line energy distribution (SLED) of HerS-3 using the Markov chain Monte Carlo (MCMC) implementation of RADEX" (Radiation transfer Large Velocity Gradient Model)
- **emcee** : MCMC for LVG  
  > "the code *emcee* is adopted to perform the MCMC calculation" (Appendix 9)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Spectroscopic redshift | 3.0607 | not stated | dimensionless | 2 | $z_{\rm spec} = 3.0607$ |
| Total magnification (cored halo) | 19 | +14/-5 | dimensionless | 4 | $\rm \mu = 19^{+14}_{-5}$ for the cored halo model |
| Total magnification (NFW halo) | 17 | +5/-4 | dimensionless | 4 | $\rm \mu = 17^{+5}_{-4}$ for the NFW halo model |
| Enclosed dark matter mass range | log M_DM = 12.2 to 13.0 | not stated | Msun | 4 | the enclosed dark matter mass ranges from $\log M_{\rm DM}/{\rm M_{\odot}} = 12.2$ up to $13.0$ |
| Halo velocity dispersion (cored) | 633 | +185/-129 | km/s | 4 | $\sigma = 633_{-129}^{+185}$ km/s |
| OH+ absorption blueshift | -350 | ±32 | km/s | 2 | $-350\pm32$ |
| CO(9-8) flux | 11.3 | ±0.95 | Jy km/s | 2 | $11.3\pm0.95$ |
| CO emission FWHM | 320 | ±28 | km/s | 2 | have a full-width half maximum (FWHM) of $320\pm28 \, \rm km s^{-1}$ |
| Dust temperature (optically thin MBB) | 34.1 | ±1.1 | K | 3 | $T_{\rm dust}=34.1 \pm 1.1 \, \rm K$ |
| Total IR luminosity mu*L_IR (optically thin) | 7.54e13 | ±0.12e13 | Lsun | 3 | $\mu L_{\rm IR}=7.54 \pm 0.12 \times 10^{13} \, L_{\ensuremath{\odot}}$ |
| mu*M_H2 | 1.25e12 | ±0.14e12 | Msun | 5 | $\mu M_{\rm H_2} = 1.25\pm0.14 \times 10^{12} \, \rm M_{\odot}$ |
| Depletion time | 152 | not stated | Myr | 5 | yielding a depletion time of $t_{\rm depl} = 152 \, \rm Myr$ |
| Source-plane inclination | ~66 | not stated | deg | 4 | yielding $i \sim 66^\circ$ for both the cored halo and NFW profile models |
| Predicted C-image delay relative to NE (cored) | 273.6 | +53.3/-71.2 | days | 4 | / C     / $273.6_{-71.2}^{+53.3}$               / |

## Qualitative findings

- All five images share the same redshift and show OH+ outflow absorption.  
  > "unambiguously demonstrating that the five images have the same redshift ($z$=3.0607)" (3.4)
- First Einstein cross detected at sub-mm wavelengths with a central fifth image.  
  > "This is the first time that a gravitationally amplified high-$z$ galaxy is seen in an Einstein cross system with an image of the background galaxy at the center of the cross" (3.1.1)

## Claim tuples

- H: Four visible galaxies alone can reproduce the five-image configuration | E: Lens models with G1-G4 plus shear, mild and strong shape priors | R: Mild priors give chi2=104 and need an overly elongated G3; strong priors give chi2=300 with 0.13'' rms offset | F: Four-galaxy models fail | **supported**
- H: An additional massive dark matter halo explains the images | E: Add cored isothermal or NFW halo and reconstruct the source with pixsrc | R: rms offset between observed and model peaks <0.02''; halo 3-7'' SE of G1 | F: A massive dark matter halo is indicated; its internal profile is unconstrained | **supported**
- H: HerS-3 is a nuclear starburst with outflow and high excitation | E: Line fits, CO SLED LVG model, SED | R: OH+ blueshift ~350 km/s, t_depl=152 Myr, inclination ~66 deg | F: Infrared luminous starburst with outflow, likely shock-excited | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Point-source modelling first for efficient exploration, then pixelated source reconstruction  
  > "This approach is computationally efficient and facilitates a thorough exploration." (Appendix 8)
- Alternative: Models with four galaxies only rejected; cored and NFW halos equally good; elliptical halo and non-isothermal galaxy profiles briefly tested  
  > "We briefly explored two ways to generalize the cored halo models." (4)
- How they decided it was enough: _not stated_
- Limitation (authors): Halo internal structure and magnification are poorly constrained; lens redshifts uncertain  
  > "the internal structure of the dark matter halo cannot be constrained with the current data" (6)
- Caveat (inferred, ours): Lens model assumes spherical halo and single lens plane with photometric redshifts
- Caveat (inferred, ours): Halo mass depends on extrapolation to large radii
- Caveat (inferred, ours): Short 3-min ALMA observation limits S/N for source reconstruction
- Caveat (inferred, ours): Magnification and halo mass degenerate

## Reproducibility

- Data public (paper): ALMA project cited; HST data from MAST with DOI  
  > "The *HST* data were obtained from the Mikulski Archive for Space Telescopes (MAST)" (2.4 HST imaging)
- Products in archive: _not stated_
- Missing: lens model MCMC settings and priors beyond those listed
- Missing: pixsrc regularization settings
- Missing: ALMA clean parameters
- Missing: NOEMA data not archive-public as stated
- Data volume (inferred): ~5-20 GB for the short ALMA Band 7 execution
- Score (inferred): 3/5, ALMA data public and key steps described, but imaging and lens-model details partly missing and analysis relies on multiple other datasets.
- Rediscovery candidate: no, Main results depend on a complex lens model with unstated sampling details and non-ALMA data.

## Links

- Method: (cite: Tagore&Keeton2014) (pixsrc source reconstruction)
- Method: (cite: Borsato2024) (HST reduction and surface brightness modeling)
- Companion: (cite: Cox2023) (z-GAL redshift survey)
- Companion: Butler et al., in prep. (follow-up of z-GAL galaxies)
- Related: z-GAL
- Related: Herschel

## Checks

```json
{
 "quotes": 82,
 "quotes_ok": 82,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 58,
  "rate": 0.674
 },
 "evidence_ok": true
}
```

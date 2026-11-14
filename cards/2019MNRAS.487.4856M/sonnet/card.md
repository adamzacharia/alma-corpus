# The kiloparsec-scale gas kinematics in two star-forming galaxies at z ∼ 1.47 seen with ALMA and VLT-SINFONI

`2019MNRAS.487.4856M` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Molina, J. | arXiv: 1906.06245 | DOI: 10.1093/mnras/stz1643

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: How do the kpc-scale CO(2-1) molecular gas kinematics compare with H-alpha ionised gas in two main-sequence galaxies at z~1.47, and what do they imply for dynamical mass, dark matter fraction and depletion time?  
  > "We carried out a follow-up study to resolve, at $\sim$kpc-scales, the CO emission." (abstract)
- Target **SHiZELS-8**: coordinates RA 02:18:21.0, Dec -05:19:07.8 (J2000)  
  > "| RA (J2000) | 02:18:21.0 | 09:59:11.5 |" (Table 2); "| $z_{\rm spec}$ | 1.4608 | 1.4861 |" (Table 2); z/distance z_spec = 1.4608  
  > "| RA (J2000) | 02:18:21.0 | 09:59:11.5 |" (Table 2); "| $z_{\rm spec}$ | 1.4608 | 1.4861 |" (Table 2); distance from _not stated_
- Target **SHiZELS-19 (COS-30)**: coordinates RA 09:59:11.5, Dec +02:23:24.3 (J2000)  
  > "| Dec (J2000) | $-$05:19:07.8 | +02:23:24.3 |" (Table 2); "| $z_{\rm spec}$ | 1.4608 | 1.4861 |" (Table 2); z/distance z_spec = 1.4861  
  > "| Dec (J2000) | $-$05:19:07.8 | +02:23:24.3 |" (Table 2); "| $z_{\rm spec}$ | 1.4608 | 1.4861 |" (Table 2); distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.01674.S, 2012.1.00402.S, 2015.1.00862.S
- bands: Band 3 (Cycle 5), combined with Cycle-1 and -3 data  
  > "We made use of Cycle-5 ALMA Band-3 observations" (2.2 ALMA observations & data reduction); "We combine them with previous $2''$ resolution Cycle-1 and -3 ALMA data" (2.2 ALMA observations & data reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ≈0.15'' (Cycle 5 extended configuration); 2'' for Cycle 1/3  
  > "The Cycle-5 observations were taken in an extended configuration (synthesized beam FWHM of $\approx 0.15\ensuremath{''}$)" (2.2 ALMA observations & data reduction)
- max recoverable scale: _not stated_
- sensitivity: rms 120–150 μJy/beam at 0.15'' with 60 km/s channels  
  > "reaching a root-mean-squared (r.m.s.) noise of 120–150 $\mu$Jy beam$^{-1}$ at 0$\ensuremath{''}$15 angular resolution using a channel width of 60 km s$^{-1}$" (2.2 ALMA observations & data reduction)
- time on source: ~44-47 min per execution (see Table 1)  
  > "| SHiZELS-8 | 2017.1.01674.S | 14 November 2017 | J0238+1636 | J0238+1636 | J0217-0820 | 3.17 | 43 | 47.05 |" (Table 1)
- observing dates: 14-20 November 2017 (Cycle 5)  
  > "Those observations were carried during November 2017" (2.2 ALMA observations & data reduction)
- pi or archival as stated: Cycle-5 PI Molina J.; Cycle-1/3 data from Hughes et al. in prep.  
  > "2017.1.01674.S; P.I. Molina J." (2.2 ALMA observations & data reduction)
- Line: CO J=2-1 (230.538 GHz)
- Other facility **VLT-SINFONI**: AO-aided H-alpha IFU data at ~0.15'' resolution  
  > "Combining ALMA with the available AO-aided H$\alpha$ data observed by the Spectrograph for INtegral Field Observations in the Near Infrared (SINFONI) on the Very Large Telescope (VLT)" (1 Introduction)
- Other facility **HST**: F160W and F814W images for morphology  
  > "consistent with the morphology observed in the H$\alpha$ intensity map (cite: Molina2017) and the *HST* F160W-band" (3.3 The SHiZELS-19 galaxy)
- Other facility **HiZELS narrow-band survey**: total H-alpha fluxes  
  > "The total H$\alpha$ emission line fluxes are taken from the HiZELS narrow-band survey" (2.1 The SHiZELS Survey)
- External data: Global CO(2-1) velocity-integrated fluxes  
  > "The global CO(2-1) velocity-integrated flux densities ($S_{\rm CO(2-1)} \Delta v$) are taken from Hughes et al. (in prep.)" (3.1 CO emission & CO-to-H2 conversion factor) [from Hughes et al. in prep.]
- External data: Stellar masses and SFRs  
  > "The global stellar masses and SFRs are taken from (cite: Gillman2019)." (2.1 The SHiZELS Survey) [from (cite: Gillman2019)]
- External data: H-alpha kinematics of SHiZELS-19  
  > "the H$\alpha$ emission line properties were derived and presented in an analogous manner in (cite: Molina2017)" (3.3 The SHiZELS-19 galaxy) [from (cite: Molina2017)]
- External data: Sersic index from HST  
  > "Taking into account that the Sérsic index derived from the *HST* image is consistent with unity for this galaxy (cite: Gillman2019)" (3.4 Dynamical Mass & Dark Matter content) [from (cite: Gillman2019)]

## Processing

### Calibration

- pipeline or manual: standard ALMA pipeline up to calibrated uv products  
  > "considering a standard ALMA pipeline up to calibrated $u$-$v$ products" (2.2 ALMA observations & data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean  
  > "We used the task tclean to deconvolve the data to produce datacubes for both galaxies." (2.2 ALMA observations & data reduction)
- deconvolver: multiscale, scales [0.5,5,15,45], cleaned to 3-sigma in emission regions  
  > "allowing multi-scale cleaning (multiscale=\[0.5,5,15,45\], where image pixel size is fixed at 0$\ensuremath{''}$04)" (2.2 ALMA observations & data reduction)
- weighting robust: Briggs, robust = 0.5  
  > "The high-resolution datacubes are produced by using Briggs weighting with robust parameter at 0.5" (2.2 ALMA observations & data reduction)
- uv taper: 2000 kλ taper  
  > "by tapering at 2000 k$\lambda$ and reducing the spatial resolution using a circular restoring synthesized beam" (2.2 ALMA observations & data reduction)
- cell size: 0.04''  
  > "where image pixel size is fixed at 0$\ensuremath{''}$04" (2.2 ALMA observations & data reduction)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Cycle 1, 3 and 5 data combined  
  > "for SHiZELS-19 we combine Cycle-1, -3 and -5 data to generate a high resolution" (2.2 ALMA observations & data reduction)
- smoothing: SHiZELS-8: 60 km/s channels, degraded to 0.50''  
  > "The spectral channel width is set to 60 km s$^{-1}$ and the spatial resolution is degraded to $0.50\ensuremath{''}$" (2.2 ALMA observations & data reduction)
- final beam: 0.15'' (high-res), 0.29'' (tapered), 0.5'' (SHiZELS-8)  
  > "a ‘low resolution’ ($\approx 0.29\ensuremath{''} \sim 2.5$ kpc) datacubes" (2.2 ALMA observations & data reduction)
- final rms: SHiZELS-8: 3.4 mJy km/s/beam (0.15''), 2.5 mJy km/s/beam (0.5'')  
  > "we obtain a velocity-integrated peak flux density r.m.s of 3.4 mJy km s$^{-1}$ beam$^{-1}$" (3.2 The SHiZELS-8 galaxy)

### Inherited from earlier work

- Cycle-1 and -3 ALMA data reduction and CO fluxes  
  > "(see Hughes et al. in prep. for more details)" (2.2 ALMA observations & data reduction) [from Hughes et al. in prep.]
- 2D emission-line fitting and genetic-algorithm kinematic modelling  
  > "by analysing the CO(2-1) emission line following the approach presented in (cite: Swinbank2012a)" (3.3 The SHiZELS-19 galaxy) [from (cite: Swinbank2012a)]
- Half-light radius calculation  
  > "We calculate the half-light radius ($r_{1/2}$) for each ISM component by following (cite: Molina2017)" (3.3.1 Global Dynamical Properties) [from (cite: Molina2017)]
- MCMC for alpha_CO and f_DM  
  > "we reproduce the parameter space built up in Eq. [\[eq:f_dm\]](#eq:f_dm) by applying an MCMC technique following (cite: Calistro2018)" (3.4 Dynamical Mass & Dark Matter content) [from (cite: Calistro2018)]

### Not stated but needed to reproduce (our reading)

- Cycle-1/-3 project-to-source assignment and their reduction details (in Hughes et al. in prep.)
- Line-free channels and continuum subtraction
- Clean mask details and tclean image size
- Phase self-calibration use
- Genetic algorithm settings and priors
- MCMC priors, walkers and chain length
- Aperture/binning details for the moment maps and the SHiZELS-8 smoothing method
- Which ALMA execution blocks went into each cube

## Analysis recipe

1. **Image CO(2-1) cubes**: tclean multiscale with Briggs weighting; high-res, 2000 kλ tapered and 0.5'' smoothed versions  
  > "We used the task tclean to deconvolve the data to produce datacubes for both galaxies." (2.2 ALMA observations & data reduction)
   - software: CASA
   - parameter: robust 0.5; multiscale [0.5,5,15,45]; 25 km/s channels for SHiZELS-19  
  > "we set the spectral channel width to 25 km s$^{-1}$" (2.2 ALMA observations & data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Molecular gas mass**: CO luminosity, r21=0.85, alpha_CO from Accurso+17 and Narayanan+12  
  > "We then estimate the CO(1-0) luminosity for each galaxy by assuming a $L'_{\rm CO(2-1)}/L'_{\rm CO(1-0)} = 0.85$ ratio" (3.1 CO emission & CO-to-H2 conversion factor)
   - assumption: alpha_CO from Narayanan+12 adopted for M_H2  
  > "The $M_{\rm H_2}$ and $f_{\rm H_2}$ quantities are computed by using $\alpha_{\rm CO,N+12}$" (Table 2)
   - fitting: _not stated_
   - validation: alpha_CO upper limit from dynamics (Appendix B)  
  > "we use the dynamical mass calculus to constrain the CO-to-H$_2$ conversion factor" (Appendix B)
3. **Moment maps**: spatial binning to beam, chi2 Gaussian line fitting for intensity, velocity and dispersion  
  > "we spatially bin the ALMA data-cube up to a scale given by the synthesized beam and then we perform an emission line fitting approach using a $\chi^2$ minimization procedure" (3.3 The SHiZELS-19 galaxy)
   - fitting: _not stated_
   - validation: _not stated_
4. **Inclination from morphology**: 2D Sersic fit to CO moment 0 giving axis ratio ~0.90±0.05, inclination ~26±6 deg, error inflated to 10%  
  > "We obtain an observed minor-to-major axis ratio of $\sim 0.90\pm 0.05$, which corresponds to an inclination angle value of $\sim26 \pm 6$ deg." (3.3.1 Global Dynamical Properties)
   - software: GALFIT
   - fitting: _not stated_
   - validation: _not stated_
5. **Joint 2D kinematic model**: arctan rotation curve, oblate spheroid of axis ratio 0.2, coupled inclination, 11 free parameters  
  > "This modelling has eleven free parameters" (3.3.1 Global Dynamical Properties)
   - assumption: ionised and molecular gas co-planar; PAs free  
  > "we are assuming that the ionized and molecular gas ISM phases are co-planar" (3.3.1 Global Dynamical Properties)
   - fitting: genetic algorithm; total chi2 summed over 2D maps  
  > "a genetic algorithm (cite: Charbonneau1995) is used to find the best-fit model" (3.3.1 Global Dynamical Properties)
   - validation: _not stated_
6. **Beam smearing correction and Vrot/sigma**: subtract velocity gradients across beam from dispersion map (Stott+16 Eq. A1); sigma is median beyond central zone of 3x resolution  
  > "We subtract them linearly from the corresponding velocity dispersion map by following Eq. A1 from (cite: Stott2016)." (3.3.1 Global Dynamical Properties)
   - fitting: _not stated_
   - validation: _not stated_
7. **Kinemetry asymmetry**: tilted-ring harmonic decomposition; k5/k1, Shapiro+08 and Bloom+18 estimators  
  > "we quantify the kinematic deviations from the ideal rotating disk case by performing a ‘*kinemetry*’ analysis" (3.3.2 Kinematic Asymmetry Characterization)
   - software: kinemetry
   - fitting: _not stated_
   - validation: _not stated_
8. **Dynamical mass and dark matter fraction**: thick-disk mass (Burkert+10 Eq. 11) from the tapered rotation curve; f_DM posterior with emcee  
  > "We use (cite: Burkert2010)’s Eq.11 with $\sigma_{v,{\rm CO}}$ and $r_{1/2,{\rm CO}}$ as input values" (3.4 Dynamical Mass & Dark Matter content)
   - software: emcee
   - assumption: _not stated_
   - fitting: _not stated_
   - validation: _not stated_
9. **Kennicutt-Schmidt and depletion time**: align Halpha and CO fields with HASTROM; pixel and tilted-ring Sigma_SFR, Sigma_H2, tau_dep, tau_orb  
  > "we use the Interactive Data Language (IDL) procedure HASTROM to align the two-dimensional fields" (3.5 The Kennicutt-Schmidt law at ~kpc-scales)
   - software: IDL HASTROM
   - assumption: _not stated_
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration and imaging  
  > "Data were reduced using Common Astronomy Software Applications" (2.2 ALMA observations & data reduction)
- **tclean** : deconvolution  
  > "We used the task tclean to deconvolve the data" (2.2 ALMA observations & data reduction)
- **GALFIT** : Sersic fit to CO moment 0  
  > "fitting a two-dimensional Sérsic model (cite: Sersic1963) to the CO intensity map (moment 0) using `GALFIT`" (3.3.1 Global Dynamical Properties)
- **emcee** : posterior sampling of alpha_CO and f_DM  
  > "using the EMCEE algorithm (cite: Foreman2013)" (3.4 Dynamical Mass & Dark Matter content)
- **MAGPHYS** : stellar masses (in earlier work)  
  > "the Bayesian SED fitting code, MAGPHYS (cite: daCunha2008)" (2.1 The SHiZELS Survey)
- **HASTROM (IDL)** : aligning 2D fields  
  > "we use the Interactive Data Language (IDL) procedure HASTROM to align the two-dimensional fields" (3.5 The Kennicutt-Schmidt law at ~kpc-scales)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SHiZELS-19 V_rot,CO | 121 | ±10 | km/s | 5 | / $V_{\rm rot,CO}$ (km s$^{-1}$)           /   121$\pm$10   /     / |
| SHiZELS-19 sigma_v,CO | 91 | ±6 | km/s | 6 | / $\sigma_{v,{\rm CO}}$ (km s$^{-1}$)      /   91$\pm$6    /     / |
| Best-fit inclination | 27.5 | ±0.6 | deg | 5 | / inc. (deg)                               / 27.5$\pm$0.6  /     / |
| M_dyn,thick (r<6 kpc) | 1.59e11 | ±0.19e11 | Msun | 8 | we obtain $M_{\rm dyn,thick} = (1.59\pm 0.19) \times 10^{11}$ $M_\odot$ |
| Dark matter fraction | 0.59 | ±0.10 | dimensionless | 8 | We find $f_{\rm DM} \approx 0.59\pm0.10$ for SHiZELS-19. |
| Median depletion time | 2.3 | ±1.2 | Gyr | 9 | We derive a median $\tau_{\rm dep}=2.3 \pm 1.2$ Gyr for this galaxy |
| k5,v/k1,v CO | 0.04 | ±0.01 | dimensionless | 7 | We obtain an average $k_{5,v}/k_{1,v}$ ratio of 0.04$\pm$0.01 and 0.09$\pm$0.05 for the CO and H$\alpha$ velocity map respectively. |
| tau_dep/tau_orb | ~9 | ±5 | dimensionless | 9 | we obtain $\tau_{\rm orb} = 256\pm22$ Myr and $\tau_{\rm dep}/\tau_{\rm orb} \sim 9 \pm 5$ |

## Qualitative findings

- SHiZELS-8 is dynamically perturbed: Halpha and CO PAs offset by ~100-120 deg.  
  > "position angles offset by $\sim 100-120$ deg" (3.2 The SHiZELS-8 galaxy)

## Claim tuples

- H: Do CO and Halpha trace the same kinematics in SHiZELS-19? | E: Joint 2D kinematic model at matched 0.15'' resolution | R: r1/2 ratio 1.07±0.09, Vrot/sigma 0.99 and 1.33, PA agree within 1 sigma | F: Both phases show similar extent, rotation and dispersion | **supported**
- H: Does SHiZELS-19 have a non-negligible dark matter fraction? | E: Thick-disk dynamical mass plus MCMC with alpha_CO of Narayanan+12 | R: f_DM = 0.59±0.10 | F: Non-negligible dark matter; consistent with Tiley+18 | **supported**
- H: Does a typical z~1.5 galaxy follow the local star formation law? | E: kpc-scale Sigma_SFR vs Sigma_H2 and depletion time | R: tau_dep = 2.3±1.2 Gyr vs 2.2±0.28 Gyr locally | F: Consistent with local law at denser ISM | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Narayanan+12 alpha_CO adopted since it includes gas density effects  
  > "we use the (cite: Narayanan2012)’s parametrization as it does consider the ISM density effect in the estimation of $\alpha_{\rm CO}$" (3.4 Dynamical Mass & Dark Matter content)
- Alternative: Thin-disk dynamical mass rejected (implies no gas); morphological quenching considered unlikely  
  > "this ‘thin disk’ dynamical mass value would suggest that this galaxy has almost no gaseous mass content" (3.4 Dynamical Mass & Dark Matter content)
- How they decided it was enough: _not stated_
- Limitation (authors): Conclusions highly dependent on the assumed alpha_CO  
  > "our conclusions are highly dependent on the assumed $\alpha_{\rm CO}$ value" (3.5 The Kennicutt-Schmidt law at ~kpc-scales)
- Limitation (authors): SHiZELS-8 CO S/N too low for detailed dynamics  
  > "Unfortunately the SHiZELS-8 CO(2-1) observations have too low S/N to allow a detailed dynamical characterization." (3.2 The SHiZELS-8 galaxy)
- Caveat (inferred, ours): Single resolved galaxy
- Caveat (inferred, ours): Strong alpha_CO-f_DM degeneracy
- Caveat (inferred, ours): Chi2_nu 3.51 indicates imperfect model
- Caveat (inferred, ours): Beam smearing and astrometry between ALMA and SINFONI

## Reproducibility

- Data public (paper): ALMA project codes cited in acknowledgements  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.01740.S, ADS/JAO.ALMA#2012.1.00402.S and ADS/JAO.ALMA#2015.1.00862.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: SINFONI H-alpha data and maps
- Missing: Hughes et al. CO fluxes
- Missing: Genetic algorithm and MCMC configuration
- Data volume (inferred): ~100-300 GB raw across three cycles
- Score (inferred): 3/5, ALMA imaging settings are well given but the kinematic modelling, MCMC priors and the Cycle 1/3 data are inherited or unstated, and H-alpha data are needed.
- Rediscovery candidate: no, Requires non-ALMA SINFONI data and unpublished companion results.

## Links

- Method: (cite: Swinbank2012a) (kinematic fitting approach)
- Method: (cite: Burkert2010) (thick-disk dynamical mass)
- Method: (cite: Krajnovic2006) (kinemetry)
- Method: (cite: Narayanan2012) (alpha_CO prescription)
- Companion: Hughes et al. in prep. (Cycle 1/3 ALMA CO data and fluxes)
- Companion: (cite: Molina2017) (Halpha kinematics of SHiZELS-19)
- Companion: (cite: Gillman2019) (stellar masses, SFRs, HST morphology)
- Related: SHiZELS
- Related: HiZELS

## Checks

```json
{
 "quotes": 79,
 "quotes_ok": 79,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2018.1.01740.S"
 ],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 99,
  "stated": 58,
  "rate": 0.586
 },
 "evidence_ok": true
}
```

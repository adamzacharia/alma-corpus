# Revealing the intermediate-mass black hole at the heart of the dwarf galaxy NGC 404 with sub-parsec resolution ALMA observations

`2020MNRAS.496.4061D` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Davis, Timothy A. | arXiv: 2007.05536 | DOI: 10.1093/mnras/staa1567

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: What is the mass of the intermediate-mass black hole in NGC 404 once the molecular gas contribution to the potential is included, using sub-parsec ALMA CO(2-1) kinematics plus stellar kinematics?  
  > "we not only obtain an independent estimate of the BH mass using the kinematics of the cold molecular material" (Introduction)
- Target **NGC 404**: coordinates ICRS 01h09m27.001s, +35d43m04.942s (ALMA phase centre)  
  > "We assume a distance of 3.06 $\pm$ 0.37 Mpc to NGC 404 (cite: 2002A&A...389..812K), yielding a physical scale of 14.8 pc arcsec$^{-1}$." (Introduction); "International Celestial Reference System (ICRS) position 01$^{\rm h}$09$^{\rm m}$27$.\!\!^{\rm s}$001, +35$^{\circ}$43$^{\prime}$04$.\!\!^{\prime\prime}$942." (2.1 Line emission); z/distance 3.06 ± 0.37 Mpc  
  > "We assume a distance of 3.06 $\pm$ 0.37 Mpc to NGC 404 (cite: 2002A&A...389..812K), yielding a physical scale of 14.8 pc arcsec$^{-1}$." (Introduction); "International Celestial Reference System (ICRS) position 01$^{\rm h}$09$^{\rm m}$27$.\!\!^{\rm s}$001, +35$^{\circ}$43$^{\prime}$04$.\!\!^{\prime\prime}$942." (2.1 Line emission); distance from tip of the red giant branch (cite: 2002A&A...389..812K)  
  > "We assume a distance of 3.06 $\pm$ 0.37 Mpc to NGC 404 (cite: 2002A&A...389..812K), yielding a physical scale of 14.8 pc arcsec$^{-1}$." (Introduction); "International Celestial Reference System (ICRS) position 01$^{\rm h}$09$^{\rm m}$27$.\!\!^{\rm s}$001, +35$^{\circ}$43$^{\prime}$04$.\!\!^{\prime\prime}$942." (2.1 Line emission)

## Data provenance

- ALMA projects: 2015.1.00597.S, 2017.1.00572.S, 2017.1.00907.S
- bands: 12CO(2-1) plus continuum at mean 237 GHz (about 1 mm)  
  > "We imaged the continuum emission of NGC 404 at a mean frequency of 237 GHz" (2.2 Continuum emission)
- frequencies and spectral setup: one 1850 MHz window on CO(2-1), raw channel ~0.6 km/s; three 2 GHz continuum windows  
  > "an 1850 MHz correlator window was placed over the $^{12}$CO(2–1) line" (2 ALMA data); "Three additional 2 GHz-wide low-resolution correlator windows were simultaneously used to probe continuum emission." (2 ALMA data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: high-res cube 0.051"x0.026" PA -10 deg (0.54 pc); combined cube 0.078"x0.037" PA 21 deg (0.8 pc)  
  > "This yields a synthesised beam of 0$.\!\!^{\prime\prime}$051 $\times$ 0$.\!\!^{\prime\prime}$026 at a position angle of $-10^{\circ}$" (2 ALMA data)
- max recoverable scale: _not stated_
- sensitivity: 0.79 mJy/beam/channel (high-res), 0.61 mJy/beam/channel (combined), 17 uJy/beam continuum  
  > "an RMS noise of 0.79 mJy beam$^{-1}$ channel$^{-1}$" (2 ALMA data); "The resulting continuum image has an RMS noise of 17$\mu$Jy beam$^{-1}$." (2.2 Continuum emission)
- time on source: _not stated_
- observing dates: 31 Oct 2015 (twice), 5 Sep 2015, 16 Jun 2018, 3 Sep 2018  
  > "observed with an extended ALMA configuration twice on 31st October 2015" (2 ALMA data); "Two additional lower resolution tracks were obtained on 16th June and 3rd September 2018" (2 ALMA data)
- pi or archival as stated: 2015.1.00597.S data previously presented by Nguyen et al. 2017; additional tracks included  
  > "These data, which detected the central disc in this object, were presented in (cite: 2017ApJ...845...50N)." (2 ALMA data)
- Line: 12CO J=2-1 (not stated)
- Other facility **HST**: F336W and Halpha+[NII] images for overlays; stellar MGE built from HST images  
  > "Figure [3](#ALMA_HST_over) shows moment zero contours over-plotted on *Hubble Space Telescope* (*HST*) images" (2.1 Line emission)
- Other facility **Gemini**: stellar kinematics used in JAM modelling  
  > "the edge of the field of view of the Gemini data used to measure the stellar kinematics" (3 Stellar kinematic modelling)
- External data: Stellar MGE mass model of NGC 404 from HST images, with pixel-by-pixel M/L  
  > "We use here the MGE model of the stellar mass distribution from (cite: 2017ApJ...836..237N), constructed from *HST* images of the nucleus" (3 Stellar kinematic modelling) [from (cite: 2017ApJ...836..237N)]
- External data: Stellar kinematics data (Vrms profile) from Gemini  
  > "the one-dimensional radial profile of the RMS observed velocity (${V}_{\mathrm{rms}}$) (as presented in (cite: 2017ApJ...836..237N))" (3 Stellar kinematic modelling) [from (cite: 2017ApJ...836..237N)]
- External data: CO(1-0) flux density used for CO(2-1)/CO(1-0) ratio ~0.6  
  > "presented a low-resolution map of CO(1-0) in this source, and combining their observed flux density with our own suggests a CO(2-1)/CO(1-0) ratio in beam temperature units of $\approx$0.6" (2.1 Line emission) [from (cite: 2015AJ....149..187T)]
- External data: Distance 3.06 Mpc  
  > "We assume a distance of 3.06 $\pm$ 0.37 Mpc to NGC 404 (cite: 2002A&A...389..812K)" (Introduction) [from (cite: 2002A&A...389..812K)]

## Processing

### Calibration

- pipeline or manual: manual calibration scripts in CASA  
  > "The raw ALMA data were calibrated using manual calibration scripts in the `Common Astronomy Software Applications` (`CASA)` package." (2 ALMA data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0238+1636 (flux); J2253+1608, J0237+2848, J0112+3522, J0112+3208 phase/bandpass  
  > "while flux calibration was performed using quasar J0238+1636." (2 ALMA data)
- flux scale uncertainty: ~10%  
  > "This error is dominated by the $\approx$10% flux calibration uncertainties." (2.1 Line emission)
- self calibration: _not stated_

### Imaging

- task: CASA; tracks combined and imaged  
  > "We used the `CASA` package to combine and image the visibility files of the different tracks." (2 ALMA data)
- deconvolver: multi-scale clean, scales for point sources and 3, 6, 9 times the beam; threshold 2x dirty-channel RMS  
  > "cleaning scales optimised for point sources, and emission with a characteristic scale 3, 6 and 9 times the synthesised beam" (2 ALMA data); "to a threshold equal to twice the root-mean square (RMS) noise of the dirty channels" (2 ALMA data)
- weighting robust: Briggs robust 0.5 (three long-baseline tracks); robust 0.1 (all tracks)  
  > "imaged using Briggs weighting (robust parameter 0.5)" (2 ALMA data); "imaged using Briggs weighting (robust parameter 0.1)" (2 ALMA data)
- uv taper: continuum tapered, beam 0.67"x0.46"  
  > "additionally tapered the data in the $uv$-plane (yielding a synthesised beam of 0$.\!\!^{\prime\prime}$67 $\times$ 0$.\!\!^{\prime\prime}$46" (2.2 Continuum emission)
- cell size: 0.015" pixels, 2 km/s channels  
  > "Both datasets use a channel width of 2 km s$^{-1}$ and pixels of 0$.\!\!^{\prime\prime}$015$\times$0$.\!\!^{\prime\prime}$015." (2 ALMA data)
- image size: _not stated_
- masking: cleaned in regions of source emission identified interactively  
  > "This dirty cube was cleaned in regions of source emission (identified interactively)" (2 ALMA data)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub in uv-plane  
  > "continuum emission was detected, and subtracted in the $uv$-plane using the CASA task *uvcontsub*" (2 ALMA data)
- line free channels: _not stated_
- primary beam correction: applied to final cube  
  > "The resulting cube was then corrected for the primary beam response." (2 ALMA data)
- array combination: all tracks (long and shorter baseline) combined in visibility space for second dataset  
  > "The second combined dataset was produced from all available ALMA tracks" (2 ALMA data)
- smoothing: _not stated_
- final beam: 0.051"x0.026" (high-res); 0.078"x0.037" (combined)  
  > "This yields a synthesised beam of 0$.\!\!^{\prime\prime}$078 $\times$ 0$.\!\!^{\prime\prime}$037 at a position angle of 21$^{\circ}$" (2 ALMA data)
- final rms: 0.79 and 0.61 mJy/beam/channel  
  > "an RMS noise of 0.61 mJy beam$^{-1}$ channel$^{-1}$" (2 ALMA data)

### Inherited from earlier work

- Stellar kinematic modelling procedure, JAM fitting details  
  > "Full details of the fitting procedure can be found in (cite: 2017ApJ...836..237N) and (cite: 2019ApJ...872..104N)." (3 Stellar kinematic modelling) [from (cite: 2017ApJ...836..237N); (cite: 2019ApJ...872..104N)]
- Masked moment technique for moment maps  
  > "created from the combined datacube using a masked moment technique (see (cite: 2011arXiv1101.1499D))" (2.1 Line emission) [from (cite: 2011arXiv1101.1499D)]
- Chi-squared variance correction of log-likelihood  
  > "To achieve the same effect within our Bayesian MCMC approach we need to scale the log-likelihood, as done by (cite: 2017MNRAS.464.4789M)." (4.4 Bayesian analysis) [from (cite: 2009MNRAS.398.1117V); (cite: 2017MNRAS.464.4789M); (cite: 2019MNRAS.485.4359S)]
- Galactic CO-to-H2 conversion factor 3e20  
  > "a Galactic CO-to-H$_2$ conversion factor of 3$\times$10$^{20}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$ (cite: 1986ApJ...309..326D)" (3 Stellar kinematic modelling) [from (cite: 1986ApJ...309..326D)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for uvcontsub and continuum imaging
- Image size and cube velocity range/imaging details, mask definition, CASA version
- Which tracks form the 'three long baseline tracks' and their execution blocks/uv-tapering parameters
- Moment mask threshold
- Exact MCMC step sizes, convergence criterion and KinMS settings
- Exact pixel selection for N=12,112 and radial range of fit
- Interpolation of potential and hot-H2/JAM chain details in this paper's re-run
- Systemic velocity from optical analysis used for prior

## Analysis recipe

1. **Calibrate, combine and image CO(2-1) and continuum**: Manual CASA calibration, uvcontsub, multiscale clean of combined tracks, primary-beam correction; two cubes (robust 0.5 long baselines; robust 0.1 all tracks)  
  > "In this work we make use of two different sets of CO(2-1) data products." (2 ALMA data)
   - software: CASA
   - parameter: robust 0.5 / 0.1; 2 km/s channels; 0.015" pixels; clean threshold 2x RMS  
  > "Both datasets use a channel width of 2 km s$^{-1}$ and pixels of 0$.\!\!^{\prime\prime}$015$\times$0$.\!\!^{\prime\prime}$015." (2 ALMA data)
   - fitting: _not stated_
   - validation: Compared combined-cube flux with ACA total flux (174±17 vs 161±16 Jy km/s)  
  > "We derive a total CO(2-1) flux of $174\pm17$ Jy km s$^{-1}$ from these data, in agreement with the estimate from our combined dataset." (2.1 Line emission)
2. **Moment maps, PVD and continuum source measurement**: Masked moment maps from combined cube; major-axis PVD at PA 37 deg, 5 pixel width; tapered continuum image with source fluxes  
  > "A major-axis position-velocity diagram (PVD) was extracted from the same data cube with a position angle of 37$^{\circ}$" (2.1 Line emission)
   - fitting: _not stated_
   - validation: _not stated_
3. **Stellar kinematic JAM fit including molecular gas potential**: MGE of gas surface density (MGEFIT) added to stellar MGE; JAM fit to Gemini kinematics with free BH mass, anisotropy, inclination, stellar normalisation Gamma  
  > "The free parameters of this fit are the BH mass, orbital anisotropy, inclination of the system and stellar mass normalisation factor $\Gamma$" (3 Stellar kinematic modelling)
   - software: MGEFIT, JAM
   - parameter: flat priors (log flat for BH mass), ranges in Table 2; 3 million iterations  
  > "based on 3 million iterations" (3 Stellar kinematic modelling)
   - assumption: Galactic CO-to-H2 factor 3e20; CO(2-1)/CO(1-0)~0.6; HI negligible; distance 3.06 Mpc  
  > "We have assumed that the mass of any H present around the nucleus of NGC 404 is negligible." (3 Stellar kinematic modelling)
   - fitting: MCMC; flat priors; chi2_red=1.23 over 920 dof  
  > "reduced-chi$^2$ $\chi^2_{\rm red}=1.23$ over 920 degrees of freedom" (3 Stellar kinematic modelling)
   - validation: Compared Vrms profile for models with different BH masses  
  > "Figure [8](#stellar1drms) shows the one-dimensional radial profile of the RMS observed velocity" (3 Stellar kinematic modelling)
4. **Build gas distribution and potential for gas kinematic model**: SKYSAMPLER samples clean components with 1e6 point sources; potential via IDL POTENTIAL_NEWTON from symmetrised cloudlets in thin warped disc  
  > "that samples the observed clean components with an arbitrary number of point sources ($10^6$ in this case)" (4.1 Gas distribution)
   - software: SKYSAMPLER, IDL POTENTIAL_NEWTON
   - assumption: thin disc; each cloudlet equal mass fraction  
  > "assuming each cloudlet has an equal fraction of the total gas mass" (4.2 Mass model)
   - fitting: _not stated_
   - validation: MGE-based potential gives same results  
  > "our results would not have changed" (4.2 Mass model)
5. **Forward-model gas kinematics to measure BH mass**: KinMS with KinMS_MCMC fit to the high-res cube within 0.25" (3.7 pc); circular rotation, constant dispersion, BH point mass plus stars (Gamma prior) plus gas  
  > "To do this we concentrate on the molecular gas disc/torus within a radius of 0$.\!\!^{\prime\prime}$25 (or $\approx$3.7 pc) from the centre of NGC 404." (4 Molecular gas kinematic modelling)
   - software: KinMS, KinMS_MCMC, SKYSAMPLER
   - parameter: log MBH prior uniform 4.0-6.9; Gamma Gaussian (0.61, 0.11); inclination Gaussian (37, 3); noise scaled by (2N)^(1/4)=12.47 with N=12,112  
  > "this equates to increasing the RMS by a factor of 12.47" (4.4 Bayesian analysis)
   - assumption: circular orbits, thin disc, constant velocity dispersion, no dark matter  
  > "In this work we assume that the molecular gas is in circular motion" (4.3 Gas kinematics)
   - fitting: MCMC with Gibbs sampling and adaptive stepping; log-likelihood -chi2/2 plus log priors; final chain 300,000 steps with 10% burn-in; median and 68%/99% CLs  
  > "the best chain is run (with a fixed step size) for 300,000 steps (with a 10% burn-in)" (4.4 Bayesian analysis)
   - validation: PVDs and velocity-field residuals; models with no BH or >1e6 Msun fail  
  > "a model without an IMBH cannot provide a good fit to our data, nor can a BH of mass $\raisebox{-0.6ex}{$\,\stackrel{\raisebox{-.2ex}{$\textstyle >$}}{\sim}\,$}10^6$ M$_{\odot}$" (4.4 Bayesian analysis)
6. **Test systematic uncertainties**: Velocity dispersion gradient, asymmetric drift estimate, free disc thickness, varying alpha_CO, Gamma prior removal  
  > "we ran a further fitting procedure where the thickness of the disc was allowed to vary" (4.5 Uncertainties)
   - software: KinMS
   - fitting: _not stated_
   - validation: Asymmetric drift <5%; z_h<1.3 pc; alpha_CO 0.1-10 does not affect gas result  
  > "allowing $\alpha_{\rm CO}$ to vary over a large range (0.1 $< \alpha_{\rm CO} <$ 10 M$_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$) in our fitting procedure does not significantly affect the best-fitting BH mass" (4.5 Uncertainties)

## Software

- **CASA** : calibration, uvcontsub, combining and imaging  
  > "We used the `CASA` package to combine and image the visibility files of the different tracks." (2 ALMA data)
- **MGEFIT** : MGE of molecular gas surface density  
  > "using the python MGEFIT package to fit the molecular gas surface density map" (3 Stellar kinematic modelling)
- **JAM** : Jeans anisotropic modelling of stellar kinematics  
  > "using the Jeans anisotropic modelling (JAM) code of (cite: 2008MNRAS.390...71C)" (3 Stellar kinematic modelling)
- **KinMS** : forward-modelling mock ALMA cubes  
  > "we use the Kinematic Molecular Simulation (KINMS) mm-wave observation simulation tool of (cite: 2013MNRAS.429..534D)" (4 Molecular gas kinematic modelling)
- **KinMS_MCMC** : MCMC fitting  
  > "coupled to the Markov Chain Monte Carlo (MCMC) code KINMS_MCMC" (4 Molecular gas kinematic modelling)
- **SKYSAMPLER** : sampling clean components as point sources  
  > "We use the publicly available SKYSAMPLER python code of (cite: 2019MNRAS.485.4359S)" (4.1 Gas distribution)
- **IDL POTENTIAL_NEWTON** : gravitational potential of gas cloudlets  
  > "calculated using the Interactive Data Language (IDL) POTENTIAL_NEWTON routine" (4.2 Mass model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(2-1) integrated flux (inner 8"x8", combined) | 161 | 16 | Jy km/s | 1 | we find an integrated line flux of $161\pm16$ Jy km s$^{-1}$ within the inner 8$^{\prime \prime}$$\,\times$ 8$^{\prime \prime}$ |
| CO(2-1) flux from ACA | 174 | 17 | Jy km/s | 1 | We derive a total CO(2-1) flux of $174\pm17$ Jy km s$^{-1}$ from these data |
| Flux resolved out in high-res dataset | 74 | not stated | percent | 1 | The high-resolution dataset resolves out 74% of this emission |
| Continuum flux, central source A | 0.38 | 0.02 | mJy | 2 | / Centre + arm / A / 01:09:26.999 / +35:43:05.02 / 1$.\!\!^{\prime\prime}$55 $\times$ 0$.\!\!^{\prime\prime}$9 / 23 $\times$ 13 / 0.38$\pm$0.02 / |
| Stellar-kinematic BH mass | 5.1e5 | +3.9/-2.4 (68%) | Msun | 3 | We find that the best-fitting BH mass of NGC 404 is 5.1$^{+3.9}_{-2.4}\times$10$^5$ M$_{\odot}$ |
| Stellar mass normalisation Gamma (stellar fit) | 0.61 | ±0.11 (68%) | dimensionless | 3 | the stellar mass normalisation factor is $\Gamma=0.61\pm0.11$ (at the 68% confidence level) |
| Gas mass within 0.25" (3.7 pc) | 2.5e5 | 0.3e5 | Msun | 4 | the total molecular gas mass is (2.5$\pm$0.3)$\times$10$^5$ M$_{\odot}$ |
| Gas-kinematic BH mass | 5.5e5 | +4.1/-3.8 (99% CL) | Msun | 5 | with a mass of 5.5$^{+4.1}_{-3.8}\times$10$^5$ M$_{\odot}$ (at the 99% CL) |
| Gas disc inclination (fit) | 37.1 | -0.46,+0.57 (68%) | deg | 5 | / Inclination ($^\circ$)                          / $N$($\mu$=37, $\sigma$=3)                               / 37.1     / $-$ 0.46, + 0.57      / $-$ 1.76, + 1.61      / |
| Gas velocity dispersion | 12.9 | ±0.9 (68%) | km/s | 5 | / Gas velocity dispersion ($\sigma$; km s$^{-1}$) / 0.0        / $\xrightarrow[]{\rm uniform}$ / 20.0       / 12.9     / $-$ $\pm$0.9          / $-$ 2.7, + 3.6        / |
| Disc scale-height limit | <1.3 | 1 sigma limit | pc | 6 | We are, however, able to set a 1$\sigma$ limit to the Gaussian scale-height in the vertical direction of $z_{\rm h}$\<1.3 pc |
| Sphere-of-influence radius | 0.1 (~1.4 pc) | not stated | arcsec | 0 | In NGC 404 this equates to 0$.\!\!^{\prime\prime}$1 (or $\approx$1.4 pc). |

## Qualitative findings

- Central disc/torus of molecular gas within ~5 pc rotates around the BH, surrounded by a warped arm and incomplete ring of radius ~40 pc  
  > "The disc itself is rotating around the IMBH, but is surrounded by kinematically-distinct lopsided emission that appears connected to an arm-like feature." (5.1 Gas morphology)
- Continuum likely dominated by Rayleigh-Jeans dust emission  
  > "We consider it likely that the majority of this emission is from the Rayleigh-Jeans tail of the dust continuum" (5.2 Continuum emission)

## Claim tuples

- H: Including the molecular gas potential reconciles stellar-kinematic BH mass with gas-based estimates | E: JAM re-fit with MGE of gas added to the stellar mass model | R: MBH = 5.1e5 Msun (+3.9/-2.4), Gamma=0.61 | F: Gas contribution raises the stellar-kinematic BH mass above the earlier upper limit | **supported**
- H: Cold molecular gas kinematics independently require an IMBH | E: KinMS forward modelling of the 0.54 pc cube within 3.7 pc | R: MBH = 5.5e5 Msun (+4.1/-3.8, 99%) | F: A dark object is clearly detected; no-BH and >1e6 Msun models fail | **supported**
- H: Systematics do not bias the gas-based BH mass | E: Tests of thickness, dispersion gradient, asymmetric drift, alpha_CO | R: z_h<1.3 pc, drift <5%, alpha_CO insensitivity | F: Geometry and conversion factor do not significantly bias result, but depends on stellar model and Gamma | **partially**

## Reasoning

- Why this data: High resolution resolves BH sphere of influence but resolves out flux, so combined data used for morphology  
  > "This dataset allows us to image the central disc at the highest spatial resolution possible, but it does not recover all the flux." (2 ALMA data)
- Why this method: Clean-component gas distribution used because gas is clearly not axisymmetric  
  > "As the molecular gas distribution in NGC 404 is clearly not axisymmetric we here utilise a different approach" (4.1 Gas distribution)
- Alternative: Single unwarped disc model gives no significant change in parameters  
  > "Using a simple single un-warped disc model does not result in a significant change in any of the derived parameters" (4.3 Gas kinematics)
- How they decided it was enough: _not stated_
- Limitation (authors): Keplerian rise not resolved; result depends on stellar mass model and Gamma  
  > "given that we do not resolve the Keplerian increase of the circular velocity around the BH" (4.5 Uncertainties)
- Limitation (authors): Low Gamma should be treated with caution; beam correlations neglected  
  > "We therefore suggest that the low $\Gamma$ value should be treated with caution." (5.4 Stellar mass normalisation)
- Caveat (inferred, ours): Mass depends on stellar M/L normalisation prior from stellar fit, creating partial non-independence of the two methods
- Caveat (inferred, ours): Noise inflation by (2N)^(1/4) is ad hoc and controls quoted uncertainties
- Caveat (inferred, ours): Correlated pixels ignored; circular motions assumed
- Caveat (inferred, ours): Distance uncertainty (12%) not folded into errors
- Caveat (inferred, ours): Abstract/conclusion quote differing stellar BH-mass errors (Table vs text)

## Reproducibility

- Data public (paper): ALMA data acknowledged by project code; codes public (KinMS etc. on GitHub)  
  > "This paper makes use of the following ALMA data:" (Acknowledgments)
- Products in archive: _not stated_
- Code: KinMS, KinMS_MCMC and SKYSAMPLER on GitHub  
  > "https://github.com/TimothyADavis/KinMS" (footnote 3)
- Missing: Calibration scripts/CASA version
- Missing: Line-free channel selection
- Missing: Stellar kinematic data and JAM chain setup (from Nguyen et al. 2017)
- Missing: Exact fit masks and MCMC settings
- Data volume (inferred): ~several hundred GB raw for five long/short tracks plus ACA; cubes few GB
- Score (inferred): 3/5, Data public and software released with priors and settings stated, but stellar kinematic inputs and several imaging details come from other papers or are missing.
- Rediscovery candidate: no, Needs external stellar kinematic and mass-model inputs and heavy calibration/imaging with unspecified details.

## Links

- Method: (cite: 2013MNRAS.429..534D) (KinMS)
- Method: (cite: 2019MNRAS.485.4359S) (SKYSAMPLER and chi2 variance correction)
- Method: (cite: 2008MNRAS.390...71C) (JAM)
- Companion: (cite: 2017ApJ...845...50N) (earlier ALMA data and radio continuum of NGC 404)
- Companion: (cite: 2017ApJ...836..237N) (stellar kinematics and mass model)
- Companion: Liu et al. (in prep) (molecular cloud properties)
- Related: WISDOM

## Checks

```json
{
 "quotes": 97,
 "quotes_ok": 97,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 90,
  "stated": 69,
  "rate": 0.767
 },
 "evidence_ok": true
}
```

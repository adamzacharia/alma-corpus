# The observational impact of dust trapping in self-gravitating discs

`2020MNRAS.498.4256C` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Cadman, James | arXiv: 2008.09826 | DOI: 10.1093/mnras/staa2596

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Can self-gravitating discs with dust trapping in spiral arms produce spiral substructure observable with ALMA, and can GI explain the spirals in Elias 27, WaOph 6 and IM Lup?  
  > "We present a 3D semi-analytic model of self-gravitating discs, and include a prescription for dust trapping in the disc spiral arms." (abstract); "We use our models to investigate if the observed substructure in these 3 systems can be explained through the gravitational instability" (8 Analysing discs from the DSHARP sample)
- Target **Elias 27**: coordinates _not stated_; z/distance 116 (+19/-10) pc  
  > "at a distance $d=116^{+19}_{-10}$ pc (cite: gaiaDR2; dsharp1)" (Elias 27); distance from Gaia DR2 / DSHARP I (cite: gaiaDR2; dsharp1)  
  > "at a distance $d=116^{+19}_{-10}$ pc (cite: gaiaDR2; dsharp1)" (Elias 27)
- Target **WaOph 6**: coordinates _not stated_; z/distance 123 +/- 2 pc  
  > "at a distance $d=123\pm2$ pc (cite: gaiaDR2; dsharp1)" (WaOph 6); distance from Gaia DR2 / DSHARP I (cite: gaiaDR2; dsharp1)  
  > "at a distance $d=123\pm2$ pc (cite: gaiaDR2; dsharp1)" (WaOph 6)
- Target **IM Lup**: coordinates _not stated_; z/distance 158 +/- 3 pc  
  > "at a distance $d=158\pm3$ pc (cite: gaiaDR2; dsharp1)" (IM Lup); distance from Gaia DR2 / DSHARP I (cite: gaiaDR2; dsharp1)  
  > "at a distance $d=158\pm3$ pc (cite: gaiaDR2; dsharp1)" (IM Lup)
- Target **Model Taurus-like discs (synthetic)**: coordinates _not stated_; z/distance 140 pc (assumed)  
  > "We consider discs at a distance of 140pc, comparable to those in the Taurus star forming region." (6 Disc Models: Parameters); distance from assumed, comparable to Taurus  
  > "We consider discs at a distance of 140pc, comparable to those in the Taurus star forming region." (6 Disc Models: Parameters)

## Data provenance

- ALMA projects: _none stated_
- bands: Synthetic: Bands 3, 6 and 9 (115, 230, 690 GHz); DSHARP discs simulated at 240 GHz  
  > "corresponding to ALMA observing bands 3, 6 and 9 respectively." (6 Disc Models: Parameters); "240 GHz" (Table 3)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: ALMA Cycle 7 array configurations (simulated)  
  > "We use ALMA cycle 7 array configurations to produce these images" (3 ALMA Simulations: CASA)
- configurations: alma.cycle7.8 (115, 230 GHz), alma.cycle7.6 (690 GHz); C40-8 for DSHARP discs (simulated)  
  > "alma.cycle7.6" (Table 2); "using array configuration C40-8" (8 Analysing discs from the DSHARP sample)
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 1800 s per synthetic observation of model discs; 3600 s for DSHARP-like discs (simulated)  
  > "1800 s" (Table 2); "We observe each disc for $t_{\rm obs}=3600$ s using array configuration C40-8." (8 Analysing discs from the DSHARP sample)
- observing dates: _not stated_
- pi or archival as stated: Real data: DSHARP ALMA continuum images of Elias 27, WaOph 6 and IM Lup (survey data); main results are synthetic observations  
  > "The recent DSHARP survey studied 20 nearby protoplanetary discs using ALMA, with 3 of these discs exhibiting spiral substructure" (8 Analysing discs from the DSHARP sample)
- Other facility **DSHARP ALMA survey**: ALMA continuum images of Elias 27, WaOph 6 and IM Lup, and derived disc and spiral parameters  
  > "The ALMA continuum images from this survey of the Elias 27, WaOph 6 and IM Lup discs are shown in" (8 Analysing discs from the DSHARP sample)
- Other facility **Gaia DR2**: Distances to the three DSHARP discs  
  > "at a distance $d=116^{+19}_{-10}$ pc (cite: gaiaDR2; dsharp1)" (Elias 27)
- External data: Stellar and accretion parameters (M*, Teff, Mdot) and disc geometry (inclination, PA, distance, spiral radii) for Elias 27, WaOph 6, IM Lup  
  > "we simply model these 3 systems using the disc parameters derived in (cite: dsharp1) and (cite: dsharp3)" (8 Analysing discs from the DSHARP sample) [from (cite: dsharp1); (cite: dsharp3)]
- External data: Spiral shape parameters a and b for the DSHARP discs, with best-fit values adapted from DSHARP quotes  
  > "Best-fit values of $a$ and $b$ that we find from those quoted in (cite: dsharp3)" (8 Analysing discs from the DSHARP sample) [from (cite: dsharp3)]
- External data: Maximum viscous alpha = 0.06 for self-gravitating discs  
  > "the viscous stress will saturate at a maximum value $\alpha=0.06$ (cite: riceetal05)" (5 Grain Growth and the Fragmentation Threshold) [from (cite: riceetal05)]
- External data: Equation of state for T, gamma and opacity  
  > "using the equation of state from (cite: stamatellosetal07)" (2.1 Self-gravitating Disc Models) [from (cite: stamatellosetal07)]
- External data: Silicate grain optical properties  
  > "represent our grains as (cite: drainelee) silicates" (6 Disc Models: Parameters) [from (cite: drainelee)]
- Simulation/model as data: Semi-analytic 3D self-gravitating disc models (Q=2, spirals, dust trapping) turned into continuum images with TORUS, then synthetic ALMA observations with CASA  
  > "The output continuum images from TORUS are then used as inputs to the ALMA simulator in the Common Astronomy Software Application (CASA) package" (3 ALMA Simulations: CASA)
- Simulation/model as data: PHANTOM SPH self-gravitating discs with dust particles used to calibrate the peak dust concentration factor d  
  > "we employ the 3D SPH code PHANTOM (cite: priceetal18) to numerically model the behaviour of dust particles in self-gravitating discs" (4 SPH Models)

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

- task: CASA simobserve and simanalyze on simulated model images  
  > "We then use these continuum disc images as inputs to the CASA tasks SIMOBSERVE and SIMANALYZE and generate synthetic ALMA observations." (6 Disc Models: Parameters)
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
- smoothing: Unsharp masking: subtract a 2D Gaussian of FWHM matched to the beam, scaled with the peak image flux  
  > "We subtract a 2D Gaussian profile of FWHM closely matched to the beam size of our simulated images" (3 ALMA Simulations: CASA)
- final beam: 0.05"x0.05" (Gaussian used for unsharp masking, matched to simulated beam)  
  > "FWHM closely matched to the beam size of our simulated images (we use 0.05"x0.05" here)" (3 ALMA Simulations: CASA)
- final rms: _not stated_

### Inherited from earlier work

- Semi-analytic self-gravitating disc formalism and its 3D radiative transfer / ALMA simulator approach  
  > "In this paper we build on previous work by (cite: halletal16) who developed a semi-analytic formalism for determining the structure of self-gravitating protostellar discs" (1 Introduction) [from (cite: halletal16)]
- Spiral shape constants a=13.5 and b=0.38 for the generic models  
  > "Here we use $a=13.5$ and $b=0.38$, in line with that used in (cite: halletal16)." (2.1 Self-gravitating Disc Models) [from (cite: halletal16)]
- CASA observing setups for DSHARP-like discs  
  > "We produce synthetic observations of each disc using CASA with observing setups consistent with those outlined in (cite: dsharp1)." (8 Analysing discs from the DSHARP sample) [from (cite: dsharp1)]
- Residual-image method: deprojection and subtraction of the median axisymmetric radial profile  
  > "Residual images in (cite: dsharp3) are produced by deprojecting the discs and subtracting their median axisymmetric radial profiles. We do the same here" (8 Analysing discs from the DSHARP sample) [from (cite: dsharp3)]

### Not stated but needed to reproduce (our reading)

- TORUS version and source code or input parameter files
- PHANTOM version and setup files, including exact dust-gas coupling choices and random seeds
- Exact simobserve/simanalyze parameters (cell size, image size, deconvolver, weighting, thermal noise settings, total bandwidth, pointing, spectral setup) for the synthetic observations
- Spiral amplitude/phase details used to mask and compute arm vs inter-arm regions for F_RMS ratios
- Exact gas-to-dust and opacity table settings used in TORUS beyond silicates (cite: drainelee)
- Mass and radial extent (R_out) setup of the generic Taurus-like discs beyond R_out=100 AU quoted in Section 5
- Model spiral mode numbers and inclination handling for the DSHARP disc models (inclination set to 0 in deprojection)
- Which DSHARP data products (calibrated visibilities or released images) were used for observed residuals

## Analysis recipe

1. **Build self-gravitating disc models with spirals**: 1D steady-state accretion disc with Q=2 at all radii, self-consistent alpha, Sigma, c_s; 3D structure with logarithmic spiral over-densities imposed sinusoidally; m ~ 1/q  
  > "Here we assume the disc to be marginally unstable with $Q=2$ at all radii." (2.1 Self-gravitating Disc Models); "In this way we are able to construct 3D axisymmetric discs for any desired $\dot{M}$ and disc size." (2.1 Self-gravitating Disc Models)
   - parameter: Q = 2; S = 2; a = 13.5, b = 0.38 (generic discs)  
  > "where here we define $S=2$" (2.1 Self-gravitating Disc Models); "Here we use $a=13.5$ and $b=0.38$, in line with that used in (cite: halletal16)." (2.1 Self-gravitating Disc Models)
   - parameter: T_irr = 10 K  
  > "we assume that irradiation leads to a constant background temperature, $T_{\rm irr}=10$ K" (2.1 Self-gravitating Disc Models)
   - assumption: Dust-to-gas ratio 0.01 over all grain sizes  
  > "Here we use the canonical value of $\langle\epsilon\rangle=0.01$ to represent the total dust-to-gas ratio over all grain sizes." (2.2 Grain Concentration)
   - fitting: _not stated_
   - validation: Compared with SPH in Hall et al. 2016  
  > "We refer the reader to (cite: halletal16) for a comparison of this simple functional formailsm’s ability to accurately reproduce self-gravitating spiral shape and amplitudes from SPH simulations." (2 Disc Models: Setup)
2. **Calibrate dust trapping with SPH**: PHANTOM SPH runs of q=0.2, 0.3, 0.4 discs with injected dust of 20 grain sizes; fit Gaussians to dust fraction in a 5 degree radial slice at the spiral to get peak dust-to-gas ratio and hence d  
  > "peak dust-to-gas ratios are determined by taking a radial slice of the disc, of azimuthal width $5^\circ$, and fitting a Gaussian distribution to the dust mass fraction at the spiral location." (4 SPH Models)
   - software: PHANTOM
   - parameter: 500,000 gas SPH particles; 125,000 dust particles  
  > "We use 500,000 SPH particles to represent the disc gas" (4 SPH Models); "We then inject a population of 125,000 dust SPH particles and allow the discs to evolve for a further orbital period." (4 SPH Models)
   - parameter: Adopted d = 5 for discs with q <~ 0.3  
  > "we assume a maximum value of $d=5$ in our models." (4 SPH Models)
   - assumption: Dust treated as test particles (no dust self-gravity); one-fluid for a <= 2 mm, two-fluid for a > 2 mm  
  > "we neglect the self-gravity of these dust particles and treat them as test particles only." (4 SPH Models)
   - fitting: Gaussian fit to dust mass fraction at the spiral; log-normal curves fit to peak dust-to-gas ratios vs grain size  
  > "we fit log-normal curves to the best-fit dust-to-gas ratio peaks from the $q=0.3$ and $q=0.4$ discs." (4 SPH Models)
   - validation: _not stated_
3. **Set maximum grain size from fragmentation threshold**: a_max from fragmentation-limited Stokes number with alpha = 0.06 for v_frag = 10 and 30 m/s  
  > "We use this to set our value of $a_{\rm max}$ in our disc models assuming two cases of $v_{\rm frag}=10$ ms$^{-1}$ and $v_{\rm frag}=30$ ms$^{-1}$." (5 Grain Growth and the Fragmentation Threshold)
   - parameter: alpha = 0.06  
  > "the viscous stress will saturate at a maximum value $\alpha=0.06$ (cite: riceetal05)" (5 Grain Growth and the Fragmentation Threshold)
   - assumption: Grains grow at least to the fragmentation threshold  
  > "This indicates that particles are able to grow to at least as large as the fragmentation threshold, and we therefore use this to define $a_{\rm max}$ in our models." (5 Grain Growth and the Fragmentation Threshold)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compute dust temperatures and continuum images**: TORUS Monte Carlo radiative equilibrium on an adaptive grid, then continuum images at 115, 230, 690 GHz  
  > "The dust temperatures are then calculated using the TORUS radiation transfer code (cite: harriesetal19)." (2.3 Monte Carlo Radiative Transfer: TORUS)
   - software: TORUS
   - parameter: 10^9 photon packets per cycle; cell split if mass > 1e-4 Msun  
  > "Our discs are illuminated by a central star, whose radiation field is here represented by $10^9$ photon packets." (2.3 Monte Carlo Radiative Transfer: TORUS); "If the mass in a cell exceeds $1\times 10^{-4}$ M$_{\odot}$ then we further subdivide each cell into $2^D$ child cells" (2.3 Monte Carlo Radiative Transfer: TORUS)
   - parameter: 50 grain sizes log-spaced from 0.1 micron to 2e6 micron; n(a) proportional to a^-3.5  
  > "We use 50 dust grain sizes distributed logarithmically between $0.1$ $\mu$m and $2\times10^{6}$ ${\rm \mu}$m" (6 Disc Models: Parameters)
   - assumption: Star M*=1 Msun, R*=2.325 Rsun, Teff=4350 K  
  > "Our central star is modelled with $M_{*}=1$ M$_{\odot}$, $R_{*}=2.325$ R$_{\odot}$ and $T_{\rm eff}=4350$ K." (6 Disc Models: Parameters)
   - fitting: _not stated_
   - validation: _not stated_
5. **Generate synthetic ALMA observations**: CASA simobserve and simanalyze with Cycle 7 configurations, PWV and integration times from Tables 2 and 3  
  > "We then use these continuum disc images as inputs to the CASA tasks SIMOBSERVE and SIMANALYZE and generate synthetic ALMA observations." (6 Disc Models: Parameters)
   - software: CASA
   - parameter: DSHARP-like discs: 240 GHz, 3600 s, C40-8, PWV 1.35/1.30/1.05 mm  
  > "We observe each disc for $t_{\rm obs}=3600$ s using array configuration C40-8." (8 Analysing discs from the DSHARP sample); "setting values 1.35mm, 1.30mm and 1.05mm for Elias 27, IM Lup and WaOph 6 respectively" (8 Analysing discs from the DSHARP sample)
   - assumption: Face-on discs at 140 pc for the generic suite  
  > "Note however that we are observing these discs face-on and therefore in favourable conditions for resolving spiral features." (7 Observing self-gravitating discs in Taurus)
   - fitting: _not stated_
   - validation: _not stated_
6. **Quantify spiral observability**: Unsharp masking for residual images; ratio of RMS flux in arm vs interarm regions between 70-100 AU on synthetic images before masking  
  > "we calculate the RMS fluxes between radii $70-100$ AU where we find spiral structure to be most prominent." (7 Analysing the impact of grain enhancement); "Flux ratios are calculated using the synthetic ALMA observations prior to unsharp masking." (7 Analysing the impact of grain enhancement)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared models with and without dust trapping  
  > "we plot how these flux ratios vary with mass accretion rate, and show comparison plots for models that do not include dust grain enhancement" (7 Analysing the impact of grain enhancement)
7. **Derive spectral index maps**: Pixelwise beta from fluxes at 460 and 100 GHz (power-law slope minus 2)  
  > "considering fluxes $\nu_1=460$ GHz and $\nu_2=100$ GHz, and discs with $\dot{M}=5\times10^{-7}$ M$_{\odot}$yr$^{-1}$ and $a_{\rm max}=1$ mm and $10$ cm." (7 Analysing the impact of grain enhancement)
   - assumption: Optically thin, Rayleigh-Jeans limit  
  > "In the Rayleigh-Jeans limit of an optically thin disc the dust opacity at sub-mm wavelengths will approximately scale as" (7 Analysing the impact of grain enhancement)
   - fitting: _not stated_
   - validation: _not stated_
8. **Compare models with DSHARP discs**: Model each disc with DSHARP parameters, a_max at v_frag = 10 m/s, spirals from DSHARP a,b, deproject and subtract the median radial profile in 1 AU bins for both observed and model images  
  > "We do the same here by binning each disc into $1$ AU-wide radial bins and subtracting the median azimuthal fluxes." (8 Analysing discs from the DSHARP sample)
   - software: CASA
   - parameter: n(a) a^-3.5, a_min = 0.1 micron, a_max = fragmentation threshold with v_frag = 10 m/s, dust-to-gas 0.01  
  > "set $a_{\rm max}$ as the fragmentation threshold where $v_{\rm frag}=10$ ms$^{-1}$" (8 Analysing discs from the DSHARP sample)
   - parameter: Inner 50 AU (Elias 27) masked to avoid washing out spirals  
  > "where we use a mask to remove the inner $50$ AU from our observations" (Elias 27)
   - fitting: No fit: parameters taken from DSHARP; not tuned to match  
  > "a complete examination of the potential parameter space of these discs is beyond the scope of the work presented here" (8 Analysing discs from the DSHARP sample)
   - validation: Qualitative comparison of model and observed deprojected and residual image fluxes on the same colour scale  
  > "each disc model and counterpart observation is plotted between the same flux range for ease of comparison" (8 Analysing discs from the DSHARP sample)

## Software

- **CASA** 5.1: ALMA simulator (simobserve, simanalyze) for synthetic observations  
  > "the ALMA simulator in the Common Astronomy Software Application (CASA) package (version 5.1)" (3 ALMA Simulations: CASA)
- **TORUS** : Monte Carlo radiative transfer for dust temperatures and continuum images  
  > "The dust temperatures are then calculated using the TORUS radiation transfer code (cite: harriesetal19)." (2.3 Monte Carlo Radiative Transfer: TORUS)
- **PHANTOM** : 3D SPH simulations of dust in self-gravitating discs to set peak dust concentration d  
  > "we employ the 3D SPH code PHANTOM (cite: priceetal18)" (4 SPH Models)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Peak dust concentration factor d from SPH (q=0.3, q=0.4) | 5 (q=0.3), 6 (q=0.4) | not stated | dimensionless | 2 | Grains become most concentrated for sizes $a\approx200-500$ mm, with peak dust-to-gas ratios $\epsilon\approx0.06$ and $\epsilon\approx0.07$ in the $q=0.3$ and $q=0.4$ discs respectively, giving values of $d\approx5$ and $d\approx6$ |
| Mean beta, a_max = 1 mm disc | 1.197 | not stated | dimensionless | 7 | We calculate mean $\beta$-values 1.197 and 0.525 for $a_{\rm max}=1$ mm and $a_{\rm max}=10$ cm respectively |
| Mean beta, a_max = 10 cm disc | 0.525 | not stated | dimensionless | 7 | We calculate mean $\beta$-values 1.197 and 0.525 for $a_{\rm max}=1$ mm and $a_{\rm max}=10$ cm respectively |
| Elias 27 model disc mass (within 230 AU) and q | M_disc = 0.13, q = 0.27 | not stated | Msun (mass); dimensionless (q) | 8 | Our model calculates Elias 27 to have a disc mass $M_{\rm disc}=0.13$ M$_{\odot}$ inside $R_{\rm out}=230$ AU, and therefore $q=0.27$. |
| WaOph 6 model disc mass and q | M_disc = 0.16, q = 0.24 | not stated | Msun (mass); dimensionless (q) | 8 | We calculate WaOph 6 to have a disc mass $M_{\rm disc}=0.16$ M$_{\odot}$ and therefore $q=0.24$. |
| IM Lup model disc mass (within 110 AU) and q | M_disc = 0.098, q = 0.11 | not stated | Msun (mass); dimensionless (q) | 8 | We calculate IM Lup to have a disc mass $M_{\rm disc}=0.098$ M$_{\odot}$ and $q=0.11$ within $R=110$ AU |
| Lowest disc-to-star mass ratio with distinguishable spirals (Taurus-like suite) | q = 0.1 | not stated | dimensionless | 6 | exhibit distinguishable spiral structure for disc masses as low as $q=0.1$ given sufficient grain growth. |

## Qualitative findings

- Spirals are observable only when the dust mass budget is dominated by mm/cm grains; with no grain growth or growth well beyond cm sizes, arm-interarm contrast is low  
  > "disc substructure becomes invisible at the ALMA bands considered here as the arm-interarm contrast is low." (7 Observing self-gravitating discs in Taurus)
- Dust trapping gives higher arm/interarm flux ratios than models without it  
  > "For the same disc parameters we calculate considerably higher flux ratios when including dust trapping in our model" (7 Analysing the impact of grain enhancement)
- The calculated fragmentation threshold coincides with the a_max best for detecting spirals  
  > "It is also intriguing that we calculate the fragmentation threshold to fall almost exactly coincident with the ideal" (7 Observing self-gravitating discs in Taurus)

## Claim tuples

- H: Dust trapping in spiral arms makes GI substructure observable in lower mass discs than previously predicted | E: Synthetic ALMA observations of model discs at 115, 230, 690 GHz across 9 accretion rates and several a_max, with and without dust trapping | R: Higher arm/interarm flux ratios with trapping; spirals distinguishable down to q = 0.10 for mm/cm-dominated dust | F: GI spirals may be detectable at lower disc masses than previously suggested if grains have grown to the fragmentation threshold | **supported**
- H: Grain size distribution determines whether GI spirals are detectable | E: Varied a_max from 10 micron to 100 cm in the model suite | R: Substructure invisible for micron-dominated or metre-dominated dust | F: Observable spirals require mm/cm-sized dominated dust mass | **supported**
- H: Multi-wavelength observations can retrieve grain growth and trapping information | E: Pixelwise beta maps from synthetic fluxes at 460 and 100 GHz for a_max = 1 mm and 10 cm | R: Mean beta 1.197 and 0.525; lowest beta in spirals | F: Beta maps trace grain growth and dust trapping | **supported**
- H: GI can explain the spirals in Elias 27, WaOph 6 and IM Lup | E: Modelled each disc with DSHARP parameters and compared synthetic deprojected and residual images with DSHARP images | R: Model spirals of comparable structure and flux; q = 0.27, 0.24, 0.11 | F: GI is a plausible explanation if grains grew to the fragmentation threshold | **partially**

## Reasoning

- Why this data: Use real DSHARP discs with candidate spirals to test GI  
  > "We now turn our model to analysing real observational data of potential self-gravitating discs." (8 Analysing discs from the DSHARP sample)
- Why this method: Semi-analytic models are cheap versus SPH, allowing wide parameter exploration  
  > "These models allow us to produce a suite of discs at little computational expense when compared to approaches such as Smoothed Particle Hydrodynamics (SPH)." (1 Introduction)
- Alternative: Planet-disc interaction as an alternative origin of the spirals; companions would need to be tens of Jupiter masses for Elias 27 and none detected  
  > "An alternative explanation for the observed spiral structure in the DSHARP discs may be the presence of a stellar or planetary-mass companion." (8 Conclusions on DSHARP sample)
- How they decided it was enough: _not stated_
- Limitation (authors): Only face-on discs considered for the generic suite; inclination may obscure spirals  
  > "Inclining and rotating these discs may well obscure them." (7 Observing self-gravitating discs in Taurus)
- Limitation (authors): Parameter space of the DSHARP discs not fully explored  
  > "a complete examination of the potential parameter space of these discs is beyond the scope of the work presented here." (8 Analysing discs from the DSHARP sample)
- Limitation (authors): Spiral geometry is imposed, so only flux amplitudes test the model; the model approximates rather than reproduces the spirals  
  > "the purpose of this simple functional formalism is not to exactly reproduce, but to approximate, the likely spiral morphologies and fluxes of the 3 systems in question" (8 Conclusions on DSHARP sample)
- Caveat (inferred, ours): Comparison to DSHARP is qualitative: no quantitative fit, residual or uncertainty on model flux amplitudes
- Caveat (inferred, ours): Dust trapping factor d is calibrated from only q=0.3 and q=0.4 SPH discs and capped at 5
- Caveat (inferred, ours): Spiral phase and shape (a, b) are imposed from observations, so geometric agreement is not a test
- Caveat (inferred, ours): Results depend on assumed alpha=0.06, v_frag and canonical dust-to-gas ratio 0.01
- Caveat (inferred, ours): Synthetic ALMA setups (PWV, single configuration) are illustrative; noise realisations are not discussed

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: TORUS and PHANTOM input setups and versions
- Missing: Full simobserve/simanalyze parameter lists and noise settings
- Missing: Exact spiral-region masks for flux ratios
- Missing: Model disc outputs and analysis scripts
- Data volume (inferred): Small: synthetic data only; DSHARP images (if used) are a few GB or less
- Score (inferred): 2/5, Mostly simulation with named codes (TORUS, PHANTOM, CASA 5.1) and many equations and parameters, but no code or input files, and the ALMA comparison is qualitative
- Rediscovery candidate: no, Main results are simulated and qualitative image comparisons; real ALMA data play a minor role and recipe details (TORUS, PHANTOM setups) are incomplete

## Links

- Method: (cite: halletal16) (Semi-analytic self-gravitating disc model and ALMA simulator predictions this paper extends)
- Method: (cite: dsharp3) (Spiral parameters and residual-image method for the DSHARP discs)
- Companion: (cite: dsharp1) (DSHARP survey overview, disc parameters and observing setups)
- Related: DSHARP (Disk Substructures at High Angular Resolution Project)

## Checks

```json
{
 "quotes": 95,
 "quotes_ok": 95,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00531.S",
  "2013.1.00226.S",
  "2013.1.00366.S",
  "2013.1.00498.S",
  "2013.1.00601.S",
  "2013.1.00694.S",
  "2013.1.00798.S",
  "2015.1.00486.S",
  "2015.1.00964.S",
  "2016.1.00484.L"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 115,
  "stated": 71,
  "rate": 0.617
 },
 "evidence_ok": true
}
```

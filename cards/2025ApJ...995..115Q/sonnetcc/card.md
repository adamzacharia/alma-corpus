# Bouncing Grains Keep Protoplanetary Disks Bright

`2025ApJ...995..115Q` | The Astrophysical Journal 2025 | first author: Qian, Yansong | arXiv: 2507.06298 | DOI: 10.3847/1538-4357/ae17c5

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks
- Question: How can protoplanetary disks, including old Upper Scorpius disks, stay optically thick and bright at mm wavelengths for millions of years despite grain growth and radial drift? Proposed answer: the bouncing barrier stalls grain growth at about 100 micron.  
  > "How can disks shine brightly for so long, when grain growth and subsequent radial drift should have quickly depleted their solid reservoir?" (abstract); "We show that the bouncing barrier can be used to explain two key observational properties of protoplanetary disks." (Introduction)
- Target **24 Upper Scorpius (USco) disks observed at 2.86 mm (2MASS J-designations listed in the spectral-index table)**: coordinates _not stated_; z/distance 145 pc quoted for USco (resolution conversion); fluxes normalised to 140 pc  
  > "This leads us to perform our own data reduction on the archival $2.86$mm observations (2015.1.00819.S, PI: Ricci, Luca) of 24 USco disks." (A Sample of Proto-planetary Disks); "The former corresponds to $\sim 54$AU at a distance of $145$pc." (A Sample of Proto-planetary Disks); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00819.S
- bands: 2.86 mm (archival)  
  > "This leads us to perform our own data reduction on the archival $2.86$mm observations (2015.1.00819.S, PI: Ricci, Luca) of 24 USco disks." (A Sample of Proto-planetary Disks)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 2.1 arcsec  
  > "This survey also has a relatively low angular resolution ($2.1''$) but its flux measurements allow us to measure $\alpha_{1-3}$." (A Sample of Proto-planetary Disks)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: archival, PI: Ricci, Luca  
  > "This leads us to perform our own data reduction on the archival $2.86$mm observations (2015.1.00819.S, PI: Ricci, Luca) of 24 USco disks." (A Sample of Proto-planetary Disks)
- Other facility **Literature ALMA surveys of Lupus, ONC and Ophiuchus (and USco 0.88 mm surveys)**: Published continuum fluxes, dust disk sizes and spectral indexes used as the comparison sample  
  > "The high-resolution survey of (cite: Guerra2025) measured fluxes and sizes for 73 disks" (A Sample of Proto-planetary Disks); "Fig. [1](#fig:sizel observation) also displays the ONC (cite: Otter2021) and Ophiuchus (cite: Dasgupta2025) disks for comparison." (A Sample of Proto-planetary Disks)
- External data: Lupus 1.3 mm fluxes and sizes for 73 disks  
  > "The high-resolution survey of (cite: Guerra2025) measured fluxes and sizes for 73 disks" (A Sample of Proto-planetary Disks) [from (cite: Guerra2025)]
- External data: Lupus spectral indexes between 0.89 and 3.07 mm for 36 disks  
  > "Spectral indexes between $0.89$mm and $3.07$mm are provided for 36 disks in (cite: Tazzari2021)." (A Sample of Proto-planetary Disks) [from (cite: Tazzari2021)]
- External data: Lupus stellar parameters (Gaia DR2 distance correction)  
  > "Stellar parameters are adopted from (cite: Alcala2017) with later correction using Gaia DR2 distance as in (cite: Alcala2019)." (A Sample of Proto-planetary Disks) [from (cite: Alcala2017); (cite: Alcala2019)]
- External data: USco stellar parameters  
  > "We further adopt stellar parameters for these disks from (cite: Barenfeld2016) and present the scaled fluxes in Fig. [2](#fig:sizel revised)." (A Sample of Proto-planetary Disks) [from (cite: Barenfeld2016)]
- External data: USco R68% radii from earlier surveys (B17, H20 columns of the table)  
  > "a re-analysis by (cite: Hendler2020) assuming a different surface density profile obtained different radii for many of these disks" (A Sample of Proto-planetary Disks) [from (cite: Barenfeld2017); (cite: Hendler2020)]
- External data: ONC and Ophiuchus disk fluxes and sizes for comparison  
  > "Fig. [1](#fig:sizel observation) also displays the ONC (cite: Otter2021) and Ophiuchus (cite: Dasgupta2025) disks for comparison." (A Sample of Proto-planetary Disks) [from (cite: Otter2021); (cite: Dasgupta2025)]
- External data: DIANA standard dust opacities  
  > "These are from grains with a porosity of $25\%$ and a composition of $60\%$ silicates and $15\%$ amorphous carbon (in volume)." (Opacity) [from (cite: Woitke2016)]
- Simulation/model as data: DustPy 1D dust-evolution simulations with and without a bouncing barrier, used to compare predicted flux, size and spectral index evolution with observed disks  
  > "This code models the growth of dust grains, as they move under a number of processes: Brownian motion, radial drift, vertical settling, and turbulence." (DustPy Simulations); "To implement inelastic bouncing into the code, we follow the procedure outlined in Appendix D of (cite: Dominik2024)" (DustPy Simulations)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Archive image products calibrated by the ARI-L project were used  
  > "The publicly available image products from the ALMA archive have been calibrated by the Additional Representative Images for Legacy (ARI-L) Project (cite: ari_l)." (A Sample of Proto-planetary Disks)
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

- Stellar parameters for USco disks  
  > "We further adopt stellar parameters for these disks from (cite: Barenfeld2016) and present the scaled fluxes in Fig. [2](#fig:sizel revised)." (A Sample of Proto-planetary Disks) [from (cite: Barenfeld2016)]
- Two-stream continuum emission expression simplified for face-on, vertically isothermal disk  
  > "Here, we follow (cite: Sierra2020) where they further simplify the expression assuming the disk is faced-on and vertically isothermal" (A simple Model for Dust Continuum Emission) [from (cite: Sierra2020); (cite: Miyake1993)]
- Inelastic bouncing implemented in DustPy following the procedure of Appendix D of Dominik et al., with a minor modification  
  > "To implement inelastic bouncing into the code, we follow the procedure outlined in Appendix D of (cite: Dominik2024)" (DustPy Simulations) [from (cite: Dominik2024)]
- Fragmentation speed adopted from earlier literature  
  > "We follow previous literature (cite: Blum1993; Guttler2010; Dominik2024) and adopt a constant fragmentation speed of" (Order-of-magnitude Estimates) [from (cite: Blum1993; Guttler2010; Dominik2024)]
- Passively irradiated disk temperature model for DustPy runs  
  > "The temperature profile follows the (cite: Chiang1997) model of a passively irradiated disk" (DustPy Simulations) [from (cite: Chiang1997)]

### Not stated but needed to reproduce (our reading)

- Source and exact values of the 0.88 mm (L_7) fluxes listed in the spectral-index table (not said whether taken from Barenfeld 2016/2017, Carpenter 2024 or others)
- Aperture shapes, sizes and centres for the 2.86 mm flux measurement, the off-field region used for the rms, and the specific ARI-L image products/MOUS
- How R_d and tau_3mm(R_d) were fitted to the two fluxes (optimiser, priors, error treatment) and how the model R68% uncertainties were derived beyond the inclination range
- Whether any flux-scale or ARI-L calibration uncertainty was added to the flux errors
- DustPy version, simulation radial grid, run settings and the exact bouncing-implementation modification (Appendix text is partial)
- Treatment of primary-beam response or free-free contamination in the 2.86 mm fluxes

## Analysis recipe

1. **compile comparison sample and put fluxes on a common scale**: Collect literature fluxes, R68% radii and spectral indexes for Lupus, USco, ONC and Ophiuchus, convert to 0.88 mm, normalise to 140 pc and scale by stellar luminosity  
  > "In this work, we compile the continuum fluxes, dust disk sizes and spectral indexes for a sample of disks from different star forming regions" (Introduction)
   - parameter: 1.3 mm fluxes converted to 0.88 mm assuming spectral index 2; fluxes normalised to 140 pc  
  > "For disks where only $1.3$mm fluxes are available, we convert them to $0.88$mm assuming a spectral index $2$." (A Sample of Proto-planetary Disks); "All fluxes are also normalized to be at a distance of 140pc." (A Sample of Proto-planetary Disks)
   - parameter: Fluxes scaled by (L*/Lsun)^(1/4)  
  > "So to reduce scatter introduced by stars of different spectral types, one should scale the observed disk fluxes by $(L_*/L_\odot)^{1/4}$." (A Sample of Proto-planetary Disks)
   - assumption: Passively illuminated disks, T scales as L*^0.25 and Rayleigh-Jeans emission scales as T  
  > "In passively illuminated disks (cite: Chiang1997), disk temperatures scale as $T\propto L_*^{0.25}$, where $L_*$ is the central star luminosity." (A Sample of Proto-planetary Disks)
   - fitting: _not stated_
   - validation: _not stated_
2. **measure USco 2.86 mm disk fluxes**: Aperture photometry on archive ARI-L images with growing apertures until the enclosed flux is constant at 3 sigma; uncertainty from off-field rms integrated over the aperture area  
  > "To measure the disk flux, we apply successively larger apertures until the enclosed flux is constant at a $3\sigma$ level." (A Sample of Proto-planetary Disks); "The uncertainty in the total flux is taken to be the rms of the flux density in the off-field, then integrated over the area enclosed by the aperture." (A Sample of Proto-planetary Disks)
   - fitting: _not stated_
   - validation: Compared with AGE-PRO band 6 spectral indexes for 4 overlapping disks; largely consistent except one disk  
  > "Their values for the spectral indexes (between 1-1.3mm, a narrower range than ours) are largely consistent with our results" (A Sample of Proto-planetary Disks)
3. **derive USco spectral indexes**: Spectral index between 0.88 and 2.86 mm from the two fluxes  
  > "The resulting spectral indexes (between $0.88$ and $2.86$mm) are presented in Table [\[tab:spectral\]](#tab:spectral)." (A Sample of Proto-planetary Disks)
   - fitting: _not stated_
   - validation: _not stated_
4. **infer model disk radii from fluxes and spectral index**: Analytic two-stream continuum model with absorption plus scattering, searching R_d and tau_3mm(R_d) that reproduce both 0.88 mm and 2.86 mm fluxes, for a truncated power-law surface density  
  > "to search for values of $R_d$ and $\tau_{\rm 3mm}(r=R_d)$ that best reproduce both the observed fluxes in $0.88$mm and $2.86$mm." (A study of USco disk sizes)
   - software: OpacityTool
   - parameter: DIANA opacities with a_max = 100 micron and apow = 3.5  
  > "we adopt DIANA opacities with $a_{\rm max} = 100\mu$m and $\mathrm{apow}=3.5$." (A study of USco disk sizes)
   - parameter: Surface density with p = 1 and q = 5  
  > "where we restrict ourselves to $p=1$ and $q=5$." (A study of USco disk sizes)
   - parameter: Inclination 60 deg, varied 33 to 81 deg for the uncertainty  
  > "The disks are assumed to be viewed at $60^\circ$ inclination but we vary the inclination from $33^\circ$ to $81^\circ$ ($1-\sigma$ away from $60^\circ$) to obtain a fiducial uncertainty on disk sizes." (A study of USco disk sizes)
   - assumption: Common distance of 140 pc  
  > "where adopt a common distance of $d=140$ pc." (A simple Model for Dust Continuum Emission)
   - assumption: Grain size distribution dlnN/dlna = -3.5, minimum grain size 1 micron; DIANA porosity 25%  
  > "Throughout the paper, we adopt a grain size distribution with $d\ln N/d\ln a=-3.5$ and a fixed minimum grain size of $1\mu m$." (Opacity)
   - assumption: Disk temperature follows a simple power law with L* scaling  
  > "We assume the disk temperature follows a simple power law:" (A simple Model for Dust Continuum Emission)
   - assumption: Disks radially smooth; model radii are not true measurements and are opacity dependent  
  > "Our model radii are not meant to be actual measurements." (A study of USco disk sizes); "They are somewhat opacity-dependent and should be replaced when observations with higher spatial resolutions are conducted." (A study of USco disk sizes)
   - fitting: _not stated_
   - validation: Revised radii place USco disks on the same SLR as Lupus  
  > "These disks now lie on the same SLR as defined by the Lupus disks." (A study of USco disk sizes)
5. **simulate dust evolution with and without bouncing**: 1D DustPy simulations for initial disk sizes 5, 20, 50, 100 au and alpha = 1e-4 and 1e-3, with and without inelastic bouncing; opacity-weighted fluxes computed with the continuum model  
  > "and initial disk sizes $R_d=[5, 20, 50 , 100]$ au." (DustPy Simulations); "We explore turbulent parameters $\alpha = 10^{-4}$ and $10^{-3}$." (DustPy Simulations)
   - software: DustPy, OpacityTool
   - parameter: Dust-to-gas 1%, all grains initially 1 micron  
  > "The dust to gas ratio is initially 1% everywhere, and all grains initially $1\mu$m in size." (DustPy Simulations)
   - parameter: Grain mass grid [1e-12, 1e6] g with 99 grids, logarithmic radial bins  
  > "The latter spans a range $[10^{-12},10^6]$ g and is covered by 99 grids." (DustPy Simulations)
   - parameter: Host star 1 Lsun, grazing angle 0.05 rad (Chiang & Goldreich passive disk)  
  > "model of a passively irradiated disk with a host star luminosity of $1L_\odot$ and a constant grazing angle of 0.05 radian." (DustPy Simulations)
   - parameter: Constant fragmentation speed of 1 m/s  
  > "We follow previous literature (cite: Blum1993; Guttler2010; Dominik2024) and adopt a constant fragmentation speed of" (Order-of-magnitude Estimates)
   - assumption: Smooth disks in density and temperature, no sub-structure  
  > "In this work, we assume that all disks have smooth profiles in density and temperature." (Modelling the Evolution of Dusty Disks)
   - assumption: Initial Sigma_0 chosen so that even the largest disks start optically thick and on the observed SLR; inclination 60 deg  
  > "Our choice of $\Sigma_0$ ensures that even the largest disks are initially optically thick and located on the observed SLR." (DustPy Simulations)
   - fitting: _not stated_
   - validation: Simulated flux, R68% and spectral index evolution compared qualitatively with the observed SLR and low spectral indexes  
  > "Both, especially the latter, are in violation of the observed disks." (No bouncing)
6. **analytic estimates of barrier sizes and timescales**: Order-of-magnitude estimates of turbulent collision speeds, fragmentation and bouncing barrier sizes, radial drift timescales and streaming-instability constraints  
  > "When dust grains collide, the outcome is determined by their relative velocity, $\Delta v$." (Order-of-magnitude Estimates)
   - assumption: Bouncing threshold from the rolling-motion criterion of Dominik and Tielens  
  > "This criterion sets a maximum velocity for sticking as (cite: Dominik1997)" (More on the Bouncing Barrier)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **DustPy** : 1D dust growth and transport simulations with a bouncing barrier  
  > "This code models the growth of dust grains, as they move under a number of processes: Brownian motion, radial drift, vertical settling, and turbulence." (DustPy Simulations)
- **OpacityTool** : Computing DIANA standard dust opacities as a function of maximum grain size  
  > "to compute the DIANA standard dust opacities (cite: Woitke2016)" (Opacity)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Average USco spectral index alpha_1-3 (0.88 to 2.86 mm) | 2.2 | not stated | dimensionless | 3 | showing an average $\alpha_{1-3} \approx 2.2$, with some disks falling below the blackbody value to $\alpha_{1-3} \sim 1.6$. |
| Lowest USco spectral indexes | about 1.6 | not stated | dimensionless | 3 | showing an average $\alpha_{1-3} \approx 2.2$, with some disks falling below the blackbody value to $\alpha_{1-3} \sim 1.6$. |
| alpha_1-3 of J16082324-1930009 (this work) | 2.3 | not stated | dimensionless | 3 | except for disk J16082324-1930009 for which they reported $\alpha_{1-1.3} = 3.2$, compared to our value of $\alpha_{1-3}=2.3$. |
| Optical depth at disk outer edge for USco model fits | typically >= 0.5 | not stated | dimensionless | 4 | our choice of opacity yields large optical depths, typically $\tau_{3mm}(r=R_d) \geq 0.5$. |
| Grain size at which bouncing stalls growth in the simulations | about 100 micron | not stated | micron | 5 | As expected, the introduction of a bouncing barrier stalls the dust growth at $\sim 100\mu$m (eq. [\[eq:abounce2\]](#eq:abounce2)), after just a few hundred orbits. |
| Time for disks without bouncing to become substantially optically thin | within 1 Myr | not stated | Myr | 5 | In any case, all disks become substantially optically thin within 1 Myrs. |
| Dust loss time for compact (1-10 au) disks without bouncing | about 1e4 yr | not stated | yr | 6 | Without bouncing, compact (1-10au) disks would have lost all its dust within $\sim 10^4$ yrs |
| Stokes number of 100 micron grains at the bouncing barrier | about 1e-4 | not stated | dimensionless | 6 | With a Stokes number of order $St \sim 10^{-4}$, they experience very small radial drifts. |

## Qualitative findings

- USco disks have spectral indexes similar to Lupus and ONC, implying many are optically thick, so the earlier Hendler radii are likely over-estimated  
  > "This suggests that many USco disks are optically thick, at variance with their purported departure from the SLR." (A study of USco disk sizes); "We therefore hypothesize that the (cite: Hendler2020) radii are over-estimated." (A study of USco disk sizes)
- With model radii, disks across all ages follow a single SLR with optically thick normalisation, except the largest disks which may become optically thinner  
  > "If correct, disks across all ages follow a single SLR that has a normalization and slope broadly expected of optically thick emission" (Final Sample and Trends)
- With bouncing, disks stay optically thick for Myr with roughly constant size and spectral index  
  > "The disks remain optically thick throughout even after a few Myrs." (Bouncing included)

## Claim tuples

- H: USco disks are on the same size-luminosity relation as younger regions and are optically thick | E: Measured 2.86 mm fluxes of 24 USco disks from archival ALMA data, derived alpha_1-3 and fit model radii to the 0.88 and 2.86 mm fluxes | R: Average alpha_1-3 about 2.2; model radii are small and place the disks on the Lupus SLR | F: USco disks are mostly optically thick and the earlier larger radii are likely over-estimated; model radii are indicative, not true measurements | **partially**
- H: Without a bouncing barrier, smooth disks cannot stay bright and optically thick for Myr | E: DustPy runs without bouncing for several initial radii and alpha values | R: Dust drains by drift, disks become optically thin within 1 Myr, flux falls below the SLR and spectral indexes rise well above 2 | F: The fragmentation-limited picture contradicts the observed bright, low-index disks | **supported**
- H: A bouncing barrier keeps disks bright | E: DustPy runs with inelastic bouncing included | R: Growth stalls near 100 micron after a few hundred orbits; disks remain optically thick for Myr with nearly constant size and spectral index | F: The bouncing barrier keeps disks bright, especially compact ones, and is supported by the presence of compact bright disks in old USco | **supported**
- H: Planetesimal formation by streaming instability is impeded when grains are bounce-limited | E: Analytic estimate of the turbulence level allowed for midplane settling of 100 micron grains | R: Required alpha of order 1e-8 for St about 1e-4 | F: Streaming instability is unlikely to be effective with the bouncing barrier; this is a brief speculation | **partially**

## Reasoning

- Why this data: No published spectral indexes existed for USco disks and the region offers old, compact disks  
  > "We find no published measurements of spectral indexes for USco disks." (A Sample of Proto-planetary Disks); "To resolve it, we analyze archival ALMA observations at $2.86$mm" (Introduction)
- Why this method: Scale fluxes by stellar luminosity to reduce scatter from different stellar types  
  > "So to reduce scatter introduced by stars of different spectral types, one should scale the observed disk fluxes by $(L_*/L_\odot)^{1/4}$." (A Sample of Proto-planetary Disks)
- Alternative: Optically thin disks dominated by large grains (a_max >= 1 mm, top-heavy size distribution) as an explanation of the low spectral index; rejected because such disks drain quickly and conflict with small grains seen in scattered light  
  > "However, we suggest the latter explanation may be incorrect." (A study of USco disk sizes); "Third, a very top-heavy size distribution seems hard to square with the presence of abundant small grains one observes in scattered light." (A study of USco disk sizes)
- Alternative: Sub-structure with pressure maxima as the alternative way to keep disks bright; deferred to a later study  
  > "To fully support this hypothesis, we will return to consider gapped disks in a subsequent study." (Previous Works on Disk SLR)
- How they decided it was enough: _not stated_
- Limitation (authors): Model radii are constraints from spectral indexes, not measurements, and depend on the adopted opacity  
  > "They are somewhat opacity-dependent and should be replaced when observations with higher spatial resolutions are conducted." (A study of USco disk sizes)
- Limitation (authors): Models assume smooth disks without sub-structures  
  > "In this work, we assume that all disks have smooth profiles in density and temperature. This may be problematic." (Modelling the Evolution of Dusty Disks)
- Limitation (authors): USco disks are only marginally resolved at low resolution, so radii have margins for error  
  > "There are margins for error in such a situation." (A study of USco disk sizes)
- Caveat (inferred, ours): Model radii come from two fluxes plus assumed opacity (a_max = 100 micron), inclination 60 deg and temperature law, so the SLR placement of USco disks is partly circular with the bouncing hypothesis
- Caveat (inferred, ours): Low spectral indexes can also come from scattering, free-free contamination or flux errors; no free-free or flux-scale uncertainty treatment is described
- Caveat (inferred, ours): The 100 micron bouncing size depends on the assumed porosity, monomer size and composition; no fit to data was done, only qualitative comparison
- Caveat (inferred, ours): The comparison between observation and DustPy models is qualitative and for smooth disks only

## Reproducibility

- Data public (paper): Archive image products for 2015.1.00819.S are publicly available  
  > "The publicly available image products from the ALMA archive have been calibrated by the Additional Representative Images for Legacy (ARI-L) Project (cite: ari_l)." (A Sample of Proto-planetary Disks)
- Products in archive: ARI-L image products used for flux measurement  
  > "The publicly available image products from the ALMA archive have been calibrated by the Additional Representative Images for Legacy (ARI-L) Project (cite: ari_l)." (A Sample of Proto-planetary Disks)
- Missing: Aperture definitions and image products for the 2.86 mm fluxes
- Missing: Source of the 0.88 mm fluxes in the table
- Missing: Radius-fit procedure and errors
- Missing: DustPy version and full bouncing-implementation details
- Data volume (inferred): Small (about 24 archive image products, likely under 1 GB); no visibility reprocessing needed
- Score (inferred): 3/5, Public archive image products and a clear model with many parameters, but aperture photometry details, 0.88 mm flux sources, the radius-fit method and DustPy setup details are not fully given
- Rediscovery candidate: no, Data are public, but the recipe is incomplete (flux sources, fit method) and the main conclusions rest on qualitative model comparison

## Links

- Method: (cite: Sierra2020) (Analytic scattering continuum model followed for disk intensity)
- Method: (cite: Woitke2016) (DIANA standard dust opacities)
- Method: (cite: Dominik2024) (Procedure for implementing inelastic bouncing in the dust code)
- Method: (cite: dustpy) (Dust evolution code used)
- Companion: (cite: Guerra2025) (Lupus 1.3 mm fluxes and sizes)
- Companion: (cite: Tazzari2021) (Lupus spectral indexes)
- Companion: (cite: Hendler2020) (USco R68% radii compared with)
- Companion: (cite: Barenfeld2017) (USco radii and stellar-parameter sources)
- Related: ARI-L (Additional Representative Images for Legacy)
- Related: AGE-PRO
- Related: 2015.1.00819.S (PI: Ricci, Luca)

## Checks

```json
{
 "quotes": 88,
 "quotes_ok": 88,
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
  "facts": 102,
  "stated": 60,
  "rate": 0.588
 },
 "evidence_ok": true
}
```

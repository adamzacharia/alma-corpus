# The Impact of Silicate Grain Coagulation on Millimeter Emission from Massive Protostellar Disks

`2025ApJ...990...59Y` | The Astrophysical Journal 2025 | first author: Yamamuro, Ryota | arXiv: 2508.17727 | DOI: 10.3847/1538-4357/adf49c

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: star_formation, protoplanetary_disks
- Question: How does silicate grain coagulation affect (sub-)mm emission from hot massive protostellar disks, and what fragmentation velocity does the GGD27-MM1 1.14 mm profile imply?  
  > "the present study aims to self-consistently constrain both the coagulation properties of silicate grains and the parameters reproducing the overall $1.14\:\mathrm{mm}$ continuum emission." (Introduction)
- Target **GGD27-MM1**: coordinates _not stated_; z/distance 1.4 kpc  
  > "The source distance is $d = 1.4{\rm\:kpc}$" (4.1 Methodology for Parameter Search); distance from Anez+2020  
  > "The source distance is $d = 1.4{\rm\:kpc}$" (4.1 Methodology for Parameter Search)

## Data provenance

- ALMA projects: 2015.1.00480.S
- bands: Band 6 (1.14 mm, 263 GHz)  
  > "which value is the same as the previous ALMA Band 6 observations of the GGD27-MM1 disk" (3 Structure and Emission Characteristics)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beam FWHM sqrt(45.0 mas x 38.3 mas)  
  > "the observation beam has a full width at half maximum (FWHM) of $\sqrt{45.0{\rm\:mas} \times 38.3{\rm\:mas}}$" (4.1 Methodology for Parameter Search)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- External data: Radial profile of 1.14 mm dust continuum intensity (Figure 7, 16 points, r=0-220 au), corrected for compact ionized source  
  > "specifically Figure 7, which presents the radial profile of dust continuum intensity observed at $1.14{\rm\:mm}$." (4.1 Methodology for Parameter Search) [from Añez-López et al. 2020 (cite: Anez+2020)]
- External data: Polarization at 1.14 mm: P=1-1.5% in SW disk at ~100 au  
  > "the polarization vectors align with the disk minor axis with polarization degrees of $P=1$–$1.5\:\%$" (4.1 Methodology for Parameter Search) [from (cite: Girart2018)]
- External data: Stellar luminosity 1.4e4 Lsun from IR observations  
  > "The stellar luminosity is set at $L=1.4\times10^4\:L_\odot$, estimated from near, mid and far -infrared observations" (4.1 Methodology for Parameter Search) [from (cite: Yamashta1987)]
- Simulation/model as data: Steady disk model with single-size dust growth/fragmentation, plus analytic scattering radiative transfer for non-isothermal slab; astronomical silicate opacities  
  > "we introduce a new analytical solution for radiative transfer that assumes isotropic scattering, allowing us to calculate the emergent intensity while incorporating the vertical temperature gradient of the disk." (2 Model)

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

- Disk and dust growth model  
  > "The disk model used in this study is primarily based on that developed by (cite: Yamamuro2023)." (2.1 Disk Model) [from (cite: Yamamuro2023)]
- Polarization-degree method and C=2%  
  > "Following (cite: Kataoka2015), we adopt $C = 2\:\%$." (4.1 Methodology for Parameter Search) [from (cite: Kataoka2015)]
- Analytic RT derivation deferred to forthcoming paper  
  > "The detailed derivation of this analytical solution, along with a discussion of its accuracy, will be presented in a forthcoming paper (Tanaka et al., in prep.)." (2.2 Radiative Transfer for Disk Emission) [from Tanaka et al., in prep.]

### Not stated but needed to reproduce (our reading)

- Digitized values of the Anez-Lopez et al. 2020 Figure 7 profile and its uncertainties
- Disk inclination and position angle values used
- Full derivation of the analytic RT solution (in prep.)
- Optool settings (e.g. grain size grid) and the exact radial sampling of NMSE
- Exact radii r_k used

## Analysis recipe

1. **Build disk structure with grain growth**: Steady disk integrated inward from r_disk to 10 au with single-size dust growth/fragmentation  
  > "In this study, we stop the calculations at an inner radius of $10{\rm\:au}$." (2.1 Disk Model)
   - parameter: M=20 Msun, L=1.4e4 Lsun, alpha_floor=0.01, f_dg=0.01  
  > "We take $\alpha_\mathrm{floor}=0.01$" (2.1 Disk Model)
   - assumption: a_max=0.1 um at the disk outer edge  
  > "We adopt the maximum grain radius of $a_\mathrm{max}=0.1\:\mathrm{\mu m}$ at the outer edge of the disk as the boundary condition." (2.1 Disk Model)
   - fitting: _not stated_
   - validation: _not stated_
2. **Compute dust opacities**: Optool for compact spherical astronomical silicate with power-law size distribution  
  > "The grain size distribution is assumed to follow a power law with an exponent of $-3.5$" (2.3 Dust Opacity)
   - software: Optool
   - parameter: a_min=0.1 um; density 3.3 g cm^-3  
  > "the minimum grain radius is set to $a_{\rm min}=0.1{\rm\:\mu m}$" (2.3 Dust Opacity)
   - assumption: isotropic scattering with effective opacity (1-g)kappa_sca  
  > "we replace the scattering opacity with the effective value for isotropic scattering" (2.3 Dust Opacity)
   - fitting: _not stated_
   - validation: _not stated_
3. **Radiative transfer and beam smoothing**: Analytic emergent intensity for vertically non-isothermal slab with scattering; project to sky and Gaussian smooth  
  > "we apply Gaussian smoothing" (4.1 Methodology for Parameter Search)
   - parameter: sigma_sm = 58 au at d=1.4 kpc  
  > "the smoothing standard deviation is set to $\sigma_{\rm sm}=d\:{\rm FWHM}/(2\sqrt{2\log2})=58{\rm\:au}$" (4.1 Methodology for Parameter Search)
   - assumption: radially symmetric beam; I=0 for r>r_disk  
  > "our Gaussian smoothing uses a radially symmetric beam, ignoring the elliptical shape and position angle of the actual observation beam." (4.1 Methodology for Parameter Search)
   - fitting: _not stated_
   - validation: _not stated_
4. **Grid search for best-fit parameters**: Minimize NMSE between model and observed major-axis profile over Mdot, r_disk, v_frag (plus a_lim or L), subject to a_max=100-150 um at r=90-110 au from polarization  
  > "We identify candidate models by minimizing the normalized mean squared error (NMSE) between the observed and modeled intensity profiles." (4.1 Methodology for Parameter Search)
   - parameter: Grid: Mdot 1e-5 to 1e-3 (20 log steps), r_disk 150-200 au, v_frag 0.1-30 m/s (30 log steps)  
  > "Fiducial Case | $1.4\times10^4$ | $10^{-5}$–$10^{-3}$ | $150$–$200$ | $0.1$–$30$" (Table 1)
   - fitting: Grid search minimizing NMSE (no sampler)  
  > "We identify candidate models by minimizing the normalized mean squared error (NMSE) between the observed and modeled intensity profiles." (Methodology for Parameter Search)
   - validation: Inner-disk mismatch compared to observations (20-30% fiducial; 8% and 6% for alternatives)  
  > "where the discrepancy with observations is reduced to an average of $8\:\%$, compared to the $20$–$30\:\%$ mismatch in the fiducial case." (4.3.1 Grain Size Limit)

## Software

- **Optool** : Dust opacities and scattering matrix elements  
  > "we utilize the optical properties of dust grains derived by `Optool`" (2.3 Dust Opacity)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Fiducial best fit v_frag | 14 | not stated | m/s | 4 | $v_\mathrm{frag}=14\:\mathrm{m\:s^{-1}}$ |
| Fiducial best fit Mdot_gas | 1e-3 | not stated | Msun/yr | 4 | $\dot{M}_\mathrm{gas}=1\times10^{-3}\:M_\odot \mathrm{yr}^{-1}$ |
| Grain-size-limit best fit a_lim | 160 | not stated | um | 4 | Grain Size Limit / $1.4\times10^4$ / $5.0\times10^{-4}$ / $160$ / $12$ / $160$ / $5.5\times10^{-4}$ |
| High-luminosity best fit L | 7e4 | not stated | Lsun | 4 | $v_\mathrm{frag}=17\:\mathrm{m\:s^{-1}}$, $\dot{M}_\mathrm{gas}=7.9\times10^{-4}\:M_\odot \mathrm{yr}^{-1}$, $r_\mathrm{disk}=150\:\mathrm{au}$, and $L=7\times10^4\:L_\odot$. |
| Fiducial NMSE | 2.4e-3 | not stated | dimensionless | 4 | Fiducial Case / $1.4\times10^4$ / $1.0\times 10^{-3}$ / $150$ / $14$ / \- / $2.4\times10^{-3}$ |
| v_frag range across scenarios | 12-17 | not stated | m/s | 4 | the fragmentation velocity consistently falls within the range of $v_\mathrm{frag}=12$–$17{\rm\:m\:s^{-1}}$ |
| Scattering dimming relative to blackbody | 20-30 | not stated | % | 3 | enhanced scattering dims the disk emission by $20$–$30\:\%$ relative to the blackbody emission |

## Qualitative findings

- Silicate fragmentation velocity ~15 m/s is below typical maximum collision velocities (20-50 m/s) in protoplanetary disks, so collisional growth alone is unlikely to form rocky planetesimals.  
  > "suggesting that collisional coagulation alone is insufficient for silicate dust to form rocky planetesimals in such environments." (abstract)

## Claim tuples

- H: Grain growth beyond lambda/2pi dims inner-disk 1.14 mm emission | E: Radiative transfer of self-consistent disk model | R: Brightness falls up to 20-30% below surface blackbody | F: Scattering dimming is a signature of grain evolution | **supported**
- H: GGD27-MM1 profile constrains silicate v_frag | E: NMSE grid search with polarization grain size constraint | R: v_frag = 12-17 m/s | F: v_frag ~15 m/s | **supported**
- H: Fiducial model reproduces inner-disk brightness | E: Fiducial three-parameter survey | R: Inner region >20% too dim in all models | F: Need grain-size limit or higher luminosity | **refuted**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Anez-Lopez et al. settling assumption deemed unlikely given St/alpha<<1  
  > "significant vertical settling is unlikely because the condition ${\rm St}/\alpha \ll 1$ holds in this regime." (5.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Polarization may arise from aligned grains rather than self-scattering, making v_frag highly uncertain  
  > "we cannot rule out the possibility that the polarization may instead result from the alignment of elongated grains" (5.4 Caveats)
- Caveat (inferred, ours): Fit uses digitized literature profile without uncertainties; NMSE not statistical
- Caveat (inferred, ours): Degeneracy among Mdot, L, a_lim, v_frag
- Caveat (inferred, ours): Compact, spherical grains and plane-parallel slab assumed

## Reproducibility

- Data public (paper): Only the ALMA project code is cited; the model data are the published profile  
  > "which made use of ALMA data (ADS/JAO.ALMA#2015.1.00480.S)" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Model code not released
- Missing: Analytic RT derivation in prep.
- Missing: Digitized observed profile
- Data volume (inferred): negligible (uses published radial profile)
- Score (inferred): 3/5, Model equations given in detail but code and observed profile values not provided and RT derivation deferred.
- Rediscovery candidate: no, Theory paper using a published profile; no new ALMA data reduction and the RT solution derivation is not given.

## Links

- Method: Yamamuro et al. 2023 (cite: Yamamuro2023) (Disk and dust growth model)
- Method: Sato et al. 2016 (cite: Sato2016) (Single-size dust growth approach)
- Companion: Añez-López et al. 2020 (cite: Anez+2020) (Source of the ALMA 1.14 mm radial profile)
- Companion: Girart et al. 2018 (cite: Girart2018) (ALMA polarization observations)

## Checks

```json
{
 "quotes": 42,
 "quotes_ok": 42,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 30,
  "rate": 0.411
 },
 "evidence_ok": true
}
```

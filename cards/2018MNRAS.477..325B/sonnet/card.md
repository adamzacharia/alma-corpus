# The extremely truncated circumstellar disc of V410 X-ray 1: a precursor to TRAPPIST-1?

`2018MNRAS.477..325B` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Boneberg, D. M. | arXiv: 1802.07120 | DOI: 10.1093/mnras/sty486

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: What is the nature (radial extent of dust and gas) of the very compact disc around the very low mass star V410 X-ray 1, and can it be a precursor to a TRAPPIST-1-like system?  
  > "we study the nature of the disc around the very low mass star V410 X-ray 1, whose SED is indicative of an optically thick and very truncated dust disc" (abstract)
- Target **V410 X-ray 1**: coordinates RA=04h17m49.655s, Dec=+28d29m36.27s (J2000)  
  > "V410 X-ray 1 is a very low mass star located within the Taurus star forming region L1495 at a distance of $d\sim140$ pc" (2 Observations); z/distance d~140 pc  
  > "V410 X-ray 1 is a very low mass star located within the Taurus star forming region L1495 at a distance of $d\sim140$ pc" (2 Observations); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00163.S
- bands: Band 6 (230 GHz, 1.3mm)  
  > "The observations were taken on 2015-09-19 in Band 6 (230 GHz, 1.3mm) and the on-time source was 6 minutes." (2 Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.26 x 0.21 arcsec (36 x 29 au)  
  > "giving a synthesised beam of $0.26 \times 0.21\ensuremath{''}$ (or $36 \times 29$ au at a distance of 140 pc)" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 6 minutes  
  > "the on-time source was 6 minutes" (2 Observations)
- observing dates: 2015-09-19  
  > "The observations were taken on 2015-09-19 in Band 6" (2 Observations)
- pi or archival as stated: archival data (cite: SimonEtAl2017)  
  > "we also obtained archival ALMA observations of V410 X-ray 1 (cite: SimonEtAl2017)" (2 Observations)
- Line: 12CO J=2-1 (not stated)
- Other facility **Literature photometry (2MASS, WISE, Spitzer IRAC/MIPS, Herschel PACS, SCUBA-2)**: SED photometry from optical to submm  
  > "we draw on photometric measurements from the literature from multiple instruments spanning a range of wavelengths from the optical to the sub-millimetre" (2 Observations)
- External data: SED photometry compiled in Table 1  
  > "1.25 | 62 | 2MASS J | (cite: CutriEtAl2003)" (Table 1) [from BulgerEtAl2014; CutriEtAl2003; WrightEtAL2010; LuhmanEtAl2010; RebullEtAL2010; MohantyEtAl2013]
- External data: Stellar parameters adapted from Bulger et al.  
  > "We have slightly adapted the stellar parameters given by (cite: BulgerEtAl2014) in order to provide a better match to the stellar part of the SED." (3 Methods) [from BulgerEtAl2014]
- Simulation/model as data: Grid of 26 DALI thermochemical models varying gas radius and gas mass to predict CO J=2-1 flux  
  > "we have run a suite of 26 models. Each model produces a fit to the observed SED, but the gas radius $R_\text{c}$ and the total gas mass $M_\text{gas}$ are varied." (4.3 Gas radius)

## Processing

### Calibration

- pipeline or manual: pipeline reduced  
  > "We pipeline reduce the data, giving a synthesised beam of $0.26 \times 0.21\ensuremath{''}$" (2 Observations)
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

- Opacity library and dust properties  
  > "The dust opacities are taken from the opacity library used by (cite: 2017A&A...605A..16F; 2017arXiv171004418F)." (3 Methods) [from (cite: 2017A&A...605A..16F; 2017arXiv171004418F)]
- v_frag reduced by an order of magnitude inside snowline  
  > "Following (cite: BlumWurm2000; GundlachBlum2015), $v_\text{frag}$ is reduced by an order of magnitude interior to the snowline." (Appendix) [from BlumWurm2000; GundlachBlum2015]

### Not stated but needed to reproduce (our reading)

- Imaging parameters (weighting, robust, cell, image size) for the ALMA data
- Pipeline/CASA version
- Channel range and method used for continuum rms and CO upper limit
- Measured rms values
- Full DALI input files and the set of 26 model parameters
- Fitting criterion for SED (by-eye, no statistic)

## Analysis recipe

1. **Derive ALMA upper limits**: Pipeline reduction; 3 sigma upper limits for 1.3 mm continuum and 12CO 2-1 line flux assuming 10 km/s line width  
  > "we calculate a 3$\sigma$ upper limit for the continuum flux at 1.3 mm to be 0.3 mJy, and a 3$\sigma$ upper limit for the $^{12}$CO $J=2$–1 line flux to be 0.4 Jy km s$^{-1}$." (2 Observations)
   - parameter: line width 10 km/s  
  > "The latter is based on the assumption of a line width of 10 km s$^{-1}$" (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Model SED with truncated dust disc**: DALI thermochemical modelling with hydrostatic equilibrium iteration; explore truncation radius and dust mass to match SED  
  > "we use the radiation thermo-chemical disc code DALI (Dust And LInes, (cite: BrudererEtAl2012; Bruderer2013))" (3 Methods)
   - software: DALI
   - parameter: gamma=0.8; R_gas ~ 3 R_c; two grain populations 5 nm-10 um and 10 um-0.3 mm; q=3; large/small mass ratio 30; settling 0.2 h_gas  
  > "We use a size distribution index $q=3$ for the distribution of grain sizes and employ a mass ratio of large to small grains of 30." (3 Methods)
   - parameter: R_in=0.04 au, i=45 deg, Av=3.8, Rv=3.1, Lx=1e28 erg/s  
  > "The inner radius of the disc (in gas and dust) is set to $R_\text{in}=0.04$ au" (3 Methods)
   - assumption: Distance 140 pc; inclination unknown, 45 deg adopted  
  > "As the inclination of the disc is unknown, we use an inclination of $i=45^{\circ}$ for our fiducial model." (3 Methods)
   - fitting: _not stated_
   - validation: Density in hydrostatic equilibrium checked against rho_4; differences negligible  
  > "It is found that the differences between $\rho_3(r,z)$ and $\rho_4(r,z)$ are negligible (except at extremely low densities)" (3 Methods)
3. **Model migration scenario at the snowline**: Impose a_max and Sigma_dust profiles with a discontinuity in v_frag at 0.6 au in DALI; find models fitting SED with extended dust  
  > "we implement the effects on $a_\text{max}$ and $\Sigma_\text{dust}$ into DALI." (4.2)
   - software: DALI
   - parameter: a_max=3 cm and Sigma_dust=0.1 g cm^-2 just outside snowline; v_frag=5 m/s outside, 0.5 m/s inside; alpha=1e-3  
  > "The values of $a_\text{max}$ and dust surface density just outside the water snowline (3 cm and $0.1$ g cm$^{-2}$) provide an acceptable fit to the SED even if the dust extends to $45$ au" (4.2)
   - assumption: Fragmentation-limited growth and steady-state dust flux  
  > "on the assumption that grain growth in this region is limited by fragmentation and that the dust distribution is in a steady state" (4.2)
   - fitting: _not stated_
   - validation: _not stated_
4. **Predict CO J=2-1 flux grid and compare to upper limit**: Grid of 26 DALI models varying R_gas (~3-200 au) and M_gas; compare line flux with 0.4 Jy km/s limit  
  > "Our chosen ranges of gas radius span approximately 3 to 200 au." (4.3)
   - software: DALI
   - parameter: M_gas < 0.1 M_star (gravitational stability)  
  > "the disc must obey gravitational stability (and thus M$_{\rm gas} < 0.1$M$_{\rm star}$)" (4.3)
   - fitting: _not stated_
   - validation: Time-independent chemistry gives same CO 2-1 fluxes as time-dependent  
  > "models calculated with time-independent chemistry yield the same CO $J = 2$ – 1 line fluxes" (4.3)

## Software

- **DALI** : thermochemical and radiative transfer modelling of SED and CO line  
  > "The ray tracing module is then used to obtain both an SED and CO fluxes that can be compared against the observations." (3 Methods)
- **miex** : Mie theory dust opacities  
  > "opacities are computed from Mie theory using the `miex` code (cite: 2004CoPhC.162..113W)" (3 Methods)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 1.3 mm continuum 3-sigma upper limit | 0.3 | not stated | mJy | 1 | 3$\sigma$ upper limit for the continuum flux at 1.3 mm to be 0.3 mJy |
| 12CO J=2-1 3-sigma upper limit | 0.4 | not stated | Jy km/s | 1 | 3$\sigma$ upper limit for the $^{12}$CO $J=2$–1 line flux to be 0.4 Jy km s$^{-1}$ |
| Dust disc outer radius | 0.6 | ~10 per cent | au | 2 | lead to a relatively modest uncertainty in the radius of approximately 10 per cent |
| Dust mass inside 0.6 au (migration model) | ~1 | not stated | Earth masses | 3 | $M_\text{dust}(\text{R}<0.6\text{au}) \sim 1 M_\oplus$ and $M_\text{dust}(\text{R}>0.6\text{au}) \sim 0.2 M_\oplus$ |
| Maximum outer dust radius in migration scenario | ≲45 | not stated | au | 3 | this scenario matches the observed SED for outer dust disc radii of $R_\text{dust, 2}\lesssim 45\,$au |

## Qualitative findings

- CO upper limit excludes discs with gas radius >50 au and gas mass >1e-4 Msun  
  > "These broadly consist of discs with an outer gas radius greater than 50 au and a gas mass greater than $10^{-4}$ M$_{\odot}$." (4.3)

## Claim tuples

- H: The SED of V410 X-ray 1 requires a very truncated optically thick dust disc | E: DALI SED modelling with different truncation radii | R: R_dust ~0.6 au with ~10% uncertainty | F: Dust disc is extremely compact | **supported**
- H: Snowline dust migration can also explain the SED | E: Implemented a_max and Sigma_dust profiles in DALI | R: Acceptable SED fit with dust to 45 au | F: SED cannot distinguish truncation from migration | **supported**
- H: CO J=2-1 flux can discriminate scenarios | E: 26-model grid vs ALMA upper limit | R: Flux depends strongly on R_gas, weakly on M_gas; large discs excluded | F: A firm CO detection would determine gas radius | **partially**
- H: V410 X-ray 1 could be a TRAPPIST-1 precursor | E: Dust mass constraints from optically thick SED | R: ≳1 Earth mass of dust within 0.6 au allowed | F: Possible precursor of tightly packed inner planets | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Dynamical encounter truncation judged extremely unlikely in sparse environment; companion interactions needed  
  > "would imply an encounter within a few au which would be extremely unlikely only considering encounters within the star forming environment" (4.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Gas mass constraints very weak given uncertainty in alpha and v_frag  
  > "given uncertainties in both $\alpha$ and $v_\text{frag}$ the constraints on the *gas* mass from this modelling are very weak" (4.2)
- Limitation (authors): Extended-dust model not necessarily self-consistent with dust growth  
  > "is not necessarily a self-consistent outcome of dust growth models" (4.2)
- Caveat (inferred, ours): Fits are by eye with no statistical inference or parameter uncertainties
- Caveat (inferred, ours): ALMA data are only non-detections so constraints are model-dependent
- Caveat (inferred, ours): Fixed stellar parameters adapted by hand

## Reproducibility

- Data public (paper): Archival ALMA data used (project 2013.1.00163.S)  
  > "we also obtained archival ALMA observations of V410 X-ray 1" (2 Observations)
- Products in archive: _not stated_
- Missing: Modified DALI code and model inputs
- Missing: ALMA imaging and rms details
- Missing: Stellar mass source (footnote truncated)
- Data volume (inferred): <5 GB
- Score (inferred): 3/5, ALMA part is trivial (upper limits) but modelling uses a modified, unreleased DALI and by-eye fits.
- Rediscovery candidate: no, Main results come from custom modified DALI modelling not reproducible from stated recipe.

## Links

- Method: BrudererEtAl2012; Bruderer2013 (DALI code)
- Method: BirnstielEtAl2012 (grain size fragmentation fits)
- Companion: SimonEtAl2017 (original ALMA observations)
- Companion: BulgerEtAl2014 (truncated disc class and SEDs)

## Checks

```json
{
 "quotes": 47,
 "quotes_ok": 47,
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
  "facts": 74,
  "stated": 35,
  "rate": 0.473
 },
 "evidence_ok": true
}
```

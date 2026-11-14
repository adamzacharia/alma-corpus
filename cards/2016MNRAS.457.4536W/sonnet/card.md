# Comparing young massive clusters and their progenitor clouds in the Milky Way

`2016MNRAS.457.4536W` | Monthly Notices of the Royal Astronomical Society 2016 | first author: Walker, D. L. | arXiv: 1602.02762 | DOI: 10.1093/mnras/stw313

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, milky_way_ism
- Question: Are the gas mass distributions of Galactic YMC progenitor clouds consistent with the stellar distributions of YMCs, and which formation scenario (popping, in-situ, conveyor-belt) do they favour?  
  > "We compile a sample of gas clouds in the Galaxy which have sufficient gas mass within a radius of a few parsecs to form a YMC, and compare their radial gas mass distributions to the stellar mass distribution of Galactic YMCs." (abstract)
- Target **G0.253+0.016 (Galactic centre cloud, ALMA)**: coordinates _not stated_; z/distance 8.4 kpc  
  > "Following from our previous work, we include the four quiescent Galactic centre clouds – G0.253$+$0.016, ‘d’, ‘e’ and ‘f’." (Data); distance from Table 2 (reference 1, Walker15 as stated)  
  > "Following from our previous work, we include the four quiescent Galactic centre clouds – G0.253$+$0.016, ‘d’, ‘e’ and ‘f’." (Data)

## Data provenance

- ALMA projects: 2011.0.00217.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **Herschel Hi-GAL**: continuum data for Galactic centre clouds  
  > "Herschel infrared Galactic Plane Survey (cite: higal)" (Data)
- Other facility **BGPS**: continuum data  
  > "Bolocam Galactic Plane Survey (cite: bgps1; bgps2; bgps3)" (Data)
- Other facility **SMA**: 2" observations of W49 combined with single-dish data  
  > "For W49, we utilise high spatial-resolution (2") observations taken with the Submillimeter Array (SMA)." (2.2.1 Clouds)
- Other facility **JCMT SCUBA**: 450 micron data for W51 and G010.472+00.026  
  > "we have extracted 450 $\mu$m SCUBA observations of these clouds from the JCMT data archive." (2.2.1 Clouds)
- Other facility **APEX ATLASGAL**: (sub)mm continuum for three disk clouds, ~19" beam  
  > "These data provide a beam resolution of $\sim$ 19"." (2.2.1 Clouds)
- External data: Arches stellar mass surface density profile and global properties  
  > "The global properties and observed mass surface density profile for the Arches stellar cluster were obtained from (cite: Arches_esp)." (2.1.2 Clusters) [from (cite: Arches_esp)]
- External data: NGC 3603 profile from Figure 14  
  > "The data for NGC 3603 are taken from Figure 14 of (cite: Harayama_3603)." (2.2.2 Clusters) [from (cite: Harayama_3603)]
- External data: Trumpler 14 profile from Figure 10  
  > "Trumpler 14 data are taken from Figure 10 of (cite: Sana_tr14)." (2.2.2 Clusters) [from (cite: Sana_tr14)]
- External data: Westerlund 1 profile from Figure 8  
  > "Westerlund 1 data are taken from Figure 8 of (cite: wd1)." (2.2.2 Clusters) [from (cite: wd1)]
- External data: Sgr B2 Main and North stellar content extrapolated from radio UCHII regions  
  > "Data for the stellar population of Sagittarius B2 proto-clusters (Main & North) were extrapolated from the (cite: Gaume) radio observations" (2.1.2 Clusters) [from (cite: Gaume)]
- Simulation/model as data: Initial conditions of monolithic/popping cluster simulations (B&K1, B&K14, Ass_popping) compared with cloud enclosed mass  
  > "we also plot the initial conditions from several simulations in the literature." (Results)

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

- Analysis of the Galactic centre clouds and Sgr B2 profiles  
  > "The analysis of these clouds is given in (cite: Walker15)." (2.1.1 Clouds) [from (cite: Walker15)]
- Generation of Sgr B2 stellar mass surface density profiles  
  > "See (cite: Walker15) for a detailed explanation of how these data were used to generate mass surface density profiles." (2.1.2 Clusters) [from (cite: Walker15)]
- Mass conversion relation (flux to mass)  
  > "taken from (cite: Jens_mass_in), equation A.31, appendix A" (2.2.1 Clouds) [from (cite: Jens_mass_in)]
- Dust opacity relation  
  > "we use the following relation, given in §3.2 of (cite: Cara_higal)" (2.2.1 Clouds) [from (cite: Cara_higal)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, imaging, beam and rms details (given in Jill_pdf_2014/rathborne15)
- Aperture radii increments and dust peak centres
- ALMA flux integration details and distance-independent mass profile values
- Observed radial profile tables for clouds

## Analysis recipe

1. **Convert continuum flux to gas mass**: Apply dust-emission mass relation with assumed temperature and opacity  
  > "we convert the data from units of flux to units of mass." (2.2.1 Clouds)
   - parameter: dust opacity kappa = 0.04 cm2 g-1 (nu/505 GHz)^1.75  
  > "k_{\nu} = 0.04 \rm ~ cm^{2} ~ g^{-1} \left(\frac{\nu}{505 ~ GHz}\right)^{1.75}" (2.2.1 Clouds)
   - assumption: isothermal; T = 20 K quiescent GC clouds, 40 K star-forming clouds; gas-to-dust 100  
  > "We assume that this single dust temperature is 20 K in all of the quiescent Galactic centre clouds." (2.2.1 Clouds); "We assume a constant gas-to-dust ratio of 100." (2.2.1 Clouds)
   - fitting: _not stated_
   - validation: _not stated_
2. **Build enclosed mass surface density profiles**: Cumulative mass in apertures of increasing radius centred on dust peaks divided by aperture area  
  > "we use the CASA software package (cite: casa) to take cumulative mass measurements within apertures of increasing radii, which are centred on the dust peaks" (Results)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Compare with YMC profiles and simulation initial conditions**: Compare mass within 0.1 pc to cluster cores; convert 3D Plummer model masses to projected masses  
  > "we must take care to ensure that we are making a fair comparison to these models." (Results)
   - assumption: 30% global SFE upper limit for clouds  
  > "we also display this mass adjusted for an assumed upper limit of 30% for the global star formation efficiency." (4 Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : cumulative mass measurements in apertures  
  > "we use the CASA software package (cite: casa) to take cumulative mass measurements" (Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mass within 0.1 pc, G0.253+0.016 | 0.29e3 | not stated | Msun | 2 | G0.253$+$0.016 /        0.29        /        0.09 |
| Mass within 0.1 pc, W49 | 1.28e3 | not stated | Msun | 2 | W49       /        1.28        /        0.43 |
| Mass within 0.1 pc, Arches | 6.6e3 | not stated | Msun | 2 | Arches     /        6.6 |
| Mass systematic uncertainty | factor of ~2 | not stated | dimensionless | 1 | the systematic uncertainties in mass estimates obtained via Equation 1 are $\sim$ a factor of 2 |

## Qualitative findings

- Cloud gas profiles are shallower and lack the prominent cores of YMC stellar profiles; no known cloud has significantly more mass than YMCs in central 0.1 pc  
  > "The mass surface density profiles of the gas clouds are generally shallower than the stellar mass surface density profiles of the YMCs" (abstract)

## Claim tuples

- H: Can known progenitor clouds form YMCs at high initial density (popping)? | E: Compare gas mass within 0.1 pc with YMC cores and simulation initial conditions | R: No clouds contain significantly more central mass than YMCs; simulations require higher surface densities | F: Popping is not consistent with current data; conveyor-belt favoured | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Popping scenario rejected as inconsistent with available data  
  > "a ‘*popping*’ formation scenario for YMCs is not consistent with the data that is currently available" (5 Conclusions)
- How they decided it was enough: _not stated_
- Limitation (authors): Masses are upper limits due to the isothermal assumption; small sample and limited resolution  
  > "The result of our assumptions is that the steepness and mass-scaling of the profiles shown in Figure 1 are over-estimated" (Results)
- Caveat (inferred, ours): Heterogeneous data sets and resolutions
- Caveat (inferred, ours): Fixed dust temperatures drive the results
- Caveat (inferred, ours): Small sample

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA processing details
- Missing: Digitised literature profiles
- Missing: Per-cloud peak positions
- Data volume (inferred): small (~tens of GB for ALMA part)
- Score (inferred): 2/5, ALMA role is minor and inherited from earlier papers; the recipe is incomplete.
- Rediscovery candidate: no, Depends on multiple literature datasets and inherited analysis.

## Links

- Method: (cite: Jens_mass_in) (Mass-from-flux relation)
- Method: (cite: Cara_higal) (Dust opacity law)
- Companion: (cite: Walker15) (Previous Galactic centre analysis)
- Companion: (cite: rathborne15) (ALMA continuum of G0.253+0.016)
- Related: Hi-GAL
- Related: BGPS
- Related: ATLASGAL

## Checks

```json
{
 "quotes": 36,
 "quotes_ok": 36,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 1,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 28,
  "rate": 0.378
 },
 "evidence_ok": true
}
```

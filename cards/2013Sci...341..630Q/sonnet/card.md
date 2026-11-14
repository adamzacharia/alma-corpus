# Imaging of the CO Snow Line in a Solar Nebula Analog

`2013Sci...341..630Q` | Science 2013 | first author: Qi, Chunhua | arXiv: 1307.7439 | DOI: 10.1126/science.1239560

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Where is the CO snow line in the TW Hya disk, as traced by the inner edge of N2H+ J=4-3 emission?  
  > "The N$_2$H$^+$ emission is distributed in a large ring, with an inner radius that matches CO snow line model predictions." (abstract)
- Target **TW Hya**: coordinates _not stated_; z/distance 54±6 pc  
  > "TW Hya is the closest (54$\pm$6 pc) and as such the most intensively-studied pre-main-sequence star with a gas-rich circumstellar disk" (main text); distance from not stated (cited Kastner97; Qi08)  
  > "TW Hya is the closest (54$\pm$6 pc) and as such the most intensively-studied pre-main-sequence star with a gas-rich circumstellar disk" (main text)

## Data provenance

- ALMA projects: 2011.0.00340.S
- bands: Band 7  
  > "Continuum and N$_2$H$^+$ line observations toward TW Hya were carried out in ALMA band 7 (PI: C. Qi)" (Observational details)
- frequencies and spectral setup: four windows, 61.04 kHz channels, 234.375 MHz each; centered at 372.672, 372.421, 358.606, 357.892 GHz  
  > "The correlator was configured to observe four windows with a channel spacing of $\delta\nu$= 61.04 kHz and a bandwidth of 234.375 MHz each." (Observational details)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Cycle 0 compact configuration, 23 to 26 antennas  
  > "with 23 to 26 antennas in the Cycle 0 compact configuration" (Observational details)
- baselines: _not stated_
- angular resolution: N2H+ cube beam 0.63 x 0.59 arcsec (PA=-18 deg)  
  > "The resulting synthesized beam for the N$_2$H$^+$ $J=4-3$ data cube is $0.''63 \times 0.''59$ ($PA=-18\degree$)" (Observational details)
- max recoverable scale: _not stated_
- sensitivity: 30 mJy/beam per 0.1 km/s channel  
  > "the 1$\sigma$ rms is 30 mJy beam$^{-1}$ in 0.1 km s$^{-1}$ velocity intervals" (Observational details)
- time on source: _not stated_
- observing dates: 19 November 2012  
  > "on 19 November, 2012" (Observational details)
- pi or archival as stated: PI: C. Qi  
  > "ALMA band 7 (PI: C. Qi)" (Observational details)
- Line: N2H+ J=4-3 (372.672 GHz)
- Other facility **SMA**: 13CO and C18O J=2-1 data (2005, project 2004-214) used to fit the CO distribution  
  > "we also modeled two CO isotopologues which we observed with the Submillimter Array (SMA)" (CO distribution)
- External data: Disk accretion rate 2e-9 Msun/yr  
  > "given a measured disk mass accretion rate, 2$\times$10$^{-9}$ $M_{\odot}$ yr$^{-1}$ (cite: Herczeg04)" (Physical model) [from Herczeg04]
- External data: N2H+ collisional rate coefficients from LAMDA  
  > "The collisional rate coefficients are taken from the Leiden Atomic and Molecular Database (cite: Schoier05)." (N2H+ line modeling) [from Schoier05]
- External data: Disk geometric and kinematic parameters (inclination, PA, Vlsr, turbulent width)  
  > "Parameters adopted from (cite: Qi04; Qi06; Qi08; Andrews12)." (Table S1) [from Qi04; Qi06; Qi08; Andrews12]

## Processing

### Calibration

- pipeline or manual: visibilities reduced and calibrated in CASA  
  > "The visibility data were reduced and calibrated in CASA 3.4." (Observational details)
- casa version: CASA 3.4  
  > "The visibility data were reduced and calibrated in CASA 3.4." (Observational details)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ceres (primary); J1037-295 gain 0.61 Jy  
  > "The primary calibrator Ceres provided a mean flux density of 0.61 Jy for the gain calibrator J1037-295." (Observational details)
- flux scale uncertainty: _not stated_
- self calibration: continuum self-cal per TW Hya SV Band 7 CASA Guide; upper-sideband solution applied to line data  
  > "We applied the upper sideband continuum self-calibration correction to the N$_2$H$^+$ $J=4-3$ line data" (Observational details)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: in visibility domain, using line-free channels  
  > "subtracted the continuum emission in the visibility domain" (Observational details)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: continuum 0.63x0.60 (USB), 0.57x0.55 (LSB); line cube 0.63x0.59  
  > "The synthesized beam and RMS for the continuum maps are $0.''63 \times 0.''60$ ($PA=3\degree$), 0.61 mJy beam$^{-1}$ (upper sideband)" (Observational details)
- final rms: 30 mJy/beam per 0.1 km/s  
  > "the 1$\sigma$ rms is 30 mJy beam$^{-1}$ in 0.1 km s$^{-1}$ velocity intervals" (Observational details)

### Inherited from earlier work

- Disk model adopted from Qi08, updated for accretion rate and grain settling  
  > "We adopted the model presented in (cite: Qi08), updated to conform with recent observations of the accretion rate and grain settling" (main text) [from (cite: Qi08)]
- Vertical-layer molecular abundance model  
  > "We adopted the molecular abundance model introduced by (cite: Qi08; Qi11)" (N2H+ line modeling) [from (cite: Qi08; Qi11)]
- Self-calibration procedure  
  > "We carried out self-calibration procedures on the continuum as demonstrated in the TW Hya Science Verification Band 7 CASA Guides" (Observational details) [from TW Hya SV Band 7 CASA Guides]

### Not stated but needed to reproduce (our reading)

- Imaging parameters (weighting, robust, cell, image size, masking, deconvolver)
- Line-free channel selection and self-cal solution intervals
- Grid ranges and step sizes for Rin, Rout, p, N100
- Full disk model density/temperature structure files
- Flux scale uncertainty for the ALMA data

## Analysis recipe

1. **Calibrate and image continuum and N2H+**: CASA reduction, sidebands reduced separately, continuum self-calibration, uv-plane continuum subtraction  
  > "Therefore, we reduced the data separately for both sidebands." (Observational details)
   - software: CASA
   - fitting: _not stated_
   - validation: continuum fluxes agree with SMA and ALMA SV data  
  > "which agrees with previous SMA observations and ALMA science verification data" (Observational details)
2. **Build disk physical model**: Steady viscous accretion disk, irradiated, alpha prescription, two dust populations, z_big varied 2H to 3.5H, fitted to SED  
  > "We vary $z_{\rm big}$ between 2$H$ and 3.5$H$" (Physical model)
   - parameter: Mdot 2e-9 Msun/yr, alpha0 0.0007, Rc 60 AU, Md 0.04 Msun  
  > "Viscosity coefficient: $\alpha_0$                                  | 0.0007" (Table S1)
   - assumption: amax small 0.25 um, big 1 mm  
  > "$a_{max}^{small}=0.25 \mu$m (as in the interstellar medium) and $a_{max}^{big}=1$ mm" (Physical model)
   - fitting: _not stated_
   - validation: good fit to broadband SED except mid/far-IR  
  > "this physical model provides a good fit to the broadband spectral energy distribution (SED) of the disk of TW Hya" (Physical model)
3. **Fit N2H+ radial column density distribution**: Grid of RATRAN synthetic visibilities with power-law column density between Rin and Rout; chi2 minimization on real and imaginary visibilities  
  > "The best-fit model is obtained by minimizing $\chi^2$, the weighted difference between the data and the model with the real and imaginary part of the complex visibility" (N2H+ line modeling)
   - software: RATRAN
   - parameter: free: Rin, Rout, p, N100; fixed sigma_s=3.2, sigma_m=100  
  > "We fix the vertical surface boundary $\sigma_s$ to 3.2 and the midplane boundary $\sigma_m$ to 100" (N2H+ line modeling)
   - assumption: Keplerian rotation; geometry fixed from earlier work  
  > "We assumed the disk material orbits the central star in Keplerian motion" (main text)
   - fitting: chi2 grid search, 3 sigma errors  
  > "Errors within 3$\sigma$." (Table S2)
   - validation: repeated for each z_big; inner radius varies <5 AU; residual channel maps  
  > "Across this range of models, the inner radius varies by less than 5 AU" (N2H+ line modeling)
4. **Convert inner edge to CO freeze-out temperature and check with 13CO/C18O**: Read midplane temperature at Rin; fit SMA 13CO and C18O with CO between freeze-out boundary and photodissociation  
  > "CO is assumed to be present in the disk between a lower boundary set by the CO freeze-out temperature derived from the N$_2$H$^+$ modeling" (CO distribution)
   - software: RATRAN, MIRIAD
   - assumption: standard isotope ratios, 17 K freeze-out  
  > "assuming standard isotope ratios and CO freeze-out at the N$_2$H$^+$ inner edge temperature of 17 K" (CO distribution)
   - fitting: same procedure as N2H+  
  > "The CO abundance structure was optimized using the same procedure as for N$_2$H$^+$ above." (CO distribution)
   - validation: fiducial structure reproduces isotopologue fluxes  
  > "the best-fit CO abundance distribution fits the CO isotopologue observations well when using the fiducial disk structure" (CO distribution)

## Software

- **CASA** 3.4: ALMA reduction, calibration, self-cal  
  > "The visibility data were reduced and calibrated in CASA 3.4." (Observational details)
- **RATRAN** : radiative transfer and excitation for synthetic visibilities  
  > "We use the two-dimensional Monte Carlo model RATRAN (cite: Hogerheijde00) to calculate the radiative transfer and molecular excitation." (N2H+ line modeling)
- **MIRIAD** : SMA imaging and deconvolution  
  > "imaging and deconvolution were accomplished in MIRIAD" (CO distribution)
- **MIR** : SMA calibration  
  > "Routine calibration tasks were performed using the MIR software package" (CO distribution)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| N2H+ inner radius (fiducial z_big=3H) | 30 | +1/-2 (3 sigma) | AU | 3 | / 3.0 / 30$^{+1}_{-2}$ / 16–17 |
| CO freeze-out temperature at inner edge | 17 | not stated | K | 4 | the best-fit N$_2$H$^+$ inner radius corresponds to a CO midplane snow line at a temperature of 17 K |
| Continuum peak flux 372 GHz | 2.0097 | 0.0062 | Jy | 1 | 2.0097$\pm$0.0062 Jy at 372 GHz |
| N2H+ column density at 100 AU (z_big=3H) | 1.6e14 | 0.3e14 | cm^-2 | 3 | (1.6$\pm$0.3) $\times$10$^{14}$ |
| N2H+ outer radius (z_big=3H) | 140 | 10 | AU | 3 | / 3.0 / 30$^{+1}_{-2}$ / 16–17 / $-$2.0$^{+0.5}_{-0.7}$ / (1.6$\pm$0.3) $\times$10$^{14}$ / 140$\pm$10 / |
| N2H+ column density detection limit | 2e11 | not stated | cm^-2 | 1 | corresponds to a column density detection limit of 2$\times$10$^{11}$ cm$^{-2}$ at 17 K |

## Qualitative findings

- N2H+ forms a ring with visually estimated inner radius 21-32 AU, unlike centrally peaked CO  
  > "corresponding to a physical inner radius of 21 to 32 AU" (main text)

## Claim tuples

- H: N2H+ imaging locates the CO midplane snow line | E: ALMA N2H+ J=4-3 imaging and visibility-plane modeling with a disk structure model | R: Ring inner radius 28-31 AU (3 sigma), midplane T about 17 K | F: CO snow line at about 30 AU in TW Hya | **supported**
- H: The inner radius is robust to the uncertain disk vertical structure | E: Fits repeated for z_big 2-3.5H | R: Rin varies <5 AU, T <1 K | F: Snow line radius is robust | **supported**
- H: The CO snow line radius constrains Solar System formation scenarios | E: Compare 30 AU with Nice model ice-giant radii and comet formation region | R: Consistent with comets, too large for ice giants | F: Ice giant carbon enrichment likely not from CO ice accretion | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: N2H+ is abundant only where CO is depleted, so it traces the midplane snow line while CO emission comes from surface layers  
  > "is to image molecular emission from a species that is abundant only where CO is highly depleted from the gas phase" (main text)
- Alternative: Lack of ions in inner disk rejected using HCO+ observations  
  > "The different morphologies cannot be explained by a lack of ions in the inner disk" (main text)
- How they decided it was enough: _not stated_
- Limitation (authors): Vertical disk structure is uncertain; vertical N2H+ boundaries fixed  
  > "The details of the vertical structure in the TW Hya disk are therefore uncertain" (Physical model)
- Caveat (inferred, ours): Single temperature threshold may not describe the vertical CO snow surface
- Caveat (inferred, ours): Fixed vertical boundaries and parametric power-law abundance
- Caveat (inferred, ours): chi2 grid errors only, no posterior sampling

## Reproducibility

- Data public (paper): ALMA project 2011.0.00340.S; SMA project 2004-214 named  
  > "This Report makes use of the following ALMA data: ADSJAO.ALMA#2011.0.00340.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging settings
- Missing: Disk model files and fit grid definitions
- Data volume (inferred): ~10-30 GB
- Score (inferred): 3/5, Data public and the model is described, but imaging settings and the full model grid are not given.
- Rediscovery candidate: no, Recipe depends on a bespoke disk model and RATRAN grid that are not fully specified.

## Links

- Method: Qi08 (ApJ 681, 1396) (disk model and N2H+/HCO+ abundance method)
- Method: Qi11 (ApJ 740, 84) (abundance model and snow line approach)
- Companion: Qi13 (ApJ 765, 34) (earlier marginally resolved N2H+ observations)
- Related: ALMA Science Verification TW Hya Band 7

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 48,
  "rate": 0.649
 },
 "evidence_ok": true
}
```

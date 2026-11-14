# Spirals, shadows, and precession in HD 100453 - I. The orbit of the binary

`2020MNRAS.499.3837G` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Gonzalez, Jean-François | arXiv: 2009.10504 | DOI: 10.1093/mnras/staa2938

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks
- Question: Which orbit of the secondary HD 100453 B (eccentricity, semi-major axis, inclination relative to the disc) best reproduces the observed spirals and CO gas structure of the outer disc of HD 100453 A?  
  > "our goal is to bring further constraints, independent of astrometric fitting, to the orbit of the secondary in the HD 100453 system using hydrodynamical simulations to reproduce the observed outer disc morphology" (Introduction)
- Target **HD 100453**: coordinates _not stated_; z/distance 104.2±0.4 pc  
  > "The (cite: GaiaDR2) measured the distance to HD 100453 A to be $104.2\pm0.4$ pc" (Introduction); distance from Gaia DR2  
  > "The (cite: GaiaDR2) measured the distance to HD 100453 A to be $104.2\pm0.4$ pc" (Introduction)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 6 continuum (2017.1.01678); Band 7 12CO J=3-2 (2017.1.01424)  
  > "2017.1.01678 (band 6, PI G. van der Plas) for the continuum image and 2017.1.01424.s (band 7, PI A. Juhász)" (4.1 ALMA data)
- frequencies and spectral setup: Two TDM windows centred at 234.18 and 217.24 GHz, 128 channels over 1.875 GHz  
  > "These two TDM spectral windows were centered at 234.18 GHz and 217.24 GHz." (4.1 ALMA data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-10  
  > "in the C43-10 configuration reaching a total of 92.68 minutes on source" (4.1 ALMA data)
- baselines: 41.4 to 16196.3 m  
  > "baseline distances between 41.4 and 16196.3 meters" (4.1 ALMA data)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 92.68 minutes (Band 6)  
  > "reaching a total of 92.68 minutes on source" (4.1 ALMA data)
- observing dates: 21 Oct and 3 Nov 2017 (Band 6)  
  > "Observations for Program 2017.1.01678 were conducted on October 21$^{\mathrm{st}}$ and on November 3$^{\mathrm{rd}}$ 2017" (4.1 ALMA data)
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (not stated)
- Other facility **VLT/SPHERE**: I'-band scattered light image and astrometry of the secondary  
  > "with the same angular resolution and coronagraph size as in the VLT/SPHERE image from (cite: Benisty2017)" (4.3.1 Scattered light)
- External data: Astrometric orbit fits (MCMC) and probability distributions for the binary  
  > "performed an astrometric fit of the binary orbit using the Markov-chain Monte Carlo (MCMC) Bayesian analysis technique" (2.3 Setup for the binary orbit) [from (cite: vanderPlas2019)]
- External data: Stellar parameters T_A=7250 K, L_A=6.2 Lsun  
  > "$T_\mathrm{A}=7\,250$ K, $L_\mathrm{A}=6.2$ L$_\odot$ (cite: Vioque2018)" (2.4 Radiative transfer) [from (cite: Vioque2018)]
- Simulation/model as data: PHANTOM SPH gas+11-grain dust simulations, 10^6 particles, for 7 orbits, post-processed with MCFOST  
  > "In both sets of simulations we use $10^6$ SPH particles." (2.1 Hydrodynamic simulations)

## Processing

### Calibration

- pipeline or manual: CASA pipeline; Band 7 calibration deferred to Rosotti2020  
  > "The data were calibrated and combined using the *Common Astronomy Software Applications* pipeline (cite: CASA2007)." (4.1 ALMA data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: one round of phase-only self-calibration (continuum)  
  > "We applied one round of phase-only self-calibration and imaged the continuum visibilities" (4.1 ALMA data)

### Imaging

- task: CLEAN in CASA  
  > "imaged the continuum visibilities with the CLEAN task in CASA" (4.1 ALMA data)
- deconvolver: _not stated_
- weighting robust: Briggs, robust 0.5  
  > "using Briggs weighting with a Robust parameter of 0.5" (4.1 ALMA data)
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
- final beam: 0.025'' x 0.023'' at PA = 2 deg  
  > "restored beam size of $0.025\ensuremath{''} \times 0.023\ensuremath{''}$ at PA = $2\ensuremath{^\circ}$" (4.1 ALMA data)
- final rms: 14 uJy/beam  
  > "a RMS of 14 $\mu$Jy/beam" (4.1 ALMA data)

### Inherited from earlier work

- Band 7 12CO data calibration and reduction  
  > "refer the reader to (cite: Rosotti2020) for details on the data calibration and reduction of the latter dataset" (4.1 ALMA data) [from (cite: Rosotti2020)]
- Simulation method for comparing orbit with disc morphology  
  > "following the method for HD 142527 by (cite: Price2018)" (Introduction) [from (cite: Price2018)]
- CO freeze-out, photodissociation and photodesorption treatment  
  > "following Appendix B of (cite: Pinte2018a)" (2.4 Radiative transfer) [from (cite: Pinte2018a)]

### Not stated but needed to reproduce (our reading)

- Band 7 data calibration and imaging details (in Rosotti2020)
- Spectral line channel width and CLEAN parameters for CO cube
- Exact simulation snapshot/viewing geometry conversion to MCFOST inputs
- Input files only available on request

## Analysis recipe

1. **Run SPH simulations for seven orbits**: PHANTOM gas-only forward runs, then rewind runs from extrapolated relative angles, then gas+11-grain dust runs  
  > "we choose to extrapolate the evolution of the relative angles $i_\mathrm{rel}$ and $\Omega_\mathrm{rel}$ between disc and binary orbit backwards in time" (3.2 Rewind simulations)
   - software: PHANTOM
   - parameter: Disc mass 0.003 Msun, 12-60 au, Sigma∝R^-1, H/R=0.05 at 12 au, alpha_SS=5e-3  
  > "The disc has a mass $M_\mathrm{disc}=0.003$ M$_\odot$ and extends between $R_\mathrm{in}=12$ au and $R_\mathrm{out}=60$ au." (2.1 Hydrodynamic simulations)
   - fitting: _not stated_
   - validation: Rewind final disc orientation agrees with observed  
  > "with the final values after 10 orbits very similar to the observed ones" (3.2 Rewind simulations)
2. **Synthetic observations**: MCFOST radiative transfer for I'-band, 1.3 mm and 12CO J=3-2, convolved with beams  
  > "We compute scattered light images in the $I'$ band at $\lambda=0.79\ \mu$m, thermal emission at $\lambda=1.3$ mm, and $^{12}$CO $J=3$–2 molecular emission." (2.4 Radiative transfer)
   - software: MCFOST
   - assumption: 12CO abundance 1e-4 relative to H2; astrosilicate Mie grains  
  > "We set the $^{12}$CO abundance to a uniform value of $10^{-4}$ relative to H$_2$." (2.4 Radiative transfer)
   - fitting: _not stated_
   - validation: _not stated_
3. **Compare with ALMA**: Visual comparison of moment 0 and channel maps (velocity kinks) with ALMA CO, plus dust images  
  > "our methodology of visually comparing synthetic images or channel maps to observations is somewhat subjective" (5.3 Caveats)
   - fitting: _not stated_
   - validation: Updated astrometric fits with MCMC and OFTI  
  > "To validate these new results with an independent method, we use a custom Interactive Data Language (IDL) implementation of the Orbits For The Impatient (OFTI) approach" (Updated orbital fitting)

## Software

- **PHANTOM** : SPH simulations  
  > "public code PHANTOM" (2.1 Hydrodynamic simulations)
- **MCFOST** : synthetic observations  
  > "We use the radiative transfer code MCFOST" (2.4 Radiative transfer)
- **CASA** : calibration and CLEAN imaging  
  > "imaged the continuum visibilities with the CLEAN task in CASA" (4.1 ALMA data)
- **SpeCal** : ADI astrometry of SPHERE data  
  > "We rely mainly on the SpeCal software (cite: Galicher2018)" (Updated orbital fitting)
- **SPLASH** : figures  
  > "Figures were made with SPLASH" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Best orbit eccentricity | 0.32 | not stated | dimensionless | 3 | eccentricity $e=0.32$ and semi-major axis $a=207$ au, inclined by $61\ensuremath{^\circ}$ |
| Best orbit semi-major axis | 207 | not stated | au | 3 | semi-major axis $a=207$ au |
| Relative inclination of best orbit | 61 | ±2 | deg | 3 | F0 & $61\pm2$ |

## Qualitative findings

- Spirals are caused by gravitational interaction with the secondary  
  > "the origin of the grand design spiral structure observed in HD 100453’s disc is the gravitational interaction with the secondary star" (5.2 Origin of the spirals)

## Claim tuples

- H: Which of seven candidate orbits reproduces the observed 12CO disc | E: SPH plus MCFOST synthetic moment 0 and channel maps compared with ALMA | R: Only orbit 0 reproduces spiral reaching secondary, disc extent and kinks | F: Best orbit is eccentric (0.32), a=207 au, inclined 61 deg to disc | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Shadow-induced spirals rejected as origin  
  > "the hypothesis that the spirals are caused by the shadows cast by the inner disc is unlikely" (5.2 Origin of the spirals)
- How they decided it was enough: _not stated_
- Limitation (authors): Only seven orbits tested; comparison is visual and subjective  
  > "The main caveat of this work is the small number of orbital configurations tested" (5.3 Caveats)
- Caveat (inferred, ours): Qualitative visual comparison with no quantitative metric
- Caveat (inferred, ours): Solution non-unique; locally isothermal and inner disc absent

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: PHANTOM public; MCFOST on collaborative basis; input files on request  
  > "The input files for generating our SPH simulations and radiative transfer models, as well as the fitted orbits from the OFTI and MCMC algorithms, are available on request." (Data Availability)
- Missing: Simulation input files only on request
- Missing: Band 7 reduction details
- Data volume (inferred): ~100 GB for Band 6 and 7 visibilities
- Score (inferred): 3/5, Public codes and ALMA data, but visual comparison and inputs on request.
- Rediscovery candidate: no, Main results come from simulations and qualitative visual comparison.

## Links

- Method: (cite: Price2018) (Method for HD 142527 followed)
- Companion: (cite: Rosotti2020) (Band 7 ALMA data)
- Companion: (cite: vanderPlas2019) (Astrometric orbit fits)

## Checks

```json
{
 "quotes": 44,
 "quotes_ok": 44,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2017.1.01424.S",
  "2017.1.01678.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 38,
  "rate": 0.543
 },
 "evidence_ok": true
}
```

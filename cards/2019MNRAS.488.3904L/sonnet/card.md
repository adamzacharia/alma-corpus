# Survival of molecular gas in a stellar feedback-driven outflow witnessed with the MUSE TIMER project and ALMA

`2019MNRAS.488.3904L` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Leaman, Ryan | arXiv: 1907.13142 | DOI: 10.1093/mnras/stz1844

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, milky_way_ism
- Question: Can stellar feedback from the nuclear star-forming ring of NGC 3351 explain the ionised outflow and the transverse dust/CO shell, and how did the cold gas survive?  
  > "with the goal of understanding the survival of cold gas in outflows and providing quantitative tests for sub-grid stellar feedback prescriptions." (Introduction)
- Target **NGC 3351**: coordinates kinematic centre RA=10:43:57.793, Dec=+11:42:14.20  
  > "(640 pc at the assumed distance of 10.1 Mpc; (cite: Moustakas04))" (2.2 ALMA & HERACLES Molecular Gas Observations); z/distance 10.1 Mpc  
  > "(640 pc at the assumed distance of 10.1 Mpc; (cite: Moustakas04))" (2.2 ALMA & HERACLES Molecular Gas Observations); distance from Moustakas04  
  > "(640 pc at the assumed distance of 10.1 Mpc; (cite: Moustakas04))" (2.2 ALMA & HERACLES Molecular Gas Observations)

## Data provenance

- ALMA projects: 2013.1.00885.S, 2013.1.00634.S
- bands: Band 3  
  > "These ALMA Band 3 observations reach a typical rms sensitivity of $\sim 6$ mK per 1.92 MHz-wide channel" (2.2 ALMA & HERACLES Molecular Gas Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 2.0 x 1.2 arcsec (100 x 60 pc; PA=27 deg)  
  > "The synthesized beam is $2.0 \times 1.2"$ ($100 \times 60$ pc; PA$=27^\circ$)." (2.2 ALMA & HERACLES Molecular Gas Observations)
- max recoverable scale: _not stated_
- sensitivity: ~6 mK per 1.92 MHz channel (5 km/s)  
  > "reach a typical rms sensitivity of $\sim 6$ mK per 1.92 MHz-wide channel (a velocity resolution of 5 km s$^{-1}$)" (2.2 ALMA & HERACLES Molecular Gas Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival, PI Karin Sandstrom  
  > "we utilized archival ALMA Early Science Cycle 2 observations from project 2013.1.00885.S (PI: Karin Sandstrom)." (2.2 ALMA & HERACLES Molecular Gas Observations)
- Line: 12CO J=1-0 (115.27 GHz)
- Other facility **VLT/MUSE (TIMER)**: Ionised gas flux and kinematics, stellar populations  
  > "Details on the observations, data reduction and analyses of the TIMER MUSE data can be found in Gadotti et al. (2018)" (2.1 MUSE Spectroscopy)
- Other facility **HERACLES (IRAM 30m)**: CO(2-1) maps for gas mass and rotation curve  
  > "we used the public CO(2-1) maps from HERACLES" (2.2 ALMA & HERACLES Molecular Gas Observations)
- Other facility **HST WFC3**: F336W and F814W images of the dust  
  > "Archival HST WFC3 images (Program ID 13364; PI Calzetti) in the F336W and F814W filters were obtained from the MAST archive." (2.3 Ancillary Imaging Data)
- External data: Distance 10.1 Mpc  
  > "at the assumed distance of 10.1 Mpc; (cite: Moustakas04))" (2.2 ALMA & HERACLES Molecular Gas Observations) [from (cite: Moustakas04)]
- External data: HERACLES CO(2-1) maps  
  > "we used the public CO(2-1) maps from HERACLES[^3] (cite: Leroy09)" (2.2 ALMA & HERACLES Molecular Gas Observations) [from (cite: Leroy09)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Calibrated and imaged datasets downloaded from the archive, primary-beam corrected  
  > "We downloaded the calibrated and imaged datasets from the ALMA archive[^4], corrected for the response of the primary beam" (2.2 ALMA & HERACLES Molecular Gas Observations)
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
- masking: 4 sigma per-pixel clip using line-free channel rms (immoments includepix)  
  > "our preferred maps use a threshold of $4\sigma$, where $\sigma$ is the rms noise in line-free channels and is calculated on a pixel-by-pixel basis." (2.2 ALMA & HERACLES Molecular Gas Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: 114.878-115.068 GHz remaining channels outside integration window 114.902-115.031 GHz  
  > "We integrated emission for channels in the window 114.902-115.031 GHz, using line-free channels to estimate the noise (remaining channels in the frequency range 114.878-115.068 GHz)." (2.2 ALMA & HERACLES Molecular Gas Observations)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 2.0 x 1.2 arcsec, PA=27 deg  
  > "The synthesized beam is $2.0 \times 1.2"$ ($100 \times 60$ pc; PA$=27^\circ$)." (2.2 ALMA & HERACLES Molecular Gas Observations)
- final rms: _not stated_

### Inherited from earlier work

- MUSE observations, reduction and analysis  
  > "Details on the observations, data reduction and analyses of the TIMER MUSE data can be found in Gadotti et al. (2018)" (2.1 MUSE Spectroscopy) [from Gadotti et al. (2018)]
- Stellar dynamical JAM model  
  > "The stellar dynamical model for NGC 3351 was constructed identical to the descriptions in (cite: Leung18)" (2.4 Kinematic Analysis) [from (cite: Leung18)]
- Moment 2 window method  
  > "For the moment 2 map we use the “window method” (cite: Bosma81)" (2.2 ALMA & HERACLES Molecular Gas Observations) [from (cite: Bosma81)]

### Not stated but needed to reproduce (our reading)

- Imaging details of the archival ALMA cube (weighting, deconvolution, array combination) not given
- Whether the archive product includes total-power or short-spacing data is not stated
- CASA version used for moment maps
- Shell mass derivation details from CO(1-0) with alpha_CO and line ratio
- Method for measuring D_CO, radius of curvature, and shell radii

## Analysis recipe

1. **Make CO(1-0) moment maps**: Convert cube to brightness temperature; moments 0, 1 with 4 sigma per-pixel clip; moment 2 with window method  
  > "We converted the ALMA cube to brightness temperature and constructed moment maps for the $^{12}$CO(1-0) line" (2.2 ALMA & HERACLES Molecular Gas Observations)
   - software: CASA
   - parameter: 4 sigma threshold; window 114.902-115.031 GHz  
  > "We integrated emission for channels in the window 114.902-115.031 GHz" (2.2 ALMA & HERACLES Molecular Gas Observations)
   - fitting: _not stated_
   - validation: Tried different thresholds and windows; agree with 13CO maps  
  > "We have experimented with different thresholds and different integration windows, confirming that the maps are sufficiently robust for our purposes" (2.2 ALMA & HERACLES Molecular Gas Observations)
2. **Derive CO rotation curve from HERACLES**: ROTCUR on HERACLES moment 1, with grid over Vsys, PA, inclination  
  > "we ran the task `ROTCUR` within *GIPSY* (cite: Gipsy) on the moment-1 map obtained with HERACLES" (2.4 Kinematic Analysis)
   - software: GIPSY
   - assumption: alpha_CO = 4.4; CO(2-1)/CO(1-0)=0.8  
  > "we use the standard Milky Way conversion factor $\alpha_\mathrm{CO} = 4.4\,M_\odot$" (2.2 ALMA & HERACLES Molecular Gas Observations)
   - fitting: _not stated_
   - validation: Independent check by varying input parameters  
  > "We performed an independent check of the rotation curve by assuming different sets of input parameters" (2.4 Kinematic Analysis)
3. **Model outflow expansion and infer parameters**: SB99 feedback momentum with Kim17 bubble model; MCMC over SFR, density, Z, kappa_IR  
  > "we run an MCMC analysis to ascertain if any qualitative constraints on the original SFR, gas density, metallicity or opacity/re-scattering factor are possible." (3.2 Outflow Expansion Model)
   - software: STARBURST99, emcee
   - parameter: 300 walkers, 1000 simulations each, first 30% discarded  
  > "with 300 walkers running 1000 simulations each. The first 30% of the trials are discarded" (3.2 Outflow Expansion Model)
   - fitting: Uniform priors; likelihood on SFR, Z, and shell distance D_CO = 738 ± 127 pc  
  > "We draw parameters $\theta =$ (SFR, $\rho_{\rm ISM}, Z, \kappa_{\rm IR}$) for each bubble expansion model from a uniform set of priors" (3.2 Outflow Expansion Model)
   - validation: _not stated_

## Software

- **CASA** : moment maps (immoments)  
  > "this is equivalent to running the task `immoments`[^5] within CASA (cite: CASA)" (2.2 ALMA & HERACLES Molecular Gas Observations)
- **GIPSY ROTCUR** : CO rotation curve  
  > "we ran the task `ROTCUR` within *GIPSY* (cite: Gipsy)" (2.4 Kinematic Analysis)
- **STARBURST99** : stellar feedback energetics  
  > "we combine stellar population synthesis models (`STARBURST99`; (cite: Leitherer99), hereafter SB99)" (3.1 Feedback Energetics)
- **emcee (IDL implementation)** : MCMC of bubble models  
  > "we use a modified `IDL` implementation of `emcee`" (3.2 Outflow Expansion Model)
- **RAMSES** : gas response hydrodynamic simulations  
  > "The gas response simulations are produced with the hydrodynamic Adaptive Mesh Refinement (AMR) grid code RAMSES (cite: Teyssier02)." (3.2 Gas response simulations)
- **PyParadise** : MUSE stellar and emission-line fitting  
  > "we used PyParadise, which is an extended Python version of Paradise" (2.1 MUSE Spectroscopy)
- **STECKMAP** : star formation history  
  > "we use the full spectral fitting routine `STECKMAP`" (Star formation history)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Molecular shell gas mass | 6±4 x10^5 | ±4 x10^5 | Msun | 1 | suggest a gas mass of $\sim 6\pm 4 \times 10^{5}$ M$_{\odot}$ for the shell |
| Shell expansion time log t | 7.2 | ±0.6 | log yr | 3 | log $t_{\rm stall} = 7.2 \pm 0.6$ yr |
| Initial mass loading factor | 0.2-1.5 | not stated | dimensionless | 3 | suggest an initial mass loading factor of $0.2 \lesssim \eta \lesssim 1.5$ |
| Required magnetic field | 330 | ±20 | microgauss | 0 | B = V_{\rm Alfv\acute{e}n}(4\pi\rho)^{1/2} = 330 \pm 20 \mu{\rm G} |

## Qualitative findings

- Hydrodynamic simulations do not reproduce the transverse dust lane, so it is not of gravitational origin  
  > "we do not find in any of our models evidence for a secondary curved dust lane." (3.3 Origin of the Transverse Dust Shell)

## Claim tuples

- H: Is the transverse shell caused by the bar potential? | E: RAMSES gas response simulations with observed potential | R: No secondary curved dust lane in any model | F: Stellar feedback is needed | **supported**
- H: Can ring feedback push the shell out? | E: SB99 plus bubble model with MCMC | R: Expansion in ~10^7 yr; direct photon pressure dominant | F: Feedback origin supported | **supported**
- H: How did the cold gas survive? | E: Compare condensation, radiative cooling, magnetic entrainment | R: Magnetic field ~330 uG consistent with the curvature | F: Magnetic entrainment appears possible; others less likely | **partially**

## Reasoning

- Why this data: Archival ALMA CO maps pinpoint the molecular gas distribution and kinematics near the nuclear ring  
  > "To pinpoint the detailed distribution and kinematics of molecular gas in the vicinity of the nuclear ring, we utilized archival ALMA Early Science Cycle 2 observations" (2.2 ALMA & HERACLES Molecular Gas Observations)
- Why this method: _not stated_
- Alternative: Tidal fly-by, inflows, fountain flows and wiggle instability judged less likely than feedback  
  > "we find these less likely than the scenario we propose" (3.3 Origin of the Transverse Dust Shell)
- How they decided it was enough: _not stated_
- Limitation (authors): Significant systematic uncertainties in simple analytic predictions  
  > "there are significant systematic uncertainties in these simple analytic predictions, due to geometry or other factors" (4.3 Magnetic Entrainment)
- Caveat (inferred, ours): Heavily analytic and order-of-magnitude; many assumptions (spherical expansion, constant SFR)
- Caveat (inferred, ours): Magnetic field not observed; consistency argument only
- Caveat (inferred, ours): ALMA data is a minor part and its processing is lightly described

## Reproducibility

- Data public (paper): Archival ALMA, HERACLES and HST data  
  > "we used archival data of molecular gas emission in NGC 3351." (2.2 ALMA & HERACLES Molecular Gas Observations)
- Products in archive: _not stated_
- Missing: MUSE data products and TIMER reduction
- Missing: Exact MCMC likelihood form and IDL code
- Missing: ALMA imaging settings
- Data volume (inferred): ~10-50 GB for ALMA plus MUSE cube
- Score (inferred): 2/5, ALMA is a supporting dataset; main results come from MUSE and analytic models with incomplete detail.
- Rediscovery candidate: no, Recipe is incomplete and ALMA plays a minor role.

## Links

- Method: Gadotti et al. (2018) (MUSE TIMER data reduction)
- Method: (cite: Kim17) (bubble expansion model)
- Companion: (cite: Gadotti19) (TIMER survey NGC 3351 properties)
- Related: MUSE TIMER
- Related: HERACLES
- Related: LEGUS

## Checks

```json
{
 "quotes": 52,
 "quotes_ok": 52,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2013.1.00634.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 41,
  "rate": 0.562
 },
 "evidence_ok": true
}
```

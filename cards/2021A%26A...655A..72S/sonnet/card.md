# Physical conditions in the warped accretion disk of a massive star. 349 GHz ALMA observations of G023.01‒00.41

`2021A&A...655A..72S` | Astronomy and Astrophysics 2021 | first author: Sanna, A. | arXiv: 2107.05683 | DOI: 10.1051/0004-6361/202040000

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: What are the temperature and density structure and the stability of the warped accretion disk around the massive young star in G023.01-00.41, probed by high-excitation CH3CN lines?  
  > "to probe, at different radii, the physical conditions in the accretion disk of an early-type young star." (Introduction)
- Target **G023.01-00.41**: coordinates 18:34:40.290 -09:00:38.30 (phase center, ICRS)  
  > "at a trigonometric distance of 4.59$^{+0.38}_{-0.33}$ kpc from the Sun (cite: Brunthaler2009)" (Introduction); "18:34:40.290 | –09:00:38.30" (Table 1); z/distance 4.59 (+0.38/-0.33) kpc  
  > "at a trigonometric distance of 4.59$^{+0.38}_{-0.33}$ kpc from the Sun (cite: Brunthaler2009)" (Introduction); "18:34:40.290 | –09:00:38.30" (Table 1); distance from trigonometric parallax, Brunthaler2009  
  > "at a trigonometric distance of 4.59$^{+0.38}_{-0.33}$ kpc from the Sun (cite: Brunthaler2009)" (Introduction); "18:34:40.290 | –09:00:38.30" (Table 1)

## Data provenance

- ALMA projects: 2016.1.01200.S
- bands: Band 7 (275–373 GHz)  
  > "We observed the star-forming region G023.01$-$00.41 with the 12 m-array of ALMA in band 7 (275–373 GHz)." (2 Observations and calibration)
- frequencies and spectral setup: 4 basebands; BB1-3 TDM at 336.57, 338.57, 348.57 GHz; BB4 FDM at 349.15 GHz, 1920 channels over 938 MHz, 0.84 km/s resolution  
  > "The FDM window had 1920 spectral channels spaced over a bandwidth of 938 MHz, to achieve a velocity resolution of 0.84 km s$^{-1}$ after spectral averaging by a factor of 2." (2 Observations and calibration)
- continuum bandwidth: _not stated_
- arrays: 12 m array  
  > "with the 12 m-array of ALMA in band 7" (2 Observations and calibration)
- configurations: _not stated_
- baselines: 16 m to 2647 m, 40 antennas  
  > "The 12 m-array observed with 40 antennas covering a baseline range between 16 m and 2647 m" (2 Observations and calibration)
- angular resolution: approx. 0.08'' (beam 0.10'' at 338.57 GHz)  
  > "achieving an angular resolution and maximum recoverable scale of approximately $0.08\ensuremath{''}$ and $1.4\ensuremath{''}$, respectively." (2 Observations and calibration)
- max recoverable scale: 1.4''  
  > "achieving an angular resolution and maximum recoverable scale of approximately $0.08\ensuremath{''}$ and $1.4\ensuremath{''}$, respectively." (2 Observations and calibration)
- sensitivity: ~1 mJy/beam per resolution unit (~1 K); continuum 0.2 mJy/beam  
  > "The continuum emission was integrated over a line free[^1] bandwidth of 52 MHz achieving a sensitivity of 0.2 mJy beam$^{-1}$." (2 Observations and calibration)
- time on source: 3 hour run  
  > "on 2017 July 10 (Cycle 4) during a 3 hour run" (2 Observations and calibration)
- observing dates: 2017 July 10 (Cycle 4)  
  > "on 2017 July 10 (Cycle 4)" (2 Observations and calibration)
- pi or archival as stated: _not stated_
- Line: CH3CN 19_K-18_K, K=0-10 (348.784-349.453 GHz)
- Line: CH3(13)CN 19_K-18_K, K=0-8 (348.853-349.280 GHz)
- Line: CH3OH 14_{1,13}-14_{0,14} A+ (349.107 GHz)
- Other facility **SMA**: preparatory experiment identifying the bright CH3OH line (project 2014B-S006)  
  > "include a bright CH$_3$OH line previously identified in a preparatory SMA experiment (project code 2014B-S006)" (2 Observations and calibration)
- External data: Dust absorption coefficient 1.98 cm2/g from tabulated values (thick ice mantles, 1e8 cm-3)  
  > "a uniform dust absorption coefficient of 1.98 cm $^2$ g$^{-1}$ at the observing frequency, obtained for thick ice mantles, densities of 10$^8$ cm$^{-3}$" (3 Results) [from Ossenkopf1994]
- External data: Mass infall rate 6e-4 Msun/yr, system mass and disk geometry  
  > "$\rm \dot{M}_{inf}$ and M$_{sys}(R)$ were quantified in (cite: Sanna2019)" (4.2 Disk stability) [from Sanna2019]
- External data: Hydrodynamic simulation midplane temperature and density for comparison  
  > "recent hydrodynamics simulations by (cite: Kuiper2018)" (4.1.1 Model comparison) [from Kuiper2018]

## Processing

### Calibration

- pipeline or manual: QA2 calibration scripts  
  > "making use of the calibration scripts provided with the quality assessment process (QA2)" (2 Observations and calibration)
- casa version: CASA 4.7.2 (r39762)  
  > "calibrated with the Common Astronomy Software Applications (CASA) package, version 4.7.2 (r39762)" (2 Observations and calibration)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1733-1304 (polarization and absolute flux calibrator)  
  > "Columns 7, 8, and 9: bandpass, phase, and polarization (and absolute flux) calibrators employed." (Table 1)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "We imaged the line and continuum emission with the task *clean* of CASA" (2 Observations and calibration)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5  
  > "obtained with a Briggs’s robustness parameter of 0.5" (2 Observations and calibration)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub, fitorder=0  
  > "The task *uvcontsub* of CASA was used to subtract a constant continuum level across the spectral window (*fitorder* $=$ 0)." (2 Observations and calibration)
- line free channels: selected by eye from spectrum over 0.5'' circle; 52 MHz continuum bandwidth  
  > "The line free channels in the high spectral-resolution dataset were selected based on an accurate eye inspection of the band" (Footnote 1)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: circular 0.114''  
  > "setting a circular restoring beam size of $0.114\ensuremath{''}$" (2 Observations and calibration)
- final rms: _not stated_

### Inherited from earlier work

- Disk geometry, star position, infall rate, system mass  
  > "column 4 quantifies the (projected) linear distance of the center of each pointing from the star position, as defined in (cite: Sanna2019)" (3 Results) [from Sanna2019]
- CH3CN/CH3(13)CN abundance ratio 30  
  > "whose relative abundance is set to 30 (cite: Wilson1994; Sanna2014)" (3 Results) [from Wilson1994; Sanna2014]
- CH3CN/H2 abundance 1e-8 above 100 K  
  > "we assume a constant relative abundance of 10$^{-8}$ between CH$_3$CN and H$_2$ species for temperatures above 100 K, for consistency with previous work (cite: Johnston2020; Ahmadi2019)" (4.1 Physical conditions) [from Johnston2020; Ahmadi2019]
- Fragmentation analysis and boundary Gamma = xi^2.5/850  
  > "this empirical boundary condition is defined at $\Gamma$ $=$ $\rm \xi^{2.5} \cdot 850^{-1}$ (cite: Kratter2010)" (4.2 Disk stability) [from Kratter2010]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for continuum
- clean parameters: cell size, image size, masks, niter, threshold
- MCWeeds priors, chain length, convergence criteria
- Exact flux calibrator flux value and flux scale uncertainty
- Exact pixel positions/regions of the 22 pointings (only from figure)
- Fitting method for the power laws (weights, error treatment)
- Systemic velocity/rest-frequency handling and the exact K components used per pointing

## Analysis recipe

1. **Calibrate, continuum-subtract and image**: QA2 calibration scripts, uvcontsub, clean with robust 0.5 and common 0.114'' beam  
  > "We imaged the line and continuum emission with the task *clean* of CASA" (2 Observations and calibration)
   - software: CASA
   - parameter: robust = 0.5; beam 0.114''  
  > "obtained with a Briggs’s robustness parameter of 0.5" (2 Observations and calibration)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract spectra at 22 positions**: Integrated spectra over circular areas of radius 250 au along midplane and spiral features  
  > "Each position covers a circular area of radius 250 au" (3 Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **LTE spectral fit step-1: linewidth and velocity**: Gaussian fit to five K-components with common width (MINIMIZE of CLASS); opacity-corrected intrinsic linewidth; source size varied in 5 mas steps with Weeds  
  > "fixed parameters (i) and (ii) by fitting a Gaussian profile to five K-components simultaneously" (3 Results)
   - software: Weeds, CLASS
   - parameter: source size varied about beam size at steps of 5 mas; 13C ratio 30  
  > "Parameter **(iii)** was varied about the beam size at discrete steps of 5 mas" (3 Results)
   - assumption: LTE, Gaussian emitting region, single temperature/density component  
  > "Under the assumption of local thermodynamic equilibrium (LTE)" (3 Results)
   - fitting: _not stated_
   - validation: same size assumption checked a posteriori via fit convergence  
  > "This assumption was verified a posteriori based on the fit convergence (step-2)." (3 Results)
4. **Bayesian fit for Trot and column density**: MCWeeds MCMC fit with other parameters fixed; opacity<5; CH3CN K=0-3 excluded except P6, P12; at least 7 lines per pointing  
  > "the CH$_3$CN K $=$ 0–3 components were excluded from the fit (except for P6 and P12)" (3 Results)
   - software: MCWeeds
   - fitting: Monte Carlo Markov chains minimizing observed-model difference; priors not stated  
  > "We made use of a Monte Carlo Markov chains method to minimize the difference between the observed and computed spectra" (3 Results)
   - validation: _not stated_
5. **Gas mass and H2 column from dust**: Hildebrand formula, optically thin dust at Trot, gas-to-dust 100, kappa 1.98 cm2/g, 500 au diameter  
  > "with a standard gas-to-dust mass ratio of 100, and a uniform dust absorption coefficient of 1.98 cm $^2$ g$^{-1}$" (3 Results)
   - assumption: optically thin dust (later noted as optically thick)  
  > "However, the dust emission is optically thick at these wavelengths" (4.1 Physical conditions)
   - fitting: _not stated_
   - validation: _not stated_
6. **Radial power-law fits and volume density**: Linear fit in log-log of T, N, and volume density vs projected radius; volume density from N divided by line-of-sight length with Rmax=3000 au and abundance 1e-8; 10% systematic added in quadrature  
  > "Error bars plotted in Fig. [3](#fig3) account for a nominal uncertainty of 10% summed in quadrature to the statistical errors." (4.1 Physical conditions)
   - assumption: edge-on circular disk with sharp cutoff at 3000 au  
  > "has a sharp cutoff at radii of 3000 au (R$_{\rm max}$)" (4.1 Physical conditions)
   - fitting: least-squares linear fit in log space  
  > "obtained by minimizing a linear relation between the logarithms of the gas temperature and radius" (4.1 Physical conditions)
   - validation: comparison with Kuiper2018 simulations  
  > "The observed slope is fully consistent with the model expectation" (4.1.1 Model comparison)
7. **Disk stability analysis**: Compute Gamma and xi following Kratter2010 for each pointing with Keplerian or 70% Keplerian rotation  
  > "considering an orbital motion which is either Keplerian or 70% of its value" (4.2 Disk stability)
   - parameter: gamma=7/5, mu=2.8 for sound speed  
  > "where $\gamma$ $=$ $7/5$ is the adiabatic index for a diatomic gas (H$_2$)" (Footnote 3)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.2 (r39762): calibration, uvcontsub, clean  
  > "version 4.7.2 (r39762)" (2 Observations and calibration)
- **Weeds (GILDAS)** : LTE synthetic spectra  
  > "we made use of the Weeds package of GILDAS (cite: Maret2011)" (3 Results)
- **CLASS** : MINIMIZE for simultaneous Gaussian line fitting  
  > "(command MINIMIZE of CLASS)" (3 Results)
- **MCWeeds** : Bayesian MCMC spectral fitting  
  > "MCWeeds (cite: Giannetti2017), which implements a Bayesian statistical analysis for an automated fit" (3 Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Temperature power-law exponent vs radius | -0.43 | 0.03 | dimensionless | 6 | related to each other by a power-law of exponent $-0.43$ $\pm$0.03 |
| Linear correlation coefficient of T-R fit | 0.98 | not stated | dimensionless | 6 | ($r$ $=$ 0.98) |
| Peak volume density at 250 au | 4.8e9 cm-3 (1.6e-14 g cm-3) | not stated | cm-3 | 6 | one derives a peak density of 4.8 $\times$ $10^9$ cm$^{-3}$ (or 1.6 $\times$ $10^{-14}$ g cm$^{-3}$) |
| Rotational temperature at P1 | 267 | +2/-2 | K | 4 | $267^{+2}_{-2}$ |
| CH3CN column density at P1 | 56.75e16 | +0.53/-0.58 | cm-2 | 4 | $56.75^{+0.53}_{-0.58}$ |
| Average volume density at 3000 au | 1.8e7 | not stated | cm-3 | 6 | an average of 1.8 $\times$ $10^7$ cm$^{-3}$ at a radius of 3000 au |

## Qualitative findings

- Apparent spirals are likely accretion streams with velocity gradients ~1 km/s per 2000 au  
  > "These apparent spirals likely represent streams of accretion from the outer envelope onto the disk." (4.3)
- CH3OH 349.1 GHz line shows maser contribution  
  > "showing a maser contribution up to (at least) 2000 au from the young star" (Conclusions)

## Claim tuples

- H: Gas temperature follows the thin-disk R^-3/4 law | E: Fit T vs projected radius at 22 positions | R: Exponent -0.43±0.03 | F: Shallower than classical law and consistent with Kuiper2018 simulation | **supported**
- H: The disk is gravitationally unstable | E: Gamma-xi analysis following Kratter2010 | R: Points near the stability boundary | F: Disk marginally fragmenting, more unstable beyond 1000 au | **partially**
- H: Apparent spirals are accretion streams, not outflow | E: Line offset velocity gradients along streams | R: Gradients ~1 km/s per 2000 au toward blueshift near disk | F: Consistent with infall | **supported**

## Reasoning

- Why this data: High-excitation CH3CN K-ladder probes inner disk  
  > "high excitation-energy transitions of CH$_3$CN allow us to peer into the inner disk regions" (Conclusions)
- Why this method: _not stated_
- Alternative: Streams as outflow or envelope overdensities considered unlikely  
  > "we consider this hypothesis very unlikely given the spatial morphology and physical conditions observed" (4.3)
- How they decided it was enough: _not stated_
- Limitation (authors): Single temperature/density LTE component may not hold in inner disk  
  > "the working hypothesis we have done, that only a single temperature and density component exists, may not be fully satisfied" (3 Results)
- Limitation (authors): Dust is optically thick so continuum masses are unreliable  
  > "the dust emission is optically thick at these wavelengths" (4.1 Physical conditions)
- Caveat (inferred, ours): Uncertainties are statistical plus ad hoc 10%
- Caveat (inferred, ours): Maser contamination of CH3OH and filtering of low-K lines
- Caveat (inferred, ours): Edge-on assumption with inclination <30 deg
- Caveat (inferred, ours): Fixed CH3CN abundance 1e-8 affects density

## Reproducibility

- Data public (paper): Project code given, ALMA archive data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.01200.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: clean parameters
- Missing: MCWeeds priors and chain settings
- Missing: regions of the 22 pointings
- Missing: Sanna2019 disk model quantities
- Data volume (inferred): ~50-100 GB raw (single 3 h Band 7 execution, long baselines)
- Score (inferred): 3/5, Data public and the methods are mostly described, but imaging and MCMC settings are incomplete and the stability analysis relies on prior-paper values.
- Rediscovery candidate: no, Several key inputs (MCMC setup, pointing positions, Sanna2019 values) are missing.

## Links

- Method: Maret2011 (Weeds)
- Method: Giannetti2017 (MCWeeds)
- Method: Kratter2010 (disk stability analysis)
- Companion: Sanna2019 (earlier Cycle-3 ALMA observations of the same disk)
- Companion: Sanna2014 (SMA CH3CN measurements)
- Related: SMA 2014B-S006

## Checks

```json
{
 "quotes": 74,
 "quotes_ok": 74,
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
  "facts": 87,
  "stated": 57,
  "rate": 0.655
 },
 "evidence_ok": true
}
```

# A gap in HD 92945's broad planetesimal disc revealed by ALMA

`2019MNRAS.484.1257M` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Marino, S. | arXiv: 1901.01406 | DOI: 10.1093/mnras/stz049

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks
- Question: Does the HD 92945 planetesimal disc have a gap and asymmetry, what planets could cause them, and is gas present?  
  > "present the first ALMA observations of this system to search for evidence of single or multiple planets that could be shaping the distribution of planetesimals." (1 Introduction)
- Target **HD 92945**: coordinates _not stated_; z/distance 21.5 pc  
  > "HD 92945, a 100-300 Myr old K0 star (cite: Song2004; Plavchan2009) at 21.5 pc (cite: Gaiadr2)" (1 Introduction); distance from Gaia DR2  
  > "HD 92945, a 100-300 Myr old K0 star (cite: Song2004; Plavchan2009) at 21.5 pc (cite: Gaiadr2)" (1 Introduction)

## Data provenance

- ALMA projects: 2016.1.00104.S
- bands: Band 7 (0.86 mm)  
  > "We observed HD 92945 in band 7 (0.86 mm)" (2 Observations)
- frequencies and spectral setup: Four SPWs: continuum at 343.1 and 357.0 GHz (2 GHz BW, 15.625 MHz channels); line SPWs at 345.0 and 355.1 GHz (2 GHz BW, 0.977 and 0.488 MHz channels)  
  > "Two were used to study the continuum emission only, centred at 343.1 and 357.0 GHz with 2 GHz bandwidth and a channel width of 15.625 MHz." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: 12m array and ACA  
  > "We requested both 12m array and ACA observations" (2 Observations)
- configurations: _not stated_
- baselines: 12m: 46-360 m; ACA: 9-44 m (5th-95th percentiles)  
  > "The baselines ranged from 46 to 360 m (5th and 95th percentiles)" (2 Observations)
- angular resolution: 12m beam 0.55''x0.48''; 12m+ACA 0.54''x0.49''  
  > "Band 7 - 12m+ACA" (Table 1)
- max recoverable scale: 0.5'' to 20'' (10 to 400 au)  
  > "allows us to recover emission on angular scales ranging from $0.5\ensuremath{''}$ to $20\ensuremath{''}$ or 10 to 400 au" (2 Observations)
- sensitivity: image rms 16 uJy (12m and 12m+ACA), 175 uJy (ACA)  
  > "Band 7 - 12m" (Table 1)
- time on source: 12m 2.2 h; ACA 3.6 h  
  > "for a total of 2.2 h on source" (2 Observations)
- observing dates: 12m: 13-18 Dec 2016; ACA: 24 Oct 2016 - 23 Mar 2017  
  > "ACA observations were taken between 24 October 2016 and 23 March 2017" (2 Observations)
- pi or archival as stated: Cycle 4 project, PI S. Marino  
  > "cycle 4 project 2016.1.00104.S (PI: S. Marino)" (2 Observations)
- Line: CO J=3-2 (not stated)
- Line: HCN J=4-3 (not stated)
- Other facility **JCMT/SCUBA-2 (SONS)**: Comparison total flux 8.6±1.1 mJy  
  > "consistent with the $8.6\pm1.1$ mJy flux measured with JCMT/SCUBA-2 as part of the SONS survey" (2.1 Dust continuum)
- Other facility **HST**: Previous scattered light images showing gap  
  > "large scale structure that was previously observed by HST" (2 Observations)
- External data: Simulation A of secular resonance model (planets at 3 and 26 au, 1.5 and 0.6 MJup)  
  > "their simulation A (with planetary semi-major axes of 3 and 26 au, masses of 1.5 and 0.6 M$_\mathrm{Jup}$ respectively" (4 Gap opening by secular resonances) [from (cite: Yelverton2018)]
- External data: Direct imaging upper limit ~9 MJup at ~70 au  
  > "only discarding planets more massive than $\sim9$ M$_\mathrm{Jup}$ (cite: Biller2013)" (5.1.1 Planet in situ) [from (cite: Biller2013)]
- Simulation/model as data: N-body simulations tailored to HD 92945 compared with visibilities to limit planet mass  
  > "By comparing new N-body simulations tailored to HD 92945 with the observed visibilities (as in (cite: Marino2018hd107))" (3.1 Results)

## Processing

### Calibration

- pipeline or manual: calibration routines provided by ALMA  
  > "the calibration routines provided by ALMA" (2 Observations)
- casa version: CASA 4.7 for calibration  
  > "Calibrations were applied using CASA 4.7 (cite: casa) and the calibration routines provided by ALMA." (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: TCLEAN in CASA 5.1  
  > "Continuum maps at 0.86 mm are obtained using the TCLEAN task in CASA 5.1" (2.1 Dust continuum)
- deconvolver: _not stated_
- weighting robust: natural weights  
  > "Clean image using natural weights (left panel)" (2.1 Dust continuum)
- uv taper: Gaussian taper 0.7''  
  > "smoothed with a Gaussian tapering of $0.7\ensuremath{''}$" (2.1 Dust continuum)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum subtracted, dirty cubes, no clean  
  > "after subtracting the continuum emission and producing dirty data cubes (no clean iterations are necessary)" (2.2 CO J=3-2 and HCN J=4-3)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12m+ACA combined image  
  > "Band 7 - 12m+ACA" (Table 1)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Parametric disc model (triple power law with Gaussian gap), details in earlier paper  
  > "We use the same parametric model as (cite: Marino2018hd107) that was used to fit ALMA observations of HD 107146 (we direct the reader to that work for details)." (3 Parametric disc model) [from (cite: Marino2018hd107)]
- MCMC visibility fitting with radiative transfer  
  > "We combine radiative transfer simulations and an MCMC fitting procedure in visibility space (cite: Marino2016)." (3 Parametric disc model) [from (cite: Marino2016)]
- Line flux upper limit method (Keplerian-masked integration)  
  > "We have used this method previously to both detect faint lines" (2.2 CO J=3-2 and HCN J=4-3) [from (cite: Marino2016; Marino2017etacorvi; Matra2017fomalhaut; Matra2015)]
- Gas mass non-LTE code  
  > "We use the code developed by (cite: Matra2018) to compute CO gas masses" (5.3 Gas mass upper limits) [from (cite: Matra2018)]

### Not stated but needed to reproduce (our reading)

- MCMC sampler, priors, number of walkers/steps
- Dust opacity and grain size distribution in radiative transfer
- Cell size, image size, clean threshold and masks
- Line-free channels and exact continuum subtraction
- Flux calibrators and flux scale uncertainty
- Spectral window combination and weighting between 12m and ACA
- Velocity range/channels used for line integration
- Kinetic temperature and density grids for CO gas mass

## Analysis recipe

1. **Image continuum and measure total flux**: tclean with natural weights and 0.7'' taper; integrate within elliptical mask of 7'' semi-major axis  
  > "We measure a total disc flux of $9.6\pm1.0$ mJy (including absolute flux uncertainties) by integrating the emission inside an elliptic mask" (2.1 Dust continuum)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared with SCUBA-2 flux 8.6±1.1 mJy  
  > "This total flux is consistent with the $8.6\pm1.1$ mJy flux measured with JCMT/SCUBA-2" (2.1 Dust continuum)
2. **Radial profiles**: Azimuthally average deprojected emission in 60 deg wedges; compare NE and SW  
  > "azimuthally averaging the deprojected emission (using the disc inclination and PA found in §3) within $60\ensuremath{^\circ}$ wide wedges" (2.1 Dust continuum)
   - fitting: _not stated_
   - validation: _not stated_
3. **Parametric visibility modelling**: Radiative transfer + MCMC in visibility space with triple power-law disc, Gaussian gap, eccentricity, free stellar flux  
  > "We combine radiative transfer simulations and an MCMC fitting procedure in visibility space (cite: Marino2016)." (3 Parametric disc model)
   - parameter: stellar template Teff 5250 K, radius 0.77 Rsun; h>0.02 imposed  
  > "a stellar template spectrum corresponding to an effective temperature of 5250 K and a radius of 0.77 $R_{\odot}$" (3 Parametric disc model)
   - assumption: Gaussian vertical profile; all particles share the same eccentricity and pericentre  
  > "we are assuming that all particles have the same eccentricity and pericentre orientation" (3 Parametric disc model)
   - fitting: MCMC; medians with 16th/84th percentiles; upper limits at 95th percentile  
  > "uncertainties based on the 16th and 84th percentiles of the marginalised distributions or upper limits based on 95th percentile." (Table 1)
   - validation: Gap improves chi2 by 19 with three extra parameters; deprojected visibilities compared with no-gap model  
  > "the addition of the gap improves the $\chi^2$ by 19" (3.1 Results)
4. **Secular resonance model comparison**: Populate orbits from simulation A, build RADMC-3D images, fit 11 parameters in visibility space  
  > "we produce synthetic images using RADMC-3D, which we use to compare with observations in visibility space" (4 Gap opening by secular resonances)
   - software: RADMC-3D
   - parameter: 11 free parameters  
  > "in total we vary 11 parameters" (4 Gap opening by secular resonances)
   - fitting: _not stated_
   - validation: chi2 only 11 larger than circular disc; chi2 test and BIC favour SR over eccentric model  
  > "we find a $\chi^2$ that is larger only by 11 compared to the circular disc" (4 Gap opening by secular resonances)
5. **Gas flux and mass upper limits**: Integrate dirty cubes within disc edges and Keplerian-allowed channels; convert with non-LTE code (CO) or LTE (HCN)  
  > "we integrate the dirty data cubes between the disc inner and outer edge and only in those channels where gas emission is expected" (2.2 CO J=3-2 and HCN J=4-3)
   - assumption: HCN in LTE at 40 K; CO/H2 ratio 1e-4  
  > "Assuming a kinetic temperature of 40 K (worst case scenario), we find a HCN gas upper limit of $10^{-9}$ M$_\oplus$." (5.3 Gas mass upper limits)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7 (calibration), 5.1 (imaging): Calibration and tclean imaging  
  > "Continuum maps at 0.86 mm are obtained using the TCLEAN task in CASA 5.1" (2.1 Dust continuum)
- **RADMC-3D** : Synthetic images of secular resonance model  
  > "we produce synthetic images using RADMC-3D" (4 Gap opening by secular resonances)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total disc flux at 0.86 mm | 9.6 | 1.0 | mJy | 1 | We measure a total disc flux of $9.6\pm1.0$ mJy |
| Gap radius | 73.4 | +2.7/-2.4 | au | 3 | $73.4^{+2.7}_{-2.4}$ |
| Gap FWHM | 20 | +10/-8 | au | 3 | $20^{+10}_{-8}$ |
| Gap fractional depth | 0.66 | 0.15 | dimensionless | 3 | $0.66\pm0.15$ |
| Disc inner radius | 52 | 3 | au | 3 | $52\pm3$ |
| Disc outer radius | 121 | +6/-7 | au | 3 | $121^{+6}_{-7}$ |
| Total dust mass | 0.047 | 0.003 | Earth masses | 3 | $0.047\pm0.003$ |
| Inclination | 65.4 | 0.9 | deg | 3 | $65.4\pm0.9$ |
| Position angle | 100.0 | 0.9 | deg | 3 | $100.0\pm0.9$ |
| Disc eccentricity upper limit | <0.097 | 95th percentile | dimensionless | 3 | \<0.097 |
| CO 3-2 3sigma flux upper limit | 69 | not stated | mJy km/s | 5 | $3\sigma$ upper limits of 69 mJy km s$^{-1}$ for CO (3-2) and 63 mJy km s$^{-1}$ for HCN (4-3) |
| HCN 4-3 3sigma flux upper limit | 63 | not stated | mJy km/s | 5 | 63 mJy km s$^{-1}$ for HCN (4-3) |
| Planet mass upper limit for in-situ gap (3sigma) | 0.6 MJup (or 10 Earth masses without co-rotation particles) | not stated | MJup | 3 | we find $3\sigma$ upper limits of 0.6 M$_\mathrm{Jup}$ and 10 M$_\oplus$, respectively |
| CO gas mass upper limit (radiation dominated) | 3e-5 | not stated | Earth masses | 5 | We find a CO gas mass upper limit of $3\times10^{-5}$ M$_\oplus$ in the radiation dominated regime |

## Qualitative findings

- Disc may be asymmetric; SW side brighter with no clear gap, possibly a background galaxy  
  > "These findings suggest that the disc is asymmetric" (2.1 Dust continuum)

## Claim tuples

- H: Does the broad planetesimal disc host a gap? | E: Visibility-space MCMC fit with and without a gap | R: Gap at 73±3 au, width 20 au, depth 0.66; chi2 improves by 19 | F: A gap is required in the planetesimal distribution | **supported**
- H: Could a planet in situ clear the gap? | E: N-body simulations compared with visibilities | R: Planet mass <0.6 MJup (3sigma) | F: Only low-mass planet allowed, or secular resonance with inner planets | **supported**
- H: Can two inner planets via secular resonances explain gap and asymmetry? | E: Synthetic observations of simulation A compared to data | R: chi2 only 11 worse than circular disc with fewer parameters | F: SR model fits as well as parametric model | **supported**
- H: Is gas present? | E: Keplerian-masked integration of dirty cubes | R: No CO or HCN detected | F: Consistent with destruction of Solar System-like comets | **supported**

## Reasoning

- Why this data: 12m for resolution plus ACA to recover large-scale structure seen by HST  
  > "to obtain high angular resolution and to recover large scale structure that was previously observed by HST" (2 Observations)
- Why this method: _not stated_
- Alternative: Mean motion resonance scenario ruled out because required planet mass would push inner edge to >=60 au  
  > "Therefore, we rule out this scenario." (5.1.2 Inner planets)
- How they decided it was enough: _not stated_
- Limitation (authors): Asymmetry could be a background galaxy; low S/N  
  > "Whether this observed residual is due to a true disc asymmetry or background emission is uncertain." (3.1 Results)
- Caveat (inferred, ours): Gap and asymmetry detections are marginal (about 3 sigma)
- Caveat (inferred, ours): Eccentricity poorly constrained because stellar flux/position unconstrained
- Caveat (inferred, ours): Mass limits depend on simulation assumptions
- Caveat (inferred, ours): Secular resonance model is one non-unique configuration

## Reproducibility

- Data public (paper): ALMA project code cited; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00104.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: MCMC settings and priors
- Missing: Dust properties
- Missing: Imaging parameters
- Missing: Simulation code for N-body
- Missing: Exact calibration details
- Data volume (inferred): about 20-60 GB raw for 12m plus ACA
- Score (inferred): 3/5, Data identified and fits well described, but depends on earlier-paper model and lacks MCMC and imaging details.
- Rediscovery candidate: no, Recipe relies on inherited custom model code and unstated settings.

## Links

- Method: (cite: Marino2018hd107) (Parametric model and N-body method)
- Method: (cite: Marino2016) (MCMC visibility fitting)
- Method: (cite: Matra2018) (Non-LTE CO mass code)
- Companion: (cite: Yelverton2018) (Secular resonance gap model)
- Related: HD 107146 ALMA observations
- Related: SONS survey

## Checks

```json
{
 "quotes": 71,
 "quotes_ok": 71,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 49,
  "rate": 0.645
 },
 "evidence_ok": true
}
```

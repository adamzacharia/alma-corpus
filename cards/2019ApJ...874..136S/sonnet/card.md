# High-precision Dynamical Masses of Pre-main-sequence Stars with ALMA and Gaia

`2019ApJ...874..136S` | The Astrophysical Journal 2019 | first author: Sheehan, Patrick D. | arXiv: 1903.00032 | DOI: 10.3847/1538-4357/ab09f9

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, stellar_physics
- Question: Can Keplerian-rotation modeling of ALMA 12CO(2-1) disk emission combined with Gaia distances give high-precision dynamical masses of pre-main-sequence stars, and how do they compare with evolutionary-track masses?  
  > "We employ detailed modeling of the Keplerian rotation profile, coupled with accurate distances from $Gaia$, to directly measure the stellar masses with $\sim$2% precision." (abstract)
- Target **2M1626-2527 (2MASS J16262774-2527247)**: coordinates _not stated_; z/distance 138.258 pc  
  > "2M1626–2527 has a parallax of $7.232 \pm 0.074$ mas and a distance of $138.258^{+1.426}_{-1.396}$ pc" (Appendix: The MCMC Fitting Procedure); distance from Gaia parallax (Gaia Collaboration 2018)  
  > "2M1626–2527 has a parallax of $7.232 \pm 0.074$ mas and a distance of $138.258^{+1.426}_{-1.396}$ pc" (Appendix: The MCMC Fitting Procedure)
- Target **CT Cha**: coordinates _not stated_; z/distance 191.775 pc  
  > "CT Cha has a parallax of $5.214 \pm 0.021$ mas and a distance of $191.775^{+0.781}_{-0.774}$ pc" (Appendix: The MCMC Fitting Procedure); distance from Gaia parallax (Gaia Collaboration 2018)  
  > "CT Cha has a parallax of $5.214 \pm 0.021$ mas and a distance of $191.775^{+0.781}_{-0.774}$ pc" (Appendix: The MCMC Fitting Procedure)
- Target **DH Tau**: coordinates _not stated_; z/distance 135.355 pc  
  > "DH Tau has a parallax of $7.388 \pm 0.069$ mas and a distance of $135.355^{+1.282}_{-1.258}$ pc" (Appendix: The MCMC Fitting Procedure); distance from Gaia parallax (Gaia Collaboration 2018)  
  > "DH Tau has a parallax of $7.388 \pm 0.069$ mas and a distance of $135.355^{+1.282}_{-1.258}$ pc" (Appendix: The MCMC Fitting Procedure)

## Data provenance

- ALMA projects: 2015.1.00773.S
- bands: Band 6 (Cycle 3)  
  > "Our targets were observed with ALMA Band 6 during Cycle 3, in September 2016." (2 Observations & Data Reduction)
- frequencies and spectral setup: Three continuum basebands of 2 GHz centered at 233, 246, 248 GHz; 12CO(2-1) baseband with 3840 0.122 MHz channels centered at 230.538 GHz (0.32 km/s, Hanning smoothed)  
  > "The final baseband was configured for $^{12}$CO (2–1) observations, with 3840 0.122 MHz channels centered at 230.538 GHz (0.32 km s$^{-1}$ velocity resolution; Hanning smoothed)" (2 Observations & Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15-3247 m (DH Tau, CT Cha), 15-3143 m (2M1626)  
  > "| DH Tau | Sep. 14 2016 | 15$\,$-$\,$3247 | 13 | 0.30" $\times$ 0.17" | 4 | J0510+1800, J0433+2905 |" (Table 1)
- angular resolution: 0.30x0.17" (DH Tau), 0.21x0.18" (2M1626), 0.27x0.14" (CT Cha)  
  > "| 2M1626-2527 | Sep. 16 2016 | 15$\,$-$\,$3143 | 12 | 0.21" $\times$ 0.18" | 3.1 | J1517-2422, J1634-2058 |" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: RMS 4, 3.1, 3.8 mJy (DH Tau, 2M1626, CT Cha)  
  > "| CT Cha | Sep. 27 2016 | 15$\,$-$\,$3247 | 13.5 | 0.27" $\times$ 0.14" | 3.8 |" (Table 1)
- time on source: ~12-13.5 min integration per target  
  > "| CT Cha | Sep. 27 2016 | 15$\,$-$\,$3247 | 13.5 | 0.27" $\times$ 0.14" | 3.8 | J1107-4449, J1058-8003 |" (Table 1)
- observing dates: Sep 14, 16, 27 2016  
  > "| DH Tau | Sep. 14 2016 |" (Table 1)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.538 GHz)
- Other facility **Gaia**: Parallaxes/distances used as prior  
  > "we use direct measurements of source distances from trigonometric parallaxes by $Gaia$ to place a prior constraint on the distance." (Appendix: The MCMC Fitting Procedure)
- External data: Optical/near-IR photometry used for SED fits  
  > "fitting optical and near-infrared photometry collected from the literature" (3.2 Masses and Stellar Parameters from Evolutionary Tracks) [from Vrba1989; Epchtein1999; Briceno2002; Ducati2002; Cutri2003; Monet2003; Zacharias2003; Torres2006; Robberto2012; Muinos2014; Henden2016; Bowler2017]
- External data: Literature Teff for Gaussian prior  
  > "using temperatures collected from the literature (cite: Herczeg2014; Bowler2017; Manara2016a)" (3.2 Masses and Stellar Parameters from Evolutionary Tracks) [from Herczeg2014; Bowler2017; Manara2016a]
- Simulation/model as data: BT-Settl atmospheres and evolutionary tracks (Baraffe2015, PARSEC Bressan2012/Chen2014, Feiden2016 non-magnetic and magnetic)  
  > "the (cite: Baraffe2015) models, the PARSEC models (cite: Bressan2012) and subsequent updates to low-mass ($<0.75~M_\ensuremath{\odot}$) stars (cite: Chen2014)" (3.2 Masses and Stellar Parameters from Evolutionary Tracks)

## Processing

### Calibration

- pipeline or manual: ALMA Pipeline in CASA  
  > "The data were calibrated using the ALMA Pipeline in the `CASA` software package (cite: McMullin2007)." (2 Observations & Data Reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Single iteration of phase-only self-cal, one solution per scan, on continuum basebands, applied to line window  
  > "we employed a single iteration of phase-only self-calibration, with one solution per scan, to the continuum basebands and applied these phase solutions to our spectral line window." (2 Observations & Data Reduction)

### Imaging

- task: CASA clean, spectral cube mode  
  > "the data were imaged and deconvolved using the spectral cube mode of the CASA *clean* task." (2 Observations & Data Reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting, 0.4 km/s channels  
  > "The imaging was done using natural weighting to increase the sensitivity of the channel maps" (2 Observations & Data Reduction)
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

- Evolutionary-track mass method  
  > "following the method outlined in (cite: Andrews2013) and (cite: Czekala2015)." (3.2 Masses and Stellar Parameters from Evolutionary Tracks) [from (cite: Andrews2013); (cite: Czekala2015)]
- Excluding channels affected by cloud absorption  
  > "A similar effect (and resolution) were adopted by (cite: Czekala2016)." (2 Observations & Data Reduction) [from (cite: Czekala2016)]

### Not stated but needed to reproduce (our reading)

- Which channel range was used in each fit and exact channels excluded for DH Tau
- CASA version and pipeline version
- Clean mask, threshold, cell and image size
- MCMC initial walker ranges and burn-in length
- Source coordinates and field centers
- Model grid sizes/RADMC-3D settings (photon count, image resolution)
- Prior form for gamma, v_sys, and Gaussian prior parameters for extinction model
- Flux calibrator flux scale uncertainty

## Analysis recipe

1. **Calibrate and image CO(2-1) data**: ALMA pipeline calibration, phase-only self-cal, CASA clean spectral cube with natural weighting, 0.4 km/s channels  
  > "The imaging was done using natural weighting to increase the sensitivity of the channel maps, as the emission is often faint, and with 0.4 km s$^{-1}$ channels." (2 Observations & Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit Keplerian disk model to visibilities**: RADMC-3D channel maps (LTE) transformed to visibilities with GALARIO, fit in uv-plane with emcee; 14 free parameters  
  > "We fit the model channel map visibilities generated by RADMC-3D and GALARIO to our data in the $uv$-plane using the MCMC fitting code `emcee`" (3.1 Dynamical Stellar Masses)
   - software: pdspy, RADMC-3D, GALARIO, emcee
   - parameter: 200 walkers; ~5000 post-burn-in steps; autocorrelation time ~1000 steps; walkers with chi2-chi2min>44 discarded  
  > "Instead, we discard any walkers with $(\chi^2 - \chi^2_{min}) > 44$" (Appendix: The MCMC Fitting Procedure)
   - assumption: X_CO = 1e-4, mu = 2.37, vertically isothermal disk, Keplerian rotation, tapered power-law surface density, LTE  
  > "We typically assume that $X_{\rm CO} = 1.0\times10^{-4}$." (3.1 Dynamical Stellar Masses)
   - fitting: Likelihood exp(-chi2/2) on complex visibilities; uniform priors on most parameters (log-uniform for some), Chabrier IMF prior on M*, Gaussian Gaia parallax prior on distance; i<90 deg  
  > "We assume a Gaussian prior on the parallax, with a mean given by the measured $Gaia$ parallax and the standard deviation given by the $Gaia$ uncertainty." (Appendix: The MCMC Fitting Procedure)
   - validation: Convergence judged by median walker position stability; walker step plots and triangle plots; residual channel maps  
  > "We consider a fit to be “converged" when the median walker position does not change significantly compared to the spread of the walkers over a significant number of steps." (Appendix: The MCMC Fitting Procedure)
3. **Fit stellar SEDs for Teff and L***: BT-Settl models fit to photometry with emcee; Gaussian priors on d (Gaia) and Teff (literature, sigma 150 K)  
  > "We assumed a Gaussian prior on $d_{pc}$ derived from $Gaia$ parallaxes" (3.2 Masses and Stellar Parameters from Evolutionary Tracks)
   - software: emcee
   - assumption: Weingartner & Draine extinction with R_V = 5.5  
  > "using the extinction curves from (cite: Weingartner2001) with $R_V = 5.5$" (3.2 Masses and Stellar Parameters from Evolutionary Tracks)
   - fitting: _not stated_
   - validation: _not stated_
4. **Map Teff, L* onto evolutionary tracks**: Each post-burn-in sample mapped onto five sets of tracks to build mass and age distributions; compare with dynamical mass  
  > "For each post-burn in MCMC sample, we mapped $T_{eff}$ and $L_*$ on to evolutionary tracks to build up a probabilistic sample of stellar masses" (3.2 Masses and Stellar Parameters from Evolutionary Tracks)
   - fitting: _not stated_
   - validation: _not stated_
5. **Test foreground extinction in DH Tau**: Add Gaussian optical-depth absorption exp(-tau) per channel with 3 extra parameters and refit  
  > "We assume that each channel is extincted by an amount of $\exp{(-\tau_{\nu})}$." (4.3 DH Tau)
   - software: pdspy
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration and imaging  
  > "The data were calibrated using the ALMA Pipeline in the `CASA` software package" (2 Observations & Data Reduction)
- **pdspy** : Disk modeling and MCMC fitting  
  > "using our new code `pdspy`[^1] (cite: Sheehan2018b)" (1 Introduction)
- **RADMC-3D** : Radiative transfer synthetic channel maps  
  > "generate synthetic channel maps for a given set of model parameters" (3.1 Dynamical Stellar Masses)
- **GALARIO** : Fourier transform to synthetic visibilities  
  > "using the GALARIO code (cite: Tazzari2017; Tazzari2018)" (3.1 Dynamical Stellar Masses)
- **emcee** : MCMC fitting  
  > "using the MCMC fitting code `emcee`" (3.1 Dynamical Stellar Masses)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 2M1626-2527 dynamical mass | 0.535 | +0.006/-0.007 | Msun | 2 | $0.535^{+0.006}_{-0.007}~M_\ensuremath{\odot}$ |
| CT Cha dynamical mass | 0.796 | +0.015/-0.014 | Msun | 2 | $0.796^{+0.015}_{-0.014}~M_\ensuremath{\odot}$ |
| DH Tau dynamical mass | 0.101 | +0.004/-0.003 | Msun | 2 | $0.101^{+0.004}_{-0.003}~M_\ensuremath{\odot}$ |
| DH Tau mass with extinction model | 0.141 | +0.016/-0.011 | Msun | 5 | this new model does increase the stellar mass to $0.141^{+0.016}_{-0.011}$ $M_\ensuremath{\odot}$ |
| CT Cha inclination | 54.0 | +1.0/-0.9 | deg | 2 | $54.0^{+ 1.0}_{- 0.9}$ |
| CT Cha Baraffe2015 track mass | 1.06 | +0.20/-0.20 | Msun | 4 | / Baraffe et al. 2015 / $0.53^{+0.12}_{-0.10}$ / $1.06^{+0.20}_{-0.20}$ / $0.40^{+0.05}_{-0.03}$ / |

## Qualitative findings

- Magnetic Feiden2016 tracks overestimate masses for all three sources.  
  > "The magnetic tracks from (cite: Feiden2016), however, seem to universally over-estimate the masses for all three sources." (4 Results)

## Claim tuples

- H: Gaia distances plus ALMA CO Keplerian modeling yield percent-level dynamical masses | E: pdspy visibility-plane fit of CO(2-1) with Gaia parallax prior | R: Mass uncertainties 2-4% | F: Mass uncertainty no longer dominated by distance | **supported**
- H: Dynamical masses agree with evolutionary tracks | E: Compare with five track sets | R: 2M1626 and CT Cha within <2 sigma of most models; differences remain | F: Reasonable but not perfect agreement; magnetic tracks poor | **partially**
- H: DH Tau mass discrepancy is due to foreground cloud absorption | E: Add Gaussian absorption model | R: Mass rises to 0.141 Msun, still below tracks | F: Simple extinction does not reconcile; unclear | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Keplerian rotation with precise Gaia distance breaks mass-distance degeneracy  
  > "As stellar mass is highly degenerate with source distance (cite: Czekala2015), placing some constraint on source distance is important." (Appendix: The MCMC Fitting Procedure)
- Alternative: Inclinations above 90 deg not distinguished; limited i<90  
  > "so we limit $i < 90^{\circ}$." (Appendix: The MCMC Fitting Procedure)
- How they decided it was enough: _not stated_
- Limitation (authors): DH Tau mass may be affected by strong foreground absorption  
  > "but it suffers from strong foreground absorption that may affect our mass estimate." (abstract)
- Limitation (authors): Some walkers not converged and discarded for computational cost  
  > "the computational demands of these fits are significant, so we opt not to continue running the fits." (Appendix: The MCMC Fitting Procedure)
- Caveat (inferred, ours): Simplified disk model (vertically isothermal, no radial/vertical velocity) may bias masses at percent level
- Caveat (inferred, ours): Walker-discarding cut is ad hoc
- Caveat (inferred, ours): Dynamical mass depends on assumed inclination and CO emission geometry
- Caveat (inferred, ours): Only three sources

## Reproducibility

- Data public (paper): ALMA project data cited; pdspy public on GitHub  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00773.S." (Acknowledgments)
- Products in archive: _not stated_
- Code: pdspy publicly available at github.com/psheehan/pdspy  
  > "`pdspy` can handle both spectral line and continuum observations, and is now publicly available." (1 Introduction)
- Missing: CASA version
- Missing: exact clean parameters and channel selection
- Missing: fit configuration files
- Missing: photometry values
- Data volume (inferred): ~10-30 GB total for three short Band 6 execution blocks
- Score (inferred): 3/5, Public data and public code, with MCMC setup well described, but imaging parameters and many fit configuration details are missing, and compute is heavy.
- Rediscovery candidate: yes, Public ALMA data, public code, and numeric stellar masses with stated priors and method.

## Links

- Method: (cite: Sheehan2018b) (pdspy code)
- Method: (cite: Czekala2015) (Keplerian disk dynamical mass methodology)
- Method: (cite: Andrews2013) (evolutionary track mass method)
- Companion: (cite: Wu2017a; Wu2017b; Wu2017c) (Same ALMA program, companion results)
- Related: Gaia DR2

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
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
  "facts": 83,
  "stated": 46,
  "rate": 0.554
 },
 "evidence_ok": true
}
```

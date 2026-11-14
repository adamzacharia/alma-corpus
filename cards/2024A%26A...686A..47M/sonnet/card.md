# A possible relation between global CO excitation and massive molecular outflows in local ULIRGs

`2024A&A...686A..47M` | Astronomy and Astrophysics 2024 | first author: Montoya Arroyave, I. | arXiv: 2402.17851 | DOI: 10.1051/0004-6361/202348292

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: Is there a link between global CO excitation and the presence of broad/high-velocity CO components tracing massive molecular outflows in local ULIRGs?  
  > "A connection between outflows and molecular gas excitation has however never been established" (abstract); "we will test the hypothesis of a relation between CO excitation and the appearance of broad and/or high-velocity CO spectral components" (4.1 Analysis of line widths as a function of $J_{\rm up}$ of the CO transition)
- Target **17 local ULIRGs (e.g. IRAS F01572+0009, IRAS 17208-0014, IRAS 09022-3615)**: coordinates listed per source in the sample table (e.g. IRAS F01572+0009 01:59:50.253 +00:23:40.87)  
  > "We now extend the analysis to higher-$J$ CO data ($4\leq J_{\rm up} \leq 7$) for 17 ULIRGs" (2.1 The sample); "IRAS F01572+0009 | 0.1631 | 806.66 | 01:59:50.253 | +00:23:40.87" (Table 1); z/distance 0.04<z<0.18; D_L listed per source  
  > "We now extend the analysis to higher-$J$ CO data ($4\leq J_{\rm up} \leq 7$) for 17 ULIRGs" (2.1 The sample); "IRAS F01572+0009 | 0.1631 | 806.66 | 01:59:50.253 | +00:23:40.87" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00177.S, 2013.1.00535.S, 2016.1.00140.S, 2013.1.00180.S, 2018.1.00503.S, 2016.2.00006.S, 2017.1.01398.S, 2017.1.00297.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: ALMA and ACA archival data used for some low-J CO lines (APEX is the main facility)  
  > "The low-$J$ CO data combine proprietary and archival single-dish (APEX) and archival interferometric (ACA, ALMA and IRAM PdBI) observations." (2.2.1 Low-J CO data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: varies by project; ALMA/ACA data from different configurations  
  > "The archival ALMA and ACA data were gathered from different projects with different array configurations, leading to different angular resolutions and maximum recoverable scales." (2.2.1 Low-J CO data)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=4-3 (461.041 GHz)
- Line: CO J=5-4 (576.268 GHz)
- Line: CO J=6-5 (691.473 GHz)
- Line: CO J=7-6 (806.652 GHz)
- Other facility **APEX (nFLASH460, SEPIA660, SEPIA180, SEPIA345, nFLASH230)**: New CO(4-3) to CO(7-6) spectra plus proprietary low-J CO  
  > "All mid-$J$ CO rotational transitions (with $J_{\rm up}=4,5,6,7$) were observed with the APEX telescope between October 2020 and June 2021" (2.2.2 Higher-J CO data)
- Other facility **IRAM PdBI**: Archival low-J CO interferometric data  
  > "archival interferometric (ACA, ALMA and IRAM PdBI) observations" (2.2.1 Low-J CO data)
- Other facility **Herschel**: OH 119um outflow detections in 11 of 17 galaxies  
  > "have reliably detected molecular outflow signatures in 11 out of the 17 galaxies studied in this paper" (2.1 The sample)
- External data: AGN fractions, L_IR, L_AGN and SFR of the sample  
  > "**References.** $\beta$: (cite: Veilleux+13), $\gamma$: (cite: Spoon+13), $\delta$: (cite: Fluetsch+19)." (Table 1) [from (cite: Veilleux+13; Spoon+13; Fluetsch+19)]
- External data: CO collisional data from LAMDA  
  > "The CO collisional data are taken from the Leiden Atomic and Molecular Database (LAMDA) (cite: Shoier+05)." (3.3 LVG modeling) [from (cite: Shoier+05)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: APEX K-to-Jy: 63 ± 11 Jy/K (nFLASH460), 57 ± 5 Jy/K (SEPIA660)  
  > "the average Kelvin to Jansky conversion factor measured during our observation period is $63 \pm 11$ $\mathrm{Jy~K^{-1}}$, and for SEPIA660 it is $57 \pm 5$ $\mathrm{Jy~K^{-1}}$" (2.3 Data reduction)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: uv-tapering applied where only high-resolution ALMA data were available  
  > "For the sources where only high-resolution ALMA observations were available, we applied *uv*-tapering to enhance the sensitivity to extended structures." (2.2.1 Low-J CO data)
- cell size: _not stated_
- image size: _not stated_
- masking: care with cleaning mask to recover extended emission  
  > "We re-reduced all these data paying particular attention to recovering the extended and diffuse emission (which may be affected by the choice of the cleaning mask, for example)" (2.2.1 Low-J CO data)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Full low-J CO data description, ALMA/ACA reduction, spectrum extraction apertures  
  > "A full description of low-$J$ ($J_{\rm up}\leq3$) CO data was given in (cite: MontoyaArroyave+23)" (2.2.1 Low-J CO data) [from (cite: MontoyaArroyave+23)]
- RADEX_EMCEE LVG fitting method  
  > "we use the code developed by (cite: Yang+17), `RADEX_EMCEE`" (3.3 LVG modeling) [from (cite: Yang+17)]
- Simultaneous multi-Gaussian fit with tied v_cen and sigma_v  
  > "by tying $v_{\rm cen}$ and $\sigma_v$ of each Gaussian to be equal in all CO transitions, allowing only their amplitudes to vary freely in the fit (cite: MontoyaArroyave+23)" (4.2 A possible relation between CO excitation and molecular outflows) [from (cite: MontoyaArroyave+23)]

### Not stated but needed to reproduce (our reading)

- ALMA/ACA reduction details (CASA version, robust, masks, tapers, apertures) only in Montoya Arroyave+23
- Which ALMA project supplies which source/transition
- Exact conversion of K to flux for low-J data
- Initial guesses and bounds for mpfit Gaussians
- Number of walkers/steps and convergence criteria of emcee runs
- Exact quiescent/outflow classification for sources beyond the rectangle cut in FWHM-v_cen

## Analysis recipe

1. **reduce APEX high-J spectra**: Scan inspection, baseline subtraction with line masked, co-addition, linear baseline, export at 5 km/s resolution  
  > "we then discarded those scans that were affected by baseline instabilities and other instrumental issues." (2.3 Data reduction)
   - software: GILDAS/CLASS
   - parameter: mask v in (-500, 500) km/s; output resolution ~5 km/s  
  > "we produced the final spectra and exported them with a common spectral resolution of $\delta v \approx 5$ km s$^{-1}$" (2.3 Data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **fit line profiles and measure fluxes**: Multi-Gaussian (up to 3) least-squares fit; luminosities via Solomon+97  
  > "This code uses the Levenberg-Marquardt technique to solve the least-squares problem in order to fit data (the observed spectrum) with a model (a multi-Gaussian function)." (2.4 Data analysis)
   - software: mpfit, Python
   - fitting: Levenberg-Marquardt least squares, up to three Gaussians  
  > "We allowed the fit to use up to a maximum of three Gaussian functions to reproduce the observed global line profiles" (2.4 Data analysis)
   - validation: Gaussian-fit fluxes compared with direct integration in (-1000,1000) km/s; consistent  
  > "We find that the two methods give consistent results within the statistical errors." (2.4 Data analysis)
3. **single-component LVG fit of CO SLEDs**: MCMC with pyradex inside emcee, flat log priors  
  > "We used a flat log-prior for all the parameters to set boundaries for the parameter space." (3.3 LVG modeling)
   - software: RADEX_EMCEE, pyradex, emcee, RADEX
   - parameter: n_H2 10^1.5-10^7.5 cm^-3; T_kin from T_CMB to 10^3 K; N_CO/dv 10^14.5-10^19.5; dv/dr 0.1-1000 km/s/pc  
  > "volume density $n_{\rm H_2}$ from $10^{1.5}$ to $10^{7.5}$ cm$^{-3}$" (3.3 LVG modeling)
   - assumption: H2 sole collisional partner, ortho-to-para ratio 3; X_CO/(dv/dr)=1e-5  
  > "we assume that H$_2$ is the only collisional partner of CO with an ortho-to-para ratio of 3" (3.3 LVG modeling)
   - fitting: emcee ensemble MCMC, flat log priors  
  > "A Markov chain Monte Carlo (MCMC) calculation is performed to explore the continuous parameter space" (3.3 LVG modeling)
   - validation: Single component judged inadequate for several higher-excitation sources  
  > "The CO SLED plots reported in Appendix [7](#app:spec_sleds) confirm that the LVG single component modeling is not adequate for some of our sources." (3.3 LVG modeling)
4. **line width vs J_up trend**: FWHM and v84-v16 widths per transition; Pearson correlation of averaged widths  
  > "we also estimate the 16th-84th percentile velocity interval (${\rm v_{84}}-{\rm v_{16}}$)" (4.1)
   - software: Python
   - fitting: _not stated_
   - validation: Two width estimators give similar results  
  > "The relations obtained with the two line width estimate methods show remarkably similar results." (4.1)
5. **decompose higher-excitation sources and build component SLEDs**: Simultaneous multi-Gaussian fit tied in v_cen and sigma; components in |v_cen|<150 km/s and FWHM<400 km/s are quiescent, others outflow-dominated  
  > "enclosed within $-150 < v_{\rm cen}\;{\rm [km\;s^{-1}]}<150$ and ${\rm FWHM}<400$ km s$^{-1}$" (4.2)
   - software: mpfit
   - assumption: Broad/high-velocity components are dominated by outflowing gas  
  > "we can assume that, in first approximation, the broad and/or high-$v_{\rm cen}$ components of the CO spectra are most likely dominated by molecular gas embedded in outflows" (4.2)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **GILDAS/CLASS** : APEX data reduction  
  > "We reduced the data using the `GILDAS/CLASS` software package" (2.3 Data reduction)
- **mpfit** : multi-Gaussian spectral fits  
  > "all CO line spectra were fit using `mpfit`" (2.4 Data analysis)
- **RADEX_EMCEE** : MCMC LVG modelling of CO SLEDs  
  > "`RADEX_EMCEE`[^9], which combines `pyradex`[^10] and `emcee`[^11]" (3.3 LVG modeling)
- **emcee** : MCMC sampler  
  > "which combines `pyradex`[^10] and `emcee`[^11]" (3.3 LVG modeling)
- **pyradex** : RADEX wrapper  
  > "which combines `pyradex`[^10] and `emcee`[^11]" (3.3 LVG modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| mean r41 | 0.54 | 0.03 | dimensionless | 2 | $r_{41}$ /  $0.54$  /    $0.03$    /    9 |
| mean r61 | 0.17 | 0.007 | dimensionless | 2 | $r_{61}$   /  $0.17$  /   $0.007$    /    6 |
| mean r31 | 0.77 | 0.02 | dimensionless | 2 | The average $r_{31}$ line ratio is $0.77\pm0.02$ |
| Pearson correlation of mean v84-v16 vs J_up | 0.91 (p=4.3e-3) | not stated | dimensionless | 4 | with a Pearson correlation coefficient of 0.91 and a $p$-value of $4.3\times10^{-3}$ |
| number of lines detected | 74 of 75 | not stated | lines | 2 | We detected a total of 74 (out of 75) CO lines |

## Qualitative findings

- Eight of 17 sources are higher-excitation; quiescent components have significantly less excited SLEDs than high-v/high-sigma components  
  > "the CO ladders that are characteristic of the quiescent gas are significantly less excited than those produced by considering the high-v/high-sigma gas components" (4.2)

## Claim tuples

- H: CO line width increases with J_up, linked to excitation | E: Gaussian and v84-v16 widths per transition vs J_up | R: Mean trend with Pearson 0.91, ~4 sigma, driven by higher-excitation sources | F: Broader high-J lines are consistent with outflow contribution | **supported**
- H: High CO excitation resides in outflowing gas | E: Tied multi-Gaussian decomposition of eight higher-excitation sources, separate SLEDs | R: High-v/high-sigma components are clearly more excited | F: Highly excited gas likely resides in galaxy-scale outflows; classical PDR/XDR challenged | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Single-dish spectra chosen to capture faint extended outflow emission missed by interferometers  
  > "This survey was expressly designed to be sensitive to faint and diffuse components" (Summary and conclusions)
- Alternative: Two-component LVG fit rejected due to degeneracy without J>7 lines  
  > "the lack of CO($J_{\rm up}>7$) lines in our study prevents us from fitting two different components" (3.3 LVG modeling)
- How they decided it was enough: _not stated_
- Limitation (authors): Only two measurements for r51 and r71; single-component LVG inadequate  
  > "The average ratios $r_{51}$ and $r_{71}$ are computed solely from two measurements" (2.4 Data analysis)
- Caveat (inferred, ours): Outflow attribution rests on a velocity-space cut, not spatial information
- Caveat (inferred, ours): Single-dish beams include mergers, inflows and tidal gas that can broaden lines
- Caveat (inferred, ours): The 4 sigma trend uses only 7 averaged points

## Reproducibility

- Data public (paper): APEX programme IDs and ALMA project IDs listed in acknowledgements  
  > "This publication is based on data acquired with the Atacama Pathfinder Experiment (APEX) under programme IDs 0104.B-0672, 0106.B-0674" (Acknowledgements)
- Products in archive: _not stated_
- Missing: Low-J ALMA/ACA reduction parameters (in Montoya Arroyave+23)
- Missing: Per-source ALMA project assignment
- Data volume (inferred): Small APEX spectra (MB); ALMA/ACA archival cubes tens to hundreds of GB if re-reduced
- Score (inferred): 3/5, APEX high-J analysis is well described; ALMA part deferred to a companion paper.
- Rediscovery candidate: no, ALMA is a minor component and the key recipe depends on APEX data and the companion paper.

## Links

- Method: (cite: Yang+17) (RADEX_EMCEE LVG fitting)
- Companion: (cite: MontoyaArroyave+23) (Low-J CO and [CI] data, ALMA/ACA reduction, parent sample)
- Related: APEX project E-0106.B-0674

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 8,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2018.1.00888.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 40,
  "rate": 0.513
 },
 "evidence_ok": true
}
```

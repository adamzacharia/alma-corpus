# Demographics of disks around young very low-mass stars and brown dwarfs in Lupus

`2020A&A...633A.114S` | Astronomy and Astrophysics 2020 | first author: Sanchis, E. | arXiv: 1911.06005 | DOI: 10.1051/0004-6361/201936913

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Do disks around brown dwarfs and very low-mass stars in Lupus follow the demographic relations (disk mass, size, accretion) known for disks around stars?  
  > "with the aim of testing whether the known relations for stars hold for disks around BDs." (Introduction)
- Target **Lupus brown dwarf disks (J154518.5-342125, SONYC-Lup3-7, Lup706, AKC2006-18, SONYC-Lup3-10)**: coordinates J154518.5-342125: 15:45:18.53 -34:21:24.8 (J2000)  
  > "| J$154518.5$-$342125$ | $15$:$45$:$18.53$ | \-$34$:$21$:$24.8$ | I           | $152\pm4$   |" (Table 1 (targets)); z/distance ~149-158.5 pc  
  > "| J$154518.5$-$342125$ | $15$:$45$:$18.53$ | \-$34$:$21$:$24.8$ | I           | $152\pm4$   |" (Table 1 (targets)); distance from Gaia DR2  
  > "| J$154518.5$-$342125$ | $15$:$45$:$18.53$ | \-$34$:$21$:$24.8$ | I           | $152\pm4$   |" (Table 1 (targets))

## Data provenance

- ALMA projects: 2017.1.01243.S, 2013.1.00220.S, 2016.1.01239.S, 2013.1.00226.S, 2013.1.00663.S
- bands: Band 7  
  > "observed with ALMA in Band 7 in the original Lupus disks survey" (2 Sample selection)
- frequencies and spectral setup: 4 continuum spws centered at 334.432, 336.321, 345.889, 347.821 GHz; bandwidths 2, 1.875, 1.875, 0.938 GHz  
  > "centered at $334.432$, $336.321$, $345.889$ and $347.821$ GHz and bandwidths of $2$, $1.875$, $1.875$ and $0.938$ GHz respectively" (3 Observations)
- continuum bandwidth: _not stated_
- arrays: 12 m array  
  > "with $44$, and $42$ $12$ m antennas respectively" (3 Observations)
- configurations: _not stated_
- baselines: 15.1-704.1 m (day 1), 15.1-629.2 m (day 2)  
  > "The baselines ranged between $15.1$ and $704.1$ m for the array configuration of the first day, and between $15.1$ and $629.2$ m" (3 Observations)
- angular resolution: 0.27x0.24 arcsec (robust -1); 0.36x0.33 arcsec (robust +0.5)  
  > "is $0.27^{\prime\prime} \times 0.24^{\prime\prime}$ for robust parameter $=-1$, and $0.36^{\prime\prime} \times 0.33^{\prime\prime}$ for robustness $=+0.5$" (3 Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: >12 minutes per source  
  > "for a total integration time of more than $12$ minutes per source." (3 Observations)
- observing dates: 2018 April 1 and 2  
  > "ALMA observed our targets on 2018 April 1 and April 2 with $44$, and $42$ $12$ m antennas respectively." (3 Observations)
- pi or archival as stated: _not stated_
- Other facility **X-Shooter (VLT)**: Accretion rates and stellar properties  
  > "taken from the X-Shooter observations presented by (cite: alcala2014; alcala2017)" (5 Discussion)
- Other facility **Gaia DR2**: Parallax distances  
  > "$L_{\star}$ have been adjusted accounting for updated distances by Gaia DR$2$" (2 Sample selection)
- External data: Stellar properties (SpT, Teff, AV, L*) of targets  
  > "were reported by (cite: alcala2014; alcala2017) and (cite: muzic+2014)" (2 Sample selection) [from (cite: alcala2014; alcala2017; muzic+2014)]
- External data: Band 7 fluxes and data of original Lupus disks survey  
  > "For the observations results from the Lupus disks survey (ALMA Project ID: 2013.1.00220.S), we refer to (cite: ansdell+2016)." (3 Observations) [from (cite: ansdell+2016)]
- External data: Mass accretion rates and accretion luminosities  
  > "The $\dot{M}_{\mathrm{acc}}$ and its uncertainty is taken from the X-Shooter observations presented by (cite: alcala2014; alcala2017)." (5 Discussion) [from (cite: alcala2014; alcala2017)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 5.3.0  
  > "The CASA 5.3.0 software has been used for the interferometric visibilities calibration and imaging." (3 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1517-2422 (flux and passband); J1610-3958 gain  
  > "The calibrators for the observations were J$1517$-$2422$ for flux and passband, and J$1610$-$3958$ for the complex gain calibration" (3 Observations)
- flux scale uncertainty: 10%  
  > "The flux density scale accuracy is expected to be of 10$\%$ for observations of the Lupus BD disks survey." (3 Observations)
- self calibration: not performed; sources too faint  
  > "None of the sources are bright enough to perform self-calibration." (3 Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust -1.0 (resolved) and +0.5 (unresolved)  
  > "with Briggs weighting of the visibilities ($-1.0$ and $+0.5$ robustness for resolved and unresolved objects respectively)" (3 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: continuum from line-free channels  
  > "The continuum maps are produced using the channels free from spectral line emission" (3 Observations)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.27x0.24 arcsec (r=-1); 0.36x0.33 arcsec (r=+0.5), PA 28 deg  
  > "with average position angle ($PA$) of $28^{\circ}$" (3 Observations)
- final rms: 0.07-0.12 mJy/beam for the new BDs  
  > "| SONYC-Lup$3$-$7$     | $0.52$              | $0.62$                             | $0.07$                             |" (Table 1)

### Inherited from earlier work

- Flux and rms measurement methodology identical to original Lupus survey  
  > "These values from the observations are obtained using identical methodology to the results presented in (cite: ansdell+2016) for the original Lupus disks survey." (3 Observations) [from (cite: ansdell+2016)]
- Flux correction factor 1.3 for completion-survey Band 7 data  
  > "obtaining a fluxes ratio of $1.3\pm0.009$ between both observations." (3 Observations) [from (cite: vanterwisga2018A; macgregor+2017)]
- Nuker profile modeling for stellar disks  
  > "We follow the modeling described in (cite: tripathi+2017), using the (cite: lauer+1995) formulation" (4 Modeling) [from (cite: tripathi+2017; andrews2018A; lauer+1995)]
- Fitting methodology (Galario+emcee)  
  > "For a detailed description of the methodology we refer to (cite: tazzari+2016; tazzari+2017A)." (4 Modeling) [from (cite: tazzari+2016; tazzari+2017A)]
- Dust opacity 2 cm2/g at 890um and Tdust=20 K  
  > "following previous ALMA Band $7$ observations for VLMs and BDs (cite: ricci+2014; testi+2016), and an averaged dust temperature of $T_{\mathrm{dust}} = 20$ K, as in (cite: pascucci+2016; ansdell+2016; ansdell+2018)" (4.2 Dust disk masses) [from (cite: ricci+2014; testi+2016; ansdell+2016)]

### Not stated but needed to reproduce (our reading)

- Cell size and image size for tclean
- Clean threshold, masks, deconvolver
- Line-free channel selection
- Priors and bounds of the MCMC fits
- CASA pipeline vs manual calibration
- Burn-in and how fit convergence was judged
- Distance used for conversion of dust mass formula (exact), and Planck function details
- Flux-ratio correction details for completion survey

## Analysis recipe

1. **Calibrate and image continuum**: CASA calibration and Briggs-weighted continuum imaging with line-free channels  
  > "The continuum maps are produced using the channels free from spectral line emission, with Briggs weighting of the visibilities" (3 Observations)
   - software: CASA
   - parameter: robust -1.0 / +0.5  
  > "($-1.0$ and $+0.5$ robustness for resolved and unresolved objects respectively)" (3 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure continuum flux and rms**: uvmodelfit with elliptical Gaussian or point source; curve of growth for resolved; rms in 4-9 arcsec annulus; upper limits 3 rms  
  > "The continuum flux is inferred from the *uvmodelfit* task in CASA: emission is fitted with an elliptical gaussian in case that resulting FWHM along the major axis from the fit is at least five times its uncertainty" (3 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit visibilities with disk brightness models**: Gaussian profile for BDs (6 parameters); Nuker profile for stellar disks (9 parameters); fit in uv plane  
  > "The free parameters to model the BD disks are $6$ in total" (4 Modeling)
   - software: Galario, emcee
   - parameter: 200 walkers, 20000 steps  
  > "$200$ walkers have been used" (4 Modeling)
   - assumption: Azimuthally symmetric disk  
  > "The disk is assumed to be azimuthally symmetric." (4 Modeling)
   - fitting: Affine invariant MCMC; medians and 16th/84th percentiles  
  > "To run the affine invariant Markov chain Monte Carlo (MCMC) (cite: GoodmanWeare2010)" (4 Modeling)
   - validation: Residuals at noise level; R68 tested across models and compared with Andrews+2018  
  > "Residuals are at noise level on all fitted disks, indicating that the model represents the observation faithfully." (4.4 Modeling results)
4. **Derive R68 and R95 sizes**: Radii enclosing 68% and 95% of cumulative flux from each MCMC model  
  > "These radii are computed for each model of the MCMC; the final values of $R_{68\%}$ and $R_{95\%}$ are the median of their respective PDFs" (4.4 Modeling results)
   - fitting: _not stated_
   - validation: R68 scatter across models 29.3-30.1 au vs R95 40.5-47.4 au for RXJ1556.1  
  > "The values of $R_{68\%}$ for the various models range between \[$29.3$, $30.1$\] $\mathrm{au}$" (Appendix A)
5. **Compute dust masses**: Optically thin emission, constant kappa and Tdust  
  > "using the simplifying assumption of optically thin emission and using an average temperature of $20$ K" (4.2 Dust disk masses)
   - assumption: kappa(890um)=2 cm2/g, Tdust=20 K  
  > "constant dust opacity of $\kappa_{890\mu m} = 2$ $\mathrm{cm}^2$ $\mathrm{g}^{-1}$" (4.2 Dust disk masses)
   - fitting: _not stated_
   - validation: Repeated with Andrews+2013 and van der Plas+2016 Tdust prescriptions  
  > "in Appendix [8] we show the main demographic results of this work using the dust temperature and stellar luminosity relations" (4.2 Dust disk masses)
6. **Demographic comparison BDs vs stars**: Linear regression with Bayesian linmix including upper limits; Anderson-Darling tests  
  > "obtained following the Bayesian method described in (cite: kelly2007)" (5.1.1)
   - software: linmix, scipy.stats
   - assumption: Gas-to-dust ratio 100 for total disk mass  
  > "assuming a gas-to-dust ratio of $100$" (5.1.3)
   - fitting: linmix regression; sub-luminous objects excluded  
  > "while sub-luminous objects are excluded for the fit" (5.1.1)
   - validation: Repeated with other Tdust prescriptions  
  > "Nevertheless, in Appendix [8](#sec:appendix_otherrelations) we show the main demographic results of this work using the dust temperature and stellar luminosity relations from (cite: andrews+2013; vanderplas+2016)." (Modeling, Dust disk masses)

## Software

- **CASA** 5.3.0: calibration, imaging, uvmodelfit  
  > "The CASA 5.3.0 software has been used for the interferometric visibilities calibration and imaging." (3 Observations)
- **Galario** : visibility modeling  
  > "the `Galario` (cite: tazzari+2018) and `emcee` (cite: foremanmackey+2013) packages have been used" (4 Modeling)
- **emcee** : MCMC sampling  
  > "the `Galario` (cite: tazzari+2018) and `emcee` (cite: foremanmackey+2013) packages have been used" (4 Modeling)
- **linmix** : Bayesian linear regression  
  > "implemented with the `linmix` Python package" (5.1.1)
- **scipy.stats** : Anderson-Darling test  
  > "using `scipy.stats` Python module" (5.1.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dust mass of J154518.5-342125 | 2.3 | 0.2 | Earth masses | 5 | $8.2_{-1.2}^{+1.0}$   / $13.2_{-2.0}^{+1.7}$ / $2.3 \pm 0.2$ |
| R68 of J154518.5-342125 | 8.2 | +1.0/-1.2 | au | 4 | $8.2_{-1.2}^{+1.0}$   / $13.2_{-2.0}^{+1.7}$ / $2.3 \pm 0.2$ |
| Detected BD dust mass range | 0.2-3.2 | not stated | Earth masses | 5 | The total dust mass for the detected BD disks range between $0.2$ and $3.2$ $M_{\Earth}$. |
| Mstar-Mdust slope (stars+BDs) | 1.69 | 0.19 | dimensionless | 6 | the slope and intercept become $1.69 \pm 0.19$ and $-3.89 \pm 0.13$ |
| Mdust-Macc slope (stars) | 0.69 | 0.14 | dimensionless | 6 | The resulting slope is $\alpha = 0.69 \pm 0.14$, while the intercept is $\beta = -7.26 \pm 0.36$. |
| Median accretion depletion timescale BDs vs stars | 9.5 vs 1.4 | not stated | Myr | 6 | The median value of this timescale for the BD sample is $9.5$ Myr, while for the stellar sub-sample considered is $1.4$ Myr. |
| AD test probability, Mdust/Mstar BD vs stars | 6 | not stated | percent | 6 | obtaining a probability of $6 \%$ that the BD and stellar disk populations are drawn from the same distribution |
| AD test probability, depletion timescale | 0.6 | not stated | percent | 6 | with only a $0.6 \%$ probability that the BD and stellar disks populations are drawn from the same original distribution |

## Qualitative findings

- BD disks are extremely compact; only one has a measured size  
  > "BD disks are extremely compact, size determination was only possible on one BD disk" (6 Conclusions)

## Claim tuples

- H: BD disks follow the stellar Mstar-Mdust relation | E: Regression and Anderson-Darling test of Mdust/Mstar | R: AD probability 6% (80-90% with other Tdust); slope 1.69±0.19 | F: No statistically different dust mass fraction in BDs vs stars | **supported**
- H: BD disks have different accretion behaviour than stellar disks | E: Compared depletion timescales Mdisk/Macc | R: 9.5 Myr vs 1.4 Myr, AD probability 0.6% | F: BD disks have significantly longer depletion timescale, implying possibly lower alpha viscosity | **supported**
- H: BD disk sizes follow the stellar size-luminosity relation | E: Fitted R68 for J154518.5-342125 | R: Agrees with stellar relation; others only upper limits | F: Consistent but based on a single object | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Empirical profiles and R68 used for homogeneous, model-independent size comparison  
  > "By using the Nuker profile we ensure the homogeneity on the characterization of the Lupus disks sample" (4 Modeling)
- Alternative: R95, transition radius and two-layer model rejected as size definitions  
  > "Thus, we consider $R_{68\%}$ as the most reliable size definition for our sample." (4.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Small BD sample and optical thickness may underestimate masses  
  > "We caution that our sample of VLM stars and BDs in Lupus is very limited" (5.1.1)
- Caveat (inferred, ours): Gaussian model of marginally resolved BD disks gives poorly constrained sizes
- Caveat (inferred, ours): Constant Tdust=20 K and fixed opacity drive masses
- Caveat (inferred, ours): Flux calibrator variability required ad hoc 1.3 correction for completion survey data
- Caveat (inferred, ours): Small N (9 BDs) limits statistics

## Reproducibility

- Data public (paper): ALMA data referenced by project ID  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA$\#2018$.$1$.$00544$.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Priors and imaging parameters
- Missing: Stellar masses and accretion rates from external papers
- Data volume (inferred): ~20-50 GB for the 2017.1.01243.S raw data
- Score (inferred): 3/5, Data are public and methods are well described, but imaging parameters and priors are missing, and the analysis relies on several external datasets.
- Rediscovery candidate: yes, Public data, numeric fluxes, dust masses and sizes in tables.

## Links

- Method: (cite: tazzari+2018) (Galario)
- Method: (cite: tripathi+2017) (Nuker modeling and R68)
- Method: (cite: kelly2007) (Bayesian regression)
- Companion: (cite: ansdell+2016) (Lupus disks survey)
- Companion: (cite: vanterwisga2018A) (Lupus completion survey)
- Companion: (cite: andrews2018A) (Lupus disk sizes)
- Related: Lupus disks survey
- Related: Lupus completion survey

## Checks

```json
{
 "quotes": 73,
 "quotes_ok": 73,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 5,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2013.1.00220.S",
  "2016.1.01239.S",
  "2013.1.00226.S",
  "2013.1.00663.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 84,
  "stated": 56,
  "rate": 0.667
 },
 "evidence_ok": true
}
```

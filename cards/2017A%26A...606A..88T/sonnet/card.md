# Physical properties of dusty protoplanetary disks in Lupus: evidence for viscous evolution?

`2017A&A...606A..88T` | Astronomy and Astrophysics 2017 | first author: Tazzari, M. | arXiv: 1707.01499 | DOI: 10.1051/0004-6361/201730890

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: What are the dust surface density profiles, sizes and masses of Lupus disks from uv-plane fits of ALMA 890 um continuum, and does the mass-size relation differ from Taurus/Ophiuchus (viscous evolution)?  
  > "By modeling the continuum emission with a physical disk model for passively irradiated disks (cite: Chiang:2010fk; 2001ApJ...560..957D) we determine the surface density profile of more than 20 disks and we put constraints on their midplane temperature." (Introduction)
- Target **Lupus Class II disks (22 fitted, 36 selected)**: coordinates per-source RA/Dec in source table (e.g. Sz 71 15:46:44.71 -34:30:36.05)  
  > "for sources in the Lupus I, II and IV clouds $d=150\,\textrm{pc}$, while for stars in the Lupus III cloud $d=200\,\textrm{pc}$ (cite: Comeron:2008qy)." (Table 1 notes); z/distance 150 pc (Lupus I, II, IV); 200 pc (Lupus III)  
  > "for sources in the Lupus I, II and IV clouds $d=150\,\textrm{pc}$, while for stars in the Lupus III cloud $d=200\,\textrm{pc}$ (cite: Comeron:2008qy)." (Table 1 notes); distance from Comeron 2008  
  > "for sources in the Lupus I, II and IV clouds $d=150\,\textrm{pc}$, while for stars in the Lupus III cloud $d=200\,\textrm{pc}$ (cite: Comeron:2008qy)." (Table 1 notes)

## Data provenance

- ALMA projects: 2013.1.00220.S, 2013.1.00226.S
- bands: Band 7, 890 um (335.8 GHz average)  
  > "The bandwidth-weighted average frequency of the continuum observations is 335.8 GHz (890 $\mu$m)" (Observations and sample selection)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 21.4 to 783.5 m  
  > "covering baselines between 21.4 and 783.5m" (Observations and sample selection)
- angular resolution: 0.34"x0.28" average beam  
  > "corresponding to an average beam size (for the continuum) of 0.34”$\times$0.28”" (Observations and sample selection)
- max recoverable scale: _not stated_
- sensitivity: average rms 0.25-0.41 mJy/beam  
  > "the average rms between 0.25 and 0.41 mJy beam$^{-1}$" (Observations and sample selection)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Ansdell et al. survey data; IM Lup from Cleeves program  
  > "(PI: Cleeves, I.; id: ADS/JAO.ALMA#2013.1.00226.S)" (Observations and sample selection)
- Other facility **Herschel/PACS**: 70, 100, 160 um photometry for spectral slopes to calibrate disk flaring  
  > "we use *Herschel*/PACS measurements at 70, 100 and 160 $\mu$m obtained from the *Herschel* Science Archive" (Disk flaring)
- Other facility **VLT/X-Shooter**: stellar parameters from literature  
  > "complemented by the VLT/X-Shooter spectroscopic survey by (cite: Alcala:2014uq; Alcala:2016ys)" (Observations and sample selection)
- External data: Stellar masses, luminosities, Teff, spectral types  
  > "$M_\star$ is the stellar mass as in (cite: Ansdell:2016qf), obtained using evolutionary tracks by (cite: Siess:2000qy)." (Table 1 notes) [from (cite: Ansdell:2016qf); (cite: Alcala:2014uq; Alcala:2016ys)]
- External data: Taurus-Auriga/Ophiuchus fluxes and Rc for mass-size comparison  
  > "The data have been collected from previous observations with angular resolution better than 0.75” from (cite: Andrews:2009zr; Andrews:2010fk; Isella:2010dq; 2011A&amp;A...529A.105G; Pietu:2014bh)" (Disk mass-size relation) [from Andrews 2009, 2010; Isella 2010; Guilloteau 2011; Pietu 2014]
- External data: Integrated 890 um fluxes and rms per source  
  > "$F_{890\mu\mathrm{m}}$ is the integrated flux and rms is the root mean square noise from (cite: Ansdell:2016qf)." (Table 1 notes) [from (cite: Ansdell:2016qf)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10%  
  > "The flux calibration error of these observations is estimated to be 10%." (Observations and sample selection)
- self calibration: IM Lup: two rounds of phase and one of amplitude+phase self-cal  
  > "we performed self calibration with two rounds of phase calibration and one round of amplitude and phase." (Observations and sample selection)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting (for model/residual images only)  
  > "derived from the respective visibilities with the CLEAN algorithm (cite: Clark:1980lr) and a natural weighting scheme using the software CASA 4.5.0." (Derived disk properties)
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

- Observational setup and data reduction  
  > "For additional details on the observational setup and the data reduction we refer to (cite: Ansdell:2016qf)." (Observations and sample selection) [from (cite: Ansdell:2016qf)]
- Disk model and fitting implementation  
  > "for more details we refer to (cite: Tazzari:2016qy)." (Modeling) [from (cite: Tazzari:2016qy)]
- Visibility weights computed per Wrobel & Walker  
  > "As in (cite: Tazzari:2016qy), the theoretical weights are calculated according to (cite: Wrobel:1999gf)" (Modeling methodology) [from (cite: Tazzari:2016qy)]
- Herschel photometry procedure  
  > "performing the photometry as in (cite: van-der-Marel:2016aa)" (Disk flaring) [from (cite: van-der-Marel:2016aa)]

### Not stated but needed to reproduce (our reading)

- Calibration pipeline/CASA version and calibrators for the Ansdell data (deferred to Ansdell et al.)
- Self-calibration solution intervals for IM Lup
- Initial chain positions and convergence criterion
- Code for the uv-plane fitting (Tazzari et al. 2016) availability
- Stellar spectra/SED inputs to two-layer model beyond Teff and L
- Exact Taurus/Ophiuchus sample list and flux extrapolation details
- Specific disk inner-radius grid and radial grid details

## Analysis recipe

1. **Select sub-sample**: Exclude edge-on, gapped, binary, no-stellar-parameter, irregular and unresolved (F<4 mJy) disks from 61 detections, add IM Lup  
  > "This results in a sub-sample of 35 sources." (Observations and sample selection)
   - fitting: _not stated_
   - validation: _not stated_
2. **Calibrate disk flaring**: Compare observed Herschel/J-band spectral slopes with model slopes for varying flaring factor f; adopt single f for all disks  
  > "we find that a disk flaring reduced by a factor $\approx3$ ($f=0.3$) gives a good representation of the slopes at all the three bands simultaneously." (Disk flaring)
   - parameter: f = 0.3  
  > "We adopt this value for all the fits that we perform in this study." (Disk flaring)
   - fitting: _not stated_
   - validation: Fits repeated for f = 0.1, 0.3, 1.0: temperature changes up to factor 1.5, Rc by at most 10%  
  > "the surface density profile remains mostly unaltered with the cut-off radius $R_c$ varying by 10% at most." (Disk flaring)
3. **Fit visibilities with two-layer disk model**: Synthetic image Fourier-transformed and sampled at observed uv points; chi^2 on visibilities; MCMC with 7 free parameters  
  > "for a given set of values of the free parameters the model produces a synthetic image of the disk that is then Fourier-transformed and sampled in the same $(u,v)-$locations of the observed visibilities." (Modeling methodology)
   - software: emcee
   - parameter: R0 = 10 au fixed; gamma in [-2,2], Sigma0 0.05-400 g/cm2, Rc 2-400 au, i 0-90, PA 0-180, offsets +/-2"  
  > "| ${R_{\mathrm{c}}}$ |        2 au        |      400 au       |" (Table 1)
   - parameter: 100 walkers, burn-in 1000-1500 steps, then 4000-5000 steps  
  > "we perform the fits using one hundred chains" (Modeling methodology)
   - assumption: dust-to-gas ratio 0.01; midplane amax=1.023 cm, q=3.0; kappa890=3.37 cm2/g; minimum temperature 7 K  
  > "assumed to be constant and equal to the typical ISM value $\zeta=0.01$" (Disk model); "7 K, which is the minimum temperature allowed in the model" (Derived disk properties)
   - fitting: Affine-invariant ensemble MCMC (emcee); posterior exp(-chi2/2) with uniform priors within bounds; median and 16-84% interval  
  > "The posterior PDF is computed as $\exp(-\chi^{2}/2)$ within a rectangular domain in the parameter space" (Modeling methodology)
   - validation: Deprojected visibility comparison and CLEAN residual maps; normalized chi-square 1.0+/-0.2  
  > "the best-fit model has usually a normalized chi-square of $1.0\pm0.2$" (Derived disk properties)
4. **Derive Rout and dust mass**: Rout = radius containing 95% of model flux; Mdust by integrating dust surface density from 0.1 au to Rout  
  > "$R_{\mathrm{in}}=0.1\,\textrm{au}$ is the inner edge of the radial grid of the model (fixed for all the disks)." (Derived disk properties)
   - fitting: _not stated_
   - validation: Compared with Ansdell et al. masses (T=20 K): within factor 2 for most  
  > "accurate within a factor of 2 at a 1$\sigma$ level for the majority of disks (15 out of 20)." (Comparison with Ansdell)
5. **Mass-size relation and population comparison**: Bayesian linear regression (linmix) of log F890 vs log Rc for Taurus/Oph, Lupus and combined; Anderson-Darling test on perpendicular offsets  
  > "we perform a linear regression using the Bayesian algorithm by (cite: Kelly:2007lq)" (Disk mass-size relation)
   - software: linmix, scipy.stats.anderson_ksamp
   - parameter: uniform priors on coefficients; fluxes normalized to 150 pc; Taurus 1.3 mm extrapolated with alpha=3.0  
  > "using an average spectral index $\alpha=3.0$ that corresponds to moderate grain growth" (Disk mass-size relation)
   - fitting: linmix Bayesian regression with errors on both axes  
  > "we perform a linear regression using the Bayesian algorithm by (cite: Kelly:2007lq) which allows the uncertainties on both axes to be included in the computation." (5.1 Disk mass-size relation)
   - validation: _not stated_

## Software

- **emcee** : affine-invariant MCMC  
  > "we use the implementation of the MCMC algorithm provided by the Python package `emcee`" (Modeling methodology)
- **CASA** 4.5.0: CLEAN images of data/model/residuals  
  > "using the software CASA 4.5.0" (Derived disk properties)
- **linmix** : Bayesian linear regression (Kelly 2007)  
  > "We use the `linmix` Python package which implements (cite: Kelly:2007lq)" (footnote 3)
- **scipy.stats.anderson_ksamp** : Anderson-Darling two-sample test  
  > "We used the implementation of the test as provided in `scipy.stats.anderson_ksamp`" (footnote 4)
- **matplotlib** : figures  
  > "Figures have been generated using the Python-based `matplotlib` package" (Acknowledgements)
- **triangle** v0.1.1: corner plots  
  > "Staircase plots of PDFs have been generated with a user-modified version of the Python-based `triangle` package" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Sz 71 Rc | 84.68 | 1.00 | au | 3 | / Sz 71 / $0.25\pm{0.01}$ / $16.19\pm{0.24}$ / $84.68\pm{1.00}$ |
| IM Lup Mdust | 439.46 | 3.76 | Earth masses | 4 | $504.01\pm{0.10}$ / $439.46\pm{3.76}$ |
| Average gamma | 0 | 0.6 | dimensionless | 3 | The average radial slope for the sample of 22 disks is $<\gamma> = 0\pm 0.6$ |
| Taurus/Oph mass-size slope | 0.8 | 0.1 | dimensionless | 5 | \log F_{890\,\mu\mathrm{m}} = (0.8\pm0.1)\log R_{c} + (0.84\pm0.2) |
| Lupus mass-size slope | 0.8 | 0.2 | dimensionless | 5 | \log F_{890\,\mu\mathrm{m}} = (0.8\pm 0.2)\log R_{c} + (0.7\pm 0.3) |
| Anderson-Darling probability full sample | <=0.2 | not stated | percent | 5 | The AD test on the full sample gives a very low probability that the two samples are drawn by the same parent distribution ($\le 0.2$%). |
| AD probability for 0.7-1 Msun subsample | ~8 | not stated | percent | 5 | then the null hypothesis cannot be excluded (p$\sim$8%) |

## Qualitative findings

- Most disks are well described by a smooth exponentially tapered profile; IM Lup and Sz 98 show ring-like residuals  
  > "except for Sz 98 and IM Lup, for which we find a ring-like residual emission with flux $\lesssim 15\%$ of the integrated flux." (Conclusions)
- Masses are systematically larger than constant-20 K estimates because model disk-averaged temperatures are below 20 K  
  > "Our masses tend to be slightly larger as our disk-averaged temperatures $<T_\mathrm{mid}>$ are generally smaller than 20 K." (Conclusions)

## Claim tuples

- H: Do Lupus disks differ in mass-size relation from younger Taurus/Ophiuchus disks? | E: Linmix regressions and Anderson-Darling test on offsets | R: Lupus relation lies below Taurus/Oph; AD p<=0.2% for full sample, ~8% for 0.7-1 Msun | F: Lupus disks larger and fainter, tentatively consistent with viscous spreading; other mechanisms not excluded | **partially**
- H: Are constant 20 K flux-to-mass conversions biased? | E: Compare fitted masses with Ansdell et al. | R: Masses within factor 2, slightly larger; no Tmid trend with stellar properties | F: Constant-T assumption introduces no bias vs stellar mass | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Radial drift, photoevaporation, grain growth, planet formation as alternatives to viscous spreading cannot be ruled out  
  > "The current observations at 890$\mu$m do not allow us to rule out these alternative processes." (Disk mm fluxes: caveats)
- How they decided it was enough: _not stated_
- Limitation (authors): Constant dust-to-gas ratio and constant opacity assumed; slope may be shallower than real  
  > "we caution that the slope of $\Sigma(R)$ derived here might be shallower than the real one" (Distribution of surface density profiles)
- Caveat (inferred, ours): Single average flaring factor applied to all disks
- Caveat (inferred, ours): Taurus/Oph comparison sample is biased to high masses and heterogeneous
- Caveat (inferred, ours): Lupus III distance 200 pc vs Gaia 150 pc affects the offset
- Caveat (inferred, ours): Small samples in 0.7-1 Msun bin

## Reproducibility

- Data public (paper): ALMA project codes given  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00220.S, ADS/JAO.ALMA#2013.1.00226.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Fitting code from Tazzari et al. 2016 not stated as released
- Missing: Data calibration details deferred to Ansdell et al.
- Missing: IM Lup self-calibration parameters
- Data volume (inferred): ~50-200 GB raw for two ALMA Band 7 projects; much less for calibrated visibilities
- Score (inferred): 3/5, Data public and model well described with priors and bounds, but fitting code and calibration details are inherited from other papers.
- Rediscovery candidate: no, Fitting code is external and not stated as released; heavy MCMC with a custom two-layer model.

## Links

- Method: (cite: Tazzari:2016qy) (disk model and uv-plane MCMC implementation)
- Method: (cite: Ansdell:2016qf) (data reduction and observations)
- Companion: (cite: Ansdell:2016qf) (source ALMA Lupus survey)
- Companion: (cite: Manara:2016lr) (disk mass vs accretion rate in same Lupus dataset)
- Related: ALMA Lupus survey (Ansdell et al. 2016)
- Related: Upper Scorpius and Chamaeleon I ALMA surveys

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 47,
  "rate": 0.573
 },
 "evidence_ok": true
}
```

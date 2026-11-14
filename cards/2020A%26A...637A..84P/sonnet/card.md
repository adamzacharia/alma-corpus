# The ALMA view of the high-redshift relation between supermassive black holes and their host galaxies

`2020A&A...637A..84P` | Astronomy and Astrophysics 2020 | first author: Pensabene, A. | arXiv: 2002.00958 | DOI: 10.1051/0004-6361/201936634

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: What is the relation between BH mass and host-galaxy dynamical mass at 2<z<7 when dynamical masses come from full kinematical modelling of the cold gas rather than virial estimates?  
  > "our aim is to study the $M_\text{BH}-M_{dyn}$ relation of a sample of $2<z<7$ quasars by constraining their galaxy masses through a full kinematical modelling of the cold gas kinematics" (abstract)
- Target **72 archival z>1.5 QSOs (32 with line detections, 10 in final sample, e.g. SDSS J0923+0247)**: coordinates listed per object in sample table  
  > "observations of $z>1.5$ QSOs on the ALMA data archive public as of June 2017 for a total of $72$ QSOs in the redshift range $1.5<z<7.1$." (2 ALMA data selection and reduction); z/distance z_cat from SIMBAD; z refined from integrated [CII]/CO spectra  
  > "observations of $z>1.5$ QSOs on the ALMA data archive public as of June 2017 for a total of $72$ QSOs in the redshift range $1.5<z<7.1$." (2 ALMA data selection and reduction); distance from SIMBAD for catalog z; own Gaussian fits of integrated spectra  
  > "observations of $z>1.5$ QSOs on the ALMA data archive public as of June 2017 for a total of $72$ QSOs in the redshift range $1.5<z<7.1$." (2 ALMA data selection and reduction)

## Data provenance

- ALMA projects: 2011.0.00206.S, 2012.1.00240.S, 2012.1.00882.S, 2013.1.00815.S, 2013.1.01153.S, 2015.1.00228.S, 2015.1.00399.S, 2015.1.00606.S, 2015.1.01115.S, 2015.1.01247.S, 2016.1.00544.S, 2016.A.00018.S
- bands: Different ALMA bands depending on transition and redshift  
  > "Different ALMA bands were involved according to the atomic/molecular transition targeted and the redshift of the sources." (2 ALMA data selection and reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Beams ~0.17-5.4 arcsec; typical ~0.5 arcsec  
  > "The typical angular resolution of the observations ($\sim0.5\si{\arcsecond}$) is frequently not good enough" (10 Conclusions)
- max recoverable scale: _not stated_
- sensitivity: Line sensitivity over 10 km/s of ~0.5-1.9 mJy/beam  
  > "$^{e}$Line sensitivity over $10\,\si{km\,s^{-1}}$." (Table notes)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Public archival data as of June 2017, plus deeper data public by end of February 2018  
  > "We thus picked deeper observations from the archive for this final sub-sample of sources that became public while the work was in progress (by the end of February 2018)." (2 ALMA data selection and reduction)
- Line: [CII] 158 micron fine-structure (not stated)
- Line: CO J=4-3 and 3-2 (not stated)
- Other facility **LBT/LUCI**: New NIR spectra targeting CIV (MgII for one source) for BH mass estimates  
  > "We thus obtained NIR spectra of the quasars with LUCI (LBT Utility Camera in the Infrared) targeting the CIV line and the adjacent continuum" (5.2 Black hole mass from LBT data)
- External data: BH masses and MgII FWHM / L3000 from literature  
  > "Black hole mass estimated using SE virial relation in Eq. [\[eq:se_virial_BH\]](#eq:se_virial_BH) when possible, otherwise, the value provided here is the one available in literature" (Table 3) [from Ban2015, Tra2011, Wan2013, She2019, DeR2011, Sha2017, Ven2015, DeR2014]
- External data: Redshifts from SIMBAD  
  > "Redshift values retrieved from SIMBAD Astronomical Database" (Table 1 notes) [from SIMBAD]
- External data: Local reference relations and Gamma(z) relation  
  > "we also overplot the relation found by (cite: Decarli+2010) using galaxy stellar masses of a sample of quasars at $z\apprle3$, extrapolated up to $z=7$" (8.1) [from (cite: Decarli+2010); (cite: DML2019); (cite: Kormendy+2013); (cite: Reines+2015)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline in CASA, using the calibration scripts of each observation  
  > "The collected data were calibrated using the ALMA pipeline in the Common Astronomy Software Applications, CASA (cite: McMullin), by executing the appropriate ALMA calibration scripts corresponding to each specific observation." (2 ALMA data selection and reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Attempted, no improvement for almost all, not used  
  > "Self-calibration was attempted but showed no additional improvement for almost all observations and was not used for the final cubes." (2 ALMA data selection and reduction)

### Imaging

- task: CASA tclean (continuum in MFS; line cubes after uvcontsub)  
  > "The continuum-subtracted line visibilities were then imaged using `tclean`." (2 ALMA data selection and reduction)
- deconvolver: _not stated_
- weighting robust: Briggs, robust R=0.5 (continuum)  
  > "`briggs` weighting scheme (with robustness parameter $R=0.5$)" (2 ALMA data selection and reduction)
- uv taper: _not stated_
- cell size: ~B_min/7; typical 0.025-0.05 arcsec  
  > "the pixel size was commonly set to $\sim B_{min}/7$" (2 ALMA data selection and reduction)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Zeroth-order polynomial fit in uv plane with uvcontsub  
  > "fitting the continuum emission with a zeroth order polynomial[^2] that was then subtracted from the spectral windows containing the line using the CASA task `uvcontsub`" (2 ALMA data selection and reduction)
- line free channels: Determined by inspecting visibilities; for undetected lines 300 km/s line width and literature redshift  
  > "The line-free channels were determined by inspecting the visibilities in all the frequency sidebands." (2 ALMA data selection and reduction)
- primary beam correction: Applied to continuum and cubes  
  > "both continuum images and the line cubes were corrected for the primary beam response." (2 ALMA data selection and reduction)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Residual red/blue maps test for resolved kinematics  
  > "we performed the same analysis computed by (cite: Carniani+2013) for ALMA \[CII\] observations of a QSO at $z=4.7$" (3.3) [from (cite: Carniani+2013)]
- Disc model fitting method (flux map then velocity map)  
  > "we basically adopted the same method used in (cite: Cresci+2009) and (cite: Carniani+2013)" (4.1) [from (cite: Cresci+2009); (cite: Carniani+2013)]
- SE virial BH relation calibrated on Sani+2011 scaling relations  
  > "we used the relation by (cite: Bongiorno+2014), which was calibrated by assuming the BH-galaxy scaling relations by (cite: Sani+2011)" (5.1) [from (cite: Bongiorno+2014)]
- Tex=100 K for [CII] mass  
  > "$T_{ex}$ the excitation temperature that we set equal to $T_{ex}=100\,\si{K}$ (cite: Venemans+2017b)" (Appendix 11) [from (cite: Venemans+2017b)]

### Not stated but needed to reproduce (our reading)

- Which ALMA band/spectral windows and line-free channel ranges per source
- Exact array configurations, observing dates and exposure times
- CASA/pipeline version
- Per-source cleaning thresholds, masks, number of iterations
- Priors on sin(beta) beyond chi2 curve cut; exact data-model convolution PSF handling
- Initial guesses for the Gaussian line fits
- LSF value for each dataset (only given for J0923)

## Analysis recipe

1. **Calibrate and image archival data**: ALMA pipeline calibration, uv continuum subtraction, tclean cubes with pixel ~B_min/7 and 40-70 km/s channels  
  > "we obtained cubes with a typical pixel size of $0.025\si{\arcsecond}-0.05\si{\arcsecond}$ and with a spectral bin width set to $40-70$ km/s." (2)
   - software: CASA
   - parameter: briggs robust 0.5 for continuum  
  > "`briggs` weighting scheme (with robustness parameter $R=0.5$)" (2)
   - fitting: _not stated_
   - validation: _not stated_
2. **Spaxel-by-spaxel Gaussian line fits to make flux, velocity, dispersion maps**: Single Gaussian (A, nu_obs, sigma) fitted in a spiral path from the central pixel, chi-square minimisation; keep pixels with peak >=1.5 rms and flux error <=50%  
  > "The underlying idea of the procedure is the subsequent performance of the line fit in all spaxels starting from the central pixel and moving away following a spiral-like path." (3); "(1) the peak of the best-fitting Gaussian is $\ge1.5\times rms$ in the corresponding channel; (2) the percentage relative error on the flux value is $\le50\%$." (3.2)
   - parameter: spiral size d~20-25 pixels, ~1200-2000 pixels per source  
  > "a typical value of $d\sim20-25$ pixels" (3)
   - fitting: minimum chi-square  
  > "We used the minimum chi-square method to estimate the best-fitting parameters." (3)
   - validation: _not stated_
3. **Integrated spectra, redshift, FWHM, flux**: Sum fitted spectra; Monte Carlo with 2000 noise realisations, Gaussian fit to z histogram  
  > "Firstly, we collected a large number (e.g. 2000) of different integrated spectra obtained by adding a random value extracted from a normal distribution" (3.1)
   - fitting: single Gaussian per integrated spectrum  
  > "Then, we performed the fit of each spectrum with a single Gaussian" (3.1)
   - validation: _not stated_
4. **Test whether kinematics are spatially resolved**: Red/blue residual maps after fitting amplitude only with fixed nu and sigma; look for symmetric positive/negative lobes  
  > "we expect the blue and red residual maps to show two symmetric lobes: a positive and negative lobe at the opposite side with respect to the map centre" (3.3)
   - fitting: _not stated_
   - validation: 14 of 32 objects show no resolved kinematics and are excluded  
  > "we conclude that 14 of them $(\sim45\%)$ show no evidence of spatially resolved kinematics." (3.3)
5. **Fit flux maps for scale radius R_D**: 2D fit of Monte Carlo thin exponential disc model (5e6 clouds, R=20 pixels) convolved with PSF; fit repeated for fixed beta from 5 to 90 deg in 5 deg steps  
  > "We thus generated simulated maps using a 3D disc model with radius of $R=20$ pixels filled by $N_{p}=5\times 10^6$ clouds." (4.2); "fixing the disc inclination angle ($\beta$) to $5\,{\rm deg}$ and up to $90\,{\rm deg}$ with a step size $\Delta\beta = 5\,{\rm deg}$" (4.2)
   - software: cap-mpfit (pPXF)
   - parameter: penalty P=5*N_out added to chi2  
  > "penalty term $\mathcal{P}=5\times N_{out}$" (4.2)
   - assumption: Thin disc, exponential surface density, stellar mass distributed like gas, negligible dark matter (Freeman disc)  
  > "The galaxy stellar mass is distributed as the gas mass component" (4)
   - fitting: Levenberg-Marquardt chi2 minimisation  
  > "performing a Levenberg-Marquardt least-squares minimisation between the data and the model" (4.2)
   - validation: _not stated_
6. **Fit velocity maps for M_dyn**: MCMC fit of Freeman rotation curve model with free [V_sys, mu=log(Mdyn sin^2 beta), gamma, sin beta, x0, y0]; R_D fixed from flux fit  
  > "We thus maximised Eq. [\[eq:lnlike\]](#eq:lnlike) using $[V_{sys},\mu,\gamma,\sin\beta, x_0, y_0]$ as free parameters" (4.3)
   - software: emcee
   - parameter: 50 walkers, 1000 steps  
  > "We set up the MCMC procedure with 50 walkers performing 1000 steps each for a total of $5\times10^{4}$ evaluations of the log-likelihood function." (footnote 3)
   - fitting: Gaussian priors on centre (width 0.1 pixel), box priors on PA and Mdyn>0, inclination restricted by flux-map chi2_m(beta) curve; 16/50/84 percentiles  
  > "we assumed Gaussian priors for the coordinates of the galaxy centre" (4.3)
   - validation: Compared with literature kinematic models and with spectroastrometric and virial masses  
  > "We conclude that the two estimators are consistent within uncertainties." (Appendix 13)
7. **Fit M_BH-M_dyn relation and Gamma(z)**: Fixed slope 1.01 from de Nicola+2019, fit normalisation alpha with bootstrap (10^4 iterations)  
  > "we performed the fit assuming fixed slope $\beta = 1.01\pm 0.07$ as found by (cite: DML2019), and the normalisation $\alpha$ as the only free parameter." (8)
   - fitting: bootstrap on chi2 minimisation  
  > "we executed the fit adopting the bootstrap method on the standard $\chi^2$ minimisation." (8)
   - validation: _not stated_

## Software

- **CASA** : Pipeline calibration, tclean, uvcontsub, 2D Gaussian fits of flux maps  
  > "using the CASA task `tclean` and `briggs` weighting scheme" (2)
- **cap-mpfit (pPXF)** : Levenberg-Marquardt fits of flux maps  
  > "we carried out the 2D map fit using the `cap-mpfit` PYTHON procedure part of the `pPXF` package" (4.2)
- **emcee** : MCMC fit of velocity maps  
  > "we used the PYTHON affine invariant Markov chain Monte Carlo (MCMC) ensemble sampler `emcee`" (4.3)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Normalisation alpha of log MBH = alpha + 1.01(log Mdyn - 10.8) | 9.4 | 0.3 | dimensionless | 7 | $$\begin{equation}
 \alpha = 9.4 \pm 0.3. 
\end{equation}$$ |
| Mdyn SDSS J1328 (No. 6) | 0.26 | +0.03/-0.02 | 1e10 Msun | 6 | / 6         /              / $4.64616\pm0.00002$    / $0.776 \pm 0.015$ / $0.26^{+0.03}_{-0.02}$             / $0.84^{+0.02}_{-0.03}$ / |
| Mdyn PSO J167-13 (No. 26) | 1.69e11 | +0.14/-0.11 (x10^11) | Msun | 6 | $4.28 \pm 0.08$   / $1.69^{+0.14}_{-0.11}\times10^{1}$ / $0.83^{+0.03}_{-0.04}$ |
| Mdyn CO(3-2) source No. 2 | 2.6 | +1.5/-0.9 | 1e10 Msun | 6 | $2.307262\pm0.000007$  / $2.95 \pm 0.11$   / $2.6^{+1.5}_{-0.9}$ |
| Fraction of 32 objects with unresolved kinematics | 14 (~45%) | not stated | objects | 4 | we conclude that 14 of them $(\sim45\%)$ show no evidence of spatially resolved kinematics. |
| Turbulent support mass J0923 | 1.3e9 | not stated | Msun | 0 | we obtain $M_{\sigma} \sim 1.3\times10^9\,M_{\astrosun}$. |
| LBT CIV-based MBH of J2310+1855 | 6e9 | not stated | Msun | 0 | we derived a CIV-based $M_\text{BH}$ estimate of $6\times10^{9}\,M_{\astrosun}$ |

## Qualitative findings

- Beam smearing makes inclination and dynamical mass nearly degenerate at the typical ~0.5 arcsec resolution.  
  > "making the disc inclination angle and galaxy dynamical mass almost degenerate parameters." (10)
- Virial masses and kinematic dynamical masses are not correlated.  
  > "but they appear not to be correlated, confirming that virial mass is not a reliable dynamical mass estimate of the host galaxy." (9.3)

## Claim tuples

- H: The MBH-Mdyn relation at high z lies above the local relation | E: Kinematic modelling of resolved [CII]/CO discs, MBH from literature/virial, fit of normalisation with fixed slope | R: alpha = 9.4±0.3; MBH ~10x higher at given Mdyn | F: The relation evolves with redshift; six of ten quasars lie above the local relation | **supported**
- H: Some high-z quasars have MBH/Mdyn consistent with local values | E: Gamma=MBH/Mdyn vs z | R: Four quasars at z~4-6 have ratios consistent with local | F: Preliminary evidence of Gamma decreasing at z>~6 | **partially**
- H: Virial masses are reliable proxies for Mdyn | E: Compare Mvir with kinematic Mdyn | R: Roughly agree but uncorrelated | F: Virial masses are unreliable; spectroastrometry is better | **refuted**

## Reasoning

- Why this data: ALMA resolves cold-gas kinematics unaffected by quasar nuclear emission  
  > "thus allowing observations that are not affected by the non-stellar emission of the central source." (1)
- Why this method: _not stated_
- Alternative: CIV-based MBH of J2310+1855 rejected in favour of MgII due to CIV outflow bias  
  > "In the following, we refer to the MgII estimate from (cite: Shen+2019), because of the aforementioned issues related to CIV-based measurements." (5.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Poor angular resolution prevents constraining Mdyn for most; thin-disc assumption too simple for some perturbed systems; MBH systematics up to ~0.4 dex  
  > "it is still very challenging to infer the dynamical mass due to the poor angular resolution and sensitivity of current observations." (10)
- Caveat (inferred, ours): Final sample is small (8-10) and selection of resolved discs may bias toward massive hosts
- Caveat (inferred, ours): Inconsistent counts of final sample (8, 10, 13) across sections
- Caveat (inferred, ours): Mixed BH-mass estimators with different calibrations
- Caveat (inferred, ours): Fixed-slope fit with few points gives little constraint on evolution
- Caveat (inferred, ours): Mdyn from thin disc model with no dark matter and beam smearing handled by simple convolution

## Reproducibility

- Data public (paper): All data public ALMA archive data  
  > "we retrieved public observations of 72 quasar host galaxies" (abstract)
- Products in archive: _not stated_
- Missing: Kinematic modelling code not released
- Missing: Per-source imaging details and CASA version
- Missing: Line-free channel selections
- Data volume (inferred): Large: ~32 archival datasets across 12 projects, probably several hundred GB raw
- Score (inferred): 3/5, Data public and method well described, but code unreleased and many per-source settings missing.
- Rediscovery candidate: no, Custom unreleased modelling code and many unstated per-source choices.

## Links

- Method: (cite: Carniani+2013) (Resolved-kinematics test and disc model method)
- Method: (cite: Cresci+2009) (Disc fitting approach)
- Method: (cite: Gnerucci+2011) (Spectroastrometry)
- Method: (cite: Bongiorno+2014) (SE virial BH relation)
- Companion: (cite: Decarli+2018) (Virial-mass based MBH-Mdyn at z>6)
- Companion: (cite: Venemans+2016) (Earlier high-z MBH-Mdyn)
- Companion: (cite: Neeleman+2019) (High-resolution [CII] modelling of overlapping sources)

## Checks

```json
{
 "quotes": 79,
 "quotes_ok": 79,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 12,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 84,
  "stated": 52,
  "rate": 0.619
 },
 "evidence_ok": true
}
```

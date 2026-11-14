# Modeling ALMA Observations of the Warped Molecular Gas Disk in the Red Nugget Relic Galaxy NGC 384

`2024ApJ...975..179C` | The Astrophysical Journal 2024 | first author: Cohn, Jonathan H. | arXiv: 2409.08812 | DOI: 10.3847/1538-4357/ad7bb0

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: What is the supermassive BH mass and stellar M/L in the compact relic galaxy NGC 384 from warped-disk molecular gas dynamics, and does it lie on the BH scaling relations?  
  > "In this work, we measure the BH mass in NGC 384 with molecular gas dynamics, accounting for a kinematic twist in the gas disk." (Introduction)
- Target **NGC 384**: coordinates RA 01h07m25.0181s, Dec +32d17m33.798s (J2000), continuum maximum  
  > "We adopt an angular diameter distance of 55 Mpc to NGC 384, where 267 pc spans 1$''$" (Introduction); "RA = $01^{\mathrm{h}} 07^{\mathrm{m}} 25.0181^{\mathrm{s}}$ and Dec = $+32^\circ 17\ensuremath{'} 33\ensuremath{''}{798}$ (J2000), the maximum of the continuum emission." (Table 2 notes); z/distance 55 Mpc angular diameter distance (267 pc/arcsec)  
  > "We adopt an angular diameter distance of 55 Mpc to NGC 384, where 267 pc spans 1$''$" (Introduction); "RA = $01^{\mathrm{h}} 07^{\mathrm{m}} 25.0181^{\mathrm{s}}$ and Dec = $+32^\circ 17\ensuremath{'} 33\ensuremath{''}{798}$ (J2000), the maximum of the continuum emission." (Table 2 notes); distance from Virgo + Great Attractor + Shapley infall model (Mould2000) Hubble-flow distance in NED, H0=73  
  > "We adopt an angular diameter distance of 55 Mpc to NGC 384, where 267 pc spans 1$''$" (Introduction); "RA = $01^{\mathrm{h}} 07^{\mathrm{m}} 25.0181^{\mathrm{s}}$ and Dec = $+32^\circ 17\ensuremath{'} 33\ensuremath{''}{798}$ (J2000), the maximum of the continuum emission." (Table 2 notes)

## Data provenance

- ALMA projects: 2016.1.01010.S
- bands: Band 6  
  > "We obtained ALMA band 6 observations of NGC 384 on 2016 October 13" (2.2 ALMA Observations)
- frequencies and spectral setup: one SPW at 227.325 GHz (CO 2-1), two continuum SPWs at 229.288 and 243.015 GHz  
  > "one spectral window centered at 227.325 GHz, the redshifted frequency of the 230.538 GHz $^{12}$CO(2$-$1) emission line" (2.2 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-6  
  > "The observations were taken in the C40$-$6 configuration" (2.2 ALMA Observations)
- baselines: 16.7 m to 3100 m  
  > "minimum (maximum) baselines of 16.7 m (3100 m)" (2.2 ALMA Observations)
- angular resolution: 0.30" x 0.16", geometric mean 0.22" (59.0 pc)  
  > "for a geometric mean of $0\ensuremath{''}{22}$, or 59.0 pc" (2.2 ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: 0.3 mJy/beam/channel rms  
  > "Emission-free regions have root-mean-square (rms) noise at the 0.3 mJy beam$^{-1}$ channel$^{-1}$ level." (2.2 ALMA Observations)
- time on source: 27.3 minutes  
  > "a total on-source exposure time of 27.3 minutes" (2.2 ALMA Observations)
- observing dates: 2016 October 13  
  > "We obtained ALMA band 6 observations of NGC 384 on 2016 October 13" (2.2 ALMA Observations)
- pi or archival as stated: PI Walsh, Cycle 4  
  > "through Program 2016.1.01010.S (PI: Walsh) in Cycle 4" (2.2 ALMA Observations)
- Line: 12CO J=2-1 (230.538 GHz)
- Other facility **HST WFC3**: H-band (F160W) and I-band (F814W) images for MGE stellar light model and dust characterization  
  > "Program GO-13050 (PI: van den Bosch) observed NGC 384 with HST WFC3 in the IR/F160W ($H$-band) and UVIS/F814W ($I$-band) filters" (2.1 HST Observations)
- External data: Stellar velocity dispersion sigma_star = 221±6 km/s and stellar age/metallicity, effective radius  
  > "$\sigma_\star = 221\pm6$ km s$^{-1}$ (cite: Yildirim2017)" (4.2) [from (cite: Yildirim2017)]
- External data: Host properties and BH masses of other compact relic galaxies for scaling-relation comparison  
  > "using the host properties listed in (cite: Cohn2021) and (cite: Cohn2023)" (4.2) [from (cite: Cohn2021; Cohn2023; Walsh2015; Walsh2016; Walsh2017)]
- External data: BH scaling relations (M-L_bul; M-M_bul and M-sigma)  
  > "Compared to the $M_{\mathrm{BH}}-L_{\mathrm{bul}}$ relation of (cite: Kormendy2013) and the $M_{\mathrm{BH}}-M_{\mathrm{bul}}$ and $M_{\mathrm{BH}}-\sigma_\star$ relations of (cite: Saglia2016)" (4.2) [from (cite: Kormendy2013; Saglia2016)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.7.2  
  > "We processed the data with Common Astronomy Software Applications (CASA) version 4.7.2" (2.2 ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J2253+1608; 10% absolute flux uncertainty  
  > "Fluxes were calibrated using the ALMA standard quasar J$2253+1608$ for flux calibration, leading to a $10\%$ uncertainty in the absolute flux calibration" (2.2 ALMA Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: TCLEAN  
  > "employing a `TCLEAN` deconvolution with Briggs weighting ($r = 0.5$; (cite: Briggs1995))" (2.2 ALMA Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, r = 0.5  
  > "Briggs weighting ($r = 0.5$; (cite: Briggs1995))" (2.2 ALMA Observations)
- uv taper: _not stated_
- cell size: 0.04" per pixel  
  > "The data cube’s pixel scale is $0\ensuremath{''}{04}$ pixel$^{-1}$." (2.2 ALMA Observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uv-plane subtraction using line-free channels  
  > "We used the line-free channels to perform $uv$-plane continuum subtraction." (2.2 ALMA Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.30" x 0.16", PA 16.17 deg  
  > "The beam PA is $16.17^\circ$ east of north." (2.2 ALMA Observations)
- final rms: 0.3 mJy/beam/channel; 124 channels of 15.07 MHz (~19.88 km/s)  
  > "the data cube has 124 frequency channels with widths of 15.07 MHz, corresponding to $\sim$19.88 km s$^{-1}$" (2.2 ALMA Observations)

### Inherited from earlier work

- Dust-masked, dust-corrected MGE construction  
  > "we follow (cite: Cohn2021) and (cite: Cohn2023) in building an MGE with the dustiest portions of the $H$-band image masked out." (2.1.1) [from (cite: Cohn2021; Cohn2023)]
- Gas-dynamical modeling code and model details  
  > "We use a molecular gas-dynamical modeling code developed and tested in previous work (cite: Cohn2021; Cohn2023)." (3 Dynamical Modeling) [from (cite: Cohn2021; Cohn2023)]
- Tilted ring warped-disk approach  
  > "following a similar approach to the concentric tilted ring model developed in (cite: Boizelle2019)" (3.1.1) [from (cite: Boizelle2019)]
- Radial motion toy models  
  > "Following (cite: Cohn2021) and (cite: Cohn2023), we employ two toy models to determine whether the data favor any radial motion." (5.2) [from (cite: Cohn2021; Cohn2023; Jeter2019)]
- HST images processed with calwf3 and AstroDrizzle  
  > "These images were processed in (cite: Yildirim2017) using the `calwf3` pipeline" (2.1 HST Observations) [from (cite: Yildirim2017)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges used for continuum subtraction
- CLEAN threshold, mask, niter and image size
- Calibrator list beyond flux (bandpass, phase) and any self-calibration
- Dynesty settings (live points, stopping criterion)
- Dynamical modeling code is unpublished (available only on request)
- Exact down-sampling alignment and noise estimation regions per channel
- Distance-dependent assumptions (M_BH scales linearly with distance)

## Analysis recipe

1. **Build stellar light model from HST**: Fit 2D MGEs to H-band image in GALFIT (dust-masked, original, dust-corrected variants) with Tiny Tim PSF  
  > "We complete an initial fit with a 2D regularized MGE (cite: Cappellari2002) and use that result as the initial guess for a 2D MGE fit in `GALFIT`" (2.1.1)
   - software: GALFIT, mgefit, Tiny Tim
   - parameter: dust-masked MGE used in fiducial model; initial I-H color cut 2.05  
  > "We start with a conservative color cut of $I-H = 2.05$" (2.1.1)
   - assumption: oblate axisymmetric galaxy, thin dust disk; Galactic R_V=3.1 extinction  
  > "we take the standard Galactic $R_V=3.1$ extinction curve (cite: Rieke1985)" (2.1.1)
   - fitting: _not stated_
   - validation: residuals ≲5% near nucleus  
  > "We repeat this process iteratively until the residuals near the nucleus are $\lesssim$5%." (2.1.1)
2. **Make moment maps and PVDs and gas mass**: Moment maps with interactive masking; MC uncertainties on moment 1; PVD along major axis; CO luminosity to gas mass  
  > "To calculate the uncertainty in the first moment, we perform a 1000-iteration Monte Carlo simulation." (2.2.1)
   - software: CASA
   - parameter: R21=0.7, alpha_CO=3.1, f_He=0.36  
  > "we assume $R_{21} \equiv L^\prime_{\mathrm{CO}(2-1)}/L^\prime_{\mathrm{CO}(1-0)} = 0.7$ (cite: Lavezzi1999)" (2.2.1)
   - assumption: alpha_CO calibrated for spiral galaxy disks  
  > "we used an $\alpha_\mathrm{CO}$ calibrated for spiral galaxy disks, which may be different from ETG disks" (2.2.1)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit gas-dynamical warped disk model to data cube**: Thin disk circular orbits in BH + stellar potential; i linear and Gamma exponential with radius; forward-model cube convolved with beam, 4x4 down-sampling, elliptical fitting region  
  > "we assume the molecular gas follows circular orbits in a thin disk." (3)
   - software: dynesty, scikit-image
   - parameter: oversampling s=6; R_fit=1.5"; q_ell=0.54; PA 132.8 deg; 43 channels; intrinsic flux map from 10 Lucy iterations  
  > "with a projected semi-major axis of $\mathcal{R}_\mathrm{fit} = 1\ensuremath{''}{5}$, an axis ratio $q_\mathrm{ell} = 0.54$" (3)
   - assumption: constant turbulent dispersion sigma_0; gas mass negligible; same inclination as stellar oblate shape  
  > "We treat the gas mass as negligible, although this assumption is tested" (3)
   - fitting: Likelihood exp(-chi2/2); dynesty nested sampling; flat priors (log-uniform for M_BH); 68% and 99.7% intervals  
  > "Flat priors are sampled for each parameter uniformly in linear space, except for $M_{\mathrm{BH}}$, which is sampled uniformly in logarithmic space." (3)
   - validation: Compared flat disk, tilted ring, linear twist models via BIC  
  > "We exclude models that have $\Delta$BIC $\geq+10$" (5.2)
4. **Quantify systematic uncertainties**: Vary warp model, MGE, radial motion, gas mass, sigma_turb, oversampling, Lucy iterations, down-sampling, fitting ellipse; sum shifts of acceptable models in quadrature  
  > "We calculate the positive and negative systematic (sys) uncertainties on $M_{\mathrm{BH}}$ and $M/L_\mathrm{H}$ by summing the respective changes in quadrature" (5.2)
   - parameter: acceptance: Delta BIC < +10  
  > "We exclude models that have $\Delta$BIC $\geq+10$" (5.2)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compare with BH scaling relations**: Compute L_H, L_K, M_star; compare M_BH to relations; Monte Carlo offset test for six relic galaxies (10,000 iterations)  
  > "We repeat this process 10,000 times" (4.2)
   - assumption: H-K=0.2 mag from SSP models; total galaxy luminosity/mass as upper bounds on bulge  
  > "$H-K=0.2$ mag from SSP models (cite: Vazdekis2010)" (4.2)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.2: data processing and tclean imaging  
  > "We processed the data with Common Astronomy Software Applications (CASA) version 4.7.2" (2.2 ALMA Observations)
- **dynesty** : nested sampling of model parameters  
  > "with `dynesty` (cite: Speagle2020), a nested sampling code" (3)
- **GALFIT** : MGE and Nuker fits to HST image  
  > "use that result as the initial guess for a 2D MGE fit in `GALFIT` (cite: Peng2010)" (2.1.1)
- **mgefit** : initial regularized MGE  
  > "We complete an initial fit with a 2D regularized MGE (cite: Cappellari2002)" (2.1.1)
- **Tiny Tim** : HST PSF  
  > "The PSF, which comes from Tiny Tim (cite: Krist2004)" (2.1.1)
- **AstroDrizzle** : HST image combination  
  > "combined using `AstroDrizzle` (cite: Gonzaga2012)" (2.1 HST Observations)
- **scikit-image** : Lucy-Richardson deconvolution of zeroth moment map  
  > "using the `lucy` task (cite: Richardson1972; Lucy1974) from `scikit-image` (cite: Walt2014)" (3)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| M_BH | 7.26e8 | +0.43/-0.48 (1σ stat), +0.55/-1.00 (sys) | Msun | 3 | $M_{\mathrm{BH}}$ $= (7.26^{+0.43}_{-0.48}$ \[$1\sigma$ statistical\] $^{+0.55}_{-1.00}$ \[systematic\])$\times 10^8$ $M_\odot$ |
| M/L_H | 1.34 | ±0.01 stat ±0.02 sys | Msun/Lsun | 3 | $M/L_H = 1.34\pm0.01$ \[$1\sigma$ statistical\] $\pm0.02$ \[systematic\] $M_\odot/L_\odot$ |
| Total CO(2-1) flux | 7.20 | ±0.06 stat ±0.72 sys | Jy km/s | 2 | The total CO(2$-$1) flux is $7.20 \pm 0.06\ \mathrm{(stat)} \pm 0.72\ \mathrm{(sys)}$ Jy km s$^{-1}$ |
| Total gas mass | 7.91e7 | ±0.07 stat ±0.79 sys (x1e7) | Msun | 2 | We find a total gas mass of ($7.91\pm0.07$ \[stat\] $\pm0.79$ \[sys\]) $\times10^7\ M_\odot$ |
| BH sphere of influence radius | 0.12 arcsec (31 pc) | not stated | arcsec | 5 | is $r_\mathrm{SOI} = 0\ensuremath{''}{12}$ (31 pc) for our fiducial model |
| Total H-band luminosity | 6.13e10 | not stated | Lsun | 5 | finding $L_H = 6.13\times10^{10}\ L_\odot$ |
| Stellar mass | 8.22e10 | not stated | Msun | 5 | finding $M_{\star} = 8.22\times10^{10}\ M_\odot$ |
| Reduced chi2 of fiducial model | 1.159 | not stated | dimensionless | 3 | with $\chi^2 = 7511.1$ and $\chi^2_\nu = 1.159$ |
| Inclination i0 / i1 | 52.6 / 59.8 | ±0.4 / ±0.3 | deg | 3 | ${52.6}$ / $\pm0.4$ |

## Qualitative findings

- Inner ~0.5" of CO disk shows a kinematic twist, not reproduced by a flat disk  
  > "the inner $\sim$0$''$5 exhibits a kinematic twist" (abstract)
- NGC 384 lies within the scatter of all three BH scaling relations, unlike most compact relics  
  > "NGC 384 lies within the scatter of those scaling relations." (abstract)

## Claim tuples

- H: A warped disk model can account for the central kinematic twist and yield M_BH | E: Fit flat, tilted ring, linear twist and exponential-Gamma warped disk models to the CO cube | R: Fiducial warped model preferred with Delta BIC +112, +53, +211 for the alternatives | F: M_BH = 7.26e8 Msun with M/L_H=1.34 | **supported**
- H: NGC 384 hosts an over-massive BH like other compact relics | E: Compare M_BH to Kormendy & Ho and Saglia scaling relations | R: M_BH is factor 2.2, 2.2, 1.9 above expected | F: Within upper scatter of the relations, unlike prior relics | **supported**
- H: The relic sample as a whole is offset above scaling relations | E: Monte Carlo comparison of six measured vs predicted BH masses | R: Dynamical median above predicted 100.0%, 99.9%, 91.5% of iterations | F: Sample still offset but preliminary | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Flat disk cannot reproduce twist; tilted rings with N≥3 unstable at low S/N, so a parameterized warp was developed  
  > "due to the low signal-to-noise of the data and the increasing number of free parameters, these models do not exhibit consistent behavior or provide robust parameter solutions." (3.1.2)
- Alternative: Flat disk, tilted ring, linear twist, exponential sigma_turb and M_BH=0 models rejected by Delta BIC  
  > "However, this model is ruled out with $\Delta$BIC $=+66.4$ compared to the fiducial model" (5.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Relatively low S/N; chi2_nu underestimated because adjacent down-sampled pixels not independent  
  > "would translate to fewer degrees of freedom and higher estimates of $\chi^2_\nu$" (Footnote 4)
- Limitation (authors): Systematic uncertainty in gas mass likely underestimated  
  > "We likely underestimate the total systematic uncertainties in the gas mass" (2.2.1)
- Caveat (inferred, ours): Gas-vs-stellar dynamical systematic offset cannot be tested without stellar-dynamical M_BH for NGC 384
- Caveat (inferred, ours): Fiducial model chosen despite radial-motion models having better BIC
- Caveat (inferred, ours): Distance dependence: M_BH scales linearly with the assumed 55 Mpc

## Reproducibility

- Data public (paper): ALMA and HST data acknowledged from archives  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.01010.S." (Acknowledgements)
- Products in archive: _not stated_
- Code: Modeling code unpublished; available from corresponding author on request  
  > "Although this code is not currently published, anyone who wishes to reproduce our results may contact the corresponding author for the code." (Footnote 3)
- Missing: Unpublished dynamical modeling code
- Missing: Line-free channels, clean parameters
- Missing: dynesty configuration
- Data volume (inferred): ~5-20 GB raw for a single Band 6 execution; HST images small
- Score (inferred): 5/5, Public data and detailed model description with priors and tables, but the modeling code is unpublished and imaging details are sparse.
- Rediscovery candidate: no, Key results require the unreleased custom gas-dynamical code.

## Links

- Method: (cite: Cohn2021) (Original modeling code and systematic uncertainty framework)
- Method: (cite: Boizelle2019) (Tilted ring warped disk model and dust extinction equations)
- Method: (cite: Cohn2023) (Dust-corrected MGE method and modeling)
- Companion: (cite: Yildirim2017) (Stellar kinematics and photometry of the compact galaxy sample)
- Related: Hobby-Eberly Telescope Massive Galaxy Survey (HETMGS)
- Related: HST GO-13050

## Checks

```json
{
 "quotes": 79,
 "quotes_ok": 79,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 88,
  "stated": 61,
  "rate": 0.693
 },
 "evidence_ok": true
}
```

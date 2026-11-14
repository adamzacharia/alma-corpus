# Radiative equilibrium estimates of dust temperature and mass in high-redshift galaxies

`2020MNRAS.495.1577I` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Inoue, Akio K. | arXiv: 2004.12612 | DOI: 10.1093/mnras/staa1203

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies, milky_way_ism
- Question: Can dust temperature and mass of a high-z galaxy be derived by assuming dust radiative equilibrium, even from sparse IR data?  
  > "Here we present an algorithm for deriving the temperature and mass of dust in a galaxy, assuming dust to be in radiative equilibrium." (abstract)
- Target **A1689zD1**: coordinates RA 13h11m29.96s, Dec -01d19m18.7s (J2000), from NASA NED  
  > "$7.5\pm0.2$" (Table 1); "the magnification factor is $\mu_{\rm GL}\simeq9$; (cite: Bradley08)" (2.1 A normal, dusty star-forming galaxy, A1689zD1); z/distance z = 7.5±0.2; lensing magnification ~9  
  > "$7.5\pm0.2$" (Table 1); "the magnification factor is $\mu_{\rm GL}\simeq9$; (cite: Bradley08)" (2.1 A normal, dusty star-forming galaxy, A1689zD1); distance from Watson et al. (2015) (Lyα break)  
  > "$7.5\pm0.2$" (Table 1); "the magnification factor is $\mu_{\rm GL}\simeq9$; (cite: Bradley08)" (2.1 A normal, dusty star-forming galaxy, A1689zD1)

## Data provenance

- ALMA projects: 2016.1.00954.S
- bands: Band 8 (0.73 mm), new; Band 7 and Band 6 from literature  
  > "We have also made follow-up ALMA observations in Band 8 and have detected the dust continuum at 0.73 mm" (2.1 A normal, dusty star-forming galaxy, A1689zD1)
- frequencies and spectral setup: four 1.875 GHz spectral windows, sidebands 393.49–397.16 and 405.55–409.22 GHz, 7.8125 MHz channels  
  > "The lower and upper sidebands covered the contiguous frequency ranges of 393.49–397.16 GHz and 405.55–409.22 GHz, respectively." (2.2 ALMA Band 8 observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15–704 m, 40 antennas  
  > "using 40 antennas with baseline lengths of 15–704 m in the dual-polarization setup" (2.2 ALMA Band 8 observations)
- angular resolution: 0.61 x 0.53 arcsec, PA 65 deg  
  > "The spatial resolution of the continuum image is $0''.61 \times 0''.53$ in FWHM with the beam position angle PA $= 65^{\circ}$." (2.2 ALMA Band 8 observations)
- max recoverable scale: _not stated_
- sensitivity: 77 uJy/beam continuum rms  
  > "we estimated the rms level of the continuum image to be 77 $\mu$Jy beam$^{-1}$" (2.2 ALMA Band 8 observations)
- time on source: 48 minutes  
  > "The total on-source exposure time was 48 minutes." (2.2 ALMA Band 8 observations)
- observing dates: November 2016  
  > "in November 2016" (2.2 ALMA Band 8 observations)
- pi or archival as stated: Own program (PI A. K. Inoue); Band 7 data also used from archive  
  > "we have measured the apparent beam-deconvolved size in the archived Band 7 data" (2.2 ALMA Band 8 observations)
- Other facility **HST (H140 photometry)**: UV magnitude m_H140 = 24.64±0.05 AB, taken from Watson15  
  > "The flux density is obtained from the observed magnitude $m_{H140}=24.64\pm0.05$ AB (cite: Watson15)" (2.1 A normal, dusty star-forming galaxy, A1689zD1)
- External data: Band 6 flux 0.56±0.10 mJy at 1.33 mm  
  > "$0.56\pm0.10$" (Table 1) [from Watson et al. (2015) (cite: Watson15)]
- External data: Band 7 flux 1.33±0.14 mJy at 0.873 mm  
  > "$1.33\pm0.14$" (Table 1) [from Knudsen et al. (2017) (cite: Knudsen17)]
- External data: Redshift, H140 magnitude and lensing magnification  
  > "Watson et al. (2015)" (Table 1) [from (cite: Watson15)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline  
  > "We reduced and calibrated the data using the Common Astronomy Software Applications (CASA; (cite: McMullin07)), pipeline version 4.7.0." (2.2 ALMA Band 8 observations)
- casa version: _not stated_
- pipeline version: 4.7.0  
  > "pipeline version 4.7.0" (2.2 ALMA Band 8 observations)
- archive products used as is: _not stated_
- flux calibrator: J1256-0547 (bandpass and flux)  
  > "We used quasar J1256-0547 for bandpass and flux calibrations" (2.2 ALMA Band 8 observations)
- flux scale uncertainty: better than 10%  
  > "We estimate the flux-calibration uncertainty to be better than 10%." (2.2 ALMA Band 8 observations)
- self calibration: _not stated_

### Imaging

- task: CLEAN  
  > "We produced images with the `CLEAN` task using natural weighting with a 0.5 arcsec taper." (2.2 ALMA Band 8 observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "using natural weighting with a 0.5 arcsec taper" (2.2 ALMA Band 8 observations)
- uv taper: 0.5 arcsec  
  > "using natural weighting with a 0.5 arcsec taper" (2.2 ALMA Band 8 observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.61 x 0.53 arcsec, PA 65 deg  
  > "$0''.61 \times 0''.53$ in FWHM" (2.2 ALMA Band 8 observations)
- final rms: 77 uJy/beam  
  > "77 $\mu$Jy beam$^{-1}$" (2.2 ALMA Band 8 observations)

### Inherited from earlier work

- Photometry, redshift, lens magnification taken from Watson et al.  
  > "Watson et al. (2015)" (Table 1) [from Watson et al. (2015) (cite: Watson15)]
- Kennicutt conversion for SFR  
  > "using Kennicutt’s conversion (cite: Kennicutt98)" (2.1 A normal, dusty star-forming galaxy, A1689zD1) [from (cite: Kennicutt98)]
- CMB correction for interferometric observations  
  > "The CMB term in the parenthesis is the correction term for detection against the CMB in interferometric observations (cite: daCunha13)." (3.4 Determining the temperature and mass of dust from observations) [from (cite: daCunha13)]

### Not stated but needed to reproduce (our reading)

- CLEAN parameters (threshold, mask, cell size, image size, niter)
- line-free channel selection for the Band 8 continuum
- exact lines of sight and imfit region
- Band 7 archival project code and its reduction
- grid ranges for T_d, M_d, xi_cl in chi2 search
- number of Monte Carlo realizations beyond '>10,000'
- bounds of xi_cl grid other than lower limit of 10^-3

## Analysis recipe

1. **Measure Band 8 continuum flux and size**: Gaussian fit to the continuum image with imfit  
  > "By spatially integrating the image using the CASA task `imfit` with a 2D Gaussian profile, we estimate the continuum flux density to be $1.67 \pm 0.36$ mJy." (2.2 ALMA Band 8 observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared position and extension with Bands 6 and 7  
  > "the spatial position and extension of the Band 8 continuum are quite consistent with those in Bands 6 and 7" (2.2 ALMA Band 8 observations)
2. **Modified black-body fit**: 2D chi^2 minimisation in (T_d, M_d) to the three band fluxes with CMB correction  
  > "We have adopted a two-dimensional $\chi^2$ minimization method to find the best-fit solution in the $(T_{\rm d}, M_{\rm d})$ plane." (4.1 Modified black-body cases)
   - parameter: beta = 1, 1.5, 2; kappa_IR,0 = 30 cm2/g at 100 um  
  > "We also consider cases with the indices $\beta=1.0$ and 1.5." (4.1 Modified black-body cases)
   - assumption: fiducial kappa_UV = 5.0e4 cm2/g, kappa_IR,0 = 30 cm2/g, beta = 2.0  
  > "we have adopted $\kappa_{\rm IR,0}=30$ cm$^2$ g$^{-1}$ and $\beta=2.0$ as our fiducial set" (3.5 Dust-grain properties)
   - fitting: chi^2 minimisation; 68% ranges  
  > "We have adopted a two-dimensional $\chi^2$ minimization method to find the best-fit solution in the $(T_{\rm d}, M_{\rm d})$ plane." (4.1 Modified black-body cases)
   - validation: _not stated_
3. **Radiative-equilibrium fits for shell and homogeneous spheres**: 1D chi^2 minimisation in M_d, T_d fixed by radiative equilibrium; Monte Carlo over R and fluxes  
  > "We repeated this procedure $>10,000$ times." (4.2.1 Multi-band fit)
   - parameter: R = 0.46±0.06 arcsec from Band 7; L_UV^esc = (8.0±1.0)e43 erg/s  
  > "we used the geometric mean of the semi-major and semi-minor axes of the Band 7 continuum: $R_{\rm o}=0.''46\pm0.''06$" (2.2 ALMA Band 8 observations)
   - assumption: Single dust temperature, uniform ISM, no scattering, optically thin IR, H0=70, Om=0.3, OL=0.7  
  > "we varied $R$ and the flux densities in each realization, assuming Gaussian distributions with the observed $1\sigma$ uncertainties" (4.2.1 Multi-band fit)
   - fitting: chi^2 minimisation with Gaussian Monte Carlo  
  > "Specifically, we varied $R$ and the flux densities in each realization, assuming Gaussian distributions with the observed $1\sigma$ uncertainties as the standard deviations" (4.2.1 Multi-band fit)
   - validation: Single-band fits compared with the multi-band solution  
  > "these three single-band solutions are reasonably consistent with the multi-band solution" (4.2.2 Single-band fit)
4. **Clumpy-sphere fit (mega-grain)**: 2D chi^2 minimisation in (M_d, xi_cl) with Monte Carlo errors  
  > "We have accordingly performed a two-dimensional $\chi^2$ minimization in the $(M_{\rm d}, \xi_{\rm cl})$ plane." (4.3 Radiative-equilibrium case in the clumpy geometry)
   - parameter: lowest xi_cl limit: log10 xi_cl = -3  
  > "which is the lowest limit of $\xi_{\rm cl}$ in our calculations" (4.3 Radiative-equilibrium case in the clumpy geometry)
   - assumption: High-contrast limit C_cl >> 1  
  > "In the following, we consider only the high-contrast limit (i.e. $C_{\rm cl}\gg1$)." (3.3.3 Clumpy sphere: Mega-grain approximation)
   - fitting: chi^2 minimisation  
  > "We have accordingly performed a two-dimensional $\chi^2$ minimization in the $(M_{\rm d}, \xi_{\rm cl})$ plane." (4.3 Radiative-equilibrium case in the clumpy geometry)
   - validation: Monte Carlo distribution is bimodal  
  > "The distribution is clearly bimodal." (4.3 Radiative-equilibrium case in the clumpy geometry)

## Software

- **CASA** pipeline 4.7.0: calibration, CLEAN imaging, imstat, imfit  
  > "We reduced and calibrated the data using the Common Astronomy Software Applications (CASA; (cite: McMullin07)), pipeline version 4.7.0." (2.2 ALMA Band 8 observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Band 8 continuum flux density | 1.67 | 0.36 | mJy | 1 | we estimate the continuum flux density to be $1.67 \pm 0.36$ mJy |
| Modified BB T_d (beta=2, 3 bands) | 37.7 | 68% range 31.6–46.5 | K | 2 | 37.7 (31.6–46.5) |
| Modified BB log10 M_d (beta=2) | 7.30 | 68% range 6.96–7.66 | Msun | 2 | 7.30 (6.96–7.66) |
| Shell T_d | 70.3 | 68% range 65.2–76.7 | K | 3 | 70.3 (65.2–76.7) |
| Shell log10 M_d | 6.45 | 68% range 6.36–6.53 | Msun | 3 | 6.45 (6.36–6.53) |
| Homogeneous T_d | 57.3 | 68% range 54.7–60.3 | K | 3 | 57.3 (54.7–60.3) |
| Homogeneous log10 M_d | 6.69 | 68% range 6.61–6.75 | Msun | 3 | 6.69 (6.61–6.75) |
| Clumpy T_d | 37.8 | 68% range 31.5–46.7 | K | 4 | 37.8 (31.5–46.7) |
| Clumpy log10 M_d | 7.29 | 68% range 6.96–7.67 | Msun | 4 | 7.29 (6.96–7.67) |
| Clumpiness log10 xi_cl | -0.97 | 68% range -1.24 to -0.82 | dimensionless | 4 | $-0.97$ ($-1.24$–$-0.82$) |
| Escaping UV luminosity | 8.0e43 x (9/mu) | 1.0e43 | erg/s | 0 | we obtain $L_{\rm UV}^{\rm esc}=(8.0\pm1.0)\times(9/\mu_{\rm GL})\times10^{43}$ erg s$^{-1}$ |

## Qualitative findings

- Radiative equilibrium breaks the T_d–M_d degeneracy; a single band gives similar T_d and M_d to multi-band.  
  > "Even if we use only a single data point from the IR SED, the resulting $T_{\rm d}$ and $M_{\rm d}$ are very similar." (5 Summary)

## Claim tuples

- H: Radiative equilibrium can give T_d and M_d for a high-z galaxy from sparse IR data | E: Applied shell, homogeneous and clumpy models to A1689zD1 with three ALMA bands, and to single bands | R: Shell T_d≈70 K, homogeneous ≈57 K, M_d 10^6.5–7.3 Msun; single-band results similar | F: The algorithm is useful for galaxies with limited IR data | **supported**
- H: Clumpiness can be constrained from IR SED | E: Clumpy mega-grain fit | R: log xi_cl ≈ -1; T_d equals the modified BB value | F: xi_cl acts as an adjuster; ~10% filling factor for ~10 pc clumps | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Clumpy model allows unphysical unlimited dust mass hidden in clumps; shell/homogeneous high T_d may indicate invalid simple geometries  
  > "This means that an infinitely large amount of dust can exist in clumpy media while a constant continuum flux density is maintained, which is unphysical." (3.6 Overall behaviour)
- Caveat (inferred, ours): Single sphere assumed though Band 6 may show two components
- Caveat (inferred, ours): Result depends strongly on adopted kappa_UV and kappa_IR
- Caveat (inferred, ours): Size taken from Band 7 only
- Caveat (inferred, ours): Method not validated on simulations or galaxies with known T_d

## Reproducibility

- Data public (paper): Band 8 data labelled with project code; Band 7 described as archived  
  > "we have measured the apparent beam-deconvolved size in the archived Band 7 data" (2.2 ALMA Band 8 observations)
- Products in archive: _not stated_
- Missing: Fit codes not released
- Missing: imaging parameters beyond taper and weighting
- Missing: Band 7 project code
- Data volume (inferred): ~10 GB for Band 8 raw data (a single short track); the fits themselves use only a handful of tabulated fluxes
- Score (inferred): 4/5, Analytic formulae are fully given and inputs tabulated, so the fits are reproducible from the table; the ALMA imaging details are sparse.
- Rediscovery candidate: yes, Public data, tabulated fluxes and analytic equations give numeric results that can be recomputed.

## Links

- Method: Hirashita et al. 2014 (cite: Hirashita14) (Earlier radiative equilibrium approach extended here)
- Method: Varosi & Dwek 1999 (cite: Varosi99) (Mega-grain escape probability formulae)
- Companion: Watson et al. 2015 (cite: Watson15) (Band 6 detection of A1689zD1)
- Companion: Knudsen et al. 2017 (cite: Knudsen17) (Band 7 detection)

## Checks

```json
{
 "quotes": 67,
 "quotes_ok": 67,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 48,
  "rate": 0.676
 },
 "evidence_ok": true
}
```

# The REASONS Survey: Resolved Millimeter Observations of a Large Debris Disk around the Nearby F Star HD 170773

`2019ApJ...881...84S` | The Astrophysical Journal 2019 | first author: Sepulveda, Aldo G. | arXiv: 1906.08797 | DOI: 10.3847/1538-4357/ab2b98

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks
- Question: What are the radius, width and geometry of the HD 170773 debris disk at 1.3 mm, does it contain CO/CN gas, and how does it fit the disk radius-stellar luminosity relation?  
  > "We image the face-on ring and determine its fundamental parameters by forward-modeling the interferometric visibilities through a Markov Chain Monte Carlo approach." (abstract)
- Target **HD 170773**: coordinates 18h33m01.056s, -39d53m32.744s (J2000 pointing, proper-motion corrected)  
  > "J2000 Pointing R.A. | 18h 33m 01.056s | 18h 33m 01.056s | 18h 33m 01.057s" (Table 1); "J2000 Pointing Dec. | $-$39$^{\circ}$ 53$'$ 32.744$''$ | $-$39$^{\circ}$ 53$'$ 32.745$''$ | $-$39$^{\circ}$ 53$'$ 32.752$''$" (Table 1); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2018.1.00200.S
- bands: Band 6 (1.3 mm, 211-275 GHz)  
  > "Three ALMA Band 6 observations at 1.3 mm (211 - 275 GHz) of HD 170773 were made on 2018 Apr 29, May 3 and Jun 5." (2 ALMA Observations)
- frequencies and spectral setup: Four 2 GHz SPWs: continuum at 243.1 and 245.1 GHz; line SPWs at 230.1 and 227.2 GHz; ~1.28 km/s resolution  
  > "The correlator setup included four 2 GHz-wide spectral windows, two of which were centered at 243.1 and 245.1 GHz at low spectral resolution for continuum" (2 ALMA Observations); "The other two spectral windows were centered at 230.1 and 227.2 GHz at high spectral resolution" (2 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: ACA (7 m) and 12 m array  
  > "Observing HD 170773 with both the Atacama Compact Array (ACA) and the 12-meter array provides greater coverage of the u-v visibility space" (2 ALMA Observations)
- configurations: _not stated_
- baselines: ACA 8.9-48.9 m; 12 m 15.0-360.6 m  
  > "Min/Max baseline | 8.9 to 48.9 m | 8.9 to 48.9 m | 15.0 to 360.6 m" (Table 1)
- angular resolution: 2.15" x 1.90" (tapered)  
  > "where the beam size is 2.15$''$ by 1.90$''$" (3.1 1.3 mm Dust Continuum Image)
- max recoverable scale: _not stated_
- sensitivity: 2.8e-2 mJy/beam RMS  
  > "$\sigma_{\rm RMS} =$ 2.8$\times 10^{-2}$ mJy beam$^{-1}$" (3.1 1.3 mm Dust Continuum Image)
- time on source: 34m49s + 34m49s (ACA); 14m12s (12 m)  
  > "Time on Target | 34m 49s | 34m 49s | 14m 12s" (Table 1)
- observing dates: 2018 Apr 29, May 3, Jun 5  
  > "were made on 2018 Apr 29, May 3 and Jun 5." (2 ALMA Observations)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (230.538 GHz)
- Line: CN N=2-1 (226.875 GHz)
- Other facility **Gaia DR2**: Absolute G magnitude and BP-RP colour for stellar parameters  
  > "absolute G magnitude (6.1040$\pm$0.0004 mag, obtained from the apparent G magnitude and the parallax) and BP$-$RP color from Gaia DR2" (3.5 Stellar Parameters)
- Other facility **Herschel, Spitzer, WISE, AKARI, JCMT, APEX**: Literature photometry for the SED  
  > "JCMT/SCUBA-2 | 850 | 26$\pm$2 | mJy | 12" (Table 2)
- External data: Photometry compiled for SED fit (optical to submm)  
  > "APEX/LABOCA | 870 | 18$\pm$5 | mJy | 13" (Table 2) [from references 1-13 in Table 2, e.g. (cite: holland2017), (cite: Nilssonetal2010)]
- External data: Photodissociation timescales ~120 yr (CO) and ~61 yr (CN)  
  > "leading to photodissociation timescales of $\sim$120 and $\sim61$ years for CO and CN (cite: heays2017)" (3.4 Constraints on CO and CN Line Emission) [from (cite: heays2017)]
- External data: Radius-luminosity sample of mm-resolved disks  
  > "(cite: matra2018b) analyzed the 26 published debris disks resolved at millimeter wavelengths and found a significant correlation between their radii and host star luminosities." (4.2 Radius-Luminosity Relationship) [from (cite: matra2018b)]
- Simulation/model as data: PARSEC isochrone grid with Gaia synthetic photometry for stellar parameters  
  > "we downloaded and arranged a grid of `PARSEC` isochrones (cite: Bressan2012; chen2014; chen2015; Tang2014), using the synthetic photometry from (cite: Evans+2018)." (3.5 Stellar Parameters)

## Processing

### Calibration

- pipeline or manual: Calibrated by ALMA observatory pipeline  
  > "The interferometric visibility data was fully calibrated by the ALMA observatory using their pipeline." (2 ALMA Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1924-2914 (passband/flux)  
  > "Passband/Flux Calibrator | J1924$-$2914 | J1924$-$2914 | J1924$-$2914" (Table 1)
- flux scale uncertainty: 10% absolute flux uncertainty  
  > "including an absolute flux uncertainty of 10% added in quadrature" (3.1 1.3 mm Dust Continuum Image)
- self calibration: _not stated_

### Imaging

- task: CASA 5.4.1 tclean  
  > "We then use the `tclean` task of `CASA` 5.4.1 (cite: CASA) to inverse transform and deconvolve the visibility data" (2 ALMA Observations)
- deconvolver: _not stated_
- weighting robust: Briggs 0.5  
  > "We apply a Gaussian u-v taper of 2$''$ and a Briggs weighting factor of 0.5 to the visibilities in the imaging process." (2 ALMA Observations)
- uv taper: Gaussian 2"  
  > "We apply a Gaussian u-v taper of 2$''$" (2 ALMA Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: CASA uvcontsub  
  > "We first subtracted continuum emission from the visibilities using the `CASA` `uvcontsub` task" (2 ALMA Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Three datasets frequency-averaged then concatenated  
  > "we first average the observations in frequency to reduce the data size, then concatenate all three observations." (2 ALMA Observations)
- smoothing: _not stated_
- final beam: 2.15" x 1.90"  
  > "where the beam size is 2.15$''$ by 1.90$''$" (3.1 1.3 mm Dust Continuum Image)
- final rms: 2.8e-2 mJy/beam  
  > "$\sigma_{\rm RMS} =$ 2.8$\times 10^{-2}$ mJy beam$^{-1}$" (3.1 1.3 mm Dust Continuum Image)

### Inherited from earlier work

- Spectro-spatial filtering of CO/CN assuming co-location with dust and Keplerian rotation  
  > "we employ the spectro-spatial filtering technique of (cite: matra2015; matra2017b) to boost the SNR" (3.4 Constraints on CO and CN Line Emission) [from (cite: matra2015; matra2017b)]
- NLTE excitation code for gas mass limits  
  > "using the non-local thermodynamic equilibrium (NLTE) excitation code of (cite: matra2015; matra2018a) in the optically thin assumption" (3.4 Constraints on CO and CN Line Emission) [from (cite: matra2015; matra2018a)]
- Bayesian stellar parameter inference  
  > "using the Bayesian approach applied in (cite: delBurgo&AllendePrieto2016; delBurgo&AllendePrieto2018)" (3.5 Stellar Parameters) [from (cite: delBurgo&AllendePrieto2016; delBurgo&AllendePrieto2018)]
- Mass loss rate equation for collisional cascade  
  > "(cite: matra2017b) derive a simple equation for the mass loss rate of these smallest grains assuming a steady-state collisional cascade model" (4.1 Collisional Cascade Status) [from (cite: matra2017b)]

### Not stated but needed to reproduce (our reading)

- Number of CLEAN iterations, threshold and mask, image size and cell size
- Archive project code linkage: paper prints 2018.1.00200.S, archive lists 2017.1.00200.S
- Line-free channels used for uvcontsub
- Prior ranges for the MCMC parameters
- Model grid, collider densities and frequency-weighting details for spectro-spatial filtering
- Distance adopted to convert arcsec to au
- SED fit priors and the modified blackbody lambda0 grid

## Analysis recipe

1. **Image the 1.3 mm continuum**: Average in frequency, concatenate three datasets, tclean with u-v taper and Briggs weighting  
  > "we first average the observations in frequency to reduce the data size, then concatenate all three observations." (2 ALMA Observations)
   - software: CASA
   - parameter: Gaussian u-v taper 2", Briggs 0.5  
  > "We apply a Gaussian u-v taper of 2$''$ and a Briggs weighting factor of 0.5" (2 ALMA Observations)
   - fitting: _not stated_
   - validation: Width resolved without taper  
  > "the width is clearly resolved when imaging with no u-v taper" (3.1 1.3 mm Dust Continuum Image)
2. **Fit the SED**: Star plus modified blackbody disk grids fitted to photometry and IRS spectrum  
  > "We fit grids of star and disk models to the data, using synthetic photometry of the models to fit photometry, and resampled model spectra to fit the IRS spectrum." (3.1 1.3 mm Dust Continuum Image)
   - software: MultiNest
   - fitting: MultiNest, stellar and disk parameters fit simultaneously  
  > "The best fitting model parameters are found with the `MultiNest` code (cite: Multinest), with both the stellar and disk parameters found simultaneously." (3.1 1.3 mm Dust Continuum Image)
   - validation: _not stated_
3. **Forward-model visibilities with Gaussian ring**: Axisymmetric vertically thin Gaussian ring, S_B ∝ f0/sqrt(r) exp(-(r-mu)^2/2sigma^2); GALARIO FT; per-dataset weight scaling  
  > "The `galario` (cite: GALARIO) package is utilized to Fourier transform the model image at the u-v locations of our ALMA data to calculate the ${\chi}^2$ of the model given the data." (3.2 Disk Modeling and Fitting)
   - software: galario, emcee
   - parameter: 1024 walkers, 1.25e4 steps, burn-in 2.5e3  
  > "We initialize an ensemble of 1024 walkers each sampling from the parameter space for 1.25$\times 10^{4}$ time steps with a burn-in strip size of 2.5$\times 10^{3}$." (3.2 Disk Modeling and Fitting)
   - assumption: Dust blackbody temperature T ∝ r^-1/2  
  > "The temperature dependence as a function of radius (assuming blackbody dust grains) is also factored into our surface brightness profile" (3.2 Disk Modeling and Fitting)
   - fitting: emcee affine-invariant sampler, likelihood ∝ exp(-chi2/2), linearly uniform priors on f0, sigma, mu, i, PA, dRA, dDec  
  > "We use a likelihood function proportional to $\exp(-\chi^2/2)$ and use linearly uniform priors on all our model parameters" (3.2 Disk Modeling and Fitting)
   - validation: Chains >=67 autocorrelation times; residuals consistent with noise; BIC favors symmetric over asymmetric-sigma model by 7.3  
  > "We find that all the chains are at least $\sim$67 times their integrated autocorrelation time, ensuring convergence." (3.2 Disk Modeling and Fitting); "we find a $\Delta BIC$ value of 7.3 favoring the symmetric density model" (3.3 Model Fitting Results)
4. **Limit CO and CN gas and ice fractions**: Spectro-spatial filtering of cubes, 3 sigma flux limits, NLTE masses, steady-state photodissociation balance to give ice mass fractions  
  > "we set an upper limit (3$\sigma$) of 35 and 47 mJy km/s on the integrated line flux of the CO and CN transitions, respectively." (3.4 Constraints on CO and CN Line Emission)
   - software: NLTE code of Matra et al.
   - parameter: Temperatures 10-250 K, full collider density range  
  > "We explore the full range of collider densities between the regime where excitation is dominated by collisions (LTE) and radiative absorption/emission, and temperatures between 10 and 250 K." (3.4 Constraints on CO and CN Line Emission)
   - assumption: Gas co-located with dust, Keplerian, optically thin; rock/ice ratio ~4  
  > "by assuming CO and CN are co-located with the dust and in Keplerian velocity" (3.4 Constraints on CO and CN Line Emission)
   - fitting: _not stated_
   - validation: _not stated_
5. **Infer stellar parameters**: Bayesian fit to PARSEC isochrones using Gaia absolute G, BP-RP and [Fe/H]  
  > "as well as \[Fe/H\] (assumed to be solar, 0.0 $\pm$ 0.20 dex), all three as input parameters using the Bayesian approach" (3.5 Stellar Parameters)
   - software: PARSEC
   - assumption: [Fe/H] solar, 0.0 +/- 0.20 dex  
  > "\[Fe/H\] (assumed to be solar, 0.0 $\pm$ 0.20 dex)" (3.5 Stellar Parameters)
   - fitting: _not stated_
   - validation: _not stated_
6. **Collisional cascade mass and R-L relation update**: Steady-state cascade mass loss and total mass vs largest body size; update R-L correlation and compute outlier significance  
  > "Assuming a planetesimal strength of 150 J/kg and a mean planetesimal eccentricity of 0.05" (4.1 Collisional Cascade Status)
   - assumption: Millimeter dust opacity 2.3 cm^2/g; size distribution n(D) ∝ D^-3.5  
  > "Assuming a millimeter dust opacity of $\kappa _{\nu} = 2.3\ \rm cm^2 g^{-1}$" (4.1 Collisional Cascade Status)
   - fitting: _not stated_
   - validation: Compared to MMSN-like disk mass  
  > "we compare it with the expectation from the Minimum Mass Solar Nebula" (4.1 Collisional Cascade Status)

## Software

- **CASA** 5.4.1: tclean imaging and uvcontsub  
  > "We then use the `tclean` task of `CASA` 5.4.1 (cite: CASA)" (2 ALMA Observations)
- **galario** : Fourier transform of model at data uv points  
  > "The `galario` (cite: GALARIO) package is utilized to Fourier transform the model image" (3.2 Disk Modeling and Fitting)
- **emcee** : MCMC posterior sampling  
  > "the posterior probability distributions of our model parameters are explored using the `emcee` (cite: foremanmackey13) package" (3.2 Disk Modeling and Fitting)
- **MultiNest** : SED fitting  
  > "The best fitting model parameters are found with the `MultiNest` code (cite: Multinest)" (3.1 1.3 mm Dust Continuum Image)
- **corner** : Corner plot  
  > "`corner` (cite: corner)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk radius at peak surface density | 193 | +2/-3 | au | 3 | R \[au\] / disk radius at peak surface density / 193 / (+2,-3) |
| Disk width (FWHM) | 71 | +/-4 | au | 3 | $\Delta$R \[au\] / width of disk / 71 / (+4,-4) |
| Inclination | 33 | +1/-2 | deg | 3 | $i$ \[$^{\circ}$\] / line-of-sight inclination / 33 / (+1,-2) |
| Position angle | 114 | +2/-3 | deg | 3 | $PA$ \[$^{\circ}$\] / position angle (east of north) / 114 / (+2,-3) |
| Disk flux density from visibility modeling | 6.2 | 0.2 (0.6 incl. absolute flux) | mJy | 3 | visibility modeling (6.2 $\pm$ 0.2 mJy |
| Fractional luminosity | 5.0e-4 | 0.1e-4 | dimensionless | 2 | $f = (5.0 \pm 0.1) \times 10^{-4}$ |
| mm spectral slope | 2.87 | 0.04 | dimensionless | 2 | $\alpha_{mm} = 2.87 \pm 0.04$ |
| CO ice mass fraction limit | <77 | not stated | % | 4 | upper limit to the CO and HCN exocometary mass fraction of $<77$% and $<3$%, respectively |
| HCN ice mass fraction limit | <3 | not stated | % | 4 | upper limit to the CO and HCN exocometary mass fraction of $<77$% and $<3$%, respectively |
| CO and CN line flux upper limits (3 sigma) | 35 and 47 | not stated | mJy km/s | 4 | we set an upper limit (3$\sigma$) of 35 and 47 mJy km/s on the integrated line flux of the CO and CN transitions |
| Stellar mass | 1.29 | +/-0.08 | Msun | 5 | Mass \[$\mbox{$\rm M_{\odot}$}$\] / 1.29 / (+0.08,-0.08) |
| Stellar age | 1.5 | +1.2/-0.7 | Gyr | 5 | Age \[Gyr\] / 1.5 / (+1.2,-0.7) |
| Total mass of collisional cascade | 299 | not stated | Earth masses | 6 | we in turn use to find a total mass of $M_{tot} = 299$ $\rm M_{\oplus}$ |
| Updated R-L normalization R_1Lsun | 74 | 7 | au | 6 | $R_{1L_{\odot} }=74 \pm 7$ au, $\alpha=0.16 \pm 0.05$ |

## Qualitative findings

- No significant asymmetry in the disk; centre consistent with star  
  > "The phase center offsets ($\Delta$$RA$ and $\Delta$$Dec$) are consistent with zero" (3.3 Model Fitting Results)

## Claim tuples

- H: Is the HD 170773 belt large and narrow compared with other mm-resolved belts? | E: Visibility forward-modeling with a Gaussian ring | R: R = 193 au, width 71 au, dR/R=0.37 | F: The disk is large and narrow | **supported**
- H: Does HD 170773 host detectable CO/CN gas? | E: Spectro-spatial filtering of line cubes | R: No detection; ice fractions <77% (CO), <3% (HCN) | F: Consistent with Solar System comets and other exocometary belts | **supported**
- H: Is HD 170773 an outlier of the R-L relation, linked to giant planets? | E: Updated the R-L fit and outlier significance | R: Outlier at 3.5 sigma, in a group of four, two with imaged planets | F: Possible connection between large belts and long-period giant planets (tentative) | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: u-v taper boosts SNR of the ring at the cost of resolution  
  > "The Gaussian u-v taper boosts the SNR of the ring at the cost of resolution." (2 ALMA Observations)
- Alternative: Asymmetric Gaussian (sigma_in, sigma_out) rejected via BIC  
  > "it did not describe the data significantly better than the symmetric density model" (3.3 Model Fitting Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Outlier conclusion sensitive to Gaussian intrinsic scatter assumption; large age uncertainty affects masses  
  > "we caution that this conclusion is sensitive to the intrinsic scatter of radii about the best-fit $R-L_{\star}$ model being modelled as a Gaussian" (4.2 Radius-Luminosity Relationship)
- Caveat (inferred, ours): Peak SNR only 14 with tapered image; ring profile assumed Gaussian
- Caveat (inferred, ours): Outlier significance and planet-correlation rest on small numbers (2 of 4)
- Caveat (inferred, ours): Mass estimates dominated by age and planetesimal strength assumptions
- Caveat (inferred, ours): Project code in text differs from archive-linked code

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Tclean mask, threshold, cell and image size
- Missing: Line-free channels and the filtering implementation for gas limits
- Missing: Priors' ranges and initialization for MCMC
- Missing: Distance value used
- Data volume (inferred): ~20-50 GB raw (three ACA/12m Band 6 executions)
- Score (inferred): 3/5, Uses standard public-style tools and states MCMC set-up, but imaging details and gas filtering code are missing.
- Rediscovery candidate: no, Data public status is not stated and the imaging recipe is incomplete, though results are numeric.

## Links

- Method: (cite: matra2015; matra2017b) (Spectro-spatial filtering for gas limits)
- Method: (cite: GALARIO) (Visibility modeling)
- Companion: (cite: matra2018b) (Radius-luminosity relation being updated)
- Companion: (cite: holland2017) (SONS survey, REASONS parent)
- Related: REASONS
- Related: SONS

## Checks

```json
{
 "quotes": 81,
 "quotes_ok": 81,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2018.1.00200.S"
 ],
 "obscore_codes_not_in_card": [
  "2017.1.00200.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 57,
  "rate": 0.663
 },
 "evidence_ok": true
}
```

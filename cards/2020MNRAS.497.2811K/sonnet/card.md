# Survey of planetesimal belts with ALMA: gas detected around the Sun-like star HD 129590

`2020MNRAS.497.2811K` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Kral, Quentin | arXiv: 2005.05841 | DOI: 10.1093/mnras/staa2038

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks, astrochemistry
- Question: Do debris discs around later-type stars host secondary CO/CN gas, and what are the dust and gas properties of 10 planetesimal-belt systems?  
  > "We looked for continuum emission of mm-dust as well as gas emission (CO and CN transitions)." (abstract)
- Target **HD 129590**: coordinates _not stated_; z/distance 136.0 pc  
  > "| HD 129590 | $5.8 \times 10^{-3}$ | 136.0 | G1V | 3.0 | 1.3 | 5810 | 0.98 |" (Table 1); distance from GAIA DR2 (Table 1 note)  
  > "| HD 129590 | $5.8 \times 10^{-3}$ | 136.0 | G1V | 3.0 | 1.3 | 5810 | 0.98 |" (Table 1)
- Target **HD 121191**: coordinates _not stated_; z/distance 132.1 pc  
  > "| HD 121191 | $2.4 \times 10^{-3}$ | 132.1 | A5V | 7.2 | 1.6 | 7690 | 1.9 |" (Table 1); distance from GAIA DR2 (Table 1 note)  
  > "| HD 121191 | $2.4 \times 10^{-3}$ | 132.1 | A5V | 7.2 | 1.6 | 7690 | 1.9 |" (Table 1)
- Target **HD 106906, HD 114082, HD 117214, HD 143675, HD 15745, HD 191089, HD 69830, HR 4796A**: coordinates _not stated_; z/distance 12.6-139.2 pc  
  > "References: From (cite: 2017MNRAS.469..521K) updated with GAIA DR2 distances (cite: 2016A&A...595A...1G; 2018A&A...616A...1G)" (Table 1); distance from GAIA DR2  
  > "References: From (cite: 2017MNRAS.469..521K) updated with GAIA DR2 distances (cite: 2016A&A...595A...1G; 2018A&A...616A...1G)" (Table 1)

## Data provenance

- ALMA projects: 2017.1.00704.S
- bands: Band 6  
  > "Our sample of 10 stars were targeted by ALMA in band 6" (2.2 ALMA observing configuration)
- frequencies and spectral setup: 4 SPWs: two continuum at 243.1 and 245.1 GHz (128 channels, 2 GHz each); CO 2-1 and CN 2-1 SPWs with 488.281 kHz channels, 3840 channels  
  > "two of which focused on observing the dust continuum with 128 channels centered at 243.1 and 245.1 GHz (bandwidth of 2 GHz each)." (2.2 ALMA observing configuration)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15-500 m, 43 antennas  
  > "The observations were carried out using 43 antennas with baselines ranging from 15 to 500 m." (2.2 ALMA observing configuration)
- angular resolution: ~1.5 arcsec  
  > "due to the limited resolution of our observations ($\sim 1.5$ arcsec)" (3.1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 7 April to 12 August 2018  
  > "between $7^{\rm th}$ April and $12^{\rm th}$ August 2018" (2.2 ALMA observing configuration)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (230.538 GHz)
- Line: CN N=2-1 (strongest hyperfine ~226.875 GHz) (~227 GHz)
- External data: Stellar parameters, fractional luminosities and SEDs for the sample  
  > "References: From (cite: 2017MNRAS.469..521K) updated with GAIA DR2 distances" (Table 1) [from (cite: 2017MNRAS.469..521K)]
- External data: JCMT 850 micron flux of HD 15745 (12±1.4 mJy)  
  > "Extrapolating the observed JCMT flux for HD 15745 at 850 $\mu$m ($12\pm1.4$ mJy) to 1.27 mm" (4.1.6 HD 15745) [from (cite: 2017MNRAS.470.3606H)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline  
  > "The pipeline provided by ALMA was used to apply calibrations and extract the calibrated visibilities." (2.2 ALMA observing configuration)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10%  
  > "flux calibration uncertainties (10%) added in quadrature" (2.3 Dust continuum observations)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We then used the CLEAN algorithm to image the data using natural weightings." (2.3 Dust continuum observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub in CASA, avoiding line channels  
  > "using the task `uvcontsub` in CASA), avoiding channels around the line frequencies" (2.4 Gas observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Gas MCMC radiative transfer method  
  > "was already used in (cite: 2018arXiv181108439K) to fit the \[CI\] fine structure line at 609.14$\mu$m in HD 131835" (3.2.2) [from (cite: 2018arXiv181108439K)]
- Temperature exponents fixed to 0, double power law profile  
  > "we fixed them to 0 (cite: 2016MNRAS.461..845K)" (3.2.2) [from (cite: 2016MNRAS.461..845K)]
- mu=14  
  > "To be consistent with previous studies, we assume $\mu=14$." (3.2.2) [from (cite: 2017MNRAS.469..521K; 2018arXiv181108439K)]

### Not stated but needed to reproduce (our reading)

- Line-free channels for continuum and uvcontsub
- CASA version and pipeline version
- Image size, cell size, clean threshold
- Flux, bandpass and phase calibrators
- MCMC priors ranges and burn-in length
- Velocity binning of cubes and masks used for fluxes
- Stellar models for non-LTE fluorescence and electron density grid

## Analysis recipe

1. **Image continuum and measure fluxes**: Combine four SPWs excluding CO line channels, CLEAN with natural weighting, integrate flux in ellipse where S/N >~2  
  > "we removed the channels close to the CO J=2-1 line and summed the four spectral windows to obtain a continuum image at $\sim$ 1.27mm" (2.3 Dust continuum observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **2-D Gaussian fit for resolution check**: imfit on continuum images  
  > "We use the CASA function `imfit` to find the best fit parameters of a 2-D Gaussian to our continuum images." (3.1.1)
   - software: CASA
   - fitting: _not stated_
   - validation: integrated fluxes checked against Table values  
  > "verified that all integrated fluxes are consistent with values listed in Table" (3.1.1)
3. **Fit dust ring geometry and mass**: Gaussian ring model, RADMC-3D images at 1.27 mm fit to dirty images with MCMC  
  > "We fit the dirty images (i.e. not cleaned) directly, which is closest to fitting the visibilities" (3.1.2)
   - software: RADMC-3D, emcee
   - parameter: 100 walkers, 1000 steps after burn-in  
  > "The MCMC simulations were run with 100 walkers and for 1000 steps after the burn-in period." (3.1.2)
   - assumption: size distribution index -3.5, max grain 1 cm, min = blowout size, astrosilicates 2.7 g/cm3, kappa~1.3 cm2/g  
  > "a mass-weighted mean opacity of $\kappa \sim 1.3$ cm$^2$g$^{-1}$ at 1.27 mm" (3.1.2)
   - fitting: emcee, uniform priors, likelihood exp(-chi2/2) over dirty-beam-convolved pixels  
  > "We assume uniform priors and the posterior distributions of our parameters are given by the product of the prior distribution function and the likelihood function" (3.1.2)
   - validation: HR 4796A compared to Kennedy et al. 2018 band 7 results  
  > "This is consistent with the results by (cite: 2018MNRAS.475.4924K), who did a similar analysis with ALMA data at higher resolution in band 7." (3.1.2)
4. **Extract CO/CN moment maps, spectra and fluxes**: uvcontsub cubes, moment-0 integrated over ±20 km/s refined per source, upper limits 3 sigma  
  > "integrated the cubes in velocity between $\pm20$km/s" (2.4 Gas observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
5. **Fit gas disc with LTE radiative transfer MCMC**: Gaussian ring gas model, RADMC-3D CO cubes vs dirty cubes, per channel  
  > "We then produce dirty cubes (i.e. without cleaning the images) around the CO line and use RADMC-3D to produce CO model cubes" (3.2.2)
   - software: RADMC-3D, emcee
   - parameter: 100 walkers, ~10,000 steps; 2.667 channels per resolution element  
  > "we run the simulations with 100 walkers and for $\sim$10,000 steps" (3.2.2)
   - assumption: LTE, mu=14, axisymmetric  
  > "we first assume that CO is in local thermal equilibrium (LTE)" (3.2.2)
   - fitting: free: R0, DeltaR, Sigma0, T0, v*, i, PA, offsets  
  > "The free parameters of this gas model are thus $R_0$, $\Delta R$, $\Sigma_0$, $T_0$, $v_\star$" (3.2.2)
   - validation: HD 121191 compared to Moor et al. 2017  
  > "We compare our results on the CO detection in HD 121191 to (cite: 2017ApJ...849..123M)." (3.2.2)
6. **Non-LTE CO and CN masses**: Optically thin non-LTE with fluorescence, scan over electron density and Tk 10-250 K, take min/max  
  > "To account for our lack of knowledge of the temperature and electron density in each system, we assume wide ranges for both and then give a mass range estimate computed as being the minimum and maximum values reached on these plots" (3.2.2 Fit with an MCMC radiative transfer model)
   - software: LAMDA database
   - assumption: collision rates from Dickinson & Richards 1975, Allison & Dalgarno 1971  
  > "The CO/electron collision rates where taken from (cite: 1975JPhB....8.2846D)" (3.2.2)
   - fitting: _not stated_
   - validation: _not stated_
7. **Derive planetesimal CO ice fraction and HCN/CO**: Steady-state gas vs dust production using Matra et al. 2017 Eq. 2 and 2018 Eq. 3  
  > "we assume that the production rate of gas and dust are at steady state and compare them to get the CO mass fraction" (4.5.1)
   - assumption: no shielding  
  > "assuming no shielding and where we derived the level populations" (4.5.2)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : imaging, uvcontsub, imfit  
  > "We use the CASA function `imfit`" (3.1.1)
- **RADMC-3D** : dust and CO model images/cubes  
  > "The RADMC-3D code (cite: 2012ascl.soft02015D) is then used to compute images" (3.1.2)
- **emcee** : MCMC fitting  
  > "we use the emcee module" (3.1.2)
- **PHOENIX** : stellar spectrum fit for HD 69830  
  > "we fit a PHOENIX stellar spectrum (cite: 2013A&A...553A...6H)" (4.4)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HD 129590 CO flux | 0.056 | 0.014 | Jy km/s | 4 | / HD 129590 / $1.61 \times 1.16$ / 81.9 / 1.52 / $0.056 \pm 0.014$ |
| HD 129590 CO mass (non-LTE) | 2.1e-5 - 1.3e-4 | range | M_earth | 6 | we find that (the optically thin) mass range is $2.1\times10^{-5}$ - $1.3\times10^{-4}$ M$_\oplus$ |
| HD 121191 CO flux | 0.21 | 0.02 | Jy km/s | 4 | $0.21 \pm 0.02$ |
| HD 121191 gas ring radius | 22 | +2/-3 | au | 5 | $R_0 = 22^{+2}_{-3}$ au |
| HD 121191 CO mass LTE | 2.3e-3 | +2.3/-0.9 e-3 | M_earth | 5 | $2.3^{+2.3}_{-0.9} \times 10^{-3}$ M$_\oplus$ |
| HD 129590 dust ring radius | 74.2 | +6.1/-5.9 | au | 3 | / HD 129590 / $74.2^{+6.1}_{-5.9}$ |
| HD 129590 dust mass | 0.39 | ±0.02 | M_earth | 3 | $0.39^{+0.02}_{-0.02}$ |
| HCN/CO outgassing ratio HD 129590 | <2.4 | upper limit | percent | 7 | $<2.4$% for HD 129590 and $<0.46$% for HD 121191 |
| HR 4796A CO ice fraction | <1.9 | upper limit | percent | 7 | HR 4796A ($<$1.9%) |

## Qualitative findings

- First CO detection around a G-type star; HD 121191 CO lies inside the planetesimal belt, possibly due to shielding and viscous spreading  
  > "we detect CO for the first time around the young 10-16 Myr old G1V star HD 129590" (abstract)

## Claim tuples

- H: Gas can be detected around Sun-like stars | E: Band 6 CO 2-1 survey of 10 debris discs | R: CO flux 0.056±0.014 Jy km/s, S/N~4-9 around HD 129590 | F: First CO around a G-type star, mass 2-10e-5 Mearth | **supported**
- H: CO in HD 121191 is colocated with the planetesimals | E: MCMC fit of CO cube | R: gas at ~22 au vs dust at ~52 au | F: CO closer in, consistent with shielding and spreading | **partially**
- H: Exocomets resemble Solar System comets in CO content | E: Upper limits on CO mass converted to ice fractions | R: HD 114082 <1.6%, HR 4796A <1.9% | F: some systems below Solar System comet range | **supported**

## Reasoning

- Why this data: Targets chosen as bright discs with late spectral types and highest predicted CO detectability  
  > "we prioritised systems with late spectral types (which have less detections so far) and bright debris discs" (2.1 Observed sample)
- Why this method: _not stated_
- Alternative: CO near HD 114082 attributed to a line-of-sight cloud rather than circumstellar gas  
  > "might be due to a cloud on the line of sight" (2.4 Gas observations)
- How they decided it was enough: _not stated_
- Limitation (authors): Dust masses have large systematic uncertainties from arbitrary composition; HD 129590 gas unconstrained by MCMC  
  > "it should be understood that it has large systematic uncertainties" (3.1.2)
- Caveat (inferred, ours): Low S/N (~4) CO detection for HD 129590
- Caveat (inferred, ours): Low resolution limits geometry
- Caveat (inferred, ours): Non-LTE masses depend on wide assumed density and temperature ranges
- Caveat (inferred, ours): Astrometric offsets possibly calibration artefacts

## Reproducibility

- Data public (paper): Data in ALMA archive  
  > "The data underlying this article are available in the ALMA archive: ADS/JAO.ALMA#2017.1.00704.S." (Data availability)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Calibration details
- Missing: MCMC priors and non-LTE grid ranges
- Missing: Custom MCMC wrapper code
- Data volume (inferred): ~100-300 GB raw for 10 targets
- Score (inferred): 5/5, Public data and clear model description, but many imaging and fitting settings are missing and the gas fits need weeks of CPU.
- Rediscovery candidate: yes, Public data, numeric results (fluxes, masses, radii); continuum and CO flux are redoable.

## Links

- Method: (cite: 2018arXiv181108439K) (gas MCMC method)
- Method: (cite: 2018ApJ...853..147M) (non-LTE and HCN/CO method)
- Companion: (cite: 2017MNRAS.469..521K) (CO detectability predictions and sample)
- Related: Lieman-Sifry et al. 2016 ALMA survey
- Related: Moor et al. 2017

## Checks

```json
{
 "quotes": 64,
 "quotes_ok": 64,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 1,
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
  "stated": 48,
  "rate": 0.545
 },
 "evidence_ok": true
}
```

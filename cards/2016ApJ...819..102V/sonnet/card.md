# Dust Masses of Disks around 8 Brown Dwarfs and Very Low-mass Stars in Upper Sco OB1 and Ophiuchus

`2016ApJ...819..102V` | The Astrophysical Journal 2016 | first author: van der Plas, G. | arXiv: 1602.01724 | DOI: 10.3847/0004-637X/819/2/102

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: What are the dust (and CO gas) masses of disks around brown dwarfs and very low-mass stars in Upper Sco, does the disk mass / stellar mass correlation extend to the BD regime, and how does mass-averaged dust temperature scale with luminosity?  
  > "suggesting that the stellar mass / disk mass correlation can be extrapolated for brown dwarfs with masses as low as 0.05 M$_\odot$ ." (abstract)
- Target **8 BD/VLMS disks (7 in Upper Sco, 2MASS J16214199 in Ophiuchus)**: coordinates 2MASS IDs only (e.g. J15555600-2045187)  
  > "The seven Upper Sco targets for this study have spectral types ranging from M5.5 to M7.5" (Target selection); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00743.S
- bands: Band 7 (885 um continuum, 12CO J=3-2)  
  > "ALMA Early Science Cycle 1 band 7 observations were conducted on 2014 Mar 20 and 2014 Apr 27" (Observations and Data Reduction)
- frequencies and spectral setup: 3 TDM windows at 331.8, 333.8, 343.8 GHz (128 channels, 1.875 GHz); 1 FDM window on CO 3-2, 488.281 kHz channels (0.42 km/s)  
  > "The three TDM spectral windows were centred at 331.8 GHz, 333.8 GHz, and 343.8 GHz." (Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: 34 and 35 antennas  
  > "| 2014 Mar 20 | 34 | 15.1 to 437.8 | 0.97 | Titan | J1517-2422 | J1626-2951 |" (Observations and Data Reduction)
- configurations: _not stated_
- baselines: 15.1 to 558.2 m  
  > "The array configuration provided baselines ranging between 15.1 and 558.2 meters." (Observations and Data Reduction)
- angular resolution: 0.56" x 0.44" at PA = -82 deg (natural weighting)  
  > "which results in a synthetic beam size of 0.56" $\times$ 0.44" at PA = -82 degrees" (Observations and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: 0.13 mJy/beam continuum; 9 mJy/beam per 0.423 km/s channel for CO  
  > "We reach a 1 $\sigma$ sensitivity of 0.13 mJy/beam for the continuum maps, and 9 mJy/beam per 0.423 km s$^{-1}$ channel for the CO line images." (Results)
- time on source: 2519 and 2588 s total execution; 4.55 min per source  
  > "with 2519 and 2588 seconds of total execution time respectively, translating to 4.55 minutes per source" (Observations and Data Reduction)
- observing dates: 2014 Mar 20 and 2014 Apr 27  
  > "ALMA Early Science Cycle 1 band 7 observations were conducted on 2014 Mar 20 and 2014 Apr 27" (Observations and Data Reduction)
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (not stated)
- Other facility **Herschel PACS / Spitzer**: Far-IR and mid-IR photometry used for target selection and SED fitting  
  > "Our sample was selected based on the results of the far-IR *Herschel* PACS survey of (cite: 2012ApJ...755...67H)" (Target selection)
- External data: Proper motions from PPMXL used to shift images  
  > "we shift our images using the proper motion correction from the PPMXL Catalog (cite: 2010AJ....139.2440R)" (Observations and Data Reduction) [from Roeser et al. 2010 (cite: 2010AJ....139.2440R)]
- External data: Stellar parameters (R*, M*, T*) from evolutionary models for 1 and 10 Myr objects used in temperature grid  
  > "use stellar parameters ($R_{*}$, $M_{*}$ and $T_{*}$) from the (cite: 2015A&A...577A..42B) models for objects of 1 and 10 Myr" (Discussion) [from Baraffe et al. 2015 (cite: 2015A&A...577A..42B)]

## Processing

### Calibration

- pipeline or manual: standard CASA reduction tools  
  > "We used the standard reduction tools within the *Common Astronomy Software Applications* package (cite: 2007ASPC..376..127M) to calibrate and combine the data." (Observations and Data Reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (both executions)  
  > "| 2014 Mar 20 | 34 | 15.1 to 437.8 | 0.97 | Titan | J1517-2422 | J1626-2951 |" (Table 2)
- flux scale uncertainty: ~15%  
  > "We estimate the absolute flux calibration, based on the scatter of flux values of the calibrators in the different executions, to be accurate within $\sim$15%." (Observations and Data Reduction)
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN (Högbom)  
  > "we image the disks with the CLEAN task in CASA (cite: 1974AAS...15..417H) using natural weighting" (Observations and Data Reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "using natural weighting due to the faintness of our targets" (Observations and Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: For CO detections, channels within 0.1 GHz of line center excluded from continuum; otherwise line window included  
  > "For the two sources with CO emission detected, we exclude those channels within 0.1 GHz of the CO line center." (Results)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.56" x 0.44", PA -82 deg  
  > "synthetic beam size of 0.56" $\times$ 0.44" at PA = -82 degrees" (Observations and Data Reduction)
- final rms: 0.13 mJy/beam continuum  
  > "We reach a 1 $\sigma$ sensitivity of 0.13 mJy/beam for the continuum maps" (Results)

### Inherited from earlier work

- SED-fitting approach with MCFOST grids  
  > "The approach used here is similar to the one we previously used (cite: 2008A&A...486..877B; 2012ApJ...744L...1H; 2012ApJ...755...67H; 2013A&A...559A.126A)." (Radiative transfer models) [from Bouy 2008; Harvey 2012a,b; Alves de Oliveira 2013]
- Analytic dust mass opacity and temperature scaling  
  > "Following them, we calculate the dust masses for our targets in a similar way using the same opacity as used by (cite: andrews2013)" (6.1) [from Andrews et al. 2013; Carpenter et al. 2014]
- CO gas mass lower-limit prescription  
  > "by following the prescription from (cite: 2015arXiv150904589R) and references therein" (6.3) [from Rodriguez et al. 2015]

### Not stated but needed to reproduce (our reading)

- Distances to targets used for dust masses
- CASA version
- Clean threshold, mask, image size and cell size
- uvmodelfit starting model and fitting details
- Stellar luminosities derivation
- MCFOST version and wavelength grid/photometry used in SED
- Rest frequency of CO line and velocity reference

## Analysis recipe

1. **Calibrate and image**: CASA calibration, natural-weighted CLEAN, proper-motion shifts  
  > "We used the standard reduction tools within the *Common Astronomy Software Applications* package (cite: 2007ASPC..376..127M) to calibrate and combine the data." (Observations and Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure continuum flux densities**: uv-plane point-source fit  
  > "We extract the fluxes using the CASA task *uvmodelfit*" (Observations and Data Reduction)
   - software: CASA uvmodelfit
   - fitting: _not stated_
   - validation: _not stated_
3. **Extract CO line fluxes**: elliptical aperture spectra, integrated over velocities where >3 sigma; upper limits from common ellipse and 14 km/s width  
  > "For all other disks we define a 1$\sigma$ upper limit to the CO line by using an extraction ellipse that encompasses the CO emission of both 2MASS J15555600 and 2MASS J16214199 and a linewidth of 14 km s$^{-1}$." (4.2)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
4. **SED fitting with MCFOST grid for dust masses**: Grid of parametric disk models fit to SEDs; chi^2, Bayesian probability exp(-chi2/2) with flat priors, marginalised  
  > "For each model we estimated the Bayesian probability via exp(-$\chi ^2$/2), assuming flat priors." (Radiative transfer models)
   - software: MCFOST
   - parameter: Disk mass 1e-4 to 1e-7 Msun in 7 log steps; Rout 100 au; Av 0-7; T* 2800-3200 K; R* 0.2-2 Rsun  
  > "we allow extinction values $A_v$ between 0 and 7 with steps of 0.5." (Radiative transfer models)
   - assumption: Astronomical silicates, amin 0.05 um, amax 1 mm, dn/da ~ a^-3.5, kappa 3.72 cm2/g at 885 um  
  > "The continuum opacity of this grain population is 3.72cm$^2$/g at $\lambda=885 \mu$m." (Radiative transfer models)
   - fitting: chi^2 with uncertainties set to max of observed error and 10% of flux; model uncertainties neglected  
  > "Uncertainties were set to the maximum between the observed value and 10% of the measured flux" (Radiative transfer models)
   - validation: Masses agree with Harvey et al. 2012 within a factor of 3  
  > "The disk masses we derive here are in agreement with those from our previous study (cite: 2012ApJ...755...67H) within a factor of 3, often better." (Radiative transfer models)
5. **Compare with analytic dust masses**: Optically thin isothermal formula with Andrews et al. T-L scaling  
  > "We call these dust masses the "analytical masses"." (6.1)
   - assumption: kappa885 = 2.7 cm2/g, beta = 0.4, T=25 (L/Lsun)^0.25  
  > "$\kappa_{885} = 2.7 g^{-1} cm^{2}$ at 885 $\mu$m" (6.1)
   - fitting: _not stated_
   - validation: _not stated_
6. **Derive T_dust-L relation**: MCFOST grid with fixed parameters, varying Rout and age; power-law fit of mass-averaged T vs L  
  > "We fit a power law to the correlation between luminosity and mass-averaged disk dust temperature for the models with an outer radius of 100 au" (6.1)
   - software: MCFOST
   - parameter: H0=10 au, beta=1.125, i=45 deg, Rin=0.1 au, p=-0.5, Mdisk=1% of stellar mass, Rout 10-200 au  
  > "We vary the disk outer radius R$_{out}$ between 10 and 200 au" (6.1)
   - fitting: power-law fit  
  > "We fit a power law to the correlation between luminosity and mass-averaged disk dust temperature for the models with an outer radius of 100 au and obtain a best fit represented by" (Discussion, Comparison of dust masses from radiative transfer models and analytical prescriptions)
   - validation: _not stated_
7. **Lower limit CO gas mass**: Prescription of Rodriguez et al. 2015 with CO:H 1e-4, tau=1, T 7.5-26.6 K  
  > "adopting a CO:H ratio of 10$^{-4}$, a line optical depth of $\tau$ = 1 and a temperature range of 7.5 - 26.6 K" (6.3)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration, imaging (CLEAN), uvmodelfit flux extraction  
  > "We extract the fluxes using the CASA task *uvmodelfit*" (Observations and Data Reduction)
- **MCFOST** : Radiative transfer SED modelling and temperature grid  
  > "We have modeled the detected disks with the radiative transfer code MCFOST" (Radiative transfer models)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 885 um flux 2MASS J15555600 | 0.68 | 0.13 | mJy | 2 | / J15555600-2045187 / usd155556 / M6.5 / -17.9 / -24.9 / 0.07 / 0.68 $\pm$ 0.13 / 0.275 $\pm$ 0.025 / |
| 885 um flux 2MASS J16214199 | 3.68 | 0.13 | mJy | 2 | / J16214199-2313432 / Allers 8 / M3 / -11.2 / -29.8 / 0.34 / 3.68 $\pm$ 0.13 / 0.350 $\pm$ 0.036 / |
| Mass-averaged dust temperature relation | <T_dust> ≈ 22 (L*/Lsun)^0.16 K | not stated | K | 6 | obtain a best fit represented by $\langle T_{dust} \rangle \approx 22 (L_{*} /L_{\odot})^{0.16} K$ |
| Model dust mass 2MASS J15555600 | 0.33 | not stated | Earth masses | 4 | / 2MASS J15555600 / 0.0075 / 1.20 (0.88) / 0.54 (0.39) / 0.13 (0.09) / 0.33 / |
| CO gas mass lower limit | 0.07 - 0.43 | not stated | Earth masses | 7 | We estimate a lower limit to the emitting gas mass of 0.07 - 0.43 M$_\oplus$ |
| CO 3-2 flux 2MASS J15555600 | 0.275 | 0.025 | Jy km/s | 3 | the line fluxes increase to 275 $\pm$ 25 mJy km s$^{-1}$ and 350 $\pm$ 36 mJy km s$^{-1}$, respectively |

## Qualitative findings

- Continuum emission is unresolved, limiting disks to within ~40 au radius  
  > "All continuum emission is spatially unresolved, limiting the detected disk emission to be within a radius of $\approx$ 40 au." (4.1)

## Claim tuples

- H: The disk mass–stellar mass correlation extends to BD masses | E: MCFOST SED fitting of ALMA 885 um + IR data | R: Dust masses 0.1–1 Earth masses | F: Correlation can be extrapolated to ~0.05 Msun | **supported**
- H: The Andrews et al. T-L scaling holds for BD disks | E: MCFOST grid of mass-averaged temperatures | R: Shallower relation, <T> ≈ 22 L^0.16 K, warmer disks; analytic masses 3.5x larger than model masses | F: Relation must be revised for late-M objects | **supported**
- H: Gas disks fade faster than dust | E: 12CO 3-2 detection statistics | R: CO detected in 1 of 7 Upper Sco disks | F: Gas-phase CO likely decreased/disappeared; the CO disk has warmest inner disk by H-[4.5] | **partially**

## Reasoning

- Why this data: Sample of Herschel-detected BD/VLMS in Upper Sco to extend to sub-mm  
  > "our sample includes 7 of the 8 targets that were detected in both PACS channels at 70 $\mu$m and 160 $\mu$m" (Target selection)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Sample biased toward far-IR bright, larger-mass disks; SED fitting insensitive to geometry; opacity uncertainties affect masses  
  > "our sample is by construction significantly biased towards far-IR bright sources, and therefore also biased towards sources with larger disk masses" (6)
- Caveat (inferred, ours): Dust masses depend on fixed opacity and unresolved outer radius
- Caveat (inferred, ours): Distances not stated
- Caveat (inferred, ours): Marginal detection of 2MASS J16024575
- Caveat (inferred, ours): Dust temperature fit rests on a sparse model grid

## Reproducibility

- Data public (paper): ALMA programme 2012.1.00743.S cited  
  > "This paper makes use of data from ALMA programme 2012.1.00743.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Full SED photometry table
- Missing: MCFOST setup files
- Missing: CASA scripts
- Data volume (inferred): ~10-20 GB raw
- Score (inferred): 5/5, Public data and clear model grid, but imaging parameters, photometry and distances missing.
- Rediscovery candidate: no, Fluxes reproducible but SED modelling needs unstated inputs.

## Links

- Method: Andrews et al. 2013 (cite: andrews2013) (Dust mass and temperature scaling)
- Method: Pinte et al. 2006 (cite: 2006A&A...459..797P) (MCFOST code)
- Companion: Harvey et al. 2012 (cite: 2012ApJ...755...67H) (Herschel survey and sample)
- Related: Herschel PACS survey of BD/VLMS
- Related: Ward-Duong et al. in prep (Taurus continuum)

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
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
  "facts": 78,
  "stated": 44,
  "rate": 0.564
 },
 "evidence_ok": true
}
```

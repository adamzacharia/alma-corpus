# ALMA Band 3 polarimetric follow-up of a complete sample of faint PACO sources

`2019MNRAS.489..470G` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Galluzzi, V. | arXiv: 1907.00299 | DOI: 10.1093/mnras/stz1930

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars
- Question: What are the total intensity and linear polarization properties at 97.5 GHz of a complete sample of 32 faint PACO radio sources, and how do they extend the spectra, polarization fractions, RMs and polarized source counts to mm wavelengths?  
  > "In this paper, we extend the frequency coverage in total and polarized intensity of a complete sub-sample of 32 sources, drawn from the (cite: Galluzzi2018) sample, by means of high sensitivity observations with the Atacama Large Millimeter/submillimiter Array (ALMA) at $97.5\,$GHz (Band 3)." (1 Introduction)
- Target **Complete sample of 32 faint PACO (AT20G) sources at b<-75 deg**: coordinates RA/Dec per source in the catalogue table; three ~10 deg regions at b<-75 deg  
  > "We observed a complete sample of $32$ objects drawn from the faint PACO sample ($S_{20\,GHz}> 200\,$mJy) in three circular regions at $b<-75^\circ$" (2 ALMA Observations); z/distance redshifts available for only some sources (e.g. 0.13 to 2.00 in the RM table)  
  > "We observed a complete sample of $32$ objects drawn from the faint PACO sample ($S_{20\,GHz}> 200\,$mJy) in three circular regions at $b<-75^\circ$" (2 ALMA Observations); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.01522.S
- bands: Band 3 (97.5 GHz)  
  > "polarimetric observations at $97.5\,$GHz (Band 3)" (abstract)
- frequencies and spectral setup: four 2 GHz-wide bands centred at 90.5, 92.5, 102.5, 104.5 GHz  
  > "in four $2\,$GHz-wide spectral bands centered at $90.5\,$, $92.5$, $102.5$ and $104.5\,$GHz, respectively" (2 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: 39 antennas, compact configuration (C40-6)  
  > "using $39$ antennas in a compact configuration (baseline range $118 - 1318\,$m" (2 ALMA Observations)
- configurations: _not stated_
- baselines: 118-1318 m  
  > "baseline range $118 - 1318\,$m, corresponding to resolutions of $4.8-0.3\,$arcsec at 97.5 GHz" (2 ALMA Observations)
- angular resolution: ~0.2-0.3 arcsec  
  > "Our ALMA observations achieved a resolution of $\simeq 0.2\,$arcsec" (2 ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: 20-40 uJy per SG; median polarization sensitivity ~0.4 mJy including calibration error  
  > "The median sensitivity in polarization for our ALMA observations (including the calibration error), is $\simeq 0.4\,$mJy." (4 Data analysis)
- time on source: 5.04 min (SG1), 11.69 min (SG2, SG3)  
  > "| 1 | C40-6 | $0.4-4.8$ | 5.04 | 40 | |" (Table 2)
- observing dates: 24 Aug, 22 and 27 Sep 2016  
  > "on 24th August, 22th and 27th September $2016$" (2 ALMA Observations)
- pi or archival as stated: Cycle 3, PI Galluzzi  
  > "(Cycle 3, Project ID: 2015.1.01522.S, PI: Galluzzi)" (2 ALMA Observations)
- Other facility **ATCA**: New 2.1-35/38 GHz total intensity and polarization data (2014 and 2016 campaigns)  
  > "We complement these observations with new Australia Telescope Compact Array (ATCA) data between $2.1$ and $35\,$GHz" (abstract)
- Other facility **GLEAM**: 70-230 MHz total intensity detections  
  > "Adding the co-eval GaLactic and Extragalactic All-sky Murchison widefield array (GLEAM) survey detections between $70\,$ and $230\,$MHz" (abstract)
- External data: ATCA 5.5-38 GHz and 2 GHz polarimetric data of the 104-source sample  
  > "combining observations from $2\,$GHz (cite: Galluzzi2018), through the $5.5-38\,$GHz range (cite: Galluzzi2017; Galluzzi2018)" (4 Data analysis) [from (cite: Galluzzi2017; Galluzzi2018)]
- External data: GLEAM flux densities  
  > "in total intensity we include GLEAM (cite: HurleyWalker2017), the Sydney University Molonglo Sky Survey (cite: Mauch2003) and PACO (cite: Massardi2016) flux densities." (4.1 Spectral behaviour) [from (cite: HurleyWalker2017); (cite: Mauch2003); (cite: Massardi2016)]
- External data: C2Ex total intensity source count model  
  > "We started from the C2Ex model for total intensity source counts, $n(S)$, by (cite: Tucci2011)" (5 Source Counts) [from (cite: Tucci2011)]

## Processing

### Calibration

- pipeline or manual: CASA standard calibration scheme (Nagai2016 and CASA Guide), two steps: parallel hands, then cross hands and gain refinement  
  > "following the current standard calibration scheme reported in (cite: Nagai2016) and the CASA Guide" (3 Data reduction)
- casa version: CASA 4.7.0  
  > "Common Astronomical Software Applications (CASA) version 4.7.0" (3 Data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Pictor A core (J0519-4546), stable within ~2%  
  > "the primary calibrator, namely the core of Pictor A (AT20GJ051949-454643), is found to be stable within $\sim 2\%$" (3 Data reduction)
- flux scale uncertainty: 7% for I; 10% for Q and U plus 2 deg on angle  
  > "Indeed we assumed a lower error for $I$ (i.e. $7\%$)" (3 Data reduction)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "obtained with a natural weighting" (3 Data reduction)
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
- final beam: ~0.3 arcsec FWHM  
  > "whose widths are of the order of the FWHM of the synthesized beam, i.e. $0.3\,$arcsec" (3 Data reduction)
- final rms: _not stated_

### Inherited from earlier work

- Error budget (calibration errors added in quadrature to statistical)  
  > "The errors in total intensity, linear polarization flux density and position angle were computed as in (cite: Galluzzi2017)" (3 Data reduction) [from (cite: Galluzzi2017)]
- RM fitting with IDL linfit, reduced chi2<2 and probability>0.1  
  > "Following (cite: Galluzzi2018) we used the IDL “linfit” procedure, accepting only fits with a reduced $\chi^2<2$ and with a probability level $>
0.1$." (4.3 Rotation measures) [from (cite: Galluzzi2018)]
- Spectral component classification (1C, 2-3C, >3C)  
  > "We again apply the same classification in terms of synchrotron components in order to distinguish between sub-populations." (4.2 Linear polarization fraction) [from (cite: Galluzzi2018)]
- Source-frame RM correction for redshift, Galaxy and ionosphere  
  > "correcting for the effect of redshift and for the relatively small contributions of our own Galaxy and of Earth’s ionosphere, as detailed by (cite: Galluzzi2018)" (4.3 Rotation measures) [from (cite: Galluzzi2018)]

### Not stated but needed to reproduce (our reading)

- Number/size of Stokes images and cell size
- Whether tclean/clean parameters, niter, thresholds, masks were used
- Exact way polarization leakage and angle calibration were solved (CASA tasks)
- Spectral windows combined for the Gaussian fits and per-sub-band fitting procedure
- How redshifts were assigned and the Galactic RM values used
- Total intensity source count error computation details and C2Ex model implementation
- Per-source flux density extraction when fit fails (peak definition)

## Analysis recipe

1. **Extract Stokes I, Q, U flux densities**: 2D Gaussian fit of naturally weighted maps; central peak if Q/U fit fails  
  > "Whenever the fit fails because the source is too faint to be detected in Stokes $Q$ and $U$, we consider the central peak in the image." (3 Data reduction)
   - software: CASA
   - assumption: Sources point-like; no Stokes V debiasing  
  > "Since almost all the objects are point-like" (3 Data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive P, polarization angle and fraction**: P = sqrt(Q^2+U^2), Pi = 100 P/I, 3 sigma detection limit  
  > "the linearly polarized emission, $P$, can be safely estimated from the Stokes parameters $Q$ and $U$ only" (3 Data reduction)
   - assumption: Debiasing term lowers P by ~0.01%, negligible  
  > "the debiasing term $\sigma_V$ lowers the estimated value of the polarized flux density by $\sim 0.01\%$" (3 Data reduction)
   - fitting: _not stated_
   - validation: _not stated_
3. **Polarization fraction distribution**: Bootstrap with 1000 resamplings, Gaussian per detection, uniform for upper limits, log-normal fit  
  > "Then, we generated $1000$ simulated data sets by resampling with repetitions the distributions of percentage polarization fractions of each source." (4.2 Linear polarization fraction)
   - fitting: log-normal with A=0.86, mu=2.05, sigma=0.97  
  > "with $A=0.86$, $\mu=2.05$ and $\sigma=0.97$." (4.2 Linear polarization fraction)
   - validation: _not stated_
4. **Rotation measures at 90-105 GHz**: Linear fit of angle vs lambda^2 using up to 8 sub-bands  
  > "In the case of a foreground screen of magnetized plasma the polarization angle varies as $\Delta \phi = RM\lambda^2$." (4.3 Rotation measures)
   - software: IDL linfit
   - assumption: Foreground Faraday screen  
  > "In the case of a foreground screen of magnetized plasma" (4.3 Rotation measures)
   - fitting: linfit, reduced chi2<2, probability>0.1  
  > "accepting only fits with a reduced $\chi^2<2$ and with a probability level $>
0.1$" (4.3 Rotation measures)
   - validation: _not stated_
5. **Polarized source counts at 95 GHz**: Convolve C2Ex total intensity counts with log-normal polarization fraction distribution  
  > "We started from the C2Ex model for total intensity source counts, $n(S)$, by (cite: Tucci2011) and used the approach of (cite: Tucci2012)" (5 Source Counts)
   - assumption: Same distribution applied to all sub-populations  
  > "the distribution of eq. ([\[eq:lognorm\]](#eq:lognorm)) was applied to all sub-populations" (5 Source Counts)
   - fitting: _not stated_
   - validation: Compared with Tucci2012 and D05-based predictions  
  > "there is a very remarkable agreement between our current data and the model predictions by (cite: Tucci2012)" (5 Source Counts)

## Software

- **CASA** 4.7.0: calibration and imaging of ALMA data  
  > "Common Astronomical Software Applications (CASA) version 4.7.0" (3 Data reduction)
- **IDL linfit** : linear fits for rotation measures  
  > "we used the IDL “linfit” procedure" (4.3 Rotation measures)
- **MIRIAD** : ATCA data reduction  
  > "During the data reduction with MIRIAD (the standard radio interferometry package for ATCA)" (6.1 Calibrator candidates for CPR studies)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Polarization detection rate at 3 sigma | 97 | not stated | percent | 2 | 3\,\sigma$ detection rate of $97\%$ (only one non-detection) |
| Median polarization fraction at 97.5 GHz | 2.2 | 0.6 | percent | 3 | The median polarization fraction measured by ALMA for the full sample is $2.2\pm 0.6\%$ |
| Median total intensity spectral index 36.5-97.5 GHz | -0.19 | not stated | dimensionless | 0 | the median spectral index in total intensity between $36.5$ and $97.5\,$GHz is $\alpha_{36.5}^{97.5}\simeq -0.19$ |
| Median ALMA flux excess over ATCA extrapolation (26 of 32 sources) | ~46 | not stated | percent | 0 | The median excess is of $\sim 46\%$ (with a maximum of $\simeq 98\%)$. |
| Median RM at the source (7 sources with z) | 6.4e4 | not stated | rad m^-2 | 4 | / All sample ($7$) / 2-3C ($5$) / $>$3C ($2$) /
/ $6.4\times 10^4$ / $5.7\times 10^4$ / $1.4\times 10^5$ / |
| Log-normal parameters of polarization fraction distribution | A=0.86, mu=2.05, sigma=0.97 | not stated | dimensionless | 3 | with $A=0.86$, $\mu=2.05$ and $\sigma=0.97$. |

## Qualitative findings

- Spectra are smooth with no sign of dust emission or high-frequency breaks; multiple emitting components indicated  
  > "The spectra of our sources are smooth over the whole frequency range, with no sign of dust emission from the host galaxy at mm wavelengths" (abstract)

## Claim tuples

- H: Does the polarization fraction change with frequency up to 97.5 GHz? | E: Median polarization fractions of ALMA sample compared with ATCA values of the 104-source sample, by component class | R: Median 2.2% vs 2.09% at 38 GHz | F: No statistically significant trend with frequency or flux density | **supported**
- H: Do the spectra show an additional component at mm wavelengths? | E: Compare ALMA flux with ATCA extrapolation | R: 26 of 32 sources show excess | F: Suggests another emission component emerging at mm wavelengths | **partially**
- H: What are the RMs at ~100 GHz? | E: Fit angle vs lambda^2 | R: Median intrinsic RM ~6.4e4 rad/m^2 | F: Dense magnetized screens may depolarize mm emission; small sample | **partially**
- H: Do polarized source counts at 95 GHz match models? | E: Convolve C2Ex counts with measured polarization fraction distribution | R: Counts down to ~1 mJy | F: Remarkable agreement with Tucci2012 predictions | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA and ATCA not simultaneous so no joint fit; small sample prevents firm conclusions  
  > "Therefore we have not attempted a joint fit of ALMA and ATCA data" (4.1 Spectral behaviour)
- Limitation (authors): Stokes V unreliable in Cycle 3  
  > "Stokes V images obtained were not reliable" (3 Data reduction)
- Caveat (inferred, ours): Non-simultaneity with ATCA makes excess interpretation vulnerable to variability
- Caveat (inferred, ours): RM errors very large; many consistent with zero
- Caveat (inferred, ours): Polarization fractions assume P without debiasing
- Caveat (inferred, ours): Classification relies on 2014 data

## Reproducibility

- Data public (paper): Project code given in acknowledgments; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.01522.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Leakage/angle calibration details
- Missing: Galactic RM and redshift sources
- Missing: ATCA data tables from earlier papers
- Data volume (inferred): ~50-100 GB raw
- Score (inferred): 3/5, Catalogue table gives results and calibrators, but imaging and calibration details are sparse and ATCA data come from earlier papers.
- Rediscovery candidate: no, Recipe is too sparse on imaging/calibration and relies on external ATCA data, though the ALMA flux table could be rechecked.

## Links

- Method: (cite: Nagai2016) (ALMA polarization calibration scheme)
- Method: (cite: Tucci2012) (polarized source count method)
- Companion: (cite: Galluzzi2017) (ATCA 5.5-38 GHz data)
- Companion: (cite: Galluzzi2018) (ATCA polarimetry 2-38 GHz of 104 sources)
- Companion: (cite: Puglisi2018) (used this paper's polarization fractions for CMB forecasts)
- Related: PACO
- Related: AT20G
- Related: GLEAM

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 1,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 46,
  "rate": 0.597
 },
 "evidence_ok": true
}
```

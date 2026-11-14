# Submillimeter polarization and variability of quasar PKS 1830-211

`2019A&A...621A..18M` | Astronomy and Astrophysics 2019 | first author: Marti-Vidal, I. | arXiv: 1810.11012 | DOI: 10.1051/0004-6361/201834036

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: agn_and_quasars
- Question: What are the submm polarization, rotation measure and short-term variability of the lensed quasar PKS 1830-211, using differential polarimetry on dual-polarization ALMA data?  
  > "we use the flux-density ratios between lensed images to analyze the short-term (intra-hour) source variability, and we use the $\psi$ dependence on $R_{pol}$ to analyze the source polarization." (Introduction)
- Target **PKS 1830-211**: coordinates _not stated_; z/distance z = 2.5 (lensed quasar); lens galaxy z = 0.89  
  > "PKS 1830$-$211 is a gravitationally lensed quasar at a redshift of $z=2.5$ ((cite: lid99))." (Introduction); distance from (cite: lid99)  
  > "PKS 1830$-$211 is a gravitationally lensed quasar at a redshift of $z=2.5$ ((cite: lid99))." (Introduction)

## Data provenance

- ALMA projects: _none stated_
- bands: Bands 7, 8 and 9  
  > "we use complementary observations at Bands 7 and 8 (at frequencies between 300 and 500 GHz) to constrain the Faraday rotation." (Introduction)
- frequencies and spectral setup: Spectral windows 1.875 GHz wide, channel spacing 0.977 or 1.953 MHz; centre frequencies in Table (e.g. B9 647.7-653.6 GHz)  
  > "The correlator was set up with spectral windows 1.875 GHz wide, and channel spacings of 0.977 MHz or 1.953 MHz." (2 Observations and data analysis)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: about one hour on target in Band 9  
  > "spanning about one hour on the target and covering a wide range of parallactic angles" (Introduction)
- observing dates: 2015 May 14, May 19, May 20, June 6  
  > "2015 May 19 | 07:10:30.7 – 08:17:17.0 | 230 – 100 | B9" (Table 1)
- pi or archival as stated: Observations from different projects targeting molecular species in the z=0.89 lens galaxy; reused  
  > "in the frame of different projects aiming at detecting various molecular species in the $z=0.89$ galaxy" (2 Observations and data analysis)
- Other facility **Fermi-LAT**: gamma-ray flares mentioned as context only  
  > "with several flaring events reported in recent years by the Fermi-LAT collaboration" (Introduction)
- External data: Earlier rotation measures (1-2)x10^7 rad m^-2 and Rpol epochs 2012-2014 for comparison  
  > "(cite: IMV2015) derived even higher $RM \sim (1-2) \times 10^7$ rad m$^{-2}$" (Introduction) [from (cite: IMV2015)]

## Processing

### Calibration

- pipeline or manual: CASA, standard procedure  
  > "The data were calibrated within the CASA[^2] package, following a standard procedure." (2 Observations and data analysis)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan or Ceres, Butler-JPL-Horizons 2012 model; bandpass J1924-292  
  > "The absolute flux calibration was scaled from Titan or Ceres, using the Butler-JPL-Horizons 2012 model." (2 Observations and data analysis)
- flux scale uncertainty: 10-20% absolute accuracy in Bands 7-9  
  > "within the ALMA expectations of 10–20% for absolute flux accuracy in Bands 7–9" (2 Observations and data analysis)
- self calibration: Phases 6 s integration-based; amplitudes scan-based (~3-5 min); common gains for both polarizers  
  > "integration-based (6 s) for the phases and scan-based ($\sim 3-5$ min) for the amplitudes." (2 Observations and data analysis)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: channels with molecular absorption flagged; remaining channels used for continuum  
  > "the channels with molecular absorption lines were flagged and the remaining channels were used to build the continuum." (2 Observations and data analysis)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Differential polarimetry method using Rpol and RM model  
  > "(cite: IMV2015) noted that it is possible to recover some source polarization information, even from standard dual-polarization observations" (Introduction) [from (cite: IMV2015)]
- Rpol multi-frequency model with RM  
  > "The $R_{pol}$ model for the multi-frequency data is given by (cite: IMV2015)" (4.1 Polarimetry and submm Faraday rotation) [from (cite: IMV2015)]

### Not stated but needed to reproduce (our reading)

- Which channels contain absorption lines and were flagged
- Fitting method, priors and error treatment for Rpol and RM
- Exact time bin lengths
- CASA version
- Initial model/geometry for two-point-source fit (positions)
- Project code to dataset mapping
- Whether self-cal model and image parameters used

## Analysis recipe

1. **Calibrate and self-calibrate**: Standard CASA calibration, bandpass J1924-292, flux Titan/Ceres, self-cal on target continuum  
  > "The data were calibrated within the CASA[^2] package, following a standard procedure." (2 Observations and data analysis)
   - software: CASA
   - fitting: _not stated_
   - validation: J1924-292 flux cross-checked with ALMA calibrator database, ~10% consistency  
  > "the consistency was on the order of 10%" (2 Observations and data analysis)
2. **Measure flux densities of NE and SW images per polarization and time bin**: Fit two point sources to visibilities in XX, YY, I in short time bins of a few minutes  
  > "by fitting a model of two point sources to the interferometric visibilities." (2 Observations and data analysis)
   - software: UVMULTIFIT
   - fitting: _not stated_
   - validation: Consistency across bands and epochs; images checked  
  > "The fact that we obtain the same qualitative behavior from data taken with two independent receiver bands and within a few hours indicates that our technique is robust." (3.2 Band 7 and 8 data)
3. **Fit Rpol versus parallactic angle in Band 9**: Fit Rpol = p_d cos[2(psi+beta+phi0)]  
  > "R_{pol} = p_d \cos{\left[2(\psi + \beta + \phi_0)\right]}" (4.1 Polarimetry and submm Faraday rotation)
   - assumption: SW image unpolarized so p_d is NE polarization  
  > "since the polarization of SW is negligible, the differential polarization corresponds to the absolute polarization of NE" (4.1 Polarimetry and submm Faraday rotation)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit RM using Band 7/8 data**: Fix p_d and phi0 from Band 9, fit RM with multi-frequency Rpol model using May 19-20 data  
  > "we can fix the differential polarimetry parameters in Band 9 (i.e., $p_d$ and $\phi_0$ in Eq. [\[RpolSine\]](#RpolSine)) and fit for $RM$ in the NE image" (4.1 Polarimetry and submm Faraday rotation)
   - assumption: negligible EVPA change over ~1 day  
  > "assuming a negligible change in the EVPA during this time range ($\sim$ 1 day)" (4.1 Polarimetry and submm Faraday rotation)
   - fitting: _not stated_
   - validation: Compared Rpol slopes in lambda^2 per epoch with 2012-2014  
  > "These values have been obtained by fitting a linear model in $\lambda^2$ space to each frequency configuration at each epoch." (4.1.1 Spectral behavior of Rpol)

## Software

- **CASA** : calibration and imaging  
  > "The data were calibrated within the CASA[^2] package, following a standard procedure." (2 Observations and data analysis)
- **UVMULTIFIT** : fitting two point sources to visibilities  
  > "the CASA-python task UVMULTIFIT ((cite: IMV2014))" (2 Observations and data analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| NE fractional polarization (Band 9) | 4.9 | 0.1 | % | 3 | We estimate a fractional polarization of $p_d = (4.9 \pm 0.1)$% and an EVPA of $(80.3 \pm 1.3)$ deg. for the NE image. |
| NE EVPA | 80.3 | 1.3 | deg | 3 | We estimate a fractional polarization of $p_d = (4.9 \pm 0.1)$% and an EVPA of $(80.3 \pm 1.3)$ deg. for the NE image. |
| Rotation measure | 2.3e5 | 0.6e5 | rad m^-2 | 4 | we estimate $RM = (2.3 \pm 0.6)\times 10^5$ rad m$^{-2}$ |
| Spectral index | -1.2 | 0.2 | dimensionless | 2 | $\alpha = -1.2 \pm 0.2$ |
| NE/SW Stokes I ratio change in Band 9 | 1.75 to 1.60 | not stated | dimensionless | 2 | from a value of $\sim1.75$ (at 7:10 UT) to $\sim1.60$ (at 8:17 UT) |
| SW flux variation rate (upper limit) | ~15 | not stated | mJy per hour | 2 | the SW image varied its flux density at an average rate of $\sim 15$ mJy per hour |

## Qualitative findings

- NE image polarized, SW unpolarized; RM in 2015 far lower than 2012-2014 values  
  > "the $RM$ in May 2015 is much lower than the values on 2012/2014 reported by (cite: IMV2015)" (4.1.1 Spectral behavior of Rpol)

## Claim tuples

- H: Differential polarimetry can recover polarization from dual-polarization ALMA data of PKS 1830-211 | E: Fit Rpol vs parallactic angle in Band 9 | R: p_d = 4.9±0.1%, EVPA 80.3±1.3 deg for NE | F: NE is polarized and SW is nearly unpolarized | **supported**
- H: RM remains as high as in 2012-2014 | E: Fit RM with Bands 7-9 and compare Rpol slopes | R: RM = (2.3±0.6)e5 rad m^-2, slopes compatible with zero | F: RM much lower in 2015; detection only tentative | **refuted**
- H: Intra-hour variability is detectable in Band 9 | E: Track NE/SW flux ratio over one hour | R: ~10% decrease in R_I mostly from SW increase | F: fast submm variability of SW | **supported**

## Reasoning

- Why this data: Archival ALMA observations offered the only Band 9 data over a wide parallactic angle range  
  > "However, we have also used these observations to study the AGN variability and polarization as a byproduct." (Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Poor parallactic angle coverage in Bands 7/8 limits RM precision; EVPA variability could mimic RM  
  > "The main reason for the high relative uncertainty in $RM$ is the poor parallactic-angle coverage of the data at Bands 7 and 8" (4.1 Polarimetry and submm Faraday rotation)
- Caveat (inferred, ours): RM fit assumes constant EVPA over ~1 day while allowing for rapid variation
- Caveat (inferred, ours): SW unpolarized assumption
- Caveat (inferred, ours): Fit method and error derivation not described
- Caveat (inferred, ours): Few epochs

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Project codes
- Missing: Fit procedure details
- Missing: Time binning
- Missing: Flagged channels
- Data volume (inferred): ~50-200 GB raw across five executions
- Score (inferred): 4/5, Data public archive and method simple, but fitting details and project codes not given.
- Rediscovery candidate: no, Project codes are not printed and the fitting recipe is incomplete.

## Links

- Method: (cite: IMV2015) (Differential polarimetry method and earlier RM)
- Method: (cite: IMV2014) (UVMULTIFIT)
- Companion: (cite: IMV2013) (Earlier variability study of flux ratio)

## Checks

```json
{
 "quotes": 41,
 "quotes_ok": 41,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2013.1.00020.S",
  "2013.1.00296.S",
  "2013.1.01099.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 65,
  "stated": 31,
  "rate": 0.477
 },
 "evidence_ok": true
}
```

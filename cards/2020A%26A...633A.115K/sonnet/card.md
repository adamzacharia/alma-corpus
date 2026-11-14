# ALMA and NACO observations towards the young exoring transit system J1407 (V1400 Cen)

`2020A&A...633A.115K` | Astronomy and Astrophysics 2020 | first author: Kenworthy, M. A. | arXiv: 1912.03314 | DOI: 10.1051/0004-6361/201936141

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: exoplanets, debris_disks
- Question: Can thermal emission from the putative ring system that occulted J1407 in 2007 be directly detected with ALMA and NACO, and what are its orbital parameters?  
  > "Our aim was to directly detect the thermal emission of the putative exoring system responsible for the complex deep transits observed in the light curve" (abstract)
- Target **J1407 (V1400 Cen)**: coordinates _not stated_; z/distance 138.7±0.6 pc  
  > "consistent with $d=138.7\pm 0.6{\rm~pc}$ (cite: Bailer-Jones18) and membership of the Sco-Cen OB association" (Introduction); distance from Gaia parallax / Bailer-Jones18  
  > "consistent with $d=138.7\pm 0.6{\rm~pc}$ (cite: Bailer-Jones18) and membership of the Sco-Cen OB association" (Introduction)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 7, 340 GHz continuum  
  > "in the 340 GHz (Band 7) continuum" (abstract)
- frequencies and spectral setup: SPWs at 336.495, 338.432, 348.495, 350.495 GHz; TDM, 128 channels per SPW  
  > "The observations were made in time domain mode (TDM) with 128 channels per spectral window." (2 Observations with ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: min 16.7-30.5 m, max 3638-3697 m  
  > "X54fd         | 40             | J1427-4206 | J1427-4206 | J1427-4206 | 2017-07-24     | 3638     | 30.5     | 0.51" (Table 1)
- angular resolution: 0.12x0.07 arcsec, PA -77.5 deg  
  > "which resulted in a synthesised beam of 0.12$\times$0.07$''$ at a position angle of -77.5$^\circ$." (2 Observations with ALMA)
- max recoverable scale: _not stated_
- sensitivity: rms 19 uJy/beam  
  > "we derive a peak flux of 89 $\mu$Jy/beam and an rms noise of 19 $\mu$Jy/beam" (2 Observations with ALMA)
- time on source: 2 hours on source, 5.11 hours total  
  > "for a total of 2 hours on source and a total time of 5.11 hours." (2 Observations with ALMA)
- observing dates: 20, 22, 24 July 2017  
  > "The star J1407 was observed by ALMA on UT 20, 22, and 24 July 2017" (2 Observations with ALMA)
- pi or archival as stated: _not stated_
- Other facility **VLT/NACO**: 3.8 micron ADI imaging, 5220 s on source, March 2019  
  > "Excluding telescope and instrument overheads the on-source integration was 5 220 seconds with a field rotation of 71.8$^\circ$." (3 Observations with NACO)
- Other facility **Gaia**: parallax of J1407  
  > "parallax $7.1835\pm 0.0447{\rm~mas}$ (cite: Gaia18)" (Introduction)
- External data: 2007 eclipse transverse velocity 35 km/s and ring model optical depths  
  > "moving with a transverse velocity of 35 km s$^{-1}$ relative to J1407 (assuming source is co-distant with J1407) derived from the 2007 observations (cite: Kenworthy15b)" (4 Astrometric analysis) [from (cite: Kenworthy15b)]
- External data: 1.2 mm galaxy number counts used for background probability  
  > "Using Table 2 from (cite: Aravena16) we estimate 71500 sources with a flux of $89\rm{~\mu Jy}$ or greater per square degree." (7.3 An unrelated background source) [from (cite: Aravena16)]
- External data: Substellar evolutionary model: 5 MJup, 16.67 Myr  
  > "we adopt the model from (cite: Baraffe08), which is closest to the mass and age constraints" (5 Modelling) [from (cite: Baraffe08)]
- Simulation/model as data: MCMax radiative transfer models of ring systems (Thin, Thick, Flared) at 5-50 au  
  > "We model the dust in the ring system using a 3D version of the radiative transfer code MCMax (cite: Min09)" (5 Modelling)

## Processing

### Calibration

- pipeline or manual: Pipeline reduction re-run after flagging double-source secondary phase calibrator J1405-3907  
  > "the double source secondary calibrator was flagged out of the dataset and explicitly removed from the calibration process (in the first `hifa_flagdata()` pipeline step), and the pipeline was re-run without it." (2 Observations with ALMA)
- casa version: CASA 4.7.2  
  > "All ALMA data in this paper were reduced using casa 4.7.2" (2 Observations with ALMA)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1427-4206 (1.46-1.5 Jy)  
  > "Bandpass, phase, and flux calibrations were all carried out using J1427-4206" (2 Observations with ALMA)
- flux scale uncertainty: _not stated_
- self calibration: not possible, target too faint  
  > "Self-calibration of the final dataset was not possible as the target was too faint." (2 Observations with ALMA)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The final calibrated data was imaged using natural weighting" (2 Observations with ALMA)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: none applied (source near phase centre)  
  > "As the point source was near the phase centre of the observations, we did not do any primary beam correction." (2 Observations with ALMA)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.12x0.07 arcsec, PA -77.5 deg  
  > "synthesised beam of 0.12$\times$0.07$''$ at a position angle of -77.5$^\circ$" (2 Observations with ALMA)
- final rms: 19 uJy/beam  
  > "an rms noise of 19 $\mu$Jy/beam" (2 Observations with ALMA)

### Inherited from earlier work

- Ring model geometry and optical depths per ring  
  > "the number density of the dust particles is adjusted to match the optical depth measured at optical wavelengths for each of the rings from the model in (cite: Kenworthy15b)." (5 Modelling) [from (cite: Kenworthy15b)]
- Stellar parameters for heating  
  > "Heating from the primary star J1407 and from the companion J1407b are taken into account using the stellar parameters listed in (cite: vanWerkhoven14) and (cite: Kenworthy15)" (5 Modelling) [from (cite: vanWerkhoven14); (cite: Kenworthy15)]

### Not stated but needed to reproduce (our reading)

- Image size, cell size and any clean threshold/iterations for the ALMA image
- Exact ALMA MOUS/execution identifiers and pipeline version
- Whether all three executions were concatenated and how
- Grain size distributions and mass settings used in MCMax grid
- Imfit region/fitting details
- NACO reduction parameters beyond PCA=5 (centering, frame selection, data archive ID)

## Analysis recipe

1. **Re-run ALMA pipeline and image**: Pipeline re-run without double-source secondary calibrator, natural-weighted continuum image  
  > "the pipeline was re-run without it." (2 Observations with ALMA)
   - software: CASA
   - fitting: _not stated_
   - validation: Astrometry checked with ALMA Allegro node and independent pipelines  
  > "confirming with both the ALMA Allegro node in Leiden and independently with our own reduction pipelines that the astrometry is consistent" (4 Astrometric analysis)
2. **Measure source position, size and flux**: imfit for position and size; imstat for peak and rms  
  > "Using the casa task `imstat`, we derive a peak flux of 89 $\mu$Jy/beam and an rms noise of 19 $\mu$Jy/beam, resulting in a 4.7 $\sigma$ detection." (2 Observations with ALMA)
   - software: CASA imfit, CASA imstat
   - fitting: _not stated_
   - validation: _not stated_
3. **NACO PCA-ADI contrast and mass limits**: PynPoint PCA with 5 components, fake companion injection, Mawet14 small-sample correction, AMES-Cond conversion to mass  
  > "We determined that 5 PCA components is a reasonable compromise between speckle removal and sky background sensitivity" (3 Observations with NACO)
   - software: PynPoint
   - parameter: 5 sigma contrast; separations 0.14-1.20 arcsec in 0.054 arcsec steps; 60 deg PA increments  
  > "at various angular separations (0.14 to 1.20 arcsec in 0.054 arcsecond steps) and position angles (at 60 degree increments starting from 0 degrees)" (3 Observations with NACO)
   - assumption: age 16 Myr (Sco-Cen)  
  > "assume an age of 16 Myr corresponding to the age of Sco-Cen" (3 Observations with NACO)
   - fitting: _not stated_
   - validation: Fake companion injection to correct flux loss  
  > "fake point sources are injected at several radii from the star into the data, and then the recovered flux is measured after the pipeline data reduction." (3 Observations with NACO)
4. **Model ring thermal emission**: MCMax radiative transfer for Thin, Thick, Flared ring models with varying separation 5-50 au and grain sizes  
  > "The parameter space for ring models is explored by varying the separation of the ring system from the star (from 5 au to 50 au)" (5 Modelling)
   - software: MCMax
   - parameter: outer radius 0.6 au; inner edge 0.19 au; 40% pyroxene, 60% water ice  
  > "We assume an outer radius of 0.6 au for the ring system (equivalent to the Hill radius derived above)" (5 Modelling)
   - assumption: Sigma = tau_V/kappa_V; irregular grains; central object 5 MJup, 16.67 Myr  
  > "The surface density is calculated to match the optical depth in the rings as measured: $\Sigma = \tau_V/\kappa_V$" (5 Modelling)
   - fitting: _not stated_
   - validation: _not stated_
5. **Assess background galaxy probability**: Scale Aravena16 1.2 mm counts to 850 um and compute Poisson probability within 0.5 arcsec and annulus  
  > "The probability of finding more than zero galaxies within a radius of $0.5$ arcseconds is around 0.0047, or 1 in 212" (7.3 An unrelated background source)
   - assumption: S_1.2mm = 0.6 S_850um  
  > "Taking the mean of the two shorter wavelengths gives $S_{1.2\rm{mm}}=0.6S_{\rm 850\mu m}$." (7.3 An unrelated background source)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.2: ALMA reduction, imaging, imfit, imstat  
  > "All ALMA data in this paper were reduced using casa 4.7.2" (2 Observations with ALMA)
- **PynPoint** : NACO PCA-ADI reduction  
  > "Processing the data with the latest release of the `PynPoint` package (cite: Stolker19)" (3 Observations with NACO)
- **MCMax** 3D version: radiative transfer of ring models  
  > "using a 3D version of the radiative transfer code MCMax (cite: Min09)" (5 Modelling)
- **Astropy** : general analysis  
  > "This research made use of Astropy" (Acknowledgements)
- **APLpy** : plotting  
  > "This research made use of APLpy, an open-source plotting package for Python" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA source peak flux | 89 | rms 19 | uJy/beam | 2 | we derive a peak flux of 89 $\mu$Jy/beam and an rms noise of 19 $\mu$Jy/beam, resulting in a 4.7 $\sigma$ detection. |
| 3sigma upper limit at J1407 | 57.6 | not stated | uJy | 2 | The $3\sigma$ upper limit on this ALMA non-detection is $57.6{\rm~\mu Jy}$. |
| Separation of ALMA source from J1407 2007 location | 438 | 8 | mas | 2 | is $438\pm 8$ mas, which is equal to a separation of 61 au |
| Expected separation for 35 km/s free-floating object | 543 | 82 | mas | 0 | ($543\pm82\rm{~mas),}$ |
| NACO mass limit at 30 au | 6 | not stated | MJup | 3 | down to $6M_{Jup}$ at 30au (0.25 arcsec) and dropping to less than $4M_{Jup}$ beyond 100au |
| Background galaxy probability within 0.5 arcsec | 0.0047 | not stated | dimensionless | 5 | The probability of finding more than zero galaxies within a radius of $0.5$ arcseconds is around 0.0047 |
| Predicted proper motion | 43 | not stated | mas/yr | 0 | the proper motion of the ALMA source is $43$ mas/yr |

## Qualitative findings

- No ALMA or NACO source within 100 mas of J1407; ALMA upper limit implies bound ring dust <1 mm  
  > "implies that a hypothesised bound ring system is composed of dust smaller than $1\rm{~mm}$ in size" (abstract)

## Claim tuples

- H: A bound ring system around J1407 is detectable with ALMA | E: Band 7 continuum at J1407 plus MCMax models | R: No detection, 3sigma < 57.6 uJy | F: Bound rings must be small-grained (<1 mm) and young | **supported**
- H: The ALMA source is the free-floating ring system from the 2007 eclipse | E: Astrometry vs 35 km/s motion; NACO limits; models | R: Separation 438±8 mas vs 543±82 mas; NACO <6 MJup | F: Consistent with free-floating ringed substellar object, but a background galaxy is not excluded | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Background galaxy judged unlikely (~1 in 212) but not ruled out; noise peak considered unlikely  
  > "It seems unlikely that the source is a background galaxy, but we cannot rule this hypothesis out without a second epoch observation with ALMA." (7.3 An unrelated background source)
- How they decided it was enough: _not stated_
- Limitation (authors): Second ALMA epoch needed to confirm via proper motion  
  > "An observation with ALMA three or more years after the 2017 detection will show this proper motion with enough significance" (8 Conclusions)
- Caveat (inferred, ours): Only 4.7 sigma detection; noise-peak probability not quantified
- Caveat (inferred, ours): Astrometric uncertainty from phase calibrator not fully propagated
- Caveat (inferred, ours): Background probability depends on flux scaling between bands
- Caveat (inferred, ours): Ring models are lower bounds with limited parameter exploration

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, image size, threshold)
- Missing: MCMax grain-size/mass grid details
- Missing: NACO raw data identifiers
- Data volume (inferred): ~10-50 GB for three ALMA executions
- Score (inferred): 3/5, ALMA project code and CASA version stated, but imaging parameters and modelling grid details missing.
- Rediscovery candidate: no, Public status of data not stated and imaging recipe incomplete.

## Links

- Method: (cite: Stolker19) (PynPoint package)
- Method: (cite: Min09) (MCMax radiative transfer code)
- Method: (cite: Mawet14) (small-sample correction to contrast)
- Companion: (cite: Kenworthy15b) (ring model of 2007 eclipse)
- Companion: (cite: Mamajek12) (discovery of J1407 eclipse)
- Related: Sco-Cen association
- Related: SuperWASP
- Related: ASAS

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2016.1.00470.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 46,
  "rate": 0.582
 },
 "evidence_ok": true
}
```

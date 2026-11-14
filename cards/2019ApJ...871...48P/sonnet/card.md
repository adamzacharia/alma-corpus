# High-resolution ALMA Observations of HD 100546: Asymmetric Circumstellar Ring and Circumplanetary Disk Upper Limits

`2019ApJ...871...48P` | The Astrophysical Journal 2019 | first author: Pineda, Jaime E. | arXiv: 1811.10365 | DOI: 10.3847/1538-4357/aaf389

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, exoplanets
- Question: What is the dust ring structure of the HD 100546 disk at ~4 au resolution, and can compact circumplanetary disk emission be detected at the claimed protoplanet positions?  
  > "data with higher angular resolution and image fidelity were needed to settle this issue." (The HD 100546 system); "high enough angular resolution to separate the CPD and CSD." (Introduction)
- Target **HD 100546**: coordinates Phase center 11:33:25.318652 -70:11:41.23173  
  > "HD 100546 is a Herbig Ae/Be star located at a distance of 110.02$\pm$0.62 pc (cite: Gaia2018_DR2)." (The HD 100546 system); "11:33:25.318652" (Table 1); z/distance 110.02±0.62 pc  
  > "HD 100546 is a Herbig Ae/Be star located at a distance of 110.02$\pm$0.62 pc (cite: Gaia2018_DR2)." (The HD 100546 system); "11:33:25.318652" (Table 1); distance from Gaia DR2  
  > "HD 100546 is a Herbig Ae/Be star located at a distance of 110.02$\pm$0.62 pc (cite: Gaia2018_DR2)." (The HD 100546 system); "11:33:25.318652" (Table 1)

## Data provenance

- ALMA projects: 2015.1.00806.S
- bands: Band 7 (870 um)  
  > "HD 100546 was observed on 2015 December 2nd with ALMA using Band 7 receivers under project 2015.1.00806.S (PI: J.E. Pineda)." (Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 17 to 10800 m, 36 antennas  
  > "The array configuration included 36 antennas with baselines between 17 and 10800 m" (Data)
- angular resolution: 0.056x0.041 arcsec natural; 0.047x0.031 arcsec Briggs 0.5  
  > "which results in an angular resolution of 0.047$\ensuremath{''} \times$0.031$\ensuremath{''}$ (PA=33.9$\ensuremath{^\circ}$)" (Data)
- max recoverable scale: ~1 arcsec (insufficient baselines <100 m)  
  > "insufficient short baselines ($<$100 m) to properly recover emission at scales larger than $\approx 1$ $''$" (Data)
- sensitivity: 66 uJy/beam (Briggs), 86 uJy/beam (natural); CO 5.8 mJy/beam/channel  
  > "with an rms noise of 86 $\mu$Jy beam$^{-1}$, as estimated from emission free regions" (Data)
- time on source: _not stated_
- observing dates: 2015 December 2  
  > "HD 100546 was observed on 2015 December 2nd" (Data)
- pi or archival as stated: PI J.E. Pineda (own Cycle 3 data)  
  > "project 2015.1.00806.S (PI: J.E. Pineda)" (Data)
- Line: CO J=3-2 (not stated)
- Other facility **SPHERE/ZIMPOL**: Qphi polarimetric image compared with ALMA maps  
  > "we show the SPHERE $Q_\phi$ image with our ALMA continuum map overlaid in contours" (Comparison with SPHERE scattered light data)
- Other facility **ALMA Cycle 0**: Lower-resolution continuum and CO data used for total flux comparison and CO extent  
  > "This flux is consistent with the total flux measured in the ALMA C0 data." (Data)
- External data: Disk inclination and position angle for deprojection  
  > "using the position angle and disk inclination parameters obtained by (cite: Pineda2014)" (Maps and brightness profile) [from (cite: Pineda2014)]
- External data: Radiative transfer dust temperature profile; T_d,mean=53 K  
  > "with an average temperature of $T_{d,mean}=$53 K between 20 and 50 au" (Maps and brightness profile) [from (cite: Pineda2014)]
- External data: Teff=9800 K and stellar accretion rate  
  > "$T_{\rm eff}=9,800$ K (cite: Fairlamb2015)" (Updated stellar parameters) [from (cite: Fairlamb2015)]
- External data: CSD mass of 50 MJ  
  > "the CSD mass of 50 $M_J$ (cite: Pineda2014)" (CPD masses and ages) [from (cite: Pineda2014)]
- External data: CPD-CSD-planet mass relation (Eq. 7)  
  > "using Eq. 7 from (cite: Szulagyi2017_CPD_GAP)" (CPD masses and ages) [from (cite: Szulagyi2017_CPD_GAP)]
- External data: APEX CO total flux 191 Jy km/s  
  > "reported by (cite: Panic_2009-Disk_Models) using APEX of 191 Jy km s$^{-1}$" (Data) [from (cite: Panic_2009-Disk_Models)]
- Simulation/model as data: PHOENIX stellar photosphere model and Siess et al. PMS tracks  
  > "We adopt a PHOENIX model of the stellar photosphere (cite: Hauschildt1999:Paper1)" (Updated stellar parameters)

## Processing

### Calibration

- pipeline or manual: Standard flagging and calibration in CASA 4.5.1  
  > "The standard flagging and calibration was done using CASA 4.5.1 (cite: McMullin2007)" (Data)
- casa version: CASA 4.5.1 calibration; CASA 4.7 imaging  
  > "while imaging was done using CASA 4.7 and multiscale clean" (Data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1107-4449  
  > "while J1107$-$4449 was used to set the flux amplitude" (Data)
- flux scale uncertainty: _not stated_
- self calibration: Shortest phase and amplitude cycles of 10 and 60 s  
  > "Self-calibration was performed with the shortest phase and amplitude cycle of 10 and 60 seconds, respectively." (Data)

### Imaging

- task: _not stated_
- deconvolver: multiscale clean  
  > "imaging was done using CASA 4.7 and multiscale clean" (Data)
- weighting robust: natural; Briggs robust 0.5; CO natural  
  > "Similarly, we imaged the continuum using a Briggs weight of $0.5$" (Data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Per-channel clean mask around bright emission; Keplerian mask (within 2 km/s, R=352 au) for moments  
  > "only voxels that are within 2 km s$^{-1}$(similar to the linewidth in the inner part of the disk, $<$150 au) from predicted Keplerian velocity are kept in the final mask" (Data)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub on visibilities after applying self-cal solutions  
  > "obtained from the continuum subtracted visibilities resulting from using the task `uvcontsub`" (Data)
- line free channels: continuum from line free channels (ranges not given)  
  > "The 870 $\mu$m continuum was obtained from line free channels" (Data)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.047x0.031 arcsec PA 33.9 (Briggs); CO 0.059x0.044 PA 18.22  
  > "Beam PA" (Table 1)
- final rms: 66 uJy/beam continuum; 5.8 mJy/beam/channel CO  
  > "We estimate the rms in the spectral cube using the line-free channels as 5.8 mJy beam$^{-1}$ per channel" (Data)

### Inherited from earlier work

- Keplerian-mask moment map approach  
  > "which is a similar to (cite: Friesen2017-GAS; Bergner2018; Calcutt2018)" (Data) [from (cite: Friesen2017-GAS; Bergner2018; Calcutt2018)]
- Dust opacity and composition  
  > "This opacity assumes a dust composition and grain size distribution as in (cite: Isella2012)." (Circumplanetary disk upper limits) [from (cite: Isella2014-CPD; Isella2012)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges and spectral windows
- Multiscale clean scales, cell and image size, mask details
- Phase calibrator/self-cal solint beyond shortest values
- Fit starting values, optimiser and uncertainties for the GALARIO model
- CO rest frequency and spectral setup
- Planet position used for CPD upper limit and its flux measurement method

## Analysis recipe

1. **Update stellar parameters**: PHOENIX photosphere scaled to Gaia distance and compared with Siess PMS tracks  
  > "are compared to the Pre-Main Sequence (PMS) stellar tracks by (cite: Siess2000)" (Updated stellar parameters)
   - parameter: Teff=9800 K, Av=0.1  
  > "de-reddened ($A_{\rm V}=0.1$ mag) $V$-band photometry" (Updated stellar parameters)
   - assumption: Tracks with depleted metallicity Z  
  > "We employed the tracks with depleted abundance of $Z$" (Updated stellar parameters)
   - fitting: _not stated_
   - validation: _not stated_
2. **Image continuum and CO**: CASA multiscale clean; natural and Briggs 0.5 continuum; uvcontsub CO cube; Keplerian-mask moment maps  
  > "imaging was done using CASA 4.7 and multiscale clean" (Data)
   - software: CASA
   - fitting: _not stated_
   - validation: Total flux compared to Cycle 0 and APEX  
  > "which is in excellent agreement with the total integrated intensity CO reported by (cite: Panic_2009-Disk_Models)" (Data)
3. **Parametric continuum model**: Two concentric Gaussian rings + central Gaussian + vortex sampled on observed visibilities with GALARIO  
  > "We use `GALARIO` (cite: Tazzari_2017-GALARIO) to sample the model image on the same visibilities as the observations." (Parametric model)
   - software: GALARIO, CASA, Python
   - fitting: chi2 minimized in Python  
  > "The $\chi^2$ is then calculated using the sampled visibilities, and then minimized in Python to find the optimal model." (Parametric model)
   - validation: Residual image from model visibilities imaged in CASA  
  > "The observed model and residuals are produced by sampling the same visibilities as the data, and then performing the imaging in CASA." (Parametric model)
4. **Radial cuts**: Beam-wide strips along major axis and vortex maximum fitted with 5 Gaussians  
  > "Fitting the profiles with a superposition of 5 Gaussians provides a good fit, however." (Radial cuts)
   - fitting: _not stated_
   - validation: _not stated_
5. **CPD upper limits**: 3-sigma limit on point-like flux converted to mass (optically thin) and radius (optically thick)  
  > "place a strong 3-$\sigma$ detection limit of 198 $\mu$Jy for an unresolved source" (Circumplanetary disk emission)
   - parameter: kappa=0.2 (7mm/lambda) cm2/g; f_d=0.01; T=53 K  
  > "Finally, $f_d$ is assumed to be 0.01." (Circumplanetary disk upper limits)
   - assumption: Distance 110.02 pc; dust temperature 53 K (932 K alternative)  
  > "while the radius would be only 0.09 au for a temperature of $932$ K" (Circumplanetary disk upper limits)
   - fitting: _not stated_
   - validation: Compared with Szulagyi 2018 and Zhu 2016 predicted fluxes  
  > "which is comparable to the upper limits here reported, and therefore it is still consistent with the ALMA observations." (Circumplanetary disk upper limits)
6. **Planet mass and inner disk mass**: Szulagyi 2017 CPD-CSD-planet relation; inner disk mass from the same opacity equation at 300 K  
  > "a disk temperature of 300 K, to derive an inner disk mass of 15 $M_{\ensuremath{\oplus}}$" (Central or inner disk)
   - assumption: CSD mass 50 MJ; ongoing accretion  
  > "This assumes that the planet is still accreting from the surrounding CSD" (CPD masses and ages)
   - fitting: single Gaussian fit to central source  
  > "We fitted a single Gaussian over a 80 mas region" (Central or inner disk)
   - validation: _not stated_

## Software

- **CASA** 4.5.1 (calibration); 4.7 (imaging): Calibration, imaging, uvcontsub  
  > "The standard flagging and calibration was done using CASA 4.5.1 (cite: McMullin2007)" (Data)
- **GALARIO** : Sampling model on visibilities and fitting  
  > "We use `GALARIO` (cite: Tazzari_2017-GALARIO) to sample the model image on the same visibilities as the observations." (Parametric model)
- **Astropy** : Analysis  
  > "This research made use of `Astropy`, a community-developed core Python package for Astronomy" (Acknowledgments)
- **Matplotlib** : Plotting  
  > "Astropy (cite: Robitaille_2013), Matplotlib (cite: Hunter_2007), CASA (cite: McMullin2007), GALARIO (cite: Tazzari_2017-GALARIO)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum rms (Briggs 0.5) | 66 | not stated | uJy/beam | 2 | / rms / ($\mu$Jy beam$^{-1}$) / 66 / |
| Total continuum flux | 1.27 | not stated | Jy | 2 | / Total Flux / (Jy) / 1.27 / |
| 3-sigma point source limit at planet positions | 198 | not stated | uJy | 5 | 3-$\sigma$ detection limit of 198 $\mu$Jy |
| CPD mass upper limit (optically thin) | 1.44 | not stated | Earth masses | 5 | we determine the CPD (dust and gas) mass upper limit in the optically thin case to be 1.44 $M_{\ensuremath{\oplus}}$ |
| CPD radius upper limit (optically thick, 53 K) | 0.44 | not stated | au | 5 | An upper limit for the CPD radius of 0.44 au is obtained |
| Planet mass upper limit from CPD-CSD relation | 1.65 | not stated | MJ | 6 | we place a planetary mass upper limit of 1.65 $M_J$ |
| Stellar mass | 2.2 | ±0.2 | Msun | 1 | $M_*=2.2\pm0.2$ M$_\odot$ |
| Inner disk mass | 15 | not stated | Earth masses | 6 | an inner disk mass of 15 $M_{\ensuremath{\oplus}}$ |
| Inner disk depletion lifetime | 500 | not stated | yr | 6 | is only 500 yr |
| Integrated CO flux | 190 | not stated | Jy km/s | 2 | The total flux of the integrated intensity CO cube is 190 Jy km s$^{-1}$ |

## Qualitative findings

- Asymmetric ring at 20-40 au with 15-25% flux asymmetry; central unresolved source  
  > "The continuum disk emission is resolved as ring-like (between 20–40 au) and shows a flux asymmetry of $\approx$15–25%." (Summary)
- CO spiral-like feature matches SPHERE spiral  
  > "This coincidence might suggests that the spiral-like feature might be real and present in the disk surface." (Comparison with SPHERE scattered light data)

## Claim tuples

- H: Is there compact CPD continuum emission at the claimed protoplanet positions? | E: Search 66 uJy/beam Briggs image at planet positions | R: No point-like emission; 3-sigma limit 198 uJy | F: CPD mass <1.44 Mearth (thin), radius <0.44 au (thick); inconsistent with several accretion models, gas-starved still compatible | **supported**
- H: Is the dust ring asymmetric? | E: Parametric fit and radial cuts | R: Two Gaussian rings plus vortex fit; 15-25% peak asymmetry | F: Asymmetric ring is real | **supported**
- H: Does the CO map show a spiral matching scattered light? | E: Compare CO moment 0 with SPHERE Qphi | R: Spiral-like CO enhancement coincident with NE arm | F: Possible real surface spiral, needs confirmation | **partially**

## Reasoning

- Why this data: Higher resolution needed to resolve asymmetry and separate CPD from disk  
  > "data with higher angular resolution and image fidelity were needed to settle this issue." (The HD 100546 system)
- Why this method: _not stated_
- Alternative: Asymmetric Gaussians for radial profiles gave poor fits  
  > "but the results are rather poor and therefore not reported here." (Radial cuts)
- How they decided it was enough: _not stated_
- Limitation (authors): Missing short baselines limit large-scale emission; imaging artifacts in CO  
  > "still some imaging artifacts are present due to the missing short spacings" (Data)
- Caveat (inferred, ours): CPD limits depend on assumed temperature, opacity and gas-to-dust ratio
- Caveat (inferred, ours): Fit uncertainties for the parametric model not given
- Caveat (inferred, ours): Spiral claim from single CO moment map with artifacts

## Reproducibility

- Data public (paper): Project code given; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00806.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Line-free channels, clean scales, mask and image size
- Missing: Starting values and uncertainties for the model fit
- Missing: Planet candidate positions used
- Data volume (inferred): Large, probably several hundred GB raw for long-baseline Band 7 data
- Score (inferred): 3/5, Public project code and main recipe stated, but many imaging and fitting details are missing.
- Rediscovery candidate: yes, Archive data are available and the results are numeric, though some settings are missing.

## Links

- Method: (cite: Tazzari_2017-GALARIO) (Visibility sampling and model fitting)
- Companion: (cite: Pineda2014) (Cycle 0 ALMA data of the same disk)
- Companion: (cite: Walsh2014) (Independent Cycle 0 analysis)
- Related: ALMA Cycle 0 HD 100546 observations

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
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 85,
  "stated": 59,
  "rate": 0.694
 },
 "evidence_ok": true
}
```

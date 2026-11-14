# The unbearable opaqueness of Arp220

`2016A&A...590A..25M` | Astronomy and Astrophysics 2016 | first author: Martín, S. | arXiv: 1603.01291 | DOI: 10.1051/0004-6361/201528064

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, astrochemistry
- Question: What do vibrationally excited HCN emission and the HCN/HCO+ ground-state lines reveal about the morphology, physical structure, absorption and powering of the two nuclei of Arp 220?  
  > "We explore the potential of imaging vibrationally excited molecular emission at high angular resolution to better understand the morphology and physical structure of the dense gas in Arp 220" (abstract)
- Target **Arp 220 (western and eastern nuclei)**: coordinates WN 15h34m57.223s +23d30m11.53s; EN 15h34m57.293s +23d30m11.38s (J2000)  
  > "separated by $\sim1"$ ($\sim370$ pc for $D=76$ Mpc)" (Introduction); "These sky frequencies are redshifted, adopting $z=0.018126$." (Observations); z/distance z=0.018126; D=76 Mpc  
  > "separated by $\sim1"$ ($\sim370$ pc for $D=76$ Mpc)" (Introduction); "These sky frequencies are redshifted, adopting $z=0.018126$." (Observations); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00453.S
- bands: Band 6 and Band 7  
  > "Band 6 observations were carried out on July 8,$^{}$ 2014, with 31 antennas." (Observations)
- frequencies and spectral setup: 2x1.875 GHz spectral windows per sideband overlapping by 100 MHz; Band 6 centered at 247.1 and 262.5 GHz, Band 7 at 336.8 and 348.7 GHz  
  > "The correlator was configured on each sideband with $2\times1.875$ GHz spectral windows overlapping by 100 MHz." (Observations); "the two bands were centered on the sky frequencies 336.8 and 348.7 GHz" (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.5'' matching synthesized beams  
  > "The similar *uv*-coverage in both bands resulted in matching $\sim 0.5''$ synthesized beams" (Observations)
- max recoverable scale: _not stated_
- sensitivity: Band 6 rms 1.1-1.3 mJy/beam per ~27-28 km/s channel; Band 7 ~1 mJy/beam per ~25-26 km/s channel  
  > "resulted in an rms of 1.1-1.3 mJy beam$^{-1}$ at the smoothed resolution" (Observations); "resulted in an rms of $\sim1$ mJy beam$^{-1}$ per smoothed channel" (Observations)
- time on source: Band 6 2.5 min; Band 7 7.2 min total  
  > "The short snapshot with 2.5 minutes of on-source integration" (Observations); "The total on-source integration of 7.2 minutes" (Observations)
- observing dates: Band 6: 8 July 2014; Band 7: 27 April and 27 May 2014  
  > "Band 7 observations were carried out in two separate snapshots on April 27$^{}$ (34 antennas) and May 27,$^{}$ 2014 (31 antennas)." (Observations)
- pi or archival as stated: _not stated_
- Line: HCN J=3-2 (261.152 GHz (as given; sky-frequency))
- Line: HCO+ J=3-2, 4-3 (262.794 GHz (sky), 350.383 GHz (sky))
- Line: HCN v2=1f J=3-2, 4-3 (267.199 GHz, 356.255 GHz)
- External data: Nuclear FIR luminosities and dust properties used for L_vib/L_FIR  
  > "We also present their ratios relative to the total luminosity of each nucleus as estimated by (cite: Wilson2014)." (5.3 High L_vib/L_FIR ratio) [from (cite: Wilson2014)]
- External data: HC3N physical conditions used to estimate line blending contamination  
  > "From the physical conditions derived by (cite: Mart’in2011), we infer for this line a peak flux density integrated over the whole source of $\sim20-40$ mJy" (3.2.1 Line blending) [from (cite: Mart’in2011)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.2.1  
  > "The data were calibrated and deconvolved using CASA release 4.2.1" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan, Butler-JPL-Horizons 2012 models; bandpass J1550+0527, gain J1516+1932  
  > "J1550+0527, Titan, and J1516+1932 were used as bandpass, flux, and gain calibrators." (Observations); "flux calibration used the Butler-JPL-Horizons 2012 models." (Observations)
- flux scale uncertainty: better than 10-15%  
  > "Flux accuracy is expected to be better than $10-15\%$." (Observations)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: in uv visibilities, first-order linear fit, separately for bands 6 and 7  
  > "Continuum subtraction was performed in the *uv* visibilities." (Observations); "A first-order linear fit to the continuum emission was used individually for bands 6 and 7." (Observations)
- line free channels: selected by visual inspection and spectroscopic catalogs; 15-25% of bandwidth usable (5% in lower sideband of band 6)  
  > "we selected regions that we estimated to be free of molecular emission based on both visual inspection and spectroscopic catalogs." (Observations)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: channels degraded by 48 (band 6) and 60 (band 7) to ~25-28 km/s  
  > "The resolution was degraded by 60 channels to a velocity resolution of $\sim 25-26$ $\rm km\,s^{-1}$." (Observations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Full spectral line survey data context; isotopolog and other analysis deferred  
  > "as part of a spectral line survey of Arp 220 (Martín et al. in preparation)" (Observations) [from Martín et al. in preparation]
- Virial mass formula M_vir=250 dv^2 R  
  > "we can estimate virial masses as $(M_{vir}/M_\odot)=250(\Delta v_{1/2}/{\rm km~s^{-1}})^2(R/{\rm pc})$ (cite: Wilson2009)" (3.3.2 Gas surface densities) [from (cite: Wilson2009)]

### Not stated but needed to reproduce (our reading)

- tclean/clean parameters (weighting, robust, cell, image size, deconvolver)
- exact line-free channel ranges
- number and selection of antennas/configurations
- how the scaled HCN profile was chosen for HCO+ subtraction
- gas-surface-density area definition
- line luminosity conversion details and L_FIR values used

## Analysis recipe

1. **Measure continuum fluxes and nuclear positions**: Line-free channels give continuum per band; double Gaussian fit in image plane to the two nuclei  
  > "The good signal-to-noise ratio of the observations allowed fitting a double Gaussian in the image plane to the two nuclei." (3.1 Continuum emission)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared with literature and single-dish flux; positions agree across bands  
  > "The positions derived for all bands agree within the uncertainties." (3.1 Continuum emission)
2. **Characterize absorption systems and nuclear velocities**: Gaussian fit to unabsorbed HCO+ 3-2 channels, subtract, then multi-Gaussian fit to absorptions  
  > "We assumed a Gaussian shape for the HCO$^+$ emission and performed a fit to the unabsorbed channels, while masking those where the absorption is observed." (3.2.2 Absorption systems)
   - assumption: Gaussian intrinsic emission profile  
  > "we considered the Gaussian as the best approach at the current resolution" (3.2.2 Absorption systems)
   - fitting: Gaussian fits; statistical errors not meaningful  
  > "we do not refer to the statistical errors of the fits since they are not meaningful" (3.2.2 Absorption systems)
   - validation: Blueshifted absorption agrees with HCN IR absorption centroid  
  > "Our corrected blueshifted absorption agrees better with the average velocity centroid of $-110\pm10$ $\rm km\,s^{-1}$" (3.2.2 Absorption systems)
3. **Fit HCN v2=1f lines de-blended from HCO+**: Double Gaussian fit, and fit to residual after subtracting scaled HCN 3-2 profile  
  > "First we fit the redshifted peak of HCO$^+$ and the HCN $v_2=1f$ line with a double Gaussian." (3.3 HCN v2=1 emission)
   - fitting: Gaussian  
  > "We assumed a Gaussian shape for the HCO$^+$ emission and performed a fit to the unabsorbed channels, while masking those where the absorption is observed." (3.2.2 Absorption systems)
   - validation: Central velocities of two transitions agree better with subtraction method  
  > "the central velocities derived from the two HCN $v_2=1f$ transitions show agree better than when derived from a double Gaussian fit" (3.3 HCN v2=1 emission)
4. **Virial masses and gas surface densities**: M_vir=250 dv^2 R with R~25-30 pc, f_g=0.1  
  > "These masses correspond to gas surface densities of $3\pm0.3\times10^4~M_\odot~\rm pc^{-2}$ (WN) and $1.1\pm0.1\times10^4~M_\odot~\rm pc^{-2}$ (EN) assuming a gas fraction $f_g=0.1$." (3.3.2 Gas surface densities)
   - assumption: gas fraction 0.1  
  > "assuming a gas fraction $f_g=0.1$" (3.3.2 Gas surface densities)
   - fitting: _not stated_
   - validation: Compared with Engel2011 mass estimates and alternative virial formula (factor ~2 lower)  
  > "our derived masses would be a factor of $\sim2$ lower" (3.3.2 Gas surface densities)
5. **Size of vibrational emission and excitation analysis**: Gaussian fits to integrated maps of HCN 4-3 v2=1f; LTE excitation temperature from 3-2/4-3; optically thick size limits  
  > "Gaussian fits were performed to these integrated emission maps." (5.2 Vibrational emission within the opaque dust)
   - assumption: LTE; T_vib 300 K or T_ex 40 K as limiting cases  
  > "If we assume local thermodynamic equilibrium (LTE) conditions" (5.1 HCN excitation of vibrational levels)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2.1: calibration and deconvolution  
  > "The data were calibrated and deconvolved using CASA release 4.2.1" (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| V_WN | 5342 | 4 | km/s | 2 | individual nuclear velocities of $V_{WN}=5342\pm4$ $\rm km\,s^{-1}$  and $V_{EN}=5454\pm8$ $\rm km\,s^{-1}$ |
| V_EN | 5454 | 8 | km/s | 2 | individual nuclear velocities of $V_{WN}=5342\pm4$ $\rm km\,s^{-1}$  and $V_{EN}=5454\pm8$ $\rm km\,s^{-1}$ |
| Gas surface density WN | 3e4 | 0.3e4 | Msun/pc^2 | 4 | $3\pm0.3\times10^4~M_\odot~\rm pc^{-2}$ (WN) |
| Gas surface density EN | 1.1e4 | 0.1e4 | Msun/pc^2 | 4 | $1.1\pm0.1\times10^4~M_\odot~\rm pc^{-2}$ (EN) |
| Excitation temperature of HCN v2=1f (WN, EN) | 38 K, 45 K | not stated | K | 5 | is $T_{\rm ex}\sim38$ K and $45$ K for the WN and EN, respectively |
| Vibrational emission extent | ~60x50 pc | not stated | pc | 5 | the HCN vibrational emission is confined to a barely resolved region of $\sim60\times50$ pc in the $4-3$ transition |
| Optically thick size lower limits | 22 pc (WN), 15 pc (EN) | not stated | pc | 5 | we can establish lower limits to the emitting region of 15 pc (EN) and 22 pc (WN) |

## Qualitative findings

- Absorption may hide up to ~70% of HCN and HCO+ line emission; blueshifted absorptions indicate outflows  
  > "absorptions alone could hide up to $\sim70\%$ of the total intrinsic HCN and HCO$^+$ emission lines" (6)

## Claim tuples

- H: HCN v2=1f traces the innermost regions of both nuclei | E: Imaged and fitted HCN v2=1f 3-2 and 4-3 emission | R: Detected in both nuclei, marginally resolved ~60x50 pc, centered on nuclear velocities | F: Vibrational HCN probes much smaller scales than ground-state lines | **supported**
- H: Absorption affects ground-state dense gas tracers | E: Gaussian emission fits to HCO+ 3-2 and absorption imaging | R: Up to ~70% absorbed; blueshifted systems | F: HCN and HCO+ poorly trace dense gas and indicate outflows | **supported**
- H: Vibrational luminosity relative to L_FIR is unusual | E: Computed L_vib/L_FIR | R: Highest ratio among known galaxies; EN higher than WN | F: Not explained by Galactic-type hot cores | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Collisional excitation and hot ISM without IR pumping rejected  
  > "further confirm the impossibility of understanding HCN excitation without taking into account radiative excitation through IR photons" (5.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Line blending and absorption make de-blending highly uncertain  
  > "Although subtracting the HCN $3-2$ profile to account for HCO$^+$ is highly uncertain" (3.3)
- Caveat (inferred, ours): Gaussian emission assumption drives absorption and velocity results
- Caveat (inferred, ours): Fixed gas fraction 0.1 and virial radius assumption
- Caveat (inferred, ours): Short snapshots limit sensitivity

## Reproducibility

- Data public (paper): ALMA project 2012.1.00453.S cited  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00453.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: imaging parameters
- Missing: line-free channel ranges
- Missing: de-blending scaling
- Data volume (inferred): ~10-50 GB raw
- Score (inferred): 3/5, Public data and clear Gaussian-fit methods, but imaging parameters and de-blending details missing.
- Rediscovery candidate: yes, Public data and numeric Gaussian-fit results, though imaging details must be reconstructed.

## Links

- Companion: Aalto et al. 2015b (cite: Aalto2015a) (Earlier WN HCN v2=1f detection and pumping framework)
- Related: Arp 220 ALMA spectral line survey (Martín et al. in preparation)

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 38,
  "rate": 0.551
 },
 "evidence_ok": true
}
```

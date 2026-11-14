# An ALMA Constraint on the GSC 6214-210 B Circum-Substellar Accretion Disk Mass

`2015ApJ...805L..17B` | The Astrophysical Journal Letters 2015 | first author: Bowler, Brendan P. | arXiv: 1505.01483 | DOI: 10.1088/2041-8205/805/2/L17

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, exoplanets
- Question: How massive is the circum-substellar accretion disk around the ~15 MJup companion GSC 6214-210 B (and any disk around the host star), as constrained by 880 um continuum?  
  > "neither component was detected in our 880 $\mu$m (341 GHz) continuum observations down to a 3-$\sigma$ limit of 0.22 mJy/beam." (abstract)
- Target **GSC 6214-210 A and B**: coordinates RA 16:21:54.67, Dec -20:43:09.2  
  > "GSC 6214-210 AB ($\alpha$=16:21:54.67, $\delta$=–20:43:09.2)" (3 ALMA Observations); "the distance to the system (145 pc)" (4 Results); z/distance 145 pc  
  > "GSC 6214-210 AB ($\alpha$=16:21:54.67, $\delta$=–20:43:09.2)" (3 ALMA Observations); "the distance to the system (145 pc)" (4 Results); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00487.S
- bands: Band 7 (880 um, 341 GHz)  
  > "was observed with ALMA in Band 7 at 880 $\mu$m (341 GHz) during Cycle 2 Early Science operations on UT 2014 June 30." (3 ALMA Observations)
- frequencies and spectral setup: four SPWs at 334.0, 336.0, 346.0, 347.8 GHz; 346.0 GHz window 1920 channels of 0.98 MHz; others 128 channels of 15.6 MHz  
  > "four spectral windows centered at 334.0, 336.0, 346.0, and 347.8 GHz." (3 ALMA Observations)
- continuum bandwidth: 7.7 GHz total effective bandwidth  
  > "the total effective bandwidth was 7.7 GHz" (3 ALMA Observations)
- arrays: 31 12-m antennas  
  > "31 12-meter antennas targeted this system" (3 ALMA Observations)
- configurations: _not stated_
- baselines: maximum baseline 650 m  
  > "The maximum array baseline reached 650 m" (3 ALMA Observations)
- angular resolution: 0.32"x0.41" at PA 96.3 deg  
  > "synthesized beam FWHM of 0$\ensuremath{''}$32$\times$0$\ensuremath{''}$41 at a position angle of 96.3$^{\circ}$" (3 ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: rms 0.074 mJy/beam  
  > "No detections are present above the background rms level of 0.074 mJy/beam" (3 ALMA Observations)
- time on source: 11.6 minutes  
  > "The total on-source integration time was 11.6 minutes" (3 ALMA Observations)
- observing dates: UT 2014 June 30  
  > "during Cycle 2 Early Science operations on UT 2014 June 30" (3 ALMA Observations)
- pi or archival as stated: _not stated_
- Line: CO J=3-2 (not stated)
- External data: Primary luminosity log L = -0.42 +/- 0.08 dex  
  > "using the luminosity of log $L$/$L_\mathrm{Bol}$ = –0.42 $\pm$ 0.08 dex from (cite: Bowler:2011gw)" (4 Results) [from (cite: Bowler:2011gw)]
- External data: Accretion rate 10^-10.8 Msun/yr  
  > "its accretion rate (10$^{-10.8}$ $M_{\odot}$ yr$^{-1}$; (cite: Zhou:2014ct))" (5 Discussion) [from (cite: Zhou:2014ct)]

## Processing

### Calibration

- pipeline or manual: not stated (CASA used for reduction)  
  > "The visibility data reduction and image reconstruction were carried out with `CASA` version 4.2.2." (3 ALMA Observations)
- casa version: CASA 4.2.2  
  > "carried out with `CASA` version 4.2.2" (3 ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
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
- continuum subtraction: No line detected; 346.0 GHz window averaged with continuum windows  
  > "No line emission was detected in the 346.0 GHz data so this window was incorporated with the continuum regions to create an averaged continuum image." (3 ALMA Observations)
- line free channels: _not stated_
- primary beam correction: divided by primary beam response  
  > "the continuum image was corrected for the non-uniform sensitivity across the field of view by dividing by the primary beam response." (3 ALMA Observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.32"x0.41", PA 96.3 deg  
  > "synthesized beam FWHM of 0$\ensuremath{''}$32$\times$0$\ensuremath{''}$41" (3 ALMA Observations)
- final rms: 0.074 mJy/beam in central 3.2"x3.2"  
  > "rms level of 0.074 mJy/beam as measured in the central 3$\ensuremath{''}$2$\times$3$\ensuremath{''}$2 region" (3 ALMA Observations)

### Inherited from earlier work

- Dust opacity law kappa = 10(nu/1e12 Hz) cm2/g  
  > "For consistency with previous work we use the frequency-dependent dust opacity relationship $\kappa_\nu$ = 10($\nu$/10$^{12}$ Hz) cm$^2$ g$^{-1}$ from (cite: Beckwith:1990hj)." (4 Results) [from (cite: Beckwith:1990hj)]
- Dust temperature-luminosity relation T=25 (L/Lsun)^1/4  
  > "Following (cite: Andrews:2013ku), we adopt the dust temperature-stellar luminosity relationship $T_C$ = 25 ($L$/$L_{\odot}$)$^{1/4}$" (4 Results) [from (cite: Andrews:2013ku)]
- Optically thin dust mass formula  
  > "a dust opacity ($\kappa_\nu$) following (cite: Hildebrand:1983tm)" (4 Results) [from (cite: Hildebrand:1983tm)]

### Not stated but needed to reproduce (our reading)

- Calibrator roles (bandpass, flux, phase) and flux scale/uncertainty
- Whether the archive pipeline or manual scripts were used
- tclean parameters: weighting/robust, cell and image size, deconvolver, threshold
- Channel selection for the continuum averaging
- Exact formula and Planck function treatment (e.g. CMB correction) for the dust mass

## Analysis recipe

1. **Image continuum and measure rms**: Average all four SPWs into a continuum image, correct for primary beam, measure rms in the central region and check for sources at A and B  
  > "this window was incorporated with the continuum regions to create an averaged continuum image." (3 ALMA Observations)
   - software: CASA
   - parameter: rms 0.074 mJy/beam; 3-sigma limit 0.22 mJy (point source)  
  > "implying a 3-$\sigma$ upper limit of 0.22 mJy (assuming a point source)" (4 Results)
   - fitting: _not stated_
   - validation: _not stated_
2. **Convert flux limit to dust and disk mass limits**: Optically thin isothermal dust mass from flux, distance, temperature and opacity; gas-to-dust 100  
  > "Assuming the continuum emission is optically thin, an upper limit on the dust mass ($M_\mathrm{dust}$) can be derived from our ALMA flux density constraint" (4 Results)
   - parameter: d = 145 pc; kappa(880 um) = 3.4 cm2/g  
  > "At 880 $\mu$m, the dust opacity $\kappa_\mathrm{880 \mu m}$ is 3.4 cm$^2$ g$^{-1}$." (4 Results)
   - assumption: T = 20 K for A; 10-20 K for B; gas-to-dust 100  
  > "We therefore assume a dust temperature between 10–20 K for GSC 6214-210 B" (4 Results)
   - fitting: _not stated_
   - validation: Sensitivity to temperature tested (5 K, 25 K)  
  > "dipping to 0.03 $\mbox{$M_{\ensuremath{\oplus}}$}$ (2.8 lunar masses) of dust for a slightly warmer temperature of 25 K" (4 Results)

## Software

- **CASA** 4.2.2: visibility data reduction and image reconstruction  
  > "The visibility data reduction and image reconstruction were carried out with `CASA` version 4.2.2." (3 ALMA Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Image rms | 0.074 | not stated | mJy/beam | 1 | no significant emission above the background level (0.074 mJy/beam rms) |
| 3-sigma flux upper limit | 0.22 | not stated | mJy | 1 | implying a 3-$\sigma$ upper limit of 0.22 mJy |
| Dust mass upper limit, B | <0.05-0.15 | not stated | Earth masses | 2 | $<$0.05–0.15 $\mbox{$M_{\ensuremath{\oplus}}$}$ (3.9–12.6 lunar masses) for the companion |
| Disk mass upper limit, A | <5 | not stated | Earth masses | 2 | putative disk masses of $<$5 $\mbox{$M_{\ensuremath{\oplus}}$}$ for GSC 6214-210 A |
| Remaining accretion time | ~3 | not stated | Myr | 2 | At most, accretion will continue for another $\sim$3 Myr |

## Qualitative findings

- GSC 6214-210 B's disk is low mass and lacks cold dust; giant planet formation has ceased around A.  
  > "Our deep 880 $\mu$m upper limit implies that GSC 6214-210 B’s disk has a low mass ($\lesssim$0.05 $M_\mathrm{Jup}$)" (5 Discussion)

## Claim tuples

- H: Does the accreting companion GSC 6214-210 B host a massive sub-mm-detectable disk? | E: ALMA Band 7 continuum, non-detection converted to mass limits | R: Dust <0.15 Earth masses, total <0.05 MJup | F: The disk is low mass; B is near the end of assembly | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Limits depend strongly on temperature and gas-to-dust ratio, so disk masses are approximate.  
  > "the total disk masses in this work are approximate at best." (4 Results)
- Caveat (inferred, ours): Non-detection only; mass limit depends on assumed temperature, opacity and gas-to-dust ratio
- Caveat (inferred, ours): Possible small optically thick disk is not excluded

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters and calibration details
- Data volume (inferred): ~10-30 GB
- Score (inferred): 3/5, Single short dataset and simple calculation, but imaging settings and calibration details are missing.
- Rediscovery candidate: no, Public status is not stated in the paper and imaging settings are missing.

## Links

- Companion: (cite: Kraus:2015fx) (ALMA detection of FW Tau C, a comparison case)

## Checks

```json
{
 "quotes": 43,
 "quotes_ok": 43,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 60,
  "stated": 32,
  "rate": 0.533
 },
 "evidence_ok": true
}
```

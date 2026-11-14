# SS433's Jet Trace from ALMA Imaging and Global Jet Watch Spectroscopy: Evidence for Post-launch Particle Acceleration

`2018ApJ...867L..25B` | The Astrophysical Journal Letters 2018 | first author: Blundell, Katherine M. | arXiv: 1811.00760 | DOI: 10.3847/2041-8213/aae890

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, stellar_physics
- Question: Does the jet trace predicted from Global Jet Watch optical Doppler spectroscopy match the ALMA 230 GHz synchrotron image (ballistic motion), and what is the magnetic-field structure along the jet from mm polarimetry?  
  > "This allows us to distinguish ballistic motion post-launch from deceleration (cite: Stirling2004)." (Introduction)
- Target **SS433**: coordinates _not stated_; z/distance 5.5 kpc  
  > "distance $d =
5.5$ kpc (cite: Blundell04; lockman2007)" (2 Optical spectroscopy and inference from Doppler shifts); distance from Blundell & Bowler 2004; Lockman et al. 2007  
  > "distance $d =
5.5$ kpc (cite: Blundell04; lockman2007)" (2 Optical spectroscopy and inference from Doppler shifts)

## Data provenance

- ALMA projects: 2013.1.01369.S
- bands: _not stated_
- frequencies and spectral setup: TDM, 7.5 GHz total, four 1.75-GHz spws at 224, 226, 240, 242 GHz, 64 channels each, full polarization  
  > "in four 1.75-GHz spectral windows (spw) centred at 224, 226, 240 and 242 GHz. Each spw was divided into 64 spectral channels" (3 Millimetre polarimetric imaging)
- continuum bandwidth: _not stated_
- arrays: 27 ALMA antennas  
  > "SS433 was observed using 27 ALMA antennas" (3 Millimetre polarimetric imaging)
- configurations: _not stated_
- baselines: 43 m to 2270 m  
  > "The longest and shortest baselines were 2270 and 43 m" (3 Millimetre polarimetric imaging)
- angular resolution: 0.19 x 0.16 arcsec2  
  > "The restoring beam has FWHM $0.19 \times 0.16$ arcsec$^2$." (3 Millimetre polarimetric imaging)
- max recoverable scale: ≲3.7 arcsec  
  > "sensitive to angular scales $\ensuremath{\lesssim} 3.7$ arcsec" (3 Millimetre polarimetric imaging)
- sensitivity: rms 13, 11, 12 µJy/beam in I, Q, U  
  > "The off-source rms levels are 13, 11 and 12 $\mu$Jy beam$^{-1}$ in $I$, $Q$ and $U$, respectively" (3 Millimetre polarimetric imaging)
- time on source: ≈2 hr  
  > "The total integration time on SS433 was $\approx$2 hr." (3 Millimetre polarimetric imaging)
- observing dates: 2015 September 28 21:26 to September 29 01:46 UT  
  > "SS433 was observed using 27 ALMA antennas between 2015 September 28 21:26 and September 29 01:46 UT." (3 Millimetre polarimetric imaging)
- pi or archival as stated: _not stated_
- Line: H-alpha (optical, Global Jet Watch) Balmer Hα moving lines (not stated)
- Other facility **Global Jet Watch**: Optical spectra (5800-8500 Å, R~4000) giving Hα redshift pairs and launch speeds in the year before ALMA  
  > "These were carried out with the multi-longitude Global Jet Watch telescopes each of which is equipped with an Aquila spectrograph" (2 Optical spectroscopy and inference from Doppler shifts)
- External data: Systemic velocity of SS433  
  > "according to its systemic velocity with respect to Earth (cite: lockman2007)" (2 Optical spectroscopy and inference from Doppler shifts) [from (cite: lockman2007)]
- External data: Rotation on the sky chi = 10 deg taken from Hjellming & Johnston  
  > "which was taken from (cite: Hjellming1981), not determined independently" (4 Comparison of time-extrapolated spectroscopy with ALMA imaging) [from (cite: Hjellming1981)]
- External data: Rotation measures ~119 and ~600 rad m^-2  
  > "(cite: Stirling2004) found a mean rotation measure (RM) of 119 rad m$^{-2}$ (excluding the core)" (5 B-field structure) [from (cite: Stirling2004)]
- External data: Knot expansion speed ≈0.015c from VLBI  
  > "expansion rate of the radio knots measured with VLBI ($\approx 0.015c$; (cite: Jeffrey2016))" (5 B-field structure) [from (cite: Jeffrey2016)]

## Processing

### Calibration

- pipeline or manual: Standard ALMA scripts in CASA  
  > "Initial data reduction followed standard ALMA scripts, executed in CASA (cite: Schnee2014)." (3 Millimetre polarimetric imaging)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1751+0939, 3.7275 Jy at 232.86 GHz, alpha = -0.441  
  > "The flux density of J1751+0939 during these observations was taken to be 3.7275 Jy at 232.86 GHz with a spectral index $\alpha = -$0.441" (3 Millimetre polarimetric imaging)
- flux scale uncertainty: about 10%  
  > "the total flux scale uncertainty is about 10%" (3 Millimetre polarimetric imaging)
- self calibration: Several clean+selfcal iterations; final amplitude and phase selfcal combining all four spws with 2 Taylor terms  
  > "The final iteration of amplitude and phase self-calibration was made by combining all four spectral windows using a model with two Taylor series terms." (3 Millimetre polarimetric imaging)

### Imaging

- task: _not stated_
- deconvolver: clean in multi-frequency synthesis mode (nterms=2)  
  > "Several iterations of clean in multi-frequency synthesis mode (cite: Rau) followed by self-calibration" (3 Millimetre polarimetric imaging)
- weighting robust: _not stated_
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
- final beam: 0.19 x 0.16 arcsec2  
  > "The restoring beam has FWHM $0.19 \times 0.16$ arcsec$^2$." (3 Millimetre polarimetric imaging)
- final rms: 13, 11, 12 µJy/beam (I, Q, U)  
  > "The off-source rms levels are 13, 11 and 12 $\mu$Jy beam$^{-1}$ in $I$, $Q$ and $U$" (3 Millimetre polarimetric imaging)

### Inherited from earlier work

- Polarization leakage calibration  
  > "Polarization leakage was calibrated as described by (cite: Nagai16)." (3 Millimetre polarimetric imaging) [from (cite: Nagai16)]
- Standard kinematic model  
  > "adopting the standard kinematic model (cite: Hjellming1981)" (2 Optical spectroscopy and inference from Doppler shifts) [from (cite: Hjellming1981)]
- Launch speed derivation from redshift pairs  
  > "derived the launch speed of each pair of bolides (cite: Blundell05)" (2 Optical spectroscopy and inference from Doppler shifts) [from (cite: Blundell05)]
- GJW spectra processing and calibration  
  > "processing and calibration of the spectroscopic data streams are described in (cite: Blundell2018)" (2 Optical spectroscopy and inference from Doppler shifts) [from (cite: Blundell2018)]

### Not stated but needed to reproduce (our reading)

- CLEAN weighting/robust, cell and image size, masks, iterations
- self-calibration solution intervals
- CASA version
- Global Jet Watch spectra (not public) and centroid measurements
- Source coordinates and the two positional offsets used
- Method for deriving polarised intensity, debiasing and fractional polarisation thresholds
- Pipeline calibrator for polarization angle

## Analysis recipe

1. **Predict jet trace from optical spectra**: Convert Hα blue/red centroid pairs to launch speeds, propagate ballistically with kinematic model to ALMA mid-epoch JD 2457294.4836  
  > "Assuming that the subsequent motion is ballistic (this assumption is discussed in Sec [4](#sec:ballistic)), and adopting the standard kinematic model (cite: Hjellming1981)" (2 Optical spectroscopy and inference from Doppler shifts)
   - parameter: cone angle 19 deg, i=79 deg, chi=10 deg, P=162.34 d, phi0=-0.241 rad, t_ref=2456000  
  > "cone angle $\theta = 19^\circ$ (Hjellming et al. use $\psi$), inclination $i = 79^\circ$, rotation on the sky $\chi = 10^\circ$" (2 Optical spectroscopy and inference from Doppler shifts)
   - assumption: ballistic motion; d = 5.5 kpc  
  > "distance $d =
5.5$ kpc (cite: Blundell04; lockman2007)" (2 Optical spectroscopy and inference from Doppler shifts)
   - fitting: Ejection phase fit to observed redshift pairs JD 2457000-2457293.5  
  > "The ejection phase was determined by fitting to the observed redshift pairs from JD 2457000 to JD 2457293.5." (2 Optical spectroscopy and inference from Doppler shifts)
   - validation: Overlay on ALMA image with 3 free parameters  
  > "There are only three free parameters in the superposition" (4 Comparison of time-extrapolated spectroscopy with ALMA imaging)
2. **Calibrate, self-calibrate and image ALMA I, Q, U**: Standard ALMA scripts in CASA, leakage calibration, MFS clean with selfcal  
  > "Several iterations of clean in multi-frequency synthesis mode (cite: Rau) followed by self-calibration were used to improve the imaging of SS433." (3 Millimetre polarimetric imaging)
   - software: CASA
   - fitting: _not stated_
   - validation: Off-source rms consistent with thermal noise  
  > "consistent with the expectations for thermal noise alone" (3 Millimetre polarimetric imaging)
3. **Check Faraday rotation and derive B-field direction**: Compare literature RMs scaled to 230 GHz and per-spw position angles at core; E-vectors taken orthogonal to B  
  > "the position angles measured for the individual spws at the location of the core (where we might expect maximum Faraday rotation) are consistent with the mean value for the band with an rms scatter of 1.0$^\circ$" (5 B-field structure)
   - assumption: Negligible Faraday rotation at 230 GHz  
  > "We therefore conclude that the position angles plotted in Fig. [3](#fig:fracpolvectors) are not significantly affected by Faraday rotation." (5 B-field structure)
   - fitting: _not stated_
   - validation: No systematic trend of PA with spw  
  > "Fig. [2](#fig:paplot) shows no systematic trend" (5 B-field structure)

## Software

- **CASA** : Data reduction, clean, self-calibration  
  > "Initial data reduction followed standard ALMA scripts, executed in CASA (cite: Schnee2014)." (3 Millimetre polarimetric imaging)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Peak flux density at 233 GHz | 86.0 | not stated | mJy/beam | 2 | The peak flux density at 233 GHz is 86.0 mJy/beam. |
| In-band spectral index of core | -0.29 | 0.14 | dimensionless | 2 | The in-band spectral index of the core is $-0.29 \pm 0.14$. |
| Fractional polarisation of nucleus | 0.011 | not stated | dimensionless | 3 | the nucleus of SS433 at 230 GHz is low ($p = 0.011$) |
| Radius of B-field transition | ≈0.35 (3e14 m) | not stated | arcsec | 3 | The transition in field direction at 0.35 arcsec ($3 \times
10^{14}$ m) |
| Off-ridgeline fractional polarisation | 0.6-0.7 | not stated | dimensionless | 3 | Our 230 GHz data show significantly higher fractional polarisation values (0.6 – 0.7) in these regions. |
| Per-spw PA scatter at core | 1.0 | not stated | deg | 3 | rms scatter of 1.0$^\circ$ |

## Qualitative findings

- Optical-spectroscopy jet trace matches ALMA image; no significant post-launch deceleration; 0.02c deceleration ruled out  
  > "We find no evidence for significant deceleration of the jet post-launch" (4 Comparison of time-extrapolated spectroscopy with ALMA imaging)

## Claim tuples

- H: Jet motion is ballistic post-launch | E: Overlay of trace predicted from GJW spectroscopy on ALMA 230 GHz image | R: Excellent agreement with 3 free parameters; 0.02c deceleration would give ≈0.3 arcsec offset, not seen | F: No significant deceleration | **supported**
- H: Faraday rotation is negligible at 230 GHz | E: Scaled literature RMs and per-spw PAs | R: Rotation ≤0.06 deg; PA scatter 1.0 deg, no trend | F: E-vectors orthogonal to B | **supported**
- H: B-field orientation changes along the jet where bolides interact | E: Polarisation vectors vs distance | R: Perpendicular within ≈0.35 arcsec, parallel to ridge beyond | F: Consistent with shocks/particle acceleration from colliding bolides, coincident with X-ray variability | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Mm wavelengths make Faraday rotation negligible so projected B-field is determined in a single observation  
  > "wide-band observations at mm wavelengths allow the projected field direction to be determined accurately in a single observation" (Introduction)
- Alternative: Deceleration of 0.02c suggested by Stirling et al. 2004 rejected  
  > "we can rule out a deceleration of 0.02$c$ just outside the launch location" (4 Comparison of time-extrapolated spectroscopy with ALMA imaging)
- How they decided it was enough: _not stated_
- Limitation (authors): Accurate position angles not measurable beyond 0.7 arcsec; 230 GHz trace not detectable far out  
  > "beyond which we cannot measure accurate position angles" (5 B-field structure)
- Caveat (inferred, ours): Shock-expansion argument is order-of-magnitude and uses an assumed expansion speed
- Caveat (inferred, ours): Visual overlay agreement not quantified statistically
- Caveat (inferred, ours): Single epoch; precession-dependent polarisation not tested
- Caveat (inferred, ours): Dependence on assumed distance

## Reproducibility

- Data public (paper): ALMA data identified by project code; GJW spectra not released  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.01369.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: GJW spectra and redshift-pair measurements
- Missing: clean parameters and selfcal details
- Missing: Polarisation analysis details
- Data volume (inferred): ~50-100 GB raw
- Score (inferred): 4/5, ALMA data public, but imaging parameters and optical data absent; trace comparison is qualitative.
- Rediscovery candidate: no, Optical spectra unavailable and imaging recipe incomplete; main results largely qualitative.

## Links

- Method: (cite: Nagai16) (Polarization leakage calibration)
- Method: (cite: Hjellming1981) (Kinematic model)
- Companion: (cite: Blundell2018) (GJW observatories and data processing)
- Companion: (cite: Lee2018) (Aquila spectrograph)
- Related: Global Jet Watch

## Checks

```json
{
 "quotes": 55,
 "quotes_ok": 55,
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
  "facts": 68,
  "stated": 43,
  "rate": 0.632
 },
 "evidence_ok": true
}
```

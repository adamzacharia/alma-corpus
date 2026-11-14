# Origin and Kinematics of the Eruptive Flow from XZ Tau Revealed by ALMA

`2015ApJ...811L...4Z` | The Astrophysical Journal Letters 2015 | first author: Zapata, Luis A. | arXiv: 1509.00316 | DOI: 10.1088/2041-8205/811/1/L4

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: What are the kinematics and origin of the eruptive bubble-like molecular flow from the multiple system XZ Tau, and which component drives it?  
  > "we present new, high angular resolution $^{12}$CO(1-0) line observations obtained with the *Atacama Large Millimeter/Submillimeter Array* (ALMA) toward the eruptive outflow from XZ Tau." (Introduction)
- Target **XZ Tau (A/B)**: coordinates not stated (phase center is the position of HL Tau: 04h31m38.426s, -18d13'57.04")  
  > "The binary system is separated by approximately 0.3$''$ (at a P.A. of 154$^\circ$), or 42 AU at a distance of 150 pc (cite: tor2009)." (Introduction); z/distance 150 pc  
  > "The binary system is separated by approximately 0.3$''$ (at a P.A. of 154$^\circ$), or 42 AU at a distance of 150 pc (cite: tor2009)." (Introduction); distance from Torres et al. 2009 (cite: tor2009)  
  > "The binary system is separated by approximately 0.3$''$ (at a P.A. of 154$^\circ$), or 42 AU at a distance of 150 pc (cite: tor2009)." (Introduction)

## Data provenance

- ALMA projects: 2011.0.00015.SV
- bands: 3 mm (12CO(1-0) at 115 GHz)  
  > "we present the resulting 3 mm continuum ALMA image of the XZ Tau." (Results and Discussion)
- frequencies and spectral setup: 12CO(1-0) at 115.27120 GHz; bandwidth 234375.0 kHz, 3840 channels, 61.035 kHz (0.15 km/s) channels, smoothed to 0.25 km/s  
  > "The spectral window to observe this line was configured with a total bandwidth of 234375.0 kHz and was divided into 3840 channels, providing a spectral channel resolution of 61.035 kHz or 0.15 km s$^{-1}$." (Observations)
- continuum bandwidth: _not stated_
- arrays: 12 m antennas only, 32-35 antennas  
  > "These observations only included antennas with diameters of 12 meters." (Observations)
- configurations: _not stated_
- baselines: 12 to 15,240 m  
  > "The independent baselines ranged in projected length from 12 to 15,240 m." (Observations)
- angular resolution: 0.98'' x 0.90'' (PA -8.66 deg) after tapering to ~1.0''  
  > "at an angular resolution 0.98$''$ $\times$ 0.90$''$ with a P.A. of $-$8.66$^\circ$." (Observations)
- max recoverable scale: _not stated_
- sensitivity: ~10 mJy/beam per velocity channel  
  > "The resulting r.m.s. noise for the line emission was about 10 mJy beam$^{-1}$ per velocity channel" (Observations)
- time on source: _not stated_
- observing dates: 2014 October and November  
  > "in 2014 October and November, during the ALMA science verification data program for the long baseline campaign." (Observations)
- pi or archival as stated: ALMA science verification data (long baseline campaign)  
  > "during the ALMA science verification data program for the long baseline campaign." (Observations)
- Line: 12CO J=1-0 (115.27120 GHz)
- Other facility **HST/ACS (FR656N)**: Archival optical narrow-band image of the eruptive outflow, used as reference  
  > "The HST/ACS (narrow band FR656N) image from XZ Tau was obtained from the HST archive and this is only used as a reference for the ALMA data." (Observations)
- External data: Cloud systemic LSR velocity ~6.8 km/s from 13CO  
  > "The systemic LSR velocity of the cloud where XZ Tau is located is $\sim$6.8 km s$^{-1}$ (as derived from the $^{13}$CO observations of Calvet et al, 1983" (Results and Discussion) [from Calvet et al. 1983 (ref: calvisie1983)]
- External data: Radial and transversal velocities of optical jet/bubbles used for the angle range  
  > "Using the determinations and respective errors for the radial and transversal velocities (cite: hir1997; kri2008) for the optical jet" (Results and Discussion) [from (cite: hir1997; kri2008)]

## Processing

### Calibration

- pipeline or manual: CASA used for calibration (details in cited ALMA Partnership papers)  
  > "The data were calibrated, imaged, and analyzed using the Common Astronomy Software Applications (CASA), see (cite: par2015; pare2015)." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0510+1800 (flux scale and bandpass); J0431+2037 gain  
  > "Observations of the quasar J0510$+$1800 provided the absolute scale for the flux density calibration, while the quasar J0431$+$2037 provided the gain calibration." (Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "We used a robust parameter of 0.5 in the CLEAN task" (Observations)
- uv taper: tapered to ~1.0'' resolution  
  > "the $^{12}$CO(1-0) data were tapered to a resolution of about 1.0$''$." (Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied to final continuum image  
  > "we corrected the final continuum image for the primary beam attenuation." (Observations)
- array combination: _not stated_
- smoothing: spectral resolution smoothed to 0.25 km/s  
  > "the spectral resolution in the data cube was smoothed to 0.25 km s$^{-1}$" (Observations)
- final beam: 0.98'' x 0.90'', PA -8.66 deg  
  > "at an angular resolution 0.98$''$ $\times$ 0.90$''$ with a P.A. of $-$8.66$^\circ$." (Observations)
- final rms: ~10 mJy/beam per channel  
  > "about 10 mJy beam$^{-1}$ per velocity channel" (Observations)

### Inherited from earlier work

- Calibration and imaging details and the 3.3 mm continuum are given in the ALMA Partnership papers  
  > "The continuum emission at 3.3 mm is presented and discussed in (cite: par2015)." (Results and Discussion) [from (cite: par2015; pare2015)]
- Outflow mass equation  
  > "we estimate the outflow mass using the following equation (cite: sco1986; palau2007)" (Results and Discussion) [from (cite: sco1986; palau2007)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration script details
- Clean mask, threshold, niter, cell and image size
- Continuum subtraction and line-free channels
- Outflow lobe sizes and integrated intensities used for the mass
- Procedure to derive the kinetic energy
- PV cut width and extraction details
- Flux scale uncertainty

## Analysis recipe

1. **Image the 12CO cube**: CLEAN with taper to ~1'' and robust 0.5, channels smoothed to 0.25 km/s  
  > "We used a robust parameter of 0.5 in the CLEAN task, in order to obtain a better signal-to-noise ratio" (Observations)
   - software: CASA
   - parameter: robust 0.5; taper ~1.0''  
  > "the $^{12}$CO(1-0) data were tapered to a resolution of about 1.0$''$." (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Moment and PV analysis of kinematics**: Moment 1 map from -2.25 to +11.75 km/s; PV cuts at PA 124 and 24 deg; moment 0 for blue (+0.75 to +4.5) and red (+8.25 to +10.75 km/s) lobes  
  > "We integrated LSR velocities from $+$0.75 to $+$4.5 km s$^{-1}$ for the blueshifted lobe, and from $+$8.25 to $+$10.75 km s$^{-1}$ for the redshifted one." (Results and Discussion)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Outflow mass, energy and dynamical age**: Optically thin LTE mass equation; dynamical age = size/velocity x tan(theta)  
  > "Assuming that the $^{12}$CO(1-0) line emission is optically thin and in Local Thermodynamic Equilibrium, we estimate the outflow mass using the following equation" (Results and Discussion)
   - parameter: Tex = 10 K; D = 150 pc; radial velocity 5 km/s; size 1''; angle 30 deg  
  > "Taking a radial velocity for the CO of 5 ${\,{\textnormal{km}}\,{\textnormal{s}}^{-1}}$" (Results and Discussion)
   - assumption: H2/CO abundance ~1e4; mean molecular weight 2.8; optically thin, LTE  
  > "where we used 2.8 as mean molecular weight, and X$_\frac{H_2}{CO}$ is the abundance ratio between the molecular hydrogen and the carbon monoxide ($\sim$$10^4$" (Results and Discussion)
   - fitting: _not stated_
   - validation: Compared dynamical age with the 34 yr age of the optical bubble  
  > "with the smaller value close to the estimated age of 34 years for the bubble by the time the ALMA data was taken." (Results and Discussion)

## Software

- **CASA** : Calibration, imaging and analysis  
  > "The data were calibrated, imaged, and analyzed using the Common Astronomy Software Applications (CASA)" (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Collimated outflow mass | 3e-7 | not stated | Msun | 3 | We then estimate a mass for the molecular collimated outflow powered by XZ Tau A of approximately 3 $\times$ $10^{-7}$ M$_\odot$. |
| Kinetic energy | 3e37 | not stated | erg | 3 | We also estimated a kinetic energy of 3 $\times$ 10$^{37}$ ergs. |
| Dynamical age range | 33-266 | not stated | yr | 3 | This implies an age estimate between 33 and 266 years |
| Velocity centroid of expanding structure | ~5.8 | not stated | km/s | 2 | The velocity centroid of the expanding structure is $\sim$5.8 km s$^{-1}$ |
| Jet position angle | ~20 | not stated | deg | 2 | The P.A. of the jet is approximately 20$^\circ$. |

## Qualitative findings

- CO shows a rotating and expanding structure with a SE-NW velocity gradient around XZ Tau  
  > "reveal a rotating and expanding structure with a southeast-northwest velocity gradient." (abstract)

## Claim tuples

- H: Which component drives the eruptive flow? | E: Mapped high-velocity 12CO(1-0) and compared with HST and the continuum positions | R: A compact collimated bipolar outflow emanates from XZ Tau A | F: XZ Tau A is the origin of the eruptive flow | **supported**
- H: What are the molecular kinematics of the flow? | E: Moment 1 map and PV cuts | R: Expansion at about +5 and +7 km/s and a SE-NW velocity gradient | F: The molecular structure is expanding and rotating | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Deeper observations are needed to refine the kinematic interpretation  
  > "Deeper observations are needed to refine our kinematic interpretation for this rotating and expanding structure." (Results and Discussion)
- Caveat (inferred, ours): Rotation inferred from a velocity gradient at ~1'' resolution, and could be a different outflow geometry
- Caveat (inferred, ours): Mass depends on assumed Tex=10 K, optical thinness and X=1e4, with no uncertainties given
- Caveat (inferred, ours): Inverted lobe orientations compared with the optical jet weaken the link to the bubbles

## Reproducibility

- Data public (paper): ALMA science verification data, project 2011.0.00015.SV  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA$\#$2011.0.00015.SV." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version
- Missing: clean parameters and masks
- Missing: lobe sizes and fluxes for the mass
- Data volume (inferred): Large long-baseline SV dataset (HL Tau campaign); tens to hundreds of GB raw
- Score (inferred): 3/5, Public SV data and simple analysis, but key imaging and measurement parameters are missing.
- Rediscovery candidate: no, Mass and lobe-measurement inputs are not given, so numeric results cannot be reproduced exactly.

## Links

- Method: ALMA Partnership et al. 2015 (cite: par2015; pare2015) (Describe the long baseline campaign data and calibration)
- Companion: Krist et al. 2008 (cite: kri2008) (HST image of the XZ Tau flow)
- Related: ALMA Science Verification long baseline campaign (HL Tau)

## Checks

```json
{
 "quotes": 46,
 "quotes_ok": 46,
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
  "facts": 63,
  "stated": 36,
  "rate": 0.571
 },
 "evidence_ok": true
}
```

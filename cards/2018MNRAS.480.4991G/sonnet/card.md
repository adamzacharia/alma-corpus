# ALMA imaging of the nascent planetary nebula IRAS 15103-5754

`2018MNRAS.480.4991G` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Gómez, José F. | arXiv: 1808.03681 | DOI: 10.1093/mnras/sty2193

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars
- Question: What are the morphology and kinematics of the circumstellar structure of the nascent PN IRAS 15103-5754, and what physical processes operate at the beginning of the PN phase?  
  > "Our aim is to study the morphology
and kinematics of the circumstellar structure, in order
to determine the physical processes taking place at the
beginning of the PN phase." (1 INTRODUCTION)
- Target **IRAS 15103-5754**: coordinates phase centre RA 15h14m17.94s, Dec -58d05m21.9s (ICRS)  
  > "R.A.(ICRS) = 15 [h] 14 [m] 17.94 [s], Dec(ICRS) = −58 [◦] 05 [′] 21.9 [′′]," (2 OBSERVATIONS AND DATA PROCESSING); "Assuming a
distance of 3.38 kpc (Vickers et al. 2015)" (3.1 Continuum emission); z/distance 3.38 kpc  
  > "R.A.(ICRS) = 15 [h] 14 [m] 17.94 [s], Dec(ICRS) = −58 [◦] 05 [′] 21.9 [′′]," (2 OBSERVATIONS AND DATA PROCESSING); "Assuming a
distance of 3.38 kpc (Vickers et al. 2015)" (3.1 Continuum emission); distance from Vickers et al. 2015 (SED fit assuming a total luminosity)  
  > "R.A.(ICRS) = 15 [h] 14 [m] 17.94 [s], Dec(ICRS) = −58 [◦] 05 [′] 21.9 [′′]," (2 OBSERVATIONS AND DATA PROCESSING); "Assuming a
distance of 3.38 kpc (Vickers et al. 2015)" (3.1 Continuum emission)

## Data provenance

- ALMA projects: 2015.1.00777.S
- bands: Band 6 (1.3 mm) and Band 7 (0.85 mm)  
  > "at
bands 6 (1.3 mm) and 7 (0.85 mm) in different sessions" (2 OBSERVATIONS AND DATA PROCESSING)
- frequencies and spectral setup: four spectral windows, dual linear polarization; windows of 1875 MHz (976.562 kHz channels) and 234.375 MHz (122.070 kHz channels)  
  > "with a spectral set-up comprising four spectral windows." (2 OBSERVATIONS AND DATA PROCESSING); "CO(2-1) 230.538 234.375 122.070 230.538" (Table 1)
- continuum bandwidth: _not stated_
- arrays: between 38 and 49 antennas depending on session  
  > "the array comprised between 38 and 49 antennas." (2 OBSERVATIONS AND DATA PROCESSING)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: synthesized beams ~0.2-0.3 arcsec  
  > "The synthesized beams of all images is ≃ 0.2 − 0.3
arcsec" (2 OBSERVATIONS AND DATA PROCESSING)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 50 and 35 uJy/beam at 0.85 and 1.3 mm  
  > "the rms of each map (50 and 35 µJy/beam at 0.85 and 1.3 mm, respectively)" (Figure 1 caption)
- time on source: _not stated_
- observing dates: 2016 March 14 to 2016 August 11 (Cycle 3)  
  > "between 2016 March 14 and 2016 August 11" (2 OBSERVATIONS AND DATA PROCESSING)
- pi or archival as stated: _not stated_
- Line: C18O 2-1 (219.560 GHz)
- Line: CO 2-1 (230.538 GHz)
- Line: CO 3-2 (345.796 GHz)
- Line: HCO+ 4-3 (356.734 GHz)
- Other facility **ATCA**: cm continuum position used as phase centre  
  > "the position reported by G´omez et al. (2015) for the radio
continuum emission in IRAS 15103-5754 from centimetre" (2 OBSERVATIONS AND DATA PROCESSING)
- Other facility **Mid-infrared image (Lagadec et al. 2011)**: 12.2 um [NeII] image compared with molecular structures  
  > "a mid-infrared image of the source (in the [Neii] filter centred at 12.2 µm,
Lagadec et al. 2011)" (3.4 Comparison of molecular structures with the
infrared nebula)
- External data: Distance 3.38 kpc  
  > "Assuming a
distance of 3.38 kpc (Vickers et al. 2015)" (3.1 Continuum emission) [from Vickers et al. 2015]
- External data: HCO+ abundance ~1e-7 relative to H2  
  > "≃ 10 [−][7], which is the main value obtained by
Schmidt & Ziurys (2016) in a sample of PNe" (3.3.2 A high-density outflow) [from Schmidt & Ziurys (2016)]
- External data: Dust mass absorption coefficient 0.294 cm2 g-1 at 1 mm  
  > "Assuming κ ν = 0.294 cm [2] g [−][1] at 1 mm (Draine 2003)" (3.1 Continuum emission) [from Draine 2003]
- External data: 12CO abundance 3e-4 and 16O/18O ~330  
  > "an
abundance of 12 C 16 O with respect to H 2 of 3 × 10 −4 (standard value of O-rich evolved stars, see, e.g., Teyssier et al.
2006)" (3.2 Line emission: an expanding torus) [from Teyssier et al. 2006; Wilson 1999]
- External data: HCO+ dipole moment and T1 from the line catalogue  
  > "T 1 = 4.280129 K and µ = 3.888 debye (Pickett et al. 1998)" (A1 Line emission) [from Pickett et al. 1998]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline  
  > "Data were calibrated using the ALMA pipeline, and
with versions 4.5.1 and 4.5.3 of the Common Astronomy
Software Applications (CASA) package." (2 OBSERVATIONS AND DATA PROCESSING)
- casa version: CASA 4.5.1 and 4.5.3 (calibration); 4.6.0 (processing and imaging)  
  > "Further processing
and imaging were carried out with version 4.6.0 of CASA." (2 OBSERVATIONS AND DATA PROCESSING)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1617-5848 and Titan (bandpass J1427-4206, gain J1524-5903)  
  > "The absolute
flux density scale was determined with sources J1617-5848
and Titan." (2 OBSERVATIONS AND DATA PROCESSING)
- flux scale uncertainty: _not stated_
- self calibration: phase and amplitude self-cal on continuum, applied to line data  
  > "Self-calibration was carried out
on the continuum data in both phase and amplitude, and
the corresponding gains were interpolated and applied to the
line data." (2 OBSERVATIONS AND DATA PROCESSING)

### Imaging

- task: clean in CASA, Briggs weighting  
  > "Images were obtained with a Briggs’ weighting and a robust parameter of
0.5 (as defined in task clean of casa)" (2 OBSERVATIONS AND DATA PROCESSING)
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "Briggs’ weighting and a robust parameter of
0.5" (2 OBSERVATIONS AND DATA PROCESSING)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum subtracted from visibilities before line imaging; continuum from line-free channels, MFS  
  > "Continuum emission was subtracted
from the visibilities before imaging the line emission." (2 OBSERVATIONS AND DATA PROCESSING)
- line free channels: _not stated_
- primary beam correction: all images primary-beam corrected  
  > "All images presented in this paper have
been corrected by the primary beam response." (2 OBSERVATIONS AND DATA PROCESSING)
- array combination: sessions combined into one measurement set per band  
  > "For each frequency band, data from different sessions were
combined into a single measurement set." (2 OBSERVATIONS AND DATA PROCESSING)
- smoothing: velocity resolution 1 km/s (1.34 km/s for C18O); images convolved to 0.33 arcsec for spectral index map  
  > "final data cubes with a velocity resolution of 1 km s [−][1], except for the C [18] O line, which was observed with a coarser
resolution of 1.34 km s [−][1]" (2 OBSERVATIONS AND DATA PROCESSING)
- final beam: 0.23x0.21 arcsec (0.85 mm), 0.32x0.27 arcsec (1.3 mm)  
  > "Synthesized
beams are 0.23 × 0.21 arcsec, p.a. = 62 [◦] (0.85 mm) and 0.32 × 0.27 arcsec, p.a. = 28 [◦] (1.3 mm)." (Figure 1 caption)
- final rms: 50 uJy/beam (0.85 mm), 35 uJy/beam (1.3 mm)  
  > "(50 and 35 µJy/beam at 0.85 and 1.3 mm, respectively)" (Figure 1 caption)

### Not stated but needed to reproduce (our reading)

- cell size and image size
- clean masks, threshold and number of iterations
- line-free channel ranges for continuum
- self-calibration solution intervals and number of iterations
- flux scale uncertainty
- uv-range/taper details beyond the 300 kilolambda cut
- free parameter values (density, HCO+ profile exponents) of the torus model
- fitting procedure used for the biconical model (done by eye?)
- method for deriving spectral-index uncertainty

## Analysis recipe

1. **Image continuum and measure source parameters**: MFS continuum images at 0.85 and 1.3 mm; elliptical Gaussian fits; baselines >300 klambda for compact sources  
  > "We tried to fit elliptical
Gaussians to the central part of the image (including
the two point sources and the extended emission around it)" (3.1 Continuum emission)
   - software: CASA
   - parameter: projected baselines >300 kilolambda for filtered images  
  > "Bottom panels: Same as the top panels,
but using only baselines - 300 kilolambda." (Figure 1 caption)
   - fitting: _not stated_
   - validation: _not stated_
2. **Spectral index and dust mass**: Spectral index from 0.85/1.3 mm ratio after convolving to 0.33 arcsec; dust mass of source B from optically thin emission  
  > "obtained from a ratio between the emission at 0.85 and 1.3

mm, after convolving both images to a common angular resolution of 0.33 arcsec." (3.1 Continuum emission)
   - assumption: kappa=0.294 cm2/g at 1 mm, Td=100 K, gas-to-dust 100, d=3.38 kpc  
  > "Assuming κ ν = 0.294 cm [2] g [−][1] at 1 mm (Draine 2003),
and a dust temperature of 100 K" (3.1 Continuum emission)
   - fitting: _not stated_
   - validation: _not stated_
3. **Torus geometry, kinematics and mass**: Integrated intensity maps and PV diagrams along major/minor axes; C18O LTE mass; HCO+ parameters  
  > "The estimated mass of the structure is 0.4-1.0 M ⊙ assuming local
thermodynamic equilibrium (LTE) with a temperature of
60-180 K" (3.2 Line emission: an expanding torus)
   - parameter: Tex 60-180 K; 12CO/H2 = 3e-4; 16O/18O ~330  
  > "a [16] O/ [18] O ratio of ≃ 330" (3.2 Line emission: an expanding torus)
   - assumption: LTE, optically thin C18O  
  > "Because the C [18] O(2-1) line is optically thinner, it can
provide a better estimate of the mass of the torus." (3.2 Line emission: an expanding torus)
   - fitting: _not stated_
   - validation: Parameters consistent within errors among all lines  
  > "the obtained geometric and kinematic parameters are consistent,
within the errors, for all observed lines." (3.2 Line emission: an expanding torus)
4. **Model HCO+ emission from expanding torus**: Radiative transfer model of an LTE expanding torus with power-law temperature (Appendix A), compared qualitatively with PV diagrams  
  > "We have modelled the HCO [+] emission from an expanding torus, as described in Appendix A." (3.2 Line emission: an expanding torus)
   - parameter: Tmax 180 K, Tmin 60 K, turbulence >~2 km/s, HCO+ abundance ~1e-7  
  > "for a torus with a maximum (inner) temperature of 180 K, and a minimum (outer) temperature of 60 K." (3.2 Line emission: an expanding torus)
   - fitting: No detailed fit; first-order approximation only  
  > "Therefore we did not attempt any detailed fit
to the data, other than a first-order approximation to the
temperatures in the torus." (3.2 Line emission: an expanding torus)
   - validation: Model PV diagrams visually compared to observed ones  
  > "the resulting positionvelocity diagrams (Fig. 5) reasonably resemble the observed
ones (Fig. 4)" (3.2 Line emission: an expanding torus)
5. **CO and HCO+ outflow masses**: LTE optically thin CO(2-1) and (3-2) for high-velocity gas (>30 km/s); HCO+ outflow mass assuming abundance 1e-7  
  > "Assuming LTE and optically thin emission in both CO
transitions for the high-velocity gas, we obtain a total mass
of 0.03 − 0.10 M ⊙ for the outflow" (3.3.1 A biconical outflow)
   - assumption: Tex 60-180 K  
  > "assuming excitation temperatures 60-180 K" (3.3.2 A high-density outflow)
   - fitting: _not stated_
   - validation: Could not obtain consistent Tex from CO(3-2)/CO(2-1), suggesting non-LTE  
  > "We could not obtain consistent values of
excitation temperatures from the ratio CO(3-2)/CO(2-1) at
different velocities" (3.3.1 A biconical outflow)
6. **Biconical outflow kinematic model**: Analytic PV relation for the walls of truncated cones with linear velocity gradient and equatorial velocity V0 (Appendix C), matched to the PV diagram along p.a.=36 deg  
  > "We have modelled the outflow geometry and kinematics
as arising from the walls of a biconical structure, in order
to reproduce the position-velocity diagram in Fig. 7." (3.3.1 A biconical outflow)
   - parameter: theta~106 deg, half-opening theta0~28 deg, dv/dr=73 km/s/arcsec, v0~23 km/s  
  > "θ ≃ 106 [◦], a half opening angle θ 0 ≃ 28 [◦], a velocity
gradient � dvdr � = 73 km s [−][1] arcsec [−][1] and v 0 ≃ 23 km s [−][1]" (APPENDIX C)
   - assumption: explosive event with ballistic particles; d=3.38 kpc  
  > "The conical outflow model assumes an explosive
event with particles having ballistic trajectories." (APPENDIX C)
   - fitting: _not stated_
   - validation: Model lines overlaid on observed PV diagram; more complex cone variants tested and rejected  
  > "None
of these spatial changes led to a PV diagram in agreement
with the data." (APPENDIX C)

## Software

- **CASA** 4.5.1, 4.5.3 (calibration); 4.6.0 (imaging): Calibration, imaging (clean), self-calibration and continuum subtraction  
  > "Further processing
and imaging were carried out with version 4.6.0 of CASA." (2 OBSERVATIONS AND DATA PROCESSING)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Separation of continuum sources A and B | 0.39 | 0.03 | arcsec | 1 | separated by 0.39 ± 0.03 arcsec |
| Total continuum flux density at 0.85 mm | 161.9 | 1.1 | mJy | 1 | The total flux densities are 161.9 ± 1.1
and 71.3 ± 0.5 mJy, respectively. |
| Total continuum flux density at 1.3 mm | 71.3 | 0.5 | mJy | 1 | The total flux densities are 161.9 ± 1.1
and 71.3 ± 0.5 mJy, respectively. |
| Spectral index of whole emission | 1.835 | 0.021 | dimensionless | 2 | we estimated a spectral index
α (defined as S ν ∝ ν [α] ) of 1.835 ± 0.021. |
| Spectral index of source A | 0.97 | 0.04 | dimensionless | 2 | 77.8 ± 1.2 50.46 ± 0.16 0.97 ± 0.04 |
| Spectral index of source B | 4.1 | 0.4 | dimensionless | 2 | The emission from
source B has a spectral index of 4.1 ± 0.4 |
| Dust mass of source B | 2.5e-3 | not stated | Msun | 2 | we estimate a dust mass
M d = 2.5 × 10 [−][3] M ⊙ for source B. |
| Torus mass (C18O, LTE) | 0.4-1.0 | not stated | Msun | 3 | The estimated mass of the structure is 0.4-1.0 M ⊙ |
| Torus expansion velocity (deprojected) | 23 | not stated | km/s | 3 | we obtain a deprojected expansion velocity of 23 km s [−][1] |
| Torus mean diameter | 0.6 (2000 au) | not stated | arcsec | 3 | We obtain a torus mean diameter of ≃ 0.6 arcsec (2000 au at 3.38 kpc) |
| Torus dynamical age | 200 | not stated | yr | 3 | we estimate a dynamical age
of 200 yr for the expanding torus. |
| CO high-velocity outflow mass | 0.03-0.10 | not stated | Msun | 5 | we obtain a total mass
of 0.03 − 0.10 M ⊙ for the outflow |
| HCO+ outflow mass | 0.02-0.04 | not stated | Msun | 5 | We obtain an estimate of 0.02-0.04
M ⊙ for the HCO [+] outflow |
| Cone opening angle (2 theta0) | 56 | not stated | deg | 6 | an opening angle of the cone
(2 × θ 0 ) of ≃ 56 [◦] |
| Misalignment of cone axis with torus axis | 14 | not stated | deg | 6 | so the total 3-D misalignment is ≃ 14 [◦] |
| Maximum deprojected outflow velocity | 250 | not stated | km/s | 6 | we
estimate a maximum deprojected outflow velocity of ≃ 250
km s [−][1] |
| Velocity gradient along cone | 73 | not stated | km/s/arcsec | 6 | The velocity gradient along the conical surface is 73
km s [−][1] arcsec [−][1] |
| Outflow dynamical age | 220 | not stated | yr | 6 | This gradient indicates a dynamical age
of ≃ 220 yr for the outflow. |

## Qualitative findings

- Brighter continuum source A has substantial free-free emission (spectral index down to 0.6), confirming PN nature; source B is dust emission  
  > "it seems that a significant fraction of the
observed emission in IRAS 15103-5754 arises from free-free

processes in ionized gas." (3.1 Continuum emission)
- Biconical CO outflow has central velocity ~-41 km/s, offset from the torus (-33 km/s)  
  > "a velocity for the former of ≃−41 km s [−][1] is required to reproduce the observed diagrams." (3.3.1 A biconical outflow)

## Claim tuples

- H: Does the continuum emission arise from dust only? | E: Two-band continuum imaging and spectral index map | R: Spectral index of 1.835 overall, down to 0.6 near source A | F: Significant free-free emission from ionized gas; confirms PN nature | **supported**
- H: Is the molecular gas dominated by an expanding torus? | E: C18O, HCO+, CO PV diagrams and maps; torus model | R: Torus diameter 0.6 arcsec, vexp 23 km/s, mass 0.4-1 Msun | F: Expanding torus, with a ~200 yr dynamical age | **supported**
- H: Do high-velocity outflows exist and what is their geometry? | E: CO and HCO+ high-velocity maps; biconical kinematic model | R: Biconical CO outflow up to 250 km/s, misaligned by 14 deg; separate HCO+ outflow perpendicular to the torus | F: At least two outflows with different axes | **supported**
- H: What formation scenario explains the system? | E: Comparison of geometry and kinematics with expectations of triple-system common envelope scenario | R: Misaligned axes and velocity offset | F: Proposed triple system with an ejected component and a subsequent wind stripping the torus | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: HCO+ used for torus modelling because of higher S/N than C18O and less contamination from high-velocity gas than CO  
  > "we
have used the HCO [+] images and PV diagrams, as they have
a higher S/N ratio than the C [18] O images" (3.2 Line emission: an expanding torus)
- Alternative: Contracting torus ruled out by asymmetry in optically thick lines; truncated/separated cones without V0 rejected  
  > "We can rule out
contracting motions, given the observed asymmetry in the
optically thicker lines" (3.2 Line emission: an expanding torus)
- How they decided it was enough: _not stated_
- Limitation (authors): Mass and mass-loss estimates are very uncertain; distance is a single uncertain literature estimate  
  > "our estimates of mass and mass-loss rate are very uncertain, as they
depend on several parameters that are not well constrained" (3.1 Continuum emission)
- Limitation (authors): Torus model too simple for close reproduction; no detailed fit  
  > "Our model of HCO [+] emission is only intended as an
illustration of the general geometric characteristics of the
torus" (3.2 Line emission: an expanding torus)
- Caveat (inferred, ours): Models are compared by eye with no quantitative goodness of fit or parameter uncertainties (e.g. cone parameters).
- Caveat (inferred, ours): Distance of 3.38 kpc is poorly constrained and propagates to all masses and sizes.
- Caveat (inferred, ours): Triple-system scenario is speculative.
- Caveat (inferred, ours): CO atmospheric-calibration artefacts affect some channels.

## Reproducibility

- Data public (paper): Project code given in acknowledgements; data not explicitly stated to be public  
  > "This paper makes use of the following ALMA data:
ADS/JAO.ALMA#2015.1.00777.S." (ACKNOWLEDGEMENTS)
- Products in archive: _not stated_
- Missing: image/cell sizes, clean masks and thresholds
- Missing: self-calibration parameters
- Missing: torus and cone model code and full parameter set
- Missing: exact channel selection and uv-range choices for flux estimates
- Data volume (inferred): Hundreds of GB for multi-session Band 6 and 7 cubes (raw); tens of GB after calibration
- Score (inferred): 3/5, Data and processing basics are given (CASA, robust 0.5, lines), but many imaging and self-cal parameters are missing and the models are by-eye.
- Rediscovery candidate: no, Key numbers derive from by-eye model matching and missing imaging parameters, although the continuum numbers could be partly redone.

## Links

- Companion: Gómez et al. (2015) (Earlier Herschel/VLT/ATCA study establishing PN nature and radio properties)
- Companion: Gómez et al. in preparation (Updated ATCA position)

## Checks

```json
{
 "quotes": 88,
 "quotes_ok": 88,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 18,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 56,
  "rate": 0.683
 },
 "evidence_ok": true
}
```

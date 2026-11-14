# ALMA resolves the remarkable molecular jet and rotating wind in the extremely radio-quiet galaxy NGC 1377

`2020A&A...640A.104A` | Astronomy and Astrophysics 2020 | first author: Aalto, S. | arXiv: 2007.07824 | DOI: 10.1051/0004-6361/202038282

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: What are the structure, kinematics, physical conditions and driving mechanisms of the molecular jet and wind in the extremely radio-quiet galaxy NGC 1377, and what is the nature of its nuclear power source?  
  > "the nature of the power source behind the molecular outflow, and the FIR luminosity, is still not fully understood." (Introduction)
- Target **NGC 1377**: coordinates R.A.=03h36m39.074, Dec.=-20d54m07.0553 (ICRS) (phase centre)  
  > "NGC 1377 is a nearby (21 Mpc (1$''$=102 pc)) lenticular galaxy" (Introduction); "The phase centre was set to R.A.=03h36m39.074, Dec.=$-$20d54m07.0553 (ICRS)." (2 Observations); z/distance 21 Mpc (1''=102 pc)  
  > "NGC 1377 is a nearby (21 Mpc (1$''$=102 pc)) lenticular galaxy" (Introduction); "The phase centre was set to R.A.=03h36m39.074, Dec.=$-$20d54m07.0553 (ICRS)." (2 Observations); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00900.S, 2017.1.0659.S
- bands: Band 7 (345 GHz), CO 3-2 tuning  
  > "Here we present new ALMA observations, with the same spectral tuning but with more extended array configurations, taken in November 2017." (2 Observations)
- frequencies and spectral setup: Four 1.875 GHz-wide spectral windows centred at 342.2, 343.8, 354.7 and 356.1 GHz, native channel spacing ~2 MHz  
  > "The correlator was set up with four 1.875 GHz-wide spectral windows centred at 342.2, 343.8 (covering the CO $J$=3–2 line, rest frequency 345.79599 GHz)" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 2017: 113 m-13.9 km and 92 m-8.5 km; 2014: 31 m-1.1 km  
  > "| 12 Nov 2017 $^{(a2)}$ | 45 | $\sim$0.6 | 50 | 113 / 13.9 |" (Table 1)
- angular resolution: 0.030 x 0.022 arcsec (3 x 2.2 pc), PA=59 deg  
  > "The synthesised beam is $0.\mbox{$''$}030 \, \times \, 0.\mbox{$''$}022$ (3$\times$2.2 pc for NGC 1377) with position angle PA=59$^{\circ}$." (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: 0.36 mJy/beam per 10 km/s channel; continuum rms 30 uJy  
  > "the resulting data has a sensitivity of 0.36 mJy per beam in a 10 ${\rm km\,s}^{-1}$ (12 MHz) channel width." (2 Observations)
- time on source: 50 min each for 12 and 21 Nov 2017  
  > "| 21 Nov 2017 $^{(a2)}$ | 47 | 0.4–0.6 | 50 | 92 / 8.5 |" (Table 1)
- observing dates: 12 and 21 Nov 2017 (plus 12 Aug 2014 lower-resolution data)  
  > "| 12 Aug 2014 $^{(a1)}$ | 33 | $\sim$0.5 | 30 | 31 / 1.1 |" (Table 1)
- pi or archival as stated: _not stated_
- Line: CO J=3-2 (345.79599 GHz)
- Line: HCO+ J=4-3 (356.73422 GHz)
- Line: HCN (vib. excited) J=4-3 v2=1f (356.25557 GHz)
- Other facility **HST**: H-band image used to estimate stellar mass within 100 pc  
  > "The mass of the stars inside $r$=100 pc is estimated to $2 \times 10^8$ M$_{\odot}$ from an HST H-band image (HST program GO14728, J Gallagher PI)." (Table 1)
- External data: Previous 0.25x0.18 arcsec CO 3-2 data (2014), jet mass 2.3e7 Msun with Galactic X(CO), 345 GHz continuum flux 2.2 mJy  
  > "the molecular mass in the jet is estimated to $2.3 \times 10^7$ M$_{\odot}$ (cite: aalto16)" (6.1 Molecular masses) [from (cite: aalto16)]
- External data: Radio observations used to bound synchrotron and free-free contribution to 0.8 mm continuum  
  > "Based on the radio observations of (cite: costagliola16), we estimate an upper limit to the contribution from synchrotron and free-free emission to the 0.8 mm continuum of 3% and 6% respectively." (3.6 Continuum) [from (cite: costagliola16)]
- External data: Stellar velocity dispersion 83 km/s  
  > "with stellar velocity dispersion $\sigma$=83 ${\rm km\,s}^{-1}$ (cite: aalto12b)" (5.2 Indications of inflowing gas) [from (cite: aalto12b)]

## Processing

### Calibration

- pipeline or manual: Calibrated in CASA, then imported into AIPS for imaging  
  > "After calibration within the CASA reduction package, the visibility set was imported into the AIPS package for further imaging." (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0522-3627 (2017); J0334-401 (2014)  
  > "| 12 Nov 2017 $^{(a2)}$ | 45 | $\sim$0.6 | 50 | 113 / 13.9 | J 0522$-$3627 | J 0522$-$3627 ($4.81 \pm 0.23$) | J 0340$-$2119 |" (Table 1)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: AIPS imaging  
  > "the visibility set was imported into the AIPS package for further imaging." (2 Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "With Briggs weighting (parameter robust set to 0.5)" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum image from all line-free channels merged  
  > "We merged all line-free channels in our observations into a 0.8 mm continuum image (Fig. [7](#f:cont)) with an rms of 30 $\mu$Jy." (3.6 Continuum)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Smoothed to two-channel resolution before moments; clipped at 3 sigma (moment 0), 4 sigma (moments 1, 2)  
  > "We smoothed to two channel resolution, then for the moment 0 map we clipped at the 3$\sigma$ level, and for the moment 1 and 2 maps we clipped at 4$\sigma$." (3.2 CO 3–2 moment maps)
- final beam: 0.030 x 0.022 arcsec, PA 59 deg  
  > "The synthesised beam is $0.\mbox{$''$}030 \, \times \, 0.\mbox{$''$}022$" (2 Observations)
- final rms: 0.36 mJy/beam per 10 km/s channel  
  > "the resulting data has a sensitivity of 0.36 mJy per beam in a 10 ${\rm km\,s}^{-1}$ (12 MHz) channel width." (2 Observations)

### Inherited from earlier work

- Same spectral tuning as earlier 2014 observations  
  > "Here we present new ALMA observations, with the same spectral tuning but with more extended array configurations" (2 Observations) [from (cite: aalto16)]
- Luminosity of nuclear dust structure estimated with same method  
  > "To estimate the luminosity of the nuclear dust structure we adopt the same method as (cite: aalto17)." (5.3 Accretion luminosity or compact star formation) [from (cite: aalto17)]
- Dust column density formalism  
  > "Using the formalism of (cite: keene82) $N$(H + H$_2$)/$\tau_{\lambda}$=$1.2 \times 10^{25}(\lambda/400 \mu{\rm m})^2$ $\rm {cm^{-2}}$" (5.1 Nuclear morphology, dynamics, and enclosed mass) [from (cite: keene82)]
- Lower X(CO) factor (Galactic overestimates turbulent gas mass by ~5)  
  > "(cite: aalto15a) found that a Galactic X(CO) overestimates the mass in turbulent outflowing gas by a factor $\sim$5." (6.1 Molecular masses) [from (cite: aalto15a)]
- Jet launch radius via equation (5) of Anderson et al.  
  > "The launch region of an MHD jet can be estimated using the formalism of (cite: anderson03)." (7.3 Jet driving mechanism) [from (cite: anderson03)]

### Not stated but needed to reproduce (our reading)

- CASA version and whether the pipeline or manual scripts were used
- AIPS task names, cell size, image size, masking and deconvolver
- Self-calibration details
- Line-free channels used for the continuum
- How the 2014 and 2017 data were handled in the final image (2017 only apparently)
- Moment-map rms values used for clipping
- Detailed jet precession model and rotating wind model parameters
- Method for the dynamical mass fit (velocity, radius, inclination)
- Details of the jet and wind mass derivation (CO luminosity, line ratios, X(CO) value)

## Analysis recipe

1. **Calibrate and image visibilities**: Calibration in CASA, imaging in AIPS with Briggs weighting  
  > "After calibration within the CASA reduction package, the visibility set was imported into the AIPS package for further imaging." (2 Observations)
   - software: CASA, AIPS
   - parameter: robust = 0.5  
  > "With Briggs weighting (parameter robust set to 0.5)" (2 Observations)
   - fitting: _not stated_
   - validation: Recovered ~60% of flux of earlier lower-resolution CO 3-2 map  
  > "In the high resolution data we recover $\sim$60% of the emission in the previous, $0.\mbox{$''$}25 \times 0.\mbox{$''$}18$ resolution CO 3–2 map" (3.2 CO 3–2 moment maps)
2. **Make moment maps and continuum image**: Flux-weighted moments 0,1,2 per pixel; continuum from line-free channels with 2D Gaussian fit  
  > "The velocity centroids were determined through a flux-weighted first moment of the spectrum of each pixel, therefore assigning one velocity to a spectral structure." (3.2 CO 3–2 moment maps)
   - parameter: clipping 3 sigma (mom0), 4 sigma (mom1,2); smoothing to two channels  
  > "for the moment 0 map we clipped at the 3$\sigma$ level, and for the moment 1 and 2 maps we clipped at 4$\sigma$" (3.2 CO 3–2 moment maps)
   - fitting: Two-dimensional Gaussian fit to continuum  
  > "A two-dimensional Gaussian fit gives a FWHM size of $4.1 \times 2$ pc and a position angle PA=90$\pm 5^{\circ}$." (3.6 Continuum)
   - validation: _not stated_
3. **Derive gas and dust temperature, column density and luminosity of nucleus**: CO 3-2 brightness temperature as lower limit to Tk; assume Td~Tk; optical depth from Tb/Td; column from Keene et al. formalism; luminosity of spherical dust structure  
  > "For $T_{\rm d}$=180 K the dust opacity at $\lambda$=0.8 mm is $\tau$$\simeq$0.04." (5.1 Nuclear morphology, dynamics, and enclosed mass)
   - parameter: Td=180 K, r=1.5 pc  
  > "Fitting the luminosity to a simple spherical dust structure with the average radius of $r$=1.5 pc and $T_{\rm d}$=180 K" (5.3 Accretion luminosity or compact star formation)
   - assumption: Dust and gas coupled (Td~Tk) because n>1e4 cm-3 from HCO+ detection  
  > "We can therefore assume that $T_{\rm d}$$\sim$$T_{\rm k}$ and that $T_{\rm d}>$100 K in the central region" (4.1 Gas and dust temperatures)
   - fitting: _not stated_
   - validation: _not stated_
4. **Estimate dynamical (SMBH) mass from nuclear high-velocity gas**: Keplerian rotation of high-velocity gas at +-160 km/s with offset 0.028 arcsec, inclination >~60 deg  
  > "The high resolution 0.8 mm continuum implies a nuclear inclination $i{_>\atop{^\sim}}$60$^{\circ}$ suggesting a dynamical mass $M_{\rm dyn}$ of $0.9 \times 10^7$ M$_{\odot}$." (5.1 Nuclear morphology, dynamics, and enclosed mass)
   - assumption: Keplerian rotation; inclination uncertain due to warp  
  > "The nuclear high-velocity gas appears to be in Keplerian rotation with a PA of 100$^{\circ}$" (5.1 Nuclear morphology, dynamics, and enclosed mass)
   - fitting: _not stated_
   - validation: _not stated_
5. **Derive masses, outflow velocities, energetics and momentum flux of jet and wind**: Masses with reduced X(CO) for turbulent gas; precessing jet model for jet velocity; kinetic energy K=0.5M(v^2+sigma^2), gravitational W=GM^2/r  
  > "The kinetic energy is $K$$\simeq$$\frac{1}{2}M(v^2+ \sigma^2)$ where $M$ is the mass of the component" (Table 1)
   - parameter: narrow wind inclination i=70 deg; precession angle ~15 deg  
  > "Assuming an average inclination $i$=70$^{\circ}$ of the launch region, the $v_{\rm out}$ of the narrow wind is 90$\pm 30$ ${\rm km\,s}^{-1}$" (6.2 Outflow velocities)
   - assumption: X(CO) lower by ~5 than Galactic for turbulent gas  
  > "Applying this factor, we instead find a jet gas-mass of $M_{\rm jet}$$\simeq$$5 \times 10^6$ M$_{\odot}$" (6.1 Molecular masses)
   - fitting: _not stated_
   - validation: _not stated_
6. **Model rotating magneto-centrifugal wind and estimate jet launch radius**: Illustrative wind model with v_out = a v_K (a=1); jet launch radius from Anderson et al. eq. 5  
  > "In our model we have selected $a$ to be unity" (7.1.1 An illustrative model)
   - parameter: v_out~600 km/s, r_jet~3 pc, rotation 60 km/s, M=9e6 Msun gives r_launch~0.4 pc  
  > "yields a launch radius for the molecular jet of $r_{\rm launch}$$\sim$0.4 pc" (7.3 Jet driving mechanism)
   - fitting: _not stated_
   - validation: Qualitative comparison with moment maps and channel maps  
  > "However, it’s structure can be compared to the inner part of the narrow wind." (7.1.1 An illustrative model)

## Software

- **CASA** : Calibration of the ALMA data  
  > "After calibration within the CASA reduction package" (2 Observations)
- **AIPS** : Imaging of visibility data  
  > "the visibility set was imported into the AIPS package for further imaging." (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Synthesised beam | 0.030 x 0.022, PA=59 | not stated | arcsec, deg | 1 | The synthesised beam is $0.\mbox{$''$}030 \, \times \, 0.\mbox{$''$}022$ |
| 0.8 mm continuum peak | 0.41 | 0.02 | mJy/beam | 2 | 0.41$\pm$0.02 mJy beam$^{-1}$ peak ($T_{\rm B}$=5 K) and 1.3$\pm$0.1 mJy integrated |
| 0.8 mm continuum integrated flux | 1.3 | 0.1 | mJy | 2 | 0.41$\pm$0.02 mJy beam$^{-1}$ peak ($T_{\rm B}$=5 K) and 1.3$\pm$0.1 mJy integrated |
| Continuum FWHM size | 4.1 x 2 | PA=90+-5 deg | pc | 2 | A two-dimensional Gaussian fit gives a FWHM size of $4.1 \times 2$ pc |
| Maximum CO 3-2 brightness temperature | 180 | not stated | K | 3 | The maximum $T_{\rm B}$(CO 3–2)=180 K is found at a velocity $v$=1700 |
| Nuclear column density N(H+H2) | 1.8e24 | upper limit if Td>180 K | cm^-2 | 3 | we find a $N$(H + H$_2$)$\simeq$$1.8 \times 10^{24}$ $\rm {cm^{-2}}$ |
| Dynamical mass in nucleus (r=1.4 pc) | 9e6 | +2/-3 e6 | Msun | 4 | which results in $M_{\rm dyn}$=$9^{+2}_{-3} \times 10^6$ M$_{\odot}$ |
| Nuclear core luminosity | 4.8e9 | not stated | Lsun | 3 | results in $L_{\rm core}$$\simeq$$4.8 \times 10^9$ L$_{\odot}$ |
| Eddington ratio | ~2% | not stated | percent | 3 | the growth of the NGC 1377 black hole would occurs at a rate of $\sim$2% Eddington |
| Jet gas mass | 5e6 | not stated | Msun | 5 | we instead find a jet gas-mass of $M_{\rm jet}$$\simeq$$5 \times 10^6$ M$_{\odot}$ |
| Narrow wind outflow velocity | 90 | 30 | km/s | 5 | the $v_{\rm out}$ of the narrow wind is 90$\pm 30$ ${\rm km\,s}^{-1}$ |
| Jet outflow velocity | ~600 | 60 | km/s | 5 | A $\theta_{\rm p}$=15$^{\circ}$ implies a jet $v_{\rm out}$ of $\sim$600 ${\rm km\,s}^{-1}$ ($\pm$60 ${\rm km\,s}^{-1}$ |
| Precession angle | ~15 | not stated | deg | 5 | gives $\theta_{\rm p}$$\simeq$15$^{\circ}$ |
| Jet momentum flux | ~37 | not stated | L/c | 5 | An estimate of the momentum flux of the jet (${\dot M}v$) is $\sim$$37L/c$ |
| Jet launch radius | ~0.4 | not stated | pc | 6 | yields a launch radius for the molecular jet of $r_{\rm launch}$$\sim$0.4 pc |
| Systemic velocity | 1730 | not stated | km/s | 2 | Here we find a $v_{\rm sys}$=1730 ${\rm km\,s}^{-1}$ of the nuclear rotation |

## Qualitative findings

- Narrow wind shows east-west velocity shift consistent with rotation, suggesting a rotating magneto-centrifugal disk-wind  
  > "The narrow wind shows an east-west velocity shift (Sec. [3.3.3](#s:narrow)) which is consistent with the rotation of the nuclear disk." (7.1 Driving mechanism of the narrow wind)
- Tentative evidence of inflowing gas from double-peaked CO and HCO+ spectra with redshifted absorption  
  > "It may indicate that lower excitation foreground gas is moving in towards the centre of NGC 1377" (5.2 Indications of inflowing gas)

## Claim tuples

- H: Is the nuclear power source of NGC 1377 an embedded starburst or an accreting SMBH? | E: Estimated nuclear dust luminosity, column and compactness from 0.8 mm continuum and CO | R: L_core~4.8e9 Lsun inside r=1.5 pc, N~1.8e24 cm-2; a starburst would need r<0.6 pc | F: Accretion onto a dust-enshrouded SMBH is favoured | **partially**
- H: Is the narrow wind a rotating disk-wind? | E: Resolved velocity structure of wind in channel/moment maps compared to simple model | R: East-west velocity shifts of +-110 to 160 km/s in the wind | F: Narrow wind is a magneto-centrifugal wind primarily direct-driven | **supported**
- H: What drives the molecular jet? | E: Energetics, momentum flux and launch radius estimates | R: Momentum flux ~37 L/c; jet kinetic and gravitational energy in rough equipartition | F: Jet proposed as gravitationally powered magneto-centrifugal wind; entrainment by weak jet not excluded | **partially**
- H: Is the SMBH massive relative to host properties? | E: Dynamical mass of nuclear rotation | R: M_dyn=9+2-3 e6 Msun | F: SMBH is over-massive relative to M-sigma | **supported**

## Reasoning

- Why this data: Higher resolution needed to resolve jet and wind structure and nucleus  
  > "Here we present new ALMA observations, with the same spectral tuning but with more extended array configurations" (2 Observations)
- Why this method: _not stated_
- Alternative: Embedded starburst rejected: would need r<0.6 pc, smaller than typical clusters  
  > "This is much smaller than typical sizes of stellar clusters of this mass (2-10 pc) and the stars have to be packed extremely close." (5.3 Accretion luminosity or compact star formation)
- Alternative: ADAF challenged by extreme radio-quietness  
  > "ADAF flows are, however, expected to result in powerful relativistic radio jets" (7.4 Alternative jet-driving mechanisms)
- How they decided it was enough: _not stated_
- Limitation (authors): Inclination of nuclear gas difficult to determine  
  > "The actual inclination of the nuclear gas is difficult to determine and is likely changing with radius" (5.1 Nuclear morphology, dynamics, and enclosed mass)
- Limitation (authors): Mass estimates have significant uncertainties  
  > "These numbers have significant uncertainties" (6.1 Molecular masses)
- Limitation (authors): Missing flux for extended low-velocity emission  
  > "Most of the missing flux originates in extended, low-velocity emission associated with the slow wind" (3.2 CO 3–2 moment maps)
- Caveat (inferred, ours): X(CO) factor choice drives mass, energy and momentum numbers
- Caveat (inferred, ours): Dynamical mass depends on assumed inclination and a single velocity offset
- Caveat (inferred, ours): Tb-to-Td and opacity assume gas-dust coupling and filling factor of 1
- Caveat (inferred, ours): Missing flux (~40%) affects low-velocity wind/disk results
- Caveat (inferred, ours): Wind model is only illustrative, no fit

## Reproducibility

- Data public (paper): Acknowledges use of ADS/JAO.ALMA#2012.1.00900.S; 2017 data project listed in table  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00900.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, masks, clean threshold)
- Missing: Calibration scripts and CASA version
- Missing: Mass and energetics derivation details
- Missing: Jet precession model details
- Data volume (inferred): ~50-100 GB for the 2017 extended-configuration Band 7 execution blocks
- Score (inferred): 4/5, Data are partly public and key numbers are given, but imaging and modelling details are sparse and many results rely on assumptions.
- Rediscovery candidate: no, Imaging recipe incomplete, and derived quantities depend on unstated modelling choices.

## Links

- Method: (cite: aalto16) (Earlier low-resolution CO 3-2 data and jet analysis)
- Method: (cite: keene82) (Dust column density formalism)
- Method: (cite: anderson03) (Jet launch radius formalism)
- Companion: (cite: aalto17) (Band 9 CO 6-5 high-resolution observations of NGC 1377)
- Companion: (cite: aalto12b) (SMA discovery of the molecular outflow)

## Checks

```json
{
 "quotes": 83,
 "quotes_ok": 83,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2017.1.0659.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 16,
 "numeric_problems": 0,
 "fill": {
  "facts": 87,
  "stated": 55,
  "rate": 0.632
 },
 "evidence_ok": true
}
```

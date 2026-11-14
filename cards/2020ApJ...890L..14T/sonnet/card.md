# Shaping the Envelope of the Asymptotic Giant Branch Star W43A with a Collimated Fast Jet

`2020ApJ...890L..14T` | The Astrophysical Journal Letters 2020 | first author: Tafoya, Daniel | arXiv: 2006.07157 | DOI: 10.3847/2041-8213/ab70b8

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars
- Question: How is a collimated jet launched and how does it interact with and shape the circumstellar envelope of the AGB/water-fountain star W43A?  
  > "However, the launching of the jet and the way it interacts with the circumstellar material to create such asymmetric morphologies have remained poorly known." (abstract)
- Target **W43A**: coordinates _not stated_; z/distance 2.2 kpc  
  > "W43A, located at a distance of 2.2 kpc from the Sun (see Appendix [5](#sec:W43A_distance))" (Introduction); "We adopt the near kinematical distance since it is compatible with the result of the Bayesian Distance Calculator (cite: Reid2016)." (Distance to W43A.); distance from near kinematic distance (Revised Kinematic Distance Calculator, Reid2014 model A5), consistent with Bayesian Distance Calculator  
  > "W43A, located at a distance of 2.2 kpc from the Sun (see Appendix [5](#sec:W43A_distance))" (Introduction); "We adopt the near kinematical distance since it is compatible with the result of the Bayesian Distance Calculator (cite: Reid2016)." (Distance to W43A.)

## Data provenance

- ALMA projects: 2016.1.00540.S
- bands: Band 6 (~230 GHz)  
  > "using 42 antennas of the ALMA 12m array with Band 6 receivers ($\sim$230 GHz)" (Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 0.7 GHz total from three 234.375 MHz spectral windows  
  > "The continuum image was created by averaging line-free channels from three 234.375 MHz wide spectral windows giving a total bandwidth of 0.7 GHz." (Observations)
- arrays: ALMA 12m array, 42 antennas  
  > "using 42 antennas of the ALMA 12m array" (Observations)
- configurations: _not stated_
- baselines: 41.4 m to 12.1 km  
  > "The maximum and minimum baseline lengths were 12.1 km and 41.4 m, respectively." (Observations)
- angular resolution: 0.04 arcsec  
  > "The corresponding angular resolution and maximum recoverable scale are 0$\rlap{.}^{\prime\prime}$04 and 0$\rlap{.}^{\prime\prime}$6, respectively." (Observations)
- max recoverable scale: 0.6 arcsec  
  > "The corresponding angular resolution and maximum recoverable scale are 0$\rlap{.}^{\prime\prime}$04 and 0$\rlap{.}^{\prime\prime}$6, respectively." (Observations)
- sensitivity: channel rms ~2 mJy/beam; continuum rms ~110 uJy/beam  
  > "The typical channel root-mean-square (rms) noise level is $\sim$2 mJy beam$^{-1}$ in line-free channels." (Observations); "The rms level in the continuum image is $\sim$110 $\mu$Jy beam$^{-1}$." (Observations)
- time on source: 23 min  
  > "The total time of observation on W43A was 23 min." (Observations)
- observing dates: 22 September 2017  
  > "The observations were carried out on 22 September 2017" (Observations)
- pi or archival as stated: Project 2016.1.00540.S, P.I. H. Imai  
  > "as part of the project 2016.1.00540.S (P.I. H. Imai)" (Observations)
- Line: CO J=2-1 (not stated)
- Line: p-H2S 2(2,0)-2(1,1) (not stated)
- Other facility **VLBA**: H2O maser observations (BI41A, 19 January 2014) and positions  
  > "the latest observation on 19 January 2014 (project code BI41A)" (VLBA observations of the H$_{2}$O masers.)
- External data: H2O maser distribution, kinematics and inclination of 35 deg  
  > "considering an inclination angle with respect to the plane of the sky of 35$^{\circ}$ (cite: Imai2002; Chong2015)" (Introduction) [from (cite: Imai2002; Chong2015)]
- External data: Dust absorption coefficient 1.8 cm2/g  
  > "a dust absorption coefficient $\kappa_{\nu}$=1.8 cm$^{2}$ g$^{-1}$ for small silicate grains with coating of amorphous carbon (cite: Ossenkopf1994)" (Volume density of the molecular gas in the bipolar shell.) [from (cite: Ossenkopf1994)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline  
  > "The data were calibrated with the ALMA pipeline" (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1924-2914 (~3.4 Jy) flux/bandpass; J1851+0035 (~260 mJy) gain  
  > "using J1924$-$2914 ($\sim$3.4 Jy) as a flux/bandpass calibrator and J1851+0035 ($\sim$260 mJy) as a gain calibrator" (Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA 5.4.0  
  > "Images were created with CASA 5.4.0 using a Briggs weighting scheme with the robust parameter set to 0." (Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0  
  > "Images were created with CASA 5.4.0 using a Briggs weighting scheme with the robust parameter set to 0." (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum subtracted from data cubes; channel width ~1.3 km/s  
  > "The continuum emission was subtracted from the data cubes and channel maps with a spectral resolution of $\sim$1.3 km s$^{-1}$ were created." (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: ~2 mJy/beam per channel; ~110 uJy/beam continuum  
  > "The rms level in the continuum image is $\sim$110 $\mu$Jy beam$^{-1}$." (Observations)

### Inherited from earlier work

- Jet launch velocity and deceleration analysis from PV-diagram follows IRAS 16342-3814 work  
  > "Following the analysis done by (cite: Tafoya2019), the launch velocity of the jet can be obtained from the highest velocity-offset of the CO($J$=2$\rightarrow$1) emission" (3.3 A decelerating collimated jet and a bipolar outflow) [from (cite: Tafoya2019)]
- Maser map superposition by spatio-kinematical fitting  
  > "was made by the spatio-kinematical fitting to the bipolar jet as described by (cite: Chong2015)" (VLBA observations of the H$_{2}$O masers.) [from (cite: Chong2015)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for continuum subtraction and the method/order of subtraction
- Image size, cell size, and CLEAN masks/thresholds
- Rest frequencies and spectral window setup for CO and H2S
- Self-calibration, if any
- Method for PV-diagram extraction and how velocity offsets and the 75 km/s turnover were measured
- Details of how the shell flux density (267 mJy) was defined and shell volume/thickness
- Knot identification method

## Analysis recipe

1. **Image continuum and line cubes**: Pipeline calibration, Briggs imaging, continuum subtraction, channel maps  
  > "Images were created with CASA 5.4.0 using a Briggs weighting scheme with the robust parameter set to 0." (Observations)
   - software: CASA
   - parameter: robust = 0; ~1.3 km/s channels  
  > "channel maps with a spectral resolution of $\sim$1.3 km s$^{-1}$ were created" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive jet velocities from CO PV-diagram**: PV-diagram along P.A.=68 deg; launch and tip velocities from offsets de-projected by sin(35 deg)  
  > "this velocity corresponds to a de-projected expansion velocity $U_{\rm i}$$\equiv$$|$$V_{\rm i}$$|$/sin 35$^{\circ}$=175 km s$^{-1}$." (3.3 A decelerating collimated jet and a bipolar outflow)
   - assumption: inclination 35 deg to plane of sky; Vsys=34 km/s  
  > "Considering the inclination of the source of 35$^{\circ}$ with respect to the plane of the sky" (3.3 A decelerating collimated jet and a bipolar outflow)
   - fitting: _not stated_
   - validation: compared with IRAS 16342-3814 pattern  
  > "it is evident that the spatio-kinematical configuration of W43A is similar to the one of IRAS 16342$-$3814" (3.3 A decelerating collimated jet and a bipolar outflow)
3. **Estimate shell mass and density from continuum**: Optically thin dust mass M=D^2 S/(kappa B(Td))  
  > "The mass of the gas in the bipolar shell can be estimated assuming optically thin emission and isothermal conditions for the dust." (Volume density of the molecular gas in the bipolar shell.)
   - parameter: S=267±25 mJy; Td=100 K; kappa=1.8 cm2/g  
  > "The flux density of the continuum emission that traces the bipolar shell is 267$\pm$25 mJy." (Volume density of the molecular gas in the bipolar shell.)
   - assumption: dust-to-gas ratio 100; Ossenkopf & Henning coated silicate grains  
  > "and a dust-to-gas ratio value of 100, the mass of the bipolar shell is 2.0$\pm$0.2 solar masses." (Volume density of the molecular gas in the bipolar shell.)
   - fitting: _not stated_
   - validation: uncoated grains give unrealistically high mass given M<~8 Msun  
  > "which are unrealistically high given that the initial mass of the star must be $M$$\lesssim$8$M_{\odot}$." (Volume density of the molecular gas in the bipolar shell.)
4. **Kinematic ages of jet and shell**: Jet age from constant velocity then constant deceleration; shell age R/V using H2S PV-diagram  
  > "The kinematical age of the bipolar shell can be obtained as $\tau_{\rm shell}$$\approx$$R_{\rm shell}$/$V_{\rm shell}$" (3.4 Time scale of the jet and bipolar shell)
   - assumption: H2S traces the shell kinematics  
  > "Thus, we assume that the H$_{2}$S emission traces not only the spatial distribution but also the kinematics of the bipolar shell." (3.4 Time scale of the jet and bipolar shell)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.4.0: imaging  
  > "Images were created with CASA 5.4.0" (Observations)
- **Revised Kinematic Distance Calculator** 2014: kinematic distance to W43A  
  > "using the Revised Kinematic Distance Calculator (2014) using Galactic parameters from model A5 in (cite: Reid2014)" (Distance to W43A.)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Jet launch velocity (de-projected) | 175 | not stated | km/s | 2 | $U_{\rm i}$$\equiv$$/$$V_{\rm i}$$/$/sin 35$^{\circ}$=175 km s$^{-1}$. |
| Jet velocity at tip | 130 | not stated | km/s | 2 | $U_{\rm f}$$\equiv$$/$$V_{\rm f}$$/$/sin 35$^{\circ}$=130 km s$^{-1}$. |
| Shell mass | 2.0 | 0.2 | Msun | 3 | the mass of the bipolar shell is 2.0$\pm$0.2 solar masses |
| Shell density | 5.1e8 | 0.5e8 | cm^-3 | 3 | $n_{\rm H_{2}, Shell}$=5.1$\pm$0.5$\times$10$^{8}$ cm$^{-3}$ |
| Jet kinematic age | 65 | not stated | yr | 4 | Thus, the total kinematical age of the jet is of just $\tau_{\rm jet}$=65 years. |
| Shell kinematic age | 60 | not stated | yr | 4 | The resulting timescale for the shell is $\tau_{\rm shell}$$\approx$60 years. |
| Brightness temperature of bright shell regions | ~110 | not stated | K | 0 | the brightness temperature of the bright regions ($\approx 110$ K) |
| Average knot spacing | 180 | not stated | AU | 0 | The average knot spacing is 180 AU. |

## Qualitative findings

- CO traces a collimated, decelerating jet from near the star to the shell; the continuum shows a bipolar shell with a central compact source.  
  > "The continuum emission reveals a bipolar shell with a compact bright dot in the centre that pinpoints the location of the driving source of the jet." (abstract)

## Claim tuples

- H: The CO emission traces a decelerating jet interacting with the envelope | E: CO(2-1) PV-diagram analysis | R: S-shaped PV pattern; 175 km/s launch decelerating to 130 km/s | F: A collimated jet decelerates as it entrains circumstellar material | **supported**
- H: The jet and bipolar shell formed simultaneously | E: Compare kinematic ages from CO and H2S | R: jet 65 yr, shell ~60 yr | F: Created together by a common mechanism in a very short time | **supported**
- H: The knotty jet may indicate a binary | E: Count knots and spacing | R: 9 red and 7 blue knots; spacing 180 AU; interval 5-7 yr | F: Possible eccentric binary with orbital period 5-7 yr | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Uncoated silicate opacity rejected as giving unrealistically high shell mass  
  > "which are unrealistically high given that the initial mass of the star must be $M$$\lesssim$8$M_{\odot}$." (Volume density of the molecular gas in the bipolar shell.)
- How they decided it was enough: _not stated_
- Limitation (authors): No clear evidence from these data of jet precession.  
  > "from these observations there is no clear evidence that the jet is precessing" (3.3 A decelerating collimated jet and a bipolar outflow)
- Caveat (inferred, ours): Shell kinematics assumed from H2S as a shock tracer
- Caveat (inferred, ours): Inclination of 35 deg taken from maser work and applied to all components
- Caveat (inferred, ours): Dust temperature, opacity and gas-to-dust ratio assumptions dominate mass uncertainty
- Caveat (inferred, ours): Binary interpretation is speculative

## Reproducibility

- Data public (paper): ALMA project 2016.1.00540.S acknowledged via ADS/JAO.ALMA; public status not explicitly stated  
  > "ADS/JAO.ALMA#2016.1.00540.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters (image/cell size, masks, thresholds)
- Missing: PV extraction and velocity measurement procedure
- Missing: Shell geometry for volume
- Data volume (inferred): ~20-50 GB raw single-EB Band 6 data; cubes a few GB
- Score (inferred): 5/5, Data and main imaging settings are given, but cube parameters and measurement procedures for the key velocities are not detailed.
- Rediscovery candidate: no, Key results depend on visually chosen velocity-offsets and undefined shell geometry, so recipe is incomplete.

## Links

- Method: (cite: Tafoya2019) (PV-diagram jet deceleration analysis for IRAS 16342-3814)
- Companion: (cite: Chong2015) (VLBA H2O maser results for W43A)

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 41,
  "rate": 0.586
 },
 "evidence_ok": true
}
```

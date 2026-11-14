# <SUP>13</SUP>C<SUP>17</SUP>O suggests gravitational instability in the HL Tau disc

`2020MNRAS.493L.108B` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Booth, Alice S. | arXiv: 2001.07550 | DOI: 10.1093/mnrasl/slaa014

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: How much gas mass does the HL Tau disc contain when traced by the rare isotopologue 13C17O, and is the disc gravitationally unstable?  
  > "We use these data to derive a lower limit to the total gas disc mass and discuss how this impacts the gravitational stability of the HL Tau star-disc system." (Introduction)
- Target **HL Tau**: coordinates _not stated_; z/distance 140 pc  
  > "HL Tau is located in the nearby (140 pc) Taurus-Auriga star forming region (cite: rebull_2004)." (Introduction); distance from Taurus-Auriga membership (cite: rebull_2004)  
  > "HL Tau is located in the nearby (140 pc) Taurus-Auriga star forming region (cite: rebull_2004)." (Introduction)

## Data provenance

- ALMA projects: 2017.1.01178.S, 2011.0.00015.SV
- bands: Band 7  
  > "HL Tau was observed by ALMA in Band 7 on the 24th of November 2017" (2 Observations)
- frequencies and spectral setup: SPW covering J=3–2 (321.852 GHz), native resolution 0.908 km/s  
  > "had a native spectral resolution of 0.908 km s $^{-1}$" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-8, 49 antennae  
  > "for 1.46 hours with 49 antennae in configuration C43-8" (2 Observations)
- baselines: 92–8547 m  
  > "Baseline lengths ranged from 92–8547 m" (2 Observations)
- angular resolution: natural beam 0.14'' x 0.11''; final 0.28'' x 0.24'' with 0.2'' taper  
  > "resulting in a final beamsize of 0.28$''$ $\times$ 0.24$''$ ($-36$$^\circ$)" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: rms 4 mJy/beam per channel  
  > "with a rms of 4 mJy beam$^{-1}$ per channel measure from the line-free channels" (2 Observations)
- time on source: 1.46 hours  
  > "for 1.46 hours with 49 antennae" (2 Observations)
- observing dates: 24 November 2017  
  > "on the 24th of November 2017" (2 Observations)
- pi or archival as stated: Project 2017.1.01178.S, P.I. E. Humphreys (not the authors); Science Verification data for the continuum  
  > "under project code 2017.1.01178.S (P.I. E. Humphreys)" (2 Observations)
- Line: 13C17O J=3–2 (321.852 GHz)
- External data: HL Tau Band 7 continuum image (ALMA Science Verification) and 0.9 mm continuum profile  
  > "shows the ALMA Science Verification Band 7 ($\sim$345 GHz) continuum image" (3 Results) [from (cite: 2015ApJ...808L...3A)]
- External data: Dust surface density parameters: Md=0.105 Msun, Rc=80 au, Rin=8.78 au, gamma=-0.20  
  > "$R_c$ is 80 au, $R_{in}$ is 8.78 au and $\gamma$ is -0.20 (cite: 2015ApJ...808..102K)" (4.1) [from (cite: 2015ApJ...808..102K)]
- External data: Midplane temperature profile T=55 K (r/10 au)^-0.65  
  > "$T_{\rm mid} = 55\,{\rm K} (r/10~{\rm au})^{-0.65}$ for $r>10$ au" (4.1) [from (cite: 2015ApJ...808..102K)]
- External data: Partition function, Eu, S mu^2 from CDMS  
  > "are taken from the CDMS database (cite: 2005JMoSt.742..215M)" (4.1) [from (cite: 2005JMoSt.742..215M)]
- External data: ISM isotope ratios 69, 557, 3.6  
  > "$n(\ce{^{12}C^{16}O})/n(\ce{^{12}C^{18}O}) = 557$" (4.1) [from (cite: Wilson_1999)]
- External data: Stellar mass 1.7 Msun  
  > "we assume a central star mass of 1.7 M$_{\odot}$" (5.2) [from (cite: 2016ApJ...816...25P)]
- External data: C18O J=2-1 radial profile from SMA and gas mass  
  > "the data from the radial profile presented in (cite: 2018ApJ...869...59W) for a radius of 100 au" (5.1) [from (cite: 2018ApJ...869...59W)]

## Processing

### Calibration

- pipeline or manual: Data (self-)calibration performed with CASA; details not given  
  > "Data (self-)calibration and imaging were performed with CASA version 5.1.1 (cite: mcmullin_2007)." (2 Observations)
- casa version: CASA 5.1.1  
  > "performed with CASA version 5.1.1" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: CLEAN  
  > "Line imaging was performed with the CLEAN algorithm" (2 Observations)
- weighting robust: _not stated_
- uv taper: 0.2''  
  > "We used a 0.2$''$ $uv$-taper, which was found to maximise the signal-to-noise (S/N) of the line emission" (2 Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: Keplerian mask using measured position and inclination angles  
  > "using a Keplerian mask with the measured position and inclination angles of the disc" (2 Observations)
- multiscale scales: _not stated_
- continuum subtraction: uv-plane, constant baseline (fitorder 0)  
  > "Continuum subtraction was performed in the $uv$-plane using a constant baseline (fitorder 0)." (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.28'' x 0.24'' (-36 deg)  
  > "resulting in a final beamsize of 0.28$''$ $\times$ 0.24$''$ ($-36$$^\circ$)" (2 Observations)
- final rms: 4 mJy/beam per channel, 1.0 km/s channels  
  > "The emission is detected across 9 (1.0 km s $^{-1}$) channels with a rms of 4 mJy beam$^{-1}$ per channel" (2 Observations)

### Inherited from earlier work

- Disc position and inclination angles for Keplerian mask  
  > "using a Keplerian mask with the measured position and inclination angles of the disc (cite: 2015ApJ...808L...3A)" (2 Observations) [from (cite: 2015ApJ...808L...3A)]
- 13C17O as a robust gas-mass tracer, demonstrated previously  
  > "We have demonstrated this line to be a robust tracer of disc gas mass (cite: Booth_2019)." (Introduction) [from (cite: Booth_2019)]

### Not stated but needed to reproduce (our reading)

- CASA version-specific calibration scripts/pipeline and self-calibration solints
- Disc position angle and inclination values and Keplerian mask parameters
- Line-free channels used for continuum subtraction
- Clean threshold, cell and image size, robust/weighting
- Method for deriving radial profiles (annuli, bin widths, deprojection) and integrated-intensity error propagation
- Moment-map clipping details beyond 2.5 sigma for first moment
- Toomre Q uncertainty propagation procedure

## Analysis recipe

1. **Image 13C17O J=3-2 and make moment maps and radial profile**: uv-plane continuum subtraction, CLEAN with Keplerian mask and 0.2'' taper, zeroth and first moment maps, deprojected azimuthally averaged profile  
  > "Also shown are the de-projected and azimuthally averaged $J=3$–2 integrated intensity and 0.9 mm continuum profiles derived from our dataset" (3 Results)
   - software: CASA
   - parameter: 0.2'' uv-taper; first moment with 2.5 sigma clip  
  > "made with a 2.5 $\sigma$ clip" (3 Results)
   - fitting: _not stated_
   - validation: _not stated_
2. **Convert integrated intensity to 13C17O column density**: LTE, optically thin column density equation at each radial point  
  > "under the assumption of both local thermodynamic equilibrium (LTE) and optically thin line emission" (4.1)
   - parameter: Tex = 25 K at 90–110 au; 20–80 K gives column densities within errors  
  > "We therefore adopt $T_{\rm ex} = 25$ K for the excitation temperature in this region" (4.1)
   - assumption: LTE, optically thin  
  > "under the assumption of both local thermodynamic equilibrium (LTE) and optically thin line emission" (4.1)
   - fitting: _not stated_
   - validation: _not stated_
3. **Extrapolate to total gas mass**: Scale 13C17O to 12C16O with ISM isotope ratios, to H2 with CO/H2 = 5e-5, then scale the Kamp-type dust-based surface density profile to match 90–110 au  
  > "an increase in the total disc gas mass to $M_{\rm gas} = 0.20^{+0.06}_{-0.06}$ M$_{\odot}$ is required to match the observations between 90–110 au" (4.1)
   - assumption: CO/H2 = 5e-5 (depletion factor of two); 80% of gas mass in H2  
  > "A total gas density is then calculated assuming 80% of the gas mass lies in (cite: 2013ApJ...774...16R)." (4.1)
   - assumption: ISM isotope ratios 69, 557, 3.6  
  > "$n(\ce{^{12}C^{16}O})/n(\ce{^{13}C^{16}O}) = 69$, $n(\ce{^{12}C^{16}O})/n(\ce{^{12}C^{18}O}) = 557$, and $n(\ce{^{12}C^{18}O})/n(\ce{^{12}C^{17}O}) = 3.6$" (Analysis, Conversion of line flux to disc gas mass)
   - fitting: _not stated_
   - validation: Compared with dust-based mass from Tapia 2019 and C18O mass from Wu 2018  
  > "Our result from therefore brings mass measurements from dust continuum and molecular line emission into agreement for the first time in this disc." (5.1)
4. **Compute Toomre Q profile**: Q = cs kappa/(pi G Sigma) with cs from Tmid, Keplerian kappa, M*=1.7 Msun, Sigma of gas and dust  
  > "where $c_s$ is the sound speed of the gas (calculated from T$_{\rm mid}$)" (5.2)
   - parameter: instability threshold Q<~1.7  
  > "Regions of the disc with $Q \lesssim 1.7$ will be susceptible to gravitational instability" (5.2)
   - assumption: Stellar mass 1.7 Msun  
  > "we assume a central star mass of 1.7 M$_{\odot}$" (5.2)
   - fitting: _not stated_
   - validation: Magnetic-field correction checked with beta_p ~10 to 10^4  
  > "Such values do not alter our minimum Toomre $Q$ value by more than $\sim$5 per cent" (5.2)

## Software

- **CASA** 5.1.1: Calibration, self-calibration, continuum subtraction and CLEAN imaging  
  > "Data (self-)calibration and imaging were performed with CASA version 5.1.1 (cite: mcmullin_2007)." (2 Observations)
- **CDMS** : Partition function, upper energy level, S mu^2  
  > "are taken from the CDMS database (cite: 2005JMoSt.742..215M)" (4.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Peak line emission per channel | 30 | not stated | mJy/beam | 1 | a peak line emission of 30 mJy beam$^{-1}$ per channel (S/N of 7.5) |
| Detection S/N | 7.5 | not stated | dimensionless | 1 | a peak line emission of 30 mJy beam$^{-1}$ per channel (S/N of 7.5) |
| Radial extent of emission | ~140 | not stated | au | 1 | The emission is detected out to approximately 140 au from the central star |
| Total disc gas mass | 0.20 | +0.06/-0.06 | Msun | 3 | $M_{\rm gas} = 0.20^{+0.06}_{-0.06}$ M$_{\odot}$ |
| Minimum Toomre Q | 1.1 at r = 77 au | +0.5/-0.2 | dimensionless | 4 | with minimum $Q = 1.1_{-0.2}^{+0.5}$ at $r  = 77$ au |
| Unstable region (Q<1.7) | 50–110 | not stated | au | 4 | gravitationally unstable ($Q<1.7$) from approximately 50–110 au |
| Gas mass if CO/H2 matches Wu 2018 (2.7e-4) | ~0.04 | not stated | Msun | 3 | our resulting gas mass would be $\sim$0.04 M$_{\odot}$ |
| C18O/13C17O column density ratio at 100 au | ~4 | not stated | dimensionless | 2 | we find that the ratio is only $\sim 4$ |

## Qualitative findings

- Line emission deficit near 50 au is likely due to high continuum opacity, not a real gap.  
  > "This deficit of emission is therefore likely due to the high continuum opacity at Band 7 obscuring the line emission originating from the midplane" (3 Results)
- C18O J=2-1 is optically thick and does not trace bulk gas mass.  
  > "This demonstrates that the $J=2$–1 emission is optically thick in the HL Tau disc" (5.1)

## Claim tuples

- H: The HL Tau gas mass has been underestimated by optically thick CO tracers. | E: Detect 13C17O J=3-2 and convert to gas mass assuming LTE, optically thin emission. | R: Mgas = 0.20 Msun, at least ten times higher than previous measurements. | F: The disc is much more massive than previously reported; 0.2 Msun is a conservative lower limit. | **supported**
- H: The HL Tau disc is gravitationally unstable. | E: Compute Toomre Q using the new gas surface density. | R: Q<1.7 from 50–110 au, min Q=1.1. | F: The disc is gravitationally unstable in this region, coinciding with the gap and the gas spiral. | **supported**
- H: A planet in the 65–74 au gap formed via gravitational fragmentation. | E: Compare the unstable region with the gap location and cooling time arguments. | R: Q<=1 from ~60–100 au at the lower error bound. | F: If the gap is planet-carved, the planet likely formed via gravitational fragmentation. | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Few other molecular line observations are usable for HL Tau due to absorption and velocity gradients, so a simpler method was adopted instead of full radiative transfer modelling.  
  > "meaning a similar wealth of observational data is not readily available. We therefore employ a simpler method of analysis." (4.1)
- Alternative: Warmer temperature models rejected because they lack a CO snowline, in tension with a snowline chemical tracer detection.  
  > "warmer models have no CO snowline ($\sim 20$ K) within the radial extent of the disc" (4.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Gas mass depends on CO/H2 ratio, possible freeze-out, optical thickness and isotope ratios; precise effects need dedicated modelling.  
  > "The precise magnitude of these effects cannot be determined without dedicated modelling of the HL Tau disc." (4.2)
- Caveat (inferred, ours): Single-temperature LTE optically thin conversion at only 90–110 au, extrapolated to total mass via an assumed dust-based profile
- Caveat (inferred, ours): Tex and CO/H2 abundance assumed; uncertainties not propagated
- Caveat (inferred, ours): Continuum optical depth may hide emission, so the mass is a lower limit but Q is sensitive
- Caveat (inferred, ours): Detection is modest S/N 7.5
- Caveat (inferred, ours): Hyperfine structure unresolved

## Reproducibility

- Data public (paper): Data from ALMA projects acknowledged with ADS/JAO.ALMA identifiers; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00015.SV, ADS/JAO.ALMA#2017.1.01178.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Calibration and self-calibration details
- Missing: Deprojection parameters and radial-profile binning
- Missing: Imaging parameters (weighting, cell, image size, threshold)
- Missing: Exact procedure for scaling model to 90–110 au and error propagation
- Data volume (inferred): ~50-100 GB raw for one long-baseline Band 7 execution
- Score (inferred): 3/5, Data are identified and the analysis is simple and analytic, but imaging and calibration details and profile extraction are missing.
- Rediscovery candidate: no, Key recipe parts (deprojection, binning, mask, scaling) are not fully specified, though the data are likely public.

## Links

- Method: (cite: Booth_2019) (Showed 13C17O to be a robust gas mass tracer; modelling approach in HD 163296)
- Companion: (cite: 2018ApJ...869...59W) (Previous C18O-based HL Tau gas mass compared against)
- Companion: (cite: yen_2019_spiral) (Detected gas spiral in HL Tau)
- Related: ALMA HL Tau Long Baseline Campaign / Science Verification 2011.0.00015.SV

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 50,
  "rate": 0.649
 },
 "evidence_ok": true
}
```

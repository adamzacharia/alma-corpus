# Angular Momentum Loss in the Envelope-Disk Transition Region of the HH 111 Protostellar System: Evidence for Magnetic Braking?

`2016ApJ...826..213L` | The Astrophysical Journal 2016 | first author: Lee, Chin-Fei | arXiv: 1605.08132 | DOI: 10.3847/0004-637X/826/2/213

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks
- Question: How does a Keplerian disk form inside the flattened envelope of HH 111, and how does the specific angular momentum change across the envelope-disk transition region?  
  > "In order to study how a KRD can be formed, we need to resolve the transition region, and compare its structure and kinematics to current model predictions." (Introduction)
- Target **HH 111 (VLA 1 and VLA 2)**: coordinates VLA 1: 05h51m46.254s, +02d48m29.65s (J2000)  
  > "$\alpha_{(2000)}=05^\mathrm{h} 51^\mathrm{m} 46^\mathrm{s}_{^\textrm{.}} 254$, $\delta_{(2000)}=+02\ensuremath{^\circ} 48\ensuremath{'} 29^{\prime\prime}_{^\textrm{.}}65$" (Results); "in the L1617 cloud of Orion at a distance of 400 pc" (Introduction); z/distance 400 pc  
  > "$\alpha_{(2000)}=05^\mathrm{h} 51^\mathrm{m} 46^\mathrm{s}_{^\textrm{.}} 254$, $\delta_{(2000)}=+02\ensuremath{^\circ} 48\ensuremath{'} 29^{\prime\prime}_{^\textrm{.}}65$" (Results); "in the L1617 cloud of Orion at a distance of 400 pc" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00013.S
- bands: 230 GHz band (Band 6)  
  > "The 230 GHz band receivers were used to observe the $^{12}$CO ($J=2-1$), $^{13}$CO ($J=2-1$), and C$^{18}$O ($J=2-1$) lines simultaneously with the 230 GHz continuum." (2.1 ALMA Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12m array and 7m array, 3-point mosaic  
  > "Observations toward the HH 111 system were obtained with ALMA using both the 12m array (in C32-4 configuration with a total time of $\sim$ 140 minutes) and the 7m array" (2.1 ALMA Observations)
- configurations: _not stated_
- baselines: 12m: 20-558.2 m; 7m: 7-48.9 m  
  > "33-35 antennas were used with the projected baseline length of 20$-$558.2 m." (2.1 ALMA Observations)
- angular resolution: 0.50 arcsec continuum (super-uniform + taper); 0.74x0.62 arcsec PA 77 deg in C18O  
  > "With super-uniform weighting, the synthesized beam has a size of $0^{\prime\prime}_{^\textrm{.}}74$$\times$$0^{\prime\prime}_{^\textrm{.}}62$ at a position angle (P.A.) of 77$^\circ$ in C$^{18}$O." (2.1 ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: 0.22 mJy/beam continuum; 4.3 mJy/beam per 0.083 km/s channel in C18O  
  > "The rms noise level is $\sim$ 0.22 mJy beam$^{-1}$ ($\sim$ 20 mK) for the continuum, and $\sim$ 4.3 mJy beam$^{-1}$ ($\sim$ 0.23 K)" (2.1 ALMA Observations)
- time on source: 12m: ~140 min; 7m: ~445 min  
  > "12m array (in C32-4 configuration with a total time of $\sim$ 140 minutes) and the 7m array (with a total time of $\sim$ 445 minutes)" (2.1 ALMA Observations)
- observing dates: 12m: 2014 April 13-28; 7m: Dec 2013 to Dec 2014  
  > "3 executions were carried out during 2014 April 13-28, all with 47.11 minutes on the source." (2.1 ALMA Observations)
- pi or archival as stated: _not stated_
- Line: C18O J=2-1 (not stated)
- Line: SO (SMA) N_J=5_6-4_5 (not stated)
- Other facility **SMA**: SO N_J=5_6-4_5 maps at similar resolution  
  > "The longest projected baseline length is $\sim$ 480 m, similar to that of ALMA observations." (2.2 SMA Observations)
- Other facility **HST NICMOS**: infrared background image  
  > "mosaic image based on the Hubble Space Telescope (HST) NICMOS image" (Results)
- Other facility **VLA**: 7 mm positions of VLA 1 and 2  
  > "These VLA positions are adopted here as the source positions." (Results)
- External data: VLA 1 and VLA 2 source positions at 7 mm  
  > "These VLA positions are adopted here as the source positions." (Results) [from (cite: Rodriguez2008)]
- External data: HST NICMOS mosaic image  
  > "obtained by (cite: Reipurth1999)" (Results) [from (cite: Reipurth1999)]
- External data: jet inclination of ~10 deg to the plane of the sky  
  > "jet that was found to have an inclination of $\sim$ 10$^\circ$ to the plane of the sky (cite: Reipurth1992)" (3.2 C18O Envelope and Disk) [from (cite: Reipurth1992)]
- External data: disk gas+dust mass ~0.14 +/- 0.03 Msun  
  > "the gas and dust associated with the disk were estimated to have a total mass of $\sim 0.14 \pm 0.03$ $M_\odot$" (4.2 Keplerian Disk) [from (cite: Lee2011)]

## Processing

### Calibration

- pipeline or manual: CASA calibration; passband J0750+1231 and J0607-0834; gain J0532+0732 and J0607-0834; flux Callisto and Ganymede  
  > "The data were calibrated with the CASA package, with Quasars J0750+1231 and J0607-0834 as passband calibrators" (2.1 ALMA Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto and Ganymede  
  > "and Callisto and Ganymede as flux calibrators." (2.1 ALMA Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: super-uniform weighting; continuum also with taper  
  > "With super-uniform weighting and taper, the synthesized beam becomes circular with a size of $0^{\prime\prime}_{^\textrm{.}}50$ in continuum." (2.1 ALMA Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12m and 7m data combined (implied; method not described)  
  > "using both the 12m array (in C32-4 configuration with a total time of $\sim$ 140 minutes) and the 7m array" (2.1 ALMA Observations)
- smoothing: _not stated_
- final beam: 0.74x0.62 arcsec PA 77 deg (C18O); 0.50 arcsec (continuum)  
  > "the synthesized beam has a size of $0^{\prime\prime}_{^\textrm{.}}74$$\times$$0^{\prime\prime}_{^\textrm{.}}62$ at a position angle (P.A.) of 77$^\circ$ in C$^{18}$O" (2.1 ALMA Observations)
- final rms: 0.22 mJy/beam continuum; 4.3 mJy/beam C18O channel  
  > "The rms noise level is $\sim$ 0.22 mJy beam$^{-1}$ ($\sim$ 20 mK) for the continuum" (2.1 ALMA Observations)

### Inherited from earlier work

- SMA SO observation and MIRIAD imaging details  
  > "For SO observations with SMA, the details have been reported in (cite: Lee2011) and are thus not repeated here." (2.2 SMA Observations) [from (cite: Lee2011)]
- Results presented relative to HST image  
  > "As in (cite: Lee2010), the results are presented in comparison to a mosaic image based on the Hubble Space Telescope (HST) NICMOS image" (Results) [from (cite: Lee2010)]
- infall velocity assumed to scale as r^-0.5  
  > "Assuming that the infall velocity in the envelope increases toward the center with $r^{-0.5}$ as in (cite: Lee2010)" (3.4 Infall Motion) [from (cite: Lee2010)]

### Not stated but needed to reproduce (our reading)

- Rest frequencies of C18O and SO
- Imaging task, robust/uniform parameters, cell and image size, deconvolver and masks
- How 12m and 7m data were combined
- CASA version
- Continuum-subtraction and line-free channels
- Taper parameters
- How rotation curves were extracted from PV diagrams and fit (method, errors)
- Angular momentum profile calculation details
- Flux scale uncertainty for ALMA

## Analysis recipe

1. **Measure 230 GHz continuum of the disks**: Gaussian deconvolved size and flux density of VLA 1 and VLA 2 from 0.5 arcsec continuum map  
  > "resolved into a disklike structure with a Gaussian deconvolved size of $0^{\prime\prime}_{^\textrm{.}}53$$\times$$0^{\prime\prime}_{^\textrm{.}}19$ (212 AU $\times$ 76 AU)" (3.1 230 GHz Continuum Emission)
   - software: CASA
   - fitting: _not stated_
   - validation: compared with previous results of Lee2011  
  > "all similar to those found in (cite: Lee2011)" (3.1 230 GHz Continuum Emission)
2. **Fit envelope and disk rotation curves from C18O PV diagram**: PV cut along major axis; fit v=v_c(r/r0)^-1 in outer envelope and v=v_k(r/r0)^-0.5 in inner disk, r0=1 arcsec  
  > "Now we can refine the fitting parameters with ALMA at higher angular and velocity resolutions." (3.2 C18O Envelope and Disk)
   - parameter: systemic velocity refined to 8.85 km/s to fit both sides  
  > "In this fit, the systemic velocity is refined to 8.85 km s$^{-1}$ from 8.9 km s$^{-1}$" (3.2 C18O Envelope and Disk)
   - assumption: jet inclination ~10 deg, edge-on envelope-disk  
  > "is thus almost edge-on, with its farside to the west and nearside to the east." (3.2 C18O Envelope and Disk)
   - fitting: _not stated_
   - validation: compared with SMA fit from Lee2010  
  > "but with slightly smaller $v_c=3.6\pm0.5$ km s$^{-1}$ (solid curves)" (3.2 C18O Envelope and Disk)
3. **Derive central mass from Keplerian velocity**: Keplerian fit within 0.4 arcsec gives stellar mass  
  > "The Keplerian velocity here implies a mass of $\sim 1.8\pm0.5$ $M_\odot$ for the central VLA 1 source." (3.2 C18O Envelope and Disk)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit infall velocity along minor axis**: PV diagrams along minor axis of C18O and SO fitted with v_i=-1.7(r/r0)^-0.5 km/s and compared to free-fall  
  > "the infall velocity seen in C$^{18}$O and SO can be roughly fitted with $v_i =
-1.7 (r/r_0)^{-0.5}$ km s$^{-1}$" (3.4 Infall Motion)
   - assumption: infall velocity scales as r^-0.5  
  > "Assuming that the infall velocity in the envelope increases toward the center with $r^{-0.5}$ as in (cite: Lee2010)" (3.4 Infall Motion)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compute specific angular momentum profile and centrifugal radius**: specific angular momentum proportional to rotation velocity times radius; centrifugal radius (v_c/v_k)^2 r0  
  > "The specific angular momentum, which is proportional to the product of rotation velocity and radius, decreases tremendously in the transition region, by a factor of $\sim 3$" (5.1 Flattened Envelope: Transition Region)
   - assumption: steady-state flow  
  > "If the flow in the transition region is in steady state, the drop implies a tremendous loss of specific angular momentum, by a factor of 3." (5.1 Flattened Envelope: Transition Region)
   - fitting: _not stated_
   - validation: qualitative comparison with MHD models  
  > "Nevertheless, its inferred sub-free-fall collapse and large loss of angular momentum are qualitatively consistent with a strongly magnetized envelope-disk region that is expected on general theoretical grounds." (Discussion: Comparing to theoretical models)

## Software

- **CASA** : ALMA calibration  
  > "The data were calibrated with the CASA package" (2.1 ALMA Observations)
- **MIR** : SMA visibility calibration  
  > "The visibility data were calibrated with the MIR package." (2.2 SMA Observations)
- **MIRIAD** : SMA imaging  
  > "The calibrated visibility data was then imaged with the MIRIAD package" (2.2 SMA Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| VLA 1 continuum flux density | 270 | 40 | mJy | 1 | with a flux density of 270$\pm$40 mJy |
| VLA 2 continuum flux density | 9 | 1.4 | mJy | 1 | unresolved with a flux density of $\sim$ 9$\pm$1.4 mJy |
| Systemic velocity | 8.85 | 0.14 | km/s LSR | 2 | $V_\textrm{\scriptsize sys}= 8.85\pm0.14$ km s$^{-1}$ LSR |
| v_c (outer envelope) | 3.6 | 0.5 | km/s | 2 | slightly smaller $v_c=3.6\pm0.5$ km s$^{-1}$ (solid curves) |
| v_k (Keplerian) | 2.0 | 0.3 | km/s | 2 | with $v_k=2.0\pm0.3$ km s$^{-1}$ |
| Central mass of VLA 1 | 1.8 | 0.5 | Msun | 3 | implies a mass of $\sim 1.8\pm0.5$ $M_\odot$ for the central VLA 1 source |
| Infall velocity coefficient | -1.7 | not stated | km/s at 1 arcsec | 4 | $v_i =
-1.7 (r/r_0)^{-0.5}$ km s$^{-1}$ |
| Centrifugal radius of envelope | 3.24 arcsec (~1300 AU) | not stated | arcsec | 5 | this radius is $(\frac{v_c}{v_k})^2 r_0=$$3^{\prime\prime}_{^\textrm{.}}24$ ($\sim$ 1300 AU) |
| Drop in specific angular momentum 2000 AU to 160 AU | ~3 | not stated | dimensionless | 5 | decreases tremendously in the transition region, by a factor of $\sim 3$, from a distance of roughly 2000 AU ($5''$) to 160 AU |

## Qualitative findings

- SO emission traces a ring of accretion shocks around the disk outer edge, occurring before rotation becomes Keplerian  
  > "Therefore, the SO emission likely traces a ring of accretion shocks around the disk." (5.3 A Ring of SO Shocks)

## Claim tuples

- H: Does the rotation profile switch directly from angular momentum conservation to Keplerian? | E: C18O PV diagram along major axis with ALMA | R: Rotation first rises slower, dips slightly, then rises rapidly; Keplerian only within ~0.4 arcsec | F: Flattened envelope is a transition region and the KRD is compact | **supported**
- H: Is angular momentum lost in the transition region? | E: Compare rotation velocity times radius from 2000 AU to 160 AU | R: Specific angular momentum drops by factor ~3 (if steady state) | F: Consistent with efficient magnetic braking in a magnetized core | **partially**
- H: Is infall in the envelope slower than free-fall? | E: Minor-axis PV of C18O and SO | R: Infall ~50% of free-fall | F: Sub-free-fall infall consistent with magnetic support | **supported**
- H: Where does SO shock emission originate? | E: SMA SO map and PV | R: SO peaks near the disk outer edge, rotating and infalling | F: Likely a ring of accretion shocks around the disk | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: SO shock could alternatively come from ambipolar-diffusion heating in the post-AD-shock region  
  > "Alternatively, it could be related to heating through ambipolar diffusion in the post-AD-shock region, which could be broader in the radial range." (5.5 Comparing to theoretical models)
- How they decided it was enough: _not stated_
- Limitation (authors): Infall velocity poorly determined in the edge-on, unresolved envelope; steady state assumed  
  > "the infall velocity is not well determined, because the flattened envelope is almost edge-on and thus not well resolved along the minor axis." (5.1 Flattened Envelope: Transition Region)
- Limitation (authors): Extended emission resolved out for lack of short uv coverage  
  > "is resolved out from our ALMA observations, due to a lack of shorter $uv$ coverage." (3.2 C18O Envelope and Disk)
- Caveat (inferred, ours): Rotation curve fits lack stated fitting method and error treatment
- Caveat (inferred, ours): Angular momentum loss relies on steady-state assumption and an edge-on geometry
- Caveat (inferred, ours): Magnetic braking is inferred only qualitatively with no magnetic field measurement
- Caveat (inferred, ours): Resolved-out flux and self-absorption near systemic velocity may bias fits

## Reproducibility

- Data public (paper): ALMA data acknowledged by project code 2012.1.00013.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00013.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters and CASA version
- Missing: PV fitting procedure
- Missing: SMA data details given only in Lee2011
- Data volume (inferred): ~50-200 GB for 12m+7m raw data
- Score (inferred): 3/5, Data are public and results numeric, but imaging and fitting details are sparse.
- Rediscovery candidate: no, Recipe is incomplete: imaging parameters and the rotation-curve fitting method are not given.

## Links

- Companion: (cite: Lee2010) (Previous SMA study of HH 111 envelope rotation and infall)
- Companion: (cite: Lee2011) (Earlier SMA/continuum observations of HH 111, including SO details)

## Checks

```json
{
 "quotes": 65,
 "quotes_ok": 65,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 46,
  "rate": 0.582
 },
 "evidence_ok": true
}
```

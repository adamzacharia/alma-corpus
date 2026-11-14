# Rotation in the NGC 1333 IRAS 4C Outflow

`2018ApJ...864...76Z` | The Astrophysical Journal 2018 | first author: Zhang, Yichen | arXiv: 1808.00346 | DOI: 10.3847/1538-4357/aad7ba

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: Does the IRAS 4C molecular outflow rotate, and what do its angular momentum and launching radii imply for the launching mechanism (X-wind vs disk wind)?  
  > "we estimate the range of outflow launching radii to be $5-15$ au." (abstract); "by measuring the outflow rotation, one can constrain the launching radii of the outflow." (Introduction)
- Target **NGC 1333 IRAS 4C**: coordinates RA(J2000)=03h29m13.55s, Dec=+31d13m58.11s (continuum peak)  
  > "located in the NGC 1333 star-forming region in the Perseus Molecular Cloud at a distance of 235 pc ((cite: Hirota08))" (Introduction); "The continuum peak is derived to be at $(\alpha_{2000},\delta_{2000})=(3^{\mathrm{h}}29^{\mathrm{m}}13^{\mathrm{s}}.55$, $+31^\circ13\ensuremath{'}58\ensuremath{''}.11)$." (Observations); z/distance 235 pc  
  > "located in the NGC 1333 star-forming region in the Perseus Molecular Cloud at a distance of 235 pc ((cite: Hirota08))" (Introduction); "The continuum peak is derived to be at $(\alpha_{2000},\delta_{2000})=(3^{\mathrm{h}}29^{\mathrm{m}}13^{\mathrm{s}}.55$, $+31^\circ13\ensuremath{'}58\ensuremath{''}.11)$." (Observations); distance from Hirota08  
  > "located in the NGC 1333 star-forming region in the Perseus Molecular Cloud at a distance of 235 pc ((cite: Hirota08))" (Introduction); "The continuum peak is derived to be at $(\alpha_{2000},\delta_{2000})=(3^{\mathrm{h}}29^{\mathrm{m}}13^{\mathrm{s}}.55$, $+31^\circ13\ensuremath{'}58\ensuremath{''}.11)$." (Observations)

## Data provenance

- ALMA projects: 2016.1.01501.S
- bands: Band 6  
  > "The observations were carried out in ALMA band 6 for four times from Nov. 26 to Nov. 30, 2016." (Observations)
- frequencies and spectral setup: velocity resolution about 0.14 km/s  
  > "The molecular lines were observed with velocity resolutions of about 0.14 $\mbox{km s}^{-1}$." (Observations)
- continuum bandwidth: 938 MHz spectral window  
  > "a spectral window with a bandwidth of 938 MHz was used to map the 1.3 mm continuum." (Observations)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 to 700 m; 40 to 42 antennas  
  > "40 to 42 antennas were used and the baselines range from 15 to 700 m." (Observations)
- angular resolution: continuum 0.65" x 0.41" (PA -6.8 deg); lines in Table 1  
  > "The resulting synthesized beam of the continuum data is $0.65\ensuremath{''} \times 0.41\ensuremath{''}$ ($\mathrm{P.A.}=-6.8^\circ$)" (Observations)
- max recoverable scale: about 4"  
  > "The largest recoverable scale is about $4\ensuremath{''}$." (Observations)
- sensitivity: _not stated_
- time on source: 10 min per source  
  > "The total integration time per source is 10 min." (Observations)
- observing dates: Nov. 26 to Nov. 30, 2016  
  > "The observations were carried out in ALMA band 6 for four times from Nov. 26 to Nov. 30, 2016." (Observations)
- pi or archival as stated: PEACHES, PI N. Sakai  
  > "Perseus ALMA Chemical Survey (PEACHES; ALMA project 2016.1.01501.S; PI: N. Sakai)" (Observations)
- Line: CCH N=3-2, J=5/2-3/2, F=3-2 (262.0649860 GHz)
- Line: CCH N=3-2, J=5/2-3/2, F=2-1 (262.0674690 GHz)
- Line: CS J=5-4 (244.9355565 GHz)
- Line: SO J_N=6_6-5_5 (258.2558259 GHz)
- External data: Dust opacity kappa_1.3mm=0.899 cm2/g  
  > "dust opacity of (cite: Ossenkopf94) ($\kappa_\mathrm{1.3mm}=0.899~\mathrm{cm}^2~\mathrm{g}^{-1}$)" (Results) [from (cite: Ossenkopf94)]
- External data: Line frequencies and parameters from CDMS  
  > "Information taken from the CDMS database ((cite: Muller05))" (Table 1) [from (cite: Muller05)]
- External data: Inclination about 25 deg from Segura-Cox et al.  
  > "to about $25^\circ$ between the disk plane and the line of sight ((cite: SeguraCox16))" (Introduction) [from (cite: SeguraCox16)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0238+1636 (bandpass J0237+2848, phase J0336+3218)  
  > "J0237+2848 was used as the bandpass calibrator, J0238+1636 was used as the flux calibrators, and J0336+3218 was used as the phase calibrator." (Observations)
- flux scale uncertainty: _not stated_
- self calibration: phase and amplitude self-cal on continuum, applied to line data  
  > "Self-calibration to the phase and amplitude was performed using the continuum data after the normal calibration, and applied to the molecular line data." (Observations)

### Imaging

- task: CLEAN in CASA  
  > "The CLEAN algorithm was used to image the data." (Observations)
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "Robust weighting with the robust parameter of 0.5 was used in the clean process." (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: own clean region per channel around brightest emission  
  > "For the spectral data we defined its own clean region for each channel, encircling the area with the brightest emission." (Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: continuum 0.65"x0.41"; lines 0.64x0.41 (CCH, SO), 0.68x0.43 (CS)  
  > "| CS | $J=5-4$ | 244.9355565 | 35.3 | 19.17 | $0.68\ensuremath{''}\times0.43\ensuremath{''}$ ($\mathrm{P.A.}=-6.8^\circ$) |" (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- Launching radius derived following Anderson et al. method (Eq. 4)  
  > "following the method of (cite: Anderson03) (their Eq. 4)" (4.2.3 Launching Radius) [from (cite: Anderson03)]
- Magnetic lever arm via Eq. 10 of Ferreira et al.  
  > "Following Eq. 10 of (cite: Ferreira06), we derive the magnetic lever arm $\lambda$" (4.2.3 Launching Radius) [from (cite: Ferreira06)]
- Protostellar mass from centrifugal barrier M=V^2R/(2G)  
  > "Following (cite: Sakai14), we then estimate the protostellar mass to be $M_*=V_\mathrm{CB}^2 R_\mathrm{CB}/(2G)\approx0.18~M_\odot$" (4.3) [from (cite: Sakai14)]

### Not stated but needed to reproduce (our reading)

- CASA version and whether the pipeline or manual calibration was used
- Self-calibration solution intervals and number of iterations
- Flux calibrator flux density and calibration uncertainty
- Cell size, image size, clean threshold, deconvolver
- Continuum-free channels / continuum subtraction method
- Exact peak-finding procedure and uncertainties per z cut in the PV diagrams
- Whether primary beam correction was applied
- Exact outflow axis center used and Anderson03 equation implementation details

## Analysis recipe

1. **Calibrate and image continuum and line data**: CASA calibration, phase+amplitude self-cal on continuum applied to lines, CLEAN imaging  
  > "The data were calibrated and imaged in CASA ((cite: McMullin07))." (Observations)
   - software: CASA
   - parameter: robust = 0.5  
  > "Robust weighting with the robust parameter of 0.5 was used in the clean process." (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Continuum mass**: Total flux above 3 sigma within 2" converted to mass  
  > "The total continuum flux above $3\sigma$ within a radius of 2$\ensuremath{''}$ is 95 mJy, which corresponds to a mass of 0.061 $M_\odot$" (3.1)
   - assumption: T=30 K, kappa_1.3mm=0.899 cm2/g (Ossenkopf94), gas-to-dust 100  
  > "assuming a temperature of 30 K, dust opacity of (cite: Ossenkopf94) ($\kappa_\mathrm{1.3mm}=0.899~\mathrm{cm}^2~\mathrm{g}^{-1}$), and the standard gas-to-dust mass ratio of 100." (3.1)
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure outflow rotation and specific angular momentum from PV cuts**: PV cuts perpendicular to the outflow axis at each z; locate emission peaks of northern and southern walls; derive R_out, V_rot, j=R_out V_rot  
  > "The specific angular momentum is then $j(z)=R_\mathrm{out}(z)V_\mathrm{rot}(z)$." (4.2.2)
   - parameter: cuts 0.5" wide, z=+0.5" to +6" (east), peaks defined as 0.9x peak intensity, PA of axis 96 deg  
  > "Each cut has a width of 0.5$\ensuremath{''}$ and has a distance to the central source ranging from $z=+0.5\ensuremath{''}$ to $z=+6\ensuremath{''}$" (4.2.1)
   - assumption: edge-on inclination for rotation velocity  
  > "Assuming an edge-on inclination, the rotation velocity is $V_\mathrm{rot}(z)=[V_\mathrm{lsr,S}(z)-V_\mathrm{lsr,N}(z)]/2$" (4.2.2)
   - fitting: parabolic cavity shape z=0.79R^2+0.089  
  > "The shape of the CCH outflow cavity can be described by a parabolic function $z=0.79R^2+0.089$ with both $z$ and $R$ in arcsec." (4.2.2)
   - validation: uncertainties from velocity dispersions and wall widths  
  > "we calculate the velocity dispersions of the emission relative to $V_\mathrm{lsr,N}$ and $V_\mathrm{lsr,S}$ as the uncertainties in velocities" (4.2.2)
4. **Derive launching radius and magnetic lever arm**: Anderson03 method using R_out, V_rot, V_p, protostar mass; lever arm from Ferreira06  
  > "can be constrained by the outflow radius $R_\mathrm{out}$, the rotation velocity $V_\mathrm{rot}$, and the poloidal velocity of the outflow $V_p$, combined with the protostellar mass $m_*$" (4.2.3)
   - parameter: V_p = 1, 3, 10, 30 km/s; m* = 0.1, 0.2, 0.4 Msun  
  > "We adopt four values of $V_p$ (1, 3, 10 and 30 $\mbox{km s}^{-1}$) in the calculation." (4.2.3)
   - assumption: inclination 5-25 deg; fiducial mass 0.2 Msun  
  > "which we adopt as the fiducial value of the protostellar mass." (4.2.3)
   - fitting: _not stated_
   - validation: _not stated_
5. **Centrifugal barrier and protostellar mass**: CS highest velocity/position (method 1) and SO outer radius and max velocity (method 2) in mid-plane PV diagrams; M=V^2R/(2G)  
  > "we use the highest velocity seen in CS and its position as the velocity and radius of the centrifugal barrier" (4.3)
   - assumption: CS traces envelope outside barrier; SO enhanced at barrier  
  > "assuming that CS only traces the envelope outside of the centrifugal barrier" (4.3)
   - fitting: _not stated_
   - validation: two independent estimates give same mass  
  > "$M_*=V_\mathrm{CB}^2 R_\mathrm{CB}/(2G)\approx0.18~M_\odot$ from both sets of estimations." (4.3)

## Software

- **CASA** : calibration, self-calibration and imaging  
  > "The data were calibrated and imaged in CASA ((cite: McMullin07))." (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean specific angular momentum of outflow | about 100 | std dev 40 | au km/s | 3 | The mean value of the specific angular momentum is about 100 $\mbox{au km s}^{-1}$ with a standard deviation of 40 $\mbox{au km s}^{-1}$. |
| Outflow axis position angle | 96 | not stated | deg | 3 | The position angle of this outflow axis is 96$^\circ$ |
| Rotation velocity at z=0.5" and 6" | 0.5 and 0.1 | not stated | km/s | 3 | from about 0.5 $\mbox{km s}^{-1}$ at $z=0.5\ensuremath{''}$ (120 au) to about 0.1 $\mbox{km s}^{-1}$ at $z=6\ensuremath{''}$ (1400 au) |
| Outflow median velocity | 7.5 | std 0.07 | km/s | 3 | with a mean value of about 7.5 $\mbox{km s}^{-1}$ and standard deviation of 0.07 $\mbox{km s}^{-1}$ |
| Launching radius (V_p=3 km/s, 0.2 Msun) | 15 | std 7 | au | 4 | mean value of 15 au and a standard deviation of 7 au for the case of $V_p=3~\mbox{km s}^{-1}$ |
| Launching radius (V_p=10 km/s, 0.2 Msun) | 5.6 | std 1.8 | au | 4 | a mean value of 5.6 au and a standard deviation of 1.8 au for the case of $V_p=10~\mbox{km s}^{-1}$ |
| Continuum flux within 2" | 95 | not stated | mJy | 2 | The total continuum flux above $3\sigma$ within a radius of 2$\ensuremath{''}$ is 95 mJy |
| Continuum mass | 0.061 | not stated | Msun | 2 | which corresponds to a mass of 0.061 $M_\odot$ |
| Centrifugal barrier radius (CS / SO methods) | 50 / 140 | not stated | au | 5 | which gives $V_\mathrm{CB1}=2.5~\mbox{km s}^{-1}$ and $R_\mathrm{CB1}=0.2\ensuremath{''}$, i.e. 50 au |
| Protostellar mass from centrifugal barrier | 0.18 | not stated | Msun | 5 | $M_*=V_\mathrm{CB}^2 R_\mathrm{CB}/(2G)\approx0.18~M_\odot$ |

## Qualitative findings

- CCH traces the outflow cavity walls while CS traces envelope; CCH is absent on the disk/envelope mid-plane.  
  > "While the CCH emission appears to mostly trace the outflow cavity structure, the CS emission traces the envelope." (Conclusions)

## Claim tuples

- H: Is the IRAS 4C outflow rotating? | E: CCH PV cuts perpendicular to the outflow axis | R: Northern wall blue-shifted, southern red-shifted; V_rot 0.5 to 0.1 km/s from 120 to 1400 au | F: The outflow rotates about its axis with flat specific angular momentum ~100 au km/s | **supported**
- H: Is the outflow an X-wind or a disk wind? | E: Launching radius from angular momentum with assumed V_p and protostar mass | R: Launching radii 5-15 au (1-50 au with uncertainties) | F: Consistent with a slow disk wind from relatively large radii, not an X-wind | **supported**
- H: Does the centrifugal barrier relate to outflow launching? | E: CS and SO PV diagrams along the mid-plane | R: Barrier radius 50-140 au versus launching 5-15 au | F: Link unclear given resolution and different radii | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Measuring outflow rotation constrains launching radii since transferred angular momentum depends on launching radius  
  > "by measuring the outflow rotation, one can constrain the launching radii of the outflow." (Introduction)
- Alternative: Entrained outflow rejected because of the smooth, clear rotation over large distances  
  > "the fact that we detect clear and smooth distribution of rotation over a large distance suggests that what we detected is unlikely to be an entrained outflow." (4.1)
- Alternative: Infall explanation for CCH disfavored  
  > "Therefore, the CCH emission in this source, at least in the part distant from the disk mid-plane, is most likely tracing the outflowing gas." (4.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Resolution insufficient to resolve the launching region or the centrifugal barrier; estimates highly uncertain.  
  > "Therefore the above estimated radius and specific angular momentum are highly uncertain." (Conclusions)
- Limitation (authors): Interferometer recovers about 1/3 of single-dish CCH flux.  
  > "our ALMA observation covers about 1/3 of the single dish fluxes." (4.1)
- Caveat (inferred, ours): Launching radius depends strongly on assumed V_p, inclination and mass, not measured
- Caveat (inferred, ours): Only ~10 min per source at ~0.5" resolution; rotation of 0.1-0.5 km/s is near the 0.14 km/s channel width
- Caveat (inferred, ours): Peak-picking from PV diagrams may be affected by cavity-wall geometry and expanding shell or infall contamination
- Caveat (inferred, ours): Edge-on assumption for V_rot

## Reproducibility

- Data public (paper): ALMA project data acknowledged; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.01501.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and exact imaging parameters
- Missing: Self-cal details
- Missing: Peak-finding and uncertainty procedure for the PV analysis
- Missing: Exact implementation of Anderson03 equation inputs
- Data volume (inferred): ~50-100 GB raw for the PEACHES project; a few GB for this single source
- Score (inferred): 3/5, Data and many settings are given, but the CASA version, self-cal details and manual peak-picking are unspecified; the analysis is simple and numeric.
- Rediscovery candidate: yes, The archival ALMA data are linked to the paper, the recipe (imaging, PV cuts, formulas) is mostly specified, and the results are numeric.

## Links

- Method: (cite: Anderson03) (Launching radius method)
- Method: (cite: Ferreira06) (Magnetic lever arm)
- Method: (cite: Sakai14) (Centrifugal barrier and mass estimate)
- Companion: (cite: Higuchi17) (IRAM 30 m CCH observations and systemic velocity)
- Companion: (cite: Tobin15) (Previous IRAS 4C observations and inclination/outflow axis)
- Related: PEACHES (Perseus ALMA Chemical Survey)

## Checks

```json
{
 "quotes": 71,
 "quotes_ok": 71,
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
  "facts": 77,
  "stated": 48,
  "rate": 0.623
 },
 "evidence_ok": true
}
```

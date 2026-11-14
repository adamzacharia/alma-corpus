# The fast molecular outflow in the Seyfert galaxy IC 5063 as seen by ALMA

`2015A&A...580A...1M` | Astronomy and Astrophysics 2015 | first author: Morganti, Raffaella | arXiv: 1505.07190 | DOI: 10.1051/0004-6361/201525860

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: Where and how does the cold molecular gas outflow in IC 5063 relate to the radio jet, and how massive is it?  
  > "The limited spatial resolution of these observations did not allow to determine where the outflow is occurring in relation to the radio structure and the main goal of the ALMA data presented in this paper is to remedy this situation." (A case study: IC 5063)
- Target **IC 5063**: coordinates _not stated_; z/distance 47.9 Mpc (angular scale distance); 1 arcsec = 232 pc  
  > "we use an angular scale distance to IC 5063 of 47.9 Mpc, implying a scale of 1 arcsec = 232 pc." (footnote 1); distance from H0 = 70 km/s/Mpc, Omega_Lambda=0.7, Omega_M=0.3  
  > "we use an angular scale distance to IC 5063 of 47.9 Mpc, implying a scale of 1 arcsec = 232 pc." (footnote 1)

## Data provenance

- ALMA projects: 2012.1.00435.S
- bands: Band 6  
  > "using Band 6, covering simultaneously the CO(2-1) centered on 227.968 GHz and two additional base-bands (at 232 and 247 GHz) for imaging of the continuum." (The ALMA data)
- frequencies and spectral setup: CO(2-1) at 227.968 GHz; continuum basebands at 232 and 247 GHz; CS(5-4) in a fourth baseband; 1.875 GHz bandwidth; 976.5 kHz (1.28 km/s) resolution  
  > "The frequency resolution was 976.5 kHz (1.28 $\,$km$\,$s$^{-1}$), but channels were combined when making the image cube" (The ALMA data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: 31 antennas, maximum baseline 1.5 km  
  > "The observation made use of 31 antennas with a maximum baseline of 1.5 km." (The ALMA data)
- baselines: _not stated_
- angular resolution: 0.54 x 0.45 arcsec (PA = -31.7 deg) for line; 0.45 x 0.42 arcsec for continuum  
  > "resolution of the line data of $0.54 \times 0.45$ arcsec (PA $= -31.7^{\circ}$)" (The ALMA data)
- max recoverable scale: _not stated_
- sensitivity: line rms ~0.3 mJy/beam per 20 km/s channel; continuum rms 30 uJy/beam  
  > "the r.m.s. noise per channel is $\sim 0.3$ mJy beam$^{-1}$." (The ALMA data); "The r.m.s. noise of the continuum image is 30 $\mu$Jy beam$^{-1}$." (The ALMA data)
- time on source: 1 h duration  
  > "The duration of the observations was 1 h" (The ALMA data)
- observing dates: 27 May 2014 (Cycle 1)  
  > "IC 5063 was observed during Cycle 1 on the 27 May 2014" (The ALMA data)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (227.968 GHz (band centre))
- Line: CS 5-4 (242.205 GHz)
- Other facility **ATCA**: 17 and 24 GHz radio continuum used for spectral indices; H i disk  
  > "(17 and 24 GHz with the ATCA) presented and discussed in (cite: Morganti2007)" (4.5 The radio continuum)
- Other facility **HST**: photometry from Kulkarni et al. used for the rotation curve  
  > "We have modelled the rotation of the regular CO distribution using the HST photometry of (cite: Kulkarni1998)." (4.3 The regularly rotating CO disk)
- External data: 17 GHz radio continuum fluxes of E, core, W components  
  > "Using the present and the previous radio continuum observations, we have derived the spectral indices of the three components." (4.5 The radio continuum) [from (cite: Morganti2007)]
- External data: HST photometry (de Vaucouleurs law, effective radius 21.5 arcsec)  
  > "shows that the unobscured light distribution of the inner regions of IC 5063 can accurately be described using a de Vaucouleurs’ law" (4.3 The regularly rotating CO disk) [from (cite: Kulkarni1998)]
- External data: AGN bolometric luminosity 7.7e44 erg/s  
  > "The bolometric luminosity of the AGN is estimated to be $L^{\rm bol}_{\rm AGN} = 7.7 \times 10^{44}$ $\,$erg$\,$s$^{-1}$ (cite: Morganti2007)" (5.3 The power source of the outflow) [from (cite: Morganti2007)]

## Processing

### Calibration

- pipeline or manual: Initial calibration in CASA with ALMA reduction scripts; self-calibration in MIRIAD  
  > "The initial calibration was done in CASA (cite: McMullin2007) using the ALMA reduction scripts." (The ALMA data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Additional self-calibration in MIRIAD improved images significantly  
  > "which was used to perform additional self-calibration which improved the quality of the images significantly." (The ALMA data)

### Imaging

- task: continuum subtraction and mapping/cleaning in MIRIAD  
  > "All further reduction steps (continuum subtraction, mapping/cleaning) were also done in MIRIAD." (The ALMA data)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0 for line cubes; uniform weighting for continuum  
  > "Here we present the final data cubes obtained using Briggs robust = 0." (The ALMA data); "A continuum image was also produced from the 2 additional basebands using uniform weighting." (The ALMA data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied to integrated total flux  
  > "The integrated total flux (after primary beam correction) corresponds to $76.4 \pm 3.8$ Jy $\,$km$\,$s$^{-1}$." (4.4 Molecular gas masses)
- array combination: _not stated_
- smoothing: Hanning smoothing; 20 km/s velocity resolution  
  > "The line cube was produced using a velocity resolution, after Hanning smoothing, of 20 $\,$km$\,$s$^{-1}$." (The ALMA data)
- final beam: 0.54 x 0.45 arcsec, PA -31.7 deg (line)  
  > "resolution of the line data of $0.54 \times 0.45$ arcsec (PA $= -31.7^{\circ}$)" (The ALMA data)
- final rms: ~0.3 mJy/beam per channel (line); 30 uJy/beam (continuum)  
  > "The r.m.s. noise of the continuum image is 30 $\mu$Jy beam$^{-1}$." (The ALMA data)

### Inherited from earlier work

- L'CO(2-1)/L'CO(1-0)=1 assumption for H2 masses  
  > "As for the APEX data presented in (cite: Morganti2013b), we estimate the H$_2$ masses by assuming a luminosity ratio $L^{\prime}$CO(2-1)/$L^{\prime}$CO(1-0) = 1" (4.4 Molecular gas masses) [from (cite: Morganti2013b)]
- Kinetic power formula including radial and turbulent components  
  > "The kinetic power of the outflowing gas can be estimated using the formula in (cite: Holt2006)" (5.3 The power source of the outflow) [from (cite: Holt2006)]
- Geometrical ring-based kinematic modelling technique  
  > "we employ a geometrical modelling technique often used for modelling the kinematics of gas disks in galaxies (cite: Jozsa2007)" (5.2 Modeling of the kinematics of the gas) [from (cite: Jozsa2007)]
- Jet power formulae with normalisation factor f=10  
  > "We estimate the jet power using the formulae given in (cite: Willot1999), (cite: Wu2009) and (cite: Cavagnolo2010)" (5.3 The power source of the outflow) [from (cite: Willot1999), (cite: Wu2009), (cite: Cavagnolo2010)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for MIRIAD continuum subtraction
- Self-calibration solution intervals and number of iterations
- Clean mask, threshold and iteration count
- Velocity ranges defining anomalous versus regular gas in the cube
- Mask/region definitions for the radio-co-spatial and W-lobe fluxes
- Model code and exact ring parameters (density, radial profile, ring radii) for the kinematic model
- Flux calibrator and ALMA flux scale uncertainty
- CASA version
- Exact conversion used from Jy km/s to H2 mass (line frequency, distance)

## Analysis recipe

1. **Calibrate and image the data**: CASA initial calibration, then MIRIAD self-calibration, continuum subtraction and cleaning; Briggs robust 0 cube, Hanning smoothed to 20 km/s  
  > "These calibrated $uv$ data were subsequently exported to MIRIAD (cite: Sault1995) which was used to perform additional self-calibration" (The ALMA data)
   - software: CASA, MIRIAD
   - parameter: robust = 0; 20 km/s channels  
  > "Here we present the final data cubes obtained using Briggs robust = 0." (The ALMA data)
   - fitting: _not stated_
   - validation: Different Briggs weightings tried; no major differences  
  > "However, the images did not show any major differences (owing to the good $uv$ coverage of ALMA)." (The ALMA data)
2. **Build position-velocity diagram and compare with rotation curve**: pv diagram along the major axis integrated over 2 arcsec perpendicular; overplot rotation curve from de Vaucouleurs HST light profile, light traces mass, spherical, amplitude matched to outer regions  
  > "we have integrated the data over a length of 2$''$ in the direction perpendicular to the major axis." (4.1 A complex, extended outflow of molecular gas)
   - parameter: effective radius 21.5 arcsec (4.3 kpc)  
  > "The horizontal scale of the rotation curve is set by the observed effective radius (21$''$5 corresponding to 4.3 kpc)" (4.3 The regularly rotating CO disk)
   - assumption: light traces mass; spherical mass distribution  
  > "we have assumed that the light traces the mass distribution and that the mass distribution is spherical." (4.3 The regularly rotating CO disk)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive molecular gas masses**: Integrated fluxes of total, radio-co-spatial, anomalous and W-lobe gas converted to H2 mass with X_CO  
  > "we derive masses for the anomalous molecular gas ranging between $1.9$ and $4.8 \times 10^7$ $M_\odot$" (4.4 Molecular gas masses)
   - parameter: X_CO = 0.4e20 (alpha_CO 0.8) to 0.2e20 (alpha_CO 0.34) for outflow; 2e20 (alpha_CO 4.6) for regular gas  
  > "assuming an $X_{\rm CO}$ conversion factor equal to $2 \times 10^{20}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$ (corresponding to $\alpha_{\rm CO} = 4.6$, typical for the Milky Way)" (4.4 Molecular gas masses)
   - assumption: L'CO(2-1)/L'CO(1-0) = 1  
  > "assuming a luminosity ratio $L^{\prime}$CO(2-1)/$L^{\prime}$CO(1-0) = 1" (4.4 Molecular gas masses)
   - fitting: _not stated_
   - validation: _not stated_
4. **Measure continuum fluxes and spectral indices**: Fluxes at 228 GHz for E, core, W components combined with 17 GHz ATCA fluxes to derive spectral indices  
  > "The total fluxes of the three components at 17 and 228 GHz are listed in Table[1](#tab:radio), together with the derived spectral indices." (4.5 The radio continuum)
   - assumption: S proportional to nu^-alpha  
  > "$S\propto \nu^{-\alpha}$" (4.5 The radio continuum)
   - fitting: _not stated_
   - validation: _not stated_
5. **Geometric kinematic model of jet-driven lateral expansion**: Concentric elliptical rings with orientation, density, rotation and radial velocity; model cube compared qualitatively to the pv diagram  
  > "each ring has an orientation, a density, and a rotation- and radial velocity." (5.2 Modeling of the kinematics of the gas)
   - parameter: inclination 80 deg, PA 115 deg; lateral expansion up to 200 km/s; ring R rotation ~50 km/s at r=2 arcsec vs nominal 170 km/s  
  > "For the inclination of the rings, we choose 80$^\circ$ and for the position angle 115$^\circ$." (5.2 Modeling of the kinematics of the gas)
   - assumption: jet in the plane of the sky (lower limit on expansion velocity); uniform density for O and R; large-scale disk D excluded  
  > "We have therefore chosen to consider only models for which the jet is moving the plane of the sky" (5.2 Modeling of the kinematics of the gas)
   - fitting: No numerical fit; qualitative match to locations of emission in the pv diagram  
  > "the quality of a fit is not assessed using a numerical goodness-of-fit criterion such, e.g., a $\chi^2$." (5.2 Modeling of the kinematics of the gas)
   - validation: Radial-expansion and circular-shape variants tested and found worse  
  > "We found, however, that such models do not reproduce the observed $pv$ diagram very well." (5.2 Modeling of the kinematics of the gas)
6. **Outflow rate and energetics**: Mdot = M/tau_dyn; kinetic power from Holt et al. formula; compare with AGN bolometric luminosity and jet power  
  > "we derive the mass outflow rate using $\dot{M} = M/\tau_{\rm dyn}$" (5.3 The power source of the outflow)
   - parameter: r = 0.3 kpc, v = 200 km/s, tau_dyn ~1.5e6 yr; v_turb ~ FWHM ~100 km/s  
  > "This gives $\tau_{\rm dyn} \simeq 1.5\times 10^6$ yr" (5.3 The power source of the outflow)
   - assumption: turbulence represented by line FWHM present throughout the outflow  
  > "we have assumed that the relatively large line-width of the outflowing gas reflects a turbulent motion that is present at all locations in the outflow region." (5.3 The power source of the outflow)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Initial calibration with ALMA reduction scripts  
  > "The initial calibration was done in CASA (cite: McMullin2007) using the ALMA reduction scripts." (The ALMA data)
- **MIRIAD** : Self-calibration, continuum subtraction, mapping and cleaning  
  > "All further reduction steps (continuum subtraction, mapping/cleaning) were also done in MIRIAD." (The ALMA data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total CO(2-1) integrated flux | 76.4 | 3.8 | Jy km/s | 3 | The integrated total flux (after primary beam correction) corresponds to $76.4 \pm 3.8$ Jy $\,$km$\,$s$^{-1}$. |
| Flux of gas co-spatial with radio | 38.9 | 1.9 | Jy km/s | 3 | The flux of the gas in the region co-spatial with the radio is $38.9 \pm 1.9$ Jy |
| Flux of anomalous-velocity gas | 10.0 | 0.5 | Jy km/s | 3 | of which $10.0 \pm 0.5$ Jy $\,$km$\,$s$^{-1}$are associated with gas with anomalous velocities |
| Anomalous gas flux at W lobe | 2.7 | 0.3 | Jy km/s | 3 | The anomalous gas at the location of the W lobe has a flux of about $2.7 \pm 0.3$ Jy $\,$km$\,$s$^{-1}$. |
| Outflowing molecular gas mass | 1.9 to 4.8 e7 | range from X_CO choice | Msun | 3 | we derive masses for the anomalous molecular gas ranging between $1.9$ and $4.8 \times 10^7$ $M_\odot$ |
| Regular gas H2 mass outside radio region | 1.0 - 1.1 e9 | not stated | Msun | 3 | to be in the range $M_{\rm H_2} = 1.0 - 1.1 \times 10^9$ $M_\odot$ |
| Mass outflow rate | 12 to 30 | range from X_CO | Msun/yr | 6 | we obtained $\dot{M}$ to lie in the range 12 to 30 $M_\odot$ yr$^{-1}$ |
| Kinetic power of outflow (H i + CO) | ~5e42 | not stated | erg/s | 6 | this gives a kinetic power of the outflow of $\sim 5 \times 10^{42}$ $\,$erg$\,$s$^{-1}$. |
| Spectral index E lobe / core / W lobe (17-228 GHz) | 0.87 / 0.33 / 0.9 (table 0.93 for W) | not stated | dimensionless | 4 | $\alpha = 0.87$ for the E lobe and $\alpha = 0.9$ for the W lobe |
| Jet power | 5e43 to 9e43 | not stated | erg/s | 6 | we obtain values between $5 \times 10^{43}$ $\,$erg$\,$s$^{-1}$ and of $9 \times 10^{43}$ $\,$erg$\,$s$^{-1}$ |

## Qualitative findings

- Bright CO wraps around the radio continuum, brightest at the W lobe  
  > "Figure [2](#fig:ContCO) illustrates how the CO bright emission wraps around the radio continuum" (4 Results)

## Claim tuples

- H: Is the cold molecular outflow driven by the radio jet interacting with the ISM? | E: CO(2-1) pv diagram and a geometric lateral-expansion model | R: Anomalous gas lies along the radio jet; model with lateral expansion up to 200 km/s reproduces the S-shape | F: The radio jet pushes a clumpy medium and drives the outflow, with direct interaction at the W hot spot | **supported**
- H: How massive is the cold molecular outflow relative to other phases? | E: Convert anomalous CO flux to H2 mass with conservative X_CO | R: 1.9-4.8e7 Msun, Mdot 12-30 Msun/yr | F: Molecular outflow exceeds H i outflow mass | **supported**
- H: Can the AGN or the jet power the outflow? | E: Compare kinetic power with AGN luminosity and jet power | R: Required efficiency >0.6% for AGN, 0.05-0.1 for jet | F: Both can power it; kinematics favour the jet | **partially**
- H: Will the outflowing gas escape the galaxy? | E: Compare observed velocities with escape velocity | R: Almost no gas above ~550 km/s | F: Gas is redistributed rather than removed | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Qualitative model comparison because of asymmetry; few free parameters  
  > "Therefore we have not attempted to replicate the fine details of the brightness distribution" (5.2 Modeling of the kinematics of the gas)
- Alternative: Radial expansion from the centre (AGN-driven) did not reproduce the pv diagram  
  > "We found, however, that such models do not reproduce the observed $pv$ diagram very well." (5.2 Modeling of the kinematics of the gas)
- How they decided it was enough: _not stated_
- Limitation (authors): Only one molecular line, so excitation mechanisms cannot be discriminated; X_CO uncertain  
  > "we not able to discriminate between these different processes." (4.2 The bright inner CO(2-1) distribution)
- Limitation (authors): Jet orientation degenerate with lateral expansion velocity  
  > "We found, however, this parameter to be strongly degenerate with the outflow velocity of component $O$" (5.2 Modeling of the kinematics of the gas)
- Caveat (inferred, ours): Mass range depends strongly on assumed X_CO and the CO(2-1)/(1-0) ratio
- Caveat (inferred, ours): Model is qualitative with no goodness-of-fit or uncertainties
- Caveat (inferred, ours): Boundary between anomalous and regular gas is not defined quantitatively
- Caveat (inferred, ours): Table gives W-lobe alpha 0.93 while text says 0.9

## Reproducibility

- Data public (paper): ALMA project code cited in acknowledgements  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00435.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Self-calibration and cleaning parameters
- Missing: Region/velocity masks for flux measurements
- Missing: Kinematic model code and full parameters
- Data volume (inferred): ~10-50 GB raw for one 1 h Band 6 execution
- Score (inferred): 3/5, Data public and flux/mass steps simple, but masks, self-cal and the model are underspecified.
- Rediscovery candidate: no, Key results depend on unspecified velocity/region masks and a qualitative model.

## Links

- Method: (cite: Jozsa2007) (geometrical ring modelling technique)
- Method: (cite: Holt2006) (kinetic power formula)
- Companion: (cite: Tadhunter2014) (warm molecular outflow in IC 5063)
- Companion: (cite: Morganti2013b) (APEX CO(2-1) of IC 5063)
- Companion: (cite: Morganti2007) (ionized gas and ATCA continuum of IC 5063)
- Related: Wagner & Bicknell jet-clumpy ISM simulations

## Checks

```json
{
 "quotes": 74,
 "quotes_ok": 74,
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
  "facts": 86,
  "stated": 54,
  "rate": 0.628
 },
 "evidence_ok": true
}
```

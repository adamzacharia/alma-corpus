# Molecular and Ionized Gas Phases of an AGN-driven Outflow in a Typical Massive Galaxy at z ≈ 2

`2019ApJ...871...37H` | The Astrophysical Journal 2019 | first author: Herrera-Camus, R. | arXiv: 1807.07074 | DOI: 10.3847/1538-4357/aaf6a7

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: What are the extent, mass and energetics of the molecular and ionized phases of the AGN-driven outflow in zC400528 at z=2.39, and can the outflow quench the galaxy?  
  > "The main goal of our observations was to detect and spatially resolve the molecular gas outflow in zC400528 using the redshifted CO(3-2) line emission as a tracer of molecular gas." (Observations and Data Reduction)
- Target **zC400528**: coordinates R.A.=09:59:47.6, Decl.=+01:44:19.0  
  > "zC400528 (R.A.$=09:59:47.6$, Decl.$=+01:44:19.0$) is a massive ($M_{\star}=1.1\times10^{11}~M_{\odot}$)" (zC400528); "galaxy at $z=2.3873$ (cite: rhc_f-s18)" (zC400528); z/distance z=2.3873  
  > "zC400528 (R.A.$=09:59:47.6$, Decl.$=+01:44:19.0$) is a massive ($M_{\star}=1.1\times10^{11}~M_{\odot}$)" (zC400528); "galaxy at $z=2.3873$ (cite: rhc_f-s18)" (zC400528); distance from Förster Schreiber et al. 2018 (cite: rhc_f-s18)  
  > "zC400528 (R.A.$=09:59:47.6$, Decl.$=+01:44:19.0$) is a massive ($M_{\star}=1.1\times10^{11}~M_{\odot}$)" (zC400528); "galaxy at $z=2.3873$ (cite: rhc_f-s18)" (zC400528)

## Data provenance

- ALMA projects: 2013.1.00092.S, 2015.1.00220.S
- bands: Band 3  
  > "resulting in an angular resolution of $0.4\ensuremath{''} \times 0.3\ensuremath{''}$ in Band 3." (Observations and Data Reduction)
- frequencies and spectral setup: one spectral window centered on redshifted CO(3-2), nu_obs=102.004 GHz  
  > "the spectral setup included one of the spectral windows in Band 3 centered around the redshifted CO(3-2) line emission ($\nu_{\rm obs}=102.004$ GHz)" (Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C34-5/6 (Cycle 2) and C40-6 (Cycle 3)  
  > "The observations were carried out in the C34-5/6 configuration" (Observations and Data Reduction); "in a more extended configuration, C40-6" (Observations and Data Reduction)
- baselines: _not stated_
- angular resolution: 0.51'' x 0.47'' (4.2x3.9 kpc) combined beam  
  > "The size of the restoring beam of the combined data was $0.51\ensuremath{''}\times 0.47\ensuremath{''}$ ($4.2\times3.9$ kpc)" (Observations and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: rms 0.08 mJy/beam in 50 km/s channels  
  > "We reached an rms noise of 0.08 mJy beam$^{-1}$ in 50 km s$^{-1}$ channels for CO(3-2)." (Observations and Data Reduction)
- time on source: Cycle 2: 0.6 h on-source; Cycle 3: 4.5 h on-source  
  > "The total observation time was 5.4 hours (4.5 hours on-source)." (Observations and Data Reduction)
- observing dates: _not stated_
- pi or archival as stated: Projects PI R. Genzel; used as archival data  
  > "as part of project 2013.1.00092.S (PI R. Genzel)" (Observations and Data Reduction)
- Line: CO 3-2 (not stated (observed 102.004 GHz))
- Other facility **VLT/SINFONI**: K-band AO Halpha and [N II] IFU data, 4 hr on-source, 0.15'' PSF  
  > "The achieved angular resolution (PSF FWHM) of the final reduced data was 0.15$''$." (Observations and Data Reduction)
- Other facility **HST**: H-band image tracing stellar mass  
  > "the stellar mass traced by the *HST* $H$-band (cite: rhc_tacchella15)" (The molecular disk)
- External data: Ionized outflow mass 2.2e8 Msun (300/ne), outflow velocity 802 km/s  
  > "For an outflow size of $R_{\rm out,ion}=3$ kpc (cite: rhc_f-s14) and an outflow velocity of $v_{\rm out,ion}=802$ km s$^{-1}$ (cite: rhc_genzel14)" (Mass and energetics) [from Genzel et al. 2014 (cite: rhc_genzel14); Förster Schreiber et al. 2014 (cite: rhc_f-s14)]
- External data: Galaxy properties: z=2.3873, circular velocity 344 km/s, inclination 37 deg  
  > "using a circular velocity for zC400528 of $v_{\rm circ}=344$ km s$^{-1}$ (cite: rhc_f-s18)" (Can the outflowing material escape) [from (cite: rhc_f-s18)]
- External data: Local (U)LIRG and Seyfert outflow compilation  
  > "The plot includes zC400528 and a compilation of local (U)LIRG and Seyfert galaxies (cite: rhc_fiore17)." (Molecular mass outflow rate) [from Fiore et al. 2017 (cite: rhc_fiore17)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline-calibrated visibilities  
  > "The pipeline-calibrated interferometric visibilities delivered by ALMA from both cycles were then combined" (Observations and Data Reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: pipeline-calibrated visibilities delivered by ALMA used  
  > "The pipeline-calibrated interferometric visibilities delivered by ALMA from both cycles were then combined" (Observations and Data Reduction)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "imaged at 50 km s$^{-1}$ resolution using natural weighting" (Observations and Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied for all quantitative analyses  
  > "All values were primary beam corrected for all quantitative analyses." (Observations and Data Reduction)
- array combination: Cycle 2 and 3 visibilities combined, weights rescaled with STATWT  
  > "we took into account the different CASA visibility weights applied during Cycle 2 and 3 using the CASA task STATWT." (Observations and Data Reduction)
- smoothing: _not stated_
- final beam: 0.51'' x 0.47'', PA=-12.13 deg  
  > "at a position angle of ${\rm PA=-12.13^{\circ}}$" (Observations and Data Reduction)
- final rms: 0.08 mJy/beam per 50 km/s channel  
  > "We reached an rms noise of 0.08 mJy beam$^{-1}$ in 50 km s$^{-1}$ channels for CO(3-2)." (Observations and Data Reduction)

### Inherited from earlier work

- SINFONI Halpha/[N II] observations and reduction described elsewhere  
  > "we refer to (cite: rhc_f-s14)" (Observations and Data Reduction) [from Förster Schreiber et al. 2014 (cite: rhc_f-s14)]
- Disk-subtraction approach similar to earlier CO(1-0) outflow study  
  > "A similar approach was used by (cite: rhc_veilleux17) to study the molecular outflow in a luminous infrared galaxy using CO(1-0) observations." (Disentangling the molecular emission) [from (cite: rhc_veilleux17)]
- Outflow rate formalism (instantaneous vs average)  
  > "a detailed description of the assumptions that go into the calculations can be found in (cite: rhc_rupke05)" (Molecular mass outflow rate) [from (cite: rhc_rupke05)]
- Escape velocity from truncated isothermal sphere  
  > "For this we follow (cite: rhc_rupke02) and use a simple gravitational model" (Can the outflowing material escape) [from (cite: rhc_rupke02)]

### Not stated but needed to reproduce (our reading)

- Exact apertures and positions of outflow regions 1-4 (only in Figure 7)
- imfit region definitions and fitting initial guesses per channel
- Whether continuum was subtracted (none detected) and line-free channels
- Data weights and calibration versions (CASA/pipeline version)
- Cell size, image size and clean threshold
- Details of Gaussian fits to aperture spectra
- Whether the B-balance halo mass and accretion constants are re-derived

## Analysis recipe

1. **Combine and image ALMA data**: Combine Cycle 2 and 3 pipeline-calibrated visibilities, reweight with STATWT, image at 50 km/s with natural weighting  
  > "were then combined and imaged at 50 km s$^{-1}$ resolution using natural weighting" (Observations and Data Reduction)
   - software: CASA, STATWT
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure molecular disk flux and gas mass**: Integrated CO(3-2) flux converted to luminosity and mass with alpha_CO and R13  
  > "We measure an integrated CO(3-2) flux of $F_{\rm CO}=1.11\pm0.05$ Jy km s$^{-1}$" (The molecular disk)
   - assumption: alpha_CO=4.3 Msun/(K km/s pc^2), R13=1.3, helium factor 1.36  
  > "a velocity-integrated Rayleigh-Jeans brightness temperature line ratio $R_{13}=1.3$" (The molecular disk)
   - fitting: _not stated_
   - validation: _not stated_
3. **Separate outflow from rotating disk**: Fit 2D Gaussian per 50 km/s channel, build velocity-dependent source model, subtract to get residual cube  
  > "we use the CASA task IMFIT to fit in each 50 km s$^{-1}$ channel of the CO(3-2) cube a two-dimensional Gaussian" (Disentangling the molecular emission)
   - software: CASA imfit
   - fitting: 2D Gaussian per channel  
  > "we use the CASA task IMFIT to fit in each 50 km s$^{-1}$ channel of the CO(3-2) cube a two-dimensional Gaussian to the image in the region where the source is detected." (Disentangling the molecular emission from disk and outflow)
   - validation: Residual ~0.06 Jy km/s only in SE extended component; compared with two-Gaussian method giving 3.6e9 Msun  
  > "we only observe a relatively high residual at the level of $\sim$0.06 Jy km s$^{-1}$" (Disentangling the molecular emission)
4. **Outflow masses**: Gaussian fits to spectra from apertures in residual cube; mass with ULIRG alpha_CO=0.8  
  > "we measure CO(3-2) flux densities with Gaussian fits to the spectra in the residual cube extracted from the circular and elliptical apertures" (The molecular gas mass in the outflow)
   - assumption: alpha_CO,ULIRG=0.8 adopted; thin 0.34 and MW 4.3 as bounds  
  > "In this paper we adopt the ULIRG-like conversion factor ($\alpha_{\rm CO,ULIRG}$)" (The molecular gas mass in the outflow)
   - fitting: _not stated_
   - validation: _not stated_
5. **Mass outflow rate and energetics**: Average approach Mdot=M v/R with R=4.2 kpc, v=450 km/s; P=Mdot v; E=0.5 Mdot v^2  
  > "In this paper we use the *average* approach" (Molecular mass outflow rate)
   - assumption: No inclination correction in baseline; ~0.75 correction if perpendicular to disk with i~37 deg  
  > "the correction is small and of the order of $\sim0.75$" (Molecular mass outflow rate)
   - fitting: _not stated_
   - validation: Compared with two-Gaussian maximum-velocity method giving 180 Msun/yr  
  > "we calculate a mass loss rate of $\dot{M}_{\rm out}=180$ M$_{\odot}$ yr$^{-1}$" (Molecular mass outflow rate)
6. **Compare with ionized outflow, escape and quenching**: Ionized phase from literature with ne=300; escape velocity from truncated isothermal sphere; gas balance B using accretion rate  
  > "we can attempt to further explore the quenching scenario with a simple back-of-the-envelope calculation" (Is zC400528 moving down)
   - assumption: rmax=100 kpc, eps_in=0.7, fb=0.18, Mh~10^12.5 Msun  
  > "a halo mass of $M_{\rm h}\approx10^{12.5}~M_{\odot}$ (cite: rhc_moster13)" (Is zC400528 moving down)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Data processing, imaging, STATWT weighting, IMFIT  
  > "The data were processed using the Common Astronomy Software Applications package (cite: rhc_casa)." (Observations and Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Integrated CO(3-2) flux (disk) | 1.11 | 0.05 | Jy km/s | 2 | $F_{\rm CO}=1.11\pm0.05$ Jy km s$^{-1}$ |
| Molecular gas mass of disk | 1.1e11 | not stated | Msun | 2 | is $M_{\rm mol,disk}=1.1\times10^{11}~M_{\odot}$ |
| Total molecular outflow mass (ULIRG alpha_CO) | 3.36e9 | range 1.42-18.06e9 for other alpha_CO | Msun | 4 | /     4     /  $0.184\pm0.029$   /   3.36 $(1.42-18.06)$   /     /     /     / |
| Molecular mass outflow rate | 256 | range 108.8-1376 | Msun/yr | 5 | / Molecular$^{a}$ / 3.36 $(1.42-18.06)$ / 256 $(108.8-1376.0)$ / 7.2 $(3.1-38.7)$ / 1.6 $(0.68-8.6)$ / |
| Outflow depletion time | 4.7e8 | not stated | yr | 5 | \tau_{\rm dep,out}\approx4.7\times10^8~{\rm yr} |
| Molecular mass loading factor | 1.7 | not stated | dimensionless | 5 | ($\eta_{\rm mol}=1.7$) |
| Momentum boost | ~3 | not stated | dimensionless | 5 | the momentum boost is $\dot{P}_{\rm out,mol}/(L_{\rm AGN,bol}/c)\approx3$ |
| Ionized outflow rate | 53 | range 15.9-159 | Msun/yr | 6 | the ionized mass outflow rate is $\dot{M}_{\rm ion,out}=53$ M$_{\odot}~{\rm yr}^{-1}$ |
| Gas balance B | 0.6 | not stated | dimensionless | 6 | =0.6. |

## Qualitative findings

- Only a receding molecular outflow component is detected, extending to ~10 kpc, ~3 times the ionized wind size, with a positive velocity gradient  
  > "extends for at least $\sim$10 kpc from the nuclear region, about three times the projected size of the ionized wind" (abstract)
- Outflow velocity below escape velocity, so gas expected to be reaccreted  
  > "The molecular gas in the outflow does not reach velocities high enough to escape the galaxy" (abstract)

## Claim tuples

- H: Is there a molecular outflow in zC400528 and how large is it? | E: Disk-model subtraction of CO(3-2) cube and channel maps | R: Red wing at +300 to +500 km/s extending ~10 kpc, 3.36e9 Msun | F: A powerful, asymmetric molecular outflow is detected | **supported**
- H: Which phase dominates the outflow mass and energetics? | E: Compare molecular to literature ionized outflow | R: Molecular Mdot 256 vs ionized 53 Msun/yr | F: Molecular phase dominates, given assumptions | **partially**
- H: Can the outflow quench star formation? | E: Compare depletion timescales | R: Outflow depletion time ~2x shorter than SF depletion | F: Outflow is one of the main quenching engines | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: High spatial resolution and S/N allow channel-by-channel disk subtraction instead of two-Gaussian decomposition, which gives upper limits  
  > "Given that we have sufficient spatial resolution and signal-to-noise (S/N) in our ALMA CO(3-2) data, here we try a different strategy" (Disentangling the molecular emission)
- Alternative: Two-Gaussian decomposition gives M=3.6e9 Msun and Mdot=180 Msun/yr, consistent  
  > "Following this method we measure $M_{\rm out}=3.6\times10^{9}$ M$_{\odot}$ and $v_{\rm out,max}=590$ km s$^{-1}$." (Molecular mass outflow rate)
- How they decided it was enough: _not stated_
- Limitation (authors): Outflow properties depend on poorly constrained assumptions (alpha_CO, electron density, geometry)  
  > "these results depend on assumptions of the properties of the outflow gas that are not yet fully constrained" (Mass and energetics)
- Limitation (authors): Outflow geometry/inclination not constrained  
  > "we do not have enough information to constrain the geometry of the outflow" (Molecular mass outflow rate)
- Caveat (inferred, ours): Single galaxy; outflow wing detected at modest S/N (fluxes ~0.03-0.1 Jy km/s)
- Caveat (inferred, ours): Disk subtraction by Gaussian model may leave or remove outflow flux
- Caveat (inferred, ours): Order-of-magnitude uncertainty from alpha_CO choice drives conclusions
- Caveat (inferred, ours): Ionized mass taken from literature with different ne
- Caveat (inferred, ours): AGN bolometric luminosity uncertain by factor ~6 between methods

## Reproducibility

- Data public (paper): Archival ALMA projects cited; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00092.S and #2015.1.00220.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Exact CASA version, imaging parameters, apertures and imfit setup
- Missing: Source model details
- Missing: SINFONI data not included (from earlier papers)
- Data volume (inferred): ~50-100 GB raw for two ALMA Band 3 execution blocks sets
- Score (inferred): 3/5, ALMA codes and main steps are given and results numeric, but imaging parameters, apertures and model details are missing.
- Rediscovery candidate: no, Recipe incomplete in imaging and aperture details; ALMA data likely public but key parameters unstated.

## Links

- Method: Veilleux et al. 2017 (cite: rhc_veilleux17) (Similar outflow-disk separation approach)
- Method: Rupke et al. 2005 (cite: rhc_rupke05) (Outflow rate formalism)
- Companion: Förster Schreiber et al. 2014 (cite: rhc_f-s14) (SINFONI Halpha observations of zC400528)
- Companion: Genzel et al. 2014 (cite: rhc_genzel14) (Ionized outflow properties)
- Related: SINS/zC-SINF
- Related: 3D-HST
- Related: COSMOS

## Checks

```json
{
 "quotes": 68,
 "quotes_ok": 68,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 48,
  "rate": 0.6
 },
 "evidence_ok": true
}
```

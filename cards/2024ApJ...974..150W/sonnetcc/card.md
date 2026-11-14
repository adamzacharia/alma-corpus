# Accretion and Outflow in Orion-KL Source I

`2024ApJ...974..150W` | The Astrophysical Journal 2024 | first author: Wright, Melvyn | arXiv: 2408.05114 | DOI: 10.3847/1538-4357/ad7026

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: Do ALMA molecular line maps of Orion Source I (outflow, disk and ambient gas) show signatures of accretion, and how does the outflow interact with the ambient medium  
  > "to look for signatures of accretion in SrcI" (Introduction); "These images map the molecular outflow and disk of Orion Source I (SrcI)" (abstract)
- Target **Orion-KL Source I (SrcI)**: coordinates _not stated_; z/distance 415 pc (Orion-KL)  
  > "At a distance of 415pc (cite: Menten2007; Kim2008; Kounkel2018), Orion-KL is the nearest interstellar cloud with observable massive star formation." (Introduction); distance from (cite: Menten2007; Kim2008; Kounkel2018)  
  > "At a distance of 415pc (cite: Menten2007; Kim2008; Kounkel2018), Orion-KL is the nearest interstellar cloud with observable massive star formation." (Introduction)

## Data provenance

- ALMA projects: 2017.1.00497.S, 2016.1.00165.S
- bands: Band 6 (223 GHz) and Band 7 (340 GHz); also 99 GHz continuum from earlier work  
  > "ALMA Band 6; B6" (Observations); "ALMA Band 7; B7" (Observations); "The less opaque $99$ GHz continuum observations from (cite: Wright2022) will also be analyzed" (Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 99 GHz: 40 - 16200 m; 224 GHz: 40 - 10500 m; 340 GHz: 90 - 12900 m  
  > "40 - 16200" (Table 1); "40 - 10500" (Table 1); "90 - 12900" (Table 1)
- angular resolution: ~30 to 50 mas; synthesized beams 45x36 (99 GHz), 39x19 (224 GHz), 26x11 mas (340 GHz)  
  > "30 to 50 mas resolution" (abstract); "39$\times$19 at PA 66" (Table 1); "26$\times$11 at PA 58" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 158 min (99 GHz), 44 min (224 GHz), 45 min (340 GHz)  
  > "time" (Table 1); "158" (Table 1)
- observing dates: 2017-10-12 (99 GHz), 2017-09-19 (224 GHz), 2017-11-08 (340 GHz)  
  > "2017-10-12" (Table 1); "2017-09-19" (Table 1); "2017-11-08" (Table 1)
- pi or archival as stated: _not stated_
- Line: 28SiO v=0, J=5-4 (217.105 GHz)
- Line: 29SiO v=0, J=5-4 (214.385 GHz)
- Line: SiS v=0, J=12-11 (217.818 GHz)
- Line: H2O 5(5,0), v2=1 - 6(4,3), v2=1 (232.687 GHz)
- Line: NaCl v=1, J=18-17 (232.510 GHz)
- Line: NaCl v=2, J=17-16 (217.980 GHz)
- Line: SO J=5-4 (215.221 GHz)
- Line: SO J=8-7 (344.311 GHz)
- Other facility **VLA**: _not stated_
- External data: Positions and proper motions of the runaway stars in OMC1 (SrcI proper motion PA = 152 +/- 4 deg)  
  > "Table 1 from (cite: Rodgriguez2017) gives the positions and proper motions of the runaway stars in OMC1." (5.4 Possibility of Bondi-Hoyle-Lyttleton Accretion onto the Circumbinary Disk of Source I) [from (cite: Rodgriguez2017)]
- External data: SrcI mass of 15 +/- 2 Msun from rotation curve, used as M = 15 Msun in BHL and luminosity estimates  
  > "found SrcI to have a mass of $15 \pm 2 M_\odot$ by fitting the rotation curve" (Introduction) [from (cite: Ginsburg2018)]
- External data: Ambient density n ~1.6e5 cm^-3 used for ambient mass flow  
  > "(cite: Snell1984), a velocity 10" (The Bipolar Outflow) [from (cite: Snell1984)]
- External data: SrcI disk mass ~0.02 to 0.2 Msun  
  > "(cite: Plambeck2016) estimated M$_{disk}$ $\sim$ 0.02 to 0.2$M_\odot$" (Possibility of Bondi-Hoyle-Lyttleton Accretion onto the Circumbinary Disk of Source I) [from (cite: Plambeck2016)]
- External data: SrcI disk major axis PA = -37 +/- 0.4 deg at 220-340 GHz  
  > "(PA$=-$37 $\pm$ 0.4$^\circ$, as observed at 220-340 GHz) (cite: Wright2020)" (Possibility of Bondi-Hoyle-Lyttleton Accretion onto the Circumbinary Disk of Source I) [from (cite: Wright2020)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: uniform-like images with robust = 0; naturally weighted images with robust = 2  
  > "The Brigg’s visibility weighting was set to robust $=0$ to avoid the excessive weight being given to visibilities in relatively sparsely filled regions of the uv-plane by uniform weighting." (Observations); "For naturally-weighted images, we set robust $=2$ to map the low-brightness, more extended emission." (Observations)
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
- final beam: SO 215.22 GHz natural weighting: 95x76 mas at PA -83 deg; SiS 54x34 mas  
  > "in a synthesized beam FWHM 95$\times$76 mas at PA -83$^\circ$" (Possibility of Bondi-Hoyle-Lyttleton Accretion onto the Circumbinary Disk of Source I); "At 54$\times$34 mas (22$\times$14 au) resolution, the SiS image shows a shell-like structure." (The Bipolar Outflow)
- final rms: 9 mJy/beam (35 K) for naturally weighted 215.22 GHz SO in 1 km/s channels  
  > "The RMS noise level is 9 mJy/beam (35 K)" (Possibility of Bondi-Hoyle-Lyttleton Accretion onto the Circumbinary Disk of Source I)

### Inherited from earlier work

- The Band 6 and Band 7 data and their observation/processing description  
  > "as described in (cite: Ginsburg2018)" (Observations) [from (cite: Ginsburg2018)]
- 99 GHz continuum observations analysed from earlier work  
  > "The less opaque $99$ GHz continuum observations from (cite: Wright2022) will also be analyzed" (Observations) [from (cite: Wright2022)]

### Not stated but needed to reproduce (our reading)

- Calibration: pipeline vs manual, CASA version, calibrators, flux scale and any self-calibration are not given (deferred to Ginsburg2018)
- Imaging software and task, deconvolver, cell and image size, masks, and clean thresholds
- Continuum subtraction method and line-free channels
- Which weighting (robust=0 vs 2) was used for each figure beyond the few stated
- Spectral setup and channel widths for the 340 GHz and 99 GHz data
- Moment-map clipping thresholds and the method for the NaCl velocity-gradient model
- Exact coordinates of SrcI and the image phase centre

## Analysis recipe

1. **image the line data**: Process the uv data into images with uniform and natural weighting  
  > "This data was processed into images using both uniform and natural weighting of the uv-data." (Observations)
   - parameter: robust = 0 for uniform-like images; robust = 2 for natural-weighted images  
  > "For naturally-weighted images, we set robust $=2$ to map the low-brightness, more extended emission." (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **make moment maps of each line**: Average intensity and average velocity derived from the intensity and velocity of each spectral channel  
  > "These were derived from the intensity and velocity of each spectral channel." (Results)
   - parameter: Velocity resolution 2 km/s (SiO, SiS, NaCl), 1 km/s (SO)  
  > "at a velocity resolution of $2$" (The Molecular Outflow; SiO and SiS)
   - fitting: _not stated_
   - validation: _not stated_
3. **extract position-velocity profiles of outflow and disk**: Four cuts across the outflow: two along the outflow edges (PA 122 and 172 deg), disk major axis (PA 142 deg), outflow axis (PA 52 deg)  
  > "Four cuts are drawn across the outflow: along the outflow edges" (The Bipolar Outflow)
   - assumption: Disk inclination 80 to 85 deg  
  > "Assuming a disk inclination 80 to 85$^\circ$" (Entrainment of ambient material into the Molecular Outflow ?)
   - fitting: Gaussian fits to the spectra along the minor axis  
  > "Gaussian fits to the spectra along the minor axis show that the line of sight velocity of the emission" (Entrainment of ambient material into the Molecular Outflow ?)
   - validation: Compared with Hirota2017 results for Si18O J=12-11  
  > "consistent with the results shown by (cite: Hirota2017) for the Si$^{18}$O $J=12-11$ line" (Entrainment of ambient material into the Molecular Outflow ?)
4. **estimate ambient mass flow and BHL accretion rate**: Ambient mass flow through the outflow cross section; Bondi-Hoyle-Lyttleton rate formula  
  > "Accretion onto the disk from the ambient cloud would be limited to roughly the BHL rate" (Possibility of Bondi-Hoyle-Lyttleton Accretion onto the Circumbinary Disk of Source I)
   - parameter: n_H2 = 1.6e5 cm^-3, M = 15 Msun, v = 10 km/s, mu = 2.8  
  > "$M = 15 \; M_\odot$, and $v= 10 \; \text{km} \; \text{s}^{-1}$" (Possibility of Bondi-Hoyle-Lyttleton Accretion onto the Circumbinary Disk of Source I)
   - assumption: Outflow cross section 1000 x 200 AU; sound speed 1-5 km/s for T = 10-1000 K  
  > "cross sectional dimensions of 1000 $\times$ 200 AU for the SrcI outflow" (The Bipolar Outflow)
   - fitting: _not stated_
   - validation: _not stated_
5. **model NaCl velocity structure**: Model images in 2 km/s channels from a linear velocity gradient combined with the observed NaCl moment 0 image; offsets fitted vs velocity  
  > "Using a linear velocity gradient combined with the observed NaCl moment 0 image, we generated model images in 2 km/s channels" (Evidence of a Warped Disk in Salt Emission)
   - software: MIRIAD (imdiff)
   - assumption: Disk almost edge-on (inclination ~85 deg from SiO masers)  
  > "found that the SiO masers suggest an inclination of $\sim$85" (Evidence of a Warped Disk in Salt Emission)
   - fitting: imdiff used to fit the offset as a function of velocity  
  > "to fit the offset as as a function of velocity" (Evidence of a Warped Disk in Salt Emission)
   - validation: Model compared with data in 2 km/s channels between -10 and +20 km/s  
  > "This simple model agrees with the observed NaCl emission in 2 km/s channels between -10 and +20 km/s." (Evidence of a Warped Disk in Salt Emission)
6. **estimate luminosity and disk depletion timescale**: Compare stellar-photosphere and accretion luminosity; disk mass divided by accretion rate  
  > "then the disk will be depleted on a timescale of $M_{disk}$/$\dot{M}$." (Possibility of Bondi-Hoyle-Lyttleton Accretion onto the Circumbinary Disk of Source I)
   - assumption: Stellar radius 1 AU, colour temperature 4000 K; infall 5e-3 Msun/yr onto 15 Msun  
  > "Assuming a stellar radius of 1 AU with color temperature 4000K" (Possibility of Bondi-Hoyle-Lyttleton Accretion onto the Circumbinary Disk of Source I)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **MIRIAD** : Listed software; imdiff tool used to fit the NaCl model offset versus velocity  
  > "Miriad (cite: Sault1995)" (Software); "to fit the offset as as a function of velocity" (Evidence of a Warped Disk in Salt Emission)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Peak brightness 28SiO v=0 J=5-4 | 1078 | not stated | K | 2 | emission with a peak brightness of $1078$ K |
| Peak brightness 29SiO v=0 J=5-4 | 18300 | not stated | K | 2 | emission with a peak brightness of $18300$ K |
| Peak brightness SiS v=0 J=12-11 | 409 | not stated | K | 2 | emission with a peak brightness of $409$ K |
| Peak brightness SO 344.31 GHz (natural weighting) | 375 | not stated | K | 2 | velocity resolution is 375 K |
| Peak brightness NaCl v=1 J=18-17 | 197 | not stated | K | 2 | emission with a peak brightness of $197$ K |
| RMS noise, 215.22 GHz SO natural weighting, 1 km/s | 9 mJy/beam (35 K) | not stated | mJy/beam | 1 | The RMS noise level is 9 mJy/beam (35 K) |
| Implied outflow velocity v_z | 23 to 45 | not stated | km/s | 3 | the implied outflow velocity, $v_z\sim$23 to 45 km s$^{-1}$ |
| Ambient mass flow around SrcI outflow | ~1e-5 | not stated | Msun/yr | 4 | the ambient mass flow is $\sim$ 10$^{-5}$ M$_{\odot}$$\mathrm{yr^{-1}}$ |
| BHL accretion rate | ~5e-7 | not stated | Msun/yr | 4 | \approx 5 \times 10^{-7} M_\odot \; \text{yr}^{-1} |
| Misalignment of SrcI proper motion with disk major axis | 9 | +/-4 | deg | 0 | It appears to be misaligned by 9$\pm$4$^\circ$ with the SrcI disk major axis |
| SiS persistence time after formation | ~20 | not stated | yr | 0 | we would expect the SiS to persist for $\sim$20 yr after formation |
| Gravitational radius r_G | ~130 | not stated | AU | 0 | $r_G$ $\sim GM/v_{rot}^2$ $\sim$ 130 AU |
| Disk depletion time | 200 to 2000 | not stated | yr | 6 | giving a disk depletion time of 200 to 2000 yr |

## Qualitative findings

- SiS traces a turbulent boundary layer in the outflow where ambient material may be entrained  
  > "The SiS maps a turbulent boundary layer in the outflow." (Summary)
- NaCl emission closely traces the disk with a linear velocity gradient and a possible warp at the disk ends  
  > "The NaCl emission closely traces the disk." (Summary)
- SO traces a bow shock at the leading edge and a turbulent trailing plume of SrcI  
  > "SO traces a bow-shock at the leading edge of the SrcI disk" (Summary)

## Claim tuples

- H: Does ambient material entrained into the rotating outflow dissipate its angular momentum | E: PV cuts and moment maps of SiO and SiS along outflow edges and axes | R: Rotational velocity decreases with distance from the disk; SiS forms a shell-like layer with complex velocity structure | F: SiS maps a turbulent boundary layer that may dissipate outflow angular momentum into the surroundings | **partially**
- H: Do NaCl lines trace accretion shocks on a warped disk | E: Compare NaCl v=1 and v=2 maps and a linear-velocity-gradient model | R: Model offsets at disk ends; v=1 and v=2 come from the same regions with the same velocity distribution | F: Bright NaCl hot spots may be excited by accretion shocks and the disk may be warped | **partially**
- H: Does the proper motion of SrcI through the medium shape its environment | E: SO maps compared with the expected proper motion and BHL estimates | R: SO shows a steep gradient at the SE end of the disk and a trailing tail to the NW | F: SO traces a bow shock and trailing plume from SrcI motion through the medium | **partially**

## Reasoning

- Why this data: Re-examine existing ALMA data using lines that trace key SrcI structures to look for accretion signatures  
  > "we re-examine our observational data from ALMA, using several molecular spectral lines that trace key structures in SrcI" (Introduction)
- Why this method: robust = 0 chosen to avoid excess weight on sparsely filled uv regions; robust = 2 to map low-brightness extended emission  
  > "For naturally-weighted images, we set robust $=2$ to map the low-brightness, more extended emission." (Observations)
- How they decided it was enough: _not stated_
- Limitation (authors): More detailed modelling is needed to test whether accretion shocks populate the observed NaCl levels  
  > "More detailed modeling is needed to see if accretion shocks could populate the observed NaCl levels." (Evidence of a Warped Disk in Salt Emission)
- Limitation (authors): No direct observation of infall onto SrcI  
  > "Currently, no direct observations of infall onto SrcI have been made." (Possibility of Bondi-Hoyle-Lyttleton Accretion onto the Circumbinary Disk of Source I)
- Caveat (inferred, ours): Interpretations (entrainment, accretion shocks, warp) are qualitative with no fitted models or uncertainties
- Caveat (inferred, ours): Several estimates rest on assumed density, inclination and temperature
- Caveat (inferred, ours): Maser contamination of 29SiO peak brightness is only noted, not corrected

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Calibration and imaging recipe (deferred to Ginsburg2018)
- Missing: Clean parameters and masks
- Missing: Moment-map and PV extraction parameters
- Missing: NaCl model details
- Data volume (inferred): Large: three long-baseline ALMA execution blocks (Band 6, Band 7 and Band 3) across two projects, likely tens to hundreds of GB raw
- Score (inferred): 2/5, Project codes and observing dates are given, but calibration, imaging parameters and analysis details are not, and results are mostly qualitative or images
- Rediscovery candidate: no, Recipe incomplete and main results are mostly qualitative maps rather than numeric answers

## Links

- Method: (cite: Ginsburg2018) (Describes the Band 6 and Band 7 data used here)
- Method: (cite: Wright2022) (Source of the 99 GHz continuum observations)
- Companion: (cite: Wright2020) (Earlier ALMA study of SiO, SiS and other lines in SrcI)
- Companion: (cite: Hirota2017) (Hollow-cone rotating outflow model of Si18O in SrcI)
- Related: 2016.1.00165.S
- Related: 2017.1.00497.S

## Checks

```json
{
 "quotes": 86,
 "quotes_ok": 86,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 43,
  "rate": 0.524
 },
 "evidence_ok": true
}
```

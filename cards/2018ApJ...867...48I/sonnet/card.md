# Circumnuclear Multiphase Gas in the Circinus Galaxy. II. The Molecular and Atomic Obscuring Structures Revealed with ALMA

`2018ApJ...867...48I` | The Astrophysical Journal 2018 | first author: Izumi, Takuma | arXiv: 1809.09154 | DOI: 10.3847/1538-4357/aae20b

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: What are the geometry, mass, chemistry and kinematics of the molecular (CO) and atomic (CI) gas in the Circinus circumnuclear disk, and do they support the radiation-driven fountain model of the AGN torus?  
  > "Our aim is to investigate the nature of the circumnuclear obscuring material, by focusing particularly on the differences in the dynamical or geometrical structures as a function of the phase of the gas (molecular vs. atomic)." (1 Introduction)
- Target **Circinus galaxy**: coordinates 14h13m09.950s, -65d20m21.0s (J2000, phase center)  
  > "We set the phase tracking center to ($\alpha_{\rm J2000.0}$, $\delta_{\rm J2000.0}$) = (14$^{\rm h}$13$^{\rm m}$09$^{\rm s}$.950, $-$65$\ensuremath{^\circ}$20$\ensuremath{'}$21$\ensuremath{''}$.0)" (2.1 ALMA observations); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.01613.S
- bands: Band 7 and Band 8  
  > "We observed Circinus with ALMA Band 7 and 8 during 2016–2017 using 42–47 antennas" (2.1 ALMA observations)
- frequencies and spectral setup: Four 1.875 GHz spectral windows, one covering CO(3–2) or [C I](1–0); 2SB dual polarization  
  > "one of the four spectral windows (each with a width of 1.875 GHz) was used to fully cover the CO(3–2) or [C I](1–0) emission lines, both in the 2SB dual-polarization mode." (2.1 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15–704 m and 15–1124 m (Band 7); 15–287 m (Band 8)  
  > "| 2017 May 5  | 47                 | 15–1124  | 42.5           | J1427-4206 | J1424-6807 | J1427-4206 | $\sim 140$    |" (Table 1)
- angular resolution: CO(3–2) 0.29x0.24 arcsec (5.9x4.9 pc); [CI](1–0) 0.71x0.66 arcsec (14.5x13.4 pc)  
  > "| CO(3–2) | 345.796 | 0.29 $\times$ 0.24 (153.6) | 5.9 $\times$ 4.9 | 0.37 | 301 |" (Table 2)
- max recoverable scale: ~7'' (Band 7), ~5'' (Band 8)  
  > "The expected maximum recoverable scales per pointing are $\sim 7\ensuremath{''}$ (Band 7) and $\sim 5\ensuremath{''}$ (Band 8)." (2.1 ALMA observations)
- sensitivity: rms 0.37 (CO), 0.08 (B7 cont), 3.10 ([CI]), 0.80 (B8 cont) mJy/beam  
  > "| $[$C I$]$(1–0) | 492.161 | 0.71 $\times$ 0.66 (95.9) | 14.5 $\times$ 13.4 | 3.10 | 1435 |" (Table 2)
- time on source: 42.5 min per Band 7 execution; 31.5 min Band 8  
  > "| [C I](1–0) | 2017 Mar 18 | 43 | 15–287 | 31.5 |" (Table 1)
- observing dates: 2016 Nov 24, 2016 Nov 26, 2017 May 5 (Band 7); 2017 Mar 18 (Band 8)  
  > "| [C I](1–0) | 2017 Mar 18 | 43 | 15–287 | 31.5 | J1427-4206 | J1424-6807 | J1427-4206 | $\sim 500$ |" (Table 1)
- pi or archival as stated: Cycle 4 program, PI T. Izumi  
  > "as a Cycle 4 program (ID = 2016.1.01613.S, PI = T. Izumi)" (2.1 ALMA observations)
- Line: CO J=3–2 (345.7960 GHz)
- Line: [C I] 3P1–3P0 (492.1607 GHz)
- Other facility **HST**: PC F656N, F606W, F814W images from Hubble Legacy Archive (Halpha map, F814 for Ks/F814 ratio)  
  > "We retrieved the *Hubble Space Telescope (HST)* Planetary Camera images (PC-F656N, F606W, F814W) of Circinus from the Hubble Legacy Archive" (2.2 Ancillary data)
- Other facility **VLT/NaCo**: Ks-band image  
  > "We also use the $Ks$-band image obtained with the NaCo/VLT (cite: 2016MNRAS.457L..94M)" (2.2 Ancillary data)
- External data: APEX single-dish CO(3–2) and [CI] fluxes used for missing-flux estimates and line ratio comparison  
  > "a roughly $\sim 50\%$ of the total CO(3–2) line flux has been resolved out compared to the APEX single dish data (cite: 2014A&A...568A.122Z)" (4.1 CO(3–2) map) [from (cite: 2014A&A...568A.122Z)]
- External data: X-ray luminosity L44=0.13 (photon index 1.31, cutoff 160 keV) for XDR estimate  
  > "we adopted $L_{44} = 0.13$ (with a photon index = 1.31 and cut-off energy = 160 keV) from (cite: 2014ApJ...791...81A)" (4.3 line ratio) [from (cite: 2014ApJ...791...81A)]
- External data: Black hole mass 1.7e6 Msun from H2O masers  
  > "$M_{\rm BH} = (1.7\pm0.3) \times 10^6~M_\odot$ (cite: 2003ApJ...590..162G)" (1.1 Our target) [from (cite: 2003ApJ...590..162G)]
- External data: Ks and HST F814 data for warm dust ratio map  
  > "We thank Dr. M. Mezcua for kindly providing us the NIR $Ks$-band and *HST*/F814 data." (Acknowledgments) [from (cite: 2016MNRAS.457L..94M)]
- Simulation/model as data: Snapshot of the multi-phase dynamic (radiation-driven fountain) torus model tuned for Circinus, with non-equilibrium XDR chemistry and post-processed non-LTE radiative transfer for CO(3–2) and [CI](1–0); r~16 pc, M_H2 = 2e6 Msun, 128^3 grids at 0.25 pc  
  > "The simulated CND has a circular gas distribution for simplicity with $r \simeq 16$ pc, with the total $M_{\rm H_2}$ of $2 \times 10^6~M_\odot$ (128$^3$ grids; 0.25 pc resolution)" (6.1 Line intensities)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.7  
  > "Data reduction, calibration, and analyses were performed with CASA version 4.7 (cite: 2007ASPC..376..127M) in the usual way." (2.1 ALMA observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1427-4206 (or J1617-5848 on 2016 Nov 26)  
  > "| 2016 Nov 26 | 42 | 17–704 | 42.5 | J1427-4206 | J1424-6807 | J1617-5848 | $\sim 140$ |" (Table 1)
- flux scale uncertainty: ~10%  
  > "The absolute flux uncertainty is $\sim 10\%$ according to the ALMA Cycle 4 Proposer’s Guide" (2.1 ALMA observations)
- self calibration: _not stated_

### Imaging

- task: CLEAN  
  > "The line and underlying continuum emission were reconstructed using the `CLEAN` task with Briggs weighting (robust = 0.5)." (2.1 ALMA observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "The line and underlying continuum emission were reconstructed using the `CLEAN` task with Briggs weighting (robust = 0.5)." (2.1 ALMA observations)
- uv taper: _not stated_
- cell size: 0.03'' (Band 7), 0.1'' (Band 8)  
  > "the pixel scale of Band 7 maps is set to 0$\ensuremath{''}$.03, whereas that of Band 8 maps is 0$\ensuremath{''}$.1" (2.1 ALMA observations)
- image size: _not stated_
- masking: Emission <1.5 sigma clipped in displayed images; moment 1/2 maps with 10 sigma clipping  
  > "emission with $<1.5\sigma$ are clipped to enhance the clarity of the images" (2.1 ALMA observations)
- multiscale scales: _not stated_
- continuum subtraction: Subtracted in the uv plane before line cubes  
  > "These continuum emission were subtracted in the $uv$ plane before making the line cubes." (2.1 ALMA observations)
- line free channels: _not stated_
- primary beam correction: Applied when comparing with APEX fluxes  
  > "After convolving the map to an 18$\ensuremath{''}$ aperture and correcting for the primary beam attenuation" (4.1 CO(3–2) map)
- array combination: _not stated_
- smoothing: Channels binned to ~10 km/s; CO(3–2) uv range (25–470 kλ) and beam matched to [CI] (0.71x0.66)  
  > "We first adjust the $uv$ range and the beam size of the CO(3–2) data to those of the \[C I\](1–0) data (25–470 k$\lambda$, $0\ensuremath{''}.71 \times 0\ensuremath{''}.66$ with PA = 96$\ensuremath{^\circ}$)." (4.3 line ratio)
- final beam: CO 0.29x0.24 (PA 153.6); [CI] 0.71x0.66 (PA 95.9)  
  > "| CO(3–2) | 345.796 | 0.29 $\times$ 0.24 (153.6) | 5.9 $\times$ 4.9 | 0.37 | 301 |" (Table 2)
- final rms: CO 0.37, B7 cont 0.08, [CI] 3.10, B8 cont 0.80 mJy/beam; matched CO cube 0.54 mJy/beam  
  > "The resultant CO(3–2) cube has a 1$\sigma$ sensitivity of 0.54 mJy beam$^{-1}$ at a velocity resolution of 10 km s$^{-1}$." (4.3 line ratio)

### Inherited from earlier work

- Multi-phase dynamic torus model tuned for Circinus, used for comparisons  
  > "we used a snapshot of our multi-phase dynamic torus model tuned for Circinus (cite: 2016ApJ...828L..19W)" (6.1 Line intensities) [from (cite: 2016ApJ...828L..19W)]
- Non-LTE radiative transfer procedure for CO lines, applied here to [CI](1–0)  
  > "Their procedure was fully applied to the case of the \[C I\](1–0) in this work." (6.1 Line intensities) [from (cite: 2018ApJ...852...88W)]
- C I mass equation  
  > "We first estimate the atomic carbon mass ($M_{\rm CI}$) by following (cite: 2002ApJS..139..467I) and (cite: 2005A&A...429L..25W)" (4.2 [C I](1–0) map) [from (cite: 2002ApJS..139..467I); (cite: 2005A&A...429L..25W)]

### Not stated but needed to reproduce (our reading)

- Image sizes, clean thresholds, masks, and deconvolver settings
- Line-free channels and continuum fitting order for uv continuum subtraction
- Exact channel binning and velocity range per cube
- Flux calibrator models/values and any self-calibration
- 3DBarolo parameter settings (initial guesses, weighting, mask, fit bounds)
- Alpha_CO value used (0.8 stated in Sect. 6 only) and conversion details
- UVMULTIFIT initial values and fitting setup
- Region definitions of AGN, CND and 10'' box apertures for flux ratios
- Distance to Circinus used for pc scale conversions

## Analysis recipe

1. **Image continuum and line cubes**: CASA CLEAN with Briggs robust 0.5; channels binned to ~10 km/s; uv-plane continuum subtraction  
  > "The line and underlying continuum emission were reconstructed using the `CLEAN` task with Briggs weighting (robust = 0.5)." (2.1 ALMA observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Continuum nature and spectral index**: Compare Band 7 and 8 flux at AGN position after matching uv range and beam; compare synchrotron extrapolation from 6 cm  
  > "A Band 8 to 7 flux density ratio at the AGN position, after matching the Band 7 $uv$ range and beam size to the Band 8 ones" (3.2 Physical nature)
   - software: CASA
   - assumption: Synchrotron spectral index -0.7  
  > "with a typical synchrotron spectral index[^4] of $\alpha = -0.7$ is only $\sim 2.5$ mJy" (3.2 Physical nature)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit compact and extended continuum components in the visibility plane**: Two-component 2D Gaussian fit to Band 7 visibilities  
  > "Here we performed a two-dimensional *double* Gaussian fit to this visibility data" (3.4 The polar elongation)
   - software: UVMULTIFIT
   - fitting: Visibility-plane Gaussian model fit; sampler not stated  
  > "Here we performed a two-dimensional *double* Gaussian fit to this visibility data" (Continuum Emission, The polar elongation)
   - validation: Compared with MIR polar elongation size and PA  
  > "are roughly consistent with those of the MIR polar elongation ($\sim 1.9$ pc and $\sim 287\ensuremath{^\circ}$, respectively)" (3.4 The polar elongation)
4. **CND size and molecular mass**: IMFIT 2D Gaussian on 3''x3'' CO(3–2) moment 0; CO(3–2) assumed thermalized with CO(1–0); L'CO to M_H2 with canonical alpha_CO  
  > "We assume that the CO(3–2) emission there (integrated intensity = 805 Jy km s$^{-1}$) is thermalized with that of CO(1–0)" (4.1.2 The CND)
   - software: CASA IMFIT, CASA IMMOMENTS
   - assumption: CO(3–2)/CO(1–0) thermalized; canonical alpha_CO in active environments (0.8 Msun (K km/s pc2)^-1)  
  > "$\alpha_{\rm CO} = 0.8$ $M_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$" (6.1 Line intensities)
   - fitting: _not stated_
   - validation: Compared with [CI]-based M_H2  
  > "This is consistent with the CO(3–2)-based $M_{\rm H_2}$ derived in § 4.1.2." (4.2 [C I](1–0) map)
5. **Atomic carbon mass and M_H2**: Optically thin LTE M_CI equation with Tex = 30 K; C I/H2 abundance 8e-5  
  > "If we adopt a relative C I abundance with respect to H$_2$ as $8 \times 10^{-5}$" (4.2 [C I](1–0) map)
   - assumption: Tex=30 K, tau<~1  
  > "Then we achieve $M_{\rm CI} \simeq 1770~M_\odot$ within the CND by assuming that $T_{\rm ex} = 30$ K" (4.2 [C I](1–0) map)
   - fitting: _not stated_
   - validation: _not stated_
6. **[CI]/CO line ratio and XDR interpretation**: Ratio on matched uv/beam maps; one-zone XDR model H_X/n estimate  
  > "we can estimate the X-ray energy deposition rate per particle ($H_X/n$)" (4.3 line ratio)
   - assumption: n_H2 = 1e5 cm^-3, r = 7 pc  
  > "as well as $n_{\rm H_2} = 10^5$ cm$^{-3}$ as a typical value" (4.3 line ratio)
   - fitting: _not stated_
   - validation: _not stated_
7. **Tilted-ring kinematics**: Fit concentric rings to cubes, free Vrot, sigma, i, PA; dynamical center fixed at AGN, Vsys = 446 km/s; 50 rings (0.15'') on full-resolution CO, 20 rings (0.25'') on matched cubes  
  > "$V_{\rm rot}$, $\sigma_{\rm disp}$, $i$, and PA were thus the major free parameters and were evaluated by minimizing $|$model$-$observed data$|$." (5.2 Decomposition)
   - software: 3DBarolo
   - assumption: sigma/Vrot ~ H/R under hydrostatic equilibrium  
  > "This ratio can be considered as a scale height ($H$) to scale radius ($R$) ratio" (5.2.1)
   - fitting: Minimize |model-observed|; no sampler stated  
  > "were thus the major free parameters and were evaluated by minimizing $|$model$-$observed data$|$" (Molecular and Atomic Gas Dynamics, Decomposition with tilted rings)
   - validation: Compare model and observed PVDs and residual map; compare full-resolution and matched results  
  > "The overall structures are well reproduced by a combination of gas rotation and dispersion" (5.2.1)
8. **Multi-Gaussian fit to nuclear spectra and compare with model**: Single and triple Gaussian fits to AGN-position spectra, observed and simulated at i=75 deg  
  > "adding two more components (i.e., triple Gaussians) can fit the observed nuclear [C I](1–0) spectrum more faithfully" (5.2.2)
   - fitting: _not stated_
   - validation: Consistency of outflow velocities with model  
  > "The blueshifted and redshifted features emerge at around the coherent outflow velocity of $\sim 50-60$ km s$^{-1}$ in our model." (6.2)

## Software

- **CASA** 4.7: Reduction, calibration, CLEAN imaging, IMMOMENTS, IMFIT  
  > "Data reduction, calibration, and analyses were performed with CASA version 4.7" (2.1 ALMA observations)
- **MIRIAD** : Some analyses  
  > "Some parts of our analyses were also performed with the MIRIAD package" (2.1 ALMA observations)
- **UVMULTIFIT** : Visibility model fitting of Band 7 continuum  
  > "we applied the `UVMULTIFIT` procedure (cite: 2014A&A...563A.136M) to the Band 7 continuum visibility data" (3.4 The polar elongation)
- **3DBarolo** : Tilted-ring fits  
  > "we fitted concentric titled rings to the observed velocity structures with the $^{\rm 3D}$Barolo code" (5.2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Band 7 total continuum flux (10'' box) | 66.5 | not stated | mJy | 1 | The total fluxes are $\sim 66.5$ mJy (Band 7) and $\sim 320$ mJy (Band 8) within the 10$\ensuremath{''}$ box. |
| Band 8 total continuum flux (10'' box) | 320 | not stated | mJy | 1 | The total fluxes are $\sim 66.5$ mJy (Band 7) and $\sim 320$ mJy (Band 8) within the 10$\ensuremath{''}$ box. |
| Dust emissivity index beta | 1.72 (spectral index 3.72) | not stated | dimensionless | 2 | revealed a steep spectral index of 3.72, or dust emissivity index [^5] of $\beta = 1.72$ |
| Component-1 integrated flux (Band 7) | 20.7 | 1.3 | mJy | 3 | /   Integrated flux (mJy)    / 20.7 $\pm$ 1.3 / 73.5 $\pm$ 1.6 / |
| Component-1 size | 1.6 x 1.2 pc, PA 298 | ±0.3, ±0.1 pc; ±21 deg | pc, deg | 3 | The derived source size ($1.6 \pm 0.3$ pc $\times$ $1.2 \pm 0.1$ pc) and PA ($298\ensuremath{^\circ} \pm 21\ensuremath{^\circ}$) of Component-1 |
| CND deconvolved size | 74 x 34 pc, PA 212.0 | ±3, ±1 pc; ±1.9 deg | pc, deg | 4 | or (74 $\pm$ 3) pc $\times$ (34 $\pm$ 1) pc with PA = $212.0\ensuremath{^\circ} \pm 1.9\ensuremath{^\circ}$ |
| CND M_H2 (CO-based) | 3e6 | not stated | Msun | 4 | We estimate the molecular mass of the CND to be $M_{\rm H_2} \simeq 3 \times 10^6~M_\odot$ |
| N_H2 toward AGN | 5.4e23 | not stated | cm^-2 | 4 | as $N_{\rm H_2} = 5.4 \times 10^{23}$ cm$^{-2}$ |
| M_CI in CND | 1770 | not stated | Msun | 5 | $M_{\rm CI} \simeq 1770~M_\odot$ within the CND by assuming that $T_{\rm ex} = 30$ K |
| M_H2 from [CI] | 3.7e6 | not stated | Msun | 5 | we obtain $M_{\rm H_2}$ of $\simeq 3.7 \times 10^6~M_\odot$ in the CND |
| R_CI/CO at AGN (Jy km/s, K km/s scales) | 1.80 / 0.89 | 0.25 / 0.13 | dimensionless | 6 | / Jy km s$^{-1}$ / 1.80 $\pm$ 0.25 / 1.03 $\pm$ 0.15 /     0.97 $\pm$ 0.14     / |
| log(H_X/n) at r=7 pc | -27.3 | not stated | dimensionless | 6 | as $\log(H_X/n) = -27.3$ |
| sigma/Vrot at r>~15 pc and r<~10 pc (CO) | ~0.25 and ~0.4 | not stated | dimensionless | 7 | the $\sigma_{\rm disp}$/$V_{\rm rot}$ at $r \gtrsim 15$ pc is $\sim 0.25$, while the ratio at the central $r \lesssim 10$ pc increases to $\sim 0.4$ |
| [CI] outflow velocity offsets | ~75 blue, ~60 red | not stated | km/s | 8 | with a velocity offset of $\sim 75$ km s$^{-1}$ (blue) and $\sim 60$ km s$^{-1}$ (red), respectively |

## Qualitative findings

- Continuum traces thermal dust; extended cold dust lies radially farther than warm dust in the Ks/F814 map  
  > "This indicates the existence of temperature-dependent dusty structures around this AGN." (3.3)

## Claim tuples

- H: Compact submm continuum shows polar elongation like MIR | E: Double Gaussian visibility fit of Band 7 | R: Component-1 1.6x1.2 pc, PA 298 deg | F: Traces same structure as MIR polar elongation | **partially**
- H: CND contributes to nuclear obscuration | E: CO(3–2)-derived mass and column density | R: M_H2 ~3e6 Msun, N_H2 ~5.4e23 cm^-2 (beam-averaged) | F: CND is a significant part of the obscurer | **supported**
- H: XDR chemistry elevates [CI]/CO at AGN | E: Line ratio maps and XDR estimate | R: R~0.9 at AGN vs ~0.3 in arms | F: XDR dissociation is a possible cause | **partially**
- H: Atomic gas is vertically more extended than molecular gas at r<~10 pc, driven by outflows | E: Tilted-ring sigma/Vrot, triple Gaussian fits, model comparison | R: sigma/Vrot ~0.4 ([CI]) vs ~0.15 (CO); outflow components ~±60–75 km/s | F: Supports the radiation-driven fountain scheme | **supported**

## Reasoning

- Why this data: [C I] observable with Band 8 probes diffuse atomic gas and XDR signatures, complementing dense molecular gas  
  > "Thus, C I lines will be excellent probes of AGN signatures." (1 Introduction)
- Why this method: _not stated_
- Alternative: Synchrotron contamination of continuum rejected  
  > "we first argue that contamination by such synchrotron emission is not significant at the ALMA Band 7 and 8 frequencies" (3.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Significant missing flux (~50% CO, 45% recovered for [CI]) relative to single dish  
  > "a roughly $\sim 50\%$ of the total CO(3–2) line flux has been resolved out" (4.1)
- Limitation (authors): Keplerian rotation evidence uncertain given large errors  
  > "it is difficult at this moment to achieve a firmer conclusion given the large errors associated with the inner rings" (5.2.1)
- Caveat (inferred, ours): Model comparison is qualitative; model amplitudes differ from observed
- Caveat (inferred, ours): Distance, alpha_CO and Tex choices drive mass estimates
- Caveat (inferred, ours): Beam dilution makes N_H2 a lower limit
- Caveat (inferred, ours): Different beam/uv matching for CO and [CI] limits inner-ring comparisons

## Reproducibility

- Data public (paper): ALMA project code given; ALMA data acknowledged by code  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.01613.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Simulation snapshot of the fountain model not provided
- Missing: 3DBarolo settings and ring initial values
- Missing: Clean masks and thresholds, line-free channels
- Data volume (inferred): ~100-200 GB raw for 4 execution blocks in Bands 7 and 8
- Score (inferred): 3/5, Public data and main numbers clear, but many imaging and fitting settings unstated and the model comparison relies on unreleased simulations.
- Rediscovery candidate: no, Key results require unstated parameters and an unreleased model, though some ALMA-only numbers could be redone.

## Links

- Method: (cite: 2015MNRAS.451.3021D) (3DBarolo tilted-ring code)
- Method: (cite: 2014A&A...563A.136M) (UVMULTIFIT visibility fitting)
- Companion: (cite: 2018ApJ...852...88W) (Paper I: model CO line predictions)
- Companion: (cite: 2016ApJ...828L..19W) (Fountain torus model tuned for Circinus)

## Checks

```json
{
 "quotes": 84,
 "quotes_ok": 84,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 90,
  "stated": 62,
  "rate": 0.689
 },
 "evidence_ok": true
}
```

# The Molecular Gas in the NGC 6240 Merging Galaxy System at the Highest Spatial Resolution

`2020ApJ...890..149T` | The Astrophysical Journal 2020 | first author: Treister, Ezequiel | arXiv: 2001.00601 | DOI: 10.3847/1538-4357/ab6b28

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: How is the molecular gas distributed and moving at 15 pc resolution in the NGC 6240 dual-AGN merger, and how much gas is available to feed each SMBH or drive outflows?  
  > "We are thus directly imaging the reservoir of gas that can accrete onto each supermassive black hole." (abstract)
- Target **NGC 6240**: coordinates North 16h52m58.924, +02d24m04.776s; South 16h52m58.890, +02d24m03.350s (VLBI)  
  > "For our work, the nuclear positions were obtained from the Very Long Baseline Interferometry (VLBI) observations of this source, as reported by (cite: hagiwara11)." (3.1 NGC 6240 12CO(2-1) Emission); "$z$=0.02448 and $d_{Gpc}$=0.1" (4.2 Gas Mass from sub-mm continuum); z/distance z=0.02448; d=0.1 Gpc  
  > "For our work, the nuclear positions were obtained from the Very Long Baseline Interferometry (VLBI) observations of this source, as reported by (cite: hagiwara11)." (3.1 NGC 6240 12CO(2-1) Emission); "$z$=0.02448 and $d_{Gpc}$=0.1" (4.2 Gas Mass from sub-mm continuum); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00370.S, 2015.1.00003.S
- bands: Band 6, 12CO(2-1) plus 1.3 mm continuum  
  > "the high resolution band 6 ALMA observations of the $^{12}$CO(2-1) emission" (5 Conclusions)
- frequencies and spectral setup: 4 SPWs of 1875 MHz (7.5 GHz total), 1.953 MHz resolution; CO(2-1) SPW centered at 225.1 GHz; continuum SPWs at 227.5, 239.9, 241.9 GHz  
  > "The total ALMA bandwidth of 7.5 GHz was divided into four spectral windows (SPWs) of 1875 MHz each and a spectral resolution of 1.953 MHz." (2.1 Description of Observations); "The remaining ones were used to trace the mm continuum centered at frequencies of 227.5 GHz, 239.9 GHz and 241.9 GHz" (2.1 Description of Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 m to 15 km, three array configurations  
  > "recovering most of the total flux at large scales by combining three different array configurations (baselines from 15 meters to 15 km)" (2 ALMA Data)
- angular resolution: ~0.03'' (~15 pc); cube beam 0.06''x0.032''  
  > "The achieved angular resolution is $\sim$0.03$''$, corresponding to a physical scale of $\sim$15 pc" (2 ALMA Data)
- max recoverable scale: emission recovered out to 30''  
  > "we are able to recover all the emission out to scales of 30$''$" (3.1 NGC 6240 12CO(2-1) Emission)
- sensitivity: Cube RMS ~0.28 mJy/beam; continuum RMS 0.024 mJy/beam  
  > "The final RMS of the cube is $\sim$0.28 mJy/beam." (A Imaging Parameters); "the RMS of the final image is 0.024 mJy/beam" (A Imaging Parameters)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.538 GHz)
- Other facility **HST/WFPC2**: optical imaging compared with CO  
  > "the optical imaging provided by the Hubble Space Telescope (HST) using the Wide Field Planetary Camera 2 (WFPC2) instrument" (3.1 NGC 6240 12CO(2-1) Emission)
- Other facility **VLT/SINFONI**: H2 1-0 S(1) luminosity from Engel et al. used for gas mass comparison  
  > "This luminosity can be estimated from the VLT/SINFONI observations of NGC 6240 presented by (cite: engel10)." (4.1 Gas Mass from 12CO(2-1))
- External data: alpha_CO and r21 values adopted (alpha_CO 3.2 systemic, 2.1 outflow; r21 1.0 and 1.4)  
  > "We adopt the (cite: cicone18) $\alpha_{CO}$ conversion factor for our calculations" (4.1 Gas Mass from 12CO(2-1)) [from (cite: cicone18)]
- External data: Nuclear positions and SMBH sphere-of-influence radii (235 and 212 pc)  
  > "radii of 235$\pm$8 pc and 212$\pm$9 pc for the northern and southern nuclei, respectively" (3.1 NGC 6240 12CO(2-1) Emission) [from (cite: medling15); VLBI positions (cite: hagiwara11)]
- External data: L(1-0)S(1)/Mgas = 2.5e-3 calibration  
  > "We use the empirically-calibrated relation L$_{\textnormal{(1-0)S(1)}}/M_\textnormal{gas}$ = 2.5$\times$10$^{-3}$ (cite: muller-sanchez06)." (4.1 Gas Mass from 12CO(2-1)) [from (cite: muller-sanchez06)]

## Processing

### Calibration

- pipeline or manual: Standard ALMA reduction with modifications; WVR scaling, step-wise self-calibration  
  > "In general, the standard ALMA data reduction[^1] approach was pursued, with some specific differences." (2.2 Data Analysis)
- casa version: CASA v5.4  
  > "the Common Astronomy Software Applications (CASA, v5.4; (cite: mcmullin07)) was used" (2.2 Data Analysis)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1751+0939 instead of Pallas in Xb5fdce/X79d  
  > "J1751$+$0939 was used as flux calibrator instead of Pallas, which showed problematic amplitude visibilities" (A.1 Compact and Intermediate configurations)
- flux scale uncertainty: _not stated_
- self calibration: Compact/intermediate: single phase-only step, solint inf. Long baseline: unfolding self-cal with baseline cuts 800, 2400, 4000, 8000 klambda, >=3 baselines, >1.5 sigma, gaintype T, per scan  
  > "a single self-calibration step considering phase solutions alone was adopted" (A.1 Compact and Intermediate configurations); "Such step-wise (“unfolding”) approach was considered using the following baseline cuts: 800, 2400, 4000, 8000 k$\lambda$." (A.2 Self-calibrating Xc5148b/X127e)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "This was done using a natural weighting scheme that led to a beam size on the $^{12}$CO(2-1) line cube of 0.06$''$$\times$0.032$''$" (A Imaging Parameters)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: feathering on a per-channel basis; long-baseline execution Xc5148b/X127e only, combined with compact and intermediate  
  > "the use of feathering on a per-channel basis, when retrieving the $^{12}$CO(2-1) emission map, prevented this low-surface density to be parsed to the final combined map." (3.2 Continuum emission)
- smoothing: final cube 20 km/s channels  
  > "the final cube had a resolution of 20 km/s" (A Imaging Parameters)
- final beam: Line 0.06''x0.032'' PA -72 deg; continuum 0.078''x0.047'' PA -73 deg  
  > "the resulting beam size is 0.078$''$$\times$0.047$''$ at an angle of -73$^o$" (A Imaging Parameters)
- final rms: cube 0.28 mJy/beam; moment 0 0.04 Jy/beam km/s; continuum 0.024 mJy/beam  
  > "The RMS of this moment 0 map is 0.04 Jy/beam km/s." (A Imaging Parameters)

### Inherited from earlier work

- Gas mass conversion procedure from CO flux  
  > "we follow the procedure described by (cite: solomon05), as done previously by (cite: treister18)" (4.1 Gas Mass from 12CO(2-1)) [from (cite: solomon05); (cite: treister18)]
- Dust-continuum ISM mass equation  
  > "Following the procedure presented by (cite: scoville15), the ISM mass is given by their equation 3" (4.2 Gas Mass from sub-mm continuum) [from (cite: scoville15)]
- Outflow rate formula  
  > "We estimate the mass outflow rate associated with this high velocity structure using equation 3 in (cite: maiolino12)" (4.3 Outflowing Material) [from (cite: maiolino12)]
- WVR scaling algorithm  
  > "we considered the use of the algorithm developed by (cite: maud17)" (A.1 High resolution) [from (cite: maud17)]

### Not stated but needed to reproduce (our reading)

- Channel ranges used for continuum/line separation and continuum subtraction
- Clean threshold, mask, niter, cell and image size
- Feathering procedure details and weights
- Aperture definitions for outflow region and mass extraction
- Exact moment-map channel/threshold masks beyond sigma cuts
- Scripts for custom calibration and execution block to dataset mapping
- Spectral-line flux extraction rms method

## Analysis recipe

1. **Calibrate and self-calibrate**: Standard ALMA calibration with WVR scaling, flagging DA61, and unfolding self-calibration on the long-baseline EB  
  > "The final calibration adopted WVR scaling, with DA61 flagged, and the “unfolding” self-calibration strategy applied." (A.2 Self-calibrating Xc5148b/X127e)
   - software: CASA
   - parameter: baseline cuts 800, 2400, 4000, 8000 klambda; >1.5 sigma  
  > "significance was greater than 1.5$\sigma$ (probability greater than 86.6%)" (A.2 Self-calibrating Xc5148b/X127e)
   - fitting: _not stated_
   - validation: Dynamic range of nuclei continuum and phase-rms of calibrators/check source  
  > "determining the dynamic range of the NGC 6240 continuum image (dominated by the two point-like nuclei) and the improvement of the phase-rms in each antenna" (A.1 High resolution)
2. **Image cube and continuum, make moment maps**: Natural-weighted cube, per-channel feathering; moment 0 over -500 to 980 km/s; moment 1 (3 sigma) and 2 (5 sigma) with immoments  
  > "by integrating the line emission between -500 km/s and 980 km/s" (A Imaging Parameters)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared fluxes to Tacconi99 and single-dish Greve09  
  > "implying that our ALMA observations recover 67-94% of the single-dish flux" (3.1 NGC 6240 12CO(2-1) Emission)
3. **Derive molecular gas masses from CO**: L'CO from flux, M(H2)=alpha_CO L'CO, including He, in two nuclear spheres of influence and 1'' central aperture  
  > "M(H_2)=\alpha_{\textnormal{CO}} L'_{\textnormal{CO}}" (4.1 Gas Mass from 12CO(2-1))
   - parameter: r21 = 1.0 systemic, 1.4 outflow  
  > "$r_{21}$=1.0$\pm$0.2 for the systemic component and 1.4$\pm$0.3 for the outflows" (4.1 Gas Mass from 12CO(2-1))
   - assumption: alpha_CO 3.2 (systemic) and 2.1 (outflow) Msun (K km/s pc^2)^-1 from Cicone18  
  > "$\alpha_{CO}$=3.2$\pm$1.8 $M_\odot$(K km s$^{-1}$pc$^2$)$^{-1}$ for the systemic components" (4.1 Gas Mass from 12CO(2-1))
   - fitting: _not stated_
   - validation: Compared with H2 1-0 S(1)-based mass and literature  
  > "hence fully consistent with the values derived here based on the $^{12}$CO(2-1) observations" (4.1 Gas Mass from 12CO(2-1))
4. **Dust-continuum ISM mass**: Scoville15 Rayleigh-Jeans formula on compact+intermediate continuum fluxes  
  > "Furthermore, we assume $T_{25}$=1." (4.2 Gas Mass from sub-mm continuum)
   - assumption: T_dust=25 K (T25=1), emission thermal dust  
  > "Therefore, we can assume that the continuum emission is dominated by thermal emission from dust" (4.2 Gas Mass from sub-mm continuum)
   - fitting: _not stated_
   - validation: Compared to CO masses  
  > "These masses are roughly consistent with those derived from the CO measurements in the previous section." (4.2 Gas Mass from sub-mm continuum)
5. **Outflow mass and rate**: Mass of >500 km/s component from CO; Mdot=3 v M/R  
  > "Assuming values of $v$=500 km/s, $M_{\textnormal{out}}$=9$\times$10$^8$ $M_\odot$ and $R_{\textnormal{out}}$ between 290pc and 430pc" (4.3 Outflowing Material)
   - assumption: uniformly filled spherical/conical outflow; factor ~3 uncertainty  
  > "have uncertainties of factors of $\sim$3 (cite: lutz19)" (4.3 Outflowing Material)
   - fitting: _not stated_
   - validation: Compared to Cicone18 rate  
  > "roughly consistent with the value of $2500\pm1200$ M$_{\odot}$/yr reported by (cite: cicone18)" (4.3 Outflowing Material)
6. **Kinematics via p-v diagrams and dispersion**: p-v slits compared with stellar disk models and toy expanding shells fitted by eye; moment 2 dispersions  
  > "These are illustrative ‘toy’ models fitted by eye" (3.3 Gas kinematics)
   - software: CASA
   - assumption: gas disk PA and inclination same as stellar disks  
  > "assuming for simplicity that the PA and inclination of the inner gas disks around the north and south supermassive black holes follow the same kinematics as the larger scale stellar disk" (3.3 Gas kinematics)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.4: calibration, imaging, immoments  
  > "the Common Astronomy Software Applications (CASA, v5.4; (cite: mcmullin07)) was used" (2.2 Data Analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total CO(2-1) flux in 25'' aperture | 1163 | 28 | Jy km/s | 2 | the total measured flux is 1163$\pm$28 Jy km/s in the ALMA field of view of 25$''$ diameter |
| Gas mass, northern SMBH sphere | 7.4e8 | not stated | Msun | 3 | these line fluxes correspond to gas masses of 7.4$\times$10$^8$M$_\odot$ for the northern nucleus |
| Gas mass, southern SMBH sphere | 3.3e9 | not stated | Msun | 3 | 3.3$\times$10$^9$M$_\odot$ for the southern nucleus |
| Gas mass, central 1'' region | 8.6e9 | not stated | Msun | 3 | 8.6$\times$10$^9$M$_\odot$ for the central region |
| Total molecular mass in 25'' aperture | 2.6e10 | not stated | Msun | 3 | we derive a mass of 2.6$\times$10$^{10}$M$_\odot$ |
| Continuum 235 GHz flux, southern nucleus (all configs) | 9.92 | 0.16 | mJy | 2 | 9.92$\pm$0.16 mJy and 3.50$\pm$0.037 mJy |
| Continuum flux, south and north (compact+intermediate) | 5.19 and 1.73 | 0.06 and 0.03 | mJy | 4 | we obtain values of 5.19$\pm$0.06 mJy and 1.73$\pm$0.03 mJy |
| Dust ISM mass, south and north | 2.1e9 and 6.9e8 | not stated | Msun | 4 | These correspond to ISM masses of 2.1$\times$10$^9M_\odot$ and 6.9$\times$$10^8M_\odot$ respectively. |
| Outflowing molecular mass | 9e8 | not stated | Msun | 5 | The total mass of this outflowing material is estimated at 9$\times$10$^8$ $M_\odot$ |
| Outflow rate | 3200-4700 | factor ~3 | Msun/yr | 5 | We then obtain values of 3200 M$_\odot$/yr to 4700 M$_\odot$/y |
| Mean velocity dispersion north / south nucleus | 184 / 155 | not stated | km/s | 6 | we find an average velocity dispersion of 184 km/s, while for the southern one, on a similar area, we find an average velocity dispersion of 155 km/s |

## Qualitative findings

- No clear rotating disk between nuclei; gas is clumpy and turbulence-dominated (v/sigma~1)  
  > "there is no clear evidence for a rotating disk in the inter-nuclear region" (3.3 Gas kinematics)
- CO does not coincide with the mm continuum, which concentrates around each nucleus  
  > "the millimeter continuum emission arising from dust is mostly concentrated around each nucleus" (3.2 Continuum emission)

## Claim tuples

- H: Is the inter-nuclear gas a smooth rotating disk? | E: Moment maps and p-v diagrams at 0.03'' | R: No butterfly pattern; localized gradients; v/sigma~1 | F: Gas is a clumpy stream dominated by turbulence | **supported**
- H: How much gas lies within each SMBH sphere of influence? | E: CO flux in spheres converted with alpha_CO | R: 7.4e8 (N) and 3.3e9 (S) Msun | F: Reservoir available to feed the SMBHs is directly imaged | **supported**
- H: Is there a significant high-velocity molecular outflow? | E: Identified >500 km/s component and estimated mass and rate | R: 9e8 Msun, ~11% of nuclear gas, 3200-4700 Msun/yr | F: Significant outflow of uncertain origin | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Natural weighting and per-channel feathering to keep line fluxes reliable despite long-baseline decorrelation  
  > "Similarly, by comparing with previously reported $^{12}$CO(2-1) fluxes at a range of scales and resolutions we concluded that our line measurements have not been significantly affected." (3.2 Continuum emission)
- Alternative: Long-baseline EB Xac5575/X8a5f excluded due to poor phase stability  
  > "the final images consider the Xc5148b/X127e alone, which is less affected by signal decorrelation" (A.1 High resolution)
- How they decided it was enough: _not stated_
- Limitation (authors): Continuum fluxes at ~1'' scales biased by decorrelation and sparse uv coverage; dust-based masses biased low  
  > "clearly better *uv* coverage and phase stability are required to measure continuum fluxes at relatively small scales" (3.2 Continuum emission)
- Limitation (authors): Outflow rate geometry uncertain to factor ~3  
  > "We caution that the geometry of this outflow is likely more complex" (4.3 Outflowing Material)
- Caveat (inferred, ours): alpha_CO adopted from lower-resolution work may not apply at 15 pc
- Caveat (inferred, ours): Outflow identification relies on a velocity cut without kinematic modelling
- Caveat (inferred, ours): Residual phase decorrelation may bias fluxes
- Caveat (inferred, ours): Toy shell models fitted by eye

## Reproducibility

- Data public (paper): Data from ALMA programs cited in acknowledgments  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00370.S and #2015.1.00003.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Full cleaning parameters
- Missing: Self-calibration scripts
- Missing: Feathering details
- Missing: Aperture and mask definitions
- Data volume (inferred): ~1-2 TB raw for three configurations; several hundred GB for the long-baseline data
- Score (inferred): 3/5, Data are public and calibration is described in detail, but imaging parameters and scripts are incomplete.
- Rediscovery candidate: no, Complex multi-configuration self-calibration and feathering with missing imaging parameters make exact reproduction hard.

## Links

- Method: (cite: maud17) (WVR scaling algorithm)
- Method: (cite: scoville15) (dust-continuum ISM mass formula)
- Method: (cite: solomon05) (CO luminosity and gas-mass conversion)
- Companion: (cite: cicone18) (lower-resolution CO and [CI] data; alpha_CO and r21 adopted)
- Companion: (cite: saito18) (ALMA program 2015.1.00003.S data included)
- Companion: (cite: medling19) (ALMA continuum of the nuclei and SMBH mass analysis)

## Checks

```json
{
 "quotes": 75,
 "quotes_ok": 75,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 52,
  "rate": 0.634
 },
 "evidence_ok": true
}
```

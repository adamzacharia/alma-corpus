# A Dense Molecular Ringlike Structure in Gaseous CO Depletion Region G34.74−0.12

`2025ApJ...992L..15L` | The Astrophysical Journal Letters 2025 | first author: Lin, Shuting | arXiv: 2509.11475 | DOI: 10.3847/2041-8213/ae0579

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: What is the nature and origin of a pc-scale dense molecular ring-like structure in the 70 um dark, CO-depleted IRDC G34.74-0.12?  
  > "Whether stellar feedback in the very early stages of star formation is sufficient to produce a ring structure on parsec scales remains an open question." (Introduction)
- Target **G34.74-0.12**: coordinates 18h55m09.83s, +01d33m14.5s (ICRS) (mosaic center)  
  > "located at a kinematic distance of 5.1$\pm$0.5 kpc (cite: 2025arXiv250714564L)" (Introduction); "centered at 18$^{\rm h}$55$^{\rm m}$09$^{\rm s}$.83, +01$^{\circ}$33$^{\prime}$14$^{\prime \prime}$.5 (ICRS)" (2 Observation); z/distance 5.1±0.5 kpc  
  > "located at a kinematic distance of 5.1$\pm$0.5 kpc (cite: 2025arXiv250714564L)" (Introduction); "centered at 18$^{\rm h}$55$^{\rm m}$09$^{\rm s}$.83, +01$^{\circ}$33$^{\prime}$14$^{\prime \prime}$.5 (ICRS)" (2 Observation); distance from kinematic distance (Lin et al. 2025, arXiv:2507.14564)  
  > "located at a kinematic distance of 5.1$\pm$0.5 kpc (cite: 2025arXiv250714564L)" (Introduction); "centered at 18$^{\rm h}$55$^{\rm m}$09$^{\rm s}$.83, +01$^{\circ}$33$^{\prime}$14$^{\prime \prime}$.5 (ICRS)" (2 Observation)

## Data provenance

- ALMA projects: 2015.1.01539.S, 2017.1.00716.S, 2018.1.00192.S, 2022.1.01203.S
- bands: 1.3 mm (ASHES) and 3.0 mm (VELLA)  
  > "at 1.3 mm, and Very Low Luminosity/Mass Ratio Clumps (VELLA) ALMA survey (Project ID: 2022.1.01203.S, Wang et al., in prep.) at 3.0 mm." (2 Observation)
- frequencies and spectral setup: C18O 2-1 at 488 kHz (1.33 km/s); N2H+ 1-0 at 16 kHz (0.1 km/s); HNC 1-0 at 31 kHz (0.21 km/s)  
  > "N$_2$H$^+$ ($J$=1-0) was targeted at a channel width of 16 kHz, corresponding to a spectral resolution of 0.1 km s$^{-1}$ at the rest frequency of 93.174 GHz." (2 Observation)
- continuum bandwidth: _not stated_
- arrays: ASHES: 12 m, ACA 7 m, TP; VELLA: 12 m  
  > "The ASHES observations used the 12 m array, the Atacama Compact 7 m Array (ACA), and the total power (TP) antennas." (2 Observation)
- configurations: VELLA: C4 and C1 12 m configurations  
  > "The VELLA observation used two 12 m array configurations (C4 and C1)." (2 Observation)
- baselines: _not stated_
- angular resolution: C18O: 1.68"x1.24"; N2H+: 1.40"x1.30"; HNC: 1.44"x1.34"  
  > "The synthesized beam of the C$^{18}$O (2–1) line is 1.68$''$ $\times$ 1.24$''$, with a position angle (P.A.) of -71.1$^\circ$." (2 Observation)
- max recoverable scale: ~30" (VELLA)  
  > "jointly image to achieve a maximum recoverable scale of $\sim30^{\prime\prime}$" (2 Observation)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: C18O 2-1 (219.560 GHz)
- Line: H2CO 3_0,3-2_0,2 (218.222 GHz)
- Line: N2H+ 1-0 (93.174 GHz)
- Line: HNC 1-0 (90.664 GHz)
- Other facility **IRAM-30m**: C18O, DCO+ maps and CO depletion at 11.8" / 36" resolution (Feng et al. 2020)  
  > "as observed by IRAM-30m at an angular resolution of 11.8$^{\prime \prime}$" (3.1 A Ring-like structure)
- Other facility **VLA**: NH3 (1,1),(2,2) temperature map (Lin et al. in prep.), and GLOSTAR 6 GHz  
  > "based on the temperature map derived from VLA NH$_3$ (1,1) and (2,2) observations" (4.2 Physical structure of the ring)
- Other facility **MeerKAT SMGPS**: 1.3 GHz continuum, no emission detected  
  > "The 1.3 GHz continuum data from the SARAO MeerKAT Galactic Plane Survey (SMGPS)" (4.3 Large-scale environment)
- Other facility **Spitzer, Herschel, WISE**: archival IR images for YSO search  
  > "comparing archival infrared images from Spitzer (3.6, 4.5, 5.8, 8.0 and 24 $\mu$m), Herschel (70 $\mu$m), and WISE" (4.3 Large-scale environment)
- External data: Clump C18O depletion factor ~5 and abundance basis; H13CO+ systemic velocity 79.0 km/s  
  > "C$^{18}$O exhibits a depletion factor of 5 at pc scale" (3.1 A Ring-like structure) [from (cite: Feng2020ApJ...901..145F)]
- External data: Core catalog and masses (Core1, 2, 4, 10) from 1.3 mm  
  > "as labeled by (cite: Morii2023ApJ...950..148M)" (4.3 Large-scale environment) [from (cite: Morii2023ApJ...950..148M)]
- External data: Protostellar outflows and dynamical timescales  
  > "at least four protostellar outflows with estimated dynamical timescales of $10^3$–$10^4$ years (cite: 2025arXiv250714564L)" (4.3 Large-scale environment) [from (cite: 2025arXiv250714564L)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 5.1.1 and 6.4.1 (ASHES); CASA 6.5.4 (VELLA)  
  > "Data calibration was carried out using the CASA versions 5.1.1 and 6.4.1." (2 Observation); "The data calibration and imaging were performed using CASA 6.5.4." (2 Observation)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10% absolute flux calibration  
  > "absolute flux calibration (10%)" (4.2 Physical structure of the ring)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12m, ACA, TP combined in uv domain with almica; VELLA C4 and C1 jointly imaged  
  > "to combine the 12m, ACA, and TP in the UV domain" (2 Observation); "We combine data from two configurations and jointly image" (2 Observation)
- smoothing: _not stated_
- final beam: C18O 1.68"x1.24" PA -71.1; N2H+ 1.40"x1.30" PA 59.0; HNC 1.44"x1.34" PA 66.5  
  > "1.40$''$ $\times$ 1.30$''$ (P.A. = 59.0$^\circ$) and 1.44$''$ $\times$ 1.34$''$ (P.A. = 66.5$^\circ$)" (2 Observation)
- final rms: _not stated_

### Inherited from earlier work

- ASHES calibration/combination and core catalog  
  > "(cite: Sanhueza2019ApJ...886..102S; Morii2023ApJ...950..148M)" (2 Observation) [from (cite: Sanhueza2019ApJ...886..102S; Morii2023ApJ...950..148M)]
- Excitation temperature of 15 K from VLA NH3 temperature map  
  > "(Lin et al., in prep.)" (4.2 Physical structure of the ring) [from Lin et al., in prep.]
- C18O abundance 2e-7 accounting for depletion  
  > "taking into account the depletion of the cloud (cite: Feng2020ApJ...901..145F)" (4.2 Physical structure of the ring) [from (cite: Feng2020ApJ...901..145F)]
- VELLA survey observation details  
  > "Wang et al., in prep." (2 Observation) [from Wang et al., in prep.]

### Not stated but needed to reproduce (our reading)

- CLEAN parameters (robust, deconvolver, threshold, masks) for ASHES and VELLA images
- Continuum-subtraction and line-free channels
- Cell/image size and primary-beam handling
- Exact procedure for ring ellipse fit and PV fitting method/priors
- How the ring mass integration region (solid angle) was defined
- NH3 temperature map (unpublished)
- Fitting algorithm and likelihood for the expanding shell model
- Core flux extraction method for 3 mm and 1.3 mm

## Analysis recipe

1. **Combine and image ALMA data**: ASHES 12m+ACA+TP combined with almica; VELLA two configurations jointly imaged in CASA 6.5.4  
  > "We use MIRIAD-based package, *almica*[^1] (cite: Liu2015ApJ...804...37L), to combine the 12m, ACA, and TP in the UV domain." (2 Observation)
   - software: CASA, almica
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify the ring and measure geometry**: Integrate C18O over 79.9-81.9 km/s, fit ellipse to emission above 10 sigma  
  > "the ring exhibits a diameter of 0.68 pc and an eccentricity value of 0.08, when fitted with an elliptical profile, using emission above the 10$\sigma$ level" (3.1 A Ring-like structure)
   - fitting: _not stated_
   - validation: _not stated_
3. **Kinematics via PV diagrams and expanding shell fit**: Four HNC PV cuts at PA 0,45,90,135 centered on Core10, width ~1.3"; fit thin expanding shell V(x)=V0±Vexp sqrt(1-(x/R)^2) to PA 45 cut  
  > "Each cut, with a width of beam size $\sim$ 1.3$''$, is centered on Core10 and oriented at PA of 0$^{\circ}$, 45$^{\circ}$, 90$^{\circ}$, and 135$^{\circ}$" (4.1 Kinematic structure of the ring)
   - assumption: thin spherical shell expanding at constant velocity  
  > "Assuming the gas is distributed on a thin spherical shell expanding at a constant velocity" (4.1 Kinematic structure of the ring)
   - fitting: _not stated_
   - validation: large 1-sigma uncertainty on Vexp acknowledged  
  > "Note that the fitted expansion velocity exhibits a relatively large uncertainty at the 1$\sigma$ level." (4.1 Kinematic structure of the ring)
4. **Column density and ring mass**: LTE optically thin column density (Mangum & Shirley), mass from C18O with X=2e-7  
  > "Assuming local thermodynamic equilibrium (LTE) and optically thin, the column density of the molecule is calculated using the following equation" (4.2 Physical structure of the ring)
   - parameter: Tex = 15 K; mean molecular weight 2.72 m_H2; X(C18O)=2e-7; distance 5.1 kpc  
  > "The excitation temperature ($T_{\rm ex}$) is set to 15 K" (4.2 Physical structure of the ring)
   - assumption: LTE, optically thin C18O  
  > "The ring mass is estimated using the C$^{18}$O (2–1) line, which is optically thin and includes total flux." (4.2 Physical structure of the ring)
   - fitting: _not stated_
   - validation: uncertainty budget: ~30% column density, ~50% mass; Tex=50 K test raises mass by 2-3x  
  > "the mass estimation can reach up to $\sim$ 50%" (4.2 Physical structure of the ring)
5. **Core masses and CO depletion factors**: 3 mm core mass from optically thin dust; f_D = expected/observed C18O abundance with N_H2 from 1.3 mm dust  
  > "The depletion factor of gaseous CO ($f_{\rm D}$) is then defined as the ratio of the expected abundance $X_{\rm C^{18}O}^E$ to the observed abundance" (Depletion factor estimation)
   - parameter: Tdust=15 K; gas-to-dust 100 (3 mm mass), 78 (depletion); kappa 3mm=0.18, 1.3mm=0.9 cm2/g; mu=2.8; Rgc=5.2 kpc  
  > "We assume a dust temperature of 15 K, a gas-to-dust mass ratio of 100" (Core mass estimation)
   - assumption: Dust temperature equals NH3 gas temperature  
  > "The dust temperature is assumed to be equal to the gas temperature" (Depletion factor estimation)
   - fitting: _not stated_
   - validation: Repeated at 50 K giving f_D 9-63  
  > "which provide the depletion factor of 9-63 on the core scale" (4.4 CO Depletion)

## Software

- **CASA** 5.1.1, 6.4.1, 6.5.4: calibration and imaging  
  > "The data calibration and imaging were performed using CASA 6.5.4." (2 Observation)
- **almica** : combining 12m, ACA and TP in uv domain  
  > "to combine the 12m, ACA, and TP in the UV domain" (2 Observation)
- **myradex** : critical densities  
  > "using the *myradex* package (https://github.com/fjdu/myRadex)" (footnote 2)
- **APLpy, Astropy, Matplotlib** : plotting and analysis  
  > "APLpy (cite: aplpy2012; aplpy2019)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Ring diameter | 0.68 | not stated | pc | 2 | the ring exhibits a diameter of 0.68 pc and an eccentricity value of 0.08 |
| Ring eccentricity | 0.08 | not stated | dimensionless | 2 | an eccentricity value of 0.08 |
| Expansion velocity | 2.3 | ±2.6 | km/s | 3 | expansion velocity ($V_{\text{exp}}$) of 2.3$\pm$2.6 km s$^{-1}$ |
| Shell radius | 16.0 (0.39 pc) | ±5.3 | arcsec | 3 | a shell radius ($R_{\rm shell}$) of 16.0$''$$\pm$5.3$''$ (i.e., 0.39 pc) |
| Ring mass | 109 | ~50% | Msun | 4 | resulting in a total mass of 109 $M_\odot$ |
| Ambient gas mass | 693 | not stated | Msun | 4 | we estimate an ambient gas mass of 693 $M_\odot$ |
| Dynamical timescale | 1.6e5 | not stated | yr | 3 | we derive a dynamical timescale of 1.6 $\times$ 10$^5$ years for the bubble |
| Core-scale depletion factor | 10 to 110 (9-63 at 50 K) | not stated | dimensionless | 5 | with $f_\mathrm{D}$ ranging from 10 to 110 |
| Expected C18O/H2 abundance | 4.94e-7 | not stated | dimensionless | 5 | we derived the $X^{\rm E}_{\rm C^{18}O}$ as 4.94$\times$10$^{-7}$ |
| Core1 mass from 3 mm | 13.3 | not stated | Msun | 5 | We estimate the mass of Core1 as 13.3 $M_{\odot}$ from 3.0 mm emission. |

## Qualitative findings

- No free-free emission or HII region associated with the ring; no mature YSOs in IR  
  > "no free-free emission or HII region is detected in association with this structure" (abstract)

## Claim tuples

- H: Is there a pc-scale dense ring in an early-stage, 70 um dark IRDC? | E: ALMA C18O, HNC, N2H+ imaging of G34.74-0.12 | R: Ring diameter 0.68 pc, redshifted 0.9-2.9 km/s, mass 109 Msun | F: A dense molecular ring-like structure exists in this young region | **supported**
- H: Is the ring expanding? | E: PV cuts and expanding shell fit | R: U-shape along PA 45 only; Vexp 2.3±2.6 km/s | F: Possible slow expansion, weakly constrained | **partially**
- H: Is the ring produced by HII region or SNR feedback? | E: Checked GLOSTAR 6 GHz and MeerKAT 1.3 GHz | R: No free-free emission detected | F: No ionized gas; W44 limited impact but not ruled out | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: HNC used for kinematics since it resolves multiple components better than C18O and N2H+  
  > "Therefore, in the following discussion, we primarily use the HNC (1–0) line to investigate the kinematic properties of the ring." (4.1 Kinematic structure of the ring)
- Alternative: Four origins considered: relic wind-blown bubble, cloud-cloud interaction, temperature gradient, line-of-sight superposition; none conclusively favored  
  > "Four possible origins may result in this ring-like structure" (Conclusion)
- How they decided it was enough: _not stated_
- Limitation (authors): HNC and N2H+ interferometer-only, absorption from missing short spacings; C18O missing flux ~60%  
  > "missing flux in C$^{18}$O (2–1) ($\sim$ 60%), estimated from the IRAM-30m data" (4.4 CO Depletion)
- Caveat (inferred, ours): Expansion velocity consistent with zero within 1 sigma
- Caveat (inferred, ours): C18O velocity resolution 1.33 km/s with ring spanning only three channels
- Caveat (inferred, ours): Tex and abundance assumptions drive mass by factors of a few
- Caveat (inferred, ours): Key inputs (NH3 temperatures, outflows, VELLA) are unpublished or in prep.

## Reproducibility

- Data public (paper): ALMA project IDs given; PI-owned data  
  > "Project ID: 2015.1.01539.S, 2017.1.00716.S, and 2018.1.00192.S" (2 Observation)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Fit routine details
- Missing: NH3 temperature map (in prep.)
- Missing: Core flux extraction
- Data volume (inferred): Several tens to ~100 GB raw across four projects
- Score (inferred): 3/5, Archival ALMA data identified and formulae given, but imaging and fitting settings are missing and several inputs are in prep.
- Rediscovery candidate: no, Imaging recipe incomplete and key inputs unpublished.

## Links

- Method: (cite: Liu2015ApJ...804...37L) (almica data combination)
- Method: (cite: Mangum2015PASP..127..266M) (LTE column density)
- Companion: (cite: Sanhueza2019ApJ...886..102S) (ASHES survey)
- Companion: (cite: Morii2023ApJ...950..148M) (ASHES core catalog)
- Companion: (cite: 2025arXiv250714564L) (outflows and distance in G34.74-0.12)
- Related: ASHES
- Related: VELLA
- Related: GLOSTAR
- Related: SMGPS
- Related: MWISP

## Checks

```json
{
 "quotes": 74,
 "quotes_ok": 74,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 47,
  "rate": 0.58
 },
 "evidence_ok": true
}
```

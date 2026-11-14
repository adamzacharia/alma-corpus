# Molecular remnant of Nova 1670 (CK Vulpeculae). II. A three-dimensional view of the gas distribution and velocity field

`2021A&A...646A...1K` | Astronomy and Astrophysics 2021 | first author: Kamiński, T. | arXiv: 2010.05832 | DOI: 10.1051/0004-6361/202039634

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type observational_alma_primary

## Science

- Fields: evolved_stars, stellar_physics, astrochemistry
- Question: What is the 3D spatio-kinematic structure, distance, age and outflow momentum/energy of the molecular and atomic remnant of Nova 1670 (CK Vul)?  
  > "In this paper, we take a closer look at the three-dimensional spatio-kinematic structure of the atomic and molecular remnant of Nova 1670." (Introduction)
- Target **CK Vul (Nova 1670 remnant)**: coordinates l = 63.3 deg (Galactic longitude)  
  > "With the object’s Galactic longitude of $l$=63.3$^\circ$" (2 Revised physical parameters of the remnant); "Its Gaia Data Release 2 parallax (cite: gaia) implies a distance of 4.9 kpc or a 1$\sigma$-like confidence interval 3.0–8.1 kpc" (2 Revised physical parameters of the remnant); z/distance >2.6 kpc; adopted 3.5 (+2.1/-0.9) kpc, upper limit 5.7 kpc  
  > "With the object’s Galactic longitude of $l$=63.3$^\circ$" (2 Revised physical parameters of the remnant); "Its Gaia Data Release 2 parallax (cite: gaia) implies a distance of 4.9 kpc or a 1$\sigma$-like confidence interval 3.0–8.1 kpc" (2 Revised physical parameters of the remnant); distance from SHAPE model of the large optical hourglass nebula (Hubble flow, 340 yr age), with Gaia DR2 parallax of a field star as an independent check  
  > "With the object’s Galactic longitude of $l$=63.3$^\circ$" (2 Revised physical parameters of the remnant); "Its Gaia Data Release 2 parallax (cite: gaia) implies a distance of 4.9 kpc or a 1$\sigma$-like confidence interval 3.0–8.1 kpc" (2 Revised physical parameters of the remnant)

## Data provenance

- ALMA projects: 2017.1.00999.S, 2017.A.00030.S, 2016.1.00448.S, 2015.A.00013.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.45" in CO  
  > "we are limited by our angular resolutions of 0.45$''$ in CO and 1.1$''$ in the optical" (3.4 Step 4: Extended bubbles of CO emission)
- max recoverable scale: ≈23" (limited short baselines); ALMA recovers ~52% of CO 1-0 flux  
  > "the interferometric data are not sensitive to structures larger than $\approx$23$''$ owing to the limited range of short interferometric baselines (Paper I)" (3.4 Step 4: Extended bubbles of CO emission)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO (12CO, 13CO) J=1-0 (also 2-1) (not stated)
- Line: SiO, HCN, HCO+, N2H+ several transitions averaged (not stated)
- Other facility **Gemini**: Halpha and [N II] image from 2010 (Hajduk et al. 2013)  
  > "we used a map of H$\alpha$ and \[N II\] emission obtained in 2010 with Gemini by (cite: hajduk2013)" (3.4 Step 4: Extended bubbles of CO emission)
- Other facility **Gaia DR2**: Parallax of field star variable 2 behind southern lobe  
  > "Its Gaia Data Release 2 parallax (cite: gaia) implies a distance of 4.9 kpc" (2 Revised physical parameters of the remnant)
- External data: CO column densities in SW, NE, NW, SE regions and central region from non-LTE models  
  > "In our calculations we use results from Paper I where column densities of CO have been estimated in four parts of the CK Vul’s remnant" (4 Mass, momentum, and kinetic energy in the lobes) [from Kaminski et al. 2020, Paper I (cite: Kami2020)]
- External data: Optical images and long-slit spectra of the hourglass nebula  
  > "compared it to images and long-slit spectra presented in (cite: hajduk2013)" (2 Revised physical parameters of the remnant) [from (cite: hajduk2013)]
- External data: CO/H2 abundance of 2e-4  
  > "using a CO abundance of 2$\times$10$^{-4}$ relative to H$_2$ (cite: Bujarrabal2001)" (4 Mass, momentum, and kinetic energy in the lobes) [from (cite: Bujarrabal2001)]

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
- weighting robust: _not stated_
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
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA observations, averaged data cubes, and line identification used here  
  > "The observables were extracted from average data-cubes introduced in Paper I." (3 Three-dimensional molecular remnant) [from Paper I (cite: Kami2020)]
- Definitions of momentum and kinetic energy in outflow  
  > "We follow closely the definitions of linear angular momentum and kinetic energy in the outflow of (cite: Bujarrabal2001)" (4 Mass, momentum, and kinetic energy in the lobes) [from (cite: Bujarrabal2001)]

### Not stated but needed to reproduce (our reading)

- Exact ALMA reduction, calibration, imaging parameters (all in Paper I)
- SHAPE model files and parameter values (bump definitions) not given
- Procedure for flux weighting of the 312 km/s velocity
- How the 52% flux recovery was computed in detail
- Uncertainty derivation for the distance

## Analysis recipe

1. **Revise distance via hourglass model**: SHAPE model of optical hourglass compared with images and spectra; Hubble flow; distance from angular size, velocity and kinematic age  
  > "We assumed a simple Hubble-flow expansion of the shells." (2 Revised physical parameters of the remnant)
   - software: SHAPE
   - parameter: apex radial velocity ±820 km/s, radial extent 36", age 340 yr  
  > "With the radial extent of each lobe of 36$''$ and the kinematical age of 340 yr" (2 Revised physical parameters of the remnant)
   - assumption: Lobe shape along sight line same as in sky plane; optically thin  
  > "We assumed that the shape and size of the nebula are the same along the line of sight as in the sky plane." (2 Revised physical parameters of the remnant)
   - fitting: _not stated_
   - validation: Compared with slit spectra and Gaia parallax of a background star  
  > "Such a model reproduces very well the spectra obtained with a slit located at the high-proper motion star west of CK Vul" (2 Revised physical parameters of the remnant)
2. **3D model of molecular lobes**: Iterative manual SHAPE modelling compared with intensity maps, channel maps and PV diagrams; linear velocity law v=kr; neutral shells, ion shells, CO bubbles  
  > "SHAPE models were iteratively constructed by comparing the simulated spatio-kinematic structure to products of the observational data" (3 Three-dimensional molecular remnant)
   - software: SHAPE
   - parameter: k=37 km/s/arcsec within 1", k=58–68 outward; northern lobe i=10°, southern i=0  
  > "$k$=37 km s$^{-1}$ arcsec$^{-1}$ near the central region (i.e., roughly within a radius, $r$, of 1$''$) and $k$=58–68 km s$^{-1}$ arcsec$^{-1}$ outwards" (3.1 Step 1: General shape)
   - assumption: Optically thin, homologous expansion, arbitrary flux scale, single temperature ~14 K  
  > "Our simulations were performed within the optically-thin limit and we assumed a homologous expansion" (3 Three-dimensional molecular remnant)
   - fitting: Manual, qualitative; no unique solution (k and i degenerate)  
  > "The values of $k$ and $i$ are degenerate and cannot be determined independently." (3.1 Step 1: General shape)
   - validation: Visual comparison of simulated and observed PV diagrams  
  > "A comparison between sample PV diagrams of simulated and observed emission of SiO is shown in Fig. [6](#fig-PV-neutrals)." (Step 2: Distribution of neutral species)
3. **Mass, momentum, kinetic energy**: CO column density times area, converted to H2 mass with CO abundance; momentum and Ekin from model deprojected velocities at 2.6, 3.5, 5.7 kpc  
  > "By multiplying these column densities by the respective sizes of the regions, we estimated the number of CO molecules" (4 Mass, momentum, and kinetic energy in the lobes)
   - parameter: Lobe velocity 312 km/s, central 50 km/s  
  > "we calculated a flux-weighted average CO velocity in the lobes (at $r>$2$''$) of CO of 312 km s$^{-1}$." (4 Mass, momentum, and kinetic energy in the lobes)
   - assumption: CO/H2 = 2e-4  
  > "using a CO abundance of 2$\times$10$^{-4}$ relative to H$_2$" (4 Mass, momentum, and kinetic energy in the lobes)
   - fitting: _not stated_
   - validation: Compared with PPN ranges of Bujarrabal et al. 2001  
  > "Values at the considered distances are within the ranges of $M\varv$ and $E_{\rm kin}$ found by (cite: Bujarrabal2001) for PPNe" (4 Mass, momentum, and kinetic energy in the lobes)

## Software

- **SHAPE** X.alpha.619 (2018): 3D spatio-kinematic modelling of the optical hourglass and molecular remnant  
  > "We again used the SHAPE package (version X.$\alpha$.619 from 2018) to reconstruct the overall spatio-kinematic structure in 3D." (3 Three-dimensional molecular remnant)
- **SAO DS9** : figure preparation  
  > "Several figures in this paper were prepared with `matplolib` (cite: matplotlib) and with SAO DS9." (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Distance lower limit | >2.6 | not stated | kpc | 1 | We can thus quite confidently claim that the distance to CK Vul is $>$2.6 kpc and we adopt 5.7 kpc as a plausible upper limit. |
| Kinematic age of outer molecular shell | 254 | +153/-65 | yr | 2 | ballistic motion with such a speed would take $254^{+153}_{-65}$ yr to reach the outer parts of the molecular remnant |
| Maximum deprojected molecular speed | 470 | not stated | km/s | 2 | the outermost emission is located at 7.2$''$ where gas moves with a deprojected speed of 470 km s$^{-1}$ |
| CO flux recovered by ALMA | 52 | not stated | % | 2 | the ALMA maps recover only about 52% of the line flux |
| Total H2 mass at 3.5 kpc (analysed regions) | 0.59 | not stated | Msun | 3 | / All     /              /            / 0.32          / 0.59          / 1.56 |
| Total momentum at 3.5 kpc | 1.8e40 | not stated | g cm/s | 3 | / 9.9e39   / 1.8e40   / 4.8e40 |
| Total kinetic energy at 3.5 kpc | 2.3e47 | not stated | erg | 3 | / 1.3e47  / 2.3e47  / 6.2e47 |

## Qualitative findings

- Molecular lobes are not made in a single ejection; point-symmetric structures suggest episodic jets of varying orientation  
  > "Neutral species and ions fill walls of complex structures that could not have been created in a single mass ejection episode." (Summary)

## Claim tuples

- H: Is CK Vul at 0.7 kpc? | E: SHAPE model of the hourglass nebula | R: Inclination below ~35 deg implies d>2.6 kpc; model at 5.7 kpc | F: Distance is much larger and CK Vul much more luminous (12–60 Lsun) | **supported**
- H: Is the molecular remnant from the 1670 eruption? | E: Kinematic age from 3D models | R: 240–470 yr at 3.5 kpc | F: Consistent with 17th-century origin or later, not uniquely constrained | **partially**
- H: Are CK Vul's outflows similar to PPNe? | E: Momentum and kinetic energy from CO | R: Values within PPN ranges | F: Similar to PPNe outflows | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Single precessing jet judged highly unlikely; magnetic merged star mass loss considered as alternative  
  > "A single jet, even a precessing one, is highly unlikely to be responsible for the observed characteristics." (3.2 Step 2: Distribution of neutral species)
- How they decided it was enough: _not stated_
- Limitation (authors): Model is non-unique owing to k–i degeneracy; masses underestimated  
  > "Thus, our model does not generally offer a unique representation of the available data." (3.1 Step 1: General shape)
- Caveat (inferred, ours): Manual SHAPE models without quantitative fit or uncertainties
- Caveat (inferred, ours): Distance depends on assumed Hubble flow and a single inclination argument
- Caveat (inferred, ours): Large missing flux affects mass estimates

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: SHAPE model files
- Missing: Paper I reduction details
- Missing: Column densities from Paper I
- Data volume (inferred): Not stated; likely tens to hundreds of GB for four ALMA projects (raw)
- Score (inferred): 2/5, Manual, qualitative modelling with no released model files; relies on Paper I.
- Rediscovery candidate: no, Main results come from manual 3D modelling that is not reproducible numerically.

## Links

- Method: Steffen & Koning 2017 (cite: steffen) (SHAPE software)
- Companion: Kaminski et al. 2020, Paper I (cite: Kami2020) (ALMA/SMA data and non-LTE analysis)

## Checks

```json
{
 "quotes": 52,
 "quotes_ok": 52,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 31,
  "rate": 0.443
 },
 "evidence_ok": true
}
```

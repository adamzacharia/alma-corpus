# Recombination Lines and Molecular Gas from Hypercompact H II regions in W51 A

`2020ApJ...899...94R` | The Astrophysical Journal 2020 | first author: Rivera-Soto, Rudy | arXiv: 2007.12276 | DOI: 10.3847/1538-4357/aba749

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, milky_way_ism
- Question: What are the physical properties, ionized-gas kinematics and molecular-gas kinematics of compact (hypercompact) HII regions in W51 A?  
  > "We present a detailed characterization of the population of compact radio-continuum sources in W51 A using subarcsecond VLA and ALMA observations." (abstract)
- Target **W51 A**: coordinates _not stated_; z/distance d = 5.4 kpc  
  > "which corresponds to 0.026 pc at a distance of $d = 5.4$ kpc (cite: Sato10)" (Source Selection); distance from Sato10 (cite: Sato10)  
  > "which corresponds to 0.026 pc at a distance of $d = 5.4$ kpc (cite: Sato10)" (Source Selection)

## Data provenance

- ALMA projects: 2013.1.00308.S
- bands: VLA Ku-band (2 cm); ALMA lines near 218-232 GHz  
  > "The VLA Ku-band observations were executed for a total time of 1 hour in D-configuration on March 02, 2013, plus 5 hours in B-configuration on October 01, 2013." (Observational Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: ALMA 12m array, two configurations; VLA D and B configurations  
  > "The ALMA observations were executed as part of Cycle 2 project 2013.1.00308.S in two 12m-array configurations." (Observational Data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: H30alpha beam 0.32"x0.31"; all RL/continuum images convolved to 0.40"  
  > "a synthesized beam FWHM of $0.32\ensuremath{''} \times 0.31\ensuremath{''}$, $\mathrm{P.A.} = 50.7 \degree$" (Observational Data)
- max recoverable scale: _not stated_
- sensitivity: H30alpha rms about 3.53 mJy/beam per channel; 2-cm continuum rms about 50 uJy/beam  
  > "The typical *rms* noise in all channels is about $3.53$ mJy beam$^{-1}$." (Observational Data)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Data from Ginsburg et al. 2016 (VLA) and Ginsburg et al. 2017 (ALMA data release)  
  > "We also use the molecular-line cubes from the data release of (cite: Ginsburg17)." (Observational Data)
- Line: H30alpha recombination line (231.901 GHz)
- Line: H77alpha recombination line (14.129 GHz)
- Line: H2CO 3(0,3)-2(0,2) (218.22219 GHz)
- Line: H2CO 3(2,1)-2(2,0) (218.76007 GHz)
- Line: SO 6(5)-5(4) (219.94944 GHz)
- Other facility **VLA**: 2-cm continuum and H77alpha images (program 13A-064)  
  > "The observations were made under program 13A-064 and were originally reported in (cite: Ginsburg16)." (Observational Data)
- External data: Catalog of cm-continuum sources in W51 A used for source selection  
  > "We first impose a size cut to the catalog of (cite: Ginsburg16)" (Source Selection) [from Ginsburg16]
- External data: Molecular-line cubes (H2CO, SO) from ALMA data release  
  > "We also use the molecular-line cubes from the data release of (cite: Ginsburg17)." (Observational Data) [from Ginsburg17]
- External data: Atomic and molecular line parameters from Splatalogue, mainly CDMS  
  > "We retrieved atomic and molecular parameters from *Splatalogue*[^1], mainly taking the laboratory measurements from the Cologne Database for Molecular Spectroscopy (CDMS)" (Observational Data) [from Muller05]

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
- weighting robust: H77alpha cube made with uniform weighting (VLA)  
  > "The H77$\alpha$ cube ($\nu_{\rm 0, ~H77} = 14.129$ GHz) was created with uniform weighting" (Observational Data)
- uv taper: _not stated_
- cell size: 0.05"  
  > "we regridded both the 2-cm continuum and H77$\alpha$ images to pixel dimensions of $0.05 \ensuremath{''}$, matching those of the ALMA images" (Observational Data)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 2-cm continuum, H77alpha and H30alpha images regridded to 0.05" pixels and convolved to common circular 0.40" beam  
  > "convolved the 2-cm continuum, H$77\alpha$, and H$30\alpha$ images to a common circular beam with HPBW$=0.40\ensuremath{''}$" (Observational Data)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- VLA observations and data reduction  
  > "We use the 2-cm continuum and Hydrogen $77\alpha$ RL images and refer the reader to their paper for details on the observations and data reduction." (Observational Data) [from Ginsburg16]
- ALMA data reduction  
  > "We refer to (cite: Ginsburg17) for details on the data reduction." (Observational Data) [from Ginsburg17]
- RL analysis of broadening components and kinematics  
  > "In this paper we perform a RL analysis similar to that presented in (cite: KZK08) for brighter RL sources." (Recombination Lines) [from KZK08]

### Not stated but needed to reproduce (our reading)

- ALMA calibration and imaging details (CASA version, robust, continuum subtraction) are only in Ginsburg17
- Exact aperture positions and background ring radii for flux extraction
- PySpecKit baseline and fit settings
- Velocity ranges used for baseline fitting
- Moment-0 integration ranges

## Analysis recipe

1. **Select compact cm sources**: Size cut radii<1" on Ginsburg16 catalog gives catalog A (29); sources within ALMA field give catalog B (20)  
  > "The resulting catalog *A* is composed of 29 objects (see table [1](#tab:catalogs))." (Source Selection)
   - assumption: d = 5.4 kpc  
  > "which corresponds to 0.026 pc at a distance of $d = 5.4$ kpc (cite: Sato10)" (Source Selection)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure sizes, fluxes, optical depths, EM, ne, Lyman rate from 2-cm continuum**: Interactive 2D Gaussian fits; background-subtracted flux; brightness temperature, tau, EM, ne,c, Lc from equations  
  > "We performed an interactive 2D Gaussian fitting in CASA v.5.3.0-143 (cite: McMullin07) on each source" (2-cm Continuum)
   - software: CASA
   - assumption: Te = 7500 K; alpha_B = 2e-13 cm3/s  
  > "when assuming $\rm T_{\rm e} = 7500K$ as the typical temperature for an ionized plasma (cite: Osterbrock06)" (2-cm Continuum)
   - fitting: _not stated_
   - validation: sources mixed with background flagged as unreliable  
  > "are significantly mixed with background emission, such that the results of Gaussian fitting are unreliable." (2-cm Continuum)
3. **Extract RL spectra and derive broadening and ne,RL**: Spectra from 2sigma aperture, scaled by 1/0.95; Gaussian fits; thermal, dynamical, pressure broadening via Voigt; ne from GM12 eq. A.4  
  > "The spectra are then scaled up by a 1/0.95 factor to account for the flux outside the aperture." (Recombination Lines)
   - software: PySpecKit
   - parameter: R_apert = 2 x 0.42465 Theta_conv  
  > "$R_{\rm apert} = 2 \times 0.42465 \Theta_{\rm conv}$" (Recombination Lines)
   - assumption: _not stated_
   - fitting: Gaussian fits with baseline removal  
  > "The Gaussian fitting and baseline removal was done using *PySpecKit*" (Recombination Lines)
   - validation: _not stated_
4. **Classify molecular line profiles for infall/expansion**: Extract H2CO and SO spectra in same apertures; qualitative profile classification (blue/red-peaked, inverse P-Cygni); compare with H30alpha centroid  
  > "We extracted the molecular-line spectra of all the cm sources in catalog $B$ over the same apertures as for the RL’s." (Molecular morphology and profiles)
   - assumption: _not stated_
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** v.5.3.0-143: 2D Gaussian fitting of continuum sources  
  > "We performed an interactive 2D Gaussian fitting in CASA v.5.3.0-143 (cite: McMullin07) on each source" (2-cm Continuum)
- **PySpecKit** : Gaussian fitting and baseline removal of RL spectra  
  > "The Gaussian fitting and baseline removal was done using *PySpecKit*" (Recombination Lines)
- **NumPy** : listed in software section  
  > "NumPy (cite: Numpy), PySpecKit (cite: GinsburgMirocha11), APLpy (cite: AplPy), CASA (cite: McMullin07)" (Software)
- **APLpy** : listed in software section (plotting)  
  > "NumPy (cite: Numpy), PySpecKit (cite: GinsburgMirocha11), APLpy (cite: AplPy), CASA (cite: McMullin07)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Deconvolved diameter of sources with valid fits | 1e-3 to 1e-2 pc (10/20 sources) | not stated | pc | 2 | We derive diameters for 10/20 sources in the range $D \sim 10^{-3}$ to $\sim 10^{-2}$ pc |
| Continuum electron density ne,c | 1e4 to 1e5 | not stated | cm^-3 | 2 | electron densities are of order $n_{\rm e, c} \sim 10^4$ to $10^5$ cm$^{-3}$ |
| e2 H30alpha peak flux | 1365.84 | 3.11 | mJy | 3 | e2 / $3.26\pm0.10$ / $56.84\pm0.53$ / $34.42\pm1.25$ / $1365.84\pm3.11$ |
| e2 RL electron density | 3.62e5 | 0.29e5 | cm^-3 | 3 | e2$^a$ / 18.52 / 9.68 / 21.18 $\pm$ 1.70 / 7500 / 3.62 $\pm$ 0.29 |
| H77-H30 velocity differences | -1 to -4 | not stated | km/s | 3 | The velocity differences range from $\Delta v_{77-30} \approx - 1$ to $- 4$ km s$^{-1}$  for all sources except for d2 |
| Infall candidates | 3 of 8 embedded HC HII (e2, e3, e4) | not stated | dimensionless | 4 | we have 3 out of 8 HC HII’s (e2, e3, e4) whose local molecular gas appears to have bulk infall motions |

## Qualitative findings

- Ionized gas kinematics is outflow in all 7 sources with both RLs  
  > "We found bulk *outward* motions in the ionized gas for *all* the 7 sources" (Discussion)
- Most sources are ionized by early B-type stars  
  > "Therefore, 5 to 8 out of 10 sources are ionized by early B-type stars, not O-type stars." (Physical Properties of the HII Regions)

## Claim tuples

- H: Are HC HII regions in W51 A as dense as classical HC HII definition? | E: Derived ne from 2-cm continuum and RLs | R: ne ~1e4-1e5 cm^-3 from both methods | F: Lower than typical HC HII, follow the ne-D relation of UC HII regions | **supported**
- H: Is the ionized gas accreting or outflowing? | E: Compared H77alpha and H30alpha centroids | R: H77alpha always blueshifted relative to H30alpha | F: Ionized gas outflowing; accretion mostly ceased | **supported**
- H: Do embedded HC HII show molecular infall or expansion? | E: Classified H2CO and SO line profiles | R: 5 expansion, 3 infall candidates | F: Mixture of expansion and infall | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: More complex kinematics (bipolar outflows, rotation, multiplicity) not considered for profile asymmetries  
  > "We do not consider more complex kinematics as alternate mechanisms for producing profile asymmetries" (Molecular morphology and profiles)
- How they decided it was enough: _not stated_
- Limitation (authors): Sidelobes from bright emission affect several spectra; d2 H77alpha possibly biased  
  > "Sources d2, e2, e4, and e8n have a negative bowl in their H$30\alpha$ spectra toward redshifted velocities caused by sidelobes of nearby bright emission." (Recombination Lines)
- Caveat (inferred, ours): Infall/expansion classification is qualitative with no radiative transfer modelling
- Caveat (inferred, ours): Small sample (7 and 8 sources)
- Caveat (inferred, ours): ne from RL and continuum disagree, suggesting LTE or co-spatial assumptions fail
- Caveat (inferred, ours): Fixed Te=7500 K assumed

## Reproducibility

- Data public (paper): ALMA project 2013.1.00308.S and VLA 13A-064 used; data releases of Ginsburg16/17  
  > "This paper makes use of the ALMA data set 2013.1.00308.S and VLA data set 13A-064." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Reduced cubes from Ginsburg17 data release
- Missing: Aperture and background ring definitions
- Missing: Fit initial guesses
- Data volume (inferred): tens of GB (ALMA Cycle 2 mosaic, two configurations) plus VLA images
- Score (inferred): 3/5, Analytic equations are given, but data reduction is deferred to earlier papers and many extraction details are missing.
- Rediscovery candidate: yes, Public data, equations and numeric tables are given, though processed cubes are needed.

## Links

- Method: KZK08 (RL broadening and kinematics analysis)
- Method: GM12 (pressure-broadening electron density formula)
- Companion: Ginsburg16 (VLA data and source catalog)
- Companion: Ginsburg17 (ALMA data reduction and release)
- Related: VLA 13A-064

## Checks

```json
{
 "quotes": 52,
 "quotes_ok": 52,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 36,
  "rate": 0.48
 },
 "evidence_ok": true
}
```

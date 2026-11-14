# Inefficient jet-induced star formation in Centaurus A. High resolution ALMA observations of the northern filaments

`2017A&A...608A..98S` | Astronomy and Astrophysics 2017 | first author: Salomé, Q. | arXiv: 1710.09851 | DOI: 10.1051/0004-6361/201731429

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars, star_formation
- Question: Why does molecular gas in the northern filaments of Centaurus A not follow the Kennicutt-Schmidt law, and does the eastern CO bright region differ from the rest of the filaments?  
  > "The goal of this paper is to understand why the molecular gas in the northern filaments of Centaurus A does not follow the Kennicutt-Schmidt law, and whether there is a difference between the eastern CO bright region and the rest of the filaments." (Introduction)
- Target **Centaurus A (NGC 5128) northern filaments**: coordinates _not stated_; z/distance 3.8 Mpc  
  > "At the distance of Centaurus A (3.8 Mpc, $1''\sim 18.3\: pc$; (cite: Harris_2010))" (2.1 ALMA data); distance from Harris et al. 2010  
  > "At the distance of Centaurus A (3.8 Mpc, $1''\sim 18.3\: pc$; (cite: Harris_2010))" (2.1 ALMA data)

## Data provenance

- ALMA projects: 2015.1.01019.S
- bands: Band 3  
  > "during Cycle 3 using Band 3 receivers" (2.1 ALMA data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12 m array; 34-pointing mosaic  
  > "consists in a mosaic of 34 pointings, each with an integration time between 140 and 430s." (2.1 ALMA data)
- configurations: _not stated_
- baselines: 15 m to 704 m  
  > "The baselines ranged from 15 m to 704 m" (2.1 ALMA data)
- angular resolution: 1.30'' x 0.99'' (PA=81.5 deg)  
  > "providing a resolution of $1.30''\times 0.99''$ ($PA=81.5$$^{\circ}$)" (2.1 ALMA data)
- max recoverable scale: 14'' (~260 pc)  
  > "The largest angular scale recovered by the interferometer is $14''$" (2.1 ALMA data)
- sensitivity: noise histogram peaks at 6.5 mJy/beam at 1.47 km/s  
  > "The histogram of the noise level peaks at 6.5 mJy/beam at a spectral resolution of $1.47\: km.s^{-1}$." (2.1 ALMA data)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=1-0 (not stated)
- Other facility **APEX**: 12CO(2-1) mapping and total gas mass for comparison  
  > "we mapped the outer filaments (hereafter the northern filaments) in $^{12}CO$(2-1) with APEX." (Introduction)
- Other facility **MUSE**: optical emission lines for velocity and BPT diagrams  
  > "we focus on the fields of view previously observed in the northern filaments with MUSE" (3.4 Excitation of the clouds)
- Other facility **ACA**: short-spacing data, not analysed here  
  > "These data will be presented in a future paper" (2.3 Effect of large-scale filtering)
- External data: APEX CO(2-1) total gas mass (9.8e7 Msun)  
  > "We determined that the total molecular gas mass is $(9.8\pm 0.6)\times 10^7\: M_\odot$." (2.3 Effect of large-scale filtering) [from (cite: SalomeQ_2016b)]
- External data: Milky Way cloud distributions for comparison  
  > "We added the 2D histograms of the molecular clouds in the Milky Way (cite: MAMD_2017a)." (3.3 Larson's relations) [from (cite: MAMD_2017a)]

## Processing

### Calibration

- pipeline or manual: CASA with the supplied script  
  > "The data were calibrated using the Common Astronomy Software Applications (CASA) and the supplied script." (2.1 ALMA data)
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

- Gaussian decomposition and clustering method for cloud extraction  
  > "we first used a Gaussian decomposition method developed by (cite: MAMD_2017a)." (2.2 Cloud identification method) [from (cite: MAMD_2017a)]
- Energy injection rate evaluation  
  > "Following (cite: MAMD_2017a), we evaluated the energy injection rate in the clouds." (4 Discussion) [from (cite: MAMD_2017a)]
- Gaussian line fitting of MUSE lines  
  > "Each line was fitted by a Gaussian at each spatial resolution element (see (cite: Hamer_2014) for the details)" (3.4 Excitation of the clouds) [from (cite: Hamer_2014)]

### Not stated but needed to reproduce (our reading)

- Imaging parameters (weighting, robust, cell, image size, deconvolver, masking)
- CASA version
- Continuum subtraction and line-free channels
- Parameters of the Gaussian decomposition code
- Whether the data were primary-beam corrected before extraction and how noise was handled
- Pointing coordinates and phase centre
- Flux calibrator and flux scale uncertainty

## Analysis recipe

1. **Extract clouds from the CO cube**: Gaussian decomposition and clustering to build a modelled cube, then clumpfind on it  
  > "We then applied the *clumpfind* algorithm (cite: Clumpfind) on this cube with five equally spaced threshold values from 6.5 to 58.5 mJy/beam." (2.2 Cloud identification method)
   - software: clumpfind
   - parameter: Keep sizes >= beam, v_cent between -350 and -100 km/s, sigma_v <~ 50 km/s  
  > "We kept the structures with a size larger or equal to the beam size." (2.2 Cloud identification method)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive cloud sizes, velocity dispersions, masses, densities**: Inertia-matrix radius; emission-weighted velocity moments; Solomon 1987 L'CO; alpha_CO; density from mass and radius  
  > "The mass is then estimated by applying a CO-to-$H_2$ conversion factor of $\alpha_{CO}=4.3\: M_\odot.(K.km.s^{-1}.pc^2)^{-1}$ (cite: Bolatto_2013)." (3.2 Giant molecular clouds)
   - assumption: Prolate clouds; alpha_CO=4.3; mu=2.4; f_H2=1; distance 3.8 Mpc  
  > "We assume that the GMCs are prolate and adopt the following definition of the angular radius" (3.2 Giant molecular clouds)
   - fitting: Power-law fit to high-mass end of mass distribution assuming 1/sqrt(N) uncertainty; log-normal fit to surface density PDF  
  > "assuming a $1/\sqrt{N}$ uncertainty for each data point" (3.2 Giant molecular clouds)
   - validation: Compared with literature GMC statistics (M33, LMC, M51, MW)  
  > "| Quantity | Horseshoe | SF clouds | M33 | LMC | M51 | MW |  |" (Results, Giant molecular clouds (Table of statistics))
3. **Stability, pressure and energy injection**: Compute t_ff, t_dyn, virial parameter, internal pressure and energy injection rate per cloud  
  > "$\alpha_{vir}=5\sigma_v^2\, R/(GM)\sim t_{ff}^2/t_{dyn}^2$" (4 Discussion)
   - assumption: Turbulence in steady state, injection balanced by dissipation  
  > "Here we make the assumption that turbulence has reached a steady state where energy injection is balanced by energy dissipation." (4 Discussion)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compare CO with MUSE excitation**: Pixel-by-pixel velocity comparison and BPT diagrams  
  > "We computed pixel-by-pixel BPT diagrams based on the $H\alpha$, \[N@\], $H\beta$" (3.4 Excitation of the clouds)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration  
  > "The data were calibrated using the Common Astronomy Software Applications (CASA) and the supplied script." (2.1 ALMA data)
- **clumpfind** : cloud identification  
  > "We then applied the *clumpfind* algorithm (cite: Clumpfind) on this cube" (2.2 Cloud identification method)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of GMCs | 140 | not stated | clouds | 1 | we obtained a catalogue of 140 GMCs |
| Total GMC mass | 1.6e7 | not stated | Msun | 2 | The total mass of the GMCs is $\sim 1.6\times 10^7\: M_\odot$. |
| Mean velocity dispersion | 5.4 | 1.4 | km/s | 2 | with an average value of $5.4\pm 1.4\: km.s^{-1}$ |
| Mass function slope alpha (M>=9.3e4 Msun) | 0.75 | 0.18 | dimensionless | 2 | For $M\geq 9.3\times 10^4\: M_\odot$ we obtain $\alpha=0.75\pm 0.18$. |
| Mean surface density | 46.5 | 19.1 | Msun/pc^2 | 2 | average value of $46.5\pm 19.1\: M_\odot.pc^{-2}$ |
| Mean virial parameter | 11.1 | 6.6 | dimensionless | 3 | with an average value of $11.1\pm 6.6$ |
| Mean internal pressure | 6.0e-11 | 4.7e-11 | dyn/cm^2 | 3 | we found an internal pressure $P_{int}=(6.0\pm 4.7)\times 10^{-11}\: dyn.cm^{-2}$ |
| CO minus Halpha velocity | -35.3 | 23.2 | km/s | 4 | $v_{CO}-v_{H\alpha}=-35.3\pm 23.2\: km.s^{-1}$ |

## Qualitative findings

- Clouds have size, sigma_v and mass similar to Milky Way clouds but higher virial parameters; the Horseshoe complex is shock-excited and shows no star formation  
  > "These clouds have size, velocity dispersion, and mass of the same order than molecular clouds in the Milky Way." (5 Conclusion)

## Claim tuples

- H: Why star formation is inefficient in the northern filaments | E: Extract GMCs from ALMA CO(1-0) and derive their dynamical properties | R: Virial parameters ~8-12, free-fall time about twice the dynamical time | F: Clouds are not gravitationally bound, which limits star formation | **supported**
- H: Horseshoe complex differs from the rest of the filaments | E: Compare CO with Halpha, FUV, clusters and MUSE BPT | R: Horseshoe has Halpha but no FUV or clusters; shock excited | F: Two regimes: inefficient Horseshoe and star-forming Vertical filament | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA 12 m data recover only ~20% of APEX mass due to spatial filtering; narrow radius range limits Larson-relation tests  
  > "the present data recover only 20% of the total molecular gas mass found by APEX." (5 Conclusion)
- Caveat (inferred, ours): Cloud properties depend on clumpfind splitting of filtered emission
- Caveat (inferred, ours): Constant alpha_CO=4.3 assumed in a jet-shocked environment
- Caveat (inferred, ours): Short-spacing filtering biases sizes and virial parameters

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Cloud catalogue available at CDS  
  > "a catalogue of the molecular clouds are only available at the CDS via anonymous ftp" (footnote)
- Missing: Imaging parameters
- Missing: Decomposition code settings
- Data volume (inferred): ~50-100 GB raw
- Score (inferred): 3/5, Archival project and clear formulas, but imaging and decomposition settings are missing.
- Rediscovery candidate: no, Imaging and extraction parameters are not given.

## Links

- Method: (cite: MAMD_2017a) (Gaussian decomposition and clustering method)
- Companion: (cite: SalomeQ_2016b) (APEX CO(2-1) mapping of the same filaments)

## Checks

```json
{
 "quotes": 45,
 "quotes_ok": 45,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 1,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 32,
  "rate": 0.457
 },
 "evidence_ok": true
}
```

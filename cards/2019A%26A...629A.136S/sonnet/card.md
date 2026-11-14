# A rotating fast bipolar wind and disk system around the B[e]-type star MWC 922

`2019A&A...629A.136S` | Astronomy and Astrophysics 2019 | first author: Sánchez Contreras, C. | arXiv: 1907.06415 | DOI: 10.1051/0004-6361/201936057

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, stellar_physics
- Question: What are the structure, kinematics and physical conditions of the ionized disk and fast wind at the core of the B[e] star MWC 922, and what is its evolutionary nature?  
  > "We have modelled our data using the non-LTE radiative transfer code MORELI, which has enabled us to constrain the morphology, kinematics and physical conditions at the core of this outstanding object." (Conclusions)
- Target **MWC 922 (Red Square Nebula)**: coordinates RA=18h21m16.0570s, Dec=-13d01m25.72s (J2000)  
  > "The 3 mm continuum surface brightness peaks at coordinates RA=18$^{\rm h}$21$^{\rm m}$16.0570s and Dec=$-$13$^\circ$01$'$25$.\!\!^{\prime\prime}$72 (J2000)." (3.1 Continuum); "Throughout this paper, we use $d$=1.7 kpc by default because this is the most commonly used value in the literature" (1 Introduction); z/distance d=1.7 kpc default; ~3 kpc alternative  
  > "The 3 mm continuum surface brightness peaks at coordinates RA=18$^{\rm h}$21$^{\rm m}$16.0570s and Dec=$-$13$^\circ$01$'$25$.\!\!^{\prime\prime}$72 (J2000)." (3.1 Continuum); "Throughout this paper, we use $d$=1.7 kpc by default because this is the most commonly used value in the literature" (1 Introduction); distance from Ser OB1 association distance (low end) and near kinematic distance from V_LSR (high end), CSC+17  
  > "The 3 mm continuum surface brightness peaks at coordinates RA=18$^{\rm h}$21$^{\rm m}$16.0570s and Dec=$-$13$^\circ$01$'$25$.\!\!^{\prime\prime}$72 (J2000)." (3.1 Continuum); "Throughout this paper, we use $d$=1.7 kpc by default because this is the most commonly used value in the literature" (1 Introduction)

## Data provenance

- ALMA projects: 2016.1.00161.S, 2017.1.00376.S
- bands: Band 3 (3 mm) and Band 6 (1 mm), twelve SPWs  
  > "A total of twelve different spectral windows (SPWs) within Band 3 (3 mm) and Band 6 (1 mm) were observed" (Observations and data reduction)
- frequencies and spectral setup: SPW centers 232.90, 231.90, 230.54, 217.50, 215.40 GHz (Band 6); 110.20, 109.54, 109.00, 107.10, 106.74, 97.00, 95.35 GHz (Band 3); bandwidths 234-1875 MHz  
  > "Central frequency, bandwidth, velocity resolution, spectral lines and continuum fluxes in the different spectral windows (SPWs)." (Table 1)
- continuum bandwidth: _not stated_
- arrays: ALMA 12-m array, 44-48 antennas  
  > "The data were obtained with 44-48 antennas, with baselines ranging from 41.4 m to 14.9 km for Band 3 and from 113.0 m to 13.9 km for Band 6." (Observations and data reduction)
- configurations: _not stated_
- baselines: 41.4 m-14.9 km (Band 3); 113.0 m-13.9 km (Band 6)  
  > "with baselines ranging from 41.4 m to 14.9 km for Band 3 and from 113.0 m to 13.9 km for Band 6." (Observations and data reduction)
- angular resolution: ~22x32 mas at 1 mm; ~50x65 mas at 3 mm  
  > "which results in angular resolutions down to $\sim$22$\times$32 mas at 1 mm and $\sim$50$\times$65 mas at 3 mm." (Observations and data reduction)
- max recoverable scale: ~0.8'' (3 mm), ~0.35'' (1 mm)  
  > "The maximum recoverable scale is $\sim$0$.\!\!^{\prime\prime}$8 and $\sim$0$.\!\!^{\prime\prime}$35 at 3 and 1 mm, respectively." (Observations and data reduction)
- sensitivity: rms ~1.1 mJy/beam (1.5 km/s channels), ~0.4 mJy/beam (4.5 km/s channels); continuum 0.10-0.15 (Band 3) and 0.04-0.09 (Band 6) mJy/beam  
  > "The rms noise level range in the continuum maps is $\sim$0.10-0.15 and 0.04-0.09 mJy beam$^{-1}$ for the individual SPWs within Band 3 and Band 6, respectively." (Observations and data reduction)
- time on source: ~49 min Band 3; ~33 min Band 6  
  > "The total time spent on the science target, MWC 922, was about 49 min in Band 3 and 33 min in Band 6." (Observations and data reduction)
- observing dates: Band 6: 2017-10-28; Band 3: 2017-09-28 to 2017-09-29  
  > "Band 3. Obs. DATE: 2017-09-28 to 2017-09-29" (Table 1)
- pi or archival as stated: _not stated_
- Line: H30alpha RRL H30α (231.9 GHz)
- Line: H39alpha RRL H39α (106.7 GHz)
- Line: H51epsilon RRL H51ε (215.7 GHz)
- Line: H55gamma RRL H55γ (109.5 GHz)
- Line: H63delta RRL H63δ (96.0 GHz)
- Line: 12CO 2-1 (230.54 GHz)
- Other facility **IRAM-30m**: Earlier single-dish mm-RRL spectra and fluxes for comparison  
  > "The comparison of the ALMA fluxes with those obtained at similar frequencies with the IRAM-30 m single-dish telescope" (3.1 Continuum)
- External data: Departure coefficients b_n used in the model  
  > "The departure coefficients $b_{\rm n}$ used are from (cite: sto95)." (Table of model parameters notes) [from (cite: sto95)]
- External data: Grid of early B-type star model atmospheres for Lyman continuum photon rates  
  > "has been compared with those obtained from the grid of model atmospheres of early B-type stars by (cite: lan07)" (5.3 The ionizing central source) [from (cite: lan07)]
- External data: Post-main-sequence evolutionary tracks of massive stars used for the HR diagram  
  > "We have used the set of different evolutionary tracks compiled and jointly evaluated by (cite: mar05)" (5.2.1 Position in the HR diagram) [from (cite: mar05)]

## Processing

### Calibration

- pipeline or manual: Initial calibration with automated ALMA pipeline; then self-calibration in GILDAS MAPPING  
  > "An initial calibration of the data was performed using the automated ALMA pipeline of the Common Astronomy Software Applications" (Observations and data reduction)
- casa version: CASA 4.7.2 and 5.1.1  
  > "(CASA[^2], versions 4.7.2 and 5.1.1)" (Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1733-1304 2.958 Jy at 108.983 GHz; J1924-2919 3.717 Jy at 231.868 GHz  
  > "The flux density adopted for J 1733-1304 is 2.958 Jy at 108.983 GHz and for J 1924-2919 is 3.717 Jy at 231.868 GHz." (Observations and data reduction)
- flux scale uncertainty: ~5%  
  > "Absolute flux calibration uncertainties are $\sim$5%." (Table 1)
- self calibration: Self-calibrated using initial source model from standard calibration, in GILDAS MAPPING  
  > "we self-calibrated our data using the initial model of the source derived from the standard calibration to improve the sensitivity and fidelity of the images." (Observations and data reduction)

### Imaging

- task: GILDAS MAPPING for restoration and deconvolution  
  > "Self-calibration as well as image restoration and deconvolution was done using the GILDAS[^3] software MAPPING." (Observations and data reduction)
- deconvolver: Hogbom  
  > "By default, we used the Hogbom deconvolution method with a robust weighting scheme," (Observations and data reduction)
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum from line-free channels of each SPW subtracted before line cubes  
  > "Line emission cubes were produced after subtracting the corresponding continuum (i.e. the continuum of the SPW containing the line)." (Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Channel width 1.5-4.5 km/s (1.5 for H30α/H39α, 4.5 for non-α lines)  
  > "We used a spectral resolution of $\Delta$v=1.5-4.5 km s$^{-1}$, depending on the S/N of the maps" (Observations and data reduction)
- final beam: Super-resolution circular beams of 15 mas (1 mm) and 30 mas (3 mm)  
  > "by imposing a circular restoring beam of 15 and 30 mas at 1 and 3 mm, respectively." (Observations and data reduction)
- final rms: 1.1 mJy/beam (1.5 km/s) and 0.4 mJy/beam (4.5 km/s) channels  
  > "$\sigma$$\sim$1.1 mJy beam$^{-1}$ ($\sigma$$\sim$0.4 mJy beam$^{-1}$)" (Observations and data reduction)

### Inherited from earlier work

- MORELI model basis (geometry, kinematics, assumptions) taken from the earlier pilot model and refined  
  > "The reader is referred to CSC+17 for full details on the parameters, major assumptions and general uncertainties of our modelling approach." (4 Analysis) [from CSC+17 (cite: san17)]
- MORELI code description  
  > "which is described in detail in (cite: bae13)" (4 Analysis) [from (cite: bae13)]
- Dust mass formulation  
  > "Using the formulation described, e.g., in (cite: san98)" (5.1 The mass in MWC 922's close environment) [from (cite: san98)]

### Not stated but needed to reproduce (our reading)

- Robust weighting value used in MAPPING
- Line-free channel ranges per SPW
- Self-calibration solution intervals and number of iterations
- Clean masks and iteration/threshold settings
- MORELI code availability and fitting procedure (no formal optimisation or parameter uncertainties given)
- Dust opacity law/normalisation used for dust mass
- Rest frequencies and cell/image sizes

## Analysis recipe

1. **Calibrate and self-calibrate**: ALMA pipeline calibration followed by self-calibration in GILDAS MAPPING  
  > "we self-calibrated our data using the initial model of the source derived from the standard calibration to improve the sensitivity and fidelity of the images." (Observations and data reduction)
   - software: CASA, GILDAS MAPPING
   - fitting: _not stated_
   - validation: Compared ALMA fluxes with IRAM-30m to check no interferometric flux loss  
  > "indicates that there are no significant interferometric flux losses in our data." (3.1 Continuum)
2. **Image continuum and line cubes**: Continuum from line-free channels per SPW; continuum-subtracted line cubes; Hogbom clean with robust weighting; super-resolution images  
  > "We created continuum images for each of the 12 SPWs using line-free channels." (Observations and data reduction)
   - software: GILDAS MAPPING
   - parameter: Δv=1.5 km/s (H30α, H39α), 4.5 km/s (non-α)  
  > "typically $\Delta$v=1.5 km s$^{-1}$ for the H30$\alpha$ and H39$\alpha$ transitions and $\Delta$v=4.5 km s$^{-1}$ for the non-$\alpha$ lines." (Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
3. **Continuum fluxes, spectral index and dust contribution**: Total fluxes per SPW; spectral index from 1-3 mm; modified blackbody dust fit to far-IR SED subtracted to get free-free slope  
  > "The dust emission in MWC 922 in the mid-to-far IR (from $\sim$12 to $\sim$300 $\mu$m) is well represented by a modified black-body at $\sim$162 K" (3.1 Continuum)
   - parameter: dust T~162 K, opacity ∝ ν^1.1  
  > "a modified black-body at $\sim$162 K with a dust opacity frequency dependence of $\sim$$\nu$$^{1.1}$" (3.1 Continuum)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive kinematics directly from maps**: Peak separation of red/blue H30α emission and PV cuts; edge-on Keplerian rotation gives central mass; wing width gives wind velocity  
  > "For an edge-on rotating disk, the velocity gradient observed implies a rotation velocity of $\sim$17 km s$^{-1}$ at a radial distance of about 25 au$\times$$\frac{d}{1.7\,kpc}$." (3.2 Radio recombination lines)
   - assumption: edge-on disk, Keplerian rotation, d=1.7 kpc  
  > "Assuming Keplerian rotation, this implies a value for the central mass of $\sim$8 $M_{\odot}$$\times$$\frac{d}{1.7\,kpc}$" (3.2 Radio recombination lines)
   - fitting: _not stated_
   - validation: _not stated_
5. **Model free-free continuum and RRLs with MORELI**: Non-LTE radiative transfer model of bicone disk+slow+fast wind; synthetic visibilities via uv_model using the same UV sampling, imaged identically; compared by eye to data and SED  
  > "we used our input model and the same UV sampling and weighting of our ALMA observations to generate the synthetic or model visibilities." (4 Analysis)
   - software: MORELI, GILDAS MAPPING
   - parameter: θa=60°, θd=6.5°, θw=38°, Rin=29 au, Te=8750 K, Vfast=95 km/s, Vslow=9 km/s, ne=4.3e7 (r/30au)^-2.7 exp(-(θa-θ)/40°) cm^-3 (d=1.7 kpc)  
  > "Electron density ($n_{\rm e}$) | 4.3$\times 10^{\rm 7}$($\frac{r}{30{\rm au}}$)$^{-2.7}$exp($-(\theta_a-\theta)/40\ensuremath{^\circ}$)" (Model results table)
   - assumption: Isothermal, Keplerian disk, rotation also in winds, constant Te, departure coefficients from Storey & Hummer  
  > "we adopt a constant value of the electron temperature ($T_{\rm e}$) within the disk and within the outflow." (4 Analysis)
   - fitting: _not stated_
   - validation: Tested alternative models (no fast-wind rotation, 1/r rotation law, d=3 kpc, parameter ranges)  
  > "We have also run a model adopting an angular-momentum conservation rotation-law ($V_{\rm rot}$$\propto$1/$r$, not shown)." (4 Analysis)
6. **Derive dust and gas masses**: Optically thin dust emission at 230.9 GHz (~35 mJy) with formulation of Sánchez Contreras et al. 1998; gas-to-dust 100  
  > "adopting a dust emission flux at 230.9 GHz of $\sim$35 mJy, we estimate that the total dust mass in MWC 922 is $M_{\rm d}$$\sim$8$\times 10^{\rm -5}$ $M_{\odot}$" (5.1 The mass in MWC 922's close environment)
   - assumption: gas-to-dust ratio ~100; T_d~160 K; emissivity ∝ ν^1  
  > "For a typical gas-to-dust mass ratio of $\sim$100, we deduce a total mass of $M_{\rm H_2}$$\sim$8$\times 10^{\rm -3}$ $M_{\odot}$" (5.1 The mass in MWC 922's close environment)
   - fitting: _not stated_
   - validation: _not stated_
7. **Constrain nature of the star**: Compare model central mass and luminosity with HR diagram evolutionary tracks and Lyman-continuum model atmospheres  
  > "we aim to test whether such a position is consistent with a stellar mass $M_{\star}$$\raisebox{-.4ex}{$\stackrel{<}{\scriptstyle \sim}$}$10 or $\raisebox{-.4ex}{$\stackrel{<}{\scriptstyle \sim}$}$18 $M_{\odot}$" (5.2.1 Position in the HR diagram)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.2 and 5.1.1: ALMA pipeline initial calibration  
  > "An initial calibration of the data was performed using the automated ALMA pipeline of the Common Astronomy Software Applications" (Observations and data reduction)
- **GILDAS MAPPING** : Self-calibration, imaging, deconvolution, uv_model synthetic visibilities  
  > "Self-calibration as well as image restoration and deconvolution was done using the GILDAS[^3] software MAPPING." (Observations and data reduction)
- **MORELI** : Non-LTE radiative transfer modelling of free-free continuum and mm-RRLs  
  > "using the non-LTE radiative transfer code MORELI (MOdel for REcombination LInes)" (4 Analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Spectral index 1-3 mm (total continuum) | 0.65 | not stated | dimensionless | 3 | The spectral index deduced from our ALMA 1 mm-to-3 mm data is $\alpha$$\sim$0.65 |
| Free-free spectral index at 3 mm after dust subtraction | 0.77 | 0.04 | dimensionless | 3 | the spectral index of the remaining free-free emission at 3 mm is smaller than, but similar to, the initial value ($\alpha$=0.77$\pm$0.04) |
| Free-free spectral index at 1 mm after dust subtraction | -0.16 | 0.3 | dimensionless | 3 | even appears to reach a negative spectral index ($\alpha$=$-$0.16$\pm$0.3) |
| H30α peak velocities | 15.3 and 50.3 | not stated | km/s (V_LSR) | 4 | two prominent peaks of emission at $V_{\rm LSR}$$\sim$15.3 and 50.3 km s$^{-1}$ |
| H30α wing full width | ~180 | not stated | km/s | 4 | The full width of the wings ($\sim$180 km s$^{-1}$) indicates a lower limit to the expansion velocity of the fast polar wind of $\sim$90 km s$^{-1}$. |
| Central mass (d=1.7 kpc / 3 kpc) | 10 / 18 | up to 25% | Msun | 5 | Central mass ($M_{\rm c}$) / 10 $M_{\odot}$  / 18 $M_{\odot}$; the uncertainty of this value is relatively high, of up to 25% |
| Fast wind velocity | 95 | not stated | km/s | 5 | Fast outflow’s velocity ($V_{\rm fast}$) / 95 km s$^{-1}$ (*radial expansion*) |
| Fast wind mass-loss rate (d=1.7/3 kpc) | 2e-6 / 4e-6 | not stated | Msun/yr | 5 | Mass-loss rate of the fast wind ($\dot{M}$$_{\rm  fast}$) / 2$\times 10^{\rm -6}$ $M_{\odot}$ yr$^{-1}$  / 4$\times 10^{\rm -6}$ |
| Inner cavity radius (d=1.7/3 kpc) | 29 / 51.5 | not stated | au | 5 | Inner radius ($R_{\rm in}$) / 29 au / 51.5 au |
| Ionized mass (d=1.7 kpc) | 2e-5 | not stated | Msun | 5 | Ionized mass ($M_{\rm ion}$) / 2$\times 10^{\rm -5}$$M_{\odot}$ |
| H30α maser optical depth at blue peak | -6 | not stated | dimensionless | 5 | with a minimum optical depth at the line (blue) peak $\tau_{30\alpha}$$\sim$$-$6 |
| Dust mass (d=1.7 kpc) | 8e-5 | factor of a few | Msun | 6 | the total dust mass in MWC 922 is $M_{\rm d}$$\sim$8$\times 10^{\rm -5}$ $M_{\odot}$ (at $d$=1.7 kpc). |
| Gas mass M_H2 (d=1.7 kpc) | 8e-3 | not stated | Msun | 6 | we deduce a total mass of $M_{\rm H_2}$$\sim$8$\times 10^{\rm -3}$ $M_{\odot}$ in the proximity of MWC 922. |
| Lyman continuum rate log N_LyC | 46.9 | not stated | s^-1 | 7 | The value found, log$N_{\rm LyC}$$\sim$46.9 s$^{-1}$ |

## Qualitative findings

- H30α wing emission shows an offset indicating rotation of the fast bipolar wind in the same sense as the disk.  
  > "The overall offset of these two features denotes a velocity gradient perpendicular to the outflow axis that is an explicit indication for rotation in the fast wind." (3.2 Radio recombination lines)
- H30α profile changed in 2 years relative to IRAM-30m, attributed to variability amplified by maser action.  
  > "These changes cannot be due to calibration errors but rather point to variations with time of the physical properties within the emitting volume." (3.2 Radio recombination lines)

## Claim tuples

- H: Does MWC 922 host a rotating disk and a fast bipolar wind? | E: Mapped H30α and H39α with ALMA and compared with MORELI models | R: Red/blue peaks displaced along the equator; wings extended perpendicular to the disk with ~180 km/s width; Vfast~95 km/s | F: A rotating disk and a fast bipolar wind with rotation are present | **supported**
- H: Is the free-free continuum optically thick across 1-3 mm? | E: Spectral index from SPW fluxes after dust subtraction | R: alpha=0.77 at 3 mm, -0.16 at 1 mm | F: Turnover to optically thin near ~2 mm, requiring a central cavity | **supported**
- H: What is the evolutionary stage of MWC 922? | E: Mass budget, HRD position and N_LyC comparison | R: Low close-environment mass, M_H2~8e-3 Msun; HRD consistent with ~15 Msun at 3 kpc | F: Post-main-sequence blue giant in mass exchange favoured over young YSO | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: mm-RRLs trace the deepest regions where fast winds are launched  
  > "showed that mm-RRLs are optimal tracers to probe the deepest regions at the heart ($\raisebox{-.4ex}{$\stackrel{<}{\scriptstyle \sim}$}$150au) of these objects" (1 Introduction)
- Alternative: Pre-main-sequence YSO and post-AGB nature judged improbable  
  > "make a pre-main sequence nature in the early stages of evolution improbable." (5.2 The nature of MWC 922)
- How they decided it was enough: _not stated_
- Limitation (authors): Distance very uncertain; central mass uncertain by up to 25%; slow wind not firmly established; model axisymmetric and cannot reproduce blue-peak asymmetry.  
  > "The distance to MWC 922 is probably the most uncertain parameter that affects the interpretation and modelling of the data." (4.2 Model caveats and uncertainties)
- Caveat (inferred, ours): Model parameters are hand-tuned without formal fitting or uncertainties.
- Caveat (inferred, ours): Results depend on uncertain b_n departure coefficients and maser sensitivity.
- Caveat (inferred, ours): Distance ambiguity propagates to masses and evolutionary conclusion.
- Caveat (inferred, ours): Fast wind is barely resolved so its geometry is poorly constrained.

## Reproducibility

- Data public (paper): Data come from ALMA projects acknowledged by code; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00161.S and ADS/JAO.ALMA#2017.1.00376.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: MORELI code and input files
- Missing: robust weighting value and clean parameters
- Missing: self-calibration details
- Missing: line-free channel definitions
- Data volume (inferred): ~100-300 GB raw for two long-baseline Band 3/6 execution sets
- Score (inferred): 3/5, Data are archival-quality and imaging is outlined, but the MORELI model is hand-tuned with key settings unstated and the code is not provided.
- Rediscovery candidate: no, Main results depend on a custom hand-tuned radiative transfer model and unstated imaging/self-cal parameters.

## Links

- Method: (cite: bae13) (Describes MORELI code)
- Companion: (cite: san17) (Pilot IRAM-30m mm-RRL study and original MWC 922 model (CSC+17))

## Checks

```json
{
 "quotes": 85,
 "quotes_ok": 85,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 84,
  "stated": 55,
  "rate": 0.655
 },
 "evidence_ok": true
}
```

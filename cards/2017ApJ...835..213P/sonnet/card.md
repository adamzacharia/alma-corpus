# The Dense Molecular Gas and Nuclear Activity in the ULIRG IRAS 13120-5453

`2017ApJ...835..213P` | The Astrophysical Journal 2017 | first author: Privon, G. C. | arXiv: 1612.04401 | DOI: 10.3847/1538-4357/835/2/213

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, astrochemistry, agn_and_quasars
- Question: What are the excitation, abundance and kinematics of dense gas tracers (HCN, HCO+, CS) in the ULIRG IRAS 13120-5453, and what do they imply for nuclear starburst/AGN activity and outflows?  
  > "The present study is focused on the properties of the high-density tracers HCN and HCO$^+$, emission, and the excitation and kinematics of those tracers in the ultraluminous infrared galaxy (ULIRG), IRAS 13120–5453." (1 Overview)
- Target **IRAS 13120-5453**: coordinates 13h15m06.316s -55d09m22.79s (J2000)  
  > "at a distance, $D_L=144$ Mpc ($z=0.03112$; angular scale: $0.656$ kpc/arcsec)" (1.3 Target); "The phase center is 13h15m06.316s –55d09m22.79s (J2000)." (2.1 Observations); z/distance D_L=144 Mpc, z=0.03112  
  > "at a distance, $D_L=144$ Mpc ($z=0.03112$; angular scale: $0.656$ kpc/arcsec)" (1.3 Target); "The phase center is 13h15m06.316s –55d09m22.79s (J2000)." (2.1 Observations); distance from systemic redshift from ALMA moment 1 at continuum center; WMAP-5 cosmology with 3-attractor correction  
  > "at a distance, $D_L=144$ Mpc ($z=0.03112$; angular scale: $0.656$ kpc/arcsec)" (1.3 Target); "The phase center is 13h15m06.316s –55d09m22.79s (J2000)." (2.1 Observations)

## Data provenance

- ALMA projects: 2012.1.00817.S
- bands: Band 7 (~340 GHz)  
  > "We present new ALMA Band 7 ($\sim340$ GHz) observations" (abstract)
- frequencies and spectral setup: four spectral windows, each 1.875 GHz wide; two centered at 331.9 and 333.7 GHz, others on redshifted lines  
  > "two centered at frequencies of 331.9 GHz (covering ) and 333.7 GHz" (2.1 Observations); "All four spectral windows had bandwidths of $1.875$ GHz." (2.1 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C32-5  
  > "ALMA observations were carried out on 18 May 2014 in the C32-5 configuration" (2.1 Observations)
- baselines: 23-625 m  
  > "These data have projected baseline lengths between $23-625$m." (2.1 Observations)
- angular resolution: 0.50" x 0.28" (~325x180 pc), PA -75 deg  
  > "the resulting resolution of the data cubes is $0\ensuremath{''}.50\times0\ensuremath{''}.28$ ($\sim325\times180$ pc) at a position angle of $-75^{\circ}$" (2.1 Observations)
- max recoverable scale: ~8" (filtering affects >~4")  
  > "the largest recoverable scale for this ALMA configuration and observing frequency" (3.1 Comparison)
- sensitivity: RMS 1.2 (units missing in text) at 20 km/s  
  > "with an RMS sensitivity of 1.2 at 20 km s$^{-1}$ spectral resolution" (2.1 Observations)
- time on source: 19.1 minutes  
  > "with an on-source time of 19.1 minutes" (2.1 Observations)
- observing dates: 18 May 2014  
  > "ALMA observations were carried out on 18 May 2014" (2.1 Observations)
- pi or archival as stated: PI: Aalto  
  > "project #2012.1.00817.S (PI: Aalto)" (2.1 Observations)
- Line: HCN 4-3 (v=0) (354.526 GHz (as listed in order in text))
- Line: HCN v2=1f (356.256 GHz)
- Other facility **Herschel PACS/SPIRE**: H2O line fluxes used to model dust temperature  
  > "IRAS 13120–5453 was observed using the Photodetector Array Camera and Spectrometer (cite: Poglitsch2010) and the Spectral and Photometric Imaging Receiver (cite: Griffin2010)" (2.2 Herschel)
- External data: APEX single-dish HCN and HCO+ fluxes  
  > "IRAS 13120–5453 was observed by (cite: Zhang2014) with the APEX 12m telescope." (3.1) [from Zhang2014]
- External data: Spitzer mid-IR core size <=2.68 kpc and 80% of emission  
  > "found IRAS 13120–5453 to have an unresolved core with a size of $\leq2.68$ kpc (FWHM) at $13.2~\mu m$" (3.2.1) [from Diaz-Santos2010]
- External data: 14 micron flux F14=0.5 Jy  
  > "show a $14~\mu m$ flux of $F_{14}=0.5$ Jy" (3.2.1) [from Inami2013]
- External data: SFR ~170 per yr from NuSTAR  
  > "a star formation rate of $\sim170$ yr$^{-1}$" (1.3 Target) [from Teng2015]

## Processing

### Calibration

- pipeline or manual: calibrated in a standard fashion with CASA  
  > "Observations were calibrated and imaged in a standard fashion using the Common Astronomy Software Applications (cite: McMullin2007)." (2.1 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ganymede, Butler-JPL-Horizons 2012 model  
  > "The flux calibration was set by observations of Ganymede, using the Butler-JPL-Horizons 2012 model" (2.1 Observations)
- flux scale uncertainty: better than 10%  
  > "The absolute flux calibration is expected to be better than 10%." (2.1 Observations)
- self calibration: one iteration of phase self-cal, 20 s solutions  
  > "An iteration of phase self-calibration was possible since the continuum of IRAS13120-5453 is strong enough to allow us to derive gain solutions on a time interval of 20s." (2.1 Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs weighting (robust not stated)  
  > "The data were imaged using Briggs weighting (cite: Briggs1995)" (2.1 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: linear baseline fit to line-free channels in image plane (imcontsub)  
  > "Continuum-free cubes were created by subtracting a linear baseline fit to the line-free channels in the image plane (CASA task `imcontsub`)." (2.1 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.50" x 0.28", PA -75 deg  
  > "$0\ensuremath{''}.50\times0\ensuremath{''}.28$ ($\sim325\times180$ pc) at a position angle of $-75^{\circ}$" (2.1 Observations)
- final rms: _not stated_

### Inherited from earlier work

- Absolute flux scale per ALMA Memo 594  
  > "as described in the ALMA Memo 594" (2.1 Observations) [from ALMA Memo 594]
- H2O radiative transfer code and dust opacity law  
  > "We have used the spherically symmetric radiative transfer code described by (cite: Gonzalez-Alfonso1997; Gonzalez-Alfonso1999)" (4 Water) [from Gonzalez-Alfonso1997; Gonzalez-Alfonso1999; Gonzalez-Alfonso2014]
- Herschel photometry for SED fit  
  > "we fit the Herschel PACS and SPIRE photometry (J. Chu et al. in preparation)" (6.1) [from J. Chu et al. in preparation]

### Not stated but needed to reproduce (our reading)

- Briggs robust value
- line-free channels used for continuum subtraction
- CASA version
- clean threshold, cell and image size
- how the 3D kinematic fit (GalPak3D) was parameterized
- Herschel photometry values for the SED fits
- velocity ranges defining outflow channels
- region definitions for 1 kpc aperture spectra

## Analysis recipe

1. **Measure line and continuum fluxes**: integrated line fluxes and 333 GHz flux from continuum-subtracted cubes  
  > "Measured Molecular Line and Continuum Properties" (Table 1)
   - software: CASA
   - fitting: _not stated_
   - validation: compared with APEX single-dish fluxes  
  > "Our HCN flux agrees with theirs, suggesting we are recovering the total flux with these ALMA data." (3.1)
2. **HCN/HCO+ ratio maps**: divide total intensity maps, masking where HCO+ not detected at >=3 sigma  
  > "The ratio map was created by dividing the total intensity map of by the total intensity map of , masking out the regions where was not detected at $\geq3\sigma$." (3.2)
   - fitting: _not stated_
   - validation: _not stated_
3. **Exploratory LVG modeling of HCN/HCO+ abundance**: grids of Radex and DESPOTIC models in density, column and relative abundance  
  > "We have performed some exploratory large velocity gradient (LVG) modeling of the , , and lines using the Radex and DESPOTIC codes" (3.2.1)
   - software: Radex, DESPOTIC
   - parameter: log n=2-7, log N_H2=21-25, abundance ratio 1e-3 to 1e3  
  > "relative HCN/HCO$^+$ abundances ($10^{-3}-10^{3}$)" (3.2.1)
   - fitting: grid comparison; under-constrained  
  > "While the solutions are under-constrained and so we cannot propose “best” values for the system, solutions which matched the observed / value of 2.8 over the nucleus required relative HCN/HCO$^+$ abundances $\gtrsim10$." (3.2.1 Limits on Vibrational HCN Emission)
   - validation: _not stated_
4. **Outflow identification and rotation modeling**: kinematic modeling of cubes with GalPak3D; PV diagrams; wings outside virial range flagged as outflow  
  > "The solid white lines denote the best-fit rotation curve obtained from modeling the data cubes with GalPak$^{\mathrm{3D}}$ (cite: Bouche2015)" (3.3)
   - software: GalPak3D
   - assumption: non-circular motion 50% of circular velocity  
  > "in-plane non-circular motion (taken as having a magnitude of $50\%$ of the circular velocity)" (3.3)
   - fitting: _not stated_
   - validation: _not stated_
5. **Model Herschel H2O lines for dust temperature**: compare observed H2O line ratios to grid of radiative transfer models  
  > "Our general approach to the modeling was to compare the observed ratios of various H$_{2}$O lines to a grid of models" (4)
   - parameter: Tgas=150 K, nH2=3e4 cm-3 fixed  
  > "We used $T_{\mathrm{gas}}=150$ K and $n_{H_{2}}=3\times10^{4}$ cm$^{-3}$" (4)
   - assumption: gas-to-dust ratio 100 by mass  
  > "We have adopted a gas-to-dust ratio of 100 by mass" (4)
   - fitting: grid comparison, best fit by eye/ratios  
  > "Our general approach to the modeling was to compare the observed ratios of various H$_{2}$O lines to a grid of models with varying $T_{\mathrm{dust}}$" (Water Emission in IRAS 13120–5453)
   - validation: _not stated_
6. **Dynamical mass**: M~V_circ^2 R/G with V_circ=FWHM/(2 sqrt(ln2)) in 1 kpc diameter  
  > "we compute the circular velocity as $V_{circ}=FWHM/(2\sqrt{\ln 2})$" (5.1)
   - assumption: intrinsically circular disk gives i~55 deg  
  > "the observed axis ratios suggest $i\approx55^{\circ}$" (5.1)
   - fitting: _not stated_
   - validation: _not stated_
7. **Continuum size, dust and ISM mass, Sigma_IR**: 2D Gaussian fit to 333 GHz continuum; dust mass with kappa; Scoville2014 relation  
  > "The distribution of the emission is well represented by a 2D Gaussian with a beam-deconvolved size (FWHM) of $0.86\ensuremath{''} \times 0.75\ensuremath{''}$" (6)
   - parameter: Tdust=40 K, kappa(333 GHz)=0.28 cm2/g  
  > "$\kappa(333~\textnormal{GHz})=0.28$ cm$^{2}$ g$^{-1}$ (cite: Bianchi2013)" (6)
   - assumption: gas-to-dust 100; 80% of L_IR in starburst following sub-mm distribution  
  > "If we assume a gas-to-dust ratio of 100 (cite: Wilson2008)" (6)
   - fitting: _not stated_
   - validation: compared with dynamical mass and Herschel/Planck extrapolation  
  > "This is comparable to the dynamical mass estimated from the HCN and HCO$^+$ kinematics (Section [5.1](#sec:dynamicalmass)) and implies $M_{ISM}/M_{dyn}\approx0.9$ within the central kpc." (Nuclear Continuum Emission)
8. **Modified blackbody SED fits to Herschel photometry**: single- and two-component modified blackbody, beta=1.8, errors by MCMC  
  > "we fit the Herschel PACS and SPIRE photometry (J. Chu et al. in preparation) with a single-component modified blackbody." (6.1)
   - software: emcee, dust_emissivity
   - parameter: beta=1.8 fixed  
  > "We fix the dust emissivity to $\beta=1.8$" (6.1)
   - fitting: MCMC with emcee; priors not stated  
  > "Errors obtained using MCMC exploration with the `emcee` package (cite: Foreman-Mackey2013)" (Footnote 5)
   - validation: compared with Planck upper limit  
  > "Our ALMA detection is consistent with the Planck $357$ GHz non-detection, which reported an upper limit of $\sim200$ mJy" (Comparison to Planck Limit and Herschel Extrapolation)

## Software

- **CASA** : calibration, imaging, imcontsub  
  > "using the Common Astronomy Software Applications (cite: McMullin2007)" (2.1 Observations)
- **GalPak3D** : rotation-curve modeling of cubes  
  > "modeling the data cubes with GalPak$^{\mathrm{3D}}$ (cite: Bouche2015)" (3.3)
- **Radex** : LVG modeling  
  > "using the Radex and DESPOTIC codes (cite: vanderTak2007; Krumholz2014)" (3.2.1)
- **DESPOTIC** : LVG modeling  
  > "using the Radex and DESPOTIC codes (cite: vanderTak2007; Krumholz2014)" (3.2.1)
- **HIPE** 14.0.1: Herschel data reduction  
  > "Herschel interactive processing environment (cite: Ott2010) version 14.0.1" (2.2)
- **emcee** : MCMC errors on blackbody fits  
  > "Errors obtained using MCMC exploration with the `emcee` package" (Footnote 5)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HCN integrated flux | 86.2 | 0.4 | Jy km/s | 1 | $86.2 \pm 0.4$ Jy km s$^{-1}$ |
| 333 GHz continuum flux | 89.8 | 0.4 | mJy | 1 | total flux of $89.8\pm0.4$ mJy |
| HCN/HCO+ ratio, integrated | 1.77 | 0.01 | dimensionless | 2 | We measure a spatial- and velocity-integrated / ratio of $1.77\pm0.01$. |
| HCN/HCO+ peak ratio over nucleus | ~2.8 | not stated | dimensionless | 2 | We find the HCN/HCO$^+$ ratio peaks at $\sim2.8$ over the nucleus |
| v2=1f 3 sigma upper limit | 0.81 | not stated | Jy km/s | 1 | with a $3\sigma$ upper limit of $0.81$ Jy km s$^{-1}$ |
| best-fit H2O model Tdust | 40 | range 40-60 K allowed | K | 5 | The best fit, which is also included in Figure [7](#fig:herschel), is achieved with $\tau_{100}=0.5$ $T_{\mathrm{dust}}=40$ K |
| Sigma_IR,50 | 4.7e12 | not stated | Lsun kpc^-2 (as in table) | 7 | We find $\Sigma_{IR,50}=4.7\times10^{12}$ kpc$^{-2}$. |
| dust mass from 333 GHz | 2.9e8 | not stated | Msun | 7 | this implies a dust mass of $2.9\times10^{8}$ |
| single-component blackbody temperature | 33 | 0.5 | K | 8 | derive a best-fit temperature, $T_{BB}=33\pm0.5$ K |
| upper limit dense outflow mass rate | <770 | not stated | Msun/yr | 0 | $\dot{M}_{dense}<770$ yr$^{-1}$ |

## Qualitative findings

- No HCN v2=1f emission detected; radiative pumping unlikely to explain enhanced HCN.  
  > "Though not conclusive, this suggests that radiative pumping is not a significant contributor to the enhanced HCN emission." (7.1)

## Claim tuples

- H: Is HCN enhanced by IR pumping? | E: Search for v2=1f line and estimate Sigma_14 | R: v2=0/v2=1f >100; Sigma_14 2-3 dex below pumped sources | F: Radiative pumping not significant | **supported**
- H: Can mechanical heating explain high HCN/HCO+? | E: Supernova rate and Kazandjian models plus LVG | R: Gamma_mech > 8e-21 erg/s/cm3 | F: Consistent with abundance enhancement from mechanical heating | **partially**
- H: Is there a dense molecular outflow that escapes? | E: Line wings vs rotation curve and virial range | R: outflow speeds 200-400 km/s vs escape ~600 km/s | F: tentative outflow, bound | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: v2=1f line as origin of HCN red wing rejected because high-velocity emission is not cospatial with nucleus  
  > "Thus, we conclude the line wing on is *not* the $v_2=1f$ line." (3.2.1)
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA may resolve out up to ~50% of 333 GHz flux  
  > "it suggests were are resolving out up to $\sim50\%$ of the 333 GHz flux with our ALMA observations." (6.1)
- Limitation (authors): LVG solutions under-constrained  
  > "While the solutions are under-constrained and so we cannot propose “best” values for the system" (3.2.1)
- Caveat (inferred, ours): Single short observation; outflow wings low-level and tentative
- Caveat (inferred, ours): H2O modeling grid fit without formal uncertainties
- Caveat (inferred, ours): ISM mass depends strongly on kappa, gas-to-dust and calibration choices

## Reproducibility

- Data public (paper): ALMA data from project 2012.1.00817.S acknowledged; archival use implied  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00817.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Briggs robust, line-free channels, CASA version
- Missing: Herschel photometry table (in prep paper)
- Missing: outflow channel definitions
- Data volume (inferred): ~10-30 GB raw
- Score (inferred): 3/5, Data public and flux/line measurements reproducible, but imaging parameters and modeling details are missing.
- Rediscovery candidate: yes, Public data, numeric line fluxes, ratios and continuum size can be redone with standard imaging.

## Links

- Method: Aalto2015a (HCN v2=1f detections and Sigma_14 thresholds)
- Method: Gonzalez-Alfonso2014 (H2O excitation modeling)
- Method: Scoville2014 (ISM mass from 850 micron luminosity)
- Companion: Zhang2014 (APEX single-dish comparison)
- Related: Herschel Hermolirg
- Related: Herschel Hercules

## Checks

```json
{
 "quotes": 83,
 "quotes_ok": 83,
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
  "facts": 93,
  "stated": 62,
  "rate": 0.667
 },
 "evidence_ok": true
}
```

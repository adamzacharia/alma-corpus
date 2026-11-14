# The Taurus Boundary of Stellar/Substellar (TBOSS) Survey. II. Disk Masses from ALMA Continuum Observations

`2018AJ....155...54W` | The Astronomical Journal 2018 | first author: Ward-Duong, K. | arXiv: 1712.07669 | DOI: 10.3847/1538-3881/aaa128

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: What are the dust masses of disks around Taurus low-mass stars and brown dwarfs (M4-M7.75), and how do they scale with host mass, age (vs Upper Sco) and compare with exoplanet inventories?  
  > "key questions remain as to whether similar disk mass relations and depletion timescales hold for lower-mass stars and substellar objects." (Introduction)
- Target **24 Taurus M4-M7.75 members (TBOSS ALMA sample)**: coordinates 2MASS positions in Table 1 (e.g. J04144730+2646264); ALMA positions in Table 3  
  > "The ALMA target sample consists of 24 Taurus low mass stars and brown dwarfs with spectral types of M4-M7.75." (Sample); "A distance to Taurus of 140pc (cite: kenyon94; bertout99; torres09) is used in the calculation." (Data Analysis); z/distance 140 pc  
  > "The ALMA target sample consists of 24 Taurus low mass stars and brown dwarfs with spectral types of M4-M7.75." (Sample); "A distance to Taurus of 140pc (cite: kenyon94; bertout99; torres09) is used in the calculation." (Data Analysis); distance from Kenyon94; Bertout99; Torres09  
  > "The ALMA target sample consists of 24 Taurus low mass stars and brown dwarfs with spectral types of M4-M7.75." (Sample); "A distance to Taurus of 140pc (cite: kenyon94; bertout99; torres09) is used in the calculation." (Data Analysis)

## Data provenance

- ALMA projects: 2012.1.00743.S
- bands: Band 7 (885 um, mean 338.8 GHz)  
  > "ALMA Band 7 observations were obtained for all targets" (Observations and Data Reduction)
- frequencies and spectral setup: Four SPWs at 331.8, 333.8, 343.8, 345.7 GHz; 2 GHz modes, highest-frequency SPW 1.875 GHz  
  > "The four spectral windows were centered on the following four frequencies: 331.8, 333.8, 343.8, and 345.7 GHz, providing a mean frequency of 338.8 GHz (885$\mu$m)." (Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 17.3-1300 m (some tracks 24.2-820.2 m)  
  > "17.3 – 1300" (Table 2)
- angular resolution: Natural 0.47x0.38 arcsec; Uniform 0.33x0.22; Briggs 0.34x0.24  
  > "Average CLEAN beam sizes for the various weighting schemes were $0.47\ensuremath{''} \times 0.38\ensuremath{''}$ (Natural)" (Data Analysis)
- max recoverable scale: _not stated_
- sensitivity: Target RMS 0.15 mJy/beam  
  > "set to reach an RMS noise level of 0.15 mJy/beam" (Observations and Data Reduction)
- time on source: 5 to 10 minutes per target  
  > "The time on-source ranged from 5 minutes to 10 minutes per target" (Observations and Data Reduction)
- observing dates: November 2013 to July 2014  
  > "a series of tracks executed between November 2013 and July 2014" (Observations and Data Reduction)
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (searched in SPW; flagged for continuum, analyzed in companion paper) (345.70599 GHz)
- Other facility **Herschel PACS**: 70 and 160 um fluxes used for target selection and SEDs  
  > "which were selected on the basis of previous *Herschel* detections at 70$\mu$m and 160$\mu$m (cite: bulger14)" (Introduction)
- External data: Herschel photometry and SED-derived stellar radius and Av  
  > "the stellar radius and value of $A_\textnormal{v}$ for each source were derived with SED fitting in the previous *Herschel* TBOSS study by (cite: bulger14)" (6.2) [from (cite: bulger14)]
- External data: 179 Taurus systems 890um flux densities (SMA + single dish)  
  > "provide a catalog of measured or extrapolated 890$\mu$m flux densities for a sample of 179 Taurus systems (cite: andrews13)" (6.3) [from (cite: andrews13)]
- External data: Upper Sco and Rho Oph submm fluxes for comparison  
  > "values drawn from a single dish IRAM survey of high-mass Upper Sco members (cite: mathews12) and a large recent ALMA study (cite: barenfeld16)" (6.4) [from (cite: mathews12; barenfeld16; gvdp16; testi16)]
- External data: Kepler heavy-element masses  
  > "The average heavy element mass required to form the population of *Kepler*-detected 2-50 day period planets was inferred by (cite: mulders15)." (6.5) [from (cite: mulders15)]
- Simulation/model as data: Evolutionary models BHAC15, MESA, Baraffe98 for stellar mass/luminosity  
  > "a comparison of the evolutionary models of (cite: baraffe98) and (cite: baraffe15), and the MESA models for higher mass targets (cite: choi16)" (6.3)

## Processing

### Calibration

- pipeline or manual: ALMA QA calibration and flagging tables re-applied to raw data, minimal extra flagging  
  > "calibration and flagging tables derived from the ALMA Quality Assurance process (cite: petry14) were re-applied to the raw data in CASA 4.2.2" (Data Analysis)
- casa version: CASA 4.2.2  
  > "re-applied to the raw data in CASA 4.2.2 (cite: mcmullin07)" (Data Analysis)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10% absolute flux uncertainty added  
  > "an additional 10% uncertainty was added to the uncertainties in Table [\[tab:fluxes\]] to account for the absolute flux scaling uncertainty" (Data Analysis)
- self calibration: 2-3 rounds phase-only self-cal for 8 sources with SNR>40  
  > "For the 8 highest signal-to-noise ratio detections (SNR $>$ 40), we also performed self-calibration, consisting of 2 or 3 rounds of phase-only self-calibration." (Data Analysis)

### Imaging

- task: CASA clean; imfit for image-plane 2D Gaussian; uvmodelfit in uv-plane  
  > "The *imfit* task in CASA was used to fit the continuum emission in the image plane with 2D Gaussians for each of the 22 detections." (Data Analysis)
- deconvolver: _not stated_
- weighting robust: Natural, Briggs and uniform compared; self-cal sources Briggs robust=0.5; others natural  
  > "For the self-calibrated sources, imaging was performed with Briggs weighting with *“robust”*=0.5." (Data Analysis)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: CO channels flagged, remaining channels averaged  
  > "flagging all channels associated with CO emission as visually identified from plotting the amplitudes per channel" (Data Analysis)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Dust temperature-luminosity relation T=A L^B for low-luminosity objects  
  > "a different temperature-luminosity relation more appropriate for samples extending to spectral types of $\sim$M5 and later was used, as explored in our previous paper (cite: gvdp16)" (6.1) [from (cite: gvdp16)]
- Genetic algorithm approach for MCFOST fitting  
  > "We apply a genetic algorithm approach, previously employed in (cite: mathews13)" (6.2) [from (cite: mathews13)]
- Opacity normalization and T-L scaling as in earlier surveys  
  > "similar to previous studies (cite: andrews13; carpenter14)" (6.1) [from (cite: andrews13; carpenter14)]

### Not stated but needed to reproduce (our reading)

- Briggs robust used for non-self-cal imaging checks, cell size, image size, clean threshold/masks
- Which channels were flagged for CO per source
- Self-cal solution intervals
- Genetic algorithm population size, number of generations, mutation fraction
- Fixed MCFOST parameters (inclination, A_v handling, grid)
- uvmodelfit starting parameters
- Kelly regression priors/settings and handling of upper limits

## Analysis recipe

1. **Calibrate and image continuum**: Re-apply QA calibration, concatenate EBs, flag CO channels, average, clean (natural/Briggs/uniform)  
  > "aligning the spectral windows between individual observations and concatenating the measurement sets" (Data Analysis)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared fluxes across weightings  
  > "The extracted fluxes agree within 7% on average for all methods." (Data Analysis)
2. **Measure flux densities**: Re-centre by phase shift; imfit 2D Gaussians; uvmodelfit; self-cal for SNR>40 sources  
  > "The phase-shifted measurement sets were also used to fit the continuum emission in the *uv*-plane using the CASA task *uvmodelfit*" (Data Analysis)
   - software: CASA
   - fitting: Gaussian fit; 10% flux scale uncertainty added  
  > "The *imfit* task in CASA was used to fit the continuum emission in the image plane with 2D Gaussians for each of the 22 detections." (Data Analysis)
   - validation: Image vs uv-plane comparison  
  > "A comparison between the image plane fitting and *uv*-fitting for the extracted fluxes is shown in Figure [3](#fig:fluxcomparison). The extracted fluxes agree within 7% on average for all methods." (Data Analysis)
3. **Analytic dust masses**: M_dust from S_nu, d, kappa, B_nu(T_dust) with T=A L^B  
  > "\log M_{dust} = \log S_{\nu}+2 \log d-\log \kappa_{\nu}-\log B_{\nu}(\langle T_{dust} \rangle)" (6.1)
   - parameter: disk outer radii 10-200 au; central 100 au, 40 or 20 au for low-mass  
  > "we explore a range of radii from 10 au to 200 au" (6.1)
   - assumption: kappa_1.3mm=2.3 cm2/g, kappa~nu^0.4, d=140 pc  
  > "The opacity was scaled to the observation wavelength of 885$\mu$m from the assumptions of $\kappa_{1.3mm}$=2.3cm$^{2}$g$^{-1}$ and $\kappa \sim \nu^{0.4}$" (6.1)
   - fitting: _not stated_
   - validation: Compared with MCFOST masses  
  > "the dust masses are compared with the analytically-derived masses in Figure [9](#fig:dustmass_modelanalytic)" (Calculations of Disk Masses from Radiative Transfer Models (MCFOST))
4. **SED radiative transfer fits**: MCFOST models with genetic algorithm minimizing chi2, 5 free parameters  
  > "to explore five free model parameters – M$_\textnormal{dust}$, $H_{0}$, $r_\textnormal{in}$, $\beta$, and surface density index" (6.2)
   - software: MCFOST
   - parameter: r_out=100 au, a_min=0.01 um, a_max=3 mm, N(a)~a^-3.5, kappa=2.78 cm2/g at 870 um  
  > "with a corresponding continuum opacity $\kappa = 2.78\textnormal{cm}^{2}/\textnormal{g}$ at 870$\mu$m" (6.2)
   - assumption: Single continuous disk, no envelope  
  > "a single continuous disk model was used, with no envelope component" (6.2)
   - fitting: Genetic algorithm, minimum chi2  
  > "We apply a genetic algorithm approach, previously employed in (cite: mathews13), to explore five free model parameters" (Calculations of Disk Masses from Radiative Transfer Models (MCFOST))
   - validation: Compared with analytic masses (Fig 9)  
  > "the dust masses are compared with the analytically-derived masses in Figure [9](#fig:dustmass_modelanalytic)" (Calculations of Disk Masses from Radiative Transfer Models (MCFOST))
5. **Host masses and Mdust-Mstar regression**: SpT to Teff (HH14), mass from BHAC15 at 1 Myr / MESA; Bayesian linear regression with limits  
  > "applying the Bayesian linear regression approach of (cite: kelly07) to incorporate both detections and upper limits" (6.3)
   - assumption: Taurus age 1 Myr; gas:dust 100:1  
  > "For this study, an age of 1 Myr and the (cite: baraffe15) model grid were used in the mass determination" (Central Object Spectral Type, Temperatures, and Masses)
   - fitting: Kelly07 linear regression  
  > "applying the Bayesian linear regression approach of (cite: kelly07) to incorporate both detections and upper limits." (Disk Mass as a Function of Central Object Mass)
   - validation: Varied disk size, split by SpT, recomputed Barenfeld slope  
  > "the Taurus and Upper Sco samples were broken into separate subsets at the M4 spectral type." (Disk Mass as a Function of Time and Environment)

## Software

- **CASA** 4.2.2: calibration application, imaging, imfit, uvmodelfit, self-cal  
  > "re-applied to the raw data in CASA 4.2.2 (cite: mcmullin07)" (Data Analysis)
- **MCFOST** : radiative transfer SED modeling  
  > "Monte Carlo 3D continuum radiative transfer code MCFOST (cite: pinte06; pinte09)" (6.2)
- **APLpy** : plotting  
  > "This research made use of APLpy, an open-source plotting package for Python" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Detections | 22 of 24 detected; flux densities 1.0-55.7 mJy | not stated | mJy | 2 | The flux densities of the detections range from 1.0 to 55.7 mJy. |
| Non-detection 3sigma limits | 0.27 (J04190110), 0.29 (J04213459) | not stated | mJy/beam | 2 | The non-detections have 3$\sigma$ upper limits of 0.27 mJy/beam for J04190110 and 0.29 mJy/beam for J04213459 |
| Dust masses range | 0.3-20 | not stated | Earth masses | 3 | dust mass estimates ranging from $\sim$0.3–20M$_{\oplus}$ |
| Taurus Mdust-Mstar slope | 0.97 | 0.14 | dimensionless | 5 | $\textnormal{log}[M_\textnormal{dust} (M_{\oplus})] = (0.97\pm0.14) \textnormal{log}[M_\textnormal{star}(M_{\odot})] + (1.15\pm0.09)$ |
| Upper Sco slope | 0.92 | 0.18 | dimensionless | 5 | (0.92\pm0.18) \textnormal{log}[M_\textnormal{star}(M_{\odot})] + (0.46\pm0.09) |
| Taurus to Upper Sco dust mass decline | ~4-5 | not stated | factor | 5 | suggests a decline in disk mass by a factor of $\sim$4-5 |
| Fraction of M-star Taurus disks > MMSN | 17% (32 of 193) | not stated | percent | 5 | 32 (17%) have disk masses larger than the MMSN |

## Qualitative findings

- Brown dwarf disks form a continuous sequence with low-mass stars  
  > "The substellar disks appear as part of a continuous sequence and not a distinct population." (abstract)

## Claim tuples

- H: Do substellar disks differ from stellar ones? | E: ALMA Band 7 survey plus regression with SMA Taurus sample | R: Slope 0.97±0.14 consistent with linear | F: BD disks continue the stellar trend | **supported**
- H: Do disk masses decline with age? | E: Compare Taurus and Upper Sco with uniform dust masses | R: Intercepts imply factor ~4-5 decline | F: Taurus disks more massive than Upper Sco | **supported**
- H: Are disks massive enough for giant planets? | E: Compare to MMSN with 100:1 gas:dust | R: 17% of M-star disks exceed MMSN; none of BDs | F: Low giant-planet formation efficiency | **partially**

## Reasoning

- Why this data: Band 7 best compromise between declining flux and ALMA sensitivity  
  > "Band 7 represented the best compromise between declining disk flux with wavelength and increasing ALMA sensitivity with wavelength." (Observations and Data Reduction)
- Why this method: _not stated_
- Alternative: Eqn T=25 L^0.25 rejected for giving unphysically low temperatures (~12 K)  
  > "To avoid the unphysically low temperatures implied by Eqn." (6.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Slope depends strongly on stellar evolutionary model and dust temperature relation  
  > "derived power-law slopes depend strongly upon choices of stellar evolutionary model and dust temperature relation" (abstract)
- Caveat (inferred, ours): Optically thin single-opacity assumption; disk radii unresolved
- Caveat (inferred, ours): Herschel-detected selection may bias sample
- Caveat (inferred, ours): Class III BDs assumed to have no MMSN disks

## Reproducibility

- Data public (paper): Reduction scripts and auxiliary data on OSF  
  > "Example reduction scripts and auxiliary data are available at https://osf.io/9dyx4." (footnote)
- Products in archive: _not stated_
- Code: Example reduction/analysis scripts at osf.io/9dyx4  
  > "Example analysis scripts and auxiliary data for the methods described in Appendices A and B are available at https://osf.io/9dyx4." (footnote)
- Missing: Imaging parameters (cell, size, thresholds)
- Missing: Genetic algorithm settings
- Missing: Regression configuration
- Data volume (inferred): Tens of GB (Cycle 1, 7 EBs)
- Score (inferred): 4/5, Data and tools clear with tabulated fluxes and masses; some imaging and fitting settings missing.
- Rediscovery candidate: yes, Archive data, tabulated numeric results (fluxes, dust masses); analytic recipe is simple.

## Links

- Method: (cite: gvdp16) (T-L relation for low-luminosity objects)
- Method: (cite: mathews13) (genetic algorithm with MCFOST)
- Companion: (cite: bulger14) (TBOSS Herschel survey (Paper I))
- Companion: van der Plas et al. 2017, in prep (12CO(3-2) spectral line analysis)
- Related: TBOSS
- Related: Taurus SMA survey (Andrews 2013)

## Checks

```json
{
 "quotes": 70,
 "quotes_ok": 70,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 54,
  "rate": 0.684
 },
 "evidence_ok": true
}
```

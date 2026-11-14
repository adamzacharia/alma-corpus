# Gas structure inside dust cavities of transition disks: Ophiuchus IRS 48 observed by ALMA

`2014A&A...562A..26B` | Astronomy and Astrophysics 2014 | first author: Bruderer, Simon | arXiv: 1312.2756 | DOI: 10.1051/0004-6361/201322857

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: How does the gas surface density behave inside the dust cavity (60 AU) and the inner 20 AU of the transition disk Oph IRS 48, and what is the total gas mass?  
  > "The observed gas lines are used to set constraints on the gas surface density profile." (abstract)
- Target **Oph IRS 48**: coordinates RA 16h27m37.18s, Dec -24d30m35.3s (J2000)  
  > "is an A0 star located in the $\rho$ Ophiuchi star formation region at a distance of 120 parsec" (1 Introduction); "$\alpha_{\rm 2000}=$16$^{\rm h}$27$^{\rm m}$37.18s, $\delta_{\rm 2000}=$-24$^\circ$ 30$'$ 35.3$''$" (1 Introduction); z/distance 120 pc  
  > "is an A0 star located in the $\rho$ Ophiuchi star formation region at a distance of 120 parsec" (1 Introduction); "$\alpha_{\rm 2000}=$16$^{\rm h}$27$^{\rm m}$37.18s, $\delta_{\rm 2000}=$-24$^\circ$ 30$'$ 35.3$''$" (1 Introduction); distance from Loinard08; Brown12  
  > "is an A0 star located in the $\rho$ Ophiuchi star formation region at a distance of 120 parsec" (1 Introduction); "$\alpha_{\rm 2000}=$16$^{\rm h}$27$^{\rm m}$37.18s, $\delta_{\rm 2000}=$-24$^\circ$ 30$'$ 35.3$''$" (1 Introduction)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 9 (690 GHz), Cycle 0  
  > "Band 9 ALMA Cycle 0 observations of IRS 48 were carried out in the extended configuration" (2 Observations and data reduction)
- frequencies and spectral setup: 4 spectral windows centered at 674.00, 678.84, 691.47, 693.88 GHz; 3840 channels each, 488 kHz spacing, 1875 MHz bandwidth; velocity resolution 0.21 km/s  
  > "The spectral setup consisted of four spectral windows, centered at 674.00 , 678.84, 691.47 and 693.88 GHz" (2 Observations and data reduction); "The final velocity resolution is 0.21 km s$^{-1}$ using a reference of 690 GHz" (2 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: extended configuration  
  > "carried out in the extended configuration" (2 Observations and data reduction)
- baselines: up to 390 m, 18 to 21 antennas  
  > "In these blocks, 18 to 21 antennas were used with baselines up to 390 meter." (2 Observations and data reduction)
- angular resolution: 0.32'' x 0.21'' (38 x 25 AU), PA 96 deg  
  > "The synthetic beam has a size of $0.32'' \times 0.21''$ ($38 \times 25$ AU) and a position angle of 96$^\circ$ (east-of-north)." (2 Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: rms 40 mJy/beam/channel  
  > "the rms noise level is 40 mJy beam$^{-1}$ channel$^{-1}$" (2 Observations and data reduction)
- time on source: three execution blocks of 1.7 hours each  
  > "in three execution blocks of 1.7 hours each" (2 Observations and data reduction)
- observing dates: June 6th and July 17th 2012  
  > "on June 6th and July 17th 2012" (2 Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: 12CO J=6-5 (around 690 GHz)
- Line: C17O J=6-5 (spectral window centered at 674.00 GHz)
- Other facility **VLT-VISIR**: 18.7 um dust continuum image used to constrain dust structure  
  > "the VLT-VISIR 18.7 $\mu$m dust continuum images" (abstract)
- External data: SED photometry and spectroscopy (2MASS, WISE, IRAC, IRAS, PACS, SMA, SCUBA, etc.)  
  > "| WISE       | 3.4        | 1.29       | (cite: Wright10)    |" (Table 2) [from Table 2 references (Cutri03, Wright10, vanKempen09, Fedele13a, Andrews07, Geers07, McClure10, ...)]
- External data: Inclination 48+-8 deg and PA 98+-3 deg from 18.7 um images  
  > "The inclination is determined by (cite: Geers07) from 18.7 $\mu$m dust continuum images to be $i=48\pm8^\circ$." (3.1 Integrated intensity maps) [from (cite: Geers07)]
- External data: Stellar type A0, mass 2 Msun, luminosity 14.3 Lsun; AV=11.5  
  > "| Stellar mass | M$_* =$ 2 M$_\odot$ | B12 |" (Table 1) [from (cite: Brown12)]
- External data: Accretion rate 4e-9 Msun/yr  
  > "| Accretion rate | $4 \times 10^{-9}$ M$_\odot$ yr$^{-1}$ | S13 |" (Table 1) [from (cite: Salyk13)]
- Simulation/model as data: DALI physical-chemical models of the disk with varying gas surface density profiles, compared with ALMA CO cuts and spectra  
  > "we use the combined physical-chemical model DALI (Dust And LInes) by (cite: Bruderer13), based on (cite: Bruderer12)." (4 Analysis)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 3.4  
  > "Reduction and calibration of the data was performed using the Common Astronomy Software Application (CASA) version 3.4" (2 Observations and data reduction)
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
- continuum subtraction: integrated intensity maps are continuum subtracted (method not given)  
  > "Figure [1](#fig:int_imgdeproj)a shows the continuum subtracted integrated intensity of the $^{12}$CO $J=6-5$ observation." (3.1 Integrated intensity maps)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Data reduction and calibration  
  > "is further described in the Supplementary Online Material of (cite: vdMarel13)." (2 Observations and data reduction) [from (cite: vdMarel13)]
- Disk structure from Andrews et al. 2011, with dust opacities and f, chi values  
  > "we adopt the physical structure suggested by (cite: Andrews11), as implemented by (cite: Bruderer13)." (4.1 Disk structure) [from (cite: Andrews11)]
- Dust structure of IRS 48 derived from SED and VISIR image  
  > "The dust structure of IRS 48 is derived from the SED and 18.7 $\mu$m VLT-VISIR dust continuum image by (cite: Geers07)." (4.1 Disk structure) [from (cite: Geers07)]

### Not stated but needed to reproduce (our reading)

- Imaging parameters (weighting, robust, cell size, image size, deconvolver, masks) for the CO cubes
- Continuum-subtraction line-free channels
- Flux calibrator and flux scale uncertainty
- Velocity range for integrated intensity and region definition of the cut along major axis
- DALI code and input configuration (grid, chemistry, UV field) not released here; fit criterion between models and data is by-eye
- Dust opacity details beyond Andrews11

## Analysis recipe

1. **Map CO emission and extract spectra**: Integrated intensity maps, channel maps binned to 1 km/s, total spectrum from >5 sigma regions, cut along disk major axis  
  > "The total spectrum extracted from regions with $>$5$\sigma$ detections in $^{12}$CO is shown in Figure [3](#fig:tot_spec)" (3.3 Total spectrum and C17O)
   - software: CASA
   - assumption: Keplerian rotation around 2 Msun star, inclination 50 deg, PA 100.3 deg  
  > "The contour lines are derived assuming a geometrically thin disk in Keplerian rotation around a 2 M$_{\odot}$ star" (3.1 Integrated intensity maps)
   - fitting: _not stated_
   - validation: _not stated_
2. **Model dust structure from SED and VISIR image**: Power-law surface density with Gaussian vertical structure, explore parameters to fit SED and 18.7 um image  
  > "The surface density profile is assumed to be a power-law and the vertical structure follows a Gaussian distribution (vertically isothermal structure)." (4.1 Disk structure)
   - software: DALI
   - parameter: h_60AU = 0.14 rad, psi = 0.22, f = 0.85, chi = 0.2, R_inner,dust = 1 AU  
  > "| Vertical structure | $h_{\rm 60\, AU}$ | 0.14 radians |" (Table 3)
   - assumption: kappa(450 um)=7.1 cm2/g; PAH abundance ~10% of ISM; AV=11.5, RV=5.5 extinction  
  > "the resulting total dust mass is $1.6 \times 10^{-5}$ M$_\odot$ ($\kappa_{450\, \mu{\rm m}}=7.1$ cm$^2$ g$^{-1}$)" (4.1 Disk structure)
   - fitting: by-eye comparison, no formal fit  
  > "Figure [10](#fig:surfcomp) shows the $^{12}$CO $J=6-5$ integrated intensity cuts along the major axis of the disk for various trial gas distributions." (Comparison to observations)
   - validation: Compared model SED and VISIR images  
  > "Figure [7](#fig:visir_irs48) compares the VLT-VISIR 18.7 $\mu$m observations to model images." (4.1 Disk structure)
3. **Constrain gas surface density and drops by comparing physical-chemical models to CO data**: Vary Sigma_60AU, delta_60AU, delta_20AU; compare 12CO integrated intensity cut along major axis, total spectrum, and C17O total flux  
  > "The major parameters that are varied are $\Sigma_{\rm 60\, AU, gas}$, $\delta_{\rm 60 \, AU}$ and $\delta_{\rm 20 \, AU}$." (4.3 Comparison to observations)
   - software: DALI, CASA
   - parameter: gamma = 1; also tested gamma = 0 and 2; inner radii 15, 20, 25 AU tested  
  > "we have also run models with $\gamma=0$ and $\gamma=2$" (4.4 The slope gamma)
   - assumption: 2D axisymmetric model; foreground absorption and asymmetries ignored, focus on velocities >=4 km/s from source velocity  
  > "we will restrict our analysis to 2d axisymmetric models." (4 Analysis)
   - fitting: visual comparison of trial models, no formal sampler  
  > "Figure [10](#fig:surfcomp) shows the $^{12}$CO $J=6-5$ integrated intensity cuts along the major axis of the disk for various trial gas distributions." (Comparison to observations)
   - validation: Model convolved to ALMA beam checked against simulated ALMA observations in CASA  
  > "The ALMA observations have been simulated using the CASA software by converting the model image to ${\rm (u,v)}$-data according to the observed ${\rm (u,v)}$-coverage" (4.3 Comparison to observations)
4. **Predict CO isotopologue lines for future ALMA**: Model integrated intensity cuts for 12CO, 13CO, C18O, C17O J=3-2 and 6-5 at beams 0.25, 0.1, 0.05''; detection limits from ALMA sensitivity calculator  
  > "The limits have been calculated with the ALMA sensitivity calculator[^3], using a channel width of 0.2 km s$^{-1}$, and an intrinsic line width of 1 km s$^{-1}$." (4.7 Prediction for the CO isotopologue lines)
   - software: DALI, ALMA sensitivity calculator
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 3.4: Data reduction and calibration; simulated ALMA observations of models  
  > "Reduction and calibration of the data was performed using the Common Astronomy Software Application (CASA) version 3.4" (2 Observations and data reduction)
- **DALI** : Physical-chemical disk modeling of dust, gas temperature, CO abundance and line emission  
  > "we use the combined physical-chemical model DALI (Dust And LInes) by (cite: Bruderer13)" (4 Analysis)
- **ALMA sensitivity calculator** : Detection limits for predicted isotopologue lines  
  > "The limits have been calculated with the ALMA sensitivity calculator[^3]" (4.7 Prediction for the CO isotopologue lines)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total gas mass | 1.4e-4 | factor of a few | Msun | 3 | The gas mass[^2] of the representative model is $1.4 \times 10^{-4}$ M$_\odot$. |
| Dust mass | 1.6e-5 | factor of a few | Msun | 2 | the resulting total dust mass is $1.6 \times 10^{-5}$ M$_\odot$ |
| Gas-to-dust mass ratio | ~10 | considerable | dimensionless | 3 | this gives a gas-to-dust mass ratio of about 10. |
| Gas surface density at 60 AU | 3.2e-2 | not stated | g cm-2 | 3 | / Surface density profile$^{1}$ / $\gamma$ / 1.0 /; $\Sigma_{\rm 60 AU,gas}=3.2 \times 10^{-2}$ g cm$^{-2}$ |
| Gas drop inside 60 AU (delta_60AU) | 8e-2 (factor ~12) | not stated | dimensionless | 3 | / Gas, 20-60 AU / $\delta_{\rm 60\, AU} = 8 \times 10^{-2}$ / |
| Gas drop inside 20 AU (delta_20AU) | < 9e-3 (factor >110) | lower limit | dimensionless | 3 | A model with a drop $\delta_{\rm 20\, AU} < 9 \times 10^{-3}$ (factor of $>$110) reproduces the observed dip at the center position. |
| Inner gas radius | 20 | better than 5 | AU | 3 | We conclude that the drop of the surface density at 20 AU is constrained to better than $\sim$5 AU. |
| Observed C17O total flux | 1.3 | not stated | Jy km/s | 1 | compares the modeled C$^{17}$O total flux of the three models discussed before with the observed 1.3 Jy km s$^{-1}$ |
| Upper limit CO mass of inner disk (10 AU) | 5e23 | upper limit | g | 3 | The upper limits on the CO mass of an inner disk are $5 \times 10^{23}$ g for a 10 AU disk with $\delta_{\rm 20\, AU} = 8 \times 10^{-3}$ |

## Qualitative findings

- 12CO emission is partly absorbed by foreground cloud at vlsr ~2.0-4.5 km/s, causing asymmetries  
  > "We conclude that some, but not all, of the asymmetries seen in the integrated intensity maps can be attributed to foreground absorption." (3.1 Integrated intensity maps)
- Photoevaporation alone is unlikely to form the cavities  
  > "We thus conclude that in IRS 48 photoevaporation is unlikely the reason for the gap formation at 20 and 60 AU." (5.1 The gas mass and surface density profile)

## Claim tuples

- H: Does the gas surface density drop inside the 60 AU dust cavity? | E: Compared DALI models with different delta_60AU to the 12CO cut and spectrum | R: Drop of a factor ~12 required for gamma=1 | F: Gas is partly depleted but not removed inside the dust cavity | **supported**
- H: Is gas depleted inside 20 AU? | E: Varied delta_20AU and inner radius | R: Drop of factor >=110; inner radius 20+-5 AU | F: Gas hole at 20 AU, only a limit on depth | **partially**
- H: What is the total gas mass and gas-to-dust ratio? | E: Fit 12CO and C17O flux with models | R: 1.4e-4 Msun, ratio ~10 | F: Low gas mass, ratio only marginally below ISM given a factor-of-few uncertainties | **supported**
- H: What clears the cavity? | E: Compared derived profile with photoevaporation and planet predictions | R: Drops moderate, accretion rate too high for photoevaporation | F: Points to one or more massive planets or companions | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Optically thick CO needs a model with chemistry and thermal balance to determine CO abundance in the UV-exposed cavity  
  > "Such a model is also needed to determine the abundance of CO inside and outside the dust cavity since it is not a priori obvious that CO can survive in the dust-free gas exposed to intense UV radiation from the star." (4 Analysis)
- Alternative: Photoevaporation (X-ray and EUV) rejected as sole mechanism  
  > "This accretion rate is also higher than typical EUV photoevaporation rates ((cite: Alexander06a; Alexander06)) ruling out EUV driven evaporation." (5.1 The gas mass and surface density profile)
- How they decided it was enough: _not stated_
- Limitation (authors): 12CO is optically thick so surface density is not directly constrained; profiles accurate only to a factor of a few  
  > "We do not expect that derived surface density profiles are more accurate than a factor of a few." (4.3 Comparison to observations)
- Limitation (authors): Beam comparable to 20 AU hole, so only limits inside 20 AU  
  > "the current data can only set limits on the gas mass inside 20 AU." (4.3.3 The inner 20 AU)
- Caveat (inferred, ours): Model matching is by eye with no formal chi-square or uncertainty estimation
- Caveat (inferred, ours): Axisymmetric model ignores strong azimuthal asymmetry and foreground absorption
- Caveat (inferred, ours): Gas mass depends on assumed CO abundance, isotope ratios and gamma; a previous paper's gas mass was in error
- Caveat (inferred, ours): Vertical structure and dust opacities adopted rather than fit

## Reproducibility

- Data public (paper): ALMA project acknowledged; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA no. 2011.0.00635.SSB." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters and line-free channels
- Missing: DALI model setup files and chemistry network details
- Missing: Calibration details deferred to vdMarel13 supplement
- Data volume (inferred): Cycle 0 Band 9, 3 execution blocks, ~tens of GB raw
- Score (inferred): 3/5, Data are Cycle 0 archive data and measurements are clear, but the modeling code setup and imaging details are not given and model fitting is by eye.
- Rediscovery candidate: no, Main results depend on a specialized DALI model with by-eye comparison and calibration details deferred to another paper.

## Links

- Method: (cite: Bruderer13) (DALI model and transition-disk framework)
- Method: (cite: Bruderer12) (Physical-chemical model basis)
- Method: (cite: Andrews11) (Disk structure and dust opacities)
- Companion: (cite: vdMarel13) (Original presentation of the ALMA continuum, dust trap and data reduction)
- Companion: (cite: vdMarel13b) (Other lines (CN, H13CO+, H2CO) from the same data)

## Checks

```json
{
 "quotes": 67,
 "quotes_ok": 67,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 1,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00635.S"
 ],
 "codes_printed_but_missing": [
  "2011.0.00635.SSB"
 ],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 46,
  "rate": 0.597
 },
 "evidence_ok": true
}
```

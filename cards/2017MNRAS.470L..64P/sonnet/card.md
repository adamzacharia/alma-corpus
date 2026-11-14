# CO excitation in the Seyfert galaxy NGC 7130

`2017MNRAS.470L..64P` | Monthly Notices of the Royal Astronomical Society 2017 | first author: Pozzi, F. | arXiv: 1705.08221 | DOI: 10.1093/mnrasl/slx077

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, agn_and_quasars, astrochemistry
- Question: What is the impact of AGN activity (X-ray heating) on the molecular gas in NGC7130, as probed by modelling its CO SLED with PDR and XDR models?  
  > "The goal of this letter is to definitively assess the impact of the AGN activity on the molecular gas in NGC7130." (1 INTRODUCTION)
- Target **NGC7130**: coordinates _not stated_; z/distance z=0.0161  
  > "NGC7130 is a local ( _z_ =0.0161) Luminous Infrared Galaxy" (1 INTRODUCTION); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00524.S
- bands: Band 9  
  > "with the Band 9 receiver searching for the CO(6-5) transition at 691.473 GHz" (2.2 CO data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C34-5  
  > "The configuration user (C34-5) allowed a synthesized beam" (2.2 CO data)
- baselines: _not stated_
- angular resolution: ~0.20 x 0.14 arcsec (~70 x 49 pc)  
  > "synthesized beam FWHM of _∼_ 0 _._ 20 _×_ 0 _._ 14 _[′′]_ corresponding to physical scales of _∼_ 70 _×_ 49 pc" (2.2 CO data)
- max recoverable scale: ~3 arcsec (~1 kpc)  
  > "the largest angular scales recovered by the ALMA configuration is only _∼_ 3 _[′′]_, corresponding to _∼_ 1 kpc" (2.2 CO data)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival; PI Nanyao Lu, Cycle 2; results from Zhao et al. (2016)  
  > "The yellow triangle represent the new ALMA CO(6-5) data from Zhao et al. (2016)." (2.2 CO data)
- Line: CO J=6-5 (691.473 GHz)
- Other facility **Chandra**: ACIS-S3 X-ray spectrum, 38.6 ks  
  > "NGC7130 was observed by _Chandra_ in Cycle 2 with the ACIS-S3 CCD at the aimpoint (on Oct. 23 _[rd]_, 2001), for an exposure time of 38.6 ks." (2.1 Chandra and NuSTAR data)
- Other facility **NuSTAR**: Hard X-ray spectrum, 21.2 ks  
  > "_NuSTAR_ observed NGC7130 on Aug. 17 _[th]_, 2014, for an exposure time of 21.2 ks." (2.1 Chandra and NuSTAR data)
- Other facility **Herschel SPIRE/FTS**: mid/high-J CO fluxes (Jup>4)  
  > "The mid/high-J levels ( _J_ _up_ _>_ 4) are from Herschel SPIRE/FTS observations" (2.2 CO data)
- Other facility **SEST**: low-J CO transitions  
  > "while the low-J transitions are from Albrecht et al. (2007) using the Swedish ESO Submillimeter Telescope (SEST)" (2.2 CO data)
- External data: ALMA CO(6-5) line flux, beam and extent  
  > "For details on the analysis of the ALMA data we refer to Zhao et al. (2016)" (2.2 CO data) [from Zhao et al. (2016)]
- External data: Herschel SPIRE/FTS mid/high-J CO fluxes  
  > "(Pereira-Santaella et al. 2013)" (2.2 CO data) [from Pereira-Santaella et al. 2013]
- External data: SEST low-J CO fluxes  
  > "the low-J transitions are from Albrecht et al. (2007)" (2.2 CO data) [from Albrecht et al. (2007)]
- External data: SFR ~21 Msun/yr used to normalise the stellar SED  
  > "normalized to reproduce the NGC7130 of SFR _∼_ 21 M _⊙_ yr _[−]_ [1] (Gruppioni et al. 2016)" (3 ISM MODELLING) [from Gruppioni et al. 2016]

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

- Analysis of the ALMA CO(6-5) data  
  > "For details on the analysis of the ALMA data we refer to Zhao et al. (2016)" (2.2 CO data) [from Zhao et al. (2016)]
- XDR modelling approach for the AGN radiation on a gas slab  
  > "follows the same approach proposed by Abel & Satyapal (2008) for modeling the AGN radiation impinging a gas slab" (3 ISM MODELLING) [from Abel & Satyapal (2008)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, imaging and flux extraction (in Zhao et al. 2016)
- Initial guesses, grid sampling and bounds of the 9-parameter chi2 fit
- Herschel and SEST flux values and uncertainties (only plotted)
- Exact CLOUDY input files

## Analysis recipe

1. **Fit X-ray spectrum for AGN luminosity**: Joint Chandra+NuSTAR fit with mekal thermal components and MYTorus  
  > "To achieve these goals, we used the MYTorus model (Murphy & Yaqoob 2009)" (2.1 Chandra and NuSTAR data)
   - software: xspec
   - parameter: photon index fixed to 1.9; NH and inclination free  
  > "While the photon index was fixed to 1.9, as typically observed in AGN and quasars" (2.1 Chandra and NuSTAR data)
   - fitting: chi2 statistics, chi2/dof = 99.1/85  
  > "This overall modelling provides a _χ_ [2] /dof (degrees of freedom) of 99.1/85" (2.1 Chandra and NuSTAR data)
   - validation: Compared with Koss et al. (2016) and Ricci et al. (2017)  
  > "Our results are in good agreement with the analysis of the hard-X ray data" (2.1 Chandra and NuSTAR data)
2. **Compute PDR and XDR CO emissivity grids**: 1-D constant-density slab CLOUDY runs; PDR with Starburst99 SED, XDR with table AGN  
  > "we run two sets of CLOUDY models that assume the molecular clouds to be a 1-D gas slab with constant density located at a fixed distance _d_ from the source" (3 ISM MODELLING)
   - software: CLOUDY, Starburst99
   - parameter: PDR: log n=2-4.5, d=75-250 pc; XDR: log n=3.5-5.5; max log NH=23  
  > "_log_ ( _n/_ cm _[−]_ [3] ) = [2 _−_ 4 _._ 5] and _d_ = [75 _−_ 250] pc" (3 ISM MODELLING)
   - assumption: Salpeter IMF 1-100 Msun, solar metallicity, aox=-1.4, Tcut=1e6 K  
  > "The ratio of the UV and X-ray continua ( _a_ _ox_ ) is fixed to _−_ 1 _._ 4" (3 ISM MODELLING)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit CO SLED with three components**: chi2 minimisation with 9 free parameters (density, radiation field, normalisation per component)  
  > "We find the best fit by a _χ_ [2] minimitation routine with 9 free parameters" (3 ISM MODELLING)
   - parameter: NH ~1e22 cm-2 for PDRs, ~1e23 for XDR  
  > "We fix the column density _N_ _H_ _∼_ 10 [22] cm _[−]_ [2] for the PDRs and _N_ _H_ _∼_ 10 [23] cm _[−]_ [2] for XDR." (3 ISM MODELLING)
   - fitting: 1 sigma from Delta chi2=3.5 marginalising over other parameters  
  > "considering a ∆ _χ_ [2] =3.5 (see Lampton et al. 1976)" (3 ISM MODELLING)
   - validation: _not stated_
4. **Derive cold gas mass and alpha_CO**: alpha_CO = Mcold/LCO using observed CO(1-0) luminosity  
  > "the estimated gas mass allow us to estimate directly the CO-to-H 2 conversion factor" (3 ISM MODELLING)
   - fitting: _not stated_
   - validation: Compared with MW and ULIRG values  
  > "The value found is consistent with the overall properties of NGC7130 being a LIRG galaxy hosting a moderate, obscured AGN." (3 ISM MODELLING)

## Software

- **CLOUDY** c13.03: PDR/XDR CO emissivity models  
  > "We model the CO SLED using the version c13.03 of the photoionization/photodissociation code CLOUDY" (3 ISM MODELLING)
- **Starburst99** : stellar SED for PDR models  
  > "The SED is obtained with the stellar population synthesis code Starburst99" (3 ISM MODELLING)
- **xspec** : X-ray spectral fitting  
  > "to apply _χ_ [2] statistics within the xspec package (Arnaud 1996)" (2.1 Chandra and NuSTAR data)
- **nupipeline/nuproducts** : NuSTAR reprocessing and spectral extraction  
  > "Data were reprocessed and screened using standard settings and the nupipeline task" (2.1 Chandra and NuSTAR data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA CO(6-5) total line flux | 1230 | 74 | Jy km/s | 0 | The total line flux is 1230 _±_ 74 Jy km s _[−]_ [1] |
| Intrinsic L2-10keV | 1.6e43 | not stated | erg/s | 1 | The intrinsic 2–10 keV and 1–100 keV luminosities of the AGN are 1 _._ 6 _×_ 10 [43] erg s _[−]_ [1] and 5 _._ 1 _×_ 10 [43] erg s _[−]_ [1], respectively. |
| Equatorial NH | 5.3e24 | 1.6e24 | cm^-2 | 1 | We obtain an equatorial column density of (5 _._ 3 _±_ 1 _._ 6) _×_ 10 [24] cm _[−]_ [2] and _θ_ _obs_ = 79 _±_ 5 degrees. |
| Cold gas mass | ~1e9 | not stated | Msun | 3 | The total cold gas mass necessary to fit the CO observation is _M_ _cold_ _∼_ 10 [9] _M_ _⊙_ |
| alpha_CO | 1.1 | not stated | Msun pc^-2 (K km/s)^-1 | 4 | that implies a CO-to-H2 conversion factor _α_ _CO_ =1.1 M _⊙_ pc _[−]_ [2] K km s _[−]_ [1] |

## Qualitative findings

- PDR models reproduce CO up to J~6 but not higher J; an XDR component is needed.  
  > "We find that PDRs can reproduce the CO lines up to J _∼_ 6, however, the higher rotational ladder requires the presence of a separate source of excitation." (abstract)

## Claim tuples

- H: PDRs alone can reproduce the CO SLED | E: CLOUDY PDR grids compared with CO(5-4)/(4-3) and CO(10-9)/(5-4) ratios | R: PDR reproduces the CO(5-4)/(4-3) ratio but not CO(10-9)/(5-4) | F: An additional high-J excitation source is needed | **supported**
- H: AGN X-ray heating explains the high-J CO | E: Three-component PDR+PDR+XDR chi2 fit | R: XDR at 250 pc, log n=3.5, T~100 K fits the SLED | F: XDR heating by the Compton-thick AGN is favoured over shocks | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Shocks are judged unlikely given the observed LCO/LFIR ratio.  
  > "A chemistry driven by shocks (scenario (b), supported by Pereira-Santaella et al. 2014) is unlikely given the observed _L_ _CO_ _/L_ _IR_ ratio." (3 ISM MODELLING)
- Alternative: Shock heating rejected based on LCO/LFIR ~1.5e-4 typical of XDR/PDR  
  > "NGC7130 has an observed _L_ _CO_ _/L_ _F IR_ ratio _∼_ 1 _._ 5 _×_ 10 _[−]_ [4], a factor typical of XDR/PDR models" (3 ISM MODELLING)
- How they decided it was enough: _not stated_
- Caveat (inferred, ours): Nine-parameter fit to ~11 integrated CO points is degenerate; no goodness-of-fit stated
- Caveat (inferred, ours): ALMA used as a single flux and size constraint, and single-dish fluxes cover a larger area
- Caveat (inferred, ours): Shocks excluded by one ratio argument only

## Reproducibility

- Data public (paper): ALMA data are archival from project 2013.1.00524.S  
  > "This paper makes use of the ALMA data ADS/JAO.ALMA#2013.1.00524.S." (5 ACKNOWLEDGEMENTS)
- Products in archive: _not stated_
- Missing: Fit grid and optimisation details
- Missing: Tabulated CO line fluxes
- Missing: ALMA processing (deferred to Zhao et al. 2016)
- Data volume (inferred): ~tens of GB for the ALMA Band 9 data; the X-ray and Herschel data are small
- Score (inferred): 3/5, The ALMA role is minor and only a published flux is used; the modelling is described but incompletely parameterised.
- Rediscovery candidate: no, The ALMA analysis is deferred to another paper and the main results come from CLOUDY modelling of literature fluxes.

## Links

- Method: Zhao et al. (2016) (ALMA CO(6-5) data analysis)
- Method: Abel & Satyapal (2008) (XDR modelling approach)
- Companion: Lu et al. 2017, arXiv1703.00005 (ALMA flux consistent with Herschel)

## Checks

```json
{
 "quotes": 47,
 "quotes_ok": 47,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 37,
  "rate": 0.493
 },
 "evidence_ok": true
}
```

# VALES V: a kinematic analysis of the molecular gas content in H-ATLAS galaxies at z ∼ 0.03-0.35 using ALMA

`2019MNRAS.482.1499M` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Molina, J. | arXiv: 1809.10752 | DOI: 10.1093/mnras/sty2577

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, high_z_galaxies
- Question: How does global galactic dynamics (Vrot/sigma_v) relate to ISM properties, [CII]/IR deficit, dynamical mass, gas stability and star formation timescales in VALES galaxies?  
  > "to characterise the role of global galactic dynamics on the global interstellar medium (ISM) properties" (abstract)
- Target **VALES sub-sample of 39 H-ATLAS galaxies (20 resolved)**: coordinates Table 2 lists RA/Dec per galaxy (e.g. HATLASJ083601.5+002617: 08:36:01.6 +00:26:18.1)  
  > "Out of the 49 galaxies that were spectroscopically detected in CO(1-0) by V17, we find that only 39 of them are spectroscopically detected at a 5 $\sigma$ significance" (2.1 VALES Survey); z/distance z=0.025-0.32 (spectroscopic, Table 2)  
  > "Out of the 49 galaxies that were spectroscopically detected in CO(1-0) by V17, we find that only 39 of them are spectroscopically detected at a 5 $\sigma$ significance" (2.1 VALES Survey); distance from z_spec from V17 (Villanueva2017)  
  > "Out of the 49 galaxies that were spectroscopically detected in CO(1-0) by V17, we find that only 39 of them are spectroscopically detected at a 5 $\sigma$ significance" (2.1 VALES Survey)

## Data provenance

- ALMA projects: 2012.1.01080.S, 2013.1.00530.S, 2015.1.01012.S
- bands: Band 3  
  > "ALMA observations targeting the CO(1-0) emission line in band 3 for 67 galaxies during Cycle-1 and Cycle-2" (2.1 VALES Survey)
- frequencies and spectral setup: cubes at fixed 20 km/s spectral resolution  
  > "we kept the spectral resolution fixed at 20 km s$^{-1}$ despite of the degrade of S/N" (2.1 VALES Survey)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: synthesized beam major axis 3"-4" (2-17 kpc)  
  > "of $3"- 4"$ that corresponds to a physical scale between 2 and 17 kpc" (Introduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=1-0 (115.271 GHz)
- Other facility **Herschel/H-ATLAS, IRAS, WISE**: FIR photometry for L_FIR and SFR (via V17)  
  > "derived from SEDs constructed with photometry from the Infrared Astronomical Satellite (IRAS; (cite: Neugebauer1984)), Wide-field Infrared Survey Explorer" (2.1 VALES Survey)
- Other facility **GAMA**: 21-band photometry for stellar masses and K-band Sersic models  
  > "provided by the GAMA Panchromatic Data Release (cite: Driver2016)" (2.1 VALES Survey)
- External data: ALMA data reduction, L_FIR, SFR, M*, morphology classification (V17)  
  > "The observations, data reduction and analysis are presented in detail for the complete sample in V17" (2.1 VALES Survey) [from Villanueva2017]
- External data: [CII] luminosities  
  > "whilst the \[C ii\] luminosity data is presented in (cite: Ibar2015)" (2.1 VALES Survey) [from Ibar2015]
- External data: PDR model parameters n_H and G0  
  > "For the VALES survey, (cite: Hughes2017a) applied the PDR model of (cite: Kaufman1999; Kaufman2006)" (4.3 PDR modelling) [from Hughes2017a]
- External data: EDGE-CALIFA CO maps for comparison  
  > "we complement our analysis by adding the EDGE-CALIFA survey data (cite: Bolatto2017) to our VALES data" (EDGE-CALIFA SURVEY) [from Bolatto2017]

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
- smoothing: no spectral filtering for imaging; channels 20 km/s  
  > "Considering that we have not applied any spectral filtering for imaging purposes" (2.2 Galaxy Dynamics)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Pixel-by-pixel line fitting and 2D arctan kinematic model with genetic algorithm  
  > "following the approach presented in (cite: Swinbank2012a)" (2.2 Galaxy Dynamics) [from Swinbank2012a]
- ALMA reduction, SFR, L_FIR, stellar masses, CO-to-H2 classification  
  > "The observations, data reduction and analysis are presented in detail for the complete sample in V17" (2.1 VALES Survey) [from Villanueva2017]
- Beam-smearing correction of velocity dispersion  
  > "subtract it linearly from the corresponding velocity dispersion value following Eq. A1 from (cite: Stott2016)" (3.5) [from Stott2016]

### Not stated but needed to reproduce (our reading)

- CASA version and imaging parameters (weighting, cell, cleaning) used to make 20 km/s cubes
- Continuum subtraction and line-free channels
- Flux calibration details and uncertainties
- Genetic algorithm settings
- Which cubes/execution blocks correspond to each galaxy
- Exact SIGMA K-band catalogue values for inclination priors

## Analysis recipe

1. **Sample selection**: Re-detect V17 CO(1-0) sources at fixed 20 km/s; classify resolved vs compact; normal vs starburst via Genzel2015 sSFR  
  > "the observed CO(1-0) emission extends for more than $\sqrt{2}$ times the major axis of the synthesized beam" (2.1 VALES Survey)
   - parameter: 5 sigma detection; starburst if sSFR > 4 sSFR(z,M*)  
  > "all the galaxies with sSFR \> 4 sSFR$(z,M_*)$ are labelled as ‘starburst’" (2.1 VALES Survey)
   - assumption: alpha_CO = 0.8 (merger) or 4.6 (disk); LambdaCDM H0=70  
  > "bimodal CO-to-H$_2$ conversion factor of 0.8 or 4.6 $M_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$" (2.1 VALES Survey)
   - fitting: _not stated_
   - validation: _not stated_
2. **Velocity field extraction**: chi2 Gaussian line fits per pixel in beam-sized region, S/N>5, width > sqrt2 channel width  
  > "we impose a S/N \> 5 threshold to the best-fit to detect the emission line" (2.2 Galaxy Dynamics)
   - fitting: chi2 minimisation  
  > "We use a $\chi^2$ minimisation procedure" (2.2 Galaxy Dynamics)
   - validation: _not stated_
3. **Kinematic modelling**: 2D disk model with arctan rotation curve, 4 free parameters; inclination from GAMA K-band b/a with q0=0.14, 10% error, 3 sigma range  
  > "This model has four free parameters \[$V_{\rm asym}$, r$_{\rm t}$, position angle (PA) and disk inclination\] and a genetic algorithm" (3.3 Kinematic model)
   - parameter: centre fixed to CO intensity peak; confidence limit Delta chi2_nu = 1  
  > "we constrain the kinematic centre to the CO(1-0) intensity peak location" (3.3 Kinematic model)
   - assumption: oblate spheroid with q0=0.14  
  > "we adopt ${\rm q_0=0.14}$" (3.2 Inclination angles)
   - fitting: genetic algorithm  
  > "a genetic algorithm (cite: Charbonneau1995) is used to find the best fit" (3.3 Kinematic model)
   - validation: mean residual <data-model> = 17±9 km/s  
  > "$\langle$data $-$ model$\rangle$ = 17$\pm$9 km s$^{-1}$" (3.3 Kinematic model)
4. **Derive r1/2,CO, Vrot, sigma_v**: half-light radius within Petrosian radius, deconvolved by beam in quadrature; Vrot at 2 r1/2; sigma_v median beyond 2 beams after gradient correction  
  > "median value of the pixels at an angular distance 2 times greater than the angular extension of the synthesized beam" (3.6)
   - parameter: R_P,lim=0.2  
  > "We adopted the SDSS Petrosian radius definition with R$_{\rm P,lim}=0.2$" (3.4 CO(1-0) spatial extent)
   - fitting: Bootstrapping Monte-Carlo for r1/2 errors  
  > "errors are derived by bootstrapping via Monte-Carlo simulations" (3.4 CO(1-0) spatial extent)
   - validation: Compared with Wisnioski2015 sigma method; degraded high-res mock cubes  
  > "We found a median $\sigma_{v,{\rm W}}$ value of 36 km s$^{-1}$" (4.1)
5. **Dynamical mass, stability, SF law**: thin vs thick (Burkert2010) disk Mdyn; Q_gas/Q_thick/Q_2; SFR vs L'CO/t_orb and t_cross power-law fits and Spearman correlations  
  > "Following (cite: Burkert2010), we model our galaxies as turbulent galactic gas disks in which pressure support cannot be neglected" (4.4)
   - assumption: K-band Sersic traces mass with constant M/L  
  > "constant $K-$band mass-to-light ratio across the galactic disk" (4.4)
   - fitting: power-law fits; method not stated  
  > "The data are fitted by a power-law function with best-fit slope of 1.21$\pm$0.14." (4.7 Kennicutt-Schmidt Law Efficiency & Depletion Times)
   - validation: exponential-profile test in appendix, median ratio ~1.5  
  > "the median ratio of $\sim1.5$ indicates that our conclusions should not be sensitive to the chosen surface density profiles" (Appendix)

## Software

- **SIGMA** : GAMA Sersic photometric models (K-band)  
  > "Those models are produced by using SIGMA (Structural Investigation of Galaxies via Model Analysis; (cite: Kelvin2012))" (3.1)
- **MAGPHYS** : SED fitting for stellar masses (in V17)  
  > "modelled with the bayesian SED fitting code MAGPHYS" (2.1 VALES Survey)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median Vrot/sigma_v (all resolved) | 4.1 | not stated | dimensionless | 4 | The median $V_{\rm rot}/\sigma_v$ ratio for our sample is 4.1 |
| Median Vrot/sigma_v normal / starburst | 4.3 / 1.6 | not stated | dimensionless | 4 | the median $V_{\rm rot}/\sigma_v$ values for the ‘normal’ star-forming and starburst sub-samples are 4.3 and 1.6 |
| L_CII/L_IR vs Vrot/sigma_v Spearman rho | 0.76 | not stated | dimensionless | 5 | This correlation has $\rho_{\rm Spearman}=0.76$ |
| L_CII/L_IR power-law slope | 0.74 | 0.14 | dimensionless | 5 | best-fit slope of 0.74$\pm$0.14 |
| SFR-L'CO/t_orb slope | 1.21 | 0.14 | dimensionless | 5 | best-fit slope of 1.21$\pm$0.14 |
| SFR-L'CO/t_cross slope | 1.38 | 0.13 | dimensionless | 5 | The best-fit power law function is 1.38$\pm$0.13 |
| Median r1/2,CO | 4.4 | 3 | kpc | 4 | The median $r_{1/2,\rm CO}$ for our sample is $4.4 \pm 3$ kpc |

## Qualitative findings

- Thin-disk Mdyn underestimates mass for five low Vrot/sigma galaxies; thick disk resolves this  
  > "the thin disk model tends to underestimate the galactic total mass as its values are lower than the estimated stellar masses for five of our galaxies" (Conclusions)

## Claim tuples

- H: The [CII] deficit relates to galaxy dynamics | E: Compare L_CII/L_IR with Vrot/sigma_v | R: rho=0.76, slope 0.74±0.14; low Vrot/sigma galaxies below KINGFISH | F: [CII]/IR depends on dynamical state | **supported**
- H: Star formation timescale set by crossing time | E: (L'CO/SFR)/t vs SFR | R: no correlation with t_cross (rho=-0.003); correlation with t_orb | F: t_cross may control SF | **partially**
- H: Turbulence is driven by gravity or feedback | E: Compare SFR, f_H2, sigma_v with models | R: both models poor descriptions | F: other energy sources needed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Fixed 20 km/s resolution to avoid spectral resolution effects on kinematics  
  > "in order to minimize spectral resolution effects in our dynamical analysis" (2.1 VALES Survey)
- How they decided it was enough: _not stated_
- Limitation (authors): Low spatial resolution biases sigma_v and r1/2 high and Vrot low  
  > "which may imply an overestimation of the observed $\sigma_v$ and $r_{1/2,\rm CO}$ values and an underestimation of the $V_{\rm rot}$ value" (3.7)
- Caveat (inferred, ours): Beam smearing at 3-4" dominates sigma_v
- Caveat (inferred, ours): Only 20 resolved galaxies; weak correlations with high chance probability
- Caveat (inferred, ours): alpha_CO bimodal assumption affects f_H2 and Q

## Reproducibility

- Data public (paper): ALMA project codes cited; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.01080.S" (Acknowledgements)
- Products in archive: _not stated_
- Missing: Cube imaging parameters
- Missing: Genetic algorithm code and settings
- Missing: V17 tables for SFR and M*
- Data volume (inferred): tens of GB
- Score (inferred): 3/5, Analysis described but imaging and fitting details inherited from V17/Swinbank2012a; code not released.
- Rediscovery candidate: no, Key imaging and fitting settings not given.

## Links

- Method: Swinbank2012a (kinematic fitting approach)
- Method: Burkert2010 (thick disk dynamical mass model)
- Companion: Villanueva2017 (VALES data and reduction)
- Companion: Ibar2015 ([CII] data)
- Companion: Hughes2017a (PDR modelling)
- Related: VALES
- Related: H-ATLAS
- Related: GAMA
- Related: EDGE-CALIFA
- Related: KINGFISH
- Related: DYNAMO

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 41,
  "rate": 0.532
 },
 "evidence_ok": true
}
```

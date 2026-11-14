# The Galaxy Activity, Torus, and Outflow Survey (GATOS). IV. Exploring Ionized Gas Outflows in Central Kiloparsec Regions of GATOS Seyferts

`2024ApJ...974..195Z` | The Astrophysical Journal 2024 | first author: Zhang, Lulu | arXiv: 2409.09771 | DOI: 10.3847/1538-4357/ad6a4b

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: How do ionized gas distributions, kinematics and outflows in the central kpc of six GATOS Seyferts appear in JWST MIRI/MRS data, and how do their outflow rates compare at comparable AGN luminosity?  
  > "Our final goal is to shed light on the relative outflow strength in AGN with comparable luminosity." (Introduction)
- Target **NGC 5728**: coordinates 14:42:23.880 -17:15:11.08  
  > "NGC 5728   | 14:42:23.880 | $-$17:15:11.08" (Table 2); "NGC 5728 | SAB(r)a | 0.00932 | 39" (Table 1); z/distance z=0.00932, D_L=39 Mpc  
  > "NGC 5728   | 14:42:23.880 | $-$17:15:11.08" (Table 2); "NGC 5728 | SAB(r)a | 0.00932 | 39" (Table 1); distance from NED  
  > "NGC 5728   | 14:42:23.880 | $-$17:15:11.08" (Table 2); "NGC 5728 | SAB(r)a | 0.00932 | 39" (Table 1)
- Target **NGC 5506**: coordinates 14:13:14.878 -03:12:27.76  
  > "NGC 5506 | Sa pec | 0.00608 | 27" (Table 1); z/distance z=0.00608, D_L=27 Mpc  
  > "NGC 5506 | Sa pec | 0.00608 | 27" (Table 1); distance from NED  
  > "NGC 5506 | Sa pec | 0.00608 | 27" (Table 1)
- Target **ESO137-G034**: coordinates 16:35:13.995 -58:04:47.91  
  > "ESO137-G034 | SAB0/a | 0.00914 | 35" (Table 1); z/distance z=0.00914, D_L=35 Mpc  
  > "ESO137-G034 | SAB0/a | 0.00914 | 35" (Table 1); distance from NED  
  > "ESO137-G034 | SAB0/a | 0.00914 | 35" (Table 1)
- Target **NGC 7172**: coordinates 22:02:1.889 -31:52:10.47  
  > "NGC 7172 | Sa pec | 0.00868 | 37" (Table 1); z/distance z=0.00868, D_L=37 Mpc  
  > "NGC 7172 | Sa pec | 0.00868 | 37" (Table 1); distance from NED  
  > "NGC 7172 | Sa pec | 0.00868 | 37" (Table 1)
- Target **MCG-05-23-016**: coordinates 09:47:40.135 -30:56:56.00  
  > "MCG-05-23-016 | S0 | 0.00849 | 35" (Table 1); z/distance z=0.00849, D_L=35 Mpc  
  > "MCG-05-23-016 | S0 | 0.00849 | 35" (Table 1); distance from NED  
  > "MCG-05-23-016 | S0 | 0.00849 | 35" (Table 1)
- Target **NGC 3081**: coordinates 09:59:29.534 -22:49:34.78  
  > "NGC 3081 | (R)SAB0/a(r) | 0.00798 | 34" (Table 1); z/distance z=0.00798, D_L=34 Mpc  
  > "NGC 3081 | (R)SAB0/a(r) | 0.00798 | 34" (Table 1); distance from NED  
  > "NGC 3081 | (R)SAB0/a(r) | 0.00798 | 34" (Table 1)

## Data provenance

- ALMA projects: 2015.1.00086.S, 2015.1.00116.S, 2017.1.00236.S, 2019.1.01742.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO 2-1 (cold molecular gas contours, per ALMA; transition not stated for all targets) (not stated)
- Other facility **JWST MIRI/MRS**: Main data: IFU spectra of six Seyferts, GO program #1670  
  > "obtained by the JWST cycle 1 GO program #1670 (PI: Shimizu, T. Taro)" (2.1 Targets and Observations)
- Other facility **VLA**: Archival radio images used as contours  
  > "This paper also makes use of the following VLA images:" (Acknowledgments)
- External data: Bolometric luminosities, [O III] outflow rates and kinetic energies, Eddington ratios  
  > "Reference for Column (7)-(10): ((cite: Davies.etal.2015; Davies.etal.2020; Caglar.etal.2020))." (Table 1) [from (cite: Davies.etal.2015; Davies.etal.2020; Caglar.etal.2020)]

## Processing

### Calibration

- pipeline or manual: JWST MIRI/MRS pipeline (JWST data, not ALMA) with extra residual_fringe step  
  > "We primarily follow the standard JWST MIRI/MRS pipeline (release 1.11.4) to reduce the raw data" (2.1 Targets and Observations)
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

- JWST data reduction and extra steps  
  > "The data reduction and extra steps are described in (cite: Garcia-Bernete.etal.2024a)." (2.1 Targets and Observations) [from (cite: Garcia-Bernete.etal.2024a)]
- Spatially resolved analysis strategy  
  > "We adopt the same strategy to study ionized gas kinematics in central kpc-scale regions of the six Seyfert galaxies" (2.2 Data Analysis) [from (cite: Zhang.etal.2021); (cite: Zhang&Ho2023)]

### Not stated but needed to reproduce (our reading)

- ALMA CO data processing, transitions, resolution and how CO contours were made
- Which ALMA project maps to which target
- Exact aperture-flux weighting and per-target n_e/U inputs

## Analysis recipe

1. **Fit emission lines**: Single then double Gaussian plus local linear continuum, Levenberg-Marquardt; F-test p<0.05; 100 noise perturbations  
  > "we fit each ionic emission line using a single- and then a double-Gaussian profile, plus a local linear continuum." (2.3 Emission Line Fitting)
   - fitting: Levenberg-Marquardt least-squares  
  > "The fitting is implemented with the Levenberg-Marquardt least-squares minimization algorithm." (2.3 Emission Line Fitting)
   - validation: _not stated_
2. **Compute outflow rates from [Ne V]**: Upper limit Mdot=M_ion W80/R; lower limit from broad component with v_out=v2+1.18 sigma2; r=0.9'' aperture  
  > "we take $\dot{M}_{\rm ion} = M_{\rm ion} W_{80} / R$" (5 Quantification)
   - software: PyNeb
   - assumption: Te = 10^4 K; n(He)/n(H)=0.1; n_e from L_bol and U  
  > "we assume a standard value of $T_{e} = 10^{4}\,\rm K$" (Derivation of Ionized Gas Mass)
   - fitting: _not stated_
   - validation: Compared with Davies et al. 2020 [O III] rates and Fiore et al. 2017 correlation  
  > "the outflow rates calculated based on the total \[Ne V\] flux are consistent with those calculated by (cite: Davies.etal.2020)" (5 Quantification)

## Software

- **JWST pipeline** 1.11.4: MIRI/MRS reduction  
  > "standard JWST MIRI/MRS pipeline (release 1.11.4)" (2.1 Targets and Observations)
- **Source Extractor (SEP)** : Measure AGN ionization axis from [Ne V] maps  
  > "major axis of a elliptical source detected from \[Ne V\] $f_{\rm total}$ maps using `Source Extractor`" (3.2.1 Flux Distributions)
- **PyNeb** : Line emissivities  
  > "The line emissivity $j_{\rm line}(n_{e}, T_{e})$ is obtained by `PyNeb`" (Derivation of Ionized Gas Mass)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Convolved angular resolution | 0.7 | not stated | arcsec | 0 | After convolving all slices to the same angular resolution, of $0.7\ensuremath{''}$ |
| Median log U range | -2.9 to -2.6 | std 0.1-0.3 dex | dimensionless | 2 | median values of $\sim -2.9$ to $-2.6$, with the standard deviations of $\sim 0.1$ to $0.3$ dex |

## Qualitative findings

- Highly ionized [Ne V] velocity fields twist relative to low-ionization lines, indicating AGN-driven outflows along ionization cones  
  > "$v_{\rm m}$ distributions of high ionization lines (e.g., \[Ne V\]) are increasingly dominated by outflow motions along the AGN ionization cone." (3.2.2 Velocity Fields)

## Claim tuples

- H: Do the six Seyferts show ionized outflows? | E: Non-parametric velocity and W80 maps of six lines | R: Twisting of velocity fields or shock evidence in all six | F: Outflows are present in all six | **supported**
- H: Are outflow rates diverse at similar luminosity? | E: [Ne V]-based outflow rates | R: Rates converge to narrower range than [O III]-based | F: Measurement accuracy may contribute to the diversity | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Phenomenological jet model; conclusive explanation needs modeling  
  > "this model is only for a phenomenological explanation" (4.1 Highly Disturbed Regions in NGC 5728)
- Caveat (inferred, ours): ALMA role is only CO contours; not reproducible from ALMA alone
- Caveat (inferred, ours): Outflow rate depends on assumed n_e from L_bol and U

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA CO processing details
- Missing: JWST fitting code
- Data volume (inferred): not stated; ALMA part small
- Score (inferred): 2/5, ALMA minor; JWST central; ALMA details absent.
- Rediscovery candidate: no, ALMA role minor and undocumented.

## Links

- Method: (cite: Zhang.etal.2021) (Spatially resolved analysis strategy)
- Companion: (cite: Davies.etal.2024) (NGC 5728 study)
- Companion: (cite: Hermosa-Munoz.etal.2024a) (NGC 7172 study)
- Related: GATOS
- Related: JWST GO 1670

## Checks

```json
{
 "quotes": 49,
 "quotes_ok": 49,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 2,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 35,
  "rate": 0.467
 },
 "evidence_ok": true
}
```

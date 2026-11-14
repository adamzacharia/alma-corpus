# Does the HCN/CO ratio trace the star-forming fraction of gas?: II. Variations in CO and HCN emissivity

`2024A&A...692A.146B` | Astronomy and Astrophysics 2024 | first author: Bemis, Ashley R. | arXiv: 2410.00243 | DOI: 10.1051/0004-6361/202347879

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: nearby_galaxies, star_formation
- Question: How do variations in optical depth and excitation affect HCN and CO emissivities across a grid of cloud models, and does the HCN/CO ratio trace the dense or gravitationally bound gas fraction  
  > "We assess the impact of variations in optical depth and excitation on the emissivities of HCN and CO across this grid" (Introduction)
- Target **Archival ten-galaxy sample (five disk-galaxy centers, five U/LIRGs; defined in Paper I)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **NGC 3256**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **NGC 4038/9 (Antennae)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00467.S, 2011.0.00525.S, 2011.0.00772.S, 2012.1.00165.S, 2012.1.00185.S, 2012.1.01004.S, 2013.1.00218.S, 2013.1.00247.S, 2013.1.00634.S, 2013.1.00885.S, 2013.1.00911.S, 2013.1.01057.S, 2015.1.00993.S, 2015.1.01177.S, 2015.1.01286.S, 2015.1.01538.S
- bands: _not stated_
- frequencies and spectral setup: HCN and CO J=1-0 lines plus radio continuum at 93 GHz (imaged in earlier work)  
  > "the radio continuum at 93 GHz" (Introduction); "observed in the sample of ten galaxies from using archival ALMA data of the HCN and CO" (Introduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: archival ALMA data  
  > "observed in the sample of ten galaxies from using archival ALMA data of the HCN and CO" (Introduction)
- Line: HCN J=1-0 (not stated)
- Line: CO J=1-0 (not stated)
- Other facility **PHANGS (CO J=2-1 cloud-scale measurements)**: cloud-scale surface density and velocity dispersion measurements used to define the model parameter space  
  > "We randomly sampled measurements from each of these cloud-scale studies" (2.3 The model parameter space)
- Other facility **EMPIRE survey**: HCN and CO intensities of disk galaxies used for comparison with modeled intensities  
  > "compared to the intensities measured in our sample from and the EMPIRE sample from" (3.1 Excitation and optical depth)
- External data: Cloud-scale (R = 40-45 pc) pairs of molecular gas surface density and velocity dispersion from PHANGS, NGC 3256 and the Antennae, randomly sampled to build the model grid  
  > "We randomly sampled measurements from each of these cloud-scale studies" (2.3 The model parameter space) [from Sun et al. 2020 (cite: Sun:2020); Brunetti et al. 2021 (cite: Brunetti:2021); Brunetti et al. 2024 (cite: Brunetti:2024)]
- External data: Analytical fits to PHANGS rotation curves used to estimate shear  
  > "We use the analytical fits to the rotation curves of the PHANGS galaxies from" (Velocity dispersion estimates from molecular lines as a measure of mach number) [from Lang et al. 2020 (cite: Lang:2020)]
- External data: Relationship between HCN/CO and gas surface density from extinction in Milky Way clouds, used for comparison  
  > "gas surface density as determined through extinction measurements in Milky Way clouds" (3.1 Excitation and optical depth) [from Tafalla et al. 2023 (cite: Tafalla:2023)]
- External data: ALMOND survey HCN/CO versus velocity dispersion and surface density relations, used for comparison  
  > "found in nearby galaxies from the ALMOND survey" (3.1 Excitation and optical depth) [from Neumann et al. 2023 (cite: Neumann:2023)]
- Simulation/model as data: Grid of cloud models, each a piecewise lognormal plus power-law n-PDF defined by n_0, sigma_v, T_kin and alpha_PL, with RADEX run across the PDF  
  > "Each cloud model is comprised of a piecewise lognormal and power-law gas volume density PDF" (2.2 Cloud models); "with 500 resolution elements across the PDF in volume density" (2.4 Applying radiative transfer)

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

- Imaging of the archival ALMA HCN, CO and 93 GHz continuum data  
  > "for details on imaging" (Introduction) [from (cite: Wilson:2023)]
- Definition of the ten-galaxy sample (Table 1 of the earlier paper)  
  > "This sample includes the dense centers of five disk galaxies and five U/LIRGs" (Introduction) [from Paper I (cite: Bemis:2023); reference text is blank in the conversion]
- Use of the Burkhart gravoturbulent LN+PL star formation models  
  > "we use the gravoturbulent models of star formation from" (2.3 The model parameter space) [from Paper I; (cite: Burkhart:2018); (cite: Burkhart:2019)]
- Selection of the model parameter space following the Sigma_mol-sigma_v trend  
  > "we selected a model parameter space such that the median" (2.3 The model parameter space) [from Paper I; (cite: Sun:2018)]
- Constant conversion factors alpha_CO = 3 and alpha_HCN = 3.2 alpha_CO applied to modeled intensities  
  > "to produce estimates of gas mass surface densities, which are the same values used in" (3 Model results) [from Paper I (cite: Bemis:2023)]

### Not stated but needed to reproduce (our reading)

- ALMA project code to galaxy mapping, beam sizes, imaging parameters and final intensity values of the ten-galaxy sample (all deferred to earlier papers)
- Number of randomly sampled cloud-scale measurements, random seed and size of the model grid
- RADEX settings other than escape probability geometry: line width definition, background temperature, collider and molecular data files
- Exact expressions for t_dep, epsilon_ff, Sigma_SFR and the f_grav definition (Table 2 of Paper I) and numeric value of the t_dep used in the cosmic ray rate
- Number of bootstrap resamples and how orthogonal distance regression weights were set
- Tabulated measurements from Sun et al. 2020, Brunetti et al. 2021 and 2024 are not reproduced here

## Analysis recipe

1. **Build cloud-model parameter space**: Randomly sample cloud-scale Sigma_mol and sigma_v pairs from PHANGS, NGC 3256 and the Antennae; derive n_0 = Sigma/R, fix alpha_PL and T_kin prescription  
  > "We randomly sampled measurements from each of these cloud-scale studies" (2.3 The model parameter space)
   - parameter: b = 0.4  
  > "we fix $b=0.4$, which represents stochastic mixing between the two turbulent forcing modes" (2.2 Cloud models)
   - parameter: mu = 2.33  
  > "We assume a mean molecular weight of $\mu=2.33$" (2.3 The model parameter space)
   - parameter: alpha_PL = 3 (fiducial)  
  > "We choose $\alpha_\mathrm{PL}=3$ as our fiducial value" (2.3 The model parameter space)
   - parameter: epsilon_0 = 0.01  
  > "For $\alpha_\mathrm{PL}=3$ we take $\epsilon_0=0.01$" (2.3 The model parameter space)
   - assumption: magnetic fields neglected (beta to infinity)  
  > "we neglect magnetic fields and take $\beta\rightarrow\infty$" (2.2 Cloud models)
   - assumption: CO velocity dispersion tracks the turbulent velocity dispersion, typical uncertainty 50%  
  > "Setting our model parameter space this way relies on the assumption that the CO velocity dispersion tracks the turbulent velocity dispersion at these scales." (2.3 The model parameter space)
   - fitting: _not stated_
   - validation: Modeled CO J=1-0 intensities compared with measured intensities of the lower-resolution sample  
  > "we confirm that our modeled CO $J=1-0$ intensities with $I_\mathrm{CO}$ are consistent with the intensities measured in our lower resolution sample" (2.3 The model parameter space)
2. **Compute gas kinetic temperature**: Thermal equilibrium of heating and cooling following Sharda and Krumholz 2022, with cosmic ray heating from Krumholz et al. 2023 and added mechanical heating  
  > "which assumes thermal equilibrium balance of heating and cooling processes in the presence of protostellar radiation feedback" (2.3 The model parameter space)
   - parameter: q_CR = 12.25 eV  
  > "where we have taken the average energy per ionization to be $q_\mathrm{CR}=12.25\ \mathrm{eV}$" (2.3 The model parameter space)
   - assumption: solar metallicity composition for all cloud models  
  > "We note that we assume a solar metallicity composition of the gas for all our cloud models for simplicity" (2.3 The model parameter space)
   - fitting: _not stated_
   - validation: _not stated_
3. **Run non-LTE radiative transfer on each cloud model**: RADEX run at each of 500 resolution elements across the n-PDF using a power-law radial density profile, k = 3/(alpha_PL - 1)  
  > "with 500 resolution elements across the PDF in volume density" (2.4 Applying radiative transfer); "using the escape probability formulation and adopting its default uniform sphere geometry" (2.4 Applying radiative transfer)
   - software: RADEX
   - parameter: x_HCN = 1e-8 and x_CO = 1.4e-4 relative to H2  
  > "we present the results of our models assuming fixed molecular abundances $x_\mathrm{HCN}=10^{-8}$ and $x_\mathrm{CO}=1.4\times10^{-4}$ relative to H$_2$" (2.4 Applying radiative transfer)
   - assumption: column density profile tracks the volume density profile with slope k-1  
  > "We assumes that, in general, the radial profile of the column density will track the radial profile of the volume density." (2.4 Applying radiative transfer)
   - fitting: _not stated_
   - validation: Models compared with EMPIRE and own-sample intensities, and with literature excitation and optical depth results  
  > "our models reproduce the expectations of CO excitation and optical depth" (3.1 Excitation and optical depth)
4. **Derive mass-weighted emissivities, intensities, tau and Tex**: Mass-weighted integration of the unintegrated emissivity over the n-PDF, with emissivity-weighted tau and Tex  
  > "we numerically integrated the PDF over densities that are relevant to molecular gas, roughly $\sim10-10^{8}$ cm$^{-3}$" (2.5 Deriving emissivity and intensity from molecular cloud models)
   - fitting: _not stated_
   - validation: _not stated_
5. **Fit and compare modeled relations to observations and star formation models**: Orthogonal distance regression, Spearman rank coefficients and bootstrapped uncertainties between intensities, emissivities, gas fractions, f_grav and depletion times; compare constant alpha with modeled 1/emissivity  
  > "We perform fits using orthogonal distance regression." (3.1 Excitation and optical depth); "Uncertainties on the fit are determined using bootstrapping." (3.1 Excitation and optical depth)
   - parameter: alpha_HCN/alpha_CO = 3.2 applied to modeled HCN/CO  
  > "We note that we multiply the modeled $I_\mathrm{HCN}/I_\mathrm{CO}$ ratio by a fixed factor, $\alpha_\mathrm{HCN}/\alpha_\mathrm{CO}=3.2$" (3.2 The fraction of gas traced by the HCN/CO ratio)
   - fitting: Orthogonal distance regression; bootstrapped uncertainties; priors and likelihood not stated  
  > "We perform fits using orthogonal distance regression." (3.1 Excitation and optical depth)
   - validation: Modeled slopes and scatter compared to Narayanan et al. 2012, Teng et al. 2024, He et al. 2024 and Tafalla et al. 2023  
  > "We find good agreement with these studies." (3.3 Using estimates of CO and HCN Emissivity to derive gas masses)

## Software

- **RADEX** : non-LTE radiative transfer to compute HCN and CO emissivities, optical depths and excitation temperatures  
  > "We used RADEX (cite: vanderTak:2007) to perform radiative transfer and calculate emissivities of our cloud models." (2.4 Applying radiative transfer)
- **Astropy** : listed among software used in the work; specific use not stated  
  > "This work made use of the following software: RADEX (cite: vanderTak:2007), ASTROPY" (Acknowledgements)
- **pandas** : listed among software used in the work; specific use not stated  
  > "PANDAS (cite: mckinney-proc-scipy-2010; reback2020pandas)" (Acknowledgements)
- **Matplotlib** : listed among software used in the work; specific use not stated  
  > "MATPLOTLIB (cite: Hunter:2007), NUMPY (cite: harris:2020), and SCIPY (cite: virtanen:2020)" (Acknowledgements)
- **NumPy** : listed among software used in the work; specific use not stated  
  > "MATPLOTLIB (cite: Hunter:2007), NUMPY (cite: harris:2020), and SCIPY (cite: virtanen:2020)" (Acknowledgements)
- **SciPy** : listed among software used in the work; specific use not stated  
  > "MATPLOTLIB (cite: Hunter:2007), NUMPY (cite: harris:2020), and SCIPY (cite: virtanen:2020)" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| f_grav in PHANGS-type, NGC 4038/9-type and NGC 3256-type models | 1.7%, 0.8%, 0.6% | not stated | percent | 5 | We confirm that $f_\mathrm{grav}$ is predicted to decrease from $1.7\%$ in the PHANGS-type models to $0.8\%$ and $0.6\%$ in the NGC 4038/9- and NGC 3256-type models, respectively. |
| Fraction of gas above n = 10^4.5 cm^-3 in PHANGS-type, NGC 4038/9-type and NGC 3256-type models | 1.9%, 22%, 30% | not stated | percent | 5 | increases from $1.9\%$ in the PHANGS-type models to $22\%$ and $30\%$ in the NGC 4038/9- and NGC 3256-type models, respectively. |
| Transition density in PHANGS-type, NGC 4038/9-type and NGC 3256-type models | 10^4.5, 10^5.9, 10^6.6 | not stated | cm^-3 | 5 | from $n=10^{4.5}\,\mathrm{cm}^{-3}$ in the PHANGS-type models to $n=10^{5.9}\,\mathrm{cm}^{-3}$ and $n=10^{6.6}\,\mathrm{cm}^{-3}$ in the NGC 4038/9- and NGC 3256-type models, respectively |
| alpha_HCN/alpha_CO to recover f(n>10^3.5 cm^-3) from I_HCN/I_CO | ~5 | not stated | dimensionless | 5 | our models predict that one can apply $\alpha_\mathrm{HCN}/\alpha_\mathrm{CO}\approx5$ to $I_\mathrm{HCN}/I_\mathrm{CO}$ |
| Slope of log(alpha_CO) versus log(I_CO) | -0.26 | +0.03/-0.04 (intercept 0.90 +/- 0.07) | dimensionless | 5 | We find a similar slope, -0.26, compared to -0.32 in |
| Slope of log(alpha_HCN) versus log(I_HCN) | -0.55 | 0.01 (intercept 2.55 +/- 0.01) | dimensionless | 5 | \left(-0.55\pm0.01\right) \mathrm{log}\, \left(\frac{I_\mathrm{HCN}}{\mathrm{K\,km\,s^{-1}}}\right) + 2.55\pm0.01 |
| Slope of log(I_HCN/I_CO) versus log(Sigma_mol) | 0.81 | 0.03 (intercept -2.73 +0.07/-0.08) | dimensionless | 5 | (0.81\pm0.03)\, \mathrm{log}\ \left(\frac{\Sigma_\mathrm{mol}}{\mathrm{M_\odot\,pc^{-2}}}\right) -2.73^{+0.07}_{-0.08} |
| Scatter of epsilon_ff versus P_turb with constant alpha vs with modeled 1/emissivity | ~0.36 vs ~0.05 (theory ~0.02) | not stated | dimensionless | 5 | the scatter in the $\epsilon_\mathrm{ff}$ vs. $P_\mathrm{turb}$ relationship is $\sim0.36$ using method one and becomes $\sim0.05$ when we apply; which is similar to the scatter in the theoretical prediction ($\sim0.02$) |
| Scatter of t_dep versus HCN/CO with constant alpha vs with modeled 1/emissivity | ~0.21 vs ~0.12 (theory ~0.18) | not stated | dimensionless | 5 | The scatter in $t_\mathrm{dep}$ with HCN/CO is $\sim0.21$ when assuming constant conversion factors and becomes $\sim0.12$ when we apply; The scatter in the theoretical prediction is $\sim0.18$. |
| Spearman coefficient between alpha_CO and tau_CO | 0.9 | not stated | dimensionless | 5 | only strongly ($/r_\mathrm{s}/ > 0.7$) correlates with $\left<\tau_\mathrm{CO}\right>$ ($r_\mathrm{s}=0.9$) |
| Slope of epsilon_ff versus P_turb: theoretical prediction | ~0.05 | not stated | dimensionless | 5 | the theoretical prediction for $\epsilon_\mathrm{ff}$ as a function of $P_\mathrm{turb}$ in our models has a slope of only $\sim0.05$ |
| Slope of alpha_CO versus sigma_v in the models | ~-0.5 | not stated | dimensionless | 5 | we find a slope of $\sim\,-0.5$ |
| Mean CO optical depth for x_CO = 1.4e-5, 1.4e-4, 1.4e-3 | 2.7, 16.9, 107.2 | not stated | dimensionless | 3 | We find mean CO optical depths of $\tau_\mathrm{CO}\approx2.7,\ 16.9,\ \mathrm{and}\ 107.2$ |

## Qualitative findings

- HCN J=1-0 is subthermally excited and only moderately optically thick  
  > "HCN appears subthermally excited, as has been found" (3.1 Excitation and optical depth)
- HCN/CO tracks gas above a relatively fixed but moderate density rather than strictly dense gas  
  > "does appear to track gas above a relatively fixed density, but that this fraction includes more moderately dense gas" (3.2 The fraction of gas traced by the HCN/CO ratio)

## Claim tuples

- H: Does I_HCN/I_CO trace the fraction of dense gas above n = 10^4.5 cm^-3 | E: Compare modeled I_HCN/I_CO with gas fractions above 10^2.5 to 10^5.5 cm^-3 from the n-PDFs | R: Closest to a linear relation for the fraction above n ~ 10^3.5 cm^-3; sublinear for 10^4.5 | F: I_HCN/I_CO tracks a fraction including moderate densities, so earlier dense gas fractions are likely overestimated | **supported**
- H: Does I_HCN/I_CO trace the gravitationally bound fraction of gas | E: Compare modeled I_HCN/I_CO and f(n>10^4.5) with f_grav from the LN+PL models | R: Strong negative correlation with f_grav | F: I_HCN/I_CO may not be a straightforward tracer of gas associated with ongoing star formation | **supported**
- H: Does CO emissivity variation drive scatter in star formation scaling relations | E: Apply modeled 1/emissivity instead of a constant alpha_CO and compare scatter | R: Scatter in epsilon_ff vs P_turb falls from ~0.36 to ~0.05 | F: A significant portion of the scatter originates from variations in emissivity | **supported**
- H: Do HCN emissivity variations contribute to the scatter of star formation relations | E: Examine t_dep,dense versus HCN/CO and Spearman correlations of alpha_HCN | R: alpha_HCN correlates with excitation, only weakly with tau | F: HCN emissivity variations do not contribute significantly to the scatter in the models | **supported**

## Reasoning

- Why this data: Model parameter space built from cloud-scale measurements so it includes normal galaxies (PHANGS) and more extreme mergers  
  > "ensures that our models include representatives of cloud-scale observations of normal galaxies (from PHANGS), as well as more extreme systems" (2.3 The model parameter space)
- Why this method: Power-law radial density distributions adopted instead of a fixed optical depth one-zone model as more realistic for molecular clouds  
  > "We therefore adopt power-law radial density distributions that are more realistic for molecular clouds." (2.4 Applying radiative transfer)
- Alternative: Other prescriptions for mean gas density (fixed virial parameter, dynamical equilibrium) gave similar results, so n_0 = Sigma/R was used  
  > "We note that we also considered different prescriptions for calculating mean gas density based on the assumption of energy equipartition" (2.3 The model parameter space)
- How they decided it was enough: _not stated_
- Limitation (authors): Large-scale motions may bias the measured velocity dispersions of the cloud-scale studies  
  > "We cannot exclude the possibility of large-scale motions impacting the measured velocity dispersions of studies at $45-50$ pc." (2.3 The model parameter space)
- Limitation (authors): The heating/cooling model sometimes produces unphysical temperature increases at low density  
  > "the heating/cooling model sometimes produces temperature increases, which are likely unphysical" (2.3 The model parameter space)
- Caveat (inferred, ours): Main results are model outputs; agreement with the ALMA-based sample is shown only qualitatively through figures, with no stated goodness of fit
- Caveat (inferred, ours): Fixed abundances, b = 0.4 and alpha_PL = 3 mean conclusions depend on untested priors, only partly explored in appendices
- Caveat (inferred, ours): The mapping from ALMA data to the model grid goes through earlier-paper tables that this paper does not reproduce

## Reproducibility

- Data public (paper): archival ALMA data (project codes listed in Acknowledgements)  
  > "observed in the sample of ten galaxies from using archival ALMA data of the HCN and CO" (Introduction)
- Products in archive: _not stated_
- Missing: Grid size, random seed and sampling of cloud-scale measurements
- Missing: RADEX line width and collider settings
- Missing: Equations and constants in Table 2 of Paper I for t_dep, epsilon_ff, f_grav
- Missing: Observed-sample intensity table (earlier paper)
- Data volume (inferred): Model reproduction is small (RADEX runs plus public literature tables); re-deriving the observed sample from 16 ALMA projects would be tens to hundreds of GB
- Score (inferred): 2/5, The ALMA data are only used for comparison and imaged in earlier papers; the model recipe is described with equations but key grid and RADEX details are missing and no code is released.
- Rediscovery candidate: no, Main results come from an under-specified model grid rather than a data reduction, and the recipe is not complete enough to redo exactly.

## Links

- Method: Wilson et al. 2023 (cite: Wilson:2023) (Imaging of the archival ALMA HCN, CO and 93 GHz data)
- Method: Burkhart 2018 (cite: Burkhart:2018) (Piecewise lognormal and power-law gas density PDF and star formation model)
- Method: Sharda and Krumholz 2022 (cite: Sharda:2022) (Gas kinetic temperature prescription)
- Method: van der Tak et al. 2007 (cite: vanderTak:2007) (RADEX radiative transfer code)
- Companion: Bemis and Wilson 2023 (cite: Bemis:2023) (Paper I: observed sample and analytical star formation model comparison)
- Related: PHANGS
- Related: EMPIRE
- Related: ALMOND

## Checks

```json
{
 "quotes": 92,
 "quotes_ok": 92,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 16,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 98,
  "stated": 49,
  "rate": 0.5
 },
 "evidence_ok": true
}
```

# Systematic Variations of CO Gas Abundance with Radius in Gas-rich Protoplanetary Disks

`2019ApJ...883...98Z` | The Astrophysical Journal 2019 | first author: Zhang, Ke | arXiv: 1908.03267 | DOI: 10.3847/1538-4357/ab38b9

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Does the CO gas abundance vary with radius in four well-studied protoplanetary disks, and do chemical processing or dust evolution (pebble settling and drifting) explain it?  
  > "Here we investigate the CO abundance structures in four well-studied disks and compare their structures with predictions of chemical processing of CO and transport of CO ice-coated dust grains in disks." (abstract)
- Target **DM Tau**: coordinates _not stated_; z/distance 140 pc  
  > "| DM Tau | 0.53 | 1.25 | 3705 | 140 | 5.00E-04 | 5.00E-02 | 5.95 | 35 | 335 | 3.00E+29 | 1, 2, 3, 4, 5 |" (Table 3); distance from Gaia (Gaia2)  
  > "| DM Tau | 0.53 | 1.25 | 3705 | 140 | 5.00E-04 | 5.00E-02 | 5.95 | 35 | 335 | 3.00E+29 | 1, 2, 3, 4, 5 |" (Table 3)
- Target **TW Hya**: coordinates _not stated_; z/distance 60 pc  
  > "| TW Hya | 0.8 | 1.04 | 4110 | 60 | 5.00E-04 | 5.00E-02 | 2.84 | 7 | 335 | 1.60E+30 | 2, 6, 7, 8 |" (Table 3); distance from Gaia (Gaia2)  
  > "| TW Hya | 0.8 | 1.04 | 4110 | 60 | 5.00E-04 | 5.00E-02 | 2.84 | 7 | 335 | 1.60E+30 | 2, 6, 7, 8 |" (Table 3)
- Target **HD 163296**: coordinates _not stated_; z/distance 101 pc  
  > "| HD 163296 | 2.47 | 1.69 | 9250 | 101 | 1.40E-03 | 1.50E-01 | 5.74 | 49 | 312 | 4.00E+29 | 2, 9, 10, 11, 12, 16 |" (Table 3); distance from Gaia (Gaia2)  
  > "| HD 163296 | 2.47 | 1.69 | 9250 | 101 | 1.40E-03 | 1.50E-01 | 5.74 | 49 | 312 | 4.00E+29 | 2, 9, 10, 11, 12, 16 |" (Table 3)
- Target **IM Lup**: coordinates _not stated_; z/distance 160 pc  
  > "| IM Lup | 1 | 2.5 | 3900 | 160 | 1.70E-03 | 1.70E-01 | 4.5 | 48 | 144 | 4.30E+30 | 2, 13, 14, 15 |" (Table 3); distance from Gaia (Gaia2)  
  > "| IM Lup | 1 | 2.5 | 3900 | 160 | 1.70E-03 | 1.70E-01 | 4.5 | 48 | 144 | 4.30E+30 | 2, 13, 14, 15 |" (Table 3)

## Data provenance

- ALMA projects: 2015.1.00308.S, 2016.1.01495.S, 2013.1.00601.S, 2013.1.00226.S, 2013.1.00798.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15-1574 m across datasets (see Table 1)  
  > "| HD 163296 | 2013.1.00601.S | A. Isella | 151 | 35-1574 | 44 | 08/2015 | 31 |" (Table 1)
- angular resolution: 0.2-0.5 arcsec (20-80 AU)  
  > "The spatial resolution of these observations is between 0.$''$2 and 0.$''$5, corresponding to 20-80 AU resolution based on distances from Gaia measurements" (Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 21-151 min per dataset  
  > "| HD 163296 | 2013.1.00601.S | A. Isella | 151 | 35-1574 | 44 | 08/2015 | 31 |" (Table 1)
- observing dates: _not stated_
- pi or archival as stated: Archival data from other PIs  
  > "We employed a sample of 4 protoplanetary disks with high angular resolution C$^{18}$O line observations from ALMA archive." (Observations)
- Line: C18O 3-2 (DM Tau, TW Hya); 2-1 (HD 163296, IM Lup) (not stated)
- Line: 13CO 3-2 (TW Hya) (not stated)
- Other facility **Gaia**: Distances to the sources  
  > "based on distances from Gaia measurements" (Observations)
- External data: TW Hya gas surface density profile (gamma_g, exponential taper beyond 104 AU) from scattered light  
  > "we adopt the general gas surface density profile of TW Hya derived from scattered light images from (cite: Vanboekel17)" (3.2.1 Disk parameters) [from (cite: Vanboekel17)]
- External data: HD 163296 basic disk structure  
  > "we employ the basic structure of (cite: Isella16) which fitted the 1.3 mm continuum emission" (3.2.1 Disk parameters) [from (cite: Isella16)]
- External data: IM Lup surface density parameters  
  > "other surface density profile parameters from (cite: Cleeves16)" (3.2.1 Disk parameters) [from (cite: Cleeves16)]
- External data: DM Tau large-grain structure  
  > "based on the model of (cite: Andrews11), which matches the 880$\mu m$ continuum observations of DM Tau" (3.2.1 Disk parameters) [from (cite: Andrews11)]
- Simulation/model as data: RAC2D thermo-chemical models run for 1 Myr, with CO abundance rescaled by a grid of depletion factors, used as the model comparison grid  
  > "we generate a set of synthetic line images by rescaling the model CO gas abundance throughout the disk with a constant factor." (4.4 Radial distribution)

## Processing

### Calibration

- pipeline or manual: Archive accompanying reduction scripts  
  > "All raw data were calibrated through the accompanying reduction scripts under the corresponding version of CASA" (Observations)
- casa version: CASA 5.0 for imaging  
  > "The following imaging processes were all performed with CASA 5.0." (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10%  
  > "The absolute flux uncertainty is estimated to be 10%." (Observations)
- self calibration: Self-cal on continuum from line-free channels for each dataset  
  > "We carried out self-cal for each data set using continuum visibilities combined from line-free channels." (Observations)

### Imaging

- task: tclean  
  > "The calibrated data were imaged in CASA using the `tclean` task." (Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust=0.5 or 1  
  > "Briggs weighting (robust=0.5 or 1) and the multiscale option with a factor of (0, 5, 10) were used." (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: (0, 5, 10)  
  > "Briggs weighting (robust=0.5 or 1) and the multiscale option with a factor of (0, 5, 10) were used." (Observations)
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: IM Lup two programs combined after self-cal using fixvis and fixplanets  
  > "using `fixvis` and `fixplanets` tasks in CASA to shift the data sets to a common phase center" (Observations)
- smoothing: Channel width 0.2 or 0.22 km/s; HD 163296 binned to 0.2 km/s  
  > "we binned the data into a channel width of 0.2 ${\rm km\,s^{-1}}$for a better signal-to-noise ratio" (Observations)
- final beam: e.g. 0.36x0.29 (DM Tau), 0.58x0.39 arcsec (IM Lup)  
  > "| IM Lup | C$^{18}$O (2-1) | 0.2 | 4 | 1.29$\pm$0.04 | 0.58$\times$0.39 (-76) | 93$\times$62 |" (Table 2)
- final rms: 2.86-5.3 mJy/beam per channel  
  > "| TW Hya | C$^{18}$O (3-2) | 0.22 | 5.3 | 1.21$\pm$0.04 | 0.36$\times$0.31 (-51) | 22$\times$19 |" (Table 2)

### Inherited from earlier work

- Disk density structures and parameters adopted from earlier modeling  
  > "When gas/small dust distribution constraints are available from scattered light images, we adopt these values from previous studies." (3.2.1 Disk parameters) [from Vanboekel17, Isella16, Cleeves16, Andrews11, Andrews12]
- Thermo-chemical code RAC2D and initial composition  
  > "The chemical models are initialized with a composition listed in the Table 1 of (cite: Du14)." (3.3 The numerical methods) [from (cite: Du14)]
- Large-grain mass fraction of 99% for IM Lup  
  > "we adopt 99% of the mass in large grains as this value was used on the comprehensive model of the IM Lup disk of (cite: Cleeves16)" (3.2.1 Disk parameters) [from (cite: Cleeves16)]

### Not stated but needed to reproduce (our reading)

- Rest frequencies and spectral windows used
- Line-free channel ranges for continuum and self-cal solution intervals
- Image size, cell size, masking, and clean thresholds
- CASA versions for the archive calibration
- Method for assigning best depletion factor at each radius (fit metric, radial binning, uncertainties)
- Stellar UV spectrum and luminosity details
- Full RAC2D configuration and code availability
- SED data used for the h0 and psi fits

## Analysis recipe

1. **Calibrate and image C18O/13CO lines**: Archive reduction scripts, self-cal on continuum, tclean imaging  
  > "The calibrated data were imaged in CASA using the `tclean` task." (Observations)
   - software: CASA
   - parameter: Briggs robust 0.5 or 1; multiscale (0,5,10); channel width 0.2 or 0.22 km/s  
  > "Briggs weighting (robust=0.5 or 1) and the multiscale option with a factor of (0, 5, 10) were used." (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Build parametric disk density models**: Self-similar surface density with gas, small and large grain components, taken from the literature  
  > "The disk model is composed of three mass components – gas, a small dust population, and a large dust grain population." (3.1 Parametric Density Model)
   - parameter: Gas-to-dust ratio 100, chi=0.2 settling, 80% mass in large grains (99% for IM Lup)  
  > "Here we adopt an intermediate level of 80% of the mass in large grains for modeling." (3.2.1 Disk parameters)
   - assumption: MRN size distribution n(a) ∝ a^-3.5; Mie opacities  
  > "Both dust populations are assumed to follow an MRN size distribution $n(a)\propto a^{-3.5}$" (3.1 Parametric Density Model)
   - fitting: _not stated_
   - validation: _not stated_
3. **Constrain scale height and flaring with SEDs**: Grid of h0 and psi run with RADMC3D to find best-fitting SED models  
  > "we first run a grid of $h_0$ and $\psi$ to search for best-fitting SED models of each disk." (3.3 The numerical methods)
   - software: RADMC3D
   - parameter: h0 0.02-0.2 step 0.02; psi 1-1.3 step 0.05  
  > "The $h_0$ range is from 0.02 to 0.2 with a step size of 0.02, and $\phi$ from 1 to 1.3 with a step size of 0.05." (3.3 The numerical methods)
   - fitting: Grid search  
  > "To constrain the vertical scale height of dust, we first run a grid of $h_0$ and $\psi$ to search for best-fitting SED models of each disk." (Methods, The numerical methods)
   - validation: _not stated_
4. **Run thermo-chemical models and synthesize line images**: RAC2D 2D time-dependent chemistry for 1 Myr, LTE ray tracing, convolution to observed resolution  
  > "we compute line images using the ray-tracing module of RAC2D, assuming an LTE condition." (3.3 The numerical methods)
   - software: RAC2D
   - parameter: zeta_CR = 1.36e-18 (standard) and 1.36e-17 s^-1 (high); gamma ±0.2 tests  
  > "we run two sets of models: a set of standard models with a $\zeta_{\rm CR}=1.36\times10^{-18}$ s$^{-1}$ and the other set with a high CR rate of 1.36$\times10^{-17}$ s$^{-1}$." (3.4 Parameter Tests)
   - assumption: Initial CO abundance 1.4e-4 relative to H; CO/C18O=570, CO/13CO=69; no isotopologue fractionation  
  > "We rescale the output CO abundance by the local ISM ratios of CO/$^{13}$CO= 69, and CO/C$^{18}$O=570" (3.3 The numerical methods)
   - fitting: _not stated_
   - validation: Model CO snowline locations compared with literature  
  > "the mid-plane CO snowline locations are consistent with existing observational constraints" (4.1 results)
5. **Derive radial CO depletion profiles**: Rescale model CO abundance by constant factors on a grid and record the best-matching factor at each radius from surface brightness profiles  
  > "Using the grid of models, we record which depletion factor matches the best with models at each radius." (4.4 Radial distribution)
   - parameter: Depletion factor grid 0.1 to 400, step ×1.2  
  > "The grid spans from a depletion factor of 0.1 to 400, increasing by a factor of 1.2 at each step." (4.4 Radial distribution)
   - fitting: Grid matching of radial surface brightness; no formal likelihood stated  
  > "Using the grid of models, we record which depletion factor matches the best with models at each radius." (Results, Radial distribution of CO gas abundance: models vs. observations)
   - validation: Compared change of I_CO from gamma ±0.2 (<30%) against derived variations  
  > "The $I_{\rm CO}$ profiles only change less than 30% for uncertainty of 0.2 in the $\gamma$ index." (4.3)

## Software

- **CASA** 5.0 (imaging): Calibration, self-cal, tclean imaging, fixvis/fixplanets  
  > "The following imaging processes were all performed with CASA 5.0." (Observations)
- **RADMC3D** : Dust thermal structure and model SEDs  
  > "We first use the radiative transfer code RADMC3D to calculate the dust thermal structure in a disk" (3.3 The numerical methods)
- **RAC2D** : Thermo-chemical modeling and line ray tracing  
  > "a full 2D time-dependent thermo-chemical code RAC2D" (3.3 The numerical methods)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Observed C18O (3-2) integrated flux, DM Tau | 3.0 | 0.1 | Jy km/s | 1 | / DM Tau / C$^{18}$O (3-2) / 0.22 / 5 / 3.0$\pm$0.1 / 0.36$\times$0.29 (-47) / 50$\times$41 / |
| DM Tau CO depletion inside 100 AU | factor of 12 | not stated | dimensionless | 5 | the DM Tau disk shows a nearly constant level of CO depletion inside 100 AU (by a factor of 12) |
| TW Hya CO depletion beyond 100 AU | >200 | not stated | dimensionless | 5 | outside 100 AU the CO abundance is extremely depleted ($>$ a factor of 200) |
| HD 163296 CO enhancement inside 70 AU | factor of 2-5 | not stated | dimensionless | 5 | HD 163296 shows a modest CO abundance enhancement inside 70 AU (by a factor of 2-5) |
| CO gas column depletion in high-CR models, DM Tau and TW Hya, 10-100 AU | 5-20 | not stated | dimensionless | 4 | Models of DM Tau and TW Hya show substantial CO gas depletions between 10-100 AU, by a factor of 5-20 after 1 Myr. |
| Fraction of CO converted in standard models | <10% | not stated | percent | 4 | In these models, less than 10% of total CO (gas+ice) have been converted to other carbon carriers after 1 Myr. |

## Qualitative findings

- CO abundance varies by at least an order of magnitude with radius within individual disks  
  > "We find at least one order of magnitude variation within individual disks." (Summary)
- Chemical processing alone, even with ISM-level CR rate, cannot explain weak CO lines because depletion occurs deep in the disk  
  > "The reason is that the ionization driven CO depletions are active within the deep denser regions close to the mid-plane of these disks." (Summary)

## Claim tuples

- H: CO gas abundance varies with radius in disks | E: Compare C18O (and 13CO) surface brightness profiles with thermo-chemical models rescaled by depletion factors | R: About one order of magnitude radial variation in each disk | F: CO abundance in the warm layer varies significantly with radius | **supported**
- H: Chemical processing of CO explains observed depletion | E: Run models with standard and high cosmic-ray rates and compare C18O brightness | R: Column density drops but surface brightness changes little (<20%) | F: Chemical processing without vertical mixing is insufficient | **supported**
- H: Dust evolution (pebble settling and drift) explains the radial pattern | E: Compare derived profiles with Krijt et al. 2018 predictions | R: Three disks qualitatively match, but depletion magnitudes are higher than predicted | F: Dust evolution alone cannot fully explain the depletion | **partially**
- H: The TW Hya outer disk is CO-depleted by a known mechanism | E: Compare with chemistry and dust evolution predictions | R: Extreme depletion beyond 100 AU fits neither | F: Likely gas dissipation beyond 100 AU | **partially**

## Reasoning

- Why this data: Optically thin C18O, with 13CO for TW Hya beyond 100 au where C18O drops below noise  
  > "For the TW Hya disk, we included additional $^{13}$CO (3-2) line observations to constrain the CO abundance structure in $>$100 au region" (Observations)
- Why this method: _not stated_
- Alternative: Substructures alone rejected as the cause of order-of-magnitude CO abundance variations  
  > "it is unlikely that the order of magnitude variations in CO abundance profiles are due to substructures alone." (5.3)
- How they decided it was enough: _not stated_
- Limitation (authors): Small-scale substructures ignored; smooth density profiles used  
  > "We also ignore small-scale substructures in these disks" (3.2.1 Disk parameters)
- Limitation (authors): Gas-to-dust ratio fixed at 100; gas mass uncertainty considered not crucial  
  > "For simplicity, we use a gas-to-dust (small+large) mass ratio of 100 for all four disks." (3.2.1 Disk parameters)
- Caveat (inferred, ours): Results depend on assumed gas masses and surface density profiles; depletion degenerate with gas-to-dust ratio
- Caveat (inferred, ours): No formal uncertainties on depletion profiles
- Caveat (inferred, ours): Only one model grid per disk; thermal structure not constrained by observations
- Caveat (inferred, ours): Depletion derived from optically thick emission layers is sensitive to temperature
- Caveat (inferred, ours): Single-timestep 1 Myr chemistry for disks of differing ages

## Reproducibility

- Data public (paper): Data from ALMA archive  
  > "high angular resolution C$^{18}$O line observations from ALMA archive." (Observations)
- Products in archive: _not stated_
- Missing: RAC2D configuration/availability
- Missing: SED photometry and fitting details
- Missing: Exact radial fitting procedure
- Missing: Imaging parameters like mask, size, thresholds
- Data volume (inferred): ~50-200 GB raw across five datasets
- Score (inferred): 3/5, Data are public and the model setup is partly tabulated, but the RAC2D code and the radial matching method are under-specified.
- Rediscovery candidate: no, The recipe depends on a specialized thermo-chemical code and an incompletely described fitting procedure.

## Links

- Method: (cite: Du14) (RAC2D thermo-chemical code description)
- Method: (cite: Krijt18) (dust evolution predictions compared with results)
- Companion: (cite: Bergner19) (C2H analysis of the same three disks)
- Related: Large ALMA Cycle 6 program on dust substructures and chemistry

## Checks

```json
{
 "quotes": 77,
 "quotes_ok": 77,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 5,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 91,
  "stated": 59,
  "rate": 0.648
 },
 "evidence_ok": true
}
```

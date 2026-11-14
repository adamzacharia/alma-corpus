# ATOMS-QUARKS Survey: Inflow and Infall in Massive Protocluster G318.049+00.086— Evidence of Competitive Accretion

`2026ApJ...999..180G` | The Astrophysical Journal 2026 | first author: Gupta, Shivani | arXiv: 2602.01238 | DOI: 10.3847/1538-4357/ae40fd

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation
- Question: How do filamentary inflow and core-scale infall in the protocluster G318.049+00.086 feed its cores, and do they support competitive accretion?  
  > "We present a gas kinematic study of the massive protocluster G318.049+00.086." (abstract)
- Target **G318.049+00.086 (I14498-5856)**: coordinates _not stated_; z/distance 2.90 (+0.52/-0.47) kpc; Vlsr -49.82 km/s  
  > "is located at a distance of 2.90$^{+0.52}_{-0.47}$ kpc (cite: 2019ApJ...885..131R) and has a local standard of rest velocity (V$_{\rm{lsr}}$) of -49.82 km s$^{-1}$" (Selected region); distance from 2019ApJ...885..131R  
  > "is located at a distance of 2.90$^{+0.52}_{-0.47}$ kpc (cite: 2019ApJ...885..131R) and has a local standard of rest velocity (V$_{\rm{lsr}}$) of -49.82 km s$^{-1}$" (Selected region)

## Data provenance

- ALMA projects: 2019.1.00685.S, 2017.1.00545.S
- bands: 3 mm (ATOMS), 1.3 mm (QUARKS), ASSEMBLE Band 7-like lines near 343-345 GHz  
  > "3 mm (left panel) and 1.3 mm (right panel) dust continuum maps of the protocluster obtained from the ATOMS and QUARKS surveys" (Selected region)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: ATOMS: 12m+ACA; ASSEMBLE: 12m only; QUARKS: 12m+7m  
  > "the ASSEMBLE data include only the 12 m array, whereas the QUARKS data combine the 12 m and 7 m arrays" (Selected region)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ATOMS 3 mm beam 2.34"x2.16"; QUARKS ~0.3" (beam 0.40"x0.34")  
  > "having a beam size of 2.34$^{\prime\prime}$ $\times$ 2.16$^{\prime\prime}$" (2.1 ATOMS survey)
- max recoverable scale: ATOMS ~87"; ASSEMBLE ~8.45"; QUARKS combined ~8.45"  
  > "The maximum recoverable scale (MRS) of 12m + ACA combine data reaches $\sim$ 87$^{\prime\prime}$" (2.1 ATOMS survey)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Survey data (PI Tie Liu)  
  > "PI: Tie Liu" (2.1 ATOMS survey)
- Line: H13CO+ (1-0) (86.754288 GHz)
- Line: CCH (1-0) F(2-1) (87.316898 GHz)
- Line: CH3OH 13(1,12)-13(0,13) (342.729781 GHz)
- Line: H13CN (4-3) (345.339760 GHz)
- External data: Core catalog (16 cores; masses, radii, classification)  
  > "We adopted these cores in our analyses." (Selected region) [from (cite: 2024ApJS..270....9X)]
- External data: Distance 2.90 kpc  
  > "located at a distance of 2.90$^{+0.52}_{-0.47}$ kpc (cite: 2019ApJ...885..131R)" (Selected region) [from (cite: 2019ApJ...885..131R)]
- External data: Clump mass 1023.3 Msun and Tdust 26.7 K  
  > "The mass and dust temperature ($T_{\rm{dust}}$) of the protocluster are 1023.3 M$_{\odot}$ and 26.7 K" (Selected region) [from (cite: 2018MNRAS.473.1059U)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 5.6 (ATOMS)  
  > "Common Astronomy Software Applications (CASA) package version 5.6" (2.1 ATOMS survey)
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
- primary beam correction: All images primary beam corrected  
  > "All the images used in our analysis are primary beam corrected." (2.1 ATOMS survey)
- array combination: 12m and ACA calibrated separately, then combined and re-imaged  
  > "subsequently the visibility data were combined and re-imaged to recover the extended emission" (2.1 ATOMS survey)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ATOMS survey data reduction  
  > "Further details about the survey and data reduction can be found in (cite: 2020MNRAS.496.2790L)." (2.1 ATOMS survey) [from (cite: 2020MNRAS.496.2790L)]
- QUARKS continuum map construction  
  > "The corresponding 1.3 mm dust continuum map is prepared from the available line-free spectral channels (cite: 2024RAA....24b5009L)." (2.3 QUARKS survey) [from (cite: 2024RAA....24b5009L)]
- Mass inflow rate method  
  > "we followed a similar methodology described in (cite: 2013ApJ...766..115K)" (3.4) [from (cite: 2013ApJ...766..115K)]

### Not stated but needed to reproduce (our reading)

- FilFinder parameters (smoothing, thresholds, masks) for both maps
- Continuum-subtraction and line-free channels
- Hill5 priors, bounds, walker and step numbers
- Segments of PV diagrams used for linear fits
- Method for deriving filament mass from N(H2) (mean molecular weight, pixel region)
- Imaging parameters (robust, cell size) of survey products

## Analysis recipe

1. **Identify filaments**: FilFinder on H13CO+ moment-0 and 1.3 mm continuum maps  
  > "we also employed the `FilFinder` algorithm to the 1.3 mm continuum map obtained in the QUARKS survey" (3.1)
   - software: FilFinder
   - fitting: _not stated_
   - validation: Reproduced the earlier H13CO+ filaments; compared overlay of both  
  > "the previously identified filamentary structures were well-reproduced with the same `FilFinder` algorithm" (3.1)
2. **Column density map**: LTE optically thin H13CO+ N, then N(H2) with abundance 1e-11, pixels >5 sigma  
  > "we considered only the pixels with integrated intensity $>5\sigma$ in the moment-0 map" (3.2)
   - assumption: Tex = Tdust of clump; [H13CO+/H2]=1e-11  
  > "we assume that $T_{\rm ex}$ is equal to the dust temperature of the clump ($T_{\rm dust}$)" (3.2)
   - fitting: _not stated_
   - validation: Sensitivity to opacity, temperature, abundance discussed  
  > "Adopting these extreme values would decrease or increase the inferred column density by an order of magnitude, respectively, implying that the total mass estimates could vary by up to a factor of 10." (3.2 Column density map)
3. **Filament velocity gradients**: PV diagrams along skeletons; least-squares linear fits  
  > "we performed least-square fits to different parts of the PV diagrams signifying the filaments" (3.3)
   - fitting: least squares  
  > "For estimation of the velocity gradients, we performed least-square fits to different parts of the PV diagrams signifying the filaments" (3.3 Dynamical properties of filaments)
   - validation: _not stated_
4. **Mass inflow rate along filaments**: Mdot = gradV * Mfil / tan(alpha), cylindrical model  
  > "assuming the inclination angle ($\alpha$) of 45$^{\circ}$" (3.4)
   - assumption: alpha = 45 deg (tan=1); factor 2 uncertainty for 30-60 deg  
  > "We thus assume $\tan$ $\alpha$ = 1 in our calculation" (3.4)
   - fitting: _not stated_
   - validation: _not stated_
5. **Core systemic velocity and profile classification**: Gaussian fits to optically thin CH3OH / H13CN(4-3); classify blue/red H13CO+ and CCH profiles  
  > "We fit Gaussians to the average spectra of these optically thin tracers to determine the V$_{\rm lsr}$ of each core." (3.5)
   - fitting: Gaussian  
  > "We fit Gaussians to the average spectra of these optically thin tracers to determine the V$_{\rm lsr}$ of each core." (3.5 Gas infall rates in cores)
   - validation: Vlsr of thin tracers coincides with dip of H13CO+  
  > "Figure [6](#fig:infall_prove) shows that the V$_{\rm lsr}$ of these tracers coincides with the dip in the H$^{13}$CO$^{+}$ profiles for cores 8, 10, and 13" (3.5)
6. **Infall velocity and mass infall rate**: Hill5 fit with emcee MCMC to average spectra with S/N>=15; Mdot=3 M V/R  
  > "we applied a signal-to-noise (S/N) threshold $\gtrsim$ 15 to the observed spectra" (3.5)
   - software: emcee, FUNStools
   - parameter: rms 0.27 K from line-free channels  
  > "based on an rms noise level of 0.27 K" (3.5)
   - fitting: Hill5 with 5 free parameters (Tpeak, tau, Vinfall, VLSR, sigma); two-trial MCMC  
  > "These five parameters were set as free with initial guesses and bounds to fit the observed spectra with the model." (Appendix Hill5)
   - validation: Corner plots; H13CO+ and CCH values consistent for cores 10-12  
  > "Note that for cores where V$_{\rm in}$ is derived for both the tracers (cores 10, 11 and 12), the obtained values are found to be consistent with each other." (3.5 Gas infall rates in cores)

## Software

- **CASA** 5.6: Calibration and imaging of ATOMS data  
  > "Common Astronomy Software Applications (CASA) package version 5.6" (2.1 ATOMS survey)
- **FilFinder** : Filament identification  
  > "Python-based `FilFinder` algorithm" (3.1)
- **emcee** : MCMC for Hill5 fits  
  > "using the `emcee`[^2] Python package" (Appendix Hill5)
- **FUNStools** : Spectral rms estimate  
  > "estimated from the line-free channels using `FUNStools`" (3.5)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Velocity gradient F1 (table) | 17.8 | 1.1 | km/s/pc | 3 | 17.8$\pm$1.1 |
| Velocity gradient F3 | 22.1 | 2.0 | km/s/pc | 3 | 22.1$\pm$2.0 |
| Velocity gradient F4 | 10.9 | 0.8 | km/s/pc | 3 | 10.9$\pm$0.8 |
| Mass inflow rate F3 | 5017 | 1735 | Msun/Myr | 4 | 5017$\pm$1735 |
| Mass inflow rate F1 | 1762 | 598 | Msun/Myr | 4 | 1762$\pm$598 |
| Mass inflow rate F4 | 1297 | 445 | Msun/Myr | 4 | 1297$\pm$445 |
| Line mass of filaments | 992-1746 | not stated | Msun/pc | 4 | found to be 992-1746 M$_\odot$ pc$^{-1}$ |
| Core 7 mass infall rate (CCH) | 196.2 | 110.9 | 1e-5 Msun/yr | 6 | 196.2$\pm$110.9 |
| Core 5 mass infall rate (H13CO+) | 54.9 | 35.1 | 1e-5 Msun/yr | 6 | 54.9$\pm$35.1 |

## Qualitative findings

- Most cores show blue profiles; cores 10, 11, 13 show red profiles; hub cores have higher infall rates  
  > "the derived mass infall rates for the protostellar cores in hub-region is significantly higher in comparison to those located along the filaments." (abstract)

## Claim tuples

- H: Filaments channel mass onto the central hub | E: PV analysis of H13CO+ along filaments | R: Gradients 10.9-22.1 km/s/pc; inflow rates >1e3 Msun/Myr | F: Hub can form massive stars | **supported**
- H: Cores show infall or expansion | E: H13CO+ and CCH profile classification and Hill5 fits | R: Majority blue, a few red | F: Collapse in most cores, expansion in a few | **supported**
- H: Competitive accretion operates | E: M-R relation plus filament velocity profiles | R: Massive-regime cores with red profiles lose gas to hub | F: Supports competitive accretion | **partially**

## Reasoning

- Why this data: H13CO+ and CCH used since HCO+ is contaminated by outflows and CS has coarse resolution  
  > "the HCO$^{+}$ line is significantly contaminated by outflow activities from the embedded protostars" (3.5)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Optically thin assumption gives lower limit on N(H2); mass uncertain up to factor 10 from abundance  
  > "implying that the total mass estimates could vary by up to a factor of 10" (3.2)
- Caveat (inferred, ours): Constant Tdust=Tex across region
- Caveat (inferred, ours): Inclination fixed at 45 deg
- Caveat (inferred, ours): Single-spectrum Hill5 fits may be non-unique
- Caveat (inferred, ours): Small number of cores
- Caveat (inferred, ours): Inconsistent units in summary (Msun/yr vs Myr) and F1 gradient 22.5 vs 17.8

## Reproducibility

- Data public (paper): Project IDs given; public status not stated  
  > "(ATOMS; Project ID: 2019.1.00685.S; PI: Tie Liu)" (2.1 ATOMS survey)
- Products in archive: _not stated_
- Missing: FilFinder settings
- Missing: Hill5 priors and MCMC settings
- Missing: Filament mass derivation details
- Missing: Survey image products
- Data volume (inferred): ~50-150 GB for ATOMS, ASSEMBLE and QUARKS raw data
- Score (inferred): 3/5, Data and main formulas are given but many analysis parameters are missing.
- Rediscovery candidate: no, Key settings missing, depends on external core catalog and survey-pipeline products.

## Links

- Method: (cite: 2020MNRAS.496.2790L) (ATOMS survey and data reduction)
- Method: (cite: 2005ApJ...620..800D) (Hill5 infall model)
- Method: (cite: 2013ApJ...766..115K) (Filament inflow rate method)
- Companion: (cite: 2024ApJS..270....9X) (Core catalog)
- Companion: (cite: 2022MNRAS.514.6038Z) (Prior filament analysis in ATOMS)
- Related: ATOMS
- Related: ASSEMBLE
- Related: QUARKS

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 41,
  "rate": 0.539
 },
 "evidence_ok": true
}
```

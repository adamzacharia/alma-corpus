# Key Physical Parameters Influencing Fragmentation and Multiplicity in Dense Cores of Orion A

`2025ApJ...990...80K` | The Astrophysical Journal 2025 | first author: Kao, Jo-Shui | arXiv: 2507.22470 | DOI: 10.3847/1538-4357/adf206

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation
- Question: Which physical parameters (density, turbulence, magnetic field) distinguish dense cores in Orion A hosting binary/multiple protostars from those hosting single protostars?  
  > "we investigated the key mechanisms influencing fragmentation by comparing the physical conditions of fragmented and unfragmented dense cores ($\sim$0.1 pc) in Orion A." (abstract)
- Target **Orion A dense cores (53 protostellar cores)**: coordinates Table 1 lists core centers; JCMT pointing center 05h36m00, -06°23'00  
  > "$D$ is the distance to the core ranging from 383 to 392 pc (cite: 2020ApJ...890..130T)" (3.2 Core Mass and Density); z/distance 383 to 392 pc  
  > "$D$ is the distance to the core ranging from 383 to 392 pc (cite: 2020ApJ...890..130T)" (3.2 Core Mass and Density); distance from Tobin et al. 2020 (VANDAM)  
  > "$D$ is the distance to the core ranging from 383 to 392 pc (cite: 2020ApJ...890..130T)" (3.2 Core Mass and Density)

## Data provenance

- ALMA projects: _none stated_
- bands: VANDAM ALMA at 0.87 mm  
  > "with the Atacama Large Millimeter/submillimeter Array (ALMA) at 0.87 mm and a resolution of $\sim 0.1\ensuremath{''}$ (40 au)" (2.1 Protostar Sample)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.1" (40 au)  
  > "at 0.87 mm and a resolution of $\sim 0.1\ensuremath{''}$ (40 au), and it is sensitive to the projected separations larger than 20 au" (2.1 Protostar Sample)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: N2H+ J=1-0 (Nobeyama 45m, not ALMA) (not stated)
- Other facility **JCMT SCUBA-2/POL-2**: 850 um continuum and polarization maps for core identification, mass and B-field  
  > "For the present paper, we used the POL-2 data at 850 $\mu$m." (2.2 JCMT Data)
- Other facility **Herschel Gould Belt Survey**: dust temperature map (37" resolution)  
  > "The dust temperature was estimated by fitting the spectral energy distributions at 160, 250, 350, and 500 $\mu$m." (2.3 Herschel Dust Temperature Map)
- Other facility **Nobeyama 45-m**: N2H+ (1-0) cube for velocity dispersion  
  > "a beam size of 23.4$''$, and a spectral resolution of 37.8 kHz, corresponding to 0.12 km s$^{-1}$" (2.4 Nobeyama 45-m N$_2$H$^+$ J=1–0)
- External data: VANDAM protostar catalog (positions, ALMA fluxes, distances)  
  > "obtained from Table 6 in (cite: 2020ApJ...890..130T)" (3.1 Core Identification) [from (cite: 2020ApJ...890..130T)]
- External data: Nobeyama N2H+ (1-0) cube  
  > "We obtained the N$_2$H$^+$ J=1–0 image cube taken by the 45-m telescope of the Nobeyama Radio Observatory from (cite: 2008PASJ...60..407T)." (2.4 Nobeyama 45-m N$_2$H$^+$ J=1–0) [from (cite: 2008PASJ...60..407T)]
- External data: dust opacity 0.0125 cm2 g-1 at 850 um  
  > "Here we adopted $\kappa_{\nu}$ of 0.0125 cm$^2$ g$^{-1}$ (cite: 2017ApJ...836..132J)" (3.2 Core Mass and Density) [from (cite: 2017ApJ...836..132J)]

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

- DCF correction factor Q = 0.5  
  > "is adopted to be 0.5 (cite: 2001ApJ...546..980O)" (3.6 Magnetic Field and Mass-to-flux Ratio) [from (cite: 2001ApJ...546..980O)]
- N2H+ hyperfine relative intensity ratios  
  > "their relative intensity ratios were from (cite: 1992ApJ...387..417W)" (3.4 Velocity Dispersion) [from (cite: 1992ApJ...387..417W)]

### Not stated but needed to reproduce (our reading)

- Exact JCMT pol2map parameters and the bootstrap/binning details
- Exact astrodendro call and core-size cuts for excluding unresolved cores
- Details of N2H+ hyperfine fitting code and BIC criterion
- Debiasing method for polarized intensity
- Treatment of cores without N2H+ coverage in the DCF calculation
- Which of the 275 Orion A protostars lie in the JCMT map

## Analysis recipe

1. **identify cores and associate with protostars**: astrodendro dendrogram on 850 um map, 2D Gaussian fit to leaves; protostars inside core ellipse counted  
  > "We identified dense cores in the JCMT 850 $\mu$m map by applying the *astrodendro* package which builds dendrograms of observed data and fits a 2D Gaussian function to each leaf." (3.1 Core Identification)
   - software: astrodendro
   - parameter: min threshold 50 mJy/beam, min significance 30 mJy/beam, min 5 pixels  
  > "we adopted the minimum threshold of 50 mJy/beam (5$\sigma$ noise level), minimum significance of 30 mJy/beam (3$\sigma$ noise level), and minimum number of pixels of 5" (3.1 Core Identification)
   - fitting: _not stated_
   - validation: tested that excluding systems with separations <500 au does not change results  
  > "We have tested it and confirmed that including or excluding these sources having multiples with small separations does not affect the results of our subsequent analysis and conclusions." (3.1 Core Identification)
2. **derive core mass and density**: optically thin dust emission with Herschel Td, spherical density  
  > "found that all the dense cores in our sample have $\tau < 0.02$ at 850 $\mu$m. Thus, our assumption of optically thin dust emission is valid." (Core Mass and Density)
   - assumption: kappa=0.0125 cm2/g (32% uncertainty), Td from Herschel, tau<0.02  
  > "found that all the dense cores in our sample have $\tau < 0.02$ at 850 $\mu$m." (3.2 Core Mass and Density)
   - fitting: _not stated_
   - validation: disk contribution checked against ALMA fluxes: <15% in 80% of sample  
  > "In 80% of our sample, the possible disk contribution is less than 15% of the total flux of the dense cores." (3.2 Core Mass and Density)
3. **N2H+ velocity dispersion and Mach number**: seven-hyperfine fit per pixel, optical-depth-weighted average sigma_NT, Mach = sigma_NT/c_s  
  > "We calculated the average $\Delta v$ of all the pixels within the core area weighted by their optical depths" (3.5 Mach Number and Turbulence Pressure)
   - assumption: gas temperature equals dust temperature  
  > "Here we assumed that the gas temperature is the same as the dust temperature." (3.3 Jeans Instability)
   - fitting: Gaussian profile, common Tex and width; two components if BIC prefers  
  > "we fitted the spectra with two velocity components if the Bayesian information criterion suggests that the two velocity components provide a better fit" (3.4 Velocity Dispersion)
   - validation: _not stated_
4. **magnetic field strength and mass-to-flux ratio**: DCF with unsharp-masking angular dispersion; lambda=7.6e-21 N(H2)/B  
  > "We estimated the magnetic field strengths in the dense cores using the David-Chandrasekhar-Fermi (DCF) method" (3.6 Magnetic Field and Mass-to-flux Ratio)
   - parameter: 3x3 pixel (36") smoothing kernel  
  > "We smoothed the magnetic field orientation map with a kernel of 3 by 3 pixels (or 36$\ensuremath{''}$ by 36$\ensuremath{''}$)" (3.6 Magnetic Field and Mass-to-flux Ratio)
   - assumption: no inclination correction  
  > "we did not correct it for projection due to unknown inclination angles" (3.6 Magnetic Field and Mass-to-flux Ratio)
   - fitting: _not stated_
   - validation: _not stated_
5. **compare single vs multiple cores**: CDFs with Monte Carlo uncertainties (10000 realizations), KS tests, Spearman correlations  
  > "We repeated this process 10000 times, generated a sample of CDF, and adopted the 50th percentile at each step as the final CDF" (4 Results)
   - fitting: power-law fits to mass-radius and density-radius relations  
  > "The power-law fitting to the mass–radius and density–radius relations suggests that the mass and density tend to be a factor of 3 higher" (4.2 Density and Thermal Jeans Instability)
   - validation: _not stated_

## Software

- **starlink (pol2map)** 2023A: POL-2 data reduction  
  > "calibrated together using the software *starlink* version 2023A" (2.2 JCMT Data)
- **astrodendro** : core identification  
  > "by applying the *astrodendro* package which builds dendrograms of observed data" (3.1 Core Identification)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| dense cores with single protostars | 38 | not stated | cores | 1 | we identified 38 dense cores hosting single protostars and 15 cores hosting binary or multiple systems |
| KS p-value, Mach number single vs multiple | 0.006 | +0.002/-0.003 | dimensionless | 5 | with a p-value of $0.006^{+0.002}_{-0.003}$ from the KS test |
| KS p-value, core mass | 0.005 | +0.01/-0.003 | dimensionless | 5 | The p-value from the KS test on their CDF is $0.005^{+0.01}_{-0.003}$. |
| KS p-value, P_T/u_G | 0.27 | +0.31/-0.20 | dimensionless | 5 | with a p-value of $0.27^{+0.31}_{-0.20}$ from the KS test |
| KS p-value, mass-to-flux ratio | 0.64 | +0.25/-0.37 | dimensionless | 5 | The KS test results in a p-value of $0.64^{+0.25}_{-0.37}$. |
| supersonic fraction in multiples | 73% (11 of 15) | not stated | percent | 3 | 4 of them (27%) have subsonic and 11 of them (73%) have supersonic turbulence |

## Qualitative findings


## Claim tuples

- H: Higher density and turbulence promote core fragmentation | E: Compare CDFs of core properties for single vs multiple cores | R: Multiples have higher mass, density, Mach number, R/R_Jeans, M/M_Jeans | F: Consistent with turbulent core fragmentation | **supported**
- H: Magnetic fields suppress fragmentation | E: Compare B and mass-to-flux ratio between groups | R: No significant difference | F: Magnetic field has limited influence on fragmentation | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Protostellar mass not included in core mass, so gravity may be underestimated  
  > "the mass calculated here does not include the protostellar mass, and thus the total mass within the core area may be underestimated" (3.2 Core Mass and Density)
- Caveat (inferred, ours): Small sample (15 multiples) and KS tests with marginal p-values
- Caveat (inferred, ours): B_pos has no inclination correction and DCF Q is assumed
- Caveat (inferred, ours): Heterogeneous resolutions (14.6", 23.4", 37") applied to cores of similar size
- Caveat (inferred, ours): Text inconsistencies, e.g. mass-to-flux ratio range 0.2-4.0 vs 0.3-6.8

## Reproducibility

- Data public (paper): JCMT, Herschel and VANDAM data are public/archival; Nobeyama cube from Tatematsu et al. 2008  
  > "We retrieved the JCMT POL-2 data of the Orion A molecular clouds taken under the projects M16BD001, M17BL011, M20AL006, M20AL018, M21BF005, and M21BF004 from the public archive." (2.2 JCMT Data)
- Products in archive: _not stated_
- Missing: Tabulated VANDAM catalog needed from Tobin et al. 2020
- Missing: Pol2map parameters
- Missing: Fitting code for hyperfine lines
- Data volume (inferred): Small: ALMA used only via published catalog; JCMT/Herschel maps ~ GB
- Score (inferred): 3/5, Equations and tables given but ALMA role is catalog only and several processing details are missing.
- Rediscovery candidate: no, ALMA data not reprocessed; recipe depends on several external datasets and incomplete parameters.

## Links

- Method: (cite: 2020ApJ...890..130T) (VANDAM protostar catalog)
- Method: (cite: 2008PASJ...60..407T) (N2H+ data)
- Companion: (cite: 2022ApJ...931..158L) (similar fragmentation study in complementary sample)
- Related: VANDAM
- Related: Herschel Gould Belt Survey

## Checks

```json
{
 "quotes": 42,
 "quotes_ok": 42,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2015.1.00041.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 32,
  "rate": 0.432
 },
 "evidence_ok": true
}
```

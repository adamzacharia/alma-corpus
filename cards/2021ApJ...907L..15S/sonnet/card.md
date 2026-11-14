# ALMA Survey of Orion Planck Galactic Cold Clumps (ALMASOP): Detection of Extremely High-density Compact Structure of Prestellar Cores and Multiple Substructures Within

`2021ApJ...907L..15S` | The Astrophysical Journal Letters 2021 | first author: Sahu, Dipen | arXiv: 2012.08737 | DOI: 10.3847/2041-8213/abd3aa

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Do prestellar cores in Orion host extremely dense compact central structures, and do these contain ~1000 au fragments that could seed multiple stellar systems?  
  > "we report the detection of high density (sub)structures on the thousand-au scale in a sample of dense prestellar cores" (abstract)
- Target **G205.46-14.56M3 (G205-M3)**: coordinates 05:46:05.99 -00:09:32.37 (J2000, ACA peak)  
  > "G205.46-14.56M3\* | 05:46:05.99  | -00:09:32.37" (Table 1); z/distance _not stated_; distance from _not stated_
- Target **G208.68-19.20N2**: coordinates 05:35:20.72 -05:00:54.09  
  > "G208.68-19.20N2   | 05:35:20.72  | -05:00:54.09" (Table 1); z/distance _not stated_; distance from _not stated_
- Target **G209.29-19.65S1**: coordinates 05:34:56.04 -05:46:05.28  
  > "G209.29-19.65S1   | 05:34:56.04  | -05:46:05.28" (Table 1); z/distance _not stated_; distance from _not stated_
- Target **G209.94-19.52N**: coordinates 05:36:11.39 -06:10:45.93  
  > "G209.94-19.52N    | 05:36:11.39  | -06:10:45.93" (Table 1); z/distance _not stated_; distance from _not stated_
- Target **G212.10-19.15N1**: coordinates 05:41:21.27 -07:52:27.01  
  > "G212.10-19.15N1   | 05:41:21.27  | -07:52:27.01" (Table 1); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2018.1.00302.S
- bands: Band 6 (1.3 mm)  
  > "resulting in a resolution ranging 0.34$''$ - 5.5$''$ in the 1.3 mm band" (2 Observations)
- frequencies and spectral setup: four spectral windows of 1.875 GHz; 1.129 MHz resolution (1.465-1.563 km/s); continuum at 233.0 and 216.6 GHz  
  > "The correlator was configured into four spectral windows with 1.875 GHz bandwidth, which provides a spectral resolution of 1.129 MHz" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: 12m C43-5 (TM1), 12m C43-2 (TM2), 7m ACA  
  > "12m C43-5 (TM1), 12m C43-2 (TM2), and 7m ACA" (2 Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.34" - 5.5" overall; ACA ~6", ACA+TM2 ~1.2", tapered 0.8"  
  > "an angular resolution of 0.8$''$ ( corresponding to a uv-taper of 150 k$\lambda$" (3.2 Substructures)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2018 October to 2019 January  
  > "during 2018 October to 2019 January" (2 Observations)
- pi or archival as stated: _not stated_
- Line: CO 2-1 (not stated)
- Line: N2D+ 3-2 (not stated)
- Other facility **JCMT SCUBA-2**: core-scale continuum and starless classification (via Yi2018)  
  > "all these starless cores were detected in the SCUBA-2 observations" (1 Introduction)
- Other facility **NRO 45m**: N2D+/N2H+ ratios, linewidths, temperatures (Kim2020)  
  > "seen by the NRO 45m telescope at a larger ($\sim 0.05$ pc to 0.1 pc) scale (cite: Kim2020)" (3.1)
- External data: N2D+ and N2H+ linewidths, gas temperatures 10.8-17.3 K, FWHMs for virial parameters  
  > "found from $\mathrm{N_2H^+}$ and $\mathrm{N_2D^+}$ line observations that under LTE conditions the gas temperatures of the five cores are in the range of 10.8-17.3 K" (4.2) [from (cite: Kim2020)]
- External data: Dust opacity kappa = 0.009 cm2/g at 1.3 mm  
  > "$\kappa$ = 0.009 cm$^2$ g$^{-1}$ at the observing wavelength for grains with thick icy mantles after 10$^5$ yr of coagulation" (3.1) [from (cite: Ossenkopf1994)]

## Processing

### Calibration

- pipeline or manual: observatory-delivered CASA pipeline calibration  
  > "The calibrated visibility data were obtained using CASA 5.4 (cite: McMullin2007) pipeline script as delivered by the observatory." (2 Observations)
- casa version: CASA 5.4  
  > "The calibrated visibility data were obtained using CASA 5.4" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean, automask on  
  > "generated through CASA’s tclean task with the ‘automask’ on, the hogbom deconvolver, and a robust weighting of 0.5" (2 Observations)
- deconvolver: hogbom  
  > "the hogbom deconvolver, and a robust weighting of 0.5" (2 Observations)
- weighting robust: robust = 0.5  
  > "the hogbom deconvolver, and a robust weighting of 0.5" (2 Observations)
- uv taper: 100-200 kλ tested; 150 kλ (~0.8") adopted  
  > "we applied a range of uv-tapering on the combined ALMA data from 100 k$\lambda$ to 200 k$\lambda$" (Dendrogram analysis)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: configurations imaged jointly  
  > "The visibility data for different configurations and executions corresponding to the 72 sources were then separated into continuum and spectral data, and imaged jointly." (2 Observations)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Remaining observational parameters and survey overview  
  > "The remaining details of the observational parameters are presented in (cite: Dutta2020)." (2 Observations) [from (cite: Dutta2020)]
- Outflow non-detection in CO and SiO  
  > "None of the five cores displays an outflow signature when observed in CO ($J$=2-1), its isotopologue lines and SiO ($J$=5-4) (cite: Dutta2020)." (3.1) [from (cite: Dutta2020)]

### Not stated but needed to reproduce (our reading)

- Continuum channel selection / line-free channels
- Image size, cell size, clean threshold and masks
- Per-source image rms and beams
- Distance to Orion used for au conversions
- Fitting region and tool for 2D Gaussian fits
- Primary-beam correction details
- Dendrogram image rms (sigma) value
- Aperture-flux procedure details

## Analysis recipe

1. **image continuum**: Joint tclean imaging of ACA, TM2, TM1 data; uv-tapering to vary resolution  
  > "Different $uv$–tapering of the visibility data has been employed to highlight the intricate features of the core seen at different angular scales." (3.2)
   - software: CASA
   - parameter: robust 0.5, hogbom, automask  
  > "the hogbom deconvolver, and a robust weighting of 0.5" (2 Observations)
   - fitting: _not stated_
   - validation: substructure checked via different tapers, slicing and dendrogram  
  > "This helps us identify the real and prominent substructures which are not related to imaging artifacts" (4.1.1)
2. **measure flux, size, mass, density**: 2D Gaussian fits; mass from dust emission at 10 K and 6.5 K; R_core = sqrt(major*minor)/2; N and n assuming sphere  
  > "The flux density of the observed structure toward each of the five cores can be estimated from 2-dimensional (2D) Gaussian fitting." (3.1)
   - parameter: T = 6.5-10 K  
  > "we assume the temperature of the compact component is at most 10 K and can go as low as 6.5 K" (3.1)
   - assumption: kappa = 0.009 cm2/g, gas-to-dust 100, mu_H2 = 2.8, spherical geometry  
  > "By assuming a spherical geometry, the gas volume density can also be calculated" (3.1)
   - fitting: 2D Gaussian; B1 and B2 fitted simultaneously  
  > "They were fitted simultaneously with 2D Gaussian fitting." (3.2)
   - validation: _not stated_
3. **identify substructures with dendrogram**: dendrogram with min_value=4σ, min_delta=2σ on 150 kλ-tapered combined image  
  > "We ran the dendrogram algorithm with min_value =4$\sigma$ (minimum intensity considered in the analysis) and min_delta= 2$\sigma$" (Dendrogram analysis)
   - software: astrodendro
   - fitting: _not stated_
   - validation: peak separation 1148 au vs Gaussian 1360±140 au  
  > "then the separation is given by 1360 $\pm$ 140 AU, considering the fitting uncertainties" (Dendrogram analysis)
4. **density profile from enclosed flux**: aperture fluxes at several radii give M ∝ r^1.2, density ∝ r^-1.8  
  > "we find the corresponding enclosed masses will scale as $r^{1.2}$, which hints at a density profile of $r^{-1.8}$" (4.1)
   - assumption: uniform temperature and dust properties  
  > "Assuming the gas temperature and dust property are uniform within these scales" (4.1)
   - fitting: _not stated_
   - validation: _not stated_
5. **stability and dynamics**: Jeans length, virial parameter, free-fall vs crossing time, binding condition  
  > "The fate of the substructures can be assessed from their virial parameters." (4.3)
   - parameter: c_s,eff = 0.247 km/s from N2D+ linewidth 0.4 km/s  
  > "The effective sound speed, $\mathrm{c_{s,eff} = (C_{ s}^2 + \sigma_{nt}^2)^{0.5}}$, is 0.247 km s$^{-1}$" (4.3)
   - assumption: a = 2±1; mu_p = 2.37 for Jeans length  
  > "$a = 2\pm1$ for a wide range of geometries and density structures" (4.3)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.4: pipeline calibration and tclean imaging  
  > "The calibrated visibility data were obtained using CASA 5.4" (2 Observations)
- **dendrogram algorithm (Rosolowsky2008)** : identify substructures B1 and B2  
  > "We ran the dendrogram algorithm with min_value =4$\sigma$" (Dendrogram analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| B1 mass | 0.38-0.84 | not stated | Msun | 2 | The masses of B1 and B2 are 0.38-0.84 M$_\odot$ and 0.08-0.19 M$_\odot$ |
| B2 mass | 0.08-0.19 | not stated | Msun | 2 | The masses of B1 and B2 are 0.38-0.84 M$_\odot$ and 0.08-0.19 M$_\odot$ |
| B1-B2 separation (dendrogram) | 1148 | not stated | au | 3 | is 1148 AU |
| B1-B2 separation (Gaussian fits) | 1360 | ±140 | au | 3 | the separation is given by 1360 $\pm$ 140 AU |
| Enclosed mass scaling | M ∝ r^1.2 (density ∝ r^-1.8) | not stated | dimensionless | 4 | enclosed masses will scale as $r^{1.2}$ |
| Virial parameter B1 | 0.36a to 0.79a | not stated | dimensionless | 5 | $\alpha_{\rm vir} = 0.36a$ to $0.79a$ for B1 |
| Virial parameter B2 | 0.74a to 1.76a | not stated | dimensionless | 5 | $\alpha_{\rm vir} = 0.74a$ to $1.76a$ for B2 |
| Crossing time | 2.3e4 | not stated | yr | 5 | $t_{cross} = 5.0$ yr $s/c_{\rm s, eff} = 2.3\ensuremath{\times 10^{4}}$ yr |
| Free-fall time | <7.06e3 | not stated | yr | 5 | $t_{\rm ff} < 7.06\ensuremath{\times 10^{3}}$ yr |

## Qualitative findings

- Five Orion starless cores have compact central regions ~2000 au with densities of several 1e7 cm-3, at least 10x L1544; only G205-M3 shows substructure.  
  > "The average and peak densities of the five prestellar cores are at least 10 times higher than that of the L1544 core" (4.1)

## Claim tuples

- H: Prestellar cores contain extremely dense compact central structures | E: ACA+TM2 1.3 mm continuum, 2D Gaussian fits | R: mean densities of several 1e7 cm-3, sizes ~2000 au, masses 0.30-6.89 Msun | F: Five chemically evolved, Jeans-unstable prestellar cores | **supported**
- H: Substructure exists at ~1000 au scale inside prestellar cores | E: uv-tapered combined images, dendrogram | R: G205-M3 resolved into B1 and B2 separated by ~1200 au | F: first detection of fragmentation in a prestellar core, likely forming a wide binary | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Gas temperature on small scales unknown; velocity resolution insufficient to measure line data at substructure scales.  
  > "We have neither gas nor dust temperature measurements on the observed angular scales." (3.1)
- Caveat (inferred, ours): Mass depends on assumed 6.5-10 K and a single kappa
- Caveat (inferred, ours): Substructures only visible in a narrow taper range, so imaging artifacts are not fully excluded
- Caveat (inferred, ours): Only one core fragments; small-number statistics

## Reproducibility

- Data public (paper): ALMA project 2018.1.00302.S acknowledged; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.00302.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging grid, cleaning thresholds, rms
- Missing: Distance assumption
- Missing: Dendrogram sigma
- Data volume (inferred): ~100s of GB for 72 fields across three arrays; subset for 5 fields is less
- Score (inferred): 3/5, Imaging recipe partly given and formulas explicit, but many imaging details and the distance are missing.
- Rediscovery candidate: yes, Archival data, simple Gaussian fit and mass formulas, numeric table.

## Links

- Method: (cite: Rosolowsky2008) (dendrogram method)
- Companion: (cite: Dutta2020) (ALMASOP overview)
- Companion: (cite: Kim2020) (NRO 45m line data)
- Related: ALMASOP
- Related: SCUBA-2 JCMT survey (Yi2018)

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 43,
  "rate": 0.5
 },
 "evidence_ok": true
}
```

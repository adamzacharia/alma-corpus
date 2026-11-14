# Molecular Gas Tracers in Young and Old Protoplanetary Disks

`2024ApJ...966...84A` | The Astrophysical Journal 2024 | first author: Anderson, Dana E. | arXiv: 2403.04715 | DOI: 10.3847/1538-4357/ad2fa2

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: How do disk-integrated fluxes of N2H+, HCO+, HCN and C18O relate to stellar and disk properties and to each other in a sample of 20 T Tauri disks?  
  > "We seek to determine how disk-integrated molecular fluxes relate to other observed disk properties and how they compare among different molecular species." (Introduction)
- Target **J1614, J1608, J1609 (Upper Sco)**: coordinates _not stated_; z/distance 142.00, 137.82, 137.40 pc (Table 1)  
  > "Available source distances are from (cite: Manara22-arxiv), which are derived by inverting their parallaxes from Gaia Data Release 3" (2.4 Data from the Literature); distance from Gaia DR3 parallaxes via Manara et al. 2022  
  > "Available source distances are from (cite: Manara22-arxiv), which are derived by inverting their parallaxes from Gaia Data Release 3" (2.4 Data from the Literature)
- Target **GG Tau A, RY Tau, UZ Tau E, IRAS 04302+2247 (Taurus; SMA)**: coordinates _not stated_; z/distance 141 pc (GG Tau A, RY Tau, UZ Tau E); 161 pc (IRAS 04302+2247)  
  > "For IRAS 04302+2247, the distance is taken to be 161 pc (cite: Garufi21)." (2.4 Data from the Literature); distance from Gaia DR3 via Manara22; Garufi21 for IRAS 04302  
  > "For IRAS 04302+2247, the distance is taken to be 161 pc (cite: Garufi21)." (2.4 Data from the Literature)

## Data provenance

- ALMA projects: 2015.1.01199.S, 2018.1.01623.S, 2019.1.01135.S
- bands: Band 6 (HCO+, HCN); Band 7 (N2H+, 13CO, C18O)  
  > "Band 6 observations of HCO$^+$ and HCN were taken on December 4, 2018. Band 7 observations of N$_2$H$^+$ were taken on December 8, 2018." (2.1 ALMA Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: ALMA 43–47 antennas; SMA compact configuration  
  > "Observations were taken with 43–47 antennas and maximum baselines of 740.4, 783.5, and 313.7–360.6 m, respectively." (2.1 ALMA Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: SMA 3–4 arcsec  
  > "providing an angular resolution of 3–4$''$" (2.2 SMA Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: ~23 min Band 6; 36 min Band 7 N2H+; 57 min Band 7 13CO/C18O per source; SMA 5–6 hr per source  
  > "The on-source integration time per source was about 23 min for Band 6, 36 min for Band 7 observations of N$_2$H$^+$ and 57 min for Band 7 observations of $^{13}$CO and C$^{18}$O." (2.1 ALMA Observations)
- observing dates: ALMA Dec 2018–Mar 2019; 2015.1.01199.S in 2016; SMA Dec 16–19, 2018  
  > "Data were taken between December 16–19, 2018" (2.2 SMA Observations)
- pi or archival as stated: PI Anderson (ALMA and SMA)  
  > "Using the Submillimeter Array (PI:Anderson, 2018B-S046)" (2.2 SMA Observations)
- Line: N2H+ J=3-2 (279.51176 GHz)
- Line: HCO+ J=3-2 (267.55763 GHz)
- Line: HCN J=3-2 (265.88643 GHz)
- Line: C18O J=3-2 (329.33055 GHz)
- Line: 13CO J=3-2 (330.587967 GHz)
- Other facility **SMA**: New N2H+, HCO+, HCN 3-2 and CO, 13CO, C18O 2-1 observations of four Taurus disks  
  > "we searched for N$_2$H$^+$, HCO$^+$, and HCN $J$ = 3–2 and CO, $^{13}$CO, and C$^{18}$O $J$ = 2–1 line emission from our sources" (2.2 SMA Observations)
- Other facility **Gaia DR3**: Parallax distances  
  > "derived by inverting their parallaxes from Gaia Data Release 3" (2.4 Data from the Literature)
- External data: Disk-integrated line fluxes for 13 other disks  
  > "Line fluxes are taken from the literature referenced in Table [2](#table2)." (2.4 Data from the Literature) [from references listed in Table 2]
- External data: Spectral types, stellar luminosities, masses, accretion rates, R_cont,68 and distances  
  > "are taken from (cite: Manara22-arxiv) when available." (2.4 Data from the Literature) [from (cite: Manara22-arxiv)]
- External data: Continuum fluxes for AS 209, IRAS 04302, TW Hya, V4046 Sgr  
  > "(cite: Andrews18_DSHARPI) for AS 209, (cite: vantHoff20) for IRAS 04302+2247, (cite: Tsukagoshi16) for TW Hya, and (cite: Kastner18) for V4046 Sgr" (2.4 Data from the Literature) [from Andrews18_DSHARPI; vantHoff20; Tsukagoshi16; Kastner18]
- External data: CO/H2 vs N2H+/C18O flux ratio relation from TW Hya model (CR ionization 1e-18 s-1)  
  > "we used the modeled relation between the N$_2$H$^+$ 3–2 / C$^{18}$O 2–1 flux ratio and the CO/H$_2$ abundance for the TW Hya model" (3.4 Disk Gas Masses) [from (cite: Trapman22)]
- Simulation/model as data: Miotello et al. fit functions from model grids used to derive CO-based gas masses  
  > "These masses were computed using the fits functions provided by (cite: Miotello16; Miotello17) from their large grid of models." (3.4 Disk Gas Masses)

## Processing

### Calibration

- pipeline or manual: Standard ALMA pipeline; SMA calibrated with MIR  
  > "The data were calibrated using the standard ALMA pipeline and analyzed with the Common Astronomy Software Applications (CASA) package" (2.1 ALMA Observations)
- casa version: Archive-specified version for restoring; CASA 6.4.0 for imaging and analysis  
  > "Otherwise, imaging and analysis were performed using CASA version 6.4.0." (2.1 ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1427-4206 (Band 6), J1517-2422 (Band 7); SMA: Uranus  
  > "Pipeline flux and bandpass calibrators were J1427-4206 in Band 6 and J1517-2422 in Band 7." (2.1 ALMA Observations)
- flux scale uncertainty: 10% assumed  
  > "added in quadrature with 10% of the integrated line flux representing the assumed uncertainty for the flux amplitude calibration" (2.3 Spectral Line Analysis)
- self calibration: Tested, not applied  
  > "Self-calibration was tested but ultimately not applied to the data because it did not produce improvements in signal-to-noise that were significant for this analysis." (2.1 ALMA Observations)

### Imaging

- task: tclean  
  > "Images are generated by CASA’s $tclean$ using Briggs weighting with a robust parameter of 0.5" (2.3 Spectral Line Analysis)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "Briggs weighting with a robust parameter of 0.5" (2.3 Spectral Line Analysis)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Empirical mask from 1.5x-beam-smoothed dirty cube, >3 sigma, largest clump per channel; 13CO or CO masks for weak lines  
  > "we selected pixels with flux densities $>$3$\times$ the standard deviation of a sample of off-source pixels." (2.3 Spectral Line Analysis)
- multiscale scales: _not stated_
- continuum subtraction: CASA uvcontsub on line windows  
  > "Continuum subtraction was performed on the spectral line windows using CASA’s $uvcontsub$." (2.3 Spectral Line Analysis)
- line free channels: _not stated_
- primary beam correction: impbcor applied before flux and noise estimates  
  > "the primary beam correction using CASA’s $impbcor$ was applied to the image before the noise and line flux estimates were made." (2.3 Spectral Line Analysis)
- array combination: _not stated_
- smoothing: Dirty cube convolved with Gaussian 1.5x original beam (ALMA only) for mask generation  
  > "The dirty image cube was smoothed via convolution with a Gaussian beam with dimensions 1.5$\times$ the original beam size." (2.3 Spectral Line Analysis)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- N2H+ observations of J1608 and J1609 previously reported  
  > "previously reported by (cite: Anderson19)" (2.1 ALMA Observations) [from (cite: Anderson19)]
- Dust mass formula and opacity  
  > "Dust masses (Table [1](#table1)) are computed as described in (cite: Manara22-arxiv) with the formula used by (cite: Ansdell16) from (cite: Hildebrand83)" (2.4 Data from the Literature) [from Manara22; Ansdell16; Hildebrand83]
- Linear regression method with errors and non-detections  
  > "Using the Python linear regression tool `linmix`[^3] based on the method of (cite: Kelly07)" (3.2 Searching for Line Flux Trends) [from (cite: Kelly07)]
- Gas masses from CO isotopologue fit functions  
  > "These masses were computed using the fits functions provided by (cite: Miotello16; Miotello17)" (3.4 Disk Gas Masses) [from Miotello16; Miotello17]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for continuum subtraction and noise
- Exact tclean threshold, cell size, image size and mask details
- linmix settings (chains, priors, convergence)
- Exact literature flux values' method per source and how asterisked 2-1 fluxes were scaled in each case
- Version of ALMA pipeline
- Specific sigma threshold or line-free regions for 30 noise apertures
- Manual flags in ALMA data

## Analysis recipe

1. **Image line cubes**: uvcontsub then tclean with Briggs weighting and empirical masks, 1 km/s channels  
  > "channel widths of 1 km s$^{-1}$" (2.3 Spectral Line Analysis)
   - software: CASA, uvcontsub, tclean
   - parameter: robust = 0.5; threshold ~3x sigma of line-free channels  
  > "a threshold of roughly 3$\times$ the standard deviation of the flux density in a sample of line-free channels" (2.3 Spectral Line Analysis)
   - fitting: _not stated_
   - validation: Compared empirical dirty-image masks with clean-image masks  
  > "the empirical masks based on the dirty images do not significantly differ from those derived from the clean images" (2.3 Spectral Line Analysis)
2. **Extract disk-integrated line fluxes and uncertainties**: Multiply image by mask (immath), spectrum via specflux, integrate over line velocity range; noise from 30 line-free regions plus 10% calibration; upper limits at 3x uncertainty  
  > "Upper limits are estimated as three times this uncertainty value with fluxes above this threshold being considered detections." (2.3 Spectral Line Analysis)
   - software: CASA immath, specflux, impbcor
   - parameter: 30 line-free regions; 10% flux calibration uncertainty  
  > "Noise estimates are determined by applying each line’s empirical mask to 30 different line-free regions across the image cube." (2.3 Spectral Line Analysis)
   - fitting: _not stated_
   - validation: _not stated_
3. **Compile literature sample and dust masses**: Optically thin isothermal dust mass formula; scale fluxes to 160 pc; 2-1 13CO/C18O fluxes multiplied by 2 to approximate 3-2  
  > "they are multiplied by a factor of 2$\times$ as a conversion to approximate the $J$ = 3–2 fluxes." (2.4 Data from the Literature)
   - parameter: kappa = 2.3(nu/230 GHz) cm2/g; T_dust = 20 K  
  > "$\kappa_{\nu}$ = 2.3($\nu$/230 GHz) cm$^{2}$ g$^{-1}$ and assuming a dust temperature of 20 K" (2.4 Data from the Literature)
   - assumption: Optically thin, isothermal dust emission  
  > "This assumes optically-thin, isothermal dust emission at (sub-)millimeter wavelengths." (2.4 Data from the Literature)
   - fitting: _not stated_
   - validation: 2x factor based on observed C18O 3-2/2-1 ratios of ~1-3 in three sources  
  > "These values are in the range of $\sim$1–3, not well described by an optically-thin LTE analysis." (2.4 Data from the Literature)
4. **Search for correlations**: Bayesian linear regression with linmix handling errors and non-detections; median correlation coefficient with 1 sigma  
  > "We report the median correlation coefficient from the `linmix` runs with one standard deviation as the listed uncertainties." (3.2 Searching for Line Flux Trends)
   - software: linmix
   - fitting: MCMC sampling to approximate posterior (Kelly 2007); priors not stated  
  > "The method uses Markov chain Monte Carlo (MCMC) sampling to approximate the posterior distribution." (3.2 Searching for Line Flux Trends)
   - validation: _not stated_
5. **Estimate disk gas masses**: Dust-based (100 x Mdust), CO-based via Miotello fit functions, and CO-based scaled by CO/H2 from N2H+/C18O ratio using Trapman22 TW Hya model  
  > "The top panel shows gas masses as equal to 100$\times$ M$_{dust}$." (3.4 Disk Gas Masses)
   - assumption: CO/H2 ~1e-4 baseline; gas/dust = 100  
  > "These values assume a CO/H$_2$ abundance of $\sim$10$^{-4}$." (3.4 Disk Gas Masses)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 6.4.0: Calibration restoration, imaging and analysis  
  > "imaging and analysis were performed using CASA version 6.4.0." (2.1 ALMA Observations)
- **MIR** : SMA phase and amplitude calibration  
  > "All data were phase- and amplitude-calibrated using the MIR software package" (2.2 SMA Observations)
- **linmix** : Linear regression with errors and upper limits  
  > "Using the Python linear regression tool `linmix`" (3.2 Searching for Line Flux Trends)
- **Astropy** : listed in software section  
  > "Astropy (cite: astropy:2013; astropy:2018), CASA (cite: 2007ASPC..376..127M), linmix" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| N2H+ and HCO+ detected in J1608 (flux) | N2H+ 18.9; HCO+ 62.8 | ±2.1; ±6.4 | mJy km/s | 2 | 62.8$\pm$6.4(1) |
| HCO+ flux of J1614 | 78.2 | ±8.1 | mJy km/s | 2 | 78.2$\pm$8.1(1) |
| Gas mass increase factor from CO/H2 scaling for subset | ~5–135 | not stated | dimensionless | 5 | the gas masses for a subset of our sample were increased by factors of $\sim$5–135$\times$ relative to the CO-based values |
| HCO+ fraction of total molecular flux | 35–55% typical; >80% in J1614 | not stated | percent | 4 | HCO$^+$ makes up around 35–55% of the total molecular flux. |

## Qualitative findings

- Line fluxes of all four species increase with dust mass and continuum radius with large scatter  
  > "Overall, we find positive correlations between multiple line fluxes and the disk dust mass and radius." (abstract)
- Strong positive correlations between fluxes of different species, but relative fluxes vary even within one region  
  > "These differences occur even within a single star-forming region." (abstract)

## Claim tuples

- H: Do disk-integrated molecular line fluxes scale with dust mass and disk size? | E: linmix regression of fluxes versus Mdust and R_cont,68 across 20 disks | R: Positive median correlations, tentative to moderate, with upper limits affecting significance | F: Fluxes generally increase with dust mass and radius | **supported**
- H: Are fluxes of different molecular species correlated? | E: Pairwise linmix correlations | R: At least tentative positive correlations for all pairs; strong for most | F: Species fluxes are positively correlated, possibly via physical factors or optical depth | **supported**
- H: Do disks in the same region have similar relative molecular fluxes? | E: Compared flux fractions per disk | R: Different fractions within Lupus and Upper Sco | F: Range of chemical compositions coexists in one region | **supported**
- H: Do age or birth environment trends appear? | E: Compared younger and older disks | R: No obvious distinctions; sample biased | F: Inconclusive | **partially**

## Reasoning

- Why this data: Targets chosen from Upper Sco ALMA survey and Taurus IRAM survey with strong CO emission  
  > "Three sources with detected CO emission and relatively high dust masses were selected from the ALMA survey of Upper Sco" (2.1 ALMA Observations)
- Why this method: _not stated_
- Alternative: Self-calibration tested but not applied  
  > "Self-calibration was tested but ultimately not applied to the data" (2.1 ALMA Observations)
- How they decided it was enough: _not stated_
- Limitation (authors): Sample is heterogeneous with selection biases toward bright disks and non-uniform sensitivity  
  > "because the sample is compiled from different observing programs, the sensitivity is not the same for all sources or molecular lines." (4.1 Comparison within our sample)
- Limitation (authors): Optically thick dust or lines may affect trends  
  > "The sub-mm dust emission may in fact be optically thick" (2.4 Data from the Literature)
- Caveat (inferred, ours): Small, heterogeneous sample with many upper limits; correlations partly driven by distance-scaled brightness
- Caveat (inferred, ours): 2-1 to 3-2 factor of 2 is ad hoc
- Caveat (inferred, ours): Correlations in flux may arise from common disk size/distance scaling
- Caveat (inferred, ours): Gas-mass rescaling relies on a single TW Hya model

## Reproducibility

- Data public (paper): ALMA projects cited; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.01199.S, ADS/JAO.ALMA#2018.1.01623.S, and" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Literature line flux values need collecting from many papers
- Missing: SMA data access not stated
- Missing: Exact tclean parameters and line-free channels
- Data volume (inferred): ~50-100 GB for the ALMA datasets
- Score (inferred): 3/5, New flux extraction is described in reasonable detail but the sample is mostly literature-derived and several settings are unstated.
- Rediscovery candidate: no, Main results depend on many literature fluxes and correlation coefficients are in figures, not tables.

## Links

- Method: (cite: Kelly07) (linmix regression method)
- Method: (cite: Anderson19) (Earlier N2H+ observations and analysis)
- Companion: (cite: Anderson22) (Lupus sample of seven disks analysed earlier)
- Related: AGE-PRO
- Related: ALMA DECO

## Checks

```json
{
 "quotes": 74,
 "quotes_ok": 74,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2019.1.01135.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 57,
  "rate": 0.663
 },
 "evidence_ok": true
}
```

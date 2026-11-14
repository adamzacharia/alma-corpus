# An Evolutionary Study of Volatile Chemistry in Protoplanetary Disks

`2020ApJ...898...97B` | The Astrophysical Journal 2020 | first author: Bergner, Jennifer B. | arXiv: 2006.12584 | DOI: 10.3847/1538-4357/ab9e71

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry, star_formation
- Question: How does volatile chemistry (CO depletion, C2H/HCN/C18O relations, HCN D and 15N fractionation) evolve from Class 0/I to Class II disks?  
  > "In this work, we present an evolutionary study of volatile chemistry in Class 0, I, and II sources." (Introduction)
- Target **Ser-emb 1, 7, 8, 15, 17 (Serpens Class 0/I)**: coordinates Ser-emb 1: 18:29:09.1 +0:31:30.9 (J2000); others in Table 2  
  > "A distance of 436 pc is assumed for all Serpens sources (cite: Ortiz2018)." (Table 2 notes); "| Ser-emb 1$^*$  | Serpens     | 18:29:09.1   | 0:31:30.9    | 0              | 39 \[2\]      | 3.1 \[0.05\]               | 4.1 \[0.3\]                |" (Table 2); z/distance 436 pc  
  > "A distance of 436 pc is assumed for all Serpens sources (cite: Ortiz2018)." (Table 2 notes); "| Ser-emb 1$^*$  | Serpens     | 18:29:09.1   | 0:31:30.9    | 0              | 39 \[2\]      | 3.1 \[0.05\]               | 4.1 \[0.3\]                |" (Table 2); distance from Ortiz-Leon et al. 2018  
  > "A distance of 436 pc is assumed for all Serpens sources (cite: Ortiz2018)." (Table 2 notes); "| Ser-emb 1$^*$  | Serpens     | 18:29:09.1   | 0:31:30.9    | 0              | 39 \[2\]      | 3.1 \[0.05\]               | 4.1 \[0.3\]                |" (Table 2)
- Target **Class II disks (CI Tau, DM Tau, DO Tau, HD 143006, J1604, J1609, J1612, J1614, LkCa 15, MWC 480, AS 209, HD 163296, IM Lup, V4046 Sgr)**: coordinates see Table 2  
  > "$^d$ From *Gaia* Data Release 2 (cite: Gaia2018)" (Table 2 notes); z/distance 72.4-166.1 pc  
  > "$^d$ From *Gaia* Data Release 2 (cite: Gaia2018)" (Table 2 notes); distance from Gaia DR2  
  > "$^d$ From *Gaia* Data Release 2 (cite: Gaia2018)" (Table 2 notes)

## Data provenance

- ALMA projects: 2015.1.00964.S, 2016.1.00627.S
- bands: Band 6; two spectral setups (217–233 GHz and 243–262 GHz)  
  > "Two Band 6 spectral setups (217–233 GHz and 243–262 GHz) were covered." (2.1 Protostellar (Class 0/I) disk candidates)
- frequencies and spectral setup: channel width 122 kHz, ~0.14–0.17 km/s  
  > "All spectral windows have a channel width of 122 kHz, corresponding to $\sim$0.14–0.17 km/s across the range of frequencies." (2.1 Protostellar (Class 0/I) disk candidates)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.5"  
  > "the spatial resolution of these observations ($\sim$0.5$\ensuremath{''}$; Table [3](#tab:class0i_fluxes))" (3.1.1 Line detections and velocity structures)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: Class 0/I: May–June 2016; Class II: May–June 2016 (2015.1.00964) and December 2016 (2016.1.00627)  
  > "Observations took place from May–June of 2016 for project 2015.1.00964S and in December 2016 for project 2016.1.00627.S." (2.2 Class II disks)
- pi or archival as stated: PI K. Öberg  
  > "(PI: K. Öberg)" (Observations)
- Line: C18O 2–1 (219.560 GHz)
- Line: DCN 3–2 (217.239 GHz)
- Line: HC15N 3–2 (258.157 GHz)
- Line: H13CN 3–2 (259.012 GHz)
- Line: HCN 3–2 (265.886 GHz)
- Line: C2H N=3–2, J=5/2–5/2, F=3–3 (262.209 GHz)
- Other facility **SMA**: HCN fluxes for some Class II disks used in Bergner et al. 2019b (replaced here by H13CN-based values)  
  > "we do not have ALMA observations of HCN 3–2, so we previously used HCN fluxes measured with the SMA for these disks." (4.2 Class II column densities)
- External data: Class 0/I source properties (Tbol, Menv, Lbol, classes)  
  > "Class 0/I source properties are taken from (cite: Enoch2009) and (cite: Enoch2011)." (Table 2 notes) [from (cite: Enoch2009); (cite: Enoch2011)]
- External data: Class II stellar properties and ages  
  > "Stellar properties are taken from (cite: Pegues2020)" (Table 2 notes) [from (cite: Pegues2020)]
- External data: Class II C2H, HCN, C18O observations/fluxes and mean optical depths (C2H 2.1±0.4, HCN 5.8±1.8)  
  > "Column density estimates for C$_2$H, HCN, and C$^{18}$O in the Class II sources are derived using the observations presented in (cite: Bergner2019b), with a few exceptions." (4.2 Class II column densities) [from (cite: Bergner2019b)]
- External data: Local ISM 12C/13C ratio of 68±15  
  > "we convert from H$^{13}$CN to HCN column densities using the local ISM $^{12}$C/$^{13}$C ratio of 68$\pm$15 (cite: Milam2005)." (4.3) [from (cite: Milam2005)]
- External data: 16O/18O ratio of 560±25  
  > "assuming the local ISM $^{16}$O/$^{18}$O ratio of 560$\pm$25 (cite: Wilson1994)" (4.3) [from (cite: Wilson1994)]
- External data: Spectroscopic line parameters  
  > "All line parameters are taken from the CDMS catalog (cite: Muller2001; Muller2005)" (Table 4 notes) [from (cite: Muller2001; Muller2005)]
- External data: Class II disk inclinations and position angles  
  > "References: \[1\] (cite: Huang2017), \[2\] (cite: Long2019), \[3\] (cite: Teague2015)" (Table 8 notes) [from Huang2017, Long2019, Teague2015, Benisty2018, Dong2017, Barenfeld2017]
- External data: Literature HCN isotopologue ratios for comparison  
  > "the Class II disks AS 209, LkCa 15, MWC 480, HD 163296, V4046 Sgr, (cite: Guzman2017) and TW Hya (cite: Hily-Blant2019)" (5.3) [from Guzman2017, Huang2017, Hily-Blant2019, and others]

## Processing

### Calibration

- pipeline or manual: Pipeline calibration followed by phase self-calibration  
  > "Following pipeline calibration of the ALMA data, we performed self-calibration using the combined continuum emission from spectral windows within a given sideband." (2.3 Data reduction)
- casa version: CASA 5.5.0 (imaging)  
  > "Calibrated and continuum-subtracted data were CLEANed to a 4$\sigma$ noise threshold in CASA 5.5.0" (2.3 Data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10% absolute calibration uncertainty  
  > "added in quadrature with a 10% calibration uncertainty, i.e. the estimated absolute calibration uncertainty for ALMA (cite: Remijan2020)" (3.1.7 Spectral extraction)
- self calibration: Up to two rounds of phase self-cal; solints 12.1–42.35 s (Class 0), 6.05–12.1 s (Class I), 60.5–84.7 s (Upper Sco), 6.05–48.4 s (other Class II)  
  > "Depending on the continuum brightness, up to two rounds of phase self-calibration were performed." (2.3 Data reduction)

### Imaging

- task: tclean with auto-multithresh, Briggs weighting, CLEAN to 4σ  
  > "using Briggs weighting and the automasking task `auto-multithresh` in `tclean`." (2.3 Data reduction)
- deconvolver: _not stated_
- weighting robust: Class 0/I: 0.5 (C2H: 2.0); Class II: 2.0 except HD 143006 (1.0) and J1604 (0.0)  
  > "A robust factor of 2.0 was used for all disks except for HD 143006 and J1604, whose bright emission permitted robust factors of 1.0 and 0.0 respectively." (2.3 Data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: auto-multithresh: sidelobethreshold 2.0, noisethreshold 4.5, minbeamfrac 0.3, negativethreshold 15.0, lownoisethreshold 1.5  
  > "sidelobethreshold = 2.0, noisethreshold = 4.5, minbeamfrac = 0.3, negativethreshold = 15.0, lownoisethreshold = 1.5" (2.3 Data reduction)
- multiscale scales: _not stated_
- continuum subtraction: in the uv plane  
  > "The self-calibration solutions were applied to the spectral line data following continuum subtraction in the uv plane." (2.3 Data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: HCN/H13CN images smoothed to DCN resolution with imsmooth (Class II)  
  > "The CASA task `imsmooth` is used to smooth the HCN and H$^{13}$CN images to the same resolution as the DCN images." (5.2 Class II sources)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Full Class 0/I observational details  
  > "Full observational details can be found in (cite: Bergner2019c)." (2.1) [from (cite: Bergner2019c)]
- Class II sample description  
  > "The full Class II disk sample is described in (cite: Bergner2019b)" (2.2 Class II disks) [from (cite: Bergner2019b)]
- Keplerian masking technique  
  > "A full description of the masking technique can be found in (cite: Bergner2018) and (cite: Pegues2020)." (3.2 Class II sources) [from (cite: Bergner2018); (cite: Pegues2020)]
- Optical depth correction  
  > "We therefore adjust the Class II HCN and C$_2$H column densities following (cite: Goldsmith1999)" (4.2) [from (cite: Goldsmith1999)]
- Disk mass from continuum: dust opacity, dust-to-gas, 20 K  
  > "Following (cite: Hildebrand1983) and (cite: Andrews2005), we convert the 260 GHz continuum flux to a disk mass" (4.3) [from (cite: Hildebrand1983); (cite: Andrews2005); (cite: Beckwith1990)]

### Not stated but needed to reproduce (our reading)

- Which pipeline version was used for the initial calibration, and flux/bandpass/phase calibrators
- Line-free channels used for continuum subtraction
- Exact self-calibration solint per source/sideband
- Image size and cell size
- Which sources have which gaussian components in spectral fits and emcee priors, walkers, steps
- Maximum recoverable scale and array configurations
- Details of Keplerian mask radii per source
- Precise C18O/H abundance derivation for age plot (extraction circle fluxes)

## Analysis recipe

1. **Self-calibrate and image line cubes**: Phase self-calibration on continuum, applied to uv-continuum-subtracted data, tclean with auto-multithresh  
  > "Calibrated and continuum-subtracted data were CLEANed to a 4$\sigma$ noise threshold in CASA 5.5.0" (2.3 Data reduction)
   - software: CASA
   - parameter: Channel width 0.25 km/s (Class 0/I), 0.5 km/s (Class II)  
  > "For the Class II sources, imaging was performed with a channel width of 0.5 km s$^{-1}$." (2.3 Data reduction)
   - fitting: _not stated_
   - validation: Automasking compared with hand-masked images for select lines  
  > "Automasking results were verified by comparing to hand-masked images for select lines" (2.3 Data reduction)
2. **Extract Class 0/I spectra and fit line fluxes**: Extract spectra within DCN emission mask (6σ; 8σ for Ser-emb 1); fit sum of Gaussian components; take 'medium' component as disk flux  
  > "We fit each line as a sum of Gaussians corresponding to different possible velocity components" (3.1.7 Spectral extraction)
   - software: emcee
   - parameter: medium width [0.1,3] km/s; absorption [0.1,1]; broad [2,10]; narrow [0.1,0.4]  
  > "a ‘medium’ component (Gaussian width constrained to \[0.1, 3\] km/s) is included for all lines" (3.1.7 Spectral extraction)
   - assumption: Narrow components arise from the cloud; broad components from outflows  
  > "We assume that narrow velocity components (emission or absorption, with Gaussian widths $\lesssim$0.5 km/s) arise from the cloud." (3.1.7 Spectral extraction)
   - fitting: emcee MCMC sampling of posterior of Gaussian parameters; priors not stated  
  > "We use the MCMC package `emcee` (cite: Foreman2013) to sample posterior distributions of the Gaussian fit parameters." (3.1.7 Spectral extraction)
   - validation: _not stated_
3. **Measure Class II fluxes**: Keplerian-masked moment zero maps; sum flux; uncertainty from 200 emission-free synthetic cubes plus 10% calibration  
  > "We also apply the same Keplerian mask to 200 synthetic image cubes of randomly drawn emission-free channels neighboring the target line." (3.2 Class II sources)
   - parameter: Detection: flux >3σ and >3σ emission in moment zero map  
  > "We consider a line to be detected if the measured flux is $>$3$\sigma$ and if emission $>$3$\sigma$ is present in the moment zero map." (3.2 Class II sources)
   - fitting: _not stated_
   - validation: Compared H13CN/HC15N fluxes with Guzman et al. 2017  
  > "We obtain H$^{13}$CN fluxes a factor of $\sim$1.3 and 1.7 higher compared to (cite: Guzman2017) for MWC 480 and LkCa 15, respectively" (3.2 Class II sources)
4. **Derive column densities**: Optically thin LTE formula with Trot=20, 30, 50 K (30 K fiducial); Class II HCN and C2H opacity-corrected  
  > "we calculate column densities adopting rotational temperatures of 20, 30, and 50 K." (4.1 Class 0/I column densities)
   - parameter: tau_blend(C2H)=1.1±0.2; tau(HCN)=5.8±1.8  
  > "this results in a $\tau_{\rm{blend}}$ of 1.1$\pm$0.2 for use in Equation" (4.2)
   - assumption: Emitting area = mask size; Trot unknown  
  > "The rotational temperatures are not known and cannot be determined from these data alone" (4.1)
   - fitting: _not stated_
   - validation: Tested T=100 K: columns rise ~2x  
  > "If we instead adopt an excitation temperature of 100 K in the Class 0/I sources, this increases the column densities of all molecules by a factor of $\sim$2." (4.5 Abundance caveats)
5. **Derive H2 columns and abundances**: Continuum flux to dust mass with kappa=2.62 cm2/g, dust-to-gas 1:100, T=20 K, mu=2.37; divide by mask area  
  > "We adopt a $\kappa_v$ of 2.62 cm$^2$ g$^{-1}$ following the power-law scaling of (cite: Beckwith1990) with a power-law index $\beta$=1." (4.3)
   - assumption: Uniform dust temperature 20 K; dust-to-gas 1:100  
  > "We assume a dust-to-gas ratio of 1:100 and a uniform dust temperature of 20 K (cite: Andrews2005)." (4.3)
   - fitting: _not stated_
   - validation: Sensitivity to kappa and T discussed  
  > "Adopted dust temperatures of 15 K or 30 K instead of 20 K results in $\sim$40–50% variations in the derived dust masses" (4.5)
6. **Correlations and C18O abundance vs age**: Spearman correlation on abundances (excluding upper limits); C18O/H vs age with apparent ISM abundance for tau=8 and 40  
  > "We use the `scipy.stats.spearmanr` module to calculate Spearman $\rho$ coefficients and their p values." (4.3)
   - software: scipy
   - parameter: p<5% significant; ages 0.1±0.1 Myr (Class 0), 0.35±0.15 Myr (Class I)  
  > "we adopt ages of 0.1$\pm$0.1 and 0.35$\pm$0.15 Myr, respectively." (4.4)
   - assumption: ISM C18O abundance ~2.5e-7 (CO/H=1.4e-4, 16O/18O=560)  
  > "ISM abundance of $\sim$2.5$\times$10$^{-7}$ (assuming CO/H = 1.4$\times$10$^{-4}$ and $^{16}$O/$^{18}$O = 560)" (4.4)
   - fitting: _not stated_
   - validation: Compared depletion factors with Zhang et al. 2019 modeling  
  > "We recover similar CO depletion factors for HD 163296 and DM Tau in the $\tau$=40 scenario" (4.4)
7. **HCN isotopologue ratios**: Column-density ratios HCN/HC15N and HCN/DCN at 30 K; H13CN converted with 12C/13C=68; Class II fluxes from common 3σ mask on smoothed images; HCN opacity corrected  
  > "We define the extraction mask as pixels with $>$3$\sigma$ emission of both the major and minor isotopologue" (5.2)
   - software: CASA imsmooth
   - assumption: Isotopologues co-spatial with same Trot  
  > "this treatment assumes that the HCN isotopologues emit co-spatially" (5.1)
   - fitting: _not stated_
   - validation: Compared with Huang 2017 and Guzman 2017  
  > "Both the opacity-uncorrected and corrected values that we find are consistent with this range." (5.2)

## Software

- **CASA** 5.5.0: calibration, tclean imaging, imsmooth  
  > "CLEANed to a 4$\sigma$ noise threshold in CASA 5.5.0" (2.3 Data reduction)
- **emcee** : MCMC sampling of Gaussian line fit parameters  
  > "We use the MCMC package `emcee` (cite: Foreman2013)" (3.1.7)
- **scipy.stats.spearmanr** : Spearman correlation coefficients  
  > "We use the `scipy.stats.spearmanr` module to calculate Spearman $\rho$ coefficients and their p values." (4.3)
- **NumPy, Matplotlib, Astropy, SciPy** : general analysis and plotting  
  > "NumPy (cite: VanDerWalt2011), Matplotlib (cite: Hunter2007), Astropy (cite: Astropy2013), SciPy (cite: SciPy2020)," (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HCN/HC15N range, Class 0/I | 88 (Ser-emb 17) to 287 (Ser-emb 1) | not stated | dimensionless | 7 | HCN/HC$^{15}$N ratios range from 88 in Ser-emb 17 to 287 in Ser-emb 1. |
| HCN/DCN range, Class 0/I | 52 (Ser-emb 15) to 87 (Ser-emb 8) | not stated | dimensionless | 7 | ranging only from 52 in Ser-emb 15 to 87 in Ser-emb 8 |
| HCN/HC15N in LkCa 15 and MWC 480 | 100 and 106 | [31] and [29] | dimensionless | 7 | In LkCa 15 and MWC 480, the HCN/HC$^{15}$N ratios of 100 and 106, respectively |
| HCN/DCN Class II (tau-corrected) | 54–75 (HD 143006, J1604, J1609); ~10 optically thin | not stated | dimensionless | 7 | the HCN/DCN ratio is $\sim$10 assuming HCN is optically thin, or 54–75 for an HCN opacity of 5.8 |
| C18O column density Ser-emb 1 (30 K) | 6.8e15 | ±1.7e15 | cm^-2 | 4 | / Ser-emb 1  / 6.8 $\pm$ 1.7 $\times$10$^{15}$ \[-0.8, +2.3\]                    / |
| Class I CO depletion relative to ISM (tau=8) | ~1 order of magnitude | not stated | dimensionless | 6 | even assuming $\tau$=8, the Class I C$^{18}$O/H abundances are depleted in CO relative to ISM levels by about an order of magnitude. |
| Class II CO depletion | factors of a few up to 100 | not stated | dimensionless | 6 | The Class II sources are likely depleted in CO by factors of a few up to 100 |
| Mean optical depths (adopted from prior work) | C2H blended 1.1±0.2; HCN 5.8±1.8 | as stated | dimensionless | 4 | results in a $\tau_{\rm{blend}}$ of 1.1$\pm$0.2 |

## Qualitative findings

- Compact line emission in Class 0/I sources rotates perpendicular to outflows; DCN best traces disk-like structure  
  > "DCN 3–2 emission seems to reliably trace the compact disk-like structures of the embedded sources, especially notable in Ser-emb 15." (Conclusions)
- HCN and C2H abundances positively correlated in Class II; HCN and C18O correlated in Class 0/I  
  > "Statistically significant positive correlations are seen between the HCN and C$_2$H abundances in the Class II sources, and between the HCN and C$^{18}$O abundances in the Class 0/I sources." (4.3)

## Claim tuples

- H: CO is depleted early in the disk lifetime | E: C18O/H abundances across Class 0, I, II, with optical-depth benchmarks | R: Class 0 consistent with ISM (tau=8), Class I ~10x depleted, Class II similar depletion | F: CO depletion occurs on ~0.5–1 Myr timescale, largely set in embedded stages | **partially**
- H: CO depletion enhances C2H and HCN formation | E: Abundance correlations among C2H, HCN, C18O | R: No anti-correlation of C18O with C2H or HCN | F: Gas already high C/O; further depletion may limit carbon supply | **refuted**
- H: 15N fractionation of HCN evolves with stage | E: HCN/HC15N vs Tbol across Class 0/I and Class II | R: Ratio ~90–290 in Class 0/I, decreasing with Tbol; Class II ~80–150 | F: Photodissociation-driven fractionation increases as the envelope clears | **supported**
- H: Deuterium fractionation of HCN evolves with stage | E: HCN/DCN across sample | R: Flat ~50–90 in Class 0/I; slight decrease to young Class II, tentative increase >3 Myr | F: D fractionation temperature-driven, no strong trend in protostellar stage | **partially**
- H: Ices sublimation affects HCN in protostellar cores | E: Compare hot corino vs non-hot corino sources | R: HCN isotopologue columns systematically higher in hot corino sources | F: HCN-C18O correlation likely from sublimation of infalling ices | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: DCN used to define extraction region because it most consistently traces compact disk-like emission  
  > "DCN seems to most consistently trace compact disk-like emission." (3.1.7)
- Alternative: Used H13CN rather than HCN for column densities in some Class II disks because HCN is optically thick; 13CO instead of CO  
  > "we opt to solve for the HCN column density using H$^{13}$CN as a proxy since HCN suffers from optical depth effects" (4.2)
- How they decided it was enough: _not stated_
- Limitation (authors): C18O optical depth is a major uncertainty; rare isotopologue needed  
  > "We emphasize that the C$^{18}$O optical depth is a major uncertainty in assessing both the absolute C$^{18}$O/H abundances and the relative trends between evolutionary stages." (4.4)
- Limitation (authors): Small sample: two Class 0 and three Class I sources  
  > "our sample contains just two Class 0 and three Class I sources" (4.3)
- Limitation (authors): Resolution too low to identify Keplerian disks  
  > "is not high enough to definitively identify the presence of Keplerian disks" (3.1.1)
- Caveat (inferred, ours): Rotational temperature, emitting area and dust opacity assumed uniform; abundances could shift by factors of several
- Caveat (inferred, ours): Optical-depth benchmarks for C18O chosen from literature, making depletion conclusions model-dependent
- Caveat (inferred, ours): Envelope contamination in Class 0 sources
- Caveat (inferred, ours): Statistics from five embedded sources; Spearman tests exclude upper limits

## Reproducibility

- Data public (paper): Project codes given; ALMA archive data (no explicit statement)  
  > "This paper makes use of ALMA data, project codes 2015.1.00964.S and 2016.1.00627.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Calibrator and pipeline details
- Missing: Self-cal exact solints per dataset
- Missing: emcee setup and priors
- Missing: Keplerian mask parameters per source
- Missing: Class 0/I mask files
- Data volume (inferred): ~100–300 GB raw for the two programs
- Score (inferred): 3/5, Data public and many parameters given, but the recipe depends on prior papers and several choices (priors, line-free channels, masks) are unstated.
- Rediscovery candidate: no, Main results numeric and data public, but the analysis depends on inherited masking and Class II data from earlier papers and uncertain optical depth assumptions.

## Links

- Method: (cite: Bergner2018); (cite: Pegues2020) (Keplerian masking technique)
- Method: (cite: Goldsmith1999) (optical depth correction)
- Companion: (cite: Bergner2019b) (Class II C2H, HCN, C18O data and sample)
- Companion: (cite: Bergner2019c) (Serpens Class 0/I observations and hot corino detection)
- Companion: (cite: Guzman2017); (cite: Huang2017) (previous HC15N and DCN measurements in Class II disks)
- Related: Serpens protostars (Enoch et al.)

## Checks

```json
{
 "quotes": 96,
 "quotes_ok": 96,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 101,
  "stated": 71,
  "rate": 0.703
 },
 "evidence_ok": true
}
```

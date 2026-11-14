# ALMA Observations of HCN and HCO<SUP>+</SUP> Outflows in the Merging Galaxy NGC 3256

`2018ApJ...868...95M` | The Astrophysical Journal 2018 | first author: Michiyama, Tomonari | arXiv: 1810.04821 | DOI: 10.3847/1538-4357/aae82a

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars, astrochemistry
- Question: Is dense gas (HCN, HCO+) present in the molecular outflows of the merging galaxy NGC 3256, and how do outflow line ratios and physical conditions differ from the nuclei and between the AGN-hosting southern and starburst northern outflows?  
  > "The main motivation of this work is to identify the dense gas in the molecular gas outflows in NGC 3256, and to investigate how the outflows impact the surrounding ISM." (A case study: NGC 3256)
- Target **NGC 3256**: coordinates Field center RA=10h27m51.18s, Dec=-43d54m17.85s (Appendix figure captions)  
  > "the luminosity distance of $D_{\rm L}$ = 35 Mpc (cite: Sanders+03). This galaxy has two nuclei separated by 5$\ensuremath{''}$($\sim$ 850 pc)." (A case study: NGC 3256); z/distance D_L = 35 Mpc  
  > "the luminosity distance of $D_{\rm L}$ = 35 Mpc (cite: Sanders+03). This galaxy has two nuclei separated by 5$\ensuremath{''}$($\sim$ 850 pc)." (A case study: NGC 3256); distance from Sanders+03  
  > "the luminosity distance of $D_{\rm L}$ = 35 Mpc (cite: Sanders+03). This galaxy has two nuclei separated by 5$\ensuremath{''}$($\sim$ 850 pc)." (A case study: NGC 3256)

## Data provenance

- ALMA projects: 2015.1.00993.S, 2015.1.00714.S, 2011.0.00525.S
- bands: Band 3 for HCN/HCO+ (1–0); CO(2–1) Cycle 3 archival; CO(1–0) and CO(3–2) Cycle 0 archival  
  > "with the Band 3 receiver (ALMA Project ID: 2015.1.00993.S)" (2 ALMA data); "The CO (1–0) and CO (3–2) observations were conducted during Cycle 0" (2 ALMA data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 45 twelve meter antennas  
  > "using 45 twelve meter antennas with the Band 3 receiver" (2 ALMA data)
- configurations: _not stated_
- baselines: 15 m to 460 m (HCN/HCO+); CO(1-0)/(3-2) compact 15–269 m and extended 16–374 m  
  > "The range of unprojected baseline length is from 15 m to 460 m." (2 ALMA data); "combined the visibility data from the compact (15–269 m) and the extended (16–374 m) configurations" (2 ALMA data)
- angular resolution: 2.1" x 1.7" (360 x 460 pc); beam-matched to 2.1"  
  > "the achieved beam size is $2.1\ensuremath{''}\times1.7\ensuremath{''}$ (360 $\times$ 460 pc)" (2 ALMA data)
- max recoverable scale: _not stated_
- sensitivity: ~0.2 mJy/beam per 30 km/s channel  
  > "The r.m.s noise level is $\sim 0.2$ mJy beam$^{-1}$ for the velocity resolution of 30 km s$^{-1}$" (2 ALMA data)
- time on source: ~33 minutes on source (~2 h total)  
  > "the on source time is $\sim$ 33 minutes" (2 ALMA data)
- observing dates: 2016 March 7 and 8 (HCN/HCO+)  
  > "were carried out on 2016, March 7 and 8" (2 ALMA data)
- pi or archival as stated: HCN/HCO+ data from 2015.1.00993.S; CO(2-1) and CO(1-0)/(3-2) archival  
  > "In addition, we use the archival CO (2–1) data that was obtained during Cycle 3" (2 ALMA data)
- Line: HCN 1–0 (not stated)
- Line: HCO+ 1–0 (not stated)
- Line: CO 1–0, 2–1, 3–2 (not stated)
- External data: Radio peaks used to define North- and South-Nucleus positions  
  > "We define North-Nucleus and South-Nucleus (stars in Figures) as the peaks of the radio emission (cite: Neff+03)." (2 ALMA data) [from Neff+03]
- External data: 54%/46% split of red-shifted CO between southern and northern outflow  
  > "we assume 54$\%$ and 46$\%$ of the red-shifted components arise from the southern and northern nucleus, respectively (cite: Sakamoto+14)" (Discussion, OF-Red) [from Sakamoto+14]
- External data: SFR ~6 Msun/yr within ~3" of the southern nucleus from IR SED fitting  
  > "We adopt SFR of $\sim6$ M$_{\odot}$ yr$^{-1}$ [^4] for the $\sim3.0\ensuremath{''}$ region around the southern nucleus, which is derived from infrared SED fitting (cite: Lira+08)." (3.2 Outflow Properties) [from Lira+08]
- External data: Inclination of 80 deg for de-projecting outflow velocity  
  > "assuming an inclination of 80$^\circ$ (cite: Sakamoto+14)" (3.2 Outflow Properties) [from Sakamoto+14]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Calibrated visibility data used  
  > "We used the calibrated visibility data, and subtracted the continuum by using the uvcontsub task" (2 ALMA data)
- flux calibrator: Ganymede  
  > "The absolute flux density is calibrated using Ganymede, and the nominal calibration error is 5$\%$." (2 ALMA data)
- flux scale uncertainty: 10% adopted overall photometric error (5% nominal + 6% bandpass calibrator variation)  
  > "Hence, we adopt 10$~\%$ as a conservative overall photometric error." (2 ALMA data)
- self calibration: _not stated_

### Imaging

- task: CASA tclean (version 4.7.0) for HCN/HCO+; clean for CO(2-1)  
  > "using tclean task in ${\tt CASA}$ (version 4.7.0, Briggs weighting, robust = 0.5)" (2 ALMA data); "We made beam-matched and uv-clipped images by using clean task in ${\tt CASA}$" (2 ALMA data)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "Briggs weighting, robust = 0.5" (2 ALMA data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: automatic masking loop per CASA Guides  
  > "with automatically masking loop as described in the ${\tt CASA~Guides}$" (2 ALMA data)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub in CASA  
  > "subtracted the continuum by using the uvcontsub task in ${\tt CASA}$" (2 ALMA data)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: CO(1-0)/(3-2) compact and extended configurations combined  
  > "combined the visibility data from the compact (15–269 m) and the extended (16–374 m) configurations" (2 ALMA data)
- smoothing: Beam-matched to 2.1" (~360 pc) and uv-clipped >18 kλ  
  > "We made beam-matched ($2.1\ensuremath{''}\sim$ 360 pc) and uv-clipped ($>$ 18 k$\lambda$) images" (2 ALMA data)
- final beam: 2.1" x 1.7" before matching; 2.1" matched  
  > "the achieved beam size is $2.1\ensuremath{''}\times1.7\ensuremath{''}$ (360 $\times$ 460 pc)" (2 ALMA data)
- final rms: ~0.2 mJy/beam at 30 km/s  
  > "The r.m.s noise level is $\sim 0.2$ mJy beam$^{-1}$ for the velocity resolution of 30 km s$^{-1}$" (2 ALMA data)

### Inherited from earlier work

- Bayesian likelihood method for RADEX parameter constraints and one-sigma ranges  
  > "we conducted Bayesian likelihood statistical analysis, following the method described in (cite: Kame+12)" (4.1 RADEX and Bayesian analysis) [from Kame+12]
- CO(1-0) and CO(3-2) Cycle 0 calibrated archival data  
  > "The CO (1–0) and CO (3–2) observations were conducted during Cycle 0 (cite: Sakamoto+14)" (2 ALMA data) [from Sakamoto+14]
- Supernova kinetic power relation  
  > "by using the relationship derived by (cite: Veilleux+05)" (3.2 Outflow Properties) [from Veilleux+05]

### Not stated but needed to reproduce (our reading)

- Exact line-free channels used for uvcontsub
- Image size and cell size
- Clean thresholds and mask parameters
- Spectral setup/rest frequencies and windows
- Details of CO(2-1) channel width and uv-clip for CO data
- Priors and grid sampling for the Bayesian RADEX analysis
- How beam-matching and region apertures were applied for flux measurement
- Source of the SFR-dense gas mass relation used

## Analysis recipe

1. **Image line cubes**: Continuum subtraction and tclean with automasking; beam-matched, uv-clipped (>18 kλ) cubes for all CO and dense gas lines  
  > "We made data cubes with a velocity resolution of 30 km s$^{-1}$ using tclean task in ${\tt CASA}$" (2 ALMA data)
   - software: CASA
   - parameter: 30 km/s channels, Briggs robust 0.5  
  > "Briggs weighting, robust = 0.5" (2 ALMA data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify outflow components and measure fluxes**: Moment 0 maps over extreme velocity ranges; integrate nuclei over channels with S/N>3; 3 sigma upper limits for non-detections  
  > "We define the emission in $v=[240,360]~\rm{km~s}^{-1}$ and $v=[-360,-180]~\rm{km~s}^{-1}$ as the red-shifted and blue-shifted outflow gas, respectively." (3.1 Outflow Identification); "In the case of non-detection, we use the three sigma upper limit." (3.3 Line Ratio)
   - assumption: Southern share of CO(1-0) at OF-Red set by blue flux ratio, giving ~5 Jy km/s  
  > "we assume that the flux ratio between the two blue shifted components (at North-OF-Blue and South-OF-Blue) is the fractional contribution of the southern outflow at OF-Red" (3.1 Outflow Identification)
   - fitting: _not stated_
   - validation: Compared with CO fluxes of Sakamoto+14 (differences explained by uv-coverage and velocity range)  
  > "These values are different from our measurements." (Footnote 2)
3. **Derive outflow masses, rates and power**: Mass = alpha x luminosity; age = l/V; Mdot = M/age; kinetic power; compare with supernova power 7e41 x SFR  
  > "We estimate the age ($Age$), outflow rate ($\dot{M}$), and kinetic energy ($P_{\rm kin,OF}$) from the following equations." (3.2 Outflow Properties)
   - parameter: V_OF ~1600 km/s, l_OF = 400 pc  
  > "$V_{\rm OF}$ \[km s$^{-1}$\] | 1600" (Table 2)
   - assumption: alpha_HCN = 0.24–10, alpha_CO = 0.8–4.6  
  > "$\alpha_{\rm HCN}=[0.24,10.0]$ and $\alpha_{\rm CO}=[0.8,4.6]$" (3.2 Outflow Properties)
   - assumption: Inclination 80 deg  
  > "assuming an inclination of 80$^\circ$ (cite: Sakamoto+14)" (3.2 Outflow Properties)
   - fitting: _not stated_
   - validation: Compared with nominal starburst-driven ratio (~1%)  
  > "the $P_{\rm kin,OF}/P_{\rm kin,SF}$ is larger than the nominal ratio for pure starburst driven outflow ($\sim1\%$" (3.2 Outflow Properties)
4. **Compute line ratios**: Ratios in brightness temperature of CO 2-1/1-0, 3-2/1-0, HCN/CO, HCO+/CO, HCN/HCO+ in each region and velocity channel  
  > "Here, the line ratios (in unit of brightness temperature) are defined by the symbol “$R$" as follows" (1.2)
   - fitting: _not stated_
   - validation: _not stated_
5. **Non-LTE RADEX modelling with Bayesian likelihood**: Single-phase RADEX grid fit to five line fluxes for North-Nucleus, South-Nucleus, South-OF-Blue  
  > "We use the non local thermodynamic equilibrium (non-LTE) radiative transfer code ${\tt RADEX}$ (cite: RADEX) to estimate the physical properties" (4.1 RADEX and Bayesian analysis)
   - software: RADEX
   - parameter: Tkin 5–6300 K, nH2 1e1–1e7 cm-3, NCO 1e12–1e22 cm-2, FF 1e-5–1, abundance ratios 1e-7–1e-3  
  > "$T_{\rm kin}=5-6300$ K, $n_{\rm H_2}=10^1-10^7$ cm$^{-3}$, $N_{\rm CO}=10^{12}-10^{22}$ cm$^{-2}$, $FF=10^{-5}-10^{0}$" (4.1 RADEX and Bayesian analysis)
   - assumption: Tbg 2.73 K, FWHM 150 km/s, [CO/H2]=1e-4  
  > "We adopt the CO and H$_2$ abundance ratio of \[CO/H$_2$\] =$1.0\times10^{-4}$" (4.1 RADEX and Bayesian analysis)
   - fitting: Bayesian likelihood following Kamenetzky+12; column length limited to beam diameter ~400 pc and mass limited by virial mass  
  > "We use the diameter of the photometric beam size ($\sim400$ pc$~\sim2.1\ensuremath{''}$) as the upper limit to the length of the column." (4.1 RADEX and Bayesian analysis)
   - validation: FWHM 300 and 50 km/s tested; results consistent within one sigma  
  > "We find that the results are consistent to within one sigma range." (4.1 RADEX and Bayesian analysis)

## Software

- **CASA** 4.7.0: uvcontsub, tclean/clean imaging  
  > "using tclean task in ${\tt CASA}$ (version 4.7.0, Briggs weighting, robust = 0.5)" (2 ALMA data)
- **RADEX** : non-LTE radiative transfer modelling  
  > "We use the non local thermodynamic equilibrium (non-LTE) radiative transfer code ${\tt RADEX}$" (4.1 RADEX and Bayesian analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| R_HCO+/CO at South-OF-Blue | 0.20 | 0.04 | dimensionless | 4 | / South-OF-Blue / 1.2$\pm$0.2 / 1.3$\pm$0.2 / 0.13$\pm$0.04 / 0.20$\pm$0.04 / 0.68$\pm$0.24 / |
| R_HCO+/CO at South-Nucleus | 0.08 | 0.01 | dimensionless | 4 | / South-Nucleus / 0.9$\pm$0.1 / 0.7$\pm$0.1 / 0.05$\pm$0.01 / 0.08$\pm$0.01 / 0.60$\pm$0.08 / |
| R_32/10 at South-OF-Blue | 1.3 | 0.2 | dimensionless | 4 | larger in the southern outflow (0.20$\pm$0.04 and 1.3$\pm$0.2, respectively) |
| R_32/10 at South-Nucleus | 0.7 | 0.1 | dimensionless | 4 | than in the southern nucleus (0.08$\pm$0.01, 0.7$\pm$0.1, respectively) |
| Southern outflow molecular mass (CO) | 100–260e5 | range from alpha_CO | Msun | 3 | $M_{\rm dense}$ or $M_{\rm mol}$ \[$10^5~$M$_{\odot}$\] / 2.8–120 / 100–260 |
| Southern outflow dense gas mass (HCN) | 2.8–120e5 | range from alpha_HCN | Msun | 3 | $M_{\rm dense}$ or $M_{\rm mol}$ \[$10^5~$M$_{\odot}$\] / 2.8–120 / 100–260 |
| Outflow rate (HCN; CO) | 1–48; 40–104 | range | Msun/yr | 3 | $\dot{M}$ \[$M_{\odot}$ yr$^{-1}$\] / 1–48 / 40–104 |
| Outflow age | 0.25 | not stated | Myr | 3 | $Age$ \[Myr\] / 0.25 |
| Tkin South-OF-Blue (1 sigma) | 33–254 | 1 sigma range | K | 5 | / South-OF-Blue / 33 - 254 / $10^{4.3}$ - $10^{6.2}$ / $10^{16.6}$ - $10^{17.7}$ / 0.0006 - 0.0055 / |
| SFR from dense gas in outflow | 0.003–0.14 | range | Msun/yr | 0 | we estimate $SFR$ = 0.003-0.14 \[M$_\odot$ yr$^{-1}$\] from dense gas mass associated with outflow |

## Qualitative findings

- HCN and HCO+ detected in southern outflow but undetected in northern outflow.  
  > "the same lines were undetected in the outflow region associated with the northern nucleus" (abstract)

## Claim tuples

- H: Dense gas is present in the AGN-driven southern outflow but not in the starburst-driven northern outflow | E: HCN/HCO+ extreme-velocity moment maps compared with CO | R: Detected at OF-Red and South-OF-Blue; undetected at North-OF-Blue (<0.06 Jy km/s) | F: Southern outflow contains dense gas; northern does not | **supported**
- H: Southern outflow gas is denser and more excited than the southern nucleus | E: Line ratios in outflow vs nucleus | R: R_HCO+/CO 0.20 vs 0.08; R_32/10 1.3 vs 0.7 | F: Larger dense gas fraction and higher excitation in the outflow | **supported**
- H: The southern outflow is two-phase | E: Line ratios vs velocity offset | R: Dense gas fraction increases and R_32/10 decreases toward largest velocity offset | F: Suggests diffuse plus clumpy phases, possibly from jet-ISM interaction | **partially**
- H: Starburst alone cannot power the southern outflow | E: Compare outflow kinetic power with supernova power | R: P_kin,OF/P_kin,SF >20% (dense) and >100% (CO) | F: Another energy source such as AGN needed | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Non-LTE modelling because outflow conditions can differ from ambient ISM  
  > "The physical properties (e.g., temperature and density) of the outflow can be substantially different from the conditions seen in the ambient ISM." (4.1 RADEX and Bayesian analysis)
- Alternative: HCN/HCO+ enhancement cannot be explained by shocks alone  
  > "It is difficult to explain the origin of the large HCN/HCO$^+$ ratio seen in the outflows by shocks alone." (6.4 Shock in the outflow)
- How they decided it was enough: _not stated_
- Limitation (authors): Four lines constrain many parameters giving broad probability functions; single-phase assumption inappropriate  
  > "The critical issue of this modeling is that four lines are used as input parameters to estimate five parameters, resulting in the broad probability functions." (4.2 Results)
- Limitation (authors): Sensitivity insufficient for meaningful upper limit at North-OF-Blue  
  > "Our observation sensitivity is insufficient to derive a meaningful upper limit" (6.2 North-OF-Blue)
- Caveat (inferred, ours): Extreme-velocity integration excludes low-velocity entrained gas
- Caveat (inferred, ours): Mass conversion factors uncertain by large factors
- Caveat (inferred, ours): Northern/southern flux split at OF-Red is an assumption
- Caveat (inferred, ours): Only ~2 arcsec resolution; velocity-channel ratios depend on beam matching

## Reproducibility

- Data public (paper): Archival ALMA data used  
  > "we use the archival CO (2–1) data that was obtained during Cycle 3" (2 ALMA data)
- Products in archive: _not stated_
- Missing: Line-free channels and image grid parameters
- Missing: Bayesian prior/grid details
- Missing: Aperture definitions for flux extraction
- Data volume (inferred): ~50-150 GB raw across three projects
- Score (inferred): 3/5, Public data and many parameters stated, but line-free channels, imaging grids and Bayesian details missing.
- Rediscovery candidate: yes, Public ALMA data, imaging recipe mostly given, and results are numeric line ratios and fluxes.

## Links

- Method: Kamenetzky et al. 2012 (cite: Kame+12) (Bayesian likelihood RADEX method)
- Method: van der Tak et al. 2007 (cite: RADEX) (RADEX code)
- Companion: Sakamoto+14 (Earlier CO outflow study using Cycle 0 data)
- Companion: Harada+18 (ALMA line survey of NGC 3256)

## Checks

```json
{
 "quotes": 79,
 "quotes_ok": 79,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 54,
  "rate": 0.692
 },
 "evidence_ok": true
}
```

# A Spatially Resolved [C II] Survey of 31 z ∼ 7 Massive Galaxies Hosting Luminous Quasars

`2024ApJ...968....9W` | The Astrophysical Journal 2024 | first author: Wang, Feige | arXiv: 2404.15413 | DOI: 10.3847/1538-4357/ad3fb4

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: What are the [C II] and FIR continuum properties, sizes, kinematics, dynamical masses and SMBH-host relations of host galaxies of 31 luminous z>6.5 quasars?  
  > "In this paper, we present an overview of our spatially resolved [C II] survey of 31 luminous $z\sim7$ quasars and discuss the properties of quasar host galaxies based on [C II] and dust emission." (1 Introduction)
- Target **31 quasars at z>6.5 with M1450<-25 (e.g. J0038-1527, J0313-1806, J1007+2115, J0439+1634)**: coordinates per-object RA/Dec listed in Table 1 (e.g. J0038-1527: 00:38:36.10 -15:27:23.6)  
  > "J0038$-$1527 | 00:38:36.10 | $-$15:27:23.6 | 6.999$\pm$0.001 | $-$27.13 | ALMA | 2018.1.01188.S" (Table 1); z/distance z_MgII ~6.5-7.6 (Table 1)  
  > "J0038$-$1527 | 00:38:36.10 | $-$15:27:23.6 | 6.999$\pm$0.001 | $-$27.13 | ALMA | 2018.1.01188.S" (Table 1); distance from Mg II redshifts from near-IR spectroscopy (refs in Table 1); [C II] redshifts also measured  
  > "J0038$-$1527 | 00:38:36.10 | $-$15:27:23.6 | 6.999$\pm$0.001 | $-$27.13 | ALMA | 2018.1.01188.S" (Table 1)

## Data provenance

- ALMA projects: 2018.1.01188.S, 2019.1.01025.S, 2019.A.00017.S
- bands: _not stated_
- frequencies and spectral setup: two SPWs (0,1) on [C II], SPWs 2,3 ~15 GHz away for continuum  
  > "We tuned two spectral windows (SPW, 0 and 1) centered at the expected frequency of [C II] and the other two SPWs (2 and 3) centered at about 15 GHz away" (2.1 ALMA observation and data reduction)
- continuum bandwidth: _not stated_
- arrays: NOEMA: 10 antennas, C configuration, PolyFiX  
  > "All quasars were observed using 10 antennas with the C array configuration during winter 2018." (2.2 NOEMA observation and data reduction)
- configurations: C43-3 or C43-4  
  > "targets were observed with either the C43-3 or C43-4 configuration" (2.1 ALMA observation and data reduction)
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: design ~0.3 mJy/beam per 100 km/s; resolution 0.4''-0.7''  
  > "designed to reach a flux sensitivity of $\sim$0.3 mJy/beam per 100 $\rm km ~s^{-1}$ and a resolution of 0.4$''$–0.7$''$" (2.1 ALMA observation and data reduction)
- time on source: ~15 min per target designed for ALMA; NOEMA ~2.5 h on-source  
  > "The on-source exposure time for each target was designed to be $\sim15$ minutes" (2.1 ALMA observation and data reduction); "(on-source $\sim2.5$ hours) per target" (2.2 NOEMA observation and data reduction)
- observing dates: ALMA 2018 December to 2020 March; NOEMA winter 2018  
  > "Observations were carried out between 2018 December and 2020 March with 42–50 12m antennas." (2.1 ALMA observation and data reduction)
- pi or archival as stated: _not stated_
- Line: [C II] 158 um fine structure (not stated)
- Other facility **NOEMA**: [C II] and continuum for 5 quasars at Decl.>30 deg (program W18EJ)  
  > "26 quasars with $\rm Decl. < 30^\circ$ were targeted with ALMA and the other 5 quasars with $\rm Decl.>30^\circ$ were observed with NOEMA." (2 Observations and Data Reduction)
- External data: Mg II redshifts and M1450 of quasars  
  > "References for the quasar discovery (first number) and for $z_{\rm MgII}$ and $M_{\rm 1450}$ measurements (second number)." (Table 1 notes) [from Yang21 and others (cite: Yang21)]
- External data: Mg II black hole masses for the quasars  
  > "are measured from the Mg II emission line and are collected from the literature (cite: Banados21; Wang21b; Yang21)" (4.3 SMBH-host Co-evolution) [from (cite: Banados21; Wang21b; Yang21)]
- External data: [C II]/FIR properties and kinematics of z>5.7 quasars from the literature  
  > "There are 65 $z>5.7$ quasars with [C II] and FIR continuum observations in the literature at the time of doing our analyses." (3.1) [from (cite: Decarli18; Venemans20; Neeleman21)]
- Simulation/model as data: Haro 11 galaxy template used to derive L_FIR/L_TIR  
  > "a galaxy template from Haro 11 which has a relatively low metallicity and is thought to be a good analogue of high-redshift galaxies (cite: Lyu16)" (3.1)

## Processing

### Calibration

- pipeline or manual: CASA pipeline, default calibration procedure  
  > "All the ALMA data were processed using the CASA (cite: CASA) pipeline for ALMA using the default calibration procedure." (2.1 ALMA observation and data reduction)
- casa version: Cycle 6 calibrated with 5.4.0; Cycle 7 with 5.6.1; analysis with 5.6.1  
  > "The Cycle 6 data were calibrated with CASA version 5.4.0 and the Cycle 7 data were calibrated with CASA version 5.6.1." (2.1 ALMA observation and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "We imaged the data cubes using Briggs cleaning via the CASA task `tclean`" (2.1 ALMA observation and data reduction)
- deconvolver: _not stated_
- weighting robust: robust = 2.0 (natural) for main analysis; robust = 0.5 for kinematics  
  > "robustness parameter $r=2.0$, corresponding to natural weighting" (2.1 ALMA observation and data reduction); "using the `tclean` task with robust parameter $r=0.5$ to obtain images with slightly higher spatial resolution" (4.1 Kinematics and Morphology)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: box masks from dirty continuum+line map  
  > "creating box masks for detected sources and estimating the sensitivity of the observations" (2.1 ALMA observation and data reduction)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub in uv plane on SPWs 0&1  
  > "We then subtract the continuum for the data cube from SPWs 0&1 using the `uvcontsub` task in the UV plane." (2.1 ALMA observation and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: cube rebinned to 23.4 MHz (~30 km/s); NOEMA 50 km/s channels  
  > "re-bin the data cube to $\rm 23.4~MHz$ ($\rm\sim 30~ km~s^{-1}$ at the quasar redshifts)" (2.1 ALMA observation and data reduction)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Imaging process designed to follow Decarli et al. 2018 (z~6 quasars)  
  > "the imaging process was designed to closely follow that used by (cite: Decarli18)" (2.1 ALMA observation and data reduction) [from (cite: Decarli18)]
- Graybody T=47 K, beta=1.6  
  > "we assume a dust temperature of $T_{\rm dust}=47$ K and an emissivity index of $\beta=1.6$ (cite: Beelen06)" (3.1) [from (cite: Beelen06)]
- Dust mass opacity kappa=0.77 (nu/352 GHz)^beta cm2/g  
  > "Following (cite: Venemans18), the opacity coefficient is set by $\kappa_\nu(\beta)=0.77\,(\nu/352\,\mathrm{GHz})^\beta$ cm$^2$ g$^{-1}$." (3.4 Dust and Gas Mass) [from (cite: Venemans18)]
- Dynamical mass formula calibrated for marginally resolved data  
  > "They suggested an empirical relation based on their high-resolution [C II] observations" (4.2 Dynamical Mass) [from (cite: Neeleman21)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for continuum maps
- Clean threshold, niter, cell and image size, and mask details
- Self-calibration usage
- Flux calibrators and flux-scale uncertainty
- How v_proj was measured from velocity maps
- Scheme for correcting missing flux in 3'' aperture NOEMA fluxes
- Exact L_bolometric values used for Spearman tests
- Cosmic-microwave-background correction details for the graybody fit

## Analysis recipe

1. **Image ALMA data and extract spectra**: tclean dirty map, cubes at ~30 km/s, 1.5'' aperture 1D spectra fitted with flat continuum plus Gaussian  
  > "The spectra extracted from the SPWs 0&1 data cubes are then fitted with a flat continuum and a Gaussian function." (2.1 ALMA observation and data reduction)
   - software: CASA
   - parameter: aperture diameter 1.5''; robust 2.0  
  > "We extract a 1D spectrum of each object with an aperture diameter of 1.5$''$." (2.1 ALMA observation and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Make [C II] line and continuum maps and measure 2D flux and size**: collapse ±1.4 sigma_line (~83% flux, corrected), imfit 2D Gaussian  
  > "The fit is performed with the `imfit` task within CASA by assuming a 2D Gaussian profile" (3.1)
   - software: CASA
   - fitting: imfit 2D Gaussian with free centroid, flux, axes, PA  
  > "with the centroid, integrated flux, major and minor axes, and the position angle as free parameters" (3.1)
   - validation: ±3.0 sigma collapse gives size ratio median 1.04±0.10  
  > "falls within the range of 0.86 to 1.27, with a median of $1.04\pm0.10$" (3.2)
3. **Derive L_[CII], L_FIR, SFR, dust mass, C+ mass**: Luminosity equation; graybody and Haro 11 templates; De Looze14 and Murphy11 SFR relations; dust mass with CMB correction  
  > "We use the empirical relation calibrated by (cite: DeLooze14) for high-redshift galaxies to estimate the SFR" (3.3 Star Formation Rates)
   - parameter: T_dust=47 K, beta=1.6; T_ex=100 K for C+  
  > "By assuming $T_{\rm ex}=100$ K (cite: Meijerink07)" (3.4 Dust and Gas Mass)
   - assumption: dust-to-gas ratio 100, molecular fraction 0.75  
  > "By assuming a dust-to-gas ratio of 100 and a molecular-to-total gas mass fraction of 0.75 (cite: Neeleman21)" (3.4 Dust and Gas Mass)
   - fitting: _not stated_
   - validation: Compared SFR from [C II], graybody and Haro 11; tested HC18 Sigma_SFR-dependent relation  
  > "the [C II]-based SFR after considering the $\Sigma_{\rm SFR}$ is more consistent with the $L_{\rm FIR}$-based SFR" (3.5 [C II] Deficit)
4. **Classify kinematics and estimate dynamical masses**: re-image with robust 0.5, moment maps with immoments, v_proj/2sigma_int>0.4 criterion; thin-disk M_dyn and Neeleman21 relation  
  > "galaxies with $v_{\rm proj}/2\sigma_{\rm int}>0.4$ can be classified as rotation-dominated systems" (4.1 Kinematics and Morphology)
   - software: CASA
   - parameter: D=1.5×FWHM major axis; i=arccos(b/a)  
  > "The inclination angle, $i$, is given by the ratio of minor ($a_{\rm min}$) and major ($a_{\rm maj}$) axes" (4.2 Dynamical Mass)
   - assumption: [C II] from thin rotating disk  
  > "by assuming that the [C II] emission is originating from a thin rotating disk" (4.2 Dynamical Mass)
   - fitting: _not stated_
   - validation: Two M_dyn equations compared (factor ~2.3)  
  > "which are $\sim2.3$ times lower than those estimated from Equation" (4.2 Dynamical Mass)

## Software

- **CASA** 5.4.0 (calibration Cycle 6), 5.6.1 (calibration Cycle 7 and analysis): calibration, tclean, uvcontsub, imfit, immoments  
  > "All the data were then analyzed using CASA version 5.6.1." (2.1 ALMA observation and data reduction)
- **GILDAS mapping** : NOEMA data analysis  
  > "The NOEMA data were analyzed using the `mapping` software from the GILDAS[^2] suite." (2.2 NOEMA observation and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| L_[CII] range | 0.3-5.5 | not stated | 1e9 Lsun | 3 | $L_{\rm [CII]}=(0.3-5.5)\times10^9~L_\odot$ |
| L_FIR range | 0.5-13.0 | not stated | 1e12 Lsun | 3 | $L_{\rm FIR}=(0.5-13.0)\times10^{12}~L_\odot$ |
| Spearman rho L_[CII] vs L_bol | 0.43 | p=1.7e-4 | dimensionless | 3 | correlation coefficient of $\rho=0.43$ and a chance probability of $p=1.7\times10^{-4}$ |
| Spearman rho L_FIR vs L_bol | 0.48 | p=7.4e-6 | dimensionless | 3 | correlation coefficient of $\rho=0.48$ and a chance probability of $p=7.4\times10^{-6}$ |
| Median host diameter and inclination | D=5.0 kpc, i=46 deg | not stated | kpc, deg | 2 | The median values are $D=5.0$ kpc and $i=46^\circ$ |
| Rotation-dominated fraction | 10 of 23 (43%) | not stated | percent | 4 | (43%) as rotation-dominated galaxies |
| M_dyn range of rotation-dominated hosts | 0.1-7.5 | large | 1e11 Msun | 4 | The dynamical mass spans a broad range of $\sim(0.1-7.5)\times10^{11}~M_\odot$. |
| M_BH/M_dyn excess over local | ~10 (range 0.6-60) | not stated | dimensionless | 4 | with a broad range spanning from approximately 0.6 to 60 |

## Qualitative findings

- Continuum emission more concentrated than [C II]; [C II] deficit similar to local IR-luminous galaxies  
  > "In general, the continuum emission is more concentrated than the [C II] emission" (3.2)

## Claim tuples

- H: Do quasar luminosity and host [C II]/FIR luminosity correlate? | E: Spearman tests on this work plus literature | R: rho=0.43 and 0.48 | F: moderate correlation with large scatter | **supported**
- H: What are the kinematics of z~7 quasar hosts? | E: Moment maps and v_proj/2sigma_int criterion | R: 43% rotation-dominated | F: diverse kinematics, rest dispersion-dominated or disturbed | **supported**
- H: Are SMBHs overmassive relative to local M_BH-M_dyn? | E: Dynamical masses combined with literature | R: ratio ~10 higher, range 0.6-60 | F: overmassive BHs with large scatter and uncertainty | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Imaging at natural weighting to maximize S/N and follow Decarli18 for comparison  
  > "to maximize the signal-to-noise ratio (S/N) of our observations" (2.1 ALMA observation and data reduction)
- Alternative: Haro 11 template luminosities not used in later analyses; graybody preferred as more widely used  
  > "Since the modified graybody has been more broadly used in the literature, we only use the luminosities derived from the graybody fitting in the following analyses." (3.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Marginal resolution, assumed T_dust, and uncertain inclination give large uncertainties in M_dyn and SFR  
  > "We emphasize that the $M_{\rm dyn}$ estimated from both equations have large uncertainties" (4.2 Dynamical Mass)
- Caveat (inferred, ours): Dynamical masses from marginally resolved data with assumed inclination and a thin-disk formula are very uncertain
- Caveat (inferred, ours): Single fixed T=47 K graybody drives L_FIR, SFR and dust mass
- Caveat (inferred, ours): Selection biased to UV-luminous quasars affects correlations
- Caveat (inferred, ours): Counts of detections differ between abstract (27/28) and summary (26/27)

## Reproducibility

- Data public (paper): ALMA program IDs are given in acknowledgements; archival status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.01188.S., ADS/JAO.ALMA #2019.1.01025.S, ADS/JAO.ALMA#2019.A.00017.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Line-free channel definitions
- Missing: Clean parameters
- Missing: Bolometric luminosities and literature compilation
- Missing: NOEMA mapping details
- Data volume (inferred): ~100-300 GB raw for 26 ALMA fields
- Score (inferred): 3/5, Data and main steps are described with equations, but several imaging parameters and the literature compilation are missing.
- Rediscovery candidate: yes, ALMA data are public in the listed projects, steps are largely specified, and results are numeric (fluxes, luminosities, sizes).

## Links

- Method: (cite: Decarli18) (imaging and analysis approach followed)
- Method: (cite: Neeleman21) (dynamical mass relation and kinematic comparison)
- Companion: (cite: Yang19b) (NOEMA observation of J0439+1634)
- Companion: (cite: Yue21) (high-resolution ALMA of J0439+1634)
- Related: ALMA Cycle 9 Large Program 2022.1.01077.L

## Checks

```json
{
 "quotes": 64,
 "quotes_ok": 64,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2022.1.01077.L"
 ],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 46,
  "rate": 0.622
 },
 "evidence_ok": true
}
```

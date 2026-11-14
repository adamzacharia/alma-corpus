# Molecular remnant of Nova 1670 (CK Vulpeculae). I. Properties and enigmatic origin of the gas

`2020A&A...644A..59K` | Astronomy and Astrophysics 2020 | first author: Kamiński, Tomek | arXiv: 2006.10471 | DOI: 10.1051/0004-6361/202038648

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, astrochemistry, stellar_physics
- Question: What are the molecular composition, morphology, excitation, and origin of the molecular gas in the remnant of Nova 1670 (CK Vul), a candidate stellar merger?  
  > "this study presents the survey and focuses on the molecular composition in different parts of the nebula." (Introduction)
- Target **CK Vul (Nova 1670)**: coordinates RA=19:47:39.07, Dec=27:28:45.16 (ICRS, field center)  
  > "The field center for the ALMA and SMA surveys was set to ICRS coordinates RA=19:47:39.07 and Dec=27:28:45.16." (2.1 ALMA survey); "assume a distance of 0.7 kpc to CK Vul (cite: hajduk2013)" (6 Molecule survival); z/distance 0.7 kpc (lower limit)  
  > "The field center for the ALMA and SMA surveys was set to ICRS coordinates RA=19:47:39.07 and Dec=27:28:45.16." (2.1 ALMA survey); "assume a distance of 0.7 kpc to CK Vul (cite: hajduk2013)" (6 Molecule survival); distance from Hajduk et al. 2013  
  > "The field center for the ALMA and SMA surveys was set to ICRS coordinates RA=19:47:39.07 and Dec=27:28:45.16." (2.1 ALMA survey); "assume a distance of 0.7 kpc to CK Vul (cite: hajduk2013)" (6 Molecule survival)

## Data provenance

- ALMA projects: 2017.1.00999.S, 2017.A.00030.S, 2016.1.00448.S, 2015.A.00013.S
- bands: ALMA bands 3, 4, 5 (survey) plus archival band 6  
  > "sub-arcsec resolution over ALMA bands 3, 4, and 5, in which molecular emission lines are brightest and most numerous for CK Vul. Archival data extend the spectral coverage up to band 6." (2.1 ALMA survey)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12-m antennas, two array configurations per setup (archival: single configuration); 25 setups  
  > "Each frequency setup was executed in two different array configurations of 12-m antennas to cover a wide range of spatial frequencies" (2.1 ALMA survey)
- configurations: _not stated_
- baselines: 13–3200 m at lowest frequencies  
  > "the observations at the lowest frequencies were obtained with projected baselines 13–3200 m." (2.1 ALMA survey)
- angular resolution: survey studies structures larger than about 0.3''  
  > "the survey allows us to study structures larger than about 0.3$''$ and should recover emission smaller than about 15$''$." (2.1 ALMA survey)
- max recoverable scale: about 15''  
  > "the survey allows us to study structures larger than about 0.3$''$ and should recover emission smaller than about 15$''$." (2.1 ALMA survey)
- sensitivity: rms 0.04 Jy/beam in band 3, 0.01 Jy/beam in bands 4 and 5 (5 MHz binning)  
  > "the typical rms noise values are 0.04 Jy/beam in band 3 and 0.01 Jy/beam in bands 4 and 5 (at 5 MHz binning)." (2.1 ALMA survey)
- time on source: _not stated_
- observing dates: Dec 2017–Sep 2018 (survey); 2016–Apr 2017 archival  
  > "| 03-Dec-17   | 1391      | 3         | 88.32–90.19   |" (Table 1)
- pi or archival as stated: Survey plus archival ALMA runs (one archival run PI: Evans)  
  > "Note that the observations from April 2017 (PI: Evans) have a much poorer spectral resolution than the other data." (2.1 ALMA survey)
- Other facility **SMA (with SWARM)**: Band 6 and 7 line survey extending to higher frequencies, 2018 plus archival 2014  
  > "A dedicated and complementary extension of the ALMA survey towards higher frequencies was done in 2018 with the SMA and the SWARM correlator" (2.2 SMA survey)
- Other facility **VLA**: K, Ka, Q-band data; NH3 map and Q-band spectra for SiO modeling  
  > "used the $Q$-band spectra to achieve a better convergence in modeling the excitation of SiO" (2.3 VLA observations)
- Other facility **VLT X-shooter**: Near-IR H2 spectrum used for H2 excitation temperatures  
  > "The near-infrared X-shooter spectrum covering the spectral range 1–2.48 $\mu$m has not been analyzed." (2.4 H2 emission)
- External data: Collisional rate coefficients for RADEX modeling  
  > "The collisional rate coefficients of the modeled molecules were taken from the LAMDA database" (5.1 The modeling procedure) [from (cite: lamda) and sources listed]
- External data: Photodissociation rates and shielding functions  
  > "In the calculations, we used the photodissociation rates of (cite: dissociation)." (8 Molecule survival) [from (cite: dissociation)]
- External data: Optical nebula S abundance and N, O abundances from X-shooter  
  > "except for sulfur which was found to be slightly less abundant in CK Vul (S=6.76) than in the Sun (S=7.20) (cite: xshooter)." (6 Equilibrium chemistry) [from (cite: xshooter)]

## Processing

### Calibration

- pipeline or manual: Default ALMA pipeline in CASA; most data self-calibrated on continuum  
  > "The visibility data were calibrated with the default ALMA data reduction pipeline in the Common Astronomy Software Applications (CASA) package" (2.1 ALMA survey)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: SMA: Callisto, Neptune or Titan  
  > "Careful calibration to absolute flux was obtained by observations of Callisto, Neptune, or Titan." (2.2 SMA survey)
- flux scale uncertainty: SMA flux calibration consistent within 20%  
  > "The flux calibration is consistent to within 20%." (2.2 SMA survey)
- self calibration: Most ALMA data self-calibrated on continuum; SMA phase-only self-cal where S/N high  
  > "Most data were further self-calibrated using the strong continuum emission of CK Vul." (2.1 ALMA survey)

### Imaging

- task: clean and tclean in CASA 5.4–5.6  
  > "employing the `clean` and `tclean` implementations of the CLEAN algorithm in CASA versions 5.4–5.6." (2.1 ALMA survey)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "we used the optimal Briggs weighting with the robust parameter of 0.5." (2.1 ALMA survey)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Subtracted in the uv domain  
  > "The continuum contribution was subtracted in the calibrated visibility ($uv$) domain." (2.1 ALMA survey)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Visibility data overlapping in frequency combined; SMA configurations combined  
  > "Visibility data overlapping in frequency were combined." (2.1 ALMA survey)
- smoothing: Maps of a species smoothed to the largest beam; regions analysed at common 1'' beam  
  > "In CASA, we restored the image cubes with a common beam size of 1$''$" (5.1 The modeling procedure)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Line identifications from single-dish survey  
  > "were attributed to molecular transitions following the identification presented in KMT17." (3 Survey summary) [from KMT17 (cite: kami-singledish)]
- Modeling procedures similar to KMT17  
  > "Our modeling procedures are similar to those used in KMT17" (5.1 The modeling procedure) [from KMT17 (cite: kami-singledish)]
- Archival ALMA observations described in earlier papers  
  > "These observations were described in detail in (cite: kamiAlF) and (cite: Eyres)." (2.1 ALMA survey) [from (cite: kamiAlF); (cite: Eyres)]
- Isotopic ratios for correcting column densities  
  > "after correcting for their respective isotopologues as constrained in (cite: kami-singledish)" (5.3 Column densities) [from (cite: kami-singledish)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum-subtraction fit order
- Self-calibration solution intervals and which datasets were self-calibrated
- Cell size, image size, masks and clean thresholds
- Exact transitions and velocity windows used for each molecule and region
- Region polygons coordinates for the five regions
- CASSIS grid ranges and steps for chi2 minimization
- Per-line Gaussian fit parameters
- Exact CASA version per dataset
- Flux scale uncertainty of ALMA data

## Analysis recipe

1. **Calibrate and image line cubes**: Pipeline calibration, self-calibration, uv continuum subtraction, (t)clean Briggs 0.5 cubes at 3–5 km/s  
  > "The continuum-subtracted data were used to create data cubes employing the `clean` and `tclean` implementations of the CLEAN algorithm in CASA versions 5.4–5.6." (2.1 ALMA survey)
   - software: CASA
   - parameter: robust = 0.5  
  > "we used the optimal Briggs weighting with the robust parameter of 0.5." (2.1 ALMA survey)
   - fitting: _not stated_
   - validation: _not stated_
2. **Make combined moment/total-intensity maps per molecule**: Combine unblended transitions of all isotopologues, smooth to largest beam, noise-weighted mean  
  > "In the combination procedure, we calculated a weighted mean with weights set by the respective noise levels in the smoothed maps." (4 Morphology)
   - software: CASA
   - assumption: Morphology does not change much with transition owing to narrow Eu range  
  > "the emission morphology typically does not change much with transition owing to the narrow range of the upper-level energies" (4 Morphology)
   - fitting: _not stated_
   - validation: _not stated_
3. **Extract regional spectra and fit excitation (LTE then non-LTE)**: Averaged spectra in 5 regions at 1'' beam; chi2 grid of Tex/Tkin and N with LTE then RADEX; Gaussian velocity components  
  > "We used CASSIS and its $\chi^2$ minimization procedures plugged into RADEX" (5.1 The modeling procedure)
   - software: CASSIS, RADEX, CASA
   - parameter: beam filling factor 1.0 for almost all models  
  > "The beam filling factor was set to 1.0 for almost all models." (5.1 The modeling procedure)
   - assumption: H2 main collisional partner; ortho/para 3; CMB 2.73 K only external radiation; isothermal homogeneous gas  
  > "We assume that throughout the entire molecular nebula H$_2$ is the main collisional partner for all molecules." (5.1 The modeling procedure)
   - fitting: chi2 minimum on regular grid  
  > "Physical parameters were identified within a regular grid of models through finding the $\chi^2$ minimum." (5.1 The modeling procedure)
   - validation: Compared with KMT17 results; model-vs-observed spectra for SO2 and CH3OH  
  > "The “integrated” column densities reported in KMT17 cannot be directly compared, but they are in reasonable quantitative agreement with our results." (5.4 Lobes)
4. **Constrain CNO and elemental abundances via thermal equilibrium chemistry**: GGChem TE abundances vs observed relative to CO, chi2 grid and emcee MCMC  
  > "We used the chemical equilibrium code GGChem of (cite: woitke) to simulate molecular gas abundances for different physical conditions." (6 Equilibrium chemistry)
   - software: GGChem, emcee
   - parameter: 32 starting sets, 64 walkers, 4000 samples; priors 5<C<12, 3.5<N<12, 4<O<12, sum<27  
  > "We used 32 starting sets of parameters, 64 walkers, and draw 4000 samples." (6 Equilibrium chemistry)
   - assumption: Frozen chemistry at T~700–2500 K, n~1e10–1e14 cm-3; solar abundances for other metals, S=6.76  
  > "temperatures of $\sim$700–2500 K and densities of the order of 10$^{10}$–10$^{14}$ cm$^{-3}$" (6 Equilibrium chemistry)
   - fitting: emcee MCMC, median and 16th–84th percentiles  
  > "Taking the most likely value as the 50th percentile and uncertainties as 16th to 84th percentile" (6 Equilibrium chemistry)
   - validation: Compared N and O with optical jet abundances  
  > "N and O abundances within the lobes are in reasonable agreement (i.e., within an order of magnitude) with those derived from the optical nebular "jet"" (6 Equilibrium chemistry)
5. **Molecule photodissociation lifetimes**: Lifetimes under ISRF and WD radiation with dust shielding using Heays et al. rates  
  > "We recalculated the lifetimes of molecules assuming $A_V=3$ mag for standard interstellar dust" (8 Molecule survival)
   - software: IRAF
   - parameter: AV = 3 mag; gas-to-dust 124; WD Teff 20 and 60 kK; r=2''; d=0.7 kpc  
  > "assume a distance of 0.7 kpc to CK Vul (cite: hajduk2013)" (8 Molecule survival)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.4–5.6: Calibration, imaging, SMA/VLA processing  
  > "CASA versions 5.4–5.6" (2.1 ALMA survey)
- **MIR** : SMA calibration  
  > "The SMA data were calibrated using standard procedures in the MIR package." (2.2 SMA survey)
- **CASSIS** 5.0: Line identification and radiative-transfer modeling  
  > "We used the CASSIS software (version 5.0)" (5.1 The modeling procedure)
- **RADEX** : Non-LTE excitation  
  > "RADEX is a one-dimensional radiative-transfer code" (5.1 The modeling procedure)
- **GGchem** : Thermal equilibrium chemistry  
  > "We used the chemical equilibrium code GGChem" (6 Equilibrium chemistry)
- **emcee** : MCMC of elemental abundances  
  > "We used the *emcee* implementation (cite: emcee) of the MCMC method" (6 Equilibrium chemistry)
- **IRAF** : reddening procedure for WD spectra  
  > "with the `reddening` procedure in IRAF" (8 Molecule survival)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median temperature, central region | 17.1 | not stated | K | 3 | The median temperature for species we modeled with the highest confidence is 17.1 K. |
| Median temperature, SW and NE lobes | 13.9 | not stated | K | 3 | The median temperature in the SW and NE lobes is about 13.9 K |
| H2 density from CH3OH in lobes | (1-20)e4 | not stated | cm^-3 | 3 | Our models yield $n$(H$_2$) of $(1-20)\times10^4$ cm$^{-3}$. |
| H2 vibrational excitation temperature | 2613 | 173 (1 sigma) | K | 0 | the vibrational excitation temperature of 2613$\pm$173 K (1$\sigma$ error) |
| H2 rotational temperature | 2781 | 212 | K | 0 | rotational temperature of 2781$\pm$212 K |
| CNO abundances in central region (MCMC) | C=9.2, N=6.9, O=6.3 | C -1.3/+1.0, N -0.3/+0.6, O ±0.1 | dex (H=12) | 4 | $\mathrm{C} = 9.2_{-1.3}^{1.0}, 
\mathrm{N} = 6.9_{-0.3}^{0.6}, \mathrm{and}~
\mathrm{O} = 6.3_{-0.1}^{0.1}.$ |
| Fluorine abundance from AlF | 5.0 | not stated | dex (H=12) | 4 | we obtained also the abundance of fluorine at F=5.0 |
| Major axis PA of continuum central region | 98.2 | not stated | deg E of N | 2 | In the continuum, the longer axis is at a PA of 98.2$^\circ$ E of N. |

## Qualitative findings

- Molecular nebula is an 8-shaped structure with S-shaped neutral and mirrored ion emission, surrounded by a larger dust 8  
  > "The S- and -shaped structures complement each other forming a very regular structure in the shape of an "8"." (4 Morphology)
- Central region is O-rich (SO2, SO, AlF exclusive); complex species mostly in lobes  
  > "this species is indeed present exclusively in the central region" (4 Morphology)

## Claim tuples

- H: Non-LTE modeling of resolved regions gives better excitation constraints than LTE | E: LTE and RADEX fits to spectra of five regions | R: RADEX reproduces lines (e.g. CH3OH anti-inversion absorption) better; T~17 K central, ~14 K lobes | F: Gas is cold, n~1e4–1e6 cm-3, with chemical differences between center and lobes | **supported**
- H: Molecules can survive 350 yr in the remnant | E: Photodissociation lifetimes with dust shielding | R: Lifetimes with AV=3 mag grains exceed or approach 350 yr | F: Molecular gas could have formed 350 yr ago or more recently | **supported**
- H: Central star is a hot WD | E: WD radiation field photodissociation estimates | R: Teff>~60 kK would destroy molecules | F: Hot WD excluded; cool remnant favored | **supported**
- H: Elemental CNO abundances can be derived with equilibrium chemistry | E: GGchem + chi2 and MCMC | R: Large uncertainties | F: Relative CNO abundances not quantified | **partially**

## Reasoning

- Why this data: Interferometric survey to resolve molecular emission in bands where lines are brightest  
  > "The survey was intended to obtain interferometric maps of molecular emission at a sub-arcsec resolution over ALMA bands 3, 4, and 5" (2.1 ALMA survey)
- Why this method: _not stated_
- Alternative: LTE models rejected as inadequate in many cases in favor of non-LTE RADEX  
  > "Despite the best effort, many of the LTE models turned out to be inadequate" (5.1 The modeling procedure)
- Alternative: NH2CHO claimed earlier considered a mis-identification  
  > "We find no evidence for the presence of NH$_2$CHO claimed by (cite: Eyres) and consider it a mis-identification." (3 Survey summary)
- How they decided it was enough: _not stated_
- Limitation (authors): Errors underestimated; isothermal assumption fails in center; SO2 fits unsatisfactory  
  > "The errors are highly underestimated as they do not account for systematic errors" (5.3 Excitation central region)
- Limitation (authors): Beam filling factors set to 1; no collisions with e- and H  
  > "collisions with electrons (and with atomic hydrogen) are not considered in our analysis" (5.1 The modeling procedure)
- Caveat (inferred, ours): Single-component Gaussian, isothermal RADEX model oversimplifies a kinematically complex nebula
- Caveat (inferred, ours): TE chemistry applied to a shocked remnant is of doubtful validity
- Caveat (inferred, ours): Beam filling factor of 1 biases column densities
- Caveat (inferred, ours): Missing short spacings affect CO

## Reproducibility

- Data public (paper): ALMA project codes acknowledged; archival ALMA data used  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00999.S" (Acknowledgements)
- Products in archive: _not stated_
- Missing: Region definitions and spectral fit windows
- Missing: CASSIS fit grids
- Missing: Reduced cubes and fitted-line tables not provided
- Data volume (inferred): Several hundred GB to ~1 TB raw ALMA data (25+3 setups, two configurations each)
- Score (inferred): 3/5, Public data and software named, but imaging details and fitting setups are largely unstated; many results are qualitative.
- Rediscovery candidate: no, Recipe incomplete (regions, line selections, grids unstated) and many results qualitative.

## Links

- Method: Kamiński et al. 2017 (KMT17) (Single-dish line identifications and LTE modeling approach)
- Method: Heays et al. 2017 (Photodissociation rates and shielding)
- Companion: Kamiński et al. 2018, Nature Astronomy (kamiAlF) (Earlier ALMA data and isotopic analysis)
- Companion: Tylenda et al. 2019 (xshooter) (Optical X-shooter analysis of the nebula)
- Related: ALMA/SMA CK Vul line survey
- Related: Forthcoming papers on 3D structure, continuum, isotopic ratios

## Checks

```json
{
 "quotes": 82,
 "quotes_ok": 82,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 88,
  "stated": 62,
  "rate": 0.705
 },
 "evidence_ok": true
}
```

# Chemistry of a newly detected circumbinary disk in Ophiuchus

`2018A&A...614A..26A` | Astronomy and Astrophysics 2018 | first author: Artur de la Villarmois, Elizabeth | arXiv: 1802.09286 | DOI: 10.1051/0004-6361/201731603

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry, protoplanetary_disks
- Question: Is there a circumbinary disk around the Class I proto-binary Oph-IRS67AB, and what are its kinematics, chemistry, mass and temperature structure?  
  > "The purpose of this paper is to present the detection of a circumbinary disk around the system Oph-IRS67 and analyse its chemical and physical structure." (abstract)
- Target **Oph-IRS67AB (L1689SAB, WLY2-67)**: coordinates Geometric center 16h32m00.983s, -24d56m43.09s (J2000)  
  > "The distance was determined to be 147.3 $\pm$ 3.4 pc to L1689 as a whole and 151.2 $\pm$ 2.0 pc to IRS67AB specifically; in this paper, we adopt the latter." (1 Introduction); z/distance 151.2 ± 2.0 pc  
  > "The distance was determined to be 147.3 $\pm$ 3.4 pc to L1689 as a whole and 151.2 $\pm$ 2.0 pc to IRS67AB specifically; in this paper, we adopt the latter." (1 Introduction); distance from Ortiz-Leon et al. 2017 (proper motion and parallax)  
  > "The distance was determined to be 147.3 $\pm$ 3.4 pc to L1689 as a whole and 151.2 $\pm$ 2.0 pc to IRS67AB specifically; in this paper, we adopt the latter." (1 Introduction)

## Data provenance

- ALMA projects: 2013.1.00955.S
- bands: _not stated_
- frequencies and spectral setup: Five spws near 337-350 GHz (0.8 mm); 0.11 and 0.22 km/s resolution  
  > "The observations targeted five different spectral windows" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 21-556 m (up to 784 m on June 5)  
  > "providing baselines between 21 and 556 metres (784 metres for the June 5 observations)" (2 Observations)
- angular resolution: beam 0.44'' x 0.33''  
  > "The resulting dataset has a beam size of 0.44$''$ $\times$ 0.33$''$" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 0.4 mJy/beam; 10 mJy/beam per channel  
  > "a continuum *rms* level of 0.4 mJy beam$^{-1}$ and a spectral *rms* level of 10 mJy beam$^{-1}$ per channel" (2 Observations)
- time on source: ~15 min per source (43 min per session for 12 sources)  
  > "each source was observed for approximately 15 minutes in total" (2 Observations)
- observing dates: Four sessions between 2015 May 21 and June 5  
  > "IRS67 was observed with ALMA on four occasions between 2015 May 21 and June 5" (2 Observations)
- pi or archival as stated: Part of survey of 12 Class I protostars in Ophiuchus, PI Jes Jørgensen  
  > "as part of a larger program to survey the line and continuum emission towards 12 Class I protostars in Ophiuchus" (2 Observations)
- Line: C17O J=3-2 (spw 337.002-337.119 GHz)
- Line: C34S J=7-6 (spw 337.337-337.454 GHz)
- Line: H13CO+ J=4-3 (spw 346.880-347.115 GHz)
- Line: SO2 18(4,14)-18(3,15), 20(1,19)-19(2,18) (spw 338.165-338.634 GHz)
- Line: c-C3H2 5(5,1)-4(4,0) and 5(5,0)-4(4,1) (spw 2 and spw 4)
- Line: C2H N=4-3 hyperfine doublets (spw 349.165-349.634 GHz)
- Line: CH3OH J_k=7_k-6_k branch (338.4 GHz (not detected))
- External data: Distance to IRS67AB of 151.2 pc  
  > "in this paper, we adopt the latter." (1 Introduction) [from (cite: OrtizLeon2017)]
- External data: System velocity VLSR 4.2 km/s  
  > "relative to the system velocity ($V_{\rm LSR}$) of 4.2 km s$^{-1}$ (cite: Lindberg2017)" (3.1 Continuum emission) [from (cite: Lindberg2017)]
- External data: Dust opacity at 0.87 mm  
  > "opacity at 0.87 mm (cite: Ossenkopf1994)" (4.2 Disk mass) [from (cite: Ossenkopf1994)]
- External data: IRAS 16293-2422 abundance ratios for comparison  
  > "taken from (cite: Schoier2002)" (4.3 Fits and abundances) [from (cite: Schoier2002)]
- External data: Standard isotope ratios  
  > "employing standard isotope ratios (cite: Wilson1999)" (4.3 Fits and abundances) [from (cite: Wilson1999)]

## Processing

### Calibration

- pipeline or manual: Calibration and imaging done in CASA; gain cal J1517-2422, J1625-2527; passband J1924-2914  
  > "the complex gains were calibrated through observations of the quasars J1517-2422 and J1625-2527, passband calibration on J1924-2914 and flux calibration on Titan." (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan  
  > "flux calibration on Titan" (2 Observations)
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

### Not stated but needed to reproduce (our reading)

- CASA version and whether pipeline or manual calibration
- Imaging parameters: weighting/robust, cell and image size, deconvolver, masks
- Continuum subtraction method and line-free channels
- Whether spws were combined across the four sessions
- Flux calibration uncertainty and any self-calibration
- Velocity ranges for moment maps and clipping thresholds
- Uncertainty and weighting details of the imfit peak-position PV fits
- RADEX setup details beyond density, Tkin, and b
- Dust temperature adopted for the 30 K versus 100 K masses (continuum flux used for mass)

## Analysis recipe

1. **Measure continuum structure and source positions**: 2D Gaussian fits to both peaks; deconvolved size of disk-like structure; inclination from toy thin circular model  
  > "The position and integrated flux of each source are obtained by fitting two-dimensional (2D) Gaussians to both peaks" (3.1 Continuum emission)
   - software: CASA
   - assumption: Thin circular structure gives inclination ~80 deg  
  > "Assuming a toy model for a thin and circular structure, an inclination of $\sim$ 80$\ensuremath{^\circ}$" (3.1 Continuum emission)
   - fitting: _not stated_
   - validation: _not stated_
2. **Moment maps, spectra and channel maps of lines**: Moment 0/1 maps; spectra extracted over 1 pixel (0.1''x0.1''); channel maps; two-component Gaussian for SO2  
  > "Each spectrum was extracted over 1 pixel, that is, 0.1$''$ $\times$ 0.1$''$." (3.2.2 Spectra)
   - software: CASA
   - fitting: Gaussian fits to central components  
  > "the central component of the spectra of both species is fitted with a Gaussian and the values are listed in Table" (4.3 Fits and abundances)
   - validation: _not stated_
3. **Fit velocity profiles (Keplerian vs infalling)**: Peak emission per channel via imfit; fit v∝r^-0.5 and v∝r^-1 to points >1.7 km/s along PA=234 deg  
  > "the peak emission for each channel is obtained through the CASA task `imfit`." (4.1 Velocity profiles)
   - software: CASA imfit
   - parameter: Centre at geometric centre; inclination 80 deg  
  > "the central (0,0) position corresponds to the location of the geometric centre" (4.1 Velocity profiles)
   - assumption: Inclination 80 deg  
  > "assuming an inclination of 80$\ensuremath{^\circ}$" (4.1 Velocity profiles)
   - fitting: reduced chi2 compared; central mass derived  
  > "This fact is highlighted by their reduced *$\chi^{2}$* values, listed in Table [1](#table:PIV)." (4.1.1 Disk-like structure)
   - validation: Test with source B as centre gave chi2_red > 10; perpendicular PV cut shows no infall  
  > "resulting in *$\chi^{2}_\mathrm{red}$* values higher than 10 for both fits" (4.1.1 Disk-like structure)
4. **Derive dust and gas masses and CO abundance**: Optically thin dust mass from 0.87 mm flux; gas mass from C17O 3-2 integrated intensity; CO abundance by inverting gas-mass equation with gas-to-dust 100  
  > "The dust and gas masses are calculated from the continuum emission (Fig. [1](#fig:continuum)) and from the integrated intensity of C$^{17}$O *J*=3$-$2" (4.2 Disk mass)
   - parameter: C17O integrated over 20 km/s, 5.31 ± 0.01 Jy km/s above 5 sigma  
  > "obtaining a value of 5.31 $\pm$ 0.01 Jy km s$^{-1}$ for *S$_{\nu}$* times the velocity interval" (4.2 Disk mass)
   - assumption: Dust T=30 K, Ossenkopf & Henning opacity, gas-to-dust 100, C17O/CO=4.5e-4 and CO/H2=2.7e-4  
  > "By assuming a C$^{17}$O abundance with respect to CO of 4.5 $\times$ 10$^{-4}$ (cite: Penzias1981)" (4.2 Disk mass)
   - fitting: _not stated_
   - validation: CO abundance compared to canonical 2.7e-4 across temperatures  
  > "We note that for all of the temperatures used in the calculations, CO abundances are comparable to the canonical value of 2.7 $\times$ 10$^{-4}$." (4.2 Disk mass)
5. **Estimate optical depth, column densities and abundances**: Non-LTE RADEX at source B, n(H2)=1e7 cm-3, Tkin=30 and 100 K, b=FWHM; abundance ratios vs CO compared with IRAS 16293  
  > "assuming a H$_{2}$ number density of 1 $\times$ 10$^{7}$ cm$^{-3}$ (collision partner), two kinetic temperatures (*T$_\mathrm{kin}$*) of 30 and 100 K" (4.3 Fits and abundances)
   - software: RADEX
   - assumption: Standard isotope ratios 16O/17O=2005, 12C/13C=69  
  > "Assuming standard isotope ratios for C$^{17}$O ($^{16}$O/$^{17}$O = 2005) and H$^{13}$CO$^{+}$ ($^{12}$C/$^{13}$C = 69) from (cite: Wilson1999)." (Table of abundances notes)
   - fitting: _not stated_
   - validation: Density varied by factor of 10 to test column density sensitivity  
  > "If we change the H$_{2}$ density by a factor of 10, the C$^{17}$O column density remains constant" (4.3 Fits and abundances)

## Software

- **CASA** : Calibration, imaging, imfit  
  > "The calibration and imaging were done in CASA" (2 Observations)
- **RADEX** : Non-LTE optical depth and column densities  
  > "The statistical equilibrium radiative transfer code (cite: vanderTak2007) is used to estimate the optical depth ($\tau$) and column densities" (4.3 Fits and abundances)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Circumbinary disk deconvolved continuum size | 4.1'' x 0.82'' (620 x 124 AU) | ±0.2'' x ±0.05'' | arcsec | 1 | (4.1$''$ $\pm$ 0.2$''$) $\times$ (0.82$''$ $\pm$ 0.05$''$) or (620 $\pm$ 20 AU) $\times$ (124 $\pm$ 7 AU) |
| Flux of Oph-IRS67B | 155 | ±4 | mJy | 1 | Oph-IRS67B / 16$^\mathrm{h}$32$^\mathrm{m}$00.978$^\mathrm{s}$ $\pm$ 0.001$^\mathrm{s}$ / $-$24$^\circ$56$'$43.44$''$ $\pm$ 0.01$''$ / 155 $\pm$ 4 |
| Flux of Oph-IRS67A | 30 | ±3 | mJy | 1 | 30 $\pm$ 3 |
| A-B separation | 0.71'' (107 AU) | ±0.01'' (±2 AU) | arcsec | 1 | The separation between sources A and B is 0.71$''$ $\pm$ 0.01$''$ (107 $\pm$ 2 AU). |
| Keplerian central mass | 2.2 | ±0.2 | Msun | 3 | C$^{17}$O / Keplerian / 2.2 $\pm$ 0.2 / 3.3 |
| Infalling central mass for c-C3H2 | 3.6 | ±0.3 | Msun | 3 | the central mass associated with the infalling fit is 3.6 $\pm$ 0.3 M$_{\odot}$ |
| Total mass at 30 K | 1.1e-2 | not stated | Msun | 4 | a value of 1.1 $\times$ 10$^{-2}$ *M$_{\odot}$* is obtained for the total mass |
| Dust mass at 30 K | 1.1e-4 | not stated | Msun | 4 | a dust mass of 1.1 $\times$ 10$^{-4}$ *M$_{\odot}$* is derived |
| C17O column density (30 K) | 2.0e16 | not stated | cm-2 | 5 | C$^{17}$O *J*=3$-$2 / Central / 30 / 2.4 / 0.76 / 2.0 $\times$ 10$^{16}$ |
| CH3OH column density upper limit | <1.6e14 | not stated | cm-2 | 5 | \< 1.6 $\times$ 10$^{14}$ |

## Qualitative findings

- C2H and c-C3H2 trace a high-density region offset ~430 AU, enriched in carbon chain molecules; SO2 compact only around source B  
  > "Two further molecular species, C$_{2}$H and c$-$C$_{3}$H$_{2}$, trace a higher-density region which is spatially offset from the sources ($\sim$430 AU)." (abstract)

## Claim tuples

- H: A circumbinary disk surrounds Oph-IRS67AB | E: Continuum and C17O/H13CO+ kinematics with PV fits | R: Flattened 620 AU structure; Keplerian fit gives 2.2 Msun, but infall fit not excluded | F: Circumbinary disk detected, Keplerian on <200 AU scales | **supported**
- H: CO is frozen out in the disk midplane | E: Compare CO abundance from C17O and dust mass with canonical value | R: Abundances comparable to 2.7e-4 at all temperatures | F: No significant CO freeze-out | **supported**
- H: Complex organics such as methanol are present | E: Search for CH3OH 7k-6k and RADEX upper limit | R: No emission; abundance < 1e-10-1e-9 | F: Low methanol consistent with extended disk flattening density profile | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: High-density region as centrifugal barrier rejected because infall mass inconsistent; outflow cavity, spiral arms, infalling envelope remain possible  
  > "thus a centrifugal barrier cannot explain the presence of the high-density region in Oph-IRS67." (5.1 Structure of Oph-IRS67)
- How they decided it was enough: _not stated_
- Limitation (authors): Neither Keplerian nor infalling fit can be discarded from the PV analysis  
  > "but neither of them can be discarded by this PV analysis" (4.1.1 Disk-like structure)
- Caveat (inferred, ours): PV fits use imfit peaks with reduced chi2 of 3-15, so Keplerian versus infall is weakly constrained
- Caveat (inferred, ours): Masses depend on assumed dust temperature, opacity, isotopic ratios and gas-to-dust ratio
- Caveat (inferred, ours): RADEX abundances at one density and temperature; SO2 poorly constrained
- Caveat (inferred, ours): Single configuration with limited uv coverage; flux recovery not discussed

## Reproducibility

- Data public (paper): Project code given; ALMA archive data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00955.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: Line-free channels and continuum subtraction
- Missing: PV fitting details
- Data volume (inferred): ~20-50 GB for the four sessions
- Score (inferred): 3/5, Data public and analysis simple, but imaging and fitting settings are missing.
- Rediscovery candidate: yes, Public data and numeric results such as continuum fluxes and central mass, though imaging details must be chosen.

## Links

- Method: (cite: vanderTak2007) (RADEX non-LTE code)
- Companion: (cite: Lindberg2014) (Methanol comparison in R CrA IRS7B)
- Companion: (cite: Brinch2016) (Circumbinary disk in IRS 43)
- Related: Spitzer c2d legacy program
- Related: ALMA program 2013.1.00955.S survey of 12 Class I protostars in Ophiuchus

## Checks

```json
{
 "quotes": 62,
 "quotes_ok": 62,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 40,
  "rate": 0.541
 },
 "evidence_ok": true
}
```

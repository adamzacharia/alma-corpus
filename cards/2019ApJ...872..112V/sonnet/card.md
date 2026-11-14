# Protoplanetary Disk Rings and Gaps across Ages and Luminosities

`2019ApJ...872..112V` | The Astrophysical Journal 2019 | first author: van der Marel, Nienke | arXiv: 1901.03680 | DOI: 10.3847/1538-4357/aafd31

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: Do gap/ring locations in 16 multi-ring protoplanetary disks relate to snow lines, planet resonances, age or luminosity, and how do outer radii evolve?  
  > "We aim here to compare the ring and gap locations with the stellar radiation field, disk age and disk mass to understand their common origin." (Introduction)
- Target **16 ring disks (AA Tau, AS 209, DM Tau, Elias 24, GY 91, HD 100546, HD 135344B, HD 163296, HD 169142, HD 97048, HL Tau, RXJ 1615.3-3255, Sz 98, TW Hya, V1094 Sco, V1247 Ori)**: coordinates Table 1 lists RA/Dec for each target (e.g. AA Tau 04:34:55.427 +24:28:52.687)  
  > "| AA Tau | 04:34:55.427 | +24:28:52.687 | 2013.1.01070 | Loomis | 6 | 1 | 0.20$\times$0.13 | 27$\times$18 |" (Table 1); "Distances have been taken from the *Gaia* Data Release 2 (cite: Gaia2018)." (Distances and ages); z/distance 60.1 pc (TW Hya) to 398 pc (V1247 Ori), Table 2  
  > "| AA Tau | 04:34:55.427 | +24:28:52.687 | 2013.1.01070 | Loomis | 6 | 1 | 0.20$\times$0.13 | 27$\times$18 |" (Table 1); "Distances have been taken from the *Gaia* Data Release 2 (cite: Gaia2018)." (Distances and ages); distance from Gaia DR2; VLBA for HL Tau; Ophiuchus average for GY 91  
  > "| AA Tau | 04:34:55.427 | +24:28:52.687 | 2013.1.01070 | Loomis | 6 | 1 | 0.20$\times$0.13 | 27$\times$18 |" (Table 1); "Distances have been taken from the *Gaia* Data Release 2 (cite: Gaia2018)." (Distances and ages)

## Data provenance

- ALMA projects: 2011.0.00724.S, 2012.1.00870.S, 2016.1.01239.S
- bands: Band 6 or 7 mostly (1.3 mm or 870 um); Band 9 for RXJ1615.3-3255  
  > "either Band 6 or 7, 1.3 mm or 870 $\mu$m" (Sample)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beams 0.03" to 0.48"; mostly ~20-30 AU  
  > "Beam sizes range between 0.03" and 0.48"." (ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: images obtained from PIs and in a few cases the ALMA archive  
  > "The ALMA continuum images have been obtained from the PIs and in a few cases from the ALMA archive." (ALMA observations)
- Other facility **Gaia DR2**: distances  
  > "Distances have been taken from the *Gaia* Data Release 2 (cite: Gaia2018)." (Distances and ages)
- Other facility **VLBA**: HL Tau distance  
  > "we use instead the VLBA derived distance for HL Tau of 147.3 $\pm$0.5 pc (cite: Galli2018)" (Distances and ages)
- External data: Disk inclinations and position angles  
  > "Inclinations and position angles are taken from the literature and listed in Table [3](#tbl:imageprops)." (Analysis) [from literature (Table 1 refs)]
- External data: Spectral types  
  > "Spectral types have been taken from the literature." (Distances and ages) [from Table 2 refs]
- External data: Gas outer radii from 12CO  
  > "Table [5](#tbl:outer) lists gas outer radii of most of our sample based on $^{12}$CO observations as reported in the literature." (Outer radius) [from Table 5 refs]

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
- final beam: HL Tau, TW Hya, V1247 Ori convolved with 20 AU beam  
  > "In the subsequent analysis, these three images are convolved with a 20 AU beam." (ALMA observations)
- final rms: _not stated_

### Inherited from earlier work

- Enhanced imaging representation (EIR) technique  
  > "the images are first produced using the enhanced imaging representation (cite: vanderMarel2018-hd16), a variant of unsharp masking." (Analysis) [from (cite: vanderMarel2018-hd16)]
- Disk mass relations  
  > "using the relations presented in (cite: Cieza2008), following (cite: AndrewsWilliams2007oph)" (Analysis) [from (cite: Cieza2008); (cite: AndrewsWilliams2007oph)]
- DALI model parametrization  
  > "with the code DALI (cite: Bruderer2013) following the parametrization as described in (cite: Andrews2011)" (Snow lines) [from (cite: Andrews2011)]

### Not stated but needed to reproduce (our reading)

- Imaging/calibration details of each dataset (images taken from PIs)
- Exact weighting/robust per image
- Per-target DALI surface density and vertical parameters
- Disk-fit starting guesses and uncertainties on gap parameters
- Which images were obtained from PI vs archive

## Analysis recipe

1. **Stellar properties and ages**: Fit NIR photometry to Kurucz models for L* and A_V; interpolate Siess and Baraffe tracks for age/mass  
  > "Near infrared photometry data (0.8-2.2 $\mu$m) were fit to Kurucz models (cite: CastelliKurucz2004)" (Distances and ages)
   - parameter: R_V=3.1; Teff uncertainty 100 K  
  > "An uncertainty of 100 K is adopted for the effective temperature." (Distances and ages)
   - fitting: _not stated_
   - validation: _not stated_
2. **Enhanced image representation and profiles**: Divide normalized image by version convolved with 2x beam; deproject and azimuthally average  
  > "the normalized image is convolved with a beam 2 times larger than the original beam, and the original is divided by this convolved image." (Analysis)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit gap locations**: chi2 minimization of power-law I(r) with empty gaps, convolved with beam  
  > "The intensity profile is fit using a $\chi^2$ minimization with a power-law profile $I(r) = (r/r_c)^{-\gamma}$" (Analysis)
   - parameter: gamma free 0-1; gap center/width varied in 1 AU steps; 4-8 free parameters  
  > "varied in steps of 1 AU for the $\chi^2$ minimization." (Analysis)
   - fitting: chi2 minimization grid in 1 AU steps  
  > "varied in steps of 1 AU for the $\chi^2$ minimization." (Analysis)
   - validation: Compared with literature gap parameters  
  > "we find a good correspondence between our parameters and those derived in the literature" (Analysis)
4. **Disk temperature and snow lines**: DALI radiative transfer per disk fit to SED and mm flux; compare gap radii with freeze-out temperature radii  
  > "The midplane dust temperature of each radiative transfer model provides a way to locate the approximate radii where a snow line is expected." (Snow lines)
   - software: DALI
   - parameter: freeze-out T: N2 13.5 K, CO 25.5 K, CH4 29 K, CO2 66 K, NH3 80 K  
  > "N$_2$ (13.5 K), CO (25.5 K), CH$_4$ (29 K), CO$_2$ (66 K) and NH$_3$ (80 K)" (Snow lines)
   - assumption: only inner cavities included in surface density, not outer gaps  
  > "only the inner dust cavities are included in the surface density model where applicable, not the gaps further out" (Snow lines)
   - fitting: _not stated_
   - validation: _not stated_
5. **Disk masses**: Convert mm flux to mass  
  > "assuming a disk temperature of 20 K, a dust opacity $\kappa_{\nu}$=10 cm$^2$ g$^{-1}$ at 1000 GHz" (Analysis)
   - assumption: T=20 K, kappa=10 cm2/g at 1000 GHz, beta=1, gas-to-dust 100  
  > "a dust opacity law coefficient $\beta$=1 (considering $\kappa_{\nu}\sim\nu^{\beta}$) and a gas-to-dust ratio of 100." (Analysis)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **DALI** : dust radiative transfer temperature profiles  
  > "we have run a dust radiative transfer model for each disk, using the stellar properties in Table [2](#tbl:stellar), with the code DALI (cite: Bruderer2013)" (Snow lines)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean outer radius of 12 young disks | 178 | 48 | AU | 3 | the mean outer radius of the 12 young disks is 178$\pm$48 AU |
| Mean outer radius of 4 oldest disks | 79 | 17 | AU | 3 | for the 4 oldest disks it is 79$\pm$17 AU |
| Average disk mass | 55 | not stated | M_Jup | 5 | average disk mass of 55 $M_{\rm Jup}$ |
| Mdisk/M* | ~5±3 | 3% | percent | 5 | typical $M_{\rm disk}/M_*$ of only $\sim5\pm3$% |

## Qualitative findings

- Gap radii do not correspond to snow line radii; no trends with age/luminosity; no systematic resonance ratios  
  > "The gap radii generally do not correspond to the orbital radii of snow lines of the most common molecules." (abstract)

## Claim tuples

- H: Snow lines explain gap locations | E: Compare gap radii with freeze-out radii from DALI temperature profiles | R: No general trend | F: Snow line model discarded as common origin | **supported**
- H: Gap positions follow planet resonances | E: Gap center ratios to power 3/2 | R: Less than one third near first-order resonances | F: No systematic resonance trend | **supported**
- H: Outer dust radius evolves with age | E: Compare fitted outer radii of young vs oldest disks | R: 178 vs 79 AU | F: Outer rings disappear with gas or become planetesimal belts | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Large sample with uniform analysis needed to understand origin  
  > "In order to understand the origin of the rings, a large sample and a uniform analysis are required." (Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Method ignores gap depth and absolute intensity; sample biased  
  > "Clearly this method does not account for depth of the gap or absolute intensity variations, it is only a way to quantify the gap locations." (Analysis)
- Caveat (inferred, ours): Ages highly uncertain
- Caveat (inferred, ours): Resolution-limited (20-30 AU) gap detection may bias results
- Caveat (inferred, ours): No uncertainties on gap fits
- Caveat (inferred, ours): Inhomogeneous imaging across datasets
- Caveat (inferred, ours): Small, biased sample

## Reproducibility

- Data public (paper): Archival ALMA data, some images from PIs  
  > "The ALMA continuum images have been obtained from the PIs and in a few cases from the ALMA archive." (ALMA observations)
- Products in archive: _not stated_
- Missing: Reduced images supplied by PIs
- Missing: DALI model parameters per disk
- Missing: Imaging parameters
- Data volume (inferred): ~100s GB raw for 16 datasets if re-imaged; small if using images
- Score (inferred): 3/5, Simple method but images are PI-provided and models underspecified.
- Rediscovery candidate: no, Inputs are processed PI images and per-disk model parameters are unstated.

## Links

- Method: (cite: vanderMarel2018-hd16) (Enhanced image representation)
- Method: (cite: Bruderer2013) (DALI code)
- Companion: (cite: Long2018) (Similar snow line conclusion for Taurus)
- Companion: (cite: Huang2018) (DSHARP snow line conclusion)
- Related: DSHARP

## Checks

```json
{
 "quotes": 47,
 "quotes_ok": 47,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00015.SV",
  "2012.1.00158.S",
  "2012.1.00799.S",
  "2013.1.00498.S",
  "2013.1.00601.S",
  "2013.1.00647.S",
  "2013.1.00658.S",
  "2013.1.01070.S",
  "2015.1.00222.S",
  "2015.1.00486.S",
  "2015.1.00678.S",
  "2015.1.00686.S",
  "2015.1.00761.S",
  "2015.1.00986.S",
  "2016.1.00344.S"
 ],
 "codes_printed_but_missing": [
  "2011.0.00015.SV",
  "2012.1.00158.S",
  "2012.1.00799.S",
  "2013.1.00498.S",
  "2013.1.00601.S",
  "2013.1.00658.S",
  "2013.1.01070.S",
  "2015.1.00222.S",
  "2015.1.00486.S",
  "2015.1.00678.S",
  "2015.1.00686.S",
  "2015.1.00761.S",
  "2015.1.00986.S",
  "2016.1.00344.S"
 ],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 33,
  "rate": 0.446
 },
 "evidence_ok": true
}
```

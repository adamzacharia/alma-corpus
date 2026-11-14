# Star Formation and ISM Properties in the Host Galaxies of Three Far-infrared Luminous Quasars at z ∼ 6

`2019ApJ...876...99S` | The Astrophysical Journal 2019 | first author: Shao, Yali | arXiv: 1903.01105 | DOI: 10.3847/1538-4357/ab133d

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: What are the molecular gas masses (from VLA CO(2-1)) and the dust/SFR/ISM properties of three FIR-luminous z~6 quasar hosts, using ALMA and Herschel continuum for J2310+1855?  
  > "In this paper, we report VLA observations of CO (2$-$1) line emission in three FIR-luminous high redshift quasars" (1 Introduction)
- Target **J2310+1855**: coordinates SDSS J231038.88+185519.7  
  > "SDSS J231038.88$+$185519.7 (hereafter J2310$+$1855 at $z =$ 6.0)" (1 Introduction); z/distance z = 6.0029 ± 0.0005 (CO 2-1)  
  > "SDSS J231038.88$+$185519.7 (hereafter J2310$+$1855 at $z =$ 6.0)" (1 Introduction); distance from CO(2-1) fit; ALMA [CII] z=6.0031 from Wang et al. 2013  
  > "SDSS J231038.88$+$185519.7 (hereafter J2310$+$1855 at $z =$ 6.0)" (1 Introduction)
- Target **J0129-0035**: coordinates SDSS J012958.51-003539.7  
  > "SDSS J012958.51$-$003539.7 (hereafter J0129$-$0035 at $z =$ 5.7)" (1 Introduction); z/distance z = 5.7783 ± 0.0004 (CO 2-1)  
  > "SDSS J012958.51$-$003539.7 (hereafter J0129$-$0035 at $z =$ 5.7)" (1 Introduction); distance from CO(2-1) Gaussian fit  
  > "SDSS J012958.51$-$003539.7 (hereafter J0129$-$0035 at $z =$ 5.7)" (1 Introduction)
- Target **J2054-0005**: coordinates SDSS J205406.42-000514.8  
  > "SDSS J205406.42$-$000514.8 (hereafter J2054$-$0005 at $z =$ 6.0)" (1 Introduction); z/distance z = 6.0394 ± 0.0004 (CO 2-1)  
  > "SDSS J205406.42$-$000514.8 (hereafter J2054$-$0005 at $z =$ 6.0)" (1 Introduction); distance from CO(2-1) Gaussian fit  
  > "SDSS J205406.42$-$000514.8 (hereafter J2054$-$0005 at $z =$ 6.0)" (1 Introduction)

## Data provenance

- ALMA projects: 2015.1.01265.S
- bands: ALMA Bands 4 and 6 (~140 and ~300 GHz); VLA Ka band  
  > "The observations were carried out using Bands 4 and 6 with spatial resolutions of 0$\ensuremath{''}$42 to 0$\ensuremath{''}$65 with 36$-$44 12-m antennas." (2.3 ALMA)
- frequencies and spectral setup: One 2 GHz spw on the line, three on continuum  
  > "One of the 2 GHz spectral windows was tuned on the line and the other three on the continuum." (2.3 ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.42-0.65 arcsec (ALMA)  
  > "spatial resolutions of 0$\ensuremath{''}$42 to 0$\ensuremath{''}$65" (2.3 ALMA)
- max recoverable scale: _not stated_
- sensitivity: 0.02-0.04 mJy/beam (dust maps)  
  > "The noise levels of the dust maps are 0.02$-$0.04 mJy beam$^{-1}$." (2.3 ALMA)
- time on source: 5.5 h and 3.4 h (Band 4, Band 6 respectively, as stated)  
  > "The on-source observation time was 5.5 hours and 3.4 hours, respectively." (2.3 ALMA)
- observing dates: _not stated_
- pi or archival as stated: PI Ran Wang  
  > "program ID: 2015.1.01265.S; PI: Ran Wang" (2.3 ALMA)
- Line: CO 2-1 (VLA) (230.538 GHz)
- Other facility **VLA**: CO(2-1) line cubes, Ka band, C and D configs  
  > "The CO (2$-$1) observations were performed using the Ka band receivers (centered at 32 GHz) of the VLA." (2.1 VLA)
- Other facility **Herschel PACS/SPIRE**: FIR photometry 100-500 um  
  > "Herschel SPIRE observations towards J2310$+$1855 and J0129$-$0035 were carried out at 250, 350, and 500 $\mu$m" (2.2.2 SPIRE)
- External data: CO(6-5) and [CII] redshifts, widths, fluxes  
  > "CO (6$-$5) information comes from (cite: Wang2010) and (cite: Wang2011fir), and \[C ii\] information is from (cite: Wang2013)." (Table 2) [from (cite: Wang2010); (cite: Wang2011fir); (cite: Wang2013)]
- External data: Literature photometry (SDSS, WISE, ALMA 91.5/496/263 GHz, IRAM 250 GHz)  
  > "$^{i}$(cite: Feruglio2018); $^{j}$(cite: Hashimoto2018)." (Table 3) [from (cite: Wang2013); (cite: Feruglio2018); (cite: Hashimoto2018); (cite: Leipski2014)]
- Simulation/model as data: PDR model grid of Kaufman et al. 1999, 2006 via PDR Toolbox  
  > "These models can be recreated using the PDR Toolbox (PDRT" (4.3 The Characteristics of the ISM)

## Processing

### Calibration

- pipeline or manual: CASA pipeline (ALMA)  
  > "We reduced the data with the CASA pipeline." (2.3 ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Pallas (ALMA); 3C286 and 3C48 (VLA)  
  > "The phase and flux calibrators were J2253+1608 and Pallas." (2.3 ALMA)
- flux scale uncertainty: better than 10%  
  > "The flux density scale calibration accuracy is better than 10$\%$." (2.3 ALMA)
- self calibration: _not stated_

### Imaging

- task: CLEAN (VLA)  
  > "The final data cubes were reduced by the CLEAN task" (2.1 VLA)
- deconvolver: _not stated_
- weighting robust: robust 0.5 (VLA cubes)  
  > "using a robust weighting factor of 0.5" (2.1 VLA)
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
- final rms: 0.02-0.04 mJy/beam (ALMA continuum)  
  > "The noise levels of the dust maps are 0.02$-$0.04 mJy beam$^{-1}$." (2.3 ALMA)

### Inherited from earlier work

- Photometric uncertainty method for Herschel  
  > "We followed (cite: Leipski2013; Leipski2014) to determine the photometric uncertainties" (2.2.1 PACS) [from (cite: Leipski2013; Leipski2014)]
- SED fitting method  
  > "based on the method in (cite: Leipski2013; Leipski2014)" (4.2) [from (cite: Leipski2013; Leipski2014)]
- Upper-limit likelihood  
  > "we follow (cite: Shangguan2018) to create a likelihood function for the flux upper limits" (4.2) [from (cite: Shangguan2018)]

### Not stated but needed to reproduce (our reading)

- ALMA CASA/pipeline version
- ALMA imaging parameters (weighting, cell, size, deconvolver)
- VLA CASA version, channel width, cube velocity resolution
- MCMC walkers, steps, priors for SED fit
- How ALMA flux densities were measured (Gaussian fit region, spw frequencies)
- Which ALMA execution blocks were used

## Analysis recipe

1. **Measure ALMA continuum flux densities**: 2D Gaussian fits to continuum maps at 140 and 300 GHz  
  > "The continuum flux densities using 2D Gaussian fits to the ALMA continuum maps at 140 GHz and 300 GHz are listed in Table [3]" (3.1 J2310+1855)
   - software: CASA
   - fitting: _not stated_
   - validation: ALMA 263 GHz compared with IRAM 250 GHz, consistent, so flux loss ignored  
  > "By comparing two flux density measurements in two similar bands - ALMA 263 GHz and IRAM 250 GHz, we find consistent values" (4.2)
2. **SED fit of J2310+1855**: UV/optical power law + CAT3D torus + MBB (beta=1.6) or Draine&Li 2007 dust model; CMB correction  
  > "We use the $emcee$ package (cite: emcee2013) to do SED fit to the emission from both star formation and the central AGN" (4.2)
   - software: emcee
   - parameter: beta fixed at 1.6  
  > "fixed emissivity index $\beta$ of 1.6" (4.2)
   - assumption: kappa_125um = 18.75 cm2/g; Salpeter IMF with Kennicutt 1998 SFR  
  > "Assuming a Salpeter IMF and adopting Equation 4 in (cite: Kennicutt1998)" (4.2)
   - fitting: emcee MCMC; upper-limit likelihood following Shangguan 2018  
  > "we follow (cite: Shangguan2018) to create a likelihood function for the flux upper limits." (4.2)
   - validation: two FIR scenarios give consistent T~40 K  
  > "The two scenarios both give a consistent dust temperature $\sim40$ K." (4.2)

## Software

- **CASA** : VLA and ALMA reduction, CLEAN  
  > "The data were reduced using the Common Astronomy Software Application (CASA" (2.1 VLA)
- **HIPE** 15.0.1: Herschel reduction and photometry  
  > "Herschel Interactive Processing Environment (HIPE; version 15.0.1" (2.2.1 PACS)
- **emcee** : SED fitting  
  > "We use the $emcee$ package (cite: emcee2013) to do SED fit" (4.2)
- **PDR Toolbox** : PDR models  
  > "These models can be recreated using the PDR Toolbox (PDRT" (4.3)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| J2310+1855 dust temperature (MBB) | 39-40 | +3/-2 | K | 2 | 39$_{-3}^{+3}$ / 40$_{-2}^{+3}$ |
| J2310+1855 SFR (MBB) | 2400-2700 | +500/-400 | Msun/yr | 2 | we derive SFRs of 2400$-$2700 $M_{\odot}$ yr$^{-1}$ |
| J2310+1855 dust mass (MBB) | 1.6-1.7e9 | +0.4/-0.3 | Msun | 2 | We estimate dust masses (1.7 and 1.6 $\times$ 10$^{9} M_{\odot}$ |
| J2310+1855 CO(2-1) gas mass | 4.3e10 | 0.4e10 | Msun | 0 | (4.3 $\pm$ 0.4) $\times$ 10$^{10}$ $M_{\odot}$ |
| ALMA 295 GHz flux J2310+1855 | 11.56 | 0.10 | mJy | 1 | $F_{295\rm GHz}$ (mJy) / ALMA / **11.56 $\pm$ 0.10** |

## Qualitative findings

- CO(2-1) redshifts and widths consistent with CO(6-5) and [CII]  
  > "consistent with previous CO (6$-$5) and \[C II\] measurements" (abstract)

## Claim tuples

- H: Do CO(2-1) gas masses agree with CO(6-5)-based ones? | E: VLA CO(2-1) with alpha_CO=0.8 | R: Gas masses (0.8-4.3)e10 Msun | F: Consistent with CO(6-5) estimates | **supported**
- H: Dust properties of J2310+1855 | E: SED fit of Herschel+ALMA | R: T~40 K, Mdust~1e9, SFR 2400-2700 | F: Strong star formation | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Lack of NIR/MIR data prevents distinguishing dust models  
  > "More NIR and MIR data would allow us to distinguish these models." (4.2)
- Caveat (inferred, ours): SED model degeneracies; FIR luminosity differs 2x between dust models
- Caveat (inferred, ours): ALMA flux loss assumed negligible

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA imaging settings
- Missing: MCMC priors
- Data volume (inferred): ~100 GB
- Score (inferred): 2/5, ALMA part is minor and imaging details are sparse.
- Rediscovery candidate: no, Recipe incomplete for ALMA part; main results mostly VLA.

## Links

- Companion: Li et al. in preparation (ALMA line data from the same program)

## Checks

```json
{
 "quotes": 54,
 "quotes_ok": 54,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 43,
  "rate": 0.606
 },
 "evidence_ok": true
}
```

# Detection of Coronal Magnetic Activity in nearby Active Supermassive Black Holes

`2018ApJ...869..114I` | The Astrophysical Journal 2018 | first author: Inoue, Yoshiyuki | arXiv: 1810.10732 | DOI: 10.3847/1538-4357/aaeb95

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars
- Question: Can coronal synchrotron emission (mm excess) from nearby Seyferts be detected with multi-band ALMA plus cm data, and what coronal magnetic field strength and electron distribution does it imply?  
  > "Here we report the detection of coronal radio synchrotron emission from two nearby Seyfert galaxies using the Atacama Large Millimeter/submillimeter Array, the Karl G. Jansky Very Large Array, and Australia Telescope Compact Array." (abstract)
- Target **IC 4329A**: coordinates 13h49m19.26170s, -30d18m34.22145s (J2000)  
  > "IC 4329A is a southern Seyfert 1.2 galaxy at $z=0.0161$ (cite: wil91)" (2.1 Target objects); z/distance z=0.0161  
  > "IC 4329A is a southern Seyfert 1.2 galaxy at $z=0.0161$ (cite: wil91)" (2.1 Target objects); distance from Willmer et al. 1991 (cite: wil91)  
  > "IC 4329A is a southern Seyfert 1.2 galaxy at $z=0.0161$ (cite: wil91)" (2.1 Target objects)
- Target **NGC 985**: coordinates 02h34m37.84028s, -08d47m16.07808s (J2000)  
  > "NGC 985 is a southern Seyfert 1 galaxy at $z=0.0427$ (cite: Fisher1995)" (2.1 Target objects); z/distance z=0.0427  
  > "NGC 985 is a southern Seyfert 1 galaxy at $z=0.0427$ (cite: Fisher1995)" (2.1 Target objects); distance from Fisher et al. 1995 (cite: Fisher1995)  
  > "NGC 985 is a southern Seyfert 1 galaxy at $z=0.0427$ (cite: Fisher1995)" (2.1 Target objects)

## Data provenance

- ALMA projects: 2016.1.01140.S
- bands: Band 3, 4, 6  
  > "using the ALMA Band 3,  4, and 6 receivers" (2.2 Radio observations with ALMA)
- frequencies and spectral setup: 4 SPWs of 2.000 GHz per band; centers 90.5/92.4/102.5/104.5, 138.0/139.9/150.0/152.0, 213.0/215.0/229.0/231.0 GHz; TDM, 128 channels per SPW  
  > "Four spectral windows (SPWs) with a bandwidth of 2.000 GHz were placed at sky frequencies centered at 90.5 GHz, 92.4 GHz, 102.5 GHz, and 104.5 GHz in Band 3" (2.2 Radio observations with ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: synthesized beams from ~0.45 arcsec (Band 3) to ~0.1 arcsec (Band 6)  
  > "| 90.5  | $8.00\pm0.49$     | $0.094$    | $0.45  \times 0.44$                              | $-25.3$  | 2016-10-02 |" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: IC 4329A 2016-10-02; NGC 985 2017-08-18  
  > "We observed IC 4329A and NGC 985 on October 2nd, 2016 and August 18th, 2017, respectively" (2.2 Radio observations with ALMA)
- pi or archival as stated: PI Y. Inoue (new ALMA observations)  
  > "project-ID: $\#$2016.1.01140.S, PI = Y. Inoue" (2.2 Radio observations with ALMA)
- Other facility **VLA**: archival cm data  
  > "We retrieved archival data obtained using the VLA and the ATCA" (2.3)
- Other facility **ATCA**: archival cm data  
  > "We retrieved archival data obtained using the VLA and the ATCA" (2.3)
- Other facility **NuSTAR**: archival hard X-ray spectrum of NGC 985 for coronal temperature and optical depth  
  > "For NGC 985, we analyze archival *NuSTAR* data in order to derive coronal properties." (2.4)
- Other facility **NVSS**: 1.4 GHz images  
  > "We also retrieved and analyzed the 1.4-GHz images from the NRAO VLA Sky Survey" (2.3)
- External data: IC 4329A coronal temperature 50 keV and Thomson optical depth 2.34  
  > "They found that the coronal temperature and the Thomson scattering optical depth are 50 keV and 2.34, respectively, assuming a spherical geometry." (2.4) [from (cite: brenneman2014b)]
- External data: Previous VLA results for NGC 985  
  > "Additionally, we used the results of previous VLA studies for NGC 985 (cite: doi2016)." (2.3) [from (cite: doi2016)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline scripts from regional center  
  > "We reduced raw data using pipeline scripts provided by the ALMA regional center." (2.2)
- casa version: CASA 4.7.0  
  > "ALMA reduction package `CASA` version 4.7.0" (2.2)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: IC 4329A: J1427-4206; NGC 985: J0238+1636 (Bands 3,4), J0334-4008 (Band 6)  
  > "the flux scaling factors were determined with reference to the quasar J0238+1636 at Bands 3 and 4, and J0334-4008 at Band 6." (2.2)
- flux scale uncertainty: 5% Bands 3,4; 10% Band 6  
  > "5% for Bands 3 and 4, and 10% for Band 6 following the ALMA Proposer’s Guide" (2.2)
- self calibration: _not stated_

### Imaging

- task: visibilities exported per SPW, mapped and CLEANed; fluxes via IMFIT Gaussian fit  
  > "The flux measurements were performed by a Gaussian fit using the `CASA` task `IMFIT`." (2.2)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "processed for mapping and CLEANing using natural weighting" (2.2)
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
- final rms: 0.037-0.16 mJy/beam  
  > "Col. (3) image r.m.s. noise in the blank sky" (Table 1)

### Inherited from earlier work

- Hybrid corona synchrotron model  
  > "synchrotron emission from a hybrid corona (cite: inoue2014)" (3 Results) [from (cite: inoue2014)]
- NuSTAR analysis procedure followed from IC 4329A analysis  
  > "we followed the analysis procedure of IC 4329A (cite: brenneman2014a)" (2.4) [from (cite: brenneman2014a)]
- Non-thermal energy fraction eta=4%  
  > "This value is inferred from the explanation of the cosmic MeV gamma-ray background radiation by Seyferts (cite: Inoue2008)." (3 Results) [from (cite: Inoue2008)]

### Not stated but needed to reproduce (our reading)

- Fitting algorithm, priors and likelihood for the SED fit
- Image sizes, cell sizes, CLEAN masks and thresholds
- Pipeline version
- Implementation of the hybrid corona model
- Black hole mass and distance adopted in the fit
- Details of the VLA/ATCA data sets used and their calibrators

## Analysis recipe

1. **Measure ALMA continuum fluxes**: Per-SPW natural-weighted CLEAN images; Gaussian fit with IMFIT  
  > "The flux measurements were performed by a Gaussian fit using the `CASA` task `IMFIT`." (2.2)
   - software: CASA
   - fitting: _not stated_
   - validation: Calibrator flux stability checked in ALMA calibrator database  
  > "We queried the ALMA calibrator database to make the assurance doubly sure." (2.2)
2. **Measure VLA/ATCA fluxes**: Standard reduction with AIPS or Miriad, natural weighting, JMFIT Gaussian fit; star-forming western component subtracted for NVSS and AB417  
  > "The source identification was performed by Gaussian model fitting on each image using the `AIPS` task `JMFIT`." (2.3)
   - software: AIPS, Miriad
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive X-ray coronal parameters for NGC 985**: NuSTAR 5-79 keV spectral fit with pexmon then compTT plus pexmon reflection  
  > "we employed the `compTT` model (cite: Titarchuk1994), which calculates the Comptonization spectra." (2.4)
   - software: NuSTARDAS, nupipeline, nuproducts, pexmon, compTT
   - assumption: solar abundances, inclination 60 deg, NH=3.17e20 cm^-2  
  > "We fixed the abundance of elements to the solar abundances, the inclination angle of $i=60^\circ$" (2.4)
   - fitting: _not stated_
   - validation: chi2/nu=191/146  
  > "with a goodness-of-fit of $\chi^2/\nu=191/146 (1.31)$" (2.4)
4. **Fit cm-mm SED with corona+jet+galactic components**: Simultaneous fit of ALMA, VLA, ATCA 1-250 GHz data with hybrid-corona synchrotron, jet power law, galactic free-free and synchrotron with beam-size dependence; free R, B, p; eta fixed at 0.04  
  > "we simultaneously fit ALMA, VLA, and ATCA measurements between 1 GHz and 250 GHz with four spectral components." (3 Results)
   - parameter: eta=0.04 fixed; free-free index 0.1, galactic synchrotron index 0.8  
  > "We fix the energy fraction $\eta$ of non-thermal electrons as 4% of that of the total electron population." (3 Results)
   - assumption: spherical corona  
  > "We adopt spherical geometry for coronae for simplicity." (3 Results)
   - fitting: _not stated_
   - validation: Varying eta 0.01-0.30 leaves B, R, p consistent within 1 sigma  
  > "Even if we vary $\eta$ from 0.01 to 0.30, the parameters $B$, $R$, and $p$ are consistent within an uncertainty of 1-$\sigma$." (3 Results)

## Software

- **CASA** 4.7.0: ALMA calibration, imaging and IMFIT  
  > "ALMA reduction package `CASA` version 4.7.0" (2.2)
- **AIPS** : VLA reduction and JMFIT  
  > "software Astronomical Image Processing System (cite: Greisen:2003)" (2.3)
- **Miriad** : ATCA reduction  
  > "using the software `Miriad` (cite: Sault:1995)" (2.3)
- **NuSTARDAS** calibration 1.4.1: NuSTAR data reduction  
  > "We reduced the data using the NuSTAR Data Analysis Software (NuSTARDAS) and calibration version 1.4.1." (2.4)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| IC 4329A coronal radius | 38.8 | 9.7 | r_s | 4 | / $R$ ($r_s$)                / $38.8\pm9.7$   / $46.9\pm20.5$  / |
| IC 4329A magnetic field | 9.42 | 6.16 | G | 4 | / $B$ (G)                    / $9.42\pm6.16$  / $4.18\pm 1.90$ / |
| IC 4329A p | 2.90 | 0.86 | dimensionless | 4 | / $p$                        / $2.90\pm0.86$  / $2.11\pm0.28$  / |
| NGC 985 R | 46.9 | 20.5 | r_s | 4 | / $R$ ($r_s$)                / $38.8\pm9.7$   / $46.9\pm20.5$  / |
| NGC 985 B | 4.18 | 1.90 | G | 4 | / $B$ (G)                    / $9.42\pm6.16$  / $4.18\pm 1.90$ / |
| NGC 985 p | 2.11 | 0.28 | dimensionless | 4 | / $p$                        / $2.90\pm0.86$  / $2.11\pm0.28$  / |
| NGC 985 coronal kTe | 29 | +5/-9 | keV | 3 | We found the coronal temperature of $kT_e=29_{-9}^{+5}~{\rm keV}$ |
| NGC 985 Thomson optical depth | 3.5 | +1.2/-0.6 | dimensionless | 3 | the Thomson scattering optical depth of $\tau=3.5_{-0.6}^{+1.2}$ |
| plasma beta | ~0.1 | not stated | dimensionless | 4 | becomes $\sim0.1$ for both objects |

## Qualitative findings

- Clear mm excess in both Seyferts; thermal dust disfavored  
  > "The mm excess is clearly visible in the cm–mm spectrum, which determines the properties of the coronae." (3 Results)

## Claim tuples

- H: Do Seyfert coronae produce compact synchrotron emission in the mm band? | E: Multi-band ALMA 90-230 GHz plus VLA/ATCA SED fitting | R: mm excess with SSA turnover near 100 GHz in both sources | F: Coronal synchrotron detected, B~10 G at ~40 r_s | **supported**
- H: Are coronae magnetically heated? | E: Compare heating and cooling rates from measured B | R: Q_B,heat ~1e10-1e11 vs Q_IC,cool ~1e14 erg/cm^2/s | F: Field too weak for magnetic heating | **supported**
- H: Are coronal electrons purely thermal? | E: Compare pure thermal vs hybrid fits | R: Pure thermal requires R~2600-3100 r_s | F: Hybrid thermal+non-thermal electrons needed | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Thermal dust and pure thermal synchrotron rejected  
  > "given the ALMA spectral shapes, the dust scenario is clearly disfavored" (4.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Eta, B and R are degenerate; eta had to be fixed  
  > "current radio data do not allow us to solve these three parameters simultaneously without decoupling thermal and non-thermal components" (3 Results)
- Caveat (inferred, ours): Only two sources
- Caveat (inferred, ours): eta fixed from the MeV background assumption
- Caveat (inferred, ours): Large B uncertainties
- Caveat (inferred, ours): Fitting procedure not described
- Caveat (inferred, ours): Non-simultaneous multi-epoch cm data

## Reproducibility

- Data public (paper): ALMA, VLA, ATCA archival data  
  > "We retrieved archival data obtained using the VLA and the ATCA" (2.3)
- Products in archive: _not stated_
- Missing: SED fit code and sampler
- Missing: Hybrid corona model implementation
- Missing: Imaging parameters
- Data volume (inferred): tens of GB
- Score (inferred): 3/5, Data public and fluxes tabulated, but the SED fitting procedure and model code are not detailed.
- Rediscovery candidate: no, Fitting method and priors are not specified.

## Links

- Method: (cite: inoue2014) (hybrid corona synchrotron model)
- Companion: (cite: doi2016) (earlier multi-band radio study of NGC 985 and mm excess)
- Related: NVSS

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
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
  "facts": 77,
  "stated": 46,
  "rate": 0.597
 },
 "evidence_ok": true
}
```

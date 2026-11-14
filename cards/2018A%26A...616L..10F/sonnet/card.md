# ALMA observations of RCW 120 Fragmentation at 0.01 pc scale&amp;star

`2018A&A...616L..10F` | Astronomy and Astrophysics 2018 | first author: Figueira, M. | arXiv: 1807.11860 | DOI: 10.1051/0004-6361/201832930

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: How do the most massive Herschel cores in Condensation 1 of the RCW 120 H II region fragment down to 0.01 pc, and can high-mass stars form there?  
  > "We want to study the fragmentation process down to the 0.01 pc scale in the most massive condensation (1700 $M_{\odot}$) observed at the south-western edge of the H  region RCW 120" (abstract)
- Target **RCW 120 Condensation 1**: coordinates _not stated_; z/distance 1.3 kpc  
  > "located 0.5$^\circ$ above the Galactic Plane at a distance of 1.3 kpc" (2 The Galactic H region RCW 120); distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00314.S
- bands: Band 3 (3 mm)  
  > "We used a continuum bandwith of 2.227 GHz in Band 3" (3 ALMA observations and data reduction)
- frequencies and spectral setup: 3x117.19 MHz + 1x1875 MHz; centered 93.17, 91.98, 104.02, 102.5 GHz  
  > "The spectral bands were centered on 93.17, 91.98, 104.02 and 102.5 GHz" (3 ALMA observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-3, 38 of 40 12 m antennas  
  > "using 38 of the 40 12 m ALMA antennas in nominal configuration C40-3 with baselines ranging from 15 m to 459 m" (3 ALMA observations and data reduction)
- baselines: _not stated_
- angular resolution: 1.7"x1.5" (0.01 pc)  
  > "synthesized beam of 1.7$''$$\times$1.5$''$ (0.01 pc at a distance of 1.3 kpc)" (3 ALMA observations and data reduction)
- max recoverable scale: 14"  
  > "The largest recoverable angular scale for these observations is 14$''$." (3 ALMA observations and data reduction)
- sensitivity: _not stated_
- time on source: 27.8 minutes total  
  > "The total observing time was 27.8 minutes" (3 ALMA observations and data reduction)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: N2H+ not stated (not stated)
- Line: CH3CN not stated (not stated)
- Line: SO2 not stated (not stated)
- Other facility **Herschel (HOBYS)**: 100-500 um maps, cores and SED properties  
  > "using the $\it{Herschel}$ observations of the OB Young Stellar objects (HOBYS) guaranteed time key program" (2 The Galactic H region RCW 120)
- Other facility **MALT90**: N2H+(1-0) velocity dispersion at 30"  
  > "observed with the MALT90 survey at a spatial resolution of 30$''$-0.18 pc" (5.1 Fragmentation)
- External data: Herschel core sample of RCW 120 (re-extracted with getimages+getsources)  
  > "The $\it{Herschel}$  cores of RCW 120 (cite: fig17) were extracted with a new method using the $\it{getimages}$ (cite: men17) and $\it{getsources}$ algorithms" (4 Results and analysis) [from Figueira et al. 2017 (cite: fig17)]
- External data: Mach number of 4 in the PDR  
  > "Assuming a Mach number of 4 in the PDR of RCW 120 (cite: tre12)" (5.1 Fragmentation) [from (cite: tre12)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Used ALMA-delivered (pipeline) products  
  > "For this work, we used the products delivered by ALMA." (3 ALMA observations and data reduction)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN in CASA  
  > "The imaging was performed with the CLEAN algorithm of CASA" (3 ALMA observations and data reduction)
- deconvolver: _not stated_
- weighting robust: Briggs, robust 0.5  
  > "using a Briggs weighting with a robust parameter of 0.5 and a primary beam limit of 20%" (3 ALMA observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum subtracted from all spectral cubes  
  > "The continuum emission was subtracted from all the spectral data cubes" (3 ALMA observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: 0.16 mJy/beam continuum; 4.6 mJy/beam for SO2 and CH3CN  
  > "a rms noise level of 0.16 mJy beam$^{-1}$ for the aggregate continuum (4 spectral windows)" (3 ALMA observations and data reduction)

### Inherited from earlier work

- Fragment dust temperature set to host core temperature  
  > "assuming that they are at the same temperature than their hosting $\it{Herschel}$ core (Louvet et al. submitted)" (4 Results and analysis) [from Louvet et al. submitted]
- Hildebrand opacity law with kappa_300um = 10 cm2/g  
  > "$\kappa _{300\mu m}=10~\rm{cm}^2~g^{-1}$ (cite: hil83)" (4 Results and analysis) [from (cite: hil83)]
- HOBYS recipe for Herschel core extraction  
  > "The $\it{Herschel}$ cores from (cite: fig17) were extracted using the $\it{getsources}$ algorithm and the HOBYS recipe (cite: tig17)." (Appendix getsources extraction) [from (cite: tig17)]

### Not stated but needed to reproduce (our reading)

- CASA version and pipeline version
- CLEAN threshold, cell and image size, deconvolver
- Flux calibrator and flux uncertainty
- Herschel maps used and SED fitting details
- Exact getimages/getsources configuration files (CDS link redacted)
- Line transitions and rest frequencies for CH3CN and SO2
- Mass of fragment detection thresholds

## Analysis recipe

1. **Extract Herschel cores**: getimages + getsources on Herschel maps; SED fit 100-500 um  
  > "The properties of the $\it{Herschel}$  cores were obtained using a Spectral Energy Distribution (SED) fitting from 100 to 500 $\mu$m" (4 Results and analysis)
   - software: getimages, getsources
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract ALMA 3 mm fragments**: getimages and getsources on the continuum image  
  > "we used $\it{getimages}$ (Version 2.171128) with the default parameters and a maximal size of the structures set to 2$''$ , and $\it{getsources}$ (Version 1.140127) with the default parameters" (Appendix getsources extraction)
   - software: getimages, getsources
   - parameter: maximal structure size 2"; default parameters  
  > "a maximal size of the structures set to 2$''$" (Appendix getsources extraction)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fragment masses and sizes**: Hildebrand optically thin formula; size = geometric mean deconvolved in quadrature with beam  
  > "The size of the fragments, computed as the geometrical mean of the major and minor angular size of the source, was deconvolved in quadrature with the beam angular resolution." (4 Results and analysis)
   - assumption: gas-to-dust ratio 100; kappa_300um=10 cm2/g with beta=2; T_dust = host core temperature; D=1.3 kpc  
  > "$R$ is the gas-to-dust ratio assumed to be equal to 100" (4 Results and analysis)
   - fitting: _not stated_
   - validation: Opacity choice gives factor 2 mass uncertainty  
  > "The choice of the opacity factor leads to a factor of 2 for the absolute mass uncertainty of the ALMA fragments" (4 Results and analysis)
4. **Compare to thermal and turbulent Jeans mass**: M_Jeans=0.6285 (T/10K)^1.5 (n/1e5)^-0.5; turbulent version with Mach 4 (Mac Low & Klessen)  
  > "$\rm{M}_{\rm{Jeans}}=0.6285\times (T_{\rm{env}}/{10K})^{1.5}\times(n_{H_2}/10^5cm^{-3})^{-0.5}$" (5.1 Fragmentation)
   - assumption: core scale 0.1 pc where not deconvolvable (upper limit on M_Jeans)  
  > "we assumed a typical scale of 0.1 pc which gives an upper limit for M$_{\rm{Jeans}}$" (5.1 Fragmentation)
   - fitting: _not stated_
   - validation: _not stated_
5. **High-mass star formation criterion**: Baldeschi et al. mass-radius threshold M>1282 r^1.42  
  > "M$_{\rm{core}}$\>1282$\left(r/[pc]\right)^{1.42}$ $M_{\odot}$" (5.2 High-mass star formation)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : CLEAN imaging  
  > "The imaging was performed with the CLEAN algorithm of CASA" (3 ALMA observations and data reduction)
- **getsources** 1.140127: source extraction and measurement  
  > "$\it{getsources}$ (Version 1.140127) with the default parameters" (Appendix getsources extraction)
- **getimages** 2.171128: background-flattened images for extraction  
  > "$\it{getimages}$ (Version 2.171128) with the default parameters" (Appendix getsources extraction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of ALMA fragments | 18 | not stated | dimensionless | 2 | we found 18 ALMA sources, called fragments, in total |
| Fraction of 3 mm emission recovered | 20 | not stated | % | 2 | we recover 20% of the emission with the ALMA 12 m observations |
| Fragment mass range | 2 to 32 | not stated | Msun | 3 | a mass ranging from 2 to 32 $M_{\odot}$ and an average of 12 $M_{\odot}$ |
| Herschel core Jeans mass range | 0.3 to 2.5 (average 0.8) | not stated | Msun | 4 | range from 0.3 $M_{\odot}$ to 2.5 $M_{\odot}$ with an average of 0.8 $M_{\odot}$ |
| Upper limit turbulent Jeans mass | 100 | not stated | Msun | 4 | we obtain an upper limit of 100 $M_{\odot}$ for the M$_{\rm{Jeans}}^{\rm{turb}}$ |
| Fragment 1 of Core 2 mass | 27.4 | 0.6 | Msun | 3 | / Core 2           / 1  / 258.0363  / -38.5129  / 27.4 $\pm$ 0.6  / 8.6        / |

## Qualitative findings

- CH3CN and SO2 emission toward Fragment 1 suggests a probable UC HII region  
  > "CH$_3$CN and SO$_2$ emission are observed towards the main fragment in the most massive core arguing for the presence of an UCH  region in the PDR." (6 Conclusions)

## Claim tuples

- H: Do the cores fragment as predicted by thermal Jeans fragmentation? | E: Compare 18 ALMA fragments with thermal Jeans masses of Herschel cores | R: Fewer fragments than expected; three cores with none | F: Fragmentation inconsistent with ideal gravitational fragmentation; turbulence or magnetic fields needed | **supported**
- H: Is Condensation 1 favourable for high-mass star formation? | E: Fragment masses and CH3CN/SO2 detection | R: Fragments up to 32 Msun; line emission toward Fragment 1 | F: Favourable place with probable UCHII region | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Only 20% of emission recovered; extended emission filtered  
  > "while the emission above 14$''$  is filtered and lost" (4 Results and analysis)
- Caveat (inferred, ours): Fragment masses assume host-core temperature, uncertain by factor 2 plus opacity
- Caveat (inferred, ours): Short single-pointing observation; fragment completeness not tested
- Caveat (inferred, ours): Jeans comparison uses assumed 0.1 pc scale

## Reproducibility

- Data public (paper): Project code given; products delivered by ALMA  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00314.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Herschel maps/SED fits and configuration files
- Missing: CASA version
- Missing: Louvet et al. temperature recipe
- Data volume (inferred): ~5-20 GB
- Score (inferred): 3/5, Data and simple formulas given, but extraction configs and Herschel inputs are unspecified.
- Rediscovery candidate: no, Depends on getsources configs and Herschel core properties not fully provided.

## Links

- Method: Men'shchikov 2017 (cite: men17) (getimages)
- Method: Men'shchikov et al. 2012 (cite: men12) (getsources)
- Companion: Figueira et al. 2017 (cite: fig17) (Herschel cores of RCW 120)
- Companion: Louvet et al. submitted (NGC 6334 ALMA fragments, method comparison)
- Related: HOBYS
- Related: MALT90

## Checks

```json
{
 "quotes": 48,
 "quotes_ok": 48,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 35,
  "rate": 0.479
 },
 "evidence_ok": true
}
```

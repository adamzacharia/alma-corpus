# Searches for Interstellar HCCSH and H<SUB>2</SUB>CCS

`2019ApJ...883..201M` | The Astrophysical Journal 2019 | first author: McGuire, Brett A. | arXiv: 1908.04247 | DOI: 10.3847/1538-4357/ab3b01

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: astrochemistry, star_formation
- Question: Can HCCSH and H2CCS be detected in interstellar sources, and could they be major reservoirs of missing interstellar sulfur?  
  > "we report searches for the rotational lines in the microwave, millimeter, and sub-millimeter regions of the sulfur-containing hydrocarbon HCCSH." (abstract)
- Target **NGC 6334I**: coordinates 17:20:53.374, -35:46:58.34 (J2000)  
  > "NGC 6334I is a nearby HMSFR (1.3 kpc by maser parallax; (cite: Chibueze:2014iv))" (4.1 NGC 6334I); "The spectra were extracted from (J2000) $\alpha$ = 17:20:53.374, $\delta$=-35:46:58.34." (4.1 NGC 6334I); z/distance 1.3 kpc  
  > "NGC 6334I is a nearby HMSFR (1.3 kpc by maser parallax; (cite: Chibueze:2014iv))" (4.1 NGC 6334I); "The spectra were extracted from (J2000) $\alpha$ = 17:20:53.374, $\delta$=-35:46:58.34." (4.1 NGC 6334I); distance from maser parallax (Chibueze et al. 2014)  
  > "NGC 6334I is a nearby HMSFR (1.3 kpc by maser parallax; (cite: Chibueze:2014iv))" (4.1 NGC 6334I); "The spectra were extracted from (J2000) $\alpha$ = 17:20:53.374, $\delta$=-35:46:58.34." (4.1 NGC 6334I)

## Data provenance

- ALMA projects: 2015.A.00022.T, 2017.1.00717.S
- bands: Band 7 and Band 10  
  > "The complete observing parameters for the Band 10 data are provided in (cite: McGuire:2018bz). The Band 7 observing parameters are provided in (cite: McGuire:2017gy)" (4.1 NGC 6334I)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Band 7 degraded from 0.25"x0.19" to 0.26"x0.26" to match Band 10  
  > "the angular resolution of the Band 7 data, originally 0.25$^{\prime\prime}\times$0.19$^{\prime\prime}$ was degraded to match that of the Band 10 data: 0.26$^{\prime\prime}\times$0.26$^{\prime\prime}$." (4.1 NGC 6334I)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **Herschel/HIFI (HEXOS)**: ~860 GHz spectra toward Orion-KL and Sgr B2(N)  
  > "are from the *Herschel* Observations of EXtraordinary Sources (HEXOS) key project using the Heterodyne Instrument for the Far Infrared (HIFI) instrument" (4.2 Orion-KL)
- Other facility **GBT PRIMOS**: centimeter spectra toward Sgr B2(N)  
  > "This frequency range falls within the coverage of the Prebiotic Interstellar Molecular Survey (PRIMOS) project observations of Sgr B2(N) using the 100-m Robert C. Byrd Green Bank Telescope." (4.3.3 GBT PRIMOS Data)
- Other facility **IRAM 30m (ASAI; Belloche et al. survey)**: line surveys toward Solar-type protostellar sources and 3 mm Sgr B2(N) data  
  > "We also searched the line survey data toward sources from the publicly available Astrochemical Surveys at IRAM (ASAI) Large Project conducted with the IRAM 30-m telescope." (4 Observations and Analysis)
- External data: Laboratory rest frequencies and spectroscopy of HCCSH (up to 660 GHz) and dipole moments  
  > "The detailed spectroscopic analysis of its $a$- and $b$-type transitions up to 660 GHz was presented in (cite: Lee:2018uw)." (3 Energetics and Spectroscopy) [from (cite: Lee:2018uw)]
- External data: H2CCS laboratory frequencies and dipole moment  
  > "its dipole moment is sizable, 1.01(3) D (cite: Winnewisser:1980ic)." (3 Energetics and Spectroscopy) [from (cite: Winnewisser:1980ic)]
- External data: Excitation parameters (Tex, vlsr, dV, Tbg) for NGC 6334I  
  > "were assumed to match those described in (cite: McGuire:2018bz)" (4.1 NGC 6334I) [from (cite: McGuire:2018bz)]

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
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA Band 10 observing parameters  
  > "The complete observing parameters for the Band 10 data are provided in (cite: McGuire:2018bz)." (4.1 NGC 6334I) [from (cite: McGuire:2018bz)]
- ALMA Band 7 observing parameters  
  > "The Band 7 observing parameters are provided in (cite: McGuire:2017gy), with one exception." (4.1 NGC 6334I) [from (cite: McGuire:2017gy)]
- Column density formalism  
  > "following the formalisms of (cite: Hollis:2004uh)" (3 Analysis) [from (cite: Hollis:2004uh); optical depth corrections (cite: Turner:1991um)]

### Not stated but needed to reproduce (our reading)

- Calibration and imaging details of the ALMA data (in companion papers)
- Spectral extraction details: aperture size and continuum subtraction
- Reduced ALMA spectra and rms values per line
- Assumed vlsr values

## Analysis recipe

1. **Simulate spectra and find strongest predicted line**: Simulate spectrum with source parameters; use strongest predicted line and local rms as 1-sigma brightness temperature  
  > "The strongest predicted line in the observational spectrum was then used to calculate the $1\sigma$ upper limit, taking the rms noise value at that point as the value of the brightness temperature $\Delta T_b$." (3 Analysis)
   - assumption: Tex, dV, Tbg, source size taken from analogue molecules or literature per source  
  > "the values of $T_{ex}$, $v_{lsr}$, $\Delta V$, and $\theta_s$ were assumed to match those of from the analysis of (cite: Crockett:2014er)" (4.2 Orion-KL)
   - fitting: _not stated_
   - validation: _not stated_
2. **Compute column density upper limits**: Single-excitation-temperature column density formula with partition function Q = Qrot x Qvib x Qelec  
  > "Column densities were calculated assuming a single-excitation temperature model following the formalisms of (cite: Hollis:2004uh)" (3 Analysis)
   - parameter: Qvib uses lowest five vibrational states from CCSD(T)/cc-pVQZ harmonic energies; Qelec = 1  
  > "Here, we consider only the lowest five vibrational states as those higher in energy make a negligible contribution to $Q_{\rm{vib}}$." (3 Analysis)
   - assumption: Qelec = 1  
  > "Under interstellar conditions, we assume $Q_{elec} = 1$." (3 Analysis)
   - fitting: _not stated_
   - validation: _not stated_
3. **Convert to abundances relative to H2**: Divide upper limit N_T by literature N(H2) per source  
  > "Sgr B2(N) | 844982.2$^b$ | $21_{2,19} - 21_{1,20}$ | 176.7 | 7.1 | 35808 (8441, 4.24) | $\leq 1.4\times10^{17}$ | $1\times10^{24}$ | $\leq 1\times10^{-7}$ | 1" (Table 1 (HCCSH upper limits))
   - fitting: _not stated_
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HCCSH N_T upper limit, NGC 6334I (ALMA) | <= 1.4e16 | not stated | cm^-2 | 2 | NGC 6334I / 293352.8 / $16_{1,15} - 16_{0,16}$ / 85.8 / 10.4 / 3894 (2824, 1.38) / $\leq 1.4\times10^{16}$ |
| H2CCS N_T upper limit, NGC 6334I (ALMA) | <= 4.7e15 | not stated | cm^-2 | 2 | NGC 6334I / 292685.4$^b$ / $26_{1,25} - 25_{1,24}$ / 203.2 / 78.2 / 9051 (5456, 1.66) / $\leq 4.7\times10^{15}$ |
| HCCSH N_T upper limit, Orion-KL (618565.8 MHz) | <= 3.1e15 | not stated | cm^-2 | 2 | Orion-KL / 618565.8 / $33_{1,33} - 32_{0,32}$ / 307.9 / 11.4 / 12664 (5442, 2.32) / $\leq 3.1\times10^{15}$ |

## Qualitative findings

- No detection of HCCSH or H2CCS in any source; typical abundance upper limits relative to H are 1e-9 to 1e-10.  
  > "Typical upper limits on the abundance of both species relative to hydrogen are $10^{-9}$–$10^{-10}$." (abstract)

## Claim tuples

- H: HCCSH and H2CCS are major interstellar sulfur reservoirs | E: Searched ALMA, Herschel, GBT and IRAM line surveys toward high-mass and low-mass sources using new laboratory frequencies | R: Non-detections everywhere; upper limits on column densities and abundances | F: Neither isomer is a substantial sulfur reservoir in the environments studied | **supported**

## Reasoning

- Why this data: Strongest HCCSH transitions fall in ALMA Bands 7 and 10 and the THz window  
  > "Due to its geometry, the most intense transitions fall in ALMA Bands 7 and 10 and the 1.4 THz window of the SOFIA GREAT receiver" (4 Observations and Analysis)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Upper limits are uncertain because the strongest lines lie beyond laboratory frequency coverage and require extrapolation, especially in line-confused sources.  
  > "In line-confused sources, however, such as NGC 6334I in ALMA Band 10, frequency extrapolation can not be made with confidence, making any purported detection highly tenuous." (6 Results and Discussion)
- Caveat (inferred, ours): Upper limits depend on analogue-molecule excitation parameters rather than measured ones
- Caveat (inferred, ours): Single-line 1-sigma limits are not conservative
- Caveat (inferred, ours): Source size and beam dilution assumptions are poorly constrained for some sources

## Reproducibility

- Data public (paper): ASAI is described as publicly available; ALMA project codes are given  
  > "publicly available Astrochemical Surveys at IRAM (ASAI) Large Project" (4 Observations and Analysis)
- Products in archive: _not stated_
- Missing: ALMA calibration/imaging details (in companion papers)
- Missing: Spectral extraction details
- Missing: Exact rms and spectra per line
- Data volume (inferred): Tens of GB for the ALMA Band 7 and 10 datasets; the other data are small spectra
- Score (inferred): 3/5, Formulas and tables of parameters are given, but ALMA processing is deferred to other papers and many inputs come from the literature.
- Rediscovery candidate: no, The ALMA part is minor and the results are upper limits that depend on literature parameters and non-ALMA datasets.

## Links

- Method: (cite: Hollis:2004uh) (Column density formalism)
- Method: (cite: Lee:2018uw) (HCCSH laboratory spectroscopy)
- Companion: (cite: McGuire:2018bz) (ALMA Band 10 data and source parameters for NGC 6334I)
- Companion: (cite: McGuire:2017gy) (ALMA Band 7 data for NGC 6334I)
- Related: HEXOS
- Related: PRIMOS
- Related: ASAI

## Checks

```json
{
 "quotes": 35,
 "quotes_ok": 35,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 25,
  "rate": 0.379
 },
 "evidence_ok": true
}
```

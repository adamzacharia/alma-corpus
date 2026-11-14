# First detection of the pre-biotic molecule glycolonitrile (HOCH<SUB>2</SUB>CN) in the interstellar medium

`2019MNRAS.484L..43Z` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Zeng, S. | arXiv: 1901.02576 | DOI: 10.1093/mnrasl/slz002

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: astrochemistry, star_formation
- Question: Is glycolonitrile (HOCH2CN) present in the ISM toward the Solar-type protostar IRAS16293-2422 B, what are its excitation temperatures and abundances, and can gas-grain chemical modelling reproduce them?  
  > "we report the first detection of this pre-biotic molecule in the interstellar medium (ISM) by using ALMA data obtained at frequencies between 86.5$\,$GHz and 266.5$\,$GHz toward the Solar-type protostar IRAS16293-2422 B" (abstract)
- Target **IRAS16293-2422 B**: coordinates RA(J2000)=16h32m22.61s, Dec(J2000)=-24d28m32.44s  
  > "$\alpha$(J2000.0)=16$^h$32$^m$22.61$^s$, $\delta$(J2000.0)=-24$^{\circ}$28$^{\prime}$32.44$^{\prime\prime}$" (Observations); "at a distance of 141$^{+31}_{-21}$ pc (cite: Dzib2018)" (Introduction); z/distance 141 +31/-21 pc  
  > "$\alpha$(J2000.0)=16$^h$32$^m$22.61$^s$, $\delta$(J2000.0)=-24$^{\circ}$28$^{\prime}$32.44$^{\prime\prime}$" (Observations); "at a distance of 141$^{+31}_{-21}$ pc (cite: Dzib2018)" (Introduction); distance from Dzib et al. 2018  
  > "$\alpha$(J2000.0)=16$^h$32$^m$22.61$^s$, $\delta$(J2000.0)=-24$^{\circ}$28$^{\prime}$32.44$^{\prime\prime}$" (Observations); "at a distance of 141$^{+31}_{-21}$ pc (cite: Dzib2018)" (Introduction)

## Data provenance

- ALMA projects: 2011.0.00007.SV, 2012.1.00712.S, 2013.1.00061.S, 2013.1.00352.S, 2015.1.01193.S
- bands: Bands 3, 4, and 6  
  > "several publicly available datasets in Bands 3, 4, and 6 in the ALMA archive" (Observations)
- frequencies and spectral setup: ~7 GHz total bandwidth in multiple ranges between 86.5 and 266.5 GHz; 61-282 kHz resolution (0.1-0.9 km/s)  
  > "Our dataset covers a total bandwidth of $\sim$7$\,$GHz spread in multiple spectral ranges between 86.5$\,$GHz and 266.5$\,$GHz." (Observations); "spectral resolutions of 61-282$\,$kHz that correspond to velocity resolutions of 0.1-0.9$\,$km s$^{-1}$" (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beam sizes 1.42" to 1.85"  
  > "The beam sizes range between 1.42$^{\prime\prime}$ and 1.85$^{\prime\prime}$" (Observations)
- max recoverable scale: _not stated_
- sensitivity: line rms 2-4 mJy km/s (Table 1)  
  > "| 266.232097 | (30,0,30)-(29,0,29),v=0-0 | -3.21 | 200 | 77$\pm$9 | 1.0$\pm$0.1 | 3 |  |" (Table 1)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: publicly available archival datasets  
  > "We searched for HOCH$_2$CN using several publicly available datasets" (Observations)
- Line: HOCH2CN 15 unblended transitions, e.g. (10,1,10)-(9,1,9) to (30,0,30)-(29,0,29) (89.650064-266.232097 GHz)
- External data: N(H2)=2.8e25 cm-2 for warm component  
  > "An H$_2$ column density of N(H$_2$)=2.8$\times$10$^{25}$ cm$^{-2}$ was adopted from (cite: martin-domenech_detection_2017)" (Results) [from (cite: martin-domenech_detection_2017)]
- External data: N(H2)=1.5e23 cm-2 for cold envelope  
  > "an H$_2$ column density of N(H$_2$)=1.5$\times$10$^{23}$ cm$^{-2}$ was adopted using the envelope profile constrained by (cite: crimier2010)" (Results) [from (cite: crimier2010)]
- External data: HOCH2CN spectroscopy from CDMS based on laboratory work  
  > "we have used the spectroscopic parameters from the Cologne Database for Molecular Spectroscopy (CDMS)" (Results) [from (cite: muller_cologne_2001; muller_cologne_2005; endres_cologne_2016); lab work (cite: margules_submillimeter_2017)]

## Processing

### Calibration

- pipeline or manual: standard ALMA calibration scripts and CASA, as in Martin-Domenech et al. 2017  
  > "the standard ALMA calibration scripts and the Common Astronomy Software Applications package were used for data calibration and imaging" (Observations)
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
- continuum subtraction: uv-plane subtraction using line-free channels before imaging  
  > "continuum subtraction performed in the uv-plane before imaging using line-free channels from the observed spectra" (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Calibration and imaging procedure  
  > "As in (cite: martin-domenech_detection_2017), the standard ALMA calibration scripts and the Common Astronomy Software Applications package were used" (Observations) [from (cite: martin-domenech_detection_2017)]
- Warm-component source size fixed to 0.5"  
  > "As in the analysis of CH$_3$NCO by (cite: martin-domenech_detection_2017) toward I16293B, the source size was fixed to 0.5$^{\prime\prime}$ for the warm component" (Results) [from (cite: martin-domenech_detection_2017)]
- Starting elemental abundances of chemical model  
  > "The starting elemental abundances are the same as in (cite: quenard2018a)." (Chemical modelling) [from (cite: quenard2018a)]

### Not stated but needed to reproduce (our reading)

- CASA version and imaging parameters (weighting, cell, deconvolver, masks)
- line-free channels used for continuum subtraction
- which dataset covers which lines and the per-dataset beam
- flux calibration uncertainty
- priors/initial values and fixed parameters in MADCUBA fits
- how the cold-component N and abundance were converted (extended source size handling)
- how the warm/cold temperature split was chosen in the rotational diagram (E_up=100 K)
- UCLCHEM version and warm-up timescale/heating prescription

## Analysis recipe

1. **Calibrate and image archival data, extract spectra**: Standard calibration scripts and CASA; uv-plane continuum subtraction; spectra extracted in a 1.6" diameter circle at I16293B  
  > "a circle of 1.6$^{\prime\prime}$ diameter was used to extract the spectra from each dataset at the position of I16293 B" (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify HOCH2CN lines and fit LTE synthetic spectra**: MADCUBA-SLIM synthetic LTE spectra with opacity, manual adjustment then MADCUBA-AUTOFIT; two temperature components  
  > "Then the MADCUBA-AUTOFIT tool was employed to provide the best non-linear least-squared fit using the Levenberg-Marquardt algorithm." (Results)
   - software: MADCUBA, CDMS
   - parameter: Free: Ntot, Tex, VLSR, linewidth; cold component linewidth fixed to 1 km/s; warm source size 0.5", cold >20"  
  > "with $\Delta \nu$ fixed to 1$\,$km s$^{-1}$" (Results)
   - assumption: LTE  
  > "For the typical densities and linear scales imaged with ALMA toward I16293, LTE is a good approximation" (Results)
   - fitting: Levenberg-Marquardt least squares  
  > "best non-linear least-squared fit using the Levenberg-Marquardt algorithm" (Results)
   - validation: Rotational diagram consistency  
  > "two temperature components were invoked, which is also agreed with our rotational diagram analysis" (Results)
3. **Rotational diagram and abundances**: Two linear least-squares fits to E_up<=100 K and >=100 K lines assuming optically thin emission; divide by adopted N(H2)  
  > "Two linear least square fits are required to fit simultaneously the transitions with E$\rm_{up}$$\leq$100$\,$K and $E_{\rm up}$$\geq$100$\,$K." (Results)
   - assumption: N(H2)=2.8e25 (warm), 1.5e23 cm-2 (cold)  
  > "N(H$_2$)=1.5$\times$10$^{23}$ cm$^{-2}$ was adopted" (Results)
   - fitting: _not stated_
   - validation: Trot compared with MADCUBA Tex  
  > "They are consistent (within the errors) with the $T_{\rm ex}$ computed by MADCUBA" (Results)
4. **Chemical modelling of abundance**: UCLCHEM three-phase model (diffuse, pre-stellar collapse, warm-up) with updated HOCH2CN network; zeta varied 1-6 times standard  
  > "we vary the cosmic-ray ionisation rate ($\zeta$) from 1 to 6 times the standard value ($\zeta_{\rm std}=1.3\times10^{-17}$ s$^{-1}$)" (Chemical modelling)
   - software: UCLCHEM
   - parameter: Warm: nH=5e8 cm-3, T up to 160 K; cold: nH=6e6 cm-3, T up to 30 K; G0=1 Habing  
  > "the gas/grain temperatures increase from 10 K up to either 160 K for the warm component, or to 30 K for the cold envelope" (Chemical modelling)
   - assumption: HOCH2CN forms only on grains; ion-neutral rates assumed like CH3NCO  
  > "we assume that they are similar to those involving CH$_3$NCO and keep the different branching ratios" (Chemical modelling)
   - fitting: _not stated_
   - validation: Compared with observed abundances at dynamical age ~1-2e4 yr  
  > "at the dynamical age of I16293B of $\sim$1-2$\times$10$^4$ yrs" (Chemical modelling)

## Software

- **CASA** : calibration and imaging  
  > "the Common Astronomy Software Applications package were used for data calibration and imaging" (Observations)
- **MADCUBA** : line identification, LTE fitting (SLIM, AUTOFIT)  
  > "The line identification and analysis were performed with MADCUBA package" (Results)
- **UCLCHEM** : gas-grain chemical modelling  
  > "we have used the gas-grain chemical code UCLCHEM" (Chemical modelling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Tex cold component | 24 | ±8 | K | 2 | cold component (with $T_{\rm ex}$=24$\pm$8$\,$K; see green lines) |
| Tex warm component | 158 | ±38 | K | 2 | warm component (with $T_{\rm ex}$=158$\pm$38$\,$K; red lines) |
| Trot cold / warm | 39 / 156 | ±7 / ±27 | K | 3 | are 39$\pm$7$\,$K and 156$\pm$27$\,$K |
| Ntot cold | 8.5e13 | ±2.6e13 | cm-2 | 3 | $N_{\rm tot}$=(8.5$\pm$2.6)$\times$10$^{13}$$\,$cm$^{-2}$ |
| Ntot warm | 1.8e15 | ±0.1e15 | cm-2 | 3 | $N_{\rm tot}$=(1.8$\pm$0.1)$\times$10$^{15}$$\,$cm$^{-2}$ for the cold and warm components |
| Abundance warm | 6.5e-11 | ±0.6e-11 | relative to H2 | 3 | yielding an HOCH$_2$CN abundance of (6.5$\pm$0.6)$\times$10$^{-11}$ for the warm component |
| Abundance cold (lower limit) | 6e-10 | ±2e-10 | relative to H2 | 3 | The resulting HOCH$_2$CN abundance for the cold component is therefore (6$\pm$2)$\times$10$^{-10}$. |
| NH2CH2CN upper limit (3 sigma) | <=1.7e14 | not stated | cm-2 | 2 | 3$\sigma$ upper limit $N_{\rm tot}$ $\leq$1.7$\times$10$^{14}$$\,$cm$^{-2}$ |

## Qualitative findings

- Models underproduce the cold-component abundance for all zeta; gas-phase formation routes likely missing  
  > "The observed abundance cannot be reproduced by any model." (Chemical modelling)

## Claim tuples

- H: HOCH2CN is present toward IRAS16293 B | E: Line search in archival ALMA Band 3/4/6 spectra with MADCUBA | R: 35 transitions >=3 sigma, 15 unblended | F: First ISM detection of HOCH2CN | **supported**
- H: One temperature suffices | E: LTE fit and rotational diagram | R: Tex 24 and 158 K components | F: Molecule is in both the hot corino and the cold envelope | **supported**
- H: Current gas-grain chemistry reproduces the abundances | E: UCLCHEM modelling with varied zeta | R: Warm matched for zeta_std and 3x zeta_std at ~1-2e4 yr; cold not reproduced | F: Network lacks gas-phase formation routes | **partially**

## Reasoning

- Why this data: Excluded Bands 7 and 8 to limit spectral confusion and dust opacity effects  
  > "By excluding datasets in Bands 7 and 8, we limit the spectral confusion seen at high frequencies" (Observations)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): LTE may not apply; cold abundance is a lower limit  
  > "we cannot rule out the possibility that LTE might not apply" (Results); "our abundance must be considered as a lower limit" (Results)
- Caveat (inferred, ours): Cold-component parameters rest on few low-Eup lines and an assumed extended source size
- Caveat (inferred, ours): Blending and non-LTE could bias the two-temperature fit
- Caveat (inferred, ours): Single N(H2) values adopted from literature dominate abundance uncertainty

## Reproducibility

- Data public (paper): publicly available ALMA archive datasets  
  > "several publicly available datasets in Bands 3, 4, and 6 in the ALMA archive" (Observations)
- Products in archive: _not stated_
- Missing: CASA version and imaging settings
- Missing: MADCUBA fit setup details
- Missing: UCLCHEM version and input files
- Data volume (inferred): ~100-300 GB for five archival datasets
- Score (inferred): 5/5, Public data and software named, but processing and fit settings are sparse and rely on a prior paper.
- Rediscovery candidate: yes, Data public, numeric results (Tex, N, abundances); recipe moderately complete.

## Links

- Method: (cite: martin-domenech_detection_2017) (calibration, source size, N(H2) approach)
- Method: (cite: rivilla2016) (MADCUBA software)
- Companion: (cite: jorgensen_alma_2016) (PILS survey data)
- Companion: (cite: ligterink_alma-pils_2017) (related data/analysis)
- Related: ALMA-PILS

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 5,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 37,
  "rate": 0.521
 },
 "evidence_ok": true
}
```

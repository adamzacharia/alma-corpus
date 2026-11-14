# Detection of methyl isocyanate (CH<SUB>3</SUB>NCO) in a solar-type protostar

`2017MNRAS.469.2230M` | Monthly Notices of the Royal Astronomical Society 2017 | first author: Martín-Doménech, R. | arXiv: 1701.04376 | DOI: 10.1093/mnras/stx915

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: astrochemistry, star_formation
- Question: Is methyl isocyanate (CH3NCO) present in the solar-type protostar IRAS16293-2422 B, what are its abundance and ratios to HNCO and NH2CHO, and how is it formed?  
  > "We report the detection of the prebiotic molecule CH$_3$NCO in a solar-type protostar, IRAS16293-2422 B." (abstract)
- Target **IRAS16293-2422 B**: coordinates RA 16h32m22.61s, Dec -24d28m32.44s (J2000)  
  > "IRAS 16293$-$2422 (hereafter IRAS16293) is located in the $\rho$ Ophiuchi cloud complex at a distance of 120 pc (cite: loinard08)" (Introduction); "$RA_{\rm J2000}$ = 16$h$ 32$m$ 22.61$s$, $DEC_{\rm J2000}$ = -24$^{\circ}$ 28$^{\prime}$ 32.44$^{\prime\prime}$" (Observations); z/distance 120 pc  
  > "IRAS 16293$-$2422 (hereafter IRAS16293) is located in the $\rho$ Ophiuchi cloud complex at a distance of 120 pc (cite: loinard08)" (Introduction); "$RA_{\rm J2000}$ = 16$h$ 32$m$ 22.61$s$, $DEC_{\rm J2000}$ = -24$^{\circ}$ 28$^{\prime}$ 32.44$^{\prime\prime}$" (Observations); distance from Loinard et al. 2008  
  > "IRAS 16293$-$2422 (hereafter IRAS16293) is located in the $\rho$ Ophiuchi cloud complex at a distance of 120 pc (cite: loinard08)" (Introduction); "$RA_{\rm J2000}$ = 16$h$ 32$m$ 22.61$s$, $DEC_{\rm J2000}$ = -24$^{\circ}$ 28$^{\prime}$ 32.44$^{\prime\prime}$" (Observations)

## Data provenance

- ALMA projects: 2013.1.00352.S, 2011.0.00007.SV, 2012.1.00712.S, 2013.1.00061.S
- bands: Bands 3, 4 and 6 (Bands 7 and 8 excluded)  
  > "all other public datasets in Bands 3, 4, and 6 available in the ALMA archive as of January 2017" (Observations)
- frequencies and spectral setup: ~6 GHz total bandwidth in 26 spectral windows between 89.5 and 266.5 GHz; velocity resolution 0.14-0.30 km/s  
  > "Our dataset covers a total bandwidth of $\sim$6 GHz split in 26 spectral windows spread between 89.5 and 266.5 GHz" (Observations); "The velocity resolution falls between 0.14 and 0.30 km s$^{-1}$." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beams 0.57"x0.28" to 1.42"x1.23"  
  > "with synthesised beam sizes ranging from 0.57$^{\prime\prime}\times$0.28$^{\prime\prime}$ to 1.42$^{\prime\prime}\times$1.23$^{\prime\prime}$" (Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CH3NCO 8 unblended transitions, e.g. (29,0,29,0)-(28,0,28,0) (157.258-250.676 GHz)
- Line: HNC18O five unresolved transitions (~250 GHz)
- Line: NH2(13)CHO three lines (156.957, 157.097, 239.628 GHz)
- External data: Dust opacity 0.009 cm2/g  
  > "a dust opacity of 0.009 cm$^{2}$ g$^{-1}$ (cite: ossenkopf94)" (3.1) [from (cite: ossenkopf94)]
- External data: Isotopic ratio 12C/13C=68  
  > "By assuming an isotopic ratio $^{12}$C/$^{13}$C=68 (cite: milam05)" (3.2) [from (cite: milam05)]
- External data: Isotopic ratio 16O/18O = 500  
  > "By assuming an isotopic ratio $^{16}$O/$^{18}$O = 500 (Wilson & Rood 1994)" (3.2) [from Wilson & Rood 1994]
- External data: Spectroscopic line catalogs (JPL, CDMS)  
  > "using the information from the Jet Propulsion Laboratory (cite: pick98) and the Cologne Database for Molecular Spectroscopy spectral catalogs (cite: mull05)" (3.1) [from (cite: pick98); (cite: mull05)]

## Processing

### Calibration

- pipeline or manual: Re-calibrated with standard ALMA calibration scripts and CASA  
  > "All data matching our criteria were downloaded and re-calibrated using standard ALMA calibration scripts and the Common Astronomy Software Applications package" (Observations)
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
- continuum subtraction: In the uv-plane before imaging using line-free channels  
  > "Continuum subtraction was performed in the uv-plane before imaging using line-free channels." (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Molecular emission is compact (<1.5") so spectra contain all emission  
  > "is compact and lies below 1.5$"$ (cite: coutens16)" (Observations) [from (cite: coutens16)]
- HNCO and NH2CHO lines optically thick, so isotopologues used  
  > "The HNCO and NH$_2$CHO lines are optically thick (cite: coutens16)" (3.2) [from (cite: coutens16)]
- Source size 0.5" agrees with previous works  
  > "which agrees with the source size assumed in previous works (cite: jorgensen16; coutens16; lykke16)" (3.1) [from (cite: jorgensen16; coutens16; lykke16)]

### Not stated but needed to reproduce (our reading)

- CASA version and imaging parameters (weighting, robust, cell, image size, deconvolver)
- Line-free channels used for continuum subtraction
- Per-dataset imaging details and which datasets cover which lines
- MADCUBAIJ fitting settings (parameter priors, velocity, fit method)
- Whether catalogs entries (JPL vs CDMS) used for CH3NCO
- Details of chemical model grid, best-fit age and parameter sampling

## Analysis recipe

1. **Extract spectra**: Spectrum extracted from each datacube with circular aperture ~1.6" centred on IRAS16293 B  
  > "a spectrum was extracted from each datacube using a circular support with size $\sim$1.6$^{\prime\prime}$ centered at the position of IRAS16293 B" (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify lines and fit LTE CH3NCO**: MADCUBAIJ synthetic LTE spectra compared with observed to derive Tex and N  
  > "The comparison between the observed and the synthetic spectrum for the unblended ransitions can be used to derive the excitation temperature and total column density that best match the observations." (3.1)
   - software: MADCUBAIJ
   - parameter: Linewidth 1.1 km/s; source size 0.5"  
  > "We assumed a linewidth of 1.1 km s$^{-1}$, and the source size was constrained by the continuum emission to 0.5$^{\prime\prime}$" (3.1)
   - assumption: LTE  
  > "MADCUBAIJ produces synthetic spectra assuming Local Thermodinamical Equilibrium (LTE) conditions." (3.1)
   - fitting: _not stated_
   - validation: Checked synthetic spectrum for missing detectable transitions; lines optically thin  
  > "a careful check of the synthetic spectrum was performed to confirm that no dectectable transitions were missing from our observational data." (3.1)
3. **Derive H2 column density and abundance**: Optically thin dust continuum at 232 GHz  
  > "we have derived the H$_2$ column density by using the continuum flux measured at 232 GHz (1.4$\pm$0.05 Jy within a deconvolved size of 0.55$\ensuremath{''}\times$0.47$\ensuremath{''}$)" (3.1)
   - assumption: Optically thin dust, kappa 0.009 cm2/g, gas-to-dust 100, Tdust=Tex=110 K  
  > "assuming optically thin dust, a dust opacity of 0.009 cm$^{2}$ g$^{-1}$ (cite: ossenkopf94) and a gas-to-dust mass ratio of 100" (3.1)
   - fitting: _not stated_
   - validation: Consistent with Jorgensen et al. 2016  
  > "consistent with that estimated by (cite: jorgensen16) at higher frequencies" (3.1)
4. **HNCO and NH2CHO columns via isotopologues**: LTE fits of HNC18O (Tex fixed 110 K) and NH2 13CHO (Tex 75 K), scaled by isotopic ratios  
  > "For a fixed excitation temperature of $T_{ex}$=110 K, (the $T_{ex}$ derived for CH$_3$NCO; see Section 3.1)" (3.2)
   - software: MADCUBAIJ
   - assumption: 16O/18O=500; 12C/13C=68  
  > "By assuming an isotopic ratio $^{16}$O/$^{18}$O = 500 (Wilson & Rood 1994)" (3.2)
   - fitting: _not stated_
   - validation: _not stated_
5. **Chemical modelling**: Three-phase UCL_CHEM gas-grain model with added CH3NCO, HNCO routes  
  > "The physical conditions and the chemical composition of the IRAS16293 B hot corino were modelled using a three phase model." (4)
   - software: UCL_CHEM
   - parameter: nH 5e8 cm-3, T 10 to 110 K over 1e5 yr  
  > "assuming a constant H$_2$ gas density ($5\times10^{8}$ cm$^{-3}$) while gradually increasing the gas temperature from 10$\,$K to 110$\,$K during the first 10$^5$ yrs" (4)
   - fitting: _not stated_
   - validation: Compared with observed abundances and L1544 upper limits  
  > "our model perfectly reproduces the upper limits of CH$_3$NCO measured in cold cores such as L1544" (4)

## Software

- **CASA** : Recalibration of archival data  
  > "re-calibrated using standard ALMA calibration scripts and the Common Astronomy Software Applications package" (Observations)
- **MADCUBAIJ** : Line identification and LTE fitting  
  > "The identification of the lines was performed using the software MADCUBAIJ" (3.1)
- **UCL_CHEM** : Gas-grain chemical modelling  
  > "we have used the gas-grain chemical code UCL_CHEM" (4)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CH3NCO excitation temperature | 110 | 19 | K | 2 | an excitation temperature of 110$\pm$19 K |
| N(CH3NCO) | 4.0e15 | 0.3e15 | cm-2 | 2 | a column density of (4.0$\pm$0.3)$\times$10$^{15}$ cm$^{-2}$ |
| CH3NCO abundance wrt H2 (upper limit) | 1.4e-10 | 0.1e-10 | dimensionless | 3 | abundance of $\le$(1.4$\pm$0.1)$\times$10$^{-10}$ |
| N(H2) | 2.8e25 | not stated | cm-2 | 3 | is $N$(H$_{2}$)=2.8 $\times$10$^{25}$ cm$^{-2}$ |
| N(HNCO) | 4.9e16 | 1.9e16 | cm-2 | 4 | $N$(HNCO)=(4.9$\pm$1.9)$\times$10$^{16}$ cm$^{-2}$ |
| N(NH2CHO) | 5.2e16 | 2.5e16 | cm-2 | 4 | $N$(NH$_2$CHO)=(5.2$\pm$2.5)$\times$10$^{16}$ cm$^{-2}$ |
| CH3NCO/HNCO and CH3NCO/NH2CHO ratios | ~0.08 | not stated | dimensionless | 4 | CH$_3$NCO/HNCO and CH$_3$NCO/NH$_2$CHO column density ratios of $\sim$0.08 |
| Model CH3NCO abundance | 6.0e-10 | not stated | dimensionless | 5 | a predicted abundance for CH$_3$NCO of \[CH$_3$NCO\]=$6.0\times10^{-10}$ |

## Qualitative findings

- CH3NCO lines optically thin and coincident with continuum, size ~0.5"  
  > "The measured deconvolved size is $\sim$0.5$"$, consistent with the assumed source size." (3.1)

## Claim tuples

- H: CH3NCO exists in a solar-type protostar | E: LTE analysis of archival+own ALMA Band 3-6 spectra of IRAS16293 B | R: 8 unblended lines, Tex 110 K, N 4.0e15 cm-2 | F: CH3NCO detected in a low-mass protostar | **supported**
- H: CH3NCO/HNCO and /NH2CHO ratios compare with other sources | E: Isotopologue-based columns of HNCO and NH2CHO | R: Ratios ~0.08; similar to SgrB2(N) HNCO ratio, much lower than comet 67P in HNCO | F: Ratios similar to high-mass sources, differ from comet | **supported**
- H: Formation route of CH3NCO | E: UCL_CHEM modelling | R: Grain surface alone insufficient; gas+ice reproduce within factor 4 | F: Both ice and gas-phase formation required | **partially**

## Reasoning

- Why this data: Bands 7 and 8 excluded to avoid dust optical depth and line confusion  
  > "to prevent any dust optical depth problems (cite: zapata13; jorgensen16)" (Observations)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): H2 column is a lower limit, so abundances are upper limits as dust may be optically thick  
  > "We however caution that this value should be considered as a lower limit since dust may be optically thick even at these low frequencies." (3.1)
- Limitation (authors): NH2CHO underproduced by model by factor 10  
  > "the abundance of NH$_2$CHO is underproduced by a factor of 10" (4)
- Caveat (inferred, ours): Single Tex and source size for all lines despite different beams and datasets
- Caveat (inferred, ours): No dust optical depth correction
- Caveat (inferred, ours): Uncertainties on isotopologue-based columns propagate from fixed Tex
- Caveat (inferred, ours): Model best-fit not formally fitted

## Reproducibility

- Data public (paper): Public ALMA archive datasets  
  > "all other public datasets in Bands 3, 4, and 6 available in the ALMA archive as of January 2017" (Observations)
- Products in archive: _not stated_
- Code: UCL_CHEM available at uclchem.github.io  
  > "UCL_CHEM can be downloaded at https://uclchem.github.io/." (footnote 4)
- Missing: CASA version and imaging parameters
- Missing: Line-free channels
- Missing: MADCUBAIJ fit settings
- Missing: Model grid and best-fit procedure details
- Data volume (inferred): Several hundred GB across four projects (26 spectral windows)
- Score (inferred): 3/5, Public data and clear LTE recipe, but imaging parameters and fit settings absent.
- Rediscovery candidate: yes, Public data, LTE fit with numeric results, though imaging details must be reconstructed.

## Links

- Method: (cite: rivilla16a; rivilla16b) (MADCUBAIJ software)
- Companion: (cite: ligterink17) (Consistent CH3NCO detection at >=300 GHz)
- Companion: (cite: coutens16) (Isotopologue columns and compact emission of HNCO/NH2CHO)

## Checks

```json
{
 "quotes": 61,
 "quotes_ok": 61,
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
  "facts": 77,
  "stated": 38,
  "rate": 0.494
 },
 "evidence_ok": true
}
```

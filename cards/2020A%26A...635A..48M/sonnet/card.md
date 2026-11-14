# The ALMA-PILS survey: inventory of complex organic molecules towards IRAS 16293-2422 A

`2020A&A...635A..48M` | Astronomy and Astrophysics 2020 | first author: Manigand, S. | arXiv: 2001.06400 | DOI: 10.1051/0004-6361/201936299

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, astrochemistry
- Question: How do the abundances, rotational temperatures and spatial distributions of O-bearing complex organic molecules towards IRAS 16293A compare with those towards IRAS 16293B?  
  > "This paper aims to study the O-bearing COMs in the other protostar IRAS 16293A of the binary system and to compare their abundances with IRAS 16293B." (Introduction)
- Target **IRAS 16293-2422 A and B**: coordinates _not stated_; z/distance ~140 pc  
  > "which is located in the $\rho$ Ophiuchus cloud complex at a distance of $\sim$140 pc (cite: Dzib-2018)" (Introduction); "the spectra were extracted towards offset positions at 0.6$''$ from the continuum peak position in the north-east direction and 0.5$''$ in the south-west direction for IRAS 16293A and B, respectively." (2.2 Species identification); distance from Dzib et al. 2018  
  > "which is located in the $\rho$ Ophiuchus cloud complex at a distance of $\sim$140 pc (cite: Dzib-2018)" (Introduction); "the spectra were extracted towards offset positions at 0.6$''$ from the continuum peak position in the north-east direction and 0.5$''$ in the south-west direction for IRAS 16293A and B, respectively." (2.2 Species identification)

## Data provenance

- ALMA projects: 2013.1.00278.S, 2012.1.00712.S
- bands: _not stated_
- frequencies and spectral setup: 329.1-362.9 GHz, 0.244 MHz resolution (~0.2 km/s)  
  > "The observations cover the frequency range of 329.1 to 362.9 GHz with a spectral resolution of 0.244 MHz, corresponding to $\sim$0.2 km s$^{-1}$" (2.1 Observations)
- continuum bandwidth: _not stated_
- arrays: 12 m dishes plus ACA  
  > "The data are a combination of the 12 m dishes and the Atacama Compact Array (ACA)." (2.1 Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.5 arcsec restoring beam  
  > "a restoring beam of 0.5$''$" (2.1 Observations)
- max recoverable scale: _not stated_
- sensitivity: 4-5 mJy/beam km/s  
  > "The survey reaches a sensitivity of 4–5 mJy beam$^{-1}$ km s$^{-1}$ across the entire frequency range." (2.1 Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- External data: PILS reduced dataset and calibration  
  > "We used ALMA data from the PILS survey of the low-mass protostellar binary IRAS 16293 (cite: Jorgensen-2016)." (2.1 Observations) [from (cite: Jorgensen-2016)]
- External data: IRAS 16293B column densities, temperatures and D/H ratios from earlier PILS papers  
  > "previous studies of IRAS 16293B (cite: Coutens-2016; Lykke-2017; Persson-2018; Jorgensen-2018)" (Discussion) [from (cite: Jorgensen-2018)]
- External data: Laboratory spectroscopic data from CDMS/JPL and cited lab papers  
  > "Spectroscopic data for CH$_3^{18}$OH are provided in the Cologne Database of Molecular Spectroscopy" (Laboratory spectroscopic data) [from CDMS, JPL]

## Processing

### Calibration

- pipeline or manual: Data reduced with CASA following the PILS paper; continuum subtracted after reduction  
  > "The ALMA software suite CASA (cite: McMullin-2007) was used to reduce the data, except for the continuum subtraction, which was performed after the data reduction (cite: Jorgensen-2016)." (2.1 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: consistent at 5% level  
  > "The flux calibration across the spectral range is consistent with the 5% level." (2.1 Observations)
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
- final beam: 0.5 arcsec  
  > "a restoring beam of 0.5$''$" (2.1 Observations)
- final rms: _not stated_

### Inherited from earlier work

- Data reduction and calibration  
  > "CASA (cite: McMullin-2007) was used to reduce the data, except for the continuum subtraction, which was performed after the data reduction (cite: Jorgensen-2016)." (2.1 Observations) [from (cite: Jorgensen-2016)]
- Extraction positions as in previous PILS studies  
  > "This is in agreement with the choice of the extracted spectrum position in the previous PILS studies (cite: Calcutt-2018b; Jorgensen-2018; Lykke-2017)." (2.2 Species identification) [from (cite: Calcutt-2018b; Jorgensen-2018; Lykke-2017)]
- Filling factor 0.5 (source size 0.5 arcsec)  
  > "The filling factors of the gas emission, $\Omega$, is equal to 0.5 (cite: Jorgensen-2016), corresponding to a source size of 0$''$5." (2.3 LTE model) [from (cite: Jorgensen-2016)]
- Relative uncertainties for IRAS 16293B (~20% Trot, ~10% N)  
  > "For consistency, the relative uncertainty values used in the study of (cite: Jorgensen-2018) are assumed for IRAS 16293B" (2.5 Uncertainties) [from (cite: Jorgensen-2018)]
- VINE map method and CH3OH reference line  
  > "(cite: Calcutt-2018b) developed a new method to map the emission, called the velocity integrated emission map (VINE map)" (6.2 Spatial extent) [from (cite: Calcutt-2018b)]
- Column densities of CH3OCHO isotopologues for source A  
  > "from which the derived column densities for source A are taken" (Laboratory spectroscopic data) [from (cite: Manigand-2018)]

### Not stated but needed to reproduce (our reading)

- Exact continuum-subtraction procedure and line-free channels
- Exact spectrum extraction pixel coordinates (continuum peak positions not given)
- Number of Monte Carlo iterations
- Rms noise values per spectral window used in sigma_b
- Calibration uncertainty sigma_cal value in chi2
- CASA version
- The custom chi2 fitting code is not named or released
- Line-by-line list of lines included per species

## Analysis recipe

1. **Extract spectra at offset positions**: Spectra extracted at 0.6 arcsec NE of A and 0.5 arcsec SW of B continuum peaks  
  > "the spectra were extracted towards offset positions at 0.6$''$ from the continuum peak position in the north-east direction and 0.5$''$ in the south-west direction" (2.2 Species identification)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit LTE synthetic spectra for column density and Trot**: Grid chi2 fit of optically thin lines, Ntot 1e14-1e18 cm-2 and Trot 75-300 K in 5 K steps, species fitted iteratively from most to least abundant  
  > "ranging from 10$^{14}$ to 10$^{18}$ cm$^{-2}$ in logarithmic scale and from 75 to 300 K by increments of 5 K, respectively." (2.4 chi2-fitting)
   - parameter: FWHM 2.2-2.4 km/s, vlsr 0.8 km/s for A  
  > "a line width FWHM of 2.2–2.4 km s$^{-1}$, and a peak velocity $v_\text{lsr}$ of 0.8 km s$^{-1}$" (2.4 chi2-fitting)
   - parameter: Weight 3 when model exceeds data  
  > "The weighting factor $\omega(v)$ is equal to three if $T_b(v) > I_b(v)$, and it is one otherwise." (2.4 chi2-fitting)
   - parameter: Optically thin lines only (tau<0.1); unblended criteria  
  > "Only the optically thin lines, which have a line opacity lower than 0.1, are considered in the comparison of the modelled spectrum." (2.3 LTE model)
   - assumption: LTE, single Trot, filling factor 0.5, isotopologue Trot fixed to main species, continuum correction with Td 30.1 K (A), 21.2 K (B)  
  > "The dust brightness temperatures used in this paper are 30.1 K and 21.2 K towards the offset position from continuum peak positions towards IRAS16293A and B, respectively." (2.5 Uncertainties)
   - fitting: Modified chi2 minimisation over grid  
  > "The comparison between the observed spectrum and the model is quantified by the $\chi^2$ minimisation" (2.4 chi2-fitting)
   - validation: Compared with PILS B results and local ISM isotopic ratios  
  > "CH$_3^{18}$OH and H$_2$C$^{18}$O show a $^{16}$O/$^{18}$O ratio close to the local interstellar medium value" (3.1 Abundances)
3. **Estimate uncertainties**: Bootstrap-like Monte Carlo with Gaussian noise; conservative adopted ~20% Trot and ~30% N for A  
  > "we chose to take conservative values of $\sim$20 and $\sim$30% for the rotational temperatures and the column densities relative uncertainties, respectively, for IRAS 16293A." (2.5 Uncertainties)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compare abundances A vs B with statistical distance**: Abundances relative to CH3OH; S = difference of ratios over combined sigma for every species pair  
  > "we estimated the statistical distance $S$ of abundance ratios of each pair of species between IRAS 16293 A and B" (6.1 Comparison)
   - fitting: _not stated_
   - validation: _not stated_
5. **Map spatial distribution**: VINE maps shifting velocity range per pixel using CH3OH 337.519 GHz line  
  > "the same bright transition $7_{3,5}-6_{4,4}$ of CH$_3$OH at 337.519 GHz as used by (cite: Calcutt-2018b)" (6.2 Spatial extent)
   - fitting: _not stated_
   - validation: Maps used only to check emission reaches offset position  
  > "the VINE maps were only used to check whether the emission distribution reaches the offset position" (6.2 Spatial extent)
6. **Identify CHD2OH lines**: Gaussian fit per line with fixed vlsr and FWHM of CH3OH; integrated intensity over +-FWHM  
  > "each line was independently fitted to a simple Gaussian line profile in terms of amplitude and by using the same velocity peak $v_\text{lsr}$ and FWHM as CH$_3$OH" (4.3 Identification of CHD2OH lines)
   - fitting: Gaussian amplitude only  
  > "each line was independently fitted to a simple Gaussian line profile in terms of amplitude and by using the same velocity peak $v_\text{lsr}$ and FWHM as CH$_3$OH" (Results, Identification of CHD$_2$OH lines)
   - validation: _not stated_

## Software

- **CASA** : Data reduction  
  > "The ALMA software suite CASA (cite: McMullin-2007) was used to reduce the data" (2.1 Observations)
- **Astropy** : Python packages used in the research  
  > "including Astropy (cite: Astropy), Scipy (cite: Scipy), Numpy (cite: Numpy) and Matplotlib (cite: Matplotlib)" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CH3OH column density, IRAS 16293A | 1.3e19 | ±0.4e19 | cm-2 | 2 | / CH$_3$OH                  / 18                / $61-1201$           / $130\pm 26$             / $1.3\pm0.4\times10^{19}$ / |
| CH3OH Trot, IRAS 16293A | 130 | ±26 | K | 2 | / CH$_3$OH                  / 18                / $61-1201$           / $130\pm 26$             / $1.3\pm0.4\times10^{19}$ / |
| CH3OCH2OH column density towards B | 1.4e17 | ±0.2e17 | cm-2 | 2 | / CH$_3$OCH$_2$OH          / 130                  / $1.4\pm0.2\times10^{17}$   / $1.4\times10^{-2}$                   / |
| t-C2H5OCH3 column density towards B | 1.8e16 | ±0.2e16 | cm-2 | 2 | / *t*-C$_2$H$_5$OCH$_3$    / 100                  / $1.8\pm0.2\times10^{16}$   / $1.8\times10^{-3}$                   / |
| Mean 12C/13C towards A | 76 | ±12 | dimensionless | 2 | the mean $^{12}$C/$^{13}$C ratio of 76$\pm$12 towards IRAS 16293A is consistent with the local ISM value |
| Dust continuum correction factor | ~1.1 at 300 K to ~1.4 at 90 K | not stated | dimensionless | 2 | The value of the continuum correction factor ranges from $\sim$1.1 at 300 K to $\sim$1.4 at 90 K |

## Qualitative findings

- 15 species and 16 isotopologues securely detected towards A, 11 tentative  
  > "In total, 15 different species as well as 16 isotopologues, have been securely detected, while 11 additional species and isotopologues are tentatively identified towards IRAS 16293A." (3 Results)

## Claim tuples

- H: Do COM abundances relative to CH3OH differ between the two binary components? | E: LTE fits at offset positions and pairwise statistical distance | R: Half of the species are significantly lower towards A, at ~2 sigma (factor of two) | F: Selective differentiation with three categories of species | **supported**
- H: Is the abundance difference linked to spatial distribution and sublimation temperature? | E: VINE maps and Trot comparison | R: Depleted species are more compact around the continuum peak | F: Stratification of COMs in the hot corino | **partially**
- H: New O-bearing COMs in B? | E: Searches with LTE fits | R: CH3OCH2OH and t-C2H5OCH3 detected towards B; upper limits towards A | F: First detection in a low-mass star-forming region | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: CH3OH used as reference since H2 column density has only lower limits from optically thick dust  
  > "H$_2$ was not used as a reference for the estimation of the abundances because only the lower limit of H$_2$ column density can be determined from the optically thick dust emission." (3.1 Abundances)
- How they decided it was enough: _not stated_
- Limitation (authors): Statistical errors not conservative given LTE assumptions; neglected effects such as beam dilution and self-absorption  
  > "This suggests that the proper statistical estimate of the errors is not conservative considering the underlying hypotheses of the LTE model" (2.5 Uncertainties)
- Caveat (inferred, ours): Single offset position per source, so abundance differences may reflect spatial extent rather than chemistry
- Caveat (inferred, ours): Weight factor of three is arbitrary
- Caveat (inferred, ours): Adopted uncertainties are ad hoc, so 2 sigma significance is weak
- Caveat (inferred, ours): Abundances relative to CH3OH only

## Reproducibility

- Data public (paper): PILS reduced dataset available on website  
  > "The reduced dataset and all the publications are available on the website <http://youngstars.nbi.dk/PILS/>" (Introduction footnote)
- Products in archive: _not stated_
- Missing: Fitting code not released
- Missing: Exact extraction coordinates
- Missing: Line lists used per species
- Missing: CASA version
- Data volume (inferred): Large; ~100s GB raw; reduced PILS cubes tens of GB
- Score (inferred): 3/5, Public data and well-described LTE method, but custom code, positions and noise settings are unspecified.
- Rediscovery candidate: no, Requires custom fitting code and the PILS-reduced cubes, with many settings unstated.

## Links

- Method: Jorgensen et al. 2016 (cite: Jorgensen-2016) (PILS survey description and data reduction)
- Method: Calcutt et al. 2018b (cite: Calcutt-2018b) (VINE map method)
- Companion: Jorgensen et al. 2018 (cite: Jorgensen-2018) (IRAS 16293B COM analysis)
- Companion: Manigand et al. 2018 (cite: Manigand-2018) (CH3OCHO isotopologues)
- Related: PILS

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2012.1.00712.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 39,
  "rate": 0.5
 },
 "evidence_ok": true
}
```

# Laboratory spectroscopic study of the <SUP>15</SUP>N isotopomers of cyanamide, H<SUB>2</SUB>NCN, and a search for them toward IRAS 16293-2422 B

`2019A&A...623A..93C` | Astronomy and Astrophysics 2019 | first author: Coutens, Audrey | arXiv: 1901.00421 | DOI: 10.1051/0004-6361/201834605

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: astrochemistry, star_formation
- Question: Determine accurate spectroscopic parameters of 15N isotopomers of cyanamide from laboratory spectra and search for them in the ALMA PILS data toward IRAS 16293-2422 B  
  > "We wanted to determine spectroscopic parameters of the $^{15}$N isotopomers of cyanamide that are accurate enough for predictions well into the submillimeter region and to search for them in the PILS data." (abstract)
- Target **IRAS 16293-2422 B**: coordinates RA 16h32m22.58s, Dec -24d28m32.8s (J2000, continuum peak of source B; analysis position offset 0.5" from it)  
  > "($\alpha_{\rm J2000} =16^{\rm h}32^{\rm m}22.58s$, $\delta_{\rm J2000} = -24\ensuremath{^\circ}28\ensuremath{'}32.8\ensuremath{''}$)" (Astronomical search); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00278.S
- bands: Band 7  
  > "carried out in band 7 of ALMA and covering the spectral range 329.15$-$362.90 GHz at 0.244 MHz resolution" (Astronomical search)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: 7-10 mJy/beam/channel or 4-5 mJy/beam km/s  
  > "7$-$10 mJy beam$^{-1}$ channel$^{-1}$ or 4$-$5 mJy beam$^{-1}$ km s$^{-1}$" (Astronomical search)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **Cologne laboratory spectrometer**: Rotational spectra of cyanamide isotopologs, 192-507 GHz  
  > "to cover frequencies between 192 and 507 GHz" (Laboratory spectroscopic details and observed lines)
- External data: Earlier 15N and 13C isotopolog line lists (135-176 GHz etc.) used in fits  
  > "The line lists of the $^{15}$N isotopomers covered 135$-$176 GHz ($J'' = 6$ to 8)" (Introduction) [from (cite: H2NCN_isos_rot_2011)]
- External data: Main isotopolog H2NCN line list used for reanalysis  
  > "Our reanalysis of H$_2$NCN data started with the line list from (cite: H2_HD_D2NCN_rot_2013)." (Determination of spectroscopic parameters) [from (cite: H2_HD_D2NCN_rot_2013)]
- External data: H2N13CN column density 7e13 cm-2 and model parameters  
  > "A column density of $7 \times 10^{13}$ cm$^{-2}$ was obtained for the H$_2$N$^{13}$CN isotopolog." (Astronomical search) [from (cite: H2NCN_etc_solar-type_2018)]

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

- PILS survey data and details, observed spectra  
  > "Details of the survey have been presented by (cite: PILS_2016)." (Astronomical search) [from (cite: PILS_2016)]
- Same position, Tex, source size and FWHM as for H2NCN  
  > "Using the same position, $T_{\rm ex}$, source size, and $FWHM$ as for H$_2$NCN" (Astronomical search) [from (cite: H2NCN_etc_solar-type_2018)]

### Not stated but needed to reproduce (our reading)

- Calibration and imaging details of the PILS data
- Spectroscopic partition function and line catalog entries used for the LTE modeling
- Software used for the LTE modeling
- Rest frequencies and identity of the two H2(15)NCN lines
- Noise level used for the 3 sigma limit

## Analysis recipe

1. **Fit lab rotational spectra**: Fit of rotational spectra with SPCAT/SPFIT using reduced axis system Hamiltonian, Watson S reduction  
  > "We used Pickett’s SPCAT and SPFIT programs (cite: spfit_1991) to predict and fit rotational spectra of the minor isotopic species of cyanamide" (Determination of spectroscopic parameters)
   - software: SPCAT, SPFIT
   - parameter: Uncertainties 20-100 kHz; higher-order parameters scaled from main isotopolog  
  > "The uncertainties ranged from 20 kHz for isolated lines with symmetric line shape and good signal-to-noise ratio to 100 kHz." (Laboratory spectroscopic details and observed lines)
   - fitting: Parameters released stepwise until fit no longer improved  
  > "parameters of higher order were released until the qualities of the fits no longer significantly improved" (Determination of spectroscopic parameters)
   - validation: _not stated_
2. **LTE model of PILS spectra**: LTE modeling of emission lines at offset position to search for 15N isotopomers  
  > "The emission lines were modeled under the assumption of local thermodynamic equilibrium" (Astronomical search)
   - parameter: Tex = 300 K, source size 0.5", FWHM 1 km/s  
  > "with an excitation temperature $T_{\rm ex} = 300$ K, a source size of 0.5$\ensuremath{''}$, and a full line width at half maximum (*FWHM*) of 1 km s$^{-1}$" (Astronomical search)
   - fitting: _not stated_
   - validation: Checked that lines were not due to other identified species and no expected line was missing  
  > "We carefully checked that the two potential lines of H$_2^{15}$NCN were not due to any other species already identified toward this source" (Astronomical search)

## Software

- **SPCAT/SPFIT** : Predict and fit rotational spectra  
  > "We used Pickett’s SPCAT and SPFIT programs (cite: spfit_1991) to predict and fit rotational spectra" (Determination of spectroscopic parameters)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| H2(15)NCN column density (tentative, upper limit) | 6e13 | not stated | cm-2 | 2 | we obtain a good model for a column density of $6 \times 10^{13}$ cm$^{-2}$ |
| H2NC(15)N 3 sigma upper limit | 3e13 | not stated | cm-2 | 2 | A 3$\sigma$ upper limit of $3 \times 10^{13}$ cm$^{-2}$ is derived for H$_2$NC$^{15}$N. |
| 14N/15N lower limits | >=80 (H2(15)NCN), >=160 (H2NC(15)N) | not stated | dimensionless | 2 | $^{14}$N/$^{15}$N ratios of $\gtrsim$80 for H$_2^{15}$NCN and $\gtrsim$160 for H$_2$NC$^{15}$N |

## Qualitative findings

- Neither 15N isotopomer is unambiguously detected; two clean lines tentatively assigned to H2(15)NCN  
  > "Two relatively clean lines can be tentatively assigned to H$_2^{15}$NCN." (abstract)

## Claim tuples

- H: Can 15N cyanamide isotopomers be detected in PILS with new line lists? | E: Lab spectroscopy then LTE modeling of PILS data toward source B | R: Two possible H2(15)NCN lines, none for H2NC(15)N; limits 14N/15N >=80 and >=160 | F: No secure detection; more sensitive observations needed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Line-rich spectra, blending; more transitions needed  
  > "As the spectra of IRAS 16293$-$2422 are very line-rich, more transitions need to be detected to claim a secure detection." (Astronomical search)
- Caveat (inferred, ours): No fit uncertainty on the column density
- Caveat (inferred, ours): Tex and source size fixed to those of the 13C species
- Caveat (inferred, ours): No quantitative detection significance for the two lines

## Reproducibility

- Data public (paper): Line lists deposited at CDS and CDMS; PILS ALMA project code given  
  > "Files containing the experimental lines or parameters along with auxiliary files are available in the data section of the CDMS" (Conclusion and outlook)
- Products in archive: _not stated_
- Missing: PILS calibrated data processing details
- Missing: Modeling code
- Data volume (inferred): Large (PILS Band 7 full survey, hundreds of GB)
- Score (inferred): 3/5, Lab fits are reproducible with the deposited line lists; the astronomical part lacks code and calibration details.
- Rediscovery candidate: no, The ALMA part is a minor, qualitative search with few numeric results.

## Links

- Method: (cite: PILS_2016) (Survey description)
- Companion: (cite: H2NCN_etc_solar-type_2018) (Detection of cyanamide and isotopologs in PILS)
- Related: PILS

## Checks

```json
{
 "quotes": 26,
 "quotes_ok": 26,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 60,
  "stated": 20,
  "rate": 0.333
 },
 "evidence_ok": true
}
```

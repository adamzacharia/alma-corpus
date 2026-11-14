# ALMACAL V: absorption-selected galaxies with evidence for excited ISMs

`2019MNRAS.482L..65K` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Klitsch, A. | arXiv: 1810.01418 | DOI: 10.1093/mnrasl/sly187

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies, nearby_galaxies
- Question: What are the CO excitation (CO SLED) and molecular gas conditions of absorption-selected galaxies, and are Galactic CO line ratios and alpha_CO applicable?  
  > "We infer that the CO line ratios and the $\alpha_{\rm CO}$ conversion factor differ from the Galactic values." (abstract)
- Target **J0238A and J0238A1 (towards J0238+1636)**: coordinates J0238A: 02 38 38.94 +16 36 57.3; J0238A1: 02 38 39.01 +16 36 59.2 (J2000)  
  > "We discover two new molecular gas-rich galaxies with multiple CO emission lines detected at the redshift of an Hi absorber towards the quasar J0238$+$1636 at $z_{\rm abs} = 0.524$." (Sample and Reduction); z/distance z = 0.524  
  > "We discover two new molecular gas-rich galaxies with multiple CO emission lines detected at the redshift of an Hi absorber towards the quasar J0238$+$1636 at $z_{\rm abs} = 0.524$." (Sample and Reduction); distance from CO redshift / absorber redshift  
  > "We discover two new molecular gas-rich galaxies with multiple CO emission lines detected at the redshift of an Hi absorber towards the quasar J0238$+$1636 at $z_{\rm abs} = 0.524$." (Sample and Reduction)
- Target **J0423B (towards J0423-0120)**: coordinates 04 23 16.07 -01 20 52.1 (J2000)  
  > "Additionally, we include the molecular gas-rich galaxy detected in the field of J0423$-$0120 ($z_{\rm abs} = 0.633$) (cite: Klitsch2018) in our analysis." (Sample and Reduction); z/distance z = 0.633  
  > "Additionally, we include the molecular gas-rich galaxy detected in the field of J0423$-$0120 ($z_{\rm abs} = 0.633$) (cite: Klitsch2018) in our analysis." (Sample and Reduction); distance from from Klitsch2018 (cite: Klitsch2018)  
  > "Additionally, we include the molecular gas-rich galaxy detected in the field of J0423$-$0120 ($z_{\rm abs} = 0.633$) (cite: Klitsch2018) in our analysis." (Sample and Reduction)

## Data provenance

- ALMA projects: 2013.1.00989.S
- bands: Band 6 and Band 7 continuum used  
  > "We cannot use the Band 6 observations to measure the continuum flux of J0238A and J0238A1, because of strong residuals from the quasar continuum. In Band 7 we do not see any residuals" (Sample and Reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO 2-1, 3-2, 4-3 (not stated)
- Other facility **ALMACAL**: Calibrator observations from the ALMA archive forming the survey  
  > "ALMACAL, a (sub-)millimetre survey utilizing calibrator observations from the ALMA archive (cite: Oteo2016)" (Sample and Reduction)
- External data: J0423B properties, absorber gas properties, impact parameters  
  > "The properties of J0423B are taken from (cite: Klitsch2018)." (Table 1) [from (cite: Klitsch2018)]
- External data: Gas properties of absorbers and host galaxies  
  > "taken from (cite: Klitsch2018; Rao2006; Junkkarinen2004; Burbidge1996)" (Sample and Reduction) [from (cite: Klitsch2018; Rao2006; Junkkarinen2004; Burbidge1996)]
- External data: Starburst template spectra  
  > "We use a set of template spectra for starburst galaxies from (cite: Polletta2007)" (Sample and Reduction) [from (cite: Polletta2007)]

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

- Calibrator data retrieval  
  > "The retrieval of the calibrator data is described in detail in (cite: Oteo2016)" (Sample and Reduction) [from (cite: Oteo2016)]
- Calibration and data reduction  
  > "the calibration and data reduction are carried out as described in (cite: Klitsch2018)" (Sample and Reduction) [from (cite: Klitsch2018)]
- CO line flux to L'_line conversion  
  > "We convert the CO line flux to $L'_{\rm line}$ following the description from (cite: Solomon1992)." (Analysis) [from (cite: Solomon1992)]
- SFR from L_FIR  
  > "This is converted to the SFR using the (cite: Kennicutt1998) relation." (Sample and Reduction) [from (cite: Kennicutt1998)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration details
- Imaging parameters (weighting, robust, cell, size, tclean settings)
- Continuum subtraction and line-free channels
- Spectral setups, frequencies, array configurations, beams, rms of cubes
- Definition of w20 and aperture used
- Which template from Polletta2007 was used
- Quasar continuum subtraction method

## Analysis recipe

1. **Match absorbers to ALMACAL calibrators**: Cross-correlate absorber positions with calibrators and match CO frequency coverage with absorber redshift  
  > "Cross-correlating the sky positions of known absorbers detected at optical and UV wavelengths with the 749 calibrators in our ALMACAL catalogue leads to 109 positional matches." (Sample and Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract CO spectra and line fluxes**: Moment maps integrated over w20; spectra from aperture enclosing 3 sigma contours; line flux integrated over w20  
  > "The spectra are measured using an aperture that encompasses the $3\sigma$ contours in the moment map. The line flux is determined by integrating over $w_{20}$." (Sample and Reduction)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive SFR limits from continuum**: Scale starburst templates to 870 um flux, integrate 8-1000 um to get L_FIR, convert to SFR  
  > "The fitted spectrum is then integrated in the wavelength range from $8$ - $1000 \:\mu \text{m}$ to obtain the total far-infrared luminosity $L_{\rm FIR}$." (Sample and Reduction)
   - fitting: _not stated_
   - validation: _not stated_
4. **Construct CO SLEDs and compute molecular gas masses**: Normalize SLED to CO(2-1); convert CO(2-1) to CO(1-0) with r21 = 0.9 and derive masses in M_sun/alpha_CO  
  > "We convert the line luminosities using the median conversion factor $r_{21} = L'_{\rm CO(2-1)}/L'_{\rm CO(1-0)} = 0.9$ for LIRGs (cite: Papadopoulos2012a)." (Analysis)
   - assumption: LIRG-like r21 = 0.9; masses expressed in units of M_sun/alpha_CO  
  > "Instead, we argue that for the absorption-selected galaxies studied here, LIRG-like conversion factors are more appropriate." (Analysis)
   - fitting: _not stated_
   - validation: Compared with Milky Way, BzK, LIRG SLEDs and L'CO-LFIR relation  
  > "Comparing the L$'_{\rm CO}$–L$_{{\rm FIR}}$ relation we find that J0423B is consistent with local LIRGs" (Analysis)
5. **Test correlations of L_CO with impact parameter and N(HI)**: Pearson correlation coefficient with this sample and Kanekar2018  
  > "Using the Pearson correlation coefficient we find a correlation between $L_{\rm CO}$ and the impact parameter with a p-value of 0.01" (Discussion and Conclusion)
   - fitting: _not stated_
   - validation: Repeated excluding J0423B  
  > "we exclude it from the analysis resulting in p-values of 0.1 and 0.01" (Discussion and Conclusion)

## Software

- **Astropy** : Acknowledged as used in the research  
  > "This research made use of Astropy, a community-developed core Python package for Astronomy (cite: Astropy2018)." (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| log L'CO(2-1) J0238A | 9.07 | 0.06 | K km/s pc^2 | 2 | $9.07 \pm 0.06$ |
| log L'CO(2-1) J0423B | 10.28 | 0.02 | K km/s pc^2 | 2 | $10.28 \pm 0.02$ |
| Band 7 continuum 3 sigma upper limit J0238A/A1 | 0.1 | not stated | mJy | 3 | The $3 \sigma$ upper limit assuming that the galaxies are not resolved is 0.1 mJy. |
| SFR J0238A and A1 | <50 | not stated | M_sun/yr | 3 | $<50$ |
| log M_mol J0238A | 9.12 | 0.08 | M_sun/alpha_CO | 4 | $9.12 \pm 0.08$ |
| p-value L_CO vs impact parameter | 0.01 | not stated | dimensionless | 5 | correlation between $L_{\rm CO}$ and the impact parameter with a p-value of 0.01 |

## Qualitative findings

- CO SLEDs of J0238A and A1 are more excited than normal star-forming galaxies; J0423B only slightly steeper than the Milky Way  
  > "The CO SLEDs of J0238A and J0238A1 are clearly distinct from the CO SLED of the Milky Way or $BzK$ galaxies." (Analysis)

## Claim tuples

- H: Absorption-selected galaxies have CO excitation like normal star-forming galaxies | E: Compare CO SLEDs normalized to CO(2-1) with Milky Way and BzK galaxies | R: J0238A and A1 have more excited SLEDs; J0423B only slightly steeper than the Milky Way | F: Galactic line ratios and alpha_CO may not apply to some absorption-selected galaxies | **supported**
- H: L_CO correlates with impact parameter and N(HI) | E: Pearson correlation with Kanekar2018 sample | R: p = 0.01 and 0.002; 0.1 and 0.01 without J0423B | F: Only the impact-parameter correlation is rejected as null at 0.05 level; small sample | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): CO(1-0) not observed so SLEDs normalized to CO(2-1); small sample  
  > "the CO(1–0) emission line was not observed towards the absorption-selected galaxies" (Analysis)
- Caveat (inferred, ours): Only three galaxies; statistical correlations weak
- Caveat (inferred, ours): r21 and alpha_CO assumed from LIRGs without independent constraint
- Caveat (inferred, ours): Reduction details deferred to other papers

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging and calibration parameters
- Missing: Exact ALMA projects/EBs for J0238+1636
- Missing: Aperture definitions and template choice
- Data volume (inferred): tens of GB for the relevant calibrator datasets
- Score (inferred): 3/5, ALMA archival data but processing deferred to earlier papers and few parameters given.
- Rediscovery candidate: no, Processing recipe is incomplete and relies on ALMACAL and previous papers.

## Links

- Method: (cite: Oteo2016) (ALMACAL data retrieval)
- Method: (cite: Klitsch2018) (calibration and data reduction)
- Companion: (cite: Klitsch2018) (J0423B detection)
- Companion: (cite: Kanekar2018) (comparison sample of absorber CO hosts)
- Related: ALMACAL

## Checks

```json
{
 "quotes": 38,
 "quotes_ok": 38,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2012.1.00090.S",
  "2012.1.00245.S",
  "2012.1.00979.S",
  "2013.1.00001.S",
  "2013.1.00534.S",
  "2013.1.01225.S",
  "2015.1.00024.S",
  "2015.1.00187.S",
  "2015.1.00330.S",
  "2015.1.00419.S",
  "2015.1.00456.S",
  "2015.1.00598.S",
  "2015.1.00723.S",
  "2015.1.00932.S",
  "2015.1.01084.S",
  "2015.1.01144.S",
  "2015.1.01290.S",
  "2015.1.01503.S",
  "2016.1.00434.S",
  "2016.1.00505.S",
  "2016.1.00683.S",
  "2016.1.01010.S",
  "2016.1.01184.S",
  "2016.1.01262.S",
  "2016.1.01305.S",
  "2016.1.01435.S",
  "2016.1.01553.S"
 ],
 "codes_printed_but_missing": [
  "2012.1.00090.S",
  "2012.1.00245.S",
  "2012.1.00979.S",
  "2013.1.00001.S",
  "2013.1.00534.S",
  "2013.1.01225.S",
  "2015.1.00024.S",
  "2015.1.00187.S",
  "2015.1.00330.S",
  "2015.1.00419.S",
  "2015.1.00456.S",
  "2015.1.00598.S",
  "2015.1.00723.S",
  "2015.1.00932.S",
  "2015.1.01084.S",
  "2015.1.01144.S",
  "2015.1.01290.S",
  "2015.1.01503.S",
  "2016.1.00434.S",
  "2016.1.00505.S",
  "2016.1.00683.S",
  "2016.1.01010.S",
  "2016.1.01184.S",
  "2016.1.01262.S",
  "2016.1.01305.S",
  "2016.1.01435.S",
  "2016.1.01553.S"
 ],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 27,
  "rate": 0.37
 },
 "evidence_ok": true
}
```

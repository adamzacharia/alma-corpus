# Submillimeter wave spectroscopy of ethyl isocyanide and its searches in Orion

`2018A&A...610A..44M` | Astronomy and Astrophysics 2018 | first author: Margulès, L. | arXiv: - | DOI: 10.1051/0004-6361/201731515

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: astrochemistry, star_formation
- Question: Can new submillimeter laboratory spectroscopy of ethyl isocyanide give predictions accurate enough to search for CH3CH2NC in Orion KL and Sgr B2?  
  > "The extrapolation of the prediction in the millimeter wave domain is inaccurate and does not permit an unambiguous detection." (abstract)
- Target **Orion KL (EtCN1, EtCN2, EtCN3 positions)**: coordinates EtCN3 5h35m14.5s, -05d22m30.0s; EtCN1 5h35m14.6s, -05d22m27.9s; EtCN2 5h35m14.6s, -05d22m31.6s (J2000, as listed in Table 4; column assignment is partly ambiguous in the table)  
  > "α = 5 [h] 35 [m] 14. [s] 6 α = 5 [h] 35 [m] 14. [s] 6 α = 05 [h] 35 [m] 14. [s] 2" (Table 4); z/distance _not stated_; distance from _not stated_
- Target **Sgr B2 (N)**: coordinates 17h47m20.0s, -28d22m19.0s (J2000)  
  > "α = 17 [h] 47 [m] 20. [s] 0" (Table 4); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00009.SV
- bands: _not stated_
- frequencies and spectral setup: 213.7–246.7 GHz considered in the analysis  
  > "Frequency _[b]_ [GHz] 80–307 213.7–246.7 213.7–246.7 213.7–246.7 80–115.5" (Table 4)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: synthetic beam ~1.9 x 1.4 arcsec  
  > "HPBW _[a]_ [ [′′] ] 30–8 ∼1.9 × 1.4 ∼1.9 × 1.4 ∼1.9 × 1.4 30–21" (Table 4)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CH3CH2CN v20=1 24(2,22)-23(2,21) (219.632 GHz)
- Other facility **IRAM 30m**: Orion KL survey (López et al. 2014 results) and Sgr B2 3 mm data (Belloche et al. 2013)  
  > "we used the public data of Sgr B2 at 3 mm collected with the IRAM 30m telescope and provided by Belloche et al. (2013)." (4. Radioastronomical observations)
- Other facility **Lille submillimeter spectrometer**: Laboratory rotational spectra 150–990 GHz  
  > "The measurements in the frequency range under investigation (150–990 GHz) were performed using the Lille spectrometer" (2. Experimental section)
- External data: Orion KL IRAM 30m isocyanide column densities  
  > "The molecular column densities for these species derived by these authors are summarized in Table 4." (Table 4) [from López et al. (2014)]
- External data: CH3CN and CH3CH2CN column densities for EtCN1 and EtCN2  
  > "CH 3 CN and CH 3 CH 2 CN column densities for EtCN1 and EtCN2 (Positions A and B) from Cernicharo et al. (2016)." (Table 4) [from Cernicharo et al. (2016)]
- External data: Sgr B2(N) cyanide column densities and physical components  
  > "CH 3 CN, CH 3 CH 2 CN, and CH 2 CHCN column densities for Sgr B2 (N) from Belloche et al. (2013)." (Table 4) [from Belloche et al. (2013)]

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
- smoothing: 5 x 5 pixel spectrum extracted and averaged around emission peaks  
  > "Then, we extracted and averaged a 5 × 5 pixel spectrum around these emission peaks to search for ethyl isocyanide." (4. Radioastronomical observations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA SV observations and data reduction  
  > "(see, e.g., Tercero et al. 2015 for observations and data reduction)" (4. Radioastronomical observations) [from Tercero et al. 2015]
- Average kinetic temperature of 200 K  
  > "an average kinetic temperature of 200 K (see Daly et al. 2013; López et al. 2014)" (4. Radioastronomical observations) [from Daly et al. 2013; López et al. 2014]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration/imaging details of the ALMA SV data
- Detection limit criterion used for upper limits
- How the column density uncertainties were derived
- Pixel coordinates and size of the 5x5 pixel region
- Source sizes/line parameters per component beyond Table 5

## Analysis recipe

1. **Laboratory spectral fit**: Fit new transitions with previous data using Watson Hamiltonian, A and S reductions  
  > "For the fitting, we employed ASFIT (Kisiel 2001) and predictions were made with SPCAT (Pickett 1991)." (3. Analysis of the spectra)
   - software: ASFIT, SPCAT
   - fitting: _not stated_
   - validation: Compared A reduction with Krüger & Dreizler parameters; rms 30.3 vs 28.7 kHz  
  > "Using S reduction slightly decreases root mean square from 30.3 to 28.7 kHz." (3. Analysis of the spectra)
2. **Search for CH3CH2NC in ALMA SV and IRAM spectra**: Synthetic spectra from MADEX compared to observed spectra at three emission peaks, assuming Gaussian line parameters from CH3CH2CN v20=1 and Trot 200 K  
  > "We used the MADEX code (Cernicharo 2012) to derive the synthetic spectrum of methyl isocyanide according to the CH 3 CH 2 NC spectroscopy reported in this work" (4. Radioastronomical observations)
   - software: MADEX
   - parameter: Trot 200 K; source size 3 arcsec; vLSR and FWHM per Table 5  
  > "_T_ rot [K] 200 200 200 200" (Table 5)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **ASFIT** : Fitting rotational spectra  
  > "we employed ASFIT (Kisiel 2001)" (3. Analysis of the spectra)
- **SPCAT** : Predictions  
  > "predictions were made with SPCAT (Pickett 1991)" (3. Analysis of the spectra)
- **MADEX** : Synthetic spectra and column densities  
  > "We used the MADEX code (Cernicharo 2012)" (4. Radioastronomical observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| New assigned transitions | 2906 | not stated | dimensionless | 1 | We newly assigned 2906 transitions |
| Standard deviation of fit (A reduction) | 30.3 | not stated | kHz | 1 | Standard deviation of the fit (in kHz) 30.3 |
| N(CH3CH2NC) upper limit, Sgr B2 (N) | ≤1.5e16 | 0.5e16 | cm-2 | 2 | ≤(1.5 ± 0.5) × 10 [16] |
| CH3NC/CH3CN ratio in Sgr B2 (N) | 0.01 | not stated | dimensionless | 2 | we obtained a CH 3 NC/CH 3 CN column density ratio of 0.01. |

## Qualitative findings

- CH3CH2NC not detected in Orion KL or Sgr B2; CH3NC detected in both; CH2CHNC not detected in ALMA SV  
  > "We did not find ethyl isocyanide above the detection limit of the data." (4. Radioastronomical observations)

## Claim tuples

- H: New spectroscopy allows an accurate prediction up to 1 THz | E: Measured 150–990 GHz spectra and fitted with Watson Hamiltonian | R: 2906 new lines, J up to 103, rms 30.3 kHz | F: Predictions in the ALMA range are accurate | **supported**
- H: Ethyl isocyanide is detectable in Orion KL or Sgr B2 | E: Synthetic spectra compared with ALMA SV and IRAM 30m data | R: No detection; column density upper limits | F: Only upper limits derived | **supported**

## Reasoning

- Why this data: Public data of two prototypical high-mass star-forming regions rich in ethyl cyanide  
  > "we focused on public data of the two prototypical high-mass star-forming regions, Orion KL and Sgr B2." (4. Radioastronomical observations)
- Why this method: _not stated_
- Alternative: S reduction rejected because it needs 5 additional parameters for a marginal improvement  
  > "The A reduction requires 23 parameters, but 5 additional parameters are required for the S reduction (Table 2)." (3. Analysis of the spectra)
- How they decided it was enough: _not stated_
- Limitation (authors): Limited ALMA SV frequency band prevents ruling out the tentative CH2CHNC detection  
  > "owing to the limited frequency band of the ALMA SV data, we cannot disclaim the tentative detection of CH 2 CHNC reported by López et al. (2014)." (4. Radioastronomical observations)
- Caveat (inferred, ours): Upper-limit method and detection threshold not defined
- Caveat (inferred, ours): Uncertainties on upper limits not explained
- Caveat (inferred, ours): Assumed source size and Trot are not tested for sensitivity

## Reproducibility

- Data public (paper): Public ALMA SV and IRAM data used  
  > "we focused on public data of the two prototypical high-mass star-forming regions" (4. Radioastronomical observations)
- Products in archive: _not stated_
- Code: Fit files and prediction (.lin, .par, .cat) at CDS  
  > "The fitting files .lin (S2), .par (S3), and the prediction .cat (S4) are also available at CDS." (3. Analysis of the spectra)
- Missing: ALMA data reduction details
- Missing: Upper limit criterion
- Missing: Line lists used for blending assessment
- Data volume (inferred): tens of GB (ALMA SV Orion KL cubes)
- Score (inferred): 3/5, Spectroscopy is well documented and files are released; the astronomical search is only loosely specified.
- Rediscovery candidate: no, The ALMA part is a non-detection with loosely specified upper limits, and the recipe is incomplete.

## Links

- Method: Tercero et al. 2015 (ALMA SV Orion KL observations and data reduction)
- Method: Cernicharo 2012 (MADEX code)
- Companion: López et al. 2014 (Previous isocyanide search in Orion KL with IRAM 30m)
- Related: ALMA Science Verification Orion KL
- Related: IRAM 30m Orion KL survey

## Checks

```json
{
 "quotes": 35,
 "quotes_ok": 35,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 26,
  "rate": 0.388
 },
 "evidence_ok": true
}
```

# ALMA observations of the variability of the quiet Sun at millimeter wavelengths

`2021A&A...652A..92N` | Astronomy and Astrophysics 2021 | first author: Nindos, A. | arXiv: 2106.04220 | DOI: 10.1051/0004-6361/202141241

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: sun
- Question: Variability of the quiet solar chromosphere at 1.26 mm and 3 mm: spatially resolved p-mode oscillations and transient brightenings  
  > "We address the variability of the quiet solar chromosphere at 1.26 mm and 3 mm with a focus on the study of spatially resolved oscillations and transient brightenings" (abstract)
- Target **Quiet Sun region (12 April 2018)**: coordinates heliocentric about -132'', -398'' (mu ~ 0.9)  
  > "it was centered at heliocentric coordinates of about -132$''$, -398$''$ ($\mu \approx 0.9$)." (2 Data reduction); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: Band 6 (1.26 mm, 239 GHz) and Band 3 (3 mm, 100 GHz)  
  > "Band 6 at 1.26 mm (239 GHz)" (2 Data reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.6'' x 0.7'' (Band 6); 2.7'' x 1.7'' (Band 3)  
  > "spatial resolution of 1.6$''$ by 0.7$''$ for Band 6 and 2.7$''$ by 1.7$''$ for Band 3" (2 Data reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: Band 6: 8 scans (6 of ~7.9 min, 2 of ~2 min); Band 3: 6 scans (4 of ~9.9 min, 2 of ~6.9 min)  
  > "Each scan had a duration of about 7.9 min, with the exception of scans 4 and 8 which had a duration of about 2 min." (2 Data reduction)
- observing dates: 12 April 2018  
  > "Our observations took place on 12 April 2018" (2 Data reduction)
- pi or archival as stated: _not stated_
- Other facility **SDO/AIA**: 1600 and 304 A images for pointing correction and event comparison  
  > "comparison with simultaneous 1600 Å data taken with the Atmospheric Imaging Assembly (AIA; Lemen et al. 2012)" (2 Data reduction)
- Other facility **SDO/HMI**: magnetograms  
  > "Helioseismic and Magnetic Imager (HMI) aboard SDO magnetograms" (2 Data reduction)
- Other facility **GONG**: broadband H-alpha images  
  > "single frames of the best nearest H$\alpha$ images from the Global Oscillation Network Group (GONG)" (2 Data reduction)
- External data: Average quiet Sun brightness temperatures and Band 6 disk-center value (6343 K), emission height  
  > "the 1.26 mm background brightness temperature at disk center is 6343 K; see Alissandrakis et al. 2020" (5 Conclusions) [from Alissandrakis et al. 2020]
- External data: FAL C model densities  
  > "$\rho$ from the Fontenla et al. (1993) FAL C model" (3 Analysis of Oscillations) [from Fontenla et al. (1993)]

## Processing

### Calibration

- pipeline or manual: Calibrated visibilities received from JAO, using the Shimojo et al. 2017a scheme  
  > "From the Joint ALMA Observatory we received calibrated visibilities (their calibration employed the scheme described by Shimojo et al. 2017a)" (2 Data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: flux scale via ALMA Calibrator Device  
  > "whose flux calibration is established via the ALMA Calibrator Device" (2 Data reduction)
- flux scale uncertainty: _not stated_
- self calibration: four rounds of phase and one round of amplitude self-calibration  
  > "after four rounds of phase self-calibration and one round of amplitude self-calibration" (2 Data reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.25'' (Band 6), 0.5'' (Band 3)  
  > "The pixel size and diameter of the field of view of the images were 0.25$''$ and 46.5$\ensuremath{''}$ for Band 6 and 0.5$''$ and 110$\ensuremath{''}$ for Band 3." (2 Data reduction)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 1 s snapshot images combined with full-disk ALMA images to recover large scales and absolute Tb  
  > "all snapshot images were combined with contemporaneous full-disk ALMA images in order to recover large spatial scales" (2 Data reduction)
- smoothing: Band 6 deconvolved with its beam then convolved with Band 3 beam  
  > "the superior spatial resolution Band 6 images were first deconvolved with the Band 6 beam, and then convolved with the Band 3 beam" (3 Analysis of Oscillations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Snapshot/average CLEAN image computation  
  > "1 s snapshot images (see Nindos et al. 2018 for details)" (2 Data reduction) [from Nindos et al. 2018]
- PSD fitting function and p-mode rms  
  > "we followed Paper I and fitted the observed PSDs with an analytical function" (3 Analysis of Oscillations) [from Patsourakos et al. 2020 (Paper I)]
- Transient detection procedure and energy calculation  
  > "For the detection of transient brightenings we followed the procedure described in Paper II." (4.1 Detection) [from Nindos et al. 2020 (Paper II)]
- Noise evaluation via XX-YY  
  > "The evaluation of noise was done using the prescription described by Shimojo et al. (2017a)" (4.2 Properties) [from Shimojo et al. 2017a]

### Not stated but needed to reproduce (our reading)

- CASA version and imaging parameters (weighting, deconvolver, self-cal solints)
- Exact pointing offset values from the general-relativity correction
- Method to remove oscillations from light curves in detail (in Paper II)
- Treatment of the 2.5 sigma threshold sigma definition and network/intra-network segmentation thresholds
- Energy distribution binning and fit ranges
- Whether calibrated visibilities and full-disk images are in the public archive

## Analysis recipe

1. **Correct pointing and re-image**: Cross-correlate ALMA images with AIA 1600 A; re-compute average and 1 s snapshot CLEAN images with self-calibration; combine with full-disk images  
  > "We computed the actual pointing by cross-correlating the ALMA images with the 1600 Å images" (2 Data reduction)
   - software: CLEAN
   - fitting: _not stated_
   - validation: Offset consistent with general-relativistic radial offset  
  > "verified that the position offset we established was consistent with the general-relativistic radial offset" (2 Data reduction)
2. **Power spectra of oscillations**: Per-pixel light curves in blocks (scans 1-4, 5-8; 1-3, 4-6), zero-filled gaps, FT to PSD, averaged over 120x120 pixel FoV and blocks; fit log-normal plus linear in ln(nu)  
  > "zeroes were added to fill the blanks in the concatenated light curves." (3 Analysis of Oscillations)
   - parameter: Fit range lower 2-4 mHz, upper 30-50 mHz chosen by minimum chi^2  
  > "The lower and upper frequency employed in our analysis was the one leading to the smallest ${\chi}^{2}$." (3 Analysis of Oscillations)
   - fitting: chi^2 minimization of PSD model a0+a1 ln nu+a2 exp(...)  
  > "for each combination of lower and upper frequency that could be drawn from these intervals, we performed the PSD fitting and calculated the corresponding ${\chi}^{2}$." (3 Analysis of Oscillations)
   - validation: Residuals not exceeding ~20%; errors from difference between two blocks; gap correction factors 0.6 (Band 6), 0.7 (Band 3)  
  > "relatively small absolute residuals (blue solid lines) not exceeding $\approx 20 \%$." (3 Analysis of Oscillations)
3. **p-mode energy density**: epsilon = rho dv^2 with linear sound wave relation  
  > "For linear sound waves it is:" (3 Analysis of Oscillations)
   - assumption: gamma=5/3; rho from FAL C model  
  > "$\gamma=5/3$" (3 Analysis of Oscillations)
   - fitting: _not stated_
   - validation: _not stated_
4. **Detect transient brightenings**: Remove oscillations, then require >=4 consecutive points above 2.5 sigma, shared by a beam-size patch of 18 pixels, peaking within +-2 min; same on AIA 304/1600 with 1 point  
  > "at least four consecutive points in each “corrected” time profile should have intensity exceeding a 2.5$\sigma$ threshold above the mean intensity of the light curve" (4.1 Detection)
   - fitting: _not stated_
   - validation: Oscillatory power suppressed by factors 11-16; pairing with AIA within 15 s  
  > "by factors of 13 to 16 in Band 3, and by factors of 11 to 15 in Band 6" (4.1 Detection)
5. **Event energies and power-law fits**: Thermal free-free energy from excess Tb, FAL C electron density, and volume from area; power-law fits to frequency distributions  
  > "we assume that they emit thermal free-free radiation, the electron density and apparent volume do not change significantly in the course of the events, and that the filling factor is unity" (4.3 Energy budgets)
   - assumption: height equals horizontal size; filling factor unity  
  > "assuming their height is equal to their horizontal size" (4.3 Energy budgets)
   - fitting: Power-law fit with Poisson bin errors  
  > "derived from the propagation of errors associated with the histogram bins assuming Poisson statistics" (4.2 Properties)
   - validation: _not stated_

## Software

- **CLEAN** : average and snapshot images  
  > "we re-computed average CLEAN images synthesized from the entire observing interval" (2 Data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| p-mode rms, Band 6 original | 175 | 1 | K | 2 | 1.26 mm Band 6 original / $175\pm~1$ |
| p-mode rms, Band 3 original | 152 | 1 | K | 2 | 3.00 mm Band 3 original / $152\pm1$ |
| p-mode energy density at 1.26 mm | 3e-2 | not stated | erg cm^-3 | 3 | an energy density of $\approx 3 \times {10}^{-2} \mathrm{erg\,{cm}^{-3}}$ |
| Number of transient brightenings 1.26 mm / 3 mm | 77 / 115 | not stated | events | 4 | We detected 77 transient brightenings at 1.26 mm and 115 at 3 mm. |
| Energy power-law index 1.26 mm / 3 mm | 1.64 / 1.73 | 0.04 / 0.06 | dimensionless | 5 | indices of $1.64 \pm 0.04$ and $1.73 \pm 0.06$ for the 1.26 mm and 3 mm events |
| Noise levels Band 3 / Band 6 | 10.5 / 21.2 | not stated | K | 4 | We measured noise levels of 10.5 K and 21.2 K in Bands 3 and 6, respectively. |

## Qualitative findings

- Bright ALMA network structures correspond to dark mottles/spicules in broadband H-alpha  
  > "We also found that ALMA bright network structures corresponded to dark mottles/spicules seen in broadband H$\alpha$ images from the GONG network." (abstract)

## Claim tuples

- H: p-mode relative amplitude is similar at 1.26 and 3 mm when matched for resolution and FoV | E: PSD fits for four series | R: Fractional rms 1.7-1.8%; rms 137 and 109 K | F: Relative amplitude does not change appreciably between formation heights | **supported**
- H: Weaker, lower-energy events can be detected at 1.26 mm | E: Event detection and energy computation | R: Energies 1.8e23-1.1e26 erg at 1.26 mm; occurrence rate higher than at 3 mm | F: 1.26 mm low-end energies are among the smallest reported | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Observed p-mode rms is a lower limit since resolution is coarse and pixels are correlated  
  > "as a lower limit of the actual value" (5 Conclusions)
- Caveat (inferred, ours): Event detection depends on threshold choices and the oscillation-removal method
- Caveat (inferred, ours): Different regions (cell interior vs network) at the two bands confound comparisons
- Caveat (inferred, ours): Energy estimates assume filling factor unity and a FAL C model

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters and CASA version
- Missing: Oscillation removal algorithm details (Paper II)
- Missing: Pointing correction values
- Missing: Full-disk images and AIA data handling
- Data volume (inferred): tens to hundreds of GB (solar time-series visibilities); not stated
- Score (inferred): 3/5, Data public project but custom solar processing, inherited methods from Papers I/II and missing parameters hinder reproduction.
- Rediscovery candidate: no, Recipe relies on earlier papers and unspecified solar imaging steps.

## Links

- Method: Shimojo et al. 2017a (Solar calibration and noise prescription)
- Method: Nindos et al. 2020 (Paper II) (Transient detection and energy method)
- Method: Patsourakos et al. 2020 (Paper I) (PSD fitting method)
- Companion: Jafarzadeh et al. 2021 (Earlier oscillation analysis of the same data)
- Companion: Alissandrakis et al. 2020 (Brightness temperature calibration values)

## Checks

```json
{
 "quotes": 46,
 "quotes_ok": 46,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2017.1.00653.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 37,
  "rate": 0.507
 },
 "evidence_ok": true
}
```

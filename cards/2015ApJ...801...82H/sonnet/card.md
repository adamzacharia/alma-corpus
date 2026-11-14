# ALMA Imaging of Millimeter/Submillimeter Continuum Emission in Orion KL

`2015ApJ...801...82H` | The Astrophysical Journal 2015 | first author: Hirota, Tomoya | arXiv: 1502.00458 | DOI: 10.1088/0004-637X/801/2/82

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: What are the compact continuum sources in Orion KL at ALMA bands 6 and 7, what are their dust graybody properties, and what does the centimeter-to-submillimeter SED of Source I imply for its emission mechanism (H- free-free plus dust)?  
  > "In order to reveal physical properties of continuum sources in Orion KL, in particular Source I, we present observational study of multi-band continuum emission with the sub-arcsecond resolution by using ALMA." (Introduction)
- Target **Orion KL**: coordinates RA(J2000)=05h35m14.1250s, Decl(J2000)=-05d22'36.486'' (tracking center)  
  > "Located at a distance of 420 pc from the Sun (cite: hirota2007; menten2007; kim2008)" (Introduction); "RA(J2000)=05h35m14.1250s, Decl(J2000)=-05d22$'$36.486$''$" (2.1 Band 6 data); z/distance 420 pc  
  > "Located at a distance of 420 pc from the Sun (cite: hirota2007; menten2007; kim2008)" (Introduction); "RA(J2000)=05h35m14.1250s, Decl(J2000)=-05d22$'$36.486$''$" (2.1 Band 6 data); distance from hirota2007; menten2007; kim2008  
  > "Located at a distance of 420 pc from the Sun (cite: hirota2007; menten2007; kim2008)" (Introduction); "RA(J2000)=05h35m14.1250s, Decl(J2000)=-05d22$'$36.486$''$" (2.1 Band 6 data)

## Data provenance

- ALMA projects: 2011.0.00199.S, 2011.0.00009.SV
- bands: Band 6 (245 GHz) and Band 7 (339 GHz)  
  > "We identify 11 compact sources at ALMA band 6 (245 GHz) and band 7 (339 GHz)" (abstract)
- frequencies and spectral setup: Band 6: 240-244 and 256-260 GHz, 4 SPWs of 2 GHz; Band 7 continuum: 341.5-345.4 and 353.5-357.5 GHz  
  > "The observed frequency ranges were 240$-$244 GHz and 256$-$260 GHz consisted of 4 spectral windows with bandwidth of 2 GHz for each." (2.1 Band 6 data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Band 6 cycle 0 extended; SV compact; Band 7 extended  
  > "The observation in cycle 0 was done in the extended configuration on 2012 April 08 with 17$\times$12 m antennas." (2.1 Band 6 data)
- baselines: Band 6 cycle 0: 17-310 klambda; SV: 14-203 klambda; Band 7 continuum: 19-425 klambda  
  > "The baseline lengths ranged from 17 to 310 k$\lambda$ (from 21 to 385 m)." (2.1 Band 6 data)
- angular resolution: uv>100 klambda beams 0.63x0.47 arcsec (245 GHz), 0.46x0.41 arcsec (339 GHz)  
  > "| uv$>$100 k$\lambda$ | 245 | ... | ... | ... | ... | 0.63$\times$0.47 | -72 | 5 |" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: rms 5 mJy/beam (uv>100 klambda) in both bands  
  > "| uv$>$100 k$\lambda$ | 339 | ... | ... | ... | ... | 0.46$\times$0.41 | 57 | 5 |" (Table 1)
- time on source: Band 6 cycle 0: 30 s; Band 7 continuum: 100 s  
  > "The total on-source integration time was 30 s." (2.1 Band 6 data)
- observing dates: 2012 Jan 20 (SV), Apr 08, Jul 16, Aug 25, Oct 21, Oct 23  
  > "| 7 | Oct. 23 | 350 | 8000 | 3641 | 23 | 100.8 | 0.47$\times$0.44 |   0 | 9 |" (Table 1)
- pi or archival as stated: _not stated_
- Other facility **CARMA 90 GHz and 229 GHz, SMA, VLA, BIMA**: Literature flux densities for the SED of Source I and 3 mm data for graybody fits  
  > "| 229    | 310$\pm$45 | 150$\times$130 | CARMA | 2009.1 | Y | (cite: plambeck2013) |" (Table 6)
- External data: 3 mm (90 GHz) continuum peak intensities  
  > "$^{a}$ See Table 1 in (cite: friedel2011)." (Table 4) [from (cite: friedel2011)]
- External data: Source I SED flux densities from cm to submm  
  > "we plot a SED of Source I as shown in Figures [5](#fig-sed) and Table [6](#tab-flux) (cite: plambeck2013)." (4.1 Source I) [from (cite: plambeck2013)]
- External data: Source I apparent size 0.20 x 0.03 arcsec  
  > "The apparent size of Source I of 0.20$''$$\times$0.03$''$  is employed (cite: plambeck2013)" (H- free-free emission) [from (cite: plambeck2013)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto (primary flux calibrator)  
  > "A primary flux calibrator, band-pass calibrator, and secondary gain calibrator were Callisto, J053851-440507, and J0607-085, respectively." (2.1 Band 6 data)
- flux scale uncertainty: 20%  
  > "we estimate the accuracy of the flux measurement to be 20%." (3 Results)
- self calibration: Phase and amplitude self-calibration with continuum images (gaincal, applycal)  
  > "Both phase and amplitude self-calibrations were done with the continuum images by the CASA task `gaincal` and these results were applied to the visibility data by the CASA task `applycal`." (2.3 Synthesis imaging)

### Imaging

- task: CASA clean; concat to combine datasets  
  > "After combining the data, continuum images of Orion KL were made using the CASA task `clean`." (2.3 Synthesis imaging)
- deconvolver: _not stated_
- weighting robust: uniform weighting  
  > "the uniform-weighted synthesized beam size were summarized in Table [1](#tab-obs)." (2.3 Synthesis imaging)
- uv taper: uv>100 klambda cut for compact source identification  
  > "we made synthesized images by employing only baselines longer than 100 k$\lambda$" (3 Results)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: Continuum made by integrating line-free channels; effective bandwidth about half  
  > "The line emissions were excluded to make continuum images by integrating over the line-free channels." (2.3 Synthesis imaging)
- primary beam correction: Flux densities measured after primary beam correction  
  > "The flux densities are measured by employing the images after correction of primary beam attenuation." (3 Results)
- array combination: SV band 6 (230-232 GHz) concatenated with cycle 0; band 7 continuum and line-mode data concatenated  
  > "For the band 6 data, we combined calibrated SV and cycle 0 data by using the task `concat` in CASA." (2.3 Synthesis imaging)
- smoothing: _not stated_
- final beam: Band 6 0.63x0.47 arcsec; Band 7 0.46x0.41 arcsec (uv>100 klambda)  
  > "| uv$>$100 k$\lambda$ | 245 | ... | ... | ... | ... | 0.63$\times$0.47 | -72 | 5 |" (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- Dust opacity kappa=0.1 cm2/g at 1.2 THz, gas-to-dust 100  
  > "$\kappa_{\nu_{0}}=0.1$ cm$^{2}$ g$^{-1}$ at $\nu_{0}=1.2$ THz, or wavelength of 250$\mu$m, is adopted (cite: hildebrand1983)" (5.2 Graybody) [from (cite: hildebrand1983)]
- H- free-free formalism  
  > "Here we follow the discussion by (cite: reid1997) to construct a SED of Source I" (Appendix) [from (cite: reid1997)]
- Dust temperatures 100 K and 20 K  
  > "we assume the temperature of 100 K as obtained from the molecular line observations (cite: favre2011) and lower value of 20 K (cite: eisner2008) for comparison." (5.2 Graybody) [from (cite: favre2011); (cite: eisner2008)]

### Not stated but needed to reproduce (our reading)

- clean parameters (weighting beyond uniform, cell, image size, niter, threshold, masks)
- CASA version and calibration procedure for cycle 0 data
- self-calibration solution intervals and reference images
- line-free channel selection
- fitting method/software for graybody and power-law SED
- table of derived masses, sizes and densities (Table 5 not rendered)
- how upper-limit uncertainties handled when 90 GHz missing

## Analysis recipe

1. **Combine data and make continuum images**: concat of calibrated datasets, clean of line-free channels, self-calibration, uv>100 klambda images  
  > "For band 7 data, we combined all of the calibrated data for both in continuum and spectral line mode by using the CASA task `concat`." (2.3 Synthesis imaging)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared single-epoch continuum with combined line-mode epochs; flux accuracy 20%  
  > "both results are in good agreement with each other." (3 Results)
2. **Identify compact sources and measure positions/fluxes**: 2D Gaussian fit with imfit on uv>100 klambda primary-beam-corrected images; detection threshold 5 sigma in both bands  
  > "we conservatively regard the sources as real detections if their signal-to-noise ratio greater than 5 for both bands 6 and 7." (3 Results)
   - software: CASA imfit
   - fitting: _not stated_
   - validation: _not stated_
3. **Graybody SED fit for masses and densities**: Fit 245, 339 GHz (and 90 GHz when available) peak intensities to optically thin graybody with beta free  
  > "Thus we fit the observed flux densities at 245 GHz, and 339 GHz as listed in Table [4](#tab-cont) to the graybody function;" (5.2 Graybody)
   - parameter: Tdust fixed to 100 K or 20 K  
  > "we assume the temperature of 100 K as obtained from the molecular line observations (cite: favre2011) and lower value of 20 K (cite: eisner2008) for comparison." (5.2 Graybody)
   - assumption: kappa=0.1 cm2/g at 250 um, gas-to-dust 100, D=420 pc  
  > "assuming the gas to dust mass ratio of 100." (5.2 Graybody)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit Source I SED with power law and power law plus graybody**: Single power law log F = p + q log nu over 8.4-690 GHz, then power law + graybody; H- free-free model for turnover frequency, density, temperature  
  > "with the power law index $q$ of 1.97$\pm$0.10 for the frequency range between 8.4 GHz and 690 GHz." (4.1.1)
   - parameter: Disk 0.20x0.03 arcsec = 84 AU x 12.6 AU, edge-on, uniform density and temperature  
  > "Hereafter we assume that Source I is an edge-on disk with uniform density and temperature for simplicity." (4.1.1)
   - assumption: Dust temperature 100 K for graybody component  
  > "assuming the dust to gas mass ratio of 100 and the dust temperature of 100 K" (4.1.2)
   - fitting: _not stated_
   - validation: Compared model flux densities with observed; noted deviations  
  > "Still the fitting result shows a significant deviation from the observed flux densities." (abstract)

## Software

- **CASA** : Calibration, concat, clean, gaincal/applycal, imfit  
  > "The data were calibrated and imaged with the Common Astronomy Software Applications (CASA) package." (2.3 Synthesis imaging)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of compact sources | 11 | not stated | dimensionless | 2 | As a result, we identify total 11 sources as listed in Tables [2](#tab-band6) and [3](#tab-band7). |
| Source I single power-law index q | 1.97 | 0.10 | dimensionless | 4 | / Single power law     / -1.99(19) / 1.97(10) /            ...            /   ...    / |
| Source I power law+graybody index q | 1.60 | 0.24 | dimensionless | 4 | / power law$+$graybody / -1.51(30) / 1.60(24) /         0.082(49)         / 1.34(83) / |
| Source I graybody mass (100 K) | 0.082 | 0.049 | Msun | 4 | / power law$+$graybody / -1.51(30) / 1.60(24) /         0.082(49)         / 1.34(83) / |
| Source I (HKKH4) band 7 peak | 849 | 29 | mJy/beam | 2 | / 4 / 14.5113(5) / 30.571(7) / 0.50(2) $\times$ 0.44(1) / 126(5) / 1001(34) / 849(29) / |
| Source I (HKKH4) band 6 peak | 272 | 13 | mJy/beam | 2 | / 4 / 14.5073(10) / 30.603(12) / 0.66(2) $\times$ 0.47(3) / 124(2) / 284(14) / 272(13) / |
| Masses of compact sources at 20 K | 0.08-0.27 | not stated | Msun | 3 | The derived masses (0.08$M_{\odot}$-0.27$M_{\odot}$ for assumed temperature of 20 K) |

## Qualitative findings

- Source I SED is consistent with optically thick emission up to submm; H- free-free requires T of 1200-3000 K and n of 1e11-1e14 cm-3  
  > "total hydrogen density of 10$^{11}$-10$^{14}$ cm$^{-3}$ are required to account for the SED with a single power-law index of 2.0 under the temperature of 1200-3000 K" (Summary)

## Claim tuples

- H: Compact continuum sources in Orion KL can be identified and characterized with ALMA bands 6 and 7 | E: uv>100 klambda imaging, 5 sigma detection, imfit | R: 11 sources detected in both bands | F: Compact sources have masses of ~0.08-0.27 Msun (20 K), sizes 200-300 AU, consistent with disk-like or core origins but unresolved nature | **supported**
- H: Source I SED is explained by H- free-free emission | E: Power-law fit and H- opacity model | R: q=1.97 single power law; 1.60 with dust graybody | F: H- free-free fits with caveats; size/temperature degenerate and fit deviates from data | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Uniform 100 klambda cut chosen to find compact sources and suppress sidelobes  
  > "In order to identify compact continuum sources, we made synthesized images by employing only baselines longer than 100 k$\lambda$" (3 Results)
- Alternative: Proton-electron free-free from compact HII region ruled out as main opacity from size and brightness temperature ~1500 K at 43 GHz  
  > "the free-free emission from such a compact H region is ruled out as a main opacity source of continuum emissions" (4.1.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Missing flux and lack of short baselines; BN outside field of view; flux calibration unreliable for sources outside primary beam; no size correction in SED  
  > "In the present analysis, we do not make any correction for above flux densities such as the different source/beam sizes" (4.1.2)
- Caveat (inferred, ours): Temperatures assumed rather than fitted; masses depend strongly on this
- Caveat (inferred, ours): Heterogeneous literature fluxes with different beams and uv coverage mixed in SED
- Caveat (inferred, ours): Only two ALMA points; beta poorly constrained
- Caveat (inferred, ours): Short on-source times and limited uv coverage

## Reproducibility

- Data public (paper): ALMA cycle 0 and SV data cited by project code  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00009.SV and 2011.0.00199.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: clean parameters and CASA version
- Missing: self-calibration details
- Missing: Table 5 graybody results
- Missing: fitting code for SEDs
- Data volume (inferred): ~10-30 GB
- Score (inferred): 3/5, Data public and steps outlined, but imaging and fitting parameters mostly unstated.
- Rediscovery candidate: no, Imaging parameters and SED fitting method are insufficiently specified.

## Links

- Method: (cite: reid1997) (H- free-free formalism)
- Companion: (cite: hirota2014a) (Same cycle 0 band 7 H2O line monitoring data)
- Companion: (cite: plambeck2013) (CARMA SED of Source I)
- Related: ALMA Science Verification Orion KL

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 45,
  "rate": 0.643
 },
 "evidence_ok": true
}
```

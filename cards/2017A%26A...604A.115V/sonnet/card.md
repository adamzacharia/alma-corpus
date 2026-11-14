# The correct estimate of the probability of false detection of the matched filter in weak-signal detection problems . II. Further results with application to a set of ALMA and ATCA data

`2017A&A...604A.115V` | Astronomy and Astrophysics 2017 | first author: Vio, R. | arXiv: 1705.03285 | DOI: 10.1051/0004-6361/201629330

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type archival_reuse

## Science

- Fields: other, star_formation
- Question: How to quantify the reliability of individual weak point-source detections in matched-filtered maps via a specific probability of false alarm (SPFA), and whether it reveals faint sources in ALMA and ATCA maps  
  > "in this work we introduce the so-called specific probability of false alarm (SPFA), which is able to provide a precise (within a few percent) quantification of the reliability of a detection." (Introduction)
- Target **PKS0745-19 BCG field**: coordinates RA 07:47:31.3, Dec -19:17:39.94 (J2000)  
  > "centered on the bright cluster galaxy (BCG) of PKS0745-19 (RA 07:47:31.3, Dec -19:17:39.94, J2000)" (6 Application to real ALMA maps); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00837.S
- bands: Band 3 (100 GHz, 3 mm) and Band 7 (340 GHz, 0.87 mm)  
  > "100 {\rm GHz}$ ($3 {\rm mm}$, ALMA band 3), whereas the second map (hereafter M2) was obtained at a frequency of $340 {\rm GHz}$ ($0.87 {\rm mm}$, ALMA band 7)" (6 Application to real ALMA maps)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.9" x 1.4" (Band 3); 0.27" x 0.19" (Band 7)  
  > "The beam size is 1.9” $\times$ 1.4” in band 3, and 0.27” $\times$ 0.19” in band 7." (6 Application to real ALMA maps)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PI R. McNamara; CO line was the original target  
  > "free of the CO line emission, which was the original observation target" (6 Application to real ALMA maps)
- Other facility **ATCA**: 4.8 GHz map of the LMC from Dickel et al. 2005, used as a second test  
  > "radio image taken with the ATCA array toward the Large Magellanic Cloud at a frequency of $4.8~{\rm GHz}$ by (cite: dic05)" (7 Application to a real ATCA map)
- External data: ATCA 4.8 GHz LMC radio image (500x500 pixel crop)  
  > "radio image taken with the ATCA array toward the Large Magellanic Cloud at a frequency of $4.8~{\rm GHz}$ by (cite: dic05)" (7 Application to a real ATCA map) [from Dickel et al. 2005 (cite: dic05)]
- Simulation/model as data: Simulated 300x300 pixel map with 30 Gaussian point sources (sigma 1.3 and 1.8 pixels) of amplitude equal to the noise sigma, in Gaussian white noise  
  > "simulated $300 \times 300$ pixels map where $30$ point sources, with a uniform random spatial distribution and Gaussian profile" (5 A numerical experiment)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.2.2 with ALMA reduction scripts  
  > "The data reduction was carried out with CASA version 4.2.2 and the ALMA reduction scripts (cite: mcm07)." (6 Application to real ALMA maps)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean, Briggs weighting  
  > "The images were reconstructed via the CASA task *clean* with Briggs weighting and a robust parameter of 1.5 in band 3 and 2 in band 7." (6 Application to real ALMA maps)
- deconvolver: _not stated_
- weighting robust: robust = 1.5 (Band 3), 2 (Band 7)  
  > "a robust parameter of 1.5 in band 3 and 2 in band 7" (6 Application to real ALMA maps)
- uv taper: _not stated_
- cell size: _not stated_
- image size: 256 x 256 pixels  
  > "Both maps, with a size of $256 \times 256$ pixels" (6 Application to real ALMA maps)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum from averaging channels free of CO line emission  
  > "we selected and averaged only the channels free of the CO line emission" (6 Application to real ALMA maps)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Band 3 and Band 7 maps combined with CASA Feather into M3  
  > "Such operation was carried out by the algorithm Feather implemented in CASA (cite: mcm07)." (6 Application to real ALMA maps)
- smoothing: _not stated_
- final beam: 1.9" x 1.4" (B3); 0.27" x 0.19" (B7)  
  > "The beam size is 1.9” $\times$ 1.4” in band 3, and 0.27” $\times$ 0.19” in band 7." (6 Application to real ALMA maps)
- final rms: _not stated_

### Inherited from earlier work

- Correct PFA for matched filter via peak PDF of Gaussian random fields  
  > "The same authors have provided an alternative procedure to correctly compute this quantity." (Introduction) [from Vio & Andreani 2016 (cite: vio16)]
- PDF and expected number of local maxima of Gaussian random fields  
  > "are given by (cite: che15a; che15b)" (4 Extension of matched filter to the two-dimensional case) [from Cheng & Schwartzman 2015a,b (cite: che15a; che15b)]

### Not stated but needed to reproduce (our reading)

- Line-free channel selection and spectral setup
- Number of iterations, threshold, and mask for clean
- Pixel (cell) size of the maps
- Calibration details and the CASA pipeline/manual choice
- Source masking regions and how the Gaussian filtering scale was set
- Code for the SPFA computation (not released)
- Flux-scale uncertainty

## Analysis recipe

1. **Build continuum maps**: CASA clean with Briggs weighting on line-free channels  
  > "The images were reconstructed via the CASA task *clean* with Briggs weighting and a robust parameter of 1.5 in band 3 and 2 in band 7." (6 Application to real ALMA maps)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Mask bright sources and check noise**: Mask BCG and a known IR source; check Gaussianity via histograms and noise correlation functions  
  > "the pixels in the masked areas are not used in the analysis." (6 Application to real ALMA maps)
   - fitting: _not stated_
   - validation: Histograms and autocorrelation functions  
  > "indicate that the noise is Gaussian but, as shown by the two-point autocorrelation functions in Figs. [12](#fig12)(a)-(b), not white." (6 Application to real ALMA maps)
3. **Find peaks, estimate kappa, threshold by PFA**: Maximum likelihood estimate of kappa from peaks; threshold at PFA=1e-3 (u≈3.98) using the peak PDF  
  > "A threshold $u \approx 3.98$, corresponding to a PFA [\[eq:corra\]](#eq:corra) equal to $10^{-3}$, provides two candidate point sources in M1 and four in M2." (6 Application to real ALMA maps)
   - assumption: Matched filter reduces to thresholding (T = x) since sources are unresolved  
  > "In this case $\mathcal{T}(\boldsymbol{x}, i_0) = \boldsymbol{x}$ and the detection test becomes a thresholding test" (6 Application to real ALMA maps)
   - fitting: Maximum likelihood for kappa  
  > "The maximum likelihood estimate [\[eq:ml\]](#eq:ml) provides $\hat{\kappa}\approx 1$ for both M1 and M2" (6 Application to real ALMA maps)
   - validation: Bootstrap confidence band on peak correlation (1000 resamples) and 5000 simulated Gaussian fields to check iid  
  > "computed from $1000$ resampled sets of peaks with the same spatial coordinates as in the original map but whose values have been randomly permuted" (6 Application to real ALMA maps)
4. **Compute SPFA and Poisson-binomial false detection counts**: alpha = 1-[Psi(z_max)]^Np per peak, removing confirmed detections; Poisson-binomial for N_FD  
  > "& = 1-\left[ \Psi(z_{\rm max}) \right]^{N_p}." (3 Specific probability of false alarm)
   - fitting: _not stated_
   - validation: Tested on simulated map with known sources  
  > "This result is in good agreement with the true $N_{\rm FD} =6$." (5 A numerical experiment)
5. **Measure fluxes of detected sources**: Integrated flux over assumed Gaussian PSF using CASA statistics  
  > "We computed the fluxes with the CASA statistics tool." (6 Application to real ALMA maps)
   - software: CASA
   - assumption: Sources unresolved, PSF Gaussian  
  > "Since our sources are not resolved, to estimate the flux we measured the integrated flux over the PSF, which is assumed to have a Gaussian shape." (6 Application to real ALMA maps)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2.2: Data reduction, clean imaging, Feather combination, statistics for fluxes  
  > "The data reduction was carried out with CASA version 4.2.2 and the ALMA reduction scripts (cite: mcm07)." (6 Application to real ALMA maps)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Peaks identified in M1 | 328 | not stated | count | 3 | We identified $328$ peaks in M1 and $948$ in M2. |
| Peaks identified in M2 | 948 | not stated | count | 3 | We identified $328$ peaks in M1 and $948$ in M2. |
| SPFA of sources 1a, 2a in M1 | 8.8e-2, 2.0e-2 | not stated | dimensionless | 4 | in M1 the SPFA is $8.8 \times 10^{-2}$ and $2.0 \times 10^{-2}$ for the sources 1a and 2a |
| SPFA of sources 1b-4b in M2 | 5.7e-1, 5.0e-1, 1.4e-1, 1.3e-1 | not stated | dimensionless | 4 | whereas in M2 it is $5.7 \times 10^{-1}$, $5.0 \times 10^{-1}$, $1.4 \times 10^{-1}$, and $1.3 \times 10^{-1}$ for the sources 1b-4b |
| Integrated flux of source 1b (Band 7) | 0.78 (RMS 0.06) | not stated | mJy | 5 | / 1b                      / 0.78                  / 0.06      / |
| Integrated flux of BCG in Band 3 | 9.00 (RMS 0.18) | not stated | mJy | 5 | / BCG PKS0745-191         / 9.00                  / 0.18      / |
| kappa estimate in M3 | 0.96 | not stated | dimensionless | 3 | These peaks provide a maximum likelihood estimate $\hat{\kappa}=0.96$. |
| SPFA of sources 1c-3c in M3 | 3.2e-1, 2.7e-1, 4.0e-3 | not stated | dimensionless | 4 | The SPFA is equal to $3.2 \times 10^{-1}$, $2.7 \times 10^{-1}$ and $4.0 \times 10^{-3}$ for the detections 1c-3c, respectively. |

## Qualitative findings

- Standard Gaussian PFA would give 104 (M1), 294 (M2) and 326 (M3) detections at the chosen threshold, hugely overestimating  
  > "the chosen detection threshold $u$ should have produced $104$ detections in M1 and $294$ in M2." (6 Application to real ALMA maps)

## Claim tuples

- H: PFA alone is insufficient to judge reliability of individual detections; the SPFA does better | E: Simulated map with 30 sub-noise sources; compare SPFA, least-squares fit and FDR | R: SPFA predicted N_FD≈7 vs true 6; least squares gave six false detections; FDR gave a false fraction of 0.44 and 0.58 | F: Only the SPFA quantifies per-detection reliability | **supported**
- H: Faint point sources exist in the PKS0745-19 ALMA maps | E: Apply the method to Band 3, Band 7 and combined maps | R: 2 candidates in M1, 3 in M2, 2 in M3 | F: 7 potential new point sources, with differing reliability | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Least-squares fit of template plus polynomial and FDR compared against SPFA  
  > "Another useful comparison is with the FDR technique mentioned in Sect. [3](#sec:spfa)." (5 A numerical experiment)
- How they decided it was enough: _not stated_
- Limitation (authors): Flux measurements of 1b+3b are highly uncertain because of source shape  
  > "The fluxes measurement are therefore subject to a large uncertainty that depends on the chosen source shape." (6 Application to real ALMA maps)
- Caveat (inferred, ours): Candidate sources have no independent confirmation; SPFA of 0.5 means many are likely false
- Caveat (inferred, ours): Method assumes iid peaks and Gaussian stationary noise, which is only approximately true for interferometric maps
- Caveat (inferred, ours): Feathering independent-band maps to combine them is physically questionable given different frequencies and spectral indices

## Reproducibility

- Data public (paper): Data from ALMA project 2012.1.00837.S, acknowledged as used  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00837.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Clean parameters (cell, threshold, niter, masks)
- Missing: Calibration and line-free channels
- Missing: SPFA code
- Missing: Source masks
- Data volume (inferred): Tens of GB raw for two bands; small after imaging
- Score (inferred): 3/5, Public data and a clear statistical recipe, but imaging parameters are incomplete and no code is released.
- Rediscovery candidate: no, Imaging recipe is incomplete and the main results depend on unreleased custom code.

## Links

- Method: Vio & Andreani 2016 (cite: vio16) (Correct PFA of matched filter)
- Method: Cheng & Schwartzman 2015 (cite: che15a) (Peak PDF of Gaussian random fields)
- Companion: Vio & Andreani 2016 (cite: vio16) (Paper I)

## Checks

```json
{
 "quotes": 45,
 "quotes_ok": 45,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 33,
  "rate": 0.478
 },
 "evidence_ok": true
}
```

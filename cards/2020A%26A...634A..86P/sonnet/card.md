# Observations of solar chromospheric oscillations at 3 mm with ALMA

`2020A&A...634A..86P` | Astronomy and Astrophysics 2020 | first author: Patsourakos, S. | arXiv: 1912.03480 | DOI: 10.1051/0004-6361/201936618

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: sun
- Question: Characterize spatially-resolved chromospheric oscillations of the quiet Sun at 3 mm, their center-to-limb variation, and their lag relative to AIA 1600 Å  
  > "To study spatially-resolved chromospheric oscillations of the quiet Sun in the mm-domain at a resolution of a few arcsec, typically 2.4$''$$\times$4.5$''$." (abstract)
- Target **Quiet Sun, targets 2-7 (mu = 0.34-1) along position angle 135 deg**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: 3 mm (100 GHz)  
  > "seven 120$^{"}$ circular fields of view (targets) were observed at 3 mm (100 GHz) on March 16, 2017." (2 Observations and data analysis)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 2.4"x4.5" (target 7: 2.3"x8.1")  
  > "for all targets was 2.4$''$$\times$4.5$''$, with the exception of target 7 where the resolution was 2.3$''$$\times$8.1$''$." (2 Observations and data analysis)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 10 min per target, 2-s cadence  
  > "Each target was observed for 10 minutes with a 2-s cadence." (2 Observations and data analysis)
- observing dates: March 16, 2017  
  > "The observations were performed on March 16, 2017" (abstract)
- pi or archival as stated: _not stated_
- Other facility **SDO/AIA**: 1600 Å and 304 Å image sequences for comparison and time-lag analysis  
  > "We also analyzed AIA images at 1600 and 304 Å, convolved with the ALMA resolution" (2 Observations and data analysis)
- External data: Reduced ALMA 3 mm quiet-Sun image sequences (targets, solar rotation correction, reduction)  
  > "More details regarding the reduction of the ALMA data can be found in Nindos et al. (2018)." (2 Observations and data analysis) [from Nindos et al. (2018)]

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
- cell size: 1" pixels  
  > "The resulting ALMA images have 1$''$ pixels" (2 Observations and data analysis)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 2.4"x4.5"  
  > "for all targets was 2.4$''$$\times$4.5$''$" (2 Observations and data analysis)
- final rms: _not stated_

### Inherited from earlier work

- Data reduction and imaging of the ALMA data  
  > "More details regarding the reduction of the ALMA data can be found in Nindos et al. (2018)." (2 Observations and data analysis) [from Nindos et al. (2018)]
- Cell-network masking procedure (second-degree 2D polynomial fit of average image)  
  > "we submitted the resulting average images to the masking procedure described in Nindos et al. (2018)." (2.1 Cell-Network Segregation) [from Nindos et al. (2018)]
- 3rd-degree polynomial detrending of light curves  
  > "to remove long-term trends from the data (see also White et al. 2006)." (2.2 Calculation of Power Spectral Density) [from White et al. 2006]

### Not stated but needed to reproduce (our reading)

- Calibration and imaging details (CASA version, self-calibration, weighting) only in Nindos et al. 2018
- Exact AIA data series/level and download specification
- Exact parameters of the AIA-ALMA cross-correlation co-alignment
- Fit initial guesses and fitting method for the PSD function
- How uncertainties of the lag and error bars are computed

## Analysis recipe

1. **Prepare ALMA and AIA data**: Extract central 80"x80" region of each target; degrade AIA to ALMA resolution; correct differential rotation; co-align by cross-correlating time-averaged images  
  > "We extracted a 80$''$$\times$80$''$ region from the original 120$''$ diameter FoV at the center of each target" (2 Observations and data analysis)
   - fitting: _not stated_
   - validation: _not stated_
2. **Cell/network segregation**: Pixels below (above) a second-degree 2D polynomial fit of the average image are cell (network)  
  > "Pixels with values smaller (larger) than these of the mask are tagged as cell (network) pixels." (2.1 Cell-Network Segregation)
   - fitting: _not stated_
   - validation: visual inspection of masks  
  > "it though leads to satisfactory results as judged by visual inspection of the resulting masks and the actual average images." (2.1 Cell-Network Segregation)
3. **Compute PSDs**: Subtract 3rd-degree polynomial from each pixel light curve, Fourier transform, average PSDs over FoV, cell and network  
  > "We then calculated the PSDs for every pixel in the FoV and averaged over the entire FoV, as well as the cell and network using the masks described above." (2.2 Calculation of Power Spectral Density)
   - parameter: frequency resolution 1.7 mHz  
  > "The frequency resolution of all three data sets, determined by the duration of the time series, is 1.7 mHz." (2 Observations and data analysis)
   - fitting: _not stated_
   - validation: Compared with subtraction of mean only; polynomial degrees 1-4 tested  
  > "experimentation with different degree polynomials (i.e., 1-4) showed that the higher the degree of the polynomial, the smaller the amplitude of the peak around the p-mode domain." (3.1 ALMA 3 mm)
4. **Fit PSD peaks**: Fit linear background plus log-normal peak; derive peak frequency a3 and rms from integral  
  > "The fittings were performed in the frequency range of $\approx$ \[0.008, 13.3\] mHz" (2.3 Fitting of spatially averaged power spectra)
   - assumption: linear (white-noise) background  
  > "a linear background is deemed as a reasonable choice." (2.3 Fitting of spatially averaged power spectra)
   - fitting: _not stated_
   - validation: Residuals not exceeding about 15% (ALMA) and 10% (AIA)  
  > "with residuals (blue lines) not exceeding $\approx 15 \%$." (3.1 ALMA 3 mm)
5. **Spatial coherence**: Pixel-to-pixel cross-correlation with region growing, clusters with coefficient above 0.7  
  > "we determined clusters of pixels with cross-correlation coefficient above 0.7 and counted the number of pixels per cluster." (2 Observations and data analysis)
   - fitting: _not stated_
   - validation: _not stated_
6. **ALMA-AIA time lag and formation height difference**: Cross-correlate light curves averaged over 3"x3" macropixels, keep max coefficient >= 0.7, parabolic fit of peak for lag; height from lag times sound speed  
  > "The optimal temporal lag was calculated from a parabolic fitting of the cross-correlation function around its peak." (3.3 Time-lag analysis)
   - assumption: Upward sound waves at about 12 km/s (7000 K)  
  > "traveling at a speed of $\approx$ 12 $\mathrm{km{s}^{-1}}$ (i.e., corresponding to a temperature of 7000 K)" (3.3 Time-lag analysis)
   - fitting: _not stated_
   - validation: Argued lag is real despite differing peak frequencies  
  > "We may thus safely conclude that the time lag is real." (3.3 Time-lag analysis)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA 3 mm oscillation frequency | 4.2 | 1.7 | mHz | 4 | with frequencies of $4.2 \pm 1.7$ mHz are observed in the quiet Sun |
| ALMA spatially averaged rms | 55-75 | not stated | K | 4 | yield rms in the range $\approx$ 55-75 K |
| AIA 1600 Å oscillation frequency | 3.7 | 1.7 | mHz | 4 | For AIA 1600 Å  the oscillation frequency is $3.7\pm1.7$ mHz. |
| ALMA lag behind AIA 1600 Å | about 100 | not stated | s | 6 | ALMA 3 mm time-series lag AIA 1600 Å  by $\approx$ 100 s |
| Formation height difference | about 1200 | not stated | km | 6 | a formation-height difference of $\approx$ 1200 km |

## Qualitative findings

- Oscillation coherence length is comparable to the ALMA resolution (about 4")  
  > "The coherence length-scale of the oscillations is commensurate with the spatial resolution of our ALMA observations." (abstract)

## Claim tuples

- H: Are p-mode oscillations present at 3 mm in cell and network? | E: PSD analysis of ALMA light curves with log-normal peak fits | R: Peak at 4.2 mHz, rms about 55-75 K (about 1% of Tb) | F: Omnipresent p-mode oscillations in cell and network, with a moderate center-to-limb increase | **supported**
- H: What is the formation-height difference between ALMA 3 mm and AIA 1600 Å? | E: Cross-correlation of co-spatial light curves | R: Lag of about 100 s | F: About 1200 km height difference assuming upward sound waves | **supported**
- H: Are oscillations fully resolved by lower-resolution BIMA data? | E: Compare with White et al. 2006 | R: Larger amplitudes in ALMA | F: Oscillations are not fully resolved | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Power-law background not used because the 10-min series are too short  
  > "the short duration of the analyzed sequences per target (i.e., $\sim$ 10 min), does not allow to extend the PSDs to significantly lower frequencies" (2.3 Fitting of spatially averaged power spectra)
- How they decided it was enough: _not stated_
- Limitation (authors): 10-min series limit frequency resolution to 1.7 mHz and prevent detecting longer-period oscillations; rms values are upper limits due to detrending  
  > "the derived p-mode rms amplitudes from the use of a 3rd degree polynomial fitting of the original light-curves could be seen as upper limits." (3.1 ALMA 3 mm)
- Caveat (inferred, ours): Height difference depends on assumed sound speed and on 1600 Å temperature dependence
- Caveat (inferred, ours): Lag assumes similar wave-propagation phase in both channels; a 1.7 mHz frequency resolution is coarse
- Caveat (inferred, ours): Cell/network separation is non-unique

## Reproducibility

- Data public (paper): ALMA project data acknowledged  
  > "This work makes use of the following ALMA data: ADS/JAO.ALMA2016.1.00572.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Reduced ALMA solar images from Nindos et al. 2018 pipeline
- Missing: AIA data selection details
- Data volume (inferred): Tens to hundreds of GB of raw solar ALMA data; the reduced image cubes are small
- Score (inferred): 3/5, Analysis steps are clear, but ALMA reduction is deferred to another paper and no code or software is named.
- Rediscovery candidate: no, Needs the inherited reduction from Nindos et al. 2018, and solar ALMA reduction is nontrivial.

## Links

- Method: Nindos et al. (2018) (ALMA data reduction and cell-network masking)
- Companion: White et al. (2006) (BIMA 3.5 mm oscillation comparison)

## Checks

```json
{
 "quotes": 38,
 "quotes_ok": 38,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2016.1.00572.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 29,
  "rate": 0.403
 },
 "evidence_ok": true
}
```

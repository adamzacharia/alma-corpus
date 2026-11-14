# An independent hybrid imaging of Sgr A* from the data in EHT 2017 observations

`2024MNRAS.534.3237M` | Monthly Notices of the Royal Astronomical Society 2024 | first author: Miyoshi, Makoto | arXiv: 2410.19267 | DOI: 10.1093/mnras/stae1158

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type archival_reuse

## Science

- Fields: agn_and_quasars, milky_way_ism, instrumentation
- Question: Is the ring structure reported by the EHTC for Sgr A* real, or an artifact of the bumpy EHT 2017 PSF? Independent hybrid-mapping reimaging of the public EHT 2017 data.  
  > "We propose that the ring structure found by the Event Horizon Telescope Collaboration (EHTC) as the black hole shadow of Sgr A$^{*}$ is an artifact by the bumpy PSF (Point Spread Function) of the EHT2017." (abstract)
- Target **Sgr A***: coordinates _not stated_; z/distance about 8 kpc; mass ~4e6 Msun  
  > "The distance from the Earth to the Galactic center is about 8 kpc" (1.2 Prior radio research of Sgr A*); distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: _not stated_
- frequencies and spectral setup: two recording channels at 227.1 and 229.1 GHz  
  > "(227.1 and 229.1 GHz)" (4.2.2 Residuals of closure phase)
- continuum bandwidth: _not stated_
- arrays: EHT 2017, eight stations including ALMA and SPT  
  > "The EHT observed Sgr A$^{*}$ in early April 2017 with a total of eight stations, including the Antarctic station" (2 Observational data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: default restoring beam 23.0x15.3 uas, PA 66.6 deg; ~20 uas  
  > "yields a default restoring beam of $\mathrm{(FWHM) =23.0\times15.3~\mu \rm as}$ and $\mathrm{PA= 66.6^{\circ}}$" (5.1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: EHT 2017; analysis of April 7 data (April 6 in appendix)  
  > "Our data analysis focused on the April 7 data, which the EHTC analyzed in detail" (2 Observational data)
- pi or archival as stated: _not stated_
- Other facility **EHT network (public EHTC data)**: Network-calibrated, HOPS-calibrated, LMT-corrected, normalized April 7 visibilities  
  > "Namely we analyzed data from April 7, i.e., calibrated by HOP, corrected for amplitude with respect to LMT, and normalized for time variability using measured intensities." (2 Observational data)
- External data: EHTC ring image digitized from Figure 3 for residual comparison; ring diameter 51.8±2.3 uas, shadow 48.7±7.0 uas  
  > "we digitized Figure 3 in (cite: EHTC2022a) to obtain each coordinate value and the intensity at that coordinate." (4.2 Reliability of our final image) [from (cite: EHTC2022a)]
- External data: Intrinsic size and scattering scaling used for expected shape  
  > "Assuming that the intrinsic angular size of Sgr A$^{*}$ is proportional to the observed wavelength (cite: Johnson:2018)" (4.1) [from (cite: Johnson:2018)]
- Simulation/model as data: Simulated UVMOD datasets (noise only; 1 Jy point source) with EHT 2017 uv coverage, self-calibrated on ring models  
  > "We created two simulated data sets by using a AIPS task, UVMOD." (5.2)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Public EHTC HOPS-calibrated data used as released  
  > "We selected the HOP-calibrated datasets because the CASA calibration data show a large difference in closure amplitude between channels of the raw data" (2 Observational data)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: phase-only self-cal, six steps, SOLINT=0.15 min, point-source initial model; no amplitude self-cal  
  > "The six steps of self-calibration were performed in phase-only mode." (3.2); "Data calibration using self-calibration solutions for amplitude was omitted due to the significant intensity variations in Sgr A$^{*}$" (3.2)

### Imaging

- task: AIPS IMAGR CLEAN with hybrid mapping  
  > "hybrid mapping technique, which is commonly used in VLBI imaging and implemented in AIPS" (3.2)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: FOV 1 mas square; CLEAN BOX 256 uas diameter  
  > "the CLEAN subtraction area is restricted by the BOX setting ($\mathrm{256~\mu \rm as}$ in diameter)" (3.2)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: Gaussian beam 25 uas used for alternate image convolution  
  > "a $\mathrm{25~\mu \rm as}$ Gaussian beam is used to convolve the CLEAN components" (4.1)
- final rms: _not stated_

### Inherited from earlier work

- SOLINT in CALIB set shorter than coherence time following earlier approach  
  > "following the same approach as in CALIB in (cite: Miyoshi2022a)" (3.2) [from (cite: Miyoshi2022a)]
- LMT amplitude gains pre-corrected assuming 60 uas source size  
  > "According to Section 2-2 of (cite: EHTC2022c), the LMT amplitude gains were pre-corrected assuming a $\mathrm{60~\mu \rm as}$ source size" (2 Observational data) [from (cite: EHTC2022c)]

### Not stated but needed to reproduce (our reading)

- IMAGR ROBUSTNESS, GAIN and NITER values for the final image
- Which candidate maps were averaged and how the final image was chosen
- BOX positions for simulations
- Weighting scheme and cell size
- Software versions

## Analysis recipe

1. **Hybrid mapping of April 7 data**: Iterate CLEAN imaging and phase-only self-calibration from a point-source start; choose among candidate images by residuals  
  > "We started the hybrid mapping with a point source as the initial image model" (3.2)
   - software: AIPS
   - parameter: SOLINT = 0.15 min, SNR cutoff 3, REFANT ALMA  
  > "APARM(7) (SNR cut off)" (Appendix self-calibration table)
   - fitting: _not stated_
   - validation: Compared residuals of normalized amplitude, closure phase and closure amplitude, and PSF features  
  > "compared the residuals of closure phases, closure amplitudes, and normalized amplitudes" (3.2)
2. **Compare with EHTC ring via visibility residuals**: Digitized EHTC image converted to visibilities with UVMOD at 1 Jy and residuals computed vs data  
  > "this numerical image data was input into the AIPS task, UVMOD, to create a visibility set" (4.2)
   - software: AIPS UVMOD
   - fitting: _not stated_
   - validation: Compared across integration times 10-900 s  
  > "Our final image consistently exhibits smaller means and standard deviations in the residuals than the case of the EHTC ring image, regardless of the integration time between $\mathrm{T_{\text{int}} = 10~sec}$ and $\mathrm{T_{\text{int}} = 900~sec}$." (4.2.1 Residuals of normalized amplitude of our final image compared to those of the EHTC ring)
3. **Simulate ring artifacts**: Self-calibrate noise-only and point-source data with ring models then CLEAN with narrow BOX; rings 30-70 uas  
  > "We made rings with diameters ranging from $\mathrm{30}$ to $\mathrm{70~\mu \rm as}$" (5.2)
   - software: AIPS
   - fitting: _not stated_
   - validation: flux/rms ratio peaks at 50 uas  
  > "It can be seen that the ring image with a diameter of $\mathrm{50~\mu \rm as}$ shows the largest value and is the most plausible image among them." (5.2 Rings from the simulated data of other structures)
4. **Doppler boost interpretation**: Brightness ratio of east peak to west dark spot gives v/c cosθ; radius and inclination derived  
  > "$\frac{v}{c}\cos\theta =  0.438.$" (4.1)
   - assumption: D=8 kpc, M=4e6 Msun, optically thin edge-on disk  
  > "Assuming a distance to the Galactic Center of $\mathrm{D_{GC} = 8 kpc}$ and a black hole mass of $\mathrm{4\times10^6M_{\odot}}$" (4.1)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **AIPS** : Hybrid mapping, CALIB, IMAGR, UVMOD, DBCON  
  > "implemented in AIPS (the NRAO Astronomical Image Processing System" (3.2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Normalized amplitude residual, our image (Tint=180 s) | 0.080 ± 0.397 | not stated | dimensionless | 2 | $\mathrm{NR_{ours} = 0.080 \pm 0.397}$ |
| Normalized amplitude residual, EHTC ring (Tint=180 s) | 0.862 ± 1.552 | not stated | dimensionless | 2 | $\mathrm{NR_{EHTC} = 0.862 \pm 1.552}$ |
| Closure phase residual, our image | 0.2 ± 58.1 | not stated | deg | 2 | $\mathrm{Res_{cp} = 0.2 \pm 58.1^\circ}$ |
| PSF first sidelobe spacing | 49.09 | not stated | uas | 0 | which is $\mathrm{49.09~\mu \rm as}$ |
| Brightness ratio Delta | 5.617 | not stated | dimensionless | 4 | $\mathrm{\Delta=\frac{2.1701\times 10^{-4}}{3.8635\times 10^{-5}}=5.617}$ |
| Inferred viewing angle | ~43.8 | not stated | deg | 4 | the viewing angle is estimated to be $\mathrm{\theta \sim 43.8 ^{\circ}}$ |

## Qualitative findings

- Final image is east-west elongated with brighter east side, not a ring  
  > "our final image of Sgr A$^{*}$shows an east-west elongation with an asymmetry, the east side appearing brighter than the west side." (4.1)
- Closure quantities differ between the two recording channels in all public data, suggesting internal inconsistency  
  > "an unexplained closure discrepancy between recording channels is present in all EHTC data" (4.2.4)

## Claim tuples

- H: EHTC ring is a PSF artifact | E: Rings reproduced from noise-only and point-source simulated data with ring-model self-cal and narrow BOX | R: Ring images produced, best at 50 uas | F: Ring can arise from the PSF and self-cal | **supported**
- H: Hybrid mapping gives a more consistent image than the EHTC ring | E: Residual comparison of normalized amplitudes and closures | R: Half the amplitude residuals, comparable closure residuals | F: Elongated image more reliable | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Fine structure not very reliable; the west dark spot disappears with 25 uas beam  
  > "the reliability of the fine structure seen in Figure 2 (a) is not very high." (4.1)
- Caveat (inferred, ours): Image selected by authors' own residual metric; both images have large residuals
- Caveat (inferred, ours): Variability of Sgr A* unmodelled
- Caveat (inferred, ours): Simulations use deliberately extreme self-cal and BOX
- Caveat (inferred, ours): Doppler interpretation rests on single pixels

## Reproducibility

- Data public (paper): EHTC public data; derived products on request  
  > "The original observational data are available on the EHTC website." (Data availability)
- Products in archive: _not stated_
- Missing: Final IMAGR parameters
- Missing: Digitization details of EHTC image
- Data volume (inferred): <1 GB
- Score (inferred): 3/5, Public data and AIPS but key imaging parameters are missing.
- Rediscovery candidate: no, Recipe incomplete and the result depends on subjective image selection.

## Links

- Companion: (cite: Miyoshi2022a) (Same method applied to M87)
- Related: Event Horizon Telescope 2017

## Checks

```json
{
 "quotes": 41,
 "quotes_ok": 41,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2016.1.01154.V"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 31,
  "rate": 0.463
 },
 "evidence_ok": true
}
```

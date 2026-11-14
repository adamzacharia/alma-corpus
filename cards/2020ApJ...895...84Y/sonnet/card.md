# Super-resolution Imaging of the Protoplanetary Disk HD 142527 Using Sparse Modeling

`2020ApJ...895...84Y` | The Astrophysical Journal 2020 | first author: Yamaguchi, Masayuki | arXiv: 2004.10989 | DOI: 10.3847/1538-4357/ab899f

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks, instrumentation
- Question: Can sparse modeling (l1+TSV) imaging applied to ALMA data reproduce super-resolution structure (finer than the beam) of the HD 142527 disk with higher fidelity than MS-CLEAN?  
  > "it has not yet been applied to ALMA observational data, and it is therefore unknown whether SpM imaging is useful for the reconstruction of super-resolution images based on actual observational data." (Introduction)
- Target **HD 142527**: coordinates _not stated_; z/distance 156 ± 7.5 pc  
  > "It is a binary system at a distance of 156 $\pm$ 7.5 pc (cite: gaia2016b; gaia2016a)." (Introduction); distance from Gaia (cite: gaia2016b; gaia2016a)  
  > "It is a binary system at a distance of 156 $\pm$ 7.5 pc (cite: gaia2016b; gaia2016a)." (Introduction)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 7 (~330 GHz); Data 1 at 343 GHz, Data 2 at 322 GHz  
  > "Two data sets of ALMA observations of the protoplanetary disk around HD 142527 at a frequency of $\sim$ 330 GHz (ALMA Band 7) are used in our investigation." (2.1 ALMA Data Set used for Imaging)
- frequencies and spectral setup: Data 1: four 2 GHz SPWs at 336, 338, 348, 350 GHz; Data 2: two 0.5 GHz SPWs (314, 329 GHz) and two 1.9 GHz SPWs (315, 328 GHz)  
  > "consisting of four 2 GHz spectral windows centered at 336, 338, 348, and 350 GHz." (2.1 ALMA Data Set used for Imaging); "two 0.5 GHz spectral windows centered at 314 and 329 GHz and two 1.9 GHz spectral windows centered at 315 and 328 GHz." (2.1 ALMA Data Set used for Imaging)
- continuum bandwidth: _not stated_
- arrays: Data 1: thirty-eight 12 m antennas; Data 2: forty 12 m antennas  
  > "The observing array consisted of thirty-eight 12 m antennas." (2.1 ALMA Data Set used for Imaging)
- configurations: _not stated_
- baselines: Data 1 max 430 m; Data 2 max 1570 m  
  > "The data set obtained with the extended array with a maximum baseline length of 1570 m was labeled as *Data 2*." (2.1 ALMA Data Set used for Imaging)
- angular resolution: MS-CLEAN beams 0.51x0.44 asec (Data 1), 0.20x0.14 asec (Data 2)  
  > "provided the beam size of $0.20 \times 0.14$ asec at P.A. of $78.1$$^\circ$." (2.2 Data Reduction and Imaging with MS-CLEAN)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: Data 1: 1.2 h; Data 2: 1.9 h  
  > "The on-source time of HD 142527 was 1.2 h, and observations were carried out for 3.4 h in total." (2.1 ALMA Data Set used for Imaging); "The total observing time was 22.5 h with an on-source time of 1.9 h." (2.1 ALMA Data Set used for Imaging)
- observing dates: Data 1: March 11, 2015; Data 2: July 17, 2015  
  > "The corresponding observations were carried out on March 11, 2015, at 343 GHz (0.87 mm)" (2.1 ALMA Data Set used for Imaging)
- pi or archival as stated: _not stated_

## Processing

### Calibration

- pipeline or manual: ALMA pipeline initial calibration, then phase-only self-calibration with MS-CLEAN models  
  > "The initial calibration was performed using the ALMA pipeline." (2.2 Data Reduction and Imaging with MS-CLEAN)
- casa version: CASA 4.7.2  
  > "Data 1 were calibrated using version 4.7.2 of the Common Astronomy Software Applications package" (2.2 Data Reduction and Imaging with MS-CLEAN)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Data 2: Pallas, Ceres, J1427-4206  
  > "Pallas, Ceres, and J1427-4206 were used for the flux calibration" (2.2 Data Reduction and Imaging with MS-CLEAN)
- flux scale uncertainty: _not stated_
- self calibration: Phase-only (calmode=p); solint 420 to 30 s (Data 1), 360 to 50 s (Data 2)  
  > "The interval time used to solve the complex gain varied from 420 to 30 s." (2.2 Data Reduction and Imaging with MS-CLEAN); "The interval of time used to solve the complex gain varied from 360 to 50 s." (2.2 Data Reduction and Imaging with MS-CLEAN)

### Imaging

- task: MS-CLEAN (multi-scale Cotton-Schwab CLEAN) for reference images; SpM l1+TSV with MFISTA for SpM images  
  > "Images were constructed from the data sets using the SpM and the popular multi-scale Cotton-Schwab CLEAN algorithm" (Introduction)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5  
  > "by adopting Briggs weighting of robust parameter 0.5" (2.2 Data Reduction and Imaging with MS-CLEAN)
- uv taper: _not stated_
- cell size: SpM pixel 0.05 asec (Data 1), 0.025 asec (Data 2)  
  > "A pixel size of $0.05\: \times\: 0.05$ asec was used for Data 1 and $0.025\: \times\: 0.025$ asec for Data 2" (2.3 Imaging with Sparse Modeling)
- image size: SpM field of view 5.0 x 5.0 asec  
  > "$5.0 \times 5.0$ asec for the field of view" (2.3 Imaging with Sparse Modeling)
- masking: _not stated_
- multiscale scales: [0, 0.3, 0.9] asec  
  > "MS-CLEAN performed with scale parameters of \[0, 0.3, 0.9\] asec" (2.2 Data Reduction and Imaging with MS-CLEAN)
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.51x0.44 asec PA 58.7 deg (Data 1); 0.20x0.14 asec PA 78.1 deg (Data 2)  
  > "provided the beam size of $0.51 \times 0.44$ asec with position angle (P.A.) of 58.7$^\circ$." (2.2 Data Reduction and Imaging with MS-CLEAN)
- final rms: MS-CLEAN 0.32 mJy/beam (Data 1), 0.07 mJy/beam (Data 2)  
  > "The RMS noise level of the resultant image was $0.07~ \rm mJy~beam^{-1}$." (2.2 Data Reduction and Imaging with MS-CLEAN)

### Inherited from earlier work

- Data 1 calibration performed in the same manner as the earlier published analysis  
  > "in the same manner as (cite: kataoka2016)." (2.2 Data Reduction and Imaging with MS-CLEAN) [from (cite: kataoka2016)]
- l1+TSV SpM imaging formulation  
  > "SpM utilizing $\ell _1$+TSV regularization (cite: Kuramochi2018)." (2.3 Imaging with Sparse Modeling) [from (cite: Kuramochi2018)]
- NRMSE fidelity metric and gradient-domain Prewitt filter  
  > "the NRMSE of the gradient-domain brightness distribution was also evaluated using the Prewitt filter (cite: Kuramochi2018)." (3.2 Fidelity at Multi-resolution) [from (cite: Kuramochi2018)]

### Not stated but needed to reproduce (our reading)

- SpM code/implementation used (not named or released)
- Selected optimal (Lambda_l, Lambda_t) per spectral window
- Clean masks, thresholds, iteration counts, cell/image size for MS-CLEAN
- Number of self-cal iterations and exact steps
- Calibrator for Data 1 flux scale
- Frequency ordering/weighting when averaging four SPW images
- Reference position of the star for radial profiles

## Analysis recipe

1. **Calibrate and self-calibrate visibilities**: ALMA pipeline then iterative phase-only self-calibration using MS-CLEAN models  
  > "we performed iterative self-calibration of the visibility phase (calmode = p)." (2.2 Data Reduction and Imaging with MS-CLEAN)
   - software: CASA
   - fitting: _not stated_
   - validation: Total fluxes from visibility amplitude 3.3 Jy vs 3.2 Jy  
  > "The resultant total fluxes of Data 1 and 2 are derived to be 3.3 Jy and 3.2 Jy, respectively" (2.2 Data Reduction and Imaging with MS-CLEAN)
2. **MS-CLEAN imaging**: MS-CLEAN with Briggs robust 0.5 and scales [0,0.3,0.9] asec  
  > "The corrected data were imaged using MS-CLEAN performed with scale parameters of \[0, 0.3, 0.9\] asec" (2.2 Data Reduction and Imaging with MS-CLEAN)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **SpM imaging with cross-validation**: l1+TSV regularized least squares solved with MFISTA on cell-averaged gridded visibilities; one image per spectral window, four averaged  
  > "a monotonic variant of FISTA (MFISTA) was used" (2.3 Imaging with Sparse Modeling)
   - parameter: Grid Lambda_l 1e2-9e2, Lambda_t 3e4-9e5 (16x9) for Data 1; 1e2-1e7 and 1e-3-1e2 (6x6) for Data 2  
  > "consisting of $(10^{2}, 10^{3}, ..., 10^{7})$ for $\Lambda_{l}$ and $(10^{-3}, 10^{-2}, ..., 10^{2})$ for $\Lambda_{t}$." (2.3 Imaging with Sparse Modeling)
   - fitting: Convex optimization; parameters chosen by minimum 10-fold CV error per spectral window  
  > "the parameter set and corresponding image were selected, minimizing the CVE for each spectral window of each set of data." (2.3 Imaging with Sparse Modeling)
   - validation: 10-fold cross validation  
  > "The optimal parameter set of ($\Lambda_{l}$, $\Lambda_{t}$) was determined by 10-fold cross validation (CV)" (2.3 Imaging with Sparse Modeling)
4. **Fidelity versus resolution (NRMSE)**: Convolve images with beams of fraction R of Data 1 nominal beam; compute NRMSE in image and gradient (Prewitt) domains against Data 2 MS-CLEAN reference; optimal resolution is minimum, worse of two domains  
  > "The beam size providing the minimum NRMSE may be considered as an optimal resolution" (3.2 Fidelity at Multi-resolution)
   - assumption: Data 2 MS-CLEAN at nominal resolution is trusted reference  
  > "The Data 2 MS-CLEAN at its nominal resolution is therefore the best choice as the reference image." (3.2 Fidelity at Multi-resolution)
   - fitting: _not stated_
   - validation: Ideal NRMSE curve from convolved reference image  
  > "The solid green line shows the ideal NRMSE curves between the non-convolved and the convolved reference images" (3.2 Fidelity at Multi-resolution)
5. **Radial/azimuthal profile comparison and noise/detection threshold**: Peak and FWHM of radial profiles per PA (10 deg bins); residual maps via DIFMAP; I100 = max intensity in off-source area  
  > "A maximum intensity ($\rm I_{100}$) of $81.6$ and $54.5$ mJy asec$^ {- 2}$ is apparent for Data 1 and 2, respectively." (4.1.1 Noise Terms in Reconstructed Images)
   - software: DIFMAP
   - assumption: Radial structure approximated as Gaussian  
  > "Considering that each radial structure would form a Gaussian distribution" (3.3 Evaluation of Radial and Azimuthal Structure of the Outer Disk)
   - fitting: _not stated_
   - validation: Residual statistics compared with noise  
  > "The peak and integrated intensity are also consistent; the mean and standard deviation are comparable to the noise levels on the residual maps" (3.3 Evaluation of Radial and Azimuthal Structure of the Outer Disk)

## Software

- **CASA** 4.7.2: Calibration, MS-CLEAN imaging, self-calibration  
  > "Data 1 were calibrated using version 4.7.2 of the Common Astronomy Software Applications package" (2.2 Data Reduction and Imaging with MS-CLEAN)
- **DIFMAP** : Residual maps from SpM residual visibilities  
  > "The residual maps of SpM were reconstructed from the residual visibilities using the DIFMAP software" (4.1.1 Noise Terms in Reconstructed Images)
- **Astropy** : Listed in software section  
  > "Astropy (cite: astropy2013; astropy2018), CASA (cite: mcmullin2007), DIFMAP (cite: Shepherd1994), matplotlib (cite: Hunter2007)" (Software)
- **matplotlib** : Plotting  
  > "matplotlib (cite: Hunter2007)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Optimal resolution Data 1 SpM, image domain | 23 x 16 (41%) | not stated | mas | 4 | 23 $\times$ 16  (41 $\%$) |
| Optimal resolution Data 1 MS-CLEAN, gradient domain | 34 x 24 (60%) | not stated | mas | 4 | 34 $\times$ 24 (60 $\%$) |
| Total flux Data 1 / Data 2 | 3.3 / 3.2 | not stated | Jy | 1 | The resultant total fluxes of Data 1 and 2 are derived to be 3.3 Jy and 3.2 Jy, respectively |
| Detection threshold I100 Data 1 / Data 2 | 81.6 / 54.5 | not stated | mJy asec^-2 | 5 | A maximum intensity ($\rm I_{100}$) of $81.6$ and $54.5$ mJy asec$^ {- 2}$ is apparent for Data 1 and 2, respectively. |
| SpM residual RMS Data 1 / Data 2 | 0.44 / 0.14 | not stated | mJy/beam | 5 | the SpM residual images have RMS noise of $0.44$ and $0.14$ mJy beam$^{-1}$ for Data 1 and 2, respectively |
| Data 1 SpM NRMSE plateau at R<=41% | 5-10% image domain, 10-15% gradient domain | not stated | percent | 4 | with typical ranges of $5-10~\%$ in the image domain and $10-15~\%$ in the gradient domain |

## Qualitative findings

- Raw SpM images are smooth in the outer disk, while raw MS-CLEAN component maps show compact point-like artifacts  
  > "consists of more compact point-like features, which are not consistent with each other or with any of the other images" (3.1 Images at Different Angular Resolutions)
- Tentative double-ridge structure at PA 265-270 deg seen only in Data 2 SpM image  
  > "The radial profile of the raw Data 2 SpM image only shows a double ridge-like structure at P.A.= $265^{\circ} - 270^{\circ}$" (4.1.2 Double Ridge-line shown in the Outer Disk)

## Claim tuples

- H: SpM gives higher fidelity than MS-CLEAN in the super-resolution regime | E: NRMSE of Data 1 SpM and MS-CLEAN images vs Data 2 MS-CLEAN reference at varying beam sizes | R: SpM optimal resolution 41% of nominal vs 55-60% for MS-CLEAN | F: SpM achieves ~3x finer resolution than nominal Data 1 | **supported**
- H: Known disk structures appear in both SpM and CLEAN images | E: Compare PA profiles of Data 1 SpM and Data 2 MS-CLEAN | R: Residuals consistent within ~10% of nominal resolution | F: Radial and azimuthal structure agree well | **supported**
- H: Raw SpM image reveals new substructure | E: Contours at I100 and radial profiles of raw Data 2 SpM | R: Break at PA ~230 deg and double ridge at PA 265-270 deg | F: Possible substructure in horseshoe, needs confirmation | **partially**

## Reasoning

- Why this data: Same band, different resolutions allow testing SpM against CLEAN  
  > "An observational data set covering several different angular resolutions therefore exists in the same frequency band." (Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): SpM images have larger asymmetric residuals due to self-calibration with MS-CLEAN; degree of super-resolution for Data 2 not established  
  > "SpM images have more asymmetric and larger residuals, while MS-CLEAN images have nearly symmetric residuals distributions." (5 Conclusion)
- Caveat (inferred, ours): Reference image is itself a CLEAN image from different data/frequency
- Caveat (inferred, ours): Self-calibration with CLEAN models biases SpM comparison
- Caveat (inferred, ours): Single target; resolution gain may not generalize
- Caveat (inferred, ours): Metrics from one regularization grid, no uncertainties

## Reproducibility

- Data public (paper): Archival ALMA data from projects 2015.1.00425.S and 2012.1.00631.S  
  > "two sets of ALMA archive data at Band 7" (Introduction)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: SpM code not released
- Missing: Chosen regularization parameters
- Missing: CLEAN masks and self-cal details
- Data volume (inferred): ~50-100 GB raw for two Band 7 datasets
- Score (inferred): 3/5, Public data and clear algorithm, but SpM code, selected parameters and CLEAN details missing.
- Rediscovery candidate: no, Requires the authors' unreleased SpM code and unspecified selected parameters.

## Links

- Method: (cite: Kuramochi2018) (l1+TSV SpM imaging method and NRMSE metrics)
- Method: (cite: akiyama2017b) (MFISTA and cross validation)
- Companion: (cite: kataoka2016) (Published Data 1 and its calibration)
- Related: DSHARP

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2012.1.00631.S",
  "2015.1.00425.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 46,
  "rate": 0.639
 },
 "evidence_ok": true
}
```

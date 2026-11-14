# The ALMA Spectroscopic Survey in the HUDF: Constraining Cumulative CO Emission at 1 ≲ z ≲ 4 with Power Spectrum Analysis of ASPECS LP Data from 84 to 115 GHz

`2019ApJ...887...37U` | The Astrophysical Journal 2019 | first author: Uzgil, Bade D. | arXiv: 1911.00028 | DOI: 10.3847/1538-4357/ab517f

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies, cosmology
- Question: What constraints does a power spectrum analysis of ASPECS LP Band 3 data place on the cumulative CO emission (shot noise power, mean intensity) of galaxies at 1<z<4?  
  > "We place an integral constraint on CO luminosity functions (LFs) in this redshift range via a direct measurement of their second moments in the three-dimensional (3D) auto-power spectrum" (abstract)
- Target **Hubble Ultra Deep Field ASPECS LP 3mm mosaic**: coordinates _not stated_; z/distance CO(2-1) at z~1.0-1.7 (z_cen=1.315); CO(3-2), CO(4-3) at higher z  
  > "ASPECS LP targeted a $\sim4.6$ arcmin$^2$ field in a region of HUDF containing the deepest near-infrared (near-IR) photometric data on the sky" (1 Introduction); distance from adopted band-center redshift for CO(2-1)  
  > "ASPECS LP targeted a $\sim4.6$ arcmin$^2$ field in a region of HUDF containing the deepest near-infrared (near-IR) photometric data on the sky" (1 Introduction)

## Data provenance

- ALMA projects: 2016.1.00324.L
- bands: Band 3 (84-115 GHz)  
  > "with 68 hours of total telescope time to scan the full ALMA Band 3 from 84 to 115 GHz" (1 Introduction)
- frequencies and spectral setup: 17-pointing mosaic, five frequency tunings; native 3.91 MHz channels  
  > "a 17-pointing mosaic over $\sim4.7$ arcmin$^2$ at five frequency tunings spanning the full extent of ALMA Band 3" (3 Data and Methods)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.80 x 1.48 arcsec at band center  
  > "$\Delta\theta_{b} = \Delta\theta_{b,maj} \times \Delta\theta_{b,min} = 1.80 \ \mathrm{arcsec} \times 1.48 \ \mathrm{arcsec}$" (2.1.1 Real-space dimensions)
- max recoverable scale: _not stated_
- sensitivity: mean RMS 1.96e-4 Jy/beam per 2-channel; 4.55e-5 Jy/beam per 40-channel  
  > "mean RMS $=\langle\sigma_{N,\mathrm{2chn}} \rangle = 1.96\times10^{-4}$ Jy beam$^{-1}$ per channel" (3 Data and Methods)
- time on source: 68 hours total telescope time  
  > "with 68 hours of total telescope time to scan the full ALMA Band 3 from 84 to 115 GHz" (1 Introduction)
- observing dates: December 2-21, 2016  
  > "time (December 2–December 21, 2016) covered by the observations" (3 Data and Methods)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (not stated)
- Line: CO J=3-2, 4-3, 1-0 (not stated)
- Other facility **MUSE UDF**: Spectroscopic redshift catalog of galaxy positions for cross-power analysis  
  > "The MUSE Ultra Deep Field (UDF) survey (cite: Bacon2017) has yielded $\sim1500$ spectroscopic redshifts within a 3$'$ by 3$'$ field in HUDF" (4.3 CO-galaxy statistics)
- External data: Blind CO line detections and fluxes (16 sources)  
  > "Integrated line flux from Table 6 of GL19." (Table 1) [from González-López et al. 2019 (cite: GL2019_3mm)]
- External data: CO luminosity function Schechter parameters  
  > "CO LF Schechter parameters from D19" (Table 2) [from Decarli et al. 2019 (cite: Decarli2019_3mm)]
- External data: MUSE spec-z catalog positions  
  > "known positions of MUSE galaxies listed in (cite: Inami2017)" (4.3.1 Masked noise-bias free auto-power spectrum) [from (cite: Inami2017)]
- External data: COLDz CO(1-0) LF posteriors and COPSS II shot noise measurement for comparison  
  > "(cite: Keating2016) present a marginal 2-$\sigma$ detection of $P_{\operatorname{CO(1-0)},\operatorname{CO(1-0)}}^{shot}(k_{\operatorname{CO(1-0)}}) = 3000\pm1300$ $\mu$K$^2$ (Mpc h$^{-1}$)$^3$" (4.2.2 Comparison to higher redshift CO(1-0) observations) [from (cite: Riechers2018); (cite: Keating2016)]
- Simulation/model as data: MAGPHYS-based CO model catalog and Popping et al. 2016 semi-analytic model used for shot noise comparison  
  > "The “Popping" model refers to the semi-analytic model described in (cite: Popping2016)." (4.2 Measurement of CO auto-power spectrum)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Used ASPECS team visibility data and imaging from D19  
  > "As described in D19 (see their Section 2.2 for more detail) of this series, the resulting visibility data were imaged using the CASA task tclean" (3 Data and Methods)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean  
  > "the resulting visibility data were imaged using the CASA task tclean" (3 Data and Methods)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "with natural weighting applied in the *uv*-plane" (3 Data and Methods)
- uv taper: _not stated_
- cell size: 0.36 arcsec  
  > "the smallest transverse dimension present in the dataset is actually $\Delta\theta_{cell}=0.36$ arcsec" (2.1.1 Real-space dimensions)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: imcontsub with linear baseline across all channels  
  > "The continuum was approximated using a linear baseline fit across all channels to prevent introducing artificial spectral structure." (3 Data and Methods)
- line free channels: _not stated_
- primary beam correction: applied after imaging  
  > "After imaging and applying a primary beam correction to correct flux densities for the effect of the mosaic sensitivity pattern" (3 Data and Methods)
- array combination: _not stated_
- smoothing: channel rebinning by 40 native channels (0.156 GHz) for power spectrum; 2 channels for line search  
  > "we have imaged the ASPECS data cube while re-binning the native ALMA channel resolution by a factor of 40" (2.1.1 Real-space dimensions)
- final beam: 1.80 x 1.48 arcsec at 99.572 GHz  
  > "$\Delta\theta_{b} = \Delta\theta_{b,maj} \times \Delta\theta_{b,min} = 1.80 \ \mathrm{arcsec} \times 1.48 \ \mathrm{arcsec}$" (2.1.1 Real-space dimensions)
- final rms: 4.55e-5 Jy/beam per 40-channel; 1.96e-4 Jy/beam per 2-channel  
  > "$\langle \sigma_{N,\mathrm{40chn}} \rangle = 4.55\times 10^{-5}$ Jy beam$^{-1}$ channel$^{-1}$" (3 Data and Methods)

### Inherited from earlier work

- Imaging of the visibility data into cube T0 (tclean, natural weighting)  
  > "As described in D19 (see their Section 2.2 for more detail) of this series, the resulting visibility data were imaged using the CASA task tclean" (3 Data and Methods) [from Decarli et al. 2019 (cite: Decarli2019_3mm)]
- Construction of stitched T0 measurement set  
  > "(Please refer to Section 2.4 of (cite: Walter2016_survey) for more details on the construction of $T_0$.)" (3 Data and Methods) [from (cite: Walter2016_survey)]
- Noise-bias-free cross-power method using split data subsets  
  > "(cite: Dillon2014) demonstrate that it is possible—and, indeed, preferable when the expected signal-to-noise is sub-unity" (3 Data and Methods) [from (cite: Dillon2014)]
- Lower limit on mean CO surface brightness procedure  
  > "We repeat the analysis performed for the ASPECS-Pilot program by (cite: Carilli2016) to place a lower limit on $\langle T_{\operatorname{CO}} \rangle$ at $\nu_{obs}=99$ GHz" (4.1.1 Mean surface brightness at 99 GHz) [from (cite: Carilli2016)]
- Cosmic variance prescription  
  > "Following the prescription in (cite: Moster2011), we estimate a 19.5% relative uncertainty" (4.1.1 Mean surface brightness at 99 GHz) [from (cite: Moster2011)]

### Not stated but needed to reproduce (our reading)

- Power spectrum estimator code, FFT/windowing and gridding details
- How scans were allocated among the four subsets (exact split lists)
- Details of simobserve simulation parameters
- Exact k binning/averaging implementation and 6-degree polynomial error fit procedure
- Imaging details (image size, masking/threshold, deconvolver) deferred to D19
- Which visibility weighting/statwt settings were used
- Masking implementation for MUSE positions

## Analysis recipe

1. **Build 40-channel continuum-subtracted cube**: Image visibilities with tclean (40-channel rebin), primary beam correct, imcontsub linear fit, crop to 1.84 arcmin square  
  > "we estimate and subtract any possible continuum emission by running CASA task imcontsub in the full cube" (3 Data and Methods)
   - software: CASA
   - parameter: survey width 1.84 arcmin within 50% primary beam; 196 channels  
  > "we limit our analysis to a square region (shown as the black, dotted square boundary in Figure 1) with area $\Delta\theta_S^2 = \left(1.84~\mathrm{arcmin}\right)^2$" (2.1.1 Real-space dimensions)
   - assumption: Cosmology Omega_M=0.7, Omega_Lambda=0.3, h=0.70; target z_cen=1.315 for CO(2-1)  
  > "we adopt a cosmological model with $\Omega_{\mathrm{M}}=0.7$, $\Omega_{\Lambda}=0.3$, $\Omega_{k}=0$, and $h = H_0/100 = 0.70$" (1 Introduction)
   - fitting: _not stated_
   - validation: Compared RMS and spectra before/after continuum subtraction  
  > "finding negligible (less than 0.1–1%) change in both quantities" (3 Data and Methods)
2. **Split data into four subsets**: Distribute scans evenly into four visibility subsets with split, merge with concat and statwt; image each to tau1-tau4  
  > "Using CASA task split, we select and distribute these scans evenly among four subsets." (3 Data and Methods)
   - software: CASA split, CASA concat, CASA statwt
   - parameter: gamma_N = 0.25  
  > "Therefore, we find $\gamma_N=0.25$." (3 Data and Methods)
   - assumption: noise predominantly thermal, equal visibility weights among subsets  
  > "confirms the assumptions that our noise is predominantly thermal, that the visibility datasets have been divided equally among the subsets" (3 Data and Methods)
   - fitting: _not stated_
   - validation: RMS of tau1-tau4 matches 2*sigma_40chn  
  > "matches well the RMS level representing $2\langle \sigma_{N,\mathrm{40chn}} \rangle$" (3 Data and Methods)
3. **Measure noise-bias free auto-power spectrum and errors**: Cross-power spectra of cubes; errors from cross-power of differenced pairs; linear k bins of width 4.1 h/Mpc; inverse-variance weighted averaging; 6-degree polynomial smoothing of errors; 3-sigma upper limit  
  > "have been calculated using a 6-degree polynomial fit to the raw values calculated per Equation" (Results, Measurement of CO auto-power spectrum at $0.001 \lesssim z \lesssim 4.5$)
   - parameter: k = 9.55-100.05 h/Mpc, 23 bins; lowest bin discarded  
  > "averaged across all $N_{b} = 23$ bins from $k_{\operatorname{CO(2-1)}} = 9.55$ h Mpc$^{-1}$ to 100.05 h Mpc$^{-1}$" (4.2 Measurement of CO auto-power spectrum)
   - assumption: power spectrum flat (shot noise) at k>~10 h/Mpc; measured in CO(2-1) frame with distortion factors for other transitions  
  > "By restricting our analysis to $k\gtrsim10$ h Mpc$^{-1}$, where the true power spectrum is expected to be flat" (2.1.2 Fourier-space dimensions)
   - fitting: _not stated_
   - validation: Noise-only simobserve simulations give consistent power  
  > "As an independent check on our error estimation, we also compute the noise-bias free power spectrum of noise-only simulated data cubes" (4.2 Measurement of CO auto-power spectrum)
4. **Lower limits from blind detections (mean brightness, shot noise)**: Sum GL19 line fluxes to get mean T_CO; analytic shot noise from individual fluxes; integrate D19 Schechter LFs  
  > "We begin by summing the line fluxes of the sixteen blindly detected CO emission line candidates reported in GL19" (4.1.1 Mean surface brightness at 99 GHz)
   - parameter: Rayleigh-Jeans conversion; area 1.69e4 arcsec^2; L'_upp=1e12, L'_min=1e8 K km/s pc^2  
  > "Extending the lower limit of integration down to $L'_{min}=10^8$ K km s$^{-1}$ pc$^2$ at all redshifts" (4.1.1 Mean surface brightness at 99 GHz)
   - assumption: Faint-end slope alpha=-0.2 fixed  
  > "Note that the faint-end slope, $\alpha$, has been fixed at $\alpha=-0.2$ for all LFs." (4.1.1 Mean surface brightness at 99 GHz)
   - fitting: _not stated_
   - validation: Compared revised ASPECS-Pilot value  
  > "resulting in a revised $\langle T_{\operatorname{CO}} \rangle=0.55\pm0.05$ $\mu$K for ASPECS-Pilot, consistent with our new measurement" (4.1.1 Mean surface brightness at 99 GHz)
5. **CO-MUSE masked auto-power and cross-shot noise**: Mask voxels outside ~1 arcsec/1 channel of MUSE positions, compute masked auto-power; cross-power with galaxy density field to get mean T_CO of MUSE galaxies; masking by flux threshold and one-by-one source  
  > "masking was performed on $\tau_1$, $\tau_2$, $\tau_3$, and $\tau_4$ to remove flux densities from voxels beyond a spatial radius of $\sim$1 arcsecond" (4.3.1 Masked noise-bias free auto-power spectrum)
   - parameter: 415 MUSE positions in cropped region  
  > "415 of these lie within the cropped region used here for the power spectrum analysis" (4.3 CO-galaxy statistics)
   - assumption: MUSE galaxies trace CO emitters  
  > "we expect a non-zero positive correlation" (4.3 CO-galaxy statistics)
   - fitting: _not stated_
   - validation: Errors from 100 simulations of random MUSE positions  
  > "include an additional contribution estimated from 100 simulations of random MUSE source positions" (4.3.1 Masked noise-bias free auto-power spectrum)

## Software

- **CASA** : tclean imaging, imcontsub, split, concat, statwt, simobserve  
  > "We repeat these steps for every block of scans and every spectral window, and merge visibilities in the four subsets using CASA task concat" (3 Data and Methods)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Sum of blind CO fluxes | 6.91 | 0.19 | Jy km/s | 4 | total CO flux of $6.91\pm0.19$ Jy km s$^{-1}$ |
| Mean CO surface brightness at 99 GHz (lower limit) | 0.55 | 0.02 | muK | 4 | $\langle T_{\operatorname{CO}} \rangle = 0.55\pm0.02$ $\mu$K |
| Total averaged CO power, 9.55-100.05 h/Mpc | -45 | 77 | muK^2 (Mpc/h)^3 | 3 | -45 \pm 77 \ \mu\mathrm{K}^2 \ (\mathrm{Mpc} \ \mathrm{h}^{-1})^3 |
| 3-sigma upper limit on CO power | <=190 (abstract 1.9e2; conclusion 187.29) | not stated | muK^2 (Mpc/h)^3 | 3 | $P_{\operatorname{CO},\operatorname{CO}}(k_{\operatorname{CO(2-1)}}) \le  190$ $\mu$K$^2$ (Mpc h$^{-1}$)$^3$ |
| Shot noise power from blind detections (cropped region) | 113.24 | not stated | muK^2 (Mpc/h)^3 | 4 | 113.24 $\mu$K$^2$ (Mpc h$^{-1}$)$^3$ for the full survey and cropped region, respectively |
| Shot noise from ASPECS LFs (total, CO(2-1) frame) | 170 | +290/-92 | muK^2 (Mpc/h)^3 | 4 | $P_{\operatorname{CO},\operatorname{CO}}^{shot}(k_{\operatorname{CO(2-1)}}) = 170^{+290}_{-92}$ |
| Fraction of CO brightness recovered by blind detections | 68.1-79.5 | not stated | percent | 4 | $\langle T_{\operatorname{CO}} \rangle_{\mathrm{LF,7\sigma}}/\langle T_{\operatorname{CO}} \rangle_{\mathrm{LF}}=68.1$–79.5% |
| Shot noise recovered by MUSE positions of blind detections | 106 | 6.5 | percent | 5 | recover $106\pm6.5$% of the total CO shot noise power |
| Excess CO(2-1) brightness from MUSE galaxies without ASPECS detection | 0.07 | 0.02 | muK | 5 | which can contribute $0.07\pm0.02$ $\mu$K, or $19\pm7.8$% of the total observed CO(2-1) emission |
| SNR on shot noise from toy estimate | 0.39 | not stated | dimensionless | 4 | Then, SNR $= 0.39$, and the CO power spectrum is not expected to be detected at high significance |

## Qualitative findings

- Blind detections account for nearly all CO shot noise power; power spectrum is less efficient than individual detection at this depth/volume  
  > "provides a better SNR on the shot-noise term than the power spectrum analysis" (5.1 Power spectrum vs. Individual galaxy detection)

## Claim tuples

- H: Does the ASPECS power spectrum constrain total CO shot noise power and LFs? | E: Noise-bias-free cross-power of time-split cubes at k=10-100 h/Mpc | R: Power consistent with zero; 3-sigma upper limit ~190 muK^2 (Mpc/h)^3 | F: Upper limit consistent with D19 LFs but rules out much of the allowed range, attributed to uncertain Phi* and L* at z>2 | **supported**
- H: Do blind detections account for the CO power from MUSE galaxies? | E: Masked auto-power and cross-shot noise with MUSE positions | R: Blind detections recover 106+-6.5% of shot noise; ~20% excess CO(2-1) mean intensity from undetected sources | F: Mostly accounted for by blind detections, with marginal faint contribution in CO(2-1) | **supported**
- H: What is the mean CO surface brightness at 99 GHz? | E: Sum blind detection fluxes; integrate LFs | R: 0.55+-0.02 muK, 68-80% of the total | F: Lower limit on total CO brightness | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Cross-power of data subsets removes noise bias when noise power is 2-3 orders of magnitude above signal  
  > "our estimated noise power is 2–3 orders of magnitude greater than the predicted CO power spectrum signal" (3 Data and Methods)
- Alternative: Subtracting independent noise power estimates rejected in favour of cross-power  
  > "we avoid *subtracting* this noise-bias term from the data based on independent estimates of $P_N$" (3 Data and Methods)
- How they decided it was enough: _not stated_
- Limitation (authors): Error on cross-shot noise is a lower estimate; CO(3-2)/CO(4-3) cannot be separated with low sensitivity  
  > "is derived via simulation of random MUSE positions only, and is a lower estimate of the true error" (4.3.2 Cross-shot noise power spectrum)
- Caveat (inferred, ours): Redshift ambiguity forces assuming CO(2-1) frame, with distortion factors
- Caveat (inferred, ours): Lower-limit mean brightness depends on cosmic variance in a small pencil beam
- Caveat (inferred, ours): Upper limit and sign-negative mean power show measurement is consistent with noise
- Caveat (inferred, ours): Adopted statistical errors rely on smoothed polynomial fit and gamma_N=0.25 assumption

## Reproducibility

- Data public (paper): ALMA project 2016.1.00324.L cited as data  
  > "*data*: 2016.1.00324.L." (Conclusions)
- Products in archive: _not stated_
- Missing: Power spectrum code and exact binning/windowing
- Missing: Scan-to-subset assignment
- Missing: Calibrated visibilities / D19 imaging parameters
- Missing: Specific noise-simulation configuration
- Data volume (inferred): Large: full Band 3 five-tuning mosaic visibilities, ~hundreds of GB to TB
- Score (inferred): 3/5, Data public and method described, but key implementation details are deferred or unstated, and processing of visibilities is heavy.
- Rediscovery candidate: no, Method is described but not complete enough, and results rely on data products from companion papers and unstated code.

## Links

- Method: (cite: Dillon2014) (Noise-bias free cross-power spectrum from data splits)
- Method: (cite: LidzTaylor2016) (Distortion factors and shot noise Schechter formula)
- Companion: (cite: Decarli2019_3mm) (CO luminosity functions and data imaging)
- Companion: (cite: GL2019_3mm) (Blind line and continuum search catalog)
- Companion: (cite: Boogaard2019_3mm) (MUSE counterparts and SED modeling)
- Related: ASPECS LP
- Related: ASPECS Pilot
- Related: COLDz
- Related: COPSS II
- Related: MUSE UDF

## Checks

```json
{
 "quotes": 72,
 "quotes_ok": 72,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 83,
  "stated": 55,
  "rate": 0.663
 },
 "evidence_ok": true
}
```

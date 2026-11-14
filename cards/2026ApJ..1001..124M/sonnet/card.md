# Multiwavelength ALMA Imaging of HD 34282: Dust-trapping Signatures of a Vortex Candidate

`2026ApJ..1001..124M` | The Astrophysical Journal 2026 | first author: Ma, Xiaoyi | arXiv: 2603.06992 | DOI: 10.3847/1538-4357/ae5105

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Is the bright azimuthal mm arc in the HD 34282 disk consistent with dust trapping in a vortex, as tested by its multi-wavelength morphology, spectral index and peak shifts?  
  > "enable us to probe the physical origin of the arc." (abstract)
- Target **HD 34282**: coordinates _not stated_; z/distance 309±2 pc  
  > "HD 34282 is a Herbig Ae star located at a distance of 309$\pm$2 pc" (1 Introduction); distance from Gaia (cite: Gaia_2023)  
  > "HD 34282 is a Herbig Ae star located at a distance of 309$\pm$2 pc" (1 Introduction)

## Data provenance

- ALMA projects: 2022.1.00315.S, 2015.1.00192.S, 2023.1.00108.S, 2017.1.01578.S
- bands: Bands 3, 4, 6, 7 (3.1, 2.1, 1.3, 0.9 mm)  
  > "new ALMA continuum observations at 3.1, 2.1, and 0.9 mm (Bands 3, 4, and 7) together with archival 1.3 mm data (Band 6)" (2.1 Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Band 3/4: C-6 (SB) + C-9 (LB); Band 7: C-4 (SB) + C-7 (LB)  
  > "The SB observations used C-6 configuration of 42 antennas with baselines from 15.3 m to 2.5 km" (2.1 Observations)
- baselines: _not stated_
- angular resolution: B3 0.095x0.081"; B4 0.081x0.049"; B6 0.056x0.051"; B7 0.059x0.050"  
  > "| Band 7    | 2022.1.00315.S | Ruobing Dong        | 335.55 - 351.50 | 0.059$\times$ 0.050   | 24.99" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: RMS 5.99, 7.41, 20.90, 24.99 µJy/beam at B3, B4, B6, B7  
  > "| Band 3    | 2022.1.00315.S | Ruobing Dong        | 89.54 - 105.48  | 0.095$\times$ 0.081   | 5.99" (Table 1)
- time on source: Band 3: ~49 min SB + ~142 min LB; Band 4: ~34 + ~82 min; Band 7: ~20 min SB + ~74 min LB  
  > "with a total on-source integration time of $\sim$142 min." (2.1 Observations)
- observing dates: B3 May-Jun 2023; B4 May-Jul 2023; B7 LB 24 Sep 2023, SB 23 Dec 2023  
  > "The LB observations at Band 7 were conducted on September 24, 2023" (2.1 Observations)
- pi or archival as stated: _not stated_
- External data: Processed concatenated Band 6 (1.3 mm) continuum visibilities  
  > "We used the processed dataset in which the SB and LB executions were concatenated, as presented by (cite: Francis_2020)" (2.1 Observations) [from (cite: Francis_2020)]
- External data: Dust midplane temperature at arc radius 29.6±0.1 K  
  > "At the arc radius, $T_{\rm dust} = 29.6 \pm 0.1$ K." (4.1 Optical Depth) [from (cite: Galloway_Sprietsma_2025)]
- External data: Gas surface density at arc radius 2.6 g cm^-2 from CO kinematics  
  > "We adopt $\Sigma_{\rm gas}(r_{\rm arc}=0.45'') = 2.6~{\rm g~cm^{-2}}$ inferred from CO kinematics" (4.3.2 Peak Shift) [from (cite: Longarini_2025)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline, then DSHARP-style procedures and self-calibration  
  > "The data reduction followed the standard procedures adopted by the DSHARP collaboration (cite: Andrews_2018)." (2.2 Data Reduction)
- casa version: CASA 6.4.1.12 (B3, B4 pipeline); 6.5.4.9 (B7 pipeline); 6.5.1.23 (self-cal)  
  > "Bands 3 and 4 observations were calibrated with the ALMA pipeline in CASA 6.4.1.12 (cite: CASA_2022), and Band 7 observations with the ALMA pipeline in CASA 6.5.4.9." (2.2 Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 5% absolute flux calibration for both bands  
  > "We adopt a 5$\%$ absolute flux-calibration uncertainty for both bands" (4.2 Spectral Index Distributions)
- self calibration: B3: 3 phase rounds (inf,300,100 s)+1 amp (inf); B4: 4 phase (inf,300,100,60 s)+1 amp; B7: 5 phase (inf,300,100,60,20 s), no amp  
  > "For the Band 7 data, five rounds of phase-only self-calibration were performed with solution intervals of solint = inf, 300 sec, 100 sec, 60 sec and 20 sec." (2.2 Data Reduction)

### Imaging

- task: tclean, threshold 3σ  
  > "The images are reconstructed using tclean with a threshold of 3$\sigma$ and a cell size of tenth the synthesized beam." (2.2 Data Reduction)
- deconvolver: mtmfs, scales [0,1,2,4,8] beams, nterms=2  
  > "with deconvolution scales of \[0, 1, 2, 4, 8\] beam sizes and nterms = 2" (2.2 Data Reduction)
- weighting robust: briggs, robust = 0.5  
  > "We adopted briggs weighting with robust = 0.5." (2.2 Data Reduction)
- uv taper: _not stated_
- cell size: one tenth of synthesized beam  
  > "a cell size of tenth the synthesized beam" (2.2 Data Reduction)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Line-containing channels flagged  
  > "channels containing any line emissions were first flagged from the data when present" (2.2 Data Reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Convolved to common 0.095x0.081" beam for comparison  
  > "We convolve all images to a common synthesized beam ($0.095 \times 0.081''$; Band 3 beam" (3.1 Images)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Band 6 observational setup and calibration  
  > "The observational setup and calibration procedures are described in detail in (cite: Francis_2020)." (2.1 Observations) [from (cite: Francis_2020)]
- Reduction procedure  
  > "The data reduction followed the standard procedures adopted by the DSHARP collaboration (cite: Andrews_2018)." (2.2 Data Reduction) [from (cite: Andrews_2018)]
- Global morphological model: three Gaussian rings + 2D Gaussian arc  
  > "We adopt the global morphological model of (cite: Curone_2025) for HD 34282" (Appendix galario) [from (cite: Curone_2025)]
- Coarse-to-fine MCMC scheme  
  > "similar to the procedure used in (cite: Curone_2025)" (Appendix galario) [from (cite: Curone_2025)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges and flagged channels
- Pipeline versions for archival data and Band 6 details
- Image sizes and mask choice for tclean
- MCMC walker count, steps, prior bounds in galario fits
- Phase-center/alignment details and reference execution
- How the arc radial FWHM and contrast were measured
- Gaia coordinates of target

## Analysis recipe

1. **Calibrate and self-calibrate visibilities**: ALMA pipeline, flag lines, average to 6 s and 8 channels, self-calibrate SB then concatenated, align with exoALMA tools  
  > "the data was averaged in time to 6 seconds and in frequency over 8 channels." (2.2 Data Reduction)
   - software: CASA, gaincal
   - fitting: _not stated_
   - validation: Peak SNR gains: 42% (B3), 60% (B4), 168% (B7)  
  > "The peak SNR was improved by 42$\%$ after the self-calibration." (2.2 Data Reduction)
2. **Parametric visibility fit for geometry and arc radius**: galario fit of three Gaussian rings and 2D Gaussian arc, Gaussian likelihood, emcee  
  > "The visibilities are modeled with three Gaussian rings and a 2D Gaussian arc." (3.2 Measurement of the Arc Morphology)
   - software: galario, emcee
   - fitting: Two-step coarse-to-fine emcee; Band 7 first then initialises others; amplitudes uniform in log  
  > "We start with the high-S/N Band 7 data, then use its posterior medians to initialize independent fits for Bands 3, 4, and 6" (Appendix galario)
   - validation: Residual images: noise-like at 3.1 and 2.1 mm, >10σ at 1.3 and 0.9 mm  
  > "At 1.3 and 0.9 mm, residual structures at $>10\sigma$ level remain" (Appendix galario)
3. **Remove axisymmetric emission and measure arc peak and width**: Deproject, frank 1D radial reconstruction, subtract, image residuals, subtract background profile from 180° opposite, measure peak and FWHM  
  > "We subtract the `frank` model from the visibilities, image the residuals, and measure the arc peak location and full width at half maximum (FWHM)" (3.2 Measurement of the Arc Morphology)
   - software: frank, CASA tclean
   - parameter: N=400, alpha=1.3, w_smooth=0.01, Rmax=3"  
  > "The hyper-parameters are set to $\alpha = 1.3$ and $w_\mathrm{smooth} = 0.01$" (3.2 Measurement of the Arc Morphology)
   - fitting: _not stated_
   - validation: Bootstrap, 500 realizations adding Gaussian noise at map RMS  
  > "We estimate the statistical uncertainties of the arc peak location and azimuthal width using a bootstrap approach for 500 realizations." (3.2 Measurement of the Arc Morphology)
4. **Estimate optical depth**: tau = -ln[1 - I/B(Tdust)] with Tdust 29.6 K; galario-model based estimate; scattering via Zhu 2019 relation  
  > "We estimate $\tau_\nu$ at each wavelength using a toy model based on the Eddington-Barbier approximation in an isothermal slab" (4.1 Optical Depth)
   - assumption: Dust and gas thermally coupled; constant temperature in azimuth; albedo up to 0.8 (0.7 representative)  
  > "we adopt a constant dust temperature with azimuth." (4.1 Optical Depth)
   - fitting: _not stated_
   - validation: Compared image-based vs galario-model-based estimates; ±5 K changes tau by 25-30%  
  > "a $\pm 5$ K change in $T_{\rm dust}$ would alter $\tau_\nu$ by $\sim$25-30% in the arc" (4.1 Optical Depth)
5. **Spectral index map B3-B4**: Align images, convolve to common beam, alpha = ln(I1/I2)/ln(nu1/nu2) where SNR>15  
  > "We compute the spectral index only for regions with SNR $>15$ in both bands." (4.2 Spectral Index Distributions)
   - fitting: _not stated_
   - validation: Compared with baseline-corrected arc and galario model images  
  > "we also compute $\alpha$ from the best-fit `galario` model images" (4.2 Spectral Index Distributions)
6. **Stokes number and comparison with vortex predictions**: St = pi rho_s a /(2 Sigma_gas) with a = lambda/2pi, rho_s=1 g/cm3, Sigma_gas=2.6 g/cm2; compare width and peak shift trends  
  > "We assume that emission at each wavelength is dominated by a characteristic size $a \sim\lambda_{\mathrm{obs}}/2\pi$ (cite: Draine_2006) and take $\rho_s = 1~\mathrm{g\,cm^{-3}}$." (4.3.2 Peak Shift)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 6.4.1.12, 6.5.4.9, 6.5.1.23: Pipeline calibration, self-calibration, tclean imaging  
  > "Self-calibration was then performed in CASA version 6.5.1.23, beginning with the SB data." (2.2 Data Reduction)
- **galario** : Parametric visibility modeling  
  > "as obtained from parametric $\{u,v\}$-plane fitting with `galario` (cite: Tazzari_2018)" (3.1 Images)
- **frank** : Non-parametric radial profile reconstruction  
  > "use `frank` (cite: Jennings_2020) to reconstruct a non-parametric axisymmetric radial intensity profile" (3.2 Measurement of the Arc Morphology)
- **emcee** : MCMC sampling of galario posteriors  
  > "using a Markov Chain Monte Carlo (MCMC) approach via `emcee` (cite: Foreman-Mackey_2013)" (Appendix galario)
- **exoALMA visibility-alignment tools** : Aligning execution blocks in the u-v plane  
  > "using the exoALMA visibility-alignment tools (cite: loomis_2025)" (2.2 Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Arc azimuthal FWHM at 0.9 mm | 65.8 | 0.7 | deg | 3 | / 0.9 mm / $23.1 \pm 2.6$ / $65.8 \pm 0.7$ / |
| Arc azimuthal FWHM at 3.1 mm | 37.1 | 1.4 | deg | 3 | / 3.1 mm / $35.0 \pm 2.2$ / $37.1 \pm 1.4$ / |
| Arc peak shift 0.9 to 1.3 mm | 15 | 4 | deg | 3 | The azimuthal peak shifts by $\sim15\pm4^\circ$ between 0.9 and 1.3 mm |
| Spectral index alpha_B4,B3 at arc | 2.48 | 0.18 | dimensionless | 5 | $\alpha_{\mathrm{B4,B3}} = 2.48 \pm 0.18$ |
| Spectral index of surrounding ring | 3.11 | 0.25 | dimensionless | 5 | $\alpha_{\mathrm{B4,B3}} \simeq 3.11 \pm 0.25$ |
| Arc-to-ring contrast at 0.9,1.3,2.1,3.1 mm | 1.5, 2.0, 2.8, 3.5 | not stated | dimensionless | 0 | contrast $=$ 1.5, 2.0, 2.8 and 3.5 at 0.9, 1.3, 2.1 and 3.1 mm, respectively |
| Arc optical depth at 3.1 mm (galario model) | 0.47 | not stated | dimensionless | 4 | the model yields $\tau_\nu \approx 0.47$ at the arc peak |
| Arc aspect ratios at 2.1,1.3,0.9 mm | 2.7, 3.2, 4.0 | not stated | dimensionless | 3 | We find aspect ratios of 2.7, 3.2, and 4.0 at 2.1, 1.3, and 0.9 mm, respectively |
| Observed Stokes number | ≲0.03 | not stated | dimensionless | 6 | This yields $\mathrm{St_\mathrm{obs}} \lesssim 0.03$ at all four wavelengths |

## Qualitative findings

- Arc sits in a double-gap, triple-ring disk; 0.9 mm shows arc shoulder, dimmer near-side ring and faint inner arc at r~0.17"  
  > "We also detect a faint, azimuthally extended arc at $r \sim 0.17''$ with $\sim7\sigma$ significance" (5 Additional Band 7 Features)

## Claim tuples

- H: Arc narrows azimuthally at longer wavelengths as expected for dust trapping | E: frank-residual arc FWHM at four wavelengths | R: FWHM falls from 65.8° to 37.1° from 0.9 to 3.1 mm | F: Consistent with size-dependent azimuthal trapping | **supported**
- H: Peak shifts follow vortex predictions for low Stokes numbers | E: Arc peak azimuth vs wavelength with St estimate | R: No shift among 1.3-3.1 mm; 15±4° shift at 0.9 mm opposite to rotation | F: Longer wavelengths consistent; 0.9 mm shift likely optical depth or temperature | **partially**
- H: Arc has larger grains or higher dust density than the ring | E: B3-B4 spectral index map | R: alpha 2.48 in arc vs 3.11 in ring | F: Consistent with enhanced grain growth and/or surface density | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Eccentric-disk apocenter pile-up cannot be excluded; unresolved optically thick clumps cannot be excluded  
  > "we cannot formally exclude the possibility that the arc consists of unresolved optically thick clumps" (4.1 Optical Depth)
- How they decided it was enough: _not stated_
- Limitation (authors): Arc may be optically thick at 0.9 mm; vortex origin not unique; need longer-wavelength and gas kinematics  
  > "A definitive test will require longer-wavelength continuum data to constrain the grain-size distribution" (Conclusions)
- Caveat (inferred, ours): Stokes number rests on a single assumed grain size and gas surface density from another paper
- Caveat (inferred, ours): Temperature assumed constant in azimuth
- Caveat (inferred, ours): galario model fails at 1.3 and 0.9 mm, and model-based optical depths are only at 3.1 and 2.1 mm
- Caveat (inferred, ours): Band 6 was processed by others, so band-to-band alignment may differ

## Reproducibility

- Data public (paper): Programs are listed by code; public status not stated  
  > "| Band 3    | 2022.1.00315.S | Ruobing Dong        | 89.54 - 105.48  | 0.095$\times$ 0.081   | 5.99                    | 60       |" (Table 1 (observations))
- Products in archive: _not stated_
- Missing: Processed Band 6 dataset from Francis et al. (2020)
- Missing: Exact self-calibration reference antennas and flagging
- Missing: emcee walkers, steps and bounds
- Data volume (inferred): ~200-500 GB raw for four bands with long baselines
- Score (inferred): 3/5, Data are listed and imaging settings and many parameters are given, but the processed Band 6 data, line-free channels and MCMC settings are missing.
- Rediscovery candidate: no, Band 6 needs a private processed product and several fitting settings are not stated.

## Links

- Method: (cite: Andrews_2018) (DSHARP reduction procedures)
- Method: (cite: Tazzari_2018) (galario)
- Method: (cite: Jennings_2020) (frank)
- Method: (cite: loomis_2025) (exoALMA visibility alignment tools)
- Companion: (cite: Curone_2025) (exoALMA HD 34282 arc morphology and model)
- Companion: (cite: Francis_2020) (Processed Band 6 data)
- Related: DSHARP
- Related: exoALMA

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2017.1.02578.S"
 ],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 49,
  "rate": 0.628
 },
 "evidence_ok": true
}
```

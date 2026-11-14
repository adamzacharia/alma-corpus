# Data Combination: Interferometry and Single-dish Imaging in Radio Astronomy

`2023PASP..135c4501P` | Publications of the Astronomical Society of the Pacific 2023 | first author: Plunkett, Adele | arXiv: 2303.02177 | DOI: 10.1088/1538-3873/acb9bd

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type technical_calibration_or_instrument

## Science

- Fields: instrumentation, nearby_galaxies
- Question: Which interferometer plus single-dish data combination methods recover the true sky flux best, and how can their performance be quantitatively assessed (new A-par, fidelity, power-spectrum and spectrogram diagnostics)  
  > "In this work, we provide an overview of the prominent available methods to combine single dish and interferometric observations." (abstract); "We develop a set of new assessment tools which are generally applicable to all radio-astronomical cases of data combination." (abstract)
- Target **Skymodel (simulated multi-scale molecular cloud)**: coordinates (RA,Dec) = (12h00m00.0s, -35d00m0.0s)  
  > "The center coordinate of the field was set as (RA,Dec) $=$ (12h00m00.0s, $-35$d00m0.0s)." (4.1 Simulated continuum observations); z/distance _not stated_; distance from _not stated_
- Target **M100 (NGC 4321)**: coordinates RA 12h22m54.900s, Dec +15d49m15.000s (phase center)  
  > "The galaxy M100 (NGC 4321) was observed by ALMA as Science Verification" (4.2 Observational, spectrally resolved data); "12h22m54.900s" (Table 5); "+15d49m15.000s" (Table 5); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00004.SV
- bands: M100: ALMA Band 3 (CO 1-0, 115.271 GHz); Skymodel: simulated at 115 GHz  
  > "(115.271 GHz, ALMA Band 3) molecular emission" (4.2 Observational, spectrally resolved data); "for an observing frequency of 115 GHz" (4.1 Simulated continuum observations)
- frequencies and spectral setup: M100 cube: 50 channels on CO(1-0) plus 10 baseline channels on each side (70 channels total); skymodel covers 2 GHz bandwidth  
  > "On each side of the spectral line, additional 10 channels are included in the cube to show the spectral baseline." (4.2 Observational, spectrally resolved data); "we covered 2 GHz bandwidth" (4.1 Simulated continuum observations)
- continuum bandwidth: _not stated_
- arrays: M100: ALMA 12m mosaic (47 pointings), 7m mosaic (23 pointings), SD on-the-fly map; Skymodel: simulated 12m, ACA 7m and SD  
  > "Observations were made of a 47 pointing mosaic with the 12m Array, a 23 pointing mosaic with the 7m Array, and an on-the-fly map with the SD array" (4.2 Observational, spectrally resolved data); "we adopted two configurations for 12m array (C-4 and C-1 in cycle 7) along with ACA 7m and SD" (4.1 Simulated continuum observations)
- configurations: Skymodel: 12m configurations C-4 and C-1 (cycle 7); M100 configurations not stated  
  > "we adopted two configurations for 12m array (C-4 and C-1 in cycle 7) along with ACA 7m and SD" (4.1 Simulated continuum observations)
- baselines: _not stated_
- angular resolution: Skymodel: 1.2'' (interferometer) and 57'' (SD); M100: 12m Array resolution <2''  
  > "The achieved beam sizes are 57$''$ for the SD data and 1.2$''$ for the interferometric data." (4.1 Simulated continuum observations); "down to the 12m Array resolution of $<2\ensuremath{''}$" (4.2 Observational, spectrally resolved data)
- max recoverable scale: For ALMA 12m nominal configurations (43 antennas) the MRS is approximately a factor 10 larger than the achieved angular resolution (general statement)  
  > "For the ALMA 12m nominal configurations with 43 antennas, the MRS is approximately a factor 10 larger than the achieved angular resolution." (Footnote 10)
- sensitivity: _not stated_
- time on source: Skymodel (simulated): 1040/1020/3549 minutes for 12m/7m/SD; M100 not stated  
  > "Consequently, the total integration time to cover the skymodel image with 12m/7m/SD array is 1040/1020/3549 minutes, respectively." (4.1 Simulated continuum observations)
- observing dates: _not stated_
- pi or archival as stated: M100 is ALMA Science Verification data (featured in a CASA Guide)  
  > "The galaxy M100 (NGC 4321) was observed by ALMA as Science Verification" (4.2 Observational, spectrally resolved data)
- Line: CO J=1-0 (115.271 GHz)
- Simulation/model as data: Skymodel: synthetic multi-scale molecular cloud with power-law power spectrum plus two bright point sources, 4096^2 pixels of 0.05'' (204.8'' per side), observed with simobserve in CASA 5.6.1 for 12m (C-4, C-1), ACA 7m and SD  
  > "An elegant way of achieving this is to emulate a multi-scale molecular cloud with a power spectrum that follows a power law." (4.1 Simulated continuum observations); "In addition we insert two bright point sources, one in a bright and one in a faint region." (4.1 Simulated continuum observations)

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

- task: tclean (mosaic gridder), 100,000 iterations; same parameters for all combination methods; also sdintimaging, feather  
  > "To facilitate the comparison among the combination methods, we fix all `tclean` parameters to common values. We set the number of iterations to 100,000." (2 Imaging Interferometric Data with CLEAN); "in this study we deal exclusively with mosaic maps" (2 Imaging Interferometric Data with CLEAN)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "with robust value of 0.5 (i.e. balance between natural and uniform weighting) for all runs of" (2 Imaging Interferometric Data with CLEAN)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: SD image mask (>0.3 x SD image max) plus additional regions from auto-multithresh with standard parameters  
  > "The mask is generated by first utilizing the SD image to mask (include) all regions above 0.3 times the max value in the SD image" (2 Imaging Interferometric Data with CLEAN); "using the standard “auto-multithresh” parameters" (2 Imaging Interferometric Data with CLEAN)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: For assessment, combination results are convolved and regridded to the reference image resolution (SD image or simulated model)  
  > "is assumed to be the combination result image convolved to the resolution of the reference image" (5 Assessment metrics)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Skymodel construction follows an earlier procedure  
  > "We follow the procedure described in (cite: koda2019)." (4.1 Simulated continuum observations) [from (cite: koda2019)]
- Simulated array configurations taken from the ALMA Technical Handbook  
  > "Following the ALMA Technical Handbook (cite: remijan2019)" (4.1 Simulated continuum observations) [from (cite: remijan2019)]
- auto-multithresh masking algorithm and its standard parameters  
  > "using the standard “auto-multithresh” parameters" (2 Imaging Interferometric Data with CLEAN) [from (cite: kepley2020)]
- SDINT algorithm details (full details and explanatory diagrams)  
  > "We refer the reader to (cite: rau2019) for full details and explanatory diagrams" (3.2 Joint Deconvolution: SDINT) [from (cite: rau2019)]
- TP2VIS method described in detail elsewhere  
  > "TP2VIS is roughly structured in four steps, with much more detail on each available in (cite: koda2019):" (3.4 TP2VIS) [from (cite: koda2019)]

### Not stated but needed to reproduce (our reading)

- Calibration of the M100 Science Verification data (manual vs pipeline, CASA version, flux scale) and which calibrated products/MS were used
- Actual sdfactor / effdishdiam values for Feather and MACF, sdgain and dishdia for SDINT (paper only says 'standard values')
- sdintimaging deconvolver, scales, thresholds, cell size and image size; tclean cell/imsize and stopping threshold
- Power-law index and normalisation of the skymodel, and level of the added Gaussian noise in the simulated data
- How the SD M100 cube and the skymodel SD image were generated/obtained (beam, units, header fixes) and exact regridding steps
- Line-free channels and any continuum subtraction for M100
- Values of the intermediate reference resolutions used for assessment (2'' versus 1.7'' stated inconsistently) and RMS_mask measurement region
- Number of flux bins and binning scheme for A-par vs flux diagnostics beyond the 10-bin example

## Analysis recipe

1. **Simulate ALMA observations of the skymodel**: Run simobserve on the synthetic skymodel for 12m (two configurations), ACA 7m and SD, with multiple fields and days  
  > "we ran the `simobserve` task in CASA version 5.6.1 to create simulated observational data in MeasurementSet format (MSs)" (4.1 Simulated continuum observations)
   - software: CASA simobserve 5.6.1
   - parameter: 12m (7m): 52 (17) fields, each visited 30 (90) times per session, 10 s integration per field  
  > "For 12m (7m) array, there are 52 (17) fields to cover the simulated image and each field is set to be visited 30 (90) times per observing session on different days with the integration time of 10 seconds per field." (4.1 Simulated continuum observations)
   - parameter: Skymodel 4096^2 pixels of 0.05'' (204.8'' per side)  
  > "The model has $4,096^2$ pixels with a size of 0.05$''$ each, resulting in an image size of 204.8$''$ each side" (4.1 Simulated continuum observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Prepare the M100 SD and interferometer data**: Header manipulation, axis reordering and regridding of M100 12m/7m/SD data  
  > "This dataset allows us to showcase the necessary preparatory steps of header manipulation, axis reordering, and regridding." (4.2 Observational, spectrally resolved data)
   - software: CASA, Python/astropy (DC_script)
   - parameter: Cube of 50 line channels plus 10 baseline channels on each side  
  > "On each side of the spectral line, additional 10 channels are included in the cube to show the spectral baseline." (4.2 Observational, spectrally resolved data)
   - fitting: _not stated_
   - validation: _not stated_
3. **Image interferometer-only data (int-CLEAN)**: tclean with Briggs weighting, mosaic gridder, 100,000 iterations and SD+auto-multithresh mask  
  > "In CASA, CLEAN and its extensions are all accessible via the" (2 Imaging Interferometric Data with CLEAN); "We set the number of iterations to 100,000." (2 Imaging Interferometric Data with CLEAN)
   - software: CASA 6.1 tclean
   - parameter: robust = 0.5  
  > "with robust value of 0.5 (i.e. balance between natural and uniform weighting) for all runs of" (2 Imaging Interferometric Data with CLEAN)
   - parameter: Mask: >0.3 x SD max plus auto-multithresh  
  > "The mask is generated by first utilizing the SD image to mask (include) all regions above 0.3 times the max value in the SD image" (2 Imaging Interferometric Data with CLEAN)
   - fitting: _not stated_
   - validation: _not stated_
4. **Combine SD and interferometric data with each method**: Feather, SDINT (sdintimaging), MACF (tclean with SD image as startmodel, then feather) and FSSC applied to skymodel and M100; TP2VIS implemented in the script but not evaluated  
  > "The methods we present for evaluation are: Feather" (3 Combination Methods); "we decided not to include it in the evaluation section of this paper" (3.4 TP2VIS)
   - software: CASA 6.1 feather, CASA 6.1 sdintimaging, CASA 6.1 tclean, FSSC Python code, DC_script
   - parameter: Standard (default-like) values for briggs, sdfactor (Feather, MACF) and sdgain (SDINT); numbers not given  
  > "For simplicity, our data combinations assumed standard values for reduction parameters such as" (6.4 Single-dish flux recovery)
   - parameter: MACF: SD image (Jy per pixel) used as tclean startmodel, then feathered with the SD image  
  > "providing the SD image (in units of Janskys per pixel) as the starting model image" (3.3 Model-assisted CLEAN plus Feather method (MACF))
   - assumption: Flux scales of the interferometer and SD data are aligned; astrometry aligned; images corrected for PB response  
  > "We assume that flux scales are aligned, but further fine-tuning can be done for specific use cases." (3 Combination Methods)
   - fitting: _not stated_
   - validation: Results compared against the true skymodel (simulation) or the SD cube (M100)  
  > "In real observations the emission of any interferometric or data combination map can be compared against its SD counterpart" (5 Assessment metrics)
5. **Assess image quality with A-par, fidelity, flux vs signal, power spectra and spectrograms**: Pixel-by-pixel Accuracy parameter A=(I-R)/|R| and Fidelity inside an adaptive assessment mask, at the reference resolution; histograms, A-par vs flux bins, spatial power spectra (median in annuli of 2D FT) and per-channel A-par spectrograms  
  > "In this work, we introduce a new assessment parameter which we call the *Accuracy parameter* (A-par)." (5.2 Accuracy parameter & Fidelity: assessing flux recovery); "In practice the distribution of power is measured by computing the 2D Fourier transforms of the integrated intensity images and measuring the median in progressively larger annuli." (5.4 Power Spectra (PS): spatial scale sensitivity)
   - software: DC_script, Python/astropy
   - parameter: Assessment mask threshold 3 x RMS_mask (off-source RMS at native resolution), corrected for PB response and for beam ratio  
  > "We define the “mask threshold” at a level of $3\times RMS_{mask}$, where $RMS_{mask}$ is the off-source noise level of the target (in this case, interferometric) image at its native resolution $\theta_0$." (5.1 Assessment mask: definition and adaptive thresholding)
   - parameter: A-par computed per pixel/voxel after convolving and regridding to the reference image beam and grid  
  > "We calculate both A-par and Fidelity parameters pixel-by-pixel (or voxel in cubes) in our images" (5.2 Accuracy parameter & Fidelity: assessing flux recovery)
   - assumption: For the skymodel the reference is the true model; for M100 the reference is the SD cube  
  > "(in the case of simulated test data) or the original SD image (in the case of a real observation)" (7 Summary)
   - fitting: _not stated_
   - validation: Feather used as benchmark combination method  
  > "Feather is used as a benchmark of any combination technique presented here, since it is the most common method used in CASA." (5 Assessment metrics)
6. **Compare combination methods**: Compare A-par distributions, flux recovery per signal bin, intensity and A-par power spectra, and M100 spectrograms for int-CLEAN, Feather, SDINT, MACF (FSSC nearly identical to Feather)  
  > "We quantitatively investigate the performance of the different data combination techniques" (6.3 Comparison between data combination methods); "The FSSC method is not shown but produced results nearly identical to Feather in this test." (6.3 Comparison between data combination methods)
   - software: DC_script
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 6.1: Imaging (tclean) and data combination (feather, sdintimaging) for all combination tests  
  > "For actual data analysis work in this study, we use exclusively the CASA (Common Astronomy Software Applications) package (cite: casa2022) version 6.1." (2 Imaging Interferometric Data with CLEAN)
- **simobserve (CASA)** 5.6.1: Creating simulated 12m/7m/SD observations of the skymodel  
  > "we ran the `simobserve` task in CASA version 5.6.1 to create simulated observational data in MeasurementSet format (MSs)" (4.1 Simulated continuum observations)
- **tclean** : CLEAN imaging of interferometric data, startmodel step of MACF  
  > "In CASA, CLEAN and its extensions are all accessible via the" (2 Imaging Interferometric Data with CLEAN)
- **feather** : Combining high- and low-resolution images in Fourier space (Feather, MACF)  
  > "The algorithm is implemented as a CASA task of the same name." (3.1 Feather)
- **sdintimaging** : SDINT joint deconvolution of SD and interferometer data  
  > "permits joint deconvolution of wideband SD and interferometer data" (3.2 Joint Deconvolution: SDINT)
- **TP2VIS** : Included in the accompanying software but not evaluated in the paper  
  > "we decided not to include it in the evaluation section of this paper" (3.4 TP2VIS)
- **DC_script** : Python script running the combination methods and the assessment metrics (github.com/teuben/DataComb)  
  > "“DC_script” also includes the full set of quality assessment metrics described in this work to evaluate the performance of the different data combination methods" (3.6 Software developed in this study)
- **FSSC Python code (Faridani et al.)** : Image-domain short spacing correction incorporated in the script suite  
  > "they provide a stand-alone Python code that we have also incorporated into our suite of combination methods" (3.5 Faridani’s Short Spacing Correction (FSSC) method)
- **Astropy** : Used within DC_script  
  > "that runs with Python and incorporates Astropy" (3.6 Software developed in this study)
- **numpy** : _not stated_
- **scipy** : _not stated_
- **matplotlib** : _not stated_
- **analysisUtils** : _not stated_

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Skymodel int-CLEAN A-par (mean, dispersion) | -0.60 | 0.43 (dispersion) | dimensionless | 5 | (red histogram; A-par$\approx-0.60\pm0.43$) |
| Skymodel Feather A-par (mean, dispersion) | -0.08 | 0.24 (dispersion) | dimensionless | 5 | (here Feather, blue histogram; A-par$\approx -0.08\pm 0.24$) |
| Skymodel total flux recovered by int-CLEAN | ~32% | not stated | % of reference flux | 5 | While int-CLEAN only recovers $\sim$ 32% of the total reference flux, Feather manages to improve these values up to 89%. |
| Skymodel total flux recovered by Feather | ~89% | not stated | % of reference flux | 5 | While int-CLEAN only recovers $\sim$ 32% of the total reference flux, Feather manages to improve these values up to 89%. |
| Skymodel total flux recovery by SDINT and MACF | above ~92% | not stated | % of reference flux | 6 | The total flux recovery is improved by the SDINT and MACF methods with total flux values above $\sim$ 92% with respect to the true sky emission. |
| Skymodel SDINT A-par dispersion | 0.13 | not stated | dimensionless | 6 | While SDINT shows a smaller dispersion of the A-par values ($\sigma($A-par$)=0.13$ |
| Skymodel MACF mean A-par | -0.08 | not stated | dimensionless | 6 | MACF shows a better mean A-par value (A-par = -0.08 |
| Peak flux loss of brightest compact skymodel source in int-CLEAN | ~40% | not stated | % of true peak | 6 | the peak flux of this source in the interferometric-alone int-CLEAN observations is reduced by a factor of $\sim$ 40% compared to the true emission in our skymodel |
| M100 int-CLEAN mean A-par over channels | -0.51 | 0.07 | dimensionless | 5 | with mean 50% flux losses (A-par$=-0.51\pm0.07$) |
| M100 Feather mean A-par over channels | -0.07 | 0.04 | dimensionless | 5 | respect to the SD flux per channel (A-par$=-0.07\pm0.04$) |
| M100 SDINT A-par and dispersion at SD resolution | |A-par| = -0.11 (as written) | sigma(A-par) = 0.06 | dimensionless | 6 | while SDINT shows slightly larger differences with respect to the SD flux ($/$A-par$/=-0.11$ and $\sigma($ A-par$)=0.06$) |
| M100 Feather and MACF A-par dispersion | 0.04 | not stated | dimensionless | 6 | both showing narrow A-par distributions ($\sigma($ A-par$)=0.04$) |

## Qualitative findings

- Interferometric filtering affects flux recovery at all scales, including compact structures comparable to the beam, not only beyond the MRS  
  > "our results clearly demonstrate how the interferometric filtering has a significant impact at all scales" (6.1 The indispensable short-spacing information)
- FSSC produced results nearly identical to Feather in the skymodel test  
  > "The FSSC method is not shown but produced results nearly identical to Feather in this test." (6.3 Comparison between data combination methods)
- Recovered power-spectrum values and slopes in interferometric images should be interpreted with extreme caution  
  > "The physical interpretation of the recovered SPS in interferometric observations (e.g. absolute values and changes in the power spectrum slope) should be treated with extreme caution." (6.3 Flux and A-par power spectra)

## Claim tuples

- H: Does omitting single-dish data cause significant flux and spectral-line errors in interferometric images of resolved sources | E: Compared int-CLEAN with combined images against the true skymodel and the M100 SD cube using A-par, flux vs signal, power spectra and spectrograms | R: int-CLEAN recovers ~32% of the skymodel flux and loses ~50% on average in M100 channels; combination recovers ~89-92% | F: Interferometer-only reductions can miss up to 90% of flux at all scales, and deform line profiles | **supported**
- H: Do the tested combination methods all improve over interferometry alone | E: Applied Feather, SDINT, MACF and FSSC to skymodel and M100 | R: Feather, SDINT and MACF recover most flux with errors of about 10% or less | F: Any tested combination method is better than interferometric data alone | **supported**
- H: Is any one combination method clearly superior | E: Compared A-par statistics and spectrograms of methods on both datasets | R: SDINT and MACF best on the skymodel; Feather and MACF best on M100 at SD resolution | F: Performance varies with target structure; no clear universal winner | **partially**
- H: Is the new A-par parameter a better diagnostic than Fidelity | E: Computed both A-par and Fidelity maps and histograms for the same combinations | R: A-par is signed and has a defined optimum, Fidelity is unsigned and has no target value | F: A-par has higher diagnostic value than Fidelity | **supported**
- H: Does lacking short-spacing information distort spectral line profiles | E: Compared M100 spectra from int-CLEAN, Feather and SDINT in two regions | R: int-CLEAN spectra show negative features, reduced FWHM and shifted peak | F: Data combination is needed to preserve line fluxes and kinematic information in cubes | **supported**

## Reasoning

- Why this data: Simulated skymodel gives a known truth; M100 chosen as a spectrally resolved real example where flux must be recovered per channel  
  > "Only with simulated observations can the accuracy of the image reconstruction be properly measured, since in that case the “true” intensity distribution on the sky is known." (4.1 Simulated continuum observations); "we therefore choose the spectrally resolved observation of the galaxy M100 as an example of real observational data" (4.2 Observational, spectrally resolved data)
- Why this method: Feather used as the benchmark method because it is the most common one in CASA  
  > "Feather is used as a benchmark of any combination technique presented here, since it is the most common method used in CASA." (5 Assessment metrics)
- Alternative: TP2VIS not evaluated because it was less straightforward to use consistently across datasets; included only in the accompanying software  
  > "TP2VIS turned out to be less straight-forward to use effectively and consistently across different datasets" (3.4 TP2VIS)
- Alternative: J-comb linear combination technique not explored  
  > "is a new linear combination technique that has been benchmarked against both CASA’s `feather` and Miriad’s `immerge` tasks, but is not further explored in this work" (Footnote 2)
- Alternative: Impact of the feather lowpassfiltersd option not investigated  
  > "We did not further investigate the impact of `lowpassfiltersd`." (3.1 Feather)
- How they decided it was enough: _not stated_
- Limitation (authors): Test cases exclude bright emission extending beyond the well-characterised primary beam  
  > "Finally, we use test cases without bright emission that extends or emerges beyond the area of the well-characterised PB-response." (3 Combination Methods)
- Limitation (authors): At SD resolution the M100 comparison has few voxels per channel, making ~10% differences hard to interpret  
  > "Comparisons within these 10% variations are however difficult to interpret given the low number statistics available" (6.4 Single-dish flux recovery)
- Limitation (authors): Standard values were assumed for reduction parameters (briggs, sdfactor, sdgain) for simplicity  
  > "For simplicity, our data combinations assumed standard values for reduction parameters such as" (6.4 Single-dish flux recovery)
- Caveat (inferred, ours): Method ranking rests on one simulated skymodel and one galaxy; no repeats or uncertainty on the differences between methods
- Caveat (inferred, ours): Reference for M100 is the SD cube itself, so SD calibration errors and SD-resolution averaging limit the test; ~20 voxels per channel
- Caveat (inferred, ours): Method parameters (sdfactor, sdgain, effdishdiam) were not tuned, so ranking may change with tuning
- Caveat (inferred, ours): M100 calibration and the origin of the SD cube are not described in the paper
- Caveat (inferred, ours): Noise properties of the simulated data are not given, so noise-dependent A-par widths are hard to compare

## Reproducibility

- Data public (paper): Scripts, data to reproduce figures and documentation released on GitHub; M100 is ALMA Science Verification data  
  > "The script suite for running the combination methods and our evaluation tools, and the data to reproduce the figures in this paper are available from <https://github.com/teuben/DataComb>." (1 Introduction)
- Products in archive: _not stated_
- Code: DC_script and assessment tools at https://github.com/teuben/DataComb  
  > "The script, data, and documentation are available at <https://github.com/teuben/DataComb>." (3.6 Software developed in this study)
- Missing: Numeric values of sdfactor/sdgain/effdishdiam/dishdia and tclean/sdintimaging threshold and cell parameters
- Missing: M100 calibration details and which MS/SD products were used
- Missing: Skymodel power-law index and noise level; random seeds
- Data volume (inferred): Roughly tens of GB for the M100 12m+7m+SD cubes and simulated MSs (estimate, not in paper)
- Score (inferred): 4/5, Public code and data on GitHub plus an explicit recipe and many numeric A-par/flux-recovery results; several tclean/combination parameters and M100 calibration are left to the scripts.
- Rediscovery candidate: yes, M100 SV data are public, the methods and metrics are clearly defined and the main results are numeric (A-par means, flux recovery fractions), though exact parameters must come from the released scripts.

## Links

- Method: (cite: koda2019) (TP2VIS method and skymodel construction procedure)
- Method: (cite: rau2019) (SDINT algorithm (sdintimaging))
- Method: (cite: faridani2018) (FSSC image-domain combination method)
- Method: (cite: kepley2020) (auto-multithresh masking algorithm)
- Method: (cite: cotton2017) (Comprehensive discussion of feather)
- Companion: (cite: mason2020) (Update on the feathering technique of data combination)
- Companion: (cite: PHANGS_datareduction) (ALMA combination in PHANGS data reduction)
- Related: ALMA Science Verification M100 Band 3 data (2011.0.00004.SV)
- Related: Lorentz Center workshop on interferometer and single-dish data combination (2019)

## Checks

```json
{
 "quotes": 97,
 "quotes_ok": 97,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 104,
  "stated": 62,
  "rate": 0.596
 },
 "evidence_ok": true
}
```

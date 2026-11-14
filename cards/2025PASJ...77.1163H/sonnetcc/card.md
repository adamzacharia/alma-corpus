# ALMA deep field in SSA22: Reconstructed [C II] luminosity function at z = 6

`2025PASJ...77.1163H` | Publications of the Astronomical Society of Japan 2025 | first author: Hayatsu, Natsuki H. | arXiv: 2510.02303 | DOI: 10.1093/pasj/psae094

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Why two [C II] line emitter candidates in the ADF22 Cycle 2 data were spurious (statistics, TDM smoothing, non-Gaussian noise, technical problems), and how to reconstruct the [C II] luminosity function at z~6 with completeness and contamination corrections  
  > "We investigate the detectability of far-infrared emitters in ALMA deep fields using mock observations by injecting artificial line-emitting sources into the visibility planes." (abstract); "We also discuss our investigation, conducted together with the ALMA operations team, of a possible technical problem in the original observations." (abstract)
- Target **ADF22 (ALMA Deep Field in SSA22), Cycle 2 mosaic**: coordinates RA (J2000) = 22h17m34s, Dec (J2000) = +00d17'00'' (field centre)  
  > "The field is centered on a $z$ = $3.09$ proto-cluster; RA (J2000) = 22$\rm ^h$17$\rm ^m$34$\rm^s$, Dec (J2000) = +00$^\circ$17$'$00$''$." (Original Data, Cycle-2 data); z/distance field centred on a z = 3.09 proto-cluster; [C II] search coverage z = 6.0-6.5  
  > "The field is centered on a $z$ = $3.09$ proto-cluster; RA (J2000) = 22$\rm ^h$17$\rm ^m$34$\rm^s$, Dec (J2000) = +00$^\circ$17$'$00$''$." (Original Data, Cycle-2 data); distance from _not stated_
- Target **ADF22-LineA and ADF22-LineB ([C II] candidates)**: coordinates LineA (22h17m37.43s, +00d17'10''.7) at 253.79 GHz; LineB (22h17m31.95s, +00d18'20''.3) at 269.92 GHz (assignment to A/B inferred from listed order)  
  > "resulted in the detection of two emission lines, at 253.79 and 269.92 GHz, with J2000 positions" (The Previous Method); "lie at $z = 6.0$ and $6.5$, respectively." (Introduction); z/distance z = 6.0 (LineA) and z = 6.5 (LineB) if the line is [C II]  
  > "then these galaxies dubbed ADF22-LineA and ADF22-LineB lie at $z = 6.0$ and $6.5$, respectively." (Introduction); "lie at $z = 6.0$ and $6.5$, respectively." (Introduction); distance from [C II] line identification assumed (candidates were not confirmed)  
  > "is the correct line identification, then these galaxies dubbed ADF22-LineA and ADF22-LineB lie at" (Introduction); "lie at $z = 6.0$ and $6.5$, respectively." (Introduction)

## Data provenance

- ALMA projects: 2013.1.00162.S, 2017.1.00602.S, 2013.1.00718.S, 2019.1.00883.S
- bands: Band 6 TDM (Cycle 2); Band 3 observations for one candidate  
  > "The field was observed using Band 6 time division mode (TDM) correlator, yielding four 1.875-GHz spectral windows (SPWs)" (Original Data, Cycle-2 data); "Also, Band 3 observations for one of the candidates were performed." (Original Data, Cycle-5 data)
- frequencies and spectral setup: Cycle 2: four 1.875-GHz SPWs at 254, 256, 270, 272 GHz, search coverage 253.1-272.8 GHz, ~18 km/s channels (36 km/s resolution); Cycle 5: FDM, 4 x 1920 channels over 7.5 GHz, fields at 251.284 and 261.183 GHz  
  > "yielding four 1.875-GHz spectral windows (SPWs) with central frequencies of 254, 256, 270, and 272 GHz, where no significant atmosphere absorption is seen" (Original Data, Cycle-2 data); "and a frequency coverage of 253.1–272.8 GHz" (Original Data, Cycle-2 data); "Single fields centered on the targets were observed at frequencies of 251.284 and 261.183 GHz for ADF22-LineA and ADF22-LineB, respectively." (Original Data, Cycle-5 data)
- continuum bandwidth: _not stated_
- arrays: 12-m array, 33-36 antennas (Cycle 2)  
  > "The configurations using 33–36 12-m antennas are C34-2 and C34-4." (Original Data, Cycle-2 data)
- configurations: Cycle 2: C34-2 and C34-4; Cycle 5: C43-3  
  > "The configurations using 33–36 12-m antennas are C34-2 and C34-4." (Original Data, Cycle-2 data); "in array configuration C43-3, where the PWV was 1.4 mm." (Original Data, Cycle-5 data)
- baselines: _not stated_
- angular resolution: Cycle 2: 0.54x0.49 arcsec (2014), 1.24x0.87 arcsec (2015), combined 0.72x0.62 arcsec; Cycle 5: ~1.0x0.6 arcsec  
  > "The data observed in 2014 and 2015 have typical angular resolutions of $0''.54 \times 0''.49$ and $1''.24 \times 0''.87$, respectively, and the combined data has $0''.72 \times 0''.62$ angular resolution." (Original Data, Cycle-2 data); "the angular resolution was around $1''.0 \times 0''.6$." (Original Data, Cycle-5 data)
- max recoverable scale: _not stated_
- sensitivity: Cycle 2 RMS 0.7, 0.7, 0.8, 0.9 mJy/beam per SPW at 36 km/s; Cycle 5 median ~0.77 mJy/beam at ~36 km/s  
  > "the four SPWs have root-mean-square (RMS) noise levels of 0.7, 0.7, 0.8, or 0.9 mJy beam$^{-1}$ at a 36 km s$^{-1}$ velocity resolution." (Original Data, Cycle-2 data); "The median noise value is $\approx 0.77$ mJy beam$^{-1}$ at $\approx 36$ km s$^{-1}$ spectral resolution" (Original Data, Cycle-5 data)
- time on source: Cycle 2: 2.5 min (2014) and 2.0 min (2015) per pointing; Cycle 5: ~11 min  
  > "The on-source time per pointing in the fields is 2.5 min. and 2.0 min. for 2014 and 2015, respectively." (Original Data, Cycle-2 data); "On-source integration times were $\approx 11$ min" (Original Data, Cycle-5 data)
- observing dates: June 2014 and April 2015 (Cycle 2); April 2017 (Cycle 5)  
  > "in June 2014 and April 2015 (Proposal ID 2013.1.00162.S, PI: H. Umehata)" (Original Data, Cycle-2 data); "observations were undertaken in April 2017 (2017.1.00602.S, PI: N. H. Hayatsu)" (Original Data, Cycle-5 data)
- pi or archival as stated: Cycle 2 PI H. Umehata (2013.1.00162.S); Cycle 5 PI N. H. Hayatsu (2017.1.00602.S); the survey is re-analysed from earlier published data  
  > "(Proposal ID 2013.1.00162.S, PI: H. Umehata)" (Original Data, Cycle-2 data); "which were taken in ALMA Cycle 2 by (cite: umehata2017)" (Introduction)
- Line: [C II] 158 um fine-structure line (z = 6.0-6.5 coverage) (not stated)
- External data: Local [C II] luminosity function (double power law parameters alpha, beta, L*, phi*) used as model input  
  > "The estimated \[C ii\] LFs at $z$ = $0.0023$–$0.076$ (cite: hemmati2017) are derived from follow-up observations of samples from the Great Observatories All-sky LIRG Survey (cite: diaz2013)." (The LF Reconstruction) [from Hemmati et al. 2017 (cite: hemmati2017)]
- External data: High-z [C II] LF lower limit at z=4.4 (ALESS serendipitous detections) and upper limit from the ADF22 follow-up  
  > "we indicate the lower limit at $z$ = $4.4$ based on two serendipitous detections in the ALESS survey (cite: swinbank2012) (hereafter S12) and the upper limit from (cite: hayatsu2019) (hereafter H19)." (The LF Reconstruction) [from Swinbank et al. 2012 (cite: swinbank2012); Hayatsu et al. 2019 (cite: hayatsu2019)]
- External data: Observed [C II] luminosity-FWHM correlation (Tully-Fisher-like) used to assign line widths  
  > "The latter implies the Tully-Fisher relation (cite: kohandel2019)." (The LF Reconstruction) [from Kohandel et al. 2019 (cite: kohandel2019)]
- External data: SFR-L[CII] relations for metal-poor dwarfs and starbursts  
  > "which is calibrated using observations of nearby low-metallicity dwarf galaxies and starburst galaxies" (Implications for Cosmic Star-Formation History) [from De Looze et al. 2014 (cite: delooze2014)]
- External data: Empirical SFR-line luminosity relations for ULIRGs ([O I], [N II], [O III] lines)  
  > "The SFRs are calculated from line luminosities using the empirical relations for ultra-luminous infrared galaxies estimated by (cite: farrah2013)." (Implications for Cosmic Star-Formation History) [from Farrah et al. 2013 (cite: farrah2013)]
- External data: Flux to [C II] luminosity conversion equation  
  > "The calculation to convert flux to the \[C ii\] luminosity, $L_{\rm [CII]}$, using luminosity distance $D_{\rm L}$, observed frequency $\nu_{\rm o}$, velocity-integrated flux $S^{\rm v}$ is written as (e.g., (cite: carilli2013))" (Source Injection) [from Carilli & Walter 2013 (cite: carilli2013)]
- Simulation/model as data: Mock ADF22 visibilities: real-data visibility noise replaced by pure Gaussian noise with Hanning smoothing; 100 blank mock mosaics, 320 single-pointing sets  
  > "We measure the RMS value and the mean value of the noise in the visibility plane and replace the values with pure Gaussian noise." (The Mock Observations, Replaced Data); "We generate 100 mock mosaic data sets by using the replacement process." (Results, Statistical Fluctuation)
- Simulation/model as data: simobserve single-pointing TDM and FDM mock data (320 sets each, 4.5 min per field)  
  > "we generate mock single-pointing data for both TDM and FDM modes using simobserve, with pure Gaussian noise, with Hanning smoothing applied, as in the real observations." (The Mock Observations, Simulated Data); "We use each field as the test, i.e., 320 data sets for TDM and FDM, respectively." (The Mock Observations, Simulated Data)
- Simulation/model as data: Artificial Gaussian line sources injected in the visibility plane: 121 (peak S/N, FWHM) sets, 84 positions, 100 repeats, 1,016,400 sources  
  > "We inject 1,016,400 sources in total." (Source Injection)

## Processing

### Calibration

- pipeline or manual: pipeline re-run with an updated version (version not given)  
  > "We have examined all the observing logs and the data scan by scan and re-run the pipeline with a more updated (and reliable) version." (Technical Problems)
- casa version: CASA 4.5.3 (stated for the analysis)  
  > "The data are analyzed with the Common Astronomy Software Application (`casa`) ver. 4.5.3 (cite: casa2022)." (Introduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: uvcontsub and clean for dirty continuum-subtracted cubes (real data); TCLEAN for dirty cubes from mock visibilities  
  > "We make ’dirty’ continuum-subtracted datacubes using uvcontsub and clean." (Original Data, Cycle-2 data); "The generated visibility data are converted into the ’dirty’ image cube using TCLEAN." (The Mock Observations, Replaced Data)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: 946 x 1896 pixels x 112 channels x 4 SPWs (~10^9 pixels)  
  > "946 pixels $\times$ 1896 pixels $\times$ 112 frequency channels $\times$ 4 spectral windows (SPWs)" (Footnote 2)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub (UV-plane)  
  > "We make ’dirty’ continuum-subtracted datacubes using uvcontsub and clean." (Original Data, Cycle-2 data)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: boxcar (top-hat) spectral smoothing, widths 0, 2, 4, ..., 12, 15, 18, ..., 21 channels (~18 km/s each); no spatial smoothing  
  > "The top-hat spectral smoothing window is set to be 0, 2, 4, ..., 12, 15, 18, ..., 21 channels, with a width corresponding to $\sim$18 km s$^{-1}$." (Smoothing Process); "We do not consider spatial smoothing since high-$z$ emitters should be observed as point sources." (Footnote 7)
- final beam: combined Cycle 2 beam 0.72x0.62 arcsec  
  > "and the combined data has $0''.72 \times 0''.62$ angular resolution." (Original Data, Cycle-2 data)
- final rms: 0.7, 0.7, 0.8, 0.9 mJy/beam per SPW at 36 km/s  
  > "the four SPWs have root-mean-square (RMS) noise levels of 0.7, 0.7, 0.8, or 0.9 mJy beam$^{-1}$ at a 36 km s$^{-1}$ velocity resolution." (Original Data, Cycle-2 data)

### Inherited from earlier work

- Cycle 2 ADF22 observations and reduction  
  > "(Proposal ID 2013.1.00162.S, PI: H. Umehata), as detailed in (cite: umehata2017)." (Original Data, Cycle-2 data) [from (cite: umehata2017)]
- Source-finding procedure (smoothing, RMS normalisation, clumpfind low=4.5, >6 sigma and > max negative S/N selection)  
  > "In this section, we briefly describe the previous method to extract line emitter candidates." (The Previous Method) [from (cite: hayatsu2017)]
- clumpfind parameter set for the blank mock search  
  > "We search for noise clumps in the blank mock data using clumpfind (cite: williams1994) with the same parameter set as the previous search." (Results, Statistical Fluctuation) [from (cite: hayatsu2017)]
- Selection of 80 pointing fields (Field 2 - Field 81) and survey area  
  > "In order to search faint emission-line sources, we use high-sensitivity data of 80 pointing fields, Field 2–Field 81" (Introduction) [from (cite: hayatsu2017)]
- Error-function form for Q(x) and C(x)  
  > "The results of $Q(x)$ and $C(x)$ can be approximated with the error function (e.g., (cite: hatsukade2016)):" (The Detection Methods) [from (cite: hatsukade2016)]

### Not stated but needed to reproduce (our reading)

- clumpfind parameters other than the 'low' threshold of 4.5 (high threshold, step levels, minimum clump size)
- The weighting table used to weight N_cor by luminosity bin (referred to as Tab. weighting but not given in the text)
- tclean/clean parameters for the real and mock cubes (weighting, robust, cell size, deconvolver, niter, threshold, masking)
- Line-free channels or fit order used in uvcontsub
- Which RMS measurement per channel and which sky mask were used to normalise the S/N cubes
- Exact scripts for visibility noise replacement (RMS and mean estimates per baseline/channel, flag handling) and Hanning smoothing
- simobserve inputs (antenna configuration files, scan times, hour angles, Tsys settings)
- Version of the ALMA pipeline and CASA used in the pipeline re-run; calibration products and flux scale
- Number of mock mosaics: 25 for four SPWs vs 100 quoted elsewhere is not reconciled
- Final choice of phi*(z) amplitude fitting, gamma value, and the quantitative LF output (no table of corrected LF given)
- Rest frequency of [C II] adopted and the exact luminosity bins

## Analysis recipe

1. **Prepare Cycle 2 smoothed S/N cubes and the previous source-finding baseline**: Make dirty continuum-subtracted cubes, spectrally smooth with boxcar widths, normalise each channel by its RMS to form S/N cubes, then run clumpfind and select >6 sigma clumps exceeding the maximum negative clump  
  > "As each spectral data slice has a different RMS value as shown in Figure 1, we normalize each slice by its RMS." (The Previous Method); "We use clumpfind (cite: williams1994) to search for emission line sources in the S/N cube." (The Previous Method)
   - software: CASA 4.5.3, uvcontsub, clean, clumpfind
   - parameter: clumpfind threshold 'low' >= 4.5; selection S/N > 6.0 sigma and above the maximum negative S/N in each SPW  
  > "We search for sources with a threshold value “low” of clumpfind of $\geq$ 4.5." (The Previous Method)
   - assumption: Sources are point-like so only spectral smoothing is applied  
  > "We do not consider spatial smoothing since high-$z$ emitters should be observed as point sources." (Footnote 7)
   - fitting: _not stated_
   - validation: Visual check for non-Gaussian features in the smoothed cube  
  > "Additionally, we visually check the non-Gaussian feature in the smoothed datacube." (The Previous Method)
2. **Build blank mock mosaics with pure Gaussian noise**: Replace the visibility noise by Gaussian noise with the measured RMS and mean, apply Hanning smoothing, multiply RMS by sqrt(3), per field, concatenate fields into the mosaic, and make dirty cubes with TCLEAN  
  > "We replace the tables of both the real and imaginary parts using a `casa` command TB.PUTCOL and multiply the RMS values by $\sqrt{3}$ since the smoothing process reduces the values by a factor of $\sqrt{3}$." (The Mock Observations, Replaced Data); "We perform this process for each field, and then concatenate the elemental fields to reproduce the mosaic field." (The Mock Observations, Replaced Data)
   - software: CASA 4.5.3, tb.putcol, tclean, concat
   - parameter: 25 mock mosaic data for 4 SPWs (replaced-data section) and 320 single-pointing data for the non-Gaussian test; 100 mock mosaics used in the Results  
  > "We generate 25 mock mosaic data for 4 SPWs to check the effect of statistical fluctuation." (The Mock Observations, Replaced Data); "Additionally, we prepare 320 single-pointing data to examine the non-Gaussian effect." (The Mock Observations, Replaced Data)
   - assumption: Noise is Gaussian in the mock data; flagging is preserved by replacement  
  > "Note that the replacement process can reproduce the flagging information without further treatment." (The Mock Observations, Replaced Data)
   - fitting: _not stated_
   - validation: Pixel distribution of the original data closely follows a Gaussian profile  
  > "as the pixel distribution of the original data closely aligns with a Gaussian profile" (The Mock Observations, Replaced Data)
3. **Test non-Gaussian noise and TDM vs FDM clump properties**: Compare pixel S/N distributions of real vs replaced-mock single-field cubes smoothed over 12 channels; compare clump FWHM distributions between simobserve TDM and FDM cubes  
  > "The maximum and minimum SN values extend $\pm$ 4–6$~\sigma$ for both real and mock data, and there is no statistical difference between them." (Results, Non-Gaussian effect); "The peaks of the distributions are 1.65 and 2.38 for the FDM and TDM case, respectively." (Results, TDM and FDM)
   - software: CASA 4.5.3, simobserve
   - parameter: 12-channel spectral smoothing; FDM binned from 1.129 MHz to 16.935 MHz to match TDM; velocity resolution 36 km/s; 4.5 min per field  
  > "The FDM observation is binned in frequency resolution from 1.129 MHz to 16.935 MHz to achieve a comparable frequency resolution to TDM data." (Spectral Smoothing Process); "we choose the same observing time of 4.5 min and noise value for each field" (The Mock Observations, Simulated Data)
   - assumption: Known sources masked in the real data to avoid confusion  
  > "The positions of the known sources in the real data are masked to avoid confusion by real sources." (Results, Non-Gaussian effect)
   - fitting: _not stated_
   - validation: Overdensities in replaced data noted as a caution; QA3 check  
  > "one should remain cautious of any potential instrumental effects that cause this noise tendency." (Results, Non-Gaussian effect)
4. **Inject artificial line sources in the visibility plane**: Define Gaussian-profile sources per channel, build with cl.addcomponent, Fourier transform with ft, copy model into corrected data via uvsub reverse=True, then image  
  > "We prepare a source model with `cl.addcomponent` and Fourier-transform the model using `ft`." (The Mock Observations, Artificial Sources); "Then we use `uvsub` with a parameter reverse=True since the command is usually to subtract the model in UV-plane." (The Mock Observations, Artificial Sources)
   - software: CASA 4.5.3, cl.addcomponent, ft, uvsub
   - parameter: Peak S/N 2.0-7.0 in 0.5 steps (11), FWHM 36-396 km/s in 36 km/s steps (11), 121 parameter sets, 84 positions, 100 repeats, 1,016,400 sources  
  > "Therefore, we inject artificial sources with 121 parameter sets of the artificial source." (The Mock Observations, Source Injection); "Then 84 positions in total." (The Mock Observations, Source Injection); "To evaluate the statistical error, we repeat the same process 100 times with different fields." (The Mock Observations, Source Injection)
   - assumption: Mean [C II] redshift z = 6.2 for flux to luminosity conversion  
  > "assuming the average \[C ii\] redshift to be $z = 6.2$." (The Mock Observations, Source Injection)
   - assumption: Flat Lambda-CDM with Omega_M = 0.3, Omega_Lambda = 0.7, h = 0.7  
  > "we adopt the standard $\Lambda$-CDM cosmology with a matter density $\Omega_{\rm M} = 0.3$, a cosmological constant $\Omega_{\rm \Lambda} = 0.7$, and a Hubble constant $h = 0.7$" (Introduction)
   - fitting: _not stated_
   - validation: simobserve and cl.addcomponent injection results are identical  
  > "Note that the results using `simobserve` and `cl.addcomponent` are identical." (The Mock Observations, Artificial Sources)
5. **Derive contamination rate Q and completeness C**: Run clumpfind on smoothed S/N cubes of blank mocks (N_mock), real data (N_real) and injected cubes (N_out vs N_inj); Q = N_mock/N_real and C = N_out/N_inj as functions of (peak S/N, FWHM); fit error functions and classify into Categories I-III  
  > "are the cumulative number of clumps in the real and the blank mock field without injected sources, respectively, as a function of $x$." (The Detection Methods, Detection Classes); "We calculate the value of completeness $C(x)$ by injecting an artificial source and checking if the source is detected by the source-extracting process." (The Detection Methods, Detection Classes)
   - software: clumpfind
   - parameter: x = (peak S/N, FWHM); Q and C fitted with error functions with parameters a1, b1, a2, b2 per FWHM  
  > "The results of $Q(x)$ and $C(x)$ can be approximated with the error function (e.g., (cite: hatsukade2016)):" (The Detection Methods, Detection Classes)
   - assumption: Region considered where N_mock <= N_real and N_real > 0  
  > "We consider the region where $N_{\rm mock} \leq N_{\rm real}$ and $N_{\rm real} > 0$" (The Detection Methods, Detection Classes)
   - fitting: Error-function fit of Q(x) and C(x); sampler, priors, likelihood not stated  
  > "The results of $Q(x)$ and $C(x)$ can be approximated with the error function (e.g., (cite: hatsukade2016)):" (The Detection Methods, Detection Classes)
   - validation: Detected ADF22 candidates fall at the boundary between Category II and III, consistent with non-detection in Cycle 5  
  > "According to our analysis, the detected sources are at the boundary between Category II and III, meaning the detections are likely affected by noise contamination." (Results, The detectability)
6. **Reconstruct the [C II] luminosity function with contamination and completeness corrections**: Correct detected numbers N_cor = N_det (1 - Q)/C per (FWHM, peak flux) set, weight by an assumed luminosity-FWHM distribution, divide by weighted effective survey volume; assume a high-z double power law with amplitude phi*(z) = phi*0 (1+z)^gamma  
  > "N_{\rm cor} = N_{\rm det} (1 - Q)/C." (The LF Reconstruction); "we make the simplest assumption and define the shape of the high-$z$ LF as a double power-law with the same parameters except for the amplitude." (The LF Reconstruction)
   - parameter: Survey volume of the unsmoothed cube 2200 Mpc^-3 (sic), typically 120 channels; gamma < -0.3 satisfies the S12 and H19 constraints  
  > "Note that the survey volume of the unsmoothed datacube is 2200 Mpc$^{-3}$ and the typical number of channels of the datacube is 120." (The LF Reconstruction); "$\gamma < -0.3$ satisfies the constraint from S12 and H19" (The LF Reconstruction)
   - assumption: Line widths follow the observed L[CII]-FWHM correlation; local LF shape applied at high z  
  > "The latter implies the Tully-Fisher relation (cite: kohandel2019)." (The LF Reconstruction)
   - fitting: _not stated_
   - validation: Corrected detection number for Category II clumps is ~0, consistent with the non-detection of [C II] emitters  
  > "Therefore, the corrected detection number is $\sim$ 0, which is consistent with the result of non-detection of \[C ii\] emitters." (Results, The detectability)
7. **Test the LF reconstruction on a mock input LF and derive SFRD limits**: Draw 1000 luminosities from a Schechter input LF, assign FWHM from the L-FWHM correlation, convert to peak S/N with RMS 0.8 mJy/beam at 260 GHz and z = 6.2, apply output/input ratios and completeness over 100 realizations; convert the L[CII] upper limit to SFR with De Looze relations  
  > "We generate 1000 luminosity values (sources) obeying the distribution and assign the input FWHM values from the observed correlation between $L_{\rm [CII]}$-FWHM (cite: kohandel2019)." (Preparation for Abundant Detection); "We repeat the process for 100 realizations and calculate the variance." (Preparation for Abundant Detection)
   - software: CASA 4.5.3
   - parameter: Single Gaussian fit of output lines; typical RMS 0.8 mJy/beam; observed frequency 260 GHz; mean z = 6.2  
  > "We fit the output line emission, assuming a single Gaussian profile, and obtain the peak flux and FWHM." (Preparation for Abundant Detection); "by dividing the typical RMS value of 0.8 mJy beam$^{-1}$." (Preparation for Abundant Detection)
   - assumption: All sources in the datacube are [C II] emitters and no other lines are detected  
  > "For simplicity, we assume that all the sources in the datacube are \[C ii\] emitters and no other emission lines are detected." (Preparation for Abundant Detection)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.5.3: all data analysis, imaging, simulation and visibility manipulation  
  > "The data are analyzed with the Common Astronomy Software Application (`casa`) ver. 4.5.3 (cite: casa2022)." (Introduction)
- **simobserve** : generating TDM and FDM single-pointing mock observations  
  > "By using `simobserve` in `casa`, we compare the difference between Time Division Mode (TDM) and Frequency Division Mode (FDM) observation." (The Mock Observations)
- **tb.putcol** : replacing visibility columns with Gaussian noise  
  > "We replace the tables of both the real and imaginary parts using a `casa` command TB.PUTCOL" (The Mock Observations, Replaced Data)
- **tclean** : imaging mock visibilities into dirty cubes  
  > "The generated visibility data are converted into the ’dirty’ image cube using TCLEAN." (The Mock Observations, Replaced Data)
- **uvcontsub / clean** : continuum subtraction and dirty cube creation for the real data  
  > "We make ’dirty’ continuum-subtracted datacubes using uvcontsub and clean." (Original Data, Cycle-2 data)
- **cl.addcomponent, ft, uvsub** : injecting artificial line sources in the UV-plane  
  > "We thus inject artificial sources to the UV-plane using `cl.addcomponent`." (The Mock Observations, Artificial Sources)
- **clumpfind** : searching S/N cubes for emission-line clumps  
  > "We then normalize the frequency data slice with the RMS values and execute clumpfind (cite: williams1994)." (The Detection Methods, Detection Classes)
- **immoment** : zeroth moment maps for cross-checking the detections  
  > "using immoment and checked spectral features by binning" (Cross-Check of the Detection and Non-Detection)
- **imfit** : checking positions and continuum flux of ADF22.4 between cycles  
  > "we checked the consistency between the positions and continuum flux densities using imfit." (Cross-Check of the Detection and Non-Detection)
- **analysisUtils (aU.plotDelayUpdates)** : checking phase tracking offsets per field for the QA3 investigation  
  > "found no missing directions using the function aU.plotDelayUpdates." (Technical Problems)
- **ALMA pipeline** : re-running the Cycle 2 calibration with an updated version  
  > "re-run the pipeline with a more updated (and reliable) version." (Technical Problems)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| False detections per datacube above 6 sigma (100 blank mock mosaics, previous source-finding method) | 0.43 | 0.67 | per datacube | 5 | Using 100 blank mock-mosaic datasets, we show 0.43 $\pm$ 0.67 false detections per datacube with the previous source-finding method. |
| Width of TDM noise clumps relative to FDM | up to 3 times wider | peak S/N within ~10% | dimensionless | 3 | the line widths of the clumps become up to $3\times$ wider for TDM observations. |
| Contamination inflection point a1 vs FWHM = 2,4,...,22 channels | 6.50, 6.42, 6.50, 6.50, 6.50, 6.50, 6.18, 5.87, 5.67, 5.54, 4.94 | not stated | sigma | 5 | 6.50 / 6.42 / 6.50 / 6.50 / 6.50 / 6.50 / 6.18 / 5.87 / 5.67 / 5.54 / 4.94 |
| Completeness inflection point a2 vs FWHM = 2,4,...,22 channels | 4.71, 3.61, 3.03, 2.96, 2.40, 2.15, 2.16, 1.98, 1.00, 2.35, 1.71 | not stated | sigma | 5 | 4.71 / 3.61 / 3.03 / 2.96 / 2.40 / 2.15 / 2.16 / 1.98 / 1.00 / 2.35 / 1.71 |
| Required correction to the raw [C II] number counts | over an order of magnitude at >= 5e8 Lsun | not stated | dimensionless | 7 | significant correction to the ’raw’ number counts is required, by over an order of magnitude at $\geq$ 5 $\times 10^8$ L$_\odot$. |
| Upper limits on SFRD[CII] at z = 6.2 (metal-poor dwarf and starburst relations) | <0.02 and <0.04 | not stated | Msun/yr/Mpc^3 | 7 | The derived upper limits of the first SFRD$_{\rm [C\,II]}$ become $<$ 0.02 and 0.04 M$_\odot$ yr$^{-1}$ Mpc$^{-3}$ with the correlations for metal-poor local dwarfs and starbursts, respectively. |
| Effective survey area and volume for [C II] in ADF22 | about 29 comoving Mpc^2; ~2.2e3 comoving Mpc^3 at z = 6.2 | not stated | comoving Mpc^2 and Mpc^3 | 0 | The effective survey area for \[C ii\] corresponds to about 29 comoving Mpc$^2$ and the survey volume is $\sim$ 2.2 $\times$ $10^3$ comoving Mpc$^3$ at $z$ = $6.2$. |
| Evolution index of the LF amplitude phi*(z) = phi*0 (1+z)^gamma allowed by constraints | gamma < -0.3 | not stated | dimensionless | 6 | $\gamma < -0.3$ satisfies the constraint from S12 and H19 |

## Qualitative findings

- Non-Gaussian noise is negligible for the ADF22 datacube  
  > "confirming that the effect of non-Gaussian noise is negligible for the ADF22 datacube." (abstract)
- The earlier contamination rate was underestimated because only 4 real datacubes were used  
  > "We argue that the underestimation of the contamination rate in the previous work is caused by the smaller number of datacubes, using only 4 real ADF22 datacubes." (abstract)
- No technical problem was found in the Cycle 2 data by the QA3 process  
  > "Additionally, the conclusion of the quality assurance process, QA3, carried out by the ALMA observatory staff, stated that no technical issues were found." (Technical Problems)

## Claim tuples

- H: Non-Gaussian noise caused the false [C II] detections | E: Compare pixel distributions of real vs Gaussian-replaced mock single-field cubes smoothed by 12 channels (320 fields) | R: S/N extremes extend +-4-6 sigma for both with no statistical difference | F: Non-Gaussian noise does not affect the false detection | **supported**
- H: Statistical fluctuation in the large correlated mosaic could produce >6 sigma clumps | E: Clump search in 100 blank mock mosaics with the previous method | R: 0.43 +- 0.67 detected clumps per datacube | F: The false detections are explained by statistical fluctuation with correlated pixels and smoothing | **supported**
- H: TDM correlation broadens noise clumps compared with FDM | E: simobserve TDM and FDM single-pointing mocks, clump FWHM distributions | R: FDM and TDM FWHM distribution peaks 1.65 and 2.38; TDM clumps up to 3x wider | F: Noise clumps in TDM data have larger velocity widths | **supported**
- H: A technical problem in the Cycle 2 observations caused the false detections | E: Inspection of logs, scan-by-scan data, pipeline re-run, pointing offsets, QA3 | R: No technical issues found | F: False high-S/N detections are unavoidable given clump-like structure in large TDM cubes | **supported**
- H: The previously detected candidates are reliable detections | E: Classify real clumps in the peak S/N-FWHM plane with Q and C fits | R: Candidates lie at the Category II/III boundary; corrected number ~0 | F: Previously detected candidates are unreliable | **supported**
- H: Raw number counts from blind line surveys need correcting to recover the LF | E: Mock LF input/output test with Q and C | R: Correction of up to an order of magnitude at >= 5e8 Lsun | F: The reconstruction method can be applied to future blind line surveys | **partially**

## Reasoning

- Why this data: Follow-up of the ADF22 Cycle 2 line search candidates that were not confirmed in Cycle 5  
  > "Nonetheless, the follow-up observations could not confirm the presence of line emitters at the same frequency (cite: hayatsu2019)." (Introduction)
- Why this method: Injection in the visibility plane chosen for realism  
  > "We have decided to inject sources in the visibility plane to make it as realistic as possible." (The Mock Observations, Artificial Sources)
- Alternative: Adding convolved line emitters to the image cube (ia.convolve2d) or using simobserve inbright; the latter cannot inject into real or replaced data  
  > "A simple way is to generate convolved line emitters and add them to the image datacube." (The Mock Observations, Artificial Sources); "In this case, injection to real/replaced datacube is impossible." (The Mock Observations, Artificial Sources)
- Alternative: Capak et al. 2015 and ASPECS LF estimates not used as constraints  
  > "We do not consider the estimation from (cite: capak2015) at $z$ = $5$–$6$." (The LF Reconstruction)
- How they decided it was enough: _not stated_
- Limitation (authors): Simulated mock data do not necessarily reproduce real observation properties  
  > "In this case, the dataset does not necessarily reproduce the properties of real observations." (The Mock Observations)
- Limitation (authors): clumpfind cannot identify low-S/N clumps so a Gaussianity fit test was not done  
  > "it is important to note that the clumpfind method is not capable of identifying clumps with low SN ratios; therefore, we did not perform this particular test." (Results, Statistical Fluctuation)
- Limitation (authors): Observational constraints at high z are limited, so the LF shape is assumed  
  > "Owing to the limitation of observational constraints at high-$z$, we make the simplest assumption" (The LF Reconstruction)
- Limitation (authors): Overdensities of clumps were found in replaced data after QA3, so instrumental effects remain possible  
  > "one should remain cautious of any potential instrumental effects that cause this noise tendency." (Results, Non-Gaussian effect)
- Caveat (inferred, ours): Mock-mosaic counts are inconsistent (25 vs 100) and the weighting table for the LF is not shown, so the final LF cannot be checked.
- Caveat (inferred, ours): No actual reconstructed LF values are tabulated despite the title; the LF test uses a Schechter input rather than the data.
- Caveat (inferred, ours): Assumed double-power-law shape and L-FWHM relation from local and literature samples may not hold at z~6.
- Caveat (inferred, ours): Noise replacement may not capture baseline-dependent non-Gaussianity.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Scripts and parameters for noise replacement, injection and clumpfind runs
- Missing: Weighting table and LF binning
- Missing: Explicit statement that the data are public or archive product versions
- Missing: Final numeric LF
- Data volume (inferred): Roughly 100-300 GB raw for the nine Cycle 2 execution blocks and the four ALMA projects, plus very large compute for ~1e6 injections and 100 mock mosaics
- Score (inferred): 2/5, The data come from ALMA projects with archive links, but key parameters (imaging settings, clumpfind settings, weighting table, scripts) and the final LF numbers are not published, so the full pipeline cannot be rebuilt from the paper.
- Rediscovery candidate: no, The recipe is incomplete (weighting, clumpfind and imaging parameters missing) and the main results are not tabulated as a final LF, although Q/C parameters are numeric.

## Links

- Method: Hayatsu et al. 2017, PASJ, 69, 45 (cite: hayatsu2017) (Original blind line search method and candidate detection)
- Method: Williams, de Geus & Blitz 1994 (cite: williams1994) (clumpfind algorithm)
- Method: Hatsukade et al. 2016 (cite: hatsukade2016) (Error-function form for Q and C and spurious-source handling)
- Method: Aravena et al. 2016 (cite: aravena2016) (Fidelity definition P(x) = 1 - Q(x))
- Companion: Umehata et al. 2017 (cite: umehata2017) (ADF22 Cycle 2 survey and data description)
- Companion: Hayatsu et al. 2019 (cite: hayatsu2019) (Cycle 5 follow-up non-detections and LF upper limit)
- Companion: Gonzalez-Lopez et al. 2017 (cite: gonzalez2017) (High-sigma pixels from statistical fluctuations in large ALMA datasets)
- Related: ADF22
- Related: ALESS
- Related: ASPECS

## Checks

```json
{
 "quotes": 141,
 "quotes_ok": 141,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 116,
  "stated": 88,
  "rate": 0.759
 },
 "evidence_ok": true
}
```

# First Results from ALPPS: A Sub-Alfvénic Streamer in SVS 13A

`2025ApJ...992L..31C` | The Astrophysical Journal Letters 2025 | first author: Cortés, P. C. | arXiv: 2509.21701 | DOI: 10.3847/2041-8213/ae0c04

Card schema 1.0 | model gpt-6.1-sol | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Are dust grains magnetically aligned, and does the magnetic field guide the infalling streamer onto the SVS13A circumbinary disk?  
  > "To understand if the polarized dust emission obtained by ALMA corresponds to magnetically aligned dust grains, we compare the orientations of the total intensity emission and the C$^{18}$O velocity field gradients with respect to the inferred magnetic field orientation." (Interpreting the polarized dust emission); "we need to compare the turbulent energy against the magnetic energy, as the system is already assumed to be gravitationally dominated." (A sub-Alfvénic Streamer)
- Target **SVS13A**: coordinates _not stated_; z/distance d = 300 pc  
  > "SVS13A is located in the Perseus region at a distance of $d= 300$ pc (cite: Ortiz-Leon2018)" (INTRODUCTION); distance from (cite: Ortiz-Leon2018)  
  > "SVS13A is located in the Perseus region at a distance of $d= 300$ pc (cite: Ortiz-Leon2018)" (INTRODUCTION)

## Data provenance

- ALMA projects: 2017.1.00053.S, 2021.1.00418.S, 2022.1.00479.S
- bands: Band 7; effective wavelength 0.88 mm  
  > "| 7 | 334.5 | 976.562 | 336.5 | 976.562 | 345.8 | 244.141 | 348.5 | 976.562 | 0.35 | 0.27 | -26.5 |" (Table 1); "The observations were obtained at an effective wavelength of 0.88 mm." (OBSERVATIONS)
- frequencies and spectral setup: Full-polarization FDM; SPW centers 334.5, 336.5, 345.8, 348.5 GHz; channel widths 976.562, 976.562, 244.141, 976.562 kHz  
  > "the correlator was configured to yield full polarization cross correlations ($XX, XY, YX,$ and $YY$) using the Frequency Division Mode (FDM)" (OBSERVATIONS); "| 7 | 334.5 | 976.562 | 336.5 | 976.562 | 345.8 | 244.141 | 348.5 | 976.562 | 0.35 | 0.27 | -26.5 |" (Table 1); "For each spectral window (e.g., Spw 1), the center frequency is indicated in GHz, along with the channel width in kHz" (Table 1)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: 2021.1.00418.S: C43-4; 2017.1.00053.S: C43-5; 2022.1.00479.S: C43-7  
  > "from August 21$^{\mathrm{st}}$ 2022 to September 14$^{\mathrm{th}}$ 2022 in configuration C43-4" (OBSERVATIONS); "project 2017.1.00053.S executed from December 17$^{\mathrm{th}}$ 2017 and September 29$^{\mathrm{th}}$ 2018 in configuration C43-5" (OBSERVATIONS); "project 2022.1.00479.S observed between June 10th 2023 and June 23rd 2023 in configuration C43-7" (OBSERVATIONS)
- baselines: C43-4: 15–1301 m; C43-5: 43–1400 m; C43-7: 64–6300 m  
  > "in configuration C43-4 providing baseline lengths from 15 m to 1301 m" (OBSERVATIONS); "in configuration C43-5 providing baselines between 43 m and 1400 m" (OBSERVATIONS); "in configuration C43-7 providing baselines between 64 m and 6300 m" (OBSERVATIONS)
- angular resolution: Continuum ~0.3 arcsec; C17O(3–2) ~0.3 arcsec; C18O(2–1) ~0.2 arcsec; DCN(3–2) ~0.1 arcsec  
  > "The dataset includes full-Stokes dust continuum observations at $\sim0.3\ensuremath{''}$ and 870 $\mu$m" (abstract); "molecular line emission from C$^{17}$O$(J=3 \rightarrow 2)$ at $\sim0.3\ensuremath{''}$, C$^{18}$O$(J=2 \rightarrow 1)$ at $\sim0.2\ensuremath{''}$, and DCN$(J=3 \rightarrow 2)$ at $\sim0.1\ensuremath{''}$ angular resolution." (abstract)
- max recoverable scale: _not stated_
- sensitivity: Self-calibrated continuum: rms = 200 μJy beam−1, robust = 0.5  
  > "$\sigma_{\mathrm{rms}} = 200\,\, \mu\mathrm{Jy\,beam}^{-1}$ with robust=0.5" (OBSERVATIONS)
- time on source: _not stated_
- observing dates: 2021.1.00418.S: August 21–September 14 2022; 2017.1.00053.S: December 17 2017 and September 29 2018; 2022.1.00479.S: June 10–23 2023  
  > "from August 21$^{\mathrm{st}}$ 2022 to September 14$^{\mathrm{th}}$ 2022" (OBSERVATIONS); "project 2017.1.00053.S executed from December 17$^{\mathrm{th}}$ 2017 and September 29$^{\mathrm{th}}$ 2018" (OBSERVATIONS); "project 2022.1.00479.S observed between June 10th 2023 and June 23rd 2023" (OBSERVATIONS)
- pi or archival as stated: _not stated_
- Line: C17O J=3 → 2 (not stated)
- Line: C18O J=2 → 1 (not stated)
- Line: DCN J=3 → 2 (not stated)
- Line: 12CO J=3 → 2 (not stated)
- Other facility **NOEMA**: Earlier streamer detection and DCN hyperfine constraints  
  > "(cite: Hsieh2024), fitted the NOEMA DCN hyperfine structure with a multi-Gaussian model, which confirmed optically thin emission." (Molecular emission)
- Other facility **JCMT/POL-2**: Larger-scale magnetic-field context  
  > "At larger scales, JCMT/POL-2 polarimetry indicates a smooth and ordered magnetic field across the SVS13 region (cite: Doi2020)" (On the origins of the sub-Alfvénic streamer in SVS13A)
- External data: SVS13A distance: 300 pc  
  > "SVS13A is located in the Perseus region at a distance of $d= 300$ pc (cite: Ortiz-Leon2018)" (INTRODUCTION) [from (cite: Ortiz-Leon2018)]
- External data: VLA 4A systemic velocity: 7.36 km s−1  
  > "the systemic velocity of the VLA 4A protostellar core is $v_{\mathrm{lsr}} = 7.36$   km s$^{-1}$  (cite: Diaz-Rodriguez2022)." (C17O (J=3→2)) [from (cite: Diaz-Rodriguez2022)]
- External data: Streamer temperature: Ts ~35–45 K  
  > "By using the streamer temperature estimate of $T_{\mathrm{s}} \sim 35-45$ K (cite: Hsieh2024)" (Molecular emission) [from (cite: Hsieh2024)]
- External data: NOEMA DCN hyperfine fit confirms optically thin emission  
  > "(cite: Hsieh2024), fitted the NOEMA DCN hyperfine structure with a multi-Gaussian model, which confirmed optically thin emission." (Molecular emission) [from (cite: Hsieh2024)]
- External data: DCN(3–2) critical density ~6×10^6 cm−3 at T ~40 K, adopted as gas number density  
  > "Assuming the critical density from DCN$(J=3 \rightarrow 2)$, or $n_{crit} \sim 6\times10^{6}$ cm$^{-3}$, as the gas number density when considering $T \sim 40$ K for the streamer (cite: Hsieh2023)" (A sub-Alfvénic Streamer) [from (cite: Hsieh2023)]
- External data: Factor-of-3 critical-density uncertainty  
  > "This absence can have an effect on the uncertainty as large as a factor of 3 (cite: Shirley2015), which we use here." (A sub-Alfvénic Streamer) [from (cite: Shirley2015)]
- External data: Circumbinary-disk nH2 ~10^9 cm−3  
  > "using a $n_{\mathrm{H_{2}}} \sim 10^{9}$ cm$^{-3}$ estimate for the circumbinary disk (cite: Diaz-Rodriguez2022)" (Mechanical Alignment) [from (cite: Diaz-Rodriguez2022)]
- External data: 500 μG conservative field assumption extrapolated from Zeeman values  
  > "a conservative assumption for the field strength of 500 $\mu$G obtained by extrapolating from Zeeman values (cite: Crutcher2019)" (Mechanical Alignment) [from (cite: Crutcher2019)]
- External data: VLA 4a/VLA 4b flux ratio wf = 0.08 for the radiation model  
  > "$w_{f} = 0.08$ is the ratio between the VLA 4a and VLA 4b fluxes (cite: Diaz-Rodriguez2022)" (Radiative Alignment) [from (cite: Diaz-Rodriguez2022)]
- External data: 380 GHz fluxes: VLA 4B 110 ± 11 mJy; VLA 4A 83 ± 9 mJy; projected separation 90 au  
  > "with a resolved flux of $110 \pm 11$ mJy with respect to $83 \pm 9$ mJy from VLA 4A at 380 GHz" (Radiative Alignment); "a projected distance of 90 au between the stars (cite: Diaz-Rodriguez2022)" (Radiative Alignment) [from (cite: Diaz-Rodriguez2022)]
- External data: Resolved disk minor axes slightly aligned with the observed polarization position angle  
  > "the higher resolution observations of (cite: Diaz-Rodriguez2022) put the VLA 4A and 4B disks with their minor axes slightly aligned to the polarization position angle that we see" (Self-Scattering) [from (cite: Diaz-Rodriguez2022)]
- External data: Smooth, ordered larger-scale SVS13 magnetic field  
  > "At larger scales, JCMT/POL-2 polarimetry indicates a smooth and ordered magnetic field across the SVS13 region (cite: Doi2020)" (On the origins of the sub-Alfvénic streamer in SVS13A) [from (cite: Doi2020)]
- External data: Predominantly transonic to supersonic envelope ammonia motions  
  > "ammonia kinematics point to predominantly transonic to supersonic motions (cite: Dhabal2019)" (On the origins of the sub-Alfvénic streamer in SVS13A) [from (cite: Dhabal2019)]
- External data: Expected Band 7 polarization-position-angle error <2 degrees within the primary beam covering the streamer  
  > "the polarization position angle expected error in ALMA’s Band 7, within the primary beam area covering the streamer, is approximately $< 2^{\circ}$ (cite: Hull2020)." (The effect of Using a Smaller Moving Window) [from (cite: Hull2020)]
- Simulation/model as data: Comparison with gravo-magneto sheetlets in (cite: Tu2024)  
  > "Recent simulations by (cite: Tu2024) introduce “gravo-magneto sheetlets” as anisotropic inflow structures that bridge the envelope and disk, resembling observed streamers." (On the origins of the sub-Alfvénic streamer in SVS13A); "While our measured plasma-$\beta=0.7$[^2] differs from the values obtained in the (cite: Tu2024) models" (On the origins of the sub-Alfvénic streamer in SVS13A)
- Simulation/model as data: Q = 0.5 simulation-derived magnetic-field correction  
  > "$Q=0.5$ is a correction factor derived from simulations (cite: Crutcher2004; Liu2022)" (A sub-Alfvénic Streamer)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: 5.4 for calibration; 6.5 for imaging; DCN calibrated and imaged with 6.4.12  
  > "For calibration and imaging, we used CASA versions 5.4 and 6.5, respectively (cite: CASA2022)." (OBSERVATIONS); "The DCN$(J=3\rightarrow2)$ data were obtained from project 2022.1.00479.S where the visibilities were calibrated and imaged using CASA 6.4.12." (OBSERVATIONS)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Iterative continuum phase self-calibration; final solution interval 30 seconds; solutions applied to molecular lines  
  > "we later iteratively self-calibrated the phase of these data using a final solution interval of 30 seconds" (OBSERVATIONS); "These solutions were then applied to all of the molecular line transitions presented here before imaging." (OBSERVATIONS)

### Imaging

- task: CASA tclean  
  > "The Stokes parameters were imaged using the CASA task *tclean*" (OBSERVATIONS)
- deconvolver: _not stated_
- weighting robust: Explored −2 to 2 in steps of 0.5; main gradient/AM analysis robust=0.5; Mach map robust=1; DCN robust=0.5 and 2  
  > "We covered the baseline weighting parameter space from -2 to 2 in steps of 0.5 to explore what structures are recovered in Stokes space for both line and continuum, except for DCN" (OBSERVATIONS); "For this discussion, all quantities were computed using maps produced with robust=0.5, which gives the best balance between noise, angular resolution, and recovered emission." (Interpreting the polarized dust emission); "The imaging is made with a robust weighting of 0.5 and 2" (OBSERVATIONS)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: Manually extracted from each spectral window; exact channels not stated  
  > "To image the continuum, we manually extracted the line-free channels from each spectral window" (OBSERVATIONS)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: Stokes: ~0.4×0.3 arcsec, PA ~27 degrees; Table 1: 0.35×0.27 arcsec, PA −26.5 degrees; DCN: 0.11×0.08 and 0.2×0.15 arcsec  
  > "an approximate angular resolution of $0.4^{\prime \prime} \times 0.3^{\prime \prime}$, with an approximate position angle of $27^{\circ}$." (OBSERVATIONS); "| 7 | 334.5 | 976.562 | 336.5 | 976.562 | 345.8 | 244.141 | 348.5 | 976.562 | 0.35 | 0.27 | -26.5 |" (Table 1); "resulting in beam sizes of $0.11\ensuremath{''}\times0.08\ensuremath{''}$ ($\sim$30 au) and $0.2\ensuremath{''}\times0.15\ensuremath{''}$ ($\sim$ 45 au), respectively." (OBSERVATIONS)
- final rms: Continuum self-calibration: 200 μJy beam−1 at robust=0.5; polarization-map discussion: 0.25 mJy beam−1  
  > "$\sigma_{\mathrm{rms}} = 200\,\, \mu\mathrm{Jy\,beam}^{-1}$ with robust=0.5" (OBSERVATIONS); "the lowest dust emission contour shown in the map has an S/N of 40 $\sigma$ with $\sigma=0.25$ mJy beam$^{-1}$." (The polarized dust emission)

### Inherited from earlier work

- Pixelwise Stokes Q/U debiasing and 3σ Stokes I cutoff  
  > "we debiased the Stokes $Q$ and $U$ images pixel by pixel, enforcing a 3 $\sigma$ cutoff from Stokes $I$ (total intensity), by following (cite: Vaillancourt2006) and (cite: Hull2015)." (The polarized dust emission) [from (cite: Vaillancourt2006); (cite: Hull2015)]
- Gaussian-derivative gradients  
  > "We compute the gradients by following the approach implemented by (cite: Soler2013), who calculated the column density gradient using Gaussian derivatives." (Comparing with the intensity gradient) [from (cite: Soler2013)]
- Alignment-measure maps and histograms  
  > "we compute maps and histograms of the alignment measure (cite: Gonzales2017; Gonzales2019)" (Interpreting the polarized dust emission) [from (cite: Gonzales2017; Gonzales2019)]
- Moving-average angle-difference maps  
  > "by taking a moving average over the absolute angle difference map following the approach used by (cite: Cortes2024)." (Alignment Measures) [from (cite: Cortes2024)]
- Davis-Chandrasekhar-Fermi field-strength estimation  
  > "estimating the magnetic field strength is required, which we do by applying the Davis-Chandrasekhar-Fermi method (cite: Davis1951; Chandrasekhar1953)" (A sub-Alfvénic Streamer) [from (cite: Davis1951; Chandrasekhar1953)]
- Practical DCF coefficient 9.3  
  > "$\mathrm{B}_{\mathrm{pos}} = 9.3 \sqrt{n_{\mathrm{H}_{2}}} \Delta V / \delta \phi$  $\mu$G" (A sub-Alfvénic Streamer); "$\Delta V$ is the FWHM linewidth obtained from a Gaussian fit to the line data (cite: Crutcher2004)." (A sub-Alfvénic Streamer) [from (cite: Crutcher2004)]
- Thermal and non-thermal velocity contribution v²=2σu²+cs²  
  > "If we consider $v^{2}=2\sigma_{u}^{2} + c_{s}^{2}$ to include both thermal and non-thermal motions (cite: Myers1988)" (A sub-Alfvénic Streamer) [from (cite: Myers1988)]
- Field-dispersion moving window and DCF-based local Alfvén Mach map  
  > "To obtain a map of $\delta_{\phi}$, we followed (cite: Cortes2024), who applied a moving window to the polarization position angle data." (A sub-Alfvénic Streamer); "(cite: Cortes2024) showed that when assuming DCF, the $\mathcal{M}_{\mathrm{A}}$ number can be directly estimated from the field dispersion, yielding a map." (A sub-Alfvénic Streamer) [from (cite: Cortes2024)]
- Q=0.5 and 4/π statistical field correction  
  > "$Q=0.5$ is a correction factor derived from simulations (cite: Crutcher2004; Liu2022)" (A sub-Alfvénic Streamer); "$\frac{4}{\pi}$ corresponds to the statistical average of the magnetic field when considering isotropic 3-dimensional turbulence (cite: Crutcher2004)" (A sub-Alfvénic Streamer) [from (cite: Crutcher2004; Liu2022)]

### Not stated but needed to reproduce (our reading)

- Exact continuum line-free channel selections and effective continuum bandwidth.
- Flux calibrator, adopted flux models, flux-scale uncertainty, and calibration scripts for each project.
- Self-calibration iteration sequence, earlier solution intervals, reference antenna, and solution-combination settings.
- tclean cell size, image dimensions, deconvolver, masks, stopping thresholds, and primary-beam treatment.
- Whether and how continuum subtraction was performed on the spectral-line visibilities.
- Project-to-line assignment and full spectral setup for C18O.
- Exact spectral regridding and smoothing settings resolving the different channel-width descriptions.
- Moment-map integration ranges, masks, and treatment of contaminating emission.
- Map registration, pixel-grid matching, and beam matching before gradient comparisons.
- DCN spectral extraction coordinates, apertures, fit ranges, noise weights, and fitting implementation.
- Exact northeast-streamer mask and circular-dispersion error treatment.
- Gaussian-filter boundary/NaN handling, angle wrapping, and moving-window edge handling.
- Radiation-model source coordinates, Gaussian widths, and resolution of the stated flux-ratio inconsistency.

## Analysis recipe

1. **Produce continuum and spectral-line images**: Extract line-free continuum channels, phase self-calibrate, transfer solutions to lines, and image Stokes parameters and cubes  
  > "To image the continuum, we manually extracted the line-free channels from each spectral window" (OBSERVATIONS); "These solutions were then applied to all of the molecular line transitions presented here before imaging." (OBSERVATIONS); "The Stokes parameters were imaged using the CASA task *tclean*" (OBSERVATIONS)
   - software: CASA, tclean
   - parameter: Final phase self-calibration solution interval: 30 seconds  
  > "we later iteratively self-calibrated the phase of these data using a final solution interval of 30 seconds" (OBSERVATIONS)
   - parameter: General spectral cubes: 1 km s−1 channel width  
  > "The spectral cubes were produced by using a 1 km s$^{-1}$ channel width." (OBSERVATIONS)
   - parameter: DCN follow-up spectral resolution ~0.1 km s−1  
  > "a much higher angular resolution ($\sim 0^{\prime\prime}.1$) and spectral resolution ($\sim 0.1$ km s$^{-1}$)." (Molecular emission)
   - parameter: Bandpass: J0423-0120, J0510+1800, J0238+1636; gain: J0336+3218; instrumental polarization: J0522-3627  
  > "The bandpass was calibrated using J0423-0120, J0510+1800, and J0238+1636." (OBSERVATIONS); "The time-dependent gain and the instrumental polarization terms were calibrated using J0336+3218 and J0522-3627, respectively." (OBSERVATIONS)
   - fitting: _not stated_
   - validation: Explore weighting from −2 to 2 in steps of 0.5 to assess recovered structure  
  > "We covered the baseline weighting parameter space from -2 to 2 in steps of 0.5 to explore what structures are recovered in Stokes space for both line and continuum, except for DCN" (OBSERVATIONS)
2. **Infer polarization and projected magnetic-field morphology**: Debias Q/U pixelwise, apply Stokes I cutoff, and rotate polarization angles by 90 degrees  
  > "we debiased the Stokes $Q$ and $U$ images pixel by pixel, enforcing a 3 $\sigma$ cutoff from Stokes $I$ (total intensity), by following (cite: Vaillancourt2006) and (cite: Hull2015)." (The polarized dust emission); "under the assumption of magnetic alignment of dust grains (i.e., the polarization position angle is rotated by 90$^{\circ}$)." (The polarized dust emission)
   - parameter: 3σ Stokes I cutoff  
  > "enforcing a 3 $\sigma$ cutoff from Stokes $I$ (total intensity)" (The polarized dust emission)
   - assumption: Magnetically aligned dust grains  
  > "under the assumption of magnetic alignment of dust grains" (The polarized dust emission)
   - fitting: _not stated_
   - validation: Check spatial coherence of polarized emission  
  > "the polarized emission varies smoothly and consistently across the region, without abrupt changes or discontinuities" (The polarized dust emission)
3. **Trace the streamer and measure its linewidth**: Inspect channel/moment maps, fit selected DCN spectra, and compare velocity dispersion with sound speed  
  > "For the ALMA data, we fitted a simple Gaussian model to selected positions in the DCN velocity cube" (Molecular emission); "we obtained a streamer sound speed between 0.32–0.36 km s$^{-1}$ ($\sim 0.34$ km s$^{-1}$), which suggests the streamer has subsonic motions." (Molecular emission)
   - parameter: DCN channel maps: 7.55–9.07 km s−1  
  > "shows the DCN channel maps from 7.55 km s$^{-1}$ to 9.07 km s$^{-1}$" (Molecular emission)
   - assumption: Streamer temperature Ts ~35–45 K from (cite: Hsieh2024)  
  > "By using the streamer temperature estimate of $T_{\mathrm{s}} \sim 35-45$ K (cite: Hsieh2024)" (Molecular emission)
   - assumption: C17O single-peaked, without self-absorption, suggests optically thin emission  
  > "The C$^{17}$O emission appears single-peaked through the whole region with no evidence of self-absorption, which suggests optically thin emission." (C17O (J=3→2))
   - fitting: Simple Gaussian fits at selected DCN positions  
  > "For the ALMA data, we fitted a simple Gaussian model to selected positions in the DCN velocity cube" (Molecular emission)
   - validation: Compare streamer morphology among DCN, C18O, C17O and dust, and with prior NOEMA results  
  > "This spiral structure is likely the resolved NOEMA DCN streamer detected by (cite: Hsieh2024)." (Molecular emission); "the overall morphology of the spiral agrees quite well with the structures seen in the continuum and C$^{17}$O emission." (C18O (J=2→1))
4. **Compute intensity and velocity gradients**: Apply Gaussian derivatives to continuum intensity and C18O moment 1  
  > "We compute the gradients by following the approach implemented by (cite: Soler2013), who calculated the column density gradient using Gaussian derivatives." (Comparing with the intensity gradient); "we computed the velocity gradient for the C$^{18}$O velocity field map using the same Gaussian derivative and kernel window" (Comparing with the velocity gradient)
   - software: scipy Gaussian2DKernel
   - parameter: Gaussian kernel σG=8 pixels  
  > "We define the size of the Gaussian kernel as the number of pixels used to sample the beam when imaging the data, which in our case corresponds to $\sigma_{\mathrm{G}}=8$." (Comparing with the intensity gradient)
   - parameter: Circumbinary disk to 3σ continuum cutoff; exclude bridge to VLA 3  
  > "the intensity gradient was calculated over the circumbinary disk up to the 3 $\sigma$ cutoff in continuum emission only (the bridge to the VLA 3 source was excluded)." (Comparing with the intensity gradient)
   - parameter: robust=0.5 maps  
  > "For this discussion, all quantities were computed using maps produced with robust=0.5" (Interpreting the polarized dust emission)
   - fitting: _not stated_
   - validation: Visually compare gradient orientations with field and polarization  
  > "From visual inspection, the inferred magnetic field appears to agree quite well with the intensity gradient throughout the map, while the polarization does not show the same level of agreement." (Comparing with the intensity gradient)
5. **Quantify alignment**: Compute AM=<cos(2Δθ)>, maps and histograms for field versus intensity/velocity gradients  
  > "\mathrm{AM} = \left<\cos{(2\Delta\theta_{\mathrm{1,2}}}) \right>~," (Interpreting the polarized dust emission); "we computed histograms of the absolute angle differences and of the alignment measure (AM) using 10 equally weighted bins for each distribution." (Alignment Measures)
   - parameter: 10 equally weighted histogram bins  
  > "using 10 equally weighted bins for each distribution." (Alignment Measures)
   - parameter: 8-pixel moving-average window  
  > "the moving average window is defined by taking the same window used to calculate the gradient using Gaussian derivatives (8 pixels across) to avoid introducing excessive averaging" (Alignment Measures)
   - parameter: robust=0.5 polarized-emission and velocity-gradient maps  
  > "The histograms were computed considering the total extent of the polarized emission and the velocity gradient maps produced using the *robust* = 0.5 maps." (Alignment Measures)
   - assumption: Compare overlapping emission within the circumbinary disk  
  > "We calculate the AM parameter pixel by pixel over the regions where there is emission overlap, but considering only the extension of the circumbinary disk." (Interpreting the polarized dust emission)
   - fitting: _not stated_
   - validation: AM maps and histograms agree on preferred field–gradient alignment  
  > "Although the histograms also show a population of intermediate values, the preferred orientation is alignment between the inferred magnetic field orientation and the intensity and velocity gradients." (Interpreting the polarized dust emission)
6. **Test radiative alignment**: Model both stars as circular Gaussians; combine radial gradients by a flux-weighted 1/r² vector sum  
  > "The model assumes circular Gaussian profiles for each source at their respective positions, which we used to calculate their gradients." (Radiative Alignment); "we did a weighted vector sum of each of the gradients, considering a $1/r^{2}$ pixel dependence and the flux ratio between VLA 4a and VLA 4b" (Radiative Alignment)
   - parameter: wf=0.08 from (cite: Diaz-Rodriguez2022)  
  > "$w_{f} = 0.08$ is the ratio between the VLA 4a and VLA 4b fluxes (cite: Diaz-Rodriguez2022)" (Radiative Alignment)
   - assumption: Binary system is the radiation-flux source  
  > "we produced a simple model for the flux emission coming from the binary system, which we assumed to be the source of the radiation flux." (Radiative Alignment)
   - fitting: _not stated_
   - validation: Visually compare modeled radiation orientation with polarization angles  
  > "From visual inspection, the polarization position angle appears not to be aligned with the radiation field throughout most of the map, where a bimodal distribution is not apparent." (Radiative Alignment)
7. **Compare magnetic and mechanical alignment times**: Estimate Larmor precession time and compare with Badminton-Birdie mechanical alignment  
  > "the Larmor precession time-scale is $\sim 10$ hours." (Mechanical Alignment); "This suggests that overall alignment by magnetic fields is faster than the Badminton-Birdie mechanical alignment in SVS13A." (Mechanical Alignment)
   - assumption: Strong radiation field permits efficient RAT spin-up  
  > "we can assume a strong radiation field which suggests efficient supra-thermal spin-up of grains by the RAT mechanism is possible." (Mechanical Alignment)
   - assumption: nH2~10^9 cm−3; conservative B=500 μG  
  > "using a $n_{\mathrm{H_{2}}} \sim 10^{9}$ cm$^{-3}$ estimate for the circumbinary disk (cite: Diaz-Rodriguez2022)" (Mechanical Alignment); "a conservative assumption for the field strength of 500 $\mu$G obtained by extrapolating from Zeeman values (cite: Crutcher2019)" (Mechanical Alignment)
   - fitting: _not stated_
   - validation: _not stated_
8. **Estimate streamer magnetic-field strength**: DCF: Bpos=9.3√nH2 ΔV/δφ μG; propagate errors  
  > "$\mathrm{B}_{\mathrm{pos}} = 9.3 \sqrt{n_{\mathrm{H}_{2}}} \Delta V / \delta \phi$  $\mu$G" (A sub-Alfvénic Streamer); "where the uncertainty is calculated using error propagation over equation" (A sub-Alfvénic Streamer)
   - parameter: Northeast streamer above the field bifurcation  
  > "The following analysis only refers to the north-east section of the streamer, over the bifurcation line, where we have established grain alignment by magnetic fields." (A sub-Alfvénic Streamer)
   - parameter: Mean FWHM ΔV=0.6 km s−1; circular standard deviation δφ=12 degrees  
  > "a mean velocity linewidth, $\langle \Delta V \rangle = 0.6 \,{\mbox{km\,s$^{-1}$}}$" (A sub-Alfvénic Streamer); "a field dispersion over the streamer of $\delta_{\phi} = 12^{\circ}$ (calculated as the circular standard deviation)" (A sub-Alfvénic Streamer)
   - parameter: Density uncertainty factor 3; linewidth uncertainty 0.1 km s−1; polarization-angle error 2 degrees  
  > "This absence can have an effect on the uncertainty as large as a factor of 3 (cite: Shirley2015), which we use here." (A sub-Alfvénic Streamer); "We used 0.1 km s$^{-1}$ in the linewidth (coming from the velocity resolution), and a polarization position angle error of $2^{\circ}$ for the ALMA observations" (A sub-Alfvénic Streamer)
   - assumption: Gas number density equals DCN critical density ~6×10^6 cm−3 at T~40 K  
  > "Assuming the critical density from DCN$(J=3 \rightarrow 2)$, or $n_{crit} \sim 6\times10^{6}$ cm$^{-3}$, as the gas number density when considering $T \sim 40$ K for the streamer (cite: Hsieh2023)" (A sub-Alfvénic Streamer)
   - fitting: Linewidth from Gaussian fits to DCN  
  > "For the ALMA data, we fitted a simple Gaussian model to selected positions in the DCN velocity cube" (Molecular emission)
   - validation: _not stated_
9. **Compare kinetic and magnetic energies**: Compute Ek/EB=4πmH2 nH2 v²/Bpos²; cancel volume and propagate errors  
  > "To compare both energies, we take the ratio, which cancels the volume" (A sub-Alfvénic Streamer); "\frac{E_{k}}{E_{B}} = \frac{4\pi m_{\mathrm{H}_{2}}n_{\mathrm{H}_{2}} v^2}{B_{\mathrm{pos}}^{2} }~." (A sub-Alfvénic Streamer); "the uncertainty in the energy ratio was computed using error propagation" (A sub-Alfvénic Streamer)
   - parameter: Channel-corrected σu=0.22 km s−1; cs=0.34 km s−1 at Tgas=40 K  
  > "$\sigma_{u}=\left< \Delta V \right>/2\sqrt{2\log{2}}=0.22 \,{\mbox{km\,s$^{-1}$}}$ is the velocity dispersion along the line-of-sight after removing the channel width" (A sub-Alfvénic Streamer); "$c_{s} = 0.34\, {\mbox{km\,s$^{-1}$}}$ is the sound speed for $T_{gas}$=40 K." (A sub-Alfvénic Streamer)
   - assumption: Constant field over the volume  
  > "where $\mathrm{V}$ is the volume assuming a constant field." (A sub-Alfvénic Streamer)
   - assumption: v²=2σu²+cs²; plane velocity assumed equal to line-of-sight velocity  
  > "If we consider $v^{2}=2\sigma_{u}^{2} + c_{s}^{2}$ to include both thermal and non-thermal motions (cite: Myers1988)" (A sub-Alfvénic Streamer); "the factor of 2 representing the assumption that the velocity on the plane is the same as the line-of-sight" (A sub-Alfvénic Streamer)
   - fitting: _not stated_
   - validation: Interpret ratio as an average and recognize proximity to equipartition  
  > "This estimate yields a single value that should be regarded as an average representation rather than a detailed description of local conditions." (A sub-Alfvénic Streamer)
10. **Map the local Alfvénic Mach number**: Convert moving-window polarization-angle dispersion to MA using the DCF relation  
  > "To obtain a map of $\delta_{\phi}$, we followed (cite: Cortes2024), who applied a moving window to the polarization position angle data." (A sub-Alfvénic Streamer); "\frac{2\sqrt{2\log 2}\,\pi}{4\,Q}\,\delta\phi" (A sub-Alfvénic Streamer)
   - parameter: 1 arcsec moving window; robust=1  
  > "using a moving window of $1^{\prime\prime}$ and a robust value of 1 to recover sufficient emission over the streamer." (A sub-Alfvénic Streamer)
   - parameter: Q=0.5  
  > "$Q=0.5$ is a correction factor derived from simulations (cite: Crutcher2004; Liu2022)" (A sub-Alfvénic Streamer)
   - assumption: Gaussian polarization-angle distribution  
  > "Assuming that the distribution of the polarization position angle is Gaussian" (A sub-Alfvénic Streamer)
   - assumption: Isotropic 3-dimensional turbulence for the 4/π statistical correction  
  > "$\frac{4}{\pi}$ corresponds to the statistical average of the magnetic field when considering isotropic 3-dimensional turbulence (cite: Crutcher2004)" (A sub-Alfvénic Streamer)
   - assumption: Dispersion represents local deviations from the mean field; accuracy depends on DCF  
  > "estimating $\mathcal{M}_{\mathrm{A}}$ directly from the dispersion in the field lines requires that the dispersion represent local deviations from the mean field." (A sub-Alfvénic Streamer); "the estimate of $\mathcal{M}_{\mathrm{A}}$ derived here is as good as DCF itself." (A sub-Alfvénic Streamer)
   - fitting: _not stated_
   - validation: Repeat with 0.5 arcsec window; dispersion error rises from 6 to 10 degrees  
  > "using a moving window of $0^{\prime\prime}.5$ in size" (The effect of Using a Smaller Moving Window); "the associated error almost doubles from $6^{\circ}$ to $10^{\circ}$" (The effect of Using a Smaller Moving Window)

## Software

- **CASA** 5.4; 6.5; 6.4.12: Calibration and imaging; DCN calibration and imaging  
  > "For calibration and imaging, we used CASA versions 5.4 and 6.5, respectively (cite: CASA2022)." (OBSERVATIONS); "The DCN$(J=3\rightarrow2)$ data were obtained from project 2022.1.00479.S where the visibilities were calibrated and imaged using CASA 6.4.12." (OBSERVATIONS)
- **tclean** : Image Stokes parameters  
  > "The Stokes parameters were imaged using the CASA task *tclean*" (OBSERVATIONS)
- **scipy Gaussian2DKernel** : Gaussian filtering that handles not-a-number values  
  > "We implement a version of the Gaussian filter that can handle not-a-number values using the *scipy Gaussian2DKernel* object" (Comparing with the intensity gradient)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Polarization fraction over the region | 0.15% to 30% | not stated | % | 2 | the fractional polarization ranges from 0.15% to 30% |
| Polarization fraction over the binary | 0.15% to ~1% | not stated | % | 2 | Over the binary system, the fractional polarization ranges between 0.15%, marginally close to the ALMA accuracy (cite: Cortes2023), and $\sim 1\%$. |
| DCN streamer extent | 675 | not stated | au | 3 | the DCN streamer matches the spiral seen in the dust emission extending up to $2^{\prime\prime}.25$ or 675 au |
| DCN Gaussian FWHM linewidths | 0.6 to 0.7 | not stated | km s−1 | 3 | obtaining FWHM velocity linewidths between 0.6 km s$^{-1}$ and 0.7 km s$^{-1}$ |
| Mean DCN velocity dispersion before channel correction | 0.25 | not stated | km s−1 | 3 | which yields a mean velocity dispersion of 0.25 km s$^{-1}$ |
| Streamer sound speed | 0.32–0.36 (~0.34) | not stated | km s−1 | 3 | we obtained a streamer sound speed between 0.32–0.36 km s$^{-1}$ ($\sim 0.34$ km s$^{-1}$) |
| Alignment-measure distribution peak | 1 | not stated | dimensionless | 5 | we find that the AM distribution peaks at a value of 1. |
| Estimated Larmor precession timescale | ~10 | not stated | hours | 7 | the Larmor precession time-scale is $\sim 10$ hours. |
| Streamer field circular standard deviation | 12 | not stated | degrees | 8 | a field dispersion over the streamer of $\delta_{\phi} = 12^{\circ}$ (calculated as the circular standard deviation) |
| Plane-of-sky magnetic-field strength Bpos | 1.1 | ± 0.6 | mG | 8 | we obtain $\mathrm{B}_{\mathrm{pos}} = 1.1 \pm 0.6$ mG |
| Channel-corrected line-of-sight velocity dispersion | 0.22 | not stated | km s−1 | 9 | $\sigma_{u}=\left< \Delta V \right>/2\sqrt{2\log{2}}=0.22 \,{\mbox{km\,s$^{-1}$}}$ is the velocity dispersion along the line-of-sight after removing the channel width |
| Kinetic-to-magnetic energy ratio | 0.5 | ± 0.4 | dimensionless | 9 | We obtain $E_{k}/E_{B}=0.5 \pm 0.4$ |
| Plasma beta | 0.7 | not stated | dimensionless | 0 | our measured plasma-$\beta=0.7$ |
| Alfvénic Mach number along significant portions of the streamer | < 1 | not stated | dimensionless | 10 | The resulting map suggests that the gas motions along significant portions of the streamer are sub-Alfvénic ($< 1$) |
| Dispersion-estimate statistical error with 1 arcsec window | ~6 | not stated | degrees | 10 | Using a $1^{\prime\prime}$ moving window yields an error estimate of $\sim 6^{\circ}$ |
| Dispersion-estimate statistical error with 0.5 arcsec window | about 10 | not stated | degrees | 10 | yielding an error of about $10^{\circ}$ when we use a population dispersion estimate of $12^{\circ}$ (cite: Cortes2024). |

## Qualitative findings

- Asymmetric double dust spiral correlated with the molecular streamer and field morphology  
  > "revealing an asymmetric double spiral." (Summary and Conclusions); "The dust spiral is spatially well correlated with the streamer seen in molecular line emission and with the magnetic field morphology." (Summary and Conclusions)
- Magnetic grain alignment favored over most of the circumbinary disk  
  > "We interpret this result as evidence for magnetically aligned dust grains in the SVS13A circumbinary disk." (Are we seeing magnetic fields?)
- Magnetic field may guide infall by constraining motion across field lines  
  > "the field is likely facilitating the inflow of material from the envelope onto the disk by constraining movement across the field lines." (abstract)
- Southwestern gas substructure remains unclassified  
  > "we cannot conclude about its nature or its infalling properties, if any." (A sub-Alfvénic Streamer)

## Claim tuples

- H: The streamer is sub-Alfvénic and magnetically guided. | E: Compare molecular morphology with field orientation; estimate DCF field strength, energy ratio, and local Mach map. | R: Bpos=1.1±0.6 mG; Ek/EB=0.5±0.4; significant streamer portions have MA<1. | F: Magnetic guidance is favored, with marginal energetic separation from equipartition. | **partially**
- H: Magnetic grain alignment explains most polarized dust emission. | E: Compare inferred field and polarization orientations with intensity and velocity gradients using AM maps and histograms. | R: AM distribution peaks at 1; gradients preferentially align with the inferred field. | F: Magnetic alignment is favored across most of the region, with local alternatives remaining possible. | **partially**
- H: The dust spiral is associated with the molecular streamer. | E: Compare continuum morphology with resolved molecular channel and moment maps. | R: DCN matches the dust spiral to 675 au; molecular and dust structures correlate. | F: The asymmetric dust spiral is spatially correlated with the streamer and magnetic field. | **supported**
- H: Radiative alignment is the preferred polarization mechanism. | E: Compare polarization with a two-source, flux-weighted radiation-field model. | R: Polarization is not aligned with the modeled radiation field over most of the map. | F: Radiative alignment is disfavored. | **refuted**

## Reasoning

- Why this data: Use C18O for better velocity sampling than C17O  
  > "the velocity resolution in our data ($\sim 0.9$ km s$^{-1}$) is not sufficient to trace the velocity gradient effectively." (C17O (J=3→2)); "We do this instead by using C$^{18}$O$(J=2\rightarrow1)$ emission" (C17O (J=3→2))
- Why this method: robust=0.5 balances noise, resolution and recovered emission; Gaussian derivatives permit gradient filtering  
  > "For this discussion, all quantities were computed using maps produced with robust=0.5, which gives the best balance between noise, angular resolution, and recovered emission." (Interpreting the polarized dust emission); "the computation of the gradient can be performed by applying the Gaussian derivative as a filter" (Comparing with the intensity gradient)
- Alternative: Self-scattering may contribute over a few binary pixels  
  > "Although self-scattering may be present in SVS13A, its extent is most likely confined to a few pixels over the VLA 4 binary." (Self-Scattering)
- Alternative: Mechanical alignment inconsistent with predominant flow–polarization orthogonality, but possible locally  
  > "the flow direction is predominantly orthogonal to the polarization pattern, which is inconsistent with mechanical alignment." (Mechanical Alignment); "mechanical alignment may play a role locally." (Mechanical Alignment)
- Alternative: Radiative alignment disfavored  
  > "Therefore, we disfavor radiative alignment as the preferred mechanism for the polarized emission that we see in SVS13A." (Radiative Alignment)
- Alternative: 3×3 Sobel kernel considered; Gaussian derivative selected  
  > "one common choice is a $3\times3$ Sobel kernel (cite: Sobel1968)." (Comparing with the intensity gradient); "Using a Gaussian derivative, however, is more convenient" (Comparing with the intensity gradient)
- Alternative: 0.5 arcsec dispersion window reduces spread of high dispersion but increases statistical error  
  > "Although using a small window size decreases the spread of larger dispersion values" (The effect of Using a Smaller Moving Window); "the associated error almost doubles from $6^{\circ}$ to $10^{\circ}$" (The effect of Using a Smaller Moving Window)
- How they decided it was enough: Choose 1 arcsec dispersion window for ~6-degree statistical error while keeping central artificial dispersion away from the streamer  
  > "Using a $1^{\prime\prime}$ moving window yields an error estimate of $\sim 6^{\circ}$, which is reasonable compared with the Band 7 polarization position angle error of $2^{\circ}$" (A sub-Alfvénic Streamer); "the artificially larger dispersion values are confined to the center of the circumbinary disk, away from the streamer." (A sub-Alfvénic Streamer)
- Limitation (authors): High polarization fractions outside the disk may reflect missing Stokes I flux  
  > "The higher values $(> 10\%)$ are seen outside the circumbinary disk and might be the result of missing flux in the total intensity emission" (Polarization Fraction)
- Limitation (authors): C18O may be contaminated by a wide-angle outflow  
  > "The presence of a wide-angle outflow in this source may introduce some kinematic contamination in the C$^{18}$O emission, which is difficult to untangle." (C18O (J=2→1))
- Limitation (authors): DCN critical-density uncertainty dominates because collisional rates are lacking  
  > "The uncertainty in the critical number density is likely the largest factor because of the lack of collisional rates for DCN (cite: Hsieh2024)." (A sub-Alfvénic Streamer)
- Limitation (authors): Energy ratio is an average near equipartition  
  > "the regulating effect of the magnetic field in the infalling flow appears to be marginal, as both quantities are not far from equipartition." (A sub-Alfvénic Streamer); "This estimate yields a single value that should be regarded as an average representation rather than a detailed description of local conditions." (A sub-Alfvénic Streamer)
- Limitation (authors): Large-scale field morphology can inflate local dispersion  
  > "If the mean field is not subtracted, the estimated dispersion might be higher than what local perturbations by the gas might induce." (A sub-Alfvénic Streamer)
- Limitation (authors): Multiple uncorrelated line-of-sight field components invalidate a global Mach interpretation  
  > "If the field has multiple, uncorrelated, components along the line of sight, the $\mathcal{M}_{\mathrm{A}}$ map will not accurately represent the global Alfvén Mach number." (A sub-Alfvénic Streamer)
- Limitation (authors): Connection to the larger-scale envelope is not directly traced  
  > "Although our observations cannot directly trace the connection between the circumbinary disk and the larger-scale envelope" (On the origins of the sub-Alfvénic streamer in SVS13A)
- Limitation (authors): Gradient filtering partially smooths intensity and velocity maps but not polarization  
  > "it will still partially smooth the data because the Gaussian kernel is symmetric, and the beam is not." (Comparing with the intensity gradient); "This technique, however, was not applied to the polarization data" (Comparing with the intensity gradient)
- Caveat (inferred, ours): The radiation-model flux ratio 0.08 is inconsistent with the quoted 83 and 110 mJy fluxes; its intended definition needs clarification.
- Caveat (inferred, ours): Spectral sampling is described as 1 km s−1, ~0.9 km s−1 and ~2 km s−1 for the general/C17O data; exact products need identification.
- Caveat (inferred, ours): The prose and Table 1 give different continuum beams and opposite signs for the position angle.
- Caveat (inferred, ours): The mean 0.6 km s−1 FWHM and channel-corrected 0.22 km s−1 dispersion need an explicit correction calculation.
- Caveat (inferred, ours): Using critical density as actual density is a consequential assumption for Bpos.
- Caveat (inferred, ours): Gradient alignment supports the interpretation but does not independently establish three-dimensional gas motion along the field.
- Caveat (inferred, ours): AM intermediate values are discarded without a numerical significance criterion.
- Caveat (inferred, ours): The local Mach map is derived from field dispersion under DCF assumptions rather than an independent field-strength measurement.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Public availability and exact archive products are not stated.
- Missing: Full imaging and calibration scripts, continuum selections, and per-line spectral processing.
- Missing: Analysis code for debiasing, gradients, AM, circular dispersion, uncertainty propagation and Mach maps.
- Missing: Exact analysis masks, spectral extraction positions, map grids and beam matching.
- Missing: Clarification of the radiation flux ratio, beam position angle, spectral resolution and linewidth correction.
- Data volume (inferred): Cannot estimate from the supplied text; integration times, visibility counts and image dimensions are absent.
- Score (inferred): 6/5, 6/10: project codes, CASA versions, major analysis equations and numerical benchmarks are given; exact imaging, masks, code and several internally inconsistent settings prevent an exact reproduction.
- Rediscovery candidate: no, Main results are numeric, but public availability is not established in the supplied text and the recipe lacks essential selections and implementation details.

## Links

- Method: (cite: CASA2022) (CASA calibration and imaging.)
- Method: (cite: Vaillancourt2006); (cite: Hull2015) (Polarization debiasing.)
- Method: (cite: Soler2013) (Gaussian-derivative gradients.)
- Method: (cite: Gonzales2017; Gonzales2019) (Alignment measure.)
- Method: (cite: Cortes2024) (Moving-window averaging, dispersion errors and DCF-based Mach maps.)
- Method: (cite: Davis1951; Chandrasekhar1953) (DCF magnetic-field estimation.)
- Method: (cite: Crutcher2004; Liu2022) (DCF normalization and simulation-derived field correction.)
- Method: (cite: Myers1988) (Thermal and non-thermal kinetic-energy prescription.)
- Method: (cite: Shirley2015) (Critical-density uncertainty.)
- Method: (cite: Hull2020) (Band 7 polarization-angle accuracy.)
- Method: (cite: Lin2024) (Badminton-Birdie mechanical-alignment alternative.)
- Companion: (cite: Hsieh2024) (Earlier NOEMA streamer identification, temperature estimate and DCN optical-depth constraints.)
- Companion: (cite: Diaz-Rodriguez2022) (Earlier resolved SVS13A disk/spiral observations and adopted systemic velocity, density and stellar flux information.)
- Companion: (cite: Tobin2018) (Earlier dust spiral observations confirmed here.)
- Related: ALMA Perseus Polarization Survey (ALPPS)

## Checks

```json
{
 "quotes": 207,
 "quotes_ok": 207,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 16,
 "numeric_problems": 0,
 "fill": {
  "facts": 152,
  "stated": 119,
  "rate": 0.783
 },
 "evidence_ok": true
}
```

# A Centiparsec-scale Compact Radio Core in the Nearby Galaxy M60

`2024ApJ...960....1L` | The Astrophysical Journal 2024 | first author: Li, Xiaofeng | arXiv: 2311.06126 | DOI: 10.3847/1538-4357/ad0be6

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: agn_and_quasars, nearby_galaxies
- Question: What is the nature of the centi-pc-scale radio core of the low-luminosity AGN in M60 (jet base or ADAF), and does its compactness support a central SMBH; ALMA 350 GHz continuum only supplies flux densities for the radio spectrum  
  > "To investigate the nature of its innermost radio nucleus, data from the Very Long Baseline Array (VLBA) at 4.4 and 7.6 GHz were reduced." (abstract); "This suggests that the observed centi-parsec-scale compact core could be attributed to a nonthermal jet base or an advection-dominated accretion flow (ADAF) with nonthermal electrons." (abstract)
- Target **M60 (NGC 4649)**: coordinates RA=12:43:39.9715, Dec=+11:33:09.688 (RFC radio position)  
  > "the coordinates are RA=12:43:39.9715 and Dec=+11:33:09.688 (with an error of 1.8 mas)" (Radio images of M60); "In this work, we use the weighted average of the two distances, $d = 16.5\pm0.5~$Mpc." (Introduction); z/distance d = 16.5 +/- 0.5 Mpc  
  > "the coordinates are RA=12:43:39.9715 and Dec=+11:33:09.688 (with an error of 1.8 mas)" (Radio images of M60); "In this work, we use the weighted average of the two distances, $d = 16.5\pm0.5~$Mpc." (Introduction); distance from weighted average of TRGB (Lee2017) and SBF (Cantiello2018) distances  
  > "the coordinates are RA=12:43:39.9715 and Dec=+11:33:09.688 (with an error of 1.8 mas)" (Radio images of M60); "In this work, we use the weighted average of the two distances, $d = 16.5\pm0.5~$Mpc." (Introduction)

## Data provenance

- ALMA projects: 2016.1.01135.S, 2017.1.00830.S
- bands: ~350 GHz (ALMA band not named)  
  > "M60 was observed by ALMA at $\sim$350 GHz to study its black hole mass, central parsec gas dynamics, and event horizon detectability by CO lines" (Non-simultaneous radio spectrum)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2017-07-18 and 2017-12-24 (continuum flux measurements)  
  > "$1.7\pm0.2$ mJy on 18 July 2017 and $1.1\pm0.1$ mJy on 24 December 2017" (Non-simultaneous radio spectrum)
- pi or archival as stated: Programs 2016.1.01135.S and 2017.1.00830.S, PI Neil Nagar; reduced by the authors (archival reuse)  
  > "to study its black hole mass, central parsec gas dynamics, and event horizon detectability by CO lines (program code 2016.1.01135.S and 2017.1.00830.S, Principal Investigator: Neil Nagar)" (Non-simultaneous radio spectrum)
- Line: CO not stated (not stated)
- Other facility **VLBA (program BP252AF, VLBA Calibrator Survey 12)**: 4.4 and 7.6 GHz simultaneous 3-min snapshot, the main high-resolution data of the paper  
  > "In the VLBA Calibrator Survey 12 (program code BP252AF, principal investigator: Leonid Petrov), the radio AGN in M60 was observed simultaneously at 4.4 and 7.6 GHz for a duration of 3 min on July 26, 2022." (VLBA observations and data reduction)
- Other facility **VLA (NVAS archive and published data)**: Archival 1.5-43 GHz flux densities for the non-simultaneous radio spectrum  
  > "Most data extracted from the NRAO VLA Archive Survey (cite: Crossley2008)" (Non-simultaneous radio spectrum)
- Other facility **SCUBA**: 150 GHz upper limit from the literature  
  > "one data point was observed by submillimetre common-user bolometer array (SCUBA) at 150 GHz (cite: DiMatteo1999)" (Non-simultaneous radio spectrum)
- Other facility **SMA**: 223 GHz variability detection (Lo2023); noted but not used in the spectrum fit  
  > "but was not used in the continuum spectrum fitting" (Jet base)
- Other facility **Gaia DR3**: optical position of M60 compared with the radio position  
  > "In Gaia Data Release 3 (DR3), the optical coordinates of M60 are given as RA=12:43:39.9708 (with an error of 6.2 mas) and Dec=+11:33:09.6882" (Radio images of M60)
- External data: BH mass M_BH = (4.5+/-1.0)e9 Msun from stellar dynamics  
  > "has a dynamic mass of $M_{\rm BH} = (4.5\pm1.0)\times10^{9}~M_{\odot}$ (cite: Shen2010)" (Introduction) [from (cite: Shen2010)]
- External data: TRGB distance 16.23 Mpc  
  > "$d=16.23\pm0.50({\rm ran})\pm0.42({\rm sys})~$Mpc (cite: Lee2017)" (Introduction) [from (cite: Lee2017)]
- External data: SBF distance 16.7 +/- 0.6 Mpc  
  > "the surface brightness fluctuation (SBF) method gives an estimate of $d=16.7\pm0.6~$Mpc (cite: Cantiello2018)" (Introduction) [from (cite: Cantiello2018)]
- External data: Scaled accretion rates 1.4e-8 and 7.2e-9 (mean ~1.1e-8 adopted)  
  > "The scaled mass accretion rate of M60, as reported by (cite: Johannsen2012), is $\dot{m}=1.4\times10^{-8}$ and (cite: Paggi2014) reported a rate of $\dot{m}=7.2\times10^{-9}$." (Introduction) [from (cite: Johannsen2012); (cite: Paggi2014)]
- External data: VLA flux densities from the NRAO VLA Archive Survey (NVAS)  
  > "Most data extracted from the NRAO VLA Archive Survey (cite: Crossley2008)" (Non-simultaneous radio spectrum) [from (cite: Crossley2008)]
- External data: VLA/A 1.5 GHz point, VLA/D 22 and 43 GHz points, SCUBA 150 GHz point  
  > "two data points were observed by VLA with D-configuration at 22 and 43 GHz respectively (cite: DiMatteo1999)" (Non-simultaneous radio spectrum) [from (cite: Temi2022; Grossova2022); (cite: DiMatteo1999)]
- External data: Non-detection of the CO lines in the ALMA data  
  > "(cite: Temi2022) reported non-detection of the CO lines." (Non-simultaneous radio spectrum) [from (cite: Temi2022)]
- External data: Radio position of M60 from the Radio Fundamental Catalog  
  > "According to the Radio Fundamental Catalog (RFC)[^4], which is available to the public, the coordinates are RA=12:43:39.9715 and Dec=+11:33:09.688 (with an error of 1.8 mas)." (Radio images of M60) [from Radio Fundamental Catalog (RFC), Astrogeo Center]
- External data: Corrected VLBA C-band gain curve table for PT and NL  
  > "To fix the issue, we used the new gain curve table provided by NRAO" (VLBA observations and data reduction) [from NRAO VLBA 7 GHz flux density scale page (footnote 2)]

## Processing

### Calibration

- pipeline or manual: ALMA data: ALMA Pipeline-Cycle5-R2-B in CASA (VLBA data calibrated manually in AIPS)  
  > "The data reduction was carried out in Common Astronomy Software Applications (CASA) casa-release-5.1.1 (cite: McMullin2007) with ALMA Pipeline-Cycle5-R2-B (cite: ALMAPipeline)." (Non-simultaneous radio spectrum)
- casa version: casa-release-5.1.1  
  > "The data reduction was carried out in Common Astronomy Software Applications (CASA) casa-release-5.1.1 (cite: McMullin2007)" (Non-simultaneous radio spectrum)
- pipeline version: ALMA Pipeline-Cycle5-R2-B  
  > "with ALMA Pipeline-Cycle5-R2-B (cite: ALMAPipeline)" (Non-simultaneous radio spectrum)
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: VLBA data only (Difmap): phase self-cal with 1.5 min solution interval, then amplitude+phase selfcal with 3 min interval  
  > "Initially, we fitted the circular Gaussian model to the visibility data and then performed phase self-calibration with a solution interval of 1.5 min." (VLBA observations and data reduction); "command was then run with a solution interval of 3 min, allowing the amplitude and phase to change simultaneously" (VLBA observations and data reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: VLBA data only: average beam 2.31/1.33 mas at 4.4/7.6 GHz  
  > "the average beam size at 4.4/7.6 GHz is 2.31/1.33 mas" (Radio images of M60)
- final rms: VLBA data only: 0.16/0.17 mJy/beam at 4.4/7.6 GHz  
  > "The peak brightness of the 4.4/7.6 GHz image is $18.58/19.69\,{\rm mJy\,beam^{-1}}$ and the image rms is 0.16/0.17 mJy beam$^{-1}$, respectively." (Radio images of M60)

### Inherited from earlier work

- Smooth broken power-law spectral model  
  > "we use a smooth broken power law model proposed by (cite: Callingham2017)" (Jet base) [from (cite: Callingham2017)]
- Jet power and inclination from Falcke & Biermann equation 8  
  > "Equation 8 in (cite: Falcke1999) can be used to determine the jet power $Q_{\rm jet}$ and the inclination angle $i$ of the jet in relation to the line of sight." (Jet base) [from (cite: Falcke1999)]
- ADAF analytical spectrum (self-similar solution)  
  > "(cite: Mahadevan1997) provided an analytical expression for the ADAF radiation spectrum by a self-similar solution" (ADAF) [from (cite: Mahadevan1997)]
- MCMC visibility fitting approach  
  > "we fitted the calibrated visibility data using the MCMC method, as recommended by (cite: Salafia2022)" (MCMC fitting) [from (cite: Salafia2022)]
- Dark-cluster lifetime calculation  
  > "Our approach to estimating the lifetime of the dark cluster present here follows (cite: Maoz1995; Maoz1998) and references therein." (Lifetime of the dark cluster) [from (cite: Maoz1995; Maoz1998)]
- Photon-ring size to SMBH mass method (d_ring = 5.2 R_S)  
  > "Johannsen et al. (2010) proposed a method to estimate the mass of SMBH by imaging its compact radio structure with VLBI." (New evidence for the existence of a SMBH in M60) [from (cite: Johannsen2010)]

### Not stated but needed to reproduce (our reading)

- ALMA band, spectral setup, array configurations and execution blocks used for the 350 GHz continuum flux measurements
- ALMA imaging parameters (task, cell, image size, weighting, mask, continuum channel selection, aperture or fit used to get 1.7 and 1.1 mJy)
- Whether any ALMA flux scale systematic error was added to the 0.2 and 0.1 mJy uncertainties
- Difmap weighting, uv-tapering, clean windows, and number of iterations for the VLBA images
- MCMC sampler algorithm and prior form inside MCMCUVFit (only search ranges, 200 walkers and 1e4 iterations given); code availability
- ADAF fit method and priors, and the free parameter ranges for alpha, beta, delta and the BPL component
- Exact flux values and uncertainty handling for NVAS points beyond Table 2
- Dust, gas and other assumptions are not needed here; only the compactness-to-lifetime inputs (mass range grid, mu) are not fully given

## Analysis recipe

1. **Measure ALMA 350 GHz continuum flux density**: Reduce archival ALMA data with the pipeline in CASA and extract the continuum flux density of M60 at two epochs  
  > "We reduced these ALMA data to extract flux densities from the radio continuum spectrum." (Non-simultaneous radio spectrum); "The data reduction was carried out in Common Astronomy Software Applications (CASA) casa-release-5.1.1 (cite: McMullin2007) with ALMA Pipeline-Cycle5-R2-B (cite: ALMAPipeline)." (Non-simultaneous radio spectrum)
   - software: CASA 5.1.1, ALMA Pipeline-Cycle5-R2-B
   - fitting: _not stated_
   - validation: _not stated_
2. **Calibrate VLBA correlated data**: AIPS: sampling correction, amplitude calibration from Tsys and gain curves (corrected PT/NL C-band gains), fringe fitting on B1116+128, global fringe fitting on M60 with merged half-bands, frequency averaging per subband  
  > "we corrected the correlation amplitudes due to minor sampling errors, and then ran amplitude calibration based on the system temperature data and antenna gain curves" (VLBA observations and data reduction); "we merged the subbands in halves (i.e., the 4.4 and 7.6 GHz data are combined, respectively) to enhance the Signal Noise Ratio (SNR) of the solution and conducted global fringe fitting on the data of M60 with 0.75 min solution interval." (VLBA observations and data reduction)
   - software: AIPS, DiFX2
   - parameter: Global fringe fit solution interval 0.75 min; all solutions SNR > 4  
  > "All the solutions had SNRs greater than 4." (VLBA observations and data reduction)
   - parameter: Correlation: 0.0625 MHz frequency resolution, 0.1 s integration  
  > "utilizing a 0.0625-MHz frequency resolution and a 0.1-s integration time" (VLBA observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
3. **Transfer amplitude gains from calibrator B1241+166**: Derive gain correction factors with Difmap gscale on B1241+166 and apply them to M60 in AIPS; first tested that self-cal solutions of the pair were consistent  
  > "we transferred the amplitude self-calibration solutions from the bright calibrator" (VLBA observations and data reduction); "The amplitude self-calibration solutions looked quite similar and were fully as expected." (VLBA observations and data reduction)
   - software: AIPS, Difmap
   - assumption: M60 and B1241+166 (4.8 deg apart, neighbouring scans) suffer consistent amplitude errors  
  > "their data were supposed to suffer fairly consistent amplitude errors" (VLBA observations and data reduction)
   - fitting: _not stated_
   - validation: Self-cal solutions of the calibrator pair compared and found similar  
  > "The amplitude self-calibration solutions looked quite similar and were fully as expected." (VLBA observations and data reduction)
4. **Deconvolve, self-calibrate and image VLBA data**: Difmap: circular Gaussian model fit, phase self-cal (1.5 min), then amplitude+phase selfcal (3 min), repeated until reduced chi-square minimized; same method at both frequencies  
  > "The model fitting and self-calibration processes were repeated until the reduced chi-square $\chi_{\nu}^{2}$ was minimized." (VLBA observations and data reduction); "The data at 4.4 and 7.6 GHz were reduced in the same method." (VLBA observations and data reduction)
   - software: Difmap
   - parameter: Data weights scaled so that reduced chi-square = 1  
  > "To obtain accurate uncertainty estimates, we scaled the data weights to set" (VLBA observations and data reduction)
   - assumption: Circular Gaussian source model; elliptical Gaussian not adopted because parameters (position angle) were poorly constrained  
  > "Because some best-fitting parameters, in particular the position angle of the major axis, had large uncertainties, the more complex model was not considered in the paper." (VLBA observations and data reduction)
   - fitting: _not stated_
   - validation: Phase-only self-cal with MCMC and least-squares fits gave consistent results with slightly larger uncertainties  
  > "The best-fitting parameters show slightly larger uncertainties but are fully consistent with the above results using the phase and amplitude self-calibration." (VLBA observations and data reduction)
5. **MCMC fit of circular Gaussian to visibilities**: Fit total flux, core size and position with MCMCUVFit using a Gaussian visibility likelihood  
  > "The MCMC fitting was executed using MCMCUVFit, a Python-based software specifically designed for fitting visibility data using MCMC method." (MCMC fitting)
   - software: MCMCUVFit
   - parameter: Search ranges: 10-25 mJy for S_tot, 1e-6 to 2 mas for theta_core, -1 to 1 mas for x and y  
  > "The search ranges for these four parameters to be estimated were set as follows: 10–25 mJy for $S_{\rm tot}$, $10^{-6}$–2  mas for $\theta_{\rm core}$, -1–1  mas for both $x$ and $y$." (MCMC fitting)
   - parameter: 200 walkers, 1e4 iterations, first half of samples discarded  
  > "The initial half of the samples were discarded" (MCMC fitting); "The MCMC fitting process was conducted with 200 walkers and $10^{4}$ iterations." (MCMC fitting)
   - assumption: Source is a circular Gaussian with free S_tot, theta_core, x, y  
  > "The input model for MCMC fitting need four parameters: $S_{\rm tot}$, $\theta_{\rm core}$, $x$ and $y$." (MCMC fitting)
   - fitting: MCMC, Gaussian log-likelihood in real and imaginary visibility residuals weighted by data weights; sampler name not stated; priors given only as search ranges  
  > "The logarithmic likelihood equation used in the fitting is" (MCMC fitting)
   - validation: Compared with Difmap fits; corner plots shown  
  > "results are presented using corner plots in Figure [5](#fig:corner)" (MCMC fitting)
6. **Build non-simultaneous radio spectrum**: Combine VLBA, ALMA and VLA/SCUBA flux densities; VLA A-configuration data used at <=15 GHz to avoid relic jet emission, higher frequencies include low-resolution data  
  > "To exclude possible diffuse emission from the relic jet, we used the measurements from the VLBA data and the VLA data observed with A-configuration at $\leq15$ GHz." (Non-simultaneous radio spectrum)
   - parameter: Systematic errors included: 5 percent for VLBA, 3 percent for VLA  
  > "These error bars include systematic errors: 5 percent for the VLBA results and 3 percent for the VLA results." (Non-simultaneous radio spectrum)
   - assumption: SMA 223 GHz variable data not used  
  > "except the SMA data, which is not used" (Non-simultaneous radio spectrum)
   - fitting: _not stated_
   - validation: Variability index m_var computed, indicating low variability  
  > "indicating a low variability" (Jet base)
7. **Fit broken power law spectrum and jet-base model**: Fit smooth broken power law to flux densities; then use Falcke & Biermann eq. 8 for jet power and inclination  
  > "we use a smooth broken power law model proposed by (cite: Callingham2017)" (Jet base); "Equation 8 in (cite: Falcke1999) can be used to determine the jet power $Q_{\rm jet}$ and the inclination angle $i$ of the jet in relation to the line of sight." (Jet base)
   - parameter: Extra 10% variability error added in quadrature to flux density errors  
  > "a variable error 10% ($\sigma_{\rm var}=10\%\times S_{\rm tot}$) was added to the flux density error" (Jet base)
   - parameter: gamma_e,0 = 230 (free parameter, lower than median 300)  
  > "We set it to $\gamma_{\rm e,0}=230$, which is lower than the median value of 300, to ensure that the simulated jet size is in line with the core size-frequency relation" (Jet base)
   - assumption: Jet base has inverted spectrum (0 < alpha <= 2.5) at low frequency and steep at high frequency  
  > "The jet base has an inverted spectrum at low frequency with a spectral index of $0<\alpha\leq2.5$, and a steep spectrum at high frequency (cite: Falcke1999)." (Origin of the centi-pc-scale compact component)
   - fitting: _not stated_
   - validation: Gamma_e,0 chosen so simulated jet size matches the core size-frequency relation  
  > "to ensure that the simulated jet size is in line with the core size-frequency relation" (Jet base)
8. **Fit ADAF model with optional nonthermal BPL component**: Fit Mahadevan (1997) ADAF spectrum to the radio continuum with alpha, beta, delta free; add a broken power law to model low-frequency flat part  
  > "The other three parameters $\alpha$, $\beta$, and $\delta$ were allowed to vary in order to fit the radio continuum spectrum of M60." (ADAF); "We included a broken power law (BPL) component in the model to refine the fit of the low-frequency data." (ADAF)
   - assumption: BH mass and accretion rate fixed to observed values  
  > "The black hole mass (cite: Shen2010) and accretion rate (cite: Johannsen2012; Paggi2014) were determined by observations and kept constant." (ADAF)
   - fitting: _not stated_
   - validation: Thermal-only ADAF fails at low frequency, motivating the BPL addition  
  > "Therefore, a simple ADAF model with only thermal electrons cannot fully explain the observed radio spectrum of M60." (ADAF)
9. **Test SMBH versus dark cluster by lifetime**: Compute half-mass density from M_BH and the 7.6 GHz size, then dark-cluster lifetime as min of evaporation and collision timescales, maximized over object types  
  > "The maximum lifetime of a dark cluster, $\tau_{\rm max}$, can be determined by examining all classes of dark objects mentioned above, across different mass ranges" (Lifetime of the dark cluster)
   - assumption: Plummer model, equal-mass objects at zero temperature  
  > "We presuppose that the structure of the cluster is described by Plummer model, with each constituent object assumed to have the same mass and zero temperature." (Lifetime of the dark cluster)
   - fitting: _not stated_
   - validation: _not stated_
10. **Upper limit on SMBH mass from photon ring size**: Use the 7.6 GHz core size limit as upper limit of photon ring diameter (d_ring = 5.2 R_S) to bound M_BH  
  > "Taking the core size of M60 at 7.6 GHz ($\theta_{\rm size}\leq0.27\,{\rm mas}$) as the upper limit of the photon ring diameter, an upper limit for the SMBH mass can be derived" (New evidence for the existence of a SMBH in M60)
   - assumption: Ring diameter 5.2 R_S, insensitive to spin, inclination and frequency  
  > "its diameter is determined by the mass of the SMBH ($d_{\rm ring}=5.2\, R_{\rm S}$)" (New evidence for the existence of a SMBH in M60)
   - fitting: _not stated_
   - validation: Compared with stellar-dynamics and X-ray gas masses  
  > "This independent derived upper limit for the black hole mass is consistent with the mass determined by stellar dynamics" (New evidence for the existence of a SMBH in M60)

## Software

- **CASA** casa-release-5.1.1: Reduction of the ALMA 350 GHz data  
  > "The data reduction was carried out in Common Astronomy Software Applications (CASA) casa-release-5.1.1 (cite: McMullin2007)" (Non-simultaneous radio spectrum)
- **ALMA Pipeline** Pipeline-Cycle5-R2-B: ALMA data reduction  
  > "with ALMA Pipeline-Cycle5-R2-B (cite: ALMAPipeline)" (Non-simultaneous radio spectrum)
- **AIPS** : VLBA amplitude and phase calibration, fringe fitting  
  > "The correlation data were calibrated in the Astronomical Image Processing System (cite: Greisen2003)." (VLBA observations and data reduction)
- **Difmap** : Deconvolution, model fitting, self-calibration and gscale for VLBA data  
  > "we did deconvolution and self-calibration in" (VLBA observations and data reduction)
- **DiFX2** : Software correlator for the VLBA data  
  > "The DiFX2 software correlator (cite: Deller2011) at the National Radio Astronomy Observatory (NRAO) was employed to correlate the data" (VLBA observations and data reduction)
- **MCMCUVFit** : MCMC fitting of a circular Gaussian to visibilities  
  > "The MCMC fitting was executed using MCMCUVFit, a Python-based software specifically designed for fitting visibility data using MCMC method." (MCMC fitting)
- **Astropy** : _not stated_

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA 350 GHz flux density of M60, 2017-07-18 | 1.7 | 0.2 | mJy | 1 | The resulting radio flux density of M60 at 350 GHz is $1.7\pm0.2$ mJy on 18 July 2017 and $1.1\pm0.1$ mJy on 24 December 2017. |
| ALMA 350 GHz flux density of M60, 2017-12-24 | 1.1 | 0.1 | mJy | 1 | The resulting radio flux density of M60 at 350 GHz is $1.7\pm0.2$ mJy on 18 July 2017 and $1.1\pm0.1$ mJy on 24 December 2017. |
| VLBA peak brightness at 4.4/7.6 GHz | 18.58/19.69 | not stated | mJy/beam | 4 | The peak brightness of the 4.4/7.6 GHz image is $18.58/19.69\,{\rm mJy\,beam^{-1}}$ and the image rms is 0.16/0.17 mJy beam$^{-1}$, respectively. |
| VLBA total flux density at 4.4 GHz | 19.1 | 1.0 | mJy | 5 | The total flux density at 4.4 and 7.6 GHz is $19.1\pm1.0$ mJy and $20.2\pm1.0$ mJy, respectively |
| VLBA total flux density at 7.6 GHz | 20.2 | 1.0 | mJy | 5 | The total flux density at 4.4 and 7.6 GHz is $19.1\pm1.0$ mJy and $20.2\pm1.0$ mJy, respectively |
| Core size upper limit at 4.4 GHz (99.7% confidence) | <=0.45 (0.036 pc, 83 R_S) | upper limit | mas | 5 | The radio component remains unresolved, with an upper limit size of $\leq 0.45$ mas (0.036 pc, or 83 $R_{\rm S}$) at 4.4 GHz |
| Core size upper limit at 7.6 GHz (99.7% confidence) | <=0.27 (0.022 pc, 50 R_S) | upper limit | mas | 5 | and $\leq$0.27 mas (0.022 pc, or 50 $R_{\rm S}$) at 7.6 GHz at a confidence level of $99.7\%$ |
| Brightness temperature T_B at 4.4 GHz | >=6.0e9 | lower limit | K | 5 | The brightness temperature of the unresolved component is $T_{\rm B}(4.4{\rm \,GHz})\geq6.0\times10^{9}$ K and $T_{\rm B}(7.6{\rm \,GHz})\geq5.9\times10^{9}$ K |
| Brightness temperature T_B at 7.6 GHz | >=5.9e9 | lower limit | K | 5 | The brightness temperature of the unresolved component is $T_{\rm B}(4.4{\rm \,GHz})\geq6.0\times10^{9}$ K and $T_{\rm B}(7.6{\rm \,GHz})\geq5.9\times10^{9}$ K |
| VLBA spectral index 4.4-7.6 GHz | 0.11 | 0.13 | dimensionless | 5 | The VLBA data of M60 suggest a spectral index of $\alpha_{\rm 4.4\,GHz}^{\rm 7.6\,GHz}=0.11\pm0.13$ |
| Variability index m_var at 1.5 GHz and 4.9 GHz | 7.4% and 11.9% | not stated | dimensionless | 6 | The $m_{\rm var}$ at 1.5 GHz and 4.9 GHz is approximately 7.4% and 11.9%, respectively |
| Broken power law turnover frequency nu_t | 51 | +8/-7 | GHz | 7 | The fitting results are $\nu_{\rm t} = 51_{-7}^{+8}$ GHz, $S_{\rm t} = 15_{-1}^{+1}$ mJy, $\alpha_{\rm thick} = 0.12_{-0.04}^{+0.04}$ and $\alpha_{\rm thin} = -1.5_{-0.1}^{+0.1}$. |
| Flux density at turnover S_t | 15 | +1/-1 | mJy | 7 | The fitting results are $\nu_{\rm t} = 51_{-7}^{+8}$ GHz, $S_{\rm t} = 15_{-1}^{+1}$ mJy, $\alpha_{\rm thick} = 0.12_{-0.04}^{+0.04}$ and $\alpha_{\rm thin} = -1.5_{-0.1}^{+0.1}$. |
| Optically thick spectral index alpha_thick | 0.12 | +0.04/-0.04 | dimensionless | 7 | The fitting results are $\nu_{\rm t} = 51_{-7}^{+8}$ GHz, $S_{\rm t} = 15_{-1}^{+1}$ mJy, $\alpha_{\rm thick} = 0.12_{-0.04}^{+0.04}$ and $\alpha_{\rm thin} = -1.5_{-0.1}^{+0.1}$. |
| Optically thin spectral index alpha_thin | -1.5 | +0.1/-0.1 | dimensionless | 7 | The fitting results are $\nu_{\rm t} = 51_{-7}^{+8}$ GHz, $S_{\rm t} = 15_{-1}^{+1}$ mJy, $\alpha_{\rm thick} = 0.12_{-0.04}^{+0.04}$ and $\alpha_{\rm thin} = -1.5_{-0.1}^{+0.1}$. |
| Peak frequency nu_p and peak flux density S_p | ~21.6 GHz and ~21.2 mJy | not stated | GHz; mJy | 7 | we obtain $\nu_{\rm p}\sim21.6~$GHz and $S_{\rm p}\sim21.2~$mJy. |
| Jet power Q_jet and inclination i | ~5.7e41 erg/s; ~30 deg | not stated | erg/s; deg | 7 | This yields an estimated jet power of $Q_{\rm jet} \sim 5.7\times10^{41}~{\rm erg\,s^{-1}}$ and an inclination angle of $i\sim30^\circ$. |
| ADAF+BPL fit parameters alpha, beta, delta | alpha=2.4e-4, beta=0.96, delta=0.61 | alpha +1.7/-1.1 (x1e-4); beta +0.01/-0.03; delta +0.25/-0.30 | dimensionless | 8 | $\alpha=2.4_{-1.1}^{+1.7}\times10^{-4}$, $\beta=0.96_{-0.03}^{+0.01}$, $\delta=0.61_{-0.30}^{+0.25}$ |
| Half-mass density of central object | >=5.4e13 | lower limit | Msun pc^-3 | 9 | the half mass density of the central object is $\rho_{\rm h} \geq 5.4\times10^{13}\,M_{\rm \odot}{\rm \,pc^{-3}}$ |
| Maximum dark cluster lifetime | <=8.4e9 | upper limit | yr | 9 | its lifetime would be $\tau \leq 8.4\times10^{9}\,{\rm yr}$ |
| Upper limit on SMBH mass from photon ring size | <=4.3e10 | upper limit | Msun | 10 | an upper limit for the SMBH mass can be derived: $M_{\rm BH} \leq 4.3\times10^{10}\, M_{\odot}$. |

## Qualitative findings

- No extended jets or winds above 0.85 mJy/beam detected in the VLBI images  
  > "no extended jets or winds exceeding $0.85~\mathrm{mJy\,beam^{-1}}$ were detected in the VLBI images" (Origin of the centi-pc-scale compact component)
- Radio emission attributed to an AGN rather than star formation  
  > "all point to the radio emission being caused by an AGN rather than star formation" (Radio images of M60)

## Claim tuples

- H: Is the VLBA radio core of M60 compact enough to constrain its nature at centi-pc scale? | E: Difmap and MCMC Gaussian fits to 4.4 and 7.6 GHz VLBA visibilities | R: Unresolved core, S_tot ~19-20 mJy, size <=0.27 mas at 7.6 GHz, T_B >=6e9 K | F: The component is the AGN radio core on centi-pc scale | **supported**
- H: Is the core a nonthermal jet base or an ADAF? | E: Fit broken power law and ADAF (with and without a BPL component) to the non-simultaneous 1.5-350 GHz spectrum | R: Peaked spectrum, alpha_thick=0.12, alpha_thin=-1.5; thermal-only ADAF fails at low frequency | F: Jet base or ADAF with nonthermal electrons both possible; not distinguished | **partially**
- H: Is the central massive object an SMBH rather than a dark cluster? | E: Compute half-mass density from the 7.6 GHz size and the lifetime of a putative dark cluster | R: rho_h >= 5.4e13 Msun/pc^3 and tau <= 8.4e9 yr, below the host age of ~1e10 yr | F: The radio core is more likely associated with an SMBH | **supported**
- H: Can the core size bound the SMBH mass via the photon ring? | E: Treat the 7.6 GHz size upper limit as the photon ring diameter (5.2 R_S) | R: M_BH <= 4.3e10 Msun | F: Consistent with the dynamical mass of 4.5e9 Msun | **supported**

## Reasoning

- Why this data: M60 chosen as a high-latitude LLAGN with very low luminosity and accretion rate; ALMA data reduced to add a 350 GHz flux density point to the spectrum  
  > "identified M60 as a prime candidate for studying the presence of jets in LLAGNs with very low luminosity and extremely low accretion rates." (Introduction); "We reduced these ALMA data to extract flux densities from the radio continuum spectrum." (Non-simultaneous radio spectrum)
- Why this method: MCMC used for reliable uncertainty on the angular size  
  > "To accurately characterize the uncertainties of the parameters of the Gaussian model, in particular the angular size, we also used the Markov Chain Monte Carlo (MCMC) method" (VLBA observations and data reduction)
- Alternative: Elliptical Gaussian model rejected because of poorly constrained position angle  
  > "Because some best-fitting parameters, in particular the position angle of the major axis, had large uncertainties, the more complex model was not considered in the paper." (VLBA observations and data reduction)
- Alternative: Thermal-electron-only ADAF rejected as it cannot reproduce the low-frequency spectral index  
  > "Therefore, a simple ADAF model with only thermal electrons cannot fully explain the observed radio spectrum of M60." (ADAF)
- How they decided it was enough: _not stated_
- Limitation (authors): Low VLBA image sensitivity; extended sub-pc jet emission not detected  
  > "The relatively low image sensitivity did not allow us to detect the emission beyond the compact core" (Radio images of M60)
- Limitation (authors): Sparse (u,v) coverage with high side lobes  
  > "The maximum side lobe was approximately 72% of the primary lobe." (VLBA observations and data reduction)
- Limitation (authors): Spectrum is non-simultaneous  
  > "There is no hint of strong variability from these non-simultaneous observations" (Non-simultaneous radio spectrum)
- Caveat (inferred, ours): Upper limit on size from a 3-min snapshot with 7 stations and 72% sidelobes; model dependence on the circular Gaussian assumption
- Caveat (inferred, ours): Spectrum mixes epochs spanning four decades and different resolutions; SMA variability suggests the 350 GHz ALMA points may not be contemporaneous with VLBA
- Caveat (inferred, ours): ALMA flux extraction is described in one sentence; no imaging or aperture details, so the 350 GHz points constrain the high-frequency slope only weakly
- Caveat (inferred, ours): Jet and ADAF models are not statistically compared; fit sampler and priors not given

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: MCMCUVFit developed by the authors; no availability statement  
  > "was developed by us" (VLBA observations and data reduction)
- Missing: ALMA imaging and flux extraction details for the two 350 GHz epochs
- Missing: Difmap imaging parameters and MCMCUVFit sampler details/code
- Missing: ADAF fit implementation and priors
- Data volume (inferred): ALMA: two 350 GHz datasets, likely tens of GB raw; VLBA: one 3-min 4096 Mbps snapshot, a few GB
- Score (inferred): 3/5, VLBA recipe and numeric results are reasonably detailed and the ALMA programs are named, but ALMA processing and model-fit implementation details are missing.
- Rediscovery candidate: no, ALMA is a minor part with no imaging details, the paper does not state data availability, and the main results rely on VLBA manual calibration steps.

## Links

- Method: (cite: Callingham2017) (smooth broken power-law spectral model)
- Method: (cite: Salafia2022) (MCMC fitting of visibilities)
- Method: (cite: Falcke1999) (jet-base model for jet power and inclination)
- Method: (cite: Mahadevan1997) (ADAF radio spectrum)
- Method: (cite: Maoz1995; Maoz1998) (dark cluster lifetime)
- Method: (cite: Johannsen2010) (photon ring mass method)
- Companion: (cite: Temi2022) (reported non-detection of CO in the same ALMA data; VLA 1.5 GHz point)
- Companion: (cite: Lo2023) (SMA 223 GHz variability of M60)
- Companion: (cite: Grossova2022) (VLA 1.5 GHz measurement)
- Related: VLBA Calibrator Survey 12 (BP252AF)
- Related: NRAO VLA Archive Survey (NVAS)
- Related: Radio Fundamental Catalog (RFC)
- Related: ALMA 2016.1.01135.S
- Related: ALMA 2017.1.00830.S

## Checks

```json
{
 "quotes": 128,
 "quotes_ok": 128,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 1,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 21,
 "numeric_problems": 0,
 "fill": {
  "facts": 124,
  "stated": 83,
  "rate": 0.669
 },
 "evidence_ok": true
}
```

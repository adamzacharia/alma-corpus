# Isotopic Ratios in the Disk of HD 163296

`2026ApJ...997L..19Q` | The Astrophysical Journal Letters 2026 | first author: Qi, Chunhua | arXiv: 2601.02593 | DOI: 10.3847/2041-8213/ae2916

Card schema 1.0 | model gemini-4-argon | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Can rare CO isotopologue observations in an optically thin outer disk region beyond a sharp CO snowline empirically constrain carbon and oxygen isotopic ratios without detailed disk modeling?  
  > "to empirically constrain carbon and oxygen isotopic ratios without detailed disk modeling." (Abstract); "Measuring flux ratios of multiple rare CO isotopologues observed at the same excitation level, such as C$^{17}$O and C$^{18}$O in the $J=1\rightarrow0$ transition or $^{13}$C$^{18}$O and C$^{17}$O in the $J=2\rightarrow1$ transition, provides an empirical means to constrain isotopic ratios while minimizing assumptions." (Introduction)
- Target **HD 163296**: coordinates _not stated_; z/distance 1.5'' is around 150 au (approx 100 pc)  
  > "beyond 1.5$''$ ($r \gtrsim 150$ au), where the emission becomes optically thin." (Abstract); distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00884.S, 2018.1.01055.L, 2021.1.00899.S
- bands: Band 3, Band 6  
  > "represents the worst case of uncorrelated 5% absolute flux errors between the Band 6 datasets, whereas for the C$^{18}$O/C$^{17}$O(1–0) profile we include only statistical uncertainties because the two Band 3 lines share a common flux scale" (Observations and Results)
- frequencies and spectral setup: C17O(1-0): 112.359 GHz (0.50 km/s channel width); C18O(1-0): 109.782 GHz (0.50 km/s); 13C18O(2-1): 209.419 GHz (0.32 km/s); C17O(2-1): 224.714 GHz (0.32 km/s)  
  > "| C$^{17}$O(1–0) | 112.359 | 0.50 | 0.51 |" (Table 3); "| C$^{18}$O(1–0) | 109.782 | 0.50 | 0.48 |" (Table 3); "| $^{13}$C$^{18}$O(2–1) | 209.419 | 0.32 | 1.17 |" (Table 3)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.28'' x 0.25'' for 13C18O(2-1); 0.52'' circularized common beam for all transitions  
  > "The final image has a beam size of $0.28\ensuremath{''} \times 0.25\ensuremath{''}$, CLEANed to a $3\sigma$ threshold" (Observations and Results); "we reimaged each transition to a common circularized beam of $0.52\ensuremath{''}$, defined by the major axis of the synthesized beam for C$^{17}$O(2–1) with robust 0.5 weighting and a $u,v$ taper" (Observations and Results)
- max recoverable scale: _not stated_
- sensitivity: 0.51 mJy/beam (C17O 1-0), 0.48 mJy/beam (C18O 1-0), 1.17 mJy/beam (13C18O 2-1), 2.54 mJy/beam (C17O 2-1) in 0.52'' common beam  
  > "| C$^{17}$O(1–0) | 112.359 | 0.50 | 0.51 |" (Table 3); "| $^{13}$C$^{18}$O(2–1) | 209.419 | 0.32 | 1.17 |" (Table 3); "| C$^{17}$O(2–1) | 224.714 | 0.32 | 2.54 |" (Table 3)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: New observations (Project ID: 2021.1.00899.S, PI: K. Zhang) combined with archival observations  
  > "We present Atacama Large Millimeter/submillimeter Array observations of the rare isotopologue $^{13}$C$^{18}$O(2–1) at $\sim$0.3$''$ resolution from the disk around the Herbig Ae star HD 163296, combined with archival observations of C$^{17}$O(2–1), C$^{18}$O(1–0), and C$^{17}$O(1–0)" (Abstract); "A detailed description of the observations (Project ID: 2021.1.00899.S, PI: K. Zhang) is given by T. Armitage et al. (ApJ accepted)." (Observations and Results)
- Line: C17O 1-0 (112.359 GHz)
- Line: C18O 1-0 (109.782 GHz)
- Line: 13C18O 2-1 (209.419 GHz)
- Line: C17O 2-1 (224.714 GHz)
- External data: CO molecular data from LAMDA database  
  > "We adopted molecular data from the LAMDA database (cite: Schoier2005), using collisional rate coefficients from (cite: Yang2010)." (Constraining Optical Depths with Same-transition Isotopologue Flux Ratios) [from (cite: Schoier2005)]
- External data: CO collisional rate coefficients with ortho- and para-H2  
  > "We adopted molecular data from the LAMDA database (cite: Schoier2005), using collisional rate coefficients from (cite: Yang2010)." (Constraining Optical Depths with Same-transition Isotopologue Flux Ratios) [from (cite: Yang2010)]
- External data: Canonical ISM isotopic ratios (12C/13C = 69 +/- 6, 16O/18O = 557 +/- 30, 18O/17O = 3.6 +/- 0.2)  
  > "We adopted canonical ISM isotopic ratios (cite: Wilson1999): $^{12}$C/$^{13}$C$= 69$, $^{16}$O/$^{18}$O$= 557$, and $^{18}$O/$^{17}$O$= 3.6$" (Constraining Optical Depths with Same-transition Isotopologue Flux Ratios); "The best-fit isotopic ratios at 1.5$''$ and comparisons with ISM values (cite: Wilson1999) are as follows:" (MCMC Fitting to Constrain Isotopic Ratios) [from (cite: Wilson1999)]
- Simulation/model as data: Non-LTE radiative transfer calculations using RADEX via SpectralRadex  
  > "To quantify how same-transition isotopologue flux ratios vary with line-center optical depth, we performed a systematic non-LTE radiative transfer analysis using the `RADEX` code (cite: vanderTak2007) through the Python package `SpectralRadex` (cite: Holdship2021)." (Constraining Optical Depths with Same-transition Isotopologue Flux Ratios)

## Processing

### Calibration

- pipeline or manual: standard pipeline calibration followed by self-calibration  
  > "The data reduction and imaging were performed using `CASA` v6.6.3 (cite: McMullin2007; CASA+2022), following standard pipeline calibration, self-calibration for improved signal-to-noise, and imaging with the `tclean` task using Briggs weighting (robust 0.5)." (Observations and Results)
- casa version: v6.6.3  
  > "The data reduction and imaging were performed using `CASA` v6.6.3 (cite: McMullin2007; CASA+2022)" (Observations and Results)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 5% per dataset (7.1% for uncorrelated inter-band/epoch ratios)  
  > "we propagate both the statistical map uncertainties and a 7.1% systematic calibration term that represents the worst case of uncorrelated 5% absolute flux errors between the Band 6 datasets" (Observations and Results); "We adopt the standard ALMA absolute calibration uncertainty of approximately 5% per dataset." (Flux Calibration Uncertainty Propagation for Ratios)
- self calibration: performed for improved signal-to-noise  
  > "following standard pipeline calibration, self-calibration for improved signal-to-noise, and imaging with the `tclean` task using Briggs weighting (robust 0.5)." (Observations and Results)

### Imaging

- task: tclean  
  > "and imaging with the `tclean` task using Briggs weighting (robust 0.5)." (Observations and Results)
- deconvolver: _not stated_
- weighting robust: Briggs weighting, robust 0.5  
  > "and imaging with the `tclean` task using Briggs weighting (robust 0.5)." (Observations and Results); "we reimaged each transition to a common circularized beam of $0.52\ensuremath{''}$, defined by the major axis of the synthesized beam for C$^{17}$O(2–1) with robust 0.5 weighting and a $u,v$ taper" (Observations and Results)
- uv taper: applied to achieve a common circularized beam of 0.52''  
  > "we reimaged each transition to a common circularized beam of $0.52\ensuremath{''}$, defined by the major axis of the synthesized beam for C$^{17}$O(2–1) with robust 0.5 weighting and a $u,v$ taper, following the MAPS cleaning strategy (cite: Czekala2021)." (Observations and Results); "All datasets were tapered and Briggs weighted to a common circularized beam (FWHM $0.52\ensuremath{''}$)." (Line Properties and Noise)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied consistently to all transitions  
  > "The final image has a beam size of $0.28\ensuremath{''} \times 0.25\ensuremath{''}$, CLEANed to a $3\sigma$ threshold, corrected for the so called (cite: Jorsater1995) effect (cite: Czekala2021), and primary beam corrected." (Observations and Results); "The JvM correction and primary beam correction were applied consistently to all transitions" (Observations and Results)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.28'' x 0.25'' for native 13C18O(2-1); 0.52'' circularized common beam for all four transitions  
  > "The final image has a beam size of $0.28\ensuremath{''} \times 0.25\ensuremath{''}$, CLEANed to a $3\sigma$ threshold" (Observations and Results); "we reimaged each transition to a common circularized beam of $0.52\ensuremath{''}$, defined by the major axis of the synthesized beam for C$^{17}$O(2–1) with robust 0.5 weighting and a $u,v$ taper" (Observations and Results)
- final rms: 0.51 mJy/beam (C17O 1-0), 0.48 mJy/beam (C18O 1-0), 1.17 mJy/beam (13C18O 2-1), 2.54 mJy/beam (C17O 2-1) per channel in 0.52'' beam  
  > "| C$^{17}$O(1–0) | 112.359 | 0.50 | 0.51 |" (Table 3); "| $^{13}$C$^{18}$O(2–1) | 209.419 | 0.32 | 1.17 |" (Table 3); "| C$^{17}$O(2–1) | 224.714 | 0.32 | 2.54 |" (Table 3)

### Inherited from earlier work

- Detailed description of the 2021.1.00899.S observations and data reduction  
  > "A detailed description of the observations (Project ID: 2021.1.00899.S, PI: K. Zhang) is given by T. Armitage et al. (ApJ accepted)." (Observations and Results) [from T. Armitage et al. (ApJ accepted)]
- MAPS cleaning strategy, JvM correction, and beam circularization  
  > "we reimaged each transition to a common circularized beam of $0.52\ensuremath{''}$, defined by the major axis of the synthesized beam for C$^{17}$O(2–1) with robust 0.5 weighting and a $u,v$ taper, following the MAPS cleaning strategy (cite: Czekala2021)." (Observations and Results) [from (cite: Czekala2021)]
- Archival C17O(2-1), C18O(1-0), and C17O(1-0) data and CO snowline analysis at 0.75''  
  > "The disk around the Herbig Ae star HD 163296 provides an optimal environment to search for optically thin regions in rare CO isotopologue emission, owing to its previously established sharp CO snowline transition at a readily accessible spatial scale (cite: Qi2024)." (Observations and Results); "(cite: Qi2024) performed forward radiative‐transfer calculations for the C$^{17}$O(2–1), C$^{18}$O(1–0), and C$^{17}$O(1–0) lines" (Observations and Results) [from (cite: Qi2024)]

### Not stated but needed to reproduce (our reading)

- Disk inclination and position angle used for deprojection in GoFish
- Exact uv-taper parameters used for each transition to reach the 0.52'' circularized beam
- Continuum subtraction procedure (e.g., uvcontsub order and line-free channel ranges)
- Velocity range or Keplerian mask parameters used to compute the integrated intensity profiles in GoFish
- Self-calibration solution intervals, number of rounds, and whether phase+amplitude self-cal was applied
- Number of MCMC walkers, steps, and burn-in length in emcee

## Analysis recipe

1. **Calibrate and image native 13C18O(2-1) and verify Keplerian kinematics**: Standard pipeline calibration, self-calibration, tclean imaging with Briggs robust 0.5 to 3-sigma threshold, JvM and primary beam correction; generate moment-0 and moment-1 maps using bettermoments with 2-sigma clip  
  > "The data reduction and imaging were performed using `CASA` v6.6.3 (cite: McMullin2007; CASA+2022), following standard pipeline calibration, self-calibration for improved signal-to-noise, and imaging with the `tclean` task using Briggs weighting (robust 0.5)." (Observations and Results); "The final image has a beam size of $0.28\ensuremath{''} \times 0.25\ensuremath{''}$, CLEANed to a $3\sigma$ threshold, corrected for the so called (cite: Jorsater1995) effect (cite: Czekala2021), and primary beam corrected." (Observations and Results); "These maps were generated using the `bettermoments` package (cite: Teague2018), with a $2\sigma$ intensity clip to mitigate noise bias." (Kinematics of $^{13}$C$^{18}$O(2–1) Emission)
   - software: CASA, bettermoments
   - parameter: robust = 0.5, 3-sigma CLEAN threshold, 0.28'' x 0.25'' beam, 2-sigma intensity clip for moments  
  > "The final image has a beam size of $0.28\ensuremath{''} \times 0.25\ensuremath{''}$, CLEANed to a $3\sigma$ threshold" (Observations and Results); "These maps were generated using the `bettermoments` package (cite: Teague2018), with a $2\sigma$ intensity clip to mitigate noise bias." (Kinematics of $^{13}$C$^{18}$O(2–1) Emission)
   - fitting: _not stated_
   - validation: Confirmed velocity pattern follows Keplerian gradient aligned with disk major axis and radial derivative minimum at 0.75'' matches CO snowline  
  > "the derivative exhibits a clear local minimum at 0.75$''$, coincident with the CO snowline radius inferred from other CO isotopologues (cite: Qi2024)." (Observations and Results); "The velocity pattern clearly traces a Keplerian gradient aligned with the disk’s major axis, and the emission is confined within the disk extent seen in other isotopologues (cite: Qi2011)." (Kinematics of $^{13}$C$^{18}$O(2–1) Emission)
2. **Reimage all four transitions to a common circularized beam and extract radial intensity and ratio profiles**: Reimage C17O(1-0), C18O(1-0), 13C18O(2-1), and C17O(2-1) with robust 0.5 and uv taper to a common 0.52'' circularized beam with JvM and PB corrections; extract deprojected azimuthally averaged radial profiles using GoFish radial_profile  
  > "we reimaged each transition to a common circularized beam of $0.52\ensuremath{''}$, defined by the major axis of the synthesized beam for C$^{17}$O(2–1) with robust 0.5 weighting and a $u,v$ taper, following the MAPS cleaning strategy (cite: Czekala2021)." (Observations and Results); "The JvM correction and primary beam correction were applied consistently to all transitions, and deprojected, azimuthally averaged radial profiles were extracted using the `radial_profile` function from `GoFish` (cite: Teague2019)." (Observations and Results)
   - software: CASA, GoFish
   - parameter: common circularized beam FWHM = 0.52'', robust = 0.5, 7.1% systematic uncertainty added in quadrature for Band 6 ratio  
  > "For the C$^{17}$O/$^{13}$C$^{18}$O(2–1) profile, we propagate both the statistical map uncertainties and a 7.1% systematic calibration term that represents the worst case of uncorrelated 5% absolute flux errors between the Band 6 datasets" (Observations and Results)
   - assumption: 5% absolute flux calibration uncertainty per dataset; Band 3 lines share common flux scale (correlated, rho ~ 1); Band 6 datasets assumed uncorrelated (rho = 0) worst case  
  > "We adopt the standard ALMA absolute calibration uncertainty of approximately 5% per dataset." (Flux Calibration Uncertainty Propagation for Ratios); "In the worst-case scenario where the calibration errors are uncorrelated ($\rho = 0$), the systematic contribution to the ratio uncertainty is $\sqrt{2} \times$ 5% $\approx$ 7.1%." (Flux Calibration Uncertainty Propagation for Ratios)
   - fitting: _not stated_
   - validation: Both flux ratios rise steeply across the 0.75'' snowline and converge to plateaus beyond 1.5''  
  > "Both ratios remain relatively flat inside 0.75$''$, consistent with high optical depth, then rise rapidly across the CO snowline and converge to plateaus beyond 1.5$''$ ($r \gtrsim 150$ au), where all lines become optically thin." (Observations and Results)
3. **Quantify same-transition isotopologue flux ratios as a function of optical depth using non-LTE radiative transfer grids**: Run non-LTE radiative transfer calculations over a grid of T_kin, n_H2, and N_CO using RADEX via SpectralRadex to compute line-center optical depth and flux ratios  
  > "To quantify how same-transition isotopologue flux ratios vary with line-center optical depth, we performed a systematic non-LTE radiative transfer analysis using the `RADEX` code (cite: vanderTak2007) through the Python package `SpectralRadex` (cite: Holdship2021)." (Constraining Optical Depths with Same-transition Isotopologue Flux Ratios)
   - software: RADEX, SpectralRadex
   - parameter: T_kin = 30, 50, 70 K; n_H2 = 10^5 to 10^8 cm^-3; log N_CO = 16 to 19  
  > "and explored a grid of kinetic temperatures ($T_{\rm kin} = 30$, 50, 70 K), molecular hydrogen densities ($n_{\rm H_2} = 10^5$–$10^8$ cm$^{-3}$), and CO column densities ($\log N_{\rm CO} = 16$–19)." (Constraining Optical Depths with Same-transition Isotopologue Flux Ratios)
   - assumption: Ortho-to-para H2 ratio of 3:1; CMB background T_bg = 2.73 K; canonical ISM isotopic ratios: 12C/13C = 69, 16O/18O = 557, 18O/17O = 3.6  
  > "Collisions with both ortho- and para-H$_2$ were included, assuming an ortho-to-para ratio of 3:1, and level populations were solved with the Cosmic Microwave Background (CMB) as the only background radiation field ($T_{\rm bg} = 2.73$ K)." (Constraining Optical Depths with Same-transition Isotopologue Flux Ratios); "We adopted canonical ISM isotopic ratios (cite: Wilson1999): $^{12}$C/$^{13}$C$= 69$, $^{16}$O/$^{18}$O$= 557$, and $^{18}$O/$^{17}$O$= 3.6$" (Constraining Optical Depths with Same-transition Isotopologue Flux Ratios)
   - fitting: _not stated_
   - validation: Tested sensitivity of ratio-tau curves to +/-30% independent and coherent variations in assumed isotopic ratios; normalized curves agree within <= 1-2% for tau <= 0.3  
  > "We explicitly tested the sensitivity of these ratio-$\tau$ curves to $\pm30$% variations in the assumed isotopic ratios (Appendix 7) and found that while the thin-limit plateau shifts as expected, the shape of the ratio as a function of $\tau$ over the $\tau \lesssim 0.3$ regime used to identify the optically thin zone in HD 163296 is essentially unchanged." (Constraining Optical Depths with Same-transition Isotopologue Flux Ratios); "As in Test A, the absolute thin-limit plateaus shift as expected, but the normalized ratio–$\tau$ curves agree to within $\lesssim$1–2% for $\tau \lesssim 0.3$, the regime used to identify the optically thin region in HD 163296." (Test B: coherent scaling of the full elemental set.)
4. **Constrain carbon and oxygen isotopic ratios at r = 1.5'' using MCMC fitting of beam-averaged line intensities**: Extract beam-averaged integrated intensities in an annulus centered at 1.5'' and fit them using an MCMC approach (emcee) coupled with RADEX over 7 free parameters  
  > "To constrain the isotopic ratios in the optically thin region, we retrieved the integrated intensity in an annulus centered at 1.5$''$, which is effectively smoothed over the $0.52\ensuremath{''}$ beam." (MCMC Fitting to Constrain Isotopic Ratios); "We used an MCMC approach to fit these intensities using `RADEX` with seven free parameters: kinetic temperature ($T_{\rm kin}$), molecular hydrogen density ($n_{\rm H_2}$), CO column density ($N_{\rm CO}$), line width ($\Delta V$), and three isotopic ratios ($^{12}$C/$^{13}$C, $^{16}$O/$^{18}$O, and $^{18}$O/$^{17}$O)." (MCMC Fitting to Constrain Isotopic Ratios)
   - software: GoFish, emcee, RADEX, SpectralRadex
   - parameter: Annulus centered at 1.5'' (~150 au), smoothed over 0.52'' beam; 7 free parameters  
  > "To constrain the isotopic ratios in the optically thin region, we retrieved the integrated intensity in an annulus centered at 1.5$''$, which is effectively smoothed over the $0.52\ensuremath{''}$ beam." (MCMC Fitting to Constrain Isotopic Ratios)
   - assumption: Single uniform slab at 1.5'' where Delta V represents local thermal plus microturbulent FWHM  
  > "We note that in our `RADEX` calculations, $\Delta V$ represents the local thermal plus microturbulent FWHM, not the beam-smeared Keplerian shear." (MCMC Fitting to Constrain Isotopic Ratios)
   - fitting: MCMC via emcee; uniform priors: T_kin ~ U(10, 200) K, Delta V ~ U(0.1, 0.6) km/s, log10(n_H2) ~ U(4, 9), log10(N_CO) ~ U(16, 20), 12C/13C ~ U(10, 200), 16O/18O ~ U(100, 1000), 18O/17O ~ U(1, 10)  
  > "we adopted uniform priors in linear space for $T_{\rm kin}\!\sim\!{\cal U}(10,200)$ K and $\Delta V\!\sim\!{\cal U}(0.1,0.6)$ km s$^{-1}$, and uniform-in-log priors for the scale parameters $\log_{10} n_{\rm H_2}\!\sim\!{\cal U}(4,9)$ and $\log_{10} N_{\rm CO}\!\sim\!{\cal U}(16,20)$." (MCMC Fitting to Constrain Isotopic Ratios); "For the isotopic ratios, we used broad uniform priors, $^{12}$C/$^{13}$C$\!\sim\!{\cal U}(10,200)$, $^{16}$O/$^{18}$O$\!\sim\!{\cal U}(100,1000)$, and $^{18}$O/$^{17}$O$\!\sim\!{\cal U}(1,10)$, so that the posteriors are driven by the data rather than by the priors." (MCMC Fitting to Constrain Isotopic Ratios)
   - validation: Inspected posterior corner plots and covariances; performed global +/-10% and worst-case per-band +/-10% flux calibration rescaling sensitivity tests  
  > "The corner plot of the posterior distributions, which illustrates parameter covariances and uncertainties, is shown in Appendix 9. As demonstrated by the calibration sensitivity tests in Appendix 10, $5$–$10$% flux scale offsets do not shift the inferred isotopic ratios beyond their quoted uncertainties." (MCMC Fitting to Constrain Isotopic Ratios); "We quantified how absolute–flux systematics propagate into the posteriors with two bracketing tests that leave the modeling and priors unchanged and only rescale the four measured, beam–averaged integrated intensities used in the MCMC." (Calibration Sensitivity)

## Software

- **Astropy** : General astronomical data analysis  
  > "Astropy (cite: Astropy2013; Astropy2018; Astropy2022), `bettermoments` (cite: Teague2018), `CASA` (cite: CASA+2022), `emcee` (cite: emcee), `GoFish` (cite: Teague2019), Matplotlib (cite: Hunter2007), NumPy (cite: vanderWalt2011), `RADEX` (cite: vanderTak2007), `SpectralRadex` (cite: Holdship2021)." (Software)
- **bettermoments** : Generating moment-0 and moment-1 maps of 13C18O(2-1) emission  
  > "These maps were generated using the `bettermoments` package (cite: Teague2018), with a $2\sigma$ intensity clip to mitigate noise bias." (Kinematics of $^{13}$C$^{18}$O(2–1) Emission)
- **CASA** v6.6.3: Data reduction, calibration, self-calibration, and tclean imaging  
  > "The data reduction and imaging were performed using `CASA` v6.6.3 (cite: McMullin2007; CASA+2022), following standard pipeline calibration, self-calibration for improved signal-to-noise, and imaging with the `tclean` task using Briggs weighting (robust 0.5)." (Observations and Results)
- **tclean** : Imaging CO isotopologue lines  
  > "and imaging with the `tclean` task using Briggs weighting (robust 0.5)." (Observations and Results)
- **emcee** : MCMC fitting of beam-averaged intensities to constrain isotopic ratios  
  > "Astropy (cite: Astropy2013; Astropy2018; Astropy2022), `bettermoments` (cite: Teague2018), `CASA` (cite: CASA+2022), `emcee` (cite: emcee), `GoFish` (cite: Teague2019), Matplotlib (cite: Hunter2007), NumPy (cite: vanderWalt2011), `RADEX` (cite: vanderTak2007), `SpectralRadex` (cite: Holdship2021)." (Software)
- **GoFish** : Extracting deprojected, azimuthally averaged radial intensity profiles using radial_profile  
  > "and deprojected, azimuthally averaged radial profiles were extracted using the `radial_profile` function from `GoFish` (cite: Teague2019)." (Observations and Results)
- **Matplotlib** : Plotting  
  > "Astropy (cite: Astropy2013; Astropy2018; Astropy2022), `bettermoments` (cite: Teague2018), `CASA` (cite: CASA+2022), `emcee` (cite: emcee), `GoFish` (cite: Teague2019), Matplotlib (cite: Hunter2007), NumPy (cite: vanderWalt2011), `RADEX` (cite: vanderTak2007), `SpectralRadex` (cite: Holdship2021)." (Software)
- **NumPy** : Numerical calculations  
  > "Astropy (cite: Astropy2013; Astropy2018; Astropy2022), `bettermoments` (cite: Teague2018), `CASA` (cite: CASA+2022), `emcee` (cite: emcee), `GoFish` (cite: Teague2019), Matplotlib (cite: Hunter2007), NumPy (cite: vanderWalt2011), `RADEX` (cite: vanderTak2007), `SpectralRadex` (cite: Holdship2021)." (Software)
- **RADEX** : Non-LTE radiative transfer calculations for optical depth grids and MCMC fitting  
  > "we performed a systematic non-LTE radiative transfer analysis using the `RADEX` code (cite: vanderTak2007) through the Python package `SpectralRadex` (cite: Holdship2021)." (Constraining Optical Depths with Same-transition Isotopologue Flux Ratios); "We used an MCMC approach to fit these intensities using `RADEX` with seven free parameters" (MCMC Fitting to Constrain Isotopic Ratios)
- **SpectralRadex** : Python wrapper to run RADEX  
  > "we performed a systematic non-LTE radiative transfer analysis using the `RADEX` code (cite: vanderTak2007) through the Python package `SpectralRadex` (cite: Holdship2021)." (Constraining Optical Depths with Same-transition Isotopologue Flux Ratios)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO snowline radius (local minimum of radial derivative) | 0.75 | not stated | arcsec | 1 | The intensity decreases smoothly with radius, and the derivative exhibits a clear local minimum at 0.75$''$, coincident with the CO snowline radius inferred from other CO isotopologues (cite: Qi2024). |
| Optically thin inner boundary radius | 1.5 | not stated | arcsec | 2 | Both the C$^{17}$O/$^{13}$C$^{18}$O(2–1) and C$^{18}$O/C$^{17}$O(1–0) flux ratios rise sharply across the CO snowline and flatten beyond 1.5$''$ ($r \gtrsim 150$ au), where the emission becomes optically thin. |
| C17O/13C18O(2-1) plateau flux ratio beyond 1.5'' | 20 | not stated | dimensionless | 2 | The C$^{17}$O/$^{13}$C$^{18}$O(2–1) ratio approaches approximately 20, consistent with the ISM value expected under optically thin emission conditions for both lines |
| C18O/C17O(1-0) plateau flux ratio beyond 1.5'' | 2.7 | not stated | dimensionless | 2 | while the C$^{18}$O/C$^{17}$O(1–0) ratio stabilizes near 2.7, implying moderate optical depth in the C$^{18}$O(1–0) line for ISM-like abundances |
| Beam-averaged integrated intensity of C17O(1-0) at 1.5'' (mJy/beam km/s) | 5.82 | 0.29 | mJy beam^-1 km s^-1 | 4 | / C$^{17}$O(1–0) / $5.82 \pm 0.29$ / $2.09 \pm 0.10$ / |
| Beam-averaged integrated intensity of C17O(1-0) at 1.5'' (K km/s) | 2.09 | 0.10 | K km s^-1 | 4 | / C$^{17}$O(1–0) / $5.82 \pm 0.29$ / $2.09 \pm 0.10$ / |
| Beam-averaged integrated intensity of C18O(1-0) at 1.5'' (mJy/beam km/s) | 15.49 | 0.25 | mJy beam^-1 km s^-1 | 4 | / C$^{18}$O(1–0) / $15.49 \pm 0.25$ / $5.80 \pm 0.09$ / |
| Beam-averaged integrated intensity of C18O(1-0) at 1.5'' (K km/s) | 5.80 | 0.09 | K km s^-1 | 4 | / C$^{18}$O(1–0) / $15.49 \pm 0.25$ / $5.80 \pm 0.09$ / |
| Beam-averaged integrated intensity of 13C18O(2-1) at 1.5'' (mJy/beam km/s) | 3.33 | 0.41 | mJy beam^-1 km s^-1 | 4 | / $^{13}$C$^{18}$O(2–1) / $3.33 \pm 0.41$ / $0.34 \pm 0.04$ / |
| Beam-averaged integrated intensity of 13C18O(2-1) at 1.5'' (K km/s) | 0.34 | 0.04 | K km s^-1 | 4 | / $^{13}$C$^{18}$O(2–1) / $3.33 \pm 0.41$ / $0.34 \pm 0.04$ / |
| Beam-averaged integrated intensity of C17O(2-1) at 1.5'' (mJy/beam km/s) | 74.85 | 1.17 | mJy beam^-1 km s^-1 | 4 | / C$^{17}$O(2–1) / $74.85 \pm 1.17$ / $6.70 \pm 0.10$ / |
| Beam-averaged integrated intensity of C17O(2-1) at 1.5'' (K km/s) | 6.70 | 0.10 | K km s^-1 | 4 | / C$^{17}$O(2–1) / $74.85 \pm 1.17$ / $6.70 \pm 0.10$ / |
| Kinetic temperature T_kin at 1.5'' | 112.1 | +50.5/-38.3 | K | 4 | / $T_{\rm kin}$ (K) / $112.1^{+50.5}_{-38.3}$ / |
| log10(n_H2) at 1.5'' | 6.05 | +1.34/-1.26 | log10(cm^-3) | 4 | / $\log_{10}(n_{\rm H_2}$/cm$^{-3}$) / $6.05^{+1.34}_{-1.26}$ / |
| log10(N_CO) at 1.5'' | 19.25 | +0.25/-0.32 | log10(cm^-2) | 4 | / $\log_{10}(N_{\rm CO}$/cm$^{-2}$) / $19.25^{+0.25}_{-0.32}$ / |
| Line width Delta V at 1.5'' | 0.32 | +0.18/-0.15 | km s^-1 | 4 | / $\Delta V$ (km s$^{-1}$) / $0.32^{+0.18}_{-0.15}$ / |
| 12C/13C isotopic ratio at 1.5'' | 75.3 | +14.7/-11.4 | dimensionless | 4 | we derive isotopic ratios of $^{12}$C/$^{13}$C = $75.3^{+14.7}_{-11.4}$ and $^{18}$O/$^{17}$O = $3.28^{+0.31}_{-0.26}$, both consistent with local interstellar medium values.; / $^{12}$C/$^{13}$C / $75.3^{+14.7}_{-11.4}$ / |
| 16O/18O isotopic ratio at 1.5'' | 599 | +276/-310 | dimensionless | 4 | / $^{16}$O/$^{18}$O / $599^{+276}_{-310}$ / |
| 18O/17O isotopic ratio at 1.5'' | 3.28 | +0.31/-0.26 | dimensionless | 4 | we derive isotopic ratios of $^{12}$C/$^{13}$C = $75.3^{+14.7}_{-11.4}$ and $^{18}$O/$^{17}$O = $3.28^{+0.31}_{-0.26}$, both consistent with local interstellar medium values.; / $^{18}$O/$^{17}$O / $3.28^{+0.31}_{-0.26}$ / |

## Qualitative findings

- The radial derivative of the 13C18O(2-1) integrated intensity profile shows a local minimum at 0.75'', confirming a sharp drop in CO column density at the CO snowline is not an opacity artifact.  
  > "The intensity decreases smoothly with radius, and the derivative exhibits a clear local minimum at 0.75$''$, coincident with the CO snowline radius inferred from other CO isotopologues (cite: Qi2024)." (Observations and Results); "Because $^{13}$C$^{18}$O(2–1) is optically thinner than those transitions, the persistence of the derivative dip in this line further indicates that the feature is not an opacity artifact." (Observations and Results)
- Same-transition isotopologue flux ratios (C17O/13C18O(2-1) and C18O/C17O(1-0)) rise steeply across the snowline and plateau beyond 1.5'', providing a model-independent diagnostic of optical depth.  
  > "Both ratios remain relatively flat inside 0.75$''$, consistent with high optical depth, then rise rapidly across the CO snowline and converge to plateaus beyond 1.5$''$ ($r \gtrsim 150$ au), where all lines become optically thin." (Observations and Results); "We have shown that same-transition isotopologue flux ratios provide a direct and model-independent diagnostic of optical depth in protoplanetary disks." (Conclusions and future work)
- Carbon (12C/13C) and oxygen (18O/17O) isotopic ratios in the optically thin outer disk of HD 163296 are consistent with local ISM values, suggesting the bulk outer disk gas reservoir has remained largely unprocessed since formation.  
  > "These results confirm that, in the optically thin outer disk of HD 163296, the carbon and oxygen isotopic ratios are broadly consistent with those of the local ISM." (MCMC Fitting to Constrain Isotopic Ratios); "The ISM-like $^{12}$C/$^{13}$C and $^{18}$O/$^{17}$O ratios in HD 163296’s outer disk suggest that the bulk gas reservoir has remained largely unprocessed since formation." (Conclusions and future work)

## Claim tuples

- H: The dip in the radial derivative of CO isotopologue intensity at 0.75'' in HD 163296 reflects a true sharp drop in CO column density across the snowline rather than an optical depth artifact. | E: Observed the much rarer and optically thinner 13C18O(2-1) transition at ~0.3'' resolution and computed the radial derivative of its deprojected integrated intensity profile. | R: The radial derivative of 13C18O(2-1) exhibits a clear local minimum at 0.75'', coincident with the snowline radius inferred from more abundant CO isotopologues. | F: The persistence of the derivative dip in the optically thinner 13C18O(2-1) line confirms that the sharp transition across the CO snowline is a genuine column density drop and not an opacity artifact. | **supported**
- H: Same-transition flux ratios of rare CO isotopologues can empirically identify optically thin disk regions without detailed physical or chemical disk modeling. | E: Reimaged C17O(2-1), 13C18O(2-1), C18O(1-0), and C17O(1-0) to a common 0.52'' circularized beam, extracted radial flux ratio profiles, and compared them to non-LTE RADEX radiative transfer grids across optical depth. | R: Both C17O/13C18O(2-1) and C18O/C17O(1-0) ratios are flat inside 0.75'', rise sharply across the snowline, and flatten to constant plateaus (~20 and ~2.7, respectively) beyond 1.5''. | F: Same-transition isotopologue flux ratios directly trace optical depth and empirically identify the outer disk beyond 1.5'' (r >= 150 au) as optically thin. | **supported**
- H: Carbon and oxygen isotopic ratios in the outer disk of HD 163296 preserve local interstellar medium values rather than showing strong disk-level fractionation. | E: Performed a 7-parameter MCMC fit using emcee and RADEX on the beam-averaged integrated intensities of the four CO isotopologue transitions in the optically thin annulus at 1.5''. | R: Derived 12C/13C = 75.3 (+14.7/-11.4), 18O/17O = 3.28 (+0.31/-0.26), and 16O/18O = 599 (+276/-310). | F: Both 12C/13C and 18O/17O are well constrained and consistent with local ISM values, indicating the outer disk gas reservoir has remained largely unprocessed, whereas 16O/18O is only weakly constrained due to moderate optical depth in C18O(1-0) and covariance with N_CO. | **supported**

## Reasoning

- Why this data: HD 163296 has a previously established sharp CO snowline transition at an accessible spatial scale (0.75''), and combining new deep 13C18O(2-1) data with archival C17O(2-1), C18O(1-0), and C17O(1-0) provides two same-transition isotopologue pairs.  
  > "The disk around the Herbig Ae star HD 163296 provides an optimal environment to search for optically thin regions in rare CO isotopologue emission, owing to its previously established sharp CO snowline transition at a readily accessible spatial scale (cite: Qi2024)." (Observations and Results); "Measuring flux ratios of multiple rare CO isotopologues observed at the same excitation level, such as C$^{17}$O and C$^{18}$O in the $J=1\rightarrow0$ transition or $^{13}$C$^{18}$O and C$^{17}$O in the $J=2\rightarrow1$ transition, provides an empirical means to constrain isotopic ratios while minimizing assumptions." (Introduction)
- Why this method: Measuring flux ratios of rare isotopologues in the same J -> J-1 transition minimizes sensitivity to excitation temperature and beam dilution and avoids reliance on complex thermochemical disk models.  
  > "The present study is the first to use high signal-to-noise $^{13}$C$^{18}$O(2–1) observations of the HD 163296 disk to empirically identify an optically thin region beyond the sharply defined CO snowline, directly from the flux ratio behavior, without relying on detailed physical or chemical modeling." (Introduction); "Because both lines in each pair arise from the same $J \rightarrow J-1$ transition and have nearly identical frequencies, their ratios substantially reduce sensitivity to excitation temperature and beam dilution" (Constraining Optical Depths with Same-transition Isotopologue Flux Ratios)
- Alternative: Plausible excitation gradients alone (without a sharp drop in CO column density) were rejected as the cause of the radial derivative dip at the snowline.  
  > "(cite: Qi2024) performed forward radiative‐transfer calculations for the C$^{17}$O(2–1), C$^{18}$O(1–0), and C$^{17}$O(1–0) lines and showed that the observed dip in the radial derivative of the integrated-intensity profile cannot be produced by plausible excitation gradients alone and a sharp drop in the CO column density at the snowline is required." (Observations and Results)
- How they decided it was enough: A single representative annulus at 1.5'' was deemed sufficient because the optically thin zone is in the outer disk where rare lines are weak and no significant radial trend is detected in either ratio beyond 1.5'' within uncertainties.  
  > "Because the optically thin area is confined to the outer disk and the rare isotopologue lines are weak, we adopted this single beam-averaged annulus at 1.5$''$ for quantitative fitting." (MCMC Fitting to Constrain Isotopic Ratios); "Within the uncertainties, no significant radial trend is detected in either ratio across the outer disk region (Fig. 2), so a single representative radius is sufficient for the isotopic analysis." (MCMC Fitting to Constrain Isotopic Ratios)
- Limitation (authors): Vertical differences in the emitting layers of different isotopologues can introduce residual excitation effects.  
  > "their ratios substantially reduce sensitivity to excitation temperature and beam dilution, though vertical differences in the emitting layers can introduce residual effects." (Constraining Optical Depths with Same-transition Isotopologue Flux Ratios)
- Limitation (authors): The 16O/18O ratio is weakly constrained due to moderate optical depth in C18O(1-0) and strong positive covariance with log N_CO.  
  > "The $^{16}$O/$^{18}$O ratio remains weakly constrained due to moderate optical depth in the C$^{18}$O(1–0) line and degeneracy with CO column density." (Abstract); "In contrast, the $^{16}$O/$^{18}$O ratio remains weakly constrained because C$^{18}$O(1–0) is only marginally optically thick at line center and because of strong parameter covariance." (MCMC Fitting to Constrain Isotopic Ratios)
- Limitation (authors): Physical parameters T_kin, n_H2, and Delta V have broad, unconstrained posteriors because optically thin line intensities are insensitive to them.  
  > "The $T_{\rm kin}$, $n_{\rm H_2}$, and $\Delta V$ parameters also show broad, unconstrained posteriors, as expected for optically thin conditions in which line intensities are relatively insensitive to these quantities." (MCMC Fitting to Constrain Isotopic Ratios)
- Limitation (authors): Measurements trace gas in the outer disk rather than ices and refractory solids, so the connection to solar system meteoritic and cometary reservoirs is tentative.  
  > "The connection to solar system materials is suggestive but necessarily tentative, because our measurements trace gas in the outer disk, whereas meteoritic and cometary values primarily record ices and refractory solids." (Conclusions and future work)
- Caveat (inferred, ours): C17O hyperfine structure splitting is not explicitly discussed in the 1D RADEX slab modeling, which could affect line-center optical depth and linewidth (Delta V) interpretation if hyperfine components are treated as a single line.
- Caveat (inferred, ours): Single-slab 1D RADEX modeling at r = 1.5'' neglects vertical temperature and density gradients as well as vertical differences in the emitting heights of 1-0 vs 2-1 transitions.

## Reproducibility

- Data public (paper): ALMA project codes ADS/JAO.ALMA#2016.1.00884.S, ADS/JAO.ALMA#2018.1.01055.L, and ADS/JAO.ALMA#2021.1.00899.S are cited.  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00884.S, ADS/JAO.ALMA#2018.1.01055.L" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Exact disk geometry (inclination, position angle, stellar mass, systemic velocity) and velocity integration window passed to GoFish
- Missing: Specific uv-taper values used in tclean for each of the four lines to reach the 0.52'' circularized beam
- Missing: Self-calibration parameters for 2021.1.00899.S (deferred to T. Armitage et al., ApJ accepted)
- Missing: Exact likelihood definition in the MCMC (whether statistical errors from Table 1 alone or including systematic calibration errors were used in the baseline MCMC likelihood)
- Data volume (inferred): ~50-200 GB for raw/calibrated visibilities across the three ALMA projects (including MAPS 2018.1.01055.L); <1 GB for the four reimaged spectral cubes and extracted radial profiles.
- Score (inferred): 82/5, The core analysis (RADEX + emcee MCMC on the four beam-averaged fluxes in Table 1) is completely specified with explicit priors, molecular data sources, and tabular inputs/outputs, making the radiative transfer and MCMC steps immediately reproducible. The visibility imaging and GoFish profile extraction steps lose a few points because self-cal details are deferred to a companion paper and exact deprojection/uv-taper parameters are not explicitly listed.
- Rediscovery candidate: yes, All three ALMA datasets are public in the archive, the software stack (CASA, GoFish, bettermoments, SpectralRadex/RADEX, emcee) is standard and open-source, intermediate integrated intensities at 1.5'' are explicitly tabulated in Table 1, and the main scientific results are precise numeric isotopic ratios in Table 2.

## Links

- Method: (cite: Czekala2021) (MAPS cleaning strategy, JvM correction, and beam circularization)
- Method: (cite: Teague2019) (GoFish package for extracting deprojected azimuthally averaged radial profiles)
- Method: (cite: Teague2018) (bettermoments package for generating moment-0 and moment-1 maps)
- Method: (cite: vanderTak2007) (RADEX non-LTE radiative transfer code)
- Method: (cite: Holdship2021) (SpectralRadex Python wrapper for RADEX)
- Method: (cite: emcee) (emcee MCMC ensemble sampler)
- Companion: T. Armitage et al. (ApJ accepted) (Detailed description of the new 13C18O(2-1) ALMA observations (2021.1.00899.S))
- Companion: (cite: Qi2024) (Previous analysis of the sharp CO snowline and archival C17O(2-1), C18O(1-0), and C17O(1-0) data in HD 163296)
- Related: MAPS (Molecules with ALMA at Planet-forming Scales, 2018.1.01055.L)

## Checks

```json
{
 "quotes": 134,
 "quotes_ok": 134,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 9,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 19,
 "numeric_problems": 0,
 "fill": {
  "facts": 87,
  "stated": 62,
  "rate": 0.713
 },
 "evidence_ok": true
}
```

# Oxygen Isotopes Reveal Low-mass Star Dominance in the Small Magellanic Cloud

`2025ApJ...994..158G` | The Astrophysical Journal 2025 | first author: Gong, Yan | arXiv: 2510.16343 | DOI: 10.3847/1538-4357/ae1035

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: astrochemistry, nearby_galaxies, star_formation
- Question: Can the oxygen isotope ratios (especially 18O/17O) of molecular gas in the low-metallicity SMC be measured via C18O and C17O J=2-1 and what do they say about stellar enrichment and the galaxy-wide IMF  
  > "Oxygen isotope abundances and their ratios are fingerprints of stellar evolution and therefore provide a powerful tool in tracing the enrichment history of galaxies." (abstract); "Precise measurements of the gas-phase $^{18}$O/$^{17}$O isotope ratios in the SMC will yield important insight into its chemical evolution" (Introduction)
- Target **LIRS 36 (aka N12A), SMC southwest bar**: coordinates ACA phase center (J2000) 00h46m40.8s, -73d06m14.4s  
  > "00$^{\rm h}$46$^{\rm m}$40$^{\rm s}$8, $-$73$^{\circ}$06$^{\prime}$14$^{\prime\prime}$4" (Observations and data reduction); "The Small Magellanic Cloud (SMC), at a distance of 62.1$\pm$1.9 kpc (cite: 2014ApJ...780...59G)" (Introduction); z/distance SMC distance 62.1+/-1.9 kpc  
  > "00$^{\rm h}$46$^{\rm m}$40$^{\rm s}$8, $-$73$^{\circ}$06$^{\prime}$14$^{\prime\prime}$4" (Observations and data reduction); "The Small Magellanic Cloud (SMC), at a distance of 62.1$\pm$1.9 kpc (cite: 2014ApJ...780...59G)" (Introduction); distance from (cite: 2014ApJ...780...59G) Graczyk et al. 2014  
  > "00$^{\rm h}$46$^{\rm m}$40$^{\rm s}$8, $-$73$^{\circ}$06$^{\prime}$14$^{\prime\prime}$4" (Observations and data reduction); "The Small Magellanic Cloud (SMC), at a distance of 62.1$\pm$1.9 kpc (cite: 2014ApJ...780...59G)" (Introduction)

## Data provenance

- ALMA projects: 2023.1.01576.S, 2015.1.00196.S
- bands: Band 6, two frequency setups, 16 spectral windows in total (four used here)  
  > "Observations were performed using the ALMA Band 6 receivers, covering both spectral line and continuum emission with two frequency setups comprising 16 spectral windows in total." (Observations and data reduction)
- frequencies and spectral setup: Four windows on 12CO, 13CO, C18O, C17O J=2-1; 244 kHz channels (~0.3 km/s); first three observed simultaneously, C17O separately  
  > "The spectral channel width was 244 kHz, corresponding to a velocity spacing of $\sim$0.3 km s$^{-1}$ for the four transitions." (Observations and data reduction); "The former three transitions were observed simultaneously, while the last line was observed independently." (Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: Atacama Compact Array (ACA) for the main data; total-power (TP) data from 2015.1.00196.S  
  > "were conducted between 2024 June 24 and August 23 using the Atacama Compact Array" (Observations and data reduction); "Total-power (TP) $^{12}$CO" (Observations and data reduction)
- configurations: _not stated_
- baselines: 8.9-48.9 m, 7-10 antennas  
  > "The observations employed 7–10 antennas with baseline lengths of 8.9–48.9 m" (Observations and data reduction)
- angular resolution: Restoring beams 6.5x5.7 to 7.0x6.1 arcsec (Table 1); all data convolved to a common circular 7.5 arcsec beam  
  > "6.5$\times$5.7, $-$86" (Table 1); "all data were convolved to a common circular beam of 7$''$5 for subsequent analysis" (Observations and data reduction)
- max recoverable scale: 29.0-30.5 arcsec (MRS column of Table 1)  
  > "(6) Maximum recoverable scale." (Table 1); "29.0" (Table 1)
- sensitivity: ACA noise 11, 10, 8, 4 mJy/beam at ~0.3 km/s channel width for 12CO, 13CO, C18O, C17O; TP ~0.5 Jy/beam (12CO, 13CO), ~0.4 Jy/beam (C18O) per 244 kHz channel  
  > "(7) Noise level at the corresponding channel width." (Table 1); "are $\sim$0.5 Jy beam$^{-1}$ for both" (Observations and data reduction)
- time on source: ~60 hours of telescope time  
  > "a total of $\sim$60 hours of telescope time" (Observations and data reduction)
- observing dates: ACA 2024 June 24 to August 23; TP 2016 June and August  
  > "were conducted between 2024 June 24 and August 23" (Observations and data reduction); "observations were conducted in 2016 June and August" (Observations and data reduction)
- pi or archival as stated: ACA project PI Yan Gong (new observations); TP project PI Julia Roman-Duval (2015.1.00196.S)  
  > "(project code: 2023.1.01576.S, PI: Yan Gong)" (Observations and data reduction); "PI: Julia Roman-Duval" (Observations and data reduction)
- Line: 12CO J=2-1 (230538.0000(5) MHz)
- Line: 13CO J=2-1 (220398.6842(1) MHz)
- Line: C18O J=2-1 (219560.3577(3) MHz)
- Line: C17O J=2-1 (224714.3858(3) MHz)
- Other facility **APEX 12CO and 13CO J=3-2 survey (in prep.)**: Identified LIRS 36 as the brightest 13CO J=3-2 position, used to select the target  
  > "LIRS 36 in the southwest bar is identified as the brightest position in $^{13}$CO $J=3\to 2$ emission" (Observations and data reduction)
- Other facility **ALMA total power (project 2015.1.00196.S)**: TP 12CO and 13CO J=2-1 data used to recover missing flux via feathering with the ACA data  
  > "to recover the missing flux in our ACA observations" (Observations and data reduction)
- External data: SMC distance of 62.1+/-1.9 kpc  
  > "at a distance of 62.1$\pm$1.9 kpc (cite: 2014ApJ...780...59G)" (Introduction) [from (cite: 2014ApJ...780...59G)]
- External data: Line rest frequencies from the Cologne Database for Molecular Spectroscopy  
  > "suggested by the Cologne Database for Molecular Spectroscopy (cite: 2016JMoSp.327...95E)" (Table 1) [from (cite: 2016JMoSp.327...95E)]
- External data: Background temperature 2.73 K  
  > "the background temperature, which is set to be 2.73 K (cite: 2009ApJ...707..916F)" (Local thermodynamic equilibrium) [from (cite: 2009ApJ...707..916F)]
- External data: SMC star formation history and low star formation rate (<0.3 Msun/yr over >~10 Gyr)  
  > "the overall star formation rates were low, of order $<$0.3  M$_{\odot}$yr$^{-1}$ over the past $\gtrsim$10 Gyr (cite: 2004AJ....127.1531H)" (Discussion) [from (cite: 2009AJ....138.1243H); (cite: 2004AJ....127.1531H)]
- External data: Gaia census: number of high-mass stars lower by a factor of 3-7 than expected from the low-mass population  
  > "finds the number of high-mass stars to be lower by a factor of 3–7 than expected from the low-mass population (cite: 2021A&A...646A.106S)" (Discussion) [from (cite: 2021A&A...646A.106S)]
- External data: Literature oxygen isotope ratios for LMC, NGC 253, NGC 4945, M82, PKS 1830-211, NGC 3256, Arp 220, M83 and Milky Way regions (comparison table)  
  > "Table notes: $^a$This work; $^b$(cite: 2009ApJ...690..580W); $^c$(cite: 2021AA...656A..46M)" (Table 3) [from (cite: 2009ApJ...690..580W); (cite: 2021AA...656A..46M); (cite: 2004AA...422..883W); (cite: 1993AA...274..730H); (cite: 2010AA...522A..62M); (cite: 2023AA...674A.101M); (cite: 2018ApJ...855...49H); (cite: 2015AA...579A.101A); (cite: 2023AA...670A..98Y); (cite: 1989GeCoA..53..197A)]
- External data: 13CO/C18O intensity ratio of ~100 in N83C (comparison)  
  > "consistent with the high intensity ratios reported for N83C in the SMC (cite: 2017ApJ...844...98M)" (Results) [from (cite: 2017ApJ...844...98M)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline in CASA for the ACA data; standard CASA pipeline for the TP data  
  > "The raw data were calibrated using the ALMA pipeline of the Common Astronomy Software Applications (CASA) package (cite: 2022PASP..134k4501C)." (Observations and data reduction); "The single-dish data were reduced using the standard CASA pipeline." (Observations and data reduction)
- casa version: CASA 6.5.4 (stated for imaging; calibration version not stated)  
  > "Subsequent imaging of the calibrated data was performed manually with CASA version 6.5.4." (Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J2258-2758 (also bandpass); phase calibrator J0102-7546  
  > "The bandpass and flux calibrator was J2258$-$2758, while the phase calibrator was J0102$-$7546." (Observations and data reduction)
- flux scale uncertainty: better than 10%  
  > "Based on the measurements of the calibrators, the flux calibration accuracy is estimated to be better than 10%." (Observations and data reduction)
- self calibration: _not stated_

### Imaging

- task: tclean (manual imaging in CASA 6.5.4)  
  > "The image reconstruction was carried out using the" (Observations and data reduction)
- deconvolver: Hogbom  
  > "employing the Högbom algorithm" (Observations and data reduction)
- weighting robust: Briggs, robust = 0.5  
  > "Briggs weighting with a robust parameter of 0.5" (Observations and data reduction)
- uv taper: _not stated_
- cell size: 1.1 arcsec (~1/5 of the synthesized beams)  
  > "All cleaned images have a pixel size of 1$''$1, corresponding linearly to approximately 1/5 of their synthesized beams." (Observations and data reduction)
- image size: _not stated_
- masking: AUTO-MULTITHRESH with parameters as in Table 2 of Kepley et al. 2020  
  > "with parameters set identically to those listed in Table 2 of (cite: 2020PASP..132b4505K)" (Observations and data reduction)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied to all cleaned data  
  > "A primary beam correction was applied to all cleaned data." (Observations and data reduction)
- array combination: ACA and TP combined with CASA feather (12CO and 13CO only)  
  > "The combination of the single-dish and ACA datasets was performed using the" (Observations and data reduction)
- smoothing: all data convolved to a common circular 7.5 arcsec beam  
  > "all data were convolved to a common circular beam of 7$''$5 for subsequent analysis" (Observations and data reduction)
- final beam: common circular beam of 7.5 arcsec  
  > "all data were convolved to a common circular beam of 7$''$5 for subsequent analysis" (Observations and data reduction)
- final rms: ACA-only noise 11, 10, 8, 4 mJy/beam per ~0.3 km/s channel (before convolution to 7.5 arcsec)  
  > "(7) Noise level at the corresponding channel width." (Table 1)

### Inherited from earlier work

- AUTO-MULTITHRESH masking parameters  
  > "with parameters set identically to those listed in Table 2 of (cite: 2020PASP..132b4505K)" (Observations and data reduction) [from (cite: 2020PASP..132b4505K) Kepley et al. 2020, Table 2]
- LTE radiative transfer equation for the peak brightness temperature  
  > "According to the radiative transfer equation (cite: 2015PASP..127..266M)" (Local thermodynamic equilibrium) [from (cite: 2015PASP..127..266M)]
- Weeds LTE spectral modelling approach  
  > "we use the CLASS extension Weeds for the LTE spectral modeling (cite: 2011A&A...526A..47M)" (Local thermodynamic equilibrium) [from (cite: 2011A&A...526A..47M)]

### Not stated but needed to reproduce (our reading)

- Image size / field of view and tclean threshold, niter, mask parameter values (only given by reference to Kepley et al. 2020)
- Whether and how continuum was subtracted, and which channels were line-free
- CASA version and pipeline version used for calibration (only the imaging version is given)
- Feather settings (sdfactor, TP scaling, units conversion from Jy/beam to K) and TP imaging/gridding details
- Which software did the Gaussian line fits and how the Table 2 uncertainties were derived
- Prior ranges for Tex and column densities, burn-in length, and how the noise sigma_i entering chi-square was set (spectral channels vs peak value)
- How the C17O hyperfine structure was handled in the Weeds model and whether per-channel spectra or only peak values were fit
- Pixel/aperture used for the 'emission peak' spectrum extraction beyond the quoted peak coordinates
- Details of the self-calibration, if any, and of the antenna flagging

## Analysis recipe

1. **Calibrate and image the ACA data**: ALMA pipeline calibration in CASA, then manual tclean imaging  
  > "The raw data were calibrated using the ALMA pipeline of the Common Astronomy Software Applications (CASA) package (cite: 2022PASP..134k4501C)." (Observations and data reduction)
   - software: CASA 6.5.4, tclean
   - parameter: Hogbom deconvolver, Briggs robust 0.5  
  > "Briggs weighting with a robust parameter of 0.5" (Observations and data reduction)
   - parameter: AUTO-MULTITHRESH masking, parameters as Kepley et al. 2020 Table 2  
  > "The automated masking algorithm" (Observations and data reduction)
   - parameter: pixel size 1.1 arcsec, primary beam correction applied  
  > "A primary beam correction was applied to all cleaned data." (Observations and data reduction)
   - fitting: _not stated_
   - validation: Flux calibration accuracy estimated to be better than 10% from the calibrators  
  > "the flux calibration accuracy is estimated to be better than 10%" (Observations and data reduction)
2. **Add short spacings and match resolution**: Feather TP 12CO and 13CO data with the ACA data, then convolve all lines to a common 7.5 arcsec beam; C18O and C17O stay ACA-only  
  > "The combination of the single-dish and ACA datasets was performed using the" (Observations and data reduction); "all data were convolved to a common circular beam of 7$''$5 for subsequent analysis" (Observations and data reduction)
   - software: CASA feather
   - parameter: common circular beam 7.5 arcsec  
  > "all data were convolved to a common circular beam of 7$''$5 for subsequent analysis" (Observations and data reduction)
   - assumption: C18O and C17O ACA-only spectra have negligible missing flux at the peak position because they are compact  
  > "we conclude that the missing flux in the ACA-only data is negligible for the C$^{18}$O $J=2 \to 1$ and C$^{17}$O $J=2 \to 1$ spectra at the peak position" (Short spacing)
   - fitting: _not stated_
   - validation: ACA-only vs ACA+TP flux comparison: ACA-only recovers 70% (12CO) and 82% (13CO) of total flux, 83% and 97% at the peak position  
  > "the ACA-only data account for only 70% and 82% of the total flux densities in the ACA+TP combined data" (Short spacing)
3. **Extract peak spectra and fit Gaussians**: Extract spectra at the emission peak (13CO peak) and fit a Gaussian to each to get velocity, peak Tb, FWHM and integrated intensity  
  > "we extracted spectra at the emission peak and used them to derive the isotopic ratios." (Results); "We performed a Gaussian fitting to each spectrum" (Results)
   - parameter: Integration velocity range 105-145 km/s for 12CO and 122-129 km/s for the other three lines  
  > "The values are obtained by integrating the velocity range of 105–145 km s$^{-1}$ for" (Table 2)
   - assumption: 12CO and 13CO from ACA+TP; C18O and C17O from ACA-only  
  > "whereas those of C$^{18}$O ($2 \to 1$) and C$^{17}$O ($2 \to 1$) are derived from the ACA-only datasets" (Table 2)
   - fitting: Single-Gaussian fit to each line profile; software not stated  
  > "We performed a Gaussian fitting to each spectrum" (Results)
   - validation: Velocity centroids of the four lines agree within the uncertainties and with earlier studies  
  > "The velocity centroids of the four transitions are consistent within the uncertainties" (Results)
4. **Derive excitation temperature and optical depths**: LTE radiative transfer with optically thick 12CO J=2-1: Tex from the 12CO peak brightness temperature, then optical depths of the isotopologues assuming the same Tex  
  > "we can derive excitation temperatures from the peak brightness temperatures of $^{12}$CO $J=2\to 1$ using Eqs." (Local thermodynamic equilibrium); "Assuming that the four $J=2\to 1$ transitions have the same excitation temperature, we derive a peak optical depth of 0.34$\pm$0.02 for $^{13}$CO $J=2\to 1$." (Results)
   - parameter: Background temperature 2.73 K  
  > "the background temperature, which is set to be 2.73 K (cite: 2009ApJ...707..916F)" (Local thermodynamic equilibrium)
   - parameter: Beam dilution factor f=1 (fiducial) or f=0.34 (source size 5.4 arcsec)  
  > "For the fiducial case, we neglect the beam dilution effects by assuming $f\sim 1$." (Local thermodynamic equilibrium)
   - assumption: LTE, 12CO optically thick, same Tex for all four lines  
  > "Assuming that $^{12}$CO $J=2\to 1$ is optically thick and neglecting the beam dilution effects" (Local thermodynamic equilibrium)
   - fitting: _not stated_
   - validation: Optical depths of 13CO, C18O, C17O stay almost unchanged when f=0.34 is assumed, so the three lines are treated as optically thin  
  > "the optical depths of $^{13}$CO $J=2\to 1$, C$^{18}$O $J=2\to 1$, and C$^{17}$O $J=2\to 1$ stay almost unchanged" (Results)
5. **Fit Tex and column densities with LTE MCMC**: Weeds LTE spectral model fitted to the observed spectra with emcee; Tex and the 13CO, C18O, C17O column densities are fit  
  > "we use the CLASS extension Weeds for the LTE spectral modeling (cite: 2011A&A...526A..47M)" (Local thermodynamic equilibrium); "To fit the observed spectra, we employed the" (Local thermodynamic equilibrium)
   - software: Weeds (CLASS/GILDAS), emcee
   - parameter: 10 walkers, 4500 iterations after burn-in  
  > "The MCMC sampling was carried out with 10 walkers over 4500 iterations, following an initial burn-in phase to ensure convergence." (Local thermodynamic equilibrium)
   - parameter: Velocities and FWHM fixed to Table 2 values; C17O FWHM set equal to C18O  
  > "The systemic velocities and FWHM line widths are based on Table" (Local thermodynamic equilibrium)
   - parameter: 10% flux density uncertainty adopted  
  > "adopting a 10% uncertainty in flux density" (Results)
   - assumption: Single Gaussian component for all molecules  
  > "we assume a single Gaussian component for all molecules for simplicity" (Local thermodynamic equilibrium)
   - assumption: Same source size for all four lines  
  > "we assume the same source size for the four lines" (Local thermodynamic equilibrium)
   - assumption: C17O line width set equal to C18O because Gaussian fit overestimates it owing to hyperfine splitting  
  > "The FWHM line width of C$^{17}$O $J=2\to 1$ is set to be identical to C$^{18}$O $J=2\to 1$" (Local thermodynamic equilibrium)
   - fitting: emcee affine-invariant ensemble sampler; uniform priors on Tex and the three column densities; Gaussian likelihood exp(-chi2/2); errors from 16th and 84th percentiles  
  > "We assumed uniform priors for the excitation temperature" (Local thermodynamic equilibrium); "the likelihood was taken to be Gaussian" (Local thermodynamic equilibrium); "The reported best-fit values and associated 1$\sigma$ errors correspond to the 16th and 84th percentiles of the posterior distributions." (Local thermodynamic equilibrium)
   - validation: Posterior parameters reported as well constrained (corner plot, Fig. 3)  
  > "where the four parameters are well constrained" (Local thermodynamic equilibrium)
6. **Compute isotope abundance ratios**: Isotope ratios taken directly from the fitted column densities; 12CO integrated intensity ratios give only lower limits on 16O/18O and 16O/17O  
  > "The corresponding isotope ratios were directly determined from these column densities." (Results); "Because the $^{12}$CO $J=2\to1$ transition is optically thick" (Results)
   - assumption: Oxygen isotopes not chemically fractionated; C18O and C17O optically thin  
  > "oxygen isotopes are not subject to chemical fractionation (cite: 1984ApJ...277..581L)" (Introduction)
   - fitting: _not stated_
   - validation: Ratios compared with values for the LMC, other galaxies and the Milky Way (Table 3)  
  > "compares oxygen isotope ratios with those measured in various environments" (Discussion)
7. **Test sensitivity to the assumed source size**: Repeat the MCMC fit with source size 5.4 arcsec (beam dilution factor 0.34) inferred from the compact C17O component  
  > "In order to test the impact of the assumed source size on the derived isotope ratios, the MCMC approach was performed again by assuming" (Local thermodynamic equilibrium)
   - software: emcee, Weeds
   - parameter: source size 5.4 arcsec, f=0.34  
  > "a beam dilution factor of 0.34 (i.e., a source size of 5$''$4;" (Results)
   - fitting: _not stated_
   - validation: Isotope ratios essentially unchanged (18O/17O 0.88+/-0.29), so ratios are robust although Tex and N change  
  > "but the isotope ratios remain almost identical" (Local thermodynamic equilibrium)
8. **Interpret ratios in terms of stellar enrichment and IGIMF**: Compare the low 18O/17O and high 13CO/C18O with nucleosynthesis sources, SMC carbon-star fraction, Gaia high-mass star census and IGIMF predictions  
  > "an unusually low $^{18}$O/$^{17}$O ratio indicates chemical enrichment dominated by low- and intermediate-mass stellar populations, with little contribution from massive stars" (Discussion)
   - assumption: SMC ISM is well mixed so LIRS 36 may be representative (not established)  
  > "In the SMC, large-scale mixing of nucleosynthetic products may also be expected, although this remains less well constrained." (Discussion)
   - fitting: _not stated_
   - validation: Consistency with Gaia high-mass-star deficit and low SMC star formation history  
  > "The low $^{18}$O/$^{17}$O ratio that we measure is in line with this prediction" (Discussion)

## Software

- **CASA** 6.5.4 (imaging): ALMA pipeline calibration, tclean imaging, feather combination  
  > "Subsequent imaging of the calibrated data was performed manually with CASA version 6.5.4." (Observations and data reduction)
- **tclean** : image reconstruction (Hogbom, Briggs, auto-multithresh)  
  > "The image reconstruction was carried out using the" (Observations and data reduction)
- **feather** : combining TP and ACA data  
  > "The combination of the single-dish and ACA datasets was performed using the" (Observations and data reduction)
- **Weeds (CLASS extension of GILDAS)** : LTE spectral modelling  
  > "we use the CLASS extension Weeds for the LTE spectral modeling (cite: 2011A&A...526A..47M)" (Local thermodynamic equilibrium)
- **GILDAS** : _not stated_
- **emcee** : MCMC fitting of Tex and column densities  
  > "which applies the affine-invariant ensemble sampler (cite: 2010CAMCS...5...65G) within a Markov chain Monte Carlo (MCMC) framework." (Local thermodynamic equilibrium)
- **astropy** : _not stated_
- **NumPy** : _not stated_
- **SciPy** : _not stated_
- **Matplotlib** : _not stated_

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 18O/17O abundance ratio in LIRS 36 (SMC) | 0.87 | +/-0.26 | dimensionless | 6 | Neglecting the beam dilution effects, we obtain $^{13}$C/$^{18}$O=109.3$\pm$35.6, $^{13}$C/$^{17}$O=95.2$\pm$31.4, and $^{18}$O/$^{17}$O=0.87$\pm$0.26. |
| 13C/18O abundance ratio | 109.3 | +/-35.6 | dimensionless | 6 | Neglecting the beam dilution effects, we obtain $^{13}$C/$^{18}$O=109.3$\pm$35.6, $^{13}$C/$^{17}$O=95.2$\pm$31.4, and $^{18}$O/$^{17}$O=0.87$\pm$0.26. |
| 13C/17O abundance ratio | 95.2 | +/-31.4 | dimensionless | 6 | Neglecting the beam dilution effects, we obtain $^{13}$C/$^{18}$O=109.3$\pm$35.6, $^{13}$C/$^{17}$O=95.2$\pm$31.4, and $^{18}$O/$^{17}$O=0.87$\pm$0.26. |
| 16O/18O lower limit | >~444 | lower limit | dimensionless | 6 | yield only lower limits of $^{16}$O/$^{18}$O$\gtrsim$444 and $^{16}$O/$^{17}$O$\gtrsim$386, respectively. |
| 16O/17O lower limit | >~386 | lower limit | dimensionless | 6 | yield only lower limits of $^{16}$O/$^{18}$O$\gtrsim$444 and $^{16}$O/$^{17}$O$\gtrsim$386, respectively. |
| 13CO/C18O integrated intensity ratio | 90 | +/-5 | dimensionless | 3 | The integrated intensity ratio of $^{13}$CO/C$^{18}$O is 90$\pm$5 |
| Excitation temperature (f=1) | 18.4 | +/-3.0 | K | 5 | Our approach results in $T_{\rm ex}$=18.4$\pm$3.0 K |
| 13CO column density (f=1) | 5.9e15 | +/-1.5e15 | cm^-2 | 5 | $N_{^{13}{\rm CO}}$=(5.9$\pm$1.5)$\times 10^{15}$ cm$^{-2}$ |
| C18O column density (f=1) | 5.4e13 | +/-1.1e13 | cm^-2 | 5 | $N_{{\rm C^{18}O}}$=(5.4$\pm$1.1)$\times 10^{13}$ cm$^{-2}$ |
| C17O column density (f=1) | 6.2e13 | +/-1.3e13 (appendix text) or +/-1.5e13 (Table 2) | cm^-2 | 5 | $N_{{\rm C^{17}O}}$=(6.2$\pm$1.3)$\times 10^{13}$ cm$^{-2}$ |
| 13CO peak optical depth | 0.34 | +/-0.02 | dimensionless | 4 | we derive a peak optical depth of 0.34$\pm$0.02 for $^{13}$CO $J=2\to 1$ |
| Excitation temperature (f=0.34, source size 5.4 arcsec) | 46.5 | +/-8.2 | K | 7 | The physical parameters change to $T_{\rm ex}$=46.5$\pm$8.2 K |
| 18O/17O ratio with source size 5.4 arcsec | 0.88 | +/-0.29 | dimensionless | 7 | 0.88$\pm$0.29 |
| C18O J=2-1 integrated intensity | 0.099 | +/-0.005 | K km/s | 3 | 0.099$\pm$0.005 |
| C17O J=2-1 integrated intensity | 0.114 | +/-0.002 | K km/s | 3 | 0.114$\pm$0.002 |
| C17O J=2-1 detection significance | >10 | not stated | dimensionless (S/N) | 1 | the C$^{17}$O $J=2\to1$ transition is detected with a signal-to-noise ratio of $>$10 |

## Qualitative findings

- First detection of C17O in the SMC; first instance of C17O integrated intensity exceeding C18O in molecular clouds  
  > "To our knowledge, this is the first instance in which C$^{17}$O emission exhibits a higher integrated intensity than C$^{18}$O emission in molecular clouds." (Results)
- SMC 18O/17O is lower than all literature values for molecular clouds in the Milky Way and other galaxies  
  > "The $^{18}$O/$^{17}$O isotope ratio in the SMC is markedly lower than all previously reported values for molecular clouds" (Discussion)
- Top-light IGIMF in the SMC suggested, possibly a general feature of low-metallicity dwarf galaxies  
  > "Our findings imply that such a top-light IGIMF may be a general feature of low-metallicity dwarf galaxies." (Summary and conclusion)

## Claim tuples

- H: C17O can be detected in the SMC, allowing a direct 18O/17O measurement | E: ACA Band 6 observations of 12CO, 13CO, C18O, C17O J=2-1 toward LIRS 36, spectra at the 13CO peak | R: C17O detected at S/N >10; 18O/17O = 0.87+/-0.26 | F: First solid C17O detection and first direct 18O/17O in the SMC | **supported**
- H: The SMC 18O/17O ratio differs from other galaxies and Milky Way clouds | E: Compare the measured ratio with literature values (Table 3) | R: 0.87+/-0.26 vs 1.7 (LMC), 3.4-5.5 (Milky Way), >=6.4 (other galaxies in table) | F: SMC ratio is lower than all previous molecular-cloud values | **supported**
- H: Chemical enrichment in the SMC is dominated by low-mass stars, consistent with a top-light IGIMF | E: Interpret low 18O/17O and high 13CO/C18O with nucleosynthesis, Gaia high-mass star census and low SFR history | R: Low 18O/17O together with high 13CO/C18O | F: Enrichment dominated by low-mass stars; SMC governed by a top-light IGIMF | **partially**
- H: The derived isotope ratios are robust against assumed source size and missing flux | E: Re-run MCMC with source size 5.4 arcsec; compare ACA-only vs ACA+TP flux | R: Ratios unchanged (18O/17O 0.88 vs 0.87) while Tex and N change; C18O and C17O missing flux negligible at the peak | F: Isotope ratios are robust | **supported**

## Reasoning

- Why this data: LIRS 36 is the brightest 13CO J=3-2 position in the APEX SMC survey, so it has the highest 13CO column density on the surveyed scale, making it best for rare isotopologues  
  > "Therefore, we selected LIRS 36 as the target to search for rare CO isotopologues." (Observations and data reduction)
- Why this method: Optically thin C18O and C17O transitions give 18O/17O directly; oxygen isotopes are not fractionated and isotope-selective photodissociation affects both similarly  
  > "the $^{18}$O/$^{17}$O isotope ratios can be directly determined by the optically thin transitions of C$^{18}$O and C$^{17}$O" (Introduction)
- Alternative: Isotope-selective photodissociation dismissed as unlikely to affect the ratios significantly  
  > "Isotope-selective photodissociation is unlikely to significantly affect these ratios" (Introduction)
- Alternative: Beam dilution f=0.34 tested as an alternative to f=1; isotope ratios unchanged  
  > "In order to test the impact of the assumed source size on the derived isotope ratios, the MCMC approach was performed again by assuming" (Local thermodynamic equilibrium)
- How they decided it was enough: _not stated_
- Limitation (authors): Single sightline/cloud; representativeness for the whole SMC unknown  
  > "but establishing whether it is representative on a global scale will require future studies with larger samples." (Discussion)
- Limitation (authors): 12CO shows moderate missing flux in ACA-only data  
  > "emphasizing the need for total power data to accurately determine its brightness temperatures" (Short spacing)
- Limitation (authors): Single Gaussian component assumed for simplicity; 12CO optical depth leads only to lower limits on 16O/18O and 16O/17O  
  > "we assume a single Gaussian component for all molecules for simplicity" (Local thermodynamic equilibrium)
- Caveat (inferred, ours): Single source and single sightline; 18O/17O result rests on one C17O line with hyperfine blending and an ad hoc FWHM assumption
- Caveat (inferred, ours): Equal Tex for all isotopologues and a single-component LTE model are assumed; 12CO-derived Tex may not apply to the optically thin lines
- Caveat (inferred, ours): Inconsistencies in the text: Tex 18.6 K (Results) vs 18.4 K (Table 2 and appendix); C17O column uncertainty 1.5e13 (Table 2) vs 1.3e13 (appendix)
- Caveat (inferred, ours): C18O and C17O taken from ACA-only data; missing flux for them is argued, not measured (TP did not detect C18O)
- Caveat (inferred, ours): Interpretation to a galaxy-wide IGIMF extrapolates from one cloud; alternative sources (novae, AGB yields at low Z) not quantitatively tested

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Explicit statement that the ACA and TP data are public; no data-release or product link is given
- Missing: tclean threshold, niter, image size and auto-multithresh parameter values (given only by citation)
- Missing: Continuum subtraction and line-free channel choice
- Missing: Feather parameters and TP processing details
- Missing: MCMC prior ranges, burn-in length, how sigma_i was set, hyperfine treatment of C17O in Weeds
- Missing: No code or fitting scripts released
- Data volume (inferred): Roughly 20-60 GB of raw ACA Band 6 data (~60 h, 16 spws, two setups) plus a few GB of TP data, if the archive products are re-imaged; the derived spectra themselves are tiny
- Score (inferred): 3/5, ALMA project codes, calibrators, CASA version, robust and key imaging choices and the MCMC recipe are given with numeric results, but masking parameters are by reference, there is no line-free/continuum-subtraction or feather detail, and no code is released.
- Rediscovery candidate: yes, Both project codes are given and the main results are numeric (18O/17O = 0.87+/-0.26) from peak spectra and a simple LTE MCMC; public availability is not stated in the paper (inferred from ALMA archive norms), and some imaging and fit details would need to be reconstructed.

## Links

- Method: (cite: 2020PASP..132b4505K) (AUTO-MULTITHRESH masking parameters used in tclean)
- Method: (cite: 2011A&A...526A..47M) (Weeds extension of CLASS used for LTE modelling)
- Method: (cite: 2013PASP..125..306F) (emcee sampler)
- Method: (cite: 2015PASP..127..266M) (Radiative transfer equation used for LTE column densities)
- Method: (cite: 2022PASP..134k4501C) (CASA and its ALMA pipeline)
- Companion: (cite: 2017ApJ...844...98M) (ALMA 13CO/C18O ratios in SMC N83C, compared with this work)
- Companion: (cite: 2018Natur.558..260Z) (ALMA detection of high 13CO/C18O intensity ratios in the SMC and related IGIMF work)
- Companion: (cite: 2009ApJ...690..580W) (LMC 18O/17O ratio used for comparison)
- Companion: (cite: 2023AA...670A..98Y) (Milky Way oxygen isotope ratio gradient used for comparison)
- Related: APEX 12CO and 13CO J=3-2 SMC survey (C.-H. Rosie Chen, in prep.)
- Related: ALMA project 2015.1.00196.S (TP observations, PI Julia Roman-Duval)

## Checks

```json
{
 "quotes": 138,
 "quotes_ok": 138,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 16,
 "numeric_problems": 0,
 "fill": {
  "facts": 116,
  "stated": 92,
  "rate": 0.793
 },
 "evidence_ok": true
}
```

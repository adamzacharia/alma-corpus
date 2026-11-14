# The TW Hya Rosetta Stone Project IV: A Hydrocarbon-rich Disk Atmosphere

`2021ApJ...911...29C` | The Astrophysical Journal 2021 | first author: Cleeves, L. Ilsedore | arXiv: 2102.09577 | DOI: 10.3847/1538-4357/abe862

Card schema 1.0 | model gemini-4-argon | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Spatially constrain the radial and vertical location, abundance, and ortho-to-para ratio of the c-C3H2 hydrocarbon layer in the TW Hya protoplanetary disk to improve the interpretation of the disk's C/O ratio.  
  > "The present paper uses multi-line observations of $c-$C$_3$H$_2$ to better spatially constrain the nature of the hydrocarbon layer in the TW Hya protoplanetary disk, with the goal of improving our interpretation of the C/O ratio(s) of this disk." (Introduction); "From this multi-line data set of $c-$C$_3$H$_2$ rotational transitions spanning upper state energies from 29.1 K to 96.5 K, we aim to use excitation to constrain the location of the hydrocarbon layer in the TW Hya disk." (Methods)
- Target **TW Hya**: coordinates _not stated_; z/distance 59.5 pc  
  > "We assume a distance of 59.5 pc (cite: GAIA16)." (Images and Radial Integrated Flux Profiles); "The source velocity was assumed to be 2.84 km s$^{-1}$." (Images and Radial Integrated Flux Profiles); distance from (cite: GAIA16)  
  > "We assume a distance of 59.5 pc (cite: GAIA16)." (Images and Radial Integrated Flux Profiles); "The source velocity was assumed to be 2.84 km s$^{-1}$." (Images and Radial Integrated Flux Profiles)

## Data provenance

- ALMA projects: 2016.1.00311.S, 2013.1.00198.S, 2013.1.00114.S
- bands: _not stated_
- frequencies and spectral setup: 227.16913 GHz to 352.19364 GHz; channel widths 0.16 km/s and 0.21 km/s  
  > "| $4_{3,2} - 3_{2,1}$ | o | 227.16913 | 3.113E-04 | 29.07 | 0.16 | 3.2 | $80 \pm 5$ | 1 |" (Table 1); "| $8_{3 , 6} - 7_{2 , 5}$ | o | 352.19364 | 1.734E-03 | 86.93 | 0.21 | 4.2 | $220 \pm 30$ | 3 |" (Table 1)
- continuum bandwidth: _not stated_
- arrays: 40 antennas (for 2016.1.00311.S)  
  > "The observations from 2016.1.00311.S were carried out with 40 antennas on April 8, 2017 (C40-2; 15m – 390m baselines) and May 21, 2017 (C40-5; 15m – 1124m baselines)." (ALMA Observations)
- configurations: C40-2 and C40-5 (for 2016.1.00311.S)  
  > "The observations from 2016.1.00311.S were carried out with 40 antennas on April 8, 2017 (C40-2; 15m – 390m baselines) and May 21, 2017 (C40-5; 15m – 1124m baselines)." (ALMA Observations)
- baselines: 15m – 390m (C40-2) and 15m – 1124m (C40-5)  
  > "The observations from 2016.1.00311.S were carried out with 40 antennas on April 8, 2017 (C40-2; 15m – 390m baselines) and May 21, 2017 (C40-5; 15m – 1124m baselines)." (ALMA Observations)
- angular resolution: typically 0.2'' - 0.4'' native, homogenized to 0.5'' round beam (15-20 au)  
  > "We present resolved $c-$C$_3$H$_2$ observations from the TW Hya Rosetta Stone Project, a program designed to map the chemistry of common molecules at $15-20$ au resolution in the TW Hya disk." (Abstract); "The mask is convolved with the respective beam for each data set (typically between $0.2\ensuremath{''} - 0.4\ensuremath{''}$)." (Images and Radial Integrated Flux Profiles); "Finally, we take the cleaned image and apply the CASA task imsmooth, which operates in the image plane, to create a final image with an exactly $0.5\ensuremath{''}$ round beam." (Images and Radial Integrated Flux Profiles)
- max recoverable scale: _not stated_
- sensitivity: 2.9 to 5.3 mJy/beam in a 0.5'' beam  
  > "| $5_{5 , 1} - 4_{4 , 0}$ | p | 338.20399 | 1.598E-03 | 48.78 | 0.21 | 5.3 | $140 \pm 16$ | 3 |" (Table 1); "| $10_{1,10} - 9_{0, 9}$ | o (bl) | 351.78157 | 2.439E-03 | 96.50 | 0.21 | 2.9 | $330 \pm 15$ | 2,3 |" (Table 1)
- time on source: _not stated_
- observing dates: April 8, 2017 and May 21, 2017 (for 2016.1.00311.S)  
  > "The observations from 2016.1.00311.S were carried out with 40 antennas on April 8, 2017 (C40-2; 15m – 390m baselines) and May 21, 2017 (C40-5; 15m – 1124m baselines)." (ALMA Observations)
- pi or archival as stated: PI: Cleeves (2016.1.00311.S) augmented by archival observations from 2013.1.00198.S (PI: Bergin) and 2013.1.00114.S (PI: Öberg)  
  > "We present new observations of $c-$C$_3$H$_2$ taken as part of the TW Hya as a Chemical Rosetta Stone Program (PI: Cleeves, 2016.1.00311.S), augmented by archival observations from 2013.1.00198.S (PI: Bergin) and 2013.1.00114.S (PI: Öberg)." (ALMA Observations)
- Line: o-c-C3H2 4_{3,2} - 3_{2,1} (227.16913 GHz)
- Line: o-c-C3H2 7_{3,4} - 6_{4,3} (351.52327 GHz)
- Line: o-c-C3H2 8_{3,6} - 7_{2,5} (352.19364 GHz)
- Line: p-c-C3H2 5_{5,1} - 4_{4,0} (338.20399 GHz)
- Line: p-c-C3H2 8_{2,6} - 7_{3,5} (352.18551 GHz)
- Line: o-c-C3H2 9_{1,8} - 8_{2,7} (351.96593 GHz)
- Line: p-c-C3H2 9_{2,8} - 8_{1,7} (351.96594 GHz)
- Line: o-c-C3H2 10_{1,10} - 9_{0,9} (351.78157 GHz)
- Line: p-c-C3H2 10_{0,10} - 9_{1,9} (351.78157 GHz)
- External data: Line catalogue data (frequencies, Einstein A coefficients, upper state energies)  
  > "Table notes: $^{a}$ Line catalogue data from CDMS (cite: Muller05)" (Table 1) [from CDMS (cite: Muller05)]
- External data: Collisional rate coefficients for ortho and para c-C3H2  
  > "We adopt the collisional rate coefficients hosted on the Leiden LAMDA database (cite: Schoier05) originally computed in (cite: chandra2000) for ortho and para separately." (Methods) [from (cite: Schoier05), (cite: chandra2000)]
- External data: Physical conditions (gas temperature, dust temperature, gas density) of TW Hya disk model  
  > "We approximate the emission from TW Hya as a series of radial annular regions, where the physical conditions as a function of height at each radial location are taken from the (cite: Cleeves15) model of TW Hya." (Methods) [from (cite: Cleeves15)]
- External data: Disk inclination, position angle, and stellar mass  
  > "We assume an inclination of $5^\circ$, a position angle of $152^\circ$, and a stellar mass of 0.8 M$_\odot$ to create the Keplerian mask following (cite: Huang18)." (Images and Radial Integrated Flux Profiles) [from (cite: Huang18)]
- External data: Distance to TW Hya (59.5 pc)  
  > "We assume a distance of 59.5 pc (cite: GAIA16)." (Images and Radial Integrated Flux Profiles) [from (cite: GAIA16)]
- Simulation/model as data: Grid of 7,150 1D non-LTE radiative transfer slab models built on the TW Hya physical structure of (cite: Cleeves15)  
  > "To fit the data, we use a simple slab model method (cite: Qi08; Oberg17) and employ a non-LTE line radiative transfer code based upon Ratran (cite: hogerheijde2000) designed to handle blended transitions and be computationally efficient (https://github.com/ryanaloomis/nLTErt1d)." (Methods); "| Total number of models | 7150 | |" (Table 2)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline followed by phase self-calibration  
  > "All data were calibrated with the ALMA pipeline with CASA version 4.7.0. Prior to imaging, we phase self-calibrated the data using the line-free portions of the continuum, adopting a solution interval of 30s and averaging polarizations." (ALMA Observations)
- casa version: 4.7.0  
  > "All data were calibrated with the ALMA pipeline with CASA version 4.7.0." (ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1058+0133 (April 8, 2017) and J1037-2934 (May 21, 2017); also adjusted 2013.1.00198.S flux by ~10% to match 2016.1.00311.S  
  > "The April 8 observation used J1037-2934 for bandpass and phase calibration, and J1058+0133 for flux calibration. The May 21 observation used J1037-2934 for bandpass, flux, and phase calibration." (ALMA Observations); "The integrated line flux measured between these two programs differed by about 10% (well within the quoted ALMA flux uncertainty), however we adjusted the flux of 2013.1.00198.S to match the flux measured in 2016.1.00311.S flux." (ALMA Observations)
- flux scale uncertainty: _not stated_
- self calibration: Phase self-calibration on line-free continuum, solint=30s, averaging polarizations, spws independent, min SNR=3, min baselines per antenna=6  
  > "Prior to imaging, we phase self-calibrated the data using the line-free portions of the continuum, adopting a solution interval of 30s and averaging polarizations." (ALMA Observations); "In addition, spws were self calibrated independently, and we set a minimum signal to noise ratio of 3 and a minimum number of baselines per antenna of 6." (ALMA Observations)

### Imaging

- task: tclean  
  > "Imaging was carried out using the `tclean` task in a semi-automated fashion described here." (Images and Radial Integrated Flux Profiles)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: line-specific uv-taper applied to create a beam just below 0.5'' on the major axis  
  > "Because we want to have a consistent beam size across all the transitions, which we chose to be $0.5\ensuremath{''}$, we calculate the uv-taper that is necessary to create a beam of just below $0.5\ensuremath{''}$ on the major axis." (Images and Radial Integrated Flux Profiles); "We then clean each line with its respective mask in non-interactive mode down to a noise level of 3$\sigma$ standard deviation, with the line specific uv-taper applied." (Images and Radial Integrated Flux Profiles)
- cell size: _not stated_
- image size: _not stated_
- masking: Keplerian mask convolved with native beam (0.2'' - 0.4''); cleaned down to 3 sigma noise level  
  > "From these data, we create a mask based on expectations from Keplerian motion using the code presented as part of (cite: Pegues2020), see also code reference (cite: jpegues2020code)." (Images and Radial Integrated Flux Profiles); "We then clean each line with its respective mask in non-interactive mode down to a noise level of 3$\sigma$ standard deviation, with the line specific uv-taper applied." (Images and Radial Integrated Flux Profiles)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub in uv-plane assuming a linear fit to the continuum shape  
  > "The continuum was subtracted in the uv-plane using the CASA task `uvcontsub` assuming a linear fit to the continuum shape." (Images and Radial Integrated Flux Profiles)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: CASA task imsmooth applied in image plane to produce an exactly 0.5'' round beam  
  > "Finally, we take the cleaned image and apply the CASA task imsmooth, which operates in the image plane, to create a final image with an exactly $0.5\ensuremath{''}$ round beam." (Images and Radial Integrated Flux Profiles)
- final beam: 0.5'' round beam  
  > "Finally, we take the cleaned image and apply the CASA task imsmooth, which operates in the image plane, to create a final image with an exactly $0.5\ensuremath{''}$ round beam." (Images and Radial Integrated Flux Profiles)
- final rms: 2.9 to 5.3 mJy/beam in 0.5'' beam (at 0.16 or 0.21 km/s channel width)  
  > "$^{b}$ In a $0.5\ensuremath{''}$ beam, with the specified channel width" (Table 1); "| $10_{1,10} - 9_{0, 9}$ | o (bl) | 351.78157 | 2.439E-03 | 96.50 | 0.21 | 2.9 | $330 \pm 15$ | 2,3 |" (Table 1); "| $5_{5 , 1} - 4_{4 , 0}$ | p | 338.20399 | 1.598E-03 | 48.78 | 0.21 | 5.3 | $140 \pm 16$ | 3 |" (Table 1)

### Inherited from earlier work

- Calibration process for archival observations from programs 2013.1.00198.S and 2013.1.00114.S  
  > "The calibration process for the observations from program 2013.1.00198.S and 2013.1.00114.S are reported in (cite: Bergin16) and (cite: Oberg17) and not repeated here." (ALMA Observations) [from (cite: Bergin16) and (cite: Oberg17)]
- Disk geometry and stellar mass for Keplerian masking and deprojection (inclination 5 deg, PA 152 deg, M_* = 0.8 M_sun)  
  > "We assume an inclination of $5^\circ$, a position angle of $152^\circ$, and a stellar mass of 0.8 M$_\odot$ to create the Keplerian mask following (cite: Huang18)." (Images and Radial Integrated Flux Profiles) [from (cite: Huang18)]
- Physical structure of the TW Hya disk (gas temperature, dust temperature, gas density, dust settling factor, total mass 0.04 M_sun)  
  > "We approximate the emission from TW Hya as a series of radial annular regions, where the physical conditions as a function of height at each radial location are taken from the (cite: Cleeves15) model of TW Hya." (Methods); "The gas temperature, dust temperature, and gas density are taken from this model, where the total mass of this TW Hya disk model is 0.04 $M_\odot$." (Methods) [from (cite: Cleeves15)]
- Simple slab model method for molecular emission fitting  
  > "To fit the data, we use a simple slab model method (cite: Qi08; Oberg17) and employ a non-LTE line radiative transfer code based upon Ratran (cite: hogerheijde2000) designed to handle blended transitions and be computationally efficient (https://github.com/ryanaloomis/nLTErt1d)." (Methods) [from (cite: Qi08; Oberg17)]
- Keplerian mask creation procedure  
  > "From these data, we create a mask based on expectations from Keplerian motion using the code presented as part of (cite: Pegues2020), see also code reference (cite: jpegues2020code)." (Images and Radial Integrated Flux Profiles) [from (cite: Pegues2020), (cite: jpegues2020code)]

### Not stated but needed to reproduce (our reading)

- Weighting scheme and robust parameter used in tclean
- Deconvolver algorithm (e.g., hogbom, clark, multiscale) used in tclean
- Pixel cell size and image dimensions used during tclean imaging
- Exact uv-taper values applied to each individual transition
- Line-free channel frequency ranges used for uvcontsub and continuum self-calibration
- Non-thermal linewidth value input to the nLTErt1d radiative transfer code
- Radial annulus width / spacing used in GOFISH extraction and synthetic model profile binning

## Analysis recipe

1. **Calibrate visibilities, align flux scales across programs, subtract continuum, and image c-C3H2 transitions with a uniform 0.5'' beam**: Calibrate with ALMA pipeline, phase self-calibrate on line-free continuum, scale 2013.1.00198.S flux by ~10% to match 2016.1.00311.S, subtract continuum with uvcontsub, clean with tclean using Keplerian masks and line-specific uv-tapers, and smooth to a 0.5'' round beam with imsmooth.  
  > "Prior to imaging, we phase self-calibrated the data using the line-free portions of the continuum, adopting a solution interval of 30s and averaging polarizations." (ALMA Observations); "The integrated line flux measured between these two programs differed by about 10% (well within the quoted ALMA flux uncertainty), however we adjusted the flux of 2013.1.00198.S to match the flux measured in 2016.1.00311.S flux." (ALMA Observations); "Finally, we take the cleaned image and apply the CASA task imsmooth, which operates in the image plane, to create a final image with an exactly $0.5\ensuremath{''}$ round beam." (Images and Radial Integrated Flux Profiles)
   - software: CASA, uvcontsub, tclean, imsmooth, pykepmask
   - parameter: source velocity = 2.84 km s^-1, inclination = 5 deg, PA = 152 deg, M_* = 0.8 M_sun, distance = 59.5 pc  
  > "The source velocity was assumed to be 2.84 km s$^{-1}$." (Images and Radial Integrated Flux Profiles); "We assume an inclination of $5^\circ$, a position angle of $152^\circ$, and a stellar mass of 0.8 M$_\odot$ to create the Keplerian mask following (cite: Huang18). We assume a distance of 59.5 pc (cite: GAIA16)." (Images and Radial Integrated Flux Profiles)
   - parameter: clean threshold = 3 sigma, final beam = 0.5'' round  
  > "We then clean each line with its respective mask in non-interactive mode down to a noise level of 3$\sigma$ standard deviation, with the line specific uv-taper applied." (Images and Radial Integrated Flux Profiles); "Finally, we take the cleaned image and apply the CASA task imsmooth, which operates in the image plane, to create a final image with an exactly $0.5\ensuremath{''}$ round beam." (Images and Radial Integrated Flux Profiles)
   - assumption: Keplerian rotation with inclination 5 deg, PA 152 deg, M_* = 0.8 M_sun at 59.5 pc; linear continuum shape  
  > "The continuum was subtracted in the uv-plane using the CASA task `uvcontsub` assuming a linear fit to the continuum shape." (Images and Radial Integrated Flux Profiles); "We assume an inclination of $5^\circ$, a position angle of $152^\circ$, and a stellar mass of 0.8 M$_\odot$ to create the Keplerian mask following (cite: Huang18). We assume a distance of 59.5 pc (cite: GAIA16)." (Images and Radial Integrated Flux Profiles)
   - fitting: _not stated_
   - validation: Checked overlapping bright 10-9 and 9-8 blended transitions between 2013.1.00198.S and 2016.1.00311.S, finding ~10% flux difference  
  > "The projects 2013.1.00198.S and 2016.1.00311.S had overlapping coverage of the bright 10 – 9 and 9 – 8 blends (see Table 1). The integrated line flux measured between these two programs differed by about 10% (well within the quoted ALMA flux uncertainty), however we adjusted the flux of 2013.1.00198.S to match the flux measured in 2016.1.00311.S flux." (ALMA Observations)
2. **Extract azimuthally stacked, spectrally integrated radial intensity profiles and total integrated line fluxes**: Measure integrated line fluxes within Keplerian masks; use GOFISH on the cleaned 0.5'' image cubes to spectrally align and azimuthally stack spectra by deprojecting Keplerian rotation, then integrate over velocity to get radial profiles.  
  > "Measured within a Keplerian mask" (Table 1 notes); "GOFISH works in the image plane to spectrally align spectra at a given radius by taking into account the projected disk rotation, such that the spectra can be stacked, thereby creating a higher signal-to-noise ratio radial intensity profile." (Images and Radial Integrated Flux Profiles); "After shifting and stacking the azimuthal emission, we integrate over a conservative velocity range of 2.5 km s$^{-1}$ to 3.18 km s$^{-1}$ and obtain the profiles shown in Figure 2." (Images and Radial Integrated Flux Profiles)
   - software: GOFISH
   - parameter: velocity integration range = 2.5 km s^-1 to 3.18 km s^-1  
  > "After shifting and stacking the azimuthal emission, we integrate over a conservative velocity range of 2.5 km s$^{-1}$ to 3.18 km s$^{-1}$ and obtain the profiles shown in Figure 2." (Images and Radial Integrated Flux Profiles)
   - assumption: Same disk geometry and stellar mass as Keplerian masking (inclination 5 deg, PA 152 deg, M_* = 0.8 M_sun, d = 59.5 pc)  
  > "We assume the same disk parameters as for the Keplerian masking above to carry out the GOFISH deprojection." (Images and Radial Integrated Flux Profiles)
   - fitting: _not stated_
   - validation: Faint para transitions show clearer ring-like structure in GOFISH profiles with peak detected at >= 3-4 sigma  
  > "Note that even though the para transitions are faint in the moment-0 maps in Figure 1, the ring-like structure becomes clearer in the GOFISH extraction and the peak of the resolved profile is detected at $\ge 3 - 4 \sigma$." (Images and Radial Integrated Flux Profiles)
3. **Fit observed radial intensity profiles with a grid of 1D non-LTE radiative transfer slab models**: Run a 7,150-model grid of 1D non-LTE radiative transfer slab models (nLTErt1d) over radial annuli using the Cleeves et al. (2015) TW Hya physical structure, reconstruct 2D sky images, convolve with a 0.5'' Gaussian beam, extract radial profiles in matching annuli, and evaluate reduced chi^2.  
  > "To fit the data, we use a simple slab model method (cite: Qi08; Oberg17) and employ a non-LTE line radiative transfer code based upon Ratran (cite: hogerheijde2000) designed to handle blended transitions and be computationally efficient (https://github.com/ryanaloomis/nLTErt1d)." (Methods); "To create the synthetic integrated radial intensity profile for each model, we reconstruct a 2D sky image of the velocity integrated line brightness and convolve the image with a Gaussian $0.5\ensuremath{''}$ beam." (Methods); "Goodness of fit is assessed based on a reduced $\chi^2$ between the beam-convolved model spectrally integrated intensity profile and the data." (Methods)
   - software: nLTErt1d
   - parameter: Min H2 column = 10^19 cm^-2; Max H2 column = (1 to 187.5) x 10^21 cm^-2; chi(c-C3H2) = (1 to 1000) x 10^-11 per H; OPR = 1, 3; R_inner = 20, 25, 30, 35, 40 au; R_outer = 80, 90, 100, 110, 120 au; Total models = 7150  
  > "| Min H$_2$ Column | $10^{19}$ | cm$^{-2}$ |" (Table 2); "| OPR | 1, 3 | n/a | | $R_{\rm inner}$ $c-$C$_3$H$_2$ | 20, 25, 30, 35, 40 | au | | $R_{\rm outer}$ $c-$C$_3$H$_2$ | 80, 90, 100, 110, 120 | au | | Total number of models | 7150 | |" (Table 2)
   - assumption: Physical structure from Cleeves et al. (2015) with disk mass 0.04 M_sun and 6.7x reduced small grains in the surface (1 A_V = 1.27 x 10^22 cm^-2 N_H2); constant c-C3H2 abundance within the slab; LAMDA collisional rates from Chandra & Kegel (2000)  
  > "The gas temperature, dust temperature, and gas density are taken from this model, where the total mass of this TW Hya disk model is 0.04 $M_\odot$." (Methods); "But since our model has 6.7$\times$ less small grains in the surface of the disk due to the formation and subsequent settling of larger grains, then $1~ A_{ V}$ occurs at $N_{\rm H_2} = 1.27\times10^{22}$ cm$^{-2}$." (Methods); "We adopt the collisional rate coefficients hosted on the Leiden LAMDA database (cite: Schoier05) originally computed in (cite: chandra2000) for ortho and para separately." (Methods)
   - fitting: Grid search over 7,150 models assessed via reduced chi^2 summed over annuli and all transitions equally, selecting the 30 lowest chi^2 models  
  > "To estimate $\chi^2$, the flux in a given annulus for the data and model are measured per beam, and we sum the square of the difference divided by the observed RMS uncertainty." (Methods); "To provide an even clearer picture of our best fit models, we extract the 30 models with the lowest $\chi^2$ from our grid and plot a histogram of the model parameters (see Figure 5)." (Fiducial Model Results)
   - validation: Tested +/- 10% flux scaling on the 4_{3,2}-3_{2,1} line and varying minimum H2 column between 10^19 and 10^20 cm^-2; neither changed the best-fit models  
  > "We therefore have also examined our best fit models from the profiles as extracted directly from GOFISH, and then with a 10% uniform increase and decrease on just the $4_{3,2} - 3_{2,1}$, with the rest of the lines fixed. We do not find a change in the best fit models, in part since we have two other ortho lines." (Methods); "Initially, we also varied the minimum column density of the layer, but since we did not see a significant change between changing the upper boundary from $N_{\rm H_2} = 1\times10^{19}$ cm$^{-2}$ to $1\times10^{20}$ cm$^{-2}$, we decided to fix the upper boundary for the full grid of simulations to the former value of $1\times10^{19}$ cm$^{-2}$" (Methods)
4. **Confirm ortho-to-para ratio via disk-averaged rotational diagram analysis**: Perform a disk-averaged rotational diagram analysis using the unblended, optically thin ortho and para transitions to independently derive rotational temperatures and column densities.  
  > "To confirm this result, we have done an additional disk-averaged rotational diagram analysis using the unblended ortho and para transitions, which are also optically thin based on our model comparisons." (The ortho-to-para ratio of $c-$C$_3$H$_2$ is consistent with a constant value of 3); "Figure 7 shows the results of the fitting, and we find that the ortho and para lines have consistent rotational temperatures, and the derived ortho-to-para ratio from the column densities is $3.02\pm0.78$." (The ortho-to-para ratio of $c-$C$_3$H$_2$ is consistent with a constant value of 3)
   - assumption: Unblended ortho and para transitions are optically thin and in LTE  
  > "To confirm this result, we have done an additional disk-averaged rotational diagram analysis using the unblended ortho and para transitions, which are also optically thin based on our model comparisons." (The ortho-to-para ratio of $c-$C$_3$H$_2$ is consistent with a constant value of 3)
   - fitting: Rotational diagram fit to unblended ortho and para transitions  
  > "Figure 7 shows the results of the fitting, and we find that the ortho and para lines have consistent rotational temperatures, and the derived ortho-to-para ratio from the column densities is $3.02\pm0.78$." (The ortho-to-para ratio of $c-$C$_3$H$_2$ is consistent with a constant value of 3)
   - validation: Consistent with the non-LTE slab model grid result favoring OPR = 3  
  > "Via the non-LTE fitting we find that the ortho-to-para ratio across the slab can be well reproduced with a single value of 3, however we only consider values of 1 or 3 in our grid. To confirm this result, we have done an additional disk-averaged rotational diagram analysis using the unblended ortho and para transitions, which are also optically thin based on our model comparisons." (The ortho-to-para ratio of $c-$C$_3$H$_2$ is consistent with a constant value of 3)

## Software

- **CASA** 4.7.0: ALMA pipeline calibration, phase self-calibration, continuum subtraction (uvcontsub), imaging (tclean), and image smoothing (imsmooth)  
  > "All data were calibrated with the ALMA pipeline with CASA version 4.7.0." (ALMA Observations); "The continuum was subtracted in the uv-plane using the CASA task `uvcontsub` assuming a linear fit to the continuum shape. Imaging was carried out using the `tclean` task in a semi-automated fashion described here." (Images and Radial Integrated Flux Profiles); "Finally, we take the cleaned image and apply the CASA task imsmooth, which operates in the image plane, to create a final image with an exactly $0.5\ensuremath{''}$ round beam." (Images and Radial Integrated Flux Profiles)
- **pykepmask** v2.0.0: Creating Keplerian masks for cleaning and flux integration  
  > "From these data, we create a mask based on expectations from Keplerian motion using the code presented as part of (cite: Pegues2020), see also code reference (cite: jpegues2020code)." (Images and Radial Integrated Flux Profiles); "(ref: jpegues2020code) jpegues. 2020, jpegues/kepmask: Python Package: pykepmask v2.0.0, vv2.0.0, Zenodo, doi:10.5281/zenodo.3672187. <https://doi.org/10.5281/zenodo.3672187>" (References)
- **GOFISH** : Deprojecting, spectrally aligning, and azimuthally stacking line emission in the image plane to extract high-SNR radial intensity profiles  
  > "We do not use these moment-0 maps for analysis, showing them here to illustrate the detection significance, and instead we apply the GOFISH package (cite: gofish) to improve the signal to noise of the radial profile for each transition." (Images and Radial Integrated Flux Profiles)
- **nLTErt1d** : 1D non-LTE line radiative transfer modeling based upon Ratran, including handling blended transitions  
  > "To fit the data, we use a simple slab model method (cite: Qi08; Oberg17) and employ a non-LTE line radiative transfer code based upon Ratran (cite: hogerheijde2000) designed to handle blended transitions and be computationally efficient (https://github.com/ryanaloomis/nLTErt1d)." (Methods)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Integrated flux of o-c-C3H2 4_{3,2} - 3_{2,1} (227.16913 GHz) | 80 | 5 | mJy km/s | 2 | / $4_{3,2} - 3_{2,1}$ / o / 227.16913 / 3.113E-04 / 29.07 / 0.16 / 3.2 / $80 \pm 5$ / 1 / |
| Integrated flux of o-c-C3H2 7_{3,4} - 6_{4,3} (351.52327 GHz) | 237 | 13 | mJy km/s | 2 | / $7_{3 , 4} - 6_{4 , 3}$ / o / 351.52327 / 1.237E-03 / 77.24 / 0.21 / 3.4 / $237 \pm 13$ / 2 / |
| Integrated flux of o-c-C3H2 8_{3,6} - 7_{2,5} (352.19364 GHz) | 220 | 30 | mJy km/s | 2 | / $8_{3 , 6} - 7_{2 , 5}$ / o / 352.19364 / 1.734E-03 / 86.93 / 0.21 / 4.2 / $220 \pm 30$ / 3 / |
| Integrated flux of p-c-C3H2 5_{5,1} - 4_{4,0} (338.20399 GHz) | 140 | 16 | mJy km/s | 2 | / $5_{5 , 1} - 4_{4 , 0}$ / p / 338.20399 / 1.598E-03 / 48.78 / 0.21 / 5.3 / $140 \pm 16$ / 3 / |
| Integrated flux of p-c-C3H2 8_{2,6} - 7_{3,5} (352.18551 GHz) | 96 | 15 | mJy km/s | 2 | / $8_{2 , 6} - 7_{3 , 5}$ / p / 352.18551 / 1.735E-03 / 86.93 / 0.21 / 4.3 / $96 \pm 15$ / 3 / |
| Integrated flux of blended o/p-c-C3H2 9_{1,8}-8_{2,7} and 9_{2,8}-8_{1,7} (351.96593/4 GHz) | 398 | 14 | mJy km/s | 2 | / $9_{1,8} - 8_{2, 7}$ / o (bl) / 351.96593 / 2.117E-03 / 93.34 / 0.21 / 2.9 / $398 \pm 14$ / 2,3 / |
| Integrated flux of blended o/p-c-C3H2 10_{1,10}-9_{0,9} and 10_{0,10}-9_{1,9} (351.78157 GHz) | 330 | 15 | mJy km/s | 2 | / $10_{1,10} - 9_{0, 9}$ / o (bl) / 351.78157 / 2.439E-03 / 96.50 / 0.21 / 2.9 / $330 \pm 15$ / 2,3 / |
| Best-fit total abundance of c-C3H2 (both isomers) | (7.5-10)e-11 | not stated | per H atom | 3 | We find the ortho-to-para ratio of $c-$C$_3$H$_2$ is consistent with 3 throughout extent of the emission, and the total abundance of both $c-$C$_3$H$_2$ isomers is $(7.5-10)\times10^{-11}$ per H atom, or $1-10$% of the previously published $\rm C_2H$ abundance in the same source.; The best fit models have similar characteristics, and abundance of $(7.5-10) \times 10^{-11}$ per H atom, and extend down to an H$_2$ column density of approximately $2\pm0.5 \times 10^{22}$ cm$^{-2}$. |
| Maximum H2 column density depth of best-fit c-C3H2 slab (N_max) | 2e22 | 0.5e22 | cm^-2 | 3 | The best fit models have similar characteristics, and abundance of $(7.5-10) \times 10^{-11}$ per H atom, and extend down to an H$_2$ column density of approximately $2\pm0.5 \times 10^{22}$ cm$^{-2}$. |
| Column density of c-C3H2 in the slab (30 best-fit models) | (1-3)e12 | not stated | cm^-2 | 3 | To test how much of the spread is due to the degeneracy between the thickness of the layer and the abundance, we also show in Figure 5 a histogram of the product of $\chi_{\rm c-C_3H_2}$ and $N_{\rm max}$ and find that this distribution is much tighter, and corresponds to an approximate column density of $c-$C$_3$H$_2$ in the slab of $(1-3) \times 10^{12}$ cm$^{-2}$. |
| Vertical location (z/r) of c-C3H2 layer | 0.25 to 0.4 | not stated | dimensionless | 3 | We find $c-$C$_3$H$_2$ comes from a layer near the surface that extends no deeper than $z/r=0.25$.; While this lower boundary does not directly correspond to a normalized height value of $z/r$ due to the nature of the assumed density profile (a power-law with an exponential taper), we can say that within the radial boundaries of the emission, that the $c-$C$_3$H$_2$ arises above a $z/r$ value of approximately 0.25 based upon Figure 3, and no higher than 0.4. |
| Inner radius of c-C3H2 ring (R_inner) | 25 - 30 | not stated | au | 3 | Based on this sub-selection of models, an inner radius of 25 or 30 au is favored by 2/3 of the 30 models.; The inner edge of the $c-$C$_3$H$_2$ distribution (25 – 30 au) is consistent with the CO snow line (cite: Qi13c; Zhang17) and/or the dip in CO emission (cite: Huang18) and scattered light (cite: debes2013; vanBoekel16). |
| Outer radius of c-C3H2 ring (R_outer) | 110 - 120 | not stated | au | 3 | Nearly all of the best fit models have an outer radius of $c-$C$_3$H$_2$ at $>100$ au, with 110 au favored slightly over 120 au.; The outer edge of $c-$C$_3$H$_2$ is located at 110 – 120 au. |
| Ortho-to-para ratio of c-C3H2 from rotational diagram | 3.02 | 0.78 | dimensionless | 4 | Figure 7 shows the results of the fitting, and we find that the ortho and para lines have consistent rotational temperatures, and the derived ortho-to-para ratio from the column densities is $3.02\pm0.78$. |

## Qualitative findings

- c-C3H2 emission in TW Hya has a ring-like morphology bounded between R_inner = 25-30 au and R_outer = 110-120 au, and resides in the upper warm molecular layer at z/r between ~0.25 and 0.4 (extending down to A_V ~ 1-2).  
  > "While this lower boundary does not directly correspond to a normalized height value of $z/r$ due to the nature of the assumed density profile (a power-law with an exponential taper), we can say that within the radial boundaries of the emission, that the $c-$C$_3$H$_2$ arises above a $z/r$ value of approximately 0.25 based upon Figure 3, and no higher than 0.4." ($c-$C$_3$H$_2$ is located in and above the warm molecular layer in a ring); "The inner edge of the $c-$C$_3$H$_2$ distribution (25 – 30 au) is consistent with the CO snow line (cite: Qi13c; Zhang17) and/or the dip in CO emission (cite: Huang18) and scattered light (cite: debes2013; vanBoekel16)." ($c-$C$_3$H$_2$ is located in and above the warm molecular layer in a ring); "The outer edge of $c-$C$_3$H$_2$ is located at 110 – 120 au." ($c-$C$_3$H$_2$ is located in and above the warm molecular layer in a ring)
- The rotational emission of c-C3H2 is thermalized (well approximated by LTE), indicating H2 gas densities > 10^6 cm^-3 at high altitudes (z/r > 0.25) between 25 and 110 au.  
  > "We conclude that the $c-$C$_3$H$_2$ appears to be reasonably well approximated by LTE. The critical density for the transitions observed is typically around $10^6$ cm$^{-3}$, and our results suggest there remains a substantial amount of H$_2$ gas, $>10^6$ cm$^{-3}$, at high ($z/r > 0.25$) altitudes and moderately far out radii (25 – 110 au), consistent with disk mass estimates provided by HD for this source (cite: Bergin13; Favre13; Cleeves15; Trapman2019; Calahan20)." (The rotational emission of $c-$C$_3$H$_2$ appears to be thermalized)
- The abundance of c-C3H2 relative to C2H (~1-10% or 3-30%) is consistent with gas-phase chemical models with elevated C/O driven by volatile oxygen removal into large settling grains.  
  > "Taking our best fit model abundances of $c-$C$_3$H$_2$ and comparing it to the results of (cite: Bergin16) for C$_2$H in TW Hya, we find $c-$C$_3$H$_2$’s abundance is $\sim 3-30\%$ that of C$_2$H. If instead we use the column density, for (cite: Bergin16)’s C/O = 1 model, the $c-$C$_3$H$_2$ to C$_2$H ratio is approximately 10%." (The abundance of $c-$C$_3$H$_2$ relative to C$_2$H is consistent with gas-phase chemical models)
- The ortho-to-para ratio of c-C3H2 is consistent with 3 across the emitting region.  
  > "We find the ortho-to-para ratio of $c-$C$_3$H$_2$ is consistent with 3 throughout extent of the emission, and the total abundance of both $c-$C$_3$H$_2$ isomers is $(7.5-10)\times10^{-11}$ per H atom, or $1-10$% of the previously published $\rm C_2H$ abundance in the same source." (Abstract)

## Claim tuples

- H: Multi-line observations of c-C3H2 spanning E_u = 29 to 97 K can break excitation degeneracies and localize the vertical and radial extent of the hydrocarbon layer in the TW Hya disk. | E: Extract azimuthally averaged radial intensity profiles using GOFISH for 7 transition sets (9 lines) of ortho and para c-C3H2 and fit them against a grid of 7,150 1D non-LTE radiative transfer slab models. | R: Best-fit models have R_inner = 25-30 au, R_outer = 110-120 au, maximum H2 column density depth N_max = (2 +/- 0.5) x 10^22 cm^-2 (corresponding to A_V ~ 1 and z/r >= 0.25), and total abundance (7.5-10) x 10^-11 per H atom. | F: c-C3H2 resides in a ring between 25-30 au and 110-120 au in the upper warm molecular layer (z/r ~ 0.25-0.4) and does not originate from the deep midplane (N_H2 >= 10^23 cm^-2) or the tenuous uppermost surface (N_H2 <= 10^21 cm^-2). | **supported**
- H: The ortho-to-para ratio of c-C3H2 in the TW Hya disk is consistent with the statistical weight ratio of 3 rather than a lower value such as 1. | E: Include ortho-to-para ratios of 1 and 3 in the 7,150 non-LTE slab model grid and perform an independent disk-averaged rotational diagram analysis on the unblended optically thin ortho and para lines. | R: All 30 best-fit slab models have OPR = 3 (no good fits with OPR = 1), and the rotational diagram yields an OPR of 3.02 +/- 0.78. | F: The ortho-to-para ratio of c-C3H2 is consistent with a constant value of 3 throughout the emission extent. | **supported**
- H: The c-C3H2 to C2H abundance ratio in TW Hya can be explained by gas-phase chemistry in an oxygen-depleted, high C/O surface layer. | E: Compare the derived c-C3H2 abundance and column density in TW Hya with previously published C2H measurements in TW Hya (Bergin et al. 2016) and chemical models of oxygen depletion (Cleeves et al. 2018). | R: The c-C3H2 abundance is ~3-30% of C2H (or ~10% in column density for the C/O = 1 model), matching the 1-10% ratio predicted by chemical models with volatile oxygen removal at z/r = 0.25-0.5. | F: The c-C3H2 to C2H ratio is consistent with gas-phase chemical routes in a high-C/O, water-poor disk surface without requiring additional carbon sources, though carbon grain/PAH destruction cannot be formally ruled out. | **supported**

## Reasoning

- Why this data: Multi-line observations of ortho and para c-C3H2 spanning E_u = 29.1 K to 96.5 K probe a high critical density and a range of opacities, allowing excitation modeling to break the vertical location degeneracy inherent to face-on disks.  
  > "The set of lines covers energies spanning 29.1 K to 96.5 K, and with the relatively highly critical density and range of opacities probed, these lines are well suited to constraining the nature, and crucially the location, of small hydrocarbon chemistry in TW Hya." (Introduction)
- Why this method: Used GOFISH deprojection and azimuthal stacking to boost SNR of faint para transitions; smoothed all lines to a common 0.5'' round beam for uniform comparison; parameterized vertical slab boundaries by H2 column density because hydrocarbon chemistry is driven by UV radiation; simulated blended ortho/para transitions via weighted population averages to properly account for optical depth.  
  > "We do not use these moment-0 maps for analysis, showing them here to illustrate the detection significance, and instead we apply the GOFISH package (cite: gofish) to improve the signal to noise of the radial profile for each transition." (Images and Radial Integrated Flux Profiles); "The general reasoning for this vertical parameterization rather than a simple $z/r$ cut is that we expect the $c-$C$_3$H$_2$ distribution to be driven by the stellar radiation field, largely UV (cite: Du15; Bergin16)." (Methods); "We took this approach since for some of the models the blended transitions became optically thick, so we could not simply sum the line fluxes from the independent components without potentially overestimating the blended line flux." (Methods)
- Alternative: Using moment-0 maps directly for radial analysis was rejected in favor of GOFISH azimuthal spectral stacking to improve SNR.  
  > "We do not use these moment-0 maps for analysis, showing them here to illustrate the detection significance, and instead we apply the GOFISH package (cite: gofish) to improve the signal to noise of the radial profile for each transition." (Images and Radial Integrated Flux Profiles)
- Alternative: Summing independent line fluxes for the blended ortho/para transitions was rejected because the blends become optically thick in some models, which would overestimate the flux.  
  > "We took this approach since for some of the models the blended transitions became optically thick, so we could not simply sum the line fluxes from the independent components without potentially overestimating the blended line flux." (Methods)
- Alternative: Applying a 10% flux scaling to the 4_{3,2}-3_{2,1} line or varying the upper slab boundary between N_H2 = 10^19 and 10^20 cm^-2 were tested and not adopted for the final grid because they did not alter the best-fit results.  
  > "Furthermore, the models that fit the rest of the data give reasonable fits to the native $4_{3,2} - 3_{2,1}$ observations without flux scaling, and therefore we do not vary the flux for the remainder of the analysis described here." (Methods); "Initially, we also varied the minimum column density of the layer, but since we did not see a significant change between changing the upper boundary from $N_{\rm H_2} = 1\times10^{19}$ cm$^{-2}$ to $1\times10^{20}$ cm$^{-2}$, we decided to fix the upper boundary for the full grid of simulations to the former value of $1\times10^{19}$ cm$^{-2}$" (Methods)
- How they decided it was enough: _not stated_
- Limitation (authors): The inner edge constraint (25-30 au) is close to the half-beam resolution (0.25'' = 15 au) and cannot be constrained further with existing data.  
  > "An inner edge of 25 and 30 au tends to be a better fit for the $c-$C$_3$H$_2$ distribution. We note that this edge is close to the half-beam of the data (0.25$''$ = 15 au), and so cannot constrain this any further from existing data." (Fiducial Model Results)
- Limitation (authors): The inner and outer edge constraints depend on the assumption of a constant-abundance slab geometry; more complex structures would require higher SNR data.  
  > "Finally, we note that both the value for the inner and outer edge only hold if a slab model is an adequate representation of the data, and certainly more complex structural representations could be explored with higher SNR data." (Fiducial Model Results)
- Limitation (authors): There is a degeneracy between the slab depth (N_max) and the c-C3H2 abundance because the emission is thermalized and fundamentally traces column density in a face-on disk.  
  > "The flatness of the $\chi^2_{\rm reduced}$ for the best models suggests some degeneracy between the maximum column density, i.e., the depth of the layer, and the abundance of $c-$C$_3$H$_2$ in the layer, which is to be expected especially if the emission is thermalized." (Fiducial Model Results)
- Limitation (authors): The upper boundary of the c-C3H2 layer is poorly constrained by the existing transitions.  
  > "We do not have strong constraints on the upper extent of the layer, and where additional observations for lines with higher upper state energies (and smaller Einstein A coefficients) would be helpful." ($c-$C$_3$H$_2$ is located in and above the warm molecular layer in a ring)
- Limitation (authors): Due to data SNR, ortho-to-para ratios between 1 and 3 were not explored in the non-LTE slab grid.  
  > "Ortho-to-para of 3 is strongly favored over 1. We do not try to fit between these values given the signal to noise of the data." (Fiducial Model Results)
- Limitation (authors): Cannot distinguish whether the c-C3H2 OPR of 3 reflects an H2 OPR of 3 or a high ratio of electron dissociative recombination to ion-atom reactions (large phi).  
  > "Therefore it is not clear whether our measured $c-$C$_3$H$_2$ ortho to para ratio is shedding light on the ortho-to-para ratio of H$_2$ or if it is related to the relative rate of dissociative recombination." (The ortho-to-para ratio of $c-$C$_3$H$_2$ is consistent with a constant value of 3)
- Caveat (inferred, ours): The derived c-C3H2 abundance per H atom and the conversion from N_H2 to A_V and z/r depend directly on the fixed background disk model (total gas mass 0.04 M_sun, temperature structure, and 6.7x small dust depletion) adopted from Cleeves et al. (2015).
- Caveat (inferred, ours): Spatial correlation between adjacent radial annuli that supersample the 0.5'' beam may affect the absolute scale of the reduced chi^2 metric if the full covariance matrix is not included.

## Reproducibility

- Data public (paper): Archival ALMA datasets 2013.1.00114.S, 2013.1.00198.S, and 2016.1.00311.S acknowledged  
  > "We present new observations of $c-$C$_3$H$_2$ taken as part of the TW Hya as a Chemical Rosetta Stone Program (PI: Cleeves, 2016.1.00311.S), augmented by archival observations from 2013.1.00198.S (PI: Bergin) and 2013.1.00114.S (PI: Öberg)." (ALMA Observations); "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.0.00114.S, ADS/JAO.ALMA#2013.0.00198.S, and\ ADS/JAO.ALMA#2016.0.00311.S." (Acknowledgments)
- Products in archive: _not stated_
- Code: 1D non-LTE radiative transfer code nLTErt1d available at https://github.com/ryanaloomis/nLTErt1d; pykepmask available on Zenodo (doi:10.5281/zenodo.3672187)  
  > "To fit the data, we use a simple slab model method (cite: Qi08; Oberg17) and employ a non-LTE line radiative transfer code based upon Ratran (cite: hogerheijde2000) designed to handle blended transitions and be computationally efficient (https://github.com/ryanaloomis/nLTErt1d)." (Methods); "(ref: jpegues2020code) jpegues. 2020, jpegues/kepmask: Python Package: pykepmask v2.0.0, vv2.0.0, Zenodo, doi:10.5281/zenodo.3672187. <https://doi.org/10.5281/zenodo.3672187>" (References)
- Missing: Exact machine-readable table of the Cleeves et al. (2015) 2D physical model (gas density, gas/dust temperatures as a function of r and z) used as input to nLTErt1d
- Missing: tclean weighting scheme (robust parameter), cell size, image size, and exact uv-taper values per line
- Missing: Non-thermal linewidth assumed in the nLTErt1d radiative transfer calculations
- Missing: Exact radial annulus bin width used in GOFISH and chi^2 evaluation
- Data volume (inferred): ~50-150 GB of raw/calibrated visibilities across the three ALMA programs, plus <5 GB for cleaned spectral cubes and the 7,150 1D slab model outputs.
- Score (inferred): 78/5, All three ALMA project codes are public, open-source analysis and radiative transfer packages (pykepmask, GOFISH, nLTErt1d) are linked and cited, and the 7,150-model parameter grid is fully tabulated in Table 2. Minor deductions for unstated tclean imaging parameters (robust, cell size, exact uv-tapers), unstated non-thermal linewidth in nLTErt1d, and reliance on the external Cleeves et al. (2015) physical disk profiles.
- Rediscovery candidate: yes, Public ALMA data, clearly tabulated integrated line fluxes and slab model parameter grid, and public availability of the exact post-processing and radiative transfer codes (pykepmask, GOFISH, nLTErt1d) make the integrated fluxes, rotational diagram OPR, and radial profile fits strong targets for automated reproduction.

## Links

- Method: (cite: Pegues2020), (cite: jpegues2020code) (Keplerian masking code (pykepmask) used for tclean and flux measurement)
- Method: (cite: gofish) (GOFISH package used to deproject and azimuthally stack spectra into radial profiles)
- Method: (cite: hogerheijde2000) (Ratran code upon which the 1D non-LTE radiative transfer code nLTErt1d is based)
- Method: (cite: Qi08; Oberg17) (Slab model methodology used to parameterize molecular emission)
- Method: (cite: Cleeves15) (Underlying 2D physical structure model of the TW Hya disk)
- Companion: (cite: Bergin16) (Earlier TW Hya hydrocarbon (C2H and c-C3H2) study providing archival data (2013.1.00198.S) and C2H comparison models)
- Companion: (cite: Oberg17) (Earlier TW Hya study providing archival data and calibration details for 2013.1.00114.S)
- Companion: (cite: Calahan20) (TW Hya Rosetta Stone Project series paper)
- Related: TW Hya Rosetta Stone Project

## Checks

```json
{
 "quotes": 155,
 "quotes_ok": 155,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 18,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2013.0.00114.S",
  "2013.0.00198.S",
  "2016.0.00311.S"
 ],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 92,
  "stated": 72,
  "rate": 0.783
 },
 "evidence_ok": true
}
```

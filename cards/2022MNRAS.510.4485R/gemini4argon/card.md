# The AGN fuelling/feedback cycle in nearby radio galaxies - IV. Molecular gas conditions and jet-ISM interaction in NGC 3100

`2022MNRAS.510.4485R` | Monthly Notices of the Royal Astronomical Society 2022 | first author: Ruffa, Ilaria | arXiv: 2112.00755 | DOI: 10.1093/mnras/stab3541

Card schema 1.0 | model gemini-4-argon | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: Investigate the molecular gas physical conditions, kinematics, and jet-ISM interaction in the nearby low-excitation radio galaxy NGC 3100 using multiple molecular transitions and continuum data.  
  > "Coupling these new data with previous $^{12}$CO(2-1) and radio continuum observations, we primarily aim at carrying out an analysis of the molecular gas physics and jet-CO interplay in this object." (Introduction)
- Target **NGC 3100**: coordinates 10h00m40.8s -31d39m52.3s  
  > "RA (J2000) | 10$^{\rm h}$00$^{\rm m}$40$^{\rm s}$.8" (Table 1); "DEC (J2000) | -31$^{\circ}$39$^{'}$52$^{''}$.3" (Table 1); "(2) and (3) Galaxy sky coordinates from (cite: Petrov05)" (Table 1 notes); "(4) Galaxy redshift from (cite: Dopita15). (5) Luminosity distance derived from the tabulated redshift and assuming the cosmology stated in Section 1." (Table 1); z/distance z = 0.0088, D_L = 38.0 Mpc  
  > "Redshift | 0.0088" (Table 1); "D$_{\rm L}$ (Mpc) | 38.0" (Table 1); "(5) Luminosity distance derived from the tabulated redshift and assuming the cosmology stated in Section" (Table 1 notes); "(4) Galaxy redshift from (cite: Dopita15). (5) Luminosity distance derived from the tabulated redshift and assuming the cosmology stated in Section 1." (Table 1); distance from Redshift from (cite: Dopita15), D_L derived assuming H0=70 km s^-1 Mpc^-1, Omega_Lambda=0.7, Omega_M=0.3  
  > "(4) Galaxy redshift from (cite: Dopita15)" (Table 1 notes); "(5) Luminosity distance derived from the tabulated redshift and assuming the cosmology stated in Section" (Table 1 notes); "Throughout this work we assume a standard $\Lambda$CDM cosmology with H$_{\rm 0}=70$ km s$^{-1}$ Mpc$^{\rm -1}$, $\Omega_{\rm \Lambda}=0.7$ and $\Omega_{\rm M}=0.3$." (Introduction); "(4) Galaxy redshift from (cite: Dopita15). (5) Luminosity distance derived from the tabulated redshift and assuming the cosmology stated in Section 1." (Table 1)

## Data provenance

- ALMA projects: 2015.1.01572.S, 2018.1.01095.S
- bands: Band 3, Band 4, Band 6, Band 7  
  > "NGC 3100 was observed in three different ALMA Bands: in Band 3 we targeted the CO(1-0) transition, in Band 4 the HNCO(6-5) and SiO(3-2), and in Band 7 the CO(3-2) and HCO$^{+}$(4-3) lines." (ALMA observations and data reduction); "As already mentioned above, these newly-acquired data complement previous Band 6 observations of NGC 3100 in the CO(2-1) transition, which were obtained in March 2016 as part of ALMA Cycle 3 (PI: I. Prandoni)." (ALMA observations and data reduction)
- frequencies and spectral setup: 4 SPWs: 1 or 2 line SPWs (1920 channels of 1.129 MHz width) and 3 or 2 continuum SPWs (240 channels of 7.813 MHz width)  
  > "a total of four spectral windows (SPWs); one (or two, depending on the number of lines targeted in the observing block) centred at the line(s) redshifted frequency ($\nu_{\rm sky}$) and divided into 1920 1.129 MHz-wide channels" (ALMA observations and data reduction); "the other three (or two) used to map the continuum emission and divided into 240 7.813-MHz-wide channels." (ALMA observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: 12-m array (41 to 48 antennae)  
  > "Between 41 and 48 12-m antennae were used; the maximum baseline length was 783 m for Band 3 and 4 observations, 360 m for Band 7." (ALMA observations and data reduction)
- configurations: _not stated_
- baselines: max 783 m (Band 3 and 4), max 360 m (Band 7)  
  > "Between 41 and 48 12-m antennae were used; the maximum baseline length was 783 m for Band 3 and 4 observations, 360 m for Band 7." (ALMA observations and data reduction)
- angular resolution: Band 3: 1.4" x 1.0" (250 pc); Band 4: 1.1" x 0.9" (195 pc); Band 6: 0.9" x 0.7" (160 pc); Band 7: 1.1" x 0.6" (195 pc)  
  > "Band 3 | 2019-04-23/24 | $^{12}$CO(1-0) | 115.2712 | 114.2657 | 62 | 3.7 (21) | 8.9 (50) | 1.4 | 1.0 | -85 | 250" (Table 2); "188   | 3.4 (19)       | 7.6 (43)       | 1.1           | 0.9" (Table 2); "32    | 1.2 (7.0)      | 3.0 (17)       | 1.1           | 0.6           | -84             | 195" (Table 2)
- max recoverable scale: Band 3: 21" (3.7 kpc); Band 4: 19" (3.4 kpc); Band 6: 11" (1.9 kpc); Band 7: 7.0" (1.2 kpc)  
  > "Band 3 | 2019-04-23/24 | $^{12}$CO(1-0) | 115.2712 | 114.2657 | 62 | 3.7 (21) | 8.9 (50) | 1.4 | 1.0 | -85 | 250" (Table 2); "Band 6$^{*}$ | 2016-03-22 | $^{12}$CO(2-1) | 230.5380 | 228.6299 | 28 | 1.9 (11) | 4.4 (25) | 0.9 | 0.7 | -87 | 160" (Table 2); "32    | 1.2 (7.0)      | 3.0 (17)" (Table 2)
- sensitivity: Continuum rms: 9 to 50 uJy beam^-1; CO cubes (10 km/s): 0.6 mJy beam^-1; HNCO/SiO cubes (105 km/s): 0.05 mJy beam^-1; HCO+ cube (105 km/s): 0.2 mJy beam^-1  
  > "This allowed us to obtain root-mean square (rms) noise levels ranging from 9 to 50 $\mu$Jy beam$^{-1}$ for synthesized beams of 0.6 – 0.9 arcsec full-width at half-maximum (FWHM)." (Continuum imaging); "HNCO(6-5) | 0.05 | $<0.15$ | $-$ | 105" (Table 3); "HCO$^{+}$(4-3) | 0.2 | 1.0 | 5 | 105" (Table 3)
- time on source: Band 3: 62 min; Band 4: 188 min; Band 6: 28 min; Band 7: 32 min  
  > "Band 3 | 2019-04-23/24 | $^{12}$CO(1-0) | 115.2712 | 114.2657 | 62 | 3.7 (21) | 8.9 (50) | 1.4 | 1.0 | -85 | 250" (Table 2); "188   | 3.4 (19)       | 7.6 (43)" (Table 2); "28    | 1.9 (11)       | 4.4 (25)" (Table 2)
- observing dates: Band 3: 2019-04-23/24; Band 4: 2018-12-14/15; Band 6: 2016-03-22; Band 7: 2019-03-15  
  > "Band 3 | 2019-04-23/24 | $^{12}$CO(1-0)" (Table 2); "Band 4 | 2018-12-14/15" (Table 2); "Band 6$^{*}$ | 2016-03-22" (Table 2)
- pi or archival as stated: PI: I. Ruffa (Cycle 6); PI: I. Prandoni (Cycle 3 Band 6)  
  > "The observations presented in this paper were carried out during ALMA Cycle 6 between December 2018 and April 2019 (PI: I. Ruffa)." (ALMA observations and data reduction); "As already mentioned above, these newly-acquired data complement previous Band 6 observations of NGC 3100 in the CO(2-1) transition, which were obtained in March 2016 as part of ALMA Cycle 3 (PI: I. Prandoni)." (ALMA observations and data reduction)
- Line: 12CO 1-0 (115.2712 GHz)
- Line: HNCO 6-5 (131.8857 GHz)
- Line: SiO 3-2 (130.2686 GHz)
- Line: 12CO 2-1 (230.5380 GHz)
- Line: HCO+ 4-3 (356.7342 GHz)
- Line: 12CO 3-2 (345.7960 GHz)
- Other facility **Karl G. Jansky Very Large Array (JVLA)**: High-resolution 5 and 10 GHz radio continuum maps  
  > "The comparison between the ALMA CO(2-1) data and newly-acquired, high-resolution Karl G. Jansky Very Large Array (JVLA) radio continuum observations at 10 GHz (cite: Ruffa20) adds further evidence for the presence of such an interaction" (A southern radio galaxy sample); "Our multi-frequency (107, 136, 235 and 348 GHz) mm continuum images show the same compact core-double lobe structure seen in the radio continuum at 5 and 10 GHz" (Continuum emission)
- Other facility **NASA/IPAC extragalactic database (NED)**: Unresolved 1.4 GHz, 843 MHz, and 408 MHz radio flux density measurements  
  > "and also measurements from unresolved 1.4 GHz, 843 and 408 MHz data taken from the NASA/IPAC extragalactic database (NED; https://ned.ipac.caltech.edu)." (Continuum emission)
- Other facility **HyperLeda database**: Morphological type S0 and stellar velocity dispersion sigma_* = 191 km s^-1  
  > "(1) Morphological type of the galaxy from the HyperLeda database (http://leda.univ-lyon1.fr)." (Table 1); "where we assumed a stellar velocity dispersion $\sigma_{*}=191$ km s$^{-1}$ taken from the HyperLeda database (http://leda.univ-lyon1.fr)." (CO excitation conditions and kinematics)
- External data: B-I optical colour map of NGC 3100  
  > "knowing from the B-I colour map of NGC 3100" (Section 4.4 (CO kinematics)); "where $\Sigma$ is the area covered by the dust features, $\langle A_{\rm \lambda} \rangle$ is the wavelength-dependent mean extinction (i.e. dust absorption) of that area (measured directly from the $B$-$I$ colour map" (CO-dust comparison and gas-phase metallicity: implications for the gas origin) [from (cite: Ruffa19a; Ruffa20)]
- External data: Galaxy sky coordinates  
  > "(2) and (3) Galaxy sky coordinates from (cite: Petrov05)." (Table 1) [from (cite: Petrov05)]
- External data: Galaxy redshift z = 0.0088 and [OIII]5007 luminosity L_[OIII] ~ 1.7x10^39 erg s^-1  
  > "(4) Galaxy redshift from (cite: Dopita15)." (Table 1); "Based on the optical spectroscopy presented by (cite: Dopita15), $L_{\rm [OIII]}\approx1.7\times10^{39}$ erg s$^{-1}$ and thus $L_{\rm bol}=6\times10^{42}$ erg s$^{-1}$." (CO excitation conditions and kinematics) [from (cite: Dopita15)]
- External data: Radio power at 1.4 GHz (log P_1.4GHz = 23.0 W Hz^-1)  
  > "(7) Radio power at 1.4 GHz derived from the flux density given in (cite: Brown11), including all the radio emission associated with the source." (Table 1) [from (cite: Brown11)]
- External data: Optical stellar velocity v_opt = 2629 +/- 20 km s^-1  
  > "$v_{\rm opt}$ (km s$^{-1}$) | $2629\pm20$" (Table 1); "(8) Optical stellar velocity from (cite: Kerr86)." (Table 1) [from (cite: Kerr86)]

## Processing

### Calibration

- pipeline or manual: manual using customized Python data reduction scripts  
  > "We manually calibrated all data using the Common Astronomy Software Application (cite: McMullin07) package, version 5.4.1 (4.7.2 for Band 6 data), reducing each dataset separately with customized PYTHON data reduction scripts." (ALMA observations and data reduction)
- casa version: 5.4.1 (4.7.2 for Band 6 data)  
  > "We manually calibrated all data using the Common Astronomy Software Application (cite: McMullin07) package, version 5.4.1 (4.7.2 for Band 6 data), reducing each dataset separately with customized PYTHON data reduction scripts." (ALMA observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1037-2934 (Band 3), J1107-4449 (Band 4), J1058+0133 (Band 7)  
  > "for each session, a single bright quasar was used as both flux and bandpass calibrator, a second one as phase calibrator." (ALMA observations and data reduction); "Specifically, we used J1037$-$2934 and J1024$-$3234 for Band 3, J1107$-$4449 and J1037$-$2934 for Band 4, and J1058$+$0133 and J1037$-$2934 for Band 7, respectively." (ALMA observations and data reduction)
- flux scale uncertainty: 10%  
  > "These latter are estimated as $\sqrt{{\rm rms}^{2} + (0.1 \times S_{\rm \nu})^{2}}$, where the second term dominates in all cases." (Continuum imaging)
- self calibration: Multiple cycles of phase-only self-calibration and one cycle of amplitude and phase self-calibration at all frequencies, applied to line cubes  
  > "Since continuum emission from the core is detected at high signal-to-noise ratios (S/N) at all frequencies, multiple cycles of phase-only self calibration and one cycle of amplitude and phase self-calibration were performed at all frequencies." (Continuum imaging); "After applying the continuum self-calibration, the CO line emission was isolated in the $uv$-plane using the casa task `uvcontsub`." (Line imaging)

### Imaging

- task: tclean  
  > "The continuum SPWs and the line-free channels of the line SPW(s) of each observing run were used to produce the continuum maps, using the `tclean` task in multi-frequency synthesis (MFS) mode (cite: Rau11) with no spectral dependence." (Continuum imaging); "We created the data cubes of the CO transitions using the `tclean` task with natural weighting and channel widths of 10 km s$^{-1}$." (Line imaging)
- deconvolver: MFS with no spectral dependence (continuum)  
  > "The continuum SPWs and the line-free channels of the line SPW(s) of each observing run were used to produce the continuum maps, using the `tclean` task in multi-frequency synthesis (MFS) mode (cite: Rau11) with no spectral dependence." (Continuum imaging)
- weighting robust: natural weighting  
  > "All the continuum maps were made using natural weighting in order to maximise the sensitivity, with the goal of imaging extended emission from the radio source." (Continuum imaging); "We created the data cubes of the CO transitions using the `tclean` task with natural weighting and channel widths of 10 km s$^{-1}$." (Line imaging)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: interactive cleaning in regions of line emission to 1.5x rms threshold  
  > "The continuum-subtracted dirty cubes were cleaned in regions of line emission (identified interactively) to a threshold equal to 1.5 times the rms noise level (determined from line-free channels), and then primary-beam corrected." (Line imaging)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub with linear fits in frequency to line-free channels (CO) or continuum SPWs only (SiO, HNCO, HCO+)  
  > "After applying the continuum self-calibration, the CO line emission was isolated in the $uv$-plane using the casa task `uvcontsub`. This forms a continuum model from linear fits in frequency to line-free channels, and then subtracts this model from the visibilities." (Line imaging); "SiO(3-2), HNCO(6-5) and HCO$^{+}$(4-3) emission (and consequently line-free channels) could not be identified in the SPWs centred on the corresponding redshifted line frequencies; the continuum was thus modelled using the continuum SPWs only." (Line imaging)
- line free channels: _not stated_
- primary beam correction: applied to all continuum maps and line cubes  
  > "All the continuum maps are primary-beam corrected." (Continuum imaging); "The continuum-subtracted dirty cubes were cleaned in regions of line emission (identified interactively) to a threshold equal to 1.5 times the rms noise level (determined from line-free channels), and then primary-beam corrected." (Line imaging)
- array combination: _not stated_
- smoothing: selected common uv range and convolved to common synthesized beam of 1.4" x 0.9" for line ratio maps  
  > "We also corrected for the different $uv$ coverages by smoothing to a common resolution (i.e. selecting a common $uv$ range and convolving to a common synthesized beam)." (Spatially-resolved line ratios); "This resulted in data cubes with synthesized beams of $1^{\prime \prime}.4 \times 0^{\prime \prime}.9$ (corresponding to $\approx250 \times 160$ pc$^{2}$)." (Spatially-resolved line ratios)
- final beam: Continuum: 0.6" - 0.9" FWHM; Line cubes: 1.4"x1.0" PA -85 deg (Band 3), 1.1"x0.9" PA -81/-84 deg (Band 4), 0.9"x0.7" PA -87 deg (Band 6), 1.1"x0.6" PA -84 deg (Band 7); Matched cubes: 1.4"x0.9"  
  > "This allowed us to obtain root-mean square (rms) noise levels ranging from 9 to 50 $\mu$Jy beam$^{-1}$ for synthesized beams of 0.6 – 0.9 arcsec full-width at half-maximum (FWHM)." (Continuum imaging); "1.4           | 1.0           | -85             | 250" (Table 2); "This resulted in data cubes with synthesized beams of $1^{\prime \prime}.4 \times 0^{\prime \prime}.9$ (corresponding to $\approx250 \times 160$ pc$^{2}$)." (Spatially-resolved line ratios)
- final rms: Continuum: 9 to 50 uJy beam^-1; CO(1-0), CO(2-1), CO(3-2) cubes (10 km/s): 0.6 mJy beam^-1; HNCO(6-5), SiO(3-2) cubes (105 km/s): 0.05 mJy beam^-1; HCO+(4-3) cube (105 km/s): 0.2 mJy beam^-1  
  > "This allowed us to obtain root-mean square (rms) noise levels ranging from 9 to 50 $\mu$Jy beam$^{-1}$ for synthesized beams of 0.6 – 0.9 arcsec full-width at half-maximum (FWHM)." (Continuum imaging); "HNCO(6-5) | 0.05 | $<0.15$ | $-$ | 105" (Table 3); "HCO$^{+}$(4-3) | 0.2 | 1.0 | 5 | 105" (Table 3)

### Inherited from earlier work

- Sample selection and Band 6 CO(2-1) and 230 GHz continuum observations and data reduction  
  > "A full description of our project, including details on the sample selection and all the available observations, can be found in (cite: Ruffa19a); a brief summary is presented here." (A southern radio galaxy sample); "Nine sample members were observed during ALMA Cycle 3 in the $^{12}$CO(2-1) line and 230 GHz continuum (cite: Ruffa19a)." (A southern radio galaxy sample) [from (cite: Ruffa19a)]
- 3D kinematic modelling procedure with KinMS and KinMS_MCMC  
  > "The 3D modelling of these discs (cite: Ruffa19b) demonstrates that, although the bulk of the gas appears to be in ordered rotation, low-amplitude perturbations and/or non-circular motions are ubiquitous" (A southern radio galaxy sample); "The procedure adopted to carry out the kinematic modelling is the same as that followed for the CO(2-1) transition." (CO kinematics) [from (cite: Ruffa19b)]
- 10 GHz and 5 GHz JVLA radio continuum maps and flux densities  
  > "The comparison between the ALMA CO(2-1) data and newly-acquired, high-resolution Karl G. Jansky Very Large Array (JVLA) radio continuum observations at 10 GHz (cite: Ruffa20) adds further evidence" (A southern radio galaxy sample); "Flux density measurements including emission from single components (i.e. core or jet) are instead taken only from spatially-resolved and matched-resolution data (i.e. the 5 and 10 GHz VLA and all ALMA continuum data" (Continuum emission) [from (cite: Ruffa20)]
- Masked moment map creation technique  
  > "Integrated intensity (moment 0), mean line-of-sight velocity (moment 1), and velocity dispersion (moment 2) maps of the CO lines were created from the continuum-subtracted data cubes using the masked moment technique as described by (cite: Dame11)." (Moment maps) [from (cite: Dame11)]

### Not stated but needed to reproduce (our reading)

- Image cell size and image dimensions (pixel and image size) for continuum maps and line cubes
- Solution intervals (solint) and number of cycles for phase-only and amplitude+phase self-calibration
- Exact frequency/velocity ranges of line-free channels used for uvcontsub
- Exact common uv-range selected when matching resolution for the line ratio maps
- Exact parameter values for the nuclear logarithmic spiral component in the KinMS model
- Missing continuum flux density table (Table of continuum image properties was omitted/unparsed in text)

## Analysis recipe

1. **Create moment maps of molecular lines**: Masked moment technique: copy of cleaned cube is Gaussian-smoothed spatially (FWHM equal to synthesized beam) and Hanning-smoothed in velocity; a 3D mask is defined above a flux threshold, then applied to the un-smoothed cube.  
  > "In this technique, a copy of the cleaned data cube is first Gaussian-smoothed spatially (with a FWHM equal to that of the synthesised beam) and then Hanning-smoothed in velocity." (Moment maps); "A three-dimensional mask is then defined by selecting all the pixels above a fixed flux-density threshold." (Moment maps); "The moment maps were then produced from the un-smoothed cubes using the masked regions only (cite: Davis17)." (Moment maps)
   - parameter: Flux threshold = 1.2 sigma (measured in un-smoothed cube)  
  > "Given the high significance of our CO detections (see Table 11), a threshold of 1.2$\sigma$ (where $\sigma$ is the rms noise level measured in the un-smoothed data cube) has been used in all the cases." (Moment maps)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract spectral profiles, line widths, and integrated fluxes / upper limits**: Extract spectra within boxes covering central 10"x11" (CO) and 1.5"x1.5" (HCO+); measure FWZI across channels >=3 sigma; measure CO FWHM directly from double-horned profile and HCO+ FWHM via Gaussian fit; compute 3-sigma upper limits for non-detections.  
  > "The spectral profiles of the central CO(1-0) and CO(3-2) structures were extracted from the cleaned data cubes within boxes covering the same $10''\times11''$ central area of each cube." (Line widths and profiles); "extracted from the cleaned data cube within a $1.5''\times 1.5''$ box centred on the emission peak" (Line widths and profiles); "For the undetected SiO(3-2) and HNCO(6-5) shock tracers, 3$\sigma$ upper limits on the velocity-integrated flux densities were calculated from the relation (cite: Koay15):" (Line widths and profiles)
   - parameter: Extraction box: 10" x 11" for CO, 1.5" x 1.5" for HCO+(4-3); FWZI threshold >= 3 sigma  
  > "The spectral profiles of the central CO(1-0) and CO(3-2) structures were extracted from the cleaned data cubes within boxes covering the same $10''\times11''$ central area of each cube." (Line widths and profiles); "The former was defined as the full velocity range covered by channels (identified interactively in the channel maps) with line intensities $\geq3\sigma$." (Line widths and profiles)
   - assumption: For SiO and HNCO upper limits, emission is assumed unresolved (within synthesized beam) with expected FWHM = 340 km s^-1 (same as CO(2-1)).  
  > "We assumed the same FWHM of the CO(2-1) line (see Table 1)." (Line widths and profiles); "is only valid if all of the molecular gas is concentrated within the synthesized beam ($\approx190 \times 160$ pc$^2$ for Band 4 observations" (Line widths and profiles)
   - fitting: Gaussian fit on the integrated spectrum of HCO+(4-3)  
  > "we estimated the FWHM by performing a Gaussian fit on the integrated spectrum" (Line widths and profiles)
   - validation: _not stated_
3. **Estimate total molecular gas mass from CO(1-0)**: Convert integrated CO(1-0) flux density to total molecular gas mass including heavy elements using the standard Bolatto et al. (2013) relation.  
  > "We adopted the following relation to estimate the total molecular gas mass, including contributions from heavy elements (cite: Bolatto13):" (Molecular gas mass)
   - assumption: Milky Way CO-to-H2 conversion factor X_CO = 2 x 10^20 cm^-2 (K km s^-1)^-1 (with +/- 0.4 dex systematic scatter), z = 0.0088, D_L = 38.0 Mpc (10% distance uncertainty).  
  > "Therefore, we adopt an average Milky Way CO-to-H$_{2}$ conversion factor of $X$~CO~$=2 \times 10^{20}$ cm$^{-2}$(K km s$^{-1}$)$^{-1}$." (Molecular gas mass); "This can be quantified by assuming a conservative scatter of $\pm0.4$ dex (about a factor of 2.5; (cite: Bolatto13)) around the adopted Milky Way value, leading the molecular gas mass to vary within the range $0.5-3.5 \times 10^{8}$ M$_{\odot}$." (Molecular gas mass)
   - fitting: _not stated_
   - validation: Compared against previous estimate from CO(2-1) data (1.2 +/- 0.1 +/- 0.3 x 10^8 M_sun) and found fully consistent.  
  > "This is fully consistent with that estimated from CO(2-1) data ($M_{\rm mol}=(1.2\pm0.1\pm0.3)~\times~10^{8}$ M~$\odot$~; ), despite the average flux density ratio assumed for that calculation (i.e. $R$~21~$=2.32$; ) was slightly larger than that measured" (Molecular gas mass)
4. **Compute spatially-resolved line ratio maps (R_21, R_31, R_HCO)**: Re-image CO cubes to identical channel number, channel width, pixel and image size, select a common uv range, convolve to a common 1.4" x 0.9" beam, produce masked moment 0 maps, and divide using CASA immath.  
  > "We thus re-imaged the three CO transitions making new data cubes with the same number of channels, channel width (i.e. 10 km s$^{-1}$), pixel and image size." (Spatially-resolved line ratios); "We also corrected for the different $uv$ coverages by smoothing to a common resolution (i.e. selecting a common $uv$ range and convolving to a common synthesized beam)." (Spatially-resolved line ratios); "Masked integrated intensity maps of these smoothed data cubes were produced, and then used to make ratio maps using the CASA task `immath`." (Spatially-resolved line ratios)
   - software: CASA, immath
   - parameter: Common beam: 1.4" x 0.9"; channel width: 10 km s^-1 (for CO ratios) and 105 km s^-1 (for HCO+/CO(2-1) ratio)  
  > "This resulted in data cubes with synthesized beams of $1^{\prime \prime}.4 \times 0^{\prime \prime}.9$ (corresponding to $\approx250 \times 160$ pc$^{2}$)." (Spatially-resolved line ratios); "We used the same method described above, but binned the CO(2-1) data cube to a channel width of 105 km s$^{-1}$." (Spatially-resolved line ratios)
   - assumption: Local thermodynamic equilibrium (LTE) and optically thin conditions in the inner high-ratio region to infer T_ex >= 50 K from R_31 >= 12.  
  > "Assuming local thermodynamic equilibrium (LTE) and optically thin conditions, CO ratios $\gtrsim12$ imply gas excitation temperatures $T_{\rm ex} \gtrsim50$ K (cite: Oosterloo17)." (Spatially-resolved line ratios)
   - fitting: _not stated_
   - validation: _not stated_
5. **3D kinematic modelling of CO(3-2) and outflow mass/rate estimation**: Simulate mock cubes with KinMS using a nuclear two-armed logarithmic spiral embedded in an axisymmetric exponential disc, linear radial PA and inclination warps, an arctangent rotation curve, and spatially constant velocity dispersion; fit to observed cube with KinMS_MCMC; extract spectra in velocity residual regions to identify inflow/outflow components and compute outflow mass and rate.  
  > "The former was parametrised in KinMS as a uniform brightness distribution along loci whose positions from the phase centre are described by a logarithmic spiral function; the latter as an axisymmetric exponential disc" (CO kinematics); "The gas was then assumed to be in purely circular motion and its rotation curve was modelled using a simple arctangent function (cite: Swinbank12; Voort18)." (CO kinematics); "The so-simulated data cube was then fitted to the observed one using the Markov Chain Monte Carlo (MCMC) code KINMS_MCMC, which explores the full space defined by the input model and outputs the full Bayesian posterior probability distribution" (CO kinematics)
   - software: KinMS, KINMS_MCMC, IDL
   - parameter: 10^5 - 10^6 point-like sources; R_max = 300 pc, v_max = 200 km s^-1 for outflow  
  > "and constructs the corresponding mock data cube by calculating the line-of-sight projection of the circular velocity for a defined number (typically $10^{5}-10^{6}$) of point-like sources representing the gas distribution." (CO kinematics); "Assuming $R_{\rm max}=300$ pc (i.e. the maximum extent of regions C and D in Figure 13) and $v_{\rm max}=200$ km s$^{-1}$, we obtain $\dot{M} \lesssim 0.12$ M$_{\odot}$ yr$^{-1}$." (CO kinematics)
   - assumption: Pure circular motion for the baseline model; spatially constant intrinsic velocity dispersion; optically thin LTE gas with T_ex = 50 K giving X_CO = 2.5 x 10^19 cm^-2 (K km s^-1)^-1 for outflow mass; spherical geometry for outflow rate (M_dot <= 3 v_max M_out / R_max).  
  > "Assuming $T_{\rm ex}=50$ K for an average $R_{\rm 31}\approx12$ in the high-excitation regions, we get $X_{\rm CO}= 2.5\times10^{19}$ cm$^{2}$ (K km s$^{-1}$)$^{-1}$ and $M_{\rm out} = 5.6 \times 10^{4}$ M$_{\odot}$." (CO kinematics); "Making the simple assumption of spherical geometry for the outflowing region, an upper limit on the mass outflow rate can also be obtained from the relation $\dot{M} \lesssim 3v_{\rm max}M_{\rm out}/R_{\rm max}$ (cite: Maiolino12)" (CO kinematics)
   - fitting: Markov Chain Monte Carlo (MCMC) Bayesian posterior exploration using KINMS_MCMC  
  > "The so-simulated data cube was then fitted to the observed one using the Markov Chain Monte Carlo (MCMC) code KINMS_MCMC, which explores the full space defined by the input model and outputs the full Bayesian posterior probability distribution, identifying the best-fitting set of parameters." (CO kinematics)
   - validation: Compared best-fitting parameters with CO(2-1) kinematic modelling; extracted local spectral profiles in residual regions (A, B, C, D) to verify multiple kinematic components against flux-weighted moment 1 residuals.  
  > "These latter are fully in agreement with that obtained from the CO(2-1) kinematic modelling, and thus not further discussed here (see Table 2 and for details)." (CO kinematics); "As a further check, we then extracted spectral profiles from the cleaned CO(3-2) data cube within the regions enclosing the most significant velocity residuals described above." (CO kinematics)
6. **Fit radio to (sub-)mm continuum spectral energy distribution**: Fit single power-law function S_nu = A nu^alpha to total, core, and jet continuum flux densities across radio and ALMA mm bands.  
  > "To obtain spectral indices, the data points of each component are fitted with a single power-law function (of the form $S_{\rm \nu} = A\nu^{\rm \alpha}$, where $S_\nu$ is the flux density as a function of frequency $\nu$, $A$ is the power-law normalisation, and $\alpha$ is the spectral index) using the least-squares minimization Python routine `lmfit` (cite: Newville14)." (Continuum emission)
   - software: lmfit, PYTHON
   - assumption: Radio source is compact with no emission on larger scales, allowing combination of low- and high-resolution data for total spectrum; matched-resolution data used for core and jet components.  
  > "Such combination of high- and low-resolution data in the total radio to sub-mm spectrum is possible in this case because the radio source in NGC 3100 is compact and there is no evidence from the available multi-frequency radio data for emission on larger scales" (Continuum emission); "Flux density measurements including emission from single components (i.e. core or jet) are instead taken only from spatially-resolved and matched-resolution data (i.e. the 5 and 10 GHz VLA and all ALMA continuum data from , and this work)." (Continuum emission)
   - fitting: Least-squares minimization with A and alpha free to vary  
  > "using the least-squares minimization Python routine `lmfit` (cite: Newville14). The spectral index and power-law normalization are left free to vary in the fitting process." (Continuum emission)
   - validation: _not stated_
7. **Estimate dust mass, molecular gas-to-dust ratio, and gas-phase metallicity**: Measure mean extinction <A_lambda> from B-I colour map in regions co-spatial with CO, compute dust mass M_dust = Sigma <A_lambda> Gamma_lambda^-1, and derive gas-phase metallicity upper limit from M_gas/M_dust using the Draine et al. (2007) relation.  
  > "Following (cite: Draine07), we estimated the gas-phase metallicity in the central dusty gas structure and eastern patch" (CO-dust comparison and gas-phase metallicity); "Based on the works of (e.g. ) (cite: Kaviraj12), the mass of dust clumps and patches can be estimated as: $$\begin{eqnarray} \label{eq:clumpy_dust_mass} M_{\rm dust} = \Sigma \langle A_{\rm \lambda} \rangle \Gamma_{\rm \lambda}^{-1}, \end{eqnarray}$$" (CO-dust comparison and gas-phase metallicity: implications for the gas origin)
   - parameter: <A_lambda> = 2.0 mag (central structure) and 1.7 mag (eastern patch)  
  > "where $\Sigma$ is the area covered by the dust features, $\langle A_{\rm \lambda} \rangle$ is the wavelength-dependent mean extinction (i.e. dust absorption) of that area (measured directly from the $B$-$I$ colour map and equal to 2.0 and 1.7 mag in the central structure and eastern patch, respectively)" (CO-dust comparison and gas-phase metallicity: implications for the gas origin)
   - assumption: Milky Way B-band mass absorption coefficient Gamma_B = 8 x 10^-6 mag kpc^2 M_sun^-1; solar metallicity 12+log10(O/H) = 8.66 at gas-to-dust ratio of 100; neglecting HI yields a lower limit on M_gas/M_dust and upper limit on metallicity.  
  > "The numerical factor is set as to obtain the solar metallicity ($12 + \log_{10}({\rm O/H}) = 8.66$; (cite: Asplund04)) at a gas-to-dust mass ratio of 100." (CO-dust comparison and gas-phase metallicity: implications for the gas origin); "Assuming that the dust properties of ETGs are similar to those of our Galaxy (cite: Finkelman08), we adopt the Milky Way $B$-band mass absorption coefficient ($\Gamma_{\rm B} = 8 \times 10^{-6}$ mag kpc$^{2}$ M$_{\odot}^{-1}$)." (CO-dust comparison and gas-phase metallicity: implications for the gas origin)
   - fitting: _not stated_
   - validation: Tested sensitivity to X_CO variations across the +/- 0.4 dex uncertainty range, finding M_gas/M_dust >= 200 and sub-solar metallicity in all cases.  
  > "we obtain a molecular gas-to-dust mass ratio $M_{\rm gas}/M_{\rm dust}\approx200$ and then a gas-phase metallicity which is about 2.5 times smaller than the solar one" (CO-dust comparison and gas-phase metallicity)

## Software

- **CASA** 5.4.1 (4.7.2 for Band 6 data): Manual calibration, continuum and line imaging (tclean), continuum subtraction (uvcontsub), and line ratio map calculation (immath)  
  > "We manually calibrated all data using the Common Astronomy Software Application (cite: McMullin07) package, version 5.4.1 (4.7.2 for Band 6 data), reducing each dataset separately with customized PYTHON data reduction scripts." (ALMA observations and data reduction); "Masked integrated intensity maps of these smoothed data cubes were produced, and then used to make ratio maps using the CASA task `immath`." (Spatially-resolved line ratios)
- **tclean** : Continuum imaging in MFS mode and line data cube deconvolution  
  > "The continuum SPWs and the line-free channels of the line SPW(s) of each observing run were used to produce the continuum maps, using the `tclean` task in multi-frequency synthesis (MFS) mode (cite: Rau11) with no spectral dependence." (Continuum imaging); "We created the data cubes of the CO transitions using the `tclean` task with natural weighting and channel widths of 10 km s$^{-1}$." (Line imaging)
- **uvcontsub** : Visibility-plane continuum subtraction for line data cubes  
  > "After applying the continuum self-calibration, the CO line emission was isolated in the $uv$-plane using the casa task `uvcontsub`." (Line imaging)
- **immath** : Creating spatially-resolved line ratio maps from masked moment 0 maps  
  > "Masked integrated intensity maps of these smoothed data cubes were produced, and then used to make ratio maps using the CASA task `immath`." (Spatially-resolved line ratios)
- **KINEMATIC MOLECULAR SIMULATION (KinMS)** IDL version: Constructing 3D mock data cubes of the CO gas distribution and kinematics  
  > "We analysed the CO kinematics using the Integrated Development Language (IDL) version of the KINEMATIC MOLECULAR SIMULATION tool (cite: Davis13)." (CO kinematics)
- **KINMS_MCMC** : MCMC fitting of simulated KinMS data cubes to the observed CO(3-2) cube  
  > "The so-simulated data cube was then fitted to the observed one using the Markov Chain Monte Carlo (MCMC) code KINMS_MCMC, which explores the full space defined by the input model and outputs the full Bayesian posterior probability distribution" (CO kinematics)
- **IDL** : Running the KinMS kinematic modelling tool  
  > "We analysed the CO kinematics using the Integrated Development Language (IDL) version of the KINEMATIC MOLECULAR SIMULATION tool (cite: Davis13)." (CO kinematics)
- **lmfit** : Least-squares power-law fitting of the radio to sub-mm continuum SED  
  > "using the least-squares minimization Python routine `lmfit` (cite: Newville14)." (Continuum emission)
- **PYTHON** : Customized data reduction scripts and SED fitting with lmfit  
  > "reducing each dataset separately with customized PYTHON data reduction scripts." (ALMA observations and data reduction); "using the least-squares minimization Python routine `lmfit` (cite: Newville14)." (Continuum emission)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 12CO(1-0) peak flux density | 13.8 | not stated | mJy beam^-1 | 0 | $^{12}$CO(1-0) / 0.6 / 13.8 / 23 / 10 |
| 12CO(3-2) peak flux density | 50.0 | not stated | mJy beam^-1 | 0 | $^{12}$CO(3-2) / 0.6 / 50.0 / 83 / 10 |
| HCO+(4-3) peak flux density | 1.0 | not stated | mJy beam^-1 | 0 | HCO$^{+}$(4-3) / 0.2 / 1.0 / 5 / 105 |
| HNCO(6-5) peak flux density upper limit | <0.15 | not stated | mJy beam^-1 | 0 | HNCO(6-5) / 0.05 / $<0.15$ / $-$ / 105 |
| SiO(3-2) peak flux density upper limit | <0.15 | not stated | mJy beam^-1 | 0 | SiO(3-2) / 0.05 / $<0.15$ / $-$ / 105 |
| 12CO(1-0) integrated flux density (S Delta v) | 9.3 | 1.1 | Jy km s^-1 | 2 | $^{12}$CO(1-0) / 350 / 440 / 9.3$\pm$1.1 / $-$ |
| 12CO(1-0) line FWHM | 350 | not stated | km s^-1 | 2 | $^{12}$CO(1-0) / 350 / 440 / 9.3$\pm$1.1 / $-$ |
| 12CO(1-0) line FWZI | 440 | not stated | km s^-1 | 2 | $^{12}$CO(1-0) / 350 / 440 / 9.3$\pm$1.1 / $-$ |
| 12CO(2-1) integrated flux density (S Delta v) | 20.0 | 2.1 | Jy km s^-1 | 2 | $^{12}$CO(2-1) / 340 / 440 / 20.0$\pm$2.1$^{*}$ / 2.14$\pm0.4$ |
| Average integrated flux density ratio R_21 (CO(2-1)/CO(1-0)) | 2.14 | 0.4 | dimensionless | 2 | $^{12}$CO(2-1) / 340 / 440 / 20.0$\pm$2.1$^{*}$ / 2.14$\pm0.4$ |
| 12CO(3-2) integrated flux density (S Delta v) | 31.3 | 3.2 | Jy km s^-1 | 2 | $^{12}$CO(3-2) / 350 / 460 / 31.3$\pm$3.2 / 3.35$\pm0.6$ |
| 12CO(3-2) line FWHM | 350 | not stated | km s^-1 | 2 | $^{12}$CO(3-2) / 350 / 460 / 31.3$\pm$3.2 / 3.35$\pm0.6$ |
| 12CO(3-2) line FWZI | 460 | not stated | km s^-1 | 2 | $^{12}$CO(3-2) / 350 / 460 / 31.3$\pm$3.2 / 3.35$\pm0.6$ |
| Average integrated flux density ratio R_31 (CO(3-2)/CO(1-0)) | 3.35 | 0.6 | dimensionless | 2 | $^{12}$CO(3-2) / 350 / 460 / 31.3$\pm$3.2 / 3.35$\pm0.6$ |
| HCO+(4-3) integrated flux density (S Delta v) | 0.32 | 0.2 | Jy km s^-1 | 2 | HCO$^{+}$(4-3) / 150 / 420 / 0.32$\pm0.2$ / $-$ |
| HCO+(4-3) line FWHM | 150 | not stated | km s^-1 | 2 | HCO$^{+}$(4-3) / 150 / 420 / 0.32$\pm0.2$ / $-$ |
| HCO+(4-3) line FWZI | 420 | not stated | km s^-1 | 2 | HCO$^{+}$(4-3) / 150 / 420 / 0.32$\pm0.2$ / $-$ |
| HNCO(6-5) velocity-integrated flux upper limit | <28 | not stated | Jy beam^-1 km s^-1 | 2 | HNCO(6-5) / 340 / $-$ / $<28$ / |
| SiO(3-2) velocity-integrated flux upper limit | <28 | not stated | Jy beam^-1 km s^-1 | 2 | SiO(3-2) / 340 / $-$ / $<28$ / |
| Total molecular gas mass (M_mol) | 1.4e8 | +/- 0.2e8 (random) +/- 0.3e8 (systematic) | M_sun | 3 | The estimated molecular gas mass is $(1.4\pm0.2\pm0.3)\times10^{8}$ M~$\odot$~. |
| Inner high-excitation gas excitation temperature (T_ex) | >=50 | not stated | K | 4 | Assuming local thermodynamic equilibrium (LTE) and optically thin conditions, CO ratios $\gtrsim12$ imply gas excitation temperatures $T_{\rm ex} \gtrsim50$ K (cite: Oosterloo17). |
| Spatially-resolved HCO+(4-3)/CO(2-1) flux density ratio (R_HCO) | 0.1 to 0.7 | not stated | dimensionless | 4 | The R$_{\rm HCO}$ values are found to vary from $\approx0.1$ to $\approx 0.7$, much higher than those typically observed in unperturbed gas regions (cite: Oosterloo17). |
| CO(3-2) kinematic position angle (PA) | 190-250 | not stated | deg | 5 | (1) / Kinematic position angle, PA / (deg) / 190$-$250 |
| CO(3-2) disc inclination (i) | 20-80 | not stated | deg | 5 | (2) / Disc inclination, $i$ / (deg) / 20$-$80 |
| CO(3-2) disc scale length (R_disc) | 3.1 | 0.3 | arcsec | 5 | (3) / Disc scale length, R$_{\rm disc}$ / (arcsec) / 3.1$\pm0.3$ |
| CO(3-2) maximum circular velocity (v_flat) | 345 | 5 | km s^-1 | 5 | (4) / Max circular velocity, v$_{\rm flat}$ / (km s$^{-1}$) / 345$\pm$5 |
| CO(3-2) rotation curve turnover radius (r_turn) | 2.6 | 0.2 | arcsec | 5 | (5) / Rotation curve turn over radius, r$_{\rm turn}$ / (arcsec) / 2.6$\pm0.2$ |
| CO(3-2) intrinsic gas velocity dispersion (sigma_gas) | 41 | 3 | km s^-1 | 5 | (6) / Velocity dispersion, $\sigma_{\rm gas}$ / (km s$^{-1}$) / 41$\pm3$ |
| Jet-induced outflow gas mass (M_out) | 5.6e4 | not stated | M_sun | 5 | Assuming $T_{\rm ex}=50$ K for an average $R_{\rm 31}\approx12$ in the high-excitation regions, we get $X_{\rm CO}= 2.5\times10^{19}$ cm$^{2}$ (K km s$^{-1}$)$^{-1}$ and $M_{\rm out} = 5.6 \times 10^{4}$ M$_{\odot}$. |
| Jet-induced maximum outflow velocity (v_max) | 200 | not stated | km s^-1 | 5 | Assuming $R_{\rm max}=300$ pc (i.e. the maximum extent of regions C and D in Figure 13) and $v_{\rm max}=200$ km s$^{-1}$, we obtain $\dot{M} \lesssim 0.12$ M$_{\odot}$ yr$^{-1}$. |
| Jet-induced mass outflow rate (M_dot) | <=0.12 | not stated | M_sun yr^-1 | 5 | Assuming $R_{\rm max}=300$ pc (i.e. the maximum extent of regions C and D in Figure 13) and $v_{\rm max}=200$ km s$^{-1}$, we obtain $\dot{M} \lesssim 0.12$ M$_{\odot}$ yr$^{-1}$. |
| Total radio-to-mm continuum spectral index (alpha_tot) | -0.49 | 0.03 | dimensionless | 6 | The resulting best-fitting spectral indices are $\alpha_{\rm tot}=-0.49\pm0.03$ for the total continuum, $\alpha_{\rm core}=-0.3\pm0.2$ for the core component, and $\alpha_{\rm jet}=-0.73\pm0.01$ for the jet component. |
| Core radio-to-mm continuum spectral index (alpha_core) | -0.3 | 0.2 | dimensionless | 6 | The resulting best-fitting spectral indices are $\alpha_{\rm tot}=-0.49\pm0.03$ for the total continuum, $\alpha_{\rm core}=-0.3\pm0.2$ for the core component, and $\alpha_{\rm jet}=-0.73\pm0.01$ for the jet component. |
| Jet radio-to-mm continuum spectral index (alpha_jet) | -0.73 | 0.01 | dimensionless | 6 | The resulting best-fitting spectral indices are $\alpha_{\rm tot}=-0.49\pm0.03$ for the total continuum, $\alpha_{\rm core}=-0.3\pm0.2$ for the core component, and $\alpha_{\rm jet}=-0.73\pm0.01$ for the jet component. |
| Dust mass in regions co-spatial with molecular gas (M_dust) | 2.5e5 | not stated | M_sun | 7 | The estimated dust mass in the regions co-spatial with the molecular gas is then $2.5\times10^5$ M$_{\odot}$. |
| Molecular gas-to-dust mass ratio (M_gas/M_dust) | 560 | not stated | dimensionless | 7 | These values imply a molecular $M_{\rm gas}/M_{\rm dust}=560$ and a gas-phase metallicity $<$7.9, which about six times smaller than the solar metallicity. |
| Gas-phase metallicity 12 + log10(O/H) | <7.9 | not stated | dimensionless | 7 | These values imply a molecular $M_{\rm gas}/M_{\rm dust}=560$ and a gas-phase metallicity $<$7.9, which about six times smaller than the solar metallicity. |

## Qualitative findings

- CO(1-0), CO(2-1), and CO(3-2) show distinct spatial morphologies: CO(1-0) has a central gap, CO(2-1) has a ring-like structure, and CO(3-2) shows a full disc peaking towards the core, indicating higher excitation in the inner regions.  
  > "As a result, also the gas morphology changes: a gap is observed at the centre of the CO(1-0) distribution, whereas the CO(2-1) and CO(3-2) lines shows a ring-like and full disc morphology, respectively." (Moment maps)
- Millimetre continuum up to 348 GHz shows the same compact core-double lobe structure as at 5 and 10 GHz and is dominated by non-thermal synchrotron emission with no clear evidence of thermal dust emission.  
  > "The great morphological similarity between the continuum emission over this wide range of frequencies suggests that the continuum of NGC 3100 is dominated by non-thermal synchrotron emission from the core and extended radio structures up to at least 348 GHz." (Continuum emission)
- HCO+(4-3) is tentatively detected at 5 sigma in an unresolved blob 2 arcsec west of the core at blueshifted velocities on the receding CO side, suggesting kinematic decoupling and jet-induced compression.  
  > "Interestingly, HCO$^{+}$(4-3) emission is detected only at blueshifted velocities (see Section 4.2), while it is located in a small region of the receding (i.e. redshifted) CO side." (Moment maps); "This suggests that the two molecular species have opposite velocity gradients (i.e. they are kinematically-decoupled) in that region." (Moment maps)
- SiO(3-2) and HNCO(6-5) shock tracers are undetected, which together with faint HCO+(4-3) may indicate a deficiency of very dense (n_crit > 10^6 cm^-3) cold gas in the inner regions.  
  > "The SiO(3-2) and HNCO(6-5) shock tracers are undetected: this - along with the tentative HCO$^{+}$(4-3) detection - may be consistent with a deficiency of very dense (i.e. $n_{\rm crit} > 10^{6}$ cm$^{-3}$) cold gas in the central regions of NGC 3100." (Abstract)

## Claim tuples

- H: Expanding radio jets and lobes in the LERG NGC 3100 interact with the surrounding molecular gas, altering its excitation conditions. | E: Create resolution-matched, spatially-resolved flux density ratio maps R_21 = S_CO(2-1)/S_CO(1-0) and R_31 = S_CO(3-2)/S_CO(1-0) and compare them spatially with 10 GHz JVLA radio continuum lobes. | R: Two components are found: an outer low-excitation component (ratios ~1-4) and an inner high-excitation component spatially correlated with the radio lobes where R_21 >= 8 and R_31 >= 12, implying optically thin gas with T_ex >= 50 K. | F: The expanding radio plasma is driving a jet-ISM interaction that strongly alters the excitation conditions of the inner circumnuclear molecular gas. | **supported**
- H: Non-circular motions in the central molecular disc of NGC 3100 are driven by both a nuclear spiral perturbation and a radio jet-driven outflow that strongly perturbs the gas kinematics. | E: Fit a 3D warped rotating disc + two-armed spiral model to the CO(3-2) cube using KinMS_MCMC, inspect velocity residuals along major and minor axes, and extract local spectra in residual regions A, B, C, and D. | R: Bulk gas is in regular rotation, with two non-rotational components: major-axis inflow/outflow streaming motions (+90 and -250 km s^-1) at the spiral arms, and a minor-axis jet-driven outflow with v_max ~ 200 km s^-1, M_out = 5.6 x 10^4 M_sun, and M_dot <= 0.12 M_sun yr^-1. | F: Two non-circular components (spiral streaming and jet-induced outflow) are confirmed, but the jet-CO coupling only mildly affects the gas kinematics with negligible global impact, much weaker than predicted by simulations or seen in Seyfert-like jet-ISM systems. | **partially**
- H: Jet-ISM interaction in NGC 3100 compresses the gas and drives shocks detectable in dense gas (HCO+(4-3)) and shock tracers (SiO(3-2), HNCO(6-5)). | E: Image HCO+(4-3), SiO(3-2), and HNCO(6-5) data cubes at 105 km s^-1 channel width and map the HCO+(4-3)/CO(2-1) line ratio relative to the radio lobes. | R: HCO+(4-3) is tentatively detected (5 sigma) adjacent to the base of the radio lobe with R_HCO up to ~0.7, while SiO(3-2) and HNCO(6-5) are undetected (< 0.15 mJy beam^-1). | F: The tentative HCO+(4-3) detection is consistent with localized jet-induced gas compression, while the non-detection of shock tracers and faintness of HCO+(4-3) suggest an intrinsic deficiency of very dense (n_crit > 10^6 cm^-3) gas. | **partially**
- H: The cold gas and dust reservoir in NGC 3100 was externally accreted via galaxy interaction rather than internally generated by stellar mass loss or halo cooling. | E: Compare the spatial distribution of CO(1-0) and optical B-I dust extinction, estimate dust mass in co-spatial regions, and compute the molecular gas-to-dust ratio and gas-phase metallicity. | R: CO(1-0) and dust are tightly co-spatial in the central structure and eastern patch, with M_gas/M_dust = 560 (>= 200 across X_CO uncertainties) and sub-solar metallicity 12+log10(O/H) < 7.9. | F: The strongly sub-solar metallicity and dust-CO co-spatiality rule out internal stellar/cooling origin and confirm external accretion, likely from the gas-rich companion NGC 3095. | **supported**

## Reasoning

- Why this data: Multiple CO transitions probe gas excitation temperature and density, HCO+(4-3) traces dense gas (n_crit > 10^4 cm^-3), SiO(3-2) traces fast shocks (v > 50 km s^-1), HNCO(6-5) traces slow shocks (v < 20 km s^-1), and NGC 3100 showed clear signs of jet-CO interaction in previous CO(2-1) and JVLA data.  
  > "Higher-$J$ transitions require rapidly increasing densities and temperatures to be excited (i.e. $n_{\rm crit} \propto J^{3}$ and $T_{\rm ex} \propto J^{2}$; (cite: Bolatto13)), therefore ratios of multiple CO lines can be used to probe the excitation temperature and density of molecular gas" (Introduction); "A multi-species approach is therefore key to properly characterise the impact of jet-induced feedback on the physics of the surrounding cold gas." (Introduction)
- Why this method: Natural weighting maximizes sensitivity to extended emission; masked moment maps recover flux while minimizing noise; 3D kinematic modelling with KinMS accounts for beam smearing and separates warps from non-circular motions; local spectral extraction avoids flux-weighting biases of moment 1 residual maps.  
  > "All the continuum maps were made using natural weighting in order to maximise the sensitivity, with the goal of imaging extended emission from the radio source." (Continuum imaging); "Full kinematic modelling is the only way to derive reliable estimates of the intrinsic gas velocity dispersion" (Moment maps); "Caution is needed, however, as interpreting the gas motions from the sole residual map may lead to draw inaccurate conclusions. This is because - by definition - the mean line-of-sight velocities are flux density-weighted and thus biased towards the brighter components." (CO kinematics)
- Alternative: Merger-induced shocks as the cause of enhanced HCO+ emission (rejected in favour of jet-induced gas compression due to spatial coincidence with the radio lobe base).  
  > "Enhanced dense gas emission can be induced by various type of perturbations (such as merger-induced shocks; (cite: Konig18)). However, Figure 7 clearly shows that the faint HCO$^{+}$(4-3) emission arises from a region adjacent to the base of the southern radio lobe, making a jet-induced gas compression the most likely scenario." (Spatially-resolved line ratios)
- Alternative: Internal gas origin from stellar mass loss or hot halo cooling (rejected because freshly cooled gas is dustless and internally produced gas in ETGs has super-solar metallicity, whereas < 7.9 is measured).  
  > "Indeed, dusty cold gas produced through internal processes (i.e. stellar mass loss and/or hot halo cooling) in ETGs is expected to have a higher abundance of heavy elements (i.e. super-solar metallicities) than ISM acquired from outside the galaxy (cite: Martini13; Davis15)." (CO-dust comparison and gas-phase metallicity: implications for the gas origin)
- How they decided it was enough: _not stated_
- Limitation (authors): Some CO(2-1) and CO(3-2) emission from the detached eastern patch (~2 kpc from centre) may be lost due to primary beam attenuation/limitation at 235 GHz (FoV = 25") and 348 GHz (FoV = 17").  
  > "(at least some) of the CO(2-1) emission of the eastern patch may be lost due to significant primary beam attenuation in that region at 235 GHz" (Moment maps); "Primary beam attenuation/limitation may also explain the non-detection of any emission from the eastern patch in Band 7 observations" (Moment maps)
- Limitation (authors): 3-sigma upper limits on SiO(3-2) and HNCO(6-5) assume all gas is concentrated within the synthesized beam and would be underestimated if distributed on larger scales.  
  > "If the molecular gas is actually distributed on larger scales, the quoted upper limits would be underestimated." (Line widths and profiles)
- Limitation (authors): Poor S/N at the very centre of the CO(3-2) distribution and in the redshifted excess of Region C prevents extracting reliable spectral features or performing Gaussian fits there.  
  > "We note that we also attempted to extract the spectrum of the region at the centre of the gas distribution showing the brightest redshifted residuals, but the poor S/N ratio in that area does not allow to clearly distinguish any spectral feature and carry out a reliable analysis." (CO kinematics); "However, the S/N ratio of the corresponding channels is too low to allow a proper Gaussian fitting and thus robustly identifying it as an additional kinematic component." (CO kinematics)
- Limitation (authors): Core continuum spectral index alpha_core has large fitting errors due to scatter across multi-epoch observations (possible core variability), and some thermal dust contribution to the unresolved core cannot be excluded.  
  > "although we cannot exclude some contribution from this mechanism to the unresolved core emission." (Continuum emission); "The observed scatter in the data points, however, results in large fitting errors, making $\alpha_{\rm core}$ poorly constrained. Since the various flux measurements are taken at different epochs, we may be observing the effects of core variability." (Continuum emission)
- Limitation (authors): HCO+(4-3) detection is only 5 sigma in 4 channels, too marginal for higher moment maps or firm conclusions without other dense/shock gas transitions.  
  > "The significance of the detection is not sufficient to produce reliable higher moment maps (line emission can be identified only in four channels of the data cube, with a peak S/N $=5$; see Table 11 and Section 4.2)." (Moment maps); "This hypothesis, however, currently remains purely speculative, as observations of other HCO$^{+}$ transitions and/or of different dense/shocks gas tracers (such as HCN, HNC, CS, CH$_{3}$OH, etc. ) would be needed to draw more solid conclusions." (Dense and shock gas tracers)
- Limitation (authors): Spatially-resolved HI observations are not yet available, and X_CO is uncertain (especially at low metallicity), making the derived gas-phase metallicity an upper limit with systematic uncertainty.  
  > "Spatially-resolved observations of the atomic hydrogen in NGC 3100 are currently not available. We thus estimate a *molecular* gas-to-dust mass ratio, which thus yields to an upper limit of the actual gas-phase metallicity." (CO-dust comparison and gas-phase metallicity: implications for the gas origin); "Spatially-resolved observations of the atomic hydrogen in NGC 3100 are currently not available." (CO-dust comparison and gas-phase metallicity)
- Caveat (inferred, ours): Inconsistent text regarding the location of the HCO+(4-3) detection relative to the radio lobes: Section 4.4 states it is adjacent to the base of the southern radio lobe, whereas the Abstract, Section 5.2.2, and Summary state northern radio lobe.
- Caveat (inferred, ours): Single-transition CO ratios (R_21, R_31) are interpreted using simple LTE optically thin approximations without non-LTE radiative transfer modelling (e.g., RADEX) to break temperature-density-optical depth degeneracies.
- Caveat (inferred, ours): Outflow mass and rate rely on visually defined velocity channels (dark-grey shaded regions in Regions C and D) rather than multi-component spectral decomposition.

## Reproducibility

- Data public (paper): Raw ALMA data are publicly available at the ALMA archive under project codes 2015.1.01572.S and 2018.1.01095.S.  
  > "The ALMA data used in this article are available to download at the ALMA archive (https://almascience.nrao.edu/asax/; project codes: 2015.1.01572.S and 2018.1.01095.S)." (Data Availability)
- Products in archive: Calibrated data, final data products and original plots are available upon reasonable request to the first author.  
  > "The calibrated data, final data products and original plots generated for the research study underlying this article will be shared upon reasonable request to the first author." (Data Availability)
- Code: KINMS_MCMC public repository referenced (https://github.com/TimothyADavis/KinMS_MCMC); custom calibration/analysis scripts not released.  
  > "https://github.com/TimothyADavis/KinMS_MCMC" (CO kinematics)
- Missing: Exact pixel size and image dimensions for tclean
- Missing: Self-calibration solution intervals and S/N thresholds
- Missing: Exact uv-range tapering/clipping limits used when matching the CO cubes to 1.4" x 0.9"
- Missing: Logarithmic spiral parametrisation values used in the KinMS model
- Missing: Exact coordinates/apertures of Regions A, B, C, and D and exact velocity integration limits for the outflow mass calculation
- Missing: External 5 and 10 GHz JVLA continuum maps and optical B-I colour map needed for SED fitting and dust mass calculation
- Data volume (inferred): Moderate (~20-50 GB raw visibilities across 4 ALMA bands, 12-m array single-pointing observations totaling ~5 hours on-source)
- Score (inferred): 75/5, ALMA project codes, CASA versions, calibrators, channel widths, weighting, cleaning thresholds, and analysis equations/software (KinMS, KinMS_MCMC, lmfit) are clearly documented. Minor deductions for missing self-calibration solints, pixel/image sizes, exact uv-range cuts for resolution matching, and spiral parameter values in KinMS.
- Rediscovery candidate: yes, Both ALMA project codes (2015.1.01572.S and 2018.1.01095.S) are public, the imaging and kinematic modelling recipes use standard public tools (CASA, KinMS_MCMC), and the main findings are quantitative (line fluxes, line ratios R_21 and R_31, molecular gas mass, KinMS rotation parameters, and outflow mass/rate).

## Links

- Method: (cite: Dame11) (Masked moment map creation technique using spatial Gaussian and velocity Hanning smoothing)
- Method: (cite: Davis13) (KinMS 3D kinematic molecular simulation tool and exponential disc modelling)
- Method: (cite: Bolatto13) (CO-to-H2 conversion factor and molecular gas mass relation)
- Method: (cite: Koay15) (3-sigma velocity-integrated flux density upper limit formula for non-detections)
- Method: (cite: Draine07) (Gas-phase metallicity estimation from gas-to-dust mass ratio)
- Method: (cite: Kaviraj12) (Dust mass estimation from optical extinction maps)
- Companion: (cite: Ruffa19a) (Paper I of the series: sample selection and ALMA Cycle 3 Band 6 CO(2-1) and 230 GHz continuum observations)
- Companion: (cite: Ruffa19b) (Paper II of the series: 3D kinematic modelling of the CO(2-1) discs in the sample)
- Companion: (cite: Ruffa20) (Paper III of the series: high-resolution JVLA 10 GHz radio continuum observations and jet-ISM comparison)
- Related: The AGN fuelling/feedback cycle in nearby radio galaxies

## Checks

```json
{
 "quotes": 215,
 "quotes_ok": 215,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 13,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 37,
 "numeric_problems": 0,
 "fill": {
  "facts": 109,
  "stated": 90,
  "rate": 0.826
 },
 "evidence_ok": true
}
```

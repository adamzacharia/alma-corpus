# Kinematical Signs of Dust Trapping and Feedback in a Local Pressure Bump in the Protoplanetary Disk around HD 142527 Revealed with ALMA

`2020ApJ...905...89Y` | The Astrophysical Journal 2020 | first author: Yen, Hsi-Wei | arXiv: 2010.13990 | DOI: 10.3847/1538-4357/abc55a

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: Does the gas kinematics (deviation from Keplerian rotation) in the HD 142527 disk reveal a local pressure bump, and how does it relate to the dust density, gas-to-dust mass ratio and dust beta (dust trapping and feedback)?  
  > "comparing the dust distributions with the deviation of gas motion from Keplerian rotation in protoplanetary disks could shed light on dust properties and mechanisms of dust concentration" (Introduction); "we analyze the gas kinematics traced by the CO isotopologue lines in comparison with Keplerian rotation" (Introduction)
- Target **HD 142527**: coordinates _not stated_; z/distance 156 pc  
  > "The distance to HD 142527 is 156 pc, measured with the" (Introduction); "mission (cite: Gaia16; Gaia18)" (Introduction); distance from Gaia (cite: Gaia16; Gaia18)  
  > "The distance to HD 142527 is 156 pc, measured with the" (Introduction); "mission (cite: Gaia16; Gaia18)" (Introduction)

## Data provenance

- ALMA projects: 2012.1.00631.S, 2012.1.00725.S, 2013.1.00305.S, 2013.1.00670.S, 2015.1.00614.S, 2015.1.01137.S, 2015.1.01353.S, 2017.1.00987.S
- bands: Continuum at 3, 2 (2.1 in Table 2), 1.3, 0.9, 0.6 and 0.4 mm; Table 1 lists frequency bands 3, 4, 6, 7, 8 and 9 across the eight projects  
  > "We retrieved the data of the continuum emission at 3 mm, 2 mm, 1.3 mm, 0.9 mm, 0.6 mm, and 0.4 mm" (Data)
- frequencies and spectral setup: 13CO and C18O J = 1-0, 2-1 and 3-2 lines plus continuum; rest frequencies and spectral windows not stated; image channel widths 0.05 to 0.2 km/s (Table 2)  
  > "$^{13}$CO and C$^{18}$O (1–0, 2–1, and 3–2) lines in the protoplanetary disk around HD 142527 obtained with ALMA" (Summary)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: Per-project uv ranges from 7-1216 k$\lambda$ (2017.1.00987.S) to 17-1789 k$\lambda$ (2012.1.00631.S); see Table 1  
  > "7–1216 k$\lambda$" (Table 1); "17–1789 k$\lambda$" (Table 1)
- angular resolution: Original synthesized beams about 0.2-0.43 arcsec; all images convolved to a 0.45 arcsec beam for the joint analysis  
  > "Then all the images were convolved to a beam with a size of 0.45$''$ for the joint analysis." (Data)
- max recoverable scale: 3.4 arcsec to 18.7 arcsec across bands, larger than the disk diameter  
  > "range from 3.4$''$ to 18.7$''$, and are all larger than the diameter of the HD 142527 disk" (Data)
- sensitivity: Image noise levels per continuum band and line listed in Table 2 (original beam, before convolution)  
  > "This table summarizes the original synthesized beams and noise levels of the images." (Table 2)
- time on source: Per project 23 mins (2015.1.00614.S) to 226 mins (2013.1.00670.S); see Table 1  
  > "226 mins" (Table 1); "23 mins" (Table 1)
- observing dates: _not stated_
- pi or archival as stated: Archival ALMA data retrieved from the ALMA archive  
  > "We analyzed the archival data of the continuum emission at six wavelengths from 3 to 0.4 mm and" (abstract)
- Line: 13CO J = 1-0, 2-1, 3-2 (not stated)
- Line: C18O J = 1-0, 2-1, 3-2 (not stated)
- Other facility **Gaia**: Distance to HD 142527 of 156 pc  
  > "The distance to HD 142527 is 156 pc, measured with the" (Introduction)
- External data: Distance of 156 pc  
  > "The distance to HD 142527 is 156 pc, measured with the" (Introduction) [from Gaia Collaboration (cite: Gaia16; Gaia18)]
- External data: Dust absorption coefficient kappa_nu = 10 (nu/1000 GHz)^beta g cm^-2 used to convert optical depth to dust surface density  
  > "We adopted the function of the dust absorption coefficient in (cite: Beckwith90)" (3.1 Dust distribution) [from (cite: Beckwith90)]
- External data: Analytic vertical temperature and density (pressure) profiles in hydrostatic equilibrium used for the C18O model  
  > "we adopted the vertical temperature and density profiles derived in (cite: Lee15)" (3.2 Gas distribution) [from (cite: Lee15)]
- External data: Constant C18O abundance of 2e-7, set to zero where temperature is below 20 K  
  > "The C$^{18}$O abundance was assumed to be a constant of $2\times10^{-7}$ (cite: Wilson94; Jorgensen04)" (3.2 Gas distribution) [from (cite: Wilson94; Jorgensen04)]
- External data: Absolute flux calibration uncertainties of 5% (Bands 3, 4), 10% (Bands 6, 7), 20% (Bands 8, 9)  
  > "of 5% in Band 3 and 4, 10% in Band 6 and 7, and 20% in Band 8 and 9 were considered in our error estimate." (3.1 Dust distribution); "From the ALMA proposer’s guide." (footnote 2) [from ALMA proposer's guide (footnote 2)]
- External data: Eccentricity 0.2 and pericenter position angle 330 deg used for the eccentric-disk test model, similar to values measured from the dust ring  
  > "These values are similar to those measured from the dust ring traced by the continuum emission (cite: Boehler17)." (Appendix: Maps of residual velocity) [from (cite: Boehler17)]
- External data: Emitting-layer scale height h/r = 0.15 (r/1.0)^1.25 used for the flaring-disk test, similar to HD 163296 13CO (2-1)  
  > "the emitting layer of the $^{13}$CO (2–1) line in the protoplanetary disk around HD 163296 (cite: Teague18)" (Appendix: Maps of residual velocity) [from (cite: Teague18)]
- Simulation/model as data: Authors' own simulated residual velocity maps of a geometrically thin Keplerian disk (2.48 Msun, 156 pc, PA 340 deg, i 26.7 deg) with model errors, eccentricity or an axisymmetric Gaussian pressure bump, used to interpret the observed residual map  
  > "we first computed the expected velocity map of a geometrically thin Keplerian disk around a central star with a mass of 2.48 $M_\odot$." (Appendix: Maps of residual velocity)

## Processing

### Calibration

- pipeline or manual: Archive data calibrated in CASA with ALMA-provided calibration scripts or pipelines; which projects used which, and versions, not stated  
  > "We calibrated the raw visibility data obtained from the archive using the software Common Astronomy Software Applications (cite: McMullin07) with the calibration scripts or pipelines provided by the ALMA observatory." (Data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 5% in Bands 3 and 4, 10% in Bands 6 and 7, 20% in Bands 8 and 9 (included in error estimate)  
  > "of 5% in Band 3 and 4, 10% in Band 6 and 7, and 20% in Band 8 and 9 were considered in our error estimate." (3.1 Dust distribution)
- self calibration: Phase-only self-calibration on the continuum data; solution intervals not stated  
  > "We additionally performed self calibration of phase on the continuum data" (Data)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs weighting; robust = 0 (3 mm), -0.5 (13CO and C18O 1-0), 2 (all other continuum and lines); chosen to give beams close to a common resolution  
  > "All the images were generated with the Briggs weighting." (Data); "The robust parameters were chosen to make the resultant sizes of the synthesized beams of these images to be close to a common resolution." (Data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum subtracted from the line data in the uv domain; line-free channels not stated  
  > "and the continuum was subtracted from the molecular-line data in the *uv* domain." (Data)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Calibrated visibilities of the same line or the continuum in the same band (from different projects) were combined for imaging  
  > "The calibrated visibility data of the same lines or the continuum in the same frequency bands were combined to generate images." (Data)
- smoothing: All images convolved to a common beam for the joint analysis  
  > "Then all the images were convolved to a beam with a size of 0.45$''$ for the joint analysis." (Data)
- final beam: Circular beam of 0.45 arcsec  
  > "All the images were convolved to a circular beam with a size of 0.45$''$." (Appendix: Continuum and molecular-line images)
- final rms: _not stated_

### Inherited from earlier work

- Most continuum and molecular-line datasets were already presented and discussed in earlier papers  
  > "Most of these continuum and molecular-line data have been presented and discussed in detail in the literature" (Data) [from (cite: Christiaens14; Casassus15; Muto15; Perez15; Boehler17; Soon19; Francis20; Yamaguchi20)]
- Detailed description of the DiskFit Keplerian disk models (power-law density and temperature, vertical structure)  
  > "The detail descriptions of the disk models are in (cite: Pietu07)." (3.4 Gas kinematics) [from (cite: Pietu07)]
- Vertical temperature and hydrostatic pressure/density profile formulation (n = 2 analytic solution)  
  > "As derived in (cite: Lee15), with $n=2$, the hydrostatic equilibrium can be solved analytically." (3.2 Gas distribution) [from (cite: Lee15)]
- Dust absorption coefficient law  
  > "We adopted the function of the dust absorption coefficient in (cite: Beckwith90)" (3.1 Dust distribution) [from (cite: Beckwith90)]
- Equations for the velocity field of an eccentric disk  
  > "We followed the equations in (cite: Goodchild06) to compute the motional velocity of an eccentric disk." (Appendix: Maps of residual velocity) [from (cite: Goodchild06)]
- Equations for rotational velocity from gravity and pressure gradient in a pressure bump  
  > "following the equations in (cite: Rosotti20)" (Appendix: Maps of residual velocity) [from (cite: Rosotti20)]

### Not stated but needed to reproduce (our reading)

- Array type (12 m vs 7 m) and configurations of each project, and which execution blocks or MOUS were used
- CASA version and ALMA pipeline version, and which projects used the delivered scripts versus the pipeline; flux, bandpass and phase calibrators
- Self-calibration details: solution intervals, number of iterations, reference antenna, which datasets were self-calibrated and the SNR criteria
- Line-free channels and the spectral windows used to build the continuum and to subtract it in the uv plane (fit order)
- tclean parameters: deconvolver, cell size, image size, masks, threshold, niter, primary-beam correction; the 2 mm vs 2.1 mm label for the same band
- How the continuum peak positions were measured and the images re-centred; which pixels or signal-to-noise cut were used for the per-pixel SED and C18O fits
- SED fit: fitting algorithm, initial values, bounds, how the flux-scale errors were propagated
- C18O radiative-transfer fit: code, minimiser, parameter bounds, how the 20 K freeze-out threshold and the continuum suppression were implemented
- DiskFit: which parameters were free versus fixed, minimiser, assumed distance, channel ranges and masks used
- How the observed peak velocity map was derived (moment, Gaussian peak fit, or other) and how the model peak velocity map was made
- Pressure bump models for Fig. 9: the three 1-sigma widths, the power-law gradient parameters and the parabolic inner profile

## Analysis recipe

1. **Calibrate, self-calibrate, combine, image and align the archival data**: Calibrated raw archive data with ALMA scripts or pipelines, phase self-calibration on continuum, uv-domain continuum subtraction for lines, combined data of the same line or band, Briggs imaging, convolution to a 0.45 arcsec beam, and alignment on the continuum peak in each band  
  > "We calibrated the raw visibility data obtained from the archive using the software Common Astronomy Software Applications (cite: McMullin07) with the calibration scripts or pipelines provided by the ALMA observatory." (Data); "Then we aligned the images obtained in different frequency bands by centering these imaging at the continuum peak positions measured in the corresponding frequency bands." (Data)
   - software: CASA
   - parameter: Briggs weighting with robust values per image in Table 2 (0, -0.5, 2); final circular beam 0.45 arcsec  
  > "All the images were generated with the Briggs weighting." (Data); "All the images were convolved to a circular beam with a size of 0.45$''$." (Appendix: Continuum and molecular-line images)
   - assumption: Missing flux is not an issue because maximum recoverable scales (3.4 to 18.7 arcsec) exceed the disk diameter  
  > "Thus, we expect that our results and joint analysis are not affected by the effects of missing fluxes." (Data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit pixel-by-pixel SED to get dust temperature, optical depth and beta**: Gray-body slab model I_nu = (B_nu(Td) - B_nu(Tbg)) (1 - exp(-tau_nu)) with tau_nu = tau_100GHz (nu/100 GHz)^beta, fitted to the six-wavelength continuum intensities at each position  
  > "We performed simple fitting of spectral energy distributions (SED) using the continuum data at six different wavelengths to derive the dust distribution in the protoplanetary disk around HD 142527." (3.1 Dust distribution); "and we assumed $\tau_\nu$ to be a simple power-law function of frequency," (3.1 Dust distribution)
   - parameter: Free parameters per position: Td, tau_100GHz, beta  
  > "The derived maps of $T_{\rm d}$, $\tau_{\rm 100~GHz}$, and $\beta$ are shown in Fig." (3.1 Dust distribution)
   - parameter: CMB temperature 2.73 K subtracted; absolute flux uncertainties of 5-20% by band included in the error estimate  
  > "$T_{\rm bg}$ is the comic microwave background temperature of 2.73 K" (3.1 Dust distribution); "of 5% in Band 3 and 4, 10% in Band 6 and 7, and 20% in Band 8 and 9 were considered in our error estimate." (3.1 Dust distribution)
   - assumption: Dust scattering not included in the SED model  
  > "The effects of dust scattering were not considered in our simple SED fitting." (3.1 Dust distribution)
   - fitting: _not stated_
   - validation: Test fit at the 1.3 mm peak with 0.9-0.4 mm intensities artificially raised by 20-30%: Td and tau change by 10-30%, beta by 0.1 (<10%)  
  > "We have tested our SED fitting at the 1.3 mm intensity peak by artificially increasing the intensities at 0.9 mm to 0.4 mm by 20% to 30%." (3.1 Dust distribution)
3. **Convert optical depth and beta to dust surface density**: Dust surface density from tau_100GHz and beta using the Beckwith et al. absorption coefficient kappa_nu = 10 (nu/1000 GHz)^beta  
  > "We then estimated the dust surface density from the derived $\beta$ and $\tau_{\rm 100~GHz}$." (3.1 Dust distribution); "We adopted the function of the dust absorption coefficient in (cite: Beckwith90)" (3.1 Dust distribution)
   - assumption: Values depend on the adopted dust absorption coefficient  
  > "We note that the values of the estimated dust surface density in Fig." (3.1 Dust distribution)
   - fitting: _not stated_
   - validation: Compared qualitatively with Soon et al. 2019; trend consistent but values and contrast differ  
  > "This general trend is consistent with the previous results in the literature (cite: Soon19)" (3.1 Dust distribution)
4. **Estimate gas surface density from the C18O (1-0, 2-1, 3-2) spectra**: At each position, LTE radiative transfer through a vertical temperature and hydrostatic density structure plus a thin midplane dust layer, fitted to the three C18O spectra  
  > "we computed the radiative transfer equation assuming the local thermal equilibrium (LTE) condition, integrated the equation along the line of sight," (3.2 Gas distribution); "generated model spectra of the C$^{18}$O (3–2), (2–1), and (1–0) lines to fit the observations for every position in the HD 142527 disk." (3.2 Gas distribution)
   - parameter: Vertical temperature profile exponent n = 2  
  > "Here we adopted $n=2$." (3.2 Gas distribution)
   - parameter: Midplane temperature Tm = dust temperature from the SED fit  
  > "In our calculations, $T_m$ was adopted to the dust temperature." (3.2 Gas distribution)
   - parameter: Atmosphere temperature Ta = peak brightness temperature of 13CO (3-2) without continuum subtraction  
  > "$T_{\rm a}$ was adopted to be the peak brightness temperature of $^{13}$CO (3–2) without continuum subtraction" (3.2 Gas distribution)
   - parameter: Za = one pressure scale height, with stellar mass 2.48 Msun  
  > "computed with the midplane temperature and the stellar mass of 2.48 $M_\odot$" (3.2 Gas distribution); "adopting $Z_{\rm a}$ to be one pressure scale height provides better fits to the observed spectra." (footnote 3)
   - parameter: Model centroid velocity and line width set to the mean of Gaussian fits to the three observed C18O lines  
  > "the centroid velocity and line width of the model spectra were adopted to be the mean centroid velocity and line width of the three C$^{18}$O lines" (3.2 Gas distribution)
   - assumption: C18O abundance 2e-7, zero where temperature is below 20 K (CO freeze-out)  
  > "The C$^{18}$O abundance was assumed to be a constant of $2\times10^{-7}$ (cite: Wilson94; Jorgensen04), and it was set to be zero in the regions where the temperature is below 20 K" (3.2 Gas distribution)
   - assumption: Dust settled to the midplane and thermally coupled with gas, so Td represents the midplane temperature  
  > "Assuming the dust grains have settled to the midplane and are thermally coupled with gas in the HD 142527 disk" (3.2 Gas distribution)
   - assumption: Disk treated as face-on (no inclination correction in the radiative transfer), inclination 26 deg  
  > "We did not consider that the line of sight is inclined with respect to the disk midplane in our radiative transfer calculation" (3.2 Gas distribution)
   - fitting: _not stated_
   - validation: Model fluxes typically match observations within 3 sigma or within 20%  
  > "The fluxes of our model spectra typically match with the observations within the 3$\sigma$ uncertainties, or the difference is less than 20%." (3.2 Gas distribution)
5. **Compute the gas-to-dust mass ratio map**: Ratio of the C18O-derived gas surface density to the SED-derived dust surface density at each position  
  > "With the gas and dust surface density estimated from the C$^{18}$O lines and the continuum, the gas-to-dust mass ratio was computed." (3.3 Gas-to-dust mass ratio)
   - assumption: Absolute ratio scales inversely with the assumed C18O abundance; only the spatial trend is interpreted  
  > "If the C$^{18}$O abundance is ten times lower than our assumed value, the derived gas-to-dust mass ratio becomes ten times higher." (3.3 Gas-to-dust mass ratio)
   - fitting: _not stated_
   - validation: Trend of lower ratios in the north is consistent with Soon et al. 2019  
  > "This trend of the lower gas-to-dust mass ratios in the north than in the south has also been reported by (cite: Soon19)." (3.3 Gas-to-dust mass ratio)
6. **Fit Keplerian disk models to C18O (1-0) and (2-1) in the uv domain**: DiskFit (in GILDAS) axisymmetric Keplerian models with power-law density, temperature and vertical structure; radiative transfer, Fourier transform and sampling at the observed uv coverage, fitted in the uv plane to C18O (1-0) and (2-1) separately  
  > "In this work, we performed the fitting on the C$^{18}$O (1–0) and (2–1) data." (3.4 Gas kinematics); "The fitting of the two lines was performed separately for a consistency check." (3.4 Gas kinematics); "the model images were Fourier transformed and sampled with the same *uv* coverage as the observations" (3.4 Gas kinematics)
   - software: DiskFit, GILDAS
   - parameter: Model parameters in Table 3: Mstar, i, PA, Vsys, N0, p, T0, q, Rin, Rout, H0, h, deltaV (which are free versus fixed not stated)  
  > "$M_\star$, $i$, $PA$, and $V_{\rm sys}$ are the stellar mass, inclination angle, position angle of the major axis, and systemic velocity of the model disks, respectively." (Table 3)
   - assumption: Observed emission approximated as Keplerian rotation around a central point mass; fitted Mstar represents the total binary mass  
  > "We expect that the disk rotation traced by the C$^{18}$O (1–0) and (2–1) lines can be approximated with the Keplerian rotation around a central point mass" (3.4 Gas kinematics)
   - assumption: Models are axisymmetric while the disk is asymmetric, leaving significant residuals  
  > "We note that our model disks are axisymmetric and the observed disk is asymmetric, so that there are significant residuals" (3.4 Gas kinematics)
   - fitting: _not stated_
   - validation: The two lines give identical stellar mass and systemic velocity and differ by less than 1 deg in inclination and position angle; consistent with earlier ALMA 13CO and C18O (3-2) results  
  > "The estimated stellar mass and systemic velocity from the fitting of the two different lines are identical" (3.4 Gas kinematics); "our measured stellar mass and inclination and position angles of the disk are also consistent with the previous results" (3.4 Gas kinematics)
7. **Derive the residual (deviation from Keplerian) velocity map**: Subtracted the peak velocity map of the best-fit C18O (2-1) Keplerian model from the observed C18O (2-1) peak velocity map  
  > "we subtracted the peak velocity map of our best-fit Keplerian disk model of the C$^{18}$O (2–1) line" (5.1 Deviation from Keplerian rotation)
   - parameter: Discussion limited to radii larger than 0.5 arcsec because of the 0.45 arcsec beam and complicated central velocity field  
  > "Thus, in the present work, our discussion focuses on the velocity deviation at radii larger than 0.5$''$." (5.1 Deviation from Keplerian rotation)
   - fitting: _not stated_
   - validation: Simulated residual maps for errors in center, position angle, inclination, emitting-layer height, and eccentricity do not match the observed pattern  
  > "The patterns in the observed residual velocity map are different from those in the simulated residual velocity maps assuming that there are errors in the disk center," (5.1 Deviation from Keplerian rotation); "Nevertheless, the observed velocity deviation is inconsistent with the expectation for an eccentric disk" (5.1 Deviation from Keplerian rotation)
8. **Compare residual velocity with dust, gas-to-dust ratio and beta, and constrain bump versus ring widths**: Overlaid the residual velocity on the dust density, gas-to-dust ratio and beta maps; fitted a Gaussian to the radial dust profile along the NW major axis and compared its width with model velocity deviations of Gaussian pressure bumps in a 2.48 Msun Keplerian disk  
  > "We fitted a Gaussian function to the radial profile of the dust surface density and measured its 1$\sigma$ width to be 0.34$''$." (5.5 Dust feedback in pressure bump); "we computed the expected velocity deviation due to a Gaussian pressure bump centered at a radius of 1.2$''$ in a Keplerian disk around a central star of 2.48 $M_\odot$" (5.5 Dust feedback in pressure bump)
   - parameter: Dust ring width deconvolved with the 0.19 arcsec 1-sigma beam width  
  > "to be 0.28$''$, where 0.19$''$ is the 1$\sigma$ width of the beam size" (5.5 Dust feedback in pressure bump)
   - assumption: Pressure bump width inferred from the separation between bump center and turning point, which is about 1.2 to 1.5 times the bump width for Gaussian profiles  
  > "the separations between the centers of the pressure bumps and the turning points are approximately 1.2 to 1.5 times the widths of the pressure bumps." (5.5 Dust feedback in pressure bump)
   - fitting: _not stated_
   - validation: _not stated_
9. **Simulate residual velocity patterns for model errors, eccentricity and a pressure bump**: Computed velocity maps of a thin Keplerian disk (2.48 Msun, 156 pc, PA 340 deg, i 26.7 deg) with perturbed center (0.04 arcsec), PA (5 deg), inclination (2 deg), flaring emitting layer, eccentricity 0.2, and an axisymmetric Gaussian pressure bump at 1.2 arcsec, then subtracted the unperturbed map  
  > "We computed four cases, (a) by shifting the center by 0.04$''$," (Appendix: Maps of residual velocity); "a constant eccentricity of 0.2 was adopted in the entire disk" (Appendix: Maps of residual velocity)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration of the archival visibility data  
  > "We calibrated the raw visibility data obtained from the archive using the software Common Astronomy Software Applications (cite: McMullin07)" (Data); "CASA (cite: McMullin07)" (Software)
- **DiskFit** : Fitting Keplerian disk models to the C18O data in the uv domain  
  > "which is a package built in the software GILDAS" (3.4 Gas kinematics); "DiskFit (cite: Pietu07)" (Software)
- **GILDAS** : Software package hosting DiskFit  
  > "which is a package built in the software GILDAS" (3.4 Gas kinematics); "GILDAS (cite: Pety05; gildas13)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median fractional uncertainties of Td, tau_100GHz and beta from the SED fit | 18%, 22%, 8% | not stated | percent | 2 | The median uncertainties are 18%, 22%, and 8% in $T_{\rm d}$, $\tau_{\rm 100~GHz}$, and $\beta$, respectively. |
| Dust beta in the northern part of the dust ring | ~1.5-1.8 | not stated | dimensionless | 2 | Our derived $\beta$ of $\sim$1.5–1.8 in the northern part of the dust ring |
| Dust beta from south to north | decreases from two to approximately one | not stated | dimensionless | 2 | the dust $\beta$ decreases from two to approximately one from the southern to northern parts of the disk |
| Gas-to-dust mass ratio range and mean | 0.4 to 9, mean 1.6 | median 50% | dimensionless | 5 | The estimated gas-to-dust mass ratios range from 0.4 to 9 with a mean value of 1.6; with a median uncertainty of 50% |
| Gas-to-dust mass ratio in the northern region relative to disk mean | more than a factor of three lower | not stated | dimensionless | 5 | the gas-to-dust mass ratio is more than a factor of three lower than the mean ratio in the disk |
| Stellar (binary total) mass from Keplerian fit | 2.48 | <5% (noise-only) | Msun | 6 | and the stellar mass of 2.48 $M_\odot$; The uncertainties in the best-fit parameters due to the the noise in the data are less than 5%. |
| Disk inclination from C18O (1-0) | 26.1 | <5% (noise-only) | deg | 6 | 26.1$^\circ$ |
| Disk inclination from C18O (2-1) | 26.7 | <5% (noise-only) | deg | 6 | 26.7$^\circ$ |
| Position angle of the major axis from C18O (1-0) | 340.3 | <5% (noise-only) | deg | 6 | 340.3$^\circ$ |
| Position angle of the major axis from C18O (2-1) | 340.8 | <5% (noise-only) | deg | 6 | 340.8$^\circ$ |
| Maximum redshifted residual velocity at 1.2-1.4 arcsec in the northwest | 0.13 | not stated | km/s | 7 | there is redshifted excess with a maximum residual velocity of 0.13 km s$^{-1}$ in the northwest |
| Velocity deviation at 0.6 arcsec radius | >10% of Keplerian velocity | not stated | percent | 8 | The velocity deviation at a radius of 0.6$''$ is $>$10% of the Keplerian velocity. |
| Minimum velocity deviation at 1.3-1.4 arcsec | -6 | not stated | percent of Keplerian velocity | 8 | The minimum velocity deviation is $-$6% at a radius between 1.3$''$ and 1.4$''$ |
| Dust ring 1-sigma Gaussian width along the NW major axis (observed) | 0.34 | not stated | arcsec | 8 | measured its 1$\sigma$ width to be 0.34$''$ |
| Dust ring width after beam deconvolution | 0.28 | not stated | arcsec | 8 | to be 0.28$''$, where 0.19$''$ is the 1$\sigma$ width of the beam size |
| Inferred 1-sigma width of the pressure bump | 0.2-0.25 | not stated | arcsec | 8 | could suggest the width of the pressure bump to be 0.2$''$–0.25$''$. |

## Qualitative findings

- The continuum is optically thick only at wavelengths shorter than 1 mm  
  > "The continuum in the HD 142527 disk becomes optically thick only at wavelengths shorter than 1 mm." (3.1 Dust distribution)
- Only C18O (1-0) is likely optically thin; 13CO lines are optically thick in upper layers  
  > "suggest that only the C$^{18}$O (1–0) line is likely optically thin" (3.2 Gas distribution)
- No correlation between the beta distribution and the pressure bump location  
  > "there is no correlation between our derived $\beta$ distribution and the location of the pressure bump" (abstract)
- The observed velocity pattern cannot distinguish a vortex from companion-driven spirals as the pressure bump origin  
  > "we are not able to distinguish a pressure bump formed by a vortex or spirals." (5.4 Origins of the pressure bump and dust trapping)

## Claim tuples

- H: Does the HD 142527 disk show super- and sub-Keplerian rotation indicating a local pressure bump? | E: Subtracted the best-fit Keplerian model peak velocity map from the observed C18O (2-1) peak velocity map and checked the residuals against simulated error and eccentricity patterns | R: Blue- and redshifted excesses inside and outside 1.2 arcsec in the northwest (up to 0.13 km/s), not matching model-error or eccentric-disk patterns | F: A local pressure bump at about 1.2 arcsec in the northwest is suggested; the pressure profile is not axisymmetric | **supported**
- H: Is dust trapped in the pressure bump? | E: Compared dust surface density and gas-to-dust ratio maps (SED fit and C18O model) with the residual velocity map | R: The bump region has about three times higher dust density and about three times lower gas-to-dust mass ratio than the disk mean | F: Dust trapping in the pressure bump is suggested | **supported**
- H: Is grain growth (low beta) enhanced in the pressure bump? | E: Compared the SED-derived beta map with the location of the pressure bump | R: beta decreases from south to north but does not correlate with the bump location | F: No evidence for significant grain growth in the bump, with a caveat that unmodelled dust scattering could bias beta | **partially**
- H: Is dust feedback significant in the pressure bump? | E: Compared the Gaussian width of the dust ring with the pressure bump width inferred from the velocity deviation profile and Gaussian bump models | R: Dust ring width 0.28 arcsec versus inferred bump width 0.2-0.25 arcsec | F: Ring width comparable to or larger than the bump width, a possible hint of dust feedback | **partially**

## Reasoning

- Why this data: HD 142527 has been observed in six ALMA bands, allowing joint multi-wavelength and multi-transition analysis  
  > "HD 142527 has been observed with ALMA in six different frequency bands to date." (Introduction)
- Why this method: Joint continuum and multi-line analysis reduces uncertainty from continuum opacity and line excitation temperature; C18O chosen for gas because C18O (1-0) is possibly optically thin  
  > "to minimize the uncertainties due to the continuum opacity and the excitation temperature of the lines" (Introduction); "we adopted the data of the three C$^{18}$O lines to estimate the gas distribution in the HD 142527 disk because the C$^{18}$O (1–0) line is possibly optically thin." (3.2 Gas distribution)
- Alternative: Za of 1.5 or 2 pressure scale heights tried and rejected in favour of one scale height  
  > "We have also tried $Z_{\rm a}$ of 1.5 or 2 times the pressure scale height and found that adopting $Z_{\rm a}$ to be one pressure scale height provides better fits to the observed spectra." (footnote 3)
- Alternative: Eccentric-disk explanation for the velocity deviation rejected  
  > "Nevertheless, the observed velocity deviation is inconsistent with the expectation for an eccentric disk" (5.1 Deviation from Keplerian rotation)
- Alternative: Small grains or strong turbulence (weak trapping without feedback) rejected as explanation for the wide dust ring  
  > "Thus, this scenario of small dust grains or strong turbulence does not match with our observational results" (5.5 Dust feedback in pressure bump)
- How they decided it was enough: _not stated_
- Limitation (authors): Absolute gas-to-dust ratios are not interpreted because of uncertain C18O abundance and dust absorption coefficient  
  > "we do not discuss the absolute values of the estimated gas-to-dust mass ratio" (3.3 Gas-to-dust mass ratio)
- Limitation (authors): Dust scattering not modelled in the SED fit  
  > "The effects of dust scattering were not considered in our simple SED fitting." (3.1 Dust distribution)
- Limitation (authors): Velocity features within the 0.45 arcsec beam are uncertain  
  > "any velocity feature within a radius of 0.45$''$ is uncertain due to the beam convolution" (5.1 Deviation from Keplerian rotation)
- Limitation (authors): Axisymmetric Keplerian models leave significant residuals in the asymmetric disk  
  > "We note that our model disks are axisymmetric and the observed disk is asymmetric, so that there are significant residuals" (3.4 Gas kinematics)
- Limitation (authors): Resolution too limited to separate vortex from spiral origin or to resolve the bump profile  
  > "Therefore, with the current data sets, we are not able to distinguish a pressure bump formed by a vortex or spirals." (5.4 Origins of the pressure bump and dust trapping)
- Caveat (inferred, ours): Bump width of 0.2-0.25 arcsec is below the 0.45 arcsec beam, so the dust feedback inference rests on a width estimate from a model comparison, not on a resolved measurement
- Caveat (inferred, ours): Gas density relies on a single assumed C18O abundance and LTE with Ta taken from 13CO (3-2); freeze-out threshold and uniform abundance can bias the gas-to-dust trend
- Caveat (inferred, ours): Dust density uses a fixed Beckwith opacity and no scattering; beta and density in the optically thick bands may be biased where the continuum is thick
- Caveat (inferred, ours): Peak velocity maps from a 0.45 arcsec beam and one line (C18O 2-1) with 0.09 km/s channels give residuals of only about 1 channel; sensitivity to the emitting layer height is only tested in an idealised simulation
- Caveat (inferred, ours): Pressure-bump claim does not independently measure pressure (the derived gas pressure map shows no bump)

## Reproducibility

- Data public (paper): Data retrieved from the ALMA archive under eight project codes  
  > "from the ALMA archive." (Data)
- Products in archive: _not stated_
- Missing: CASA and pipeline versions, calibrators and per-project calibration choices
- Missing: Self-calibration and imaging parameters (line-free channels, masks, cell and image size)
- Missing: Details of the per-pixel SED and C18O model fitting code and error propagation
- Missing: DiskFit setup (free versus fixed parameters, minimiser, distance, masks)
- Missing: Definition of the peak velocity maps and the Gaussian pressure-bump model parameters
- Data volume (inferred): Roughly 100-300 GB of raw data for eight ALMA projects spanning Bands 3-9 (inference, not stated in paper)
- Score (inferred): 2/5, Data are public and the SED and gas-model equations are given, but calibration, imaging, self-calibration and fitting settings are largely unstated and key results are maps rather than tabulated numbers
- Rediscovery candidate: no, Data are public but the imaging and fitting recipe is incomplete, and the main results are spatial maps and model comparisons rather than a few numeric answers

## Links

- Method: (cite: Pietu07) (DiskFit Keplerian disk model description)
- Method: (cite: Lee15) (Vertical temperature and hydrostatic density profile used for the C18O model)
- Method: (cite: Beckwith90) (Dust absorption coefficient used for dust surface density)
- Method: (cite: Goodchild06) (Eccentric disk velocity equations)
- Method: (cite: Rosotti20) (Pressure bump rotation equations)
- Companion: (cite: Soon19) (Earlier ALMA analysis of gas and dust (3 mm and 0.9 mm) in HD 142527, compared throughout)
- Companion: (cite: Casassus15) (Earlier multi-band dust SED analysis including ATCA 8.8 mm, compared for beta)
- Companion: (cite: Boehler17) (Earlier ALMA 13CO and C18O (3-2) analysis of the disk, compared for Keplerian fit)
- Companion: (cite: Muto15) (Earlier ALMA study of the gas and dust distributions)

## Checks

```json
{
 "quotes": 147,
 "quotes_ok": 147,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 8,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 16,
 "numeric_problems": 0,
 "fill": {
  "facts": 121,
  "stated": 88,
  "rate": 0.727
 },
 "evidence_ok": true
}
```

# The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: Constraining the Molecular Content at log(M<SUB>*</SUB>/M<SUB>☉</SUB>) ∼ 9.5 with CO Stacking of MUSE-detected z ∼ 1.5 Galaxies

`2020ApJ...902..113I` | The Astrophysical Journal 2020 | first author: Inami, Hanae | arXiv: 2009.10843 | DOI: 10.3847/1538-4357/abba2f

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies
- Question: How much molecular gas do z~1.5 MUSE-detected galaxies hold, as a function of stellar mass and offset from the main sequence, measured by stacking ASPECS Band 3 CO spectra at MUSE redshifts (including below log M* = 10)?  
  > "We report molecular gas mass estimates obtained from a stacking analysis of CO line emission in the ALMA Spectroscopic Survey (ASPECS) using the spectroscopic redshifts from the optical integral field spectroscopic survey" (abstract); "Below this stellar mass, we present a new constraint on the molecular gas content of $z\sim1.5$ main-sequence galaxies by stacking based on the MUSE detections." (abstract)
- Target **MUSE-detected galaxies in the HUDF/XDF (111 stacked for CO(2-1))**: coordinates ASPECS LP pointing centre (RA, Dec) = (03:32:38.5, -27:47:00); individual galaxy positions not tabulated  
  > "With a total of 17 pointings centered at (RA, Dec) $=$ (03:32:38.5, -27:47:00), which completely cover the Pilot region" (2.1 ASPECS observations and data); "For our main target emission line, CO(2-1), the ALMA Band 3 scan offers redshift coverage of $z=1.0059-1.7387$." (2.1 ASPECS observations and data); "We refer to (cite: Inam17) for details about the redshift determination and redshift catalogs of the MUSE-HUDF field." (2.2 MUSE observations and data); z/distance CO(2-1) selection z = 1.0059-1.7387; main-sequence reference z = 1.43; flat LCDM H0 = 70 km/s/Mpc, Omega_m = 0.3  
  > "With a total of 17 pointings centered at (RA, Dec) $=$ (03:32:38.5, -27:47:00), which completely cover the Pilot region" (2.1 ASPECS observations and data); "For our main target emission line, CO(2-1), the ALMA Band 3 scan offers redshift coverage of $z=1.0059-1.7387$." (2.1 ASPECS observations and data); "We refer to (cite: Inam17) for details about the redshift determination and redshift catalogs of the MUSE-HUDF field." (2.2 MUSE observations and data); distance from MUSE spectroscopic redshifts (cite: Inam17; cite: Baco17)  
  > "With a total of 17 pointings centered at (RA, Dec) $=$ (03:32:38.5, -27:47:00), which completely cover the Pilot region" (2.1 ASPECS observations and data); "For our main target emission line, CO(2-1), the ALMA Band 3 scan offers redshift coverage of $z=1.0059-1.7387$." (2.1 ASPECS observations and data); "We refer to (cite: Inam17) for details about the redshift determination and redshift catalogs of the MUSE-HUDF field." (2.2 MUSE observations and data)

## Data provenance

- ALMA projects: _none stated_
- bands: ALMA Band 3 (ASPECS Pilot + Large Program combined)  
  > "In this work, we used the combined data of the ASPECS Pilot and LP surveys taken with ALMA Band 3." (2.1 ASPECS observations and data)
- frequencies and spectral setup: Full Band 3 frequency scan, 84-115 GHz; channels rebinned to 7.813 MHz (23.5 km/s at 99.5 GHz)  
  > "ASPECS LP carried out a full frequency scan in Band 3 ($84-115$ GHz) over the XDF, which resides in the HUDF." (2.1 ASPECS observations and data); "The frequency channel was rebinned to 7.813 MHz ($23.5\,{\rm km\,s^{-1}}$ at 99.5 GHz)." (2.1 ASPECS observations and data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-3  
  > "With the C40-3 array configuration, we obtained a synthesized beam size of" (2.1 ASPECS observations and data)
- baselines: _not stated_
- angular resolution: 1.75'' x 1.49'', PA 91.5 deg at ~99.5 GHz (natural weighting)  
  > "$1.75\ensuremath{''} \times 1.49\ensuremath{''}$ with a position angle $91.5\deg$ at $\approx 99.5\,{\rm GHz}$ by using natural weighting in CASA when imaging the data." (2.1 ASPECS observations and data)
- max recoverable scale: _not stated_
- sensitivity: ~0.2 mJy/beam per 7.813 MHz channel; 5 sigma CO(2-1) L' > 1.4e9 K km/s pc^2 for 200 km/s line width  
  > "The sensitivity for this channel bin size was $\sim 0.2\,{\rm mJy\,beam^{-1}}$ throughout the entire scanned frequency range." (2.1 ASPECS observations and data); "The $5\sigma$ CO(2-1) line sensitivity is $> 1.4 \times 10^9 \, {\rm K\,km\,s^{-1}\,pc^2}$ assuming a line width of $200\,{\rm km\,s^{-1}}$." (2.1 ASPECS observations and data)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: ASPECS Pilot and Large Program survey data; survey strategy and reduction given in earlier ASPECS papers  
  > "The detailed survey strategy and data reduction of the ASPECS Pilot and Large Program surveys are presented in (cite: Walt16) and (cite: Gonz19), respectively." (2.1 ASPECS observations and data)
- Line: CO 2-1 (230.538 GHz)
- Line: CO 3-2, 4-3, 5-4, 6-5 (higher-J stacks) (not stated)
- Other facility **VLT/MUSE (MUSE-HUDF survey)**: Spectroscopic redshifts (and positions) of galaxies used to place the stacks; [O II] emitters dominate the CO(2-1) sample  
  > "The MUSE spectroscopic redshifts were measured from the spectral features in the extracted spectra." (2.2 MUSE observations and data); "In this work, we only use the reliable MUSE redshifts of confidence levels 2 and 3." (2.2 MUSE observations and data)
- Other facility **HST, ground-based, Spitzer and Herschel photometry**: UV-to-IR photometry for MAGPHYS SED fits giving SFR and stellar mass  
  > "These photometry catalogs and data include ultraviolet to infrared from the *HST*, various ground-based telescopes, and all of the *Spitzer* IRAC channels." (2.3 Ancillary data)
- External data: ASPECS Band 3 data cube and the blind-search CO line detections (16 sources, 11 as CO(2-1))  
  > "Using the same data cube, (cite: Gonz19) reported CO emission line detections from an unbiased blind search without prior knowledge of source positions and observed CO frequencies." (2.1 ASPECS observations and data); "They found 16 high significance CO emitting sources, among which 11 were identified as CO(2-1) emission." (2.1 ASPECS observations and data) [from (cite: Gonz19)]
- External data: Molecular gas properties of the directly detected ASPECS CO sources, used for comparison  
  > "(cite: Arav19) assessed the molecular gas properties of these sources, which will be used for comparison in this paper." (2.1 ASPECS observations and data) [from (cite: Arav19)]
- External data: MUSE-HUDF spectroscopic redshift catalog (confidence >= 2 used) and MUSE data  
  > "We refer to (cite: Inam17) for details about the redshift determination and redshift catalogs of the MUSE-HUDF field." (2.2 MUSE observations and data) [from (cite: Inam17); (cite: Baco17)]
- External data: UVUDF catalog coordinates for prior-based MUSE spectral extraction  
  > "The MUSE spectra were extracted with two methods: prior extractions based on the UVUDF catalog (cite: Rafe15) and a blind search for emission lines in the data cubes." (2.2 MUSE observations and data) [from (cite: Rafe15)]
- External data: Optical and near-infrared photometric catalogs for SED fitting  
  > "We assembled optical and near-infrared photometric data from (cite: Skel14)." (2.3 Ancillary data) [from (cite: Skel14)]
- External data: ALMA 1.2 and 3 mm photometry from ASPECS used in the SED fits of CO/continuum-detected sources  
  > "the ALMA 1.2 and 3 mm photometry from the ASPECS data (cite: Gonz19; Gonz20) were also used for the SED fitting for a subset of the sources whose CO or continuum emission was detected." (2.3 Ancillary data) [from (cite: Gonz19; Gonz20)]
- External data: Main-sequence relation (Eq. 11) used to classify galaxies as MS / above / below  
  > "The SSFR classification was based on the main-sequence (MS) relation from Eq.11 of (cite: Boog18), using the mean redshift of the CO(2-1) line detectable in Band 3 (cite: Walt16)." (3.2 Sample selection) [from (cite: Boog18)]
- External data: CO excitation ratio r21 = 0.76 +/- 0.09  
  > "We assume $r_{21}=0.76 \pm 0.09$ following (cite: Dadd15)." (5.1 CO Luminosities and Molecular Gas Masses) [from (cite: Dadd15); alternative r21 = 0.75 +/- 0.11 from (cite: Boog20)]
- External data: alpha_CO = 3.6 Msun (K km/s pc^2)^-1 for log M* > 10  
  > "which is one of the best estimates for high-redshift main-sequence star-forming galaxies (cite: Dadd10b)." (5.1 CO Luminosities and Molecular Gas Masses) [from (cite: Dadd10b)]
- External data: Metallicity dependence of alpha_CO (factor ~2 and ~3 increase for ~2/3 and ~1/2 solar metallicity)  
  > "Thus, $\alpha_{\rm CO}$ would increase by a factor of $\sim 2$ and $\sim 3$, respectively, compared to galaxies with $\log{(M_*/M_\odot)} > 10.0$ (cite: Genz12; Schr12)." (5.1 CO Luminosities and Molecular Gas Masses) [from (cite: Genz12; Schr12)]
- External data: Cosmological model predictions of molecular gas mass (IllustrisTNG, Santa Cruz SAM) at z = 1.43  
  > "We use the gas mass model predictions at $z=1.43$ (cite: Popp19), which is the mean redshift of the CO(2-1) line detectable in Band 3." (5.2 Molecular gas and stellar mass scaling relation) [from (cite: Popp19)]
- External data: PHIBSS2 molecular gas measurements shown as comparison contours  
  > "For comparison, we also show the contours of the molecular gas measurements from the PHIBSS2 survey (cite: Tacc13; Tacc18; Freu19)." (5.2 Molecular gas and stellar mass scaling relation) [from (cite: Tacc13; Tacc18; Freu19)]
- External data: Molecular gas density from CO-selected ASPECS luminosity functions, compared with this work's rho(H2)  
  > "This value is lower than, but formally consistent with, the value derived in (cite: Deca19) with a different CO selection." (5.3 Molecular gas-to-stellar mass ratio) [from (cite: Deca19)]
- Simulation/model as data: Cosmological galaxy-formation model gas masses (IllustrisTNG, Santa Cruz SAM) compared with stacked gas masses  
  > "We also compare our measurements with cosmological galaxy formation model calculations of molecular gas mass presented in (cite: Popp19)." (5.2 Molecular gas and stellar mass scaling relation)

## Processing

### Calibration

- pipeline or manual: CASA used to calibrate and image the data (pipeline vs manual not stated; details deferred to earlier ASPECS papers)  
  > "The CASA (Common Astronomy Software Applications) software was used to calibrate and image the data." (2.1 ASPECS observations and data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "$1.75\ensuremath{''} \times 1.49\ensuremath{''}$ with a position angle $91.5\deg$ at $\approx 99.5\,{\rm GHz}$ by using natural weighting in CASA when imaging the data." (2.1 ASPECS observations and data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Combined Pilot + LP primary beam response applied after sub-cube extraction  
  > "The primary beam correction using the combined Pilot and LP primary beam response was applied after the sub-cube extraction." (3.1 ALMA spectral extraction and stacking)
- array combination: _not stated_
- smoothing: Spectral Gaussian decimation filter (FWHM 63.2 km/s) before resampling to 27.8 km/s channels  
  > "The effect of this filter was equivalent to performing a linear convolution of the spectrum with an area-normalized Gaussian of FWHM $63.2\,{\rm km\,s^{-1}}$." (3.1 ALMA spectral extraction and stacking)
- final beam: 1.75'' x 1.49'', PA 91.5 deg at ~99.5 GHz  
  > "$1.75\ensuremath{''} \times 1.49\ensuremath{''}$ with a position angle $91.5\deg$ at $\approx 99.5\,{\rm GHz}$ by using natural weighting in CASA when imaging the data." (2.1 ASPECS observations and data)
- final rms: ~0.2 mJy/beam per 7.813 MHz channel (survey cube, before stacking)  
  > "The sensitivity for this channel bin size was $\sim 0.2\,{\rm mJy\,beam^{-1}}$ throughout the entire scanned frequency range." (2.1 ASPECS observations and data)

### Inherited from earlier work

- ASPECS survey strategy and data reduction (calibration, imaging, cube construction)  
  > "The detailed survey strategy and data reduction of the ASPECS Pilot and Large Program surveys are presented in (cite: Walt16) and (cite: Gonz19), respectively." (2.1 ASPECS observations and data) [from (cite: Walt16); (cite: Gonz19)]
- Blind-search CO line detection methods  
  > "We refer the readers to (cite: Gonz19) for comprehensive discussions on the detection methods." (2.1 ASPECS observations and data) [from (cite: Gonz19)]
- MUSE survey and data treatment  
  > "For a more detailed description of the survey and data treatments, see (cite: Baco17)." (2.2 MUSE observations and data) [from (cite: Baco17)]
- HST-to-radio astrometric offset correction (+0.279'' Dec, -0.076'' RA)  
  > "Following (cite: Dunl17), we corrected the known systematic offset of the *Hubble* Space Telescope (*HST*) positions to match the radio astrometric reference frame" (2.2 MUSE observations and data) [from (cite: Dunl17)]
- MUSE redshift determination and catalogs  
  > "We refer to (cite: Inam17) for details about the redshift determination and redshift catalogs of the MUSE-HUDF field." (2.2 MUSE observations and data) [from (cite: Inam17)]
- SED fitting procedure (MAGPHYS high-z extension) for SFR and stellar mass  
  > "See (cite: Boog19) for the detailed process of the SED fitting." (2.3 Ancillary data) [from (cite: Boog19)]
- Gas-mass equation and conditions  
  > "We then adopted the following equation and the same conditions as (cite: Deca16b) to infer molecular gas masses" (5.1 CO Luminosities and Molecular Gas Masses) [from (cite: Deca16b)]
- Correction of Lya-based redshifts to systemic via Lya peak/width correlation  
  > "we tried to recover their systemic redshifts based on an empirical correlation between the Ly$\alpha$ emission peak and the Ly$\alpha$ line width (cite: Verh18)." (4.2 Higher-J CO stacked spectra) [from (cite: Verh18)]
- Depletion-time extrapolation assumption (continuous gas consumption at observed SFR)  
  > "Following the same assumption as (cite: Spil18), if these galaxies continuously consume the existing gas with the observed SFR" (5.4.1 Gas-to-stellar mass ratios) [from (cite: Spil18)]

### Not stated but needed to reproduce (our reading)

- Table of the 111 stacked MUSE sources (IDs, positions, redshifts, confidence, MAGPHYS stellar mass and SFR, MS class); only 10 blind-detected IDs and a few others are named
- ASPECS cube version/product (Pilot + LP combined cube, primary-beam model) and how the combined primary beam response was constructed
- Whether the cube was continuum-subtracted and which channels were treated as line-free; CASA version and task parameters (cell size, robust, deconvolver)
- Which r21 was finally adopted (the text says 'the former' after quoting both 0.76 and 0.75)
- Software/implementation of the stacking, filter and 2D Gaussian fit (no code or package named beyond astropy and CASA)
- Definition of the 'local fluctuations' / central area used for the 3 sigma detection threshold and upper limits, and how the point-source upper limit is converted to flux
- MAGPHYS priors and configuration used for the SED fits
- How rho(H2) and its uncertainty were computed from the stacked bins (volume, bins, weights)
- How flux, r21 and alpha_CO uncertainties were propagated into M_gas and mu_gas
- Exact Lya velocity-offset correction coefficients used for high-J stacks

## Analysis recipe

1. **Select MUSE sources for CO stacking**: Select MUSE sources with spec-z in the CO line's Band 3 redshift range, confidence >= 2 and ALMA LP primary beam response >= 50%; same criteria for high-J with different z ranges  
  > "The criteria were the following: (1) $1.0059 \leq {\rm MUSE \ spec-}z \leq 1.7387$, (2) MUSE spec$-z$ confidence levels $\geq 2$, and (3) location within ALMA Band 3 LP primary beam response $\geq 50\%$." (3.2 Sample selection); "For high-$J$ CO emission, we used the same selection criteria, except for the redshift range." (3.2 Sample selection)
   - parameter: 111 MUSE sources for CO(2-1) (104 from [O II], 5 absorption, 1 C III], 1 quasar Mg II)  
  > "The resulting number of MUSE sources for stacking CO(2-1) was 111 in total" (3.2 Sample selection); "For 104 sources, the MUSE spectroscopic redshift identifications were based on \[O II\], five sources used absorption features, one source used C III\], and one quasar had strong Mg II emission." (3.2 Sample selection)
   - parameter: High-J redshift ranges: CO(3-2) 2.0088-3.1080, CO(4-3) 3.0115-4.4771, CO(5-4) 4.0142-5.8460, CO(6-5) 5.0166-7.2146  
  > "The ranges were $z=2.0088-3.1080$ for CO(3-2), $z=3.0115-4.4771$ for CO(4-3) $z=4.0142-5.8460$ for CO(5-4) $z=5.0166-7.2146$ for CO(6-5)." (3.2 Sample selection)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive SFR and M* by SED fitting and classify galaxies into stellar-mass and main-sequence bins**: MAGPHYS SED fits at the MUSE redshift; bins of 1.0 dex in log M* (8-12) and above/on/below the Boogaard+18 MS at z = 1.43 using 0.44 dex intrinsic scatter  
  > "we inferred physical parameters such as star formation rate (SFR) and stellar mass ($M_*$) via modeling with the high redshift extension of the Spectral Energy Distribution (SED) fitting code" (2.3 Ancillary data); "we set the bins to have steps of $\log{(M_*/M_\odot)} = 1.0$ over the range $8.0 < \log{(M_*/M_\odot)} \leq 12.0$ (4 bins) with stellar mass" (4.1.2 Stacking in stellar mass and SSFR bins)
   - software: MAGPHYS
   - parameter: MS intrinsic scatter 0.44 dex  
  > "Galaxies lying within, above, and below the intrinsic scatter (0.44 dex" (3.2 Sample selection)
   - parameter: MS relation evaluated at z = 1.43  
  > "based on the main-sequence relation at $z = 1.43$ discussed in" (4.1.2 Stacking in stellar mass and SSFR bins)
   - parameter: Finer 0.5 dex bins used for low-mass MS galaxies (14, 24, 23, 9 sources)  
  > "This smaller bin size results in 14, 24, 23, and 9 MS sources from $8.0 < \log{(M_*/M_\odot)} \leq 8.5$ to $9.5 < \log{(M_*/M_\odot)} \leq 10.0$ in steps of $\log{(M_*/M_\odot)} = 0.5$." (4.1.2 Stacking in stellar mass and SSFR bins)
   - assumption: ALMA 1.2 and 3 mm photometry added to SED fits only for sources with CO or continuum detections  
  > "were also used for the SED fitting for a subset of the sources whose CO or continuum emission was detected." (2.3 Ancillary data)
   - fitting: _not stated_
   - validation: _not stated_
3. **Extract ALMA sub-cubes and spectra at MUSE positions**: 11'' x 11'' x 3000 km/s sub-cube at each MUSE position, then primary beam correction; spectrum noise from region with beam response > 99% scaled by local beam response  
  > "we first extracted a sub-cube centered at the position of each MUSE source with a secure spectroscopic redshift." (3.1 ALMA spectral extraction and stacking); "This sub-cube has a size of $11\ensuremath{''} \times 11\ensuremath{''} \times 3000\,{\rm km\,s^{-1}}$." (3.1 ALMA spectral extraction and stacking); "The uncertainty for each spectrum is then scaled by the combined primary beam response of the location of the objects under consideration." (3.1 ALMA spectral extraction and stacking)
   - software: CASA
   - parameter: Sub-cube 11'' x 11'' x 3000 km/s  
  > "This sub-cube has a size of $11\ensuremath{''} \times 11\ensuremath{''} \times 3000\,{\rm km\,s^{-1}}$." (3.1 ALMA spectral extraction and stacking)
   - fitting: _not stated_
   - validation: _not stated_
4. **Shift to rest frame, filter, resample and mean-stack spectra**: Channel frequencies shifted to rest frame by MUSE z, Gaussian decimation filter applied via Fourier plane, interpolation onto common 27.8 km/s grid, unweighted mean stack  
  > "This conversion was implemented by first shifting the channel frequencies of the spectra to the rest-frame, according to the MUSE redshift." (3.1 ALMA spectral extraction and stacking); "Next, we interpolated the filtered spectrum onto the frequency grid of the stacked spectra." (3.1 ALMA spectral extraction and stacking); "We did not apply any weighting when performing the stack." (3.1 ALMA spectral extraction and stacking)
   - parameter: Common grid: 3000 km/s centred on 230.538 GHz, 27.8 km/s (21.4 MHz) channels, 108 channels (229.395-231.682 GHz)  
  > "we set the final spectral range and the channel width of the extracted spectra to be $3000\, {\rm km\,s^{-1}}$, centered on the CO(2-1) rest-frame frequency ($230.538\,$GHz), and $27.8 \, {\rm km\,s^{-1}}$ ($21.4 \, {\rm MHz}$), respectively." (3.1 ALMA spectral extraction and stacking)
   - parameter: Gaussian filter width set for 40 dB attenuation at the Nyquist folding frequency; equivalent to Gaussian FWHM 63.2 km/s  
  > "In the Fourier plane, the width of the Gaussian filter was set to give an attenuation of 40 dB at the Nyquist folding frequency of half a cycle per channel of the new channel width" (3.1 ALMA spectral extraction and stacking); "The effect of this filter was equivalent to performing a linear convolution of the spectrum with an area-normalized Gaussian of FWHM $63.2\,{\rm km\,s^{-1}}$." (3.1 ALMA spectral extraction and stacking)
   - fitting: _not stated_
   - validation: Random stacks with random redshifts and with random positions (same number as real samples); stack rms falls roughly as 1/sqrt(N)  
  > "We also carried out two different random extractions following the same procedure described above, to produce random stacked spectra for comparisons." (3.1 ALMA spectral extraction and stacking); "The standard deviation of stacked spectra roughly decreases with $1/\sqrt{N}$." (3.1 ALMA spectral extraction and stacking)
5. **Measure stacked CO line fluxes and upper limits**: Coadd moment-0 over 528 km/s around the CO(2-1) frequency, fit a 2D Gaussian with positions free within 1/3 beam and widths fixed to the beam; detection if amplitude > 3 sigma of local fluctuations; otherwise 3 sigma point-source upper limit  
  > "that were coadded between $230.335 \leq \nu_{\rm rest}/{\rm GHz} \leq 230.741$ ($\Delta v = 528\,{\rm km\,s^{-1}}$) centered at the CO(2-1) rest frequency" (4.1.1 Stacking the entire sample); "For each stacked spectrum, we performed a best fit on the 2D image (moment-0) with a 2D Gaussian function to estimate the line flux or upper limit." (3.3 CO line flux and upper limit measurements); "When the CO line was not detected, the standard deviation in the central area of the image was used to evaluate the $3\sigma$ upper limit, assuming a point source." (3.3 CO line flux and upper limit measurements)
   - parameter: Positions free within a radius of 1/3 of the ALMA beam size; widths fixed to the beam size  
  > "The x- and y-positions are allowed to vary in the vicinity of the MUSE positions within a radius of $1/3$ of the ALMA beam size. The widths were fixed to the beam size." (3.3 CO line flux and upper limit measurements)
   - parameter: Detection threshold: fitted amplitude > 3 sigma of local fluctuations  
  > "We considered a CO emission line to have been detected when the amplitude of the fitted Gaussian function was higher than $3\sigma$ of the local fluctuations in the 2D image." (3.3 CO line flux and upper limit measurements)
   - assumption: 300 km/s FWHM line assumed in the flux-loss simulation; no flux-loss scaling applied  
  > "We assumed an emission line with a width of $300\,{\rm km\,s^{-1}}$ (full width at half maximum, FWHM) and performed a bootstrap simulation" (3.3 CO line flux and upper limit measurements); "We do not scale up our measured fluxes in this work to take account of this flux loss, because its impact on our line flux measurements is not significant." (3.3 CO line flux and upper limit measurements)
   - fitting: 2D Gaussian fit to moment-0 images (fit minimiser and error estimation not stated)  
  > "The line flux was estimated by integrating the fitted Gaussian function." (3.3 CO line flux and upper limit measurements)
   - validation: Bootstrap of MUSE redshift errors (sigma_z = 0.00012(1+z)): with 10000 realizations 92% gave less than 3% flux loss  
  > "With 10000 realizations, we found that 92% of them resulted in less than 3% flux loss." (3.3 CO line flux and upper limit measurements)
6. **Convert CO(2-1) flux to line luminosity and molecular gas mass**: L' from the Solomon relation using mean redshift of each bin; M_gas = alpha_CO / r21 x L'  
  > "We employed the following equation to obtain the CO luminosities from the measured CO(2-1) emission (cite: Solo97; Solo05):" (5.1 CO Luminosities and Molecular Gas Masses); "For the redshift ($z$), we used the mean redshift of the galaxies in each stacking bin." (5.1 CO Luminosities and Molecular Gas Masses)
   - parameter: r21 = 0.76 +/- 0.09 (Daddi+15); Boogaard+20 value 0.75 +/- 0.11 also quoted  
  > "We assume $r_{21}=0.76 \pm 0.09$ following (cite: Dadd15)." (5.1 CO Luminosities and Molecular Gas Masses)
   - parameter: alpha_CO = 3.6 (log M* > 10), 7.2 (log M* ~ 9.5), 10.8 (log M* ~ 8.5) Msun (K km/s pc^2)^-1  
  > "We adopt $\alpha_{\rm CO} = 7.2$ and $10.8 \, M_\odot \, ({\rm K\,km\,s^{-1}\,pc^2})^{-1}$ for galaxies with $\log{(M_*/M_\odot)} \sim 9.5$ and $\log{(M_*/M_\odot)} \sim 8.5$, respectively." (5.1 CO Luminosities and Molecular Gas Masses)
   - assumption: Metallicities ~2/3 Zsun at log M* ~ 9.5 and ~1/2 Zsun at ~8.5 drive the alpha_CO increase  
  > "In this work, we assume that the metallicities of galaxies with $\log{(M_*/M_\odot)} \sim 9.5$ and $\sim 8.5$ are $\sim 2/3Z_\odot$ and $\sim 1/2Z_\odot$" (5.1 CO Luminosities and Molecular Gas Masses)
   - assumption: Flat LCDM, H0 = 70 km/s/Mpc, Omega_Lambda = 0.7, Omega_m = 0.3  
  > "A flat $\Lambda$CDM cosmology with $H_0 = 70 \, {\rm km\,s^{-1}\,Mpc^{-1}}$, $\Omega_\Lambda = 0.7$, and $\Omega_m = 0.3$ is adopted throughout this paper." (Introduction)
   - fitting: _not stated_
   - validation: Gas masses with a constant alpha_CO = 3.6 also shown for the low-mass bins for reference  
  > "In these lower stellar mass bins, the $M_{\rm gas}$ estimates with a constant $\alpha_{\rm CO} = 3.6 \, M_\odot \, ({\rm K\,km\,s^{-1}\,pc^2})^{-1}$ are also shown as dotted symbols in figures for reference." (5.1 CO Luminosities and Molecular Gas Masses)
7. **Derive gas-to-stellar mass ratio, depletion time and gas density; compare with PHIBSS2 and models**: mu_gas = M_gas/M*, t_depl = M_gas/SFR for each stack; compare with PHIBSS2 contours and IllustrisTNG/SC SAM predictions at z = 1.43; compute rho(H2) at z~1.5 from the stacked measurements  
  > "molecular gas-to-stellar mass ratio, $\mu_{\rm gas} \equiv M_{\rm gas}/M_*$" (5.3 Molecular gas-to-stellar mass ratio); "The gas depletion time, $t_{\rm depl} = M_{\rm gas}/SFR$, is another way" (5.4.2 Gas depletion time); "The estimated molecular gas density $\rho{\rm (H_2)}$ at $z\sim1.5$, based on our CO(2-1) stacking measurements, is $(0.49 \pm 0.09) \times 10^8 \,{\rm M_\odot\,Mpc^{-3}}$." (5.3 Molecular gas-to-stellar mass ratio)
   - parameter: Measurements used include the directly detected CO(2-1) sources from the blind search  
  > "Because we are interested in global properties of the molecular gas, we use the measurements that include the direct CO(2-1) detections from the blind search." (5.1 CO Luminosities and Molecular Gas Masses)
   - assumption: Model predictions taken at z = 1.43, the mean redshift of CO(2-1) in Band 3  
  > "We use the gas mass model predictions at $z=1.43$ (cite: Popp19), which is the mean redshift of the CO(2-1) line detectable in Band 3." (5.2 Molecular gas and stellar mass scaling relation)
   - fitting: _not stated_
   - validation: Results repeated with the Speagle+14 main-sequence relation in an appendix  
  > "the results are consistent even when the MS relation of (cite: Spea14) is adopted" (Appendix: Comparisons with earlier studies)
8. **Stack higher-J CO lines (CO(3-2) to CO(6-5))**: Same stacking procedure on MUSE sources in the corresponding redshift ranges; Lya-based redshifts corrected to systemic with a Lya peak vs width relation  
  > "The same procedure is adopted for stacking high-$J$ CO lines." (3.1 ALMA spectral extraction and stacking); "we tried to recover their systemic redshifts based on an empirical correlation between the Ly$\alpha$ emission peak and the Ly$\alpha$ line width (cite: Verh18)." (4.2 Higher-J CO stacked spectra)
   - parameter: Intrinsic scatter of the Lya-offset relation +/-73 km/s from 13 sources with Lya and C III]  
  > "The intrinsic scatter of the relation is $\pm 73\,{\rm km\,s^{-1}}$ measured with 13 sources that have both Ly$\alpha$ and C III\] detections." (4.2 Higher-J CO stacked spectra)
   - fitting: _not stated_
   - validation: Stacks re-done after discarding CO(3-2) sources MUSE IDs 35 and 1124 (and pair ID 24): no significant emission remains; consistent with Uzgil+19  
  > "If we discard them, no significant emission remains." (4.2 Higher-J CO stacked spectra)

## Software

- **CASA** : Calibrating and imaging the ASPECS data  
  > "The CASA (Common Astronomy Software Applications) software was used to calibrate and image the data." (2.1 ASPECS observations and data)
- **MAGPHYS (high-z extension)** : SED fitting to derive SFR and stellar mass  
  > "we inferred physical parameters such as star formation rate (SFR) and stellar mass ($M_*$) via modeling with the high redshift extension of the Spectral Energy Distribution (SED) fitting code" (2.3 Ancillary data)
- **astropy** : Listed in the Software section; specific use not stated  
  > "astropy (cite: AsPy13; AsPy18), CASA (cite: McMu07)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total CO(2-1) stacked line flux, entire sample including direct detections (111 spectra) | 0.031 | 0.007 | Jy km/s | 5 | We obtained total line fluxes (upper limit) of $0.031 \pm 0.007 \, {\rm Jy\,km\,s^{-1}}$ ($<0.012\, {\rm Jy\,km\,s^{-1}}$) for the stacked spectra including (excluding) the sources with direct CO(2-1) detections. |
| Total CO(2-1) stacked line flux, entire sample excluding direct detections (101 spectra), 3 sigma upper limit | <0.012 | not stated | Jy km/s | 5 | We obtained total line fluxes (upper limit) of $0.031 \pm 0.007 \, {\rm Jy\,km\,s^{-1}}$ ($<0.012\, {\rm Jy\,km\,s^{-1}}$) for the stacked spectra including (excluding) the sources with direct CO(2-1) detections. |
| CO(2-1) stacked flux, MS, 10 < log M* <= 11 (12 sources; value in parentheses excludes direct detections, 7 sources: 0.095 +/- 0.024) | 0.130 | 0.021 | Jy km/s | 5 | $<0.022$($<0.022$) & $<0.019$($<0.019$) & $0.130 \pm 0.021$($0.095 \pm 0.024$) & $0.453 \pm 0.042$ |
| CO(2-1) stacked flux, MS, 11 < log M* <= 12 (3 sources) | 0.453 | 0.042 | Jy km/s | 5 | $<0.022$($<0.022$) & $<0.019$($<0.019$) & $0.130 \pm 0.021$($0.095 \pm 0.024$) & $0.453 \pm 0.042$ |
| CO(2-1) stacked flux, above MS, 9 < log M* <= 10 (4 sources; excluding direct detection <0.041) | 0.110 | 0.027 | Jy km/s | 5 | $<0.032$($<0.032$) & $0.110 \pm 0.027$($<0.041$) |
| CO(2-1) stacked 3 sigma upper limits, MS bins 8-9 and 9-10 in log M* (38 and 32 sources) | <0.022 and <0.019 | not stated | Jy km/s | 5 | On the MS & $<0.022$($<0.022$) & $<0.019$($<0.019$) |
| CO(2-1) 3 sigma upper limits in 0.5 dex MS bins from 8.0-8.5 to 9.5-10.0 in log M* | 0.028, 0.024, 0.017, 0.030 | not stated | Jy km/s | 5 | The estimated $3\sigma$ upper limits with the 2D data are $0.028$, $0.024$, and $0.017$, $0.030 \, {\rm Jy\,km\,s^{-1}}$, from lower to higher stellar mass bins, respectively. |
| CO(2-1) line luminosity L', MS, 10 < log M* <= 11 (including direct detections) | 2.51 | 0.40 | 1e9 K km/s pc^2 | 6 | $<0.43$($<0.43$) & $<0.38$($<0.38$) & $2.51 \pm 0.40$($1.85 \pm 0.47$) & $10.57 \pm 0.97$ |
| CO(2-1) line luminosity L', MS, 11 < log M* <= 12 | 10.57 | 0.97 | 1e9 K km/s pc^2 | 6 | $<0.43$($<0.43$) & $<0.38$($<0.38$) & $2.51 \pm 0.40$($1.85 \pm 0.47$) & $10.57 \pm 0.97$ |
| Molecular gas mass, MS, 10 < log M* <= 11 and 11 < log M* <= 12 (alpha_CO = 3.6) | 11.87 and 50.07 | 1.95 and 5.00 | 1e9 Msun | 6 | $<6.11$($<6.11$) & $<3.62$($<3.62$) & $11.87 \pm 1.95$($8.74 \pm 2.26$) & $50.07 \pm 5.00$ |
| Molecular gas mass 3 sigma upper limits, MS, 8-9 (alpha_CO = 10.8) and 9-10 (alpha_CO = 7.2) in log M* | <6.11 and <3.62 | not stated | 1e9 Msun | 6 | $<6.11$($<6.11$) & $<3.62$($<3.62$) & $11.87 \pm 1.95$($8.74 \pm 2.26$) & $50.07 \pm 5.00$ |
| Gas-to-stellar mass ratio mu_gas at log M* ~ 10.5 and ~ 11.5 (MS) | 0.49 and 0.24 | 0.08 and 0.02 | dimensionless | 7 | we estimate $\mu_{\rm gas} =$ $0.49 \pm 0.08$ and $0.24 \pm 0.02$, respectively |
| mu_gas 3 sigma upper limit at log M* ~ 9.5 (MS) with alpha_CO = 7.2 (0.63 if alpha_CO = 3.6) | <1.25 | not stated | dimensionless | 7 | we constrain $\mu_{\rm gas}$ to have a $3\sigma$ upper limit of $<1.25$ with $\alpha_{\rm CO}=7.2 \, M_\odot \, ({\rm K\,km\,s^{-1}\,pc^2})^{-1}$ (or $< 0.63$ if |
| Gas depletion time, MS, 10 < log M* <= 11 and 11 < log M* <= 12 | 0.69 and 1.13 | 0.11 and 0.11 | Gyr | 7 | $<11.27$($<11.27$) & $<1.46$($<1.46$) & $0.69 \pm 0.11$($0.67 \pm 0.17$) & $1.13 \pm 0.11$ |
| Molecular gas density rho(H2) at z ~ 1.5 from CO(2-1) stacking | 0.49e8 | 0.09e8 | Msun Mpc^-3 | 7 | The estimated molecular gas density $\rho{\rm (H_2)}$ at $z\sim1.5$, based on our CO(2-1) stacking measurements, is $(0.49 \pm 0.09) \times 10^8 \,{\rm M_\odot\,Mpc^{-3}}$. |
| Fraction of MUSE-redshift-error bootstrap realizations with less than 3% flux loss (10000 realizations) | 92% | not stated | dimensionless | 5 | With 10000 realizations, we found that 92% of them resulted in less than 3% flux loss. |

## Qualitative findings

- Molecular gas mass of MS galaxies at z~1.5 increases with stellar mass from at least log M* ~ 9.0 to 12.0 (upper limits at the low-mass end); the low-mass upper limit is consistent with models  
  > "Taking upper limits into account, an increase of gas mass is found with increasing stellar mass from at least $\log{(M_*/M_\odot)} \sim 9.0$ to $12.0$." (5.2 Molecular gas and stellar mass scaling relation); "The upper limit at $\log{(M_*/M_\odot)} \sim 9.5$ derived from the stacking is consistent with the models." (5.2 Molecular gas and stellar mass scaling relation)
- mu_gas increases with SSFR, also for galaxies below the MS; depletion time decreases with SSFR  
  > "We find that $\mu_{\rm gas}$ increases with increasing SSFRs" (5.4.1 Gas-to-stellar mass ratios); "Both the stacked and directly detected sources show decreasing $t_{\rm depl}$ with increasing SSFR" (5.4.2 Gas depletion time)
- No higher-J CO emission recovered by stacking once direct detections (CO(3-2) IDs 35 and 1124) are excluded; two tentative CO(5-4) lines seen in individual spectra  
  > "There is also no stack detection for $J_{\rm up} \ge 4$ CO emission in our sample with the blind search" (4.2 Higher-J CO stacked spectra); "Deeper observations are needed to confirm these detections." (4.2 Higher-J CO stacked spectra)

## Claim tuples

- H: Stacking ASPECS Band 3 spectra at MUSE redshifts reveals CO(2-1) emission below the sensitivity of individual detections | E: Mean-stacked rest-frame spectra of 111 MUSE galaxies in bins of stellar mass and MS offset; 2D Gaussian flux fit | R: Stacked CO(2-1) detected for log M* > 10.0, including after removing blind-search detections (e.g. MS bin 10-11: 0.095 +/- 0.024 Jy km/s) | F: CO(2-1) emission is detected by stacking down to log M* = 10.0 | **supported**
- H: Molecular gas mass of z~1.5 MS galaxies continues to decrease with decreasing stellar mass below log M* = 10 | E: Stacks of 38 and 32 MS galaxies at log M* = 8-9 and 9-10 with 3 sigma upper limits and metallicity-based alpha_CO | R: No CO(2-1) detection in these bins; only upper limits on M_gas | F: Gas mass increases with stellar mass from at least log M* ~ 9.0 (constraints are upper limits and alpha_CO dependent) | **partially**
- H: The gas-to-stellar mass ratio of MS galaxies keeps declining with decreasing stellar mass below log M* ~ 10 | E: mu_gas from stacks with alpha_CO = 3.6/7.2/10.8, compared with PHIBSS2, local galaxies and models | R: mu_gas = 0.49 +/- 0.08 at log M* ~ 10.5 and < 1.25 at ~ 9.5 (alpha_CO = 7.2); constant mu_gas from 9.5 to 10.5 if alpha_CO = 3.6 | F: The decline of mu_gas is not as steep below log M* ~ 10, in line with models and lower-redshift studies; the downturn mass cannot be pinned down | **partially**
- H: MUSE-selected stacking recovers most of the CO emission at z~1.5 found with CO-selected ASPECS detections | E: Compute rho(H2) from stacked CO(2-1) measurements and compare with the CO luminosity function based value | R: rho(H2) = (0.49 +/- 0.09) x 10^8 Msun Mpc^-3, lower than but formally consistent with the CO-selected value | F: Most of the CO emission at z~1.5 is recovered through stacking | **supported**
- H: Higher-J CO (3-2 to 6-5) emission is recoverable by stacking MUSE-redshift galaxies | E: Same stacking for CO(3-2) to CO(6-5) with Lya redshift offset correction | R: No stacked detection once directly detected sources are excluded; only upper limits | F: No higher-J CO emission is recovered at z >~ 3 by stacking | **refuted**
- H: The known increase of mu_gas with SSFR also holds for galaxies below the main sequence | E: Stacked mu_gas versus SSFR for above/on/below-MS bins | R: mu_gas rises with SSFR across all three MS classes | F: The trend holds for galaxies below the MS at z ~ 1.5 | **supported**

## Reasoning

- Why this data: Band 3 line scan and MUSE redshifts overlap at z > 1, where ASPECS is most sensitive to CO(2-1)  
  > "In particular, over the range $1.0059 \leq z \leq 1.7387$, the ASPECS survey has the highest sensitivity for detecting CO(2-1) among all of the observable CO emission features (cite: Boog19)." (3.2 Sample selection)
- Why this method: Stacking at MUSE positions and redshifts maximizes sensitivity; Boogaard+18 MS relation chosen because it was calibrated on MUSE-detected sources and better constrains the low-mass end  
  > "Here, we maximize the sensitivity of the ASPECS data to detect CO emission by stacking ALMA spectra using the Band 3 data." (Introduction); "We here use the main-sequence relation from (cite: Boog18) because their $SFR-M_*$ correlation is assessed with the objects whose spectral features and redshifts were measured based on the MUSE data." (3.2 Sample selection)
- Alternative: Median stacking gave similar results; mean stacking adopted for simpler noise estimates and for stacks with only two spectra  
  > "The median stacking also produced similar results, but here we adopt the mean stacking for simpler noise estimates and for a better treatment when there are only two samples to stack." (Footnote 2)
- Alternative: Earlier MS relations (Whitaker+14, Schreiber+15) not used because they are based on mostly massive galaxies; Speagle+14 relation tested in an appendix  
  > "Compared with earlier studies such as (cite: Whit14) and (cite: Schr15) whose samples are mostly massive galaxies, (cite: Boog18) better constrained the low-mass end of the relation." (3.2 Sample selection)
- How they decided it was enough: Finer 0.5 dex low-mass bins tried in case emission was diluted; flux-loss from redshift errors judged negligible so no correction applied  
  > "we adopt a $\Delta \log{(M_*/M_\odot)}=0.5$ stellar mass bin size in case some hidden emission from a small number of sources has been diluted by averaging too many sources without any emission." (4.1.2 Stacking in stellar mass and SSFR bins); "We do not scale up our measured fluxes in this work to take account of this flux loss, because its impact on our line flux measurements is not significant." (3.3 CO line flux and upper limit measurements)
- Limitation (authors): Data limitations plus unknown alpha_CO dependence prevent locating the mu_gas downturn mass  
  > "Given the limitations of our data, and the unknown dependence of the $\alpha_{\rm CO}$ conversion factor, we cannot determine at which stellar mass a possible downturn of the gas-to-stellar mass ratio occurs." (5.3 Molecular gas-to-stellar mass ratio)
- Limitation (authors): A factor of 10 larger sample is needed to confirm or rule out model predictions at low mass  
  > "This result also implies that at least a factor of 10 increase in the sample size is needed to confirm or rule out the model predictions." (5.2 Molecular gas and stellar mass scaling relation)
- Limitation (authors): High-J non-detections may reflect dilution from Lya velocity-offset uncertainty or lower gas content of Lya emitters  
  > "This is likely either due to dilution of the stacked signal, owing to uncertainties in the velocity offset, or to Ly$\alpha$ emitters on average having smaller SFRs and molecular gas content." (4.2 Higher-J CO stacked spectra)
- Caveat (inferred, ours): Low-mass gas masses depend directly on the assumed alpha_CO (7.2 and 10.8 are assumed from metallicity guesses, not measured), so the 'plateau' in mu_gas flips with the alpha_CO choice
- Caveat (inferred, ours): Mean stack mixes sources with different noise and beam response; no weighting is applied, and 2D Gaussian fits with fixed beam widths may miss extended or offset emission
- Caveat (inferred, ours): Stellar mass and SFR (hence MS classification) come from SED fits whose inputs are not reproduced here
- Caveat (inferred, ours): rho(H2) method and uncertainty propagation are not described
- Caveat (inferred, ours): Upper limits in bins with 1-4 sources are poorly informative; the stacked detection claims in sparse bins rest on few objects

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Per-source table of the 111 stacked galaxies (positions, z, M*, SFR, MS class)
- Missing: Stacking and filtering code or an explicit CASA/Python recipe
- Missing: ASPECS cube and primary-beam product versions used
- Missing: MAGPHYS setup and SED results
- Missing: rho(H2) derivation details and error propagation
- Data volume (inferred): ASPECS Band 3 line-scan: raw ALMA data likely several hundred GB; calibrated cubes/products probably a few to tens of GB (inferred)
- Score (inferred): 3/5, Stacking, filtering, fitting and conversion steps are described in good numeric detail with a results table, but the sample catalog, cube products, SED fit outputs and code are not given in the paper.
- Rediscovery candidate: no, Per-source M*, SFR, MS classes and the exact ASPECS/MUSE inputs are not provided in the paper, and the paper does not state data availability, so the recipe is not complete enough to redo from the text alone.

## Links

- Method: (cite: Walt16) (ASPECS survey design and Pilot data)
- Method: (cite: Gonz19) (ASPECS Large Program data reduction, cube and blind line search)
- Method: (cite: Baco17) (MUSE-HUDF survey and data treatment)
- Method: (cite: Inam17) (MUSE-HUDF redshift determination and catalogs)
- Method: (cite: Boog19) (SED fitting procedure and MUSE-based ASPECS CO analysis)
- Method: (cite: Boog18) (Main-sequence relation (Eq. 11) used for classification)
- Method: (cite: Deca16b) (Gas mass equation and conditions)
- Companion: (cite: Arav19) (Gas properties of directly detected ASPECS CO sources)
- Companion: (cite: Deca19) (CO luminosity functions and cosmic gas density from ASPECS)
- Companion: (cite: Popp19) (Model predictions compared with ASPECS)
- Companion: (cite: Uzgi19) (CO power spectrum analysis of ASPECS using MUSE positions)
- Companion: (cite: Boog20) (r21 estimate from ASPECS galaxies)
- Related: ASPECS Pilot and Large Program (ALMA Spectroscopic Survey in the HUDF)
- Related: MUSE-HUDF deep and ultra-deep survey
- Related: PHIBSS2
- Related: xCOLD GASS
- Related: UVUDF

## Checks

```json
{
 "quotes": 147,
 "quotes_ok": 147,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2016.1.00324.L"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 16,
 "numeric_problems": 0,
 "fill": {
  "facts": 122,
  "stated": 88,
  "rate": 0.721
 },
 "evidence_ok": true
}
```

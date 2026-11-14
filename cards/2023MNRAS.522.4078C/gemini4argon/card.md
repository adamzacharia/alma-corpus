# WISDOM Project - XV. Giant molecular clouds in the central region of the barred spiral galaxy NGC 5806

`2023MNRAS.522.4078C` | Monthly Notices of the Royal Astronomical Society 2023 | first author: Choi, Woorak | arXiv: 2304.10471 | DOI: 10.1093/mnras/stad1211

Card schema 1.0 | model gemini-4-argon | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation
- Question: What are the physical properties, dynamics, scaling relations, and lifetimes of individual giant molecular clouds in the central region of the barred spiral galaxy NGC 5806, and how are they influenced by the bar?  
  > "As part of the mm-Wave Interferometric Survey of Dark Object Masses (WISDOM) project, we analyse here the properties and dynamics of individual GMCs in the centre of the barred spiral galaxy NGC 5806 (SAB(s)) located in the field." (Introduction); "We study cloud properties and scaling relations in different regions, and investigate how they could be influenced by the bar." (Conclusions)
- Target **NGC 5806**: coordinates R.A. = 15h00m00.5s, Dec. = 1d53m30s (J2000)  
  > "NGC 5806 is a nearby barred spiral galaxy (SAB(s)b) located at ${\rm R.A.}=15^{\rm h} 00^{\rm m}00.5s$, ${\rm Dec.}=1\ensuremath{^\circ}53\ensuremath{'}30\ensuremath{''}$ (J2000)." (Target); "Throughout this paper, we adopt a distance $D=21.4$ Mpc for NGC 5806 (cite: cappellari2011), whereby $1\ensuremath{''}$ corresponds to $\approx103$ pc." (Target); z/distance D = 21.4 Mpc  
  > "NGC 5806 is a nearby barred spiral galaxy (SAB(s)b) located at ${\rm R.A.}=15^{\rm h} 00^{\rm m}00.5s$, ${\rm Dec.}=1\ensuremath{^\circ}53\ensuremath{'}30\ensuremath{''}$ (J2000)." (Target); "Throughout this paper, we adopt a distance $D=21.4$ Mpc for NGC 5806 (cite: cappellari2011), whereby $1\ensuremath{''}$ corresponds to $\approx103$ pc." (Target); distance from (cite: cappellari2011)  
  > "NGC 5806 is a nearby barred spiral galaxy (SAB(s)b) located at ${\rm R.A.}=15^{\rm h} 00^{\rm m}00.5s$, ${\rm Dec.}=1\ensuremath{^\circ}53\ensuremath{'}30\ensuremath{''}$ (J2000)." (Target); "Throughout this paper, we adopt a distance $D=21.4$ Mpc for NGC 5806 (cite: cappellari2011), whereby $1\ensuremath{''}$ corresponds to $\approx103$ pc." (Target)

## Data provenance

- ALMA projects: 2016.1.00437.S, 2016.2.00053.S
- bands: _not stated_
- frequencies and spectral setup: 12-m: 1 SPW of 1.875 GHz (3840 channels of 488 kHz / 0.6 km/s) for 12CO(2-1) at 230.586 GHz and 3 SPWs of 2 GHz for continuum; ACA: 1 SPW of 2 GHz (2048 channels of 977 kHz / 1.3 km/s) for line and 3 SPWs of 2 GHz for continuum  
  > "The correlator was set up with one spectral window of $1.875$ GHz bandwidth ($\approx2400$ km s$^{-1}$) and $3840$ channels each of $488$ kHz ($\approx0.6$ km s$^{-1}$) used for $^{12}$CO(2-1) line observations" (Data); "The correlator was set up with one spectral window of $2$ GHz bandwidth ($\approx2600$ km s$^{-1}$) and $2048$ channels each of $977$ kHz ($\approx1.3$ km s$^{-1}$) used for $^{12}$CO(2-1) line observations" (Data)
- continuum bandwidth: Three 2 GHz SPWs; ~6.3 GHz total line-free bandwidth  
  > "and the three remaining spectral windows of $2$ GHz bandwidth used solely for continuum observations." (Data); "Averaging over the entire line-free bandwidth ($\approx6.3$ GHz), the resulting RMS noise is $25$ $\mu$Jy beam$^{-1}$ at a central frequency of 238.351 GHz." (Data reduction)
- arrays: 12-m array (44 and 41 antennae) and 7-m ACA (10 antennae)  
  > "The observations were carried out using two different $12$-m array configurations in October and December 2016 (programme 2016.1.00437.S, configurations C40-3 and C40-6, PI Davis) and the $7$-m Atacama Compact Array (ACA) in July 2017 (programme 2016.2.00053.S, PI Liu)" (Data)
- configurations: C40-3, C40-6, ACA  
  > "The observations were carried out using two different $12$-m array configurations in October and December 2016 (programme 2016.1.00437.S, configurations C40-3 and C40-6, PI Davis) and the $7$-m Atacama Compact Array (ACA) in July 2017" (Data)
- baselines: 15-600 m (C40-3), 15-1800 m (C40-6), 8-43 m (ACA)  
  > "The C40-3 configuration observations had $242$ s on-source using $44$ antennae and baselines of $15$ – $600$ m, leading to a maximum recoverable scale of $6.0\ensuremath{''}$." (Data); "The C40-6 configuration observations had $272$ s on-source using $41$ antennae and baselines of $15$ – $1800$ m, leading to a maximum recoverable scale of $1.3\ensuremath{''}$." (Data); "The ACA observations had $1088$ s on-source using $10$ antennae and baselines of $8$ – $43$ m, leading to a maximum recoverable scale of $29.0\ensuremath{''}$." (Data)
- angular resolution: 0.25'' x 0.22'' (25.7 x 22.6 pc^2) for line; 0.20'' x 0.18'' for continuum  
  > "Finally, we achieved a synthesised beam of $0.25\ensuremath{''}\times0.22\ensuremath{''}$ ($25.7\times22.6$ pc$^2$) at a position angle of $48\ensuremath{^\circ}$." (Data reduction); "resulting in a synthesised beam of $0.20\ensuremath{''}\times0.18\ensuremath{''}$." (Data reduction)
- max recoverable scale: 6.0'' (C40-3), 1.3'' (C40-6), 29.0'' (ACA)  
  > "The C40-3 configuration observations had $242$ s on-source using $44$ antennae and baselines of $15$ – $600$ m, leading to a maximum recoverable scale of $6.0\ensuremath{''}$." (Data); "The C40-6 configuration observations had $272$ s on-source using $41$ antennae and baselines of $15$ – $1800$ m, leading to a maximum recoverable scale of $1.3\ensuremath{''}$." (Data); "The ACA observations had $1088$ s on-source using $10$ antennae and baselines of $8$ – $43$ m, leading to a maximum recoverable scale of $29.0\ensuremath{''}$." (Data)
- sensitivity: 0.86 mJy beam^-1 (0.85 K) per 2 km s^-1 channel (cube); 25 uJy beam^-1 (continuum)  
  > "The RMS noise of this cube is $\sigma_{\mathrm{rms}}=0.86$ mJy beam$^{-1}$ ($0.85$ K) per channel." (Data reduction); "Averaging over the entire line-free bandwidth ($\approx6.3$ GHz), the resulting RMS noise is $25$ $\mu$Jy beam$^{-1}$ at a central frequency of 238.351 GHz." (Data reduction)
- time on source: 242 s (C40-3), 272 s (C40-6), 1088 s (ACA)  
  > "The C40-3 configuration observations had $242$ s on-source using $44$ antennae and baselines of $15$ – $600$ m" (Data); "The C40-6 configuration observations had $272$ s on-source using $41$ antennae and baselines of $15$ – $1800$ m" (Data); "The ACA observations had $1088$ s on-source using $10$ antennae and baselines of $8$ – $43$ m" (Data)
- observing dates: October and December 2016 (12-m), July 2017 (ACA)  
  > "The observations were carried out using two different $12$-m array configurations in October and December 2016 (programme 2016.1.00437.S, configurations C40-3 and C40-6, PI Davis) and the $7$-m Atacama Compact Array (ACA) in July 2017" (Data)
- pi or archival as stated: PI Davis (2016.1.00437.S), PI Liu (2016.2.00053.S)  
  > "The observations were carried out using two different $12$-m array configurations in October and December 2016 (programme 2016.1.00437.S, configurations C40-3 and C40-6, PI Davis) and the $7$-m Atacama Compact Array (ACA) in July 2017 (programme 2016.2.00053.S, PI Liu)" (Data)
- Line: 12CO J=2-1 (230.586 GHz)
- Other facility **Sloan Digital Sky Survey (SDSS)**: Three-colour optical image of NGC 5806  
  > "[1](#fig:optical_image) shows the Sloan Digital Sky Survey (SDSS) three-colour image of NGC 5806 (left)" (Target)
- Other facility **Hubble Space Telescope (HST) / WFPC3**: F555W optical image of NGC 5806  
  > "a *Hubble Space Telescope*’s (*HST*) Wide-Field and Planetary Camera 3 (WFPC3) *F555W* image (top-right)" (Target)
- External data: Distance D = 21.4 Mpc  
  > "Throughout this paper, we adopt a distance $D=21.4$ Mpc for NGC 5806 (cite: cappellari2011), whereby $1\ensuremath{''}$ corresponds to $\approx103$ pc." (Target) [from (cite: cappellari2011)]
- External data: Total stellar mass of 3.89 x 10^10 M_sun  
  > "NGC 5806 has a total stellar mass of $3.89\times10^{10}$ M$_{\odot}$ (cite: salo2017; morales2018)" (Target) [from (cite: salo2017; morales2018)]
- External data: Luminosity-weighted stellar velocity dispersion sigma_* = 120 km s^-1 within central 10'' and SMBH mass ~1.2 x 10^7 M_sun  
  > "a luminosity-weighted stellar velocity dispersion $\sigma_*=120$ km s$^{-1}$ within the central $10\ensuremath{''}$ (cite: dumas2007)" (Target); "(cite: dumas2007) estimated the mass of the central supermassive black hole to be $\approx1.2\times10^7$ M$_{\odot}$ using the $M_{\mathrm{BH}}$ – $\sigma_\star$ relation of (cite: tremaine2002)." (Target) [from (cite: dumas2007)]
- External data: Molecular gas mass at central 27.4'' of ~10^9 M_sun  
  > "The mass of molecular gas at the centre region of NGC 5806 ($27.4\ensuremath{''}$) is $\approx10^9$ M$_{\odot}$ (cite: davis2022_wisdom)" (Target) [from (cite: davis2022_wisdom)]
- External data: Total atomic hydrogen (HI) mass of 1.74 x 10^9 M_sun  
  > "and the total mass of atomic hydrogen (H I) is $1.74\times10^9$ M$_{\odot}$ (cite: haynes2018ALFALFA)." (Target) [from (cite: haynes2018ALFALFA)]
- External data: Total star formation rate of 3.6 M_sun yr^-1  
  > "Star formation is present only in the inner and nuclear rings, with a total star formation rate (SFR) of $3.6$ M$_{\odot}$ yr$^{-1}$ derived using a spectral energy distribution fitting code (cite: errozferrer2019)." (Target) [from (cite: errozferrer2019)]
- External data: Systemic velocity V_sys = 1360 km s^-1 from HI line emission  
  > "with respect to the systemic velocity $V_{\mathrm{sys}}=1360$ km s$^{-1}$(as determined from H i line emission; (cite: springob2005_vsys_ref))." (Moment maps) [from (cite: springob2005_vsys_ref)]

## Processing

### Calibration

- pipeline or manual: Standard ALMA pipeline provided by ALMA regional centre staff  
  > "The raw data of each configuration were calibrated using the standard ALMA pipeline provided by ALMA regional centre staff, using COMMON ASTRONOMY SOFTWARE APPLICATIONS (CASA; (cite: mcmullin2007_casa)) version 4.7.0." (Data reduction)
- casa version: 4.7.0 (pipeline calibration), 5.6.1 (combination and imaging)  
  > "The raw data of each configuration were calibrated using the standard ALMA pipeline provided by ALMA regional centre staff, using COMMON ASTRONOMY SOFTWARE APPLICATIONS (CASA; (cite: mcmullin2007_casa)) version 4.7.0." (Data reduction); "Using CASA version 5.6.1, we then combined the ACA data using the CASA task `concat` with default weighting." (Data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean (interactive)  
  > "We then cleaned the data using the `tclean` task interactively, to a depth equal to the root-mean-square (RMS) noise of the dirty cube" (Data reduction)
- deconvolver: _not stated_
- weighting robust: Briggs weighting with robust = 0.5  
  > "and imaged the cleaned components using Briggs weighting with a robust parameter of $0.5$." (Data reduction)
- uv taper: _not stated_
- cell size: 0.05''  
  > "Pixels of $0.05\ensuremath{''}$ were chosen as a compromise between spatial sampling and image size, resulting in approximately $5\times4.5$ pixels across the synthesised beam." (Data reduction)
- image size: Encompassing most of the primary beam spatially  
  > "We thus created a fully calibrated and cleaned cube encompassing most of the primary beam spatially, with $2$ km s$^{-1}$ (binned) channels spectrally." (Data reduction)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: CASA task uvcontsub  
  > "Although continuum emission is not detected (see below), we subtracted any continuum that may be present using the CASA task `uvcontsub`." (Data reduction)
- line free channels: ~6.3 GHz total line-free bandwidth  
  > "Averaging over the entire line-free bandwidth ($\approx6.3$ GHz), the resulting RMS noise is $25$ $\mu$Jy beam$^{-1}$ at a central frequency of 238.351 GHz." (Data reduction)
- primary beam correction: _not stated_
- array combination: Manual weighting of 0.2 to C40-3 and 1.0 to C40-6, then combined with ACA using CASA task concat with default weighting  
  > "we manually applied a low weighting ($0.2$) to the shorter baseline $12$-m data (C40-3) and a higher weighting ($1.0$) to the longer baseline $12$-m data (C40-6)." (Data reduction); "Using CASA version 5.6.1, we then combined the ACA data using the CASA task `concat` with default weighting." (Data reduction)
- smoothing: 2 km s^-1 binned channels spectrally  
  > "We thus created a fully calibrated and cleaned cube encompassing most of the primary beam spatially, with $2$ km s$^{-1}$ (binned) channels spectrally." (Data reduction)
- final beam: 0.25'' x 0.22'' (25.7 x 22.6 pc^2), PA = 48 deg (cube); 0.20'' x 0.18'' (continuum)  
  > "Finally, we achieved a synthesised beam of $0.25\ensuremath{''}\times0.22\ensuremath{''}$ ($25.7\times22.6$ pc$^2$) at a position angle of $48\ensuremath{^\circ}$." (Data reduction); "To establish an uuper limit, we created a continuum image using the `tclean` task in CASA and Briggs weighting with a robust parameter of $0.5$, resulting in a synthesised beam of $0.20\ensuremath{''}\times0.18\ensuremath{''}$." (Data reduction)
- final rms: 0.86 mJy beam^-1 (0.85 K) per 2 km s^-1 channel (cube); 25 uJy beam^-1 (continuum)  
  > "The RMS noise of this cube is $\sigma_{\mathrm{rms}}=0.86$ mJy beam$^{-1}$ ($0.85$ K) per channel." (Data reduction); "Averaging over the entire line-free bandwidth ($\approx6.3$ GHz), the resulting RMS noise is $25$ $\mu$Jy beam$^{-1}$ at a central frequency of 238.351 GHz." (Data reduction)

### Inherited from earlier work

- Smooth-moment masking method for generating moment maps  
  > "To generate these maps, we utilised a smooth-moment masking method (cite: dame2011)." (Moment maps) [from (cite: dame2011)]
- Modified CPROPSTOO algorithm, gradient-subtracted velocity dispersion, convexity parameter, bootstrapping uncertainty estimation, and shear timescale definition  
  > "We utilise our own modified version of the algorithms of CPROPSTOO (cite: liu2021ngc4429), that is an updated version of CPROPS (cite: Rosolowsky2006cprops; Leroy2015cpropstoo), to identify the clouds in NGC 5806." (Cloud identification); "The uncertainties of all cloud properties are estimated via a bootstrapping technique as in (cite: liu2021ngc4429), with $500$ samples." (GMC properties); "We derive the shear timescale $t_{\mathrm{shear}}=1/2A$ (cite: liu2021ngc4429)" (GMC lifetime in the nuclear ring) [from (cite: liu2021ngc4429)]
- Standard CPROPSTOO/CPROPS cloud property definitions  
  > "Following the standard CPROPSTOO/CPROPS definitions (cite: Rosolowsky2006cprops), we calculate the physical properties of the clouds identified." (GMC properties) [from (cite: Rosolowsky2006cprops)]
- Cloud size geometric parameter eta = 1.91  
  > "and we adopt $\eta=1.91$ for consistency with earlier studies (cite: solomon1987; utomo2015; liu2021ngc4429)." (GMC properties) [from (cite: solomon1987; utomo2015; liu2021ngc4429)]
- Error in variable method for fitting cumulative mass functions  
  > "To fit each cumulative mass function, we apply the "error in variable" method of (cite: rosolowsky2005), and the fitting parameters and the uncertainties are estimated via bootstrapping." (GMC cumulative mass functions) [from (cite: rosolowsky2005)]
- Mass completeness limit definition M_comp = M_min + 10 delta_M  
  > "We calculate the mass completeness limit using the minimum mass ($M_{\mathrm{min}}$) of resolved cloud and the observational sensitivity, i.e. $M_{\mathrm{comp}}\equiv M_{\mathrm{min}}+10\delta_{\mathrm{M}}$ (cite: colombo2014m51; liu2021ngc4429)" (GMC cumulative mass functions) [from (cite: colombo2014m51; liu2021ngc4429)]
- Method to estimate cloud lifetimes in the nuclear ring from number statistics and rotating bar pattern travel time  
  > "We note that our method to estimate cloud lifetimes in the nuclear ring of a barred galaxy is similar to that introduced by (cite: meidt2015) to estimate cloud lifetimes in the inter-arm region of a spiral galaxy." (GMC lifetime in the nuclear ring); "Nevertheless, we measure travel time $t_{\rm travel}$ with respect to the rotating bar pattern as inspired by the work of (cite: koda2021)." (GMC lifetime in the nuclear ring) [from (cite: meidt2015); (cite: koda2021)]

### Not stated but needed to reproduce (our reading)

- Exact frequency ranges or channel ranges used for uvcontsub continuum subtraction
- Exact pixel size in pixels (e.g., imsize) and deconvolver setting used in CASA tclean
- Exact spatial polygon coordinates defining the four galactic subregions (nucleus, arcs, nodes, dust lanes)
- Smoothing kernel size used to generate the low-resolution coarse-grained 12CO(2-1) velocity map for omega_model
- Details of how the rotation curve V_c(R_gal) was derived (mentioned as 'rotation curve that derived above' without an explicit derivation section in the text)

## Analysis recipe

1. **Calibrate, combine, and image the ALMA 12CO(2-1) cube and continuum**: Calibrate raw data with ALMA pipeline; manually weight C40-3 (0.2) and C40-6 (1.0), combine with ACA using concat; subtract continuum with uvcontsub; interactively clean with tclean to dirty cube RMS depth.  
  > "we manually applied a low weighting ($0.2$) to the shorter baseline $12$-m data (C40-3) and a higher weighting ($1.0$) to the longer baseline $12$-m data (C40-6)." (Data reduction); "Using CASA version 5.6.1, we then combined the ACA data using the CASA task `concat` with default weighting." (Data reduction); "We then cleaned the data using the `tclean` task interactively, to a depth equal to the root-mean-square (RMS) noise of the dirty cube, and imaged the cleaned components using Briggs weighting with a robust parameter of $0.5$." (Data reduction)
   - software: CASA
   - parameter: Briggs robust = 0.5, pixel size = 0.05'', channel width = 2 km s^-1, C40-3 weight = 0.2, C40-6 weight = 1.0  
  > "and imaged the cleaned components using Briggs weighting with a robust parameter of $0.5$." (Data reduction); "Pixels of $0.05\ensuremath{''}$ were chosen as a compromise between spatial sampling and image size" (Data reduction); "We thus created a fully calibrated and cleaned cube encompassing most of the primary beam spatially, with $2$ km s$^{-1}$ (binned) channels spectrally." (Data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Generate moment maps and define galactic regions**: Smooth-moment masking method: convolve cube spatially with a Gaussian equal to synthesised beam width, Hanning-smooth spectrally, mask at 1.5x RMS of smoothed cube, apply to original cube; divide galaxy into four regions (nucleus, arcs, nodes, dust lanes).  
  > "In brief, we convolved the data cube spatially with a Gaussian of width equal to that of the synthesised beam and Hanning-smoothed the cube spectrally." (Moment maps); "We then only selected pixels with an intensity above $1.5$ times the RMS of the smoothed cube to create a mask, and applied this mask to the original data cube to create the moment maps." (Moment maps); "Based on the moment maps, we divide the galaxy into four distinct regions labelled as follows (see [3](#fig:cloudfinding_result)): nucleus (blue), arcs (green), nodes (red) and dust lanes (yellow)." (Region definition)
   - parameter: Mask threshold = 1.5 x RMS of smoothed cube; nucleus = inner 250 pc  
  > "We then only selected pixels with an intensity above $1.5$ times the RMS of the smoothed cube to create a mask" (Moment maps); "The nucleus indicates the inner $250$ pc region" (Region definition)
   - assumption: Systemic velocity V_sys = 1360 km s^-1  
  > "with respect to the systemic velocity $V_{\mathrm{sys}}=1360$ km s$^{-1}$(as determined from H i line emission; (cite: springob2005_vsys_ref))." (Moment maps)
   - fitting: _not stated_
   - validation: _not stated_
3. **Identify giant molecular clouds (GMCs)**: Use modified CPROPSTOO algorithm: generate 3D mask of islands (2 adjacent channels > 2.5 sigma_rms expanded to > 1.5 sigma_rms, area >= 2 beams), find local maxima in running 3x3x3 pix^3 sub-cubes, decompose into clouds across a stepped range of minarea and minpix.  
  > "The mask initially includes only pixels for which two adjacent channels are above $2.5$ $\sigma_\mathrm{rms}$. The mask is then expanded to include all neighbouring pixels for which two adjacent channels are above $1.5$ $\sigma_\mathrm{rms}$." (Cloud identification); "Local maxima (i.e. cloud candidates) are identified within running $3\times3\times3$ pix$^3$ subsets of the cube (i.e. $0.15\ensuremath{''}\times0.15\ensuremath{''}\times6$ km s$^{-1}$ sub-cubes)." (Cloud identification); "The code searches for clouds from the largest $minarea$ ($96$ spaxels) and $minpix$ ($96$ pixels) to the smallest $minarea$ ($24$ spaxels) and $minpix$ ($24$ pixels) with a step size of $24$ spaxels (or pixels)." (Cloud identification)
   - software: CPROPSTOO
   - parameter: minvchan = 2, Delta T_max = 2 sigma_rms = 1.7 K, minarea = 96 to 24 spaxels (step 24), minpix = 96 to 24 pixels (step 24), convexity = 0.5  
  > "We then run CPROPSTOO, setting the minimum of number channels spanned by each cloud ($minvchan=2$) and the minimum contrast between a cloud’s peak and its boundary ($\Delta T_{\mathrm{max}}=2\sigma_{\mathrm{rms}}=1.7$ K)." (Cloud identification); "The code searches for clouds from the largest $minarea$ ($96$ spaxels) and $minpix$ ($96$ pixels) to the smallest $minarea$ ($24$ spaxels) and $minpix$ ($24$ pixels) with a step size of $24$ spaxels (or pixels)." (Cloud identification); "In this work, we set $convexity=0.5$, by testing a range of $0.4$ – $0.8$." (Cloud identification)
   - fitting: _not stated_
   - validation: Apply the same island identification criteria to the inverted data cube; test convexity over a range of 0.4 - 0.8.  
  > "We also apply the same criteria to the inverted data cube to verify the reliability of our island identification." (Cloud identification); "In this work, we set $convexity=0.5$, by testing a range of $0.4$ – $0.8$." (Cloud identification)
4. **Calculate physical properties of identified GMCs and fit their distributions**: Compute cloud size R_c, observed velocity dispersion sigma_obs,los, gradient-subtracted velocity dispersion sigma_gs,los, CO(2-1) luminosity, gas mass M_gas, and surface density Sigma_gas; fit Gaussian curves to property distributions and estimate uncertainties with 500 bootstrap samples.  
  > "Following the standard CPROPSTOO/CPROPS definitions (cite: Rosolowsky2006cprops), we calculate the physical properties of the clouds identified." (GMC properties); "The uncertainties of all cloud properties are estimated via a bootstrapping technique as in (cite: liu2021ngc4429), with $500$ samples." (GMC properties); "In each panel, the black histogram (data) and curve (Gaussian fit) show the full sample, while the blue, green, red and yellow colours show those of the clouds in the nucleus, arcs, nodes and dust lanes only, respectively." (GMC properties in different regions)
   - software: CPROPSTOO
   - parameter: Bootstrap samples = 500, T_edge = 0 K extrapolation  
  > "Finally, we calculate the second moment of the shifted emission summed over the whole cloud, and extrapolate it to $T_{\mathrm{edge}}=0$ K." (GMC properties); "The uncertainties of all cloud properties are estimated via a bootstrapping technique as in (cite: liu2021ngc4429), with $500$ samples." (GMC properties)
   - assumption: Distance D = 21.4 Mpc, geometric parameter eta = 1.91, line ratio R_21 = 1, X_CO = 2 x 10^20 cm^-2 (K km s^-1)^-1 (alpha_CO(2-1) = 4.4 M_sun (K km s^-1 pc^2)^-1), inclination i = 58 deg, PA = 166 deg  
  > "Throughout this paper, we adopt a distance $D=21.4$ Mpc for NGC 5806 (cite: cappellari2011), whereby $1\ensuremath{''}$ corresponds to $\approx103$ pc." (Target); "and we adopt $\eta=1.91$ for consistency with earlier studies (cite: solomon1987; utomo2015; liu2021ngc4429)." (GMC properties); "To convert the CO luminosity to a molecular gas mass, we adopt a $^{12}$CO(2-1)/$^{12}$CO(1-0) ratio $R_{21}=1$ in temperature units, within the range typically found in the central regions of (barred) spiral galaxies ($0.8$ – $1.2$; e.g. (cite: Crosthawaite2002_lineratio)), and a CO-to-H2 conversion factor $X_{\mathrm{CO}}=2\times10^{20}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$ equivalent to a $^{12}$CO(2-1) conversion factor $\alpha_{\mathrm{CO(2-1)}}\approx4.4$ M$_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$." (GMC properties)
   - fitting: Gaussian fits to distributions; bootstrapping with 500 samples for property uncertainties.  
  > "The uncertainties of all cloud properties are estimated via a bootstrapping technique as in (cite: liu2021ngc4429), with $500$ samples." (GMC properties)
   - validation: _not stated_
5. **Fit GMC cumulative mass functions**: Fit cumulative gas mass distributions above the mass completeness limit with power-law and truncated power-law functions using the 'error in variable' method and bootstrapping.  
  > "The cumulative mass functions are fit with both a power-law function" (GMC cumulative mass functions); "To fit each cumulative mass function, we apply the "error in variable" method of (cite: rosolowsky2005), and the fitting parameters and the uncertainties are estimated via bootstrapping." (GMC cumulative mass functions); "Fittings are only performed above the mass completeness limit of $M_{\mathrm{comp}}=2.4\times10^5$ M$_{\odot}$." (GMC cumulative mass functions)
   - parameter: M_comp = 2.4 x 10^5 M_sun, delta_M = 1.03 x 10^4 M_sun, RMS surface density sensitivity = 17.8 M_sun pc^-2, beam area = 565 pc^2; 5 most massive clouds excluded in nucleus and nodes regional fits  
  > "Fittings are only performed above the mass completeness limit of $M_{\mathrm{comp}}=2.4\times10^5$ M$_{\odot}$." (GMC cumulative mass functions); "where the the contribution to the mass due to noise $\delta_{\mathrm{M}}\approx1.03\times10^4$ M$_{\odot}$ is estimated by multiplying our RMS gas mass surface density sensitivity of $17.8$ M$_{\odot}$ pc$^{-2}$ by the synthesised beam area of $\approx565$ pc$^2$." (GMC cumulative mass functions); "We note that to avoid a failure of some of the fits, the five most massive clouds from each of the nucleus and the nodes were excluded from the fit (although the nucleus truncated power-law fit still fails)." (GMC cumulative mass functions)
   - fitting: Error in variable method of (cite: rosolowsky2005) with bootstrapping for parameter and uncertainty estimation.  
  > "To fit each cumulative mass function, we apply the "error in variable" method of (cite: rosolowsky2005), and the fitting parameters and the uncertainties are estimated via bootstrapping." (GMC cumulative mass functions)
   - validation: _not stated_
6. **Measure internal velocity gradients of individual clouds and compare with galaxy rotation and turbulence**: Fit a 2D plane v_bar(x,y) = ax + by + c to the intensity-weighted first moment map of each resolved cloud using MPFIT2DFUN to derive projected angular velocity omega_obs and rotation axis PA phi_rot; compare with low-resolution galaxy velocity map model (omega_model, phi_model), Burkert & Bodenheimer (2000) turbulence relation, and sigma_gs,los.  
  > "As previous studies, we thus quantify the observed velocity gradient by fitting a plane to the intensity-weighted first moment map of each cloud." (Velocity Gradients of Individual Clouds); "where $a$ and $b$ are the projected velocity gradient along the $x$- and the $y$-axis on the sky, respectively, and $c$ is a zero point, that we determine using the Interactive Data Language code MPFIT2DFUN (cite: mpfit2dfun_ref)." (Velocity Gradients of Individual Clouds); "we compare in [7](#fig:omega_model_comparison) the measured angular velocities ($\omega_{\mathrm{obs}}$) and rotation axes ($\phi_{\mathrm{rot}}$) of the clouds with those expected ($\omega_{\mathrm{model}}$ and $\phi_{\mathrm{model}}$), as calculated from a low-resolution (i.e. coarse-grained) $^{12}$CO(2-1) velocity map over the same position and area as each resolved cloud" (Origin of velocity gradients)
   - software: IDL, MPFIT2DFUN
   - assumption: Solid-body rotation plane approximation; turbulence relation omega = 1.6 (R_c / 0.1 pc)^(-1/2) km s^-1 pc^-1  
  > "Because clouds in external galaxies are usually poorly spatially resolved, solid-body rotation provides an adequate description of the observations." (Velocity Gradients of Individual Clouds); "They claimed a relation of the form $\left(\frac{\omega}{\mathrm{km~s^{-1}~pc^{-1}}}\right)=1.6\left(\frac{R_\mathrm{c}}{\mathrm{0.1~pc}}\right)^{-1/2}$." (Origin of velocity gradients)
   - fitting: 2D plane fitting via IDL MPFIT2DFUN; standard error propagation for uncertainties of omega_obs and phi_rot.  
  > "and the uncertainties of $\omega_{\mathrm{obs}}$ and $\phi_{\mathrm{rot}}$ are estimated from the uncertainties of the parameters $a$ and $b$ using standard error propagation rules." (Velocity Gradients of Individual Clouds)
   - validation: Compare observed velocity dispersions sigma_obs,los with gradient-subtracted velocity dispersions sigma_gs,los.  
  > "Another way to assess whether bulk motions due to galaxy rotation contribute significantly to the observed velocity dispersions and velocity gradients of the NGC 5806 clouds is to compare the observed velocity dispersions ($\sigma_{\mathrm{obs,los}}$) with the gradient-subtracted velocity dispersions ($\sigma_{\mathrm{gs,los}}$)" (Origin of velocity gradients)
7. **Assess dynamical states, scaling relations, virial parameter, and X_CO variations**: Fit power laws to size-linewidth (R_c vs sigma_obs,los), virial mass vs gas mass (M_obs,vir vs M_gas), and virial parameter vs velocity dispersion; analyze Sigma_gas vs sigma_obs,los R_c^(-1/2) pressure curves; infer X_CO distribution assuming virial equilibrium.  
  > "The left panel of [2](#fig:larson_obs) shows the size – linewidth relation of all resolved clouds of NGC 5806, with the best-fitting power-law relation overlaid (black solid line)" (Dynamical states of clouds); "The middle panel of [2](#fig:larson_obs) shows the virial masses of the resolved clouds of NGC 5806 (calculated using the observed velocity dispersion $\sigma_{\mathrm{obs,los}}$) as a function of their gas masses, overlaid with the best-fitting power law (black solid line)." (Dynamical states of clouds); "By rejecting the assumption of a uniform CO-to-H$_2$ conversion factor $X_{\mathrm{CO}}$ and assuming instead that all resolved clouds are virialised ($\alpha_{\mathrm{obs,los}}=1$), we can infer the variations of $X_{\mathrm{CO}}$." (CO conversion factor)
   - parameter: Geometrical factor b_s = 1/5  
  > "Here we adopt $b_{\mathrm s}=1/5$ assuming the clouds have homogeneous spherical shapes." (Dynamical states of clouds)
   - assumption: Homogeneous spherical cloud shapes (b_s = 1/5); alpha_obs,los = 1 for inferring X_CO variations  
  > "Here we adopt $b_{\mathrm s}=1/5$ assuming the clouds have homogeneous spherical shapes." (Dynamical states of clouds); "By rejecting the assumption of a uniform CO-to-H$_2$ conversion factor $X_{\mathrm{CO}}$ and assuming instead that all resolved clouds are virialised ($\alpha_{\mathrm{obs,los}}=1$), we can infer the variations of $X_{\mathrm{CO}}$." (CO conversion factor)
   - fitting: Power-law fits and Spearman rank correlation coefficients.  
  > "There is a strong correlation between size and linewidth, with a Spearman rank correlation coefficient of $0.77$." (Dynamical states of clouds); "The best-fitting power-law of all clouds is $\alpha_{\mathrm{vir}}\propto\sigma_{\mathrm{obs,los}}^{0.63\pm0.06}$ (black solid lines in first row of [1](#fig:virial_relation))." (Dependence of virial parameter on cloud properties)
   - validation: _not stated_
8. **Estimate bar-driven gas inflow rate and compare inflow kinetic energy with turbulent dissipation in the nuclear ring**: Measure average velocity difference between double peaks in node LOSVDs to obtain V_in = V_in,obs / sin(i); compute mass inflow rate M_dot_in = 2 <Sigma_gas> W_in V_in and kinetic energy input rate E_dot_in = 0.5 M_dot_in V_in^2; compare with turbulent energy dissipation rate E_dot_diss = M_NR sigma_NR^3 / (2 h_NR).  
  > "To measure the relative velocity between the gas inflowing along the dust lanes and the nuclear ring, we consider individual LOSVDs in the nodes and estimate the velocity difference between the two dominant peaks." (Turbulence maintained by bar-driven gas inflow); "Adopting this relative velocity, the total mass inflow rate along the two dust lanes is estimated to be $\dot{M}_{\mathrm{in}}=2\langle\Sigma_{\mathrm{gas}}\rangle W_{\mathrm{in}}V_{\mathrm{in}}\approx5$ M$_{\odot}$ yr$^{-1}$" (Turbulence maintained by bar-driven gas inflow); "The energy per unit time dissipated by the observed turbulence can be estimated as (cite: maclow_klessen2004) $$\begin{equation}
    \dot{E}_{\rm diss} \approx M_{\rm NR} \sigma_{\rm NR}^3/(2h_{\rm NR})~,
\end{equation}$$" (Turbulence maintained by bar-driven gas inflow)
   - parameter: W_in = 100 pc, <Sigma_gas> = 200 M_sun pc^-2, i = 58 deg, M_NR = 2.2 x 10^8 M_sun, sigma_NR = 16 km s^-1, h_NR = 16 pc  
  > "where the width of gas inflow $W_{\mathrm{in}}$ is taken to be $\approx100$ pc and the mean of the molecular gas surface density in the bar is $\langle\Sigma_{\mathrm{gas}}\rangle\approx 200$ M$_{\odot}$ pc$^{-2}$." (Turbulence maintained by bar-driven gas inflow); "where $M_{\rm NR} \approx 2.2 \times 10^8 ~{\rm M_\odot}$, $\sigma_{\rm NR} \approx 16~{\rm km~s^{-1}}$ and $h_{\rm NR} \approx 16~{\rm pc}$ are the total gas mass, mean velocity dispersion and scale height of the molecular gas in the nuclear ring, respectively." (Turbulence maintained by bar-driven gas inflow)
   - assumption: Inflow occurs in galaxy plane with inclination i = 58 deg; two dust lanes of width 100 pc  
  > "The gas inflow velocity is then $V_{\mathrm{in}}= V_{\mathrm{in,obs}}/\sin i\approx120$ km s$^{-1}$(cite: sato2021)." (Turbulence maintained by bar-driven gas inflow)
   - fitting: _not stated_
   - validation: _not stated_
9. **Estimate GMC lifetimes and disruption timescales in the nuclear ring**: Calculate travel time between nodes t_travel = pi R_NR / (V_c,NR - Omega_p R_NR); count clouds in adjacent azimuthal zones (N_I, N_II) to find lost fraction F_lost = (N_I - N_II)/N_I and lifetime t_lifetime = (t_travel / 2) / F_lost; compare with collision (t_coll), shear (t_shear), and turbulent crossing (t_cross) timescales.  
  > "We estimate $t_{\rm travel}$ as** $$\begin{equation}
    t_{\mathrm{travel}}=\pi R_{\mathrm{NR}}/(V_{\mathrm{c,NR}}-\Omega_{\mathrm{p}}R_{\mathrm{NR}}) ~,
\end{equation}$$" (GMC lifetime in the nuclear ring); "In this case, the cloud lifetime can be calculated as** $$\begin{equation}
    t_{\mathrm{lifetime}}=\frac{t_{\mathrm{travel}}}{2} \frac{1}{F_{\mathrm{lost}}}~.
\end{equation}$$" (GMC lifetime in the nuclear ring); "To gain insights into the mechanism responsible for cloud disruptions, we now derive the time scales for these processes and compare them with our derived cloud lifetime." (GMC lifetime in the nuclear ring)
   - parameter: R_NR = 320 pc, V_c,NR = 150 km s^-1, bar end = 3.5 kpc, corotation radius = 4.2 kpc, V_c(4.2 kpc) = 220 km s^-1, D_c = 78 pc, sigma_cc = 10 km s^-1, elliptical annulus (230 pc inner, 370 pc outer, ellipticity 0.3, 85 clouds), Oort's A = 0.15 km s^-1 pc^-1, R_c = 39 pc, sigma_obs,los = 7.4 km s^-1  
  > "where $R_{\mathrm{NR}}$ is the radius at the centre of the nuclear ring (here $\approx320$ pc), $V_{\mathrm{c,NR}}$ is the circular velocity at the nuclear ring radius (here $\approx150$ km s$^{-1}$)" (GMC lifetime in the nuclear ring); "The end of the bar has a $\approx3.5$ kpc distance from the centre and a rotational velocity at the corotation radius of $V_{\mathrm{c}}(4.2~\mathrm{kpc})\approx220$ km s$^{-1}$, yielding $\Omega\approx52$ km s$^{-1}$ kpc$^{-1}$." (GMC lifetime in the nuclear ring); "To estimate $N_{\mathrm{mc}}$, we consider the $85$ nuclear ring clouds to be contained within an elliptical annulus of inner semi-major axis length $230$ pc, outer semi-major axis length $370$ pc and ellipticity $0.3$, that nicely encloses the nuclear ring, yielding $N_{\mathrm{mc}}\approx450$ kpc$^{-2}$ and in turn $t_{\mathrm{coll}}\approx3.1$ Myr." (GMC lifetime in the nuclear ring)
   - assumption: Pattern speed of nuclear ring equals large-scale bar pattern speed; corotation radius is 1.2 times bar length; cloud-cloud velocity dispersion sigma_cc = 10 km s^-1  
  > "by adopting the fact that the orbital angular velocity at the corotation radius, which is typically 1.2 times larger than the bar length, represents the bar pattern speed (cite: anthanassoula1992_dust_shock; aguerri1998_bar)." (GMC lifetime in the nuclear ring); "and $\sigma_{\mathrm{cc}}$ is the cloud-cloud velocity dispersion, generally assumed to be $\approx10$ km s$^{-1}$ (cite: koda2006; inutsuka2015_cloud)." (GMC lifetime in the nuclear ring)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.0, 5.6.1: Pipeline calibration of raw data (v4.7.0), combining array configurations via concat, continuum subtraction via uvcontsub, and interactive cleaning/imaging via tclean (v5.6.1).  
  > "The raw data of each configuration were calibrated using the standard ALMA pipeline provided by ALMA regional centre staff, using COMMON ASTRONOMY SOFTWARE APPLICATIONS (CASA; (cite: mcmullin2007_casa)) version 4.7.0." (Data reduction); "Using CASA version 5.6.1, we then combined the ACA data using the CASA task `concat` with default weighting." (Data reduction); "Although continuum emission is not detected (see below), we subtracted any continuum that may be present using the CASA task `uvcontsub`. We then cleaned the data using the `tclean` task interactively" (Data reduction)
- **CPROPSTOO (modified)** : Identifying giant molecular clouds and calculating their physical properties.  
  > "We utilise our own modified version of the algorithms of CPROPSTOO (cite: liu2021ngc4429), that is an updated version of CPROPS (cite: Rosolowsky2006cprops; Leroy2015cpropstoo), to identify the clouds in NGC 5806." (Cloud identification); "Following the standard CPROPSTOO/CPROPS definitions (cite: Rosolowsky2006cprops), we calculate the physical properties of the clouds identified." (GMC properties)
- **IDL** : Running MPFIT2DFUN to fit 2D velocity planes to individual clouds.  
  > "where $a$ and $b$ are the projected velocity gradient along the $x$- and the $y$-axis on the sky, respectively, and $c$ is a zero point, that we determine using the Interactive Data Language code MPFIT2DFUN (cite: mpfit2dfun_ref)." (Velocity Gradients of Individual Clouds)
- **MPFIT2DFUN** : Fitting a 2D plane to the intensity-weighted first moment map of each cloud to measure velocity gradients.  
  > "where $a$ and $b$ are the projected velocity gradient along the $x$- and the $y$-axis on the sky, respectively, and $c$ is a zero point, that we determine using the Interactive Data Language code MPFIT2DFUN (cite: mpfit2dfun_ref)." (Velocity Gradients of Individual Clouds)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total number of identified GMCs | 366 | not stated | dimensionless | 3 | As a result, we identify $366$ GMCs, $170$ of which are both spatially and spectrally resolved, as shown in [3](#fig:cloudfinding_result). |
| Number of spatially and spectrally resolved GMCs | 170 | not stated | dimensionless | 3 | As a result, we identify $366$ GMCs, $170$ of which are both spatially and spectrally resolved, as shown in [3](#fig:cloudfinding_result). |
| Total 12CO(2-1) flux in central 9'' x 9'' region | 300 | not stated | Jy km s^-1 | 2 | The total $^{12}$CO(2-1) flux in that region is $\approx300$ Jy km s$^{-1}$. |
| Resolved cloud size (R_c) range | 15 to 85 | not stated | pc | 4 | The sizes ($R_\mathrm{c}$) of the resolved clouds of NGC 5806 range from $15$ to $85$ pc (top-left panel of [4](#fig:histogram)). |
| Mean of Gaussian fit to resolved cloud size (R_c) | 27.8 | 0.7 (std dev 9.4) | pc | 4 | The mean of the Gaussian fit is $27.8\pm0.7$ pc and the standard deviation $9.4$ pc, while the median radius is $30.2$ pc. |
| Median resolved cloud size (R_c) | 30.2 | not stated | pc | 4 | The mean of the Gaussian fit is $27.8\pm0.7$ pc and the standard deviation $9.4$ pc, while the median radius is $30.2$ pc. |
| Resolved cloud gas mass (M_gas) range | 1.18 x 10^5 to 3.64 x 10^7 | not stated | M_sun | 4 | The resolved clouds have gas masses $M_{\mathrm{gas}}$ ranging from $1.18\times10^5$ to $3.64\times10^7$ M$_{\odot}$ (top-right panel of [4](#fig:histogram)). |
| Mean of Gaussian fit to log(M_gas / M_sun) | 5.66 | 0.04 (std dev 0.4) | dex | 4 | The mean of the Gaussian fit to the $\log(M_\mathrm{gas}/\mathrm{M_{\odot}})$ distribution is $5.66\pm0.04$ ($\approx4.6\times10^5$ M$_{\odot}$) and the standard deviation $0.4$, while the median gas mass is $5.5\times10^5$ M$_{\odot}$. |
| Median resolved cloud gas mass (M_gas) | 5.5 x 10^5 | not stated | M_sun | 4 | while the median gas mass is $5.5\times10^5$ M$_{\odot}$. |
| Resolved cloud observed velocity dispersion (sigma_obs,los) range | 1.6 to 35.9 | not stated | km s^-1 | 4 | The observed velocity dispersions of the resolved clouds range from $1.6$ to $35.9$ km s$^{-1}$ (bottom-left panel of [4](#fig:histogram)). |
| Mean of Gaussian fit to observed velocity dispersion (sigma_obs,los) | 5.2 | 0.23 (std dev 2.7) | km s^-1 | 4 | The mean of the Gaussian fit is $5.2\pm0.23$ km s$^{-1}$ and the standard deviation $2.7$ km s$^{-1}$, while the median observed velocity dispersion is $5.63$ km s$^{-1}$. |
| Median observed velocity dispersion (sigma_obs,los) | 5.63 | not stated | km s^-1 | 4 | while the median observed velocity dispersion is $5.63$ km s$^{-1}$. |
| Resolved cloud gas mass surface density (Sigma_gas) range | 81 to 1000 | not stated | M_sun pc^-2 | 4 | The gas mass surface densities of the resolved clouds range from $81$ to $1000$ M$_{\odot}$ pc$^{-2}$ (bottom-right panel of [4](#fig:histogram)). |
| Mean of Gaussian fit to log(Sigma_gas / M_sun pc^-2) | 2.29 | 0.02 (std dev 0.2) | dex | 4 | The mean of the Gaussian fit to the $\log(\Sigma_{\mathrm{gas}}/{\mathrm{M_\odot~pc^{-2}}})$ distribution is $2.29\pm0.02$ ($\approx195$ M$_{\odot}$) and the standard deviation $0.2$, while the median gas mass surface density is $2.3$ ($\approx200$ M$_{\odot}$). |
| Cumulative mass function truncated power-law slope (gamma) | -1.72 | 0.12 | dimensionless | 5 | The best-fitting slopes of the truncated and non-truncated power laws are $\gamma=-1.72\pm0.12$ and $\gamma=-1.86\pm0.06$, respectively. |
| Cumulative mass function non-truncated power-law slope (gamma) | -1.86 | 0.06 | dimensionless | 5 | The best-fitting slopes of the truncated and non-truncated power laws are $\gamma=-1.72\pm0.12$ and $\gamma=-1.86\pm0.06$, respectively. |
| Projected velocity gradient (omega_obs) range | 0.01 to 0.67 | not stated | km s^-1 pc^-1 | 6 | The projected velocity gradients $\omega_{\mathrm{obs}}$ of the $170$ resolved clouds of NGC 5806 range from $0.01$ to $0.67$ km s$^{-1}$ pc$^{-1}$, with an average and median gradient of $0.10$ and $0.08$ km s$^{-1}$ pc$^{-1}$, respectively. |
| Average projected velocity gradient (omega_obs) | 0.10 | not stated | km s^-1 pc^-1 | 6 | with an average and median gradient of $0.10$ and $0.08$ km s$^{-1}$ pc$^{-1}$, respectively. |
| Median projected velocity gradient (omega_obs) | 0.08 | not stated | km s^-1 pc^-1 | 6 | with an average and median gradient of $0.10$ and $0.08$ km s$^{-1}$ pc$^{-1}$, respectively. |
| Size-linewidth relation power-law slope | 1.07 | 0.06 | dimensionless | 7 | $$\begin{equation}
    \log\left(\frac{\sigma_{\mathrm{obs,los}}}{\mathrm{km\ s^{-1}}}\right)=(0.15\pm0.03)+(1.07\pm0.06)\log\left(\frac{R_\mathrm{c}}{\mathrm{pc}}\right)\,\,\,,
\end{equation}$$ |
| Size-linewidth relation intercept | 0.15 | 0.03 | dex | 7 | $$\begin{equation}
    \log\left(\frac{\sigma_{\mathrm{obs,los}}}{\mathrm{km\ s^{-1}}}\right)=(0.15\pm0.03)+(1.07\pm0.06)\log\left(\frac{R_\mathrm{c}}{\mathrm{pc}}\right)\,\,\,,
\end{equation}$$ |
| Virial mass vs gas mass power-law slope | 1.11 | 0.03 | dimensionless | 7 | $$\begin{equation}
    \log\left(\frac{M_{\mathrm{obs,vir}}}{\mathrm{M_{\odot}}}\right)=(-0.41\pm0.02)+(1.11\pm0.03)\log\left(\frac{M_{\mathrm{gas}}}{\mathrm{M_{\odot}}}\right)\,\,\,,
\end{equation}$$ |
| Mean virial parameter (alpha_vir) | 2.07 | not stated | dimensionless | 7 | The mean (median) of $\alpha_{\mathrm{vir}}$ is $2.07$ ($1.66$), indicating that on average the clouds are marginally virialised. |
| Median virial parameter (alpha_vir) | 1.66 | not stated | dimensionless | 7 | The mean (median) of $\alpha_{\mathrm{vir}}$ is $2.07$ ($1.66$), indicating that on average the clouds are marginally virialised. |
| Gas inflow velocity (V_in) | 120 | not stated | km s^-1 | 8 | The gas inflow velocity is then $V_{\mathrm{in}}= V_{\mathrm{in,obs}}/\sin i\approx120$ km s$^{-1}$(cite: sato2021). |
| Total mass inflow rate (M_dot_in) | 5 | not stated | M_sun yr^-1 | 8 | Adopting this relative velocity, the total mass inflow rate along the two dust lanes is estimated to be $\dot{M}_{\mathrm{in}}=2\langle\Sigma_{\mathrm{gas}}\rangle W_{\mathrm{in}}V_{\mathrm{in}}\approx5$ M$_{\odot}$ yr$^{-1}$ |
| Kinetic energy input rate by gas inflow (E_dot_in) | 3.5 x 10^4 | not stated | M_sun km^2 s^-2 yr^-1 | 8 | the kinetic energy per unit time input by gas inflow is $\dot{E}_{\rm in} \approx 3.5\times 10^4 {\rm ~M_\odot~ km^2~s^{-2}~yr^{-1}}$. |
| Turbulence energy dissipation rate in nuclear ring (E_dot_diss) | 2.8 x 10^4 | not stated | M_sun km^2 s^-2 yr^-1 | 8 | We then derive the turbulence energy dissipation per unit time in the nuclear ring $\dot{E}_{\rm diss} \approx 2.8 \times 10^4 {\rm ~M_\odot~ km^2~s^{-2}~yr^{-1}}$ |
| Bar pattern speed (Omega_p) | 52 | not stated | km s^-1 kpc^-1 | 9 | The end of the bar has a $\approx3.5$ kpc distance from the centre and a rotational velocity at the corotation radius of $V_{\mathrm{c}}(4.2~\mathrm{kpc})\approx220$ km s$^{-1}$, yielding $\Omega\approx52$ km s$^{-1}$ kpc$^{-1}$. |
| Travel time between nodes in nuclear ring (t_travel) | 7.8 | not stated | Myr | 9 | We thus adopt this orbital angular velocity as the pattern speed of the bar $\Omega_{\mathrm{p}}$, yielding the travel time $t_{\rm travel}$ of $\approx7.8$ Myr. |
| GMC lifetime in the nuclear ring (t_lifetime) | 5.4 to 6.4 | not stated | Myr | 9 | By adopting the travel time ($7.8$ Myr), the cloud lifetime $t_{\mathrm{lifetime}}$ ranges $5.4$ – $6.4$ Myr. |
| Cloud-cloud collision timescale in nuclear ring (t_coll) | 3.1 | not stated | Myr | 9 | yielding $N_{\mathrm{mc}}\approx450$ kpc$^{-2}$ and in turn $t_{\mathrm{coll}}\approx3.1$ Myr. |
| Shear timescale in nuclear ring (t_shear) | 3.2 | not stated | Myr | 9 | This thus yields a shear timescale of $t_{\mathrm{shear}}\approx3.2$ Myr, that is again approximately half the travel time and smaller than the cloud lifetime $t_{\rm lifetime} \approx 5.4$ – $6.4$ Myr. |
| Turbulent crossing timescale in nuclear ring (t_cross) | 11 | not stated | Myr | 9 | yielding a typical turbulent crossing timescale $t_{\rm cross} \approx 11~$ Myr, that is much larger than the travel time and the cloud lifetime. |
| Mean inferred CO-to-H2 conversion factor (X_CO,20) | 4.05 | not stated | 10^20 cm^-2 (K km s^-1)^-1 | 7 | and show in [2](#fig:Xco_obs) the distribution of $X_{\mathrm{CO,20}}$ of all resolved clouds of NGC 5806 (identical to [\[fig:alpha_obs\]](#fig:alpha_obs) within a scaling factor), with a logarithmic mean of $0.61$ ($X_{\mathrm{CO,20}}\approx4.05$). |

## Qualitative findings

- The molecular gas in NGC 5806 has a highly structured distribution with a clear nucleus, nuclear ring (nodes and arcs), and bi-symmetric offset dust lanes.  
  > "The molecular gas of NGC 5806 has a highly structured distribution with a clear nucleus, nuclear ring (including two nodes and arcs) and dust lanes." (Abstract)
- Clouds in the nuclear ring (arcs and nodes) are generally larger, more massive, more turbulent, and have higher surface densities than those in the nucleus and dust lanes, and have shallower cumulative mass functions.  
  > "On the other hand, the clouds in the arcs and nodes are the largest, most massive, most turbulent and have the largest surface densities." (GMC properties in different regions); "Despite these limitations, however, the cloud mass functions of the nodes and arcs (i.e. nuclear ring) are significantly shallower than those of the nucleus and dust lanes." (GMC cumulative mass functions)
- A spatially-varying CO-to-H2 conversion factor is likely not necessary in the central kiloparsec of NGC 5806 because the inferred X_CO distributions across the four regions are similar.  
  > "Finally, [2](#fig:Xco_obs) shows that the distributions of $X_{\mathrm{CO,20}}$ in the four regions are similar to each other, with similar means. A spatially-varying conversion factor might therefore not be necessary in the central kiloparsec of NGC 5806." (CO conversion factor)

## Claim tuples

- H: Internal velocity gradients of GMCs in NGC 5806 are governed by large-scale galaxy rotation rather than turbulent motions. | E: Fit 2D planes to cloud first-moment maps to obtain projected angular velocities and rotation axes, and compare them with galaxy isovelocity contours, low-resolution velocity models, Burkert & Bodenheimer (2000) turbulence predictions, and gradient-subtracted velocity dispersions. | R: Cloud rotation axes are not well aligned with galaxy isovelocity contours, modelled galaxy angular velocities are ~3.5 times larger than observed, observed median angular velocity (0.08-0.10 km s^-1 pc^-1) matches the turbulence prediction (0.092 km s^-1 pc^-1), and 107/170 clouds have sigma_gs,los / sigma_obs,los > 0.7. | F: The observed velocity gradients and velocity dispersions of the clouds in NGC 5806 are dominated by internal turbulence rather than large-scale galaxy rotation. | **refuted**
- H: The resolved GMCs in NGC 5806 follow a steep size-linewidth relation and are marginally virialised, with gravitational boundedness primarily determined by internal turbulence. | E: Fit power laws to the size-linewidth relation (sigma_obs,los vs R_c), virial mass vs gas mass relation, and virial parameter vs cloud properties for the 170 resolved clouds. | R: The size-linewidth relation has a slope of 1.07 +/- 0.06 (Spearman coefficient 0.77), the mean (median) virial parameter is 2.07 (1.66), and alpha_vir correlates positively with sigma_obs,los (slope 0.63 +/- 0.06, Spearman 0.45) but shows no clear dependence on R_c or M_gas. | F: The size-linewidth relation in NGC 5806 is the steepest found so far, likely due to strong bar-induced shocks and compressible turbulence, and the clouds are on average marginally virialised with boundedness primarily dependent on turbulence. | **supported**
- H: Bar-driven gas inflow maintains the high velocity dispersions and turbulence observed in the nuclear ring of NGC 5806. | E: Measure the velocity splitting of double-peaked LOSVDs in the nodes to estimate the gas inflow velocity and mass inflow rate, and compare the resulting kinetic energy input rate (E_dot_in) with the turbulent energy dissipation rate (E_dot_diss) in the nuclear ring. | R: The gas inflow velocity is ~120 km s^-1 and the mass inflow rate is ~5 M_sun yr^-1, yielding E_dot_in ~ 3.5 x 10^4 M_sun km^2 s^-2 yr^-1, which approximately balances E_dot_diss ~ 2.8 x 10^4 M_sun km^2 s^-2 yr^-1. | F: Bar-driven gas inflow is a viable origin for maintaining the observed high velocity dispersions in the nuclear ring. | **supported**
- H: The strong azimuthal decline in cloud numbers downstream of the nodes in the nuclear ring is caused by short cloud lifetimes regulated by cloud-cloud collisions, shear, and/or stellar feedback rather than internal turbulent disruption. | E: Count clouds in adjacent azimuthal zones between the nodes to compute the lost fraction F_lost and cloud lifetime from the travel time in the bar pattern frame, and compare with characteristic timescales of cloud-cloud collisions, shear, and turbulent crossing. | R: Cloud numbers drop from N_I = 23 to N_II = 9 (F_lost = 0.61) and N_I = 40 to N_II = 11 (F_lost = 0.72), yielding t_lifetime = 5.4 - 6.4 Myr for t_travel = 7.8 Myr; collision (t_coll ~ 3.1 Myr) and shear (t_shear ~ 3.2 Myr) timescales are shorter than t_lifetime, whereas the turbulent crossing timescale (t_cross ~ 11 Myr) is much longer. | F: Clouds in the nuclear ring have short lifetimes (~6 Myr) and are disrupted primarily by cloud-cloud collisions (especially in the nodes), galactic shear, and/or stellar feedback (in the arcs), while turbulent disruption is ruled out. | **supported**

## Reasoning

- Why this data: Combined two 12-m configurations (C40-3 and C40-6) with 7-m ACA observations to achieve both high angular resolution (~24 pc to resolve individual GMCs) and good flux recovery.  
  > "The observations were carried out using two different $12$-m array configurations in October and December 2016 (programme 2016.1.00437.S, configurations C40-3 and C40-6, PI Davis) and the $7$-m Atacama Compact Array (ACA) in July 2017 (programme 2016.2.00053.S, PI Liu) to achieve both high angular resolution and good flux recovery." (Data)
- Why this method: Used a modified version of CPROPSTOO with stepped minarea/minpix and a convexity parameter to reduce arbitrariness and identify structures over multiple scales in complex and crowded environments; used gas mass rather than virial mass for cumulative mass functions because it is well-defined for unresolved clouds and requires no dynamical state assumptions.  
  > "Our version of CPROPSTOO has fewer free parameters, leading to a more efficient and robust cloud identification in complex and crowded environments." (Cloud identification); "This parameter allows to identify structures over multiple scales with less arbitrariness." (Cloud identification); "Here we use the gas mass rather than the virial mass to determine the mass function, as the former is well defined even for spatially-unresolved clouds, and no assumption on the dynamical state of the clouds is required." (GMC cumulative mass functions)
- Alternative: Using gradient-subtracted velocity dispersion (sigma_gs,los) instead of observed velocity dispersion (sigma_obs,los) for dynamical scaling analyses: rejected because bulk motions due to galaxy rotation are found not to be important, and using sigma_obs,los is consistent with previous GMC studies.  
  > "In turn, we will use the observed velocity dispersions ($\sigma_{\mathrm{obs,los}}$) rather than the gradient-subtracted velocity dispersions ($\sigma_{\mathrm{gs,los}}$) for the rest of our analyses, also consistent with previous GMC studies." (Origin of velocity gradients)
- Alternative: Using virial mass instead of gas mass for cumulative mass functions: rejected because gas mass is well-defined even for spatially-unresolved clouds and requires no assumption on dynamical state.  
  > "Here we use the gas mass rather than the virial mass to determine the mass function, as the former is well defined even for spatially-unresolved clouds, and no assumption on the dynamical state of the clouds is required." (GMC cumulative mass functions)
- Alternative: Comparing star formation rate with gas inflow rate using MUSE data: considered in author notes and deferred due to dust extinction correction issues and SFR discrepancies.  
  > "I suggest not to discuss SF and SFR in our paper, since correction for dust extinction is a big issue.)" (Turbulence maintained by bar-driven gas inflow)
- How they decided it was enough: _not stated_
- Limitation (authors): Small sample sizes of clouds within individual galactic regions and the fixed convexity parameter over multiple scales in modified CPROPSTOO lead to bumpy cumulative mass functions, large slope uncertainties, and failed truncated power-law fits in the nucleus.  
  > "We note that to avoid a failure of some of the fits, the five most massive clouds from each of the nucleus and the nodes were excluded from the fit (although the nucleus truncated power-law fit still fails)." (GMC cumulative mass functions); "Due to limited number of clouds (i.e. the small sample size) in each region, and the fact that our modified CPROPSTOO code identifies GMCs with a fixed convexity over multiple scales (leading to bumpy mass functions), our best-fitting slopes for each region have large uncertainties and the fits do not always seem to represent the mass functions well, especially in the nucleus and nodes." (GMC cumulative mass functions)
- Limitation (authors): Uncertainty in galaxy distance D is not propagated into cloud property uncertainties (it acts as a systematic scaling).  
  > "The uncertainty of the galaxy distance $D$ is not considered, as an error of the distance translates to a systematic scaling of some quantities" (GMC properties)
- Limitation (authors): Lack of a high-resolution, extinction-free star formation tracer image prevents direct constraint on stellar feedback timescales.  
  > "A high-resolution image of star formation tracer that is free of dust extinction, however, is required to constrain the effect of stellar feedback on cloud disruption in future studies." (GMC lifetime in the nuclear ring)
- Caveat (inferred, ours): The provided manuscript text contains unremoved internal co-author draft comments (marked 'WR:', 'MB:', 'LL:') and minor inconsistencies between numbers in the text (e.g., median cloud radius stated as 30.2 pc in Section 3.2.1 vs 30.6 pc in Section 4.2).
- Caveat (inferred, ours): The derivation of the rotation curve V_c(R_gal) used in Section 6.2 to compute the bar pattern speed and Oort's constant A is referred to as 'the rotation curve that derived above', but the actual derivation of the rotation curve is missing from the text.
- Caveat (inferred, ours): The formula for F_lost is printed with a missing parenthesis as 'F_lost = N_I - N_II / N_I' instead of '(N_I - N_II) / N_I', though the numerical values (0.61 and 0.72) use the correct expression.

## Reproducibility

- Data public (paper): Available in the ALMA archive under project codes 2016.1.00437.S and 2016.2.00053.S.  
  > "The data underlying this article are available in the ALMA archive (https://almascience.eso.org/asax/) under project code: (1) 2016.1.00437.S (2) 2016.2.00053.S." (Data availability)
- Products in archive: _not stated_
- Missing: Source code or repository link for the authors' modified version of CPROPSTOO (from Liu et al. 2021)
- Missing: Exact spatial coordinates/masks for the four galactic regions (nucleus, arcs, nodes, dust lanes)
- Missing: Details and parameters of the rotation curve derivation V_c(R_gal)
- Missing: Exact smoothing kernel size used to construct the coarse-grained velocity map for omega_model
- Data volume (inferred): ~10-50 GB (two 12-m configurations and one ACA 7-m dataset in Band 6 with 3840-channel spectral windows)
- Score (inferred): 7/5, Raw ALMA project codes, CASA versions, visibility combination weights (0.2 and 1.0), imaging parameters (robust=0.5, pixel=0.05'', channel=2 km/s, RMS=0.86 mJy/beam), and CPROPSTOO parameters (SNR thresholds 2.5/1.5, minvchan=2, Delta T_max=1.7 K, minarea/minpix=96-24 step 24, convexity=0.5) are all explicitly specified. However, the modified CPROPSTOO code is not publicly linked, the region boundary coordinates are only shown graphically, and the rotation curve derivation is omitted.
- Rediscovery candidate: yes, All ALMA data are public under two stated project codes, the data reduction and cloud decomposition parameters are thoroughly documented, and the paper provides a rich set of quantitative answer keys (cloud catalog, property distributions, scaling relation slopes, mass function slopes, inflow rate, and cloud lifetimes).

## Links

- Method: (cite: liu2021ngc4429) (Introduced the modified CPROPSTOO algorithm, convexity parameter, gradient-subtracted velocity dispersion, bootstrapping method, and shear timescale formulation used throughout this work.)
- Method: (cite: Rosolowsky2006cprops) (Original CPROPS algorithm and standard GMC property definitions.)
- Method: (cite: Leroy2015cpropstoo) (CPROPSTOO update to the CPROPS cloud identification package.)
- Method: (cite: dame2011) (Smooth-moment masking method used to generate the CO moment maps.)
- Method: (cite: rosolowsky2005) (Error-in-variable method used to fit the cumulative GMC mass functions.)
- Method: (cite: meidt2015) (Azimuthal cloud number statistics method adapted here to estimate GMC lifetimes in the nuclear ring.)
- Method: (cite: koda2021) (Measuring cloud travel time with respect to the rotating bar pattern.)
- Companion: (cite: liu2021ngc4429) (Earlier WISDOM project GMC study (NGC 4429) establishing the modified CPROPSTOO methodology.)
- Companion: (cite: liu2022_ngc404) (Earlier WISDOM project GMC study (NGC 404).)
- Companion: (cite: lu2022_wisdom) (WISDOM project paper linking GMC properties to star formation.)
- Companion: (cite: davis2022_wisdom) (WISDOM project paper providing the central molecular gas mass of NGC 5806.)
- Related: WISDOM (mm-Wave Interferometric Survey of Dark Object Masses)

## Checks

```json
{
 "quotes": 202,
 "quotes_ok": 202,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 5,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 35,
 "numeric_problems": 0,
 "fill": {
  "facts": 113,
  "stated": 88,
  "rate": 0.779
 },
 "evidence_ok": true
}
```

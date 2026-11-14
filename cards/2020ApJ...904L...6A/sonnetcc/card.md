# A Case of Simultaneous Star and Planet Formation

`2020ApJ...904L...6A` | The Astrophysical Journal Letters 2020 | first author: Alves, Felipe O. | arXiv: 2010.15135 | DOI: 10.3847/2041-8213/abc550

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Does the young Class I-II disk BHB1 host a giant dust gap carved by a planet, and is the system still accreting gas from its environment?  
  > "Gaps are also now being observed in younger, Class I sources, and thus there is reinvigorated debate about *when* the process of planet formation starts" (Introduction); "As a result, this system asks the question, can planets form before the disk itself is fully formed?" (Conclusions)
- Target **[BHB2007] 1 (BHB1)**: coordinates _not stated_; z/distance _not stated_; distance from Dzib et al. 2018 (cite: Dzib18), numerical distance not given in the text  
  > "a K7 young stellar object (YSO) with a bolometric luminosity of" (Introduction); "The bolometric luminosity reported by (cite: Covey10) and mentioned above is scaled with the distance estimation reported by (cite: Dzib18)." (Footnote 2)

## Data provenance

- ALMA projects: 2013.1.00291.S
- bands: 226 GHz (1.3 mm)  
  > "BHB1 was observed with ALMA at 226 GHz as part of project code 2013.1.00291.S (PI: Alves)." (2.1 ALMA data)
- frequencies and spectral setup: 12CO and C18O J=2-1 observed simultaneously; line velocity resolution 0.35 km/s (~270 kHz)  
  > "$^{12}$CO and C$^{18}$O $J=2\rightarrow1$ were simultaneously observed covering the source and its surroundings." (2.1 ALMA data); "The spectral line data have velocity resolution of 0.35 km s$^{-1}$ ($\sim 270$ kHz)" (2.1 ALMA data)
- continuum bandwidth: 2.4 GHz  
  > "The total continuum-dedicated bandwidth is 2.4 GHz." (2.1 ALMA data)
- arrays: 44 antennae  
  > "These observations used 44 antennae with baseline ranging from 15 to 1460 m." (2.1 ALMA data)
- configurations: _not stated_
- baselines: 15 to 1460 m  
  > "These observations used 44 antennae with baseline ranging from 15 to 1460 m." (2.1 ALMA data)
- angular resolution: continuum beam 0.24'' x 0.20'', PA 77 deg; line beam 0.25'' x 0.20'', PA ~72 deg  
  > "The continuum map was produced using Briggs robust parameter 0.5 and has a synthesized beam of $0.24\ensuremath{''} \times 0.20\ensuremath{''}$ and position angle (PA) of 77$^\circ$ (East of North)." (2.1 ALMA data); "The final map has an rms noise of 3.5 mJy beam$^{-1}$ and a synthesized beam of $0.25\ensuremath{''} \times0.20\ensuremath{''}$ (PA $\sim 72\ensuremath{^\circ}$)." (2.1 ALMA data)
- max recoverable scale: ~21''  
  > "In this configuration, the maximum recoverable angular scale is $\sim$ 21$''$." (2.1 ALMA data)
- sensitivity: continuum rms 0.095 mJy/beam; line rms 3.5 mJy/beam  
  > "The reprocessed image has an *rms* noise of 0.095 mJy beam$^{-1}$" (2.1 ALMA data); "The final map has an rms noise of 3.5 mJy beam$^{-1}$" (2.1 ALMA data)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: project 2013.1.00291.S, PI: Alves  
  > "BHB1 was observed with ALMA at 226 GHz as part of project code 2013.1.00291.S (PI: Alves)." (2.1 ALMA data)
- Line: 12CO J=2-1 (not stated)
- Line: C18O J=2-1 (not stated)
- Other facility **VLA**: 22.2 GHz (K-band) continuum in the most extended configuration; synthesized beam 0.197'' x 0.087'', rms 7.5 uJy/beam  
  > "We have used the VLA in its most extended configuration to observe the 22.2 GHz continuum" (2.2 VLA data); "an *rms* noise of 7.5 $\mu$Jy beam$^{-1}$" (2.2 VLA data)
- External data: Stellar parameters of BHB1: K7, L_bol ~1.7 Lsun, Teff 4060 K, flat SED  
  > "a bolometric luminosity of $\sim1.7$ L$_{\odot}$, effective temperature of 4060 K" (Introduction) [from (cite: Brooke07; Forbrich09; Covey10)]
- External data: Source (cloud) velocity of 3.6 km/s used as a consistency check  
  > "consistent with previous estimates of 3.6 km s$^{-1}$ (cite: Onishi99)" (3.2 Disk CO observations) [from (cite: Onishi99)]
- External data: Dzib et al. distance scaling the bolometric luminosity  
  > "is scaled with the distance estimation reported by (cite: Dzib18)" (Footnote 2) [from (cite: Dzib18)]
- Simulation/model as data: TORUS parametric axisymmetric radiative transfer disk model, synthetic 1.287 mm image convolved with the observed beam, compared to the ALMA continuum by eye  
  > "TORUS computes a synthetic image at 1.287 mm, which we convolve with the observed beam." (4.1 Radiative transfer analysis)
- Simulation/model as data: A few non-LTE LIME models on the TORUS structure with the gas inside the gap artificially reduced  
  > "We have artificially decreased the gas inside of the gap by varying factors." (4.1 Radiative transfer analysis)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.5  
  > "CASA 4.5 was used for calibration and imaging" (2.1 ALMA data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: phase gains (scan and integration time intervals) then amplitude gains (scan intervals), decreasing solution intervals  
  > "We performed self-calibration of the *uv* visibilities by interpolating over decreasing solution intervals the phase gains (scan and integration time intervals) and amplitude gains (scan intervals)." (2.1 ALMA data)

### Imaging

- task: CASA clean (stated for the VLA image; ALMA imaging task not named)  
  > "The VLA image was obtained using CASA clean and a robust weighting of 1" (2.2 VLA data)
- deconvolver: _not stated_
- weighting robust: ALMA continuum and lines: Briggs robust 0.5; VLA: robust 1  
  > "The continuum map was produced using Briggs robust parameter 0.5" (2.1 ALMA data); "Images were produced using a 0.5 Briggs robust parameter." (2.1 ALMA data); "a robust weighting of 1" (2.2 VLA data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied to continuum and line maps  
  > "Both continuum and spectral line maps were primary beam corrected" (2.1 ALMA data)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: continuum 0.24'' x 0.20'' PA 77 deg; line 0.25'' x 0.20'' PA ~72 deg; VLA 0.197'' x 0.087'' PA 10.3 deg  
  > "The continuum map was produced using Briggs robust parameter 0.5 and has a synthesized beam of $0.24\ensuremath{''} \times 0.20\ensuremath{''}$ and position angle (PA) of 77$^\circ$ (East of North)." (2.1 ALMA data); "The final map has an rms noise of 3.5 mJy beam$^{-1}$ and a synthesized beam of $0.25\ensuremath{''} \times0.20\ensuremath{''}$ (PA $\sim 72\ensuremath{^\circ}$)." (2.1 ALMA data)
- final rms: continuum 0.095 mJy/beam; line 3.5 mJy/beam; VLA 7.5 uJy/beam  
  > "The reprocessed image has an *rms* noise of 0.095 mJy beam$^{-1}$" (2.1 ALMA data); "The final map has an rms noise of 3.5 mJy beam$^{-1}$" (2.1 ALMA data); "an *rms* noise of 7.5 $\mu$Jy beam$^{-1}$" (2.2 VLA data)

### Inherited from earlier work

- ALMA calibration details taken from an earlier paper  
  > "CASA 4.5 was used for calibration and imaging, where details of the calibration can be found in (cite: Alves17)." (2.1 ALMA data) [from (cite: Alves17)]
- VLA correlator setup and the same VLA observations used for another source  
  > "A detailed description of the correlator setup is found in (cite: Alves19)" (2.2 VLA data) [from (cite: Alves19)]
- Keplerian model fit to the CO position-velocity diagram follows a published prescription  
  > "following the prescription of (cite: SSW16), we fit a Keplerian model to the position-velocity diagram of the CO emission" (3.2 Disk CO observations) [from (cite: SSW16)]
- Planet-mass estimate uses the DSHARP gap-width scaling  
  > "we adopt the approach used in DSHARP survey (cite: Zhang2018)" (4.2 The Mass of the potential planet) [from (cite: Zhang2018)]
- Disk surface-density form follows the viscously evolving disk formalism  
  > "The functional form of the disk model follows the (cite: lyndenbell1974) formalism for a viscously evolving disk" (4.1 Radiative transfer analysis) [from (cite: lyndenbell1974)]
- Dust split into two MRN populations (up to 1 micron and 1 mm)  
  > "The dust is split into two MRN population distributions with sizes up to 1 micron and 1 mm (cite: cleeves2016)" (4.1 Radiative transfer analysis) [from (cite: cleeves2016)]
- CO abundance prescription approximating freeze-out and photodissociation  
  > "similar to the approach of (cite: qi2006) to approximate CO freeze-out and photodissociation" (4.1 Radiative transfer analysis) [from (cite: qi2006)]

### Not stated but needed to reproduce (our reading)

- Which calibration route (pipeline or manual) and which pipeline version were used; the paper defers to Alves et al. 2017
- Self-calibration solution intervals (the actual solint values) and number of iterations
- Clean mask, threshold, deconvolver, cell and image size for continuum and CO cubes
- Continuum-subtraction method and line-free channels for the CO and C18O cubes
- Flux calibrator and flux-scale uncertainty
- Which ALMA configuration(s) and number of execution blocks were combined, and on-source time
- Source distance used to convert arcsec to au (only 'Dzib18' is cited, no number given)
- Procedure used to extract disk radius, gap width and PV-diagram Keplerian fit, including channel range and PV cut position angle
- TORUS model grid, by-eye fit criterion and full parameter table for the best model (e.g. ring masses, flaring of the dust)
- LIME model setup (grid, velocity field, gas-depletion factors tried)
- Source of the stellar-mass-to-Jupiter-mass conversion details and the exact disk Sigma_g profile used in the Zhang2018 scaling
- VLA calibration steps, observing dates and total time on source

## Analysis recipe

1. **Calibrate, self-calibrate and image ALMA continuum and CO cubes**: Calibration in CASA 4.5; phase then amplitude self-calibration; Briggs robust 0.5 imaging; primary beam correction  
  > "CASA 4.5 was used for calibration and imaging" (2.1 ALMA data); "Both continuum and spectral line maps were primary beam corrected" (2.1 ALMA data)
   - software: CASA 4.5
   - parameter: Briggs robust 0.5 for continuum and lines  
  > "Images were produced using a 0.5 Briggs robust parameter." (2.1 ALMA data)
   - parameter: Source offset ~4.6'' from the phase center  
  > "since the source is offset by $\sim 4.6\ensuremath{''}$ from the phase center" (2.1 ALMA data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure dust disk geometry and gap from the 1.3 mm continuum**: Read from the continuum image: three peaks interpreted as an edge-on gapped disk; radius, position angle, gap width and brightness temperature measured; extraction procedure not described  
  > "interpreted as an edge-on view of a gapped disk" (3.1 Dust substructure in the disk); "The inner and outer disk are separated by a gap with $\sim70$ au width." (3.1 Dust substructure in the disk)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit Keplerian rotation to CO PV diagram for stellar mass**: Keplerian model fit to the CO position-velocity diagram using uncontaminated channels, following Seifried et al. 2016  
  > "Using the uncontaminated channels and following the prescription of (cite: SSW16), we fit a Keplerian model to the position-velocity diagram of the CO emission" (3.2 Disk CO observations)
   - parameter: Central channels of 12CO contaminated by cloud; C18O less contaminated  
  > "The $^{12}$CO has cloud contamination in the central channels" (3.2 Disk CO observations)
   - fitting: _not stated_
   - validation: Source velocity compared with the previous estimate of 3.6 km/s  
  > "we find that the source velocity is consistent with previous estimates of 3.6 km s$^{-1}$ (cite: Onishi99)" (3.2 Disk CO observations)
4. **Measure VLA 22.2 GHz compact sources and spectral-index limit**: Flux densities of VLA 1 and tentative VLA 1b from the K-band image; 1.3 mm intensity minima in the northern and southern gaps compared to bound the spectral index of VLA 1b  
  > "The VLA data show a compact radio source at the protostellar position with a flux density of $103\pm12$ $\mu$Jy (we refer to this source as VLA 1)." (3.4 Localized emission in the south-east gap); "This puts an upper limit for the spectral index of VLA 1b of $\ensuremath{\lesssim} 0.8$ (assuming a 2-$\sigma$ upper limit at 1.3 mm)" (3.4 Localized emission in the south-east gap)
   - software: CASA clean
   - parameter: VLA robust weighting 1, beam 0.197'' x 0.087''  
  > "The VLA image was obtained using CASA clean and a robust weighting of 1" (2.2 VLA data)
   - assumption: No trace of VLA 1b at 1.3 mm because gap minima are equal within uncertainties  
  > "i. e., there are no traces of VLA 1b at 1.3 mm." (3.4 Localized emission in the south-east gap)
   - fitting: _not stated_
   - validation: _not stated_
5. **Model dust gap size and test for gas in the gap (TORUS and LIME)**: Parametric axisymmetric TORUS model adjusted by eye over just over 100 models to the mm image; LIME non-LTE models with the gas in the gap reduced by various factors  
  > "we have adjusted the model parameters until we achieve a good fit by eye to the mm data" (4.1 Radiative transfer analysis); "We explored just over 100 models and arrived at a reasonable fit as shown in Figure [3](#fig:dustmod)." (4.1 Radiative transfer analysis)
   - software: TORUS, LIME
   - parameter: Gas: Sigma_c = 15 g cm^-2, R_c = 100 au, gamma = 1, no gas gaps  
  > "For the gas, $\Sigma_{c} = 15$ g cm$^{-2}$, $R_c = 100$ au, and $\gamma = 1$, and we do not include gas gaps." (4.1 Radiative transfer analysis)
   - parameter: Large grains: gamma = 0.2, R_c = 1000 au; outer disk component from 93 au to 160 au; inner disk edge 0.1 au extending to 20 au  
  > "We model an empty gap, and then an outer disk component starting at 93 au extending out to 160 au where it is truncated." (4.1 Radiative transfer analysis); "The inner disk edge is set to 0.1 au and extends to 20 au." (4.1 Radiative transfer analysis)
   - assumption: Global gas-to-dust ratio of 100; small grains (up to 1 micron) hold 1% of dust mass; pure astrosilicate  
  > "we assume a global gas to dust ratio of 100" (4.1 Radiative transfer analysis); "both adopt pure astrosilicate compositions (cite: draine84)" (4.1 Radiative transfer analysis)
   - assumption: CO abundance 1e-4 per H above 20 K dust temperature and 1e-10 per H below  
  > "We assume a simple uniform CO abundance of $10^{-4}$ relative to H above dust temperatures of 20 K and $10^{-10}$ per H below" (4.1 Radiative transfer analysis)
   - fitting: By-eye fit, no sampler or likelihood  
  > "we have adjusted the model parameters until we achieve a good fit by eye to the mm data" (4.1 Radiative transfer analysis)
   - validation: Fit judged by eye; gap-edge position reproduced within ~5 au within the model grid  
  > "We find that within our grid of models, the inner edge of the outer ring can reasonably reproduce the structure qualitatively within $\pm5$ au." (4.1 Radiative transfer analysis)
6. **Estimate companion mass from the gap width (DSHARP scaling)**: Relative gap width (Delta) from the gap profile, then width-mass fitting of K' for two dust size distributions and two viscosities to get planet-to-star mass ratio  
  > "we estimate the relative width of the gap ($\Delta$ parameter in (cite: Zhang2018), which is the gap width over the radius of the outer gap edge) as 0.78." (4.2 The Mass of the potential planet)
   - parameter: DSD1: 0.005 micron to 0.1 mm, power-law index -3.5; DSD2: 0.005 micron to 1 cm, index -2.5  
  > "If we adopt DSD1 dust size distribution in DSHARP (dust size follows a power law distribution from 0.005 $\mu$m to 0.1 mm with a power law index of -3.5)" (4.2 The Mass of the potential planet)
   - parameter: (h/r) at 50 au = 0.1; alpha = 1e-3 and 1e-4  
  > "Thus, with $(h/r)_{50 au}$=0.1, we can derive that the planet-to-star mass ratio is 0.031 if the disk viscosity coefficient is $\alpha=10^{-3}$ and 0.015 if $\alpha=10^{-4}$." (4.2 The Mass of the potential planet)
   - assumption: Gas surface density taken from the TORUS model of step 5; stellar mass from step 3  
  > "Adopting the stellar mass computed in §[3.2](#sec:gas), the mass of the planet ranges between $\sim 4$ and 70 M$_{\mathrm{Jup}}$." (4.2 The Mass of the potential planet)
   - fitting: _not stated_
   - validation: Dominant uncertainty identified as maximum particle size and viscosity  
  > "We note that the dominant uncertainty in this determination is the maximum particle size and disk viscosity" (4.2 The Mass of the potential planet)
7. **Characterise CO filaments and test infall kinematics**: Line-of-sight CO velocity versus distance to the protostar compared with free-fall projected onto the line of sight  
  > "Figure [4](#figinfall) displays the line-of-sight (LOS) velocity of CO gas as a function of distance to the protostar." (5.1 Accretion filaments); "Infalling gas parcels departing from rest with no energy dissipation have their LOS velocities determined as" (5.1 Accretion filaments)
   - assumption: Infall from rest with no energy dissipation; protostellar mass M_star  
  > "Infalling gas parcels departing from rest with no energy dissipation" (5.1 Accretion filaments)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.5: ALMA calibration and imaging; VLA imaging (clean)  
  > "CASA 4.5 was used for calibration and imaging" (2.1 ALMA data); "The VLA image was obtained using CASA clean" (2.2 VLA data)
- **TORUS** : Parametric axisymmetric radiative transfer model of the dust gap  
  > "we explore parametric axisymmetric models using the TORUS radiative transfer code (cite: harriestorus2014)" (4.1 Radiative transfer analysis)
- **LIME** : Non-LTE models to test how much gas could be hidden in the gap in optically thick 12CO  
  > "we have additionally run a few non-LTE LIME (cite: Brinch10) models with our TORUS-derived structure" (4.1 Radiative transfer analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA continuum rms noise | 0.095 | not stated | mJy/beam | 1 | The reprocessed image has an *rms* noise of 0.095 mJy beam$^{-1}$, intensity peak of 19.5 mJy beam$^{-1}$ and flux density of 0.16 $\pm$ 0.02 Jy. |
| ALMA continuum peak intensity | 19.5 | not stated | mJy/beam | 1 | The reprocessed image has an *rms* noise of 0.095 mJy beam$^{-1}$, intensity peak of 19.5 mJy beam$^{-1}$ and flux density of 0.16 $\pm$ 0.02 Jy. |
| ALMA continuum flux density | 0.16 | 0.02 | Jy | 1 | The reprocessed image has an *rms* noise of 0.095 mJy beam$^{-1}$, intensity peak of 19.5 mJy beam$^{-1}$ and flux density of 0.16 $\pm$ 0.02 Jy. |
| CO line map rms noise | 3.5 | not stated | mJy/beam | 1 | The final map has an rms noise of 3.5 mJy beam$^{-1}$ |
| Disk inclination | 75 | not stated | deg | 0 | We present ALMA observations of a nearly edge-on ($i = 75^{\circ}$) disk |
| Dust disk radius | 107 | not stated | au | 2 | The disk has a radius of 107 au and is oriented $\sim 15\ensuremath{^\circ}$ East-of-North. |
| Disk orientation (position angle) | ~15 East of North | not stated | deg | 2 | The disk has a radius of 107 au and is oriented $\sim 15\ensuremath{^\circ}$ East-of-North. |
| Dust gap width | ~70 | not stated | au | 2 | The inner and outer disk are separated by a gap with $\sim70$ au width. |
| Peak mm dust brightness temperature | ~10 | not stated | K | 2 | The mm dust brightness temperature peaks at $\sim10$ K. |
| Protostellar mass from Keplerian fit | 2.23 | 0.04 | Msun | 3 | find a mass of 2.23 $\pm$ 0.04 M$_{\odot}$ for the embedded protostar |
| Filament length scale | ~4000 | not stated | au | 1 | Molecular emission reveals large scale ($\sim4000$ au) and narrow ($\sim80-300$ au) bipolar filaments |
| Filament width | ~80-300 | not stated | au | 1 | Molecular emission reveals large scale ($\sim4000$ au) and narrow ($\sim80-300$ au) bipolar filaments |
| VLA 1 flux density at 22.2 GHz | 103 | 12 | uJy | 4 | a flux density of $103\pm12$ $\mu$Jy (we refer to this source as VLA 1) |
| VLA 1b flux density at 22.2 GHz | 30 | 8 | uJy | 4 | This tentative source has a flux density of $30\pm8$ $\mu$Jy |
| Spectral index upper limit of VLA 1b | <~0.8 | not stated | dimensionless | 4 | This puts an upper limit for the spectral index of VLA 1b of $\ensuremath{\lesssim} 0.8$ (assuming a 2-$\sigma$ upper limit at 1.3 mm) |
| ALMA continuum minima in northern and southern gaps | 5.21 and 5.28 | 0.10 | mJy/beam | 4 | show intensity minima (5.21 and 5.28 mJy beam$^{-1}$) that within uncertainties (0.10 mJy beam$^{-1}$) are the same |
| CO hot spot temperature in the gap | 100 | not stated | K | 0 | Inside the gap, the molecular gas has a warm (100 K) component coinciding in position with a tentative free-free emission excess observed with the VLA. |
| Gas+dust mass of the TORUS disk model | 0.1 | not stated | Msun | 5 | The gas+dust mass of this disk model is 0.1 M$_\odot$. |
| Inner edge of outer ring (model) | 93 | 5 (qualitative) | au | 5 | We model an empty gap, and then an outer disk component starting at 93 au extending out to 160 au where it is truncated.; the inner edge of the outer ring can reasonably reproduce the structure qualitatively within $\pm5$ au |
| Gas gap depth needed to be visible in 12CO | > factor 100 | not stated | dimensionless | 5 | a gap in the gas distribution is only visible when the gap depth is higher than a factor 100 |
| Relative gap width Delta | 0.78 | not stated | dimensionless | 6 | which is the gap width over the radius of the outer gap edge) as 0.78 |
| Planet-to-star mass ratio, DSD1 | 0.031 (alpha=1e-3); 0.015 (alpha=1e-4) | not stated | dimensionless | 6 | we can derive that the planet-to-star mass ratio is 0.031 if the disk viscosity coefficient is $\alpha=10^{-3}$ and 0.015 if $\alpha=10^{-4}$. |
| Planet-to-star mass ratio, DSD2 | 0.0039 (alpha=1e-3); 0.0019 (alpha=1e-4) | not stated | dimensionless | 6 | The planet-to-star mass ratio is 0.0039 if $\alpha=10^{-3}$, and 0.0019 if $\alpha=10^{-4}$. |
| Companion mass range | ~4 to 70 | range from dust size distribution and viscosity | MJup | 6 | the mass of the planet ranges between $\sim 4$ and 70 M$_{\mathrm{Jup}}$ |

## Qualitative findings

- Giant dust gap with no matching gap seen in 12CO  
  > "a giant gap seen in dust but not in $^{12}$CO gas" (abstract)
- Large-scale low-velocity CO filaments aligned with the disk major axis, interpreted as infall from the local ISM  
  > "the $^{12}$CO observations reveal low- velocity large scale filaments aligned with the disk major axis and velocity coherent with the disk gas that we interpret as ongoing gas infall from the local ISM" (abstract)
- CO hot spot in the southern gap coincides with the tentative VLA 1b source  
  > "Interestingly, VLA 1b coincides with a bright ($\sim 100$ K) and compact $^{12}$CO emission hot spot" (3.4 Localized emission in the south-east gap)

## Claim tuples

- H: Is the wide dust gap carved by a young giant planet or brown dwarf? | E: TORUS fit of the gap size plus DSHARP gap-width scaling for two dust size distributions and two viscosities | R: Gap ~70 au wide; planet-to-star mass ratio 0.0019 to 0.031 (about 4-70 MJup) | F: Gap consistent with a single companion of 4-70 MJup, but the feature still must be confirmed | **partially**
- H: Does compact warm gas and radio emission inside the gap trace the companion? | E: Compared the VLA 22.2 GHz map and the ALMA 1.3 mm and 12CO maps in the gap | R: VLA 1b at 30 +/- 8 uJy at the position of a ~100 K CO hot spot, no counterpart at 1.3 mm | F: VLA 1b is ionized gas coinciding with warm CO; tentative sign of an accreting substellar companion | **partially**
- H: Is gas present inside the dust gap? | E: LIME non-LTE models on the TORUS structure with the gas in the gap depleted by different factors | R: A gas gap is visible in 12CO only when depleted by more than a factor 100 | F: Some gas remains in the gap; it is not fully cleared | **supported**
- H: Are the large-scale CO filaments infalling streamers feeding the disk? | E: Mapped 12CO filaments and compared their LOS velocities with disk rotation and free-fall | R: Filaments ~4000 au long, aligned with the disk major axis, velocity-coherent with disk rotation, no acceleration along them | F: Filaments are most plausibly streamers connecting B59 gas to BHB1; a limb-brightened outer disk or flattened envelope is not excluded | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: By-eye TORUS model used only to constrain the gap size, leaving detailed modelling to later work  
  > "Since the goal of this is to approximately constrain the size of the gap, we have adjusted the model parameters until we achieve a good fit by eye to the mm data and leave more complex modeling to a future analysis." (4.1 Radiative transfer analysis)
- Alternative: Filaments could instead be a limb-brightened large outer disk or flattened envelope  
  > "Alternatively, we could be seeing a limb-brightened large ($>1000$ au) scale outer disk or flattened envelope" (3.3 Large-scale filamentary CO emission)
- Alternative: VLA 1b radio emission could come from a strong magnetosphere of a fast rotating substellar object; disfavoured because old brown dwarfs are 1-2 orders of magnitude fainter  
  > "However, the radio luminosities observed in old brown dwarfs are $1-2$ orders of magnitudes lower than the flux detected here" (5.2 A giant planet hidden in the cavity?)
- How they decided it was enough: Stopped after just over 100 models once a reasonable fit was reached  
  > "We explored just over 100 models and arrived at a reasonable fit as shown in Figure [3](#fig:dustmod)." (4.1 Radiative transfer analysis)
- Limitation (authors): Gap depth in dust was not varied because only one thermal continuum wavelength is available  
  > "We do not vary the depth of the gap as we only have one thermal continuum wavelength" (4.1 Radiative transfer analysis)
- Limitation (authors): Gas gap depth would need more detailed thermo-chemical fitting  
  > "We emphasize that the true gap depth would require more detailed fitting, ideally with thermo- chemical models" (4.1 Radiative transfer analysis)
- Limitation (authors): VLA 1b is a marginal, tentative detection needing follow-up  
  > "the data reveal a marginal second peak in the southern gap" (3.4 Localized emission in the south-east gap)
- Caveat (inferred, ours): The abstract cites 1D hydrodynamic models, but the text derives the planet mass from the DSHARP width-mass scaling, not a hydrodynamic run described here.
- Caveat (inferred, ours): The planet mass range (4-70 MJup) spans the planet to brown dwarf regime and rests on assumed alpha, dust size distribution and h/r.
- Caveat (inferred, ours): VLA 1b is a marginal detection (30 +/- 8 uJy, under 4 sigma) and its link to the CO hot spot is positional only.
- Caveat (inferred, ours): Distance is never given as a number, so au conversions (gap width, radius, 49 au separation) cannot be checked.
- Caveat (inferred, ours): The dust model is fit by eye with one wavelength and no uncertainties on the gap edges beyond ~5 au.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Full calibration and self-calibration recipe (deferred to Alves et al. 2017)
- Missing: Clean parameters, masks and line-free channels
- Missing: Best-fit TORUS and LIME input files and the by-eye fit criterion
- Missing: VLA calibration details and observing dates
- Missing: Distance adopted for converting angular to physical scales
- Data volume (inferred): One ALMA Band 6 project, 44 antennas, continuum plus 12CO/C18O cubes: likely tens of GB of raw data (inferred, not stated).
- Score (inferred): 3/5, The ALMA project code, band, beams, robust and rms are given, but calibration is deferred to an earlier paper, key imaging and self-calibration settings are missing, and the models are fit by eye; the main numbers (stellar mass, flux densities, mass ratios) are reported.
- Rediscovery candidate: no, The paper does not state that the data are public, self-calibration and imaging settings are incomplete, and the dust model is a by-eye fit that cannot be redone exactly.

## Links

- Method: Alves et al. 2017 (cite: Alves17) (Details of the ALMA calibration)
- Method: Alves et al. 2019 (cite: Alves19) (VLA correlator setup for the same VLA observations)
- Method: Zhang et al. 2018 (cite: Zhang2018) (DSHARP gap-width to planet-mass scaling)
- Method: Seifried et al. 2016 (cite: SSW16) (Prescription for the Keplerian fit to the position-velocity diagram)
- Companion: Alves et al. 2019 (cite: Alves19) (Reports a distinct source from the same VLA observations)
- Companion: Zurlo et al. in preparation (Near-infrared scattered-light observations of the same system)
- Related: VLA/16B-290
- Related: DSHARP

## Checks

```json
{
 "quotes": 124,
 "quotes_ok": 124,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 1,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 24,
 "numeric_problems": 0,
 "fill": {
  "facts": 101,
  "stated": 68,
  "rate": 0.673
 },
 "evidence_ok": true
}
```

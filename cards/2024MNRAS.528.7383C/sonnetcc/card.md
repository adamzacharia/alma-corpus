# FAUST XII. Accretion streamers and jets in the VLA 1623-2417 protocluster

`2024MNRAS.528.7383C` | Monthly Notices of the Royal Astronomical Society 2024 | first author: Codella, C. | arXiv: 2402.10258 | DOI: 10.1093/mnras/stae472

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: Do molecular streamers feed the VLA 1623-2417 protostars, and do SO and SiO trace the streamers and the protostellar jet?  
  > "we present a survey in SO and SiO of the VLA 1623–2417 protostellar cluster in order to reveal material associated with accretions streamers as well as protostellar jets." (Introduction)
- Target **VLA 1623-2417 (A1+A2, B, W)**: coordinates Phase centre RA(J2000) = 16h 26m 26.392s, Dec(J2000) = -24d 24m 30.178s  
  > "The observations were centered at $\alpha_{\rm J2000}$ = 16$^{\rm h}$ 26$^{\rm m}$ 26.392s, $\delta_{\rm J2000}$ = –24$\ensuremath{^\circ}$ 24$\ensuremath{'}$ 30.178$''$." (Observations); "at a projected angular separation of $\simeq$ 1$\ensuremath{''}$ ($\sim$130 au)" (The VLA1623–2417 protostellar system); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2018.1.01205.L
- bands: Band 6; Setup 1: 214.0-219.0 and 229.0-234.0 GHz, Setup 2: 242.5-247.5 and 257.2-262.5 GHz  
  > "ALMA Band 6 (Setup 1: 214.0–219.0 GHz and 229.0–234.0 GHz, Setup 2: 242.5–247.5 GHz and 257.2–262.5 GHz)" (Observations)
- frequencies and spectral setup: SO and SiO windows with 59 MHz bandwidth, 122 kHz resolution (0.14-0.17 km/s)  
  > "The SO and SiO lines were observed using spectral windows with a bandwidth/frequency resolution of 59 MHz/122 kHz ($\sim$80 km s$^{-1}$/0.14–0.17 km s$^{-1}$)." (Observations)
- continuum bandwidth: 1.875 GHz wide spectral window  
  > "A wide bandwidth (1.875 GHz) spectral window was also included to support measurement of the continuum emission." (Observations)
- arrays: 12-m array plus ACA 7-m array (12 antennas)  
  > "using the 12-m array (C43-1, C43-4, with 48 and 49 antennas, respectively) as well as the ACA (Atacama Compact Array) 7-m array (12 antennas)" (Observations)
- configurations: C43-1 and C43-4 (12-m, 48 and 49 antennas) plus ACA  
  > "using the 12-m array (C43-1, C43-4, with 48 and 49 antennas, respectively)" (Observations)
- baselines: 9 m to 969 m  
  > "The baselines were between 9 m ($B_{\rm min}$) and 969 m ($B_{\rm max}$), for a maximum recoverable scale" (Observations)
- angular resolution: 50 au; line beams 0.54'' x 0.45'' (PA=-75 deg) Setup 1, 0.48'' x 0.45'' (PA=+86 deg) Setup 2  
  > "at the spatial resolution of 50 au" (abstract); "The synthesized beams of the line datasets are 0.54$''$$\times$0.45$''$ (PA=–75$^{\circ}$), for Setup 1, and 0.48$''$$\times$0.45$''$ (PA=+86$^{\circ}$), for Setup 2." (Observations)
- max recoverable scale: ~29 arcsec  
  > "for a maximum recoverable scale ($\theta_{\rm MRS}$ $\sim$ $0.6\,\lambda\,B_{\rm min}^{-1}$) of $\sim\,$29$\ensuremath{''}$" (Observations)
- sensitivity: line rms ~3 mJy/beam per channel; continuum rms 0.22 mJy/beam (Setup 1), 0.15 mJy/beam (Setup 2)  
  > "The typical r.m.s. noise (per channel) is $\sim$3 mJy beam$^{-1}$." (Observations); "the r.m.s. noise is 0.22 mJy beam$^{-1}$ (Setup 1), and 0.15 mJy beam$^{-1}$ (Setup 2)" (Observations)
- time on source: _not stated_
- observing dates: 2018 December to 2020 March  
  > "The VLA1623 multiple system was observed between 2018 December, and 2020 March with ALMA Band 6" (Observations)
- pi or archival as stated: FAUST Large Program (PI: S. Yamamoto)  
  > "in the context of the FAUST Large Program (2018.1.01:205.L, PI: S. Yamamoto)" (Observations)
- Line: SO 5_6-4_5 (219.9 GHz (219949.442 MHz))
- Line: SO 6_6-5_5 (258.3 GHz (258255.826 MHz))
- Line: SiO 5-4 (217.1 GHz (217104.980 MHz))
- External data: C18O(2-1) FAUST dataset used for H2 column density and streamer mass  
  > "we inspected the C$^{18}$O(2–1) dataset, published by (cite: Mercimek2023)" (Excitation temperature of the VLA1623 B accretion streamer) [from (cite: Mercimek2023)]
- External data: CS(5-4) moment 1 map overlaid on SO maps and PV cuts  
  > "On these maps the intensity-weighted velocity CS(5–4) map (moment 1 map), by (cite: Ohashi2022), is overlapped." (Southern region: the VLA1623 B accretion streamer) [from (cite: Ohashi2022)]
- External data: Systemic velocity Vsys = +3.8 km/s  
  > "i.e. $V_{\rm sys}$ = +3.8 km s$^{-1}$ (cite: Ohashi2022)" (Overall SO spatial distribution and spectra) [from (cite: Ohashi2022)]
- External data: Spectroscopic parameters of SO and SiO lines  
  > "Spectroscopic parameters are from (cite: Klaus1996), and (cite: Bogey1997) (SO), and (cite: Manson1977), for SiO, retrieved from the CDMS database (cite: Muller2005)." (Table 1) [from (cite: Klaus1996); (cite: Bogey1997); (cite: Manson1977); (cite: Muller2005)]
- External data: Bolometric luminosity of source B, 0.2-0.3 Lsun  
  > "The bolometric luminosity of source B derived by (cite: Murillo2018L) based on the source spectral energy distribution is 0.2–0.3 $L_{\rm \ensuremath{\odot}}$" (Accretion and infalling rates) [from (cite: Murillo2018L)]
- External data: Dynamical mass of protostar B, 1.7 Msun (from disk rotation curve)  
  > "the protostellar mass has been estimated from the fit of the rotation curve of the disk by (cite: Ohashi2022), giving a dynamical mass of 1.7 $M_{\rm \ensuremath{\odot}}$." (Accretion and infalling rates) [from (cite: Ohashi2022)]
- External data: Total mass inside the streamer radius, 1-2 Msun  
  > "a total mass in the 1–2 $M_{\rm \ensuremath{\odot}}$ range (cite: Murillo2018L; Ohashi2022)" (Accretion and infalling rates) [from (cite: Murillo2018L; Ohashi2022)]
- External data: 16O/18O = 560 and CO/H2 = 1e-4  
  > "Using the classical $^{16}$O/$^{18}$O = 560 and CO/H$_2$ = 10$^{-4}$ (cite: Wilson1994)" (Accretion and infalling rates) [from (cite: Wilson1994)]
- External data: Stellar radius R* = 2 Rsun  
  > "assuming that the stellar radius is $R_{\rm *}$ = 2 $R_{\rm \ensuremath{\odot}}$ (cite: Stahler1988)" (Accretion and infalling rates) [from (cite: Stahler1988)]
- External data: Typical jet temperature of 100+-50 K used for the SiO column density  
  > "The SiO total column density has been derived assuming a typical jet temperature of 100$\pm$50 K (cite: Podio2021)" (VLA 1623B: the SiO jet) [from (cite: Podio2021)]
- External data: Disk geometry (inclination, position angle) used to deproject jet velocities  
  > "The velocities once deprojected using the geometry of the protostellar system (cite: Harris2018)" (SO and SiO jet emission) [from (cite: Harris2018)]
- External data: Toy model of protostellar heating giving ~20 K at ~390 au  
  > "Based on a simple toy model where the gas and dust are heated by the central protostars (without considering the outflow cavities and the disks) (cite: Ceccarelli2000)" (Excitation temperature of the VLA1623 B accretion streamer) [from (cite: Ceccarelli2000)]

## Processing

### Calibration

- pipeline or manual: calibration pipeline in CASA plus an additional routine for Tsys issues and spectral normalization  
  > "including an additional calibration routine to correct for $T_{\rm sys}$ issues and spectral data normalization" (Observations)
- casa version: CASA 5.6.1-8  
  > "within CASA 5.6.1-8 (cite: CASA2022)" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: quasars J1427-4206, J1517-2422, J1625-2527, J1924-2914, J1626-2951 (roles not specified)  
  > "Data were calibrated using the quasars J1427-4206, J1517-2422, J1625-2527, J1924-2914, and J1626-2951" (Observations)
- flux scale uncertainty: ~10%  
  > "reaching an absolute flux calibration uncertainty of $\sim$10%" (Observations)
- self calibration: self-calibrated using line-free continuum channels  
  > "The data were self-calibrated using line-free continuum channels." (Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs parameter 0.5 for line cubes; uniform weighting for continuum  
  > "were cleaned with a Briggs parameter of 0.5" (Observations); "The continuum has been imaged using uniform weighting" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: line cubes are continuum-subtracted (method not described)  
  > "the resulting continuum-subtracted line-cubes were cleaned" (Observations)
- line free channels: _not stated_
- primary beam correction: applied  
  > "The primary beam correction has also been applied." (Observations)
- array combination: three array configurations merged before cleaning  
  > "Once the three array configurations were merged, the resulting continuum-subtracted line-cubes were cleaned" (Observations)
- smoothing: SiO(5-4) cube spectrally smoothed to 1 km/s (rms 1 mJy/beam)  
  > "the SiO(5–4) datacube has been spectrally smoothed to 1 km s$^{-1}$, for an r.m.s. of 1 mJy beam$^{-1}$." (Observations)
- final beam: continuum 0.37'' x 0.34'' (-65 deg) Setup 1, 0.43'' x 0.32'' (-65 deg) Setup 2; lines 0.54'' x 0.45'' (PA=-75 deg) Setup 1, 0.48'' x 0.45'' (PA=+86 deg) Setup 2  
  > "thus obtaining a beam of 0.37$''$ $\times$ 0.34$''$ ($-65^\circ$), and 0.43$''$ $\times$ 0.32$''$ ($-65^\circ$), for Setup 1 and Setup 2, respectively" (Observations); "The synthesized beams of the line datasets are 0.54$''$$\times$0.45$''$ (PA=–75$^{\circ}$), for Setup 1, and 0.48$''$$\times$0.45$''$ (PA=+86$^{\circ}$), for Setup 2." (Observations)
- final rms: continuum 0.22 mJy/beam (Setup 1), 0.15 mJy/beam (Setup 2); lines ~3 mJy/beam per channel  
  > "the r.m.s. noise is 0.22 mJy beam$^{-1}$ (Setup 1), and 0.15 mJy beam$^{-1}$ (Setup 2)" (Observations); "The typical r.m.s. noise (per channel) is $\sim$3 mJy beam$^{-1}$." (Observations)

### Inherited from earlier work

- Calibration pipeline (FAUST line-imaging pipeline)  
  > "Chandler et al. (in preparation)" (footnote 3) [from Chandler et al. (in preparation)]
- Additional Tsys and spectral normalization correction routine  
  > "Moellenbrock et al. (in preparation)" (footnote 4) [from Moellenbrock et al. (in preparation)]
- 1.2 mm continuum image previously reported (C43-4 only)  
  > "A 1.2 mm image has been already reported in the context of the FAUST campaign by (cite: Codella2022), but only using the C43-4 configuration of the 12m array." (Continuum emission) [from (cite: Codella2022)]
- 1.4 mm continuum image presented earlier  
  > "The 1.4 mm image has been presented by (cite: Mercimek2023) in the context of the analysis of source W." (Continuum emission) [from (cite: Mercimek2023)]
- Free-fall timescale equation  
  > "An estimate of the free-fall timescale of the southern streamer accreting VLA1623 B can be obtained using the classical equation (cite: Pineda2020; Pineda2023)" (Accretion and infalling rates) [from (cite: Pineda2020; Pineda2023)]

### Not stated but needed to reproduce (our reading)

- The cleaning task, deconvolver, threshold, mask and number of iterations for the line cubes and continuum.
- The line-free channels used for self-calibration and continuum subtraction, and the self-calibration solution intervals.
- Which of the listed quasars served as flux, bandpass and phase calibrator for each execution block.
- The velocity channel width and velocity grid of the final cubes (only the native 0.14-0.17 km/s is given).
- The extraction aperture or beam-averaging used for the spectra at (-0.7'',-3.0'') and the other positions, and the velocity range integrated for the SO line ratio.
- Line-flux or integrated-intensity values of the two SO lines, and the partition function and constants used for the LTE Tex and column density.
- How the 33+-9 K uncertainty was obtained, and the emitting area used for the streamer mass.
- How the C18O(2-1) cube of Mercimek2023 was imaged and regridded to compare with SO, and the C18O excitation temperature assumed.
- The GILDAS procedures used for moment maps and PV cuts, and any intensity clipping for moments 1 and 2.
- Details of the FAUST line-imaging pipeline (in preparation) and the Tsys/normalization routine.

## Analysis recipe

1. **Calibrate, self-calibrate, merge and image the data**: Calibration pipeline in CASA with an extra Tsys/spectral normalization routine, self-calibration on line-free continuum, merge of three array configurations, cleaning of continuum-subtracted line cubes  
  > "Once the three array configurations were merged, the resulting continuum-subtracted line-cubes were cleaned with a Briggs parameter of 0.5." (Observations); "The data were self-calibrated using line-free continuum channels." (Observations)
   - software: CASA 5.6.1-8
   - parameter: Briggs parameter 0.5 for line cubes  
  > "were cleaned with a Briggs parameter of 0.5" (Observations)
   - parameter: uniform weighting for the continuum  
  > "The continuum has been imaged using uniform weighting" (Observations)
   - fitting: _not stated_
   - validation: Dynamic range of the continuum improved by up to one order of magnitude with the extra calibration routine  
  > "the dynamical range of the continuum data improved up to one order of magnitude" (Observations)
2. **Extract spectra and make moment maps in velocity windows (S, LV, HV)**: SO spectra integrated over the 22'' field of view; moment 0 maps integrated over S (Vsys +-1 km/s), LV (blue 1-6.6, red 1-2.5 km/s from Vsys) and HV (blue up to 11.2, red up to 8.2 km/s) ranges; moment 1 and 2 maps for blue LV emission  
  > "SO(6$_6$–5$_5$) maps of the blue-shifted (by 1–6.6 km s$^{-1}$ with respect to $V_{\rm sys}$) and red-shifted emission (by 1–2.5 km s$^{-1}$)" (Southern region: the VLA1623 B accretion streamer); "blue-shifted by up to 11.2 km s$^{-1}$, and red-shifted by up to 8.2 km s$^{-1}$" (SO and SiO jet emission)
   - software: GILDAS
   - parameter: Vsys = +3.8 km/s  
  > "i.e. $V_{\rm sys}$ = +3.8 km s$^{-1}$ (cite: Ohashi2022)" (Overall SO spatial distribution and spectra)
   - assumption: LV velocity ranges are asymmetric and were chosen a posteriori to isolate the same molecular structure  
  > "they have been defined a posteriori after inspecting the SO dataset to identify velocity ranges tracing the same molecular structure" (Southern region: the VLA1623 B accretion streamer)
   - fitting: _not stated_
   - validation: _not stated_
3. **Characterise streamer kinematics with PV cuts and moment maps**: PV cuts along the southern direction from A and B, compared with CS(5-4); moment 1 and moment 2 maps of blue-shifted LV emission  
  > "Position-Velocity (PV) cut (obtained with a slice width equal to the beam)" (Southern region: the VLA1623 B accretion streamer)
   - software: GILDAS
   - parameter: slice width equal to the beam  
  > "Position-Velocity (PV) cut (obtained with a slice width equal to the beam)" (Southern region: the VLA1623 B accretion streamer)
   - fitting: _not stated_
   - validation: Outflow-cavity origin excluded because of curved morphology and because the southern cavity is red-shifted  
  > "the association with the outflow cavity is excluded from both the curved morphology" (Southern region: the VLA1623 B accretion streamer)
4. **Estimate SO excitation temperature of the streamer from two lines**: Two-line LTE estimate from SO(5_6-4_5) and SO(6_6-5_5) spectra extracted at offset (-0.7'', -3.0'')  
  > "a crude estimate of the SO excitation temperature ($T_{\rm ex}$) can be derived from the two SO observed lines: 33$\pm$9 K" (Excitation temperature of the VLA1623 B accretion streamer); "We extracted the spectrum at the position offset by –0.7$''$,–3.0$''$ (with respect to the phase center of the map, see Sect. 2)" (Excitation temperature of the VLA1623 B accretion streamer)
   - parameter: Spectrum position offset (-0.7'', -3.0'') from the phase centre  
  > "We extracted the spectrum at the position offset by –0.7$''$,–3.0$''$" (Excitation temperature of the VLA1623 B accretion streamer)
   - assumption: LTE population and optically thin lines  
  > "Assuming an LTE (Local Thermodynamic Equilibrium) population and optically thin lines" (Excitation temperature of the VLA1623 B accretion streamer)
   - fitting: _not stated_
   - validation: Compared with a toy protostellar heating model giving ~20 K at ~390 au; authors caution the comparison is based on two transitions only  
  > "For a total bolometric luminosity of $\sim$ 1 $L_{\rm \ensuremath{\odot}}$, we find that the temperature is $\sim$ 20 K." (Excitation temperature of the VLA1623 B accretion streamer)
5. **Derive column densities and streamer mass**: SO column density at Tex = 33 K; C18O column density converted to H2 with 16O/18O = 560 and CO/H2 = 1e-4; mass from emitting region and average H2 column density  
  > "The total mass of the blue-shifted southern streamer can be estimated from the emitting region and the estimate of the average C$^{18}$O (and consequently H$_2$) column density throughout the emitting region" (Accretion and infalling rates)
   - parameter: Tex = 33 K for SO; N_SO increases by a factor 2 for 20 K  
  > "To derive the uncertainty, $N_{\rm SO}$ increases by a factor 2 assuming 20 K instead of 33 K." (Accretion and infalling rates)
   - assumption: 16O/18O = 560 and CO/H2 = 1e-4  
  > "Using the classical $^{16}$O/$^{18}$O = 560 and CO/H$_2$ = 10$^{-4}$ (cite: Wilson1994)" (Accretion and infalling rates)
   - fitting: _not stated_
   - validation: Mass compared with Class 0 and Class I streamers from the literature  
  > "if we compare the VLA 1623–2417 southern streamer with the Class I streamers, our estimates are similar" (Accretion and infalling rates)
6. **Compute streamer infall rate and compare with accretion rate onto B**: Free-fall time t_ff = sqrt(R^3/(G M_total)) with R = 1500 au and M_total = 1-2 Msun; streamer infall rate = streamer mass / t_ff; accretion rate of B from Lbol R*/(G M*)  
  > "By dividing the streamer mass with the free-fall timescale we obtain an estimate of the accretion rate of the southern streamer onto the B protostar" (Accretion and infalling rates); "we assume that the source bolometric luminosity is due to the gravitational energy released by the accretion onto the protostar" (Accretion and infalling rates)
   - parameter: R = 1500 au; total mass 1-2 Msun  
  > "Taking R = 1500 au, a total mass in the 1–2 $M_{\rm \ensuremath{\odot}}$ range (cite: Murillo2018L; Ohashi2022)" (Accretion and infalling rates)
   - parameter: Lbol(B) = 0.2-0.3 Lsun, M* = 1.7 Msun, R* = 2 Rsun  
  > "assuming that the stellar radius is $R_{\rm *}$ = 2 $R_{\rm \ensuremath{\odot}}$ (cite: Stahler1988)" (Accretion and infalling rates)
   - assumption: Lbol = Lacc (all luminosity from accretion)  
  > "we assume that the source bolometric luminosity is due to the gravitational energy released by the accretion onto the protostar" (Accretion and infalling rates)
   - fitting: _not stated_
   - validation: Free-fall velocity compared with observed velocity difference of 1.6 km/s (56%-81%); M* varied over 0.05-0.25 Msun to bracket the accretion rate  
  > "i.e. values quite close (56%–81%) to the difference in velocity, 1.6 km s$^{-1}$, observed within the southern streamer" (Accretion and infalling rates)
7. **Derive SO abundance in the streamer**: Ratio of SO and H2 column densities at (-0.7'', -3.0'') where C18O is dominated by the streamer  
  > "by comparing the SO and H$_2$ column densities extracted at the (–0.7$''$,–3.0$''$) position" (SO abundances in the southern VLA1623 B streamer)
   - fitting: _not stated_
   - validation: Compared with abundances in molecular clouds and hot-corinos from the literature  
  > "This value is larger than that measured in the gas phase in molecular clouds located in Perseus, Taurus, and Orion" (SO abundances in the southern VLA1623 B streamer)
8. **Characterise the jet from B with HV SO and SiO**: Two-line LTE Tex for HV SO red and blue emission, SO column density, and SiO column density assuming a jet temperature of 100+-50 K; jet velocity deprojected with the disk geometry  
  > "The SiO total column density has been derived assuming a typical jet temperature of 100$\pm$50 K (cite: Podio2021)" (VLA 1623B: the SiO jet); "The velocities once deprojected using the geometry of the protostellar system (cite: Harris2018)" (SO and SiO jet emission)
   - assumption: LTE and optically thin emission  
  > "Assuming LTE conditions and optically thin emission" (VLA 1623B: the SiO jet)
   - assumption: Jet temperature 100+-50 K for SiO  
  > "assuming a typical jet temperature of 100$\pm$50 K (cite: Podio2021)" (VLA 1623B: the SiO jet)
   - fitting: _not stated_
   - validation: SiO velocity gradient compared with CO(2-1) jet of Santangelo et al. and with the perpendicular disk rotation traced by methanol and C18O  
  > "This is consistent with the CO(2–1) ALMA Band 6 images by (cite: Santangelo2015)" (SO and SiO jet emission)

## Software

- **CASA** 5.6.1-8: Calibration pipeline  
  > "within CASA 5.6.1-8 (cite: CASA2022)" (Observations)
- **GILDAS** : Data analysis  
  > "The data analysis was performed using the IRAM-GILDAS" (Observations)
- **CDMS** : Source of spectroscopic parameters of SO and SiO  
  > "retrieved from the CDMS database (cite: Muller2005)" (Table 1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SO excitation temperature of southern streamer | 33 | +-9 | K | 4 | a crude estimate of the SO excitation temperature ($T_{\rm ex}$) can be derived from the two SO observed lines: 33$\pm$9 K |
| SO excitation temperature at northern streamer impact on A circumbinary disk | 55 | +-12 | K | 4 | is higher than the value measured in the southern streamer, 55$\pm$12 K |
| SO excitation temperature where southern streamer impacts B disk | 63 | +-12 | K | 4 | the temperature is high, 63$\pm$12 K, and it can be explained again by a shock |
| SO column density of southern streamer | 2e14 | factor 2 higher if Tex = 20 K | cm^-2 | 5 | At a temperature of 33 K, the total SO column density is $N_{\rm SO}$ $\simeq$ 2 $\times$ 10$^{14}$ cm$^{-2}$. |
| C18O total column density in streamer | 4e15 | not stated | cm^-2 | 5 | The total column density of C$^{18}$O is 4 $\times$ 10$^{15}$ cm$^{-2}$. |
| H2 total column density in streamer | 2e22 | not stated | cm^-2 | 5 | the H$_2$ total column density is 2 $\times$ 10$^{22}$ cm$^{-2}$ |
| Total mass of blue-shifted southern streamer | 3e-3 | not stated | Msun | 5 | The total mass of the blue-shifted southern streamer is 3 $\times$ 10$^{-3}$ $M_{\rm \ensuremath{\odot}}$. |
| Streamer free-fall timescale | 6-9e3 | not stated | yr | 6 | we obtain, for the southern blue-shifted streamer, $t_{\rm ff}$ $\simeq$ 6–9 $\times$ 10$^{3}$ yr. |
| Free-fall velocity of streamer | 0.9-1.3 | not stated | km/s | 6 | the free-fall velocity lies in the range 0.9–1.3 km s$^{-1}$ |
| Streamer accretion rate onto B | 3-5e-7 | not stated | Msun/yr | 6 | we obtain an estimate of the accretion rate of the southern streamer onto the B protostar: 3–5 $\times$ 10$^{-7}$ $M_{\rm \ensuremath{\odot}}$ yr$^{-1}$. |
| Mass accretion rate of protostar B (M* = 1.7 Msun) | 1e-8 | highly uncertain | Msun/yr | 6 | we infer $\dot{M}_{\rm acc}$ = 10$^{-8}$ $M_{\rm \ensuremath{\odot}}$ yr$^{-1}$. |
| Mass accretion rate of B for M* = 0.25 and 0.05 Msun | up to 6e-8 and 3e-7 | not stated | Msun/yr | 6 | we obtain a mass accretion rate up to 6 $\times$ 10$^{-8}$ $M_{\rm \ensuremath{\odot}}$ yr$^{-1}$ (for 0.25 $M_{\rm \ensuremath{\odot}}$) and 3 $\times$ 10$^{-7}$ $M_{\rm \ensuremath{\odot}}$ yr$^{-1}$ (for 0.05 $M_{\rm \ensuremath{\odot}}$). |
| SO abundance relative to H2 in southern streamer | 1e-8 | not stated | dimensionless | 7 | $X_{\rm SO}$ $\simeq$ 10$^{-8}$ |
| Length of southern blue-shifted streamer | ~1500 | not stated | au | 3 | a long ($\sim$ 1500 au) southern streamer pointing to the central protostellar A+B system |
| Increase in mean velocity along southern streamer | ~1.6 | not stated | km/s | 3 | with an increase in the mean velocity of $\sim$ 1.6 km s$^{-1}$ approaching the central A+B system |
| HV SO excitation temperature, red-shifted emission | 92 | +-18 (Discussion); +-5 (Conclusions) | K | 8 | the excitation temperature of the HV SO ranges between 92$\pm$18 K (emission red-shifted by up to 8.2 km s$^{-1}$) |
| HV SO excitation temperature, blue-shifted emission | 102 | +-19 (Discussion); +-6 (Conclusions) | K | 8 | and 102$\pm$19 K (emission blue-shifted by up to 11.2 km s$^{-1}$) |
| HV SO column density | ~5e14 | not stated | cm^-2 | 8 | With these temperatures the SO column density is $\sim$ 5 $\times$ 10$^{14}$ cm$^{-2}$. |
| SiO total column density | 2-5e12 | not stated | cm^-2 | 8 | obtaining $N_{\rm SiO}$ = 2–5 $\times$ 10$^{12}$ cm$^{-2}$. |
| Deprojected jet velocity with respect to systemic | ~40 | not stated | km/s | 8 | reaches values $\sim$ 40 km s$^{-1}$ with respect to the systemic velocity |

## Qualitative findings

- SiO(5-4) detected for the first time in VLA1623, compact and associated with B  
  > "The SiO(5–4) line has been detected, for the first time, in the VLA1623 star forming region." (SO and SiO jet emission)
- SO profiles at B show an absorption dip near the systemic velocity, stronger in the lower-excitation SO(5_6-4_5) line  
  > "An absorption dip is observed at velocities close to the systemic one in the SO(5$_6$–4$_5$) line" (SO emission close to the A and B protostars)
- The elevated SO abundance in the streamer is tentatively attributed to mild accretion shocks  
  > "A possibility to explain an SO abundance larger than those typical in starless molecular clouds is to speculate the occurrence of mild shocks" (SO abundances in the southern VLA1623 B streamer)

## Claim tuples

- H: Extended SO emission reveals an accretion streamer feeding VLA1623 B | E: SO(5_6-4_5) and SO(6_6-5_5) LV maps, PV cuts and moment 1/2 maps compared with the CS outflow cavity | R: A ~1500 au blue-shifted southern structure with velocity increasing towards B, not associated with the red-shifted outflow cavity | F: An accelerating streamer plausibly feeds B | **supported**
- H: The excitation temperature of a streamer can be constrained from two SO lines | E: LTE optically thin ratio of SO(5_6-4_5) and SO(6_6-5_5) at the streamer peak | R: Tex = 33+-9 K, higher than the ~20 K toy-model value | F: First two-line Tex of an accreting streamer, with caveats on LTE and opacity | **partially**
- H: The mass infall rate of the streamer is comparable to the accretion rate of B | E: Streamer mass from C18O divided by free-fall time, versus Lbol-based Mdot of B | R: Streamer rate 3-5e-7 Msun/yr versus B accretion rate 1e-8 to 3e-7 Msun/yr depending on assumed mass | F: The streamer can supply a significant fraction of the accretion onto B | **partially**
- H: SiO and high-velocity SO trace the protostellar jet driven by B | E: HV SO and SiO(5-4) red/blue maps, Tex of HV SO, deprojected velocity | R: Compact (100-200 au) emission on B with SE-NW velocity gradient, Tex ~100 K | F: SiO and HV SO trace shocks from the jet from B | **supported**
- H: A northern N-S streamer falls onto the A circumbinary disk | E: LV SO maps and moment 2 map | R: ~2'' structure outside the cavity with broader line width at the outer circumbinary disk | F: Material plausibly falls onto the A circumbinary disk | **partially**

## Reasoning

- Why this data: Survey of SO and SiO in the cluster to find streamers and jets  
  > "we present a survey in SO and SiO of the VLA 1623–2417 protostellar cluster in order to reveal material associated with accretions streamers as well as protostellar jets." (Introduction)
- Why this method: LV velocity ranges chosen after inspecting the data to isolate one structure  
  > "they have been defined a posteriori after inspecting the SO dataset to identify velocity ranges tracing the same molecular structure" (Southern region: the VLA1623 B accretion streamer)
- Alternative: Outflow cavity as origin of the southern blue-shifted SO structure was rejected  
  > "the association with the outflow cavity is excluded from both the curved morphology" (Southern region: the VLA1623 B accretion streamer)
- Alternative: Hot-corino origin (thermal evaporation) of streamer SO excluded from the derived Tex  
  > "the hot-corino nature, i.e. the thermal evaporation of the dust mantle in the streamer, is here excluded (assuming LTE conditions)" (SO abundances in the southern VLA1623 B streamer)
- Alternative: Strong shocks (>=10 km/s) excluded as origin of the streamer SO abundance  
  > "Even the occurrence of strong shocks ($V_{\rm shocks}$ $\geq$ 10 km s$^{-1}$) has to be excluded" (SO abundances in the southern VLA1623 B streamer)
- How they decided it was enough: _not stated_
- Limitation (authors): Tex from two SO lines under LTE and optically thin assumptions; more lines needed  
  > "more lines need to be observed to investigate the reliability of the LTE assumption, as well as possible line opacity effects" (Excitation temperature of the VLA1623 B accretion streamer)
- Limitation (authors): Mass accretion rate of B is highly uncertain  
  > "The estimated mass accretion rate is highly uncertain because it depends strongly on the protostellar properties" (Accretion and infalling rates)
- Limitation (authors): SO emission from the hot-corino in A cannot be assessed because of absorption  
  > "the contribution of the SO emission by the hot-corino in A cannot be assessed using the observed lines" (SO emission close to the A and B protostars)
- Limitation (authors): Streamer length not fully traced because it exceeds the field of view  
  > "which looks not fully traced because it is larger than the FoV of the interferometric (IRAM-NOEMA, ALMA) images" (Conclusions)
- Caveat (inferred, ours): Streamer mass and accretion rate rest on C18O taken from another paper with a CO/H2 and 16O/18O fixed at standard values; no uncertainty on the mass is given.
- Caveat (inferred, ours): Tex rests on two SO lines at one position with LTE and thin assumptions, while SO shows self-absorption near Vsys elsewhere.
- Caveat (inferred, ours): The B accretion rate depends on Lbol, R* and M*, spanning a factor of ~30, so 'comparable' to the streamer rate is weakly constrained.
- Caveat (inferred, ours): Streamer length is 1500 au in the Results and ~2000 au in the abstract and conclusions; HV SO Tex uncertainties differ between Discussion (+-18, +-19) and Conclusions (+-5, +-6).
- Caveat (inferred, ours): The LV velocity windows were chosen a posteriori, and a blue-shifted streamer on the red-shifted side requires an assumed back-side geometry.

## Reproducibility

- Data public (paper): Raw data available in the ALMA archive after the proprietary period  
  > "The raw data are available on the ALMA archive at the end of the proprietary period (ADS/JAO.ALMA#2018.1.01205.L)." (DATA AVAILABILITY)
- Products in archive: _not stated_
- Code: Calibration/line-imaging pipeline referenced at a public GitHub repository (autocorr/faust_line_imaging)  
  > "https://github.com/autocorr/faust" (footnote 3)
- Missing: Cleaning parameters, masks and line-free channels for the FAUST cubes.
- Missing: Spectrum extraction aperture, integration windows and constants for the LTE Tex and column densities.
- Missing: The C18O(2-1) cube from Mercimek et al. and the exact emitting area used for the streamer mass.
- Missing: In-preparation pipeline papers (Chandler et al.; Moellenbrock et al.) for the calibration details.
- Data volume (inferred): ~100-300 GB raw for the three arrays and two setups of the field; a few GB of cubes
- Score (inferred): 3/5, Data are public through the archive and the pipeline repository exists, with numeric results, but imaging settings, extraction apertures and the C18O input are not given.
- Rediscovery candidate: no, Data will be public and results are numeric, but key imaging choices, spectrum extraction and the C18O cube from another paper are not specified well enough to redo the Tex and mass estimates.

## Links

- Method: Chandler et al. (in preparation) (FAUST calibration/line-imaging pipeline)
- Method: Moellenbrock et al. (in preparation) (Tsys and spectral normalization correction)
- Method: (cite: Codella2021) (FAUST Large Program description)
- Companion: (cite: Ohashi2022) (FAUST CS, CCH, H13CO+ study of VLA1623; Vsys, CS map, disk dynamical mass)
- Companion: (cite: Codella2022) (FAUST methanol and methyl formate in VLA1623)
- Companion: (cite: Mercimek2023) (FAUST C18O(2-1) data and source W)
- Companion: (cite: Hsieh2020) (Earlier SO(8_8-7_7) streamers in VLA1623)
- Related: FAUST ALMA Large Program (2018.1.01205.L)

## Checks

```json
{
 "quotes": 129,
 "quotes_ok": 129,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 20,
 "numeric_problems": 0,
 "fill": {
  "facts": 112,
  "stated": 88,
  "rate": 0.786
 },
 "evidence_ok": true
}
```

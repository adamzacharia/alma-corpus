# Reconciling 3D Models for the Central 10 pc of the Milky Way

`2026ApJ..1001..184M` | The Astrophysical Journal 2026 | first author: Mills, Elisabeth A. C. | arXiv: 2603.02211 | DOI: 10.3847/1538-4357/ae4d3a

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type multi_facility_alma_minor

## Science

- Fields: milky_way_ism, astrochemistry
- Question: Where along the line of sight do the 50 and 20 km/s clouds, Sgr A East and the CND lie relative to Sgr A*; build a 3D model of the central 10 pc consistent with radio observations and CMZ orbital kinematics  
  > "The construction of an accurate 3D model of the Milky Way center is necessary to understand inflow processes that drive its overall evolution" (abstract); "This paper seeks to resolve the tension between models of the central 10 parsecs and the entire CMZ by presenting an alternative model of the inner 10 parsecs" (2.3 Tensions between models and observations)
- Target **Sgr A* (ALMA Band 3 12CO pointing)**: coordinates alpha = 17h45m40s, delta = -29deg00'28'' (pointing center)  
  > "centered at $\alpha=17^h45^m40^s$, $\delta=-29\ensuremath{^\circ}00'28''$" (3.2.1 Band 3 CO pointing toward Sgr A*); "at the assumed Galactocentric distance of 8.3 kpc (cite: Gravity21)" (3.1.1 VLA observations); z/distance 8.3 kpc (assumed Galactocentric distance)  
  > "centered at $\alpha=17^h45^m40^s$, $\delta=-29\ensuremath{^\circ}00'28''$" (3.2.1 Band 3 CO pointing toward Sgr A*); "at the assumed Galactocentric distance of 8.3 kpc (cite: Gravity21)" (3.1.1 VLA observations); distance from (cite: Gravity21)  
  > "centered at $\alpha=17^h45^m40^s$, $\delta=-29\ensuremath{^\circ}00'28''$" (3.2.1 Band 3 CO pointing toward Sgr A*); "at the assumed Galactocentric distance of 8.3 kpc (cite: Gravity21)" (3.1.1 VLA observations)
- Target **CND mosaic (ALMA Band 3 and Band 6)**: coordinates _not stated_; z/distance 8.3 kpc  
  > "The Band 3 observations analyzed here consist of an 11-pointing mosaic covering a $75''\times100''$ (3$\times$4 pc) field of view." (3.2.2 Band 3 and 6 CND Mosaic); "Our edge-on view of the Milky Way Galaxy can cause components to appear to align along the 8.3 kpc (cite: Gravity19; Gravity21) line of sight to the center." (1 Introduction); distance from (cite: Gravity19; Gravity21)  
  > "The Band 3 observations analyzed here consist of an 11-pointing mosaic covering a $75''\times100''$ (3$\times$4 pc) field of view." (3.2.2 Band 3 and 6 CND Mosaic); "Our edge-on view of the Milky Way Galaxy can cause components to appear to align along the 8.3 kpc (cite: Gravity19; Gravity21) line of sight to the center." (1 Introduction)
- Target **50 and 20 km/s clouds (GCM-0.02-0.07 and GCM-0.13-0.08), VLA/GBT NH3**: coordinates not stated (Galactic-coordinate names only)  
  > "In this paper we focus on GCM-0.02-0.07 and GCM-0.13-0.08" (3.1.1 VLA observations); z/distance 8.3 kpc (assumed Galactocentric distance)  
  > "In this paper we focus on GCM-0.02-0.07 and GCM-0.13-0.08" (3.1.1 VLA observations); distance from (cite: Gravity21)  
  > "In this paper we focus on GCM-0.02-0.07 and GCM-0.13-0.08" (3.1.1 VLA observations)

## Data provenance

- ALMA projects: 2019.1.01240.S, 2013.1.00857.S
- bands: Band 3 (3 mm) for 2019.1.01240.S; Band 3 and Band 6 for 2013.1.00857.S  
  > "The observations were made using two frequency settings, both at 3 mm (ALMA Band 3), over a total of eight spectral windows." (3.2.1 Band 3 CO pointing toward Sgr A*); "which made observations towards the CND in both Band 3 and Band 6" (3.2.2 Band 3 and 6 CND Mosaic)
- frequencies and spectral setup: 2019.1.01240.S: 8 spws (5 narrow, 234 MHz wide, 141 kHz resolution, CO isotopologues + H40alpha; 3 continuum, 1875 MHz wide). 2013.1.00857.S Band 3: 4 spws at 90.7, 92.6, 102.75, 104.6 GHz. Band 6: 8 spws at 252.55-273.5 GHz  
  > "Five of these had bandwidths of 234 MHz ($\sim$640 km s$^{-1}$) and resolutions of 141 kHz (0.37 km s$^{-1}$)" (3.2.1 Band 3 CO pointing toward Sgr A*); "Observations were made in a single frequency setting covering four spectral windows centered at 90.7 GHz, 92.6 GHz, 102.75 GHz, and 104.6 GHz." (3.2.2 Band 3 and 6 CND Mosaic); "Observations were made at two frequency settings, covering eight spectral windows centered at 252.55 GHz, 254.72 GHz, 256.7 GHz, 258.7 GHz, 266.72 GHz, 269.70 GHz, 271.5 GHz, and 273.5 GHz." (3.2.2 Band 3 and 6 CND Mosaic)
- continuum bandwidth: 2019.1.01240.S: three continuum spws of 1875 MHz each; 2013.1.00857.S: all spws 1.875 GHz bandwidth  
  > "while the remaining three had bandwidths of 1875 MHz" (3.2.1 Band 3 CO pointing toward Sgr A*); "All spectral windows were configured with bandwidths of 1.875 GHz and channel widths of 1.13 MHz" (3.2.2 Band 3 and 6 CND Mosaic)
- arrays: 2019.1.01240.S: 12m array (average 45 antennas); 2013.1.00857.S: 12m array combined with 7m array (ACA) and total power  
  > "The observations were completed over eight sessions, with an average of 45 antennas" (3.2.1 Band 3 CO pointing toward Sgr A*); "The 12m observations were combined with observations from the 7m array (ALMA Compact Array) and total power dishes in order to recover emission at all spatial scales." (3.2.2 Band 3 and 6 CND Mosaic)
- configurations: 2019.1.01240.S: C43-2, baselines 15-697 m. 2013.1.00857.S Band 3: C34-2/1 (14-348 m) and C34-4/5 (17-783 m); Band 6: C34-1 (14-327 m)  
  > "The observations were made in the C43-2 configuration, with baselines ranging between 15 and 697 m." (3.2.1 Band 3 CO pointing toward Sgr A*); "C34-2/1 with minimum baselines of 14m and maximum baselines of 348 m and C34-4/5 with minimum baselines of 17 m and maximum baselines of 783 m" (3.2.2 Band 3 and 6 CND Mosaic); "C34-1, with minimum baselines of 14 m and maximum baselines of 327 m" (3.2.2 Band 3 and 6 CND Mosaic)
- baselines: _not stated_
- angular resolution: 12CO 1-0 cube beam 2.4'' x 1.4'' (0.09 x 0.06 pc); CND mosaic lines 0.88-1.95'' (Table 1)  
  > "The imaged cube for this line has 0.28$''$ pixels (0.011 pc) and a beam size of $2.4'' \times 1.4''$ or $0.09 \times 0.06$ pc." (3.2.1 Band 3 CO pointing toward Sgr A*); "HC$_3$N | $10-9$ | 24.0 | $1.2\times10^6$ | 90.97902 | 1.95 $\times$ 1.39 | 3.4 | 0.23" (Table 1)
- max recoverable scale: 21'' (0.84 pc) for the Band 3 12CO pointing  
  > "It is sensitive to emission on size scales up to 21$''$ (0.84 pc)." (3.2.1 Band 3 CO pointing toward Sgr A*)
- sensitivity: 12CO cube per-channel noise 13.3 mJy/beam (0.395 K); CND mosaic per-channel line sensitivity 0.10-0.27 K (Table 1)  
  > "The per-channel noise in this cube is 13.3 mJy/beam (0.395 K)." (3.2.1 Band 3 CO pointing toward Sgr A*); "SO | $6_6-5_5$ | 56.5 | $3.8\times10^6$ | 258.25583 | 1.42 $\times$ 0.97 | 1.2 | 0.10" (Table 1)
- time on source: _not stated_
- observing dates: 2019.1.01240.S: 2019 Oct 31 - Nov 24 (eight sessions); 2013.1.00857.S: Band 3 on 2014 Jul 21 and Dec 6; Band 6 on 2015 Apr 6  
  > "between 2019 October 31 and November 24" (3.2.1 Band 3 CO pointing toward Sgr A*); "Observations were conducted on July 21, 2014 and December 6, 2014." (3.2.2 Band 3 and 6 CND Mosaic); "Observations were conducted on April 6, 2015." (3.2.2 Band 3 and 6 CND Mosaic)
- pi or archival as stated: Both projects have PI E.A.C. Mills (first author); not described as archival  
  > "(Project code 2019.1.01240.S; PI: E.A.C. Mills)" (3.2.1 Band 3 CO pointing toward Sgr A*); "(project code 2013.1.00857.S; PI: E.A.C. Mills)" (3.2.2 Band 3 and 6 CND Mosaic)
- Line: 12CO J=1-0 (115.2712018 GHz)
- Line: H40alpha recombination line and other CO isotopologues not stated (not stated)
- Line: HC3N 10-9 (90.97902 GHz)
- Line: N2H+ 1-0 (93.17340 GHz)
- Line: SO 6_6-5_5 (258.25583 GHz)
- Line: H13CN 3-2 (259.01179 GHz)
- Line: CH3OH 5_2,3-4_1,3 (266.83813 GHz)
- Line: HNC 3-2 (271.98111 GHz)
- Line: NH3 (VLA/GBT, not ALMA) (3,3) (23.87013 GHz)
- Other facility **VLA (K band, WIDAR; hybrid DnC)**: Seven-pointing NH3 mosaic of the 50 and 20 km/s clouds and CND, ~3'' resolution  
  > "All three clouds were observed as part of a seven-pointing mosaic covering an area of 4.5$'$ by 9$'$ (11$\times$22 pc)" (3.1.1 VLA observations); "The data were taken in the hybrid DnC array configuration of the VLA" (3.1.1 VLA observations)
- Other facility **GBT (K-band Focal Plane Array, VEGAS)**: Single-dish NH3 mosaic combined with VLA to recover extended structure  
  > "The GBT data consist of a dual-polarization on-the-fly mosaic using four beams of the K-band Focal Plane Array" (3.1.2 GBT observations); "The (1,1) through (6,6) NH$_{3}$  lines were observed simultaneously with the VEGAS spectrometer" (3.1.2 GBT observations)
- Other facility **MeerKAT (literature)**: 20 cm spectral-index map used as supporting evidence (Figure 14 of Heywood22)  
  > "A spatially-extended region of positive spectral index can also be seen toward the minispiral in MeerKat images, e.g. Figure 14 of (cite: Heywood22)." (5.3 Revisiting Radio Absorption Measurements)
- External data: 1720 MHz OH maser positions and velocities overlaid on the NH3 peak-velocity map  
  > "we also overlay the 1720 MHz OH masers from (cite: Sjouwerman08)" (4.1 A New NH3 map of the central 10 parsecs) [from (cite: Sjouwerman08)]
- External data: Galactocentric distance 8.3 kpc  
  > "at the assumed Galactocentric distance of 8.3 kpc (cite: Gravity21)" (3.1.1 VLA observations) [from (cite: Gravity21)]
- External data: Initial mass function slope and young-cluster mass range used for supernova rate  
  > "Following (cite: Lu13), we assume an initial mass function with a slope of 1.7" (5.3 Revisiting Radio Absorption Measurements) [from (cite: Lu13)]
- External data: Magnetic field strengths and synchrotron lifetimes  
  > "Field strengths of 1-5 mG observed toward the central parsec (cite: Killeen92; Plante95; Guerra23) correspond to a synchrotron lifetime of 10,000 - 100,000 years (cite: Condon92)." (5.3 Revisiting Radio Absorption Measurements) [from (cite: Killeen92; Plante95; Guerra23); (cite: Condon92)]
- External data: Cloud areas, masses, densities and column densities of the 50 and 20 km/s clouds  
  > "From the analysis presented in (cite: Battersby25b), the 50 km/s cloud is physically smaller than the 20 km/s cloud" (5.5.3 Molecular Cloud Lifetimes in the CMZ) [from (cite: Battersby25b)]
- External data: CMZ orbital models and cloud distances (Table of models)  
  > "Open Stream | rosette | 100-200 | 50-100 | $\sim$ 50 (in front) | (cite: Kruijssen15)" (Table 2) [from (cite: Sofue95; Sofue25; Molinari11; Walker25; Kruijssen15); Lipman et al. (submitted)]
- External data: 90 cm continuum image of Sgr A (source of the image not stated in the text)  
  > "we place three representative apertures (the size of the 90 cm beam) on the 90 cm image" (5.3 Revisiting Radio Absorption Measurements) [from not stated]
- Simulation/model as data: pySTARBURST99 population-synthesis model used for the nuclear-cluster supernova rate  
  > "by using pySTARBURST99 (cite: Hawcroft25) to estimate the average supernova rate for the young nuclear cluster" (5.3 Revisiting Radio Absorption Measurements)

## Processing

### Calibration

- pipeline or manual: 2019.1.01240.S: ALMA pipeline; 2013.1.00857.S: manual calibration by the North American ALMA Science Center  
  > "The calibration of the data was performed in the Common Astronomy Software Applications package (CASA versions 5.6.1–8) with the ALMA pipeline." (3.2.1 Band 3 CO pointing toward Sgr A*); "The data were calibrated manually by North American Science Center." (3.2.2 Band 3 and 6 CND Mosaic)
- casa version: CASA 5.6.1-8 (2019.1.01240.S)  
  > "(CASA versions 5.6.1–8)" (3.2.1 Band 3 CO pointing toward Sgr A*)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean for line and continuum (2019.1.01240.S); CASA joint imaging of 7m and 12m data for 2013.1.00857.S  
  > "The imaging of both line and continuum emission was performed in CASA, using the `tclean` task" (3.2.1 Band 3 CO pointing toward Sgr A*); "The 7m and 12m data were then jointly imaged using CASA" (3.2.2 Band 3 and 6 CND Mosaic)
- deconvolver: _not stated_
- weighting robust: robust = 1.0  
  > "with a robust weighting of 1.0, so that the observations were sensitive to a combination of both point source emission and extended emission" (3.2.1 Band 3 CO pointing toward Sgr A*)
- uv taper: _not stated_
- cell size: 0.28'' pixels (0.011 pc) for the 12CO cube  
  > "The imaged cube for this line has 0.28$''$ pixels (0.011 pc)" (3.2.1 Band 3 CO pointing toward Sgr A*)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12m + 7m jointly imaged in CASA, then feathered with total power (2013.1.00857.S)  
  > "The 7m and 12m data were then jointly imaged using CASA, and the images were then feathered with the total power data." (3.2.2 Band 3 and 6 CND Mosaic)
- smoothing: _not stated_
- final beam: 12CO 1-0: 2.4'' x 1.4'' (0.09 x 0.06 pc); NH3 (3,3) VLA+GBT: 2.9'' x 3.7''  
  > "a beam size of $2.4'' \times 1.4''$ or $0.09 \times 0.06$ pc" (3.2.1 Band 3 CO pointing toward Sgr A*); "The resulting NH$_{3}$(3,3) image has a beam size of $2.9''\times3.7''$" (3.1.2 GBT observations)
- final rms: 12CO 1-0: 13.3 mJy/beam (0.395 K) per channel; NH3 (3,3): 1.3 mJy/beam (0.26 K) per channel  
  > "The per-channel noise in this cube is 13.3 mJy/beam (0.395 K)." (3.2.1 Band 3 CO pointing toward Sgr A*); "a per-channel noise of 1.3 mJy/beam (0.26 K)" (3.1.2 GBT observations)

### Inherited from earlier work

- VLA NH3 calibration  
  > "The calibration of these data is the same as described in (cite: Mills15), and additional details of this procedure can be found there." (3.1.1 VLA observations) [from (cite: Mills15)]
- VLA survey observations described in separate papers  
  > "These observations are described further in separate papers (cite: Mills15; Ludovici16; Butterfield18; Mills18b; Butterfield22)." (3.1.1 VLA observations) [from (cite: Mills15; Ludovici16; Butterfield18; Mills18b; Butterfield22)]
- GBT NH3 data calibration  
  > "additional details of the data calibration can be found there" (3.1.2 GBT observations) [from (cite: Minh13)]
- GBT+VLA combination procedure  
  > "Combination of the GBT and VLA data was performed using a procedure that is similar to that used in (cite: Liu13) (see their Appendix A)" (3.1.2 GBT observations) [from (cite: Liu13), Appendix A]
- IMF slope and cluster mass for the supernova-rate estimate  
  > "Following (cite: Lu13), we assume an initial mass function with a slope of 1.7" (5.3 Revisiting Radio Absorption Measurements) [from (cite: Lu13)]

### Not stated but needed to reproduce (our reading)

- ALMA flux calibrator and flux-scale uncertainty for either project
- ALMA pipeline version and whether archive products were used as is; pipeline vs manual for each execution block
- Whether any self-calibration was done
- tclean parameters other than robust = 1.0: deconvolver, niter/threshold, masks, image size, uv-taper, and the spectral channelization of the 12CO cube (stated only as 141 kHz native resolution)
- Continuum subtraction method and line-free channels for the CND mosaic line cubes
- Total-power data processing and feather parameters (scaling, uv cut) for 2013.1.00857.S, and the 7m/12m weights used in joint imaging
- Method for the 12CO absorption spectrum: aperture or pixel used, continuum level, baseline treatment, any optical-depth conversion
- Exact calibration (flagging, flux scale) of the VLA data (only referred to Mills15) and of the GBT data (Minh13)
- Source, frequency and resolution of the 90 cm image, and the exact aperture positions and sizes
- PV slit width and averaging, and how velocity gradients were measured from the PV diagram
- Units of the supernova rate (stated without units)
- How moment-0, peak-intensity and peak-velocity maps were made (velocity ranges, clipping)

## Analysis recipe

1. **Calibrate and image ALMA data**: ALMA pipeline calibration (2019.1.01240.S) and manual calibration (2013.1.00857.S); tclean imaging with robust 1.0; 7m+12m joint imaging feathered with total power for 2013.1.00857.S  
  > "The imaging of both line and continuum emission was performed in CASA, using the `tclean` task, with a robust weighting of 1.0" (3.2.1 Band 3 CO pointing toward Sgr A*); "The 7m and 12m data were then jointly imaged using CASA, and the images were then feathered with the total power data." (3.2.2 Band 3 and 6 CND Mosaic)
   - software: CASA, tclean, ALMA pipeline
   - parameter: robust = 1.0  
  > "with a robust weighting of 1.0" (3.2.1 Band 3 CO pointing toward Sgr A*)
   - fitting: _not stated_
   - validation: _not stated_
2. **Combine VLA and GBT NH3 data**: Miriad-based combination: GBT cubes smoothed and regridded, deconvolved, converted to visibilities and jointly imaged with VLA; final linear combination of joint and GBT cubes with immerge  
  > "We then jointly imaged the GBT and VLA visibilities using the Miriad-`invert` and `mossdi` tasks." (3.1.2 GBT observations); "we used the Miriad-`immerge` task to linearly combine the GBT+VLA joint image cubes we produced and the spectrally smoothed and regridded GBT image cubes" (3.1.2 GBT observations)
   - software: Miriad, ALMICA, CASA feather
   - parameter: relative VLA/GBT weights set manually by resetting system temperature columns  
  > "the relative weights between the GBT and VLA visibilities were manually optimized by artificially resetting the system temperature columns" (3.1.2 GBT observations)
   - fitting: _not stated_
   - validation: Residual systematic intensity errors <~1% stated to be negligible compared with thermal noise  
  > "which is negligible as compared to the thermal noises in our present study" (3.1.2 GBT observations)
3. **Map NH3 (3,3) velocity structure and build PV diagram**: Integrated intensity map, brightest-pixel velocity map and a PV slice parallel to the Galactic plane from the NH3 (3,3) cube; velocity gradients read from the PV diagram and compared to features of the Herrnstein05 model  
  > "The right panel of Figure [3](#fig:Fig-velocity) shows the velocity that corresponds to the brightest pixel in the cube at each position." (4.1 A New NH3 map of the central 10 parsecs); "The slit runs parallel to the Galactic plane." (4.1 A New NH3 map of the central 10 parsecs)
   - assumption: Distance 8.3 kpc  
  > "at the assumed Galactocentric distance of 8.3 kpc (cite: Gravity21)" (3.1.1 VLA observations)
   - fitting: _not stated_
   - validation: Gradients compared with Henshaw16 values  
  > "consistent with measurements by (cite: Henshaw16)" (4.1 A New NH3 map of the central 10 parsecs)
4. **Map ALMA molecular lines of the CND region**: Integrated intensity, peak intensity and peak-velocity maps of six lines from the Band 3/6 mosaics, compared qualitatively between CND and surrounding gas  
  > "we show the peak intensities (the brightest pixel in the cube at each position) from all of the lines" (4.2 Chemistry of the CND and surrounding gas)
   - software: CASA
   - assumption: Critical densities given at a temperature of 60 K  
  > "At a temperature of 60 K" (Footnote 4)
   - fitting: _not stated_
   - validation: Chemical differentiation compared with Martin12 and not attributed to excitation alone because CH3OH and SO have similar upper level energies  
  > "as the observed transitions of CH$_3$OH and SO have similar upper level energies $E_{upper}$" (4.2 Chemistry of the CND and surrounding gas)
5. **Measure 12CO absorption toward Sgr A***: 12CO J=1-0 spectrum toward the unresolved Sgr A* point source; narrow (FWHM ~1-2 km/s) absorption features identified on a broad trough and compared with channel maps  
  > "toward the unresolved bright (90 K / 3.3 Jy at 115 GHz) point source Sgr A\*" (4.3 CO absorption toward Sgr A*); "absorption features superposed on the broader absorption trough" (4.3 CO absorption toward Sgr A*)
   - software: CASA
   - assumption: Absorption only arises from gas in front of Sgr A*; gas behind Sgr A* is not seen  
  > "Gas behind Sgr A\* (in the back half of the CMZ) will not be present in absorption in this spectrum." (4.3 CO absorption toward Sgr A*)
   - assumption: Narrow linewidths (1-2 km/s) vs CND clump widths (11-55 km/s) used to assign features to the 50 and 20 km/s clouds rather than the CND  
  > "Ultimately, based on their linewidth and velocity, we then identify these four absorption features as being associated with the 50 and 20 km/s clouds" (4.3 CO absorption toward Sgr A*)
   - fitting: _not stated_
   - validation: Compared with a saturated -5 km/s feature and an 87 km/s feature in channel maps  
  > "We also compare these features to two other features in the spectra" (4.3 CO absorption toward Sgr A*)
6. **Measure 90 cm intensities toward Sgr A East and the minispiral**: Mean intensity in three beam-sized apertures on a 90 cm image: Sgr A East interior, minispiral, and west of both  
  > "we place three representative apertures (the size of the 90 cm beam) on the 90 cm image" (5.3 Revisiting Radio Absorption Measurements)
   - assumption: Bright northeast edge of Sgr A East is not representative of the shell brightness where it overlaps Sgr A West  
  > "Assuming that the bright edge emission observed in the northeast part of Sgr A East is not representative of the brightness of the shell where it overlaps with Sgr A West" (5.3 Revisiting Radio Absorption Measurements)
   - fitting: _not stated_
   - validation: Compared with 6 cm emission at higher resolution and MeerKAT spectral index map  
  > "our comparison of these apertures with 6 cm emission (from an image with much higher spatial resolution) shows this is unlikely to be the case" (5.3 Revisiting Radio Absorption Measurements)
7. **Estimate nuclear-cluster supernova rate and synchrotron sustainability**: pySTARBURST99 average supernova rate between 3 and 5.8 Myr for the young cluster, converted to mean time between supernovae and compared with synchrotron lifetimes  
  > "by using pySTARBURST99 (cite: Hawcroft25) to estimate the average supernova rate for the young nuclear cluster" (5.3 Revisiting Radio Absorption Measurements); "This corresponds to an average time between supernovae of 11,000-30,000 years" (5.3 Revisiting Radio Absorption Measurements)
   - software: pySTARBURST99
   - parameter: IMF slope 1.7; cluster mass above 1 Msun 14,000-37,000 Msun; Z = 0.02; upper mass 120 Msun  
  > "Following (cite: Lu13), we assume an initial mass function with a slope of 1.7" (5.3 Revisiting Radio Absorption Measurements); "We also adopt a Galactic center metallicity of $Z=0.02$" (5.3 Revisiting Radio Absorption Measurements)
   - assumption: Magnetic field 1-5 mG gives synchrotron lifetime 10,000-100,000 years  
  > "Field strengths of 1-5 mG observed toward the central parsec (cite: Killeen92; Plante95; Guerra23) correspond to a synchrotron lifetime of 10,000 - 100,000 years (cite: Condon92)." (5.3 Revisiting Radio Absorption Measurements)
   - fitting: _not stated_
   - validation: _not stated_
8. **Compare kinematics with CMZ orbital models and construct the alternative 3D model**: Compare observed velocity gradients of the clouds and CND with those required by the Kruijssen15 orbit and other models; combine with absorption evidence to place structures in two groups along the line of sight  
  > "Assuming the potential adopted by (cite: Kruijssen15) is broadly correct for the inner 10 parsecs" (5.2 Revisiting Orbital Constraints); "Our main goal with this model is not to provide an exact placement of all of the structures in three dimensions relative to Sgr A\*" (5.5 An Updated Model of the Inner 10 Parsecs)
   - assumption: Potential of Kruijssen15 broadly correct for inner 10 pc  
  > "Assuming the potential adopted by (cite: Kruijssen15) is broadly correct for the inner 10 parsecs" (5.2 Revisiting Orbital Constraints)
   - fitting: _not stated_
   - validation: Consistency with prior radio constraints and CMZ orbital fits  
  > "we are able to create a model of the central 10 pc that is consistent with the existing observational constraints of this region" (6 Conclusions)

## Software

- **CASA** 5.6.1-8: ALMA calibration and imaging (tclean), 7m+12m joint imaging, feathering with total power  
  > "The calibration of the data was performed in the Common Astronomy Software Applications package (CASA versions 5.6.1–8) with the ALMA pipeline." (3.2.1 Band 3 CO pointing toward Sgr A*); "The 7m and 12m data were then jointly imaged using CASA" (3.2.2 Band 3 and 6 CND Mosaic)
- **tclean** : Line and continuum imaging of 2019.1.01240.S  
  > "using the `tclean` task, with a robust weighting of 1.0" (3.2.1 Band 3 CO pointing toward Sgr A*)
- **ALMA pipeline** : Calibration of 2019.1.01240.S  
  > "(CASA versions 5.6.1–8) with the ALMA pipeline" (3.2.1 Band 3 CO pointing toward Sgr A*)
- **Miriad** : GBT+VLA NH3 combination (clean, demos, uvrandom, uvmodel, invert, mossdi, immerge)  
  > "The procedure was based on the Miriad software package, which has now been re-organized as a comprehensive tool, ALMICA" (3.1.2 GBT observations); "we used the Miriad-`uvrandom` and `uvmodel` tasks to convert the deconvolved and VLA-primary-beam attenuated GBT image cubes to visibilities" (3.1.2 GBT observations)
- **ALMICA** : Comprehensive tool reorganizing the Miriad-based combination procedure  
  > "which has now been re-organized as a comprehensive tool, ALMICA" (3.1.2 GBT observations)
- **pySTARBURST99** : Average supernova rate of the young nuclear cluster  
  > "by using pySTARBURST99 (cite: Hawcroft25) to estimate the average supernova rate for the young nuclear cluster" (5.3 Revisiting Radio Absorption Measurements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 12CO cube per-channel noise (ALMA Band 3) | 13.3 mJy/beam (0.395 K) | not stated | mJy/beam | 1 | The per-channel noise in this cube is 13.3 mJy/beam (0.395 K). |
| 12CO cube maximum recoverable scale | 21'' (0.84 pc) | not stated | arcsec | 1 | It is sensitive to emission on size scales up to 21$''$ (0.84 pc). |
| NH3 (3,3) per-channel noise (VLA+GBT) | 1.3 mJy/beam (0.26 K) | not stated | mJy/beam | 2 | a per-channel noise of 1.3 mJy/beam (0.26 K) |
| Velocity gradient connecting 50 and 20 km/s clouds | 2.5 | not stated | km/s/pc | 3 | we see a smooth and continuous velocity structure connecting the 20 and 50 km/s clouds, with an average velocity gradient of 2.5 km s$^{-1}$ pc$^{-1}$ |
| Maximum velocity gradient of the Molecular Ridge | 5 | not stated | km/s/pc | 3 | the connecting ‘Molecular Ridge’ has a maximum velocity gradient of 5 km s$^{-1}$ pc$^{-1}$ |
| CND velocity gradient (PV diagram) | 150 | not stated | km/s/pc | 3 | In contrast, the CND has a velocity gradient of 150 km s$^{-1}$ pc$^{-1}$. |
| Sgr A* brightness at 115 GHz | 90 K / 3.3 Jy | not stated | K / Jy | 5 | toward the unresolved bright (90 K / 3.3 Jy at 115 GHz) point source Sgr A\* |
| Velocity range of 12CO absorption components in front of Sgr A* | -200 to 63 | not stated | km/s | 5 | shows dozens of velocity components ranging from -200 km/s to 63 km/s that lie in front of Sgr A\* |
| Narrow absorption features in 50/20 km/s cloud velocity range (32, 43, 50, 63 km/s), FWHM | 4 features; FWHM ~1-2 | not stated | km/s | 5 | We identify 4 narrow (FWHM $\sim 1-2$ km/s) absorption features superposed on the broader absorption trough |
| 90 cm mean intensity, Aperture 1 (Sgr A East interior) | 6.13 | not stated | Jy | 6 | For Aperture 1, we measure a mean intensity of 6.13 Jy. |
| 90 cm mean intensity, Aperture 2 (minispiral) | 3.27 | not stated | Jy | 6 | For Aperture 2, we measure a mean intensity of 3.27 Jy. |
| 90 cm mean intensity, Aperture 3 (west of Sgr A East and minispiral) | 3.44 | not stated | Jy | 6 | For Aperture 3, we measure a mean intensity of 3.44 Jy. |
| Average time between supernovae | 11,000-30,000 | not stated | years | 7 | This corresponds to an average time between supernovae of 11,000-30,000 years |
| Observed velocity change of the 50/20 km/s clouds over 10 pc | 33 | not stated | km/s | 8 | The observed velocity change of the clouds over the same distance is 33 km/s |
| Line-of-sight distance of 20 km/s cloud, 50 km/s cloud and Sgr A East in front of Sgr A* | more than 10 | lower limit | pc | 8 | Our model places the 20 km/s cloud, 50 km/s cloud, and Sgr A East more than 10 pc in front of Sgr A\*. |

## Qualitative findings

- The Northern Ridge, Western Streamer and Southern Streamer do not link the 50 and 20 km/s clouds to the CND in position-velocity space  
  > "The 50 km/s cloud is not feeding the CND through this feature." (4.1 A New NH3 map of the central 10 parsecs)
- ALMA lines show chemical differentiation: H13CN and SO strongest in the inner CND; CH3OH, HC3N and N2H+ strongest in the Southern Streamer and 50/20 km/s cloud gas  
  > "the strongest emission from the inner CND is seen in H$^{13}$CN (3-2) and SO ($6_5-5_5$)" (4.2 Chemistry of the CND and surrounding gas)
- The 80 km/s cloud lies at a velocity distinct from CND gas and appears subject to a weaker radiation field  
  > "indicates the 80 km/s cloud is clearly subject to a less intense radiation field than the CND" (4.2 Chemistry of the CND and surrounding gas)

## Claim tuples

- H: Are the 50 and 20 km/s clouds kinematically connected to the CND? | E: VLA+GBT NH3 (3,3) map and PV diagram compared with features of the Herrnstein05 model | R: Velocities of the proposed connecting features are discontinuous with the CND; the clouds show a shallow ~2.5 km/s/pc gradient versus 150 km/s/pc for the CND | F: No evidence for a connection between the CND and the 50 or 20 km/s clouds | **supported**
- H: Is the molecular gas of the CND chemically distinct from the 50/20 km/s cloud gas and Southern Streamer? | E: Maps of six ALMA lines (HC3N, N2H+, SO, H13CN, CH3OH, HNC) over the CND mosaic | R: H13CN and SO bright in the CND; CH3OH, HC3N and N2H+ faint in the CND and bright in surrounding cloud gas | F: Clear chemical difference between inner CND gas and gas at the velocities of the 50 and 20 km/s clouds | **supported**
- H: Do the 50 and 20 km/s clouds lie in front of Sgr A*? | E: 12CO J=1-0 absorption spectrum toward Sgr A* (ALMA Band 3) | R: Four narrow (FWHM ~1-2 km/s) absorption features at 32, 43, 50 and 63 km/s | F: Features attributed to the 50 and 20 km/s clouds, which therefore lie in front of Sgr A*; the distance in front is not set by absorption alone | **supported**
- H: Can the 90 cm morphology of Sgr A be explained with Sgr A West behind Sgr A East? | E: Three beam-sized aperture intensities at 90 cm, MeerKAT spectral index, supernova-rate and synchrotron-lifetime estimate | R: Non-zero 90 cm emission toward the minispiral (3.27 Jy) interpreted as a local synchrotron background | F: An alternative explanation with an extra synchrotron background is viable but requires further testing | **partially**
- H: Can a 3D model of the central 10 pc be reconciled with both radio constraints and CMZ orbital kinematics? | E: Combine NH3 kinematics, ALMA chemistry, CO absorption and a re-examination of prior constraints | R: Minispiral, CND and Western Streamer near Sgr A*; 50 and 20 km/s clouds and Sgr A East more than 10 pc in front | F: Alternative model proposed; connection of the clouds to the CND is not conclusively ruled out | **partially**

## Reasoning

- Why this data: GBT data added to the VLA NH3 data to recover spatially extended structure  
  > "In order to increase sensitivity to spatially-extended structure" (3.1.2 GBT observations)
- Why this method: Robust 1.0 weighting chosen for sensitivity to both point-source and extended emission; NH3 (3,3) chosen as the brightest transition with the simplest hyperfine structure  
  > "so that the observations were sensitive to a combination of both point source emission and extended emission" (3.2.1 Band 3 CO pointing toward Sgr A*); "we focus on observations of the (3,3) line, as it is the brightest of these six transitions" (3.1.1 VLA observations)
- Alternative: Option that the minispiral lies in front of Sgr A East and absorbs all its emission, with a partly filled aperture: judged unlikely because the minispiral fills most of the aperture at 6 cm  
  > "the minispiral emission appears to take up the majority of this aperture" (5.3 Revisiting Radio Absorption Measurements)
- Alternative: Option that the minispiral is inside the Sgr A East shell: judged incompatible with the geometric constraints  
  > "we find that this is incompatible with the geometric constraints discussed previously" (5.3 Revisiting Radio Absorption Measurements)
- How they decided it was enough: _not stated_
- Limitation (authors): Deconvolution does not conserve integrated flux, leading to underestimates of extended emission in the NH3 combination  
  > "The deconvolution algorithms used throughout this procedure do not conserve integrated flux densities." (3.1.2 GBT observations)
- Limitation (authors): CO absorption cannot set how far in front the clouds are  
  > "While our absorption measurements alone cannot determine how far in front the 20 and 50 km/s clouds lie" (5 Discussion)
- Limitation (authors): Exact line-of-sight distances remain hard to determine  
  > "their exact distance along the line of sight still remains difficult to determine" (6 Conclusions)
- Caveat (inferred, ours): Main result (cloud placement) rests on kinematic and absorption arguments rather than a quantitative fit; no uncertainties on velocity gradients
- Caveat (inferred, ours): CO absorption features are assigned to the clouds by linewidth and velocity alone, and the spectrum extraction is not described
- Caveat (inferred, ours): 90 cm aperture analysis uses an image of unstated origin and three hand-placed apertures, so the alternative synchrotron-background picture is weakly constrained
- Caveat (inferred, ours): ALMA data play a supporting role; much of the ALMA processing (self-cal, masks, line-free channels) is unspecified

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: tclean parameters beyond robust, masks and image sizes
- Missing: Continuum subtraction and line-free channels for CND mosaic cubes
- Missing: Aperture and extraction recipe for the 12CO absorption spectrum
- Missing: Total-power and feather settings for 2013.1.00857.S
- Missing: VLA and GBT NH3 data access and processing details (only referred to other papers)
- Missing: Identity and location of the 90 cm image
- Data volume (inferred): Roughly 100-500 GB of raw ALMA data across the two projects (11-pointing Band 3 and 68-pointing Band 6 mosaics with 12m+ACA+TP, plus eight sessions of the 2019 survey); estimate only
- Score (inferred): 2/5, ALMA project codes and observation properties are given, but key imaging and extraction settings are missing, the VLA/GBT data and 90 cm image are not tied to public products, and the main conclusions are largely qualitative kinematic and chemical arguments.
- Rediscovery candidate: no, The paper does not state data are public, many processing settings are missing, and the headline results (3D placement of clouds) are qualitative rather than numeric.

## Links

- Method: (cite: Mills15) (VLA calibration procedure used for the NH3 data)
- Method: (cite: Minh13) (GBT NH3 data calibration details)
- Method: (cite: Liu13) (GBT+VLA combination procedure (Appendix A))
- Method: (cite: Sault95) (Miriad software reference)
- Companion: (cite: Wallace22) (Observations toward Sgr E from the same 2019.1.01240.S survey)
- Companion: Mai et al. in prep. (More thorough ALMA study of chemistry and kinematics of the CND and surrounding gas)
- Companion: (cite: Lipman25); (cite: Walker25) (Independent absorption-based constraints on the cloud line-of-sight positions)
- Related: 2019.1.01240.S: ALMA Cycle 7 survey of 25 pointings within the central 5 degrees of the Galaxy
- Related: VLA K-band NH3 survey of Galactic center clouds (Mills15 and related papers)

## Checks

```json
{
 "quotes": 150,
 "quotes_ok": 150,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 15,
 "numeric_problems": 0,
 "fill": {
  "facts": 113,
  "stated": 83,
  "rate": 0.735
 },
 "evidence_ok": true
}
```

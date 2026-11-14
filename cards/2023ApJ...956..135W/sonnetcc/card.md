# Deep Search for Molecular Oxygen in TW Hya

`2023ApJ...956..135W` | The Astrophysical Journal 2023 | first author: Williams, Becky J. | arXiv: 2309.04521 | DOI: 10.3847/1538-4357/acf717

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Is a significant amount of oxygen in TW Hya hiding in gas-phase O2, searched via 16O18O emission (plus SO and SO2)?  
  > "Could oxygen be hiding in gas-phase O$_2$?" (Introduction); "We conclude that gas-phase O$_2$ is not a major oxygen-carrier in TW Hya." (abstract)
- Target **TW Hya**: coordinates _not stated_; z/distance 60.1 pc  
  > "equivalent to a spatial resolution of 30 to 35 au at a distance of 60.1 pc (cite: BailerJones2018)" (Observations); distance from Bailer-Jones et al. 2018  
  > "equivalent to a spatial resolution of 30 to 35 au at a distance of 60.1 pc (cite: BailerJones2018)" (Observations)

## Data provenance

- ALMA projects: 2019.1.01177.S
- bands: _not stated_
- frequencies and spectral setup: 16O18O 2_1-0_1 at 233.946 GHz; SO 219.949 GHz and SO2 235.152 GHz in the same set-up; original channel width 0.078 km/s  
  > "lines at 219.949 GHz and 235.152 GHz, respectively, were also included in the observational set-up." (Constraints from Serendipitous Molecular Lines); "The original channel width of the data was 0.078 km s$^{-1}$" (Methods)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15-1398 m (April 4, 44 antennas); 15-1263 m (April 6, 45 antennas)  
  > "On April 4, there were 44 antennas and baselines of 15-1398 meters, and on April 6, 45 antennas and baselines of 15-1263 meters." (Observations)
- angular resolution: 0.59'' by 0.50'', PA -88 deg (natural weighting); 30 to 35 au at 60.1 pc  
  > "The resulting beam is $0.59''$ by $0.50''$ with a position angle of $-88\degree$" (Observations); "equivalent to a spatial resolution of 30 to 35 au at a distance of 60.1 pc (cite: BailerJones2018)" (Observations)
- max recoverable scale: _not stated_
- sensitivity: rms 2.59 mJy/beam per 0.235 km/s channel  
  > "The rms noise is 2.59 mJy beam$^{-1}$ for a channel width of 0.235 km s$^{-1}$." (Observations)
- time on source: 91 minutes combined  
  > "for a combined time of 91 minutes on source" (Observations)
- observing dates: 2021 April 4 and April 6  
  > "Observations occurred on two nights in 2021, April 4 and April 6" (Observations)
- pi or archival as stated: ALMA program 2019.1.01177.S (PI: Eistrup)  
  > "were carried out as part of ALMA program 2019.1.01177.S (PI: Eistrup)" (Observations)
- Line: 16O18O N_J = 2_1-0_1 (233.946 GHz (233.94618 GHz in the LTE calculation))
- Line: SO N_J = 5_6-4_5 (219.949 GHz)
- Line: SO2 N_J = 4(2,2)-3(1,3) (235.152 GHz)
- Line: C15N N_J = 2_{5/2}-1_{3/2}, F = 2-1 and F = 3-2 (219.93404 GHz and 219.93482 GHz)
- External data: Disk mass 2.5e-2 Msun and surface density profile (used for hydrogen budget)  
  > "We adopt the (cite: Calahan2021) value of $2.5\times10^{-2}$ M$_\odot$ since it uses the HD line and multiple CO isotopologues to constrain the temperature structure." (O2 Upper Limits); "Within 120 au, we use the surface density profile from (cite: Calahan2021)" (O2 Upper Limits) [from Calahan et al. 2021 (cite: Calahan2021)]
- External data: Distance to TW Hya of 60.1 pc  
  > "$D=60.1$ pc is the distance to TW Hya (cite: BailerJones2018)" (O2 Upper Limits) [from Bailer-Jones et al. 2018 (cite: BailerJones2018)]
- External data: Systemic velocity 2.86 km/s for the Keplerian mask  
  > "We assumed a systemic velocity of 2.86 km s$^{-1}$ (cite: Favre2013)" (Methods) [from Favre et al. 2013 (cite: Favre2013)]
- External data: Inclination 5.8 deg, position angle 151 deg and stellar mass 0.81 Msun for the Keplerian mask  
  > "inclination $= 5.8\degree$, position angle $=151\degree$, and stellar mass $= 0.81$ M$_\odot$ (cite: Teague2019)" (Methods) [from Teague et al. 2019 (cite: Teague2019)]
- External data: CO J=3-2 emission data for TW Hya used to build the Keplerian mask  
  > "The mask was created using CO $J=3-2$ emission data for TW Hya from (cite: Huang2018)" (Methods) [from Huang et al. 2018 (cite: Huang2018)]
- External data: Einstein A coefficient 1.33e-8 s^-1 and upper state energy 11.23 K for the 2_1-0_1 transition  
  > "is the Einstein A coefficient of the $N_J=2_1-0_1$ transition (cite: Marechal1997)" (O2 Upper Limits); "11.23 K is the upper state energy (cite: Marechal1997)" (O2 Upper Limits) [from Marechal et al. 1997 (cite: Marechal1997)]
- External data: Partition function Q(T) from the JPL catalog, 9.4 K to 300.0 K  
  > "$Q(T)$ is the partition function from the JPL spectral line catalog (cite: Pickett1998; Mizushima1991; Crownover1990; Steinbach1975; Amano1974)" (O2 Upper Limits) [from Pickett et al. 1998 and others (cite: Pickett1998)]
- External data: 16O16O/16O18O ratio of 280  
  > "we assumed a $^{16}$O$^{16}$O/$^{16}$O$^{18}$O ratio of 280 (cite: Taquet2018; Wilson1994)" (O2 Upper Limits) [from Taquet et al. 2018; Wilson & Rood 1994 (cite: Taquet2018; Wilson1994)]
- External data: Molecular mass per hydrogen molecule of 2.8  
  > "Assuming a molecular mass per hydrogen molecule of 2.8 (cite: Kauffman2008)" (O2 Upper Limits) [from Kauffmann et al. 2008 (cite: Kauffman2008)]
- External data: Molecular line data for SO and SO2 from LAMDA and CDMS  
  > "using values from LAMDA (cite: Schoier2005) and CDMS (cite: Muller2001)" (Constraints from Serendipitous Molecular Lines) [from Schoier et al. 2005 (cite: Schoier2005); Muller et al. 2001 (cite: Muller2001)]
- External data: Earlier C15N 3-2 integrated fluxes in TW Hya of 150 +/- 20 and 160 +/- 13 mJy km/s  
  > "They used two methods to calculate an integrated flux of $150 \pm 20$ mJy km s$^{-1}$ and $160 \pm 13$ mJy km s$^{-1}$" (Constraints from Serendipitous Molecular Lines) [from Hily-Blant et al. 2017 (cite: HilyBlant2017)]

## Processing

### Calibration

- pipeline or manual: standard ALMA pipeline  
  > "The data were calibrated using the standard ALMA pipeline." (Observations)
- casa version: CASA 6.4 (stated for subsequent imaging and analysis)  
  > "Subsequent imaging and analysis were carried out using the Common Astronomy Software Applications (CASA) version 6.4 (cite: CASA2007)." (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1058+0133 (amplitude and bandpass); J1037-2934 for phase  
  > "J1058+0133 was adopted as the amplitude and bandpass calibrator, while J1037-2934 was used for phase calibration." (Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean (CASA 6.4), after uvcontsub; cvel for matched filtering  
  > "The data were imaged using *tclean*, initially with a natural weighting scheme to improve line sensitivity." (Observations); "For the matched filtering analysis, Earth’s rotation was first corrected for using the CASA task *cvel*." (Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting initially; several Briggs robust values tried (not listed); robust = 2 for the C15N images  
  > "We imaged the data with several combinations of the Briggs weighting robust parameter (cite: Briggs1995) and uvtaper." (Methods); "For these images, we used Briggs weighting (robust = 2) and a uvtaper of 0.3 arcsec." (Constraints from Serendipitous Molecular Lines)
- uv taper: several tried (values not listed); 0.3 arcsec for the C15N images  
  > "For these images, we used Briggs weighting (robust = 2) and a uvtaper of 0.3 arcsec." (Constraints from Serendipitous Molecular Lines)
- cell size: _not stated_
- image size: _not stated_
- masking: Keplerian masks of 120 au and 260 au radius (convolved), cleaning threshold 5 sigma  
  > "Two masks were then created for the O$_2$ data, one with a radius set to 100 au (convolved to 120 au), and a second with a radius set to 240 au (convolved to 260 au, covering the extent of the CO emission)." (Methods); "Both masks were used separately in cleaning, using a $5\sigma$ threshold." (Methods)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub, fit order 1, edge channels excluded  
  > "Continuum emission was subtracted using the task *uvcontsub*, applying a fit order of 1 and excluding edge channels." (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: channel averaging of 2, 3 and 5 channels tried; final 0.235 km/s channels  
  > "we experimented with averaging 2, 3, and 5 channels together." (Methods); "shows the data imaged with natural weighting and velocity averaging to a channel size of 0.235 km s$^{-1}$." (Imaging Results)
- final beam: 0.59'' by 0.50'', PA -88 deg  
  > "The resulting beam is $0.59''$ by $0.50''$ with a position angle of $-88\degree$" (Observations)
- final rms: 2.59 mJy/beam per 0.235 km/s channel  
  > "The rms noise is 2.59 mJy beam$^{-1}$ for a channel width of 0.235 km s$^{-1}$." (Observations)

### Inherited from earlier work

- Keplerian mask method and code  
  > "We first created a Keplerian mask (cite: TeagueKepMask) to use with the CASA *tclean* task." (Methods) [from Teague keplerian_mask (cite: TeagueKepMask); Salinas et al. 2017 (cite: Salinas2017); Teague et al. 2022 (cite: Teague2022)]
- Matched filtering technique, including Keplerian mask as template  
  > "matched filtering has previously been successful at finding the signatures of line emission in other sources (cite: Loomis2020), including when using a Keplerian mask as a template (cite: Loomis2018)." (Matched Filter Results) [from Loomis et al. 2018 (cite: Loomis2018); Loomis et al. 2020 (cite: Loomis2020)]
- Flux-to-number-of-molecules equation for the upper limits  
  > "we calculate the 1$\sigma$ upper limit on the maximum number of O$_2$ molecules that could be present in TW Hya, using the following adapted from (cite: Bergin2013)." (O2 Upper Limits) [from Bergin et al. 2013 (cite: Bergin2013)]
- Disk parameters (v_sys, inclination, PA, stellar mass) for the Keplerian mask taken from earlier papers  
  > "We assumed a systemic velocity of 2.86 km s$^{-1}$ (cite: Favre2013), distance of 60.1 pc (cite: BailerJones2018)" (Methods) [from Favre et al. 2013 (cite: Favre2013); Bailer-Jones et al. 2018 (cite: BailerJones2018); Teague et al. 2019 (cite: Teague2019)]

### Not stated but needed to reproduce (our reading)

- Final Briggs robust and uvtaper values for each tclean run (only natural weighting and the C15N values are given)
- Image size, cell size, deconvolver, niter and cleaning threshold units for tclean
- Which channels count as edge channels excluded in uvcontsub
- Spectral windows and velocity grid (rest frequency and LSRK start) used for imaging and the flux velocity ranges
- How the 1-sigma uncertainty on the disk-integrated flux was computed (aperture, beam correction, number of channels, correlated noise)
- Whether primary beam correction was applied and the image or aperture shape used for the 120 au and 260 au fluxes
- Matched filter details: the filter spectral resolution, how the impulse response sigma was measured, and the VISIBLE version and settings
- Exact Q(T) values and the specific gas-temperature grid used in the LTE calculation
- Calahan et al. 2021 surface density profile values used inside 120 au
- ALMA pipeline and CASA pipeline version used for calibration, and the array (12 m) and number of execution blocks
- Source coordinates and phase centre

## Analysis recipe

1. **Continuum subtraction and imaging of the 16O18O cube**: uvcontsub (order 1) then tclean with natural weighting, with channel averaging and several Briggs robust and uvtaper combinations tried  
  > "Continuum emission was subtracted using the task *uvcontsub*, applying a fit order of 1 and excluding edge channels." (Observations); "We imaged the data with several combinations of the Briggs weighting robust parameter (cite: Briggs1995) and uvtaper." (Methods)
   - software: CASA 6.4, uvcontsub, tclean
   - parameter: natural weighting; channel width 0.078 km/s averaged to 0.235 km/s; rms 2.59 mJy/beam  
  > "The rms noise is 2.59 mJy beam$^{-1}$ for a channel width of 0.235 km s$^{-1}$." (Observations); "The original channel width of the data was 0.078 km s$^{-1}$, and we experimented with averaging 2, 3, and 5 channels together." (Methods)
   - fitting: _not stated_
   - validation: _not stated_
2. **Keplerian-mask clean and disk-integrated flux limits in the image plane**: Keplerian masks (120 au and 260 au) built from TW Hya parameters and CO J=3-2 data, used in tclean with a 5 sigma threshold; flux summed within 120 au and 260 au  
  > "Both masks were used separately in cleaning, using a $5\sigma$ threshold." (Methods); "We calculated a disk integrated flux (for a velocity range of 4.69 km s$^{-1}$) of $-11.8 \pm 14.2$ mJy km s$^{-1}$ within 120 au" (Imaging Results)
   - software: CASA tclean, Keplerian Mask
   - parameter: target_res = 0.4 arcsec, dV0 = 500 m/s  
  > "Specifically, we set the *target_res* = 0.4, which convolves the mask with a circular beam of 0.4 arcsec FWHM, and *dV0* = 500 m s$^{-1}$, which affects the radially varying line width of emission." (Methods)
   - assumption: v_sys 2.86 km/s, distance 60.1 pc, inclination 5.8 deg, PA 151 deg, stellar mass 0.81 Msun  
  > "inclination $= 5.8\degree$, position angle $=151\degree$, and stellar mass $= 0.81$ M$_\odot$ (cite: Teague2019)" (Methods)
   - fitting: _not stated_
   - validation: Both masks gave the same image because no values exceeded 5 sigma  
  > "The resulting image was the same in both cases because there were no values above $5\sigma$ within either mask." (Methods)
3. **Matched filtering in the visibility plane**: cvel to correct for Earth's rotation, then Keplerian masks (120 au and 260 au) used as filters, Fourier transformed to a kernel and cross-correlated with the visibilities to give an impulse response spectrum; a 3 sigma response at 0 km/s would indicate emission  
  > "The filter is Fourier transformed to generate a kernel that is then cross-correlated with the data." (Methods); "A $3\sigma$ response at 0 km s$^{-1}$ would indicate emission from $^{16}$O$^{18}$O." (Matched Filter Results)
   - software: VISIBLE, CASA cvel, Keplerian Mask
   - parameter: filters: Keplerian masks of 120 au and 260 au radius  
  > "For matched filtering, we used both Keplerian masks as filters (one with a 120 au radius, and one with a 260 au radius)." (Methods)
   - fitting: _not stated_
   - validation: _not stated_
4. **Convert flux limit to a limit on the number of O2 molecules**: LTE single-line relation with the 1 sigma flux as F_l, over gas temperatures 9.4 K to 300.0 K, then scaled by 16O16O/16O18O = 280  
  > "we explore a range of temperatures and assume its emission is in local thermodynamic equilibrium (LTE)." (O2 Upper Limits); "we assumed a $^{16}$O$^{16}$O/$^{16}$O$^{18}$O ratio of 280 (cite: Taquet2018; Wilson1994)." (O2 Upper Limits)
   - parameter: A_20 = 1.33e-8 s^-1, nu = 233.94618 GHz, D = 60.1 pc, upper state energy 11.23 K, degeneracy 3  
  > "$\nu=233.94618$ GHz is the frequency of the $N_J=2_1-0_1$ transition, and $D=60.1$ pc is the distance to TW Hya (cite: BailerJones2018)." (O2 Upper Limits)
   - assumption: LTE, temperature range 9.4 K to 300.0 K (set by the range of the JPL partition functions)  
  > "These partition functions are given for temperatures ranging from 9.4 K to 300.0 K, so this is the temperature range we use in our calculations." (O2 Upper Limits)
   - fitting: _not stated_
   - validation: _not stated_
5. **Express the O2 limit as an abundance relative to H**: Divide the O2 molecule limit by the number of hydrogen atoms from the Calahan et al. 2021 disk mass (whole disk) or surface density profile (within 120 au)  
  > "Assuming a molecular mass per hydrogen molecule of 2.8 (cite: Kauffman2008), this equates to $2.1\times10^{55}$ hydrogen atoms in the whole disk." (O2 Upper Limits)
   - parameter: disk mass 2.5e-2 Msun (whole disk), 1.8e-2 Msun within 120 au; 2.1e55 and 1.5e55 H atoms  
  > "Within 120 au, we use the surface density profile from (cite: Calahan2021) to calculate a disk mass of $1.8\times10^{-2}$ M$_\odot$, which equates to $1.5\times10^{55}$ hydrogen atoms." (O2 Upper Limits)
   - assumption: Disk mass from Calahan et al. 2021; the paper notes a wide range of literature disk masses  
  > "but we note that there are a wide range of mass values for the TW Hya disk in the literature (cite: Miotello2022)" (O2 Upper Limits)
   - fitting: _not stated_
   - validation: _not stated_
6. **Search for SO, SO2 and C15N in the same data**: Same imaging and matched filtering approach as for 16O18O; limits for SO and SO2 from the modified LTE equation; C15N found by matched filtering with the 120 au mask and measured in images  
  > "we searched for emission from these lines using similar techniques as for $^{16}$O$^{18}$O." (Constraints from Serendipitous Molecular Lines); "Using matched filtering with the 120 au Keplerian mask, we obtained a 7$\sigma$ filter response." (Constraints from Serendipitous Molecular Lines)
   - software: CASA tclean, VISIBLE
   - parameter: C15N images: Briggs robust = 2, uvtaper 0.3 arcsec, 200 au circular region  
  > "calculated within a 200 au circular region covering visible emission. For these images, we used Briggs weighting (robust = 2) and a uvtaper of 0.3 arcsec." (Constraints from Serendipitous Molecular Lines)
   - fitting: _not stated_
   - validation: C15N found by matched filtering and confirmed in images; first integrated flux consistent with the earlier 3-2 measurement  
  > "which we found via matched filtering and confirm through imaging." (abstract); "the first of which is consistent with our value" (Constraints from Serendipitous Molecular Lines)

## Software

- **CASA** 6.4: imaging and analysis (uvcontsub, tclean, cvel)  
  > "Subsequent imaging and analysis were carried out using the Common Astronomy Software Applications (CASA) version 6.4 (cite: CASA2007)." (Observations)
- **Keplerian Mask** : building Keplerian masks for cleaning and as matched filter templates  
  > "We first created a Keplerian mask (cite: TeagueKepMask) to use with the CASA *tclean* task." (Methods)
- **VISIBLE** : listed in the Software section, matched filtering (VISibility-Based Line Extraction)  
  > "Astropy (cite: Astropy2013), CASA (cite: CASA2007), Keplerian Mask (cite: TeagueKepMask), VISIBLE (cite: LoomisVISIBLE)" (Software)
- **Astropy** : listed in the Software section; specific use not stated  
  > "Astropy (cite: Astropy2013), CASA (cite: CASA2007), Keplerian Mask (cite: TeagueKepMask), VISIBLE (cite: LoomisVISIBLE)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 16O18O disk-integrated flux within 120 au | -11.8 | +/- 14.2 | mJy km/s | 2 | We calculated a disk integrated flux (for a velocity range of 4.69 km s$^{-1}$) of $-11.8 \pm 14.2$ mJy km s$^{-1}$ within 120 au |
| 16O18O disk-integrated flux within 260 au | 7.4 | +/- 18.0 | mJy km/s | 2 | and $7.4 \pm 18.0$ mJy km s$^{-1}$ within 260 au |
| Upper limit on number of O2 molecules within 120 au (9.4-300 K) | (1.1-10.4)e49 | not stated | molecules | 4 | We obtained an upper limit of $(1.1-10.4)\times10^{49}$ O$_2$ molecules within 120 au |
| Upper limit on number of O2 molecules within 260 au (9.4-300 K) | (1.4-13.2)e49 | not stated | molecules | 4 | and $(1.4-13.2)\times10^{49}$ molecules within 260 au, for a temperature range of 9.4 K to 300.0 K. |
| Hydrogen atoms in the whole disk | 2.1e55 | not stated | atoms | 5 | this equates to $2.1\times10^{55}$ hydrogen atoms in the whole disk. |
| Disk mass within 120 au | 1.8e-2 | not stated | Msun | 5 | to calculate a disk mass of $1.8\times10^{-2}$ M$_\odot$, which equates to $1.5\times10^{55}$ hydrogen atoms. |
| O2/H upper limit within 120 au | (7.2-70)e-7 | not stated | dimensionless | 5 | we estimate an O$_2$/H abundance of $(7.2-70)\times10^{-7}$ within 120 au |
| O2/H upper limit within 260 au | (6.4-62)e-7 | not stated | dimensionless | 5 | and $(6.4-62)\times10^{-7}$ within 260 au, for temperatures ranging from 9.4 K to 300.0 K. |
| SO disk-integrated flux within 120 au | -0.05 | +/- 12.5 | mJy km/s | 6 | The disk integrated flux for the SO line is $-0.05 \pm 12.5$ mJy km s$^{-1}$ within 120 au |
| SO disk-integrated flux within 260 au | -21.4 | +/- 21.2 | mJy km/s | 6 | and $-21.4 \pm 21.2$ mJy km s$^{-1}$ within 260 au (covering a range of 4.99 km s$^{-1}$) |
| SO2 disk-integrated flux within 120 au | 24.4 | +/- 14.8 | mJy km/s | 6 | For SO$_2$, the flux is $24.4 \pm 14.8$ mJy km s$^{-1}$ within 120 au |
| SO2 disk-integrated flux within 260 au | 34.3 | +/- 24.5 | mJy km/s | 6 | and $34.3 \pm 24.5$ mJy km s$^{-1}$ within 260 au (covering a range of 4.67 km s$^{-1}$) |
| SO/H 1-sigma upper limit within 120 au and 260 au | (2.4-10)e-13 within 120 au; (2.9-12)e-13 within 260 au | not stated | dimensionless | 6 | We calculate a 1$\sigma$ upper limit of SO/H = $(2.4-10)\times10^{-13}$ within 120 au and $(2.9-12)\times10^{-13}$ within 260 au |
| SO2/H 1-sigma upper limit within 120 au and 260 au | (7.9-197)e-13 within 120 au; (9.1-229)e-13 within 260 au | not stated | dimensionless | 6 | SO$_2$/H = $(7.9-197)\times10^{-13}$ within 120 au and $(9.1-229)\times10^{-13}$ within 260 au, for a temperature range of 9.4 K to 300.0 K. |
| C15N matched filter response | 7 | not stated | sigma | 6 | Using matched filtering with the 120 au Keplerian mask, we obtained a 7$\sigma$ filter response. |
| C15N integrated flux (2.33 km/s range, 200 au region) | 113.5 | +/- 17.0 | mJy km/s | 6 | with an integrated flux of $113.5 \pm 17.0$ mJy km s$^{-1}$ for a range of 2.33 km s$^{-1}$, calculated within a 200 au circular region covering visible emission. |

## Qualitative findings

- 16O18O is not detected in either imaging or matched filtering, so gas-phase O2 is not a major oxygen carrier in TW Hya  
  > "We can conclusively say that the $^{16}$O$^{18}$O 233.946 GHz line is not detected at the sensitivity of the present measurements." (Matched Filter Results)
- The main oxygen carrier(s) in TW Hya remain undetected  
  > "Taking into account other existing molecular detections in TW Hya, the main oxygen-carrier(s) remain undetected." (Conclusions)

## Claim tuples

- H: Gas-phase O2 is a major carrier of volatile oxygen in the TW Hya disk, as some astrochemical models predict | E: Image-plane search (Keplerian-mask tclean, natural weighting) and visibility-plane matched filtering for 16O18O at 233.946 GHz, then LTE upper limits scaled to O2/H | R: No detection; O2/H below (6.4-70)e-7 | F: Gas-phase O2 is not a major oxygen carrier in TW Hya | **supported**
- H: SO and SO2 might be prominent oxygen carriers in TW Hya | E: Same imaging and matched filtering applied to the SO and SO2 lines covered in the same set-up | R: Neither line detected above 3 sigma; SO/H and SO2/H upper limits derived | F: Oxygen is not bound up with sulfur either | **supported**
- H: Weak, unexpected lines in the data can be recovered by matched filtering | E: Matched filter with the 120 au Keplerian mask, followed by imaging with robust = 2 and a 0.3 arcsec uvtaper | R: C15N hyperfine detection at 7 sigma with an integrated flux of 113.5 +/- 17.0 mJy km/s | F: C15N is detected in TW Hya, with a flux consistent with one earlier measurement | **supported**
- H: Protoplanetary disks could be the origin of the O2 seen in comets | E: Compare the O2/H limits with water vapor abundance in TW Hya and the O2/H2O ratio of about 0.04 in comets | R: Limits are about two orders of magnitude above the detected water vapor abundance | F: The limits are not constraining enough to rule out disks as the origin of cometary O2 | **partially**

## Reasoning

- Why this data: TW Hya is gas-rich and nearby, a good candidate for faint emission  
  > "TW Hya’s relatively gas-rich disk and nearby proximity make it a good candidate for searching for faint emission." (Introduction)
- Why this method: Disk-integrated flux is the goal so full resolution was not needed; matched filtering works in the visibility plane without imaging  
  > "Because we were mainly interested in looking at the disk integrated flux, we did not need the full spatial resolution of the observations." (Methods); "Matched filtering is applied in the visibility plane and therefore does not involve any imaging." (Methods)
- Alternative: Two Keplerian mask radii (120 au and 260 au) and several weighting, uvtaper and channel-averaging combinations were tried; none gave a detection  
  > "For all attempted combinations of imaging parameters, no significant detection was found within either choice of mask." (Imaging Results)
- How they decided it was enough: Detection criterion of a 3 sigma response in imaging or matched filtering  
  > "A $3\sigma$ response at 0 km s$^{-1}$ would indicate emission from $^{16}$O$^{18}$O." (Matched Filter Results)
- Limitation (authors): O2 emission could be confined to a smaller area than the masks and hidden in the noise  
  > "It is possible that O$_2$ emission covers a smaller area than these radii and could be hidden in the noise." (Methods)
- Limitation (authors): Wide range of literature disk masses for TW Hya, affecting the hydrogen budget  
  > "but we note that there are a wide range of mass values for the TW Hya disk in the literature (cite: Miotello2022)" (O2 Upper Limits)
- Caveat (inferred, ours): Abundance limits depend on a single disk mass (Calahan et al. 2021) and on an assumed 16O16O/16O18O of 280; gas-to-dust and mass uncertainties are not propagated
- Caveat (inferred, ours): LTE over 9.4-300 K is broad; no physical temperature structure or non-LTE or disk-model treatment of where O2 would emit
- Caveat (inferred, ours): Quoted limits are 1 sigma, not 3 sigma, which makes them weaker constraints than usual upper limits
- Caveat (inferred, ours): Image-plane versus matched-filter sensitivity is not compared quantitatively, and the flux uncertainty method is not described

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Final robust and uvtaper values for each tclean run and imaging geometry
- Missing: Matched filter implementation details and sigma estimation
- Missing: Partition function values and flux aperture/uncertainty method
- Missing: Pipeline version and exact set of execution blocks used
- Data volume (inferred): About 10-30 GB for two execution blocks (91 min on source, raw plus calibrated); a few GB if only calibrated spectral windows are kept
- Score (inferred): 3/5, One ALMA project code and a clear workflow, with numeric flux and abundance limits and fully given Keplerian mask parameters, but final tclean settings, matched-filter details and uncertainty method are not given
- Rediscovery candidate: yes, Single named ALMA project and stated numeric limits; imaging and the LTE abundance calculation are reproducible within tolerance, though public release of the data is not stated in the paper

## Links

- Method: Loomis et al. 2018 (cite: Loomis2018) (Matched filtering technique with Keplerian mask templates)
- Method: Teague keplerian_mask (cite: TeagueKepMask) (Code used to build the Keplerian masks)
- Method: Bergin et al. 2013 (cite: Bergin2013) (Source of the LTE flux to molecule number relation)
- Companion: Calahan et al. 2021 (cite: Calahan2021) (TW Hya disk mass and surface density used for the hydrogen budget)
- Companion: Eistrup et al. 2018 (cite: Eistrup2018) (Chemical model predicting abundant gas-phase O2 in disk midplanes)
- Related: ALMA program 2019.1.01177.S (PI: Eistrup)

## Checks

```json
{
 "quotes": 112,
 "quotes_ok": 112,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 1,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 16,
 "numeric_problems": 0,
 "fill": {
  "facts": 94,
  "stated": 65,
  "rate": 0.691
 },
 "evidence_ok": true
}
```

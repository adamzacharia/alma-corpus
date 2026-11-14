# First Millimeter Flares Detected from ϵ Eridani with the Atacama Large Millimeter/submillimeter Array

`2022ApJ...939L...6B` | The Astrophysical Journal Letters 2022 | first author: Burton, Kiana | arXiv: 2210.10818 | DOI: 10.3847/2041-8213/ac9973

Card schema 1.0 | model gemini-4-argon | depth full | type archival_reuse

## Science

- Fields: stellar_physics, debris_disks
- Question: Search archival ALMA 12-m and ACA observations of the Sun-like star epsilon Eridani for millimeter flaring emission and characterize its temporal, spectral, and polarization properties, as well as constraints on inner dust belt emission.  
  > "In this paper, we analyze archival observations from the Atacama Large Millimeter/submillimeter Array (ALMA) full 12-m array and Atacama Compact Array (ACA) of $\epsilon$ Eridani and report the discovery of three millimeter flaring events." (Introduction); "In Section 4, we discuss the properties of the $\epsilon$ Eridani flares in the context of those seen from M dwarfs and the Sun, and consider the complications of disentangling stellar and dust components" (Introduction)
- Target **\epsilon Eridani**: coordinates _not stated_; z/distance 3.22 pc  
  > "$\epsilon$ Eridani is a K2V star (cite: Keenan:1998) at a distance of 3.22 pc (cite: vanLeeuwen:2007)" (Introduction); distance from (cite: vanLeeuwen:2007)  
  > "$\epsilon$ Eridani is a K2V star (cite: Keenan:1998) at a distance of 3.22 pc (cite: vanLeeuwen:2007)" (Introduction)

## Data provenance

- ALMA projects: 2016.1.00803.S, 2013.1.00645.S
- bands: Band 6 (1.3 mm / 1.33 mm)  
  > "found in archival ALMA 12m and ACA observations at 1.33 mm" (Abstract); "Archival observations are available using Band 6 (center wavelength of 1.3 mm) from both the full 12-m array and ACA." (Observations)
- frequencies and spectral setup: lower sideband (217 and 219 GHz) and upper sideband (230 and 232 GHz)  
  > "fit point source models to the candidate flares this time to the lower (217 and 219 GHz) and upper (230 and 232 GHz) sidebands independently." (Creating Light Curves and Identifying Flares)
- continuum bandwidth: _not stated_
- arrays: ALMA 12-m array (34-35 antennas) and ACA (7-m)  
  > "$\epsilon$ Eridani was also observed with the full ALMA 12-m array with 34–35 antennas between 2015 January 17–18" (ALMA 12-m Observations); "with fewer antennas in the array and smaller antenna diameters (7-m for the ACA)" (Creating Light Curves and Identifying Flares)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.6'' x 1.1'' (12-m array)  
  > "The synthesized beam size is $1.6\ensuremath{''}\times1.1\ensuremath{''}$." (ALMA 12-m Observations)
- max recoverable scale: _not stated_
- sensitivity: 94 \muJy beam^-1 (ACA), 33 \muJy beam^-1 (12-m)  
  > "The rms noise is 94 $\mu$Jy beam$^{-1}$." (ACA Observations); "We determine the rms noise to be 33 $\mu$Jy beam$^{-1}$" (ALMA 12-m Observations)
- time on source: 5 hours (ACA), 4.4 hours (12-m)  
  > "The $\epsilon$ Eridani system was observed by the ACA between 2015 October 24 and 2015 November 23 (2016.1.00803.S, PI: MacGregor) for a total of 5 hours on-source." (ACA Observations); "$\epsilon$ Eridani was also observed with the full ALMA 12-m array with 34–35 antennas between 2015 January 17–18 (2013.1.00645.S, PI: Jordán) for a total of 4.4 hours on-source." (ALMA 12-m Observations)
- observing dates: 2015 January 17-18 (12-m); 2015 October 24-November 23 / 2016 October 24-November 23 (ACA)  
  > "found in archival ALMA 12m and ACA observations at 1.33 mm taken from 2015 January 17–18 and 2016 October 24–November 23, respectively." (Abstract); "The $\epsilon$ Eridani system was observed by the ACA between 2015 October 24 and 2015 November 23 (2016.1.00803.S, PI: MacGregor) for a total of 5 hours on-source." (ACA Observations)
- pi or archival as stated: archival (PI: MacGregor for 2016.1.00803.S; PI: Jordán for 2013.1.00645.S)  
  > "The $\epsilon$ Eridani system was observed by the ACA between 2015 October 24 and 2015 November 23 (2016.1.00803.S, PI: MacGregor) for a total of 5 hours on-source." (ACA Observations); "$\epsilon$ Eridani was also observed with the full ALMA 12-m array with 34–35 antennas between 2015 January 17–18 (2013.1.00645.S, PI: Jordán) for a total of 4.4 hours on-source." (ALMA 12-m Observations)
- External data: Millimeter flare properties for AU Mic and Proxima Centauri  
  > "Previous detection of flares at millimeter wavelengths have mostly come from M dwarfs (see Table 1) (cite: MacGregor:2018a; MacGregor:2020)" (Introduction); "Table 1 lists these values in comparison to all other millimeter flares previously detected with ALMA." (Characterizing Millimeter Flaring Emission) [from (cite: MacGregor:2018a; MacGregor:2020)]
- External data: Effective temperature of epsilon Eridani (5039 +/- 126 K)  
  > "The effective temperature of $\epsilon$ Eridani is $5039\pm126$ K (cite: Baines:2012)" (Constraints on Dust Emission from an Inner Debris Disk) [from (cite: Baines:2012)]
- External data: Expected photospheric flux at 1.3 mm of 0.53 mJy  
  > "which implies a photospheric flux at 1.3 mm of $0.53$ mJy (cite: Backman:2009)." (Constraints on Dust Emission from an Inner Debris Disk) [from (cite: Backman:2009)]
- External data: Predicted flux at 1.3 mm of ~0.2-0.3 mJy from extrapolated SED fits for the inner dust ring  
  > "Extrapolating the SED fits for the inner dust ring from (cite: Su:2017) yields a predicted flux at 1.3 mm of $\sim0.2-0.3$ mJy, strikingly consistent with what we determine here." (Constraints on Dust Emission from an Inner Debris Disk) [from (cite: Su:2017)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0423-013, Uranus, and Mars  
  > "while J0423-013, Uranus, and Mars were used for absolute flux calibration." (ACA Observations); "while J0423-013, Uranus, and Mars were used for absolute flux calibration." (ALMA 12-m Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "Imaging made use of the `tclean` task." (Observations)
- deconvolver: _not stated_
- weighting robust: natural weight  
  > "Figure 1 (left panel) shows the natural weight continuum image obtained by combining all of these observations into a single map of the system." (ACA Observations); "Figure 1 (right panel) displays the primary beam corrected natural weight continuum image." (ALMA 12-m Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied to all images  
  > "It is important to note that a primary beam correction has been applied to all of the images we present in this paper." (ALMA 12-m Observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.6'' x 1.1'' (12-m)  
  > "The synthesized beam size is $1.6\ensuremath{''}\times1.1\ensuremath{''}$." (ALMA 12-m Observations)
- final rms: 94 \muJy beam^-1 (ACA), 33 \muJy beam^-1 (12-m)  
  > "The rms noise is 94 $\mu$Jy beam$^{-1}$." (ACA Observations); "We determine the rms noise to be 33 $\mu$Jy beam$^{-1}$" (ALMA 12-m Observations)

### Inherited from earlier work

- Additional details about the ALMA 12-m observations  
  > "Additional details about these observations can be found in (cite: Booth:2017), who analyzed the northern arc of $\epsilon$ Eridani’s outer debris disk." (ALMA 12-m Observations) [from (cite: Booth:2017)]
- Approach of searching for time-variable emission and flares by fitting point source models to the millimeter visibilities  
  > "As in (cite: MacGregor:2018a) and (cite: MacGregor:2020), we search for time-variable emission and flares by fitting point source models to the millimeter visibilities." (Creating Light Curves and Identifying Flares) [from (cite: MacGregor:2018a) and (cite: MacGregor:2020)]

### Not stated but needed to reproduce (our reading)

- CASA version used for calibration, imaging, and uvmodelfit
- Whether archival data were calibrated via pipeline or manual scripts
- Image pixel cell size and image dimensions in tclean
- Deconvolver algorithm and stopping threshold/masking in tclean
- Exact coordinates or proper-motion-corrected position fixed or fitted in uvmodelfit
- How the ten background regions for RMS calculation were defined

## Analysis recipe

1. **Continuum imaging and combined visibility fitting**: Create natural weight primary-beam-corrected continuum images using tclean, calculate rms across ten source-free regions, and fit point source models to the combined visibilities using uvmodelfit.  
  > "Imaging made use of the `tclean` task." (Observations); "In order to calculate the rms, we choose ten regions that do not overlap with known emission sources (i.e., the star and surrounding disk), calculate the rms in each region, and average the values." (ALMA 12-m Observations); "We use the `uvmodelfit` task in `CASA` to fit a point source model to the visibilities and return a flux density of $794\pm45$ $\mu$Jy" (ALMA 12-m Observations)
   - software: CASA, tclean, uvmodelfit
   - parameter: natural weighting  
  > "Figure 1 (right panel) displays the primary beam corrected natural weight continuum image." (ALMA 12-m Observations)
   - parameter: ten source-free regions for rms calculation  
  > "In order to calculate the rms, we choose ten regions that do not overlap with known emission sources (i.e., the star and surrounding disk), calculate the rms in each region, and average the values." (ALMA 12-m Observations)
   - assumption: Point source model at the stellar position  
  > "Fitting a point source model to the combined visibilities yields a flux of $776 \pm 103$ $\mu$Jy." (ACA Observations)
   - fitting: Point source visibility fitting with CASA uvmodelfit  
  > "We use the `uvmodelfit` task in `CASA` to fit a point source model to the visibilities" (ALMA 12-m Observations)
   - validation: Compare 12-m stellar flux density (794 +/- 45 uJy) to value reported in Booth et al. 2017 (820 +/- 70 uJy)  
  > "return a flux density of $794\pm45$ $\mu$Jy, consistent within the mutual uncertainties to the $820\pm70$ $\mu$Jy reported in (cite: Booth:2017)." (ALMA 12-m Observations)
2. **Create light curves and identify millimeter flares**: Run an automatic pipeline using CASA uvmodelfit to fit point source models to each telescope integration step-by-step in time, flagging flux densities above 3 sigma, and confirm candidates by fitting lower and upper sidebands independently.  
  > "we have now developed an automatic pipeline approach that makes use of the `uvmodelfit` task in `CASA`. For a given data set, models are fit to each integration from the telescope starting at the beginning of the observations and stepping forward in time." (Creating Light Curves and Identifying Flares); "Once the initial light curve is created, any recorded flux density that is above $3\sigma$ is flagged as a potential flaring event." (Creating Light Curves and Identifying Flares); "In order to confirm flares, we run a second pipeline and again fit point source models to the candidate flares this time to the lower (217 and 219 GHz) and upper (230 and 232 GHz) sidebands independently." (Creating Light Curves and Identifying Flares)
   - software: CASA, uvmodelfit
   - parameter: integration time = 6 sec (ALMA 12-m) and 10 sec (ACA)  
  > "For the ALMA 12-m and ACA observations, the integration times were 6 and 10 sec, respectively, setting the finest temporal resolution of the final light curves." (Creating Light Curves and Identifying Flares)
   - parameter: detection threshold > 3 sigma  
  > "Once the initial light curve is created, any recorded flux density that is above $3\sigma$ is flagged as a potential flaring event." (Creating Light Curves and Identifying Flares)
   - parameter: sideband flux agreement within 20%  
  > "We require that the flux densities measured in both sidebands be within 20% of each other." (Creating Light Curves and Identifying Flares)
   - assumption: Point source model for the star  
  > "we search for time-variable emission and flares by fitting point source models to the millimeter visibilities." (Creating Light Curves and Identifying Flares)
   - fitting: CASA uvmodelfit per integration  
  > "For a given data set, models are fit to each integration from the telescope starting at the beginning of the observations and stepping forward in time." (Creating Light Curves and Identifying Flares)
   - validation: Require lower and upper sideband flux densities to be within 20% of each other, and compare visibility-derived fluxes with images made before, at peak, and after each flare.  
  > "We require that the flux densities measured in both sidebands be within 20% of each other. Any events that do not meet this criteria are discarded as spurious noise." (Creating Light Curves and Identifying Flares); "The flux densities obtained from these images are consistent with those obtained from our visibility modeling, adding further credibility to these detections." (Creating Light Curves and Identifying Flares)
3. **Characterize flare temporal structure, spectral index, and linear polarization**: Fit Gaussian functions to flare light curves to measure FWHM (t_1/2), fit point source models with uvmodelfit to upper and lower sidebands independently for spectral index, and fit XX and YY polarizations independently to compute Stokes Q and I for fractional linear polarization |Q/I| at flare peak.  
  > "To determine the temporal structure of the flaring events, we fit Gaussian functions to the light curves shown in Figure 4." (Characterizing Millimeter Flaring Emission); "To obtain the spectral index, we fit point source models using `uvmodelfit` in `CASA` to the millimeter visibilities of the upper and lower sidebands independently." (Characterizing Millimeter Flaring Emission); "For the fractional linear polarization, we fit point sources models to ALMA’s XX and YY polarizations independently, and compute the Stokes parameters $Q = <{E_{x}}^2>-<{E_{y}}^2>$ and $I = <{E_{x}}^2>+<{E_{y}}^2>$." (Characterizing Millimeter Flaring Emission)
   - software: CASA, uvmodelfit
   - parameter: upper (230 + 232 GHz) and lower (219 + 217 GHz) sidebands  
  > "we examine the spectral index (dependence of the flux on the frequency, F$_\nu\propto\nu^\alpha$) of the upper (230 + 232 GHz) and lower (219 + 217 GHz) sidebands" (Characterizing Millimeter Flaring Emission)
   - parameter: ALMA XX and YY polarizations at flare peak  
  > "For the fractional linear polarization, we fit point sources models to ALMA’s XX and YY polarizations independently, and compute the Stokes parameters $Q = <{E_{x}}^2>-<{E_{y}}^2>$ and $I = <{E_{x}}^2>+<{E_{y}}^2>$." (Characterizing Millimeter Flaring Emission)
   - assumption: Gaussian temporal profile and power-law spectral dependence F_nu \propto \nu^\alpha  
  > "To determine the temporal structure of the flaring events, we fit Gaussian functions to the light curves shown in Figure 4." (Characterizing Millimeter Flaring Emission); "we examine the spectral index (dependence of the flux on the frequency, F$_\nu\propto\nu^\alpha$) of the upper (230 + 232 GHz) and lower (219 + 217 GHz) sidebands" (Characterizing Millimeter Flaring Emission)
   - fitting: Gaussian function fits to light curves; CASA uvmodelfit point source fits to sideband and XX/YY visibilities  
  > "To determine the temporal structure of the flaring events, we fit Gaussian functions to the light curves shown in Figure 4." (Characterizing Millimeter Flaring Emission); "To obtain the spectral index, we fit point source models using `uvmodelfit` in `CASA` to the millimeter visibilities of the upper and lower sidebands independently." (Characterizing Millimeter Flaring Emission)
   - validation: _not stated_
4. **Estimate magnetic field strength in the flare-emitting region**: Associate the observing frequency with harmonic numbers s (between 10 and 100) of the electron gyrofrequency \nu_B = 2.83 x 10^6 B(G).  
  > "Gyrosynchrotron emission is produced by a range of harmonic numbers $s$ of the electron gyrofrequency, $\nu_{B}=2.83\times10^{6} B (G)$, with $s$ between 10 and 100." (Nature of the Detected Millimeter Flares); "The properties of the emitting region under consideration here can be determined generally by associating the observing frequency with a harmonic of the gyrofrequency. This leads to an unbiased but large range of magnetic field strengths in the mm-emitting region of 0.8–8 kG." (Nature of the Detected Millimeter Flares)
   - parameter: harmonic numbers s between 10 and 100  
  > "Gyrosynchrotron emission is produced by a range of harmonic numbers $s$ of the electron gyrofrequency, $\nu_{B}=2.83\times10^{6} B (G)$, with $s$ between 10 and 100." (Nature of the Detected Millimeter Flares)
   - assumption: Gyrosynchrotron emission mechanism  
  > "Gyrosynchrotron emission is produced by a range of harmonic numbers $s$ of the electron gyrofrequency, $\nu_{B}=2.83\times10^{6} B (G)$, with $s$ between 10 and 100." (Nature of the Detected Millimeter Flares)
   - fitting: _not stated_
   - validation: Compare derived range with photospheric magnetic field strengths from literature  
  > "The lower range of magnetic field strengths derived above is compatible with the photospheric value, suggesting an origin for the flare in a region close to the surface of the star." (Nature of the Detected Millimeter Flares)
5. **Measure quiescent stellar and inner dust excess flux density**: Fit a point source model using CASA uvmodelfit over all available ALMA observations excluding the flare intervals (E1, E2, E3), and subtract the expected photospheric flux at 1.3 mm.  
  > "We use `uvmodelfit` `CASA` to determine the flux density of the star over all of the available ALMA observations, excluding the time when the star was flaring (i.e., during events E1, E2, and E3)." (Constraints on Dust Emission from an Inner Debris Disk); "The result is $787\pm45$ $\mu$Jy, less than previous millimeter measurement but still in excess of the expected stellar photosphere by $257\pm34$ $\mu$Jy." (Constraints on Dust Emission from an Inner Debris Disk)
   - software: CASA, uvmodelfit
   - parameter: Exclude flaring intervals E1, E2, and E3  
  > "excluding the time when the star was flaring (i.e., during events E1, E2, and E3)." (Constraints on Dust Emission from an Inner Debris Disk)
   - assumption: Expected stellar photospheric flux at 1.3 mm is 0.53 mJy  
  > "The effective temperature of $\epsilon$ Eridani is $5039\pm126$ K (cite: Baines:2012), which implies a photospheric flux at 1.3 mm of $0.53$ mJy (cite: Backman:2009)." (Constraints on Dust Emission from an Inner Debris Disk)
   - fitting: CASA uvmodelfit point source fit to flare-excluded visibilities  
  > "We use `uvmodelfit` `CASA` to determine the flux density of the star over all of the available ALMA observations, excluding the time when the star was flaring (i.e., during events E1, E2, and E3)." (Constraints on Dust Emission from an Inner Debris Disk)
   - validation: Compare excess flux with extrapolated SED fits for the inner dust ring from Su et al. 2017 (~0.2-0.3 mJy)  
  > "Extrapolating the SED fits for the inner dust ring from (cite: Su:2017) yields a predicted flux at 1.3 mm of $\sim0.2-0.3$ mJy, strikingly consistent with what we determine here." (Constraints on Dust Emission from an Inner Debris Disk)

## Software

- **CASA** : All data analysis, continuum imaging (tclean), and visibility point-source modeling (uvmodelfit)  
  > "All analysis was performed using the Common Astronomy Software Package of `CASA` (cite: McMullin:2007). Imaging made use of the `tclean` task." (Observations); "We use the `uvmodelfit` task in `CASA` to fit a point source model to the visibilities" (ALMA 12-m Observations)
- **tclean** : Continuum imaging  
  > "Imaging made use of the `tclean` task." (Observations)
- **uvmodelfit** : Fitting point source models to millimeter visibilities for quiescent flux, light curves, spectral index, and linear polarization  
  > "We use the `uvmodelfit` task in `CASA` to fit a point source model to the visibilities" (ALMA 12-m Observations); "we have now developed an automatic pipeline approach that makes use of the `uvmodelfit` task in `CASA`." (Creating Light Curves and Identifying Flares); "To obtain the spectral index, we fit point source models using `uvmodelfit` in `CASA` to the millimeter visibilities of the upper and lower sidebands independently." (Characterizing Millimeter Flaring Emission)
- **astropy** : Software used in the study (specific role not stated in text)  
  > "`CASA` (cite: McMullin:2007), `astropy` (cite: astropy:2013; astropy:2018)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ACA combined visibility point source flux density | 776 | 103 | \muJy | 1 | Fitting a point source model to the combined visibilities yields a flux of $776 \pm 103$ $\mu$Jy. |
| ALMA 12-m combined visibility point source flux density | 794 | 45 | \muJy | 1 | We use the `uvmodelfit` task in `CASA` to fit a point source model to the visibilities and return a flux density of $794\pm45$ $\mu$Jy |
| Flare E1 peak flux density | 28 | 7 | mJy | 2 | with a peak flux density of 28 $\pm$ 7 mJy; reaching a peak flux density of $28\pm7$ mJy and peak luminosity of $3.4\pm 0.9 \times 10^{14}$ erg s$^{-1}$ Hz$^{-1}$. |
| Flare E1 peak luminosity | 3.4e14 | 0.9e14 | erg s^-1 Hz^-1 | 2 | The peak brightness of the largest flare is $3.4 \pm 0.9 \times 10^{14}$ erg s$^{-1}$Hz$^{-1}$; reaching a peak flux density of $28\pm7$ mJy and peak luminosity of $3.4\pm 0.9 \times 10^{14}$ erg s$^{-1}$ Hz$^{-1}$. |
| Flare E2 peak flux density | 14 | 3 | mJy | 2 | The other two flares reached lower peak flux densities of $14\pm 3$ mJy (labeled E2) and $9\pm 2$ mJy (labeled E3) |
| Flare E2 peak luminosity | 1.7e14 | 0.4e14 | erg s^-1 Hz^-1 | 2 | corresponding to peak luminosities of $1.7\pm 0.4 \times 10^{14}$ erg s$^{-1}$ Hz$^{-1}$ and $1.1\pm 0.2 \times 10^{14}$ erg s$^{-1}$ Hz$^{-1}$, respectively. |
| Flare E3 peak flux density | 9 | 2 | mJy | 2 | The other two flares reached lower peak flux densities of $14\pm 3$ mJy (labeled E2) and $9\pm 2$ mJy (labeled E3) |
| Flare E3 peak luminosity | 1.1e14 | 0.2e14 | erg s^-1 Hz^-1 | 2 | corresponding to peak luminosities of $1.7\pm 0.4 \times 10^{14}$ erg s$^{-1}$ Hz$^{-1}$ and $1.1\pm 0.2 \times 10^{14}$ erg s$^{-1}$ Hz$^{-1}$, respectively. |
| Flare E1 duration (t_1/2) | 7.9 | not stated | sec | 3 | Event E3 has the shortest duration of only 6.6 sec, while the E1 and E2 flares do not last much longer, at 7.9 and 9.0 sec, respectively.; / $\epsilon$ Eridani / E1 / 28 / 34 / 7.9$^\text{a}$ / 1.81 $\pm$ 1.94 / $>$0.08$\pm$0.12 / / |
| Flare E2 duration (t_1/2) | 9.0 | not stated | sec | 3 | Event E3 has the shortest duration of only 6.6 sec, while the E1 and E2 flares do not last much longer, at 7.9 and 9.0 sec, respectively.; / / E2 / 14 / 17 / 9.0$^\text{a}$ / 7.29 $\pm$ 2.89 / $>$-0.48 $\pm$ 0.15 / / |
| Flare E3 duration (t_1/2) | 6.6 | not stated | sec | 3 | Event E3 has the shortest duration of only 6.6 sec, while the E1 and E2 flares do not last much longer, at 7.9 and 9.0 sec, respectively.; / / E3 / 9 / 11 / 6.6$^\text{a}$ / -2.83 $\pm$2.33 / $>$-0.11$\pm$0.19 / / |
| Flare E1 spectral index (\alpha) | 1.81 | 1.94 | dimensionless | 3 | We find changes in the spectral index (F$_\nu\propto\nu^\alpha$) at the flare peak, with $\alpha$ = 1.81 $\pm$ 1.94; / $\epsilon$ Eridani / E1 / 28 / 34 / 7.9$^\text{a}$ / 1.81 $\pm$ 1.94 / $>$0.08$\pm$0.12 / / |
| Flare E2 spectral index (\alpha) | 7.29 | 2.89 | dimensionless | 3 | / / E2 / 14 / 17 / 9.0$^\text{a}$ / 7.29 $\pm$ 2.89 / $>$-0.48 $\pm$ 0.15 / / |
| Flare E3 spectral index (\alpha) | -2.83 | 2.33 | dimensionless | 3 | / / E3 / 9 / 11 / 6.6$^\text{a}$ / -2.83 $\pm$2.33 / $>$-0.11$\pm$0.19 / / |
| Flare E1 fractional linear polarization lower limit (|Q/I|) | >0.08 | 0.12 | dimensionless | 3 | and a lower limit on the fractional linear polarization $/Q/I/ =$ 0.08 $\pm$ 0.12.; / $\epsilon$ Eridani / E1 / 28 / 34 / 7.9$^\text{a}$ / 1.81 $\pm$ 1.94 / $>$0.08$\pm$0.12 / / |
| Flare E2 fractional linear polarization lower limit (|Q/I|) | >-0.48 | 0.15 | dimensionless | 3 | / / E2 / 14 / 17 / 9.0$^\text{a}$ / 7.29 $\pm$ 2.89 / $>$-0.48 $\pm$ 0.15 / / |
| Flare E3 fractional linear polarization lower limit (|Q/I|) | >-0.11 | 0.19 | dimensionless | 3 | / / E3 / 9 / 11 / 6.6$^\text{a}$ / -2.83 $\pm$2.33 / $>$-0.11$\pm$0.19 / / |
| Magnetic field strength in mm-emitting region | 0.8-8 | not stated | kG | 4 | This leads to an unbiased but large range of magnetic field strengths in the mm-emitting region of 0.8–8 kG. |
| Quiescent stellar flux density (excluding flares) | 787 | 45 | \muJy | 5 | The result is $787\pm45$ $\mu$Jy, less than previous millimeter measurement but still in excess of the expected stellar photosphere by $257\pm34$ $\mu$Jy. |
| Quiescent flux excess over stellar photosphere | 257 | 34 | \muJy | 5 | The result is $787\pm45$ $\mu$Jy, less than previous millimeter measurement but still in excess of the expected stellar photosphere by $257\pm34$ $\mu$Jy. |

## Qualitative findings

- First detection of millimeter flares from a Sun-like (K2V) star, epsilon Eridani.  
  > "This is the first time that flares have been detected from a Sun-like star at millimeter wavelengths." (Abstract)
- The three detected flares have short, symmetric Gaussian temporal profiles (t_1/2 < 10 s) with little exponential decay, similar to M dwarf millimeter flares.  
  > "The Gaussian fits reveal symmetric temporal structures and show that there is little exponential decay following the flare peak. This is similar to the structure of the millimeter flares reported from other M dwarfs." (Characterizing Millimeter Flaring Emission)
- Events E1 and E2 exhibit positive spectral indices, similar to millimeter solar flares and differing from M dwarf flares which show steeply negative spectral indices.  
  > "This positive spectral index is more similar to millimeter solar flares, differing from M dwarf flares also detected at millimeter wavelengths that exhibit steeply negative spectral indices." (Abstract); "In our new sample, only event E3 shows a similar negative spectral index. In contrast, events E1 and E2 exhibit positive $\alpha$ values." (Nature of the Detected Millimeter Flares)
- Two flare events are consistent with no net linear polarization, while event E2 shows marginally significant linear polarization.  
  > "We note that two flare events are consistent with no net linear polarization, and a third event (E2) is marginally significant." (Characterizing Millimeter Flaring Emission)
- Previous millimeter measurements of excess flux from epsilon Eridani likely included significant flaring emission, and the flare-excluded excess of 257 +/- 34 uJy is consistent with extrapolated inner dust ring SED predictions.  
  > "Given that the previous millimeter measurements are much in excess of what we report here, those values likely include significant flaring emission. Extrapolating the SED fits for the inner dust ring from (cite: Su:2017) yields a predicted flux at 1.3 mm of $\sim0.2-0.3$ mJy, strikingly consistent with what we determine here." (Constraints on Dust Emission from an Inner Debris Disk)

## Claim tuples

- H: Sun-like stars such as epsilon Eridani exhibit detectable flaring emission at millimeter wavelengths. | E: Fit point source models to each integration of archival ALMA 12-m and ACA Band 6 visibilities using CASA uvmodelfit, flagging >3 sigma events and verifying sideband agreement within 20%. | R: Detected three flares in the ALMA 12-m data with peak flux densities of 28 +/- 7 mJy (E1), 14 +/- 3 mJy (E2), and 9 +/- 2 mJy (E3), and durations t_1/2 of 7.9, 9.0, and 6.6 sec. | F: First detection of millimeter flares from a Sun-like star, with peak brightness >50x quiescent stellar luminosity and >10x brighter than solar millimeter flares. | **supported**
- H: Millimeter flares from the K2V star epsilon Eridani share spectral and temporal properties with solar and M dwarf millimeter flares. | E: Fit Gaussian profiles to flare light curves and fit point source models to upper/lower sidebands and XX/YY polarizations at flare peaks. | R: Flares have short durations (<10 sec) with symmetric profiles; E1 and E2 have positive spectral indices (1.81 +/- 1.94 and 7.29 +/- 2.89) while E3 is negative (-2.83 +/- 2.33); E2 has |Q/I| > -0.48 +/- 0.15. | F: Temporal structures are short and symmetric like M dwarf flares, but positive spectral indices in E1 and E2 are more similar to solar millimeter flares than M dwarf flares. | **supported**
- H: Millimeter flaring emission contributes to the apparent millimeter excess attributed to an unresolved inner debris disk around epsilon Eridani. | E: Fit a point source model with uvmodelfit to all ALMA visibilities excluding the flaring intervals E1, E2, and E3, and compare with expected photospheric flux and inner dust SED predictions. | R: Quiescent flux density is 787 +/- 45 uJy, representing an excess of 257 +/- 34 uJy above the 0.53 mJy photosphere, lower than previous millimeter measurements (1.2 +/- 0.3 and 1.08 mJy) and matching the ~0.2-0.3 mJy predicted for the inner dust ring. | F: Previous millimeter excess measurements likely included flaring emission; the flare-excluded excess matches predictions for the inner dust belt, though chromospheric and dust contributions remain unresolved. | **supported**

## Reasoning

- Why this data: epsilon Eridani is the closest Sun-like star hosting a tentative planet and debris disks, and has archival ALMA 12-m and ACA Band 6 observations originally targeting the outer debris disk.  
  > "Given that it is the closest Sun-like star to Earth that hosts a tentative planet along with both inner and outer debris disks, the $\epsilon$ Eridani system has been a frequent target for ALMA. Archival observations are available using Band 6 (center wavelength of 1.3 mm) from both the full 12-m array and ACA." (Observations)
- Why this method: Primary beam correction increases apparent noise at the edge of the image where the star is located (~18'' from pointing center), making image-plane significance difficult to judge; fitting visibilities directly at fine integration times captures short (<30 s) flares.  
  > "Because the primary beam correction is applied uniformly, it not only ‘upweights’ any real signals but also increases the apparent noise at the edges of the image (as can be seen in the right panel if Fig. 1) making it difficult to determine the uncertainty and judge significance levels. As a result, we choose to fit the visibilities directly to determine the stellar flux and search for any flare candidates" (ALMA 12-m Observations); "However, millimeter flares have so far proven to be short events (typically lasting $<30$ sec), so fine time resolution is needed in order to fully characterize their temporal behavior." (Creating Light Curves and Identifying Flares)
- Alternative: Measuring stellar flux and searching for flares in the primary-beam-corrected image plane was rejected in favor of direct visibility fitting because primary beam correction increases apparent noise at the beam edge.  
  > "Because the primary beam correction is applied uniformly, it not only ‘upweights’ any real signals but also increases the apparent noise at the edges of the image (as can be seen in the right panel if Fig. 1) making it difficult to determine the uncertainty and judge significance levels. As a result, we choose to fit the visibilities directly" (ALMA 12-m Observations)
- How they decided it was enough: _not stated_
- Limitation (authors): Shorter integration times imply higher rms noise, so fainter flares will not be detected.  
  > "Shorter integration times imply higher rms noise and fainter flares will not be detected." (Creating Light Curves and Identifying Flares)
- Limitation (authors): ACA has fewer and smaller (7-m) antennas, resulting in 3-5x higher rms noise per integration than the 12-m array, preventing detection of flares of this brightness in the ACA data.  
  > "with fewer antennas in the array and smaller antenna diameters (7-m for the ACA), the total collecting area is reduced and as a result the rms noise in each integration was a factor of $3-5\times$ higher than for the ALMA 12-m observations." (Creating Light Curves and Identifying Flares)
- Limitation (authors): Due to limited signal-to-noise, spectral index and fractional linear polarization lower limits can only be computed at the peak of the three flares, and lack of polarization calibration leads to large uncertainties.  
  > "Due to limited signal-to-noise, we are only able to compute the spectral index and lower limit on the fractional linear polarization at the peak of the three detected flares." (Characterizing Millimeter Flaring Emission); "Although there are large uncertainties due to the low signal-to-noise ratio and lack of polarization calibration" (Nature of the Detected Millimeter Flares)
- Limitation (authors): The 12-m ALMA beam (~1.6'' or ~5 AU) cannot spatially resolve the proposed inner dust belts from the central star, so quiescent flux contains both chromospheric and dust contributions.  
  > "The beam size in the 12-m ALMA observations is $\sim1.6\ensuremath{''}$ or $\sim5$ AU. The potential inner dust belt(s) have been proposed to extend from either 3–21 AU (cite: Greaves:2014) or 1.5–2 AU and 8–20 AU (cite: Backman:2009). In either of these two models, the inner dust would not be resolved from the central star by the existing ALMA observations." (Constraints on Dust Emission from an Inner Debris Disk)
- Caveat (inferred, ours): In the 12-m observations, the star is ~18 arcsec from the pointing center (at the edge of the primary beam), where primary beam attenuation, pointing errors, and off-axis instrumental polarization leakage are significant.
- Caveat (inferred, ours): uvmodelfit does not automatically apply primary beam attenuation correction when fitting visibilities off-axis unless accounted for, and the paper does not state how primary beam response at 18 arcsec off-axis was applied to the uvmodelfit visibility fluxes.
- Caveat (inferred, ours): Point source fitting with uvmodelfit on single 6-second integrations in a field containing extended debris disk emission could be affected by unmodeled disk structure if short baselines are not excluded or disk emission is not subtracted.
- Caveat (inferred, ours): There is a date discrepancy in the text for the ACA observations: the Abstract says '2016 October 24-November 23' while Section 2.1 says '2015 October 24 and 2015 November 23' for project 2016.1.00803.S.

## Reproducibility

- Data public (paper): Archival ALMA observations (#2013.1.00645.S and #2016.1.00803.S)  
  > "found in archival ALMA 12m and ACA observations at 1.33 mm" (Abstract); "This paper makes use of the following ALMA data: ADS/JAO.ALMA #2013.1.00645.S and #2016.1.00803.S." (Conclusions)
- Products in archive: _not stated_
- Missing: The custom automatic pipeline scripts wrapping CASA uvmodelfit are not released.
- Missing: Exact phase center offset / coordinates fixed or varied in uvmodelfit for the star at each epoch.
- Missing: Details on how primary beam attenuation (~18 arcsec off-axis in 12-m data, and across the 7-pointing ACA mosaic) was corrected in the visibility-domain uvmodelfit measurements.
- Missing: Exact time windows excluded for flares E1, E2, and E3 when computing the quiescent flux density (only scan ranges are given for E1, and exact UTC ranges for E2 and E3 are only shown in plots).
- Missing: CASA version and calibration procedure (pipeline vs manual) used prior to visibility fitting.
- Data volume (inferred): ~20-50 GB (calibrated measurement sets for 4.4 hr of 12-m and 5 hr of ACA Band 6 continuum/TDM observations)
- Score (inferred): 70/5, Archival ALMA project codes are clearly stated and the core method (CASA uvmodelfit per integration on upper/lower sidebands and XX/YY polarizations) is conceptually simple, but the custom pipeline scripts, exact stellar position fixing in uvmodelfit, off-axis primary beam correction in visibility space, and exact time windows for E2/E3 are not specified.
- Rediscovery candidate: yes, Both ALMA datasets (2013.1.00645.S and 2016.1.00803.S) are public in the archive, the core analysis relies on standard CASA tasks (tclean, uvmodelfit), and the main results are concrete numeric values (flare peak fluxes, durations, spectral indices, polarization limits, and quiescent stellar flux).

## Links

- Method: (cite: MacGregor:2018a) (Introduced the visibility point-source modeling approach to search for millimeter flares and generate light curves.)
- Method: (cite: MacGregor:2020) (Further developed visibility point-source modeling for millimeter flares and polarization/spectral index analysis.)
- Companion: (cite: Booth:2017) (Original publication and analysis of the 2013.1.00645.S ALMA 12-m observations of epsilon Eridani's northern debris disk arc.)
- Related: MUSCLES Treasury survey

## Checks

```json
{
 "quotes": 135,
 "quotes_ok": 135,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 9,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 20,
 "numeric_problems": 0,
 "fill": {
  "facts": 92,
  "stated": 67,
  "rate": 0.728
 },
 "evidence_ok": true
}
```

# Carina's pillars of destruction: the view from ALMA

`2020MNRAS.491..178K` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Klaassen, P. D. | arXiv: 1910.09164 | DOI: 10.1093/mnras/stz3012

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: Do the kinematics (velocity dispersions, internal motions, offsets from the parent cloud rim) of 13 Carina pillars discriminate between feedback simulations of pillar formation?  
  > "However, these models predict measurably different kinematics which provides testable discriminants." (abstract); "The overarching goal of this project is to quantify the kinematics of pillars in Carina, to determine whether the simulations are accurately predicting the effects of feedback on the local environment." (Introduction)
- Target **13 pillars in the Carina Nebula (Pillars 2, 3, 4, 5, 6, 8, 16, 17, 18, 20, 22, 44, 45)**: coordinates not stated (map centres are in a table not reproduced in the text)  
  > "in the following we use their pillar numbering scheme to refer to the pillars observed in this work." (Observations); "We adopt the 2.5 kpc distance estimate of (cite: Povich19), because of their more robust outlier rejection algorithms." (2.2 Systematic Uncertainties in ALMA data); z/distance 2.5 kpc  
  > "in the following we use their pillar numbering scheme to refer to the pillars observed in this work." (Observations); "We adopt the 2.5 kpc distance estimate of (cite: Povich19), because of their more robust outlier rejection algorithms." (2.2 Systematic Uncertainties in ALMA data); distance from Povich19 (Gaia-based distance)  
  > "in the following we use their pillar numbering scheme to refer to the pillars observed in this work." (Observations); "We adopt the 2.5 kpc distance estimate of (cite: Povich19), because of their more robust outlier rejection algorithms." (2.2 Systematic Uncertainties in ALMA data)

## Data provenance

- ALMA projects: 2016.1.00101.S
- bands: 230 GHz continuum plus CO J=2-1 lines (Band 6 not named in text)  
  > "and the 230 GHz continuum" (abstract)
- frequencies and spectral setup: CO, 13CO, C18O J=2-1; additional spectral windows for 233 GHz continuum, 13CS (J=5-4) and SiO (J=5-4); channel widths 0.079-0.158 km/s, continuum 1.87 GHz  
  > "we had additional spectral windows set to detect the 233 GHz continuum emission, as well as $^{13}$CS (J=5-4) and SiO (J=5-4)." (Observations); "| CO (J=2-1) | 6.59 | 5.03 | 43 | 0.60 | 0.079 |" (Table 1); "| Continuum | 6.25 | 4.71 | 75.8 | 6$\times 10^{-5}$ | 1.87 GHz |" (Table 1)
- continuum bandwidth: 1.87 GHz  
  > "| Continuum | 6.25 | 4.71 | 75.8 | 6$\times 10^{-5}$ | 1.87 GHz |" (Table 1)
- arrays: ACA 7m (stand-alone) plus Total Power (TP)  
  > "We present ALMA Compact Array (ACA) and Total Power (TP) observations of CO, $^{13}$CO and C$^{18}$O (J=2-1)" (Observations); "Despite using the ACA in stand alone mode, our interferometric data suffered from spatial filtering of the large scale emission." (3.1 Feathering the ACA and Total Power Data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Synthesised beam 6.59 x 5.03 arcsec, PA 43 deg (CO, feathered); 7.06 x 5.10 (13CO); 7.16 x 5.18 (C18O); 6.25 x 4.71 (continuum, ACA only)  
  > "| CO (J=2-1) | 6.59 | 5.03 | 43 | 0.60 | 0.079 |" (Table 1); "| $^{13}$CO (J=2-1) | 7.06 | 5.10 | 85.7 | 0.66 | 0.083 |" (Table 1); "| C$^{18}$O (J=2-1) | 7.16 | 5.18 | 83.3 | 0.49 | 0.083 |" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: Per-channel noise 0.60 (CO), 0.66 (13CO), 0.49 (C18O) Jy/beam; continuum 6e-5 Jy/beam (units as in Table 1)  
  > "| CO (J=2-1) | 6.59 | 5.03 | 43 | 0.60 | 0.079 |" (Table 1); "| Continuum | 6.25 | 4.71 | 75.8 | 6$\times 10^{-5}$ | 1.87 GHz |" (Table 1); "Our sensitivity limits suggest we would be able to detect 30 K gas in our beam at levels below 0.001 M$_\odot$ in CO if the emission fully filled the beam" (Virial Stability)
- time on source: _not stated_
- observing dates: ACA October and November 2016; TP mostly 19-21 October 2016 (Pillar 3 TP on 3 March 2017)  
  > "taken in October and November 2016 (ACA) and with the TP data primarily taken between October 19 and 21" (Observations); "with the exception of the TP data for Pillar 3, which was taken on 3 March, 2017." (Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (not stated)
- Line: 13CO J=2-1 (not stated)
- Line: C18O J=2-1 (not stated)
- Line: 13CS J=5-4 (not stated)
- Line: SiO J=5-4 (not stated)
- Other facility **Herschel**: 250, 160 and 70 micron context images used for pillar selection and figure backgrounds  
  > "250, 160 and 70 $\mu$m emission, with the black boxes highlighting the regions mapped with the ACA in this study." (Results)
- Other facility **Spitzer (IRAC archive)**: 8 micron images of each imaged region for comparison with the CO  
  > "archive 8 $\mu$m emission from each imaged region in the upper left panel" (Results)
- Other facility **MUSE (VLT)**: H-alpha and [SII] images and ionisation-front velocity maps from McLeod16, compared with ALMA CO for Pillars 44 and 45  
  > "we compare out ALMA observations to those obtained with MUSE in the study of (cite: McLeod16)." (2.3 Supplementary MUSE data)
- External data: O-star radial velocities used to colour stars in the context figure  
  > "the radial velocities of the surrounding O stars taken from the 2014 epoch measurements of (cite: Hanes18), and Table 2 of (cite: Kiminki18)" (Results) [from (cite: Hanes18); (cite: Kiminki18)]
- External data: Positions of Carina O stars without radial velocity measurements  
  > "The positions of the Carina O stars without radial velocity measurements, taken from (cite: Alexander16), are plotted as black stars for reference." (Results) [from (cite: Alexander16)]
- External data: Local standard of rest velocity of Carina (-20 km/s) and CO/13CO abundance ratio of 60  
  > "the local standard of rest velocity of -20 km s$^{-1}$ expected for Carina (cite: Rebolledo16)" (Pillar Velocities); "the abundance ratio expected at the distance of Carina (cite: Rebolledo16)" (Pillar Column Density and Mass) [from (cite: Rebolledo16)]
- External data: Distance to Carina of 2.5 kpc  
  > "We adopt the 2.5 kpc distance estimate of (cite: Povich19), because of their more robust outlier rejection algorithms." (2.2 Systematic Uncertainties in ALMA data) [from (cite: Povich19)]
- External data: Canonical CO abundance of 1e-4 with respect to H2  
  > "we use the canonical CO abundance of $10^{-4}$ presented in (cite: Frerking82)" (2.2 Systematic Uncertainties in ALMA data) [from (cite: Frerking82)]
- External data: Star-formation column density threshold (2e21 cm^-2) used for the integrated-intensity contour  
  > "This contour corresponds to an H$_2$ column density of $2\times10^{21}$ cm$^{-2}$" (Results) [from (cite: Clark14)]
- External data: Herschel-derived mass of Pillar 8 for comparison  
  > "The mass we derive from our CO observations for this region is about twice that derived by (cite: Roccatagliata13)" (Pillar 8) [from (cite: Roccatagliata13)]
- Simulation/model as data: Predicted pillar velocity dispersions, internal flows and ordered motions from SPH simulations of Dale12II, Gritschneder09 and Gritschneder10 (Table 2) compared with the observations  
  > "The predictions of these models are summarised in Table 2." (Comparisons to Models); "Both use smooth particle hydrodynamics (SPH) codes with 1-2$\times10^6$ particles" (Introduction)

## Processing

### Calibration

- pipeline or manual: Pipeline reduced  
  > "All data were pipeline reduced in CASA 4.7" (Observations)
- casa version: CASA 4.7 (pipeline); CASA 5.4 (re-imaging of ACA 7m mosaics)  
  > "All data were pipeline reduced in CASA 4.7" (Observations); "Because of the bug in CASA 4.7 with respect to creating mosaics, the ACA 7m data were re-mosaiced (re-imaged) in CASA 5.4." (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: less than 6% (used as upper envelope in mass and column density)  
  > "in all cases the flux calibration uncertainty was less than 6%." (2.2 Systematic Uncertainties in ALMA data)
- self calibration: None applied  
  > "No further self-calibration was applied because the continuum emission was not well detected in all mosaics." (Observations)

### Imaging

- task: CASA feather for ACA+TP combination of CO and isotopologue windows  
  > "To feather the data, both datasets were first imaged on the same velocity grid, and the TP data was spatially regridded using the ACA data as a template." (3.1 Feathering the ACA and Total Power Data)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Feather of ACA 7m and TP; TP converted to the flux scale of the ACA data before feathering  
  > "The TP data was then converted to the same flux scale as the ACA data, and the two data cubes were feathered together." (3.1 Feathering the ACA and Total Power Data)
- smoothing: _not stated_
- final beam: 6.59 x 5.03 arcsec at PA 43 deg (CO, feathered)  
  > "| CO (J=2-1) | 6.59 | 5.03 | 43 | 0.60 | 0.079 |" (Table 1)
- final rms: 0.60 Jy/beam per channel (CO, feathered); 0.66 (13CO); 0.49 (C18O)  
  > "| CO (J=2-1) | 6.59 | 5.03 | 43 | 0.60 | 0.079 |" (Table 1); "| $^{13}$CO (J=2-1) | 7.06 | 5.10 | 85.7 | 0.66 | 0.083 |" (Table 1)

### Inherited from earlier work

- Pillar numbering scheme  
  > "in the following we use their pillar numbering scheme to refer to the pillars observed in this work." (Observations) [from (cite: Hartigan15)]
- Optical depth of the CO emission computed with equation 1 of Choi93  
  > "This was done using equation 1 of (cite: Choi93)." (Pillar Column Density and Mass) [from (cite: Choi93)]
- CO/C18O emission and abundance ratios used when 13CO is optically thick  
  > "the emission and abundance ratios between the CO and C$^{18}$O was used instead (cite: WR94)." (Pillar Column Density and Mass) [from (cite: WR94)]
- Optical-depth correction in the column density equation  
  > "the final portion is the correction for optical depth (cite: Mangum15)" (Pillar Column Density and Mass) [from (cite: Mangum15)]
- Mean molecular weight of 2.8 times the mass of a hydrogen atom  
  > "assuming a mean molecular weight of 2.8 times the mass of a hydrogen atom (cite: Kauffmann08)" (Pillar Column Density and Mass) [from (cite: Kauffmann08)]
- Canonical CO abundance of 1e-4  
  > "we use the canonical CO abundance of $10^{-4}$ presented in (cite: Frerking82)" (2.2 Systematic Uncertainties in ALMA data) [from (cite: Frerking82)]
- Clump identification with Fellwalker  
  > "we determined the peak positions of each CO emission peak" (Separations Between Intensity Peaks) [from (cite: fellwalker)]

### Not stated but needed to reproduce (our reading)

- Flux scale factor and procedure used to convert the TP data to the ACA flux scale, and feather parameters (e.g. sdfactor, uv cut)
- Imaging parameters for the ACA re-mosaic in CASA 5.4: weighting/robust, cell size, image size, deconvolver, clean threshold, masking, primary-beam correction
- Calibrator names, time on source and PWV (only in a table not reproduced in the text)
- Continuum imaging and which channels were line-free / how continuum was subtracted
- Fellwalker parameters (noise, thresholds) and the minimum-spanning-tree implementation
- How the velocity dispersion, FWHM, and mean velocities were computed (moment maps, fits, masks) and the virial mass formula, core radii and geometry
- Map centres and pointing coordinates of each pillar
- How the 30 K excitation temperature was chosen and the CO partition function treatment
- How the 10.4 Jy/beam km/s contour and 10 sigma limits were defined (rms of integrated maps)
- Uncertainty estimation for masses and column densities beyond the systematic terms

## Analysis recipe

1. **Calibrate and re-image ACA data**: Pipeline calibration in CASA 4.7; ACA 7m mosaics re-imaged in CASA 5.4 because of a mosaicking bug; no self-calibration  
  > "Because of the bug in CASA 4.7 with respect to creating mosaics, the ACA 7m data were re-mosaiced (re-imaged) in CASA 5.4." (Observations); "No further self-calibration was applied because the continuum emission was not well detected in all mosaics." (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Combine ACA and Total Power data**: Image both on the same velocity grid, regrid TP to the ACA template, scale TP to the ACA flux scale, feather the cubes (CO and isotopologues only)  
  > "To feather the data, both datasets were first imaged on the same velocity grid, and the TP data was spatially regridded using the ACA data as a template." (3.1 Feathering the ACA and Total Power Data); "The TP data was then converted to the same flux scale as the ACA data, and the two data cubes were feathered together." (3.1 Feathering the ACA and Total Power Data)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared ACA-only, feathered and TP-only cubes for Pillar 8 to show improved sensitivity to large-scale structure  
  > "highlight how the combination of ACA and TP data improves the sensitivity to large scale structure in the CO emission." (3.1 Feathering the ACA and Total Power Data)
3. **Clip velocity range and make moment maps**: Clip cubes to -30 to +10 km/s to remove foreground/background components; make integrated intensity and intensity-weighted velocity (moment 1) maps  
  > "we clipped the velocity ranges of the cubes to contain only emission between -30 km s$^{-1}$ and + 10 km s$^{-1}$" (Results); "moment one (intensity weighted velocity) maps of the $^{12}$CO in each region" (Results)
   - parameter: velocity window -30 to +10 km/s  
  > "we clipped the velocity ranges of the cubes to contain only emission between -30 km s$^{-1}$ and + 10 km s$^{-1}$" (Results)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive optical depth and CO column density**: Per channel where 13CO exceeds 6 sigma, compute CO optical depth with 13CO (or C18O when tau>60), then compute column density with an optical-depth correction at fixed excitation temperature  
  > "For every channel in each map where the $^{13}$CO emission was above six sigma we calculated the optical depth of the CO" (Pillar Column Density and Mass); "When the calculated optical depth was greater than 60, generally C$^{18}$O was detected" (Pillar Column Density and Mass)
   - parameter: 13CO detection threshold of six sigma  
  > "A cutoff of six sigma was used in order to ensure a robust detection in all isotopologues used in the calculation." (Pillar Column Density and Mass)
   - parameter: Excitation temperature 30 K  
  > "given an excitation temperature of 30 K" (Pillar Column Density and Mass)
   - assumption: [CO]/[13CO] = 60 abundance ratio expected at the distance of Carina  
  > "the abundance ratio expected at the distance of Carina (cite: Rebolledo16)" (Pillar Column Density and Mass)
   - assumption: CO abundance 1e-4 relative to H2  
  > "Using a CO abundance of 10$^{-4}$ with respect to H$_2$" (Pillar Column Density and Mass)
   - assumption: Distance 2.5 kpc  
  > "under the assumption of T = 30 K, and d= 2.5 kpc." (Table 2)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compute pillar gas masses**: Convert column density per pixel to number of molecules and mass, sum over pixels above the six sigma threshold  
  > "assuming a mean molecular weight of 2.8 times the mass of a hydrogen atom (cite: Kauffmann08), we calculate the mass in each pixel" (Pillar Column Density and Mass); "which is then summed across each map (above the six $\sigma$ threshold) to give the total gas mass in each pillar." (Pillar Column Density and Mass)
   - assumption: Mean molecular weight 2.8 m_H; T = 30 K; d = 2.5 kpc  
  > "assuming a mean molecular weight of 2.8 times the mass of a hydrogen atom (cite: Kauffmann08)" (Pillar Column Density and Mass)
   - fitting: _not stated_
   - validation: Compared Pillar 8 mass with the Herschel-derived mass (factor of about two higher)  
  > "The mass we derive from our CO observations for this region is about twice that derived by (cite: Roccatagliata13)" (Pillar 8)
6. **Find CO peaks and measure their separations**: Fellwalker on CO integrated intensity maps to locate peaks, then a minimum spanning tree of peak separations, compared with the Jeans length of 30 K gas and the beam  
  > "we determined the peak positions of each CO emission peak, and, using a minimum spanning tree analysis, determined the separations of these peaks in all pillars." (Separations Between Intensity Peaks); "Also plotted here are, in red, the resolution of our observations, and in black, the Jeans length of 30 K gas." (Separations Between Intensity Peaks)
   - software: Fellwalker
   - assumption: CO emission used as a proxy for cores because the dust continuum was poorly detected (7 pillars)  
  > "the dust continuum in the observed pillars was poorly detected, with faint detections in only 7 pillars." (Separations Between Intensity Peaks)
   - fitting: _not stated_
   - validation: _not stated_
7. **Measure pillar velocities and dispersions**: Mean velocity of CO per pillar from moment 1 maps, comparison of mean CO and 13CO velocities (linear relation) to test internal vs surface motions, mean velocity dispersion of CO compared with the thermal line width at 30 K  
  > "comparing the mean velocity of the CO in each pillar to the $^{13}$CO shows no significant differences between the regions probed by these isotopologues" (Pillar Velocities); "In all cases, the CO emission has a low velocity dispersion, but remaining higher than what is expected for a thermally supported line at T = 30 K." (Virial Stability)
   - fitting: _not stated_
   - validation: Compared with MUSE ionisation-front velocities for Pillars 44 and 45  
  > "what appeared as a single pillar in the MUSE data appears as two components in the ALMA data" (Comparisons to Models)
8. **Virial analysis of C18O cores**: Compare core mass from C18O emission to virial mass for each C18O-detected core  
  > "Where C$^{18}$O is detected, we performed a virial analysis of the emission, and find that most cores are unstable against virial collapse" (Virial Stability)
   - fitting: _not stated_
   - validation: _not stated_
9. **Compare kinematics with feedback simulations**: Compare observed velocity dispersions, ordered flows and internal flows with predictions summarised from Dale12II, Gritschneder09 and Gritschneder10  
  > "There is evidence for some pillars having ordered flows, but the incidence rate is roughly 50%, and there is no evidence for internal flows" (Comparisons to Models)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7 (pipeline), 5.4 (re-imaging); feather task: Pipeline calibration, re-mosaicking of ACA data, feathering ACA with TP  
  > "All data were pipeline reduced in CASA 4.7" (Observations); "the ACA 7m data were re-mosaiced (re-imaged) in CASA 5.4." (Observations)
- **Fellwalker** : Identify peaks in CO integrated intensity maps  
  > "we determined the peak positions of each CO emission peak" (Separations Between Intensity Peaks)
- **spectralcube** : Acknowledged as used in the research (specific use not stated)  
  > "This research made use of spectralcube, a library for astronomical spectral data cubes" (Acknowledgements)
- **pyspeckit** : Acknowledged as used in the research (specific use not stated)  
  > "This research made use of pyspeckit, an open-source spectral analysis and plotting package for Python" (Acknowledgements)
- **Astropy** : Acknowledged as used in the research  
  > "This research made use of Astropy, a community-developed core Python package for Astronomy" (Acknowledgements)
- **APLpy** : Plotting  
  > "This research made use of APLpy, an open-source plotting package for Python" (Acknowledgements)
- **NumPy** : Acknowledged as used in the research  
  > "This research made use of NumPy (cite: numpy)" (Acknowledgements)
- **matplotlib** : Plotting  
  > "This research made use of matplotlib, a Python library for publication quality graphics" (Acknowledgements)
- **IPython** : Acknowledged as used in the work  
  > "This work made use of the IPython package (cite: ipython)" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Pillar 2 CO gas mass | 501 | 30 | Msun | 5 | / 2 / 501 / 30 / 8.3 / 0.7 / 51 / 3 / -18.83 / |
| Pillar 3 CO gas mass | 187 | 11 | Msun | 5 | / 3 / 187 / 11 / 6.5 / 0.5 / 45 / 3 / -1.04 / |
| Pillar 4 CO gas mass | 203 | 12 | Msun | 5 | / 4 / 203 / 12 / 2.8 / 0.3 / 50 / 3 / -26.02 / |
| Pillar 5 CO gas mass | 22 | 1 | Msun | 5 | / 5 / 22 / 1 / 2.2 / 0.2 / 42 / 3 / -22.38 / |
| Pillar 6 CO gas mass | 48 | 3 | Msun | 5 | / 6 / 48 / 3 / 6.1 / 0.4 / 46 / 3 / -9.61 / |
| Pillar 8 CO gas mass | 1386 | 83 | Msun | 5 | / 8 / 1386 / 83 / 12.4 / 1.2 / 57 / 3 / -14.77 / |
| Pillar 16 CO gas mass | 124 | 8 | Msun | 5 | / 16 / 124 / 8 / 2.9 / 0.3 / 49 / 3 / -19.53 / |
| Pillar 17 CO gas mass | 56 | 3 | Msun | 5 | / 17 / 56 / 3 / 1.3 / 0.1 / 35 / 2 / -20.12 / |
| Pillar 18 CO gas mass | 124 | 7 | Msun | 5 | / 18 / 124 / 7 / 4.0 / 0.4 / 63 / 4 / -19.71 / |
| Pillar 20 CO gas mass | 449 | 27 | Msun | 5 | / 20 / 449 / 27 / 12.9 / 1.0 / 88 / 5 / -13.41 / |
| Pillar 22 CO gas mass | 89 | 5 | Msun | 5 | / 22 / 89 / 5 / 1.8 / 0.2 / 39 / 2 / -7.51 / |
| Pillar 44 CO gas mass | 101 | 6 | Msun | 5 | / 44 / 101 / 6 / 4.3 / 0.4 / 86 / 5 / -8.91 / |
| Pillar 45 CO gas mass | 25 | 1 | Msun | 5 | / 45 / 25 / 1 / 1.0 / 0.1 / 21 / 1 / -5.48 / |
| Mean pillar column density (order of magnitude) | 1e20 | not stated | cm^-2 | 4 | we find mean pillar column densities of order 1$\times10^{20}$ cm$^{-2}$ |
| Systematic offset between CO and 13CO mean velocities (y-intercept) | 0.9 | 0.8 | km/s | 7 | shows a minimal systematic velocity offset of 0.9$\pm$0.8 km s$^{-1}$ between the CO and $^{13}$CO |
| Velocity difference between cloud rim and tip of main body of Pillar 5 | 11 | not stated | km/s | 7 | That there is an $\sim$ 11 km s$^{-1}$ velocity difference between the cloud rim and the tip of the main body of the pillar |
| Expansion time of the Trumpler 15 cloud rim (Pillars 20 and 22) | 30000 | not stated | yr | 7 | the cloud has been expanding for roughly 30 000 years |
| Contour of CO integrated intensity corresponding to N(H2) = 2e21 cm^-2 | 10.4 | not stated | Jy/beam km/s | 4 | This contour corresponds to an H$_2$ column density of $2\times10^{21}$ cm$^{-2}$ |

## Qualitative findings

- Pillar velocity dispersions are generally below 1 km/s and the CO and 13CO mean velocities show no significant offset, implying little bulk internal motion  
  > "We generally find pillar velocity dispersions of $<$ 1 km s$^{-1}$ and that the outer few layers of molecular emission in these pillars show no significant offsets from each other" (abstract)
- Some pillars are offset in velocity from their parent cloud rim and some are not, suggesting stochastic development  
  > "There are instances where the pillars are offset in velocity from their parental cloud rim, and some with no offset, hinting at a stochastic development of these motions." (abstract)
- Several apparent single pillars (e.g. 5 and 45) are chance alignments of distinct velocity components along the line of sight  
  > "It is only through analyses such as these, with the velocity information of the pillar structures, that we are able to distinguish these types of chance alignments." (Pillar Velocities)

## Claim tuples

- H: Pillar kinematics can discriminate between competing feedback simulations | E: ACA+TP CO, 13CO, C18O J=2-1 survey of 13 Carina pillars compared with predictions of Dale12II, Gritschneder09 and Gritschneder10 | R: Velocity dispersions below 1 km/s, no internal flows, ordered flows in about 50% of pillars | F: The observations are most consistent with the Dale12II models | **supported**
- H: Surface and interior gas of the pillars move differently | E: Compared mean CO and 13CO velocities for each pillar | R: No significant differences; systematic offset 0.9+/-0.8 km/s | F: No significant internal motions in the pillars | **supported**
- H: Pillar cores seen in C18O are gravitationally bound and spaced by Jeans lengths | E: Virial analysis of C18O cores and minimum spanning tree separation of CO peaks versus the Jeans length | R: Most C18O cores are virially unstable; core separations are 1-2 Jeans lengths | F: Embedded cores are likely to collapse | **partially**
- H: Pillar masses and column densities span a range sufficient for star formation | E: Optical-depth corrected CO column density and mass for 13 pillars | R: Masses of order 30-2000 Msun; mean column densities of a few 1e20 cm^-2 | F: Pillars have a wide range of masses depending on size | **supported**

## Reasoning

- Why this data: A multi-pillar, spatially and spectrally resolved survey in a single environment is needed to constrain general ionised feedback processes  
  > "To do that, a moderately high resolution survey of multiple pillars in a single environment is required." (Introduction)
- Why this method: TP added because ACA alone filters out large-scale emission; CO isotopologues used to correct for optical depth  
  > "Despite using the ACA in stand alone mode, our interferometric data suffered from spatial filtering of the large scale emission." (3.1 Feathering the ACA and Total Power Data); "Because we observed multiple CO isotopologues in the same transition, we are able to calculate the optical depth of the CO emission." (Pillar Column Density and Mass)
- Alternative: Canonical Carina distance of 2.3 kpc rejected in favour of Gaia-based 2.5 kpc  
  > "The canonical distance has generally been accepted as 2.3 kpc (cite: Smith06b)" (2.2 Systematic Uncertainties in ALMA data)
- Alternative: Lower CO abundance of order 5e-6 (low extinction regions) not adopted; canonical 1e-4 used  
  > "we use the canonical CO abundance of $10^{-4}$ presented in (cite: Frerking82)" (2.2 Systematic Uncertainties in ALMA data)
- How they decided it was enough: _not stated_
- Limitation (authors): Distance uncertainty scales masses and column densities as distance squared  
  > "vary with distance squared" (2.2 Systematic Uncertainties in ALMA data)
- Limitation (authors): CO abundance uncertainty up to a factor of 3 scales linearly into column densities and masses  
  > "point out that uncertainties in the CO abundance can be up to a factor of 3" (2.2 Systematic Uncertainties in ALMA data)
- Limitation (authors): Dust continuum poorly detected, so CO peaks serve as proxy for cores  
  > "the dust continuum in the observed pillars was poorly detected, with faint detections in only 7 pillars." (Separations Between Intensity Peaks)
- Caveat (inferred, ours): Fixed T_ex = 30 K and a single CO abundance applied to all pillars without per-pillar temperature estimates; masses depend strongly on these.
- Caveat (inferred, ours): No quantitative statistic (e.g. likelihood or chi-square) is used to discriminate between the three models; the comparison is qualitative against three coarse predictions.
- Caveat (inferred, ours): Imaging, feathering and virial analysis settings are largely unspecified, limiting reproduction of the cubes and core masses.
- Caveat (inferred, ours): Velocity dispersion is compared with a thermal width only; contributions from unresolved beam smoothing (about 6-7 arcsec, around 0.07 pc at 2.5 kpc) are not discussed.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: TP-to-ACA flux scaling and feather settings
- Missing: CASA 5.4 imaging parameters (weighting, cell, size, cleaning)
- Missing: Fellwalker parameters and MST implementation
- Missing: Virial mass formula, core sizes and mask definitions
- Missing: Map centres, calibrator and time-on-source details (in tables not reproduced in the text)
- Data volume (inferred): ACA 7m plus TP cubes for 13 mosaics in three CO lines: tens of GB in the archive (rough guess).
- Score (inferred): 2/5, ALMA project code is given, but imaging, feathering, mask and virial recipes are largely unspecified; the main kinematic results are qualitative or tabulated only per pillar.
- Rediscovery candidate: no, Public status of data is not stated in the text and the recipe lacks key imaging/feather/virial parameters; main conclusions are qualitative.

## Links

- Method: (cite: Choi93) (Equation 1 used for CO optical depth)
- Method: (cite: Mangum15) (Optical-depth correction in the column density equation)
- Method: (cite: fellwalker) (Clump-finding algorithm for CO peaks)
- Companion: (cite: Klaassen14) (Earlier spatially and spectrally resolved study of a single large Carina pillar)
- Companion: (cite: McLeod16) (MUSE observations of pillar ionisation fronts, compared with ALMA CO)
- Companion: (cite: Rebolledo16) (Lower-resolution CO(J=1-0) study of Carina; source of LSR velocity and abundance ratio)
- Related: Reiter et al. in prep (outflows and H-alpha of Carina pillars)

## Checks

```json
{
 "quotes": 132,
 "quotes_ok": 132,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 18,
 "numeric_problems": 0,
 "fill": {
  "facts": 113,
  "stated": 76,
  "rate": 0.673
 },
 "evidence_ok": true
}
```

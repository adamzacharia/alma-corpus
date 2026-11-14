# Molecular Gas in the X-Ray Bright Group NGC 5044 as Revealed by ALMA

`2014ApJ...792...94D` | The Astrophysical Journal 2014 | first author: David, Laurence P. | arXiv: 1407.3235 | DOI: 10.1088/0004-637X/792/2/94

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, galaxy_clusters_and_sz
- Question: What are the mass, kinematics and confinement of the molecular gas in the cooling-flow group NGC 5044, and how does it relate to the hot gas, dust and AGN?  
  > "Our results concerning the mass and kinematics of the observed molecular structures and correlations between the molecular gas, dust, H$\alpha$ filaments and hot gas are presented in $\S 3$." (Introduction)
- Target **NGC 5044**: coordinates RA=13:15:23.97, Dec-16.23.07.5  
  > "A single pointing was made towards the center of NGC 5044 (RA=13:15:23.97, Dec-16.23.07.5) on 2012 January 13." (Data Reduction); "We adopt a systemic velocity of 2758 km s$^{-1}$ for NGC 5044 and a luminosity distance of 31.2 Mpc (Tonry et al. 2001)" (Data Reduction); z/distance D_L = 31.2 Mpc; systemic velocity 2758 km/s; 1" = 150 pc  
  > "A single pointing was made towards the center of NGC 5044 (RA=13:15:23.97, Dec-16.23.07.5) on 2012 January 13." (Data Reduction); "We adopt a systemic velocity of 2758 km s$^{-1}$ for NGC 5044 and a luminosity distance of 31.2 Mpc (Tonry et al. 2001)" (Data Reduction); distance from Tonry et al. 2001  
  > "A single pointing was made towards the center of NGC 5044 (RA=13:15:23.97, Dec-16.23.07.5) on 2012 January 13." (Data Reduction); "We adopt a systemic velocity of 2758 km s$^{-1}$ for NGC 5044 and a luminosity distance of 31.2 Mpc (Tonry et al. 2001)" (Data Reduction)

## Data provenance

- ALMA projects: 2011.0.00735.S
- bands: Band 6 (1.3 mm), CO(2-1)  
  > "One of the spectral windows was centered on the CO(2-1) line (1.3-mm band) at the systemic velocity of NGC 5044" (Data Reduction)
- frequencies and spectral setup: 4 spectral windows, 1875 MHz each, 3840 channels of 488.28 kHz; one on CO(2-1), three line-free continuum windows; 0.64 km/s resolution  
  > "Each spectral window spanned a total bandwidth of 1875 MHz and was split into 3840 channels so that each channel had a width of 488.28125 kHz." (Data Reduction); "The other three spectral windows (229.336-231.211 GHz, 241.270-243.145 GHz and 242.853-244.728 GHz) covered line-free regions" (Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.4" by 2.2" FWHM (210 by 330 pc)  
  > "The synthesized beam attained in our cycle 0 ALMA observation was 1.4$^{\prime\prime}$ by 2.2$^{\prime\prime}$ FWHM (210 by 330 pc)." (Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: 4 sigma surface brightness limit 0.16 Jy/beam (in 50 km/s bins); mass limit 3e5 Msun  
  > "We detect 24 GMAs above a surface brightness limit of 0.16 Jy beam$^{-1}$" (4.1 Source of the Molecular gas)
- time on source: 29 min on source (1.0 hr observation)  
  > "The observation spanned 1.0 hr, for a total on-source integration time of 29 min." (Data Reduction)
- observing dates: 2012 January 13  
  > "A single pointing was made towards the center of NGC 5044 (RA=13:15:23.97, Dec-16.23.07.5) on 2012 January 13." (Data Reduction)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (not stated)
- Other facility **IRAM 30m**: CO(2-1) spectrum for comparison of total flux  
  > "we also show in Fig.1 the IRAM 30m CO(2-1) spectrum" (Results)
- Other facility **Chandra ACIS**: X-ray image and hot gas pressure  
  > "The unsharp masked 0.5-2.0 keV *Chandra* ACIS image from David et al. (2009) is shown in Fig. 11" (Results)
- Other facility **HST WFPC2**: F791W image for dust extinction map  
  > "This map was created based on a F791W image obtained with the WFPC2 Planetary Camera." (Results)
- External data: GMRT flux densities at 235 and 610 MHz (229 mJy and 39 mJy)  
  > "the total flux densities (central point source plus extended emission) for 5044 at 235 MHz and 610 MHz from GMRT data are 229 mJy and 39 mJy (Giacintucci et al. 2008)" (The Central AGN and Absorption Feature) [from Giacintucci et al. 2008]
- External data: Star formation rate 0.073 Msun/yr from GALEX and WISE  
  > "The star formation rate in NGC 5044 based on *GALEX* and *WISE* data is 0.073 M$_{\odot}$ yr$^{-1}$ (Werner et al. 2014)." (Effects of Star Formation) [from Werner et al. 2014]
- External data: Cavity power 6e42 erg/s  
  > "The cavity power in NGC 5044 is ${P_{cav}=6 \times 10^{42}}$ erg s$^{-1}$ (David et al. 2009)" (Cloud Dynamics) [from David et al. 2009]

## Processing

### Calibration

- pipeline or manual: Calibrated with CASA by the ALMA observatory  
  > "The data were calibrated using the software package CASA by the ALMA observatory." (Data Reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Delivered calibrated data used, but own continuum subtraction and imaging performed  
  > "we performed our own continuum subtraction in the CO(2-1) line and made channel maps at our own desired velocity resolutions and weightings of the visibility data." (Data Reduction)
- flux calibrator: Titan (flux), 3C 279 (bandpass), J1337-129 (gain)  
  > "The quasar 3C 279 served as the bandpass calibrator and Titan as the absolute flux (primary) calibrator." (Data Reduction)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Own continuum subtraction using line-free spectral windows  
  > "covered line-free regions to measure the continuum emission of NGC 5044, necessary for subtracting any continuum emission at the frequency of the CO(2-1) line." (Data Reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Velocity binning 10-100 km/s; 50 km/s chosen for detection  
  > "We found that a bin width of 50 km s$^{-1}$ optimized the signal-to-noise of the emission lines." (Results)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Molecular mass relation and Xco = 2e20  
  > "The molecular mass was computed using the relation in Bolatto et al. (2013)," (Results) [from Bolatto et al. (2013)]
- Linewidth-size relation for absorber size  
  > "Assuming the linewidth-size relation in Solomon et al. (1987), we obtain a size for the absorbing cloud of 27 pc" (The Central AGN and Absorption Feature) [from Solomon et al. (1987)]

### Not stated but needed to reproduce (our reading)

- Weighting scheme / robust value and tclean/clean parameters for the cubes
- CASA version
- Cell size and image size
- Line-free channels or fit order used for continuum subtraction
- How the 24 structures were delineated and spectral extraction apertures
- Flux-scale uncertainty
- Integration regions for each GMA
- Derivation of GMC density and pressure estimates and X-ray gas values

## Analysis recipe

1. **Continuum subtraction and cube creation**: Own continuum subtraction and channel maps with chosen velocity resolution and weighting  
  > "we performed our own continuum subtraction in the CO(2-1) line and made channel maps at our own desired velocity resolutions and weightings of the visibility data." (Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Detect molecular structures**: Bin cube into 50 km/s slices and identify structures above 4 sigma within the central 2.5 kpc where primary beam response >0.3  
  > "A total of 24 molecular structures are detected with a CO(2-1) surface brightness exceeding $4 \sigma$ within the central 2.5 kpc (16.7$^{\prime\prime}$) where the primary beam response is greater than 0.3." (Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit spectra and derive molecular masses**: Gaussian fits to spectra in 10 km/s channels; mass from Bolatto et al. relation  
  > "The results shown in Table 1 were derived by fitting spectra binned into 10 km s$^{-1}$ channels." (Results)
   - assumption: Xco = 2e20 cm^-2 (K km/s)^-1; CO(2-1)/CO(1-0) flux density ratio 3.2  
  > "We assume a CO(2-1) to CO (1-0) flux density ratio of 3.2" (Results)
   - fitting: Gaussian profile; double Gaussian for GMA 18 at 1 km/s resolution  
  > "Fitting a double Gaussian model yields a mean velocity, linewidth and molecular mass for the narrow-line component" (Results)
   - validation: _not stated_
4. **Size, density, virial parameter of resolved GMAs**: 2D Gaussian fits to GMAs 11, 13, 18; deconvolved radius; surface and volume density; virial parameter  
  > "Using the CASA task *imfit*, we fit 2D Gaussians to GMAs 11, 13 and 18" (The central region)
   - software: CASA imfit
   - assumption: n_H2 = 100 cm^-3 for true GMCs  
  > "Assuming an average density of $n_{H2}=100$ cm$^{-3}$ for true GMCs, the average GMC volume filling factor for the three GMAs is 15%." (The central region)
   - fitting: 2D Gaussian  
  > "Using the CASA task *imfit*, we fit 2D Gaussians to GMAs 11, 13 and 18" (The central region)
   - validation: _not stated_
5. **Central continuum source and absorption**: imfit point-source check, flux in line-free region, Gaussian fit to absorption in a 2x2 arcsec extraction  
  > "Fitting a Gaussian profile to the absorption feature gives a mean velocity of $260.3 \pm 0.8$ km s$^{-1}$ and a linewidth of $5.2 \pm 0.8$ km s$^{-1}$." (The Central AGN and Absorption Feature)
   - software: CASA imfit
   - fitting: Gaussian  
  > "Fitting a Gaussian profile to the absorption feature gives a mean velocity of $260.3 \pm 0.8$ km s$^{-1}$ and a linewidth of $5.2 \pm 0.8$ km s$^{-1}$." (The Central AGN and Absorption Feature)
   - validation: Smaller extraction regions give the same 30% absorbed fraction  
  > "found that 30% of the continuum flux is absorbed at line-center in all spectra" (The Central AGN and Absorption Feature)

## Software

- **CASA** : Calibration, continuum subtraction, imaging, imfit  
  > "The data were calibrated using the software package CASA by the ALMA observatory." (Data Reduction)
- **GALFIT** : Two-component Sersic fit to HST image for dust map  
  > "The two-dimensional surface brightness distribution of the galaxy was fit with two Sersic components using GALFIT (Peng et al. 2002; 2010)." (Correlations between the molecular gas, H$\alpha$ filaments, dust and hot gas)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of molecular structures | 24 | not stated | dimensionless | 2 | detected 24 molecular structures within the central 2.5 kpc |
| Total molecular mass | 5.1e7 | not stated | Msun | 3 | The total molecular mass of the GMAs listed in Table 1 is $5.1 \times 10^7$ M$_{\odot}$ |
| Narrow component of GMA 18 linewidth | 5.5 | not stated | km/s | 3 | 58.7 km s$^{-1}$, 5.5 km s$^{-1}$ and ${M_{mol}=8.7 \times 10^5}$ M$_{\odot}$ |
| Deconvolved radius of GMA 18 | 120 | 12 | pc | 4 | $115 \pm 25$, $140 \pm 15$ and $120 \pm 12$ pc for GMAs 11, 13 and 18 |
| GMC volume filling factor | 15% | not stated | percent | 4 | the average GMC volume filling factor for the three GMAs is 15% |
| Central AGN flux density at 230 GHz | 55.3 | 3.9 | mJy | 5 | ${S_{\nu}= 55.3 \pm 3.9}$ mJy |
| Absorption feature velocity | 260.3 | 0.8 | km/s | 5 | a mean velocity of $260.3 \pm 0.8$ km s$^{-1}$ and a linewidth of $5.2 \pm 0.8$ km s$^{-1}$ |
| Dispersal timescale of GMA 18 | 12 | not stated | Myr | 4 | $t_{disp} \sim 2~r_c/\sigma$=12 Myr |

## Qualitative findings

- No disk-like molecular structures; gas appears infalling and ballistic after condensing from hot gas  
  > "No disk-like molecular structures are detected and all indications suggest that the molecular gas follows ballistic trajectories" (abstract)

## Claim tuples

- H: Are the CO structures individual GMCs or larger associations, and are they bound? | E: Gaussian line fits, imfit sizes, virial parameter | R: Linewidths 15-65 km/s; alpha = 36 and 24 for GMA 11 and 18 broad component | F: They are unbound giant molecular associations | **supported**
- H: Are GMAs pressure confined by hot gas? | E: Compare turbulent pressure with Chandra thermal pressure | R: P_turb is about four times P_ext | F: Not confined; disperse in about 12 Myr | **supported**
- H: Origin of the molecular gas | E: Compare morphology, kinematics and cooling and stellar mass-loss rates | R: No disks; dispersion below stellar; mass deposition 5.1 Msun/yr | F: Cooling flow origin | **partially**
- H: Nature of the central continuum source | E: Compare 230 GHz with low-frequency radio | R: 230 GHz luminosity at least 500 times the 610 MHz luminosity | F: Probably a recent accretion event | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: 50 km/s bins optimize S/N for detecting structures  
  > "We found that a bin width of 50 km s$^{-1}$ optimized the signal-to-noise of the emission lines." (Results)
- Alternative: Dust thermal emission as source of 230 GHz continuum rejected (<1 mJy predicted)  
  > "It is unlikely that thermal emission from dust makes a substantial contribution to the 230 GHz continuum emission." (The Central AGN and Absorption Feature)
- How they decided it was enough: _not stated_
- Limitation (authors): Diffuse CO resolved out; ALMA flux in blueshifted part only 20% of IRAM 30m; GMA count likely a lower limit  
  > "the integrated flux density in the blueshifted portion of the ALMA spectrum is only 20% of that in the IRAM 30m data" (Results)
- Caveat (inferred, ours): Conversion factor and 3.2 line ratio uncertain for this environment
- Caveat (inferred, ours): Single 29-min pointing with limited field of view
- Caveat (inferred, ours): Structure identification subjective with no clean-parameter details
- Caveat (inferred, ours): Absorber and virial results depend on assumed geometry

## Reproducibility

- Data public (paper): Cycle 0 data credited to ADS/JAO.ALMA#2011.0.00735.S; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00735.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: CASA version
- Missing: Structure extraction regions
- Missing: X-ray derived inputs
- Data volume (inferred): ~10-20 GB (single Cycle 0 execution, 4 spw x 3840 channels)
- Score (inferred): 3/5, Public data and simple analysis, but imaging and region definitions are unstated.
- Rediscovery candidate: yes, Data public, a single short execution, and numeric results (masses, linewidths, flux density) are tabulated, though imaging details need reconstruction.

## Links

- Method: Bolatto, Wolfire & Leroy 2013 (Mass relation and Xco)
- Companion: Russell et al. 2014 (ALMA CO in A1664)
- Companion: McNamara et al. 2014 (ALMA CO in A1835)

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 41,
  "rate": 0.562
 },
 "evidence_ok": true
}
```

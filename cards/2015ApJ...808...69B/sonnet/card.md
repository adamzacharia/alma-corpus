# ALMA Observations of the Largest Proto-Planetary Disk in the Orion Nebula, 114-426: A CO Silhouette

`2015ApJ...808...69B` | The Astrophysical Journal 2015 | first author: Bally, John | arXiv: 1506.03391 | DOI: 10.1088/0004-637X/808/1/69

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: What are the dust mass, gas tracers and CO kinematics (central star mass) of the largest silhouette disk in the Orion Nebula, 114-426, from ALMA Band 7 data?  
  > "we present the ALMA observations of the 114-426 disk in four spectral lines and re-analyze the dust continuum in more detail than (cite: Mann2014)." (Introduction)
- Target **114-426**: coordinates J2000 05:35:11.316, -5:24:26.62 (continuum peak)  
  > "With a major axis diameter of 2.3$''$ , or 950 AU at a distance of 414 pc (cite: Menten2007), the 114-426 disk is the largest silhouette in the Orion Nebula" (Introduction); "The peak flux, 4.2 mJy beam$^{-1}$ is located at J2000 = 05:35:11.316, $-$5:24:26.62" (Results); z/distance 414 pc  
  > "With a major axis diameter of 2.3$''$ , or 950 AU at a distance of 414 pc (cite: Menten2007), the 114-426 disk is the largest silhouette in the Orion Nebula" (Introduction); "The peak flux, 4.2 mJy beam$^{-1}$ is located at J2000 = 05:35:11.316, $-$5:24:26.62" (Results); distance from Menten et al. 2007  
  > "With a major axis diameter of 2.3$''$ , or 950 AU at a distance of 414 pc (cite: Menten2007), the 114-426 disk is the largest silhouette in the Orion Nebula" (Introduction); "The peak flux, 4.2 mJy beam$^{-1}$ is located at J2000 = 05:35:11.316, $-$5:24:26.62" (Results)

## Data provenance

- ALMA projects: 2011.0.00028.S
- bands: Band 7  
  > "Four transitions were observed in ALMA Band 7; CO J=3$-$2, HCO$^+$ J=4$-$3, HCN J=4$-$3, and CS J=7$-$6." (Observations)
- frequencies and spectral setup: four 1.875 GHz wide bands, 488.28 kHz channels (3840 channels); Hanning smoothed to 976.56 kHz = 0.84 km/s  
  > "The correlator was configured to observe four 1.875 GHz wide bands using a channel spacing of 488.28 kHz to yield 3840 channel spectra." (Observations)
- continuum bandwidth: _not stated_
- arrays: twenty-two 12 m antennas, Cycle 0  
  > "using twenty-two 12 m antennas" (Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.51'' x 0.46''  
  > "The synthesized beam full-width at half-maximum (FWHM) size is 0.51$''$ ($\sim$211 AU) $\times$ 0.46$''$ ($\sim$190 AU)." (Observations)
- max recoverable scale: ~5''  
  > "the maximum recoverable angular structure is about 5$''$ ($\sim$2000 AU)" (Observations)
- sensitivity: continuum ~0.56 mJy/beam; line 0.025-0.1 Jy/beam per channel  
  > "resulting in a continuum sensitivity of about 0.56 mJy per beam" (Observations)
- time on source: 1300 s  
  > "Total on-source integration times were 1300 seconds" (Observations)
- observing dates: 24 October 2012  
  > "on 24 October 2012" (Observations)
- pi or archival as stated: _not stated_
- Line: CO J=3-2 (not stated)
- Line: HCO+ J=4-3 (not stated)
- Line: HCN J=4-3 (not stated)
- Line: CS J=7-6 (not stated)
- Other facility **HST**: Halpha and F775W images of the silhouette  
  > "Figure [2](#fig2) (top) shows a closeup of the disk in the F775W HST filter" (Results)
- Other facility **Nobeyama 45m, IRAM 30m, APEX**: single-dish 12CO background emission (J=1-0, 2-1, 3-2)  
  > "The IRAM 30-meter $^{12}$CO J=2$-$1 emission (cite: Berne2014) shows peak temperatures of 60$-$70 K" (Results)
- External data: Single-dish 12CO J=1-0 background used to estimate background temperature  
  > "The background is estimated by interpolation of the $^{12}$CO emission in the J=1$-$0 emission from (cite: Shimajiri2011)" (Table 2) [from Shimajiri2011; Shimajiri2014]
- External data: 12CO J=2-1 IRAM 30m background  
  > "the J=2$-$1 emission from (cite: Berne2014)" (Table 2) [from Berne2014]
- External data: Distance 414 pc  
  > "950 AU at a distance of 414 pc (cite: Menten2007)" (Introduction) [from Menten2007]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.11'' per pixel (re-gridded)  
  > "The reduced data were re-gridded to $X_{pix}$ = 0.11$''$ per pixel." (Observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Hanning smoothing  
  > "After Hanning smoothing, the spectral resolution was $\Delta \nu$ = 976.56 kHz" (Observations)
- final beam: 0.51'' x 0.46''  
  > "The synthesized beam full-width at half-maximum (FWHM) size is 0.51$''$ ($\sim$211 AU) $\times$ 0.46$''$ ($\sim$190 AU)." (Observations)
- final rms: 0.56 mJy/beam continuum  
  > "resulting in a continuum sensitivity of about 0.56 mJy per beam" (Observations)

### Inherited from earlier work

- Observation description and data reduction procedures  
  > "(cite: Mann2014) present a detailed description of the observations and data reduction procedures." (Observations) [from Mann et al. 2014 (cite: Mann2014)]

### Not stated but needed to reproduce (our reading)

- Calibration details, CASA version, calibrators
- Imaging weighting/robust, deconvolver, masks
- Continuum-subtraction and line-free channels
- Details of the Keplerian CO absorption model fit (likelihood, grid, inclination, parameter ranges)
- How the background CO temperature was interpolated per channel
- Aperture used for flux measurement beyond its approximate size

## Analysis recipe

1. **Measure continuum flux and size**: Elliptical aperture flux sum divided by N_pix; beam deconvolved sizes  
  > "the total flux in an aperture containing $n$ pixels is obtained by summing the pixel values in the aperture and dividing by $N_{pix}$." (Observations)
   - parameter: aperture ~0.74'' by 1.55''  
  > "The area integrated flux in a $\sim$ 0.74$''$ by 1.55$''$ diameter elliptical aperture aligned with the disk major axis" (Results)
   - fitting: _not stated_
   - validation: compared with 7 mJy of Mann et al. 2014  
  > "14% smaller than the 7 mJy flux reported by (cite: Mann2014)" (Results)
2. **Derive disk mass from dust continuum**: Optically thin M = S D^2/(kappa B(T))  
  > "$$M_{disk}  = {{S_{\nu} D^2} \over {\kappa B_{\nu}(T_{dust}) }}" (Results)
   - assumption: kappa=0.034 cm^2/g, gas-to-dust 100, T_dust=20 K, D=414 pc  
  > "a grain emissivity $\kappa$ = 0.034 ${\rm cm}^2~{\rm g}^{-1}$ (which assumes a gas-to-dust ratio of 100), and a grain temperature $T_{dust}$ = 20 K" (Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure CO absorption depths and velocities**: Locate deepest absorption per channel; convert Jy/beam to K; compare with interpolated single-dish background  
  > "Table 2 lists the location of the deepest absorption as a function of radial velocity, the absorption depth in Janskys and degrees Kelvin" (Results)
   - fitting: _not stated_
   - validation: Cube rms of ~0.1 Jy in background is smaller than absorption signal  
  > "the CO intensity fluctuations in the ALMA data cube have a 1 $\sigma$ rms of about 0.1 Jy or less" (Results)
4. **Estimate central star mass**: Keplerian from separation and velocity difference of absorption minima; plus thin optically thick Keplerian disk model convolved with beam  
  > "We modeled the CO absorption from a geometrically thin, optically thick Keplerian disk inclined by a few degrees, convolved with a Gaussian to represent the synthesized ALMA beam" (Discussion)
   - parameter: free parameters: inner hole radius R_in and M_*  
  > "using two free parameters: an inner hole with radius $R_{in}$ and the central star mass, $M_*$." (Discussion)
   - assumption: edge-on disk, Keplerian rotation, D=414 pc  
  > "assuming that the disk is in Keplerian rotaion, the enclosed mass is $M_* = R V^2_{orbit}(R) / G" (Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk gas mass | 3.1 | 0.6 | Jupiter masses | 2 | Using these values, the disk mass is only 3.1$\pm$0.6 times the mass of Jupiter . |
| Disk mass | 5.9e30 | 1.1e30 | g | 2 | \approx 5.9 \pm  1.1  \times 10^{30}~{\rm grams} |
| Integrated continuum flux | 6.0 | 0.6 | mJy | 1 | is 6.0$\pm$0.6 mJy |
| Continuum major axis FWHM | 1.11 | 0.05 | arcsec | 1 | major axis FWHM diameter of 1.11$\pm$0.05$''$ |
| Peak continuum | 4.2 | not stated | mJy/beam | 1 | The peak flux, 4.2 mJy beam$^{-1}$ |
| CO absorption depth north | -0.63 | not stated | Jy/beam (27 K) | 3 | has the strongest CO absorption with a depth of $-$0.63 Jy beam$^{-1}$ |
| Velocity difference of absorption peaks | 2.9 | 0.2 | km/s | 3 | differ in radial velocity by $\Delta$V = 2.9 $\pm$0.2 km s$^{-1}$ |
| Central star mass (Keplerian) | 0.43 | 0.11 | Msun | 4 | $0.43 \pm 0.11$ M$_{\odot}$ |
| Disk lifetime against photoevaporation | (1.0-1.6)e4 | not stated | yr | 0 | $\tau \sim M_{disk}  / \dot M_{disk}  \sim (1.0 - 1.6) \times 10^4$ years |

## Qualitative findings

- Disk is not detected in HCO+, HCN or CS.  
  > "HCO$^+$, HCN, and CS lines, in either emission or absorption, are not detected from 114-426." (Discussion)

## Claim tuples

- H: Does the 114-426 disk have a low mass? | E: Optically thin 856um continuum mass | R: 3.1±0.6 Jupiter masses | F: Low mass disk, possibly a lower limit if grains are large | **supported**
- H: Can the central star mass be constrained from CO absorption? | E: Keplerian analysis of absorption minima plus model | R: M* ~0.43 Msun; 0.4-0.7 favored for small hole | F: M* less than 1 Msun | **supported**
- H: Is the disk evolved/depleted in dense gas tracers? | E: Search for HCO+, HCN, CS | R: Non-detections | F: May indicate evolved disk, but only suggestive | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Large (~250 AU) inner hole with ~1 Msun star also allowed by model  
  > "A stellar mass of about 1 M$_{\odot}$ and a thin annular disk with a large ($\sim$ 250 AU) hole, however, is also allowed." (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Mass is a lower limit if solids are in large grains  
  > "If most solids and ices have have been incorporated into large grains, however, this value is a lower limit." (abstract)
- Limitation (authors): Beam dilution and background brightness limit CO absorption interpretation  
  > "The observed CO absorption can be affected by several factors including the optical depth, radial velocity, and temperature of the disk gas, beam dilution" (Discussion)
- Caveat (inferred, ours): Single-dish background interpolated from other transitions, not measured in CO 3-2
- Caveat (inferred, ours): Star mass from only two absorption minima; rough Keplerian assumption
- Caveat (inferred, ours): Model fit is poorly documented; no uncertainties on model
- Caveat (inferred, ours): Fixed T=20 K and kappa dominate mass uncertainty

## Reproducibility

- Data public (paper): Project code given; ALMA Cycle 0 data  
  > "obtained with ALMA during Cycle 0 (ALMA project 2011.0.00028.S)" (Observations)
- Products in archive: _not stated_
- Missing: Reduction/imaging parameters (in Mann et al. 2014)
- Missing: Model fitting code and details
- Missing: Single-dish background cubes
- Data volume (inferred): ~10-50 GB for Cycle 0 Band 7 raw data
- Score (inferred): 3/5, Public data and simple formulae, but calibration/imaging and the disk model are not specified.
- Rediscovery candidate: yes, Public data and simple numeric results (flux, mass, absorption depths), though imaging details must come from Mann et al. 2014.

## Links

- Method: Mann et al. 2014 (cite: Mann2014) (Observations and data reduction description)
- Companion: Williams et al. 2014 (cite: Williams2014) (Similar absorption analysis for 253-1536)
- Related: ALMA Cycle 0 study of Orion proplyds

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 37,
  "rate": 0.536
 },
 "evidence_ok": true
}
```

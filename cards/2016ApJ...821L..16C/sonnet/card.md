# The VLA View of the HL Tau Disk: Disk Mass, Grain Evolution, and Early Planet Formation

`2016ApJ...821L..16C` | The Astrophysical Journal Letters 2016 | first author: Carrasco-González, Carlos | arXiv: 1603.03731 | DOI: 10.3847/2041-8205/821/1/L16

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: protoplanetary_disks
- Question: What do new deep VLA 7.0 mm images of the HL Tau disk, which are optically thin, reveal about disk dust mass, grain growth and early planet formation, compared with the ALMA images?  
  > "At this long wavelength the dust emission from HL Tau is optically thin, allowing a comprehensive study of the inner disk." (abstract)
- Target **HL Tau**: coordinates RA(J2000)=04h31m38.426s, Dec(J2000)=18d13m57.23s (image alignment position)  
  > "The object is located at a distance of $\sim$140 pc (Loinard et al. 2007), within the Taurus star-forming region." (1 Introduction); "$\alpha$(J2000)=04$^h$31$^m$38$^s$426, $\delta$(J2000)=18$^\circ$13$\ensuremath{'}$57$\ensuremath{''}$23." (2 Observations and image analysis); z/distance ~140 pc  
  > "The object is located at a distance of $\sim$140 pc (Loinard et al. 2007), within the Taurus star-forming region." (1 Introduction); "$\alpha$(J2000)=04$^h$31$^m$38$^s$426, $\delta$(J2000)=18$^\circ$13$\ensuremath{'}$57$\ensuremath{''}$23." (2 Observations and image analysis); distance from Loinard et al. 2007  
  > "The object is located at a distance of $\sim$140 pc (Loinard et al. 2007), within the Taurus star-forming region." (1 Introduction); "$\alpha$(J2000)=04$^h$31$^m$38$^s$426, $\delta$(J2000)=18$^\circ$13$\ensuremath{'}$57$\ensuremath{''}$23." (2 Observations and image analysis)

## Data provenance

- ALMA projects: 2011.0.00015.SV
- bands: VLA Q band, 39-47 GHz (7.0 mm); ALMA 2.9, 1.3, 0.87 mm images used for comparison  
  > "We observed the frequency range 39-47 GHz (central wavelength $\simeq$ 7.0 mm)." (2 Observations and image analysis)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: VLA C, B and A configurations  
  > "using the Q band receivers in the C, B, and A configurations" (2 Observations and image analysis)
- baselines: _not stated_
- angular resolution: VLA most sensitive image beam ~0.067 arcsec; images convolved to 0.07 arcsec common beam  
  > "our most sensitive VLA image at 7.0 mm (natural weighting; beam size$\simeq$0$\ensuremath{''}$067)" (2 Observations and image analysis)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: VLA: 2014-Dec-07 to 2015-Sep-21  
  > "| 2015-Sep-21 | 14B-487 |   A   |   3.4 h    |" (Table 1)
- pi or archival as stated: _not stated_
- Other facility **VLA**: New 7.0 mm observations (projects 14B-485, 14B-487) and archival 6 and 2 cm A-configuration data (12B-272) for jet free-free correction  
  > "we calibrated VLA A configuration archival data at 6 and 2 cm (project code: 12B-272)" (2 Observations and image analysis)
- Other facility **ALMA**: Public 2.9, 1.3, 0.87 mm HL Tau images (2011.0.00015.SV) used for comparison and radial profiles  
  > "the smallest beam size obtained from the public 2.9 mm ALMA uv-data with a uniform weighting" (2 Observations and image analysis)
- External data: Disk inclination 46.72 deg and position angle 138.02 deg from ALMA images  
  > "inclination angle, $i\simeq$46.72$^\circ$, and position angle, P.A.$\simeq$138.02$^\circ$; ALMA Partnership et al. 2015b" (2 Observations and image analysis) [from ALMA Partnership et al. 2015b]
- External data: Dust masses from radiative transfer modeling of ALMA images, for comparison  
  > "Calculated by radiative transfer modeling of the ALMA images by Pinte et al. (2016)." (Table 2) [from Pinte et al. 2016]

## Processing

### Calibration

- pipeline or manual: CASA with a modified version of the NRAO calibration pipeline  
  > "using a modified version of the NRAO calibration pipeline" (2 Observations and image analysis)
- casa version: CASA 4.4.0  
  > "Common Astronomy Software Applications (CASA; version 4.4.0)" (2 Observations and image analysis)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: 3C147 (bandpass 3C84, phase J0431+1731)  
  > "The bandpass, flux density and phase calibrators were 3C84, 3C147 and J0431+1731, respectively." (Table 1)
- flux scale uncertainty: 10%  
  > "We estimate a 10% uncertainty for the absolute flux calibration." (Table 1)
- self calibration: Self-calibration was achieved (details not given)  
  > "Self-calibration was achieved." (Table 1)

### Imaging

- task: CASA CLEAN, multi-scale multi-frequency synthesis, nterms=2  
  > "Images were made with the CASA task `CLEAN` using multi-scale multi-frequency synthesis that fits the emission with a Taylor series with nterms=2 during the deconvolution" (2 Observations and image analysis)
- deconvolver: _not stated_
- weighting robust: Briggs robust varied to get different resolutions; natural weighting for the most sensitive image  
  > "we made images with different angular resolutions by adjusting the Briggs `robust` parameter (Briggs 1995) and the Gaussian uv-taper in `CLEAN`." (2 Observations and image analysis)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: All images convolved to a common circular 0.07 arcsec beam  
  > "we convolved all images to a common circular beam size of 0$\ensuremath{''}$07" (2 Observations and image analysis)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Disk geometry (inclination, PA) from ALMA images  
  > "inclination angle, $i\simeq$46.72$^\circ$, and position angle, P.A.$\simeq$138.02$^\circ$; ALMA Partnership et al. 2015b" (2 Observations and image analysis) [from ALMA Partnership et al. 2015b]
- Dust opacity at 7 mm range  
  > "we use a range of typical values for the disk-averaged opacity, $\kappa_{7mm}=$0.13-0.2 cm$^2$ g$^{-1}$ (e.g., Men’shchikov et al. 1999, Pérez et al. 2012)" (3.1 Mass distribution) [from Men’shchikov et al. 1999, Pérez et al. 2012]

### Not stated but needed to reproduce (our reading)

- robust values and uv-taper values for each VLA image
- multiscale scales, cleaning masks and thresholds
- self-calibration solution intervals
- how the ALMA images were produced (calibration, imaging, flux scale) from 2011.0.00015.SV
- exact ALMA flux scale/bands and dates
- details of the free-free subtraction applied to profiles
- dust temperature profile adopted per radius and the method for column density integration

## Analysis recipe

1. **Image VLA 7 mm data**: CLEAN multi-scale MFS, varying robust and uv-taper; also two 4 GHz sub-bands  
  > "We also made images by splitting the 8 GHz band in two sub-bands of 4 GHz each (central wavelengths 6.7 and 7.3 mm)." (2 Observations and image analysis)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Radial intensity profiles**: Average intensity in 0.01 arcsec wide elliptical rings using IRING on images aligned and convolved to 0.07 arcsec  
  > "we obtained the average intensity within concentric elliptical rings of 0$\ensuremath{''}$01 width at different radii, using the task `IRING`" (2 Observations and image analysis)
   - software: AIPS
   - fitting: _not stated_
   - validation: _not stated_
3. **Correct free-free contamination**: Extrapolate jet flux from 6 and 2 cm with spectral index 0.4 (upper limit) or -0.1 from 2 cm (lower limit)  
  > "an upper limit to the free-free contribution at 7.0 mm is obtained by extrapolating the flux density from cm wavelengths with a spectral index of 0.4" (2 Observations and image analysis)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared with spectral index from 6.7 and 7.3 mm sub-bands (~1 at disk center)  
  > "we obtain a spectral index of $\sim$1 at the center of the disk" (2 Observations and image analysis)
4. **Derive Tb, spectral indices, optical depth, column density and dust mass**: Planck brightness temperature; spectral indices; optical depth and column density from power-law dust temperature and opacity; masses by integrating column density between dark rings  
  > "we obtain first estimates by assuming a simple power-law for the dust temperature in the form $T_{dust}=T_{0} (R/R_{0})^{-q}$." (3.1 Mass distribution)
   - parameter: T0 ≃ 70-140 K at R0 = 10 au; q = 0.5-0.6  
  > "with different proposed values in the range $T_0\simeq$70-140 K at $R_0$=10 au" (3.1 Mass distribution)
   - assumption: kappa_7mm = 0.13-0.2 cm^2 g^-1; distance 140 pc  
  > "$\kappa_{7mm}=$0.13-0.2 cm$^2$ g$^{-1}$" (3.1 Mass distribution)
   - fitting: _not stated_
   - validation: Compared with Pinte et al. (2016) masses for optically thin ALMA rings B2-B6  
  > "we obtain dust masses consistent with previous estimations (Pinte et al. 2016)" (3.1 Mass distribution)

## Software

- **CASA** 4.4.0: Calibration and CLEAN imaging  
  > "Calibration of the data was performed with the data reduction package Common Astronomy Software Applications (CASA; version 4.4.0)" (2 Observations and image analysis)
- **AIPS** : IRING radial intensity profiles  
  > "using the task `IRING` of the Astronomical Image Processing System (AIPS)" (2 Observations and image analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total disk dust mass | (1-3)e-3 | range from opacity and temperature | Msun | 4 | the total dust mass of the disk is within the range (1-3)$\times$10$^{-3}$ M$_\ensuremath{\odot}$ |
| Dust column density at disk center | ~1 | not stated | g cm^-2 | 4 | We estimated values of the dust column density around $\sim$1 g cm$^{-2}$ at the center of the disk |
| Free-free flux density at 7.0 mm | ~200-400 | range | uJy | 3 | unresolved ($<$0$\ensuremath{''}$07) free-free emission with a flux density in the range $\sim$200-400 $\mu$Jy |
| Spectral index of NE knot (6.7-7.3 mm) | 2.5 | 0.4 | dimensionless | 4 | $\alpha_{6.7-7.3 mm}$=2.5$\pm$0.4 |
| Dust mass of NE clump candidate | 3-8 | range | Mearth | 4 | we estimate a dust mass in the range 3-8 M$_\ensuremath{\oplus}$ for this clump |
| Dust mass of B1 | 70-210 | range | Mearth | 4 | / B1           / 13 - 32 / 1.45 $\pm$ 0.02 / 70 - 210             / $>$47                  / |

## Qualitative findings

- 7.0 mm emission is optically thin at all radii (tau ≲ 0.4), unlike ALMA wavelengths  
  > "This imply that dust emission at 7.0 mm is well optically thin at all radii, even in the densest parts of the disk." (3 Results and discussion)

## Claim tuples

- H: Is the HL Tau inner disk optically thin at 7 mm, allowing mass determination? | E: Compared 7.0 mm VLA brightness temperatures with ALMA 0.87 mm | R: Tb ~45 and 15 K vs ~130 and 60 K; tau ≲0.4 at 7 mm | F: Emission optically thin; total dust mass (1-3)e-3 Msun, larger than earlier estimates | **supported**
- H: Does grain size vary with radius? | E: Spectral index 7.0-2.9 mm vs radius | R: Clear gradient between ~10-50 au | F: Larger grains at smaller radii | **supported**
- H: Is there a dust clump in the first bright ring? | E: Multiple images of B1 at 7 mm | R: Compact NE knot persistent in all images, alpha=2.5±0.4 | F: Likely a dense dust clump; planets may be forming in the bright rings | **partially**

## Reasoning

- Why this data: Longer wavelength gives lower optical depth in the inner disk  
  > "The challenge of deriving density profiles and grain size distributions can only be circumvented by observations at even longer wavelengths where the disk will be optically thinner." (1 Introduction)
- Why this method: _not stated_
- Alternative: NE knot brightening from jet free-free emission considered but disfavored  
  > "at 7.0 mm, the free-free emission from the jet is expected to be confined within the inner disk" (3.3 Substructure in the first bright ring)
- How they decided it was enough: _not stated_
- Limitation (authors): Mass estimates are rough; detailed radiative transfer modeling needed; free-free correction adds uncertainty at the center  
  > "An accurate determination of the mass distribution in the HL Tau disk requires detailed radiative transfer modeling." (3.1 Mass distribution)
- Caveat (inferred, ours): Simple power-law temperature and single opacity range dominate mass uncertainty
- Caveat (inferred, ours): Clump significance rests on a ~4 sigma knot and image morphology
- Caveat (inferred, ours): Free-free correction is extrapolated from cm data at a different epoch

## Reproducibility

- Data public (paper): ALMA uv-data described as public; VLA archival 12B-272 used  
  > "the public 2.9 mm ALMA uv-data with a uniform weighting" (2 Observations and image analysis)
- Products in archive: _not stated_
- Missing: Imaging parameters per image
- Missing: ALMA image processing details
- Missing: Column density integration details
- Data volume (inferred): VLA ~100s GB raw; ALMA science verification data ~tens of GB
- Score (inferred): 3/5, Public data and simple analysis, but many imaging and calibration parameters unstated.
- Rediscovery candidate: no, The main VLA data are not ALMA, and imaging recipe is incomplete.

## Links

- Method: Rau & Cornwell 2011 (multi-scale multi-frequency synthesis)
- Companion: ALMA Partnership et al. 2015b (ALMA HL Tau images)
- Companion: Pinte et al. 2016 (radiative transfer modeling of ALMA data)
- Related: ALMA HL Tau long baseline campaign

## Checks

```json
{
 "quotes": 52,
 "quotes_ok": 52,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 37,
  "rate": 0.544
 },
 "evidence_ok": true
}
```

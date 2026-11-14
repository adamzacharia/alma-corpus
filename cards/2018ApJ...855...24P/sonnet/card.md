# Thermal Jeans Fragmentation within ∼1000 au in OMC-1S

`2018ApJ...855...24P` | The Astrophysical Journal 2018 | first author: Palau, Aina | arXiv: 1706.04623 | DOI: 10.3847/1538-4357/aaad03

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: What processes regulate fragmentation of the OMC-1S region down to ~1000 AU scales, and is it consistent with thermal Jeans fragmentation?  
  > "Here we present a study of the fragmentation properties of a region forming intermediate and low-mass protostars, the Orion Molecular Cloud 1 South (hereafter, OMC-1S)." (Introduction)
- Target **OMC-1S**: coordinates phase center RA 05:35:14.0, Dec -05:24:00 (J2000)  
  > "The most recent measurement of the distance has been done by Kounkel et al. (2017), who report 388 pc." (Introduction); "The phase center for both observations was the same $\alpha(J2000) = 05^h~ 35^m~ 14\rlap.^s0$; $\delta(J2000) = -05^\circ~ 24'~ 00''$." (2.1 ALMA at 1.3 mm); z/distance 388 pc  
  > "The most recent measurement of the distance has been done by Kounkel et al. (2017), who report 388 pc." (Introduction); "The phase center for both observations was the same $\alpha(J2000) = 05^h~ 35^m~ 14\rlap.^s0$; $\delta(J2000) = -05^\circ~ 24'~ 00''$." (2.1 ALMA at 1.3 mm); distance from Kounkel et al. (2017)  
  > "The most recent measurement of the distance has been done by Kounkel et al. (2017), who report 388 pc." (Introduction); "The phase center for both observations was the same $\alpha(J2000) = 05^h~ 35^m~ 14\rlap.^s0$; $\delta(J2000) = -05^\circ~ 24'~ 00''$." (2.1 ALMA at 1.3 mm)

## Data provenance

- ALMA projects: 2013.1.01037.S
- bands: Band 6 (1.3 mm) ALMA; VLA 7 mm  
  > "The ALMA[^1] Band 6 (1.3 mm) observations were carried out on 2015 May 19 and August 18" (2.1 ALMA at 1.3 mm)
- frequencies and spectral setup: four 1.875 GHz spectral windows at 233.683, 231.323, 219.266, 216.875 GHz; 7.5 GHz total  
  > "centered at rest frequencies: 233.683 GHz, 231.323 GHz, 219.266 GHz, and 216.875 GHz, which covers a total bandwidth of 7.5 GHz." (2.1 ALMA at 1.3 mm)
- continuum bandwidth: 7.5 GHz (line-free channels)  
  > "The continuum image was obtained averaging line-free channels from four spectral windows" (2.1 ALMA at 1.3 mm)
- arrays: 12 m antennas, 38 (May 19) and 37 (Aug 18)  
  > "On May 19, we used 38 of the 12 m antennas" (2.1 ALMA at 1.3 mm)
- configurations: _not stated_
- baselines: 16–1230 kλ combined (21–555 m and 43–1600 m)  
  > "Including both epochs, the covered range of projected baselines is 16–1230 k$\lambda$" (2.1 ALMA at 1.3 mm)
- angular resolution: 0.28x0.22 arcsec combined; 0.22x0.17 arcsec (~74 AU) extended only  
  > "the synthesized beam is $0\rlap.{''}22 \times 0\rlap.{''}17$, corresponding to a spatial resolution of $\sim74$ AU" (2.1 ALMA at 1.3 mm)
- max recoverable scale: 5.7 arcsec  
  > "Largest Angular Scale to which ALMA was sensitive of $5.7''$" (2.1 ALMA at 1.3 mm)
- sensitivity: rms 0.7 mJy/beam (combined); 0.45 mJy/beam (extended only)  
  > "In this case, the rms of the 1.3 mm continuum is 0.45 m$\rm Jy~beam^{-1}$" (2.1 ALMA at 1.3 mm)
- time on source: about 8 minutes per observation  
  > "The integration time on-source (OMC-1S) was about 8 minutes in each observation." (2.1 ALMA at 1.3 mm)
- observing dates: 2015 May 19 and August 18 (ALMA); 2004 November 10 (VLA)  
  > "during 2004 November 10, under the project code AZ154" (2.2 VLA at 7 mm)
- pi or archival as stated: _not stated_
- Other facility **VLA 7 mm (project AZ154)**: 7 mm continuum, A configuration, 0.09 arcsec beam, rms 0.13 mJy/beam  
  > "The rms noise of the smoothed image is 0.13 m$\rm Jy~beam^{-1}$." (2.2 VLA at 7 mm)
- Other facility **CAHA OMEGA-2000 Ks**: near-infrared image to flag IR counterparts of cores  
  > "we present a CAHA $K_\mathrm{s}$ image of the OMC-1S region." (4.4 Fragmentation level vs evolutionary stage)
- External data: 1.3 cm peak intensities and spectral indices of counterparts  
  > "In the Table, we also give the peak intensity of the 1.3 cm emission from Zapata et al. (2004)." (3 Results) [from Zapata et al. (2004)]
- External data: Dust opacity 0.00899 cm2/g at 1.3 mm  
  > "dust (+gas) mass opacity coefficient at 1.3 mm of 0.00899 cm$^2$ g$^{-1}$ (Ossenkopf & Henning 1994, see main text)" (Table 1) [from Ossenkopf & Henning 1994]
- External data: Dust temperature 25 K from NH3 (2,2)/(1,1) rotational temperatures 18–33 K  
  > "the ratio ranges from 0.5 to 1, corresponding to rotational temperatures from 18 to 33 K" (3 Results) [from Wiseman & Ho (1998)]
- External data: X-ray counterpart catalog  
  > "we searched for *Chandra* X-ray counterparts to the ALMA cores (Rivilla et al. 2013)." (4.4 Fragmentation level vs evolutionary stage) [from Rivilla et al. (2013)]

## Processing

### Calibration

- pipeline or manual: calibrated in CASA 4.7; quasars for bandpass, flux, gain  
  > "The data were calibrated, imaged, and analyzed using the Common Astronomy Software Applications (CASA) version 4.7." (2.1 ALMA at 1.3 mm)
- casa version: CASA 4.7  
  > "Common Astronomy Software Applications (CASA) version 4.7" (2.1 ALMA at 1.3 mm)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Quasars J0541-0541, J0522-364, J0750+1231 (roles not individually assigned)  
  > "Quasars J0541$-$0541, J0522$-$364, and J0750$+$1231 were used to calibrate the bandpass, the flux scale, the atmosphere and the gain fluctuations." (2.1 ALMA at 1.3 mm)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN in CASA; epochs combined with CONCAT  
  > "Imaging of the calibrated visibilities was done using the task CLEAN. We combined the two epochs with the task CONCAT in CASA." (2.1 ALMA at 1.3 mm)
- deconvolver: _not stated_
- weighting robust: robust = 0 (ALMA CLEAN; VLA IMAGR also 0)  
  > "We used the ROBUST parameter of CLEAN in CASA set to 0 for an optimal compromise between angular resolution and sensitivity." (2.1 ALMA at 1.3 mm)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied; FWHM ~27 arcsec  
  > "The millimeter continuum image obtained for OMC-1S was corrected by the primary beam attenuation." (2.1 ALMA at 1.3 mm)
- array combination: two epochs concatenated; extended-only image for compact sources  
  > "We also generated an image using only the extended configuration, in order to extract the compact sources." (2.1 ALMA at 1.3 mm)
- smoothing: VLA image smoothed to circular 0.09 arcsec beam  
  > "we smoothed the image to a final circular beam of $0.09''$" (2.2 VLA at 7 mm)
- final beam: 0.22x0.17 arcsec PA 73.37 deg (extended)  
  > "with PA=73.37$^\circ$" (2.1 ALMA at 1.3 mm)
- final rms: 0.45 mJy/beam (extended)  
  > "the rms of the 1.3 mm continuum is 0.45 m$\rm Jy~beam^{-1}$" (2.1 ALMA at 1.3 mm)

### Inherited from earlier work

- Largest angular scale computed with equation A5  
  > "following equation A5 of Palau et al. 2010" (2.1 ALMA at 1.3 mm) [from Palau et al. 2010]
- MSDC grouping in 0.1 dex annuli  
  > "Following the prescription by Simon (1997), we took the angular separations $\theta$ and grouped them in 0.1 dex annuli" (4.1 Typical separations between the ALMA sources) [from Simon (1997)]
- Fragmentation level definition  
  > "This is similar to the definition used in Palau et al. (2013, 2014, 2015)" (4.3 Fragmentation level vs density) [from Palau et al. (2013, 2014, 2015)]

### Not stated but needed to reproduce (our reading)

- CLEAN threshold, mask, niter, and cell/image size
- Which calibrator served which role and flux calibrator model
- Line-free channel selection
- Self-calibration, if any
- Exact Gaussian fitting regions and residual criteria
- Details of density-within-1100-AU aperture measurement
- Calibrated data/scripts not provided; VLA reduction in AIPS unspecified

## Analysis recipe

1. **Image 1.3 mm continuum**: CLEAN of concatenated epochs and extended-only data, robust 0, primary beam corrected  
  > "Imaging of the calibrated visibilities was done using the task CLEAN. We combined the two epochs with the task CONCAT in CASA." (2.1 ALMA at 1.3 mm)
   - software: CASA
   - parameter: robust = 0  
  > "We used the ROBUST parameter of CLEAN in CASA set to 0" (2.1 ALMA at 1.3 mm)
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify sources and fit them**: 12 sigma threshold in extended image, discarding peaks with 12 sigma area under half a beam; 2D Gaussians with IMFIT on combined image; extra Gaussians for N1 and SF5  
  > "We identified 31 compact sources above a 12$\sigma$ threshold" (3 Results)
   - software: CASA IMFIT
   - fitting: 2D Gaussian fits  
  > "after performing 2D Gaussian fits (with the task IMFIT in CASA) using the extended+compact configuration image" (3 Results)
   - validation: residuals inspected against 12 sigma  
  > "if the residuals lie above the 12$\sigma$ detection threshold, we required the inclusion of an additional Gaussian." (3 Results)
3. **Derive source masses**: Flux density to gas+dust mass  
  > "Masses derived using the flux density given in column (5), and assuming a dust temperature of 25 K" (Table 1)
   - assumption: Td = 25 K; kappa(1.3mm) = 0.00899 cm2/g; factor-2 opacity uncertainty; d = 388 pc  
  > "The uncertainty in the masses due to the opacity law is estimated to be a factor of 2." (Table 1)
   - fitting: _not stated_
   - validation: _not stated_
4. **Extract 7 mm sources**: 5 sigma threshold in VLA image; flux integrated in 2.5 sigma contour; compare with ALMA  
  > "We identified those 7 mm sources above the 5$\sigma$ threshold." (3 Results)
   - software: AIPS IMAGR
   - assumption: spectral index 2 to map 7 mm limit to 18 mJy/beam at 1.3 mm  
  > "correspond to a 1.3 mm intensity of $\sim18$ m$\rm Jy~beam^{-1}$, assuming a spectral index of 2" (3 Results)
   - fitting: _not stated_
   - validation: _not stated_
5. **Mean surface density of companions**: Separations histogram; MSDC and two-point correlation function with Monte Carlo random points; linear fit in log-log  
  > "To determine $N_\mathrm{r}$, we averaged the output from $5\times 10^4$ drawings using a simple Monte Carlo routine." (4.1 Typical separations between the ALMA sources)
   - parameter: 0.1 dex annuli, -6<log theta<0; field area 1e-4 deg2  
  > "within $-6<\log{\theta}<0$" (4.1 Typical separations between the ALMA sources)
   - fitting: linear fit in -4.5<log theta<-3.4  
  > "the linear fit in the $-4.5<\log{\theta}<-3.4$ range, or 44–556 AU, has a well defined slope of $-1.05$" (4.1 Typical separations between the ALMA sources)
   - validation: MSDC compared with TPCF  
  > "The values of the MSDC and the TPCF are very consistent down to this last value" (4.1 Typical separations between the ALMA sources)
6. **Define cores and fragmentation level**: Group sources with separation <556 AU; count sources within 1100 AU diameter; compare with density within 1100 AU  
  > "the grouping of those millimeter sources for which the distance between each member of the group and at least another member is $<556$ AU" (4.2 Cores defined as groups of ALMA sources)
   - assumption: temperature structure similar across cores  
  > "assuming that the temperature structure does not change significantly from one core to the other" (4.3 Fragmentation level vs density)
   - fitting: Gaussian probability test of Southern vs Eastern fragmentation  
  > "the probability of drawing three ones as in the Eastern Filament is $\sim0.0071$%" (4.3 Fragmentation level vs density)
   - validation: _not stated_
7. **Jeans comparison**: Compute Jeans mass and length at mean density and 25 K  
  > "the Jeans mass is $\sim0.04$ $M_{\ensuremath{\odot}}$ (following Palau et al. 2015), while the Jeans length is 360 AU (following Bontemps et al. 2010)" (5 Discussion)
   - assumption: T = 25 K; filament surface density ~2 g cm-2  
  > "Assuming a temperature of 25 K, and a surface density around 2 g cm$^{-2}$" (5 Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7: calibration, CLEAN imaging, CONCAT, IMFIT  
  > "Common Astronomy Software Applications (CASA) version 4.7" (2.1 ALMA at 1.3 mm)
- **AIPS (IMAGR)** : VLA 7 mm imaging  
  > "We used the ROBUST parameter of IMAGR in AIPS set to 0." (2.2 VLA at 7 mm)
- **GILDAS** : acknowledged as used by authors  
  > "The authors made use of the GILDAS software" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of 1.3 mm sources | 31 | not stated | dimensionless | 2 | We identified 31 compact sources above a 12$\sigma$ threshold |
| Source masses range | 0.02–1.5 | factor 2 (opacity) | Msun | 3 | The derived masses range from 0.02 to 1.5 $M_{\ensuremath{\odot}}$. |
| MSDC slope 44–556 AU | -1.05 | not stated | dimensionless | 5 | has a well defined slope of $-1.05$ |
| Characteristic scales (MSDC breaks) | 556 and 2787 AU (~2900) | not stated | AU | 5 | at $\log{\theta}=-3.4$ and $-2.7$ (556 and 2787 AU respectively) |
| Number of cores | 19 | not stated | dimensionless | 6 | By doing this, we identified 19 cores |
| Mean density within 1100 AU, fragmenting vs non-fragmenting | 36e7 vs 9.3e7 | not stated | cm-3 | 6 | is $36\times10^{7}$ cm$^{-3}$, while the average density within 1100 AU for the non-fragmenting cores is about a factor of 4 smaller, $9.3\times10^{7}$ cm$^{-3}$ |
| Probability of Eastern Filament fragmentation | ~0.0071 | not stated | percent | 6 | the probability of drawing three ones as in the Eastern Filament is $\sim0.0071$% |
| Jeans mass / Jeans length | 0.04 Msun / 360 AU | not stated | Msun; AU | 7 | the Jeans mass is $\sim0.04$ $M_{\ensuremath{\odot}}$ (following Palau et al. 2015), while the Jeans length is 360 AU |
| Filament Jeans length | 1780 | not stated | AU | 7 | the Jeans length is 1780 AU |

## Qualitative findings

- Southern Filament cores are more fragmented and denser within 1100 AU than other filaments  
  > "We measured the fragmentation level within each core and find a higher fragmentation towards the southern filament." (abstract)
- No conclusion on evolutionary stage trend because most cores are deeply embedded  
  > "cannot infer any conclusion because most of the cores seem to be in a similar, deeply embedded, evolutionary stage" (5 Discussion)

## Claim tuples

- H: Fragmentation at ~1000 AU is governed by thermal Jeans processes | E: Compare fragmentation level to density within 1100 AU and Jeans mass/length | R: Higher density gives higher fragmentation; Jeans mass 0.04 Msun and length 360 AU consistent with sources | F: Thermal Jeans fragmentation is consistent with the data | **supported**
- H: Two characteristic fragmentation scales exist | E: MSDC analysis of 31 sources | R: Breaks at ~556 and ~2900 AU | F: Two-level fragmentation | **partially**
- H: Fragmentation level depends on evolutionary stage | E: Tentative classification from IR, X-ray, cm, outflows | R: Poor statistics, mostly Class 0/I | F: No firm conclusion | **partially**

## Reasoning

- Why this data: Active clustered star formation makes OMC-1S a target for small-scale fragmentation  
  > "the region becomes an excellent target to study fragmentation down to very small scales ($\lesssim1000$ AU)" (Introduction)
- Why this method: _not stated_
- Alternative: Disk fragmentation cannot be tested without kinematic information  
  > "definitely requires kinematic information from molecular gas tracers" (6 Conclusions)
- How they decided it was enough: _not stated_
- Limitation (authors): 7 mm emission may include free-free so no 7 mm masses  
  > "we refrain from estimating masses of gas and dust using the 7 mm emission" (3 Results)
- Limitation (authors): Masses are upper limits and projected separations are lower limits  
  > "the observed separations have not been corrected for projection effects and that these are lower limits" (5 Discussion)
- Caveat (inferred, ours): Single mean Td=25 K for all sources, including heated hot cores, affects masses and densities
- Caveat (inferred, ours): 12 sigma threshold chosen from sidelobes may bias source counts
- Caveat (inferred, ours): Small-number statistics for fragmentation vs density
- Caveat (inferred, ours): Arbitrary cores defined from the MSDC break

## Reproducibility

- Data public (paper): ALMA project code given; public availability not explicitly stated  
  > "as part of the Cycle 2 program 2013.1.01037.S" (2.1 ALMA at 1.3 mm)
- Products in archive: _not stated_
- Missing: CLEAN parameters other than robust
- Missing: VLA AIPS reduction details
- Missing: Density-within-aperture procedure
- Missing: Flux calibrator assignments
- Data volume (inferred): ~20-60 GB for two ALMA Band 6 epochs plus a small VLA dataset
- Score (inferred): 3/5, Public ALMA data and mostly numeric method, but imaging details and aperture procedures are under-specified.
- Rediscovery candidate: yes, Data are from an ALMA program (public after proprietary period), recipe is mostly given, results are numeric (31 sources, MSDC breaks).

## Links

- Method: Simon (1997) (MSDC prescription)
- Method: Palau et al. 2014 (fragmentation level definition and density link)
- Companion: Zapata et al. (2004) (1.3 cm VLA data and spectral indices)
- Related: VLA AZ154

## Checks

```json
{
 "quotes": 78,
 "quotes_ok": 78,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2015.1.00865.S"
 ],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 87,
  "stated": 61,
  "rate": 0.701
 },
 "evidence_ok": true
}
```

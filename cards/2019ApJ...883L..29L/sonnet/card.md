# First [N II]122 μm Line Detection in a QSO-SMG Pair BRI 1202-0725 at z = 4.69

`2019ApJ...883L..29L` | The Astrophysical Journal Letters 2019 | first author: Lee, Minju M. | arXiv: 1909.02284 | DOI: 10.3847/2041-8213/ab412e

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: What are the electron densities of the ionized gas in the QSO and SMG of BRI 1202-0725 at z=4.69, from the [NII] 122/205 μm line ratio?  
  > "we constrain the electron densities of the ionized gas based on the line ratio of [N II] 122/205." (abstract)
- Target **BRI 1202-0725 (QSO and SMG)**: coordinates _not stated_; z/distance z = 4.69  
  > "It consists of an optically selected QSO, optically faint SMG, which is located $4'' (\approx$26 kpc) northwest of the quasar" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00259.S
- bands: Band 6 (N II 205 um), Band 8 (N II 122 um, 700 um)  
  > "The Band 8 observations at 700 $\mu$m were also a subset of the same ALMA Cycle 2 program." (2.2 Band 8 observations)
- frequencies and spectral setup: Band 6: four 1.875 GHz SPWs, two in USB at 3.906 MHz resolution for [NII]205; Band 8: four 1.875 GHz SPWs, two in USB at 3.906 MHz for [NII]122  
  > "Two of them were set in the upper sideband with 3.906 MHz resolution ($\sim$ 2.7 km s$^{-1}$) to detect [$\mbox{N\,II}$] 122 $\mu$m ." (2.2 Band 8 observations)
- continuum bandwidth: _not stated_
- arrays: 12-m array configuration C34-2/1 (Band 6)  
  > "(C34-2/1)" (2.1 Band 6 observations)
- configurations: _not stated_
- baselines: Band 6: 15-348 m; Band 8: 21-783 m  
  > "with the unprojected length ($L_{\rm baseline}$) between 21–783 m on 2015 June 6 through 8" (2.2 Band 8 observations)
- angular resolution: Natural weighting: 1.43x0.84 arcsec (205), 0.32x0.24 arcsec (122)  
  > "the synthesized beam sizes are $1''.43\times0''.84$ and $0''.32\times0''.24$ for the [NII] 205 $\mu$m and [NII] 122$\mu$m observations, respectively." (2.4 Data reduction and analysis)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: Band 6: 58 min; Band 8: 112 min  
  > "total on-source time was 112 minutes." (2.2 Band 8 observations)
- observing dates: Band 6: 2014 Dec 14 and 2015 Jan 4; Band 8: 2015 June 6-8  
  > "on 2014 December 14 and 2015 January 4 with the total on-source time of 58 minutes." (2.1 Band 6 observations)
- pi or archival as stated: _not stated_
- Line: N+ [NII] 3P1-3P0 (121.9 um)
- Line: N+ [NII] 3P2-3P1 (205.2 um)
- External data: Archival Cycle 3 Band 6 [NII]205 data (Lu data) from Lu et al. 2017  
  > "We downloaded the archival data sets that were independently taken during ALMA Cycle 3" (2.3 Archival data) [from Lu2017b]
- External data: Local galaxy and Galactic Plane [NII] comparison data  
  > "we compiled the available data sets for various types of galaxies including our Galaxy (MW) and local galaxies" (Discussion) [from Herrera-Camus2016; Goldsmith2015]

## Processing

### Calibration

- pipeline or manual: ARC-provided calibration scripts; pipeline script for Lu data  
  > "we used the calibration scripts provided by the ALMA ARC members that used CASA versions of 4.2.2 and 4.3.1, respectively." (2.4 Data reduction and analysis)
- casa version: 4.2.2 (Band 6), 4.3.1 (Band 8), 4.5.2 (Lu data); imaging 5.4.0  
  > "For the Lu data, we used the CASA version 4.5.2." (2.4 Data reduction and analysis)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Band 6: Callisto; Band 8: 3C 273 and Titan  
  > "3C 273 and Titan were chosen for flux calibration." (2.2 Band 8 observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean, CASA 5.4.0  
  > "Images were produced by $\mathtt{CASA}$ task $\mathtt{tclean}$." (2.4 Data reduction and analysis)
- deconvolver: _not stated_
- weighting robust: Natural for [NII]122 and Lu data comparison; Briggs robust 0.5 for [NII]205 (beam 1.32x0.68 arcsec)  
  > "we applied the Briggs weighting with a robustness parameter of 0.5" (2.4 Data reduction and analysis)
- uv taper: 330 klambda (beam 0.44x0.38) and 80 klambda (beam 1.20x1.13) for [NII]122  
  > "We chose the $uv$-tapering parameter of 330k$\lambda$ with the synthesized beam of $0''.44\times0''.38$" (2.4 Data reduction and analysis)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: imcontsub on image cube; checked against uvcontsub  
  > "We subtracted the continuum based on image data cube using $\mathtt{imcontsub}$" (2.4 Data reduction and analysis)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 1.5 arcsec resolution images for Band 6 data to compare with Lu data  
  > "we made $1''.5$-resolution images for all Band 6 data sets" (2.4 Data reduction and analysis)
- final beam: _not stated_
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- Line-free channels / continuum fit ranges for imcontsub
- Cell size, image size, masking, cleaning threshold
- Spectral channelization of final cubes
- Exact rest frequencies and velocity centers used
- Aperture centers for flux extraction
- Flux calibration uncertainty
- Line fitting function details for FWHM

## Analysis recipe

1. **Calibrate and image**: ARC calibration scripts, tclean imaging with natural/Briggs weighting and uv-tapering  
  > "Images were produced by $\mathtt{CASA}$ task $\mathtt{tclean}$." (2.4 Data reduction and analysis)
   - software: CASA, tclean
   - parameter: uvtaper 330 klambda; Briggs robust 0.5 for [NII]205  
  > "we applied the Briggs weighting with a robustness parameter of 0.5" (2.4 Data reduction and analysis)
   - fitting: _not stated_
   - validation: Compared 205 um results with Lu data  
  > "we found our measurements are consistent with the Lu data within the uncertainties" (Results)
2. **Measure line fluxes**: Growth curves to choose apertures; Gaussian fit with imfit  
  > "we derived the flux values based on a Gaussian fit using the CASA task $\mathtt{imfit}$." (2.4 Data reduction and analysis)
   - software: CASA imfit
   - parameter: apertures 1.2 arcsec ([NII]122), 3.0 arcsec ([NII]205)  
  > "aperture sizes of $1''.2$ and $3''.0$ for the [$\mbox{N\,II}$] 122 $\mu$m and [$\mbox{N\,II}$] 205 $\mu$m , respectively" (2.4 Data reduction and analysis)
   - fitting: _not stated_
   - validation: Tested continuum subtraction methods and tapering  
  > "we found that the line profile is robust regardless of continuum-subtraction methods" (Results)
3. **Assess missing flux**: simobserve mock observations of Gaussian components  
  > "We investigated the mock observations of a Gaussian structure component with various sizes at a given configuration of C34-5" (2.5 Missing flux)
   - software: CASA simobserve
   - fitting: _not stated_
   - validation: No correction applied  
  > "Therefore, we rely on the flux measurements without any correction." (2.5 Missing flux)
4. **Derive electron density**: 122/205 luminosity ratio converted with PyNeb  
  > "We used the PYNEB package ((cite: pyneb)) to perform the calculations." (Discussion)
   - software: PyNeb
   - assumption: Te = 8000 K; both lines from same region  
  > "at the electron temperature of $T_e$ = 8000 K" (Discussion)
   - fitting: _not stated_
   - validation: Systematic tests with tapered map, smaller aperture, 2D Gaussian fit  
  > "We evaluate potential systematic errors originating from the flux extraction methods in the following manner." (Discussion)

## Software

- **CASA** 4.2.2, 4.3.1, 4.5.2; 5.4.0 for imaging: Calibration, imaging, imfit, simobserve  
  > "All imaging processes were handled with version 5.4.0." (2.4 Data reduction and analysis)
- **PyNeb** : Electron density from line ratio  
  > "We used the PYNEB package ((cite: pyneb)) to perform the calculations." (Discussion)
- **uvmultifit** : Dust continuum size estimates  
  > "based on the $\mathtt{uvmultifit}$ ((cite: Marti-Vidal2014))" (Discussion)
- **astropy** : Listed in software section  
  > "astropy (cite: Astropy)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [NII]122 flux SMG | 1.13 | 0.27 | Jy km/s | 2 | $1.13 \pm 0.27$ |
| [NII]122 flux QSO | 1.62 | 0.27 | Jy km/s | 2 | $1.62 \pm 0.27$ |
| [NII]205 flux SMG | 1.32 | 0.11 | Jy km/s | 2 | $1.32 \pm 0.11$ |
| [NII]205 flux QSO | 0.70 | 0.05 | Jy km/s | 2 | $0.70\pm0.05$ |
| 122/205 luminosity ratio SMG | 1.44 | 0.36 | dimensionless | 4 | $1.44\pm0.36$ and $3.89\pm0.71$ for the SMG and the QSO |
| 122/205 luminosity ratio QSO | 3.89 | 0.71 | dimensionless | 4 | $1.44\pm0.36$ and $3.89\pm0.71$ for the SMG and the QSO |
| electron density SMG | 26 | +12/-11 | cm^-3 | 4 | $26^{+12}_{-11}$ and $134^{+50}_{-39}$ cm$^{-3}$ |
| electron density QSO | 134 | +50/-39 | cm^-3 | 4 | $26^{+12}_{-11}$ and $134^{+50}_{-39}$ cm$^{-3}$ |
| [NII]122 FWHM QSO | 613 | 133 | km/s | 2 | $613\pm 133$ |

## Qualitative findings

- QSO [NII]122 line is about twice as broad as [NII]205, CII and CO lines  
  > "which is broader roughly by a factor of two than those observed in the [$\mbox{N\,II}$]  205 $\mu$m line" (Results)

## Claim tuples

- H: Can [NII]122 be detected at z~4.7 and constrain electron density? | E: ALMA Band 8 and Band 6 observations of BRI 1202-0725; line ratio with PyNeb | R: ne = 26 (SMG) and 134 (QSO) cm^-3 | F: Large scatter of electron densities at fixed SFR in extreme starbursts | **supported**
- H: Are the derived densities robust to flux systematics? | E: Tapered maps, smaller aperture, 2D Gaussian fit | R: Densities could rise up to ~1.5x (QSO) and ~3x (SMG) | F: Systematics can increase densities | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Flux uncertainties large; size differences between lines could bias ratio; low S/N  
  > "we could not confirm any statistically significant difference in the fitted line widths partially owing to the low S/N." (Discussion)
- Caveat (inferred, ours): Different resolutions of the two lines may bias ratio
- Caveat (inferred, ours): Te fixed at 8000 K
- Caveat (inferred, ours): Line widths of 122 um have large uncertainty
- Caveat (inferred, ours): Dust attenuation of 122 um not corrected

## Reproducibility

- Data public (paper): Archival Cycle 3 data downloaded; project 2013.1.00259.S acknowledged  
  > "We downloaded the archival data sets that were independently taken during ALMA Cycle 3" (2.3 Archival data)
- Products in archive: _not stated_
- Missing: Cell/image size, masks, clean thresholds
- Missing: Line-free channels
- Missing: Exact fitting spectral model
- Data volume (inferred): ~50-150 GB
- Score (inferred): 3/5, Data public and main steps given, but several imaging and fitting details are missing.
- Rediscovery candidate: yes, Public data, numeric fluxes and densities, fairly clear recipe.

## Links

- Companion: Lu2017b (First [NII]205 detection with Cycle 3 data)
- Companion: Pavesi2016 (Earlier use of the Band 6 data)

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
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 37,
  "rate": 0.561
 },
 "evidence_ok": true
}
```

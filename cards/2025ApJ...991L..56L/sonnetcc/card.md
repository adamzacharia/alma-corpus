# Resolving Emission from Small Dust Grains in the Blue Compact Dwarf II Zw 40 with JWST

`2025ApJ...991L..56L` | The Astrophysical Journal Letters 2025 | first author: Lai, Thomas S.-Y. | arXiv: 2509.04662 | DOI: 10.3847/2041-8213/ae0467

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, star_formation
- Question: Where does small-grain (3.3 um) PAH emission survive in the low-metallicity BCD II Zw 40 on ~20 pc scales, and how do radiation hardness and metallicity shape the PAH size distribution  
  > "we use JWST to investigate the resolved dust properties of II Zw 40" (1 Introduction); "We propose that the PAH size distribution is fundamentally shaped by two competing mechanisms in low-metallicity environments: photo-destruction and inhibited growth." (abstract)
- Target **II Zw 40**: coordinates northern SSC (5:55:42.6324, +3:23:32.000 ICRS)  
  > "located at a distance of 10 Mpc with a metallicity of 12+log(O/H) = 8.1" (1 Introduction); "we adopt a redshift for II Zw 40 of $z$=0.00248[^1]" (1 Introduction); "the grid was set to center at the northern SSC (5:55:42.6324, +3:23:32.000 ICRS)" (3 Analysis & Method); z/distance D = 10 Mpc; z = 0.00248  
  > "located at a distance of 10 Mpc with a metallicity of 12+log(O/H) = 8.1" (1 Introduction); "we adopt a redshift for II Zw 40 of $z$=0.00248[^1]" (1 Introduction); "the grid was set to center at the northern SSC (5:55:42.6324, +3:23:32.000 ICRS)" (3 Analysis & Method); distance from z from NED (footnote); source of the 10 Mpc distance not stated  
  > "located at a distance of 10 Mpc with a metallicity of 12+log(O/H) = 8.1" (1 Introduction); "we adopt a redshift for II Zw 40 of $z$=0.00248[^1]" (1 Introduction); "the grid was set to center at the northern SSC (5:55:42.6324, +3:23:32.000 ICRS)" (3 Analysis & Method)

## Data provenance

- ALMA projects: 2012.1.00984.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: ALMA CO (3-2), ID 2012.1.00984.S, PI: A. Kepley (a different program from the JWST GO 2511 of the paper's PI)  
  > "CO (3-2) emission from ALMA (ID: 2012.1.00984.S; PI: A. Kepley)" (4.1 Spectral Variation across II Zw 40)
- Line: CO J = 3-2 (not stated)
- Other facility **JWST NIRSpec IFU and MIRI MRS (GO 2511)**: Primary data: NIRSpec G395M/F290LP IFU and MIRI MRS channels 1-4 spectral cubes used for PAH and neon line measurements  
  > "The GO program 2511 (PI: T. Lai)" (2 Observations and data reduction); "In this study, we focus on the observations with the NIRSpec G395M/F290LP grating together with Channel 1-4 of MIRI MRS IFUs." (2 Observations and data reduction)
- Other facility **HST (ID 9739)**: H-alpha emission map used as a comparison with the Pf delta map  
  > "are from H$\alpha$ emission observed by HST (ID: 9739; PI: R. Chandar)" (4.1 Spectral Variation across II Zw 40)
- Other facility **AKARI + Spitzer**: Previously published low-resolution spectrum of II Zw 40 used for comparison  
  > "The AKARI+Spitzer spectrum of II Zw 40 from (cite: Lai2020) is shown in Figure" (4 Results)
- External data: Dereddened far-UV spectrum of SSC-N used to derive G0  
  > "We adopt the dereddened far-UV (FUV) spectrum of SSC-N from (cite: Leitherer2018)" (Estimate of the radiation field) [from (cite: Leitherer2018)]
- External data: 1C PAH template and empirical NIRCam 3.3 um PAH formula  
  > "The dashed lines represent the modified 1C template from (cite: Lai2020)" (4 Results); "The empirical formula for probing 3.3 $\mu$m PAH flux as established by (cite: Lai2020)" (5.2 Probing 3.3 um PAHs Photometrically in Dwarfs) [from (cite: Lai2020)]
- External data: Metallicity of II Zw 40, 12+log(O/H) = 8.1  
  > "with a metallicity of 12+log(O/H) = 8.1, corresponding to Z = 25% Z$_\odot$ (cite: Guseva2000)" (1 Introduction) [from (cite: Guseva2000)]
- External data: NGC 7469 star-forming ring spectrum used as a reference 3.3 um profile  
  > "the star-forming ring spectrum in NGC 7469 (cite: Lai2023)" (4.1 Spectral Variation across II Zw 40) [from (cite: Lai2023)]
- External data: PAH band central wavelengths and FWHMs used to define the upper-limit integration widths  
  > "centered on the central wavelength reported in (cite: Smith2007)" (Appendix: The apparent absence of 7.7, 8.6, and 17 um PAH) [from (cite: Smith2007)]
- Simulation/model as data: PAH-metallicity model spectrum (Z = 0.25 Zsun) from Whitcomb et al. (in prep.), scaled to the observed PAH 6.2 um flux to estimate upper limits on total PAH  
  > "By scaling a PAH-metallicity model spectrum ($Z = 0.25\,Z_{\odot}$) from Whitcomb et al. (in prep.) to match the observed PAH 6.2" (5.1 PAH Formation and Destruction in Low Metallicity Environments)

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
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Method for combining NIRSpec and MIRI cubes (smoothing to a common PSF, grid extraction)  
  > "we follow the method detailed in (cite: Lai2022)" (3 Analysis & Method) [from (cite: Lai2022)]
- Comparison of PAH and neon ratios with star-forming and PDR references  
  > "Following the analysis presented in (cite: Lai2023), we study the comparison between the PAH and neon ratios" (5.1 PAH Formation and Destruction in Low Metallicity Environments) [from (cite: Lai2023)]
- Spectral decomposition code CAFE (latest version)  
  > "we perform a detailed spectral decomposition of this wavelength range using the latest version of the" (3 Analysis & Method) [from (cite: Diaz-Santos2025)]
- NIRCam-filter recipe for the 3.3 um PAH flux  
  > "The empirical formula for probing 3.3 $\mu$m PAH flux as established by (cite: Lai2020)" (5.2 Probing 3.3 um PAHs Photometrically in Dwarfs) [from (cite: Lai2020)]

### Not stated but needed to reproduce (our reading)

- How the ALMA CO (3-2) data were calibrated, imaged and turned into the map compared with the PAH map (band, array, beam, rms, moment definition): none of this is given
- ALMA observing details (configuration, resolution, sensitivity) for 2012.1.00984.S are not stated
- CAFE fit settings: continuum and feature component list, priors, fixed or free line widths, and the code version
- Details of the Q3D cube construction and reproject settings beyond the 0.05 arcsec spaxel size
- Whether the ALMA CO emission was compared quantitatively (e.g. correlation) or only by eye
- Distance source for the adopted 10 Mpc

## Analysis recipe

1. **Calibrate JWST NIRSpec and MIRI MRS data**: JWST Science Calibration Pipeline Detector1 and Spec2 for NIRSpec (version 1.12.5); Detector1, Spec2 and Spec3 for MIRI MRS (version 1.15.0) with residual_fringe on and an alternative straylight reference file  
  > "Science Calibration Pipeline version 1.12.5" (2 Observations and data reduction); "we followed the data reduction processes based on the Pipeline version 1.15.0" (2 Observations and data reduction)
   - software: JWST Science Calibration Pipeline
   - parameter: NIRSpec G395M/F290LP with MIRI MRS channels 1-4  
  > "In this study, we focus on the observations with the NIRSpec G395M/F290LP grating together with Channel 1-4 of MIRI MRS IFUs." (2 Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Build NIRSpec cube at finer spaxel size**: Q3D routine using reproject instead of Spec3, 0.05 arcsec spaxels  
  > "that uses the Python package `reproject` to construct the cube with a finer spaxel size of 0.05$''$" (2 Observations and data reduction)
   - software: Q3D, reproject
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit NIRSpec spaxel spectra and extract apertures**: CAFE spectral decomposition of every NIRSpec spaxel over 2.87 to 5.27 um; total extraction with 1.6 arcsec radius, and two 0.6 arcsec apertures on SSC-N and SSC-S  
  > "The spectrum from each NIRSpec spaxel is fitted with `CAFE`, covering a wavelength range from 2.87 to 5.27 $\mu$m" (3 Analysis & Method); "Two smaller apertures (each with a radius of 0.6$''$)" (3 Analysis & Method)
   - software: CAFE
   - parameter: Total aperture centered at (5:55:42.6474, +3:23:31.020 ICRS), radius 1.6 arcsec  
  > "The dashed line aperture, centered at (5:55:42.6474, +3:23:31.020 ICRS) with a radius of 1.6$''$, represents the total extraction" (3 Analysis & Method)
   - fitting: _not stated_
   - validation: _not stated_
4. **Combine NIRSpec and MIRI cubes on a common grid**: Smooth cubes to common FWHM at 11.5 um, then CAFE extraction on a 19x19 grid of 0.4 arcsec cells; CH3 LONG as stitching reference channel  
  > "by convolving them with wavelength-dependent Gaussian convolution kernels to match with the FWHM measured at 11.5 $\mu$m (FWHM$\sim$0.46$''$)" (3 Analysis & Method); "For spectral stitching, CH3 LONG is used as the reference channel" (3 Analysis & Method)
   - software: CAFE
   - parameter: 19x19 grid, cell width 0.4 arcsec (~20 pc)  
  > "perform a 19$\times$19 grid extraction on both smoothed cubes with each cell having a width of 0.4$''$ ($\sim$20 pc)" (3 Analysis & Method)
   - fitting: _not stated_
   - validation: _not stated_
5. **Measure PAH and neon line fluxes with attenuation correction**: Local band fits over [3.0, 3.6], [5.6, 7.2], [10.7, 12.4] um for PAH 3.3, 6.2, 11.3; flux corrected for attenuation with a mixed geometry from the CAFE opacity profile  
  > "we fit each band locally with carefully defined spectral ranges, with \[3.0, 3.6\], \[5.6, 7.2\], and \[10.7, 12.4\] for PAH 3.3, 6.2, and 11.3 $\mu$m bands, respectively." (3 Analysis & Method); "assuming a mixed geometry based on the opacity profile fitted by CAFE using the full NIRSpec+MIRI spectrum" (3 Analysis & Method)
   - software: CAFE
   - assumption: Mixed dust-gas geometry for attenuation  
  > "assuming a mixed geometry based on the opacity profile fitted by CAFE using the full NIRSpec+MIRI spectrum" (3 Analysis & Method)
   - fitting: _not stated_
   - validation: _not stated_
6. **Estimate upper limit on total PAH power**: 3 sigma integrated fluxes of undetected 7.7, 8.6 and 17 um bands in the total spectrum, applied to all cells as a fixed ratio  
  > "by estimating the 3$\sigma$ integrated fluxes of the 7.7, 8.6, and 17 $\mu$m bands in the total extracted spectrum" (Appendix: The apparent absence of 7.7, 8.6, and 17 um PAH)
   - parameter: RMS 0.68 mJy over 9.68-10.43 um (7.7 and 8.6 um bands); 1.93 mJy over 18.15-18.50 um (17 um)  
  > "the RMS is measured over the 9.68—10.43 $\mu$m continuum range, yielding 0.68 mJy" (Appendix: The apparent absence of 7.7, 8.6, and 17 um PAH); "the RMS derived from the 18.15–18.50 $\mu$m region is 1.93 mJy" (Appendix: The apparent absence of 7.7, 8.6, and 17 um PAH)
   - fitting: 3rd order polynomial fit to local continuum for residual RMS  
  > "RMS) of the residuals after subtracting a 3rd order polynomial fit from the local continuum" (Appendix: The apparent absence of 7.7, 8.6, and 17 um PAH)
   - validation: Cross-check with a scaled PAH-metallicity model spectrum (Z = 0.25 Zsun) gives 3.3/SigmaPAH of 3-7%  
  > "The resulting PAH 3.3/$\Sigma$PAH ratios, ranging from 3–7% across all spatial cells" (5.1 PAH Formation and Destruction in Low Metallicity Environments)
7. **Compare 3.3 um PAH map with ALMA CO (3-2)**: Qualitative comparison of the CAFE 3.3 um PAH flux map with ALMA CO (3-2) emission (ID 2012.1.00984.S); how the CO map was made is not described  
  > "This PAH emission correlates well with the CO (3-2) emission from ALMA (ID: 2012.1.00984.S; PI: A. Kepley)" (4.1 Spectral Variation across II Zw 40)
   - assumption: Co-spatiality with CO implies molecular-gas shielding protects small PAHs  
  > "This co-spatiality suggests that shielding from the molecular gas is likely conducive to the survival of these small PAHs" (4.1 Spectral Variation across II Zw 40)
   - fitting: _not stated_
   - validation: _not stated_
8. **Correlate PAH ratios with radiation hardness**: Pearson correlation of PAH band ratios against [Ne III]/[Ne II] across the eight grid cells  
  > "The 3.3/11.3 ratio exhibits a strong correlation (Pearson r=-0.92) to" (4.2 Resolving PAH band ratios in II Zw 40)
   - assumption: Short-to-long PAH ratio traces PAH size; [Ne III]/[Ne II] traces radiation field hardness  
  > "The PAH ratios are expressed as short-to-long wavelength ratios, where a higher value indicates a smaller PAH size distribution" (4.2 Resolving PAH band ratios in II Zw 40)
   - fitting: _not stated_
   - validation: _not stated_
9. **Estimate radiation field of SSC-N**: Linearly extrapolate the FUV spectrum to 912-2400 A, integrate, convert to luminosity and local flux at the cluster radius, then G0 and U  
  > "we extrapolate the spectrum linearly to span 912–2400 Å for the flux integration" (Estimate of the radiation field); "Using the relation $U = 0.88 \times G_0$ (cite: Draine2007b)" (Estimate of the radiation field)
   - assumption: D = 10 Mpc  
  > "Assuming the distance to II Zw 40 of $D$=10 Mpc" (Estimate of the radiation field)
   - assumption: Cluster radius R = 10 pc  
  > "assuming the cluster radius of $R$=10 pc (cite: Leitherer2018)" (Estimate of the radiation field)
   - fitting: _not stated_
   - validation: _not stated_
10. **Test NIRCam photometric recovery of 3.3 um PAH**: Synthetic photometry in F300M, F335M, F360M from the NIRSpec cube compared with CAFE 3.3 um PAH flux per spaxel, using the empirical Lai et al. 2020 relation  
  > "we compare synthetic photometry derived from three NIRCam filters (F300M, F335M, and F360M) using the `pyphot` software (cite: Morgan2025)" (5.2 Probing 3.3 um PAHs Photometrically in Dwarfs)
   - software: pyphot
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **JWST Science Calibration Pipeline** 1.12.5 (NIRSpec); 1.15.0 (MIRI MRS): Calibration of NIRSpec and MIRI MRS data  
  > "Science Calibration Pipeline version 1.12.5" (2 Observations and data reduction); "we followed the data reduction processes based on the Pipeline version 1.15.0" (2 Observations and data reduction)
- **Q3D** : Cube construction for NIRSpec at 0.05 arcsec spaxel size  
  > "we substituted it with a routine built in the" (2 Observations and data reduction)
- **reproject** : Python package used inside the Q3D routine to build the cube  
  > "that uses the Python package `reproject` to construct the cube" (2 Observations and data reduction)
- **CAFE** : Spectral decomposition of NIRSpec and MIRI spectra and IFU cube extraction  
  > "The spectrum from each NIRSpec spaxel is fitted with `CAFE`" (3 Analysis & Method)
- **pyphot** : Synthetic NIRCam photometry from NIRSpec spectra  
  > "using the `pyphot` software (cite: Morgan2025)" (5.2 Probing 3.3 um PAHs Photometrically in Dwarfs)
- **lmfit** : _not stated_
- **Astropy** : _not stated_
- **SciPy** : _not stated_

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 3.3 um PAH flux, total extraction (1.6 arcsec radius) | 2.21e-17 | not stated | W/m^2 | 5 | we find the 3.3 $\mu$m PAH flux measured in the total extraction is $2.21\times10^{-17}$ W/m$^{2}$ |
| Pearson correlation of 3.3/11.3 PAH ratio with [Ne III]/[Ne II] | -0.92 | not stated | dimensionless | 8 | The 3.3/11.3 ratio exhibits a strong correlation (Pearson r=-0.92) to |
| Maximum [Ne III]/[Ne II] (cell 8-8) | 35 | not stated | dimensionless | 5 | ratio reaches as high as 35 in cell 8-8 |
| 3.3/11.3 PAH ratio range across cells | ~0.13-0.42 | not stated | dimensionless | 5 | a 3.3/11.3 PAH ratio ranging from $\sim$0.13—0.42 |
| SigmaPAH_UL / SigmaPAH_IIZw40 | 2.81 | not stated | dimensionless | 6 | The resulting ratio of $\Sigma$PAH$_\mathrm{UL}$/$\Sigma$PAH$_\mathrm{IIZw40}$ is 2.81. |
| Pf delta / PAH 3.3 ratio near illuminated stars | ~2 | not stated | dimensionless | 3 | reaching $\sim$2 in regions close to the illuminated stars |
| Fractional PAH 3.3 strength (PAH 3.3/SigmaPAH) in moderate neon-ratio regions | as high as ~10% | not stated | percent | 6 | the fractional PAH 3.3 strength can reach values as high as $\sim$10% |
| Radiation field U in SSC-N | ~76,000 (75,680; log U ~ 4.88) | not stated | dimensionless | 9 | The radiation field intensity in SSC-N is exceptionally high, with $U \sim 76{,}000$ |
| Habing field G0 at SSC-N | ~8.6e4 | not stated | Habing units | 9 | corresponding to a Habing unit of G$_\mathrm{0}$$\sim 8.6 \times 10^4$ |
| PAH 3.3 / (PAH 3.3 + Pf delta) in F335M, 5-95% range | 54-89% | not stated | percent | 10 | range of PAH 3.3 / ($\mathrm{Pf}\,\delta$+PAH 3.3) is 54—89% |
| Surface-brightness threshold above which NIRCam photometry recovers 3.3 um PAH within 50% | 0.1 | not stated | MJy/sr | 10 | We find that the photometric method can recover the 3.3 $\mu$m PAH flux within 50% when the continuum-subtracted F335M surface brightness exceeds 0.1 MJy/sr |

## Qualitative findings

- 3.3 um PAH emission is concentrated near the northern SSC and is co-spatial with ALMA CO (3-2)  
  > "spatially coincident with the CO emission detected by ALMA" (6 Summary)
- Only the 3.3, 6.2 and 11.3 um PAH bands are robustly detected; 7.7, 8.6 and 17 um are not  
  > "we find in II Zw 40 the only detected PAHs are the 3.3, 6.2, and 11.3 $\mu$m bands" (3 Analysis & Method)

## Claim tuples

- H: Where do small PAHs survive in II Zw 40, and are they tied to molecular gas | E: CAFE 3.3 um PAH map from NIRSpec compared with ALMA CO (3-2) emission | R: 3.3 um PAH is concentrated near SSC-N and correlates well with CO (3-2) | F: Molecular gas likely shields the small PAHs there | **supported**
- H: Does radiation hardness photodestroy small PAHs | E: Compare PAH band ratios with [Ne III]/[Ne II] across eight 20 pc cells | R: 3.3/11.3 correlates strongly with [Ne III]/[Ne II] (Pearson r=-0.92) | F: Photo-processing of small grains occurs in the hardest radiation fields, but small PAHs are not preferentially destroyed throughout the galaxy | **partially**
- H: Does inhibited PAH growth at low metallicity shape the size distribution | E: Fractional PAH 3.3/SigmaPAH compared with star-forming references and a metallicity model | R: PAH 3.3/SigmaPAH reaches ~10% or more, higher than other star-forming environments | F: Inhibited growth may play a key role alongside photo-processing | **partially**
- H: Can NIRCam photometry recover the 3.3 um PAH flux in a dwarf galaxy | E: Synthetic F300M/F335M/F360M photometry from NIRSpec compared with CAFE fluxes | R: Recovery within 50% only when continuum-subtracted F335M exceeds 0.1 MJy/sr; Pf delta contaminates F335M | F: Caution is needed when using photometry for 3.3 um PAH in highly ionized dwarfs | **supported**

## Reasoning

- Why this data: High spatial resolution mid-infrared observations are needed to track PAH emission in low-metallicity dwarfs  
  > "high spatial resolution MIR observations are essential for tracking PAH emission in low-metallicity dwarf galaxies" (1 Introduction)
- Why this method: Spectra are continuum-dominated, so each PAH band is fitted locally rather than in one broad simultaneous fit  
  > "Given that the spectra are continuum-dominated, simultaneous spectroscopic fitting with a wide wavelength range across NIRSpec and MIRI is challenging." (3 Analysis & Method)
- Alternative: Photodissociation alone rejected as the dominant mechanism for the PAH size distribution  
  > "Photodissociation is clearly not the dominant mechanism determining the size distribution of PAHs in II Zw 40." (5.1 PAH Formation and Destruction in Low Metallicity Environments)
- Alternative: Double-photon heating of large PAHs proposed as an alternative to small-PAH enhancement  
  > "an alternative explanation for the disappearance of the 17 $\mu$m PAH feature together with the enhanced 3.3 $\mu$m PAH emission" (5.1 PAH Formation and Destruction in Low Metallicity Environments)
- How they decided it was enough: _not stated_
- Limitation (authors): MIRI imaging saturated near the northern SSC; pixels were replaced with synthetic photometry from the IFU cube  
  > "these images were saturated at the first frame of the ramp near the northern SSC" (3 Analysis & Method)
- Limitation (authors): Only eight grid cells have adequate S/N across both NIRSpec and MIRI  
  > "Spectra from regions farther from the clusters, however, suffer from low S/N" (3 Analysis & Method)
- Limitation (authors): Photometric recovery results are specific to II Zw 40  
  > "We emphasize that these findings are specific to II Zw 40" (5.2 Probing 3.3 um PAHs Photometrically in Dwarfs)
- Caveat (inferred, ours): ALMA CO (3-2) comparison is qualitative and its reduction is not described
- Caveat (inferred, ours): Correlation r=-0.92 rests on only eight cells that are partly correlated at the smoothed PSF
- Caveat (inferred, ours): Upper limit on total PAH is a fixed scaling from one total spectrum applied to all cells
- Caveat (inferred, ours): Inhibited growth versus photodestruction is argued from fractional strengths and a model not yet published (in prep.)

## Reproducibility

- Data public (paper): JWST data in MAST; ALMA program ID given  
  > "The data are available at the Mikulski Archive for Space Telescopes (MAST)" (2 Observations and data reduction); "CO (3-2) emission from ALMA (ID: 2012.1.00984.S; PI: A. Kepley)" (4.1 Spectral Variation across II Zw 40)
- Products in archive: _not stated_
- Code: CAFE code at github.com/GOALS-survey/CAFE  
  > "https://github.com/GOALS-survey/CAFE" (footnote 3)
- Missing: ALMA CO (3-2) calibration, imaging and map-making details
- Missing: CAFE configuration and fit priors
- Missing: Q3D cube-building parameters
- Missing: Quantitative method for the PAH-CO comparison
- Data volume (inferred): ALMA CO (3-2): likely a few GB of raw data; JWST NIRSpec and MIRI MRS cubes: a few GB; reproduction of the JWST part is the main cost
- Score (inferred): 3/5, JWST data public and CAFE code released with many numeric results, but the ALMA CO processing and the CAFE fit settings are not described.
- Rediscovery candidate: no, The main results come from JWST IFU fitting with unreported CAFE settings, and the ALMA part is a qualitative comparison without a processing recipe.

## Links

- Method: (cite: Diaz-Santos2025) (CAFE spectral decomposition code)
- Method: (cite: Lai2022) (Method for combining NIRSpec and MIRI cubes)
- Method: (cite: Lai2020) (1C PAH template and NIRCam 3.3 um PAH empirical relation)
- Companion: (cite: Consiglio2016) (Earlier ALMA observations of II Zw 40 indicating a low gas-to-dust ratio)
- Companion: (cite: Lai2023) (NGC 7469 PAH and neon ratio comparison)
- Related: JWST GO 2511
- Related: ALMA 2012.1.00984.S

## Checks

```json
{
 "quotes": 92,
 "quotes_ok": 92,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 111,
  "stated": 55,
  "rate": 0.495
 },
 "evidence_ok": true
}
```

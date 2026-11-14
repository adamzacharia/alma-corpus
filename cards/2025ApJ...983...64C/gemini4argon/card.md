# Polycyclic Aromatic Hydrocarbon and CO(2─1) Emission at 50─150 pc Scales in 70 Nearby Galaxies

`2025ApJ...983...64C` | The Astrophysical Journal 2025 | first author: Chown, Ryan | arXiv: 2410.05397 | DOI: 10.3847/1538-4357/adbd40

Card schema 1.0 | model gemini-4-argon | depth full | type large_program_or_survey

## Science

- Fields: nearby_galaxies, star_formation
- Question: Characterize the relationship, scaling relations, environmental variations, and galaxy-to-galaxy scatter between CO(2-1) and polycyclic aromatic hydrocarbon (PAH) emission at 50-150 pc scales in 70 nearby star-forming galaxies.  
  > "Combining Atacama Large Millimeter/sub-millimeter Array CO(2-1) mapping and JWST near- and mid-infrared imaging, we characterize the relationship between CO(2-1) and polycyclic aromatic hydrocarbon (PAH) emission at $\approx 100$ pc resolution in 70 nearby star-forming galaxies." (Abstract); "What are the median and scatter in the CO(2-1)/PAH band ratios across a representative sample of nearby star-forming galaxies at molecular cloud scales (50 to 150 pc)?" (Introduction)
- Target **70 nearby star-forming galaxies from PHANGS**: coordinates _not stated_; z/distance D <= 20 Mpc  
  > "Our targets are all part of the PHANGS surveys, and as such are relatively massive ($M_\star \gtrsim 10^{9.5}~\mathrm{M_\odot}$), star-forming (SFR/$M_\star \gtrsim 10^{-11}~\mathrm{yr^{-1}}$), and moderate inclination ($i \lesssim 70^\circ$) galaxies within $D \lesssim 20$ Mpc (cite: leroy2021)." (Data and Methods); distance from (cite: leroy2021)  
  > "Our targets are all part of the PHANGS surveys, and as such are relatively massive ($M_\star \gtrsim 10^{9.5}~\mathrm{M_\odot}$), star-forming (SFR/$M_\star \gtrsim 10^{-11}~\mathrm{yr^{-1}}$), and moderate inclination ($i \lesssim 70^\circ$) galaxies within $D \lesssim 20$ Mpc (cite: leroy2021)." (Data and Methods)
- Target **NGC 2903**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00650.S, 2013.1.00803.S, 2013.1.01161.S, 2015.1.00121.S, 2015.1.00782.S, 2015.1.00925.S, 2015.1.00956.S, 2016.1.00386.S, 2017.1.00392.S, 2017.1.00766.S, 2017.1.00886.L, 2018.1.01321.S, 2018.1.01651.S, 2018.A.00062.S, 2019.1.01235.S, 2019.2.00129.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: Includes short- and zero-spacing data  
  > "All maps include short- and zero-spacing data and are expected to achieve full flux recovery." (ALMA CO(2-1))
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: approx 1.0'' (median 98 pc, 16-84% range 63-129 pc)  
  > "The native resolution is $\approx 1.0\ensuremath{''}$, varying slightly from galaxy to galaxy." (ALMA CO(2-1)); "Over the range of distances of the galaxies in the sample, the working resolution for PHANGS–ALMA corresponds to median $98$ pc with a $16{-}84\%$ range of $63{-}129$ pc (cite: leroy2021)." (Analysis approach)
- max recoverable scale: _not stated_
- sensitivity: approx +- 1 K km s^-1 in flat CO maps  
  > "Much of this reflects the statistical noise in the PHANGS–ALMA CO maps, which often approaches $\approx \pm 1$ K km s$^{-1}$ in the “flat” CO maps that we use." (Results)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PHANGS-ALMA survey  
  > "We use PHANGS–ALMA CO (2-1) observations, which are described in (cite: leroy2021)." (ALMA CO(2-1)); "This paper makes use of the following ALMA data, which have been processed as part of the PHANGS–ALMA survey:" (Acknowledgments)
- Line: CO 2-1 (not stated)
- Other facility **JWST**: MIRI and NIRCam imaging in F150W, F187N, F200W, F300M, F335M, F360M, F770W, F1130W, and F2100W from PHANGS-JWST Cycle 1 (GO 2107) and Cycle 2 (GO 3707) Treasuries  
  > "We use JWST MIRI and NIRCam imaging of 19 galaxies from the PHANGS-JWST Cycle 1 Treasury (cite: lee2023). These data cover the F335M, F770W, and F1130W bands, each of which captures a strong PAH feature (cite: tielens2008)." (JWST imaging of PAH emission); "We also analyze 51 galaxies from a new Cycle 2 Treasury (GO 3707, PI: A. Leroy), which we describe in Appendix 8." (JWST imaging of PAH emission); "These observations are associated with programs 2107 and 3707." (Acknowledgments)
- Other facility **VLT/MUSE**: Optical integral field spectroscopy of H-alpha and ionized gas emission used to define nebular/H II region masks as part of PHANGS-MUSE  
  > "The subset of 19 targets presented in (cite: lee2023) and (cite: williams2024) have both F1130W imaging and “nebular masks,” which identify H II regions based on a morphological decomposition of the H$\alpha$ emission observed by the Very Large Telescope’s Multi-Unit Spectroscopic Explorer (cite: groves2023)." (Data and Methods); "We define galaxy centers using the masks in (cite: querejeta2021), which are based on near-IR stellar morphology, and nebular regions following (cite: santoro2022; groves2023), which are based on ionized gas emission observed by the VLT/MUSE as part of the PHANGS-MUSE survey (cite: emsellem2022)." (Environment masks)
- External data: PHANGS-ALMA CO(2-1) observations and strict masks  
  > "We use PHANGS–ALMA CO (2-1) observations, which are described in (cite: leroy2021)." (ALMA CO(2-1)); "We additionally ensure that all significant CO emission is included by combining the fixed-width velocity mask with the “strict” mask from (cite: leroy2021)." (ALMA CO(2-1)) [from (cite: leroy2021)]
- External data: Galaxy inclinations  
  > "We correct all intensities to face-on values by scaling by $\cos i$, where $i$ is the galaxy inclination from (cite: lang2020) and/or (cite: leroy2021)." (Analysis approach) [from (cite: lang2020) and/or (cite: leroy2021)]
- External data: Galaxy stellar masses and star formation rates  
  > "lists the targets of both the Cycle 1 and Cycle 2 PHANGS Treasury, along with the list of bands observed and the stellar mass and SFR for each target" (Appendix: Cycle 2 JWST Imaging of PHANGS Galaxies); "We also report the stellar mass and SFR/$M_\star$, adopted from (cite: leroy2019), the brightness of band $X$ in that galaxy at $I_{\rm \nu}^X = 1$ MJy sr$^{-1}$, the number of sight lines analyzed, and Spearman’s rank correlation coefficient relating the PAH and CO emission for each sightline." (Fits for individual galaxies) [from (cite: leroy2019; leroy2021)]
- External data: Galaxy center masks based on near-IR stellar morphology  
  > "We define galaxy centers using the masks in (cite: querejeta2021), which are based on near-IR stellar morphology, and nebular regions following (cite: santoro2022; groves2023), which are based on ionized gas emission observed by the VLT/MUSE as part of the PHANGS-MUSE survey (cite: emsellem2022)." (Environment masks) [from (cite: querejeta2021)]
- External data: Nebular / H II region masks from PHANGS-MUSE  
  > "We define galaxy centers using the masks in (cite: querejeta2021), which are based on near-IR stellar morphology, and nebular regions following (cite: santoro2022; groves2023), which are based on ionized gas emission observed by the VLT/MUSE as part of the PHANGS-MUSE survey (cite: emsellem2022)." (Environment masks) [from (cite: santoro2022; groves2023)]
- External data: PHANGS-JWST Cycle 1 imaging of 19 galaxies  
  > "We use JWST MIRI and NIRCam imaging of 19 galaxies from the PHANGS-JWST Cycle 1 Treasury (cite: lee2023)." (JWST imaging of PAH emission) [from (cite: lee2023); (cite: williams2024)]

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
- masking: Flat velocity window masks (20 to 200 km/s around local mean velocity) combined with strict mask  
  > "These “flat” maps are produced following (cite: neumann2023) using a procedure analogous to spectral stacking (cite: schruba2011)." (ALMA CO(2-1)); "The velocity window is adapted to the disk-average line width of each individual galaxy and can vary from 20 to 200 km/s. We additionally ensure that all significant CO emission is included by combining the fixed-width velocity mask with the “strict” mask from (cite: leroy2021)." (ALMA CO(2-1))
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Short- and zero-spacing data included  
  > "All maps include short- and zero-spacing data and are expected to achieve full flux recovery." (ALMA CO(2-1))
- smoothing: _not stated_
- final beam: approx 1.0'' (median 98 pc, 16-84% range 63-129 pc)  
  > "The native resolution is $\approx 1.0\ensuremath{''}$, varying slightly from galaxy to galaxy." (ALMA CO(2-1)); "Over the range of distances of the galaxies in the sample, the working resolution for PHANGS–ALMA corresponds to median $98$ pc with a $16{-}84\%$ range of $63{-}129$ pc (cite: leroy2021)." (Analysis approach)
- final rms: approx +- 1 K km s^-1 in flat CO maps  
  > "Much of this reflects the statistical noise in the PHANGS–ALMA CO maps, which often approaches $\approx \pm 1$ K km s$^{-1}$ in the “flat” CO maps that we use." (Results)

### Inherited from earlier work

- ALMA CO(2-1) observations, calibration, imaging, and strict masks  
  > "We use PHANGS–ALMA CO (2-1) observations, which are described in (cite: leroy2021)." (ALMA CO(2-1)) [from (cite: leroy2021)]
- Production of flat integrated CO(2-1) intensity maps  
  > "These “flat” maps are produced following (cite: neumann2023) using a procedure analogous to spectral stacking (cite: schruba2011)." (ALMA CO(2-1)) [from (cite: neumann2023); (cite: schruba2011)]
- JWST data reduction with pjpipe  
  > "Reduction for both data sets was done using the PHANGS-JWST pipeline (`pjpipe`), following (cite: williams2024)." (JWST imaging of PAH emission) [from (cite: williams2024)]
- F770W stellar continuum subtraction using F200W or F300M scaling factors  
  > "We calculate stellar-continuum-subtracted F770W surface brightness $I_{\rm F770W}^{\rm PAH}$ by subtracting F200W (Cycle 1) or F300M (Cycle 2) times a scaling factor (one factor per band) following (cite: sutter2024)." (JWST imaging of PAH emission) [from (cite: sutter2024)]
- F335M stellar continuum subtraction using F300M and F360M  
  > "We use the continuum subtraction method defined by H. Koziol et al. (in preparation) based on (cite: sandstrom2023), where the F300M and F360M (for Cycle 1) are used to estimate continuum." (JWST imaging of PAH emission) [from H. Koziol et al. (in preparation); (cite: sandstrom2023)]
- PSF convolution of JWST images to match CO(2-1) resolution  
  > "Using `webbpsf`-generated JWST PSFs, we convolve all JWST PAH images to share the same resolution of the corresponding CO (2-1) data following (cite: aniano2011) and (cite: williams2024)." (Analysis approach) [from (cite: aniano2011); (cite: williams2024)]
- Environment classification and masks for centers, nebular regions, and diffuse regions  
  > "We define galaxy centers using the masks in (cite: querejeta2021), which are based on near-IR stellar morphology, and nebular regions following (cite: santoro2022; groves2023), which are based on ionized gas emission observed by the VLT/MUSE as part of the PHANGS-MUSE survey (cite: emsellem2022)." (Environment masks); "See (cite: pathak2024) for further details on a similar application of these environment masks." (Environment masks) [from (cite: querejeta2021); (cite: santoro2022; groves2023); (cite: pathak2024)]

### Not stated but needed to reproduce (our reading)

- Exact velocity integration window widths and reference velocity tracer chosen for each individual galaxy's flat CO(2-1) map
- Exact F335M continuum subtraction equations/coefficients from H. Koziol et al. (in preparation)
- Coordinates and dimensions of the elliptical apertures used to mask bright foreground stars and background galaxies
- Exact bin widths and spacing used for the logarithmically-spaced MIR intensity bins prior to linmix fitting
- SpecificPHANGS-ALMA internal/public data release version used

## Analysis recipe

1. **Reduce JWST imaging and subtract stellar continuum to isolate PAH emission**: Reduce Cycle 1 and Cycle 2 JWST NIRCam and MIRI mosaics using pjpipe, mask bright stars and background galaxies with elliptical apertures, and subtract stellar continuum from F770W (using 0.13*F200W or 0.22*F300M) and F335M (using F300M and F360M).  
  > "Reduction for both data sets was done using the PHANGS-JWST pipeline (`pjpipe`), following (cite: williams2024)." (JWST imaging of PAH emission); "In our sample, the F770W stellar continuum correction (F770W$_\star = 0.22\times$F300M, or $0.13\times$F200W for Cycle 1) tends to be largest in the gas-poor, high stellar surface density inner regions of galaxies, including bars and bulges, which have high stellar-to-gas ratios." (JWST imaging of PAH emission); "We use the continuum subtraction method defined by H. Koziol et al. (in preparation) based on (cite: sandstrom2023), where the F300M and F360M (for Cycle 1) are used to estimate continuum." (JWST imaging of PAH emission)
   - software: pjpipe, jwst
   - parameter: F770W_star = 0.22 * F300M (Cycle 2) or 0.13 * F200W (Cycle 1)  
  > "In our sample, the F770W stellar continuum correction (F770W$_\star = 0.22\times$F300M, or $0.13\times$F200W for Cycle 1) tends to be largest in the gas-poor, high stellar surface density inner regions of galaxies, including bars and bulges, which have high stellar-to-gas ratios." (JWST imaging of PAH emission)
   - assumption: Hot dust continuum in F770W and stellar continuum in F1130W are negligible and not subtracted  
  > "The F770W filter also captures emission from hot, very small dust grains, but this has a small effect (cite: baron2024a) and we do not subtract any underlying dust continuum." (JWST imaging of PAH emission); "We do not consider stellar continuum correction necessary for F1130W." (How to estimate CO (2-1) intensity from PAH emission maps)
   - fitting: _not stated_
   - validation: _not stated_
2. **Construct flat integrated ALMA CO(2-1) intensity maps**: Integrate PHANGS-ALMA CO(2-1) cubes over a fixed-width velocity window (20-200 km/s) around the local mean velocity combined with the strict mask to capture >90% of CO flux without S/N clipping bias.  
  > "We use a noisy but uniform and high-completeness version of the CO (2-1) maps to ensure that $>90\,\%$ of the CO flux enters our analysis and that our mean trends will be unbiased by signal-to-noise based clipping of the CO data (cite: leroy2023)." (ALMA CO(2-1)); "The velocity window is adapted to the disk-average line width of each individual galaxy and can vary from 20 to 200 km/s. We additionally ensure that all significant CO emission is included by combining the fixed-width velocity mask with the “strict” mask from (cite: leroy2021)." (ALMA CO(2-1))
   - parameter: Velocity integration window = 20 to 200 km/s  
  > "The velocity window is adapted to the disk-average line width of each individual galaxy and can vary from 20 to 200 km/s." (ALMA CO(2-1))
   - assumption: No CO-to-H2 conversion factor is adopted when analyzing intensities  
  > "To avoid introducing systematic uncertainties, we analyze CO(2-1) intensities and do not adopt a CO-to-H$_2$ conversion factor." (Analysis approach)
   - fitting: _not stated_
   - validation: Captures >90% of the CO flux with well-defined noise  
  > "We use a noisy but uniform and high-completeness version of the CO (2-1) maps to ensure that $>90\,\%$ of the CO flux enters our analysis and that our mean trends will be unbiased by signal-to-noise based clipping of the CO data (cite: leroy2023)." (ALMA CO(2-1))
3. **Match angular resolution, reproject to common grid, correct for inclination, and apply environment and surface brightness masks**: Convolve JWST images to CO(2-1) resolution using webbpsf PSFs, reproject CO, JWST, and environment masks onto a grid with pixel size 1/3 of CO PSF FWHM, multiply intensities by cos(i), and select bright pixels (I_F770W^PAH >= 0.5 MJy sr^-1; I_F335M^PAH > 0.1 MJy sr^-1).  
  > "Using `webbpsf`-generated JWST PSFs, we convolve all JWST PAH images to share the same resolution of the corresponding CO (2-1) data following (cite: aniano2011) and (cite: williams2024). Then we define an astrometric grid with pixels $1/3\times$ the CO PSF FWHM in size so that approximately 9 pixels represent an independent measurement." (Analysis approach); "We correct all intensities to face-on values by scaling by $\cos i$, where $i$ is the galaxy inclination from (cite: lang2020) and/or (cite: leroy2021)." (Analysis approach); "To avoid lines of sight where H I is expected to make up most of the ISM, we consider only regions that have inclination-corrected $I_\mathrm{F770W}^{\rm PAH} \geq 0.5~\mathrm{MJy~sr^{-1}}$ (cite: leroy2023a)." (Analysis approach)
   - software: webbpsf
   - parameter: Grid pixel size = 1/3 * CO PSF FWHM  
  > "Then we define an astrometric grid with pixels $1/3\times$ the CO PSF FWHM in size so that approximately 9 pixels represent an independent measurement." (Analysis approach)
   - parameter: I_F770W^PAH >= 0.5 MJy sr^-1 threshold  
  > "To avoid lines of sight where H I is expected to make up most of the ISM, we consider only regions that have inclination-corrected $I_\mathrm{F770W}^{\rm PAH} \geq 0.5~\mathrm{MJy~sr^{-1}}$ (cite: leroy2023a)." (Analysis approach)
   - parameter: I_F335M^PAH > 0.1 MJy sr^-1 threshold  
  > "As a result, we impose an additional threshold for analyzing the $3.3~\mu$m emission, considering only lines of sight with $I_{\rm F335M}^{\rm PAH} > 0.1$ MJy sr$^{-1}$." (Analysis approach)
   - assumption: Regions with inclination-corrected I_F770W^PAH >= 0.5 MJy sr^-1 are dominated by molecular gas (Sigma_mol >= 4 M_sun pc^-2)  
  > "To avoid lines of sight where H I is expected to make up most of the ISM, we consider only regions that have inclination-corrected $I_\mathrm{F770W}^{\rm PAH} \geq 0.5~\mathrm{MJy~sr^{-1}}$ (cite: leroy2023a)." (Analysis approach); "Our results formally apply to regions where molecular gas is likely to constitute a significant fraction of the ISM, with $\Sigma_{\rm mol} \gtrsim 4$ M$_\odot$ pc$^{-2}$." (Discussion)
   - fitting: _not stated_
   - validation: Checked fraction of total flux and area captured by brightness cut (93-100% of flux across bands, 51% of area)  
  > "Our analysis captures the majority of the flux in all bands, but only includes about half the total observed area." (Table 1 notes)
4. **Compute CO-to-PAH ratios, correlation coefficients, and power-law scaling relations across environments and individual galaxies**: Compute Spearman rank correlation coefficients, median and MAD scatter of log10(CO/X), bin I_CO(2-1) in logarithmically-spaced bins of MIR intensity I_X, and fit power-law relations using linmix for the full sample, sub-environments, and individual galaxies, as well as fitting galaxy normalizations against M_star and SFR/M_star.  
  > "For each MIR band $X$, we record the Spearman rank correlation coefficient ($r$), as well as the median and scatter in the ratio $I_{\rm CO(2-1)}/I_{\rm X}$. We then calculate a best-fit power law relating $I_{\rm CO(2-1)}$ to $I_{\rm X}$." (Analysis approach); "We construct logarithmically-spaced bins in $I_\nu^\mathrm{X}$ and then compute the median and scatter, captured by the 16-84% range, of $I_\mathrm{CO(2-1)}$ within each bin. We perform linear regression on these binned measurements using `linmix` a hierarchical Bayesian method described in (cite: kelly2007)." (Analysis approach); "We compute the normalization of the best-fit CO(2-1) versus F770W$_\mathrm{PAH}$ power law for each galaxy, $C_\mathrm{F770W}^\mathrm{PAH}$, by performing a linear fit of $\log_{10}I_\mathrm{CO(2-1)}$ versus $\log_{10}\ensuremath{I^\mathrm{PAH}_{\rm F770W}}$ for each galaxy." (Galaxy to galaxy variations)
   - software: linmix
   - parameter: Pivot point x_0 = median(x)  
  > "where the pivot $x_0\equiv \mathrm{median}(x)$. Re-centering the fit at $x_0$ ensures minimal covariance between the best-fit $m$ and $b$." (Analysis approach)
   - fitting: Hierarchical Bayesian linear regression (linmix) incorporating measurement errors in both variables on binned median and 16-84% range measurements  
  > "We construct logarithmically-spaced bins in $I_\nu^\mathrm{X}$ and then compute the median and scatter, captured by the 16-84% range, of $I_\mathrm{CO(2-1)}$ within each bin. We perform linear regression on these binned measurements using `linmix` a hierarchical Bayesian method described in (cite: kelly2007)." (Analysis approach)
   - validation: Checked for correlations of galaxy normalization with distance (r = -0.04, p = 0.78) and cos(i) (r = 0.24, p = 0.06) to test orientation and resolution biases  
  > "We also checked for correlations with distance and inclination to test how orientation and resolution might bias our results. We found that the normalization is uncorrelated with distance ($r=-0.04, p=0.78$), and weakly correlated with $\cos i$ ($r=0.24, p=0.06$)." (Galaxy to galaxy variations)

## Software

- **pjpipe** : PHANGS-JWST pipeline wrapper used to reduce JWST NIRCam and MIRI imaging and produce mosaics  
  > "Reduction for both data sets was done using the PHANGS-JWST pipeline (`pjpipe`), following (cite: williams2024). `pjpipe` is a wrapper on `jwst`, tailored to produce mosaics of images with extended emission." (JWST imaging of PAH emission)
- **jwst** : Underlying STScI JWST data reduction pipeline wrapped by pjpipe  
  > "`pjpipe` is a wrapper on `jwst`, tailored to produce mosaics of images with extended emission." (JWST imaging of PAH emission)
- **webbpsf** : Generating JWST PSFs used to convolve JWST PAH images to match CO(2-1) angular resolution  
  > "Using `webbpsf`-generated JWST PSFs, we convolve all JWST PAH images to share the same resolution of the corresponding CO (2-1) data following (cite: aniano2011) and (cite: williams2024)." (Analysis approach)
- **linmix** : Hierarchical Bayesian linear regression of binned CO(2-1) vs PAH intensities  
  > "We perform linear regression on these binned measurements using `linmix` a hierarchical Bayesian method described in (cite: kelly2007)." (Analysis approach)
- **astropy** : General astronomical data analysis  
  > "astropy (cite: astropy-collaboration2013; astropy-collaboration2018; astropy-collaboration2022)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median log10(CO(2-1) / F770W_PAH) ratio (all pixels) | 0.03 | 0.35 | dex (K km s^-1 / (MJy sr^-1)) | 4 | / F770W$_\mathrm{PAH}$ / 70 / 2090731 / $0.03 \pm 0.35$ / $0.64$ / $1.39 \pm 0.06$ / $0.90 \pm 0.07$ / $1.44$ / $0.43$ / |
| Power-law slope m for CO(2-1) vs F770W_PAH (all pixels) | 0.90 | 0.07 | dimensionless | 4 | / F770W$_\mathrm{PAH}$ / 70 / 2090731 / $0.03 \pm 0.35$ / $0.64$ / $1.39 \pm 0.06$ / $0.90 \pm 0.07$ / $1.44$ / $0.43$ /; $m=0.90\pm 0.07$, agree reasonably well with previous work on much smaller samples or at lower resolution |
| Power-law intercept b for CO(2-1) vs F770W_PAH (all pixels, at x_0 = 1.44) | 1.39 | 0.06 | dex (K km s^-1) | 4 | / F770W$_\mathrm{PAH}$ / 70 / 2090731 / $0.03 \pm 0.35$ / $0.64$ / $1.39 \pm 0.06$ / $0.90 \pm 0.07$ / $1.44$ / $0.43$ / |
| Spearman rank correlation coefficient r for CO(2-1) vs F770W_PAH (all pixels) | 0.64 | not stated | dimensionless | 4 | / F770W$_\mathrm{PAH}$ / 70 / 2090731 / $0.03 \pm 0.35$ / $0.64$ / $1.39 \pm 0.06$ / $0.90 \pm 0.07$ / $1.44$ / $0.43$ / |
| Median log10(CO(2-1) / F335M_PAH) ratio (all pixels) | 1.27 | 0.38 | dex (K km s^-1 / (MJy sr^-1)) | 4 | / F335M$_\mathrm{PAH}$ / 19 / 296834 / $1.27 \pm 0.38$ / $0.58$ / $1.38 \pm 0.07$ / $1.01 \pm 0.10$ / $0.10$ / $0.44$ / |
| Power-law slope m for CO(2-1) vs F335M_PAH (all pixels) | 1.01 | 0.10 | dimensionless | 4 | / F335M$_\mathrm{PAH}$ / 19 / 296834 / $1.27 \pm 0.38$ / $0.58$ / $1.38 \pm 0.07$ / $1.01 \pm 0.10$ / $0.10$ / $0.44$ / |
| Median log10(CO(2-1) / F1130W) ratio (all pixels) | -0.12 | 0.37 | dex (K km s^-1 / (MJy sr^-1)) | 4 | / F1130W / 20 / 972892 / $-0.12 \pm 0.37$ / $0.63$ / $1.20 \pm 0.08$ / $1.02 \pm 0.09$ / $1.34$ / $0.44$ / |
| Power-law slope m for CO(2-1) vs F1130W (all pixels) | 1.02 | 0.09 | dimensionless | 4 | / F1130W / 20 / 972892 / $-0.12 \pm 0.37$ / $0.63$ / $1.20 \pm 0.08$ / $1.02 \pm 0.09$ / $1.34$ / $0.44$ / |
| Median log10(CO(2-1) / F770W_PAH) ratio (outside centers) | 0.02 | 0.35 | dex (K km s^-1 / (MJy sr^-1)) | 4 | / F770W$_\mathrm{PAH}$ / 70 / 2041245 / $0.02 \pm 0.35$ / $0.62$ / $1.12 \pm 0.07$ / $0.98 \pm 0.08$ / $1.16$ / $0.42$ / |
| Power-law slope m for CO(2-1) vs F770W_PAH (outside centers) | 0.98 | 0.08 | dimensionless | 4 | / F770W$_\mathrm{PAH}$ / 70 / 2041245 / $0.02 \pm 0.35$ / $0.62$ / $1.12 \pm 0.07$ / $0.98 \pm 0.08$ / $1.16$ / $0.42$ / |
| Median log10(CO(2-1) / F770W_PAH) ratio (galaxy centers) | 0.18 | 0.33 | dex (K km s^-1 / (MJy sr^-1)) | 4 | / F770W$_\mathrm{PAH}$ / 58 / 49469 / $0.18 \pm 0.33$ / $0.88$ / $1.52 \pm 0.07$ / $0.80 \pm 0.07$ / $1.44$ / $0.42$ / |
| Power-law slope m for CO(2-1) vs F770W_PAH (galaxy centers) | 0.80 | 0.07 | dimensionless | 4 | / F770W$_\mathrm{PAH}$ / 58 / 49469 / $0.18 \pm 0.33$ / $0.88$ / $1.52 \pm 0.07$ / $0.80 \pm 0.07$ / $1.44$ / $0.42$ / |
| Median log10(CO(2-1) / F770W_PAH) ratio (nebular regions, Cycle 1) | -0.02 | 0.34 | dex (K km s^-1 / (MJy sr^-1)) | 4 | / F770W$_\mathrm{PAH}$ / 19 / 186605 / $-0.02 \pm 0.34$ / $0.75$ / $1.02 \pm 0.09$ / $1.03 \pm 0.11$ / $1.09$ / $0.40$ / |
| Median log10(CO(2-1) / F770W_PAH) ratio (diffuse regions, Cycle 1) | 0.08 | 0.38 | dex (K km s^-1 / (MJy sr^-1)) | 4 | / F770W$_\mathrm{PAH}$ / 19 / 632119 / $0.08 \pm 0.38$ / $0.52$ / $0.72 \pm 0.13$ / $1.20 \pm 0.27$ / $0.66$ / $0.47$ / |
| Galaxy-to-galaxy scatter in CO/F770W_PAH normalization | 0.17 | not stated | dex | 4 | Specifically, the normalization of the CO-PAH relation scatters by $\pm 0.17$ dex from galaxy to galaxy.; / F770W$_\mathrm{PAH}$ / 70 / $-0.21 \pm 0.04$ / $0.03 \pm 0.02$ / $-10.14$ / $-0.50$ / $0.13$ / $0.17$ / |
| Slope of log10(C_F770W^PAH) vs log10(SFR/M_star) | -0.21 | 0.04 | dimensionless | 4 | \nonumber \log_{10}\ensuremath{C_\mathrm{F770W}^\mathrm{PAH}}= -0.21 \pm 0.04~(\log_{10}\ensuremath{\mathrm{SFR}/M_\star}+10.14)\\ +0.03 \pm 0.02.; / F770W$_\mathrm{PAH}$ / 70 / $-0.21 \pm 0.04$ / $0.03 \pm 0.02$ / $-10.14$ / $-0.50$ / $0.13$ / $0.17$ / |
| Slope of log10(C_F770W^PAH) vs log10(M_star) | 0.15 | 0.04 | dimensionless | 4 | \nonumber \log_{10}\ensuremath{C_\mathrm{F770W}^\mathrm{PAH}}= 0.15 \pm 0.04~(\log_{10} M_\star -10.34) \\ +0.06 \pm 0.02,; / F770W$_\mathrm{PAH}$ / 70 / $0.15 \pm 0.04$ / $0.06 \pm 0.02$ / $10.34$ / $0.38$ / $0.16$ / $0.17$ / |
| Renormalized power-law slope m for CO(2-1) vs F770W_PAH (all pixels) | 0.88 | 0.06 | dimensionless | 4 | \log_{10}I_\mathrm{CO(2-1)}=(0.88\pm 0.06)(x-1.44)+(1.36\pm 0.06), |
| Renormalized power-law intercept b for CO(2-1) vs F770W_PAH (all pixels, at x_0 = 1.44) | 1.36 | 0.06 | dex (K km s^-1) | 4 | \log_{10}I_\mathrm{CO(2-1)}=(0.88\pm 0.06)(x-1.44)+(1.36\pm 0.06), |

## Qualitative findings

- CO(2-1) and PAH emission (3.3, 7.7, and 11.3 um) exhibit strong, nearly linear correlations at 50-150 pc scales across 70 nearby star-forming galaxies.  
  > "Focusing on regions of galaxies where most of the gas is likely to be molecular, we find strong correlations between CO(2-1) and 3.3 $\mu$m, $7.7\mu$m, and $11.3~\mu$m PAH emission, estimated from JWST’s F335M, F770W, and F1130W filters." (Abstract)
- CO-to-PAH ratios and scaling relations near H II regions are very similar to those in diffuse disk regions, likely because the 70 pc resolution nebular masks include well-shielded molecular gas surrounding the H II regions.  
  > "We find that CO-to-PAH ratios and scaling relationships near H II regions are similar to those in diffuse sight lines." (Abstract); "The similarity of the CO-vs-PAH relationship in diffuse and nebular regions likely results from the fact that the H II region masks that we use (cite: groves2023) are based on data with coarse resolution (median $70$ pc) compared to the actual size of most H II regions (cite: barnes2022)." (Nebular and diffuse regions)
- Galaxy centers exhibit higher overall intensities and ~0.16-0.2 dex (~60%) higher CO-to-PAH ratios compared to galaxy disks, likely driven by lower X_CO in galaxy centers.  
  > "On average the CO-to-PAH ratio is $\approx 0.16$ dex ($\approx 60\%$) higher in galaxy centers compared to disks, and the median $I_{\rm CO(2-1)}$ in centers appear higher than that found for disks at fixed $I^\mathrm{PAH}_{\rm F770W}$." (Centers and disks of galaxies); "may indicate that $X_{\rm CO}$ represents the dominant effect, offsetting these other PAH-enhancing effects." (Centers and disks of galaxies)
- Galaxy-to-galaxy normalizations of CO at fixed PAH intensity correlate positively with stellar mass and anti-correlate with specific star formation rate.  
  > "Consistent with previous work we find a mild positive correlation between the CO/PAH ratio at fixed $I^\mathrm{PAH}_{\rm F770W}$ and $M_\star$ and an anti-correlation between the CO/PAH normalization and $\mathrm{SFR}/M_\star$." (Galaxy to galaxy variations)

## Claim tuples

- H: PAH emission in JWST NIR and MIR bands correlates with and scales nearly linearly with CO(2-1) emission at molecular cloud scales (50-150 pc) across the nearby star-forming galaxy population. | E: Compare resolution-matched ALMA CO(2-1) and JWST F335M_PAH, F770W_PAH, and F1130W intensities across 70 PHANGS galaxies at ~100 pc resolution and fit power-law scaling relations with linmix. | R: Rank correlations r = 0.58 to 0.64 across all pixels, with power-law slopes m = 0.8 to 1.3 (e.g., m = 0.90 +- 0.07 for F770W_PAH, m = 1.01 +- 0.10 for F335M_PAH, m = 1.02 +- 0.09 for F1130W). | F: Strong, approximately linear scaling relationships exist between CO(2-1) and 3.3, 7.7, and 11.3 um PAH emission at 50-150 pc scales. | **supported**
- H: CO-to-PAH ratios and scaling relations differ significantly between nebular (H II) regions and diffuse disk regions due to PAH destruction inside H II regions. | E: Apply VLT/MUSE nebular masks to 19 Cycle 1 galaxies to separate disk sight lines into nebular and diffuse regions and compare their CO-to-PAH ratios and power-law fits. | R: Median CO/F770W_PAH in H II regions is -0.02 +- 0.34 dex vs 0.08 +- 0.38 dex in diffuse regions (~0.10 dex difference), with similar power-law scaling relations. | F: At ~100 pc resolution, CO-to-PAH ratios and scaling relations near H II regions are very similar to diffuse regions, except nebular sight lines have higher overall intensities, likely because the 70 pc masks blend H II regions with surrounding shielded gas. | **refuted**
- H: Galaxy centers exhibit different CO-to-PAH ratios compared to galaxy disks due to extreme ISM conditions and lower X_CO. | E: Use morphological center masks across 70 galaxies to compare CO-to-PAH ratios and power-law fits in galaxy centers versus disks. | R: Median log10(CO/F770W_PAH) is 0.18 +- 0.33 in centers vs 0.02 +- 0.35 outside centers, an enhancement of ~0.16 dex (~60%). | F: Galaxy centers show higher overall intensities and systematically enhanced CO-to-PAH ratios compared to galaxy disks, consistent with suppressed X_CO in centers dominating over stronger radiation fields. | **supported**
- H: Galaxy-to-galaxy variations in the CO(2-1)-to-PAH normalization correlate with global galaxy properties that trace radiation field strength and ISM properties. | E: Fit the CO-PAH normalization C_band at I_PAH = 1 MJy sr^-1 for each of the 70 galaxies and perform linear regressions against log10(M_star) and log10(SFR/M_star). | R: Galaxy normalizations scatter by +-0.17 dex (0.19 dex in abstract) and correlate with log10(M_star) (slope 0.15 +- 0.04, r = 0.38) and anti-correlate with log10(SFR/M_star) (slope -0.21 +- 0.04, r = -0.50). | F: Galaxy-to-galaxy offsets in CO/PAH normalization are not random; they anti-correlate with specific star formation rate and correlate with stellar mass, allowing an empirical renormalization prescription. | **supported**

## Reasoning

- Why this data: Combining PHANGS-JWST Cycle 1 and 2 treasuries with PHANGS-ALMA CO(2-1) expands the sample of ~100 pc resolution CO-PAH comparisons by over an order of magnitude to 70 galaxies, while flat CO maps ensure >90% flux completeness without S/N clipping bias.  
  > "Leveraging a new Cycle 2 JWST treasury program targeting nearby galaxies, we expand the sample size by more than an order of magnitude compared to previous $\approx 100$ pc resolution CO-PAH comparisons." (Abstract); "We use a noisy but uniform and high-completeness version of the CO (2-1) maps to ensure that $>90\,\%$ of the CO flux enters our analysis and that our mean trends will be unbiased by signal-to-noise based clipping of the CO data (cite: leroy2023)." (ALMA CO(2-1))
- Why this method: Because ALMA CO maps are much less sensitive than JWST MIR maps at matched resolution, MIR intensity is used as the independent x-axis and CO is averaged in logarithmic bins before Bayesian linear regression with linmix, avoiding S/N clipping bias.  
  > "Because the PHANGS–ALMA CO maps are much less sensitive than the JWST F770W and F1130W maps at matched angular resolution (cite: leroy2023), we treat the mid-IR imaging as the independent ($x$) axis for this calculation." (Analysis approach); "We construct logarithmically-spaced bins in $I_\nu^\mathrm{X}$ and then compute the median and scatter, captured by the 16-84% range, of $I_\mathrm{CO(2-1)}$ within each bin. We perform linear regression on these binned measurements using `linmix` a hierarchical Bayesian method described in (cite: kelly2007)." (Analysis approach)
- Alternative: Adopting a CO-to-H2 conversion factor was rejected for the main analysis to avoid introducing systematic uncertainties.  
  > "To avoid introducing systematic uncertainties, we analyze CO(2-1) intensities and do not adopt a CO-to-H$_2$ conversion factor." (Analysis approach)
- Alternative: Subtracting hot dust continuum from F770W was rejected because it has a small effect.  
  > "The F770W filter also captures emission from hot, very small dust grains, but this has a small effect (cite: baron2024a) and we do not subtract any underlying dust continuum." (JWST imaging of PAH emission)
- Alternative: Analyzing Cycle 2 F335M data was deferred because the F300M-based stellar continuum subtraction for Cycle 2 is not yet science-ready.  
  > "Both the JWST Cycle 1 and Cycle 2 data include the F335M filter but the continuum subtraction needed to isolate the PAH emission has only reached a science-ready state for the Cycle 1 data (§3.1)." (Data and Methods)
- Alternative: NGC 3344, NGC 5530, and NGC 1068 were excluded from the Cycle 2 sample due to lack of CO(2-1) data, unexecuted observations, and uncertain JWST background levels, respectively.  
  > "From the 54 available Cycle 2 galaxies, we remove NGC 3344 due to the lack of CO (2-1) observations, NGC 5530 because the observations are still to be executed, and NGC 1068 because the background level in the JWST images remain too uncertain for the current analysis." (JWST imaging of PAH emission)
- How they decided it was enough: _not stated_
- Limitation (authors): Results only apply to bright, molecular gas-dominated regions (I_F770W^PAH >= 0.5 MJy sr^-1, Sigma_mol >= 4 M_sun pc^-2) and exclude 49% of the map area outside galaxy centers and nebulae where H I dominates.  
  > "However, we do exclude a majority ($49\%$) of the area in the maps outside galaxy centers and nebulae. Analysis of this faint, extended diffuse emission requires the inclusion of H I and will be the topic of future work." (Analysis approach); "Our results formally apply to regions where molecular gas is likely to constitute a significant fraction of the ISM, with $\Sigma_{\rm mol} \gtrsim 4$ M$_\odot$ pc$^{-2}$." (Discussion)
- Limitation (authors): Sightline-to-sightline scatter in CO at low PAH intensity is large (~0.5 dex) and dominated by statistical noise (~1 K km s^-1) in the flat PHANGS-ALMA CO maps.  
  > "At lower $I^\mathrm{PAH}_{\rm F770W}$, which corresponds to most of the area, the scatter in CO at fixed $I^\mathrm{PAH}_{\rm F770W}$ appears somewhat higher, $\pm 0.5$ dex. Much of this reflects the statistical noise in the PHANGS–ALMA CO maps, which often approaches $\approx \pm 1$ K km s$^{-1}$ in the “flat” CO maps that we use." (Results)
- Limitation (authors): Nebular region masks have coarse physical resolution (median 70 pc) compared to true H II region sizes, blending emission from inside H II regions with surrounding shielded molecular gas.  
  > "The similarity of the CO-vs-PAH relationship in diffuse and nebular regions likely results from the fact that the H II region masks that we use (cite: groves2023) are based on data with coarse resolution (median $70$ pc) compared to the actual size of most H II regions (cite: barnes2022)." (Nebular and diffuse regions)
- Limitation (authors): Hot dust continuum is not subtracted from F770W, which could affect regions where PAHs are destroyed or galaxy centers where hot dust is stronger.  
  > "Subtracting hot dust continuum emission from F770W, which we do not do, may also be important, since the filter still captures such emission in regions where PAHs have been destroyed to the point where their emission is not detectable." (Nebular and diffuse regions); "Finally, we note that we do not subtract any hot dust continuum from F770W. Hot dust continuum is likely stronger in galaxy centers, implying that our reported CO-to-PAH ratio measurements are lower than the true ratios." (Centers and disks of galaxies)
- Limitation (authors): Predicting molecular gas surface density N(H2) from predicted CO(2-1) requires an environment-dependent CO-to-H2 conversion factor, which is not included in the empirical CO-PAH relations.  
  > "The CO(2-1)-to-H$_2$ conversion factor is known to vary as a function of environment across galaxies and this will need to be included to predict the gas column density, $N({\rm H}_2)$ (cite: bolatto2013; schinnerer2024)." (Discussion)
- Caveat (inferred, ours): Cycle 2 JWST reductions and F335M continuum subtraction rely on several in-preparation papers (Koziol et al., Pathak et al., Weinbeck et al.), making exact replication of the Cycle 2 background anchoring and F335M continuum subtraction dependent on unpublished details.
- Caveat (inferred, ours): Spatial pixels of size FWHM/3 oversample the beam (9 pixels per independent beam area), which affects formal statistical uncertainties if pixels are treated as independent prior to binning.

## Reproducibility

- Data public (paper): JWST data obtained from MAST (programs 2107 and 3707); ALMA data processed as part of PHANGS-ALMA survey  
  > "The data were obtained from the Mikulski Archive for Space Telescopes at the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5-03127 for JWST. These observations are associated with programs 2107 and 3707." (Acknowledgments); "This paper makes use of the following ALMA data, which have been processed as part of the PHANGS–ALMA survey:" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Exact F335M continuum subtraction coefficients/recipe from Koziol et al. (in preparation)
- Missing: Exact background anchoring procedures for Cycle 2 JWST images from Koziol et al. (in preparation) and Pathak et al. (in preparation)
- Missing: Exact per-galaxy velocity window widths and reference velocity fields used to generate the flat CO(2-1) maps
- Missing: Locations and sizes of manual elliptical masks for bright foreground stars and background galaxies
- Missing: Exact number or width of logarithmic bins used before linmix regression
- Data volume (inferred): Tens of GB for processed 2D CO(2-1) moment maps and JWST mosaics across 70 galaxies (several TB if starting from raw ALMA visibilities and uncalibrated JWST exposures)
- Score (inferred): 75/5, The statistical analysis, pixel gridding, thresholds, and fitting methods (linmix, webbpsf, pjpipe) are clearly described and high-level PHANGS-ALMA and PHANGS-JWST products are publicly archived, but several preprocessing details (flat CO map velocity windows, F335M continuum subtraction coefficients from in-prep work, star masks, and exact bin widths) are not explicitly stated in the paper.
- Rediscovery candidate: yes, The main findings are clean numerical power-law scaling relations and correlation coefficients across 70 galaxies using public PHANGS-ALMA and PHANGS-JWST treasury datasets, making it well-suited for reproducing the CO-PAH scaling relations from processed maps.

## Links

- Method: (cite: leroy2021) (PHANGS-ALMA survey description, CO(2-1) data processing, strict masks, and target properties)
- Method: (cite: neumann2023) (Method for producing flat integrated CO(2-1) intensity maps)
- Method: (cite: schruba2011) (Spectral stacking / velocity window integration concept)
- Method: (cite: williams2024) (PHANGS-JWST pipeline (pjpipe) data reduction and PSF convolution methodology)
- Method: (cite: sutter2024) (F770W stellar continuum subtraction method)
- Method: (cite: sandstrom2023) (F335M stellar continuum subtraction methodology)
- Method: (cite: aniano2011) (PSF convolution kernels and resolution matching methodology)
- Method: (cite: kelly2007) (Hierarchical Bayesian linear regression method (linmix))
- Companion: (cite: lee2023) (PHANGS-JWST Cycle 1 Treasury overview paper)
- Companion: (cite: pathak2024) (Companion PHANGS-JWST analysis of MIR intensity distributions and environment masks in 19 Cycle 1 galaxies)
- Companion: (cite: leroy2023a) (Initial 4-galaxy PHANGS-JWST and ALMA CO(2-1) comparison paper)
- Companion: (cite: querejeta2021) (PHANGS morphological environment masks defining galaxy centers)
- Companion: (cite: groves2023) (PHANGS-MUSE nebular/H II region masks)
- Companion: (cite: santoro2022) (PHANGS-MUSE H II region catalog methodology)
- Related: PHANGS
- Related: PHANGS-ALMA
- Related: PHANGS-JWST
- Related: PHANGS-MUSE

## Checks

```json
{
 "quotes": 141,
 "quotes_ok": 141,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 23,
 "unsupported_facts": 0,
 "project_codes": 16,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2017.1.00766.S",
  "2019.1.01235.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 19,
 "numeric_problems": 0,
 "fill": {
  "facts": 100,
  "stated": 64,
  "rate": 0.64
 },
 "evidence_ok": true
}
```

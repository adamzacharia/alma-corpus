# Evidence for disks at an early stage in class 0 protostars?

`2017A&A...606A..35G` | Astronomy and Astrophysics 2017 | first author: Gerin, M. | arXiv: 1709.07702 | DOI: 10.1051/0004-6361/201630187

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Do the class 0 protostars B1b-N and B1b-S host compact, disk-like structures at an early stage, as compared with MHD collapse simulations?  
  > "We present 0.06 – 0.1 $^{\prime\prime}$ resolution images at 350 GHz toward B1b-N and B1b-S" (abstract)
- Target **B1b-N**: coordinates 03:33:21.209 +31:07:43.66 (J2000)  
  > "| B1b-N | 03:33:21.209 | 31:07:43.66 |" (Table 1); "a moderately active star-forming region in the Perseus molecular cloud at a distance of 230 pc (cite: hirota)" (1 Introduction); z/distance 230 pc (Perseus)  
  > "| B1b-N | 03:33:21.209 | 31:07:43.66 |" (Table 1); "a moderately active star-forming region in the Perseus molecular cloud at a distance of 230 pc (cite: hirota)" (1 Introduction); distance from Hirota et al. 2008  
  > "| B1b-N | 03:33:21.209 | 31:07:43.66 |" (Table 1); "a moderately active star-forming region in the Perseus molecular cloud at a distance of 230 pc (cite: hirota)" (1 Introduction)
- Target **B1b-S**: coordinates 03:33:21.355 +31:07:26.37 (J2000)  
  > "| B1b-S | 03:33:21.355 | 31:07:26.37 |" (Table 1); z/distance 230 pc (Perseus)  
  > "| B1b-S | 03:33:21.355 | 31:07:26.37 |" (Table 1); distance from Hirota et al. 2008  
  > "| B1b-S | 03:33:21.355 | 31:07:26.37 |" (Table 1)

## Data provenance

- ALMA projects: 2015.1.00025.S
- bands: Band 7 (350 GHz)  
  > "received the digitized signals from the Band 7 receiver" (2 ALMA observations)
- frequencies and spectral setup: Four continuum basebands, 2 GHz wide, 128 channels; 336.5 and 338.4 GHz (LSB), 348.5 and 350.5 GHz (USB)  
  > "Central sky frequencies in each band are 336.5 and 338.4 GHz in the lower sideband (LSB), and 348.5 and 350.5 GHz in the upper sideband (USB)." (2 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C36-7 (46 antennas, long baseline campaign) plus C40-4 (38 antennas, DDT)  
  > "a total of 46 antennas were used in the C36-7 configuration, with baselines from 82 m up to 15 km" (2 ALMA observations); "a total of 38 antennas were used in the C40-4 configuration with baselines from 15 m to 704 m" (2 ALMA observations)
- baselines: _not stated_
- angular resolution: ~0.06 arcsec (~13 au)  
  > "providing an angular resolution of $\sim0.06''$, corresponding to $\sim 13$ au at the distance of Perseus, 230 pc" (2 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 30 minutes combined  
  > "providing 30 minutes on source combined" (2 ALMA observations)
- observing dates: 2015 Nov 22 (long baseline); 2016 Jun 16 (DDT)  
  > "performed on 2015 November 22 during the Long Baseline Campaign, combined with supplementary Director’s Discretionay Time (DDT) observations obtained on 2016 June 16" (2 ALMA observations)
- pi or archival as stated: _not stated_
- Other facility **VLA (VANDAM survey)**: 32.9 GHz continuum images at 0.2 arcsec  
  > "we show as gray contours the 32.9 GHz emission mapped with a 0.2$^{\prime\prime}$ beam with the Very Large Array (VLA)" (3.1 Resolving the continuum emission)
- External data: VLA 32.9 GHz VANDAM images  
  > "J. Tobin for access to the VANDAM images" (Acknowledgements) [from (cite: tobin:15a; tobin:16)]
- External data: Dust opacity kappa = 0.01 (nu/230 GHz)^1.8 cm2/g  
  > "$\kappa = 0.01(\frac{\nu}{230~\mathrm{GHz}})^{1.8}$  cm$^2$g$^{-1}$, a value commonly used for cold and dense cores, from (cite: oh94)" (3.2 Analysis) [from (cite: oh94)]
- External data: Emissivity 0.006 cm2/g at 1 cm for large grains up to 3 mm  
  > "assuming an emissivity of $\kappa = 0.006$  cm$^2$g$^{-1}$ at 1 cm, adapted to a population of large grains with sizes reaching 3 mm (cite: tazzari:16)" (3.2 Analysis) [from (cite: tazzari:16)]
- External data: Gas kinetic temperature T0 = 12 K  
  > "the kinetic temperature $T_0$ is 12 K (cite: lis:10)" (3.2 Analysis) [from (cite: lis:10)]
- Simulation/model as data: 3D RAMSES MHD collapse simulation of a 1 Msun turbulent magnetized core (mu=2, Mach 1.2) from Hennebelle et al. 2016, post-processed with RADMC-3D  
  > "The model consists of a collapsing 1M$_\odot$ magnetized and turbulent dense core of radius $R_0=2500$ au." (4.1 Description of the model)

## Processing

### Calibration

- pipeline or manual: Standard calibration in CASA 4.5.0  
  > "Standard calibration was performed in CASA 4.5.0" (2 ALMA observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0238+1636 (1.06 Jy at 343.5 GHz) for first dataset; J0237+2848 (1.10 Jy) for DDT  
  > "The adopted flux density of J0238+1636 is 1.06 Jy at 343.5 GHz." (2 ALMA observations); "J0237+2848 (flux 1.10 Jy at 343.5 GHz) was used instead" (2 ALMA observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: Imaging with GILDAS and CASA 4.7.0  
  > "for imaging and data analysis we used the GILDAS software and CASA 4.7.0" (2 ALMA observations)
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
- final beam: 0.064x0.048 arcsec (high-res); 0.39x0.27 arcsec (DDT); combined 0.086x0.069 (B1b-N), 0.14x0.11 (B1b-S)  
  > "The final clean beams are $0.086'' \times 0.069''$ for B1b-N, and $0.14'' \times 0.11''$ for B1b-S." (2 ALMA observations)
- final rms: 0.1 mJy/beam per spw (high-res); 0.2 mJy/beam (DDT)  
  > "with a noise level of 0.1 mJy/beam for each spectral window" (2 ALMA observations)

### Inherited from earlier work

- Inversion of radial profile method and attenuated power-law profile  
  > "We used a simple attenuated power-law profile for the radial distribution of the flux density (cite: krco:16)" (Appendix B) [from (cite: krco:16)]
- Collapse model nearly identical to earlier model, with turbulence instead of rotation  
  > "The model is almost identical to the model used in (cite: masson:15), except that we account for initial turbulent velocity fluctuations" (4.1 Description of the model) [from (cite: masson:15), (cite: hennebelle:16)]
- Gas-dust temperature coupling and 1% dust-to-gas ratio in radiative transfer  
  > "Following (cite: commercon:12a; commercon:12b), we assumed that the gas and dust temperature are perfectly coupled and that the dust-to-gas ratio is uniform and equal to 1%." (4.2 Synthetic observations) [from (cite: commercon:12a; commercon:12b)]

### Not stated but needed to reproduce (our reading)

- Weighting scheme/robust, cell size, image size, deconvolver and masking in GILDAS/CASA imaging
- How the two datasets were combined (relative weights, flux scaling between them)
- Phase calibrator names (blank in text)
- Self-calibration usage on targets
- Ellipse-fit and radial profile binning details
- Radiative transfer settings (photon number, grid) for RADMC-3D
- Exact method for combining 32 GHz and 350 GHz mass estimates

## Analysis recipe

1. **Image and measure continuum**: Concatenate the two datasets, average spectral windows per sideband, image; measure peak and 1 arcsec aperture flux  
  > "For the data reported here, we have concatenated the two datasets." (2 ALMA observations)
   - software: CASA, GILDAS
   - fitting: _not stated_
   - validation: Phase transfer tested on calibrator; flux versus uv distance curves overlap  
  > "The good overlap of the curves of flux versus UV distance in the domain from 20 m up to 600 m shows that the flux calibration is very good." (Appendix A)
2. **Fit source size and shape**: Fit isocontours with ellipses (free PA and ellipticity) and Gaussians  
  > "we fit the flux density isocontours with ellipses centered on the protostar positions, with the position angle ($PA$) and ellipticity as free parameters" (3.1 Resolving the continuum emission)
   - fitting: _not stated_
   - validation: Compared with VLA 32 GHz sizes  
  > "The sizes of the compact component for both sources correspond to the size of the centimeter continuum emission" (3.1 Resolving the continuum emission)
3. **Derive radial density, temperature and mass profiles**: Fit circularly averaged intensity with two modified power laws and analytically invert; polytropic temperature law; disk region temperature from brightness temperature; masses from 32 GHz flux  
  > "we used a two-component fit with a central component with a steep flux density profile ($r^{-4}$ or $r^{-6}$) and a more extended envelope with flux decreasing as $r^{-2}$" (3.2 Analysis)
   - parameter: T0 = 12 K below n0 = 1e10 cm-3; polytropic gamma = 1.6 above  
  > "We have chosen $\gamma = 1.6$, adapted for moderately warm molecular gas." (3.2 Analysis)
   - assumption: Spherical symmetry, constant dust optical properties, dust-gas thermal coupling, optically thin envelope  
  > "This assumes spherical symmetry, that the gas is molecular, and that the dust has constant optical properties" (3.2 Analysis)
   - fitting: Two-component attenuated power-law fit; priors not stated  
  > "For both sources, we used a two-component fit with a central component with a steep flux density profile ($r^{-4}$ or $r^{-6}$) and a more extended envelope with flux decreasing as $r^{-2}$." (Analysis of intensity, density, and temperature radial distributions)
   - validation: Compared with an isothermal spherical envelope model, which fails to reproduce cumulative flux  
  > "this model presents a cumulative flux distribution very different from that of B1b-N and B1b-S" (3.2 Analysis)
4. **Compare with MHD collapse simulation**: Post-process the simulation with RADMC-3D at 350 GHz and compare radially averaged flux at two epochs, inclination 20 deg  
  > "We used the views with $i = 20^\circ$ for two different epochs" (4.3 Comparison)
   - software: RADMC-3D, RAMSES
   - assumption: Semenov et al. 2003 opacities; dust-to-gas 1%  
  > "We used the dust opacity from (cite: semenov:03) for the homogeneous spheres model" (4.2 Synthetic observations)
   - fitting: _not stated_
   - validation: Late-stage model agrees with observations within a factor of two  
  > "both the disk radius and the predicted flux density radial distribution agree within better than a factor of two with the observations" (4.3 Comparison)

## Software

- **CASA** 4.5.0 (calibration), 4.7.0 (imaging): Calibration, imaging and analysis  
  > "Standard calibration was performed in CASA 4.5.0, while for imaging and data analysis we used the GILDAS software and CASA 4.7.0." (2 ALMA observations)
- **GILDAS** : Imaging and data analysis  
  > "for imaging and data analysis we used the GILDAS software and CASA 4.7.0" (2 ALMA observations)
- **RADMC-3D** : Radiative transfer post-processing of the simulation  
  > "We post-processed the simulation using the the  radiative transfer code (cite: dullemond:12) to compute the expected 350 GHz emission." (4.2 Synthetic observations)
- **RAMSES** : MHD collapse simulation with ambipolar diffusion (code name inferred from the teyssier:02 citation)  
  > "We have used the  code (cite: teyssier:02), which integrates the MHD equations using a constrained transport scheme" (4.1 Description of the model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| B1b-N peak flux density (both sidebands) | 13.4 | rms 0.71 | mJy/beam | 1 | / B1b-N / 03:33:21.209 / 31:07:43.66 / $0.086\times0.069$ / 1.1 / 13.4 / 0.71 / |
| B1b-S peak flux density | 63.1 | rms 2.4 | mJy/beam | 1 | / B1b-S / 03:33:21.355 / 31:07:26.37 / $0.14\times0.11$ / 16 / 63.1 / 2.4 / |
| Flux in 1 arcsec radius, B1b-N / B1b-S | 0.73 / 0.89 | 0.07 / 0.08 | Jy | 1 | $0.73\pm 0.07$ |
| Spectral index 32-350 GHz, B1b-N / B1b-S | 2.4 / 2.8 | 0.1 | dimensionless | 1 | low spectral index $S_{32}^{350}(0.3'')$ between 32 and 350 GHz of 2.4 and 2.8 for B1b-N and B1b-S |
| Central dust temperature, B1b-S / B1b-N | 56 / 41 | not stated | K | 3 | / $T_c$$^d$ (K)                         / 56                                 / 41                               / |
| Mass within 0.3 arcsec, B1b-S / B1b-N | 0.093 / 0.11 | not stated | Msun | 3 | / $M(r<0.3'')$ (M$_\ensuremath{\odot}$) / 0.093                              / 0.11                             / |
| Compact component FWHM | ~0.4 (~90 au) | not stated | arcsec | 2 | We obtain a FWHM of about 0.4 $^{\prime\prime}$, corresponding to $\sim 90$ au |

## Qualitative findings

- The 350 GHz compact component is likely optically thick (~35 K brightness temperature); flat spectral index suggests opacity plus large grains.  
  > "It is therefore likely that the continuum emission of the compact component is optically thick." (3.1 Resolving the continuum emission)

## Claim tuples

- H: The compact structures in B1b-N and B1b-S are disks rather than inner envelopes | E: Compare radial profiles with a spherical envelope model and an MHD collapse simulation | R: Spherical envelope fails; late-stage disk model agrees within a factor of two | F: The sources are consistent with early-forming rotationally supported disks, tentatively since kinematics are lacking | **partially**
- H: B1b-N is younger than B1b-S | E: Compare compact-to-envelope flux ratios | R: B1b-N compact component is smaller and has a lower flux fraction | F: Consistent with earlier evolutionary status of B1b-N | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Simple isothermal spherical envelope rejected as explanation of compact component  
  > "supporting the association of the compact component detected with ALMA with a disk" (3.2 Analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): No kinematic data; missing short spacings, so envelope parameters poorly constrained; grain emissivity uncertain  
  > "Because of the lack of short spacings, some flux may be missing at scales larger than $\sim 2$ $''$." (3.2 Analysis)
- Caveat (inferred, ours): Disk identification relies on morphology and a single simulation, not kinematics
- Caveat (inferred, ours): Mass depends strongly on assumed large-grain emissivity at 32 GHz
- Caveat (inferred, ours): Optically thick assumption makes temperature degenerate with filling factor

## Reproducibility

- Data public (paper): ALMA project code cited in acknowledgements  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00025.S" (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Dataset combination details
- Missing: Simulation outputs from Hennebelle et al. 2016
- Data volume (inferred): Tens of GB (two Band 7 continuum datasets)
- Score (inferred): 3/5, Data identified and analysis described, but imaging parameters and simulation inputs are missing.
- Rediscovery candidate: no, Imaging recipe incomplete and the comparison relies on an external simulation.

## Links

- Method: (cite: krco:16) (Radial profile inversion method)
- Companion: (cite: gerin:15) (NOEMA outflow study of B1b-N and B1b-S)
- Companion: (cite: tobin:16) (VANDAM VLA data)
- Related: VANDAM

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2015.A.00012.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 47,
  "rate": 0.61
 },
 "evidence_ok": true
}
```

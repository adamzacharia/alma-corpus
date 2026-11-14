# Detection of Dimethyl Ether in the Central Region of the MWC 480 Protoplanetary Disk

`2024ApJ...974...83Y` | The Astrophysical Journal 2024 | first author: Yamato, Yoshihide | arXiv: 2407.21518 | DOI: 10.3847/1538-4357/ad6981

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Are sublimated complex organic molecules (CH3OCH3, CH3OCHO, CH3OH) present in the inner warm region of the full (non-transitional) MWC 480 Herbig Ae disk, and what are their excitation conditions and abundance ratios?  
  > "In this paper, we present the first detection of CH$_3$OCH$_3$ in the MWC 480 protoplanetary disk." (Introduction)
- Target **MWC 480**: coordinates ICRS 04h58m46.279s, +29d50m36.40s (continuum peak, used as disk center)  
  > "in the Taurus-Auriga star-forming region ($d\approx162$ pc; (cite: GaiaColaboration2018))" (Introduction); "$\alpha(\mathrm{ICRS}) = 04^{\mathrm{h}}58^{\mathrm{m}}46.279s, \delta(\mathrm{ICRS}) = +29^{\mathrm{d}}50^{\mathrm{m}}36.40s$" (Observations); z/distance d ≈ 162 pc  
  > "in the Taurus-Auriga star-forming region ($d\approx162$ pc; (cite: GaiaColaboration2018))" (Introduction); "$\alpha(\mathrm{ICRS}) = 04^{\mathrm{h}}58^{\mathrm{m}}46.279s, \delta(\mathrm{ICRS}) = +29^{\mathrm{d}}50^{\mathrm{m}}36.40s$" (Observations); distance from Gaia Collaboration 2018  
  > "in the Taurus-Auriga star-forming region ($d\approx162$ pc; (cite: GaiaColaboration2018))" (Introduction); "$\alpha(\mathrm{ICRS}) = 04^{\mathrm{h}}58^{\mathrm{m}}46.279s, \delta(\mathrm{ICRS}) = +29^{\mathrm{d}}50^{\mathrm{m}}36.40s$" (Observations)

## Data provenance

- ALMA projects: 2021.1.00535.S, 2021.1.00982.S
- bands: Band 7  
  > "We observed the MWC 480 disk in Band 7 during ALMA Cycle 8" (Observations)
- frequencies and spectral setup: Continuum SPW 298.88–300.75 GHz (1.1 MHz, ≈1.1 km/s) for 00535; 288.56–290.43 GHz (1.1 MHz, ≈1.2 km/s) for 00982  
  > "which covered a frequency range of 298.88–300.75 GHz and had a spectral resolution of 1.1 MHz (${\approx}1.1$ km s$^{-1}$)" (Observations); "covered a frequency range of 288.56–290.43 GHz with a spectral resolution of 1.1 MHz" (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15–1302 m  
  > "| 2022 Aug. 10 | 42         | 44             | 0.4       | 15–1302   | 0.2                 | 2.8                 | J0510+1800         | J0438+3004 |" (Table 1)
- angular resolution: ~0.2 arcsec (Table); cube beam 0.31x0.21 arcsec  
  > "The CLEANed image cube has a synthesized beam of $0.31\ensuremath{''}\times0.21\ensuremath{''}$ (PA $=8.2\ensuremath{^\circ}$)" (Observations)
- max recoverable scale: 2.6–3.1 arcsec  
  > "| 2022 Aug. 9  | 40         | 44             | 0.2       | 15–1246   | 0.2                 | 3.0                 | J0510+1800         | J0438+3004 |" (Table 1)
- sensitivity: RMS 0.33 mJy/beam (00535) and 0.67 mJy/beam (00982) at 4 km/s channels  
  > "a root mean square (RMS) noise level of 0.33 mJy beam$^{-1}$ at 4 km s$^{-1}$ channel width" (Observations); "0.67 mJy beam$^{-1}$ at 4 km s$^{-1}$ channel width" (Observations)
- time on source: 44 min per EB (00535, 5 EBs); 40 min per EB (00982, 3 EBs)  
  > "| 2022 Aug. 11 | 45         | 40             | 0.5       | 15–1302   | 0.2                 | 2.9                 | J0510+1800         | J0438+3004 |" (Table 1)
- observing dates: 2022 Aug 8–10 (00535, five EBs); 2022 Aug 11–14 (00982, three EBs)  
  > "| 2022 Aug. 8  | 42         | 44             | 0.7       | 15–1302   | 0.2                 | 2.6                 | J0510+1800         | J0438+3004 |" (Table 1)
- pi or archival as stated: 00535: PI Y. Yamato; 00982: PI V. V. Guzman  
  > "(project code: 2021.1.00982.S; PI: V. V. Guzman)" (Observations)
- Line: CH3OCH3 5(4,x)-4(3,x) cluster (12 blended transitions) (~299.89 GHz)
- Line: CH3OCHO / CH3OCH3 tentative features (~299.12 GHz and ~300.06 GHz)
- Line: CH3OH 6(k)-5(k) cluster (undetected) (~290.0–290.4 GHz)
- External data: Disk density/temperature structure model tailored to MWC 480  
  > "we used the disk model tailored to MWC 480 in (cite: Zhang2021)" (Parametric Disk Model) [from Zhang et al. 2021 (cite: Zhang2021)]
- External data: Spectroscopic data and partition functions from CDMS and JPL  
  > "are taken from the Cologne Database for Molecular Spectroscopy (cite: CDMS1; CDMS2; CDMS3) for CH$_3$OCH$_3$ and CH$_3$OH" (Details of Spectral Analysis) [from CDMS (cite: CDMS1; CDMS2; CDMS3); JPL (cite: JPL)]
- External data: Systemic velocity ≈5.1 km/s and stellar mass 2.1 Msun  
  > "systemic velocity (5.1 km,s$^{-1}$; (cite: Pietu2007; Teague2021_MAPS))" (3.1 Spectra and Spatial Distributions) [from Pietu2007; Teague2021_MAPS]
- External data: Abundance ratios of other disks (HD 100546, IRS 48) for comparison  
  > "compares the abundance ratios of CH$_3$OCH$_3$ and CH$_3$OCHO relative to CH$_3$OH among HD 100546 (cite: Booth2024_HD100546), Oph IRS 48 (cite: Booth2024_IRS48), and MWC 480" (4.2 COM-rich Transition Disks) [from Booth2024_HD100546; Booth2024_IRS48]
- External data: Binding energies of CH3OCH3 and CH3OH  
  > "binding energies of CH$_3$OCH$_3$(${\approx}4000$ K; (cite: Lattelais2011)) and CH$_3$OH(${\approx}5000$–5500 K; (cite: Ferrero2020; Minissale2022))" (Parametric Disk Model) [from Lattelais2011; Ferrero2020; Minissale2022]
- Simulation/model as data: Parametric RADMC-3D disk model with COM abundance within temperature boundaries, based on the Zhang2021 MWC 480 structure  
  > "here we simply assumed that the gas temperature is the same as the dust temperature (surface-area-weighted over both populations) computed with thermal Monte Carlo simulations using the RADMC-3D package" (Parametric Disk Model)

## Processing

### Calibration

- pipeline or manual: Standard ALMA pipeline by ALMA staff, then self-calibration in CASA  
  > "The pipeline calibrations were performed by ALMA staff using the standard ALMA pipeline." (Observations)
- casa version: CASA 6.2.1.7 (00535); 6.4.1 (00982)  
  > "were performed using the Common Astronomy Software Applications (cite: CASA) version 6.2.1.7." (Observations); "but with CASA version 6.4.1" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0510+1800 (bandpass/amplitude); phase J0438+3004  
  > "| 2022 Aug. 10 | 41         | 44             | 0.5       | 15–1302   | 0.2                 | 3.1                 | J0510+1800         | J0438+3004 |" (Table 1)
- flux scale uncertainty: ≲10%, not included in analysis  
  > "the absolute flux calibration uncertainty is expected to be ${\lesssim}10$% based on the Quality Assurance (QA2) criteria" (Observations)
- self calibration: 00535: 5 phase-only + 1 amplitude rounds (S/N x≈15); 00982: 3 phase-only + 1 amplitude (S/N x≈5.5)  
  > "five rounds of phase-only self-calibration and one round of amplitude self-calibration were performed, resulting in a signal-to-noise ratio (S/N) increase by a factor of ${\approx}15$" (Observations); "We performed three rounds of phase-only self-calibration and one round of amplitude self-calibration, which resulted in an increase in S/N by a factor of ${\approx}5.5$." (Observations)

### Imaging

- task: tclean with briggsbwtaper  
  > "modified Briggs weighting scheme of `briggsbwtaper` implemented in the `tclean` task" (Observations)
- deconvolver: _not stated_
- weighting robust: robust = 0.5 for cubes; −0.5 for 1.03 mm continuum  
  > "a Briggs robust value of 0.5 in the modified Briggs weighting scheme" (Observations); "continuum image at 1.03 mm with a Briggs robust value of $-0.5$" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub with first-order polynomial to line-free channels  
  > "fitting a first-order polynomial to line-free channels using the CASA task `uvcontsub`" (Observations)
- line free channels: Selected by visual inspection of cubes (ranges not given)  
  > "averaging the line-free channels specified by visually inspecting the data cubes delivered from the observatory" (Observations)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Channel spacing 4 km/s to boost S/N  
  > "The large channel width of 4 km s$^{-1}$ intended to boost the S/N of detected CH$_3$OCH$_3$ emission" (Observations)
- final beam: 0.31x0.21 arcsec PA 8.2 deg (00535); 0.31x0.22 arcsec PA −3.4 deg (00982)  
  > "The resulting beam size and the RMS noise level were $0.31\ensuremath{''}\times0.22\ensuremath{''}$ (P.A. $= -3.4\ensuremath{^\circ}$)" (Observations)
- final rms: 0.33 mJy/beam (00535); 0.67 mJy/beam (00982) at 4 km/s, before primary beam correction  
  > "The RMS noise was measured on the line-free region of the image cube prior to primary beam correction." (Observations)

### Inherited from earlier work

- LTE slab model spectral fitting method  
  > "We basically followed the method described in (cite: Yamato2024), which is detailed in Appendix [7](#appendix:LTE_model)." (3.2 Spectral Analysis) [from Yamato2024]
- Matched filter analysis technique  
  > "We performed the matched filter analysis (cite: Loomis2018_MF), which is commonly used to extract weak molecular line emission in protoplanetary disks" (Matched Filter Analysis) [from Loomis2018_MF]
- Disk density and temperature structure  
  > "The details of the model are referred to the original paper." (Parametric Disk Model) [from Zhang2021]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges used for continuum and uvcontsub
- Self-calibration solution intervals and reference antenna/spw choices
- Image size, cell size, cleaning threshold and masks
- Aperture-extraction details for spectrum conversion to beam-averaged units (primary beam correction)
- Exact MCMC convergence diagnostics and initialization
- Matched filter inclination-based kernel details beyond listed parameters
- Full Zhang2021 disk model parameters

## Analysis recipe

1. **Calibrate and self-calibrate, make cubes**: Pipeline calibration, align continuum peaks, phase and amplitude self-cal, uvcontsub, tclean cube at 4 km/s  
  > "The continuum emission was finally subtracted from the line visibilities by fitting a first-order polynomial to line-free channels using the CASA task `uvcontsub`." (Observations)
   - software: CASA
   - parameter: robust 0.5, briggsbwtaper, 4 km/s channels  
  > "channel spacing of 4 km s$^{-1}$ and a Briggs robust value of 0.5" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract spectra and moment maps**: Spatially integrate cube in 0.6 arcsec diameter circular aperture at disk center; moment maps with bettermoments without flux threshold  
  > "extracted the integrated spectra by spatially integrating the image cubes in a circular aperture with 0.6$''$ diameter toward the disk center" (3.1 Spectra and Spatial Distributions)
   - software: bettermoments, CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Verify detections with matched filter**: Cross-correlate visibilities with Keplerian kernel (i=37 deg, PA=148 deg, M=2.1 Msun, outer radius 0.15 arcsec)  
  > "assuming a disk inclination angle of $37.0\ensuremath{^\circ}$, position angle of $148.0\ensuremath{^\circ}$ and central stellar mass of $2.1\,M_\odot$" (Matched Filter Analysis)
   - software: VISIBLE, keplerian_mask
   - fitting: _not stated_
   - validation: Cross-check of detections: ~17 sigma for the 299.89 GHz cluster, no ≥5 sigma for CH3OH/CH3CHO  
  > "The response spectra do not exhibit any ${\ge}5\sigma$ responses of CH$_3$OH and CH$_3$CHO transitions." (Matched Filter Analysis)
4. **Fit LTE slab model for Tex, line width, column densities**: Simultaneous 7-parameter LTE fit of four species with common Tex to all >600 transitions  
  > "the entire spectra are modeled with a total of seven free parameters" (3.2 Spectral Analysis)
   - software: emcee, specfit
   - parameter: 50 walkers, 10000 steps, 2000 burn-in  
  > "We run 50 walkers for 10000 steps to sample the posterior distributions and the initial 2000 steps are discarded as burn-in." (Details of Spectral Analysis)
   - assumption: Common Tex for all species, optically thin, Gaussian line shape, Tcmb=2.73 K  
  > "The assumption of a common excitation temperature for all COM species reflects the expectation that different COMs sublimate simultaneously with water ice." (3.2 Spectral Analysis)
   - fitting: emcee affine-invariant MCMC; uniform priors Tex U(5,1000) K, dV U(0,100) km/s, vsys U(-5,15) km/s, log10 N U(10,20); upper limits at 99.85th percentile  
  > "using uniform prior distributions" (Details of Spectral Analysis)
   - validation: Best-fit model compared with observed spectra  
  > "The three observed spectral features are well reproduced by the best-fit model." (3.2 Spectral Analysis)
5. **Radiative transfer test of spatial distribution**: RADMC-3D image cubes from Zhang2021 disk structure with COMs set above sublimation temperatures (80/100 K for CH3OCH3; 100/120/140 K for CH3OH), z/r<0.3, Keplerian rotation; abundances adjusted to fit  
  > "The abundance $x$(CH$_3$OCH$_3$) and $x$(CH$_3$OH) are adjusted to fit the observed spectra." (Parametric Disk Model)
   - software: RADMC-3D
   - assumption: Gas temperature = dust temperature; constant abundance in regions above sublimation temperature  
  > "we simply assumed that the gas temperature is the same as the dust temperature" (Parametric Disk Model)
   - fitting: abundance adjusted to match spectra (method not specified)  
  > "The abundance $x$(CH$_3$OCH$_3$) and $x$(CH$_3$OH) are adjusted to fit the observed spectra." (Parametric Disk Model)
   - validation: Comparison to observed CH3OCH3 spectrum  
  > "Both models with boundary temperatures of 80 and 100 K reproduce the spectrum well, particularly the broad line width." (Parametric Disk Model)

## Software

- **CASA** 6.2.1.7 / 6.4.1: Self-calibration, imaging, uvcontsub, imfit  
  > "Subsequent self-calibration and imaging were performed using the Common Astronomy Software Applications (cite: CASA) version 6.2.1.7." (Observations)
- **bettermoments** : Velocity-integrated intensity maps  
  > "generated using the Python package `bettermoments` (cite: bettermoments) with no flux threshold for pixel inclusion" (3.1 Spectra and Spatial Distributions)
- **emcee** : MCMC sampling of LTE model  
  > "implemented in the Python package `emcee` (cite: emcee)" (3.2 Spectral Analysis)
- **VISIBLE** : Matched filter cross-correlation  
  > "The Python package `VISIBLE` (cite: Loomis2018_MF) was used to compute the cross-correlation" (Matched Filter Analysis)
- **keplerian_mask** 1.0: Keplerian filter kernel  
  > "generated with the Python script `keplerian_mask` (cite: Teague2020_kepmask)" (Matched Filter Analysis)
- **RADMC-3D** : Dust temperature and image cubes of parametric disk model  
  > "we compute the image cubes covering the frequency ranges of the robustly detected CH$_3$OCH$_3$ transitions at $\sim$ 299.89 GHz and the undetected CH$_3$OH transitions at 290.0–290.4 GHz using the RADMC-3D package" (Parametric Disk Model)
- **specfit** : Public code for column density retrieval  
  > "packaged into a public Python code `specfit` (<https://github.com/yyamato-as/specfit>)" (Footnote 2)
- **corner.py** : Corner plots of posteriors  
  > "`corner.py` (cite: corner)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Excitation temperature | 200 | +50/-50 | K | 4 | $T_\mathrm{ex} = 200_{-50}^{+50}$ K |
| Line width FWHM | 30 | +8/-6 | km/s | 4 | $\Delta V = 30_{-6}^{+8}$ km s$^{-1}$ |
| N(CH3OCH3) | 7.4e15 | +4.6/-3.2 e15 | cm^-2 | 4 | $7.4_{-3.2}^{+4.6} \times 10^{15}$ |
| N(CH3OCHO) | 7.4e14 | +3.6/-4.9 e14 | cm^-2 | 4 | $7.4_{-4.9}^{+3.6} \times 10^{14}$ |
| N(CH3OH) upper limit | <9.1e14 | 3 sigma | cm^-2 | 4 | $<9.1\,\times\,10^{14}$ and $<1.9\,\times\,10^{14}$ cm$^{-2}$ |
| N(CH3CHO) upper limit | <1.9e14 | 3 sigma | cm^-2 | 4 | $<9.1\,\times\,10^{14}$ and $<1.9\,\times\,10^{14}$ cm$^{-2}$ |
| N(CH3OCH3)/N(CH3OH) lower limit | >7 | 3 sigma | dimensionless | 4 | we derived a CH$_3$OCH$_3$/CH$_3$OH column density ratio (lower limit) of ${>}7$ |
| Systemic velocity fit | 4.3 | +2.4/-2.5 | km/s | 4 | $4.3^{+2.4}_{-2.5}$ |
| Peak S/N of 299.89 GHz CH3OCH3 feature | 9.4 | not stated | dimensionless | 2 | shows a peak S/N of 9.4 |
| Matched filter response of 299.89 GHz cluster | ~17 | not stated | sigma | 3 | shows a ${\sim}17\sigma$ filter response |
| Disk-model abundance ratio x(CH3OCH3)/x(CH3OH) lower limits | ~0.3–2 | not stated | dimensionless | 5 | The constrained lower limits of the abundance ratios span ${\sim}0.3$–2 |

## Qualitative findings

- CH3OCH3 emission is spatially unresolved and compact (≲25 au), consistent with sublimation in the warm inner disk  
  > "The spatially unresolved, compact (${\lesssim}25$ au in radius) nature, the broad line width (${\sim}30$ km s$^{-1}$), and the high excitation temperature (${\sim}200$ K) indicate sublimation of COMs in the warm inner disk." (abstract)
- A new submillimeter source detected ~5.2 arcsec from the star, origin unclear  
  > "We report the detection of a new submillimeter source at a separation of ${\approx}5.2\ensuremath{''}$ from the central star" (Detection of a new submillimeter source)

## Claim tuples

- H: Sublimated COMs are detectable in a full (non-transitional) Class II disk | E: Band 7 ALMA spectra at the MWC 480 disk center, matched filter and LTE fit | R: CH3OCH3 detected (peak S/N 9.4; ~17 sigma matched filter); CH3OCHO tentative | F: First detection of CH3OCH3 in a non-transitional Class II disk, from inner-disk ice sublimation | **supported**
- H: CH3OH should accompany CH3OCH3 if COMs are sublimated inherited ice | E: Simultaneous LTE fit including CH3OH covered in 2021.1.00982.S | R: CH3OH undetected; N ratio CH3OCH3/CH3OH >7 | F: High ratio suggests disk-phase reprocessing and/or distribution differences | **partially**
- H: Differing sublimation radii of CH3OH and CH3OCH3 could explain the CH3OH non-detection | E: RADMC-3D parametric disk models | R: Abundance ratio lower limits ~0.3–2, factor 3–20 below column ratio | F: Spatial distribution is critical for the true abundance ratio | **partially**
- H: COM ratios differ between full and transition disks | E: Compare ratios with HD 100546 and IRS 48 from literature | R: MWC 480 ratios higher | F: Suggests more reprocessing in inner full disk versus inherited ice at transition-disk cavity edges | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Large 4 km/s channels to boost S/N while resolving the broad line  
  > "The large channel width of 4 km s$^{-1}$ intended to boost the S/N of detected CH$_3$OCH$_3$ emission while resolving its broad line width." (Observations)
- Alternative: Exhaustive search found only CH3OCH3 and CH3OCHO could consistently explain the features  
  > "only CH$_3$OCH$_3$ and CH$_3$OCHO can consistently explain these features among the lines of detectable species/transitions in typical disk environment" (3.1 Spectra and Spatial Distributions)
- How they decided it was enough: _not stated_
- Limitation (authors): No detailed line shape modeling due to unresolved emission, low S/N and low spectral resolution  
  > "given the unresolved emission, the low S/N, and the low spectral resolution, we do not perform a detailed line shape modeling here" (Details of Spectral Analysis)
- Limitation (authors): Inner disk structure is an extrapolation of the outer disk  
  > "the disk physical structure used in this modeling is an extrapolation of the outer disk structure" (Parametric Disk Model)
- Limitation (authors): Flux calibration systematic uncertainty not included  
  > "The following analyses consider only the statistical uncertainty and does not include the systematic flux calibration uncertainty." (Observations)
- Caveat (inferred, ours): Detection rests on a single blended cluster; other features only tentative
- Caveat (inferred, ours): Common Tex and optically thin slab assumptions with unresolved emission; beam dilution/filling factor degeneracy
- Caveat (inferred, ours): CH3OH and CH3OCH3 constrained from different datasets with different noise and calibration
- Caveat (inferred, ours): Dust continuum optical depth could hide CH3OH
- Caveat (inferred, ours): Disk model gas temperature taken equal to dust temperature

## Reproducibility

- Data public (paper): Archive project codes cited; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2021.1.00535.S and ADS/JAO.ALMA#2021.1.00982.S." (Acknowledgements)
- Products in archive: _not stated_
- Code: specfit public at github.com/yyamato-as/specfit  
  > "packaged into a public Python code `specfit` (<https://github.com/yyamato-as/specfit>)" (Footnote 2)
- Missing: Line-free channel selection
- Missing: Self-calibration solints
- Missing: Image/cell size and clean parameters
- Missing: Full MWC 480 disk model from Zhang2021
- Data volume (inferred): ~100–300 GB raw for 8 execution blocks in two projects
- Score (inferred): 7/5, Clear spectral fit recipe with priors, line list and code; some imaging and selfcal details missing, and data proprietary period likely ended.
- Rediscovery candidate: yes, Data from two ALMA Cycle 8 projects, a complete LTE fit recipe with priors and line list, and numeric results (Tex, N, ratio) are given.

## Links

- Method: Yamato et al. 2024 (cite: Yamato2024) (LTE slab spectral fitting method)
- Method: Loomis et al. 2018b (cite: Loomis2018_MF) (Matched filter technique/VISIBLE)
- Companion: Oberg et al. 2021 (cite: Oberg2021) (MAPS Large Program of the MWC 480 disk)
- Companion: Zhang et al. 2021 (cite: Zhang2021) (MWC 480 disk model used)
- Related: MAPS (Molecules with ALMA at Planet-forming Scales)

## Checks

```json
{
 "quotes": 94,
 "quotes_ok": 94,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 65,
  "rate": 0.756
 },
 "evidence_ok": true
}
```

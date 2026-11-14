# GASP. XXII. The Molecular Gas Content of the JW100 Jellyfish Galaxy at z ∼ 0.05: Does Ram Pressure Promote Molecular Gas Formation?

`2020ApJ...889....9M` | The Astrophysical Journal 2020 | first author: Moretti, Alessia | arXiv: 1912.06565 | DOI: 10.3847/1538-4357/ab616a

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, galaxy_clusters_and_sz
- Question: How much molecular gas does the jellyfish galaxy JW100 contain, where is it, and does ram pressure promote molecular gas formation in the stripped tail?  
  > "Does Ram Pressure Promote Molecular Gas Formation?" (abstract); "In order to understand where the cold molecular gas is located and what is the origin of this gas, we have therefore collected ALMA interferometric data at $\sim$1 kpc resolution" (Introduction)
- Target **JW100 (jellyfish galaxy in cluster A2626)**: coordinates region D1 at 23:36:24.927 +21:09:05.958; AGN at 23:36:25.0,+21:09:02.5  
  > "which yields 1$^{\prime\prime}$=1.071 kpc at the cluster redshift (z=0.055). The galaxy redshift is, instead, z=0.06189." (Introduction); "JW100 D1 | 23:36:24.927 | +21:09:05.958" (Table 2); z/distance z=0.06189 (galaxy); cluster z=0.055  
  > "which yields 1$^{\prime\prime}$=1.071 kpc at the cluster redshift (z=0.055). The galaxy redshift is, instead, z=0.06189." (Introduction); "JW100 D1 | 23:36:24.927 | +21:09:05.958" (Table 2); distance from standard cosmology H0=70, OmegaM=0.3, OmegaL=0.7  
  > "which yields 1$^{\prime\prime}$=1.071 kpc at the cluster redshift (z=0.055). The galaxy redshift is, instead, z=0.06189." (Introduction); "JW100 D1 | 23:36:24.927 | +21:09:05.958" (Table 2)

## Data provenance

- ALMA projects: 2017.1.00496.S
- bands: Band 3 (CO(1-0)) and Band 6 (CO(2-1))  
  > "using Band 3 and Band 6 to observe the CO(1-0) and (2-1) transitions, respectively." (2 Observations and data reduction)
- frequencies and spectral setup: One spw on CO at 108.645 GHz (1-0) and 217.294 GHz (2-1), three spws for continuum; 1920 channels, 0.976 MHz resolution (3.1 and 1.5 km/s)  
  > "centering one spectral window (spw) on the redshifted frequency of the CO transition, 108.645 GHz for CO(1-0) and 217.294 GHz for CO(2-1), and setting other three spws to observe the continuum." (2 Observations and data reduction)
- continuum bandwidth: 5.25 GHz  
  > "covering a bandwidth of 5.25 GHz using Briggs weighting with a robust value of 0.5" (2 Observations and data reduction)
- arrays: 12m array (Bands 3 and 6) plus 7m ACA (Band 6)  
  > "Additional observations with the 7m ACA array have been obtained in Band 6 to increase the maximum recoverable scale." (2 Observations and data reduction)
- configurations: compact configuration, 43-45 antennas (12m); ACA 9-11 antennas  
  > "A compact configuration of the array with a number of antennas ranging between 43 and 45 was used in both Bands." (2 Observations and data reduction)
- baselines: _not stated_
- angular resolution: 0.98 arcsec (Band 3), 0.7 arcsec (Band 6) from uv-distance proxy; final beams ~2x1.7 and 1.4x1.12 arcsec  
  > "the actual configurations used provide a resolution and maximum recoverable scale of 0.98 and 13.38 arcsec, respectively, in Band 3, and of 0.7 and 7.5 arcsec, in Band 6." (2 Observations and data reduction)
- max recoverable scale: 13.38 arcsec (Band 3), 7.5 arcsec (Band 6 12m), ~18 arcsec (ACA)  
  > "with a 8.9 m shortest baseline, providing a maximum recoverable scale of $\sim$ 18 arcsec." (2 Observations and data reduction)
- sensitivity: rms 9e-4 Jy/beam CO(1-0); 8e-4 Jy/beam CO(2-1) in 20 km/s channels  
  > "| CO(1-0) | 2              | 1.7            | 8.3   | 9$\cdot 10^{-4}$   | 2.5$\cdot 10^{-2}$  |" (Table 1)
- time on source: Band 3: 40 min (1 session); Band 6 12m: 96 min (2 sessions); ACA ~1 hr per pointing  
  > "Band 6 observations have been taken in 2 sessions, for a total time on source of 96 min, observing each pointing for 4.2 min." (2 Observations and data reduction)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=1-0 (redshifted 108.645 GHz)
- Line: CO J=2-1 (redshifted 217.294 GHz)
- Other facility **VLT/MUSE**: Halpha maps and star formation rates, stellar continuum, kinematics of ionized gas  
  > "star formation rate surface density derived from the H$\alpha$ emission from MUSE data" (abstract)
- Other facility **APEX**: single dish CO(2-1) spectra from earlier paper for flux comparison  
  > "Col. 4 refers to the integrated fluxes of APEX spectra from (cite: gaspX) in the same velocity range of ALMA data." (Table 2)
- External data: APEX CO(2-1) spectra/fluxes in regions A and B  
  > "Col. 4 refers to the integrated fluxes of APEX spectra from (cite: gaspX) in the same velocity range of ALMA data." (Table 2) [from (cite: gaspX)]
- External data: AGN position of JW100  
  > "located at 23:36:25.0,+21:09:02.5 , from (cite: gaspXIX)" (5 Quantifying the H2 mass) [from (cite: gaspXIX)]
- External data: Reference depletion time ~2 Gyr and HERACLES relation at 1 kpc  
  > "the depletion times are generally larger than the typical value of $\sim 2$ Gyr (cite: Bigiel2011)" (6 Resolved Star Formation Efficiency) [from (cite: Bigiel2011)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline, 12m and ACA calibrated independently  
  > "The 12m array and ACA datasets have been independently calibrated using the ALMA pipeline (version Pipeline-CASA51-P2-B)." (2 Observations and data reduction)
- casa version: CASA 5.4.0-7  
  > "The calibrated data have been further analyzed with the CASA software (version 5.4.0-7; (cite: CASA))." (2 Observations and data reduction)
- pipeline version: Pipeline-CASA51-P2-B  
  > "calibrated using the ALMA pipeline (version Pipeline-CASA51-P2-B)" (2 Observations and data reduction)
- archive products used as is: _not stated_
- flux calibrator: J0006-0623 (ACA Band 6); J2253+1608 (12m Bands 3 and 6)  
  > "The flux density scale has been fixed using observations of J0006-0623 (for ACA observations in Band 6), and J2253+1608 for the 12m-array observations both in Band 3 and Band 6." (2 Observations and data reduction)
- flux scale uncertainty: ~10%  
  > "We can estimate an uncertainty in the flux measured to be of the order of 10$\%$, including the calibration and clean errors." (2 Observations and data reduction)
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "The images of line and continuum emissions in Band 3 and Band 6 have been obtained using the CASA task *tclean*." (2 Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: continuum Briggs robust 0.5; line cubes natural  
  > "The weighting used for the line images has been natural, to enhance the sensitivity." (2 Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: automask in tclean, refined interactively  
  > "cleaned in regions of line emission initially identified automatically (using the *automask* parameter in tclean), and further refined interactively" (2 Observations and data reduction)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub, linear fit in visibility plane  
  > "A linear fit of the continuum in the visually selected line-free channels of the spw centered on the line emission has been calculated in the visibility plane and subtracted from the full spw." (2 Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12m and ACA visibilities concatenated before deconvolution  
  > "The 12m and ACA visibilities, calibrated and continuum subtracted, have been concatenated and used for the deconvolution." (2 Observations and data reduction)
- smoothing: spectral resolution smoothed to 20 km/s  
  > "The datacubes have been obtained smoothing the spectral resolution to 20 km/s." (2 Observations and data reduction)
- final beam: CO(2-1) 1.4x1.12 arcsec PA 33.04; CO(1-0) 2x1.7 arcsec PA 8.3  
  > "| CO(2-1) | 1.4            | 1.12           | 33.04 | 8$\cdot 10^{-4}$   | 4.2$\cdot 10^{-2}$  |" (Table 1)
- final rms: CO(1-0) 9e-4; CO(2-1) 8e-4 Jy/beam; continuum 1.8e-5 (B3), 4.4e-5 (B6)  
  > "| Cont    | 1.35           | 1.08           | 33.7  | 4.4$\cdot 10^{-5}$ | 6.7 $\cdot 10^{-4}$ |" (Table 1)

### Inherited from earlier work

- MUSE data analysis (emission lines, Balmer decrement dust correction, Halpha to SFR)  
  > "The MUSE data analysis has been performed as described in (cite: gaspI)" (2 Observations and data reduction) [from (cite: gaspI)]
- Adopted r21=0.79 for mass comparison, same as APEX analysis  
  > "we will use the same value (0.79) that we used in our APEX data analysis for the sake of comparison" (5 Quantifying the H2 mass) [from (cite: gaspX)]
- Mass formulae for H2 from CO fluxes  
  > "derive the molecular gas mass adopting the formulations by (cite: WatsonKoda2016)" (5 Quantifying the H2 mass) [from (cite: WatsonKoda2016)]
- Stellar disk contour from MUSE continuum  
  > "(as in Poggianti et al., accepted)" (3.1 Molecular gas morphology) [from Poggianti et al., accepted]

### Not stated but needed to reproduce (our reading)

- SoFiA parameter file (kernels, thresholds, reliability cut)
- gausspy+ parameters (alpha values, SNR thresholds)
- Line-free channel ranges for uvcontsub
- tclean cell size, image size, niter, threshold, primary beam limit
- Aperture/polygon definitions for regions A and B and for disk vs tail split
- Exact method for the disk/tail boundary and the large-scale fraction estimates
- Smoothing/regridding details for r21 and SFE maps
- Calibrator names other than flux calibrators (bandpass, phase)
- Mass conversion luminosity distance value

## Analysis recipe

1. **Calibrate, combine and image CO cubes and continuum**: Pipeline calibration, uvcontsub, concatenate 12m+ACA, tclean with natural weighting, 20 km/s channels  
  > "The 12m and ACA visibilities, calibrated and continuum subtracted, have been concatenated and used for the deconvolution." (2 Observations and data reduction)
   - software: CASA, tclean, uvcontsub
   - parameter: natural weighting for lines; 20 km/s channels; continuum robust 0.5  
  > "The weighting used for the line images has been natural, to enhance the sensitivity." (2 Observations and data reduction)
   - fitting: _not stated_
   - validation: 12m vs ACA flux scales consistent within 10% on overlapping scales  
  > "found that they are consistent within 10%, which is the calibration uncertainty" (2 Observations and data reduction)
2. **Detection masks and moment maps**: SoFiA source finding with smoothing kernels and reliability, moments 0-2 within masks  
  > "we constructed a detection mask using the SoFiA software (cite: sofia)." (3.1 Molecular gas morphology)
   - software: SoFiA
   - fitting: _not stated_
   - validation: _not stated_
3. **Define emitting regions**: 2D Gaussian fit on each clump in CO(2-1) moment-0 map  
  > "we fitted a 2d gaussian profile on each of them in the zero moment CO(2-1) map" (3.1 Molecular gas morphology)
   - fitting: 2D Gaussian per region  
  > "we fitted a 2d gaussian profile on each of them in the zero moment CO(2-1) map" (3.1 Molecular gas morphology)
   - validation: _not stated_
4. **Kinematics: multi-Gaussian line fits and PV diagram**: gausspy+ on pixels above 3 sigma; PV slit 20 arcsec x 9 arcsec at PA 0.66 deg  
  > "by using a multi-gaussian fitting of the CO line emission on each pixel above the 3$\sigma$ level." (3.2 Molecular gas kinematics)
   - software: gausspy+
   - parameter: slit 20 arcsec long, 9 arcsec wide, PA 0.66 deg  
  > "a generous slit 20 arcsec long and 9 arcsec wide, centered on the galaxy center, in the south-north direction with a Position Angle (PA) of 0.66 degrees" (3.2 Molecular gas kinematics)
   - fitting: gausspy+ automatic number of Gaussians  
  > "automatically evaluates the number of gaussians needed to fit a spectrum" (3.2 Molecular gas kinematics)
   - validation: _not stated_
5. **Derive r21 map**: Smooth CO(2-1) cube to CO(1-0) beam, regrid, ratio of zero-moment maps; Gaussian fit to distribution  
  > "we first masked the CO(2-1) and the CO(1-0) cubes at 20 $\rm km \, s^{-1}$ resolution" (4 r21)
   - fitting: Gaussian fit of r21 distribution  
  > "A gaussian fit of the distribution (shown in green in the lower panel of Fig. [6](#fig:r21_map)) finds an average value of $\sim 0.58 \pm 0.15$" (4 r21)
   - validation: _not stated_
6. **Compute H2 masses and compare with APEX**: Watson & Koda relations from CO(2-1) and CO(1-0) fluxes; integrate ALMA spectra in APEX regions A and B  
  > "we simply integrated the ALMA spectra within the two A and B regions defined by APEX pointings" (5 Quantifying the H2 mass)
   - parameter: alpha10=4.3; r21=0.79 fixed or measured per region  
  > "Throughout this paper we always use $\rm \alpha_{10}=4.3$" (5 Quantifying the H2 mass)
   - assumption: Milky Way CO-to-H2 conversion 2e20 cm^-2 (K km/s)^-1 with helium  
  > "CO-to-H2 = $2\times 10^{20}$ $cm^{-2}(K km s^{-1})^{-1}$ including the helium correction" (5 Quantifying the H2 mass)
   - assumption: H2/HI=0.3 for total gas fraction  
  > "Assuming for this galaxy a normal HI content, i.e. $\rm H_{2}$/HI=0.3" (5 Quantifying the H2 mass)
   - fitting: _not stated_
   - validation: Masses within 5% using Solomon & Vanden Bout formulation  
  > "does not change more than 5% our masses" (5 Quantifying the H2 mass)
7. **Resolved SFE and depletion time at 1 kpc**: Convolve MUSE Halpha SFR to ALMA beam, regrid, compare to H2 surface density, BPT star-forming spaxels  
  > "we first convolve them to the same resolution and regrid them to the same WCS grid." (6 Resolved Star Formation Efficiency)
   - assumption: Chabrier IMF; Balmer decrement dust correction  
  > "We then converted the H$\alpha$ flux in SFR adopting the (cite: Chabrier2003) IMF" (6 Resolved Star Formation Efficiency)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.4.0-7: calibrated data analysis, uvcontsub, tclean  
  > "The calibrated data have been further analyzed with the CASA software (version 5.4.0-7; (cite: CASA))." (2 Observations and data reduction)
- **SoFiA** : detection masks  
  > "we constructed a detection mask using the SoFiA software (cite: sofia)." (3.1 Molecular gas morphology)
- **gausspy+** : multi-Gaussian fitting of CO spectra  
  > "We have used the *gausspy+* code" (3.2 Molecular gas kinematics)
- **Astropy** : listed software  
  > "Astropy (cite: astropy; astropy2), CASA (cite: CASA)" (Software)
- **APLpy** : plotting  
  > "This research made use of APLpy, an open-source plotting package for Python" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total H2 mass from ALMA | 2.5e10 | not stated | Msun | 6 | We find that ALMA data account for a total $\rm H_{2}$ mass of $\sim 2.5\times 10^{10}$$\rm M_\odot$. |
| H2 mass in disk | 1.8e10 | not stated | Msun | 6 | total molecular gas mass in the galaxy disk of $1.8\times 10^{10}$$\rm M_\odot$ |
| H2 mass in tail | 0.7e10 | not stated | Msun | 6 | while in the tail it amounts to $0.7\times 10^{10}$$\rm M_\odot$. |
| Mean r21 in disk | 0.58 | 0.15 | dimensionless | 5 | finds an average value of $\sim 0.58 \pm 0.15$ in the galaxy disk |
| Flux fraction missed by 12m only | ~43% (disk), ~70% (tail) | not stated | percent | 6 | we miss $\sim$43% of the flux in the galaxy disk and $\sim$70% in the tail region. |
| CO(2-1) flux region A (12m, 12m+ACA, APEX) | 63, 99, 110 | ~10% ALMA | Jy km/s | 6 | / JW100 \[A\] / 63      / 99      / 110     /     /     / |
| Mean depletion time in disk regions D1-D3 | 6.6 | not stated | Gyr | 7 | The average depletion time in the disk regions (D1, D2 and D3) is 6.6 Gyr |
| Mean depletion time in near-tail regions | 7.3 | not stated | Gyr | 7 | where it reaches 7.3 Gyr |
| Depletion time far tail | 13.9 | not stated | Gyr | 7 | (13.9 Gyr on average) |
| Minimum measurable mass | ~1e7 | not stated | Msun | 2 | is $\sim 1 \times 10^7$ $\rm M_\odot$ |

## Qualitative findings

- CO is displaced toward the west (ram-pressure direction), with a deficit near the nucleus and clumps in the tail out to ~35 kpc  
  > "it is clearly less extended and displaced towards the west side of the disk" (3.1 Molecular gas morphology)
- Double CO components only within 1-2 kpc of the disk; tail CO fits a single Gaussian with low dispersion  
  > "The CO(2-1) emission in the tail regions can be fitted instead with one single gaussian" (3.2 Molecular gas kinematics)

## Claim tuples

- H: Is JW100 unusually rich in molecular gas, with a significant fraction in the stripped tail? | E: CO(2-1) and CO(1-0) masses from ALMA 12m+ACA | R: Total ~2.5e10 Msun, ~30% in the tail, molecular fraction ~8% of stellar mass | F: JW100 is extremely rich in molecular gas, suggesting part is newly formed | **supported**
- H: Is the tail molecular gas formed in situ rather than stripped? | E: r21, line widths, kinematics and cloud lifetime vs travel time | R: r21 up to >=1 in the tail, low dispersion, single component; stripping would need ~5900 km/s | F: Tail gas is formed in situ from stripped HI or diffuse molecular gas | **partially**
- H: Is molecular gas diffuse on large scales, especially in the tail? | E: Compare 12m-only, 12m+ACA and APEX fluxes | R: 12m misses ~43% (disk) and ~70% (tail) | F: Tail gas is more diffuse than disk gas; ACA is essential | **supported**
- H: Does ram pressure change star formation efficiency of molecular gas? | E: Resolved depletion time at 1 kpc using MUSE SFR | R: Depletion times 5-10 Gyr in disk and tail regions, above ~2 Gyr | F: Low SFE in disk and tail | **supported**

## Reasoning

- Why this data: APEX beam ~28 arcsec could not resolve cold gas distribution, so ALMA at ~1 kpc resolution was collected  
  > "the APEX beam has a size of $\sim$28 $''$ at the observed frequency of CO(2-1), and therefore does not allow to study the cold gas distribution on small scales." (Introduction)
- Why this method: ACA added to recover large-scale flux  
  > "Additional observations with the 7m ACA array have been obtained in Band 6 to increase the maximum recoverable scale." (2 Observations and data reduction)
- Alternative: Massive outflow explanation for D1 rejected because of distance from the center and orientation differing from the ionized outflow  
  > "we therefore think it is not due to a massive outflow." (3.2 Molecular gas kinematics)
- How they decided it was enough: _not stated_
- Limitation (authors): Resolution cannot exclude that regions comprise unresolved clouds  
  > "our resolution is such that we can not exclude that each of them could be made of different unresolved regions." (3.1 Molecular gas morphology)
- Limitation (authors): No HI data available; total gas fraction relies on assumed H2/HI  
  > "Unfortunately, we could not observe the HI emission of this galaxy with the J-VLA" (5 Quantifying the H2 mass)
- Limitation (authors): Detailed kinematic characterization left for future work  
  > "A comprehensive characterization of the galaxy kinematics is beyond the scope of this paper" (3.2 Molecular gas kinematics)
- Caveat (inferred, ours): Single alpha_CO (MW) assumed everywhere, despite ram-pressure and AGN environment
- Caveat (inferred, ours): Fixed r21=0.79 vs measured values changes masses by up to ~25%
- Caveat (inferred, ours): Disk/tail masses depend on the arbitrary stellar-disk contour
- Caveat (inferred, ours): Large-scale flux fractions depend on APEX comparison with ~20% errors
- Caveat (inferred, ours): SFR from Halpha in AGN-contaminated regions only partly excluded

## Reproducibility

- Data public (paper): Data cited as ALMA project 2017.1.00496.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00496.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Line-free channel ranges
- Missing: tclean cell/image size and cleaning thresholds
- Missing: SoFiA and gausspy+ settings
- Missing: Region definitions for A/B and disk/tail
- Missing: MUSE data (not in ALMA archive)
- Missing: APEX spectra from earlier paper
- Data volume (inferred): ~100-300 GB raw for 12m, ACA Band 6 and Band 3 mosaics
- Score (inferred): 5/5, Data and main software known, but many imaging and SoFiA/gausspy+ parameters and MUSE/APEX inputs are not given.
- Rediscovery candidate: no, Recipe incomplete (masking, region definitions, MUSE and APEX inputs), so full numeric reproduction is not straightforward.

## Links

- Method: (cite: WatsonKoda2016) (H2 mass formulae from CO fluxes)
- Method: (cite: gaspI) (MUSE data analysis and SFR derivation)
- Method: (cite: sofia) (source finding)
- Method: (cite: gausspy+) (multi-Gaussian fitting)
- Companion: (cite: gaspX) (APEX CO observations of the same galaxies)
- Companion: Poggianti et al., accepted (multiwavelength baryon cycle analysis of JW100)
- Companion: (cite: gaspXIX) (AGN and outflow in JW100)
- Related: GASP (MUSE Large Program)
- Related: HERACLES
- Related: xCOLD GASS

## Checks

```json
{
 "quotes": 89,
 "quotes_ok": 89,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 90,
  "stated": 67,
  "rate": 0.744
 },
 "evidence_ok": true
}
```

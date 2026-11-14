# First Identification of 10 kpc [C II] 158 μm Halos around Star-forming Galaxies at z = 5-7

`2019ApJ...887..107F` | The Astrophysical Journal 2019 | first author: Fujimoto, Seiji | arXiv: 1902.06760 | DOI: 10.3847/1538-4357/ab480f

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies
- Question: Do normal star-forming galaxies at z=5-7 have extended (~10 kpc) [CII] 158um halos, and how do they compare with the dust and stellar continuum, Lya halos and simulations?  
  > "We report the discovery of 10-kpc 158$\mu$m halos surrounding star-forming galaxies in the early Universe." (abstract)
- Target **18 [CII]-detected star-forming galaxies at z=5.153-7.142 (e.g. WMH5, CLM1, COS301855, Hz1-Hz9, NB816-S-61269, WMH13)**: coordinates per-source R.A./Dec. listed in Table 1  
  > "The 18 line sources have the spectroscopic redshifts determined by the lines ($z_{\rm [CII]}$) and the absolute rest-frame UV magnitudes" (2.1 Our ALMA Sample); z/distance z=5.153-7.142; weighted average z=6.01, 1''=5.7 kpc  
  > "The 18 line sources have the spectroscopic redshifts determined by the lines ($z_{\rm [CII]}$) and the absolute rest-frame UV magnitudes" (2.1 Our ALMA Sample); distance from [CII] line redshifts  
  > "The 18 line sources have the spectroscopic redshifts determined by the lines ($z_{\rm [CII]}$) and the absolute rest-frame UV magnitudes" (2.1 Our ALMA Sample)

## Data provenance

- ALMA projects: 2012.1.00523.S, 2012.1.00602.S, 2013.1.00815.S, 2015.1.00834.S, 2015.1.01111.S, 2016.1.01240.S
- bands: Band 6/7  
  > "utilizing new and archival deep ALMA Band 6/7 data" (1 Introduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Per-source beams 0.40''x0.29'' to 1.85''x1.05'' (natural weighting); stacked 0.43''x0.36'' (ALMA-ALL)  
  > "synthesized beam size of $0.43\ensuremath{''}\times0.36\ensuremath{''}$ ($0.74\ensuremath{''}\times0.58$)" (3.2 ALMA Visibility-based Stacking)
- max recoverable scale: _not stated_
- sensitivity: Stacked continuum rms 4.1 (ALMA-ALL) and 8.3 (ALMA-HST) uJy/beam; per-source 8-64 uJy/beam  
  > "the standard deviation of the pixel values in the dust continuum image achieves 4.1 (8.3) $\mu$Jy/beam" (3.2 ALMA Visibility-based Stacking)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: [CII] 2P3/2 -> 2P1/2 (1900.5469 GHz)
- Other facility **HST/WFC3 F160W**: Rest-frame UV H-band images for 9 sources (ALMA-HST sample), from the Hubble Legacy Archive  
  > "we also use the HST Wide Field Camera 3 (WFC3) in F160W, 1.54 $\mu$m ($H$-band), images from the Hubble Legacy Archive" (2.3 HST Data)
- Other facility **Gaia DR2**: Astrometric correction of HST images  
  > "we calibrate the astrometry of the $H$-band maps with the Gaia Data Release 2 catalog" (2.3 HST Data)
- External data: Leclercq et al. Lya halo scale lengths from MUSE (6 LAEs at z>5)  
  > "we use the recent results with the deep MUSE data for the high-$z$ LAEs of (cite: leclercq2017)" (4.4 Scale Length of Halo) [from (cite: leclercq2017)]
- External data: Local dwarf galaxy L[CII]/SFR ratios  
  > "global scale $L_{\rm [CII]}$/SFR$_{\rm total}$ ratios of the local dwarf galaxies (cite: delooze2014)" (4.3 Radial ratio) [from (cite: delooze2014)]
- External data: Extended [CII] around local LIRGs  
  > "we show the $L_{\rm [CII]}$/SFR$_{\rm total}$ ratios of the extended emission around local LIRGs" (4.3 Radial ratio) [from (cite: diaz-santos2014)]
- Simulation/model as data: Althaea zoom-in hydro+dust RT simulation; 12 snapshots at 6.0<=z<=7.2, 4 angles each  
  > "For the Alth$\ae$a simulation, we take 12 snapshots at different redshifts within $6.0\leq z\leq7.2$" (4.6 Comparison with Model)
- Simulation/model as data: Gadget-3 SPH zoom-in halos Halo-12, A, B, C with ART2 radiative transfer  
  > "we use four different halos: Halo-12, Halo-A, Halo-B, and Halo-C" (4.6 Comparison with Model)

## Processing

### Calibration

- pipeline or manual: Standard reduction with ALMA-provided scripts in CASA, plus flux re-calibration and extra antenna flagging where needed  
  > "in the standard manner with the scripts provided by the ALMA observatory" (2.2 ALMA Data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "produced by the CLEAN algorithm with the tclean task with a pixel scale of $0.01\ensuremath{''}$" (2.2 ALMA Data)
- deconvolver: _not stated_
- weighting robust: natural  
  > "Synthesized beam size of our ALMA maps (weighting = "natural")." (Table 1)
- uv taper: _not stated_
- cell size: 0.01''  
  > "with a pixel scale of $0.01\ensuremath{''}$" (2.2 ALMA Data)
- image size: _not stated_
- masking: CLEAN boxes at peak pixels S/N>=5, cleaned to 3 sigma; line cubes not cleaned; dirty images used for analysis  
  > "The CLEAN boxes were set at the peak pixel positions with S/N $\geq$ 5 in the auto mode" (2.2 ALMA Data)
- multiscale scales: _not stated_
- continuum subtraction: uv continuum subtraction for 4 sources (Hz4, Hz6, Hz9, WMH5)  
  > "the continuum is subtracted from the $uv$-data of the line cubes for 4 sources" (2.2 ALMA Data)
- line free channels: velocity range v>|2xFWHM| in same baseband  
  > "estimated from the channels in the velocity range of $v>$ $|$2 $\times$ FWHM$|$ in the same baseband" (2.2 ALMA Data)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 20 km/s channels for cubes; uv-taper 0.6'' for centroiding  
  > "the velocity channel width is re-binned to 20 km s$^{-1}$" (2.2 ALMA Data)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- uv-plane Monte Carlo justification for centroiding on uv-tapered maps  
  > "Monte-Carlo simulations in the $uv$-visibility plane show that smoothed maps have lower uncertainties in the positional measurements than the intrinsic maps (cite: fujimoto2018)" (3.1 3D Position) [from (cite: fujimoto2018)]
- Stacked-spectrum procedure  
  > "we adopt the same manner as previous ALMA studies (cite: decarli2018; bischetti2018)" (4.5 [C ii] Stacked Spectrum) [from (cite: decarli2018; bischetti2018)]
- SFR calibrations  
  > "with the equations in (cite: murphy2011)" (4.3 Radial ratio) [from (cite: murphy2011)]

### Not stated but needed to reproduce (our reading)

- Exact flux re-calibrations and extra flagging per dataset
- CASA version
- Stacker and statwt parameters
- Random-aperture method details and radial bin definitions
- galfit/uvmultifit initial conditions and priors
- Simulation outputs (Althaea, Halo-A/B/C unpublished)
- Aperture/continuum image parameters beyond natural weighting

## Analysis recipe

1. **Reduce ALMA data and image**: CASA standard calibration, tclean cubes at 20 km/s and continuum, uv continuum subtraction for 4 sources  
  > "The continuum images and line cubes are produced by the CLEAN algorithm with the tclean task" (2.2 ALMA Data)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared re-reduced [CII] morphology and spectra to previous studies  
  > "We confirm that the spatial morphology and the spectrum shape of the \[C ii\] lines are consistent with the previous studies" (Appendix)
2. **Measure 3D source positions**: Velocity-integrated map, peak position on uv-tapered (0.6'') map, Gaussian fit to 1.2'' aperture spectrum for peak and FWHM, then re-integrate over 2xFWHM  
  > "We obtain the peak frequencies and FWHMs of the [CII] line emission by fitting a single Gaussian to the [CII] spectra." (3.1 3D Position)
   - software: CASA
   - fitting: single Gaussian  
  > "We obtain the peak frequencies and FWHMs of the \[C ii\] line emission by fitting a single Gaussian to the \[C ii\] spectra." (3D Position in ALMA Cube)
   - validation: _not stated_
3. **Visibility-based stacking**: Extract +-50 km/s line channels (and line-removed continuum), shift centers with stacker, concat, statwt reweight  
  > "Second, we shift the coordinate of the visibility datasets by re-writing the source center determined in Section [3.1](#sec:lp_measure) as "00:00:00.00 00:00:00.0" with stacker" (ALMA Visibility-based Stacking)
   - software: stacker, CASA concat, CASA statwt
   - assumption: z=6.01 average, 1''=5.7 kpc  
  > "we adopt the angular scale of $1''=5.7$ kpc in the following analyses" (3.2 ALMA Visibility-based Stacking)
   - fitting: _not stated_
   - validation: Leave-one-out sample variance, removal of low-resolution/companion sources, z split, noise-enhanced maps  
  > "Second, we evaluate the uncertainty of the sample variance. We make 18 newly stacked data with 17 \[C ii\] line sources" (ALMA Visibility-based Stacking)
4. **Stack HST H-band images**: 8''x8'' stamps, remove low-z contaminants with galfit Sersic, noise-weighted average, convolve to ALMA beam with 3-Sersic galfit kernel  
  > "We remove the low-redshift contaminants from the $H$-band images by fitting S$\acute{\rm e}$rsic profiles" (3.3 HST/H-band Stacking)
   - software: galfit, sextractor
   - fitting: three Sersic kernel  
  > "For the kernel, we assume a sum of three independent S${\acute{\rm e}}$rsic profiles whose positions are fixed at the center." (HST/H-band Stacking)
   - validation: Mock vs actual ALMA beam residual <~1.8% within 1''  
  > "the difference between the mock and actual ALMA beams are less than $\sim 1.8$%" (3.3 HST/H-band Stacking)
5. **Radial profiles and L[CII]/SFR**: Radial surface brightness of dirty images; SFR_IR and SFR_UV from Murphy+11 with modified blackbody  
  > "$\beta_{\rm d}=1.8$ (cite: planck2011) and $T_{\rm d}=35$ K (cite: coppin2008)" (4.3 Radial ratio)
   - assumption: beta=1.8, Td=35 K, single Gaussian line FWHM 270 km/s to correct 100 km/s window  
  > "we correct the velocity-integrated value in the range from 100 km s$^{-1}$ to 270 km s$^{-1}$, assuming a single Gaussian line profile, to recover the total value of $L_{\rm [CII]}$." (Radial ratio of $L_{\rm [CII]}$ to total SFR)
   - fitting: _not stated_
   - validation: _not stated_
6. **Fit halo scale length**: Two-component Sersic (central, fixed from HST) + exponential halo with galfit; uvmultifit visibility fits as check  
  > "We characterize the detail radial surface brightness profile of the line emission by two-component fitting with galfit." (4.4 Scale Length of Halo)
   - software: galfit, uvmultifit
   - fitting: central positions fixed  
  > "We fix the central positions of both central and halo components to obtain a stable result." (Scale Length of Halo)
   - validation: uvmultifit re=5.1+-1.7 kpc consistent with galfit  
  > "Note that the visibility-based profile fitting with uvmultifit (cite: marti2014) also provides us with the best-fit value of $r_{\rm e}=5.1\pm$ 1.7 kpc for the halo component" (Scale Length of Halo)
7. **Compare with simulations**: Stack simulated [CII], FIR, UV images (9 of 48 Althaea; 12 Halo images) and smooth to ALMA beam  
  > "we carry out the stacking for the zoom-in simulation results of the [CII] line, the rest-frame FIR and the rest-frame UV continuum in the same manner as the observations" (4.6 Comparison with Model)
   - software: cloudy, Gadget-3, ART2
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Data reduction, tclean, concat, statwt  
  > "Common Astronomy Software Applications package (CASA; (cite: mcmullin2007))" (2.2 ALMA Data)
- **stacker** : Shifting visibility phase centers  
  > "with stacker (cite: lindroos2015)" (3.2 ALMA Visibility-based Stacking)
- **galfit** : Contaminant removal, PSF kernel, two-component profile fits  
  > "fitting S$\acute{\rm e}$rsic profiles (cite: sersic1963) with galfit (cite: peng2010)" (3.3 HST/H-band Stacking)
- **uvmultifit** : Visibility-based profile fitting  
  > "visibility-based profile fitting with uvmultifit (cite: marti2014)" (4.4 Scale Length of Halo)
- **sextractor** 2.5.0: Bright-object detection for HST astrometry  
  > "with sextractor version 2.5.0 (cite: bertin1996)" (2.3 HST Data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Stacked [CII] peak S/N (ALMA-ALL) | 21 | not stated | sigma | 3 | 21$\sigma$ (20$\sigma$) and 10$\sigma$ (8$\sigma$) significance levels for the line and dust continuum |
| Halo scale length r_n | 3.3 | 0.1 | kpc | 6 | We obtain the best-fit scale-length values of $r_{\rm n}=$ 3.3 $\pm$ 0.1 kpc. |
| Halo effective radius | 5.6 | 0.1 | kpc | 6 | best-fit effective radius of $r_{\rm e}=5.6$ $\pm$ 0.1 kpc |
| Central UV Sersic r_e | 1.1 | 0.1 | kpc | 6 | $r_{\rm e}=1.1\pm0.1$ kpc and $n=1.2\pm0.01$ |
| Median Lya r_n of 6 LAEs | 3.8 | 1.7 | kpc | 6 | The median $r_{\rm n}$ value for the 6 LAEs is estimated to be $3.8\pm1.7$ kpc |
| Stacked spectrum core and broad FWHM | 296 and 799 | 40 and 654 | km/s | 0 | 296 $\pm$ 40 km/s and 799 $\pm$ 654 km/s for the core and broad components |
| Outer-region L[CII]/SFR_total | >1e8 | not stated | Lsun Msun^-1 yr | 5 | The highest ratios ($> 10^{8}\, L_{\odot}\,M_{\odot}^{-1}\,{\rm yr}$) are found at the outer regions |

## Qualitative findings

- Simulations match dust and UV continuum but not the extended [CII] emission beyond r>5 kpc  
  > "the line emission in both simulations is not as extended as the observed data" (4.6 Comparison with Model)

## Claim tuples

- H: Do normal z=5-7 galaxies have ~10 kpc [CII] halos? | E: Visibility stacking of 18 galaxies | R: Extended [CII] to ~10 kpc at 9.2-9.3 sigma, more extended than continuum | F: [CII] halos exist universally | **supported**
- H: Halo comparable to Lya halos? | E: Sersic+exponential fit versus Leclercq+17 | R: r_n 3.3+-0.1 vs 3.8+-1.7 kpc | F: Scale lengths agree within 1 sigma | **supported**
- H: Satellite galaxies explain the halo? | E: Radial L[CII]/SFR ratio | R: Outer ratios >1e8 exceed dwarfs and LIRG halos | F: Satellites ruled out | **supported**
- H: Do simulations reproduce the halo? | E: Stack Althaea and Halo zoom-ins | R: Simulated [CII] less extended | F: Halo challenges current simulations | **supported**
- H: Outflow signatures in stacked spectrum | E: Two-Gaussian fit | R: Broad wing tentative at 3.2 sigma | F: No definite conclusion | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Dirty images used because extended structure is hard to model with CLEAN; stacking needed for S/N  
  > "Because the extended structure is difficult to be modeled by the clean algorithm perfectly, we use the dirty images" (3.2 ALMA Visibility-based Stacking)
- Alternative: Scenario A (satellite galaxies) rejected; B-E remain  
  > "From the observational results, we rule out scenario (A)." (5.3 Physical Origin of Halo)
- How they decided it was enough: _not stated_
- Limitation (authors): Faint AGN or past AGN activity cannot be ruled out; faint continuum or satellites could mimic the broad wing  
  > "we cannot rule out the possibility that our ALMA sources contain faint AGNs and/or have the past AGN activity." (5 Discussion)
- Caveat (inferred, ours): Heterogeneous archival data and beams (0.4''-1.9'') may bias stacked profiles
- Caveat (inferred, ours): Dirty-image profiles are affected by beam sidelobes
- Caveat (inferred, ours): Heterogeneous sample selection (FWHM>80 km/s, S/N>=5) biases toward bright [CII]
- Caveat (inferred, ours): Simulations were compared at different redshifts than most ALMA-HST sources
- Caveat (inferred, ours): Errors from the fit may be underestimated (0.1 kpc)

## Reproducibility

- Data public (paper): Archival ALMA projects listed; HST from Hubble Legacy Archive  
  > "images from the Hubble Legacy Archive" (2.3 HST Data)
- Products in archive: _not stated_
- Missing: Re-calibration/flagging details
- Missing: CASA version
- Missing: Newly simulated Halo-A/B/C outputs
- Missing: Radial bin definitions and noise estimation details
- Data volume (inferred): ~100-300 GB raw across 7 ALMA projects
- Score (inferred): 3/5, Public data and clear stacking recipe, but many parameters unstated and simulations unavailable.
- Rediscovery candidate: yes, Data are archival, the stacking recipe is mostly described, and results are numeric (scale length, S/N).

## Links

- Method: (cite: lindroos2015) (stacker visibility stacking tool)
- Method: (cite: marti2014) (uvmultifit)
- Method: (cite: fujimoto2018) (uv-plane Monte Carlo centroid tests)
- Companion: (cite: leclercq2017) (Lya halo profiles compared)
- Companion: (cite: kohandel2019) (Althaea morphology analysis)
- Companion: (cite: sugahara2019) (UV absorption outflow in overlapping sample)
- Related: Hubble Legacy Archive
- Related: COSMOS
- Related: Gaia DR2
- Related: OWLS
- Related: FiBY

## Checks

```json
{
 "quotes": 72,
 "quotes_ok": 72,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 6,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2015.1.01105.S"
 ],
 "codes_printed_but_missing": [
  "2015.1.01105.S"
 ],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 84,
  "stated": 51,
  "rate": 0.607
 },
 "evidence_ok": true
}
```

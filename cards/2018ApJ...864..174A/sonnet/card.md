# The 30 Year Search for the Compact Object in SN 1987A

`2018ApJ...864..174A` | The Astrophysical Journal 2018 | first author: Alp, Dennis | arXiv: 1805.04526 | DOI: 10.3847/1538-4357/aad739

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, stellar_physics, transients
- Question: What upper limits can be placed on the compact object in SN 1987A from millimeter to X-ray observations, and what do they imply for a neutron star or black hole?  
  > "Despite more than 30 years of searches, the compact object in Supernova (SN) 1987A has not yet been detected." (abstract)
- Target **SN 1987A**: coordinates RA 05h35m27.9875s, Dec -69d16m11.107s (ICRF J2015.0), from fitting HST hotspot ellipses  
  > "The distance to SN 1987A is taken to be 51.2 kpc (cite: panagia91; gould98; panagia99; mitchell02)." (3 Methods); "The arithmetic mean of the 33 best-fit coordinates are $\alpha = 05^\mathrm{h}\,35^\mathrm{m}\,27^\mathrm{s}\!.9875(11)," (3.1 Position of SN 1987A); z/distance 51.2 kpc  
  > "The distance to SN 1987A is taken to be 51.2 kpc (cite: panagia91; gould98; panagia99; mitchell02)." (3 Methods); "The arithmetic mean of the 33 best-fit coordinates are $\alpha = 05^\mathrm{h}\,35^\mathrm{m}\,27^\mathrm{s}\!.9875(11)," (3.1 Position of SN 1987A); distance from Panagia et al. 1991; Gould & Uza 1998; Panagia 1999; Mitchell et al. 2002  
  > "The distance to SN 1987A is taken to be 51.2 kpc (cite: panagia91; gould98; panagia99; mitchell02)." (3 Methods); "The arithmetic mean of the 33 best-fit coordinates are $\alpha = 05^\mathrm{h}\,35^\mathrm{m}\,27^\mathrm{s}\!.9875(11)," (3.1 Position of SN 1987A)

## Data provenance

- ALMA projects: 2013.1.00280.S, 2015.1.00631.S
- bands: Band 6 (1.3 mm, 211-275 GHz)  
  > "ALMA observations of SN 1987A (Table [1](#tab:obs_all)) at 1.3 mm (Band 6, 211–275 GHz) were performed on two different epochs" (2.1 ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: Cycle 2: 23-770 klambda; Cycle 3: 190-8600 klambda  
  > "Cycle 2 modest angular resolution data (2013.1.00280; 23–770 k$\lambda$) were obtained on 2 September 2014." (2.1 ALMA); "Cycle 3 high angular resolution data (2015.1.00631; 190–8600 k$\lambda$) were obtained from 1 to 15 November 2015" (2.1 ALMA)
- angular resolution: Beams 57x40 mas (213 GHz), 49x30 mas (233 GHz), 40x34 mas (247 GHz)  
  > "The FWHM of the restoring beam of the 213GHz image is $57\times40$ mas$^{2}$ (major and minor axis), the 233GHz image $49\times30$ mas$^{2}$, and the 247GHz image $40\times34$ mas$^{2}$." (2.1 ALMA)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2 Sep 2014 (Cycle 2); 1-15 Nov 2015 (Cycle 3)  
  > "Cycle 3 high angular resolution data (2015.1.00631; 190–8600 k$\lambda$) were obtained from 1 to 15 November 2015" (2.1 ALMA)
- pi or archival as stated: _not stated_
- Other facility **HST (WFC3, STIS)**: Optical/UV/NIR imaging and optical spectrum for limits and position  
  > "*Hubble Space Telescope* (*HST*) in optical and ultraviolet (UV), and *Chandra* in X-rays." (1 Introduction)
- Other facility **VLT (NACO, SINFONI)**: NIR imaging and spectra  
  > "the Very Large Telescope (VLT) in near-infrared (NIR)" (1 Introduction)
- Other facility **Chandra ACIS/HETG**: X-ray spectrum of central region  
  > "*Chandra* observed SN 1987A on 17 September 2015 (Obs. ID 16756, Table [1](#tab:obs_all))" (2.6 Chandra)
- External data: X-ray ejecta absorption column densities from 3D neutrino-driven explosion models (B15)  
  > "Here, we use the absorption estimates based on the B15 explosion model (cite: woosley88) for our X-ray analysis." (9 X-ray Ejecta Absorption) [from (cite: alp18b)]
- External data: Dust luminosity L_d = 295 +/- 17 Lsun from Herschel  
  > "$L_\mathrm d = 295 \pm 17$ L$_{\ensuremath{\odot}}$ (cite: matsuura15; dwek15)" (4.5 Bolometric Limit) [from (cite: matsuura15; dwek15)]
- External data: Ti-44 luminosity L_Ti = 298 +/- 36 Lsun  
  > "$L_\mathrm{Ti} = 298 \pm 36$ L$_{\ensuremath{\odot}}$ (cite: jerkstrand11; boggs15)" (4.5 Bolometric Limit) [from (cite: jerkstrand11; boggs15)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0519-4546 (also J0334-4008 for one 247 GHz execution)  
  > "The quasar J0519-4546 (05:19:49.72, -45:46:43.85; 0.75 Jy at 234 GHz) was the absolute flux calibrator" (2.1 ALMA)
- flux scale uncertainty: better than 7 %  
  > "These combined yield an estimated absolute flux calibration uncertainty of better than 7 %." (2.1 ALMA)
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "For imaging we use the task `tclean` with multiscale deconvolution with scales of 0 and 7 times the $6^2$mas$^{2}$ pixel size." (2.1 ALMA)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 6 mas  
  > "multiscale deconvolution with scales of 0 and 7 times the $6^2$mas$^{2}$ pixel size" (2.1 ALMA)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: 0 and 7 pixels  
  > "multiscale deconvolution with scales of 0 and 7 times the $6^2$mas$^{2}$ pixel size" (2.1 ALMA)
- continuum subtraction: _not stated_
- line free channels: 211.83-213.25, 232.55-233.52, 245.95-247.20 GHz  
  > "211.83–213.25 GHz, 232.55–233.52 GHz, and 245.95–247.20 GHz (cite: matsuura17)" (2.1 ALMA)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 57x40, 49x30, 40x34 mas, then mapped to circular beams  
  > "the real-space images are transformed by a linear mapping such that the beams are circular for optimal performance with the finding algorithm" (2.1 ALMA)
- final rms: _not stated_

### Inherited from earlier work

- Line-free spectral ranges for ALMA continuum images  
  > "211.83–213.25 GHz, 232.55–233.52 GHz, and 245.95–247.20 GHz (cite: matsuura17)" (2.1 ALMA) [from (cite: matsuura17)]
- X-ray ejecta absorption model  
  > "based on three-dimensional neutrino-driven SN explosion models (cite: alp18b)" (abstract) [from (cite: alp18b)]

### Not stated but needed to reproduce (our reading)

- tclean weighting/robust, niter, threshold and masks
- CASA version and calibration script
- Number of Cycle 2/3 executions and which data enter each of the three images
- Noise (rms) of the ALMA images
- Image size and phase-center details

## Analysis recipe

1. **Make ALMA continuum images**: Calibrate and image data into 3 narrow line-free frequency images with tclean multiscale  
  > "We use the Common Astronomy Software Application[^1] (cite: mcmullin07) to calibrate and image the interferometric data into 3 images" (2.1 ALMA)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Point-source upper limits via artificial sources**: Insert artificial PSFs and recover them with daofind until crossing 3-sigma threshold, repeated every 12.5 mas in the 800 km/s kick search region (radius ~100 mas)  
  > "Limits are determined by inserting artificial PSFs and finding the PSF flux such that it just crosses the 3-$\sigma$ threshold of `daofind`." (8 Finding Algorithm)
   - software: DAOPHOT daofind
   - parameter: daofind sigma set to off-source noise for ALMA  
  > "For ALMA images, this is set to the off-source noise in the images." (8 Finding Algorithm)
   - assumption: Compact object is a point source  
  > "The source luminosity limits based on the imaging analysis rely on the assumption that the compact object is a point source." (3 Methods)
   - fitting: _not stated_
   - validation: Noise cross-checked with visibility amplitudes  
  > "We verified that this method gives essentially the same noise estimates as measurements of the noise in the visibility amplitudes." (8 Finding Algorithm)

## Software

- **CASA** : Calibrate and image ALMA data (tclean)  
  > "We use the Common Astronomy Software Application[^1] (cite: mcmullin07) to calibrate and image the interferometric data" (2.1 ALMA)
- **XSPEC** 12.9.1p: X-ray spectral analysis  
  > "XSPEC 12.9.1p (cite: arnaud96) is used for the spectral analysis" (2.6 Chandra)
- **CIAO** 4.9: Chandra data reduction  
  > "The data are reduced following standard procedures using CIAO 4.9 and CALDB 4.7.7 (cite: fruscione06)." (2.6 Chandra)
- **DAOPHOT** : PSF fitting and daofind source finding  
  > "Searches for point sources in the ejecta are made using the DAOPHOT task `daofind`." (8 Finding Algorithm)
- **MARX** 5.3.2: Chandra PSF simulation  
  > "The *Chandra* PSF is created using MARX 5.3.2 (cite: davis12)" (12 Chandra PSF)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA 213 GHz point-source limit | 0.11 | not stated | mJy | 2 | /    213    /     0.11     / |
| ALMA 233 GHz point-source limit | 0.20 | not stated | mJy | 2 | /    233    /     0.20     / |
| ALMA 247 GHz point-source limit | 0.12 | not stated | mJy | 2 | /    247    /     0.12     / |
| Bolometric limit, dust-free | 22 | not stated | Lsun | 0 | The allowed bolometric luminosity of the compact object is 22 L$_{\ensuremath{\odot}}$ if our line-of-sight is free of ejecta dust, or 138 L$_{\ensuremath{\odot}}$ if dust-obscured. |
| Bolometric limit, dust-obscured | 138 | not stated | Lsun | 0 | The allowed bolometric luminosity of the compact object is 22 L$_{\ensuremath{\odot}}$ if our line-of-sight is free of ejecta dust, or 138 L$_{\ensuremath{\odot}}$ if dust-obscured. |

## Qualitative findings

- No point source seen in any ALMA image; ER and central ejecta resolved  
  > "The ER and central ejecta structure are clearly resolved and no obvious point source is seen in any of the ALMA images." (4.2 Millimeter & UVOIR Image Limits)

## Claim tuples

- H: Can the compact object in SN 1987A be detected or constrained across the spectrum? | E: Point-source and spectral limits from ALMA, VLT, HST, Chandra plus energy budget | R: Limits ~0.1 mJy at 213 GHz, ~1 Lsun optical, ~1e36 erg/s X-ray; bolometric 22/138 Lsun | F: Most likely a dust-obscured thermally-emitting neutron star; Crab-like pulsars excluded | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Conclusion is model-dependent  
  > "We stress that this result is model-dependent." (6 Summary & Conclusions)
- Caveat (inferred, ours): ALMA is one of several datasets; limits depend on point-source assumption and ejecta-dust modelling
- Caveat (inferred, ours): ALMA imaging parameters are underspecified

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: tclean weighting and thresholds
- Missing: CASA version
- Missing: Detailed ALMA noise levels
- Data volume (inferred): ~100s GB for the two ALMA projects (raw); other facilities add more
- Score (inferred): 3/5, ALMA part is only partially specified; the multi-facility analysis is described but with missing parameters.
- Rediscovery candidate: no, Multi-facility analysis with incomplete ALMA imaging recipe.

## Links

- Companion: (cite: alp18b) (X-ray ejecta absorption from 3D explosion models)
- Companion: (cite: matsuura17) (Earlier ALMA analysis of SN 1987A; source of line-free ranges)

## Checks

```json
{
 "quotes": 48,
 "quotes_ok": 48,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 35,
  "rate": 0.53
 },
 "evidence_ok": true
}
```

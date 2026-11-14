# ALMA 26 arcmin<SUP>2</SUP> Survey of GOODS-S at 1 mm (ASAGAO): Near-infrared-dark Faint ALMA Sources

`2019ApJ...878...73Y` | The Astrophysical Journal 2019 | first author: Yamaguchi, Yuki | arXiv: 1903.02744 | DOI: 10.3847/1538-4357/ab0d22

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Are there faint ALMA 1.2 mm sources in GOODS-S with no near-IR (H/K) counterparts, what are their likely redshifts and physical properties, and how much do they contribute to the cosmic SFRD?  
  > "All these studies strongly motivate us to conduct a systematic search for near-IR-dark faint SMGs in the fields where the deepest near-IR images to date are available." (Introduction)
- Target **K-dropout ASAGAO sources (ID17, ID20, ID22, ID24, ID25) in GOODS-S**: coordinates ID17: RA 53.206042, Dec -27.819166 deg (J2000); others in Table 1  
  > "| 17 | 53.206042 | $-$27.819166 | 0.564 $\pm$ 0.090 | 6.078 | 0.403 | 3.93$^{+0.43}_{-0.30}$ | $>$4.14 | Y |" (Table 1); z/distance ID17 z = 3.93 (+0.43/-0.30) from S3.6um/S1.2mm; others lower limits z>~4.5-5.9  
  > "| 17 | 53.206042 | $-$27.819166 | 0.564 $\pm$ 0.090 | 6.078 | 0.403 | 3.93$^{+0.43}_{-0.30}$ | $>$4.14 | Y |" (Table 1); distance from photometric redshift from flux ratio assuming average ALESS SED  
  > "| 17 | 53.206042 | $-$27.819166 | 0.564 $\pm$ 0.090 | 6.078 | 0.403 | 3.93$^{+0.43}_{-0.30}$ | $>$4.14 | Y |" (Table 1)

## Data provenance

- ALMA projects: 2015.1.00098.S, 2015.1.00543.S, 2012.1.00173.S
- bands: _not stated_
- frequencies and spectral setup: 1.14 mm and 1.18 mm (two tunings), central wavelength 1.16 mm  
  > "The 26 arcmin$^2$ map of the ASAGAO field was obtained at 1.14 mm and 1.18 mm (two tunings) to cover a wider frequency range, whose central wavelength was 1.16 mm." (2 ALMA source catalog)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.59" x 0.53" (PA = -83 deg) with 250 klambda taper  
  > "synthesized beam 0$^{\prime\prime}$.59 $\times$ 0$^{\prime\prime}$.53 (PA = $-$83$^\circ$)" (2 ALMA source catalog)
- max recoverable scale: _not stated_
- sensitivity: rms 30 uJy/beam in central ~4 arcmin^2, ~70 uJy/beam elsewhere  
  > "typical rms noise of 30 $\mu$Jy beam$^{-1}$ at the central $\sim$ 4 arcmin$^2$ and $\sim$ 70 $\mu$Jy beam$^{-1}$ at the remaining area" (2 ALMA source catalog)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **ZFOURGE (FourStar)**: K-band selected catalog for cross-matching  
  > "the 5$\sigma$ limiting magnitude of $K_s$ = 26.0 mag at the 80% completeness levels" (2 ALMA source catalog)
- Other facility **HST ACS/WFC3 (3D-HST)**: optical/near-IR images for stacking  
  > "First, we perform a stacking analysis for each 5 $K$-dropout ASAGAO candidates using optical/near-IR images obtained by the 3D-*HST* survey" (3 K-dropout ASAGAO candidates)
- Other facility **Spitzer/IRAC (S-CANDELS)**: 3.6, 4.5, 8.0 um photometry  
  > "This object is detected at 3.6 and 4.5 $\mu$m bands of *Spitzer*/InfraRed Array Camera" (3 K-dropout ASAGAO candidates)
- Other facility **JVLA C band**: 5 cm deep radio non-detections  
  > "They are not detected by the Kerl G. Jansky Very Large Array (JVLA) C band (5 cm) deep observation" (4 Physical properties)
- Other facility **JCMT/SCUBA2 and ALMA Band 7**: 870 um detection of ID20  
  > "The observed flux density is 1.35 $\pm$ 0.24 mJy at 870 $\mu$m" (3 K-dropout ASAGAO candidates)
- External data: ASAGAO 1.2 mm source catalog (25 sources S/N>5)  
  > "The details of the ALMA observations and the source catalog creation are given in (cite: hatsukade2018)." (2 ALMA source catalog) [from (cite: hatsukade2018)]
- External data: Average SED of ALESS sources with Av>3  
  > "obtained by (cite: dacunha2015)" (4 Physical properties) [from (cite: dacunha2015)]
- External data: IRAC 3.6/4.5 um magnitudes of ID17  
  > "Its apparent magnitudes at 3.6 $\mu$m and 4.5 $\mu$m are 25.38 $\pm$ 0.30 and 25.00 $\pm$ 0.27 mag, respectively (cite: ashby2015)." (3 K-dropout ASAGAO candidates) [from (cite: ashby2015)]
- External data: 870 um flux of ID20 (ID68)  
  > "This source is recognized as ID68 in (cite: cowie2018)." (3 K-dropout ASAGAO candidates) [from (cite: cowie2018)]

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
- uv taper: 250 klambda taper  
  > "After adopting a 250-k$\lambda$ taper, which gives an optimal combination of the sensitivity and angular resolution" (2 ALMA source catalog)
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

- ALMA observations, data combination and source catalog creation  
  > "The details of the ALMA observations and the source catalog creation are given in (cite: hatsukade2018). Here we provide a brief overview." (2 ALMA source catalog) [from (cite: hatsukade2018)]
- ZFOURGE cross-match of 20 of 25 sources  
  > "Yamaguchi et al. (submitted to ApJ) report that 20 of 25 sources candidates have been listed in $K$-band selected sources catalog" (2 ALMA source catalog) [from Yamaguchi et al. (submitted to ApJ)]

### Not stated but needed to reproduce (our reading)

- Imaging details (robust, cell, deconvolver, masks) are not given here
- CASA version and calibration not stated
- Stacking method details for HST images
- SED integration and SFR conversion details for L_IR
- Cosmic SFRD comoving volume and SFR values per source not tabulated

## Analysis recipe

1. **Cross-match ALMA sources with ZFOURGE**: Match S/N>5 sources to ZFOURGE K-band catalog after astrometric offset correction using Gaia; radius 0.5"  
  > "Here, we adopt the search radius $=$ 0$^{\prime\prime}$.5 for point-like sources, which is comparable with the synthesized beam of the final ALMA map." (2 ALMA source catalog)
   - fitting: _not stated_
   - validation: random coincidence likelihood 0.03  
  > "the likelihood of random coincidence is estimated to be 0.03" (2 ALMA source catalog)
2. **Reliability tests**: Source finding on negative map; split XX and YY polarization images  
  > "we split the ASAGAO visibilities into two polarization components (i.e., XX and YY polarization images)" (2 ALMA source catalog)
   - fitting: _not stated_
   - validation: all 5 detected at S/N ~3-5 in both XX and YY  
  > "we find that all 5 candidates are detected with S/N $\sim$ 3–5 in both XX and YY." (2 ALMA source catalog)
3. **Stack HST images**: Stack ACS/WFC3 images at ALMA positions with PSFs matched to F160W  
  > "the Point Spread Functions (PSFs) of the *HST* images are matched to the WFC3/*F160W* image" (3 K-dropout ASAGAO candidates)
   - fitting: _not stated_
   - validation: _not stated_
4. **Estimate redshift, stellar mass, LIR**: Flux ratios (3.6um/1.2mm, 5cm/1.2mm) with average ALESS SED; M*/L_H=0.15; IRAC 8 um upper limits  
  > "we adopt the average value (i.e., $M_*/L_H$ = 0.15 $M_\odot\ L_\odot^{-1}$) of those two extreme case." (4 Physical properties)
   - assumption: Average SED of ALESS sources with Av>3; Dale & Helou template with Tdust = 25 K at z~2  
  > "when we assume the SED template of (cite: dale2002) with $T_\mathrm{dust}$ = 25 K" (4 Physical properties)
   - fitting: _not stated_
   - validation: _not stated_
5. **Estimate contribution to cosmic SFRD**: Sum SFRs of K-dropout sources and divide by comoving volume for z~3-5  
  > "Here, we simply sum up the SFRs of $K$-dropout ASAGAO sources and divide them by the co-moving volume." (5 Contribution to the cosmic SFRD)
   - assumption: All lie at z~3-5  
  > "we assume the case that all of $K$-dropout ASAGAO candidates lie somewhere in the redshift interval of $z$ $\sim$ 3–5" (5 Contribution to the cosmic SFRD)
   - fitting: _not stated_
   - validation: SED-template uncertainty ~±0.3 dex  
  > "their contributions to the cosmic IR SFRD can vary by $\sim$ $\pm$ 0.3 dex" (5 Contribution to the cosmic SFRD)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ID17 photometric redshift | 3.93 | +0.43/-0.30 | dimensionless | 4 | it can lie at $z$ = 3.93$^{+0.43}_{-0.30}$ |
| Stellar mass 3sigma upper limit at z~4 | log(M*/Msun) <~ 10.4 | not stated | log Msun | 4 | $\log(M_*/M_\odot)$ $\lesssim$ 10.4 |
| LIR at z~4 | log(LIR/Lsun) ~ 12.0 (SFR log ~2) | not stated | log Lsun | 4 | find $\log(L_\mathrm{IR}/L_\odot)\sim$ 12.0 |
| SFRD contribution, all 5 sources | ~3e-3 | not stated | Msun/yr/Mpc^3 | 5 | ($\rho_\mathrm{SFR}\sim$ 3 $\times10^{-3}$ $M_\odot\ \mathrm{yr^{-1}\ Mpc^{-3}}$) |
| SFRD contribution, ID17 and ID20 only | ~1e-3 | not stated | Msun/yr/Mpc^3 | 5 | ($\rho_\mathrm{SFR}\sim$ 1 $\times10^{-3}$ $M_\odot\ \mathrm{yr^{-1}\ Mpc^{-3}}$) |

## Qualitative findings


## Claim tuples

- H: Do faint ALMA sources exist without near-IR counterparts? | E: Cross-match 25 S/N>5 ASAGAO sources with ZFOURGE, test reliability | R: 5 sources lack counterparts; ID17 and ID20 have IRAC/SCUBA2/Band 7 detections | F: Two secure and three tentative near-IR-dark faint ALMA sources | **supported**
- H: Are they high-redshift? | E: SED and flux-ratio redshift indicators | R: Consistent with z>~3-5 but low-z not excluded for 4 | F: Can lie at z>~3-5 | **partially**
- H: Do they contribute significantly to the cosmic SFRD? | E: Sum SFRs over comoving volume at z~3-5 | R: 1-3e-3 Msun/yr/Mpc^3 | F: Comparable to or greater than bright ALESS SMGs | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Three candidates may contain false detections  
  > "whereas remaining 3 sources may contain false detections" (2 ALMA source catalog)
- Caveat (inferred, ours): Redshifts rely on one assumed SED template
- Caveat (inferred, ours): Low S/N of candidates
- Caveat (inferred, ours): Source redshift range assumed for SFRD

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging and calibration details (in Hatsukade et al. 2018)
- Missing: Photometric catalogs and stacking details
- Data volume (inferred): ~100-300 GB for combined three ALMA projects
- Score (inferred): 3/5, Data public, but recipe mostly deferred to companion papers and the SFRD calculation is under-specified.
- Rediscovery candidate: no, Key processing and SED analysis are not detailed enough.

## Links

- Method: (cite: hatsukade2018) (ASAGAO observations and catalog)
- Companion: Yamaguchi et al. (submitted to ApJ) (ZFOURGE cross-matching of ASAGAO sources)
- Related: ASAGAO
- Related: ZFOURGE
- Related: 3D-HST
- Related: S-CANDELS
- Related: ALESS

## Checks

```json
{
 "quotes": 42,
 "quotes_ok": 42,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 30,
  "rate": 0.417
 },
 "evidence_ok": true
}
```

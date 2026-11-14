# The ALMA Frontier Fields Survey. II. Multiwavelength Photometric analysis of 1.1 mm continuum sources in Abell 2744, MACSJ0416.1-2403 and MACSJ1149.5+2223

`2017A&A...604A.132L` | Astronomy and Astrophysics 2017 | first author: Laporte, N. | arXiv: 1706.09605 | DOI: 10.1051/0004-6361/201730628

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: What are the optical/NIR/FIR counterparts, photometric redshifts and physical properties (stellar mass, SFR, dust) of the 12 ALMA 1.1 mm >5σ sources in A2744, M0416 and M1149?  
  > "We report here on the photometric analysis of all 1.1 mm continuum detections, combining data from the HST, VLT, Spitzer and Herschel observatories." (1. Introduction)
- Target **Abell 2744 (A2744)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **MACSJ0416.1-2403 (M0416)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **MACSJ1149.5+2223 (M1149)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00999.S
- bands: 1.1 mm continuum (Band 6)  
  > "was designed to produce deep ≈2.′1×2.′2 maps at 1.1mm covering the HST/WFC3 fields-of-view for all six clusters." (1. Introduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: unlensed 55, 59 and 71 µJy/beam for A2744, M0416, M1149  
  > "with unlensed sensitivities of 55, 59 and 71 µJy/beam respectively." (1. Introduction)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: ALMA Frontier Fields survey, PI F. Bauer  
  > "The ALMA Frontier Fields survey (ID 2013.1.00999.S, PI: F. Bauer)" (1. Introduction)
- Other facility **HST (ACS, WFC3)**: Frontier Fields optical/NIR mosaics, F435W to F160W  
  > "We used ACS F435W, F606W, F814W and WFC3 F105W, F125W, F140W, F160W -filter images obtained within the framework of the Frontier Fields (FFs) legacy survey" (2. Multi-wavelength Data)
- Other facility **VLT/HAWK-I**: Ks images for A2744 and M0416  
  > "We took benefit of the deep Ks images obtained with HAWK-I/VLT (Kissler-Patig et al. 2008) around A2744 and" (2. Multi-wavelength Data)
- Other facility **Spitzer (IRAC, MIPS)**: 3.6-24 µm photometry  
  > "We used images acquired with the IRAC and MIPS instruments onboard the Spitzer Space Telescope" (2. Multi-wavelength Data)
- Other facility **Herschel (PACS, SPIRE)**: 85-600 µm photometry  
  > "to add photometric constraints on the SEDs of the ALMA detected sources between ≈85–600 µm." (2. Multi-wavelength Data)
- Other facility **GLASS**: HST grism spectroscopic redshifts for five sources  
  > "Among all the ALMA-FFs DSFGs presented here, only five objects have GLASS redshifts:" (5.2 Spectroscopic Redshifts)
- External data: List of twelve 1.1 mm continuum detections, positions, beam sizes and ALMA sizes  
  > "Recently González-López et al. (2017) reported a list of twelve 1.1 mm continuum detections in these three clusters." (1. Introduction) [from González-López et al. (2017)]
- External data: AstroDeep photometric catalogs used for HST photometry  
  > "we will use the HST photometry they extracted for each source." (4.1 Hubble Space Telescope) [from Merlin et al. 2016, Castellano et al. 2016]
- External data: _not stated_ [from CATS group; Jauzac et al. 2014, 2015]

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

- HST optical size measurement method  
  > "measure the optical extents of our objects following the method described in Laporte et al. (2016)." (5.5 Star Formation Rate, Stellar mass, Dust properties and Size) [from Laporte et al. (2016)]
- Stacked SED method  
  > "we followed the method described in Dunlop et al. (2016) to compute the stacked SED of all our ALMA 1.1mm sources" (5.6 Stacked SED) [from Dunlop et al. (2016)]
- Spitzer reductions at 3.6 and 4.5 µm for A2744 and M0416  
  > "The reduction of the A2744 and M0416 images at 3.6 and 4.5 µm are described in detail in Laporte et al. (2014) and Laporte et al. (2015)" (2. Multi-wavelength Data) [from Laporte et al. (2014), Laporte et al. (2015)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, imaging and flux extraction details (taken from González-López et al. 2017)
- Hyperz updated version and exact setup, IMF, extinction law
- MAGPHYS settings and priors
- MCMC sampler details and software for Herschel deblending
- Which prior positions were added by hand for PACS
- Redshift-dependent stacking bin definitions

## Analysis recipe

1. **Find NIR counterparts**: Search in HST F160W within a circle of 2× the ALMA beam FWHM around each ALMA position  
  > "We examined all the sources residing within a circle centered on the ALMA position with a radius of 2× the ALMA average FWHM of the synthesized beam" (3. Search for NIR-counterparts)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure multiwavelength photometry**: AstroDeep or SExtractor for HST; daophot for Ks; GALFIT deblending for Spitzer; MCMC point-source fitting with ALMA priors for Herschel  
  > "the positions of the ALMA detected sources were used as priors for the to" (4.4 Herschel Space Observatory)
   - software: SExtractor, IRAF daophot, GALFIT
   - parameter: SExtractor DETECT_MINAREA 5 pixels, DETECT_THRESHOLD 1.5σ, DEBLEND_NTHRESH 32, DEBLEND_MINCONT 0.005  
  > "DETECT_THRESHOLD : 1.5σ" (4.1 Hubble Space Telescope)
   - fitting: Herschel fluxes: median of MCMC posterior, 3σ upper limits for non-detections  
  > "The flux corresponding to each point source was left to vary following an MCMC sampler." (4.4 Herschel Space Observatory)
   - validation: Compared with AstroDeep photometry; consistent within errors  
  > "We find consistency for nearly all measurement within the errors" (4.3 Spitzer Space Telescope)
3. **Photometric redshifts**: Hyperz template fitting on NIR-SED, FIR-SED and full SED, with decision rule on reduced chi2  
  > "We used an updated version of Hyperz (Bolzonella et al. 2000) to estimate the photometric redshifts of these sources." (5.1 Photometric redshifts)
   - software: Hyperz, iSEDfit
   - parameter: z = 0.0-6.0, Av = 0.0-20 mag  
  > "The reddening interval is defined between Av=0.0–20 mag" (5.1 Photometric redshifts)
   - fitting: Template fitting, FIR bands as true upper limits or pseudo-detections  
  > "We adopt a template-based method using template library models from" (5.1 Photometric redshifts)
   - validation: Cross-check with iSEDfit; comparison with GLASS spectroscopic redshifts  
  > "We find general consistency between the Hyperz and iSEDfit results." (5.1 Photometric redshifts)
4. **Magnification and physical properties**: Lenstool magnifications with CATS models; MAGPHYS SED fits at adopted redshifts  
  > "We use the latest version of MAGPHYS (da Cunha et al. 2008), adapted to fit the SED of" (5.5 Star Formation Rate, Stellar mass, Dust properties and Size)
   - software: Lenstool, MAGPHYS
   - assumption: Concordance cosmology Ωm=0.3, ΩΛ=0.7, H0=70  
  > "we use a concordance cosmology (ΩM = 0.3, ΩΛ = 0.7 and H0 = 70 km/s/Mpc)" (1. Introduction)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **SExtractor** v2.19.5: HST photometry for sources not in AstroDeep  
  > "we used SExtractor v2.19.5 (Bertin & Arnouts 1996) in double image mode" (4.1 Hubble Space Telescope)
- **GALFIT** : Deblending Spitzer IRAC and MIPS photometry  
  > "we adopt a deblending technique with the help of the GALFIT software (Peng et al. 2010)" (4.3 Spitzer Space Telescope)
- **IRAF daophot** : HAWK-I Ks aperture photometry  
  > "measured using 0′′.4 radius apertures with the IRAF NOAO daophot package" (4.2 Ground-based Telescopes)
- **Hyperz** updated version: Photometric redshifts  
  > "We used an updated version of Hyperz (Bolzonella et al. 2000)" (5.1 Photometric redshifts)
- **iSEDfit** : Cross-check of NIR-SED redshifts  
  > "we used another SED-fitting tool, iSEDfit (Moustakas et al. 2013), on the NIR-SED." (5.1 Photometric redshifts)
- **Lenstool** : Magnifications  
  > "We used Lenstool (Jullo & Kneib 2009) to calculate magnifications for the ALMA DSFGs" (5.4 Magnification)
- **MAGPHYS** latest version: Stellar mass, SFR, dust mass, Av, Tdust  
  > "We use the latest version of MAGPHYS (da Cunha et al. 2008)" (5.5 Star Formation Rate, Stellar mass, Dust properties and Size)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean photometric redshift | 1.99 | 0.27 (standard deviation) | dimensionless | 3 | with a mean photometric redshift of <zphot>=1.99±0.27 |
| Mean magnification | 2.16 | 0.44 | dimensionless | 4 | mean magnification factor of our sources (µ= 2.16 ±0.44) |
| Mean dust temperature | 42 | 8 (standard deviation) | K | 4 | T _dust_ =42±8 K (error bars are from the standard deviation) |
| Mean dust attenuation Av | 2.8 | 0.55 | mag | 4 | average value of <Aν>=2.8±0.55 mag |
| Dust mass range | 8.1 < log Mdust < 8.8 | not stated | log Msun | 4 | Their dust masses lie in the range 8.1< log[Mdust/M⊙] <8.8, with an average value of ≈8.3. |
| Recalibrated OIRTC accuracy and completeness | 30% and 80% | not stated | percent | 0 | 10 ALMA-detected DSFGs are selected among 28 total field galaxies, yielding a formal accuracy (30%) and completeness (80%). |

## Qualitative findings

- Herschel FIR photometry deblended with ALMA priors differs strongly from Rawle et al. (2016) because most of the SPIRE flux is associated with the ALMA sources.  
  > "We caution that our photometry differs from that presented in Rawle et al. (2016), mainly due to the different approaches taken." (4.4 Herschel Space Observatory)
- Dust emission is more compact than the HST stellar light for seven of 12 sources.  
  > "This trend holds true for seven of the 12 ALMA-FFs DSFGs (Fig. 8), while the remaining five have comparable sizes." (5.5 Star Formation Rate, Stellar mass, Dust properties and Size)

## Claim tuples

- H: Do the ALMA-FF sources have robust NIR counterparts and are they red? | E: Counterpart search in HST F160W within a 2×beam radius. | R: Clear counterparts for all but one source; eight of 11 have F814W-Ks ≳ 4. | F: Sources are red DSFG-like objects. | **supported**
- H: Does the SED-fitting methodology yield reliable photo-z? | E: Compared photo-z with GLASS spec-z for five objects. | R: Mean z=1.99±0.27 and broad agreement with GLASS, though A2744-ID02 is inconsistent from the NIR-SED. | F: Methodology validated. | **partially**
- H: Are the ALMA-FF sources massive, dusty, star-forming galaxies similar to earlier ALMA samples? | E: MAGPHYS fits compared to ALESS, ASPECS, HUDF. | R: 10.0<log M*<11.5, 0.9<log SFR<2.0, 8.1<log Mdust<8.8. | F: Consistent with previous ALMA surveys. | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: 1.1 mm priors limit misidentification of blended FIR counterparts  
  > "we carefully estimate the far-infrared (FIR) photometry using 1.1 mm priors to limit the misidentification of blended FIR counterparts" (abstract)
- How they decided it was enough: _not stated_
- Limitation (authors): Four sources could not be fitted properly in the FIR due to few constraints.  
  > "Four objects could not be fitted properly due the small number of constraints in the FIR" (5.1 Photometric redshifts)
- Caveat (inferred, ours): Small sample of 12 sources limits statistics
- Caveat (inferred, ours): Photo-z depend on template choice and upper-limit treatment
- Caveat (inferred, ours): Herschel deblending degeneracies remain

## Reproducibility

- Data public (paper): HST data from MAST and public Herschel/Spitzer archives; ALMA project code given  
  > "were retrieved from the STScI Mikulski Archive for Space Telescopes (MAST)" (2. Multi-wavelength Data)
- Products in archive: _not stated_
- Missing: ALMA flux and position catalog (González-López et al. 2017)
- Missing: MAGPHYS and Hyperz configuration
- Missing: Herschel MCMC code
- Missing: Zheng et al. M1149 IRAC reduction (in prep.)
- Data volume (inferred): ~100 GB (ALMA plus HST, Spitzer and Herschel images)
- Score (inferred): 3/5, Multi-instrument photometry with public data, but ALMA inputs come from a companion paper and many fitting settings are not given.
- Rediscovery candidate: no, Depends on companion-paper ALMA catalog, heterogeneous non-ALMA data and unspecified SED-fitting configurations.

## Links

- Method: González-López et al. (2017) (ALMA-FF data reduction and source catalog)
- Companion: González-López et al. (2017) (Paper I of the ALMA Frontier Fields survey)
- Related: Frontier Fields
- Related: GLASS
- Related: Herschel Lensing Survey
- Related: AstroDeep
- Related: ALESS
- Related: ASPECS
- Related: HUDF Band 6 survey

## Checks

```json
{
 "quotes": 48,
 "quotes_ok": 48,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 85,
  "stated": 37,
  "rate": 0.435
 },
 "evidence_ok": true
}
```

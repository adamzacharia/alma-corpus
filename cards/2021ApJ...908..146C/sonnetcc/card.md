# ALMA Lensing Cluster Survey: An ALMA Galaxy Signposting a MUSE Galaxy Group at z = 4.3 Behind "El Gordo"

`2021ApJ...908..146C` | The Astrophysical Journal 2021 | first author: Caputi, K. I. | arXiv: 2009.04838 | DOI: 10.3847/1538-4357/abd4d0

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: Is the ALMA 1.2 mm source behind El Gordo part of the lensed MUSE galaxy group at z=4.32, and what are the star formation properties of the group galaxies and the ALMA source  
  > "This reported case of an ALMA/MUSE group association suggests that some presumably isolated ALMA sources are in fact signposts of richer star-forming environments at high redshifts." (abstract)
- Target **El Gordo (ACT-CL J0102-4915) lensing cluster**: coordinates _not stated_; z/distance z = 0.87  
  > "the massive galaxy cluster ACT-CL J0102-4915 (aka *El Gordo*) at $z=0.87$" (Datasets); distance from _not stated_
- Target **Lensed ALMA source (ALMA-a, -b, -c) and MUSE galaxy group at z=4.32**: coordinates Table 1 lists RA, DEC in decimal degrees; ALMA-a 15.7320058, -49.2525287  
  > "Its lensing-derived redshift is $z_{lens}=4.32^{+0.08}_{-0.06}$" (3.1 System description); "The ALMA source redshift can be obtained through the lensing model analysis (cite: cam21)." (3.1 System description); "The coordinates and properties of all these sources are listed in Table [1](#tab:sumtab)." (3.1 System description); z/distance z_lens = 4.32 +0.08/-0.06 (ALMA source); MUSE group z_spec = 4.32-4.33  
  > "Its lensing-derived redshift is $z_{lens}=4.32^{+0.08}_{-0.06}$" (3.1 System description); "The ALMA source redshift can be obtained through the lensing model analysis (cite: cam21)." (3.1 System description); "The coordinates and properties of all these sources are listed in Table [1](#tab:sumtab)." (3.1 System description); distance from Lensing model of Caminha et al. 2021 (cam21) for the ALMA source; MUSE spectroscopy for the group galaxies  
  > "Its lensing-derived redshift is $z_{lens}=4.32^{+0.08}_{-0.06}$" (3.1 System description); "The ALMA source redshift can be obtained through the lensing model analysis (cite: cam21)." (3.1 System description); "The coordinates and properties of all these sources are listed in Table [1](#tab:sumtab)." (3.1 System description)

## Data provenance

- ALMA projects: 2018.1.00035.L
- bands: Band 6 (1.1-1.4 mm); source measured at 1.2 mm  
  > "The ALMA Band-6 (1.1-1.4 mm) data for" (Datasets)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: synthesized beam (FWHM) 1.17'' x 0.91''  
  > "The natural-weighted continuum map achieves a sensitivity of 71.9 $\rm \mu Jy$/beam and a synthesized beam size (FWHM) of $1.17'' \times 0.91''$." (Datasets)
- max recoverable scale: _not stated_
- sensitivity: 71.9 uJy/beam (natural-weighted continuum map)  
  > "The natural-weighted continuum map achieves a sensitivity of 71.9 $\rm \mu Jy$/beam and a synthesized beam size (FWHM) of $1.17'' \times 0.91''$." (Datasets)
- time on source: _not stated_
- observing dates: ALMA cycles 6 and 7  
  > "using CASA versions 5.4.0 and 5.6.1 for cycles 6 and 7 data, respectively, following the standard pipeline." (Datasets)
- pi or archival as stated: ALMA Lensing Cluster Survey Large Programme, P.I. K. Kohno  
  > "Large Programme (ID 2018.1.00035.L; P.I. K. Kohno)" (Datasets)
- Other facility **VLT/MUSE**: Public MUSE cube of El Gordo (ESO programme 0102.A-0266), used for spectroscopic redshifts of the group galaxies  
  > "The MUSE data on ACT-CL J0102-4915 was taken under the ESO programme ID 0102.A-0266 (P.I. G. B. Caminha) and have a final depth of" (Datasets)
- Other facility **HST**: Broad-band photometry (11 bands) for SED fitting of the MUSE sources  
  > "Also based on observations carried out by NASA/ESA" (Acknowledgments)
- Other facility **Spitzer/IRAC**: 3.6 and 4.5 micron detections of the ALMA source, used for its stellar mass  
  > "At wavelengths tracing the stellar emission, the ALMA source is only detected in the IRAC 3.6 and 4.5 $\rm \mu m$ bands." (3.2.2 The lensed ALMA source)
- Other facility **Herschel/SPIRE**: 250, 350, 500 micron flux densities of the ALMA source for MAGPHYS SED fitting  
  > "at a relatively shallow depth ($\mathrm{r.m.s.}=11.8$ mJy/beam at 250 $\mu$m)" (Datasets); "We extracted the SPIRE flux densities of the ALCS sources using an iterative point-spread-function fitting algorithm based on ALMA positional priors (Sun et al., in prep.)." (Datasets)
- External data: Lensing model: magnifications, ALMA source redshift, source-plane distances  
  > "The lensing model used in this paper, which is based on a large number of spectroscopically confirmed multiple images, will be presented in a companion paper (cite: cam21)." (3.1 System description) [from Caminha et al. 2021 (cite: cam21)]
- External data: Star-formation main sequence and starburst locus used as reference in the SFR versus stellar mass plane  
  > "For reference, we also show the location of the star formation main sequence as well as starburst galaxies, as derived in previous works" (3.2.1 The lensed MUSE sources) [from (cite: spe14; cap17; san17)]
- External data: Earlier ALMA detection of the three components as three different sources  
  > "have also been detected in an earlier ALMA programme (P.I. A. Baker) and reported as three different sources (Wu et al. 2018)" (Datasets) [from Wu et al. 2018 (cite: wu18)]

## Processing

### Calibration

- pipeline or manual: standard pipeline with scripts provided by the ALMA observatory  
  > "The data have been reduced with the scripts provided by the ALMA observatory, using CASA versions 5.4.0 and 5.6.1 for cycles 6 and 7 data, respectively, following the standard pipeline." (Datasets)
- casa version: CASA 5.4.0 (cycle 6), 5.6.1 (cycle 7)  
  > "using CASA versions 5.4.0 and 5.6.1 for cycles 6 and 7 data, respectively, following the standard pipeline." (Datasets)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The natural-weighted continuum map achieves a sensitivity of 71.9 $\rm \mu Jy$/beam and a synthesized beam size (FWHM) of $1.17'' \times 0.91''$." (Datasets)
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
- final beam: 1.17'' x 0.91''  
  > "The natural-weighted continuum map achieves a sensitivity of 71.9 $\rm \mu Jy$/beam and a synthesized beam size (FWHM) of $1.17'' \times 0.91''$." (Datasets)
- final rms: 71.9 uJy/beam  
  > "The natural-weighted continuum map achieves a sensitivity of 71.9 $\rm \mu Jy$/beam and a synthesized beam size (FWHM) of $1.17'' \times 0.91''$." (Datasets)

### Inherited from earlier work

- ALCS programme description, data reduction and imaging  
  > "The details of the ALCS programme description and the data reduction and imaging are presented in Kohno et al. (in prep.) and Fujimoto et al. (in prep.), respectively." (Datasets) [from Kohno et al. (in prep.); Fujimoto et al. (in prep.)]
- Detailed MUSE data description  
  > "The detailed description of the data will be presented in (cite: cam21)." (Datasets) [from (cite: cam21)]
- Lensing model and magnification corrections  
  > "The lensing model used in this paper, which is based on a large number of spectroscopically confirmed multiple images, will be presented in a companion paper (cite: cam21)." (3.1 System description) [from (cite: cam21)]
- Total infrared luminosity from 1.2 mm flux using empirical submillimetre galaxy templates  
  > "and then we scaled them taking into account empirical sub-millimetre galaxy templates, following the same methodolgy as in (cite: cap14)" (3.2.2 The lensed ALMA source) [from (cite: cap14)]
- Dust temperature estimate  
  > "We also estimated dust temperatures for these sources, following the methodology of (cite: dud20)." (3.2.2 The lensed ALMA source) [from (cite: dud20)]
- SFR from H-alpha excess in IRAC 3.6 micron band  
  > "Following the methodology described in (cite: cap17), we obtained" (3.2.1 The lensed MUSE sources) [from (cite: cap17)]
- Starburst lower-envelope definition in sSFR  
  > "defined by $\rm log_{10} (sSFR(yr^{-1})) \geq -7.60$ (see (cite: cap17))" (3.2.1 The lensed MUSE sources) [from (cite: cap17)]
- SPIRE data reduction pipeline  
  > "The data were reduced with the standard reduction pipeline described in (cite: raw16)." (Datasets) [from (cite: raw16)]
- SPIRE flux extraction with ALMA positional priors  
  > "We extracted the SPIRE flux densities of the ALCS sources using an iterative point-spread-function fitting algorithm based on ALMA positional priors (Sun et al., in prep.)." (Datasets) [from Sun et al. (in prep.)]

### Not stated but needed to reproduce (our reading)

- ALMA imaging parameters (tclean settings, cell, image size, masking, primary-beam correction, mosaic handling) are deferred to Fujimoto et al. in prep.
- How the 1.2 mm flux densities of components a, b, c were measured (aperture or Gaussian fit, deblending)
- ALMA frequency setup, array configurations, time on source and observing dates
- Whether the ALCS ALMA data are public and where the calibrated products can be found
- Lensing model (images, magnification maps, source-plane positions) is in an unpublished companion paper
- LePhare settings: age grid, SFH tau grid, photometric uncertainties, priors, treatment of emission lines
- MUSE redshift measurement procedure and velocity dispersion estimator
- HST and IRAC photometry values and aperture/deblending choices for each source
- SPIRE flux densities actually used and the empirical SMG template set with its normalisation
- MAGPHYS library, priors and fitting setup, and how dust temperature was derived
- ALMA stacking procedure for MUSE sources (apertures, weights, lensing treatment)

## Analysis recipe

1. **Reduce and image ALMA Band 6 continuum, measure 1.2 mm flux densities**: Standard ALMA pipeline scripts; natural-weighted continuum map; total flux densities of components a, b, c  
  > "The data have been reduced with the scripts provided by the ALMA observatory, using CASA versions 5.4.0 and 5.6.1 for cycles 6 and 7 data, respectively, following the standard pipeline." (Datasets); "The total measured ALMA 1.2 mm flux densities are $S_\nu(1.2 \, mm) = 9.50\pm 0.12, 3.83 \pm 0.11$ and $3.29 \pm 0.12$ mJy, in the components a, b and c, respectively" (3.1 System description)
   - software: CASA
   - parameter: natural weighting; sensitivity 71.9 uJy/beam; beam 1.17'' x 0.91''  
  > "The natural-weighted continuum map achieves a sensitivity of 71.9 $\rm \mu Jy$/beam and a synthesized beam size (FWHM) of $1.17'' \times 0.91''$." (Datasets)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure MUSE spectroscopic redshifts and group velocity dispersion**: Redshifts from Lyman-alpha and rest-UV absorption lines in MUSE spectra of the four group members; rest-frame velocity dispersion from their redshifts  
  > "The signal-to-noise (S/N) ratio of the spectra is high enough to enable the detection of rest UV absorption lines" (3.1 System description); "The spectroscopic redshifts of the different MUSE galaxies (ID #1 to #4) allow us to estimate the rest-frame group velocity dispersion." (3.1 System description)
   - software: MUSE reduction pipeline 2.6
   - fitting: _not stated_
   - validation: _not stated_
3. **Obtain ALMA source redshift and magnification from the lensing model**: Lensing model of Caminha et al. 2021 gives z_lens for the ALMA source, magnifications and source-plane separations  
  > "The ALMA source redshift can be obtained through the lensing model analysis (cite: cam21)." (3.1 System description)
   - assumption: cosmology H0=70, Omega_M=0.3, Omega_Lambda=0.7  
  > "Throughout this paper we adopt a cosmology with $\rm H_0=70 \,{\rm km \, s^{-1} Mpc^{-1}}$, $\rm \Omega_M=0.3$ and $\rm \Omega_\Lambda=0.7$." (Introduction)
   - fitting: _not stated_
   - validation: _not stated_
4. **SED fitting of the MUSE sources for stellar masses**: LePhare SED fitting at fixed spectroscopic redshift with exponentially declining SFHs, Z_sun and 0.2 Z_sun, Calzetti reddening with E(B-V)=0 to 1, on HST bands (IRAC for source #3)  
  > "We performed the optical/near-IR spectral energy distribution (SED) fitting of all the MUSE sources of the main group (sources ID #1 to #4) at their fixed spectroscopic redshifts" (3.2.1 The lensed MUSE sources); "To account for dust extinction we convolved the templates with the (cite: cal00) reddening law for different extinction values from $E(B-V)=0$ to $1$." (3.2.1 The lensed MUSE sources)
   - software: LePhare
   - parameter: Bruzual and Charlot (2003) templates  
  > "We considered (cite: bc03) templates corresponding to a single stellar population and different exponentially declining star formation histories" (3.2.1 The lensed MUSE sources)
   - assumption: Chabrier IMF for stellar masses and SFRs  
  > "Stellar masses and SFRs refer to a (cite: cha03) initial mass function." (Introduction)
   - fitting: _not stated_
   - validation: Fits with both IRAC bands versus only 4.5 micron for source #3 gave consistent results  
  > "and found that the results were consistent" (3.2.1 The lensed MUSE sources)
5. **Derive SFRs of MUSE sources from UV flux and H-alpha excess**: Extinction-corrected rest-frame UV flux (F105W) with the Kennicutt formula; for source #3 also the H-alpha excess in IRAC 3.6 micron  
  > "We also independently derived star formation rates for all our galaxies using their extinction-corrected, rest-frame UV fluxes (based on the F105W filter photometry) and the corresponding (cite: ken98) formula." (3.2.1 The lensed MUSE sources); "For source ID #3, we can independently derive an SFR from the H$\alpha$ excess in the IRAC 3.6$\rm \mu m$ band." (3.2.1 The lensed MUSE sources)
   - fitting: _not stated_
   - validation: _not stated_
6. **Estimate L_TIR and dust-obscured SFR of ALMA source from 1.2 mm flux**: Magnification-corrected 1.2 mm flux densities scaled with empirical submillimetre galaxy templates, then Kennicutt SFR  
  > "and then we scaled them taking into account empirical sub-millimetre galaxy templates, following the same methodolgy as in (cite: cap14)" (3.2.2 The lensed ALMA source)
   - assumption: SFR conversion with Kennicutt (1998) formula, after correction to Chabrier IMF  
  > "The derived SFRs using the (cite: ken98) formula corresponding to infrared luminosities are" (3.2.2 The lensed ALMA source)
   - fitting: _not stated_
   - validation: _not stated_
7. **Independent dust SED fit with MAGPHYS**: MAGPHYS high-z extension fit to ALMA 1.2 mm plus Herschel/SPIRE 250, 350, 500 micron flux densities  
  > "to perform the SED fitting of the ALMA source dust emission using the high-$z$ extension of the code MAGPHYS (cite: dac08)" (3.2.2 The lensed ALMA source)
   - software: MAGPHYS
   - parameter: SPIRE upper limit ~15 mJy (3 sigma) for non-detections  
  > "In the case of non-detections, an upper limit of $\sim 15$ mJy ($3\sigma$) can be placed for their peak far-IR flux density in the SPIRE bands." (3.2.2 The lensed ALMA source)
   - fitting: _not stated_
   - validation: Consistent with the template-based L_TIR estimate  
  > "The output of the MAGPHYS SED fitting is consistent with our first total infrared luminosity estimates for the ALMA source." (3.2.2 The lensed ALMA source)
8. **Estimate dust temperatures of the ALMA source**: Following the methodology of Dudzeviciute et al. 2020  
  > "We also estimated dust temperatures for these sources, following the methodology of (cite: dud20)." (3.2.2 The lensed ALMA source)
   - fitting: _not stated_
   - validation: Compared with the median temperature of submillimetre galaxies of similar L_TIR at z~2.5  
  > "We obtained $T_{\rm dust} \approx 30.1-34.8 \, \rm K$, which is consistent with the median temperature derived by (cite: dud20) for sub-millimetre galaxies" (3.2.2 The lensed ALMA source)
9. **Estimate the stellar mass of the ALMA source**: LePhare SED fit at the lensing redshift using IRAC detections and HST upper limits, for two lensed components  
  > "We fit its SED running LEPHARE at the known fixed redshift to obtain an estimate of its stellar mass for two lensed components" (3.2.2 The lensed ALMA source)
   - software: LePhare
   - fitting: _not stated_
   - validation: Two lensed components give consistent masses, though fits rely on flux upper limits and blended IRAC  
  > "the SED fitting is mostly constrained by flux upper limits and that the IRAC photometry is somewhat blended with that of source ID #4" (3.2.2 The lensed ALMA source)
10. **Stack ALMA data at MUSE source positions**: ALMA stacking of MUSE sources ID 1, 2, 3 in the three lensed components; no signal, giving a limit on average L_TIR  
  > "An ALMA stacking analysis of the MUSE group sources ID \# 1, 2 and 3 in the three lensed components does not result in a signal either" (3.2.1 The lensed MUSE sources)
   - fitting: _not stated_
   - validation: _not stated_
11. **Classify sources on the SFR versus stellar mass plane**: Compare SFR and M* (and sSFR) with the main sequence and the starburst lower envelope log10(sSFR) >= -7.60  
  > "From the location of our galaxies in this diagram we see that sources ID #3 and #4 can be classified as main-sequence galaxies." (3.2.1 The lensed MUSE sources); "defined by $\rm log_{10} (sSFR(yr^{-1})) \geq -7.60$ (see (cite: cap17))" (3.2.1 The lensed MUSE sources)
   - assumption: Main-sequence/starburst division extrapolated linearly below ~10^8 Msun  
  > "Note, however, that we should take this classification with care because the main-sequence/starburst division is not known at stellar masses" (3.2.1 The lensed MUSE sources)
   - fitting: _not stated_
   - validation: H-alpha SFR for source #3 does not change its main-sequence classification  
  > "Interestingly, source ID #3 would still be classified as a main-sequence galaxy considering the SFRs inferred from the H$\alpha$ excess in the IRAC 3.6$\rm \mu m$ band." (3.2.1 The lensed MUSE sources)

## Software

- **CASA** 5.4.0 (cycle 6), 5.6.1 (cycle 7): ALMA data reduction following the standard pipeline  
  > "using CASA versions 5.4.0 and 5.6.1 for cycles 6 and 7 data, respectively, following the standard pipeline." (Datasets)
- **MUSE data reduction pipeline** 2.6: Processing MUSE data into the stacked data cube  
  > "The data was processed using the reduction pipeline version 2.6 (cite: wei14), following all standard corrections and calibrations to create the stacked data-cube." (Datasets)
- **LePhare** : Optical/near-IR SED fitting for stellar masses of MUSE sources and the ALMA source  
  > "For this, we made use of the SED fitting code LEPHARE (cite: arn99; ilb06)." (3.2.1 The lensed MUSE sources)
- **MAGPHYS** high-z extension: Dust SED fitting of ALMA plus SPIRE flux densities  
  > "to perform the SED fitting of the ALMA source dust emission using the high-$z$ extension of the code MAGPHYS (cite: dac08)" (3.2.2 The lensed ALMA source)
- **SExtractor** : _not stated_
- **IRAF** : _not stated_

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA 1.2 mm flux densities (components a, b, c) | 9.50, 3.83, 3.29 | 0.12, 0.11, 0.12 | mJy | 1 | The total measured ALMA 1.2 mm flux densities are $S_\nu(1.2 \, mm) = 9.50\pm 0.12, 3.83 \pm 0.11$ and $3.29 \pm 0.12$ mJy, in the components a, b and c, respectively |
| ALMA natural-weighted continuum sensitivity | 71.9 | not stated | uJy/beam | 1 | The natural-weighted continuum map achieves a sensitivity of 71.9 $\rm \mu Jy$/beam and a synthesized beam size (FWHM) of $1.17'' \times 0.91''$. |
| MUSE group rest-frame velocity dispersion | 300 | 160 | km/s | 2 | We obtained $\sigma_r\approx 300 \pm 160 \, \rm km/s$, which indicates that this is likely an unrelaxed galaxy group |
| Lensing-derived redshift of the ALMA source | 4.32 | +0.08/-0.06 | dimensionless | 3 | Its lensing-derived redshift is $z_{lens}=4.32^{+0.08}_{-0.06}$ |
| Projected distance between ALMA source and MUSE ID #4 (source plane) | 2.07 | 0.88 | kpc | 3 | these sources are at a projected distance of $2.07 \pm 0.88$ kpc in the source plane |
| SFR of MUSE source ID #4 from UV | between ~4.4 and ~23.5 | not stated | Msun/yr | 5 | its value is between $\sim 4.4$ and $\sim 23.5 \, \rm M_\odot/yr$ |
| SFR of sources ID #3a and #3c from H-alpha excess | 28.2 and 4.74 | 7.9 and 1.33 | Msun/yr | 5 | we obtained $(28.2 \pm 7.9)$ and $(4.74\pm1.33) \, \rm M_\odot/yr$ for sources ID #3a and c, respectively |
| L_TIR of ALMA source from template scaling (component c to component b) | 1.23e12 to 2.32e12 | 0.52e12 and 0.95e12 | Lsun | 6 | We obtained total infrared luminosities ranging between $\rm L_{\rm TIR}=(1.23 \pm 0.52)\times 10^{12} \, \rm L_\odot$ (component c) and $(2.32 \pm 0.95)\times 10^{12} \, \rm L_\odot$ (component b). |
| SFR of ALMA source from template L_TIR | 130-250 | 42% | Msun/yr | 6 | The derived SFRs using the (cite: ken98) formula corresponding to infrared luminosities are $\mathrm SFR\approx 130-250 \, \rm M_\odot/yr \, (\pm 42\%)$ |
| L_TIR of ALMA source from MAGPHYS (component c to component b) | 1.86e12 to 2.73e12 | 0.89e12 and 1.07e12 | Lsun | 7 | the values derived with MAGPHYS range between $\rm L_{TIR}=(1.86\pm 0.89)\times 10^{12} \, \rm L_\odot$ (component c) and $(2.73\pm 1.07)\times 10^{12} \, \rm L_\odot$ (component b). |
| Dust-obscured SFR of ALMA source from MAGPHYS L_TIR | ~200-300 | 42% | Msun/yr | 7 | These values correspond to dust-obscured SFRs ranging between $\approx 200$ and $300 \, \rm M_\odot/yr \, (\pm 42\%)$ (after correction to a Chabrier IMF). |
| Dust temperature of ALMA source components | 30.1-34.8 | not stated | K | 8 | We obtained $T_{\rm dust} \approx 30.1-34.8 \, \rm K$, which is consistent with the median temperature derived by (cite: dud20) for sub-millimetre galaxies |
| Lensing-corrected stellar mass of ALMA source | between ~5.8e10 and 7.8e10 | not stated | Msun | 9 | We obtained that the lensing corrected stellar mass of the ALMA source is between $\sim5.8$ and $7.8 \times 10^{10} \, \rm M_\odot$. |
| Upper limit on average L_TIR of stacked MUSE group sources #1, 2, 3 | below a few 1e10 | not stated | Lsun | 10 | indicating that the average total infrared luminosity of these sources must be below a few $\times 10^{10} \, \rm L_\odot$ (after correcting for lensing magnification) |
| Stellar-mass doubling time of MUSE sources ID #1 and #2 | ~2e7 | not stated | yr | 11 | imply that the doubling time for their stellar masses is only $~2\times 10^7$ years |
| Starburst percentage in the galaxy group | 40-50 | not stated | percent | 11 | The presence of two starburst galaxies in this galaxy group with only 4-5 members makes for a starburst percentage of 40-50%. |

## Qualitative findings

- Only the ALMA source associated with MUSE ID #4 is individually detected by ALMA among the group  
  > "None of the MUSE sources at $z=4.32$ is individually detected by ALMA, except for the association between the ALMA source discussed here and source MUSE ID #4." (3.2.1 The lensed MUSE sources)
- MUSE sources ID #3 and #4 are main-sequence galaxies; ID #1 and #2 lie above the starburst division  
  > "From the location of our galaxies in this diagram we see that sources ID #3 and #4 can be classified as main-sequence galaxies." (3.2.1 The lensed MUSE sources)
- The ALMA source is a main-sequence galaxy on the SFR versus M* plane  
  > "As it is clear from this plot, the ALMA source is a main-sequence galaxy." (3.2.2 The lensed ALMA source)

## Claim tuples

- H: The ALMA 1.2 mm source belongs to the same galaxy group at z=4.32 as the MUSE sources | E: Lensing-model redshift of the ALMA source compared with MUSE spectroscopic redshifts and positions across three lensed images | R: z_lens = 4.32 +0.08/-0.06; projected distance to MUSE ID #4 of 2.07 +/- 0.88 kpc | F: The ALMA source is very likely part of the MUSE galaxy group | **supported**
- H: What type of galaxy is the ALMA source | E: Magnification-corrected 1.2 mm flux scaled with SMG templates and fit with MAGPHYS; LePhare stellar mass | R: L_TIR ~1.2-2.7e12 Lsun, dust-obscured SFR ~200-300 Msun/yr, M* ~5.8-7.8e10 Msun | F: The ALMA source is an ordinary ULIRG on the star-formation main sequence | **supported**
- H: Are starbursts common in this compact galaxy group | E: UV-based SFRs and LePhare stellar masses of the four MUSE members placed on the SFR versus M* plane | R: Two of the members (ID #1, #2) lie above the starburst line, with doubling times ~2e7 yr | F: High starburst incidence of 40-50%, likely driven by interactions in a compact group with high velocity dispersion | **partially**
- H: Do isolated-looking ALMA sources signpost richer environments | E: Association of one lensed ALMA source with a MUSE-confirmed galaxy group | R: At least four star-forming galaxies are associated with the ALMA source | F: Some presumably isolated ALMA sources are signposts of richer star-forming environments | **partially**

## Reasoning

- Why this data: Lensing fields give access to fainter high-redshift galaxies than usual  
  > "Lensing fields are excellent systems to study high-redshift galaxies to fainter limits than what is typically possible with current telescopes." (Introduction)
- Why this method: SED fitting of the ALMA source is feasible despite few detections because its redshift is known independently  
  > "However, in our case, we exploit the fact that we have an independent redshift determination for the ALMA source." (3.2.2 The lensed ALMA source)
- Alternative: ALMA source and MUSE ID #4 may be two regions of one galaxy, but they are analysed separately  
  > "Nevertheless, we will analyse these two sources separately throughout this paper" (3.1 System description)
- How they decided it was enough: _not stated_
- Limitation (authors): Main-sequence/starburst classification is uncertain at low stellar masses  
  > "Note, however, that we should take this classification with care because the main-sequence/starburst division is not known at stellar masses" (3.2.1 The lensed MUSE sources)
- Limitation (authors): Velocity-dispersion relaxation status cannot be tested with only four members  
  > "which cannot be determined for our galaxy group with only four members" (3.1 System description)
- Limitation (authors): ALMA source SED fit is constrained mostly by upper limits with blended IRAC photometry  
  > "the SED fitting is mostly constrained by flux upper limits and that the IRAC photometry is somewhat blended with that of source ID #4" (3.2.2 The lensed ALMA source)
- Limitation (authors): Starburst fraction rests on very low statistics  
  > "Although this is based on very low statistics, this percentage is much higher than the overall starburst percentage known among star-forming galaxies at any redshift." (Discussion)
- Caveat (inferred, ours): Stellar mass of ALMA source and of MUSE ID #4 have very large uncertainties (factor of several), so main-sequence placement is weakly constrained
- Caveat (inferred, ours): Dust-obscured SFR relies on unpublished lensing magnifications and SMG templates; no independent check beyond MAGPHYS
- Caveat (inferred, ours): Starburst classification of ID #1 and #2 rests on UV SFRs with extrapolated sequences below 1e8-1e9 Msun
- Caveat (inferred, ours): Group membership of the ALMA source relies on a lensing redshift with 0.07 uncertainty, not a spectroscopic redshift

## Reproducibility

- Data public (paper): MUSE data stated as publicly available; ALMA public status not stated  
  > "Our study is based on the analysis of the publicly available MUSE data for the massive galaxy cluster ACT-CL J0102-4915" (Datasets)
- Products in archive: _not stated_
- Missing: ALMA imaging recipe and flux-extraction method (in prep. papers)
- Missing: Lensing model and magnification maps (unpublished companion)
- Missing: SED fitting configuration for LePhare and MAGPHYS
- Missing: HST/IRAC/SPIRE photometry used
- Data volume (inferred): ALMA Band 6 mosaic for one cluster (ALCS) plus a MUSE cube; roughly tens of GB, plus HST/IRAC/SPIRE images
- Score (inferred): 2/5, MUSE data are public and numerical outputs are given, but ALMA imaging, lensing model and SED fitting setups are deferred to unpublished papers or not specified.
- Rediscovery candidate: no, Key inputs (lensing model, imaging parameters, photometry) are not available in the paper, so the main results cannot be redone from the text.

## Links

- Method: Kohno et al. (in prep.) (ALCS programme description)
- Method: Fujimoto et al. (in prep.) (ALCS data reduction and imaging)
- Method: Caminha et al. 2021 (cite: cam21) (Lensing model and MUSE data description)
- Method: Caputi et al. 2014 (cite: cap14) (Template-based L_TIR from submillimetre flux)
- Method: Caputi et al. 2017 (cite: cap17) (H-alpha excess SFR and starburst definition)
- Method: Dudzeviciute et al. 2020 (cite: dud20) (Dust temperature method)
- Companion: Caminha et al. 2021 (cite: cam21) (Companion paper presenting the lensing model and MUSE data)
- Companion: Wu et al. 2018 (cite: wu18) (Earlier ALMA detection of the three components)
- Related: ALMA Lensing Cluster Survey (ALCS), ALMA Large Programme 2018.1.00035.L
- Related: Herschel Lensing Survey

## Checks

```json
{
 "quotes": 107,
 "quotes_ok": 107,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 16,
 "numeric_problems": 0,
 "fill": {
  "facts": 116,
  "stated": 69,
  "rate": 0.595
 },
 "evidence_ok": true
}
```

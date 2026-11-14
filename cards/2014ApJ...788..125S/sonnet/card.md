# An ALMA Survey of Submillimeter Galaxies in the Extended Chandra Deep Field South: The Redshift Distribution and Evolution of Submillimeter Galaxies

`2014ApJ...788..125S` | The Astrophysical Journal 2014 | first author: Simpson, J. M. | arXiv: 1310.6363 | DOI: 10.1088/0004-637X/788/2/125

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: What is the photometric redshift distribution, stellar mass distribution and evolutionary fate of ALMA-identified 870 um SMGs in the ECDFS?  
  > "we exploit the extensive optical and near–infrared imaging of the ECDFS to derive the photometric redshift distribution, stellar mass distribution, and evolution of the ALMA-LESS (ALESS) SMGs." (Introduction)
- Target **ALESS SMGs in the ECDFS (96 main-catalog sources from 126 LESS sources)**: coordinates Table 3 gives RA/Dec per source (ECDFS, ~03:32, -27:50)  
  > "Our final sample thus consists of 96 SMGs with precise interferometrically-identified positions." (2.1 Sample Selection); z/distance median z_phot = 2.5 +/- 0.2 for the full sample  
  > "Our final sample thus consists of 96 SMGs with precise interferometrically-identified positions." (2.1 Sample Selection); distance from hyperz photometric redshifts from this paper  
  > "Our final sample thus consists of 96 SMGs with precise interferometrically-identified positions." (2.1 Sample Selection)

## Data provenance

- ALMA projects: 2011.0.00294.S
- bands: Band 7 (344 GHz, 870 um)  
  > "The observing frequency was matched to the original LESS survey, 344 GHz (Band 7)" (2.1 Sample Selection)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Cycle 0 compact configuration  
  > "These Cycle 0 observations used the compact configuration, yielding a median synthesized beam of $\sim$ $1.6'' \times 1.2''$." (2.1 Sample Selection)
- baselines: _not stated_
- angular resolution: ~1.6'' x 1.2'' median beam  
  > "yielding a median synthesized beam of $\sim$ $1.6'' \times 1.2''$." (2.1 Sample Selection)
- max recoverable scale: _not stated_
- sensitivity: typical RMS 0.4 mJy/beam  
  > "we reach a typical RMS across our velocity-integrated maps of $0.4$ mJy beam$^{-1}$." (2.1 Sample Selection)
- time on source: 120 s integrations  
  > "we obtained 120s integrations of 122 of the original 126 LESS submm sources" (2.1 Sample Selection)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **MUSYC optical/NIR imaging**: U–K imaging of the ECDFS  
  > "provides $U$–$K$-band imaging (cite: Taylor09) of the entire $0.5 \times 0.5$ degree ECDFS region" (2.2 Optical & NIR Imaging)
- Other facility **Spitzer SIMPLE IRAC**: 3.6, 4.5, 5.8, 8.0 um imaging  
  > "which provides imaging at 3.6, 4.5, 5.8 and 8.0 $\mu$m over the entire field." (2.2 Optical & NIR Imaging)
- Other facility **Herschel/SPIRE (HerMES)**: 250/350/500 um maps for stacking  
  > "In this work we make use of observations at 250, 350 and 500 $\mu$m using the Spectral and Photometric Imaging Receiver" (2.3 Herschel/SPIRE)
- Other facility **VLA 1.4 GHz**: radio fluxes and stacking  
  > "we utilize the VLA 1.4-GHz imaging of the ECDFS." (2.4 VLA/1.4 GHz)
- Other facility **APEX/LABOCA (LESS)**: parent 870 um source list  
  > "This “LESS” survey (cite: Weiss09) detected 126 submm sources with 870– $\mu$m fluxes $S_{870} > 4.4$ mJy" (Introduction)
- External data: ALMA main/supplementary SMG catalog, positions and 870 um fluxes  
  > "we undertake a multi-wavelength analysis of the ALMA detected submm galaxies from the catalog presented by (cite: Hodge13)" (2.1 Sample Selection) [from (cite: Hodge13)]
- External data: Deblended SPIRE fluxes, FIR SFRs, dust-based gas masses  
  > "Deblended 250, 350 and 500 $\mu$m fluxes for each ALESS SMG, along with the FIR-properties, are presented in (cite: Swinbank13)." (2.3 Herschel/SPIRE) [from (cite: Swinbank13)]
- External data: X-ray properties of ALESS SMGs  
  > "To estimate black hole masses for the ALESS SMGs we use their X-ray properties, presented in (cite: Wang13)." (4.6 Black Hole Masses) [from (cite: Wang13)]
- External data: Local elliptical comparison sample (PM2GC)  
  > "taken from the Padova Millennium Galaxy and Group Catalog (PM2GC;  (cite: Calvi11; Calvi13))" (4.4 Evolution of SMGs: z=0) [from (cite: Calvi11; Calvi13)]

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

- ALMA data reduction, source extraction and catalog  
  > "For full details of the data reduction and source extraction we refer the reader to (cite: Hodge13)." (2.1 Sample Selection) [from (cite: Hodge13)]
- Lyman-alpha absorption handling in hyperz  
  > "Finally we follow the same prescription as (cite: Wardlow11) for handling of Lyman–$\alpha$ absorption in hyperz" (3 Photometric redshifts) [from (cite: Wardlow11)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration and imaging settings (all in Hodge et al. 2013)
- Zibetti et al. HAWK-I data are unpublished
- Exact hyperz configuration beyond the listed parameters
- Details of the clipped-mean stacking algorithm and mask choices
- Number of bootstrap realisations

## Analysis recipe

1. **Measure multi-band photometry at ALMA positions**: Align images to ALMA astrometry, PSF-match, 3'' aperture photometry (3.8'' for IRAC) with aperture corrections  
  > "We then measure photometry in a $3''$ diameter aperture using the iraf package apphot." (2.2.1 Photometry)
   - software: SExtractor, IRAF apphot
   - parameter: 3 sigma detection threshold; errors from random blank-sky apertures  
  > "In all of the following analysis, we define detections if the flux is 3 $\sigma$ above the background noise." (2.2.1 Photometry)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive photometric redshifts by SED fitting**: hyperz chi2 fitting of Bruzual & Charlot templates with four SFHs, z=0-7, A_V 0-5, Calzetti law  
  > "We use the spectral templates of (cite: Bruzual03), with solar metalicities, and consider four SFHs; a single burst (B), constant star formation (C) and two exponentially decaying SFHs" (3 Photometric redshifts)
   - software: hyperz
   - parameter: minimum 4 detected bands required  
  > "We therefore can be confident in the reliability of photometric redshifts derived from detections in four photometric bands, and adopt this limit throughout our analysis." (3.2.1 Reliability of SMG redshifts)
   - assumption: Calzetti dust law; galaxy age less than age of Universe  
  > "We also include the constraint that the age of the galaxy must be less than the age of Universe." (3 Photometric redshifts)
   - fitting: minimum chi2; 99% hyperz intervals adopted as 1 sigma errors  
  > "we determine that the Hyperz “99 per cent” confidence intervals provide the best estimate of the redshift error" (3.1 Training sample)
   - validation: Photometric offsets calibrated on 5942 spectroscopic galaxies; compared to 22 ALESS spectroscopic redshifts  
  > "measuring a median $\Delta \,z\,$ / $( 1+z_{\rm spec} ) = 0.011\,\pm \,0.002$" (3.1 Training sample)
3. **Estimate redshifts of the 19 poorly detected SMGs**: Stack in IRAC and SPIRE; assume M_H distribution complete at z<2.5 and assign M_H to place them via selection limits  
  > "we construct $\sim$ $1000$ realizations of the ALESS SMG $H$-band absolute magnitude distribution over the range $z=0$–2.5 and compare this to the $H$-band absolute magnitude at $z>2.5$." (3.2.3 Undetected or Faint Counterparts)
   - assumption: M_H distribution not bimodal; undetected sources lie at z>2.5  
  > "that the 19 SMGs detected in $<4$ wave-bands lie at $z>2.5$ and that the absolute $H$-band magnitude distribution is not bimodal" (3.2.3 Undetected or Faint Counterparts)
   - fitting: _not stated_
   - validation: Herschel stacks show the sources are real  
  > "The SMGs are clearly detected at $> 4\sigma$ in all SPIRE bands in both the 0-or-1- and 2-or-3 subsets" (3.2.3 Undetected or Faint Counterparts)
4. **Stellar masses**: M_H from best-fit SED times M/L_H from burst and constant SFH Bruzual & Charlot models, averaged; Salpeter IMF  
  > "We note that all the stellar masses quoted here are for a Salpeter Initial Mass Function (IMF)" (4.3 Stellar Masses)
   - software: Starburst99
   - assumption: SFH age restricted to 20 Myr–1 Gyr  
  > "We enforce the condition that the age of the star-formation event is $20$ Myr $\le$ $t_{\rm age}$ $\le$ $1$ Gyr." (Footnote 9)
   - fitting: _not stated_
   - validation: Compared to dynamical and gas masses of similar SMGs  
  > "we can crudely test their accuracy by comparing them to the dynamical masses, and CO–derived gas masses, of similar SMGs." (4.3 Stellar Masses)
5. **Fade SMGs to z=0 and compare to local ellipticals**: Fade H-band luminosity with BC03 SSPs for a 100 Myr burst, duty-cycle correct space density, compare with PM2GC  
  > "we calculate the fading in $L_{H}$ between 50 Myr into the burst, and the required age at the present day." (4.4 Evolution of SMGs: z=0)
   - parameter: SMG phase duration 100 Myr; factor-two number count correction for ECDFS under-density  
  > "We also apply a factor of two correction to the number counts to account for the under-density of SMGs in the ECDFS" (4.4 Evolution of SMGs: z=0)
   - assumption: single burst, negligible pre-burst population  
  > "each SMG undergoes only a single burst" (4.4 Evolution of SMGs: z=0)
   - fitting: _not stated_
   - validation: Compared with mass-weighted ages and halo masses of ellipticals  
  > "We now consider two further tests of this evolutionary model. First, we consider the mass-weighted stellar ages of the PM2GC ellipticals" (Discussion, Evolution of SMGs: z=0)

## Software

- **hyperz** : SED fitting for photometric redshifts and SFHs  
  > "we use the SED fitting code hyperz (cite: Bolzonella00)" (3 Photometric redshifts)
- **SExtractor** : source catalogs, astrometric alignment  
  > "We use SExtractor (cite: Bertin96) to create a source catalog for each image" (2.2.1 Photometry)
- **IRAF apphot** : aperture photometry  
  > "using the iraf package apphot" (2.2.1 Photometry)
- **Starburst99** : mass lost to winds and supernovae  
  > "using Starburst99 to determine the mass lost due to winds and supernovae" (4.3 Stellar Masses)
- **EAZY** : cross-check photometric redshifts and emission-line template test  
  > "We also derived photometric redshifts for our training sample using the SED fitting code EAZY (cite: Bramer08)." (Footnote 1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median photometric redshift of 77 SMGs | 2.3 | 0.1 | dimensionless | 2 | deriving a median photometric redshift of $z_{phot}\,=\,2.3\,\pm\,0.1$ |
| Median photometric redshift of full 96 SMGs | 2.5 | 0.2 | dimensionless | 3 | raising the median redshift for SMGs to $z_{phot}\,=\,2.5\,\pm\,0.2$ |
| Fraction of SMGs at z>3 | 35 | 5 | per cent | 3 | $35 \pm 5$ per cent of the ALESS SMGs lie at $z_{phot} > 3$. |
| Median stellar mass | 8e10 | 1e10 | Msun | 4 | median stellar mass for the 96 ALESS SMGs of $M_{\star} = (8 \pm  1) \times 10^{10}$ M$_{\odot}$ |
| Faded median M_H of descendants (100 Myr burst) | -21.2 | 0.2 | mag (AB) | 5 | estimate a median faded absolute $H$–band magnitude of $M_{H} = -21.2 \pm 0.2$ |
| Space density of SMG descendants | 1.4e-3 | 0.4e-3 | Mpc^-3 | 5 | is $\sim$ $(1.4 \pm 0.4) \times 10^{-3}$ Mpc$^{-3}$ |
| Median black hole mass of X-ray detected SMGs | 3e7 | +3/-1 e7 | Msun | 0 | we calculate a median black hole mass of $M_{\rm BH}$ $\sim$ $(3 ^{+3}_{-1}) \times 10^{7}$ M$_{\odot}$ |

## Qualitative findings

- The ALESS redshift distribution declines steadily above z~2.5 rather than plateauing at high z  
  > "the redshift distribution of the ALESS SMGs declines steadily from $z$ $\sim$ $2.5$ and does not plateau at high redshift ($z>3$)" (Summary & Conclusions)

## Claim tuples

- H: The SMG redshift distribution has a large high-z tail | E: Photometric redshifts for ALMA-identified SMGs plus estimates for faint sources | R: Median z=2.5+/-0.2, 35+/-5% at z>3 | F: Proportion of SMG-phase galaxies at z>=3 is at most ~35%, declining at high z | **supported**
- H: SMGs are progenitors of local ellipticals | E: Fade H-band luminosity assuming 100 Myr burst and compare with PM2GC | R: M_H=-21.2 vs -21.1; density 1.4e-3 vs 2.0e-3 Mpc^-3 | F: Consistent with a simple model in which SMGs form most stars in luminous ellipticals | **supported**
- H: ALMA blank maps contain multiple faint SMGs | E: Stack Herschel and ALMA 870 um at 3.6 um sources | R: 0.76+/-0.19 mJy per blank map | F: Faint SMGs exist but do not explain all missing flux | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Stellar masses have systematic uncertainties up to 5x because SFHs are unconstrained  
  > "although there are systematic uncertainties of up to 5 $\times$ for individual sources" (abstract)
- Caveat (inferred, ours): Redshifts for 19 sources rely on a strong assumption about the M_H distribution
- Caveat (inferred, ours): Photometric redshifts for dusty SMGs lack AGN templates
- Caveat (inferred, ours): The descendant test depends on an assumed 100 Myr duration

## Reproducibility

- Data public (paper): All data obtainable from ALMA, ESO, Spitzer and Herschel archives  
  > "All data used in this analysis can be obtained from the ALMA, ESO, *Spitzer* and *Herschel* archives." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Zibetti et al. in prep HAWK-I data
- Missing: Hodge et al. 2013 ALMA catalog needed
- Missing: Exact stacking implementation
- Data volume (inferred): small for ALMA (catalog from Hodge+13); tens of GB for ancillary imaging
- Score (inferred): 3/5, Catalogs and public imaging are usable, but the ALMA part is inherited and several steps are loosely specified.
- Rediscovery candidate: no, Depends on the external ALMA catalog and unpublished data, and the recipe is not fully specified.

## Links

- Method: (cite: Hodge13) (ALMA data reduction and source catalog)
- Method: (cite: Bolzonella00) (hyperz SED fitting code)
- Companion: (cite: Swinbank13) (FIR properties of ALESS SMGs)
- Companion: (cite: Karim13) (ALESS number counts)
- Companion: (cite: Wang13) (X-ray properties)
- Related: LESS
- Related: ALESS
- Related: MUSYC
- Related: HerMES
- Related: SIMPLE
- Related: TENIS
- Related: PM2GC

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 83,
  "stated": 45,
  "rate": 0.542
 },
 "evidence_ok": true
}
```

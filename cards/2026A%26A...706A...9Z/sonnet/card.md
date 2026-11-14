# JWST reveals extended stellar disks for ALMA-bright dusty star-forming galaxies in the Spiderweb protocluster

`2026A&A...706A...9Z` | Astronomy and Astrophysics 2026 | first author: Zhang, Y. H. | arXiv: 2512.07050 | DOI: 10.1051/0004-6361/202556611

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies, galaxy_clusters_and_sz
- Question: What are the stellar morphologies, sizes and size-wavelength trends of ALMA-detected DSFGs in the Spiderweb protocluster, as seen with JWST/NIRCam, compared with field DSFGs?  
  > "we utilize newly acquired JWST data (cite: Shimakawa2024b; Perez2024b) to identify ALMA-detected DSFGs and construct the first statistical sample of DSFGs in $z\sim2$ protocluster environments." (Introduction)
- Target **Spiderweb protocluster DSFGs (ASW2DF sources)**: coordinates _not stated_; z/distance z=2.16  
  > "which corresponds to a scale of 0.490 physical Mpc (pMpc) or 1.549 comoving Mpc (cMpc) per arcmin at $z=2.16$." (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2021.1.00435.S
- bands: 1.2 mm  
  > "The ASW$^2$DF is a 1.2 mm ALMA survey covering $\sim$20 arcmin$^2$ across six contiguous fields centered on the Spiderweb galaxy." (2.1 ALMA observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.5''-0.9''  
  > "at a spatial resolution of $0.5\ensuremath{''}-0.9\ensuremath{''}$" (2.1 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: 40.3-57.1 uJy  
  > "the final images reach a sensitivity range of $40.3-57.1\,\mu$Jy at a spatial resolution of $0.5\ensuremath{''}-0.9\ensuremath{''}$." (2.1 ALMA observations)
- time on source: 12.84 hrs  
  > "with a total on-source time of 12.84 hrs" (2.1 ALMA observations)
- observing dates: December 2021 to April 2022, Cycle 8  
  > "The observations were conducted between December 2021 and April 2022 in Cycle 8" (2.1 ALMA observations)
- pi or archival as stated: _not stated_
- Other facility **JWST/NIRCam**: F115W, F182M, F405N, F410M imaging of 3x6 arcmin2 (program 1572)  
  > "covered an area of $3\times6$ arcmin$^2$ using four filters to trace rest-frame $U$, $V$, $J$ band continuum (F115W, F182M, F410M), and Pa$\beta$ emission (F405N)" (2.2 JWST/NIRCam imaging)
- Other facility **HST/WFC3 G141 grism**: Redshift confirmation of ASW2DF.04  
  > "Additional redshift constraints are obtained from our HST/WFC3 G141 grism observations (cite: Koyama2022), which confirm ASW2DF.04 as a protocluster member" (3.1 JWST+ALMA counterparts)
- External data: Stellar masses for five HAE DSFGs from SED modelling  
  > "We obtain stellar masses for five of the nine remaining ALMA-detected sources (ASW2DF.05, 12, 20, 23, 28) from (cite: Perez2023)" (3.4.2 Size-mass relation) [from (cite: Perez2023)]
- External data: Field DSFG JWST size measurements for comparison  
  > "we compile the size measurements at rest-frame near-infrared wavelengths for field DSFGs from the literature (cite: Cheng2022; Cheng2023; Boogaard2024; Price2025; Ren2025)" (3.4.1 Effective radii) [from (cite: Cheng2022; Cheng2023; Boogaard2024; Price2025; Ren2025)]

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

- ALMA observations and source extraction details  
  > "We refer the reader to (cite: Zhang2024) for more details about the observations and source extractions." (2.1 ALMA observations) [from (cite: Zhang2024)]
- JWST data reduction and source selection  
  > "We refer the reader to (cite: Shimakawa2024b) and (cite: Perez2024b) for more details about the data and source selection." (2.2 JWST/NIRCam imaging) [from (cite: Shimakawa2024b; Perez2024b)]
- Slope normalization procedure  
  > "Following the normalization procedure of (cite: Gillman2024), we obtain an even steeper slope of $-1.20\pm0.30$ for our DSFG members." (3.4.3 Size-wavelength relation) [from (cite: Gillman2024)]

### Not stated but needed to reproduce (our reading)

- CASA version and imfit parameters
- Calibration and imaging settings for ALMA (robust, taper, cleaning)
- Exact stellar mass-to-light formula and coefficients
- Galight fitting settings, PSF star selection and priors
- Slope fitting method and normalization details
- SFR conversion calibration from 1.2 mm flux

## Analysis recipe

1. **Cross-match ALMA and JWST sources**: Cross-match catalogs with 0.5'' radius; detection in more than one NIRCam filter  
  > "By cross-matching the ALMA and JWST/NIRCam catalogs with a 0.5$''$ radius, we identified 30 ALMA sources located within the JWST coverage." (3.1 JWST+ALMA counterparts)
   - fitting: _not stated_
   - validation: _not stated_
2. **Non-parametric morphology**: statmorph on 201x201 pixel cutouts; segmentation from F410M at 1.5 sigma via Photutils; keep flag=0 or S/N per pixel >2  
  > "We only retain robust results with a flag equal zero (cite: Rodriguez-Gomez2019), or an S/N per pixel greater than two (cite: Lotz2004)." (3.3 Non-parametric morphologies)
   - software: statmorph, Photutils
   - fitting: _not stated_
   - validation: Consistency with statmorph outputs from Galight  
  > "We confirm the reliability of our results by validating the consistency of `statmorph` outputs across both approaches." (3.4 Parametric morphologies)
3. **Parametric Sersic fits**: Galight single Sersic fits with empirical median-stacked PSF; 1 sigma posterior intervals  
  > "We fit the target galaxy along with any possible nearby companions with single Sérsic model, and mask out other sources within each cutout." (3.4 Parametric morphologies)
   - software: Galight
   - fitting: 1 sigma interval of posterior distribution  
  > "We determine the uncertainty for each parameter by deriving the 1$\sigma$ interval of the posterior distribution." (3.4 Parametric morphologies)
   - validation: Empirical PSF FWHM within 5% of archival NIRCam PSFs  
  > "while comparable with the empirical PSFs extracted from archival JWST/NIRCam data (cite: Finkelstein2023) within 5% uncertainty" (3.4 Parametric morphologies)
4. **Stellar masses**: SED masses from literature for five; Bell2003 mass-to-light from F115W-F182M colour and F410M luminosity for four, Chabrier IMF  
  > "We therefore estimate their stellar masses using their F115W–F182M colors and F410M-based NIR luminosities, adopting the mass-to-light ratio prescriptions from (cite: Bell2003)" (3.4.2 Size-mass relation)
   - assumption: Chabrier IMF  
  > "correcting for a (cite: Chabrier03) IMF" (3.4.2 Size-mass relation)
   - fitting: _not stated_
   - validation: Compared with SED masses for five sources: mean offset 0.13 dex, scatter 0.17 dex  
  > "with a mean offset of 0.13 dex and a 1$\sigma$ scatter of 0.17 dex" (Appendix D)
5. **Dust sizes from ALMA**: CASA imfit elliptical Gaussian; circularized Re = r_maj*sqrt(q)  
  > "The `imfit` function in CASA was used to model the sources with an elliptical Gaussian profile." (3.4.3 Size-wavelength relation)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : ALMA data reduction and imfit size measurements  
  > "The `imfit` function in CASA was used to model the sources with an elliptical Gaussian profile." (3.4.3 Size-wavelength relation)
- **statmorph** : Non-parametric morphology  
  > "The non-parametric morphological analysis are performed by the code `statmorph`" (3.3 Non-parametric morphologies)
- **Photutils** : Segmentation maps  
  > "The Python package `Photutils` is employed to create a segmentation of each target based on the F410M image" (3.3 Non-parametric morphologies)
- **Galight** : Sersic fitting and PSF construction  
  > "we obtain parametric measurements of the DSFG members using `Galight`" (3.4 Parametric morphologies)
- **SExtractor** : JWST source extraction in dual-image mode  
  > "Sources were extracted using SExtractor in dual-image mode, with a median-stacked detection image." (2.2 JWST/NIRCam imaging)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA sources detected by JWST | 22 of 30 | not stated | sources | 1 | Among these, 22 are detected in more than one NIRCam filters, corresponding to a detection rate of 73%. |
| Median stellar mass of DSFG members | 10.8 | 0.3 | log(M/Msun) | 4 | we estimate the median stellar mass of our DSFG sample to be log$(M/M_{\odot})=10.8\pm0.3$ |
| Size-wavelength slope | -1.20 | 0.30 | dimensionless | 3 | we obtain an even steeper slope of $-1.20\pm0.30$ for our DSFG members |
| Median stellar-to-dust size ratio | 1.5 | 0.7 | dimensionless | 5 | The median stellar-to-dust size ratio for our protocluster members is $1.5\pm0.7$ |
| Merger fraction | 20% (up to 30% with candidate) | not stated | percent | 0 | this yields a merger fraction of 20%, up to 30% when including the potential candidate. |

## Qualitative findings

- DSFG members have larger stellar sizes than coeval field DSFGs and protocluster HAEs at fixed mass  
  > "In summary, our sample exhibits larger sizes than both typical HAEs in protoclusters and field DSFGs at similar redshifts." (3.4.2 Size-mass relation)

## Claim tuples

- H: DSFGs in the Spiderweb protocluster have larger stellar disks than field DSFGs | E: Sersic fits in F115W/F182M/F410M compared with literature field samples | R: Systematically larger Re at similar redshift and mass | F: Accelerated size growth in dense environments | **supported**
- H: Mergers drive star formation in these DSFGs | E: Gini-M20 and visual classification | R: Most are late-type disks; merger fraction 20-30% | F: Secular processes likelier than major mergers | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Small sample from a single protocluster; tentative conclusions  
  > "given the limited sample size and focus on a single protocluster, larger samples across multiple protoclusters are needed to confirm this scenario." (4.1 The origin of extended stellar disks)
- Caveat (inferred, ours): Dust sizes only for six of nine and measured at 1.2 mm versus 870 um in comparisons
- Caveat (inferred, ours): Slope compared with field samples of differing mass and selection
- Caveat (inferred, ours): Mass-to-light masses for four sources have 0.17 dex scatter

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Reduced JWST images and catalogs from other papers
- Missing: ALMA catalog from Zhang2024
- Missing: Galight/statmorph configuration
- Data volume (inferred): ALMA ~tens of GB; JWST images a few GB
- Score (inferred): 3/5, ALMA role is minor; morphology analysis depends on JWST data and inherited catalogs with limited parameter detail.
- Rediscovery candidate: no, Main results rely on JWST morphology and many unstated settings; ALMA only gives catalogs and dust sizes.

## Links

- Method: (cite: Zhang2024) (ALMA observations and source extraction)
- Method: (cite: Rodriguez-Gomez2019) (statmorph)
- Method: (cite: Ding2020; Ding2021) (Galight)
- Companion: (cite: Shimakawa2024b; Perez2024b) (JWST NIRCam data and source selection)
- Related: ASW2DF

## Checks

```json
{
 "quotes": 40,
 "quotes_ok": 40,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 31,
  "rate": 0.425
 },
 "evidence_ok": true
}
```

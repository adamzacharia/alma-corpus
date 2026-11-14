# The ALPINE-ALMA [CII] survey. Survey strategy, observations, and sample properties of 118 star-forming galaxies at 4 &lt; z &lt; 6

`2020A&A...643A...1L` | Astronomy and Astrophysics 2020 | first author: Le Fèvre, O. | arXiv: 1910.09517 | DOI: 10.1051/0004-6361/201936965

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies
- Question: Survey overview of ALPINE: what are the [CII] and continuum detection rates and the morpho-kinematic mix (rotators, mergers, dispersion-dominated) of 118 normal star-forming galaxies at 4<z<6?  
  > "This paper presents a general overview of the survey, in combination with papers presenting a detailed account of the data processing, [CII] flux and continuum measurements" (1 Introduction)
- Target **ALPINE sample of 118 star-forming galaxies in COSMOS and ECDFS**: coordinates Per-source RA/Dec listed in Table 1  
  > "The sample is drawn from large spectroscopic survey samples of normal SFGs in the COSMOS (cite: Scoville:07a) and ECDFS fields (cite: Giacconi2002)." (2.2 Sample selection); "A key element of the selection is based on galaxies having a reliable spectroscopic redshift in $4.4<z_{spec} <5.9$" (2.2 Sample selection); z/distance 4.4<z_spec<5.9, excluding 4.65<z<5.05  
  > "The sample is drawn from large spectroscopic survey samples of normal SFGs in the COSMOS (cite: Scoville:07a) and ECDFS fields (cite: Giacconi2002)." (2.2 Sample selection); "A key element of the selection is based on galaxies having a reliable spectroscopic redshift in $4.4<z_{spec} <5.9$" (2.2 Sample selection); distance from UV spectroscopic redshifts from VUDS (Le Fevre 2015) and Keck DEIMOS (Hasinger 2018)  
  > "The sample is drawn from large spectroscopic survey samples of normal SFGs in the COSMOS (cite: Scoville:07a) and ECDFS fields (cite: Giacconi2002)." (2.2 Sample selection); "A key element of the selection is based on galaxies having a reliable spectroscopic redshift in $4.4<z_{spec} <5.9$" (2.2 Sample selection)

## Data provenance

- ALMA projects: 2017.1.00428.L
- bands: Band 7  
  > "ALMA observations were carried out in Band-7 starting in May 2018 during Cycle 5 and completed in February 2019 in Cycle 6." (3.1 ALMA)
- frequencies and spectral setup: TDM mode; two spectral windows on the [CII] sideband and two on the other sideband for continuum; resolution 26-35 km/s  
  > "We use the TDM mode of the ALMA correlator, which offers the largest bandwidth to optimize the continuum sensitivity. The resolution varies with redshift from 26 to 35 km/s." (3.1 ALMA); "we placed two additional spectral windows to cover the other side band." (3.1 ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-1 or C43-2  
  > "we elected to use ALMA array configurations (C43-1 or C43-2)" (3.1 ALMA)
- baselines: _not stated_
- angular resolution: minimum minor axis 0.72 arcsec; average beam 0.85"x1.13"  
  > "The minimum achieved minor-axis size of the ALMA beam is 0.72 arcsec and the average beam size is 0.85"$\times$1.13"." (3.1 ALMA)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 69 hours total including calibration and overheads; about 30 min to 1 hr per target  
  > "Each target was observed for about 30 minutes and up to one hour of integration time" (3.1 ALMA)
- observing dates: May 2018 (Cycle 5) to February 2019 (Cycle 6)  
  > "ALMA observations were carried out in Band-7 starting in May 2018 during Cycle 5 and completed in February 2019 in Cycle 6." (3.1 ALMA)
- pi or archival as stated: _not stated_
- Line: [CII] 158 um (not stated)
- Other facility **HST ACS F814W / WFC3 F160W**: Rest-frame UV imaging for comparison with [CII] and classification  
  > "the HST F814W i-band imaging provides a sharper look with a PSF$\sim$0.1 arcsec" (3.2 Ancillary data)
- Other facility **VLT VUDS and Keck DEIMOS**: Spectroscopic redshifts of the sample  
  > "Accurate redshifts come from extensive spectroscopic campaigns at the VLT (cite: LeFevre:15) and Keck (cite: Hasinger2018)." (2.2 Sample selection)
- Other facility **Spitzer, UltraVista, Subaru, XMM, Chandra, radio, CANDELS**: Multiwavelength ancillary data for SED fitting  
  > "SPITZER 3.6 and 4.5 $\mu$m imaging (cite: Sanders:2007)" (3.2 Ancillary data)
- External data: Ancillary multiwavelength photometry catalog (COSMOS)  
  > "A source catalog with matched photometry is available as described in (cite: Laigle2016)." (3.2 Ancillary data) [from Laigle et al. 2016 (cite: Laigle2016)]
- External data: SED-derived stellar mass, SFR, dust extinction  
  > "The derivation of key physical quantities from the SED fitting, including stellar mass, SFR, dust extinction, is described in detail in (cite: Faisst:19)." (3.2 Ancillary data) [from Faisst et al. 2019 (cite: Faisst:19)]
- External data: L[CII]-SFR relation used to set selection limit  
  > "Assuming the (cite: DeLooze2014) relation, this SFR limit is equivalent to $L_{[CII]} > 1.2\times10^8 L_{\odot}$." (2.2 Sample selection) [from De Looze et al. 2014 (cite: DeLooze2014)]

## Processing

### Calibration

- pipeline or manual: Customized pipelines based on CASA tools  
  > "following the best practice with customized pipelines based on the Common Astronomy Software Applications (CASA) tools (cite: McMullin2007)." (3.1 ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN algorithm; immoments for flux maps  
  > "are produced using the CLEAN algorithm and the  `i`mmoments routine" (5 [CII] flux maps)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Flux maps collapse channels [f_cen - FWHM; f_cen + FWHM] using an iterative line profile determination  
  > "optimally extracted using an iterative process to determine the line profile of the source and then collapse channels \[$f_{cen} - FWHM$; $f_{cen} + FWHM$\]" (5 [CII] flux maps)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Data processing, observation description, line flux and continuum measurements, detection threshold validation  
  > "pointing to (cite: Bethermin:20) for an extensive description of observations and data processing" (3.1 ALMA) [from Bethermin et al. 2020 (cite: Bethermin:20)]
- Ancillary data, SED fitting and physical parameters  
  > "as is extensively described in (cite: Faisst:19)" (3.2 Ancillary data) [from Faisst et al. 2019 (cite: Faisst:19)]

### Not stated but needed to reproduce (our reading)

- Imaging weighting/robust, cell and image size, and deconvolution settings (deferred to Bethermin+20)
- Continuum subtraction and line-free channels
- Flux calibrators and flux scale uncertainty
- CASA version
- Exact spectral window frequencies and per-source integration times
- Visual classification inputs (individual votes) are not provided

## Analysis recipe

1. **Select sample**: UV-selected galaxies with spectroscopic z in 4.4-5.9 (excluding 4.65-5.05), L_UV>0.6L*, no type I AGN; 118 selected  
  > "Galaxies are UV-selected (cite: LeFevre:15) with $L_{UV} >0.6L^*$ to include most of the star formation traced by the UV" (2.2 Sample selection)
   - assumption: De Looze 2014 relation for predicted L[CII]; flat LCDM H0=70, Om=0.3  
  > "we use a $\Lambda$CDM cosmology with $H_0=70$ km/s/Mpc, $\Omega_{\Lambda}=0.70$, $\Omega_m=0.30$." (1 Introduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Detect [CII] and continuum**: Search for S/N peaks close spatially and spectrally to candidates; threshold 3.5 sigma (95% reliability from simulations)  
  > "This is the threshold at which our simulation indicates a 95% reliability." (3.1 ALMA)
   - software: CASA
   - parameter: detection threshold S/N>3.5  
  > "when detected above $3.5\sigma$" (3.1 ALMA)
   - fitting: _not stated_
   - validation: Validation simulations described in Bethermin+20  
  > "where the data analysis process and the validation simulations are described" (3.1 ALMA)
3. **Make [CII] flux maps**: CLEAN images, immoments collapse of channels within +-FWHM of line centre; compare with HST F814W  
  > "These flux maps are compared to HST i-band F814W images" (5 [CII] flux maps)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
4. **Morpho-kinematic classification**: Eight team members independently classified each object (classes 1-5) from flux map, 25 km/s channel maps, moment 1, PV diagrams, spectrum and ancillary images; mode taken, then two people proposed a class, then a final consensus round  
  > "visually inspected, independently, by eight people in the team, each assigning a class to each ALPINE object." (6 Morpho-Kinematic classification)
   - fitting: _not stated_
   - validation: Iterative disagreement rounds; class fractions compared for S/N>5 subset  
  > "One last iteration was then performed, with individual team members asked to identify the objects for which they were in most disagreement with" (6 Morpho-Kinematic classification)

## Software

- **CASA** : Customized data processing pipelines, imaging  
  > "customized pipelines based on the Common Astronomy Software Applications (CASA) tools (cite: McMullin2007)" (3.1 ALMA)
- **immoments** : Collapsing channels into [CII] flux maps  
  > "the  `i`mmoments routine" (5 [CII] flux maps)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [CII] detections (S/N>3.5) | 75 of 118 (64%) | not stated | galaxies | 2 | ALPINE detected \[CII\] in 75 galaxies out of 118, hence a success rate of 64 % (40 % for S/N$>$5) |
| Continuum detections (S/N>3.5) | 25 galaxies (21%) | not stated | galaxies | 2 | 25 galaxies, or 21% (9 % for S/N$>$5), are detected with S/N$>$3.5 |
| Median [CII] S/N of detections | 6.2 | not stated | dimensionless | 2 | The median S/N is $\simeq6.2$ for the detected objects. |
| Class fractions | 13.3% rotators, 40% mergers, 20% extended dispersion-dominated, 10.7% compact, 16% unclassifiable | not stated | percent | 4 | We find 13.3% rotating discs in class 1, 40% of galaxies in the merger class 2, 20% in the extended and dispersion dominated class 3, 10.7% compact in class 4 |
| [CII]-UV positional offset dispersion | 0.18 arcsec for 90% of sources | not stated | arcsec | 0 | well represented by Gaussians centered at zero offset with a sigma of about 0.18" |

## Qualitative findings

- About two thirds of sources are resolved in [CII], with a large diversity of morphologies  
  > "about two thirds of the sources are resolved in \[CII\]" (5 [CII] flux maps)

## Claim tuples

- H: Can normal z~4-6 star-forming galaxies be detected in [CII] and continuum at high success rates with short ALMA exposures? | E: Band 7 observations of 118 spectroscopically confirmed galaxies | R: 64% [CII] and 21% continuum detection at >3.5 sigma | F: High detection rate achieved | **supported**
- H: What is the kinematic mix of normal galaxies at z~4.7? | E: Visual morpho-kinematic classification by eight classifiers | R: 40% mergers, 13.3% rotators, 20% extended dispersion-dominated, 10.7% compact | F: Merging is a dominant process for normal SFGs at this epoch | **partially**

## Reasoning

- Why this data: Spectroscopic redshifts needed because the Band 7 bandpass is narrow (~3000 km/s)  
  > "the velocity width of one ALMA bandpass in band-7 is as narrow as $\sim$3000 km/s per sideband." (3.1 ALMA)
- Why this method: Prioritized detection over spatial resolution with compact configurations  
  > "We prioritized detection over spatial resolution" (3.1 ALMA)
- How they decided it was enough: _not stated_
- Limitation (authors): Low resolution may underestimate the number of mergers; classification depends on S/N and line width  
  > "which suggests that our relatively low resolution survey may underestimate the true number of mergers." (6 Morpho-Kinematic classification)
- Caveat (inferred, ours): Visual classification is subjective and not validated with simulations or quantitative kinematic fits
- Caveat (inferred, ours): Beam of ~0.85-1.1 arcsec limits distinguishing mergers from clumpy or dispersion-dominated systems
- Caveat (inferred, ours): Classification is subject to S/N and line-width biases

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Full processing and imaging parameters (in Bethermin+20)
- Missing: Individual classifier votes
- Missing: Complete ALPINE catalogue values beyond Table 1 (detections and fluxes)
- Data volume (inferred): Large (~hundreds of GB raw for 69 h of Band 7 data across 118 targets)
- Score (inferred): 3/5, Detection counts and class fractions are in the paper, but processing details are in a companion paper and the classification is subjective.
- Rediscovery candidate: no, The main result relies on a visual team classification, and imaging details are deferred to a companion paper; public data status is not stated.

## Links

- Method: Bethermin et al. 2020 (cite: Bethermin:20) (Data processing, line and continuum measurements, validation simulations)
- Method: Faisst et al. 2019 (cite: Faisst:19) (Ancillary data and SED fitting)
- Companion: Cassata et al. 2020 (cite: Cassata:20) (Velocity differences between UV and [CII] redshifts)
- Companion: Ginolfi et al. 2019 (cite: Ginolfi2019) (Feedback and outflows from [CII] profiles)
- Companion: Jones et al. 2019 (cite: Jones2019) (Merger timescales)
- Related: Capak et al. 2015 pilot [CII] sample
- Related: VUDS
- Related: DEIMOS COSMOS
- Related: CANDELS
- Related: COSMOS

## Checks

```json
{
 "quotes": 49,
 "quotes_ok": 49,
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
  "facts": 69,
  "stated": 35,
  "rate": 0.507
 },
 "evidence_ok": true
}
```

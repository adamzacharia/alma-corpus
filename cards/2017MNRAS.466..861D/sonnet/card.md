# A deep ALMA image of the Hubble Ultra Deep Field

`2017MNRAS.466..861D` | Monthly Notices of the Royal Astronomical Society 2017 | first author: Dunlop, J. S. | arXiv: 1606.00227 | DOI: 10.1093/mnras/stw3088

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the properties of the galaxies detected in a deep 1.3-mm ALMA mosaic of the HUDF, and what do they imply for the star-forming main sequence, obscured vs unobscured star formation, and the cosmic SFR density?  
  > "The aim of the work presented here was to exploit this unique database by using ALMA to construct the deepest homogeneous mm-wavelength image obtained to date on the relevant scales." (1 Introduction)
- Target **Hubble Ultra Deep Field (HUDF)**: coordinates RA 03h, Dec -28deg (GOODS-South); 45-pointing mosaic over ~4.5 arcmin^2  
  > "lying within the GOODS-South field at RA 03$^h$, Dec $-$28$^{\circ}$, is ideally located for deep ALMA observations." (1 Introduction); z/distance detected sources <z> = 2.15  
  > "lying within the GOODS-South field at RA 03$^h$, Dec $-$28$^{\circ}$, is ideally located for deep ALMA observations." (1 Introduction); distance from spectroscopic (13) and photometric (3) redshifts  
  > "lying within the GOODS-South field at RA 03$^h$, Dec $-$28$^{\circ}$, is ideally located for deep ALMA observations." (1 Introduction)

## Data provenance

- ALMA projects: 2012.1.00173.S
- bands: 1.3 mm continuum  
  > "we have obtained a homogeneous 1.3-mm image reaching $\sigma_{1.3}~\simeq~35$ ${\rm \mu Jy}$, at a resolution of $\simeq~0.7$ arcsec." (abstract)
- frequencies and spectral setup: four 1875 MHz spectral windows, 128 channels each, 7.5 GHz total  
  > "the correlator was configured to process the maximum 7.5-GHz bandwidth in the form of four 1875 MHz-wide spectral windows, each with 128 dual-polarization channels." (2.1 ALMA observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: 13 EBs, maximum baselines 550-1250 m  
  > "2014 Aug 18    |         1250         |   1.51" (Table 1)
- baselines: _not stated_
- angular resolution: 707x672 mas after taper  
  > "produced a beam close to that requested ($707 \times 672$ mas$^2$)" (2.1 ALMA observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: 34 uJy/beam over central area  
  > "a final mosaic sensitivity as measured over a large central area of the map of 34 $\mu$Jy beam$^{-1}$." (2.1 ALMA observations and data reduction)
- time on source: ~20 hr approved  
  > "$\simeq 20$ hr of ALMA observations were approved in Cycle 1, and rolled over into Cycle 2" (1 Introduction)
- observing dates: July-Sep 2014 (9 EBs) and May 2015 (4 EBs)  
  > "the first nine Execution Blocks (EBs) in July to September of 2014 and the remaining four in May 2015." (2.1 ALMA observations and data reduction)
- pi or archival as stated: _not stated_
- Other facility **HST WFC3/IR and ACS**: deep optical/NIR imaging, counterparts, photometry  
  > "the final UDF12 WFC3/IR imaging reaches a 5-$\sigma$ detection depth of $29.7$ mag in the $Y_{105}$ filter" (2.2.1 Optical/near-infrared imaging)
- Other facility **JVLA 6 GHz**: ultra-deep radio imaging, confirmation of 12 sources and astrometry  
  > "reveals 27 radio sources with peak S/N $>$ 5 within the 4.5 arcmin$^{2}$ area of the HUDF" (2.2.3 Radio imaging)
- Other facility **Herschel and Spitzer**: FIR photometry for SED fitting  
  > "we ultilise here the final public image products from three major guaranteed-time surveys." (2.2.2 Mid/far-infrared/sub-mm imaging)
- Other facility **MUSE**: spectroscopic redshifts for 6 of 16 sources  
  > "This yielded spectroscopic redshifts for 6 of the 16 sources listed in Table 2" (2.2.5 Optical/near-infrared spectroscopy)
- Other facility **Chandra 4 Ms**: X-ray AGN identification  
  > "The deepest X-ray imaging in the HUDF is provided by the 4 Msec imaging with *Chandra* of the Chandra Deep Field South" (2.2.4 X-ray imaging)
- External data: 1.1-mm Schechter number-count fit used as input to injection simulations (scaled by 1.65)  
  > "the Schechter-function fits to the 1.1-mm source counts given by Hatsukade et al. (2016)" (5.1 Simulations, completeness, and flux boosting) [from Hatsukade et al. 2016]
- External data: UV luminosity functions for UV SFR density  
  > "we used the latest UV luminosity functions produced by Parsa et al. (2016) and Bouwens et al. (2015)" (8.3 Cosmic star-formation history) [from Parsa et al. 2016; Bouwens et al. 2015]
- External data: Radio 6 GHz fluxes of sources  
  > "Radio flux densities and associated uncertainties are from the new ultra-deep JVLA image of the HUDF region obtained by Rujopakarn et al. (2016)." (Table 3) [from Rujopakarn et al. 2016]

## Processing

### Calibration

- pipeline or manual: CASA, standard procedures  
  > "All data reduction was carried out using CASA and followed standard procedures." (2.1 ALMA observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0334-401  
  > "The flux scale was then set with reference to the regularly-monitored flux density of J0334$-$401" (2.1 ALMA observations and data reduction)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean, mosaic  
  > "A continuum mosaiced image of the calibrated data was produced using the task clean." (2.1 ALMA observations and data reduction)
- deconvolver: no cleaning performed  
  > "no deconvolution (cleaning) was performed." (2.1 ALMA observations and data reduction)
- weighting robust: natural weighting  
  > "The data were naturally weighted for maximum sensitivity" (2.1 ALMA observations and data reduction)
- uv taper: ~220 x 180 klambda  
  > "A $\simeq 220 \times 180\,k\lambda$ taper, with PA oriented to circularize the beam as much as possible" (2.1 ALMA observations and data reduction)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: data averaged to 10 channels per spw and 10 s  
  > "a dataset with 10 frequency channels per spectral window and a time sampling of 10 s." (2.1 ALMA observations and data reduction)
- final beam: 707 x 672 mas^2  
  > "produced a beam close to that requested ($707 \times 672$ mas$^2$)" (2.1 ALMA observations and data reduction)
- final rms: _not stated_

### Inherited from earlier work

- Photometric deconfusion of ground-based and Spitzer data  
  > "both using the method described in McLure et al. (2011, 2013), and independently using TPHOT (Merlin et al. 2015)." (2.2.1 Optical/near-infrared imaging) [from McLure et al. (2011, 2013)]
- Positional uncertainty/search radius formula  
  > "the corresponding conservative 3-$\sigma$ search radius is $\simeq 0.25$ arcsec (see Ivison et al. 2007)" (4.1 Galaxy identifications) [from Ivison et al. 2007]

### Not stated but needed to reproduce (our reading)

- CASA version
- exact clean parameters (cell size, image size, mosaic gridder, phasecenters)
- exact uv taper position angle
- which EB/calibrator flux values were adopted
- photometric redshift codes and SED-fit grids for the 3 photometric sources
- MUSE and JVLA reduced products not publicly specified
- far-IR template normalisation details and deconfusion priors
- stacking method details (weighting, noise estimate, mask of detections)

## Analysis recipe

1. **Image the mosaic**: Naturally weighted, tapered, uncleaned CASA continuum mosaic of 13 EBs  
  > "As this would potentially lead to problems with detecting resolved sources, we experimented with various $u,v$ tapers" (2.1 ALMA observations and data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: 50:50 splits by date, sideband and polarization  
  > "we also constructed three alternative 50:50 splits of the ALMA 1.3-mm image, splitting the data in half by observing date, sideband, and polarization." (2.1 ALMA observations and data reduction)
2. **Extract sources**: Local noise map (10 theta window, 4 sigma clipping), S/N peak finding with PSF subtraction, S/N>3.5  
  > "Within this area we detected 47 candidate sources with peak S/N $>$ 3.5 and a point-source flux-density $S_{1.3}~\ge~120\,{\rm \mu Jy}$." (3 ALMA source extraction)
   - parameter: detection limited to sigma<40 uJy, area 4.4 arcmin^2  
  > "We limited source detection to map regions with $\sigma_{1.3}~<~40\,\mu$Jy, which yielded an effective survey area of 4.4 arcmin$^2$." (3 ALMA source extraction)
   - fitting: _not stated_
   - validation: Same extraction on negative map gave 29 peaks  
  > "running an identical source extraction on the negative map (i.e. the real map multiplied by $-1$) yielded 29 sources" (3 ALMA source extraction)
3. **Clean list via HST counterparts**: Match to HST within 0.6 arcsec, apply 0.25 arcsec southward HST astrometric shift, reject H160>28.5  
  > "adopted a search radius of 0.6 arcsec." (4.1 Galaxy identifications)
   - fitting: _not stated_
   - validation: 12 radio-detected sources retained; negative map gives 3 chance IDs  
  > "yields only 3 random galaxy identifications." (4.1 Galaxy identifications)
4. **Total flux correction**: Fit resolved UDF1-3; multiply UDF4-16 point-source fluxes by 1.25  
  > "simply multiplying their point-source flux densities (and associated errors) by a factor 1.25." (4.3 Final ALMA HUDF source sample)
   - fitting: _not stated_
   - validation: _not stated_
5. **Completeness and flux boosting**: 1000 source injection and retrieval simulations  
  > "The results shown in Fig. 3a were based on 1000 realisations of an HUDF-size image" (5.1 Simulations, completeness, and flux boosting)
   - fitting: _not stated_
   - validation: _not stated_
6. **Stellar masses and SFRs**: BC03 SED fits for M*; UV SFR; FIR SFR from Kirkpatrick et al. template with Murphy et al. 2011 conversion  
  > "converting to SFR using the conversion of Murphy et al. (2011) with a final minor scaling applied to convert from a Kroupa to a Chabrier IMF." (6.3 Star-formation rates)
   - assumption: Chabrier IMF, Calzetti dust law, Madau IGM  
  > "We assumed the IMF of Chabrier (2003)" (6.2 Stellar Masses)
   - fitting: _not stated_
   - validation: Radio-based SFRs as consistency check  
  > "provide reassurance that our far-infrared derived values are not seriously over-estimated." (6.3 Star-formation rates)
7. **Stacking by mass and redshift**: Stack 1.3-mm image on positions of HUDF galaxies in z, M*, M_UV bins  
  > "We therefore explored stacking of galaxy sub-populations selected from a range of bins defined by redshift $z$, stellar mass $M_*$, and UV absolute magnitude $M_{UV}$." (7 Stacking, and the mm background)
   - fitting: _not stated_
   - validation: 6 GHz stack consistent SFR  
  > "reassuringly a stack of the galaxies in this same bin into the JVLA 6-GHz image yielded a detection" (7 Stacking, and the mm background)
8. **Main sequence, obscuration and rho_SFR**: Combine detections and stacks to get SFR-M* relation, obscured/unobscured ratios, and rho_SFR in redshift bins  
  > "dividing by the comoving cosmological volume sampled by the 4.5 arcmin$^2$ of the HUDF in each redshift bin." (8.3 Cosmic star-formation history)
   - fitting: _not stated_
   - validation: Compared with Madau & Dickinson 2014 and Behroozi et al. 2013  
  > "compared with two recently published parametric fits" (8.3 Cosmic star-formation history)

## Software

- **CASA** : calibration and imaging  
  > "All data reduction was carried out using CASA and followed standard procedures." (2.1 ALMA observations and data reduction)
- **SExtractor** v2.8.6: HST detection and photometry  
  > "sextractor v2.8.6 (Bertin & Arnouts 1996) in dual image mode with $H_{160}$ as the detection image" (2.2.1 Optical/near-infrared imaging)
- **TPHOT** : deconfusion of ground-based and Spitzer photometry  
  > "independently using TPHOT (Merlin et al. 2015)" (2.2.1 Optical/near-infrared imaging)
- **esorex** : MUSE data reduction  
  > "We downloaded the public dataset and reduced it using the esorex pipeline." (2.2.5 Optical/near-infrared spectroscopy)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Map rms | 34 | not stated | uJy/beam | 1 | a final mosaic sensitivity as measured over a large central area of the map of 34 $\mu$Jy beam$^{-1}$. |
| Robust ALMA sources | 16 | not stated | sources | 3 | This leaves the final sample of 16 sources |
| Mean redshift | 2.15 | not stated | dimensionless | 6 | The mean redshift of the ALMA HUDF sources is $\langle z \rangle = 2.15$ |
| UDF1 flux density | 924 | 76 | uJy | 4 | 924 $\pm$ 76 |
| Stack mean flux, 9.3<logM<10.3, 1<z<3 | 20.1 | 4.6 | uJy | 7 | $S_{1.3} = 20.1 \pm 4.6\,{\rm \mu Jy}$ |
| Stacked contribution to background | 4.1 | 1.0 | mJy per HUDF | 7 | which adds an additional $4.1 \pm 1.0$ mJy / HUDF |
| Main-sequence sSFR | 2.2 | not stated | Gyr^-1 | 8 | SFR $\propto~M_*^{1.0}$, with sSFR = 2.2 Gyr$^{-1}$ |
| Stacked total/UV SFR ratio at logM=10.7 | 55 | 6 | dimensionless | 8 | is significantly lower, at $55 \pm 6$ |
| Detected high-mass galaxies at z>=2 | 7 of 9 | not stated | galaxies | 6 | only 9 galaxies with $M_* > 2 \times 10^{10}\,{\rm M_{\odot}}$ at $z \geq 2$, and that our ALMA observations have detected 7 of them |

## Qualitative findings

- Astrometry of HST/GOODS-S frame is offset ~0.25 arcsec north relative to ALMA, JVLA and 2MASS  
  > "the agreement between the JVLA, ALMA and 2MASS positions strongly suggests that it is the *HST* co-ordinate system that is wrong." (4.2 Astrometry issues)

## Claim tuples

- H: Is stellar mass the best predictor of SFR at high z? | E: Compare ALMA detections with HUDF galaxies by mass | R: 7 of 9 galaxies with M*>=2e10 at z>=2 detected | F: Stellar mass is the best predictor of SFR | **supported**
- H: Is the z~2 main sequence steep? | E: Detections plus stacks in three mass bins | R: SFR proportional to M* with sSFR 2.2 Gyr^-1 | F: Steep main sequence | **supported**
- H: When does obscured star formation dominate? | E: Sum obscured (ALMA) and UV SFR density | R: rho_SFR peaks at z~2.5; transition at z~4 | F: Universe transits from unobscured to obscured at z~4 | **supported**

## Reasoning

- Why this data: 1.3 mm chosen for sensitivity to z>3 dusty galaxies, less single-dish confusion, feasibility with 45 pointings  
  > "First, in practice it maximises sensitivity to higher redshift dusty star-forming galaxies at $z > 3$." (1 Introduction)
- Why this method: _not stated_
- Alternative: S/N>4 cut rejected because 7 such peaks in negative map; S/N>6 leaves only 5 sources  
  > "A clean source list can be produced by limiting the selection to S/N $>$ 6, but this leaves only 5 sources" (4.1 Galaxy identifications)
- How they decided it was enough: _not stated_
- Limitation (authors): Small field size and cosmic variance; faint sources' total fluxes uncertain  
  > "as the area of sky imaged here is small, and the flux-density range limited." (5.2 Observed and predicted number counts)
- Caveat (inferred, ours): Sample selection requires an HST counterpart, which could bias against optically dark sources
- Caveat (inferred, ours): Uniform 1.25 flux boost for faint sources is ad hoc
- Caveat (inferred, ours): FIR SFRs depend on single SED template and AGN assumption
- Caveat (inferred, ours): Stacking uncertainties and astrometric shift influence results

## Reproducibility

- Data public (paper): ALMA data project 2012.1.00173.S acknowledged; public HST/MUSE/Herschel data used  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00173.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Exact clean/imaging parameters and CASA version
- Missing: Custom source extraction and stacking code
- Missing: Photometric redshift and SED-fit details
- Missing: Catalogues (HST, JVLA) from companion papers
- Data volume (inferred): ~50-100 GB raw for 13 EBs
- Score (inferred): 3/5, Data are public and the main steps are described, but many imaging and analysis parameters are missing and custom code is unreleased.
- Rediscovery candidate: no, The map and detections could be redone, but the main science results need many external datasets and unstated analysis choices.

## Links

- Method: Ivison et al. 2007 (positional accuracy formula)
- Method: Kirkpatrick et al. 2015 (FIR SED template)
- Companion: Rujopakarn et al. 2016 (JVLA 6 GHz HUDF imaging and mm/radio sizes)
- Companion: Ivison et al., in preparation (line detections in UDF3)
- Related: UDF09
- Related: UDF12
- Related: CANDELS
- Related: GOODS-South
- Related: HerMES
- Related: MUSE HUDF

## Checks

```json
{
 "quotes": 68,
 "quotes_ok": 68,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 54,
  "rate": 0.628
 },
 "evidence_ok": true
}
```

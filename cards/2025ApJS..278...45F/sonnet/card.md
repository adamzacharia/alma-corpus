# DUALZ—Deep UNCOVER-ALMA Legacy High-Z Survey

`2025ApJS..278...45F` | The Astrophysical Journal Supplement Series 2025 | first author: Fujimoto, Seiji | arXiv: 2309.07834 | DOI: 10.3847/1538-4365/adc677

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies, galaxy_clusters_and_sz
- Question: Establish a joint ALMA and JWST legacy field in Abell 2744 and, through a blind 1.2-mm survey with NIRCam/NIRSpec counterparts, characterize the faint dust continuum sources, HST-/JWST-dark galaxies, a z=6.33 [CII] emitter, z>9 galaxies, and the infrared luminosity function  
  > "we present the Deep UNCOVER-ALMA Legacy High-$z$ (DUALZ) Survey, specifically designed to establish Abell 2744 (A2744), one of the best-studied massive galaxy lensing clusters, as a joint ALMA and *JWST* legacy field." (Introduction)
- Target **Abell 2744 (A2744)**: coordinates _not stated_; z/distance z=0.308  
  > "Abell 2744 (A2744), at $z=0.308$, is one of the best-studied massive galaxy clusters and is the target of our survey." (2.1 Survey Design); distance from _not stated_

## Data provenance

- ALMA projects: 2022.1.00073.S, 2018.1.00035.L, 2013.1.00999.S, 2023.1.00626.S
- bands: Band 6 (1.2 mm)  
  > "The ALMA Band 6 program of DUALZ was designed to homogeneously map the main UNCOVER $4'\times6'$ field at the 1.2-mm wavelength" (2.1 Survey Design)
- frequencies and spectral setup: 4 frequency setups, 30-GHz-wide spectral scan 244-274 GHz  
  > "Four frequency setups were used to carry out a 30-GHz wide spectral scan from 244 GHz to 274 GHz" (2.1 Survey Design)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C-2 and C-3, 43-45 antennae  
  > "The observations were conducted under the array configurations of C-2 and C-3 with 43-45 antennae" (2.2 Observation and Data)
- baselines: 14-368 m to 15-500 m  
  > "baseline lengths ranging from 14-368 m to 15-500 m" (2.2 Observation and Data)
- angular resolution: 1.02x0.77 arcsec (Wide-natural); 1.81x1.60 (tapered)  
  > "*Wide*-tapered | 43.6 | $1.81\times1.60$" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: 32.7 uJy/beam (Wide-natural); 27.7 (Deep-natural)  
  > "*Wide*-natural | 32.7 | $1.02\times0.77$" (Table 1)
- time on source: total observation time 33.3 hours  
  > "The total observation time was 33.3 hours." (2.2 Observation and Data)
- observing dates: October 2022  
  > "The ALMA Band 6 observations were completed in October 2022." (2.2 Observation and Data)
- pi or archival as stated: New Cycle 9 program (PI S. Fujimoto) plus archival ALMA-HFF and ALCS data  
  > "was accepted in Cycle 9 (#2022.1.00073.S; PI: S. Fujimoto)" (2.1 Survey Design)
- Line: [CII] 158 um (not stated)
- Other facility **JWST/NIRCam (UNCOVER, GLASS, DDT)**: DR2 NIRCam imaging and source catalog for counterparts  
  > "We cross-match our ALMA continuum source catalog with the DR2 NIRCam source catalog presented in (cite: weaver2023)." (3.2 NIRCam Counterparts)
- Other facility **JWST/NIRSpec prism MSA**: spectroscopic redshifts for 17 ALMA sources  
  > "Among the NIRCam counterparts of the ALMA sources, seventeen sources were assigned to the MSA masks." (3.3)
- Other facility **HST**: HFF imaging and photometry  
  > "A2744 has been extensively observed using the *Hubble Space Telescope* (*HST*) as part of the Hubble Frontier Field Survey" (2.1 Survey Design)
- External data: Lens mass model of A2744 for magnifications  
  > "using the lens model presented in (cite: furtak2023a)" (2.3 Survey Area) [from (cite: furtak2023a)]
- External data: NIRCam DR2 source catalog and photometry  
  > "cross-match our ALMA continuum source catalog with the DR2 NIRCam source catalog presented in (cite: weaver2023)" (3.2) [from (cite: weaver2023)]
- External data: SED-fit physical parameter catalog (Prospector) and photo-z  
  > "physical parameter catalog constrained with all available *HST* and *JWST* data in A2744 and the ALMA photometry obtained from the DUALZ survey (cite: bwang2024)" (3.4) [from (cite: bwang2024)]
- External data: Spectroscopic redshift compilation in A2744  
  > "spectroscopic redshift ($z_{\rm spec}$) compilation in A2744 from the literature (cite: fujimoto2023b)" (3.4) [from (cite: fujimoto2023b)]

## Processing

### Calibration

- pipeline or manual: standard pipeline script  
  > "processed and calibrated with the Common Astronomy Software Applications package version 6.4.12 (CASA; (cite: casa2022)) using the standard pipeline script." (2.2)
- casa version: CASA 6.4.12  
  > "Common Astronomy Software Applications package version 6.4.12" (2.2)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: bandpass J2258-2758, J0334-4008; phase J2359-3133 (flux calibrator not stated)  
  > "Bandpass calibrations were performed using J2258-2758 and J0334-4008, while phase calibrations were carried out using J2359-3133." (2.2)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean  
  > "by running the CASA task tclean" (2.2)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "using the natural weighting" (2.2)
- uv taper: 1.5x1.5 arcsec  
  > "To avoid missing any strongly lensed (distorted) objects, we also produced a lower-resolution map and cube by applying a $uv$-taper parameter" (2.2)
- cell size: 0.10 arcsec  
  > "a pixel scale of $0
 \mbox{
  \kern  0.13ex.
  \kern -0.95ex\ensuremath{''}
  \kern -0.1ex
 }
10$" (2.2)
- image size: _not stated_
- masking: automask, noisethreshold=4.25, sidelobethreshold=2.0, minbeamfrac=0.3, lownoisethreshold=1.5, negativethreshold=0.0; cleaned to 2 sigma, max 100,000 iterations  
  > "We adopt noisethreshold=4.25, sidelobethreshold=2.0, minbeamfrac=0.3, lownoisethreshold=1.5, negativethreshold=0.0, following the CASA automasking guide." (footnote 4)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: primary beam limit 0.1; source extraction before PB correction, PB correction applied to fluxes afterwards  
  > "We use the maps before primary beam (PB) correction for source extraction." (3.1)
- array combination: CASA concat of DUALZ with ALMA-HFF and ALCS data within 20 arcsec radius, weights by data depth  
  > "We use CASA task concat, where the weight is applied based on the data depths." (footnote 5)
- smoothing: cubes binned to 50 km/s channels; no CLEAN iteration for cubes  
  > "we used the cube produced without the CLEAN iteration" (2.2)
- final beam: _not stated_
- final rms: 32.7 uJy/beam (Wide-natural)  
  > "*Wide*-natural | 32.7 | $1.02\times0.77$" (Table 1)

### Inherited from earlier work

- Reduction/combination of previous ALMA-HFF and ALCS data  
  > "The previous ALMA data were reduced, calibrated, and combined in the same manner as (cite: fujimoto2023b)." (2.2) [from (cite: fujimoto2023b)]
- ALMA source extraction procedure  
  > "We conduct the ALMA source extraction following the same procedure as (cite: fujimoto2023b)" (3.1) [from (cite: fujimoto2023b)]
- IRLF derivation  
  > "we derive the IRLFs in the same manner as (cite: fujimoto2023b)" (4.5) [from (cite: fujimoto2023b)]
- NIRSpec EAZY redshift fitting  
  > "in the same manner as (cite: fujimoto2023c)" (3.3) [from (cite: fujimoto2023c)]
- CMB effect correction  
  > "We account for the cosmic microwave background (CMB) effect following the recipe presented by (cite: dacunha2013)" (Introduction) [from (cite: dacunha2013)]

### Not stated but needed to reproduce (our reading)

- Flux calibrator and flux-scale uncertainty
- Which channels/spectral windows used for continuum maps
- Cube-based line search method and S/N criteria (only prior-based [CII] search described)
- Details of aperture photometry for the [CII] line optimized extraction
- Final Wide/Deep PB-corrected noise maps and mosaic phase centers
- Full SED fitting and NIRSpec reduction details (deferred to Wang et al. and Price et al. in prep)
- Survey volume computation details for IRLF and completeness
- ALMA continuum imaging uses all channels?; self-calibration not mentioned

## Analysis recipe

1. **Image ALMA mosaics**: tclean on pipeline-calibrated visibilities, natural and uv-tapered, Wide and Deep (concat with ALMA-HFF/ALCS)  
  > "In total, we produced 4 types of ALMA maps (cubes) in DUALZ – *Wide*-natural, *Wide*-tapered, *Deep*-natural, and *Deep*-tapered maps (cubes)." (2.2)
   - software: CASA, tclean, concat
   - parameter: pixel 0.1 arcsec, natural weighting, taper 1.5 arcsec, automask  
  > "using the natural weighting, a pixel scale of $0
 \mbox{
  \kern  0.13ex.
  \kern -0.95ex\ensuremath{''}
  \kern -0.1ex
 }
10$" (2.2)
   - fitting: _not stated_
   - validation: _not stated_
2. **Blind source extraction with purity estimate**: sextractor positive peaks above 2 sigma; negative-peak analysis on inverted maps; SNR thresholds chosen where positives exceed negatives  
  > "thus adopt the SNR thresholds at 5.0 and 4.4 in the *Wide*-natural and -tapered maps, respectively." (3.1 ALMA Source Extraction)
   - software: SExtractor 2.5.0
   - parameter: Deep thresholds 4.8 (natural), 4.2 (tapered); regions down to 20% relative sensitivity  
  > "we set the SNR thresholds at 4.8 and 4.2 for the deep-natural and -tapered maps, respectively." (3.1)
   - fitting: _not stated_
   - validation: purity p=(Npos-Nneg)/Npos > 0.97  
  > "demonstrating the high purity $p>0.97$ of our ALMA sources" (3.1)
3. **Measure 1.2-mm flux densities**: Peak pixel, 1.0'' aperture, or imfit Gaussian; imfit adopted if SNR>10 else best SNR; PB correction afterwards  
  > "If the SNR of the imfit measurement exceeds 10, we adopt the imfit measurement; otherwise, we use the measurement with the best SNR." (3.1)
   - software: CASA imfit
   - fitting: 2D elliptical Gaussian (imfit)  
  > "2D elliptical Gaussian fitting with CASA imfit" (3.1)
   - validation: _not stated_
4. **Identify NIRCam counterparts**: Cross-match with NIRCam DR2 catalog within 1.0'' radius, nearest taken; chance projection probability estimated  
  > "When we identify multiple NIRCam sources within the search radius, we adopt the nearest one as the counterpart." (3.2)
   - fitting: _not stated_
   - validation: Expected ~2.3 chance projections, comparable to negative source count  
  > "we obtain the expected number of chance projections to be $\sim2.3$ among our ALMA sources" (3.2)
5. **Redshifts and physical properties**: Prospector-beta SED fitting (dynesty, parrot) and EAZY; use zspec if available, else zphot; EAZY adopted if estimates differ by >1.0; magnification from Furtak lens model  
  > "In a few cases, the two $z_{\rm phot}$ estimates deviate by more than 1.0, and in such cases, we adopt the $z_{\rm phot}$ estimate from `EAZY`" (3.4)
   - software: Prospector, dynesty, parrot, EAZY, FSPS
   - assumption: AID20 assumed z=2.0; AID60 assumed z=9.0  
  > "For AID60 that lacks a NIRCam counterpart, we assume $z=9.0$" (3.4)
   - fitting: Prospector-beta with nested sampling dynesty; Chabrier IMF, 7-bin SFH, two-component dust  
  > "A sampling of the posterior space is performed using the nested sampler `dynesty`" (3.4)
   - validation: all 27 spec-z sources have |dz|/(1+z)<0.15; outlier fraction zero  
  > "all 27 sources fall in the range of $|z_{\rm spec}-z_{\rm phot}|/(1+z_{\rm spec}) < 0.15$" (3.4)
6. **Search for [CII] emitter with NIRCam priors**: Extract beam-aperture ALMA spectra at positions of 150 NIRCam galaxies (F150W<27.5, zphot=6-7); detect line, derive z, L_CII, L_IR  
  > "We produce ALMA Band 6 spectra with the beam-size aperture at source positions of 150 NIRCam galaxies that are bright (F150W $<$ 27.5 mag)" (4.3)
   - assumption: Modified blackbody Td=45 K, beta=1.8 for L_IR; FWHM=200 km/s and 5 sigma for LF  
  > "assuming a modified blackbody with a dust temperature of 45 K and dust emissivity index of 1.8" (4.3)
   - fitting: _not stated_
   - validation: Confirmed by NIRSpec prism z=6.332  
  > "the source redshift is securely confirmed at $z=6.332$" (4.3)
7. **Search for dust at z>9 and stack**: Inspect Wide-natural cutouts for 16 z>=9 galaxies; stack maps; chance probability from marginal-source density  
  > "we present a stacked ALMA map generated from the *Wide*-natural images of 16 sources at $z_{\rm spec}$ or $z_{\rm phot}\gtrsim9$" (4.4)
   - fitting: _not stated_
   - validation: Chance projection probability ~0.77%  
  > "infers the probability of the chance projection (cite: downes1986) with the $0
 \mbox{
  \kern  0.13ex.
  \kern -0.95ex\ensuremath{''}
  \kern -0.1ex
 }
1$ offset to be $\sim$0.77%" (4.4)
8. **Infrared luminosity function**: IRLF at z=1-5 and z=8-11 following ALCS method; modified blackbody Td=35 K, beta=1.8; Gehrels Poisson errors; no completeness correction  
  > "We assume the modified black body with the dust temperature of $T_{\rm d}=35$ K and the dust-emissivity index $\beta_{\rm d}=1.8$ (cite: mauerhofer2023)." (4.5)
   - assumption: Td=35 K, beta=1.8  
  > "dust temperature of $T_{\rm d}=35$ K" (4.5)
   - fitting: _not stated_
   - validation: Compared with ALCS DPL, other observations and models  
  > "Our measurements are consistent with the previous measurements and the model predictions within their scatters." (4.5)

## Software

- **CASA** 6.4.12: calibration (pipeline), tclean imaging, concat, imfit  
  > "Common Astronomy Software Applications package version 6.4.12" (2.2)
- **SExtractor** 2.5.0: ALMA source extraction  
  > "We run version 2.5.0 of sextractor" (3.1)
- **Prospector** : SED fitting for physical properties and photo-z  
  > "The main products of the catalog are inferred using the `Prospector` Bayesian inference framework" (3.4)
- **EAZY** : photometric redshifts and NIRSpec redshift fitting  
  > "An independent SED fitting using `EAZY` (cite: brammer2008) has also been performed." (3.4)
- **dynesty** : nested sampling in Prospector  
  > "nested sampler `dynesty`" (3.4)
- **astropy** : listed software  
  > "astropy (cite: astropy2013)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Wide-natural continuum rms | 32.7 | not stated | uJy/beam | 1 | *Wide*-natural / 32.7 / $1.02\times0.77$ |
| Number of continuum sources | 69 (65 Wide + 4 Deep) | not stated | sources | 2 | we identify 65 ALMA sources from the *Wide* maps and an additional 4 ALMA sources from the deep maps |
| Purity | >0.97 | not stated | dimensionless | 2 | high purity $p>0.97$ |
| Median redshift, magnification, intrinsic flux | z=2.30, mu=1.7, S_int=0.24 mJy | not stated | mixed | 5 | median values of $z=2.30$, $\mu=1.7$, and $S_{\rm 1.2mm}^{\rm int}=0.24$ mJy |
| NIRCam counterparts | 67/69 | not stated | sources | 4 | we identify 67 ALMA sources with NIRCam counterparts |
| Spectroscopically confirmed sources | 27 | not stated | sources | 5 | This yields 27 sources whose redshifts have been spectroscopically determined. |
| HST-dark galaxies | 8 | not stated | sources | 0 | We identify eight ALMA sources (AID2, AID3, AID5, AID10, AID27, AID31, AID48, and AID52) |
| [CII] line frequency | 259.445 | 0.015 | GHz | 6 | The line feature is detected at $259.445\pm 0.015$ GHz with the line width of $220\pm40$ km s$^{-1}$ |
| [CII] redshift | 6.3254 | 0.0004 | dimensionless | 6 | resulting in the \[C ii\]-based redshift estimate of $z=6.3254\pm0.0004$ |
| [CII] LF lower limit | 3.2e-5 | not stated | Mpc^-3 | 6 | we infer the lower limit of $3.2\times10^{-5}$ Mpc$^{-3}$ |
| Stacked intrinsic 1.2-mm flux of z>~9 galaxies | 14.0 | 6.2 | uJy | 7 | inferring an intrinsic (lens-corrected) 1.2-mm flux density of $14.0\pm6.2$ $\mu$Jy |

## Qualitative findings

- Almost all NIRCam counterparts show undisturbed disk or spheroid morphology; merger fraction <10%  
  > "with the merger fraction among them being $<$10% (=6/70) at maximum" (4.1)

## Claim tuples

- H: Faint mm sources are triggered by mergers | E: Visual inspection of NIRCam counterparts | R: Almost all show undisturbed disk/spheroid; merger fraction <10% | F: Faint mm emission triggered by less violent mechanisms than mergers | **supported**
- H: HST-dark galaxies are dusty due to edge-on inclination | E: Color/magnitude selection and NIRCam morphology | R: 8 HST-dark sources, 4 face-on, 4 edge-on | F: Obscuration not always from inclination | **supported**
- H: A [CII] emitter at z~6-7 can be found with NIRCam priors | E: Spectra at 150 NIRCam positions | R: One line at 259.445 GHz, z=6.3254, NIRSpec-confirmed | F: Typical SFR-L[CII], lower limit on LF above models | **supported**
- H: Dust emission is detectable from z>9 galaxies | E: Cutouts and stack of 16 z>~9 galaxies | R: Marginal 2.6 sigma at z=10.07 X-ray AGN; stack 2.3 sigma | F: Possible dust in AGN host, insufficient significance | **partially**
- H: IRLF out to z~10 is consistent with models | E: IRLF without completeness correction | R: Consistent with prior measurements and models | F: Not in tension with predicted abundances | **supported**

## Reasoning

- Why this data: Homogeneous wide ALMA map matched to UNCOVER field for ALMA+JWST legacy  
  > "designed to homogeneously map the main UNCOVER $4'\times6'$ field at the 1.2-mm wavelength" (2.1)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): 1-2 sources may be spurious; no completeness correction for IRLF; z>9 detections marginal  
  > "This implies that $\sim$1–2 out of the 69 sources might be spurious" (3.1)
- Caveat (inferred, ours): IRLF lacks completeness correction so faint-end is biased
- Caveat (inferred, ours): JWST-dark candidates are near the noise threshold and may be spurious
- Caveat (inferred, ours): Lensing magnification uncertainties not propagated
- Caveat (inferred, ours): Lir from single band depends on assumed Td

## Reproducibility

- Data public (paper): ALMA raw data in archive; reduced maps, cubes and catalog released  
  > "The reduced ALMA continuum maps and cubes are also available via <https://jwst-uncover.github.io/DR2.html#DUALZ>." (Data availability)
- Products in archive: _not stated_
- Missing: Flux calibrator and weights details
- Missing: SED catalog and NIRSpec redshifts in unpublished companion papers
- Missing: Completeness/volume calculation for IRLF
- Data volume (inferred): ~hundreds of GB raw across 16 execution blocks plus archival data; imaging products tens of GB
- Score (inferred): 6/5, Public data and clear imaging/extraction recipe, but SED, NIRSpec and IRLF details depend on companion papers.
- Rediscovery candidate: yes, Data are public, imaging and source extraction are specified, and results include numeric counts, fluxes and a line detection.

## Links

- Method: (cite: fujimoto2023b) (Source extraction, data combination, and IRLF procedures)
- Method: (cite: bwang2024) (SED fitting catalog)
- Companion: (cite: bezanson2022) (UNCOVER JWST survey)
- Companion: (cite: weaver2023) (NIRCam DR2 catalog)
- Companion: (cite: furtak2023a) (Lens model)
- Related: UNCOVER
- Related: ALCS
- Related: ALMA-HFF
- Related: ASPECS
- Related: GLASS

## Checks

```json
{
 "quotes": 88,
 "quotes_ok": 88,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2023.1.00626.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 92,
  "stated": 66,
  "rate": 0.717
 },
 "evidence_ok": true
}
```

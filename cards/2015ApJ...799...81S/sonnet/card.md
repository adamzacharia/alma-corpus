# The SCUBA-2 Cosmology Legacy Survey: ALMA Resolves the Rest-frame Far-infrared Emission of Sub-millimeter Galaxies

`2015ApJ...799...81S` | The Astrophysical Journal 2015 | first author: Simpson, J. M. | arXiv: 1411.5025 | DOI: 10.1088/0004-637X/799/1/81

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the size and morphology of the 870 um dust continuum emission of bright SMGs on 2-10 kpc scales, and how do they compare with sizes at other wavelengths and with quiescent galaxies?  
  > "investigate the size and morphology of the sub–millimeter (sub–mm) emission on 2–10 kpc scales" (abstract)
- Target **30 bright SCUBA-2 sources in the UKIDSS UDS field (52 ALMA SMGs)**: coordinates _not stated_; z/distance photometric redshifts; z=4±1 assigned to 4 SMGs without; angular scale 8.5–7.5 kpc/arcsec at z~1.5–3.5  
  > "The observations discussed here targeted 30 870 $\mu$m sources lying in the UKIDSS UDS field." (2 Observations and Analysis); distance from UKIDSS UDS photometric redshift catalog (eazy), Simpson14 for NIR-faint SMGs  
  > "The observations discussed here targeted 30 870 $\mu$m sources lying in the UKIDSS UDS field." (2 Observations and Analysis)

## Data provenance

- ALMA projects: 2012.1.00090.S
- bands: Band 7 (870 um)  
  > "using 7.5-GHz of bandwidth centered at 344 GHz (870 $\mu$m; Band 7)" (2.1 ALMA data)
- frequencies and spectral setup: single continuum setup, four basebands of 128 dual-polarization channels  
  > "We used a “single continuum” correlator setup with four basebands of 128 dual-polarization channels each." (2.1 ALMA data)
- continuum bandwidth: 7.5 GHz centered at 344 GHz  
  > "using 7.5-GHz of bandwidth centered at 344 GHz" (2.1 ALMA data)
- arrays: 26 12-m antennae  
  > "the 26 ALMA 12–m antennae employed had a maximum baseline of 1250 m, and a median baseline of 200 m" (2.1 ALMA data)
- configurations: _not stated_
- baselines: max 1250 m, median 200 m  
  > "the 26 ALMA 12–m antennae employed had a maximum baseline of 1250 m, and a median baseline of 200 m" (2.1 ALMA data)
- angular resolution: 0.35''x0.25'' (robust 0.5); detection maps 0.8''x0.65''  
  > "yields a synthesized beam of 0.35$''\times$ 0.25$''$ using Briggs weighting (robust parameter = 0.5)" (2.1 ALMA data)
- max recoverable scale: 5''  
  > "The maximum angular scale that our observations are sensitive to is 5$''$" (2.1 ALMA data)
- sensitivity: median rms 0.21 mJy/beam (0.19–0.24) in high-res maps; 0.26 mJy/beam in 0.8'' maps  
  > "a median rms of $\sigma_{870} =$ 0.21 mJy beam$^{-1}$ (with a range from 0.19–0.24 mJy beam$^{-1}$)" (2.1 ALMA data)
- time on source: 150 s per map; 2.6 hr total project  
  > "Hence, for each map we obtained a 150 s integration." (2.1 ALMA data); "The total integration time for the project was 2.6 hrs." (2.1 ALMA data)
- observing dates: 2013 November 1  
  > "The ALMA data were taken on 2013 November 1" (2.1 ALMA data)
- pi or archival as stated: _not stated_
- Other facility **SCUBA-2/JCMT (S2CLS)**: 850 um selection of the 30 sources  
  > "we selected a sample of 30 of the brightest sub-millimeter sources in the field" (2 Observations and Analysis)
- Other facility **Herschel SPIRE**: 250/350/500 um photometry for FIR luminosities  
  > "we exploit the *Herschel* SPIRE imaging (cite: Pilbratt10; Griffin10) of the field at 250, 350 and 500 $\mu$m" (2.3 Multi–wavelength properties)
- Other facility **UKIDSS UDS / Spitzer IRAC**: photometric redshifts  
  > "we use the photometric redshift catalog of this field produced by the UKIDSS UDS team" (2.3 Multi–wavelength properties)
- External data: HST H-band sizes of ALESS SMGs (17 selected)  
  > "we have restricted their sample to the 17 SMGs with an apparent $H$–band magnitude $<$ $24$ mag" (4.1.1) [from Chen et al. 2014 (cite: Chen14)]
- External data: 1.4 GHz VLA sizes of 12 SMGs  
  > "a sample of 12 SMGs (median $S_{850}$ = 6.8 $\pm$ 0.6 mJy) with deconvolved sizes measured from $0.5''$ resolution 1.4 GHz/VLA imaging (cite: Biggs08)" (4.1.1) [from (cite: Biggs08)]
- External data: 12CO sizes of SMGs  
  > "present a compilation (including new observations) of the sizes of SMGs measured from resolved $^{12}$ CO" (4.1.1) [from (cite: Engel10)]
- External data: local merger-remnant CO sizes  
  > "presented a compilation of $<1$ kpc resolution interferometric imaging (new and archival) of $^{12}$CO" (4.1.2) [from (cite: Ueda14)]
- External data: quiescent z~2 galaxy sizes  
  > "by combining the samples presented by (cite: vandokkum08) and (cite: Krogager13)" (4.3) [from (cite: vandokkum08; Krogager13)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0238+166; phase calibrator J0217+014  
  > "Absolute flux calibration was derived from J 0238 + 166 and we used observations of the secondary phase calibrator J 0217 + 014, for phase referencing." (2.1 ALMA data)
- flux scale uncertainty: _not stated_
- self calibration: not done; no sources bright enough  
  > "we do not detect any sources at sufficiently high SNR to reliably self–calibrate" (2.1 ALMA data)

### Imaging

- task: CASA 4.2.1 clean with tight boxes around >5σ emission, cleaned to 1.5σ  
  > "a tight clean box was placed around all $>$ 5 $\sigma$ emission in each map and these were cleaned down to a depth of 1.5 $\sigma$" (2.1 ALMA data)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5 (high-res); natural weighting for detection maps  
  > "using Briggs weighting (robust parameter = 0.5)" (2.1 ALMA data); "but using natural weighting, and applying a Gaussian taper to the data in the $uv$-plane" (2.1 ALMA data)
- uv taper: Gaussian taper giving 0.8''x0.65'' beam (taper width not stated)  
  > "The resulting maps have a median angular resolution of 0.8 $'' \times$ 0.65$''$" (2.1 ALMA data)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.35''x0.25'', PA ~55 deg  
  > "median angular resolution of 0.35$''\times$ 0.25$''$ (P.A. $\sim$ 55 deg)" (2.1 ALMA data)
- final rms: 0.21 mJy/beam  
  > "a median rms of $\sigma_{870} =$ 0.21 mJy beam$^{-1}$" (2.1 ALMA data)

### Inherited from earlier work

- data reduction and source extraction details  
  > "The data reduction and source extraction from our ALMA data is described in detail in Simpson et al. (in prep.)." (2.1 ALMA data) [from Simpson et al. (in prep.)]
- cleaning procedure  
  > "We then applied the same procedure adopted by Hodge et al. (2013)" (2.1 ALMA data) [from Hodge et al. 2013 (cite: Hodge13)]
- FIR luminosity/SED fitting and deblending  
  > "Following the approach of (cite: Swinbank13), they use a prior catalog of sources detected at 24 $\mu$m or 1.4 GHz" (2.3 Multi–wavelength properties) [from (cite: Swinbank13); multiwavelength analysis Ma et al. (in prep.)]
- z=4±1 for SMGs without photometric redshift  
  > "so we adopt their approach and assign these sources a redshift of $z =$ 4 $\pm$ 1" (2.3 Multi–wavelength properties) [from (cite: Simpson14)]

### Not stated but needed to reproduce (our reading)

- Gaussian taper width/uv-range for detection maps
- clean threshold values, cell and image size, niter
- bandpass calibrator and flux-scale uncertainty
- photometric redshifts and L_FIR values per SMG (from Ma et al. in prep.)
- bootstrap iteration counts
- exact conversion from FWHM to half-light radius and R80
- details of stacking (centering, weighting)

## Analysis recipe

1. **Image and build catalog**: Clean to produce 0.3'' high-res and 0.8'' detection maps; select >4σ sources; measure peak and 0.8'' aperture flux  
  > "we identify sources within the ALMA primary beam FWHM that are detected at $>$ 4 $\sigma$ in the 0.8$''$ FWHM “detection” maps" (2.1 ALMA data)
   - software: CASA
   - fitting: _not stated_
   - validation: imfit model vs aperture flux ratio 1.02±0.01  
  > "$S^{\rm Model}$ / $S^{\rm Aperture}$ = 1.02 $\pm$ 0.01" (2.1 ALMA data)
2. **Test robustness of resolved sizes**: Split-in-time imaging of UDS 204.0, phase calibrator size test, and 20,000 injected Gaussian simulations  
  > "we create 20,000 elliptical Gaussian model sources with a uniform distribution of peak SNR from 4 to 30" (2.2 Robustness of imaging)
   - software: CASA
   - parameter: SNR>=10 required for 68% of sources recovered with fractional size error <30%  
  > "We find that this requirement is met for sources that are detected at a SNR $\geq$ 10" (2.2 Robustness of imaging)
   - fitting: imfit elliptical Gaussian  
  > "we use the imfit routine in casa to fit an elliptical Gaussian model (convolved with the synthesised beam) for the 870 $\mu$m emission from each SMG." (Observations and Analysis, Robustness of imaging)
   - validation: point-source fits imply true size <=0.18''  
  > "we adopt this as an upper limit for the size of the unresolved SMGs" (2.2 Robustness of imaging)
3. **Measure sizes of SMGs**: imfit elliptical Gaussian per SMG in 0.3'' maps; uv-plane amplitude fits for 8 isolated SMGs; stacking of faint SMGs with bootstrap errors  
  > "Using the imfit routine we determine the best-fit elliptical Gaussian model for the 23 SMGs in our bright sample" (3.1 Resolved dust emission)
   - software: CASA imfit
   - parameter: free parameters: position, peak flux, major/minor axis, PA  
  > "The free parameters of the model are position; peak flux density; major and minor axis; and position angle." (3.1 Resolved dust emission)
   - fitting: _not stated_
   - validation: uv vs image size ratio 0.9±0.2  
  > "FWHM$^{\rm uv}$ / FWHM$^{\rm image} =$ 0.9 $\pm$ 0.2" (3.1 Resolved dust emission)
4. **Convert to physical sizes and compare with other wavelengths**: Use photometric redshifts to convert; compare with radio, CO, HST, local U/LIRG sizes  
  > "we use the photometric redshift to convert the measured angular diameter into an intrinsic physical scale" (4.1 Physical size of SMGs)
   - assumption: Cosmology OmegaL=0.73, Om=0.27, H0=71  
  > "we adopt a cosmology with $\Omega_{\Lambda}$ = 0.73, $\Omega_{\rm m}$ = 0.27, and $H_{\rm  0}$ = 71 km s$^{-1}$ Mpc$^{-1}$" (1 Introduction)
   - fitting: _not stated_
   - validation: _not stated_
5. **Fit Sérsic profile to stack**: Test galfit recovery on 4000 injected models; stack 23 SMGs and fit Sérsic  
  > "stack the 870 $\mu$m emission from the 23 SMGs detected at $>$ 10 $\sigma$ and use galfit to fit a Sérsic model to the stacked profile" (4.3.1 Sérsic index)
   - software: galfit
   - fitting: galfit; bootstrap errors  
  > "stack the 870 $\mu$m emission from the 23 SMGs detected at $>$ 10 $\sigma$ and use galfit to fit a Sérsic model to the stacked profile." (Sérsic index)
   - validation: injection recovery  
  > "half-light size of the model sources is recovered accurately at all values of SNR and Sérsic index" (4.3.1 Sérsic index)
6. **Derive SFR surface density**: SFR from L_FIR (Salpeter IMF), halved for half-light radius, divided by area of uniform disc; compare to Eddington limit of Andrews & Thompson  
  > "we initially divide the SFR of each SMG by a factor of two" (4.2 Eddington)
   - assumption: gas fraction 1, dust-to-gas 1/90, uniform disc  
  > "We adopt a dust–to–gas ratio of $f_{\rm dg} = 1/90$" (4.2 Eddington)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2.1: imaging, imfit size fitting  
  > "The data were imaged using the Common Astronomy Software Application (casa version 4.2.1)." (2.1 ALMA data)
- **galfit** : Sérsic fits to stacked and simulated sources  
  > "We fit a Sérsic profile to each model source using the code galfit (cite: Peng10)" (4.3.1 Sérsic index)
- **eazy** : photometric redshifts  
  > "using the public SED fitting code eazy (cite: Bramer08)" (2.3 Multi–wavelength properties)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| median intrinsic angular FWHM, SNR>10 SMGs | 0.30 | ±0.04 | arcsec | 3 | median intrinsic angular size of FWHM = $0.30 \pm 0.04''$ for the 23 SMGs |
| median physical FWHM | 2.4 | ±0.2 | kpc | 4 | the median physical size of the SMGs is $2.4 \pm 0.2$ kpc (FWHM of the major axis) |
| stacked size SNR 5–10 | 0.30 | ±0.07 | arcsec | 3 | We derive sizes of 0.30 $\pm$ 0.07$''$ and 0.35$_{-0.10}^{+0.17}$$''$ for the two sub-samples respectively. |
| peak flux ratio 0.3''/0.8'' | 0.65 | ±0.02 | dimensionless | 3 | $S^{0.3}_{\rm pk}$ / $S^{0.8}_{\rm pk} =$ 0.65 $\pm$ 0.02 |
| stacked Sérsic index | 2.5 | ±0.4 | dimensionless | 5 | Sérsic index of $n$ = 2.5 $\pm$ 0.4 and a half-light radius of $R_{\rm e}$ = 0.17 $\pm$ 0.03$''$ |
| median half-light radius at 870 um | 1.2 | ±0.1 | kpc | 4 | the SMGs have a median $R_{\rm e} = 1.2 \pm 0.1$ kpc in the sub–millimeter |
| median SFR surface density | 90 | ±30 | Msun/yr/kpc^2 | 6 | the median star formation rate surface density of the SMGs is $90 \pm 30$ $\mathrel{\rm M_{\odot}}$ yr$^{-1}$ kpc$^{-2}$ |
| median L_FIR | 5.7e12 | ±0.7e12 | Lsun | 0 | $L_{\rm FIR} =$ (5.7 $\pm$  0.7) $\times$10$^{12}$ L$_\odot$ |

## Qualitative findings

- No trend of size with 870 um flux density or redshift for z<3.5  
  > "but do not find a trend with either redshift or 870 $\mu$m flux density." (Conclusions)

## Claim tuples

- H: Are bright SMGs resolved at 0.3'' and how large is their dust emission? | E: imfit Gaussian fits to 23 SNR>10 SMGs and stacking | R: median FWHM 0.30±0.04'' = 2.4±0.2 kpc | F: Dust emission is compact, a few kpc | **supported**
- H: Do radio and CO sizes agree with sub-mm sizes? | E: Compare with Biggs08 and Engel10 | R: CO consistent; 1.4 GHz ~2x larger | F: Radio excess attributed to cosmic-ray diffusion | **partially**
- H: Is star formation compact relative to the stellar distribution and consistent with SMGs being progenitors of compact quiescent galaxies? | E: Compare with HST sizes and quiescent galaxy sizes | R: optical sizes ~4x larger; sub-mm Re 1.2 vs quiescent 1.5 kpc | F: Compact starburst may transform SMGs into compact quiescent galaxies | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: SNR>=10 cut set by simulations of size recovery precision  
  > "which is the justification for our use of this limit to define the bright SMG sample analysed in this paper" (2.2 Robustness of imaging)
- Limitation (authors): Four possibly lensed SMGs excluded; four SMGs lack redshifts; only one SMG at z>3.5  
  > "An important caveat of this result is that only one SMG in our sample has a photometric redshift of $z \mathrel{\raise 0.35ex\hbox{$\scriptstyle >$}\kern-0.6em\lower 0.40ex\hbox{{$\scriptstyle \sim$}}}3.5$." (4.1 Physical size of SMGs)
- Caveat (inferred, ours): Sizes are Gaussian FWHM comparable to the beam; conversion to half-light radius and comparison to Sérsic sizes is model dependent
- Caveat (inferred, ours): Median bias of 1.8% uncorrected; brightest-selected sample may not represent all SMGs
- Caveat (inferred, ours): Comparison samples are heterogeneous in selection and CO transition

## Reproducibility

- Data public (paper): All data obtainable from ALMA, ESO, Spitzer and Herschel archives  
  > "All data used in this analysis can be obtained from the ALMA, ESO, *Spitzer* and *Herschel* archives." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Photometric redshifts and L_FIR tables (Ma et al. in prep.)
- Missing: full reduction details deferred to Simpson et al. in prep.
- Missing: taper and clean parameters
- Data volume (inferred): ~tens of GB (30 fields, Cycle 1 Band 7, 2.6 hr)
- Score (inferred): 3/5, Public data and clear imfit-based method, but reduction details deferred to unpublished paper and redshifts/luminosities come from in-prep work.
- Rediscovery candidate: yes, Public ALMA data, simple Gaussian-fit recipe and numeric size results; redshifts need external catalog.

## Links

- Method: Hodge et al. 2013 (cite: Hodge13) (clean procedure adopted)
- Method: Swinbank et al. 2014 (cite: Swinbank13) (Herschel deblending and SED fitting)
- Companion: Simpson et al. (in prep) (ALMA catalogue, reduction and number counts)
- Companion: Ma et al. (in prep) (multi-wavelength properties of the sample)
- Related: SCUBA-2 Cosmology Legacy Survey
- Related: UKIDSS UDS
- Related: ALESS

## Checks

```json
{
 "quotes": 70,
 "quotes_ok": 70,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 55,
  "rate": 0.671
 },
 "evidence_ok": true
}
```

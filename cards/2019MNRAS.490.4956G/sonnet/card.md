# An ALMA survey of the SCUBA-2 Cosmology Legacy Survey UKIDSS/UDS field: high-resolution dust continuum morphologies and the link between sub-millimetre galaxies and spheroid formation

`2019MNRAS.490.4956G` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Gullberg, B. | arXiv: 1910.01121 | DOI: 10.1093/mnras/stz2835

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies
- Question: What are the sizes, shapes and light profiles of the 870 um dust continuum in bright SMGs, and do they indicate bar-like structures and spheroid formation?  
  > "We measure sizes, shapes and light profiles for the rest-frame far-infrared emission from these luminous star-forming systems" (abstract)
- Target **153 AS2UDS SMGs (S/N>8, Cycle 3, 0.18'' resolution) in the SCUBA-2 CLS UDS field**: coordinates _not stated_; z/distance median z=2.9±0.1 (photometric)  
  > "We therefore select all 153 SMGs which were observed in Cycle 3 (0.18$''$ FWHM) and are detected with S/N $>8$ in the 0.5$''$ tapered maps" (Sample Selection); distance from photometric redshifts from magphys SED fitting (ugne19)  
  > "We therefore select all 153 SMGs which were observed in Cycle 3 (0.18$''$ FWHM) and are detected with S/N $>8$ in the 0.5$''$ tapered maps" (Sample Selection)

## Data provenance

- ALMA projects: 2015.1.01528.S
- bands: _not stated_
- frequencies and spectral setup: receivers tuned to central frequency 344 GHz (870 um continuum)  
  > "For all the observations, the central frequency of the receivers was tuned to 344 GHz" (Sample Selection)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.18'' FWHM native (Cycle 3); 0.18''-0.35'' across cycles  
  > "the FWHM of the naturally weighted synthesised beam varies from $0.18\ensuremath{''}$ to $0.35\ensuremath{''}$" (Sample Selection)
- max recoverable scale: _not stated_
- sensitivity: 0.09-0.34 mJy/beam in 0.5'' tapered maps  
  > "The noise in these tapered maps varies between $0.09$–$0.34$ mJy beam$^{-1}$" (Sample Selection)
- time on source: 40 seconds per source  
  > "the exposure time of 40 seconds per source is short" (Sample Selection)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **HST/CANDELS**: F606W, F814W, F125W, F160W imaging for 47 SMGs  
  > "This provides F606W, F814W, F125W, and F160W-band observations for 47 of the AS2UDS SMGs that lie in the central region of the UDS." (Sample Selection)
- Other facility **UKIDSS UDS K-band**: K-band images for Sérsic size fits with GALAPAGOS  
  > "we perform a Sérsic fit to the $K$-band images of all of the SMGs in our sample using GALAPAGOS" (3.3 Comparison of the dust and rest-frame optical emission)
- External data: Photometric redshifts, SFRs, dust and stellar masses from magphys SED fitting  
  > "(cite: ugne19) use the extensive multiwavelength imaging of the UDS to estimate the photometric redshifts and physical properties of the complete sample" (Multi-wavelength data sets) [from (cite: ugne19)]
- External data: AS2UDS source positions and catalogue  
  > "aligning the phase centre of our visibilities with the source positions from (cite: stach19)" (3.1 Sizes measurements from the visibility plane) [from (cite: stach19)]
- External data: GAMA g-band morphologically classified galaxy axis ratios and Sérsic indices  
  > "to those derived in the $g$-band for the stellar light distributions of a morphologically classified sample of low-redshift galaxies from the GAMA survey (cite: kelvin14)" (4.1 Discs, spheroids or bars?) [from (cite: kelvin14)]
- External data: 12CO(3-2) profiles of four ALESS SMGs  
  > "We also overlay the gas emission as inferred from the molecular $^{12}$CO(3–2) emission from four SMGs from ALESS (cite: rivera18)." (4.2 What is the extended dust component?) [from (cite: rivera18)]

## Processing

### Calibration

- pipeline or manual: standard ALMA calibration scripts  
  > "we used the Common Astronomy Software Application (cite: mcmullin07) version 4.5.3 using the standard ALMA calibration scripts." (Sample Selection)
- casa version: CASA 4.5.3  
  > "version 4.5.3 using the standard ALMA calibration scripts" (Sample Selection)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN in CASA  
  > "The data were imaged using the CLEAN, algorithm in CASA with natural weighting (ROBUST $=2$)." (Sample Selection)
- deconvolver: _not stated_
- weighting robust: natural (robust = 2)  
  > "natural weighting (ROBUST $=2$)" (Sample Selection)
- uv taper: 0.5'' FWHM taper for catalogue  
  > "Hence to construct the catalogue, all of the maps were tapered to 0.5$''$ FWHM." (Sample Selection)
- cell size: 0.03'' per pixel  
  > "at the same pixel scale as our data ($0.03\ensuremath{''}$ pixel$^{-1}$)" (3.2 Sizes and shape measurements from the image plane)
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

- Data reduction, imaging and catalogue construction of AS2UDS  
  > "Details of the AS2UDS observations, data reduction and catalog are given in (cite: stach19), although we briefly summarise these here." (Sample Selection) [from (cite: stach19)]
- S/N>8 threshold for size uncertainty <35%  
  > "(cite: simpson15b) showed that for a signal-to-noise ratio of S/N $>8$, the uncertainties on the resulting size measurements of sources are $\lesssim35$%" (Sample Selection) [from (cite: simpson15b)]
- Apparent axis ratio formalism for projected triaxial/disc shapes  
  > "We follow the example of (cite: ryden04), where the apparent axis ratio $q$ is given by" (4.4.1 Geometrical models) [from (cite: ryden04)]

### Not stated but needed to reproduce (our reading)

- Image-plane Sérsic fitting code (not named or released), fit algorithm, priors and bounds
- Source of Cycle 3 project/member IDs and which execution blocks
- Details of CASA simulation setups (configuration files, noise, flux distribution)
- Mask/aperture and radial bin choices for stacked profiles
- Fitting method and uncertainties for the two-component stack model
- Cost function used to match axis-ratio distributions in the triaxial grid search
- Photometric redshift/SFR table (Dudzeviciute et al.)

## Analysis recipe

1. **Select sample**: Cycle 3 AS2UDS SMGs at 0.18'' with S/N>8 in 0.5'' tapered maps gives 153 sources  
  > "We therefore select all 153 SMGs which were observed in Cycle 3 (0.18$''$ FWHM) and are detected with S/N $>8$ in the 0.5$''$ tapered maps" (Sample Selection)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Size from uv-amplitude profiles**: Shift phase centre with fixvis, radially average amplitudes in 75 klambda bins, fit Gaussian and n=1 Sérsic profiles  
  > "using the casa task fixvis and then radially averaging the amplitudes in 75 k$\lambda$ bins" (3.1 Sizes measurements from the visibility plane)
   - software: CASA
   - parameter: uv-range out to 1200 klambda; n=1 with free Reff  
  > "we adopt an $n=1$ Sérsic and allow the effective radius as a free parameter and fit the $uv$-amplitude profile for each SMG" (3.1 Sizes measurements from the visibility plane)
   - fitting: _not stated_
   - validation: Compared with 1.1 mm sizes of 30 overlap sources (ratio 0.95±0.05); simulated Sérsic profiles in CASA  
  > "derive a median ratio of FWHM from Gaussian fits of $0.95\pm 0.05$" (3.1 Sizes measurements from the visibility plane)
3. **Image-plane 2D Sérsic fits**: Fit 2D Sérsic convolved with the synthesised beam, free and fixed n=1, returning Reff, b/a, PA, n  
  > "we fit a two dimensional Sérsic surface brightness profile, allowing the effective radius, axial ratio and Sérsic index to vary" (3.2 Sizes and shape measurements from the image plane)
   - software: CASA
   - fitting: _not stated_
   - validation: 1000 simulated galaxies: Reff recovered within 20%, axis ratio within 12%, n typical error 22%  
  > "On average we recover the effective radii to within 20% and the axis ratios are recovered within 12% of the value of the input parameters." (3.2 Sizes and shape measurements from the image plane)
4. **Model axis ratio distribution**: Compare observed b/a with optically thick/thin discs and triaxial models with Gaussian b/a and c/a distributions, uniform viewing angles; two-pass grid search; KS test and AIC  
  > "we perform our search for the best-fit model by running through the parameter space twice; first by using a large bin size to cover the full parameter range" (4.4.1 Geometrical models)
   - assumption: uniform angle distributions for theta and phi  
  > "We assume uniform angle distributions for both $\theta$ and $\phi$" (4.4.1 Geometrical models)
   - fitting: grid search over mode and width parameters  
  > "we perform our search for the best-fit model by running through the parameter space twice; first by using a large bin size to cover the full parameter range" (Modelling the axis ratio distribution / Geometrical models)
   - validation: KS test and AIC (triaxial 10.8 vs 33.8 thick and 15.2 thin)  
  > "for the triaxial case is 10.8. The AIC values for the optical thick and thin cases with uniform viewing angle" (4.4.1 Geometrical models)
5. **Stack maps to find extended emission**: Stack in uv plane with STACKER weighted by 1/sigma^2 and in image plane using 10''x10'' thumbnails; fit double n=1 Sérsic  
  > "employ the STACKER library developed for use in CASA to stack the visibilities (cite: lindroos15)" (4.3 Stacked emission profiles)
   - software: CASA, STACKER
   - parameter: compact Reff fixed to 0.10''; extended Reff ~0.5''  
  > "For the compact component we fix $R_{\text{eff}}$ to the value derived above, $0.10\ensuremath{''}\pm0.04\ensuremath{''}$, and for the extended component we adopt $R_{\text{eff}}$ $\sim0.5\ensuremath{''}$." (4.3 Stacked emission profiles)
   - fitting: _not stated_
   - validation: Calibrator stack and CASA simulation of a 10x brighter compact n=1 source show no extended emission  
  > "This test show that a compact source with $R_{\text{eff}}$$= 0.11\ensuremath{''}$ observed at 0.18$''$ resolution does not show emission on $\geq0.5\ensuremath{''}$ scale." (4.3 Stacked emission profiles)

## Software

- **CASA** 4.5.3: calibration, imaging, fixvis, simulations  
  > "version 4.5.3 using the standard ALMA calibration scripts" (Sample Selection)
- **STACKER** : stacking visibilities  
  > "employ the STACKER library developed for use in CASA to stack the visibilities" (4.3 Stacked emission profiles)
- **GALAPAGOS** : Sérsic fits to K-band images  
  > "using GALAPAGOS ((cite: almaini17)) which takes the PSF into account" (3.3 Comparison of the dust and rest-frame optical emission)
- **magphys** high-redshift version: SED fitting (by ugne19) for redshifts and physical properties  
  > "using the high-redshift version of magphys (cite: dacunha15; battisti19)" (Multi-wavelength data sets)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median effective radius (n=1) | 0.10 | ±0.04 | arcsec | 3 | derive a median effective radius ($R_e$) of $0.10\ensuremath{''}\pm0.04\ensuremath{''}$ |
| Median Sérsic index (free fit) | 1.00 | ±0.12 | dimensionless | 3 | we derive a median $n=1.00\pm0.12$ and $R_{\text{eff}}$$=0.11\ensuremath{''}\pm 0.01\ensuremath{''}$ |
| Median axis ratio b/a (fixed n) | 0.63 | ±0.02 | dimensionless | 3 | a median of $b/a=0.63\pm0.02$ for the fixed $n$ fit |
| Median Gaussian FWHM from uv fits | 0.25 | ±0.03 | arcsec | 2 | we derive a median FWHM size of $0.25\ensuremath{''} \pm 0.03\ensuremath{''}$ |
| Extended component fraction of total 870um emission | 13 | ±1 | % | 5 | The extended component accounts for $13\pm1$% of the total emission. |
| Luminosity-weighted effective radius including extended component | 0.15 | ±0.05 | arcsec | 5 | we derive a typical effective radius of $\simeq0.15\ensuremath{''}\pm0.05\ensuremath{''}$ or $1.2\pm0.4$ kpc |
| K-band to 870um effective radius ratio | 2.2 | ±0.2 | dimensionless | 0 | the $K$-band effective radii are a factor of $2.2\pm0.2$ larger than the effective radii measured at 870 $\mu$ |
| Best-fit triaxial b/a mode | 0.66 | ±0.02 | dimensionless | 4 | $q_{b/a}$      /   0.1–1    / $0.66\pm0.02$ |

## Qualitative findings

- Axis ratio distribution lacks round sources, matches spheroids but Sérsic index matches discs, consistent with bars  
  > "the axis ratio distribution of SMGs is most similar to those of spheroid galaxies, while their Sérsic index distribution is most similar to that of disc galaxies." (Summary and Conclusions)
- Extended component's luminosity roughly constant with SFR while compact component brightens  
  > "the size and luminosity of the extended component is roughly constant with total star-formation rate, while the compact component becomes brighter." (Summary and Conclusions)

## Claim tuples

- H: Are SMG dust continuum morphologies consistent with randomly oriented discs? | E: Compared b/a distribution with thick/thin disc and triaxial models using KS and AIC | R: Discs rejected (KS 0%); triaxial has KS 40% and lowest AIC | F: SMG emission is triaxial with n~1, bar-like | **supported**
- H: Is there faint extended dust emission around the compact starburst? | E: Stacked 870um maps in uv and image planes | R: Extended component on ~0.5'' scales with 13±1% of flux | F: Extended disc/envelope similar to CO and stellar light | **supported**
- H: Do SMG sizes evolve with redshift or flux? | E: Plotted Reff against z and S870 | R: Weak decline with z, marginal increase with S870 | F: Physical sizes do not evolve strongly | **partially**

## Reasoning

- Why this data: Cycle 3 0.18'' data with S/N>8 give reliable sizes and shapes  
  > "This selection should ensure we can measure robust sizes and shapes for these sources" (Sample Selection)
- Why this method: _not stated_
- Alternative: Optically thick and thin circular disc models rejected as they need unphysical biased viewing angles  
  > "neither of the circular disc models is able to adequately fit the data without invoking assumptions of unphysical viewing angle biases" (4.4.1 Geometrical models)
- How they decided it was enough: _not stated_
- Limitation (authors): Resolution and depth insufficient to directly detect bars; higher resolution needed  
  > "to confirm this requires deeper observations to detect the extended components in individual maps, higher resolution imaging ($\sim0.08\ensuremath{''}$)" (Summary and Conclusions)
- Caveat (inferred, ours): Bar interpretation inferred indirectly from statistics; 0.18'' resolution cannot resolve bars
- Caveat (inferred, ours): Sérsic index poorly constrained (22% error) at this S/N
- Caveat (inferred, ours): Photometric redshifts used for physical sizes
- Caveat (inferred, ours): Extended component sensitive to assumed fixed Reff and profile shape

## Reproducibility

- Data public (paper): ALMA programme 2015.1.01528.S cited  
  > "The ALMA data used in this paper were obtained under programs ADS/JAO.ALMA#2015.1.01528.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Image-plane fitting code and settings
- Missing: Photometric redshift catalogue (Dudzeviciute et al., submitted)
- Missing: Stack fitting details
- Missing: Simulation setup
- Data volume (inferred): ~100-300 GB raw for Cycle 3 execution blocks covering 153+ fields (rough estimate)
- Score (inferred): 3/5, Data public and approach clear but fitting code, priors and several settings unstated.
- Rediscovery candidate: no, Recipe incomplete (custom fitting code, redshift table external).

## Links

- Method: (cite: stach19) (AS2UDS data reduction and catalogue)
- Method: (cite: ryden04) (apparent axis ratio formalism)
- Method: (cite: lindroos15) (STACKER visibility stacking)
- Companion: (cite: ugne19) (photometric redshifts and physical properties of AS2UDS SMGs)
- Companion: (cite: hodge19) (high-resolution bar and ring structures in SMGs)
- Related: AS2UDS
- Related: SCUBA-2 Cosmology Legacy Survey
- Related: CANDELS
- Related: ALESS

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
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 45,
  "rate": 0.577
 },
 "evidence_ok": true
}
```

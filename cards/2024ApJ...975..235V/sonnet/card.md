# JWST Imaging of Edge-on Protoplanetary Disks. III. Drastic Morphological Transformation Across the Mid-infrared in Oph163131

`2024ApJ...975..235V` | The Astrophysical Journal 2024 | first author: Villenave, Marion | arXiv: 2410.00156 | DOI: 10.3847/1538-4357/ad7de0

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: protoplanetary_disks
- Question: How does the morphology of the edge-on disk Oph163131 change from 2 to 21 micron with JWST, and what do dark lane chromaticity and the central source imply for dust and disk structure?  
  > "The images show a remarkable evolution in disk structure with wavelength, quite different from previous JWST observations of other edge-on disks." (abstract)
- Target **Oph163131 (SSTc2d J163131.2-242627)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2018.1.00958.S, 2016.1.00771.S
- bands: Band 6 (ALMA, used only as overlay)  
  > "which were observed with the band 6 receivers" (Acknowledgements)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO 12CO (overlay only) (not stated)
- Other facility **JWST NIRCam and MIRI**: Broadband images at 2.0, 4.44, 7.7, 12.8, 21 micron (GO 2562)  
  > "The observations used 5 different filters, F200W ($2.0\mu$m), F444W ($4.44\mu$m), F770W ($7.7\mu$m), F1280W ($12.8\mu$m), and F2100W ($21.0\mu$m)." (Observations & Data reduction)
- Other facility **HST ACS/WFC**: 0.6 and 0.8 micron archival images (program 12514)  
  > "The $HST$ observations were obtained using filters F606W and F814W ($0.6\mu$m, $0.8\mu$m) and observed on March 4, 2012." (Observations & Data reduction)
- External data: Radiative transfer model A (inclination 84.5 deg, scale height 7.2 au at 100 au, flaring 1.5, surface density exponent 1.01)  
  > "That model includes an inclination of 84.5$^\circ$, a gas scale height of 7.2au at a radius of 100au, a flaring exponent of 1.5, and a surface density exponent of 1.01." (4.1 Chromaticity) [from Wolff_2021]
- External data: ALMA continuum modeling: bright inner region, surface density >10x higher inside ~10 au, two rings  
  > "(cite: Villenave_2022) obtained a surface density more than one order of magnitude higher in that inner region than in the rest of the disk" (4.2 Transition) [from Villenave_2022]

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

- Spine-fitting method for dark lane thickness and nebula widths  
  > "We adopt the methodology previously employed by (cite: Duchene_2023) and (cite: Villenave_2023b) to fit the two scattering surfaces and quantify disk parameters." (3 Results) [from Duchene_2023; Villenave_2023b]
- Radiative transfer model suite approach, DIANA dust composition, DHS  
  > "we produce a suite of radiative transfer models with different properties, following the approach of (cite: Duchene_2023)." (4.1 Chromaticity) [from Duchene_2023]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, imaging parameters and data products are not given; the ALMA overlay data are from earlier work
- Number of photons, wavelength grid and mcfost settings for the models
- Stellar parameters and dust grid for the toy model
- Spine polynomial order and aperture positions
- Fits to the central source were done in IDL IDP3 with no parameters given

## Analysis recipe

1. **Reduce JWST images**: Re-run JWST pipeline phase 3 (F444W from uncalibrated), skymatch background subtraction, Background2D for MIRI, reproject and align to F200W grid  
  > "we obtained the phase 2 pipeline calibrated data from the MAST archive (DOI: ), and we re-ran phase 3, using the JWST pipeline version 1.9.5." (Observations & Data reduction)
   - software: JWST pipeline, photutils, reproject
   - parameter: skymatch subtract = True; F444W suppress_one_group = False  
  > "we set `suppress_one_group = False` in the `ramp fit` step of phase 1." (Observations & Data reduction)
   - fitting: _not stated_
   - validation: Alignment shift checked visually using a background galaxy anchored to Gaia DR3  
  > "We visually checked that the alignment does not require a rotation; it only includes a shift in right ascension and declination." (Observations & Data reduction)
2. **Measure dark lane thickness and nebula widths**: Spine fitting of peaks in minor-axis cuts with polynomial fit; aperture photometry flux ratio  
  > "Those are then fitted by a polynomial function to define the spines." (3 Results)
   - fitting: polynomial  
  > "Those are then fitted by a polynomial function to define the spines." (Results)
   - validation: _not stated_
3. **Size of MIRI central source and photometry**: 2D Gaussian fit compared to WebbPSF point source, quadrature subtraction; aperture photometry with 7.5x4.5 and 2x2 arcsec apertures  
  > "We measured the size of this central source by fitting a 2D Gaussian using the IDP3 routines in IDL, comparing the observed source size to $WebbPSF$ models" (3 Results)
   - software: IDP3, WebbPSF
   - assumption: Telescope beam assumed Gaussian  
  > "After subtracting in quadrature the telescope beam size, also assumed to be Gaussian" (3 Results)
   - fitting: 2D Gaussian  
  > "We measured the size of this central source by fitting a 2D Gaussian using the IDP3 routines in IDL" (Results)
   - validation: Optical artifacts ruled out via field-star PSFs, wavefront error and spike orientation  
  > "the extended nebula seen at 7.7$\mu$m and 12.8$\mu$m is *not* aligned with JWST’s PSF hexagonal diffraction spikes" (3 Results)
4. **Model dark lane chromaticity**: Six radiative transfer models (standard, settled, small grains) convolved with WebbPSF; dust mass tuned so dark lane at 2 micron matches data  
  > "the dust mass of each model is adjusted so that its dark lane thickness at 2$\mu$m matches that of the observations." (4.1 Chromaticity)
   - software: mcfost, WebbPSF
   - parameter: p=3.5, amin 0.03 um, amax 1000 um; settling eta=0.5 with a_mix 10, 1, 0.1 um  
  > "We implement three scenarios, where grains larger than $a_{mix}=10\mu$m, 1$\mu$m, and 0.1$\mu$m are affected by vertical settling." (4.1 Chromaticity)
   - assumption: DIANA dust composition, DHS for compact aggregates  
  > "we adopt the DIANA dust composition (cite: Woitke_2016) and use the Distribution of Hollow Spheres method" (4.1 Chromaticity)
   - fitting: No formal fit; qualitative comparison  
  > "The comparison of the models and the data are shown in Fig [4](#fig:model_chromaticity)." (Discussion: Chromaticity of the Dark Lane from 0.6-4.4 μm)
   - validation: _not stated_
5. **Toy model of thick inner disk**: Modified model A: inner 10 au has as much mass as outer 100 au, scale height ~4x larger within 10 au  
  > "such that the inner 10au contain as much mass as the outer 100au of the disk (M$_{dust}=5\ 10^{-4}$ M$_\ensuremath{\odot}$)" (4.2 Transition)
   - software: mcfost
   - fitting: _not stated_
   - validation: Compared qualitatively to the morphology transition and SED rise  
  > "Consistent with observations, the spectral energy distribution of the model shows a sharp rise beyond 10$\mu$m, while the main morphological changes occur between 4.44$\mu$m and 7.7$\mu$m" (Discussion: The Transition in Disk Appearance Beyond 4.4 μm)

## Software

- **JWST pipeline** 1.9.5 (F444W: 1.11.1.dev16+gb79a88af): Reduction of JWST images  
  > "using the JWST pipeline version 1.9.5" (Observations & Data reduction)
- **photutils** : Background2D subtraction  
  > "using the `Background2D` function in the `photutils` python package" (Observations & Data reduction)
- **WebbPSF** : PSF models  
  > "comparing the observed source size to $WebbPSF$ models (cite: Perrin_2014)" (3 Results)
- **mcfost** : Radiative transfer models  
  > "`mcfost` (cite: Pinte_2006; Pinte_2009)" (Software)
- **CARTA** : Visualizing ALMA data  
  > "`CARTA` (cite: comrie_carta_2021)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dark lane thickness at 0.6 micron | 0.42 | 0.01 | arcsec | 2 | / 0.6 / $0.42 \pm 0.01$ / 3.0 / |
| Dark lane thickness at 4.44 micron | 0.21 | 0.01 | arcsec | 2 | / 4.44 / $0.21 \pm 0.01$ / 3.8 / |
| Deconvolved central source FWHM at 7.7 micron | 0.37 (54 au) | not stated | arcsec | 3 | / 7.7 / 0.44 / 0.24 / 0.37, 54 / |
| Deconvolved central source FWHM at 21 micron | 0.83 (122 au) | not stated | arcsec | 3 | / 21.0 / 1.09 / 0.71 / 0.83, 122 / |
| Flux 7.5x4.5 arcsec at 21 micron | 35.2 | 1.1 | mJy | 3 | / 21.0 / $35.2 \pm 1.1$ / $28.5 \pm 0.9$ / |

## Qualitative findings

- Beyond 4.4 micron the scattering nebulae vanish, a compact resolved central source appears and patchy extended emission reaches about twice the HST scattered light radii  
  > "Starting at 7.7$\mu$m however, 1) the two linear nebulosities flanking the dark lane disappear;" (abstract)

## Claim tuples

- H: Do upper layers of Oph163131 contain grains larger than ~1 micron? | E: Compared dark lane thickness vs wavelength to radiative transfer models | R: Thickness drops by factor of 2 from 0.6 to 4.4 micron; models with 10 micron grains in surface layers are insufficiently chromatic | F: Surface layers are depleted of grains larger than ~1 micron | **supported**
- H: Can a thick inner disk explain the sudden compact source at 7.7 micron? | E: Toy radiative transfer model with massive, vertically extended inner 10 au | R: Reproduces sharp transition between 4.4 and 7.7 micron but not the size increase | F: Compact source likely scattered thermal emission from star and inner disk | **partially**
- H: What is the extended patchy emission? | E: Morphology compared with CO and other disks | R: No sharp-edged structures | F: Argues against shocks; suggests photoexcitation or stochastic heating | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Optical or instrumental origin of extended emission ruled out; thermal continuum origin deemed unlikely  
  > "the observed morphology has to be astrophysical." (3 Results)
- How they decided it was enough: _not stated_
- Limitation (authors): No model perfectly fits dark lane chromaticity or lateral profile; the toy model does not reproduce the size increase  
  > "we note that none of the models perfectly fit the evolution of the dark lane thickness with wavelength." (4.1 Chromaticity)
- Caveat (inferred, ours): Qualitative model comparison without a quantitative fit or uncertainties
- Caveat (inferred, ours): Settling parametrization simplistic; models degenerate
- Caveat (inferred, ours): ALMA data play only an overlay role

## Reproducibility

- Data public (paper): JWST data from MAST, HST from archive; ALMA project codes given  
  > "we obtained the phase 2 pipeline calibrated data from the MAST archive" (Observations & Data reduction)
- Products in archive: _not stated_
- Missing: mcfost input parameters and stellar properties
- Missing: Aperture and spine fitting details
- Missing: ALMA processing
- Data volume (inferred): ~ few GB for JWST and HST images; ALMA not needed
- Score (inferred): 3/5, JWST reduction well specified, but ALMA role minor and modeling details sparse.
- Rediscovery candidate: no, Main results are JWST and model based, not ALMA analysis; modeling recipe incomplete.

## Links

- Method: Duchene_2023 (Spine fitting and model approach)
- Method: Villenave_2023b (Spine fitting method)
- Companion: Wolff_2021 (HST data and model A)
- Companion: Villenave_2022 (ALMA continuum modeling)
- Companion: Flores_2021 (ALMA CO temperature structure)
- Related: JWST GO 2562
- Related: JWST GO 4290
- Related: HST program 12514

## Checks

```json
{
 "quotes": 45,
 "quotes_ok": 45,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 32,
  "rate": 0.421
 },
 "evidence_ok": true
}
```

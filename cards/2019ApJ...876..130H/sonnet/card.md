# ALMA Reveals Potential Evidence for Spiral Arms, Bars, and Rings in High-redshift Submillimeter Galaxies

`2019ApJ...876..130H` | The Astrophysical Journal 2019 | first author: Hodge, J. A. | arXiv: 1810.12307 | DOI: 10.3847/1538-4357/ab1846

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Does sub-kpc-resolution 870 um continuum imaging of ALESS SMGs reveal substructure (clumps, bars, rings, spiral arms), and what does it imply for star formation rate density relative to the Eddington limit?  
  > "we present high-resolution ($\sim$0.07$''$), high-fidelity ALMA imaging of the submillimeter emission (rest-frame FIR emission) from six SMGs at redshifts $1.5<z<4.9$" (1 INTRODUCTION)
- Target **ALESS 3.1, 9.1, 15.1, 17.1, 76.1, 112.1**: coordinates _not stated_; z/distance z = 1.539–4.867 (ALESS 15.1 photometric z = 2.67)  
  > "| ALESS 3.1 | 3.374 | CO(4–3) |" (Table 1); "| ALESS 112.1 | 2.315 | Ly$\alpha$ |" (Table 1); distance from Optical/UV spectroscopic z from Danielson2017; CO z from Weiss/Wardlow in prep; photo-z from daCunha2015  
  > "| ALESS 3.1 | 3.374 | CO(4–3) |" (Table 1); "| ALESS 112.1 | 2.315 | Ly$\alpha$ |" (Table 1)

## Data provenance

- ALMA projects: 2016.1.00048.S, 2011.1.00294.S
- bands: Band 7 (870 um), TDM  
  > "We utilized ALMA’s Band 7 in Time Division Mode (TDM)." (2.1 ALMA Sample Selection & Observations)
- frequencies and spectral setup: centered 344 GHz, 4x128 dual polarization channels covering 8 GHz  
  > "This setup centered at 344 GHz (870 $\mu$m) with 4$\times$128 dual polarization channels covering the 8 GHz bandwidth." (2.1 ALMA Sample Selection & Observations)
- continuum bandwidth: _not stated_
- arrays: ALMA 12m, average 45 antennas (42–47)  
  > "The average number of antennas present during the observations was 45 (with a range of 42–47)." (2.1 ALMA Sample Selection & Observations)
- configurations: _not stated_
- baselines: max baseline 3.7 km; 5th percentile uv-distance 200 m  
  > "The observations were carried out in an extended configuration, with a maximum baseline of 3.7 km." (2.1 ALMA Sample Selection & Observations)
- angular resolution: 0.08"x0.06" beam (R=+0.5)  
  > "produced images with a synthesized beam size of 0.08$''$$\times$0.06$''$ and a typical RMS noise of 23 $\mu$Jy beam$^{-1}$" (2.2 ALMA Data Reduction & Imaging)
- max recoverable scale: 0.9" (~7.5 kpc at z~2.5)  
  > "giving a maximum recoverable scale (MRS) of 0.9$''$ according to Equation 7.7 of the ALMA Cycle 4 Technical Handbook" (2.1 ALMA Sample Selection & Observations)
- sensitivity: typical rms 23 uJy/beam  
  > "a typical RMS noise of 23 $\mu$Jy beam$^{-1}$" (2.2 ALMA Data Reduction & Imaging)
- time on source: ~50 minutes per target  
  > "The total on-source time for each of the science targets was approximately 50 minutes" (2.1 ALMA Sample Selection & Observations)
- observing dates: 28 July to 27 Aug 2017, six observing blocks  
  > "taken in six observing blocks from 28 July to 27 Aug 2017" (2.1 ALMA Sample Selection & Observations)
- pi or archival as stated: _not stated_
- Other facility **HST (CANDELS and own program)**: H160 and I814 imaging for comparison with ALMA  
  > "We include in our analysis *HST* imaging from the Cosmic Assembly Near-infrared Deep Extragalactic Legacy Survey" (2.3 HST Imaging)
- Other facility **ALMA Cycle 0 and 0.16" data**: Total flux densities (Cycle 0) and lower-resolution data concatenated  
  > "the data were combined with the lower-resolution ($\sim$0.16$''$), lower-sensitivity data previously obtained for these sources at the same frequency and presented in (cite: Hodge2016)" (2.2 ALMA Data Reduction & Imaging)
- External data: Redshifts (optical/UV spectroscopic)  
  > "Rest-frame optical/UV-based spectroscopic redshifts are from (cite: Danielson2017)" (Table 1) [from (cite: Danielson2017)]
- External data: SED-derived stellar masses, SFRs, dust temperatures (updated with Band 4)  
  > "Stellar masses, SFRs, and luminosity-averaged dust temperatures are from multi-wavelength SED fits which were updated from those presented in (cite: daCunha2015)" (Table 1) [from (cite: daCunha2015); da Cunha et al. in prep.]
- External data: Cycle 0 total 870 um flux densities  
  > "flux densities measured from the compact-configuration ($\sim$1.6$''$) Cycle 0 observations (cite: Hodge2013a)" (2.2 ALMA Data Reduction & Imaging) [from (cite: Hodge2013a)]
- External data: Local U/LIRG Sigma_SFR values for comparison  
  > "22 local luminous and ultra-luminous galaxies (U/LIRGs) from (cite: BarcosMunoz2017)" (4.1 The intensity of the star formation) [from (cite: BarcosMunoz2017)]

## Processing

### Calibration

- pipeline or manual: Pipeline-calibrated data used without further modification or flagging  
  > "Inspection of the pipeline-calibrated data tables revealed data of high quality, and the $uv$-data were therefore used without further modification to the calibration scheme or flagging." (2.2 ALMA Data Reduction & Imaging)
- casa version: CASA 4.7  
  > "(casa) version 4.7" (2.2 ALMA Data Reduction & Imaging)
- pipeline version: _not stated_
- archive products used as is: Delivered pipeline-calibrated uv-data used as is  
  > "the $uv$-data were therefore used without further modification to the calibration scheme or flagging" (2.2 ALMA Data Reduction & Imaging)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean, multi-scale  
  > "Imaging of the combined data was done using casa’s clean task and multi-scale clean" (2.2 ALMA Data Reduction & Imaging)
- deconvolver: multi-scale clean, geometric progression of scales  
  > "we employed a geometric progression of scales, as recommended, and we found that the exact scales used did not affect the outcome" (2.2 ALMA Data Reduction & Imaging)
- weighting robust: Briggs, R = +0.5 (reference)  
  > "Briggs weighting (cite: Briggs1999) and a robust parameter of $R = +0.5$" (2.2 ALMA Data Reduction & Imaging)
- uv taper: 0.3" taper for flux recovery test  
  > "we $uv$-tapered the concatenated data to 0.3$''$, cleaned them interactively, and measured the integrated flux densities" (2.2 ALMA Data Reduction & Imaging)
- cell size: _not stated_
- image size: _not stated_
- masking: interactive tight clean boxes, clean to 1.5 sigma  
  > "Cleaning was done interactively by defining tight clean boxes around the sources and cleaning down to 1.5$\sigma$." (2.2 ALMA Data Reduction & Imaging)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Concatenated with earlier 0.16" data  
  > "Prior to imaging, the data were combined with the lower-resolution ($\sim$0.16$''$)" (2.2 ALMA Data Reduction & Imaging)
- smoothing: _not stated_
- final beam: 0.08"x0.06" at R=+0.5; 0.07" and 0.05" maps also used  
  > "synthesized beam size of 0.08$''$$\times$0.06$''$" (2.2 ALMA Data Reduction & Imaging)
- final rms: 23 uJy/beam  
  > "a typical RMS noise of 23 $\mu$Jy beam$^{-1}$" (2.2 ALMA Data Reduction & Imaging)

### Inherited from earlier work

- Spectral setup identical to Cycle 0 and 0.16" observations  
  > "we utilized a spectral setup identical to the original Cycle 0 ALESS observations of these galaxies (cite: Hodge2013a)" (2.1 ALMA Sample Selection & Observations) [from (cite: Hodge2013a); (cite: Hodge2016)]
- Sigma_SFR mapping technique: scale total SED SFR by per-beam flux fraction  
  > "scaling the total SFR by the observed-to-total ALMA 870 $\mu$m flux density per beam across a source" (3.3 Star formation rate surface density maps) [from (cite: Hodge2015; Hatsukade2015; Chen2017; Canameras2017)]
- Jeans length velocity dispersion method  
  > "Following (cite: Gullberg2018) and estimating the gas surface density from the global $\Sigma_{\rm SFR}$" (4.2 Dusty substructure in SMGs) [from (cite: Gullberg2018)]
- Eddington flux in optically thick limit  
  > "the Eddington flux is then shown by (cite: Andrews2011) to be" (4.1 The intensity of the star formation) [from (cite: Andrews2011)]

### Not stated but needed to reproduce (our reading)

- multi-scale clean scale values
- clean threshold/niter and mask definitions per source
- image size and cell size
- weighting and taper details for 0.07" and 0.05" maps
- the SFR values for each source needed for Sigma_SFR maps (da Cunha et al. in prep)
- dust-to-gas ratio source (referred to as 'same as above' but not given)
- Toomre/Jeans calculation details (gas surface density conversion, kappa)
- galfit initial parameters and mask convergence settings
- how clump positions/ring radii were measured
- continuum flagging/line-free channels, flux calibrator

## Analysis recipe

1. **Image combined ALMA data**: CASA clean with multi-scale deconvolution, Briggs weighting, interactive tight boxes cleaned to 1.5 sigma; concatenated with 0.16" data  
  > "Imaging of the combined data was done using casa’s clean task and multi-scale clean" (2.2 ALMA Data Reduction & Imaging)
   - software: CASA
   - parameter: R = +0.5 gives 0.08"x0.06", rms 23 uJy/beam  
  > "a robust parameter of $R = +0.5$ – generally a good compromise between resolution and sensitivity" (2.2 ALMA Data Reduction & Imaging)
   - fitting: _not stated_
   - validation: Compared with and without multi-scale clean; residuals checked; structures also seen in dirty maps  
  > "We note that all visible structures were evident also in the dirty maps, indicating that they are not artifacts of the CLEANing process." (3.2 Sub-kpc FIR structure)
2. **Test recovered flux**: uv-taper to 0.3", measure integrated flux, compare with Cycle 0 flux  
  > "To test this, we $uv$-tapered the concatenated data to 0.3$''$, cleaned them interactively, and measured the integrated flux densities" (2.2 ALMA Data Reduction & Imaging)
   - software: CASA
   - fitting: _not stated_
   - validation: Recovered fractions 0.78–1.06  
  > "| ALESS 76.1  |    6.4$\pm$0.6    |        5.0$\pm$0.1        |   0.78$\pm$0.07    |" (Table 2)
3. **Fit smooth disk and identify substructures**: 2D Sérsic fits in galfit with iterative masking of residual pixels >5 sigma until masks converge; structures are those exceeding largest negative residual peak; 2D Gaussian fits for structure properties  
  > "we fit the galaxies with two-dimensional Sérsic profiles in galfit (cite: Peng2002; Peng2010), masking residual pixels $>$5$\sigma$ iteratively until the masks converged." (3.2 Sub-kpc FIR structure)
   - software: galfit
   - fitting: galfit Sérsic; Gaussian fits in image plane; ~20% median systematic error from residual structure  
  > "Based on two-dimensional Gaussian fits in the image plane, these structures individually make up a few percent ($\sim$1–8%) of the total continuum emission" (3.2 Sub-kpc FIR structure)
   - validation: Comparison of Sérsic parameters with unmasked and lower-resolution fits  
  > "half-light radii consistent with, and Sérsic indices that are on-average slightly higher than, those derived without the masking procedure" (3.2 Sub-kpc FIR structure)
4. **Build Sigma_SFR maps**: Scale SED-derived total SFR by per-beam fraction of total 870 um flux; galaxy-average = 0.5xSFR/(pi Re^2)  
  > "galaxy-averaged values calculated using the half-light radii as 0.5$\times$SFR/($\pi$R$_{e}^{2}$)" (3.3 Star formation rate surface density maps)
   - assumption: no variations in dust temperature or emissivity index within sources; FIR emission from star formation not AGN  
  > "it effectively assumes that there are no variations in dust temperature (T$_{\rm d}$) or emissivity index ($\beta$) within the sources" (3.3 Star formation rate surface density maps)
   - fitting: _not stated_
   - validation: SFR range cross-checked with modified blackbody + Kennicutt98 relation (cited)  
  > "instead using simple modified blackbody fits with, e.g., the (cite: Kennicutt1998) IR SFR relation (re-scaled to the (cite: Chabrier2003) IMF) returns the same results" (3.3 Star formation rate surface density maps)
5. **Compare to Eddington limit**: Estimate optical depth from peak intensity and MAGPHYS dust T; adopt optically thick Eddington flux of Andrews & Thompson, convert to SFR density, compare with Sigma_SFR and local U/LIRGs  
  > "we derive a lower limit on the Eddington-limited $\Sigma_{\mathrm{SFR}}$ of $\sim$650 M$_{\odot}$ yr$^{-1}$ kpc$^{-2}$" (4.1 The intensity of the star formation)
   - assumption: gas fraction of unity, dust-to-gas 1/90, global dust temperature, Kennicutt98 IR SFR calibration with Chabrier IMF  
  > "Assuming the same dust-to-gas ratio as above (1/90) and adopting a gas fraction of unity as the most extreme scenario" (4.1 The intensity of the star formation)
   - fitting: _not stated_
   - validation: _not stated_
6. **Velocity dispersion constraints (Jeans, Toomre)**: Jeans length equal to largest clump size gives lower limit; Toomre Q<1 with flat-rotation-curve epicyclic frequency gives upper limit; gas surface density from global Sigma_SFR  
  > "we derive upper limits for the one-dimensional velocity dispersion of the potentially barred sources of $\sigma_{\rm r} \lesssim$ 70–160 km s$^{-1}$" (4.3 Evidence for interaction, bars, rings, and spiral arms?)
   - assumption: gas disk dominates over stellar component; radius = HWHM of ALMA emission along major axis  
  > "Here we assume that the gas disk dominates over the stellar component." (4.3 Evidence for interaction, bars, rings, and spiral arms?)
   - fitting: _not stated_
   - validation: Toomre upper limits marginally consistent with Jeans lower limits  
  > "these Toomre-based upper limits are consistent, albeit marginally, with the lower limits derived from equating the sizes of the largest ‘clumps’ observed to the Jeans length" (4.3 Evidence for interaction, bars, rings, and spiral arms?)

## Software

- **CASA** 4.7: data reduction and imaging  
  > "reduced and imaged using the Common Astronomy Software Application[^1] (casa) version 4.7" (2.2 ALMA Data Reduction & Imaging)
- **galfit** : 2D Sérsic fitting of continuum  
  > "we fit the galaxies with two-dimensional Sérsic profiles in galfit" (3.2 Sub-kpc FIR structure)
- **MAGPHYS** : SED fits giving dust temperatures  
  > "the (global) dust temperature measured from the SEDs by MAGPHYS" (4.1 The intensity of the star formation)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median OLR/CR (ring/bar radius ratio) | 1.9 | 0.3 | dimensionless | 3 | resulting in a median ratio of the two sizes (interpreted here as OLR/CR) of 1.9$\pm$0.3 |
| Mean Sérsic index | 1.3 | 0.3 | dimensionless | 3 | typically disk-like ($<n>$=1.3$\pm$0.3) |
| Combined flux fraction of structures per galaxy | ~2–20% | ~20% systematic | percent | 3 | with a combined contribution of $\sim$2–20% for a given galaxy |
| Eddington-limited Sigma_SFR lower limit | ~650 | not stated | Msun/yr/kpc^2 | 5 | lower limit on the Eddington-limited $\Sigma_{\mathrm{SFR}}$ of $\sim$650 M$_{\odot}$ yr$^{-1}$ kpc$^{-2}$ |
| Peak Sigma_SFR at 0.07" for ALESS 9.1 | 547 | +102/-93 | Msun/yr/kpc^2 | 4 | / ALESS 9.1 / 102$^{+27}_{-32}$ / 547$^{+102}_{-93}$ / 575$^{+116}_{-108}$ / |
| Toomre velocity dispersion upper limits | <70–160 | not stated | km/s | 6 | / ALESS 76.1  /           $>$100            /        $<$160         / |
| Bar radii | 0.7–1.0 | ±0.1 | kpc | 3 | / ALESS 17.1 /   1.0$\pm$0.1    /    1.9$\pm$0.1    /    1.5$\pm$0.2     / |

## Qualitative findings

- Dust emission is disk-dominated with sub-kpc structures; ALMA emission is more compact than HST and offset from it  
  > "We report evidence for robust sub-kpc structure on underlying exponential disks." (Summary)
- No SMG exceeds the radiation-pressure Eddington limit on ~500 pc scales  
  > "even on 500 pc scales, they do not exceed the Eddington limit set by radiation pressure on dust" (Summary)

## Claim tuples

- H: Do SMG dust disks host sub-kpc structure? | E: 0.07" 870 um imaging plus galfit Sérsic subtraction | R: 1–5 residual structures per source at ~4–15 sigma, sizes up to ~1.1 kpc, 2–20% of flux | F: Sub-kpc structures exist within exponential disks but are not the dominant star formation sites | **supported**
- H: Are the morphologies suggestive of bars, rings and spiral arms? | E: Examine curvature and clump pairs; measure ring/bar radii | R: Ring/bar ratio 1.9±0.3, agreeing with local OLR/CR | F: Potential bars/rings/spirals, requiring kinematic confirmation | **partially**
- H: Do SMGs reach the Eddington limit at 500 pc? | E: Sigma_SFR maps compared with ~650 Msun/yr/kpc^2 limit and local U/LIRGs | R: No source exceeds the limit | F: SMGs sustain high Sigma_SFR over larger scales but remain sub-Eddington at 500 pc | **supported**

## Reasoning

- Why this data: Six submillimeter-brightest sources from 16 ALESS SMGs with 0.16" imaging to maximize S/N; no morphology pre-selection  
  > "the six SMGs were selected as the submillimeter-brightest sources from the 16 ALESS SMGs with previous high-resolution (0.16$''$) 870 $\mu$m ALMA imaging" (2.1 ALMA Sample Selection & Observations)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Single dust temperature assumed across sources, affecting Sigma_SFR maps  
  > "One important caveat in the above analysis is the previously stated assumption of a single dust temperature across the sources." (4.1 The intensity of the star formation)
- Limitation (authors): Interpretations require kinematic confirmation; small sample  
  > "a larger sample size is important for moving beyond the handful of submillimeter-brightest sources studied here" (Summary)
- Caveat (inferred, ours): Structures at 4–8 sigma peak may be noise or residuals of imperfect Sérsic model
- Caveat (inferred, ours): Bar/ring/spiral interpretation rests on morphology only, without kinematics
- Caveat (inferred, ours): Sample of six is small and bright-biased
- Caveat (inferred, ours): SFR and Sigma_SFR depend on SED and constant-temperature assumption

## Reproducibility

- Data public (paper): Project IDs given; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00048.S, and ADS/JAO.ALMA#2011.1.00294.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: clean parameters (scales, niter, cell, imsize, threshold)
- Missing: SFRs from unpublished SED fits (da Cunha et al. in prep)
- Missing: redshifts from in-prep CO work
- Missing: galfit setup and structure selection details
- Data volume (inferred): ~50-100 GB (six 8 GHz TDM EBs in extended config plus archival Cycle 0 and 0.16" data)
- Score (inferred): 3/5, Data are linked to project codes and the imaging recipe is mostly given, but key clean parameters and SED inputs are unstated.
- Rediscovery candidate: no, Key inputs (SFRs, redshifts) come from in-prep works and imaging parameters are incomplete; interpretation is qualitative in part.

## Links

- Method: (cite: Hodge2016) (Earlier 0.16" imaging of same sources and same spectral setup)
- Method: (cite: Peng2002; Peng2010) (galfit)
- Companion: (cite: Hodge2013a) (Cycle 0 ALESS survey observations)
- Companion: (cite: daCunha2015) (SED fits of ALESS sample)
- Related: ALESS
- Related: ECDFS LABOCA survey
- Related: CANDELS

## Checks

```json
{
 "quotes": 73,
 "quotes_ok": 73,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.1.00294.S"
 ],
 "obscore_codes_not_in_card": [
  "2012.1.00307.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 58,
  "rate": 0.707
 },
 "evidence_ok": true
}
```

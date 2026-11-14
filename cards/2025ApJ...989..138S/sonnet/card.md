# A First Look at Spatially Resolved Infrared Supernova Remnants in M33 with JWST

`2025ApJ...989..138S` | The Astrophysical Journal 2025 | first author: Sarbadhicary, Sumit K. | arXiv: 2410.11821 | DOI: 10.3847/1538-4357/adec7a

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, milky_way_ism
- Question: What do supernova remnants in M33 look like in JWST NIRCam/MIRI images, and how does their IR detectability correlate with multi-wavelength properties and progenitor properties?  
  > "we mainly study the visibility and spatially-resolved structures in the JWST images, and how their appearances correlate with their known properties from other multi-wavelength surveys." (2.5 Methodology)
- Target **M33 supernova remnants (e.g. L10-036, L10-118, LL14-168)**: coordinates _not stated_; z/distance 840 kpc  
  > "Throughout the paper, we adopt a distance to M33 of 840 kpc (cite: Freedman2001)." (2 Observations and Methodology); distance from Freedman et al. 2001  
  > "Throughout the paper, we adopt a distance to M33 of 840 kpc (cite: Freedman2001)." (2 Observations and Methodology)

## Data provenance

- ALMA projects: 2018.1.00378.S, 2022.1.00276.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12m+7m+total power (CO(1-0), project 2022.1.00276.S)  
  > "which surveyed the PHATTER region (section [2.4](#sec:obs:hstsfh)) using the 12m+7m+total power arrays." (2.3.2 Additional Radio/mm data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: CO(2-1) 0.5'' (2 pc); CO(1-0) synthesized beam 3.9''  
  > "The resulting data have a synthesized beam FWHM of $3.9''$, a velocity channel width of 1.3 km s$^{-1}$, and a typical noise value of 0.3 K in each channel." (2.3.2 Additional Radio/mm data)
- max recoverable scale: _not stated_
- sensitivity: CO(2-1) rms 38 mK per 1.2 km/s channel; CO(1-0) 0.3 K per channel  
  > "The CO data cube has an rms of 38 mK per $1.2$ km s$^{-1}$ channel." (2.3.2 Additional Radio/mm data)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (not stated)
- Line: CO J=1-0 (not stated)
- Other facility **JWST NIRCam/MIRI**: Primary near/mid-IR imaging of four M33 fields  
  > "we use archival Cycle 1 and 2 JWST datasets covering several regions of M33 in MIRI and NIRCam bands." (2.1 JWST data)
- Other facility **HST PHATTER**: High-resolution broadband images and star-formation histories  
  > "we also make use of the much higher-resolution wide-band HST images from the PHAT Triangulum Extended Region (PHATTER) survey" (2.4 HST Images and Star-formation histories)
- Other facility **LGGS (Mayall)**: Narrowband Halpha, [SII], [OIII] reference images  
  > "Our main reference images are narrowband continuum-subtracted images of H$\alpha$, \[S II\] and \[O III\] from the Local Group Galaxies Survey (LGGS)" (2.3.1 Ground-based Narrowband Images)
- Other facility **VLA LGLBS**: New 1.4 GHz radio continuum images  
  > "We also show new radio continuum 1.4 GHz data taken by the Very Large Array (VLA) for these two SNRs from the Local Group L-Band Survey (LGLBS)." (2.3.2 Additional Radio/mm data)
- External data: M33 SNR catalog  
  > "We use the list of SNRs from (cite: White2019) to cross-reference with our JWST fields." (2.2 Supernova Remnant catalog) [from White2019]
- External data: SNR optical line fluxes, ratios and spectroscopy  
  > "We will particularly rely on measured fluxes and ratios of optical emission lines from (cite: Long2018)" (2.2 Supernova Remnant catalog) [from Long2018]
- External data: Progenitor mass ranges from PHATTER SFHs  
  > "We use the median and 68th percentile progenitor mass range of each SNR reported in Table 2 of K23" (2.4 HST Images and Star-formation histories) [from Koplitz2023]

## Processing

### Calibration

- pipeline or manual: ALMA observatory pipeline (CO(1-0)); CO(2-1) reprocessed from archive  
  > "The data were calibrated using the observatory pipeline (v. 6.5.4.9)" (2.3.2 Additional Radio/mm data)
- casa version: _not stated_
- pipeline version: 6.5.4.9  
  > "The data were calibrated using the observatory pipeline (v. 6.5.4.9)" (2.3.2 Additional Radio/mm data)
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean via PHANGS-ALMA imaging pipeline  
  > "The images shown in this work use CASA’s `tclean` to image and deconvolve the visibilities" (2.3.2 Additional Radio/mm data)
- deconvolver: _not stated_
- weighting robust: Briggs, robust=0.5  
  > "with Brigg’s weighting with `robust=0.5` in $1.2$ km s$^{-1}$ channels." (2.3.2 Additional Radio/mm data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: PHANGS-ALMA 'strict mask' integrated intensity mask  
  > "We create an integrated intensity mask following the PHANGS-ALMA prescription, specifically the “strict mask” criteria." (2.3.2 Additional Radio/mm data)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12m+7m+total power for CO(1-0)  
  > "using the 12m+7m+total power arrays" (2.3.2 Additional Radio/mm data)
- smoothing: _not stated_
- final beam: 3.9'' (CO(1-0))  
  > "The resulting data have a synthesized beam FWHM of $3.9''$" (2.3.2 Additional Radio/mm data)
- final rms: _not stated_

### Inherited from earlier work

- ALMA imaging and masking done with PHANGS-ALMA pipeline  
  > "imaged using the PHANGS-ALMA pipeline (cite: Leroy2021_pipeline) using the same parameter choices as for the CO(2-1) data." (2.3.2 Additional Radio/mm data) [from Leroy2021_pipeline]
- JWST reduction with pjpipe  
  > "Observations were reduced using the `pjpipe` reduction pipeline designed for the Physics at High Angular Resolution in Nearby GalaxieS (PHANGS)-JWST survey" (2.1 JWST data) [from Lee2023; Williams2024; Peltonen2024]

### Not stated but needed to reproduce (our reading)

- CASA version used for ALMA imaging
- Pipeline parameters beyond robust and channel width (cell size, image size, multiscale, clean thresholds)
- Rest frequencies, continuum subtraction for ALMA cubes
- Quantitative criteria for visual SNR detection classes (by-eye)
- Exact PHANGS-ALMA pipeline version

## Analysis recipe

1. **Reprocess ALMA CO cubes**: Archival data imaged with PHANGS-ALMA pipeline using tclean; integrated intensity maps with strict masks  
  > "We reprocessed these data from the ALMA archive and used the PHANGS-ALMA imaging pipeline to make the products presented here" (2.3.2 Additional Radio/mm data)
   - software: CASA, PHANGS-ALMA pipeline
   - parameter: robust=0.5, 1.2 km/s channels  
  > "with Brigg’s weighting with `robust=0.5` in $1.2$ km s$^{-1}$ channels." (2.3.2 Additional Radio/mm data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Visual classification of SNRs in JWST images**: By-eye inspection in DS9 against Halpha/[SII] and HST references, classifying as clear, partial, ambiguous, non-detection  
  > "We carefully inspect the SNR sites in the individual JWST filter images by-eye in DS9, adjusting the stretch and data range" (2.5 Methodology)
   - software: DS9
   - parameter: [SII]/Halpha > 0.4 indicates shock-heated gas  
  > "the former typically has ratios $< 0.4$, while the latter has rations $> 0.4$" (2.5 Methodology)
   - fitting: _not stated_
   - validation: Acknowledged subjective classification  
  > "We note that this classification is somewhat subjective and user-dependent" (2.5 Methodology)

## Software

- **CASA** : ALMA calibration and imaging; VLA imaging  
  > "Both calibration and imaging used CASA (cite: CASA)." (2.3.2 Additional Radio/mm data)
- **pjpipe** : JWST data reduction  
  > "Observations were reduced using the `pjpipe` reduction pipeline" (2.1 JWST data)
- **PHANGS-ALMA pipeline** : Imaging and masking of ALMA CO data  
  > "used the PHANGS-ALMA imaging pipeline to make the products presented here" (2.3.2 Additional Radio/mm data)
- **pyneb** : Convert [SII] doublet ratios to electron densities  
  > "We use the `pyneb` software (cite: pyneb) to convert the \[S II\] doublet ratio values" (Footnote 9)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total SNR detection fraction, Southern Arm MIRI field | 43 | not stated | percent | 2 | giving a clear detection fraction of 14% and total detection fraction of 43% |
| CO(1-0) synthesized beam | 3.9 | not stated | arcsec | 1 | The resulting data have a synthesized beam FWHM of $3.9''$ |
| CO(2-1) cube rms | 38 | not stated | mK per 1.2 km/s channel | 1 | The CO data cube has an rms of 38 mK per $1.2$ km s$^{-1}$ channel. |

## Qualitative findings

- ALMA CO shows dense molecular gas near L10-036, L10-118 and LL14-168, supporting shock interaction with dense ISM  
  > "Signatures of dense ISM traced by ALMA CO and F335M at the location of the molecular emission-rich shocks further corroborate the presence of interaction." (4.4 Evidence of shocks interacting with molecular gas)

## Claim tuples

- H: Are M33 SNRs detectable in JWST MIRI/NIRCam and what governs detectability? | E: Visual inspection of 40 SNRs in four JWST fields compared with optical, radio, X-ray data | R: 43% detected in MIRI field; 1 of 16 in NIRCam; detected SNRs are small, bright, with broad lines and dense surroundings | F: Detectability correlates with dense ISM and fast shocks, not progenitor mass | **supported**
- H: Are SNRs near NGC 604 interacting with molecular gas? | E: F470N/F444W ratio images plus ALMA CO | R: Two SNRs show F470N excess ratios of 2-6 for L10-124 | F: Molecular H2 shocks in the farthest known SNRs | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Visual classification is subjective  
  > "We note that this classification is somewhat subjective and user-dependent" (2.5 Methodology)
- Caveat (inferred, ours): Detection classes are by-eye with no quantitative flux limits
- Caveat (inferred, ours): ALMA data are only qualitative context; no quantitative CO analysis
- Caveat (inferred, ours): Small sample for F770W and NIRCam conclusions

## Reproducibility

- Data public (paper): Archival JWST and ALMA data used  
  > "Our strategy in this paper is to leverage archival JWST observations that happen to overlap with SNRs previously identified" (2 Observations and Methodology)
- Products in archive: _not stated_
- Missing: Detection classification criteria are subjective
- Missing: CASA version and full ALMA imaging parameters
- Data volume (inferred): ~50-100 GB for the two ALMA CO datasets; JWST data additional
- Score (inferred): 3/5, JWST/ALMA data public and pipelines named, but the main result is subjective visual classification and ALMA use is minor.
- Rediscovery candidate: no, ALMA is minor and the main results are by-eye classifications.

## Links

- Method: Leroy2021_pipeline (PHANGS-ALMA imaging pipeline)
- Method: Williams2024 (pjpipe JWST reduction)
- Companion: Koplitz2023 (Progenitor masses of M33 SNRs)
- Companion: Sarbadhicary2023 (Correlation of SNRs with molecular gas in M33)
- Related: PHANGS-ALMA
- Related: PHANGS-JWST
- Related: PHATTER
- Related: LGLBS
- Related: LGGS

## Checks

```json
{
 "quotes": 44,
 "quotes_ok": 44,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 34,
  "rate": 0.515
 },
 "evidence_ok": true
}
```

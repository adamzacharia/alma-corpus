# ALMA Imaging of the CO (6-5) Line Emission in NGC 7130*

`2016ApJ...820..118Z` | The Astrophysical Journal 2016 | first author: Zhao, Yinghe | arXiv: 1602.07070 | DOI: 10.3847/0004-637X/820/2/118

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: Where is the warm dense gas (CO 6-5) relative to dust continuum, AGN radio emission and star formation in the LIRG NGC 7130 at <100 pc scales, and how much does the AGN heat it?  
  > "suggests that the heating contribution of the AGN to the CO (6$-$5) emission in NGC 7130 is negligible." (abstract)
- Target **NGC 7130**: coordinates 21:48:19.50 -34:57:04.7 (J2000)  
  > "| NGC 7130     | 21:48:19.50  | $-$34:57:04.7     | 72.7          | 4842          | Sa pec        | Sy 1.9        | 11.42         |" (Table 1); "At its distance of 72.7 Mpc (Table [1](#obslog); Armus et al. 2009), $1^{\prime\prime}$ corresponds to 352 pc." (1 Introduction); z/distance 72.7 Mpc (cz = 4842 km/s)  
  > "| NGC 7130     | 21:48:19.50  | $-$34:57:04.7     | 72.7          | 4842          | Sa pec        | Sy 1.9        | 11.42         |" (Table 1); "At its distance of 72.7 Mpc (Table [1](#obslog); Armus et al. 2009), $1^{\prime\prime}$ corresponds to 352 pc." (1 Introduction); distance from Armus et al. 2009  
  > "| NGC 7130     | 21:48:19.50  | $-$34:57:04.7     | 72.7          | 4842          | Sa pec        | Sy 1.9        | 11.42         |" (Table 1); "At its distance of 72.7 Mpc (Table [1](#obslog); Armus et al. 2009), $1^{\prime\prime}$ corresponds to 352 pc." (1 Introduction)

## Data provenance

- ALMA projects: 2013.1.00524.S
- bands: Band 9  
  > "using the Band 9 receivers of ALMA in the time division mode" (2 Observations and Data Reduction)
- frequencies and spectral setup: 4 SPWs centered at 680.423, 682.178, 676.693, 678.631 GHz, 2 GHz each; ~6.8 km/s velocity resolution  
  > "were centered at the sky frequencies of 680.423, 682.178, 676.693, and 678.631 GHz, respectively, each with a bandwidth of 2 GHz." (2 Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C34-5  
  > "The observations were carried out in the relatively extended configuration C34-5" (2 Observations and Data Reduction)
- baselines: 25.8-820.2 m  
  > "with the baselines in the range of $25.8-820.2$ m" (2 Observations and Data Reduction)
- angular resolution: 0.20" x 0.14" (70 x 49 pc), PA -79 deg  
  > "with the full width of half maximum (FWHM) of $\sim$$0^{\prime\prime}.20\times0^{\prime\prime}.14$" (2 Observations and Data Reduction)
- max recoverable scale: ~3.1"  
  > "the maximum recoverable scale is $\sim$$3^{\prime\prime}.1$" (2 Observations and Data Reduction)
- sensitivity: 11 mJy/beam per 13.5 km/s channel; continuum 1.3 mJy/beam; moment-0 1.1 Jy/beam km/s  
  > "For the continuum, the $1\sigma$ rms noise is 1.3 mJy beam$^{-1}$" (2 Observations and Data Reduction)
- time on source: 315 s  
  > "The total on-source integration time was 315 seconds." (2 Observations and Data Reduction)
- observing dates: 2014/07/26  
  > "| X87b480_Xa11 | 2014/07/26   | 02:40:41-03:04:14 | C34-5         | 25            | 650           | 315           | 677           |" (Table 1)
- pi or archival as stated: _not stated_
- Line: CO 6-5 (691.473 GHz)
- Other facility **HST**: F210M UV, F160W and extinction-corrected Pa-alpha images  
  > "F160W continuum and Pa-$\alpha$ (Alonso-Herrero et al. 2006; Diáz-Santos et al. 2008)" (3.3 Comparison with Other Observations)
- Other facility **VLA**: 8.4 GHz continuum reduced from archive data  
  > "The radio image was obtained by reducing the raw data downloaded from the NRAO VLA science archive" (3.3 Comparison with Other Observations)
- Other facility **Herschel SPIRE/FTS**: total CO(6-5) flux and 350/500 um fluxes for recovered-flux fractions  
  > "our SPIRE/FTS-measured flux of $1223\pm82$ Jy km s$^{-1}$ (Lu et al. 2015, in preparation)" (3.1 CO (6-5) Emission)
- External data: Herschel SPIRE/FTS total CO(6-5) flux 1223±82 Jy km/s  
  > "our SPIRE/FTS-measured flux of $1223\pm82$ Jy km s$^{-1}$ (Lu et al. 2015, in preparation)" (3.1 CO (6-5) Emission) [from Lu et al. 2015, in preparation]
- External data: HST extinction-corrected Pa-alpha map  
  > "The extinction-corrected Pa-$\alpha$ map was obtained from a set of *HST* near-IR (NIR) narrow- and broad-band images (Diáz-Santos et al. 2008)." (3.3 Comparison with Other Observations) [from Diáz-Santos et al. 2008]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.3.1  
  > "The data were reduced with CASA 4.3.1." (2 Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 7%  
  > "The error in the flux calibration was estimated to be 7%" (2 Observations and Data Reduction)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs weighting (robust value not stated)  
  > "The raw images were cleaned using the Briggs weightings" (2 Observations and Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: flux measurements after PB correction; figures and noise before  
  > "Unless otherwise stated, flux measurements are based on the images after the primary beam correction" (2 Observations and Data Reduction)
- array combination: _not stated_
- smoothing: cubes binned to 13.5 km/s channels  
  > "The spectral cubes were binned into channels with a width of $\delta v=13.5$ km s$^{-1}$." (2 Observations and Data Reduction)
- final beam: 0.20" x 0.14", PA -79 deg  
  > "a position angle (north to east) of $-79^\circ$" (2 Observations and Data Reduction)
- final rms: continuum 1.3 mJy/beam; line map 1.1 Jy/beam km/s  
  > "is 1.1 Jy beam$^{-1}$ km s$^{-1}$" (2 Observations and Data Reduction)

### Inherited from earlier work

- Total continuum flux estimated by interpolating SPIRE 350 and 500 um measurements  
  > "Following a similar procedure (i.e., interpolating the SPIRE measurements at 350 and 500 $\mu$m to obtain the total flux) in Xu et al. (2014, 2015)" (3.2 Continuum Emission at 434 um) [from Xu et al. (2014, 2015)]

### Not stated but needed to reproduce (our reading)

- Briggs robust value, clean threshold, mask and cell/image size
- Calibrators for bandpass and flux
- Line-free channels and continuum subtraction method
- Integration velocity range definition and how moment maps were clipped
- Clumpfind contour levels
- Details of Pa-alpha extinction correction and HST/ALMA registration
- SPIRE 350/500 um fluxes used

## Analysis recipe

1. **Image continuum and CO(6-5) cube**: Continuum from SPWs 1-3; cube from SPW-0 with 800 km/s bandpass, cleaned with Briggs weighting, binned to 13.5 km/s  
  > "The continuum was estimated using data in SPWs 1-3." (2 Observations and Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: Side-lobe check using beam image and simulated images  
  > "the maximum side-lobe level of our observation is around 25%" (2 Observations and Data Reduction)
2. **Identify clumps and make moment maps/spectra**: Clumpfind (Williams et al. 1994) on integrated map; Gaussian fits to regional spectra  
  > "three clumps were found by the clump-finding algorithm of Williams et al. (1994)" (3.1 CO (6-5) Emission)
   - software: Clumpfind
   - fitting: Gaussian line profile fits  
  > "together with the central velocity and FWHM from a Gaussian fit" (3.1 CO (6-5) Emission)
   - validation: Total flux compared with SPIRE/FTS  
  > "which agrees well with our SPIRE/FTS-measured flux" (3.1 CO (6-5) Emission)
3. **Compare with multiwavelength data and estimate AGN contribution**: Overlay on HST and VLA images; CO/radio ratios; CO flux within r=0.2" of radio peak as AGN upper limit  
  > "we measured the CO (6$-$5) flux within the region ($r=0^{\prime\prime}.2$; hereafter A$_{\rm XDR}$) centered at the radio peak" (3.3 Comparison with Other Observations)
   - assumption: XDR region unresolved by ALMA; F160W peak coincides with radio peak  
  > "Assuming that the X-ray dominated region associated with the AGN is unresolved by ALMA" (3.3 Comparison with Other Observations)
   - fitting: _not stated_
   - validation: HST dust lanes coincide with CO  
  > "This indicates that our method for improving the astrometry of the *HST* images is reasonable." (3.3 Comparison with Other Observations)

## Software

- **CASA** 4.3.1: data reduction and imaging  
  > "The data were reduced with CASA 4.3.1." (2 Observations and Data Reduction)
- **Clumpfind** : identify clumps in CO map  
  > "three clumps were found by the clump-finding algorithm of Williams et al. (1994)" (3.1 CO (6-5) Emission)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total CO(6-5) flux | 1230 | 74 | Jy km/s | 2 | The total flux of CO (6$-$5) measured from the integrated image is $1230\pm74$ Jy km s$^{-1}$ |
| 434 um continuum flux density | 814 | 52 | mJy | 1 | $f_{434\,\mu{\rm m,\,ALMA}}=814\pm52$ mJy |
| Fraction of total dust continuum detected | 0.51 | 0.05 | dimensionless | 3 | we estimated about $0.51\pm0.05$ of the total dust continuum is detected |
| CO-to-continuum ratio SW/NE/central | 2100 / 1700 / 1300 | not stated | dimensionless | 2 | The corresponding values of $R_{\rm CO/cont}$ are 2100 (SW), 1700 (NE) and 1300 (central) |
| CO flux in A_XDR as fraction of central region | ~15% | not stated | percent | 3 | it only accounts for $\sim$15% of our ALMA-detected flux within the central region |
| CO-peak to continuum-peak offset | ~0.2 (~70 pc) | not stated | arcsec | 2 | have a small offset of $\sim$0$^{\prime\prime}$.2 (or $\sim$70 pc) |

## Qualitative findings

- CO(6-5) shows a clumpy central region plus NE and SW regions coincident with optical dust lanes, in common rotation.  
  > "The CO (6$-$5)-emiting gas appears to participate in the general rotation of the galaxy disk." (4 Summary)

## Claim tuples

- H: Do CO(6-5) and dust emission trace the same gas on small scales? | E: Compare CO(6-5) and 434 um maps | R: Spatially correlated but ~70 pc peak offset; CO/continuum varies | F: Gas and dust may decouple at ~70 pc | **supported**
- H: Does the AGN heat the CO(6-5)? | E: Compare with VLA radio peak and CO flux within r=0.2" | R: Only ~15% of central CO flux near radio peak; poor correspondence | F: AGN heating is insignificant | **supported**
- H: Does CO(6-5) correlate with SF at <100 pc? | E: Compare with extinction-corrected Pa-alpha | R: Pa-alpha smooth, no clumps matching CO | F: Possible breakdown, uncertain due to extinction correction | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Extinction correction of Pa-alpha uncertain; radio image of limited quality  
  > "the extinction correction for the Pa-$\alpha$ image may suffer from some uncertainties" (3.3 Comparison with Other Observations)
- Caveat (inferred, ours): Single short 315 s observation; no quantitative uncertainty on peak offsets beyond astrometry
- Caveat (inferred, ours): Recovered flux comparison depends on unpublished SPIRE value
- Caveat (inferred, ours): AGN upper limit assumes unresolved XDR and is crude
- Caveat (inferred, ours): Self-registration of HST to radio assumes nucleus coincidence

## Reproducibility

- Data public (paper): ALMA project 2013.1.00524.S cited; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00524.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters (robust, threshold, masks)
- Missing: Clumpfind settings
- Missing: Calibrator names for flux/bandpass
- Missing: HST and SPIRE reduced data
- Data volume (inferred): ~10-30 GB
- Score (inferred): 3/5, Single public dataset and simple analysis, but imaging parameters and external data are unspecified.
- Rediscovery candidate: no, Imaging recipe incomplete and key comparisons depend on non-ALMA data.

## Links

- Method: Williams et al. 1994 (clump-finding algorithm)
- Companion: Xu et al. 2014, 2015 (ALMA CO(6-5) of NGC 34 and NGC 1614, same program and method)
- Companion: Lu et al. 2014 (SPIRE FTS CO ladder, SFR and AGN heating)
- Related: GOALS
- Related: Herschel SPIRE/FTS LIRG sample

## Checks

```json
{
 "quotes": 54,
 "quotes_ok": 54,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 63,
  "stated": 39,
  "rate": 0.619
 },
 "evidence_ok": true
}
```

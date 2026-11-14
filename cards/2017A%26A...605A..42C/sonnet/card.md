# Extended ionised and clumpy gas in a normal galaxy at z = 7.1 revealed by ALMA

`2017A&A...605A..42C` | Astronomy and Astrophysics 2017 | first author: Carniani, S. | arXiv: 1701.03468 | DOI: 10.1051/0004-6361/201630366

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the spatial distribution and nature of [CII] 158um and [OIII] 88um emission in the z=7.1 normal star-forming galaxy BDF-3299, given the [CII] offset from the optical emission seen previously?  
  > "The new ALMA [Cii] observations have a higher angular resolution and, along with the [Oiii] data, enable us to investigate more in detail the properties of the interstellar and circumgalactic medium of this primeval system." (Introduction)
- Target **BDF-3299**: coordinates _not stated_; z/distance z=7.1 (z=7.107)  
  > "the [Oiii] at 88$\mu$m, which is redshifted to 418.5 GHz at $z=7.107$." (Observations); distance from Ly-alpha redshift  
  > "the [Oiii] at 88$\mu$m, which is redshifted to 418.5 GHz at $z=7.107$." (Observations)

## Data provenance

- ALMA projects: 2013.1.00433.S, 2012.1.00719.S, 2012.A.00040.S
- bands: Band 6 (230 GHz) and Band 8 (410 GHz)  
  > "BDF-3299 was observed both in Band 6 (230 GHz) and in Band 8 (410 GHz)." (Observations)
- frequencies and spectral setup: Band 6: FDM, 7.5 GHz total in four 1.875 GHz SPWs, [CII] SPW at 1.95 MHz (~2.5 km/s); Band 8: FDM, 1.95 MHz (~1.4 km/s), [OIII] SPW  
  > "total bandwidth of 7.5 GHz, divided in to four spectral windows (SPWs) of 1.875 GHz." (Observations); "spectral resolution of 1.95 MHz ($\sim 1.4$ ${\rm km/s}$)" (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: Band 6 Cycle 2 longest baseline 1,570 m; Band 8 15-560 m  
  > "baseline length in a range between 15 m and 560 m" (Observations)
- angular resolution: Band 8 0.5x0.4 arcsec; Band 6 C2 0.3x0.2; combined ~0.6 arcsec  
  > "Band 6 Cycle 1+2 | 230 | 7 | 58 | $0.6\ensuremath{''}\times0.5\ensuremath{''}$" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: Band 8 40 uJy/beam continuum; Band 6 Cycle 1+2 7 uJy continuum  
  > "The combined data set results into a continuum sensitivity of 7 $\mu$Jy" (Observations)
- time on source: Band 6 ~3 h; Band 8 ~73 min  
  > "The total on-source observing time was about 73 minutes" (Observations)
- observing dates: Band 6: 2015 June 30 and July 1; Band 8: 2015 May 1 and 15  
  > "Band 8 observations were obtained on 2015 May 1 and 15." (Observations)
- pi or archival as stated: _not stated_
- Line: [CII] 158 um (not stated)
- Line: [OIII] 88 um (418.5 GHz observed at z=7.107)
- Other facility **HST**: F105W (Y-band) imaging, programme 13688, Y_AB=28 limit (S/N=10)  
  > "HST) F105W (Y-band hereafter) imaging of the BDF field obtained under cycle 22 programme 13688" (Observations)
- External data: Cycle 1 Band 6 [CII] data and flux aperture correction  
  > "we applied the aperture correction estimated by using the bright serendipitous source as in (cite: Maiolino:2015)." ([Cii] emission) [from (cite: Maiolino:2015)]
- External data: [OIII]-SFR and [CII]-SFR relations for metal-poor galaxies  
  > "relation between SFR and [Oiii] luminosity for metal poor galaxies found by (cite: De-Looze:2014)" (Nature of emitting regions) [from (cite: De-Looze:2014)]
- Simulation/model as data: Vallini et al. model of [CII]/[OIII] from molecular clouds vs incident FUV flux, Z=0.2 Zsun  
  > "By using the model by (cite: Vallini:2016), we can quantify the maximum gas mass contained in BDF-3299" (Lack of far-IR emission)

## Processing

### Calibration

- pipeline or manual: CASA calibration; phase calibrator J2223-3137 unusable in Band 6, bandpass calibrator J2258-2758 used as phase calibrator  
  > "We therefore used the bandpass calibrator J2258-2758, which was observed regularly during the ALMA programme, as phase calibrator in Band 6." (Observations)
- casa version: v4.5.3  
  > "Band 8 and 6 data were calibrated by using the casa software version v4.5.3." (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune and Ceres  
  > "Neptune and Ceres were observed as flux calibrators" (Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "We produced final continuum images and cubes with the routine clean" (Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "selecting a natural weighting to optimise the sensitivity" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Continuum cleaned with 500 iterations; no cleaning of cubes  
  > "No cleaning was performed in any cube" (Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Primary beam FWHM 16 arcsec (Band 8), 22 arcsec (Band 6)  
  > "Band 8 Cycle 2 | 410 | 40 | 260 | $0.5\ensuremath{''}\times0.4\ensuremath{''}$ |  | 16$''$" (Table 1)
- array combination: Cycle 1 and Cycle 2 Band 6 visibilities combined, weights manually rescaled to match noise variance  
  > "we manually re-scaled their relative weights so that they matched the noise variance measured in the two datasets." (Observations)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- HST-ALMA alignment: ~0.4 arcsec shift of Y-band to South-East from serendipitous sources  
  > "Following (cite: Maiolino:2015) we matched the ALMA observations to the HST images" (Observations) [from (cite: Maiolino:2015)]
- [CII] flux extraction aperture and aperture correction  
  > "The flux is extracted in the same aperture as the spectrum in (cite: Maiolino:2015)" ([Cii] emission) [from (cite: Maiolino:2015)]
- Dust temperature range 25-45 K  
  > "Assuming a dust temperature range between 25 K and 45 K (cite: Schaerer:2015a)" (Continuum emission) [from (cite: Schaerer:2015a)]
- FIR-SFR conversion  
  > "we adopt the “standard” FIR–SFR conversion factor for local galaxies (cite: Kennicutt:2012)" (Continuum emission) [from (cite: Kennicutt:2012)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum subtraction method for cubes
- Cell size, image size and mask for continuum cleaning
- Flux extraction apertures for [OIII] clumps
- Details of the blind line-search algorithm (smoothing, source extraction, noise simulation)
- Exact weights used when combining Cycle 1 and 2
- Cycle 1 data processing details
- Dust-mass and L_FIR calculation details (beta, opacity)
- Details of the Vallini model runs

## Analysis recipe

1. **calibrate and image Band 6 and 8 data**: CASA calibration; clean with natural weighting; combine Cycle 1 and 2 Band 6 visibilities  
  > "We produced final continuum images and cubes with the routine clean, selecting a natural weighting to optimise the sensitivity." (Observations)
   - software: CASA
   - parameter: 500 clean iterations for continuum; no cube cleaning  
  > "the cleaning of the continuum maps was performed with 500 iterations." (Observations)
   - fitting: _not stated_
   - validation: astrometry checked with serendipitous source seen in Bands 6 and 8  
  > "its centroid position is consistent with that in Band 6" ([Oiii] emission)
2. **continuum limits on dust and SFR**: 2 sigma upper limit on L_FIR from non-detection, converted to SFR  
  > "we derive a 2$\sigma$ upper limit estimates for the infrared luminosity $L_{\rm FIR}<10^{11}$ L$_{\odot}$." (Continuum emission)
   - assumption: Td 25-45 K; Kennicutt & Evans FIR-SFR  
  > "Assuming a dust temperature range between 25 K and 45 K (cite: Schaerer:2015a)" (Continuum emission)
   - fitting: _not stated_
   - validation: _not stated_
3. **measure [CII] in low, high and combined resolution datasets**: Extract spectra and maps; line flux with aperture correction; compare datasets  
  > "By integrating the line under the shaded gold region, we obtain a significance of the detection of 6.5" ([Cii] emission)
   - fitting: _not stated_
   - validation: consistency with Cycle 1 flux  
  > "the integrated flux obtained from the combined observations (Table 2) is consistent with the estimates obtained by the low angular resolution data alone" ([Cii] emission)
4. **detect [OIII] clumps and test reliability**: Blind search for positive and negative peaks in rebinned cube (30-300 km/s, S/N=4), compared with 100 simulated blank cubes  
  > "We simulated 100 blank datacubes similar to the real data and we applied on them the same source extraction algorithm" (Reliability of [Oiii] detections)
   - parameter: |v|<500 km/s from Lya; primary beam FWHM 16 arcsec; exclude 2 arcsec around serendipitous source  
  > "We excluded the region within 2$''$ from the continuum serendipitous source" (Reliability of [Oiii] detections)
   - fitting: _not stated_
   - validation: negative emitters below 6 sigma; 3 positives >6 sigma  
  > "the negative line emitters have a line flux with a level of confidence below $6\sigma$" (Reliability of [Oiii] detections)
5. **interpret with models and SFR relations**: Compare luminosities with Vallini et al. 2016 model vs FUV field; STARBURST99 for FUV; De Looze relations; Calzetti reddening  
  > "The FUV density field in BDF-3299 can be estimated by using STARBURST99" (Lack of far-IR emission)
   - software: STARBURST99
   - parameter: FUV luminosity ~3e43 erg/s; size ~1 kpc; ~1e3 G0; ~150 G0 at 3.5 kpc  
  > "we obtain an intensity of the UV radiation field of $\sim 150\, G_{0}$" (Nature of emitting regions)
   - assumption: Z=0.2 Zsun baseline; 100 km/s line width for upper limits  
  > "we assume a line width of 100 km/s" (Lack of far-IR emission)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.5.3: calibration and imaging  
  > "Band 8 and 6 data were calibrated by using the casa software version v4.5.3." (Observations)
- **STARBURST99** : FUV density field of BDF-3299  
  > "The FUV density field in ${\rm BDF-3299}$ can be estimated by using STARBURST99" (Lack of far-IR emission)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Combined [CII] flux | 39 | 6 | mJy km/s | 3 | Flux$^\star$ [mJy km/s] /   $49\pm7$   /  $15\pm8$   /   $39\pm6$ |
| Combined [CII] FWHM | 75 | 20 | km/s | 3 | (FWHM = $75\pm$20 km/s) |
| Fraction of [CII] flux extended/diffuse | 70 | 20 | % | 3 | about 70% ($\pm$20%) of the flux in the [Cii] system is extended and diffuse |
| [OIII] clump-I flux | 85 | 12 | mJy km/s | 4 | clump-I / 7.2 / 5.0 / $40\pm10$ / $440\pm5$ / $85\pm12$ / $1.8\pm0.2$ / 0.7 |
| [OIII] clump-II flux | 100 | 14 | mJy km/s | 4 | clump-II / 6.9 / 5.3 / $40\pm10$ / $32\pm5$ / $100\pm14$ |
| [OIII] clump-III flux | 260 | 40 | mJy km/s | 4 | clump-III / 6.7 / 5.6 / $80\pm10$ / $110\pm10$ / $260\pm40$ |
| L_FIR upper limit (2 sigma) | <1e11 | not stated | Lsun | 2 | $L_{\rm FIR}<10^{11}$ L$_{\odot}$ |
| IR-derived SFR upper limit (2 sigma) | <12 | not stated | Msun/yr | 2 | SFR$<$12 M$_{\odot}$ yr$^{-1}$ |
| [OIII] luminosity upper limit at UV location | <5.5e7 | not stated | Lsun | 5 | L_{\rm [O\textsc{iii}]} }$$<5.5\times10^{7}$ L$_{\odot}$ |
| Gas mass upper limit of BDF-3299 | <1e9 | not stated | Msun | 5 | we conclude that the gas mass in BDF-3299 is less than $10^{9}$ $\mathrm{M}_{\odot}$ |
| SFR of clump-I from [OIII] | 7.5 | not stated | Msun/yr | 5 | yields a SFR of about 7.5 M$_{\odot}$ yr$^{-1}$ |
| [OIII]-[CII] peak offset | 0.2 | 0.15 (position) | arcsec | 4 | the two emission peaks being offset by 0.2$''$  ($\sim$1 kpc) |

## Qualitative findings

- Offsets between far-IR lines and optical emission are common and do not correlate with SFR  
  > "We find that the offset, either spatial or in velocity, does not correlate with the SFR." (Summary)

## Claim tuples

- H: Is the offset [CII] emission extended/clumpy rather than compact? | E: Compare Cycle 1 low-resolution, Cycle 2 high-resolution and combined datasets | R: ~70% of [CII] flux resolved out at 0.3 arcsec; combined map clumpy | F: [CII] is diffuse plus clumpy on scales >1 kpc | **supported**
- H: Is [OIII] detected near BDF-3299? | E: Blind line search in Band 8 cube with negative-peak and blank-cube tests | R: Three clumps at >6.5 sigma integrated, within ~6.5 arcsec | F: [OIII] clumps offset from [CII] and from UV | **supported**
- H: Can UV from BDF-3299 excite the [OIII] clumps? | E: Compare luminosities with Vallini model | R: Implied gas mass >1e10 Msun | F: [OIII] must be powered by in-situ star formation | **supported**
- H: What powers the [CII] clump? | E: Model comparison and De Looze relation | R: External excitation needs ~4e9 Msun satellite; in-situ SFR ~3 Msun/yr | F: Origin remains uncertain; both viable | **partially**

## Reasoning

- Why this data: Re-observe [CII] at higher resolution and map [OIII] to study the ISM  
  > "we re-observed the [Cii] emission in BDF-3299 aiming at achieving the same sensitivity of previous observations obtained in Cycle 1" (Observations)
- Why this method: _not stated_
- Alternative: Astrometric offset between HST and ALMA rejected, as serendipitous sources agree  
  > "The offset is not ascribed to astrometric uncertainties, as astrometry is checked through serendipitous sources." (Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Cycle 2 Band 6 sensitivity worse than requested due to phase calibrator failure  
  > "the final phase errors are larger than the expected ones and the sensitivity of final images is worse than that requested." (Observations)
- Limitation (authors): Blind-search reliability may be ~50% at S/N=5 per other works  
  > "so half of our detections at S/N$\geq$5 could be spurious" (Reliability of [Oiii] detections)
- Caveat (inferred, ours): Using the bandpass calibrator as phase calibrator may leave residual phase errors and affect flux/position
- Caveat (inferred, ours): [OIII] clumps are close to detection threshold; false positives possible
- Caveat (inferred, ours): Interpretation relies on model-dependent assumptions (metallicity, geometry)
- Caveat (inferred, ours): Natural weighting and no cleaning of cubes may bias line fluxes

## Reproducibility

- Data public (paper): Data retrievable from ALMA archive  
  > "which can be retrieved from the ALMA data archive" (Acknowledgements)
- Products in archive: _not stated_
- Missing: Search algorithm code and parameters
- Missing: Extraction apertures and aperture correction values
- Missing: Cycle 1 calibration details
- Data volume (inferred): ~100-300 GB raw for three projects
- Score (inferred): 3/5, Public data and basic imaging stated, but the line search, apertures and model comparison are under-specified.
- Rediscovery candidate: no, Recipe incomplete for blind search and extraction, and key results depend on custom code and models.

## Links

- Method: (cite: Maiolino:2015) (Cycle 1 [CII] data, aperture correction, astrometry procedure)
- Companion: (cite: Carniani:2015) (serendipitous source in the field)
- Companion: (cite: Castellano:2016a) (HST Y-band imaging)
- Related: HST programme 13688

## Checks

```json
{
 "quotes": 70,
 "quotes_ok": 70,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2013.A.00433.S"
 ],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 47,
  "rate": 0.61
 },
 "evidence_ok": true
}
```

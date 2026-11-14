# A dusty, normal galaxy in the epoch of reionization

`2015Natur.519..327W` | Nature 2015 | first author: Watson, Darach | arXiv: 1503.00002 | DOI: 10.1038/nature14164

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: _not stated_
- Target **A1689-zD1**: coordinates _not stated_; z/distance z = 7.5±0.2 (spectroscopic, Lyα break)  
  > "it is gravitationally magnified by a factor of 9.3 by the galaxy cluster [10]" (main text); "The Lya cutoff is at 1035±24 nm and defines the redshift, z = 7.5±0.2." (main text); distance from X-shooter spectroscopy (this paper)  
  > "it is gravitationally magnified by a factor of 9.3 by the galaxy cluster [10]" (main text); "The Lya cutoff is at 1035±24 nm and defines the redshift, z = 7.5±0.2." (main text)

## Data provenance

- ALMA projects: 2011.0.00319.S, 2012.1.00261.S
- bands: four 3.8 GHz bands between 211 and 241 GHz (Cycles 0 and 1)  
  > "with the receivers tuned to four 3.8 GHz frequency bands between 211 and 241 GHz" (main text)
- frequencies and spectral setup: 211.06–214.94, 221.46–225.34, 227.06–230.94, 237.46–241.34 GHz; Cycle 1 data cover first and third setups; 1875 MHz per spectral window  
  > "the 2012.1.00261.S data used here cover the first and third frequency setup." (Methods); "bandwidth of 1875 MHz in each spectral window" (Methods)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 12 m to 450 m  
  > "The projected baselines range between 12m and 450m." (Methods)
- angular resolution: 0.8″×1″ natural; 1.36″×1.15″ tapered  
  > "resulting beam-size 0.8˝×1˝) and tapered using a 2D Gaussian with 1˝×1˝" (Methods)
- max recoverable scale: _not stated_
- sensitivity: 0.12 mJy/beam at source position, 42% of deepest mosaic part  
  > "the sensitivity (RMS) around its position is 0.12 mJy/beam, 42% of the sensitivity of the deepest part of the mosaic" (main text)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: [C II] 158 µm (not stated)
- Other facility **VLT/X-shooter**: 16 h spectroscopy: Lyα break redshift, continuum, line limits  
  > "a total time of 16 hours on target" (main text)
- Other facility **HST and Spitzer**: photometry for SED (ACS, WFC3, NIC2, IRAC)  
  > "and Spitzer ’s IRAC 3.6 µm and 4.5 µm bands" (Methods)
- External data: Lensing magnification 9.3 and discovery photometry  
  > "it is gravitationally magnified by a factor of 9.3 by the galaxy cluster [10]" (main text) [from Bradley et al. 2008 (ref 10)]
- External data: βIR = 1.92 as observed in HFLS3  
  > "β IR = 1.92 (as observed in HFLS3 [37] )" (Methods) [from Riechers et al. 2013 (ref 37)]

## Processing

### Calibration

- pipeline or manual: Cycle 0: additional manual reduction of preliminary-reduced data (flagging, 3C 279 frequency-dependent model)  
  > "additional careful reduction of the observatoryprovided preliminary-reduced data was required, including flagging of noisy data" (Methods)
- casa version: CASA 3.4 (Cycle 0), 4.1 (Cycle 1); imaging with 4.2  
  > "versions 3.4 and 4.1 for the Cycle 0 and 1 data respectively" (Methods)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Mars and Titan; 3C 279 for bandpass and phase  
  > "Flux calibration was done using Mars and Titan." (Methods)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "the calibrated visibilities were naturally weighted" (Methods)
- uv taper: 2D Gaussian 1″×1″  
  > "tapered using a 2D Gaussian with 1˝×1˝ to give greater weight to shorter baselines" (Methods)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: mosaic primary beam corrected, field weights included  
  > "Mosaicked images were primary beam corrected and the weights of the individual fields were taken into account." (Methods)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.36″×1.15″  
  > "resulting in a beam-size of 1.36˝×1.15˝" (Methods)
- final rms: 0.12 mJy/beam at source  
  > "the sensitivity (RMS) around its position is 0.12 mJy/beam" (main text)

### Inherited from earlier work

- Binning of X-shooter spectra  
  > "(see ref. 31 for details)" (Methods) [from Christensen et al. 2012 (ref 31)]
- Full ALMA mosaic to be presented later  
  > "The full mosaic will be presented in a forthcoming paper (Knudsen et al., in preparation)." (Methods) [from Knudsen et al., in preparation]

### Not stated but needed to reproduce (our reading)

- Imaging task parameters (cell, image size, deconvolver, threshold, masks)
- Whether Cycle 0 and 1 data were concatenated and how weights were set
- Flux-scale uncertainty
- Details of CMB correction implementation
- Exact modified blackbody fitting procedure and uncertainties
- Dust mass absorption coefficient normalisation (garbled in text)

## Analysis recipe

1. **calibrate and image ALMA mosaic**: CASA reduction, combine Cycle 0+1, natural weighting with 1″ taper, primary-beam correction  
  > "The data were combined and imaged using CASA 4.2" (Methods)
   - software: CASA
   - fitting: _not stated_
   - validation: Cycle 0 results within 1σ of preliminary-reduced data  
  > "Our results are, however, not more than 1σ different from the preliminary-reduced data." (Methods)
2. **derive dust mass and TIR luminosity**: single-temperature modified blackbody fit to one 226 GHz flux with CMB correction  
  > "single temperature modified blackbody" (Methods)
   - parameter: T = 35 K, βIR = 1.92, λ0 = 200 µm  
  > "We assumed 35K." (Methods)
   - assumption: dust temperature 35 K; optical depth unity at 200 µm  
  > "we assume the wavelength of optical depth unity is λ 0 = 200 µm" (Methods)
   - fitting: _not stated_
   - validation: compared with IRX-βUV constraints and MAGPHYS/GRASIL fits  
  > "we fit self-consistent full UV to far-infrared SED models using the MAGPHYS [47] and GRASIL [48,49,50] codes" (Methods)
3. **estimate gas mass and dust-to-gas ratio**: invert Schmidt-Kennicutt law using SFR and size  
  > "We invert the Schmidt-Kennicutt law relating the surface densities of SFR and gas mass [14]" (Methods)
   - assumption: constant CO-to-gas conversion X(CO); ±0.4 dex scatter  
  > "assuming a constant CO to gas conversion, X(CO) [14]" (Methods)
   - fitting: _not stated_
   - validation: alternative lens model gives magnification 8.6±0.5  
  > "similar magnification of 8.6±0.5 for this source" (Methods)
4. **UV-optical SED fit for mass and age**: Bayesian comparison with library of BC03 SEDs with random SFHs  
  > "the observed SED is compared to every model SED in the library" (Methods)
   - assumption: Chabrier IMF, two-component dust model  
  > "adopting a two-component model [44 ]" (Methods)
   - fitting: likelihood exp(-χ²/2), marginalised over nuisance parameters  
  > "weighting each model by its likelihood exp(–χ [2] /2)" (Methods)
   - validation: nebular line contamination check  
  > "Finally, strong emission lines are not included in the SED modelling. We consider possible contamination by the Balmer Hγ and Hδ lines to the 3.6 µm flux" (Methods, The age, mass and SED of A1689-zD1)

## Software

- **CASA** 3.4, 4.1, 4.2: ALMA reduction and imaging  
  > "Data reduction used the Common Astronomy Software Application [35] versions 3.4 and 4.1" (Methods)
- **New-HyperZ** 12.2: photometric redshift  
  > "New-HyperZ code [33], version 12.2" (Methods)
- **MAGPHYS** : UV-FIR SED fit  
  > "MAGPHYS [47] and GRASIL" (Methods)
- **GRASIL** : UV-FIR SED fit  
  > "MAGPHYS [47] and GRASIL [48,49,50] codes" (Methods)
- **ESO X-shooter pipeline** 2.2: X-shooter reduction  
  > "ESO X-shooter pipeline version 2.2" (Methods)
- **SExtractor** : HST photometry  
  > "measured using SExtractor in double-image mode" (Methods)
- **MultiDrizzle** : combining HST frames  
  > "combined using the MultiDrizzle [42] software" (Methods)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA flux of A1689-zD1 | 0.61 | 0.12 | mJy | 1 | detected at 5.0σ with an observed flux of 0.61 ± 0.12 mJy in the combined image |
| spectroscopic redshift | 7.5 | 0.2 | dimensionless | 0 | determine its redshift to be z = 7.5±0.2 |
| TIR luminosity | 6.2e10 | 0.8e10 (flux only) | Lsun | 2 | L TIR = 6.2 ± 0.8×10 [10] L ⊙ |
| dust mass | 4e7 | not stated | Msun | 2 | with a dust mass in the galaxy of 4×10 [7] M ⊙, assuming a dust temperature of 35 K |
| total SFR | 12 | +4/-2 | Msun/yr | 2 | total SFR of |
| dust-to-gas ratio | 0.017 | 0.5 dex | dimensionless | 3 | The dust-to-gas ratio we derive for our fiducial model is 0.017 |
| stellar mass | 1.7e9 | +0.15/-0.16 dex | Msun | 4 | lensing-corrected stellar mass of 1.7×10 [9] M ⊙ |

## Qualitative findings

- No [CII] detected; excludes L[CII]/LFIR >0.0024 over covered redshifts  
  > "we exclude [C II ] 158µm emission at the high end of this ratio (>0.0024" (Methods)

## Claim tuples

- H: Typical z>7 galaxies are detectable in dust emission | E: ALMA mosaic of Abell 1689 covering lensed A1689-zD1 | R: 5.0σ detection, 0.61±0.12 mJy | F: Dust emission found in a sub-L* z=7.5 galaxy | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Single FIR flux point requires assumed temperature; dust mass may be an order of magnitude larger  
  > "With only one FIR flux point it was necessary to assume a value of the dust temperature to recover the dust mass." (Methods)
- Caveat (inferred, ours): 5σ single-band detection with astrometric offset of 0.4 arcsec
- Caveat (inferred, ours): Dust mass depends on assumed T, β, κ
- Caveat (inferred, ours): Gas mass from S-K inversion, 0.5 dex uncertain

## Reproducibility

- Data public (paper): Reduction scripts provided at a URL  
  > "The data reduction scripts used for the ALMA data can be obtained at: http://dark.nbi.ku.dk/research/archive." (Methods)
- Products in archive: _not stated_
- Code: ALMA reduction scripts at dark.nbi.ku.dk  
  > "The data reduction scripts used for the ALMA data can be obtained at: http://dark.nbi.ku.dk/research/archive." (Methods)
- Missing: Imaging parameters
- Missing: Modified-blackbody fitting details
- Missing: SED library priors
- Data volume (inferred): ~50-100 GB (Cycle 0 and 1 mosaic)
- Score (inferred): 3/5, Project codes and scripts given, but imaging and fitting details are sparse.
- Rediscovery candidate: no, Key numbers rely on assumed T and lensing and SED modelling that are not fully specified.

## Links

- Method: da Cunha et al. 2013 (ref 12) (CMB correction)
- Companion: Knudsen et al., in preparation (full ALMA mosaic)
- Related: Abell 1689 ALMA mosaic
- Related: X-shooter z>7 programme

## Checks

```json
{
 "quotes": 61,
 "quotes_ok": 61,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 45,
  "rate": 0.6
 },
 "evidence_ok": true
}
```

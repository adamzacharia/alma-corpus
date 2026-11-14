# New constraints on dust emission and UV attenuation of z = 6.5-7.5 galaxies from millimeter observations

`2015A&A...574A..19S` | Astronomy and Astrophysics 2015 | first author: Schaerer, D. | arXiv: 1407.5793 | DOI: 10.1051/0004-6361/201424649

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: What are the dust emission, IR luminosity, dust mass and UV attenuation limits of z~6.5-7.5 galaxies from 1.2mm PdBI observations combined with published ALMA data on Himiko and IOK-1?  
  > "To shed new light on these questions we have targeted two recently discovered Lyman break galaxies (LBGs) at z ≈ 6.8 and z = 7.508 to search for dust continuum and [C ii] λ158µm line emission." (abstract)
- Target **A1703-zD1**: coordinates _not stated_; z/distance z≈6.8 (photometric), magnification µ=9  
  > "The redshift of A1703-zD1 is estimated from photometric observations." (2.1 IRAM observations of the lensed galaxy A1703-zD1 and the GOODS-N source z8-GND-5296); distance from photometric redshift (Bradley et al. 2012; Smit et al. 2014; own SED fits)  
  > "The redshift of A1703-zD1 is estimated from photometric observations." (2.1 IRAM observations of the lensed galaxy A1703-zD1 and the GOODS-N source z8-GND-5296)
- Target **z8-GND-5296**: coordinates _not stated_; z/distance z=7.508  
  > "the redshift is based on the detection of the Lyα line" (2.1 IRAM observations of the lensed galaxy A1703-zD1 and the GOODS-N source z8-GND-5296); distance from Lyα spectroscopic redshift (Finkelstein et al. 2013)  
  > "the redshift is based on the detection of the Lyα line" (2.1 IRAM observations of the lensed galaxy A1703-zD1 and the GOODS-N source z8-GND-5296)
- Target **Himiko**: coordinates _not stated_; z/distance z=6.595  
  > "Two bright non-lensed LAEs, Himiko at _z_ = 6.595 and IOK1 at _z_ = 6.96" (1. Introduction); distance from _not stated_
- Target **IOK-1**: coordinates _not stated_; z/distance z=6.96  
  > "Two bright non-lensed LAEs, Himiko at _z_ = 6.595 and IOK1 at _z_ = 6.96" (1. Introduction); distance from _not stated_
- Target **HCM6A**: coordinates _not stated_; z/distance z=6.56  
  > "The _z_ = 6.56 Lyα emitting galaxy (LAE) HCM6A, lensed by the galaxy cluster Abell 370," (1. Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00115.S, 2011.0.00767.S
- bands: ALMA band 6 (1.2mm) for Himiko and IOK-1 (published data); PdBI receiver 3 (1.2 mm) for new data  
  > "reaching unprecedented depths in the 1.2mm window (band 6)" (1. Introduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: PdBI continuum rms 165 and 124 µJy; ALMA rms 0.021 (IOK-1) and 0.017 (Himiko) mJy/beam  
  > "The continuum rms are 165 and 124 µJy and the line rms in 50 km s −1 channels are 1.52 and 1.83 mJy, respectively." (2.1 IRAM observations of the lensed galaxy A1703-zD1 and the GOODS-N source z8-GND-5296)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: [C II] 158 µm (1900.54 GHz)
- Other facility **IRAM PdBI**: New 1.2mm continuum and [C II] observations of A1703-zD1 and z8-GND-5296  
  > "have been observed with the Plateau de Bure interferometer (PdBI) at 1.2mm." (abstract)
- Other facility **IRAM 30m GISMO**: 2mm map of Abell 1703, not detected, not used  
  > "we have also obtained a deep 2mm map of the Abell 1703 cluster with GISMO." (2.1 IRAM observations of the lensed galaxy A1703-zD1 and the GOODS-N source z8-GND-5296)
- External data: ALMA 1.2mm observations of IOK-1  
  > "Observations from Ota et al. (2014)." (Table 1) [from Ota et al. (2014)]
- External data: ALMA 1.2mm observations of Himiko  
  > "Observations from Ouchi et al. (2013)." (Table 1) [from Ouchi et al. (2013)]
- External data: PdBI observations of HCM6A  
  > "Observations from Kanekar et al. (2013)." (Table 1) [from Kanekar et al. (2013)]
- External data: HST and IRAC photometry of A1703-zD1  
  > "The HST and IRAC photometry for A1703-zD1 is taken from Bradley et al. (2012)." (2.2 Other data) [from Bradley et al. (2012)]

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
- weighting robust: natural weighting  
  > "The data cubes were build using natural weighting to maximize the point source sensitivity." (2.1 IRAM observations of the lensed galaxy A1703-zD1 and the GOODS-N source z8-GND-5296)
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
- final beam: 2.30"×1.75" (A1703-zD1), 1.78"×1.61" (z8-GND-5296)  
  > "The beam sizes obtained are: 2.30 ′′ ×1.75 ′′ and 1.78 ′′ ×1.61 ′′ for A1703-zD1 and z8-GND5296 respectively." (2.1 IRAM observations of the lensed galaxy A1703-zD1 and the GOODS-N source z8-GND-5296)
- final rms: _not stated_

### Inherited from earlier work

- CMB correction to dust heating  
  > "by removing the contribution of the CMB to the dust heating as detailed by da Cunha et al. (2013a) and in a similar way to Ota et al. (2014)." (3. IR and dust properties) [from da Cunha et al. (2013a)]
- SED fitting code and ingredients  
  > "The code and the ingredients are the same as described in Schaerer & de Barros (2009, 2010) and Schaerer et al. (2013)." (4.3 SED modelling) [from Schaerer & de Barros (2009, 2010); Schaerer et al. (2013)]

### Not stated but needed to reproduce (our reading)

- ALMA data reduction details for Himiko and IOK-1 (in the cited papers)
- Numerical SED fitting grid and priors
- Coordinates of targets
- PdBI calibration details and flux uncertainty

## Analysis recipe

1. **Reduce PdBI data and derive limits**: GILDAS reduction, natural weighting cubes, continuum and line rms  
  > "The data reduction was done using the GILDAS software." (2.1 IRAM observations of the lensed galaxy A1703-zD1 and the GOODS-N source z8-GND-5296)
   - software: GILDAS
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive L_IR and dust mass limits**: modified blackbody with CMB correction, Td = 25, 35, 45 K  
  > "contribution removed) by integrating the SED between 8 and 1000µm assuming a modified black body SED with a power law in the Wien regime with a spectral index α = 2.9." (3. IR and dust properties)
   - parameter: β_IR = 1.5, alpha = 2.9, ν0 = 239.84 GHz  
  > "κ ν = 1.875(ν/ν 0 ) [β] [IR] m [2] kg [−][1] with ν 0 = 239.84GHz and β IR = 1.5" (3. IR and dust properties)
   - assumption: Td = 35 K adopted  
  > "we will subsequently adopt L IR and M d values derived for the intermediate value of T d = 35 K." (3. IR and dust properties)
   - fitting: _not stated_
   - validation: _not stated_
3. **UV attenuation from L_IR/L_UV**: log(f_UV)=0.24+0.44x+0.16x^2, A_UV=2.5 log f_UV  
  > "log( f UV ) = 0.24 + 0.44 x + 0.16 x [2] ." (4.1 Observed and derived properties)
   - fitting: _not stated_
   - validation: _not stated_
4. **SED fitting**: GALAXEV templates with nebular emission, Calzetti law, free age, A_V, Z  
  > "we use a large set of spectral templates based on the GALAXEV synthesis models of Bruzual & Charlot (2003)" (4.3 SED modelling)
   - assumption: Salpeter IMF 0.1-100 Msun  
  > "A Salpeter IMF from 0.1 to 100 M ⊙ is adopted." (4.3 SED modelling)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **GILDAS** : PdBI data reduction  
  > "The data reduction was done using the GILDAS software." (2.1 IRAM observations of the lensed galaxy A1703-zD1 and the GOODS-N source z8-GND-5296)
- **TOPCAT** : table handling  
  > "TOPCAT (Taylor 2005)" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| L_CII upper limit A1703-zD1 | <2.8e7 | not stated | Lsun | 2 | providing a deep upper limit of L [CII] < 2.8 × 10 [7] L ⊙ for A1703-zD1 |
| L_IR(Td=35) A1703-zD1 | <8.1e10 | not stated | Lsun | 2 | L IR ( T d = 35) < 8.1 × 10 [10] L ⊙ |
| Md(Td=35) A1703-zD1 | <1.6e7 | not stated | Msun | 2 | M d ( T d = 35) < 1.6 × 10 [7] M ⊙ |
| Md(Td=35) z8-GND-5296 | <13.9e7 | not stated | Msun | 2 | < 13.9 × 10 [7] M ⊙ respectively |

## Qualitative findings

- All five galaxies compatible with the Calzetti IRX–β relation; attenuation below mean low-z mass relation  
  > "We find that all five galaxies are compatible with the Calzetti IRX–β relation" (abstract)

## Claim tuples

- H: Are dust and [CII] detectable in A1703-zD1 and z8-GND-5296? | E: PdBI 1.2mm observations | R: No detections; rms 0.12 and 0.16 mJy/beam | F: Only upper limits; lensing gives A1703-zD1 depth comparable to ALMA | **supported**
- H: Do the galaxies follow the Calzetti IRX–β relation? | E: L_IR/L_UV limits vs β | R: Limits lie on or below relation | F: Compatible but not yet constraining | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Samples too small to establish mass-attenuation relation at high z  
  > "the currently available samples are too small to draw significant conclusions on the existence or not of the mass-attenuation relation" (5.3 UV attenuation as a function of redshift and galaxy mass)
- Caveat (inferred, ours): Dust temperature unknown, limits depend ±0.25 dex
- Caveat (inferred, ours): Lensing magnification uncertain
- Caveat (inferred, ours): Photometric redshift may not cover [CII]
- Caveat (inferred, ours): ALMA data not reprocessed

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Reduced ALMA and PdBI data details
- Missing: SED fitting code
- Data volume (inferred): small (<~10 GB for ALMA data of two sources)
- Score (inferred): 3/5, Formulas and parameters given; ALMA data reduction deferred to other papers and SED code not released.
- Rediscovery candidate: no, ALMA role is minor and results are mostly derived from published numbers and upper limits.

## Links

- Method: da Cunha et al. (2013a) (CMB correction to dust)
- Method: Schaerer & de Barros (2009, 2010) (SED fitting code)
- Companion: Ota et al. (2014) (ALMA observations of IOK-1)
- Companion: Ouchi et al. (2013) (ALMA observations of Himiko)

## Checks

```json
{
 "quotes": 42,
 "quotes_ok": 42,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 31,
  "rate": 0.378
 },
 "evidence_ok": true
}
```

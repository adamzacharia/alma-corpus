# Microwave Continuum Emission and Dense Gas Tracers in NGC 3627: Combining Jansky VLA and ALMA Observations

`2015ApJ...813..118M` | The Astrophysical Journal 2015 | first author: Murphy, Eric J. | arXiv: 1508.06284 | DOI: 10.1088/0004-637X/813/2/118

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation
- Question: How do free-free continuum (33 and 94.5 GHz) and dense gas tracers (HCN, HCO+ J=1-0) compare on ~90 pc scales in three regions of NGC 3627, and how do dense gas fraction and star formation efficiency relate?  
  > "we combined new observations from ALMA and the VLA to report one of the first extragalactic cloud-scale comparisons of dense gas" (Introduction)
- Target **NGC 3627 (nucleus, Enuc. 1, Enuc. 2)**: coordinates Nucleus 11 20 15.0 +12 59 30 (J2000)  
  > "located at a distance of $9.38 \pm 0.35$ Mpc (cite: hkp01)" (Introduction); "NGC 3627 Enuc. 1 &$11   ~20   ~16.2$&$+   11   ~20   ~16$" (Table 1); z/distance 9.38 ± 0.35 Mpc  
  > "located at a distance of $9.38 \pm 0.35$ Mpc (cite: hkp01)" (Introduction); "NGC 3627 Enuc. 1 &$11   ~20   ~16.2$&$+   11   ~20   ~16$" (Table 1); distance from Freedman et al. 2001 (cite: hkp01)  
  > "located at a distance of $9.38 \pm 0.35$ Mpc (cite: hkp01)" (Introduction); "NGC 3627 Enuc. 1 &$11   ~20   ~16.2$&$+   11   ~20   ~16$" (Table 1)

## Data provenance

- ALMA projects: 2012.1.00456.S
- bands: ALMA Band 3 (94.5 GHz LO); VLA Ka band  
  > "Atacama Large Millimeter Array (ALMA) Band 3 (94.5 GHz) continuum images" (abstract)
- frequencies and spectral setup: four 1.875 GHz wide spectral windows centered at 87.5, 89.5, 99.5, 100.5 GHz  
  > "centering the four 1.875 GHz wide spectral windows at 87.5, 89.5, 99.5, and 100.5 GHz" (2.2 ALMA Band-3 Data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: chosen to match ≲2 arcsec beam of VLA 33 GHz data (specific configuration not stated)  
  > "The array configuration was chosen to match the $\lesssim$2$''$ synthesized beam of the VLA 33 GHz data." (2.2 ALMA Band-3 Data)
- baselines: _not stated_
- angular resolution: ~2 arcsec (~90 pc)  
  > "achieving a common resolution of $\approx$2$''$" (2 Data and Analysis)
- max recoverable scale: ~25 arcsec ALMA; 44 arcsec VLA  
  > "the largest angular scales that the ALMA and VLA images should be sensitive to are $\approx$25$''$ and 44$''$, respectively" (2.4 Continuum Imaging and Photometry)
- sensitivity: continuum rms 32 µJy/beam at 94.5 GHz; line channel rms ~1.2 mJy/beam in 10 km/s  
  > "The rms noise of the ALMA channel maps is $\approx$1.2 mJy bm$^{-1}$ in a 10 km s$^{-1}$ channel." (Line Imaging and Photometry)
- time on source: _not stated_
- observing dates: ALMA December 2013 (Cycle 1); VLA Nov 2011 and Mar 2013  
  > "In December 2013 as part of ALMA’s Cycle 1 observing campaign" (2.2 ALMA Band-3 Data)
- pi or archival as stated: _not stated_
- Line: HCN J=1-0 (88.6318 GHz)
- Line: HCO+ J=1-0 (89.1885 GHz)
- Line: H40alpha H40α (not detected) (99.0229 GHz)
- Other facility **VLA Ka band (SFRS)**: 33 GHz continuum images  
  > "D-configuration observations were obtained in November 2011 (VLA/11B-032) and March 2013 (VLA/13A-129)." (2.1 VLA Ka-Band Data)
- Other facility **BIMA SONG**: CO J=1-0 map, beam 7.3x5.8 arcsec  
  > "having a synthesized beam of $7.3\ensuremath{''} \times 5.8\ensuremath{''}$" (2.3 Archival CO Data)
- External data: BIMA SONG CO J=1-0 data  
  > "we make use of $J=1\rightarrow0$ CO data taken as part of the BIMA SONG survey (cite: bimasong)" (2.3 Archival CO Data) [from (cite: bimasong)]
- External data: Distance 9.38 Mpc  
  > "located at a distance of $9.38 \pm 0.35$ Mpc (cite: hkp01)" (Introduction) [from (cite: hkp01)]
- External data: Non-thermal spectral index -0.85 from NGC 6946 regions  
  > "We took the non-thermal spectral index to be $\alpha^{\rm NT} = -0.85$" (3.1 Spectral Indices) [from (cite: ejm11b)]
- External data: Disk rotation 204 km/s and bar pattern speed 55 km/s/kpc  
  > "The bar pattern speed for NGC 3627 is $\approx$55 km s$^{-1}$ kpc$^{-1}$ (cite: kartik02)" (3.2 Spatial Offsets) [from (cite: deBlok08); (cite: kartik02)]

## Processing

### Calibration

- pipeline or manual: CASA, standard procedures / ALMA QA  
  > "the ALMA data were reduced and calibrated using CASA following standard procedures as part of the ALMA quality assurance process" (2.2 ALMA Band-3 Data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: VLA: 3C 286 (flux/bandpass)  
  > "3C 286 was used as the flux density and bandpass calibrator" (2.1 VLA Ka-Band Data)
- flux scale uncertainty: 3% at 33 GHz, 5% at 94.5 GHz  
  > "an absolute calibration uncertainty of 3% at 33 GHz (cite: pb13fcal) and 5% at 94.5 GHz (ALMA Cycle 1 Technical Handbook)" (2.4 Continuum Imaging and Photometry)
- self calibration: _not stated_

### Imaging

- task: CASA clean, MFS, nterms=2  
  > "The mode of clean was set to multifrequency synthesis (cite: mfs1; mfs2)." (2.4 Continuum Imaging and Photometry)
- deconvolver: _not stated_
- weighting robust: Briggs robust=0.5  
  > "We chose to use *Briggs* weighting with robust=0.5, and set the variable nterms=2" (2.4 Continuum Imaging and Photometry)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: scales ≈1 and 3 times synthesized beam FWHM  
  > "searching for structures with scales $\approx$1 and 3 times the FWHM of the synthesized beam" (2.4 Continuum Imaging and Photometry)
- continuum subtraction: uvcontsub  
  > "before the line images were created, the data were first continuum subtracted using the CASA task uvcontsub" (Line Imaging and Photometry)
- line free channels: _not stated_
- primary beam correction: CASA impbcor  
  > "A primary beam correction was applied using the CASA task impbcor before analyzing the images." (2.4 Continuum Imaging and Photometry)
- array combination: _not stated_
- smoothing: imsmooth to CO beam 7.3x5.8 arcsec, regrid to common pixels  
  > "The resolution matching was carried out using the task imsmooth in CASA, before re-gridding each image to a common pixel scale." (2.5 Line Imaging and Photometry)
- final beam: 94.5 GHz: 1.89x1.66 arcsec (nucleus)  
  > "$1.89\ensuremath{''} \times 1.66\ensuremath{''}$ & 32" (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- VLA SFRS Ka-band observations and reduction details deferred  
  > "Details on all of the SFRS VLA Ka-band survey observations and data reduction can be found in E.J. Murphy et al. (2015, in preparation)." (2.1 VLA Ka-Band Data) [from E.J. Murphy et al. (2015, in preparation)]
- SFR calibration for 33 GHz thermal emission  
  > "using the calibration for pure thermal emission given in (cite: ejm11b; ejm12b)" (3.3 Dense Gas Fractions) [from (cite: ejm11b; ejm12b)]

### Not stated but needed to reproduce (our reading)

- Line-free channels for uvcontsub
- ALMA array configuration, baselines, and time on source
- CASA version
- Image size and cell size
- Clean masks and thresholds
- Velocity ranges for moment 0 integration
- SFR calibration formula and how L33 converts to SFR
- Monte Carlo details for velocity dispersion errors
- Unit conversion from Jy/beam to K km/s for HCO+, HCN, CO

## Analysis recipe

1. **Image continuum and measure photometry**: clean with MFS, nterms=2, multiscale, Briggs robust 0.5; imfit within 15 arcsec circular aperture  
  > "we used the task imfit in CASA to fit sources within a circular aperture having a radius of 15$''$" (2.4 Continuum Imaging and Photometry)
   - software: CASA
   - parameter: robust=0.5, nterms=2  
  > "We chose to use *Briggs* weighting with robust=0.5, and set the variable nterms=2" (2.4 Continuum Imaging and Photometry)
   - fitting: imfit single-component Gaussian  
  > "Clearly for the case of Enuc. 2, which is an elongated structure at the end of the bar, a single-component fit is not the most appropriate." (2.4 Continuum Imaging and Photometry)
   - validation: _not stated_
2. **Image lines, extract spectra, fit line widths**: uvcontsub, clean, moment 0 maps; spectra from circular aperture 20% larger than source major axis convolved with beam; Gaussian fits  
  > "The spectra were extracted using a circular aperture centered on the 94.5 GHz source positions returned by imfit" (2.5 Line Imaging and Photometry)
   - software: CASA
   - fitting: Gaussian line profile; Monte Carlo for uncertainties  
  > "uncertainties that were estimated using the errors per channel along with a Monte Carlo approach" (2.5 Line Imaging and Photometry)
   - validation: _not stated_
3. **Spectral index map and thermal fraction**: Convolve 94.5 GHz to 33 GHz beam, regrid, compute alpha for >3 sigma pixels; thermal fraction with fixed non-thermal index  
  > "after convolving the slightly higher resolution 94.5 GHz data to match the beam of the 33 GHz data and putting the data on the same grid" (3.1 Spectral Indices)
   - software: CASA
   - assumption: alpha_NT = -0.85; free-free optically thin; negligible AME and thermal dust  
  > "We took the non-thermal spectral index to be $\alpha^{\rm NT} = -0.85$" (3.1 Spectral Indices)
   - fitting: _not stated_
   - validation: Tested alpha_NT=-0.6; AGN contribution <3% estimated  
  > "by instead assuming $\alpha^{\rm NT} = -0.6$, the mean 33 GHz thermal fractions over the nucleus, Enuc. 1, and 2 are 80, 76, and 62%, respectively" (3.1 Spectral Indices)
4. **Dense gas fraction and SFE**: Convolve to CO beam, take peak in 15 arcsec aperture; dense gas mass from HCO+ / total from CO; SFR from 33 GHz thermal luminosity  
  > "The dense molecular gas fraction is taken to be the mass ratio of dense molecular gas traced by the $J=1\rightarrow0$ transition of HCO$^{+}$ to the total molecular gas" (3.3 Dense Gas Fractions)
   - software: CASA
   - assumption: alpha_HCO+ ≈ 10, alpha_CO ≈ 4.3 Msun/(K km/s pc^2); mean 33 GHz thermal fraction 79%  
  > "$\alpha_{\rm CO} \approx 4.3$ M${_\odot}\,{\rm (K\,km\,s^{-1}\,pc^{2})}^{-1}$" (3.3 Dense Gas Fractions)
   - fitting: _not stated_
   - validation: Trend persists if HCN used for dense gas mass  
  > "the trend observed in the top panel of Figure [5](#fig:dgas) would persist even if we instead used the HCN-derived dense gas mass" (3.3 Dense Gas Fractions)

## Software

- **CASA** : calibration, clean imaging, impbcor, imfit, uvcontsub, imsmooth  
  > "Calibrated VLA and ALMA measurement sets for each source were imaged using the task clean in CASA." (2.4 Continuum Imaging and Photometry)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| mean 33-94.5 GHz spectral index (nucleus, Enuc.1, Enuc.2) | -0.10, -0.15, -0.27 | std 0.20, 0.18, 0.15 | dimensionless | 3 | we measured mean spectral indices of $\alpha_{\rm 33\,GHz}^{\rm 94.5\,GHz} = -0.10, -0.15,$ and $-0.27$ |
| mean 33 GHz thermal fraction (nucleus, Enuc.1, Enuc.2) | 85, 82, 70 | std 19, 19, 20 | % | 3 | we measure corresponding mean 33 GHz thermal fractions over the nucleus, Enuc. 1 and 2 of 85, 82 and 70%, respectively |
| continuum-HCN/HCO+ peak offset at Enuc. 2 | ≈3 arcsec (≈130 pc) | not stated | arcsec | 2 | The continuum and molecular gas are spatially offset in the plane of the sky by $\approx$3$''$ ($\approx$130 pc at the distance of NGC 3627). |
| 33 GHz integrated flux density of nucleus | 2.09 | 0.08 | mJy | 1 | $1.70\pm0.06$   / $2.09\pm0.08$ |
| propagation time between stars and dense gas peaks | ≈3 | not stated | Myr | 0 | Thus, the propagation time is $\approx$3 Myr, less than the age of typical OB stars. |

## Qualitative findings

- Dense gas fraction decreases with increasing SFE; Enuc. 1 converts gas to stars ~3x faster  
  > "A clear trend of decreasing dense gas fraction with increasing star formation efficiency is observed." (3.3 Dense Gas Fractions)

## Claim tuples

- H: Can sites of current star formation be spatially separated from dense gas at ~90 pc? | E: Compare 33/94.5 GHz continuum peaks with HCN/HCO+ moment 0 peaks | R: Enuc. 2 peaks offset by ≈3 arcsec (~130 pc) | F: Resolution suffices to distinguish current star formation from fuel for future star formation | **supported**
- H: Is 33 GHz emission dominated by thermal free-free at the HII region peaks? | E: 33-94.5 GHz spectral index and thermal decomposition | R: mean thermal fractions 70-85%, near unity at peaks | F: Thermal fraction near unity at peaks | **supported**
- H: Does dense gas fraction or dynamical state control SFE? | E: Plot dense gas fraction and HCO+ velocity dispersion vs SFE for three regions | R: Both decrease with increasing SFE | F: Dynamical state of dense gas matters more than abundance | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Only three regions; nuclear HCN cut off by bandpass; single-component fit poor for Enuc. 2  
  > "the detection of HCN towards the nucleus is cut off by the bandpass at a radial velocity of $v_\mathrm{LSRK} \approx 800\mathrm{\,km\,s^{-1}}$" (2.5 Line Imaging and Photometry)
- Caveat (inferred, ours): Trends rest on three data points
- Caveat (inferred, ours): Thermal fractions depend on assumed alpha_NT
- Caveat (inferred, ours): Single conversion factors assumed for HCO+ and CO across very different environments
- Caveat (inferred, ours): ALMA missing flux at large scales not corrected vs BIMA

## Reproducibility

- Data public (paper): ALMA project code cited in acknowledgments; BIMA SONG archival  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00456.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and exact clean parameters
- Missing: VLA Ka-band reduction details deferred to unpublished paper
- Missing: SFR calibration formula
- Missing: line-free channels and moment ranges
- Data volume (inferred): ~20-50 GB (ALMA Cycle 1 Band 3 plus VLA Ka and BIMA maps)
- Score (inferred): 3/5, Public ALMA data and clear imaging recipe, but missing CASA version, configuration details, and VLA reduction deferred.
- Rediscovery candidate: no, VLA reduction is deferred to an unpublished paper and several processing parameters are missing, so the recipe is incomplete.

## Links

- Method: (cite: ejm12b) (SFRS thermal fraction and SFR calibration methodology)
- Companion: E.J. Murphy et al. (2015, in preparation) (SFRS VLA Ka-band observations and reduction)
- Related: Star Formation in Radio Survey (SFRS)
- Related: SINGS
- Related: KINGFISH
- Related: BIMA SONG

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 44,
  "rate": 0.638
 },
 "evidence_ok": true
}
```

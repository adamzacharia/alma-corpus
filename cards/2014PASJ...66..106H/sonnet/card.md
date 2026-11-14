# VERA and ALMA observations of the H<SUB>2</SUB>O supermaser burst in Orion KL

`2014PASJ...66..106H` | Publications of the Astronomical Society of Japan 2014 | first author: Hirota, Tomoya | arXiv: 1407.2757 | DOI: 10.1093/pasj/psu110

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, milky_way_ism
- Question: What are the time variation, spatial structure, proper motions and excitation of the 22 GHz H2O supermaser burst in Orion KL, and what is its relation to the Compact Ridge seen with ALMA?  
  > "In this paper, we report results of our continued monitoring observations of the supermaser with VERA to investigate time variations of their properties." (Introduction)
- Target **Orion KL supermaser (H2O maser, Compact Ridge)**: coordinates _not stated_; z/distance 420 pc  
  > "Orion KL (Kleinmann-Low object) is one of the nearest massive star-forming regions at a distance of 420 pc (cite: menten2007; kim2008)" (Introduction); distance from menten2007; kim2008  
  > "Orion KL (Kleinmann-Low object) is one of the nearest massive star-forming regions at a distance of 420 pc (cite: menten2007; kim2008)" (Introduction)

## Data provenance

- ALMA projects: 2011.0.00199.S
- bands: ALMA Band 7 (320-340 GHz)  
  > "Observations were carried out at the ALMA band 7 (in the range of 320-340 GHz) on 2012 July 16, August 25, and October 21." (ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: maximum 400 m  
  > "The maximum baseline length in our ALMA observations was 400 m" (ALMA)
- angular resolution: ~0.5" depending on UV weighting  
  > "corresponding to a spatial resolution of $\sim$0.5$''$, depending on the UV weighting in the imaging." (ALMA)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2012 July 16, August 25, October 21  
  > "Observations were carried out at the ALMA band 7 (in the range of 320-340 GHz) on 2012 July 16, August 25, and October 21." (ALMA)
- pi or archival as stated: _not stated_
- Line: H2O 10(2,9)-9(3,6) (321.225656 GHz)
- Line: HCOOCH3 vt=0, 28(3,26)-27(3,25) A (321.22338 GHz)
- Line: H2O v2=1, 5(2,3)-6(1,6) (336.227931 GHz)
- Other facility **VERA**: 22 GHz H2O maser monitoring, astrometry and imaging  
  > "Observations of the $6_{1,6}$-$5_{2,3}$ transition of H$_{2}$O at 22.235080 GHz (cite: kukolich1969; chen2000) in Orion KL were carried out with VERA." (VERA)
- External data: Source I proper motion (6.3, -4.2) mas/yr from VLA astrometry  
  > "Source I ($\mu_{\alpha} \cos \delta$, $\mu_{\delta}$)=(6.3 mas yr$^{-1}$, -4.2 mas yr$^{-1}$), measured by astrometric observations with the Very Large Array (VLA) (cite: goddi2011)" (3.3 Maser maps and proper motion measurements) [from (cite: goddi2011)]
- External data: ALMA band 6 and 7 continuum flux densities 57±5 and 129±14 mJy  
  > "The flux density at ALMA bands 6 and 7 are 57$\pm$5 mJy and 129$\pm$14 mJy, respectively (cite: hirota2014b)." (Discussion) [from (cite: hirota2014b)]
- External data: Maser excitation model (emissivity ratio R vs temperature and xi)  
  > "As demonstrated in the model calculations (cite: neufeld1990), the lower limit of $R>10^{6}$ can be achieved when the temperature is $\sim$200-400 K" (Discussion) [from (cite: neufeld1990)]

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
- uv taper: visibilities with baseline > 100 kλ used to search for compact H2O emission (<2")  
  > "by using the visibility data with the baseline length longer than 100 k$\lambda$, corresponding to the angular size of the emission region of $<$2$''$" (3.4 Submillimeter observations with ALMA)
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

- VERA observation and AIPS calibration/imaging procedure  
  > "Calibration and synthesis imaging were performed using the NRAO Astronomical Image Processing System (AIPS) software package in the same manner employed previously (cite: hirota2007; hirota2011)." (VERA) [from (cite: hirota2007; hirota2011)]
- ALMA observation and processing details  
  > "Further details of observations are reported elsewhere (cite: hirota2014a; hirota2014b)." (ALMA) [from (cite: hirota2014a; hirota2014b)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration details, CASA version, calibrators
- Weighting/robust, cell and image size, deconvolver
- Continuum-subtraction line-free channels and self-calibration parameters
- Spectral setup and on-source times
- Moment map thresholds
- Maser fitting details (AIPS tasks, epochs' flux scale)

## Analysis recipe

1. **Fit maser spectra**: Single Gaussian fits, two Gaussians for epochs with two velocity components, giving flux, width, peak velocity  
  > "First, these parameters are determined by fitting a single Gaussian to the observed profile." (3.1 Time variation of the 22 GHz H2O maser)
   - software: AIPS
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure maser spot positions and proper motions**: 2D Gaussian fits on phase-referenced images; absolute proper motions corrected for parallax and Source I motion  
  > "We conduct two-dimensional Gaussian fittings on the phase-referenced images to measure the absolute position of each maser spot." (3.3 Maser maps and proper motion measurements)
   - software: AIPS
   - assumption: annual parallax 2.39 mas  
  > "we subtract a modulation of an annual parallax of 2.39 mas (cite: kim2008)" (3.3 Maser maps and proper motion measurements)
   - fitting: _not stated_
   - validation: _not stated_
3. **Search ALMA 321 GHz H2O line and map HCOOCH3**: Spectra from long-baseline visibilities; moment 0/1/2 and position-velocity maps of HCOOCH3; compare with continuum  
  > "Figure [9](#fig-moment)(a) shows the moment 0 (integrated intensity) map of the 321.223 GHz HCOOCH$_{3}$ line superposed on the ALMA band 7 continuum emission." (3.4 Submillimeter observations with ALMA)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
4. **Interpret pumping via emissivity ratio**: Compare 22 GHz flux to 321 GHz upper limit with Neufeld & Melnick model  
  > "an upper limit of $L_{p}$(22 GHz)/$L_{p}$(321 GHz)$>$10$^{6}$ is obtained from the flux density of the 22 GHz maser of $>$10$^{5}$ Jy." (4.2 Implication for the pumping mechanism)
   - assumption: same physical properties and beaming angle for both lines  
  > "If we assume physical properties of the masing gas are common for both the 22 GHz and 321 GHz lines" (4.2 Implication for the pumping mechanism)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **AIPS** : VERA calibration and synthesis imaging  
  > "Calibration and synthesis imaging were performed using the NRAO Astronomical Image Processing System (AIPS) software package" (VERA)
- **CASA** : ALMA synthesis imaging and self-calibration  
  > "Synthesis imaging and self-calibration were done with the Common Astronomy Software Applications (CASA) package." (ALMA)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Maximum total flux density of supermaser | 135000 | not stated | Jy | 1 | The maximum total flux density of 135000 Jy is recorded on 2012/154 at the peak velocity of 7.4 km s$^{-1}$. |
| Minimum velocity width (total power) on 2012/123 | 0.50 | 0.02 | km/s | 1 | the derived velocity widths show the minimum values of 0.50$\pm$0.02 km s$^{-1}$ and 0.46$\pm$0.02 km s$^{-1}$ |
| Maser spot size at peak | 2.265 x 0.950 | 0.014 x 0.006 | mas | 2 | is 2.265$\pm$0.014 mas$\times$0.950$\pm$0.006 mas (0.95 AU$\times$0.40 AU) |
| Brightness temperature | 1.2e14 | not stated | K | 2 | corresponding to the brightness temperature of 1.2$\times10^{14}$ K |
| Isotropic luminosity | 2.4e-4 | not stated | Lsun | 2 | The isotropic luminosity is estimated to be 2.4$\times$10$^{-4}L_{\odot}$ by assuming a linewidth of 0.6 km s$^{-1}$. |
| 321 GHz H2O flux upper limit at supermaser | ~0.1 | not stated | Jy | 3 | The upper limit of the flux density of the 321 GHz H$_{2}$O line is $\sim$0.1 Jy. |
| Offset of supermaser from continuum peak | 0.3 | not stated | arcsec | 3 | The accurate position of the supermaser is significantly shifted from the continuum peak by 0.3$''$  southeast. |

## Qualitative findings

- HCOOCH3 emission is broader at the supermaser position, suggesting a shock front  
  > "This is probably an evidence of a shock front at the position close to the supermaser." (3.4 Submillimeter observations with ALMA)

## Claim tuples

- H: Is the supermaser burst symmetric in rise and fall and unsaturated? | E: VERA monitoring and linewidth-flux fits | R: Rising and falling timescales of 2-7 months, symmetric; flux-linewidth anti-correlation | F: Consistent with unsaturated maser, saturation not ruled out | **partially**
- H: Is the supermaser excited in the Compact Ridge by interaction with the low-velocity outflow? | E: Proper motions relative to Source I and ALMA HCOOCH3 and continuum maps | R: Features elongated perpendicular to the outflow; located at the edge of the HCOOCH3 condensation with a broad velocity range | F: Supports excitation in dense gas interacting with the outflow | **supported**
- H: Does the supermaser need extraordinary conditions given 321 GHz non-detection? | E: ALMA 321 GHz search compared with Neufeld & Melnick model | R: No 321 GHz line; R>1e6 | F: Explained qualitatively without extraordinary conditions | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: 13-year periodicity considered unconvincing given weaker current burst and no 1973 burst  
  > "would make the claimed periodicity of 13 years still unconvincing." (Summary)
- How they decided it was enough: _not stated_
- Limitation (authors): Model assumes a saturated maser and collisional pumping only, with superseded collision rates  
  > "We note that the model employed here is calculated under the assumption of a saturated maser" (4.2 Implication for the pumping mechanism)
- Caveat (inferred, ours): ALMA analysis details are deferred to companion papers
- Caveat (inferred, ours): Pumping interpretation is qualitative with order-of-magnitude uncertainties
- Caveat (inferred, ours): Flux totals include other maser features, although estimated at under 8%

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: ALMA cycle 0 data ADS/JAO.ALMA#2011.0.00199.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00199.S." (Acknowledgments)
- Missing: VERA data not public as stated
- Missing: ALMA processing details
- Missing: Gaussian fit and proper motion pipeline parameters
- Data volume (inferred): ~10-50 GB (ALMA cycle 0 band 7, 3 executions)
- Score (inferred): 2/5, ALMA is a minor component, processing is inherited from companion papers, and the VERA data are not clearly public.
- Rediscovery candidate: no, The recipe is incomplete and the main results depend on VERA data.

## Links

- Method: (cite: hirota2011) (VERA observations and analysis procedure)
- Companion: (cite: hirota2014a) (ALMA observations of Source I)
- Companion: (cite: hirota2014b) (ALMA continuum details)

## Checks

```json
{
 "quotes": 41,
 "quotes_ok": 41,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 26,
  "rate": 0.382
 },
 "evidence_ok": true
}
```

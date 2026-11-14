# Near-infrared Imaging Polarimetry of Inner Region of GG Tau A Disk

`2017AJ....153....7Y` | The Astronomical Journal 2017 | first author: Yang, Yi | arXiv: 1610.09134 | DOI: 10.3847/1538-3881/153/1/7

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: protoplanetary_disks, star_formation
- Question: What is the structure of the inner region of the GG Tau A circumbinary disk in NIR polarized scattered light, and what does it imply for the binary orbit and planet formation in close binaries?  
  > "it is very important to observe this region around GG Tau A with a higher spatial resolution in the NIR band." (Introduction)
- Target **GG Tau A**: coordinates _not stated_; z/distance approximately 140 pc  
  > "GG Tau is a well-known young multiple star system in the Taurus–Auriga molecular cloud at a distance of approximately 140 pc from the Solar System (cite: Kenyon1994)." (Introduction); distance from Kenyon et al. 1994 (cite: Kenyon1994)  
  > "GG Tau is a well-known young multiple star system in the Taurus–Auriga molecular cloud at a distance of approximately 140 pc from the Solar System (cite: Kenyon1994)." (Introduction)

## Data provenance

- ALMA projects: 2011.0.00059.S
- bands: _not stated_
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
- Line: CO J=6-5 (not stated)
- Other facility **Subaru/HiCIAO with AO188**: H-band polarized intensity imaging (qPDI, no mask), 0.07'' resolution; main data of the paper  
  > "The presently reported observation of GG Tau A was performed on 8 January 2015 Hawaii Standard Time using the Subaru 8.2 m Telescope" (Observations and Data Reduction)
- Other facility **Gemini North H2 observations (Beck et al. 2012)**: H2 1-0 S(1) emission map compared with the PI image  
  > "We also compared the present observations with the H$_2$ emission observations by (cite: Beck2012), which revealed the temperature distribution in the inner disk." (Discussion, Structure in the Inner Region)
- External data: ALMA CO 6-5 map and velocity field of GG Tau A, overlaid on the PI image  
  > "For a detailed comparison, the CO 6–5 image is superimposed on the present $PI$ image in Figure 3(a)." (Discussion) [from Dutrey et al. 2014 (cite: Dutrey2014)]
- External data: CO 3-2 map and CO hotspot mass of about 2 MJ  
  > "The mass of this CO hotspot reported by (cite: Tang2016) was only approximately $2M_{\rm J}$" (Discussion) [from Tang et al. 2016 (cite: Tang2016)]

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

- Circumbinary ring inclination 37 deg and PA 277 deg adopted for the toy model  
  > "we assumed the outer edge of the ring to be circular, the inclination $37^{\circ}$, and the PA i$277^{\circ}$, as in the previous observations." (Results) [from previous observations (not specified)]

### Not stated but needed to reproduce (our reading)

- The ALMA CO data are not reprocessed; the paper gives no ALMA calibration or imaging details
- Halo-fit parameters A, B, C and the Q/U halo scaling ratios are not tabulated
- Instrumental polarization correction method not described
- Toy ring model fitting procedure and parameters not given

## Analysis recipe

1. **Reduce HiCIAO qPDI data to Stokes Q, U and PI**: IRAF pipeline: flat-fielding, stripe, bad-pixel and distortion removal; o-e differences give +Q, +U, -Q, -U; Q=((+Q)-(-Q))/2, U=((+U)-(-U))/2; PI=sqrt(U^2+Q^2)  
  > "a polarized intensity ($PI$) image was constructed as $PI=\sqrt{U^{2}+Q^{2}}$." (Observations and Data Reduction)
   - software: IRAF
   - fitting: _not stated_
   - validation: _not stated_
2. **Remove polarized PSF halo**: Fit radial profiles of each star in Stokes I, scale to Q and U via photometry, combine halos with max(Ha,Hb), subtract  
  > "the final combined halo would be $H_{c}={\rm max}(H_{a},H_{b})$." (APPENDIX)
   - software: IRAF, Python
   - parameter: Profile fit L=A exp(-r^B/C^2) over 15 to 140 pixels  
  > "the profiles are fit from 15 to 140 pixels to exclude the disturbances from the central Airy disk PSF." (APPENDIX)
   - fitting: _not stated_
   - validation: Vectors become centrosymmetric after correction  
  > "the vectors are generally centrosymmetric rather than aligned in one direction, which demonstrates that the vectors were corrected successfully using this method." (APPENDIX)
3. **Polarization vector maps and real-structure identification**: Compute theta_p=0.5 tan^-1(U/Q) on binned data (7 and 3 pixels) and check centrosymmetry to distinguish disk from speckle  
  > "We calculated PAs $\theta_{p}$ using the formula $\theta_{\rm p}=0.5{\rm tan^{-1}}(U/Q)$ with binned data of 7 and 3 pixels for Figures 2(a) and (b), respectively." (Results)
   - fitting: _not stated_
   - validation: Centrosymmetry of vectors and SNR from Q and U noise  
  > "The fact that some vectors show centrosymmetric characteristics surrounding the central stars implies the presence of real disk structures." (Results)
4. **Toy model of circumbinary ring edges**: Circular outer edge, inclination 37 deg, PA 277 deg; inner edge fitted by an ellipse with the binary barycenter near one focus  
  > "we attributed the barycenter of the binary to be near one of the foci of the inner edge ellipse." (Results)
   - assumption: Distance 140 pc  
  > "In this paper, the sizes in AU are calculated by assuming that GG Tau A lies at a distance of 140 pc from the Solar System." (Results)
   - fitting: _not stated_
   - validation: _not stated_
5. **Constrain binary semi-major axis and compare with ALMA CO and H2**: Use a_peak=(3.2+2.8e)a_binary with e=0.35 and compare disk sizes with simulations; overlay Dutrey CO 6-5 and Beck H2 maps on the PI image  
  > "$$a_{peak}=(3.2+2.8e_{binary})a_{binary}," (Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **IRAF** : HiCIAO data reduction and radial profiles  
  > "The data reduction process was completed using the Image Reduction and Analysis Facility (IRAF) pipeline." (Observations and Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Separation of GG Tau Aa/Ab | 0.27 | 0.01 | arcsec (38±1 AU) | 3 | The separation between the two companion stars was derived as 0.27$\pm0.01\ensuremath{''}$, which corresponds to 38$\pm$1 AU |
| PA of GG Tau Aa/Ab | 327 | 1 | deg | 3 | The position angle (PA) of GG Tau Aa/Ab binary is $327\pm1^{\circ}$ (measured from north to east). |
| Inner edge ellipse eccentricity | approximately 0.2 | not stated | dimensionless | 4 | the inner edge can be generally fitted by an ellipse with an eccentricity of approximately 0.2 |
| Circumstellar structure extent around Aa | 28 | not stated | AU | 3 | The outermost boundary appears to extend to approximately 0.20$\ensuremath{''}$ (28 AU) in projection. |
| Disk radius limit around Ab | <13 | not stated | AU | 3 | The speckle noise around GG Tau Ab constrains its disk radius to \<13 AU. |

## Qualitative findings

- North arc coincides with the northern CO 6-5 core and may be part of a streamer from the ring.  
  > "The north arc coincides with the position of the northern CO core observed by (cite: Dutrey2014)" (Discussion)

## Claim tuples

- H: Does the inner region of GG Tau A show real disk structure? | E: Non-masked H-band polarimetric imaging with halo removal and vector centrosymmetry analysis | R: North arc to the north of Ab (>5 sigma) and a structure around Aa out to 28 AU | F: Real inner structures were detected | **supported**
- H: Is the binary SMA 32 or 62 AU? | E: Compare ring and circumstellar disk sizes with the Pelupessy formula and simulations | R: Disk sizes favor 62 AU | F: 62 AU is more likely | **partially**
- H: Is the north arc part of a streamer? | E: Overlay the Dutrey CO 6-5 and Beck H2 maps | R: The arc coincides with the CO core and lies near the H2 peak | F: It may be part of a streamer | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): No PSF reference star, so total intensity and polarization degree images could not be derived.  
  > "Therefore, the total intensity image as well as the polarization degree image ($P$ image) of the disk could not be derived" (Observations and Data Reduction)
- Caveat (inferred, ours): The ALMA comparison is qualitative, by visual overlay with published maps
- Caveat (inferred, ours): Speckle versus disk discrimination is based on vector centrosymmetry alone
- Caveat (inferred, ours): The SMA argument rests on indirect size comparisons

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Subaru SEEDS data access not stated
- Missing: Halo fit parameters and toy model details
- Data volume (inferred): Subaru data about 1 GB; ALMA data are not reprocessed.
- Score (inferred): 2/5, ALMA is only a comparison overlay with published data, and the recipe is partly qualitative.
- Rediscovery candidate: no, The main data are Subaru, the ALMA use is minor, and the results are largely qualitative.

## Links

- Companion: Dutrey et al. 2014 (cite: Dutrey2014) (ALMA CO 6-5 data compared with the PI image)
- Companion: Itoh et al. 2014 (cite: Itoh2014) (previous masked NIR observation of GG Tau A)
- Related: SEEDS

## Checks

```json
{
 "quotes": 32,
 "quotes_ok": 32,
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
  "facts": 68,
  "stated": 20,
  "rate": 0.294
 },
 "evidence_ok": true
}
```

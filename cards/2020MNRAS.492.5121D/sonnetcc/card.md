# The nuclear region of NGC 613 - I. Multiwavelength analysis

`2020MNRAS.492.5121D` | Monthly Notices of the Royal Astronomical Society 2020 | first author: da Silva, Patrícia | arXiv: 2001.07328 | DOI: 10.1093/mnras/staa007

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: Multiwavelength (optical, NIR, X-ray, radio) study of the nuclear region of NGC 613 to understand its complexity  
  > "we report a detailed study with a variety of data from optical, near-infrared, X-ray, and radio telescopes of the nuclear region of the galaxy NGC 613 with the aim of understanding its complexity" (abstract)
- Target **NGC 613**: coordinates _not stated_; z/distance 26 +/- 5 Mpc  
  > "This is an SB(rs)bc galaxy, located at 26 $\pm$ 5 Mpc (cite: distancia)" (Introduction); distance from (cite: distancia)  
  > "This is an SB(rs)bc galaxy, located at 26 $\pm$ 5 Mpc (cite: distancia)" (Introduction)

## Data provenance

- ALMA projects: 2015.1.00404.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beam size 0.43 arcsec x 0.37 arcsec; resolution 0.14 arcsec  
  > "We used here only the data cube of CO(3-2) emission line, whose beam size was 0.43 arcsec $\times$ 0.37 arcsec and resolution was 0.14 arcsec." (ALMA data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival, public archive; program 2015.1.00404.S (PI: Combes, F.)  
  > "The data from ALMA were obtained from its public archive." (ALMA data); "The observations were part of the program 2015.1.00404.S (PI: Combes, F.)" (ALMA data)
- Line: CO 3-2 (not stated)
- Other facility **HST (WFPC2, WFPC3)**: Archival images, programs 9042 and 15133 (F450W, F606W, F814W, F475W)  
  > "Those images were part of the observation programs 9042 (PI: Smartt, S. J.) and 15133 (PI: Erwin, P.)" (Hubble Space Telescope images)
- Other facility **Gemini-South GMOS IFU**: Optical data cube of the nucleus, program GS-2014B-Q-30, DIVING3D survey  
  > "The observations of NGC 613 were taken on 2015 January 25 as part of the observation program GS-2014B-Q-30 in the Gemini-South telescope." (GMOS data)
- Other facility **SOAR SIFS**: Optical IFU mosaic of the central region, Science Verification program  
  > "The data were taken on 2017 November 23 with SIFS on the SOAR telescope, during the Science Verification program." (SIFS data)
- Other facility **VLT SINFONI**: Archival H+K band IFU data cubes, program 076.B-0646(A)  
  > "The data were obtained from the public archive and were taken on 2005 October 23 and on 2005 November 13 as part of the observation program 076.B-0646(A), PI: Böker,T." (SINFONI data)
- Other facility **Chandra ACIS**: Archival X-ray observation, 14.1 h exposure (plus Mrk 202 comparison data)  
  > "The observations were taken on 2014 August 21 (PI: Garmire, G., program: 15610062), with a 14.1 h exposure, using the ACIS instrument." (Chandra data)
- External data: Distance to NGC 613, 26 +/- 5 Mpc  
  > "This is an SB(rs)bc galaxy, located at 26 $\pm$ 5 Mpc (cite: distancia)" (Introduction) [from (cite: distancia)]
- External data: Ring inclination of 55 +/- 5 deg if circular, from radio  
  > "if its structure is circular, the inclination should be 55$^{\circ}$ $\pm$ 5$^{\circ}$ (cite: hummel)" (Introduction) [from (cite: hummel)]
- External data: High-resolution X-ray data of NGC 1068 used to identify Ne lines in the circumnuclear Chandra spectrum  
  > "By comparing the circumnuclear spectrum with high-resolution data from NGC 1068 (cite: NGC1068)" (The X-ray emission) [from (cite: NGC1068)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: CO(3-2) cube used without any further treatment  
  > "we did not perform any treatment in this data cube" (ALMA data)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.07 arcsec (spaxel size of the images)  
  > "The spaxel size of the images of this data cube is 0.07 arcsec." (ALMA data)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.43 arcsec x 0.37 arcsec  
  > "We used here only the data cube of CO(3-2) emission line, whose beam size was 0.43 arcsec $\times$ 0.37 arcsec and resolution was 0.14 arcsec." (ALMA data)
- final rms: _not stated_

### Inherited from earlier work

- ALMA CO(3-2) data calibration and imaging were done in earlier publications of the same data set  
  > "these data were already been published in (cite: Combess) and (cite: audibert) works" (ALMA data) [from (cite: Combess) and (cite: audibert)]
- Superposition of the ALMA CO(3-2) image on the SINFONI H2 image matching the circumnuclear ring, as already done before  
  > "This superposition was made to match as much as possible the structure of the circumnuclear ring in both images and also was already done by (cite: audibert)." (Nuclear emission - matching the images of distinct instruments) [from (cite: audibert)]
- Details of Richardson-Lucy deconvolution and other cube treatment techniques are given elsewhere  
  > "For more details about the Richardson–Lucy deconvolution and the other treatment techniques, see (cite: rob1; rob2; gmostreat)." (Optical and NIR data cubes treatment) [from (cite: rob1; rob2; gmostreat)]

### Not stated but needed to reproduce (our reading)

- ALMA band, frequency setup, array configurations, observing dates and sensitivity of the CO(3-2) cube are not given
- Which archive product (pipeline cube or the Combes et al. / Audibert et al. cube) was downloaded, and its CASA/pipeline version
- Velocity range used to collapse the CO(3-2) cube and the moment type or weighting
- Exact image-registration offsets used to overlay ALMA on SINFONI and HST (the match was done by eye on the ring)
- Extraction radii and coordinates of the 10 H II regions and the Chandra nuclear aperture beyond the quoted radius of about 1.7 arcsec
- Butterworth filter order and cut-off, and the fingerprint-removal details of the IDL treatment scripts

## Analysis recipe

1. **Collapse the ALMA CO(3-2) cube**: Only the cube collapsed along the spectral axis was needed, so the archive cube was used with no treatment  
  > "Since we just needed the image of the cube collapsed along the spectral axis and the data has a good quality, we did not perform any treatment in this data cube." (ALMA data)
   - parameter: Image spaxel size 0.07 arcsec  
  > "The spaxel size of the images of this data cube is 0.07 arcsec." (ALMA data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Filter and deconvolve the optical and NIR cubes**: Butterworth spatial filtering, instrumental fingerprint removal, then Richardson-Lucy deconvolution  
  > "All the data cubes were spatially filtered using the Butterworth method (cite: gwoods), in order to remove the high spatial frequency noise." (Optical and NIR data cubes treatment); "Lastly, we applied the Richardson–Lucy deconvolution ((cite: rich) and (cite: lucy))." (Optical and NIR data cubes treatment)
   - software: IDL
   - parameter: GMOS: 10 iterations  
  > "The number of iterations of the deconvolution process was 10." (Optical and NIR data cubes treatment)
   - parameter: SIFS: six iterations  
  > "The process of deconvolution was performed with six iterations." (Optical and NIR data cubes treatment)
   - parameter: SINFONI: 10 iterations, resulting PSF FWHM 0.60 arcsec  
  > "The deconvolution was applied with 10 iterations and the resulting FWHM of the PSF was 0.60 arcsec." (Optical and NIR data cubes treatment)
   - assumption: SINFONI PSF taken as constant  
  > "For the SINFONI data cube, we used a constant PSF." (Optical and NIR data cubes treatment)
   - fitting: _not stated_
   - validation: Deconvolution said not to change flux values or morphology, per earlier papers  
  > "the Richardson–Lucy deconvolution does not compromise the data in anyway" (Optical and NIR data cubes treatment)
3. **Subtract the stellar continuum to get gas cubes**: Spectral synthesis on each spaxel with emission lines masked; synthetic stellar cube subtracted from the treated cube  
  > "First, we mask all the emission lines of the treated data cube and then we apply the spectral synthesis." (Optical and NIR gas data cubes)
   - software: STARLIGHT, pPXF
   - parameter: MILES stellar base for GMOS and SIFS  
  > "Medium-resolution Isaac Newton Telescope Library of Empirical Spectra (MILES, (cite: blazquez)) in the optical spectral range (GMOS and SIFS), to trace the stellar continuum and remove it." (Optical and NIR gas data cubes)
   - fitting: STARLIGHT for optical, pPXF for SINFONI K band; priors and likelihood not stated  
  > "we applied a spectral synthesis using the STARLIGHT software (cite: starlight)" (Optical and NIR gas data cubes); "we performed the spectral synthesis using the Penalized Pixel Fitting (pPXF, (cite: cappellari)) method" (Optical and NIR gas data cubes)
   - validation: _not stated_
4. **Measure optical emission-line ratios of the regions**: Extract spectra at the PSF FWHM diameter, decompose blended lines with Gaussians, correct for extinction, integrate fluxes, form ratios  
  > "The spectra of these regions were extracted from this data cube and the diameter of the extraction area was equal to the FWHM of the PSF of these data" (Optical emission-line ratios); "In order to calculate the emission-line ratios, we decomposed those blended lines in Gaussians functions." (Optical emission-line ratios)
   - assumption: Interstellar extinction correction from the Balmer decrement with the Cardelli law  
  > "By using this ratio and also the extinction law determined by (cite: cardelli), we applied the interstellar extinction correction to each spectra." (Spectra of the observed regions and emission-line decompositions)
   - fitting: Each [S II] line fitted by a sum of two Gaussian sets with free width and velocity; [N II]+H-alpha tied to [S II] widths and redshifts; priors and sampler not stated  
  > "Each line was fitted by a sum of two Gaussian functions: the green Gaussians set and the blue Gaussians set" (Spectra of the observed regions and emission-line decompositions)
   - validation: _not stated_
5. **Search for variable sources in HST images**: Convolve the 2018 F814W image with the 2001 PSF and compare normalised brightness profiles along PA 255 deg  
  > "we convolved the 2018 image with an estimate of the PSF of the 2001 image. After that, we extracted, from each image, a brightness profile from a rectangular region along a PA= 255$^{\circ}$ and with a width of 0.75 arcsec." (Nuclear variability)
   - fitting: _not stated_
   - validation: Authors note a vertical pattern that may be instrumental fingerprint remnants in the GMOS-HST difference image  
  > "We cannot discard that this image may have some instrumental fingerprint remnants, still present in the GMOS data cube after treatment, that generated this pattern." (Nuclear variability)
6. **Analyse Chandra hard and soft X-ray emission**: Build a data cube from photon positions and energies, resample and filter, compare hard X-ray profile with Mrk 202 observed with the same instrument  
  > "From the information of the images headers, referring to the positions and energy of the detected photons, we created a data cube." (Chandra data); "we compared its profile with that of Mrk 202, a Seyfert 1 galaxy (cite: mr202class) observed with the same instrument as NGC 613" (The X-ray emission)
   - software: CIAO, SHERPA
   - assumption: Ring assumed to be a circular disc when deriving radius and inclination  
  > "The best estimates of the radius and inclination, assuming it is a circular disc" (The X-ray emission)
   - assumption: Distance 26 +/- 5 Mpc implied for the pc scales (inferred link)  
  > "This is an SB(rs)bc galaxy, located at 26 $\pm$ 5 Mpc (cite: distancia)" (Introduction)
   - fitting: _not stated_
   - validation: Mrk 202 profile used as PSF reference  
  > "we compared its profile with that of Mrk 202, a Seyfert 1 galaxy (cite: mr202class) observed with the same instrument as NGC 613" (The X-ray emission)
7. **Overlay ALMA CO(3-2), SINFONI H2 and HST to locate the nuclear spiral centre**: Superpose the CO(3-2) image on the SINFONI H2 image matching the circumnuclear ring, then compare with HST to locate N1, N2 and V1 relative to the nuclear spiral  
  > "In order to compare the molecular gas emission obtained with the ALMA data cube of CO(3-2), we made a superposition with the molecular emission observed with H$_2\lambda$21218 from SINFONI data cube" (Nuclear emission - matching the images of distinct instruments); "What we see, as said previously, is V1 is the centre of the nuclear spiral." (Circumnuclear ring and nuclear spiral)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **STARLIGHT** : Stellar continuum synthesis and subtraction in GMOS and SIFS cubes  
  > "we applied a spectral synthesis using the STARLIGHT software (cite: starlight)" (Optical and NIR gas data cubes)
- **pPXF** : Stellar continuum fitting and subtraction in the SINFONI K-band cube  
  > "we performed the spectral synthesis using the Penalized Pixel Fitting (pPXF, (cite: cappellari)) method" (Optical and NIR gas data cubes)
- **IRAF** : Gemini data reduction package environment; flux calibration and telluric removal scripts  
  > "We used data reduction packages, developed by the Gemini observatory, in IRAF environment." (GMOS data)
- **IDL** : SIFS reduction scripts  
  > "The reduction was performed using scripts developed in Iteractive Data Language (IDL)" (SIFS data)
- **GASGANO** : SINFONI data reduction  
  > "The reduction of the data was performed using the GASGANO software" (SINFONI data)
- **CIAO, CHIPS, SHERPA** : Chandra X-ray Center packages named in the acknowledgements; specific use not stated  
  > "in the application packages CIAO, CHIPS, and SHERPA" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Projected N1-N2 separation (HST) | 94 | 5 | pc | 5 | The projected distance between these two stellar nuclei is 94 $\pm$ 5 pc ($0.74 \pm 0.04$ arcsec) |
| Separation of variable source V1 from [O I] centre | 0.24 | 0.04 | arcsec | 5 | are separated by $0.24 \pm 0.04$ arcsec. |
| FWHM of hard X-ray emission of NGC 613 | 1.32 | not stated | arcsec | 6 | The FWHM of the hard X-ray emission of NGC 613 is 1.32 arcsec ($\sim$ 170 pc), while the FWHM of Mrk 202 is 0.99 arcsec; the difference is 0.33 arcsec. |
| FWHM of hard X-ray emission of Mrk 202 (PSF reference) | 0.99 | not stated | arcsec | 6 | The FWHM of the hard X-ray emission of NGC 613 is 1.32 arcsec ($\sim$ 170 pc), while the FWHM of Mrk 202 is 0.99 arcsec; the difference is 0.33 arcsec. |
| FWHM of forbidden lines in N1 | ~665 | not stated | km/s | 4 | presenting fairly broad forbidden lines (FWHM $\sim$ 665 km s$^{-1}$) |
| Number of H II regions identified | 10 | not stated | dimensionless | 4 | We also identify 10 H II regions, eight of them in a star forming ring |
| SINFONI PSF FWHM after deconvolution | 0.60 | not stated | arcsec | 2 | The deconvolution was applied with 10 iterations and the resulting FWHM of the PSF was 0.60 arcsec. |

## Qualitative findings

- The inner nuclear spiral seen in CO(3-2) passes between N1 and N2  
  > "The inner part of the spiral passes between N1 and N2" (Circumnuclear ring and nuclear spiral)
- Soft X-ray emission coincides with the [O III] ionization cone  
  > "this clearly shows that there is highly ionized gas in the ionization cone." (The X-ray emission)

## Claim tuples

- H: Where is the AGN relative to the double stellar nucleus and the nuclear spiral? | E: Compared HST F814W images from 2001 and 2018 and overlaid the ALMA CO(3-2) image | R: A variable point source V1 appears between N1 and N2, 0.24 +/- 0.04 arcsec from the [O I] centre, at the centre of the nuclear spiral | F: The AGN is most likely the central variable source V1 | **partially**
- H: Is the molecular ring fed by the bar and the nuclear spiral? | E: Compared CO(3-2) from ALMA with HST dust-extinction structure | R: Dust-affected areas connect to the molecular ring; the spiral passes between N1 and N2 | F: The ring is fed by the bar and the spiral may bring gas and dust to the centre | **partially**
- H: What produces the hard X-ray emission in the circumnuclear ring? | E: Chandra hard X-ray imaging compared with Br-gamma, [Fe II] and H2 ring parameters | R: A ring with geometry consistent with the NIR and radio ring is seen in hard X-rays | F: The ring emission most likely comes from supernova remnants | **partially**
- H: Does extended soft X-ray emission trace the ionization cone? | E: Compared Chandra 0.5-2 keV image with [O III] contours | R: Good spatial coincidence between soft X-rays and [O III] emission | F: Highly ionized gas is present in the ionization cone | **supported**
- H: Is the double stellar nucleus two real nuclei? | E: Compared HST, GMOS and SINFONI morphologies and dust structure | R: A nuclear spiral and dust stream lie between N1 and N2 | F: Two hypotheses remain: one extended structure divided by dust, or two orbiting structures | **partially**

## Reasoning

- Why this data: Correlate multiwavelength results with literature data to explain the emission in the galaxy centre  
  > "The purpose of our analysis is to correlate our results with the information and data from the literature in order to explain the nature of the observed emission in the centre of this galaxy." (Introduction)
- Why this method: Richardson-Lucy deconvolution justified as preserving fluxes and morphology, per earlier papers  
  > "the Richardson–Lucy deconvolution does not compromise the data in anyway" (Optical and NIR data cubes treatment)
- Alternative: If V1 is not the AGN, the variability could indicate a supernova or dust extinction variations along the line of sight  
  > "If not, we are seeing another indication of supernova or even variations of dust extinction in the line of sight." (Nuclear variability)
- How they decided it was enough: _not stated_
- Limitation (authors): GMOS-HST difference image may contain instrumental fingerprint remnants  
  > "We cannot discard that this image may have some instrumental fingerprint remnants, still present in the GMOS data cube after treatment, that generated this pattern." (Nuclear variability)
- Limitation (authors): SIFS resolution too low to study N2  
  > "The SIFS data cube does not have enough spatial resolution to allow the visualisation of the extended emission that we see in the GMOS data cube." (Nuclear emission - matching the images of distinct instruments)
- Limitation (authors): SINFONI RA and Dec. not reliable  
  > "the values of RA and Dec. from the SINFONI data cube are not reliable" (Nuclear emission - matching the images of distinct instruments)
- Caveat (inferred, ours): ALMA-to-SINFONI registration was done by matching the ring by eye, so offsets between CO(3-2), HST and optical frames have no quoted uncertainty
- Caveat (inferred, ours): V1 as the AGN rests on a 2001 versus 2018 comparison of different instruments (WFPC2 vs WFPC3) after PSF matching, with no photometric error budget given
- Caveat (inferred, ours): Hard X-ray ring attributed to supernova remnants without spectral or source-count evidence
- Caveat (inferred, ours): ALMA data play only a qualitative role, with no flux or kinematic measurement

## Reproducibility

- Data public (paper): ALMA, HST, SINFONI and Chandra data from public archives; GMOS and SIFS access not stated  
  > "The data from ALMA were obtained from its public archive." (ALMA data); "The data were obtained from the public archive and were taken on 2005 October 23 and on 2005 November 13" (SINFONI data)
- Products in archive: _not stated_
- Missing: Velocity range and moment used to collapse the CO(3-2) cube
- Missing: Image registration offsets between ALMA, SINFONI, HST and optical data
- Missing: IDL treatment scripts and parameters (Butterworth filter, fingerprint removal) are not published in this paper
- Missing: Region extraction coordinates and Gaussian-fit starting values
- Data volume (inferred): ALMA CO(3-2) cube likely a few GB; the full multiwavelength reproduction also needs HST, Chandra, SINFONI, GMOS and SIFS data, tens of GB in total
- Score (inferred): 2/5, The ALMA step is trivial (collapse a public cube), but the results depend on non-ALMA data and proprietary IDL scripts, and registration and region extraction details are missing.
- Rediscovery candidate: no, ALMA role is a qualitative overlay, the recipe lacks key details, and the main results are mostly positions and morphology from other facilities.

## Links

- Method: (cite: rob1; rob2; gmostreat) (Data cube treatment techniques including Richardson-Lucy deconvolution and fingerprint removal)
- Companion: (cite: Combess) (Earlier publication of the same ALMA CO(3-2) data (dust torus geometry))
- Companion: (cite: audibert) (Earlier publication of the same ALMA data; nuclear spiral and molecular outflows)
- Companion: Paper II (Stellar and gas kinematics and stellar archaeology of the NGC 613 nucleus)
- Related: DIVING3D survey
- Related: ALMA program 2015.1.00404.S

## Checks

```json
{
 "quotes": 78,
 "quotes_ok": 78,
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
  "facts": 96,
  "stated": 55,
  "rate": 0.573
 },
 "evidence_ok": true
}
```

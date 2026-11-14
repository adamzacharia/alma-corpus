# The nuclear region of NGC 613 - II. Kinematics and stellar archaeology

`2020MNRAS.496..943D` | Monthly Notices of the Royal Astronomical Society 2020 | first author: da Silva, Patrícia | arXiv: 2006.09571 | DOI: 10.1093/mnras/staa1500

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: Stellar and gas kinematics and stellar archaeology of the NGC 613 nuclear region from optical and near-infrared IFU cubes (ALMA CO(3-2) used only as a comparison of gas kinematics)  
  > "In this work, we continue the study of the central region of NGC 613 by (cite: paty), by analysing the stellar and gas kinematics and the stellar archaeology in optical and near-infrared data cubes." (abstract); "with the aim of determining a dynamic and evolutionary scenario to this galaxy nucleus." (Introduction)
- Target **NGC 613**: coordinates _not stated_; z/distance 26 +/- 5 Mpc; z = 0.00494  
  > "NGC 613 is an SB(rs)bc galaxy, located at 26 $\pm$ 5 Mpc (cite: distancia)." (Introduction); "using a redshift value of 0.00494 derived from (cite: redshift613)" (Observations and data reduction); distance from (cite: distancia) for distance; (cite: redshift613) for redshift  
  > "NGC 613 is an SB(rs)bc galaxy, located at 26 $\pm$ 5 Mpc (cite: distancia)." (Introduction); "using a redshift value of 0.00494 derived from (cite: redshift613)" (Observations and data reduction)

## Data provenance

- ALMA projects: 2015.1.00404.S
- bands: _not stated_
- frequencies and spectral setup: CO(3-2) line cube  
  > "we also studied in this paper the ALMA data cube observed in the CO(3-2) line." (Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival; ALMA public archive, program 2015.1.00404.S (PI: Combes)  
  > "These data were obtained from the ALMA public archive under program 2015.1.00404.S (PI: Combes)." (Observations and data reduction)
- Line: CO 3-2 (not stated)
- Other facility **Gemini-South GMOS IFU**: Optical data cube of the inner central region (spaxel 0.05 arcsec, PSF FWHM 0.68 arcsec)  
  > "The GMOS data cube remained with the same spaxel size of 0.05 arcsec." (Observations and data reduction); "the GMOS data cube has a full width at half-maximum (FWHM) of the point spread function (PSF) equal to 0.68 arcsec, after 10 iterations." (Observations and data reduction)
- Other facility **SOAR SIFS**: Optical data cube covering the whole circumnuclear ring (spaxel 0.1 arcsec, PSF FWHM 1.6 arcsec)  
  > "Lastly, the SIFS data cube has the FWHM of the PSF equal to 1.6 arcsec, using six iterations." (Observations and data reduction)
- Other facility **VLT SINFONI**: Public archive near-infrared data cube (spaxel 0.625 arcsec, PSF FWHM 0.60 arcsec)  
  > "the public archive data obtained with the Spectrograph for Integral Field Observations in the Near Infrared (SINFONI) at the Very Large Telescope (VLT)." (Introduction); "The SINFONI data cube, with the same number of iterations, has the FWHM of the PSF equal to 0.60 arcsec." (Observations and data reduction)
- External data: Distance to NGC 613: 26 +/- 5 Mpc  
  > "NGC 613 is an SB(rs)bc galaxy, located at 26 $\pm$ 5 Mpc (cite: distancia)." (Introduction) [from (cite: distancia)]
- External data: Redshift 0.00494 used to bring spectra to the rest frame  
  > "using a redshift value of 0.00494 derived from (cite: redshift613)" (Observations and data reduction) [from (cite: redshift613)]
- External data: Stellar base for spectral synthesis built from MILES  
  > "with a base created from the Medium-resolution Isaac Newton Telescope Library of Empirical Spectra (MILES; (cite: blazquez)) in the optical wavelengths" (2.1 Spectral synthesis methods) [from (cite: blazquez)]
- External data: Circumnuclear ring mean radius (249 pc) and inclination (57 deg) taken from Table 4 of Paper I  
  > "the average values of the ring radius and inclination taken from Table 4 of Paper I" (Discussion) [from Paper I (cite: paty)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: ALMA archive CO(3-2) cube used without further treatment  
  > "It was not necessary to apply any treatment to the data since it has already good spatial resolution and high quality." (Observations and data reduction)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.07 arcsec (spaxel size of the ALMA cube)  
  > "The size of the spaxels of this data cube is 0.07 arcsec." (Observations and data reduction)
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

- All details of the data and their treatment are in Paper I  
  > "Paper I describes all the details of the data and their treatment processes (see section 2 from Paper I)." (Observations and data reduction) [from Paper I (cite: paty), section 2]
- Data-cube treatment methodology of the authors' group  
  > "All data cubes were treated with the same methodologies developed by our group (see (cite: rob1; rob2; gmostreat) for more details)." (Observations and data reduction) [from (cite: rob1; rob2; gmostreat)]
- Richardson-Lucy deconvolution parameters  
  > "Paper I presents the parameters that we used in this last process." (Observations and data reduction) [from Paper I (cite: paty)]
- Use of the ALMA CO(3-2) cube from the archive  
  > "As in Paper I, we also studied in this paper the ALMA data cube observed in the CO(3-2) line." (Observations and data reduction) [from Paper I (cite: paty)]
- Gas data cube made by subtracting the synthetic stellar cube  
  > "and to remove the stellar continuum of the data cube to study the gas emission (as done in Paper I)." (2.1 Spectral synthesis methods) [from Paper I (cite: paty)]
- Extraction regions for N1, N2 and H II regions 1-10  
  > "N1 and N2 spectra were extracted from the GMOS data cube according to Fig. 10 in Paper I before creating the gas data cube." (4.1 Results from the GMOS data cube) [from Paper I (cite: paty), Fig. 10]

### Not stated but needed to reproduce (our reading)

- ALMA observation details for 2015.1.00404.S (array configuration, resolution, sensitivity, channel width, beam) are not given
- Which archive product (pipeline cube, version, imaging parameters) was used for the CO(3-2) cube
- How the RGB velocity composites were built (velocity channel limits, colour mapping, scaling)
- STARLIGHT settings (fitting window, extinction law, masks, number of base elements) and the full age/metallicity grid of the MILES base
- Richardson-Lucy parameters and Butterworth filter parameters (only in Paper I or earlier papers)
- pPXF settings (templates, degree of polynomials, velocity ranges, number of Gauss-Hermite moments beyond h3, SINFONI K-band base details)
- Optical and SINFONI cubes: Gemini/SOAR/VLT observation IDs and data availability are not stated
- Spectral-index choices and test details for the featureless continuum power laws

## Analysis recipe

1. **Reduce and treat the IFU data cubes**: Reduction (IRAF for GMOS, IDL scripts for SIFS, GASGANO for SINFONI), differential refraction correction, median combination, resampling, Butterworth spatial filtering, fingerprint removal and Richardson-Lucy deconvolution  
  > "The reduction process of the GMOS data was performed in an IRAF environment and that of the SIFS data with scripts developed in Interactive Data Language (IDL). The SINFONI data were reduced using the GASGANO software." (Observations and data reduction); "The Butterworth spatial filtering was applied (cite: gwoods) to all data cubes." (Observations and data reduction)
   - software: IRAF, IDL, GASGANO
   - parameter: Richardson-Lucy iterations: 10 (GMOS), 10 (SINFONI), six (SIFS)  
  > "The SINFONI data cube, with the same number of iterations, has the FWHM of the PSF equal to 0.60 arcsec." (Observations and data reduction); "Lastly, the SIFS data cube has the FWHM of the PSF equal to 1.6 arcsec, using six iterations." (Observations and data reduction)
   - assumption: Redshift 0.00494 for rest-frame conversion  
  > "using a redshift value of 0.00494 derived from (cite: redshift613)" (Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Spectral synthesis for stellar populations and gas cube**: STARLIGHT synthesis with MILES base on each spectrum of the GMOS and SIFS cubes; flux fractions by age and metallicity; synthetic stellar cube subtracted to obtain the gas data cube  
  > "The spectral synthesis is applied to each spectrum of the data cube, and is performed by a linear combination of the base spectra, in order to fit the observed spectra." (2.1 Spectral synthesis methods); "We obtain a cube with mainly gas emission, which we call gas data cube." (2.1 Spectral synthesis methods)
   - software: STARLIGHT
   - parameter: Power-law featureless continuum tests with spectral indexes between 1.0 and 1.9  
  > "applying the spectral synthesis with power laws with different spectral indexes (with values between 1.0 and 1.9)" (6.1 Stellar archaeology)
   - assumption: Featureless AGN continuum represented by a power law with spectral index of 1.5  
  > "the featureless continuum of the AGN (represented by a power law with spectral index of 1.5)" (6.1 Stellar archaeology)
   - fitting: Linear combination of base spectra  
  > "is performed by a linear combination of the base spectra, in order to fit the observed spectra." (2.1 Spectral synthesis methods)
   - validation: Monte Carlo noise realisations give median-age uncertainty of 0.02 dex; degeneracies of the method acknowledged as unquantifiable  
  > "The representative uncertainty of the process was taken as the highest value of the uncertainties determined for the median ages. The result obtained is 0.02 dex." (2.1 Spectral synthesis methods); "It is not possible to determine an uncertainty to those degeneracies" (2.1 Spectral synthesis methods)
3. **Gas kinematics from channel maps and RGB compositions**: Channel maps of Halpha and [O III] (GMOS, SIFS) and RGB velocity compositions of Br gamma, [Fe II], H2 (SINFONI) and the ALMA CO(3-2) cube  
  > "When we look at the RGB composition of the ALMA data cube of the inner centre (Fig. 4b), we see that the nuclear spiral has an opposite pattern in the nucleus" (3.3 Near-infrared (NIR) and molecular gas kinematics (SINFONI and ALMA))
   - parameter: Halpha outflow channel v = 306 km/s, PA ~ 17 deg  
  > "we took the channel with v= 306 km s$^{-1}$ and the PA of this emission is $\sim$ 17$^{\circ}$." (3.2 Inner central optical gas kinematics (GMOS))
   - fitting: _not stated_
   - validation: Kinematics compared across GMOS, SIFS, SINFONI and ALMA cubes  
  > "is consistent with what we see in the SINFONI and ALMA data" (3.4 Circumnuclear optical gas kinematics (SIFS))
4. **Stellar kinematics with pPXF**: pPXF with the same spectral base as the stellar archaeology, Gauss-Hermite coefficients h1, h2, h3 mapped for GMOS and SIFS; SINFONI spectra from concentric rings 3 spaxels thick  
  > "In this case, we used the same spectral base used for the stellar archaeology." (5 Stellar kinematics); "the pPXF method was applied to spectra extracted from concentric rings around V1, with 3 spaxels of thickness." (5.3 NIR stellar velocity dispersion obtained from SINFONI data cube)
   - software: pPXF
   - parameter: Kinematic centre defined as the point along the line of nodes where velocity equals the average of maximum and minimum velocity  
  > "The kinematic centre was defined as the point, along the line of nodes, with a velocity value equal to the average between the maximum and minimum velocity values." (5.1 Inner central stellar kinematics obtained from the GMOS data cube)
   - fitting: Gauss-Hermite expansion of the line-of-sight velocity distribution  
  > "which is more precise, as the spectral base is convolved with a Gauss–Hermite expansion." (5 Stellar kinematics)
   - validation: Monte Carlo with noise histogram from line-free spectral intervals; uncertainty is standard deviation over noisy realisations  
  > "At the end, the pPXF was applied to each one of those “synthetic noisy spectra” and the final uncertainty of the stellar velocity dispersion was taken as the standard deviation of all the obtained values." (5.3 NIR stellar velocity dispersion obtained from SINFONI data cube)
5. **Flux-weighted central stellar velocity dispersion from SINFONI**: Weighted mean of the pPXF dispersion map with integrated spaxel fluxes as weights; uncertainty from maps with the uncertainty map added and subtracted  
  > "we calculated a weighted mean of the values of the map obtained with the pPXF from the SINFONI data cube, taking as weights the integrated fluxes of each spaxel." (5.3 NIR stellar velocity dispersion obtained from SINFONI data cube)
   - software: pPXF
   - fitting: _not stated_
   - validation: Compared with the cross-correlation value of the literature  
  > "is compatible with the value obtained by (cite: batcheldor) using the cross-correlation method." (6.3 Stellar kinematics)
6. **Ring rotation timescale vs spectral-synthesis time resolution**: Time to complete one turn from representative ring velocity ~100 km/s, mean ring radius and inclination from Paper I  
  > "we conclude that the time necessary for a group of stars to complete a turn around the ring is $\sim$ 8 $\times~10^6$ yr." (6.3 Stellar kinematics)
   - parameter: v ~ 100 km/s; R = 249 pc; i = 57 deg  
  > "we could estimate a representative velocity for the stars of the circumnuclear ring, v $\sim$ 100 km s$^{-1}$, rotating around the nucleus." (6.3 Stellar kinematics)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **STARLIGHT** : Spectral synthesis of GMOS and SIFS spectra for stellar archaeology and gas cube  
  > "spectral synthesis was applied, using the STARLIGHT software (cite: starlight)" (2.1 Spectral synthesis methods)
- **pPXF** : Stellar kinematics (GMOS, SIFS, SINFONI) and K-band gas cube  
  > "The penalized pixel fitting method (pPXF; (cite: cappellari)) was used in the SINFONI data cube." (2.1 Spectral synthesis methods)
- **IRAF** : GMOS data reduction  
  > "The reduction process of the GMOS data was performed in an IRAF environment" (Observations and data reduction)
- **IDL** : SIFS reduction scripts and data-cube treatment scripts  
  > "those were treated using scripts also written in IDL." (Observations and data reduction)
- **GASGANO** : SINFONI data reduction  
  > "The SINFONI data were reduced using the GASGANO software." (Observations and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Flux-weighted mean central stellar velocity dispersion (SINFONI) | 92 | 3 | km/s | 5 | The value obtained was 92 $\pm$ 3 km s$^{-1}$. |
| Central peak of stellar velocity dispersion (SINFONI) | ~144 | not stated | km/s | 4 | a peak of the stellar velocity dispersion at the centre, with a value of $\sim$ 144 km s$^{-1}$. |
| Central stellar velocity dispersion (GMOS) | ~126 | not stated | km/s | 4 | The velocity dispersion at the centre of the curve is $\sim$ 126 km s$^{-1}$ |
| Central stellar velocity dispersion (SIFS) | ~123 | not stated | km/s | 4 | The value of the velocity dispersion at the centre is $\sim$ 123 km s$^{-1}$. |
| Representative uncertainty of median stellar ages | 0.02 | not stated | dex | 2 | The result obtained is 0.02 dex. |
| Offset of SIFS stellar kinematic centre from V1 | 0.66 | 0.11 | arcsec | 4 | being at a distance of 0.66 $\pm$ 0.11 arcsec. |
| PA of line of nodes, stellar velocity map (SIFS) | -70 | 1 | deg | 4 | The PA of the line of nodes is –70$^{\circ}$ $\pm$ 1$^{\circ}$ |
| PA of line of nodes, stellar velocity map (GMOS) | -62 | 3 | deg | 4 | the PA of the line of nodes of the GMOS results, which is –62$^{\circ}$ $\pm$ 3$^{\circ}$. |
| Halpha redshifted outflow velocity channel (GMOS) | 306 | not stated | km/s | 3 | we took the channel with v= 306 km s$^{-1}$ and the PA of this emission is $\sim$ 17$^{\circ}$. |
| Halpha outflow position angle (GMOS) | ~17 | not stated | deg | 3 | we took the channel with v= 306 km s$^{-1}$ and the PA of this emission is $\sim$ 17$^{\circ}$. |
| Time for stars to complete one turn of the circumnuclear ring | ~8e6 | not stated | yr | 6 | the time necessary for a group of stars to complete a turn around the ring is $\sim$ 8 $\times~10^6$ yr. |
| [O III] outflow near ionization cone axis: PA and velocity (SIFS) | PA ~ 55 deg, v = -710 km/s | not stated | deg; km/s | 3 | PA $\sim$ 55$^{\circ}$ and v = –710 km s$^{-1}$, observed with the SIFS data cube |

## Qualitative findings

- An inner circumnuclear ring of ~1e9 yr stellar populations with radius ~1 arcsec lies between the nucleus and the H II-region ring  
  > "allowed the detection, using spectral synthesis methods, of an inner circumnuclear ring, with a radius of $\sim$ 1 arcsec, composed of $\sim$ 10$^9$-yr stellar populations." (abstract)
- No featureless AGN continuum detected in the optical cubes  
  > "The spectral synthesis results confirm that there is no featureless continuum emission detected in the optical data cubes." (7 Conclusions)
- N1 and N2 show no difference in stellar populations or stellar velocity, consistent with being one structure  
  > "There is no difference regarding the stellar populations and the stellar kinematics along the double stellar emission" (abstract)

## Claim tuples

- H: Is there an intermediate-age stellar structure inside the known circumnuclear ring? | E: STARLIGHT synthesis over the full GMOS FOV with flux maps per stellar population | R: 1e9 yr population concentrates in a ring of radius ~1 arcsec between nucleus and the circumnuclear ring | F: An inner circumnuclear ring of intermediate-age stars exists | **supported**
- H: Do gas outflows exist and align with the radio jet and ionization cone? | E: Channel maps of Halpha and [O III] in GMOS and SIFS cubes | R: Halpha outflow PA ~17 deg at 306 km/s; [O III] outflows at PA ~43-55 deg and PA ~-10 deg | F: Three outflow components are detected; Halpha one aligns with the radio jet and one [O III] one with the ionization cone axis | **supported**
- H: Are N1 and N2 parts of the same structure separated by a dust lane? | E: Spectral synthesis and pPXF kinematics for N1 and N2 | R: No significant differences in populations or stellar velocity | F: N1 and N2 belong to the same structure | **supported**
- H: Can the age gradient of the H II regions confirm the 'pearls on string' scenario? | E: Spectral synthesis of H II regions and ring rotation timescale estimate | R: Ring turn time ~8e6 yr is shorter than the temporal resolution of the spectral synthesis | F: More precise methods are needed to test the scenario | **partially**

## Reasoning

- Why this data: Continuation of Paper I using the same Gemini GMOS, SOAR SIFS, VLT SINFONI and ALMA cubes  
  > "This work is a continuation of (cite: paty), hereafter Paper I" (Introduction)
- Why this method: _not stated_
- Alternative: Power-law featureless continua with spectral indexes 1.0-1.9 were tested; no credible evidence for a featureless continuum was found  
  > "however, we did not find credible evidence for the presence of a featureless continuum" (6.1 Stellar archaeology)
- How they decided it was enough: _not stated_
- Limitation (authors): Degeneracies in spectral synthesis cannot be assigned an uncertainty  
  > "It is not possible to determine an uncertainty to those degeneracies" (2.1 Spectral synthesis methods)
- Limitation (authors): Insufficient spectral resolution prevents separating channels in the molecular gas RGB  
  > "due to the insufficient spectral resolution." (3.3 Near-infrared (NIR) and molecular gas kinematics (SINFONI and ALMA))
- Limitation (authors): Low S/N of SINFONI cube prevented pPXF parameter maps  
  > "the low S/N prevented the construction of pPXF parameters maps that could be interpreted." (5.3 NIR stellar velocity dispersion obtained from SINFONI data cube)
- Caveat (inferred, ours): ALMA plays a minor role: only a qualitative CO(3-2) RGB comparison, no quantitative ALMA measurement
- Caveat (inferred, ours): Main results (STARLIGHT ages, pPXF dispersions) rely on optical/NIR cubes whose data availability and settings are not given here
- Caveat (inferred, ours): Kinematic centre and line-of-nodes PAs have no stated fitting method beyond the max/min definition
- Caveat (inferred, ours): Single pPXF/STARLIGHT run per region with no template-mismatch tests

## Reproducibility

- Data public (paper): ALMA cube from the public archive; SINFONI from the public archive; GMOS and SIFS availability not stated  
  > "These data were obtained from the ALMA public archive under program 2015.1.00404.S (PI: Combes)." (Observations and data reduction); "the public archive data obtained with the Spectrograph for Integral Field Observations in the Near Infrared (SINFONI) at the Very Large Telescope (VLT)." (Introduction)
- Products in archive: _not stated_
- Missing: Paper I details for data treatment and Richardson-Lucy parameters
- Missing: STARLIGHT and pPXF configuration files
- Missing: ALMA observation setup, beam and archive product used
- Missing: Region extraction coordinates (only in Paper I, Fig. 10)
- Data volume (inferred): Small for the ALMA part (one CO(3-2) cube, likely a few GB of archive product); additional GMOS/SINFONI cubes required
- Score (inferred): 2/5, ALMA data are public but only a minor qualitative component; the quantitative results depend on non-ALMA cubes and on unpublished treatment parameters deferred to Paper I and earlier papers.
- Rediscovery candidate: no, ALMA data are secondary and the main numeric results come from optical/NIR cubes with incomplete, inherited recipes.

## Links

- Method: (cite: rob1; rob2; gmostreat) (Data-cube treatment methodology applied to all cubes)
- Method: (cite: starlight) (Spectral synthesis code)
- Method: (cite: cappellari) (pPXF method)
- Companion: Paper I (cite: paty) (Describes data, treatment parameters, regions and ring properties used here)
- Related: ALMA program 2015.1.00404.S (PI: Combes)

## Checks

```json
{
 "quotes": 85,
 "quotes_ok": 85,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 93,
  "stated": 53,
  "rate": 0.57
 },
 "evidence_ok": true
}
```

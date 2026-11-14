# Chemical and Physical Picture of IRAS 16293-2422 Source B at a Sub-arcsecond Scale Studied with ALMA

`2018ApJ...854...96O` | The Astrophysical Journal 2018 | first author: Oya, Yoko | arXiv: 1801.04174 | DOI: 10.3847/1538-4357/aaa6c7

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, astrochemistry
- Question: What are the chemical differentiation, kinematic structure, outflow and gas temperature around IRAS 16293-2422 Source B at sub-arcsecond scale, compared with Source A?  
  > "In this study, we analyze molecular distributions and the kinematic structure of this source at a sub-arcsecond resolution, and compare the results with those of Source A." (1 Introduction)
- Target **IRAS 16293-2422 Source B**: coordinates continuum peak 16h32m22.61531s, -24d28m32.5467s (J2000)  
  > "IRAS 16293–2422 is a well-studied Class 0 protostellar source in Ophiuchus ($d = 120$ pc) (cite: KnudeHog1998)." (1 Introduction); z/distance 120 pc  
  > "IRAS 16293–2422 is a well-studied Class 0 protostellar source in Ophiuchus ($d = 120$ pc) (cite: KnudeHog1998)." (1 Introduction); distance from Knude & Hog 1998  
  > "IRAS 16293–2422 is a well-studied Class 0 protostellar source in Ophiuchus ($d = 120$ pc) (cite: KnudeHog1998)." (1 Introduction)

## Data provenance

- ALMA projects: 2012.1.00712.S, 2015.1.01060.S
- bands: Band 6, 230-250 GHz and 220-240 GHz (Cycle 1); SiO at ~260 GHz (Cycle 3)  
  > "in Band 6 (#2012.1.00712.S), which covers the frequency ranges from 230 to 250 GHz and from 220 to 240 GHz." (2 Observations)
- frequencies and spectral setup: 122 kHz resolution (0.15 km/s at 240 GHz); 468.75 MHz bandwidth (Cycle 1); 58.6 MHz bandwidth (Cycle 3)  
  > "The backend correlator was tuned to a resolution of 122 kHz, which corresponds to the velocity resolution of 0.15 km s$^{-1}$ at 240 GHz, and a bandwidth of 468.750 MHz." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 17 to 636 m (Cycle 3)  
  > "41 antennas were used in these observations with the baseline length ranging from 17 to 636 m." (2 Observations)
- angular resolution: _not stated_
- max recoverable scale: ~13'' at 240 GHz (Cycle 1); ~14'' at 260 GHz (Cycle 3)  
  > "The largest recoverable scale is $\sim$13$''$ at 240 GHz." (2 Observations)
- sensitivity: _not stated_
- time on source: 16.38 min (Cycle 3)  
  > "The total on-source time was 16.38 minutes with typical system temperature of (60–140) K." (2 Observations)
- observing dates: Cycle 3: 5 March 2016  
  > "ALMA Cycle 3 data, which were carried out on 5 March 2016 (#2015.1.01060.S)" (2 Observations)
- pi or archival as stated: _not stated_
- Line: OCS J=19-18 (231.0609934 GHz)
- Line: CH3OH 5(1,5)-4(1,4); A+ (239.746253 GHz)
- Line: HCOOCH3 20(3,17)-19(3,16); A (250.25837 GHz)
- Line: H2CS 7(0,7)-6(0,6) (240.2668724 GHz)
- Line: H2CS 7(2,5)-6(2,4) (240.5490662 GHz)
- Line: SiO J=6-5 (260.5180090 GHz)
- External data: Excitation temperatures of 100-300 K at 0.5'' from the protostar  
  > "Since the excitation temperatures employed by (cite: Coutens_PILS) are between 100 and 300 K at 0.5$''$ from the protostar" (3.2 Chemical Differentiation) [from (cite: Coutens_PILS)]
- External data: Systemic velocity ~3 km/s  
  > "Since the systemic velocity is around 3 km s$^{-1}$ (cite: Bottinelli_Mass)" (3.1 Overall Distributions) [from (cite: Bottinelli_Mass)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (Cycle 3)  
  > "the absolute flux density scale was derived from Titan." (2 Observations)
- flux scale uncertainty: less than 10 %  
  > "The data calibration was performed in the antenna-based manner and uncertainties are less than 10 % (cite: TechHB_Cyc1)." (2 Observations)
- self calibration: Applied to Cycle 1 data using continuum; not applied to Cycle 3 SiO data  
  > "Self-calibration using the continuum emission was applied to the ALMA Cycle 1 data (the continuum, OCS, CH$_3$OH, HCOOCH$_3$, and H$_2$CS)." (2 Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "The Brigg’s weighting with the robustness parameter of 0.5 was employed to obtain the images of the continuum and the spectral lines." (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum subtracted directly from visibilities; continuum from line-free channels of two Cycle 1 data sets (7.5 GHz)  
  > "The line images were obtained by subtracting the continuum data directly from the visibilities." (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: continuum 0.524'' x 0.463'' (PA 73.87 deg); line beams in Table 1  
  > "The synthesized beam is $(0.524\ensuremath{''} \times 0.463\ensuremath{''})$" (3.1 Overall Distributions)
- final rms: _not stated_

### Inherited from earlier work

- Observation details of Cycle 1 data  
  > "The details of the observations are reported by (cite: Jorgensen_Cycle1) and (cite: Oya_16293A)." (2 Observations) [from (cite: Jorgensen_Cycle1); (cite: Oya_16293A)]
- Infalling-rotating envelope ballistic model  
  > "using the infalling-rotating envelope model by (cite: Oya_15398)." (5.1 Infalling-Rotating Envelope Model) [from (cite: Oya_15398)]

### Not stated but needed to reproduce (our reading)

- Calibration pipeline/manual and CASA version
- Line-free channel selection and continuum channel ranges
- Self-calibration solution intervals and number of iterations
- Cell size, image size, masks, clean threshold
- Imaging software (not named)
- Details of ballistic model implementation and fitting procedure for M and r_CB
- RADEX collision data and column density/linewidth inputs for Tkin
- Calibrators for Cycle 1 data

## Analysis recipe

1. **Make continuum and line images**: Continuum from line-free channels; continuum subtracted in visibilities; Briggs robust 0.5; self-calibration on Cycle 1 data  
  > "The 1.3 mm (236 GHz) continuum image was obtained by averaging the line-free channels of the two Cycle 1 data (230 and 240 GHz), whose total band width is 7.5 GHz." (2 Observations)
   - fitting: _not stated_
   - validation: Compared Source B continuum peak position with and without self-calibration (diff ~0.03'')  
  > "the difference from the position derived from the self-calibrated data is very small ($\sim0.03\ensuremath{''}$)" (3.1 Overall Distributions)
2. **Measure continuum size, flux and position**: Two-dimensional Gaussian fit to the continuum image  
  > "are determined by a two-dimensional Gaussian fit to the image." (3.1 Overall Distributions)
   - fitting: _not stated_
   - validation: _not stated_
3. **Check optical depth and excitation effects on chemical differentiation**: Non-LTE RADEX calculation with Tkin 100 K, n(H2) 1e8 cm-3  
  > "Here, we used the RADEX code (cite: vanderTak_radex) assuming a kinetic temperature of 100 K and a $n$(H$_2$) of $10^8$ cm$^{-3}$." (3.2 Chemical Differentiation)
   - software: RADEX
   - fitting: _not stated_
   - validation: Results unchanged for n(H2) 1e6-1e9 cm-3  
  > "the above results for the optical depths do not change significantly for a $n$(H$_2$) from $10^6$ to $10^9$ cm$^{-3}$." (3.2 Chemical Differentiation)
4. **Model PV diagrams with infalling-rotating envelope**: Compare model PV diagrams with H2CS PV along PA 110 deg for sets of M and r_CB; model convolved with beam  
  > "we evaluate the physical parameters by comparing the model with this PV diagram." (5.1 Infalling-Rotating Envelope Model)
   - parameter: thickness 50 au, outer radius 300 au, inclination 5 deg, line width 0.5 km/s, systemic velocity 2.9 km/s  
  > "We assume an envelope with a constant thickness of 50 au and the outer radius of 300 au with the inclination angle of 5$^\circ$ (0$^\circ$ for a face-on configuration)." (5.1 Infalling-Rotating Envelope Model)
   - assumption: Emissivity proportional to H2 density (n ∝ r^-1.5), no radiative transfer  
  > "the emissivity is simply assumed to be proportional to the H$_2$ density ($n$(H$_2$) $\propto r^{-1.5}$) in the infalling-rotating envelope, and no radiative transfer effect is considered in this model." (5.1 Infalling-Rotating Envelope Model)
   - fitting: By-eye comparison of models  
  > "Especially, the models with $r_{\rm CB}$ of 40 au well reproduce the observations except for the absorption feature." (Modelling)
   - validation: Inclination 0 deg, negative, or >15 deg cannot reproduce the velocity structure  
  > "Likewise, the velocity structure cannot be reproduced either with the inclination angle larger than 15$^\circ$." (5.1 Infalling-Rotating Envelope Model)
5. **Free-fall model for inverse P-Cygni absorption**: Spherical clump of radius r_CB=40 au free-falling onto protostar  
  > "We approximate the gas distribution around the protostar as a spherical clump with a radius of the centrifugal barrier for simplicity." (5.2 Origin of the inverse P-Cygni Profile)
   - fitting: _not stated_
   - validation: _not stated_
6. **Derive gas kinetic temperature**: RADEX with H2CS line ratios at offsets 0, 60, 120 au along PA 110 deg using 1 km/s wide integrated maps  
  > "we prepare the integrated intensity maps of the three H$_2$CS lines ($7_{0,7}-6_{0,6}$; $7_{2,5}-6_{2,4}$; $7_{4}-6_{4}$) with the velocity width of 1 km s$^{-1}$." (7 Gas Kinetic Temperature)
   - software: RADEX
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **RADEX** : Non-LTE optical depth and gas kinetic temperature  
  > "The gas kinetic temperature is evaluated by using the non-LTE code RADEX (cite: vanderTak_radex)" (7 Gas Kinetic Temperature)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Source B continuum peak flux density | 899.9 | 1.5 | mJy/beam | 2 | The peak flux densities are $(314.0 \pm 1.4)$ and $(899.9 \pm 1.5)$ mJy/beam for Source A and Source B, respectively. |
| Source B deconvolved continuum FWHM | 0.429'' x 0.357'' (PA 139.0 deg) | 0.003''; 0.003''; 1.6 deg | arcsec | 2 | $(0.429\ensuremath{''} \pm 0.003\ensuremath{''}) \times (0.357\ensuremath{''} \pm 0.003\ensuremath{''})$ (PA $139.\!\!\ensuremath{^\circ}0 \pm 1.\!\!\ensuremath{^\circ}6$) |
| Protostellar mass | 0.4 | within a factor of 2 | Msun | 4 | it is estimated to be around 0.4 $M_\odot$ within a factor of 2 assuming the inclination angle of the disk/envelope system of 5$^\circ$. |
| Centrifugal barrier radius | 30-50 | not stated | au | 4 | Hence, $r_{\rm CB}$ is evaluated to be $(30-50)$ au. |
| OCS optical depth at -1'' | ~0.2 | rough | dimensionless | 3 | the optical depths of the OCS and CH$_3$OH lines are roughly estimated to be about 0.2 and 0.01, respectively |
| Gas kinetic temperature within 60 au | ~100 | not stated | K | 6 | The gas kinetic temperature is as high as $\sim$100 K within the radius of 60 au. |

## Qualitative findings

- OCS and H2CS are more extended than CH3OH and HCOOCH3, as in Source A  
  > "OCS and H$_2$CS have more extended distributions than CH$_3$OH and HCOOCH$_3$." (6 Summary)

## Claim tuples

- H: Source B shows chemical differentiation like Source A | E: Integrated intensity maps and profiles of OCS, CH3OH, HCOOCH3, H2CS | R: OCS extended over >1''; COMs within 0.6'' | F: Chemical differentiation similar to Source A, not due to excitation | **supported**
- H: Face-on Source B envelope shows infall-rotation with a centrifugal barrier | E: Ballistic model compared to H2CS PV diagram | R: M~0.4 Msun, r_CB 30-50 au | F: Modest rotation consistent with the infalling-rotating envelope model | **supported**
- H: SiO traces an outflow from Source B | E: SiO moment and PV maps | R: overlapping blue and red shell-like lobes | F: Likely Source B pole-on outflow, but interaction with Source A outflow not ruled out | **partially**
- H: Gas temperature structure around Source B | E: RADEX with H2CS line ratios | R: ~100 K within 60 au, rising inward | F: No enhancement at the centrifugal barrier unlike Source A | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: SiO emission from Source A outflow interaction disfavoured because CO outflow from A is blue-shifted while SiO has red component  
  > "We favor this possibility, because the CO outflow from Source A is blue-shifted while the SiO emission has the red-shift component." (6 Outflow)
- How they decided it was enough: _not stated_
- Limitation (authors): Mass poorly constrained due to absorption; free-fall picture tentative; limited resolution  
  > "it is not well constrained due to the contamination of the absorption feature." (5.1 Infalling-Rotating Envelope Model)
- Caveat (inferred, ours): Model comparison by eye without formal fit or uncertainties
- Caveat (inferred, ours): Tkin ranges depend on unstated RADEX inputs
- Caveat (inferred, ours): Inverse P-Cygni absorption contaminates red-shifted kinematics

## Reproducibility

- Data public (paper): Cycle 1 and 3 archival data with project codes  
  > "This paper makes use of the ALMA data set ADS/JAO.ALMA#2012.1.00712.S and #2015.1.01060.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters and self-cal details
- Missing: Model code and fitting procedure
- Missing: RADEX input parameters
- Data volume (inferred): ~50-100 GB
- Score (inferred): 3/5, Public data and clear lines, but imaging and model details are sparse and the model comparison is qualitative.
- Rediscovery candidate: no, Key results rely on by-eye model comparison and unstated settings.

## Links

- Method: (cite: Oya_15398) (Infalling-rotating envelope model)
- Method: (cite: vanderTak_radex) (RADEX code)
- Companion: (cite: Oya_16293A) (Source A analysis of same Cycle 1 data)
- Companion: (cite: Jorgensen_Cycle1) (Observation details)
- Related: PILS

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 37,
  "rate": 0.521
 },
 "evidence_ok": true
}
```

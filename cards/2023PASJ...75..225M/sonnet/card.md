# An expanding ring of the hypercompact H II region W 49 N:A2

`2023PASJ...75..225M` | Publications of the Astronomical Society of Japan 2023 | first author: Miyawaki, Ryosuke | arXiv: 2212.01999 | DOI: 10.1093/pasj/psac105

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation
- Question: What is the structure and kinematics of the ionized ring in the hypercompact HII region W49N:A2, and what does it imply for how a massive star ends accretion?  
  > "In this paper, we present the 250 GHz continuum and H29$\alpha$ line data for W49N:A2 and examine its kinematics." (Introduction)
- Target **W49N:A2**: coordinates phase center α(ICRS)=19h10m13.300s (Dec text garbled in source)  
  > "We assume the distance to W49N to be 11.11$^{+0.79}_{-0.69}$ kpc (cite: Zhang2013) throughout this paper." (Introduction); "The phase center was $\alpha$(ICRS) = 19$^{\rm h}$10${\rm ^m}$13 s 300" (ALMA archival data); z/distance 11.11 (+0.79/-0.69) kpc  
  > "We assume the distance to W49N to be 11.11$^{+0.79}_{-0.69}$ kpc (cite: Zhang2013) throughout this paper." (Introduction); "The phase center was $\alpha$(ICRS) = 19$^{\rm h}$10${\rm ^m}$13 s 300" (ALMA archival data); distance from Zhang2013  
  > "We assume the distance to W49N to be 11.11$^{+0.79}_{-0.69}$ kpc (cite: Zhang2013) throughout this paper." (Introduction); "The phase center was $\alpha$(ICRS) = 19$^{\rm h}$10${\rm ^m}$13 s 300" (ALMA archival data)

## Data provenance

- ALMA projects: 2018.1.00520.S, 2018.1.00589.S, 2016.1.00620.S, 2015.1.01535.S, 2017.1.00318.S, 2017.1.01499.S
- bands: _not stated_
- frequencies and spectral setup: Four ~2 GHz spectral windows: 240.76–242.63, 242.61–244.49, 255.86–257.74, 257.70–259.57 GHz  
  > "Four spectral windows (240.76–242.63 GHz, 242.61–244.49 GHz, 255.86–257.74 GHz, and 257.70–259.57 GHz), each covering a $~2$ GHz bandwidth" (ALMA archival data)
- continuum bandwidth: _not stated_
- arrays: 12-m, 43–48 antennas  
  > "The observations were performed from July 2019 to September 2019 using 43–48 12-m antennas." (ALMA archival data)
- configurations: _not stated_
- baselines: 38.4 m to 3637.7 m  
  > "The shortest and longest baselines for the 12-m antennas were 38.4 m and 3637.7 m, respectively." (ALMA archival data)
- angular resolution: continuum 0.046'' x 0.032'' (PA 70.3); H29α 0.052'' x 0.033''  
  > "The synthesized beam size of the continuum image was 0.046$''$ $\times$ 0.032$''$ (PA=$70.3\degree$) at the effective frequency of 250 GHz" (ALMA archival data)
- max recoverable scale: _not stated_
- sensitivity: 0.7 mJy/beam continuum; 2.0 mJy/beam line  
  > "The resultant noise levels were 0.7 mJy beam$^{-1}$ and 2.0 mJy beam$^{-1}$ for the continuum and line maps, respectively." (ALMA archival data)
- time on source: 3.1 hours total of three data sets; second not used  
  > "We analyzed three sets of data 3.1 hours long in total, but the second set showed a large noise level" (ALMA archival data)
- observing dates: July 2019 to September 2019  
  > "The observations were performed from July 2019 to September 2019" (ALMA archival data)
- pi or archival as stated: Archival, PI D. Wilner  
  > "(#2018.1.00520.S: PI D. Wilner)" (ALMA archival data)
- Line: H29α recombination line (not stated (image at 256 GHz))
- External data: 45 GHz continuum map of W49N:A2 (contours, flux 0.47 Jy)  
  > "This feature was first noted by (cite: DePree2000) in their 45 GHz continuum map" (Continuum and H29α Rings) [from (cite: DePree2000)]
- External data: Ionizing photon luminosity equivalent to O9 ZAMS and ionized gas mass 0.12 Msun  
  > "has the total ionized gas mass of 0.12 M$_\odot$ (cite: DePree2020)" (Introduction) [from (cite: DePree2020)]
- External data: O9 star mass 20±7 Msun  
  > "which should have a mass of 20$\pm$7 M$_\odot$[^4] (cite: Hohle2010)" (Expanding ring of ionized gas and its implication) [from (cite: Hohle2010)]
- External data: Distance 11.11 kpc  
  > "We assume the distance to W49N to be 11.11$^{+0.79}_{-0.69}$ kpc (cite: Zhang2013)" (Introduction) [from (cite: Zhang2013)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Calibrator names given; calibration method not described  
  > "Flux, bandpass, pointing, and phase calibrations were carried out with J1905+0952, J1907+0907, and J1908+1201." (ALMA archival data)
- flux calibrator: J1905+0952, J1907+0907, J1908+1201 (flux, bandpass, pointing, phase)  
  > "Flux, bandpass, pointing, and phase calibrations were carried out with J1905+0952, J1907+0907, and J1908+1201." (ALMA archival data)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "by setting the width parameter of the ‘tclean’ task to be 2 kms$^{-1}$" (ALMA archival data)
- deconvolver: _not stated_
- weighting robust: briggs, robust = 0.5  
  > "We set the parameters of the ‘tclean’ task as weighting=‘briggs’ and robust=‘0.5’." (ALMA archival data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Linear baseline fit to line-free channels with uvcontsub; continuum averaged over four windows  
  > "We separated the continuum and line emissions by fitting a linear baseline to line free channels of each spectral window using the ‘uvcontsub’ task of CASA." (ALMA archival data)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Line cube regridded to 2 km/s channels  
  > "For the H29$\alpha$ line data, we set up a data cube with a spectral resolution of 2 kms$^{-1}$." (ALMA archival data)
- final beam: continuum 0.046''x0.032'' PA 70.3; H29α 0.052''x0.033''  
  > "that of the H29$\alpha$ recombination line image was 0.052$''$$\times$ 0.033$''$ (PA=$58.0\degree$)" (ALMA archival data)
- final rms: 0.7 mJy/beam continuum; 2.0 mJy/beam line  
  > "The resultant noise levels were 0.7 mJy beam$^{-1}$ and 2.0 mJy beam$^{-1}$ for the continuum and line maps, respectively." (ALMA archival data)

### Inherited from earlier work

- 45 GHz map position shift to align A1 to compensate unknown positional displacement  
  > "to compensate the unknown positional displacement described by (cite: Rodriguez2020)" (footnote 1) [from (cite: Rodriguez2020)]
- Temperature 10000 K assumed for thermal width deconvolution  
  > "at the assumed temperature of 10000 K (cite: DePree1997)" (Expanding ring of ionized gas and its implication) [from (cite: DePree1997)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for uvcontsub
- Image size and cell size
- Cleaning threshold, masks, niter
- Which execution blocks were used and how the second set was identified
- Calibration pipeline and CASA version
- Exact procedure for double-Gaussian fits to ring profiles and PV slice widths
- Rest frequency of H29α used for velocity axis
- Details of the 100–450 GHz archival flux measurements

## Analysis recipe

1. **Make continuum and H29α images**: uvcontsub, then tclean with Briggs weighting; continuum averaged across four windows; cube at 2 km/s  
  > "The continuum data at the effective frequency of 250 GHz was then made by averaging the line-free intensities of all four windows." (ALMA archival data)
   - software: CASA
   - parameter: robust = 0.5; width 2 km/s  
  > "weighting=‘briggs’ and robust=‘0.5’" (ALMA archival data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure ring geometry and fluxes**: 2D Gaussian fits for component size, flux, inclination; double Gaussian fits to profiles for ring size and width  
  > "derived from the 2D Gaussian fitting tool of CASA" (Continuum and H29α Rings)
   - software: CASA
   - assumption: Ring is intrinsically circular, tilted, symmetric about polar axis and equatorial plane  
  > "We, therefore, assume in this paper that the 250 GHz elliptical emission represents a tilted ring, which is intrinsically circular on the equatorial plane of the star." (Continuum and H29α Rings)
   - fitting: Gaussian fits; errors from fits  
  > "Table [\[Table01\]](#Table01) lists the observed parameters of W49N:A2 derived from the 2D Gaussian fitting tool of CASA." (Results and discussion, Continuum and H29α Rings)
   - validation: Compared 250 GHz, H29α and 45 GHz ring parameters  
  > "The ring’s axis lengths are consistent between the 250 GHz and H29$\alpha$ data within the errors." (Continuum and H29α Rings)
3. **Estimate ring scale height**: Elliptical cross-section model with beta^2 = a^2 cos^2 i + b^2 sin^2 i; 2σ upper limit  
  > "$\beta^2=a^2\,\cos^2 i + b^2\,\sin^2 i$" (Continuum and H29α Rings)
   - assumption: Ionized gas 10000 K around 20 Msun star for pressure scale height  
  > "pressure scale height of $\sim$1700 au of an ionized gas disk of 10000 K around a 20 M$_\odot$ star" (Continuum and H29α Rings)
   - fitting: _not stated_
   - validation: cos^-1(β/a) consistent with inclination  
  > "The values of $\cos^{-1}(\beta/a)$ are consistent with the ring inclination angle of 50 and 45, respectively, within the errors." (Continuum and H29α Rings)
4. **Derive expansion and rotation velocities**: Gaussian fits to line profiles on PV diagrams along major and minor axes; velocity difference between ridges corrected for inclination 50  
  > "The values were measured by applying Gaussian fits to the line profiles on the PV diagrams." (Velocity structure of the ring)
   - assumption: Minor-axis velocity gives radial motion only; major-axis gives rotation only  
  > "the line of sight velocity toward the minor axis reflects only the radial motion of the tilted ring, but not its rotational motion" (Velocity structure of the ring)
   - fitting: Gaussian line fits  
  > "The values were measured by applying Gaussian fits to the line profiles on the PV diagrams." (Results and discussion, Velocity structure of the ring)
   - validation: _not stated_
5. **Interpret dynamics**: Compare with free-fall and Keplerian masses for 20 Msun star; angular momentum conservation to infer origin radius ~170 au  
  > "conserving its specific angular momentum of $\sim$1800 au km s$^{-1}$" (Expanding ring of ionized gas and its implication)
   - assumption: Star mass 20±7 Msun  
  > "which should have a mass of 20$\pm$7 M$_\odot$" (Expanding ring of ionized gas and its implication)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : uvcontsub, tclean, 2D Gaussian fitting, image analysis  
  > "Image analysis was done using the CASA software (cite: CASA2022)." (ALMA archival data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 250 GHz continuum total flux density of A2 | 1.11 | 0.03 | Jy | 2 | 1.11 $\pm$0.03 (Jy) |
| Spectral index 45–250 GHz | 0.5 | not stated | dimensionless | 2 | to give a spectral index $\alpha$ = 0.5 |
| Ring inclination (250 GHz) | 50 | 2 | deg | 2 | suggests an inclination of 50$\pm$2 |
| Ring expansion velocity | 13.2 | 1.0 | km/s | 4 | expansion or contraction velocity of 13.2$\pm$1.0 km s$^{-1}$ at the radius of 706 au |
| Ring rotation velocity | 2.7 | 1.0 | km/s | 4 | rotation velocity of 2.7$\pm$1.0 km s$^{-1}$ at the radius of 642 au |
| Scale height upper limit 250 GHz / H29α | <410 / <690 | 2σ | au | 3 | The results are $b<$410 au and $b<$ 690 au for the 250 GHz and H29$\alpha$ rings, respectively. |
| Origin radius of ring gas | ~170 | not stated | au | 5 | specifically from $R \sim$ 170 au |

## Qualitative findings

- No molecular line emission within 200 mas of A2, suggesting no neutral disk  
  > "there is a hole of molecular emission toward A2, suggesting that no neutral disk is associated with the ionized ring" (Continuum and H29α Rings)

## Claim tuples

- H: Is the A2 ionized ring expanding or contracting? | E: H29α PV diagrams and channel maps along ring axes | R: Velocity difference of 13.2 km/s between NW and SE ridges, too large for gravity of a ~20 Msun star | F: Ring is expanding in the equatorial plane | **supported**
- H: Is the ring rotating at Keplerian speed? | E: Major-axis PV velocity difference | R: 2.7 km/s vs Kepler 5.2 km/s (2.5σ) | F: Sub-Keplerian rotation implies gas transported from ~170 au conserving angular momentum | **partially**
- H: Is the ring geometrically thin? | E: Compare ring widths along major and minor axes | R: Scale height b<410 au (250 GHz) | F: Ring is relatively flat | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Gravitational infall/contraction rejected: would need ~70 Msun, or Keplerian mass only 5.3–5.7 Msun  
  > "We, therefore, conclude that the ring’s observed radial motion cannot be gravitational infall or contraction." (Expanding ring of ionized gas and its implication)
- How they decided it was enough: _not stated_
- Limitation (authors): Cannot exclude small amount of midplane accretion  
  > "we cannot exclude the possibility of a small amount of accretion through the mid-plane of the disk" (Expanding ring of ionized gas and its implication)
- Caveat (inferred, ours): Results rest on strong symmetry assumptions (circular tilted ring)
- Caveat (inferred, ours): Beam comparable to ring width, so velocities are beam-smeared
- Caveat (inferred, ours): Rotation detection only 2.5σ
- Caveat (inferred, ours): Calibration and one dataset exclusion not detailed

## Reproducibility

- Data public (paper): Archival ALMA data used  
  > "We used Atacama Large Millimeter/submillimeter Array (ALMA) archival data (#2018.1.00520.S: PI D. Wilner)" (ALMA archival data)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, masks, threshold)
- Missing: CASA version
- Missing: Line-free channels
- Missing: Fit procedure details for ring widths and PV Gaussians
- Data volume (inferred): ~50-150 GB
- Score (inferred): 3/5, Public data and key tclean settings given, but many imaging and fitting details missing.
- Rediscovery candidate: yes, Public data, numeric results, and a moderately complete recipe.

## Links

- Companion: (cite: DePree2020) (45 GHz observations and ionizing source properties of A2)
- Companion: (cite: DePree2000) (first noted the ring in 45 GHz continuum)

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 6,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 45,
  "rate": 0.616
 },
 "evidence_ok": true
}
```

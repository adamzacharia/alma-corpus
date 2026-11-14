# A Hot Molecular Circumstellar Disk around the Massive Protostar Orion Source I

`2014ApJ...782L..28H` | The Astrophysical Journal Letters 2014 | first author: Hirota, Tomoya | arXiv: 1312.0315 | DOI: 10.1088/2041-8205/782/2/L28

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: Do submillimeter H2O lines, including a vibrationally excited line, trace a hot rotating circumstellar disk around the massive protostar Source I, and what are its mass and temperature?  
  > "The present results provide a further evidence of hot and neutral circumstellar disk rotating around Source I with a diameter of $\sim$100 AU scale." (abstract)
- Target **Orion KL Source I**: coordinates Tracking center (22 GHz H2O maser) RA 05h35m14.125s, Dec -05d22'36.486'', 7'' SW of Source I  
  > "Because of its proximity to the Sun at a distance of 420 pc (cite: Menten2007; Kim2008)" (Introduction); "RA(J2000)=05h35m14.125s, Decl(J2000)=-05d22$'$36.486$''$ (cite: Hirota2011), which is 7$''$  southwest of Source I." (Observations); z/distance 420 pc  
  > "Because of its proximity to the Sun at a distance of 420 pc (cite: Menten2007; Kim2008)" (Introduction); "RA(J2000)=05h35m14.125s, Decl(J2000)=-05d22$'$36.486$''$ (cite: Hirota2011), which is 7$''$  southwest of Source I." (Observations); distance from Menten2007; Kim2008  
  > "Because of its proximity to the Sun at a distance of 420 pc (cite: Menten2007; Kim2008)" (Introduction); "RA(J2000)=05h35m14.125s, Decl(J2000)=-05d22$'$36.486$''$ (cite: Hirota2011), which is 7$''$  southwest of Source I." (Observations)

## Data provenance

- ALMA projects: 2011.0.00199.S
- bands: _not stated_
- frequencies and spectral setup: 4 spectral windows, 468.750 MHz each, 122 kHz channel spacing  
  > "The ALMA correlator provided four spectral windows with a bandwidth of 468.750 MHz for each. The channel spacing of spectrometers was 122 kHz." (Observations)
- continuum bandwidth: _not stated_
- arrays: 21-28 12-m antennas  
  > "The array was consisted of 21-28 antennas with a diameter of 12 m each" (Observations)
- configurations: _not stated_
- baselines: max baseline 400 m, extended configuration  
  > "in the extended configuration with the maximum baseline length of 400 m." (Observations)
- angular resolution: 0.40''x0.34'', PA 60 deg  
  > "The resultant beam size is 0.40$''$$\times$0.34$''$  with a position angle of 60 degrees." (Data reduction)
- max recoverable scale: _not stated_
- sensitivity: ~30 mJy/beam per channel  
  > "The image rms noise level was $\sim$30 mJy beam$^{-1}$ at each channel." (Data reduction)
- time on source: about 100 seconds per session  
  > "The on-source integration time was about 100 seconds for each session." (Observations)
- observing dates: July 16, August 25, and October 21, 2012  
  > "Observations were carried out with ALMA on July 16, August 25, and October 21, 2012." (Observations)
- pi or archival as stated: _not stated_
- Line: ortho-H2O 10(2,9)-9(3,6) (321.225656 GHz)
- Line: ortho-H2O v2=1, 5(2,3)-6(1,6) (336.227931 GHz)
- External data: H2O lower state energy levels (1846 K and 2939 K)  
  > "The lower state energy levels are 1846 K and 2939 K for the 321 GHz and 336 GHz H$_{2}$O lines, respectively (cite: Chen2000)." (Observations) [from (cite: Chen2000)]
- External data: Tracking position of bursting 22 GHz H2O maser  
  > "the tracking center position was taken to be the bursting 22 GHz H$_{2}$O maser" (Observations) [from (cite: Hirota2011)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto (primary); bandpass J053851-440507/J0423-013; gain J0607-085  
  > "A primary flux calibrator, band-pass calibrator, and secondary gain calibrator were Callisto, J053851-440507/J0423-013, and J0607-085, respectively." (Observations)
- flux scale uncertainty: ~20%  
  > "we estimated an accuracy of flux measurements to be $\sim$20%." (Data reduction)
- self calibration: Phase and amplitude self-cal on Orion KL continuum from line-free channels, applied to all channels  
  > "First, both phase and amplitude self-calibrations were done with the continuum emission of Orion KL by integrating over line-free channels." (Data reduction)

### Imaging

- task: CASA synthesis imaging, velocity resolution 0.125 km/s  
  > "We set a velocity resolution of 0.125 km s$^{-1}$ (corresponds to 130-140 kHz resolution) in the synthesized imaging of the H$_{2}$O lines." (Data reduction)
- deconvolver: _not stated_
- weighting robust: uniform weighting, uv distance > 200 kλ  
  > "by using the uniform-weighted visibility data with a UV distance longer than 200 k$\lambda$." (Data reduction)
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

### Not stated but needed to reproduce (our reading)

- CASA version and calibration pipeline/manual details
- Line-free channel ranges
- Self-calibration solution intervals
- Image size and cell size, cleaning parameters
- Ring model code and radiative transfer details
- Fitting procedure and goodness criterion for the model

## Analysis recipe

1. **Self-calibrate and image lines**: Self-calibration on continuum, applied to lines; uniform-weighted imaging with uv > 200 kλ  
  > "The solutions of self-calibration were applied to all the spectral channels including the target H$_{2}$O lines." (Data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared continuum and methyl formate lines across sessions to check flux stability  
  > "We compared the continuum emission and selected spectral lines of methyl formate, HCOOCH$_{3}$ to check the stability of the observed flux scale." (Data reduction)
2. **Velocity centroid maps**: 2D Gaussian fitting to velocity channel maps to find peak positions  
  > "we made velocity centroid maps (peak positions of velocity channel maps) of both lines by performing two dimensional Gaussian fitting to the synthesized images." (Results)
   - fitting: 2D Gaussian; formal errors 0.005-0.02'' (1σ)  
  > "Formal errors in the Gaussian fitting, 0.005-0.02$''$ (1$\sigma$), are almost consistent with this expectation." (Results)
   - validation: Compared with SiO maser maps and VLBI  
  > "The resemblance of 321 GHz H$_{2}$O emission and previous vibrationally-excited SiO maser observations ensures that the distribution of the H$_{2}$O emission traced by ALMA is reliable" (Results)
3. **Enclosed mass from velocity gradient**: Linear velocity gradient of edge-on rotating ring  
  > "If we simply assume a linear velocity gradient of the rotating edge-on ring with a radius of 42 AU, the enclosed mass is estimated to be 5$M_{\odot}$." (Results)
   - assumption: Distance 420 pc; edge-on ring  
  > "Because of its proximity to the Sun at a distance of 420 pc (cite: Menten2007; Kim2008), Orion KL (Kleinman-Low object) has been recognized as one of the best laboratories" (Introduction)
   - fitting: _not stated_
   - validation: _not stated_
4. **Edge-on ring model of PV diagram and spectrum**: Grid of ring inner/outer radii (rin 5-55 AU, rout 40-60 AU), Mrot 7 and 10 Msun, uniform temperature/density; compare to PV diagram and spectral profile  
  > "we calculated models for several parameter set of inner and outer radii of the ring, $r_{\mbox{in}}$=5, 15, 25, 35, 45, 55 AU and $r_{\mbox{out}}$=40, 50, and 60 AU" (Discussion)
   - parameter: Best model rin=45 AU, rout=50 AU, Mrot=7 Msun  
  > "the model with $r_{\mbox{in}}$=45 AU and $r_{\mbox{out}}$=50 AU is found to well reproduce the observed PV diagram and spectral profile" (Discussion)
   - assumption: Uniform H2O density 5e5 cm-3  
  > "a uniform H$_{2}$O density of 5$\times$10$^{5}$ cm$^{-3}$" (Discussion)
   - fitting: Visual comparison of model spectrum to observed profile; Tex > 3000 K  
  > "we estimate the excitation temperature of the 336 GHz H$_{2}$O line, $T_{\mbox{ex}}$, by fitting the observed line profile" (Discussion)
   - validation: Proof-of-concept; parameters degenerate  
  > "what we have done is a proof-of-concept model calculation" (Discussion)

## Software

- **CASA** : Synthesis imaging and self-calibration  
  > "Synthesis imaging and self-calibration were done with the CASA software package." (Data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Enclosed mass (ring radius 42 AU) | 5 | not stated | Msun | 3 | the enclosed mass is estimated to be 5$M_{\odot}$ |
| Enclosed mass (radius 47 AU) | 7 | not stated | Msun | 3 | a slightly larger radius of 47 AU yields a consistent value of 7$M_{\odot}$ |
| Excitation temperature of 336 GHz line | >3000 | not stated | K | 4 | can be reconciled with an excitation temperature of $>$3000 K |
| Continuum peak intensity | 698 | rms 9 | mJy/beam | 1 | Peak intensity and rms noise level of the continuum emission are 698 mJy beam$^{-1}$ and 9 mJy beam$^{-1}$, respectively. |
| 336 GHz emission size | 0.2''x0.1'' (84x42 AU) | not stated | arcsec | 2 | $\sim$0.2$''$$\times$0.1$''$ (84AU$\times$42AU) |

## Qualitative findings

- First detection of the vibrationally excited 336 GHz H2O line in a star-forming region; 321 GHz map follows the outflow base like SiO masers, 336 GHz traces the disk midplane  
  > "Thus, this is the first detection of the 336 GHz H$_{2}$O line in star-forming regions." (Results)

## Claim tuples

- H: The 336 GHz H2O line traces a hot rotating disk around Source I | E: Centroid maps, PV diagram and ring model of the 336 GHz line | R: Velocity gradient perpendicular to outflow; ring model with M>7 Msun, Tex>3000 K fits | F: Hot neutral circumstellar disk of ~100 AU rotates around Source I | **supported**
- H: The 321 GHz line traces the same structure as vibrationally excited SiO masers | E: Compare centroid map with SiO maser maps | R: Inverted Z-shaped structure similar to SiO | F: Both trace the outflow base from the disk surface | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: NW-SE outflow rejected: would need ~20 km/s expansion giving proper motion inconsistent with stable 43 GHz continuum  
  > "which is inconsistent with a stable structure of the 43 GHz continuum emission (cite: Goddi2011)." (Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Parameters degenerate and uncertain with single transition at limited resolution  
  > "it is hard to solve a degeneracy of disk parameters, such as mass, size, and temperature" (Discussion)
- Caveat (inferred, ours): Mass and Tex rely on a simple uniform ring with no formal fit or uncertainties
- Caveat (inferred, ours): Possible maser excitation of 336 GHz line not excluded
- Caveat (inferred, ours): Short integration with differing configurations

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Ring model code
- Missing: CASA version and imaging parameters
- Missing: Calibration details
- Data volume (inferred): ~10-50 GB for three short sessions
- Score (inferred): 3/5, ALMA data are public and the imaging recipe is brief, but the model code and many parameters are missing.
- Rediscovery candidate: no, The model is not fully specified and has no formal fit.

## Links

- Companion: Hirota et al. 2012 (cite: Hirota2012) (Detection of 232 GHz vibrationally excited H2O line with ALMA)

## Checks

```json
{
 "quotes": 48,
 "quotes_ok": 48,
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
  "facts": 64,
  "stated": 34,
  "rate": 0.531
 },
 "evidence_ok": true
}
```

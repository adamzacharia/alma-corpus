# ALMA observations of the <ASTROBJ>Th 28</ASTROBJ> protostellar disk. A new example of counter-rotation between disk and optical jet

`2016A&A...596A..88L` | Astronomy and Astrophysics 2016 | first author: Louvet, F. | arXiv: 1607.08645 | DOI: 10.1051/0004-6361/201628474

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Does the Th 28 disk rotate in the same sense as its optical jet, to test the interpretation of HST transverse Doppler shifts as jet rotation?  
  > "To support this interpretation, it is necessary that the underlying disks rotate in the same sense." (abstract)
- Target **Th 28**: coordinates RA(J2000)=16h08m29.72s, Dec=-39d03m11.01s (HST position, phase center)  
  > "$\alpha$($J$2000) = 16$^{h}$08$^{m}$29$\overset{s}{.}$72 and $\delta$($J$2000) = -39$^{\circ}$03$^{\prime}$11$\overset{\prime\prime}{.}$01." (2 Observations and data reduction); "We adopt the recent value of d=185$^{\rm +11}_{\rm -10}$ pc derived by (cite: Galli13) for the Lupus 3 cloud" (Introduction); z/distance 185 (+11/-10) pc  
  > "$\alpha$($J$2000) = 16$^{h}$08$^{m}$29$\overset{s}{.}$72 and $\delta$($J$2000) = -39$^{\circ}$03$^{\prime}$11$\overset{\prime\prime}{.}$01." (2 Observations and data reduction); "We adopt the recent value of d=185$^{\rm +11}_{\rm -10}$ pc derived by (cite: Galli13) for the Lupus 3 cloud" (Introduction); distance from Galli et al. 2013, Lupus 3 cloud  
  > "$\alpha$($J$2000) = 16$^{h}$08$^{m}$29$\overset{s}{.}$72 and $\delta$($J$2000) = -39$^{\circ}$03$^{\prime}$11$\overset{\prime\prime}{.}$01." (2 Observations and data reduction); "We adopt the recent value of d=185$^{\rm +11}_{\rm -10}$ pc derived by (cite: Galli13) for the Lupus 3 cloud" (Introduction)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 7 (275-373 GHz)  
  > "were observed using ALMA Band 7 (275-373 GHz)." (2 Observations and data reduction)
- frequencies and spectral setup: Two 468.75 MHz spws (3840 channels) at 345.818 and 330.609 GHz; 2 GHz continuum spw, 128 channels, centered 332.014 GHz  
  > "A third spectral window of 2 GHz bandwidth in 128 channels centered at 332.014 GHz was dedicated to the detection of the continuum emission from the dust disk." (2 Observations and data reduction)
- continuum bandwidth: 2 GHz  
  > "| Bandwidth | 469 MHz | 469 MHz | 2 GHz |" (Table 1)
- arrays: _not stated_
- configurations: Cycle 1 semi-extended configuration  
  > "The data were taken using the cycle 1 semiextended configuration of ALMA with baselines ranging from 20 m to 480 m." (2 Observations and data reduction)
- baselines: 20 m to 480 m  
  > "with baselines ranging from 20 m to 480 m." (2 Observations and data reduction)
- angular resolution: 0.46" x 0.37" (12CO)  
  > "The sub-arcsecond angular resolution (0.46$''$$\times$0.37$''$)" (abstract)
- max recoverable scale: _not stated_
- sensitivity: 4 mJy/beam per 0.4 km/s channel in CO; continuum rms 0.08 mJy/beam  
  > "The continuum displays a RMS noise of 0.08 mJy/beam over its 2 GHz bandwidth." (2 Observations and data reduction)
- time on source: two tracks of ~40 minutes each  
  > "in two tracks of $\sim$ 40 minutes each during the ALMA cycle 1 campaign." (2 Observations and data reduction)
- observing dates: April 28 2014  
  > "The observations were performed on April 28$^{}$ 2014" (2 Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (345.796 GHz)
- Line: 13CO J=3-2 (330.588 GHz)
- Other facility **HST/STIS**: Optical jet transverse Doppler shifts and HST position of source  
  > "detection with the STIS instrument mounted on the HST of transverse Doppler shifts" (Introduction)
- External data: Jet proper motions of knots E1 (0.47"/yr) and W (0.37"/yr)  
  > "They found a proper motion of 0.47$\ensuremath{''}$yr$^{-1}$ for the E1 knot, and 0.37$\ensuremath{''}$yr$^{-1}$ for the W knot." (Appendix: Jet inclination) [from Wang & Henning 2009 (cite: wang09)]
- External data: Knot radial velocities -62 and +38 km/s  
  > "Line-of-sight velocities ($V_{\rm rad}$) of -62 km.s$^{-1}$ and +38 km.s$^{-1}$ were reported for the E1 and W knots, respectively" (Appendix: Jet inclination) [from Comeron & Fernandez 2010 (cite: comeron10)]
- External data: Stellar luminosity 0.03 Lsun  
  > "0.03 L$_{\odot}$ (cite: mortier11)" (Introduction) [from Mortier et al. 2011 (cite: mortier11)]
- Simulation/model as data: Pre-main-sequence tracks of Siess et al. 2000 used for mass/luminosity comparison  
  > "Using the pre-main-sequence tracks of (cite: siess00)" (5.2 Implications for the nature of Th 28)

## Processing

### Calibration

- pipeline or manual: CASA calibration with WVR, Tsys, bandpass, flux and gain calibration; extra phase calibration using continuum spw of one track  
  > "we used the continuum spectral window of one track to further phase calibrate all spectral windows." (2 Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~10%  
  > "we estimate the absolute flux calibration to be accurate within $\sim$10%." (2 Observations and data reduction)
- self calibration: Phase transfer from the continuum spw of one track to all spws  
  > "Owing to residual inconsistency in the phase calibration between the two tracks" (2 Observations and data reduction)

### Imaging

- task: CLEAN in CASA  
  > "Imaging was carried out using the CLEAN algorithm of CASA." (2 Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "We used the Briggs weighting with a robust parameter of 0.5" (2 Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Spectral resolution degraded from ~0.11 to 0.4 km/s  
  > "that we degraded down to 0.4 km.s$^{-1}$ to detect weak $^{12}$CO and $^{13}$CO emission." (2 Observations and data reduction)
- final beam: 12CO 0.46x0.37" PA 87.5; 13CO 0.49x0.39"; continuum 0.50x0.39"  
  > "| Synthesized beam | $0.46\ensuremath{''}\times0.37\ensuremath{''}$ | $0.49\ensuremath{''}\times0.39\ensuremath{''}$ | $0.50\ensuremath{''}\times0.39\ensuremath{''}$ |" (Table 1)
- final rms: 4 mJy/beam per 0.4 km/s channel (CO); 0.08 mJy/beam continuum  
  > "The resulting root mean square (RMS) noise level is of 4 mJy/beam per 0.4 km.s$^{-1}$ channel in $^{12}$CO(3-2) and $^{13}$CO(3-2)." (2 Observations and data reduction)

### Inherited from earlier work

- Temperature profile analysis of optically thick 12CO wings follows Beckwith & Sargent 1993  
  > "Following the analysis developed by BS93, if the temperature profile follows a power law in radius ($r$), as $T\propto r^{-q}$" (4.5 Temperature profile) [from Beckwith & Sargent 1993 (cite: beckwith93)]
- Dust opacity law  
  > "a dust opacity coefficient $k_{\nu} = 0.1 {\rm cm^2.g^{-1}}\times(\nu/1000\rm GHz)^\beta$ (cite: hildebrand83) with $\beta \sim$ 0.5 (cite: beckwith91)" (3.2 Continuum emission) [from Hildebrand 1983; Beckwith & Sargent 1991]

### Not stated but needed to reproduce (our reading)

- Calibrator names (quasars) and flux values are missing from the text
- Clean threshold, mask, niter and image size/cell size
- CASA version
- Which track was used for phase transfer
- Exact velocity channels/regions for the Gaussian wing fits for Vlsr
- Details of the geometrical disk model (grid, beam convolution, fitting procedure, fixed parameters)
- Continuum subtraction method and line-free channels

## Analysis recipe

1. **Calibrate and image**: CASA calibration, CLEAN imaging with Briggs weighting, 0.4 km/s channels  
  > "We used the Briggs weighting with a robust parameter of 0.5" (2 Observations and data reduction)
   - software: CASA
   - parameter: robust = 0.5; 0.4 km/s channels  
  > "We used the Briggs weighting with a robust parameter of 0.5" (2 Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit disk size, PA and inclination in uv plane**: 2D elliptical Gaussian fits in the uv plane; inclination from aspect ratio  
  > "we performed 2D-Gaussian fits directly in the uv plane with the UV-FIT procedure of GILDAS" (3.1 (b))
   - software: GILDAS
   - assumption: Flat disk inclination from axis ratio; CO may underestimate true inclination because emission arises above the disk plane  
  > "However, the CO emission may be underestimating the true disk inclination." (4.2 Disk inclination)
   - fitting: _not stated_
   - validation: Compared with jet inclination 82.3 deg from knot proper motions  
  > "This inclination is comparable but somewhat lower than the inclination of 82.3$\pm$2$^{\circ}$ for the optical jet" (4.2 Disk inclination)
3. **Determine Vlsr and rotation sense**: Single Gaussian fit to high-velocity wings of integrated spectra; first moment maps  
  > "we fitted a single Gaussian component to the high-velocity wings of the $^{12}$CO and $^{13}$CO profiles" (4.1 Vlsr of the source)
   - fitting: _not stated_
   - validation: Compared with Lupus 3 Vlsr range  
  > "This value is compatible with the range of $V_{\rm lsr}$ observed toward the Lupus 3 cloud" (4.1 Vlsr of the source)
4. **Derive temperature power-law index**: Fit flux density of 12CO blue wing, F ~ v^(3q-5), velocity range -8.0 to -2.4 km/s  
  > "Performing the fit of the flux density on the high-velocity blue wing \[-8.0 km.s$^{-1}$; -2.4 km.s$^{-1}$\] of the $^{12}$CO emission line, we find an index q=0.8$\pm$0.2." (4.5 Temperature profile)
   - assumption: 12CO optically thick; T ∝ r^-q  
  > "Since the $^{12}$CO emission line is optically thick (see above), its spectrum is a direct probe of the temperature as a function of radius." (4.5 Temperature profile)
   - fitting: _not stated_
   - validation: _not stated_
5. **Estimate dust mass**: Optically thin dust emission from 13.3 mJy  
  > "our total flux density of 13.3 mJy implies a total mass of $\sim$8.5$\times10^{-4}$ M$_{\odot}$" (3.2 Continuum emission)
   - assumption: T=20 K, kappa=0.1 cm2/g (nu/1000GHz)^beta, beta~0.5, d=185 pc  
  > "If we assume optically thin emission from dust grains at $T$=20 K" (3.2 Continuum emission)
   - fitting: _not stated_
   - validation: Sensitivity to T and beta varied by 20%  
  > "For instance a variation of $-$20% (resp. +20%) of the dust temperature implies an augmentation" (3.2 Continuum emission)
6. **Estimate stellar mass**: Geometric model of optically thick flat disk with power-law temperature, convolved with the ALMA beam, fitted to 12CO brightness profile and peak velocity separation  
  > "we build a simple geometrical model of an optically thick flat disk with a radial power law temperature distribution of index $q$ and we convolve this model with the effective ALMA beam" (5.2 Implications for the nature of Th 28)
   - parameter: i=80 deg, q=0.8, Rout=0.5" (92.5 AU)  
  > "We fix the disk inclination to i=80$^{\circ}$ and the power law index $q$ of the temperature profile to q=0.8" (5.2 Implications for the nature of Th 28)
   - fitting: _not stated_
   - validation: Compared with K2 spectral type and Siess et al. 2000 tracks  
  > "a central stellar mass in the range 1-2 M$_{\odot}$ appears more compatible with a spectral type of early K" (5.2 Implications for the nature of Th 28)

## Software

- **CASA** : Calibration and CLEAN imaging  
  > "The data were reduced using the common astronomy software application (cite: mcmullin06)." (2 Observations and data reduction)
- **GILDAS (UV-FIT)** : 2D Gaussian fits in uv plane  
  > "we performed 2D-Gaussian fits directly in the uv plane with the UV-FIT procedure of GILDAS" (3.1 (b))

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 12CO integrated flux | 5.1 | not stated | Jy km/s | 1 | with an integrated flux of 5.1 Jy.km.s$^{-1}$ in $^{12}$CO and 0.60 Jy.km.s$^{-1}$ in $^{13}$CO |
| 13CO integrated flux | 0.60 | not stated | Jy km/s | 1 | with an integrated flux of 5.1 Jy.km.s$^{-1}$ in $^{12}$CO and 0.60 Jy.km.s$^{-1}$ in $^{13}$CO |
| Continuum flux density | 13.3 | not stated | mJy | 1 | our total flux density of 13.3 mJy |
| 12CO disk PA | 7.3 | 0.4 | deg | 2 | at a PA=7.3$\pm0.4^\circ$ in $^{12}$CO |
| Disk inclination from 12CO | 73 | 1 | deg | 2 | 73$\pm$1$^{\circ}$ and 73$\pm$9$^{\circ}$ from the $^{12}$CO and $^{13}$CO emission lines |
| Vlsr | 3 | 0.1 | km/s | 3 | we adopt a $V_{\rm lsr}$=3$\pm0.1$ km.s$^{-1}$ |
| Temperature index q | 0.8 | 0.2 | dimensionless | 4 | we find an index q=0.8$\pm$0.2 |
| Dust disk mass | 8.5e-4 | not stated | Msun | 5 | implies a total mass of $\sim$8.5$\times10^{-4}$ M$_{\odot}$ |
| Central stellar mass | 1.6 | 0.2 | Msun | 6 | The observed velocity separation between the peaks is then best fitted with a stellar mass of 1.6 M$_{\odot}$. |
| Disk outer radius | 92.5 | not stated | AU | 6 | a disk outer radius of R$_{\rm out}$=0.5$^{\prime\prime}$ is required, corresponding to 92.5 AU |
| Flux ratio 13CO/12CO | 0.16 | not stated | dimensionless | 0 | The integrated flux ratio, S($^{13}$CO)/S($^{12}$CO), is therefore of $\sim$0.16. |

## Qualitative findings

- Disk rotates opposite to the optical jet rotation sense inferred from HST  
  > "The derived sense of rotation is opposite that derived for the optical jet with the HST" (4.3 Disk rotation sense)

## Claim tuples

- H: Th 28 has a Keplerian disk | E: ALMA Band 7 12CO, 13CO and continuum imaging, uv fits, PV diagram | R: Compact elongated CO perpendicular to jet, double-peaked profile, PV symmetric | F: A Keplerian disk is detected | **supported**
- H: Disk and optical jet rotate in the same sense | E: Moment-1 maps of CO compared with HST jet rotation | R: NE redshifted, SW blueshifted, opposite to jet | F: Counter-rotation; optical velocity gradients cannot be used to infer launching radii | **supported**
- H: Central mass is higher than 0.6-0.9 Msun from Halpha | E: Disk geometrical model fit to 12CO peak separation and extent | R: 1.6±0.2 Msun | F: Stellar mass 1-2 Msun | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Inner-disk rotation reversal or warp considered unlikely given matching inclination and PA  
  > "Although we cannot fully exclude these possibilities, they seem unlikely" (5.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Detailed radiative transfer disk modelling and SED fitting beyond scope; mass estimates are simple  
  > "Such a detailed analysis goes beyond the scope of the present paper." (5.2 Implications for the nature of Th 28)
- Limitation (authors): Dust mass highly sensitive to assumptions  
  > "this value is highly sensible to the assumptions made on the parameters listed above." (3.2 Continuum emission)
- Caveat (inferred, ours): Stellar mass from simple model with fixed inclination 80 deg inconsistent with 73 deg from fits
- Caveat (inferred, ours): Text gives both 13CO(2-1) and (3-2) for the same line
- Caveat (inferred, ours): Integrated 12CO flux inconsistent between sections (5.1 vs 3.75 Jy km/s)
- Caveat (inferred, ours): Disk mass is a dust mass with assumed T and opacity

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Project code not printed in paper
- Missing: Calibrator names and CASA version
- Missing: Disk model code and fitting details
- Data volume (inferred): ~20-50 GB raw (two 40-min Band 7 tracks)
- Score (inferred): 3/5, Data are likely public in the archive and the main steps are simple, but the imaging details, calibrators and model implementation are not given.
- Rediscovery candidate: no, The paper does not state the project code or public status, and the model details are incomplete, although the results are numeric.

## Links

- Method: Beckwith & Sargent 1993 (cite: beckwith93) (Temperature profile from optically thick line wings)
- Companion: Coffey et al. 2004 (cite: coffey04) (HST optical jet rotation measurement for Th 28)

## Checks

```json
{
 "quotes": 69,
 "quotes_ok": 69,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2012.1.00857.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 49,
  "rate": 0.62
 },
 "evidence_ok": true
}
```

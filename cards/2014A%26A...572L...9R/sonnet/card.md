# ALMA sub-mm maser and dust distribution of VY Canis Majoris

`2014A&A...572L...9R` | Astronomy and Astrophysics 2014 | first author: Richards, A. M. S. | arXiv: 1409.5497 | DOI: 10.1051/0004-6361/201425024

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: evolved_stars, astrochemistry
- Question: Where do the 658, 321 and 325 GHz water masers lie relative to the star VY CMa and its dust continuum, and do they match excitation model predictions?  
  > "We present ALMA observations that test these predictions and, for the first time, resolve sub-mm masers, thermal lines, and continuum." (Introduction)
- Target **VY CMa**: coordinates RA 07 22 58.3226, Dec -25 46 03.043 (J2000) (continuum peak VY)  
  > "at 1.2$\pm$0.1 kpc, (cite: Choi08); (cite: Zhang12))" (Introduction); "The 321 GHz position of **VY** is R.A. 07 22 58.3226 Dec. –25 46 03.043 (J2000)" (VY CMa continuum and maser morphology); z/distance 1.2±0.1 kpc  
  > "at 1.2$\pm$0.1 kpc, (cite: Choi08); (cite: Zhang12))" (Introduction); "The 321 GHz position of **VY** is R.A. 07 22 58.3226 Dec. –25 46 03.043 (J2000)" (VY CMa continuum and maser morphology); distance from Choi08; Zhang12  
  > "at 1.2$\pm$0.1 kpc, (cite: Choi08); (cite: Zhang12))" (Introduction); "The 321 GHz position of **VY** is R.A. 07 22 58.3226 Dec. –25 46 03.043 (J2000)" (VY CMa continuum and maser morphology)

## Data provenance

- ALMA projects: 2011.0.00011.SV
- bands: _not stated_
- frequencies and spectral setup: Spws 0.94–1.87 GHz wide, 3840 channels each; velocity resolution 0.45 km/s (321, 658 GHz), 0.9 km/s (325 GHz)  
  > "Each spw was divided into 3840 channels, but as a result of Hanning smoothing in the correlator, the finest effective velocity resolution is approximately double the channel spacing" (Observations and data processing)
- continuum bandwidth: 1.74 GHz (321), 2.25 GHz (325), 0.4 GHz (658) line-free  
  > "| 325 $\!\!\!$ | 325.10740$\!\!\!$ | 1.873$\!\!\!\!\!\!$ | 2.25 $\!\!\!\!\!\!$ | 1.1 $\!\!\!\!\!\!$ |" (Table 2)
- arrays: 16–20 12 m antennas  
  > "VY CMa was observed by ALMA on 2013 16–19 August using 16–20 12 m antennas." (Observations and data processing)
- configurations: _not stated_
- baselines: 0.014–2.7 km  
  > "on baselines from 0.014–2.7 km" (Data acquisition and reduction)
- angular resolution: continuum beams 0.22"x0.13" (321/325 GHz), 0.11"x0.06" (658 GHz); maser beams 0.18"x0.09" and 0.088"x0.044"  
  > "After subtracting the continuum, the masers were imaged using beam sizes of (0.18$''$$\times$0.09$''$) and (0.088$''$$\times$0.044$''$) at 321/325 and 658 GHz." (Data acquisition and reduction)
- max recoverable scale: <6" at 658 GHz, <13" at 321–325 GHz  
  > "suggesting that we recover all the flux on scales $<6$” or $<13$” at the higher or lower frequencies." (Observations and data processing)
- sensitivity: _not stated_
- time on source: ~1.5 hr per frequency  
  > "giving a total time on VY CMa at each frequency of $\sim$1.5 hr in addition to calibration observations." (Observations and data processing)
- observing dates: 2013 16–19 August  
  > "observed on 2013 16–19 August" (Data acquisition and reduction)
- pi or archival as stated: Public ALMA Science Verification data  
  > "We obtained public ALMA Science Verification data for VY CMa" (Data acquisition and reduction)
- Line: H2O 10(2,9)–9(3,6) (321.22564 GHz)
- Line: H2O 5(1,5)–4(2,2) (325.15292 GHz)
- Line: H2O v2=1 1(1,0)–1(0,1) (658.00655 GHz)
- External data: Dust and wind density/velocity profiles for VY CMa used in maser excitation model  
  > "based upon the density and velocity profiles obtained for VY CMa by Decin et al. (2006)" (Maser modelling) [from Decin et al. 2006]
- External data: Collisional rate coefficients for H2O-H2  
  > "We adopted the latest quantal rate coefficients (Daniel et al. 2011)" (Maser modelling) [from Daniel et al. 2011; Neufeld 2010]
- External data: Literature continuum flux densities for comparison  
  > "We compared the total continuum flux densities with literature values (Fu et al 2012; Kamiński et al. 2013; Muller et al. 2007; Shinnaga et a. 2004)." (Observations and data processing) [from Fu et al 2012; Kamiński et al. 2013; Muller et al. 2007; Shinnaga et al. 2004]

## Processing

### Calibration

- pipeline or manual: Normal ALMA calibration with CASA; SV scripts available  
  > "Normal ALMA calibration and imaging procedures were followed, using casa (http://casa.nrao.edu)." (Observations and data processing)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Pallas (Butler-JPL-Horizons 2012)  
  > "Pallas was used as the primary flux scale calibrator (Butler-JPL-Horizons 2012, ALMA Memo 594)" (Observations and data processing)
- flux scale uncertainty: up to 15% at 658 GHz  
  > "but it suggests that the error could be up to 15%." (Observations and data processing)
- self calibration: Brightest maser channel imaged as starting model; solutions applied to all channels  
  > "In each SB, the brightest maser channel was identified and imaged, providing a starting model for self-calibration." (Observations and data processing)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Continuum natural; masers Briggs robust=0.5  
  > "partial uniform weighting (Briggs weighting with robust=0.5 as defined by casa) was used to image the masers" (Observations and data processing)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum subtracted from each data set using line-free channels  
  > "The continuum was subtracted from each data set" (Observations and data processing)
- line free channels: _not stated_
- primary beam correction: None applied  
  > "All image extents were $\le$80% of the primary beam, so no primary beam correction was applied." (Observations and data processing)
- array combination: _not stated_
- smoothing: No spectral averaging; Hanning smoothing in correlator  
  > "No spectral averaging was applied" (Observations and data processing)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Centre of expansion estimation by maximising maser separation near V*  
  > "We estimated the centre of expansion of each line as in (cite: Richards12), by maximising the separation between masers at close to $V_{\star}$" (VY CMa continuum and maser morphology) [from Richards12]
- Grouping maser components into features  
  > "We grouped the maser components into features comprising series of components in successive channels within the position errors, as in Richards et al. (2012)" (Observations and data processing) [from Richards et al. (2012)]
- Continuum analysis in companion paper  
  > "The continuum emission is analysed further by (cite: OGorman14)." (VY CMa continuum and maser morphology) [from OGorman14]

### Not stated but needed to reproduce (our reading)

- Image size and cell size
- Clean threshold, mask and iteration details
- Exact self-calibration solution intervals and iterations
- Which channels were line-free
- CASA version
- Exact component lists/flagging

## Analysis recipe

1. **calibrate and self-calibrate**: Standard ALMA calibration with Pallas flux scale, J0522-3627 bandpass, J0648-3044 phase reference; self-cal on brightest maser channel  
  > "The bright QSO J0522-3627 was used for bandpass calibration." (Observations and data processing)
   - software: CASA
   - fitting: _not stated_
   - validation: Channel-to-channel position scatter and flux spectral index ~2 checked  
  > "the flux density was consistent with the expected spectral index $\sim$2" (Observations and data processing)
2. **image continuum and masers**: Natural-weighted continuum; continuum-subtracted maser cubes with robust=0.5  
  > "The continuum channels were imaged using natural weighting" (Observations and data processing)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **measure maser and continuum positions**: 2D Gaussian fits per channel; components >3σ (321, 325) or >4σ (658), at least three successive channels  
  > "We rejected components that did not form series of at least three in successive channels, within the maximum position uncertainty." (Observations and data processing)
   - software: AIPS sad
   - fitting: Gaussian fit; position error = beam/SNR  
  > "The relative position uncertainties are given by (beam size)/S/N" (Observations and data processing)
   - validation: Sidelobe components rejected; cross-match compared with 50 mas shifted data  
  > "applying a 50 mas shift to one data set produces a similar number of pairs, so this seems like random coincidence." (Observations and data processing)
4. **excitation modelling of maser conditions**: Collisional excitation, radiative decay, escape-probability trapping with steep velocity gradient; negative optical depth contours vs T and n(H2)  
  > "We treated the effects of radiative trapping with the use of an escape probability method and the assumption of a steep velocity gradient in a single direction" (Maser modelling)
   - parameter: N(H2O)/(dv/dz) = 10^17 cm^-2 per km/s  
  > "of 10$^{17}$ cm$^{-2}$ per km s$^{-1}$" (Maser modelling)
   - assumption: Unsaturated limit  
  > "These optical depths were computed in the unsaturated limit" (Maser modelling)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration and imaging  
  > "Normal ALMA calibration and imaging procedures were followed, using casa (http://casa.nrao.edu)." (Observations and data processing)
- **AIPS (sad)** : Gaussian fitting of maser and continuum components  
  > "We measured the positions of the masers and continuum peaks by fitting Gaussian components using the aips task sad" (Data acquisition and reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| VY–C separation | 328 | ±1 | mas | 3 | **VY** is 328$\pm$1 mas from **C** at PA –33$^{\circ}$. |
| Peak continuum flux of VY at 321 GHz | 71.7 | σrms 0.9 | mJy/beam | 2 | **C** and **VY** had peak flux densities of 133.9 and 71.7 ($\sigma_{\mathrm{rms}}$ 0.9) mJy beam$^{-1}$ at 321 GHz |
| Maser peak brightness 321 GHz | 426.6 | not stated | Jy/beam | 2 | 321 GHz: 426.6 Jy beam$^{-1}$, S/N 2010 |
| J0648-3044 flux at 316.093 GHz | 0.433 | ±0.008 | Jy | 1 | was $0.433\pm0.008$ Jy at reference frequency 316.093 GHz, spectral index $\alpha$ $-0.80\pm0.03$ |
| Maser outer rims (658, 321, 325 GHz) | ~200, 500, 600 | not stated | mas | 3 | whilst the outer rims are at $\sim$ 200, 500, and 600 mas |

## Qualitative findings

- VY coincides with maser centre of expansion and is the stellar position  
  > "**VY** coincides with the maser centre of expansion and is almost certainly the location of the star." (Discussion)

## Claim tuples

- H: Sub-mm H2O masers lie at increasing distances from the star in order 658, 321, 325 GHz | E: Gaussian fitting of maser components in ALMA SV cubes | R: Inner rims at successively larger distances; outer rims ~200, 500, 600 mas | F: Maser shells are distinct but overlapping, as predicted but reaching unexpectedly large radii | **supported**
- H: The star is at the centre of expansion | E: Compare maser expansion centre with continuum peaks | R: Centre lies at compact peak VY, NW of brightest continuum C | F: VY is the stellar position | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Experimental SV observations with phase ambiguities and atmospheric phase errors; single epoch  
  > "some observational methods were experimental, for example the duration of phase-referencing cycles turned out to allow a few phase ambiguities at the highest frequencies." (Observations and data processing)
- Caveat (inferred, ours): Absolute astrometry uncertain (35 mas) so VY identification relies on phase transfer
- Caveat (inferred, ours): Brightness temperatures are lower limits
- Caveat (inferred, ours): Excitation model is simple and 658 GHz not shown

## Reproducibility

- Data public (paper): Public SV data and scripts  
  > "The data and scripts (including a description of the procedures) used for calibration and initial imaging are available from http://almascience.eso.org/alma-data/science-verification." (Observations and data processing)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, clean)
- Missing: Self-cal details
- Missing: Component tables
- Data volume (inferred): Tens of GB (three SBs, 3840-channel spws)
- Score (inferred): 5/5, Public data and stated key choices, but several imaging and selfcal details missing.
- Rediscovery candidate: yes, Public SV data, numeric positions and separations can be checked, though recipe is partly incomplete.

## Links

- Method: Richards et al. 2012 (cite: Richards12) (Maser feature grouping and centre of expansion method)
- Companion: O'Gorman et al. 2014 (cite: OGorman14) (Continuum analysis of the same data)
- Related: ALMA Science Verification

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
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
  "facts": 67,
  "stated": 41,
  "rate": 0.612
 },
 "evidence_ok": true
}
```

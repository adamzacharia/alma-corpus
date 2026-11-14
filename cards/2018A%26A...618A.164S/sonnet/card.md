# Through the magnifying glass: ALMA acute viewing of the intricate nebular architecture of OH 231.8+4.2

`2018A&A...618A.164S` | Astronomy and Astrophysics 2018 | first author: Sánchez Contreras, C. | arXiv: 1809.00619 | DOI: 10.1051/0004-6361/201833632

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, astrochemistry
- Question: What is the small- to large-scale nebular structure, kinematics and chemistry of the bipolar pre-PN candidate OH 231.8+4.2, and the location and history of its central binary system?  
  > "These data have revealed a collection of substructures previously unknown, which are the focus of this publication." (Introduction)
- Target **OH 231.8+4.2 (QX Pup)**: coordinates RA(ICRS)=07h42m16.894s, Dec=-14d42m49.836s (nominal pointing)  
  > "Here we have adopted $d$=1500 pc and $i$=35$^\circ$, which are rounded values commonly used in the literature." (Introduction); "using a nominal position of R.A.(ICRS)=07$^{\rm h}$:42$^{\rm m}$:16.894m Dec.(ICRS)=$-$14$^\circ$42$'$49$.\!\!^{\prime\prime}$836." (2 Observations); z/distance d=1500 pc (adopted); i=35 deg  
  > "Here we have adopted $d$=1500 pc and $i$=35$^\circ$, which are rounded values commonly used in the literature." (Introduction); "using a nominal position of R.A.(ICRS)=07$^{\rm h}$:42$^{\rm m}$:16.894m Dec.(ICRS)=$-$14$^\circ$42$'$49$.\!\!^{\prime\prime}$836." (2 Observations); distance from rounded from H2O maser parallax d=1.54 kpc (Choi et al. 2012)  
  > "Here we have adopted $d$=1500 pc and $i$=35$^\circ$, which are rounded values commonly used in the literature." (Introduction); "using a nominal position of R.A.(ICRS)=07$^{\rm h}$:42$^{\rm m}$:16.894m Dec.(ICRS)=$-$14$^\circ$42$'$49$.\!\!^{\prime\prime}$836." (2 Observations)

## Data provenance

- ALMA projects: 2015.1.00256.S
- bands: Band 7 (~294-345 GHz)  
  > "Five different spectral windows (SPWs) within band 7 ($\sim$294-345 GHz) were observed in each of our two science goals" (2 Observations)
- frequencies and spectral setup: 5 SPWs per science goal; SG1 5-pointing mosaic (~19''x54'', PA=21 deg), SG2 single pointing at center  
  > "SG1-observations were performed as a five-pointing mosaic covering a $\sim$19$''$$\times$54$''$ area along the main symmetry axis" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: ALMA 12-m array  
  > "OH 231.8 was observed with the ALMA 12-m array as part of project 2015.1.00256.S on July 2016." (2 Observations)
- configurations: _not stated_
- baselines: SG1: 15.1-867.2 m; SG2: 16.7-1100 m  
  > "The minimum and maximum baseline length in our SG1 and SG2 observations were 15.1 and 867.2 m and 16.7 and 1100 m, respectively" (2 Observations)
- angular resolution: ~0.2''-0.3''  
  > "leading to a spatial resolution of $\sim$0.2$''$-0.3$''$." (2 Observations)
- max recoverable scale: ~3''  
  > "the angular size of the largest smooth structure to which our observations are sensitive (or maximum recoverable scale) is $\sim$3$''$." (2.1 Flux losses)
- sensitivity: rms 1.6-6 mJy/beam in line-free channels of cubes  
  > "The typical rms noise level in the line-free channels of our spectral cubes is 1.6-6 mJy/beam." (2 Observations)
- time on source: 35x3 min (SG1), 44x3 min (SG2), ~4 h total  
  > "was 35$\times$3 and 44$\times$3 minutes for SG1 and SG2, respectively (a total of about 4 hours)" (2 Observations)
- observing dates: July 2016  
  > "OH 231.8 was observed with the ALMA 12-m array as part of project 2015.1.00256.S on July 2016." (2 Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (345795.990 MHz)
- Line: 13CO J=3-2 (330587.965 MHz)
- Line: SiO J=7-6 (303926.812 MHz)
- Line: CS J=6-5, 7-6 (293912.086, 342882.850 MHz)
- Line: CH3OH 2_1,1-2_0,2 and 4_1,3-4_0,4 (304208.350, 307165.940 MHz)
- Line: Na37Cl J=26-25 (330805.749 MHz)
- Other facility **IRAM 30m**: Single-dish spectra for comparison of line fluxes/flux losses  
  > "we confront line integrated profiles from our ALMA maps with single-dish spectra from our mm-wavelength survey of OH 231.8 with the IRAM 30m telescope" (2.1 Flux losses)
- External data: Distance from H2O maser trigonometric parallax, d=1.54 kpc  
  > "leading to $d$=1.54$^{+0.02}$$^{(-0.01)}$ kpc (cite: choi12)" (Introduction) [from (cite: choi12)]
- External data: Dust absorption coefficient 0.33 cm2/g at 1 mm  
  > "adopting a dust absorption coefficient of $\kappa_{\nu}$=0.33 cm$^2$/g at 1 mm (cite: li01)" (3 Continuum emission by dust) [from (cite: li01)]
- External data: CS fractional abundance X(CS)=5e-8  
  > "we adopt a source-averaged value of X(CS)=5$\times 10^{\rm -8}$ (cite: san97)" (5.1 Density and temperature distribution) [from (cite: san97)]
- External data: Spectroscopic data and partition functions from MADEX; line frequencies from CDMS  
  > "have been obtained from the MADEX catalog (cite: madex)." (5.1 Density and temperature distribution) [from (cite: madex); (cite: mul05)]

## Processing

### Calibration

- pipeline or manual: Automated ALMA pipeline  
  > "The visibility data for each session (execution block) were calibrated by the automated pipeline of the Common Astronomy Software Applications (CASA) version 4.7.0." (2 Observations)
- casa version: CASA 4.7.0  
  > "calibrated by the automated pipeline of the Common Astronomy Software Applications (CASA) version 4.7.0." (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~5% (294-306 GHz), 10% (330-345 GHz)  
  > "Absolute flux calibration uncertainties are $\sim$5% and 10% at \[294-306\] and \[330-345\] GHz, respectively." (Table 2)
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "we created spectral cubes for the different transitions using the CASA task `tclean` using a spectral resolution of $\Delta \upsilonup$=1-3 km s$^{-1}$" (2 Observations)
- deconvolver: _not stated_
- weighting robust: Briggs robust=0.5 by default; robust=-2 (uniform) for some transitions  
  > "By default, we used Briggs weighting with a robust parameter of 0.5" (2 Observations); "uniform weighing (robust=$-$2) for an improved angular resolution" (2 Observations)
- uv taper: _not stated_
- cell size: 0.04''  
  > "The pixels have a size of 0$.\!\!^{\prime\prime}$04 in all our maps." (2 Observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum subtracted from visibilities in the baseband containing the line  
  > "Line emission cubes were created after subtracting the continuum from the visibility data in the spectral baseband containing the line (USB or LSB)." (2 Observations)
- line free channels: _not stated_
- primary beam correction: impbcor  
  > "All images are corrected for the primary beam" (2 Observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: continuum 0.31''x0.25'' PA=-84.5 deg; cubes 0.31x0.25 (SG1), 0.28x0.22 (SG2)  
  > "restored using a common clean beam, with half-power beam width HPBW=0$.\!\!^{\prime\prime}$31$\times$0$.\!\!^{\prime\prime}$25 and oriented along PA=$-$84.5$^\circ$" (2 Observations)
- final rms: _not stated_

### Inherited from earlier work

- Rotational diagram analysis method  
  > "This method is described in detail and discussed extensively by, e.g., (cite: gol99)" (5.1 Density and temperature distribution) [from (cite: gol99)]
- Dust mass formulation for optically thin case  
  > "using the formulation described, for example, in (cite: san98)" (3 Continuum emission by dust) [from (cite: san98)]
- Bow-shock velocity analysis  
  > "Using the simple analytic formula derived by (cite: har87), which relates the centroid of the bow-shock profile" (4.2) [from (cite: har87)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for continuum imaging
- Clean threshold, masks and deconvolver/niter for tclean
- Exact continuum channel selection and flux integration region
- Whether rotational diagram fit used any S/N cut or uncertainty weighting
- Details of the CLASS MODSOURCE models (fit procedure)
- Which flux calibrator and calibration-source fluxes were used

## Analysis recipe

1. **Image continuum**: Continuum images from line-free channels of USB and LSB for each science goal, restored with a common beam  
  > "two continuum images were made using the line-free channels from the upper and lower sideband (USB and LSB) spectral windows" (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared total fluxes to single-dish measurements  
  > "The good agreement of the ALMA total fluxes with measurements from single-dish observations" (3)
2. **Size of clump S**: uv-plane fit of Gaussian and disk models to long baselines (>250 m)  
  > "we have fitted a single component source model to the $uv$ continuum data using only the longest baselines (length$>$250 m)" (3)
   - software: CASA uvmodelfit
   - fitting: uvmodelfit elliptical Gaussian / disk  
  > "we have fitted a single component source model to the $uv$ continuum data using only the longest baselines (length$>$250 m)." (3 Continuum emission by dust)
   - validation: _not stated_
3. **Dust temperature and mass of clump S**: Optically thick vs optically thin large-grain scenarios; radiative equilibrium Td formula and dust mass  
  > "assuming radiative equilibrium (i.e., that the energy absorbed by the grains is totally reemitted at longer wavelengths) and that the only dust heating mechanism is the stellar radiation, the dust temperature can be expressed as:" (3 Continuum emission by dust)
   - assumption: kappa=0.33 cm2/g at 1 mm; gas-to-dust 100-200; alpha=0 for big grains; Lbol~7000 Lsun  
  > "for a typical gas-to-dust mass ratio in O-rich AGB stars of $\sim$100-200 (cite: kna85)" (3)
   - fitting: _not stated_
   - validation: _not stated_
4. **Rotational temperature, CS column density and H2 density maps**: Pixel-by-pixel straight-line fit to ln(Nu/gu) vs Eu from CS 7-6 and 6-5 channel maps matched to common beam  
  > "a straight-line has been fitted pixel by pixel to the $\ln(N_7/g_7)$ and $\ln(N_6/g_6)$ velocity-channel maps" (5.1)
   - software: MADEX
   - parameter: common beam 0.31''x0.25''; 3 km/s channels  
  > "matching the dimensions and beam size of both maps to a common value of 0$.\!\!^{\prime\prime}$31$\times$0$.\!\!^{\prime\prime}$25" (5.1)
   - assumption: Optically thin LTE; constant X(CS)=5e-8; d=1500 pc  
  > "making the simplifying assumption that the CS-to-H$_2$ fractional abundance is constant throughout the outflow" (5.1)
   - fitting: linear least-squares line fit per pixel  
  > "Then, a straight-line has been fitted pixel by pixel to the $\ln(N_7/g_7)$ and $\ln(N_6/g_6)$ velocity-channel maps" (5.1 Density and temperature distribution)
   - validation: Compared with IRAM-30m/Herschel CS rotational diagram (private communication)  
  > "are in good agreement with the source-averaged values obtained from a similar rotational diagram ana­ly­sis" (5.1)
5. **Abundances of Na37Cl, SiS, 30SiO, CH3OH**: LTE line-profile models with CLASS MODSOURCE using column density, Tex, source size, linewidth; H2 column from mass-loss rate or CS density  
  > "We have used the CLASS task ` MODSOURCE` to model the observed Na$^{37}$Cl ($v$=0, $J$=26-25) emission profile assuming LTE" (5.2.1)
   - software: CLASS (GILDAS)
   - parameter: Tex 100-1000 K (NaCl), 500-1500 K (vib. lines), 50-200 K (CH3OH)  
  > "excitation temperature between 100 and 1000 K" (5.2.1)
   - assumption: Mdot~1e-5 Msun/yr, Vexp=7 km/s, 35Cl/37Cl~2  
  > "Adopting constant values of $\dot{M}$$\sim$10$^{-5}$ $M_{\odot}$ yr$^{-1}$ and $V_{\rm exp}$=7 km s$^{-1}$" (5.2.1)
   - fitting: _not stated_
   - validation: Compared with abundances in VY CMa and IK Tau  
  > "is again in very good agreement with the fractional abundance of salt measured in VY CMa and IK Tau" (5.2.1)
6. **Kinematic ages from PV diagrams**: Linear velocity gradients from axial PV diagrams converted to kinematic ages using inclination  
  > "This gradient implies short kinematical ages of $t_{\rm kin}$$\sim$\[84-142\]$\times$$\tan{(i)}$ years" (4.2)
   - assumption: i=30-35 deg  
  > "then we derive a value of the inclination of $i$$\sim$30$^\circ$-35$^\circ$ and a kinematical age of about 500 yr for these components." (4.3 The periphery of the SiO outflow)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.0: Pipeline calibration, tclean imaging, impbcor, uvmodelfit  
  > "The data here presented have been reduced by CASA" (Acknowledgements)
- **GILDAS/CLASS** : Data analysis and MODSOURCE line modelling  
  > "data analysis was made using the GILDAS software" (Acknowledgements)
- **MADEX** : Spectroscopic parameters and partition function  
  > "have been obtained from the MADEX catalog (cite: madex)." (5.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum total flux at 344.310 GHz | 1.88 | ~10% absolute | Jy | 1 | /  344.310  /    1.88    /    71.4    /    0.50    / |
| Continuum total flux at 293.912 GHz | 1.13 | ~5% absolute | Jy | 1 | /  293.912  /    1.13    /    51.1    /    0.30    / |
| Spectral index of clump S continuum | 2.1 | not stated | dimensionless | 1 | the continuum follows a less steep $S_\nu$ $\propto$ $\nu^{2.1}$ frequency dependence |
| Clump S deconvolved size (Gaussian) | 0.054x0.043 | not stated | arcsec | 2 | yields beam-deconvolved dimensions of $\sim$0$.\!\!^{\prime\prime}$054$\times$0$.\!\!^{\prime\prime}$043 |
| Dust mass in clump S (a=100 um) | 2e-5 | not stated | Msun | 3 | $M_{\rm d}$$\sim$2$\times 10^{\rm -5}$ (2$\times 10^{\rm -4}$) $M_{\odot}$ for a grain radius of $a$=100 (1000) $\mu$m |
| CS rotational temperature in lobe walls | 10-30 | not stated | K | 4 | We find values of $T_{\rm rot}$$\sim$10-30 K in the lobe walls |
| H2 density in lobe walls | 2-4e5 | not stated | cm-3 | 4 | $n_{\rm H_2}$$\sim$\[2-4\]$\times 10^{\rm 5}$$\,$cm$^{\rm -3}$ |
| X(CH3OH) | 1e-8 to 1e-7 | not stated | dimensionless | 5 | X(CH$_3$OH)$\approx$10$^{-8}$-10$^{-7}$ |
| X(Na37Cl) | 1-3e-9 | factor ~3 | dimensionless | 5 | we deduce a Na$^{37}$Cl fractional abundance of about $\approx$\[1-3\]$\times 10^{\rm -9}$ |
| Kinematic age of SiO outflow inner regions | 50-80 | not stated | yr | 6 | $t_{\rm kin}$$\sim$50-80 yr adopting $i$=30$^\circ$ |
| Kinematic age of large waist | 870 | not stated | yr | 6 | leading to a kinematical age of $t_{\rm kin}$$\sim$715 yr/$\cos{(i)}$$\sim$870 yr |
| Fish bowl age | 650 | 100 | yr | 6 | started expanding and moving away from each other about $\sim$650$\pm$100 yr ago |
| Offset of QX Pup from waist | 0.6 | not stated | arcsec | 0 | is clearly offset from the waist of the large hourglass by $\delta$y$\sim$0$.\!\!^{\prime\prime}$6 (900 AU) |

## Qualitative findings

- First detections of Na37Cl and CH3OH in OH 231.8; CH3OH first in an AGB star; vibrationally excited SiS and 30SiO newly detected  
  > "The detection of CH$_3$OH is particularly important since this is the first AGB star" (4)
- Newly found structures: compact SiO bipolar outflow, mini-hourglass, and two 'fish bowl' bubbles  
  > "We report the discovery of two large ($\sim$8$''$$\times$6$''$) faint bubble-like structures surrounding the central parts of the nebula" (Summary)

## Claim tuples

- H: Where is the mass-losing star QX Pup relative to the nebula? | E: Continuum maps and compact high-excitation line emission | R: Continuum peak clump S coincides with SiS v=1, 30SiO v=1, NaCl emission and SiO masers, offset 0.6'' south of the waist | F: QX Pup lies in clump S, offset from the waist | **supported**
- H: Are there recent bipolar ejections near the star? | E: SiO and 29SiO channel maps and PV diagrams | R: Compact ~1''x4'' SiO outflow with kinematic ages 50-80 yr inner to 400-500 yr at tips | F: Current jet engine is still active, disfavouring common envelope origin | **supported**
- H: Physical conditions in the central nebula | E: CS 7-6 and 6-5 rotational diagrams per pixel | R: Lobes cold (20-40 K) and dense (~1e5 cm-3), waist denser (>=1e6) and warmer | F: Dense, cold molecular lobes with warmest gas in the center | **supported**
- H: Origin of QX Pup offset | E: Compare orbital motion and recoil scenarios with offset and Vsys difference | R: Neither scenario fully satisfactory alone | F: Possibly a combination of orbital motion and recoil | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Optically thick dust for clump S rejected because implied dust mass is unrealistically high  
  > "This result rules out the optically-thick dust scenario to explain $S_\nu$ $\propto$ $\nu^{2.1}$ in clump *S*." (3)
- How they decided it was enough: _not stated_
- Limitation (authors): Clump S size uncertain/marginally resolved; angular resolution insufficient to measure binary separation  
  > "We stress that this value is very uncertain and it could well represent an upper limit" (3); "the angular resolution of our current ALMA observations is not sufficient to obtain an accurate estimate of this separation" (6.2)
- Caveat (inferred, ours): Abundance estimates rely on crude LTE models with broad Tex ranges and assumed mass-loss rate
- Caveat (inferred, ours): Kinematic ages depend strongly on inclination assumptions
- Caveat (inferred, ours): Fish-bowl geometry degenerate in c and inclination

## Reproducibility

- Data public (paper): Data cited by project code in acknowledgements; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00256.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Clean parameters and masks
- Missing: Line-free channel selection
- Missing: MODSOURCE model fit details
- Missing: Velilla Prieto et al. IRAM-30m survey data (in preparation)
- Data volume (inferred): ~50-200 GB raw for 6 execution blocks (inferred)
- Score (inferred): 3/5, Data identified and public-likely, calibration/imaging mostly described, but many analyses are qualitative with unstated details.
- Rediscovery candidate: no, Main results are largely morphological/kinematic and order-of-magnitude estimates; imaging details incomplete.

## Links

- Method: Goldsmith & Langer 1999 (cite: gol99) (Rotational diagram method)
- Method: Hartigan et al. 1987 (cite: har87) (Bow-shock profile analysis)
- Companion: Alcolea et al. 2001 (cite: alc01) (Previous CO interferometric study of OH 231.8)
- Companion: Velilla Prieto et al., in preparation (IRAM-30m survey of OH 231.8)

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
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 55,
  "rate": 0.671
 },
 "evidence_ok": true
}
```

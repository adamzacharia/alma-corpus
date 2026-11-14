# Subarcsecond Analysis of the Infalling-Rotating Envelope around the Class I Protostar IRAS 04365+2535

`2016ApJ...820L..34S` | The Astrophysical Journal Letters 2016 | first author: Sakai, Nami | arXiv: 1603.08608 | DOI: 10.3847/2041-8205/820/2/L34

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry, protoplanetary_disks
- Question: What are the kinematics and chemical structure (CS, SO) of the infalling-rotating envelope around the Class I protostar TMC-1A, and does a chemical change occur at the centrifugal barrier?  
  > "In the present study, we extend such a chemical approach to the low-mass Class I source IRAS 04365+2535 in TMC-1A, whose luminosity is 2.5 $L_\odot$ (Green et al. 2013)." (Introduction)
- Target **IRAS 04365+2535 (TMC-1A)**: coordinates 04h39m35.2s, +25d41m44.35s (J2000, field center)  
  > "The field center is: ($\alpha_{2000}, \delta_{2000})$=$(04^{\rm h} 39^{\rm m} 35.2s, 25^{\circ} 41^{\prime} 44.35\ensuremath{''})$." (Observations); "TMC-1A is located in the Heiles Cloud 2 ($d$=137 pc; Torres et al. 2007)" (Introduction); z/distance 137 pc  
  > "The field center is: ($\alpha_{2000}, \delta_{2000})$=$(04^{\rm h} 39^{\rm m} 35.2s, 25^{\circ} 41^{\prime} 44.35\ensuremath{''})$." (Observations); "TMC-1A is located in the Heiles Cloud 2 ($d$=137 pc; Torres et al. 2007)" (Introduction); distance from Torres et al. 2007  
  > "The field center is: ($\alpha_{2000}, \delta_{2000})$=$(04^{\rm h} 39^{\rm m} 35.2s, 25^{\circ} 41^{\prime} 44.35\ensuremath{''})$." (Observations); "TMC-1A is located in the Heiles Cloud 2 ($d$=137 pc; Torres et al. 2007)" (Introduction)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 6  
  > "The observation of IRAS 04365$+$2535 in L1527 was carried out with ALMA (cycle 2) on 2014 June 15 (Band 6)." (Observations)
- frequencies and spectral setup: 59 MHz bandwidth, 122 kHz resolution (61 kHz channel spacing), velocity resolution 0.14 km/s  
  > "The backend correlator was tuned to be 59 MHz bandwidth with 122 kHz resolution (channel spacing is 61 kHz). The velocity resolution is 0.14 km s$^{-1}$." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 31 antennas, max baseline 642 m  
  > "Thirty-one antennas were used during the observation, and the maximum baseline length was 642 m." (Observations)
- angular resolution: 0.65"x0.37" (continuum), 0.69"x0.40" (CS), 0.65"x0.37" (SO)  
  > "The synthesized beam size is $0.65\ensuremath{''} \times 0.37\ensuremath{''}$ (PA=13$^\circ$), $0.69\ensuremath{''} \times 0.40\ensuremath{''}$ (PA=11$^\circ$)" (Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 27 min  
  > "The total on-source time was 27 min." (Observations)
- observing dates: 2014 June 15 (Cycle 2)  
  > "was carried out with ALMA (cycle 2) on 2014 June 15 (Band 6)." (Observations)
- pi or archival as stated: _not stated_
- Line: CS J=5-4 (244.9355565 GHz)
- Line: SO J_N=7_6-6_5 (261.843721 GHz)
- External data: Systemic velocity 6.5 km/s, average of literature values  
  > "A systemic velocity of this source is 6.5 km s$^{-1}$, which is an average of the reported values (Brown & Chandler 1999; Yen et al. 2013; Harsono et al. 2014)" (CS) [from Brown & Chandler 1999; Yen et al. 2013; Harsono et al. 2014]
- External data: Envelope extension angle 30 deg from K-band image  
  > "The extension angle of the envelope thickness is assumed to be 30$^\circ$, judging from the K-band (1.92-2.55 $\mu$m) image of this source" (CS) [from Ishii, Tamura, and Itoh 2004]
- External data: Distance 137 pc  
  > "TMC-1A is located in the Heiles Cloud 2 ($d$=137 pc; Torres et al. 2007)" (Introduction) [from Torres et al. 2007]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0423-013 (flux); J0510+1800 (phase and bandpass)  
  > "The absolute flux density scale was derived from J0423-013." (Observations)
- flux scale uncertainty: less than 10 %  
  > "The data calibration was performed in the antenna-based manner, and uncertainties are less than 10 %." (Observations)
- self calibration: not performed  
  > "We did not conduct self-calibration for the data used in this paper." (Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "we used the Briggs weighting for the UV data with the robust parameter of 0.5." (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum subtracted directly from visibilities; continuum from line-free channels  
  > "The line images were obtained by CLEANing the dirty images after subtracting the continuum directly from the visibilities." (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.65"x0.37" PA 13 (cont), 0.69"x0.40" PA 11 (CS), 0.65"x0.37" PA 12 (SO)  
  > "for the continuum, CS, and SO images, respectively." (Observations)
- final rms: _not stated_

### Inherited from earlier work

- SO/CS abundance ratio derived with same non-LTE method  
  > "The abundance ratio of SO/CS at the centrifugal barrier is derived by using the same non-LTE method described in Sakai et al. (2014b)." (SO) [from Sakai et al. 2014b]
- Simple ballistic infalling-rotating envelope model  
  > "a simple ballistic model of an infalling-rotating envelope which is previously applied to L1527 (Sakai et al. 2014a, b; Oya et al. 2015) and IRAS15398-3359 (Oya et al. 2014)" (CS) [from Sakai et al. 2014a,b; Oya et al. 2014, 2015]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration pipeline/manual choice
- Line-free channels used for continuum
- Cell size, image size, clean threshold and masks
- Ballistic model code and parameter grid, and how fit quality was judged (by eye)
- Non-LTE code and collision/column density inputs for SO/CS ratio
- PV cut widths and position angle details

## Analysis recipe

1. **Measure continuum**: 2D Gaussian fit to 260 GHz continuum image  
  > "The peak position derived by the two-dimensional Gaussian fit is" (Continuum)
   - fitting: _not stated_
   - validation: Compared with fluxes of Harsono et al. 2014 and Aso et al. 2015 with beta=1.46  
  > "The integrated flux is almost consistent with those reported by Harsono et al. (2014) (164 mJy at 220 GHz)" (Continuum)
2. **Moment maps and PV diagrams of CS and SO; determine PA**: Moment 0/1 maps; PA from line through blue/red peaks and continuum peak; PV along envelope and outflow directions  
  > "We determined the position angle (PA) of the disk/envelope system to be 70$^\circ$ using this line." (CS)
   - parameter: blue/red components 2.5<|dV|<3.5 km/s from systemic 6.5 km/s  
  > "(3.5 km s$^{-1}$ $>|$$\delta$V$|>$ 2.5 km s$^{-1}$)" (CS)
   - fitting: _not stated_
   - validation: Compared with PA of Harsono et al. and Aso et al.  
  > "It is consistent with that reported by Harsono et al. (2014)" (CS)
3. **Fit ballistic infalling-rotating envelope model to PV diagrams**: Simulated emission from particle motion under energy and angular momentum conservation; parameters rCB, M, inclination explored  
  > "the gas motion is approximated by the particle motion under conservation of kinetic energy and angular momentum." (CS)
   - parameter: outer radius 350 AU; convolved with 0.5 km/s velocity width and 0.69"x0.40" beam  
  > "The model image is convolved by the velocity width of 0.5 km s$^{-1}$ and the beam size of $0.69\ensuremath{''} \times 0.40\ensuremath{''}$ (PA=11$^\circ$)." (CS)
   - assumption: r^-1.5 density profile, constant abundances, optically thin, no excitation, envelope thickness extension angle 30 deg  
  > "we simply assume an $r^{-1.5}$ density profile and constant molecular abundances. The lines are assumed to be optically thin, and no excitation effect is considered for simplicity." (CS)
   - fitting: Parameter space searched; acceptable range judged by reproducing PV diagrams (no formal sampler stated)  
  > "We found a set of parameters which can reasonably reproduce the observed PV diagrams." (CS)
   - validation: 0.2 km/s line width gives no significant change  
  > "the simulation does not change significantly by use of the 0.2 km s$^{-1}$ line width" (CS)
4. **SO/CS abundance ratio at centrifugal barrier**: Non-LTE analysis of integrated intensities for red (7.9-9.3 km/s) and blue (3.7-5.1 km/s) components  
  > "we used the intensities integrated from 7.9 to 9.3 km s$^{-1}$ and from 3.7 to 5.1 km s$^{-1}$ for the red-shifted and blue-shifted components" (SO)
   - software: LAMDA
   - parameter: H2 density 3e6-3e8 cm-3, temperature 30-120 K  
  > "for the H$_2$ density range from $3 \times 10^6$ to $3 \times 10^8$ cm$^{-3}$ and the temperature range from 30 to 120 K" (SO)
   - fitting: _not stated_
   - validation: Compared with L1527 ratio  
  > "The ratio for the red-shifted component is comparable to that found in L1527 (4.6$-$5.9)" (SO)

## Software

- **LAMDA** : Einstein A and collisional data for critical density  
  > "calculated from the Einstein A coefficient and the collisional cross section (LAMDA; Sch$\rm \ddot{o}$ier et al. 2005; Lique et al. 2006)" (SO)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum peak flux | 166.9 | 0.9 | mJy/beam | 1 | The peak flux is determined to be 166.9 $\pm$0.9 mJy beam$^{-1}$ from the Gaussian fit |
| Continuum integrated flux | 268.2 | 2.3 | mJy | 1 | while the integrated flux is 268.2$\pm$2.3 mJy |
| Disk/envelope position angle | 70 | not stated | deg | 2 | We determined the position angle (PA) of the disk/envelope system to be 70$^\circ$ using this line. |
| Centrifugal barrier radius (best) | 50 (acceptable 40-60) | not stated | AU | 3 | The acceptable range of $r_{\rm CB}$ is from 40 AU to 60 AU |
| Protostellar mass (best) | 0.25 (range 0.20-0.30) | not stated | Msun | 3 | that of the mass is from 0.20 $M_\odot$ to 0.30 $M_\odot$ |
| Inclination (best) | 20 (range 10-30) | not stated | deg | 3 | ($r_{\rm CB}$=50 AU, $M$=0.25 $M_\odot$, and $i$=20$^\circ$) |
| SO/CS ratio red-shifted | 4.6-8.8 | not stated | dimensionless | 4 | The SO/CS ratio is evaluated to be 4.6$-$8.8 and 1.9$-$3.2 for the red-shifted and blue-shifted components |
| SO/CS ratio blue-shifted | 1.9-3.2 | not stated | dimensionless | 4 | The SO/CS ratio is evaluated to be 4.6$-$8.8 and 1.9$-$3.2 for the red-shifted and blue-shifted components |

## Qualitative findings

- CS shows infalling-rotating motion; rotation disappears at ~50 AU; infalling gas distribution asymmetric  
  > "The rotation motion traced by CS abruptly disappears around the radius of 50 AU from the protostar" (CS)
- SO is concentrated around the centrifugal barrier, more compact than CS  
  > "the distribution is concentrated around the protostar, and is more compact than that of CS." (SO)

## Claim tuples

- H: CS kinematics in TMC-1A trace an infalling-rotating envelope rather than a Keplerian disk | E: PV diagrams compared with a ballistic model | R: rCB=50 AU, M=0.25 Msun, i=20 deg reproduce the PV diagrams | F: Infalling-rotating envelope conserving angular momentum down to ~50 AU | **supported**
- H: A chemical change occurs at the centrifugal barrier as in L1527 | E: Compare CS and SO distributions with model barrier | R: SO concentrated near the barrier, CS outside | F: Infalling material is chemically processed (probably by accretion shock) before entering the disk | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Simple ballistic model used because the main purpose is to account for velocity structure  
  > "Since our main purpose is to account for the velocity structure, we simply assume an $r^{-1.5}$ density profile" (CS)
- Alternative: Keplerian disk cannot explain CS features  
  > "All these characteristic features seen in the CS emission cannot be explained by a Keplerian disk" (CS)
- How they decided it was enough: _not stated_
- Limitation (authors): Ballistic model may be oversimplified  
  > "our ballistic model could be oversimplified" (CS)
- Caveat (inferred, ours): Model fit by eye with no quantitative goodness of fit or uncertainties
- Caveat (inferred, ours): Mass 0.25 Msun disagrees with 0.68 Msun of Aso et al.
- Caveat (inferred, ours): Source name misprinted as L1527 in Observations
- Caveat (inferred, ours): Asymmetric envelope not modelled

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Ballistic model code and grid
- Missing: Imaging parameters
- Missing: Non-LTE inputs
- Data volume (inferred): ~5-20 GB
- Score (inferred): 3/5, Single ALMA dataset with robust 0.5 stated, but model and imaging details are sparse.
- Rediscovery candidate: no, Public status not stated in paper and model fit is by eye with incomplete recipe.

## Links

- Method: Sakai et al. 2014b (non-LTE SO/CS method)
- Method: Oya et al. 2014 (ballistic model)
- Companion: Aso et al. 2015 (C18O ALMA study of TMC-1A)
- Companion: Sakai et al. 2014a (L1527 centrifugal barrier)

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2013.1.01102.S"
 ],
 "codes_printed_but_missing": [
  "2013.0.01102.S"
 ],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 40,
  "rate": 0.58
 },
 "evidence_ok": true
}
```

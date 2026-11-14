# Discovery of a Hot Corino in the Bok Globule B335

`2016ApJ...830L..37I` | The Astrophysical Journal Letters 2016 | first author: Imai, Muneaki | arXiv: 1610.03942 | DOI: 10.3847/2041-8205/830/2/L37

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: Does the isolated Bok globule protostar B335 (IRAS 19347+0727) harbor a hot corino, i.e. compact emission from saturated complex organic molecules?  
  > "We report the first evidence of a hot corino in a Bok globule." (abstract)
- Target **B335 (IRAS 19347+0727)**: coordinates 19h37m0.93s, +7d34m9.9s (J2000, field center)  
  > "The field center is $\alpha$(J2000)=19$^\mathrm{h}$37$^{\mathrm{m}}$0.93s, $\delta$(J2000)=7$^\circ$34$'$9.9$''$." (3 Observation); "Its distance and bolometric luminosity are reported to be 100 pc (cite: olofsson2009) and 0.72 $L_{\ensuremath{\odot}}$ (cite: evans2015), respectively." (1 Introduction); z/distance 100 pc  
  > "The field center is $\alpha$(J2000)=19$^\mathrm{h}$37$^{\mathrm{m}}$0.93s, $\delta$(J2000)=7$^\circ$34$'$9.9$''$." (3 Observation); "Its distance and bolometric luminosity are reported to be 100 pc (cite: olofsson2009) and 0.72 $L_{\ensuremath{\odot}}$ (cite: evans2015), respectively." (1 Introduction); distance from Olofsson & Olofsson 2009 (cite: olofsson2009)  
  > "The field center is $\alpha$(J2000)=19$^\mathrm{h}$37$^{\mathrm{m}}$0.93s, $\delta$(J2000)=7$^\circ$34$'$9.9$''$." (3 Observation); "Its distance and bolometric luminosity are reported to be 100 pc (cite: olofsson2009) and 0.72 $L_{\ensuremath{\odot}}$ (cite: evans2015), respectively." (1 Introduction)

## Data provenance

- ALMA projects: 2013.1.01102.S
- bands: Band 6 (1.2 mm, 250 GHz), Cycle 2  
  > "We conducted the 1.2 mm (250 GHz) observation (Band 6) of B335 with ALMA (Cycle 2) on May 18, 2015." (3 Observation)
- frequencies and spectral setup: 16 spectral windows, 58.6 MHz bandwidth, 61.027 kHz channel spacing, 0.1404 km/s velocity resolution  
  > "We used 16 spectral windows whose bandwidth and channel spacing are 58.6 MHz and 61.027 kHz, respectively. The velocity resolution is 0.1404 km s$^{-1}$." (3 Observation)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 to 444 kλ; 37 antennas  
  > "Minimum and maximum baselines are 15 k$\lambda$ and 444 k$\lambda$, respectively." (3 Observation)
- angular resolution: 0.58'' x 0.52'' (P.A. = 75 deg)  
  > "a synthesized beam size is 0.58$''$ $\times$ 0.52$''$ (P.A. = 75$^\circ$)" (3 Observation)
- max recoverable scale: _not stated_
- sensitivity: rms 3-7 mJy/beam  
  > "which resulted in the rms noise of 3-7 mJy beam$^{-1}$" (3 Observation)
- time on source: 34 minutes  
  > "On-source integration time was  34 minutes" (3 Observation)
- observing dates: May 18, 2015  
  > "We conducted the 1.2 mm (250 GHz) observation (Band 6) of B335 with ALMA (Cycle 2) on May 18, 2015." (3 Observation)
- pi or archival as stated: _not stated_
- Line: HCOOCH3 20(5,16)-19(5,15) E/A (249.031002 / 249.047428 GHz)
- Line: NH2CHO 12(0,12)-11(0,11) (247.390719 GHz)
- Line: CH3CHO 14(1,14)-13(1,13) E/A (260.530403 / 260.544020 GHz)
- Line: HNCO 12(0,12)-11(0,11) (263.748625 GHz)
- Line: SO N_J=6_7-5_6 (261.843684 GHz)
- Line: CCH N=3-2 (four hyperfine lines) (262.004260-262.067469 GHz)
- External data: Mass absorption coefficient at 850 um (1.48e-2) and beta index 2.38 for B335, used to get kappa at 1.2 mm (0.0068 cm2/g)  
  > "which are reported for B335 by (cite: shirley2011)" (4.3 Derivation of Column Density and Fractional Abundance) [from (cite: shirley2011)]
- External data: Systemic velocity 8.34 km/s  
  > "assuming the systemic velocity of 8.34 km s$^{-1}$ (cite: yen2015)" (4.2 Detected Molecules and Their Distribution) [from (cite: yen2015)]
- External data: Mass-weighted dust temperature 111 K at ~0.5'' beam  
  > "mass-weighted dust temperature (cite: kauffmann2008) at a roughly 0.5$''$ beam (111 K) reported for B335 by (cite: evans2015)" (4.3 Derivation of Column Density and Fractional Abundance) [from (cite: evans2015)]
- External data: COM abundances in IRAS 16293-2422, IRAS 4A, IRAS 2A, L1689B, Orion KL for comparison  
  > "comparable to that reported for the prototypical hot corino IRAS 16293-2422 ($9 \times 10^{-9}$) (cite: jaber2014)" (5 Discussion) [from (cite: jaber2014); (cite: taquet2015); (cite: bacmann2012); (cite: friedel2005)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (flux); J1955+1358 phase; J1751+0939 bandpass  
  > "Titan was observed as a flux calibrator. J1955+1358 and J1751+0939 were observed as a phase calibrator and a bandpass calibrator respectively." (3 Observation)
- flux scale uncertainty: 10 %  
  > "The calibration accuracy is 10 %." (3 Observation)
- self calibration: not applied  
  > "Self-calibration was not applied for simplicity." (3 Observation)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5  
  > "Maps of the spectral line emission were obtained by CLEANing the dirty images (Briggs robust = 0.5)" (3 Observation)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum subtracted directly from visibility data; continuum from averaging line-free channels  
  > "A continuum image was prepared by averaging line-free channels." (3 Observation)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.58'' x 0.52''  
  > "a synthesized beam size is 0.58$''$ $\times$ 0.52$''$ (P.A. = 75$^\circ$)" (3 Observation)
- final rms: _not stated_

### Inherited from earlier work

- Systemic velocity of 8.34 km/s adopted from Yen et al.  
  > "assuming the systemic velocity of 8.34 km s$^{-1}$ (cite: yen2015)" (4.2 Detected Molecules and Their Distribution) [from (cite: yen2015)]
- Dust opacity and beta taken from Shirley et al. for B335  
  > "which are reported for B335 by (cite: shirley2011)" (4.3 Derivation of Column Density and Fractional Abundance) [from (cite: shirley2011)]

### Not stated but needed to reproduce (our reading)

- CASA version and whether the pipeline or manual calibration was used
- Line-free channels used for continuum
- CLEAN threshold, masks, cell and image size, number of iterations
- Primary beam correction and how moment 0 maps were made (velocity ranges, clipping)
- Gaussian fit procedures for line parameters and source-size deconvolution
- Partition functions and spectroscopy entries used for column densities
- Beam/aperture and pixel used for the continuum peak flux in N(H2)
- Inconsistent beam P.A. (75 vs 55 deg) not clarified

## Analysis recipe

1. **Image continuum and fit its size/flux**: Continuum averaged over line-free channels; Gaussian fit for peak position and deconvolved size  
  > "The peak position is determined by the Gaussian fit as" (4.1 Dust Continuum)
   - software: CASA
   - fitting: _not stated_
   - validation: Total flux compared with Yen et al. 1.3 mm flux  
  > "This result is consistent with the total continuum flux (compact + extended) of 87.5$\pm$2.8 mJy at 1.3 mm reported by (cite: yen2015)." (4.1 Dust Continuum)
2. **Identify lines and fit line parameters**: Assign lines with CDMS and JPL, assuming v_sys 8.34 km/s; Gaussian fits for intensity, width, v_lsr  
  > "We assigned 31 spectral lines using the Cologne Database for Molecular Spectroscopy (CDMS) (cite: muller2005) and Jet Propulsion Laboratory (JPL) (cite: pickett1998) databases" (4.2 Detected Molecules and Their Distribution)
   - software: CDMS, JPL catalog
   - fitting: Gaussian fit  
  > "as well as the line parameters obtained by the Gaussian fit" (4.2 Detected Molecules and Their Distribution)
   - validation: _not stated_
3. **Make moment 0 maps and measure emitting-region sizes**: Moment 0 maps of selected lines; deconvolved FWHM sizes for HCOOCH3 and NH2CHO  
  > "Figures 1(b-i) show moment 0 maps of HCOOCH$_3$, NH$_2$CHO, HNCO, CH$_3$CHO, HCOOH, CCH, CS, and SO." (4.2 Detected Molecules and Their Distribution)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive beam-averaged column densities**: LTE, optically thin formula using integrated intensity at the continuum peak  
  > "assuming the local thermodynamic equilibrium (LTE) and optically thin conditions" (4.3 Derivation of Column Density and Fractional Abundance)
   - parameter: Tex = 100 K  
  > "the column densities are calculated for the excitation temperature of 100 K" (4.3 Derivation of Column Density and Fractional Abundance)
   - assumption: Tex 100 K as typical of IRAS 16293-2422 COMs and close to 111 K dust temperature  
  > "This temperature is a typical excitation temperature of COMs in the hot corino source IRAS 16293-2422" (4.3 Derivation of Column Density and Fractional Abundance)
   - fitting: _not stated_
   - validation: Density estimate ~5e8 cm-3 justifies LTE  
  > "Such a relatively high density justifies the LTE assumption employed in derivation of the column densities." (4.3 Derivation of Column Density and Fractional Abundance)
5. **Derive H2 column density and fractional abundances**: H2 column density from peak continuum flux with dust opacity; abundances = N(X)/N(H2)  
  > "the column density of H$_2$ is derived to be $(5.66 \pm 0.11) \times 10^{23}\ \mathrm{cm}^{-2}$ for the dust temperature of 100 K" (4.3 Derivation of Column Density and Fractional Abundance)
   - parameter: kappa(1.2 mm)=0.0068 cm2/g; mean molecular weight 2.33  
  > "The mass absorption coefficient at 1.2 mm is calculated to be 0.0068 cm$^2$ g$^{-1}$" (4.3 Derivation of Column Density and Fractional Abundance)
   - assumption: Dust temperature equals LTE temperature (100 K)  
  > "Here, we simply assume that the dust temperature equals to the LTE temperature." (4.3 Derivation of Column Density and Fractional Abundance)
   - fitting: _not stated_
   - validation: Compared with abundances in other hot corinos, hot cores and prestellar core  
  > "This comparison indicates that the abundances of COMs are enhanced in the compact region near the protostar of B335" (5 Discussion)
6. **Constrain emitting size and protostellar mass**: HNCO brightness temperature 4.2 K in beam with Tb<100 K gives diameter >=11 au; line width then gives mass limit (Keplerian or infall)  
  > "From this condition, the diameter of the emitting region is estimated to be 11 au or larger." (5 Discussion)
   - assumption: HNCO co-spatial with COMs at 100 K average temperature  
  > "HNCO is most likely present in the same region where the COMs exist." (5 Discussion)
   - fitting: _not stated_
   - validation: Consistent with Yen et al. mass >0.05 Msun  
  > "These mass estimates are consistent with that reported by (cite: yen2015) ($> 0.05\ M_\odot$)." (5 Discussion)

## Software

- **CASA** : Data reduction, continuum and line imaging  
  > "We used CASA for the data reduction." (3 Observation)
- **CDMS** : Line identification  
  > "Cologne Database for Molecular Spectroscopy (CDMS) (cite: muller2005)" (4.2 Detected Molecules and Their Distribution)
- **JPL catalog** : Line identification  
  > "Jet Propulsion Laboratory (JPL) (cite: pickett1998) databases" (4.2 Detected Molecules and Their Distribution)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total 1.2 mm continuum flux | 92.8 | 2.1 | mJy | 1 | The total integrated flux is 92.8$\pm$2.1 mJy. |
| Deconvolved size of compact continuum component | 0.43'' x 0.28'', PA 23 deg | PA ±15 deg | arcsec | 1 | A deconvolved size of the compact component of the continuum emission is 0.43$''$ $\times$ 0.28$''$ with the position angle of 23$\pm$15$^\circ$. |
| H2 column density (Td=100 K) | 5.66e23 | 0.11e23 | cm-2 | 5 | $(5.66 \pm 0.11) \times 10^{23}\ \mathrm{cm}^{-2}$ |
| HCOOCH3 fractional abundance | 4.6e-9 | 5e-10 | dimensionless | 5 | HCOOCH$_3$$^{b,c}$   / 26(3)                               /         / 46(5) |
| CH3CHO fractional abundance | 2.4e-9 | 4e-10 | dimensionless | 5 | CH$_3$CHO$^{d}$      / 14(2)                               /         / 24(4) |
| NH2CHO fractional abundance | 4.3e-10 | 4e-11 | dimensionless | 5 | NH$_2$CHO            / 2.4(2)                              /         / 4.3(4) |
| NH2CHO/HNCO ratio | 0.024 | not stated | dimensionless | 5 | In B335, the NH$_2$CHO/HNCO ratio is 0.024 |
| Minimum emitting-region diameter | >=11 | not stated | au | 6 | the diameter of the emitting region is estimated to be 11 au or larger |
| Protostellar mass lower limit | >=0.04 (Keplerian); >=0.02 (infall) | not stated | Msun | 6 | the protostellar mass is estimated to be 0.04 $M_\odot$ or higher, if the motion responsible to the line width is Keplerian. |

## Qualitative findings

- COM lines are broad (5-8 km/s) with no obvious rotation and are unresolved, so COMs lie in a structure much smaller than the beam  
  > "Though the COMs lines are as broad as 5-8 km s$^{-1}$, they do not show obvious rotation motion in the present observation." (abstract)
- CCH and c-C3H2 are extended over a few 100 au; sulfur-bearing species have compact and extended components  
  > "Carbon-chain related molecules, CCH and c-C$_3$H$_2$, are also found in this source, whose distributions are extended over a few 100 au scale." (abstract)

## Claim tuples

- H: Does B335, an isolated Bok globule protostar, harbor a hot corino? | E: ALMA Band 6 line survey, LTE column densities and abundances relative to H2, compared with other sources | R: CH3CHO, HCOOCH3, NH2CHO detected in compact region; COM abundances comparable to known hot corinos and much higher than prestellar core L1689B | F: B335 harbors a hot corino, the first identified in a Bok globule | **supported**
- H: Does NH2CHO abundance correlate with HNCO in B335? | E: Compared the NH2CHO/HNCO ratio with star-forming-region values | R: Ratio 0.024 vs 0.03-0.25 | F: The correlation holds in B335 | **partially**
- H: Can the emitting size and protostellar mass be constrained despite no resolution? | E: Brightness temperature argument from HNCO | R: Diameter >=11 au; M >=0.04 Msun (Keplerian) or 0.02 (infall) | F: Consistent with Yen et al. mass limit | **supported**

## Reasoning

- Why this data: B335 is an isolated Bok globule free from environmental effects of other protostars, so it is an ideal target  
  > "B335 is an ideal target for this purpose." (1 Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): COM distribution is not resolved; acetone detection tentative; angular resolution insufficient to see distribution trends  
  > "probably because of the insufficient angular resolution in this study" (5 Discussion)
- Caveat (inferred, ours): Single Tex=100 K and Td=Tex assumed; no uncertainty from temperature
- Caveat (inferred, ours): Optically thin LTE with continuum peak H2 column may be affected by continuum optical depth and beam dilution
- Caveat (inferred, ours): Several COM detections rest on single blended or tentative lines
- Caveat (inferred, ours): Mass limit depends on assumed 100 K and geometry

## Reproducibility

- Data public (paper): ALMA data cited by project code in acknowledgments  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.01102.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and exact imaging parameters
- Missing: Line-free channel selection and moment velocity ranges
- Missing: Partition functions/spectroscopic constants used
- Data volume (inferred): ~10-30 GB raw (one 34-min Band 6 execution, 16 narrow SPWs)
- Score (inferred): 3/5, Public data and simple analysis with a clear LTE recipe, but imaging details and software versions are missing.
- Rediscovery candidate: yes, Public data, numeric abundances from a straightforward LTE recipe, though imaging details must be reconstructed.

## Links

- Companion: Yen et al. 2015 (cite: yen2015) (Earlier ALMA observation of B335 at 0.34'' x 0.28''; source of systemic velocity and continuum comparison)
- Companion: Evans et al. 2015 (cite: evans2015) (ALMA observations of B335 giving luminosity and dust temperature)
- Related: Sakai et al. in preparation (sulfur and carbon-chain species in B335)

## Checks

```json
{
 "quotes": 70,
 "quotes_ok": 70,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 47,
  "rate": 0.603
 },
 "evidence_ok": true
}
```

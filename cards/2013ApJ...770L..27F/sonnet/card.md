# ALMA Follows Streaming of Dense Gas Down to 40 pc from the Supermassive Black Hole in NGC 1097

`2013ApJ...770L..27F` | The Astrophysical Journal Letters 2013 | first author: Fathi, Kambiz | arXiv: 1304.6722 | DOI: 10.1088/2041-8205/770/2/L27

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: What are the kinematics of the dense HCN(4-3) gas in the central 200 pc of NGC 1097, does it match the analytic nuclear spiral inflow model from ionized gas, and what is the dense gas inflow rate?  
  > "We find a striking similarity between the ALMA kinematic data and the analytic spiral inflow model that we have previously constructed based on ionized gas velocity fields on larger scales." (abstract)
- Target **NGC 1097**: coordinates _not stated_; z/distance 14.5 Mpc (~70 pc/arcsec)  
  > "At a distance of 14.5 Mpc (i.e., $\sim 70$ pc/$''$), this galaxy is also suitable for high-resolution studies" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00108.S
- bands: Band 7  
  > "Our Band 7 observations targeted the HCN(4–3) line at rest frequency of 354.505 GHz" (2 The data)
- frequencies and spectral setup: original channel 488.28125 kHz, binned by 20 to 9.77 MHz (~8.3 km/s)  
  > "the data were binned by a factor 20, leading to an effective channel width of 9.77 MHz" (2 The data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.50 x 1.20 arcsec (~105 x 84 pc), PA -72.4 deg  
  > "synthesized beam of $1\hbox{$.\!\!^{\prime\prime}$}50\times 1\hbox{$.\!\!^{\prime\prime}$}20$ ( $\sim 105 \times 84$ pc)" (2 The data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: November 5 and 6, 2011, with 14 and 15 antennas  
  > "NGC 1097 was observed with ALMA on November 5 and 6, 2011, with 14 and 15 antennas, respectively." (2 The data)
- pi or archival as stated: Proposal 2011.0.00108.S, PI: Kohno  
  > "(Proposal 2011.0.00108.S, PI: Kohno)" (Introduction)
- Line: HCN 4-3 (354.505 GHz)
- Other facility **Fabry-Perot (large scale Halpha)**: 7'x7' velocity mosaic at 15 km/s resolution for large-scale kinematics  
  > "we have used a mosaic of Fabry-Perot interferometric observations at 0$.\!\!^{\prime\prime}$83 spatial sampling" (2 The data)
- Other facility **Gemini South GMOS IFU**: Halpha velocity field of inner 7x15 arcsec  
  > "from the Gemini South Telescope’s Integral Field Unit, covering the inner $7\ensuremath{''}\times 15\ensuremath{''}$" (2 The data)
- External data: Halpha Fourier terms and analytic spiral model (pitch angle 52±4 deg) from ionized gas  
  > "Their nuclear spiral structure is consistent with a weak perturbation in the gravitational potential due to a two-arm logarithmic spiral" (5 Analysis) [from van de Ven & Fathi 2010 (vdVF)]
- External data: CO gas inflow of 0.3 Msun/yr at 100 pc  
  > "(cite: npf11) derived the CO gas inflow of $0.3$M$_\odot$ yr$^{-1}$ at 100 pc radius." (6 Dense Gas Streaming) [from (cite: npf11)]
- External data: SMBH mass 1.2e8 Msun  
  > "onto a SMBH mass of $1.2 \times 10^8$ M$_\odot$ (cite: l06)" (6 Dense Gas Streaming) [from (cite: l06)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.3 arcsec/pix  
  > "sampled at $0\hbox{$.\!\!^{\prime\prime}$}3$/pix" (2 The data)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.50 x 1.20 arcsec at PA -72.4 deg  
  > "synthesized beam of $1\hbox{$.\!\!^{\prime\prime}$}50\times 1\hbox{$.\!\!^{\prime\prime}$}20$" (2 The data)
- final rms: _not stated_

### Inherited from earlier work

- All ALMA data specifications described elsewhere  
  > "All data specifications are described in (cite: i13)." (2 The data) [from (cite: i13) Izumi et al. 2013]
- Fourier decomposition prescription for velocity field  
  > "apply the prescription used in vdVF to quantify the velocity field" (3 Kinematic Parameters) [from vdVF]
- Inflow rate prescription  
  > "The prescription for deriving mass inflow rates along the nuclear spirals has been presented in vdVF." (6 Dense Gas Streaming) [from vdVF; (cite: npf11)]

### Not stated but needed to reproduce (our reading)

- Calibration procedure, CASA version and imaging parameters (deferred to Izumi et al. 2013)
- Moment-1 clipping and channel range used
- Noise definition for A/N<20
- Ring widths for the Fourier decomposition
- Spiral model parameters (pitch angle, amplitude) used in inflow calculation
- Gas surface density and epicyclic frequency inputs

## Analysis recipe

1. **derive velocity field**: Moment-1 map cross-checked with Gaussian fits to each spectrum; pixels with A/N<20 excluded  
  > "We use the Moment 1 maps and exclude all pixels for which the corresponding spectrum Amplitude-over-Noise $A/N<20$" (2 The data)
   - fitting: _not stated_
   - validation: Gaussian fits cross-check, no significant non-Gaussianity  
  > "We found no significant signatures of non-Gaussianity" (2 The data)
2. **Fourier decomposition of velocity field**: Concentric rings (>7 pixels each); chi2 fit of centre, Vsys, PA, then Fourier terms up to 3rd order  
  > "we make the final $\chi^2$ fit to the desired modes (here up to and including 3rd order) of the Fourier decomposition" (3 Kinematic Parameters)
   - parameter: inclination fixed at 35 deg  
  > "We fix the inclination at $35^\circ$" (3 Kinematic Parameters)
   - assumption: disc predominantly rotating  
  > "We assume that the galactic disc is predominantly rotating" (3 Kinematic Parameters)
   - fitting: chi2 minimization; Monte Carlo with Gaussian-randomized velocity field for uncertainties  
  > "Repeated application to the Gaussian-randomized velocity field yields the uncertainties on the Fourier parameters." (3 Kinematic Parameters)
   - validation: Beam smoothing by factor two leaves Fourier terms unchanged; comparison with GMOS Halpha  
  > "We test the effect of beam smearing on the derived kinematic parameters by artificially smoothing by a factor two, and find that the Fourier terms remain virtually unchanged." (5 Analysis)
3. **dynamical mass**: Mass from c1 curve with thin disc model  
  > "We use the derived $c_1$ curve to measure the dynamical mass, assuming a thin disc model and velocity uncertainties of $20\%$." (6 Dense Gas Streaming)
   - fitting: _not stated_
   - validation: Compared with <3.0e7 Msun from line flux (Gao & Solomon 2004)  
  > "The derived mass at 40 pc agrees with the $<3.0\times10^7$ M$_\odot$" (7 Conclusions)
4. **dense gas inflow rate**: Marginally stable disc scale height from epicyclic frequency, spiral model parameters, arm overdensity  
  > "we set the sound speed at $10$ km s$^{-1}$ and derive the dense gas scale height (Fig. [3](#fig:4)) using the observed epicyclic frequency." (6 Dense Gas Streaming)
   - parameter: sound speed 10 km/s; arm overdensity 10%  
  > "We assume $10\%$ overdensity, similar to the upper limit of the observed value from the \[Sii\] doublet" (6 Dense Gas Streaming)
   - assumption: Romeo 1994 marginal stability criterion  
  > "The marginal stability criterion of (cite: r94) ensures that if the gas reaches higher densities, it will be confined to a thinner disc." (6 Dense Gas Streaming)
   - fitting: _not stated_
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| systemic velocity | 1300 | 48 | km/s | 2 | We derive a systemic velocity of $1300\pm48$ km s$^{-1}$ and the kinematic position angle of $147\pm6^\circ$. |
| kinematic position angle | 147 | 6 | deg | 2 | We derive a systemic velocity of $1300\pm48$ km s$^{-1}$ and the kinematic position angle of $147\pm6^\circ$. |
| dynamical mass within 100 pc | 3.5e8 | +1.6/-2.0 e8 | Msun | 3 | We derive the mass within the central 100 pc to $3.5^{+1.6}_{-2.0}\times 10^8$ M$_\odot$ |
| dynamical mass within 40 pc | 8.0e6 | +2.9/-3.5 e6 | Msun | 3 | inside the 40 pc radius, $8.0^{+2.9}_{-3.5}\times10^6$ M$_\odot$ |
| HCN inflow rate at 40 pc | 0.09 | not stated | Msun/yr | 4 | $0.09$ M$_\odot$ yr$^{-1}$ at 40 pc from the SMBH |
| HCN inflow rate at 100 pc | 0.3 | not stated | Msun/yr | 4 | We derive the HCN(4–3) inflow rate of $0.3$ M$_\odot$ yr$^{-1}$ at 100 pc |
| mean velocity uncertainty | 15 | not stated | km/s | 1 | Fitting Gaussians to each spectrum gives us the average velocity uncertainty for all the pixels at 15 km s$^{-1}$. |

## Qualitative findings

- HCN rotation curve agrees with Halpha, so dense gas is co-planar with ionized gas  
  > "the bulk rotation of the dense gas is co-planar to the ionized interstellar gas" (5 Analysis)

## Claim tuples

- H: Does the HCN(4-3) kinematics follow the analytic spiral model from ionized gas? | E: Fourier decomposition of the HCN velocity field compared with GMOS Halpha and the model | R: Fourier terms agree with model predictions down to 0.55 arcsec (~40 pc) | F: Nuclear spiral with pitch angle 52±4 deg continues to <=40 pc | **supported**
- H: What is the dense gas inflow rate towards the SMBH? | E: Marginally stable thin disc and spiral model | R: 0.3 Msun/yr at 100 pc, 0.09 Msun/yr at 40 pc | F: Combined molecular and ionized inflow ~0.2 Msun/yr at 40 pc | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Mass estimates not corrected for non-circular motions; likely lower limits; beam smears out SMBH effect  
  > "Thus, these are likely lower mass limits." (6 Dense Gas Streaming)
- Limitation (authors): Unclear how much HCN is radiatively excited  
  > "it is not clear how much, if any at all, of the observed HCN(4–3) is radiationally excited by the active nucleus" (7 Conclusions)
- Caveat (inferred, ours): Inflow rate depends on assumed 10% arm overdensity and sound speed
- Caveat (inferred, ours): Resolution of ~100 pc makes 40 pc claim rely on model extrapolation
- Caveat (inferred, ours): Inclination fixed, not fitted

## Reproducibility

- Data public (paper): Cycle 0 data of project 2011.0.00108.S (PI Kohno); public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00108.S (PI: Kohno)." (ACKNOWLEDGMENTS)
- Products in archive: _not stated_
- Missing: Calibration and imaging details (in Izumi et al. 2013)
- Missing: Spiral model parameters from vdVF and Piñol-Ferrer et al.
- Missing: Ring definition for Fourier fits
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Data are Cycle 0 and the analysis is simple, but processing and model inputs are deferred to other papers.
- Rediscovery candidate: no, Inflow rate relies on external model parameters and unstated settings.

## Links

- Method: van de Ven & Fathi 2010 (vdVF) (Fourier decomposition and inflow prescription)
- Companion: Izumi et al. 2013 (cite: i13) (ALMA data specifications)
- Companion: Piñol-Ferrer et al. 2011 (cite: npf11) (CO gas inflow with marginally stable disc)

## Checks

```json
{
 "quotes": 45,
 "quotes_ok": 45,
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
  "facts": 70,
  "stated": 33,
  "rate": 0.471
 },
 "evidence_ok": true
}
```

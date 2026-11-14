# X-shooter and ALMA spectroscopy of GRB 161023A. A study of metals and molecules in the line of sight towards a luminous GRB

`2018A&A...620A.119D` | Astronomy and Astrophysics 2018 | first author: de Ugarte Postigo, A. | arXiv: 1806.07393 | DOI: 10.1051/0004-6361/201833094

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: transients, astrochemistry, high_z_galaxies
- Question: Use the GRB 161023A afterglow as a background source to study the host environment, molecular content (via ALMA mm spectroscopy) and intervening systems along the line of sight.  
  > "We aim to use the afterglow of GRB 161023A at a redshift $z=2.710$ as a background source to study the environment of the explosion and the intervening systems along its line of sight." (abstract)
- Target **GRB 161023A**: coordinates RA 20:44:05.1718, Dec -47:39:47.921 (J2000, from ALMA)  
  > "RA: 20:44:05.1718 ($\pm0.\!\!^{\rm s}0003$)" (2.4 ALMA observations); "the afterglow of GRB 161023A at a redshift $z=2.710$" (abstract); z/distance z = 2.710  
  > "RA: 20:44:05.1718 ($\pm0.\!\!^{\rm s}0003$)" (2.4 ALMA observations); "the afterglow of GRB 161023A at a redshift $z=2.710$" (abstract); distance from X-shooter spectrum (Tanvir et al. 2016, refined in this paper)  
  > "RA: 20:44:05.1718 ($\pm0.\!\!^{\rm s}0003$)" (2.4 ALMA observations); "the afterglow of GRB 161023A at a redshift $z=2.710$" (abstract)

## Data provenance

- ALMA projects: 2016.1.00862.T
- bands: Band 3 and Band 7  
  > "Millimetre observations were carried out in ALMA Bands 3 and 7 two days after the burst" (2.4 ALMA observations)
- frequencies and spectral setup: Band 3: two 1.875 GHz low-res windows at ~106 and ~108 GHz plus three 468.75 MHz high-res windows at 93.5, 96.4, 96.8 GHz; Band 7: four 1.875 GHz windows at 337.5, 339.4, 347.5, 349.5 GHz  
  > "In Band 7, the correlator was set up in four low-resolution (15.6 MHz) 1.875 GHz windows centred at 337.5, 339.4, 347.5, and 349.5 GHz." (2.4 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 18 m to 1.2 km; 38 array elements  
  > "The configuration used 38 array elements with baselines ranging from 18 m to 1.2 km" (2.4 ALMA observations)
- angular resolution: 0.77"x0.63" (Band 3), 0.24"x0.17" (Band 7), natural weighting  
  > "The resolution achieved using natural weighting was" (2.4 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 51 min (Band 3, PWV 1.0 mm); 38 min (Band 7, PWV 0.74 mm)  
  > "Integration time on source was 51 minutes (with PWV 1.0 mm) and 38 minutes (with PWV 0.74 mm), respectively." (2.4 ALMA observations)
- observing dates: 25-26 October 2016  
  > "from 25 October 2016 23:03:11.0 to 26 October 2016 00:22:33.3 UT" (2.4 ALMA observations)
- pi or archival as stated: _not stated_
- Line: CO J=2-3 (as labelled) (not stated (observed 93.2316 GHz))
- Line: HCO+ 3-4 (as labelled) (not stated (observed 96.1807 GHz))
- Other facility **VLT/X-shooter**: UV-NIR spectrum (3000-24800 A) used for abundances, depletion, fine-structure and H2/CO limits  
  > "The observation consisted of $2\times600$ s exposures covering the spectral range between 3000 and 24800 Å." (2.3 X-shooter spectroscopy)
- Other facility **Swift/XRT**: X-ray afterglow for SED  
  > "which detected an X-ray counterpart starting 34.8 ks after the trigger" (2.1 High-energy observations)
- Other facility **Spitzer/IRAC, FORS2, GROND, Watcher, TAROT etc.**: Optical/IR photometry for light curve and host limits  
  > "In this paper we present the observations performed with the 0.4 m Watcher telescope" (2.2 Optical and infrared photometry)
- External data: Konus-Wind fluence and peak energy  
  > "The burst had a fluence of $(4.2 \pm 0.6)\times10^{-5}$ erg cm$^{-2}$ in the 20 keV - 10 MeV observer-frame energy range" (2.1 High-energy observations) [from (cite: fre16)]
- External data: Depletion coefficients A2, B2  
  > "the coefficients for each element, A$_2$ and B$_2$ are given in (cite: dec16)" (3.3.4 Dust depletion) [from (cite: dec16)]

## Processing

### Calibration

- pipeline or manual: Archive-provided calibration script  
  > "using the calibration script provided in the ALMA archive" (2.4 ALMA observations)
- casa version: CASA 4.7  
  > "version 4.7, (cite: mcm07)" (2.4 ALMA observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1924-2914 (Band 3), J2056-4714 (Band 7)  
  > "The flux calibration was based on observations of the quasars J1924-2914 and J2056-4714 for Bands 3 and 7, respectively." (2.4 ALMA observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The resolution achieved using natural weighting was" (2.4 ALMA observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Cubes at original resolution for low-res windows; high-res windows binned to 12 MHz  
  > "binned to 12 MHz for the high-resolution windows" (2.4 ALMA observations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Molecular column density limit formalism and integral approximation  
  > "In our case we can get a limit on the value of the integral by using Eq. (5) from (cite: wik97)" (3.3.5 ALMA limits) [from (cite: wik95; wik97)]
- X-shooter H2/CO search method  
  > "We use the method developed in Bolmer et al. (in prep.)" (3.3.6) [from Bolmer et al. (in prep.)]
- Photo-excitation code for distance  
  > "The photo-excitation code is that used by (cite: vre07) and (cite: del09)" (3.3.7) [from (cite: vre07), (cite: del09)]

### Not stated but needed to reproduce (our reading)

- tclean parameters (cell, image size, masking, deconvolver) not given
- Spectral rms and line width used to derive the 3.9 km/s optical-depth limit
- How continuum was normalised for optical depth
- Flux scale uncertainty
- Line-free channels and continuum handling
- Velocity width Delta V assumed for CO/HCO+ lines

## Analysis recipe

1. **Calibrate and image ALMA data, measure afterglow fluxes**: Archive calibration script in CASA 4.7; images per spectral window; fluxes in Table 1  
  > "subsequently images were produced by using the combined emission in each spectral window" (2.4 ALMA observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive CO and HCO+ column density upper limits from ALMA non-detections**: LTE absorption column density formula with integral of tau = 3 sigma_tau sqrt(DeltaV deltaV)  
  > "$$\begin{equation}
\int\tau_{\nu}dV\simeq3\sigma_{\tau}\sqrt{\Delta V \delta V},
\end{equation}$$" (3.3.5 ALMA limits)
   - parameter: delta v = 13 km/s; integral limit 3.9 km/s  
  > "Assuming a $\delta v=13$ km s$^{-1}$" (3.3.5 ALMA limits)
   - assumption: Tx lower limit = CMB temperature 10.1 K (also 20 and 30 K tried)  
  > "$T_x=2.725(1+z)=10.1$ K" (3.3.5 ALMA limits)
   - fitting: _not stated_
   - validation: Compared with X-shooter H2 and CO limits  
  > "which are consistent with those that we obtain from the optical spectra" (abstract)
3. **Voigt-fit host absorption lines and derive metallicity**: Voigt profile fits of X-shooter lines  
  > "We fit the absorption lines of the host complex with Voigt profiles using the FITLYMAN environment in Midas" (3.3.3)
   - software: FITLYMAN/MIDAS
   - fitting: _not stated_
   - validation: Agreement with Heintz et al. 2018  
  > "are in good agreement with (cite: hei18) who used the same data set but a different Voigt-profile fitting code" (3.3.3)
4. **Limits on H2 and CO from X-shooter**: MCMC fitting of Lyman-Werner bands and CO bandheads  
  > "We use the `PyMC` Markov Chain Monte Carlo (MCMC) python package" (3.3.6)
   - software: PyMC
   - parameter: b = 2.0 km/s; H2 J=0-5, CO J=0-6  
  > "when assuming $b=2.0$ km $s^{-1}$" (3.3.6)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7: ALMA calibration and imaging  
  > "The data were calibrated with CASA (Common Astronomy Software Applications, version 4.7, (cite: mcm07))" (2.4 ALMA observations)
- **FITLYMAN (MIDAS)** : Voigt profile fitting  
  > "using the FITLYMAN environment in Midas (cite: fon95)" (3.3.3)
- **PyMC** : MCMC fit of H2 and CO absorption  
  > "We use the `PyMC` Markov Chain Monte Carlo (MCMC) python package" (3.3.6)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| log N(CO) upper limit from ALMA (Tx=10.1 K) | <15.7 | not stated | log cm^-2 | 2 | $log(N_{CO}/cm^{-2})<15.7$ and $log(N_{HCO+}/cm^{-2})<13.2$ |
| log N(HCO+) upper limit from ALMA | <13.2 | not stated | log cm^-2 | 2 | $log(N_{CO}/cm^{-2})<15.7$ and $log(N_{HCO+}/cm^{-2})<13.2$ |
| [Zn/H] | -1.11 | 0.07 | dex | 3 | \[Zn/H\] $=-1.11\pm0.07$ |
| log N(H2) limit | <15.2 | 3 sigma | log cm^-2 | 4 | $N_{\mathrm{J0-5}}(\mathrm{H_2}) < 10^{15.2}\,\mathrm{cm}^{-2}\,(3\sigma)$ |
| Band 3 spectral slope | +0.39 | 0.13 | dimensionless | 1 | $\beta_{Band3} = +0.39\pm0.13$ |
| GRB-absorber distances | d_I=990, d_II=820, d_IV=700 | 60, 90, 140 | pc | 0 | $d_I=990 \pm 60$ pc, $d_{II} = 820\pm 90$ pc, and $d_{IV}=700\pm 140$ pc |

## Qualitative findings

- No molecular absorption detected in ALMA data; mm spectroscopy of GRBs is feasible, best for dusty, high-metallicity sight lines  
  > "we show that GRB millimetre spectroscopy is now feasible" (abstract)

## Claim tuples

- H: Can ALMA detect molecular absorption in a GRB host? | E: ALMA Band 3 spectroscopy of CO and HCO+ absorption | R: No detection; log N(CO)<15.7, log N(HCO+)<13.2 | F: Host is nearly dust-free with low molecular content; limits consistent with UV limits | **supported**
- H: What is the host metallicity? | E: Voigt fits and depletion correction | R: [Zn/H]=-1.11+-0.07; corrected [X/H]=-0.94+-0.08 | F: Average metallicity for a GRB host at this redshift | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Caveat (inferred, ours): ALMA limits depend on assumed Tx, width and b values and a rough rms
- Caveat (inferred, ours): ALMA imaging details are sparse

## Reproducibility

- Data public (paper): ALMA data listed with project code; X-shooter via GRBSpec  
  > "This data set is available through the GRBSpec database" (2.3 X-shooter spectroscopy)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: spectral rms used for limits
- Data volume (inferred): ~10-50 GB for ALMA raw data
- Score (inferred): 3/5, ALMA part is a simple limit calculation with limited details; rest uses other facilities.
- Rediscovery candidate: no, ALMA recipe incomplete and results mostly non-ALMA.

## Links

- Method: (cite: wik97) (column density limit formalism)
- Method: (cite: dec16) (depletion patterns)
- Companion: (cite: hei18) (same X-shooter data, high-ionisation lines)

## Checks

```json
{
 "quotes": 52,
 "quotes_ok": 52,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 37,
  "rate": 0.529
 },
 "evidence_ok": true
}
```

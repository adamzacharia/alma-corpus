# ALMA Observations of Dust Polarization and Molecular Line Emission from the Class 0 Protostellar Source Serpens SMM1

`2017ApJ...847...92H` | The Astrophysical Journal 2017 | first author: Hull, Charles L. H. | arXiv: 1707.03827 | DOI: 10.3847/1538-4357/aa7fe9

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: How does the magnetic field in the Class 0 protostar Serpens SMM1 change with spatial scale, and do the outflow and jet shape it?  
  > "we can compare the magnetic field orientations at different spatial scales." (abstract)
- Target **Serpens SMM1**: coordinates SMM1-a: 18:29:49.81 +1:15:20.41 (J2000)  
  > "located at a distance of 436 $\pm$ 9 pc (cite: OrtizLeon2017b)" (Introduction); "| SMM1-a | 18:29:49.81 | +1:15:20.41 | 800 |" (Table 1); z/distance 436 ± 9 pc  
  > "located at a distance of 436 $\pm$ 9 pc (cite: OrtizLeon2017b)" (Introduction); "| SMM1-a | 18:29:49.81 | +1:15:20.41 | 800 |" (Table 1); distance from Ortiz-León et al. 2017 (cite: OrtizLeon2017b)  
  > "located at a distance of 436 $\pm$ 9 pc (cite: OrtizLeon2017b)" (Introduction); "| SMM1-a | 18:29:49.81 | +1:15:20.41 | 800 |" (Table 1)

## Data provenance

- ALMA projects: 2013.1.00726.S, 2015.1.00354.S
- bands: Band 7 (870 um) polarization; Band 6 (1.3 mm) lines and continuum  
  > "We also present 1.3 mm (Band 6) ALMA spectral line data" (Observations)
- frequencies and spectral setup: 8 GHz wide-band continuum, ~336–350 GHz, mean 343.479 GHz  
  > "8 GHz of wide-band dust continuum ranging in frequency from $\sim$ 336–350 GHz, with a mean frequency of 343.479 GHz" (2.1 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.33'' (~140 AU) for 870 um polarization  
  > "have a synthesized beam (resolution element) of $\sim$ $0.33\ensuremath{''}$, corresponding to a linear resolution of $\sim$ 140 AU" (2.1 ALMA observations)
- max recoverable scale: ~5''  
  > "The largest recoverable scale in the data is approximately 5$\ensuremath{''}$." (2.1 ALMA observations)
- sensitivity: sigma_I = 0.5 mJy/beam; sigma_Q≈sigma_U≈sigma_P = 0.06 mJy/beam  
  > "The rms noise level in the final Stokes $I$ dust map is $\sigma_I = 0.5$ mJy beam$^{-1}$" (2.1 ALMA observations)
- time on source: _not stated_
- observing dates: Pol: 2015 Jun 3 and 7; Band 6 lines: 2014 Aug 18, 2015 Apr 06; Band 6 continuum: 2016 Sep 10, Sep 13, Oct 31  
  > "were taken on 2015 June 3 and 2015 June 7" (2.1 ALMA observations)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (not stated)
- Line: SiO J=5-4 (not stated)
- Line: DCO+ J=3-2 (not stated)
- Other facility **SMA**: New 345 GHz dust polarization observations and line data  
  > "new Submillimeter Array (SMA; (cite: Ho2004)) 345 GHz dust polarization observations" (Introduction)
- Other facility **CARMA**: Archival 1.3 mm polarization (TADPOL)  
  > "taken between 2011 and 2013 as part of the TADPOL survey" (2.3)
- Other facility **JCMT**: Archival 850 um SCUBA polarization  
  > "The archival JCMT SCUBA polarization data (Figure [1](#fig:pol)(a)) were obtained from supplementary data provided by (cite: Matthews2009)." (2.3)
- External data: JCMT polarization map reduction  
  > "(cite: Matthews2009) performed a fresh reduction of the original (cite: Davis2000) data" (2.3) [from Matthews2009; Davis2000]
- External data: CARMA polarization data  
  > "The image of the CARMA data in Figure [1](#fig:pol) is an improved version of Figure 27 in (cite: Hull2014)" (2.3) [from Hull2014]
- External data: Dust opacity 2 cm2/g  
  > "an opacity $\kappa_{\nu}=2\,\mathrm{cm}^2/\mathrm{g}$ (cite: Ossenkopf1994)" (4.3.1) [from Ossenkopf1994]
- External data: Dust temperature ~20 K from Herschel SED map (private communication)  
  > "is based on an estimate provided by Katherine Lee (2015, private communication)" (Footnote 6) [from Lee private comm.; Storm2016]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan  
  > "Titan was selected as the flux calibrator." (2.1 ALMA observations)
- flux scale uncertainty: ~10% in Band 6 and 7  
  > "The ALMA flux accuracy in Band 6 (1.3 mm) and Band 7 (870 $\mu$m) is $\sim$ 10%" (2.1 ALMA observations)
- self calibration: four rounds of phase-only self-calibration using Stokes I model  
  > "The image was improved iteratively by four rounds of phase-only self-calibration using the total intensity (Stokes $I$) image as a model." (2.1 ALMA observations)

### Imaging

- task: CASA CLEAN; Stokes I, Q, U cleaned independently  
  > "The Stokes $I$, $Q$, and $U$ maps (where the $Q$ and $U$ maps show the polarized emission) were each **CLEANed** independently" (2.1 ALMA observations)
- deconvolver: _not stated_
- weighting robust: robust = 1  
  > "with a Briggs weighting parameter of robust = 1" (2.1 ALMA observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: ALMA tapered and smoothed to CARMA resolution for comparison  
  > "the ALMA data are tapered and smoothed to produce a map with the same resolution" (4.4)
- final beam: 0.35'' x 0.32''  
  > "| ALMA | 870 $\ensuremath{\mu}m$ | $0.35\ensuremath{''}\times0.32\ensuremath{''}$ | 5.2 | 0.80 | 0.5 |" (Table 2)
- final rms: _not stated_

### Inherited from earlier work

- Polarization debiasing  
  > "We thus debias the polarized intensity map as described in (cite: Vaillancourt2006) and (cite: Hull2015b)." (2.1 ALMA observations) [from Vaillancourt2006; Hull2015b]
- ALMA polarization system details  
  > "For a detailed discussion of the ALMA polarization system, see (cite: Nagai2016)." (2.1 ALMA observations) [from Nagai2016]
- Magnetic field strength procedure  
  > "Our calculations for the magnetic field strength follow the procedure outlined in (cite: Houde2016)." (4.3.2) [from Houde2016]
- Outflow energetics method  
  > "Following the methods outlined in (cite: Zhang2001; Zhang2005)" (4.3.3) [from Zhang2001; Zhang2005]
- CARMA reduction  
  > "for descriptions of the observational setup and the data reduction procedure, see Section 3 of (cite: Hull2014)" (2.3) [from Hull2014]
- 1.3 mm 0.1'' continuum data  
  > "we present 1.3 mm ALMA continuum data with $\sim$ $0.1\ensuremath{''}$ resolution (Pokhrel et al., in prep.)" (2.1 ALMA observations) [from Pokhrel et al., in prep.]

### Not stated but needed to reproduce (our reading)

- CASA version and whether the pipeline or manual calibration was used
- Clean masks, threshold, cell and image size
- Imaging parameters for the Band 6 line cubes (channel width, robust, continuum subtraction)
- Polarization leakage calibration details for ALMA
- Debiasing and S/N cutoffs for the vectors
- Velocity ranges used for the CO and SiO moment maps
- Which execution blocks belong to which project code
- Data and weighting for the DCF angular dispersion analysis
- Outflow velocity integration limits

## Analysis recipe

1. **Image Stokes I, Q, U**: CLEAN with robust=1, 4 rounds phase-only self-cal  
  > "The image was improved iteratively by four rounds of phase-only self-calibration using the total intensity (Stokes $I$) image as a model." (2.1 ALMA observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive polarization maps**: P=sqrt(Q^2+U^2), P_frac=P/I, chi=0.5 arctan(U/Q); debias P  
  > "We thus debias the polarized intensity map as described in (cite: Vaillancourt2006) and (cite: Hull2015b)." (2.1 ALMA observations)
   - assumption: B perpendicular to polarization orientation  
  > "the magnetic field orientations are perpendicular to the polarization orientations" (4.5)
   - fitting: _not stated_
   - validation: Compared with SMA, CARMA, JCMT maps  
  > "The magnetic field derived from the SMA and CARMA data are consistent toward the peak of SMM1." (Results, Total-intensity and polarized dust emission)
3. **Dust mass and gravitational energy**: M_gas = S d^2/(kappa B_nu(T)) in three regions  
  > "We assume dust temperatures $T_d \sim 50$ K for the dust near SMM1-a and b, and $T_d \sim 20$ K for the remainder of the dust." (4.3.1)
   - parameter: d=436 pc, kappa=2 cm2/g, radius 1700 AU  
  > "Using a distance $d=436$ pc and an opacity $\kappa_{\nu}=2\,\mathrm{cm}^2/\mathrm{g}$" (4.3.1)
   - assumption: gas-to-dust ratio 100; optically thin  
  > "assuming a gas-to-dust ratio of 100" (4.3.1)
   - fitting: _not stated_
   - validation: _not stated_
4. **Magnetic field strength and energy**: Angular dispersion function with DCF equation  
  > "we calculate the dispersion in polarization angles from the ALMA polarization map using the function $1-\left\langle \cos\left[\Delta\Phi\left(\ell\right)\right]\right\rangle$" (4.3.2)
   - parameter: sigma(v)~0.8 km/s from unpublished 13CS ALMA data  
  > "one-dimensional turbulent velocity dispersion $\sigma\left(v\right)\sim 0.8 \:\mathrm{km}\:\mathrm{s}^{-1}$" (4.3.2)
   - fitting: _not stated_
   - validation: _not stated_
5. **Outflow energy and energy comparison**: Redshifted CO outflow mass/momentum/energy from ALMA and CARMA; adopt CARMA value; scale by 1/7 volume  
  > "Thus, for the purposes of this energetics analysis, we adopt the CARMA value of $E_\textrm{out} = 1.53\,M_\odot$ (km s$^{-1}$)$^2$" (4.3.3)
   - assumption: d=436 pc, T=20 K, optically thin, no inclination correction  
  > "We assume a distance of 436 pc, a temperature of 20 K, and optically thin emission." (4.3.3)
   - fitting: _not stated_
   - validation: CARMA values comparable to JCMT results of Davis et al. 1999  
  > "the values calculated from the CARMA data are comparable to the results obtained by (cite: Davis1999), who used JCMT (single-dish) data to measure the energetics" (Discussion, Outflow energy)

## Software

- **CASA** : CLEAN imaging and self-calibration  
  > "was produced by using the CASA task **CLEAN** with a Briggs weighting parameter of robust = 1" (2.1 ALMA observations)
- **MIR** : SMA data reduction  
  > "The data were reduced using the software packages **MIR**" (2.2 SMA observations)
- **MIRIAD** : SMA data reduction  
  > "and **MIRIAD** (cite: Sault1995)" (2.2 SMA observations)
- **APLpy** : Plotting  
  > "This research made use of APLpy, an open-source plotting package for Python" (Acknowledgments)
- **GILDAS (GREG)** : Appendix figure  
  > "The figure in the Appendix was created using the GREG package from the GILDAS data reduction package" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Stokes I rms | 0.5 | not stated | mJy/beam | 1 | $\sigma_I = 0.5$ mJy beam$^{-1}$ |
| Stokes Q/U rms | 0.06 | not stated | mJy/beam | 1 | $\sigma_Q \approx \sigma_U \approx \sigma_P = 0.06$ mJy beam$^{-1}$ |
| Total gas mass | 3.8 | not stated | Msun | 3 | we obtain a combined gas mass in all three regions of $M_{\mathrm{gas}}\approx3.8\,M_\ensuremath{\odot}$ |
| Gravitational energy | 4.8e44 | not stated | erg | 3 | $E_\textrm{grav} \sim$ $4.8 \times 10^{44}$ erg |
| Plane-of-sky B strength | 5.7 | not stated | mG | 4 | to calculate a magnetic field strength of $\sim 5.7$ mG (plane-of-the-sky component) |
| Magnetic energy | 9e43 | not stated | erg | 4 | $E_B \sim$ $9 \times 10^{43}$ erg |
| Outflow energy (CARMA) | 1.53 | not stated | Msun (km/s)^2 | 5 | energy $E_\textrm{out} = 1.53\,M_\odot$ (km s$^{-1}$)$^2$ |
| SMM1-b binary separation | ~130 | not stated | AU | 0 | SMM1-b is a binary with a separation of $\sim$ $0.3\ensuremath{''}$ ($\sim$ 130 AU) |

## Qualitative findings

- Field changes from E-W at 0.1 pc scales to complex at envelope scales  
  > "We find major changes in the magnetic field orientation between large ($\sim$ 0.1 pc) scales" (abstract)

## Claim tuples

- H: The low-velocity outflow shapes the field in SMM1 | E: Compare ALMA polarization with CO(2-1) maps | R: Field follows edges of redshifted cavity SE of SMM1-a | F: Outflow shapes field there | **supported**
- H: The EHV jets shape the field | E: Compare CO and SiO jets with field | R: No obvious relationship | F: Jets don't visibly shape the field | **supported**
- H: Gravity, field, and outflow energies are comparable | E: Energetics estimates | R: Within factor of few | F: No dominant effect can be claimed | **partially**
- H: SMM1-b is a binary driving SiO jet | E: 0.1'' 1.3 mm continuum plus SiO | R: ~130 AU binary; eastern member drives jet | F: Protobinary | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Dust self-scattering for central azimuthal pattern: data cannot discriminate; judged unlikely at >=100 AU  
  > "our current data do not allow us to resolve the disk sufficiently well to differentiate between the two scenarios described above." (4.5)
- How they decided it was enough: _not stated_
- Limitation (authors): Large uncertainties in energetics inputs  
  > "There is substantial uncertainty in several of the parameters that go into the above estimates" (4.3.4)
- Caveat (inferred, ours): Energetics use uncertain temperatures, opacity and 13CS linewidth
- Caveat (inferred, ours): DCF with a single dispersion estimate
- Caveat (inferred, ours): Self-scattering not excluded
- Caveat (inferred, ours): No uncertainties on derived energies

## Reproducibility

- Data public (paper): ALMA projects cited; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00726.S and ADS/JAO.ALMA#2015.1.00354.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and detailed imaging parameters
- Missing: Self-calibration solution intervals
- Missing: Unpublished 13CS data
- Missing: Pokhrel et al. 0.1'' data
- Missing: Private-communication dust temperature
- Data volume (inferred): tens to hundreds of GB
- Score (inferred): 4/5, Imaging basics given but many parameters missing; polarization table is provided online.
- Rediscovery candidate: no, Recipe incomplete and key inputs unpublished.

## Links

- Method: Nagai2016 (ALMA polarization system)
- Method: Houde2016 (Magnetic field strength procedure)
- Method: Vaillancourt2006 (Polarization debiasing)
- Companion: Hull2016a (Earlier ALMA EHV jet study of SMM1)
- Companion: Hull2017a (Ser-emb 8 ALMA polarization)
- Companion: Hull2014 (TADPOL CARMA survey)
- Related: TADPOL

## Checks

```json
{
 "quotes": 72,
 "quotes_ok": 72,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 84,
  "stated": 51,
  "rate": 0.607
 },
 "evidence_ok": true
}
```

# Quenching by gas compression and consumption. A case study of a massive radio galaxy at z = 2.57

`2019A&A...624A..81M` | Astronomy and Astrophysics 2019 | first author: Man, Allison W. S. | arXiv: 1902.08622 | DOI: 10.1051/0004-6361/201834542

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: What do the recent star-formation history (X-SHOOTER UV spectrum) and cold molecular gas ([CI] from ALMA) of the radio galaxy PKS 0529-549 at z=2.57 say about quenching and AGN feedback?  
  > "Here we present the most significant detection of multiple rest-frame UV photospheric absorption lines in , a radio galaxy at $z=2.57$." (Introduction)
- Target **PKS 0529-549**: coordinates RA 5h30m25.565s, Dec -54d54'22.624" (X-SHOOTER slit centroid)  
  > "Systemic redshift, $z_{\mathrm{sys}}$ | $2.5725\pm0.0003$" (Table 1); "RA | $5^{h}30^{m}25^{s}.565$" (Table 1); z/distance z_sys = 2.5725 ± 0.0003  
  > "Systemic redshift, $z_{\mathrm{sys}}$ | $2.5725\pm0.0003$" (Table 1); "RA | $5^{h}30^{m}25^{s}.565$" (Table 1); distance from broad He II emission line in X-SHOOTER spectrum  
  > "Systemic redshift, $z_{\mathrm{sys}}$ | $2.5725\pm0.0003$" (Table 1); "RA | $5^{h}30^{m}25^{s}.565$" (Table 1)

## Data provenance

- ALMA projects: 2013.1.00521.S
- bands: Band 6  
  > "The Band 6 observations were conducted on 2014 September 2 with 34 antennas" (2.3 ALMA Band 6 observations and reduction)
- frequencies and spectral setup: four 1.875 GHz spectral windows, one tuned to [CI] 2-1  
  > "We used four 1.875 GHz spectral windows, one of which was tuned to observe the \[C i\] $^3$P$_{2}$-$^3$P$_{1}$ (hereafter \[C i\]) line in PKS 0529-549." (2.3 ALMA Band 6 observations and reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.43 x 0.28 arcsec, PA 65 deg  
  > "The restoring beam used was $0\ensuremath{''}.43 \times 0\ensuremath{''}.28$ at position angle of $65^{\circ}$." (2.3 ALMA Band 6 observations and reduction)
- max recoverable scale: _not stated_
- sensitivity: 48 uJy continuum; 0.5 mJy per 50 km/s channel  
  > "The root-mean-square (rms) noise was 48 $\mu$Jy in the continuum image, and 0.5 mJy at channel width of 50 km s$^{-1}$" (2.3 ALMA Band 6 observations and reduction)
- time on source: 5 minutes  
  > "with a total on-source integration time of 5 minutes" (2.3 ALMA Band 6 observations and reduction)
- observing dates: 2014 September 2  
  > "The Band 6 observations were conducted on 2014 September 2 with 34 antennas" (2.3 ALMA Band 6 observations and reduction)
- pi or archival as stated: Cycle 2 programme, PI C. De Breuck  
  > "PKS 0529-549 was observed with ALMA through the Cycle 2 programme 2013.1.00521.S (PI: C. De Breuck)." (2.3 ALMA Band 6 observations and reduction)
- Line: [CI] 3P2-3P1 (2-1) (809.34197 GHz)
- Other facility **VLT/X-SHOOTER**: Deep rest-frame UV-optical spectrum (8.5 h) for systemic redshift, photospheric/wind lines, star-formation history  
  > "The total on-source exposure time was 8.5 hours." (2.1 VLT/X-SHOOTER observations)
- External data: SFR = 1020 (+190/-170) Msun/yr, L_IR and AGN/SF luminosities  
  > "a star-formation rate of SFR $=1020^{+190}_{-170}$ M$_{\ensuremath{\odot}}$ yr$^{-1}$ (cite: Falkendal2018)" (Introduction) [from (cite: Falkendal2018)]
- External data: ALMA Band 6 continuum flux of host (1.33±0.16 mJy)  
  > "The ALMA Band 6 continuum of the host galaxy is $(1.33\pm0.16)$ mJy (cite: Falkendal2018)" (4 Result II) [from (cite: Falkendal2018)]
- External data: Stellar mass (3±2)e11 Msun  
  > "M$_{\star}$ = $(3\pm2)\times10^{11}$ M$_{\odot}$, (cite: dBreuck2010)" (Introduction) [from (cite: dBreuck2010)]
- External data: [CI] disk dynamical model, rotation velocity and deconvolved radius  
  > "We have already presented a detailed dynamical model of the \[C i\] (2–1) emission in (cite: Lelli2018)." (4 Result II) [from (cite: Lelli2018)]
- Simulation/model as data: Starburst99 v7.0.1 model spectra (instantaneous burst 1e6 Msun; continuous 1 Msun/yr), Geneva tracks, Kroupa IMF, Z=0.014  
  > "The star-formation histories used to generate the model spectra probe two extreme cases: (1) an instantaneous burst creating a stellar population with an initial mass of 10$^{6}$ M$_{\odot}$" (3.5.1)

## Processing

### Calibration

- pipeline or manual: Supplied calibration script in CASA  
  > "The data were calibrated in the Common Astronomy Software Application (cite: McMullin2007) with the supplied calibration script." (2.3 ALMA Band 6 observations and reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "To maximize S/N we used natural weighting and a coarse channel width of 50 km s$^{-1}$ in the barycentric velocity frame." (2.3 ALMA Band 6 observations and reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum-subtracted moment-0 map used to define aperture  
  > "The extraction aperture was defined using the continuum-subtracted moment-0 map around the \[C i\] (2–1) line." (4 Result II)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.43 x 0.28 arcsec, PA 65 deg  
  > "The restoring beam used was $0\ensuremath{''}.43 \times 0\ensuremath{''}.28$ at position angle of $65^{\circ}$." (2.3 ALMA Band 6 observations and reduction)
- final rms: 48 uJy continuum; 0.5 mJy/channel (50 km/s)  
  > "The root-mean-square (rms) noise was 48 $\mu$Jy in the continuum image" (2.3 ALMA Band 6 observations and reduction)

### Inherited from earlier work

- Full ALMA calibration details  
  > "Full details about the calibration of the ALMA observations are provided in (cite: Falkendal2018) and (cite: Lelli2018)." (2.3 ALMA Band 6 observations and reduction) [from (cite: Falkendal2018); (cite: Lelli2018)]
- [CI] mass derived following Papadopoulos et al. approach  
  > "following the approach derived in (cite: Papadopoulos2004a)" (4 Result II) [from (cite: Papadopoulos2004a)]
- X_[CI] = 3e-5 following M82 value  
  > "we adopt an \[C i\]-to-H$_{2}$ abundance, $X_{\mathrm{[C\,{\textsc{i}}]}}$ = 3$\times$10$^{-5}$ following the value derived for M82 (cite: Weiss2003)" (4 Result II) [from (cite: Weiss2003)]

### Not stated but needed to reproduce (our reading)

- CASA version used
- Channel/spectral-window line-free ranges for continuum
- Exact formula and constants used to convert [CI] flux to M_H2
- SFR used in SFE (taken from Falkendal+2018) and its derivation
- How Gaussian-fit uncertainties were propagated into M_H2 and f_gas
- Deconvolved [CI] disk radius value (from Lelli+2018)

## Analysis recipe

1. **extract [CI] spectrum**: Spectrum extracted with elliptical aperture on continuum-subtracted moment-0 map  
  > "extracted using an elliptical aperture centered at $05^{h}30^{m}25^{s}.438 -54^{\circ}54'23''.135$, with major and minor axes corresponding to $0\ensuremath{''}.64\times0\ensuremath{''}.43$ at a position angle of 20$^{\circ}$." (4 Result II)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **measure [CI] line flux**: Fit 1D spectrum with two Gaussians plus flat continuum  
  > "we fit the extracted 1D spectrum with two Gaussian components and a continuum as shown in Figure [6]" (4 Result II)
   - parameter: continuum 1.33±0.16 mJy fixed approximately flat  
  > "the continuum can be approximated as a flat, straight line." (4 Result II)
   - fitting: _not stated_
   - validation: _not stated_
3. **derive H2 mass, f_gas, SFE, depletion time**: [CI] luminosity to carbon mass, then H2 mass via X_[CI] and He correction; SFE = SFR/M_H2  
  > "We assume local thermodynamic equilibrium, that the \[C i\] lines are optically thin, and that the excitation factor $Q_{21}$=0.5." (4 Result II)
   - parameter: X_[CI] = 3e-5; helium correction 1.36  
  > "The conversion to molecular mass includes the mass in Helium by a correction factor of 1.36 (cite: Solomon2005)." (4 Result II)
   - assumption: LTE, optically thin, Q21 = 0.5; cosmology H0=70, OmegaM=0.3, OmegaL=0.7; Kroupa IMF  
  > "A cosmology of $H_{0}$ = 70 km s$^{-1}$ Mpc$^{-1}$, $\Omega_\mathrm{M}$ = 0.3 and $\Omega_{\Lambda}$ = 0.7 is adopted." (Introduction)
   - fitting: _not stated_
   - validation: Systematic uncertainty from X_[CI], Q21 estimated at most ~3; compared with CO-derived masses agreeing within 2-3  
  > "H$_{2}$ masses inferred from \[C i\] and CO agree within a factor of 2–3 for dusty star-forming galaxies" (4 Result II)

## Software

- **CASA** : ALMA calibration with supplied script  
  > "The data were calibrated in the Common Astronomy Software Application (cite: McMullin2007) with the supplied calibration script." (2.3 ALMA Band 6 observations and reduction)
- **EsoRex** 2.8.19: X-SHOOTER data reduction  
  > "We used the EsoRex pipeline version 2.8.19 (cite: Modigliani2010) through the Reflex interface" (2.2 X-SHOOTER reduction)
- **Starburst99** v7.0.1: model spectra for star-formation history  
  > "model spectra generated with the `Starburst99` tool v7.0.1" (3.5.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [CI] total velocity-integrated flux | 2.0 | 0.5 | Jy km/s | 2 | we find a total velocity-integrated flux $S\Delta v=(2.0\pm0.5)$ Jy km s$^{-1}$. |
| Total molecular gas mass | 3.9e10 | 1.0e10 | Msun | 3 | total molecular mass of M$_\mathrm{H_2}$ $=(3.9\pm1.0)\times10^{10}$ M$_{\odot}$ |
| Molecular gas fraction | 12 | 7 | % | 3 | is only $(12\pm7)$% |
| Star-formation efficiency | 26 | 8 | Gyr^-1 | 3 | SFE $=(26\pm8)$ Gyr$^{-1}$ |
| Depletion time | 38 | 12 | Myr | 3 | $t_{\mathrm{depl}}$ $\equiv$ SFE$^{-1}$ $=(38\pm12)$ Myr |

## Qualitative findings

- UV spectrum implies at least two bursts in past ~100 Myr (4–7 Myr and ≥20 Myr ago)  
  > "more than one burst of star formation took place in the past $\sim100$ Myr" (Conclusions)

## Claim tuples

- H: Is PKS 0529-549 gas-poor and efficiently forming stars, nearing quenching? | E: Derived M_H2 from ALMA [CI](2-1) and combined with SFR and stellar mass | R: M_H2=3.9e10 Msun, f_gas=12%, SFE=26 Gyr^-1, t_depl=38 Myr | F: Galaxy will soon exhaust its gas and quench | **supported**
- H: Is star formation history bursty? | E: Compared Si II 1485 and S V 1502 depths to Starburst99 models | R: Best-fit burst ages 6 (+1/-2) Myr and ≳20 Myr | F: Multiple recent bursts | **supported**
- H: Is efficient star formation due to gas compression? | E: Compared narrow stellar and [CI] dispersions and Schmidt-Kennicutt position with analytic models | R: Sigma ≤55 km/s; HzRGs lie above S-K relation | F: Compressive flows likely drive efficiency | **partially**

## Reasoning

- Why this data: [CI] chosen as tracer of diffuse low-density H2  
  > "which is a tracer of relatively diffuse low-density H$_{2}$" (Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Q21 cannot be constrained without other lines; X_[CI] systematic uncertainty up to ~3  
  > "none of which we can directly constrain without observations of other lines" (4 Result II)
- Caveat (inferred, ours): Only a single [CI] line with assumed Q21 and X_[CI]; gas mass systematic factor ~2-3
- Caveat (inferred, ours): SFR taken from earlier paper
- Caveat (inferred, ours): Small sample of radio galaxies for conclusions on quenching
- Caveat (inferred, ours): Very short ALMA integration (5 min)

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Exact CASA version and imaging parameters
- Missing: Mass conversion formula details
- Missing: SFR input from Falkendal+2018
- Data volume (inferred): ~ a few GB (single short Band 6 execution)
- Score (inferred): 3/5, ALMA part is simple and archival-like but calibration and imaging details are deferred to companion papers.
- Rediscovery candidate: no, Public-data status not stated in the paper and imaging details are deferred to other papers.

## Links

- Method: (cite: Papadopoulos2004a) ([CI] mass derivation)
- Companion: (cite: Falkendal2018) (ALMA calibration, continuum and SFR)
- Companion: (cite: Lelli2018) ([CI] dynamical model and calibration)

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
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
  "facts": 69,
  "stated": 38,
  "rate": 0.551
 },
 "evidence_ok": true
}
```

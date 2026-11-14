# No Sign of Strong Molecular Gas Outflow in an Infrared-bright Dust-obscured Galaxy with Strong Ionized-gas Outflow

`2017ApJ...851...98T` | The Astrophysical Journal 2017 | first author: Toba, Yoshiki | arXiv: 1711.10091 | DOI: 10.3847/1538-4357/aa9d17

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: Does an IR-bright DOG with a strong ionized-gas ([O III]) outflow also show a strong molecular (CO) gas outflow?  
  > "whether or not there is molecular gas associated with outflows is still unclear." (Introduction)
- Target **WISE J102905.90+050132.4 (WISE1029)**: coordinates RA 10:29:05.90, Dec +05:01:32.42 (J2000, SDSS)  
  > "Decl. (SDSS) \[J2000.0\] | +05:01:32.42" (Table 1); "As a result, WISE1029 at $z_{\rm spec}$ = 0.4930 was discovered." (2.1 Target selection); z/distance z_spec = 0.4930  
  > "Decl. (SDSS) \[J2000.0\] | +05:01:32.42" (Table 1); "As a result, WISE1029 at $z_{\rm spec}$ = 0.4930 was discovered." (2.1 Target selection); distance from Toba et al. 2017c (SDSS spectrum, stellar-component fit)  
  > "Decl. (SDSS) \[J2000.0\] | +05:01:32.42" (Table 1); "As a result, WISE1029 at $z_{\rm spec}$ = 0.4930 was discovered." (2.1 Target selection)

## Data provenance

- ALMA projects: 2015.1.00199.S
- bands: Band 4 (CO 2-1) and Band 7 (CO 4-3)  
  > "The CO(2–1) line was observed in band 4 on 2016 July 14 with the C40-4 configuration, and CO(4–3) in band 7 on 2016 June 22 with the C40-5 configuration." (2.2 ALMA observations)
- frequencies and spectral setup: One SPW on the line with 1875 MHz bandwidth and 1953 kHz resolution; three continuum SPWs of 1875 MHz each  
  > "Three other spectral windows were set to observe the continuum, each with 1875 MHz bandwidth." (2.2 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-4 (band 4), C40-5 (band 7)  
  > "The CO(2–1) line was observed in band 4 on 2016 July 14 with the C40-4 configuration" (2.2 ALMA observations)
- baselines: _not stated_
- angular resolution: 0.74" x 0.68" (PA -42 deg) band 4; 0.60" x 0.36" (PA -62 deg) band 7  
  > "The resulting images have angular resolution of $0^{\prime \prime}.74 \times 0^{\prime \prime}.68$ with position angle of –42 deg. in band 4" (2.2 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2016 July 14 (band 4); 2016 June 22 (band 7)  
  > "CO(4–3) in band 7 on 2016 June 22 with the C40-5 configuration." (2.2 ALMA observations)
- pi or archival as stated: Authors' own Cycle 3 program (PI Y. Toba)  
  > "carried out as a part of our ALMA Cycle 3 program (#2015.1.00199.S PI: Y.Toba)" (2.2 ALMA observations)
- Line: 12CO J=2-1 (not stated)
- Line: 12CO J=4-3 (not stated)
- Other facility **SDSS**: Optical spectrum and target selection  
  > "from the SDSS spectroscopic catalog (cite: Alam) and ALLWISE catalog (cite: Cutri)" (2.1 Target selection)
- Other facility **WISE**: Mid-IR photometry for SED  
  > "and ALLWISE catalog (cite: Cutri)" (2.1 Target selection)
- Other facility **AKARI**: FIR 90 um 3-sigma upper limit for SED fitting  
  > "including 90 $\ensuremath{\mu}m$ data (3$\sigma$ upper limit) obtained from *AKARI* far-IR (FIR) all-sky survey" (3.2 The stellar mass and star formation rate relation)
- External data: [OIII] velocity offset and dispersion, systemic redshift from SDSS spectrum  
  > "Its $v_{\rm [OIII]}$ and $\sigma_{\rm [OIII]}$ are $-1485.0 \pm 207.7$ km s$^{-1}$ and $986.9 \pm 146.6$ km s$^{-1}$, respectively" (2.1 Target selection) [from (cite: Toba_17c)]
- External data: Comparison ULIRG sample on SFR-M* plane  
  > "those of ULIRGs at $0 < z < 0.5$ presented by (cite: Kilerci) are also shown in Figure [4]" (3.2 The stellar mass and star formation rate relation) [from (cite: Kilerci)]
- External data: Local IR galaxy L_FIR-L'CO relation  
  > "The relation for local IR galaxies at $z < 0.1$ reported by (cite: Kamenetzky) is also plotted." (3.3 $L_{\rm FIR}$ and $L^\prime_{\rm CO}$ relation) [from (cite: Kamenetzky)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline  
  > "The data were calibrated with the ALMA pipeline r38377 for band 4, and r36660 for band 7." (2.2 ALMA observations)
- casa version: _not stated_
- pipeline version: r38377 (band 4), r36660 (band 7)  
  > "The data were calibrated with the ALMA pipeline r38377 for band 4, and r36660 for band 7." (2.2 ALMA observations)
- archive products used as is: _not stated_
- flux calibrator: J1058+0133 (flux and bandpass); phase calibrator J1038+0512  
  > "J1058+0133 was used as the primary flux calibrator and the bandpass calibrator, and J1038+0512 as the phase calibrator." (2.2 ALMA observations)
- flux scale uncertainty: 5% band 4, 10% band 7  
  > "Flux uncertainties are consistent with ALMA specifications (5% in band 4 and 10% in band 7)." (2.2 ALMA observations)
- self calibration: _not stated_

### Imaging

- task: CLEAN  
  > "Images were produced by CLEAN with briggs weighting and robust=2 parameter." (2.2 ALMA observations)
- deconvolver: _not stated_
- weighting robust: briggs, robust = 2  
  > "Images were produced by CLEAN with briggs weighting and robust=2 parameter." (2.2 ALMA observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Line-free velocity ranges used  
  > "Continuum subtraction was done using the velocity offset range of -1776 to -556 km s$^{-1}$ and 609 to 1829.63 km $s^{-1}$ for band 4" (2.2 ALMA observations)
- line free channels: Band 4: -1776 to -556 and 609 to 1829.63 km/s; Band 7: -818 to -488 and 596 to 878 km/s  
  > "and -818 to -488 km s$^{-1}$ and 596 to 878 km s$^{-1}$ for band 7." (2.2 ALMA observations)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- SED fitting method with SEABASs  
  > "is described in details in (cite: Toba_17b; Toba_17d)" (3.2 The stellar mass and star formation rate relation) [from (cite: Toba_17b; Toba_17d)]
- Stellar mass offset correction and IMF conversion for literature samples  
  > "We also corrected the stellar mass and SFR in the literature to those assumed Chabrier IMF if needed (cite: Toba_17b)." (3.2 The stellar mass and star formation rate relation) [from (cite: Toba_17b)]

### Not stated but needed to reproduce (our reading)

- Cell size, image size, clean threshold, masks and channel width of the cubes
- Whether robust=2 was used for both bands and the CASA version
- Aperture/fit details for continuum and line flux (2-D Gaussian parameters)
- Broad-component noise rms and spectral binning used for the upper limit
- SED photometry list, templates and priors used in SEABASs
- Rest frequencies used for L'CO and observed frequencies

## Analysis recipe

1. **Image continuum and CO cubes**: Pipeline calibrated data, continuum subtraction in line-free velocity ranges, CLEAN imaging with Briggs weighting  
  > "Images were produced by CLEAN with briggs weighting and robust=2 parameter." (2.2 ALMA observations)
   - software: CLEAN
   - parameter: robust=2  
  > "Images were produced by CLEAN with briggs weighting and robust=2 parameter." (2.2 ALMA observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure line and continuum fluxes and moment maps**: 2-D Gaussian fitting without sigma clipping; moment 0 and 1 maps  
  > "We measured the flux densities of CO lines and continuums based on 2-D Gaussian fitting without adopting any sigma clipping" (3.1 The properties of CO molecular gas)
   - fitting: 2-D Gaussian  
  > "based on 2-D Gaussian fitting without adopting any sigma clipping" (3.1 The properties of CO molecular gas)
   - validation: _not stated_
3. **Fit line profiles for outflow wings**: Single Gaussian fit to spectra in 1" diameter apertures; check for broad wing with FWHM>500 km/s  
  > "We fit each spectrum with a single Gaussian and see if they have broad wing with a full width at half maximum (FWHM) $>$ 500 km s$^{-1}$" (3.1 The properties of CO molecular gas)
   - parameter: 1 arcsec aperture  
  > "measured in 1$\ensuremath{''}$ diameter apertures" (3.1 The properties of CO molecular gas)
   - fitting: Single Gaussian; residuals inspected  
  > "The residual indicates that there are no broad wings in both CO lines." (3.1 The properties of CO molecular gas)
   - validation: Residual shows no broad wings  
  > "The residual indicates that there are no broad wings in both CO lines." (3.1 The properties of CO molecular gas)
4. **SED fitting for M*, L_IR, L_FIR, SFR**: SEABASs SED fitting with 12 photometric points including ALMA continuum; SFR from L_IR(SF)  
  > "The SFR is converted from $L_{\rm IR}$ (SF) using a relation of $\log \,{\rm SFR} = \log \, L_{\rm IR}$ (SF) - 9.966" (3.2 The stellar mass and star formation rate relation)
   - software: SEABASs
   - assumption: Chabrier IMF  
  > "a (cite: Chabrier) initial mass function (IMF) is assumed" (Introduction)
   - fitting: Bayesian SED fit (details in Toba 2017b,d)  
  > "SEd Analysis using BAyesian Statistics" (3.2 The stellar mass and star formation rate relation)
   - validation: _not stated_
5. **Derive CO luminosities, r42, gas and dust masses**: Solomon & Vanden Bout relation for L'CO; M_gas = alpha_CO/r21 * L'CO(2-1); dust mass from SED flux at 850 um  
  > "we adopted $\alpha_{CO} = 0.8$ $M_{\ensuremath{\odot}}$ (K km $s^{-1}$)$^{-1}$ (cite: Downes) and $r_{\rm 21}$ = 0.91 (cite: Papadopoulos)" (3.4 Gas-to-dust mass ratio of WISE1029)
   - assumption: kappa(850um)=0.383 cm2/g, T_dust=40 K  
  > "$\kappa$ (850 $\ensuremath{\mu}m$) = 0.383 cm$^2$ g$^{-1}$ (cite: Draine) and a dust temperature of $T_{\rm dust}$ = 40 K" (3.4 Gas-to-dust mass ratio of WISE1029)
   - assumption: Flat cosmology H0=70, OmegaM=0.3, OmegaL=0.7  
  > "$H_0$ = 70 km s$^{-1}$ Mpc$^{-1}$, $\Omega_M$ = 0.3, and $\Omega_{\Lambda}$ = 0.7" (Introduction)
   - fitting: _not stated_
   - validation: _not stated_
6. **Upper limit on broad CO(2-1) outflow component**: 3-sigma upper limit from spectrum rms assuming unresolved broad component with FWHM 1000 km/s  
  > "FWHM of the broad component is 1000 km s$^{-1}$ that is the typical value for broad CO line of objects with strong molecular gas outflow" (3.4 Gas-to-dust mass ratio of WISE1029)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CLEAN** : Imaging  
  > "Images were produced by CLEAN with briggs weighting and robust=2 parameter." (2.2 ALMA observations)
- **ALMA pipeline** r38377 (band 4), r36660 (band 7): Calibration  
  > "The data were calibrated with the ALMA pipeline r38377 for band 4, and r36660 for band 7." (2.2 ALMA observations)
- **SEABASs** : SED fitting  
  > "This fitting code provides a best-fit SED as a combination of stellar, AGN, and SF component" (3.2 The stellar mass and star formation rate relation)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(2-1) integrated flux | 1.90 | 0.13 | Jy km/s | 2 | $S_{\rm CO (2-1)}$ $\Delta v$ \[Jy km s$^{-1}$\] / 1.90 $\pm$ 0.13 |
| CO(4-3) integrated flux | 4.66 | 0.47 | Jy km/s | 2 | $S_{\rm CO (4-3)}$ $\Delta v$ \[Jy km s$^{-1}$\] / 4.66 $\pm$ 0.47 |
| CO(2-1) FWHM | 336.3 | 32.4 | km/s | 3 | FWHM$_{\rm CO (2-1)}$ \[km s$^{-1}$\] / 336.3 $\pm$ 32.4 |
| CO(4-3) FWHM | 373.1 | 15.1 | km/s | 3 | FWHM$_{\rm CO (4-3)}$ \[km s$^{-1}$\] / 373.1 $\pm$ 15.1 |
| Band 4 continuum (146.6 GHz) | 0.18 | 0.02 | mJy | 2 | Band 4 continuum (146.6 GHz) \[mJy\] / 0.18 $\pm$ 0.02 |
| Band 7 continuum (303.9 GHz) | 0.85 | 0.09 | mJy | 2 | Band 7 continuum (303.9 GHz) \[mJy\] / 0.85 $\pm$ 0.09 |
| log L_IR (8-1000 um) | 12.40 | +0.70/-0.17 | log Lsun | 4 | $\log\,L_{\rm IR}$ (8-1000 $\ensuremath{\mu}m$) \[$L_{\ensuremath{\odot}}$\] / $12.40^{+0.70}_{-0.17}$ |
| AGN fraction of L_IR | about 54% | not stated | percent | 4 | $L_{\rm IR}$(AGN)/$L_{\rm IR}$ is about 54% |
| log M* | 10.8 | +0.02/-0.06 | log Msun | 4 | $\log$ $M_*$ \[$M_{\ensuremath{\odot}}$\] / $10.8^{+0.02}_{-0.06}$ |
| log SFR | 2.11 | +0.64/-0.28 | log Msun/yr | 4 | $\log$ SFR \[$M_{\ensuremath{\odot}}$ yr$^{-1}$\] / $2.11^{+0.64}_{-0.28}$ |
| log L'CO(2-1) | 10.25 | 0.03 | K km/s pc2 | 5 | $\log\,L^{\prime}_{\rm CO (2-1)}$ \[K km s$^{-1}$ pc$^2$\] / $10.25 \pm  0.03$ |
| log L'CO(4-3) | 10.04 | 0.04 | K km/s pc2 | 5 | $\log\,L^{\prime}_{\rm CO (4-3)}$ \[K km s$^{-1}$ pc$^2$\] / $10.04 \pm  0.04$ |
| r42 (luminosity ratio) | 0.61 | 0.07 | dimensionless | 5 | We found that the luminosity ratio of CO(4–3) and CO(2–1) lines ($r_{\rm 42}$) to be 0.61 $\pm$ 0.07. |
| Gas-to-dust ratio | 53 | not stated | dimensionless | 5 | The estimated $M_{\rm gas}$/$M_{\rm dust}$ of WISE1029 is 53 |
| Broad CO(2-1) flux upper limit | <0.02 | 3 sigma | Jy km/s | 6 | We obtained the broad CO (2–1) line flux is $<$ 0.02 Jy km s$^{-1}$ |
| Outflow gas mass upper limit | log M_gas < 8.1 | not stated | log Msun | 6 | its mass is $\log \, (M_{\rm gas}/M_{\ensuremath{\odot}}) <  8.1$ |

## Qualitative findings

- CO lines are well fit by a single narrow Gaussian with no broad wings, and moment 1 maps show velocity gradients.  
  > "Both CO lines are well-fitted by a single Gaussian with a FWHM of $\sim$350 km s$^{-1}$" (3.1 The properties of CO molecular gas)

## Claim tuples

- H: A DOG with strong ionized outflow also hosts a strong molecular outflow. | E: ALMA CO(2-1) and CO(4-3) line profile and moment-1 analysis | R: Single Gaussian FWHM ~350 km/s, no broad wings, velocity gradient | F: No sign of strong molecular gas outflow | **supported**
- H: AGN feedback has altered star formation in WISE1029. | E: SFR-M* comparison with ULIRGs | R: Located on the sequence of typical ULIRGs | F: No evidence of quenched SF | **supported**
- H: Weak molecular outflow cannot be excluded. | E: Upper limit on broad component | R: Limit of ~1/100 of detected gas mass | F: Current data cannot rule out a weak outflow | **partially**

## Reasoning

- Why this data: Extreme v_OIII and sigma_OIII among DOG sample and observable from ALMA  
  > "Since WISE1029 is an extreme case in terms of $v_{\rm [OIII]}$ and $\sigma_{\rm [OIII]}$ among our DOG sample and it is observable from ALMA" (2.1 Target selection)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Peak S/N ~20 makes weak broad components hard to detect; FIR SED poorly constrained.  
  > "We should keep in mind that the current data set still cannot constrain well the FIR SED." (3.2 The stellar mass and star formation rate relation)
- Caveat (inferred, ours): Single object; generalisation is limited
- Caveat (inferred, ours): Robust=2 (natural weighting) and 1 arcsec aperture may hide extended or weak wings
- Caveat (inferred, ours): Gas and dust masses rest on assumed alpha_CO, r21, and T_dust
- Caveat (inferred, ours): L_IR and L_FIR have large uncertainties without rest-frame FIR data

## Reproducibility

- Data public (paper): Project code given and ALMA data acknowledged  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00199.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Cell/image size, clean parameters, CASA version
- Missing: SED photometry and SEABASs configuration
- Missing: Aperture and noise details for upper limit
- Data volume (inferred): ~10-30 GB raw for two small Cycle 3 execution blocks
- Score (inferred): 3/5, Public data and simple analysis, but imaging and SED details are incomplete.
- Rediscovery candidate: yes, Data public, simple numeric results (fluxes, FWHM, r42, luminosities) can be redone, though some settings are missing.

## Links

- Method: (cite: Toba_17b) (SED fitting with SEABASs and mass corrections)
- Method: (cite: Solomon) (L'CO formula)
- Companion: (cite: Toba_17c) (Identification of DOGs with strong [OIII] outflows and systemic redshift)
- Related: SDSS
- Related: WISE
- Related: AKARI

## Checks

```json
{
 "quotes": 74,
 "quotes_ok": 74,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 16,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 48,
  "rate": 0.608
 },
 "evidence_ok": true
}
```

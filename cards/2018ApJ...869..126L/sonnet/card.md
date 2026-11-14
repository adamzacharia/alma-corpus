# Forming Super Star Clusters in the Central Starburst of NGC 253

`2018ApJ...869..126L` | The Astrophysical Journal 2018 | first author: Leroy, Adam K. | arXiv: 1804.02083 | DOI: 10.3847/1538-4357/aaecd1

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation
- Question: Are the compact 350 GHz dust peaks in the NGC 253 nuclear starburst forming super star clusters, and what are their masses, timescales and feedback state?  
  > "Our observations reveal $\sim 14$ bright, compact ($\sim 2{-}3$ pc FWHM) knots of dust emission." (abstract)
- Target **NGC 253 nuclear starburst**: coordinates peaks near RA 11.887 deg, Dec -25.288 deg (Table 1)  
  > "FWHM size assumes a distance of $3.5$ Mpc" (Table 1); z/distance 3.5 Mpc  
  > "FWHM size assumes a distance of $3.5$ Mpc" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00274.S
- bands: ~350 GHz (~850 um)  
  > "We used ALMA to observe NGC 253 at $\nu \sim 350$ GHz ($\lambda \sim 850\mu$m)" (2 Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12-m main array (two configurations) plus ACA 7-m  
  > "We observed with the main array in both an intermediate configuration and a 2-km extended configuration." (2 Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.11 arcsec (~1.9 pc) continuum; 0.175 arcsec lines  
  > "the final FWHM beam size is $\theta = 0.11\ensuremath{''}$" (2 Observations)
- max recoverable scale: 19 arcsec  
  > "The inclusion of the ACA means that scales out to 19$''$ are recovered." (2 Observations)
- sensitivity: continuum rms 0.2 K (~0.2 mJy/beam); lines 0.4 K per 5 km/s channel  
  > "the typical rms in the cube is $0.4$ K per $5$ km s$^{-1}$ channel" (2 Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Project of P.I. A. Bolatto  
  > "as part of project 2015.1.00274.S (P.I. A. Bolatto)" (2 Observations)
- Line: CS 7-6 (not stated)
- Line: H13CN 4-3 (not stated)
- Line: CO 3-2 (not stated)
- Other facility **VLA 36 GHz**: 36 GHz continuum used for free-free and stellar mass estimates  
  > "We compare the ALMA data to Karl G. Jansky VLA imaging of $\nu = 36$ GHz continuum emission (cite: GORSKI17)." (2 Observations)
- Other facility **HST WFC3**: 1.3 um near-IR continuum  
  > "We also compare to *Hubble* Space Telescope imaging of the near-IR ($\lambda = 1.3\mu$m) continuum." (2 Observations)
- External data: VLA 36 GHz continuum map  
  > "imaging of $\nu = 36$ GHz continuum emission (cite: GORSKI17)" (2 Observations) [from Gorski et al. 2017 (cite: GORSKI17)]
- External data: Total ionizing photon rate Q0=3.2e53 s^-1 of the burst  
  > "(cite: BENDO15) find $Q_0=3.2 \pm 0.2 \times 10^{53}$ s$^{-1}$ for the whole burst." (6.1 Timescales and Relation to the Starburst) [from Bendo et al. 2015 (cite: BENDO15)]
- External data: Total IR luminosity (half assumed in nucleus)  
  > "If 50% of the total infrared luminosity measured by (cite: SANDERS03) arises from the nuclear region" (6.1 Timescales and Relation to the Starburst) [from Sanders et al. 2003 (cite: SANDERS03)]
- Simulation/model as data: Starburst99 ZAMS population (10^6 Msun, Kroupa IMF, max 100 Msun) used to derive Mstar = Q0/4e46  
  > "We arrive at this value by simulating $10^6$ M$_\odot$ single stellar population, with the initial mass function of (cite: KROUPA01)" (4.3.1 Zero Age Main Sequence Stellar Mass)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 5.1.1 (imaging)  
  > "imaged them in version $5.1.1$ of the Common Astronomy Software Application (CASA)" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: Observatory-provided calibrated visibilities used  
  > "We combined the observatory-provided calibrated visibilities for two 12-m configurations and the ALMA Compact Array (ACA) 7-m array" (2 Observations)
- flux calibrator: _not stated_
- flux scale uncertainty: 10% adopted flux uncertainty  
  > "we quote a $10\%$ uncertainty on the overall flux for each source" (4.1 Size, Line Width, and Flux Measurements)
- self calibration: _not stated_

### Imaging

- task: CASA tclean  
  > "imaged them in version $5.1.1$ of the Common Astronomy Software Application (CASA) using CASA’s `tclean` task" (2 Observations)
- deconvolver: _not stated_
- weighting robust: continuum r=-2; lines r=0.5  
  > "we adopted a Briggs robust parameter $r=-2$ (i.e., nearly uniform weighting)" (2 Observations); "used a standard Briggs weighting with robust parameter $r=0.5$" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Convolved to round beams  
  > "we convolved the continuum and line images to convert from an elliptical to a round beam shape" (2 Observations)
- final beam: 0.11 arcsec continuum (from 0.105x0.065); 0.175 arcsec lines  
  > "the beam of the continuum image has major and minor FWHM $0.105\ensuremath{''} \times 0.065\ensuremath{''}$" (2 Observations)
- final rms: 0.2 K continuum; 0.4 K per 5 km/s lines  
  > "The rms noise away from the source in the cleaned, round beam image is $0.2$ K in Rayleigh Jeans brightness temperature units" (2 Observations)

### Inherited from earlier work

- Detailed line imaging deferred to companion paper  
  > "More details of the line imaging appear in N. Krieger et al. (in preparation)." (2 Observations) [from N. Krieger et al. (in preparation)]
- Dust temperature of 130 K based on ammonia warm component  
  > "assuming that the clusters coincide with the warm component seen in ammonia spectroscopy (cite: GORSKI17; MANGUM13)" (4.3.3 Gas Mass From Dust) [from (cite: GORSKI17; MANGUM13)]
- Cluster formation timescale ~8 tau_ff  
  > "The value of $\sim 8~\tau_{\rm ff} \sim 1$ Myr should be viewed as a key assumption motivated by theory (cite: SKINNER2015)." (6.1 Timescales and Relation to the Starburst) [from (cite: SKINNER2015)]

### Not stated but needed to reproduce (our reading)

- tclean parameters: deconvolver, niter, threshold, masks, cell and image size
- Reference frequency and bandwidth used for continuum, and line-free channels
- Observation dates, on-source times, baselines and calibrators
- How the 36 GHz data were convolved/aligned and the HST astrometric alignment
- CPROPS parameters beyond the search kernel and 5 sigma criterion
- Velocity ranges for line fits (picked by eye)
- Distance to NGC 253 source (3.5 Mpc stated without citation)

## Analysis recipe

1. **Image continuum and lines**: Combine 12-m and ACA visibilities, tclean, convolve to round beam  
  > "We combined the observatory-provided calibrated visibilities for two 12-m configurations and the ALMA Compact Array (ACA) 7-m array" (2 Observations)
   - software: CASA
   - parameter: robust -2 continuum, 0.5 lines  
  > "we adopted a Briggs robust parameter $r=-2$ (i.e., nearly uniform weighting)" (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify continuum peaks**: CPROPS local maximum finding with search kernel 2 beams and 5 sigma contrast  
  > "We identify their locations using the local maximum finding routine from CPROPS (cite: ROSOLOWSKY06)." (3.1 Dust Continuum and Gas)
   - software: CPROPS
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure sizes, peak T and flux**: Azimuthally averaged median radial profile in half-beam rings, 3 sigma clipping, Gaussian plus background fit, quadrature beam deconvolution  
  > "In each half-beam thick ring centered on the peak, we calculate the median intensity." (4.1 Size, Line Width, and Flux Measurements)
   - fitting: Gaussian with background term  
  > "Blue lines show a Gaussian fit to these profiles; this fit includes a background term, which is small in all cases." (4.1 Size, Line Width, and Flux Measurements)
   - validation: 2D Gaussian fits agree within 0.3 pc scatter  
  > "The deconvolved FWHM size from the Gaussian fits agree with our measured sizes with a scatter of $\pm 0.3$ pc." (4.1 Size, Line Width, and Flux Measurements)
4. **Measure line widths**: Background-subtracted aperture spectra; Gaussian fits to CS(7-6) and H13CN(4-3); average of two widths  
  > "We take the linear average of the two line widths as the characteristic line width for the source." (4.1 Size, Line Width, and Flux Measurements)
   - fitting: Gaussian, velocity range chosen by eye  
  > "fitting over a velocity range picked by eye to cover the emission line" (4.1 Size, Line Width, and Flux Measurements)
   - validation: Uncertainty = half the difference between two lines  
  > "We adopt one half the difference in the line width derived between the two lines as our uncertainty." (4.1 Size, Line Width, and Flux Measurements)
5. **Free-free fraction and stellar mass**: 36 GHz aperture photometry; f_ff with -0.1 index; Q0 from L36; Mstar=Q0/4e46  
  > "where the first factor reflects the expected $-0.1$ spectral index from optically thin free-free emission" (4.1 Size, Line Width, and Flux Measurements)
   - software: Starburst99
   - assumption: Te = 7000 K, all 36 GHz is free-free, ZAMS population  
  > "Where we have assumed an electron temperature $T_e = 7,000$ K (cite: BENDO15)." (4.3.1 Zero Age Main Sequence Stellar Mass)
   - fitting: _not stated_
   - validation: _not stated_
6. **Gas mass from dust**: Optical depth from I350=(1-exp(-tau))B(Tdust), Sigma_gas=tau/(DGR kappa), times Gaussian area  
  > "We assume a fiducial temperature of $T_{\rm dust} = 130$ K" (4.3.3 Gas Mass From Dust)
   - parameter: kappa = 1.9 cm2/g; DGR 1/100  
  > "We adopt $\kappa = 1.9$ cm$^2$ g$^{-1}$." (4.3.3 Gas Mass From Dust)
   - assumption: Tdust 130 K (60-160 K range), kappa uncertain by factor ~2  
  > "this value is uncertain by a factor of $\sim 2$" (4.3.3 Gas Mass From Dust)
   - fitting: _not stated_
   - validation: Comparison with Scoville16 conversion (30x lower)  
  > "our assumptions yield an $\approx 30$ times lower gas mass than what one would calculate" (4.3.3 Gas Mass From Dust)
7. **Virial mass, densities, escape velocity, radial momentum**: M_VT = 892 l_FWHM sigma_v^2; densities within FWHM; v_esc; p_r/Mstar = sqrt3 sigma_v Mgas/Mstar  
  > "The prefactor here assumes a density profile $\rho \propto r^{-2}$." (4.3.4 Dynamical Masses)
   - assumption: Virial equilibrium; rho ~ r^-2  
  > "This calculation assumes that the line widths are due to self gravity." (4.3.4 Dynamical Masses)
   - fitting: _not stated_
   - validation: Compared virial to gas+stellar masses  
  > "our virial mass estimates tend to exceed our combined star plus gas estimates by a factor of $\sim 2.5$" (4.3.5 Comparison of Mass Estimates)
8. **Timescales and feedback comparison**: Compare Q0, L_TIR and masses to burst totals; free-fall time and 8 tau_ff timescale; compare momentum to SN and wind models  
  > "Assuming the (cite: SKINNER2015) results to scale with the free fall time, this implies a visibility timescale for forming clusters of $\sim 8 \times 10^5$ yr." (6.1 Timescales and Relation to the Starburst)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.1.1: Imaging with tclean  
  > "imaged them in version $5.1.1$ of the Common Astronomy Software Application (CASA)" (2 Observations)
- **CPROPS** : Peak finding in continuum  
  > "We identify their locations using the local maximum finding routine from CPROPS (cite: ROSOLOWSKY06)." (3.1 Dust Continuum and Gas)
- **Starburst99** : ZAMS ionizing photon production per unit mass  
  > "Based on Starburst99 calculations (cite: LEITHERER99)" (4.3.1 Zero Age Main Sequence Stellar Mass)
- **IDL** : Listed as software; use not described  
  > "`CASA` (cite: CASA07), `IDL`, CPROPS[^5]" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of compact continuum peaks | 14 | not stated | dimensionless | 2 | Our imaging reveals $14$ bright, compact continuum peaks |
| Median log10 Mgas | 5.0 (range 3.6-5.7) | ~0.4-0.5 dex systematic | Msun (log) | 6 | We find median $\log_{10} M_{\rm gas} [\rm{M}_\odot ] \sim 5.0$ |
| Median log10 Mstar | 5.1 (range 4.1-6.0) | ~10% stat, systematics dominate | Msun (log) | 5 | have median $\log_{10} M_\star [M_\odot] = 5.1$ |
| Median log10 M_VT | 5.7 (range 5.1-6.4) | ~0.3 dex systematic | Msun (log) | 7 | we find median dynamical mass $\log_{10} M_{\rm VT} [\rm{M}_\odot ] \sim 5.7$ |
| Total ionizing photon rate from sources | 1.2e53 | not stated | s^-1 | 8 | We estimate a total ionizing photon production of $Q_0 \sim 1.2 \times 10^{53}$ s$^{-1}$ from our targets |
| Mean 350 GHz optical depth | ~0.09 (0.035-0.35) | not stated | dimensionless | 6 | with $\tau_{\rm 350 GHz} \sim 0.09$ on average |
| Fraction of 350 GHz flux in sources | ~15% (0.28 Jy of ~1.9 Jy) | not stated | dimensionless | 3 | account for $\sim 15\%$ of the total $350$ GHz emission from the nuclear region |
| Median log10 free-fall time | 4.9 (4.5-5.3) | not stated | yr (log) | 7 | $\log_{10} \tau_{\rm ff} \sim 4.9$ (range $4.5{-}5.3$) years |

## Qualitative findings

- Only one dust peak coincides with an HST-visible SSC; others are hidden by extinction  
  > "One source coincides with a known SSC, but the rest remain invisible in *Hubble* near-infrared (IR) imaging." (abstract)

## Claim tuples

- H: Compact dust peaks are forming super star clusters | E: Measure sizes, masses, line widths and 36 GHz association | R: Sizes few pc, masses 1e4-1e6 Msun, escape speeds >16 km/s, 36 GHz and dense-gas coincidence | F: Most are likely forming SSCs | **supported**
- H: Sources are still gas-rich and young | E: Compare Mgas, Mstar, virial mass and radial momentum limits | R: Gas ~50% of mass; momentum below SN/wind expectations | F: Feedback has not yet unbound the clusters | **supported**
- H: This mode produces a large fraction of the burst's stars | E: Compare Q0 and masses to burst totals using ~1 Myr formation timescale | R: 20-40% of ionizing photons; masses can account for the SFR | F: Order unity of stars may form in this phase | **partially**

## Reasoning

- Why this data: Higher resolution needed to resolve forming SSCs of few pc  
  > "This allows us resolve individual forming SSCs, which have sizes of a few pc" (1 Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Gas mass uncertain by ~0.4-0.5 dex from Tdust, kappa and DGR; sources may break up at higher resolution  
  > "the overall uncertainty on the gas mass is likely $\sim 0.4{-}0.5$ dex" (4.3.3 Gas Mass From Dust)
- Limitation (authors): Cannot distinguish free-free contamination at 350 GHz from synchrotron at 36 GHz with two bands  
  > "With only two bands, we cannot distinguish between contamination of the $350$ GHz band by free-free or the $36$ GHz band by synchrotron." (4.1 Size, Line Width, and Flux Measurements)
- Caveat (inferred, ours): Dust temperature of 130 K drives gas masses and is weakly constrained
- Caveat (inferred, ours): Formation timescale of 8 tau_ff is theory-based, so the star-fraction conclusion is assumption-dependent
- Caveat (inferred, ours): Peaks 11 and 12 are near the nucleus with uncertain ionization

## Reproducibility

- Data public (paper): ALMA project cited; VLA data from published paper; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00274.S." (Acknowledgments)
- Products in archive: _not stated_
- Code: CPROPS version at github.com/akleroy/cpropstoo  
  > "CPROPS[^5] (cite: ROSOLOWSKY06; LEROY15A)" (Software)
- Missing: Full tclean parameters and masks
- Missing: VLA 36 GHz and HST maps from other papers
- Missing: Exact aperture and fitting velocity ranges
- Data volume (inferred): ~100 GB to several hundred GB for three-array band 7 data
- Score (inferred): 3/5, Analysis equations and key assumptions are given, but imaging parameters and aligned ancillary data are not.
- Rediscovery candidate: no, Imaging recipe is incomplete and needs external VLA and HST data, though results are numeric.

## Links

- Method: Rosolowsky & Leroy 2006 (cite: ROSOLOWSKY06) (CPROPS peak finding)
- Method: Leitherer et al. 1999 (cite: LEITHERER99) (Starburst99 ionizing photon calibration)
- Companion: N. Krieger et al. (in preparation) (Full line images and CO(3-2) kinematics)
- Companion: Ando et al. 2017 (cite: ANDO17) (Lower resolution ALMA view of the clumps)
- Related: Local Volume Legacy
- Related: ATLASGAL

## Checks

```json
{
 "quotes": 72,
 "quotes_ok": 72,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 89,
  "stated": 55,
  "rate": 0.618
 },
 "evidence_ok": true
}
```

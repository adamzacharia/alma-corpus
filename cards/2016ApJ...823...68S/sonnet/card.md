# Gas Dynamics and Outflow in the Barred Starburst Galaxy NGC 1808 Revealed with ALMA

`2016ApJ...823...68S` | The Astrophysical Journal 2016 | first author: Salak, Dragan | arXiv: 1603.05881 | DOI: 10.3847/0004-637X/823/1/68

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies
- Question: How do inflow and outflow of molecular gas relate to star formation and dynamics in the barred starburst galaxy NGC 1808, as seen in CO(1-0) and 2.8 mm continuum?  
  > "To study the inflow and outflow processes related to star formation and dynamical evolution of the galaxy, we have carried out $^{12}$CO ($J=1-0$) mapping observations" (abstract)
- Target **NGC 1808**: coordinates 05h07m42.343s, -37d30m45.95s (J2000)  
  > "Distance$^{b}$ | 10.8 Mpc" (Table 1); "in the nearby (10.8 Mpc; (cite: Tul88)) starburst galaxy NGC 1808" (Introduction); z/distance 10.8 Mpc  
  > "Distance$^{b}$ | 10.8 Mpc" (Table 1); "in the nearby (10.8 Mpc; (cite: Tul88)) starburst galaxy NGC 1808" (Introduction); distance from Tully 1988 Nearby Galaxy Catalog  
  > "Distance$^{b}$ | 10.8 Mpc" (Table 1); "in the nearby (10.8 Mpc; (cite: Tul88)) starburst galaxy NGC 1808" (Introduction)

## Data provenance

- ALMA projects: 2012.1.01004.S
- bands: _not stated_
- frequencies and spectral setup: 4 SPWs at 101.271, 103.200, 113.271, 115.271202 GHz; 2 GHz each except SPW4 1.870 GHz with 976.56 kHz (2.548 km/s) channels  
  > "Four spectral windows at the rest frequencies of (1) 101.271, (2) 103.200, (3) 113.271, and (4) 115.271202 GHz" (2 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: ALMA 12-m array, 27 antennas (ACA and TP not used here)  
  > "Observations were conducted on 2014 March 8, with twenty seven antennas of the ALMA 12-m array as part of our cycle 1 project." (2 Observations and data reduction)
- configurations: _not stated_
- baselines: 15 m to 423 m  
  > "The longest baseline of the 12-m array was $L_\mathrm{max}=423$ m" (2 Observations and data reduction)
- angular resolution: 2.55x1.41 arcsec (robust=2); 2.26x1.23 arcsec (robust=0.5)  
  > "The angular resolution in the final data cube ($\mathrm{robust}=2$) is $2.55\ensuremath{''}\times1.41\ensuremath{''}$" (2 Observations and data reduction)
- max recoverable scale: ~21 arcsec  
  > "$\theta_\mathrm{MRS}\simeq0.6\lambda/L_\mathrm{min}\approx21\ensuremath{''}$" (2 Observations and data reduction)
- sensitivity: 5.5 mJy/beam per 10.2 km/s (CO); continuum 0.20 mJy/beam  
  > "The r.m.s. sensitivity of the CO image in emission-free channels is 5.5 mJy beam$^{-1}$ per velocity bin of 10.2 km s$^{-1}$" (2 Observations and data reduction)
- time on source: about 41 minutes  
  > "The total on-source time was about 41 minutes" (2 Observations and data reduction)
- observing dates: 2014 March 8  
  > "Observation date | 2014 March 8" (Table 2)
- pi or archival as stated: Authors' own cycle 1 project  
  > "as part of our cycle 1 project" (2 Observations and data reduction)
- Line: 12CO J=1-0 (115.271202 GHz)
- Other facility **ASTE**: HCN(4-3) spectrum and CO(3-2) data for systemic velocity and missing-flux estimate  
  > "Single-dish observations with Atacama Submillimeter Telescope Experiment (ASTE) were conducted in 2014 September and October" (Appendix)
- Other facility **HST**: Halpha and I-band (F814W) images for comparison  
  > "we used $I$-band (F814W filter on *Hubble Space Telescope*)" (4.1.5 Stellar surface density)
- Other facility **2MASS / VLT ISAAC**: Ks-band images for bar and stellar surface density  
  > "$K_s$-band \[ISAAC on *Very Large Telescope*; (cite: GA08)\] images" (4.1.5 Stellar surface density)
- External data: Low CO-to-H2 conversion factor X=0.8e20 from radiative transfer  
  > "Adopting a low conversion factor of $X=0.8\times10^{20}~\mathrm{cm}^{-2}~(\mathrm{K~km~s}^{-1})^{-1}$, estimated by (cite: Sal14)" (3.2.2) [from (cite: Sal14)]
- External data: SFR ~5 Msun/yr in hot spots and supernova rate 0.024/yr  
  > "$SFR\sim5~M_\ensuremath{\odot}~\mathrm{yr}^{-1}$ in all “hot spots” combined; (cite: Kra94)" (5.3) [from (cite: Kra94)]
- External data: Flat global rotation curve 190 km/s at large radius  
  > "a flat rotation curve of $v=190$ km s$^{-1}$ beyond $13.6\ensuremath{''}$, consistent with the global rotation curve (cite: Sof99)" (4.2.3) [from (cite: Sof99)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto (flux), J0609-1542 (bandpass), J0522-3627 (phase)  
  > "Callisto (flux density), J0609-1542 (bandpass), and J0522-3627 (phase)" (2 Observations and data reduction)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN with Briggs weighting, mosaic of 39 fields  
  > "deconvolved using the CLEAN algorithm with Briggs weighting" (2 Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: robust=0.5 (high-res, continuum); robust=2 (high-sensitivity)  
  > "high-resolution image with $\mathrm{robust}=0.5$, velocity resolution of 2.548 km s$^{-1}$" (2 Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Interactive CLEAN until residual looked like noise, then automatic to ~1 sigma threshold  
  > "The CLEAN procedure was carried out interactively until the residual map resembled pure noise." (2 Observations and data reduction)
- multiscale scales: _not stated_
- continuum subtraction: CO(1-0) contribution subtracted; MFS over four SPWs  
  > "produced by multi-frequency synthesis using four spectral windows after subtracting the contribution from CO (1-0)" (2 Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: Applied only for flux and mass derivation; most figures uncorrected  
  > "The images were corrected, however, in order to derive fluxes and masses." (2 Observations and data reduction)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 2.55x1.41 arcsec (robust 2); 2.26x1.23 arcsec (robust 0.5)  
  > "High resolution, FWHM$^{b}$ | $2.26\ensuremath{''}\times1.23\ensuremath{''}$" (Table 2)
- final rms: 5.5 mJy/beam (high sens.), 10.0 mJy/beam (high res.), continuum 0.20 mJy/beam  
  > "High resolution, CO (1-0)$^{b}$ | 10.0 mJy beam$^{-1}$" (Table 2)

### Inherited from earlier work

- Low X_CO, Tex=31 K, T_k and density for central 1 kpc  
  > "We adopt an excitation temperature of $T_\mathrm{ex}=31$ K (cite: Sal14)." (4.2.3 / 5.2.2) [from (cite: Sal14)]

### Not stated but needed to reproduce (our reading)

- CASA version and whether pipeline or manual calibration
- Cell size, image size, CLEAN masks, number of iterations, exact threshold in mJy
- Line-free channels used for continuum subtraction
- Flux calibrator model and flux scale uncertainty
- 3DBarolo version and parameter file (rings fixed, initial guesses, normalization, weighting)
- Moment-map clipping thresholds
- Details of how outflow flux fraction (10%, I_CO=122.4 Jy km/s) was measured
- Fitting details of bar pattern speed (which emission peaks)

## Analysis recipe

1. **Calibrate and image CO(1-0) and continuum**: CASA calibration, continuum subtraction, CLEAN with Briggs weighting producing two cubes and a continuum image  
  > "The data were calibrated, continuum-subtracted, deconvolved using the CLEAN algorithm with Briggs weighting." (2 Observations and data reduction)
   - software: CASA
   - parameter: robust=0.5 (2.548 km/s) and robust=2 (10.192 km/s)  
  > "high-sensitivity image with $\mathrm{robust}=2$ and velocity resolution 10.192 km s$^{-1}$" (2 Observations and data reduction)
   - fitting: _not stated_
   - validation: Residual inspected in emission-free channels; sidelobes ~1 sigma  
  > "side lobes were successfully suppressed to negligible levels comparable to 1 $\sigma$ r.m.s." (2 Observations and data reduction)
2. **Measure continuum sources and spectral index**: 2D Gaussian fitting of sources; spectral index from images of SPW 3+4 vs SPW 1+2  
  > "The locations and flux densities of all sources are derived by 2-dimensional Gaussian fitting" (3.1 Continuum emission)
   - fitting: 2D Gaussian  
  > "The locations and flux densities of all sources are derived by 2-dimensional Gaussian fitting and the results are presented in tables" (3.1 Continuum emission)
   - validation: _not stated_
3. **Moment maps, gas masses and surface densities**: Moments 0-2; mass M=1.05e4 (X/XMW) d^2 S dv; Sigma from I_CO with X_CO 0.8e20 or 2e20; radial profile via ELLINT in rings  
  > "by using the MIRIAD task ELLINT to find average flux densities in rings and then applied equation" (3.2.2)
   - software: MIRIAD
   - parameter: PA=324 deg, i=58 deg, dR=1.13 arcsec  
  > "$PA=324\ensuremath{^\circ}$, $i=58\ensuremath{^\circ}$ (derived in section 4.1), and radius increments of $\Delta R=1.13\ensuremath{''}$" (3.2.2)
   - assumption: X_CO=0.8e20 (low) or 2e20 (Galactic); factor 1.41 for He  
  > "The total molecular gas mass corrected for He and heavy elements is $\Sigma_\mathrm{mol}=1.41\Sigma_\mathrm{H_2}$" (3.2.2)
   - fitting: Two Gaussians to radial profile  
  > "The resulting curve can be fit with two Gaussian functions of the form $a\exp[-(R-b)^2/(2c)^2]$ that correspond to the nuclear concentration (CND) and the ring." (3.2.2 Gas surface density in the central starburst region)
   - validation: _not stated_
4. **Tilted-ring fit of kinematics**: 3DBarolo on high-resolution cube, 12 rings of 1.13 arcsec, center fixed at continuum peak, inclination constrained to 57+-5 deg, scale height 150 pc, vsys from 20% peaks  
  > "The calculation was carried out within 12 rings of equal width $\Delta r=1.13\ensuremath{''}=\theta_\mathrm{maj}/2$" (4.1.1 Parameter computation)
   - software: 3DBarolo
   - parameter: h_z=150 pc fixed  
  > "The gas scale height (disk thickness) was kept as a non-free parameter at $h_z=150$ pc." (4.1.1 Parameter computation)
   - assumption: Circular motion only  
  > "The computation, however, does not handle non-circular motion" (4.1)
   - fitting: 3DBarolo ring fitting; sampler/likelihood not stated  
  > "we used the program $^{\mathrm{3D}}$Barolo (3D-Based Analysis of Rotating Objects from Line Observations) that fits tilted-ring models to (3-dimensional) spectroscopic data" (4.1 Derivation of geometric and kinematic parameters in the central 1 kpc)
   - validation: Compared to ASTE CO(3-2) fit, HCN(4-3) velocity, 2MASS Ks PA, HI  
  > "A similar value of $965\pm5$ km s$^{-1}$ was derived when we applied the fitting procedure on the ASTE CO (3-2) data cube" (4.1.2)
5. **Decompose rotation curve into mass components**: Plummer sphere models for bulge and major core plus nuclear cluster and optional BH, fitted to rotation curve smoothed at 2.26 arcsec; compared to I and Ks profiles  
  > "The bulge and major core are represented by a simple Plummer sphere model (cite: Plu11)" (4.1.4)
   - assumption: Spherical symmetry; uniform M/L; disk and halo neglected  
  > "An exponential disk and dark halo components are not included here because their contributions are small at $r<500$ pc." (4.1.4)
   - fitting: _not stated_
   - validation: Bulge mass within 5% of Sofue et al. 1999  
  > "is consistent within 5% with the bulge mass derived by (cite: Sof99)" (4.1.4)
6. **Residual velocity field, bar pattern speed and resonances**: Subtract circular model velocity field; linear least-squares fit of velocity vs radius of ridge emission peaks (1-3 kpc); resonances from kappa  
  > "Measuring the velocities at emission peaks along the ridge within the bar ($1~\mathrm{kpc}\leq r\leq3~\mathrm{kpc}$) and fitting with a least-squares method" (4.2.3)
   - assumption: Cloud-orbit model; v_z=0; flat 190 km/s beyond 1.5 kpc  
  > "Assuming that most of the emission originates in the galactic plane ($v_z=0$), the residual image yields a relation between azimuthal and radial velocities." (4.2.2 Bar pattern speed and Lindblad resonances)
   - fitting: Least squares  
  > "Measuring the velocities at emission peaks along the ridge within the bar ($1~\mathrm{kpc}\leq r\leq3~\mathrm{kpc}$) and fitting with a least-squares method" (4.2.2 Bar pattern speed and Lindblad resonances)
   - validation: Corotation consistent with weak-bar predictions  
  > "This result is consistent with theoretical predictions for weak bars" (4.2.2 Bar pattern speed and Lindblad resonances)
7. **Outflow mass, energy, rate**: Optically thick (10% of M_mol, X=0.8e20) and optically thin (f=1e4, Tex=31 K) limits; v_z=|vobs-vsys|/cos i; t=z/v  
  > "Assuming an abundance ratio of $f=10^4$, the total mass within $r<R=15\ensuremath{''}$ becomes $M_\mathrm{out}=1.41\times2m_\mathrm{H}\mathcal{N}_{\mathrm{H}_2}\sim8\times10^6~M_\ensuremath{\odot}$" (5.2.2)
   - assumption: Outflow perpendicular to disk; height 1 kpc  
  > "Assuming a nuclear outflow perpendicular to the galactic plane, the average deprojected outflow velocity becomes" (5.1 Morphology and kinematics)
   - fitting: _not stated_
   - validation: Compared with SN energy and NGC 253/M82 ratios  
  > "By comparison, the mass outflow rate in the nearby starburst galaxy NGC 253 is" (5.3 Dynamical evolution)
8. **Disk stability**: Toomre Q_gas with v_s=sigma_mol, alpha=1  
  > "The resulting $Q_\mathrm{gas}$, calculated with $v_\mathrm{s}=\sigma_\mathrm{mol}$" (6)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration, continuum subtraction, CLEAN imaging  
  > "Data reduction was carried out using the Common Astronomy Software Applications (CASA) package (cite: McM07)." (2 Observations and data reduction)
- **3DBarolo** : tilted-ring modeling  
  > "we used the program $^{\mathrm{3D}}$Barolo (3D-Based Analysis of Rotating Objects from Line Observations) that fits tilted-ring models" (4.1)
- **MIRIAD** : ELLINT radial surface density  
  > "by using the MIRIAD task ELLINT" (3.2.2)
- **NEWSTAR** : ASTE data reduction  
  > "Data reduction was done by using the NEWSTAR tool" (Appendix)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Bar pattern speed | 56 | 11 | km/s/kpc | 6 | we derive a bar pattern speed of $\Omega_\mathrm{b}=56\pm11$ km s$^{-1}$ kpc$^{-1}$ |
| Systemic velocity (global) | 963.9 | 2.5 | km/s | 4 | $v_\mathrm{sys}=963.9\pm2.5$ km s$^{-1}$ within the central region |
| Systemic velocity (CND) | 998.4 | 2.5 | km/s | 4 | $v_\mathrm{sys}=998.4\pm2.5$ km s$^{-1}$ |
| CND molecular mass (X=0.8e20) | 1.4e8 | not stated | Msun | 3 | $M_{\mathrm{mol}}(r<250~\mathrm{pc})\simeq1.4\times10^8~M_\odot$ |
| Total CO(1-0) flux of mosaic | 1521 | not stated | Jy km/s | 3 | The total CO (1-0) flux detected over the $150\ensuremath{''}\times150\ensuremath{''}$ mosaic image is 1521 Jy km s$^{-1}$ |
| Dynamical mass r<705 pc | 7.5e9 | not stated | Msun | 4 | $M_\mathrm{dyn}(r<705~\mathrm{pc})=rv_\mathrm{rot}^2/G\simeq7.5\times10^9~M_\odot$ |
| Nuclear continuum total flux density | 4.68 | 0.57 | mJy | 2 | Total flux density / $4.68\pm0.57$ mJy |
| Core spectral index | -1 | not stated | dimensionless | 2 | with $\alpha_\mathrm{core}\simeq-1$ at the galactic center position |
| Deprojected outflow velocity | 180 | not stated | km/s | 7 | \simeq180~\mathrm{km~s}^{-1} |
| Outflow mass (optically thin) | 8e6 | not stated | Msun | 7 | $M_\mathrm{out}=1.41\times2m_\mathrm{H}\mathcal{N}_{\mathrm{H}_2}\sim8\times10^6~M_\ensuremath{\odot}$ |
| Mass outflow rate / SFR | ~0.2 | not stated | dimensionless | 7 | yielding $\dot{M}_\mathrm{out}/SFR\sim0.2$ for the optically thin case |
| Corotation radius | 2.9-3.6 | not stated | kpc | 6 | $r_\mathrm{CR}=v_\mathrm{rot}/\Omega_\mathrm{b}\simeq(2.9-3.6)$ kpc |

## Qualitative findings

- Four molecular components: CND, ~500 pc ring, gas-rich bar, spiral arms  
  > "Four distinct components of molecular gas are revealed at high spatial resolution of 2$''$ ($\sim100$ pc)" (abstract)
- Kinematic offset between CND and 500-pc ring systemic velocities  
  > "indicating a kinematic offset" (abstract)

## Claim tuples

- H: Does the CND have a different systemic velocity from the larger disk? | E: 3DBarolo fits to the central region versus global, checked with HCN(4-3) | R: 998.4 vs 963.9 km/s | F: Kinematic offset between CND and ring | **supported**
- H: What is the bar pattern speed and resonance structure? | E: Linear fit of ridge velocities in PVD | R: 56+-11 km/s/kpc; r_CR ~3.4 kpc; ILR ~500 pc | F: Weak bar with ILR coincident with the ring | **supported**
- H: Is there a molecular outflow and how efficient is it at quenching? | E: Residual velocities and PVDs; mass estimate in thick and thin limits | R: v~180 km/s; Mout/SFR~0.2 (thin) | F: Low quenching efficiency, though outflow mass uncertain without short spacings | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: 3DBarolo fits circular motion so residuals reveal non-circular features  
  > "The residuals would reveal non-circular features." (4.1)
- Alternative: Inflow in the disk rejected in favor of outflow for blueshifted NE gas  
  > "Also, the detection of blueshifted emission NE from the center excludes the possibility of an extraplanar gas inflow." (5.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Missing short spacings; fluxes are lower limits; outflow mass highly uncertain  
  > "so the derivation of the outflow mass is largely uncertain" (5.3)
- Caveat (inferred, ours): Outflow mass relies on a rough 10% flux fraction and assumed Tex, abundance and X_CO
- Caveat (inferred, ours): Only 12-m data; extended emission missing (~40% in central 2 kpc)
- Caveat (inferred, ours): Plummer decomposition is non-unique, no formal fit or uncertainties
- Caveat (inferred, ours): Spectral index sensitive to narrow lever arm in frequency

## Reproducibility

- Data public (paper): ALMA data cited by project code  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.01004.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and clean parameters
- Missing: 3DBarolo configuration
- Missing: Outflow flux extraction region and velocity range
- Data volume (inferred): ~50-100 GB raw for 39-field mosaic
- Score (inferred): 3/5, Public data and reasonably described steps, but imaging and 3DBarolo parameters and outflow extraction are underspecified.
- Rediscovery candidate: no, Key numbers depend on unstated imaging and fitting settings and judgment-based outflow estimates.

## Links

- Method: (cite: dTF15) (3DBarolo tilted-ring code)
- Companion: (cite: Sal14) (Single-dish CO(3-2) study providing X_CO and Tex)

## Checks

```json
{
 "quotes": 84,
 "quotes_ok": 84,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 90,
  "stated": 63,
  "rate": 0.7
 },
 "evidence_ok": true
}
```

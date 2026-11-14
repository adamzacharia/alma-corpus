# ALMA Reveals Sequential High-mass Star Formation in the G9.62+0.19 Complex

`2017ApJ...849...25L` | The Astrophysical Journal 2017 | first author: Liu, Tie | arXiv: 1705.04907 | DOI: 10.3847/1538-4357/aa8d73

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Does stellar feedback from evolved Hii regions trigger or shape sequential high-mass star formation in the adjacent G9.62 clump, based on its cores, outflows and fragmentation?  
  > "In this work, we study the interaction between the evolved Hii regions (“A", “B" & “C") and the G9.62 clump." (1 Introduction)
- Target **G9.62+0.19 complex (G9.62 clump)**: coordinates phase centers R.A.(J2000)=18h06m14.67s, decl.=-20d31m31.91s and R.A.=18h06m14.90s, decl.=-20d31m40.21s  
  > "Located at a distance of 5.2 kpc (cite: san09), the G9.62+0.19 complex contains a cluster of radio continuum sources" (The G9.62+0.19 complex); z/distance 5.2 kpc  
  > "Located at a distance of 5.2 kpc (cite: san09), the G9.62+0.19 complex contains a cluster of radio continuum sources" (The G9.62+0.19 complex); distance from Sanna et al. 2009 (cite: san09)  
  > "Located at a distance of 5.2 kpc (cite: san09), the G9.62+0.19 complex contains a cluster of radio continuum sources" (The G9.62+0.19 complex)

## Data provenance

- ALMA projects: 2013.1.00957.S
- bands: Band 6 (230 GHz)  
  > "The observations employed the Band 6 (230 GHz) receivers with dual-polarization mode." (2.1 ALMA Observations)
- frequencies and spectral setup: five 117 MHz windows plus one 234 MHz window; 61 kHz (0.08 km/s) channels, smoothed to 0.16 km/s  
  > "We used five spectral windows with a bandwidth of 117 MHz in each window and another spectral window with a bandwidth of 234 MHz" (2.1 ALMA Observations)
- continuum bandwidth: 350 MHz line-free channels  
  > "using the line-free spectral channels with a total bandwidth of 350 MHz" (2.1 ALMA Observations)
- arrays: 12-m (compact, 39 antennas; extended, 34 antennas) and 7-m (10 antennas)  
  > "on 2015 April 27 in its compact configuration with a total of 39 antennas in the 12-m array; on 2015 May 24 in its extended configuration with a total of 34 antennas in the 12-m array" (2.1 ALMA Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: ~20"  
  > "The largest recoverable scale (LAS) in the combined data is $\sim20\ensuremath{''}$" (2.1 ALMA Observations)
- sensitivity: continuum 1 sigma 0.8 mJy; lines ~10 mJy/beam per 0.16 km/s channel  
  > "The continuum image reaches a 1$\sigma$ rms noise of 0.8 mJy in a synthesized beam of $0\ensuremath{''}.94\times0\ensuremath{''}.71$ (P.A.=80.25 deg)." (2.1 ALMA Observations)
- time on source: _not stated_
- observing dates: 2015 April 27 (12m compact), 2015 May 24 (12m extended), 2015 May 04 (7m)  
  > "on 2015 May 04 with 10 antennas in the 7-m array" (2.1 ALMA Observations)
- pi or archival as stated: _not stated_
- Line: SiO 5-4 (217.10498 GHz)
- Line: CO 2-1 (230.53800 GHz)
- Line: CH3OH vt=1 6(1,5)-7(2,6) (217.29920 GHz)
- Other facility **IRTF/TEXES**: 12.8 um [Ne II] maps of Hii regions  
  > "We observed the Hii regions in the \[Ne ii\] 12.8 $\ensuremath{\mu}m$ line" (2.2 [Ne ii] observations)
- Other facility **JCMT HARP**: archival C18O (3-2) cube for virial analysis  
  > "The C$^{18}$O (3-2) datacube was obtained from the JCMT archive and was not published in literatures." (2.3 JCMT C18O (3-2) observations)
- Other facility **Herschel, JCMT/SCUBA, APEX/LABOCA, SEST/SIMBA**: far-IR to mm fluxes for clump SED  
  > "We obtained publicly available Herschel data from the Herschel archive." (Appendix A)
- External data: Herschel band flux densities of the clump  
  > "The flux densities of the G9.62 clump at Herschel bands were determined by (cite: moli16)." (Appendix A) [from Molinari et al. 2016 (cite: moli16)]
- External data: SEST/SIMBA 1.2 mm flux density  
  > "The flux density at SEST/SIMBA 1.2 mm was determined by (cite: fau04) from 2-D Gaussian fit." (Appendix A) [from Faundez et al. 2004 (cite: fau04)]
- External data: SiO abundances 1.4e-10 (30 K) and 2.1e-10 (40 K)  
  > "(cite: gern14) found that the median SiO abundances in HMPOs and hot cores are 1.4$\times10^{-10}$ (for T=30 K) and 2.1$\times10^{-10}$ (for T=40 K)" (3.3 Molecular outflows) [from Gerner et al. 2014 (cite: gern14)]
- External data: Ionized gas density 1.6e3 cm-3 and Te 10000 K for source B  
  > "We adopt the electron density n$_{e}$ of 1.6$\times10^{3}$ cm$^{-3}$ and an electron temperature T$_{e}$ of 10000 K (cite: gar93)." (4.2 Fragmentation analysis) [from Garay et al. 1993 (cite: gar93)]
- External data: CO optical-depth correction factors 9, 5, 2 for mass, momentum, energy  
  > "were underestimated by factors of about 9, 5, and 2, respectively, if assuming optically thin emission (cite: Zhang16)" (3.3 Molecular outflows) [from Zhang et al. 2016 (cite: Zhang16)]

## Processing

### Calibration

- pipeline or manual: calibrated in CASA by ALMA staff, checked by authors; updated antenna positions and fixed resolved flux calibrators  
  > "The visibility data were calibrated in CASA by the ALMA supporting staff. We examined the calibration." (2.1 ALMA Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune (12m extended), Titan (12m compact), J1733-130 (7m)  
  > "Neptune, Titan and Quasar J1733-130 were used for flux calibration in the observations with the extended configuration" (2.1 ALMA Observations)
- flux scale uncertainty: _not stated_
- self calibration: applied on continuum; gains applied to line data  
  > "The gain solutions from the self-calibration were applied to the spectral line data." (2.1 ALMA Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: three configurations combined in CASA; no single-dish data  
  > "The visibility data from the three configurations were combined in CASA." (2.1 ALMA Observations)
- smoothing: spectra smoothed to 0.16 km/s  
  > "We smoothed the spectra lines to 0.16 km s$^{-1}$ spectral resolution in data analysis" (2.1 ALMA Observations)
- final beam: continuum 0.94"x0.71" (PA 80.25 deg); SiO 1.02"x0.75"; CO 0.94"x0.73"; CH3OH 0.99"x0.72"  
  > "The synthesized beams for SiO (5-4), CO (2-1) and CH$_{3}$OH v$_{t}$=1 ($6_{1,5}-7_{2,6}$) lines are $1\ensuremath{''}.02\times0\ensuremath{''}.75$ (P.A.=84.97 deg)" (2.1 ALMA Observations)
- final rms: 0.8 mJy continuum  
  > "The continuum image reaches a 1$\sigma$ rms noise of 0.8 mJy" (2.1 ALMA Observations)

### Inherited from earlier work

- Outflow mass, momentum, energy computed per channel assuming optically thin emission  
  > "Following (cite: qiu07; qiu09; wang11; zhang15; liu11; liu15a; liu16a), we calculated the outflow masses (M), momentum (P) and kinetic energy (E) in each velocity channel" (3.3 Molecular outflows) [from qiu07; qiu09; wang11; zhang15; liu11; liu15a; liu16a]
- Jeans and cylindrical fragmentation analysis  
  > "Following (cite: wang12; wang14), we derive the masses and separation of dense cores predicted in Jeans fragmentation and Cylindrical fragmentation." (4.2 Fragmentation analysis) [from wang12; wang14]
- Collect-and-collapse analysis  
  > "Following (cite: whit94a; whit94b), we obtain that the time (t$_{frag}$), the radius (R$_{frag}$)" (Appendix C) [from whit94a; whit94b]
- Dynamical timescale 1e4 yr for MM8/F  
  > "Here we simply assume its timescale of $1\times10^{4}$ yr, as also used in (cite: liu11)." (3.3 Molecular outflows) [from liu11]

### Not stated but needed to reproduce (our reading)

- CASA version and tclean/clean parameters (weighting, robust, cell, image size, deconvolver, masks)
- Line-free channels used for continuum and continuum subtraction method
- Self-calibration solution intervals
- Velocity ranges integrated for outflow lobes and noise clipping
- Dust-mass equations A1-A2 for cores and how flux used
- Fitting method for mass-velocity broken power laws
- Primary beam correction details

## Analysis recipe

1. **Extract continuum cores**: Identify cores above 5 sigma in 1.3 mm map; 2-D Gaussian fits (Gaussian plus point source for MM4, MM6, MM8, MM11)  
  > "We identified 12 dense cores above 5 $\sigma$ signal level from the 1.3 mm continuum map." (4.1 ALMA 1.3 mm continuum)
   - software: CASA
   - fitting: 2-D Gaussian fits  
  > "were obtained from 2-D Gaussian fits and presented in Table [1](#corepara)" (4.1 ALMA 1.3 mm continuum)
   - validation: Residual images checked  
  > "point-like source emission remains in the residual images" (4.1 ALMA 1.3 mm continuum)
2. **Clump SED and core masses**: Single-temperature modified blackbody SED fit of clump; core masses from dust emission at assumed Td  
  > "We used a nonlinear least-squares method (the Levenberg–Marquardt algorithm coded within IDL) to fit the observed SED with equation (1) assuming a single dust component" (Appendix A)
   - software: IDL
   - parameter: Td=35 K, beta=1.5 from SED; 100 K for MM4/7/8/11; 20 K for starless candidates  
  > "We firstly calculate core masses with a T$_{d}$ of 35 K and $\beta$ of 1.5" (4.1 ALMA 1.3 mm continuum)
   - assumption: gas-to-dust 100, kappa0=0.01 cm2/g at 230 GHz (Ossenkopf & Henning 1994), mu=2.37  
  > "Assuming a gas to dust ratio of 100, the dust opacity per unit gas mass is $\kappa_{\nu}=\kappa_{0}(\frac{\nu}{\nu_{0}})^{\beta}$" (Appendix A)
   - fitting: Levenberg-Marquardt least squares, 10% flux uncertainties  
  > "we used 10% uncertainties for flux densities in SED fit" (Appendix A)
   - validation: Varying flux errors 5-20% and beta 1-2 changes little  
  > "The change (from 5% to 20%) of uncertainties does not affect the SED fit too much." (Appendix A)
3. **Virial analysis with C18O**: Two-Gaussian fit to JCMT C18O(3-2) spectrum; virial mass M=210 R dV^2  
  > "The virial mass considering turbulent support can be derived as $\frac{M_{vir}}{M_{\ensuremath{\odot}}}=210(\frac{R}{pc})(\frac{\Delta V}{km~s^{-1}})^2$" (4.2.1 JCMT C18O (3-2) line and virial analysis)
   - parameter: R~0.25 pc per sub-clump  
  > "With a radius of $\sim$0.25 pc" (4.2.1 JCMT C18O (3-2) line and virial analysis)
   - assumption: Tex=35 K, optically thin  
  > "Assuming an excitation temperature of 35 K, the same as dust temperature" (4.2.1 JCMT C18O (3-2) line and virial analysis)
   - fitting: two Gaussians  
  > "The spectrum can be well fitted with two gaussian components." (4.2.1 JCMT C18O (3-2) line and virial analysis)
   - validation: Optical depths ~0.3 and ~0.7  
  > "the optical depths of blueshifted component and redshifted component are $\sim$0.3 and $\sim$0.7, respectively" (4.2.1 JCMT C18O (3-2) line and virial analysis)
4. **Outflow mass, momentum, energy and accretion rates**: Per-channel optically thin masses from SiO and CO; inclination corrections; accretion rate from outflow force  
  > "we calculated the outflow masses (M), momentum (P) and kinetic energy (E) in each velocity channel assuming optically thin emission" (3.3 Molecular outflows)
   - parameter: Inclination 70 deg (MM6), 0 deg (MM7/G), 45 deg (MM8/F)  
  > "Therefore, we take 45$\ensuremath{^\circ}$ as the inclination angle for MM8/F." (3.3 Molecular outflows)
   - assumption: Vw~500 km/s, Mw/Macc~0.1, fent=0.25; SiO abundance enhanced x10 (MM7/MM8) and x40 (MM6); CO opacity correction from HH 46/47  
  > "We assume a typical jet/wind velocity of $V_w \sim 500$ km s$^{-1}$ (cite: lam95)." (3.3 Molecular outflows)
   - fitting: _not stated_
   - validation: Optical-depth corrected CO mass agrees with SiO mass with abundance enhancement and with earlier SO/CS/HCN  
  > "The outflow mass of MM8/F derived from SiO (5-4) is now consistent with outflow mass derived from CO (2-1) by applying optical depth correction." (3.3 Molecular outflows)
5. **Fragmentation analysis**: Compare observed core mass and spacing with thermal/turbulent Jeans and cylindrical fragmentation predictions; compare molecular and ionized gas pressure  
  > "we derive the masses and separation of dense cores predicted in Jeans fragmentation and Cylindrical fragmentation." (4.2 Fragmentation analysis)
   - parameter: T=35 K, n=9.1e4 cm-3; turbulent case Teff~670 K  
  > "Only considering thermal Jeans instability by taking T=35 K, and n=$(9.1\pm0.7)\times10^4$ cm$^{-3}$" (Table 4)
   - fitting: _not stated_
   - validation: Collect-and-collapse model tested and rejected  
  > "These inconsistences indicate that the formation and fragmentation of the G9.62 clump was not determined by the “Collect and Collapse" process." (Appendix C)
6. **Mass-velocity diagrams**: Per-channel outflow mass vs velocity fit with linear or broken power laws, slopes and break velocities tabulated  
  > "We calculate the outflow masses in each velocity channel and present the mass-velocity diagrams of the molecular outflows associated with MM6, MM7/G and MM8/F" (4.3 Mass-velocity diagrams of outflows)
   - fitting: broken power law dM/dv ~ v^-gamma; R^2 reported  
  > "A broken power law, $dM(v) / dv \propto v^{-\gamma}$ usually exhibits in the mass-velocity diagrams of molecular outflows" (4.3 Mass-velocity diagrams of outflows)
   - validation: R^2 of fits in Table 5  
  > "Flow Velocity intervals | a or $\gamma$ | R$^{2}$" (Table 5)

## Software

- **CASA** : calibration by ALMA staff, combination of three configurations, self-calibration  
  > "The visibility data from the three configurations were combined in CASA." (2.1 ALMA Observations)
- **IDL (Levenberg-Marquardt)** : SED fitting  
  > "the Levenberg–Marquardt algorithm coded within IDL" (Appendix A)
- **CuTEx** : Herschel source extraction (by Molinari et al.)  
  > "The source extraction at each Herschel band was performed with the CuTEx algorithm" (Appendix A)
- **TEXES custom FORTRAN reduction** : [Ne II] data reduction  
  > "We use a custom FORTAN reduction program (cite: lacy02) to correct optical distortions, flat-field" (2.2 [Ne ii] observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA continuum rms | 0.8 | not stated | mJy | 1 | The continuum image reaches a 1$\sigma$ rms noise of 0.8 mJy |
| Number of dense cores | 12 | not stated | dimensionless | 1 | We identified 12 dense cores above 5 $\sigma$ signal level |
| Core masses (Td=35 K) | 4 to 87, median ~20 | not stated | Msun | 2 | The core masses range from 4 to 87 M$_{\ensuremath{\odot}}$ with a median value of $\sim$20 M$_{\ensuremath{\odot}}$. |
| Clump mass from SED | 2800 | 200 | Msun | 2 | a total dust and gas mass of 2800$\pm$200 M$_{\ensuremath{\odot}}$ |
| Clump dust temperature and beta | 35 K; 1.5 | 1 K; 0.1 | K; dimensionless | 2 | a dust temperature of $35\pm1$ K and a dust opacity index ($\beta$) of 1.5$\pm$0.1 |
| Clump luminosity | 1.7e6 | 0.1e6 | Lsun | 2 | a total luminosity of $(1.7\pm0.1)\times10^{6}$ L$_{\ensuremath{\odot}}$ |
| Total virial mass of clump | 1200 | 180 | Msun | 3 | The total virial mass of the G9.62 clump is $\sim1200\pm180$ M$_{\ensuremath{\odot}}$ |
| Mass accretion rates MM6, MM7/G, MM8/F | 3.9e-4, 5.7e-5, 2.2e-3 | not stated | Msun/yr | 4 | The total mass accretion rates for MM6, MM7/G, MM8/F are about 3.9$\times10^{-4}$, 5.7$\times10^{-5}$ and 2.2$\times10^{-3}$ M$_{\ensuremath{\odot}}$ yr$^{-1}$. |
| MM6 outflow dynamical timescale | 8.5e3 | not stated | yr | 4 | we can derive a dynamic timescale of $t_{dyn}=\frac{L}{V_{char}}=8.5\times10^{3}$ yr |
| Gas depletion time of clump | 11 | 1 | Myr | 0 | The gas depletion time ($\tau_{dep}$) is $\tau_{dep}=\frac{M_{clump}}{\dot{M_{*}}}=11\pm1$ Myr |
| Molecular gas pressure P/k | 6.1e7 | 0.5e7 | K cm-3 | 5 | $(6.1\times0.5)\times$10$^{7}$ K cm$^{-3}$ |
| Thermal Jeans core mass and spacing | 6.0 Msun; 0.13 pc | 0.1; 0.01 | Msun; pc | 5 | 1-2 6.0$\pm$0.1 / 0.13$\pm$0.01 |

## Qualitative findings

- Cores span starless to UC Hii phases; evolutionary sequence MM6 -> MM7/G -> MM8/F -> MM4/E -> MM11/D  
  > "The evolutionary sequence of the 5 high-mass protostellar cores are MM6 (HMPO)$\rightarrow$MM7/G (early HMC)$\rightarrow$MM8/F (HMC)$\rightarrow$MM4/E (late HMC or HC Hii)$\rightarrow$MM11/D (UC Hii)." (4.1.1 High-mass protostellar cores)
- Lack of widespread low-mass core population  
  > "There is a lack of a widespread low-mass (M$\leq$ 1-2 M$_{\ensuremath{\odot}}$) core population in the G9.62 clump." (4.1 ALMA 1.3 mm continuum)

## Claim tuples

- H: Are there massive starless cores in the G9.62 clump? | E: Core classification from CH3OH, SiO, outflows and cm continuum; masses at 20 K | R: Five cores (MM1, MM3, MM5, MM9, MM10) have M>25 Msun at Td<=20 K and no protostellar indicators | F: They are massive starless core candidates needing confirmation | **partially**
- H: Is fragmentation governed by thermal or turbulent Jeans instability? | E: Compare observed spacing/mass with predicted values | R: Thermal spacing ~0.1 pc matches observed ~0.08 pc; turbulent gives 0.4-0.6 pc | F: Fragmentation is governed by thermal instability | **supported**
- H: Do Hii region shocks drive sequential star formation in the clump? | E: Pressure comparison, [Ne II] velocities, PDR morphology, core evolutionary ordering | R: Ionized pressure ~4e7 comparable to molecular ~6e7 K cm-3; ~5 km/s velocity offset | F: Hii shocks likely compress the clump and induce sequential collapse; collect-and-collapse rejected | **partially**
- H: Do SiO and CO outflows differ in mass-velocity break? | E: Broken power law fits to MM7/G and MM8/F outflows | R: SiO breaks at 12-18 km/s, CO at 31-33 km/s | F: SiO traces newly shocked gas while CO traces entrained ambient gas | **partially**
- H: Is star formation efficiency enhanced by Hii compression? | E: Compare L_TIR/M_clump with other clumps | R: Gas depletion time 11 Myr, ~10x shorter than average | F: Compression likely enhances efficiency | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Hot-core vs UC Hii classification via CH3OH vt=1 and outflows as evolutionary clocks  
  > "Therefore, outflows can also be used as a clock for core evolution." (4.1.1 High-mass protostellar cores)
- Alternative: Collect-and-collapse origin rejected: fragment separation 0.52 pc vs observed ~0.1 pc and tfrag longer than Hii age  
  > "the separation (2r$_{frag}\sim$0.52 pc) is about five times larger than the averaged separation ($\sim$0.1 pc) of the ALMA dense cores" (Appendix C)
- How they decided it was enough: _not stated_
- Limitation (authors): Core dust temperatures poorly known; masses uncertain mainly through Td  
  > "The main uncertainties of masses come from the determination of T$_{d}$." (4.1 ALMA 1.3 mm continuum)
- Limitation (authors): No 13CO to correct CO opacity; correction borrowed from another source  
  > "Unfortunately, we did not observe $^{13}$CO line." (3.3 Molecular outflows)
- Limitation (authors): No single-dish data in combination  
  > "although no single dish data included in the combination, the missing flux is not a severe problem" (2.1 ALMA Observations)
- Caveat (inferred, ours): Core masses depend on assumed Td (35/100/20 K) without resolved temperature data
- Caveat (inferred, ours): Causal link to Hii region triggering is circumstantial; no direct kinematic proof
- Caveat (inferred, ours): SiO abundance enhancement factors are tuned to match CO, so partly circular
- Caveat (inferred, ours): Single-temperature SED for a clump with embedded UC Hii regions
- Caveat (inferred, ours): Starless classification based on non-detection of limited tracers

## Reproducibility

- Data public (paper): ALMA project cited; JCMT and Herschel from public archives  
  > "We obtained publicly available Herschel data from the Herschel archive." (Appendix A)
- Products in archive: _not stated_
- Missing: Imaging parameters (weighting, cell, masks)
- Missing: CASA version
- Missing: Equations A1-A2 core-mass derivation details and line-free channels
- Missing: Integration velocity ranges for outflow lobes
- Missing: TEXES data not public
- Data volume (inferred): ~50-100 GB (three ALMA configurations, six spectral windows with 61 kHz channels)
- Score (inferred): 5/5, ALMA data public and many analysis numbers given, but imaging/CASA parameters and outflow integration ranges are missing.
- Rediscovery candidate: yes, Public ALMA data; core catalog and outflow parameters are numeric and checkable, though imaging details are missing.

## Links

- Method: Wang et al. 2014 (cite: wang14) (Jeans and cylindrical fragmentation formulae)
- Method: Whitworth et al. 1994 (cite: whit94a; whit94b) (collect and collapse model)
- Method: Qiu et al. 2009 (cite: qiu09) (outflow parameter derivation)
- Companion: Liu et al. 2011 (cite: liu11) (earlier SMA study of G9.62+0.19)
- Related: Herschel Hi-GAL
- Related: JCMT/SCUBA archive
- Related: APEX ATLASGAL

## Checks

```json
{
 "quotes": 87,
 "quotes_ok": 87,
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
  "stated": 65,
  "rate": 0.722
 },
 "evidence_ok": true
}
```

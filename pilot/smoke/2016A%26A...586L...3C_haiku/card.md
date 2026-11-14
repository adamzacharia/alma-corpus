# Water and acetaldehyde in HH212: The first hot corino in Orion

`2016A&A...586L...3C` | Astronomy and Astrophysics 2016 | first author: Codella, C. | arXiv: 1601.00539 | DOI: 10.1051/0004-6361/201527424

Card schema 1.0 | model claude-haiku-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, astrochemistry
- Question: Whether and how hot corinos, circumstellar disks, and ejected gas are related in young solar-mass protostars, tested with CH$_3$CHO and HDO high-excitation lines towards HH212–MM1.  
  > "we aim to investigate whether and how hot corinos, circumstellar disks, and ejected gas are related in young solar-mass protostars" (abstract)
- Target **HH212–MM1**: coordinates α(J2000) = 05h 43m 51s41, δ(J2000) = −01° 02' 53''17 (MM1 continuum peak, per Lee et al. 2014)  
  > "Positions are given with respect to the MM1 protostar continuum peak located at" (Observations); "HH212 is located in Orion (at 450 pc) and is one of the best laboratories" (Introduction: The HH212 laboratory); z/distance 450 pc  
  > "Positions are given with respect to the MM1 protostar continuum peak located at" (Observations); "HH212 is located in Orion (at 450 pc) and is one of the best laboratories" (Introduction: The HH212 laboratory); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.000647.S
- bands: 850 μm (Band 7 not named in text)  
  > "HH212 was observed at 850" (Observations)
- frequencies and spectral setup: Spectral windows 333.7–337.4 GHz and 345.6–349.3 GHz; spectral units of 488 kHz (0.42–0.44 km/s)  
  > "The spectral windows 333.7–337.4 GHz and 345.6–349.3 GHz were observed using spectral units of 488 kHz" (Observations)
- continuum bandwidth: ALMA 8 GHz bandwidth  
  > "The ALMA 8 GHz bandwidth presents a very rich spectrum with many lines in emission towards the MM1 protostar" (Results and discussion)
- arrays: 24 12 m antennas (ALMA Early Science Cycle 0)  
  > "HH212 was observed at 850 $\mu$m with ALMA using 24 12 m antennas on 2012 December 1" (Observations)
- configurations: _not stated_
- baselines: 20 m to 360 m  
  > "The baselines were between 20 m and 360 m with a maximum unfiltered scale of 3" (Observations)
- angular resolution: Clean-beam FWHM 0.65''×0.47'' (PA = 35°), typical  
  > "The continuum-subtracted images have a typical clean-beam FWHM of" (Observations)
- max recoverable scale: 3'' (maximum unfiltered scale)  
  > "The baselines were between 20 m and 360 m with a maximum unfiltered scale of 3" (Observations)
- sensitivity: rms noise 3–4 mJy/beam in 0.44 km/s channels  
  > "an rms noise level of 3–4 mJy beam" (Observations)
- time on source: _not stated_
- observing dates: 2012 December 1  
  > "on 2012 December 1 (Early Science Cycle 0 phase; Codella et al. 2014)" (Observations)
- pi or archival as stated: Archival dataset of Codella et al. (2014), PI C. Codella  
  > "This paper makes use of the ADS/JAO.ALMA#2011.0.000647.S data (PI: C. Codella)" (Acknowledgements)
- Line: CH$_3$CHO (acetaldehyde) Twelve high-excitation lines with E_u 150–200 K; e.g. 18(1,18)–17(1,17) E (333941.4 MHz for 18(1,18)–17(1,17) E (one of the twelve; see Table 1))
- Line: HDO (deuterated water) 3(3,1)–4(2,2) (335395.5 MHz)
- External data: Disk of ~0.2'' (90 AU) in rotation around a ~0.3±0.1 solar-mass source (ALMA Early Science)  
  > "consistent with a rotating disk of $\simeq 0.2\ensuremath{''}$ = 90 AU around a $\simeq 0.3\pm0.1 M_{\rm \odot}$ source" (Introduction: The HH212 laboratory) [from Lee et al. 2014; Codella et al. 2014; Podio et al. 2015]
- External data: N(H2) ~10^24–10^25 cm^-2 on ~470 AU scale towards NGC1333-IRAS2A and IRAS4A  
  > "Taquet et al. (2015) measured N(H$_2$) $\simeq$ 10$^{24}$–10$^{25}$ cm$^{-2}$ towards the NGC1333-IRAS2A and IRAS4A hot corinos" (Results and discussion) [from Taquet et al. 2015]
- External data: CH3CHO abundance ~3 x 10^-9 in IRAS16293-2422 (single-dish)  
  > "in agreement with the value recently derived in the IRAS16293-2422 hot corino (using single-dish data; 3 $\times$ 10$^{-9}$: Jaber et al. 2014)." (Results and discussion) [from Jaber et al. 2014]
- External data: Initial H2O abundance of 3 x 10^-5 assumed in hot corino HDO analysis  
  > "assuming an initial H$_2$O abundance of 3 $\times$ 10$^{-5}$; see Taquet et al. 2014, 2015" (Results and discussion) [from Taquet et al. 2014, 2015]
- External data: SO abundance up to 10^-7 in the low-velocity outflowing gas  
  > "where a high SO abundance (up to 10$^{-7}$) has also been detected by Podio et al. (2015)." (Conclusions) [from Podio et al. 2015]
- External data: HDO/H2O ratios measured in hot corinos (used as consistency check)  
  > "consistent with the values measured in hot corinos (Persson et al. 2014; Ceccarelli et al. 2015)." (Results and discussion) [from Persson et al. 2014; Ceccarelli et al. 2015]
- Simulation/model as data: Non-LTE LVG (Large Velocity Gradient) model, plane parallel geometry, using the code of Ceccarelli et al. 2003, to predict temperature versus HDO column density  
  > "we compare the observed emission with that predicted by a non-LTE LVG (Large Velocity Gradient) model using the code by Ceccarelli et al. (2003)" (HDO emission)

## Processing

### Calibration

- pipeline or manual: Calibration following standard procedures (pipeline or manual not specified)  
  > "Calibration was carried out following standard procedures" (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Quasars J0538–440, J0607–085 and planets Callisto and Ganymede used as calibrators; which one set the flux scale is not stated  
  > "using quasars J0538–440, J0607–085, Callisto, and Ganymede" (Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA package for spectral line imaging (task not stated)  
  > "Spectral line imaging was achieved with the CASA package" (Observations)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum-subtracted images used (method not stated)  
  > "The continuum-subtracted images have a typical clean-beam FWHM of" (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: Typical clean-beam FWHM 0.65''×0.47'', PA = 35°  
  > "The continuum-subtracted images have a typical clean-beam FWHM of" (Observations)
- final rms: 3–4 mJy/beam per 0.44 km/s channel  
  > "an rms noise level of 3–4 mJy beam" (Observations)

### Inherited from earlier work

- ALMA dataset of HH212 from Codella et al. (2014), Early Science Cycle 0 observations used as-is  
  > "In this letter, we further exploit the ALMA dataset of Codella et al. (2014) to probe the inner region of HH212." (Introduction: The HH212 laboratory) [from Codella et al. 2014 (cite: codella14)]
- Systemic velocity of +1.7 km/s adopted (instead of +1.3 km/s used in Codella et al. 2014)  
  > "we adopt here +1.7 km s$^{-1}$ (Lee et al. 2014)" (Results and discussion (footnote 2)) [from Lee et al. 2014 (cite: lee14)]
- HDO–H2 collisional coefficients computed by Faure et al. (2012), extracted from BASECOL  
  > "the collisional coefficients for the system HDO-H$_2$ computed by Faure et al. (2012)" (HDO emission); "The collisional coefficients are extracted from the BASECOL database, Dubernet et al. (2013)." (HDO emission (footnote 3)) [from Faure et al. 2012 (cite: faure); Dubernet et al. 2013 (cite: dubernet)]
- Line frequencies and E_u from JPL molecular database  
  > "The lines were identified using the Jet Propulsion Laboratory (JPL) molecular database (Pickett et al. 1998)." (Results and discussion) [from Pickett et al. 1998 (cite: pickett)]
- Assumed ortho-to-para H2 Boltzmann distribution (details in footnote 4)  
  > "and assuming a Boltzmann distribution for the ortho-to-para H$_2$ ratio" (HDO emission) [from Faure et al. 2012 (cite: faure) (per footnote 4)]

### Not stated but needed to reproduce (our reading)

- CASA version, calibration pipeline/manual split, and flux calibrator assignment for the 2012 Cycle 0 data
- Imaging task settings: weighting (robust), deconvolver, cell size, image size, masking, uv taper, and the continuum-subtraction method and line-free channels
- Primary-beam correction and the array-combination choice (only the ALMA-only beam is given)
- Definition of the 'typical' clean beam and which channels/images are used for the reported rms
- Method and fit used for the LTE rotational diagram (line selection threshold, error propagation, Tex/N fit procedure)
- LVG grid details: ranges of temperature and column density, step sizes, the velocity gradient, the line width used, and the beam-dilution formula
- Exact source size used for CH3CHO (0.3'' assumed) vs HDO (0.3'' and 0.06'' cases) and how the 'factor of five' size reduction was chosen
- How H2 column density was derived from density and size for the N(HDO)/N(H2) constraint
- Exact water abundance assumed for HDO/H2O (1e-4 vs 3e-5 quoted) and the D/H elemental ratio value used for the 10% limit
- Velocity-resolved profile extraction procedure (aperture, spectra averaging) and the asymmetry measurement definition

## Analysis recipe

1. **Line imaging and identification**: Spectral line imaging of the ALMA dataset in CASA; line identification against the JPL database; continuum-subtracted images analysed in GILDAS  
  > "Spectral line imaging was achieved with the CASA package, while data analysis was performed using the GILDAS" (Observations); "The lines were identified using the Jet Propulsion Laboratory (JPL) molecular database (Pickett et al. 1998)." (Results and discussion)
   - software: CASA, GILDAS, JPL molecular database
   - parameter: Spectral units 488 kHz (0.42–0.44 km/s); clean-beam 0.65''×0.47''; rms 3–4 mJy/beam per channel  
  > "The spectral windows 333.7–337.4 GHz and 345.6–349.3 GHz were observed using spectral units of 488 kHz" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive CH3CHO temperature and column density**: LTE optically thin analysis of CH3CHO using a rotational diagram; only lines with less than 30% blending contamination; source size set to half a beam (0.3'')  
  > "An LTE (Local Thermodynamic Equilibrium) optically thin analysis of CH$_3$CHO (using only lines with less than 30% contamination from blended lines, in terms of integrated emission, see Table 1)" (CH$_3$CHO emission)
   - parameter: Source size 0.3'' (half beam); alternative 0.06'' gives N larger by ~20  
  > "Given that the CH$_3$CHO emission is spatially unresolved, we assume a source size equal to half a beam, namely 0$\ensuremath{''}$3." (CH$_3$CHO emission)
   - assumption: Emission from hot corino at dust temperature ≥100 K; source spatially unresolved  
  > "the region where the dust temperature is high enough ($\geq$ 100 K) to sublimate the frozen ice mantles" (CH$_3$CHO emission)
   - fitting: Rotational diagram (LTE) fit; fitting details not stated  
  > "which allows us to derive $T_{\rm rot}$ = 87$\pm$47 K and $N_{\rm tot}$ = 2$\pm$1 $\times$ 10$^{15}$ cm$^{-2}$." (The CH$_3$CHO rotational diagram)
   - validation: Opacity check: opacity less than 0.4 with derived values  
  > "With these values the opacity is less than 0.4." (CH$_3$CHO emission)
3. **Constrain HDO physical conditions with non-LTE LVG models**: Non-LTE LVG grid in temperature versus HDO column density for densities 1e7–1e10 cm^-3, compared with observed HDO line intensity; densities 1e6 cm^-3 excluded  
  > "Figure 4 shows the temperature versus the HDO column density predicted to generate the observed signal" (HDO emission)
   - software: LVG code of Ceccarelli et al. 2003, BASECOL collisional database (Dubernet et al. 2013)
   - parameter: Source size 0.3'' (upper panel) and a size lower by a factor of five (lower panel); plane parallel geometry  
  > "the upper panel shows the case of a source size equal to half a beam (0$\ensuremath{''}$3) and the lower panel shows a case with a size that is lower by a factor of five" (HDO emission)
   - parameter: Density range 1e7 to 1e10 cm^-3; low end set by HDO/H2 ≤ 3.2e-6 constraint  
  > "The plots cover densities from 10$^7$ to $10^{10}$ cm$^{-3}$." (HDO emission)
   - assumption: HDO abundance below 10% of D/H elemental abundance; N(H2) derived from density and source size; ortho-to-para H2 Boltzmann distribution  
  > "The low end, 10$^7$ cm$^{-3}$, is set by the constraint that the HDO abundance has to be smaller than 10% of the D/H elemental abundance" (HDO emission)
   - fitting: Comparison of predicted curves with the observed line intensity; no statistical fit stated
   - validation: Density 1e6 cm^-3 ruled out because the line intensity cannot be reproduced  
  > "We find that it is not possible, then, to reproduce the HDO line intensity and we rule out a density of 10$^6$ cm$^{-3}$." (HDO emission)
4. **Interpret HDO low-velocity asymmetry (thin vs thick)**: Compare disk, infall-envelope and outflow origins for the optically thin case; for the optically thick case, require tau=1 curves to intersect observed signal within beam dilution constraint  
  > "The last and most likely possibility is that the low-velocity HDO emission is dominated by outflowing motions." (Optically thin case); "one needs to assume a larger beam dilution factor requiring a source size smaller than 0$\ensuremath{''}$08 (37 AU) and larger than 0$\ensuremath{''}$04 (18 AU)." (Optically thick case)
   - parameter: Intermediate size 0.06'' (28 AU) shown in lower panel of Fig. 4  
  > "The lower panel of Fig. 4 shows the intermediate case, with 0$\ensuremath{''}$06 (28 AU)." (Optically thick case)
   - assumption: Line opacity equal to unity (tau=1 dashed curves) for optically thick case  
  > "we add dashed curves where the HDO line opacity is equal to unity" (Optically thick case)
   - fitting: _not stated_
   - validation: Disk and infall origins disfavoured based on peak brightness and velocity asymmetry and spatial resolution arguments  
  > "However, the low-velocity range of the HDO line being due to the protostellar disk is not supported" (Optically thin case)
5. **Derive abundances and HDO/H2O ratio**: Convert HDO column density to N(HDO)/N(H2) using N(H2) from density and size; CH3CHO abundance from N(H2) of Taquet et al. 2015 at 0.3'' size  
  > "If we take these values and 0$\ensuremath{''}$3 as emitting size, then $X_{\rm CH_3CHO}$ $\sim$ 0.2–2 $\times$ 10$^{-9}$" (CH$_3$CHO emission)
   - parameter: Water abundance assumed ~1e-4 for HDO/H2O estimate  
  > "Assuming a typical water abundance of $\sim 10^{-4}$ would imply HDO/H$_2$O $\sim 1.7\times 10^{-2}$–$10^{-3}$" (Optically thick case)
   - assumption: Continuum cannot be used for N(H2) because the peak is optically thick; N(H2) taken from other hot corinos  
  > "Unfortunately, we cannot use the continuum emission to estimate the H$_2$ column density" (CH$_3$CHO emission)
   - fitting: _not stated_
   - validation: Consistency with HDO/H2O values in hot corinos and with CH3CHO abundance in IRAS16293-2422  
  > "consistent with the values measured in hot corinos (Persson et al. 2014; Ceccarelli et al. 2015)." (Optically thick case)

## Software

- **CASA** : Spectral line imaging of the ALMA data  
  > "Spectral line imaging was achieved with the CASA package" (Observations)
- **GILDAS** : Data analysis of continuum-subtracted images and spectra  
  > "while data analysis was performed using the GILDAS" (Observations)
- **JPL molecular database** : Line identification and E_u, S mu^2 values for CH3CHO and HDO transitions  
  > "The lines were identified using the Jet Propulsion Laboratory (JPL) molecular database (Pickett et al. 1998)." (Results and discussion)
- **LVG code of Ceccarelli et al. 2003** : Non-LTE LVG radiative transfer predictions for HDO  
  > "using the code by Ceccarelli et al. (2003)" (HDO emission)
- **BASECOL** : Source of HDO-H2 collisional coefficients  
  > "The collisional coefficients are extracted from the BASECOL database, Dubernet et al. (2013)." (HDO emission (footnote 3))

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CH3CHO rotational temperature T_rot | 87 | ±47 | K | 2 | which allows us to derive $T_{\rm rot}$ = 87$\pm$47 K and $N_{\rm tot}$ = 2$\pm$1 $\times$ 10$^{15}$ cm$^{-2}$. |
| CH3CHO total column density N_CH3CHO | 2 x 10^15 | ±1 x 10^15 | cm^-2 | 2 | indicates temperature of 87$\pm$47 K and a column density of 2$\pm$1 $\times$ 10$^{15}$ cm$^{-2}$ |
| CH3CHO line opacity (upper limit) | less than 0.4 | not stated | dimensionless | 2 | With these values the opacity is less than 0.4. |
| Factor by which N_CH3CHO increases for 0.06'' source size | ~20 | not stated | dimensionless | 2 | In the case of a smaller emitting size, e.g. 0$\ensuremath{''}$06 (as assumed for HDO in Sect. 3), $N_{\rm CH_3CHO}$ increases by a factor of $\sim$ 20. |
| CH3CHO fractional abundance X_CH3CHO | 0.2–2 x 10^-9 | not stated | dimensionless | 5 | then $X_{\rm CH_3CHO}$ $\sim$ 0.2–2 $\times$ 10$^{-9}$, in agreement with the value recently derived in the IRAS16293-2422 hot corino |
| HDO column density upper limit at 1e6 cm^-3 (0.3'' size; density excluded) | ≤ 7 x 10^15 | not stated | cm^-2 | 3 | In particular, for a size of 0$\ensuremath{''}$3, if the density is 10$^6$ cm$^{-3}$, then $N$(HDO) should be $\leq 7 \times 10^{15}$ cm$^{-2}$. |
| HDO column density upper limit at 1e7 cm^-3 | ≤ 7 x 10^16 | not stated | cm^-2 | 3 | On the other hand, at 10$^7$ cm$^{-3}$, $N$(HDO) has to be $\leq 7 \times 10^{16}$ cm$^{-2}$, and the temperature has to be larger than 230 K (see Fig. 4). |
| Minimum kinetic temperature for HDO at 1e7 cm^-3 | > 230 | not stated | K | 3 | and the temperature has to be larger than 230 K (see Fig. 4). |
| Optically thick HDO emitting source size range | 18–37 AU (0.04''–0.08'') | not stated | AU | 4 | one needs to assume a larger beam dilution factor requiring a source size smaller than 0$\ensuremath{''}$08 (37 AU) and larger than 0$\ensuremath{''}$04 (18 AU). |
| Optically thick HDO solution temperature range | 70–110 | not stated | K | 4 | The solution is, in this case, for temperatures between 70 K and 110 K and densities of $10^9$–$10^{10}$ cm$^{-3}$. |
| Optically thick HDO solution density range | 1e9–1e10 | not stated | cm^-3 | 4 | The solution is, in this case, for temperatures between 70 K and 110 K and densities of $10^9$–$10^{10}$ cm$^{-3}$. |
| N(HDO) at T ~100 K (optically thick case) | ~7 x 10^17 | not stated | cm^-2 | 4 | In particular, for a temperature around 100 K, $N$(HDO)$\sim 7 \times 10^{17}$ cm$^{-2}$ |
| HDO/H2 abundance N(HDO)/N(H2) | 1.7e-6 to 1e-7 | not stated | dimensionless | 5 | corresponding to $N$(HDO)/$N$(H$_2$)=$1.7\times 10^{-6}$–$10^{-7}$. |
| HDO/H2O ratio (assuming H2O ~1e-4) | 1.7e-2 to 1e-3 | not stated | dimensionless | 5 | Assuming a typical water abundance of $\sim 10^{-4}$ would imply HDO/H$_2$O $\sim 1.7\times 10^{-2}$–$10^{-3}$ |
| Line FWHM of CH3CHO and HDO profiles | 5–6 | not stated | km/s | 0 | which is also quite broad (FWHM $\simeq$ 5–6 km s$^{-1}$) |
| Line profile peak velocity range | +1.2 to +2.0 | not stated | km/s | 0 | The line profiles peak in the +1.2,+2.0 km s |

## Qualitative findings

- First detection of a hot corino in Orion (HH212-MM1)  
  > "We report the first detection of a hot corino in Orion." (abstract)
- Acetaldehyde abundance similar to hot corinos in Ophiuchus  
  > "The acetaldehyde abundance is similar to that measured in hot corinos located in low-mass star forming regions in Ophiuchus." (Conclusions)
- Low-velocity HDO asymmetry indicates contribution of slow outflowing gas  
  > "The asymmetric HDO profile at low velocities indicates that at least some of the deuterated water is associated with slow outflowing gas" (Conclusions)
- Emitting region may be associated with a disk wind if optically thick  
  > "it is tempting to speculate that the observed gas may be associated with a disk wind gas accelerated at the base." (Conclusions)

## Claim tuples

- H: Do CH3CHO and HDO high-excitation lines reveal a hot corino around HH212-MM1? | E: LTE rotational diagram of CH3CHO lines, with source size set to half a beam | R: T_rot = 87±47 K and N = 2±1 x 10^15 cm^-2 (opacity < 0.4) | F: Hot corino with T ~100 K detected in HH212; first in Orion | **supported**
- H: Is the low-velocity HDO asymmetry produced by the rotating disk or the infalling envelope? | E: Comparison of HDO peak brightness and velocities with disk and envelope kinematics and spatial scales | R: Disk origin would need a factor-2 non-axisymmetry; infall would give resolved peak emission | F: Disk and infall origins are disfavoured | **supported**
- H: Is the low-velocity HDO emission dominated by outflowing gas? | E: Optically thin LVG and kinematic arguments comparing HDO with SiO and SO outflow tracers | R: HDO brightness in the red lobe; SO shows low-velocity compact bipolar outflow | F: Outflowing motions are the most likely origin of low-velocity HDO | **partially**
- H: If HDO is optically thick, how small and dense must the emitting region be? | E: Non-LTE LVG grid with tau=1 curves and beam-dilution constraint on source size | R: Source size 18–37 AU, T 70–110 K, n 1e9–1e10 cm^-3 | F: Extremely small, dense, slowly outflowing emitting region | **partially**

## Reasoning

- Why this data: The ALMA dataset of Codella et al. (2014) is reused to probe the inner region of HH212 with high-excitation lines  
  > "In this letter, we further exploit the ALMA dataset of Codella et al. (2014) to probe the inner region of HH212." (Introduction: The HH212 laboratory)
- Why this method: A non-LTE LVG model is used to compare the HDO signal with predictions, because the emission is unresolved and optical depth matters  
  > "In order to understand the relative importance of each, we study two limit situations" (HDO emission)
- Alternative: HDO from the rotating protostellar disk: rejected on peak brightness and velocity asymmetry grounds  
  > "First, the HDO emission might probe the rotating disk" (Optically thin case)
- Alternative: HDO from the rotating infalling envelope: rejected because it would give spatially resolved peaks  
  > "which would lead to spatially resolved peak emission, unlike the observed emission" (Optically thin case)
- Alternative: Optically thick infalling envelope (redshifted absorption): rejected in favour of blueshifted absorption from outflow  
  > "because an optically thick infalling envelope would lead to redshifted absorption" (Optically thick case)
- How they decided it was enough: _not stated_
- Limitation (authors): Continuum peak optically thick, so H2 column density cannot be derived from continuum  
  > "Unfortunately, we cannot use the continuum emission to estimate the H$_2$ column density" (CH$_3$CHO emission)
- Limitation (authors): Source sizes are assumed because emission is spatially unresolved; results depend on size choice  
  > "Given that the CH$_3$CHO emission is spatially unresolved, we assume a source size equal to half a beam, namely 0$\ensuremath{''}$3." (CH$_3$CHO emission)
- Limitation (authors): Systemic velocity uncertain (+1.3 to +1.8 km/s in literature); results said to be not all dependent on the choice  
  > "However, the results are not all dependent on this choice." (Results and discussion (footnote 2))
- Caveat (inferred, ours): Optically thick scenario relies on assumed source size, N(H2) from other sources, and water abundance; the 18–37 AU size is not directly measured
- Caveat (inferred, ours): CH3CHO N(H2) and abundance borrow values from hot corinos in other regions (Taquet et al. 2015)
- Caveat (inferred, ours): Single-epoch, single-configuration dataset with unresolved emission limits kinematic conclusions
- Caveat (inferred, ours): Rotational diagram temperature uncertainty (±47 K) is large relative to the 100 K hot-corino claim

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: _not stated_
- Missing: CASA version and full imaging recipe (weighting, deconvolver, cell size, masking, continuum subtraction, line-free channels)
- Missing: Rotational diagram fitting details and the list of 12 CH3CHO lines with their blend contamination
- Missing: LVG grid parameters (velocity gradient, line width, T and N grid steps, beam-dilution formula)
- Missing: Source sizes and N(H2) conversion used for HDO and CH3CHO abundances
- Missing: External inputs: N(H2) from Taquet et al. 2015, water abundance and D/H ratio used for limits
- Data volume (inferred): Small: one spectral-line ALMA dataset (two spectral windows of about 3.7 GHz each, 24 antennas, single epoch), likely a few GB of visibilities, inferred from the setup described.
- Score (inferred): 3/5, Data are an archival reuse of Codella et al. 2014 with public status not stated; imaging recipe and LVG inputs are largely missing, though line list, frequencies, beam and rms are given.
- Rediscovery candidate: no, Public availability of the archival data is not stated in the paper, and key imaging and modelling settings are missing, so the recipe is not complete enough to redo the main results.

## Links

- Method: Ceccarelli et al. 2003 (cite: cecilia03) (Non-LTE LVG code used for HDO predictions)
- Method: Faure et al. 2012 (cite: faure) (HDO-H2 collisional coefficients)
- Method: Dubernet et al. 2013 (cite: dubernet) (BASECOL database source of collisional coefficients)
- Method: Pickett et al. 1998 (cite: pickett) (JPL molecular database used for line identification)
- Companion: Codella et al. 2014 (cite: codella14) (Source of the ALMA dataset reused in this paper)
- Companion: Podio et al. 2015 (cite: podio15) (SO and SiO ALMA results from the same dataset used to interpret outflow)
- Companion: Lee et al. 2014 (cite: lee14) (Disk, envelope and systemic velocity constraints used for HH212-MM1)
- Related: ALMA Early Science Cycle 0

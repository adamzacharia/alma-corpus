# Water and acetaldehyde in HH212: The first hot corino in Orion

`2016A&A...586L...3C` | Astronomy and Astrophysics 2016 | first author: Codella, C. | arXiv: 1601.00539 | DOI: 10.1051/0004-6361/201527424

Card schema 1.0 | model claude-haiku-5-5 | depth full | type archival_reuse

## Science

- Fields: astrochemistry, star_formation, protoplanetary_disks
- Question: Whether and how hot corinos, circumstellar disks and ejected gas are related in young solar-mass protostars, tested by imaging high-excitation CH3CHO and HDO lines in HH212-MM1.  
  > "we aim to investigate whether and how hot corinos, circumstellar disks, and ejected gas are related in young solar-mass protostars" (abstract)
- Target **HH212-MM1**: coordinates 05h 43m 51s41, -01 deg 02' 53''17 (J2000, as printed)  
  > "Positions are given with respect to the MM1 protostar continuum peak located at" (Observations); "HH212 is located in Orion (at 450 pc)" (Introduction: The HH212 laboratory); z/distance 450 pc  
  > "Positions are given with respect to the MM1 protostar continuum peak located at" (Observations); "HH212 is located in Orion (at 450 pc)" (Introduction: The HH212 laboratory); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.000647.S
- bands: 850 um (ALMA Early Science Cycle 0)  
  > "HH212 was observed at 850 $\mu$m with ALMA using 24 12 m antennas" (Observations)
- frequencies and spectral setup: Spectral windows 333.7-337.4 GHz and 345.6-349.3 GHz; spectral unit 488 kHz (0.42-0.44 km/s)  
  > "The spectral windows 333.7–337.4 GHz and 345.6–349.3 GHz were observed using spectral units of 488 kHz" (Observations)
- continuum bandwidth: _not stated_
- arrays: 24 12 m antennas  
  > "using 24 12 m antennas on 2012 December 1" (Observations)
- configurations: _not stated_
- baselines: 20 m to 360 m  
  > "The baselines were between 20 m and 360 m with a maximum unfiltered scale of" (Observations)
- angular resolution: typical clean-beam FWHM 0.65'' x 0.47'' (PA 35 deg)  
  > "The continuum-subtracted images have a typical clean-beam FWHM of" (Observations)
- max recoverable scale: 3''  
  > "with a maximum unfiltered scale of 3$\ensuremath{''}$" (Observations)
- sensitivity: rms 3-4 mJy/beam in 0.44 km/s channels  
  > "an rms noise level of 3–4 mJy beam" (Observations)
- time on source: _not stated_
- observing dates: 2012 December 1  
  > "on 2012 December 1 (Early Science Cycle 0 phase; Codella et al. 2014)" (Observations)
- pi or archival as stated: Archival dataset of Codella et al. (2014), PI C. Codella  
  > "we further exploit the ALMA dataset of Codella et al. (2014)" (Introduction: The HH212 laboratory)
- Line: CH3CHO (acetaldehyde) 18(1,18)-17(1,17) E, 17(2,15)-16(2,14) A, 18(0,18)-17(0,17) A, 18(3,16)-17(3,15) A and E (unblended set used in analysis) (333941.4, 334931.4, 335358.7, 347519.2, 347563.3 MHz)
- Line: HDO (deuterated water) 3(3,1)-4(2,2), Eu = 335 K (335395.5 MHz)
- External data: N(H2) of about 1e24-1e25 cm-2 towards NGC1333-IRAS2A and IRAS4A hot corinos on a scale of about 470 AU, used to convert CH3CHO column to abundance  
  > "Taquet et al. (2015) measured N(H$_2$)" (Results and discussion) [from Taquet et al. (2015) (cite: taquet15)]
- External data: CH3CHO abundance of 3e-9 in IRAS16293-2422 from single-dish data, used for comparison  
  > "in agreement with the value recently derived in the IRAS16293-2422 hot corino (using single-dish data; 3 $\times$ 10$^{-9}$: Jaber et al. 2014)" (Results and discussion) [from Jaber et al. 2014 (cite: jaber)]
- External data: Systemic velocity of +1.7 km/s adopted for HH212  
  > "The value of +1.3 km s$^{-1}$ adopted in Codella et al. (2014) was affected by a shift in the frequency scale" (Results and discussion) [from Lee et al. 2014 (cite: lee14)]
- External data: Disk density expected to be larger than about 1e7 cm-3  
  > "whose density is expected to be larger than $\sim 10^7$ cm$^{-3}$ (Lee et al. 2014)" (Optically thin case) [from Lee et al. 2014 (cite: lee14)]
- External data: HDO/H2O and HDO abundance ratios measured in hot corinos, used for comparison  
  > "consistent with the values measured in hot corinos (Persson et al. 2014; Ceccarelli et al. 2015)" (Optically thick case) [from Persson et al. 2014 (cite: persson); Ceccarelli et al. 2015 (cite: cecilia15)]
- Simulation/model as data: Non-LTE LVG model grid of HDO line temperature vs column density over densities 1e7-1e10 cm-3 (Figure 4)  
  > "The plots cover densities from 10$^7$ to $10^{10}$ cm$^{-3}$" (HDO emission)

## Processing

### Calibration

- pipeline or manual: Standard procedures (manual or pipeline not stated)  
  > "Calibration was carried out following standard procedures" (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Not identified which source is the flux calibrator; calibrators named as quasars J0538-440, J0607-085, Callisto and Ganymede  
  > "using quasars J0538–440, J0607–085, Callisto, and Ganymede" (Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA package (task not stated)  
  > "Spectral line imaging was achieved with the CASA package" (Observations)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Images are continuum-subtracted; method not stated  
  > "The continuum-subtracted images have a typical clean-beam FWHM of" (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.65'' x 0.47'' (PA 35 deg), typical clean beam  
  > "typical clean-beam FWHM of $0.65\ensuremath{''}\times0.47\ensuremath{''}$ (PA = 35$\ensuremath{^\circ}$)" (Observations)
- final rms: 3-4 mJy/beam in 0.44 km/s channels  
  > "an rms noise level of 3–4 mJy beam" (Observations)

### Inherited from earlier work

- ALMA dataset and calibration/imaging of the Early Science observations  
  > "we further exploit the ALMA dataset of Codella et al. (2014)" (Introduction: The HH212 laboratory) [from Codella et al. 2014 (cite: codella14)]
- Systemic velocity adoption: +1.7 km/s (the +1.3 km/s of Codella 2014 is affected by a frequency-scale shift)  
  > "we adopt here +1.7 km s$^{-1}$ (Lee et al. 2014)" (Introduction: The HH212 laboratory) [from Lee et al. 2014 (cite: lee14)]
- HDO abundance limited to below 10% of the D/H elemental abundance, with an assumed initial H2O abundance of 3e-5  
  > "assuming an initial H$_2$O abundance of 3 $\times$ 10$^{-5}$; see Taquet et al. 2014, 2015" (HDO emission) [from Taquet et al. 2014 (cite: taquet14); Taquet et al. 2015 (cite: taquet15)]
- HDO-H2 collisional coefficients  
  > "the collisional coefficients for the system HDO-H$_2$ computed by Faure et al. (2012)" (HDO emission) [from Faure et al. 2012 (cite: faure)]
- HDO collisional coefficients extracted from the BASECOL database  
  > "The collisional coefficients are extracted from the BASECOL database, Dubernet et al. (2013)." (Footnote 3) [from Dubernet et al. 2013 (cite: dubernet)]
- Non-LTE LVG code, plane-parallel geometry  
  > "a non-LTE LVG (Large Velocity Gradient) model using the code by Ceccarelli et al. (2003)" (HDO emission) [from Ceccarelli et al. 2003 (cite: cecilia03)]
- Line frequencies and line strengths from the JPL database  
  > "The lines were identified using the Jet Propulsion Laboratory (JPL) molecular database (Pickett et al. 1998)." (Results and discussion) [from Pickett et al. 1998 (cite: pickett)]

### Not stated but needed to reproduce (our reading)

- Imaging parameters: weighting/robust value, deconvolver, cell size, image size, masking and channel binning for the continuum-subtracted cubes.
- Continuum subtraction method and line-free channels used.
- Which source served as flux calibrator and the flux-scale uncertainty; whether self-calibration was applied.
- Continuum flux values and the continuum peak fit used for the MM1 position.
- Rotational diagram fitting details: which lines were used in the diagram, whether the fit was weighted, and how the 87+/-47 K and 2+/-1e15 cm-2 uncertainties were derived.
- Assumed H2 column density and H2 ortho-to-para treatment for HDO, and the exact D/H elemental abundance value used for the 10% limit.
- Precise source size used for each case (0.3'' vs 0.06'') and how the intermediate case was chosen.
- Intensity-to-TB conversion and integration ranges used for the integrated fluxes in Table 1.

## Analysis recipe

1. **Image the spectral line cubes**: Spectral line imaging with CASA; continuum-subtracted images; data analysis in GILDAS  
  > "Spectral line imaging was achieved with the CASA package, while data analysis was performed using the GILDAS" (Observations)
   - software: CASA, GILDAS
   - parameter: Clean-beam FWHM 0.65'' x 0.47'' (PA 35 deg); rms 3-4 mJy/beam per 0.44 km/s channel  
  > "an rms noise level of 3–4 mJy beam" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive CH3CHO excitation temperature and column density (LTE)**: LTE optically thin rotational diagram using unblended lines (less than 30% blending contamination); source size half a beam  
  > "An LTE (Local Thermodynamic Equilibrium) optically thin analysis of CH$_3$CHO" (CH$_3$CHO emission)
   - parameter: Source size 0.3'' (half a beam, spatially unresolved)  
  > "we assume a source size equal to half a beam, namely 0" (CH$_3$CHO emission)
   - parameter: Lines with less than 30% contamination from blended lines  
  > "using only lines with less than 30% contamination from blended lines" (CH$_3$CHO emission)
   - assumption: Emission from the hot corino region with dust temperature of at least 100 K; optically thin (opacity below 0.4)  
  > "With these values the opacity is less than 0.4." (CH$_3$CHO emission)
   - fitting: Rotational diagram (Fig. A.1); linear fit method not stated  
  > "which allows us to derive" (The CH$_3$CHO rotational diagram)
   - validation: Synthetic spectra compared with observed spectra (Fig. 2); opacity check  
  > "see the the rotational diagram in Fig. A.1 and the synthetic spectra in Fig. 2" (CH$_3$CHO emission)
3. **Constrain HDO physical conditions with non-LTE LVG models**: Grid of temperature vs HDO column density for densities 1e7-1e10 cm-3; compare with observed HDO line; optically thin and thick (tau=1) cases  
  > "Figure 4 shows the temperature versus the HDO column density predicted to generate the observed signal" (HDO emission)
   - software: Ceccarelli et al. 2003 LVG code, BASECOL database
   - parameter: Source size 0.3'' (half beam) for upper panel; size lower by a factor of five (0.06'') for lower panel  
  > "the upper panel shows the case of a source size equal to half a beam (0$\ensuremath{''}$3) and the lower panel shows a case with a size that is lower by a factor of five" (HDO emission)
   - parameter: Ortho-to-para H2 ratio assumed Boltzmann distributed  
  > "assuming a Boltzmann distribution for the ortho-to-para H$_2$ ratio" (HDO emission)
   - assumption: Plane parallel geometry  
  > "a plane parallel geometry" (HDO emission)
   - assumption: Low-density end set by HDO abundance below 10% of D/H (N(HDO)/N(H2) <= 3.2e-6)  
  > "the HDO abundance has to be smaller than 10% of the D/H elemental abundance" (HDO emission)
   - fitting: Grid comparison of predicted and observed HDO intensity; not a sampler-based fit  
  > "Armed with these predictions, we now discuss the implications of each assumption" (HDO emission)
   - validation: Density 1e6 cm-3 ruled out because HDO line cannot be reproduced  
  > "We find that it is not possible, then, to reproduce the HDO line intensity and we rule out a density of 10$^6$ cm$^{-3}$" (HDO emission)
4. **Estimate CH3CHO fractional abundance**: Divide CH3CHO column by H2 column from literature scaled to the 0.3 arcsec size  
  > "If we take these values and 0$\ensuremath{''}$3 as emitting size, then" (CH$_3$CHO emission)
   - parameter: N(H2) about 1e24-1e25 cm-2 from Taquet et al. (2015) hot corinos  
  > "Taquet et al. (2015) measured N(H$_2$)" (CH$_3$CHO emission)
   - assumption: Continuum cannot be used for N(H2) because the peak is optically thick  
  > "we cannot use the continuum emission to estimate the H$_2$ column density" (CH$_3$CHO emission)
   - fitting: _not stated_
   - validation: Agreement with abundance in IRAS16293-2422 (Jaber et al. 2014)  
  > "in agreement with the value recently derived in the IRAS16293-2422 hot corino" (CH$_3$CHO emission)
5. **Interpret HDO low-velocity asymmetry and optically thick solution**: Test disk, infalling envelope and outflow origins for the blue/red asymmetry; for optically thick case, tau=1 curves intersect observed curves for source size 18-37 AU  
  > "requiring a source size smaller than 0$\ensuremath{''}$08 (37 AU) and larger than 0$\ensuremath{''}$04 (18 AU)" (Optically thick case)
   - parameter: Intermediate size 0.06'' (28 AU)  
  > "The lower panel of Fig. 4 shows the intermediate case, with 0$\ensuremath{''}$06 (28 AU)" (Optically thick case)
   - parameter: HDO line opacity set to unity (tau = 1 dashed curves)  
  > "we add dashed curves where the HDO line opacity is equal to unity" (Optically thick case)
   - assumption: Water abundance of about 1e-4 used to convert HDO to HDO/H2O  
  > "Assuming a typical water abundance of" (Optically thick case)
   - assumption: Blueshifted absorption interpreted as slow outflowing gas  
  > "the line asymmetry is due to blueshifted absorption, revealing again outflowing gas" (Optically thick case)
   - fitting: Intersection of tau=1 curves with observed-signal curves in the T vs N(HDO) plane  
  > "to have the two families of curves intersect" (Optically thick case)
   - validation: Disk and infalling envelope origins ruled out on kinematic and spatial grounds  
  > "We can also rule out an origin from the rotating infalling envelope" (Optically thin case)

## Software

- **CASA** : Spectral line imaging  
  > "Spectral line imaging was achieved with the CASA package" (Observations)
- **GILDAS** : Data analysis  
  > "while data analysis was performed using the GILDAS" (Observations)
- **JPL molecular database** : Line identification and transition frequencies, line strengths, Eu  
  > "From the JPL database (Pickett et al. 1998)." (Table 1)
- **LVG code by Ceccarelli et al. (2003)** : Non-LTE LVG modelling of HDO emission  
  > "a non-LTE LVG (Large Velocity Gradient) model using the code by Ceccarelli et al. (2003)" (HDO emission)
- **BASECOL database** : Source of HDO collisional coefficients  
  > "The collisional coefficients are extracted from the BASECOL database" (Footnote 3)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CH3CHO rotational temperature | 87 | +/-47 | K | 2 | which allows us to derive $T_{\rm rot}$ = 87$\pm$47 K |
| CH3CHO total column density | 2 +/- 1 x 10^15 | +/-1e15 (as stated) | cm^-2 | 2 | $N_{\rm tot}$ = 2$\pm$1 $\times$ 10$^{15}$ cm$^{-2}$ |
| CH3CHO opacity | less than 0.4 | not stated | dimensionless | 2 | With these values the opacity is less than 0.4. |
| CH3CHO column density increase for 0.06'' source size | about 20 (factor) | not stated | dimensionless | 2 | In the case of a smaller emitting size, e.g. 0$\ensuremath{''}$06 |
| CH3CHO fractional abundance | 0.2-2 x 10^-9 | range as stated | dimensionless | 4 | in agreement with the value recently derived in the IRAS16293-2422 hot corino |
| HDO column density limit at density 1e6 cm-3 (size 0.3'') | <= 7 x 10^15 | not stated | cm^-2 | 3 | then $N$(HDO) should be $\leq 7 \times 10^{15}$ cm$^{-2}$ |
| HDO column density limit at density 1e7 cm-3 (size 0.3'') | <= 7 x 10^16 | not stated | cm^-2 | 3 | at 10$^7$ cm$^{-3}$, $N$(HDO) has to be $\leq 7 \times 10^{16}$ cm$^{-2}$ |
| Minimum temperature at density 1e7 cm-3 | 230 | not stated | K | 3 | the temperature has to be larger than 230 K |
| HDO emitting size range (optically thick case) | 18-37 | not stated | AU | 5 | requiring a source size smaller than 0$\ensuremath{''}$08 (37 AU) and larger than 0$\ensuremath{''}$04 (18 AU) |
| Optically thick solution temperature range | 70-110 | not stated | K | 5 | The solution is, in this case, for temperatures between 70 K and 110 K |
| Optically thick solution density range | 1e9-1e10 | not stated | cm^-3 | 5 | and densities of $10^9$–$10^{10}$ cm$^{-3}$ |
| HDO column density at 100 K (optically thick, 0.06'' size) | 7 x 10^17 | not stated | cm^-2 | 5 | for a temperature around 100 K, $N$(HDO)$\sim 7 \times 10^{17}$ cm$^{-2}$ |
| HDO/H2 abundance ratio | 1.7e-6 to 1e-7 | not stated | dimensionless | 5 | corresponding to $N$(HDO)/$N$(H$_2$)=$1.7\times 10^{-6}$–$10^{-7}$ |
| HDO/H2O abundance ratio | 1.7e-2 to 1e-3 | not stated | dimensionless | 5 | would imply HDO/H$_2$O $\sim 1.7\times 10^{-2}$–$10^{-3}$ |
| HDO line profile peak velocity range | +1.2 to +2.0 | not stated | km/s | 0 | The line profiles peak in the +1.2,+2.0 km s |
| Line FWHM | 5-6 | not stated | km/s | 0 | which is also quite broad (FWHM |
| Blue vs red HDO peak brightness ratio in the disk test | factor of 2 difference | not stated | dimensionless | 5 | the large (factor of 2) difference between (i) the blue and red peak brightnesses |

## Qualitative findings

- First detection of a hot corino in Orion (HH212-MM1)  
  > "We report the first detection of a hot corino in Orion." (abstract)
- HDO low-velocity asymmetry indicates contribution of outflowing gas, possibly a dense disk wind  
  > "The HDO asymmetric profile indicates a contribution of outflowing gas from the compact central region, possibly associated with a dense disk wind." (abstract)
- Acetaldehyde abundance similar to hot corinos in Ophiuchus low-mass regions  
  > "The acetaldehyde abundance is similar to that measured in hot corinos located in low-mass star forming regions in Ophiuchus." (Conclusions)

## Claim tuples

- H: Does HH212-MM1 host a hot corino traced by high-excitation CH3CHO? | E: LTE optically thin rotational diagram of unblended CH3CHO lines, source size 0.3'' | R: Trot = 87+/-47 K and N = 2+/-1 x 10^15 cm^-2, opacity below 0.4 | F: Hot corino with CH3CHO abundance 0.2-2e-9 detected, first in Orion | **supported**
- H: Is the low-velocity HDO asymmetry caused by disk, envelope or outflow? | E: Optically thin HDO analysis with kinematic and spatial arguments, comparison with SiO and SO outflow data | R: Disk and infall origins not supported; asymmetry with redshifted peak brighter by about factor 2 | F: Most likely outflowing gas at 100 K from the inner region | **partially**
- H: Can the HDO line be optically thick, implying a very compact dense emitting region? | E: Non-LTE LVG grid with tau=1 curves, source size varied from 0.04'' to 0.08'' | R: Solution for 70-110 K, n 1e9-1e10 cm^-3, size 18-37 AU | F: Optically thick case implies extremely small dense region and slow outflow | **partially**

## Reasoning

- Why this data: Use the existing Early Science ALMA dataset of Codella et al. (2014) to probe the inner region of HH212 with high-excitation lines  
  > "we further exploit the ALMA dataset of Codella et al. (2014) to probe the inner region of HH212" (Introduction: The HH212 laboratory)
- Why this method: LTE for CH3CHO; non-LTE LVG for HDO because its profile may be optically thick  
  > "we compare the observed emission with that predicted by a non-LTE LVG (Large Velocity Gradient) model" (HDO emission)
- Alternative: Emission from the rotating disk (rejected: no non-axisymmetry of this level seen)  
  > "This would require a high degree of non-axisymmetry in the molecular disk emission" (Optically thin case)
- Alternative: Emission from the rotating infalling envelope (rejected: would be spatially resolved)  
  > "which would lead to spatially resolved peak emission, unlike the observed emission" (Optically thin case)
- Alternative: Optically thick infalling envelope (would give redshifted absorption)  
  > "because an optically thick infalling envelope would lead to redshifted absorption" (Optically thick case)
- How they decided it was enough: _not stated_
- Limitation (authors): Continuum cannot constrain H2 column because the submillimetre peak is optically thick  
  > "because the submillimetre continuum peak seen in interferometric maps is optically thick" (CH$_3$CHO emission)
- Limitation (authors): Emission is spatially unresolved, so the emitting size is assumed  
  > "Given that the CH$_3$CHO emission is spatially unresolved, we assume a source size equal to half a beam" (CH$_3$CHO emission)
- Caveat (inferred, ours): The CH3CHO temperature (87+/-47 K) and column have large uncertainty; the abundance range spans a factor of 10 from the assumed source size and an N(H2) taken from other sources.
- Caveat (inferred, ours): The HDO outflow interpretation rests on the asymmetry and is not uniquely determined; the optically thick solution is tuned to intersect the data by choosing source size.
- Caveat (inferred, ours): Abundance comparison with IRAS16293-2422 uses single-dish data, not comparable beam.
- Caveat (inferred, ours): The text states twelve CH3CHO lines but Table 1 lists only five, so the full line set is not reproducible from the paper.
- Caveat (inferred, ours): Systemic velocity choice (+1.3 vs +1.7 km/s) affects the velocity asymmetry argument.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Data identified by ADS/JAO.ALMA project 2011.0.000647.S  
  > "This paper makes use of the ADS/JAO.ALMA#2011.0.000647.S data (PI: C. Codella)." (Acknowledgements)
- Missing: Imaging and continuum subtraction settings (weighting, cell size, channel binning, line-free channels).
- Missing: CASA and GILDAS versions.
- Missing: Full list of CH3CHO lines (only five in Table 1 though twelve are cited).
- Missing: Rotational diagram fit details and uncertainty method.
- Missing: D/H elemental abundance value and H2 column derivation used in the LVG grid.
- Missing: Exact LVG code inputs (kinetic temperature grid, H2 ortho/para ratio, line widths).
- Data volume (inferred): Not stated; a single ALMA Cycle 0 spectral setup over two windows of about 3.7 GHz each at 850 um with 0.44 km/s channels, likely several GB of visibilities.
- Score (inferred): 5/5, Observation, line lists and key numeric results are given, but imaging parameters, continuum subtraction, calibration versions and the full CH3CHO line set are missing.
- Rediscovery candidate: no, Data identity is given, but the paper does not state the data are public, and imaging and LVG inputs are incomplete, so a faithful redo is not assured.

## Links

- Method: Ceccarelli et al. 2003 (cite: cecilia03) (Non-LTE LVG code used for HDO modelling)
- Method: Faure et al. 2012 (cite: faure) (HDO-H2 collisional coefficients)
- Method: Dubernet et al. 2013 (cite: dubernet) (BASECOL database source of collisional coefficients)
- Method: Pickett et al. 1998 (cite: pickett) (JPL line database used for line identification)
- Companion: Codella et al. 2014 (cite: codella14) (Source of the ALMA Early Science dataset and C34S results)
- Companion: Podio et al. 2015 (cite: podio15) (SO and SiO outflow data from the same ALMA dataset)
- Companion: Lee et al. 2014 (cite: lee14) (Systemic velocity and disk density estimates for HH212)
- Companion: Taquet et al. 2015 (cite: taquet15) (N(H2) for NGC1333-IRAS2A and IRAS4A used for abundance)
- Related: ALMA Early Science Cycle 0 observations of HH212 (Codella et al. 2014)

## Checks

```json
{
 "quotes": 101,
 "quotes_ok": 101,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.0.000647.S"
 ],
 "obscore_codes_not_in_card": [
  "2011.0.00647.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 17,
 "numeric_problems": 0,
 "fill": {
  "facts": 98,
  "stated": 73,
  "rate": 0.745
 },
 "evidence_ok": true
}
```

## Figures

- **Figure 1** (moment_map, 3 panel(s), data): Upper panel shows the HH212 system in SiO(8-7) blue- and redshifted jet contours over the 0.9 mm continuum of MM1; middle and bottom panels zoom on the central region with CH3CHO(18,18-17,17)A and HDO integrated emission (green contours and grey scale) overlaid on the SiO jet.
  - axes: x: R.A. offset [arcsec]; y: Dec offset [arcsec]; contours: integrated line emission / continuum / SiO jet velocity-channel emission [not labelled]
  - supports step 1
  - read off the plot: approx. CH3CHO and HDO emission centred on MM1 within about 0.2 arcsec of the continuum peak; approx. scale bar 180 AU corresponds to about 1 arcsec
  - reproduction target
- **Figure 2** (spectrum, 4 panel(s), data, model): CH3CHO emission extracted at the MM1 position in four frequency windows, in brightness temperature, with the LTE optically thin synthetic spectrum (red) that best reproduces the lines.
  - axes: x: frequency [MHz]; y: brightness temperature T_B [K]
  - supports step 2
  - validation: Synthetic LTE spectrum overlaid on observed lines checks the adopted excitation temperature and column density against the data.
  - read off the plot: approx. peak line intensity about 0.4 K in the 347.6 GHz window; approx. model Trot 87 K and NCH3CHO 2e15 cm-2 as stated in the figure; approx. FWHM linewidth 5.0 km/s used in model
  - reproduction target
- **Figure 3** (spectrum, 1 panel(s), data): Comparison of the HDO(3_3,1-4_2,2) line (black) with the CH3CHO(18_0,18-17_0,17)A line (red, scaled by 1.6) towards HH212-MM1 as a function of velocity relative to systemic velocity.
  - axes: x: LSR velocity relative to Vsys [km/s]; y: brightness temperature T_B [K]
  - supports step 5
  - read off the plot: approx. peak brightness about 0.7 K near 0 to +1 km/s for both lines; approx. blueshifted wing extending to about -6 km/s
  - reproduction target
- **Figure 4** (model_vs_data, 2 panel(s), model): LVG predictions of gas temperature versus HDO column density that reproduce the observed velocity-integrated emission (solid curves) and give unit line opacity (dashed curves), for four H2 densities, for source sizes 0.3 arcsec (upper) and 0.06 arcsec (lower).
  - axes: x: HDO column density [cm-2]; y: temperature [K]; curve parameter: density [cm-3]
  - supports step 3
  - read off the plot: approx. temperature 50 to 250 K range on y-axis; approx. HDO column density 1e16 to 1e18 cm-2 range on x-axis; approx. density curves labelled 1e7, 1e8, 1e9, 1e10 cm-3

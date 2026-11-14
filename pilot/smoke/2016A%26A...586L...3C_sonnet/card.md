# Water and acetaldehyde in HH212: The first hot corino in Orion

`2016A&A...586L...3C` | Astronomy and Astrophysics 2016 | first author: Codella, C. | arXiv: 1601.00539 | DOI: 10.1051/0004-6361/201527424

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, astrochemistry
- Question: Whether and how hot corinos, circumstellar disks and ejected gas are related in the Class 0 protostar HH212-MM1, probed by CH3CHO and HDO lines  
  > "we aim to investigate whether and how hot corinos, circumstellar disks, and ejected gas are related in young solar-mass protostars." (abstract)
- Target **HH212-MM1**: coordinates RA(J2000) 05h43m51.41s, Dec -01d02m53.17s (continuum peak, Lee et al. 2014)  
  > "HH212 is located in Orion (at 450 pc)" (Introduction: The HH212 laboratory); "Positions are given with respect to the MM1 protostar continuum peak located at $\alpha({\rm J2000})$ = 05$^h$ 43$^m$ 51$s$41" (Observations); z/distance 450 pc  
  > "HH212 is located in Orion (at 450 pc)" (Introduction: The HH212 laboratory); "Positions are given with respect to the MM1 protostar continuum peak located at $\alpha({\rm J2000})$ = 05$^h$ 43$^m$ 51$s$41" (Observations); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.000647.S
- bands: 850 um (Band 7)  
  > "HH212 was observed at 850 $\mu$m with ALMA using 24 12 m antennas on 2012 December 1" (Observations)
- frequencies and spectral setup: spectral windows 333.7-337.4 GHz and 345.6-349.3 GHz; 488 kHz units (0.42-0.44 km/s)  
  > "The spectral windows 333.7–337.4 GHz and 345.6–349.3 GHz were observed using spectral units of 488 kHz (0.42–0.44 km s$^{-1}$)." (Observations)
- continuum bandwidth: _not stated_
- arrays: 24 12 m antennas  
  > "HH212 was observed at 850 $\mu$m with ALMA using 24 12 m antennas on 2012 December 1" (Observations)
- configurations: _not stated_
- baselines: 20 m to 360 m  
  > "The baselines were between 20 m and 360 m with a maximum unfiltered scale of 3$\ensuremath{''}$." (Observations)
- angular resolution: 0.65" x 0.47" (PA = 35 deg)  
  > "The continuum-subtracted images have a typical clean-beam FWHM of $0.65\ensuremath{''}\times0.47\ensuremath{''}$ (PA = 35$\ensuremath{^\circ}$)" (Observations)
- max recoverable scale: 3"  
  > "The baselines were between 20 m and 360 m with a maximum unfiltered scale of 3$\ensuremath{''}$." (Observations)
- sensitivity: rms 3-4 mJy/beam in 0.44 km/s channels  
  > "an rms noise level of 3–4 mJy beam$^{-1}$ in 0.44 km s$^{-1}$ channels" (Observations)
- time on source: _not stated_
- observing dates: 2012 December 1 (Cycle 0 Early Science)  
  > "HH212 was observed at 850 $\mu$m with ALMA using 24 12 m antennas on 2012 December 1 (Early Science Cycle 0 phase; Codella et al. 2014)." (Observations)
- pi or archival as stated: Data of PI C. Codella, reused from Codella et al. (2014)  
  > "This paper makes use of the ADS/JAO.ALMA#2011.0.000647.S data (PI: C. Codella)." (Acknowledgements)
- Line: CH3CHO 18(0,18)-17(0,17) A and other lines (12 detected, Eu 150-200 K) (335358.7 MHz (for 18(0,18)-17(0,17) A))
- Line: HDO 3(3,1)-4(2,2) (335395.5 MHz)
- External data: Spectroscopic line parameters from JPL database  
  > "The lines were identified using the Jet Propulsion Laboratory (JPL) molecular database (Pickett et al. 1998)." (Results and discussion) [from Pickett et al. 1998]
- External data: HDO-H2 collisional coefficients  
  > "the collisional coefficients for the system HDO-H$_2$ computed by Faure et al. (2012)" (HDO emission) [from Faure et al. (2012)]
- External data: N(H2) ~1e24-1e25 cm-2 from NGC1333-IRAS2A and IRAS4A hot corinos used to derive CH3CHO abundance  
  > "Taquet et al. (2015) measured N(H$_2$) $\simeq$ 10$^{24}$–10$^{25}$ cm$^{-2}$ towards the NGC1333-IRAS2A and IRAS4A hot corinos" (CH3CHO emission) [from Taquet et al. (2015)]
- External data: Systemic velocity +1.7 km/s  
  > "we adopt here +1.7 km s$^{-1}$ (Lee et al. 2014)" (Footnote 2) [from Lee et al. 2014]

## Processing

### Calibration

- pipeline or manual: Standard procedures; quasars J0538-440, J0607-085, Callisto, Ganymede  
  > "Calibration was carried out following standard procedures, using quasars J0538–440, J0607–085, Callisto, and Ganymede." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: Spectral line imaging with CASA  
  > "Spectral line imaging was achieved with the CASA package, while data analysis was performed using the GILDAS[^1] package." (Observations)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Images are continuum-subtracted  
  > "The continuum-subtracted images have a typical clean-beam FWHM" (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.65" x 0.47", PA 35 deg  
  > "typical clean-beam FWHM of $0.65\ensuremath{''}\times0.47\ensuremath{''}$ (PA = 35$\ensuremath{^\circ}$)" (Observations)
- final rms: 3-4 mJy/beam per 0.44 km/s channel  
  > "an rms noise level of 3–4 mJy beam$^{-1}$ in 0.44 km s$^{-1}$ channels" (Observations)

### Inherited from earlier work

- Observations and calibration of the dataset  
  > "(Early Science Cycle 0 phase; Codella et al. 2014)" (Observations) [from Codella et al. 2014]
- MM1 continuum peak position  
  > "Positions are given with respect to the MM1 protostar continuum peak" (Observations) [from Lee et al. 2014]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration details (bandpass/phase/gain calibrators, flux scale)
- Imaging parameters: weighting/robust, cell and image size, deconvolver, masks
- Line-free channels used for continuum subtraction
- Line-by-line blending assessment and integration windows for Table 1
- Number of spectral windows' full line list (only unblended lines in Table 1 are partly shown)
- LVG code input details (linewidth, geometry specifics, o/p ratio) beyond what is given

## Analysis recipe

1. **Image spectral lines and extract spectra**: CASA line imaging, continuum-subtracted; spectra at MM1 analysed in GILDAS  
  > "Spectral line imaging was achieved with the CASA package, while data analysis was performed using the GILDAS[^1] package." (Observations)
   - software: CASA, GILDAS
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify lines**: Compare with JPL database  
  > "The lines were identified using the Jet Propulsion Laboratory (JPL) molecular database (Pickett et al. 1998)." (Results and discussion)
   - software: JPL database
   - fitting: _not stated_
   - validation: _not stated_
3. **CH3CHO LTE rotational diagram**: Optically thin LTE analysis using lines with <30% blend contamination  
  > "An LTE (Local Thermodynamic Equilibrium) optically thin analysis of CH$_3$CHO (using only lines with less than 30% contamination from blended lines" (CH3CHO emission)
   - parameter: Source size 0.3" (half a beam)  
  > "we assume a source size equal to half a beam, namely 0$\ensuremath{''}$3" (CH3CHO emission)
   - assumption: Unresolved emission; source size = half beam  
  > "Given that the CH$_3$CHO emission is spatially unresolved, we assume a source size equal to half a beam, namely 0$\ensuremath{''}$3." (CH3CHO emission)
   - fitting: _not stated_
   - validation: Synthetic spectra compared with observed (Fig. 2); opacity <0.4  
  > "With these values the opacity is less than 0.4." (CH3CHO emission)
4. **Estimate CH3CHO abundance**: Divide N(CH3CHO) by N(H2) taken from Taquet et al. (2015) hot corinos, since continuum is optically thick  
  > "If we take these values and 0$\ensuremath{''}$3 as emitting size, then $X_{\rm CH_3CHO}$ $\sim$ 0.2–2 $\times$ 10$^{-9}$" (CH3CHO emission)
   - assumption: N(H2) of IRAS2A/IRAS4A applicable (scale ~3 times larger than sampled here)  
  > "i.e. a factor $\sim$ 3 higher than is sampled here" (CH3CHO emission)
   - fitting: _not stated_
   - validation: Compared with IRAS16293-2422 value of 3e-9 (Jaber et al. 2014)  
  > "in agreement with the value recently derived in the IRAS16293-2422 hot corino" (CH3CHO emission)
5. **HDO non-LTE LVG modelling**: LVG code of Ceccarelli et al. (2003), plane-parallel geometry, HDO-H2 rates of Faure et al. (2012), Boltzmann o/p H2; T vs N(HDO) for densities 1e7-1e10 cm-3, optically thin and thick cases (tau=1 curves)  
  > "non-LTE LVG (Large Velocity Gradient) model using the code by Ceccarelli et al. (2003), a plane parallel geometry" (HDO emission)
   - software: LVG code (Ceccarelli et al. 2003)
   - parameter: Source sizes 0.3" and 0.06"; N(HDO)/N(H2) <= 3.2e-6  
  > "namely $N$(HDO)/$N$(H$_2$) $\leq 3.2 \times 10^{-6}$" (HDO emission)
   - assumption: HDO abundance <10% of D/H; initial H2O abundance 3e-5  
  > "assuming an initial H$_2$O abundance of 3 $\times$ 10$^{-5}$" (HDO emission)
   - fitting: _not stated_
   - validation: HDO/H2O ratio compared with values in hot corinos  
  > "consistent with the values measured in hot corinos (Persson et al. 2014; Ceccarelli et al. 2015)" (Optically thick case)

## Software

- **CASA** : Spectral line imaging  
  > "Spectral line imaging was achieved with the CASA package" (Observations)
- **GILDAS** : Data analysis  
  > "data analysis was performed using the GILDAS[^1] package" (Observations)
- **LVG code (Ceccarelli et al. 2003)** : Non-LTE HDO modelling  
  > "non-LTE LVG (Large Velocity Gradient) model using the code by Ceccarelli et al. (2003)" (HDO emission)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CH3CHO rotational temperature | 87 | ±47 | K | 3 | indicates temperature of 87$\pm$47 K and a column density of 2$\pm$1 $\times$ 10$^{15}$ cm$^{-2}$ |
| CH3CHO column density | 2e15 | ±1e15 | cm^-2 | 3 | indicates temperature of 87$\pm$47 K and a column density of 2$\pm$1 $\times$ 10$^{15}$ cm$^{-2}$ |
| CH3CHO abundance | 0.2-2e-9 | not stated | dimensionless | 4 | $X_{\rm CH_3CHO}$ $\sim$ 0.2–2 $\times$ 10$^{-9}$ |
| HDO column density (optically thick, T~100 K, size 0.06") | ~7e17 | not stated | cm^-2 | 5 | for a temperature around 100 K, $N$(HDO)$\sim 7 \times 10^{17}$ cm$^{-2}$ |
| HDO emitting size, optically thick case | 18-37 | not stated | AU | 5 | a size $\simeq$ 18–37 AU, $T_{\rm kin}$ $\simeq$ 100 K, and $n_{\rm H_2}$ $\geq$ 10$^9$ cm$^{-3}$ |
| HDO/H2O ratio (optically thick) | 1.7e-2 to 1e-3 | not stated | dimensionless | 5 | would imply HDO/H$_2$O $\sim 1.7\times 10^{-2}$–$10^{-3}$ |

## Qualitative findings

- CH3CHO and HDO emission is unresolved at MM1; first hot corino detected in Orion  
  > "We thus report the detection of the first hot corino in Orion." (Conclusions)
- Asymmetric HDO profile at low velocities indicates slow outflowing gas, possibly a disk wind  
  > "at least some of the deuterated water is associated with slow outflowing gas" (Conclusions)

## Claim tuples

- H: HH212-MM1 hosts a hot corino | E: Detect high-Eu CH3CHO and HDO lines and analyse with LTE and LVG | R: 12 CH3CHO lines and 1 HDO line detected; T~87 K, N~2e15 cm-2 | F: First hot corino in Orion detected | **supported**
- H: The low-velocity HDO emission traces outflowing gas | E: Compare HDO profile asymmetry with LVG predictions in thin and thick cases | R: Redshifted emission brighter; disk and envelope disfavoured; optically thick requires 18-37 AU, n>=1e9 cm-3 | F: HDO associated with slow outflow, possibly a disk wind | **partially**

## Reasoning

- Why this data: HH212 hosts both a bright jet and compact rotating disk, ideal for linking hot corino, disk and outflow  
  > "HH212 stands out as being the perfect target for investigating the link between hot corino, disk, and outflow in the protostellar stage." (Introduction: The HH212 laboratory)
- Why this method: _not stated_
- Alternative: HDO from rotating disk or infalling envelope rejected in optically thin case  
  > "We can also rule out an origin from the rotating infalling envelope" (Optically thin case)
- How they decided it was enough: _not stated_
- Limitation (authors): Continuum optically thick, so H2 column and abundance cannot be derived directly  
  > "we cannot use the continuum emission to estimate the H$_2$ column density" (CH3CHO emission)
- Limitation (authors): Emission spatially unresolved  
  > "CH$_3$CHO and HDO are only observed towards the protostellar position and are spatially unresolved" (Results and discussion)
- Caveat (inferred, ours): Source sizes are assumed, not measured
- Caveat (inferred, ours): Abundance relies on N(H2) from other sources at different scales
- Caveat (inferred, ours): HDO interpretation depends on unconstrained optical depth
- Caveat (inferred, ours): Few unblended lines limit rotational diagram constraints (T = 87±47 K)

## Reproducibility

- Data public (paper): ALMA Cycle 0 data 2011.0.000647.S used; archival reuse  
  > "This paper makes use of the ADS/JAO.ALMA#2011.0.000647.S data (PI: C. Codella)." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: Line integration windows and blending criteria
- Missing: LVG code access and exact input setup
- Data volume (inferred): ~20-50 GB (single Cycle 0 Band 7 execution)
- Score (inferred): 3/5, Public data and simple LTE analysis are reproducible, but imaging details and the in-house LVG code settings are missing.
- Rediscovery candidate: no, Imaging recipe is incomplete and the LVG code is not public, though the data are public and results numeric.

## Links

- Method: Ceccarelli et al. (2003) (LVG code)
- Method: Faure et al. (2012) (HDO-H2 collisional coefficients)
- Companion: Codella et al. (2014) (Original description of the ALMA dataset)
- Companion: Podio et al. (2015) (SiO and SO from same dataset)
- Companion: Lee et al. (2014) (Disk and envelope of HH212 from ALMA)

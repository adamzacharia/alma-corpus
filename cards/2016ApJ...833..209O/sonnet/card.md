# Dense Core Properties in the Infrared Dark Cloud G14.225-0.506 Revealed by ALMA

`2016ApJ...833..209O` | The Astrophysical Journal 2016 | first author: Ohashi, Satoshi | arXiv: 1610.08581 | DOI: 10.3847/1538-4357/833/2/209

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: What are the properties (masses, virial state, mass function) of dense cores in the IRDC G14.225-0.506 hub-filament systems, and what do they imply for high-mass star formation?  
  > "In this paper, we report ALMA observations of the 3 mm continuum emission." (Introduction)
- Target **G14.225-0.506 (M17 SWex)**: coordinates _not stated_; z/distance 1.98 kpc  
  > "Recent measurements of parallaxes and proper motions using CH$_3$OH masers determine a distance of 1.98 kpc (cite: xu11; wu14)." (Introduction); distance from CH3OH maser parallaxes (Xu et al. 2011; Wu et al. 2014)  
  > "Recent measurements of parallaxes and proper motions using CH$_3$OH masers determine a distance of 1.98 kpc (cite: xu11; wu14)." (Introduction)

## Data provenance

- ALMA projects: 2013.1.00312.S
- bands: Band 3 (103 GHz for continuum)  
  > "The observations employed the Band 3 (103 GHz for continuum) receivers" (Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12-m array (37 antennas) and ACA 7-m (10 antennas)  
  > "in the C34-2/1 configuration with a total of 37 antennas and with the ACA (7-m Array antennas) on 2015 April $29-30$ and May 4 with a total of 10 antennas" (Observations)
- configurations: _not stated_
- baselines: 10 to 346 m  
  > "The projected baselines range from 10 to 346 m (including 7-m and 12-m arrays)." (Observations)
- angular resolution: 3.7x2.0 arcsec (field N), 3.1x2.1 arcsec (field S)  
  > "The achieved synthesized beams were $3.7\ensuremath{''}\times2.0\ensuremath{''}$ in field N and $3.1\ensuremath{''}\times2.1\ensuremath{''}$ in field S." (Observations)
- max recoverable scale: 26 arcsec (~0.25 pc)  
  > "the largest angular scale (LAS) recoverable by the 12 and 7-m arrays is 26$\ensuremath{''}$ ($\sim0.25$ pc)" (Observations)
- sensitivity: rms 0.2 mJy/beam before primary beam correction  
  > "The rms noise level for the combined data is 0.2 mJy beam$^{-1}$ before the primary beam correction." (Observations)
- time on source: about 1.7 hr total for the 12-m array including calibration  
  > "Including time for calibration, the total observing time was about 1.7 hr for the 12-m Array." (Observations)
- observing dates: 12-m: 2015 April 25; ACA: 2015 April 29-30 and May 4  
  > "G14.2 was observed with the ALMA 12-m array on 2015 April 25" (Observations)
- pi or archival as stated: Cycle 2 program, PI Vivien Chen  
  > "(Cycle 2 program, Project ID:2013.1.00312.S; PI: Vivien Chen)" (Observations)
- Line: N2H+ J=1-0 (not stated)
- Other facility **APEX**: 870 um continuum for clumps  
  > "Using APEX 870 $\mu$m continuum emission, we also identified the 18 clumps hosting these cores." (abstract)
- Other facility **VLA/Effelsberg**: NH3 lines for temperatures and clump linewidths  
  > "Through virial analysis using the ALMA N$_2$H$^+$ and VLA/Effelsberg NH$_3$ molecular line data" (abstract)
- Other facility **SMA**: 1.3 mm continuum comparison from Busquet et al. 2016  
  > "Recently, (cite: bus16) observed 1.3 mm continuum emission toward the hub-N and hub-S regions with the Submillimeter Array (SMA)." (Core properties)
- Other facility **Spitzer/Chandra/MIPSGAL**: YSO and X-ray source catalogs and 24um emission  
  > "the YSOs catalog of (cite: pov16); ii) the presence or absence of 24 $\mu$m emission using the MIPSGAL survey (cite: car09)" (Core properties)
- External data: Kinetic temperatures from NH3, NH3 linewidths, 870 um APEX maps, filament virial parameters  
  > "For the dust temperature, we use the kinetic temperature, $T_{\rm kin}$, derived from NH$_3$ ($J,K$) $=$ ($1,1$) and $(2,2)$ emission lines (cite: bus13)." (Core properties) [from (cite: bus13)]
- External data: YSO and X-ray source catalog  
  > "The ID numbers of YSOs and X-ray sources are adopted from (cite: pov16)." (Core properties) [from (cite: pov16)]
- External data: N2H+ linewidths of cores  
  > "The linewidths are measured from N$_2$H$^+$ (J=1-0) ALMA observations (Chen et al. in prep)." (Table 1) [from Chen et al. 2016, in prep]

## Processing

### Calibration

- pipeline or manual: CASA, standard manner; delivered by East Asia ARC  
  > "The reduction and calibration of the data were done with CASA version 4.3.1 (cite: mcm07) in standard manners, and the data were delivered from the East Asia ALMA Regional Center." (Observations)
- casa version: CASA 4.3.1  
  > "CASA version 4.3.1" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune and Ceres; bandpass/phase J1733-1304 and J1924-2914  
  > "Flux calibration was performed using Neptune and Ceres." (Observations)
- flux scale uncertainty: 5% in Band 3  
  > "The uncertainty of absolute flux calibration is 5% in Band 3 according to ALMA Cycle 2 Technical Handbook." (Observations)
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN  
  > "All images of continuum emission were reconstructed with the CASA task CLEAN using natural weighting." (Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "All images of continuum emission were reconstructed with the CASA task CLEAN using natural weighting." (Observations)
- uv taper: _not stated_
- cell size: 0.4 arcsec  
  > "The pixel size was set to $0.4\ensuremath{''}$." (Observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12-m and ACA combined in the uv plane in CASA  
  > "ALMA 12-m Array and ACA data sets were combined in the uv plane in CASA." (Observations)
- smoothing: _not stated_
- final beam: 3.7x2.0 (N), 3.1x2.1 arcsec (S)  
  > "The achieved synthesized beams were $3.7\ensuremath{''}\times2.0\ensuremath{''}$ in field N and $3.1\ensuremath{''}\times2.1\ensuremath{''}$ in field S." (Observations)
- final rms: 0.2 mJy/beam  
  > "The rms noise level for the combined data is 0.2 mJy beam$^{-1}$ before the primary beam correction." (Observations)

### Inherited from earlier work

- Core temperatures, filament virial parameters, NH3 and 870um data  
  > "We also refer to the virial parameters of the parent filaments derived by (cite: bus13)." (Dynamical State of the Cores) [from (cite: bus13)]
- LAS computed following Palau et al. eq. A5  
  > "Following equation A5 of (cite: pal10), the largest angular scale (LAS) recoverable by the 12 and 7-m arrays is 26$\ensuremath{''}$" (Observations) [from (cite: pal10)]
- Dust opacity from Ossenkopf & Henning, kappa(2.9mm)=0.276 following Stephens et al.  
  > "we obtain $\kappa_{\rm 2.9 mm}=0.276$ cm$^2$ g$^{-1}$ (cite: ste15)" (Core properties) [from (cite: oss94; ste15)]

### Not stated but needed to reproduce (our reading)

- Clumpfind implementation and exact parameters/mask handling
- Line-free channels and continuum bandwidth used for the 3 mm map
- CLEAN threshold, iterations and masks
- N2H+ hyperfine fitting details (in Chen et al. in prep)
- Procedure for the size deconvolution and FWHM radius
- Fitting method for the CMF slope (binning, range choice)
- Which clumps' tmperature values were adopted per core

## Analysis recipe

1. **Image combined 12-m+ACA continuum**: CASA CLEAN, natural weighting, 0.4 arcsec pixels  
  > "All images of continuum emission were reconstructed with the CASA task CLEAN using natural weighting." (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify dense cores**: Clumpfind with 2 sigma threshold and 2 sigma steps; keep peaks above 5 sigma  
  > "Therefore, we choose the threshold and stepsize of 2$\sigma$. Furthermore, we only consider cores having peak intensities above the $5\sigma$ noise level as robust detections." (Core properties)
   - software: Clumpfind
   - fitting: _not stated_
   - validation: Cite tests of threshold dependence by Pineda et al. and Ikeda & Kitamura  
  > "(cite: ike09) also showed that the power-law index remains unchanged for thresholds of $2-4$$\sigma$ and stepsizes of $2-3.5$$\sigma$ in the Orion A cloud." (Core properties)
3. **Classify protostellar vs prestellar**: Core is protostellar if a YSO or X-ray source lies within 4 arcsec of core centre  
  > "If these sources are inside a circle of radius 4$\ensuremath{''}$ from the center position of the core, the core is defined as protostellar." (Core properties)
   - assumption: YSO age 0.1 Myr, velocity dispersion width 0.8 km/s  
  > "Assuming YSO ages of 0.1 Myr (cite: pov10) and a width of the velocity dispersion of 0.8 km s$^{-1}$" (Core properties)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive core masses**: M = F d^2 / (kappa B_nu(Td)) x f_d  
  > "M_{\rm core}=\frac{F_\nu d^2}{\kappa B_\nu(T_d)}f_d" (Core properties)
   - assumption: gas-to-dust 100, kappa=0.9(lambda/1.3mm)^beta cm2/g, beta=1.5; default T 22 K protostellar, 17 K prestellar  
  > "we adopt the average value of 22 K for protostellar cores and 17 K for prestellar cores candidates in this region." (Core properties)
   - fitting: _not stated_
   - validation: _not stated_
5. **Virial analysis of cores, clumps, filaments**: Mvir=210 r dv^2 (uniform density); alpha=Mvir/Mcore; clumps from APEX 870um via Clumpfind with NH3 linewidths  
  > "The virial parameter, $\alpha_{\rm virial}$, is derived by $\alpha_{\rm virial}=M_{\rm vir}/M_{\rm core}$." (Dynamical State of the Cores)
   - software: Clumpfind
   - assumption: uniform density sphere; magnetic fields neglected  
  > "The virial analysis performed above neglects effects of magnetic fields, which can increase the virial mass." (Dynamical State of the Cores)
   - fitting: hyperfine fitting of N2H+ spectra  
  > "by performing hyperfine fitting to the N$_2$H$^+$ spectra" (Dynamical State of the Cores)
   - validation: _not stated_
6. **Fit cumulative CMF of prestellar candidates**: N(>M)=kM^-alpha+c fit with Poisson errors N^1/2, mass range 2.4-14 Msun  
  > "The power-law index $\alpha$ of the CMF is derived to be $1.6\pm0.7$ using the mass range from 2.4 to 14 $M_\odot$" (Core Mass Function)
   - fitting: power-law fit with Poisson weights  
  > "taking into account the counting uncertainties (poisson noise) of $N^{1/2}$" (Core Mass Function)
   - validation: compared with Salpeter slope alpha=1.35  
  > "The dashed lines represent the slope of the Salpeter IMF ($\alpha=1.35$)." (Core Mass Function)

## Software

- **CASA** 4.3.1: calibration, uv combination and CLEAN imaging  
  > "CASA version 4.3.1 (cite: mcm07)" (Observations)
- **Clumpfind** : identifying cores and APEX clumps  
  > "we apply the Clumpfind method (cite: wil94) to the ALMA 3 mm images" (Core properties)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of dense cores | 48 | not stated | dimensionless | 2 | We identify a total of 48 cores (29 in the northern part and 19 in the southern part). |
| Protostellar / prestellar cores | 20 / 28 | not stated | dimensionless | 3 | we identify 20 protostellar cores and 28 prestellar cores candidates |
| Core mass range | 1.1 to 78 | not stated | Msun | 4 | As a result, the core mass ranges from 1.1 to 78 $M_\odot$. |
| Core virial parameters | 0.1-1.3 | not stated | dimensionless | 5 | The virial parameters of the dense cores are between 0.1 and 1.3 |
| CMF cumulative slope alpha | 1.6 | 0.7 | dimensionless | 6 | derived to be $1.6\pm0.7$ using the mass range from 2.4 to 14 $M_\odot$ |
| Max stellar mass expected (SFE 10%, 30%) | 40 and 47 | not stated | Msun | 0 | we derive the maximum stellar mass to be **40 and 47 $M_\odot$, respectively** |

## Qualitative findings

- Virial parameter decreases from filaments (mean 2.3) to clumps (mean 1.0) to cores (<1)  
  > "We find a tendency showing that $\alpha_{\rm virial}$ decreases with decreasing size scales." (Dynamical State of the Cores)
- No massive prestellar or protostellar cores found  
  > "We find no massive prestellar or protostellar cores." (abstract)

## Claim tuples

- H: Are dense cores in G14.2 in virial equilibrium? | E: Virial parameters from ALMA N2H+ linewidths and 3 mm sizes/masses | R: Core alpha 0.1-1.3, mostly <1 | F: Cores likely undergoing dynamical collapse unless strongly magnetized | **supported**
- H: Is the prestellar CMF similar to the Salpeter IMF? | E: Cumulative CMF fit of 28 prestellar candidates | R: alpha=1.6±0.7, deficit at high mass end | F: CMF similar to IMF but lacking massive cores | **partially**
- H: How do high-mass stars form in G14.2? | E: Compare maximum expected stellar mass with core masses | R: No massive cores; high SFE needed | F: Consistent with global hierarchical collapse/competitive accretion, not firmly proven | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Clumpfind with 2 sigma threshold justified by isolated emission and prior tests  
  > "In our observations, the 3 mm continuum emission is relatively isolated and the clumpfind method is reliable to identify cores." (Core properties)
- How they decided it was enough: _not stated_
- Limitation (authors): Extended filament emission resolved out; cannot rule out deeply embedded low-mass protostars; core sizes assumed compact  
  > "This may be explained by the combined effect of resolving out extended emission from the filaments that have lengths longer than 1 pc ($\sim90\ensuremath{''}$) and insufficient sensitivity." (Results)
- Caveat (inferred, ours): Temperatures from 8-22 arcsec NH3 applied to ~3 arcsec cores
- Caveat (inferred, ours): Virial parameters depend on uncertain N2H+ linewidths from unpublished paper
- Caveat (inferred, ours): CMF slope uncertainty large (±0.7) with small sample
- Caveat (inferred, ours): Clumpfind-based masses sensitive to blending and missing flux

## Reproducibility

- Data public (paper): ALMA data cited by project code (archive acknowledged)  
  > "This paper makes use of the ALMA data: ADS/JAO.ALMA 2013.1.00312.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Chen et al. N2H+ linewidth data
- Missing: Clumpfind parameter files
- Missing: Table of per-core temperatures from Busquet 2013 already in Table 1
- Data volume (inferred): ~20-50 GB (12-m + ACA Band 3 mosaic with line cubes)
- Score (inferred): 3/5, Public data and a clear recipe for continuum cores and masses, but N2H+ linewidths and several imaging parameters are not given.
- Rediscovery candidate: yes, Public data, core table in the paper gives numeric answer keys, continuum recipe largely stated.

## Links

- Method: Williams et al. 1994 (cite: wil94) (Clumpfind algorithm)
- Companion: Chen et al. 2016, in prep (N2H+ line data from same ALMA project)
- Companion: (cite: bus13) (NH3 and 870um data, filament identification)
- Companion: (cite: bus16) (SMA 1.3 mm observations)
- Companion: (cite: pov16) (YSO and X-ray catalog)
- Related: MIPSGAL
- Related: GLIMPSE
- Related: UKIDSS GPS
- Related: Chandra

## Checks

```json
{
 "quotes": 64,
 "quotes_ok": 64,
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
  "facts": 79,
  "stated": 52,
  "rate": 0.658
 },
 "evidence_ok": true
}
```

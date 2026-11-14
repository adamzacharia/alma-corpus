# ALMA Resolves the Torus of NGC 1068: Continuum and Molecular Line Emission

`2016ApJ...823L..12G` | The Astrophysical Journal Letters 2016 | first author: García-Burillo, S. | arXiv: 1604.00205 | DOI: 10.3847/2041-8205/823/1/L12

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: Can ALMA Band 9 at ~4 pc resolution resolve the dust and molecular gas torus of NGC 1068, and what are its mass, size, orientation and kinematics?  
  > "These observations spatially resolve the CND and, for the first time, image the dust emission, the molecular gas distribution, and the kinematics" (abstract)
- Target **NGC 1068 (the name is missing from the text; the Seyfert 2 galaxy)**: coordinates 02h42m40.771s, -00d00m47.84s (phase center, J2000)  
  > "Given the distance to the galaxy ($D\sim14$ Mpc; (cite: Bla97)), which implies a scale $\sim$70 pc/$\ensuremath{''}$" (1 Introduction); "($\alpha_{2000}, \delta_{2000}$) = ($02^{h}42^{m}40.771^{s}, -00^{\circ}00^{\prime}47.84\ensuremath{''}$)" (2 ALMA observations and data reduction); z/distance D ~14 Mpc  
  > "Given the distance to the galaxy ($D\sim14$ Mpc; (cite: Bla97)), which implies a scale $\sim$70 pc/$\ensuremath{''}$" (1 Introduction); "($\alpha_{2000}, \delta_{2000}$) = ($02^{h}42^{m}40.771^{s}, -00^{\circ}00^{\prime}47.84\ensuremath{''}$)" (2 ALMA observations and data reduction); distance from Bland-Hawthorn et al. 1997 (cite: Bla97)  
  > "Given the distance to the galaxy ($D\sim14$ Mpc; (cite: Bla97)), which implies a scale $\sim$70 pc/$\ensuremath{''}$" (1 Introduction); "($\alpha_{2000}, \delta_{2000}$) = ($02^{h}42^{m}40.771^{s}, -00^{\circ}00^{\prime}47.84\ensuremath{''}$)" (2 ALMA observations and data reduction)

## Data provenance

- ALMA projects: 2013.1.00055.S
- bands: Band 9 (432 um continuum, 694 GHz)  
  > "using the Band 9 receiver (project-ID: $\#$2013.1.00055.S)" (2 ALMA observations and data reduction)
- frequencies and spectral setup: Four spectral windows of 1.875 GHz at 687.970, 688.888, 691.701, 706.221 GHz  
  > "Four spectral windows with a spectral bandwidth of 1.875 GHz were placed at sky frequencies of 687.970 GHz, 688.888 GHz, 691.701 GHz, and 706.221 GHz." (2 ALMA observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: extended configuration, one track, 35 antennas, September 2015  
  > "One track was observed with 35 antennas during September 2015 using the extended configuration of the array" (2 ALMA observations and data reduction)
- baselines: 41 m to 2251 m  
  > "The projected baselines range from 41 m to 2251 m." (2 ALMA observations and data reduction)
- angular resolution: 0.07'' x 0.05'' (natural weighting)  
  > "a spatial resolution of $0.07\ensuremath{''}\times0.05\ensuremath{''}$ using natural (NA) weighting" (2 ALMA observations and data reduction)
- max recoverable scale: significant filtering on scales >=2''  
  > "we expect to filter a significant amount of emission on scales $\geq2\ensuremath{''}$" (2 ALMA observations and data reduction)
- sensitivity: 4 mJy/beam per 12.8 km/s channel; continuum 0.5 mJy/beam  
  > "The sensitivity in the line data cube is 4 mJy beam$^{-1}$ in channels of 12.8 km s$^{-1}$ width." (2 ALMA observations and data reduction)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=6-5 (not stated (~689 GHz))
- Other facility **ALMA Cycle 0 (Band 7)**: Continuum upper limit and polygon cleaning masks  
  > "We also included as an upper limit the ALMA Cycle 0 Band 7 continuum flux from GB14." (4 Clumpy torus models)
- Other facility **NIR/MIR and VLTI data**: Nuclear SED 1.65-13 um points and MIR interferometry  
  > "We combined the ALMA Band 9 continuum thermal flux with the NIR/MIR continuum and MIR interferometry data obtained by several groups" (4 Clumpy torus models)
- External data: NIR/MIR nuclear SED points and MIR interferometry  
  > "from $1.65\,\mu$m to $432\,\mu$m ((cite: Wei04; Mar00; Lop14; Tom01); this work)" (4 Clumpy torus models) [from (cite: Wei04; Mar00; Lop14; Tom01)]
- External data: H2O maser sub-Keplerian rotation curve (alpha=0.31)  
  > "H$_2$O sub-Keplerian rotation curve of (cite: Gal96) projected along the CO major axis" (5 Kinematics of the torus) [from (cite: Gal96)]
- External data: Dust emissivity kappa_352GHz = 0.0865 m2/kg  
  > "adoption of a value for $\kappa_{{\rm 352~GHz}}=0.0865$ m$^2$ kg$^{-1}$ (cite: Kla01)" (3 Continuum and line emission maps) [from (cite: Kla01)]
- Simulation/model as data: CLUMPY torus models of Nenkova et al. fitted with BayesClumpy  
  > "We fitted the nuclear SED with the CLUMPY torus models of (cite: Nen08a; Nen08b) adopting a Bayesian approach using the `BayesClumpy` tool (cite: Ase09)." (4 Clumpy torus models)

## Processing

### Calibration

- pipeline or manual: Calibrated with CASA; version not stated  
  > "The data were calibrated using the ALMA reduction package `CASA` (cite: Mul07)." (2 ALMA observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: GILDAS mapping and CLEAN after exporting uv-tables from CASA  
  > "The calibrated uv-tables were exported to `GILDAS`[^1] for mapping and CLEANing." (2 ALMA observations and data reduction)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Polygons per channel based on >=5 sigma Cycle 0 emission; single polygon for continuum  
  > "The polygons were defined for the CO line image for each channel based on the detection of significant ($\geq5\sigma$) emission identified in our Cycle 0 project (GB14)." (2 ALMA observations and data reduction)
- multiscale scales: _not stated_
- continuum subtraction: Continuum from line-free channels averaged per sub-band, combined to 694 GHz  
  > "We obtained images of the continuum emission by averaging in each sub-band the channels free of possible line emission." (2 ALMA observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Polygon masks from Cycle 0 detections  
  > "based on the detection of significant ($\geq5\sigma$) emission identified in our Cycle 0 project (GB14)" (2 ALMA observations and data reduction) [from GB14 (Garcia-Burillo et al. 2014)]
- Phase center same as GB14  
  > "The phase tracking center of the central field is the same as in GB14" (2 ALMA observations and data reduction) [from GB14]
- Dust temperature, gas-to-dust ratio 60 and emissivity from earlier SED/line analysis  
  > "Assuming that the gas–to–dust ratio in the central 2 kpc of is $\simeq60$ (GB14)" (3 Continuum and line emission maps) [from GB14; (cite: Vit14)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibrators
- GILDAS version and CLEAN parameters (gain, threshold, cell, image size)
- Which channels were line-free
- Number of CLEAN iterations and uniform weighting details
- BayesClumpy priors for the remaining parameters, MCMC settings, and the SED data values
- Derivation of the deprojected v_mean/sigma
- Self-calibration status

## Analysis recipe

1. **Image continuum and CO(6-5) cube**: CASA calibration, GILDAS mapping and CLEAN with polygon masks; natural weighting (uniform weighting also shown)  
  > "The calibrated uv-tables were exported to `GILDAS`[^1] for mapping and CLEANing." (2 ALMA observations and data reduction)
   - software: CASA, GILDAS
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit torus size and orientation in visibilities**: UV_FIT to visibilities within r<=0.2'' of AGN  
  > "We have used the GILDAS task `UV_FIT` to find the best-fit to the visibilities inside a radius $r\leq0.2\ensuremath{''}$ (14 pc) from the AGN." (3 Continuum and line emission maps)
   - software: GILDAS
   - fitting: Ellipsoidal disk fit  
  > "The fit indicates that half of the total flux in this region stems from a spatially resolved ellipsoidal disk, characterized by a deconvolved diameter of $7\pm1$ pc" (Continuum and line emission maps)
   - validation: Residuals inspected; uniform-weighted image shows goodness of fit  
  > "The enhanced spatial resolution of the uniformly-weighted data set better illustrates the goodness of the fit" (3 Continuum and line emission maps)
3. **Derive torus dust and gas mass**: Modified black body to 13.8 mJy flux at 432 um, then gas-to-dust ratio  
  > "To estimate $M_{\rm dust}^{\rm torus}$ we used a modified black-body function" (3 Continuum and line emission maps)
   - assumption: T_dust = T_gas = 150 K, beta=2, kappa_694GHz=0.34 m2/kg, gas-to-dust 60, max 18% non-thermal flux  
  > "a dust temperature $T_{\rm dust} \simeq T_{\rm gas}=150$ K, an emissivity index $\beta=2$, and a value for the dust emissivity $\kappa_{{\rm 694~GHz}}$=0.34 m$^2$ kg$^{-1}$" (3 Continuum and line emission maps)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit nuclear SED with CLUMPY models**: Bayesian fit with BayesClumpy; sigma 40-60 deg, Y 5-30, inclination 60-90 deg (and 30-90 deg alternative)  
  > "The torus radial extent, defined by the outer–to–inner radius ratio $Y$, is in the range $5<Y<30$ based on the torus size measured by ALMA at 432 $\mu$m." (4 Clumpy torus models)
   - software: BayesClumpy
   - fitting: Bayesian with priors on six parameters; medians reported  
  > "adopting a Bayesian approach using the `BayesClumpy` tool (cite: Ase09). This scheme has been applied to model the SED of other Seyferts (cite: Alo11; Ram11). Using this approach we can specify a priori information about the six model parameters." (Clumpy torus models)
   - validation: Compared with ALMA-only mass and radius  
  > "These values are consistent with those derived in Sect [3](#maps) from the Band 9 observations alone." (4 Clumpy torus models)
5. **Analyze torus kinematics**: Mean-velocity map and p-v diagrams along major and minor axes compared with maser rotation curve  
  > "Figure [5](#Fig5)b shows the position-velocity (p-v) diagram taken along the morphological major axis of the CO torus" (5 Kinematics of the torus)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration  
  > "The data were calibrated using the ALMA reduction package `CASA` (cite: Mul07)." (2 ALMA observations and data reduction)
- **GILDAS** : Mapping, CLEAN, UV_FIT  
  > "The calibrated uv-tables were exported to `GILDAS`[^1] for mapping and CLEANing." (2 ALMA observations and data reduction)
- **BayesClumpy** : Bayesian SED fitting with CLUMPY models  
  > "adopting a Bayesian approach using the `BayesClumpy` tool (cite: Ase09)" (4 Clumpy torus models)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dust torus diameter | 7 | ±1 | pc | 2 | characterized by a deconvolved diameter of $7\pm1$ pc oriented along $PA^{\rm major}=142^{\circ}\pm23^{\circ}$ |
| Dust torus flux at 432 um | 13.8 | ±1 | mJy | 2 | $\simeq13.8\pm1$ mJy |
| CO torus diameter | 10 | ±1 | pc | 2 | diameter$\simeq10\pm1$ pc, minor-to-major axis ratio $\simeq0.5\pm0.1$ |
| Torus dust mass | ~1600 | not stated | Msun | 3 | we estimate a dust mass of $M_{\rm dust}^{\rm torus}\sim1600~M_\ensuremath{\odot}$ |
| Torus gas mass | 1e5 | ±0.3e5 | Msun | 3 | $M_{\rm gas}^{\rm torus}=(1\pm0.3)\times10^5~M_\ensuremath{\odot}$ |
| CLUMPY fit (i 60-90 deg): Mgas, R, i | 0.9e5 Msun; 4 pc; 66 deg | +0.2/-0.4e5; ±1 pc; +9/-4 deg | mixed | 4 | $R_{\rm torus} = 4\pm$1 pc, and $i=66\ensuremath{^\circ}\pm^{9}_{4}$ |
| CLUMPY fit (i 30-90 deg): Mgas, R, i | 0.6e5 Msun; 2 pc; 34 deg | +0.4/-0.2e5; ±1 pc; +5/-2 deg | mixed | 4 | $R_{\rm torus} = 2\pm$1 pc, and $i=34\ensuremath{^\circ}\pm^{5}_{2}$ |
| Tilt between kinematic and morphological major axes | 53 | ±15 | deg | 5 | is tilted by a significant angle ($\simeq53^{\circ}\pm15^{\circ}$) |

## Qualitative findings

- CO torus shows slow rotation, strong non-circular motions and enhanced turbulence (v_mean/sigma<1), and no CO counterpart of the dust polar emission  
  > "yields very low values: $v_{\rm mean}/\sigma<1$" (5 Kinematics of the torus)

## Claim tuples

- H: The submillimeter counterpart of the torus can be resolved with ALMA | E: Band 9 imaging at ~4 pc and UV_FIT | R: 7-10 pc disk in dust and CO at the AGN | F: First detection of the submillimeter torus | **supported**
- H: The CLUMPY SED fit is consistent with the ALMA-only torus mass and radius | E: BayesClumpy fit of the nuclear SED | R: Mgas 0.9e5 Msun, R 4 pc vs ALMA 1e5 Msun | F: Consistent | **supported**
- H: The torus is edge-on like the maser disk | E: Compare p-v with the maser rotation curve; SED fit with a wider inclination range | R: CO velocities >=2 times lower than for edge-on | F: The torus may be less inclined (34-66 deg) at larger radii; PPI suggested | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Outflow entrainment as alternative to PPI for minor-axis velocity gradient  
  > "Alternatively, the velocity gradient observed along the minor axis could be explained by gas being entrained in the outflow" (5 Kinematics of the torus)
- How they decided it was enough: _not stated_
- Limitation (authors): Extended emission is resolved out; NIR fluxes are under-predicted by the model  
  > "The extended emission connecting the AGN with the CND in the map of GB14 is likely resolved out in the present data." (3 Continuum and line emission maps)
- Caveat (inferred, ours): Single track, low S/N per channel; kinematic interpretation is qualitative
- Caveat (inferred, ours): Model degeneracies in inclination
- Caveat (inferred, ours): Dust mass depends on assumed T, kappa and gas-to-dust ratio

## Reproducibility

- Data public (paper): Project code given; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA$\#$2013.1.00055.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: GILDAS CLEAN parameters
- Missing: SED data table and BayesClumpy priors
- Missing: Kinematic analysis details
- Data volume (inferred): ~50-100 GB raw (single Band 9 extended-array track)
- Score (inferred): 3/5, Data are identified and the main steps are named, but imaging and fitting parameters are largely missing.
- Rediscovery candidate: no, Many imaging and SED-fit settings are unstated.

## Links

- Method: Asensio Ramos & Ramos Almeida 2009 (cite: Ase09) (BayesClumpy)
- Method: Nenkova et al. 2008 (cite: Nen08a; Nen08b) (CLUMPY torus models)
- Companion: García-Burillo et al. 2014 (cite: Gar14) (Cycle 0 ALMA data of the same CND)
- Related: ALMA Cycle 0 NGC 1068 project (GB14)

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
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
  "facts": 74,
  "stated": 41,
  "rate": 0.554
 },
 "evidence_ok": true
}
```

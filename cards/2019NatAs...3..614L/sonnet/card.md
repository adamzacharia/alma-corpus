# An intense thermospheric jet on Titan

`2019NatAs...3..614L` | Nature Astronomy 2019 | first author: Lellouch, E. | arXiv: 1903.12116 | DOI: 10.1038/s41550-019-0749-4

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: solar_system
- Question: What are the winds in Titan's upper mesosphere and thermosphere (500-1200 km), measured directly from Doppler shifts of molecular lines with ALMA?  
  > "the wind regime in Titan's upper mesosphere and thermosphere (500-1200 km) has remained unconstrained so far." (abstract)
- Target **Titan**: coordinates _not stated_; z/distance geocentric distance 9.3508 au (July 22), 9.7504-9.7512 au (August)  
  > "Titan's 5150-km diameter subtended 0.7594” and 0.7283” in the sky for the July and August observations respectively" (Supplementary Information 1) Observations and data reduction); distance from Supplementary Table 1 (geocentric distance)  
  > "Titan's 5150-km diameter subtended 0.7594” and 0.7283” in the sky for the July and August observations respectively" (Supplementary Information 1) Observations and data reduction)

## Data provenance

- ALMA projects: 2015.1.01023.S
- bands: Band 7, 329-364 GHz  
  > "All three scheduling blocks made use of Band 7 receiver sets, altogether covering large portions of the 329-364 GHz range." (Supplementary Information 1) Observations and data reduction)
- frequencies and spectral setup: Spectral resolutions 1-2 MHz generally; high resolution 61-282 kHz for HNC, HC3N, HCN, CH3CN, DCN, CH3CCH  
  > "Higher resolutions (61 – 282 kHz) were also used, to study narrow yet strong lines, in particular, HNC, HC 3 N, and the HCN hyperfine structure core" (Supplementary Information 1) Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: 38 antennas in July 2016, 39 in August  
  > "38 antennas were active in July 2016 and 39 in August." (Supplementary Information 1) Observations and data reduction)
- configurations: C40-5  
  > "ALMA was at that time in a moderately extended configuration (C40-5)" (main text)
- baselines: _not stated_
- angular resolution: ~0.16-0.23” (natural weighting)  
  > "providing angular resolutions of ~0.16-0.23” (“natural weighting”)" (main text)
- max recoverable scale: _not stated_
- sensitivity: rms noise 2.0 mJy/beam/MHz  
  > "resulting in rms noise of 2.0 mJy/beam/MHz" (Supplementary Information 1) Observations and data reduction)
- time on source: 49 min per scheduling block  
  > "The on-source time was 49 min for each of the scheduling blocks." (Supplementary Information 1) Observations and data reduction)
- observing dates: July 22 and August 18/19, 2016  
  > "Observations of Titan were conducted on July 22 and August 18/19, 2016" (main text)
- pi or archival as stated: _not stated_
- Line: HNC J=4-3 (362.63030 GHz)
- Line: CH3CN J=19-18, K=0,1,... (349.427, 349.447, 349.454 GHz)
- Line: HCN J=4-3 (hyperfine) (354.5055 GHz main, 354.5039 and 354.5075 GHz satellites)
- Line: HC3N J=39-38 (also J=38-37) (354.697 GHz (345.609 GHz))
- Other facility **Cassini (CIRS, INMS, UVIS)**: A priori temperature profile and comparison abundance profiles  
  > "we used an equatorial profile derived from Cassini/CIRS measurements in May 2016 (T119 flyby)" (Methods)
- External data: HCN a priori profile from ground-based data  
  > "we used the HCN profile from Ref. [39] (extended above 400 km to reach HCN = 10 [-4] at 800 km and above) as a priori." (Methods) [from Marten et al. 2002 (ref 39)]
- External data: DCN/HCN ratio (2.5±0.2)e-4  
  > "constant DCN/HCN ratio of (2.5±0.2) x 10 [-4] [44]" (Methods) [from Molter et al. 2016 (ref 44)]
- External data: Photochemical HNC and HC3N profiles  
  > "testing photochemical profiles [14] for HNC" (Methods) [from Dobrijevic et al. 2016 (ref 14)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: quasars J1634-2058 and J1626-2951 (phase and flux)  
  > "The quasars J1634-2058 and J1626-2951 were used for phase calibration and flux calibration." (Supplementary Information 1) Observations and data reduction)
- flux scale uncertainty: _not stated_
- self calibration: Self-calibration performed to improve imaging  
  > "Self-calibration was performed to improve imaging quality" (Supplementary Information 1) Observations and data reduction)

### Imaging

- task: CASA and GILDAS  
  > "deconvolution and imaging were performed under both the CASA and GILDAS environments" (Supplementary Information 1) Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The achieved angular resolution (“natural weighting”) varies" (Supplementary Information 1) Observations and data reduction)
- uv taper: _not stated_
- cell size: 0.02” or 0.05” pixel grids  
  > "re-gridded on 0.02” or 0.05” pixel grids" (Supplementary Information 1) Observations and data reduction)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Radiative transfer model and inversion code  
  > "home-made radiative transfer model in full spherical geometry, inherited from [4, 34, 35]" (Methods) [from refs 4, 34, 35]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration approach (pipeline vs manual)
- Self-calibration parameters
- Deconvolution details, masks, continuum subtraction
- The model-based flux corrections (<10%) per dataset
- Home-made radiative transfer/inversion code not public
- Trial-and-error wind profiles not parameterised

## Analysis recipe

1. **Doppler wind measurement**: Gaussian plus polynomial fits of line centres at each beam position; Monte-Carlo errors  
  > "we performed Gaussian fits (the sum of a Gaussian and a 1 [st] or 2 [nd] degree polynomial) of the line profiles in their central parts" (Supplementary Information 2) Doppler wind measurements)
   - parameter: 300 Monte-Carlo noise realisations  
  > "Repeating this procedure 300 times, the dispersion in the fitted positions provided an estimate of the error bars" (Supplementary Information 2) Doppler wind measurements)
   - fitting: _not stated_
   - validation: _not stated_
2. **Retrieve temperature and abundance profiles**: Optimal-estimation inversion of CO and HCN/H13CN lines in nadir and limb  
  > "using a home-made inversion code [35] and based on optimal estimation methods principles [37-38]" (Methods)
   - assumption: HCN/H13CN = 89  
  > "We assumed a telluric-like HCN / H [13] CN ratio of 89" (Supplementary Information 3) Temperature and abundance retrievals)
   - fitting: _not stated_
   - validation: Repeated with several a priori temperature and HCN profiles  
  > "Uncertainties due to the a priori were evaluated by repeating the temperature/HCN inversion process using several a priori temperature and HCN profiles" (Methods)
3. **HNC and HC3N profiles**: Compare radial variation of line-integrated intensity with models having cutoff altitudes  
  > "the latter can be determined from the observed variation of the line-integrated intensities with radial distance." (Methods)
   - fitting: _not stated_
   - validation: synthetic datasets and 30° angular bins  
  > "provides a robustness test of the method" (Supplementary Information 3))
4. **Wind contribution functions and altitudes**: Contribution functions convolved with beam and weighted by spectral slope  
  > "using a weight proportional to the local spectral slope of the synthetic spectrum [48,4]" (Methods)
   - fitting: _not stated_
   - validation: _not stated_
5. **Fit zonal wind profiles**: Solid-body fits to LOS winds; forward model with trial-and-error latitudinal zonal profiles  
  > "we used our forward model and a trial-and-error approach to de-convolve the LOS winds" (main text)
   - assumption: purely zonal flow  
  > "Assuming purely zonal flow" (main text)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : data reduction and imaging  
  > "Data reduction was initially carried out under CASA." (Supplementary Information 1))
- **GILDAS** : deconvolution and imaging  
  > "imaging were performed under both the CASA and GILDAS environments" (Supplementary Information 1))

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HNC equatorial jet max speed at ~1000 km | ~340-350 | not stated | m/s | 5 | equatorial jet with ~350 m/s maximum speed |
| HNC cutoff altitude | 870 | ±40 | km | 3 | the bulk of HNC is located above 870±40 km altitude |
| HC3N cutoff altitude | 630 | ±30 | km | 3 | best fit cutoff altitude of 630±30 km |
| Mesopause temperature and altitude | 140 K at 800 | ±50 km | K, km | 2 | a ~140 K mesopause, located at 800±50 km altitude |
| CH3CN max zonal wind | 220 at 15°S | not stated | m/s | 5 | indicate a maximum 220 m/s speed at 15°S |
| CO mixing ratio | 48 | ±1 | ppm | 2 | retrieve the CO mixing ratio (48±1 ppm) |

## Qualitative findings

- Strong prograde winds extend into the thermosphere, becoming an equatorial jet with altitude.  
  > "strong prograde winds extend up to the thermosphere, with the circulation progressively turning into an equatorial jet regime as altitude increases" (abstract)

## Claim tuples

- H: Do strong prograde winds extend to Titan's thermosphere? | E: Doppler shifts of six molecules | R: ~340 m/s at 1000 km | F: Equatorial thermospheric jet exists | **supported**
- H: Where is HNC distributed? | E: line shape and radial emission | R: above 870±40 km | F: HNC is thermospheric, GCR plays minor role | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Gravitational tides rejected as source of strong winds  
  > "Gravitational tides [28] are not promising for explaining the strong wind speeds we measure" (main text)
- How they decided it was enough: _not stated_
- Limitation (authors): Wind modelling ignores altitude-dependent Doppler shifts in 2D; approximate.  
  > "this is still an approximate way of modelling the data" (Supplementary Information 4))
- Caveat (inferred, ours): Vertical extent of wind contribution functions is broad for HCN and HC3N
- Caveat (inferred, ours): Equatorial profiles only
- Caveat (inferred, ours): Trial-and-error wind fits without formal uncertainties

## Reproducibility

- Data public (paper): Available from ALMA archive and on request  
  > "are available from the ALMA archive (http://almascience.nrao.edu/aq/) and from the corresponding author upon reasonable request." (Data availability)
- Products in archive: _not stated_
- Code: On request only  
  > "are available from the corresponding author upon reasonable request." (Code availability)
- Missing: Home-made radiative transfer and inversion code
- Missing: Calibration/imaging parameters
- Data volume (inferred): ~100-300 GB
- Score (inferred): 3/5, Public data and clear fitting recipe, but custom code and sparse reduction details.
- Rediscovery candidate: no, Requires non-public home-made modeling code and unstated imaging details.

## Links

- Method: Moreno et al. 2005 (ref 4) (Earlier interferometric wind method)
- Method: Lellouch et al. 2017 (ref 35) (Inversion code)
- Companion: Thelen et al. 2019 (ref 33) (Previous ALMA HCN/HC3N abundances)
- Related: Cassini CIRS/INMS/UVIS

## Checks

```json
{
 "quotes": 52,
 "quotes_ok": 52,
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
  "facts": 72,
  "stated": 38,
  "rate": 0.528
 },
 "evidence_ok": true
}
```

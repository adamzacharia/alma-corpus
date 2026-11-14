# ALMA Observations of Lyα Blob 1: Halo Substructure Illuminated from Within

`2016ApJ...832...37G` | The Astrophysical Journal 2016 | first author: Geach, J. E. | arXiv: 1608.02941 | DOI: 10.3847/0004-637X/832/1/37

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Do the submillimetre sources at the centre of SSA22-LAB01 and their surrounding halo substructure explain the extended Lyα emission of the blob?  
  > "develop a hypothesis about the role of the central submillimeter sources in contributing to the extended Ly _α_ emission" (3. ANALYSIS & INTERPRETATION)
- Target **SSA22-LAB01**: coordinates 22h17m26s, +00d12m36s (J2000; Table 1 positions for a+b and c)  
  > "SSA22-LAB01 ( _z_ = 3 _._ 1, Steidel et al. 2000)" (1. INTRODUCTION); z/distance z = 3.1  
  > "SSA22-LAB01 ( _z_ = 3 _._ 1, Steidel et al. 2000)" (1. INTRODUCTION); distance from Steidel et al. 2000; component c z = 3.1000 from [O III] and Hβ (Kubo et al. 2015)  
  > "SSA22-LAB01 ( _z_ = 3 _._ 1, Steidel et al. 2000)" (1. INTRODUCTION)

## Data provenance

- ALMA projects: 2013.1.00922.S
- bands: Band 7 (850 µm)  
  > "high-resolution Band 7 continuum ( _λ_ obs = 850 _µ_ m) observations of SSA22-LAB01" (1. INTRODUCTION)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 7.5 GHz centred at 347.59 GHz  
  > "the full 7.5 GHz of bandwidth centred at 347.59 GHz was used to measure the continuum emission" (2.1 ALMA)
- arrays: 36–40 12 m antennas  
  > "A total of 36–40 12 metre antennas were used in the observations" (2.1 ALMA)
- configurations: _not stated_
- baselines: 21-918 m  
  > "with baselines spanning
21-918 m" (2.1 ALMA)
- angular resolution: 0.4 arcsec max resolution; beam 0.40x0.38 arcsec  
  > "The synthesized beams are 0 _._ 40 _[′′]_ _×_ 0 _._ 38 _[′′]_ (PA 23 _[◦]_ )" (2.1 ALMA)
- max recoverable scale: 5 arcsec  
  > "capable of recovering emission on scales of
up to 5 _[′′]_" (2.1 ALMA)
- sensitivity: 40 µJy/beam, 90 µJy/beam after taper  
  > "The depth of the map is 40 _µ_ Jy beam [−][1],
increasing to 90 _µ_ Jy beam [−][1] after tapering." (2.1 ALMA)
- time on source: 2860 s total integration  
  > "the total integration time
is 2860 seconds" (2.1 ALMA)
- observing dates: _not stated_
- pi or archival as stated: Two projects, PIs Geach and Matsuda  
  > "[PI Geach] and 2013.1.00704S [PI Matsuda]) with a similar
configuration in Band 7" (2.1 ALMA)
- Other facility **HST STIS**: 50CCD clear-filter imaging, 7020 s  
  > "Six exposures of SSA22-LAB01 were taken in ‘LOWSKY’ time for a total of 7020 seconds of integration." (2.3)
- Other facility **Keck MOSFIRE**: K-band spectroscopy confirming companion S1 at z = 3.0968  
  > "detecting the [O III ] line at _z_ = 3 _._ 0968" (3.1)
- Other facility **VLT MUSE**: Lyα integral field observations  
  > "Integral field spectroscopy was performed with the Very Large
Telescope Multi Unit Spectroscopic Explorer (MUSE) instrument." (2.2)
- Other facility **JCMT SCUBA-2**: Single-dish 850 µm map used for feathering  
  > "To both maps we ‘feather’ the single
dish SCUBA-2 (regridded) map" (2.1 ALMA)
- External data: SCUBA-2 850 µm flux S850 = 4.6 ± 1.1 mJy  
  > "unresolved _S_ 850 = 4 _._ 6 _±_ 1 _._ 1 mJy submillimetre source" (1. INTRODUCTION) [from Geach et al. 2014]
- External data: Spectroscopic redshift of component c, z = 3.1000  
  > "_z_ = 3 _._ 1000 _±_ 0 _._ 0003" (3.1) [from Kubo et al. 2015]
- Simulation/model as data: GIZMO zoom simulation of 10^13 Msun halo, with Powderday/Hyperion dust RT and TLAC Lyα RT, giving mock ALMA, STIS and Lyα maps  
  > "We simulate the formation of a galaxy in a massive ( _M_ h _≈_
10 [13] _M_ _⊙_ ) halo (by _z_ = 2) utilising a cosmological zoom technique" (3.2)

## Processing

### Calibration

- pipeline or manual: CASA; visibilities from the two projects concatenated  
  > "All calibration was performed using the CASA software and the visibilities from each project concatenated into
a single measurement set" (2.1 ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Phase calibrator J2206-0031 used to confirm consistent flux scaling between projects  
  > "Observations of the phase calibrator source J2206-0031 confirm consistent flux scaling between the two projects" (2.1 ALMA)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "to the
CASA clean task" (2.1 ALMA)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We use a natural weighting of the visibilities and clean down to a threshold of 70 _µ_ Jy within 1000 iterations." (2.1 ALMA)
- uv taper: outer taper of 1 arcsec  
  > "at full resolution and with
an outer taper of 1 _[′′]_" (2.1 ALMA)
- cell size: _not stated_
- image size: _not stated_
- masking: Two circular masks, 2 arcsec radius  
  > "supply circular masks (each 2 _[′′]_ in radius)" (2.1 ALMA)
- multiscale scales: 0, 0.5, 1, 2, 3 arcsec  
  > "allowing model Gaussian components of width 0 _[′′]_ (delta function), 0.5 _[′′]_, 1 _[′′]_, 2 _[′′]_
and 3 _[′′]_" (2.1 ALMA)
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Final maps corrected for primary beam  
  > "Final maps are
corrected for primary beam attenuation for analysis." (2.1 ALMA)
- array combination: Feathered with SCUBA-2 map  
  > "To both maps we ‘feather’ the single
dish SCUBA-2 (regridded) map" (2.1 ALMA)
- smoothing: _not stated_
- final beam: 0.40x0.38 arcsec (PA 23 deg); tapered 1.01x0.98 arcsec  
  > "The synthesized beams are 0 _._ 40 _[′′]_ _×_ 0 _._ 38 _[′′]_ (PA 23 _[◦]_ ) and 1 _._ 01 _[′′]_ _×_ 0 _._ 98 _[′′]_" (2.1 ALMA)
- final rms: 40 µJy/beam; 90 µJy/beam tapered  
  > "The depth of the map is 40 _µ_ Jy beam [−][1],
increasing to 90 _µ_ Jy beam [−][1] after tapering." (2.1 ALMA)

### Inherited from earlier work

- Lyα luminosity from IR luminosity relation  
  > "_L_ Ly _α_ = 0 _._ 05 _f_ esc _,_ Ly _α_ _L_ IR (Djikstra &
Westra 2010)" (3.1) [from Djikstra & Westra 2010]
- Zoom simulation details and feedback models  
  > "(see Hopkins et al. 2014 for details)" (3.2) [from Hopkins et al. 2014]
- Dust treatment in Lyα RT  
  > "We follow the prescriptions of Laursen (2010) for the Small Magellanic Cloud" (3.2) [from Laursen 2010]

### Not stated but needed to reproduce (our reading)

- Number of SBs/execution blocks and observing dates for the ALMA data
- Flux calibrator and absolute flux uncertainty
- Whether archive-delivered or manually produced calibration was used, and CASA version
- Feathering parameters and SCUBA-2 map scaling
- SimALMA parameter values
- Simulation initial conditions and code configuration
- Molecular gas mass conversion details
- SED template normalization details

## Analysis recipe

1. **Image ALMA continuum**: Concatenate two projects, clean with masks, multi-scale, natural weighting, full-res and 1 arcsec taper, feather with SCUBA-2  
  > "We use a natural weighting of the visibilities and clean down to a threshold of 70 _µ_ Jy within 1000 iterations." (2.1 ALMA)
   - software: CASA
   - parameter: threshold 70 µJy, 1000 iterations, taper 1 arcsec  
  > "clean down to a threshold of 70 _µ_ Jy within 1000 iterations" (2.1 ALMA)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive IR luminosity and SFR**: Dale & Helou templates, alpha=1–2.5, normalized to 850 µm flux at z=3.1; Kennicutt & Evans SFR calibration  
  > "We adopt the Dale & Helou (2002) set
of templates" (3.1)
   - assumption: Cool dust traces dense ISM (Scoville et al. 2015); SFR scales linearly with gas surface density (Wong & Blitz 2002)  
  > "Assuming cool dust emission traces the dense ISM (Scoville et al. 2015)" (3.1)
   - fitting: _not stated_
   - validation: Compared with ISM-mass scaling SFR  
  > "consistent with the ISM mass scaling value derived above" (3.1)
3. **Run zoom simulation and mock observations**: GIZMO zoom simulation, Powderday/Hyperion RT, SIMALMA mock ALMA, mock STIS with noise, SExtractor source detection  
  > "To simulate the ALMA observations we use the CASA task
SIMALMA, setting the simulation parameters to match the real
observations" (3.2)
   - software: GIZMO, MUSIC, Powderday, yt, FSPS, Hyperion, CASA simalma, SExtractor
   - parameter: dust = 40% of metal mass; Kroupa IMF; WD01 dust, RV=3.15  
  > "the dust mass
is assumed to be a constant fraction (40%) of the total metal
mass in a given cell" (3.2)
   - fitting: _not stated_
   - validation: Compared mock and real source counts, with chance projection contamination estimated  
  > "In a random
5 _[′′]_ radius aperture we would expect 4 _±_ 1 sources by chance" (3.3)
4. **Lyα radiative transfer**: TLAC Monte Carlo RT with central galaxies as sources, SFR-to-Lyα relation, peeling, SMC-like dust  
  > "We use the
code TLAC (Gronke et al. 2014, 2015) with the default core
skipping parameter _x_ = 3." (3.2)
   - software: TLAC
   - parameter: f_ion = 1%  
  > "We assume that _f_ ion is 1%" (3.2)
   - fitting: _not stated_
   - validation: Compared Lyα maps with MUSE observation  
  > "Figure 4 shows the projected
Ly _α_ surface brightness maps of the simulated halo compared
to the latest integral field observations from MUSE." (3.3)

## Software

- **CASA** : Calibration, clean imaging, simalma  
  > "All calibration was performed using the CASA software" (2.1 ALMA)
- **GIZMO** : Cosmological zoom hydrodynamics  
  > "hydrodynamics code GIZMO (Hopkins et al. 2014)" (3.2)
- **Powderday** : Dust radiative transfer for mock observations  
  > "we employ the dust radiative transfer code P OWDERDAY" (3.2)
- **TLAC** : Lyα radiative transfer  
  > "We use the
code TLAC (Gronke et al. 2014, 2015)" (3.2)
- **SExtractor** 2.19.5: Detecting sources in STIS images  
  > "We detect sources using SE XTRACTOR version 2.19.5" (3.3)
- **MUSE pipeline** 1.0.5: MUSE reduction  
  > "Data
were reduced with the MUSE pipeline (version 1.0.5)" (2.2)
- **DrizzlePac** 2: STIS co-add  
  > "using the D RIZZLE P AC software (version 2)" (2.3)
- **MUSIC** : Initial conditions  
  > "The initial conditions are generated with
the MUSIC code (Hahn et al. 2011)" (3.2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total ALMA 850 µm flux density (tapered, >3σ) | 1.68 | 0.06 | mJy | 1 | _S_ 850 = 1 _._ 68 _±_ 0 _._ 06 mJy |
| S850 of a+b | 0.95 | 0.04 | mJy | 1 | 0 _._ 95 _±_ 0 _._ 04 |
| S850 of c | 0.73 | 0.05 | mJy | 1 | 0 _._ 73 _±_ 0 _._ 05 |
| Flux discrepancy with SCUBA-2 | 2.9 | 1.1 | mJy | 1 | ∆ _S_ 850 =
2 _._ 9 _±_ 1 _._ 1 mJy |
| Median LIR of a+b | 6.0e11 | 0.3e11 | Lsun | 2 | _L_ IR _≈_ 6 _._ 0 _±_ 0 _._ 3 _×_ 10 [11] _L_ _⊙_ |
| Molecular gas mass | 4e10 | not stated | Msun | 2 | _M_ gas _≈_ 4 _×_ 10 [10] M _⊙_ |
| Fraction of centrally generated Lyα photons escaping the box | 58 | not stated | percent | 4 | 58% of centrally generated photons
escape the simulation box |
| Fraction of HI mass in subhalos | 77 | not stated | percent | 4 | The majority (77%) of the H I mass |
| Synthetic STIS sources vs observed | 5 vs 8 | not stated | sources | 3 | Formally, we detect five sources at the _>_ 3 _σ_ level |

## Qualitative findings

- Companion S1 lies 2.1 arcsec (17 pkpc) and 250 km/s from ALMA component c.  
  > "S1 is 2.1 _[′′]_ (17 pkpc) from
ALMA source ‘c’ with a line-of-sight velocity offset of just
250 km s [−][1]." (3.1)

## Claim tuples

- H: Central submm sources are accompanied by low-mass satellites seen as faint STIS sources | E: Compared ALMA, STIS and MOSFIRE data with mock observations of the simulation | R: One STIS source confirmed at 250 km/s; 8 observed vs 5 simulated STIS sources, with 4±1 expected by chance | F: Observed halo population is consistent with the simulation | **partially**
- H: Lyα photons from central sources resonantly scatter in HI associated with halo substructure to form LABs | E: TLAC radiative transfer on the simulation | R: 77% of HI is in subhalos; extended Lyα resembles observed LABs | F: Scattering may be a dominant process | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Cold-flow accretion alone is considered insufficient to explain the extended Lyα  
  > "suggesting that cold
flows are not sufficient to explain the extended Ly _α_ luminosity of giant LABs." (3.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Missing flux relative to SCUBA-2 and a lack of more compact array data.  
  > "Deeper observations with a slightly more compact array configuration
would be beneficial to address this." (2.1 ALMA)
- Caveat (inferred, ours): The simulation is a single halo, not tuned to this object
- Caveat (inferred, ours): Only one STIS companion is spectroscopically confirmed
- Caveat (inferred, ours): The SED is poorly constrained, so LIR and SFR rely on the template range

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Simulation snapshots and configuration
- Missing: Calibration and feathering details
- Data volume (inferred): ~10-30 GB for ALMA Band 7 data
- Score (inferred): 3/5, The ALMA imaging recipe is mostly given, but the calibration and simulation details are incomplete.
- Rediscovery candidate: no, The simulation component cannot be reproduced from the text, and the data availability is not stated in the paper.

## Links

- Companion: Geach et al. 2014 (SCUBA-2 detection of SSA22-LAB01)
- Related: SCUBA-2 Cosmology Legacy Survey

## Checks

```json
{
 "quotes": 69,
 "quotes_ok": 69,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2013.1.00704.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 56,
  "rate": 0.7
 },
 "evidence_ok": true
}
```

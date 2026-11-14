# ALMA View of the Galactic Center Minispiral: Ionized Gas Flows around Sagittarius A<SUP>∗</SUP>

`2017ApJ...842...94T` | The Astrophysical Journal 2017 | first author: Tsuboi, Masato | arXiv: 1608.08714 | DOI: 10.3847/1538-4357/aa74e3

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: milky_way_ism, star_formation
- Question: What are the kinematics, electron temperature and density of the ionized gas streamers of the Galactic Center Mini-spiral, and how do they relate to Keplerian orbits around Sgr A*?  
  > "We revealed the kinematics of the ionized gas streamers of the GCMS." (abstract); "We estimated the LTE electron temperature and electron density in the ionized gas streamers." (abstract)
- Target **Galactic Center Mini-spiral (Sgr A*)**: coordinates _not stated_; z/distance 8 kpc (assumed)  
  > "The distance of the Galactic Center is assumed to be 8 kpc in this paper." (Introduction); distance from assumed  
  > "The distance of the Galactic Center is assumed to be 8 kpc in this paper." (Introduction)

## Data provenance

- ALMA projects: 2012.1.00080.S
- bands: ~86 GHz (Band 3)  
  > "H42$\alpha$ recombination line ($85.6884$ GHz)" (Observation and Data Reduction)
- frequencies and spectral setup: Channel width 244 kHz; velocity resolution 1.7 km/s (488 kHz)  
  > "The frequency channel width is 244 kHz. The velocity resolution is $1.7$ km s$^{-1}$(488 kHz)." (Observation and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: 12-m array 137-pointing mosaic plus 7-m array (ACA) 52-pointing mosaic  
  > "The entire ALMA observation consists of a 137 pointing mosaic of the 12-m array and a 52 pointing mosaic of the 7-m array (ACA)" (Observation and Data Reduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 2.48" x 1.86" (natural); 1.87" x 1.37" (Briggs R=0.5)  
  > "$2.48\ensuremath{''} \times 1.86\ensuremath{''}, PA=89.3^\circ$ and $1.87\ensuremath{''} \times 1.37\ensuremath{''}, PA=84.0^\circ$ using “natural weighting" and “Briggs weighting (R=0.5)"" (Observation and Data Reduction)
- max recoverable scale: 82"  
  > "The resolve-out scale of our maps is as large as $82\ensuremath{''}$ because of ample very short baselines by the ACA." (Channel Maps and Position-velocity Diagrams)
- sensitivity: ~0.7 mJy/beam per 20 km/s channel  
  > "the sensitivity for a 20 km s$^{-1}$ channel is as small as $\sim0.7$ mJy beam$^{-1}$" (Channel Maps and Position-velocity Diagrams)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: H42α recombination line (85.6884 GHz)
- Line: He42α recombination line (85.7233 GHz)
- Other facility **JVLA 34 GHz**: 34 GHz continuum map of protostar candidates  
  > "The black-and-white image shows the continuum emission at 34 GHz observed by JVLA (cite: Yusef-Zadeh2015)." (Protostar Candidates in the Galactic Center Mini-spiral)
- External data: 100 GHz ALMA continuum map of the GCMS used for the continuum flux  
  > "$S_{\mathrm{cont}}(100\mathrm{GHz})$ is calculated from the previous observation of the “Galactic Center Mini-spiral" at 100 GHz (cite: Tsuboi2016)." (Table 1) [from Tsuboi et al. 2016 (cite: Tsuboi2016)]
- External data: Keplerian orbit trajectories for NA and EA+Bar  
  > "the trajectories of the elliptical Keplerian orbits for the NA and EA+Bar which were proposed by Zhao et al (2009)" (Discussion) [from Zhao et al. 2009 (cite: Zhao2009)]
- External data: 34 GHz JVLA protostar candidates  
  > "The black-and-white image shows the continuum emission at 34 GHz observed by JVLA (cite: Yusef-Zadeh2015)." (Protostar Candidates in the Galactic Center Mini-spiral) [from Yusef-Zadeh et al. 2015 (cite: Yusef-Zadeh2015)]
- External data: CS J=2-1 map of the CND  
  > "the CND in the CS $J-2-1$ emission line (cite: Tsuboi2016b)" (Relation between the Western Arc and the Circum-Nuclear Disk) [from Tsuboi et al. 2017 (cite: Tsuboi2016b)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan, Neptune and Mars  
  > "The flux density scale was determined using Titan, Neptune and Mars." (Observation and Data Reduction)
- flux scale uncertainty: as large as 15%  
  > "the absolute flux density accuracy may be as large as 15 %" (Observation and Data Reduction)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural and Briggs R=0.5  
  > "using “natural weighting" and “Briggs weighting (R=0.5)" as *u-v* sampling" (Observation and Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: CASA UVCONTSUB, fitorder=1  
  > "was subtracted from the spectral data using the CASA task UVCONTSUB ($fitorder=1$)" (Observation and Data Reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12-m and ACA mosaic data combined  
  > "because of ample very short baselines by the ACA" (Channel Maps and Position-velocity Diagrams)
- smoothing: _not stated_
- final beam: 2.5"x1.9" natural; 1.9"x1.3" PA=84° Briggs  
  > "The angular resolution is $1.9\ensuremath{''} \times 1.3\ensuremath{''}, PA=84^\circ$ using “briggs weighting (R=0.5)"." (Channel Maps and Position-velocity Diagrams)
- final rms: ~0.7 mJy/beam per 20 km/s  
  > "The sensitivity is $\sim0.7$ mJy beam$^{-1}$\*20 km s$^{-1}$." (Channel Maps and Position-velocity Diagrams)

### Inherited from earlier work

- Full analysis of the mosaic deferred to another paper  
  > "We will present the detailed description of the analysis and the full results in another paper." (Observation and Data Reduction) [from another paper]
- LTE electron temperature correction factor a(ν,Te) from Mezger & Henderson  
  > "is $0.822-0.942$ (cite: Mezger)" (Electron Temperature) [from (cite: Mezger)]
- Electron density formula  
  > "The well-known formula of the electron density is given by" (Electron Density) [from (cite: Altenhoff)]

### Not stated but needed to reproduce (our reading)

- Which of the many observation dates, execution blocks and CASA version were used
- Imaging parameters: cell size, image size, deconvolver, masking, clean threshold
- Line-free channels used in UVCONTSUB
- How 12-m and ACA data were combined
- How line widths and integrated intensities were measured at each position
- Path length L values per position
- Mosaic and primary beam correction details
- Continuum map construction at 86 GHz

## Analysis recipe

1. **Calibrate and image H42α cube**: CASA calibration and imaging, continuum subtracted with UVCONTSUB  
  > "The calibration and imaging of the data were done by CASA (cite: McMullin)." (Observation and Data Reduction)
   - software: CASA
   - parameter: fitorder=1; natural and Briggs R=0.5 weighting  
  > "using the CASA task UVCONTSUB ($fitorder=1$)" (Observation and Data Reduction)
   - fitting: _not stated_
   - validation: Residual at Sgr A* of 5-10 mJy/beam implies GCMS continuum contamination at most ~1%  
  > "This suggests that the contamination from the continuum emission of the GCMS is at most $\sim1$ %." (Observation and Data Reduction)
2. **Kinematics from channel maps and PV diagrams**: Channel maps and position-velocity diagrams along streamers, compared with Keplerian trajectories  
  > "Figure 4 shows the position-velocity diagrams along the substructures of the GCMS in the H42$\alpha$ recombination line." (Channel Maps and Position-velocity Diagrams)
   - assumption: GCBH mass ~4e6 Msun  
  > "Assuming the GCBH mass of $M_{\mathrm {GC}}\sim4\times 10^6$ M$_\ensuremath{\odot}$" (Kinematics of the Bar)
   - fitting: Eyeball comparison of analytic Keplerian PV curves (e=0.5-0.95, various PA) with the Bar ridge; no formal fit  
  > "The curves with $e= 0.8$ seems to well reproduce the observed position-velocity curve of the Bar." (Kinematics of the Bar)
   - validation: _not stated_
3. **LTE electron temperature**: From line-to-continuum ratio and FWHM, iteratively solving the LTE formula  
  > "The LTE electron temperature is obtained by iteratively solving the formula for $T^\ast_{\mathrm e}$." (Electron Temperature)
   - parameter: N(He+)/N(H+)=0.09; a=0.822-0.942  
  > "$\frac{N(\mathrm{He^+})}{N(\mathrm{H^+})}=0.09$, a typical value for the Orion A HII region (cite: Rubin)" (Electron Temperature)
   - assumption: Optically thin line and continuum  
  > "assuming that the line and continuum emissions are optically thin" (Electron Temperature)
   - fitting: _not stated_
   - validation: Typical uncertainty ~15%  
  > "The typical uncertainty is estimated to be as large as 15% of the derived value." (Electron Temperature)
4. **Electron density**: From continuum brightness temperature, Te and path length (Altenhoff formula)  
  > "We also assumed here that the $L$ is equal to the observed width of the boundary (see Figures 1 and 2) and $n_e$ is constant over the path." (Electron Density)
   - assumption: Optically thin continuum; L equals observed streamer width; constant ne  
  > "assuming that the continuum emission is optically thin" (Electron Density)
   - fitting: _not stated_
   - validation: Typical uncertainty ~30%  
  > "The typical uncertainty is estimated to be as large as 30% of the derived value." (Electron Density)

## Software

- **CASA** : calibration, imaging, UVCONTSUB  
  > "The calibration and imaging of the data were done by CASA (cite: McMullin)." (Observation and Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Bar orbit eccentricity | ~0.8 | not stated | dimensionless | 2 | the streamer corresponding to the Bar of the GCMS has a Keplerian orbit with an eccentricity of $e\sim0.8$ |
| Bar orbit inclination | ~80 | not stated | deg | 2 | the inclination angle, is as large as $i\sim80^\circ$ |
| Bar semi-major axis | ~0.5 | not stated | pc | 2 | The semi-major axis and period of the orbit are $a\sim0.5$ pc and $P\sim1.7\times 10^4$ years |
| Bar periastron distance | ~0.1 | not stated | pc | 2 | $a(1-e) \sim0.1$ pc |
| Electron temperature range in NA | 6.4-14.0e3 | 15% | K | 3 | The electron temperatures estimated in the NA are in the range of $T^\ast_{\mathrm e}=(6.4-14.0)\times10^3$ K. |
| Electron temperature range in EA | 5.3-6.0e3 | 15% | K | 3 | They are in the range of $T^\ast_{\mathrm e}=(5.3-6.0)\times10^3$ K. |
| Electron density in NA | 7-13e3 | 30% | cm^-3 | 4 | The electron density in the NA appears to increase from $n_{\mathrm e}=7\times 10^3  ~{\mathrm cm}^{-3}$ to $n_{\mathrm e}=13\times 10^3 ~ {\mathrm cm}^{-3}$ |
| He+/H+ ratio upper limit | <~0.1 | not stated | dimensionless | 1 | less than $\frac{N(\mathrm{He^+})}{N(\mathrm{H^+})} \lesssim0.1$ |

## Qualitative findings

- Protostar candidates correlate positionally with the newly found Northeastern Arm  
  > "There is a good positional correlation between the protostar candidates detected by JVLA at 34 GHz and the ionized gas streamer, Northeastern Arm" (abstract)

## Claim tuples

- H: Do the NA and EA streamers follow the previously derived Keplerian orbits? | E: Compare H42α distribution at 70-90 km/s with Zhao et al. 2009 trajectories | R: Outer parts deviate from inner-region orbits | F: Ambient gas may perturb orbits | **partially**
- H: Is the Bar on an independent Keplerian orbit? | E: Compare Bar PV ridge with analytic eccentric orbits | R: e~0.8, i~80 deg, periastron ~0.1 pc | F: Bar has an independent orbit | **supported**
- H: Do Te and ne increase toward Sgr A*? | E: LTE Te and ne at selected positions | R: Both increase in NA and EA, without lateral expansion | F: External pressure confines streamers | **supported**
- H: Are the protostar candidates tied to ionized streamers? | E: Overlay JVLA 34 GHz candidates on H42α NEA | R: Candidates are concentrated in the NEA | F: Candidates formed in the streamer and were carried inward | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: One-armed spiral model of NA and WA (Lacy 1991; Irons 2012) disfavoured since NA extends north beyond the connecting point  
  > "However, the NA appears to extend north beyond the connecting point in the H42$\alpha$ recombination line" (Kinematics of the Northern Arm and the Eastern Arm)
- How they decided it was enough: _not stated_
- Limitation (authors): Orbital parameters of the Bar cannot be derived accurately from the PV diagram  
  > "it is not easy to derive the orbital parameters accurately from the characteristics of the streamer on the position-velocity diagram" (Kinematics of the Bar)
- Caveat (inferred, ours): Orbit e and i are by-eye matches without fit or uncertainties
- Caveat (inferred, ours): Single-component Te/ne assumes optically thin, constant density along the path with L set to the observed width
- Caveat (inferred, ours): Fixed Te=1e4 K and He ratio assumed
- Caveat (inferred, ours): Continuum subtraction residuals near Sgr A* may affect Te
- Caveat (inferred, ours): Ram-pressure argument is order-of-magnitude

## Reproducibility

- Data public (paper): Project code given and cited as ALMA data in acknowledgments  
  > "This paper makes use of the following ALMA data:ADS/JAO.ALMA#2012.1.00080.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters and line-free channels
- Missing: Per-position spectral measurement procedure
- Missing: The 100 GHz continuum map from Tsuboi 2016
- Data volume (inferred): Large (hundreds of GB; 137+52 pointing mosaic, Cycle 1)
- Score (inferred): 3/5, Public data and simple formulae, but imaging and measurement details are sparse and orbit results are qualitative.
- Rediscovery candidate: no, Imaging and line measurement recipe incomplete and key results are by-eye orbit matches.

## Links

- Method: McMullin et al. 2007 (cite: McMullin) (CASA)
- Companion: Tsuboi et al. 2016 (cite: Tsuboi2016) (100 GHz ALMA continuum of the GCMS)
- Companion: Tsuboi et al. 2017 (cite: Tsuboi2016b) (CS and SiO molecular line results from the same mosaic)
- Related: 2012.1.00080.S

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
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
  "facts": 72,
  "stated": 42,
  "rate": 0.583
 },
 "evidence_ok": true
}
```

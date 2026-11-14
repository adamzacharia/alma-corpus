# Gas flow and accretion via spiral streamers and circumstellar disks in a young binary protostar

`2019Sci...366...90A` | Science 2019 | first author: Alves, F. O. | arXiv: 1910.01141 | DOI: 10.1126/science.aaw3491

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks
- Question: How does gas flow from the circumbinary disk onto the circumstellar disks and the two protostars in the young binary [BHB2007] 11, and which component accretes preferentially?  
  > "We seek to investigate the dynamical evolution of a binary system still embedded in its natal cloud, where gas from a circumbinary disk is expected to accrete onto each binary component." (Main text)
- Target **[BHB2007] 11**: coordinates α = 17h11m23.18s, δ = -27°24′31.5″ (J2000)  
  > "[BHB2007] 11 (α = 17 [h] 11 [m] 23.18 [s], δ = -27°24′31.5″) [1] is the youngest member" (Main text); "at the B59 distance of 163 pc ( _10_ ))" (Materials and Methods); z/distance 163 pc  
  > "[BHB2007] 11 (α = 17 [h] 11 [m] 23.18 [s], δ = -27°24′31.5″) [1] is the youngest member" (Main text); "at the B59 distance of 163 pc ( _10_ ))" (Materials and Methods); distance from Dzib et al. 2018 (Gaia DR2)  
  > "[BHB2007] 11 (α = 17 [h] 11 [m] 23.18 [s], δ = -27°24′31.5″) [1] is the youngest member" (Main text); "at the B59 distance of 163 pc ( _10_ ))" (Materials and Methods)

## Data provenance

- ALMA projects: 2016.1.01186.S, 2013.1.00291.S
- bands: Band 6 (225.3 GHz, 1.3 mm); Band 3 (97.5 GHz) continuum also used  
  > "The Band 6 (225.3 GHz) ALMA data were observed in two Execution Blocks (EBs)" (Materials and Methods); "The observing setup of the ALMA Band 3 (97.5 GHz) continuum data discussed only in" (Materials and Methods)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 2.4 GHz  
  > "The full continuum bandwidth is 2.4 GHz." (Materials and Methods)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 92.1 m to 13.9 km  
  > "The antenna configurations had baselines between 92.1 m and 13.9 km." (Materials and Methods)
- angular resolution: 45 × 30 mas (~6 au), PA −86°  
  > "45 × 30 milliarcseconds (mas) (~ 6 au) and a position angle of" (Materials and Methods)
- max recoverable scale: ~0.8″ (~130 au)  
  > "sensitive to an extended emission of ~ 0.8″ (~ 130 au, at the B59 distance of 163 pc" (Materials and Methods)
- sensitivity: 19 µJy/beam (Band 6 continuum)  
  > "The noise level of the image is 19 µJy beam [-1] ." (Materials and Methods)
- time on source: 2.4 hours  
  > "The total on-source observing time was 2.4 hours" (Materials and Methods)
- observing dates: 5 and 23 November 2017, 43 and 48 antennas  
  > "on the 05 [th] and 23 [rd] of November 2017, with 43 and 48 antennas of the main array" (Materials and Methods)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (not stated)
- Line: H2CO 3(2,1)-2(2,0) (218.76 GHz)
- Other facility **VLA**: Continuum at 10, 15, 22, 34.5 GHz in A configuration (project 16B-290)  
  > "The VLA observations were carried out in the A configuration for several runs between" (Materials and Methods)
- Other facility **Herschel**: 250 µm map of the B59 core  
  > "The core of Barnard 59 observed at 250 µm with the _Herschel_ space telescope" (Figure 1 caption)
- External data: Previous ALMA CO(2-1)/H2CO data and Band 3 data  
  > "Using the molecular line data reported in ( _8, 11_ ), we performed two-dimensional Gaussian" (Materials and Methods) [from Alves et al. 2017 (cite 8); Alves et al. 2018 (cite 11)]
- External data: Bolometric luminosity of [BHB2007] 11  
  > "From the [BHB2007] 11 bolometric" (Materials and Methods) [from Brooke et al. 2007 (cite 7)]

## Processing

### Calibration

- pipeline or manual: Standard calibration by ALMA staff (QA2)  
  > "The standard calibration of the visibilities was performed by the ALMA staff as part of the" (Materials and Methods)
- casa version: CASA 5.4.0  
  > "We have selfcalibrated the continuum using CASA 5.4.0 ( _21_ )" (Materials and Methods)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: QSO B1730-130 bootstrapped; bandpass B1921-293; gain J1700-2610  
  > "Absolute flux" (Materials and Methods); "calibration was obtained by bootstrapping of the flux density of QSO B1730-130 to the bandpass" (Materials and Methods)
- flux scale uncertainty: ~15%  
  > "We expect an uncertainty of about 15% in the absolute flux density scale" (Materials and Methods)
- self calibration: Phase self-cal with decreasing solint down to integration length, then one amplitude round, one solution per EB; SNR up ~13%  
  > "We then performed one round of self-calibration on" (Materials and Methods)

### Imaging

- task: CASA tclean  
  > "We produced maps with the CASA tclean task using Briggs weighting (robust factor 0.5)" (Materials and Methods)
- deconvolver: _not stated_
- weighting robust: Briggs robust 0.5 (Band 6); robust 1 (Band 3 long baselines)  
  > "Briggs weighting (robust factor 0.5), and multiscale cleaning" (Materials and Methods)
- uv taper: Band 3: only baselines >4.6 km (>1500 kλ) used  
  > "baselines longer than 4.6 km), which correspond to a _uv_ distance larger than" (Materials and Methods)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: 0, 1, 5, 15 times synthesized beam  
  > "multiscale cleaning on scales" (Materials and Methods)
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 45 × 30 mas, PA −86°  
  > "45 × 30 milliarcseconds (mas)" (Materials and Methods)
- final rms: 19 µJy/beam  
  > "The noise level of the image is 19 µJy beam [-1] ." (Materials and Methods)

### Inherited from earlier work

- Band 3 observing setup  
  > "was reported in ( _11_ ), which presented images obtained using part of" (Materials and Methods) [from Alves et al. 2018 (cite: 11)]
- CO/H2CO data from earlier work  
  > "We measured kinematics by re-analyzing ( _9_ ) previous observations ( _8_ )" (Main text) [from Alves et al. 2017 (cite: 8)]
- Keplerian PV fitting method  
  > "following the" (Materials and Methods) [from Seifried et al. 2016 (cite 28)]

### Not stated but needed to reproduce (our reading)

- Self-calibration solution intervals and number of rounds
- Clean threshold, mask and image size/cell size
- Continuum-free channels used for line cubes
- Details of line cube imaging for CO and H2CO
- Filament spine extraction procedure
- Circumbinary disk mass inputs from Alves 2017

## Analysis recipe

1. **Self-calibrate and image continuum**: Self-cal then tclean multiscale  
  > "We produced maps with the CASA tclean task using Briggs weighting (robust factor 0.5)" (Materials and Methods)
   - software: CASA
   - fitting: _not stated_
   - validation: SNR improvement ~13%  
  > "shows an increase in signal-to-noise ratio (SNR) of about 13%" (Materials and Methods)
2. **Measure source sizes, inclinations, fluxes**: Gaussian fit to 225.3 GHz map; inclination from axis ratio  
  > "we use this map to fit a Gaussian model to determine the deconvolved beam sizes of" (Materials and Methods)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive disk and filament masses**: Modified blackbody, Eq. S8, optically thin/thick cases  
  > "The observed intensity of the dust emission at a particular frequency, _I_ ν, can be described as" (Materials and Methods)
   - assumption: κ250GHz = 1.7 cm2/g dust, gas-to-dust 100, Tdust ~110 K at 3 au (1.75 Lsun each); filament Tdust 40-100 K  
  > "we adopt the canonical gas-to-dust ratio of 100" (Materials and Methods)
   - fitting: _not stated_
   - validation: _not stated_
4. **CO kinematics and dynamical mass**: 2D Gaussian fits per channel for peak positions; Keplerian fit to H2CO PV diagram  
  > "we performed two-dimensional Gaussian" (Materials and Methods)
   - parameter: SNR threshold 5; PV emission >5σ  
  > "(we used a threshold SNR of 5)" (Materials and Methods)
   - fitting: _not stated_
   - validation: _not stated_
5. **Accretion rate, Toomre Q, ionized mass loss**: Free-fall accretion estimate; Q approximation; Anglada jet formula with VLA free-free flux  
  > "the ionized mass loss rate 𝑀 ion" (Materials and Methods)
   - assumption: jet θ=10°, v=200 km/s, T=1e4 K; M*≈1.0 Msun; 15% flux error  
  > "We adopted _θ_ =" (Materials and Methods)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.4.0: self-calibration and imaging of ALMA data; VLA pipeline  
  > "We have selfcalibrated the continuum using CASA 5.4.0" (Materials and Methods)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk radius [BHB2007] 11A | 3.1 | ±0.6 | au | 2 | 3.1 ± 0.6 au ([BHB2007] 11A) and 2.1 ± 0.5 au ([BHB2007] 11B) |
| Disk radius [BHB2007] 11B | 2.1 | ±0.5 | au | 2 | 3.1 ± 0.6 au ([BHB2007] 11A) and 2.1 ± 0.5 au ([BHB2007] 11B) |
| Dynamical mass | 2.25 | ±0.13 | Msun | 4 | of 2.25 ± 0.13 M ⊙, which represents an upper limit |
| Mass accretion rate | 1.1e-5 | not stated | Msun/yr | 5 | ~ 1.1 x 10 [-5] |
| Toomre Q | 3.9 | not stated | dimensionless | 5 | the Toomre parameter _Q_ is ~ 3.9 |
| Circumbinary disk mass | 0.08 | ±0.03 | Msun | 3 | the circumbinary disk mass is 0.08 ± 0.03 M ⊙ . |
| Ionized mass loss rate 11A | 6.4e-10 | ±0.7e-10 | Msun/yr | 5 | (6.4 ± 0.7) × 10 [-10] |

## Qualitative findings

- Filaments are accretion streamers from the circumbinary disk, not disk fragmentation products  
  > "This reinforces our conclusions that the filaments are accretion streamers" (Materials and Methods)

## Claim tuples

- H: Spiral filaments arise from disk fragmentation | E: Toomre Q and filament mass per length | R: Q~3.9; ~10 Msun/pc below critical | F: Filaments are not from fragmentation but are accretion streamers | **supported**
- H: Accretion is preferential onto the lower-mass companion | E: CO high-velocity peaks and VLA radio jet | R: High velocities centered on 11B; stronger jet on 11A | F: Circumbinary accretion preferentially onto secondary, consistent with theory | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Envelope accretion, misaligned disks or eccentric orbit could also produce substructure  
  > "could also produce substructure such as filaments in the circumbinary disk" (Main text)
- How they decided it was enough: _not stated_
- Limitation (authors): Accretion rate is rough, assuming free fall from rest along a straight line  
  > "This is a rough estimate of the value of the mass accretion rate" (Materials and Methods)
- Caveat (inferred, ours): Disk masses depend strongly on assumed opacity, temperature and optical depth
- Caveat (inferred, ours): Dynamical mass from H2CO is an upper limit
- Caveat (inferred, ours): Primary identification relies partly on radio jet strength

## Reproducibility

- Data public (paper): ALMA and VLA data archived  
  > "The data reported in this paper are archived in the ALMA Science Archive" (Data availability)
- Products in archive: _not stated_
- Missing: Self-cal parameters
- Missing: Line cube imaging settings
- Missing: Filament mask details
- Data volume (inferred): ~100-300 GB
- Score (inferred): 3/5, Public data and main parameters given, but self-cal, line imaging details and some assumptions are incomplete.
- Rediscovery candidate: yes, Public data, stated imaging parameters and numeric results (sizes, masses, fluxes) can be redone.

## Links

- Method: Seifried et al. 2016 (cite 28) (Keplerian PV fitting method)
- Companion: Alves et al. 2017 (cite 8) (Earlier ALMA CO data)
- Companion: Alves et al. 2018 (cite 11) (Band 3 and polarization data)
- Related: Herschel Gould Belt Survey

## Checks

```json
{
 "quotes": 65,
 "quotes_ok": 65,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 44,
  "rate": 0.611
 },
 "evidence_ok": true
}
```

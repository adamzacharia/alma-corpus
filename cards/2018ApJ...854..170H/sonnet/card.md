# The Extraordinary Outburst in the Massive Protostellar System NGC 6334I-MM1: Emergence of Strong 6.7 GHz Methanol Masers

`2018ApJ...854..170H` | The Astrophysical Journal 2018 | first author: Hunter, T. R. | arXiv: 1801.02141 | DOI: 10.3847/1538-4357/aaa962

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, astrochemistry
- Question: Where do the new 6.7 GHz methanol and excited OH masers appear relative to the MM1 millimeter outburst in NGC6334I, and what do they imply about maser pumping and magnetic fields?  
  > "We report the first sub-arcsecond VLA imaging of 6 GHz continuum, methanol maser, and excited-state hydroxyl maser emission toward the massive protostellar cluster NGC6334I following the recent 2015 outburst" (abstract)
- Target **NGC6334I (MM1, MM2, MM3/UCHII, CM2)**: coordinates MM3 UCHII masers near 17:20:53.4 -35:47:01.5 (J2000)  
  > "UCHII-Met4  | 17:20:53.370  | -35:47:01.52" (Table 3); z/distance _not stated_; distance from cited as Chibueze14; Reid14 (no value given in text)  
  > "UCHII-Met4  | 17:20:53.370  | -35:47:01.52" (Table 3)

## Data provenance

- ALMA projects: 2015.A.00022.T
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ALMA CH3OH cube beam 0.29'' x 0.22'' PA -84 deg  
  > "has a beamsize of $0.29\ensuremath{''} \times 0.22\ensuremath{''}$ at position angle $-84^\circ$" (Observations)
- max recoverable scale: _not stated_
- sensitivity: 1.7 mJy/beam in 1.1 km/s channels (ALMA)  
  > "The rms noise achieved is 1.7 mJy beam$^{-1}$ in 1.1 km s$^{-1}$ wide channels." (Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CH3OH 11(2)-10(3) A- (279.35191 GHz)
- Other facility **VLA**: C-band (6.7 GHz CH3OH, 6.030/6.035 GHz OH, 5 cm continuum) and K-band H64alpha data  
  > "Project code | 16B-402 | 10C-186" (Table 1)
- External data: 1.3 mm dust continuum brightness temperature and MM1 component properties  
  > "the dust temperature of MM1 inferred directly from the 1.3 mm continuum brightness temperature exceeds 250 K toward the central components" (Discussion) [from (cite: Brogan16)]
- External data: Einstein A and collisional cross section for CH3OH 11(2)-10(3)  
  > "where the values are taken from (cite: Rabli10) via the LAMDA database (cite: Schoier10)" (Discussion) [from (cite: Rabli10); (cite: Schoier10)]

## Processing

### Calibration

- pipeline or manual: VLA pipeline with extra flagging for C band; manual CASA scripts for K band  
  > "The data were calibrated using the VLA pipeline" (Observations); "These data were calibrated in CASA using manually generated scripts prior to the development of the pipeline." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: 3C286 (VLA)  
  > "Flux calibrator | 3C286 | 3C286" (Table 1)
- flux scale uncertainty: _not stated_
- self calibration: 6.7 GHz maser used to self-calibrate; solutions applied to other line and continuum data  
  > "The bright 6.7 GHz maser emission was used to iteratively self-calibrate the 6.7 GHz line emission and the resulting solutions were applied to the other line and continuum data." (Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: VLA C band robust -1.0; K band +1.0; ALMA robust 0  
  > "Robust clean parameter | $-1.0$ | +1.0" (Table 1); "The data cube was cleaned with a robust parameter of 0" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: scales 0, 5, 15 pixels (continuum, multi-term multi-scale clean)  
  > "multi-term multi-scale clean was used with scales of 0, 5, and 15 times the image pixel size" (Observations)
- continuum subtraction: uv-plane subtraction for maser cubes  
  > "After subtracting the continuum in the uv-plane, spectral cubes of the maser emission were made" (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA observing parameters and data processing  
  > "for which the observing parameters are described in more detail in (cite: Hunter17)" (Observations) [from (cite: Hunter17)]

### Not stated but needed to reproduce (our reading)

- VLA image size and cell size
- CASA version used
- ALMA calibration and imaging details (CASA version, clean mask, line-free channels)
- Distance adopted to NGC6334I
- Beam-fit and Gaussian fitting software/tool

## Analysis recipe

1. **Fit maser spots per channel**: Fit 2D Gaussians with shape fixed to synthesized beam to each channel with >6 sigma emission; manual inspection to discard artifacts  
  > "we fit each channel of the cube that had significant emission ($> 6\sigma$, measured independently for each channel) with an appropriate number of two-dimensional Gaussian sources." (6.7 GHz methanol masers)
   - fitting: _not stated_
   - validation: manual inspection of all fits  
  > "After manual inspection of all the fits, a few of the weakest features that formally met the sensitivity criterion could be attributed to imaging artifacts" (6.7 GHz methanol masers)
2. **Derive line-of-sight magnetic field from OH Zeeman pairs**: Pair RCP/LCP spots within 1/3 of beam minor axis, fit Gaussians, B = (Vc(RCP)-Vc(LCP))/Z  
  > "$B_{los}=$($V_{center}(RCP) - V_{center}(LCP)$)$/Z$ where $Z = 0.056$ km s$^{-1}$mG$^{-1}$ for the 6.035 GHz transition and $0.079$ km s$^{-1}$mG$^{-1}$ for the 6.030 GHz transition" (Zeeman splitting)
   - fitting: Gaussian profile fits per polarization  
  > "Then the RCP and LCP profiles for each Zeeman pair were independently fitted using Gaussian profiles." (Zeeman splitting)
   - validation: compared with Caswell11 LBA Zeeman pairs; agreement within 10%  
  > "differences in $B_{los}$ are less than $10\%$" (Zeeman splitting)

## Software

- **CASA** : K-band calibration with manual scripts; VLA pipeline  
  > "These data were calibrated in CASA using manually generated scripts" (Observations)
- **Astropy** : acknowledged analysis package  
  > "Astropy, a community-developed core Python package for Astronomy" (Acknowledgments)
- **APLpy** : plotting  
  > "APLpy, an open-source plotting package for Python" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Peak 6.7 GHz maser flux density in MM1 | 545 | not stated | Jy | 1 | The brightest 6.7 GHz features in MM1 (peak = 545 Jy at $-7.25$ km s$^{-1}$) |
| Line-of-sight B toward CM2 | +0.5 to +3.7 | not stated | mG | 2 | we measure a line-of-sight magnetic field of +0.5 to +3.7 mG toward CM2 |
| Line-of-sight B toward UCHII | -2 to -5 | not stated | mG | 2 | predominantly negative line-of-sight magnetic field strengths of $-2$ to $-5$ mG |
| Critical density CH3OH 11(2)-10(3) | 6e7 | not stated | cm^-3 | 0 | yielding $n_{crit} = 6\times10^7$ cm$^{-3}$ |

## Qualitative findings

- Strongest MM1 masers lie in dust cavities, absent toward MM1A, B, D  
  > "The strongest MM1 masers trace a dust cavity, while no masers are seen toward the strongest dust sources MM1A, 1B and 1D." (abstract)

## Claim tuples

- H: Did the outburst produce new 6.7 GHz methanol masers in MM1? | E: Sub-arcsecond VLA imaging at 6.7 GHz | R: New maser features in MM1 and CM2 with no previous detections in three decades | F: MM1 now hosts Class II methanol masers linked to the outburst | **supported**
- H: Do maser locations match pumping expectations? | E: Compare masers with ALMA dust and thermal CH3OH | R: Masers lie in regions of high methanol column density | F: Consistent with elevated dust temperature, IR propagation cavities, and high CH3OH column | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Resolution larger than maser spots, so brightness temperatures are lower limits  
  > "Lower limits to the brightness temperature $T_B$ using the synthesized beam" (Table 3)
- Caveat (inferred, ours): Zeeman pair identification is ambiguous at ~520 au resolution
- Caveat (inferred, ours): Brightness temperatures are only lower limits
- Caveat (inferred, ours): ALMA analysis is minimal and qualitative

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: VLA imaging parameters such as image and cell size
- Missing: CASA version
- Missing: Machine-readable tables are only in the online journal
- Data volume (inferred): VLA C band high-resolution A-config data, likely tens to hundreds of GB; ALMA cube a few GB
- Score (inferred): 3/5, VLA recipe partly described; ALMA role minor and details deferred to Hunter17.
- Rediscovery candidate: no, VLA data public status not stated; imaging parameters incomplete.

## Links

- Companion: (cite: Hunter17) (Describes the ALMA observations and the outburst)
- Companion: (cite: MacLeod17) (HartRAO single-dish maser monitoring)
- Companion: (cite: Brogan16) (Earlier ALMA and VLA study of NGC6334I)
- Related: HartRAO maser monitoring

## Checks

```json
{
 "quotes": 36,
 "quotes_ok": 36,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 58,
  "stated": 25,
  "rate": 0.431
 },
 "evidence_ok": true
}
```

# Absorption Filaments toward the Massive Clump G0.253+0.016

`2014ApJ...795...28B` | The Astrophysical Journal 2014 | first author: Bally, John | arXiv: 1409.3640 | DOI: 10.1088/0004-637X/795/1/28

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type observational_alma_primary

## Science

- Fields: milky_way_ism, star_formation
- Question: What are the nature and origin of the absorption filaments seen in ALMA HCO+ J=1-0 toward the CMZ cloud G0.253+0.016, and what do they imply for the cloud's dynamical state?  
  > "high-angular resolution, high dynamic range, and sensitive ALMA observations of J = 1 _−_ 0 HCO [+] are presented that reveal an extensive network of filaments
seen in absorption toward G0.253+0.016." (1. Introduction)
- Target **G0.253+0.016 (the Brick)**: coordinates _not stated_; z/distance 8.5 kpc (distance of the CMZ)  
  > "corresponding to a linear scale of 0.07 pc at the
8.5 kpc distance of the CMZ." (2. Observations); distance from assumed distance of the CMZ, no citation given  
  > "corresponding to a linear scale of 0.07 pc at the
8.5 kpc distance of the CMZ." (2. Observations)

## Data provenance

- ALMA projects: 2011.0.00217.S
- bands: Band 3 (3 mm)  
  > "G0.253+0.016 was imaged in the 3 mm wavelength bands (ALMA band 3) using 25
of ALMA’s 12-meter diameter antennas." (2. Observations)
- frequencies and spectral setup: 10 molecular lines, 0.488 MHz resolution (~1.5 km/s), VLSR -200 to +240 km/s  
  > "to observe 10 different molecular emission lines
with a resolution of 0.488 MHz (about 1.5 km s _[−]_ [1] velocity resolution)" (2. Observations)
- continuum bandwidth: 1.875 GHz  
  > "The ALMA correlator was configured to measure
the continuum in a 1.875 GHz bandpass" (2. Observations)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 13 to 455 m  
  > "Baselines ranged from 13 to 455 meters." (2. Observations)
- angular resolution: 1.7 arcsec  
  > "The synthesized beam produced by ALMA at
this frequency has a diameter of 1.7 _[′′]_" (2. Observations)
- max recoverable scale: _not stated_
- sensitivity: about 5 mJy (0.26 K) rms per channel in 1.7" beam  
  > "The rms noise in each frequency channel is about 5 mJy (0.26 K) in the 1.7 _[′′]_
beam." (2. Observations)
- time on source: _not stated_
- observing dates: 29 July to 1 August 2012, six occasions  
  > "G0.253+0.016 was imaged on six separate occasions over the period 29 July to 1 August 2012." (2. Observations)
- pi or archival as stated: _not stated_
- Line: HCO+ J=1-0 (89.1885 GHz)
- Other facility **Mopra 22 m (MALT90)**: Single-dish maps used to restore zero spacings in ALMA data  
  > "The resulting maps were used to restore 0-spacings
in the ALMA data in the Fourier domain (Rathborne et al. 2014a)." (2. Observations)
- External data: 20 and 6 cm radio continuum images of G0.18 non-thermal filaments  
  > "seen in 20 and 6 cm wavelength radio continuum images
of Yusef-Zadeh et al. (2004)." (3. Results) [from Yusef-Zadeh et al. (2004)]
- External data: 12C/13C abundance ratio ~24 in the CMZ  
  > "finding that in the CMZ _X_ 12 _/_ 13 _≈_ 24." (3.1 Opacity) [from Langer & Penzias (1990)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Each data set independently calibrated before merging; details deferred  
  > "Each data set was
independently calibrated prior to merging." (2. Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.35 arcsec per pixel  
  > "Final data cubes were gridded to a pixel scale of 0.35 _[′′]_ per pixel." (2. Observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Mosaic of 13 pointings; Mopra zero-spacing added in Fourier domain  
  > "a mosaic consisting of 13 separate
pointings was required." (2. Observations)
- smoothing: Resampled to 3.4 km/s channels  
  > "the data were re-sampled to 3.4 km s _[−]_ [1] per
channel." (2. Observations)
- final beam: 1.7 arcsec  
  > "has a diameter of 1.7 _[′′]_" (2. Observations)
- final rms: about 5 mJy (0.26 K) per channel  
  > "The rms noise in each frequency channel is about 5 mJy (0.26 K) in the 1.7 _[′′]_
beam." (2. Observations)

### Inherited from earlier work

- Full observation details and data reduction, including zero-spacing restoration  
  > "Full details of
the observations and data reduction will be presented in another paper (Rathborne et al.
2014a)." (2. Observations) [from Rathborne et al. 2014a (ApJ, submitted)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibrators
- Imaging task, deconvolver, weighting/robust, masking, clean threshold
- Continuum subtraction and line-free channels
- Zero-spacing combination method details
- Exact spectral windows and the other 8 lines' frequencies
- Pointing coordinates of the mosaic
- Procedure for selecting off-positions for absorption depth

## Analysis recipe

1. **Identify and classify absorption filaments**: Inspect 3.4 km/s channel maps and spatial-velocity cuts/spectra across filaments; split into BLA and NLA by linewidth  
  > "The absorption
filaments can be subdivided into two categories based on their observed properties:" (3. Results)
   - fitting: _not stated_
   - validation: _not stated_
2. **Estimate HCO+ optical depth from 12/13 ratio**: Compare area-integrated HCO+ and H13CO+ intensities with an assumed isotope ratio  
  > "_τ_ 12 _≈_ _X_ 12 _/_ 13 _ln_ [ _R_ 12 _/_ 13 _/_ ( _R_ 12 _/_ 13 _−_ 1)] _∼_ 2 _._ 5" (3.1 Opacity)
   - assumption: X12/13 = 24, equal Tex for both species, brightness = Tex for HCO+  
  > "Assuming that the _X_ 12 _/_ 13 is 24 in G0.253+0.016, that the excitation temperatures of
H [13] CO [+] and HCO [+] are the same" (3.1 Opacity)
   - fitting: _not stated_
   - validation: _not stated_
3. **Excitation and column density of absorbers**: Liszt & Lucas column-density formula plus RADEX grid for density/column/Tex/tau  
  > "Table 2 lists the excitation temperatures ( _T_ _ex_ ), opacities ( _τ_ ), and brightness temperatures ( _T_ _R_ ) for the J = 1 _−_ 0 transition of HCO [+] for a range of molecular hydrogen volume
densities" (3.1 Opacity)
   - software: RADEX
   - parameter: Tkin = 60 K, linewidth 10 km/s, background 2.73 K  
  > "gas kinetic temperature of 60 K, and a line-width of 10 km s _[−]_ [1]" (Table 2)
   - assumption: X(HCO+) = 1e-7, filament depth equal to projected width  
  > "abundance
_X_ ( _HCO_ [+] ) = 10 _[−]_ [7], assuming that the depth of the filament is comparable to its projected
width" (3.1 Opacity)
   - fitting: _not stated_
   - validation: _not stated_
4. **Estimate surface mass-loss rate and compare mechanisms**: Order-of-magnitude mass-loss estimate; compare photo-ablation and magnetic bounce energetics  
  > "For _f_ = 0.5
and _n_ ( _H_ 2 ) = 10 [3] cm _[−]_ [3]" (4. The Dynamic State)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **RADEX** : Non-LTE radiative transfer grid of HCO+ J=1-0 (online tool)  
  > "using the radiative transfer code RADEX
(van der Tak et al. 2007)" (3.1 Opacity)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HCO+/H13CO+ intensity ratio, northern part | 10 | ±1 | dimensionless | 2 | _R_ 12 _/_ 13 = I(HCO [+] )/I(H [13] CO [+] ) = 10 _±_ 1 for the
northern part of G0.253+0.016 |
| HCO+/H13CO+ intensity ratio, southern part | 11 | ±1 | dimensionless | 2 | _R_ 12 _/_ 13 = 11 _±_ 1 for the southern part |
| HCO+ J=1-0 mean optical depth | ~2.5 (1.5 to 2.5 for X12/13 17-40) | not stated | dimensionless | 2 | _τ_ 12 ranges from 1.5 to 2.5. |
| BLA absorption optical depth mean | 0.7 (range 0.2 to 2) | not stated | dimensionless | 1 | the optical depth of the absorbing gas ranges from _∼_ 0.2 to about 2 with a mean value
of 0.7. |
| Absorber HCO+ column density | 1e13 (Tex=2.73 K) to 6e13 (Tex=10 K) | not stated | cm^-2 | 3 | the
column density of HCO [+] absorbers is _N_ 0 _≈_ 10 [13] cm _[−]_ [2] for _T_ _ex_ = 2.73 K, and 6 _×_ 10 [13] cm _[−]_ [2]
for _T_ _ex_ = 10 K. |
| Surface mass-loss rate | 0.03 to 0.06 | not stated | Msun/yr | 4 | _M_ _∼_ 0.03 to 0.06 M _⊙_ yr _[−]_ [1] . |
| Required mean magnetic field for bounce | ~1.5 | not stated | milli Gauss | 4 | these parameters imply a mean magnetic field strength _B_ _∼_ 1.5 milli Gauss |

## Qualitative findings

- HCO+ emission is area-filling, optically thick and sub-thermally excited; BLAs seen only in HCO+  
  > "The 89 GHz emission
is area-filling, optically thick, and sub-thermally excited." (abstract)

## Claim tuples

- H: Is HCO+ emission from the Brick sub-thermally excited? | E: Compared HCO+ and H13CO+ intensities and brightness temperatures with gas temperature | R: Brightness 2-12 K versus Tkin 60-80 K; ratio ~10; n(H2) ~1e3 cm^-3 | F: Excitation is sub-thermal at the tau~1 surface | **supported**
- H: Do the NLA filaments reveal the cloud's surface dynamics? | E: Mapped blueshifted absorption filaments against HCO+ emission | R: NLAs mostly blueshifted, some in HCN, some in emission at cloud edges | F: Cloud surface layers are expanding, perhaps driven by stored magnetic energy | **partially**
- H: What are the BLA filaments? | E: Compared BLA orientation with G0.18 non-thermal filaments and considered shock-sheet versus magnetic models | R: BLAs parallel to nonthermal filaments, PA ~125-140 deg | F: Either foreground magnetic structures or edge-on shock sheets; not decided | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Photo-ablation judged an unlikely source of expansion (mass-loss ~1e-3 Msun/yr, an order of magnitude too low)  
  > "photo-ablation is an unlikely
source of cloud surface layer expansion." (5.1 Photo-ablation?)
- How they decided it was enough: _not stated_
- Limitation (authors): Mass-loss rate is poorly constrained; density is an upper bound, column a lower bound, layer thickness unknown  
  > "The mass-loss rate is difficult to estimate because the density on the absorbing layer
is an upper bound" (4. The Dynamic State)
- Caveat (inferred, ours): Absorption interpretation depends on assumed isotope ratio, abundance and geometry
- Caveat (inferred, ours): Foreground versus surface location of filaments is not established
- Caveat (inferred, ours): Zero-spacing and calibration handled in a companion paper, not verifiable here

## Reproducibility

- Data public (paper): ALMA Cycle 0 project cited in acknowledgments; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00217.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Calibration and imaging recipe (deferred to Rathborne et al. 2014a)
- Missing: Mopra zero-spacing combination details
- Missing: Filament selection and off-position definitions
- Data volume (inferred): ~50-200 GB raw for six Band 3 mosaic execution blocks
- Score (inferred): 2/5, Processing deferred to a companion paper; results are mostly qualitative with order-of-magnitude estimates.
- Rediscovery candidate: no, Recipe incomplete and main results largely qualitative.

## Links

- Method: Rathborne et al. 2014a (ApJ, submitted) (Full observations, data reduction and zero-spacing restoration)
- Companion: Rathborne et al. 2014b, ApJ, 786, 140 (Single-dish Mopra/APEX analysis of the cloud; baked-Alaska versus P-Cygni interpretation)
- Related: MALT90
- Related: Hi-GAL
- Related: BGPS

## Checks

```json
{
 "quotes": 46,
 "quotes_ok": 46,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 32,
  "rate": 0.485
 },
 "evidence_ok": true
}
```

# Estimating the Temperature and Density of a Spicule from 100 GHz Data Obtained with ALMA

`2020ApJ...888L..28S` | The Astrophysical Journal Letters 2020 | first author: Shimojo, Masumi | arXiv: 1912.05714 | DOI: 10.3847/2041-8213/ab62a5

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: sun
- Question: What are the temperature and density of a spicule seen at 100 GHz with ALMA, and how does it relate to spicules seen in IRIS Mg II and AIA 304 A?  
  > "To obtain the physical parameters of the 100GHz spicule, we estimate the optical depths as a function of temperature and density using two different methods." (abstract)
- Target **100GHz spicule and MgII/304A spicule (solar limb, 26 April 2017)**: coordinates not stated (limb near X=956'' in Mg II)  
  > "In the Mg II image, the solar limb is located around X=956$''$" (3 The spicules observed with ALMA, IRIS, and AIA/SDO); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00070.S
- bands: Band 3, 100 GHz  
  > "We used the Band3 receiver and the Time Division Mode (TDM) of the correlator." (2 Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: about 8 GHz (full TDM range)  
  > "a synthesized image shows a distribution of intensity at 100 GHz with a bandwidth of about 8 GHz." (2 Observations)
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: synthesized beam 2.67'' x 1.88''  
  > "The sizes of the synthesized beam are 2$''$.67 and 1$''$.88 along the major and minor axes, respectively." (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: noise ~2.6 K  
  > "This signal level is much larger than the noise, i.e. $\sim$2.6 K (Shimojo et al. 2017b)." (3 The spicules observed with ALMA, IRIS, and AIA/SDO)
- time on source: _not stated_
- observing dates: 14:22-16:13 UT on 26 April 2017  
  > "our observation was carried out between 14:22 – 16:13UT on 26 April 2017." (2 Observations)
- pi or archival as stated: _not stated_
- Other facility **IRIS**: Mg II 2796 slit-jaw images, 40 s cadence, 0.4'' resolution  
  > "IRIS obtained slit-jaw images of Mg II (2796Å) bands with a cadence and a spatial resolution of 40 s and 0$''$.40, respectively." (2 Observations)
- Other facility **SDO/AIA**: 304 A and 193 A context images, 12 s cadence, 1.5'' resolution  
  > "We also use 304Å (He II) and 193Å (Fe XII) band images taken with AIA. They provide context filtergrams with a cadence of 12 s." (2 Observations)
- External data: Temperature range 4000-7000 K for the spicule from Rutten (2017) Figure 1  
  > "According to the lower-right panel of Figure 1 in (cite: 2017A&A...598A..89R), the temperature of the 100GHz spicule should be 4000 – 7000 K." (3 The spicules observed with ALMA, IRIS, and AIA/SDO) [from (cite: 2017A&A...598A..89R)]

## Processing

### Calibration

- pipeline or manual: standard calibration of Shimojo et al. 2017b, then phase-only self-calibration  
  > "we carried out the self-calibration only for the phase after the standard calibration described in (cite: 2017SoPh..292...87S)." (2 Observations)
- casa version: CASA 5.4.0  
  > "The CLEAN deconvolution method is used for the image synthesis with the Clark algorithm and Briggs weighting scheme on CASA 5.4.0 (cite: 2007ASPC..376..127M)." (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: 5 steps, solution intervals from 10 min to 2 s, phase only  
  > "The self-calibration has 5 steps with the different accumulating period to obtain the solution from 10 minutes for the first step to 2 seconds for the last step." (2 Observations)

### Imaging

- task: _not stated_
- deconvolver: CLEAN with Clark algorithm  
  > "The CLEAN deconvolution method is used for the image synthesis with the Clark algorithm and Briggs weighting scheme on CASA 5.4.0" (2 Observations)
- weighting robust: Briggs weighting (robust not stated)  
  > "Clark algorithm and Briggs weighting scheme on CASA 5.4.0" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: not combined with single-dish full-sun images  
  > "we did not combine the synthesized images and full-sun images because it is not established how to deal with the solar limb in the full-sun image for the combining." (2 Observations)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Standard solar ALMA calibration  
  > "after the standard calibration described in (cite: 2017SoPh..292...87S)" (2 Observations) [from (cite: 2017SoPh..292...87S)]
- Noise level ~2.6 K  
  > "$\sim$2.6 K (Shimojo et al. 2017b)" (3 The spicules observed with ALMA, IRIS, and AIA/SDO) [from Shimojo et al. 2017b]

### Not stated but needed to reproduce (our reading)

- Briggs robust value, cell size, image size, clean iterations
- Pre-event reference time for background subtraction
- Details of the free-free opacity formula and constants used
- Number of antennas and array configuration
- Which sources were used as calibrators

## Analysis recipe

1. **Image synthesis and self-calibration**: Per-2 s images with CLEAN after phase-only self-calibration; jitter removed by shifting images using auto-correlation offsets  
  > "To remove jitter motion caused by the remaining phase error, we spatially shift the images based on the offsets estimated by the auto-correlation of the images." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Brightness temperature enhancement of spicule**: Subtract pre-event brightness from event brightness pixel by pixel; correct by filling factor 0.25 (assumed width 0.5'' vs apparent 2'')  
  > "Thus, we use 960 K (= 240 K/0.25) as the brightness temperature of the 100GHz spicule." (3 The spicules observed with ALMA, IRIS, and AIA/SDO)
   - assumption: spicule width 0.5''  
  > "we assume that the width of the 100GHz spicule is 0$''$.5" (3 The spicules observed with ALMA, IRIS, and AIA/SDO)
   - fitting: _not stated_
   - validation: _not stated_
3. **Optical depth vs temperature, observed and modeled**: Observed tau = -ln(1-Tb/T); model free-free optical depth for assumed T and density with 0.5'' line-of-sight depth; intersection gives T and n  
  > "The black line estimates from the observations and the colored line of the model cross when we assume the kinetic temperature of the plasma and the number density of ionized hydrogens" (3 The spicules observed with ALMA, IRIS, and AIA/SDO)
   - assumption: negligible background, T<10,000 K, thermal LTE electron-proton free-free emission  
  > "2) the temperature range of the 100GHz spicule is lower than 10,000K, 3) the emission from the spicule is the thermal free-free emission" (3 The spicules observed with ALMA, IRIS, and AIA/SDO)
   - fitting: _not stated_
   - validation: Consistency with 193 A absorption and Rutten (2017) temperature range  
  > "The temperature range is consistent with the temperature derived above, and thus, justifies our estimation." (3 The spicules observed with ALMA, IRIS, and AIA/SDO)

## Software

- **CASA** 5.4.0: CLEAN image synthesis and self-calibration  
  > "Clark algorithm and Briggs weighting scheme on CASA 5.4.0" (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Peak brightness temperature enhancement | 240 | not stated | K | 2 | the peak enhancement of the brightness temperature caused by the spicule is about 240 K. |
| Kinetic temperature | ~6800 | not stated | K | 3 | the kinetic temperature of the plasma and the number density of ionized hydrogens in the 100GHz spicule are $\sim$6800 K |
| Ionized hydrogen number density | 2.2e10 | not stated | cm^-3 | 3 | $\rm 2.2\times10^{10} \ cm^{-3}$ |
| Rising velocity of 100GHz spicule | ~40 | not stated | km/s | 0 | The rising velocity of the spicule seen in the 100GHz and 193Å images is about 40 km $\rm s^{-1}$ |
| Maximum height of 100GHz spicule | ~15'' (~11,000 km) | not stated | arcsec | 0 | The 100GHz spicule reached the maximum height of $\sim$15$''$ ($\sim$11,000 km) |

## Qualitative findings

- 100GHz spicule is a macrospicule without a hot sheath  
  > "These results suggest that the 100GHz spicule presented in this paper is classified to a macrospicule without a hot sheath in former terminology." (abstract)

## Claim tuples

- H: Are the 100GHz spicule and the MgII/304A spicule physically related? | E: Compared ALMA, IRIS and AIA images and velocities over time | R: Overlap only early; different velocities (~40 vs ~70 km/s); no counterpart afterward | F: They are individual events with no physical relationship | **supported**
- H: What are the temperature and density of the 100GHz spicule? | E: Compared observed and modeled free-free optical depth | R: T ~6800 K, n ~2.2e10 cm^-3 | F: Values consistent with the 193 A absorbing structure | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Millimeter emission satisfies LTE, making parameters easier to derive than from chromospheric lines  
  > "Since the millimeter waves emitted from the chromospheric plasma satisfies the LTE condition, it is relatively easier than other chromospheric lines to derive the physical parameters." (Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Width comparable to beam, so the actual width may be narrower  
  > "the actual width can be narrower than the value because the width is comparable to the size of the synthesized beam." (3 The spicules observed with ALMA, IRIS, and AIA/SDO)
- Limitation (authors): Only relative brightness temperatures because single-dish data not combined  
  > "in this study, we only deal with relative brightness temperatures." (2 Observations)
- Caveat (inferred, ours): Filling factor rests on an assumed 0.5'' width not measured
- Caveat (inferred, ours): Single event; no uncertainties on T and n
- Caveat (inferred, ours): Background subtraction affected by limb artifacts from sparse uv coverage

## Reproducibility

- Data public (paper): ALMA project cited in acknowledgments; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA #2016.1.00070.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Exact optical depth formula and chosen pre-event frame
- Missing: Spicule extraction region
- Data volume (inferred): Large: ~2 h of 2 s solar interferometric cadence, likely hundreds of GB
- Score (inferred): 3/5, Data public and method simple, but key imaging and model details are missing.
- Rediscovery candidate: no, Solar imaging reduction is demanding and details are underspecified; results come from a single hand-picked event.

## Links

- Method: (cite: 2017SoPh..292...87S) (Standard solar ALMA calibration and noise)
- Companion: (cite: 2018ApJ...863...96Y) (Spicules in ALMA data and emission model)

## Checks

```json
{
 "quotes": 39,
 "quotes_ok": 39,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 63,
  "stated": 30,
  "rate": 0.476
 },
 "evidence_ok": true
}
```

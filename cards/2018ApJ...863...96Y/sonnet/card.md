# ALMA Observations of the Solar Chromosphere on the Polar Limb

`2018ApJ...863...96Y` | The Astrophysical Journal 2018 | first author: Yokoyama, Takaaki | arXiv: 1807.01411 | DOI: 10.3847/1538-4357/aad27e

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: sun
- Question: What dynamic structures (jets, blobs) does the solar polar-limb chromosphere show at 100 GHz in ALMA, and how do they correspond to IRIS and AIA features?  
  > "By comparing with ultraviolet data obtained by the Interface Region Imaging Spectrograph (IRIS), we found a correspondence in the dynamic features in the ALMA data with IRIS spicules." (Introduction)
- Target **Solar south polar limb**: coordinates solar south pole  
  > "The target region was the solar south pole." (Observations); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00201.S
- bands: Band 3 (100 GHz)  
  > "ALMA obtained Band-3 data in this time period within the 100 GHz frequency range." (Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: synthesized beam 2.56'' (E-W) x 1.60'' (N-S)  
  > "The major and minor axes of the synthesized beam are 2.56$''$ (1.86 Mm on the Sun) in the east-west direction and 1.60$''$ (1.16 Mm) in the north-south direction, respectively." (Observations)
- max recoverable scale: _not stated_
- sensitivity: noise 13.2 K  
  > "The measured level of the noise is 13.2 K (Figure [4](#fig:noise))." (Discussion)
- time on source: _not stated_
- observing dates: ~1 h around 14:30 UT on 2017 April 29  
  > "The observations were performed in $\approx$ 1 h around 14:30 UT on 2017 April 29." (Observations)
- pi or archival as stated: _not stated_
- Other facility **IRIS**: Si IV and Mg II slit-jaw images, 19 s cadence, 0.33-0.40'' resolution  
  > "IRIS obtained slit-jaw images (SJIs) of Si IV and Mg II lines with a cadence and a spatial resolution of 19 s and $0.33$$''$­-$0.40$$''$ (240 – 290 km on the Sun), respectively." (Observations)
- Other facility **SDO/AIA**: context filtergrams, 12 s cadence  
  > "provided context filtergrams of multiple wavelengths with a cadence of 12 s." (Observations)
- External data: Solar disk brightness temperature of 7000 K used for absolute scale  
  > "we assume that the brightness of the solar disk is 7000 K ((cite: avrett2008ApJS..175..229A))." (Observations) [from (cite: avrett2008ApJS..175..229A)]

## Processing

### Calibration

- pipeline or manual: nominal solar-observation calibration of Shimojo et al. 2017b plus two-step phase self-calibration  
  > "The ALMA data is calibrated with the nominal processes developed for solar observations in (cite: shimojo2017SoPh..292...87S)." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: two-step phase self-cal: model from whole-period image, then 20-s images as models per slot  
  > "In the second step, we repeated the same procedure but synthesized images every 20 s and used each of them with a 20-s cadence as a calibration model for each data slot." (Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: images synthesized with 20 s integration  
  > "we synthesize each image with an integration time of 20 s" (Observations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Solar ALMA calibration and limb-artifact treatment  
  > "The ALMA data is calibrated with the nominal processes developed for solar observations in (cite: shimojo2017SoPh..292...87S)." (Observations) [from Shimojo et al. 2017b (cite: shimojo2017SoPh..292...87S)]
- Noise estimate from XX and YY correlations  
  > "the remaining signals can be regarded as noises ((cite: shimojo2017SoPh..292...87S))." (Discussion) [from (cite: shimojo2017SoPh..292...87S)]

### Not stated but needed to reproduce (our reading)

- CASA version and imaging task/parameters (weighting, cell, size, deconvolution)
- Self-calibration solution intervals and software
- Array configuration and baselines
- Number of antennas and spectral window setup
- IRIS/AIA data processing and alignment with ALMA
- Method for measuring jet length and blob proper motion

## Analysis recipe

1. **Calibrate and self-calibrate, make 20 s images**: Solar nominal calibration, two-step phase self-cal, 20 s synthesized images; scale set by 7000 K disk  
  > "we synthesize each image with an integration time of 20 s after performing a following two-step self-calibration for the antenna’s phases." (Observations)
   - assumption: disk brightness 7000 K  
  > "we assume that the brightness of the solar disk is 7000 K ((cite: avrett2008ApJS..175..229A))." (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Relative brightness movie and comparison with IRIS/AIA**: Relative brightness normalized by time-averaged Tb; compare limbs and jets with AIA 171 and IRIS Mg II  
  > "is a temporally averaged brightness over the entire observed period ($\Delta t \approx 1 \ \mathrm{h}$)." (Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Estimate electron density of blob**: Thermal free-free optical depth with Gaunt factor, tau ≈ Tb/T, EM≈n^2 L  
  > "assuming a small optical thickness, 100% filling factor, and $L \approx 1.5\ensuremath{''}$ approximated with the width of the observed blob, and $\tau \approx T_b/T$" (Discussion)
   - parameter: T = 1e4–4e5 K; Tb=135 K; L≈1.5''  
  > "we obtain $n=(4.6-8.4) \times 10^{9}\ \mathrm{cm}^{-3}$ in the range of $T=(10^4- 4\times 10^5)\ \mathrm{K}$." (Discussion)
   - assumption: 100% filling factor, small optical thickness  
  > "assuming a small optical thickness, 100% filling factor" (Discussion)
   - fitting: _not stated_
   - validation: Compared with spicule densities from IRIS spectra (Alissandrakis 2018): about an order of magnitude lower  
  > "This number is a factor of one order of magnitude smaller than those for spicules obtained through the analysis of the IRIS spectrum data" (Discussion)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Noise level at 100 GHz | 13.2 | not stated | K | 0 | The measured level of the noise is 13.2 K |
| Blob brightness enhancement | 135 | not stated | K | 2 | The brightness enhancement in ALMA images is by 135 K beyond the background |
| Blob proper motion speed | 40 | not stated | km/s | 2 | The blob shows a systematic proper motion at a speed of 40 km/s |
| ALMA jet elongation speed | 30–40 | not stated | km/s | 2 | The speed of the elongation is 30–40 $\mathrm{km}\ \mathrm{s}^{-1}$. |
| Blob electron density | (4.6-8.4)e9 | not stated | cm^-3 | 3 | we obtain $n=(4.6-8.4) \times 10^{9}\ \mathrm{cm}^{-3}$ |

## Qualitative findings

- ALMA 100 GHz limb shows saw-tooth patterns matching the AIA 171 limb; ALMA limb ~5'' above IRIS Mg II limb  
  > "The IRIS Mg II limb (panel d) is $\approx$ 5$''$ below the ALMA limb." (Results)

## Claim tuples

- H: Do ALMA 100 GHz data show jet-like activity at the limb corresponding to IRIS spicules? | E: Compare ALMA relative-brightness movie with IRIS Mg II SJIs | R: Thorn-like structures ≥8'' long match IRIS jet clusters | F: ALMA detects jet-like activity associated with spicules | **supported**
- H: Can a blob ejection be traced and characterized? | E: Track blob in ALMA and IRIS images; estimate density from free-free emission | R: 135 K enhancement, 40 km/s, n=(4.6-8.4)e9 cm^-3 | F: Blob trajectory follows spicular patterns; density estimate likely biased by resolution/filling factor | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Absolute brightness temperature is hard to determine; S/N poor beyond 10'' off limb; resolution comparable to blob size  
  > "it is still difficult to determine the absolute brightness temperature in the ALMA data" (Observations)
- Limitation (authors): Could not confirm jet generation models  
  > "Using the available data in the present observations, we could not confirm the proposed model." (Discussion)
- Caveat (inferred, ours): Self-calibration on 20 s models may bias structures
- Caveat (inferred, ours): Density estimate depends on assumed T range and filling factor
- Caveat (inferred, ours): No uncertainties on speeds or lengths

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters and CASA version
- Missing: Self-cal details
- Missing: IRIS/AIA co-alignment
- Missing: Measurement procedures for jets and blob
- Data volume (inferred): tens to hundreds of GB for solar time-series ALMA data
- Score (inferred): 2/5, Few processing details; qualitative results mostly, heavily reliant on Shimojo et al. 2017b.
- Rediscovery candidate: no, Recipe incomplete and results largely qualitative.

## Links

- Method: Shimojo et al. 2017b (cite: shimojo2017SoPh..292...87S) (Solar ALMA calibration, limb artifacts and noise estimation)
- Companion: Alissandrakis et al. 2018 (cite: alissandrakis2018SoPh..293...20A) (IRIS limb and spicule density analysis)
- Related: IRIS
- Related: SDO/AIA

## Checks

```json
{
 "quotes": 33,
 "quotes_ok": 33,
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
  "stated": 24,
  "rate": 0.381
 },
 "evidence_ok": true
}
```

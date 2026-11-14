# The Extraordinary Outburst in the Massive Protostellar System NGC 6334 I-MM1: Spatiokinematics of Water Masers during a Contemporaneous Flare Event

`2021ApJ...908..175C` | The Astrophysical Journal 2021 | first author: Chibueze, James O. | arXiv: 2101.11913 | DOI: 10.3847/1538-4357/abd474

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, milky_way_ism
- Question: What are the relative proper motions of 22 GHz H2O masers in NGC 6334I during the first year after the MM1 accretion burst, and what do they say about jets and outflows?  
  > "We derive the relative proper motion measurements for these H$_2$O masers in order to probe the kinematics of the gas surrounding MM1 and MM3-UCHII in this region of active star formation." (Introduction)
- Target **NGC 6334I (MM1, MM3-UCHII, CM2)**: coordinates phase center (17h20m53.377s, -35d46m55.808s) J2000  
  > "NGC 6334 I, located at a parallax distance of $1.30 \pm 0.09$ kpc" (Introduction); "The position of the phase tracking center of the NGC 6334I was ($\alpha,\delta$)=(17$^h$20$^m$53$^s$.377, -35$^o$46$'$55$''$.808) in the J2000.0 epoch." (Observations and data reduction); z/distance 1.30 ± 0.09 kpc  
  > "NGC 6334 I, located at a parallax distance of $1.30 \pm 0.09$ kpc" (Introduction); "The position of the phase tracking center of the NGC 6334I was ($\alpha,\delta$)=(17$^h$20$^m$53$^s$.377, -35$^o$46$'$55$''$.808) in the J2000.0 epoch." (Observations and data reduction); distance from parallax (Chibueze 2014; Reid 2014; Wu 2014)  
  > "NGC 6334 I, located at a parallax distance of $1.30 \pm 0.09$ kpc" (Introduction); "The position of the phase tracking center of the NGC 6334I was ($\alpha,\delta$)=(17$^h$20$^m$53$^s$.377, -35$^o$46$'$55$''$.808) in the J2000.0 epoch." (Observations and data reduction)

## Data provenance

- ALMA projects: 2015.A.00022.T
- bands: _not stated_
- frequencies and spectral setup: KaVA: 256 MHz total (16 MHz x 16 IFs), one 16 MHz IF analyzed, 15.625 kHz (~0.21 km/s) resolution; HartRAO: 8 MHz band, 1024 channels  
  > "The spectral resolution is 15.625 kHz ($\sim$0.21  km s$^{-1}$) for the H$_2$O maser line." (2.2 KaVA observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Synthesized beams ~2.5-2.8 mas x ~1.0 mas  
  > "2.48 mas $\times$ 0.97 mas (position angle, PA=-0.38$^\circ$)" (2.2 KaVA observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: KaVA: 21 Nov 2015, 15 Dec 2015, 4 Jan 2016; HartRAO 7 May 2013 to 2 Dec 2020  
  > "3 epochs taken on 21 November 2015 (2015.89), 15 December 2015 (2015.95) and 4 January 2016 (2016.01), respectively." (2.2 KaVA observations)
- pi or archival as stated: _not stated_
- Line: H2O 6_16-5_23 (22.235120 GHz)
- Other facility **KaVA (KVN+VERA)**: Three-epoch VLBI of 22 GHz H2O masers for proper motions  
  > "we present multi-epoch VLBI measurements of the 22 GHz H$_2$O maser emission using a combination of Korean VLBI Network (KVN) and VLBI Exploration of Radio Astronomy (VERA)" (Introduction)
- Other facility **HartRAO 26 m**: Single-dish H2O maser monitoring  
  > "The ongoing 22.2 GHz (1.3 cm) water maser observations reported here were made using the 26m telescope of Hartebeesthoek Radio Astronomy Observatory (HartRAO)." (2.1 Single-dish monitoring observations)
- Other facility **VLA**: H2O maser map used for absolute positions; 5 cm continuum  
  > "compared to the closest epoch of the Very Large Array (VLA) H$_2$O maser map to obtain the absolute positions of the maser spots/features" (2.2 KaVA observations)
- External data: ALMA 1.3 mm dust continuum image (epoch 2016.6) used as overlay background  
  > "ALMA 1.3 mm dust continuum from a comparable epoch (2016.6, grey scale from (cite: 2017ApJ...837L..29H))" (3.2 Proper motions of the H$_2$O masers) [from (cite: 2017ApJ...837L..29H)]
- External data: VLA 5 cm image contours and VLA H2O maser detections  
  > "the VLA 5 cm image (white contours from (cite: 2018ApJ...854..170H))" (3.2 Proper motions of the H$_2$O masers) [from (cite: 2018ApJ...854..170H); (cite: 2018ApJ...866...87B)]

## Processing

### Calibration

- pipeline or manual: AIPS: APCAL amplitude, FRING delays with NRAO530, bandpass with NRAO530  
  > "Next, delays and phase offsets were removed by running AIPS task FRING using NRAO530." (2.2 KaVA observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: AIPS IMAGR for imaging and CLEAN; SAD for Gaussian fitting  
  > "Imaging and CLEAN (deconvolution) were performed using the AIPS task IMAGR." (2.2 KaVA observations)
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
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Maser group nomenclature  
  > "divided into groups according to the nomenclature used by (cite: 2018ApJ...866...87B)" (3.2 Proper motions of the H$_2$O masers) [from (cite: 2018ApJ...866...87B)]
- PVCM/VVCM method  
  > "as described by (cite: 1993ApJ...406L..75B; 2000ApJ...533..893B) and (cite: 2012ApJ...748..146C)" (4.1 VVCM analysis) [from Bloemhof 1993, 2000; Chibueze 2012]

### Not stated but needed to reproduce (our reading)

- KaVA project code and phase/bandpass calibrator details (text truncated)
- How maser features were matched between epochs and the fitting thresholds
- Epoch separation and conversion to km/s at 1.30 kpc for the 3D velocities
- Monte-Carlo procedure details for position-angle errors
- How the ALMA project data were actually used

## Analysis recipe

1. **Calibrate KaVA data and image maser spots**: AIPS calibration, IMAGR/CLEAN, SAD Gaussian fits for spot positions  
  > "The SAD task was employed for the Gaussian fitting for extraction of the peak intensities and offset positions of the maser spots." (2.2 KaVA observations)
   - software: AIPS
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive relative proper motions**: Displacement of maser features between adjacent epochs, averaged for 3-epoch features, relative to a reference maser spot in UCHII-W1  
  > "For features detected in all three epochs, the average of the proper motion between epochs 1 & 2, and epochs 2 & 3 were taken." (2.2 KaVA observations)
   - software: AIPS
   - assumption: Reference maser motion contributes <10% uncertainty  
  > "The overall uncertainty in our derived relative proper motions due to the motion of the reference maser spot is $<$ 10%." (2.2 KaVA observations)
   - fitting: _not stated_
   - validation: Compared with HartRAO single-dish spectra and VLA results  
  > "This mean proper motion is in agreement with the previous results from VLA multi-epoch observations." (abstract)
3. **Characterize outflow axis via variance-covariance matrices**: PVCM and VVCM diagonalization; major axis from largest eigenvector  
  > "The major axis is defined by the eigenvector corresponding to the largest eigenvalue." (4.1 VVCM analysis)
   - assumption: Bow shock in CM2 symmetric for inclination  
  > "Assuming the bow shock in CM2 is symmetric, the inferred inclination angle" (4.1 VVCM analysis)
   - fitting: Monte-Carlo error of velocity vectors for PA  
  > "The error in the position angle was calculated using a Monte-Carlo error of the velocity vectors." (4.1 VVCM analysis)
   - validation: Tested including/excluding UCHII-W1  
  > "including UCHII-W1 into the calculation makes only a marginal difference in the results" (4.1 VVCM analysis)

## Software

- **AIPS** : KaVA calibration (APCAL, FRING), imaging (IMAGR), Gaussian fitting (SAD)  
  > "The data calibration was carried out using the Astronomical Image Processing System (AIPS)" (2.2 KaVA observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of traced maser proper motions | 186 | not stated | count | 2 | We traced 186 maser proper motions |
| Overall mean 3D maser velocity | 85 | not stated | km/s | 2 | The overall mean of the 3D velocities of the masers is 85 km s$^{-1}$. |
| VVCM major-axis position angle | -79.4 | 9.2 | deg | 3 | -79.4 $\pm$ 9.2 |
| Inclination of outflow (matrix 2) | -6.0 | 0.6 | deg | 3 | $\phi_\text{max} = -6.0^\circ \pm 0.6^\circ$ |
| CM2-W2 average velocity | 112 | not stated | km/s | 2 | with an average velocity of 112 km s$^{-1}$ |

## Qualitative findings

- Proper motions of CM2-W2, MM1-W1, MM1-W3 and UCHII-W3 are mostly driven by the MM1B radio jet; UCHII-W1 is likely driven by MM3-UCHII.  
  > "Our results suggested that the motion of the UCHII-W1 H$_2$O maser group is largely driven by the expansion of MM3-UCHII ." (Conclusions and summary)

## Claim tuples

- H: H2O maser proper motions after the burst trace jet-driven shocks | E: 3-epoch KaVA proper motions plus VVCM analysis | R: Mean 85 km/s; major axis PA -79.4 deg through MM1B cavity | F: Masers in CM2-W2 and others trace the MM1B jet | **supported**
- H: UCHII-W1 motions are driven by the MM1B jet | E: Compared proper motion direction with jet axis | R: UCHII-W1 moves northward, against the jet direction | F: Driven by MM3-UCHII rather than MM1B | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: OH maser magnetic field reversal as cause of UCHII-W1 northward motion, rejected as too distant  
  > "therefore may not be responsible for the observed northward proper motions of UCHII-W1 masers" (4.3 Impact of MM3-UCHII on UCHII-W1 maser spatio-kinematics)
- How they decided it was enough: _not stated_
- Limitation (authors): Complex maser distributions in MM1-W1 and UCHII-W1 may affect proper motions  
  > "this complexity may have affected, in small measures, the derived proper motions" (2.2 KaVA observations)
- Caveat (inferred, ours): Only three epochs spanning about 2 months
- Caveat (inferred, ours): Relative proper motions depend on a reference maser that itself moves
- Caveat (inferred, ours): ALMA data role unclear; only used as background image

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: KaVA data access and project code
- Missing: Feature identification criteria
- Missing: ALMA data use details
- Data volume (inferred): KaVA VLBI visibilities; ALMA minimal (<10 GB)
- Score (inferred): 2/5, ALMA is not analysed; VLBI recipe is only partly specified.
- Rediscovery candidate: no, Main data are KaVA VLBI, not clearly public, and the recipe is incomplete.

## Links

- Method: (cite: 1993ApJ...406L..75B) (Variance-covariance matrix method)
- Companion: (cite: 2018ApJ...866...87B) (Earlier VLA water maser proper motions and ALMA CS(6-5))
- Companion: (cite: 2017ApJ...837L..29H) (ALMA detection of MM1 outburst)

## Checks

```json
{
 "quotes": 42,
 "quotes_ok": 42,
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
  "facts": 65,
  "stated": 28,
  "rate": 0.431
 },
 "evidence_ok": true
}
```

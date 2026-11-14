# ALMA observations of the kinematics and chemistry of disc formation

`2014A&A...566A..74L` | Astronomy and Astrophysics 2014 | first author: Lindberg, Johan E. | arXiv: 1405.1416 | DOI: 10.1051/0004-6361/201322651

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: Is there a Keplerian disc around the Class 0/I protostar IRS7B in the R CrA cloud, and how does the disc relate to the presence of complex organic molecules in the inner envelope?  
  > "We aim to better understand the structure of the inner regions of these protostars and, in particular, the interplay between the chemistry and the presence of discs." (abstract)
- Target **R CrA IRS7B (plus CXO 34, IRS7A, SMM 1C)**: coordinates IRS7B 19:01:56.42 -36:57:28.4 (J2000)  
  > "in the R CrA cloud (NGC 6729) within the Corona Australis star-forming region, one of the nearest star-forming regions, at a distance of 130 pc (cite: neuhauser08)." (Introduction); "| IRS7B | 19:01:56.42 | $-$36:57:28.4 |" (Table 2); z/distance 130 pc  
  > "in the R CrA cloud (NGC 6729) within the Corona Australis star-forming region, one of the nearest star-forming regions, at a distance of 130 pc (cite: neuhauser08)." (Introduction); "| IRS7B | 19:01:56.42 | $-$36:57:28.4 |" (Table 2); distance from Neuhäuser & Forbrich 2008  
  > "in the R CrA cloud (NGC 6729) within the Corona Australis star-forming region, one of the nearest star-forming regions, at a distance of 130 pc (cite: neuhauser08)." (Introduction); "| IRS7B | 19:01:56.42 | $-$36:57:28.4 |" (Table 2)

## Data provenance

- ALMA projects: 2011.0.00628.S
- bands: Band 7  
  > "R CrA IRS7B was observed on 4, 6, and 9 May 2012 in ALMA band 7 as part of ALMA Cycle 0 observations." (Observations)
- frequencies and spectral setup: 4 spectral windows, 336.955–349.814 GHz, 3840 channels each, 122 kHz (~0.11 km/s) channels  
  > "The observations were performed in four spectral windows simultaneously (see Table [1](#tab:spw) for details), each with 3840 channels with channel widths of 122 kHz ($\sim0.11$ km s$^{-1}$)." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 30–380 m (34–430 kλ), 18 antennas  
  > "18 antennas were part of the array, positioned in an extended configuration with baselines of 30–380 m (34–$430~\mathrm{k}\lambda$)." (Observations)
- angular resolution: 0.42"x0.37" (PA ~72 deg)  
  > "This resulted in a synthesised beam size of approximately $0.42\ensuremath{''}\times0.37\ensuremath{''}$ ($\mathrm{P.A.} \approx 72\ensuremath{^\circ}$)." (Observations)
- max recoverable scale: _not stated_
- sensitivity: 9–10 mJy/beam/channel rms in line-free channels  
  > "The typical rms in line-free channels is 9–10 mJy beam$^{-1}$ channel$^{-1}$." (Observations)
- time on source: 5.5 hours total integration  
  > "The total integration time of the observations was 5.5 hours." (Observations)
- observing dates: 4, 6, and 9 May 2012  
  > "R CrA IRS7B was observed on 4, 6, and 9 May 2012 in ALMA band 7" (Observations)
- pi or archival as stated: _not stated_
- Line: C17O J=3-2 (337.06112 GHz)
- Line: CH3OH 7_0-6_0, A+ (and other 7_k-6_k lines) (338.40868 GHz)
- Line: H13CO+ J=4-3 (346.99834 GHz)
- Line: C34S J=7-6 (337.39646 GHz)
- Other facility **ASTE**: Single-dish CH3OH comparison flux  
  > "Single-dish observations of the region performed with the ASTE telescope show very strong CH$_3$OH emission (cite: watanabe12)" (Results)
- External data: Envelope model (r^-1.5 density, 2.2 Msun mass) adopted for CH3OH modelling  
  > "The envelope model of (cite: lindberg12) was adopted." (CH3OH modelling) [from (cite: lindberg12)]
- External data: CH3OH collision rates from LAMDA  
  > "CH$_3$OH collision rates from the LAMDA database were used (cite: lamda; rabli10)." (CH3OH modelling) [from (cite: lamda; rabli10)]
- External data: Bolometric temperature 89 K and Lbol/Lsmm 48 for IRS7B  
  > "The bolometric temperature is 89 K, and the bolometric/submillimetre luminosity ratio is 48" (Introduction) [from (cite: lindberg13)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune and Titan; gain and bandpass quasar J1924-292  
  > "The quasar flux was calibrated with observations of Neptune and Titan." (Observations)
- flux scale uncertainty: _not stated_
- self calibration: Continuum data self-calibrated  
  > "The continuum data were self-calibrated to reduce side-lobes and increase the signal-to-noise ratio." (Observations)

### Imaging

- task: _not stated_
- deconvolver: Högbom PSFs in minor cycles  
  > "The spectral line data were cleaned using Högbom PSFs in the minor cycles" (Observations)
- weighting robust: Briggs, robustness 0.5  
  > "Briggs weighting with a robustness parameter of 0.5" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: Line-free channels used for continuum  
  > "The line-free channels were used to record the continuum emission." (Observations)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.42"x0.37", PA ~72 deg  
  > "synthesised beam size of approximately $0.42\ensuremath{''}\times0.37\ensuremath{''}$" (Observations)
- final rms: _not stated_

### Inherited from earlier work

- Disc mass from continuum using optically thin method, T_dust=30 K  
  > "using the method of (cite: jorgensen07) assuming optically thin emission and a dust temperature of 30 K" (4.1) [from (cite: jorgensen07)]
- Position-velocity construction via weighted least-squares fit of velocity gradient  
  > "By the method of (cite: goodman93), which uses a weighted least-square fit to the positional data" (4.1) [from (cite: goodman93)]
- Envelope model for CH3OH RATRAN modelling  
  > "The envelope model of (cite: lindberg12) was adopted." (CH3OH modelling) [from (cite: lindberg12)]

### Not stated but needed to reproduce (our reading)

- Which spw/channels were line-free for continuum and the continuum bandwidth
- Self-calibration solution intervals and number of iterations
- CASA version and calibration pipeline/manual details
- Cell size, image size, masks and clean thresholds
- Dust opacity and gas-to-dust ratio used for disc mass
- Details of the LIME model (grid, abundance, inclination handling, fitting procedure)
- Fitting details/uncertainties for Keplerian parameters
- Abundance and temperature structure details of RATRAN models

## Analysis recipe

1. **Continuum point-source fluxes and disc masses**: Fit point sources in continuum; disc mass from optically thin dust emission  
  > "we can estimate the mass of the disc around IRS7B from the ALMA continuum emission using the method of (cite: jorgensen07) assuming optically thin emission and a dust temperature of 30 K" (4.1)
   - assumption: Optically thin, T_dust = 30 K, distance 130 pc  
  > "assuming optically thin emission and a dust temperature of 30 K" (4.1)
   - fitting: _not stated_
   - validation: _not stated_
2. **Build C17O PV diagram**: Fit strongest peak per channel in uv data, derive PA and PV diagram  
  > "Through the CASA task `uvmodelfit` we identify the strongest peak of the C$^{17}$O emission in each channel of the $(u,\varv)$ data." (4.1)
   - software: CASA uvmodelfit
   - parameter: PA -65 deg, centre LSR velocity 6.2 km/s  
  > "We find that the motion has a position angle of $-65$$^\circ$ on the sky and is centred around the channel corresponding to an LSR velocity of 6.2 km s$^{-1}$." (4.1)
   - fitting: Weighted least-squares fit of positions  
  > "By the method of (cite: goodman93), which uses a weighted least-square fit to the positional data to establish the inclination of the velocity gradient on the plane of sky" (Analysis, A Keplerian disc around IRS7B)
   - validation: _not stated_
3. **Fit Keplerian disc with finite radius vs infall**: Fit Keplerian profile plus linear branch; compare chi2 with v~r^-1 infall; compare against LIME fiducial disc  
  > "by fitting a Keplerian profile (blue curve) and a straight line (green curve) to the data we can determine the disc radius very accurately." (4.1)
   - software: LIME
   - parameter: free parameters: central mass and disc radius  
  > "The central mass and the disc radius are the only free parameters." (4.1)
   - assumption: Flat disc, n∝r^-1, T∝r^-0.5, LTE, optically thin, inclination 60 deg  
  > "the disc is assumed to be flat with a radial density profile $n(r) \propto r^{-1}$ and a temperature profile $T(r) \propto r^{-0.5}$." (4.1)
   - fitting: chi2 fit weighted by uvmodelfit errors  
  > "We do a $\chi^2$ fit to the velocities as a function of radius weighted by the `uvmodelfit` errors on the positional fits." (4.1)
   - validation: Keplerian chi2 a factor 2.3 lower than infall  
  > "the Keplerian fit has a $\chi^2$ value a factor 2.3 times lower than the infall fit" (4.1)
4. **Radiative transfer modelling of CH3OH**: RATRAN models with constant or jump abundance, power-law or flat inner density, compared to observed spectrum  
  > "The CH$_3$OH emission in a $1.2\ensuremath{''}\times1.0\ensuremath{''}$ box around IRS7B was modelled using the radiative transfer modelling tool RATRAN" (4.2)
   - software: RATRAN
   - parameter: r_100K ≈ 30 AU; centrifugal radius 100 AU assumed  
  > "$r_{100~\mathrm{K}} \approx 30$ AU, inside which $T>100$ K" (4.2)
   - assumption: Envelope mass 2.2 Msun, r^-1.5 density  
  > "the density profile follows an $r^{-1.5}$ power law with a mass of $2.2~M_{\odot}$." (4.2)
   - fitting: _not stated_
   - validation: Level populations checked for continuity  
  > "the level populations as function of radius were found to be continuous and well-behaved" (4.2)

## Software

- **CASA** : uvmodelfit and imaging  
  > "Through the CASA task `uvmodelfit`" (4.1)
- **LIME** : Fiducial Keplerian disc C17O model  
  > "calculated under the assumption of LTE using the LIME code (cite: brinch10)" (4.1)
- **RATRAN** : CH3OH radiative transfer modelling  
  > "radiative transfer modelling tool RATRAN (cite: ratran)" (4.2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| IRS7B disc radius | 50 | not stated | AU | 3 | We find the radius of the spatially well-constrained disc to be 0.41$''$ which equals to 50 AU |
| Central mass of IRS7B | 2.3 | not stated | Msun | 3 | corresponds to a central mass of $M_{\star}=2.3~M_{\odot}$ assuming the most probable inclination of $60\ensuremath{^\circ}$. |
| IRS7B continuum flux | 432 | 1 | mJy | 1 | / IRS7B / 19:01:56.42 / $-$36:57:28.4 / $432\pm\phantom{0}1$ / 0.024 / |
| IRS7B disc mass | 0.024 | not stated | Msun | 1 | which corresponds to a disc mass of $0.024~M_{\odot}$ |
| SMM 1C continuum flux | 233 | 50 | mJy | 1 | / SMM 1C / 19:01:55.31 / $-$36:57:17.0 / $233\pm50$ / 0.013 / |

## Qualitative findings

- CH3OH outflow emission orthogonal to the C17O disc axis; most CH3OH flux resolved out  
  > "roughly perpendicular to the C$^{17}$O disc emission." (Conclusions)

## Claim tuples

- H: C17O around IRS7B traces a Keplerian disc | E: PV diagram from uvmodelfit peak positions, Keplerian vs infall fits | R: Keplerian with edge at 50 AU, M*=2.3 Msun; chi2 2.3 times lower than infall | F: Keplerian disc favoured; infall not excluded | **supported**
- H: A growing disc quenches complex organic chemistry in the inner envelope | E: RATRAN CH3OH models with flat vs power-law inner density | R: Flat inner density with abundance 1e-8 reproduces faint emission | F: Disc dominates small-scale chemistry | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Infall with angular momentum conservation considered, deemed unlikely due to sharp disc edge  
  > "seems unlikely due to the well-defined edge of the disc which is observed." (Conclusions)
- How they decided it was enough: _not stated_
- Limitation (authors): Higher sensitivity and resolution needed to verify the Keplerian disc  
  > "To verify that the C$^{17}$O emission on IRS7B originates in a Keplerian disc, higher-sensitivity and higher-resolution observations are needed." (Conclusions)
- Caveat (inferred, ours): Fit uncertainties not given; inclination of 60 deg assumed
- Caveat (inferred, ours): CH3OH model comparison qualitative
- Caveat (inferred, ours): Extended emission resolved out, limiting chemistry constraints
- Caveat (inferred, ours): Only one source has kinematics

## Reproducibility

- Data public (paper): Project code given in acknowledgements (Cycle 0 data)  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00628.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version/calibration scripts
- Missing: Imaging parameters beyond robust
- Missing: LIME and RATRAN model setups
- Data volume (inferred): ~20-50 GB (Cycle 0, three execution blocks, 4 spws x 3840 channels)
- Score (inferred): 3/5, Data public and the recipe is simple, but many processing and modelling details are missing and fit uncertainties are not stated.
- Rediscovery candidate: yes, Public Cycle 0 data, with numeric results (disc radius, stellar mass, disc mass) obtainable by a straightforward PV analysis.

## Links

- Method: (cite: goodman93) (PV method for velocity gradient)
- Method: (cite: jorgensen07) (Disc mass from continuum)
- Companion: (cite: lindberg12) (Envelope model and earlier SMA/APEX data)
- Companion: (cite: lindberg13) (Herschel observations of IRS7B)

## Checks

```json
{
 "quotes": 61,
 "quotes_ok": 61,
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
  "facts": 74,
  "stated": 45,
  "rate": 0.608
 },
 "evidence_ok": true
}
```

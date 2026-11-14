# The radio jets of SS 433 at millimetre wavelengths

`2018A&A...619A..40M` | Astronomy and Astrophysics 2018 | first author: Martí, Josep | arXiv: 1809.01386 | DOI: 10.1051/0004-6361/201833733

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, milky_way_ism
- Question: What are the properties (brightness profile, spectral index, magnetic field, age and energy-loss mechanism) of the SS 433 jets at millimetre wavelengths?  
  > "We aim to study the SS 433 jet properties at radio frequencies corresponding to millimetre wavelengths where the synchrotron emitting particles are expected to lose their energy much faster" (abstract)
- Target **SS 433**: coordinates _not stated_; z/distance 5.5 kpc  
  > "we adopt here the canonical distance of 5.5 kpc (cite: 2007MNRAS.381..881L)" (4 Kinematic model); distance from Lockman et al. 2007 (cite: 2007MNRAS.381..881L)  
  > "we adopt here the canonical distance of 5.5 kpc (cite: 2007MNRAS.381..881L)" (4 Kinematic model)

## Data provenance

- ALMA projects: 2013.1.01369.S
- bands: Band 6 (1.24–1.34 mm)  
  > "The instrumental set-up included four spectral windows within ALMA Band 6 centred at frequencies $\nu= 224, 226, 240,$ and 242 GHz." (2 Archival observations with ALMA)
- frequencies and spectral setup: 4 spws, 2 GHz each, 64 channels  
  > "Each spectral window covered a $\Delta \nu =2$ GHz bandwidth split into 64 channels." (2 Archival observations with ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C34-7, 31 antennas  
  > "A total of 31 antennas in the C34-7 configuration were available." (2 Archival observations with ALMA)
- baselines: 42–1574 m (25–1200 kλ)  
  > "This provided baselines between 42 and 1574 m, equivalent to 25 and 1200 k$\lambda$, respectively." (2 Archival observations with ALMA)
- angular resolution: _not stated_
- max recoverable scale: ~4 arcsec  
  > "sensitivity to angular scales as large as $\sim4^{\prime\prime}$" (2 Archival observations with ALMA)
- sensitivity: rms 32 μJy/beam  
  > "the rms noise level in the image (32 $\mu$Jy beam$^{-1}$)" (4 Observed brightness profile)
- time on source: three 1 h scheduling blocks  
  > "Three consecutive scheduling blocks spanning $1^{\rm h}$ each were executed" (2 Archival observations with ALMA)
- observing dates: 2015 Sep 28–29  
  > "starting on 2015 September 28 at $21^h 50^m 06^s$ UTC, and ending on 2015 September 29 at $01^h 40^m 22^s$ UTC" (2 Archival observations with ALMA)
- pi or archival as stated: Archival, PI K. Blundell  
  > "Project Id. ADS/JAO.ALMA#2013.1.01369.S, PI K. Blundell." (Footnote 1)
- Other facility **VLA**: C-band maps from literature compared with ALMA  
  > "we are comparing our ALMA observations with the (cite: 2011ApJ...736..118B) and (cite: 2010ApJ...719.1918R) VLA maps at centimetre wavelengths" (6 Discussion)
- External data: Average jet spectral index alpha=-0.74  
  > "we use the average value $\alpha=-0.74$ for the extended jets taken from (cite: 2011ApJ...736..118B)" (5 Intrinsic brightness profile) [from (cite: 2011ApJ...736..118B)]
- External data: Precession parameters of kinematic model  
  > "updated with the precession parameters derived by (cite: 2001ApJ...561.1027E)" (3 Kinematic model) [from (cite: 2001ApJ...561.1027E)]
- External data: Quiescent flux S=1.23 Jy (nu/GHz)^-0.6  
  > "$S_{\nu} = 1.23~{\rm Jy} (\nu/{\rm GHz})^{-0.6\pm0.02}$ estimated by (cite: 1982ApJ...260..220S)" (6 Discussion) [from (cite: 1982ApJ...260..220S)]

## Processing

### Calibration

- pipeline or manual: ALMA archive calibration scripts run, with extra flagging  
  > "All steps in the python scripts for calibration provided by the ALMA archive were run" (2 Archival observations with ALMA)
- casa version: CASA 5.1.1-5  
  > "Calibration was conducted using the CASA 5.1.1-5 software package." (2 Archival observations with ALMA)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: asteroid Pallas  
  > "The flux density scale was tied to observations of the asteroid Pallas." (2 Archival observations with ALMA)
- flux scale uncertainty: 5–10%  
  > "Its accuracy in Band 6 is believed to be in the 5% – 10% range." (2 Archival observations with ALMA)
- self calibration: phase and amplitude, improved rms by ~2  
  > "Self-calibrating in phase and amplitude still worked in an acceptable way despite the variability issue" (2 Archival observations with ALMA)

### Imaging

- task: CLEAN in CASA and AIPS  
  > "Maps deconvolved with the CLEAN algorithm were computed using both CASA and AIPS, yielding very similar results." (2 Archival observations with ALMA)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The map shown in Fig. 2 was obtained using natural weight" (2 Archival observations with ALMA)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: three MSs concatenated with concat  
  > "The three calibrated measurement sets were finally concatenated into a single set using the CASA task `concat` for imaging." (2 Archival observations with ALMA)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: 32 μJy/beam  
  > "the rms noise level in the image (32 $\mu$Jy beam$^{-1}$)" (4 Observed brightness profile)

### Inherited from earlier work

- Doppler/beam correction prescription  
  > "Here we adapt the prescription developed in (cite: 2010ApJ...719.1918R) and (cite: 2011ApJ...736..118B)" (5 Intrinsic brightness profile) [from (cite: 2010ApJ...719.1918R); (cite: 2011ApJ...736..118B)]
- Uncertainty budget contributions  
  > "The uncertainty associated with it has three different contributions (cite: 2011ApJ...736..118B)" (4 Observed brightness profile) [from (cite: 2011ApJ...736..118B)]
- Kinematic model formalism  
  > "The kinematic model used is based on the (cite: 1981ApJ...246L.141H) formalism" (3 Kinematic model) [from (cite: 1981ApJ...246L.141H)]

### Not stated but needed to reproduce (our reading)

- CLEAN threshold, mask, cell and image size
- Beam size and position angle values
- Self-calibration solution intervals and reference model
- Exact flagging performed
- Pixel/radius settings for the plane fit and the jet-path sampling step
- Precession parameters numeric values
- Lorentz factor/jet speed value used

## Analysis recipe

1. **Calibrate, self-calibrate and image**: Archive CASA calibration scripts, phase and amplitude self-cal, CLEAN with natural weights  
  > "Self-calibrating in phase and amplitude still worked in an acceptable way despite the variability issue" (2 Archival observations with ALMA)
   - software: CASA, AIPS
   - fitting: _not stated_
   - validation: CASA and AIPS maps compared, very similar  
  > "Maps deconvolved with the CLEAN algorithm were computed using both CASA and AIPS, yielding very similar results." (2 Archival observations with ALMA)
2. **Core light curve and spectral index**: DFTPL light curve; maps at ~225 and ~241 GHz  
  > "creating maps at two slightly different frequencies (about 225 and 241 GHz, respectively)" (2 Archival observations with ALMA)
   - software: AIPS
   - fitting: _not stated_
   - validation: _not stated_
3. **Observed brightness profile along kinematic path**: Least-squares plane fit to pixels within ≤2 pixel radius along model path; errors added in quadrature  
  > "we store the pixel values within a small radius (typically $\leq 2$ pixel) and fit a least-squares plane to them." (4 Observed brightness profile)
   - parameter: Jet velocity ±10% for position error  
  > "the jet path position error estimated assuming a $\pm10$% variation in the jet velocity" (4 Observed brightness profile)
   - assumption: Distance 5.5 kpc; precession axis PA 100 deg  
  > "We use the historical value of 100${\rlap.}^{\circ}$0 from the north to the east" (3 Kinematic model)
   - fitting: _not stated_
   - validation: Restricted to features beyond first sidelobe (310 mas)  
  > "this secondary feature in the ALMA point spread function has a 310 milliarcsecond (mas) radius with a response still at the 10% level." (4 Observed brightness profile)
4. **Remove core and correct for Doppler/geometry**: Subtract variable point source or brightest clean components (UVSUB); apply beam-weighted Doppler correction factor C_i  
  > "Second, we removed, also in the Fourier plane, the brightest clean components closer than the first sidelobe of the synthesized beam" (5 Intrinsic brightness profile)
   - software: AIPS
   - parameter: n=2, alpha=-0.74, sum to 500 d  
  > "the summation is extended up to ejection ages of 500 d" (5 Intrinsic brightness profile)
   - assumption: continuous jet flow  
  > "we adopt $n=2$ corresponding to a continuous jet flow" (5 Intrinsic brightness profile)
   - fitting: _not stated_
   - validation: Two core-removal methods give similar results beyond ~40 d  
  > "In both cases the result is very similar for ages older than $\sim 40$ d." (5 Intrinsic brightness profile)
5. **Equipartition B field and loss mechanism**: Equipartition from core size 60x40 mas and 88 mJy; compare synchrotron lifetime and Hjellming & Johnston adiabatic model for t2 prediction  
  > "The resulting equipartition field is then 30 mG." (6 Discussion)
   - assumption: gamma=2.48 from alpha=-0.74; slowed (p=1/2) vs free (p=1) expansion  
  > "The optically thin spectral index is taken as $\alpha=-0.74$ from the same multi-frequency data of (cite: 2011ApJ...736..118B); hence $\gamma=2.48$." (6 Discussion)
   - fitting: _not stated_
   - validation: Compared predicted ages with VLA oldest ejecta (500 d and 800 d)  
  > "the oldest ejecta is about 500 d and 800 d, or 1.4 and 2.2 years old" (6 Discussion)

## Software

- **CASA** 5.1.1-5: calibration, concat, imaging  
  > "Calibration was conducted using the CASA 5.1.1-5 software package." (2 Archival observations with ALMA)
- **AIPS** : light curves (DFTPL), UVSUB, CLEAN imaging  
  > "to take advantage of the AIPS task `DFTPL` intended to easily generate light curves of stellar sources for radio photometry" (2 Archival observations with ALMA)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Core spectral index | -0.01 | 0.01 | dimensionless | 2 | ($\alpha = -0.01 \pm 0.01$) |
| Mean core flux density at 233 GHz | 88 | not stated | mJy | 5 | The SS 433 average flux density at the central ALMA frequency of 233 GHz was about 88 mJy. |
| Equipartition magnetic field | 30 | not stated | mG | 5 | The resulting equipartition field is then 30 mG. |
| Oldest ejecta age | ~90 | not stated | d | 5 | has an age $t_1\simeq 90$ d |
| Slowed expansion duration | 110 and 130 | not stated | d | 5 | it requires an initial slowed expansion phase lasting for $t_{\rm slow} \simeq 110$ and $130$ d |

## Qualitative findings

- Intrinsic brightness profiles of both jets are consistent with symmetry after correction  
  > "renders the intrinsic brightness profiles of both jets consistent with being symmetrical, even at millimetre wavelengths" (5 Intrinsic brightness profile)

## Claim tuples

- H: Energy losses of jet electrons are dominated by adiabatic expansion rather than synchrotron | E: Compare synchrotron lifetime with observed jet extent | R: Lifetime longer than a decade vs ~100 d jet extent | F: Adiabatic losses dominate | **supported**
- H: A slowed expansion phase early in the ejecta flow is needed | E: Predict VLA C-band extents with adiabatic model with a slow-to-free transition | R: t_slow ~110–130 d matches | F: Suggestive evidence for four months slowed expansion | **partially**
- H: Jets are symmetric intrinsically | E: Doppler and projection correction | R: Profiles consistent | F: Symmetric flow | **supported**

## Reasoning

- Why this data: Millimetre high-resolution observations of SS 433 are scarce  
  > "observations at very high radio frequencies with good angular resolution are still very scarce in the literature" (abstract)
- Why this method: _not stated_
- Alternative: Pure slowed expansion rejected as it predicts VLA jets far longer than observed  
  > "Clearly this is hard to reconcile with the (cite: 2011ApJ...736..118B) and (cite: 2010ApJ...719.1918R) images" (6 Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Only one epoch; limited frequency coverage; no nutation; simple model  
  > "our limited frequency coverage does not allow us a more precise measurement of $\alpha$ along the fainter jet flow regions." (2 Archival observations with ALMA)
- Caveat (inferred, ours): Core variability and resolution limits affect profile within ~40 d
- Caveat (inferred, ours): Equipartition field relies on core size and assumptions
- Caveat (inferred, ours): Single epoch with constant alpha taken from cm data
- Caveat (inferred, ours): Semi-analytic model is Newtonian and ignores helical structure

## Reproducibility

- Data public (paper): Archival ALMA data  
  > "We retrieved the only existing set of SS 433 observations in the ALMA archive" (2 Archival observations with ALMA)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Precession parameter values
- Missing: Custom AIPS task for variable-source subtraction
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Public data and analytic recipe, but imaging and several numeric inputs are unstated.
- Rediscovery candidate: no, Key imaging settings and custom tasks are unstated, and the recipe is only partly numeric.

## Links

- Method: (cite: 2010ApJ...719.1918R) (Doppler/beam correction and emission age prescription)
- Method: (cite: 1988ApJ...328..600H) (Adiabatic jet expansion model)
- Companion: (cite: 2011ApJ...736..118B) (VLA brightness profiles and spectral index)

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
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 49,
  "rate": 0.653
 },
 "evidence_ok": true
}
```

# A search for pre- and proto-brown dwarfs in the dark cloud Barnard 30 with ALMA

`2017A&A...597A..17H` | Astronomy and Astrophysics 2017 | first author: Huélamo, N. | arXiv: 1712.06400 | DOI: 10.1051/0004-6361/201628510

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: What is the nature of the 30 APEX/LABOCA sub-mm cores in Barnard 30, and are some of them proto- or pre-brown dwarfs, formed by which mechanism?  
  > "In particular, we aim to identify proto-brown dwarfs and study the mechanism of their formation." (abstract)
- Target **Barnard 30 (B30) LABOCA cores (30 pointings; 5 detected: LB08, LB10, LB14, LB19, LB31)**: coordinates LB14: 05:31:19.46 +12:09:15.1 (J2000); other detections in Table 1  
  > "a complex structure at a distance of $\sim$400 pc" (Introduction); "| 05:31:19.46          | +12:09:15.1              | 4.5             | B30-LB14$^*$     | 44.0      |" (Table 1); z/distance ~400 pc  
  > "a complex structure at a distance of $\sim$400 pc" (Introduction); "| 05:31:19.46          | +12:09:15.1              | 4.5             | B30-LB14$^*$     | 44.0      |" (Table 1); distance from Perryman1997; Dolan1999.1 (Lambda Orionis region)  
  > "a complex structure at a distance of $\sim$400 pc" (Introduction); "| 05:31:19.46          | +12:09:15.1              | 4.5             | B30-LB14$^*$     | 44.0      |" (Table 1)

## Data provenance

- ALMA projects: 2012.0.00542.S
- bands: Band 7 (880 um, avg 340.8 GHz)  
  > "December 12$^{th}$ at Band 7, as part of the ALMA Cycle 1 program 2012.0.00542.S." (2.1 ALMA observations)
- frequencies and spectral setup: four spectral windows centred at 345.8, 347.8, 333.9, 335.8 GHz; 1875 MHz effective bandwidth each; ~0.42 km/s velocity resolution after Hanning smoothing  
  > "centered at 345.8 GHz, 347.8 GHz, 333.9 GHz, and 335.8 GHz (average frequency of 340.8 GHz, or 880$\mu$m)" (2.1 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: 34 antennas (north), 32 and 33 (south), 12 m  
  > "We used 34 antennas (with $12\,{\rm m}$ diameter) in the northern region and 32 and 33 antennas in the South" (2.1 ALMA observations)
- configurations: _not stated_
- baselines: ~15 klambda to ~395 klambda  
  > "The shortest baseline of the ALMA observations is $\sim$ 15 $k\lambda$, while the upper end of the baseline range corresponds to $\sim$395 $k\lambda$." (2.1 ALMA observations)
- angular resolution: North 0.93"x0.50" (PA=111); South 0.95"x0.48" (PA=-63.5)  
  > "0.93$''$ $\times$ 0.50$''$ (PA=111 degrees) and 0.95$''$ $\times$ 0.48$''$ (PA=-63.5 degrees)" (2.1 ALMA observations)
- max recoverable scale: ~6"  
  > "we estimate that the largest angular scale (LAS) detectable by the ALMA observations is $\sim$6"." (2.1 ALMA observations)
- sensitivity: continuum rms 0.12-0.26 mJy/beam; ~0.13 mJy average  
  > "The average $rms$ of our ALMA observations is $\sim$0.13 mJy." (4.1 ALMA detection rate)
- time on source: 3.7 hours total including overheads and calibration  
  > "accounting for 3.7 hours of total integration time including overheads and calibration" (2.1 ALMA observations)
- observing dates: 2012 March 25, December 3, December 12  
  > "The ALMA observations were performed in 2012 on March 25$^{th}$, December 3$^{rd}$ and December 12$^{th}$" (2.1 ALMA observations)
- pi or archival as stated: _not stated_
- Line: CO J=3-2 (345.8 GHz)
- Other facility **APEX/LABOCA**: 870 um maps and the 34 sub-mm cores (BGH16)  
  > "analyzed APEX/LABOCA 870 $\mu$m deep observations (average $rms$ of 7 mJy)" (Introduction)
- Other facility **APEX/SABOCA**: 350 um map, 17 sources  
  > "We detected a total of 17 sources in the SABOCA map" (2.2 SABOCA observations)
- Other facility **Spitzer, WISE, AKARI, CAHA/O2000, INT/WFC, Planck**: optical to far-IR photometry for SEDs  
  > "we gathered deep, multi-wavelength observations of B30 from the optical to the far-IR regime." (2.3 Complementary data)
- External data: LABOCA source catalog, fluxes, sizes, and ancillary multiwavelength photometry/limiting magnitudes  
  > "The data are fully described in BGH16." (2.3 Complementary data) [from Barrado2016 (BGH16)]
- External data: Dust opacity tables used for kappa  
  > "interpolating from the tables of (cite: Ossenkopf1994) for the case of thin ice mantles and a density of 10$^6$ cm$^{-3}$." (4.1 ALMA detections) [from Ossenkopf1994]
- External data: Planck dust temperature maps (17-21 K)  
  > "show temperature values between 17 and 21 K in the B30 region" (4.1 ALMA detections) [from Planck2014]
- Simulation/model as data: BT-SETTL evolutionary models used for LB14 stellar mass  
  > "with BT-SETTL evolutionary models (cite: Allard2012.1)" (4.1.1 LB14)

## Processing

### Calibration

- pipeline or manual: CASA data reduction; calibrators listed  
  > "Amplitude calibration was carried out using Ganymede and J0510+180." (2.1 ALMA observations)
- casa version: CASA 4.2.2  
  > "Data reduction was performed using version 4.2.2 of the Common Astronomy Software Applications package (CASA)." (2.1 ALMA observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ganymede and J0510+180  
  > "Amplitude calibration was carried out using Ganymede and J0510+180." (2.1 ALMA observations)
- flux scale uncertainty: _not stated_
- self calibration: applied on continuum of LB19 and LB14  
  > "We applied self-calibration using the continuum data in sources B30S-13 (LB19) and B30N-18 (LB14)." (2.1 ALMA observations)

### Imaging

- task: CLEAN  
  > "Imaging of the calibrated visibilities was done using the task CLEAN." (2.1 ALMA observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 2  
  > "Briggs weighting with robust parameter equal 2 was used in all continuum and line images presented in this paper." (2.1 ALMA observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied to final images  
  > "The final images were corrected for the response of the primary beam and used to derive the physical parameters." (2.1 ALMA observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.93"x0.50" North, 0.95"x0.48" South  
  > "The average synthesized beam sizes of the continuum data in the North and South regions" (2.1 ALMA observations)
- final rms: _not stated_

### Inherited from earlier work

- LABOCA detections, ancillary data and counterpart nomenclature from BGH16  
  > "The data are fully described in BGH16." (2.3 Complementary data) [from Barrado2016]
- LAS estimate formula  
  > "Following equation A5 from (cite: Palau2010), we estimate that the largest angular scale (LAS) detectable by the ALMA observations is $\sim$6"." (2.1 ALMA observations) [from Palau2010]
- Bonnor-Ebert critical density procedure  
  > "we followed the same procedure as (cite: deGregorio2016)" (5.3 Nature of ALMA detections) [from deGregorio2016]
- internal luminosity formula for 70um limit  
  > "using the formula by (cite: Dunham2008), scaled to the distance of B30" (5.3 Nature of ALMA detections) [from Dunham2008]

### Not stated but needed to reproduce (our reading)

- Number of clean iterations, thresholds, masks, cell and image size
- Self-calibration solution intervals and number of rounds
- Continuum channel selection and line-free channels (CO contamination)
- How flux densities and uncertainties were measured (point-source fit vs peak)
- Details of the ALMA-missing-flux calculation (LABOCA flux scaling)
- Moment map and channel settings for CO
- Bolometric luminosity/temperature SED integration method

## Analysis recipe

1. **Image continuum and CO(3-2) and detect sources**: CLEAN imaging with Briggs robust 2, primary-beam corrected; detections in 5 of 30 pointings, all unresolved  
  > "We report the detection of five sources (out of 30 pointings) in our ALMA dataset." (2.1 ALMA observations)
   - software: CASA
   - parameter: robust = 2  
  > "Briggs weighting with robust parameter equal 2 was used in all continuum and line images presented in this paper." (2.1 ALMA observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive masses from continuum**: Optically thin dust emission mass M = S D^2/(B(Td) kappa)  
  > "If we assume that the dust emission is optically thin, we can estimate the total mass (gas and dust) from thermal continuum emission" (4.1 ALMA detections)
   - parameter: Td = 15 K; kappa = 0.01715 cm2/g at 340.8 GHz; D = 400 pc  
  > "We obtained a $k_{\nu}$ of 0.01715 cm$^2$g$^{-1}$ for a gas to dust mass ratio of 100." (4.1 ALMA detections)
   - assumption: conservative Td of 15 K; gas-to-dust 100; thin ice mantles at 1e6 cm-3; uncertainty factor of four  
  > "we have selected a conservative dust temperature of 15 K to estimate the masses of the cores in B30." (4.1 ALMA detections)
   - fitting: _not stated_
   - validation: compared with LABOCA masses to compute missing flux  
  > "derived the percentage of flux that ALMA did not recover compared to a single-dish (LABOCA)" (4.1 ALMA detections)
3. **Find IR counterparts and classify via SEDs**: 1" search radius counterpart match; SED classification with IRAC colors, Lbol and Tbol; BT-SETTL for LB14 star mass  
  > "We looked for possible infrared/optical counterparts to the ALMA sources using a search radius of 1" (the ALMA beam)" (4.1 ALMA detections)
   - fitting: _not stated_
   - validation: NED check within 5" for sources without counterparts  
  > "we also searched for counterparts in the NASA/IPAC Extragalactic Database (NED), but did not find any object within a 5" radius" (4.1 ALMA detections)
4. **Test gravitational stability and collapse of the three pre-BD core candidates**: Compare LABOCA densities with Bonnor-Ebert critical density; compare ALMA masses with expectation from r^-2 profile inside the ALMA beam  
  > "compared the density of the LABOCA cores with the critical density ($n_{\rm crit}$) of a Bonnor-Ebert (BE) isothermal sphere" (5.3 Nature of ALMA detections)
   - parameter: T = 15 K; ALMA beam radius 140 AU; core formation efficiency ~30%  
  > "assuming that the core formation efficiency in low-mass dense cores is $\sim$30%" (5.3 Nature of ALMA detections)
   - fitting: _not stated_
   - validation: estimated r^-2 masses consistent with observed within factor of 4  
  > "they are consistent with the measured ones within the uncertainties (typically of a factor of 4)" (5.3 Nature of ALMA detections)

## Software

- **CASA** 4.2.2: calibration, self-calibration, CLEAN imaging  
  > "Data reduction was performed using version 4.2.2 of the Common Astronomy Software Applications package (CASA)." (2.1 ALMA observations)
- **BOA** : SABOCA data reduction  
  > "we used the Bolometer Array Analysis Software (BOA" (2.2 SABOCA observations)
- **CRUSH** : SABOCA data reduction with -faint -deep  
  > "(options -faint -deep in CRUSH)" (2.2 SABOCA observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA detections | 5 of 30 (17%) | not stated | dimensionless | 1 | we have only detected 5 out of 30 sources, corresponding to a detection rate of 17%. |
| LB14 flux density | 44.0 | ±0.5 (2-sigma) | mJy | 1 | 35$\pm$14 mJy versus 44.0$\pm$0.5 mJy, assuming 2-$\sigma$ errors |
| ALMA masses of detections (15 K) | 0.9 to 67 | factor of four | M_Jup | 2 | with estimated masses between 0.9 and 67 M$_{\rm Jup}$ |
| LB14 disk mass | 43 (20 K), 24 (30 K) | not stated | M_Jup | 2 | We estimate a disk mass of 43 M$_{\rm Jup}$ for 20 K, or 24 M$_{\rm Jup}$ for 30 K. |
| LB19 Lbol and Tbol | 1.2 Lsun; ~235 K | not stated | Lsun; K | 3 | we obtain a $L_{\rm bol}$ of 1.2 $L_{\odot}$ and a temperature of $T_{\rm bol}$ $\sim$ 235 K |
| LB08 Lbol limit | <0.08 | not stated | Lsun | 3 | We estimate L$_{bol}$ $<$0.08 L$_{\odot}$ and T$_{bol}$ $>$ 54 K, respectively. |
| LB31 Lbol limit | <0.05 | not stated | Lsun | 3 | we can estimate L$_{bol}$ $<$0.05 L$_{\odot}$ and T$_{bol}$ $>$ 21 K |
| Final central-object masses (30% of LABOCA + ALMA) | ~41 (LB08), ~17 (LB10), ~26 (LB31) | not stated | M_Jup | 4 | we obtain $\sim$41 M$_{\rm Jup}$ (LB08), $\sim$17 M$_{\rm Jup}$ (LB10), and $\sim$26 M$_{\rm Jup}$ (LB31) |
| Expected ALMA-beam masses for r^-2 profile | ~3, 1, 2 (LB08, LB10, LB31) | factor of 4 | M_Jup | 4 | The estimated masses are $\sim$3, 1, and 2 M$_{\rm Jup}$ for LB08, LB10 and LB31, respectively. |

## Qualitative findings

- CO(3-2) in LB14 shows double-peaked spectrum consistent with a rotating disk; LB19 shows a compact component with infall signature and extended ~2400 AU rotating oblate envelope  
  > "The gas emission is consistent with a rotating disk in the case of B30-LB14, and with an oblate rotating envelope with infall signatures in the case of LB19." (abstract)

## Claim tuples

- H: Which LABOCA cores host compact sub-mm sources and what are their counterparts? | E: ALMA 880 um observation of 30 cores with IR counterpart search | R: 5 unresolved detections; LB14 Class II, LB19 Class I, three without IR counterparts | F: Two are low-mass YSOs; three are deeply embedded objects or pre-BD core candidates | **supported**
- H: Are the three ALMA pre-BD core candidates consistent with turbulent fragmentation (gravitationally stable)? | E: Bonnor-Ebert critical density comparison using LABOCA masses | R: LABOCA cores appear gravitationally stable but compact sources indicate collapse | F: Inconsistent with turbulent fragmentation; cores may be undergoing large-scale contraction with r^-2 profile | **partially**
- H: Why are most LABOCA cores undetected by ALMA? | E: Sensitivity and LAS comparison | R: Sensitivity sufficient; missed flux >85% | F: Most cores have sizes larger than ~2400 AU and may be transient | **supported**

## Reasoning

- Why this data: ALMA resolution and positional accuracy to assign counterparts unambiguously to LABOCA sources  
  > "The superb spatial resolution, great sensitivity, and positional accuracy of ALMA can help us to unambiguously assign the correct counterparts to the sub-mm sources" (Introduction)
- Why this method: _not stated_
- Alternative: Three sources without IR counterparts considered as deeply embedded protostars (VeLLOs) vs starless pre-BD cores; extragalactic contaminants not excluded  
  > "they could be classified either as deeply embedded protostars undetected in the Spitzer observations (cite: Stutz2013), or as starless cores." (5.3 Nature of ALMA detections)
- How they decided it was enough: _not stated_
- Limitation (authors): Cannot exclude extragalactic contaminants for LB08, LB10, LB31  
  > "we cannot exclude the possibility that these three sources are extragalactic contaminants not included in the NED database" (5.3 Nature of ALMA detections)
- Limitation (authors): Mass uncertainty a factor of four from opacity and temperature  
  > "the uncertainty in the masses due to the opacity law and dust temperature is estimated to be a factor of four" (4.1 ALMA detections)
- Caveat (inferred, ours): Masses depend on assumed 15 K and opacity; flux missed by interferometer so ALMA masses are lower limits for cores
- Caveat (inferred, ours): No kinematic confirmation of infall for the pre-BD candidates
- Caveat (inferred, ours): Single-pointing detections at SNR ~4.6 (LB31) are marginal
- Caveat (inferred, ours): No ALMA-resolved SED; classification relies on non-detection limits

## Reproducibility

- Data public (paper): Cycle 1 program 2012.0.00542.S; public status not stated in paper  
  > "as part of the ALMA Cycle 1 program 2012.0.00542.S." (Observations / ALMA observations)
- Products in archive: _not stated_
- Missing: CLEAN parameters and masks
- Missing: self-calibration details
- Missing: flux extraction method
- Missing: SED integration details
- Data volume (inferred): ~100-300 GB raw for three Band 7 execution blocks
- Score (inferred): 3/5, Data identifiable and recipe simple (mass formula), but imaging and flux measurement details missing.
- Rediscovery candidate: yes, Archive data, simple recipe, numeric fluxes and masses in tables.

## Links

- Method: Ossenkopf1994 (dust opacity)
- Method: Palau2010 (largest angular scale)
- Method: Reid1988 (positional accuracy)
- Companion: Barrado2016 (BGH16) (LABOCA census and ancillary data)
- Companion: deGregorio2016 (Bonnor-Ebert stability procedure)
- Related: APEX/LABOCA B30 survey

## Checks

```json
{
 "quotes": 70,
 "quotes_ok": 70,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2012.0.00542.S"
 ],
 "obscore_codes_not_in_card": [
  "2012.1.00542.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 52,
  "rate": 0.675
 },
 "evidence_ok": true
}
```

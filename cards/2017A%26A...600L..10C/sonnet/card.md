# ALMA survey of massive cluster progenitors from ATLASGAL. Limited fragmentation at the early evolutionary stage of massive clumps

`2017A&A...600L..10C` | Astronomy and Astrophysics 2017 | first author: Csengeri, T. | arXiv: 1703.03273 | DOI: 10.1051/0004-6361/201629754

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: How do infrared-quiet massive ATLASGAL clumps (d ≤ 4.5 kpc) fragment from 0.3 pc to 0.06 pc scales at an early evolutionary stage?  
  > "We investigate the fragmentation properties from 0.3 pc to 0.06 pc scales of a homogenous sample of infrared-quiet massive clumps within 4.5 kpc selected from the ATLASGAL survey." (abstract)
- Target **35 infrared-quiet massive ATLASGAL clumps (d ≤ 4.5 kpc)**: coordinates per-source positions in Table 2  
  > "Here we present the sample of 35 infrared quiet massive clumps located within d ≤ 4.5 kpc, which could be conveniently grouped on the sky as targets for ALMA." (2. The sample of infrared quiet massive clumps); z/distance 1.3-4.2 kpc (Table 2)  
  > "Here we present the sample of 35 infrared quiet massive clumps located within d ≤ 4.5 kpc, which could be conveniently grouped on the sky as targets for ALMA." (2. The sample of infrared quiet massive clumps); distance from Csengeri et al. (2017)  
  > "Here we present the sample of 35 infrared quiet massive clumps located within d ≤ 4.5 kpc, which could be conveniently grouped on the sky as targets for ALMA." (2. The sample of infrared quiet massive clumps)

## Data provenance

- ALMA projects: 2013.1.00960.S
- bands: Band 7  
  > "We used a lowresolution wide-band setup in Band 7, yielding 4 × 1.75 GHz effective bandwidth with a spectral resolution of 976.562 kHz." (3. Observations and data reduction)
- frequencies and spectral setup: Basebands centred on 347.331, 345.796, 337.061, 335.900 GHz; 976.562 kHz resolution  
  > "The four basebands were centred on 347.331, 345.796, 337.061, 335.900GHz, respectively." (3. Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: ALMA 7m array (ACA), 9 to 11 antennas, Cycle 2  
  > "We present observations carried out in Cycle 2 with the ALMA 7m array using 9 to 11 of the 7m antennas" (3. Observations and data reduction)
- configurations: _not stated_
- baselines: 8.2 m (9.5kλ) to 48.9 m (53.4kλ)  
  > "baselines ranging between 8.2 m (9.5kλ) to 48.9 m (53.4kλ)" (3. Observations and data reduction)
- angular resolution: synthesized beam 3.5'' to 4.6'' (geometric mean)  
  > "The synthesized beam varies between 3.5 ′′ to 4.6 ′′ taking" (3. Observations and data reduction)
- max recoverable scale: ~19'' largest angular scale  
  > "the rest of the emission is filtered above the typically 19 ′′ largest angular scale sensitivity of the ALMA 7m array observations." (4. Results and analysis)
- sensitivity: median rms 54 mJy/beam  
  > "The achieved median rms noise level is 54 mJy/beam" (3. Observations and data reduction)
- time on source: ~5.4 min per source  
  > "Each source was observed for ∼5.4 min in total." (3. Observations and data reduction)
- observing dates: June-July 2014 (five groups)  
  > "1 320 < ℓ< 330 [◦] 8, 16 July 2014" (Table 1)
- pi or archival as stated: _not stated_
- Other facility **ATLASGAL (APEX, 870 µm)**: Clump-scale flux densities and sample selection, compared with ALMA fluxes  
  > "compare the integrated flux in compact sources seen by the ALMA 7m array with the ATLASGAL flux densities measured over the primary beam of the array" (4. Results and analysis)
- External data: Sample selection, clump masses, distances, T_d=18 K for clumps  
  > "Column 10 gives the distance from Csengeri et al. (2017)." (Table 2) [from Csengeri et al. (2017)]
- External data: Dust opacity κ870µm = 0.0185 g cm-2 (gas-to-dust 100)  
  > "κ 870µm = 0.0185g cm −2 from Ossenkopf & Henning (1994) accounting for a gas-to-dust ratio of 100" (4. Results and analysis) [from Ossenkopf & Henning (1994)]

## Processing

### Calibration

- pipeline or manual: standard procedures in CASA  
  > "The data was calibrated using standard procedures in CASA 4.2.1." (3. Observations and data reduction)
- casa version: CASA 4.2.1  
  > "The data was calibrated using standard procedures in CASA 4.2.1." (3. Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan, Ceres (groups 1-3); Neptune (groups 4-5)  
  > "J1427-4206 J16170-5848 Titan, Ceres 5.0 × 2.9 -78.6 3.8 19.3 − 83.5" (Table 1)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: CLEAN  
  > "We used a robust weight of 0.5 for imaging, and the CLEAN algorithm for the deconvolution" (3. Observations and data reduction)
- weighting robust: robust = 0.5  
  > "We used a robust weight of 0.5 for imaging, and the CLEAN algorithm for the deconvolution" (3. Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: channels with lines identified per source and excluded; remaining averaged  
  > "we first identified the channels with spectral lines towards each source, and excluding these averaged the remaining channels." (3. Observations and data reduction)
- primary beam correction: applied  
  > "and corrected for the primary beam attenuation." (3. Observations and data reduction)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 3.5'' to 4.6'' (mean of axes)  
  > "The synthesized beam varies between 3.5 ′′ to 4.6 ′′ taking" (3. Observations and data reduction)
- final rms: median 54 mJy/beam  
  > "The achieved median rms noise level is 54 mJy/beam" (3. Observations and data reduction)

### Inherited from earlier work

- Mass formula and clump parameters (CFE uses clump mass and same physical parameters)  
  > "we assume optically thin dust emission and use the same formula as in Csengeri et al. (2017)" (4. Results and analysis) [from Csengeri et al. (2017)]

### Not stated but needed to reproduce (our reading)

- Which channels were line-free for each source
- Cell size and image size
- CLEAN threshold, masks and iteration count
- Exact Gaussclumps settings
- Flux calibrator assignment details and flux scale uncertainty
- Monte Carlo sample count and convergence criterion
- Clump masses used for CFE (from Csengeri et al. 2017)

## Analysis recipe

1. **Make line-free continuum images**: Calibrate in CASA, average line-free channels, CLEAN with robust 0.5, primary beam correct  
  > "We used a robust weight of 0.5 for imaging, and the CLEAN algorithm for the deconvolution, and corrected for the primary beam attenuation." (3. Observations and data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract compact sources**: 2D Gaussian fitting with Gaussclumps, sources down to ~7σ  
  > "A total number of 124 fragments down to a ∼7 σ rms noise level are systematically identified within the primary beam" (4. Results and analysis)
   - software: GILDAS
   - fitting: 2D Gaussian  
  > "using the Gaussclumps task in GILDAS [2], which performs a 2D Gaussian fitting." (4. Results and analysis)
   - validation: Compared integrated flux with ATLASGAL; 16-47% recovered  
  > "We recover between 16-47% of the flux" (4. Results and analysis)
3. **Derive core masses**: Optically thin dust: M = S d² κ⁻¹ B(Td)⁻¹  
  > "M = S 870µm d 2 κ 870µm −1 B 870µm (T d ) −1" (4. Results and analysis)
   - assumption: Td = 25 K for cores (factor of two mass uncertainty); κ870 = 0.0185 g cm-2; gas-to-dust 100  
  > "We adopt thus T d =25 K which results up to a factor of two uncertainty in the mass estimate." (4. Results and analysis)
   - fitting: _not stated_
   - validation: Td range 15-38 K estimated with Goldreich & Kwan (1974) model  
  > "we estimate T d =15-38K for the luminosity range of 10 2 − 10 4 L ⊙" (4. Results and analysis)
4. **Fit core mass distribution slope**: Least-square power-law fit above 50 Msun completeness limit; Monte Carlo over Td  
  > "The least square power-law fit to the highest mass bins above the completeness limit gives α = −1.01 ± 0.20" (4. Results and analysis)
   - parameter: _not stated_
   - fitting: least squares  
  > "The least square power-law
fit to the highest mass bins above the completeness limit gives
α = −1.01 ± 0.20" (4. Results and analysis)
   - validation: Monte Carlo repeated until slope standard deviation converged  
  > "repeated the tests until the standard deviation of the measured slope reached convergence" (4. Results and analysis)
5. **Compare with Jeans mass, turbulence and magnetic support**: Thermal Jeans mass, Turbulent Core model, magnetic critical mass (Bertoldi & McKee)  
  > "Using the Turbulent Core model (McKee & Tan 2003) for cores with M MDC >150 M ⊙ at the average radius of 0.025 pc" (5.2. Which physical processes influence fragmentation?)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2.1: calibration and imaging  
  > "The data was calibrated using standard procedures in CASA 4.2.1." (3. Observations and data reduction)
- **GILDAS (Gaussclumps)** : 2D Gaussian source extraction  
  > "We identify and measure the parameters of the compact sources using the Gaussclumps task in GILDAS" (4. Results and analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of fragments | 124 | not stated | sources | 2 | A total number of 124 fragments down to a ∼7 σ rms noise level |
| Mean fragments per clump | 3 | not stated | sources | 2 | This gives on average, N¯ fr =3 sources per clump |
| Core mass slope α | -1.01 | 0.20 | dimensionless | 4 | gives α = −1.01 ± 0.20 |
| Monte Carlo slope | 1.01 | 0.11 | dimensionless | 4 | the normal temperature distribution gives α MC =1.01±0.11 |
| Most massive core SDC335-MM1 | ~400 | not stated | Msun | 3 | the most massive core with ∼400 M ⊙ within a deconvolved FWHM size of 0.054pc |
| Mean core mass | ~63 | not stated | Msun | 3 | The extracted cores have a mean mass of ∼63 M ⊙ |
| Flux recovered vs ATLASGAL | 16-47 | not stated | percent | 2 | We recover between 16-47% of the flux |

## Qualitative findings

- Fragmentation is limited; 77% of clumps host at most 3 compact sources and ~14% remain single.  
  > "45% of the clumps hosts up to two, while 77% host up to three compact sources." (4. Results and analysis)

## Claim tuples

- H: Massive IR-quiet clumps fragment strongly as expected from thermal Jeans mass | E: ALMA 7m continuum source extraction and mass estimates | R: Mean 3 fragments per clump; core masses up to ~400 Msun far exceed Jeans mass ~1 Msun | F: Fragmentation is limited and not thermal | **supported**
- H: Turbulence or magnetic fields support the massive cores | E: Turbulent Core model and magnetic critical mass estimates | R: Required linewidth ≳6 km/s and B>10 mG at core densities | F: Lack observational support for sufficient support | **partially**
- H: Core mass distribution matches the IMF | E: Power-law fit with Monte Carlo on Td | R: α = -1.01 ± 0.20, shallower than IMF | F: Intrinsically shallower unless temperatures scale with brightness or further fragmentation occurs | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Radiative feedback as limit on fragmentation disfavoured for lack of embedded low-mass protostars  
  > "we lack evidence for a potential deeply embedded population of low-mass protostars needed to heat up the collapsing gas." (5.2. Which physical processes influence fragmentation?)
- How they decided it was enough: _not stated_
- Limitation (authors): Up to factor of two mass uncertainty from dust temperature  
  > "We adopt thus T d =25 K which results up to a factor of two uncertainty in the mass estimate." (4. Results and analysis)
- Limitation (authors): Poor uv-sampling and elongated beams in groups 4 and 5  
  > "for groups 4 and 5, the observations have been carried out at low elevation resulting in an elongated beam and poor uv-sampling." (3. Observations and data reduction)
- Caveat (inferred, ours): Short 7m-array snapshots filter large scales and resolution of ~0.06 pc may hide further fragmentation
- Caveat (inferred, ours): Single assumed Td of 25 K for all cores
- Caveat (inferred, ours): No line data to check distances or kinematics
- Caveat (inferred, ours): Mass completeness varies among fields

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Source table available at CDS  
  > "The full table is available in electronic form at the CDS via anonymous ftp" (Table 2)
- Missing: Imaging cell/image size and CLEAN threshold
- Missing: Line-free channel selection
- Missing: Gaussclumps parameters
- Missing: Clump masses from Csengeri et al. 2017
- Data volume (inferred): ~10-50 GB raw for 35 short ACA fields
- Score (inferred): 3/5, Short letter; main steps and numbers given, but imaging and extraction parameters are sparse.
- Rediscovery candidate: yes, Data from a single public project; the recipe is simple and the results are numeric (mass table, slope).

## Links

- Companion: Csengeri et al. (2017) (Sample definition, clump masses and distances)
- Related: ATLASGAL

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
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
  "facts": 70,
  "stated": 44,
  "rate": 0.629
 },
 "evidence_ok": true
}
```

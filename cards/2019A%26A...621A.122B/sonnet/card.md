# High-mass star formation at sub-50 au scales

`2019A&A...621A.122B` | Astronomy and Astrophysics 2019 | first author: Beuther, H. | arXiv: 1811.10245 | DOI: 10.1051/0004-6361/201834064

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: What are the physical properties of the densest structures (fragmentation, kinematics, jet/outflow vs disk) in the high-mass hot core G351.77-0.54 at sub-50 au resolution?  
  > "We aim to resolve the dust and gas emission at the highest spatial resolution to study the physical properties of the densest structures during high-mass star formation." (abstract)
- Target **G351.77-0.54 (IRAS 17233-3606)**: coordinates 17:26:42.568 -36:09:17.60 (J2000, phase center)  
  > "The phase center of our observations was R.A. (J2000.0) 17:26:42.568 and Dec. (J2000.0) -36:09:17.60." (2 Observations); "early studies put it at 2.2 kpc (cite: norris1993), more recent investigations favor smaller distances around 1 kpc (cite: leurini2011)." (Introduction); z/distance 1 kpc or 2.2 kpc (debated); vlsr ~ -3.6 km/s  
  > "The phase center of our observations was R.A. (J2000.0) 17:26:42.568 and Dec. (J2000.0) -36:09:17.60." (2 Observations); "early studies put it at 2.2 kpc (cite: norris1993), more recent investigations favor smaller distances around 1 kpc (cite: leurini2011)." (Introduction); distance from Leurini et al. 2011 (1 kpc); Norris et al. 1993 (2.2 kpc)  
  > "The phase center of our observations was R.A. (J2000.0) 17:26:42.568 and Dec. (J2000.0) -36:09:17.60." (2 Observations); "early studies put it at 2.2 kpc (cite: norris1993), more recent investigations favor smaller distances around 1 kpc (cite: leurini2011)." (Introduction)

## Data provenance

- ALMA projects: 2015.1.00496.S
- bands: Band 6 (1.3 mm), LO 226.378 GHz  
  > "The 1.3 mm band 6 receivers were tuned to the LO frequency of 226.378 GHz with two spectral windows (spws) in the upper and lower sidebands, respectively." (2 Observations)
- frequencies and spectral setup: four spws; resolution 244 kHz, 488 kHz and 3906 kHz (~0.33, ~0.67, 5.3 km/s)  
  > "The spectral resolution of the spws was 244 kHz, 488 kHz, and for the wider spectral windows 3906 kHz, corresponding to velocity resolutions of $\sim$0.33, $\sim$0.67 and 5.3 km s$^{-1}$, respectively." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 17 m to more than 16 km; only >55 m used for imaging  
  > "Between 33 and 43 antennas were in the array and baselines between 17 m and more than 16 km were covered." (2 Observations)
- angular resolution: 21 mas x 15 mas continuum (PA -74 deg); ~25 x 20 mas lines (PA -86 deg)  
  > "This results in a synthesized beam of 21 mas $\times$ 15 mas with a position angle of -74$^{\circ}$." (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: continuum 1 sigma ~50 uJy/beam; lines ~0.9 mJy/beam per 1 km/s channel  
  > "The continuum 1$\sigma$ rms is $\sim$50 $\mu$Jy beam$^{-1}$, and the typical rms for the spectral lines in a line-free channel of 1 km s$^{-1}$ width is $\sim$0.9 mJy beam$^{-1}$." (2 Observations)
- time on source: 24-45 min on source per block, four blocks  
  > "The duration of the four scheduling blocks varied between 1 and 1.6 hours with on-source target observing times between 24 and 45 minutes." (2 Observations)
- observing dates: Nov. 5 to Dec. 2, 2015 (cycle 3)  
  > "observed with ALMA as a cycle 3 project (id 2015.1.00496) in four separate observing blocks between Nov. 5 and Dec. 2, 2015." (2 Observations)
- pi or archival as stated: _not stated_
- Line: SiO 5-4 (217.10498 GHz)
- Line: unidentified high-excitation line (e.g. HDCO or CH3CH2CN) 217.82 GHz line (217.82 GHz)
- Other facility **ATLASGAL**: 870 um peak flux density used to estimate missing flux  
  > "we extract the 870 $\mu$m flux (central frequency 345 GHz) of G351.77-0.54 from the ATLASGAL survey (cite: schuller2009)." (3.1)
- External data: ATLASGAL 870 um peak flux density 52.1 Jy/beam (19.2'' beam)  
  > "Scaling the 870 $\mu$m peak flux density of 52.1 Jy beam$^{-1}$ (with a beam size of $19.2''$)" (3.1) [from (cite: schuller2009)]
- External data: Previous ALMA 690 GHz CO(6-5) and CH3CN data, 438 um continuum sources  
  > "Figure [6](#mom1_co) shows the previous CO(6–5) data (cite: beuther2017b)" (3.2) [from (cite: beuther2017b)]
- External data: dust opacity 1.11 cm2/g at 1.3 mm  
  > "we are using for the 1.3 mm dust opacity $\kappa$ a value of 1.11 cm$^2$ g$^{-1}$ from (cite: ossenkopf1994) at high densities of $10^8$ cm$^{-3}$." (3.1) [from (cite: ossenkopf1994)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline following observatory scripts  
  > "The calibration of the data was done with the ALMA pipeline in CASA (cite: mcmullin2007) version 4.5.0 following the scripts provided by the observatory." (2 Observations)
- casa version: CASA 4.5.0  
  > "version 4.5.0 following the scripts provided by the observatory" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1617-5848 (flux), J1517-2422 (bandpass), J1733-3722 (phase)  
  > "Bandpass and flux calibration were conducted with the sources J1517-2422 and J1617-5848, respectively." (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: phase-only, down to 30 s time steps; no amplitude self-cal  
  > "we applied phase-only self-calibration to the data going down to time-steps of 30 sec." (2 Observations); "No amplitude self-calibration was applied." (2 Observations)

### Imaging

- task: CASA (task not named)  
  > "The following imaging was also conducted within CASA." (2 Observations)
- deconvolver: _not stated_
- weighting robust: continuum robust -2 (uniform); lines robust 0  
  > "For the continuum images we applied a robust weighting of -2, corresponding to uniform weighting." (2 Observations); "The line data were then imaged with a robust weighting of 0" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: a few apparently line-free parts of spectra; weak slope remains  
  > "A few apparently line-free parts of the spectra were used for the continuum subtraction." (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: only baselines >55 m used  
  > "in the imaging process we only used data from baselines longer than 55 m" (2 Observations)
- smoothing: _not stated_
- final beam: 21 x 15 mas continuum; 25 x 20 mas lines  
  > "resulting in a slightly larger synthesized beam of $\sim$25 mas $\times$ 20 mas with a position angle of -86$^{\circ}$." (2 Observations)
- final rms: 50 uJy/beam continuum  
  > "The continuum 1$\sigma$ rms is $\sim$50 $\mu$Jy beam$^{-1}$" (2 Observations)

### Inherited from earlier work

- vlsr of -3.6 km/s  
  > "Following (cite: leurini2011), we use as $\varv_{\rm lsr}$ a value of $\sim -3.6$ km s$^{-1}$." (Introduction) [from (cite: leurini2011)]
- mass/column density equations for dust emission  
  > "Following the equations outlined in (cite: schuller2009) for dust emission" (3.1) [from (cite: schuller2009)]
- gas-to-dust ratio 150  
  > "a gas-to-dust mass ratio of 150 is assumed (cite: draine2011)" (3.1) [from (cite: draine2011)]

### Not stated but needed to reproduce (our reading)

- Continuum image size, cell size, deconvolver, and clean thresholds/masks
- Which channels were used as line-free for continuum subtraction
- Exact spw frequency ranges and which spw was bandpass/phase calibrated
- Moment map clipping thresholds and PV cut widths
- Exact flux density scale uncertainty
- Details of the self-calibration solint sequence and reference antenna
- Tool used for Tb conversion (Rayleigh-Jeans or full Planck)

## Analysis recipe

1. **calibrate and self-calibrate**: ALMA pipeline in CASA, then phase-only self-calibration  
  > "we applied phase-only self-calibration to the data going down to time-steps of 30 sec." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: compared images before and after self-calibration; structures recovered, noise decreased  
  > "Images prior and after self-calibration were carefully compared, and while all structures are well recovered, the noise is decreased after self-calibration." (2 Observations)
2. **image continuum and lines**: Continuum from whole bandpass with robust -2; lines with robust 0; baselines >55 m only  
  > "we use the continuum image created from the whole bandpass." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: compared line-free-only continuum to full-bandpass continuum; barely any difference except lower noise  
  > "Structurally and with respect to the intensities, there was barely any difference between the two images, only the noise of the full-bandpass image was lower." (2 Observations)
3. **identify continuum cores and measure fluxes, Tb**: identified by eye following 5 sigma contours; integrated fluxes within 4 sigma contours; peak and mean brightness temperatures  
  > "we identify the source structures by eye following the 5$\sigma$ contours in Fig. [2](#cont)." (3.1)
   - fitting: _not stated_
   - validation: missing flux estimated against ATLASGAL scaled flux  
  > "Taking these numbers, we recover only about 2.1% of the total continuum emission in the field." (3.1)
4. **derive masses and column densities (lower limits)**: optically thin dust formula with Tb as temperature proxy  
  > "using the derived brightness temperature as an approximate proxy to estimate the actual temperatures seems a reasonable approach." (3.1)
   - parameter: column density T = 1000 K for mm1, mm2; 100 K for others; masses use mean Tb within 4 sigma  
  > "we use 1000 K for the two very bright sources mm1 and mm2, and lower temperatures of 100 K for the other sources" (3.1)
   - assumption: kappa 1.11 cm2/g at 1.3 mm; gas-to-dust 150; distances 1 and 2.2 kpc  
  > "a gas-to-dust mass ratio of 150 is assumed (cite: draine2011)" (3.1)
   - fitting: _not stated_
   - validation: _not stated_
5. **compare to Jeans fragmentation**: Jeans lengths/masses from CORE densities 1e7-1e8 cm-3 and T~50 K compared with observed separations and masses  
  > "we find Jeans lengths between roughly 870 and 2800 au, and Jeans masses between 0.1 and 0.4 M$_{\odot}$." (4.1 Fragmentation)
   - assumption: mean temperature ~50 K  
  > "Assuming mean temperatures of around 50 K for these regions" (4.1 Fragmentation)
   - fitting: _not stated_
   - validation: _not stated_
6. **analyse line kinematics**: moment-1 maps, channel maps, position-velocity diagrams of the 217.82 GHz and SiO(5-4) lines; compare to CO(6-5) and CH3CN from earlier data  
  > "Figure [3](#mom1) presents a first moment map of the 217.82 GHz line" (3.2)
   - fitting: _not stated_
   - validation: compared velocity gradient orientation to outflow and previously inferred disk orientation  
  > "the rotational motion visible in the CH$_3$CN($37_k-36_k$) lines at $\sim$680 GHz with almost Keplerian-like motion is oriented perpendicular to the outflow" (3.2)

## Software

- **CASA** 4.5.0: pipeline calibration, self-calibration, imaging  
  > "The calibration of the data was done with the ALMA pipeline in CASA (cite: mcmullin2007) version 4.5.0" (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| number of continuum sub-sources | 12 | not stated | dimensionless | 3 | This way, we identify 12 separate mm sources within a radius of roughly $3.5''$ |
| peak brightness temperature mm1 | 1144 | not stated | K | 3 | / mm1 / 17:26:42.533 / -36:09:17.37 / 15.0 / 47.4 / 1144 / 53 / 0.41 / 2.0 / 3.3 / |
| peak brightness temperature mm2 | 1027 | not stated | K | 3 | / mm2 / 17:26:42.563 / -36:09:17.68 / 13.5 / 42.3 / 1027 / 93 / 0.20 / 1.0 / 3.0 / |
| sum of sub-core fluxes | ~208 | not stated | mJy | 3 | the sum of the fluxes of all identified sub-cores accumulates to only $\sim$208 mJy. |
| recovered fraction of continuum | 2.1 | not stated | % | 3 | we recover only about 2.1% of the total continuum emission in the field. |
| core masses (lower limits) | 0.01-0.51 Msun at 1 kpc; 0.1-2.5 Msun at 2.2 kpc | not stated | Msun | 4 | / mm9 / 17:26:42.280 / -36:09:17.73 / 1.4 / 55.3 / 115 / 50 / 0.51 / 2.5 / 3.4 / |
| H2 number density of mm2 | 6.8e10 | not stated | cm-3 | 4 | we derive high values for the approximate molecular hydrogen densities around $6.8\times 10^{10}$ cm$^{-3}$. |
| Jeans length | 870-2800 | not stated | au | 5 | we find Jeans lengths between roughly 870 and 2800 au |
| Jeans mass | 0.1-0.4 | not stated | Msun | 5 | Jeans masses between 0.1 and 0.4 M$_{\odot}$ |
| highest velocities in 217.82 GHz moment 1 near mm1 | +7.9 and -9.0 within ~0.01 arcsec | not stated | km/s | 6 | the highest velocities are close to the center of mm1 with values of +7.9 and $-9.0$ km s$^{-1}$ within a separation of only $\sim$0.01$''$ |
| separation of peaks in -18 and +14 km/s channels | 0.049 arcsec (~108/49 au) | not stated | arcsec | 6 | The spatial peak positions in the channels at $-18$ and +14 km s$^{-1}$ are separated by only $0.049''$ or $\sim$108/49 au |

## Qualitative findings

- Most lines are in absorption against optically thick continuum; a few high-excitation lines are in emission  
  > "Due to the high continuum optical depth, most spectral lines are seen in absorption." (abstract)
- No Hubble-like velocity structure; consistent with steady-state turbulent entrainment  
  > "no Hubble-like velocity structure can be identified." (abstract)

## Claim tuples

- H: Does thermal Jeans fragmentation continue to sub-1000 au scales in high-mass cores? | E: 1.3 mm long-baseline continuum, core identification, masses and separations compared with Jeans estimates | R: 12 sub-sources; separations sub-100 to >1000 au; masses 0.01-2.5 Msun | F: Separations and masses are largely consistent with thermal Jeans fragmentation | **supported**
- H: Does the velocity gradient in emission lines toward mm1 trace an inner disk or the jet/outflow? | E: Moment, channel and PV maps of the 217.82 GHz and SiO lines compared with CO and CH3CN from earlier work | R: Gradient aligned with the outflow and perpendicular to the CH3CN rotation | F: Likely jet/outflow, a disk contribution not excluded | **partially**
- H: Which entrainment process dominates on small scales? | E: PV diagrams of the high-excitation line and SiO | R: Highest velocities near the center, no Hubble law | F: Consistent with turbulent entrainment via Kelvin-Helmholtz instabilities | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Only baselines >55 m used to concentrate on compact structures because short baselines are sparsely sampled  
  > "Therefore, in the imaging process we only used data from baselines longer than 55 m, which allows us to concentrate on the most compact structures." (2 Observations)
- Alternative: Keplerian disk interpretation of the velocity gradient considered but disfavoured because of the outflow alignment  
  > "However, several observational features argue against this interpretation." (3.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Masses and column densities are lower limits because of high optical depth and missing flux; the distance is uncertain  
  > "we stress that these values have to be considered as lower limits because of the high optical depth as well as the large amount of missing flux." (3.1)
- Caveat (inferred, ours): Line identification uncertain, so excitation arguments are weak
- Caveat (inferred, ours): Mean Tb used as the dust temperature in an optically thick regime makes masses highly uncertain
- Caveat (inferred, ours): Jeans comparison uses densities from a different survey at lower resolution
- Caveat (inferred, ours): Disk versus outflow conclusion rests on comparison with data of different resolution

## Reproducibility

- Data public (paper): ALMA cycle 3 data acknowledged by project ID; CDS tables stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00496.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, masks, thresholds)
- Missing: Line-free channel selection
- Missing: Self-calibration solint details
- Missing: Moment map and PV extraction parameters
- Data volume (inferred): ~100-300 GB raw for four long-baseline execution blocks
- Score (inferred): 3/5, Data public and key steps given (robust, baseline cut, assumptions, tables) but imaging details and extraction parameters are missing.
- Rediscovery candidate: yes, Public data, a mostly stated recipe, and numeric results in Table 2 (fluxes, Tb, masses).

## Links

- Method: (cite: schuller2009) (mass and column density equations for dust emission)
- Companion: (cite: beuther2017b) (previous ALMA 690 GHz study of the same region)
- Related: ATLASGAL
- Related: CORE (NOEMA)

## Checks

```json
{
 "quotes": 71,
 "quotes_ok": 71,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 48,
  "rate": 0.632
 },
 "evidence_ok": true
}
```

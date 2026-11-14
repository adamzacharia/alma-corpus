# The complexity of Orion: an ALMA view. III. The explosion impact

`2019A&A...624L...5P` | Astronomy and Astrophysics 2019 | first author: Pagani, L. | arXiv: 1904.00921 | DOI: 10.1051/0004-6361/201935267

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: How does the 550-year-old explosion in Orion KL affect the spatial and velocity distribution of different molecular species, and what does this imply for their gas-phase chemistry?  
  > "In this Letter, we study further the interaction of the explosion blowout with the surrounding gas and dense sources." (Introduction)
- Target **Orion BN-KL**: coordinates RA 05h35m14.160s, Dec -05d22m31.504s (J2000)  
  > "the part of the data discussed in this work are centered on ra$_{ J2000}$: 05$^h$35$^m$14.160$^s$, dec$_{ J2000}$: -05$\ensuremath{^\circ}$22$'$31.504$''$" (Observations); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00533.S
- bands: Band 6, 215-252 GHz, 16 GHz discontinuous bandwidth  
  > "Sixteen GHz of discontinuous bandwidth were covered in the frequency range 215 to 252 GHz." (Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 37-39 antennas  
  > "we performed deep observations of this source during Cycle 2 with 37–39 antennas, surveying 16 GHz in ALMA band 6" (Introduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: ~2 mJy/beam for the 234 GHz band; typically 5 mJy/beam for others  
  > "reaching a sensitivity of $\sim$2 mJy/beam while the other bands were observed only in one setup each (30 minutes duration), with 488 kHz channel spacing and reaching a typical noise of 5 mJy/beam" (Observations)
- time on source: 2.5 hours for the 234 GHz band; 30 minutes for other setups  
  > "One band, centered on $^{16}$O$^{18}$O at 234 GHz, was observed all the time (2.5 hours)" (Observations)
- observing dates: December 2014 (Cycle 2)  
  > "Observations were carried out in December 2014, during the Cycle 2 period, with 37 antennas, and 39 antennas for the last run." (Observations)
- pi or archival as stated: _not stated_
- Line: H2CO 9(1,8)-9(1,9) (216568.651 MHz)
- Line: H2CNH 7(1,6)-7(0,7) (250161.775 MHz)
- Other facility **12.5 micron mid-IR map (Greenhill et al. 2004)**: mid-infrared map compared with 1.2 mm continuum  
  > "We superimposed our 1.2 mm ALMA continuum map on the (cite: 2004ApJ...605L..57G) 12.5 $\mu$m map." (Mid-infrared and millimeter continuum map comparison)
- External data: Explosion age 550 +/- 25 years  
  > "an explosive event that occurred 550 $\pm$ 25 years ago (J.Bally, priv. communication)" (Introduction) [from J. Bally, private communication]
- External data: 12.5 micron map of the region  
  > "We superimposed our 1.2 mm ALMA continuum map on the (cite: 2004ApJ...605L..57G) 12.5 $\mu$m map." (Mid-infrared and millimeter continuum map comparison) [from (cite: 2004ApJ...605L..57G)]
- External data: Hot core appears not gravitationally bound  
  > "From the (cite: Feng:2015cl) data, we find that the HC does not seem to be gravitationally bound." (Mid-infrared and millimeter continuum map comparison) [from (cite: Feng:2015cl)]
- Simulation/model as data: Gas-phase chemical model with deuteration network, run at n=1e5 cm-3, T=150 K, zeta=1e-15 s-1  
  > "we ran our gas-phase chemical model including our deuteration network with the spin states of H$_2$ and H$_3^+$ isotopologues (cite: Pagani2011)." (Discussion)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

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
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Observations, data reduction and source labels described in Paper I  
  > "The observations have been described in detail in , and we give here only a short summary." (Observations) [from Paper I (cite: Pagani:2017fx)]
- Phase center as in Paper I  
  > "As in , the part of the data discussed in this work are centered on ra$_{ J2000}$" (Observations) [from Paper I (cite: Pagani:2017fx)]
- Chemical model with deuteration network and spin states  
  > "we ran our gas-phase chemical model including our deuteration network with the spin states of H$_2$ and H$_3^+$ isotopologues (cite: Pagani2011)." (Discussion) [from (cite: Pagani2011)]

### Not stated but needed to reproduce (our reading)

- Calibration and imaging procedures (CASA version, weighting, cleaning, continuum subtraction) are all deferred to Paper I
- Beam size and rms of the channel maps
- Channel width and velocity resolution of the maps
- How the continuum was separated from line emission
- Chemical model details (initial abundances, network, code) beyond the few listed parameters
- Method for the spatial velocity cuts

## Analysis recipe

1. **Make channel maps of selected species**: Channel maps overlaid on continuum, with contours at 10-90% of the peak of the strongest channel for each species  
  > "the white contours represent 10 to 90% of the peak emission of the strongest channel for that species (which may not be one of the displayed channels) in steps of 10%." (Channel maps)
   - parameter: Comparison at 2.5, 7.5 and 9.0 km/s  
  > "we compare all species that are strong enough to be plotted channel-wise, at three representative velocities of 2.5, 7.5, and 9.0 km s$^{-1}$." (Channel maps)
   - fitting: _not stated_
   - validation: _not stated_
2. **Estimate gas expansion velocity from elongation length**: Longest H2CO elongation of ~10 arcsec attained in 550 years implies ~40 km/s  
  > "the longest H$_2$CO elongation, $\sim$10$\ensuremath{''}$ can be attained in 550 years if the gas is moving at $\sim$40 km s$^{-1}$." (Channel maps)
   - assumption: Explosion age 550 years  
  > "an explosive event that occurred 550 $\pm$ 25 years ago (J.Bally, priv. communication)" (Introduction)
   - fitting: _not stated_
   - validation: Compared with CO clump velocities of ~140 km/s  
  > "This is much lower than the maximum $^{12}$CO clump velocities noticed in various data sets including our own, on the order of 140 km s$^{-1}$" (Channel maps)
3. **Test gas-phase destruction of deuterated species**: Gas-phase chemical model with deuteration network, starting from deuterium-rich gas  
  > "Starting from a gas rich in deuterated species (D$_2$CO/H$_2$CO $\approx$ 0.01 and NH$_2$D/NH$_3$ $\approx$ 0.3) at a density of 1 $\times$ 10$^{5}$ cm$^{-3}$, a temperature of 150 K" (Discussion)
   - parameter: cosmic ionization rate 1e-15 s-1, low extinction  
  > "low extinction to the ISRF and a harsh environment (approximated by a cosmic ionization rate $\zeta$ of 1  $\times$ 10$^{-15}$ s$^{-1}$)" (Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Longest H2CO elongation length | ~10 | not stated | arcsec | 2 | the longest H$_2$CO elongation, $\sim$10$\ensuremath{''}$ can be attained in 550 years if the gas is moving at $\sim$40 km s$^{-1}$. |
| Implied gas velocity | ~40 | not stated | km/s | 2 | the longest H$_2$CO elongation, $\sim$10$\ensuremath{''}$ can be attained in 550 years if the gas is moving at $\sim$40 km s$^{-1}$. |
| D2CO/H2CO ratio drop in 500-1000 yr | factor 3 to 40 | not stated | dimensionless | 3 | we found that the D$_2$CO/H$_2$CO ratio drops by a factor of 3 to 40 in 500 to 1000 years |
| NH2D/NH3 ratio drop in 500 yr | factor 6 to 200 | not stated | dimensionless | 3 | while the NH$_2$D/NH$_3$ ratio drops by a factor 6 to 200 in 500 years, and the abundance of NH$_2$D itself decreases by a factor 20 to 5000 |

## Qualitative findings

- Some species (H2CO, OCS, D2CO) show elongations pointing away from the explosion center, while others (H2CNH, NH2D, CH3OCH3, CH3OCHO, NH2CHO) stay near the dust peaks  
  > "we see that some molecular species show emission elongated to significant distances all pointing away from the explosion center, while other species do not." (Discussion)
- Hot core appears externally heated: IRc2 mid-IR emission lies between the explosion center and the HC  
  > "This confirms the claim of (cite: Zapata:2011ez) of the absence of an internal heating source for the HC but of external heating possibly due to the explosion." (Mid-infrared and millimeter continuum map comparison)

## Claim tuples

- H: The explosion wind drives molecules released from grains away from the explosion center | E: Channel maps of many species compared with continuum peaks | R: Many species show elongations pointing away from the explosion center | F: Winds from the explosion push recently released molecules away from dense cores | **supported**
- H: Species lacking elongation are rapidly destroyed in the gas phase after release | E: Gas-phase chemical model with deuteration | R: NH2D drops much faster than D2CO | F: Consistent with NH2D not expanding unlike D2CO | **supported**
- H: The expansion acts as a chemical time-of-flight experiment | E: Interpretation of channel maps | R: Species show different displacement lengths | F: Orion KL is a benchmark for COM chemistry models | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): No zero-spacing (total power) data, so extended species (CO, SO, SO2) are distorted and no column densities are derived  
  > "Since we do not yet have total power observations to include to the data set, this paper concentrates on the kinematics and spatial positioning of the sources rather than on discussions of column density." (Observations)
- Caveat (inferred, ours): Interpretation is qualitative, based on visual inspection of channel maps
- Caveat (inferred, ours): No quantitative offsets or uncertainties
- Caveat (inferred, ours): Chemical model is illustrative with one parameter set
- Caveat (inferred, ours): Missing short spacings may bias morphologies

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Full calibration and imaging recipe (in Paper I)
- Missing: Image cubes
- Missing: Chemical model code and network
- Data volume (inferred): Large; several hundred GB to ~1 TB raw for multiple 16 GHz Band 6 setups
- Score (inferred): 2/5, Qualitative letter with processing deferred to Paper I; few numeric results.
- Rediscovery candidate: no, Results are mostly qualitative and the recipe is deferred to another paper.

## Links

- Method: Pagani et al. 2017 (cite: Pagani:2017fx) (Observations and data reduction)
- Method: Pagani, Roueff & Lesaffre 2011 (cite: Pagani2011) (Deuteration chemical model)
- Companion: Favre et al. 2017 (cite: Favre:2017ch) (First detection of gGg' ethylene glycol and acetic acid in Orion)

## Checks

```json
{
 "quotes": 37,
 "quotes_ok": 37,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2013.1.00533.S"
 ],
 "obscore_codes_not_in_card": [
  "2013.1.00553.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 25,
  "rate": 0.379
 },
 "evidence_ok": true
}
```

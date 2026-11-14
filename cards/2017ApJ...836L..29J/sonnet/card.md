# <SUP>13</SUP>CO/C<SUP>18</SUP>O Gradients across the Disks of Nearby Spiral Galaxies

`2017ApJ...836L..29J` | The Astrophysical Journal Letters 2017 | first author: Jiménez-Donaire, María J. | arXiv: 1701.01734 | DOI: 10.3847/2041-8213/836/2/L29

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, astrochemistry
- Question: How does the 13CO/C18O (1-0) intensity ratio vary across the disks of nearby spiral galaxies, and what drives the variations (abundance vs optical depth)?  
  > "Comparing transitions of different optically thin isotopologues, e.g., $^{13}$CO/C$^{18}$O, offers the chance to trace abundance variations across the disks of galaxies." (Introduction)
- Target **NGC 628, 2903, 3184, 3351, 3627, 4254, 4321, 5055, 6946**: coordinates _not stated_; z/distance 5.6-16.4 Mpc (Table 1)  
  > "| NGC 3351$^{b}$ | 10.1 | 11 | 73 | 10.6 | SBb | 5.2 |" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00004.SV
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ALMA cubes convolved to 8"; EMPIRE at 33"  
  > "For this letter, we use versions of these cubes convolved to 8$\ensuremath{''}$." (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: EMPIRE typical rms ~2.0 mK (Tmb) at 33" with 4 km/s channels  
  > "At $33\ensuremath{''}$ resolution with $4$ km s$^{-1}$ wide channels, the typical rms noise is $\sim2.0$ mK ($T_{mb}$)." (2 Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 13CO 1-0 (110.20 GHz)
- Line: C18O 1-0 (109.78 GHz)
- Other facility **IRAM 30m (EMPIRE)**: 13CO and C18O maps of eight galaxies  
  > "EMPIRE (cite: 2016ApJ...822L..26B) is mapping a suite of molecular lines across the whole area of nine nearby galaxy disks using the IRAM 30-m telescope." (2 Observations)
- Other facility **HERACLES**: 12CO(2-1) used for local mean velocity for stacking  
  > "we estimate the local mean velocity of gas from bright $^{12}$CO (2-1) emission from HERACLES (cite: 2009AJ....137.4670L)." (2 Observations)
- Other facility **Herschel**: 70, 160, 250 micron maps for TIR / SFR surface density  
  > "we combine $\lambda = 70$, 160, and 250$\mu$m maps from *Herschel* (cite: 2011PASP..123.1347K)." (2 Observations)
- External data: Sigma_SFR values from Leroy et al. 2013  
  > "From (cite: 2013AJ....146...19L)." (Table 1) [from (cite: 2013AJ....146...19L)]
- External data: Literature 13CO/C18O ratios for Milky Way, starbursts, ULIRGs  
  > "Table [2](#table:results) includes a compilation of literature measurements targeting the central regions of starburst galaxies and ULIRGs." (Results) [from (cite: 2011RAA....11..787T; 2014A&A...565A...3H)]

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
- array combination: ALMA cubes feathered with IRAM for overlapping galaxies  
  > "Those that overlap EMPIRE have been corrected to account for short and zero spacing information using the `CASA` task `feather`" (2 Observations)
- smoothing: ALMA convolved to 8"  
  > "we use versions of these cubes convolved to 8$\ensuremath{''}$." (2 Observations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA observations, reduction and feathering  
  > "for more details, see Gallagher et al. (in prep.)." (2 Observations) [from Gallagher et al., in prep.]
- EMPIRE observation and reduction strategy  
  > "(cite: 2016ApJ...822L..26B) describe the basic EMPIRE observation and reduction strategy." (2 Observations) [from (cite: 2016ApJ...822L..26B)]
- Stacking procedure  
  > "we follow a procedure similar to that of (cite: 2011AJ....142...37S) and (cite: 2013AJ....146..150C)" (2 Observations) [from (cite: 2011AJ....142...37S); (cite: 2013AJ....146..150C)]

### Not stated but needed to reproduce (our reading)

- ALMA array configurations, dates, spectral setup, time on source
- CASA version and calibration details
- feather parameters
- radial/IR zone definitions and bin edges
- ALMA-based integration window
- 12CO(1-0) data for optical-depth estimate

## Analysis recipe

1. **Stack spectra in zones**: Divide galaxies into zones of radius or IR brightness, recenter spectra on local 12CO(2-1) mean velocity (13CO for ALMA C18O), average  
  > "We recenter the $^{13}$CO and C$^{18}$O spectra about this local mean $^{12}$CO velocity. Then, we average all spectra in each zone to construct a single, high signal-to-noise spectrum." (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure integrated intensities and ratios**: Sum channels with bright 12CO(2-1) emission, window usually ~60 km/s; uncertainty from signal-free noise  
  > "We calculated the uncertainty in the integrated intensity based on the noise estimated from the signal-free part of the stacked spectrum and the width of the integration window (usually $\sim$60 km s$^{-1}$)." (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Estimate SFR surface density**: TIR from Herschel 70/160/250 micron following Galametz et al. 2013, converted with Murphy et al. 2011  
  > "calculate the TIR surface brightness following (cite: 2013MNRAS.431.1956G), and then convert to star formation rate surface density using the prescription of (cite: 2011ApJ...737...67M)." (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
4. **Estimate 13CO optical depth**: 13CO/12CO ratio assuming thick 12CO, common Tex and filling factor, CO(2-1) thermalized with (1-0)  
  > "we find $0.05<\tau_{\rm13CO}<0.25$." (4.2 Changes in the Optical Depth)
   - software: DESPOTIC
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : feather to combine ALMA with short/zero spacing  
  > "using the `CASA` task `feather`" (2 Observations)
- **GILDAS/CLASS** : IRAM 30m data reduction  
  > "We reduce the data using the GILDAS/CLASS software" (2 Observations)
- **DESPOTIC** : dissociation rate with shielding  
  > "using `DESPOTIC` (cite: 2014MNRAS.437.1662K)" (4.1 Variations in the Molecular Abundances)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean 13CO/C18O, inner 30" | 6.0 | 0.9 | dimensionless | 2 | The average $^{13}$CO/C$^{18}$O ratio for the inner $30\ensuremath{''}$ region of our targets is 6.0$\pm$0.9 |
| Mean 13CO/C18O, whole disks | 7.9 | 0.8 | dimensionless | 2 | we find a mean ratio of 7.9$\pm$0.8 for the whole galaxy disks |
| 13CO optical depth range | 0.05-0.25 | not stated | dimensionless | 4 | we find $0.05<\tau_{\rm13CO}<0.25$ |

## Qualitative findings

- Ratio increases with galactocentric radius and decreases with SFR surface density; NGC 628 is an outlier  
  > "Leaving aside NGC 628, our targets tend to show rising $^{13}$CO/C$^{18}$O with increasing galactocentric radius and falling $^{13}$CO/C$^{18}$O with increasing $\Sigma_{\rm SFR}$." (Discussion)

## Claim tuples

- H: Normal spiral galaxies have central 13CO/C18O like the Milky Way rather than starbursts | E: Stacked IRAM and ALMA spectra in the inner 30" | R: 6.0±0.9 versus 3.4±0.9 for starbursts and 1.1±0.4 for ULIRGs | F: Centers resemble the Milky Way | **supported**
- H: Optical depth drives the ratio trends | E: Compared 13CO to 12CO | R: 0.05<tau<0.25 | F: Optical depth unlikely to drive trends; abundance changes preferred | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Selective photodissociation discarded  
  > "We can therefore discard the possibility of selective photodissociation as an explanation for our results." (4.1 Variations in the Molecular Abundances)
- How they decided it was enough: _not stated_
- Limitation (authors): Nucleosynthesis not a general explanation given the Milky Way 12C/13C trend  
  > "This argues against nucleosynthesis as a general explanation." (4.1 Variations in the Molecular Abundances)
- Caveat (inferred, ours): Disentangling fractionation from nucleosynthesis needs more lines
- Caveat (inferred, ours): ALMA sample is small and its processing is deferred to a companion paper

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA processing details (deferred to Gallagher et al. in prep.)
- Missing: EMPIRE data access
- Missing: stacking zone definitions
- Data volume (inferred): tens of GB for ALMA; IRAM cubes small
- Score (inferred): 2/5, Key ALMA processing and zone definitions are deferred or unstated.
- Rediscovery candidate: no, Recipe incomplete and relies on in-prep papers and EMPIRE data.

## Links

- Method: (cite: 2016ApJ...822L..26B) (EMPIRE observing and reduction strategy)
- Companion: Gallagher et al., in prep. (ALMA data reduction and feathering)
- Related: EMPIRE
- Related: HERACLES

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
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 24,
  "rate": 0.348
 },
 "evidence_ok": true
}
```

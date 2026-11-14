# Large molecular gas reservoirs in ancestors of Milky Way-mass galaxies nine billion years ago

`2016NatAs...1E...3P` | Nature Astronomy 2016 | first author: Papovich, C. | arXiv: 1610.05313 | DOI: 10.1038/s41550-016-0003

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, high_z_galaxies
- Question: How much cold molecular gas do progenitors of Milky Way-mass galaxies at z=1.2-1.3 hold, and how efficiently do they form stars?  
  > "The first step to understand star formation in galaxies like the Milky Way is to measure the amount of the cold gas in their progenitors at $z$$>$1." (abstract)
- Target **ZFOURGE CDFS 467, 4409, 6497, 8193**: coordinates _not stated_; z/distance z=1.2-1.3  
  > "CDFS 467 (8769)" (Table 2); "measured spectroscopic redshift." (Selection of Milky-Way-Mass Galaxy Progenitors); distance from spectroscopic redshifts from literature (Vanzella et al. 2008)  
  > "CDFS 467 (8769)" (Table 2); "measured spectroscopic redshift." (Selection of Milky-Way-Mass Galaxy Progenitors)

## Data provenance

- ALMA projects: 2011.0.01234.S
- bands: Band 4  
  > "Our Cycle 2 ALMA observations were taken between 2015 April 6 and 2015 May 2 in Band 4" (ALMA Observations and Data Reduction)
- frequencies and spectral setup: four spectral windows, 1.875 GHz each, 134.48-156.90 GHz  
  > "we configured ALMA to observe in four spectral windows, 1.875 GHz per window, and spanning frequencies 134.48 to 156.90 GHz" (ALMA Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C34-2, 36 antennas, max baseline 348.5 m  
  > "with 36 antennas in the C34-2 configuration, which provided a maximum baseline of 348.5 m" (ALMA Observations and Data Reduction)
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: 0.33-0.48 mJy/beam per channel  
  > "CDFS 8193 (28279) | 2015 Apr 6 | 4.6 | 41.8 | 134.5–149.5" (Table 2)
- time on source: 37.3-41.8 min per source  
  > "The ALMA integrations ranged between 37.3 to 41.8 min on source." (ALMA Observations and Data Reduction)
- observing dates: 2015 April 6 - May 2  
  > "taken between 2015 April 6 and 2015 May 2" (ALMA Observations and Data Reduction)
- pi or archival as stated: _not stated_
- Line: CO J=3-2 (345.8 GHz)
- Other facility **ZFOURGE (FourStar/Magellan)**: target selection, photometric redshifts, stellar masses  
  > "We selected the galaxies in our sample from the Fourstar Galaxy Evolution (ZFOURGE) survey" (ZFOURGE Dataset)
- Other facility **Spitzer and Herschel**: 24-160 micron fluxes for L_IR  
  > "The ZFOURGE fields include imaging at far–IR wavelengths from *Spitzer*/MIPS (24 $\mu$m), *Herschel*/PACS (70, 100, and 160 $\mu$m)." (Far–IR data and IR Luminosities)
- Other facility **HST**: CANDELS imaging for morphology and positions  
  > "The CO(3–2) emission coincides with the spatial positions of the galaxies in Hubble Space Telescope (HST) imaging" (abstract)
- External data: spectroscopic redshifts  
  > "assuming the optical spectroscopic redshift from the literature." (ALMA Observations and Data Reduction) [from (cite: vanz08)]
- External data: CO excitation ratio r31 = 0.66  
  > "$r_{31}$ = $I_{\mathrm{CO}(3-2)} /I_{\mathrm{CO}(1-0)} \times (1/3)^2$ = 0.66." (abstract) [from (cite: bola15)]
- External data: alpha_CO = 3.6 Msun (K km/s pc^2)^-1  
  > "We therefore adopt $\alpha_\mathrm{CO} =
3.6$ $M_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$" (Molecular Gas mass from CO emission) [from (cite: daddi10a)]

## Processing

### Calibration

- pipeline or manual: NRAO-supplied calibration script  
  > "with the calibration script supplied by the National Radio Astronomy Observatory (NRAO)" (ALMA Observations and Data Reduction)
- casa version: CASA 4.5.0-REL  
  > "version 4.5.0-REL" (ALMA Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We then ran the cleaning algorithm with natural weighting." (ALMA Observations and Data Reduction)
- uv taper: _not stated_
- cell size: 0.2 arcsec  
  > "with a cell size of $0\mbox{$.\!\!^{\prime\prime}$}2$" (ALMA Observations and Data Reduction)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: no continuum detected; no correction made  
  > "We failed to detect any signal of the continuum; we also therefore made no correction for the continuum to the CO line fluxes." (ALMA Observations and Data Reduction)
- line free channels: _not stated_
- primary beam correction: applied to total intensity maps  
  > "From the primary-beam-corrected, total intensity maps" (ALMA Observations and Data Reduction)
- array combination: _not stated_
- smoothing: channels of 25 and 75 km/s  
  > "we reduced the data with channels of 25 km s$^{-1}$ and 75 km s$^{-1}$" (ALMA Observations and Data Reduction)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- L_IR flux measurement and uncertainty methods  
  > "using methods identical to those described elsewhere.(cite: elbaz11; magn11; magn13)" (Far–IR data and IR Luminosities) [from (cite: elbaz11; magn11; magn13)]
- stellar masses and photometric redshifts  
  > "estimated from the multiwavelength catalogues as described elsewhere.(cite: tomc14; papo15)" (ZFOURGE Dataset) [from (cite: tomc14; papo15)]

### Not stated but needed to reproduce (our reading)

- Clean threshold, masks, iterations
- Channel ranges used to sum moment-0 maps
- Calibrator names
- Table 1 values not included in text
- Gaussian line-fit procedure details
- Spectral-window continuum channels

## Analysis recipe

1. **select targets**: ZFOURGE cuts on photo-z, mass, SFR, plus spectroscopic z  
  > "Stellar mass, $-0.15  <  \log M_\ast/\hbox{$M_\odot$}- 10.2 < +0.15$;" (Selection of Milky-Way-Mass Galaxy Progenitors)
   - fitting: _not stated_
   - validation: _not stated_
2. **image CO(3-2) and measure line flux**: CASA clean, moment maps, 2D profile fit of integrated map  
  > "using the two-dimensional profile fitting tool in CASA" (ALMA Observations and Data Reduction)
   - software: CASA
   - fitting: single and double Gaussians to spectra  
  > "we fit the spectra with models using single- and double-Gaussians" (ALMA Observations and Data Reduction)
   - validation: _not stated_
3. **derive L'CO**: L'CO formula with r31 = 0.66  
  > "we assume an integrated Rayleigh–Jeans brightness temperature line ratio" (abstract)
   - assumption: r31=0.66; H0=70, Om=0.3, OL=0.7  
  > "$\Omega_m = 0.3$, $\Omega_\Lambda = 0.7$, and $H_0 = 70$ km s$^{-1}$ Mpc$^{-1}$" (Conventions)
   - fitting: _not stated_
   - validation: Lower r31 0.4-0.5 would not change conclusions  
  > "would increase the $L^\prime(\mathrm{CO})$ values slightly but not change our conclusions." (abstract)
4. **derive L_IR**: fit IR SED templates to 24-160 micron fluxes; adopt Rieke et al.  
  > "We therefore adopt the $L_{\mathrm{IR}}$ from the fits to the Rieke et al. models to all the IR data" (Far–IR data and IR Luminosities)
   - fitting: Chary & Elbaz, Dale, Rieke templates  
  > "we fit models of the IR spectral energy distribution(cite: chary01; dale05; rieke09) to the flux densities in Table S1." (Far–IR data and IR Luminosities)
   - validation: Chary & Elbaz vs Rieke bracket range, 0.1-0.2 dex difference  
  > "which bracket the range of values" (Far–IR data and IR Luminosities)
5. **gas mass and fractions**: Mgas = alpha_CO L'CO, fgas = Mgas/(Mgas+M*)  
  > "$\alpha_\mathrm{CO}  = M_\mathrm{gas} / \hbox{$L^\prime(\mathrm{CO})$}.$" (Molecular Gas mass from CO emission)
   - assumption: alpha_CO = 3.6 Msun (K km/s pc^2)^-1, solar metallicity  
  > "we adopt the (more conservative) CO–to-molecular gas ratio for Solar metallicity" (Molecular Gas mass from CO emission)
   - fitting: _not stated_
   - validation: lower metallicity would raise alpha_CO by at most ~2  
  > "This implies a higher $\alpha_\mathrm{CO}$ (and higher gas masses) by at most a factor of $\sim$2." (Molecular Gas mass from CO emission)

## Software

- **CASA** 4.5.0-REL: calibration, cleaning, flux fitting  
  > "We reduced the data with CASA (Common Astronomy Software Applications(cite: mcmull07)) version 4.5.0-REL" (ALMA Observations and Data Reduction)
- **FAST** : stellar masses  
  > "we rederived stellar masses and uncertainties using FAST (cite: kriek09b)" (Selection of Milky-Way-Mass Galaxy Progenitors)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(3-2) detection significance | 4.8-13.7 | not stated | sigma | 2 | the detections range in significance from 4.8–13.7$\sigma$ (r.m.s.) |
| I_CO(3-2) | 0.11-0.33 | not stated | Jy km/s | 2 | range from $I_{\mathrm{CO(3-2)}}$=0.11–0.33 Jy km s$^{-1}$ |
| L_IR | (1.5-3.2)e11 | ~0.2 dex | Lsun | 4 | span $\hbox{$L_{\mathrm{IR}}$}$=$(1.5-3.2)$$\times$$10^{11}$ $L_\odot$ |
| gas consumption timescale | 200-700 | not stated | Myr | 5 | which corresponds to a range of 200 to 700 Myr for the galaxies in our sample |

## Qualitative findings

- Gas fractions fgas>~50% in three galaxies; SFE similar to local spirals; CO spectra suggest rotation  
  > "in three of the galaxies in our sample, the molecular gas mass is greater than or equal to the stellar mass" (abstract)

## Claim tuples

- H: Progenitors of Milky Way-mass galaxies at z~1.2 are gas-rich | E: ALMA CO(3-2) of four galaxies, alpha_CO=3.6 | R: Mgas ≳ M* in three galaxies | F: High gas fractions, against early rapid gas consumption models | **supported**
- H: Star-formation efficiency evolved | E: Compare L_IR/L'CO to control samples | R: SFEs typical of upper range of local spirals | F: Similar star-formation physics; mergers not common | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Merger origin of double-peaked lines rejected: no double nuclei in HST and main-sequence SFE  
  > "we consider this unlikely for two reasons." (Velocity Shear in CO Emission)
- How they decided it was enough: _not stated_
- Limitation (authors): Beam size precludes accurate modelling of velocity shear  
  > "While the beam size precludes accurate modelling of the velocity shear" (Velocity Shear in CO Emission)
- Caveat (inferred, ours): Only four galaxies
- Caveat (inferred, ours): alpha_CO and r31 assumed
- Caveat (inferred, ours): L_IR systematic 0.2 dex
- Caveat (inferred, ours): CDFS 467 detection marginal

## Reproducibility

- Data public (paper): ZFOURGE public; other data on request  
  > "are available from the corresponding author upon reasonable request." (Data availability)
- Products in archive: _not stated_
- Missing: Table 1 values
- Missing: clean parameters
- Missing: ZFOURGE v2.1 proprietary IDs
- Data volume (inferred): ~10-30 GB
- Score (inferred): 3/5, Modest data and simple recipe, but imaging details and IR inputs are partly unstated.
- Rediscovery candidate: no, Project code discrepancy and incomplete imaging settings.

## Links

- Method: (cite: stra16) (ZFOURGE catalogues)
- Companion: (cite: papo15) (progenitor selection)
- Related: ZFOURGE
- Related: CANDELS

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.0.01234.S"
 ],
 "obscore_codes_not_in_card": [
  "2013.1.00836.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 42,
  "rate": 0.575
 },
 "evidence_ok": true
}
```

# A 50 pc Scale View of Star Formation Efficiency across NGC 628

`2018ApJ...863L..21K` | The Astrophysical Journal Letters 2018 | first author: Kreckel, K. | arXiv: 1807.11506 | DOI: 10.3847/2041-8213/aad77d

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation
- Question: How does molecular gas depletion time vary with spatial scale (50-500 pc) in NGC 628, and what does GMC/HII region overlap imply about the star formation cycle?  
  > "We catalog and match individual GMCs and H II regions to characterize the overlap phase in the star formation sequence." (1 Introduction)
- Target **NGC 628**: coordinates _not stated_; z/distance 9.6 Mpc  
  > "This galaxy is a nearby ($9.6$ Mpc, (cite: Kreckel2017)) face-on ($i=9^\circ$, (cite: Blanc2013)) type SAc grand-design spiral galaxy" (1 Introduction); distance from Kreckel2017  
  > "This galaxy is a nearby ($9.6$ Mpc, (cite: Kreckel2017)) face-on ($i=9^\circ$, (cite: Blanc2013)) type SAc grand-design spiral galaxy" (1 Introduction)

## Data provenance

- ALMA projects: _none stated_
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12m, 7m and total power  
  > "They include 12m, 7m and total power observations to recover emission on all scales" (2.1 Molecular Gas Tracers)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1'' (47 pc)  
  > "achieve $1\ensuremath{''}$ (47 pc) resolution" (2.1 Molecular Gas Tracers)
- max recoverable scale: _not stated_
- sensitivity: rms 0.15 K over 2.5 km/s; 1 sigma integrated intensity 1.1 K km/s (7.5 Msun/pc^2) over 20 km/s  
  > "reach an rms noise of $0.15$ K over $2.5$ km s$^{-1}$ and ($1\sigma$) sensitivity to the integrated line intensity of $1.1$ K km s$^{-1}$" (2.1 Molecular Gas Tracers)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (not stated)
- Other facility **VLT/MUSE**: Halpha and ionized gas maps at 1'' seeing for SFR and H II regions  
  > "We obtained MUSE observations at $1\ensuremath{''}$ seeing" (2.2 Star Formation Tracers)
- Other facility **Spitzer**: stellar mass surface density model  
  > "The latter is modeled from Spitzer imaging and cleaned of non-stellar emission (cite: Querejeta2015)." (3.3)
- External data: CO(2-1)/(1-0) ratio R21 = 0.61  
  > "We assume a CO (2-1)/(1-0) brightness temperature ratio of R$_{21} = 0.61$ as measured by (cite: Cormier2018)." (2.1 Molecular Gas Tracers) [from (cite: Cormier2018)]
- External data: HERACLES NGC 628 scatter measurements at kpc scales  
  > "we can trace the change in scatter from $50$ pc to $2.4$ kpc scales" (3.1) [from (cite: Leroy2013)]

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

- Data reduction of ALMA and MUSE data  
  > "As the data reduction has been detailed in previous work (cite: Leroy2016; Sun2018; Kreckel2016; Kreckel2017), we provide a brief summary here" (2 Data) [from (cite: Leroy2016; Sun2018; Kreckel2016; Kreckel2017)]
- GMC identification details  
  > "we refer to (cite: Rosolowsky2018) for further details" (2.1 Molecular Gas Tracers) [from (cite: Rosolowsky2018)]
- Method for correlating depletion time with mass-weighted cloud properties  
  > "This methodology (cite: Leroy2016) tests how the mean cloud-scale properties affect the depletion time." (3.3) [from (cite: Leroy2016)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration/imaging parameters
- CPROPS parameters
- Aperture sizes and sampling grid details
- DIG interpolation method
- Model parameters for the Kruijssen curve
- Exact GMC-HII association rules and fitted scatter method

## Analysis recipe

1. **Build maps and catalogs**: CPROPS GMCs from CO; HIIPhot HII regions from extinction-corrected Halpha; DIG subtracted using [SII]/Halpha>0.5  
  > "We leverage the \[S II\]/H$\alpha$ $>$ 0.5 line ratio to identify 10% of the total H$\alpha$ flux" (2.3)
   - software: CPROPS, HIIPhot, LZIFU
   - assumption: alpha_CO(1-0)=4.4 Msun/pc^2 (K km/s)^-1; R21=0.61; SFR=5.37e-42 L(Halpha)  
  > "$\alpha_\mathrm{CO}^{1-0}$ = 4.4 M$_\odot$ pc$^{-2}$ (K km s$^{-1}$)$^{-1}$" (2.1 Molecular Gas Tracers)
   - fitting: _not stated_
   - validation: Balmer decrement correction agrees ~5% with Halpha+24um  
  > "This method shows good ($\sim$5%) systematic agreement at high $\Sigma_\textrm{SFR}$ with a hybrid H$\alpha$+24$\mu$m dust correction" (2.2 Star Formation Tracers)
2. **Depletion time vs scale**: Nyquist-sampled apertures 50-500 pc, S/N>3 in both tracers; medians, scatter and Spearman rho  
  > "Individual data points show the surface density in (Nyquist sampled) apertures detected in both tracers uniformly sampling the emission maps at $\textrm{S/N}>3$." (3.1)
   - fitting: _not stated_
   - validation: compared with Kruijssen & Longmore 2014 model  
  > "The observed trend agrees qualitatively with the predictions of the (cite: Kruijssen2014) model" (3.1)
3. **Cross-match GMCs and HII regions**: Centers matched within 0.5'' (~20 pc); second match sums HII regions within GMC footprint  
  > "we cross-match all GMC and H II region centers (crossmatch tolerance of $0.5\ensuremath{''} \approx 20$ pc) and find $74$ matches" (3.2)
   - fitting: _not stated_
   - validation: by eye >90% look associated  
  > "By eye, ${>}90\%$ of these look like associated objects, and not chance alignments in crowded regions." (3.2)
4. **Drivers of depletion time**: tau_dep at 500 pc correlated with mass-weighted local properties  
  > "We test for such variations by calculating $\tau_\textrm{dep}$ at $500$ pc scales and then correlating this with the local mass-weighted mean properties of the molecular gas." (3.3)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CPROPS** : GMC identification  
  > "$738$ GMCs are identified using CPROPS (cite: Rosolowsky2006)" (2.1 Molecular Gas Tracers)
- **LZIFU** : fit stellar continuum and emission lines in MUSE  
  > "use LZIFU (cite: Ho2016) to simultaneously fit the stellar continuum and emission lines" (2.2 Star Formation Tracers)
- **HIIPhot** : HII region catalog  
  > "We construct a catalog of $1502$ H II regions using HIIPhot (cite: Thilker2000)." (2.2 Star Formation Tracers)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of GMCs | 738 | not stated | count | 1 | $738$ GMCs are identified using CPROPS |
| Number of HII regions | 1502 | not stated | count | 1 | We construct a catalog of $1502$ H II regions |
| Median GMC mass | 5.8e5 | not stated | Msun | 1 | We find median cloud masses of $5.8{\times}10^5$ M$_\ensuremath{\odot}$ |
| Median depletion time | 1-3 | not stated | Gyr | 2 | We measure median gas depletion times of $1{-}3$ Gyr |
| Scatter in depletion time at <300 pc | 0.4 | not stated | dex | 2 | We observe an increased scatter in the depletion time ($\sigma \approx 0.4$ dex) on small (${<}300$ pc) scales |
| Matched GMC-HII pairs | 74 | not stated | count | 3 | find $74$ matches |
| Median cloud-scale depletion time | 3 | not stated | Gyr | 3 | with a median value ($3$ Gyr) slightly longer |
| GMCs with associated SF | 162 | not stated | count | 3 | we find $162$ GMCs with associated star formation |

## Qualitative findings

- No clear correlation of 500 pc depletion time with boundedness, metallicity or other 50 pc properties; central ring has longer depletion times  
  > "however we observe no such correlation in NGC 628" (3.3)

## Claim tuples

- H: Are GMCs and HII regions correlated at cloud scales? | E: Uniform-aperture SF relation at 50-500 pc | R: rho~0.3 below 300 pc; 50-75% of regions detected in one tracer | F: Only a short overlap phase | **supported**
- H: Are cloud-scale depletion times in NGC 628 consistent with Milky Way clouds? | E: Cross-match catalogs | R: Median 3 Gyr, 1-10 Gyr range | F: Longer than MW cloud depletion times | **supported**
- H: Do local 50 pc conditions drive 500 pc depletion time variations? | E: Correlation analysis | R: No strong trends | F: Drivers not identified; larger-scale dynamics may matter | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): SFR may be underestimated by DIG subtraction; GMCs not fully decomposed; diffuse CO not removed  
  > "with the caveat that we could be systematically underestimating the SFR on large scales" (2.3)
- Caveat (inferred, ours): Fixed alpha_CO and DIG treatment affect depletion times
- Caveat (inferred, ours): Single galaxy
- Caveat (inferred, ours): Match tolerance and GMC decomposition affect overlap counts

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA reduction details
- Missing: Catalogs not provided
- Missing: Aperture and statistics specifics
- Data volume (inferred): ~100s GB (12m+7m+TP mosaic, plus MUSE)
- Score (inferred): 3/5, Data public project code given but processing deferred to other papers; recipe brief.
- Rediscovery candidate: no, Processing and catalog details are in companion papers and MUSE data are required.

## Links

- Method: Leroy2016 (data reduction and mass-weighted property method)
- Method: Rosolowsky2018 (GMC catalog)
- Companion: Sun2018 (PHANGS-ALMA)
- Companion: Kreckel2016 (DIG in NGC 628)
- Related: PHANGS-ALMA
- Related: PHANGS-MUSE
- Related: HERACLES

## Checks

```json
{
 "quotes": 39,
 "quotes_ok": 39,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2012.1.00650.S"
 ],
 "codes_printed_but_missing": [
  "2012.0.00650.S"
 ],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 26,
  "rate": 0.382
 },
 "evidence_ok": true
}
```

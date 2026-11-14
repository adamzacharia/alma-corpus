# Dust Emission in an Accretion-rate-limited Sample of z ≳ 6 Quasars

`2018ApJ...866..159V` | The Astrophysical Journal 2018 | first author: Venemans, Bram P. | arXiv: 1809.01662 | DOI: 10.3847/1538-4357/aadf35

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: What are the FIR dust continuum properties of a UV luminosity-limited sample of z>6 quasar hosts, and does FIR luminosity (star formation) correlate with quasar UV luminosity (black hole growth)?  
  > "To obtain a less biased view of the host galaxies of $z>6$ quasars and to investigate how the quasar bolometric and FIR luminosities relate to each other, we targeted a UV luminosity-limited quasar sample" (Introduction)
- Target **27 z~6 quasars (e.g. P007+04, J1048–0109, P183+05)**: coordinates listed per source in Table 1 (e.g. P007+04: 00:28:06.560 +04:57:25.39)  
  > "| P007+04 | 00$^\mathrm{h}$28$^\mathrm{m}$06$.\!\!^\mathrm{s}$560 | +04$^\circ$57$^\prime$25.39$''$ | 6.0008$\pm$0.0004 | \[C II\]  | –26.58 | 1, 2 |" (Table 1); z/distance z = 6.0–6.6 (e.g. 6.0008 for P007+04)  
  > "| P007+04 | 00$^\mathrm{h}$28$^\mathrm{m}$06$.\!\!^\mathrm{s}$560 | +04$^\circ$57$^\prime$25.39$''$ | 6.0008$\pm$0.0004 | \[C II\]  | –26.58 | 1, 2 |" (Table 1); distance from [C II] line, Mg II or template fit to UV spectrum, per Table 1 references  
  > "| P007+04 | 00$^\mathrm{h}$28$^\mathrm{m}$06$.\!\!^\mathrm{s}$560 | +04$^\circ$57$^\prime$25.39$''$ | 6.0008$\pm$0.0004 | \[C II\]  | –26.58 | 1, 2 |" (Table 1)

## Data provenance

- ALMA projects: 2015.1.01115.S
- bands: Band 6 (1.2 mm)  
  > "the \[C II\] 158 $\mu$m emission line is redshifted to the easily accessible 1.2 mm band (ALMA band 6)" (2.1 A Quasar Luminosity-limited Sample)
- frequencies and spectral setup: two partly overlapping 1.875 GHz spectral windows covering redshifted [C II] plus two 1.875 GHz windows at lower frequency for continuum (~16 GHz below the line)  
  > "two (partly overlapping) bandpasses of 1.875 GHz covering the redshifted \[C II\] 158 $\mu$m line and two bandpasses of 1.875 GHz width each targeting the quasar continuum at slightly lower frequencies" (2.2 ALMA Observations and Analysis)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: typical beam ~1.0 arcsec  
  > "The typical beam had a size of $\sim$1.0$''$" (2.2 ALMA Observations and Analysis)
- max recoverable scale: _not stated_
- sensitivity: typical rms 0.5 mJy/beam in 30 km/s bins  
  > "the typical rms noise is 0.5 mJy beam$^{-1}$ in 30 km s$^{-1}$ bins" (2.2 ALMA Observations and Analysis)
- time on source: 8 min per source  
  > "consisted of 8 min on-source integrations" (2.2 ALMA Observations and Analysis)
- observing dates: _not stated_
- pi or archival as stated: PI F. Walter, Cycle 3  
  > "Of these, 27 were observed with ALMA in Cycle 3 (cite: dec18)." (2.1 A Quasar Luminosity-limited Sample)
- Line: [C II] 158 um fine-structure (not stated)
- Other facility **Bolometers, PdBI/NOEMA and other ALMA programs (literature)**: 1 mm photometry of 64 literature z>5.7 quasars  
  > "In total, 64 quasars with mm observations were found in the literature, of which 30 were detected." (2.3 Literature Sample)
- External data: Redshifts and M1450 of the sample quasars  
  > "References for the redshift and $M_{1450}$: (1) (cite: dec18), (2) (cite: ban16)" (Table 1) [from (cite: dec18); (cite: ban16)]
- External data: Literature 1 mm flux densities, redshifts and M1450 of z>5.7 quasars (Table 3)  
  > "From the literature we collected all available observations of high-redshift ($z>5.7$) quasars obtained in the 1 mm band." (2.3 Literature Sample) [from (cite: wan08b); (cite: omo13); (cite: wan13); (cite: ven16) and others]
- External data: Dust mass opacity kappa = 0.77 (nu/352 GHz)^beta cm2/g  
  > "$\kappa_\nu(\beta)=0.77\,(\nu/352\,\mathrm{GHz})^\beta$ cm$^2$ g$^{-1}$ (cite: dun00)" (4.3 Dust Masses) [from (cite: dun00)]
- External data: Arp 220 and M82 templates  
  > "we can fit templates of the local star-forming galaxies Arp 220 and M82 (cite: sil98)" (4.1 FIR Luminosity) [from (cite: sil98)]

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
- line free channels: 1900 GHz map from line-free channels of the two [C II] spectral windows; 1790 GHz map from all channels of the lower-sideband windows; faint sources: all line-free channels of four windows  
  > "One was created by averaging the line-free channels in the two spectral windows targeting the \[C II\] line (cite: dec18)." (2.2 ALMA Observations and Analysis)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Observation details and data reduction  
  > "Further details of the observations and the data reduction can be found in (cite: dec18)." (2.2 ALMA Observations and Analysis) [from (cite: dec18)]
- Dust SED assumption T=47 K, beta=1.6, negligible optical depth  
  > "Following the literature on $z\sim6$ quasars (cite: wan08b; wan13; wil13; ven16), we here assume that the dust spectral energy distribution can be described by a modified blackbody" (4.1 FIR Luminosity) [from (cite: bee06; lei14); (cite: wan08b; wan13; wil13; ven16)]
- Only S/N>10 sources used for size measurement  
  > "Following (cite: dec18), we only regard objects detected at S/N $>10$ as suitable to determine the extent of the emission." (3.1 Continuum emission size) [from (cite: dec18)]
- SFR from TIR luminosity relation  
  > "SFR $=1.48\times10^{-10} L_\mathrm{TIR}/L_\ensuremath{\odot}$ (cite: mur11)" (4.2 SFRs) [from (cite: mur11)]

### Not stated but needed to reproduce (our reading)

- Calibration pipeline, CASA version, calibrators and flux scale uncertainty (deferred to Decarli et al. 2018)
- tclean parameters: weighting/robust, cell size, image size, masking, deconvolver
- Line-free channel selection for each source
- Exact flux conversion from 1900/1790 GHz rest-frame to observed 1 mm used in histograms and Table 3 comparison
- Method for the linear fit and Pearson r (sample set, treatment of upper limits)
- Rest frequency of [C II] and the continuum frequency values per source

## Analysis recipe

1. **make continuum maps**: Average line-free channels in [C II] windows (1900 GHz rest) and all channels in lower sideband windows (1790 GHz rest); for four faint sources average all line-free channels of four windows  
  > "The second map was constructed by averaging all the channels in the spectral windows in the lower sideband" (2.2 ALMA Observations and Analysis)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **measure continuum flux densities and sizes**: Peak pixel within 0.5 arcsec of quasar position; imfit integrated flux if peak S/N>=7, else peak flux  
  > "If the S/N ratio of the peak flux density in one of the continuum maps was at least 7, then the integrated flux densities provided by “imfit” were taken as the brightness of the source" (2.2 ALMA Observations and Analysis)
   - software: CASA imfit
   - parameter: search radius 0.5 arcsec  
  > "the peak flux density in the maps was measured by selecting the brightest pixel within 0.5$''$ of the quasar position" (2.2 ALMA Observations and Analysis)
   - fitting: _not stated_
   - validation: _not stated_
3. **derive FIR luminosity, SFR and dust mass**: Scale modified blackbody to measured flux; integrate 42.5–122.5 um for L_FIR and 3–1100 um for L_TIR; SFR from Murphy relation; dust mass from Eq. 2  
  > "The FIR luminosity, $L_{\mathrm{FIR}}$, is calculated by integrating Equation ([\[eq:sdust\]](#eq:sdust)) between 42.5 and 122.5 $\mu$m in the rest-frame (cite: hel88)." (4.1 FIR Luminosity)
   - assumption: T_dust=47 K, beta=1.6, negligible dust optical depth, Kroupa IMF, all dust heated by star formation  
  > "Assuming $T_\mathrm{dust}=47$ K, $\beta=1.6$ and a negligible dust optical depth at $\nu_\mathrm{rest}=1790$ GHz" (4.3 Dust Masses)
   - fitting: _not stated_
   - validation: Sensitivity to alternative SED parameters (T=55 K, Arp 220/M82 templates, tau=1) quantified  
  > "Scaling the M82 and Arp 220 templates to our measured flux density results in an FIR luminosity that is 38% and 48% lower, respectively." (4.1 FIR Luminosity)
4. **test L_FIR vs UV luminosity correlation**: Pearson correlation and straight-line fit of log L_FIR vs M1450 for all literature+new quasars and for the complete luminosity-limited sample  
  > "Fitting a straight line to the data results in the a correlation with a non-zero slope" (4.4 Correlation between the FIR and UV Luminosity)
   - fitting: _not stated_
   - validation: Restricted to complete sample to check selection bias  
  > "In this complete sample, the correlation is even weaker, with a Pearson’s $r=-0.22$." (4.4 Correlation between the FIR and UV Luminosity)

## Software

- **CASA** : continuum flux/size measurement with imfit  
  > "We also measured the source brightness and extent using the CASA task “imfit.”" (2.2 ALMA Observations and Analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Rest-frame 1900 GHz flux density range | 0.12–5.9 | not stated | mJy | 2 | $0.12<S_\mathrm{rest,\,1900\,GHz}<5.9$ mJy, with a median (mean) flux density of 0.88 mJy (1.59 mJy) |
| FIR luminosity range | (0.27–13)e12 | not stated | Lsun | 3 | $L_{\mathrm{FIR}}$ $=(0.27-13)\times10^{12}$ $L_\ensuremath{\odot}$, with 74% of our quasar hosts having $L_{\mathrm{FIR}}$ $>10^{12}$ $L_\ensuremath{\odot}$ |
| Median L_FIR | 1.8e12 | not stated | Lsun | 3 | with a median value of $L_{\mathrm{FIR}}$ $=1.8\times10^{12}$ $L_\ensuremath{\odot}$ |
| SFR range | 50–2700 | factor ~2–3 | Msun/yr | 3 | we derive SFRs of SFR $=50-2700$ $M_\ensuremath{\odot}$ yr$^{-1}$ |
| Dust mass range | 2e7–1e9 | not stated | Msun | 3 | the estimated dust masses range from $M_\mathrm{dust} \approx 2\times10^7$ $M_\ensuremath{\odot}$ for the faintest sources |
| Pearson r, L_FIR vs M1450 (all) | -0.37 | not stated | dimensionless | 4 | with a Pearson’s $r$ of $r=-0.37$ |
| Pearson r, complete sample | -0.22 | not stated | dimensionless | 4 | the correlation is even weaker, with a Pearson’s $r=-0.22$ |
| Linear fit slope log L_FIR vs (M_UV+26) | -0.18 | 0.04 | dex per mag | 4 | log($L_{\mathrm{FIR}}$) = $(12.41\pm0.05) - (0.18\pm0.04) \times (M_\mathrm{UV} + 26)$ |

## Qualitative findings

- All 27 hosts detected; sources at S/N>10 are unresolved or marginally resolved at ~1 arcsec resolution  
  > "We detect all 27 quasar hosts in the dust continuum (Figure [1](#fig:maps)) at a significance of $\gtrsim3$$\sigma$" (3 Results)

## Claim tuples

- H: Quasar UV luminosity correlates with host FIR luminosity | E: Compare L_FIR with M1450 for new plus literature quasars and the complete sample | R: r=-0.37 overall, r=-0.22 for complete sample | F: No strong correlation; coevolution not ruled out but not supported | **supported**
- H: z~6 quasar hosts are FIR luminous | E: ALMA 1 mm continuum of 27 quasars | R: 74% have L_FIR>1e12 Lsun | F: Most hosts are ULIRG-like | **supported**

## Reasoning

- Why this data: Luminosity-limited sample to give less biased view of hosts  
  > "To obtain a less biased view of the host galaxies of $z>6$ quasars" (Introduction)
- Why this method: _not stated_
- Alternative: Alternative dust SEDs (T=41 K beta=1.95; T=38 K beta=2.0; T=55 K; Arp 220/M82 templates; tau=1) tested for impact on L_FIR  
  > "Using $T_{\mathrm{dust}}$ $=38$ K and $\beta=2.0$ results in an FIR luminosity that is 23% lower" (4.1 FIR Luminosity)
- How they decided it was enough: _not stated_
- Limitation (authors): Derived L_FIR, SFR and dust mass dominated by assumed SED; only Rayleigh-Jeans data so T and beta degenerate  
  > "from our data alone we cannot derive a dust temperature together with the emissivity index, as they are degenerate" (4.1 FIR Luminosity)
- Caveat (inferred, ours): Single-band continuum, so L_FIR is extrapolated from assumed SED
- Caveat (inferred, ours): Pearson r treatment of upper limits in literature sample not described
- Caveat (inferred, ours): Low resolution prevents robust size/SFR density
- Caveat (inferred, ours): Sample selection includes quasar J1152+0055 below luminosity cut

## Reproducibility

- Data public (paper): ALMA program cited with acknowledgement; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.01115.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Calibration details (in Decarli et al. 2018)
- Missing: Table 3 conversion details
- Missing: Fit method details
- Data volume (inferred): ~50-100 GB raw for 27 short snapshots
- Score (inferred): 3/5, Simple measurements and clear SED assumptions with tabulated results, but imaging and calibration settings are deferred to another paper.
- Rediscovery candidate: yes, Data from a single ALMA program, simple continuum flux measurement and analytic derived quantities with tabulated numeric answers.

## Links

- Method: (cite: dec18) (Observation and data reduction details)
- Method: (cite: ven16) (Previous SED and correlation analysis)
- Companion: (cite: dec18) ([C II] properties of the same sample)
- Companion: (cite: dec17) ([C II] companion sources)
- Related: ALMA Cycle 3 z>6 quasar [C II] survey (2015.1.01115.S)

## Checks

```json
{
 "quotes": 47,
 "quotes_ok": 47,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 34,
  "rate": 0.486
 },
 "evidence_ok": true
}
```

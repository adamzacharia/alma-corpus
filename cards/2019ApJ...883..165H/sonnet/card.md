# ALMA Monitoring of Millimeter Line Variation in IRC +10216. I. Overview of Millimeter Variability

`2019ApJ...883..165H` | The Astrophysical Journal 2019 | first author: He, J. H. | arXiv: 1904.07114 | DOI: 10.3847/1538-4357/ab3d37

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, astrochemistry
- Question: How do millimeter molecular lines and continuum in IRC +10216 vary with time relative to NIR light, and what is the overview of line identifications and variability behaviors?  
  > "we present the average spectra and line identification, and give a qualitative presentation of the line variability of all lines identified in the ALMA monitoring program." (Introduction)
- Target **IRC +10216**: coordinates ICRS 09:47:57.4060 +13.16.43.560  
  > "stellar position of IRC +10216 at ICRS 09:47:57.4060 +13.16.43.560" (4.1 Average spectra and line identification); "pulsation period of 630 day ($\sim1.7$ yrs) of the target IRC +10216" (Observations); "the difference in beam radii only corresponds to $\sim1552$ AU at a source distance of 135 pc" (4.3 Millimeter line variations); z/distance 135 pc  
  > "stellar position of IRC +10216 at ICRS 09:47:57.4060 +13.16.43.560" (4.1 Average spectra and line identification); "pulsation period of 630 day ($\sim1.7$ yrs) of the target IRC +10216" (Observations); "the difference in beam radii only corresponds to $\sim1552$ AU at a source distance of 135 pc" (4.3 Millimeter line variations); distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00794.S, 2016.2.00033.S, 2017.1.01689.S, 2018.1.00047.S
- bands: _not stated_
- frequencies and spectral setup: 4 spectral windows of ~1.8 GHz each: 251293-253105, 253594-255406, 265791-267603, 268192-270018 MHz  
  > "There are four spectral windows, with each covering about 1.8 GHz frequency width." (Observations); "about 251293-253105, 253594-255406, 265791-267603 and 268192-270018 MHz" (Observations)
- continuum bandwidth: _not stated_
- arrays: ACA 7-m array, 9-12 antennas  
  > "The array configuration is relatively stable, with 9-12 antennas available during the observations." (Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~4'' x 8'' synthesized beam  
  > "the synthesized beam size and maximum recoverable scale of ACA is $\sim4''\times 8''$ and $28''$, respectively" (Observations)
- max recoverable scale: 28''  
  > "the synthesized beam size and maximum recoverable scale of ACA is $\sim4''\times 8''$ and $28''$, respectively" (Observations)
- sensitivity: typical RMS ~25 mJy/beam (10-75) at ~1 MHz (~1.2 km/s); stacked ~10 mJy/beam per 1 MHz channel  
  > "typical root mean square (RMS) noise of $\sim 25$ mJy/beam ($\sim 10$ to $\sim 75$ mJy/beam) at the effective spectral resolution of $\sim 1$ MHz" (Observations); "deep baseline RMS of $\sim 10$ mJy/beam per 1 MHz channel" (4.1 Average spectra and line identification)
- time on source: ~4 min Cycle 4, ~5 min Cycle 5, ~10 min Cycle 6 per epoch  
  > "The typical on-source integration time was $\sim4$ min in Cycle 4, but increased to $\sim5$ min in Cycle 5 and $\sim10$ min in Cycle 6" (Observations)
- observing dates: 21 epochs, 2016-10-21 to 2019-01-16 (817 days)  
  > "We report the initial results from the first 21 epochs (see the details in Table [1](#tab: epochs)) that cover 817 days" (Observations)
- pi or archival as stated: _not stated_
- Line: SiS 14-13 (v=0-4), 15-14 (254103.211 MHz (v=0 14-13))
- Line: HCN 3-2 (v2=0-3) (265886.18 MHz (ground))
- Other facility **Crimea 1.25 m telescope**: J, H, K, L, M NIR photometric monitoring; K-band used as stellar pulsation indicator  
  > "The NIR photometric monitoring in J, H, K, L and M bands is performed with the Crimea 1.25 m telescope" (Observations)
- External data: Single-dish line variability results for comparison (eight light curves)  
  > "Eight light curves were studied in detail in our single dish work (cite: He2017)" (4.3 Millimeter line variations) [from He et al. 2017 (cite: He2017)]
- External data: Pulsation period 630 d  
  > "pulsation period of 630 day ($\sim1.7$ yrs) of the target IRC +10216 (cite: Ment12)" (Observations) [from (cite: Ment12)]

## Processing

### Calibration

- pipeline or manual: ALMA staff default pipeline calibration, no extra calibration  
  > "We use data calibrated by ALMA staff using default pipelines." (3 Data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1058+0133 in most cases; J0854+2006 gain calibrator  
  > "The latter also serves as the flux calibrator in most cases." (Observations)
- flux scale uncertainty: 8% adopted  
  > "which is several per cent in ALMA Band 6 (we can adopt $8\%$)" (3 Data reduction)
- self calibration: not applied  
  > "the data presented in this paper has no any additional calibration aside from the standard processing in ALMA pipelines." (3 Data reduction)

### Imaging

- task: tclean per single channel, concatenated with ia.imageconcat; CASA 5.3.0-143  
  > "we utilize the *tclean* to each individual channel to produce single channel clean maps and then concatenate" (3 Data reduction)
- deconvolver: hogbom  
  > "The *hogbom* deconvolver and *briggs* weighting (with parameter robust=0.5) are used." (3 Data reduction)
- weighting robust: briggs, robust=0.5  
  > "The *hogbom* deconvolver and *briggs* weighting (with parameter robust=0.5) are used." (3 Data reduction)
- uv taper: _not stated_
- cell size: 1.2''  
  > "The pixel size is set to $1.2''$" (3 Data reduction)
- image size: 60'' x 60''  
  > "A map of $60''\times 60''$ ($\sim1.4$ times of the primary beam) is produced" (3 Data reduction)
- masking: primary beam mask pbmask=0.2; threshold 5 sigma iterated until sigma converges  
  > "we only adopt the primary beam masking at a level of *pbmask=0.2*" (3 Data reduction); "The flux threshold for the major cycles of *tclean* is set to $5\,\sigma$ level." (3 Data reduction)
- multiscale scales: _not stated_
- continuum subtraction: linear baseline fit per line group in image domain  
  > "Finally, a linear baseline is fit to the continuum channels of each line group and subtracted at each epoch." (4.3 Millimeter line variations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: imsmooth to 29'' round Gaussian for comparison with single dish  
  > "smoothed (using *imsmooth*) by a large round Gaussian beam of $29''$" (4.2 Sample light curves)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- NIR photometry data reduction  
  > "a detailed description of the data reduction can be found in (cite: Shen11)" (3 Data reduction) [from (cite: Shen11)]
- in-band calibration approach (deferred)  
  > "it is possible to apply the so-called 'in-band calibration' approach" (4.3 Millimeter line variations) [from (cite: He2017)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for each of 125 line groups
- Exact velocity limits for SiS integrated light curve
- Which 5 of 16 maximum-phase epochs were selected (only marked in a figure)
- Cell/threshold details of the clean loop convergence criteria
- ALMA pipeline version
- Whether all four projects' data are all used for the same 21 epochs per project mapping

## Analysis recipe

1. **image each channel**: Per-channel tclean with iterated 5 sigma threshold, concatenated into cubes  
  > "we repeatedly measure $\sigma$ from the residual map after a standard *tclean* procedure has finished and use a loop over *clean* to achieve the convergence of $\sigma$ for each channel." (3 Data reduction)
   - software: CASA
   - parameter: robust=0.5, hogbom, 1.2'' pixels, pbmask=0.2  
  > "The pixel size is set to $1.2''$" (3 Data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **extract spectra and identify lines**: Spectra averaged over central 2.4''x2.4'' and over 21 epochs; lines identified via CASSIS groups with LTE strengths  
  > "averaged among the pixels in the central $2.4''\times2.4''$ square region" (4.1 Average spectra and line identification)
   - software: CASSIS
   - assumption: LTE line strengths for consistency check  
  > "consistency of identified line carriers are examined according to the predicted local thermal equilibrium (LTE) line strengths in CASSIS" (4.1 Average spectra and line identification)
   - fitting: _not stated_
   - validation: Cross-check with splatalogue, CDMS, JPL  
  > "are referenced to confirm the transitions and quantum number assignments" (4.1 Average spectra and line identification)
3. **continuum and SiS light curves**: Power-law fit F_nu=F_nu0(nu/nu0)^beta to line-free channels per epoch, nu0=260655 MHz; integrate SiS 14-13  
  > "fit by a single power law function $F_\nu=F_{\nu_0}(\nu/\nu_0)^\beta$ with $\nu_0$=260655 MHz for each epoch" (4.2 Sample light curves)
   - assumption: 8% flux calibration uncertainty  
  > "which we take as $8\%$ here" (4.2 Sample light curves)
   - fitting: _not stated_
   - validation: Compared with K-band NIR light curve  
  > "all three observed light curves roughly agree to each other" (4.2 Sample light curves)
4. **max/min phase line profile comparison**: Linear baseline per 125 line groups; average 5 min-phase and 5 max-phase epochs split at 2410 Jy/beam km/s; classify by eye  
  > "The 16 epochs above this line is averaged together to make the maximum-phase line profiles, while the 5 epochs below the line make the minimum-phase line profiles." (4.3 Millimeter line variations)
   - parameter: variation identified if >5-10% of peak in at least ~1/3 of channels  
  > "a profile variation is identified only when it occurs in at least about $1/3$ channels of a line profile" (4.3 Millimeter line variations)
   - fitting: _not stated_
   - validation: Averaging reduces 8% calibration uncertainty to ~2%, 3.6%, 2.5%  
  > "can reduce it to about 2%, 3.6%, 2.5%, respectively" (4.3 Millimeter line variations)

## Software

- **CASA** 5.3.0-143: imaging (tclean, imsmooth, ia.imageconcat)  
  > "Common Astronomy Software Applications (CASA 5.3.0-143) package" (3 Data reduction)
- **CASSIS** 5.0: line identification  
  > "CASSIS, version 5.0, with line list database cassis20161026.db" (4.1 Average spectra and line identification)
- **analysisUtils** : extracting mean JD with lstrange  
  > "extracted from the calibrated measurement set using the *lstrange* function of the Python module *analysisUtils*" (Table 1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Observation span | 817 | not stated | days | 0 | cover 817 days |
| Transitions detected | 148 transitions of 20 molecules; 81 unidentified lines | not stated | count | 2 | detect about 148 known transitions of 20 molecules |
| Continuum vs SiS discrepancy | up to ~12% | not stated | percent | 3 | The discrepancies between the 1.1 mm continuum and the SiS line amount up to about $12\%$ |
| SiS double peak velocity offset | ±8.5 | not stated | km/s | 3 | two peaks at velocity shifts of around $\pm8.5$ km s$^{-1}$ |
| Line groups | 125 | not stated | count | 4 | In total, 125 such line groups are defined in our data. |

## Qualitative findings

- Most strong lines vary in phase with NIR light; some vibrational-state lines and many U-lines anti-correlate; several ground-state lines stable  
  > "most strong lines vary roughly in-phase with the NIR light and mm continuum" (Summary)
- No Eup distinction between varying and stable lines, disfavoring collisional excitation  
  > "there is no distinction in $E_{\rm up}$ values between the varying and stable lines" (4.3 Millimeter line variations)

## Claim tuples

- H: Do ACA line variations match single-dish results? | E: Compare ACA max/min profiles with He et al. 2017 light curves | R: Anti-correlations seen in single dish are not seen in ACA; in-phase ones agree | F: Differences relate to beam size, missing flux and an unknown CSE mechanism | **partially**
- H: Is variation driven by collisional excitation? | E: Compare Eup of varying and stable lines | R: No Eup distinction | F: Collisional excitation not responsible | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: ACA chosen as baselines change little with time  
  > "because its interferometric baselines do not change with time drastically" (Observations)
- Alternative: Radial phase delay from radiation transport rejected (~9 day lag)  
  > "radial phase delay due to radiation transportation is unlikely" (4.3 Millimeter line variations)
- How they decided it was enough: _not stated_
- Limitation (authors): Qualitative only; flux uncertainties not rigorously constrained; C4H lines show negative artifacts; missing extended flux  
  > "we mainly report qualitative results of our monitoring in this first report" (3 Data reduction)
- Caveat (inferred, ours): Classification by eye with no uncertainties
- Caveat (inferred, ours): Epoch selection for max-phase average is arbitrary
- Caveat (inferred, ours): Missing flux and sidelobes could mimic variations

## Reproducibility

- Data public (paper): ALMA data acknowledged by project codes; public status not explicitly stated  
  > "This paper makes use of the following ALMA data" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Line-free channel lists
- Missing: Selected epochs for average
- Missing: Line group definitions
- Data volume (inferred): ~20-50 GB (21 ACA epochs, 4 windows)
- Score (inferred): 3/5, Imaging recipe is detailed but classification is by eye and several choices unstated.
- Rediscovery candidate: no, Results are mostly qualitative.

## Links

- Method: He et al. 2017 (cite: He2017) (single dish monitoring and in-band calibration)
- Method: Shenavrin et al. 2011 (cite: Shen11) (NIR photometry reduction)
- Companion: Cernicharo et al. 2014 (cite: Cern2014) (Herschel variability and IR excitation model)
- Companion: Pardo et al. 2018 (cite: Pard2018) (IRAM 30m monitoring)
- Related: IRAM 30m monitoring of IRC +10216

## Checks

```json
{
 "quotes": 68,
 "quotes_ok": 68,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 47,
  "rate": 0.662
 },
 "evidence_ok": true
}
```

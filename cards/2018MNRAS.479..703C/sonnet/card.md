# Merger-driven star formation activity in Cl J1449+0856 at z = 1.99 as seen by ALMA and JVLA

`2018MNRAS.479..703C` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Coogan, R. T. | arXiv: 1805.09789 | DOI: 10.1093/mnras/sty1446

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, galaxy_clusters_and_sz
- Question: How are dust-obscured star formation, molecular gas content/excitation and AGN activity linked to environment and mergers in the z=1.99 cluster Cl J1449+0856?  
  > "We measure the gas excitation properties, star-formation rates, gas consumption timescales and gas-to-stellar mass ratios for the galaxies." (abstract)
- Target **Cl J1449+0856**: coordinates _not stated_; z/distance z=1.99  
  > "Cl J1449+0856 at z=1.99 (cite: ref:R.Gobat2011)" (1 Introduction); distance from Gobat et al. 2011 (spectroscopic)  
  > "Cl J1449+0856 at z=1.99 (cite: ref:R.Gobat2011)" (1 Introduction)

## Data provenance

- ALMA projects: 2015.1.01355.S, 2012.1.00885.S
- bands: ALMA Band 3, 4, 7; JVLA Ka and S band  
  > "The ALMA band 4 and band 3 observations covered the expected frequency of the CO[4-3] and CO[3-2] lines respectively, and the JVLA Ka-band data targeted the CO[1-0] line." (2 Observations and data reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Band 4 core beam 1.19"x0.96"; Band 3 1.36"x1.31"; Band 7 1.41"x0.62"  
  > "the synthesised beam was 1.19"$\times$0.96" at a position angle (PA) of -44.8." (2.1 ALMA Band 4 Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: Band 4 core ~2h; Band 3 ~2h; Band 7 ~2.3h; JVLA Ka 15.5h  
  > "for a total on-source time of $\sim$2h in the core, and $\sim$30 minutes in the outskirts." (2.1 ALMA Band 4 Observations)
- observing dates: Band 7 Dec 2014; Band 3 Jun 2015; Band 4 May 2016  
  > "| ALMA | Core, single | June 2015 | 107.9 | 7.5 | 2.0 | 1.36$\times$1.31 | -5.8 |" (Table 1)
- pi or archival as stated: _not stated_
- Line: 12CO J=4-3 (not stated)
- Line: 12CO J=3-2 (not stated)
- Line: 12CO J=1-0 (JVLA) (not stated)
- Other facility **JVLA**: Ka-band CO(1-0) and 3 GHz continuum  
  > "Deep high frequency data of Cl J1449+0856 was taken using the Karl G. Jansky Very Large Array (JVLA)" (2.3 JVLA Ka-band Observations)
- Other facility **HST/WFC3**: rest-frame optical positions of cluster members  
  > "for spectroscopically confirmed cluster members with HST/WFC3 counterparts, the signals in the submillimetre maps are consistent with the rest-frame optical positions" (2.5 Spectral flux extraction)
- External data: Stellar masses from FAST SED fitting  
  > "in order to derive the galaxy stellar masses shown in Table [\[tab:SFRs\]](#tab:SFRs), as described in (cite: ref:V.Strazzullo2016)" (3.6 Specific star-formation rates) [from (cite: ref:V.Strazzullo2016)]
- External data: Optical redshifts  
  > "with offsets between $\sim$20-400kms$^{-1}$(cite: ref:R.Gobat2013; ref:F.Valentino2015)" (3.1.2 CO Line fluxes) [from (cite: ref:R.Gobat2013; ref:F.Valentino2015)]
- External data: CO SLED templates (BzK, ULIRG/SB, MW)  
  > "known SLEDs: ‘normal’ z$\sim$2 star-forming galaxies (BzK), ULIRG/starburst galaxies, and the Milky Way (MW) (cite: ref:P.Papadoupolos2012; ref:E.Daddi2015)" (3.2 CO Spectral Line Energy Distributions) [from (cite: ref:P.Papadoupolos2012; ref:E.Daddi2015)]
- External data: SED templates for 870um/radio to LIR conversion  
  > "taking the average 870$\ensuremath{\mu}m$ to L$_{IR}$ conversion factor between the MS and SB templates in (cite: ref:M.Bethermin2015) at z=2" (3.3 Star-formation rates) [from (cite: ref:M.Bethermin2015)]
- Simulation/model as data: Draine & Li 2007 two-component dust models used to derive dust masses  
  > "We modelled the data using 2-component dust models from (cite: ref:DraineLi2007), and calculated the goodness-of-fit of each combination of parameters." (3.7.1 Dust masses)

## Processing

### Calibration

- pipeline or manual: Standard pipeline for ALMA and JVLA Ka; JVLA S-band C-config manual  
  > "The ALMA band 4, band 3, band 7, and JVLA Ka-band data were calibrated using the standard reduction pipeline in Common Astronomy Software Applications (CASA" (2.4 JVLA S-band Observations)
- casa version: Band 3/7: 4.2.2; Band 4: 4.5.3; JVLA Ka: 4.4.0; S-band C-config 4.6.0  
  > "For the band 3 and 7 observations, CASA version 4.2.2 was used for reduction. For band 4, version 4.5.3 was used." (2.4 JVLA S-band Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1550+0527 (Band 4 core), Titan (Band 3, Band 4 outskirts), J1337-1257 (Band 7), J1331+3030 (JVLA)  
  > "For the core pointing, quasar J1550+0527 was used for flux calibration" (2.1 ALMA Band 4 Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN, mfs continuum  
  > "the CASA routine `CLEAN` was used. This was performed for continuum mode=‘mfs’ with natural weighting to maximise sensitivity" (2.6 Continuum flux extraction)
- deconvolver: _not stated_
- weighting robust: natural; 3 GHz Briggs robust=0.0  
  > "except for the 3 GHz data for which Briggs robust=0.0 weighting was used" (2.6 Continuum flux extraction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum from line-free channels, a*nu^b with b=3.5, subtracted from line flux  
  > "extrapolated to the frequency under the line using a fixed spectral slope $b=3.5$. This was then subtracted from the measured line flux." (2.5 Spectral flux extraction)
- line free channels: _not stated_
- primary beam correction: Fluxes corrected for primary beam attenuation  
  > "All measured fluxes were then corrected for primary beam attenuation." (2.5 Spectral flux extraction)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: Band 4 continuum 7.98 uJy/beam; Band 3 8.36; Band 7 67.5; Ka 3.30  
  > "the continuum root-mean-squared (RMS) noise was 7.98$\mu$Jy/beam." (2.1 ALMA Band 4 Observations)

### Inherited from earlier work

- Stellar-mass SED fitting procedure and photometry  
  > "following the same procedure detailed in (cite: ref:V.Strazzullo2016)" (3.6 Specific star-formation rates) [from (cite: ref:V.Strazzullo2016)]
- Dynamical mass relation  
  > "We use the following relation from (cite: ref:E.Daddi2010a):" (3.5 Dynamical masses of A1 and A2) [from (cite: ref:E.Daddi2010a)]
- Using same extraction size for all CO transitions  
  > "This approach was also taken by (cite: ref:E.Daddi2015)." (2.5 Spectral flux extraction) [from (cite: ref:E.Daddi2015)]

### Not stated but needed to reproduce (our reading)

- Line-search algorithm details
- Exact uvfit settings and channel ranges for line-free continuum
- Polynomial coefficients of flux de-boosting fit
- CO(5-4) to LIR and SFR conversion coefficients
- Dust model grid details for Draine&Li fits
- Calibrated measurement sets or self-calibration not described

## Analysis recipe

1. **Extract CO line and continuum fluxes**: GILDAS uvfit directly on uv-visibilities at fixed optical positions, iterative source removal; GALFIT on dirty images for 870um and 3 GHz  
  > "This process was repeated iteratively until all of the sources had been modelled and then removed from the data." (Spectral flux extraction)
   - software: GILDAS uvfit, GALFIT, CASA
   - parameter: Detection at fixed position SNR>3.5; free-position SNR>5  
  > "At these fixed positions, we impose a limit of SNR$>$3.5 on the extracted CO[4-3] line fluxes." (3.1 Molecular gas detections)
   - fitting: _not stated_
   - validation: Simulated source injection (1000 per size) comparing uvfit and GALFIT; blind extraction for spurious detections  
  > "This was repeated 1000 times per size." (2.6 Continuum flux extraction)
2. **Correct CO(4-3) flux boosting**: Simulated double-Gaussian lines with noise, ratio of real/measured flux fit with y=ax^b vs SNR  
  > "We then fit this binned data with a polynomial function of the form $y = ax^{b}$." (3.1.3 CO[4-3] flux boosting)
   - fitting: _not stated_
   - validation: Correction independent of linewidth; 6±6% clipping loss  
  > "We therefore consider the loss between the measured and intrinsic line fluxes to be 6$\pm$6%." (3.1.3 CO[4-3] flux boosting)
3. **Classify gas excitation via SLED templates**: Least-squares fit of BzK and ULIRG/SB templates with free normalisation  
  > "Least-squared fitting was used to compare the data to the templates, where the normalisation of each template was allowed to vary." (3.2 CO Spectral Line Energy Distributions)
   - fitting: chi-squared least squares  
  > "Least-squared fitting was used to compare the data to the templates, where the normalisation of each template was allowed to vary." (CO Spectral Line Energy Distributions)
   - validation: _not stated_
4. **Derive SFRs**: CO(4-3) to CO(5-4) via template ratio then LIR; 870um and 3 GHz to LIR via Bethermin templates; average of CO and 870um SFR  
  > "In the remaining analyses, we therefore use the average of the SFRs from CO[4-3] and 870$\mu$m tracers as our preferred SFR." (3.3 Star-formation rates)
   - assumption: Synchrotron slope nu^-0.8; z=2 for unidentified sources; Chabrier IMF  
  > "we assume a synchrotron contribution to the radio data with a slope of $\nu^{-0.8}$" (3.3 Star-formation rates)
   - fitting: _not stated_
   - validation: Compare SFR tracers; 0.2 dex and 0.15 dex systematics included  
  > "We include in our error budget $\sim$0.2 dex for the CO[5-4] vs. L$_{IR}$ conversion" (3.3 Star-formation rates)
5. **Dynamical masses of A1 and A2**: M=1.3 re (vFWHM/2)^2/(G sin^2 i) with CO(4-3) size; half stellar, half gas  
  > "we take the average inclination angle of 57$\pm$21$\degree$, from statistical averages of randomly orientated galaxies." (3.5 Dynamical masses of A1 and A2)
   - assumption: Negligible dark matter; gas:stellar 1:1  
  > "We assume that the contribution from dark matter is negligible." (3.5 Dynamical masses of A1 and A2)
   - fitting: _not stated_
   - validation: _not stated_
6. **Dust masses**: RJ-tail template normalisation and Draine&Li models with <U>=10-50, gamma<0.2; median at <U>=28.75  
  > "We therefore take the median M$_{d}$ of the data binned in this range, at $<$U$>$=28.75." (3.7.1 Dust masses)
   - fitting: least-squares  
  > "the best-fitting normalisation of the template to the data was calculated using a least-squares fitting procedure." (Dust masses)
   - validation: Cross-check with dust-to-870um flux ratio  
  > "we recover the same values for dust mass as we found using our original method." (3.7.1 Dust masses)
7. **Gas masses and depletion times**: FMR metallicity then alpha_CO (Sargent 2014) and G/D (Remy-Ruyer 2014); gas from dust; tau=Mgas/SFR  
  > "We then use the frameworks given by (cite: ref:M.Sargent2014) and (cite: ref:A.RemyRuyer2014) to derive $\alpha_{\rm CO}$ values and G/D ratios respectively." (3.7.2 Molecular gas masses)
   - assumption: Atomic H negligible; constant SFR, no replenishment  
  > "have assumed a constant SFR with no replenishment of the cold gas reservoir." (4.3 Depletion timescales and gas fractions)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2.2, 4.4.0, 4.5.3, 4.6.0: calibration and CLEAN imaging  
  > "CASA version 4.2.2 was used for reduction." (2.4 JVLA S-band Observations)
- **GILDAS (uvfit)** : uv-plane flux extraction  
  > "extracted using the Gildas[^2] tool `uvfit` directly on the uv-visibility data." (2.5 Spectral flux extraction)
- **GALFIT** : image-plane flux extraction at 870um and 3 GHz  
  > "the software GALFIT (cite: ref:C.Peng2010) was used on the dirty, calibrated image." (2.6 Continuum flux extraction)
- **FAST** : SED fitting stellar masses  
  > "SED fitting with Fitting and Assessment of Synthetic Templates (FAST) (cite: ref:M.Kriek2009)" (3.6 Specific star-formation rates)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Galaxies with CO(4-3) detection | 8 (7 secure + S7 tentative) | not stated | galaxies | 1 | We detect molecular gas in eight cluster galaxies |
| Fraction with starburst-like excitation | 50% | not stated | percent | 3 | it is immediately striking that 50% of these galaxies show a starburst-like, rapid star-formation mode |
| Median SFE offset from MS in SFR-L'CO(1-0) | 0.37 | not stated | dex | 4 | The median offset of the cluster galaxies from the MS locus is 0.37 dex. |
| SFR fraction from mergers/interactions | ~75% | not stated | percent | 4 | we find that $\sim$75% of the total SFR in the cluster core comes from mergers and interactions alone. |
| Gas depletion timescales | <400 Myr (~100-400 Myr) | not stated | Myr | 7 | We find that all of our cluster galaxies have relatively short depletion timescales, $<$400 Myrs |
| alpha_CO of A1 | 3.6 | not stated | K km/s pc^2 / Msun ^-1 | 7 | / A1 / 3.6$^{*}$ / 44$^{*}$ / |

## Qualitative findings

- Cluster core is dominated by mergers, interactions and AGN with enhanced gas excitation and star-formation efficiency but not elevated sSFR  
  > "Interestingly, we do not see evidence for increased specific star-formation rates (sSFRs) in the cluster galaxies, despite their high SFEs and gas excitations." (abstract)

## Claim tuples

- H: Environment enhances the fraction of highly excited molecular gas galaxies | E: Build CO SLEDs from CO(4-3), (3-2), (1-0) and compare to field expectations | R: 50% starburst-like vs ~6% in field 2-SFM | F: Excited fraction strongly enhanced in cluster core | **supported**
- H: Cluster galaxies have high SFE and short gas depletion times | E: SFR vs L'CO(1-0) and dust-based gas masses | R: Offset 0.37-0.4 dex; tau<400 Myr | F: Higher SFE than field MS galaxies | **supported**
- H: Mergers drive the star formation in the core | E: Classify galaxies and sum SFR | R: ~75% of core SFR from mergers/interactions | F: Mergers drive excitation and SFR | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Conversion factors calibrated on disk-like MS galaxies; comparison with field samples not direct  
  > "It is important to note that these frameworks were calibrated on disk-like MS galaxies, and the galaxies in our sample are therefore likely to deviate from these relations." (3.7.2)
- Caveat (inferred, ours): Small sample of 8 galaxies
- Caveat (inferred, ours): FMR-based alpha_CO and G/D uncertain for mergers
- Caveat (inferred, ours): CO(4-3) selection biased toward high SFR
- Caveat (inferred, ours): Dust temperature unconstrained by short-wavelength data

## Reproducibility

- Data public (paper): Acknowledges ALMA project data; archive public  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00885.S and ADS/JAO.ALMA#2015.1.01355.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Line-search algorithm
- Missing: Flux de-boosting fit coefficients
- Missing: CO-to-LIR conversion details
- Missing: JVLA data processing details
- Data volume (inferred): ~100-300 GB across ALMA and JVLA
- Score (inferred): 3/5, Data public and methods described in prose, but algorithms and several conversion parameters unspecified and JVLA data needed.
- Rediscovery candidate: no, Multiple custom algorithms, JVLA data and external templates make a full redo incomplete.

## Links

- Method: (cite: ref:E.Daddi2015) (CO SLED templates and CO(5-4)-LIR relation)
- Method: (cite: ref:M.Bethermin2015) (SED templates for LIR conversion)
- Companion: (cite: ref:V.Strazzullo2017) (Companion paper on same dataset)
- Companion: (cite: ref:V.Strazzullo2016) (Stellar masses and passive population)
- Related: JVLA 12A-188

## Checks

```json
{
 "quotes": 64,
 "quotes_ok": 64,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 84,
  "stated": 49,
  "rate": 0.583
 },
 "evidence_ok": true
}
```

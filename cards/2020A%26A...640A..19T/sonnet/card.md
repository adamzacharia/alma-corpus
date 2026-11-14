# Dust masses of young disks: constraining the initial solid reservoir for planet formation

`2020A&A...640A..19T` | Astronomy and Astrophysics 2020 | first author: Tychoniec, Łukasz | arXiv: 2006.02812 | DOI: 10.1051/0004-6361/202037851

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks, exoplanets
- Question: Do embedded Class 0/I disks in Perseus contain enough dust to explain the solid content of the most massive exoplanets, and what efficiency is needed?  
  > "We aim to determine if disks in the embedded stage of star formation contain enough dust to explain the solid content of the most massive exoplanets." (abstract)
- Target **Perseus Class 0/I protostars (77 ALMA disks)**: coordinates _not stated_; z/distance 293±22 pc  
  > "The average spatial resolution of observations ($0.38\ensuremath{''}$) corresponds to 110 au (diameter) at the distance to Perseus (293$\pm 22$ pc; (cite: Ortiz-Leon2018))." (Observations); distance from Ortiz-Leon2018  
  > "The average spatial resolution of observations ($0.38\ensuremath{''}$) corresponds to 110 au (diameter) at the distance to Perseus (293$\pm 22$ pc; (cite: Ortiz-Leon2018))." (Observations)

## Data provenance

- ALMA projects: 2017.1.01693.S, 2017.1.01078.S, 2015.1.00041.S, 2013.1.00031.S
- bands: Band 6 (1.1 mm, 1.3 mm)  
  > "The continuum bandwidth was $\sim 1.85\,$GHz centered at 267.99 GHz (1.1 mm)." (Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: ~1.85 GHz at 267.99 GHz (44 sources); 2 GHz at 233.51 GHz (8 sources)  
  > "The continuum bandwidth was centered at 233.51 GHz (1.3 mm) with a total bandwidth of 2 GHz." (Observations)
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.45"x0.30" natural weighting (1.1 mm); 0.41"x0.28" (1.3 mm)  
  > "The synthesized beam of the continuum observations in natural weighting is $0.45\ensuremath{''} \times 0.30\ensuremath{''}$." (Observations)
- max recoverable scale: _not stated_
- sensitivity: rms ~0.1 mJy/beam (1.1 mm); ~0.05 mJy/beam (1.3 mm)  
  > "The typical rms value of the continuum images is $\sim$ 0.1 mJy beam$^{-1}$." (Observations)
- time on source: _not stated_
- observing dates: September 2018 (2017.1.01693.S)  
  > "The data were obtained in September 2018 with a Cycle 5 program" (Observations)
- pi or archival as stated: _not stated_
- Other facility **VLA (VANDAM)**: 9.1 mm Ka-band fluxes, free-free corrected, for Class 0/I protostars  
  > "Fluxes at 9.1 mm (Ka-band), obtained with 0.25$''$ resolution from 100 Class 0 and I disks (including upper limits) were reported in (cite: Tobin2016)." (Observations)
- External data: 1.3 mm flux densities of 25 Perseus disks  
  > "We also use the flux densities of 25 disks published in (cite: Tobin2018) which were observed at 1.3 mm" (Observations) [from Tobin2018]
- External data: VLA 9 mm fluxes corrected for free-free emission  
  > "We use the 9 mm fluxes corrected for the free-free emission for further analysis." (Observations) [from Tobin2016; Tychoniec2018]
- External data: Orion ALMA Band 7 disk fluxes/masses  
  > "In Fig. [3](#fig:cdplots_per_ori) we show the cumulative distribution of disks observed with ALMA for Orion (cite: Tobin2020) and for Perseus." (ALMA Class 0/I disk masses for different star-forming regions) [from Tobin2020]
- External data: Exoplanet masses (2074 planets, updated 28.04.2020)  
  > "The exoplanet systems masses were obtained from the exoplanet.eu database (cite: Schneider2011)." (Exoplanet sample selection) [from Schneider2011]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0237+2848 (2017.1.01693.S); J0510+1800 (2017.1.01078.S)  
  > "The absolute flux and bandpass calibrator was J0237+2848, and the phase calibrator was J0336+3218." (Observations)
- flux scale uncertainty: ~30% (1.1 mm), ~10% (1.3 mm)  
  > "The absolute flux calibration uncertainty is on the order of $\sim$ 30%." (Observations)
- self calibration: 2017.1.01078.S data self-calibrated  
  > "The measurement sets were self-calibrated and cleaned with the robust parameter 0.5." (Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust = 0.5 (2017.1.01078.S data); natural weighting for 1.1 mm beam  
  > "The measurement sets were self-calibrated and cleaned with the robust parameter 0.5." (Observations)
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

- Continuum images of 2017.1.01693.S presented in earlier paper  
  > "Continuum images and spectral lines observed in this project are presented in (cite: Hsieh2019)." (Observations) [from Hsieh2019]
- Free-free correction and upper-limit criteria (alpha << 2) for VLA fluxes  
  > "all sources with a Ka-band spectral index suggestive of emission not coming from dust ($\alpha \ll 2$) were marked as upper limits, and we use the same criteria here." (Observations) [from Tychoniec2018]
- kappa_1.3mm = 2.3 cm2/g adopted for ALMA masses  
  > "we use $\kappa_{\rm 1.3\ mm} = 2.3$ cm$^{2}$ g${^{-1}}$ as used in the determination of masses in (cite: Ansdell2016)." (Disk mass measurements) [from Ansdell2016]
- Solid-content formula for gas giants  
  > "we calculate the solid content in exoplanets using the formula from (cite: Thorngren2016) for estimating the solid content in gaseous planets." (Exoplanet sample selection) [from Thorngren2016]

### Not stated but needed to reproduce (our reading)

- Which sources use which ALMA project and the exact tabulated disk fluxes (table not in text)
- Calibration pipeline vs manual and CASA version used for calibration
- tclean parameters (deconvolver, cell, image size, masks) for continuum images
- Initial guess details/thresholds for deciding the envelope component
- How uncertainties on fluxes and medians were derived
- Exact Thorngren2016 formula implementation and exoplanet filtering details for efficiency
- Selection of Lupus Class II comparison data and Gaia distances

## Analysis recipe

1. **measure disk fluxes with Gaussian fits**: imfit with compact Gaussian plus optional broad 3" envelope Gaussian; compact component taken as disk  
  > "The CASA (cite: McMullin2007) v. 5.4.0 $\it imfit$ task was used to fit Gaussian profiles to the sources." (Gaussian fitting)
   - software: CASA imfit
   - parameter: Envelope Gaussian added in 31 of 51 targets; initial broad size 3"  
  > "an additional broad Gaussian with a size of 3$''$ was added to the initial guess parameters of the fitting" (Gaussian fitting)
   - assumption: Compact Gaussian flux equals disk flux  
  > "The flux density of the compact Gaussian is assumed to be that of the embedded disk." (Gaussian fitting)
   - fitting: all Gaussian parameters free; size fixed to beam in two sources  
  > "In two cases (Per-emb-4 and SVS13A2) it was necessary to fix the size of the Gaussian to the synthesized beam size for the fit to converge" (Gaussian fitting)
   - validation: Residual envelope flux measured in residual images; inspected by eye  
  > "All sources were inspected by eye to assess the number of necessary Gaussian components." (Gaussian fitting)
2. **compare ALMA and VLA fluxes and derive spectral index and beta**: Linear fit of fluxes with lmfit; alpha between 1 mm and 9 mm; beta = (alpha-2)(1+Delta); optically thin subsample where alpha_VLA/ALMA - alpha_VLA <= 0.4  
  > "There is a clear correlation with a close-to-linear slope (1.15 $\pm$ 0.10) obtained with the *lmfit* Python function." (Comparison of the integrated fluxes between 1 and 9 mm)
   - software: lmfit
   - assumption: Optically thin: Delta = 0  
  > "in which case $\Delta$ = 0 and then $\beta = \alpha - 2$." (Comparison of the integrated fluxes between 1 and 9 mm)
   - fitting: _not stated_
   - validation: Optical depth estimated from deconvolved major axis: tau < 0.4  
  > "For all the disks with available major axis value, we get $\tau < 0.4$ and in vast majortiy of cases $<0.1$." (Comparison of the integrated fluxes between 1 and 9 mm)
3. **compute dust masses and CDFs**: M = D^2 F / (kappa B(T)), T=30 K; CDFs with survival analysis including upper limits; medians at 0.5 probability  
  > "Temperature of the dust is set to 30 K, typical for dust in dense protostellar envelopes (cite: Whitney2003), and disks are assumed to be isothermal." (Disk mass measurements)
   - software: lifelines
   - parameter: kappa_9mm = 0.28 cm2/g (DIANA); kappa_1.3mm = 2.3 cm2/g; for Orion comparison kappa_1.3mm = 0.9  
  > "Here we adopt $\kappa_{9 {\rm mm}}= 0.28 \ {\rm cm^{2}\ g^{-1}}$ as provided by dust models of the DIANA project" (Disk mass measurements)
   - assumption: Distance 293 pc; optically thin emission  
  > "$\kappa_\nu$ is the dust opacity with the assumption of optically thin emission." (Disk mass measurements)
   - fitting: _not stated_
   - validation: VLA sample complete, ALMA ~80% complete so VLA medians more reliable  
  > "While the VLA observations sample is complete, the ALMA sample of disks is not, as we assemble $\sim 80\%$ of the total sample." (Disk mass measurements)
4. **compare to exoplanet solids and derive formation efficiency**: Exoplanet systems (>=1 planet >0.3 MJ) normalized to 18% of population; solid mass via Thorngren2016; efficiency = ratio of exoplanet to disk dust mass at same CDF level  
  > "The efficiency is calculated as a ratio of the total mass of the exoplanetary systems at the certain fraction of the cumulative distribution plot divided by the corresponding dust mass of the disk at the same value of the CDF plot." (Comparison of young disk dust masses with the solids in exoplanetary systems)
   - parameter: 0.3 MJ planet solid fraction 27.8 Mearth set at 18% of CDF  
  > "This is done by setting the 18% value of the CDF plot at the estimated solid fraction of the gaseous planet of 0.3 M$_{\rm J}$, which is 27.8 M$_{\oplus}$." (Exoplanet sample selection)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.4.0: imfit Gaussian fitting  
  > "The CASA (cite: McMullin2007) v. 5.4.0 $\it imfit$ task was used to fit Gaussian profiles to the sources." (Gaussian fitting)
- **lmfit** : linear fit of ALMA vs VLA fluxes  
  > "obtained with the *lmfit* Python function" (Comparison of the integrated fluxes between 1 and 9 mm)
- **lifelines** 0.11.1: survival-analysis CDFs including upper limits  
  > "The CDF plot is prepared using the survival analysis with the *lifelines* package for Python (cite: DavidsonPilon2017)." (Disk mass measurements)
- **Astropy** : general analysis  
  > "This research made use of Astropy, a community-developed core Python package for Astronomy" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Slope of ALMA vs VLA flux correlation | 1.15 | 0.10 | dimensionless | 2 | close-to-linear slope (1.15 $\pm$ 0.10) |
| Mean spectral index of optically thin subsample (23 sources) | 2.5 | not stated | dimensionless | 2 | The mean spectral index of those sources is 2.5, which means that $\beta \sim 0.5$. |
| Median dust mass from VLA, Class 0 / Class I | 158 / 52 | not stated | Earth masses | 3 | The median masses measured from the 9 mm observations are 158 M${_\oplus}$ for Class 0 and 52 M${_\oplus}$ for Class I |
| Median dust mass lower limits from ALMA, Class 0 / Class I | 47 / 12 | not stated | Earth masses | 3 | is 47 M${_\oplus}$ and 12 M${_\oplus}$ for Class 0 and Class I disks, respectively |
| Median Perseus vs Orion dust mass (kappa=0.9, 30 K), Class 0 | 131 vs 67 | not stated | Earth masses | 3 | 67 M$_\oplus$ versus 131 M$_\oplus$ in Perseus, but is remarkably similar for Class I: 25 M$_\oplus$ versus 33 M$_\oplus$. |
| Planet formation efficiency from VLA masses, Class 0 / Class I | ~15% / 34% | not stated | percent | 4 | the efficiency of planet formation would have to be on the order of 15% for Class 0 and 34% for Class I |
| Efficiency from ALMA lower-limit masses, Class 0 / Class I | 33% / 72% | not stated | percent | 4 | the efficiency of forming planets in the Class 0 phase would be on the order of 33%. The efficiency of the Class I phase would be on the order of 72%. |

## Qualitative findings

- Class 0 disks are more massive in Perseus than in Orion; Class I similar  
  > "while disk masses in Class I disks agree well, Class 0 disks are more massive in Perseus than in Orion." (Conclusions)

## Claim tuples

- H: Emission at 1 mm and 9 mm is dust-dominated and indicates grain growth | E: Compared ALMA and VLA fluxes and spectral indices | R: Slope 1.15±0.10; alpha~2.5 for optically thin subsample, beta~0.5 | F: Dust emission dominates both; significant grain growth | **supported**
- H: Young disks hold more dust than Class II disks | E: Computed medians and compared with Lupus | R: Class 0 and I masses higher by at least factors 10 and 3 | F: Embedded disks are more massive | **supported**
- H: Embedded disks contain enough solids to form observed giant exoplanets | E: Compared disk mass CDF with exoplanet solid mass CDF | R: Efficiency ~15% (Class 0), ~30% (Class I) | F: Planet formation can start in Class 0/I with acceptable efficiency | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: VLA and ALMA in same region allow direct comparison and test of wavelength dependence  
  > "The way forward is to use observations of young disks with VLA and ALMA in the same star-forming region" (Introduction)
- Alternative: Ophiuchus sample excluded from further analysis due to incompleteness and contamination  
  > "For this reason, we will not include it in the further analysis." (ALMA Class 0/I disk masses for different star-forming regions)
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA sample ~80% complete; disks mostly unresolved; opacity uncertain  
  > "The other limitation is that we analyze mostly unresolved disks, hence the radial dust distribution in the disk is unknown." (Exoplanetary systems and young disks - a comparison of their solid content)
- Caveat (inferred, ours): Single temperature 30 K for all disks strongly affects masses
- Caveat (inferred, ours): Opacity choice drives order-of-magnitude uncertainty
- Caveat (inferred, ours): Exoplanet sample biased to RV-detected massive planets and normalized by assumed 18% occurrence
- Caveat (inferred, ours): Optically thick 1 mm emission not excluded

## Reproducibility

- Data public (paper): ALMA project codes listed; VLA data from published VANDAM  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.01693.S, ADS/JAO.ALMA#2017.1.01078.S" (Acknowledgements)
- Products in archive: _not stated_
- Missing: Flux table not in text
- Missing: Imaging parameters
- Missing: Exact exoplanet processing
- Data volume (inferred): ~50-150 GB for four ALMA projects
- Score (inferred): 3/5, Public data and clear recipe, but imaging details and tabulated fluxes missing and exoplanet step loosely specified.
- Rediscovery candidate: yes, Public data, mostly simple flux fits and mass formula with numeric medians.

## Links

- Method: Tychoniec2018a (VLA 9 mm Perseus dust masses and free-free correction)
- Method: Thorngren2016 (solid content of giant planets)
- Companion: Hsieh2019 (presents continuum images of 2017.1.01693.S)
- Companion: Tobin2020 (Orion ALMA survey compared)
- Related: VANDAM
- Related: Perseus ALMA programs

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 1,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 44,
  "rate": 0.571
 },
 "evidence_ok": true
}
```

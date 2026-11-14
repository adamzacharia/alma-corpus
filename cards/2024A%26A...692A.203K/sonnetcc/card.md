# PKS 1424−418: A persistent candidate source of the mm─γ-ray connection?

`2024A&A...692A.203K` | Astronomy and Astrophysics 2024 | first author: Kim, Dae-Won | arXiv: 2411.19737 | DOI: 10.1051/0004-6361/202451773

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: agn_and_quasars
- Question: Is there a long-term correlation between mm (ALMA) and gamma-ray (Fermi-LAT) light curves of the FSRQ PKS 1424-418, with what time lag, and what does the mm spectral index say about jet opacity and the gamma-ray site  
  > "We confirm a unique long-lasting mm–$\gamma$-ray correlation of by using detailed correlation analyses and statistical tests, and we find its physical meaning in the source." (abstract); "We did not find any notable time delay within the uncertainties for the mm–$\gamma$-ray correlation, which means zero lag." (abstract)
- Target **PKS 1424-418**: coordinates RA = 216.987 deg, DEC = -42.106 deg (J2000)  
  > "RA = 216.987$^{\circ}$, DEC = $-$42.106$^{\circ}$; J2000" (2.1 gamma-ray data); "At $z$ = 1.52, the luminosity distance of is $\sim$11192 Mpc, and this corresponds to an image scale of 8.54 pc/mas." (4.3 Potential effects of a core shift to the gamma-ray origin); z/distance z = 1.52; luminosity distance ~11192 Mpc; 8.54 pc/mas  
  > "RA = 216.987$^{\circ}$, DEC = $-$42.106$^{\circ}$; J2000" (2.1 gamma-ray data); "At $z$ = 1.52, the luminosity distance of is $\sim$11192 Mpc, and this corresponds to an image scale of 8.54 pc/mas." (4.3 Potential effects of a core shift to the gamma-ray origin); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00001.CAL
- bands: Band 3, Band 6, Band 7  
  > "We obtained three ALMA millimeter (mm) radio light curves of at band 3, band 6, and band 7" (2.2 Millimeter-wave data)
- frequencies and spectral setup: Band 3 ~91 GHz and ~103 GHz (95 GHz used as representative); Band 6 ~235 GHz; Band 7 ~345 GHz  
  > "two central frequencies: $\sim$91 GHz and $\sim$103 GHz. We used all these measurements and consider 95 GHz as a representative observing frequency of band 3 in this study." (2.2 Millimeter-wave data); "the central frequencies of $\sim$235 GHz and $\sim$345 GHz, respectively" (2.2 Millimeter-wave data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: September 2011 to March 2020 (~8.5 yr)  
  > "we considered ALMA data spanning $\sim$8.5 yr from September 2011 to March 2020" (2.2 Millimeter-wave data)
- pi or archival as stated: ALMA calibrator catalog data (archival monitoring flux densities)  
  > "We made use of the Atacama Large Millimeter/submillimeter Array (ALMA) calibrator catalog data" (2.2 Millimeter-wave data)
- Other facility **Fermi-LAT**: Pass 8 gamma-ray data, 0.1-200 GeV, used to build the gamma-ray light curve  
  > "We analyzed the Pass 8 $\gamma$-ray data obtained from the *Fermi*-LAT (cite: atwood2009)." (2.1 gamma-ray data); "We analyzed $\gamma$-rays from the source in the 0.1–200 GeV energy range" (2.1 gamma-ray data)
- External data: 4FGL catalog sources and their default spectral models, used for the LAT background model  
  > "4FGL-catalog sources (cite: abdollahi2020; ballet2023) present within 20$^{\circ}$" (2.1 gamma-ray data); "We kept the default spectral models provided by the catalog for all the sources except our target" (2.1 gamma-ray data) [from (cite: abdollahi2020; ballet2023)]
- External data: Details of the ALMA calibrator catalog and its observations  
  > "Details of the catalog and ALMA observations can be found in (cite: bonato2018)." (2.2 Millimeter-wave data) [from (cite: bonato2018)]
- External data: Apparent jet speed beta_app = 9 (median for FSRQs)  
  > "a median value for FSRQs; (cite: weaver2022)" (4.3 Potential effects of a core shift to the gamma-ray origin) [from (cite: weaver2022)]
- External data: Jet viewing angle range 1-3 deg  
  > "$\theta_{\rm jet}$ = 1–3$^{\circ}$ (cite: paliya2018; weaver2022)" (4.3 Potential effects of a core shift to the gamma-ray origin) [from (cite: paliya2018; weaver2022)]
- Simulation/model as data: 100,000 artificial gamma-ray light curves simulated from fitted PSD and PDF models, used to set LCCF confidence levels  
  > "We simulated 100,000 artificial $\gamma$-ray light curves and computed LCCF curves between those simulated $\gamma$-rays and the observed ALMA band 3 light curve." (Cross-correlation analysis)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: ALMA calibrator catalog flux densities used directly; no calibration of raw data described  
  > "We made use of the Atacama Large Millimeter/submillimeter Array (ALMA) calibrator catalog data" (2.2 Millimeter-wave data)
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

- ALMA calibrator catalog and observation details taken from earlier paper  
  > "Details of the catalog and ALMA observations can be found in (cite: bonato2018)." (2.2 Millimeter-wave data) [from (cite: bonato2018)]
- Gamma-ray analysis follows the standard Fermi-LAT unbinned likelihood procedure  
  > "Overall, we followed the standard unbinned likelihood procedure" (2.1 gamma-ray data) [from Fermi Science Support Center analysis threads (https://fermi.gsfc.nasa.gov/ssc/data/analysis/scitools/)]
- LCCF confidence-level procedure follows earlier work  
  > "The overall procedure is similar to the manner of (cite: kim2022)." (Cross-correlation analysis) [from (cite: kim2022)]
- Artificial gamma-ray light curves generated with the Emmanoulopoulos et al. algorithm  
  > "were generated in the manner of (cite: emma2013)" (Cross-correlation analysis) [from (cite: emma2013)]
- Local cross-correlation function method  
  > "the local cross-correlation function (cite: welsh1999)" (3 Results) [from (cite: welsh1999)]

### Not stated but needed to reproduce (our reading)

- Exact query or extraction date of the ALMA calibrator catalogue and any flagging or quality cuts applied to its flux densities
- Flux-scale uncertainty and per-point flux errors of the catalogue measurements, and how they enter the correlations
- Fermi Science Tools or fermipy version and the 4FGL release used (the paper cites two 4FGL references)
- Which source in the ROI was the variable one and the exact fit settings per time bin
- Full list of the Bin_eq grid steps and bin edges used for the 488 Pearson calculations
- How delay-bin uncertainties and LCCF confidence curves were computed in practice (random seeds, number of delay bins)
- Fitting algorithm and weighting for the Gaussian fits to the LCCF humps
- Light-curve tables themselves (gamma-ray and ALMA flux values) are not given

## Analysis recipe

1. **Build 6-day gamma-ray light curve from Fermi-LAT**: Standard Fermi-LAT unbinned likelihood analysis of Pass 8 data in 6-day bins, power-law model for the target, two fits per bin with faint sources removed  
  > "Overall, we followed the standard unbinned likelihood procedure" (2.1 gamma-ray data); "we generated a $\gamma$-ray light curve with a binning interval of 6 days" (2.1 gamma-ray data)
   - software: Fermi-LAT unbinned likelihood analysis
   - parameter: ROI radius 10 deg; 4FGL sources within 20 deg included  
  > "We set a region of interest (ROI) to be a circle of radius 10$^{\circ}$ centered at the position of" (2.1 gamma-ray data)
   - parameter: Energy 0.1-200 GeV, 4 Sep 2011 to 26 Mar 2020 (MJD 55808-58934)  
  > "We analyzed $\gamma$-rays from the source in the 0.1–200 GeV energy range measured between 4 September 2011 and 26 March 2020 (MJD: 55808–58934)" (2.1 gamma-ray data)
   - parameter: SOURCE class evclass=128, FRONT+BACK evtype=3, zmax 90 deg  
  > "We selected SOURCE class (`evclass=128`) and FRONT$+$BACK-type (`evtype=3`) events." (2.1 gamma-ray data); "The maximum zenith angle (zmax) was set to be 90$^{\circ}$" (2.1 gamma-ray data)
   - parameter: Background: gll_iem_v07 and iso_P8R3_SOURCE_V3_v1  
  > "Two background components, `gll_iem_v07` and `iso_P8R3_SOURCE_V3_v1`, were employed" (2.1 gamma-ray data)
   - parameter: Upper limits for TS < 20 or dF/F >= 0.5; faint sources with TS < 9 removed before second fit  
  > "We computed 2 $\sigma$ upper limits for the $\gamma$-rays with TS $<$ 20 or $\Delta F_{\gamma}/F_{\gamma}$ $\geq$ 0.5" (2.1 gamma-ray data); "Then, all the faint sources with TS $<$ 9 ($\sim$3 $\sigma$) were removed from the background model." (2.1 gamma-ray data)
   - assumption: Simple power law for the target; no significant difference from LogParabola  
  > "a simple power law was applied to the target (see below)" (2.1 gamma-ray data); "there are no significant differences in the results between the two models" (2.1 gamma-ray data)
   - fitting: Maximum likelihood test statistic (TS); spectral parameters free within 5 deg of ROI center, normalizations only for 5-10 deg  
  > "We employed the maximum likelihood test statistics (TS) to evaluate the significance of the $\gamma$-ray photons." (2.1 gamma-ray data); "we left the spectral parameters free for all sources within 5$^{\circ}$ of the ROI center" (2.1 gamma-ray data)
   - validation: Two analyses with different fit tolerance; the set with higher TS or lower dF/F kept  
  > "we carried out two sets of the analysis: one set with Tol $\sim$ 0.01, and the other set with Tol $\sim$ 0.00001." (2.1 gamma-ray data)
2. **Assemble ALMA band 3, 6 and 7 light curves**: Take flux densities from the ALMA calibrator catalogue; average multiple measurements at the same timestamp; treat 91 and 103 GHz as 95 GHz band 3  
  > "When multiple flux density measurements were available at the same timestamp, we used their average." (2.2 Millimeter-wave data); "We used all these measurements and consider 95 GHz as a representative observing frequency of band 3 in this study." (2.2 Millimeter-wave data)
   - parameter: Band 3 median sampling interval 6 days (average ~10 days)  
  > "The median sampling interval is 6 days, with an average of $\sim$10 days" (2.2 Millimeter-wave data)
   - fitting: _not stated_
   - validation: _not stated_
3. **Pearson correlation between mm and gamma-ray light curves**: Divide the full time range into equal-sized bins, average flux in each bin, correlate local means over overlapping bins; repeat over many bin sizes  
  > "We calculated an average of all the flux densities belonging to each of the Bin$_{\rm eq}$ and used it as a typical flux density for each of them." (Appendix Testing Pearson correlation); "this test was repeated in a range of different sizes of Bin$_{\rm eq}$" (Appendix Testing Pearson correlation)
   - parameter: 488 calculations with Bin_eq from 6 to 100 days  
  > "Bin$_{\rm eq}$ (i.e., the equal-sized time bin) varies with the 488 calculations from 6 days to 100 days." (3.1 Linear relations)
   - fitting: _not stated_
   - validation: All coefficients highly significant (p-values << 0.01)  
  > "all the r$_{\rm P}$ values are highly significant" (3.1 Linear relations)
4. **Search for time delay with the LCCF and assess significance**: Local cross-correlation function with 6-day delay bins between band 3 and gamma-ray light curves; confidence levels from 100,000 simulated gamma-ray light curves  
  > "The binning interval ($\Delta t$) was set to be 6 days to match the basic samplings of the band 3 and $\gamma$-ray data" (3.2 Cross-correlation); "For every $\tau$, we draw a cumulative distribution function (CDF) of the correlation coefficients and find the 68%, 95%, and 99.9% confidence levels." (Appendix Cross-correlation analysis)
   - software: DELCgen
   - parameter: Also tested delay bins of 12, 30 and 60 days  
  > "with larger $\Delta t$ values (i.e., 12, 30, and 60 days)" (Appendix Tests on the LCCF curves)
   - assumption: Gamma-ray PSD as bending power law and PDF as gamma plus log-normal mixture; empty bins filled by linear interpolation  
  > "A bending power-law model and the mixture model (i.e., a combination of the gamma and log-normal distributions) introduced by (cite: emma2013), were applied to a periodogram and histogram of the data, respectively." (Appendix Cross-correlation analysis); "Using linear interpolation, we complemented these bins and thus made the light curve evenly distributed." (Appendix Cross-correlation analysis)
   - fitting: PSD and PDF model parameters fitted to interpolated gamma-ray light curve (values in a footnote)  
  > "Figure [8](#fig:gpsdpdf) shows the best-fit PSD and PDF models." (Appendix Cross-correlation analysis)
   - validation: LCCF compared with DCF; LCCF peak closer to mean Pearson coefficient  
  > "we find that the peak of the LCCF curve is much closer to the mean of the Pearson coefficients" (Appendix Cross-correlation analysis)
5. **Compute (sub)mm spectral index between band 3 and band 7**: Spectral index alpha from binned band 3 (95 GHz) and band 7 (345 GHz) flux densities, uncertainty by error propagation  
  > "we also calculated the spectral index ($\alpha$) between the band 3 and 7 flux densities" (3.3 Evolution of the (sub)mm wave spectral index); "We estimated the uncertainty of $\alpha$ following the error propagation." (1 Introduction)
   - parameter: Bin_eq from 3 to 30 days (NBin_eq 1038 to 105)  
  > "Bin$_{\rm eq}$ ranged from 3 days to 30 days, which corresponds to NBin$_{\rm eq}$ sliding from 1038 to 105" (3.3 Evolution of the (sub)mm wave spectral index)
   - assumption: alpha ~ -0.5 is the boundary between optically thick and thin  
  > "We considered $\alpha$ $\sim$ $-$0.5 as a reference point of the transition between optically thick" (3.3 Evolution of the (sub)mm wave spectral index)
   - fitting: _not stated_
   - validation: Very small bins (1-2 days) tested with consistent overall trend  
  > "We also tested very small Bins$_{\rm eq}$ that varied from from one day to two days." (3.3 Evolution of the (sub)mm wave spectral index)
6. **Estimate LCCF peak lags with Gaussian fits for bands 3 and 7**: Fit a single Gaussian to the central LCCF hump, using only points above the first side-lobe peak (LCCF ~0.48); delta t = 8 days for band 7  
  > "we fit a single Gaussian to the LCCF curve between the LAT and ALMA band 7 light curves" (Appendix Gaussian fit to the LCCF curves); "we only used the LCCF points higher than the peak of a first strong, distinct side-lobe (i.e., LCCF = $\sim$0.48)" (Appendix Gaussian fit to the LCCF curves)
   - parameter: Delta t = 8 days (median band 7 sampling)  
  > "$\Delta t$ was set to be 8 days that is the median sampling of the band 7 light curve." (Appendix Gaussian fit to the LCCF curves)
   - fitting: _not stated_
   - validation: Gaussian model describes both curves well; results independent of bin size  
  > "We note that the Gaussian model well describes both the LCCF curves shown above, and the results are irrelevant to the bin size ($\Delta t$)." (Appendix Gaussian fit to the LCCF curves)
7. **Convert lags into deprojected distance between mm core and gamma-ray site**: Distance from apparent jet speed, lag, viewing angle and redshift: delta d = beta_app c tau / (sin theta_jet (1+z))  
  > "This indicates that the $\gamma$-ray production site is located in a region upstream of the 95 GHz core by about 0.16–0.48 pc" (4.3 Potential effects of a core shift to the gamma-ray origin)
   - parameter: beta_app = 9; theta_jet = 1-3 deg  
  > "Assuming $\beta_{\rm app}$ = 9 (i.e., a median value for FSRQs; (cite: weaver2022))" (4.3 Potential effects of a core shift to the gamma-ray origin); "$\theta_{\rm jet}$ = 1–3$^{\circ}$ (cite: paliya2018; weaver2022)" (4.3 Potential effects of a core shift to the gamma-ray origin)
   - assumption: Higher beta_app gives a larger distance range (0.71-2.14 pc)  
  > "the distance range for the same $\theta_{\rm jet}$ = 1–3$^{\circ}$ can be $\Delta d_{\rm \gamma-B3}$ $\sim$ 0.71–2.14 pc" (4.3 Potential effects of a core shift to the gamma-ray origin)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **DELCgen** : Generate artificial gamma-ray light curves following Emmanoulopoulos et al.  
  > "generated with a Python implementation `DELCgen` (cite: conoly2015)" (Appendix Cross-correlation analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean Pearson coefficient, band 3 vs gamma-ray (488 bin sizes) | 0.76 | 1 sigma 0.02 (min 0.71, max 0.86) | dimensionless | 3 | The r$_{\rm P}$ values are $\sim$0.76 on average, with a 1 $\sigma$ uncertainty of 0.02 (minimum and maximum of 0.71 and 0.86, respectively). |
| LCCF peak value band 3 vs gamma-ray at tau = 0 | ~0.75 | lag uncertainty +/-3 days | dimensionless | 4 | Only the top part of this central LCCF hump where it peaks at $\tau$ = 0 with LCCF $\sim$ 0.75, exceeds the confidence level of 99.9%.; with an uncertainty of $\pm$3 days from $\tau$ = 0 |
| Mean band 3 to band 7 spectral index | -0.57 | 1 sigma 0.08 (range -0.78 to -0.19) | dimensionless | 5 | The average of the $\alpha$ values is $-$0.57 (with 1 $\sigma$ of 0.08), and they range from a minimum of $-$0.78 to a maximum of $-$0.19. |
| Gaussian-fit LCCF lag, gamma-ray vs band 3 | -2.8 | 2.0 | days | 6 | The fits estimate $\tau_{\rm \gamma-B3}$ = $-$2.8$\pm$2.0 days and $\tau_{\rm \gamma-B7}$ = $-$0.8$\pm$2.6 days. |
| Gaussian-fit LCCF lag, gamma-ray vs band 7 | -0.8 | 2.6 | days | 6 | The fits estimate $\tau_{\rm \gamma-B3}$ = $-$2.8$\pm$2.0 days and $\tau_{\rm \gamma-B7}$ = $-$0.8$\pm$2.6 days. |
| Mean Pearson coefficient between ALMA bands (B3-B7, B3-B6, B7-B6) | 0.967, 0.987, 0.988 | 0.004, 0.002, 0.005 (1 sigma) | dimensionless | 3 | 0.967$\pm$0.004 (with 1 $\sigma$ uncertainty) for B3–B7, 0.987$\pm$0.002 for B3–B6, and 0.988$\pm$0.005 for B7–B6 |
| Mean band 3 flux density at 95 GHz | ~3 | 1 sigma of 1 Jy | Jy | 2 | The band 3 flux densities are $\sim$3 Jansky (Jy) on average at 95 GHz with 1 $\sigma$ of 1 Jy. |
| Distance of gamma-ray site upstream of 95 GHz core (beta_app = 9, theta_jet 1-3 deg) | 0.16-0.48 | not stated | pc | 7 | This indicates that the $\gamma$-ray production site is located in a region upstream of the 95 GHz core by about 0.16–0.48 pc |
| Distance between 345 GHz core and gamma-ray site (if tau = 0.8 day is a real shift) | ~0.05-0.14 | not stated | pc | 7 | $\Delta d_{\rm \gamma-B7}$ $\sim$ 0.05–0.14 pc |
| Core shift between 95 GHz and 345 GHz cores | ~1.8 | not stated | microarcsec | 7 | the level of the core shift between the 95 GHz and 345 GHz cores is $\sim$1.8 $\mu$as |

## Qualitative findings

- The alpha becomes flatter (>= -0.5) when the source flares in gamma-rays, indicating temporary opacity changes  
  > "we found that $\alpha$ becomes flatter (i.e., $\geq$ $-$0.5) when the $\gamma$-rays flare." (3.3 Evolution of the (sub)mm wave spectral index)
- Gamma-ray emission appears to originate in the (sub)mm radio core region  
  > "This suggests that the $\gamma$-ray emission almost always originates in the (sub)mm wave radio core region" (Summary)

## Claim tuples

- H: Is there a significant long-term correlation between mm and gamma-ray emission in PKS 1424-418 | E: Pearson correlation of binned ALMA band 3 and Fermi-LAT light curves over 8.5 yr | R: 488 Pearson coefficients averaging 0.76, all with p << 0.01 | F: A strong, significant mm-gamma-ray correlation holds over the whole period | **supported**
- H: Is there a time delay between mm and gamma-ray emission | E: LCCF between band 3 and gamma-ray light curves with simulated confidence levels | R: LCCF peaks at tau = 0 with ~0.75, above 99.9% level | F: The emission is contemporaneous within about 3 days (zero lag) | **supported**
- H: Does the (sub)mm opacity change during gamma-ray flares | E: Band 3 to band 7 spectral index in binned light curves compared with gamma-ray flares by visual inspection | R: Mean alpha -0.57, flatter than -0.5 during gamma-ray flares | F: Source opacity at (sub)mm wavelengths is time variable and rises during strong gamma-ray flares | **partially**
- H: Is the gamma-ray site displaced from the 95 GHz and 345 GHz cores | E: Gaussian fits to the LCCF peaks for band 3 and band 7 and conversion of lags into distances | R: tau(B3) = -2.8 +/- 2.0 days, tau(B7) = -0.8 +/- 2.6 days; site 0.16-0.48 pc upstream of the 95 GHz core | F: Gamma-rays are nearly simultaneous with band 7 but precede band 3 by a few days, consistent with a small core shift | **partially**

## Reasoning

- Why this data: Band 3 had the best cadence, so analyses focus on it with the LAT data  
  > "Since band 3 had a higher cadence than the other two radio bands, our analyses were more focused on the data from this band together with the LAT $\gamma$-ray data." (2.2 Millimeter-wave data)
- Why this method: LCCF chosen over DCF because its peak is closer to the mean Pearson coefficient  
  > "Thus, we consider that LCCF is a more accurate way to search for time-correlation in this study." (Appendix Cross-correlation analysis)
- Alternative: LogParabola spectral model not used; power law selected for short bins  
  > "we selected the power-law model assuming that it is more suitable for these short day-scale bins" (2.1 gamma-ray data)
- Alternative: DCF rejected in favor of LCCF to avoid normalization issues  
  > "To avoid the normalization issues of DCF (cite: maxm2014b), however, we employed the Local Cross-Correlation Function (cite: welsh1999) in this work." (Appendix Cross-correlation analysis)
- Alternative: Band 6 skipped in LCCF and spectral-index analysis because of poor sampling  
  > "Owing to the poor sampling of the band 6, we skip the band 6 data in the LCCF analysis" (Appendix Gaussian fit to the LCCF curves)
- How they decided it was enough: _not stated_
- Limitation (authors): Early radio data (before 2014) are sparsely sampled, making alpha less robust there  
  > "Owing to this, the $\alpha$ values in this early part might be less robust, and care must therefore be taken in this time range." (3.3 Evolution of the (sub)mm wave spectral index)
- Limitation (authors): Fast gamma-ray flares (hours to minutes) would be missed by the light curve  
  > "there might be hidden fast $\gamma$-ray flares (i.e., short-term events on a scale of hours to minutes) that cannot be seen in our $\gamma$-ray light curve." (3.3 Evolution of the (sub)mm wave spectral index)
- Limitation (authors): Results reflect the long-term global trend; other gamma-ray events may deviate  
  > "there might be other $\gamma$-ray events in the source that deviate from our conclusion" (Summary)
- Caveat (inferred, ours): Spectral-index flattening during flares is judged by visual inspection, with no statistical test
- Caveat (inferred, ours): Lag uncertainties of 2-3 days are comparable to the 6-day bin, so the 0.16-0.48 pc offset rests on weak evidence
- Caveat (inferred, ours): Pearson coefficients from overlapping bin sizes are not independent, so the quoted scatter does not reflect statistical significance
- Caveat (inferred, ours): Correlation among sparsely and unevenly sampled red-noise light curves is sensitive to the PSD model, which has large parameter uncertainties
- Caveat (inferred, ours): Calibrator-catalogue flux densities mix measurements at different frequencies and epochs, with no stated error treatment
- Caveat (inferred, ours): Distance estimate depends on assumed beta_app and viewing angle

## Reproducibility

- Data public (paper): ALMA calibrator catalogue is a public web page  
  > "https://almascience.eso.org/alma-data/calibrator-catalogue" (Footnote 3)
- Products in archive: Data cited as ADS/JAO.ALMA#2011.0.00001.CAL  
  > "ADS/JAO.ALMA#2011.0.00001.CAL" (Acknowledgements)
- Missing: Catalogue extraction date, filtering and the exact flux tables used
- Missing: Fermi Science Tools version, 4FGL release and ROI model file
- Missing: Binning grids and random seeds for the Pearson and LCCF simulations
- Missing: Light-curve tables not published
- Data volume (inferred): Small: ALMA calibrator-catalogue flux table (~1000 points, kB) plus ~8.5 yr of Fermi-LAT events in a 10 deg ROI (order of a GB)
- Score (inferred): 3/5, Both data sets are public and the correlation, LCCF and spectral-index recipes are clearly described with numeric results, but software versions, catalogue selection, bin edges and fit details are missing.
- Rediscovery candidate: yes, Public ALMA calibrator-catalogue and Fermi-LAT data, a mostly complete recipe, and numeric results (r_P ~0.76, LCCF peak ~0.75 at zero lag, mean alpha -0.57) that can be re-derived.

## Links

- Method: (cite: bonato2018) (Describes the ALMA calibrator catalogue and its observations)
- Method: (cite: welsh1999) (Defines the local cross-correlation function)
- Method: (cite: emma2013) (Algorithm for simulating artificial light curves with given PSD and PDF)
- Method: (cite: maxm2014b) (Compares DCF and LCCF and defines uncertainty estimation)
- Companion: (cite: kim2022) (Similar LCCF confidence-level procedure applied to another blazar)
- Companion: (cite: benke2024) (VLBI image of the jet of PKS 1424-418)
- Related: ALMA calibrator catalogue
- Related: Fermi-LAT 4FGL catalog

## Checks

```json
{
 "quotes": 97,
 "quotes_ok": 97,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.0.00001.CAL"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 99,
  "stated": 61,
  "rate": 0.616
 },
 "evidence_ok": true
}
```

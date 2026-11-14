# Weak CS emission in an extremely metal-poor galaxy DDO 70

`2020MNRAS.496L..38D` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Du, Kaiyi | arXiv: 2005.03907 | DOI: 10.1093/mnrasl/slaa086

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, astrochemistry, star_formation
- Question: Does dense molecular gas, traced by CS J=5-4, exist in the extremely metal-poor galaxy DDO 70, and how does it relate to IR luminosity and SFR?  
  > "However, it is unclear if dense molecular gas exists at very low metallicity, and if exists, how it is related to star formation." (abstract)
- Target **DDO 70**: coordinates _not stated_; z/distance 1.38 Mpc; z = 0.001004  
  > "This galaxy is at a distance of 1.38 Mpc (cite: Tully2013) and a redshift of 0.001004 (cite: Springob2005)." (Data); distance from Tully2013 (distance); Springob2005 (redshift)  
  > "This galaxy is at a distance of 1.38 Mpc (cite: Tully2013) and a redshift of 0.001004 (cite: Springob2005)." (Data)

## Data provenance

- ALMA projects: 2016.1.00359.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: C40-4 and C40-7  
  > "with the C40-4 and C40-7 array configurations at their best angular resolutions of 0.10$''$ and 0.35$''$, respectively." (Data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.10'' (C40-4) and 0.35'' (C40-7) best resolutions of the two configurations; final synthesized beam 0.22'' x 0.19''  
  > "with the C40-4 and C40-7 array configurations at their best angular resolutions of 0.10$''$ and 0.35$''$, respectively." (Data); "The final synthesized beam is $0.22''\,\times\,0.19''$." (Data)
- max recoverable scale: _not stated_
- sensitivity: ~1.0 mJy/beam r.m.s. at 0.32 km/s velocity resolution  
  > "After combining two data sets together, the final achieved r.m.s noise level is $\rm \sim 1.0\,mJy/beam$ at a velocity resolution of $\rm 0.32\, km/s$." (Data)
- time on source: 37 minutes and 63 minutes  
  > "The on-source exposure times were 37 minutes and 63 minutes, respectively." (Data)
- observing dates: 11 Nov. 2016 and 03 Aug. 2017  
  > "our ALMA observations consist of two runs on 11 Nov. 2016 and 03 Aug. 2017" (Data)
- pi or archival as stated: Authors' own follow-up ALMA observation, detailed in Shi2020  
  > "Our follow-up ALMA observation further resolved the CO emission into a few clumpy structures at a spatial resolution of 1.4 pc (cite: Shi2020)." (Introduction)
- Line: CS J=5->4 (not stated)
- Line: CO J=2->1 (not stated)
- Other facility **IRAM 30-m telescope**: CO J=2-1 single-dish detection and flux used to check how much CO flux ALMA recovers  
  > "With the IRAM 30-m telescope, (cite: Shi2016) detected CO $J$=2$\rightarrow$1 in an extremely metal-poor galaxy, DDO 70" (Introduction); "The total CO flux summed up from all five clumps accounts for $\sim 80\%$ of the emission seen by IRAM 30-m telescope (cite: Shi2020)" (Data)
- External data: CS J=5-4 and IR luminosity measurements of extragalactic and Galactic sources used as comparison sample  
  > "we compiled both extra-galactic and Galactic measurements of CS $J$=5$\rightarrow$4 from (cite: Wang2011) and (cite: Wu2010)." (Results) [from (cite: Wang2011); (cite: Wu2010)]
- External data: UV and IR combined SFR of 1.6e-4 Msun/yr within the ALMA aperture of DDO 70  
  > "we adopted the UV and IR combined SFR of $\rm 1.6\times10^{-4}\,M_{\odot}/yr$ within the ALMA aperture of DDO 70, as detailed in (cite: Shi2020)." (Results) [from (cite: Shi2020)]
- External data: Five CO-bright clumps identified from the CO data  
  > "five clumps with significant CO emission identified in (cite: Shi2020)" (Data) [from (cite: Shi2020)]
- External data: Gas-phase oxygen abundance 12+log(O/H)=7.53  
  > "a gas-phase oxygen abundance of $\rm 12+log(O/H)=7.53$ (cite: Kniazev2005)" (Data) [from (cite: Kniazev2005)]
- External data: Distance 1.38 Mpc and redshift 0.001004  
  > "This galaxy is at a distance of 1.38 Mpc (cite: Tully2013) and a redshift of 0.001004 (cite: Springob2005)." (Data) [from (cite: Tully2013); (cite: Springob2005)]
- External data: CO J=1-0/CS J=5-4 versus IR luminosity comparison data  
  > "along with data from (cite: Wang2011) and (cite: Gao2004a)." (Results) [from (cite: Wang2011); (cite: Gao2004a)]

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
- weighting robust: natural weighting  
  > "Natural weighting was adopted in the clean process to optimize sensitivity." (Data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: CO moment-0 map convolved with twice the synthesized beam, then 3-sigma mask; spectra extracted from original-resolution data  
  > "we convolve the CO moment-0 map with twice the synthesized beam, make a mask of 3-$\sigma$ flux threshold, and then extract both CO and CS spectra from the data with original resolution." (Data)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: the two datasets (C40-4 and C40-7) were combined  
  > "After combining two data sets together, the final achieved r.m.s noise level is $\rm \sim 1.0\,mJy/beam$ at a velocity resolution of $\rm 0.32\, km/s$." (Data)
- smoothing: _not stated_
- final beam: 0.22'' x 0.19''  
  > "The final synthesized beam is $0.22''\,\times\,0.19''$." (Data)
- final rms: ~1.0 mJy/beam at 0.32 km/s  
  > "After combining two data sets together, the final achieved r.m.s noise level is $\rm \sim 1.0\,mJy/beam$ at a velocity resolution of $\rm 0.32\, km/s$." (Data)

### Inherited from earlier work

- Observation details (runs, configurations, exposure times, imaging) follow Shi2020  
  > "As detailed in (cite: Shi2020), our ALMA observations consist of two runs on 11 Nov. 2016 and 03 Aug. 2017" (Data) [from (cite: Shi2020)]
- CO-bright clump identification  
  > "five clumps with significant CO emission identified in (cite: Shi2020)" (Data) [from (cite: Shi2020)]
- SFR within the ALMA aperture  
  > "we adopted the UV and IR combined SFR of $\rm 1.6\times10^{-4}\,M_{\odot}/yr$ within the ALMA aperture of DDO 70, as detailed in (cite: Shi2020)." (Results) [from (cite: Shi2020)]
- Luminosity conversion equation for line luminosity L' from flux  
  > "according to Equation [\[eq.1\]](#eq.1) of (cite: Solomon2005):" (Data) [from (cite: Solomon2005)]
- IR luminosity to SFR conversion, IMF adapted from Chabrier2003  
  > "into the SFR using the following equation in (cite: Kennicutt1998):" (Results); "where the initial mass function (IMF) is adapted from (cite: Chabrier2003)." (Results) [from (cite: Kennicutt1998); (cite: Chabrier2003)]

### Not stated but needed to reproduce (our reading)

- ALMA band numbers, spectral windows and rest frequencies used
- Calibration approach (pipeline vs manual), calibrators and flux scale uncertainty
- Clean parameters: robust/weighting details beyond 'natural', cell size, image size, deconvolver, threshold, continuum subtraction and line-free channels
- Exact stacking recipe (weights, velocity alignment, which channels define the integrated flux)
- Velocity range / channel width used to integrate CO and CS and the FWZI value adopted
- How the 3-sigma upper limit on CS luminosity was computed (assumed line width, noise estimate)
- Source coordinates and the clump positions/sizes used for extraction
- Fitting method (least-squares details, weights) for the L'CS-LIR and L'CS-SFR lines

## Analysis recipe

1. **Extract CO and CS spectra from the CO clumps**: Convolve the CO moment-0 map with twice the synthesized beam, apply a 3-sigma mask, and extract CO and CS spectra from the original-resolution data for five CO clumps  
  > "we convolve the CO moment-0 map with twice the synthesized beam, make a mask of 3-$\sigma$ flux threshold, and then extract both CO and CS spectra from the data with original resolution." (Data)
   - software: CASA
   - parameter: mask: 3-sigma on CO moment-0 smoothed by 2x beam  
  > "we convolve the CO moment-0 map with twice the synthesized beam, make a mask of 3-$\sigma$ flux threshold" (Data)
   - fitting: _not stated_
   - validation: CO flux summed over the five clumps is ~80% of the IRAM 30-m flux  
  > "The total CO flux summed up from all five clumps accounts for $\sim 80\%$ of the emission seen by IRAM 30-m telescope (cite: Shi2020)" (Data)
2. **Stack CS spectra**: Stack CS J=5-4 spectra of all CO-bright clumps to improve S/N  
  > "Therefore, to improve the signal-to-noise ratio level, we further stack the CS spectra from all CO-bright clumps." (Data)
   - fitting: _not stated_
   - validation: _not stated_
3. **Convert line fluxes to luminosities**: Convert velocity-integrated flux density to L' (K km/s pc^2) using L'=3.25e7 (1+z)^-3 f_obs^-2 S_CO D_L^2  
  > "which converts the velocity-integrated flux density, $S_{\rm CO}$ (measured in $\rm Jy\,km\,s^{-1}$), to luminosity in units of $\rm K\,km\,s^{-1}\,pc^{2}$." (Data)
   - parameter: FWZI line width adopted for CO J=2-1  
  > "We adopt the Full Width Zero Intensity (FWZI) line width for CO $J$=2$\rightarrow$1." (Data)
   - assumption: D_L is luminosity distance at redshift z (z = 0.001004, distance 1.38 Mpc)  
  > "$D_{\rm L}$ is the luminosity distance at redshift $z$ and $f_{\rm obs}$ is the observing frequency in GHz." (Data)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive CS upper limit**: Because detection is marginal (S/N ~3.3), adopt the 3-sigma upper limit of CS J=5-4 luminosity  
  > "Because the detection is no more than marginal, we used the 3-$\sigma$ upper limit of CS $J$=5$\rightarrow$4 luminosity in the study" (Data)
   - fitting: _not stated_
   - validation: CS marginal feature lies within the CO J=2-1 velocity range  
  > "This marginal feature is within the velocity range of the CO $J$=2$\rightarrow$1 line, and shows a much narrower line width." (Data)
5. **Compare with L'CS-LIR and L'CS-SFR relations**: Compile literature CS J=5-4 and IR data, refit with a straight line excluding upper limits, convert IR luminosity to SFR, and place the DDO 70 upper limit on the relations  
  > "We refit all data points with a straight line, excluding upper limits." (Results); "Assuming that the IR luminosities represent the star-formation rates (SFR) in galaxies, we converted the IR luminosities" (Results)
   - parameter: SFR(Msun/yr) = 2.8e-44 L(IR)(erg/s)  
  > "SFR(M_{\odot}/yr)=2.8\times 10^{-44}L(IR)(erg \cdot s^{-1})," (Results)
   - assumption: IMF adapted from Chabrier2003; IR luminosity represents SFR for the literature sample; DDO 70 uses UV+IR SFR of 1.6e-4 Msun/yr  
  > "where the initial mass function (IMF) is adapted from (cite: Chabrier2003)." (Results); "we adopted the UV and IR combined SFR of $\rm 1.6\times10^{-4}\,M_{\odot}/yr$ within the ALMA aperture of DDO 70" (Results)
   - fitting: Straight-line fit to all non-upper-limit points; sampler, priors and likelihood not stated  
  > "We refit all data points with a straight line, excluding upper limits." (Results)
   - validation: Fit consistent with empirical relation from previous studies  
  > "The derived best-fit line is consistent with the empirical logarithmic relationship found in previous studies." (Results)
6. **Compute CO J=1-0 / CS J=5-4 luminosity ratio**: Convert CO J=2-1 to J=1-0 by an assumed line ratio and compare the CO J=1-0/CS J=5-4 lower limit against IR bright galaxies  
  > "We also calculated the ratio of the line integrated luminosity of CO $J$=1$\rightarrow$0 and CS $J$=5$\rightarrow$4 of DDO 70." (Results)
   - assumption: CO J=2-1/J=1-0 ratio ~1, optically thick and LTE  
  > "we assumed that CO $J$=2$\rightarrow$1/CO $J$=1$\rightarrow$0 line ratio is $\sim1$, under optically thick and local thermodynamic equilibrium conditions." (Results)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.4.0: Extract the CS J=5-4 spectra from five CO clumps  
  > "We used CASA 5.4.0 (cite: CASA2007) to extract the CS $J$=5$\rightarrow$4 spectra from five clumps" (Data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO J=2-1 stacked luminosity L' | ~156.2 | not stated | K km/s pc^2 | 3 | The CO $J$=2$\rightarrow$1 emission is detected at very high signal-to-noise ratio, with a luminosity of $\rm \sim156.2\,K\,km\,s^{-1}\,pc^{2}$ |
| Stacked CS J=5-4 integrated-flux S/N | ~3.3 | not stated | dimensionless | 2 | the stacked CS $J$=5$\rightarrow$4 emission line shows a marginal detection feature with a signal to noise ratio (S/N) of $\sim 3.3$ in the integrated flux. |
| CS J=5-4 3-sigma upper limit luminosity L' | ~10.9 | not stated | K km/s pc^2 | 4 | we used the 3-$\sigma$ upper limit of CS $J$=5$\rightarrow$4 luminosity in the study, which is $\rm \sim10.9\,K\,km\,s^{-1}\,pc^{2}$. |
| Fraction of IRAM 30-m CO flux recovered by summed ALMA clumps | ~80% | not stated | percent | 1 | The total CO flux summed up from all five clumps accounts for $\sim 80\%$ of the emission seen by IRAM 30-m telescope (cite: Shi2020) |
| Final r.m.s. noise | ~1.0 | not stated | mJy/beam | 0 | After combining two data sets together, the final achieved r.m.s noise level is $\rm \sim 1.0\,mJy/beam$ at a velocity resolution of $\rm 0.32\, km/s$. |

## Qualitative findings

- CS J=5-4 is not detected in any CO clump; the stacked spectrum shows only a marginal narrow feature within the CO velocity range  
  > "We did not detect CS $J$=5$\rightarrow$4 in any of the CO clumps." (Data); "This marginal feature is within the velocity range of the CO $J$=2$\rightarrow$1 line, and shows a much narrower line width." (Data)
- The lack of CS emission may result from lower average cloud density, low carbon and sulfur abundance, and photodissociation  
  > "Weak CS emission may be result of on average lower density of a molecular cloud at very low metallicity." (Conclusion)

## Claim tuples

- H: Dense gas traced by CS J=5-4 is detectable in CO-bright clumps of DDO 70 | E: ALMA CS J=5-4 spectra extracted from five CO clumps | R: No CS detection in any clump | F: CS is not detected where CO is strong | **supported**
- H: DDO 70 follows the L'CS-LIR and L'CS-SFR relations of local star-forming galaxies and Galactic dense cores | E: Stack CS spectra, take 3-sigma upper limit and compare with refit literature relations | R: The upper limit lies above the 1-sigma upper bound of the linear correlation | F: CS emission is weak for the given IR luminosity and SFR, a possible CS deficit at low metallicity | **partially**
- H: The CO J=1-0/CS J=5-4 ratio of DDO 70 differs from IR bright galaxies | E: Assume CO J=2-1/J=1-0 ~1 and compare CO/CS ratio versus IR luminosity with literature data | R: Lower limit on CO J=1-0/CS J=5-4 | F: Ratio lower limit is consistent with IR bright galaxies | **supported**
- H: Low density, low C and S abundance, or photodissociation explains weak CS | E: Qualitative discussion using literature results | R: Several mechanisms may contribute; dust-depletion explanation is inconsistent with the observation | F: Cause not pinned down | **partially**

## Reasoning

- Why this data: The CO observation also covers CS J=5-4, offering a chance to study CS excitation at very low metallicity  
  > "The same observation also covers the CS $J$=5$\rightarrow$4 transition, offering an opportunity to explore the complex cases of CS excitation at such extremely low metallicity." (Introduction)
- Why this method: Stacking CS spectra from all CO-bright clumps to improve S/N  
  > "Therefore, to improve the signal-to-noise ratio level, we further stack the CS spectra from all CO-bright clumps." (Data)
- Alternative: Dust-depletion explanation for weak CS is rejected as it would put DDO 70 below the relation, inconsistent with observation  
  > "DDO 70 is expected to be below the relationship, which is inconsistent with the observation." (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): CS detection is no more than marginal, so only an upper limit is used  
  > "Because the detection is no more than marginal, we used the 3-$\sigma$ upper limit of CS $J$=5$\rightarrow$4 luminosity in the study" (Data)
- Limitation (authors): Dominant physical mechanism for weak CS remains unknown  
  > "In the end, it is still unknown that whether these two effects can fully contribute to such low luminosity and whether there exists other dominant physical mechanisms." (Discussion)
- Caveat (inferred, ours): Result is a single upper limit from one galaxy
- Caveat (inferred, ours): Upper limit depends on unstated line-width and stacking choices
- Caveat (inferred, ours): CO J=2-1/1-0 ratio of ~1 is assumed, affecting the CO/CS ratio
- Caveat (inferred, ours): Literature IR-based SFRs and the DDO 70 UV+IR SFR are on different footing

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Calibration and imaging parameters (deferred to Shi2020)
- Missing: Clump masks and exact stacking recipe
- Missing: Line width and noise used for the 3-sigma upper limit
- Missing: Comparison-sample values from Wang2011, Wu2010 and Gao2004a
- Data volume (inferred): tens of GB raw for two ALMA execution blocks (about 100 min on source); smaller for the calibrated cube
- Score (inferred): 2/5, Project code and key numbers are given, but calibration, imaging and stacking details are deferred to Shi2020 or omitted, and public data status is not stated.
- Rediscovery candidate: no, Public data status and key stacking and upper-limit recipe are not stated.

## Links

- Method: (cite: Shi2020) (Describes the ALMA observations, imaging, CO clumps and SFR)
- Method: (cite: Solomon2005) (Line luminosity equation)
- Companion: (cite: Shi2020) (Same ALMA observation, CO emission in DDO 70)
- Companion: (cite: Shi2016) (IRAM 30-m CO J=2-1 detection in DDO 70)

## Checks

```json
{
 "quotes": 69,
 "quotes_ok": 69,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 85,
  "stated": 50,
  "rate": 0.588
 },
 "evidence_ok": true
}
```

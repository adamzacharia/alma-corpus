# Transient brightenings in the quiet Sun detected by ALMA at 3 mm

`2020A&A...638A..62N` | Astronomy and Astrophysics 2020 | first author: Nindos, A. | arXiv: 2004.07591 | DOI: 10.1051/0004-6361/202037810

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: sun
- Question: Are there weak transient brightenings in the quiet Sun at 3 mm with ALMA, what are their properties and energies, and can they account for chromospheric heating?  
  > "Using Atacama Large Millimeter/submillimeter Array (ALMA) observations, we performed the first systematic survey for quiet Sun transient brightenings at 3 mm." (abstract)
- Target **Quiet Sun targets 2-7 (mu = 0.16 to 1.00)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: 100 GHz (3 mm)  
  > "observed at 100 GHz (3 mm) on March 16, 2017" (Observations and data analysis)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: most compact array configuration available  
  > "Our observations were carried out with most compact array configuration available using ALMA at the cost of inferior spatial resolution" (Summary and conclusions)
- baselines: _not stated_
- angular resolution: about 2.5" x 4.5" (target 7: 2.3" x 8.1")  
  > "their spatial resolution deduced from the clean beam size was about $2.5\ensuremath{''} \times
4.5\ensuremath{''}$ with the exception of target 7 whose resolution was $2.3\ensuremath{''}  \times 8.1\ensuremath{''}$." (Observations and data analysis)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 10 min per target, 2 s cadence  
  > "Each target was observed for 10 min with a cadence of 2 s." (Observations and data analysis)
- observing dates: March 16, 2017  
  > "observed at 100 GHz (3 mm) on March 16, 2017" (Observations and data analysis)
- pi or archival as stated: _not stated_
- Other facility **SDO/AIA**: 304 Å (12 s cadence) and 1600 Å (24 s cadence) images over the same fields and times, for comparison  
  > "The cadence of the AIA images was 12 s in 304 Å and 24 s in 1600 Å." (Observations and data analysis)
- External data: Electron temperatures 7250-7950 K from center-to-limb inversion, used to estimate optical depth  
  > "we used the results by Alissandrakis et al. (2017) who, after they inverted the center-to-limb variation curve of full-disk data, found electron temperature values in the range 7250-7950 K" (Implications for chromospheric heating) [from Alissandrakis et al. (2017) (cite: 2017A&A...605A..78A)]
- External data: FAL C model electron densities and heights  
  > "If we use that range of electron temperatures and the corresponding FAL C values for $N_e$, we find that our events occur in configurations in which the optical depth ranges from about 10 to 16" (Implications for chromospheric heating) [from Fontenla et al. (1993)]
- External data: p-mode oscillation frequencies used as harmonic components in fitting  
  > "based on the harmonic components that correspond to the oscillations detected by Patsourakos et al. (2020)" (Observations and data analysis) [from Patsourakos et al. (2020) (cite: Patsourakos20)]

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
- cell size: 1 arcsec pixel  
  > "The final images had pixel size of 1$\ensuremath{''}$" (Observations and data analysis)
- image size: central 87" x 87" of each 120" field used  
  > "we used the central $87\ensuremath{''} \times 87\ensuremath{''}$ region of each field of view to avoid artifacts introduced by the primary beam correction" (Observations and data analysis)
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

- Reduction of the ALMA data  
  > "The reduction of the ALMA data has been described by Nindos et al. (2018)." (Observations and data analysis) [from Nindos et al. (2018) (cite: 2018A&A...619L...6N)]
- Network/intra-network segregation via second-degree polynomial fit  
  > "we were able to segregate the network from the intra-network pixels using the method described by Nindos et al. (2018)" (Statistics and properties of transient brightenings) [from Nindos et al. (2018)]

### Not stated but needed to reproduce (our reading)

- CASA version, calibration and imaging parameters (all in Nindos et al. 2018)
- How sigma of the light curves is defined and computed
- Number of adjacent-pixel clusters 'user-defined' beyond beam-size patch details
- Harmonic frequencies and fitting details for the oscillation removal
- AIA data processing details and alignment specifics
- Histogram binning used for the frequency distributions
- Software used (none named)

## Analysis recipe

1. **Prepare ALMA and AIA data**: Use ALMA snapshot images from Nindos et al. (2018); correct AIA for differential rotation, convolve with ALMA beam, co-align by cross-correlating time-averaged images  
  > "The analysis of the AIA data involved the correction for differential rotation, their convolution with the appropriate ALMA beam, and their co-alignment with the ALMA images" (Observations and data analysis)
   - fitting: _not stated_
   - validation: _not stated_
2. **Detrend and remove p-mode oscillations**: Subtract running average (10 min kernel) over a beam-size macropixel; iterative least-squares harmonic fit and subtraction  
  > "Each light curve was detrended by subtracting the running average of the time profile of a macropixel with size equal to the ALMA beam" (Observations and data analysis)
   - parameter: Maximum error ≲ 5 K, or fewer than five points left  
  > "until an acceptable maximum error ($\lesssim 5$ K) is reached or their number becomes less than five" (Observations and data analysis)
   - fitting: Least-squares harmonic fit (Roerink et al. 2000) with iterative outlier removal  
  > "we applied a least-squares curve fitting procedure (see Roerink et al. 2000)" (Observations and data analysis)
   - validation: Power spectra show p-mode power suppressed by factors of 12 to 17  
  > "panel (f) indicates that our algorithm can significantly suppress the power of p-mode oscillations (by factors of 12 to 17)" (Observations and data analysis)
3. **Detect transient brightenings**: Event if at least 4 consecutive points above 2.5σ, beam-size cluster of adjacent pixels also exceed, and peaks synchronous within ±2 min; AIA requires one point  
  > "the intensity of at least four consecutive points of the light curve was above some user-defined threshold above the average intensity of the curve" (Observations and data analysis)
   - parameter: 2.5σ threshold; 12 pixels (targets 2-6) or 19 pixels (target 7)  
  > "a multiplication factor of 2.5$\sigma$ above average intensity for the light curves" (Observations and data analysis)
   - fitting: _not stated_
   - validation: Threshold and Nmin sensitivity tests (Fig. 2); chance-coincidence estimate for pairing  
  > "the lack of appreciable changes for $N_{min} \leq 12$ justifies our selection of using $N_{min} = 12$ in the subsequent analysis" (Statistics and properties of transient brightenings)
4. **Characterize events and pair with AIA**: Measure areas (divided by mu), FWHM durations, network fraction; pair events sharing a pixel with maxima within 15 s; power-law fits in log-log  
  > "we requested that the two events (ALMA and AIA) have at least one common pixel and that their light curves show maxima within 15 s" (Statistics and properties of transient brightenings)
   - parameter: Fit range: widest range with mean error bars <10%; Poisson uncertainties  
  > "The fitting range was determined automatically as the widest range of values that yielded mean error bars less than 10%." (Statistics and properties of transient brightenings)
   - fitting: Linear fit in log axes with Poisson-weighted bins  
  > "In each case, a linear fit in logarithmic axes was performed that gave the power-law function parameters." (Statistics and properties of transient brightenings)
   - validation: Exponential fits compared via chi-squared  
  > "the values of $\chi^2$ for the exponential fits are about 10% smaller than those of the power-law fits" (Statistics and properties of transient brightenings)
5. **Derive thermal energies and heating power**: E = 3 N_e k V_ap (T_e,max - T_e,0) with FAL C densities at h1 and h2; power per unit area from total energy, duration and area  
  > "$$\begin{equation}
E = 3N_e k V_{ap} (T_{e,max}-T_{e,0})
.
\end{equation}$$" (Implications for chromospheric heating)
   - assumption: Optically thick (tau 10-16), so excess Tb equals excess Te; filling factor 1; constant Ne; V_ap = A^(3/2)  
  > "we assume that the volume, $V_{ap}$, can be estimated from the area, $A$, of the event through the equation $V_{ap} = A^{3/2}$" (Implications for chromospheric heating)
   - fitting: Power-law fit to energy distribution above 2.4e24 erg  
  > "For energies higher than 2.4 $\times 10^{24}$ erg" (Implications for chromospheric heating)
   - validation: Repeated with relaxed criteria (2.3σ, 2.1σ, >=1 pixel)  
  > "we estimated the energy content of the ALMA events detected by using both a 2.3$\sigma$ and a 2.1$\sigma$ threshold" (Implications for chromospheric heating)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of ALMA events | 184 | not stated | events | 3 | we were able to able to detect 184 events in the six $87\ensuremath{''} \times 87\ensuremath{''}$ targets |
| Mean event duration (3 mm) | 51.1 | 6.5 | s | 4 | Mean duration$^{d}$ (s) (all) / $51.1 \pm 6.5$ |
| Mean maximum area (3 mm) | 12.3 | 3.4 | Mm^2 | 4 | Mean area (Mm$^2$) (all) / $12.3 \pm 3.4$ |
| Power-law index of area distribution (3 mm) | 2.73 | 0.02 | dimensionless | 4 | Power-law index of distribution (all) / $2.73 \pm 0.02$ |
| Power-law index of duration distribution (3 mm) | 2.35 | 0.02 | dimensionless | 4 | Power-law index of distribution (all) / $2.35 \pm 0.02$ |
| Thermal energy range | 1.5e24 to 9.9e25 | ±0.1e24 and ±2.0e25 at ends | erg | 5 | Our computations (see Table 3) yielded thermal energies ranging from $(1.5 \pm 0.1)  \times 10^{24}$ to $(9.9 \pm 2.0) 
\times 10^{25}$ erg. |
| Energy distribution power-law index | 1.67 | 0.05 | dimensionless | 5 | can be fitted with a power-law function with index of $1.67 \pm 0.05$ |
| Power per unit area | 1.9e4 | 0.2e4 | erg cm^-2 s^-1 | 5 | All events (2.5$\sigma$, pixels $\geq$ beam size) / $15.0 \pm 1.0$ / $1.0 \pm 0.2$ / $1.67 \pm 0.05$ / $1.9 \pm 0.2$ |
| Events with 304 Å / 1600 Å counterparts | 18 / 14 | not stated | events | 4 | Only a small fraction of ALMA events had 304 Å and 1600 Å counterparts (18 and 14), respectively. |

## Qualitative findings

- All events show gradual rise and fall light curves, suggesting thermal free-free origin  
  > "the gradual rise and fall of their light curves strongly suggests a thermal origin via the free-free mechanism" (Statistics and properties of transient brightenings)

## Claim tuples

- H: Weak transient brightenings can be detected systematically in quiet Sun ALMA 3 mm data | E: Detrend and remove p-modes, apply threshold and spatial coherence criteria on six fields | R: 184 events with 70 to >500 K excess | F: A significant population of weak 3 mm brightenings exists | **supported**
- H: ALMA transient brightenings supply enough energy to heat the chromosphere | E: Energy estimate from excess Tb with FAL C densities, summed per area and time | R: 1.9e4 erg cm^-2 s^-1, about 1% of chromospheric losses | F: Energy budget is insufficient, even with relaxed criteria | **supported**
- H: ALMA events correlate with AIA 304/1600 Å events | E: Pairing by common pixel and 15 s peak tolerance | R: Only a small fraction paired; paired properties similar apart from missing low energies | F: Most ALMA events have no AIA counterparts | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Millimeter free-free emission is linearly linked to electron temperature, simplifying physical parameter derivation  
  > "the relevant emission mechanism is thermal free-free, which does not suffer from the problems mentioned above" (Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Energies are upper limits owing to assumptions; poor resolution; optically thick emission samples only a thin layer; residual oscillation power may affect detection of weak events  
  > "imply that the derived energies represent upper limits" (Implications for chromospheric heating)
- Caveat (inferred, ours): Event detection depends on user-chosen thresholds and residual p-mode power; false positives are not quantified by simulation
- Caveat (inferred, ours): Energy estimates rely on FAL C density and V=A^1.5 assumption
- Caveat (inferred, ours): Single 10 min dataset per target

## Reproducibility

- Data public (paper): ALMA data cited by project code 2016.1.00572.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA2016.1.00572.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Calibrated snapshot images (reduction in Nindos et al. 2018)
- Missing: Detection code and sigma definition
- Missing: Oscillation harmonic frequencies
- Data volume (inferred): tens of GB (solar time-series data, 2 s cadence)
- Score (inferred): 3/5, Data public and method described, but reduction is inherited and key parameters and code are unstated.
- Rediscovery candidate: no, Depends on a prior paper's reduction and custom unreleased detection code.

## Links

- Method: Nindos et al. (2018) (ALMA data reduction and network segmentation)
- Method: Roerink et al. (2000) (Harmonic least-squares fit)
- Companion: Patsourakos et al. (2020) (p-mode oscillations in the same dataset)

## Checks

```json
{
 "quotes": 47,
 "quotes_ok": 47,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2016.1.00572.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 34,
  "rate": 0.486
 },
 "evidence_ok": true
}
```

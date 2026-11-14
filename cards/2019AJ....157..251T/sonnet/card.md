# Neptune's Latitudinal Variations as Viewed with ALMA

`2019AJ....157..251T` | The Astronomical Journal 2019 | first author: Tollefson, Joshua | arXiv: 1905.03384 | DOI: 10.3847/1538-3881/ab1fdf

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: solar_system
- Question: How do Neptune's latitudinal brightness temperature variations at 1-3 mm constrain H2S, CH4 and ortho/para H2 abundances and the global circulation?  
  > "We model Neptune’s brightness temperature using the radiative transfer code Radio-BEAR and compare how various H$_2$S, CH$_4$, and *ortho/para* H$_2$ abundance profiles can fit the observed temperature variations across the disk." (abstract)
- Target **Neptune**: coordinates not stated (ephemeris from JPL Horizons)  
  > "see Neptune’s entire (2.3” diameter) disk." (2.1 Data); "Planetary coordinates are computed for each pixel on the disk using ephemeris data from JPL Horizons" (4.2 Latitudinal Brightness Temperature Variations); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00859.S
- bands: Bands 3, 4, 6 (95-250 GHz, 1-3 mm)  
  > "Our Neptune observations were taken between $2016-2017$ in Bands 3, 4, and 6, between $95-250$ GHz (1–3 mm)." (2.1 Data)
- frequencies and spectral setup: Four continuum spectral windows per band, 128 channels of 15.625 MHz, 2000 MHz each; centers 95.012/96.970/107.000/109.000, 135.986/137.924/147.986/149.986, 223.982/225.982/239.981/241.981 GHz  
  > "We observed in four spectral windows in continuum mode covering Neptune’s continuum spectra within each band." (2.1 Data); "Each spectral window has the same total bandwidth, consisting of 128 channels with the same channel width." (Table 2)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Band 3 C40-8; Bands 4 and 6 C40-7  
  > "| Band 3 | C40-8 | 2017-07-27 | J0006-0623 | J2246-1206 | 726 |" (Table 1); "| Band 4 | C40-7 | 2016-10-07 | J2258-2758 | J2246-1206 | 1701 |" (Table 1)
- baselines: _not stated_
- angular resolution: typical 0.3"; beams from 0.45"x0.33" (Band 3) to 0.29"x0.23" (Band 6)  
  > "A typical resolution was 0.3” using $\sim40$ 12-m antennas." (2.1 Data)
- max recoverable scale: _not stated_
- sensitivity: RMS 0.1-0.6 K  
  > "RMS values range from $0.1-0.6$K." (2.3 Error estimation)
- time on source: 726 s (Band 3), 1701 s (Band 4), 1032 s (Band 6)  
  > "| Band 6 | C40-7 | 2016-10-24 | J2258-2758 | J2246-1206 | 1032 |" (Table 1)
- observing dates: 2017-07-27 (B3), 2016-10-07 (B4), 2016-10-24 (B6)  
  > "| Band 3 | C40-8 | 2017-07-27 | J0006-0623 | J2246-1206 | 726 |" (Table 1)
- pi or archival as stated: _not stated_
- External data: 2003 VLA centimeter disk-averaged brightness temperatures  
  > "agrees very well with both the ALMA millimeter and the 2003 VLA centimeter data from (cite: dePater2014)." (4.1 Disk-Averaged Brightness Temperatures) [from (cite: dePater2014)]
- External data: Temperature profile above 1 bar  
  > "At altitudes above 1 bar, we use the temperature profile from (cite: Fletcher2010)." (3 Models) [from (cite: Fletcher2010)]
- External data: Protosolar abundances  
  > "We use the protosolar values from (cite: Asplund2009): C/H$_2$ = 5.90E-4; N/H$_2$ = 1.48E-4; O/H$_2$ = 1.07E-3; S/H$_2$ = 2.89E-5." (Footnote 2) [from (cite: Asplund2009)]
- External data: Methane profiles at 6S and 45S  
  > "Between $32^{\circ}$S$-20^{\circ}$N, we use the (cite: Karkoschka2011) methane profile at $6^{\circ}$S; elsewhere, we use their $45^{\circ}$S model" (4.6 Comparison to Karkoschka2011) [from (cite: Karkoschka2011)]

## Processing

### Calibration

- pipeline or manual: Standard ALMA pipeline for flagging, bandpass, flux and gain calibration  
  > "We applied the standard ALMA pipeline to perform flagging (bad edge channels, shadowed antennas, and poor quality data), bandpass and flux calibration, and gain-time solutions." (2.2 Calibration and Imaging)
- casa version: CASA 5.1  
  > "reduced and calibrated in the Common Astronomical Software Application (CASA) version 5.1." (2.2 Calibration and Imaging)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0006-0623 (B3), J2258-2758 (B4, B6)  
  > "| Band 4 | C40-7 | 2016-10-07 | J2258-2758 | J2246-1206 | 1701 |" (Table 1)
- flux scale uncertainty: about 5% or less  
  > "The ALMA Calibrator Source Catalogue lists errors in the calibrator’s flux estimate being about 5$\%$ or less in each band" (2.3 Error estimation)
- self calibration: Three iterations: first over entire observation, then 350 s and 60 s intervals  
  > "The first iteration used the entire observation range while the second and third used 350-second and 60-second intervals." (2.2 Calibration and Imaging)

### Imaging

- task: CASA tclean, multi-frequency synthesis  
  > "The multi-frequency synthesis mode in CASA *tclean* was used to transform the visibility data into image maps." (2.2 Calibration and Imaging)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We used natural weighting and restricted clean to a circular mask" (2.2 Calibration and Imaging)
- uv taper: _not stated_
- cell size: 0.02"  
  > "Our resulting maps are 512$\times$512 pixels$^2$ with a cell size of 0.02"." (2.2 Calibration and Imaging)
- image size: 512x512 pixels  
  > "Our resulting maps are 512$\times$512 pixels$^2$ with a cell size of 0.02"." (2.2 Calibration and Imaging)
- masking: circular mask of Neptune's diameter plus twice the beam size; 1000-2000 clean iterations  
  > "restricted clean to a circular mask that is roughly the size of Neptune’s diameter plus twice the beam size." (2.2 Calibration and Imaging); "The number of clean iterations varied from 1000-2000" (2.2 Calibration and Imaging)
- multiscale scales: _not stated_
- continuum subtraction: limb-darkened model subtracted from data before deconvolution  
  > "We also subtracted a limb-darkened model from the data to speed up the deconvolution process and reduce imaging artifacts." (2.2 Calibration and Imaging)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: 0.1-0.6 K  
  > "RMS values range from $0.1-0.6$K." (2.3 Error estimation)

### Inherited from earlier work

- Self-calibration approach  
  > "to remove short-term phase variability caused by fast atmospheric fluctuations (cite: Brogan2018)." (2.2 Calibration and Imaging) [from (cite: Brogan2018)]
- CMB correction procedure  
  > "we correct for the CMB by following the procedure laid out in Appendix A of (cite: dePater2014)." (4.1 Disk-Averaged Brightness Temperatures) [from (cite: dePater2014)]
- Intermediate ortho/para H2 treatment  
  > "we assume “intermediate" H$_2$ proposed by (cite: Trafton1967) and used by e.g., (cite: LuszczCook2013b)" (3 Models) [from (cite: Trafton1967)]
- Radio-BEAR radiative transfer code  
  > "our radiative transfer (RT) code Radio-BEAR described in (cite: dePater2019)" (3 Models) [from (cite: dePater2019)]

### Not stated but needed to reproduce (our reading)

- Limb-darkened model parameters used for subtraction
- Clean threshold and mask details
- Self-calibration solution type and reference antenna
- Exact method of fitting the Bessel function to uv short-spacing amplitudes
- Method of selecting best-fit profile (grid search criteria beyond reduced chi2)
- Planetary radius/ephemeris values used for sub-observer coordinates
- Full Radio-BEAR configuration file

## Analysis recipe

1. **Calibrate and self-calibrate**: Standard ALMA pipeline in CASA 5.1 followed by three rounds of self-calibration  
  > "Finally, we applied three iterations of self calibration on our Neptune data" (2.2 Calibration and Imaging)
   - software: CASA
   - parameter: Solution intervals: full observation, 350 s, 60 s  
  > "The first iteration used the entire observation range while the second and third used 350-second and 60-second intervals." (2.2 Calibration and Imaging)
   - fitting: _not stated_
   - validation: _not stated_
2. **Image Neptune per spectral window**: tclean MFS with natural weighting, circular mask, limb-darkened model subtraction  
  > "We used natural weighting and restricted clean to a circular mask" (2.2 Calibration and Imaging)
   - software: CASA
   - parameter: 512x512 pixels, 0.02" cell, 1000-2000 iterations until in-disk noise equals sky noise  
  > "stopping once the noise within the planetary disk reached the noise in the sky." (2.2 Calibration and Imaging)
   - fitting: _not stated_
   - validation: Tested uniform and intermediate weightings, which produced artificial speckles  
  > "we found that uniform and intermediate weightings produced artificial speckles on the disk and large scale structures in the sky." (2.2 Calibration and Imaging)
3. **Measure disk-averaged brightness temperature and noise**: Average of summed flux density within disk and Bessel-function fit to uv short-spacing amplitude; CMB correction; noise from RMS in four sky boxes  
  > "First, we sum the flux density contained within the planetary disk convolved with the model beam. Second, we fit the u-v short-spacing amplitude with a Bessel function" (4.1 Disk-Averaged Brightness Temperatures)
   - assumption: 5% absolute flux error from calibrators  
  > "so we use this as an estimate for the absolute error in our disk-averaged temperature data" (2.3 Error estimation)
   - fitting: Bessel function fit to uv amplitudes  
  > "we fit the u-v short-spacing amplitude with a Bessel function and obtain an estimate of the zero-spacing flux density." (4.1 Disk-Averaged Brightness Temperatures)
   - validation: Two methods agree within absolute calibration errors  
  > "Both results agree to well within the absolute calibration errors." (4.1 Disk-Averaged Brightness Temperatures)
4. **Build nominal Radio-BEAR model and residual maps**: 2D RT model maps on 9455 disk points interpolated to 0.02", convolved with elliptical Gaussian beam; maps scaled so disk average matches nominal model; subtract to get residuals; identify seven latitude bands  
  > "we calculate the RT-derived brightness temperatures of the planet on 9455 points on the disk and interpolate between these points to obtain the same resolution as our CASA imaged maps (0.02”)." (3 Models)
   - software: Radio-BEAR
   - parameter: Dry adiabat, T=71.5 K at 1 bar, trace gases 30x protosolar (NH3 1x), intermediate H2  
  > "1) Neptune’s trace gases are enhanced to 30$\times$ their protosolar value, except NH$_3$ which is $1\times$ protosolar;" (3 Models)
   - assumption: Neptune's disk-average matches the nominal model; clouds ignored; LTE  
  > "our main assumption in this analysis is that Neptune’s disk-average matches the nominal model." (4.2 Latitudinal Brightness Temperature Variations)
   - fitting: _not stated_
   - validation: Nominal model compared with ALMA and 2003 VLA disk-averaged data  
  > "which fits both our ALMA and 2003 VLA disk-averaged temperatures simultaneously." (4 Results)
5. **Fit H2S, CH4 and ortho/para H2 profiles per latitude bin**: Grid of models varying one constituent at a time, then all together; best fit chosen via reduced chi2 per latitude bin  
  > "we present models where we vary a single constituent: H$_2$S, CH$_4$, or *ortho/para* H$_2$, while holding the others at their nominal value." (4.4 Constraining Neptune’s Variations with Latitude)
   - software: Radio-BEAR
   - parameter: H2S deep 5-30xS in 5xS steps; supersaturation to 5-7 bar in 0.25 bar steps; CH4 0.55-4.4% in 0.36% steps  
  > "is set from $5-30\times$ solar in 5$\times$S steps." (4.4.1 Varying H2S); "We create a grid of models in mixing ratio step-sizes of 0.36$\%$ (or 7.5$\times$S)" (4.4.2 Varying CH4)
   - assumption: Brightness variations due to opacity variations; no latitudinal temperature variations beyond dry adiabat  
  > "apart from the dry and wet adiabat, we do not consider latitudinal variations in temperature." (4.1 Disk-Averaged Brightness Temperatures)
   - fitting: Reduced chi2 with 8 degrees of freedom (12 windows minus 4 parameters); inconsistent if chi2 > 15.5 (p<0.05)  
  > "For eight degrees of freedom, $p < 0.05$ when the reduced $\chi^2 > 15.5$." (4.4 Constraining Neptune’s Variations with Latitude)
   - validation: South pole fit tested against VLA and CARMA models; comparison with Karkoschka & Tomasko 2011 methane profiles  
  > "This provides a good litmus test for our model and fitting routine." (4 Results)

## Software

- **CASA** 5.1: Calibration, self-calibration, imaging  
  > "reduced and calibrated in the Common Astronomical Software Application (CASA) version 5.1." (2.2 Calibration and Imaging)
- **tclean** : Multi-frequency synthesis imaging  
  > "The multi-frequency synthesis mode in CASA *tclean* was used to transform the visibility data into image maps." (2.2 Calibration and Imaging)
- **Radio-BEAR** : Radiative transfer model maps of Neptune  
  > "2D model maps of Neptune’s disk were created using our radiative transfer (RT) code Radio-BEAR" (3 Models)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk-averaged Tb at 95.012 GHz | 126.6 | 6.3 | K | 3 | / 95.012 / $3.4\pm0.2$ / $126.6\pm6.3$ / 119.9 / 0.1 / 0.945 / |
| Disk-averaged Tb at 241.981 GHz | 92.8 | 4.6 | K | 3 | / 241.981 / $15.3\pm0.8$ / $92.8\pm4.6$ / 93.2 / 0.6 / 1.010 / |
| Number of latitudinal bands | 7 | not stated | dimensionless | 4 | We identify seven bands on Neptune that correspond to discrete changes in the temperature structure |
| South polar cap best-fit deep H2S and CH4 | H2S 1.5x protosolar; CH4 0.55% | not stated | x protosolar; % | 5 | our best fit model depletes the deep atmospheric abundance of both H$_2$S to 1.5$\times$ the protosolar value and CH$_4$ to 0.55$\%$ (11.5$\times$S). |
| Best-fit reduced chi2 per latitude bin (90S-66S to 20N-50N) | 3.4, 2.9, 6.8, 2.0, 8.1, 4.1, 6.2 | not stated | dimensionless | 5 | / Best Fit / 3.4 / 2.9 / 6.8 / 2.0 / 8.1 / 4.1 / 6.2 / |
| Brightness residual at 32-12S and 2-20N | -0.5 to -1.5 | not stated | K | 4 | are colder than the background by $\sim0.5-1.5$K in all three bands. |
| South polar enhancement Bands 3 and 4 | 2-3 | not stated | K | 4 | Our ALMA maps show average enhancements of $2-3$K in Bands 3 and 4 |

## Qualitative findings

- Nominal model (dry adiabat, 30x protosolar trace gases, NH3 1x) fits ALMA and VLA disk-averages; wet adiabats are too cold  
  > "Models with temperatures following wet lapse rates are too cold relative to these data." (4.1 Disk-Averaged Brightness Temperatures)
- Data inconsistent with Karkoschka & Tomasko 2011 methane profiles  
  > "Therefore, our data are not consistent with the (cite: Karkoschka2011) methane profiles." (4.6 Comparison to Karkoschka2011)

## Claim tuples

- H: Do ALMA maps show discrete latitudinal brightness variations in Neptune? | E: Subtract nominal beam-convolved model from scaled ALMA maps | R: Seven latitude bands with 0.5-3 K variations in all bands | F: Neptune has banded millimeter structure | **supported**
- H: Can varying H2S, CH4, or H2 alone explain the variations? | E: Single-constituent model grids compared via reduced chi2 | R: Varying one constituent fails in several bins; combined H2S+CH4 gives chi2 below 15.5 everywhere | F: H2S variations from sub- to super-saturation plus CH4 changes near equator are needed | **supported**
- H: Are the data consistent with the Karkoschka & Tomasko methane distribution? | E: Fit H2S with their CH4 profiles | R: Fits only at 90S-50S and north of 20N, requiring ~10xS H2S disk-average | F: Not consistent | **refuted**
- H: Do the bands imply a more complex circulation than earlier models? | E: Interpret enriched/depleted regions as upwelling/downwelling | R: Upwelling at 32-12S and 2-20N, downwelling at poles and 12S-2N | F: More complex equatorial structure than prior circulation models | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Natural weighting chosen because uniform and intermediate weightings produced artifacts  
  > "Natural weighting limits these artifacts since the sensitivity is highest, but sacrifices some angular resolution" (2.2 Calibration and Imaging)
- Alternative: Wet adiabat models rejected as too cold  
  > "Models with temperatures following wet lapse rates are too cold relative to these data." (4.1 Disk-Averaged Brightness Temperatures)
- Alternative: Normal H2 admixture rejected for best fit since other bands fail  
  > "For the best fit model, we therefore do not consider normal hydrogen." (4.4.3 Varying ortho/para H2)
- How they decided it was enough: _not stated_
- Limitation (authors): Models are highly degenerate and omit latitudinal temperature variations and adiabatic heating/cooling  
  > "First, these models are highly degenerate." (4.1 Disk-Averaged Brightness Temperatures)
- Caveat (inferred, ours): Residuals depend on assuming the disk average matches the nominal model, which rescales each band
- Caveat (inferred, ours): Chi2 with 8 degrees of freedom and per-window independence is questionable given shared calibration
- Caveat (inferred, ours): Latitudinal temperature variations ignored and may mimic opacity changes
- Caveat (inferred, ours): Cloud opacity neglected; H2S laboratory opacity uncertain
- Caveat (inferred, ours): Grid fits have no formal parameter uncertainties

## Reproducibility

- Data public (paper): ALMA project data acknowledged; archival access implied but not explicitly stated as public  
  > "This paper makes use of the following ALMA data: ADS/JAO.2016.1.00859.S." (Acknowledgements)
- Products in archive: _not stated_
- Code: Radio-BEAR code available on GitHub  
  > "This code is available at: <https://github.com/david-deboer/radiobear> ." (Footnote 1)
- Missing: Limb-darkened model parameters
- Missing: Exact abundance profile definitions for supersat-v1/v2
- Missing: Radio-BEAR configuration and opacity inputs
- Missing: Scaling-factor procedure details
- Data volume (inferred): ~50-100 GB raw for three short execution blocks
- Score (inferred): 3/5, Public data and code with clear pipeline, but several modelling and imaging details are not stated.
- Rediscovery candidate: yes, Data are from a known ALMA project, the recipe is mostly complete, code is public, and results (Tb, chi2, abundances) are numeric.

## Links

- Method: (cite: dePater2019) (Describes Radio-BEAR)
- Method: (cite: Brogan2018) (Self-calibration guidance)
- Companion: (cite: LuszczCook2013b) (CARMA maps of Neptune compared with ALMA)
- Companion: (cite: dePater2014) (VLA maps and south polar model)

## Checks

```json
{
 "quotes": 76,
 "quotes_ok": 76,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 58,
  "rate": 0.707
 },
 "evidence_ok": true
}
```

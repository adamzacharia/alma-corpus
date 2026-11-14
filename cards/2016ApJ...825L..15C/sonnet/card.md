# Interferometric Mapping of Magnetic Fields: The ALMA View of the Massive Star-forming Clump W43-MM1

`2016ApJ...825L..15C` | The Astrophysical Journal Letters 2016 | first author: Cortes, Paulo C. | arXiv: 1605.08037 | DOI: 10.3847/2041-8205/825/1/L15

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: What are the fragmentation, masses and magnetic field morphology and strength in W43-MM1, and are the fragments magnetically supercritical?  
  > "We found a smooth, ordered, and detailed polarization pattern throughout the filament which we used to derived magnetic field morphologies and strengths" (abstract)
- Target **W43-MM1**: coordinates 18:47:47.0 -01:54:28.0 (phase center)  
  > "W43-MM1 is a large and young high mass star forming clump located within the W43 region and at 5.5 kpc from the sun" (INTRODUCTION); "using $\alpha=$18:47:47.0 and $\delta=$-01:54:28.0 as phase center" (OBSERVATIONS); z/distance 5.5 kpc  
  > "W43-MM1 is a large and young high mass star forming clump located within the W43 region and at 5.5 kpc from the sun" (INTRODUCTION); "using $\alpha=$18:47:47.0 and $\delta=$-01:54:28.0 as phase center" (OBSERVATIONS); distance from Motte2003; Zhang2014a  
  > "W43-MM1 is a large and young high mass star forming clump located within the W43 region and at 5.5 kpc from the sun" (INTRODUCTION); "using $\alpha=$18:47:47.0 and $\delta=$-01:54:28.0 as phase center" (OBSERVATIONS)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 6 (1 mm)  
  > "ALMA observations at 1 mm (band 6) were done on May 30th, 2015" (OBSERVATIONS)
- frequencies and spectral setup: 4 continuum spectral windows centered at 224.884, 226.884, 238.915, 240.915 GHz; 64 channels, 31.250 MHz resolution; full polarization  
  > "Each spectral window was centered at the standard ALMA band 6 polarization frequencies (224.884, 226.884, 238.915, and 240.915 GHz)" (OBSERVATIONS)
- continuum bandwidth: _not stated_
- arrays: 35 antennas  
  > "An array of 35 antennas was used reaching an angular resolution of 0.5$^{\prime \prime}$" (OBSERVATIONS)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.5 arcsec (~0.01 pc)  
  > "An array of 35 antennas was used reaching an angular resolution of 0.5$^{\prime \prime}$ ($\sim$ 0.01 pc scales)" (OBSERVATIONS)
- max recoverable scale: _not stated_
- sensitivity: sigma = 0.41 mJy/beam (Stokes I)  
  > "The noise in the ALMA map is $\sigma = 0.41$ mJy $\mathrm{beam}^{-1}$" (CONTINUUM EMISSION)
- time on source: _not stated_
- observing dates: 2015 May 30; two executions  
  > "two successful executions were done as part of the session scheme" (OBSERVATIONS)
- pi or archival as stated: _not stated_
- Other facility **SMA**: Earlier polarization and CH3CN results used for comparison and source naming  
  > "we kept the same source nomenclature used by (cite: Sridharan2014)" (CONTINUUM EMISSION)
- External data: Dust temperature profile for source A (~150 K at 2500 AU, ~70 K at 8000 AU)  
  > "Their model suggests a temperature of $\sim$ 150 K at 2500 AU distance" (CONTINUUM EMISSION) [from Herpin2012]
- External data: Line width 3.0 km/s from H13CO+(4-3) and DCO+(5-4) single dish  
  > "which in this case was taken to be 3.0 km/s from H$^{13}$CO$^{+}$(4-3) and DCO$^{+}$(5-4) single dish emission" (THE MAGNETIC FIELD MORPHOLOGY) [from Cortes2010; Cortes2011]
- External data: Dust opacity kappa_1.3mm = 0.01 cm2/g  
  > "assuming a dust opacity of $\kappa_{\mathrm{1.3 mm}} = 0.01$ cm$^{2}$g$^{-1}$ (cite: Ossenkopf1994)" (CONTINUUM EMISSION) [from Ossenkopf1994]

## Processing

### Calibration

- pipeline or manual: Manual polarization calibration (cross-polarization delay, XY-phase, D-terms from J1924-292)  
  > "Using this source, we derived solutions for the cross polarization delay, the *XY*-phase, and the D-terms" (Calibration and imaging in full polarization mode)
- casa version: CASA 4.5  
  > "Calibration and imaging was done using the Common Astronomical Software Applications (CASA) version 4.5." (OBSERVATIONS)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (flux), J1751+0939 (bandpass), J1851+0035 (phase), J1924-292 (polarization)  
  > "also using J1751+0939 to calibrate the bandpass, J1851+0035 to calibrate the phase, and Titan to calibrate the flux." (Calibration and imaging in full polarization mode)
- flux scale uncertainty: _not stated_
- self calibration: Three iterations, final solution interval 90 s  
  > "The final images were produced after three self-calibration iterations using a final solution interval of 90 seconds" (Calibration and imaging in full polarization mode)

### Imaging

- task: CASA clean, Briggs weighting  
  > "we imaged the data using the $clean$ CASA task with the *Briggs* weighting scheme" (Calibration and imaging in full polarization mode)
- deconvolver: Clark  
  > "the Clark deconvolution algorithm to produce the Stokes images" (Calibration and imaging in full polarization mode)
- weighting robust: robust = 0.5  
  > "robust number 0.5, for sidelobe robustness" (Calibration and imaging in full polarization mode)
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

- Detailed polarization calibration procedure follows the 3C286 Band 6 polarization CASA guide  
  > "More details about the calibration procedure can be found in the 3c286 ALMA science verification data casa-guide" (footnote 1) [from CASA guide 3C286_Band6Pol_Calibration_for_CASA_4.3]
- Chandrasekhar-Fermi formula form  
  > "we estimated the strength of the field using the Chandrasekhar & Fermi technique (cite: Chandrasekhar1953) as follows from (cite: Crutcher2004)." (THE MAGNETIC FIELD MORPHOLOGY) [from Crutcher2004]
- Source nomenclature kept from SMA study  
  > "we kept the same source nomenclature used by (cite: Sridharan2014)" (CONTINUUM EMISSION) [from Sridharan2014]

### Not stated but needed to reproduce (our reading)

- Image size, cell size, clean masks and threshold
- Number of clean iterations and spectral-window continuum combination details
- Exact getsources parameters
- Method of EVPA/polarized intensity debiasing and region definitions
- How the mean densities and column densities were computed
- Flux calibration uncertainty
- Project code not printed
- Polarization sigma clipping details beyond 5 sigma

## Analysis recipe

1. **Polarization calibration and imaging**: Solve cross-pol delay, XY-phase, D-terms with J1924-292; apply to target; clean Stokes images with 3 self-cal iterations  
  > "we derived solutions for the cross polarization delay, the *XY*-phase, and the D-terms" (Calibration and imaging in full polarization mode)
   - software: CASA
   - parameter: Briggs robust 0.5, Clark, self-cal solint 90 s  
  > "robust number 0.5, for sidelobe robustness and the Clark deconvolution algorithm" (Calibration and imaging in full polarization mode)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract continuum sources and fluxes**: getsources extraction, then 2-D Gaussian fit with imfit using getsources positions and sizes as initial guesses  
  > "We used the source positions and sizes derived using *getsources* as initial guess for a Gaussian 2-D fitting (using CASA *imfit* algorithm)" (CONTINUUM EMISSION)
   - software: getsources, CASA imfit
   - fitting: Gaussian 2-D fit  
  > "We used the source positions and sizes derived using *getsources* as initial guess for a Gaussian 2-D fitting (using CASA *imfit* algorithm) in order to derived accurate fluxes from the extracted sources" (CONTINUUM EMISSION)
   - validation: Compared with clumpfind, FellWalker and Reinhold; good agreement  
  > "obtaining a good agreement with the selection produced by *getsources*" (CONTINUUM EMISSION)
3. **Derive fragment masses**: Standard dust-emission mass (Hildebrand 1983)  
  > "Using the standard procedure to calculate masses from dust emission (cite: Hildebrand1983) we computed masses for all 15 sources" (CONTINUUM EMISSION)
   - assumption: kappa_1.3mm=0.01 cm2/g, gas-to-dust 100, Tdust=25 K (70-150 K for source A), d=5.5 kpc  
  > "a gas to dust ratio of 1:100, and a dust temperature of $T_{\mathrm{dust}} = 25$ K (cite: Bally2010)" (CONTINUUM EMISSION)
   - fitting: _not stated_
   - validation: _not stated_
4. **Estimate plane-of-sky field strength**: Chandrasekhar-Fermi with Heitsch2001 and Falceta2008 modifications, per region; EVPA dispersion via circular statistics  
  > "we included modified versions of the CF method (cite: Heitsch2001; Falceta2008), to calculate the field strength on each region independently." (THE MAGNETIC FIELD MORPHOLOGY)
   - parameter: Delta V = 3.0 km/s; regions divided into four  
  > "we divided the filament into four regions according to the boundaries in the field pattern." (THE MAGNETIC FIELD MORPHOLOGY)
   - assumption: Perfect grain alignment; B rotated 90 deg from EVPA  
  > "Assuming perfect grain alignment, the magnetic field morphology onto the plane of the sky is inferred from the polarized emission by rotating the electric vector position angle (EVPA) by 90$^{\circ}$" (THE MAGNETIC FIELD MORPHOLOGY)
   - fitting: _not stated_
   - validation: Compared with SMA results and Crutcher2012 B-N relation  
  > "We found overall agreement with the SMA results" (THE MAGNETIC FIELD MORPHOLOGY)
5. **Stability: Jeans length and mass-to-flux ratio**: Thermal Jeans length and lambda_B = 7.6e-21 N(H2)/(3 Bpos)  
  > "we calculated the thermal Jeans length as $\lambda_{J} = c_{s}(\pi/G\rho)^{1/2}$" (SUMMARY AND DISCUSSION)
   - assumption: Geometric factor 3 for uniform slab  
  > "factor of 3 in the denominator corresponds to an statistical geometrical correction (cite: Crutcher2004)" (SUMMARY AND DISCUSSION)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.5: Calibration, clean imaging, imfit  
  > "Calibration and imaging was done using the Common Astronomical Software Applications (CASA) version 4.5." (OBSERVATIONS)
- **getsources** : Source extraction  
  > "We used the *getsources* algorithm (cite: Menshchikov2012) to successfully extract 14 sources" (CONTINUUM EMISSION)
- **clumpfind** : Comparison source extraction  
  > "compared to other methods such as *clumpfind* (cite: Williams1994), *FellWalker*, and *Reinhold* (cite: Berry2007)" (CONTINUUM EMISSION)
- **APLpy** : Plotting  
  > "This research made use of APLpy, an open-source plotting package for Python" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Noise in Stokes I map | 0.41 | not stated | mJy/beam | 1 | The noise in the ALMA map is $\sigma = 0.41$ mJy $\mathrm{beam}^{-1}$ |
| Source A peak intensity | 503 | 26 | mJy/beam | 2 | 503.1 $\pm$ 26 |
| Source A mass (150-70 K) | 146 to 312 | not stated | Msun | 3 | our derived mass for source A is between 312 and 146  M$_{\odot}$ |
| Fragment mass range | 14 to 312 | not stated | Msun | 3 | source masses ranging from 14 M$_{\odot}$ to 312 M$_{\odot}$ |
| Field strength range, three CF versions | 0.2 to 7 | not stated | mG | 4 | we obtained estimations of the magnetic field between 0.2 to 7 mG for our 4 regions |
| Fractional polarization range | 0.03 to 22 | not stated | % | 1 | fractional polarization levels between 0.03% to 22% |
| Source A fraction of total flux | 51 | not stated | % | 2 | source A dominates the flux distribution with a 51% of the total flux |

## Qualitative findings

- Smooth, ordered field across the fragmented filament, with ~90 deg changes near source A and D1  
  > "for source A, there is a $\sim$90$^{\circ}$ change in orientation to the west of the clump" (THE MAGNETIC FIELD MORPHOLOGY)

## Claim tuples

- H: Are the W43-MM1 fragments magnetically supported against gravity? | E: Mass-to-flux ratios from CF field strengths and column densities | R: All fragments highly super-critical | F: Field is not strong enough to support them; gravity dominates | **supported**
- H: Is W43-MM1 highly fragmented with a very massive source A? | E: Continuum extraction and mass estimates | R: 15 fragments, source A 146-312 Msun | F: Highly fragmented filament dominated by source A | **supported**
- H: Is the field dragged by gravity? | E: Field morphology and polarized intensity near source A | R: Field lines bent toward dust peak, polarized intensity drops | F: Suggests gravity pulls field lines | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): CF method assumptions; EVPA dispersion exceeds 25 deg in 2 of 4 regions  
  > "2 out of 4 of our regions have EVPA dispersions larger than the $25^{\circ}$ limit suggested by (cite: Ostriker2001)" (THE MAGNETIC FIELD MORPHOLOGY)
- Limitation (authors): Fragment sizes exceed Jeans lengths, so gravitational instability cannot be concluded  
  > "Thus, we cannot conclude what fraction of these fragments are gravitationally unstable from these data alone." (SUMMARY AND DISCUSSION)
- Caveat (inferred, ours): Source A temperature assumption drives mass by factor ~5
- Caveat (inferred, ours): Single dish line width applied to small-scale regions
- Caveat (inferred, ours): No uncertainty estimates on fields
- Caveat (inferred, ours): Inconsistent source counts (14 vs 15)
- Caveat (inferred, ours): No line data to confirm kinematics

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Project code and imaging parameters
- Missing: getsources settings
- Missing: Region definitions and polarization debiasing
- Data volume (inferred): ~10-50 GB (single Band 6 polarization session, 2 executions)
- Score (inferred): 3/5, Calibration sources and main imaging choices are given, but many imaging and extraction parameters are missing and no project code is printed.
- Rediscovery candidate: no, Project code not printed in paper and several parameters missing, though data are probably public.

## Links

- Method: Menshchikov2012 (getsources algorithm)
- Method: Crutcher2004 (CF and mass-to-flux formulae)
- Companion: Sridharan2014 (SMA polarization study of W43-MM1)
- Companion: Louvet2014 (PdBI 1 mm results)

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2013.1.00725.S"
 ],
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

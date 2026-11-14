# The Sun at millimeter wavelengths. III. Impact of the spatial resolution on solar ALMA observations

`2021A&A...656A..68E` | Astronomy and Astrophysics 2021 | first author: Eklund, Henrik | arXiv: 2109.13826 | DOI: 10.1051/0004-6361/202140972

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: sun, stellar_physics
- Question: How does limited spatial resolution (ALMA array configurations C1-C7, bands 3-10) affect the observability of small-scale dynamics in synthetic solar mm observables from a Bifrost model?  
  > "The aims are to perform estimations of the observability of the small-scale dynamics as a function of spatial resolution for regions with different characteristic magnetic field topology" (abstract)
- Target **Bifrost enhanced-network 3D solar model (QS, FS, FP regions)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00423.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- External data: Standard continuum central frequencies for bands 4, 8, 9, 10 (Table 6.1, ALMA Technical Handbook cycle 8)  
  > "the central frequencies were taken to be those of the standard continuum exemplary values (Table 6.1 in the technical handbook for ALMA cycle 8" (2.2 Brightness temperature maps at mm wavelengths corresponding to ALMA observations) [from (cite: ALMA_Tech_Hand_8.3)]
- External data: Observed band 3 brightening-event ΔTb distributions, to which the correction was applied  
  > "The distributions of the observed $\Delta T_\mathrm{b}$ of the brightening events reported in (cite: 2020A&A...644A.152E) are shown in Fig. [11](#fig:histograms_b3_obs_appli)" (4.4 Comparison with observations) [from (cite: 2020A&A...644A.152E)]
- Simulation/model as data: Bifrost 3D radiation-MHD model, 24x24x17 Mm box, 48 km horizontal spacing, ~1 hr at 1 s cadence, 50 G unsigned photospheric field; first 200 s excluded  
  > "The simulation box extends $24$ Mm in horizontal directions ($x, y$) and $17$ Mm in vertical direction ($z$)." (2.1 3D magnetohydrodynamic simulations); "The first $200$ s of the simulation were excluded from the analysis to ensure that a quasi-equilibrium state was reached." (2.1 3D magnetohydrodynamic simulations)

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

- task: CASA simobserve used to build synthetic observations; clean beams extracted and used as 2D convolution kernels  
  > "The clean beams were then extracted from the resulting measurement sets of the synthetic observations and were used as kernels in 2D convolution of the respective brightness temperature maps." (2.3 Spatial resolution of ALMA observations)
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

- Same Bifrost enhanced-network model setup as earlier works  
  > "The same model was used in (cite: 2020A&A...635A..71W) to study the diagnostic potential of ALMA observations of the Sun" (2.1 3D magnetohydrodynamic simulations) [from (cite: 2020A&A...635A..71W); (cite: 2021RSPTA.37900185E); (cite: 2016A&A...585A...4C)]
- Brightening event ΔTb detection and FWHM lifetime measure following earlier work  
  > "An indication of the lifetime of the events is provided by the FWHM of the $\Delta T_\mathrm{b}$ peak (cite: 2020A&A...644A.152E)." (3.5 Degradation of Tb excess signatures of dynamic events) [from (cite: 2020A&A...644A.152E)]

### Not stated but needed to reproduce (our reading)

- simobserve parameters (CASA version, hour angle/declination, integration, input model setup) used to derive clean beams
- Exact pixel coordinates of the QS, FS and FP regions
- Whether the beam kernel is Gaussian or the actual PSF main lobe and how it was fit
- Bifrost snapshot file identifiers and ART version/settings
- Detection algorithm for peaks and minima beyond the ΔTb>20 K threshold
- Fit method for the linear relations (weighting) and bin handling
- How the 'gray circle' exclusion of events was decided

## Analysis recipe

1. **Compute synthetic mm brightness temperature maps**: Column-wise LTE radiative transfer with ART on Bifrost; ten frequencies per band averaged; Rayleigh-Jeans conversion to Tb  
  > "The intensities at mm wavelenghts are obtained by solving the radiative transfer equation column-wise throughout the FOV, using the advanced radiative transfer (ART) code" (2.2 Brightness temperature maps at mm wavelengths corresponding to ALMA observations)
   - software: ART
   - parameter: Ten equidistant frequencies per receiver band, averaged  
  > "with ten frequencies equidistantly distributed across the spectral range of each receiver band" (2.2 Brightness temperature maps at mm wavelengths corresponding to ALMA observations)
   - assumption: LTE in radiation formation  
  > "LTE conditions in the formation of the radiation are assumed" (2.2 Brightness temperature maps at mm wavelengths corresponding to ALMA observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive clean beams for configurations C1-C7**: Synthetic observations with simobserve, Sun placed near zenith, beam extracted  
  > "As a first approximation, we placed the Sun at an angle close to zenith, which resulted in a slightly eccentric clean beam." (2.3 Spatial resolution of ALMA observations)
   - software: CASA
   - parameter: Position angle fixed at 80 degrees  
  > "the position angle was set to a constant value (of 80 degrees" (4.3 Eccentricity of clean beams)
   - assumption: Best case: perfectly sampled observation, no noise or atmosphere  
  > "corresponds to a perfectly sampled observation." (2.3 Spatial resolution of ALMA observations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Degrade maps and analyze formation heights, Tb distributions, spatial and temporal power**: 2D convolution with clean beams; tau=1 heights; radially averaged FFT power spectra; temporal power with linear detrend and tapered cosine window  
  > "The power spectra were calculated using radially averaged 2D fast Fourier transform (FFT) on the detrended (linear) brightness temperature maps over the entire FOV" (3.4 Spatial power distributions)
   - parameter: Analysis time range t=1000-2000 s for Tb and formation heights; 1550-1750 s for spatial power  
  > "for the time range $t=1000$ – $2000$ s" (3.3 Brightness temperature distributions)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive ΔTb conversion between degraded and original resolution**: Detect brightening peaks (ΔTb>20 K) at all locations in QS/FS/FP; bin degraded ΔTb; median and ±1σ fitted linearly: ΔTb,org = κ ΔTb,deg + μ  
  > "All instances of transient brightening events with $\Delta$T$_\mathrm{b} > 20$ K are considered, well below what is reported for observed brightening events so far." (3.5 Degradation of Tb excess signatures of dynamic events)
   - parameter: Bins 0.02-0.2, 0.2-0.4, ..., 1.5-2.0 kK then 0.5 kK width  
  > "the median and standard deviation values were calculated in the bins at degraded resolution of $\{0.02$ – $0.2$, $0.2$ – $0.4$, $0.4$ – $0.6$" (3.5 Degradation of Tb excess signatures of dynamic events)
   - assumption: Base temperature is hottest of local pre/post minima (conservative)  
  > "the base temperature of the specific event was defined as the hottest of the local pre- and post-minima." (3.5 Degradation of Tb excess signatures of dynamic events)
   - fitting: Linear fit to binned medians and ±1σ  
  > "the median values and the plus/minus one standard deviation values can be reasonably well estimated by a linear fit" (3.5 Degradation of Tb excess signatures of dynamic events)
   - validation: Applied to observed band 3 C3 event distributions of Eklund et al. 2020  
  > "The peak of the resulting distribution of corrected $\Delta T_\mathrm{b}$ is shifted by about $1000$ K from around $650$ K to $1750$ K for the INW events" (4.4 Comparison with observations)

## Software

- **Bifrost** : 3D radiation-MHD solar atmosphere model  
  > "A solar atmospheric numerical 3D model from the radiation-magnetohydrodynamic code Bifrost" (2.1 3D magnetohydrodynamic simulations)
- **ART** : Radiative transfer to compute mm intensities  
  > "using the advanced radiative transfer (ART) code" (2.2 Brightness temperature maps at mm wavelengths corresponding to ALMA observations)
- **CASA (simobserve)** : Synthetic ALMA observations to obtain clean beams  
  > "were constructed using the simobserve[^3] task included in the Common Astronomy Software Applications (CASA)" (2.3 Spatial resolution of ALMA observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Band 3 QS mean Tb at original resolution | 6346 | not stated | K | 3 | The average value of the $T_\mathrm{b}$ distribution at the original resolution of band 3 is $6346$ K in the QS region |
| Band 6 QS mean Tb at original resolution | 5254 | not stated | K | 3 | $5254$ K in the QS region, $6845$ K in the FS region, and $7417$ K in the FP region |
| Example event ΔTb at original vs C3 resolution (band 3 QS) | over 3200 K original; ~290 K at C3; 240 K at C1 | not stated | K | 4 | only approximately $290$ K at the resolution of array configuration C3 and $240$ K at C1. |
| Corrected original ΔTb for 1.2 kK event, band 3 QS C3 | 2.78 | +1.51/-1.92 | kK | 4 | a resulting estimated temperature of $T_\mathrm{b,ori}=2.78^{+1.51}_{-1.92}$ kK |
| Mean QS formation height band 10 / 6 / 3 | 0.6 / 0.9 / 1.3 | not stated | Mm | 3 | The average formation height increases with wavelength from $0.6$ Mm at band $10$, to $0.9$ Mm at band $6$ to $1.3$ Mm at band $3$ in the simulated QS region. |
| Shift of peak of corrected ΔTb distribution of observed INW events | 650 to 1750 | not stated | K | 4 | from around $650$ K to $1750$ K for the INW events and about $400$ K from around $550$ K to $950$ K for the NW events |

## Qualitative findings

- Limited resolution reduces Tb excess amplitudes and shifts peak times by up to tens of seconds; wider configurations are preferable.  
  > "even shifts in the times at which the peaks occur of up to tens of seconds" (abstract)

## Claim tuples

- H: Does limited resolution suppress observable amplitudes of small-scale brightening events? | E: Degrade synthetic Tb maps to C1-C7 beams and compare ΔTb of detected peaks | R: Majority of peaks underestimated, e.g. 3200 K to ~290 K at C3 | F: Amplitudes are severely reduced at compact configurations, with broad uncertain correction factors | **supported**
- H: Which configuration is needed to study subarcsecond structure? | E: Power spectra of degraded maps | R: Band 6 C3 at limit; C4+ improves; band 3 needs C5+ | F: Wider configurations needed | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Full artificial measurement-set imaging with noise and atmosphere rejected as computationally expensive and blending resolution with imaging algorithm effects  
  > "This computationally expensive approach would blend the effect of the overall angular resolution with the specifics of the employed imaging algorithm and the assumed noise properties." (4.2 Imaging with ALMA)
- How they decided it was enough: _not stated_
- Limitation (authors): Best-case scenario without noise, atmosphere, imaging artifacts; static slightly eccentric beam; correction factors not for one-to-one correction  
  > "the distributions are not intended for performing one-to-one corrections of specific events in observational data." (3.5 Degradation of Tb excess signatures of dynamic events)
- Caveat (inferred, ours): Single simulation model; transferability to other targets is assumed
- Caveat (inferred, ours): Convolution with clean beam ignores missing short spacings, noise and deconvolution effects
- Caveat (inferred, ours): Uncommissioned bands use assumed frequencies

## Reproducibility

- Data public (paper): Bifrost model described as publicly available in a cited earlier work; ART code on GitHub/Zenodo  
  > "used the same publicly available Bifrost-enhanced network model" (4.5 Comparison with previous studies of synthetic observables)
- Products in archive: _not stated_
- Code: ART code available at github.com/SolarAlma/ART (Zenodo DOI given)  
  > "ART: Advanced (and fast!) Radiative Transfer code for Solar Physics (https://github.com/SolarAlma/ART)." (References)
- Missing: simobserve settings
- Missing: Region pixel definitions
- Missing: Event-detection code
- Data volume (inferred): Bifrost snapshots ~ tens of GB; no ALMA data processing needed
- Score (inferred): 3/5, Public model and ART code, but beam-generation and event-detection details are unstated.
- Rediscovery candidate: no, Mainly simulation-based with incomplete recipe; ALMA data not directly analyzed.

## Links

- Method: (cite: art_2021) (ART radiative transfer code)
- Companion: (cite: 2020A&A...635A..71W) (Paper I of series)
- Companion: (cite: 2020A&A...644A.152E) (Paper II of series; brightening event detection)
- Related: SolarALMA

## Checks

```json
{
 "quotes": 40,
 "quotes_ok": 40,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 28,
  "rate": 0.378
 },
 "evidence_ok": true
}
```

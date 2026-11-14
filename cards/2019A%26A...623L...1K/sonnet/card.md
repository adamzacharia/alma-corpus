# Detection of highly excited OH towards AGB stars. A new probe of shocked gas in the extended atmospheres

`2019A&A...623L...1K` | Astronomy and Astrophysics 2019 | first author: Khouri, T. | arXiv: 1902.11033 | DOI: 10.1051/0004-6361/201935049

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, astrochemistry
- Question: Are highly excited OH Lambda-doubling lines detectable in the extended atmospheres of O-rich AGB stars, and what are their excitation and column density?  
  > "We report the detection and investigate the properties of high-excitation $\Lambda$-doubling line emission of hydroxyl (OH)." (abstract)
- Target **W Hya**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **R Dor**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **IK Tau**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00004.S, 2017.1.00075.S, 2016.1.00374.S, 2016.A.00029.S, 2017.1.00582.S, 2013.1.00166.S
- bands: Bands 3, 4, 6, 7  
  > "to resolve the O-rich AGB stars W Hya, R Dor, $o$ Ceti, and R Leo in ALMA Bands 4 and 6" (Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: <30 mas for the main projects; archival typically lower  
  > "using ALMA configurations that obtained an angular resolution $<30$ mas" (Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2015-08 to 2018-01 (Table 3)  
  > "17-10-18" (Table 3)
- pi or archival as stated: _not stated_
- Line: OH Lambda-doubling hyperfine main lines, e.g. v=0, N_J=13_25/2 (~130.1 GHz)
- Line: CO v=1, J=3-2 (342.648 GHz)
- Line: H2O v2=1, 8(8,1)-9(7,2) and 8(8,0)-9(7,3) (not stated)
- External data: OH line frequencies, line strengths and partition function from JPL catalogue / Drouin 2013  
  > "we use the partition function given by (cite: Drouin2013)" (4.1 W Hya) [from (cite: Pickett1998; Drouin2013)]
- External data: v_LSR of W Hya 39.2 km/s  
  > "equal to 39.2 and 8.5 km/s for W Hya (cite: Vlemmings2017)" (4.4 Transition frequencies) [from (cite: Vlemmings2017)]
- External data: CO abundance relative to H2 of 4e-4  
  > "Considering a CO abundance relative to H$_2$ of $4 \times 10^{-4}$ (cite: Willacy1997)" (Comparison to H2O and CO lines) [from (cite: Willacy1997)]

## Processing

### Calibration

- pipeline or manual: Observatory-provided calibration/pipeline scripts, then self-calibration on stellar continuum  
  > "Generally, the observatory-provided calibration or pipeline scripts were used, after which the data were self-calibrated on the strong stellar continuum." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: continuum self-calibration (parameters not given)  
  > "we applied the calibration provided by the observatory followed by continuum self-calibration" (Observations)

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

- Observational set-up and calibration details deferred to forthcoming paper  
  > "The details of the observational set-up and calibration will be presented in a forthcoming paper (Vlemmings et al., in prep.)." (Observations) [from Vlemmings et al., in prep.]
- R Dor v_LSR of 8.5 km/s  
  > "R Dor (Khouri et al., *in prep.*), respectively." (4.4 Transition frequencies) [from Khouri et al., in prep.]

### Not stated but needed to reproduce (our reading)

- Imaging parameters (weighting, robust, cell, image size, deconvolver)
- Continuum subtraction and line-free channels
- Self-calibration solution intervals
- Extraction region definitions/positions for small and large regions
- Stellar distances and coordinates
- Flux scale uncertainty
- Spectral setups per project

## Analysis recipe

1. **Calibrate and self-calibrate**: Observatory calibration followed by continuum self-calibration  
  > "we applied the calibration provided by the observatory followed by continuum self-calibration" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure OH line fluxes**: Gaussian fits to spectra from small and large regions; numerical integration for v=1, 17_35/2 lines  
  > "The line fluxes were measured by fitting Gaussian functions to the observed spectra." (4.1 W Hya)
   - software: CASA
   - parameter: small region ~6.1e-3 arcsec^2; large region ~3.1e-2 arcsec^2  
  > "a small region (${\sim 6.1 \times 10^{-3}~{\rm arcsec}^2}$, shown in Fig. [2](#fig:linesWHya)) centred on the emission peak" (4.1 W Hya)
   - fitting: Gaussian line fits  
  > "The line fluxes were measured by fitting Gaussian functions to the observed spectra." (Observational results, W Hya)
   - validation: _not stated_
3. **Population diagram for OH**: Rotation diagram giving Trot and column density, assuming optically thin LTE emission  
  > "allows us to obtain good constraints on the column density and rotational temperature using a population diagram (cite: Goldsmith1999)" (4.1 W Hya)
   - assumption: optically thin, single-temperature LTE gas  
  > "our assumption of a single-temperature gas and LTE excitation" (4.2 R Dor)
   - fitting: straight-line fit to population diagram  
  > "The derived values are not as well constrained as for W Hya because the detected lines span a smaller range in excitation energy and are not as well fitted by a straight line in the population diagram." (Observational results, R Dor)
   - validation: Optical depths estimated and line-pair flux ratios compared to LTE expectation  
  > "we find all lines to be optically thin ($\tau \lesssim 0.05$), as assumed in our analysis" (4.3 Optical depths and line-flux ratios)
4. **CO column density and CO/OH ratio**: Gaussian approximation of CO v=1 J=3-2 line in small region, optically thin, Tex 2000±1000 K  
  > "We estimate the CO column density assuming optically thin emission and considering an excitation temperature of $2000 \pm 1000$ K." (Comparison to H2O and CO lines)
   - assumption: CO/H2 = 4e-4  
  > "Considering a CO abundance relative to H$_2$ of $4 \times 10^{-4}$ (cite: Willacy1997)" (Comparison to H2O and CO lines)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compare observed and predicted OH frequencies**: Gaussian fits for line centres, v_LSR from CO modelling, compare with JPL  
  > "We derive the observed central frequencies by fitting Gaussian functions to the observed lines." (4.4 Transition frequencies)
   - parameter: v_LSR uncertainty 1.5 km/s; sigma floored at channel width  
  > "When $\sigma$ was smaller than the channel width, it was set to the channel width." (4.4 Transition frequencies)
   - fitting: Gaussian  
  > "we approximate the CO line in the small region by a Gaussian line with the observed peak value (140 mJy)" (Observational results, W Hya, Comparison to H$_2$O and CO lines)
   - validation: _not stated_

## Software

- **CASA** : Image-plane Gaussian fit of R Dor OH emission region  
  > "fitting it in the image plane using the Common Astronomy Software Applications (CASA) package (cite: McMullin2007)" (4.2 R Dor)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| OH rotational temperature, W Hya small region | 2472 | 184 | K | 3 | we find rotational temperatures for the small and large regions of $2472 \pm 184$ K and $2665 \pm 264$ K |
| OH rotational temperature, W Hya large region | 2665 | 264 | K | 3 | we find rotational temperatures for the small and large regions of $2472 \pm 184$ K and $2665 \pm 264$ K |
| OH column density, W Hya small region | 3.0e19 | 1.0e19 | cm^-2 | 3 | ${(3.0 \pm 1.0) \times 10^{19}~{\rm cm}^{-2}}$ and ${(1.4 \pm 0.3) \times 10^{19}~{\rm cm}^{-2}}$ |
| OH column density, W Hya large region | 1.4e19 | 0.3e19 | cm^-2 | 3 | ${(3.0 \pm 1.0) \times 10^{19}~{\rm cm}^{-2}}$ and ${(1.4 \pm 0.3) \times 10^{19}~{\rm cm}^{-2}}$ |
| OH rotational temperature, R Dor | 2560 | 650 | K | 3 | we find a rotational temperature of $2560 \pm 650$ K and a column density of $\sim 2 \times 10^{19}$ cm$^{-2}$ |
| CO column density, W Hya small region | 4e20 | +3/-1 e20 | cm^-2 | 4 | We find $N_{\rm CO} \sim 4^{+3}_{-1} \times 10^{20}$ cm$^{-2}$ |
| CO-to-OH column density ratio | ~15 | not stated | dimensionless | 4 | tentative CO-to-OH column density ratio of $\sim 15$ in the small region |
| R Dor OH emission FWHM | ~70 | 20 | mas | 2 | we find the emission region to have a FWHM of $\sim 70 \pm 20$ mas |

## Qualitative findings

- OH lines are optically thin with no maser effect and arise very close to the star; observed frequencies deviate from JPL predictions increasingly with frequency.  
  > "The OH lines are produced very close to the central stars and seem optically thin and with no maser effect." (abstract)

## Claim tuples

- H: Highly excited OH Lambda-doubling lines are present in AGB atmospheres | E: Search of ALMA data for several O-rich AGB stars | R: Line pairs detected towards W Hya, R Dor and IK Tau | F: OH is a new probe of shocked inner atmosphere gas | **supported**
- H: OH excitation is characterised by high temperature and column | E: Population diagram analysis | R: Trot ~2500 K and N ~1e19 cm^-2 | F: Hot, dense gas close to star | **supported**
- H: Observed OH frequencies match predicted ones | E: Compared Gaussian-fit line centres to JPL | R: Offsets exceed uncertainties and grow with frequency | F: Could improve OH Hamiltonian, but caveats from velocity and absorption | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): CO/OH results are tentative due to simple methods; non-LTE modelling needed  
  > "These results should be considered tentative because of the simple methods employed." (abstract)
- Caveat (inferred, ours): LTE single-temperature assumption with absorption against stellar disk biases column densities
- Caveat (inferred, ours): Frequency offsets depend on assumed v_LSR
- Caveat (inferred, ours): Different epochs and pulsation phases are mixed

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging and self-calibration details
- Missing: Region definitions
- Missing: Spectral setups
- Data volume (inferred): Several hundred GB across six projects
- Score (inferred): 3/5, Archival ALMA data and simple analysis, but processing details deferred to unpublished paper.
- Rediscovery candidate: no, Imaging and extraction details are missing.

## Links

- Method: (cite: Goldsmith1999) (population diagram method)
- Companion: Vlemmings et al., in prep. (observational set-up and calibration)

## Checks

```json
{
 "quotes": 48,
 "quotes_ok": 48,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 6,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2015.1.00166.S"
 ],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 27,
  "rate": 0.355
 },
 "evidence_ok": true
}
```

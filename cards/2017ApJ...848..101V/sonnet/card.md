# A <SUP>13</SUP>CO Detection in a Brightest Cluster Galaxy

`2017ApJ...848..101V` | The Astrophysical Journal 2017 | first author: Vantyghem, A. N. | arXiv: 1709.09679 | DOI: 10.3847/1538-4357/aa8fd0

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: galaxy_clusters_and_sz, milky_way_ism, nearby_galaxies
- Question: Can 13CO(3-2) emission in a BCG give an LTE molecular gas mass and a CO-to-H2 conversion factor to test the Galactic value?  
  > "This provides an estimate of the CO-to-H$_2$ conversion factor that can be compared to the Galactic value in order to evaluate previous mass estimates of BCGs." (Introduction)
- Target **BCG of RXJ0821+0752**: coordinates RA 08:21:02.258, Dec +07:51:47.28  
  > "(RA: 08:21:02.258, Dec: +07:51:47.28)" (Observations and Data Reduction); "At the redshift of RXJ0821+0752 (cite: Crawford95), the angular scale is $1''=2.0\rm\; kpc$ and the luminosity distance is $510\rm\; Mpc$." (Introduction); z/distance z=0.109; D_L = 510 Mpc; 1''=2.0 kpc  
  > "(RA: 08:21:02.258, Dec: +07:51:47.28)" (Observations and Data Reduction); "At the redshift of RXJ0821+0752 (cite: Crawford95), the angular scale is $1''=2.0\rm\; kpc$ and the luminosity distance is $510\rm\; Mpc$." (Introduction); distance from redshift from Crawford95; cosmology H0=70, Om=0.3, OL=0.7  
  > "(RA: 08:21:02.258, Dec: +07:51:47.28)" (Observations and Data Reduction); "At the redshift of RXJ0821+0752 (cite: Crawford95), the angular scale is $1''=2.0\rm\; kpc$ and the luminosity distance is $510\rm\; Mpc$." (Introduction)

## Data provenance

- ALMA projects: 2016.1.01269.S, 2011.0.00735.S, 2012.1.00988.S
- bands: Band 3 and Band 7  
  > "was observed by ALMA Band 3 on 2016 Oct 30 and Nov 4 and Band 7 on 2016 Oct 1" (Observations and Data Reduction)
- frequencies and spectral setup: CO(1-0) 103.848 GHz, CO(3-2) 311.528 GHz, 13CO(3-2) 297.827 GHz (redshifted); FDM 1.875 GHz bandwidth, 488 kHz resolution for CO lines; continuum basebands TDM 2 GHz, 15.625 MHz  
  > "These observations covered the redshifted CO(1-0) and CO(3-2) lines at $103.848\rm\; GHz$ and $311.528\rm\; GHz$, respectively." (Observations and Data Reduction); "providing a 1.875 GHz bandwidth with 488 kHz frequency resolution" (Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 18-1124 m (Band 3), 15-3247 m (Band 7); 40 antennas  
  > "The observations used 40 antennas with baselines ranging from $18-1124\rm\; m$ for Band 3 and $15-3247\rm\; m$ for Band 7." (Observations and Data Reduction)
- angular resolution: CO(1-0) 0.61''x0.59''; CO(3-2) and 13CO(3-2) 0.21''x0.165''  
  > "The final CO(1-0) data cube had a synthesized beam of $0.61''\times 0.59''$ (P.A. $-70.4^{\circ}$)" (Observations and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: RMS 0.5, 1.1, 0.3 mJy/beam in line-free channels (CO(1-0), CO(3-2), 13CO(3-2))  
  > "The RMS noise in the line-free channels were $0.5$, $1.1$, and $0.3\rm\; mJy~{\rm beam}^{-1}$, respectively." (Observations and Data Reduction)
- time on source: 86.7 min at CO(1-0); 22.7 min at CO(3-2)  
  > "The total on-source integration time was 86.7 minutes at CO(1-0) and 22.7 minutes at CO(3-2)" (Observations and Data Reduction)
- observing dates: Band 3 2016 Oct 30 and Nov 4; Band 7 2016 Oct 1  
  > "was observed by ALMA Band 3 on 2016 Oct 30 and Nov 4 and Band 7 on 2016 Oct 1" (Observations and Data Reduction)
- pi or archival as stated: _not stated_
- Line: CO 1-0 (103.848 GHz (observed))
- Line: CO 3-2 (311.528 GHz (observed))
- Line: 13CO 3-2 (297.827 GHz (observed))
- Other facility **HST WFPC2 F606W**: optical image compared with CO(3-2) contours  
  > "Contours of the CO(3-2) emission are overlaid on an *HST* WFPC2 F606W image in Fig. [4](#fig:hst)." (Gas Distribution)
- External data: IRAM-30m CO(1-0) flux 9.9±1.0 Jy km/s for comparison  
  > "IRAM-30m single dish measurement of $9.9\pm1.0\hbox{$\rm\; Jy\rm\; km\rm\; s^{-1}\,$}$ (cite: Edge01; Edge03)" (Spectra) [from (cite: Edge01; Edge03)]
- External data: Galactic alpha_CO = 4.3 and X_CO = 2e20  
  > "$\alpha_{\rm CO}=4.3 \hbox{$\rm\thinspace M_{\odot}$}(\hbox{$\rm\; K\rm\; km\rm\; s^{-1}\rm\; pc^{2}\,$})^{-1}$ (cite: Bolatto13)" (CO-to-H$_2$ Conversion Factor) [from (cite: Bolatto13)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline reduction scripts  
  > "The observations were calibrated in casa version 4.7.0 (cite: casa) using the pipeline reduction scripts." (Observations and Data Reduction)
- casa version: CASA 4.7.0  
  > "The observations were calibrated in casa version 4.7.0 (cite: casa) using the pipeline reduction scripts." (Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: not performed (faint nuclear continuum)  
  > "Additional phase self-calibration could not be performed because of the very faint nuclear continuum source." (Observations and Data Reduction)

### Imaging

- task: uvcontsub and clean  
  > "Continuum-subtracted data cubes were created using uvcontsub and clean." (Observations and Data Reduction)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 2  
  > "Images of the line emission were reconstructed using Briggs weighting with a robust parameter of 2." (Observations and Data Reduction)
- uv taper: uv taper smoothing CO(3-2) and 13CO(3-2) on scales below 0.1 arcsec  
  > "An additional $uv$ tapering was used to smooth the CO(3-2) and $^{13}$CO(3-2) images on scales below 0.1 arcsec." (Observations and Data Reduction)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: CO(3-2) smoothed to 13CO(3-2) beam; for spatially integrated spectra 3-2 images smoothed to CO(1-0) resolution  
  > "the CO(3-2) data cube was smoothed to match the $^{13}$CO(3-2) synthesized beam of $0.21''\times 0.165''$ (P.A. $37.2^{\circ}$)" (Observations and Data Reduction)
- final beam: CO(1-0) 0.61''x0.59'' PA -70.4; CO(3-2)/13CO(3-2) 0.21''x0.165'' PA 37.2  
  > "The final CO(1-0) data cube had a synthesized beam of $0.61''\times 0.59''$ (P.A. $-70.4^{\circ}$)" (Observations and Data Reduction)
- final rms: 0.5, 1.1, 0.3 mJy/beam  
  > "The RMS noise in the line-free channels were $0.5$, $1.1$, and $0.3\rm\; mJy~{\rm beam}^{-1}$, respectively." (Observations and Data Reduction)

### Inherited from earlier work

- 3-sigma flux upper-limit formula follows McNamara & Jaffe 1994 but uses flux  
  > "The $3\sigma$ upper limits on integrated flux were computed following (cite: mcn94), but using flux instead of intensity" (Gas Distribution) [from (cite: mcn94)]
- 13CO column density formula  
  > "can be estimated from the intensity of a single transition $^{13}$CO($J\rightarrow J-1$) according to (cite: Mangum15)" (CO-to-H$_2$ Conversion Factor) [from (cite: Mangum15)]
- Abundance ratios [12CO]/[13CO]=50, [12CO]/[H2]=1e-4  
  > "Assuming the abundance ratios $[^{12}{\rm CO}]/[^{13}{\rm CO}] = 50$ and $[^{12}{\rm CO}]/[{\rm H}_2] = 10^{-4}$ (cite: Dickman78; Frerking82)" (CO-to-H$_2$ Conversion Factor) [from (cite: Dickman78; Frerking82)]
- CO line luminosity definition  
  > "It is defined as (cite: Solomon05)" (Spectra) [from (cite: Solomon05)]

### Not stated but needed to reproduce (our reading)

- Number of tclean/clean iterations, threshold and masks
- Line-free channels used for uvcontsub and continuum fit order
- Flux calibrator and flux scale uncertainty
- Pipeline version
- Image size and cell size
- Exact extraction polygon for the region tracing 13CO
- Details of the Monte Carlo and Gaussian fitting method (fitter, errors)
- Whether the 2011/2012 archival projects were used and how

## Analysis recipe

1. **Calibrate and image cubes**: CASA pipeline calibration, uvcontsub, clean with Briggs robust 2, uv taper, binning to 3, 5, 16 km/s channels  
  > "The CO(1-0), CO(3-2), and $^{13}$CO(3-2) images were binned to $3$, $5$, and $16\hbox{$\rm\; km\rm\; s^{-1}\,$}$ velocity channels, respectively." (Observations and Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: CO(1-0) flux compared with IRAM-30m  
  > "is consistent within $2\sigma$ of the IRAM-30m single dish measurement" (Spectra)
2. **Extract and fit spectra**: Integrated spectrum from 6.8''x5'' box and from 13CO-tracing region, converted to brightness temperature, fitted with Gaussians; luminosities L'_CO computed  
  > "A spatially integrated spectrum was extracted for each spectral line from a $6.8''\times 5''$ ($13.6\times 10\rm\; kpc$) box encompassing all of the significant line emission." (Spectra)
   - parameter: second 13CO component at -80 km/s below 3 sigma excluded  
  > "the significance of the second component is below $3\sigma$, so has not been included in these fits" (Spectra)
   - fitting: single Gaussian per spectrum (two for 12CO in the 13CO-tracing region)  
  > "The spectra are all best fit by a single Gaussian velocity component." (Spectra)
   - validation: _not stated_
3. **Map integrated flux**: Gaussian fits per pixel after beam averaging; Monte Carlo with 1000 iterations, 3 sigma detection  
  > "The significance of the line was tested using a Monte Carlo simulation with 1000 iterations, with a detection requiring a significance of $3\sigma$." (Gas Distribution)
   - fitting: one or two Gaussians per pixel  
  > "fitting a one or two Gaussian components to the spectrum of each pixel after averaging over the size of the beam" (Gas Distribution)
   - validation: _not stated_
4. **Line ratios and excitation temperature**: r31 and R32 from peak temperatures; Tex and filling factor from Rayleigh-Jeans equation assuming optically thick 12CO and LTE  
  > "The ratio of CO (3-2)/(1-0) brightness temperatures for the $^{13}$CO-bright component, $0.71\pm0.14$, implies an excitation temperature of $T_{\rm ex}\approx 15\rm\; K$." (CO (3-2)/(1-0))
   - assumption: optically thick 12CO, same filling factor for 1-0 and 3-2, LTE  
  > "We also assume that the CO(1-0) and CO(3-2) emission originate from the same regions in the molecular clouds, so the area filling factors are the same." (CO (3-2)/(1-0))
   - fitting: _not stated_
   - validation: _not stated_
5. **LTE 13CO column density, mass and alpha_CO**: 13CO column from optical depth and Tex; N(H2) via abundances; mass = 1.36 m_H2 N A_source; alpha_CO = M/L'_10 with L'_10 = L'_32/r31  
  > "The total molecular gas mass is then computed from $M_{\rm mol} = 1.36 m_{\rm H_2} N_{\rm H_2} A_{\rm source}$" (CO-to-H$_2$ Conversion Factor)
   - parameter: Tex=15 K, filling factor 0.1, 13W32=22.8 K km/s, A_reg=11.2 kpc^2  
  > "For $T_{\rm ex}=15\rm\; K$, $\Phi_A=0.1$, and $^{13}W_{32}=22.8\hbox{$\rm\; K\rm\; km\rm\; s^{-1}\,$}$" (CO-to-H$_2$ Conversion Factor)
   - assumption: [12CO]/[13CO]=50, [12CO]/[H2]=1e-4, LTE, 13CO optically thin with finite-opacity correction  
  > "Assuming the abundance ratios $[^{12}{\rm CO}]/[^{13}{\rm CO}] = 50$ and $[^{12}{\rm CO}]/[{\rm H}_2] = 10^{-4}$" (CO-to-H$_2$ Conversion Factor)
   - fitting: _not stated_
   - validation: Optical depth cross-checked with 12CO/13CO ratio method (0.36); repeated for full region  
  > "This method yields an optical depth of $0.36$" (CO-to-H$_2$ Conversion Factor)

## Software

- **CASA** 4.7.0: calibration, uvcontsub, clean  
  > "The observations were calibrated in casa version 4.7.0 (cite: casa) using the pipeline reduction scripts." (Observations and Data Reduction)
- **APLpy** : plotting  
  > "This research made use of APLpy, an open-source plotting package for Python" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 13CO-traced molecular gas mass (LTE) | 2.1e9 | not stated | Msun | 5 | This gives a total molecular gas mass of $2.1\ensuremath{\times 10^{9}}\hbox{$\rm\thinspace M_{\odot}$}$. |
| alpha_CO (13CO-bright component) | 2.26 | not stated | Msun (K km/s pc^2)^-1 | 5 | giving a CO-to-H$_2$ conversion factor of $\alpha_{\rm CO} = 2.26\hbox{$\rm\thinspace M_{\odot}$}(\hbox{$\rm\; K\rm\; km\rm\; s^{-1}\rm\; pc^{2}\,$})^{-1}$ |
| X_CO | 1.04e20 | not stated | cm^-2 (K km/s)^-1 | 5 | $X_{\rm CO}=1.04\ensuremath{\times 10^{20}}\hbox{$\rm\; cm^{-2}\,$}(\hbox{$\rm\; K\rm\; km\rm\; s^{-1}\,$})^{-1}$ |
| Total CO(1-0) flux | 8.06 | 0.08 | Jy km/s | 2 | $8.06\pm0.08$ |
| r31 (13CO-bright component) | 0.71 | 0.15 | dimensionless | 4 | The resulting $r_{31}$ line ratio is $0.71\pm0.15$ for the $^{13}$CO-bright velocity component |
| R32 (13CO-bright, 13CO-tracing region) | 3.32 | 0.66 | dimensionless | 4 | $3.32\pm0.66$ |
| 13CO column density | 1.74e17 | not stated | cm^-2 | 5 | the total $^{13}$CO column density is $1.74\ensuremath{\times 10^{17}}\hbox{$\rm\; cm^{-2}\,$}$ |
| Total molecular gas mass with Galactic factor or alpha scaling | 1.1e10 | not stated | Msun | 5 | the total CO(1-0) luminosity gives a total molecular gas mass of $1.1\ensuremath{\times 10^{10}}\hbox{$\rm\thinspace M_{\odot}$}$ |

## Qualitative findings

- 13CO emission is confined to two bright clumps; the narrow 12CO component matches 13CO while the broad blueshifted wing has no 13CO.  
  > "The detected $^{13}$CO emission is confined entirely to the two bright clumps" (abstract)

## Claim tuples

- H: Is alpha_CO in a BCG consistent with the Galactic value? | E: LTE analysis of 13CO(3-2) with 12CO(3-2) and (1-0) in the 13CO-bright component | R: alpha_CO = 2.26 Msun (K km/s pc^2)^-1 | F: Half the Galactic value, within object-to-object scatter | **partially**
- H: Does 13CO trace all the 12CO gas? | E: Gaussian decomposition of 12CO and 13CO spectra | R: 13CO matches only the narrow component | F: Two distinct 13CO-bright and 13CO-faint components | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Mass traced is only a fraction of total; LTE and abundance assumptions are simplistic  
  > "As a result, this LTE analysis is only sensitive to a fraction of the total molecular gas mass." (CO-to-H$_2$ Conversion Factor)
- Caveat (inferred, ours): alpha_CO depends linearly on assumed abundances, with no uncertainties propagated
- Caveat (inferred, ours): Single object
- Caveat (inferred, ours): No uncertainty on mass or alpha_CO

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Clean parameters and masks
- Missing: Region definitions
- Missing: Fitting code details
- Data volume (inferred): tens of GB
- Score (inferred): 3/5, Data identified, but imaging parameters and uncertainties are incomplete.
- Rediscovery candidate: no, Public status is not stated and the recipe is incomplete.

## Links

- Method: (cite: Mangum15) (13CO column density formula)

## Checks

```json
{
 "quotes": 65,
 "quotes_ok": 65,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 44,
  "rate": 0.603
 },
 "evidence_ok": true
}
```

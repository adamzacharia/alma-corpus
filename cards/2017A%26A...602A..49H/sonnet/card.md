# VALES. II. The physical conditions of interstellar gas in normal star-forming galaxies up to z = 0.2 revealed by ALMA

`2017A&A...602A..49H` | Astronomy and Astrophysics 2017 | first author: Hughes, T. M. | arXiv: 1611.05867 | DOI: 10.1051/0004-6361/201629588

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, milky_way_ism
- Question: What are the gas density and FUV radiation field in normal star-forming galaxies at 0.03<z<0.2, from [CII]/CO(1-0)/FIR PDR modelling, and does it evolve with redshift?  
  > "we study the physical conditions in the interstellar gas for a sample of 27 dusty galaxies at $0.03<z<0.2$ selected from the Valparaíso ALMA Line Emission Survey" (Introduction)
- Target **27 VALES/H-ATLAS galaxies in GAMA 9h field (G09.DR1.xx)**: coordinates Table 1 lists RA/Dec per galaxy  
  > "G09.DR1.12 | 09:09:49 | +01:48:47 | 0.182 | 886.7" (Table 1); "we adopt a $\Lambda$CDM cosmology with $H_0=70$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_{\rm M}=0.27$ and $\Omega_{\Lambda}=0.73$" (Introduction); z/distance z_spec 0.026-0.195; D_L 111.5-958.2 Mpc  
  > "G09.DR1.12 | 09:09:49 | +01:48:47 | 0.182 | 886.7" (Table 1); "we adopt a $\Lambda$CDM cosmology with $H_0=70$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_{\rm M}=0.27$ and $\Omega_{\Lambda}=0.73$" (Introduction); distance from GAMA spectroscopic redshifts; LCDM H0=70  
  > "G09.DR1.12 | 09:09:49 | +01:48:47 | 0.182 | 886.7" (Table 1); "we adopt a $\Lambda$CDM cosmology with $H_0=70$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_{\rm M}=0.27$ and $\Omega_{\Lambda}=0.73$" (Introduction)

## Data provenance

- ALMA projects: 2013.1.00530.S
- bands: Band 3  
  > "The cycle-2 observations taken in Band-3 covered the $^{12}$CO(1–0) emission line" (The sample and data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: ~25 arcsec (60 arcsec primary beam)  
  > "the maximum recoverable angular scales of ALMA in Band-3 are approximately 25$\ensuremath{''}$ (with a 60$\ensuremath{''}$ primary beam)" (The sample and data)
- sensitivity: 2 mJy/beam at 30 km/s  
  > "down to $2$ mJy beam$^{-1}$ at $30$ km s$^{-1}$" (The sample and data)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PI E. Ibar, cycle 1-2 programme  
  > "project 2013.1.00530.S; P.I.: E. Ibar" (The sample and data)
- Line: 12CO J=1-0 (not stated)
- Line: [CII] 158 um (Herschel-PACS) (1900.54 GHz)
- Other facility **Herschel PACS**: [CII] 158um spectroscopy  
  > "The \[Cii\] 158 $\mu$m line observations of our sample are presented in (cite: ibar2015)." (Herschel-PACS [Cii] 158 micron line observations)
- Other facility **Herschel SPIRE, WISE, IRAS**: photometry for FIR luminosity SED fits  
  > "fitting the SED constructed from *Herschel* PACS and SPIRE, *WISE*-22 $\mu$m and *IRAS* photometry" (Ancillary data for far-infrared luminosities)
- External data: [CII] line fluxes and L_FIR, dust temperatures  
  > "We use previously published values of the far-infrared (FIR) luminosity, $L_{\mathrm{FIR}}$" (Ancillary data for far-infrared luminosities) [from (cite: ibar2015)]
- External data: Literature samples and high-z [CII]/CO/FIR data for comparison  
  > "together with the galaxy samples compared in Fig. 3 of (cite: hailey2010), from where this figure is taken" (Comparison with previous studies) [from (cite: hailey2010); (cite: gullberg2015)]
- Simulation/model as data: Kaufman et al. PDR model grids via PDR Toolbox  
  > "the corresponding $G_{0}$ and $n$ values predicted by the PDR model are available online via the ‘Photo Dissociation Region Toolbox’" (Results from PDR modelling)

## Processing

### Calibration

- pipeline or manual: common pipeline developed from standard pipelines in CASA  
  > "using a common pipeline, developed from standard pipelines, for calibration, concatenation and imaging" (The sample and data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto, Mars, Ceres, Titan  
  > "flux calibrators were Callisto, Mars, Ceres and Titan" (The sample and data)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: clean in CASA  
  > "when varying the cube spectral resolution from 20 to 100 km s$^{-1}$ in steps of 10 km s$^{-1}$ with the clean task" (The sample and data)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "manually cleaned to a threshold of 3$\sigma$ and created using natural weighting" (The sample and data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: 256x256 pixels  
  > "The final cubes, of 256$\times$256 pixels in spatial size" (The sample and data)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied  
  > "were corrected for the primary beam" (The sample and data)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Observations, data reduction and CO fluxes detailed elsewhere  
  > "Whereas (cite: villanuevaprep) present the observations, data reduction and analysis in detail for the complete sample" (The sample and data) [from (cite: villanuevaprep)]
- [CII] line measurement  
  > "yet we refer the reader to (cite: ibar2015) for more details" (Herschel-PACS [Cii] 158 micron line observations) [from (cite: ibar2015)]
- Optical-depth/excitation temperature analysis of L[CII]/LCO  
  > "Following the reasoning and methodology of (cite: gullberg2015)" (The origin of the line emission) [from (cite: gullberg2015)]
- No FIR halving correction, following high-z studies  
  > "choosing instead to follow the methodology of (cite: stacey2010a) and (cite: gullberg2015)" (Adjustments to observed quantities) [from (cite: stacey2010a); (cite: gullberg2015)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum subtraction
- Clean mask details, CASA version
- Flux calibration uncertainty
- Exact KDTree grid and chi2 setup
- Table of per-galaxy beam/rms
- Villanueva et al. in prep products

## Analysis recipe

1. **Measure CO(1-0) flux**: Gaussian fit to spectrum, collapse cube over nu_obs±FWHM, Gaussian fit  
  > "collapsing the data cubes between $\nu_{\mathrm{obs}}-\nu_{\mathrm{FWHM}}$ and $\nu_{\mathrm{obs}}+\nu_{\mathrm{FWHM}}$, and fitting these cubes with a Gaussian" (The sample and data)
   - software: CASA
   - parameter: upper limit = 5x RMS at 100 km/s, FWHM 250 km/s  
  > "adopt the limit as 5$\times$ the measured RMS" (The sample and data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Compute L_CO**: Solomon & Vanden Bout formula  
  > "$L_{\mathrm{CO}} = 1.04 \times 10^{-3} S_{\mathrm{CO}}\Delta \mathrm{v}\, \nu_{\mathrm{rest}}(1+z)^{-1}D_{\mathrm{L}}^{2}$" (The sample and data)
   - fitting: _not stated_
   - validation: _not stated_
3. **Excitation temperature/optical depth analysis**: Compare observed L[CII]/LCO with source-function equation varying Tex and tau  
  > "Knowing the $L_{\mathrm{[C{\textsc{ii}}]}}$/$L_{\mathrm{CO}}$ ratio leaves the two excitation temperatures ($T_{\mathrm{ex,[C{\textsc{ii}}]}}$, $T_{\mathrm{ex,CO(1-0)}}$) and two opacities" (3.1 The origin of the line emission)
   - assumption: equal [CII] and CO filling factors; Tex,CO = dust temperature  
  > "under the assumption that the \[Cii\] and CO(1–0) filling factors are equal" (The origin of the line emission)
   - fitting: _not stated_
   - validation: _not stated_
4. **Apply adjustments and fit PDR model**: [CII] scaled to 70% (or 50%) PDR fraction, CO x2; KDTree search with chi2 minimisation to Kaufman PDR grid to get n and G0  
  > "We use a KDTree search coupled with a $\chi^{2}$ minimisation technique to find the closest contour of the models" (Insights)
   - software: PDR Toolbox
   - assumption: each galaxy is a single PDR component; FIR not halved  
  > "where we must assume that each emission component – the \[Cii\] line emission, the CO(1–0) emission, and the far-IR continuum – originates from a single PDR component in our sources." (4 Results from PDR modelling)
   - fitting: chi2 minimisation; bootstrap with 1000 resamplings for errors  
  > "1000 new sets of data points are created by generating random flux values from within the errorbars" (Insights)
   - validation: Comparison with literature samples  
  > "To the first order, our galaxies fall in the region of the parameter space (i.e. $2 \leq \log G_0 \leq 3$ and $3 \leq \log n/\mathrm{cm}^{3} \leq 5$) predominantly populated by normal galaxies and non-starburst nuclei" (5.2 Comparison with previous studies)

## Software

- **CASA** : calibration, concatenation, imaging  
  > "reduced homogeneously within the *Common Astronomy Software Applications*" (The sample and data)
- **PDR Toolbox** : PDR model grids  
  > "available online via the ‘Photo Dissociation Region Toolbox’" (Results from PDR modelling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| mean L[CII]/LCO | 3500 | std 1200 | dimensionless | 2 | average $L_{\mathrm{[C{\textsc{ii}}]}}$/$L_{\mathrm{CO}}$ ratio for our sample is 3500 (median of $\sim$2400) with a standard deviation of 1200 |
| mean log G0 (unadjusted) | 2.63 | 0.32 | dimensionless | 4 | The unadjusted observations yield a mean incident field strength of 2.63$\pm$0.32 and density of 4.00$\pm$0.95 |
| mean log n (standard adjustments) | 4.52 | 0.49 | log cm^-3 | 4 | denser ($\log n =$4.52$\pm$0.49), warmer ($T$=207$\pm$68 K) |
| mean log G0 (standard adjustments) | 2.25 | 0.25 | dimensionless | 4 | ($\log G_{0} =$2.25$\pm$0.25) |

## Qualitative findings

- Galaxies have higher gas density than nearby galaxies, similar to high-z, but evolution likely due to biases  
  > "The apparent evolution most likely arises from a combination of observational biases rather than physical processes" (Conclusions)

## Claim tuples

- H: Do [CII] and CO arise from different excitation conditions? | E: Compare L[CII]/LCO with optical depth/Tex model | R: Tex[CII]>Tex[CO] | F: [CII] optically thin, CO thick | **supported**
- H: Does gas density evolve with redshift? | E: Compare n and G0 with literature using same PDR model | R: n higher than local, like high-z; G0 constant | F: cannot conclude physical evolution | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Equal excitation temperatures rejected as unviable  
  > "such a scenario where both \[Cii\] and CO lines are optically thick with equal excitation temperatures over 50 K is not a viable solution" (The origin of the line emission)
- How they decided it was enough: _not stated_
- Limitation (authors): Only two lines/one ratio used; degeneracies  
  > "the major limitation is the use of only two emission lines – one ratio – as diagnostics" (Conclusions)
- Caveat (inferred, ours): Adjustment factors are assumed, not measured
- Caveat (inferred, ours): Bootstrap ignores correction uncertainties
- Caveat (inferred, ours): Beam-matching of [CII] and CO not addressed

## Reproducibility

- Data public (paper): ALMA project cited; PDR Toolbox online  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00530.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Details of CASA reduction in Villanueva et al. in prep
- Missing: Herschel [CII] and L_FIR from Ibar 2015
- Data volume (inferred): ~tens of GB
- Score (inferred): 3/5, Final analysis uses tabulated fluxes and public PDR models, but the imaging details are deferred to an in-prep paper.
- Rediscovery candidate: yes, Table 1 gives fluxes and the PDR grid is public, so the PDR fitting can be redone; the data are public after the proprietary period.

## Links

- Method: (cite: kaufman1999) (PDR model)
- Companion: (cite: villanuevaprep) (VALES I: CO observations)
- Companion: (cite: ibar2015) ([CII] and FIR data)
- Related: VALES
- Related: H-ATLAS
- Related: GAMA

## Checks

```json
{
 "quotes": 51,
 "quotes_ok": 51,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 38,
  "rate": 0.528
 },
 "evidence_ok": true
}
```

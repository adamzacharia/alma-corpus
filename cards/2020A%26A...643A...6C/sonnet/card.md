# The ALPINE-ALMA [CII] survey. Small Lyα-[CII] velocity offsets in main-sequence galaxies at 4.4 &lt; z &lt; 6

`2020A&A...643A...6C` | Astronomy and Astrophysics 2020 | first author: Cassata, P. | arXiv: 2002.00967 | DOI: 10.1051/0004-6361/202037517

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type archival_reuse

## Science

- Fields: high_z_galaxies
- Question: What are the Lyα-[CII] and ISM-[CII] velocity offsets in main-sequence galaxies at 4.4<z<6, and how do they relate to Lyα escape fraction, EW0 and outflows?  
  > "The goal of this paper is to constrain the properties of the Ly$\alpha$ emission in these galaxies in relation to other properties of the ISM." (abstract)
- Target **53 ALPINE main-sequence galaxies with Lyα and [CII] detected (COSMOS and GOODS-S)**: coordinates _not stated_; z/distance 4.4<z<6 (z_[CII] per object in table)  
  > "a sample of 118 main-sequence galaxies at $4.4 < z < 6$ in the COSMOS (Scoville et al. 2007) and GOODS-S fields (Giavalisco et al. 2004)" (Sample and data); distance from [CII] Gaussian centroid (Béthermin et al. 2020)  
  > "a sample of 118 main-sequence galaxies at $4.4 < z < 6$ in the COSMOS (Scoville et al. 2007) and GOODS-S fields (Giavalisco et al. 2004)" (Sample and data)

## Data provenance

- ALMA projects: 2017.1.00428.L
- bands: Band 7 (~320 GHz)  
  > "By combining data obtained with ALMA in band 7 at $\sim$ 320 GHz" (abstract)
- frequencies and spectral setup: spectral window tuned on expected [CII] per object; resolution 26-35 km/s  
  > "The final spectral resolution varies with redshift from 26 to 35 km s$^{-1}$" (ALMA observations and reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-1 and C43-2  
  > "in configurations C43-1 and C43-2, which ideally produce angular resolutions coarser than 0.7 arcsec" (ALMA observations and reduction)
- baselines: _not stated_
- angular resolution: median beam about 1.13" x 0.85" FWHM  
  > "the median beam size of the ALMA observations is about 1.13" x 0.85" full width at half maximum (FWHM)" (ALMA observations and reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 15 to 30 minutes  
  > "Integration times range between 15 and 30 minutes" (ALMA observations and reduction)
- observing dates: May 2018 (cycle 5) to February 2019 (cycle 6)  
  > "starting in May 2018 during cycle 5 and completed in February 2019 in cycle 6" (ALMA observations and reduction)
- pi or archival as stated: _not stated_
- Line: [CII] 158 μm (not stated)
- Other facility **Keck/DEIMOS, VLT VIMOS and FORS2, HST/GRAPES**: Optical spectra for Lyα and UV ISM lines  
  > "49 have spectra from DEIMOS at Keck (Capak et al. 2004; Mallery et al. 2012; Hasinger et al. 2018), with a spectral resolution R $\sim2500$" (Spectroscopic data and measurements)
- External data: SED-fit stellar mass, SFR, M_FUV, E(B-V)  
  > "for more details, see Faisst et al. (2020), where the ancillary data for the ALPINE galaxies are presented in their full extent" (Associated optical/NIR and other multiwavelength data) [from Faisst et al. 2020]
- External data: [CII] redshifts from Gaussian fits and detections  
  > "the centroid of the Gaussian is used to determine $\nu_{[CII]obs}$, $z_{[CII]obs}$, and in this way, the systemic velocity of the system (Béthermin et al. 2020)" (ALMA observations and reduction) [from Béthermin et al. 2020]

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

- ALMA data processing  
  > "For more details, see Béthermin et al. (2020), where the processing of ALMA data is presented in full detail." (ALMA observations and reduction) [from Béthermin et al. (2020)]
- z_ISM determination and spectroscopic data details  
  > "The details of how $z_{ISM}$ is determined are given in Faisst et al. (2020)" (Spectroscopic data and measurements) [from Faisst et al. (2020)]

### Not stated but needed to reproduce (our reading)

- CASA version, imaging parameters and the [CII] spectrum extraction apertures (delegated to Béthermin et al. 2020)
- Line-fit settings for the [CII] Gaussian
- Exact Spearman test implementation and linear-fit method for the offset-EW relation

## Analysis recipe

1. **Systemic redshift from [CII]**: Gaussian fit to extracted [CII] spectrum; centroid gives z_[CII]  
  > "a Gaussian is fit to the spectrum and the centroid of the Gaussian is used to determine $\nu_{[CII]obs}$" (ALMA observations and reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Lyα offset**: Lyα peak position vs [CII]; error ~1/5 of line width from simulations; resolution correction of 150 (VUDS) and 50 (CANDELS) km/s  
  > "Therefore we applied an average correction of 150 and 50 km s$^{-1}$ to the offsets between Ly$\alpha$ and [CII] for the VUDS and CANDELS galaxies, respectively." (Spectroscopic data and measurements)
   - parameter: DEIMOS spectra boxcar smoothed with 100 km/s window  
  > "we applied a boxcar smoothing to those spectra, with a window length of 100 km s$^{-1}$" (Spectroscopic data and measurements)
   - assumption: No IGM correction applied to Lyα profiles  
  > "we preferred not to correct the individual line profiles for this effect" (Spectroscopic data and measurements)
   - fitting: _not stated_
   - validation: Simulated asymmetric lines; degraded DEIMOS spectra to test peak shift  
  > "we degraded the DEIMOS spectra at the resolution of CANDELS and VUDS, and we measured the shift of the Ly$\alpha$ peak induced by degrading the resolution" (Spectroscopic data and measurements)
3. **ISM line offsets, EW0 and fesc**: Cross-match Shapley et al. 2003 template (200 perturbations); EW from continuum in 1225-1245 Å windows; fesc from SFR via Kennicutt 1998 with +0.2 dex for 1/5 solar metallicity  
  > "The errors were estimated by repeating the cross-match 200 times, each time perturbing the fluxes according to a Gaussian error distribution" (Spectroscopic data and measurements)
   - assumption: Case B recombination, Chabrier IMF, one-fifth solar metallicity  
  > "when we assume a metallicity of one-fifth solar (the typical value for main-sequence galaxies found by Faisst et al. 2016 at $z\sim5$)" (Spectroscopic data and measurements)
   - fitting: _not stated_
   - validation: fesc vs EW0 compared with Sobral & Matthee 2019 relation  
  > "65% of the objects are within $\pm1\sigma$ from it" (Spectroscopic data and measurements)
4. **Correlation tests**: Spearman rank test of offsets vs EW0, fesc, M_FUV, mass, SFR, E(B-V)  
  > "We ran a Spearman rank test to check and validate possible correlations between each parameter and the velocity offsets" (Correlation of Lyα offsets with other physical properties)
   - fitting: _not stated_
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Lyα-[CII] offset peak | ~200 | not stated | km/s | 2 | with velocity offsets peaking at $\sim$200 km s$^{-1}$ and ranging from -200 to +600 km s$^{-1}$ |
| Lyα-ISM average velocity difference (28 objects) | 377 | sigma_mean 62 (scatter 329) | km/s | 3 | with an average value of 377, a scatter of 329 km s$^{-1}$, and a standard deviation of the mean $\sigma_{mean}$ of 62 km s$^{-1}$ |
| LAEs with EW0>25 (20) Å among 53 | 20 (28) | not stated | galaxies | 3 | 20(28) have $EW_0(Ly\alpha)>25(20)$ Å |
| ISM offsets typical range | -500 to 100, around -300 | not stated | km/s | 3 | with offsets around -300 km s$^{-1}$ and ranging from -500 and 100 km s$^{-1}$ |

## Qualitative findings

- Δv_Lyα anticorrelates with EW0 and fesc and correlates positively with E(B-V); no correlation with mass, SFR or M_FUV; no correlation between Δv_ISM and Δv_Lyα  
  > "We find that the Ly$\alpha$ velocity offsets are anticorrelated with $EW_0(Ly\alpha)$ and $f_{esc}(Ly\alpha$), but they correlate positively with the E(B-V)$_{\ast}$" (Correlation of Lyα offsets with other physical properties)

## Claim tuples

- H: Lyα-[CII] offsets at z~5 are smaller than at z~2-3.5 | E: Measured Lyα peak vs [CII] centroid for 53 galaxies | R: Peak ~200 km/s, 90% in 0-400 km/s | F: Offsets are smaller than at lower redshift | **supported**
- H: Outflows drive Lyα escape | E: Compared ISM-[CII] offsets with Lyα offsets and escape fraction | R: No correlation between Δv_ISM and Δv_Lyα; most outflows slow | F: Outflows are not the main driver of Lyα escape at these redshifts; lower NHI or covering fraction favoured | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: [CII] used as systemic velocity tracer since not absorbed by dust  
  > "[CII] is an optically thin cooling line that is not absorbed by dust and therefore observable in the whole galaxy." (Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): S/N of spectra insufficient to analyse ISM line morphologies; only centroids  
  > "Unfortunately, the S/N of our spectra is not enough to analyze the details of the ISM line morphologies, and we can only estimate the centroid of the line." (Discussion)
- Caveat (inferred, ours): Many offset errors comparable to values; low-resolution VUDS spectra need large corrections
- Caveat (inferred, ours): Mergers and spatial offsets up to 0.5" between Lyα and [CII]
- Caveat (inferred, ours): IGM absorption not corrected

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Measured [CII] spectra and optical spectra are not provided beyond the tables
- Missing: Processing details deferred to Béthermin et al. 2020 and Faisst et al. 2020
- Data volume (inferred): Moderate; ALPINE Band 7 cubes (~75 detections) plus external spectra
- Score (inferred): 3/5, Tables give key measurements but reduction and spectroscopy depend on companion papers.
- Rediscovery candidate: no, Depends on non-ALMA spectra and companion-paper catalogs.

## Links

- Method: Béthermin et al. 2020 (ALMA data processing and [CII] measurement)
- Method: Faisst et al. 2020 (Ancillary data, SED fitting, z_ISM)
- Companion: Le Fèvre et al. 2020 (ALPINE survey overview)
- Related: ALPINE
- Related: VUDS
- Related: DEIMOS 10k survey

## Checks

```json
{
 "quotes": 35,
 "quotes_ok": 35,
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
  "facts": 65,
  "stated": 26,
  "rate": 0.4
 },
 "evidence_ok": true
}
```

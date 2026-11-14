# The evolving far-IR galaxy luminosity function and dust-obscured star formation rate density out to z≃5.

`2017MNRAS.471.4155K` | Monthly Notices of the Royal Astronomical Society 2017 | first author: Koprowski, M. P. | arXiv: 1706.00426 | DOI: 10.1093/mnras/stx1843

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies, cosmology
- Question: What are the form and evolution of the far-IR galaxy luminosity function out to z~5, and what is the dust-obscured star-formation rate density?  
  > "We present a new measurement of the evolving galaxy far-IR luminosity function (LF) extending out to redshifts $z \simeq 5$, with resulting implications for the level of dust-obscured star-formation density in the young Universe." (abstract)
- Target **HUDF (ALMA 1.3-mm mosaic)**: coordinates _not stated_; z/distance 13 of 16 sources spectroscopic z, 3 photometric  
  > "A mosaic of 45 ALMA pointings was created to cover the full $\simeq 4.5$ arcmin$^2$ area previously imaged with WFC3/IR on *HST*." (2.2 ALMA imaging); distance from Dunlop_2017 table 2 and optical-near-IR photometry  
  > "A mosaic of 45 ALMA pointings was created to cover the full $\simeq 4.5$ arcmin$^2$ area previously imaged with WFC3/IR on *HST*." (2.2 ALMA imaging)
- Target **S2CLS UDS and COSMOS fields**: coordinates _not stated_; z/distance mean z=2.73±0.06 for the whole sample  
  > "The fields utilised here are the UKIDSS-UDS, where the 850-${\rm \mu m}$ imaging covers $\simeq 0.9$ deg$^2$ with a 1-$\sigma$ noise of 0.9 mJy" (2.1 JCMT SCUBA-2 imaging); distance from optical/near-IR photometric redshifts and long-wavelength photometric redshifts  
  > "The fields utilised here are the UKIDSS-UDS, where the 850-${\rm \mu m}$ imaging covers $\simeq 0.9$ deg$^2$ with a 1-$\sigma$ noise of 0.9 mJy" (2.1 JCMT SCUBA-2 imaging)

## Data provenance

- ALMA projects: 2012.1.00173.S
- bands: 1.3 mm  
  > "we used the ALMA 1.3-mm imaging of the HUDF undertaken by (cite: Dunlop_2017)" (2.2 ALMA imaging)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: σ1.3 ≃ 35 µJy/beam; 16 sources with S1.3 > 120 µJy  
  > "The ALMA map reached a noise level of $\sigma_{1.3}\simeq 35\,{\rm \mu Jy\, beam^{-1}}$, and 16 sources were detected with flux densities $S_{1.3}>120\,{\rm \mu Jy}$." (2.2 ALMA imaging)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **JCMT SCUBA-2 (S2CLS)**: 850-µm maps and source catalogues for UDS and COSMOS  
  > "We used the data collected as a part of the SCUBA-2 Cosmology Legacy Survey (S2CLS)." (2.1 JCMT SCUBA-2 imaging)
- Other facility **Herschel PACS/SPIRE**: far-IR flux densities for SED/photometric redshifts  
  > "far-IR imaging from *Herschel* (cite: Pilbratt_2010) was utilised, as provided by the public releases of the HerMES (cite: Oliver_2012) and PEP (cite: Lutz_2011) surveys" (2.3 Ancillary data)
- External data: ALMA HUDF 1.3-mm map, source list and redshifts  
  > "for the sources of the spectroscopic redshifts see table 2 in (cite: Dunlop_2017)" (2.2 ALMA imaging) [from (cite: Dunlop_2017)]
- External data: S2CLS maps, catalogues, false detection rate relation  
  > "The map-making process and the resulting derived source catalogues are described in (cite: Geach_2017)." (2.1 JCMT SCUBA-2 imaging) [from (cite: Geach_2017)]
- External data: UV rho_UV results used for UV-visible SFRD  
  > "The blue squares give the values of UV-visible $\rho_{\rm SFR}$ derived from the (cite: Parsa_2016) $\rho_{\rm UV}$ results" (5 Star Formation Rate Density) [from (cite: Parsa_2016)]

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

- ALMA data reduction and imaging taken from the published HUDF mosaic  
  > "we used the ALMA 1.3-mm imaging of the HUDF undertaken by (cite: Dunlop_2017)" (2.2 ALMA imaging) [from (cite: Dunlop_2017)]
- Identifications and redshifts for SCUBA-2 sources  
  > "for a more detailed description of this process and the relevant identification tables see (cite: Michalowski_2016)" (3.1 Multi-wavelength identifications) [from (cite: Michalowski_2016)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration and imaging settings (all inherited from Dunlop et al. 2017)
- How ALMA sources were converted to rest-frame 250-µm luminosities and binned for the faint-end fit
- Completeness and effective-area corrections for the ALMA map
- Optimiser used for chi2 and likelihood minimisation
- Exact luminosity bins for the faint-end slope fit

## Analysis recipe

1. **Build 850-µm samples and redshifts**: Select S2CLS sources with completeness >0.5 in uniform-noise regions; identify counterparts with radio/24µm/8µm; photometric redshifts via chi2 template fitting  
  > "for our analysis retained only sources with a simulated completeness $>0.5$" (2.1 JCMT SCUBA-2 imaging)
   - software: HYPERZ-based code
   - fitting: _not stated_
   - validation: Compared optical photometric redshifts with long-wavelength photometric redshifts  
  > "we further tested the robustness of our optical identifications by comparing the optical photometric redshifts with the ‘long-wavelength’ photometric redshifts" (3.2 Redshift distributions)
2. **Measure binned LF with 1/Vmax**: 1/Vmax in four redshift bins at rest-frame 250 µm, then Schechter fit by chi2 with alpha fixed from the ALMA data at 1.5<z<2.5  
  > "Fitting the Schechter function to the $1.5<z<2.5$ data yielded a faint-end slope of $\alpha=-0.4$." (4.1 1/Vmax method)
   - assumption: Michalowski 2010 average SMG SED used to interpolate to 250 µm  
  > "interpolated to $\lambda_{\rm rest} = 250$ ${\rm \mu m}$ using the average SMG template from (cite: Michalowski_2010)" (4.1 1/Vmax method)
   - fitting: chi2 minimisation; 68% and 95% intervals from Δchi2=1 and 4  
  > "the 68% and 95% confidence intervals are shown, corresponding to $\Delta\chi^2=1$ and 4 respectively" (4.1 1/Vmax method)
   - validation: Compared with the maximum-likelihood LF  
  > "The black solid lines (almost perfectly aligned with the coloured solid lines) with errors (grey-shaded area) depict the LFs as determined by the maximum-likelihood method" (1/Vmax method)
3. **Continuous LF evolution by maximum likelihood**: Poisson likelihood; Phi* Gaussian in z, log L* linear in z, alpha fixed at -0.4  
  > "we could adopt a simple normalised Gaussian function and a linear function of redshift respectively" (4.2 Maximum-likelihood method)
   - fitting: Minimise S=-2 ln L; 1σ from Δchi2=1  
  > "the $1\sigma$ errors (grey area in Fig. [5](#fig:params)) are based on the likelihood ratios and correspond to $\Delta \chi^2=1$" (4.2 Maximum-likelihood method)
   - validation: _not stated_
4. **Derive dust-obscured SFRD**: Integrate LF weighted by total IR luminosity down to 0.01 L*, convert with Kennicutt 1998 factor and 0.63 Chabrier correction  
  > "the LFs were integrated down to a lower luminosity limit of $0.01\times L^\star$" (5 Star Formation Rate Density)
   - assumption: Michalowski 2010 SMG SED, bolometric ~2x a 35 K modified blackbody  
  > "yields a bolometric luminosity $\simeq 2$ times greater than a simple 35 K modified blackbody template" (5 Star Formation Rate Density)
   - fitting: _not stated_
   - validation: Predicted 850-µm number counts compared with observed counts  
  > "Unsurprisingly, since our study is based primarily on 850-$\mu$m data, the number counts predicted by our new IR LFs agree well with the observed counts" (Discussion, Comparison of luminosity functions)

## Software

- **HYPERZ-based code** : photometric redshifts  
  > "with a code based on the HYPERZ package (cite: Bolzonella_2000)" (3.2 Redshift distributions)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Faint-end slope alpha (z~2, from ALMA) | -0.4 | not stated | dimensionless | 2 | Fitting the Schechter function to the $1.5<z<2.5$ data yielded a faint-end slope of $\alpha=-0.4$. |
| log L* at 1.5<z<2.5 | 25.40 | ±0.03 | W/Hz | 2 | $1.5<z<2.5$ / $-0.4$ / $-3.03^{+0.05}_{-0.10}$ / $25.40^{+0.03}_{-0.03}$ |
| Maximum-likelihood parameters a, b | a=0.19, b=25.03 | +0.02/-0.02; +0.06/-0.05 | dimensionless | 3 | $a$ / $0.19^{+0.02}_{-0.02}$ |
| Predicted N(S850>10 mJy), 0.5<z<4.5, this work vs Gruppioni+13 | 20 vs 315 (observed 17) | not stated | sources per 1.5 deg2 | 4 | This Work / $0.5<z<4.5$ / 20 |

## Qualitative findings

- Obscured SFRD declines beyond z~2-2.5 and UV-visible star formation dominates beyond z~4  
  > "we find that $\rho_{\rm SFR}$ declines beyond $z \simeq 2-2.5$ and is dominated by UV-visible star-formation activity beyond $z \simeq 4$" (7 Conclusion)

## Claim tuples

- H: Herschel-based far-IR LFs overestimate the high-z bright end | E: Predicted 850-µm counts from each LF compared with S2CLS counts | R: Herschel LFs predict about 15-20 times more S850>10 mJy sources than observed | F: Herschel LFs are biased high at the bright end by blending and misidentification | **supported**
- H: The far-IR LF shows positive luminosity and negative density evolution at high z | E: Maximum-likelihood fit of a Schechter function with evolving parameters | R: Phi* Gaussian in z, log L* rising linearly | F: The most luminous sources persist to high z while SFRD declines | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Changing the SED template (T up to ~80 K at the bright end) to reconcile Herschel LFs was rejected as unsupported  
  > "There is no evidence to support such a rapid change in typical SED temperature over such a short range in 850-$\mu$m flux density or IR luminosity." (6.1 Comparison of luminosity functions)
- How they decided it was enough: _not stated_
- Caveat (inferred, ours): The faint-end slope rests on 16 ALMA sources in one field, fixed across all bins
- Caveat (inferred, ours): Results depend on a single SED template for luminosity conversion
- Caveat (inferred, ours): The Gaussian and linear forms for Phi* and L* are assumed

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Deep S2CLS catalogues and Herschel photometry for the SCUBA-2 sources
- Missing: ALMA source list from Dunlop 2017
- Missing: Details of the ALMA faint-end luminosity binning
- Data volume (inferred): small if the published catalogues are used; ALMA HUDF mosaic of ~10s GB raw
- Score (inferred): 3/5, LF methodology is clearly described, but it relies on catalogues from other papers and unstated ALMA treatment.
- Rediscovery candidate: no, Needs non-ALMA catalogues, and the ALMA part is only a minor input inherited from another paper.

## Links

- Method: (cite: Marshall_1983) (maximum-likelihood LF method)
- Method: (cite: Michalowski_2010) (SMG SED template)
- Companion: (cite: Dunlop_2017) (ALMA HUDF survey data)
- Companion: (cite: Geach_2017) (S2CLS catalogue)
- Related: SCUBA-2 Cosmology Legacy Survey
- Related: HerMES
- Related: PEP

## Checks

```json
{
 "quotes": 36,
 "quotes_ok": 36,
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
  "facts": 70,
  "stated": 28,
  "rate": 0.4
 },
 "evidence_ok": true
}
```

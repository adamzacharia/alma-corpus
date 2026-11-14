# The ALMA-CRISTAL Survey: Spatially Resolved Star Formation Activity and Dust Content in 4 &lt; z &lt; 6 Star-forming Galaxies

`2024ApJ...976...70L` | The Astrophysical Journal 2024 | first author: Li, Juno | arXiv: 2409.10961 | DOI: 10.3847/1538-4357/ad7fee

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: How do star formation activity, stellar mass and dust obscuration vary on ~0.5-1 kpc scales in z~4-6 main-sequence galaxies, and what does ALMA dust continuum add to resolved SED fitting?  
  > "We consistently model the emission from stars and dust in $\sim$0.5-1kpc spatial bins to obtain maps of their physical properties." (abstract)
- Target **CRISTAL-02 (DC_848185)**: coordinates 10:00:21.50 +02:35:11.08  
  > "| CRISTAL-02   | DC_848185        | 5.294           | 10:00:21.50  | +02:35:11.08 |" (Table 1); z/distance z_[CII]=5.294  
  > "| CRISTAL-02   | DC_848185        | 5.294           | 10:00:21.50  | +02:35:11.08 |" (Table 1); distance from [CII] redshift  
  > "| CRISTAL-02   | DC_848185        | 5.294           | 10:00:21.50  | +02:35:11.08 |" (Table 1)
- Target **CRISTAL-25 (VC_5101218326)**: coordinates 10:01:12.50 +02:18:52.72  
  > "| CRISTAL-25   | VC_5101218326    | 4.573           | 10:01:12.50  | +02:18:52.72 |" (Table 1); z/distance z_[CII]=4.573  
  > "| CRISTAL-25   | VC_5101218326    | 4.573           | 10:01:12.50  | +02:18:52.72 |" (Table 1); distance from [CII] redshift  
  > "| CRISTAL-25   | VC_5101218326    | 4.573           | 10:01:12.50  | +02:18:52.72 |" (Table 1)
- Target **Other CRISTAL galaxies (14 total, 4<z<6, COSMOS)**: coordinates see Table 1  
  > "Here we study 14 of those 19 galaxies which were observed by JWST with NIRCam as of January 2024." (2.1 Sample); z/distance z_[CII]=4.439-5.689  
  > "Here we study 14 of those 19 galaxies which were observed by JWST with NIRCam as of January 2024." (2.1 Sample); distance from [CII] redshift  
  > "Here we study 14 of those 19 galaxies which were observed by JWST with NIRCam as of January 2024." (2.1 Sample)

## Data provenance

- ALMA projects: 2021.1.00280.L, 2017.1.00428.L, 2018.1.01359.S, 2019.1.01075.S, 2018.1.01605.S, 2019.1.00226.S
- bands: Band 7, targeting [CII] and rest-frame 158 um continuum  
  > "The CRISTAL observations and ALPINE archival observations were taken in Band 7, targeting the \[CII\] line ($\nu_\mathrm{rest}=1900.54$ GHz)" (2.2 ALMA Band 7 observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Long (C43-5/6) plus short (C43-1/2) baselines; ALPINE C43-1/2  
  > "CRISTAL observations combine long baselines (C43-5 or C43-6; typical beam sizes $0.1\ensuremath{''}-0.3\ensuremath{''}$) and short baselines (C43-1 or C43-2; typical beam sizes $0.7\ensuremath{''}-1.0\ensuremath{''}$)" (2.2 ALMA Band 7 observations)
- baselines: _not stated_
- angular resolution: median natural-weighted beam 0.45" x 0.54"  
  > "the median synthesised beam size for our subsample of 14 sources is $0.45\ensuremath{''}\times0.54\ensuremath{''}$" (2.2 ALMA Band 7 observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: [CII] 158 um (1900.54 GHz)
- Other facility **HST ACS/WFC3**: Archival rest-UV/optical imaging (F814W, F160W etc.)  
  > "We used the *grizli* pipeline (cite: brammer2023) to retrieve and reduce the archival HST/ACS and HST/WFC3 observations for all our selected targets." (2.3 HST/ACS and WFC3 observations)
- Other facility **JWST NIRCam**: 4-8 filters from PRIMER, COSMOS-Web and NIRCam parallel programs  
  > "All sources in our sample have been observed with at least 4, and up to 8, JWST/NIRCam filters" (2.4 JWST/NIRCam observations)
- External data: Stacked dust SED template: nuLnu(158um)/L_IR = 0.133  
  > "using the stacked dust SED template of (cite: Bethermin2020) (i.e., at $158\mu m$, $\rm \nu L_{\nu}/L_{IR} = 0.133$)" (4.3 Resolved dust obscuration) [from (cite: Bethermin2020)]
- External data: Dust temperature radial profile (20-65 K) for the Tdust test  
  > "We adopt the dust temperature radial profile from (cite: cochrane2019), which follows an exponential profile with effective radius 0.25$''$" (Appendix 8) [from (cite: cochrane2019)]

## Processing

### Calibration

- pipeline or manual: ALPINE and CRISTAL visibilities combined and re-processed consistently by the CRISTAL team  
  > "Visibility data from ALPINE and CRISTAL observations were combined and re-processed by the CRISTAL team consistently." (2.2 ALMA Band 7 observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural-weighted products adopted (robust=0.5 also produced)  
  > "In this work, we adopt the natural-weighted data products for their higher signal-to-noise ratio (SNR)." (2.2 ALMA Band 7 observations)
- uv taper: _not stated_
- cell size: all images resampled to 0.03"/pixel  
  > "we re-sampled all images to the same pixel grid with size of 0.03$''$/pixel using *ProPane*" (3.1.1 Absolute Alignment)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: All HST/JWST images convolved to ALMA beam with matching kernels  
  > "We then create matching kernels between PSF models of each filter to the target PSF (i.e., the ALMA synthesised beam)" (3.1.2 PSF modeling and homogenization)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA survey design, observational setup and data reduction details  
  > "Details of the survey design and observational setup are presented in Herrera-Camus et al. (in prep.)." (2.1 Sample) [from Herrera-Camus et al. (in prep.)]
- Dust detection classification and naming  
  > "We adopt the classification of dust detection and naming convention in (cite: Mitsuhashi2023)." (2.1 Sample) [from (cite: Mitsuhashi2023)]
- TinyTim F814W PSF construction  
  > "we use TinyTim (cite: Krist2011SPIE) to create the PSF model for each CRISTAL galaxy following Cook et al. (subm.)." (3.1.2 PSF modeling and homogenization) [from Cook et al. (subm.)]

### Not stated but needed to reproduce (our reading)

- Exact CRISTAL reprocessed ALMA continuum maps and CASA version/imaging parameters (not public in this paper)
- Manual circular aperture boundary per source
- Choice of [CII] line width and flux for luminosity maps
- Power-law fitting method for rSFMS
- MAGPHYS library and filter set per source details
- Which ALMA data is public

## Analysis recipe

1. **Align and homogenize images**: Resample to 0.03" pixels, linear shifts relative to F814W/F160W, PSF-match to ALMA beam with Photutils kernels  
  > "we apply only linear shifts." (3.1.1 Absolute Alignment)
   - software: ProPane, Photutils, Astropy, WebbPSF, TinyTim, grizli
   - fitting: _not stated_
   - validation: Offsets <0.03" typical, at most 3 pixels  
  > "Typical offsets were measured to be at sub-pixel scale ($<0.03\ensuremath{''}$) and at most no more than 3 pixels ($<0.09\ensuremath{''}$)." (3.1.1 Absolute Alignment)
2. **Aperture grid photometry**: Uniform square grid with bins 0.15", 0.12" or 0.09" depending on ALMA beam; sum fluxes; errors from 1000 random blank-sky apertures  
  > "We repeat this process 1000 times to obtain a sky flux distribution measured with this aperture" (3.2.1 Aperture grid photometry)
   - fitting: _not stated_
   - validation: _not stated_
3. **Resolved SED fitting**: MAGPHYS fit for bins with >1 sigma in at least four filters, 3 sigma upper limits otherwise  
  > "SEDs extracted in any aperture with more than $1\sigma$ flux detection (i.e., SNR$>1$) in at least four filters were modeled with magphys" (3.2.2 SED fitting with magphys)
   - software: magphys
   - assumption: Chabrier IMF, Bruzual & Charlot models, Charlot & Fall dust, metallicity prior 0.2-2 Zsun  
  > "randomly samples stellar metallicities in a flat prior between $0.2$ and $2\,Z_{\odot}$" (3.2.2 SED fitting with magphys)
   - fitting: Bayesian library of stochastic models, chi2 comparison, marginalised posteriors  
  > "Then, each model in this library is compared to the observations (in this case, the observed SED of each spatial bin) via the $\chi^2$ goodness-of-fit" (3.2.2 SED fitting with magphys)
   - validation: Sum of resolved fits compared to integrated fit; chi2 per filter; ProSpect check on two galaxies  
  > "We verified the results by fitting two of our sample galaxies (i.e. C11 and C13 which have 4 HST and 8 JWST filters) with a different SED fitting code `ProSpect`" (4.2 Resolved star-forming main sequence)
4. **Fit resolved main sequence**: Power-law Sigma_SFR ~ Sigma_M*^alpha per galaxy and combined with hexagonal bins  
  > "We quantify this relation by fitting a power law function, $\hbox{$\Sigma_{\rm SFR}$}\sim \hbox{$\Sigma_{M_*}$}^\alpha$, for each source." (4.2 Resolved star-forming main sequence)
   - fitting: _not stated_
   - validation: Larger hexagonal apertures (~3 kpc) give unchanged rSFMS  
  > "The rSFMS remains unchanged, confirming that the correlation between surface SFR density and the surface stellar mass density is genuine" (4.2 Resolved star-forming main sequence)
5. **Empirical fobs from ALMA and UV**: SFR_IR from Band 7 via Bethermin template and Kennicutt98; SFR_UV from F115W with Madau&Dickinson; fobs=SFR_IR/(SFR_IR+SFR_UV)  
  > "we define $f_{\rm obs}$ as: $$\begin{equation}
    f_{\rm obs} = \frac{\rm SFR_{IR}}{\rm SFR_{IR}+SFR_{UV}} \,," (4.3 Resolved dust obscuration)
   - assumption: SFRs divided by 1.6 to convert Salpeter to Chabrier IMF  
  > "we divide both $\rm SFR_{IR}$ and $\rm SFR_{UV}$ by 1.6" (4.3 Resolved dust obscuration)
   - fitting: _not stated_
   - validation: Tdust gradient simulation (20-65 K) leaves anti-correlation intact; comparison with MAGPHYS Av  
  > "We find that even a steep temperature gradient between 65 K in the center and 20 K in the outskirts does not change the negative trend" (5.3)
6. **Test with/without ALMA and SFR indicators**: Refit without ALMA; compare SED SFR with UV+IR SFR and [CII] luminosity (Solomon & Vanden Bout formula), power-law fits within 4 kpc  
  > "we exclude the outer regions of the galaxies at radii $>4$ kpc to avoid possible contamination by extended emission" (5.4.2)
   - software: magphys
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **magphys** : Resolved SED fitting  
  > "magphys (cite: magphys2008; magphys2015; magphys2020)" (Software)
- **grizli** 1.9.11: HST and PRIMER JWST reduction  
  > "We used the *grizli* pipeline (cite: brammer2023) to retrieve and reduce the archival HST/ACS and HST/WFC3 observations" (2.3 HST/ACS and WFC3 observations)
- **JWST Calibration pipeline** 1.10.0: COSMOS-Web NIRCam reduction  
  > "standard JWST Calibration python package (version=1.10.0, pmap=1075" (2.4 JWST/NIRCam observations)
- **ProPane** : Resampling to common grid  
  > "we re-sampled all images to the same pixel grid with size of 0.03$''$/pixel using *ProPane*" (3.1.1 Absolute Alignment)
- **WebbPSF** : JWST PSF models  
  > "We model the JWST PSF using the *WebbPSF* package" (3.1.2 PSF modeling and homogenization)
- **TinyTim** : HST F814W PSF  
  > "we use TinyTim (cite: Krist2011SPIE) to create the PSF model" (3.1.2 PSF modeling and homogenization)
- **Photutils** 1.5.0: Matching kernels  
  > "using the *create_matching_kernel* function in *Photutils* package" (3.1.2 PSF modeling and homogenization)
- **Astropy** : Convolution  
  > "we convolve all the images with the matching kernels using the *convolve* function in *Astropy*" (3.1.2 PSF modeling and homogenization)
- **ProSpect** : Cross-check SED fits on two galaxies  
  > "with a different SED fitting code `ProSpect` (cite: Robotham2020), adopting a non-parametric SFH" (4.2 Resolved star-forming main sequence)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Combined rSFMS slope | 0.85 | 0.02 | dimensionless | 4 | We find a best-fit power law slope of $0.85\pm0.02$, with a median scatter of $\sim0.1$ dex. |
| Per-galaxy rSFMS slope range | 0.77 to 1.24 | not stated | dimensionless | 4 | The power-law slopes for our sources range from $\alpha=0.77$ to $\alpha=1.24$. |
| Median Sigma_SFR-Sigma_L[CII] slope | 1.58 | 0.02 | dimensionless | 6 | We find a median slope of the $\rm \Sigma_{SFR_{SED}} - {\Sigma_{L_{[CII]}}}$ relation of $\alpha=1.58\pm0.02$ for our sample. |
| Total (integrated) number of spatial bins | 2,730 | not stated | bins | 2 | we are left with a total of 2,730 spatial bin SEDs to model with magphys across our sample |
| CRISTAL-02 SFR with vs without ALMA | ~135 vs ~230 | not stated | Msun/yr | 6 | from $\sim135\rm~M_{\odot}yr^{-1}$ with ALMA to $\sim230\rm~M_{\odot}yr^{-1}$ without ALMA |

## Qualitative findings

- No outshining offset between resolved-sum and integrated stellar masses and SFRs  
  > "We find no offsets between the stellar masses (M$_*$) and star formation rates (SFRs) derived from their global emission and those from adding up the values in our spatial bins" (abstract)

## Claim tuples

- H: A resolved star-forming main sequence exists at z~5 | E: Resolved MAGPHYS fits, Sigma_SFR vs Sigma_M* | R: Slope 0.85±0.02, scatter ~0.1 dex | F: rSFMS persists to z~5 | **supported**
- H: Obscured fraction correlates positively with Sigma_M* on resolved scales | E: Empirical fobs from ALMA+F115W vs Sigma_M* | R: No positive trend; apparent anti-correlation | F: Less obscured SF in centers, possibly due to feedback (speculative) | **partially**
- H: Integrated SED fitting is biased by outshining | E: Compare sum of resolved fits with integrated fit | R: Agree remarkably well | F: No outshining bias in this dataset | **supported**
- H: ALMA improves resolved SED parameters | E: Fit with and without ALMA | R: sSFR radial distribution changes for half the sample, up to factor 3 | F: ALMA breaks age-dust degeneracy | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Uniform grid chosen because galaxies are small relative to the ALMA beam and adaptive binning biases  
  > "The main reason for this choice is that our galaxies are not very extended compared to the ALMA beam size" (3.2.1 Aperture grid photometry)
- Alternative: Empirical PSF rejected in favour of WebbPSF simulated PSF as more conservative  
  > "we decide to adopt the simulated PSF because it is less method-dependant and more conservative" (3.1.2 PSF modeling and homogenization)
- How they decided it was enough: _not stated_
- Limitation (authors): Dust luminosity relies on single ALMA band; temperature variations could affect result  
  > "our inferred dust luminosity relies on a single dust continuum measurement from ALMA, and could be sensitive to spatial dust temperature variations" (Conclusion)
- Caveat (inferred, ours): Neighbouring bins correlated by PSF smoothing so fits not independent
- Caveat (inferred, ours): Single-band IR conversion constant across galaxy
- Caveat (inferred, ours): Parametric SFH in MAGPHYS biases ages young
- Caveat (inferred, ours): Feedback explanation speculative

## Reproducibility

- Data public (paper): JWST raw data public from MAST; ALMA public status not stated  
  > "The raw data are publicly available from MAST archive." (2.4 JWST/NIRCam observations)
- Products in archive: _not stated_
- Missing: CRISTAL ALMA reduction details (deferred to Herrera-Camus et al. in prep.)
- Missing: Aperture circles per source
- Missing: MAGPHYS library details
- Missing: Reduced maps not stated as released
- Data volume (inferred): Large: several ALMA Band 7 datasets for 14 fields plus HST/JWST mosaics; ~100s GB raw
- Score (inferred): 3/5, Method well described but ALMA reduction deferred and no code or products released.
- Rediscovery candidate: no, Requires CRISTAL reprocessed products and multi-facility reduction not fully specified.

## Links

- Method: (cite: magphys2015) (SED fitting code and priors)
- Method: (cite: Bethermin2020) (IR conversion template)
- Companion: Herrera-Camus et al. (in prep.) (CRISTAL survey design)
- Companion: (cite: Mitsuhashi2023) (Dust continuum detections and sizes)
- Related: CRISTAL
- Related: ALPINE
- Related: PRIMER
- Related: COSMOS-Web

## Checks

```json
{
 "quotes": 68,
 "quotes_ok": 68,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 6,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 88,
  "stated": 51,
  "rate": 0.58
 },
 "evidence_ok": true
}
```

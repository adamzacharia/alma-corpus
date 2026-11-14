# HerMES: a search for high-redshift dusty galaxies in the HerMES Large Mode Survey - catalogue, number counts and early results

`2016MNRAS.462.1989A` | Monthly Notices of the Royal Astronomical Society 2016 | first author: Asboth, V. | arXiv: 1601.02665 | DOI: 10.1093/mnras/stw1769

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: Can a map-based search of the HeLMS SPIRE maps yield a large catalogue of red (S500>S350>S250) high-redshift dusty star-forming galaxies, and what are their number counts relative to models?  
  > "Here we apply a map-based search method to 274 deg$^2$ of the HerMES Large Mode Survey (HeLMS) and create a catalogue of 477 objects" (abstract)
- Target **HELMS_RED_4**: coordinates RA 5.5867 deg, Dec -1.9224 deg  
  > "In the spectrum of HELMS\_RED\_4 we detect two lines, unambiguously identified as the CO($5-4$) and CO($6-5$) transitions." (6.1 ALMA spectroscopy); z/distance z=5.162 (CO)  
  > "In the spectrum of HELMS\_RED\_4 we detect two lines, unambiguously identified as the CO($5-4$) and CO($6-5$) transitions." (6.1 ALMA spectroscopy); distance from ALMA Band 3 CO lines  
  > "In the spectrum of HELMS\_RED\_4 we detect two lines, unambiguously identified as the CO($5-4$) and CO($6-5$) transitions." (6.1 ALMA spectroscopy)
- Target **HELMS_RED_31**: coordinates _not stated_; z/distance z=3.798 (CO(4-3) identification, VLA-confirmed) or 4.997  
  > "Only a single strong line is seen in the spectrum of HELMS\_RED\_31, and there are several spectral lines that could fall into this region." (6.1 ALMA spectroscopy); distance from single ALMA line plus VLA (Riechers et al. in prep.)  
  > "Only a single strong line is seen in the spectrum of HELMS\_RED\_31, and there are several spectral lines that could fall into this region." (6.1 ALMA spectroscopy)

## Data provenance

- ALMA projects: 2013.1.00449.S
- bands: Band 3 (84-116 GHz)  
  > "The observations were carried out in Band 3, covering frequencies between 84 and 116 GHz" (6.1 ALMA spectroscopy)
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
- Line: CO 5-4 and 6-5 (not stated)
- Other facility **Herschel/SPIRE (HeLMS)**: 250/350/500 micron maps used for the catalogue  
  > "The HerMES Large Mode Survey (HeLMS) consists of a large area shallow observation of an equatorial field at wavelengths of 250, 350 and 500 $\mu$m" (Observations)
- Other facility **CSO/MUSIC**: 143-326 GHz photometry of four sources  
  > "We observed four of our 500-micron-bright sources (HELMS\_RED\_3, HELMS\_RED\_4, HELMS\_RED\_6 and HELMS\_RED\_7)" (6.2 CSO/MUSIC millimeter-wave observations)
- Other facility **VLA**: confirmed z=3.798 for HELMS_RED_31  
  > "recent observations with the Karl G. Jansky Very Large Array (VLA) confirm the $z=3.798$ redshift value" (6.1 ALMA spectroscopy)
- External data: Bethermin et al. galaxy evolution models used for mock catalogues  
  > "We compare our observed number counts to mock “red” catalogues created from the (cite: bethermin2011) and (cite: bethermin2012) models." (4.2 Comparison to models) [from (cite: bethermin2011), (cite: bethermin2012)]

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

- Map-based red-source search, difference map coefficient k=0.392, and MCMC SED fitting  
  > "We use a similar technique to find red sources in the HeLMS field as the map-based search method described in (cite: dowell2014)." (3 Catalogue creation) [from (cite: dowell2014)]
- Photo-z estimation method for ALMA targets  
  > "the photo-$z$ estimation method will be presented in Clements et al. in prep." (6.1 ALMA spectroscopy) [from Clements et al. in prep.]

### Not stated but needed to reproduce (our reading)

- ALMA array configuration, integration time, calibrators and dates
- CASA version and calibration/imaging parameters
- Line fitting method and uncertainties on redshifts
- Coordinates of HELMS_RED_31
- Photometric redshift method (in prep.)

## Analysis recipe

1. **Build matched-filtered, difference map**: Matched filter smoothing of 250/350/500 maps, D=0.92 M500 - 0.392 M250  
  > "Our final difference map is constructed as $$\begin{equation}
\label{eq:diffmap}
 D = 0.92M_{500}-0.392M_{250}. \end{equation}$$" (3.3 Difference map)
   - fitting: _not stated_
   - validation: Injected fake sources into raw maps  
  > "We test this filtering method by injecting fake sources with known flux density values into our raw maps" (3.2 Matched filter)
2. **Extract red sources**: Local maxima in D with D>34 mJy, S500>S350>S250, S500>52 mJy; photometry at best-correlation position in nominal maps  
  > "We create a list of these peaks with a cut-off at $D = 34$ mJy which corresponds to 4$\sigma_{\text{tot},D}$ in the difference map." (3.4 Source extraction)
   - fitting: _not stated_
   - validation: Purity from mock catalogues: 94% at D>4 sigma  
  > "the purity of our HeLMS red source catalogue decreases from 94$\%$ at $D > 4 \sigma_{D}$ to 77$\%$ if we apply a $D > 3  \sigma_{D}$ cut." (3.4 Source extraction)
3. **Infer intrinsic number counts**: Inject power-law red sources into simulated maps and tune N0 and alpha to match raw counts  
  > "In an iterative process we change the input parameters $N_0$ and $\alpha$ until the output counts are within the uncertainties compared to the measured raw number counts" (4.1 Simulations)
   - assumption: Fixed colour ratios S500/S250=1.55, S500/S350=1.12  
  > "$S_{500}/S_{250}$ = 1.55 and $S_{500}/S_{350}$ = 1.12" (4.1 Simulations)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit SEDs**: Optically thick modified blackbody with MCMC and Gaussian priors on beta and lambda0(1+z)  
  > "while marginalizing over the Gaussian priors $\beta = 1.8 \pm 0.3$ and $\lambda_0 (1+z) = (1100 \pm 400)$ $\mu$m." (5 Colours and SED fits)
   - fitting: Affine invariant MCMC from Dowell et al.  
  > "We use the affine invariant MCMC code described in (cite: dowell2014)" (5 Colours and SED fits)
   - validation: _not stated_
5. **ALMA redshifts**: Identify CO lines in Band 3 spectra  
  > "These correspond to a redshift of $z=5.162$, which is in very good agreement with the photo-*z* estimate of $5.27$." (6.1 ALMA spectroscopy)
   - fitting: _not stated_
   - validation: Compared with photo-z and VLA  
  > "We note that recent observations with the Karl G. Jansky Very Large Array (VLA) confirm the $z=3.798$ redshift value (Riechers et al. in prep.)." (ALMA spectroscopy)

## Software

- **SMAP/SHIM** : SPIRE map-making  
  > "We use the SMAP/SHIM iterative map-maker (cite: levenson2010) with the modifications described in (cite: viero2013) to create our maps." (3.1 Maps)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Red sources in catalogue | 477 | not stated | sources | 2 | our final catalogue contains 477 red sources with $S_{500} > S_{350} >S_{250}$ |
| Power-law slope alpha | -5.60 | ±0.01 | dimensionless | 3 | $\alpha = -5.60$ and $\log N_0 = 8.61$ |
| Mean observed temperature | 11.03 | 1.91 | K | 4 | The mean observed temperature is $(11.03 \pm 1.91)$ K. |
| HELMS_RED_4 redshift | 5.162 | not stated | dimensionless | 5 | These correspond to a redshift of $z=5.162$ |
| HELMS_RED_4 dust temperature | 67 | 6 | K | 5 | $T_\text{d} = 67 \pm 6$ K |

## Qualitative findings


## Claim tuples

- H: Red SPIRE sources are more numerous than models predict | E: Compare simulated intrinsic counts with Bethermin models | R: Models under-predict by at least an order of magnitude | F: Excess of red sources confirmed | **supported**
- H: Red SPIRE selection finds z>4 galaxies | E: ALMA Band 3 CO spectroscopy of two sources | R: z=5.162 and z=3.798 (VLA-confirmed) | F: Selection efficiently finds high-z dusty starbursts, though one lower than 4 | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Blending is significant at 500 micron and blends are retained in the catalogue  
  > "Since we select sources at the 500 $\mu$m resolution, blending is a significant contaminating effect." (7 Conclusions)
- Caveat (inferred, ours): Only two ALMA sources; one redshift ambiguous
- Caveat (inferred, ours): Counts not corrected explicitly; depends on assumed power law and fixed colours

## Reproducibility

- Data public (paper): Catalogue to be released via HeDaM  
  > "The full catalogue of 477 red sources is available online in the contributed data section of HeDaM/HerMES" (3.4 Source extraction)
- Products in archive: _not stated_
- Missing: ALMA observing and reduction details
- Missing: Photo-z method
- Data volume (inferred): ALMA part: small (tens of GB at most); SPIRE maps few GB
- Score (inferred): 2/5, ALMA part is a minor, sparsely described piece; main catalogue work uses Herschel maps.
- Rediscovery candidate: no, ALMA reduction not described; main results are Herschel-based.

## Links

- Method: (cite: dowell2014) (Original map-based red source method)
- Method: (cite: chapin2011) (Matched filter)
- Companion: Riechers et al. in prep. (VLA confirmation of redshift)
- Related: HerMES
- Related: HeLMS

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
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 26,
  "rate": 0.371
 },
 "evidence_ok": true
}
```

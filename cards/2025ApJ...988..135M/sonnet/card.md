# The Physical Properties and Morphologies of Faint Dusty Star-forming Galaxies Identified with JWST

`2025ApJ...988..135M` | The Astrophysical Journal 2025 | first author: McKay, S. J. | arXiv: 2503.00102 | DOI: 10.3847/1538-4357/ade394

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: How do the physical properties and morphologies of faint (<2 mJy at 850 um) DSFGs, identified with JWST red-color priors, compare with those of bright DSFGs?  
  > "This procedure provides large, uniform samples of both bright and faint DSFGs with accurate JWST counterparts, making it possible to study how the two populations compare." (Introduction)
- Target **A2744 (Abell 2744) field DSFGs**: coordinates _not stated_; z/distance median z = 2.43 for the full sample (spectroscopic, grism or EAZY photometric)  
  > "The lensing magnifications are derived from the lensing model of (cite: furtak23b), which is highly constrained using both HST and JWST multiply imaged sources." (2.1 A2744); distance from literature spectroscopic/grism redshifts and EAZY photometric redshifts  
  > "The lensing magnifications are derived from the lensing model of (cite: furtak23b), which is highly constrained using both HST and JWST multiply imaged sources." (2.1 A2744)
- Target **GOODS-S field DSFGs**: coordinates _not stated_; z/distance median z = 2.43 for the full sample  
  > "We include the GOODS-S field in our study to take advantage of its extremely deep JWST and submillimeter/millimeter observations" (2.2 GOODS-S); distance from literature spectroscopic/grism redshifts and EAZY photometric redshifts  
  > "We include the GOODS-S field in our study to take advantage of its extremely deep JWST and submillimeter/millimeter observations" (2.2 GOODS-S)

## Data provenance

- ALMA projects: 2013.1.00999.S, 2015.1.01425.S, 2015.1.00543.S, 2015.1.00242.S, 2015.1.00098.S, 2017.1.01219.S, 2017.1.00755.S, 2018.1.00035.L, 2021.1.00024.S, 2022.1.00073.S
- bands: ALMA 870 um, 1.1/1.2 mm, 2 mm, 3 mm from published catalogs/images  
  > "We also use the ALMA 870 $\mu$m, 1.2 mm, 2 mm, and 3 mm fluxes from (cite: cowie18) and (cite: mckay23)." (2.2 GOODS-S)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.59'' x 0.53'' (combined GOODS-S 1.2 mm image)  
  > "The resulting synthesized beam size of this image is 0.59$''$$\times$ 0.53$''$." (2.2 GOODS-S)
- max recoverable scale: _not stated_
- sensitivity: ~30 uJy (GOODS-S 1.2 mm); min rms 32.7 uJy (DUALZ A2744)  
  > "to obtain a depth of $\sim$30 $\mu$Jy." (2.2 GOODS-S); "down to a minimum rms value of 32.7 $\mu$Jy." (2.1 A2744)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **JWST/NIRCam**: Imaging and photometric catalogs (GLASS/UNCOVER, JADES) used for red-galaxy selection, SED fitting and morphology  
  > "eight bands of JWST/NIRCam imaging from 0.9–4.4 $\mu$m" (2.1 A2744)
- Other facility **JCMT/SCUBA-2**: 450 and 850 um maps used for prior-based flux measurements  
  > "The GOODS-S has extremely deep SCUBA-2 450 $\mu$m and 850 $\mu$m data" (2.2 GOODS-S)
- Other facility **HST**: ACS/WFC3 optical-NIR photometry and grism redshifts  
  > "This includes eight bands of HST imaging from 0.4–1.6 $\mu$m" (2.1 A2744)
- Other facility **Spitzer/MIPS and Herschel PACS/SPIRE**: FIR photometry for SED fits  
  > "we use the Spitzer/MIPS 24 $\mu$m photometry from (cite: elbaz11)" (2.2 GOODS-S)
- Other facility **Keck/MOSFIRE**: a few spectroscopic redshifts  
  > "For two sources, we adopt spectroscopic redshifts obtained from our own Keck/MOSFIRE observations." (3.4 Redshifts)
- External data: ALMA 1.2 mm catalog (GOODS-ALMA v2.0)  
  > "We use the ALMA 1.2 mm catalog from v2.0 of the GOODS-ALMA survey (cite: gomez-guijarro22)" (2.2 GOODS-S) [from (cite: gomez-guijarro22)]
- External data: ASAGAO 1.2 mm catalog and combined 1.2 mm image  
  > "the ALMA 1.2 mm catalog from the ASAGAO survey (cite: hatsukade18)" (2.2 GOODS-S) [from (cite: hatsukade18)]
- External data: DUALZ 1.2 mm data and catalog in A2744  
  > "We use the data products from that survey, since they include the previous ALMA data in the field." (2.1 A2744) [from (cite: fujimoto25)]
- External data: ALMA 870 um fluxes in GOODS-S  
  > "We also use the ALMA 870 $\mu$m, 1.2 mm, 2 mm, and 3 mm fluxes from (cite: cowie18) and (cite: mckay23)." (2.2 GOODS-S) [from (cite: cowie18); (cite: mckay23)]
- External data: A2744 JWST photometric catalog  
  > "We use the catalog of isophotal photometry from (cite: paris23) for consistency with (cite: barger23)." (2.1 A2744) [from (cite: paris23)]
- External data: JADES DR2 photometric catalog  
  > "We use the imaging and photometric catalog from the second data release (JADES DR2; (cite: eisenstein23b))" (2.2 GOODS-S) [from (cite: eisenstein23b)]
- External data: Lensing magnifications and photometric redshifts (UNCOVER DR2)  
  > "such as lensing magnifications and photometric and spectroscopic redshifts (DR2; (cite: weaver24))" (2.1 A2744) [from (cite: weaver24)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Published images and catalogs used; no ALMA re-reduction  
  > "Rather than re-reduce the data, we make use of published images or submillimeter/millimeter source catalogs, where possible." (2.2 GOODS-S)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: 250 kλ (GOODS-S combined 1.2 mm image, from Hatsukade et al.)  
  > "with a $uv$-taper of 250 k$\lambda$ and primary beam correction applied" (2.2 GOODS-S)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Published primary-beam-corrected mosaics used  
  > "We use the publicly available primary beam-corrected mosaics for both fields." (3.2 Submillimeter/millimeter Properties of Red NIRCam Galaxies)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Red NIRCam color selection (F444W/F150W>3.5, F444W>1 uJy)  
  > "The photometric selection outlined in (cite: barger23) for identifying DSFG counterparts is as follows:" (3.1 Red NIRCam Galaxies) [from (cite: barger23)]
- Prior-based SCUBA-2 flux measurement method  
  > "The method we use for obtaining SCUBA-2 fluxes based on prior positions follows that of (cite: barger23)" (3.2 Submillimeter/millimeter Properties of Red NIRCam Galaxies) [from (cite: barger23)]
- OIR-faint/OIR-dark definitions  
  > "we adopt the selections used in (cite: gottumukkala23)" (3.3 Comparison with Other Red Galaxy Selections) [from (cite: gottumukkala23)]
- Charlot & Fall attenuation slope delta=-0.7  
  > "with a power-law slope of $\delta = -0.7$, in agreement with (cite: mckinney24)" (4.3 SED Results) [from (cite: mckinney24)]

### Not stated but needed to reproduce (our reading)

- Exact BAGPIPES priors beyond ranges (SFR/age priors form, sampler settings, dust emission parameters)
- Which ALMA project data went into which published catalog/image (no per-project mapping)
- GALFIT initial parameters and constraints
- Details of SCUBA-2 reduction and matched-filter PSF
- Selection of the four photometric-redshift outliers beyond stated cases

## Analysis recipe

1. **Select red NIRCam galaxies**: F444W/F150W>3.5 and F444W>1 uJy from JADES DR2 and GLASS-A2744 catalogs; 452 galaxies  
  > "After combining the samples from both fields, we have a final catalog of 452 red NIRCam galaxies." (3.1 Red NIRCam Galaxies)
   - fitting: _not stated_
   - validation: Compared with 125 ALMA sources with NIRCam counterparts; 100 satisfy the criteria  
  > "We find that 100 out of 125 ALMA sources with robust NIRCam counterparts satisfy the criteria of Equation" (3.1 Red NIRCam Galaxies)
2. **Measure submm/mm fluxes at prior positions**: SCUBA-2 850 um peak within 4'' of each prior, brightest-first with cleaning; ALMA 1.2 mm largest peak within 1.0'' of the NIRCam position; detection >3 sigma  
  > "we measure the 1.2 mm flux by finding the largest local peak within $1.0\ensuremath{''}$ of the NIRCam position." (3.2 Submillimeter/millimeter Properties of Red NIRCam Galaxies)
   - parameter: rms from 5000 random pixels within 12'' after masking >4 sigma peaks  
  > "We estimate the rms noise by measuring the standard deviation in 5000 random pixels within 12$''$ of the source" (3.2 Submillimeter/millimeter Properties of Red NIRCam Galaxies)
   - fitting: _not stated_
   - validation: False-positive fraction ~10% from 1000 random positions  
  > "By running the same detection procedure on 1000 randomly selected positions in the SCUBA-2 850 $\mu$m images, we constrain the false-positive fraction to be $\sim$10%" (3.2 Submillimeter/millimeter Properties of Red NIRCam Galaxies)
3. **SED fitting for stellar properties**: BAGPIPES with delayed exponential SFH, Calzetti attenuation, BC03, Draine&Li dust emission, CLOUDY nebular emission; redshift fixed to best available  
  > "We fit the SEDs of the red DSFG sample with the `BAGPIPES` code, which uses a fully Bayesian framework" (4.1 SED Fitting with BAGPIPES)
   - software: BAGPIPES, EAZY
   - parameter: age 1 Myr–14 Gyr, tau 100 Myr–9 Gyr, A_V 0–6, Z 0.2–1.2 Zsun, logU=-2.0, 5% error floor  
  > "the e-folding time, $\tau$, between 100 Myr and 9 Gyr." (4.1 SED Fitting with BAGPIPES)
   - assumption: Kroupa IMF; factor 2 higher attenuation in birth clouds  
  > "we assume a factor of 2 higher attenuation in the stellar birth clouds" (4.1 SED Fitting with BAGPIPES)
   - fitting: Bayesian posterior; medians with 16th–84th percentiles  
  > "the values listed are the median values of the posterior distributions, with the errors referring to the 16th–84th percentile ranges of the posteriors." (Table 2 notes)
   - validation: Photometric redshifts compared with spectroscopic; alternative Charlot & Fall curve test  
  > "we reran our SED fits using the (cite: charlot00) attenuation curve with a power-law slope of $\delta = -0.7$, in agreement with (cite: mckinney24)." (4.1 SED Fitting with BAGPIPES (Section 4.3))
4. **Derive SFRs**: SFR = 1.16e-10 L_IR + 3.35e-10 L_UV (Kennicutt98, Kroupa IMF), L_IR 8–1000 um, L_UV at 2800 A  
  > "$L_{\rm IR}$ is integrated between rest-frame 8 and 1000 $\mu$m" (4.1 SED Fitting with BAGPIPES)
   - software: BAGPIPES
   - fitting: _not stated_
   - validation: _not stated_
5. **Fit morphologies and identify mergers**: Single Sérsic GALFIT fits on 8''x8'' F444W and F150W cutouts with empirical stacked-star PSF; visual merger classification  
  > "we choose a single Sérsic profile" (5.1 Surface Brightness Profile Fitting)
   - software: GALFIT
   - parameter: F150W position angle tied to F444W; sources <26 mag within 3'' fit simultaneously  
  > "we constrain the F150W Sérsic fits to have the same position angle as the best-fit F444W model" (5.1 Surface Brightness Profile Fitting)
   - fitting: GALFIT Levenberg–Marquardt least squares  
  > "`GALFIT` uses a nonlinear least-squares fitting process (built on the Levenberg–Marquardt algorithm) to determine the combination of parameters that minimizes the fit residuals" (5.1 Surface Brightness Profile Fitting)
   - validation: Repeated with 6'' and 12'' cutouts; parameters unchanged at ~1%  
  > "we repeated the fits with 6$''$ and 12$''$ image and PSF cutouts and confirmed that the fitted parameters were unchanged" (5.1 Surface Brightness Profile Fitting)

## Software

- **BAGPIPES** : SED fitting  
  > "`BAGPIPES` (cite: carnall18)" (Software)
- **EAZY** : photometric redshifts (from published catalogs)  
  > "`EAZY` (cite: brammer08)" (Software)
- **GALFIT** : Sérsic profile fitting  
  > "`GALFIT` (cite: peng10)" (Software)
- **astropy** : general analysis  
  > "`astropy` (cite: astropy:2013; astropy:2018; astropy:2022)" (Software)
- **scipy** : general analysis  
  > "`scipy` (cite: scipy20)" (Software)
- **CLOUDY** : nebular emission within BAGPIPES  
  > "we include nebular emission based on the `CLOUDY` photoionization code (cite: ferland17)" (4.1 SED Fitting with BAGPIPES)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Red DSFG sample size | 234 (47 bright, 187 faint) | not stated | galaxies | 2 | In total, there are 234 red NIRCam galaxies with at least a $>3\sigma$ detection at 850 $\mu$m and/or at 1.1/1.2 mm. |
| Median redshift | 2.43 | 16th–84th percentile 1.57–3.46 | dimensionless | 3 | The median redshift of the full red DSFG sample is $\langle z \rangle = 2.43$ |
| Median SFR faint DSFGs | 80 | +81/-45 | Msun/yr | 4 | SFR \[${\rm M}_\odot\,$yr$^{-1}$\] / 80$^{+81}_{-45}$ / 254$^{+135}_{-131}$ |
| Median SFR bright DSFGs | 254 | +135/-131 | Msun/yr | 4 | SFR \[${\rm M}_\odot\,$yr$^{-1}$\] / 80$^{+81}_{-45}$ / 254$^{+135}_{-131}$ |
| SFR–f850 relation (all samples) | SFR = 83 x f850 | ±11 | Msun/yr per mJy | 4 | ${\rm SFR}~[{\rm M}_\odot~{\rm yr}^{-1}] = (83\pm 11) \times \ensuremath{f_{{\rm 850\, \mu m}}}~{\rm [mJy]}$ |
| Secure merger fraction | 21% | ±3% | percent | 5 | we classify 50 ($21\%\pm3$%) of the red DSFGs as secure mergers |
| Median Re F444W | 1.78 | +1.42/-1.09 | kpc | 5 | $R_{e,\,{\rm F444W}}= 1.78^{+1.42}_{-1.09}$ kpc |
| Median Re F150W | 3.16 | +2.88/-1.72 | kpc | 5 | $R_{e,\,{\rm F150W}} = 3.16^{+2.88}_{-1.72}$ kpc |
| f_F444W–z fit slope | -0.36 | 0.02 | dex per unit (1+z) | 0 | \log(f_{\rm F444W}) = (-0.36 \pm 0.02) (1+z)  +(2.05 \pm 0.09) |

## Qualitative findings

- Faint and bright DSFGs have similar redshifts, stellar masses and morphologies; only SFR and L_IR differ.  
  > "These results suggest that the faint DSFGs are drawn from the same population of galaxies as the bright DSFGs." (abstract)

## Claim tuples

- H: Faint DSFGs belong to the same population as bright DSFGs | E: SED fits and GALFIT morphologies of 234 JWST-selected DSFGs split at 2 mJy | R: Lower SFR and L_IR in faint DSFGs but similar masses and morphologies | F: Faint DSFGs are drawn from the same population | **supported**
- H: Near-IR flux traces redshift of DSFGs | E: Fit f_F444W and f_F150W versus z | R: Tight negative correlations | F: NIR flux may be used to select high-z DSFGs | **supported**
- H: DSFG merger fractions are lower in JWST than in HST studies | E: Visual classification of mergers | R: 21% secure mergers | F: Dust attenuation may have inflated earlier HST merger rates | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Relaxed color cut F444W/F150W>2.5 rejected because ~800 vs ~450 galaxies reduce efficiency  
  > "the efficiency decreases drastically as we go to lower $\ensuremath{f_{\rm F444W}}/\ensuremath{f_{\rm F150W}}$ ratios" (3.1 Red NIRCam Galaxies)
- How they decided it was enough: _not stated_
- Limitation (authors): Visual merger classifications are subjective and may miss minor mergers.  
  > "These visual classifications are inherently subjective" (5.2 Identifying Mergers)
- Limitation (authors): Stellar masses depend on the assumed attenuation curve (~0.4 dex).  
  > "it has been shown that the choice of the (cite: charlot00) attenuation curve can increase stellar mass measurements for SMGs by $\sim0.4$ dex" (4.3 SED Results)
- Caveat (inferred, ours): ALMA plays a supporting role via published catalogs; sample is mostly SCUBA-2-prior-selected with ~10% false positives
- Caveat (inferred, ours): Single-Sérsic fits and visual merger classes are subjective
- Caveat (inferred, ours): Selection incomplete (~83%), biased against high-z/faint NIR sources

## Reproducibility

- Data public (paper): Public JWST (MAST) and ALMA published catalogs/images used  
  > "We use the publicly available primary beam-corrected mosaics for both fields." (3.2 Submillimeter/millimeter Properties of Red NIRCam Galaxies)
- Products in archive: _not stated_
- Missing: SCUBA-2 maps and reduction
- Missing: Full BAGPIPES configuration files
- Missing: GALFIT setup details
- Data volume (inferred): Tens of GB (catalogs, NIRCam mosaics, SCUBA-2 and ALMA mosaics)
- Score (inferred): 3/5, Uses public catalogs and standard tools, but ALMA role is minor and several parameters are unstated.
- Rediscovery candidate: no, ALMA data are used only as published catalogs/mosaics; the main results rely on JWST/SCUBA-2 and many unstated fit settings.

## Links

- Method: (cite: barger23) (Red NIRCam color selection and SCUBA-2 prior method)
- Method: (cite: mckay24) (Verification of the prior-based selection with ALMA)
- Companion: (cite: fujimoto25) (DUALZ ALMA survey in A2744)
- Companion: (cite: hatsukade18) (ASAGAO 1.2 mm GOODS-S image)
- Related: JADES
- Related: UNCOVER
- Related: GLASS-JWST
- Related: DUALZ
- Related: ASAGAO
- Related: GOODS-ALMA
- Related: ALCS
- Related: AFFS

## Checks

```json
{
 "quotes": 78,
 "quotes_ok": 78,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 10,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 91,
  "stated": 53,
  "rate": 0.582
 },
 "evidence_ok": true
}
```

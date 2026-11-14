# The ALPINE-ALMA [CII] survey. The nature, luminosity function, and star formation history of dusty galaxies up to z ≃ 6

`2020A&A...643A...8G` | Astronomy and Astrophysics 2020 | first author: Gruppioni, C. | arXiv: 2006.04974 | DOI: 10.1051/0004-6361/202038487

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies
- Question: What is the nature, total IR luminosity function and contribution to the cosmic SFRD of dusty galaxies serendipitously detected in ALPINE continuum up to z~6, including optically/near-IR dark ones?  
  > "These sources, detected in COSMOS and ECDFS, have been used to derive the total infrared luminosity function (LF) and to estimate the cosmic star formation rate density (SFRD) up to $z$$\simeq$6." (abstract)
- Target **56 serendipitous continuum sources in ALPINE pointings (COSMOS and ECDFS)**: coordinates _not stated_; z/distance 0.5<z<6 (median z~2.84)  
  > "consists of 56 sources, of which three are in the ECDFS and 53 are in COSMOS, and which were extracted over a total area of 24.92 arcmin$^2$" (2 The ALPINE serendipitous continuum detections); distance from catalogue spectroscopic/photometric redshifts, [CII] lines, LE PHARE photo-z  
  > "consists of 56 sources, of which three are in the ECDFS and 53 are in COSMOS, and which were extracted over a total area of 24.92 arcmin$^2$" (2 The ALPINE serendipitous continuum detections)

## Data provenance

- ALMA projects: _none stated_
- bands: ALMA band 7 (~860 and ~1000 um)  
  > "serendipitously detected in continuum at $\sim$860 and $\sim$1000 $\mu$m (ALMA band 7)" (Introduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: average synthesized beam 1.13x0.85 arcsec^2  
  > "The average synthesized beam size is 1.13$\times$0.85 arcsec$^2$" (2 The ALPINE serendipitous continuum detections)
- max recoverable scale: _not stated_
- sensitivity: nominal 860-um limiting flux 0.3 mJy  
  > "the nominal 860-$\mu$m limiting flux of our survey, that is, 0.3 mJy" (4.2)
- time on source: ~30 minutes per target; 70-hour survey  
  > "Each target was observed for $\sim$30 minutes of on-source integration time" (2 The ALPINE serendipitous continuum detections)
- observing dates: Cycle 5 and 6, completed February 2019  
  > "were carried out in band 7 during Cycle 5 and Cycle 6, and were completed in February 2019" (2 The ALPINE serendipitous continuum detections)
- pi or archival as stated: _not stated_
- Line: [CII] 158 um (not stated)
- Other facility **HST, Subaru, UltraVISTA, Spitzer IRAC/MIPS, Herschel, VLA and other multiwavelength surveys**: ancillary photometry/catalogues for counterpart identification and SED fitting  
  > "We took advantage of the great wealth of multi-wavelength ancillary data, catalogues, spectroscopic and photometric redshifts, and deep images" (3 The nature of the ALPINE serendipitous sources)
- External data: Continuum source catalogue, fluxes, completeness/effective area simulations  
  > "The completenesses were derived through accurate simulations by (cite: bethermin20)." (4.1 Method) [from (cite: bethermin20)]
- External data: Serendipitous [CII] line catalogue  
  > "providing two independent catalogues of emission-line ((cite: loiacono20)) and continuum ((cite: bethermin20)) detections" (Introduction) [from (cite: loiacono20)]
- External data: Multiwavelength catalogues and photo-z (COSMOS2015, 3D-HST, super-deblended, UltraVISTA DR4)  
  > "we first matched the ALMA non-target list with the 3D-HST catalogues" (3 The nature of the ALPINE serendipitous sources) [from (cite: laigle16); (cite: jin18); (cite: brammer12)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 5.4.0  
  > "version 5.4.0, and the continuum maps were obtained by collapsing the line-free channels in all the spectral windows" (2 The ALPINE serendipitous continuum detections)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean down to 3 sigma threshold  
  > "The data cubes were imaged using the `tclean` CASA routine down to a flux threshold of 3$\sigma$" (2 The ALPINE serendipitous continuum detections)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "A natural weighting of the visibilities was applied in order to maximise the point-source sensitivity" (2 The ALPINE serendipitous continuum detections)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: line-contaminated channels masked; continuum from line-free channels  
  > "new tailored continuum maps were produced by masking the potentially line-contaminated channels and then remeasuring the continuum flux" (2 The ALPINE serendipitous continuum detections)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Data reduction, flux extraction, source selection, completeness and flux uncertainties  
  > "are comprehensively discussed in (cite: bethermin20)" (2 The ALPINE serendipitous continuum detections) [from (cite: bethermin20)]
- Description of ancillary data in fields  
  > "are presented in (cite: faisst20)" (3 The nature of the ALPINE serendipitous sources) [from (cite: faisst20)]

### Not stated but needed to reproduce (our reading)

- tclean parameters (cell, image size, masks, niter), line-free channel lists
- Exact source catalogue with fluxes and positions (in Bethermin+20)
- LE PHARE configuration, template list details and redshift PDFs per source
- MCMC sampler/software, likelihood, number of walkers and steps
- Stacking procedure details
- Completeness tables needed for Vmax

## Analysis recipe

1. **Select serendipitous continuum sources**: Peak search on SNR maps with find_peak; SNR>5 outside 1 arcsec central region (95% purity)  
  > "the threshold above which we obtain a purity of 95% corresponds to an SNR$=$5 outside the central region of 1 arcsec radius" (2)
   - software: astropy, CASA
   - fitting: _not stated_
   - validation: Simulations in Bethermin+20; inverted-map spurious estimate  
  > "2.8$^{+2.9}_{-1.6}$ (see (cite: bethermin20))" (3.1.2)
2. **Identify counterparts**: Cross-match with catalogues within 1 arcsec, then visual inspection and ad-hoc IRAC aperture photometry  
  > "We found a counterpart within 1 arcsec of the source position for all three GOODS-S galaxies in the 3D-HST catalogue" (3.1.1)
   - fitting: _not stated_
   - validation: Monte Carlo random shifts give <=2 spurious matches  
  > "we find an average number of spurious matches $\lesssim$2" (3.1.1)
3. **SED fitting for L_IR, photo-z, stellar mass**: LE PHARE chi2 fit with 32 templates plus far-IR libraries; redshift fixed to literature/[CII]; BC03 for masses; L_IR integrated 8-1000 um  
  > "The final set of templates (32 in total) included SEDs of different types of galaxies" (3.2.1)
   - software: LE PHARE
   - parameter: E(B-V) 0.0 to 5  
  > "E(B–V) from 0.0 to 5" (3.2.1)
   - assumption: Chabrier IMF  
  > "we use a (cite: chabrier03) stellar initial mass function (IMF)" (Introduction)
   - fitting: _not stated_
   - validation: Consistency of fitted SED with literature photo-z  
  > "we found good consistency between the photo-$z$ from the literature and the best fit SED" (3.2.1)
4. **Derive luminosity functions**: 1/Vmax in five redshift bins, 0.5 dex luminosity bins overlapping by 0.25 dex; Monte Carlo (100 iterations) over photo-z PDFs for errors, versus Poisson  
  > "We iterated the computation of the monochromatic and total IR LFs 100 times" (4.3)
   - parameter: incompl(z)=1 for z<=6; cosmology H0=70, Om=0.3, OL=0.7  
  > "We adopted $incompl$($z$)$=$1 for $z$$\leq$6" (4.1 Method)
   - fitting: _not stated_
   - validation: _not stated_
5. **Fit modified Schechter function**: MCMC with sigma fixed to 0.5, flat priors on alpha, L*, phi*  
  > "we therefore fixed the value of $\sigma$ (the parameter shaping the bright-end slope) to that found for the *Herschel* LFs ($\sigma$$=$0.5)" (4.3)
   - parameter: log L* in [10,13], log phi* in [-5,-2], alpha in [-1,2]  
  > "log($L^{\star}$/L$_{\odot})$: \[10,13\]" (4.3)
   - fitting: _not stated_
   - validation: _not stated_
6. **Compute SFRD**: Integrate Schechter fit down to log L_IR=8; SFR=1.09e-10 L_IR (Kennicutt98, Chabrier)  
  > "SFR (M_{\odot} yr^{-1}) \simeq 1.09 \times 10^{-10}~L_{IR} (L_{\odot})" (5)
   - assumption: AGN contribution to L_IR small  
  > "If the overall contribution to the IR luminosity density from the AGN components of galaxies is small" (5)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.4.0: calibration and imaging (tclean)  
  > "version 5.4.0, and the continuum maps were obtained by collapsing the line-free channels" (2)
- **astropy** : find_peak source extraction  
  > "using the `find_peak` routine of `astropy`" (2)
- **LE PHARE** : SED fitting, photo-z, stellar masses  
  > "using the LE PHARE software" (3.2.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of continuum non-target sources | 56 | not stated | sources | 1 | consists of 56 sources |
| Median redshift | 2.84 | 0.18 | dimensionless | 3 | $z_{med}$$\simeq$2.84$\pm$0.18 |
| Median stellar mass | 4.1e10 | 0.7e10 | Msun | 3 | M$^*$$=$(4.1$\pm$0.7)$\times$10$^{10}$ M$_\odot$ |
| SFRD at 4.5<z<6 | 5.57e-2 (min 2.49e-2, max 1.51e-1) | see range | Msun/yr/Mpc^3 | 6 | / 4.5–6.0 / 5.57$\times$10$^{-2}$ / 2.49$\times$10$^{-2}$ / 1.51$\times$10$^{-1}$ / |
| SFRD at 2.5<z<3.5 | 1.23e-1 (min 8.57e-2, max 1.88e-1) | see range | Msun/yr/Mpc^3 | 6 | / 2.5–3.5 / 1.23$\times$10$^{-1}$ / 8.57$\times$10$^{-2}$ / 1.88$\times$10$^{-1}$ / |
| Dark galaxy SFRD contribution at z~5 | 0.9e-2 | 0.7e-2 | Msun/yr/Mpc^3 | 6 | (0.9$\pm$0.7)$\times$10$^{-2}$ M$_\odot$ yr$^{-1}$ Mpc$^{-3}$ at $z$$\simeq$3 and 5 |
| Fraction of HST+near-IR dark galaxies | 14% | not stated | percent | 2 | About 14% of all the ALPINE serendipitous continuum sources are found to be optically and near-infrared (near-IR) dark |
| Schechter alpha at 4.5-6.0 | 1.28 | +0.46/-0.48 | dimensionless | 5 | / 4.5–6.0 / 1.28$^{+0.46}_{-0.48}$ |

## Qualitative findings

- The IR LF shows no appreciable evolution in shape or normalisation from z~0.5 to 6, with a flat faint end.  
  > "there does not seem to be any appreciable evolution from $z$$\sim$0.5 to $z$$\sim$6, both in shape and normalisation" (4.3)

## Claim tuples

- H: Dusty galaxies contribute significantly to SFRD at z>3 beyond UV estimates | E: Integrate total IR LF from ALPINE serendipitous sources | R: SFRD flat from z~2 to 6, up to ~10x above UV at z~6 | F: UV surveys miss substantial obscured star formation at high z | **supported**
- H: HST+near-IR dark galaxies contribute notably to SFRD and stellar mass | E: Identify dark sources, sum SFR and masses | R: ~17% of SFRD at z~5; dark galaxies could dominate the high-mass end at z>3 | F: dark galaxies are significant but not the main source of the UV vs IR difference | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Redshifts and masses of dark galaxies are extremely uncertain; LF errors large; ALPINE mostly samples faint end.  
  > "the stellar masses derived for the HST and near-IR dark galaxies are extremely uncertain" (3.2.4)
- Caveat (inferred, ours): Photo-z of mid-IR-only sources poorly constrained; strong effect on LF at z>4.5
- Caveat (inferred, ours): Extrapolation of Schechter fit to 1e8 Lsun drives SFRD
- Caveat (inferred, ours): incompl=1 assumption for unidentified sources
- Caveat (inferred, ours): Possible overdensity association of [CII] emitters

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Source catalogue and completeness from Bethermin+20
- Missing: LE PHARE settings and photometry
- Missing: MCMC details
- Data volume (inferred): Large (118 pointings, ~70 h; hundreds of GB raw); reproduction can start from catalogues
- Score (inferred): 5/5, Analysis relies heavily on external catalogues and Bethermin+20; LF method is described but several settings are missing.
- Rediscovery candidate: no, Needs the companion catalogue, completeness simulations and multiwavelength photometry not given here.

## Links

- Method: (cite: bethermin20) (ALPINE continuum data reduction, source extraction and completeness)
- Companion: (cite: loiacono20) (serendipitous [CII] line sources and LF)
- Companion: (cite: faisst20) (ALPINE ancillary data)
- Related: ALPINE
- Related: COSMOS
- Related: ECDFS
- Related: GOODS-ALMA
- Related: ASAGAO
- Related: ASPECS

## Checks

```json
{
 "quotes": 49,
 "quotes_ok": 49,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2017.1.00428.L"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 37,
  "rate": 0.481
 },
 "evidence_ok": true
}
```

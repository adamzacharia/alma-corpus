# Revealing the Stellar Mass and Dust Distributions of Submillimeter Galaxies at Redshift 2

`2019ApJ...879...54L` | The Astrophysical Journal 2019 | first author: Lang, Philipp | arXiv: 1905.06960 | DOI: 10.3847/1538-4357/ab1f77

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies
- Question: How do the spatial distributions of dust-obscured star formation (ALMA 870 um) and stellar mass (from M/L-corrected HST colors) compare in z~2 SMGs, and what does this imply for SMG formation mechanisms and descendants?  
  > "Here, we extend these studies to investigate the formation mechanisms of SMGs by combining information on the resolved distribution of both the dust-obscured" (1. INTRODUCTION)
- Target **20 SMGs (14 AS2UDS, 3 ALESS, 3 AzTEC/COSMOS) at 1.7<z<2.6**: coordinates _not stated_; z/distance median z = 2.15 (range 1.7-2.6)  
  > "Our sample has a median redshift and scatter of z = 2.15 and 0.26, respectively. 16 galaxies out of our final sample have spectroscopic redshift information." (2.5 Final sample properties); distance from spectroscopic or photometric redshifts from literature (Table 1)  
  > "Our sample has a median redshift and scatter of z = 2.15 and 0.26, respectively. 16 galaxies out of our final sample have spectroscopic redshift information." (2.5 Final sample properties)

## Data provenance

- ALMA projects: 2012.1.00090.S, 2015.1.01528.S, 2016.1.00434.S, 2017.1.01492.S, 2013.1.00118.S, 2012.1.00307.S
- bands: Band 7 (870 um) for AS2UDS and ALESS; Band 6 (1.3 mm) for AzTEC  
  > "c) Observed ALMA Band." (Table 1); "We use the sample of SMGs detected with the ALMA Band 6 (1.3 mm) follow-up of bright AzTEC sources in the COSMOS field." (2.1.3 COSMOS)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: AS2UDS 0.19-0.35 arcsec; high-res sample FWHM<0.4 arcsec; low-res sources 0.8-2.1 arcsec  
  > "The ALMA images for AS2UDS sources used in this analysis have an angular resolution of FWHM = 0 [′′] . 19-0 [′′] . 35." (2.1.1 UDS); "(ranging from 0 [′′] . 8 to 2 [′′] . 1)" (2.5 Final sample properties)
- max recoverable scale: _not stated_
- sensitivity: AS2UDS median sigma870 = 0.25 (Cy1), 0.34 (Cy3), 0.23 (Cy4), 0.085 (Cy5) mJy/beam; AzTEC rms 0.1 mJy/beam; ALESS median 0.4 mJy/beam  
  > "The final detection maps have median depths of σ 870 =" (2.1.1 UDS)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Public archival programs from AS2UDS, ALESS and AzTEC surveys; COSMOS images from A3COSMOS archive project  
  > "cleaned images for all publicly available ALMA continuum observations in COSMOS" (2.1.3 COSMOS)
- Other facility **HST/CANDELS WFC3**: J125 and H160 imaging used for color maps, M/L and stellar mass maps  
  > "from which we use the J 125 and H 160 filters observed with the WFC3 instrument." (2.2 HST imaging)
- Other facility **Spitzer/IRAC 3.6um**: used to align HST astrometry  
  > "aligned the H 160 -band images to the Spitzer / IRAC 3.6µm image of the full ECDFS and UDS fields." (2.2 HST imaging)
- External data: Deboosted, primary-beam-corrected 870 um flux densities for AS2UDS  
  > "Deboosted and primary beam-corrected flux densities are taken from (Stach et al. 2018)." (2.1.1 UDS) [from Stach et al. 2018]
- External data: Magphys stellar masses and SFRs for AzTEC sources  
  > "Stellar properties for our AzTEC sources are taken from Miettinen et al. (2017) who employ SED-modeling with Magphys." (2.3 Ancillary data and integrated galaxy properties) [from Miettinen et al. (2017)]
- External data: Magphys fits for AS2UDS SMGs  
  > "For all AS2UDS SMGs, fits with Magphys are taken from Dudzeviciute et al. (in prep)." (2.3 Ancillary data and integrated galaxy properties) [from Dudzeviciute et al. (in prep)]
- External data: Main sequence position  
  > "The solid and dotted lines represent the main sequence (adopted from Whitaker et al. 2014)" (Figure 2) [from Whitaker et al. 2014]
- External data: Quiescent z=1.5 ETG size-mass relation  
  > "Their sizes and surface densities are measured by van der Wel et al. (2014)" (5.1 Connection of SMGs to present-day ETGs) [from van der Wel et al. 2014]
- External data: Local spiral dust/stellar size ratio 0.95  
  > "(with R e,dust /R e,∗ = 0.95)" (4.4 Systematic trends with global SF properties) [from Hunt et al. (2015)]
- Simulation/model as data: Bruzual & Charlot (2003) synthetic SEDs with Chabrier IMF, Calzetti extinction, various SFHs used to calibrate J125-H160 vs M/L_H relation  
  > "We calibrate the (J 125 − H 160 )-M/L [∗] H relation by constructing synthetic galaxy SEDs based on Bruzual & Charlot (2003) models." (3.1.2 Conversion from light to stellar mass)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: AS2UDS/ALESS images from published works; AzTEC images from A3COSMOS cleaned archive images  
  > "The ALMA imaging for ALESS sources is taken from Cycle 0 observations Hodge et al. (2013)." (2.1.2 ECDFS)
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
- final beam: Major axis beam FWHM 0.18-0.35 arcsec for high-res sample (Table 1)  
  > "e) Major axis beam FWHM size of the ALMA imaging." (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- ALMA data reduction/imaging for AS2UDS  
  > "A full description can be found in (Stach et al. 2018, 2019; Simpson et al. 2015a,b)." (2.1.1 UDS) [from Stach et al. 2018, 2019; Simpson et al. 2015a,b]
- Details of AzTEC image production  
  > "(see Liu et al. 2019 submitted for details)" (2.1.3 COSMOS) [from Liu et al. 2019 submitted]
- Gas mass conversion from 870um flux  
  > "and follow thereby the recipe of Schinnerer et al. (2016)." (5.1 Connection of SMGs to present-day ETGs) [from Schinnerer et al. (2016); Groves et al. (2015)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration/imaging details (CASA version, weighting, robust, cleaning) for each dataset not given
- Target S/N and segmentation thresholds per source for Voronoi binning/SExtractor
- Initial GALFIT parameters and masks per source
- Details of R_e,beam resolvability handling
- Final per-source ALMA rms
- Exact SFR values used for hidden-mass test and gas mass results

## Analysis recipe

1. **Select sample**: Select SMGs with 1.7<z<2.6, CANDELS coverage, sufficient J125/H160 S/N, and no AGN, giving 20 sources  
  > "After applying these selection criteria, a total of 20 SMGs are considered for the final sample" (2.4 Sample selection)
   - fitting: _not stated_
   - validation: K-S tests of Ks and S870 vs parent samples  
  > "Applying a Kolmogorov-Smirnov (K-S) test, we find that the distributions of both K s -band magnitude and S 870 are not significantly (≥ 3σ) different" (2.5 Final sample properties)
2. **Build J125-H160 color maps**: PSF-match J125 to H160 with stacked PSFs, Voronoi-bin to target S/N, divide images  
  > "The Voronoi-binning is then performed on all pixels within the segmentation map of each galaxy, adopting a target S/N in the range of 10-15." (3.1.1 Derivation of color maps)
   - software: PYRAF PSFMATCH, Voronoi binning, SExtractor
   - parameter: segmentation threshold 1.5-3 times background rms  
  > "(within the range of 1.5-3 times the background r.m.s noise)" (3.1.1 Derivation of color maps)
   - fitting: _not stated_
   - validation: Checked PSF-matching introduces no artificial radial color gradients  
  > "We test the quality of the PSF-matching by ensuring that no artificial radial" (3.1.1 Derivation of color maps)
3. **Convert color to M/L and stellar mass maps**: Calibrate color-M/L_H relation from BC03 models, apply at each SMG's redshift, extrapolate to background, multiply by H160 image  
  > "We then multiply these extrapolated M/L [∗] H [maps] [with] [the] [H] [160] [-band] [image] [to] obtain the final stellar-mass distributions." (3.1.3 Final stellar-mass maps)
   - parameter: Metallicity 0.2 and 1 solar; tau 50 Myr-3 Gyr to constant SFR; A_V 0-8  
  > "We adopt models with a Chabrier (2003) IMF, two values for metallicities (0.2 and 1 times the solar value)" (3.1.2 Conversion from light to stellar mass)
   - assumption: Foreground dust screen with Calzetti law, Chabrier IMF  
  > "we consider a Calzetti et al. (2000) extinction law, assuming a foreground dust screen with a range of A V from 0 to 8." (3.1.2 Conversion from light to stellar mass)
   - fitting: _not stated_
   - validation: Compared with Magphys masses; appendix tests with burst models  
  > "We compare the total stellar mass from the best-fit model to the stellar mass from Magphys in Figure 4." (3.1.3 Final stellar-mass maps)
4. **Fit structural parameters**: GALFIT Sersic fits in the image plane to H160, mass maps and ALMA images; errors from 150 perturbed realizations  
  > "we repeat the fitting 150 times varying the central position according to a Gaussian distribution with σ equal to the uncertainty in the mass centroid position." (3.2 Structural parameters)
   - software: GALFIT
   - parameter: 6x6 arcsec cutouts; mass/light center fixed to mass-weighted center; ALMA center free; PSF = Gaussian clean beam  
  > "During our fits, we allow the center position to vary freely" (3.2 Structural parameters)
   - fitting: Sersic profile, 68% confidence intervals from 150 perturbed fits  
  > "The final errors of R e and n for a given source are then derived from the upper and lower 68% confidence interval" (3.2 Structural parameters)
   - validation: Image-plane fits stated consistent with uv-fits from previous studies  
  > "We chose to fit in the image plane since recent studies have shown that this provides consistent results compared to uv-fits" (3.2 Structural parameters)
5. **Compare dust and stellar sizes and offsets vs sSFR; test hidden mass**: Compute size ratios, centroid offsets, cumulative profiles; plot vs sSFR; add toy hidden burst mass distributed like dust  
  > "We assume a burst timescale of 150 Myr" (4.3 The case of strongly dust-obscured centers)
   - assumption: dust emission traces obscured star formation with spatially uniform dust properties  
  > "relying on the assumption that the dust properties (e.g., dust temperature) do not strongly vary spatially" (4.4 Systematic trends with global SF properties)
   - fitting: _not stated_
   - validation: Hidden-mass test shows only marginal change  
  > "However, the difference to our median stellar-mass profile is only marginal" (4.3 The case of strongly dust-obscured centers)

## Software

- **GALFIT** : 2D Sersic fitting of H160, mass maps and ALMA images  
  > "using Galfit (Peng et al. 2010)" (3.2 Structural parameters)
- **Magphys** updated version (da Cunha et al. 2015): integrated stellar masses and SFRs  
  > "SED fitting was carried out with an updated version of Magphys" (2.3 Ancillary data and integrated galaxy properties)
- **SExtractor** : source catalogs and segmentation maps  
  > "by creating segmentation maps with Sextractor" (3.1.1 Derivation of color maps)
- **Voronoi binning** Cappellari & Copin 2003: binning color maps  
  > "we perform a Voronoi-binning scheme (Cappellari & Copin 2003)" (3.1.1 Derivation of color maps)
- **PYRAF PSFMATCH** : PSF matching kernel  
  > "we use the PYRAF task PSFMATCH to construct a smooth" (3.1.1 Derivation of color maps)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median R_e,submm | 2.0 | ±0.1 | kpc | 4 | with a median size of ⟨R e,submm ⟩ = 2.0 ± 0.1 kpc |
| Median R_e,mass | 2.7 | ±0.3 | kpc | 4 | R e,H160 = 4.8 ± 0.3 kpc and R e,mass = 2.7 ± 0.3 kpc |
| Median R_e,H160 | 4.8 | ±0.3 | kpc | 4 | R e,H160 = 4.8 ± 0.3 kpc and R e,mass = 2.7 ± 0.3 kpc |
| Median Re,submm/Re,mass | 0.6 | ±0.2 | dimensionless | 5 | ⟨R e,submm /R e,mass ⟩ = 0.6 ± 0.2 |
| Median Re,mass/Re,H160 | 0.5 | ±0.1 | dimensionless | 4 | ⟨R e,mass /R e,H160 ⟩ = 0.5 ± 0.1 |
| Median dust-stellar centroid offset | 1.1 | accuracy 0.7 kpc | kpc | 5 | the centroid position of the dust distribution agrees with a median offset of 1.1 kpc |
| Median Sersic index of mass | 1.4 | ±0.4 | dimensionless | 4 | a median of n mass = 1.4 ± 0.4 |
| Offset of Magphys mass vs mass maps | 0.3 | scatter 0.3 dex | dex | 3 | M ∗ (SED) being increased by about 0.3 dex with respect to our integrated stellar-mass maps |
| Hidden burst mass fraction | 20 | not stated | percent | 5 | a hidden burst component could produce on average 20 % of the total stellar mass of our sample |

## Qualitative findings

- Dust emission is more compact than stellar mass irrespective of sSFR; SMG stellar sizes and densities match z=1.5 quiescent galaxies  
  > "This ratio does not change with specific star-formation rate (sSFR) over the factor of 30 spanned by our targets" (abstract)

## Claim tuples

- H: Is dust spatially decoupled from stellar mass in SMGs? | E: Compare ALMA 870um and M/L-corrected mass map centroids | R: Median offset 1.1 kpc vs accuracy 0.7 kpc | F: Good overall spatial agreement between dust and stellar mass | **supported**
- H: Is dust more compact than stars, and does this depend on sSFR? | E: GALFIT sizes vs sSFR | R: Median ratio 0.6, no correlation with sSFR | F: Centrally enhanced star formation in SMGs unlike local spirals | **supported**
- H: Are SMGs the progenitors of passive z~1.5 galaxies? | E: Compare sizes and surface densities with van der Wel et al. 2014 | R: Good agreement | F: Consistent with SMGs being descendants | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Optical light is affected by dust, so color-based M/L corrections recover the underlying mass distribution  
  > "it is possible to recover the underlying stellar mass distributions of galaxies and search for radial gradients in color and hence M/L [∗]" (1. INTRODUCTION)
- How they decided it was enough: _not stated_
- Limitation (authors): Foreground dust screen assumption means mass maps are a lower limit to central mass; sample biased to optically bright SMGs  
  > "Due to the high central column densities of dust in our SMGs, our mass distributions likely represent a lower limit to the true central mass density." (abstract)
- Caveat (inferred, ours): Small sample (14 high-resolution) with heterogeneous ALMA resolutions
- Caveat (inferred, ours): M/L from single color with 0.2-0.5 dex systematic uncertainty
- Caveat (inferred, ours): Image-plane fits of low-S/N ALMA data; 3 AS2UDS sources near beam size
- Caveat (inferred, ours): Optically bright selection biases against heavily obscured SMGs

## Reproducibility

- Data public (paper): Acknowledgements list ALMA project data; COSMOS images from public A3COSMOS archive  
  > "cleaned images for all publicly available ALMA continuum observations in COSMOS" (2.1.3 COSMOS)
- Products in archive: _not stated_
- Missing: Calibrated ALMA images of AS2UDS/ALESS (from companion papers)
- Missing: Dudzeviciute et al. Magphys results (in prep)
- Missing: Per-source GALFIT/SExtractor settings
- Data volume (inferred): ~50-200 GB for ALMA archive data of several projects (images only much less); HST CANDELS mosaics several GB
- Score (inferred): 3/5, Data public and methods described, but key parameters and ALMA imaging details are inherited from other papers and per-source settings missing.
- Rediscovery candidate: no, Requires many inherited products and unreleased per-source settings, though results are numeric.

## Links

- Method: Peng et al. 2010 (GALFIT)
- Method: Cappellari & Copin 2003 (Voronoi binning)
- Method: da Cunha et al. 2015 (Magphys SED fitting)
- Companion: Stach et al. 2018 (AS2UDS catalog)
- Companion: Hodge et al. 2013 (ALESS survey)
- Companion: Miettinen et al. 2017 (AzTEC COSMOS catalog)
- Companion: Hodge et al. 2016 (high-resolution ALESS)
- Related: AS2UDS
- Related: ALESS
- Related: A3COSMOS
- Related: CANDELS

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
 "obscore_codes_not_in_card": [
  "2011.0.00294.S"
 ],
 "codes_printed_but_missing": [
  "2011.0.00294.S",
  "2012.0.00307.S"
 ],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 46,
  "rate": 0.561
 },
 "evidence_ok": true
}
```

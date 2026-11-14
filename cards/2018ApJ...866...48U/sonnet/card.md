# A Cool Core Disturbed: Observational Evidence for the Coexistence of Subsonic Sloshing Gas and Stripped Shock-heated Gas around the Core of RX J1347.5-1145

`2018ApJ...866...48U` | The Astrophysical Journal 2018 | first author: Ueda, Shutaro | arXiv: 1808.09232 | DOI: 10.3847/1538-4357/aadd9d

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: galaxy_clusters_and_sz
- Question: Does the cool core of RX J1347.5-1145 slosh sub-sonically, and is the southeast substructure shock-heated stripped gas from an infalling subcluster, from joint Chandra, ALMA SZE and HST lensing data?  
  > "In this paper, we investigate the merger phenomena and merger history in RX J1347.5–1145 by combining the data of *Chandra*, ALMA, and *HST*." (Introduction)
- Target **RX J1347.5-1145**: coordinates _not stated_; z/distance z = 0.451  
  > "RX J1347.5–1145 is one of the most luminous X-ray galaxy clusters and is located at the redshift of $z = 0.451$." (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00246.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: unsmoothed SZE image with synthesized beam 4.1'' x 2.5'' FWHM  
  > "we used the unsmoothed SZE image with the synthesized beam size of $4.1'' \times 2.5''$ FWHM (cite: Kitayama16) in the SZE imaging analysis." (3.1 X-ray and SZE imaging analysis)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **Chandra ACIS**: X-ray images and spectra (ObsIDs 506, 507, 3592, 13516, 13999, 14407)  
  > "Two out of six datasets we used were taken by ACIS-S (ObsID: 506 and 507) and the others were by ACIS-I (ObsID: 3592, 13516, 13999, and 14407)." (Observations and Data Reductions)
- Other facility **HST ACS**: F475W, F814W, F850LP images for strong-lensing mass modeling  
  > "The data consisted of F475W, F814W, and F850LP images from the ACS, which were used in (cite: Halkola08), (cite: Kohlinger14), and (cite: Zitrin15)." (Observations and Data Reductions)
- External data: Missing-flux correction parameter c1=0.88 from imaging simulations  
  > "We set $f_c$ to be equal to the parameter $c_1=0.88$ in Equation (2) of (cite: Kitayama16) derived from detailed imaging simulations for RX J1347.5–1145" (3.3 Combined analysis of SZE and X-ray imaging data for the excess component) [from (cite: Kitayama16)]
- External data: Multiple-image identifications used as lensing constraints  
  > "These multiple images are identified in previous work on this cluster (cite: Halkola08; Kohlinger14; Zitrin15)." (4.1 Central mass distribution) [from (cite: Halkola08; Kohlinger14; Zitrin15)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 6% ALMA flux calibration  
  > "the 6 % uncertainty of the ALMA flux calibration (cite: Kitayama16)" (3.5 Systematic uncertainty of the ICM properties)
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
- final beam: 4.1'' x 2.5'' FWHM  
  > "synthesized beam size of $4.1'' \times 2.5''$ FWHM" (3.1 X-ray and SZE imaging analysis)
- final rms: _not stated_

### Inherited from earlier work

- ALMA SZE data and reduction same as earlier paper  
  > "The ALMA SZE data used in this paper are the same as those in (cite: Kitayama16)" (Observations and Data Reductions) [from (cite: Kitayama16)]
- Chandra data reduction same as earlier paper  
  > "The data reduction is also the same as in (cite: Kitayama16)" (Observations and Data Reductions) [from (cite: Kitayama16)]
- Mean-profile ellipse subtraction method  
  > "excluding the southeast quadrant (i.e., the substructure), following (cite: Ueda17)" (3.1 X-ray and SZE imaging analysis) [from (cite: Ueda17)]

### Not stated but needed to reproduce (our reading)

- ALMA imaging parameters (weighting, deconvolver, cell size, masking, uv range) are only in Kitayama et al. 2016
- ALMA calibration details and flux calibrator
- Conversion of ALMA SZE to pressure/Compton y and residual SZE noise levels
- Exact regions and pixel selection for the equation-of-state measurement
- GLAFIC priors and MCMC settings

## Analysis recipe

1. **Residual X-ray and SZE images**: Fit ellipse minimizing variance in 15''<r<35'' annulus excluding SE quadrant, subtract mean profile from X-ray and SZE images  
  > "we searched for the ellipse that minimizes the variance of the X-ray surface brightness relative to its mean in a $15'' < \bar{r} < 35''$ annulus" (3.1 X-ray and SZE imaging analysis)
   - software: CASA
   - parameter: axis ratio 0.66, position angle -8.7 deg  
  > "We find that the axis ratio of the ellipse is 0.66 and its position angle is $-8.7^{\circ}$" (3.1 X-ray and SZE imaging analysis)
   - fitting: _not stated_
   - validation: Repeated with smoothed X-ray image and circular symmetry; SE substructure unaffected  
  > "the geometry of the mean profile does not affect the substructure in the southeast quadrant" (3.1 X-ray and SZE imaging analysis)
2. **X-ray spectral temperatures of SE regions**: phabs*apec fits, then two-apec model with ambient temperature fixed  
  > "We then measured the temperature of the excess component ($kT_{\rm excess}$) by using the two `apec` model" (3.2 X-ray spectral analyses of the southeast substructure)
   - software: XSPEC
   - parameter: abundance fixed at 0.38 solar; NH = 4.6e20 cm^-2; L_excess = 150 kpc  
  > "we fixed the metal abundance of the ICM at 0.38 solar based on previous X-ray measurements (cite: Ota08)" (3.2 X-ray spectral analyses of the southeast substructure)
   - assumption: Collisional ionization equilibrium; line-of-sight extent 150 kpc  
  > "assuming that the ICM is in a collisional ionization equilibrium" (Observations and Data Reductions)
   - fitting: _not stated_
   - validation: _not stated_
3. **Joint X-ray + SZE temperature and density**: Solve X-ray and SZE intensity equations for n and kT per 5''x5'' pixel with relativistic correction and f_c=0.88  
  > "We then solved Equations ([\[eq:X\]](#eq:X)) and ([\[eq:SZ\]](#eq:SZ)) for $n_{\rm excess}$ and $kT_{\rm excess}$" (3.3 Combined analysis of SZE and X-ray imaging data for the excess component)
   - software: SPEX, CASA
   - parameter: pixels with S/N > 4 sigma in both  
  > "signal-to-noise ratios (S/N) of $\Delta I_{\rm X}$ and $\Delta I_{\rm SZ}$ are both over $4\sigma$" (3.3 Combined analysis of SZE and X-ray imaging data for the excess component)
   - fitting: _not stated_
   - validation: Consistent with spectral method; highest-T region in 2b  
  > "This result is consistent with that measured with an independent method using the X-ray spectra" (3.3 Combined analysis of SZE and X-ray imaging data for the excess component)
4. **Equation of state of perturbations**: w = Δp/Δρ with Δp from SZE residual and Δρ from X-ray residual; sqrt(w) compared with sound speed  
  > "The SZE residual image gives an estimate of the pressure perturbation $\Delta p$, whereas the X-ray residual image gives an estimate of the density perturbation $\Delta \rho$" (3.4 Nature of gas sloshing in the core)
   - parameter: line-of-sight depth 100 kpc for core; 150 kpc for SE  
  > "assuming the line-of-sight depth of 100 kpc" (3.4 Nature of gas sloshing in the core)
   - fitting: _not stated_
   - validation: _not stated_
5. **Strong-lensing mass model and DM cross-section limit**: GLAFIC parametrized NFW halos, member galaxies, multipole perturbations constrained by 21 images; MCMC errors; surface density within 25 kpc of subcluster peak gives sigma/m limit with tau<1  
  > "We used the `GLAFIC` software package (cite: Oguri10) for our mass modeling." (4.1 Central mass distribution)
   - software: GLAFIC, SExtractor
   - parameter: positional error 0.5'' for all images  
  > "We assumed a positional error of $0.5\ensuremath{''}$ for all the multiple images" (4.1 Central mass distribution)
   - fitting: MCMC; Gaussian priors on photometric redshifts of four image sets  
  > "we included Gaussian priors based on their photometric redshifts" (4.1 Central mass distribution)
   - validation: Three-halo model tested and rejected  
  > "We therefore neglect the third dark halo component in the rest of this paper." (4.1 Central mass distribution)

## Software

- **CASA** 5.1.1: ALMA imaging and SZE analysis  
  > "`CASA` version 5.1.1 for the SZE data analysis" (3.3 Combined analysis of SZE and X-ray imaging data for the excess component)
- **XSPEC** 12.9.1l: X-ray spectral fitting  
  > "we used `XSPEC` version 12.9.1$l$ (cite: Arnaud96)" (Observations and Data Reductions)
- **SPEX** 3.04.00: X-ray data analysis in combined analysis  
  > "We used `SPEX` version 3.04.00 for the X-ray data analysis" (3.3 Combined analysis of SZE and X-ray imaging data for the excess component)
- **CIAO** 4.9: Chandra data reduction  
  > "we used the updated versions, 4.9 and 4.7.5.1, of *Chandra* Interactive Analysis of Observations" (Observations and Data Reductions)
- **GLAFIC** : strong-lensing mass modeling  
  > "We used the `GLAFIC` software package (cite: Oguri10) for our mass modeling." (4.1 Central mass distribution)
- **SExtractor** : photometry for cluster member selection  
  > "MAG_APER of `SExtractor` (cite: Bertin96)" (4.1 Central mass distribution)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Equation-of-state velocity of core sloshing | 420 | +310/-420 | km/s | 4 | $\sqrt{w} = 420^{+310}_{-420}$ km s$^{-1}$ |
| Equation-of-state velocity of excess hot ICM | 1970 | ±150 | km/s | 4 | the velocity inferred from the equation of state of the excess hot ICM is $1970 \pm 150$ km s$^{-1}$ |
| Mach number | 1.68 | +0.69/-0.47 | dimensionless | 2 | we obtain ${\cal M} = 1.68^{+0.69}_{-0.47}$ |
| Thermal energy of excess electrons | 1.9e61 | ±0.1 stat ±0.7 sys | h^-2 erg | 3 | $(1.9 \pm 0.1\,({\rm stat.}) \pm 0.7\,({\rm sys.})) \times 10^{61}$ $h^{-2}$ erg |
| Subcluster virial mass | 2.8e14 | +2.4/-1.1 | h^-1 Msun | 5 | $2.8^{+2.4}_{-1.1} \times 10^{14}$ $h^{-1}$$M_\odot$ for the subcluster |
| DM self-interaction cross section upper limit (95% CL) | 3.7 | not stated | h^-1 cm^2 g^-1 | 5 | $\sigma_{\rm DM} / m < 3.7\,h^{-1}$ cm$^2$ g$^{-1}$ |

## Qualitative findings

- X-ray residual shows dipolar sloshing pattern in core with no SZE residual, implying isobaric, sub-sonic sloshing  
  > "we find no significant residual in the Sunyaev-Zel’dovich effect (SZE) image from the Atacama Large Millimeter/submillimeter Array (ALMA)" (abstract)

## Claim tuples

- H: Is core gas sloshing sub-sonic? | E: Compare X-ray and ALMA SZE residuals to derive equation of state | R: sqrt(w)=420 +310/-420 km/s vs sound speed ~1630 km/s | F: Sloshing is sub-sonic and isobaric | **supported**
- H: Is the SE excess shock-heated stripped gas from an infalling subcluster? | E: Joint X-ray/SZE temperature, equation of state, lensing mass peak offset | R: kT up to ~30 keV, velocity 1970 km/s, mass peak offset 5.5 sigma | F: Merger-related stripped, shock-heated gas | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Three-halo lensing model rejected as third component weakly constrained  
  > "The mass of the third component is weakly constrained to be $1.4 \times 10^{14}$ $h^{-1}$ $M_\odot$ (95% CL)." (4.1 Central mass distribution)
- How they decided it was enough: _not stated_
- Limitation (authors): Mass and concentration strongly correlated so mass systematic uncertainty may be large  
  > "The obtained mass and concentration parameter are correlated strongly, therefore the systematic uncertainty of the mass estimates might be large." (4.1 Central mass distribution)
- Caveat (inferred, ours): Line-of-sight depth assumptions drive the derived temperatures and densities
- Caveat (inferred, ours): Large uncertainty on sloshing velocity (consistent with zero)
- Caveat (inferred, ours): ALMA missing flux correction is inherited from a prior paper

## Reproducibility

- Data public (paper): Chandra ObsIDs listed and ALMA project cited; HST data from STScI  
  > "The scientific results of this paper are based in part on data obtained from the Chandra Data Archive: ObsID 506, 507, 3592, 13516, 13999, and 14407." (Acknowledgments)
- Products in archive: _not stated_
- Missing: ALMA imaging details from Kitayama et al. 2016
- Missing: MCMC settings for GLAFIC
- Missing: Region definitions for equation of state
- Data volume (inferred): Tens of GB for ALMA plus Chandra and HST archival data
- Score (inferred): 3/5, Public data and clear analysis chain, but ALMA processing is inherited and several settings are unstated.
- Rediscovery candidate: no, Multi-facility analysis with inherited ALMA reduction and incomplete settings.

## Links

- Method: (cite: Kitayama16) (ALMA SZE data reduction and missing-flux correction)
- Method: (cite: Ueda17) (Residual-image method)
- Method: (cite: Oguri10) (GLAFIC lensing code)

## Checks

```json
{
 "quotes": 47,
 "quotes_ok": 47,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 37,
  "rate": 0.463
 },
 "evidence_ok": true
}
```

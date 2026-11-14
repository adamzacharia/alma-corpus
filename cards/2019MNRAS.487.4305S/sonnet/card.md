# Testing star formation laws on spatially resolved regions in a z ≈ 4.3 starburst galaxy

`2019MNRAS.487.4305S` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Sharda, P. | arXiv: 1906.01173 | DOI: 10.1093/mnras/stz1543

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies, star_formation
- Question: Do the Kennicutt-Schmidt, KDM and SFK star formation relations predict the measured SFR surface density in resolved regions of the z~4.3 starburst AzTEC-1?  
  > "to predict $\Sigma_{\mathrm{SFR}}$ from three star formation relations in the literature." (abstract)
- Target **AzTEC-1**: coordinates RA 09h59m42.85s, Dec +02d29m38.23s  
  > "centered at RA = $09^\mathrm{h}59^\mathrm{m}42.85^\mathrm{s}$, Dec = $+02^{\circ}29'38.23''$" (Observations); "A follow-up survey by the Large Millimeter Telescope found its spectroscopic redshift to be $4.3420\pm0.0004$" (Introduction); z/distance z = 4.3420 ± 0.0004  
  > "centered at RA = $09^\mathrm{h}59^\mathrm{m}42.85^\mathrm{s}$, Dec = $+02^{\circ}29'38.23''$" (Observations); "A follow-up survey by the Large Millimeter Telescope found its spectroscopic redshift to be $4.3420\pm0.0004$" (Introduction); distance from LMT spectroscopic redshift (cite: 2015MNRAS.454.3485Y)  
  > "centered at RA = $09^\mathrm{h}59^\mathrm{m}42.85^\mathrm{s}$, Dec = $+02^{\circ}29'38.23''$" (Observations); "A follow-up survey by the Large Millimeter Telescope found its spectroscopic redshift to be $4.3420\pm0.0004$" (Introduction)

## Data provenance

- ALMA projects: 2015.1.01345.S, 2017.1.00300.S, 2017.A.00032.S
- bands: Band 7 (860 um) continuum; Band 3 (3.2 mm) continuum and CO(4-3)  
  > "ALMA observations of the $\lambda_{\mathrm{obs}}=860\,\ensuremath{\mu}m$ (Band 7) continuum emission in AzTEC-1" (Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.093'' x 0.072'' (624 x 483 pc)  
  > "The angular resolution of the data is $0.093\ensuremath{''} \times 0.072\ensuremath{''}$, corresponding to $624 \times 483\,\mathrm{pc}$ at $z \approx 4.3$" (Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: Band 7: November 2015; Band 3 and CO(4-3): Oct-Nov 2017  
  > "were carried out in November 2015" (Observations); "were procured between October and November 2017" (Observations)
- pi or archival as stated: _not stated_
- Line: CO J=4-3 (not stated)
- Other facility **LMT**: spectroscopic redshift  
  > "A follow-up survey by the Large Millimeter Telescope found its spectroscopic redshift to be $4.3420\pm0.0004$" (Introduction)
- External data: Total SFR from SED fit, 1186 (+36/-291) Msun/yr  
  > "By fitting the spectral energy distribution (SED) of the galaxy at multiple wavelengths, find $\mathrm{SFR^{tot}}=1186^{+36}_{-291}\,\mbox{$\mathrm{M}_{\ensuremath{\odot}}$}\,\mathrm{yr^{-1}}$." (3.1 Star Formation Rate) [from (cite: 2018Natur.560..613T)]
- External data: Total fluxes 17 mJy (860um), 273 uJy (3.2mm), CO(4-3) 1.8 Jy km/s  
  > "$S^{\mathrm{tot}}_{\mathrm{CO}}\,dv = 1.8\pm0.2\,\mathrm{Jy\,km\,s^{-1}}$" (Observations) [from (cite: 2018Natur.560..613T)]
- External data: Disc geometry for 3DBarolo: i=44 deg, PA=296 deg, centre  
  > "We fix the geometry of the galaxy to the best-fit parameters found by (cite: 2018Natur.560..613T)" (Kinematic Modelling) [from (cite: 2018Natur.560..613T)]

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
- smoothing: CO cube smoothed to 0.2'' only for 3DBarolo mask  
  > "A mask is built by smoothing the ALMA CO datacube to a resolution of 0.2$''$" (Kinematic Modelling)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Overall analysis method (SFR, gas mass, Mach number, relation tests)  
  > "Following the analysis presented in (cite: 2018MNRAS.477.4380S)" (Introduction) [from Sharda et al. 2018 (cite: 2018MNRAS.477.4380S)]
- Local linear velocity gradient fit and resolution check algorithm  
  > "we follow the analysis presented in Section 4 of , *i.e.,* we fit and subtract the local, linear velocity gradient in the regions" (3.2 Velocity Dispersion and Mach Number) [from Sharda et al. 2018 Sec. 4, 4.1]
- ALMA observations and data reduction  
  > "The observations and data reduction are described in detail in the respective articles." (Observations) [from (cite: 2016ApJ...829L..10I) and Tadaki et al. 2018 (cite: 2018Natur.560..613T)]
- r43 = 0.91 for CO excitation  
  > "We follow who set $r_{43}=0.91$ to ensure consistency between CO and C$\,$I gas masses" (3.3 Molecular Gas Mass) [from not given in text (citation stripped)]

### Not stated but needed to reproduce (our reading)

- Calibration, CASA version and imaging parameters of the archival data (deferred to other papers)
- Exact Gaussian fitting procedure and regions/software for the 2D fit
- Monte Carlo sample count and input distributions
- f_H2 value in KDM
- Which data products (cubes, moment maps) were used and how moment-1 maps were made
- Line-free channels and continuum subtraction
- 3DBarolo parameter details beyond ring width and mask

## Analysis recipe

1. **Measure region sizes and fluxes**: Fit 2D Gaussians to the 860 um continuum for nucleus and SF clump; integrate for flux; FWHM gives diameter  
  > "We model the starburst nucleus as a Gaussian and define its diameter to be the full width at half maximum (FWHM) of the resulting Gaussian fit" (Observations)
   - assumption: Regions approximated as spheres  
  > "can be approximated to first order as spherical regions, to estimate their volume densities" (Observations)
   - fitting: _not stated_
   - validation: CO map fit gives sizes within 14% and 21%  
  > "find an agreement with the $860\,\ensuremath{\mu}m$ continuum map for the sizes of the nucleus and the SF clump to within 14% and 21% respectively." (Observations)
2. **Derive SFR surface density**: Sigma_SFR = SFRtot x (S860/S860tot)/A with SFRtot from SED fit  
  > "$\Sigma_{\mathrm{SFR}}= \mathrm{SFR^{tot}} \times (S_{\,\nu,\,860\,\ensuremath{\mu}m}/S^{\mathrm{tot}}_{\,\nu,\,860\,\ensuremath{\mu}m})/A$" (3.1 Star Formation Rate)
   - fitting: Monte Carlo error propagation  
  > "We use a Monte Carlo analysis to estimate and propagate the uncertainties on all the parameters." (3 Physical Parameters)
   - validation: _not stated_
3. **Measure turbulent velocity dispersion and Mach number**: Fit and subtract local linear velocity gradient from CO(4-3) velocity map; Mach = sigma/cs  
  > "Then, the turbulent Mach number is given by: $\mathcal{M}= \sigma_{v,\mathrm{turb}}/c_{\mathrm{s}}$." (3.2 Velocity Dispersion and Mach Number)
   - software: 3DBarolo
   - assumption: Gas temperature 10-100 K, cs = 0.4±0.2 km/s  
  > "Assuming the temperature of the molecular gas in the two regions to be between 10-100 K, we find the sound speed as $c_{\mathrm{s}} = 0.4\pm0.2\,\mathrm{km\,s^{-1}}$" (3.2 Velocity Dispersion and Mach Number)
   - fitting: _not stated_
   - validation: Independent 3DBarolo tilted-ring fit gives 13 and 23 km/s (18 after linear gradient in clump)  
  > "The velocity dispersions we obtain for the nucleus and the SF clump are $13$ and $23\,\mathrm{km\,s^{-1}}$ respectively." (3.2 Velocity Dispersion and Mach Number)
4. **Derive molecular gas mass, surface and volume density, freefall time**: CO(4-3) flux fraction x total gas mass; convert to L'CO, scale to CO(1-0) with r43, alpha_CO; sphere density gives t_ff  
  > "$\Sigma_{\mathrm{gas}} = M^{\mathrm{tot}}_{\mathrm{gas}} \times (S_{\mathrm{CO}}dv/S^{\mathrm{tot}}_{\mathrm{CO}}dv)/A$" (3.3 Molecular Gas Mass)
   - parameter: r43 = 0.91 (also 0.46 tested)  
  > "we also experiment with $r_{43}=0.46$, which is the average value for SMGs" (3.3 Molecular Gas Mass)
   - assumption: alpha_CO = 0.8±0.1 Msun/(K km/s pc^2)  
  > "$\alpha_{\mathrm{CO}} = 0.8\pm0.1\,\mbox{$\mathrm{M}_{\ensuremath{\odot}}$}\,\mathrm{K^{-1}}\,\mathrm{km^{-1}\,s}\,\mathrm{pc}^{-2}$" (3.3 Molecular Gas Mass)
   - fitting: _not stated_
   - validation: Compared with dust-based gas mass assuming gas-to-dust 100  
  > "by assuming a gas-to-dust ratio of 100." (3.3 Molecular Gas Mass)
5. **Predict SFR surface density from KS, KDM, SFK relations and compare**: Evaluate the three relations with measured parameters via Monte Carlo and compare PDFs with measured Sigma_SFR  
  > "The median of the PDF of $\Sigma_{\mathrm{SFR}}$ from the multi-freefall model is" (4.3 Salim-Federrath-Kewley (SFK) Relation)
   - parameter: KDM eps_ff=0.015; SFK eps_ff=0.0045, b=0.4, beta_mag to infinity  
  > "where $\epsilon_{\mathrm{ff}}=0.0045$, $b$ is the turbulent driving parameter (set to 0.4" (4.3 Salim-Federrath-Kewley (SFK) Relation)
   - assumption: Zero magnetic field in SFK  
  > "This means we assume that the magnetic field is zero." (4.3 Salim-Federrath-Kewley (SFK) Relation)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **3DBarolo** : tilted-ring fit of CO(4-3) cube to check velocity dispersion  
  > "we use the code $^{\mathrm{3D}}$BAROLO (cite: 2015MNRAS.451.3021D) which fits tilted-ring models" (3.2 Velocity Dispersion and Mach Number)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Sigma_SFR nucleus | 270 | 54 | Msun/yr/kpc^2 | 2 | $\Sigma^{\mathrm{nucleus}}_{\mathrm{SFR}} = 270\pm54$ |
| Sigma_SFR SF clump | 170 | 38 | Msun/yr/kpc^2 | 2 | $\Sigma^{\mathrm{sfclump}}_{\mathrm{SFR}} = 170\pm38 |
| Turbulent velocity dispersion nucleus / clump | 12 / 17 | 1 / 2 | km/s | 3 | $\sigma_{v,\mathrm{turb}} = 12\pm1\,\mathrm{km\,s^{-1}}$ and $17\pm2\,\mathrm{km\,s^{-1}}$ |
| Mach number nucleus / clump | 35 / 50 | 16 / 20 | dimensionless | 3 | The Mach numbers we obtain for the nucleus and the SF clump are $35\pm16$ and $50\pm20$ |
| Total gas mass | 7.4e10 | 1.1e10 | Msun | 4 | $M^{\mathrm{tot}}_{\mathrm{gas}} = (7.4\pm1.1)\times 10^{10} |
| Gas mass nucleus / clump | 9.9e9 / 1.9e9 | 2.7e9 / 0.5e9 | Msun | 4 | $M_{\mathrm{gas}} = (9.9\pm2.7)\times 10^{9} |
| Freefall time nucleus / clump | 1.7 / 1.5 | 0.5 / 0.3 | Myr | 4 | $t_{\mathrm{ff}} = 1.7\pm0.5\,\mathrm{Myr}$ and $1.5\pm0.3\,\mathrm{Myr}$ |
| Sigma_SFR,KS nucleus / clump | 105 / 62 | 42 / 26 | Msun/yr/kpc^2 | 5 | $\Sigma^{\mathrm{nucleus}}_{\mathrm{SFR,KS}} = 105\pm42$ and $\Sigma^{\mathrm{sfclump}}_{\mathrm{SFR,KS}} = 62\pm26 |
| Sigma_SFR,KDM nucleus / clump | 134 / 106 | 47 / 40 | Msun/yr/kpc^2 | 5 | $\Sigma^{\mathrm{nucleus}}_{\mathrm{SFR,KDM}} = 134\pm47$ and $\Sigma^{\mathrm{sfclump}}_{\mathrm{SFR,KDM}} = 106\pm40 |
| Sigma_SFR,SFK nucleus / clump | 270 / 280 | 145 / 147 | Msun/yr/kpc^2 | 5 | $\Sigma^{\mathrm{nucleus}}_{\mathrm{SFR,SFK}} = 270\pm145$ and $\Sigma^{\mathrm{sfclump}}_{\mathrm{SFR,SFK}} = 280\pm147 |

## Qualitative findings

- The SF clump has intrinsic rotation distinct from galaxy-wide rotation.  
  > "This implies that the SF clump has some intrinsic rotation of its own which is different than the systematic galaxy-wide rotation" (3.2 Velocity Dispersion and Mach Number)

## Claim tuples

- H: Does the KS relation reproduce measured Sigma_SFR in AzTEC-1? | E: Predict Sigma_SFR from Sigma_gas via KS | R: Underestimates by factor 2-3 | F: KS is insufficient without systematics | **supported**
- H: Does adding freefall time (KDM) help? | E: Predict with KDM single-freefall model | R: Underestimates by ~2 and 1.6 but within systematic uncertainties | F: KDM consistent within uncertainties | **partially**
- H: Does turbulence-regulated SFK best predict SFR? | E: Predict with SFK and compare across low- and high-z samples | R: Agrees within uncertainties; overpredicts clump by 60% | F: SFK gives the best predictions; turbulence and gravity sustain high SFRs | **supported**

## Reasoning

- Why this data: Sub-kpc resolution of an unlensed starburst enables kinematic analysis of distinct regions  
  > "In particular, we study the galaxy nucleus and an off-center star-forming (SF) clump in this galaxy because they have sufficient resolution to apply the kinematic analysis." (Conclusions)
- Why this method: _not stated_
- Alternative: r43=0.46 tried instead of 0.91; dust-based gas mass via RJ tail as cross-check  
  > "we also experiment with $r_{43}=0.46$, which is the average value for SMGs" (3.3 Molecular Gas Mass)
- How they decided it was enough: _not stated_
- Limitation (authors): Large systematic uncertainties; magnetic field strength unknown; need larger sample  
  > "Given the large systematic uncertainties that go in calculating the key ingredients, we require a large sample of diverse star-forming regions" (4.4 Comparison of Star Formation Relations Across Multiple Datasets)
- Caveat (inferred, ours): Only two regions in one galaxy; weak statistical power to discriminate relations
- Caveat (inferred, ours): Systematic uncertainty from r43 and alpha_CO is large (factor 2-3)
- Caveat (inferred, ours): Gas mass share assumes CO flux fraction traces mass uniformly
- Caveat (inferred, ours): Channel width ~30 km/s limits dispersion measurements of ~12-17 km/s

## Reproducibility

- Data public (paper): Project codes listed in acknowledgements; public status not explicitly stated  
  > "This paper uses data from ALMA programs ADS/JAO.ALMA #2015.1.01345.S, #2017.1.00300.S and #2017.A.00032.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Reduction and calibration details (in other papers)
- Missing: Gaussian fit and velocity-gradient fit specifics
- Missing: Monte Carlo configuration
- Missing: Total-flux inputs from Tadaki et al. 2018
- Data volume (inferred): ~10-50 GB (three ALMA datasets, Band 7 and Band 3 cubes)
- Score (inferred): 3/5, Analysis formulas are explicit and results numeric, but calibration, fitting and Monte Carlo details defer to other papers.
- Rediscovery candidate: no, Key steps (velocity-gradient fit, Monte Carlo, reductions) are inherited or unspecified.

## Links

- Method: Sharda et al. 2018 (cite: 2018MNRAS.477.4380S) (Source of the full analysis procedure)
- Method: (cite: 2015MNRAS.451.3021D) (3DBarolo tilted-ring code)
- Companion: (cite: 2018Natur.560..613T) (Band 3 and CO(4-3) observations, total fluxes, SED SFR and disc geometry)
- Companion: (cite: 2016ApJ...829L..10I) (Band 7 continuum observations)
- Related: COSMOS
- Related: AzTEC/JCMT survey
- Related: LMT follow-up

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 37,
  "rate": 0.487
 },
 "evidence_ok": true
}
```

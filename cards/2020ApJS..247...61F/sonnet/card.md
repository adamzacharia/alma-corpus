# The ALPINE-ALMA [C II] Survey: Multiwavelength Ancillary Data and Basic Physical Measurements

`2020ApJS..247...61F` | The Astrophysical Journal Supplement Series 2020 | first author: Faisst, A. L. | arXiv: 1912.01621 | DOI: 10.3847/1538-4365/ab7ccd

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type large_program_or_survey

## Science

- Fields: high_z_galaxies
- Question: What are the ancillary multi-wavelength data and basic physical properties (stellar mass, SFR, UV luminosity, UV slope, Halpha, velocity offsets) of the ALPINE galaxies, and is the sample representative of 4<z<6 galaxies?  
  > "We find that the ALPINE sample is representative of the $4 < z < 6$ galaxy population selected by photometric methods and only slightly biased towards bluer colors" (abstract)
- Target **ALPINE sample of 118 main-sequence galaxies in COSMOS and ECDFS**: coordinates _not stated_; z/distance 4.4 < z < 5.9  
  > "In total, $118$ galaxies have been observed in Band 7 (covering [C II] emission at $158\,{\rm \mu m}$ and its nearby continuum)" (1.2 ALPINE in a Nutshell); distance from Ly-alpha / rest-UV absorption spectroscopic redshifts; [C II] systemic redshifts from Bethermin et al.  
  > "In total, $118$ galaxies have been observed in Band 7 (covering [C II] emission at $158\,{\rm \mu m}$ and its nearby continuum)" (1.2 ALPINE in a Nutshell)

## Data provenance

- ALMA projects: 2017.1.00428.L
- bands: Band 7 ([C II] 158 um and nearby continuum)  
  > "118$ galaxies have been observed in Band 7 (covering [C II] emission at $158\,{\rm \mu m}$ and its nearby continuum)" (1.2 ALPINE in a Nutshell)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-1  
  > "($\nu = 330\,{\rm GHz}$ and $B=0.2\,{\rm km}$ for C43-1)" (3.3 Astrometric offsets between ALMA and ancillary data)
- baselines: _not stated_
- angular resolution: <1.0"  
  > "at a spatial resolution of $<1.0\ensuremath{''}$ and with integration times $\sim30\,{\rm minutes}$ on-source" (1.2 ALPINE in a Nutshell)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: ~30 minutes per galaxy; 69 hours total program  
  > "*ALPINE* is a 69 hour large ALMA program started in Cycle 5 in May 2018 and completed during Cycle 6 in February 2019." (1.2 ALPINE in a Nutshell)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: [C II] 158 um (not stated)
- Other facility **Keck/DEIMOS, VLT/VIMOS (VUDS), VLT/FORS2, HST/GRAPES**: Rest-UV spectroscopy for selection and redshifts  
  > "$84$ are obtained by the large DEIMOS spectroscopic survey (cite: CAPAK04; MALLERY12; HASINGER18) at the Keck telescope in Hawaii." (2.1 Spectroscopic selection of ALPINE galaxies)
- Other facility **Keck/MOSFIRE**: K-band spectrum of DC_881725 detecting [O II]  
  > "We are able to detect the optical [O II] doublet ($3727.09\,{\rm \AA}$ and $3729.88\,{\rm \AA}$) at the spatial position of the galaxy at a level of $>5\sigma$." (2.4.3 How well does [C II] trace systemic redshift?)
- Other facility **COSMOS2015 and 3D-HST catalogs; HST, Spitzer, ground-based imaging**: Multi-wavelength photometry for SED fitting  
  > "The basis catalogs to which we match the *ALPINE* galaxies in the COSMOS and ECDFS field are the *COSMOS2015* (cite: LAIGLE16) and the *3D-HST* (cite: BRAMMER12; SKELTON14) catalog, respectively." (3 Photometry from Ground and Space)
- Other facility **Gaia DR2**: Astrometric reference to measure offsets  
  > "we make use of the Gaia DR2 catalog (cite: MIGNARD18a), which provides currently the most accurate absolute astrometry." (3.3 Astrometric offsets between ALMA and ancillary data)
- External data: [C II] redshifts and ALMA data processing/measurements  
  > "The measurement of the [C II] redshifts are detailed in (cite: ALPINE_BETHERMIN19)." (2.4.2 Velocity Offsets with respect to [C II] FIR Redshifts) [from (cite: ALPINE_BETHERMIN19)]
- External data: Ly-alpha redshifts, fluxes and equivalent widths  
  > "These measurements are explained in more detail in (cite: ALPINE_CASSATA19)." (2.4.1 Measurements) [from (cite: ALPINE_CASSATA19)]
- External data: COSMOS2015 and 3D-HST photometry  
  > "The basis catalogs to which we match the *ALPINE* galaxies in the COSMOS and ECDFS field are the *COSMOS2015*" (3 Photometry from Ground and Space) [from (cite: LAIGLE16); (cite: SKELTON14)]
- External data: Shapley et al. z~3 LBG stack as template for absorption redshift fitting  
  > "we use the stacked spectrum of LBGs at $z\sim3$ from (cite: SHAPLEY06) as a template" (2.4.1 Measurements) [from (cite: SHAPLEY06)]
- External data: De Looze [C II]-SFR relations for comparison with Halpha  
  > "we are showing the relation for their entire sample ($\alpha=1.01$, $\gamma=-6.99$, blue hatched)" (4.4 Measurement of Halpha emission) [from (cite: DELOOZE14)]

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

- Halpha luminosity/EW from Spitzer colors uses the same technique as Faisst et al. 2019  
  > "we follow the same technique as outlined in (cite: FAISST19b) (we refer to this paper for more technical details)" (4.4 Measurement of Halpha emission) [from (cite: FAISST19b)]
- Photometry error rescaling by 1.1 and COSMOS2015 total-magnitude corrections  
  > "we follow the prescription of (cite: LAIGLE16) and rescale the official flux density errors by a factor of 1.1." (4.1.1 Fitting Method) [from (cite: LAIGLE16)]
- Systematic photometric error terms added in quadrature  
  > "following (cite: ILBERT09), we correct for underestimated photometric errors due to varying PSF sizes" (4.1.1 Fitting Method) [from (cite: ILBERT09)]
- [C II] data processing and redshifts  
  > "for details on the data analysis see (cite: ALPINE_BETHERMIN19)" (1.2 ALPINE in a Nutshell) [from (cite: ALPINE_BETHERMIN19)]

### Not stated but needed to reproduce (our reading)

- The ALMA data reduction and [C II] line fitting are entirely deferred to Bethermin et al. 2020; no calibration or imaging settings given here
- The final catalogs are hosted at an author web page; the exact catalog contents are needed to reproduce numbers
- Mophongo/SExtractor/LePhare configuration beyond listed parameters (e.g. LePhare redshift handling is fixed to spectroscopic z but not explicit)
- Selection of galaxies in the sSFR stacks and number per bin not given
- Exact HST pointings and drizzle parameters beyond pixel scale

## Analysis recipe

1. **Recalibrate rest-UV spectra to photometry**: Convolve spectra with optical filter transmissions, compare to total, Galactic-extinction-corrected photometry, derive one average correction factor per spectrum  
  > "We then compare the photometry obtained from the spectra to the total and Galactic extinction corrected photometry discussed in Section [3](#sec:photometry), which allows us to obtain an average correction factor for each spectrum." (2.2 Uniform calibration of spectra)
   - parameter: 4-9 filters at z<5, 2-4 at z>5; filters extending >50% beyond spectrum dropped  
  > "On average, we use $4-9$ filters for galaxies at $z < 5$ and $2-4$ at $z>5$." (2.2 Uniform calibration of spectra)
   - fitting: _not stated_
   - validation: Final calibration precision 5-10% in flux  
  > "The final precision of our calibration is around $5-10\%$ in flux, which corresponds to the $1\sigma$ uncertainty in the photometry." (2.2 Uniform calibration of spectra)
2. **Measure absorption-line redshifts and Ly-alpha properties**: Cross-correlate Shapley06 template to absorption lines in five windows by chi2 minimization within +-600 km/s of a SpecPro prior redshift; combine PDFs; errors from 200 perturbations  
  > "The errors on these redshifts are derived by repeating this measurement $200$ times, thereby perturbing the fluxes according to a Gaussian error distribution" (2.4.1 Measurements)
   - software: SpecPro
   - parameter: Continuum: 4th-order polynomial fit to spectrum smoothed with 5 A box kernel  
  > "The model is derived by fitting a 4$^{\rm th}$-order polynomial to the spectrum, which is smoothed by a $5\,{\textrm \AA}$ box kernel." (2.4.1 Measurements)
   - fitting: chi2 minimization to template; chi2(z) converted to p(z) and combined  
  > "For each galaxy, the so obtained $\chi^2(z)$ distribution is then converted into a probability density function $p(z)$ for each of the windows." (2.4.1 Measurements)
   - validation: Duplicate Keck/DEIMOS and VUDS spectra compared; redshifts agree within 280 km/s for most  
  > "The redshifts are consistent within $280\,{\rm km\,s^{-1}}$ and we do not find any systematic offsets between the two observations" (2.1 Spectroscopic selection of ALPINE galaxies)
3. **Compute velocity offsets relative to [C II] and stack spectra by sSFR**: Velocity differences from redshifts; median stacks in the [C II] rest frame for low (<4 Gyr^-1) and high (>5 Gyr^-1) sSFR  
  > "namely low ($<4\,{\rm Gyr^{-1}}$) and high ($>5\,{\rm Gyr^{-1}}$) sSFR, in their corresponding rest-frames defined by the systemic redshift" (2.4.2 Velocity Offsets with respect to [C II] FIR Redshifts)
   - parameter: Requires z_IS+wind from at least three absorption lines and no -99 flag  
  > "we require that $z_{\rm IS + wind}$ is measured from at least three absorption lines" (2.4.2 Velocity Offsets with respect to [C II] FIR Redshifts)
   - fitting: _not stated_
   - validation: [O II] from MOSFIRE for one galaxy agrees with [C II] redshift  
  > "The position of the line agrees perfectly with the [C II] redshift derived from ALMA" (2.4.3 How well does [C II] trace systemic redshift?)
4. **Assemble total photometry**: Match ALPINE galaxies to 3D-HST/COSMOS2015; convert COSMOS2015 3" aperture magnitudes to total and correct for Galactic extinction; SExtractor on HST mosaics for extra bands  
  > "we use the $3\ensuremath{''}$ diameter aperture magnitudes ($\mathcal{M}^3$), which we correct for photometric ($o_i$, see their equation 4) and systematic offsets" (3.2 Photometry on the COSMOS field)
   - software: SExtractor, AWS-drizzler, grizli, mastquery
   - parameter: HST mosaics at 0.06" pixel scale registered to Gaia; ECDFS E(B-V)=0.0069 mag  
  > "which we assume to be constant for all galaxies in ECDSF at $E(B-V)= 0.0069\,{\rm mag}$" (3.1 Photometry on the ECDFS field)
   - fitting: _not stated_
   - validation: HST vs ground-based photometry agree on average to 0.2 mag  
  > "We find an overall agreement on average of $0.2$ magnitudes (dark gray region)" (3.2 Photometry on the COSMOS field)
5. **Measure astrometric offsets vs Gaia**: Compare Gaia stars (proper-motion corrected, <5 mas/yr) to catalog positions; per-galaxy offsets from HST/ACS F814W vs catalog  
  > "In total, $47$ and $2724$ Gaia stars are used in ECDFS and COSMOS, respectively." (3.3 Astrometric offsets between ALMA and ancillary data)
   - fitting: _not stated_
   - validation: Offsets consistent with earlier studies  
  > "These offsets are consistent with what was found in earlier studies (cite: DUNLOP17; FRANCO18; WHITAKER19)." (3.3 Astrometric offsets between ALMA and ancillary data)
6. **SED fitting for stellar mass, SFR, age, E(B-V), UV magnitude**: LePhare in flux density space with BC03 templates, multiple SFHs, Calzetti dust, 2 metallicities, Chabrier IMF; marginalized PDFs  
  > "we choose the `LePhare` SED fitting code (cite: ARNOUTS99; ILBERT06) to derive stellar masses, SFRs, light-weighted stellar population ages, absolute magnitudes, optical dust reddening, and UV continuum slopes" (4.1.1 Fitting Method)
   - software: LePhare
   - parameter: E_s(B-V) 0 to 0.5 in steps of 0.05; Z = Zsun and 0.2 Zsun; ages from 50 Myr to age of universe  
  > "We add dust attenuation corresponding to a stellar $E_{s}{\rm (B-V)}$ from $0$ to $0.5$ spaced in steps of $0.05$ assuming a (cite: CALZETTI00) dust attenuation law." (4.1.1 Fitting Method)
   - assumption: Chabrier IMF; Calzetti attenuation  
  > "We also adopt a (cite: CHABRIER03) IMF in the following." (4.1.1 Fitting Method)
   - fitting: Chi2 template fitting; errors scaled by 1.1 plus systematic terms; uncertainties from marginalized PDF 1 sigma  
  > "stellar masses, SFR, and sSFR values are computed from the marginalized probability distribution functions over all the models and uncertainties are given in $\pm1\sigma$ of this distribution." (4.1.1 Fitting Method)
   - validation: Compared with HyperZ (masses 0.3-0.4 dex smaller, SFR ~0.3 dex larger) and SMC dust; consistent within factor of two with COSMOS2015  
  > "We find that the stellar masses derived by `HyperZ` are systematically smaller by $0.3-0.4\,{\rm dex}$." (4.1.2 Systematic Uncertainties in Physical Properties from Modeling Assumptions)
7. **Derive UV continuum slope beta**: Robust linear fit to best-fit LePhare SED between 1300 and 2300 A; 1000 Monte Carlo perturbations; Calzetti and SMC PDFs combined with equal weight  
  > "For each galaxy we repeat this procedure $1000$ times to produce a probability density function." (4.3.1 Method)
   - software: LePhare
   - assumption: Calzetti and SMC attenuation equally weighted  
  > "combine for each galaxy the two probability density functions $P_{\rm Calzetti}(\beta)$ and $P_{\rm SMC}(\beta)$ derived from our Monte Carlo approach" (4.3.2 Systematic Uncertainties and Dependencies on Dust Attenuation)
   - fitting: robust linear fit  
  > "The $\beta$ slopes are derived by a robust linear fit (to avoid the fit being affected by any absorption or emission lines) to the logarithmic slope of the best-fit `LePhare` SED" (4.3.1 Method)
   - validation: Compared different wavelength ranges and Calzetti 1994 windows  
  > "we do not find any differences in our measurements compared to the definition by (cite: CALZETTI94)" (4.3.2 Systematic Uncertainties and Dependencies on Dust Attenuation)
8. **Derive Halpha luminosity/EW and SFR from Spitzer colors**: [3.6]-[4.5] color constrains Halpha for 4<z<5 using BC03 basis models A-F; f=0.44; [N II]/Halpha=0.15; SFR via Kennicutt98  
  > "we assume an [N II] to H$\alpha$ ratio of $0.15$, as expected for galaxies at $\log({\rm M}/{\rm {M}_{\odot}})= 10$ (cite: FAISST18)" (4.4 Measurement of Halpha emission)
   - parameter: SFR = 4.5e-42 L(Halpha) [erg/s]  
  > "${\rm SFR\,(M_{\odot}\,yr^{-1})} = 4.5 \times 10^{-42}\, L_{\rm{H\alpha}}\,{\rm (erg\,s^{-1})},$" (4.4 Measurement of Halpha emission)
   - assumption: f-factor 0.44 (likely upper limit on LHalpha); Calzetti and SMC reddening  
  > "For now, the assumed $f=0.44$ provides likely an *upper* limit on the H$\alpha$ luminosities." (4.4 Measurement of Halpha emission)
   - fitting: _not stated_
   - validation: Halpha SFRs compared to SED SFRs; Halpha vs [C II] compared with De Looze relations  
  > "The H$\alpha$-derived SFRs trace well the SED-derived SFRs above $\sim 13\,{M}_{\odot}\,{\rm yr^{-1}}$." (4.4 Measurement of Halpha emission)

## Software

- **LePhare** : SED fitting for masses, SFRs, UV mags, beta  
  > "we choose the `LePhare` SED fitting code" (4.1.1 Fitting Method)
- **HyperZ** modified version with nebular emission: Systematic comparison of SED fit parameters  
  > "we compare the measurements from `LePhare` to a modified version of the `HyperZ` code" (4.1.2 Systematic Uncertainties in Physical Properties from Modeling Assumptions)
- **SpecPro** : Interactive redshift fitting and visual flagging of spectra  
  > "using the interacting redshift-fitting tool `SpecPro`" (2.4.1 Measurements)
- **SExtractor** : HST photometry in 0.7" and 3" apertures and auto magnitudes  
  > "We subsequently measure this additional photometry for all *ALPINE* galaxies in ECDFS using `SExtractor`" (3.1 Photometry on the ECDFS field)
- **AWS-drizzler / grizli** : HST mosaics  
  > "we first create a mosaic of all the HST pointings that overlap with the *ALPINE* galaxies using the `AWS-drizzler` tool" (3.1 Photometry on the ECDFS field)
- **mastquery** : Querying MAST for HST coverage  
  > "using the `mastquery` Python package" (3.1 Photometry on the ECDFS field)
- **MOSFIRE data reduction pipeline** Version 2018: Reducing the MOSFIRE K-band spectrum  
  > "We performed a standard data reduction using the MOSFIRE data reduction pipeline (Version 2018)." (2.4.3 How well does [C II] trace systemic redshift?)
- **MOPHONGO** : Spitzer/ground photometry in 3D-HST (cited)  
  > "the Spitzer and ground-based photometry are measured using the `MOPHONGO`" (3.1 Photometry on the ECDFS field)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Ly-alpha vs IS+wind absorption velocity offset (median) | 386 | +257/-279 | km/s | 3 | We find a median offset on the order of $386^{+257}_{-279}\,{\rm km\,s^{-1}}$ |
| IS+wind absorption offset from [C II] systemic | -227 | +168/-206 | km/s | 3 | For the former we find an offset of $-227^{+168}_{-206}\,{\rm km\,s^{-1}}$ |
| Ly-alpha offset from [C II] systemic | 184 | +201/-215 | km/s | 3 | for the latter we find $184^{+201}_{-215}\,{\rm km\,s^{-1}}$ |
| Absorption-line blueshift in high-sSFR stack | 300-400 | not stated | km/s | 3 | in the high sSFR stack the lines are significantly blue shifted by $300-400\,{\rm km\,s^{-1}}$ |
| Astrometric offset in ECDFS (RA, Dec) | 98, -256 | not stated | mas | 5 | We find significant systematic offsets in the astrometry in ECDFS of $98\,{\rm mas}$ in right-ascension and $-256\,{\rm mas}$ in declination. |
| Astrometric offset in COSMOS (RA) | -64 | not stated | mas | 5 | For COSMOS we only find a significant offset in right-ascension of $-64\,{\rm mas}$. |
| HyperZ vs LePhare stellar mass offset | 0.3-0.4 dex smaller with HyperZ | not stated | dex | 6 | We find that the stellar masses derived by `HyperZ` are systematically smaller by $0.3-0.4\,{\rm dex}$. |
| ALPINE beta bluer than parent sample | 0.2 | not stated | dimensionless | 7 | the $\beta$ slope distribution of *ALPINE* galaxies peaks at $\Delta\beta \sim 0.2$ bluer values than the parent sample |
| Typical beta uncertainty | 0.2-0.3 | not stated | dimensionless | 7 | are on average on the order of $\Delta\beta = 0.2-0.3$ |
| CANDELS_GOODSS_37 stellar mass and SFR | log M = 9.22; log SFR = 0.97 | not stated | log Msun; log Msun/yr | 6 | low-mass ($\log({\rm M}/{\rm {M}_{\odot}})= 9.22$) galaxy that is forming stars at a rate typical for the main-sequence ($\log({\rm SFR}/{[\rm {M}_{\odot}\,yr^{-1}]}) = 0.97$) |

## Qualitative findings

- [C II] and optical [O II] trace the same systemic redshift in DC_881725  
  > "indicating that FIR [C II] and optical [O II] trace the same systemic redshift" (2.4.3 How well does [C II] trace systemic redshift?)
- At low [C II] luminosities Halpha luminosities fall below the De Looze full-sample relation and are closer to the metal-poor dwarf relation  
  > "For lower [C II] luminosities, the H$\alpha$ measurements fall below this relation and are instead more consistent, although with a large scatter, with the relation of metal-poor local dwarf galaxies." (4.4 Measurement of Halpha emission)

## Claim tuples

- H: Is the ALPINE sample representative of the 4<z<6 galaxy population? | E: Compare SED-derived mass-SFR and UV properties to COSMOS2015 parent sample | R: Sample follows the main sequence; UV-brighter and beta ~0.2 bluer than parent | F: Broadly representative, slightly biased to bright, blue galaxies | **supported**
- H: Do UV absorption lines and Ly-alpha show velocity offsets from the [C II] systemic redshift as at lower z? | E: Measure z_Lya and z_IS+wind versus z_[CII] | R: Ly-alpha +184 km/s; absorption -227 km/s | F: Redshifted Ly-alpha and blueshifted absorption similar to lower redshift | **supported**
- H: Do high-sSFR galaxies have stronger outflows? | E: Stack rest-UV spectra in [C II] frame for low and high sSFR | R: Absorption lines blueshifted by 300-400 km/s only in high sSFR stack | F: Indicative of stronger winds and outflows | **partially**
- H: Does [C II] trace the systemic redshift? | E: MOSFIRE [O II] spectrum of one galaxy compared to [C II] redshift | R: [O II] detected >5 sigma at the [C II] redshift | F: [C II] traces systemic redshift (single galaxy) | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: LePhare chosen for consistency and comparability with other COSMOS studies  
  > "For consistency and comparability with other studies on the COSMOS field, we choose the `LePhare` SED fitting code" (4.1.1 Fitting Method)
- Alternative: HyperZ with nebular emission as an alternative; LePhare adopted as default  
  > "For consistency and comparability with other studies on the COSMOS field, we choose the `LePhare` fitting results as the default." (4.1.2 Systematic Uncertainties in Physical Properties from Modeling Assumptions)
- How they decided it was enough: _not stated_
- Limitation (authors): Spitzer blending can overestimate stellar masses; about one-third have contaminated Spitzer photometry  
  > "In total, one-third of the galaxies have contaminated Spitzer photometry to some degree." (4.1.1 Fitting Method)
- Limitation (authors): f-factor is the largest uncertainty in the Halpha measurement  
  > "The $f$-factor is the largest uncertainty in this measurement method" (4.4 Measurement of Halpha emission)
- Caveat (inferred, ours): Stellar masses depend on SED code choice (0.3-0.4 dex) and blended Spitzer photometry
- Caveat (inferred, ours): Sample is spectroscopically selected, biasing toward UV-bright, Lya-emitting galaxies
- Caveat (inferred, ours): ALMA data analysis is not in this paper, so ALMA-derived quantities cannot be reproduced from it
- Caveat (inferred, ours): Halpha from broadband colors depends on assumed f-factor and [N II] ratio

## Reproducibility

- Data public (paper): Ancillary catalogs, images and spectra will be made public  
  > "All ancillary data products (including catalogs, images, and spectra) will be made public accessible." (5 Summary and Conclusions)
- Products in archive: _not stated_
- Missing: ALMA calibration and imaging (in Bethermin et al. 2020)
- Missing: Ly-alpha measurement details (in Cassata et al. 2020)
- Missing: Raw spectra from Keck, VUDS and VLT surveys in a common format
- Data volume (inferred): Small for ancillary catalog work (catalogs, photometry, spectra); ALMA visibilities for 118 targets would be hundreds of GB
- Score (inferred): 3/5, Photometry and SED-fitting recipe is well described with public catalogs, but ALMA processing and several measurements are deferred to companion papers.
- Rediscovery candidate: no, Main results rely on proprietary or external spectra and catalogs, and ALMA analysis is deferred to other papers.

## Links

- Method: (cite: ALPINE_BETHERMIN19) (ALMA data processing, [C II] redshifts and measurements)
- Method: (cite: FAISST19b) (Halpha from Spitzer colors method)
- Method: (cite: LAIGLE16) (COSMOS2015 photometry corrections)
- Companion: (cite: ALPINE_LEFEVRE19) (ALPINE survey overview)
- Companion: (cite: ALPINE_CASSATA19) (Ly-alpha properties and escape fraction)
- Companion: (cite: ALPINE_GINOLFI19) ([C II] outflows from stacking)
- Related: ALPINE
- Related: COSMOS
- Related: ECDFS
- Related: VUDS
- Related: CANDELS
- Related: 3D-HST
- Related: SPLASH

## Checks

```json
{
 "quotes": 80,
 "quotes_ok": 80,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 102,
  "stated": 63,
  "rate": 0.618
 },
 "evidence_ok": true
}
```

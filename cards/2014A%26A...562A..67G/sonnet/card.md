# ALMA reveals a warm and compact starburst around a heavily obscured supermassive black hole at z = 4.75

`2014A&A...562A..67G` | Astronomy and Astrophysics 2014 | first author: Gilli, R. | arXiv: 1312.1248 | DOI: 10.1051/0004-6361/201322892

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: How compact, warm and dusty is the starburst around the Compton-thick QSO XID403 at z=4.75, and can it explain the X-ray obscuration and outflows?  
  > "We proposed continuum observation of XID403 during the first ALMA Early Science call for proposal, aiming at significantly improving over the existing LABOCA and Aztec detections." (2 ALMA observations)
- Target **LESS J033229.4-275619 (XID403)**: coordinates _not stated_; z/distance z=4.75  
  > "One notable example is represented by the V-band dropout galaxy LESS J033229.4–275619 at $z=4.75$ (cite: vanzella06)." (Introduction); distance from Vanzella et al. 2006 (cite: vanzella06)  
  > "One notable example is represented by the V-band dropout galaxy LESS J033229.4–275619 at $z=4.75$ (cite: vanzella06)." (Introduction)

## Data provenance

- ALMA projects: 2011.0.00716.S
- bands: Band 6 (1.305 mm, mean 230 GHz)  
  > "After averaging over the 7.5 GHz band the mean effective frequency for the continuum observations is 230 GHz." (2 ALMA observations)
- frequencies and spectral setup: 4x1.875 GHz spectral windows covering 222-238 GHz  
  > "with $4\times1.875$ GHz spectral windows covering the frequency range 222-238 GHz" (2 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: 22x12 m antennas  
  > "The target was observed on the 21st October 2012 with a $22\times12$ m antenna array" (2 ALMA observations)
- configurations: _not stated_
- baselines: maximum baseline ~400 m  
  > "maximum baseline $\sim 400$m" (2 ALMA observations)
- angular resolution: 0.84x0.71 arcsec  
  > "The synthesized beam FWHM of $0.84\times 0.71$ arcsec" (2 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: rms 0.07 mJy at 1.305 mm  
  > "The rms achieved in our image at 1.305mm is 0.07 mJy" (2 ALMA observations)
- time on source: ~3 min (about 23 min allocated incl. calibration)  
  > "The time on source was $\sim 3$ min" (2 ALMA observations)
- observing dates: 21 October 2012  
  > "The target was observed on the 21st October 2012" (2 ALMA observations)
- pi or archival as stated: Own proposal, PI R. Gilli  
  > "The project (2011.0.00716.S; PI R. Gilli) was classified as ‘filler observation’" (2 ALMA observations)
- Other facility **Herschel PACS/SPIRE**: FIR photometry and upper limits  
  > "| 250 | 43 | $4.1\pm1.9$ | $18\times17$ | Herschel/SPIRE | 2 |" (Table 1)
- Other facility **CANDELS/HST/VLT/Spitzer**: optical to mid-IR photometry for SED decomposition  
  > "We retrieved all the photometry available for XID403 from the CANDELS catalog" (5 SED decomposition)
- Other facility **Chandra 4Ms CDFS**: X-ray spectrum reanalysed for Fe line  
  > "Here we have re-analyzed the 4Ms Chandra X-ray spectrum of XID403" (6 X-ray emission)
- Other facility **VLT FORS2**: optical spectrum, 6.3 h stacked  
  > "providing a final spectrum of 6.3 hours integration time" (7.4 Possible evidence for outflowing gas)
- External data: ALMA Band 7 872 um flux 6.1±0.5 mJy  
  > "| 872 | 152 | $6.1\pm0.5$ | $2.1\times1.1$ | ALMA band7 | 4 |" (Table 1) [from Hodge et al. 2013 (cite: hodge13)]
- External data: ALMA 1181 um flux 3.5±0.1 mJy  
  > "| 1181 | 205 | $3.5\pm0.1$ | $1.7\times1.5$ | ALMA band6 | 5 |" (Table 1) [from Nagao et al. 2012 (cite: nagao12)]
- External data: Gas masses M_H2 and M_HI  
  > "| $M_{H_2}$ | $1.6\pm0.3$ | $10^{10} M_{\odot}$ | Coppin et al. (2010) |" (Table 2) [from Coppin et al. 2010 (cite: coppin10); De Breuck et al. 2011 (cite: debreuck11)]
- External data: X-ray N_H = 1.4e24 cm^-2  
  > "| $N_H^{X-ray}$ | $1.4^{+0.9}_{-0.5}$ | $10^{24}$cm$^{-2}$ | Gilli et al. (2011) |" (Table 2) [from Gilli et al. 2011 (cite: gilli11)]

## Processing

### Calibration

- pipeline or manual: CASA standard reduction  
  > "The data reduction was performed with CASA (version 3.4, (cite: mcmullin07; petry12)) in a standard way." (2 ALMA observations)
- casa version: CASA 3.4  
  > "The data reduction was performed with CASA (version 3.4, (cite: mcmullin07; petry12)) in a standard way." (2 ALMA observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune; rescaled to Butler-JPL-Horizons 2012  
  > "Flux densities were bootstrapped to the Neptune model and subsequently rescaled according to the more recent ‘Butler-JPL-Horizon 2012’" (2 ALMA observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: MFS mode imaging of 4 spws averaged  
  > "The 4 spectral windows were calibrated separately and then averaged during the imaging using the MFS mode (cite: rau11)." (2 ALMA observations)
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
- final beam: 0.84x0.71 arcsec  
  > "The synthesized beam FWHM of $0.84\times 0.71$ arcsec" (2 ALMA observations)
- final rms: 0.07 mJy  
  > "The rms achieved in our image at 1.305mm is 0.07 mJy" (2 ALMA observations)

### Inherited from earlier work

- Modified blackbody form  
  > "We fit these data with a general modified blackbody model of the form (cite: rangwala11):" (3 Far-IR SED) [from (cite: rangwala11)]
- X-ray data reduction and spectral analysis  
  > "The details of the data reduction and X-ray spectral analysis of XID403 are presented in (cite: gilli11)." (6 X-ray emission) [from (cite: gilli11)]
- SFR calibration  
  > "By using the (cite: kennicutt98) relation SFR$(M_{\odot}/yr) = 1.74\times 10^{-10} L_{IR}(L_{\odot})$" (4 Star formation rate) [from (cite: kennicutt98)]

### Not stated but needed to reproduce (our reading)

- CLEAN parameters (weighting, robust, cell, size, masking)
- Flagging details and phase-calibrator solutions
- Exact fit setup for uvmodelfit (starting values)
- Parameters of the SED decomposition fit beyond qualitative description
- Photometry in the CANDELS fit and SPIRE 250um flux (Daddi et al. in prep)

## Analysis recipe

1. **Measure continuum flux and source size**: Image flux density at peak; fit single Gaussian to frequency-averaged visibilities with uvmodelfit, cross-checked with Gildas mapping  
  > "By using the "uvmodelfit" task provided with the CASA environment, we fitted the frequency-averaged visibilities with a single Gaussian component with a FWHM of $0.27\pm0.08$ arcsec." (2 ALMA observations)
   - software: CASA, GILDAS
   - fitting: _not stated_
   - validation: Cross-check with Gildas mapping  
  > "This $\sim3.4\sigma$ indication of source extension has been cross checked with the package "mapping" in the Gildas environment, which provided similar results." (2 ALMA observations)
2. **Fit FIR SED for dust temperature**: chi2 fit of optically thick modified blackbody to ALMA+Herschel+ATCA data  
  > "A simple $\chi^2$ fit to the FIR SED of XID403 returns an acceptable statistics with a best fit temperature of $T_{\rm d}=58.5\pm5.3$K" (3 Far-IR SED)
   - assumption: beta=2 and lambda0=200 um fixed  
  > "we fixed the dust emissivity index to $\beta=2$ and the rest-wavelength at which the dust becomes optically thick (i.e. $\tau_{\nu} =1$) to $\lambda_0=c/\nu_0=200\mu$m" (3 Far-IR SED)
   - fitting: chi2 minimisation  
  > "A simple $\chi^2$ fit to the FIR SED of XID403 returns an acceptable statistics with a best fit temperature of $T_{\rm d}=58.5\pm5.3$K" (Far-IR SED: dust mass and temperature)
   - validation: Compared with optically thin fit (T~33 K) and literature SMGs  
  > "we would measure a colder dust temperature $T_d\sim33$ K" (7.2 Dusty Star Formation)
3. **Derive dust mass**: Optically thin relation at 1.3 mm using model flux  
  > "We then used the standard relation valid for the optically thin case" (3 Far-IR SED)
   - assumption: kappa = 4.0 (nu/1.2 THz)^beta cm2/g, beta=2  
  > "We adopt $\kappa_{\nu} = 4.0 \left (\nu/1.2{\rm THz} \right)^{\beta}{\rm cm^2\,g^{-1}}$ with $\beta=2.0$." (3 Far-IR SED)
   - fitting: _not stated_
   - validation: Agreement with full dust models (Bianchi 2013)  
  > "The dust masses determined with Eq.3 using these prescriptions are in excellent agreement with those determined by full dust models (cite: bianchi13)." (3 Far-IR SED)
4. **Derive L_IR, SFR and SFR surface density**: Integrate best-fit greybody; Kennicutt98 SFR; Sigma_SFR=(SFR/2)/(pi r_half^2)  
  > "By integrating the best-fit modified greybody spectrum we obtained a far-IR (42.5-122.5$\mu$m) luminosity" (4 Star formation rate)
   - assumption: Cosmology H0=67, Om=0.32, OL=0.68; 1 arcsec=6.6 kpc  
  > "A concordance $\Lambda$CDM cosmology with $H_0=67$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_m=0.32$, $\Omega_{\Lambda}=0.68$" (1 Introduction)
   - fitting: _not stated_
   - validation: Agreement with Coppin09 and Gilli11  
  > "These values are in excellent agreement with those previously derived by (cite: coppin09) and (cite: gilli11) and have significantly smaller uncertainties." (Star formation rate and compactness)
5. **Broad-band SED decomposition**: Fit stellar, AGN torus and dusty SSP components to optical-FIR photometry  
  > "The optical to far-infrared (millimeter) data of XID403 were modelled using the spectral energy distribution (SED) fitting code originally developed by (cite: fritz06) and recently updated by (cite: feltre13)." (5 SED decomposition)
   - software: Fritz06/Feltre13 SED code
   - assumption: Salpeter IMF, Calzetti attenuation, solar metallicity, z_form=8  
  > "Extinction to the stellar component is modelled using a (cite: calzetti00) attenuation law." (5 SED decomposition)
   - fitting: _not stated_
   - validation: Compared SFR with FIR-derived value  
  > "Once corrected for this contribution, the far-IR luminosity can be used to derive a star-formation rate of $\sim$1040 M$_{\odot}$/yr, in excellent agreement with what has been estimated in Section 4." (SED decomposition)
6. **Reanalyse X-ray spectrum for Fe line**: Fit pexrav reflection plus free-energy Gaussian iron line with Cash statistic  
  > "We now fit that spectrum with a pure reflection continuum (pexrav model in XSPEC) plus an iron line at a centroid energy which is left free to vary." (6 X-ray emission)
   - software: XSPEC
   - fitting: Cash statistic, 1 sigma errors (Delta C=1)  
  > "We used the Cash statistic to estimate the best fit parameters." (6 X-ray emission)
   - validation: Confirmed on Vito et al. spectrum; background checked  
  > "The same feature is confirmed when we consider the Chandra spectrum obtained by (cite: vito13)" (6 X-ray emission)

## Software

- **CASA** 3.4: calibration, imaging, uvmodelfit  
  > "The data reduction was performed with CASA (version 3.4, (cite: mcmullin07; petry12)) in a standard way." (2 ALMA observations)
- **GILDAS (mapping)** : cross-check of source size  
  > "cross checked with the package "mapping" in the Gildas environment" (2 ALMA observations)
- **XSPEC** : X-ray spectral fit  
  > "pexrav model in XSPEC" (6 X-ray emission)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dust temperature | 58.5 | 5.3 | K | 2 | / $T_{dust}$ / $58.5\pm5.3$ / K / this work / |
| Dust mass | 4.9e8 | 0.7e8 | Msun | 3 | / $M_{dust}$ / $4.9\pm0.7$ / $10^{8} M_{\odot}$ / this work / |
| SFR | 1020 | 150 | Msun/yr | 4 | / SFR / $1020\pm150$ / $M_{\odot}$yr$^{-1}$ / this work / |
| L_IR (8-1000um) | 5.9e12 | 0.9e12 | Lsun | 4 | / $L_{IR}$ / $5.9\pm 0.9$ / $10^{12} L_{\odot}$ / this work / |
| Intrinsic Gaussian FWHM | 0.27 | 0.08 | arcsec | 1 | single Gaussian component with a FWHM of $0.27\pm0.08$ arcsec |
| ALMA 1.305 mm flux density | 2.47 | 0.07 | mJy | 1 | / 1305 / 227 / $2.47\pm0.07$ / $0.84\times0.71$ / ALMA band6 / 6 / |
| Sigma_SFR lower limit | >26 | not stated | Msun/yr/kpc2 | 4 | / $\Sigma_{SFR}$ / $>26$ / $M_{\odot}$yr$^{-1}$kpc$^{-2}$ / this work / |
| Stellar mass | 1.1e11 | within 50% | Msun | 5 | stellar mass $M_*\sim1.1\times10^{11}$ M$_{\odot}$ |
| Rest-frame Fe line energy | 6.88 | 0.16 | keV | 6 | ($6.88\pm0.16$ keV; see Fig.[4](#xray)) |

## Qualitative findings

- Source is unresolved at ~0.75 arcsec, with a ~3 sigma hint of sub-kpc size  
  > "The source is not resolved in our data at a resolution of $\sim$0.75 arcsec" (abstract)

## Claim tuples

- H: Is the dust in XID403 warm and the starburst compact? | E: Modified blackbody fit to ALMA+Herschel SED and size from uv-plane | R: Td=58.5±5.3 K, SFR=1020±150, r_half<2.5 kpc (0.9±0.3 kpc) | F: Warm, compact starburst similar to other SMGs | **supported**
- H: Can galaxy-scale gas explain the X-ray column density? | E: Co-spatial gas mass within r_half | R: N_H~0.3-1.1e24 cm^-2 vs 1.4e24 from X-rays | F: A pc-scale torus may not be required | **partially**
- H: Is there an outflow? | E: Lya shift, N V, tentative Fe 6.9 keV line, blow-out criterion | R: 350 km/s shift; C>5; 2 sigma Fe line | F: Outflow likely but speculative | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Optically thin greybody rejected as it would underestimate Td (~33 K)  
  > "the optically-thin grey-body approximation $S_{\nu_{obs}} \propto B_{\nu}\tau_{\nu}$, which is often used in the literature to fit FIR SEDs, cannot be utilized in this case" (3 Far-IR SED)
- How they decided it was enough: _not stated_
- Limitation (authors): Size measurement needs confirmation at higher resolution; sparse uv sampling  
  > "this measurement needs to be confirmed by data at even higher resolution" (2 ALMA observations)
- Caveat (inferred, ours): Size is only ~3 sigma and from a single Gaussian fit
- Caveat (inferred, ours): Few FIR points with fixed beta and lambda0; Td uncertainty is model dependent
- Caveat (inferred, ours): Gas co-spatiality with dust is assumed
- Caveat (inferred, ours): Fe line is only 2 sigma

## Reproducibility

- Data public (paper): Project code given; data use acknowledged  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00716.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: SED fit configuration and priors
- Missing: Daddi et al. in prep SPIRE 250 um flux
- Data volume (inferred): ~1-2 GB
- Score (inferred): 3/5, Simple single-EB continuum and straightforward SED fit, but imaging and SED-code details are missing.
- Rediscovery candidate: yes, Public Cycle 0 data, simple continuum and SED fit with numeric results.

## Links

- Method: Rangwala et al. 2011 (cite: rangwala11) (modified blackbody model)
- Method: Fritz et al. 2006; Feltre et al. 2013 (SED decomposition code)
- Companion: Gilli et al. 2011 (cite: gilli11) (earlier X-ray analysis of XID403)
- Companion: Nagao et al. 2012 (cite: nagao12) (other ALMA data on source)
- Related: ALESS
- Related: CANDELS
- Related: Chandra Deep Field South 4Ms

## Checks

```json
{
 "quotes": 68,
 "quotes_ok": 68,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 54,
  "rate": 0.659
 },
 "evidence_ok": true
}
```

# Identifying the subtle signatures of feedback from distant AGN using ALMA observations and the EAGLE hydrodynamical simulations

`2018MNRAS.475.1288S` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Scholtz, J. | arXiv: 1712.02708 | DOI: 10.1093/mnras/stx3177

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, high_z_galaxies, agn_and_quasars
- Question: What impact do luminous AGN have on star formation at z=1.5-3.2, as seen in sSFR distributions of X-ray AGN compared with EAGLE models with and without AGN feedback?  
  > "answer the question: what impact do luminous AGN have on star formation?" (1 Introduction)
- Target **X-ray AGN in CDF-S and COSMOS (114 with ALMA coverage; main sample of 81)**: coordinates Tables 1 and 2 list RA/Dec per source  
  > "For the CDF-S field we selected X-ray AGN at $z=$ 1.5–3.2 with $L_{\rm X}= 10^{43} - 10^{44} \mathrel{\rm erg \; s^{-1}}$" (2.1 Main sample); z/distance z=1.5-3.2 (main sample)  
  > "For the CDF-S field we selected X-ray AGN at $z=$ 1.5–3.2 with $L_{\rm X}= 10^{43} - 10^{44} \mathrel{\rm erg \; s^{-1}}$" (2.1 Main sample); distance from Hsu14 and Marchesi16 updated redshifts  
  > "For the CDF-S field we selected X-ray AGN at $z=$ 1.5–3.2 with $L_{\rm X}= 10^{43} - 10^{44} \mathrel{\rm erg \; s^{-1}}$" (2.1 Main sample)

## Data provenance

- ALMA projects: 2012.1.00869.S, 2013.1.00884.S
- bands: Band 7 (870 um)  
  > "The 107 X-ray AGN were observed by ALMA in band 7 using a fixed continuum correlated setup with $7.5$ GHz of bandwidth centered at $344$ GHz (870 $\mu$m)" (6.2 ALMA observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12 m and 7 m (compact) arrays  
  > "using thirty-four 12 m antennas and nine 7 m antennas in the compact array" (6.2 ALMA observations)
- configurations: _not stated_
- baselines: 91-393 m  
  > "the ALMA observations were taken with a variety of baselines across both programmes (91–393 m)" (6.2 ALMA observations)
- angular resolution: 0.18-0.85 arcsec native; tapered to 0.8 arcsec  
  > "All final maps and all measured 870 $\mu$m properties have the same spatial resolution of $0^{\prime\prime}.8$." (6.3 ALMA data reduction)
- max recoverable scale: _not stated_
- sensitivity: proposed RMS 0.075-0.24 mJy  
  > "the proposed root mean squared (RMS) sensitivities varied over 0.075–0.24 mJy" (6.2 ALMA observations)
- time on source: _not stated_
- observing dates: Cycle 1: 2013 Nov 2, 16-17; Cycle 2: 2014 Sep 2, 2014 Dec 31, 2015 Jan 1-2  
  > "taken on 2014 September 2, 2014 December 31, and 2015 January 1–2" (6.2 ALMA observations)
- pi or archival as stated: Own Cycle 1 (PI Mullaney) and Cycle 2 (PI Alexander) programmes  
  > "our cycle 1 (project 2012.1.00869.S; PI: J. Mullaney) and cycle 2 (project 2013.1.00884.S; PI: D. Alexander) programmes" (Appendix)
- Other facility **Spitzer and Herschel**: 8-500 um photometry for SED fitting  
  > "deblended *Herschel*-SPIRE (250, 350, 500 $\mu$m) and our ALMA photometry ($870 \mu$m, see appendix for more details)" (2.1.2 Star-formation measurements)
- Other facility **Chandra**: X-ray AGN catalogues  
  > "from the 4 Ms *Chandra* catalogues of (cite: Xue11) and (cite: Hsu14)" (2.1 Main sample)
- Other facility **EAGLE simulation**: Model sSFR distributions  
  > "In our analyses we have used two models from EAGLE: the reference model" (2.3)
- External data: Multiwavelength photometry for CDF-S  
  > "we used the multi-wavelength catalogue of (cite: Guo13)" (2.1.1) [from (cite: Guo13)]
- External data: COSMOS multiwavelength catalogue  
  > "we used the multi-wavelength catalogue of (cite: laigle16)" (2.1.1) [from (cite: laigle16)]
- External data: Deblended PACS photometry  
  > "The deblended photometry consists of the MIPS $24 \mu$m and the PACS bands from (cite: Magnelli13)" (2.1.2) [from (cite: Magnelli13)]
- External data: SPIRE photometry  
  > "SPIRE photometry from (cite: Swinbank14)" (2.1.2) [from (cite: Swinbank14)]
- Simulation/model as data: EAGLE RefL0100N1504 and NoAGNL0050N0752 queried from public database  
  > "EAGLE no AGN | NoAGNL0050N0752 |   $50^{3}$" (Table 2)

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

- task: CASA clean, iterative to 3 sigma with 5 sigma source re-cleaning  
  > "we cleaned the maps to 3 $\sigma$ (i.e., until peaks down to 3 $\sigma$ become identifiable)" (6.3 ALMA data reduction)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: Gaussian taper to 0.8 arcsec beam  
  > "we “tapered” all of the images to give a synthesized beam of $0^{\prime\prime}.8$" (6.3 ALMA data reduction)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.8 arcsec  
  > "All final maps and all measured 870 $\mu$m properties have the same spatial resolution of $0^{\prime\prime}.8$." (6.3 ALMA data reduction)
- final rms: _not stated_

### Inherited from earlier work

- ALMA data reduction and source detection approach  
  > "Our data reduction and source detection approach follows that described in (cite: Simpson15)." (6.3 ALMA data reduction) [from (cite: Simpson15)]
- Full SED fitting procedure  
  > "The full SED fitting procedure is presented in Stanley et al. (submitted)" (2.1.2) [from Stanley et al. (submitted)]
- Hierarchical Bayesian fitting of distributions  
  > "Following (cite: Mullaney15), we use a hierarchical Bayesian method" (2.2) [from (cite: Mullaney15)]

### Not stated but needed to reproduce (our reading)

- Exact CLEAN parameters (weighting, robust, cell size, image size, threshold in Jy)
- MCMC chain length, step sizes and convergence criteria
- Taper parameters (uv-taper value)
- Final SFR values for ALMA sources and Stanley et al. SED fit code
- CIGALE parameter grids for stellar population and dust attenuation
- ALMA calibration pipeline and flux calibrators

## Analysis recipe

1. **Image ALMA data and extract 870um photometry**: CASA cleaning, taper to 0.8 arcsec, SExtractor peak extraction, matching to X-ray positions (0.5/1 arcsec); 3 sigma upper limits otherwise  
  > "we calculated $3\sigma$ upper limits directly from the map" (6.4)
   - software: CASA, Source Extractor
   - fitting: _not stated_
   - validation: Spurious rates from inverted maps  
  > "we created inverted maps by multiplying the final maps by $-1$" (6.4)
2. **Stellar masses**: CIGALE SED fitting of UV-MIR photometry with BC03 stars, Charlot-Fall dust, Fritz06 AGN  
  > "We modelled the broad-band SEDs of the X-ray AGN using the CIGALE package" (2.1.1)
   - software: CIGALE
   - assumption: Chabrier IMF  
  > "assume a (cite: Chabrier03) initial mass function (IMF)" (1 Introduction)
   - fitting: _not stated_
   - validation: _not stated_
3. **Star-formation rates from IR SED decomposition**: Fit AGN + 6 SF templates to Spitzer/Herschel/ALMA photometry; BIC for AGN need; bootstrap L_IR,SF; Kennicutt98 SFR  
  > "We converted $\mathrel{\rm L_{IR,SF}}$ to SFR using Equation 4 from (cite: Kennicutt98) corrected to the (cite: Chabrier03) IMF." (2.1.2)
   - parameter: DeltaBIC>2 for AGN component; 10^5 bootstrap draws  
  > "We repeated this procedure $10^{5}$ times to build a distribution of all possible values" (2.1.2)
   - fitting: Template fitting chi2  
  > "To each value of $\mathrel{\rm L_{IR,SF,Sol}}$ we assigned a probability P($\chi^2$) (in the shape of the $\chi^{2}$ distribution) that it is the true value of $\mathrel{\rm L_{IR,SF}}$." (2.1.2 Star-formation measurements)
   - validation: _not stated_
4. **Fit log-normal sSFR distributions**: Hierarchical Bayesian with Gibbs sampling and Metropolis-Hastings MCMC; upper limits via log-error function likelihood  
  > "using Gibbs sampling and Metropolis-Hastings Markov Chain Monte Carlo (MCMC) algorithms" (2.2)
   - assumption: log-normal distribution  
  > "we fitted the SFR and sSFR distributions of the X-ray AGN assuming a log-normal function" (2.2)
   - fitting: Uniform uninformative priors on mode and width; median and 68% interval  
  > "we assume uniform, uninformative priors on $\mu$ and $w$" (2.2)
   - validation: Linear means compared with Stanley15  
  > "confirms that our new method is consistent with previous work" (2.2)
5. **Compare to EAGLE with mass matching**: Query EAGLE ref and noAGN, apply same cuts, fit same distributions, mass-match galaxies  
  > "we constructed four subsets of galaxies from the EAGLE ref model that are matched in their mass distributions" (3.2)
   - assumption: radiative efficiency 10%, bolometric correction 0.1, SFR +0.2 dex  
  > "scaled up the SFRs calculated in both EAGLE models by $0.2$ dex" (2.3)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.4.0: imaging ALMA data  
  > "The data were imaged using the Common Astronomy Software Application (CASA version 4.4.0)." (6.3)
- **CIGALE** : stellar mass SED fitting  
  > "using the CIGALE package" (2.1.1)
- **Source Extractor** : extract peaks in maps  
  > "using *Source Extractor* (cite: Sextractor)" (6.4)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| sSFR mode, low LX AGN | 0.03 | +0.14/-0.17 | log10 Gyr^-1 | 4 | Low $L_{x}$ AGN / $0.03^{+0.14}_{-0.17}$ |
| sSFR mode, high LX AGN | -0.32 | +0.15/-0.17 | log10 Gyr^-1 | 4 | High $L_{x}$ AGN / $-0.32^{+0.15}_{-0.17}$ |
| sSFR width, high mass AGN | 0.67 | +0.18/-0.12 | dex | 4 | High Mass AGN / $-0.48^{+0.17}_{-0.20}$ / $0.67^{+0.18}_{-0.12}$ |
| EAGLE noAGN high mass galaxy width | 0.28 | +/-0.01 | dex | 5 | High Mass galaxy / $-0.10^{+0.01}_{-0.01}$ / $0.28^{+0.01}_{-0.01}$ |
| mode slope vs mass, EAGLE ref | -0.52 | 0.02 | dimensionless | 5 | $-0.52 \pm 0.02$ and $-0.35 \pm 0.02$ for the EAGLE ref and EAGLE noAGN model |

## Qualitative findings

- No strong dependence of sSFR distribution on LX; AGN lie below the main sequence  
  > "the AGN clearly lie substantially ($\approx$ 0.2–0.8 dex) below it" (4.1)

## Claim tuples

- H: Does sSFR depend on LX as expected if AGN instantly quench? | E: Fit log-normal sSFR distributions in LX bins | R: Mode drops by 1.5 sigma; widths consistent | F: No instantaneous quenching | **supported**
- H: Does EAGLE ref reproduce observed sSFR distributions? | E: Mass-matched comparison | R: Good agreement once matched in mass | F: EAGLE ref consistent | **supported**
- H: Is a broad sSFR distribution a signature of AGN feedback? | E: Compare EAGLE ref vs noAGN and data | R: Ref width about 2x broader; data prefer ref | F: Indirect evidence for feedback | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Whole-galaxy SFRs cannot rule out short-timescale local impact  
  > "these results do not rule out AGN having significant impact on a short timescale on the star formation in localised regions within the galaxy" (4.2)
- Caveat (inferred, ours): Small sample with many upper limits; log-normal assumption
- Caveat (inferred, ours): Stellar mass distributions differ from EAGLE
- Caveat (inferred, ours): Offsets applied to EAGLE SFRs (0.2 dex)

## Reproducibility

- Data public (paper): EAGLE database is public; ALMA codes cited  
  > "we queried the public database" (2.3)
- Products in archive: _not stated_
- Missing: Stanley et al. SED fitting code and details
- Missing: CLEAN parameters
- Missing: MCMC code
- Data volume (inferred): ~50-100 GB raw for two ALMA programmes
- Score (inferred): 3/5, Data identifiable and tables given, but SED fitting and MCMC details are in other works.
- Rediscovery candidate: no, Key steps depend on unreleased SED fitting and EAGLE queries.

## Links

- Method: (cite: Simpson15) (ALMA reduction and detection)
- Method: (cite: Mullaney15) (hierarchical Bayesian distribution fitting)
- Companion: Stanley et al. (submitted) (SED fitting and SFRs for all ALMA targets)
- Related: CANDELS
- Related: EAGLE
- Related: Chandra Deep Field-South
- Related: COSMOS

## Checks

```json
{
 "quotes": 55,
 "quotes_ok": 55,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 44,
  "rate": 0.564
 },
 "evidence_ok": true
}
```

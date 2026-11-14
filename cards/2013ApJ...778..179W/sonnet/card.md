# An ALMA Survey of Submillimeter Galaxies in the Extended Chandra Deep Field-South: The AGN Fraction and X-Ray Properties of Submillimeter Galaxies

`2013ApJ...778..179W` | The Astrophysical Journal 2013 | first author: Wang, S. X. | arXiv: 1310.6364 | DOI: 10.1088/0004-637X/778/2/179

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: What is the AGN fraction and what are the X-ray properties of submillimeter galaxies, using ALMA-identified SMG positions matched to Chandra X-ray sources in the E-CDF-S?  
  > "Here we set improved constraints on the AGN fraction and X-ray properties of the SMGs with ALMA and *Chandra* observations in the Extended *Chandra* Deep Field-South (E-CDF-S)." (abstract)
- Target **ALESS SMGs in the E-CDF-S (99 main-catalog SMGs; 10 X-ray detected)**: coordinates E-CDF-S field; individual positions in Table 1 for X-ray detected SMGs  
  > "We found 10 X-ray sources associated with SMGs (median redshift $z=2.3$), of which 8 were identified as AGNs using several techniques that enable cross-checking." (abstract); z/distance median z=2.3 for X-ray detected SMGs  
  > "We found 10 X-ray sources associated with SMGs (median redshift $z=2.3$), of which 8 were identified as AGNs using several techniques that enable cross-checking." (abstract); distance from zLESS spectroscopic redshifts or literature; photo-z from Simpson et al. 2013 for ALESS 45.1 and X-ray undetected SMGs  
  > "We found 10 X-ray sources associated with SMGs (median redshift $z=2.3$), of which 8 were identified as AGNs using several techniques that enable cross-checking." (abstract)

## Data provenance

- ALMA projects: 2011.0.00294.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~1.5'' (ALESS); typical <1.5'' or <0.5''  
  > "With the exquisite angular resolution and great sensitivity of ALMA ($\sim
1.5\ensuremath{''}$ and 3$\times$ deeper than LESS; (cite: Hodge2013))" (Introduction)
- max recoverable scale: _not stated_
- sensitivity: RMS 0.6 mJy  
  > "which have a typical angular resolution of $<1.5\ensuremath{''}$ or even $<0.5\ensuremath{''}$ and an RMS of $0.6$ mJy" (Conclusions)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **Chandra (4 Ms CDF-S, 250 ks E-CDF-S)**: X-ray catalogs, spectra and counts used for counterpart matching, spectral analysis and stacking  
  > "we use the deep *Chandra* data in the E-CDF-S region ((cite: Lehmer2005); L05), including the most sensitive X-ray survey to date, the 4 Ms CDF-S survey" (Introduction)
- Other facility **VLA 1.4 GHz**: radio fluxes from Biggs et al. 2011 catalog  
  > "The radio counterparts and radio fluxes of the X-ray detected SMGs are from the catalog of (cite: Biggs2011)" (3.3 Multiwavelength Properties)
- Other facility **Spitzer IRAC, Herschel**: photometry for SED fitting (L_IR, stellar mass, 3.6 um flux)  
  > "The SEDs were fitted using *Spitzer*, *Herschel*, ALMA, and VLA photometry" (3.3 Multiwavelength Properties)
- External data: ALESS main-source catalog of 99 SMGs (positions, 870 um fluxes)  
  > "The main-source catalog in (cite: Hodge2013) contains 99 SMGs that are within the primary beam of ALMA" (2.1 The Submm Catalog) [from (cite: Hodge2013); (cite: Karim2013)]
- External data: Photometric redshifts and stellar masses  
  > "Whenever reshifts are needed for the X-ray undetected SMGs in the E-CDF-S, we adopt the photo-z values from (cite: Simpson2013)." (3.1 Redshifts) [from (cite: Simpson2013)]
- External data: L_IR and L_FIR from SED fitting  
  > "derived based on NIR-through-radio SED fitting by (cite: Swinbank2013)" (3.3 Multiwavelength Properties) [from (cite: Swinbank2013)]
- External data: X-ray catalogs and fluxes (4 Ms CDF-S, 250 ks E-CDF-S)  
  > "Positions and ID numbers are the same as in X11 for CDF-S or L05 for sources only in the E-CDF-S." (Table 1) [from (cite: Xue2011); (cite: Lehmer2005)]
- External data: Spectroscopic redshifts (zLESS)  
  > "all X-ray detected SMGs have spectroscopic redshifts either from the redshift follow-up survey zLESS (cite: Danielson2013) or from the literature" (3.1 Redshifts) [from (cite: Danielson2013)]

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

- X-ray spectral extraction with ACIS Extract for CDF-S sources  
  > "The spectra for sources within the 4 Ms CDF-S region were extracted by X11 using `ACIS Extract` (AE; (cite: Broos2010))." (3.2 X-ray Properties) [from (cite: Xue2011)]
- Gamma_eff derivation from hardness ratio and fixed values (1.4, 1.8)  
  > "The effective photon index $\Gamma_{\rm eff}$ is then derived from the hardness ratio following the methods described in L05 and X11." (3.2.1) [from L05 and X11]
- Likelihood-ratio matching details  
  > "Then we iterate to find a likelihood-ratio cut that maximizes the sum of the matching completeness and reliability (see (cite: Luo2010) for details)." (2.3 Source Matching) [from (cite: Luo2010)]
- Stacking procedure  
  > "We follow the stacking procedures detailed in Section 3.1 of (cite: Luo2011)." (6 Stacking) [from (cite: Luo2011)]
- AGN fraction method  
  > "We follow the method discussed in Section 3.1 of (cite: Lehmer2007) and Section 5 of (cite: Silverman2008) to calculate $f_{\rm AGN}$" (5.1 Methodology) [from (cite: Lehmer2007); (cite: Silverman2008)]
- Variability analysis  
  > "Here we follow the method in Section 3 of (cite: Young2012)" (4.4 Method V) [from (cite: Young2012)]

### Not stated but needed to reproduce (our reading)

- Exact ALESS catalog positions and fluxes for all 99 SMGs (in Hodge 2013, not reproduced)
- Simpson 2013 and Swinbank 2013 were in prep.; their photo-z, mass and L_IR tables are required
- X-ray sensitivity maps used for the 1/N method
- Extra WAVDETECT catalogs for additional sources
- ALMA data reduction details (not covered; taken from Hodge 2013)

## Analysis recipe

1. **match X-ray sources to ALMA SMG positions**: Likelihood-ratio matching of 99 SMGs to merged CDF-S and E-CDF-S catalogs, within 5''; cross-checked with closest-counterpart within 1.5''  
  > "We found secure X-ray counterparts for 10 ALESS SMGs with a false-match probability of 3% (i.e., an expected number of false matches of 0.3)." (2.3 Source Matching)
   - fitting: _not stated_
   - validation: False matches estimated by shifting catalogs by 10-60'' in 10'' steps  
  > "The number of false matches for a certain matching radius $r_{\rm s}$ was estimated by manually shifting the X-ray catalogs in RA and Dec by $\pm 10$–$60\ensuremath{''}$ in $10\ensuremath{''}$ increments" (2.3 Source Matching)
2. **derive X-ray spectral properties**: BEHR hardness ratios and Gamma_eff; XSPEC cstat fits of wabs*zwabs*zpow for sources with >100 counts; simulations at fixed Gamma_int=1.8 for low counts  
  > "The basic model we adopted was `wabs*zwabs*zpow` in `XSPEC`" (3.2.2)
   - software: XSPEC, BEHR, CIAO
   - parameter: Energy range 0.5-8 keV; Cash statistic without binning  
  > "we adopted the Cash statistic ((cite: Cash1979); `cstat` in `XSPEC`) for finding the best-fit parameters" (3.2.2)
   - assumption: Galactic N_H = 8.8e19 cm^-2; cosmology H0=70.4, Om=0.27, OL=0.73  
  > "We adopt a Galactic column density of $N_{\rm H}=8.8\times 10^{19}$ cm$^{-2}$ for the line of sight to the E-CDF-S region" (1 Introduction)
   - fitting: Cash statistic minimization; Fe Kalpha test with BIC; MCMC via XSPEC chain for equivalent width  
  > "We evaluated if the model including the Fe K$\alpha$ line is statistically a better model by computing the Bayesian Information Criterion (BIC)" (3.2.2)
   - validation: Low-count L_corr typically agrees within ~30% with spectral fits (per X11)  
  > "values estimated for the lower count sources typically agree within $\sim 30\%$ compared with those from direct spectral fitting" (3.2.2)
3. **classify X-ray SMGs as AGN or star-formation dominated**: Five methods: Gamma_eff<1.0; L_corr>3e42; L_X >5x L_X,SF from radio/IR SFR; log(fX/f3.6um)>-1; X-ray variability  
  > "Combining the results of all the methods described above, 8 out of the 10 X-ray detected SMGs show strong evidence of containing AGNs under at least one classification method" (4.5 Summary)
   - assumption: Salpeter IMF; SFR from Kennicutt 1998 L_IR relation; L_X,SF from Lehmer 2010  
  > "The SFRs were derived following Equation 3 in (cite: Kennicutt1998)" (4.2 Method III)
   - fitting: _not stated_
   - validation: Cross-check between independent methods; 3.6um threshold calibrated on X11 sources (~95% AGN)  
  > "as $\sim
95$% of the X11 sources that satisfy this criterion are AGNs" (4.3 Method IV)
4. **compute cumulative AGN fraction**: 1/N_SMG,i sum accounting for spatially varying X-ray sensitivity; Gehrels errors; N_H drawn from Rafferty 2011 distribution for L_corr case  
  > "The error for $f_{\rm AGN}$ is calculated by adding in quadrature the error for each $1/N_{\rm SMG,i}$ term (estimated following Gehrels 1986)." (5.1 Methodology)
   - software: XSPEC
   - fitting: _not stated_
   - validation: Compared with previous studies; repeated with S870>3.5 mJy flux-limited sample  
  > "We hence removed the SMGs (including SMG-AGNs) with $S_{\rm 870\mu m} < 3.5$ mJy in our sample and calculated the AGN fraction for the flux-limited ($\geqslant 3.5$ mJy) SMG sample in the E-CDF-S." (5.2 The AGN Fractions)
5. **stack X-ray undetected SMGs**: Counts in 1.5'' radius apertures at ALMA positions of 49 SMGs within 7' of aim points; background from 1000 random apertures  
  > "The background counts for each SMG were estimated by extracting counts within 1000 randomly placed $1.5
\ensuremath{''}$-radius apertures within $1 \ensuremath{'}$ of each SMG" (6 Stacking)
   - software: BEHR
   - fitting: _not stated_
   - validation: 1000 fake catalogs of 49 random positions  
  > "We performed a robustness test by generating 1000 fake submm catalogs at random RA and Dec with 49 sources each (avoiding X-ray sources)" (6 Stacking)

## Software

- **XSPEC** : X-ray spectral fitting and simulations  
  > "We used `XSPEC` (cite: Arnaud1996) for spectral fitting and modeling." (3.2.2)
- **CIAO** 4.4.1: extracting and combining E-CDF-S-only spectra (specextract, combine_spectra, chandra_repro)  
  > "`CIAO` (version $4.4.1$; (cite: Fruscione2006)) tools `specextract` and `combine_spectra`" (3.2 X-ray Properties)
- **BEHR** : Bayesian hardness ratios  
  > "The hardness ratios were derived using the Bayesian Estimation of Hardness Ratios (BEHR) package by (cite: Park2006)." (3.2.1)
- **ACIS Extract** : spectra for CDF-S sources (done by X11)  
  > "The spectra for sources within the 4 Ms CDF-S region were extracted by X11 using `ACIS Extract`" (3.2 X-ray Properties)
- **WAVDETECT** : additional lower-significance X-ray source catalogs  
  > "290 additional sources from a `WAVDETECT` catalog with a false-positive probability threshold of $10^{-5}$" (2.2 The X-ray Catalog)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of SMGs with X-ray counterparts | 10 | false-match probability 3% | count | 1 | We found secure X-ray counterparts for 10 ALESS SMGs with a false-match probability of 3% |
| AGN fraction, L_X,corr >= 7.8e42 erg/s | 17 | +16/-6 | percent | 4 | yields an AGN fraction of $17^{+16}_{-6}\%$ for AGNs with rest-frame 0.5–8 keV absorption-corrected luminosity $\geqslant 7.8 \times 10^{42}$ erg s$^{-1}$ |
| AGN fraction for massive SMGs (M*>=1e11) | 33 | +30/-12 | percent | 4 | $f_{\rm AGN}$ for the massive SMGs is $33^{+30}_{-12}\%$ |
| Stacked soft-band S/N, 49 SMGs | 5.4 | not stated | sigma | 5 | the signal to noise ratios S/N[^3] ($(S-B)/\sqrt{B}$) are 5.4$\sigma$ (soft) and 2.1$\sigma$ (hard) |
| Gamma_eff of 4 radio-excess stacked SMGs | 0.8 | +0.6/-0.5 | dimensionless | 5 | $\Gamma_{\rm eff}=0.8^{+0.6}_{-0.5}$ |
| Mean L_0.5-8keV of 4 radio-excess stacked SMGs | 3.6e42 | not stated | erg/s | 5 | we estimate their average rest-frame 0.5–8.0 keV apparent luminosity to be $L_{\rm 0.5-8\ keV}=3.6\times 10^{42}$ erg s$^{-1}$ |

## Qualitative findings

- 6 of 8 SMG-AGNs are moderately/highly absorbed with N_H>1e23 cm^-2  
  > "6 of the 8 SMG-AGNs are moderately/highly absorbed, with $N_{\rm H}> 10^{23}\ {\rm cm^{-2}}$." (abstract)

## Claim tuples

- H: What fraction of ALMA-identified SMGs host X-ray AGNs? | E: Match ALESS positions to Chandra, classify with five methods, compute 1/N cumulative fraction | R: 10 X-ray SMGs, 8 AGNs; f_AGN=17 +16/-6% | F: AGN fraction is consistent with earlier single-dish based estimates but with more reliable counterparts | **supported**
- H: Do X-ray undetected SMGs contain additional AGNs? | E: Stack X-ray counts at ALMA positions of 49 SMGs, including radio-excess subsample | R: Significant soft-band stack; 4 radio-excess SMGs hard (Gamma_eff=0.8) with excess over SF expectation | F: 4 potential SMG-AGNs in stacking sample | **partially**
- H: Are SMG-AGNs more massive than other SMGs? | E: Compare stellar masses and f_AGN for massive subsample | R: mean 1.8e11 vs 8.0e10 Msun, K-S p=0.01 | F: SMG-AGNs are more massive | **supported**

## Reasoning

- Why this data: ALMA gives a fully submm-identified SMG sample, avoiding counterpart ambiguity of single-dish surveys  
  > "ALESS provides the *first* fully submm-identified sample of SMGs based on a large, contiguous, and well-defined survey (LESS)" (Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Small sample of matched sources limits statistics; stacking results tentative  
  > "the sample size of matched objects is small and limits detailed statistical analyses" (Future Work)
- Caveat (inferred, ours): Key inputs (photo-z, SED L_IR, masses) rely on in-prep papers
- Caveat (inferred, ours): AGN classification thresholds calibrated on local galaxies
- Caveat (inferred, ours): Small-number statistics in f_AGN
- Caveat (inferred, ours): ALMA flux/position quality inherited without independent check

## Reproducibility

- Data public (paper): ALMA and Chandra data available from archives  
  > "The data used in this paper are available from the ALMA and *Chandra* data archives." (Acknowledgments)
- Products in archive: _not stated_
- Missing: ALESS catalog tables (Hodge 2013)
- Missing: Simpson 2013 and Swinbank 2013 derived tables
- Missing: X-ray sensitivity maps and WAVDETECT additional catalogs
- Data volume (inferred): Small if using published ALESS catalog; Chandra 4 Ms data tens of GB
- Score (inferred): 3/5, Methods well described but rely on external catalogs and in-prep papers; ALMA data used only as catalog
- Rediscovery candidate: no, Results depend on external catalogs and Chandra reduction by other papers, with no ALMA processing in this paper.

## Links

- Method: (cite: Hodge2013) (ALESS catalog and ALMA reduction)
- Method: (cite: Xue2011) (4 Ms CDF-S catalog and X-ray methods)
- Method: (cite: Luo2010) (likelihood-ratio matching)
- Method: (cite: Luo2011) (stacking procedure)
- Companion: (cite: Karim2013) (ALESS number counts)
- Companion: (cite: Simpson2013) (ALESS photometric redshifts and stellar masses)
- Companion: (cite: Swinbank2013) (ALESS SED fitting)
- Related: ALESS
- Related: LESS
- Related: CDF-S
- Related: E-CDF-S
- Related: zLESS

## Checks

```json
{
 "quotes": 54,
 "quotes_ok": 54,
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
  "facts": 82,
  "stated": 43,
  "rate": 0.524
 },
 "evidence_ok": true
}
```

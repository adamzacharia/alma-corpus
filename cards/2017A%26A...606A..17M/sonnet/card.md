# An ALMA survey of submillimetre galaxies in the COSMOS field: Physical properties derived from energy balance spectral energy distribution modelling

`2017A&A...606A..17M` | Astronomy and Astrophysics 2017 | first author: Miettinen, O. | arXiv: 1707.00637 | DOI: 10.1051/0004-6361/201730762

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: What are the physical properties (stellar, dust and gas masses, SFR, dust temperature, main-sequence offset) of ALMA 1.3 mm-detected, AzTEC 1.1 mm-selected SMGs in COSMOS, and what do they imply for SMG evolution?  
  > "We determine the physical properties of a sample of SMGs in the COSMOS field that were pre-selected at the observed-frame wavelength of $\lambda_{\rm obs}=1.1$ mm" (abstract)
- Target **124 AzTEC/ALMA SMGs in COSMOS (AzTEC/C1a ... C129)**: coordinates COSMOS field, RA ~10 hr, Dec ~+2.2 deg  
  > "centred at $\alpha_{2000.0}\simeq 10$ hr and $\delta_{2000.0}\simeq 2.2\ensuremath{^\circ}$" (2.1.1); z/distance median z = 2.30 (19.4% spectroscopic)  
  > "centred at $\alpha_{2000.0}\simeq 10$ hr and $\delta_{2000.0}\simeq 2.2\ensuremath{^\circ}$" (2.1.1); distance from Brisbin et al. (2017) photometric/spectroscopic redshifts  
  > "centred at $\alpha_{2000.0}\simeq 10$ hr and $\delta_{2000.0}\simeq 2.2\ensuremath{^\circ}$" (2.1.1)

## Data provenance

- ALMA projects: 2013.1.00118.S, 2012.1.00978.S
- bands: 1.3 mm continuum survey (project 2013.1.00118.S); Band 7 for C5, C17, C42  
  > "followed up with dedicated ALMA pointings at $\lambda_{\rm obs}=1.3$ mm" (2.1.1); "were observed with the ALMA Band 7 during the second early science campaign" (2.2.2)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~1.6'' x 0.9''  
  > "$\sim1.6\ensuremath{''} \times 0.9\ensuremath{''}$ angular resolution with a $1\sigma$ root-mean-square (rms) noise of $\sim0.1$ mJy beam$^{-1}$" (2.1.1)
- max recoverable scale: _not stated_
- sensitivity: 1 sigma rms ~0.1 mJy/beam; detection S/N>=5  
  > "we detected 152 ALMA sources at an S/N$_{\rm 1.3\, mm}\geq5$" (2.1.1)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Main survey PI M. Aravena (Cycle 2); Band 7 data PI A. Karim (Cycle 1)  
  > "(Cycle 2 ALMA project 2013.1.00118.S; PI: M. Aravena)" (2.1.1)
- Other facility **COSMOS2015 catalogue (CFHT, Subaru, UltraVISTA, Spitzer)**: UV/optical to mid-IR photometry  
  > "we employed the band-merged COSMOS2015 photometric catalogue" (2.2.1)
- Other facility **Herschel PACS/SPIRE**: 100-500 um far-IR photometry, with ALMA and 24 um positions as priors  
  > "the *Herschel* flux densities were extracted by using the ALMA 1.3 mm and *Spitzer* 24 $\mu$m sources as positional priors" (2.2.2)
- Other facility **ASTE/AzTEC, SCUBA-2, LABOCA, MAMBO-2, SMA**: 1.1 mm parent selection and submm/mm photometry  
  > "we used the deboosted ASTE/AzTEC 1.1 mm flux densities reported by Aretxaga et al. (2011; their Table 1)" (2.2.2)
- Other facility **GMRT and VLA**: 325 MHz, 610 MHz, 1.4 GHz and 3 GHz radio photometry  
  > "we employed the 325 MHz and 610 MHz observations taken by the Giant Meterwave Radio Telescope (GMRT)-COSMOS survey" (2.2.3)
- External data: Redshifts (photometric/spectroscopic) and multiwavelength counterparts and photometry extraction  
  > "98 ($64.5\% \pm 6.5\%$) of our SMGs were found to have a well-defined counterpart in the COSMOS2015 multiwavelength catalogue" (2.1.1) [from Brisbin et al. 2017 (cite: brisbin2017)]
- External data: 3 GHz flux densities and radio sizes  
  > "the corresponding flux densities used in the present study can be found in their Table C.1" (2.2.3) [from Miettinen et al. 2017b (cite: miettinen2017b)]
- External data: ALESS SMG MAGPHYS physical properties for comparison  
  > "we take our main comparison sample of SMGs to be the so-called ALESS SMGs studied by da Cunha et al. (2015)" (4.8) [from da Cunha et al. 2015 (cite: dacunha2015)]

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
- continuum subtraction: CASA continuum images from line-free channels (Band 7 data of C5, C17, C42)  
  > "was used to construct the continuum images from the line-free channels at $\lambda_{\rm obs}=870$ $\mu$m, 857 $\mu$m, and 994 $\mu$m, respectively" (2.2.2)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- 1.3 mm ALMA survey, catalogue, reliability and multiplicity  
  > "Our ALMA follow-up survey, which together with the source catalogue are described in detail by M. Aravena et al. (in prep.)" (2.1.1) [from M. Aravena et al., in prep.]
- Upper limits treated by setting nominal flux to zero and using 3 sigma as error  
  > "Following da Cunha et al. (2015) and Miettinen et al. (2017a), the flux density upper limits in the SED fitting process were taken into account by setting the nominal value to zero" (3.1.1) [from da Cunha et al. (2015); Miettinen et al. (2017a)]
- Gas masses via Scoville et al. (2016) long-wavelength dust method  
  > "we estimate the gas masses of our SMGs using the long-wavelength ($\lambda_{\rm rest}\gtrsim250$ $\mu$m) dust continuum method of Scoville et al. (2016)" (3.2) [from Scoville et al. (2016) (cite: scoville2016)]
- Starburst definition (Delta_MS > 3) and SED approach  
  > "In keeping with the studies by da Cunha et al. (2015) and Miettinen et al. (2017a), we define these sources as starbursts" (4.1.1) [from da Cunha et al. (2015); Miettinen et al. (2017a)]

### Not stated but needed to reproduce (our reading)

- Flux densities and rms/beam of the 1.3 mm ALMA catalogue are not described (in Aravena et al. in prep.); calibration and imaging details for 2013.1.00118.S not given
- CASA version, weighting, cleaning and masking for the Band 7 continuum images of C5, C17, C42 not given
- Exact MAGPHYS high-z library version/filter list and handling of redshift uncertainties
- How Herschel deblending was done in detail (in Brisbin et al. 2017)
- Binning scheme for the binned averages and fits

## Analysis recipe

1. **Define clean SMG sample**: Remove AGN hosts via VLBA detection and X-ray detection, and require optical-mid-IR photometry, leaving 124 SMGs  
  > "we end up with a final sample of 124 SMGs ($81.6\% \pm 7.3\%$ of the initial ALMA sample)" (2.1.3)
   - fitting: _not stated_
   - validation: IR AGN criteria of Donley et al. (2012) give ~6.5% AGN among X-ray non-detected  
  > "We found that the percentage of such AGNs in our sample of X-ray non-detected SMGs is about 6.5%." (2.1.2)
2. **Assemble multiwavelength photometry**: COSMOS2015 UV-mid-IR, Herschel with ALMA priors, submm/mm single-dish and interferometric, GMRT/VLA radio; ALMA Band 7 fluxes for C5, C17, C42 by JMFIT Gaussian fits  
  > "we used the National Radio Astronomy Observatory (NRAO) Astronomical Image Processing System (`AIPS`) software package to make two-dimensional elliptical Gaussian fits (the `AIPS` task `JMFIT`)" (2.2.2)
   - software: CASA, AIPS, BLOBCAT
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit panchromatic SEDs**: MAGPHYS high-z version energy balance fits; parameters are medians of likelihood distribution with 16-84 percentile range  
  > "We adopted the median of the likelihood distribution as an estimate of each `MAGPHYS`-based parameter" (3.1.2)
   - software: MAGPHYS
   - parameter: q_FIR centred at 2.34 with sigma 0.25; thermal fraction f_T = 0.1; synchrotron nu^-0.8  
  > "The thermal radio emission is assumed to amount to 10% ($f_{\rm T}=0.1$) of the total flux density at $\nu_{\rm rest}=1.4$ GHz." (3.1.1)
   - assumption: Chabrier (2003) IMF; no AGN contribution to dust heating  
  > "A Chabrier (2003) Galactic-disk initial mass function (IMF) is assumed in the calculation of $M_{\star}$ and SFR." (1)
   - fitting: Bayesian library fitting in MAGPHYS; upper limits entered as zero flux with 3 sigma error  
  > "setting the nominal value to zero, and using the upper limit value (here $3\sigma$) as the flux density error" (3.1.1)
   - validation: chi2 below threshold ~14 for 33 bands; refits without upper limits; AGN contribution to L_IR checked with SED3FIT (mean 1.4%); spec-z vs photo-z  
  > "the mean (median) AGN contribution to $L_{\rm IR}$ was found to be only about 1.4% (0.2%)" (3.1.2)
4. **Derive SFR**: SFR = 1e-10 L_IR (Kennicutt 1998, Chabrier IMF), L_IR integrated over 8-1000 um  
  > "${\rm SFR}=10^{-10}\times L_{\rm IR}[{\rm L}_{\ensuremath{\odot}}]\, {\rm M}_{\ensuremath{\odot}}~{\rm yr}^{-1}$" (3.1.2)
   - assumption: optically thick starburst, solar metallicity; cirrus heating ignored  
  > "it is based on the assumption of solar metallicity, and an optically thick ($\tau_{\rm dust}\gg1$) starburst region" (3.1.2)
   - fitting: _not stated_
   - validation: Compared to MAGPHYS SFR: ratio median 1.31 (100 Myr), 1.15 (10 Myr)  
  > "with a median of $1.31^{+0.83}_{-0.17}$" (3.1.2)
5. **Estimate molecular gas mass from 1.3 mm flux**: Scoville et al. (2016) R-J dust method, Eq. with Gamma_RJ  
  > "for our ALMA 1.3 mm dust continuum measurements, we can write (cf. Eq. (16) in (cite: scoville2016))" (3.2)
   - parameter: mass-weighted T_dust = 25 K, beta = 1.8  
  > "where the mass-weighted $T_{\rm dust}$ is assumed to have a constant value of 25 K" (3.2)
   - assumption: Galactic alpha_CO = 6.5 (with helium); alpha_850 = 6.7e19 erg/s/Hz/Msun; gas mostly molecular  
  > "a Galactic conversion factor of $\alpha_{\rm CO}=6.5$ M$_{\ensuremath{\odot}}$ (K km s$^{-1}$ pc$^2$)$^{-1}$ assumed by Scoville et al. (2016)" (3.2)
   - fitting: _not stated_
   - validation: Compared to CO-based gas masses of C5 and C17 (ratios 0.5 and 1.8 after alpha_CO scaling)  
  > "we obtain the ratios $M_{\rm gas}/M_{\rm gas}^{\rm CO}=0.5\pm0.1$ and $M_{\rm gas}/M_{\rm gas}^{\rm CO}=1.8\pm0.5$ for AzTEC/C5 and C17" (3.2)
6. **Main-sequence offset and derived ratios**: Delta_MS = SFR/SFR_MS with Speagle et al. (2014) MS; tau_dep = M_gas/SFR; f_gas; gas-to-dust ratio; binned linear least-squares fits vs redshift and others  
  > "we calculated the ratio of the derived SFR to that expected for a MS galaxy of the same redshift and $M_{\star}$, that is $\Delta_{\rm MS}\equiv{\rm SFR}/{\rm SFR}_{\rm MS}$" (4.1.1)
   - parameter: Starburst: Delta_MS > 3; MS: 1/3 < Delta_MS <= 3  
  > "Seventy-one of our SMGs ($57.3\%\pm6.8\%$) have $1/3 < \Delta_{\rm MS} \leq3$" (4.1.1)
   - assumption: Flat LCDM, H0=70, Om=0.30  
  > "The Hubble constant is set at $H_0=70$ km s$^{-1}$ Mpc$^{-1}$" (1)
   - fitting: Linear least squares on binned averages; Kaplan-Meier for censored size data  
  > "The latter values were calculated by using a Kaplan-Meier (K-M) survival analysis to take the upper size limits (left-censored data) into account." (4.5)
   - validation: Pearson/Spearman coefficients and slope significance quoted  
  > "The Spearman rank-order correlation coefficient between the nominal binned data point values is $\rho=-0.71$" (4.1.3)
7. **Compare with ALESS SMGs and compact quiescent galaxies**: Welch t-test and two-sided KS test against flux-matched ALESS subsample (71 sources); KS tests of final stellar mass vs cQGs and cSFGs  
  > "we also performed a two-sided Kolmogorov–Smirnov (K-S) test between the aforementioned physical parameters of our ALMA sources and the flux-limited ALESS sample" (4.8)
   - parameter: final stellar mass M_final = M_star + 0.1 M_gas  
  > "assuming that $10\%$ of the cold molecular gas reservoir is converted into stars ($M_{\star}^{\rm final}=M_{\star}+0.1\times M_{\rm gas}$)" (4.9.1)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **MAGPHYS** high-z version (not stated): panchromatic SED fitting  
  > "The observational data were modelled using the Multiwavelength Analysis of Galaxy Physical Properties code `MAGPHYS`" (3.1.1)
- **SED3FIT** : estimating AGN contribution to L_IR  
  > "the three-component SED fitting code `SED3FIT`" (3.1.2)
- **CASA** : Band 7 continuum images from line-free channels  
  > "was used to construct the continuum images from the line-free channels" (2.2.2)
- **AIPS** : JMFIT Gaussian fits for Band 7 fluxes  
  > "to make two-dimensional elliptical Gaussian fits (the `AIPS` task `JMFIT`)" (2.2.2)
- **BLOBCAT** : GMRT source catalogue  
  > "We used the `BLOBCAT` source extraction software ((cite: hales2012)) to create a preliminary catalogue of GMRT sources" (2.2.3)
- **Astropy** : acknowledged as used in the research  
  > "This research made use of Astropy, a community-developed core Python package for Astronomy" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| median stellar mass log(M*/Msun) | 11.09 | +0.41/-0.53 | dex(Msun) | 3 | $11.09^{+0.41}_{-0.53}$ |
| median SFR | 402 | +661/-233 | Msun/yr | 4 | ${\rm SFR}=402^{+661}_{-233}$ |
| median T_dust | 39.7 | +9.7/-7.4 | K | 3 | $T_{\rm dust}=39.7^{+9.7}_{-7.4}$ K |
| median log M_dust | 9.01 | +0.20/-0.31 | dex(Msun) | 3 | $\log(M_{\rm dust}/{\rm M}_{\ensuremath{\odot}})=9.01^{+0.20}_{-0.31}$ |
| median log M_gas | 11.34 | +0.20/-0.23 | dex(Msun) | 5 | $\log(M_{\rm gas}/{\rm M}_{\ensuremath{\odot}})=11.34^{+0.20}_{-0.23}$ |
| median gas-to-dust ratio | 120 | +73/-30 | dimensionless | 6 | The derived median gas-to-dust ratio of $120^{+73}_{-30}$ |
| median gas fraction | 0.62 | +0.27/-0.23 | dimensionless | 6 | with a median of $0.62^{+0.27}_{-0.23}$ |
| fraction of SMGs on main sequence | 57.3% | 6.8% | percent | 6 | Seventy-one of our SMGs ($57.3\%\pm6.8\%$) have $1/3 < \Delta_{\rm MS} \leq3$ |
| fraction of starbursts (Delta_MS>3) | 41.9% | 5.8% | percent | 6 | Fifty-two out of the 124 SMGs ($41.9\%$ with a Poisson counting error of $5.8\%$) |
| median gas depletion time | ~535 | not stated | Myr | 6 | with a median of $\sim535$ Myr |
| fit gas-to-dust ratio vs z, full sample | log(gdr) = 0.12 z + 1.79 | slope +-0.01, intercept +-0.04 | dimensionless | 6 | $\log(\delta_{\rm gdr})=(0.12\pm0.01)\times z + (1.79\pm0.04)$ |

## Qualitative findings

- Starbursts are preferentially at z>~3, likely reflecting the sensitivity limit of the selection  
  > "These super-MS objects, or starbursts, are preferentially found at $z \gtrsim 3$, which likely reflects the sensitivity limit of our source selection." (abstract)
- Irregular rest-frame UV SMGs are predominantly starbursts, disks mostly MS  
  > "Those SMGs that appear irregular in the rest-frame UV are predominantly starbursts, while the MS SMGs are mostly disk-like." (abstract)

## Claim tuples

- H: Do the SMGs follow the main sequence or lie in a starburst mode? | E: MAGPHYS SFR and M* compared with Speagle et al. 2014 MS | R: 57.3% on MS, 41.9% above MS by factor >3 | F: SMGs comprise both highly star-forming MS galaxies and starbursts | **supported**
- H: Do starbursts exhaust gas faster than MS SMGs? | E: tau_dep = M_gas/SFR compared across Delta_MS | R: median 407 Myr (super-MS) vs 644 Myr (MS) | F: Super-MS SMGs consume gas faster | **partially**
- H: Do ALMA 1.3 mm-selected AzTEC SMGs have the same property distributions as 870 um ALESS SMGs? | E: Welch t-test and KS tests vs flux-matched ALESS sample | R: KS p-values 0.003-0.22 for most parameters, 0.48 for L_dust | F: Distributions unlikely drawn from common parents, possibly due to selection wavelength | **partially**
- H: Are z>3 SMGs progenitors of z~2 compact quiescent galaxies? | E: Mass-size and stellar mass distribution comparison with Krogager et al. 2014 | R: 21%+-5% of 98 within the mass-radio size relation; final-mass KS D=0.22, p=0.33 | F: Only broadly consistent; link not universal | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Large homogeneous multiwavelength sample in COSMOS enables panchromatic SED fitting; 1.3 mm dust used as gas tracer since CO is available for only two sources  
  > "To our knowledge, only two of our target SMGs have a published CO tracer-based molecular gas mass estimate available" (3.2)
- Alternative: AGN-host candidates removed rather than modelled, since MAGPHYS lacks an AGN component  
  > "AGN-host galaxies need to be discounted from an analysis of SED properties." (2.1.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Gas masses depend on uniform Galactic alpha_CO; may be overestimated by factor >~8 if alpha_CO ~0.8  
  > "then the dust-based gas masses can be overestimated by a factor of $\gtrsim8$" (3.2)
- Limitation (authors): Selection bias at z>~3 toward warmer, brighter sources  
  > "our $z\gtrsim3$ SMGs are likely biased towards warmer objects than at lower redshifts" (3.1.2)
- Caveat (inferred, ours): Energy balance assumes stellar and dust emission are co-spatial, which may fail for SMGs
- Caveat (inferred, ours): Photometric redshifts dominate (100/124); only 5 z>3 sources spectroscopic
- Caveat (inferred, ours): Many binned fits have low significance and small number statistics
- Caveat (inferred, ours): ALMA data are only used as flux densities; the ALMA reduction itself is not documented here

## Reproducibility

- Data public (paper): Public tools and COSMOS data; ALMA data acknowledged by project codes; SED code publicly available  
  > "`MAGPHYS` is publicly available, and can be retrieved at `http://www.iap.fr/magphys/magphys/MAGPHYS.html`." (footnote 9)
- Products in archive: _not stated_
- Missing: Aravena et al. ALMA 1.3 mm catalogue (in prep.) and calibrated fluxes
- Missing: Brisbin et al. 2017 redshifts and Herschel deblended photometry
- Missing: Binning details for fitted trends
- Data volume (inferred): Small if the published photometry table is used (~MB); raw ALMA data of 2013.1.00118.S ~tens of GB
- Score (inferred): 4/5, Photometry is tabulated and MAGPHYS is public so the SED analysis is reproducible; the ALMA reduction and some inputs are in companion papers.
- Rediscovery candidate: no, ALMA role is a single flux per source taken from an unpublished catalogue; the main results come from SED fits that need external companion data.

## Links

- Method: da Cunha et al. 2008, 2015 (MAGPHYS and its high-z extension)
- Method: Scoville et al. 2016 (dust-continuum gas mass calibration)
- Method: Speagle et al. 2014 (main-sequence prescription)
- Companion: Aravena et al. in prep. (ALMA 1.3 mm survey and catalogue)
- Companion: Brisbin et al. 2017 (counterparts, photometry and redshifts)
- Companion: Miettinen et al. 2017b (3 GHz radio sizes, morphologies)
- Related: COSMOS
- Related: ALESS
- Related: AzTEC/ASTE COSMOS survey
- Related: VLA-COSMOS 3 GHz
- Related: HerMES
- Related: PEP

## Checks

```json
{
 "quotes": 74,
 "quotes_ok": 74,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 94,
  "stated": 55,
  "rate": 0.585
 },
 "evidence_ok": true
}
```

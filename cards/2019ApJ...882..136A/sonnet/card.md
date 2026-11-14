# The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: Evolution of the Molecular Gas in CO-selected Galaxies

`2019ApJ...882..136A` | The Astrophysical Journal 2019 | first author: Aravena, Manuel | arXiv: 1903.09162 | DOI: 10.3847/1538-4357/ab30df

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies
- Question: How do the molecular gas properties (depletion times, gas fractions, main-sequence offset) of CO-selected ASPECS galaxies compare with targeted CO samples, and what is the contribution of starburst, main-sequence and passive galaxies to the cosmic molecular gas density?  
  > "we measure the contribution of galaxies above, below, and on the galaxy main sequence to the total cosmic molecular gas density at different lookback times." (abstract)
- Target **Hubble Ultra Deep Field (ASPECS LP 17-pointing mosaic)**: coordinates 03:32:38.0, -27:47:00 (mosaic center)  
  > "The observations were performed using a 17-point mosaic centered at (R.A., Decl)=(03:32:38.0, $-27$:47:00) in the HUDF." (2.1 ALMA band 3); z/distance CO sources at z=1.037-3.601  
  > "The observations were performed using a 17-point mosaic centered at (R.A., Decl)=(03:32:38.0, $-27$:47:00) in the HUDF." (2.1 ALMA band 3); distance from CO redshifts of detected lines, matched to optical/MUSE counterparts  
  > "The observations were performed using a 17-point mosaic centered at (R.A., Decl)=(03:32:38.0, $-27$:47:00) in the HUDF." (2.1 ALMA band 3)

## Data provenance

- ALMA projects: 2016.1.00324.L
- bands: Band 3, 84.0-115.0 GHz  
  > "covering the ALMA band 3, from 84.0 to 115.0 GHz in 5 frequency setups." (2.1 ALMA band 3)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-3  
  > "Observations were performed in a compact array configuration, C40-3, yielding a synthesized beam of $1.75''\times1.49''$ at 99.5 GHz." (2.1 ALMA band 3)
- baselines: _not stated_
- angular resolution: 1.75'' x 1.49'' at 99.5 GHz  
  > "yielding a synthesized beam of $1.75''\times1.49''$ at 99.5 GHz." (2.1 ALMA band 3)
- max recoverable scale: _not stated_
- sensitivity: ~0.2 mJy/beam per 23.5 km/s channel  
  > "The final cube reaches a sensitivity of $\sim 0.2$ mJy beam$^{-1}$ per 23.5 km s$^{-1}$ channel" (2.1 ALMA band 3)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=2-1, 3-2, 4-3 (1-0 also covered) (not stated)
- Other facility **HST / CANDELS / XDF**: optical/near-IR photometry and photo-z  
  > "we make use of this optical and infrared coverage of the XDF, including the photometric and spectroscopic redshift information available from (cite: skelton14)." (2.3 Ancillary data and SEDs)
- Other facility **MUSE**: spectroscopic redshifts  
  > "The MUSE spectroscopic survey provides spectroscopic redshifts for optically faint galaxies at the $\sim30$ magnitude level" (2.3 Ancillary data and SEDs)
- External data: PHIBSS1/2 CO z>1 comparison sample (87 sources)  
  > "This yields a sample of 87 PHIBSS1/2 CO sources at $z>1$, compared to the 18 ASPECS CO sources" (4.1 CO-selected galaxies in context) [from (cite: tacconi18)]
- External data: CO excitation ratios r21=0.76, r31=0.42, r41=0.31  
  > "we adopt $r_{21}=0.76\pm0.09$, $r_{31}=0.42\pm0.07$ and $r_{41}=0.31\pm0.06$." (3.1 CO measurements) [from (cite: daddi15)]
- External data: MS relation used to normalize sSFR  
  > "Also shown, are the observational relationships derived for the MS galaxies as a function of redshift (cite: schreiber15)." (4.1 CO-selected galaxies in context) [from (cite: schreiber15)]
- External data: Cosmic molecular gas density from ASPECS  
  > "total molecular gas mass obtained from the recent measurement of cosmic molecular gas density ($\rho_{{\rm H}_2}$) using ASPECS data (cite: decarli19)." (4.3 Molecular gas budget) [from (cite: decarli19)]

## Processing

### Calibration

- pipeline or manual: CASA, independent procedure following the ALMA pipeline closely  
  > "The data were calibrated and imaged using the CASA software, using an independent procedure, which follows the ALMA pipeline closely." (2.1 ALMA band 3)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: TCLEAN  
  > "The visibilities were inverted using the TCLEAN task." (2.1 ALMA band 3)
- deconvolver: none; dirty cubes used  
  > "Since no very bright sources are found in the data cube, we used the ‘dirty’ cubes." (2.1 ALMA band 3)
- weighting robust: _not stated_
- uv taper: ~3'' taper for a test cube  
  > "we created a new version of the ASPECS band-3 data cube, tapered to an angular resolution of $\sim3''$" (Appendix: Flux measurements in tapered cubes)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: rebinned to 7.813 MHz channels (23.5 km/s)  
  > "The data were rebinned to a channel resolution of 7.813 MHz, corresponding to 23.5 km s$^{-1}$ at 99.5 GHz." (2.1 ALMA band 3)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Survey setup and data reduction  
  > "The ASPECS LP band 3 survey setup and data reduction steps are discussed in detail by (cite: decarli19)." (2 Observations) [from (cite: decarli19)]
- Line search procedures and CO flux measurement  
  > "Following (cite: gonzalezlopez19), the total CO intensities were derived from the ASPECS band-3 data cube by creating moment-0 images" (3.1 CO measurements) [from (cite: gonzalezlopez19)]
- MAGPHYS SED fitting setup  
  > "We fit the SED of the continuum-detected galaxies using the high-redshift extension of MAGPHYS (cite: dacunha08; dacunha15), as described in detail in (cite: boogaard19)." (2.3 Ancillary data and SEDs) [from (cite: boogaard19)]

### Not stated but needed to reproduce (our reading)

- Number of channels/velocity range used in moment-0 and spatial integration region for fluxes
- Details of the CASA version, tclean parameters (weighting, robust, cell, size)
- MAGPHYS priors and photometry catalog details (in companion papers)
- Exact PHIBSS1/2 subsample selection list
- Uncertainty treatment for gas budget, including binomial errors

## Analysis recipe

1. **Select CO line emitters**: LineSeeker search with kernels 50-500 km/s; fidelity F=1-Nneg/Npos >0.9  
  > "The probability of each line candidate of not being due to noise peaks, or *Fidelity*, $F$, was assessed by using the number of negative line sources in the data cube, with $F=1-N_{\rm Neg}/N_{\rm Pos}$." (2.2 CO sample)
   - software: LineSeeker, findclumps, MF3D
   - parameter: fidelity > 0.9 gives 16 candidates  
  > "We select the sources for which the *fidelity* is above 0.9. This yields 16 selected line candidates." (2.2 CO sample)
   - fitting: _not stated_
   - validation: Two other independent line searches (findclumps, MF3D) agree  
  > "All the algorithms coincide in the statistical reliability of these sources." (2.2 CO sample)
2. **Measure CO fluxes and luminosities**: Moment-0 maps, integrated flux, L'CO from Solomon 1997 formula, converted to CO(1-0) with r_J1  
  > "We compute the CO luminosities, $L'_{\rm CO}$ in units of K km s$^{-1}$ pc$^{2}$, following (cite: solomon97):" (3.1 CO measurements)
   - assumption: r21=0.76, r31=0.42, r41=0.31 from Daddi et al.  
  > "we adopt $r_{21}=0.76\pm0.09$, $r_{31}=0.42\pm0.07$ and $r_{41}=0.31\pm0.06$." (3.1 CO measurements)
   - fitting: _not stated_
   - validation: Fluxes compared with tapered (~3'') cube; agree within uncertainties  
  > "The flux estimates for almost all sources are in excellent agreement within the uncertainties." (Appendix: Flux measurements in tapered cubes)
3. **Derive molecular gas masses**: M_H2 = alpha_CO L'CO(1-0)  
  > "we assume a value $\alpha_{\rm CO}=3.6$ $M_\ensuremath{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$." (3.1 CO measurements)
   - assumption: alpha_CO = 3.6 Msun (K km/s pc^2)^-1  
  > "we assume a value $\alpha_{\rm CO}=3.6$ $M_\ensuremath{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$." (3.1 CO measurements)
   - fitting: _not stated_
   - validation: Compared with metallicity-dependent alpha_CO (Tacconi18): median 4.4, <0.1 dex difference  
  > "This will yield $<0.1$ dex differences in the molecular gas mass estimates throughout this study with respect to the metallicity dependent approach." (3.1 CO measurements)
4. **Derive SFR and stellar mass by SED fitting**: MAGPHYS high-z extension fitted to UV-to-IR photometry plus ALMA 1.2 and 3 mm fluxes at the CO redshift  
  > "For each individual galaxy, we perform SED fits to the photometry fixed at the CO redshift." (2.3 Ancillary data and SEDs)
   - software: MAGPHYS
   - fitting: MAGPHYS energy-balance; Herschel SPIRE excluded  
  > "We do not include *Herschel* SPIRE photometry in the fits since its angular resolution is very poor" (2.3 Ancillary data and SEDs)
   - validation: _not stated_
5. **Compare with PHIBSS1/2 and scaling relations**: KS tests of distributions; offsets from Schreiber15 MS; t_dep=Mmol/SFR, mu_mol=Mmol/Mstars  
  > "we computed the two sided Kolmogorov Smirnov (KS) statistic, which yields the probability that two datasets are drawn from the same distribution." (4.1 CO-selected galaxies in context)
   - parameter: starburst log(delta_MS)>0.4; passive <-0.4  
  > "with log$(\delta_{\rm MS})= log$(sSFR/sSFR$_{\rm MS})$ above 0.4 (“starburst”); galaxies below the MS, with log$(\delta_{\rm MS})<-0.4$ (“passive”)" (4.3 Molecular gas budget)
   - fitting: _not stated_
   - validation: _not stated_
6. **Molecular gas budget by galaxy type**: Sum of gas masses per type in two z bins divided by total cosmic H2 density from ASPECS  
  > "we thus compute this contribution as the sum of all the molecular gas masses from galaxies of this particular type divided by the total molecular gas mass" (4.3 Molecular gas budget)
   - parameter: bins 1.0<z<1.7 (10 sources) and 2.0<z<3.1 (4 sources)  
  > "Each of these redshift bins contains 10 and 4 sources, respectively" (4.3 Molecular gas budget)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration, imaging (tclean), imfit for CO sizes  
  > "The data were calibrated and imaged using the CASA software" (2.1 ALMA band 3)
- **LineSeeker** : line search in the data cube  
  > "To inspect the data cubes we used the `LineSeeker` line search routine (cite: gonzalezlopez17)." (2.2 CO sample)
- **MAGPHYS** : SED fitting for SFR, Mstar  
  > "MAGPHYS delivers estimates for the stellar mass, star-formation rate (SFR), dust mass, and IR luminosity." (2.3 Ancillary data and SEDs)
- **3DBarolo** : tilted-ring modeling of velocity fields  
  > "We take advantage of the software $^{\rm 3D}$Barolo (cite: diteodoro15) to perform a tilted-ring modeling of the gas velocity field." (Appendix: CO kinematics)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Fraction of CO-selected sample off the MS | ~30% (5 of 16) | not stated | percent | 5 | we find that $\sim30\%$ of the galaxies (5 out of 16) are offset from the galaxy main sequence |
| KS probability for SFR distribution vs PHIBSS1/2 | 2.3e-4 | not stated | dimensionless | 5 | We find KS probabilities of 0.05, 2.3$\times10^{-4}$ and 0.06 for the stellar mass, SFR and molecular gas mass, respectively. |
| KS probabilities for mu_mol and t_dep | 0.33 and 0.0012 | not stated | dimensionless | 5 | A KS test comparing the distributions of $\mu_{\rm mol}$ and $t_{\rm dep}$ yields probabilities of 0.33 and 0.0012, respectively |
| Median alpha_CO (metallicity-dependent, excluding 3mm.13) | 4.4 | std 0.5 | Msun (K km/s pc^2)^-1 | 3 | we find a median of 4.4 $M_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$ and a standard deviation of 0.5 |
| Dynamical masses of 3mm.4, 3mm.5, 3mm.7 | 8.1e10, 2.7e11, 1.4e11 | 2.4e10, 0.8e11, 0.5e11 | Msun | 0 | $(8.1\pm2.4)\times10^{10}$ M$_\odot$, $(2.7\pm0.8)\times10^{11}$ M$_\odot$ and $(1.4\pm0.5)\times10^{11}$ M$_\odot$, respectively. |
| [CI]-based H2 mass limit for 3mm.13 | <1.9e10 | 3 sigma | Msun | 0 | we find a $3\sigma$ limit for the \[CI\]-based molecular gas mass $M({\rm H}_2)^{\rm CI}<1.9\times10^{10}$ $M_\odot$. |

## Qualitative findings

- ASPECS CO galaxies follow standard t_dep and mu_mol scaling relations with sSFR and redshift despite wider parameter range  
  > "the ASPECS CO-selected sources follow remarkably the standard scaling relations trends of $t_{\rm dep}$ and $\mu_{\rm mol}$ with sSFR and redshift." (5 Conclusions)

## Claim tuples

- H: CO-selected galaxies cover a different range of properties than targeted CO samples | E: Compare distributions of Mstar, SFR, Mmol with PHIBSS1/2 z>1 via KS tests | R: Lower median Mstar and SFR; KS p=0.05 and 2.3e-4 | F: ASPECS probes lower SFR and Mstar parameter space | **supported**
- H: CO-selected galaxies follow standard scaling relations | E: t_dep and mu_mol versus sSFR, redshift | R: Most follow t_dep~1 Gyr and expected trends | F: Standard relations extend to CO-selected sample | **supported**
- H: Which galaxy types dominate the cosmic molecular gas density | E: Split sample into starburst/MS/passive and compute fractions of the ASPECS rho_H2 | R: MS dominant; passive contribution tentatively rises toward z~1 | F: MS galaxies are the largest contributor | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: CO selection avoids biases of galaxies pre-selected from optical/near-IR surveys  
  > "Under this approach, galaxies are selected purely based on their molecular gas content." (1 Introduction)
- Alternative: Metallicity-dependent alpha_CO checked; fixed 3.6 adopted  
  > "for consistency with other papers in this series, in the following we assume a fixed $\alpha_{\rm CO}=3.6$" (3.1 CO measurements)
- How they decided it was enough: _not stated_
- Limitation (authors): Low number of sources gives large statistical uncertainties; half the sample unresolved in CO  
  > "While the analysis is still limited by the admittedly low number of sources (and thus large statistical uncertainties)" (4.3 Molecular gas budget)
- Caveat (inferred, ours): Fixed alpha_CO and literature CO excitation ratios dominate systematic uncertainty in gas masses
- Caveat (inferred, ours): SED-derived SFR and Mstar systematics up to 0.3 dex affect MS classification
- Caveat (inferred, ours): Tiny samples (4 sources in high-z bin) make budget fractions weak
- Caveat (inferred, ours): No fitting details for t_dep comparisons

## Reproducibility

- Data public (paper): Large program data referenced by project code; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: 2016.1.00324.L." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Full companion-paper procedures (Decarli19, Gonzalez-Lopez19, Boogaard19)
- Missing: Source SED catalog and PHIBSS subsample list
- Data volume (inferred): ~100-300 GB (band 3 mosaic cubes, 5 setups)
- Score (inferred): 3/5, Key reduction and measurements are delegated to companion papers; table values are given, so the downstream analysis is largely reproducible.
- Rediscovery candidate: no, Recipe depends on companion papers' catalogs and SED fits; not self-contained.

## Links

- Method: (cite: decarli19) (survey strategy, data reduction, CO LF)
- Method: (cite: gonzalezlopez19) (line search and CO flux measurements)
- Method: (cite: boogaard19) (optical IDs and SED fitting)
- Companion: (cite: popping19) (theoretical CO LF predictions)
- Companion: (cite: walter16) (ASPECS pilot)
- Related: ASPECS
- Related: PHIBSS1/2
- Related: MUSE HUDF

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
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
  "stated": 46,
  "rate": 0.561
 },
 "evidence_ok": true
}
```

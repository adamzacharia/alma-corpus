# A Survey of Atomic Carbon [C I] in High-redshift Main-sequence Galaxies

`2018ApJ...869...27V` | The Astrophysical Journal 2018 | first author: Valentino, Francesco | arXiv: 1810.11029 | DOI: 10.3847/1538-4357/aaeb88

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, high_z_galaxies
- Question: Is [C I](3P1-3P0) a good tracer of molecular gas in main-sequence galaxies at z~1.2, and how do its luminosity ratios and abundance compare with starbursts, SMGs and local LIRGs?  
  > "we designed and carried out a survey with the Atacama Large Millimeter Array (ALMA), targeting [C I]$(^3P_1\,-\,^{3}P_0)$ in upper main-sequence galaxies in the COSMOS field at $z\sim1.2$." (1 Introduction)
- Target **21 COSMOS main-sequence galaxies at z~1.12-1.30 (e.g. IDs 4233, 7540, 37250)**: coordinates RA/Dec per source in Table 1 (e.g. ID 4233: 150.39732, 2.24088 deg)  
  > "We selected targets in the COSMOS field (cite: scoville_2007) with (1) an available stellar mass estimate" (2.1 Sample selection); "| 4233 | 150.39732 | 2.24088 | $1.1630 \pm 0.0003$$^{a}$ |" (Table 1); z/distance z_spec = 1.12-1.30  
  > "We selected targets in the COSMOS field (cite: scoville_2007) with (1) an available stellar mass estimate" (2.1 Sample selection); "| 4233 | 150.39732 | 2.24088 | $1.1630 \pm 0.0003$$^{a}$ |" (Table 1); distance from sub-mm lines (CO(4-3), CO(5-4), [CI], CO(2-1)) per Table 1 notes  
  > "We selected targets in the COSMOS field (cite: scoville_2007) with (1) an available stellar mass estimate" (2.1 Sample selection); "| 4233 | 150.39732 | 2.24088 | $1.1630 \pm 0.0003$$^{a}$ |" (Table 1)

## Data provenance

- ALMA projects: 2016.1.01040.S, 2015.1.00260.S, 2016.1.00171.S
- bands: Band 6 (CI, CO(4-3), CO(5-4)); Band 3 (CO(2-1))  
  > "15 and 11 galaxies of our sample have been observed by ALMA Bands 6 and 3 independent observations targeting CO $(5-4)$ and CO $(2-1)$, respectively" (2.3 ALMA [C I](1-0) and CO observations)
- frequencies and spectral setup: contiguous SPWs of 1.875 GHz, requested resolution 7.8 MHz (~10 km/s); 3 scheduling blocks  
  > "within contiguous spectral windows (SPWs) of 1.875 GHz and a requested spectral resolution of $7.8$ MHz ($\sim10$ km s$^{-1}$)" (2.3 ALMA [C I](1-0) and CO observations)
- continuum bandwidth: 7.5 GHz  
  > "We simultaneously measured the continuum emission at observed $\sim1.3$ mm over $7.5$ GHz" (2.3 ALMA [C I](1-0) and CO observations)
- arrays: _not stated_
- configurations: C40-1  
  > "Data were collected in configuration C40-1, corresponding to a synthesized beam of $2.0\times1.7$”." (2.3 ALMA [C I](1-0) and CO observations)
- baselines: _not stated_
- angular resolution: 2.0x1.7 arcsec  
  > "Data were collected in configuration C40-1, corresponding to a synthesized beam of $2.0\times1.7$”." (2.3 ALMA [C I](1-0) and CO observations)
- max recoverable scale: _not stated_
- sensitivity: rms ~0.15 Jy km/s for 400 km/s line width; continuum rms ~0.07 mJy  
  > "down to an average rms/beam of $\sim0.15$ Jy km s$^{-1}$ for a line width of $400$ km s$^{-1}$" (2.3 ALMA [C I](1-0) and CO observations); "down to an rms of $\sim0.07$ mJy on the full frequency range" (2.3 ALMA [C I](1-0) and CO observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Cycle 4, PI F. Valentino; CO programs PI Daddi  
  > "Cycle 4 (Project ID: 2016.1.01040.S, PI: F. Valentino)" (2.3 ALMA [C I](1-0) and CO observations)
- Line: [C I] 3P1-3P0 (492.161 GHz)
- Line: CO 4-3 (461.041 GHz)
- Other facility **Herschel/PACS, SPIRE, Spitzer/MIPS, JCMT/SCUBA2, ASTE/AzTEC, IRAM/MAMBO**: FIR/mm photometry for SED fitting (super-deblended catalog)  
  > "we fit the emission from *Spitzer*/MIPS 24 $\mu$m (cite: sanders_2007), *Herschel*/PACS (cite: lutz_2011) and SPIRE bands (cite: oliver_2012)" (2.2 Ancillary data)
- Other facility **Herschel/FTS**: Local galaxy [CI] and CO data via Liu et al. 2015 compilation  
  > "This sample is drawn from the public compilation of all *Herschel*/Fourier Transform Spectrometer (FTS) observations in the *Herschel* Science Archive of local galaxies by (cite: liu_2015)." (3.1 Local galaxies)
- External data: Local galaxies' [CI] fluxes and FIR luminosities (32 galaxies)  
  > "In total we retrieved $32$ galaxies (out of $146$ in the compilation by L15) with a [C I]$(^3P_1\,-\,^{3}P_0)$ $>3\sigma$ detection up to $z\sim0.03$." (3.1 Local galaxies) [from (cite: liu_2015)]
- External data: Low-J CO fluxes of local galaxies in 43.5" beam  
  > "we corrected the CO line measurements within the fixed 43.5” beam in K16 (their Table 3) to the galaxy-integrated values." (3.1 Local galaxies) [from (cite: kamenetzky_2016)]
- External data: High-z SMG and QSO [CI] and CO data  
  > "We assembled a sample of sub-millimeter galaxies (SMGs) and quasars (QSOs) with [C I]$(^3P_1\,-\,^{3}P_0)$ coverage from (cite: walter_2011), (cite: alaghband-zadeh_2013), and (cite: bothwell_2017)." (3.2 High-redshift sub-mm galaxies and quasars) [from (cite: walter_2011); (cite: alaghband-zadeh_2013); (cite: bothwell_2017)]
- External data: Super-deblended far-infrared photometry catalog  
  > "are detected with a cumulative infrared signal-to-noise ratio $\mathrm{SNR}>3$ and $>5$ in the “super-deblended” catalog by (cite: jin_2018)." (2.1 Sample selection) [from (cite: jin_2018)]
- External data: Stellar masses  
  > "we adopted the stellar masses listed in (cite: laigle_2016), consistent with the values derived by (cite: muzzin_2013)" (2.2 Ancillary data) [from (cite: laigle_2016); (cite: muzzin_2013)]

## Processing

### Calibration

- pipeline or manual: standard ALMA pipeline with CASA  
  > "We reduced the raw data with the standard ALMA pipeline with CASA (cite: mcmullin_2007)." (2.3 ALMA [C I](1-0) and CO observations)
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

- uv-plane 1D spectrum extraction with PSF/circular Gaussian models via iterative process  
  > "fitting visibilities in the *uv* space with the iterative process described in (cite: daddi_2015)" (2.3 ALMA [C I](1-0) and CO observations) [from (cite: daddi_2015)]
- SED modeling of super-deblended photometry  
  > "we modeled the “super-deblended” infrared photometry (cite: jin_2018) as in (cite: magdis_2012) to derive the galaxy integrated far-infrared properties." (2.2 Ancillary data) [from (cite: magdis_2012)]
- Metallicity-dependent alpha_CO and gas-to-dust conversion  
  > "In both cases we adopted a metallicity-dependent conversion factor as described in (cite: magdis_2012)" (4.4 Gas masses from dust and CO) [from (cite: magdis_2012)]
- [CI] mass formula  
  > "Following (cite: weiss_2005), the mass of atomic carbon is derived straightforwardly from $L'_{\mathrm{[C\,\scriptscriptstyle{I}\scriptstyle{]}}^3P_1\,-\, ^3P_0}$" (4.3 Neutral atomic carbon masses) [from (cite: weiss_2005)]

### Not stated but needed to reproduce (our reading)

- CASA version and pipeline version
- Channel selection and exact velocity widths per source for flux measurement
- Continuum/line-free channels and local continuum treatment details
- Details of the iterative uv-fitting (see Daddi et al. 2015)
- SED fit settings (DL07 library expansion, bootstrap count)
- Survival analysis implementation details
- Redshift/CO line fluxes for Daddi et al. in prep. data
- Priors/settings of LINMIXERR fit

## Analysis recipe

1. **extract spectra and measure line/continuum fluxes**: Calibrated cubes converted to uvfits; 1D spectra extracted by uv-plane fitting with PSF or circular Gaussian; fluxes as weighted-average over SNR-maximizing channels times velocity width, plus 10% correction to total  
  > "We measured fluxes as the weighted average flux density within the channels maximizing the SNR, times the velocity width covered by these channels." (2.3 ALMA [C I](1-0) and CO observations)
   - software: CASA, GILDAS
   - parameter: line width and centre fixed from high-SN CO lines  
  > "fix the center of the circular Gaussian or PSF to extract the spectrum, the central line frequency, and the width of" (ALMA [C I](1-0) and CO observations)
   - assumption: continuum slope nu^3.5 (beta=1.5)  
  > "assuming an intrinsic slope of $\nu^{3.5}$ ($\beta=1.5$)" (2.3 ALMA [C I](1-0) and CO observations)
   - fitting: single or double Gaussian fits for comparison of total fluxes  
  > "We further fit single or double Gaussians to the line profile to estimate total fluxes, generally $\sim10$% larger" (2.3 ALMA [C I](1-0) and CO observations)
   - validation: Results agree with measurements leaving line centre and width free  
  > "These results agree with measurements leaving each line center and width free to vary." (2.3 ALMA [C I](1-0) and CO observations)
2. **derive L_IR, M_dust and SFR via SED fitting**: Fit super-deblended photometry with expanded Draine & Li 2007 models plus AGN torus; bootstrap for errors  
  > "We then bootstrapped the values within the observed errors to estimate the statistical uncertainties on the derived quantities." (2.2 Ancillary data)
   - parameter: L_IR over 8-1000 um; SFR = L_IR/(9.86e9)  
  > "$\mathrm{SFR} =
L_{\mathrm{IR}}\,[L_\odot] / (9.86 \times 10^9)$ $M_{\odot}$ yr$^{-1}$" (2.2 Ancillary data)
   - assumption: Chabrier IMF  
  > "a Chabrier initial mass function (cite: chabrier_2003)" (1 Introduction)
   - fitting: upper limits included as nominal values weighted by large uncertainties  
  > "While fitting the SEDs, we included the upper limits in every band, modeling the nominal values weighted by their large uncertainties." (2.2 Ancillary data)
   - validation: _not stated_
3. **compute line luminosities and fit L_IR-L'[CI] relation**: L' from Solomon & Vanden Bout formula; Spearman/Pearson correlation; linear regression in log-log with Bayesian and chi2 fits  
  > "We further applied a linear regression analysis on $\mathrm{log}(L_{\rm IR})$ – $\mathrm{log}($$L'_{\mathrm{[C\,\scriptscriptstyle{I}\scriptstyle{]}}^3P_1\,-\, ^3P_0}$$)$ both using a Bayesian (LINMIXERR.PRO, (cite: kelly_2007))" (4.1 L_IR - L'[CI] relation)
   - software: LINMIXERR.PRO, MPFIT.PRO
   - parameter: AGN and QSOs excluded; 57 detections and 10 upper limits  
  > "We modeled a total of $57$ [C I]$(^3P_1\,-\,^{3}P_0)$-detected galaxies and $10$ upper limits." (4.1 L_IR - L'[CI] relation)
   - assumption: cosmology Omega_m=0.3, Omega_L=0.7, H0=70  
  > "$\Omega_{\rm m} = 0.3$, $\Omega_{\rm \Lambda} = 0.7$, and $H_0 = 70$ km s$^{-1}$ Mpc$^{-1}$" (1 Introduction)
   - fitting: Bayesian (Kelly 2007) with upper limits; chi2 (MPFIT) for check  
  > "The two algorithms we applied provided fully consistent results within the uncertainties, and the effect of upper limits is negligible." (4.1 L_IR - L'[CI] relation)
   - validation: two algorithms consistent  
  > "The two algorithms we applied provided fully consistent results within the uncertainties, and the effect of upper limits is negligible." (4.1 L_IR - L'[CI] relation)
4. **compare L'[CI]/L'CO(2-1) and M[CI]/Mdust ratios**: Mean log ratios with scatter, Kaplan-Meier survival analysis for upper limits; r32=0.62 and r21=0.84 conversions  
  > "For the W11 sample we converted CO $(3-2)$ to CO $(2-1)$ applying a $r_{\rm
  32}=L'_{\rm CO(3-2)}/L'_{\rm CO(2-1)}=0.62$ (cite: bothwell_2013)." (4.2 L'[CI] - L'CO(2-1) relation)
   - fitting: _not stated_
   - validation: survival-analysis values consistent with detections-only  
  > "The inclusion of $6$ upper limits with a survival analysis provides consistent values" (4.2 L'[CI] - L'CO(2-1) relation)
5. **derive [CI] masses and gas masses**: M[CI] from Weiss et al. formula with Tex=30 K; gas masses from dust (delta_GDR) and CO (alpha_CO) with metallicity from the FMR; helium 1.36x  
  > "we assume a fixed [C I] excitation temperature $T_{\rm ex} =
30$ K for all galaxies." (4.3 Neutral atomic carbon masses)
   - parameter: starbursts/SMGs: alpha_CO=0.8, delta_GDR=30; 0.2 dex error on both  
  > "fixing the conversion factors to $\alpha_{\rm
  CO}=0.8$ $M_{\odot}$/(K km s$^{-1}$ pc$^2$), and $\delta_{\rm GDR}=30$." (4.4 Gas masses from dust and CO)
   - assumption: Fundamental Metallicity Relation for metallicities  
  > "We derived metallicities converting stellar masses and SFR with the Fundamental Metallicity Relation (cite: mannucci_2010)." (4.4 Gas masses from dust and CO)
   - fitting: _not stated_
   - validation: Tex=dust temperature gives similar results  
  > "we find similar results ($\langle
T_{\rm dust} \rangle = 31 \pm 1$ K for the MS calibration sample" (4.3 Neutral atomic carbon masses)
6. **derive [CI]/H2 abundance and carbon mass fraction**: [CI]/[H2] = M[CI]/(6 M_H2); f[CI] from metal mass fraction with solar Z=0.0134 and C/metals=0.1779  
  > "Assuming a solar metallicity and composition ($Z_\odot=0.0134$ and $\frac{M_{\rm
    C}}{M_{\rm metals}}=0.1779$, (cite: asplund_2009))" (5.2 The small fraction of atomic carbon in galaxies)
   - assumption: carbon locked in stars neglected  
  > "Neglecting the carbon locked into stars" (5.2 The small fraction of atomic carbon in galaxies)
   - fitting: _not stated_
   - validation: FMR metallicity does not change result  
  > "Using the metallicity from the Fundamental Metallicity Relation does not impact this result" (5.2 The small fraction of atomic carbon in galaxies)

## Software

- **CASA** : ALMA pipeline reduction  
  > "We reduced the raw data with the standard ALMA pipeline with CASA (cite: mcmullin_2007)." (2.3 ALMA [C I](1-0) and CO observations)
- **GILDAS** : uv-plane analysis and spectrum extraction  
  > "We then converted the calibrated data cubes to *uvfits* and analyzed them with GILDAS (cite: guilloteau_2000)." (2.3 ALMA [C I](1-0) and CO observations)
- **LINMIXERR.PRO** : Bayesian linear regression  
  > "a Bayesian (LINMIXERR.PRO, (cite: kelly_2007))" (4.1 L_IR - L'[CI] relation)
- **MPFIT.PRO** : chi2 minimization fit  
  > "a $\chi^2$-minimization algorithm (MPFIT.PRO, (cite: markwardt_2009))" (4.1 L_IR - L'[CI] relation)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Slope of log L_IR - log L'[CI] relation | 0.78 | 0.05 | dimensionless | 3 | The Bayesian best fit model returns a sublinear slope of $0.78\pm0.05$ with an observed scatter of $\sigma=0.26$ dex. |
| Mean log(L'[CI]/L_IR) for 16 MS galaxies | -2.43 | 0.06 | log K km/s pc^2 / Lsun | 3 | for $16$ MS galaxies is $(-2.43\pm0.06)$ |
| Mean log(L'[CI]/L'CO(2-1)) | -0.69 | 0.04 | dimensionless | 4 | $=(-0.69\pm0.04)$ with an observed scatter of $0.23$ dex for $37$ $>3\sigma$-detected galaxies |
| Mean log(M[CI]/Mdust) | -2.20 | 0.03 | dimensionless | 4 | $\mathrm{log(}$$M_{\rm{[C\,\scriptscriptstyle{I}\scriptstyle{]}}}$/$M_{\rm dust}$$)=(-2.20\pm0.03)$ |
| Mean log([CI]/[H2]) MS galaxies, dust-based | -4.7 | 0.1 | dimensionless | 6 | $\mathrm{log(}[\mathrm{C\,\scriptstyle{I}}] /
[\mathrm{H}_2]) = (-4.7\pm 0.1)$ and $(-4.8\pm0.2)$ |
| Atomic carbon mass fraction f[CI] MS (dust) | 4.6% | +1.3/-1.0 | % | 6 | is $4.6^{+1.3}_{-1.0}$% and $3.4^{+1.4}_{-1.0}$% using $M_{\rm dust}$ and $L'_{\rm CO(2-1)}$ |
| [CI] detections >3 sigma | 18 of 21 | not stated | sources | 1 | We measured integrated [C I]$(^3P_1\,-\,^{3}P_0)$ fluxes at $>3\sigma$ in $18/21$ sources |

## Qualitative findings

- L'[CI] correlates with L_IR like low-J CO; MS galaxies have higher L'[CI]/L_IR than SMGs/starbursts (~4 sigma)  
  > "the $\sim4\sigma$ significant displacement of the [C I]$(^3P_1\,-\,^{3}P_0)$-detected MS galaxies from the sequence traced by SBs/SMGs" (Conclusions)

## Claim tuples

- H: [CI] luminosity correlates with L_IR like CO | E: Regression of L_IR vs L'[CI] for MS, local, SMG samples | R: Sublinear slope 0.78±0.05, scatter 0.26 dex | F: [CI] behaves like low-J CO on global scales | **supported**
- H: MS galaxies differ from starbursts in L'[CI]/L_IR | E: Compared mean ratios with survival analysis | R: MS -2.43±0.06 vs SMGs -2.77±0.07 | F: MS galaxies have ~2x larger ratio | **supported**
- H: [CI] traces molecular gas like CO and dust across populations | E: L'[CI]/L'CO(2-1) and M[CI]/Mdust across samples | R: Similar ratios within ~0.2 dex intrinsic scatter | F: [CI] is a good gas tracer | **supported**
- H: A universal [CI] abundance is valid | E: Derived [CI]/[H2] with standard alpha_CO and delta_GDR | R: MS ~1.6-1.9e-5, 3-8x lower than SMGs, ~4x lower than local LIRGs | F: Caution against universal abundance | **supported**

## Reasoning

- Why this data: Existing [CI] detections are biased toward lensed starbursts, SMGs and QSOs, not main-sequence galaxies  
  > "this handful of galaxies ($\sim35$) selected in diverse ways is not representative of the average main-sequence population" (1 Introduction)
- Why this method: _not stated_
- Alternative: Tex from dust temperature gave similar results to fixed 30 K  
  > "Assuming the dust temperature that we estimate from the far-infrared SED modeling as a first guess for the [C I] $T_{\rm ex}$, we find similar results" (4.3 Neutral atomic carbon masses)
- How they decided it was enough: _not stated_
- Limitation (authors): Abundance differences driven by assumed alpha_CO and delta_GDR; degeneracies cannot be broken with current data  
  > "a degeneracy that cannot be broken with the available data and tools" (Conclusions)
- Limitation (authors): Systematic uncertainties on gas masses not included  
  > "Possible larger systematic uncertainties affecting the gas masses are not listed in the error budget" (4.4 Gas masses from dust and CO)
- Caveat (inferred, ours): Fixed Tex=30 K without [CI](2-1) for MS sample
- Caveat (inferred, ours): Sample of 21 out of 50 selected, possible selection bias toward detections
- Caveat (inferred, ours): Heterogeneous literature samples and homogenization assumptions
- Caveat (inferred, ours): Abundance comparison is circular with adopted conversion factors

## Reproducibility

- Data public (paper): ALMA project codes listed; COSMOS master catalog internal  
  > "In this work we made use of the COSMOS master spectroscopic catalog, available within the collaboration and kept updated by Mara Salvato." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA/pipeline versions
- Missing: Exact channel ranges and velocity widths per source
- Missing: Details of uv-fitting from Daddi et al. 2015
- Missing: Daddi et al. in prep. CO data details
- Missing: Internal COSMOS master spectroscopic catalog
- Data volume (inferred): ~tens of GB (three Band 6 scheduling blocks plus Band 3/6 CO programs, low-resolution C40-1)
- Score (inferred): 5/5, ALMA data are public and many numbers are tabulated, but the extraction recipe relies on prior work and missing parameters, and external compilations are needed.
- Rediscovery candidate: no, Recipe depends on uv-fitting from other papers, unpublished CO data and literature compilations; parameters incomplete.

## Links

- Method: (cite: daddi_2015) (uv-plane spectrum extraction method)
- Method: (cite: magdis_2012) (SED fitting and metallicity-dependent conversion factors)
- Method: (cite: weiss_2005) ([CI] mass formula)
- Companion: Daddi et al. in prep. (CO(2-1) and CO(5-4) ALMA programs)
- Companion: Valentino et al. in prep. (full CO and [CI] modeling of whole sample)
- Companion: (cite: jin_2018) (super-deblended COSMOS catalog)
- Related: COSMOS
- Related: Herschel PEP
- Related: Herschel/FTS local compilation

## Checks

```json
{
 "quotes": 77,
 "quotes_ok": 77,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 89,
  "stated": 56,
  "rate": 0.629
 },
 "evidence_ok": true
}
```

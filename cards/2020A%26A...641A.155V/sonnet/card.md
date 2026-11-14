# CO emission in distant galaxies on and above the main sequence

`2020A&A...641A.155V` | Astronomy and Astrophysics 2020 | first author: Valentino, F. | arXiv: 2006.12521 | DOI: 10.1051/0004-6361/202038322

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies, star_formation
- Question: How do CO line emission and excitation (CO SLEDs) of IR-selected galaxies on and above the main sequence at z~1.1-1.7 depend on L_IR, SFE, <U>, Sigma_SFR and distance from the main sequence?  
  > "Our main goal is to explore the excitation conditions of the molecular gas in normal disks and bursty objects and to relate it with their star formation modes" (Introduction)
- Target **123 IR-bright COSMOS galaxies on and above the main sequence at z~1.1-1.7**: coordinates _not stated_; z/distance z ~ 1.1-1.7 (median z=1.25)  
  > "distributed on and above the main sequence at $z \simeq 1.1-1.7$ in the COSMOS area" (2.1 The primary CO (5-4) sample); distance from optical/near-IR spectroscopic redshifts from the COSMOS master catalog, refined with ALMA sub-mm redshifts  
  > "distributed on and above the main sequence at $z \simeq 1.1-1.7$ in the COSMOS area" (2.1 The primary CO (5-4) sample)

## Data provenance

- ALMA projects: 2015.1.00260.S, 2016.1.00171.S, 2019.1.01702.S, 2016.1.01040.S, 2018.1.00635.S
- bands: Band 6 (CO 5-4), Band 3 (CO 2-1), Band 7 (CO 7-6 + [CI] 2-1)  
  > "| Cycle 7 | Band 7 | CO $(7-6)$, \[C I\]$(^3P_2\,-\, ^{3}P_1)$ | $15$ | $24$ | $1.0\ensuremath{''}$ | $0.25$$^{b}$ |" (Table 1)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.8'' (Band 6), ~1.4'' (Band 3), ~1.0'' (Band 7)  
  > "delivering cubes for all targets with an average beam size of $\sim0.8\ensuremath{''}$" (3.1 ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: rms 0.5 mJy (Band 6), 0.375 mJy (Band 3), 0.190-0.315 mJy (Band 7)  
  > "reaching a flux density rms of $0.190-0.315$ mJy" (3.1 ALMA Observations)
- time on source: <~1.7 min (Band 6), ~4 min (Band 3) per target  
  > "was reached in $\lesssim1.7$ minutes of integration on source per target" (3.1 ALMA Observations)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO 5-4 (not stated)
- Line: CO 2-1 (not stated)
- Line: CO 7-6 (not stated)
- Line: [C I] 3P2-3P1 (not stated)
- Other facility **Herschel PACS/SPIRE, Spitzer MIPS, JCMT/SCUBA2, ASTE/AzTEC, IRAM/MAMBO, VLA**: IR-to-radio photometry from the super-deblended COSMOS catalog for SED modeling  
  > "The catalog includes emission recorded by *Spitzer*/MIPS at $24$ $\mu$m" (3.3 Infrared SED modeling)
- Other facility **Chandra**: X-ray luminosities to check AGN classification  
  > "Figure [4](#fig:agn) further shows how our AGN scheme overlaps with the detection rate of hard X-ray photons from *Chandra*" (3.3.1 AGN contamination)
- External data: Super-deblended IR photometry catalog of COSMOS  
  > "We re-modeled the IR photometry of our sources from the “super-deblended” catalog of the COSMOS field" (3.3 Infrared SED modeling) [from (cite: jin_2018)]
- External data: Stellar masses  
  > "compiling stellar masses (cite: muzzin_2013; laigle_2016)" (3.4 Ancillary data) [from (cite: muzzin_2013; laigle_2016)]
- External data: Literature CO samples (Herschel-FTS, HerCULES, HERACLES, PHIBSS-2, BzK, starbursts, SMGs) homogenized to the paper's conventions  
  > "To put in context the new ALMA data, we compiled samples from the literature" (3.5 Literature data) [from Table 1 references (K16, L15a, R15, L08, F19, A10, A14, D10a, Da09, D15, S15, S18a,b)]
- External data: CO (4-3) and [CI] (1-0) fluxes for part of sample  
  > "galaxies have at least a detection of \[C I\]$(^3P_1\,-\,^{3}P_0)$, CO $(4-3)$, \[C I\]$(^3P_2\,-\, ^{3}P_1)$, and CO $(7-6)$ from V18 and V20" (2.2 The CO (2-1) and CO (7-6) follow-up) [from V18 (cite: valentino_2018), V20 (cite: valentino_2020b)]
- Simulation/model as data: Model SLED tracks from Papadopoulos+2012, Narayanan & Krumholz 2014, Bournaud+2015, Vollmer+2017 compared with observed SLEDs  
  > "we show the same tracks reported in D15: the empirical model from (cite: papadopoulos_2012) and the hydrodynamical simulations from (cite: narayanan_2014) and (cite: bournaud_2015)" (4.4.2 Modeling of the CO SLEDs)

## Processing

### Calibration

- pipeline or manual: standard CASA pipeline  
  > "We calibrated the cubes using the standard pipeline with CASA (cite: mcmullin_2007)" (3.2 Data reduction and spectral extraction)
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
- continuum subtraction: continuum from S/N-weighted average of line-free channels over ~7.5 GHz, power law nu^3.7, subtracted from line flux  
  > "we considered a $S/N$-weighted average of line-free channels over the full spectral width ($\sim7.5$ GHz), assuming an intrinsic power-law shape ($\propto\nu^{3.7}$)" (3.2.1 Line and continuum flux measurements)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: all ALMA observations combined in uv space with arbitrary renormalization  
  > "we combined all the available ALMA observations in the *uv* space allowing for an arbitrary renormalization of the signal for all tracers" (3.2 Data reduction and spectral extraction)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Iterative reduction and uv-plane spectral extraction procedure  
  > "We reduced the data following the iterative procedure described in D15" (3.2 Data reduction and spectral extraction) [from D15 (cite: daddi_2015); see also V18, V20, (cite: coogan_2018; puglisi_2019; jin_2019)]
- Spurious-line probability calculation  
  > "computed the probability for each candidate line to be spurious ($P_{\rm line}$) following the approach in (cite: jin_2019)" (3.2.1 Line and continuum flux measurements) [from (cite: jin_2019)]
- Flux loss correction for point-source extraction  
  > "We estimated these losses as detailed in Appendix B of V20" (Total recovered fluxes) [from V20 (cite: valentino_2020b)]
- IR SED modeling approach  
  > "Our modeling follows the approach of (cite: magdis_2012) and V20." (3.3 Infrared SED modeling) [from (cite: magdis_2012); V20]
- LVG modeling approach  
  > "Here we followed the approach used in D15 (D. Liu et al. in prep.)." (4.4.4 Large velocity gradient modeling) [from D15; D. Liu et al. in prep.]
- Main-sequence parameterization and starburst threshold  
  > "The threshold for the definition of starburst is arbitrary and set in order to be consistent with V18 and V20." (2.1 The primary CO (5-4) sample) [from (cite: sargent_2014); V18; V20]

### Not stated but needed to reproduce (our reading)

- CASA version and pipeline version
- Weighting, robust and cleaning parameters (cubes are fit in uv plane, so mainly channel widths)
- Exact GILDAS scripts for the uv-plane fitting (customized, not released)
- Channel width / velocity resolution of the extracted spectra
- Line-free channel selections per source
- Metallicity assignment details for individual galaxies
- Details of the Kelly LINMIX censored-data treatment per fit
- Redshift-dependent flux correction details for archival flux scales
- Rest frequencies of lines

## Analysis recipe

1. **Extract spectra in uv plane**: Combine all ALMA data in uv space; fit circular Gaussian (position, size, flux per channel free) or point source; derive P_unres  
  > "We then modeled each source as circular Gaussian in the *uv* plane to extract the spectrum, allowing the source position, size, and total flux per channel to vary." (3.2 Data reduction and spectral extraction)
   - software: CASA, GILDAS
   - fitting: _not stated_
   - validation: Compared with image-plane fitting in earlier work; flux-loss corrections via injected mock sources  
  > "This method has no obvious bias against fitting in the image plane (cite: coogan_2018), but it has more flexibility in fitting parameters." (3.2 Data reduction and spectral extraction)
2. **Blind line search and flux measurement**: Maximum S/N over progressively larger frequency windows; flux over fixed velocity width set by CO(5-4); continuum subtracted; fluxes increased by 10% to match Gaussian parameterization  
  > "We did so by looking for the maximum $S/N$ computed over progressively larger frequency windows centered on each channel." (3.2.1 Line and continuum flux measurements)
   - software: GILDAS
   - parameter: upper limits: 3 sigma, Delta v = 400 km/s when only optical z available  
  > "eventually measured only upper limits adopting an arbitrary $\Delta v = 400$ km s$^{-1}$ to be consistent with V18 and V20" (3.2.1 Line and continuum flux measurements)
   - fitting: _not stated_
   - validation: Simulations of spurious-line probability, visual inspection by two team members, quality flags  
  > "As a further check, two members of our team visually inspected all the available spectra independently." (3.2.1 Line and continuum flux measurements)
3. **Model IR SED**: Fit super-deblended photometry plus ALMA continuum with Draine & Li (2007) models and Mullaney AGN templates to get L_IR, M_dust, <U>, f_AGN  
  > "We used an expanded library of (cite: draine_2007) models and the AGN templates from (cite: mullaney_2011)" (3.3 Infrared SED modeling)
   - software: CIGALE
   - parameter: AGN reliable if f_AGN+1sigma>=20%; AGN-dominated if f_AGN>=80% (excluded)  
  > "galaxies with $f_{\rm AGN}\geq 80$% are flagged as AGN dominated" (3.3.1 AGN contamination)
   - assumption: <U> = 1/125 x L_IR/M_dust; dust emission optically thin above 100 um  
  > "our SED modeling is based on the assumption that the dust emission is optically thin above $100\,\mu\mathrm{m}$" (4.4.5 The effect of dust opacity on the high-J CO emission)
   - fitting: _not stated_
   - validation: AGN classification compared with IRAC colors and Chandra X-ray luminosities  
  > "Ninety percent of sources with $Flag\geq0$ and $f_{\rm AGN}+1\sigma_{f_\mathrm{AGN}}\geq 20$% also have $L_{\rm 2-10\, keV}\geq 10^{42}$ erg s$^{-1}$." (3.3.1 AGN contamination)
4. **Fit scaling relations**: Bayesian linear regression in log space with errors on both variables and censored data (LINMIX_ERR)  
  > "applying a Bayesian regression analysis (LINMIX ERR.PRO, (cite: kelly_2007))" (4.1 How does the CO emission correlate with the infrared luminosity?)
   - software: LINMIX_ERR
   - parameter: includes sources with L_IR>=10^8.5 Lsun and Flag=0.5 upper limits; excludes AGN-dominated galaxies and QSOs  
  > "The modeling includes our and literature sources with $L_{\rm IR}\geq10^{8.5}$ $L_{\odot}$, reliable upper limits on the line luminosities ($Flag=0.5$)" (4.1 How does the CO emission correlate with the infrared luminosity?)
   - assumption: Gas mass from M_dust with metallicity-dependent gas-to-dust ratio log(delta_GDR)=10.54-0.99x(12+log(O/H)); starbursts supersolar (delta_GDR~30); Sigma_SFR=SFR/(2 pi R^2), R=FWHM/2  
  > "we then assumed that starburst galaxies have supersolar metallicities ($\delta_{\rm GDR}\sim30$" (4.3.1 The star formation efficiency and the mean interstellar radiation field intensity)
   - fitting: Kelly (2007) Bayesian approach  
  > "adopting the Bayesian approach described in (cite: kelly_2007)" (Table 5 notes)
   - validation: Robustness checks excluding SMGs, outliers, high-z only; alternate metallicity assumptions  
  > "fitting only the high-redshift samples changes the slopes of the two relations by $<15$% at $<3\sigma$ significance" (4.1 How does the CO emission correlate with the infrared luminosity?)
5. **Average CO SLEDs and line ratios**: Mean/median L' for MS, SB (DeltaMS>=3.5) and extreme SB (>=7) restricted to objects meeting the CO(2-1) follow-up criterion; compute R_52, R_72 etc.  
  > "We computed these values for the objects meeting the requirements for a potential CO $(2-1)$ follow-up, based on the updated IR photometry." (4.4 The CO spectral line energy distribution of distant main-sequence galaxies)
   - fitting: _not stated_
   - validation: _not stated_
6. **LVG modeling of CO+[CI] SLEDs**: RADEX grid at z=1.25, n(H2)=1e2-1e6 cm^-3, T_kin=5-300 K, two components (n_low<n_high), fit with michi2 chi2 minimization  
  > "We computed a model grid for the median redshift of the sample ($z=1.25$), covering density and temperature intervals of $n(\mathrm{H}_2)=10^2-10^6\,\mathrm{cm}^{-3}$ and $T_{\rm kin}= 5-300$ K" (4.4.4 Large velocity gradient modeling)
   - software: RADEX, michi2
   - parameter: line width fixed to 50 km/s (scale height 10 pc); [CO/H2]/(dv/dr)=1e-5 km/s/pc; [CI]/H2=3e-5; ortho-to-para 3  
  > "We fixed the line width to $50$ km s$^{-1}$ or, equivalently, the cloud scale height to 10 pc" (4.4.4 Large velocity gradient modeling)
   - assumption: [CI] co-spatial with CO; dense and diffuse gas share same metallicity  
  > "under the assumption that the neutral atomic carbon is co-spatial with CO" (4.4.4 Large velocity gradient modeling)
   - fitting: Customized chi2 minimization, 15,000 iterative samplings with normal randomization of parameters  
  > "we iteratively sampled the $\chi^2$ distribution $15,000$ times" (4.4.4 Large velocity gradient modeling)
   - validation: Single vs two components compared; CO-only fit gives same result; N(H2) and optical depths checked against GMC ranges  
  > "This result still holds when modeling only the CO emission, excluding the \[C I\] transitions." (4.4.4 Large velocity gradient modeling)
7. **Test dust opacity effect**: tau_dust = kappa_850 (nu/nu_850)^beta M_dust/(2 pi R^2) using ALMA sizes  
  > "We adopted $\kappa_{\rm 850\,\mu m}=0.43\,\mathrm{cm^{-2}g^{-1}}$ and $\beta=2$ (cite: li_2001)" (4.4.5 The effect of dust opacity on the high-J CO emission)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : standard pipeline calibration  
  > "We calibrated the cubes using the standard pipeline with CASA (cite: mcmullin_2007)" (3.2 Data reduction and spectral extraction)
- **GILDAS** : customized scripts for uv-plane analysis and spectral extraction  
  > "analyzed them with customized scripts within GILDAS[^1] (cite: guilloteau_2000)" (3.2 Data reduction and spectral extraction)
- **LINMIX_ERR** : Bayesian linear regression  
  > "applying a Bayesian regression analysis (LINMIX ERR.PRO, (cite: kelly_2007))" (4.1 How does the CO emission correlate with the infrared luminosity?)
- **RADEX** : LVG model grid  
  > "First, we used the RADEX tool (cite: vandertak_2007) to create a grid of LVG models." (4.4.4 Large velocity gradient modeling)
- **michi2** : chi2 minimization for LVG fits  
  > "(MICHI2[^3], (cite: liu_2020_michi2))" (4.4.4 Large velocity gradient modeling)
- **CIGALE** : refit UV-to-near-IR photometry for AGN-contaminated sources to get stellar masses  
  > "we refit the UV to near-IR photometry using the code CIGALE[^2] (cite: noll_2009_cigale)" (3.4 Ancillary data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Slope of L_IR vs L'_CO(5-4) | 0.92 | 0.01 | dimensionless | 4 | / $L_{\rm IR}$, $L'_{\rm CO(5-4)}$                                / $0.92\pm0.01$  / $-1.55\pm0.08$ / $0.17\pm0.01$      / $0.99$      / |
| Slope of L_IR vs L'_CO(7-6) | 0.94 | 0.01 | dimensionless | 4 | / $L_{\rm IR}$, $L'_{\rm CO(7-6)}$                                / $0.94\pm0.01$  / $-2.34\pm0.09$ / $0.16\pm0.01$      / $0.99$      / |
| Slope of <U> vs R_52 | 0.36 | 0.05 | dimensionless | 4 | / $\langle U \rangle$, $R_{52}$                                   / $0.36\pm0.05$  / $-0.95\pm0.07$ / $0.15\pm0.02$      / $0.75$      / |
| Slope of Sigma_SFR vs R_52 | 0.16 | 0.02 | dimensionless | 4 | / $\Sigma_{\rm SFR}$, $R_{52}$                                    / $0.16\pm0.02$  / $-0.60\pm0.03$ / $0.14\pm0.02$      / $0.82$      / |
| R_52 main sequence / starbursts / extreme starbursts | 0.28 / 0.32 / 0.40 | 0.05 / 0.06 / 0.09 | dimensionless | 5 | /    $R_{52}$    / $0.28\pm0.05$ / $0.32\pm0.06$ /   $0.40\pm0.09$    / |
| R_72 main sequence / starbursts / extreme starbursts | 0.09 / 0.12 / 0.17 | 0.02 / 0.03 / 0.04 | dimensionless | 5 | /    $R_{72}$    / $0.09\pm0.02$ / $0.12\pm0.03$ /   $0.17\pm0.04$    / |
| Mean dust optical depth at CO(5-4) wavelength (520 um) | 0.012 | 0.003 | dimensionless | 7 | $\langle \tau_{\rm dust}\,(520\mu\mathrm{m})_{\rm CO(5-4)} \rangle=0.012\pm0.003$ |
| Mean velocity offset sub-mm minus optical redshift | 101 | 46 | km/s | 2 | $\langle \Delta v \mathrm{(submm-opt)}\rangle = 101\pm 46$ km s$^{-1}$with a dispersion of $338$ km s$^{-1}$ |
| Dense-phase fraction of molecular gas mass in MS galaxies | ~50 | not stated | percent | 6 | The latter encloses $\sim50$% of the total molecular gas mass for main-sequence galaxies. |
| MS two-component LVG log n_H2 low/high | 2.2 / 3.9 | 0.3 / 0.1 | log cm^-3 | 6 | / $\mathrm{log}\left( n_{\rm H_2} / [\mathrm{cm^{-3}}] \right)$ / $2.2\pm0.3$ / $3.9\pm0.1$ / |
| Detections of CO(5-4), CO(2-1), CO(7-6) | 50, 33, 13 galaxies | not stated | galaxies | 2 | We reliably detected the emission of CO $(5-4)$, CO $(2-1)$, and CO $(7-6)$+\[C I\]$(^3P_2\,-\, ^{3}P_1)$ in 50, 33, and 13 galaxies, respectively |

## Qualitative findings

- High-J CO luminosities scale quasi-linearly with L_IR, so they trace SFR; CO(2-1) follows a sub-linear relation consistent with the SK law  
  > "suggesting that these transitions might be used as SFR – rather than molecular $M_{\rm gas}$– tracers" (4.1 How does the CO emission correlate with the infrared luminosity?)
- Distinction between upper-MS and starburst SLEDs is blurred; excitation tracks Sigma_SFR better than DeltaMS  
  > "An operational definition based on $\Sigma_{\rm SFR}$ rather than on the offset from the main sequence might better separate truly starbursting galaxies from secularly evolving disks." (7 Conclusions)

## Claim tuples

- H: Are mid/high-J CO transitions SFR tracers in MS and SB galaxies? | E: Regress L'_CO(5-4), L'_CO(7-6) against L_IR for new and literature data | R: slopes 0.92 and 0.94, intrinsic scatter ~0.16 dex | F: CO(5-4) and CO(7-6) trace SFR quasi-linearly | **supported**
- H: What drives CO excitation (R_52)? | E: Regress R_52 against SFE, <U>, Sigma_SFR and DeltaMS | R: Strong correlations with SFE (rho~0.88), <U> (0.75), Sigma_SFR (0.82); weaker with DeltaMS (0.55) | F: Excitation driven by large SFR over compact regions | **supported**
- H: Is the CO SLED of starbursts more excited than that of MS galaxies? | E: Average SLEDs in DeltaMS bins | R: R_52 0.28 vs 0.32 vs 0.40; ratios 1.1x and 1.2x higher for J=5,7 | F: Only tentative increase; distinction blurred by intrinsic diversity | **partially**
- H: Does a dense excited component exist in high-z MS galaxies and does dust opacity suppress high-J CO? | E: Two-component RADEX LVG fits; optical depth calculation | R: dense component holds ~50% of gas mass; mean tau ~0.01-0.02 | F: Excited dense component exists; dust opacity minor | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Dust-based gas masses used instead of CO(2-1) to reduce correlation with R_52  
  > "The choice of using dust instead of CO $(2-1)$ to derive $M_{\rm gas}$ was dictated by the attempt to reduce the correlation with the quantity under scrutiny, $R_{52}$." (4.3.1 The star formation efficiency and the mean interstellar radiation field intensity)
- Alternative: Single-component LVG models rejected as poor representation of the SLEDs  
  > "single components do not provide a good representation to the observed CO SLEDs of both populations" (4.4.4 Large velocity gradient modeling)
- How they decided it was enough: _not stated_
- Limitation (authors): LVG parameters highly degenerate; best-fit values reflect relative trends only  
  > "due to the high degeneracy among the LVG parameters, even with a handful of CO lines one could not obtain results simultaneously constraining $n_{\rm H_2}$, $T_{\rm kin}$, and $N(\mathrm{H_2})$" (4.4.4 Large velocity gradient modeling)
- Limitation (authors): Sample biased to upper main sequence and warm dust by PACS detection requirement  
  > "We note that the initial requirement of a PACS detection steered the sample towards upper main-sequence objects and warm dust temperatures $T_{\rm dust}\gtrsim 30$ K." (2.1 The primary CO (5-4) sample)
- Caveat (inferred, ours): Gas masses depend on assumed gas-to-dust ratio and metallicity prescriptions
- Caveat (inferred, ours): Sizes for Sigma_SFR are heterogeneous across literature samples
- Caveat (inferred, ours): Selection thresholds bias line ratios; correction relies on restricted subsample
- Caveat (inferred, ours): LVG fits to averages with few lines and fixed parameters are weakly constrained
- Caveat (inferred, ours): Starburst bin has few objects and no CO(4-3)/[CI](1-0)

## Reproducibility

- Data public (paper): Full data table released in .fits format; spectra online  
  > "Similarly, the full data table is made public in .fits format." (Data tables, galaxy spectra and spectral energy distribution)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: Customized GILDAS scripts not provided
- Missing: CASA/pipeline versions
- Missing: michi2 settings and Liu et al. in prep. LVG details
- Missing: COSMOS master spectroscopic catalog (Salvato in prep.) unpublished
- Missing: Literature compilation homogenization specifics
- Data volume (inferred): Several hundred GB for 5 ALMA programs (~123 targets in Bands 6, 3, 7), raw/calibrated cubes
- Score (inferred): 3/5, ALMA data public and released tables exist, but the custom uv-plane extraction relies on unreleased GILDAS scripts and several unpublished inputs
- Rediscovery candidate: no, Recipe depends on custom scripts and unpublished catalogs; though results are numeric, a faithful redo is hard.

## Links

- Method: D15 (cite: daddi_2015) (Reduction procedure, L_IR-CO(5-4) relation and LVG approach)
- Method: (cite: jin_2019) (Spurious line probability approach)
- Method: V20 (cite: valentino_2020b) (Flux loss correction and SED modeling approach)
- Companion: (cite: puglisi_2019) (Far-IR sizes and P_unres of the sample)
- Companion: V18 (cite: valentino_2018) (Neutral carbon and CO(4-3) data for subset)
- Related: COSMOS
- Related: PHIBSS-2
- Related: HerCULES
- Related: HERACLES
- Related: KINGFISH

## Checks

```json
{
 "quotes": 82,
 "quotes_ok": 82,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 5,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 96,
  "stated": 57,
  "rate": 0.594
 },
 "evidence_ok": true
}
```

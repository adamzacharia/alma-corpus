# Molecular gas budget of strongly magnified low-mass star-forming galaxies at cosmic noon

`2024A&A...692A.215C` | Astronomy and Astrophysics 2024 | first author: Catán, V. | arXiv: 2408.07849 | DOI: 10.1051/0004-6361/202451892

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What is the molecular gas content (CO and dust based) of strongly magnified low-mass star-forming galaxies at cosmic noon, and do they show a molecular gas deficit relative to scaling relations?  
  > "The aim of this study is to investigate the molecular gas content of strongly magnified low-mass star-forming galaxies (SFGs) around the cosmic noon period ($z\sim2$)" (abstract)
- Target **12 SGAS lensed arcs (J0033, J0108, J0900A/B, J1050, J1050A, J1226A/B, J1429, J1527, J2111, Sunburst)**: coordinates e.g. J0033 00:33:41.55 +02:42:16.58 (per-arc in Table)  
  > "The redshifts analyzed range from 1.91 to 3.625, placing them within the cosmic noon period." (Introduction); "| SGASJ003341.5+024217 | J0033 | 00:33:41.55 | 2.3900$^{(1)}$ | 8.61$\pm$0.02$^{(2)}$ | 24$^{+9}_{-5}$ | \(1\) |" (Table 1); z/distance z_spec 1.91-3.63  
  > "The redshifts analyzed range from 1.91 to 3.625, placing them within the cosmic noon period." (Introduction); "| SGASJ003341.5+024217 | J0033 | 00:33:41.55 | 2.3900$^{(1)}$ | 8.61$\pm$0.02$^{(2)}$ | 24$^{+9}_{-5}$ | \(1\) |" (Table 1); distance from spectroscopic redshifts from literature (superscripted references in table)  
  > "The redshifts analyzed range from 1.91 to 3.625, placing them within the cosmic noon period." (Introduction); "| SGASJ003341.5+024217 | J0033 | 00:33:41.55 | 2.3900$^{(1)}$ | 8.61$\pm$0.02$^{(2)}$ | 24$^{+9}_{-5}$ | \(1\) |" (Table 1)

## Data provenance

- ALMA projects: 2018.1.01142.S, 2021.2.00092.S, 2022.1.00916.S, 2021.1.01337.S
- bands: Bands 3 and 4 for CO; bands 6 and 7 for dust continuum  
  > "The observations focused on bands 3 and 4 for CO, depending on the galaxy’s redshift, and bands 6 and 7 for the dust continuum." (2.2 ACA data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: ACA (7 m, 12 antennas)  
  > "This array consists of 12 radio antennae, each of 7 m in diameter, operating in interferometric mode." (2.2 ACA data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: CO beams ~10-18 arcsec; dust beams ~3-7 arcsec  
  > "| J0033        | 142       | 344       | 1.7          | 0.2          | 13.3$\times$7.2     | 4.7$\times$3.3      |" (Table 2)
- max recoverable scale: _not stated_
- sensitivity: CO rms 1.0-2.2 mJy/beam per 30 km/s channel; continuum rms 0.1-0.6 mJy/beam  
  > "for the CO bands, this was estimated for one channel of 30 kms$^{-1}$ in which emission was expected, and for the dust band, it was calculated using the MFS images, which covered 7.5 GHz." (Table 2 notes)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=3-2, 4-3 or 5-4 depending on redshift (not stated)
- Other facility **HST**: Photometry for SED fitting; false-colour images  
  > "We analyzed HST images obtained through various filters and instruments to construct spectral energy distributions (SEDs) for each galaxy." (2.3.1 HST data)
- Other facility **JWST (TEMPLATES)**: NIRCam and MIRI photometry for J1226  
  > "We complemented the above data with James Webb Space Telescope (JWST) observations for arc J1226 belonging to the TEMPLATES program" (2.3.2 JWST)
- External data: HST HLSP data and lens models for most fields  
  > "We used the models published by (cite: sharonStrongLensModels2020) for most of the fields in our sample." (2.3.3 Lens models) [from (cite: sharonStrongLensModels2020)]
- External data: Metallicities (SB99) for arcs  
  > "we used the STARBURST99 (SB99) (cite: leithererStarburst99SynthesisModels1999) values obtained from (cite: chisholmConstrainingMetallicitiesAges2019) and (cite: baylissPhysicalConditionsMetallicity2014)" (2.1 Sample selection) [from (cite: chisholmConstrainingMetallicitiesAges2019); (cite: baylissPhysicalConditionsMetallicity2014)]
- External data: Compiled observational CO excitation (r_J1 vs Sigma_SFR) dataset  
  > "we decided to compile an observational dataset (cite: taniguchiWhatControlsStar1998; papadopoulosMolecularGasLuminous2012; riechersDustobscuredMassiveMaximumstarburst2013;" (3.5.1) [from (cite: taniguchiWhatControlsStar1998) et al.]
- External data: PHIBSS scaling relations and catalogue  
  > "we used a sample of 137 high-redshift ($z>$2) SFGs from the PHIBSS catalog (cite: tacconiPHIBSSUnifiedScaling2018)" (4.1) [from (cite: tacconiPHIBSSUnifiedScaling2018)]
- Simulation/model as data: Narayanan & Krumholz simulated r_J1-Sigma_SFR relation used for r51  
  > "for the case of ${r}_{\rm{51}}$, where insufficient observational data were available, we opted to apply this simulated model." (3.5.1)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline of each cycle, no extra flagging  
  > "The calibration was done using the pipeline corresponding to each Atacama Large Millimeter/submillimeter Array (ALMA) cycle. No extra flagging was used" (2.2 ACA data)
- casa version: CASA 6.2.1.7 and 6.4.1.12  
  > "versions 6.2.1.7 and 6.4.1.12 for the different projects" (2.2 ACA data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: Hogbom  
  > "We applied a Hogbom deconvolution algorithm and a natural weighting." (2.2 ACA data)
- weighting robust: natural  
  > "We applied a Hogbom deconvolution algorithm and a natural weighting." (2.2 ACA data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: 3-sigma threshold, interactive manual masks  
  > "We cleaned the image or cube using a three-sigma threshold when emission was found; for this, we also interactively created manual masks" (2.2 ACA data)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: cubes of 60 channels of 30 km/s  
  > "Spectral cubes were made using 60 channels of 30 km s$^{-1}$ using the spectral windows (spws) close to the expected line." (2.2 ACA data)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Metallicity procedure  
  > "following the procedure outlined by (cite: solimanoMolecularGasBudget2021)" (2.1 Sample selection) [from (cite: solimanoMolecularGasBudget2021)]
- Dust mass equations, kappa, beta, Td  
  > "Our estimates were made by applying the equations in (cite: caseyPhysicalCharacterizationUnlensed2019)" (3.4 Dust mass) [from (cite: caseyPhysicalCharacterizationUnlensed2019); (cite: scovilleISMMassesStar2016)]
- Gas-to-dust ratio calibration gamma=0.85, delta(Zsun)=100  
  > "We adopted the calibration used in (cite: tacconiPHIBSSUnifiedScaling2018), where $\gamma = 0.85$" (3.5.2) [from (cite: tacconiPHIBSSUnifiedScaling2018)]
- Uncertainty estimation with ESSENCE  
  > "uncertainties were calculated using the ESSENCE code presented in (cite: tsukuiEstimatingStatisticalUncertainty2023)" (3.1) [from (cite: tsukuiEstimatingStatisticalUncertainty2023)]

### Not stated but needed to reproduce (our reading)

- Cell size and image size for cubes and MFS images
- Line-free channels / continuum selection for MFS in bands 3-4
- Exact apertures and regions for flux extraction
- CIGALE module parameter grids (only on Zenodo)
- Velocity ranges collapsed for moment maps for each arc
- Functional form and fit parameters of r31 and r41 vs Sigma_SFR
- Which CASA version applies to which project
- Flux calibrators and flux-scale uncertainty

## Analysis recipe

1. **Image cubes and continuum**: CASA cubes (30 km/s) and MFS continuum, Hogbom, natural weighting, 3-sigma clean  
  > "We applied a Hogbom deconvolution algorithm and a natural weighting." (2.2 ACA data)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure CO fluxes and continuum fluxes**: Moment-0 maps; peak for unresolved, aperture photometry for resolved with ESSENCE uncertainties; detection above 2 sigma  
  > "For unresolved sources, the emission was determined as the peak value, with the images’ root mean square (rms) serving as its uncertainty." (3.1)
   - software: ESSENCE
   - fitting: _not stated_
   - validation: _not stated_
3. **Lens magnification**: LENSTOOL models; mean magnification in aperture from 100 MCMC realizations; new PIEMD+shear model for J1429  
  > "we used the median of the 100 samples as the nominal value and we adopted $\sigma_{\mu}\equiv(p_{84} - p_{16})/2$ as the uncertainty" (2.3.3)
   - software: LENSTOOL
   - fitting: LENSTOOL MCMC, seven free parameters  
  > "We then optimized the seven free parameters of the model using LENSTOOL’s Markov Chain Monte Carlo (MCMC) sampling." (2.3.3)
   - validation: _not stated_
4. **SED fitting for stellar mass, SFR, Sigma_SFR**: CIGALE with delayed SFH, BC03, nebular emission, Charlot & Fall attenuation, Dale 2014 dust; HST+JWST+ACA photometry  
  > "we adopted a delayed SF history and used the (cite: bruzualStellarPopulationSynthesis2003) simple stellar population model." (3.3)
   - software: CIGALE
   - assumption: Chabrier IMF; flat LCDM Om=0.3, OL=0.7  
  > "Additionally, we adopted the initial mass function (IMF) derived by (cite: chabrierGalacticStellarSubstellar2003)." (1 Introduction)
   - fitting: _not stated_
   - validation: _not stated_
5. **Dust masses**: Casey 2019/Scoville RJ-corrected optically thin equation  
  > "where $\kappa$=1.3$\rm{cm}^2 \rm{g}^{-1}$ represents the dust-mass absorption coefficient, $\beta$=1.8 denotes the emissivity spectral index, and $T_d$=25K" (3.4)
   - assumption: kappa=1.3 cm2/g, beta=1.8, Td=25 K  
  > "$\kappa$=1.3$\rm{cm}^2 \rm{g}^{-1}$ represents the dust-mass absorption coefficient, $\beta$=1.8" (3.4)
   - fitting: _not stated_
   - validation: _not stated_
6. **Stacking**: Single-pixel spectra and continuum stacked with 1/sigma^2 weights after magnification correction; significance threshold 1.5 sigma  
  > "we observed that the signal-to-noise ratio was optimized when galaxies were weighted by $1/\sigma^2$" (3.5 Stacking)
   - fitting: _not stated_
   - validation: _not stated_
7. **Molecular gas mass from CO**: M_mol = alpha_CO L'CO(1-0) with Genzel 2015 model (a); r_J1 from Sigma_SFR relations fitted to compiled data  
  > "we selected the first model (a) proposed in (cite: genzelCombinedCODust2015)." (3.6.1)
   - assumption: alpha_CO depends on metallicity (Genzel 2015)  
  > "As we are working with subsolar metallicities, we decided to employ an $\alpha_{\rm{CO}}$ model that accounts for the photo-dissociation of molecular gas in these types of galaxies" (Molecular gas mass using CO emissions)
   - fitting: relations fitted to compiled r31, r41 data; r51 from Narayanan 2014  
  > "We fitted a model to the observational data sets for J= 3,4 and derived relations between both ${r}_{\rm{31}}$ and ${r}_{\rm{41}}$ and $\Sigma_{\rm{SFR}}$" (3.6.1)
   - validation: Compared to dust-based masses  
  > "This CO-based approach is also generally consistent with the dust mass method at 870$\mu$m/1.25mm (bands 6 and 7)." (3.6.3)
8. **Molecular gas mass from dust**: Gas-to-dust ratio delta_GDR = 100 (Z/Zsun)^-0.85  
  > "$$\begin{equation}
    \label{dust_to_mass}
    \delta_{\rm{GDR}} = 100 \left (  \frac{Z}{Z_\odot} \right )^{-0.85}" (3.6.2)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 6.2.1.7 and 6.4.1.12: Calibration and imaging  
  > "The data were processed into spectral cubes and multi-frequency synthesis (MFS) images using CASA." (2.2 ACA data)
- **CIGALE** : SED fitting  
  > "we employed the Code Investigating GALaxy Emission (CIGALE; (cite: boquienCIGALEPythonCode2019)) to perform SED fitting." (3.3)
- **LENSTOOL** : Lens modelling and magnification  
  > "We estimated magnification factors using parametric lens models constructed with the LENSTOOL software" (2.3.3)
- **ESSENCE** : Flux uncertainties via autocorrelation  
  > "This code estimates uncertainties using the autocorrelation function between pixels." (3.1)
- **AstroDrizzle** : Combining HAP exposures for Sunburst  
  > "the individual HAP exposures were combined using the AstroDrizzle package" (2.3.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| J0033 CO(4-3) integrated flux (magnified) | 2.0 | 0.1 | Jy km/s | 2 | / J0033 / (4-3) / 2.0$\pm$0.1 / 3.4$\pm$0.2 / |
| J0033 Mmol from CO | 10 | 3 | 1e9 Msun | 7 | / J0033 / 4.42$\pm$0.08 / \- / 0.60$\pm$0.5 / \- / 10$\pm$3 / 23$^{+7} _{-6}$ / |
| CO all arcs stack integrated flux | 1.3 | 0.6 | mJy km/s | 6 | CO all arcs&1.3$\pm$0.6&-&2.68 &2.0$\pm$0.9 & 9.6,0.09 & 0.96,0.07 |
| Continuum B6/7 all arcs stack flux | 4.9 | 0.9 | microJy | 6 | Continuum B6/7 all arcs&-& 4.9$\pm$0.9&2.96& 22$\pm$4 & 9.6, 0.1& 1.0,0.1 |
| CO-to-dust molecular mass ratio (atomic fraction) | 9% (91% atomic) | not stated | percent | 8 | the molecular mass estimated with CO was only 9% of the molecular mass obtained with the dust mass, which means that possibly 91% of the gas is in atomic form. |

## Qualitative findings

- CO detected in 3 of 12 arcs and dust continuum in 3 others  
  > "We detected CO emission in 3 of the 12 arcs and dust continuum emission in another 3." (abstract)

## Claim tuples

- H: Low-mass lensed SFGs at z~2 show a molecular gas deficit relative to scaling relations | E: ACA CO and dust measurements compared with PHIBSS scaling relations | R: Most galaxies have lower gas fractions and shorter depletion times | F: Gas deficit present for M*<10^10.7 | **supported**
- H: The deficit is due to atomic gas/CO-dark gas | E: Compare CO and dust-based gas masses in stacks; [CII] for J1226 | R: CO is 9% of dust-based mass | F: ~91% atomic, an upper limit given possible CO-dark gas | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Genzel 2015 alpha_CO chosen for metallicity dependence and consistency with scaling relations derived with Tacconi 2018  
  > "as all the scaling relations we used to compare our data were derived using the (cite: tacconiPHIBSSUnifiedScaling2018) model, a similar model was considered more adequate." (3.6.1)
- Alternative: Madden 2020 and Accurso 2017 alpha_CO models considered; not adopted  
  > "However, the (cite: maddenTracingTotalMolecular2020) model was not chosen as its values were suggested by (cite: ramambasonModelingMolecularGas2024) to be upper limits" (4.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Scatter in r31 and r41 relations adds systematic errors  
  > "both derived relations present significant scatter, which incorporates systematic errors into our molecular gas estimations." (3.6.1)
- Caveat (inferred, ours): Gas deficit depends strongly on alpha_CO choice (up to ~1 dex)
- Caveat (inferred, ours): Low-significance stacks (1.5 sigma) support the 91% atomic claim
- Caveat (inferred, ours): Dust Td=25 K fixed despite low metallicity
- Caveat (inferred, ours): Large ACA beams may blend arcs

## Reproducibility

- Data public (paper): Additional data on Zenodo  
  > "can be found in Zenodo at the link <https://zenodo.org/records/14045715>." (Data Availability)
- Products in archive: _not stated_
- Missing: Imaging cell/image sizes
- Missing: CIGALE parameter grids (Zenodo only)
- Missing: Fit forms of r_J1 relations
- Data volume (inferred): ~10-50 GB (three ACA projects, 12 targets)
- Score (inferred): 3/5, Public ACA data and mostly described workflow, but several imaging and fitting details are missing.
- Rediscovery candidate: no, Key results depend on SED fits, lens models and literature relations that are not fully specified.

## Links

- Method: (cite: tsukuiEstimatingStatisticalUncertainty2023) (ESSENCE uncertainty estimation)
- Method: (cite: genzelCombinedCODust2015) (alpha_CO model)
- Companion: (cite: solimanoMolecularGasBudget2021) (Earlier study of four of the arcs)
- Related: SDSS Giant Arcs Survey
- Related: TEMPLATES
- Related: PHIBSS

## Checks

```json
{
 "quotes": 65,
 "quotes_ok": 65,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2021.1.01337.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 89,
  "stated": 49,
  "rate": 0.551
 },
 "evidence_ok": true
}
```

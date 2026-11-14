# Automated Mining of the ALMA Archive in the COSMOS Field (A<SUP>3</SUP>COSMOS). II. Cold Molecular Gas Evolution out to Redshift 6

`2019ApJ...887..235L` | The Astrophysical Journal 2019 | first author: Liu, Daizhong | arXiv: 1910.12883 | DOI: 10.3847/1538-4357/ab578d

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies, nearby_galaxies
- Question: How do the molecular gas depletion time and gas-to-stellar-mass ratio of galaxies depend on stellar mass, offset from the main sequence and cosmic age out to z~6, and what cosmic molecular gas density evolution follows?  
  > "we parameterize galaxies’ molecular gas depletion time ($\tau_{\mathrm{depl}}$) and molecular gas to stellar mass ratio ($\mu_{\mathrm{molgas}}$) each as a function of the stellar mass ($M_{\star}$), offset from the star-forming main sequence ($\Delta{\mathrm{MS}}$) and cosmic age (or redshift)." (abstract)
- Target **A3COSMOS galaxy sample in the COSMOS field**: coordinates _not stated_; z/distance 0.29–5.667 (spectroscopic or photometric)  
  > "a large ($\sim700$), robust galaxy sample at $0.3 < z \lesssim 6$ in the 2 deg$^2$ COSMOS field (cite: Scoville2007) from the A$^3$COSMOS project" (1 Introduction); distance from COSMOS spec-z compilation, Laigle2016/Davidzon2017 and Jin2018 photo-z  
  > "a large ($\sim700$), robust galaxy sample at $0.3 < z \lesssim 6$ in the 2 deg$^2$ COSMOS field (cite: Scoville2007) from the A$^3$COSMOS project" (1 Introduction)

## Data provenance

- ALMA projects: _none stated_
- bands: Mostly ALMA Band 6 and 7 (all public archival bands used)  
  > "Our high-redshift galaxies are most commonly observed in ALMA Band 6 and 7" (3.2.1 Band conversion)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Data with beam size < 0.1'' discarded  
  > "discarded very high resolution (beam size $< 0.1''$) data" (2.1 The A3COSMOS Galaxy Sample)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Public ALMA archival data, release date up to Aug. 1st, 2018  
  > "All A$^3$COSMOS galaxies have robust (sub-)mm continuum detections from public ALMA archival data (release date up to Aug. 1st, 2018)" (1 Introduction)
- Other facility **CO-observed literature samples (PHIBSS, xCOLD GASS, etc.)**: 20 complementary samples of CO-detected galaxies at 0<z<4 for combined fitting  
  > "We include 20 samples of galaxies with CO observations and well-constrained stellar mass and SFR properties from the literature" (2.2 Complementary Local-to-High-Redshift Galaxy Samples)
- External data: A3COSMOS catalog (continuum photometry, MAGPHYS M*, L_IR, Mdust) from the companion paper  
  > "Galaxy properties in the A$^3$COSMOS galaxy catalog, including stellar mass ($M_{\star}$), IR luminosity ($L_{\mathrm{IR}}$) and dust mass ($M_{\mathrm{dust}}$), are obtained from MAGPHYS" (2.1 The A3COSMOS Galaxy Sample) [from Liu et al. 2019 (cite: Liudz2019)]
- External data: RJ-tail calibration alpha_850 luminosity-dependent  
  > "we will adopt the three calibrations from , (cite: Hughes2017) and (cite: Groves2015)" (3.2 Molecular Gas Mass from RJ-tail Dust Continuum) [from (cite: Hughes2017)]
- External data: Main sequence function, #49 fit of Table 7 (cosmic age)  
  > "we adopt the MS function from the #49 fitting of Table 7 of (cite: Speagle2014)" (5 Fitting) [from (cite: Speagle2014)]
- External data: SIDES mock galaxy catalog  
  > "The “SIDES” simulation (cite: Bethermin2017Model) generated 1,489,629 mock galaxies within a 2 deg$^2$ lightcone" (7.3) [from (cite: Bethermin2017Model)]
- Simulation/model as data: SIDES mock catalog used to integrate molecular gas density with log M*>9 star-forming galaxies  
  > "We use the SIDES mock galaxy catalog and select $\log_{10}M_{\star}>9.0$ star-forming galaxies" (7.3)

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

- Continuum imaging, photometry extraction, flux bias correction, SED fitting and catalog flags  
  > "We developed pipelines for producing continuum images using nearly all publicly available ALMA archival data in COSMOS" (2.1) [from paper I (cite: Liudz2019)]
- Metallicity-dependent alpha_CO for complementary samples  
  > "we recalculated all molecular gas masses from the CO line luminosities by applying the metallicity-dependent $\alpha_{\mathrm{CO}}$ following ." (2.2) [from Accurso2017/Genzel2015 as cited in text]

### Not stated but needed to reproduce (our reading)

- Exact catalog entries (A3COSMOS v20180801) with MAGPHYS outputs must be obtained from paper I
- Priors and sampler settings in pymc3 beyond the (-10,10) coefficient range, and how uncertainties/weights enter the chi2
- ALMA project codes not printed in text
- Exact uncertainties used for gas masses in fitting
- Details of the Genzel2015 alpha_CO-metallicity relation used

## Analysis recipe

1. **Select robust A3COSMOS sample**: Apply S/N cuts (5.40 blind, 4.35 prior) and remove flagged sources (inconsistent flux, outlier CPA, outlier SED)  
  > "a peak flux to rms noise ratio of 5.40 for blind extraction and 4.35 for prior photometry" (2.1)
   - fitting: _not stated_
   - validation: Monte Carlo simulations in paper I; spurious fraction near zero  
  > "the spurious fraction is reduced to close to zero according to our statistics in paper" (2.1)
2. **Compute gas masses via band conversion and RJ-tail calibration**: Scale ALMA flux by MAGPHYS SED ratio Gamma to rest-frame 850 um, compute luminosity, divide by Hughes2017 alpha_850; compare with dust-SED delta_GDR and Groves2015 methods  
  > "then we scale the observed ALMA flux density by $\Gamma^{\mathrm{SED}}$ and compute the luminosity" (3.2.1)
   - software: MAGPHYS
   - assumption: Gas mass purely molecular, atomic gas ignored; metallicity from modified Genzel2015 MZR; delta_GDR from Remy-Ruyer2014  
  > "we obtain the dust-SED-based $M_{\mathrm{mol\,gas}}$ by multiplying $M_{\mathrm{dust}}$ with the mass–metallicity-derived $\delta_{\mathrm{GDR}}$ and ignore the contribution from atomic gas" (3.1)
   - fitting: _not stated_
   - validation: Band conversion bias tested with JINGLE galaxies  
  > "we have done some tests using the multi-wavelength data from UV to submm for the JINGLE survey galaxy sample" (Appendix 10)
3. **Fit functional forms for tau_depl and mu_molgas**: Multivariate fit of log tau_depl and log mu_molgas versus DeltaMS, log M*, cosmic age to combined 1663-galaxy sample; also re-fit Scoville2017 and Tacconi2018 forms  
  > "We use the `Python` packages `pymc3` and `scipy.optimize.curve_fit` for the fitting" (5)
   - software: pymc3, scipy.optimize.curve_fit, corner
   - parameter: Coefficients allowed in range (-10,10)  
  > "In the fitting we allow the coefficients to vary within a relatively large range of $(-10,10)$." (Appendix 11)
   - assumption: Speagle2014 MS with cosmic age used for DeltaMS  
  > "Here we adopt the MS function from the #49 fitting of Table 7 of (cite: Speagle2014)" (5)
   - fitting: MCMC (pymc3) and least-squares (curve_fit), agree well  
  > "The two algorithms agree very well, and the former one provides better uncertainty estimates for the fitted parameters." (5)
   - validation: chi2 comparison; subsample tests without z>4 and without z>1 CO; alternative gas calibrations  
  > "we tested the stability of our fitting for subsamples of galaxies: (a) only $z<4$ data, and (b) without $z>1$ CO" (5)
4. **Derive cosmic molecular gas mass density**: Sum SMF x M* x mu_molgas for MS galaxies (M*>1e9), and alternative sum over SIDES mock galaxies  
  > "we integrate only down to $M_{\star}=10^{9.0}\;\mathrm{M}_{\odot}$" (7.2)
   - assumption: SMFs adapted from Peng2010/Davidzon2017 shapes normalized to integrated CSFRD  
  > "we adopt the shape of our SMF from an interpolation of the (cite: Davidzon2017) SMFs" (Appendix 12)
   - fitting: _not stated_
   - validation: Compared to CO blind surveys and SAM of Popping2019  
  > "At higher redshifts ($z>0.5$) our curve coincidentally agrees with the Semi-Analytic Model (SAM) simulation by (cite: Popping2019)." (7.3)

## Software

- **MAGPHYS** : SED fitting for M*, L_IR, Mdust and band conversion  
  > "are obtained from MAGPHYS ((cite: daCunha2008; daCunha2015)) SED fitting" (2.1)
- **FAST** : independent stellar mass check  
  > "with the FAST ((cite: Kriek2009)) and “SUPER-DEBLENDED” ((cite: Liudz2017; Jin2018)) SED fitting tools" (2.1)
- **pymc3** : MCMC fitting of functional forms  
  > "The former package performs Markov chain Monte Carlo (MCMC) fitting to calculate the probability distribution of the fitting" (5)
- **scipy.optimize.curve_fit** : least-squares fitting  
  > "the latter one performs least-chi-square minimization to find the best fit" (5)
- **corner** : posterior probability plots  
  > "as automatically determined by the `Python` package `corner`" (Appendix 11)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| log tau_depl coefficient a | -0.5724 | not stated | dimensionless | 3 | a  = -0.5724, \ \mathsf{b}  = -0.5174 |
| log mu_molgas coefficient a | +0.4195 | not stated | dimensionless | 3 | a  = +0.4195, \ \mathsf{b}  = -0.6906 |
| reduced chi2 for mu_molgas, this work's form | 0.86 | not stated | dimensionless | 3 | 1663  / 1426.98  / 0.86 |
| Total sample with gas measurements | 1,663 | not stated | galaxies | 0 | In total, we have 1,663 galaxies with redshift, SFR, stellar mass and molecular gas mass measurements. |
| Local tau_depl predictions for M*=3e9, 3e10, 3e11, 3e12 | 0.7, 1.3, 2.6, 5.0 | not stated | Gyr | 3 | their $\tau_{\mathrm{depl}}=0.7$, 1.3, 2.6 and 5.0 Gyr, respectively |
| Band conversion under-prediction at z>4 | factor 2–6 | not stated | dimensionless | 2 | our SED fitting tends to underestimate their true R-J tail dust continuum by a factor of 2–6 |

## Qualitative findings

- Functional form implies downsizing and mass-quenching  
  > "implies a “downsizing” effect (i.e., more-massive galaxies evolve earlier than less-massive ones) and “mass-quenching”" (abstract)

## Claim tuples

- H: Does a new functional form fit gas fraction and depletion time better than Tacconi2018 and Scoville2017 forms? | E: Fit three forms to the combined 1663-galaxy sample | R: Reduced chi2 0.86 vs 0.87 (re-fit Tacconi) and 1.26 (re-fit Scoville); original-literature fits worse | F: The new form is statistically better | **supported**
- H: Does the gas fraction function reproduce the cosmic molecular gas density to z=6? | E: Integrate SMF x mu_molgas and SIDES mock galaxies | R: Agrees with CO blind surveys' upper bounds and SAM of Popping2019 | F: Coherent picture of gas, SFR and stellar mass evolution | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Lowering S/N threshold to 3.0 doubles sample but 40% spurious  
  > "however 40% of the sample will be spurious based on our simulation statistics" (2.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Band conversion underestimates RJ-tail flux at z>4 lacking long-wavelength data  
  > "it potentially results in a factor of 2–6 underestimation of gas mass at $z>4$" (8 Summary)
- Caveat (inferred, ours): Heterogeneous sample, with dust-based gas masses at high z and CO at low z, confounds redshift evolution
- Caveat (inferred, ours): Atomic gas ignored and metallicity inferred from relations
- Caveat (inferred, ours): MAGPHYS stellar masses 0.25 dex above FAST

## Reproducibility

- Data public (paper): Public ALMA archival data  
  > "All A$^3$COSMOS galaxies have robust (sub-)mm continuum detections from public ALMA archival data" (1)
- Products in archive: _not stated_
- Code: Python package for calculating the functions via ASCL  
  > "We also provide a `Python` package for the calculation with our functions: <https://ascl.net/code/v/2377>." (Footnote 5)
- Missing: Full catalog from paper I and complementary-sample tables
- Missing: pymc3 sampler configuration
- Missing: ALMA project code list in text
- Data volume (inferred): Large for full re-processing (~50 archival projects), but catalog-level analysis needs only small tables
- Score (inferred): 3/5, Fitting uses a public catalog and well-specified functional forms, but the ALMA processing is deferred to paper I and sample compilation is complex.
- Rediscovery candidate: no, Requires the paper I catalog and many literature tables; recipe is only partly specified.

## Links

- Method: Liu et al. 2019 (cite: Liudz2019) (A3COSMOS imaging pipeline, photometry, catalog)
- Companion: (cite: Liudz2019) (Paper I of A3COSMOS)
- Related: A3COSMOS
- Related: PHIBSS
- Related: ASPECS
- Related: COLDz
- Related: xCOLD GASS
- Related: JINGLE

## Checks

```json
{
 "quotes": 46,
 "quotes_ok": 46,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00064.S",
  "2011.0.00097.S",
  "2011.0.00539.S",
  "2011.0.00742.S",
  "2012.1.00076.S",
  "2012.1.00323.S",
  "2012.1.00523.S",
  "2012.1.00536.S",
  "2012.1.00919.S",
  "2012.1.00952.S",
  "2012.1.00978.S",
  "2013.1.00034.S",
  "2013.1.00092.S",
  "2013.1.00118.S",
  "2013.1.00151.S",
  "2013.1.00171.S",
  "2013.1.00208.S",
  "2013.1.00276.S",
  "2013.1.00668.S",
  "2013.1.00815.S",
  "2013.1.00884.S",
  "2013.1.00914.S",
  "2013.1.01258.S",
  "2013.1.01292.S",
  "2015.1.00026.S",
  "2015.1.00055.S",
  "2015.1.00122.S",
  "2015.1.00137.S",
  "2015.1.00260.S",
  "2015.1.00299.S",
  "2015.1.00379.S",
  "2015.1.00388.S",
  "2015.1.00540.S",
  "2015.1.00568.S",
  "2015.1.00664.S",
  "2015.1.00704.S",
  "2015.1.00853.S",
  "2015.1.00861.S",
  "2015.1.00862.S",
  "2015.1.00928.S",
  "2015.1.01074.S",
  "2015.1.01105.S",
  "2015.1.01111.S",
  "2015.1.01171.S",
  "2015.1.01212.S",
  "2015.1.01495.S",
  "2015.1.01590.S",
  "2015.A.00026.S",
  "2016.1.00478.S",
  "2016.1.00624.S",
  "2016.1.00735.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 37,
  "rate": 0.487
 },
 "evidence_ok": true
}
```

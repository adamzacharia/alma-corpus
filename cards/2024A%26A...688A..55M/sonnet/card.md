# A<SUP>3</SUP>COSMOS: Measuring the cosmic dust-attenuated star formation rate density at 4 &lt; z &lt; 5

`2024A&A...688A..55M` | Astronomy and Astrophysics 2024 | first author: Magnelli, Benjamin | arXiv: 2405.18086 | DOI: 10.1051/0004-6361/202450081

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies
- Question: What are the mean dust-attenuated properties (L_IR, SFR_IR, IRX relations) of mass-complete star-forming galaxies at 4<z<5, and what is the dust-attenuated cosmic SFRD?  
  > "we need to accurately measure the mean dust-attenuated properties of star-forming galaxies (SFGs) at $4<z<5$ and therefore constrain the cosmic dust-attenuated star formation rate density (SFRD)" (abstract)
- Target **COSMOS2020 mass-complete SFGs at 4<z<5 (440 with ALMA coverage)**: coordinates COSMOS field centre RA 10h00m28.6s, Dec +02d12m21.0s  
  > "COSMOS (R.A. = 10$^{\rm h}$00$^{\rm m}$28.6$^{\rm s}$, Dec. = +02$\ensuremath{^\circ}$12$\ensuremath{'}$21.0$\ensuremath{''}$)" (2 Data); "These photometric redshift and stellar mass estimates were obtained by fitting with `LePhare` the FARMER photometry in 30 bands from UV to near-infrared." (3 Sample); z/distance 4<z<5 (photometric)  
  > "COSMOS (R.A. = 10$^{\rm h}$00$^{\rm m}$28.6$^{\rm s}$, Dec. = +02$\ensuremath{^\circ}$12$\ensuremath{'}$21.0$\ensuremath{''}$)" (2 Data); "These photometric redshift and stellar mass estimates were obtained by fitting with `LePhare` the FARMER photometry in 30 bands from UV to near-infrared." (3 Sample); distance from LePhare photo-z (LP_zPDF) from COSMOS2020 FARMER catalog  
  > "COSMOS (R.A. = 10$^{\rm h}$00$^{\rm m}$28.6$^{\rm s}$, Dec. = +02$\ensuremath{^\circ}$12$\ensuremath{'}$21.0$\ensuremath{''}$)" (2 Data); "These photometric redshift and stellar mass estimates were obtained by fitting with `LePhare` the FARMER photometry in 30 bands from UV to near-infrared." (3 Sample)

## Data provenance

- ALMA projects: _none stated_
- bands: ALMA Band 6 and 7 archival  
  > "We used all archival ALMA band 6 and band 7 observations publicly available in COSMOS" (2 Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.5''-1'' in stacked measurement sets  
  > "at the angular resolution of our stacked measurement set (i.e., $\sim0.5\ensuremath{''}-1\ensuremath{''}$)" (4.1 Methods)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: archival data public as of September 1, 2022; cycles >=3 only  
  > "as of September 1, 2022" (2 Data); "We limited our analysis to projects from cycles $\ge3$" (2 Data)
- pi or archival as stated: Archival, assembled by A3COSMOS: 87 projects (53 band 6, 34 band 7), 2100 images  
  > "Our final database contains 87 ALMA projects (53 in band 6 and 34 in band 7), and has a total of 2100 images" (2 Data)
- Other facility **COSMOS2020 catalog (UltraVISTA DR4, Subaru, Spitzer-IRAC etc.)**: Sample selection, photo-z, stellar masses, L_UV, beta_UV  
  > "we used the FARMER COSMOS2020 catalog, which is the areal union of the deep near-infrared UltraVISTA DR4 imaging and the Subaru Suprime-Cam intermediate bands PDR2" (3 Sample)
- External data: Stellar mass function of SFGs at z~4.5 (fit with Schechter plus power law)  
  > "we display the SMF of SFGs used in our analysis and inferred in (cite: Weaver.2023)" (4.3 The cosmic SFRD) [from (cite: Weaver.2023)]
- External data: L_IR-to-L150 conversion factor (3.80±0.63)e-21  
  > "following (cite: Khusanova.2021)" (4.1 Methods) [from (cite: Khusanova.2021)]
- External data: Main sequence SFR-M* relation used as fiducial baseline  
  > "The measurements including the ALMA primary targets lie almost perfectly on the MS of (cite: Schreiber.2015)." (4.2 The SFR–$M_\ast$ relation) [from (cite: Schreiber.2015)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Calibrated visibilities from the A3COSMOS database  
  > "to provide calibrated visibilities, cleaned images, and value-added source catalogs" (2 Data)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean on stacked measurement set  
  > "The cleaned image was generated from the stacked measurement set with the CASA task `tclean`, using natural weighting and cleaning the image down to $3\sigma$." (4.1 Methods)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "using natural weighting and cleaning the image down to $3\sigma$" (4.1 Methods)
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

- uv-domain stacking approach, details in their Sects. 3.1 and 3.2  
  > "we followed the same approach as (cite: Wang.2022). Details regarding these steps can be found in their Sects. 3.1 and 3.2." (4.1 Methods) [from (cite: Wang.2022)]
- Sample selection identical to the Weaver et al. SMF sample  
  > "This mass-complete sample, identical to that used in (cite: Weaver.2023) to build the stellar mass function at $z\sim4.5$, contains 5,810 galaxies." (3 Sample) [from (cite: Weaver.2023)]
- L_IR from L150 conversion  
  > "were converted into mean IR luminosities, $\langle L_{\rm IR}\,[8-1000\,\mu\rm{m}]\rangle$, following (cite: Khusanova.2021)" (4.1 Methods) [from (cite: Khusanova.2021)]

### Not stated but needed to reproduce (our reading)

- Which individual A3COSMOS measurement sets and fields were used (the paper prints no project codes)
- CASA version
- Image size, cell size, and tclean mask details
- Exact weighting scheme for stacked visibilities beyond visibility counts
- Parameters of the Schechter+power-law SMF fit and Monte Carlo setup
- Details of the linear fit of IRX–M* and priors
- How MS and IRX–M* uncertainties were propagated numerically

## Analysis recipe

1. **Build mass-complete SFG sample**: Select NUV-r-J star-forming galaxies at 4<z<5 from FARMER COSMOS2020, M*>10^9.5, remove AGN, cross-match with A3COSMOS coverage (PB>0.2)  
  > "This reduces our sample to 440 galaxies" (3 Sample)
   - software: LePhare
   - parameter: m_IRAC3.6<26 AB, chi2_red<10, Δz/(1+z)<0.1  
  > "($m_{\rm IRAC3.6}<26\,$AB and $\chi^{2}_{\rm reduced} < 10$) and accurate photometric redshifts ($\Delta z/(1+z) <0.1$)" (3 Sample)
   - fitting: _not stated_
   - validation: KS test shows ALMA-covered sample is indistinguishable from the parent sample  
  > "distributions that are indistinguishable (Kolmogorov-Smirnov test) from those of their parent sample of 5,810 galaxies" (3 Sample)
2. **Stack ALMA visibilities in uv domain**: Rescale visibility amplitudes to rest-frame 150 um luminosity with SED template, shift phase centres to galaxy positions, concat per stellar mass bin, tclean, read central pixel  
  > "Finally, we measured the stacked $L_{\rm 150}^{\rm rest}$ (i.e., $\langle L_{\rm 150}^{\rm rest}\rangle$) using the central pixel value" (4.1 Methods)
   - software: CASA, STACKER
   - parameter: SED template of Bethermin et al. 2017; gencal and applycal; three mass bins  
  > "by using the redshift of the source, the SED template of (cite: Bethermin.2017) and the CASA tasks `gencal` and `applycal`" (4.1 Methods)
   - fitting: 2D Gaussian fits as cross-check  
  > "using instead 2D Gaussian fits at the phase center of the stacked images gave consistent $\langle L_{\rm 150}^{\rm rest}\rangle$ measurements" (4.1 Methods)
   - validation: Bootstrap, 100 realizations with replacement  
  > "we made 100 realizations of the stacking analysis, using for each realization a different sample, drawn from the original one" (4.1 Methods)
3. **Convert to L_IR and SFR_IR**: Linear conversions from L150 to L_IR and then SFR_IR  
  > "\frac{\langle{\rm SFR}_{\rm IR}\rangle}{M_\odot\,{\rm yr^{-1}}} = 1\times10^{-10}\times\frac{\langle L_{\rm IR}\rangle}{L_\odot}" (4.1 Methods)
   - assumption: Chabrier IMF; conversion corresponds approximately to modified blackbody with T_dust=41 K  
  > "It corresponds approximately to that of a modified blackbody function with a dust temperature of 41 K" (4.1 Methods)
   - fitting: _not stated_
   - validation: Template within 5% of the conversion factor  
  > "it yields a $L_{\rm IR}$-to-$L_{\rm 150}^{\rm rest}$ conversion factor that is within 5% to that of Eq." (4.1 Methods)
4. **Measure mean UV properties**: Take L_UV (1600 A) from best-fit LePhare SEDs, compute beta_UV from 1600 and 2300 A, weighted by visibility numbers, bootstrap errors; SFR_UV = 1.5e-10 L_UV  
  > "we used their rest-frame luminosities at $1600\,\r{A}$ and $2300\,\r{A}$" (4.2 Measuring L_UV)
   - software: LePhare
   - assumption: Bruzual & Charlot 2003 models, delayed SFH  
  > "assuming the (cite: Bruzual.2003) model with a delayed star formation history" (4.2 Measuring L_UV)
   - fitting: _not stated_
   - validation: Compared with photometry-based L_UV and beta_UV; ratio 1.03 for L_UV  
  > "The median and 16th and 84th percentiles of the $L_{\rm UV}^{\rm phot.}$-to-$L_{\rm UV}$ ratio is $1.03_{-0.12}^{+0.11}$" (4.2 Measuring L_UV)
5. **Fit IRX–beta, IRX–M*, SFR–M* relations**: Compare stack points with Meurer/Overzier relations; linear fit of log IRX vs log M*; fit MS normalization of Schreiber 2015  
  > "A linear fit to our data points yields the following IRX–$M_\ast$" (5.1 IRX)
   - fitting: _not stated_
   - validation: Stacks with and without ALMA primary targets (within 3'')  
  > "we therefore investigate the impact on our results of including or excluding these ALMA primary targets in our stacks" (3 Sample)
6. **Derive cosmic SFRD**: Multiply and integrate the fiducial SMF with MS and IRX–M* relations; Monte Carlo uncertainty propagation; total SFRD integrated down to 0.03 M*  
  > "by multiplying and then integrating our fiducial SMF with our fiducial MS" (4.3 The cosmic SFRD)
   - parameter: Fiducial MS = MS_S15 - 0.15 dex; fiducial IRX–M* slope 1.45, intercept 0.56  
  > "MS$_{\rm fid.}\equiv\,{\rm MS}_{\rm S15}-0.15\,$dex" (4.2 The SFR–M* relation)
   - assumption: All SFGs at a given mass lie on the MS (no starburst contribution)  
  > "by construction we have assumed that at a given mass, all SFGs are MS galaxies" (4.3 The cosmic SFRD)
   - fitting: Schechter plus power law fit to Weaver et al. 2023 SMF points at 3.5<z<4.5 and 4.5<z<5.5  
  > "with the combination of a Schechter function dominating at low stellar masses and a power-law dominating at high stellar masses" (4.3 The cosmic SFRD)
   - validation: Repeated with Schechter SMF and with JWST SMF of Weibel et al. 2024  
  > "we also tested the robustness of our calculations against the most recent JWST-derived SMF from (cite: Weibel.2024)" (4.3 The cosmic SFRD)

## Software

- **CASA** : gencal, applycal, concat, tclean for stacking  
  > "The visibilities of the galaxies in each of our stellar mass bins were then stacked together using the CASA task `concat`." (4.1 Methods)
- **STACKER** : Shifting visibility phase centres to galaxy coordinates  
  > "we then shifted the phase center of its visibilities to its coordinate using a CASA-based package, the `STACKER`" (4.1 Methods)
- **LePhare** : Photo-z, stellar mass and SED fits in COSMOS2020  
  > "these photometric redshift and stellar mass estimates were obtained by fitting with `LePhare` the FARMER photometry" (3 Sample)
- **Astropy** : Analysis software acknowledged  
  > "`Astropy` (cite: Collaboration.2022), `photutils` (cite: Bradley.2022), and `NumPy` (cite: Harris.2020)" (Acknowledgements)
- **photutils** : Analysis software acknowledged  
  > "`photutils` (cite: Bradley.2022)" (Acknowledgements)
- **NumPy** : Analysis software acknowledged  
  > "`NumPy` (cite: Harris.2020)" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| log10<SFR_IR>, 10^9.5-10 bin (all SFGs) | 1.19 | +0.14/-0.17 | log Msun/yr | 3 | / $9.5-10$              / 302        / $9.7^{+0.1}_{-0.1}$             / $4.4^{+0.1}_{-0.1}$ / $31.60^{+0.12}_{-0.16}$                          / 6          / $1.19^{+0.14}_{-0.17}$ |
| log10<SFR_IR>, 10^10.5-11.5 bin (all SFGs) | 2.74 | +0.26/-0.68 | log Msun/yr | 3 | / $10.5-11.5$           / 42         / $10.8^{+0.1}_{-0.1}$            / $4.5^{+0.1}_{-0.1}$ / $33.16^{+0.25}_{-0.68}$                          / 37         / $2.74^{+0.26}_{-0.68}$ |
| IRX–M* fit including primary targets: slope and intercept | slope 1.1, intercept 0.67 | +0.4/-0.4; +0.13/-0.14 | dimensionless | 5 | {\rm log_{10}\,IRX} = 1.1^{+0.4}_{-0.4}\times{\rm log_{10}}\,\Biggl(\,\frac{M_\ast}{10^{10}M_{\odot}}\Biggr)+0.67^{+0.13}_{-0.14} |
| Fiducial IRX–M* relation | slope 1.45, intercept 0.56 | not stated | dimensionless | 5 | {\rm log_{10}\,IRX} = 1.45\times{\rm log_{10}}\,\Biggl(\,\frac{M_\ast}{10^{10}M_{\odot}}\Biggr)+0.56 |
| SFRD_UV+IR at z~4.5 | 0.012-0.028 | range from ±0.15 dex MS | Msun/yr/Mpc^3 | 6 | We find SFRD$_{\rm UV+IR}\,=0.012-0.028\,M_\odot\,$yr$^{-1}\,$Mpc$^{-3}$ |
| SFRD_IR at z~4.5 | 0.007-0.021 | range | Msun/yr/Mpc^3 | 6 | SFRD$_{\rm IR}=0.007-0.021\,M_\odot\,$yr$^{-1}\,$Mpc$^{-3}$ |
| Dust-attenuated fraction at M*>=10^8.9 | 68 | ±10 | % | 6 | having a value of $68\pm10\%$ for $M_\ast\ge10^{8.9}\,M_\odot$ |
| Dust-attenuated fraction converged at M*=10^8 | 60 | ±10 | % | 6 | converging to a value of $60\pm10\%$ for $M_\ast\ge10^{8}\,M_\odot$ |
| Sample sizes | 5810 parent; 440 with ALMA coverage; 64 primary targets | not stated | galaxies | 1 | Of these 440 galaxies, 64 can be considered as the primary target of a given ALMA observation |

## Qualitative findings

- IRX–beta_UV at z~4.5 is consistent with local starbursts (Meurer), disfavoring SMC-like flatter relation  
  > "This distribution is overall very consistent with the local reference for starbursts from (cite: Meurer.1999)" (5.1 IRX)
- Cosmic SFRD is dominated by SFGs with M* of 10^9.5-10.5 Msun  
  > "The cosmic SFRD at $z\sim4.5$ is dominated by SFGs with a stellar mass of $10^{9.5-10.5}\,M_\odot$." (abstract)

## Claim tuples

- H: Does the IRX–beta_UV relation at z~4.5 differ from local starbursts? | E: Stack ALMA uv data of mass-complete SFGs in 3 mass bins and compare IRX and beta_UV with local relations | R: Points consistent with Meurer/Overzier; flatter SMC relation disfavored | F: Dust grain properties similar to local starbursts | **supported**
- H: Is the IRX–M* relation redshift-independent? | E: Linear fit to IRX versus M* from stacks, compare to Pannella 2015 | R: Slope 1.1 to 1.8; ~-0.5 dex in IRX at 10^9.75 | F: Steepening favored at z~4.5 | **partially**
- H: How much of the cosmic SFRD is dust attenuated at z~4.5? | E: Integrate SMF x MS x IRX–M* | R: 68±10% at 10^8.9 Msun; 60±10% at 10^8 | F: Dust-attenuated fraction remains significant | **supported**

## Reasoning

- Why this data: Bands 6 and 7 are close to dust emission peak of z~4.5 SFGs; A3COSMOS gives homogeneous archival data  
  > "they are close to the peak of the dust emission of $z\sim4.5$ SFGs and therefore provide good proxies of their infrared luminosities" (2 Data)
- Why this method: uv-domain stacking handles heterogeneous resolution; individual galaxies are mostly undetected  
  > "even though most of these galaxies are not detected individually in the ALMA archival data" (1 Introduction)
- Alternative: Photometric L_UV and beta_UV instead of SED-based; Schechter SMF and Weibel JWST SMF instead of the fiducial; both gave qualitatively unchanged results  
  > "Using a Schechter SMF instead of our fiducial SMF would not qualitatively change any of these results" (4.3 The cosmic SFRD)
- How they decided it was enough: _not stated_
- Limitation (authors): Sample may miss optically-dark heavily attenuated galaxies; ALMA primary targets bias the MS normalization  
  > "this sample may still miss part of the population of optically-dark galaxies that are heavily dust attenuated" (3 Sample)
- Caveat (inferred, ours): Mean IR luminosity depends on a single assumed SED template and conversion (41 K-like)
- Caveat (inferred, ours): Stacks without primary targets in the lowest bin have S/N of only 3
- Caveat (inferred, ours): Low-mass SFRD relies on extrapolation of MS and IRX–M* below 10^9.5 Msun
- Caveat (inferred, ours): Only three mass bins used to fit IRX–M*

## Reproducibility

- Data public (paper): Archival ALMA data public via A3COSMOS database  
  > "all archival ALMA band 6 and band 7 observations publicly available in COSMOS" (2 Data)
- Products in archive: _not stated_
- Missing: List of the 87 ALMA project codes/MSs used
- Missing: STACKER and CASA versions and tclean parameters
- Missing: SMF fit parameters
- Data volume (inferred): Several TB of calibrated visibilities (87 projects, 2100 pointings)
- Score (inferred): 3/5, Data are public and methods follow Wang et al. 2022, but project lists, software versions and SMF fit details are not given.
- Rediscovery candidate: no, Recipe relies on inherited stacking procedures and an unstated list of pointings; many stated inputs are external catalogs.

## Links

- Method: (cite: Wang.2022) (uv-domain stacking method for A3COSMOS data)
- Method: (cite: Lindroos.2015) (STACKER package)
- Method: (cite: Khusanova.2021) (L150 to L_IR conversion)
- Companion: (cite: Weaver.2023) (Same sample and SMF at z~4.5)
- Companion: (cite: Adscheid.2024) (A3COSMOS database)
- Related: A3COSMOS
- Related: COSMOS2020
- Related: ALPINE
- Related: REBELS

## Checks

```json
{
 "quotes": 68,
 "quotes_ok": 68,
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
  "2012.1.00173.S",
  "2012.1.00307.S",
  "2012.1.00323.S",
  "2012.1.00523.S",
  "2012.1.00536.S",
  "2012.1.00775.S",
  "2012.1.00869.S",
  "2012.1.00919.S",
  "2012.1.00952.S",
  "2012.1.00978.S",
  "2012.1.00983.S",
  "2013.1.00034.S",
  "2013.1.00092.S",
  "2013.1.00118.S",
  "2013.1.00139.S",
  "2013.1.00146.S",
  "2013.1.00151.S",
  "2013.1.00171.S",
  "2013.1.00205.S",
  "2013.1.00208.S",
  "2013.1.00250.S",
  "2013.1.00276.S",
  "2013.1.00470.S",
  "2013.1.00668.S",
  "2013.1.00718.S",
  "2013.1.00786.S",
  "2013.1.00815.S",
  "2013.1.00836.S",
  "2013.1.00884.S",
  "2013.1.00914.S",
  "2013.1.01258.S",
  "2013.1.01271.S",
  "2013.1.01292.S",
  "2015.1.00026.S",
  "2015.1.00039.S",
  "2015.1.00040.S",
  "2015.1.00055.S",
  "2015.1.00098.S",
  "2015.1.00122.S",
  "2015.1.00137.S",
  "2015.1.00207.S",
  "2015.1.00220.S",
  "2015.1.00228.S",
  "2015.1.00260.S",
  "2015.1.00299.S",
  "2015.1.00379.S",
  "2015.1.00388.S",
  "2015.1.00540.S",
  "2015.1.00543.S",
  "2015.1.00568.S",
  "2015.1.00664.S",
  "2015.1.00704.S",
  "2015.1.00821.S",
  "2015.1.00853.S",
  "2015.1.00861.S",
  "2015.1.00862.S",
  "2015.1.00870.S",
  "2015.1.00907.S",
  "2015.1.00928.S",
  "2015.1.00948.S",
  "2015.1.01074.S",
  "2015.1.01096.S",
  "2015.1.01105.S",
  "2015.1.01111.S",
  "2015.1.01171.S",
  "2015.1.01205.S",
  "2015.1.01212.S",
  "2015.1.01362.S",
  "2015.1.01379.S",
  "2015.1.01447.S",
  "2015.1.01495.S",
  "2015.1.01590.S",
  "2015.A.00009.S",
  "2015.A.00026.S",
  "2016.1.00012.S",
  "2016.1.00048.S",
  "2016.1.00171.S",
  "2016.1.00279.S",
  "2016.1.00324.L",
  "2016.1.00330.S",
  "2016.1.00463.S",
  "2016.1.00478.S",
  "2016.1.00534.S",
  "2016.1.00564.S",
  "2016.1.00567.S",
  "2016.1.00624.S",
  "2016.1.00646.S",
  "2016.1.00721.S",
  "2016.1.00726.S",
  "2016.1.00735.S",
  "2016.1.00778.S",
  "2016.1.00790.S",
  "2016.1.00798.S",
  "2016.1.00804.S",
  "2016.1.00932.S",
  "2016.1.00954.S",
  "2016.1.00967.S",
  "2016.1.00990.S",
  "2016.1.01001.S",
  "2016.1.01012.S",
  "2016.1.01040.S",
  "2016.1.01079.S",
  "2016.1.01155.S",
  "2016.1.01184.S",
  "2016.1.01208.S",
  "2016.1.01240.S",
  "2016.1.01355.S",
  "2016.1.01426.S",
  "2016.1.01454.S",
  "2016.1.01512.S",
  "2016.1.01546.S",
  "2016.1.01559.S",
  "2016.1.01604.S",
  "2017.1.00046.S",
  "2017.1.00127.S",
  "2017.1.00138.S",
  "2017.1.00190.S",
  "2017.1.00270.S",
  "2017.1.00300.S",
  "2017.1.00326.S",
  "2017.1.00373.S",
  "2017.1.00413.S",
  "2017.1.00428.L",
  "2017.1.00486.S",
  "2017.1.00604.S",
  "2017.1.00755.S",
  "2017.1.00856.S",
  "2017.1.00893.S",
  "2017.1.01020.S",
  "2017.1.01027.S",
  "2017.1.01099.S",
  "2017.1.01163.S",
  "2017.1.01176.S",
  "2017.1.01217.S",
  "2017.1.01259.S",
  "2017.1.01276.S",
  "2017.1.01347.S",
  "2017.1.01358.S",
  "2017.1.01359.S",
  "2017.1.01451.S",
  "2017.1.01471.S",
  "2017.1.01512.S",
  "2017.1.01618.S",
  "2017.1.01659.S",
  "2017.1.01674.S",
  "2017.1.01677.S",
  "2017.1.01713.S",
  "2017.A.00013.S",
  "2017.A.00032.S",
  "2017.A.00034.S",
  "2018.1.00081.S",
  "2018.1.00085.S",
  "2018.1.00164.S",
  "2018.1.00216.S",
  "2018.1.00222.S",
  "2018.1.00231.S",
  "2018.1.00236.S",
  "2018.1.00251.S",
  "2018.1.00329.S",
  "2018.1.00348.S",
  "2018.1.00429.S",
  "2018.1.00478.S",
  "2018.1.00543.S",
  "2018.1.00567.S",
  "2018.1.00570.S",
  "2018.1.00635.S",
  "2018.1.00681.S",
  "2018.1.00874.S",
  "2018.1.00876.S",
  "2018.1.00933.S",
  "2018.1.00938.S",
  "2018.1.00992.S",
  "2018.1.01044.S",
  "2018.1.01079.S",
  "2018.1.01128.S",
  "2018.1.01136.S",
  "2018.1.01225.S",
  "2018.1.01281.S",
  "2018.1.01359.S",
  "2018.1.01521.S",
  "2018.1.01536.S",
  "2018.1.01551.S",
  "2018.1.01594.S",
  "2018.1.01605.S",
  "2018.1.01673.S",
  "2018.1.01739.S",
  "2018.1.01824.S",
  "2018.1.01841.S",
  "2018.1.01852.S",
  "2018.1.01871.S",
  "2018.A.00022.S",
  "2018.A.00037.S",
  "2019.1.00074.S",
  "2019.1.00102.S",
  "2019.1.00151.S",
  "2019.1.00397.S",
  "2019.1.00399.S",
  "2019.1.00459.S",
  "2019.1.00477.S",
  "2019.1.00652.S",
  "2019.1.00678.S",
  "2019.1.00702.S",
  "2019.1.00909.S",
  "2019.1.00964.S",
  "2019.1.01075.S",
  "2019.1.01127.S",
  "2019.1.01142.S",
  "2019.1.01201.S",
  "2019.1.01286.S",
  "2019.1.01329.S",
  "2019.1.01491.S",
  "2019.1.01524.S",
  "2019.1.01528.S",
  "2019.1.01537.S",
  "2019.1.01600.S",
  "2019.1.01615.S",
  "2019.1.01634.L",
  "2019.1.01702.S",
  "2019.1.01722.S",
  "2019.1.01832.S",
  "2019.2.00118.S",
  "2019.2.00143.S",
  "2019.2.00246.S",
  "2019.A.00015.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 84,
  "stated": 51,
  "rate": 0.607
 },
 "evidence_ok": true
}
```

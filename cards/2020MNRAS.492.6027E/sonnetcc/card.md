# The ALMaQUEST Survey - II. What drives central starbursts at z ∼ 0?

`2020MNRAS.492.6027E` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Ellison, Sara L. | arXiv: 2001.05003 | DOI: 10.1093/mnras/staa001

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies
- Question: Are central starbursts at z~0 driven primarily by enhanced star formation efficiency or by increased gas fractions?  
  > "allow us to investigate whether central starbursts are driven primarily by enhancements in star formation efficiency (SFE) or by increased gas fractions." (abstract)
- Target **12 central starburst galaxies from ALMaQUEST (MaNGA plate-IFU IDs such as 8156-3701, 8081-3704, 8615-3703, 8081-9101)**: coordinates _not stated_; z/distance median z=0.03 for the ALMaQUEST sample; cosmology H0=70 km/s/Mpc, OmegaM=0.3, OmegaLambda=0.7  
  > "12 central starburst galaxies are selected from the ALMaQUEST sample" (2.4 Central starburst sample selection); "0.3 kpc at the median redshift of the sample, $z$=0.03" (2.2 ALMA); "Global values used in this paper, such as total stellar mass, total SFR and redshift, are taken from the PIPE3D Value Added Catalog (VAC)" (2.1 MaNGA); "We adopt a cosmology in which H$_0$=70 km/s/Mpc, $\Omega_M$=0.3, $\Omega_\Lambda$=0.7." (1 Introduction); distance from redshift from the PIPE3D Value Added Catalog (SDSS DR15)  
  > "12 central starburst galaxies are selected from the ALMaQUEST sample" (2.4 Central starburst sample selection); "0.3 kpc at the median redshift of the sample, $z$=0.03" (2.2 ALMA); "Global values used in this paper, such as total stellar mass, total SFR and redshift, are taken from the PIPE3D Value Added Catalog (VAC)" (2.1 MaNGA); "We adopt a cosmology in which H$_0$=70 km/s/Mpc, $\Omega_M$=0.3, $\Omega_\Lambda$=0.7." (1 Introduction)

## Data provenance

- ALMA projects: 2015.1.01225.S, 2017.1.01093.S, 2018.1.00558.S, 2018.1.00541.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: ALMA, compact configuration C43-2  
  > "using the C43-2 configuration between 2016 and 2019. In this compact configuration" (2.2 ALMA)
- configurations: C43-2  
  > "(PI Ellison) using the C43-2 configuration between 2016 and 2019." (2.2 ALMA)
- baselines: _not stated_
- angular resolution: beam matched to the MaNGA PSF, approximately 2.5 arcsecs  
  > "In this compact configuration, the beam size of the ALMA observations is well matched to the point spread function of MaNGA observations (approximately 2.5 arcsecs)" (2.2 ALMA)
- max recoverable scale: largest angular scale set to match the size of the MaNGA IFU  
  > "The largest angular scale of the ALMA observations is set to match the size of the MaNGA IFU." (2.2 ALMA)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: between 2016 and 2019 (Cycles 3, 5 and 6)  
  > "(PI Ellison) using the C43-2 configuration between 2016 and 2019." (2.2 ALMA); "with ALMA CO (1-0) follow-up observations obtained in Cycles 3, 5 and 6" (2.2 ALMA)
- pi or archival as stated: PI Lin (2015.1.01225.S, 2017.1.01093.S, 2018.1.00558.S) and PI Ellison (2018.1.00541.S); data taken from the ALMaQUEST survey  
  > "2018.1.00558.S (PI Lin) and 2018.1.00541.S (PI Ellison)" (2.2 ALMA); "The CO data used for the work presented here are taken from the ALMA-MaNGA QUEnching and STar formation (ALMaQUEST) survey (Lin et al. in prep)." (2.2 ALMA)
- Line: CO J=1-0 (not stated)
- Other facility **MaNGA / SDSS DR15 (PIPE3D)**: IFU maps of stellar mass surface density, emission line fluxes (Halpha, SFR, O/H) and global quantities  
  > "The MaNGA data used in this paper make use of the public PIPE3D (Sánchez et al. 2016a, 2016b) data products from the SDSS Data Release 15 (DR15)" (2.1 MaNGA)
- Other facility **NASA Sloan Atlas (NSA) catalog**: b/a axial ratios from single Sersic fits for inclination corrections  
  > "using the b/a axial ratios from single Sersic fits provided in the NASA Sloan Atlas (NSA) catalog" (2.1 MaNGA)
- Other facility **SDSS imaging**: gri images used to identify merger features  
  > "we show the SDSS $gri$ images of our central starburst sample" (2.4 Central starburst sample selection)
- External data: Global stellar mass, total SFR and redshift from the PIPE3D Value Added Catalog (DR15)  
  > "Global values used in this paper, such as total stellar mass, total SFR and redshift, are taken from the PIPE3D Value Added Catalog (VAC), provided with the DR15 release (Sánchez et al. 2018)." (2.1 MaNGA) [from Sánchez et al. 2018]
- External data: b/a axial ratios from NSA single Sersic fits  
  > "we compute inclination corrected galactocentric radii from the V-band centre of the galaxy using the b/a axial ratios from single Sersic fits provided in the NASA Sloan Atlas (NSA) catalog." (2.1 MaNGA) [from NASA Sloan Atlas (NSA) catalog]
- External data: Constant alpha_CO = 4.3 Msun pc^-2 (K km/s)^-1 adopted for CO to H2 conversion  
  > "The CO luminosities are converted to $\Sigma_{\rm H_2}$ by assuming a constant $\alpha_{CO}$ = 4.3 M$_{\odot}$ pc$^{-2}$ (K km s$^{-1}$)$^{-1}$, e.g. Bolatto et al. (2013)" (2.2 ALMA) [from Bolatto et al. (2013)]
- External data: Marino et al. O3N2 calibration used for metallicities  
  > "Metallicities are also computed by us using the extinction corrected emission line fluxes with the Marino et al. (2013) O3N2 calibration." (2.1 MaNGA) [from Marino et al. (2013)]
- External data: Milky Way extinction curve for internal extinction correction  
  > "the latter of which we correct for internal extinction assuming a Milky Way extinction curve (Cardelli, Clayton & Mathis 1989)" (2.1 MaNGA) [from Cardelli, Clayton & Mathis 1989]
- External data: Star-forming spaxel classification diagnostic  
  > "we only use MaNGA spaxels that are classified as star forming according to the Kauffmann et al. (2003) diagnostic criteria" (2.1 MaNGA) [from Kauffmann et al. (2003)]

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
- cell size: 0.5 arcsec pixels, same spatial sampling grid as MaNGA  
  > "allowing the datasets to be matched to the same spatial sampling grid of 0.5 arcsec pixels" (2.2 ALMA)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: approximately 2.5 arcsecs, matched to MaNGA PSF  
  > "the beam size of the ALMA observations is well matched to the point spread function of MaNGA observations (approximately 2.5 arcsecs)" (2.2 ALMA)
- final rms: _not stated_

### Inherited from earlier work

- ALMaQUEST sample definition and ALMA data reduction  
  > "The ALMaQUEST sample and data reduction are described in detail by Lin et al (in prep)." (2.2 ALMA) [from Lin et al (in prep)]
- Delta O/H offset metric definition  
  > "we compute an additional offset metric, $\Delta$O/H, which we have introduced previously in Ellison et al. (2018) and Thorp et al. (2019)" (4 Discussion) [from Ellison et al. (2018); Thorp et al. (2019)]
- Molecular gas main sequence used to define Delta f_H2  
  > "which forms a third dimension with the resolved SFMS and the Kennicutt-Schmidt relation (Lin et al. 2019)" (2.3 Offsets from local scaling relations) [from Lin et al. 2019]
- Selection of ALMaQUEST sample galaxies from MaNGA with ALMA CO follow-up  
  > "In brief, the sample includes both star forming and ‘green valley’ galaxies selected from the MaNGA DR14 and DR15" (2.2 ALMA) [from Lin et al (in prep)]

### Not stated but needed to reproduce (our reading)

- ALMA band, spectral setup, velocity resolution and integration times per project
- CASA version, pipeline vs manual calibration, flux calibrator and self-calibration (all deferred to Lin et al. in prep)
- CLEAN/tclean parameters: weighting, robust, deconvolver, masking, continuum subtraction, line-free channels
- How the CO moment-0 maps and their noise were made and how the S/N >= 3 per spaxel was evaluated
- How ALMA maps were convolved to the MaNGA PSF and regridded to the 0.5 arcsec MaNGA spaxel grid
- Exact conversion of CO intensity to Sigma_H2 (CO(1-0) luminosity formulation, including helium correction) and the inclination-correction formula
- Source of R_e used for R/R_e and the minimum number of control spaxels required
- Pearson r and p values for the Delta Sigma_SFR vs Delta SFE and Delta f_H2 correlations
- Criteria and classification used for identifying merger features (visual inspection of SDSS images)

## Analysis recipe

1. **Build MaNGA spaxel maps of Sigma_star, Sigma_SFR and O/H**: Use public PIPE3D DR15 products; correct line fluxes for extinction, compute Sigma_SFR from Halpha luminosity, compute O/H with the O3N2 calibration, inclination-correct radii and surface densities; keep star-forming spaxels  
  > "Metallicities are also computed by us using the extinction corrected emission line fluxes with the Marino et al. (2013) O3N2 calibration." (2.1 MaNGA); "we only use MaNGA spaxels that are classified as star forming according to the Kauffmann et al. (2003) diagnostic criteria" (2.1 MaNGA)
   - software: PIPE3D
   - parameter: Intrinsic Halpha/Hbeta = 2.85; Milky Way extinction curve  
  > "an intrinsic H$\alpha$/H$\beta$ = 2.85" (2.1 MaNGA)
   - parameter: Salpeter IMF for Sigma_SFR  
  > "assuming a Salpeter initial mass function (to be consistent with the PIPE3D products)" (2.1 MaNGA)
   - assumption: Salpeter initial mass function  
  > "assuming a Salpeter initial mass function (to be consistent with the PIPE3D products)" (2.1 MaNGA)
   - fitting: _not stated_
   - validation: _not stated_
2. **Convert ALMA CO(1-0) maps to Sigma_H2 on the MaNGA grid**: Map ALMA CO images to the MaNGA 0.5 arcsec spaxel grid, convert CO luminosity to Sigma_H2 with a constant alpha_CO, inclination-correct, and require S/N >= 3 in integrated CO flux  
  > "the analysis in this paper is performed on images mapped to the same spaxel grid as MaNGA" (2.2 ALMA); "In the analysis presented here, we require a S/N $\ge$ 3 in the integrated CO line flux" (2.2 ALMA)
   - parameter: alpha_CO = 4.3 Msun pc^-2 (K km/s)^-1  
  > "by assuming a constant $\alpha_{CO}$ = 4.3 M$_{\odot}$ pc$^{-2}$ (K km s$^{-1}$)$^{-1}$" (2.2 ALMA)
   - parameter: 15,330 spaxels pass both the MaNGA quality cuts and the CO S/N cut  
  > "There are 15,330 spaxels in the ALMaQUEST sample that fulfill both the MaNGA quality control criteria described in the previous sub-section and the CO S/N cut." (2.2 ALMA)
   - assumption: Fixed Milky Way-like alpha_CO for all spaxels, likely an over-estimate in starbursts and at small radii  
  > "Although the analysis in the following sections uses only a fixed $\alpha_{CO}$" (2.3 Offsets from local scaling relations)
   - fitting: _not stated_
   - validation: Effect of a lower alpha_CO discussed qualitatively and by a factor-of-two illustration, not applied  
  > "Whilst we do not attempt to estimate corrected conversion factors for individual spaxels" (3.1 Results from spatially averaged profiles)
3. **Compute Delta Sigma_SFR offsets from the resolved SFMS with control spaxels**: Offset in log Sigma_SFR from the median of control spaxels drawn from all star-forming DR15 spaxels, matched in Sigma_star, total stellar mass and R/Re  
  > "all of which are computed in log space relative to the median of their control spaxels" (2.3 Offsets from local scaling relations); "is drawn from the rSFMS reference sample, matched within 0.1 dex in $\Sigma_{\star}$, 0.1 dex in total stellar mass (of the host galaxy) and 0.1 in $R/R_e$" (2.3 Offsets from local scaling relations)
   - parameter: Matching tolerances: 0.1 dex in Sigma_star, 0.1 dex in total stellar mass, 0.1 in R/Re; typically several hundred controls per spaxel  
  > "with typically several hundred control spaxels identified for each spaxel" (2.3 Offsets from local scaling relations)
   - parameter: Reference set drawn from all DR15 star-forming spaxels (not ALMaQUEST), inclination b/a > 0.34  
  > "a set of reference spaxels, used to define the rSFMS, is selected from all star-forming spaxels in the DR15 (not just those in the ALMaQUEST sample)" (2.3 Offsets from local scaling relations)
   - fitting: No fit to the rSFMS; offsets from matched control medians  
  > "rather than from an established fit to the rSFMS, avoids parametric uncertainties related to fitting approaches" (2.3 Offsets from local scaling relations)
   - validation: Adding O/H to the matching changes Delta Sigma_SFR by ~0.01 dex, negligible  
  > "we tested the impact of including O/H in the matching parameters and find a systematic increase in $\Delta \Sigma_{\rm SFR}$ of $\sim$0.01 dex, which is negligible" (2.3 Offsets from local scaling relations)
4. **Select the 12 central starburst galaxies**: Azimuthally averaged Delta Sigma_SFR profiles (sliding bin of width 0.5 R/Re, centres stepped by 0.1 R/Re) inspected for median Delta Sigma_SFR within 0.5 Re above 0.2 dex  
  > "by taking median values within a sliding bin of width 0.5 $R/R_e$. The bin centres are incremented by 0.1 $R/R_e$ in each iteration." (2.4 Central starburst sample selection); "In practice, this was implemented by requiring the median $\Delta \Sigma_{\rm SFR}$ within 0.5 $R_e$ exceeds 0.2 dex." (2.4 Central starburst sample selection)
   - parameter: Median Delta Sigma_SFR within 0.5 Re > 0.2 dex (SFR elevated by at least 50 per cent)  
  > "In practice, this was implemented by requiring the median $\Delta \Sigma_{\rm SFR}$ within 0.5 $R_e$ exceeds 0.2 dex." (2.4 Central starburst sample selection)
   - fitting: _not stated_
   - validation: Definition acknowledged as somewhat subjective; authors state the conclusions are insensitive to it  
  > "Whilst this is a somewhat subjective definition of central starburst, the exact definition does not affect our conclusions." (2.4 Central starburst sample selection)
5. **Compute Delta SFE and Delta f_H2 offsets**: Delta SFE is the offset in Sigma_SFR from control spaxels matched in Sigma_H2, stellar mass, R/Re and O/H; Delta f_H2 is the offset in Sigma_H2 at fixed Sigma_star with matching in stellar mass, R/Re and O/H; controls from ALMaQUEST spaxels with normal SFR  
  > "matched within 0.1 dex in $\Sigma_{\rm H_2}$, 0.1 dex in total stellar mass (of the host galaxy), 0.1 in $R/R_e$ and 0.1 dex in O/H" (2.3 Offsets from local scaling relations); "Specifically, $\Delta f_{\rm H_2}$ is computed as the offset of $\Sigma_{\rm H_2}$ at fixed $\Sigma_{\star}$, with additional spaxel matching in total stellar mass of the host galaxy (within 0.1 dex), $R/R_e$ (within 0.1) and O/H (within 0.1 dex)." (2.3 Offsets from local scaling relations)
   - parameter: Control pool: ALMaQUEST spaxels with -0.5 < Delta Sigma_SFR < 0.5 and b/a > 0.34  
  > "spaxels from the ALMaQUEST sample with $-0.5 <$ $\Delta \Sigma_{\rm SFR}$ $<0.5$ and galaxy b/a$>0.34$" (2.3 Offsets from local scaling relations)
   - assumption: Matching in O/H and R/Re mitigates dependences of alpha_CO on metallicity and galactocentric radius  
  > "These matching criteria will mitigate dependences of $\alpha_{CO}$ on metallicity and galactocentric radius" (2.3 Offsets from local scaling relations)
   - fitting: No fit to the Kennicutt-Schmidt relation  
  > "an important characteristic of the above procedure for calculating $\Delta$SFE is that it does not rely on fitting the Kennicutt-Schmidt relation" (2.3 Offsets from local scaling relations)
   - validation: _not stated_
6. **Compare central averages and radial profiles of Delta SFE and Delta f_H2**: Median Delta f_H2 vs median Delta SFE within 0.5 Re per galaxy; azimuthally averaged Delta SFE and Delta f_H2 profiles with a sliding 0.1 R/Re bin, colour-coded by global Delta SFR; examine effect of a factor-of-two lower alpha_CO  
  > "the median $\Delta f_{\rm H_2}$ and median $\Delta$SFE within 0.5 $R_e$ for our starburst sample" (3.1 Results from spatially averaged profiles); "we again use a sliding bin of width 0.1 $R/R_e$ to generate the $\Delta$SFE and $\Delta f_{\rm H_2}$ profiles and colour code by global $\Delta$SFR" (3.1 Results from spatially averaged profiles)
   - parameter: alpha_CO reduced by a factor of two (0.3 dex) as an illustrative variation  
  > "If we again suppose that $\alpha_{CO}$ may be reduced by a factor of two (0.3 dex) in the centres of these starburst galaxies" (3.1 Results from spatially averaged profiles)
   - fitting: _not stated_
   - validation: Robustness of the SFE conclusion checked against a lower alpha_CO  
  > "We conclude that the evidence for enhanced SFEs in our starburst sample is robust to assumptions on the conversion factor." (3.1 Results from spatially averaged profiles)
7. **Spaxel-by-spaxel correlation of Delta Sigma_SFR with Delta SFE and Delta f_H2**: Correlate Delta Sigma_SFR against Delta SFE and Delta f_H2 for all 5278 spaxels in the starburst sample; compare steepness, scatter and significance with a Pearson test  
  > "for all 5278 spaxels in our starburst sample, the correlation between $\Delta \Sigma_{\rm SFR}$ and $\Delta$SFE (upper panel) and $\Delta f_{\rm H_2}$ (lower panel)" (3.2 Results from spaxel correlations); "is both steeper, tighter and more significant (based on a Pearson correlation test) than the relation with $\Delta f_{\rm H_2}$" (3.2 Results from spaxel correlations)
   - assumption: Fixed alpha_CO; a variable alpha_CO would steepen the SFE correlation and flatten the f_H2 correlation  
  > "The correlation between $\Delta \Sigma_{\rm SFR}$ and $\Delta$SFE would be even steeper for a variable conversion factor" (3.2 Results from spaxel correlations)
   - fitting: _not stated_
   - validation: _not stated_
8. **Test for metal dilution with Delta O/H**: Delta O/H is the difference of log O/H from the median of other star-forming spaxels matched in Sigma_star, R/Re and total stellar mass; examine profiles and Delta O/H vs Delta Sigma_SFR colour-coded by Delta SFE  
  > "we compute the difference of its log O/H from the median of all other star-forming spaxels matched in $\Sigma_{\star}$, $R/R_e$ and total stellar mass" (4 Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **PIPE3D** SDSS DR15 products: Public MaNGA data products: stellar mass surface densities and emission line fluxes  
  > "We also make use of the public PIPE3D stellar mass surface densities ($\Sigma_{\star}$) and line fluxes" (2.1 MaNGA)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Star-forming spaxels in the 12 central starburst galaxies | 10,765 | not stated | spaxels | 3 | There are a total of 10,765 star-forming spaxels in the 12 central starburst galaxies that comprise our sample |
| Starburst-sample spaxels with Sigma_H2 measurements (used for Delta SFE and Delta f_H2) | 5278 | not stated | spaxels | 5 | of which 5278 spaxels also have $\Sigma_{\rm H_2}$ measurements |
| ALMaQUEST spaxels passing MaNGA quality cuts and CO S/N cut | 15,330 | not stated | spaxels | 2 | There are 15,330 spaxels in the ALMaQUEST sample that fulfill both the MaNGA quality control criteria described in the previous sub-section and the CO S/N cut. |
| Star-forming spaxels in all of DR15 passing the MaNGA cuts | ~1.5 million | not stated | spaxels | 1 | There are $\sim$ 1.5 million star-forming spaxels in all of DR15 that fulfill these criteria. |
| Starburst galaxies with signs of merger features | 3 of 12 (8156-3701, 8615-3703, 8081-9101); 25 percent | not stated | galaxies | 4 | with only three (8156-3701, 8615-3703 and 8081-9101) showing signs of merger features; only a minority (25 percent) of our sample show signs of a recent interaction |
| Median central Delta Sigma_SFR of the two weakest central starbursts | ~0.2 | not stated | dex | 3 | Whilst two of the galaxies exhibit fairly modest central enhancements with median central $\Delta \Sigma_{\rm SFR}$ $\sim 0.2$ dex, the remaining 10 all show enhancesments of at least a factor of two. |
| Offset above global SFMS of the two strongest SFE outliers (8156-3701, 8081-3704) | ~0.7 | not stated | dex | 7 | they also lie $\sim$ 0.7 dex above the global SFMS |
| Delta SFE of the high-Delta Sigma_SFR cloud of spaxels above the dashed line | > 0.7 | not stated | dex | 7 | as indicated by the cloud of points above the dashed line with $\Delta$SFE $>$ 0.7 |
| Typical Delta O/H profile deviations | < 0.05 | not stated | dex | 8 | The $\Delta$O/H profiles are relatively flat, with deviations typically $<$ 0.05 dex. |
| Systematic change in Delta Sigma_SFR from adding O/H to the matching | ~0.01 | not stated | dex | 3 | find a systematic increase in $\Delta \Sigma_{\rm SFR}$ of $\sim$0.01 dex, which is negligible |

## Qualitative findings

- At face value, with fixed alpha_CO, equal numbers of galaxies are dominated by boosts in gas fraction or SFE in the central averages  
  > "equal numbers of galaxies are dominated by boosts in gas fraction or SFE" (3.1 Results from spatially averaged profiles)
- The two galaxies with the highest offsets above the global main sequence have the highest central Delta SFE  
  > "the two strongest central starbursts (with highest $\Delta$SFR) have the highest central $\Delta$SFE" (3.1 Results from spatially averaged profiles)
- Delta Sigma_SFR correlates more strongly with Delta SFE than with Delta f_H2  
  > "is both steeper, tighter and more significant (based on a Pearson correlation test) than the relation with $\Delta f_{\rm H_2}$" (3.2 Results from spaxel correlations)
- Two galaxies (8156-3701, 8081-3704) have significantly suppressed central metallicity  
  > "There are two galaxies with significantly offset central metallicities: 8156-3701 and 8081-3704." (4 Discussion)

## Claim tuples

- H: Central starbursts are driven mainly by elevated star formation efficiency rather than elevated gas fraction | E: Compare Delta SFE and Delta f_H2 (offsets from the resolved Kennicutt-Schmidt relation and molecular gas main sequence) for the 12 central starbursts, as central averages, radial profiles and spaxel correlations | R: Delta Sigma_SFR correlates more steeply, tightly and significantly with Delta SFE than with Delta f_H2 across 5278 spaxels | F: The primary driver of the central starburst is an elevated SFE | **supported**
- H: Elevated gas fractions also contribute to the central starbursts | E: Delta f_H2 profiles and central medians with fixed alpha_CO, and with alpha_CO lowered by a factor of two | R: Some galaxies show enhanced gas fractions at face value, but most of these vanish for a lower alpha_CO | F: A gas fraction contribution is possible but depends on the choice of alpha_CO | **partially**
- H: Starburst enhancement is accompanied by metal dilution consistent with metal-poor gas inflow | E: Delta O/H profiles and Delta O/H vs Delta Sigma_SFR colour-coded by Delta SFE | R: Two galaxies with the strongest Delta SFR and Delta SFE have suppressed central O/H; weak anti-correlation between Delta Sigma_SFR and Delta O/H across spaxels | F: Metal-poor gas injection in the strongest starburst regions has altered the ISM so that SFE is increased | **partially**
- H: Central starbursts arise from both interactions and secular mechanisms | E: Visual inspection of SDSS gri images of the 12 galaxies for merger features | R: Three of 12 show merger features; 9 of 12 are undisturbed, with similar signatures in both | F: Both interactions and secular mechanisms contribute to central starbursts | **supported**

## Reasoning

- Why this data: ALMA CO(1-0) in a compact configuration gives beams matched to MaNGA resolution, allowing kpc-scale comparison with IFU maps  
  > "The ALMA and MaNGA data are well matched in spatial resolution" (abstract)
- Why this method: Control-spaxel offsets avoid parametric fitting uncertainties of scaling relations  
  > "rather than from an established fit to the rSFMS, avoids parametric uncertainties related to fitting approaches" (2.3 Offsets from local scaling relations)
- Alternative: Including O/H in the Delta Sigma_SFR matching was tested and rejected as unnecessary (~0.01 dex change); O/H not matched because its correlation with Delta Sigma_SFR is investigated later  
  > "We do not match explicitly in O/H, since we will later investigate the correlation of metallicity with $\Delta \Sigma_{\rm SFR}$." (2.3 Offsets from local scaling relations)
- Alternative: Using the ALMaQUEST sample itself to define the rSFMS was rejected because green valley galaxies pull down the control median (~0.1 dex shift), though conclusions would not change  
  > "We do not use the ALMaQUEST sample itself to define the rSFMS" (Footnote 1)
- How they decided it was enough: _not stated_
- Limitation (authors): Fixed alpha_CO is probably an over-estimate for starbursting and central spaxels, which may overstate the gas fraction role  
  > "our assumption of a fixed $\alpha_{CO}$ may over-estimate the role of gas fraction from these centrally averaged values" (3.1 Results from spatially averaged profiles)
- Limitation (authors): Central starburst definition is somewhat subjective  
  > "Whilst this is a somewhat subjective definition of central starburst" (2.4 Central starburst sample selection)
- Limitation (authors): Sample is small  
  > "Although the sample is still small, the results suggest that metal-poor gas inflows from either merger-driven, or secular events can trigger starbursts." (4 Discussion)
- Caveat (inferred, ours): Constant alpha_CO of 4.3 drives Delta SFE and Delta f_H2 directly; only a qualitative factor-of-two test is given, so the SFE vs gas fraction conclusion rests on an untested systematic
- Caveat (inferred, ours): The conclusion relies on a sample of 12 galaxies selected from within ALMaQUEST, itself not complete in mass or volume
- Caveat (inferred, ours): The Delta SFE vs Delta Sigma_SFR correlation shares Sigma_SFR on both axes, so part of the correlation is built in by construction; no quantitative correlation coefficients are given
- Caveat (inferred, ours): Overlapping sliding bins and spaxels oversampled relative to the 2.5 arcsec beam mean the 5278 spaxels are not independent

## Reproducibility

- Data public (paper): MaNGA PIPE3D DR15 products stated as public; ALMA data public status not stated  
  > "The MaNGA data used in this paper make use of the public PIPE3D (Sánchez et al. 2016a, 2016b) data products from the SDSS Data Release 15 (DR15)" (2.1 MaNGA)
- Products in archive: _not stated_
- Missing: ALMA reduction and imaging details (deferred to Lin et al. in prep)
- Missing: CO moment maps and noise estimation, convolution and regridding to the MaNGA grid
- Missing: Region and R_e definitions, exact merger classification, no code released
- Missing: Per-galaxy numeric tables; main results are given in figures
- Data volume (inferred): Four ALMA projects, 12 galaxies used; roughly tens of GB of raw ALMA data, plus MaNGA DR15 PIPE3D cubes/VAC
- Score (inferred): 2/5, MaNGA inputs are public and the offset-metric recipe (control matching tolerances, cuts) is well described, but ALMA reduction is deferred to an unpublished paper and the main results are shown in figures with few numeric values.
- Rediscovery candidate: no, ALMA processing is unspecified and key results are graphical rather than numeric, so a faithful redo would require the unpublished ALMaQUEST reduction.

## Links

- Method: Lin et al (in prep) (ALMaQUEST sample and ALMA data reduction)
- Method: Sánchez et al. 2016a, 2016b (PIPE3D pipeline for MaNGA data products)
- Method: Lin et al. 2019 (Molecular gas main sequence used for Delta f_H2)
- Companion: Ellison et al. (2018) (MaNGA-only study showing central starburst enhancement and low central metallicities)
- Companion: Ellison et al. (2019) (More general analysis of Delta Sigma_SFR regulation for all ALMaQUEST spaxels)
- Companion: Thorp et al. (2019) (Delta O/H metric and MaNGA post-merger analysis)
- Related: ALMaQUEST
- Related: MaNGA
- Related: SDSS DR15

## Checks

```json
{
 "quotes": 100,
 "quotes_ok": 100,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 103,
  "stated": 64,
  "rate": 0.621
 },
 "evidence_ok": true
}
```

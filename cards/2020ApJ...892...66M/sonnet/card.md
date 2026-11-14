# The ALMA Spectroscopic Survey in the HUDF: The Cosmic Dust and Gas Mass Densities in Galaxies up to z ∼ 3

`2020ApJ...892...66M` | The Astrophysical Journal 2020 | first author: Magnelli, Benjamin | arXiv: 2002.08640 | DOI: 10.3847/1538-4357/ab7897

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies
- Question: How do the cosmic dust and gas (H2+HI) mass densities in galaxies, above given stellar masses, evolve with redshift up to z~3, from stacking the ASPECS 1.2 mm map at positions of H-band selected galaxies?  
  > "we measure the cosmic density of dust and implied gas (H$_{2}+$H I) mass in galaxies as a function of look–back time." (abstract)
- Target **Hubble Ultra Deep Field (ASPECS LP 1.2 mm survey area)**: coordinates RA 03h32m38.5s, Dec -27d47m00s (J2000)  
  > "The ASPECS LP 1.2 mm survey covers 4.2 arcmin$^2$ in the HUDF, centered at $\alpha$ $=$ 3$^{\rm h}$ 32$^{\rm m}$ 38.5$^{\rm s}$ , $\delta$ $=$ -27$^\circ$ 47$\ensuremath{'}$ 00$\ensuremath{''}$ (J2000; 2016.1.00324.L)." (2 Data); z/distance galaxy redshifts 0.3-5.5 (spectroscopic for 443 of 1481 catalogue sources, otherwise photometric)  
  > "The ASPECS LP 1.2 mm survey covers 4.2 arcmin$^2$ in the HUDF, centered at $\alpha$ $=$ 3$^{\rm h}$ 32$^{\rm m}$ 38.5$^{\rm s}$ , $\delta$ $=$ -27$^\circ$ 47$\ensuremath{'}$ 00$\ensuremath{''}$ (J2000; 2016.1.00324.L)." (2 Data); distance from spectroscopic compilations (MUSE, HST grism etc.) and EAZY photometric redshifts from Skelton et al. 2014  
  > "The ASPECS LP 1.2 mm survey covers 4.2 arcmin$^2$ in the HUDF, centered at $\alpha$ $=$ 3$^{\rm h}$ 32$^{\rm m}$ 38.5$^{\rm s}$ , $\delta$ $=$ -27$^\circ$ 47$\ensuremath{'}$ 00$\ensuremath{''}$ (J2000; 2016.1.00324.L)." (2 Data)

## Data provenance

- ALMA projects: 2016.1.00324.L
- bands: Band 6, 1.2 mm continuum from eight spectral tunings  
  > "The ASPECS LP 1.2 mm continuum map was obtained by combining eight spectral tunings that cover most of the ALMA band 6." (2 Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.53" x 1.08" FWHM, PA -84 deg  
  > "The synthesized beam has a full width at half maximum (FWHM) of $1.53\ensuremath{''}\times1.08\ensuremath{''}$ at a position angle of $-84^\circ$." (2 Data)
- max recoverable scale: _not stated_
- sensitivity: rms 9.5 uJy/beam in deepest region (PB >= 90%)  
  > "The deepest region in the map (i.e., with a combined PB coverage $\gtrsim90\%$) has an rms of $9.5\,\mu$Jy beam$^{-1}$." (2 Data)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **HST (CANDELS, HUDF09/12), Spitzer IRAC/MIPS, ground-based optical/NIR**: Multi-wavelength master photometric catalogue (>30 bands) for stellar masses and H-band selection  
  > "It provides measurements in $>\,$30 broad and medium bands for 1481 sources in the region of interest in the XDF" (3 Sample)
- Other facility **MUSE HUDF survey, HST grism and other spectroscopic surveys**: Spectroscopic redshifts for 443 galaxies  
  > "The spectroscopic redshifts of 443 of these galaxies were obtained from a variety of studies" (3 Sample)
- External data: Master photometric catalogue and photometric redshifts (EAZY)  
  > "we use photometric redshifts determined in (cite: skelton_2014) by means of the `EAZY` code" (3 Sample) [from (cite: skelton_2014)]
- External data: Single-Schechter parameters of star-forming galaxy stellar mass functions  
  > "The single Schechter parameters for the star-forming galaxy SMFs, as found in (cite: mortlock_2015)." (Table 1) [from (cite: mortlock_2015)]
- External data: Detected-source list for the ASPECS 1.2 mm map (22 sources) and astrometric offset  
  > "There are 22 galaxies detected by Gonzalez–Lopez et al. (2019b) in the ASPECS LP 1.2 mm continuum map" (3 Sample) [from Gonzalez–Lopez et al. (2019b)]
- Simulation/model as data: Semi-analytic and hydrodynamic dust/gas predictions (Popping 2017, Aoyama 2018, Li 2019, Vijayan 2019) compared with measurements  
  > "we compare the cosmic dust and gas mass densities predicted by the semi-analytical model of (cite: popping_2017) for different stellar mass thresholds." (7.1 Comparison to simulations)

## Processing

### Calibration

- pipeline or manual: CASA calibration pipeline with the JAO script  
  > "The data was calibrated with the Common Astronomy Software Applications (cite: mcMullin_2007) calibration pipeline using the script provided by the Joint ALMA Observatory (JAO)." (2 Data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean, multi-frequency synthesis, mosaic of 85 pointings combined down to PB gain 0.1  
  > "Imaging was also done in CASA using the multi-frequency synthesis algorithm implemented within the task TCLEAN, which combines all pointings together down to a primary beam (PB) gain of 0.1." (2 Data)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We used natural weighting and ‘cleaned’ down to 20 $\mu$Jy beam$^{-1}$ all sources with a signal-to-noise ratio (SNR) greater than 5." (2 Data)
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
- final beam: 1.53" x 1.08", PA -84 deg  
  > "The synthesized beam has a full width at half maximum (FWHM) of $1.53\ensuremath{''}\times1.08\ensuremath{''}$ at a position angle of $-84^\circ$." (2 Data)
- final rms: 9.5 uJy/beam (deepest region)  
  > "The deepest region in the map (i.e., with a combined PB coverage $\gtrsim90\%$) has an rms of $9.5\,\mu$Jy beam$^{-1}$." (2 Data)

### Inherited from earlier work

- Survey strategy, calibration and imaging of the 1.2 mm map  
  > "The survey strategy as well as the data calibration and imaging are described in detail by Gonzalez–Lopez et al. (2019b)." (2 Data) [from Gonzalez–Lopez et al. (2019b)]
- Master catalogue compilation and SED modelling  
  > "The compilation of our master catalogue of galaxies and the modelling of their spectral energy distribution (SED) are described by (cite: decarli_2019) and (cite: boogaard_2019), respectively." (3 Sample) [from (cite: decarli_2019); (cite: boogaard_2019)]
- Gas-to-dust ratio and mass-metallicity relation parametrisation  
  > "As in (cite: tacconi_2018), we used a gas-to-dust mass ratio ($\delta_{\rm GDR}$) that correlates nearly linearly with metallicity" (4.1) [from (cite: tacconi_2018)]
- Dust temperature 25 K and beta=1.8  
  > "As advocated by (cite: scoville_2016), we used a mass-weighted mean dust temperature of $\langle T\rangle_{\rm M}=T=25\,$K." (4.1) [from (cite: scoville_2016)]
- Stellar-mass completeness method  
  > "To this end, we used the empirical approach described in (cite: schreiber_2015)." (3 Sample) [from (cite: schreiber_2015)]

### Not stated but needed to reproduce (our reading)

- Exact astrometric-offset-corrected catalogue and MAGPHYS stellar masses/metallicities are not tabulated
- MAGPHYS configuration and priors
- Stack pixel scale and stamp handling of primary-beam correction
- Fitting method (algorithm, priors) for f_dust power-law and joint fits
- Method for combined uncertainty on extrapolated M>1e8 densities
- Cosmic comoving volume per bin calculation details beyond area 2.27 arcmin^2
- Details of CASA version used by the pipeline

## Analysis recipe

1. **Select H-band sample and stellar-mass completeness**: Select H<=27 galaxies from master catalogue (555 galaxies); completeness limit from fitting L_H–M* power law plus 1 sigma scatter  
  > "we kept only the 555 galaxies with an observed total[^3] $H$-band magnitude brighter than 27, of which 281 had a spectroscopic redshift." (3 Sample)
   - software: MAGPHYS, EAZY
   - parameter: Stellar masses from MAGPHYS using 0.37-8.0 um photometry plus 1.2 mm flux  
  > "We used the galaxy’s photometry between 0.37$\,\mu$m and 8.0$\,\mu$m, as well as their 1.2 mm flux density (or upper limit)." (3 Sample)
   - fitting: M* = C L^alpha power law per redshift bin  
  > "we fitted the correlation between the observed-frame $H$–band (1.6 $\mu$m) luminosities of galaxies and their stellar masses (derived as described above) with a simple power law" (3 Sample)
   - validation: Stellar mass functions agree with Mortlock+15 and Davidzon+17 above limits  
  > "Down to our stellar mass–completeness limits, these stellar mass functions agree, within the uncertainties, with the fits inferred by (cite: mortlock_2015) and (cite: davidzon_2017)" (3 Sample)
2. **Convert 1.2 mm flux to dust and gas mass**: Optically thin dust mass equation (Kovacs 2010) with CMB correction; gas mass from metallicity-dependent gas-to-dust ratio  
  > "In the optically thin approximation, which is almost always valid at the long wavelengths probed by our observations, the dust mass ($M_{\rm dust}$ in $M_{\odot}$) of a galaxy can be inferred" (4.1)
   - parameter: beta=1.8; kappa=0.0431 m^2/kg at 352.6 GHz  
  > "we adopted $\kappa_{\nu_0} = 0.0431\,$m$^2\,$kg$^{-1}$ with $\nu_{0}=352.6\,$GHz (cite: li_2001)" (4.1)
   - assumption: T_dust = 25 K mass-weighted  
  > "we used a mass-weighted mean dust temperature of $\langle T\rangle_{\rm M}=T=25\,$K" (4.1)
   - assumption: GDR = 100 at solar metallicity, 12+log(O/H)=8.67; metallicity from mass-metallicity relation  
  > "is equal to 100 at solar metallicity, $[12+{\rm log(O/H)}]_\odot=8.67$" (4.1)
   - fitting: _not stated_
   - validation: Varied T (15-35 K) and beta (1.5-2.0) to assess systematics  
  > "a dust temperature range of $T\sim15-35\,$K implies a systematic uncertainty for our dust masses of 25%–50%." (4.1)
3. **Stack mass-density stamps**: 20"x20" stamps at galaxy positions (after astrometric offset), cut from clean mosaic for detected and residual mosaic for undetected sources, converted to density units per pixel, stacked per redshift bin and cumulative mass threshold  
  > "The size of each stamp is 20$''$$\,\times\,$20$''$" (4.2)
   - software: CASA
   - parameter: Offset dRA=+0.076", dDec=-0.279"; PB coverage >75% (2.27 arcmin^2)  
  > "we applied an astrometry offset ($\Delta$RA$=+0.076\ensuremath{''}$ , $\Delta$Dec$=-0.279\ensuremath{''}$)" (4.2)
   - parameter: Redshift bins 0.3-0.6, 0.6-1.0, 1.0-1.6, 1.6-2.3, 2.3-3.2; mass thresholds from 1e11 down in 0.5 dex steps  
  > "starting at $10^{11}\,M_{\odot}$ and decreasing it in steps of 0.5 dex down to our stellar mass-completeness limit." (4.2)
   - fitting: If S/N>=5 in 0.6xFWHM aperture, 2D Gaussian fit with free amplitude and widths; else total flux in 1.0xFWHM aperture; noise from 200 random apertures; Poisson term added in quadrature  
  > "If $S_{\rm aper}/N_{\rm aper}\geq5$, we fitted the stacked stamp with a 2D Gaussian function." (4.2)
   - validation: 200-realisation bootstrap, positional jitter of 0.6", randomised positions give non-detections  
  > "As a last sanity check, we randomized the position of the galaxies in the sample and repeated the stacking analysis. We only obtained non-detections." (4.2)
4. **Model dust/gas-to-stellar mass ratio and extrapolate total densities**: Fit rho(M*>M,z) = integral of f(M,z) x SMF with power-law f; per-bin and joint fits with redshift-dependent normalisation; extrapolate to M*>1e8  
  > "Because the SMF of galaxies is well known up to $z\sim3$ (cite: mortlock_2015), one can solve for $f_{\rm dust}(M,z)$ by fitting $\rho_{\rm dust}(M_\ast>M,z)$." (5.2)
   - parameter: f = A (M/10^10.7)^B; joint: log f = C + D log(1+z) + B log(M/10^10.7)  
  > "{\rm log}(f_{\rm dust}(M,z)) = C + D \times {\rm log}(1+z)\ +" (5.2)
   - assumption: Mortlock+15 star-forming SMF used; quiescent contribution negligible  
  > "We did not use the SMF that includes quiescent galaxies, as the contribution of those to $\rho_{\rm dust}(M_\ast>M, z)$ has been shown to be negligible" (5.2)
   - fitting: Fit method/sampler not stated; reduced chi2 reported  
  > "This fit described accurately our observations, with a reduced $\chi^2=1.0$." (5.2)
   - validation: Compared to Tacconi+18 predictions, Dunne, Driver, CO surveys  
  > "These predictions are in good agreement, within the total uncertainties, with our observations, but in our lowest redshift bin" (5.2)

## Software

- **CASA** : Calibration pipeline and tclean imaging  
  > "Imaging was also done in CASA using the multi-frequency synthesis algorithm implemented within the task TCLEAN" (2 Data)
- **MAGPHYS** : SED modelling for stellar masses (high-z extension)  
  > "using the high-redshift extension of the `MAGPHYS` code (cite: dacunha_2008; dacunha_2015)" (3 Sample)
- **EAZY** : Photometric redshifts (from Skelton+14)  
  > "we use photometric redshifts determined in (cite: skelton_2014) by means of the `EAZY` code" (3 Sample)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Deepest-region rms of 1.2 mm map | 9.5 | not stated | uJy/beam | 0 | has an rms of $9.5\,\mu$Jy beam$^{-1}$ |
| rho_dust(M*>1e8) at 0.3<=z<0.6 (Table, cumulative at completeness limit) | 1.1 | ±0.8 | 1e5 Msun/Mpc^3 | 3 | $1.1\pm0.8$ ($0.5$) |
| rho_dust(M*>1e9) at 1.0<=z<1.6 | 4.3 | ±1.3 | 1e5 Msun/Mpc^3 | 3 | $4.7\pm1.4$ ($0.5$)   / $4.3\pm1.3$ ($0.3$) |
| Mass-weighted gas-to-dust ratio rho_gas/rho_dust at z~0.45, 0.80, 1.30, 1.95, 2.75 | 166, 155, 130, 140, 240 | ±115, ±104, ±73, ±63, ±140 | dimensionless | 4 | we found $166\pm115$, $155\pm104$, $130\pm73$, $140\pm63$, and $240\pm140$, respectively |
| Decrease of rho_dust from z=1.3 to 0.45 | 3.6 | ±2.0 | factor | 4 | decreased by a factor $\sim3.6\,(\pm2.0)$ from $z=1.3$ to $0.45$ |
| Decrease of rho_gas from z=1.3 to 0.45 | 2.8 | ±1.7 | factor | 4 | then decreases by a factor $\sim2.8\,(\pm1.7)$ between $z=1.3$ and $0.45$ |
| Joint fit dust-to-stellar ratio parameters C, D, B | C=-3.0, D=2.6, B=0.1 | C +0.3/-0.5; D ±1.1; B +1.0/-0.7 | dimensionless | 4 | with $C=-3.0^{+0.3}_{-0.5}$, and $D=2.6^{+1.1}_{-1.1}$) and exponent (i.e., $B=0.1^{+1.0}_{-0.7}$) |
| Joint fit gas-to-stellar ratio parameters B, C, D | B=-0.1, C=-1.1, D=3.0 | B +0.8/-0.5; C +0.3/-0.5; D +1.1/-1.0 | dimensionless | 4 | $B=-0.1^{+0.8}_{-0.5}$, $C=-1.1^{+0.3}_{-0.5}$, and $D=3.0^{+1.1}_{-1.0}$ |
| Fractional cosmic variance in the five redshift bins | 58%, 49%, 42%, 43%, 42% | not stated | percent | 0 | a fractional cosmic variance uncertainty of 58%, 49%, 42%, 43% and 42% |

## Qualitative findings

- Low-mass galaxies (<~1e9.5-10 Msun) contribute little to cosmic dust and gas density; bulk is in star-forming galaxies with M*>~1e9.5  
  > "The bulk of the dust and gas in galaxies appears to be locked in star-forming galaxies with $M_{\ast}\gtrsim10^{9.5}\,M_\odot$." (8 Conclusions)
- Popping+17 and Vijayan+19 models overestimate rho_dust at z<1  
  > "they over-estimate the cosmic dust mass density in galaxies at $z<1$" (7.1)

## Claim tuples

- H: Do dust and gas densities converge to total values at the completeness limits? | E: Cumulative stacking in mass thresholds per redshift bin | R: Densities flatten below ~1e10 Msun | F: Completeness-limit measurements approximate total cosmic dust and gas densities in galaxies | **supported**
- H: Do quiescent galaxies contribute significantly? | E: Exclude UVJ-quiescent galaxies from stacks | R: Decrease <5% to ~13% in rho_dust, <=10% in gas | F: Contribution minor | **supported**
- H: Does dust-based rho_gas agree with CO-based measurements and track the SFRD? | E: Compare with ASPECS-CO and COLDz and scaled SFRD | R: Good agreement in all redshift bins | F: Roughly constant star-formation efficiency within a factor ~2 | **supported**
- H: Is dust destroyed/ejected after z~2? | E: Compare rho_dust evolution with dust yields from SFRD | R: rho_dust decreases at z<2 | F: ~90% of dust formed has been destroyed or ejected by z~0 | **partially**

## Reasoning

- Why this data: 1.2 mm probes Rayleigh-Jeans dust emission up to z~4; blind survey gives unbiased view of all galaxies  
  > "The wavelength of this survey probes the Rayleigh-Jeans dust emission of galaxies up to $z\sim4$" (1 Introduction)
- Why this method: Stacking at known positions of a mass-complete sample recovers emission below the detection threshold  
  > "we can thus sum up their 1.2 mm emission within a given comoving volume, irrespective of their individual detectability in our 1.2 mm map." (1 Introduction)
- Alternative: IRAC-selected samples rejected since they give shallower mass completeness than the H-band selection  
  > "IRAC observations in the XDF do not provide stellar mass-complete samples as deep as that provided by the $H$-band." (3 Sample)
- How they decided it was enough: _not stated_
- Limitation (authors): Pencil-beam survey affected by cosmic variance (~42-58%)  
  > "our estimates of $\rho_{\rm dust}$ are affected by cosmic variance, which is only partly included in the Poissonian uncertainties." (5.3)
- Limitation (authors): Dust-based gas may be biased against atomic phase; low-metallicity GDR relation uncertain  
  > "This implies that dust-based gas mass estimates might be biased against the dust in the atomic phase." (6.1)
- Caveat (inferred, ours): Gas masses depend strongly on assumed T=25 K, beta, kappa and metallicity-dependent GDR
- Caveat (inferred, ours): Stellar masses and metallicities from mass-metallicity relation rather than measured
- Caveat (inferred, ours): Cumulative bins are not independent and the extrapolation to 1e8 relies on a power-law f(M)
- Caveat (inferred, ours): Fit procedure unspecified

## Reproducibility

- Data public (paper): ALMA data cited by project code 2016.1.00324.L; other data from public catalogues  
  > "This Paper makes use of the ALMA data ADS/JAO.ALMA#2016.1.00324.L." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Final stellar-mass/redshift catalogue and MAGPHYS outputs
- Missing: Stacking code and pixel-level details
- Missing: Fit procedure for f_dust/f_gas parameters
- Missing: Reduced ASPECS mosaic (from Gonzalez-Lopez+19)
- Data volume (inferred): Large mosaic of 85 pointings in 8 tunings; reduced continuum map ~ <1 GB, raw ~hundreds of GB
- Score (inferred): 3/5, Data public and method clear, but catalogues and fitting details are inherited from companion papers and not tabulated.
- Rediscovery candidate: no, Requires external catalogues and unpublished fitting details, though the main results are numeric.

## Links

- Method: Gonzalez–Lopez et al. (2019b) (ASPECS LP 1.2 mm continuum calibration, imaging and source catalogue)
- Method: (cite: decarli_2019) (Master catalogue compilation)
- Method: (cite: boogaard_2019) (SED modelling)
- Method: (cite: scoville_2016) (Rayleigh-Jeans dust-to-gas method)
- Method: (cite: tacconi_2018) (GDR, metallicity and gas ratio parametrisations)
- Companion: (cite: decarli_2019) (ASPECS LP CO luminosity function and molecular gas density comparison)
- Companion: (cite: walter_2016) (ASPECS pilot survey description)
- Related: ASPECS
- Related: COLDz
- Related: CANDELS
- Related: Hubble eXtremely Deep Field

## Checks

```json
{
 "quotes": 68,
 "quotes_ok": 68,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 53,
  "rate": 0.646
 },
 "evidence_ok": true
}
```

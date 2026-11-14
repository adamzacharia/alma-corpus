# Detecting and Characterizing Young Quasars. I. Systemic Redshifts and Proximity Zone Measurements

`2020ApJ...900...37E` | The Astrophysical Journal 2020 | first author: Eilers, Anna-Christina | arXiv: 2002.01811 | DOI: 10.3847/1538-4357/aba52e

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: Which high-z quasars preselected for small proximity zones are young, once systemic redshifts from sub-mm lines are obtained, and what fraction of quasars is young?  
  > "This study aims to determine the fraction of such young objects within the quasar population at large, and to establish a statistically uniform and significant sample of young quasars" (Introduction)
- Target **PSO J158-14**: coordinates 10:34:46.509 -14:25:15.855  
  > "PSO J158–14 & 10:34:46.509 & –14:25:15.855 & ALMA & 0.3 & 2017.1.00332.S (PI: Eilers)" (Table 1); z/distance z=6.0681 ([C II])  
  > "PSO J158–14 & 10:34:46.509 & –14:25:15.855 & ALMA & 0.3 & 2017.1.00332.S (PI: Eilers)" (Table 1); distance from [C II] line from ALMA  
  > "PSO J158–14 & 10:34:46.509 & –14:25:15.855 & ALMA & 0.3 & 2017.1.00332.S (PI: Eilers)" (Table 1)
- Target **PSO J004+17**: coordinates 00:17:34.467 +17:05:10.696  
  > "PSO J004+17 & 00:17:34.467 & +17:05:10.696 & ALMA & 0.6 & 2017.1.00332.S (PI: Eilers)" (Table 1); z/distance z=5.8165  
  > "PSO J004+17 & 00:17:34.467 & +17:05:10.696 & ALMA & 0.6 & 2017.1.00332.S (PI: Eilers)" (Table 1); distance from [C II] line from ALMA  
  > "PSO J004+17 & 00:17:34.467 & +17:05:10.696 & ALMA & 0.6 & 2017.1.00332.S (PI: Eilers)" (Table 1)
- Target **13 quasars at 5.8<z<6.5 (others: PSO J011+09, J056-16, J239-07, J359-06 with ALMA)**: coordinates see Table 1  
  > "We analyze $13$ quasars at $5.8 \lesssim z \lesssim 6.5$" (Summary & Conclusions); z/distance 5.8-6.5  
  > "We analyze $13$ quasars at $5.8 \lesssim z \lesssim 6.5$" (Summary & Conclusions); distance from sub-mm lines, or Mg II for three objects  
  > "We analyze $13$ quasars at $5.8 \lesssim z \lesssim 6.5$" (Summary & Conclusions)

## Data provenance

- ALMA projects: 2017.1.00332.S
- bands: [C II] tuned over two neighbouring spectral windows; other two windows continuum (band number not stated)  
  > "The other two spectral windows cover the dust continuum emission." (3.1 ALMA Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: compact C43-2, ~1'' resolution  
  > "Observations were carried out in May 2018 with the array in a compact configuration $\rm C43-2$, resulting in images with $\sim 1\ensuremath{''}$ spatial resolution." (3.1 ALMA Observations)
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: mean rms 0.35 mJy/beam per 30 MHz bin  
  > "The mean rms noise is $0.35\,\rm mJy\,beam^{-1}$ per $30$ MHz bin." (3.1 ALMA Observations)
- time on source: ~15-20 minutes on source  
  > "The ALMA data consist of short ($\sim 15-20$ minutes on source) observations" (3.1 ALMA Observations)
- observing dates: May 2018  
  > "Observations were carried out in May 2018" (3.1 ALMA Observations)
- pi or archival as stated: _not stated_
- Line: [C II] 158 um (1900.548 GHz)
- Other facility **NOEMA**: [C II] or CO redshifts for three northern quasars  
  > "Three quasars from our sample located in the Northern hemisphere have been observed with the ten antennas of NOEMA in compact configuration" (3.2 NOEMA Observations)
- Other facility **VLT/X-Shooter**: optical/NIR spectra for proximity zones, Mg II  
  > "Most quasar spectra observed with X-Shooter on the VLT were obtained on August 18th and 19th, 2018, in visitor mode" (3.3 VLT/X-Shooter Observations)
- Other facility **Keck/DEIMOS**: optical spectra for two northern quasars  
  > "The two quasar spectra taken with the DEIMOS instrument at the Nasmyth focus on the Keck II telescope were observed in May and September 2017." (3.4 Keck/DEIMOS Observations)
- External data: CFHQS J2100-1715 and J2229+1457 sub-mm line parameters taken from literature  
  > "Parameters for CFHQS J2100–1715 are derived by (*a*) (cite: Decarli2017), and (*b*) (cite: Decarli2018), while parameters for CFHQS J2229+1457 are taken from (*c*) (cite: Willott2015)." (Table 3 notes) [from Decarli2017; Decarli2018; Willott2015]
- External data: Mg II-[C II] velocity shift -390 (+460/-280) km/s  
  > "(Schindler et al. in prep.), i.e. $$\begin{equation}
 \Delta v_{\rm MgII-[CII]} =-390^{+460}_{-280}\,\rm km\,s^{-1}" (4.4 Proximity Zone Sizes) [from Schindler et al. in prep.]

## Processing

### Calibration

- pipeline or manual: CASA pipeline default calibration  
  > "The data were processed with the default calibration procedure making use of the CASA pipeline (cite: McMullin2007), version $5.1.2$." (3.1 ALMA Observations)
- casa version: 5.1.2  
  > "version $5.1.2$" (3.1 ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~10% systematic  
  > "neglect the $\sim 10\%$ systematic uncertainty that comes from calibrating interferometric data" (4.1 Systemic Redshifts)
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "The data cubes were then imaged with the CASA command `tclean` using Briggs cleaning and a robust parameter of $2$ (natural weighting)" (3.1 ALMA Observations)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 2 (natural)  
  > "using Briggs cleaning and a robust parameter of $2$ (natural weighting)" (3.1 ALMA Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub; line map collapsed over 0.4 GHz (PSO J158-14) or 0.25 GHz  
  > "We obtain the emission line map by subtracting the continuum emission applying the CASA command `uvcontsub`" (3.1 ALMA Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- PCA quasar continuum method  
  > "Following (cite: Davies2018), we construct a PCA decomposition based on $12,764$ training spectra from the SDSS BOSS sample" (4.3 Quasar Continuum Estimates) [from Davies2018]
- [C II] SFR relation  
  > "Following (cite: DeLooze2014) we estimate the SFR within the quasars’ host galaxies based on their \[C II\] line luminosities" (4.5 Star Formation Rates) [from DeLooze2014]
- Dust SFR and L_IR calibration  
  > "We obtain a dust-based SFR estimate following (cite: KennicuttEvans2012) via the scaling relation" (4.5 Star Formation Rates) [from KennicuttEvans2012]

### Not stated but needed to reproduce (our reading)

- Which ALMA band and exact spectral window setup/channelization per target
- Image size and cell size, clean threshold, masks
- Line-free channels used for continuum and uvcontsub fit
- Velocity-integration windows for line flux
- Boxcar/aperture details: how the 2'' sum handles noise
- Dust continuum flux uncertainty derivation
- Flux/bandpass/phase calibrator names

## Analysis recipe

1. **image ALMA cubes and continuum**: CASA pipeline calibration, tclean natural weighting, continuum from two line-free spws, uvcontsub for line maps  
  > "The map of the continuum emission is calculated by averaging the two line-free spectral windows." (3.1 ALMA Observations)
   - software: CASA
   - parameter: robust = 2  
  > "a robust parameter of $2$ (natural weighting)" (3.1 ALMA Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **fit sub-mm line for systemic redshift**: Extract 1D spectrum at brightest position, fit Gaussian with emcee, median posterior  
  > "We extract the $1$D spectra from the continuum-subtracted data cubes at the position of the brightest emission from the source." (4.1 Systemic Redshifts)
   - software: emcee
   - assumption: Gaussian line shape  
  > "We then fit the \[C II\] or CO emission lines assuming a Gaussian line shape." (4.1 Systemic Redshifts)
   - fitting: emcee, flat priors A in [0,20] mJy, sigma in [0,1] GHz, flat on peak frequency  
  > "with flat priors for the amplitude $A\in[0,\,20]$ mJy, the width $\sigma\in[0,\,1]$ GHz of the emission line" (4.1 Systemic Redshifts)
   - validation: _not stated_
3. **line and continuum fluxes, SFR**: Sum pixels within 2'' radius; L_line from Carilli & Walter; SFR from De Looze [C II] relation and modified blackbody L_IR with Kennicutt & Evans  
  > "To calculate these fluxes we sum the flux of all pixels within a radius of $2''$ around the source" (4.5 Star Formation Rates)
   - assumption: T_dust=47±3 K, beta=1.6±0.1, kappa=0.77(nu/352GHz)^beta cm2/g  
  > "with a dust temperature of $T_{\rm dust}=47\pm3\,\rm K$" (4.5 Star Formation Rates)
   - fitting: _not stated_
   - validation: Systematic scatter 0.4-0.5 dex acknowledged  
  > "the errors are dominated by systematic uncertainties arising from the scatter of $0.4-0.5$ dex in the scaling relations" (4.5 Star Formation Rates)
4. **proximity zone sizes with systemic redshifts**: PCA continuum, normalize, 20 Å boxcar smoothing, R_p where flux drops below 10%, luminosity correction to M1450=-27  
  > "The location at which the smoothed continuum-normalized flux drops below the $10\%$ level marks the extent of the proximity zone $R_p$." (4.4 Proximity Zone Sizes)
   - fitting: _not stated_
   - validation: Continuum uncertainty tested by Gaussian draws, Delta R_p ~0.01-0.03 pMpc  
  > "$\Delta R_p\approx 0.01-0.03$ pMpc, for all quasars for which NIR spectral coverage was available" (Influence of Continuum Uncertainties)

## Software

- **CASA** 5.1.2: pipeline calibration, tclean, uvcontsub  
  > "The data were processed with the default calibration procedure making use of the CASA pipeline (cite: McMullin2007), version $5.1.2$." (3.1 ALMA Observations)
- **GILDAS** : NOEMA calibration and imaging (clic, mapping)  
  > "The data were calibrated and reduced making use of the `GILDAS` routine `clic`" (3.2 NOEMA Observations)
- **emcee** : MCMC line fits  
  > "We apply the Markov Chain Monte Carlo (MCMC) affine-invariant ensemble sampler `emcee`" (4.1 Systemic Redshifts)
- **PypeIt** : optical/NIR spectral reduction  
  > "open source python spectroscopic data reduction package `PypeIt`" (3.4 Keck/DEIMOS Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| PSO J158-14 dust continuum flux | 3.46 | 0.02 | mJy | 3 | $F_{\rm cont}=3.46\pm 0.02\,\rm mJy$ |
| PSO J158-14 SFR | 1420 | not stated | Msun/yr | 3 | PSO J158–14 & 12.98 & 43.2 & 230 & 1420 |
| CFHQS J2100-1715 corrected proximity zone | 0.66 | 0.25 | pMpc | 4 | $R_p=0.37\pm0.14$ pMpc ($R_{p,\,\rm corr}=0.66\pm0.25$ pMpc) |
| fraction of young quasars | 5%-10% | not stated | percent | 4 | $5\%\lesssim f_{\rm young}\lesssim 10\%$ |
| PSO J158-14 [C II] redshift | 6.0681 | not stated | dimensionless | 2 | PSO J158–14 & \[C II\] & 268.89 & 6.0681 & 780 & 3.46 & 1.66 & 9.22 |

## Qualitative findings

- Five quasars show R_p,corr<2 pMpc with no associated absorbers/BALs, implying t_Q ≲ 1e5 yr  
  > "exhibit particularly small proximity zones, i.e. $R_{p,\,\rm corr}\lesssim 2$ pMpc, and thus likely indicate very short quasar lifetimes" (Summary & Conclusions)

## Claim tuples

- H: Preselected quasars with small preliminary proximity zones are truly young | E: Systemic redshifts from ALMA/NOEMA/Mg II, X-Shooter and DEIMOS absorber searches, R_p measurement | R: Five quasars with R_p,corr<2 pMpc and no truncating absorbers | F: Five young quasar candidates, one previously known | **supported**
- H: Fraction of young quasars in the population | E: Count 7 young in 153 total vs 3 of 31 earlier | R: 7/153~5% to 3/31~10% | F: 5%≲f_young≲10% | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Sub-mm lines give much more precise systemic redshifts than UV lines  
  > "These emission lines provide a tenfold improvement on the quasars’ systemic redshifts" (3 Multi-wavelength Data Set)
- How they decided it was enough: _not stated_
- Limitation (authors): Low SNR for CFHQS J2229+1457 redward of Lya cannot securely rule out an absorber  
  > "the low data quality does not allow us to securely rule out this option" (Absorption Systems)
- Caveat (inferred, ours): ALMA is only one of several data sources; ALMA-specific recipe is thin
- Caveat (inferred, ours): Young-fraction estimate depends on selection completeness
- Caveat (inferred, ours): Mg II velocity shift correction relies on unpublished work

## Reproducibility

- Data public (paper): ALMA/ESO program IDs given; X-Shooter archival data from ESO archive  
  > "are taken from the ESO archive" (3.3 VLT/X-Shooter Observations)
- Products in archive: _not stated_
- Code: MCMC corner plots of Mg II fits on Zenodo; no analysis code released  
  > "are available here: https://doi.org/10.5281/zenodo.3997388" (footnote)
- Missing: Imaging parameters beyond robust
- Missing: Unpublished Schindler et al. velocity shift
- Missing: PCA continuum code and training set details
- Data volume (inferred): ~10-30 GB (six short ALMA execution blocks)
- Score (inferred): 3/5, ALMA part is simple and public, but main proximity-zone results rely on non-ALMA spectra and inherited methods.
- Rediscovery candidate: no, Main results depend on VLT/Keck/NOEMA spectra and PCA continuum machinery beyond ALMA.

## Links

- Method: Davies et al. 2018 (cite: Davies2018) (PCA continuum fitting)
- Method: Eilers et al. 2017a (cite: Eilers2017a) (proximity zone method)
- Companion: Eilers et al. in prep (cite: E20prep) (quasar lifetime constraints)

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
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 48,
  "rate": 0.608
 },
 "evidence_ok": true
}
```

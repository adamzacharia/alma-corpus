# Sub-kiloparsec ALMA Imaging of Compact Star-forming Galaxies at z ~ 2.5: Revealing the Formation of Dense Galactic Cores in the Progenitors of Compact Quiescent Galaxies

`2016ApJ...827L..32B` | The Astrophysical Journal Letters 2016 | first author: Barro, G. | arXiv: 1607.01011 | DOI: 10.3847/2041-8205/827/2/L32

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Where is star formation occurring relative to the stellar mass in compact star-forming galaxies at z~2.5, and does this support dissipative formation of compact quiescent galaxies?  
  > "direct measurements of their spatial distribution of the star formation relative to the mass profile, needed to discriminate between the two formation scenarios discussed above, are still inconclusive." (Introduction)
- Target **6 compact SFGs in CANDELS GOODS-S (incl. GDS-9834, GDS-11701, GDS-3280)**: coordinates _not stated_; z/distance z~2.5  
  > "The 6 galaxies analyzed in this paper are drawn from the sample of compact SFGs in the CANDELS ((cite: candelsgro)) GOODS-S region presented in (cite: barro14a)." (Data and Sample selection); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00576.S
- bands: Band 7 (870 um)  
  > "The observations were carried out on 2015-08-29 and 2015-09-07 in band 7 using four spectral windows in the largest bandwidth mode." (Data and Sample selection)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C34-7  
  > "The on-source integration time was 1800s in the longest array configuration, C34-7." (Data and Sample selection)
- baselines: _not stated_
- angular resolution: FWHM = 0.14" x 0.11" average  
  > "The average angular resolution of the observations is FWHM $=0.14\ensuremath{''}\times0.11\ensuremath{''}$" (Data and Sample selection)
- max recoverable scale: _not stated_
- sensitivity: rms 40 uJy/beam  
  > "The rms noise of the observations is $\sigma=40$ $\mu$Jy/beam" (Data and Sample selection)
- time on source: 1800 s per target  
  > "The on-source integration time was 1800s in the longest array configuration, C34-7." (Data and Sample selection)
- observing dates: 2015-08-29 and 2015-09-07  
  > "The observations were carried out on 2015-08-29 and 2015-09-07 in band 7" (Data and Sample selection)
- pi or archival as stated: PI G. Barro, cycle 2  
  > "ALMA cycle-2 campaign (ID: 2013.1.00576.S; PI: G. Barro)" (Data and Sample selection)
- Other facility **HST ACS/WFC3 (CANDELS)**: F850LP and F125W/F160W imaging for UV/optical profiles and stellar mass  
  > "we exploit a joint analysis of the high spatial resolution HST/ACS and WFC3 and ALMA continuum imaging" (Introduction)
- Other facility **Spitzer MIPS, Herschel PACS/SPIRE**: mid-to-far-IR photometry for SED fits  
  > "we include *Spitzer*/MIPS 24 and 70 $\mu$m data (30 $\mu$Jy and 1 mJy, $5\sigma$) from (cite: pg08b)" (Data and Sample selection)
- External data: UV to 8um multi-band photometry catalog  
  > "The UV to near-IR spectral energy distributions (SEDs) include extensive multi-band data ranging from U to 8$\mu$m (cite: guo13)." (Data and Sample selection) [from (cite: guo13)]
- External data: Herschel PACS/SPIRE data  
  > "from the GOODS-Herschel ((cite: elbaz11)) and PEP ((cite: magnelli13)) surveys" (Data and Sample selection) [from (cite: elbaz11); (cite: magnelli13)]
- External data: mass-metallicity relation at z~2  
  > "using the mass-metallicity (MZR) relation at $z\sim2$ of (cite: steidel14)" (models and assumptions) [from (cite: steidel14)]

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

- task: CASA clean  
  > "We used the CASA software to process and clean the data." (Data and Sample selection)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The cleaning algorithm was run using a natural weighting for the `u-v` visibility plane." (Data and Sample selection)
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
- final rms: 40 uJy/beam (2.4 mJy/arcsec^2)  
  > "The rms noise of the observations is $\sigma=40$ $\mu$Jy/beam or $2.4$mJy/arcsec$^{2}$." (Data and Sample selection)

### Inherited from earlier work

- Sample selection method for compact SFGs  
  > "The compact SFGs were identified following the method described in (cite: barro13; barro14a)." (Data and Sample selection) [from (cite: barro13; barro14a)]
- SED fitting details (SFH)  
  > "(see (cite: santini15) for more details)" (models and assumptions) [from (cite: santini15)]
- HST PSFs created with TinyTim  
  > "the PSFs are created with TinyTim (cite: tinytim) as detailed in (cite: vdw12)" (UV, Optical and FIR surface brightness profiles) [from (cite: vdw12)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration approach
- cell size, image size, masking, clean threshold
- continuum bandwidth/frequencies
- MCMC priors and settings for DL07 fits
- FAST grid details
- coordinates of targets
- how ALMA-HST astrometric offset was measured
- GALFIT initial parameters and fit constraints

## Analysis recipe

1. **Fit optical/NIR SEDs for stellar mass**: FAST with BC03 models, Calzetti law, exponentially declining SFH  
  > "We fit the optical/NIR SEDs to calculate stellar masses using FAST (cite: fast) and assuming (cite: bc03) stellar population synthesis models" (models and assumptions)
   - software: FAST
   - parameter: 0<A_V<4  
  > "the (cite: calzetti) dust law with attenuation $0<A_{V}<4$" (models and assumptions)
   - assumption: Chabrier IMF  
  > "assume a (cite: chabrier) initial mass function (IMF)" (Introduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit FIR SEDs for L_IR, SFR, dust and gas mass**: Fit CE01, DH02, Rieke09 templates and DL07 models; SFR_UV+IR from Kennicutt relation; M_gas = delta_GDR M_dust  
  > "We fit the mid-to-FIR SEDs to the dust emission templates of (cite: ce01), (cite: dh02), and (cite: rieke09)." (models and assumptions)
   - software: emcee
   - assumption: delta_GDR ~100 from MZR, Z=8.57  
  > "the average metallicity is Z = 12+log(O/H) $=8.57$ which implies gas-to-dust ratios of $\delta_{\rm GDR}\sim100$." (models and assumptions)
   - fitting: emcee MCMC for DL07 models  
  > "by exploring the parameter space using the Python Markov-Chain Monte Carlo (MCMC) package ` emcee` (cite: mcmc)." (models and assumptions)
   - validation: IR SFRs compared across libraries and with 24um SFRs  
  > "The IR-SFRs determined from the different dust template libraries are in excellent agreement, with a median difference and 1$\sigma$ scatter of $\Delta$SFR $=0.01\pm0.13$ dex." (Integrated IR-, UV- SFRs, dust and gas masses)
3. **Measure sizes and Sersic indices**: Single-component GALFIT fits in F160W, F850LP and ALMA, with TinyTim PSFs for HST and CASA synthetic PSF for ALMA  
  > "modeling the shape of the two-dimensional surface brightness profiles using GALFIT (cite: galfit)." (UV, Optical and FIR surface brightness profiles)
   - software: GALFIT, TinyTim, CASA
   - fitting: _not stated_
   - validation: _not stated_
4. **Build deconvolved stellar mass and SFR profiles**: Scale luminosity profiles to SFR with the UV+IR relation; M/L_g vs (u-g) color from F125W and F160W GALFIT models for mass profile  
  > "The stellar mass profiles are determined from the rest-frame optical luminosity probed by WFC3/F160W (approximately g-band, $L_{\rm g}$)" (Stellar mass, UV- and IR- SFR surface density profiles)
   - software: GALFIT
   - fitting: _not stated_
   - validation: Tested undetected extended IR-SFR components 10x and 100x below detection limit; r_e would increase by ~5% and 20%  
  > "the $r_{\rm e}$ would only increase by $\sim$5% and 20% and thus the SFR would still be more concentrated than the stellar mass." (Stellar mass, UV- and IR- SFR surface density profiles)
5. **Project structural evolution**: Add star formation with constant SFR profile over Delta t = 200 Myr (~t_dpl) to the stellar mass profile; compute r_e,mass and Sigma_1  
  > "assuming that their SFR profiles remain constant during $\Delta t=200$ Myr (approximately $t_{\rm dpl}$)" (Discussion)
   - fitting: _not stated_
   - validation: Compared with Vela simulation tracks  
  > "These evolutionary tracks are very similar to the predictions of the Vela simulations during the “wet compaction” phase" (Discussion)

## Software

- **CASA** : process and clean ALMA data; synthetic PSF  
  > "We used the CASA software to process and clean the data." (Data and Sample selection)
- **FAST** : optical/NIR SED fitting  
  > "using FAST (cite: fast)" (models and assumptions)
- **emcee** : MCMC fitting of DL07 models  
  > "Python Markov-Chain Monte Carlo (MCMC) package ` emcee` (cite: mcmc)" (models and assumptions)
- **GALFIT** : 2D surface brightness profile fitting  
  > "using GALFIT (cite: galfit)" (UV, Optical and FIR surface brightness profiles)
- **TinyTim** : HST PSFs  
  > "the PSFs are created with TinyTim (cite: tinytim)" (UV, Optical and FIR surface brightness profiles)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| L_IR range | 10^12.03-12.80 | not stated | L_sun | 2 | L$_{\rm
  IR}=10^{12.03-12.80}$ L$_{\odot}$ and SFR $=150-730$ M$_{\odot}$ yr$^{-1}$ |
| Gas fraction | 0.47 | +0.19/-0.15 | dimensionless | 2 | f$_{\rm gas}=M_{\rm
  gas}/(M_{\rm gas}+M_{\star})=0.47^{+0.19}_{-0.15}$ |
| Gas depletion time | 230 | +90/-120 | Myr | 2 | $t_{\rm dpl}=M_{\rm gas}/{\rm SFR}=230^{+90}_{-120}$ Myr |
| Ratio of mean r_e,F160W to r_e,870um | 1.9 | not stated | dimensionless | 3 | $\langle r_{\rm e,F160W}\rangle/\langle r_{\rm e, 870\mu
  m}\rangle=1.9$ |
| Half-mass radius after Delta t=200 Myr | 1.9 to 1.2 | not stated | kpc | 5 | decreases the half-mass radius by $1.6\times$ from $r_{\rm e,mass}=1.9$ to $1.2$ kpc |
| log Sigma_1 | 9.7 to 10.3 | not stated | log M_sun/kpc^2 | 5 | log($\Sigma_{1}$) $=$ 9.7 to 10.3 M$_{\odot}$ kpc$^{-2}$ |

## Qualitative findings

- IR-SFR dominates over UV-SFR (UV/IR >~100) out to r~5 kpc  
  > "it is strongly dominated by the IR emission (UV/IR $\gtrsim100$) up to $r\sim5$ kpc." (Stellar mass, UV- and IR- SFR surface density profiles)

## Claim tuples

- H: Compact SFGs have nuclear starbursts more concentrated than their stellar mass | E: Joint ALMA 870um and HST profile fitting for 6 galaxies | R: Mean SFR profile ~1.5x more concentrated than stellar mass; FIR sizes ~1.9x smaller than optical | F: Star formation is centrally concentrated | **supported**
- H: Dissipative nuclear starbursts form dense cores | E: Evolve mass profile with constant SFR profile for 200 Myr | R: Sigma_1 up ~4x, half-mass radius down 1.6x | F: Supports dissipation-driven formation of compact quiescent galaxies | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Profiles detected only to r~3-4 kpc; larger radii rely on Sersic fits  
  > "Therefore, the results at larger radii are based on the best-fit Sérsic profiles." (Stellar mass, UV- and IR- SFR surface density profiles)
- Caveat (inferred, ours): Only 6 galaxies, selected to be FIR bright
- Caveat (inferred, ours): Evolution assumes constant SFR profile and no mergers or outflows
- Caveat (inferred, ours): Dust-continuum size equated with SFR distribution
- Caveat (inferred, ours): Gas masses rely on assumed gas-to-dust ratio
- Caveat (inferred, ours): Discrepancy between the 200 Myr used in text and Δt=±100 Myr in abstract

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA calibration/imaging parameters
- Missing: target coordinates and IDs
- Missing: SED-fit priors
- Missing: GALFIT configurations
- Data volume (inferred): ~10-50 GB raw for 6 targets in two executions
- Score (inferred): 3/5, Public ALMA project code and clear overall recipe, but imaging and fitting details are sparse (letter format).
- Rediscovery candidate: no, Key results depend on HST/Herschel ancillary data and many unspecified fitting choices.

## Links

- Method: (cite: barro13; barro14a) (Compact SFG selection)
- Method: (cite: szo12) (M/L-color mass profile method)
- Companion: Barro et al. 2014a (cite: barro14a) (Parent sample of compact SFGs)
- Related: CANDELS
- Related: GOODS-Herschel
- Related: PEP

## Checks

```json
{
 "quotes": 49,
 "quotes_ok": 49,
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
  "facts": 76,
  "stated": 39,
  "rate": 0.513
 },
 "evidence_ok": true
}
```

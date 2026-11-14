# HYPERION. Interacting companion and outflow in the most luminous z &gt; 6 quasar

`2024A&A...682A..54T` | Astronomy and Astrophysics 2024 | first author: Tripodi, R. | arXiv: 2306.01644 | DOI: 10.1051/0004-6361/202347081

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: Does deep, lower-resolution ALMA band 3 and 6 data of the z>6 quasar J0100+2802 reveal an interacting companion and a [CII] outflow, and what are their properties?  
  > "revealing for the first time in this source clear velocity gradients indicative of the presence of an interactive companion and a \[CII\] outflow." (Introduction)
- Target **SDSS J010013.02+280225.8 (J0100+2802)**: coordinates 01:00:13.024, +28:02:25.790 (J2000)  
  > "the HYPERION QSO SDSS J010013.02+280225.8 (hereafter J0100+2802) at $z_{\rm [CII]}=6.327$ (cite: wang2019)" (Introduction); "01:00:13.024, +28:02:25.790" (Table 1); z/distance z_[CII]=6.327; 5.66 kpc/arcsec  
  > "the HYPERION QSO SDSS J010013.02+280225.8 (hereafter J0100+2802) at $z_{\rm [CII]}=6.327$ (cite: wang2019)" (Introduction); "01:00:13.024, +28:02:25.790" (Table 1); distance from Wang et al. 2019 (redshift); Planck 2018 cosmology  
  > "the HYPERION QSO SDSS J010013.02+280225.8 (hereafter J0100+2802) at $z_{\rm [CII]}=6.327$ (cite: wang2019)" (Introduction); "01:00:13.024, +28:02:25.790" (Table 1)

## Data provenance

- ALMA projects: 2021.1.00211.S, 2021.2.00151.S
- bands: Band 3 and Band 6  
  > "continuum emission at 252.8 GHz (band 6) and 99.5 GHz (band 3)" (Observation)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: ALMA 12m array  
  > "from the ALMA 12m array" (Observation)
- configurations: _not stated_
- baselines: L5-L80: 26-184 m (B3), 26-182 m (B6)  
  > "26, 184 | 2.59$\times$1.95" (Table 1)
- angular resolution: B6 cube beam 1.08x0.82 arcsec; B3 continuum 2.59x1.95 arcsec  
  > "a clean beam of ($1.08\times 0.82$) arcsec$^2$, PA=1.7$^\circ$" (Observation)
- max recoverable scale: _not stated_
- sensitivity: B6 continuum 0.01 mJy/beam, cube 0.2 mJy/beam per 9 km/s channel; B3 continuum 5 uJy/beam  
  > "an r.m.s noise of $0.2$ mJy/beam per channel" (Observation); "The r.m.s noise reached for the continuum is $5\ \mu$Jy/beam" (Observation)
- time on source: 3.5 h (band 6), 7.5 h (band 3) integration  
  > "with an integration time of 3.5 hours and 7.5 hours for band 6 and band 3, respectively." (Observation)
- observing dates: 21 April 2022 and 21 January 2021  
  > "Observations were carried on 21 April 2022 and 21 January 2021" (Observation)
- pi or archival as stated: PI R. Maiolino  
  > "We analysed the dataset 2021.1.00211.S (PI: R. Maiolino)" (Observation)
- Line: [CII] 158 um fine-structure (not stated)
- Line: CO 6-5 (not stated)
- Other facility **ALMA 7m band 9 (previous)**: 3-sigma upper limit of 2.6 mJy on companion from continuum map in Tripodi+2023  
  > "we were able to derive a $3\sigma$ upper limit from the continuum map presented in (cite: tripodi2023b), that is $2.6$ mJy." (3.3 Dust properties of the companion)
- External data: QSO dust properties (Tdust 48 K, Mdust 2.3e7 Msun, beta 2.6) and SFR 265 Msun/yr  
  > "The dust properties and SFR of the QSO host galaxy are taken from (cite: tripodi2023b)." (Table 1) [from (cite: tripodi2023b)]
- External data: Bolometric luminosity 4.29e14 Lsun  
  > "we adopted the bolometric luminosity of $L_{\rm bol}= 4.29\times10^{14}\rm L_{\odot}$ estimated by (cite: wu2015)" (3.4 Outflow properties and energetics) [from (cite: wu2015)]
- External data: Dust mass absorption coefficient k0=0.45 cm2/g at 250 GHz  
  > "$k_0 = 0.45\  \rm cm^{2}\ g^{-1}$ the mass absorption coefficient (cite: beelen+2006)" (3.3 Dust properties of the companion) [from (cite: beelen+2006)]
- External data: Molecular gas mass 5.4e9 Msun  
  > "the molecular gas mass of $5.4\times 10^9\ \rm M_\odot$ found by (cite: wang2019)" (4 Discussion) [from (cite: wang2019)]

## Processing

### Calibration

- pipeline or manual: Calibrated by the ALMA science archive  
  > "The visibility calibration of the observations was performed by the ALMA science archive." (Observation)
- casa version: CASA 5.1.1-5 (imaging)  
  > "version 5.1.1-5" (Observation)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "we applied `tclean` using natural weighting and a $3\sigma$ cleaning threshold." (Observation)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "we applied `tclean` using natural weighting" (Observation)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub, zeroth-order polynomial on line-free channels  
  > "We used the CASA task `uvcontsub` to fit the continuum visibilities in the line-free channels with a zeroth-order polynomial." (Observation)
- line free channels: [CII] in channels 90-240 for spw2 and 0-40 for spw3; CO(6-5) channels 95-145 spw3; others line-free  
  > "\[CII\] is detected in channels 90-240 for spw2 and 0-40 for spw3." (footnote 2)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: B6 continuum 1.03x0.78 arcsec PA 0.96; cube 1.08x0.82 PA 1.7; B3 2.59x1.95 PA 15.2  
  > "a clean beam of ($1.03\times 0.78$) arcsec$^2$, and a position angle, PA = 0.96$^\circ$" (Observation)
- final rms: B6 cont 0.01 mJy/beam; cube 0.2 mJy/beam; B3 cont 5 uJy/beam  
  > "The r.m.s noise reached for the continuum is $0.01$ mJy/beam" (Observation)

### Inherited from earlier work

- Dust SED and SFR of QSO host adopted from previous work  
  > "The dust SED of the QSO has previously been studied with high accuracy by (cite: tripodi2023b)" (3.3 Dust properties of the companion) [from (cite: tripodi2023b)]
- Gas mass from [CII] luminosity relation  
  > "the corresponding neutral gas mass in PDR can be derived with the relation from (cite: Hailey2010) (see also (cite: bischetti2019b))" (3.4 Outflow properties and energetics) [from (cite: Hailey2010); (cite: bischetti2019b)]

### Not stated but needed to reproduce (our reading)

- Cell size, image size, clean mask and iteration/threshold values
- Which MFS/line channels were combined exactly for continuum and moment maps
- X_C+, gas temperature and density used in the HI mass equation
- Outflow radius derivation details and L_out computation
- Priors/initial values of the two-Gaussian MCMC
- Exact PSF subtraction procedure and apertures
- Archive pipeline version and calibrators
- Whether the second project 2021.2.00151.S data was used

## Analysis recipe

1. **Image continuum and cube**: tclean natural weighting; MFS continuum in line-free channels; uvcontsub order 0 for cube  
  > "We imaged the continuum in band 6 using the multi-frequency synthesis (MFS) mode in all line-free[^2] channels" (Observation)
   - software: CASA
   - parameter: 3 sigma clean threshold; 9 km/s channels  
  > "a $3\sigma$ cleaning threshold" (Observation)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure fluxes of QSO and companion**: 2D Gaussian fits and PSF subtraction normalized to QSO peak; flux in S/N>2 regions with RA offset <-1.3 arcsec  
  > "Then, we subtracted from the \[CII\] map the PSF normalized to the QSO host peak flux." (3.1)
   - assumption: All elongated S/N>2 features attributed to a single companion  
  > "we associated all the elongated features at S/N$>2$ with a single interactive companion." (3.1)
   - fitting: _not stated_
   - validation: Compared to Wang+2019 continuum flux and 2D fit  
  > "which is consistent with the flux of $1.26\pm 0.08$ mJy found by (cite: wang2019)" (3.2)
3. **Fit companion dust SED**: Modified black body with CMB correction; Mdust free, Tdust fixed to 50 K or 30 K, beta scanned 1-3 in steps of 0.1  
  > "We considered one free parameter, $M_{\rm dust}$, and we fixed $T_{\rm dust}$ to 50 K" (3.3)
   - software: emcee
   - parameter: 20 chains, 1000 trials per beta; uniform prior 1e4-1e12 Msun  
  > "we ran a MCMC with 20 chains and 1000 trials for each value of $\beta$ in that range with a step of 0.1." (3.3)
   - assumption: k0=0.45 cm2/g at 250 GHz; source area ~4.0 arcsec2  
  > "The solid angle was estimated using the size of the region where we extracted the flux of the companion, that is $\sim 4.0$ arcsec$^2$." (3.3)
   - fitting: emcee MCMC, uniform prior  
  > "assuming a uniform prior for the fitting parameter" (3.3)
   - validation: Band 9 upper limit 2.6 mJy constrains T<=50 K  
  > "This upper limit is shown as a hollow green square and favours temperatures $\leq 50$ K" (3.3)
4. **Derive companion TIR and SFR**: Integrate best-fit models 8-1000 um; Kennicutt 1998 with Chabrier IMF  
  > "obtaining $L_{\rm TIR}$ in the range $[0.3-3.4]\times 10^{12}\ \rm L_{\odot}$." (3.3)
   - assumption: Chabrier IMF  
  > "adopting a Chabrier initial mass function (cite: chabrier2003)" (3.3)
   - fitting: _not stated_
   - validation: _not stated_
5. **Decompose [CII] line and find outflow**: Single Gaussian then two-Gaussian MCMC fit (6 free parameters) of spectrum from ~1.2 arcsec radius aperture  
  > "running the MCMC algorithm implemented in the `EMCEE` package (cite: foreman2013) with six free parameters" (3.4)
   - software: emcee
   - parameter: uniform priors; narrow and broad mean frequencies not overlapping  
  > "We adopted uniform priors for all the parameters" (3.4)
   - fitting: emcee MCMC two Gaussians  
  > "we fitted the \[CII\] line with two Gaussian components in order to model the narrow and broader emission simultaneously, running the MCMC algorithm implemented in the `EMCEE` package" (Analysis and Results, Outflow properties and energetics)
   - validation: First-order residual approach compared (v98=720 km/s)  
  > "finding $v_{\rm 98}$=720 km s$^{-1}$" (3.4)
6. **Outflow energetics**: M_HI from Hailey-Dunsheath relation; Mdot = v M/R; kinetic power and momentum load vs L_bol/c  
  > "Assuming the scenario of time-averaged expelled shells or clumps (cite: rupke2005), we computed the mass outflow rate" (3.4)
   - parameter: R 2.4-5.5 kpc; v_out=560 km/s  
  > "$R_{\rm min}=2.4$ kpc and $R_{\rm max}=5.5$ kpc" (3.4)
   - assumption: PDR L[CII]-to-gas mass conversion  
  > "Assuming a $L_{\rm [CII]}$ to gas mass conversion as in PDR regions" (3.4)
   - fitting: _not stated_
   - validation: Compared with literature outflows  
  > "In Fig. [7](#fig:outflow), we compare our results (red stars)" (4 Discussion)

## Software

- **CASA** 5.1.1-5: imaging (tclean) and uvcontsub  
  > "The imaging was performed through the Common Astronomy Software Applications (CASA; (cite: casa2022)), version 5.1.1-5." (Observation)
- **emcee** : MCMC fits of SED and [CII] spectrum  
  > "using a Markov Chain Monte Carlo (MCMC) algorithm implemented in the `EMCEE` package" (3.3)
- **astropy** : listed software  
  > "*Software:* astropy (cite: astropy2022), Matplotlib (cite: matplotlib2007), SciPy (cite: scipy2023)" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| QSO band 6 continuum flux | 1.19 | 0.06 | mJy | 2 | $S_{\rm cont,\ 253 GHz}$ / \[mJy\] / $1.19 \pm 0.06$ / $0.25 \pm 0.01$ |
| Companion band 6 continuum flux | 0.25 | 0.01 | mJy | 2 | $S_{\rm cont,\ 253 GHz}$ / \[mJy\] / $1.19 \pm 0.06$ / $0.25 \pm 0.01$ |
| Companion band 3 continuum flux | 0.007 | 0.002 | mJy | 2 | $S_{\rm cont,\ 99 GHz}$ / \[mJy\] / $0.043 \pm 0.005$ / $0.007 \pm 0.002$ |
| L[CII] companion | 1.68e9 | 0.06e9 | Lsun | 2 | we derived $L_{\rm [CII], comp}=(1.68\pm 0.06)\times 10^9\ \rm L_\odot$ |
| L[CII] QSO host | 4.70e9 | 0.12e9 | Lsun | 2 | $L_{\rm [CII], host}=(4.70\pm 0.12)\times 10^9\ \rm L_\odot$ |
| Companion dust mass range | 0.3-2.6e7 | not stated | Msun | 3 | $M_{\rm dust}$ / \[$10^7 \rm M_\odot$\] / 2.3$\pm 0.8$ / 0.3-2.6 |
| Companion SFR range | 35-344 | not stated | Msun/yr | 4 | This implies an SFR in the range $[35-344]\ \rm M_{\odot}\ yr^{-1}$ |
| Broad component FWHM | 635 | 20 | km/s | 5 | FWHM$_{\rm B}$ / \[km s$^{-1}$\] / $635 \pm 20$ |
| Mass outflow rate | 118-269 | not stated | Msun/yr | 6 | $\dot{M}_{\rm out}$ / \[$\rm M_\odot\ yr^{-1}$\] / 118-269 |
| Outflow momentum load | 0.01-0.02 | not stated | dimensionless | 6 | =(0.01-0.02) |
| Outflow mass | 1.1e9 | not stated | Msun | 6 | This yields $M_{\rm out}=1.1\times 10^9\ \rm M_{\odot}$. |

## Qualitative findings

- Elongated ~20 kpc [CII] and continuum structure west of the QSO interpreted as a tidally stretched interacting companion; PV diagram suggests merger bridge or early disc settling, unresolved.  
  > "it is likely tracing a star-forming companion, extending on scales of $\sim$4 arcsec, in other words $\sim$20 kpc, that is interacting with the QSO host galaxy." (3.1)

## Claim tuples

- H: Is there an interacting companion to J0100+2802? | E: Channel maps, [CII] and continuum maps in bands 3 and 6 with PSF subtraction | R: Co-spatial elongated [CII] and band 6 continuum emission ~4 arcsec west; band 3 detection 0.007 mJy | F: A dusty interacting companion exists | **supported**
- H: Is there a [CII] outflow? | E: Two-Gaussian fit to spectrum and high-velocity map | R: Broad blue component FWHM 635 km/s, Mdot 118-269 Msun/yr | F: Cold outflow with low momentum load, likely jet-aligned | **supported**
- H: Does the outflow efficiently remove gas? | E: Energetics and comparison to literature | R: Momentum load 0.01-0.02 | F: Outflow cannot be very effective at removing gas | **partially**

## Reasoning

- Why this data: High sensitivity low-resolution data recover extended, diffuse emission missed by higher-resolution observations  
  > "reinforcing the idea that $\sim 1$ arcsec-resolution observations with a high sensitivity are ideal to probe the more extended and diffuse emission" (4 Discussion)
- Why this method: _not stated_
- Alternative: Broad wing as inflow or fainter companion judged unlikely given jet alignment and high dispersion  
  > "Alternative interpretations of the broad wing are that it could be inflowing gas or a fainter companion." (4 Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Resolution cannot distinguish merging from rotation, or single from multiple companions  
  > "However, the resolution of our observation did not allow us to distinguish between merging and rotation processes." (4 Discussion)
- Caveat (inferred, ours): Companion dust SED has only two detections and fixed Tdust, so degenerate
- Caveat (inferred, ours): Outflow gas mass depends on unspecified PDR parameters
- Caveat (inferred, ours): Broad component could partly be QSO host/companion kinematics
- Caveat (inferred, ours): Flux and PSF-subtraction depend on region choices

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Calibrated by ALMA archive; data from project 2021.1.00211.S  
  > "The visibility calibration of the observations was performed by the ALMA science archive." (Observation)
- Missing: Imaging parameters (cell, size, mask)
- Missing: HI mass equation inputs
- Missing: MCMC priors for line fit
- Missing: Exact regions and PSF subtraction details
- Data volume (inferred): ~50-100 GB (two bands, 11 h on source, raw MS)
- Score (inferred): 3/5, Public data and broad method outlined, but many imaging and energetics parameters unstated.
- Rediscovery candidate: yes, Data from ALMA project likely public; numeric fluxes and fit results can be compared, though some settings missing.

## Links

- Method: (cite: Hailey2010) ([CII] to HI mass relation)
- Companion: (cite: tripodi2023b) (Dust SED of the QSO)
- Companion: (cite: zappacosta2023) (HYPERION survey)
- Related: HYPERION

## Checks

```json
{
 "quotes": 78,
 "quotes_ok": 78,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 55,
  "rate": 0.671
 },
 "evidence_ok": true
}
```

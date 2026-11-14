# The ALPINE-ALMA [C II] survey. Molecular gas budget in the early Universe as traced by [C II]

`2020A&A...643A...5D` | Astronomy and Astrophysics 2020 | first author: Dessauges-Zavadsky, M. | arXiv: 2004.10771 | DOI: 10.1051/0004-6361/202038231

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies
- Question: How much molecular gas, as traced by [C II] luminosity, do main-sequence star-forming galaxies at z=4.4-5.9 contain, and how do gas depletion timescale and gas fraction evolve over cosmic time?  
  > "Relying on the (cite: zanella18) correlation, we use the ALPINE data to provide the first set of molecular gas mass estimates for MS SFGs at $z=4.4-5.9$." (Introduction)
- Target **ALPINE galaxies (118 targeted; final sample 87 non-mergers, 44 [C II]-detected)**: coordinates _not stated_; z/distance z=4.4-5.9  
  > "are UV-selected galaxies from the COSMic evOlution Survey (cite: scoville07) and the Extended Chandra Deep Field South survey" (2 Observations and physical properties of ALPINE galaxies); distance from rest-frame UV spectroscopic redshifts (cite: faisst19)  
  > "are UV-selected galaxies from the COSMic evOlution Survey (cite: scoville07) and the Extended Chandra Deep Field South survey" (2 Observations and physical properties of ALPINE galaxies)

## Data provenance

- ALMA projects: 2017.1.00428.L
- bands: Band 7 (275-373 GHz)  
  > "The ALMA observations were carried out in band 7 during Cycles 5 and 6, and completed in February 2019." (2 Observations and physical properties of ALPINE galaxies)
- frequencies and spectral setup: One spw in lower sideband tuned to redshifted [C II]; other three spws for FIR continuum  
  > "one spectral window in the lower-frequency sideband tuned to the [C ii] frequency redshifted by the rest-frame UV spectroscopic redshift of that target" (2 Observations and physical properties of ALPINE galaxies)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.72'' (minimum minor axis) to 1.6'' (maximum major axis); average circularized beam 0.9''  
  > "for an angular resolution varying between $0.72\ensuremath{''}$ (minimum minor axis) and $1.6\ensuremath{''}$ (maximum major axis)" (2 Observations and physical properties of ALPINE galaxies)
- max recoverable scale: _not stated_
- sensitivity: Cube RMS 0.2-0.55 mJy/beam per 25 km/s channel; continuum 50 uJy/beam (z=4.4-4.6), 28 uJy/beam (z=5.1-5.9)  
  > "ranges between $0.2~\rm mJy~beam^{-1}$ and $0.55~\rm mJy~beam^{-1}$ per $25~\rm km~s^{-1}$ channel" (2 Observations and physical properties of ALPINE galaxies)
- time on source: 15-25 minutes per target  
  > "Each target was observed for $15-25$ minutes of on-source time" (2 Observations and physical properties of ALPINE galaxies)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: [C II] 158 um (not stated)
- Other facility **Spitzer, HST, ground-based imaging and spectroscopy (ancillary)**: Stellar masses, SFR_UV, redshifts, SED fits  
  > "All galaxies have optical spectroscopy, ensuring reliable rest-frame UV spectroscopic redshift measurements, and benefit from multi-wavelength ground- and space-based imaging from UV to IR." (2 Observations and physical properties of ALPINE galaxies)
- External data: Stellar masses of ALPINE galaxies (Table A1)  
  > "we adopt $M_{\rm stars}$ listed in Table A1 of (cite: faisst19)" (2 Observations and physical properties of ALPINE galaxies) [from (cite: faisst19)]
- External data: L_IR of FIR-detected galaxies (Table B1) and [C II] fluxes/upper limits (Table C2)  
  > "$L_{\rm IR}$ given in Table B1 of (cite: bethermin19)" (2 Observations and physical properties of ALPINE galaxies) [from (cite: bethermin19)]
- External data: [C II] sizes (circularized effective radii) of 18 galaxies, Table 1  
  > "The circularized effective radii ($r_e$), defined as the square-root of the product of the effective major and minor axes, are adopted as size measurements and are listed in Table 1 of (cite: fujimoto19)." (3.2.3 The dynamical masses) [from (cite: fujimoto19)]
- External data: Literature CO compilation of MS SFGs (101 measurements at 1<z<3.7, plus xCOLD GASS and z=5.65 detection)  
  > "The updated compilation comprises a total of 101 CO luminosity measurements of MS SFGs at $1<z<3.7$" (4 Comparison sample) [from (cite: dessauges15; dessauges17), (cite: tacconi18), (cite: saintonge17), (cite: pavesi19) and others]
- External data: Stellar mass histories from multi-epoch abundance matching (Table 2)  
  > "Stellar mass histories from multi-epoch abundance matching predictions of (cite: behroozi19)" (Table 2) [from (cite: behroozi19)]

## Processing

### Calibration

- pipeline or manual: CASA calibration, cleaning, imaging as described in Bethermin et al. paper  
  > "The ALMA visibility calibration, cleaning, and imaging were performed using the Common Astronomy Software Applications package (cite: mcmullin07), as described in detail in (cite: bethermin19)." (2 Observations and physical properties of ALPINE galaxies)
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
- smoothing: 25 km/s channel spacing  
  > "where $25~\rm km~s^{-1}$ is the spectral resolution that, in our spectral configuration, equals the final channel spacing" (Footnote 4)
- final beam: _not stated_
- final rms: 0.2-0.55 mJy/beam per 25 km/s channel  
  > "The resulting root-mean-square noise (RMS) of the 118 [C ii] data cubes ranges between $0.2~\rm mJy~beam^{-1}$ and $0.55~\rm mJy~beam^{-1}$ per $25~\rm km~s^{-1}$ channel" (2 Observations and physical properties of ALPINE galaxies)

### Inherited from earlier work

- Data reduction, imaging, flux measurements (2-sigma clipped [C II] fluxes, 2D Gaussian continuum fluxes, 3-sigma upper limits)  
  > "as described in detail in (cite: bethermin19)" (2 Observations and physical properties of ALPINE galaxies) [from (cite: bethermin19)]
- Ancillary data, redshifts, SED fits, Mstars  
  > "The detailed description of the ancillary spectra and photometric data can be found in (cite: faisst19), together with the redshift measurements and the SED fits." (2 Observations and physical properties of ALPINE galaxies) [from (cite: faisst19)]
- Morpho-kinematic classification identifying 31 mergers  
  > "From our morpho-kinematic visual classification, described in (cite: lefevre19)" (2 Observations and physical properties of ALPINE galaxies) [from (cite: lefevre19)]
- L_CII-M_molgas calibration  
  > "Applying the calibration of (cite: zanella18) between [C ii] luminosity and molecular gas mass" (3.1) [from (cite: zanella18)]
- Virial mass formula  
  > "following Eq. (10) in (cite: bothwell13)" (3.2.3) [from (cite: bothwell13)]
- alpha_CO metallicity function  
  > "following Eq. (2) in (cite: tacconi18)" (4 Comparison sample) [from (cite: tacconi18)]

### Not stated but needed to reproduce (our reading)

- Individual [C II] fluxes and luminosities per galaxy (only referenced to Bethermin et al.)
- Exact line-luminosity conversion used to compute L_CII
- Kaplan-Meier implementation details (software, treatment)
- Precise galaxy lists and IDs in the 87-galaxy sample
- Binning edges and error-on-mean procedure details for the CO compilation
- Metallicity assumed for ALPINE galaxies (if any)

## Analysis recipe

1. **Define sample**: Exclude 31 merger-classified galaxies, leaving 87 galaxies (44 [C II]-detected, 43 upper limits)  
  > "Therefore, our final sample consists of 87 ALPINE galaxies, of which 44 are detected in [C ii], while 43 only have [C ii] upper limits." (2 Observations and physical properties of ALPINE galaxies)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive molecular gas masses from L_CII**: Apply Zanella+18 relation log L_CII = -1.28 + 0.98 log M_molgas  
  > "$$\log \left(\frac{L_{\rm CII}}{L_{\odot}}\right) = (-1.28\pm 0.21) + (0.98\pm 0.02) \log \left(\frac{M^{\rm CII}_{\rm molgas}}{M_{\odot}}\right)$$" (3.1)
   - parameter: Errors: relative flux uncertainty summed in quadrature with 0.3 dex calibration dispersion  
  > "summing in quadrature the relative uncertainty of [C ii] fluxes (cite: bethermin19) and the 0.3 dex dispersion" (3.1)
   - fitting: _not stated_
   - validation: _not stated_
3. **Cross-check with dust continuum gas masses**: Scale rest-frame 158 um luminosity to 850 um with Bethermin+17 SED template, apply Kaasinen+19 calibration  
  > "We adopt the (cite: bethermin17) FIR SED template to estimate $L_{850\mu \rm m}$ of the 11 ALPINE non-merger galaxies" (3.2.2)
   - parameter: Alternative: MBB with beta=1.8, T_dust=25 K  
  > "fixing the dust opacity spectral index to $\beta = 1.8$ and considering this time a mass-weighted dust temperature of $T_{\rm dust} = 25$ K" (3.2.2)
   - assumption: Molecular gas dominates gas budget; constant dust-to-gas ratio ~1:100  
  > "By assuming that the molecular gas dominates the overall gas budget (the atomic and ionised gas content being negligible) and fixing a dust-to-gas mass ratio" (3.2.2)
   - fitting: _not stated_
   - validation: Agreement within 1-2 sigma (0.3-0.6 dex); [C II] masses higher by 0.3 dex on average  
  > "Within $1-2\,\sigma$ uncertainty of $0.3-0.6$ dex, we find an agreement between these two measurements" (3.2.2)
4. **Cross-check with dynamical masses**: Virial mass 1.56e6 sigma^2 r_e; disk mass for 5 rotators; subtract Mstars  
  > "$$M_{\rm dyn}^{\rm virial}~(M_{\odot}) = 1.56\times 10^6 \left(\frac{\sigma_{\rm CII}}{{\rm km~s^{-1}}}\right)^2 \left(\frac{r_e}{{\rm kpc}}\right),$$" (3.2.3)
   - software: UVMULTIFIT
   - assumption: _not stated_
   - fitting: _not stated_
   - validation: Agreement within 1 sigma of 0.3 dex except two outliers  
  > "there is a good agreement within the $1\,\sigma$ uncertainty of 0.3 dex between these respective molecular gas mass estimates, except for two outliers" (3.2.3)
5. **Build CO comparison sample**: Compile CO MS SFGs, restrict to +-0.3 dex of Speagle+14 MS, apply r_J1 factors and metallicity-dependent alpha_CO  
  > "retain only SFGs lying within the MS dispersion of $\Delta {\rm MS} = \log({\rm SFR/SFR_{MS}}) = \pm 0.3$ dex" (4 Comparison sample)
   - parameter: r21=0.81, r31=0.57, r41=0.33, r51=0.23; alpha_CO,MW=4.36  
  > "$r_{2,1} = 0.81\pm 0.15$, $r_{3,1} = 0.57\pm 0.11$, $r_{4,1} = 0.33\pm 0.06$, and $r_{5,1} = 0.23\pm 0.04$" (4 Comparison sample)
   - assumption: _not stated_
   - fitting: _not stated_
   - validation: _not stated_
6. **Compute t_depl and f_molgas with survival analysis**: t_depl=Mmolgas/SFR; f_molgas=Mmolgas/(Mmolgas+Mstars); means in redshift bins; Kaplan-Meier for upper limits  
  > "In particular, we use the Kaplan-Meier estimator" (5.1)
   - parameter: _not stated_
   - fitting: _not stated_
   - validation: _not stated_
7. **Trace progenitors via abundance matching**: Select Mstars histories from Behroozi+19 for halos 1e13 and 1e14 Msun at z=0 and compare f_molgas evolution  
  > "Following the work by (cite: behroozi19), we use the evolutionary corridors they computed" (5.3)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Visibility calibration, cleaning and imaging  
  > "The ALMA visibility calibration, cleaning, and imaging were performed using the Common Astronomy Software Applications package (cite: mcmullin07)" (2 Observations and physical properties of ALPINE galaxies)
- **UVMULTIFIT** : Exponential-disk size fits in the visibility plane (Fujimoto+19)  
  > "derived their [C ii] sizes by performing exponential-disk profile fits in the visibility plane with `UVMULTIFIT`" (3.2.3)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| log M_molgas (CII) range, 44 detected galaxies | 9.2-10.8 | ~0.3 dex | log Msun | 2 | we obtain molecular gas masses in the range of $\log(M^{\rm CII}_{\rm molgas}/M_{\odot}) = 9.2-10.8$ |
| Mean t_depl (detections), 5.1<z<5.9 | 4.6 | 0.8 | 1e8 yr | 6 | $\langle t_{\rm depl}\rangle$ detections / $5.8\pm 0.6$ / $4.6\pm 0.8$ |
| Mean t_depl (detections), 4.4<z<4.6 | 5.8 | 0.6 | 1e8 yr | 6 | $\langle t_{\rm depl}\rangle$ detections / $5.8\pm 0.6$ / $4.6\pm 0.8$ |
| Mean t_depl (detections+limits), both bins | 2.3 (4.4<z<4.6); 2.3 (5.1<z<5.9) | 0.3; 0.4 | 1e8 yr | 6 | $\langle t_{\rm depl}\rangle$ detections+limits / $2.3\pm 0.3$ / $2.3\pm 0.4$ |
| Mean f_molgas (detections), 4.4<z<4.6 and 5.1<z<5.9 | 0.67; 0.59 | 0.03; 0.05 | dimensionless | 6 | $\langle f_{\rm molgas}\rangle$ detections / $0.67\pm 0.03$ / $0.59\pm 0.05$ |
| Mean f_molgas over z=4.4-5.9 (detections) | 63% | 3% | percent | 6 | reaches a mean value of $63\%\pm 3\%$ over $z=4.4-5.9$ |
| Mean f_molgas with limits | 46% | 5% | percent | 6 | drop to $46\%\pm 5\%$ |
| Spearman coefficient t_depl vs sSFR (z~1-5.9) | -0.49 | p=4.5e-10 | dimensionless | 6 | We find a Spearman rank coefficient of $-0.49$ and $p$-value of $4.5\times 10^{-10}$ |
| Spearman coefficient f_molgas vs Mstars (ALPINE) | -0.50 | p=7.0e-4 | dimensionless | 6 | Spearman rank coefficient of $-0.50$ and $p$-value of $7.0\times 10^{-4}$ |
| Mean f_molgas of progenitors of Milky Way-like galaxies at 5.1<z<5.9 | 90% | 4% | percent | 7 | mean $f_{\rm molgas}$ as high as $90\%\pm 4\%$ |

## Qualitative findings

- [C II]-based gas masses agree with dust-continuum and dynamical estimates within ~0.3 dex, with [C II] overestimating dust-based masses by 0.3 dex on average  
  > "there is some trend for a systematic overestimate of $M^{\rm CII}_{\rm molgas}$ with respect to $M^{850\mu \rm m}_{\rm molgas}$ by 0.3 dex, on average" (3.2.2)

## Claim tuples

- H: Is t_depl at z>4.5 consistent with the steep (1+z)^-1.5 bathtub prediction? | E: Compare ALPINE mean t_depl with CO compilation across redshift | R: Mean t_depl (4.6+-0.8)e8 yr at z=5.1-5.9, about an order of magnitude longer than predicted | F: t_depl declines with a shallower slope than (1+z)^-1.5; MS SFGs at z>~4.5 are not considerably more efficient | **supported**
- H: Does f_molgas continue to rise beyond z~3.7? | E: Mean f_molgas in two ALPINE bins versus lower-z CO sample | R: Mean f_molgas 63%+-3% across z=4.4-5.9 | F: f_molgas flattens at high redshift, consistent with sSFR evolution | **supported**
- H: Is [C II] a reliable gas tracer for ALPINE galaxies? | E: Compare with IR-CO relation, 158/850 um dust continuum and dynamical masses | R: Agreement within ~0.3 dex | F: [C II] is a statistically reliable tracer with 0.3 dex uncertainty, possibly tracing total gas | **supported**
- H: Do published t_depl scaling functions describe z>4 low-mass galaxies? | E: Compare ALPINE bins with Scoville17, Tacconi18, Liu19 functions | R: ALPINE excludes the Liu+19 function at z>~4.5; agrees with Scoville+17 and Tacconi+18 | F: Tacconi+18 function favoured; Liu+19 anticorrelation with Mstars too strong at low mass | **supported**
- H: Does f_molgas evolution differ for progenitors of different halo masses? | E: Behroozi+19 abundance matching to select progenitors | R: Monotonic decrease for 1e13 halos; flat then steep drop for 1e14 halos | F: Different evolution, possibly outflows, halted gas supply, and efficient star formation, if confirmed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: CO and dust are hard to detect at z>4; [C II] correlation with gas mass can overcome this  
  > "Such a correlation between [C ii] luminosity ($L_{\rm CII}$) and $M_{\rm molgas}$ can be exploited to overcome the observational challenge of detecting CO or FIR dust emission in very high-redshift normal SFGs." (Introduction)
- Alternative: Merging systems excluded since deblending [C II] and dust is difficult  
  > "since deblending the [C ii] and dust continuum emissions in closely interacting multi-component systems is difficult with the currently available ALMA data" (2 Observations and physical properties of ALPINE galaxies)
- How they decided it was enough: _not stated_
- Limitation (authors): [C II] may overestimate molecular gas since it also arises from other gas phases  
  > "the measured [C ii] luminosity might overestimate the luminosity arising from the molecular gas even in high-redshift galaxies" (3.1)
- Limitation (authors): Comparison sample under-sampled at z>2.5 and low Mstars  
  > "but is still under-sampled at high-redshift ($z>2.5$) and at the low-$M_{\rm stars}$ end" (4 Comparison sample)
- Caveat (inferred, ours): Gas masses rely on a single empirical L_CII calibration with 0.3 dex scatter, which is untested at z>4 in individual galaxies
- Caveat (inferred, ours): Comparison sample uses heterogeneous CO data and an assumed alpha_CO with uncertain metallicity at high z
- Caveat (inferred, ours): Detected-only samples are biased; upper limits are shallow
- Caveat (inferred, ours): Progenitor selection rests on only three ALPINE galaxies in one bin

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Per-galaxy [C II] fluxes and SFR tables (in companion papers)
- Missing: Kaplan-Meier code details
- Missing: Full CO compilation table
- Data volume (inferred): Large (118 targets, Band 7 cubes); but analysis could use published catalogs (~MB)
- Score (inferred): 3/5, Analysis uses published catalog values and clear formulas, but depends heavily on companion-paper tables and a literature compilation not tabulated here.
- Rediscovery candidate: no, Main results depend on external catalogs and a literature compilation rather than a reducible ALMA recipe in this paper.

## Links

- Method: (cite: bethermin19) (ALPINE data reduction and measurements)
- Method: (cite: zanella18) (L_CII-M_molgas calibration)
- Companion: (cite: lefevre19) (ALPINE survey paper)
- Companion: (cite: faisst19) (ancillary data)
- Companion: (cite: fujimoto19) ([C II] sizes)
- Related: ALPINE
- Related: A3COSMOS
- Related: PHIBSS2
- Related: xCOLD GASS

## Checks

```json
{
 "quotes": 61,
 "quotes_ok": 61,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 89,
  "stated": 43,
  "rate": 0.483
 },
 "evidence_ok": true
}
```

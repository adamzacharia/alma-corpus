# The Main Sequence at z ∼ 1.3 Contains a Sizable Fraction of Galaxies with Compact Star Formation Sizes: A New Population of Early Post-starbursts?

`2019ApJ...877L..23P` | The Astrophysical Journal Letters 2019 | first author: Puglisi, A. | arXiv: 1905.02958 | DOI: 10.3847/2041-8213/ab1f92

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Do Main Sequence galaxies at z~1.3 have star-forming gas sizes (from ALMA) consistent with extended disks, and how do ALMA sizes relate to Ks-band sizes and MS position?  
  > "In this Letter we constrain the ALMA sizes for a statistical sample of 93 IR-selected galaxies at $1.1 \leqslant z \leqslant 1.7$ in COSMOS spanning a wide range in $M_{\star}$ and $SFR$." (Introduction)
- Target **93 Herschel-selected galaxies in COSMOS at 1.1<=z<=1.7**: coordinates _not stated_; z/distance 1.1 <= z_spec <= 1.7  
  > "123 far-IR selected galaxies with $1.1 \le z_{\rm spec} \le 1.7$ in COSMOS (Program-ID 2015.1.00260.S, PI Daddi)" (2.1 ALMA observations and size measurements); distance from spectroscopic redshifts (source catalog not stated)  
  > "123 far-IR selected galaxies with $1.1 \le z_{\rm spec} \le 1.7$ in COSMOS (Program-ID 2015.1.00260.S, PI Daddi)" (2.1 ALMA observations and size measurements)

## Data provenance

- ALMA projects: 2015.1.00260.S, 2016.1.00171.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: CO(5-4)/1.3 mm continuum circularized beam ~0.7''; CO(2-1) ~1.5'' beam  
  > "circularized beam $\sim 0.7''$" (2.1 ALMA observations and size measurements); "($\sim 1.5''$ beam; Program-ID 2016.1.00171.S, PI Daddi)" (2.1 ALMA observations and size measurements)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PI Daddi programs; CO(4-3), [CI] and continuum for 29 objects from Valentino18  
  > "CO(4-3), \[CI\] and underlying continuum observations for 29 objects (cite: Valentino18)" (2.1 ALMA observations and size measurements)
- Line: CO 5-4 (not stated)
- Line: CO 2-1 (not stated)
- Line: CO 4-3 (not stated)
- Other facility **Herschel (PACS/SPIRE)**: Selection and L_IR/SFR from super-deblended catalog  
  > "including notably PACS and SPIRE *Herschel* observations" (2.2 $M_{\star}$, SFRs and $K_{\rm s}$-band sizes)
- Other facility **UltraVISTA**: Ks-band images for optical/near-IR sizes  
  > "on UltraVISTA $K_{\rm s}$-band images (cite: McCracken12)" (2.2 $M_{\star}$, SFRs and $K_{\rm s}$-band sizes)
- External data: Stellar masses for star-forming galaxies  
  > "we use $M_{\star}$ from (cite: Laigle16)" (2.2 $M_{\star}$, SFRs and $K_{\rm s}$-band sizes) [from (cite: Laigle16)]
- External data: L_IR from super-deblended catalog  
  > "from the super-deblended catalog of (cite: Jin18) (cite: Liu18)" (2.2 $M_{\star}$, SFRs and $K_{\rm s}$-band sizes) [from (cite: Jin18) (cite: Liu18)]
- External data: LTG mass-size relation  
  > "they nearly all locate within the LTG relation of (cite: vanDerWel14)" (3 Results) [from (cite: vanDerWel14)]
- Simulation/model as data: Sargent12 bi-modal model predictions of SB fraction within MS  
  > "we compare this quantity with expectation from the (cite: Sargent12) model" (4 Discussion)

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

- Spectral extraction position and line range optimization scripts  
  > "based on the recovered signal (see (cite: Daddi15) and (cite: Valentino18))" (2.1 ALMA observations and size measurements) [from (cite: Daddi15); (cite: Valentino18)]
- Full data set, data reduction and measurements deferred  
  > "For a full description of the data-set, data reduction and measurements, we refer to future papers." (2.1 ALMA observations and size measurements) [from future papers]
- AGN contribution handling in CIGALE for stellar masses  
  > "accounting for the AGN contribution as described in (cite: Circosta18)" (2.2 $M_{\star}$, SFRs and $K_{\rm s}$-band sizes) [from (cite: Circosta18)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration pipeline/CASA version and flux calibrators
- Visibility weighting, uv binning and fitting details of the GILDAS scripts
- Spectral window setup and line velocity ranges per source
- Source list with coordinates and redshifts
- Exact LTG scatter used in chi2
- Details of Kaplan-Meier survival analysis
- Which stellar masses and SFRs per source (tables not given)

## Analysis recipe

1. **Measure ALMA sizes in uv plane**: Extract uv amplitude vs uv distance for each tracer, scale to common frequency, marginalize normalization per tracer, fit circular Gaussian models by chi2; r_eff=FWHM/2  
  > "The galaxy best-fit size (defined as the effective radius $r_{\rm eff} = FWHM/2$) and its $1 \sigma$ uncertainty is determined by comparing the *uv* distance vs. amplitude distribution to circular Gaussian models" (2.1 ALMA observations and size measurements)
   - software: GILDAS
   - parameter: Resolved if P_unres <= 10%  
  > "A source is considered to be resolved when $P_{\rm unres} \leqslant 10 \%$." (2.1 ALMA observations and size measurements)
   - fitting: chi2 minimization as a function of size  
  > "The goodness of the fit is estimated from the $\chi^2$ minimization as a function of the size." (2.1 ALMA observations and size measurements)
   - validation: 1000 Monte Carlo mocks; no systematics beyond 5%  
  > "We find no significant systematics to within $5 \%$, much lower than any measurement errors." (2.1 ALMA observations and size measurements)
2. **Derive Mstar, L_IR, SFR and Ks sizes**: Mstar from Laigle16 (CIGALE for AGN); L_IR from super-deblended SED fits; SFR via Kennicutt98 scaled to Chabrier; Ks sizes via GALFIT circular Gaussian  
  > "We derive sizes in the near-IR rest-frame by fitting circular Gaussian profiles with GALFIT" (2.2 $M_{\star}$, SFRs and $K_{\rm s}$-band sizes)
   - software: CIGALE, GALFIT
   - assumption: Chabrier IMF; H0=70, Om=0.3, OL=0.7  
  > "We use a (cite: Chabrier) IMF and a standard cosmology ($H_{\rm 0} = 70 km s^{-1} Mpc^{-1}$, $\Omega_{\rm m} = 0.3$, $\Omega_{\rm \Lambda} = 0.7$)." (Introduction)
   - fitting: _not stated_
   - validation: Sersic n=1 does not affect results  
  > "Using Sersic index $n=1$ does not affect the results." (Footnote 2)
3. **Identify compact galaxies relative to LTG relation**: chi2 of ALMA size vs LTG size at each Mstar; compare with Kaplan-Meier survival analysis  
  > "we compute the compact fraction via a survival analysis approach through the non-parametric Kaplan-Meier estimator, using $1\sigma$ upper limits." (3 Results)
   - assumption: Undetected sources treated as consistent with LTG relation (conservative)  
  > "we consider undetected sources in our sample (grey dots in Fig [4](#fig3:MS_Compact_fraction_MS)-left) as consistent with the LTG relation" (4 Discussion)
   - fitting: _not stated_
   - validation: Kaplan-Meier lower 1 sigma agrees with conservative estimate  
  > "The lower 1$\sigma$ boundary in the compact fraction derived in this way is in good agreement with our conservative estimate described above." (3 Results)
4. **Compact fraction vs MS position and sSFR rescaling**: Compute compact fraction in three sSFR bins on MS; compare with Sargent12; rescale Mstar by r_Ks^2/r_ALMA^2 to get nuclear sSFR  
  > "scaling the total $M_{\star}$ by $r^{2}_{K_{\rm s}}/r^{2}_{\rm ALMA}$" (4 Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **GILDAS** : scripts for spectral extraction and uv-plane size fitting  
  > "To analyze the data we use GILDAS-based[^1] scripts." (2.1 ALMA observations and size measurements)
- **GALFIT** : Ks-band sizes and magnitudes  
  > "fitting circular Gaussian profiles with GALFIT (cite: Peng10_GALFIT)" (2.2 $M_{\star}$, SFRs and $K_{\rm s}$-band sizes)
- **CIGALE** : Mstar for AGN hosts  
  > "we derive $M_{\star}$ using the code CIGALE (cite: Noll09)" (2.2 $M_{\star}$, SFRs and $K_{\rm s}$-band sizes)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Resolved sources | 32 | not stated | sources | 1 | We obtain 32 resolved sources |
| Median size upper limit | 0.28 | not stated | arcsec | 1 | The median upper limit is $r_{\rm eff} = 0.28 ''$. |
| Compact sample | 27 of 93 | not stated | galaxies | 3 | 66 galaxies are consistent with the LTG relation whereas 27 are more compact than expected |
| Average unresolved source 3σ upper limit | 0.13 | not stated | arcsec | 3 | 3$\sigma$ upper limit $r_{\rm eff} = 0.13 ''$ |
| Compact fraction at Mstar>1e11 in MS | 50 | 18 | percent | 4 | Compact galaxies comprise the $50\pm18 \%$ of MS galaxies at $M_{\star} > 10^{11} M_{\odot}$. |

## Qualitative findings

- No clear correlation between molecular gas size and MS position  
  > "Surprisingly, we find no clear correlation between the molecular gas size and the MS position." (4 Discussion)

## Claim tuples

- H: Do MS galaxies at z~1.3 contain a sizable compact-SF population? | E: uv-plane ALMA sizes vs LTG mass-size relation for 93 galaxies | R: 27 compact galaxies; ~50% of MS at Mstar>1e11 | F: Compact SF galaxies are common within the MS, not expected in standard bimodal scenarios | **supported**
- H: Are compact MS galaxies early post-starbursts? | E: Compare ALMA and Ks sizes and rescale Mstar to nuclear region | R: Nuclear sSFR would lie off MS | F: Compact MS objects suggested to be early post-starbursts | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Combine tracers to increase size accuracy  
  > "We analyze these tracers together to increase the size measurements accuracy." (2.1 ALMA observations and size measurements)
- Alternative: Violent disk instabilities and failed-burst mergers considered unlikely to explain compactness  
  > "Alternative mechanisms such as violent disk instabilities (cite: Bournaud16) cannot dramatically reduce the global SF size" (4 Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Compactness values are lower limits for most compact galaxies; statistics limited  
  > "(but still limited by statistics)" (4 Discussion)
- Caveat (inferred, ours): Resolution of 0.7-1.5'' may hide unresolved pairs
- Caveat (inferred, ours): Sample is IR-luminous and requires spectroscopic z, so selection bias
- Caveat (inferred, ours): Post-starburst interpretation untested without stellar population data
- Caveat (inferred, ours): Upper limits dominate (61 of 93)

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Data reduction details (deferred to future papers)
- Missing: GILDAS script specifics
- Missing: Source catalog and per-source measurements
- Data volume (inferred): ~100-300 GB raw for two projects
- Score (inferred): 3/5, Data codes given and method outlined, but reduction and fitting details deferred to future papers.
- Rediscovery candidate: no, Recipe lacks detail and relies on unpublished scripts and catalogs.

## Links

- Method: (cite: Daddi15) (uv-plane extraction and line range optimization)
- Method: (cite: Valentino18) (CO(4-3), [CI] data and methods)
- Companion: (cite: Calabro19) (radio sizes of pre-coalescence MS outliers)
- Related: COSMOS
- Related: PEP Herschel survey
- Related: UltraVISTA

## Checks

```json
{
 "quotes": 46,
 "quotes_ok": 46,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 32,
  "rate": 0.438
 },
 "evidence_ok": true
}
```

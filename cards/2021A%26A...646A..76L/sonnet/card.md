# The ALPINE-ALMA [C II] survey. Luminosity function of serendipitous [C II] line emitters at z ∼ 5

`2021A&A...646A..76L` | Astronomy and Astrophysics 2021 | first author: Loiacono, Federica | arXiv: 2006.04837 | DOI: 10.1051/0004-6361/202038607

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies
- Question: What is the [C II] luminosity function at z~5 from serendipitous line emitters in ALPINE, and what cosmic SFRD does it imply?  
  > "By converting the [C II] luminosity to star formation rate we evaluated the cosmic star formation rate density (SFRD) at $z\sim 5$." (abstract)
- Target **118 ALPINE pointings (serendipitous line emitters) in COSMOS and ECDFS**: coordinates _not stated_; z/distance serendipitous [C II] at 4.3 < z < 5.4  
  > "The galaxies are located in well–studied sky regions, i.e. the Cosmic Evolution Survey field (COSMOS; (cite: 2007ApJS..172....1S)) and the Extended Chandra Deep Field-South" (2.1 Data description); distance from spectroscopic or photometric redshifts of optical/NIR counterparts  
  > "The galaxies are located in well–studied sky regions, i.e. the Cosmic Evolution Survey field (COSMOS; (cite: 2007ApJS..172....1S)) and the Extended Chandra Deep Field-South" (2.1 Data description)

## Data provenance

- ALMA projects: 2017.1.00428.L
- bands: Band 7, Cycles 5 and 6  
  > "The observations were carried out using ALMA band 7 during Cycles 5 and 6." (2.1 Data description)
- frequencies and spectral setup: two frequency settings covering 4.40<z<4.58 and 5.13<z<5.85; channel width 26-33 km/s  
  > "Two frequency settings were adopted to observe two redshift windows at $4.40 < z < 4.58$ and $5.13 < z < 5.85$." (2.1 Data description)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: average 0.85" x 1.13"  
  > "The average spatial resolution is $0.85" \times 1.13"$." (2.1 Data description)
- max recoverable scale: _not stated_
- sensitivity: 0.14 Jy/beam km/s over 235 km/s line width; 39 uJy/beam continuum  
  > "The achieved noise is, on average, 0.14 Jy/beam  km s$^{-1}$ over a line width of 235  km s$^{-1}$and 39 $\mu$Jy/beam over the continuum." (2.1 Data description)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: [C II] 158 um (not stated)
- Other facility **COSMOS15 and 3D-HST catalogs, HST, Spitzer, Herschel, JVLA 3 GHz, Chandra**: ancillary photometry and redshifts used for line identification  
  > "The UV to near–infrared photometry is widely covered by the COSMOS15 and 3D–*HST* catalogs" (2.2 Ancillary photometry)
- External data: ALPINE data reduction, continuum detections and target catalogs  
  > "The data reduction and processing was handled with the software *CASA* (see (cite: 2020arXiv200200962B) for a full description)." (2.1 Data description) [from (cite: 2020arXiv200200962B)]
- External data: De Looze et al. L[CII]-SFR relation (HII/starburst) used for SFRD conversion  
  > "using the relation (see Table 3 of (cite: 2014A&A...568A..62D); case HII/starburst)" (6 SFRD) [from (cite: 2014A&A...568A..62D)]
- External data: z~0 [C II] LF  
  > "we discuss how the $z\sim 5$ [C II] LF compares with the $z \sim 0$ values (cite: 2017ApJ...834...36H)" (5.2) [from (cite: 2017ApJ...834...36H)]

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
- weighting robust: natural weighting  
  > "The visibilities were imaged using a natural weighting of the uv–plane" (2.1 Data description)
- uv taper: _not stated_
- cell size: 0.15"  
  > "We used a pixel size of $0.15"$" (2.1 Data description)
- image size: 256 x 256 pixels  
  > "an image size of $256 \times 256$ pixels" (2.1 Data description)
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

- Data reduction and processing in CASA  
  > "(see (cite: 2020arXiv200200962B) for a full description)" (2.1 Data description) [from (cite: 2020arXiv200200962B)]
- Fidelity definition  
  > "Following the approach of (cite: 2016ApJ...833...69D) we defined the fidelity $f$" (3.2 Fidelity) [from (cite: 2016ApJ...833...69D)]
- findclumps line search algorithm  
  > "using *findclumps* (see (cite: 2016ApJ...833...69D; 2016ApJ...833...67W) for an exhaustive description)" (3.1 Code description) [from (cite: 2016ApJ...833...69D; 2016ApJ...833...67W)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration details (deferred to Bethermin et al. 2020)
- findclumps code availability and exact settings
- Exact luminosity bin edges (table lacks bin centres)
- Maximum-likelihood fit and walker/step settings for emcee
- SED fitting details for L_IR of the serendipitous sources
- Phase center coordinates of pointings

## Analysis recipe

1. **Blind line search**: findclumps floating average over channel kernels, peaks above S/N 3 in 118 cubes, channel widths ~90-550 km/s  
  > "We executed the search on the 118 ALPINE datacubes adopting a S/N threshold of 3." (3.1 Code description)
   - software: findclumps
   - fitting: _not stated_
   - validation: _not stated_
2. **Fidelity**: f = 1 - Nneg/Npos; keep f>85% (S/N>=6.30) plus two ~50% lines with counterparts  
  > "We included in it the lines with a fidelity higher than 85% (corresponding to a S/N = 6.30 cutoff)." (3.2 Fidelity)
   - software: findclumps
   - fitting: _not stated_
   - validation: negative-peak counts as pure noise  
  > "Unlike the positive ones, the negative peaks provide indeed the distribution of the pure noise of our data." (Fidelity)
3. **Completeness**: inject ~50000 Gaussian lines in noise cubes, recover with findclumps, in four primary-beam rings  
  > "We assessed the completeness by simulating $\sim 50000$ Gaussian–like lines with various peak flux $F$ and FWHM" (3.3 Completeness)
   - software: findclumps
   - fitting: _not stated_
   - validation: _not stated_
4. **Line identification and properties**: cross-match with photometric catalogs within 1"; Gaussian fit of line spectra; CASA 2D fit for sizes  
  > "We classified a galaxy as a physical counterpart of a serendipitous line if their spatial distance is less than $1 "$." (4)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
5. **Build LF**: Phi = sum F_j/(sum C V), 0.5 dex bins at 0.25 dex spacing, Poisson errors; clustered vs field split at dnu ~3.6 GHz  
  > "As the luminosity bin size we considered 0.5 dex in order to have at least one source per bin." (5.1)
   - fitting: _not stated_
   - validation: _not stated_
6. **Schechter fit**: fit log form to clustered LF, MCMC with uniform priors, log L* < 10.5; field Phi* scaled by 1/11  
  > "We assumed for $\alpha$, $\log{L^*}$, $\log{\Phi^*}$ uniform priors." (5.3)
   - software: emcee
   - fitting: maximum likelihood start then emcee MCMC, uniform priors  
  > "The best–fit values were used as initial guesses for a Markov Chain Monte Carlo (MCMC) method with the Python package *emcee*" (5.3)
   - validation: _not stated_
7. **SFRD**: integrate Schechter above 1e7 Lsun, convert with De Looze HII/starburst relation scaled to Chabrier IMF  
  > "We considered in the integration all the luminosities higher than $10^7 {\rm L}_{\odot}$." (6)
   - assumption: non-evolving L[CII]-SFR relation  
  > "We note that the working assumption of a non–evolving $L_{\rm [C~II]}$–SFR relation is not trivial" (6)
   - fitting: _not stated_
   - validation: serendipitous continuum sources and ALPINE targets lie on the De Looze relation  
  > "Therefore both the ALPINE targets and the serendipitous sources seem to independently suggest that there is no significant variation of the relation of" (Relation between [C II] luminosity and SFR)

## Software

- **findclumps** : blind line search  
  > "We performed the search for the serendipitous lines using *findclumps*" (3.1 Code description)
- **CASA** : data reduction, 2D source size fitting  
  > "Then we evaluated the deconvolved sizes of the resolved sources using the 2D fitting tool of *CASA*." (4)
- **emcee** : MCMC Schechter fit  
  > "Markov Chain Monte Carlo (MCMC) method with the Python package *emcee*" (5.3)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of final serendipitous lines | 14 | not stated | dimensionless | 2 | Based on their fidelity, we selected 14 lines for the final catalog. |
| Effective survey area | 27.42 | not stated | arcmin^2 | 0 | This entails a final effective sky area of 27.42 arcmin$^2$ |
| Total comoving volume | 9810 | not stated | Mpc^3 | 5 | $V_{\rm TOT} = \Sigma_i^{118} A_i \Delta D_c(z_i) = 9810\ {\rm Mpc}^3$ |
| log L* clustered | 9.88 | +0.54/-0.55 | log Lsun | 6 | $9.88^{+0.54}_{-0.55}$ |
| log Phi* clustered | -3.01 | +0.44/-0.61 | log Mpc^-3 dex^-1 | 6 | $-3.01^{+0.44}_{-0.61}$ |
| alpha clustered | -0.92 | +0.56/-0.44 | dimensionless | 6 | $-0.92^{+0.56}_{-0.44}$ |
| log SFRD clustered | -0.39 | +0.42/-0.27 | log Msun/yr/Mpc^3 | 7 | $-0.39^{+0.42}_{-0.27}$ |
| log SFRD field | -1.29 | +0.72/-0.62 | log Msun/yr/Mpc^3 | 7 | $-1.29^{+0.72}_{-0.62}$ |

## Qualitative findings

- 11 of 12 [C II] emitters are at redshift close to the central target, suggesting overdensities  
  > "We found that 11 out of these 12 sources have a redshift very similar to that of the ALPINE target in the same pointing" (abstract)

## Claim tuples

- H: Serendipitous [C II] emitters are clustered around ALPINE targets | E: Compared redshift offsets from central targets | R: 11 of 12 within |dz|<0.04; 7 of 8 confirmed with |dv|<750 km/s | F: Overdensities around targets; sample split into clustered and field | **supported**
- H: The [C II] LF evolves from z~0 to z~5 | E: Compared LFs with local LF | R: clustered LF >1 dex higher; field consistent within 2 sigma | F: possible evolution but field uncertain | **partially**
- H: The SFRD at z~5 from [C II] exceeds UV estimates | E: Integrated Schechter LFs and converted to SFRD | R: clustered ~10x higher, field ~1.6x higher but consistent within errors | F: cannot assess obscured fraction given large uncertainties | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Field LF based on a single source; large uncertainties  
  > "we remind that the field LF is based on one object only" (5.1)
- Caveat (inferred, ours): Field sample is one source, Phi* obtained by scaling clustered fit
- Caveat (inferred, ours): Four lines have ambiguous identification assumed to be [C II]
- Caveat (inferred, ours): Fidelity treated as function of S/N only
- Caveat (inferred, ours): Clustered/field split is by sideband offset, somewhat arbitrary

## Reproducibility

- Data public (paper): ALMA Large Program 2017.1.00428.L (public archive not explicitly stated)  
  > "This paper is based on data obtained with the ALMA Observatory, under Large Program 2017.1.00428.L." (Acknowledgements)
- Products in archive: _not stated_
- Missing: findclumps settings and availability
- Missing: CASA calibration details
- Missing: SED fits for L_IR
- Missing: emcee configuration
- Data volume (inferred): ~100s GB for 118 band 7 cubes (calibrated cubes much smaller)
- Score (inferred): 3/5, Methods well described but rely on companion papers and findclumps; data from public large program.
- Rediscovery candidate: no, Depends on inherited processing and findclumps code not provided.

## Links

- Method: (cite: 2016ApJ...833...69D) (findclumps and fidelity definition)
- Method: (cite: 2020arXiv200200962B) (ALPINE data reduction and catalogs)
- Companion: Yan et al. (2020) ([C II] LF from UV-selected central targets)
- Companion: Gruppioni et al. 2020 (serendipitous continuum LF)
- Related: ALPINE
- Related: ASPECS

## Checks

```json
{
 "quotes": 48,
 "quotes_ok": 48,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 34,
  "rate": 0.442
 },
 "evidence_ok": true
}
```

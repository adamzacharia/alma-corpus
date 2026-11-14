# The ALMA Frontier Fields Survey. V. ALMA Stacking of Lyman-Break Galaxies in Abell 2744, Abell 370, Abell S1063, MACSJ0416.1-2403 and MACSJ1149.5+2223

`2020A&A...633A.160C` | Astronomy and Astrophysics 2020 | first author: Carvajal, R. | arXiv: 1912.02916 | DOI: 10.1051/0004-6361/201936260

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies, galaxy_clusters_and_sz
- Question: What are the IR properties and IR excess (IRX) of UV-selected LBGs at z~2-8 behind five Frontier Fields clusters, individually and via stacking, and how do they compare with IRX-beta and IRX-M* relations?  
  > "The goal of our work here is to characterize the IR emission (individually and, given the low number of expected detections, as stacked-averages) for robust samples of Lyman-Break Galaxy (LBG) candidates at $z{=}$2–8 found in the Frontier Fields (FFs) survey." (Introduction)
- Target **Abell 2744**: coordinates 00:14:21.2 -30:23:50.1  
  > "| Abell 2744 | 00:14:21.2 | -30:23:50.1 | 0.308 |" (Table 1); z/distance z=0.308 (cluster)  
  > "| Abell 2744 | 00:14:21.2 | -30:23:50.1 | 0.308 |" (Table 1); distance from _not stated_
- Target **Abell 370**: coordinates 02:39:52.9 -01:34:36.5  
  > "| Abell 370 | 02:39:52.9 | -01:34:36.5 | 0.375 |" (Table 1); z/distance z=0.375 (cluster)  
  > "| Abell 370 | 02:39:52.9 | -01:34:36.5 | 0.375 |" (Table 1); distance from _not stated_
- Target **Abell S1063**: coordinates 22:48:44.4 -44:31:48.8  
  > "| Abell S1063 | 22:48:44.4 | -44:31:48.8 | 0.348 |" (Table 1); z/distance z=0.348 (cluster)  
  > "| Abell S1063 | 22:48:44.4 | -44:31:48.8 | 0.348 |" (Table 1); distance from _not stated_
- Target **MACSJ0416.1-2403**: coordinates 04:16:08.9 -24:04:28.7  
  > "| MACSJ0416.1-2403 | 04:16:08.9 | -24:04:28.7 | 0.396 |" (Table 1); z/distance z=0.396 (cluster)  
  > "| MACSJ0416.1-2403 | 04:16:08.9 | -24:04:28.7 | 0.396 |" (Table 1); distance from _not stated_
- Target **MACSJ1149.5+2223**: coordinates 11:49:36.3 +22:23:58.1  
  > "| MACSJ1149.5+2223 | 11:49:36.3 | +22:23:58.1 | 0.543 |" (Table 1); z/distance z=0.543 (cluster)  
  > "| MACSJ1149.5+2223 | 11:49:36.3 | +22:23:58.1 | 0.543 |" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00999.S, 2015.1.01425.S
- bands: Band 6 (~263 GHz, 1.1 mm)  
  > "ALMA) band 6 ($\approx$263 GHz) mosaics in the central portions of five Frontier Fields" (abstract)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: natural beam major x minor 0.63x0.49 to 1.52x0.85 arcsec  
  > "| Abell 2744 | 00:14:21.2 | -30:23:50.1 | 0.308 | 29-Jun-2014/31-Dec-2014 | 55 | 0.63 $\times$ 0.49 | 126 |" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: natural-weight rms 55, 61, 67, 59, 71 uJy/beam for A2744, A370, AS1063, MACSJ0416, MACSJ1149  
  > "Our reductions achieved natural-weight $rms$[^4] errors of $55$, $61$, $67$, $59$ and $71\, \mu \mathrm{Jy\,beam^{-1}}$ for FFs A2744, A370, AS1063, MACSJ0416 and MACSJ1149, respectively." (2.1 ALMA data)
- time on source: _not stated_
- observing dates: 2014-2015 (cycle 2: A2744, MACSJ0416, MACSJ1149); 2016 (cycle 3: A370, AS1063)  
  > "observed in 2014 and 2015 (hereafter A2744, MACSJ0416 and MACSJ1149, respectively) and, from cycle 3, and —also designed as RXJ2248$-$4431— observed in 2016" (2.1 ALMA data)
- pi or archival as stated: PI Bauer, cycles 2 and 3  
  > "2013.1.00999.S (PI Bauer; cycle 2) and 2015.1.01425.S (PI Bauer; cycle 3)" (2.1 ALMA data)
- Other facility **HST (Frontier Fields ACS/WFC3 + UV campaign)**: Nine-band photometry for LBG selection, photo-z, beta, stellar masses, UV luminosities  
  > "Deep *HST* images are available in seven broadband filters as part of the FFs campaign" (2.2 LBG candidates)
- Other facility **VLT/MUSE**: Published spectroscopic redshift catalogs used to cross-check candidates  
  > "we compared our dropout catalogs with the VLT/MUSE redshift catalogs of" (2.4 Photometric redshifts)
- External data: LBG candidate catalogs (color-selected dropout samples) from HST FF images  
  > "Bouwens et al. 2019 (in prep; hereafter B19) use these images to identify large samples of $z {\sim} 2, 3, 4, 5, 6, 7, 8$, and $9$ star-forming galaxies" (2.2 LBG candidates) [from Bouwens et al. 2019 (in prep; B19)]
- External data: Lens models (CATS v4) for magnification maps and multiple-image catalogs  
  > "we adopted the CATS (Clusters As TelescopeS) team models for our work" (2.5 Magnification factors) [from (cite: 2014MNRAS.443.1549J; 2014MNRAS.444..268R)]
- External data: Redshift-dependent dust temperature prescription  
  > "We adopted evolving values for dust temperature following the redshift-dependent formulation from (cite: 2018A&A...609A..30S)." (2.12 IR luminosities) [from (cite: 2018A&A...609A..30S)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline for MACSJ0416, A370, AS1063; manual/ad-hoc reduction for A2744 and MACSJ1149  
  > "Automatic reduction with the `CASA`-generated pipelines for A2744 and MACSJ1149 presented problems and, hence, manual and ad-hoc pipelines were used to reduce the data." (2.1 ALMA data)
- casa version: CASA v4.2.2  
  > "Common Astronomy Software Applications (`CASA` v4.2.2; (cite: 2007ASPC..376..127M))" (2.1 ALMA data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "Weights are drawn from the `CASA` `clean` PB-correction map" (2.3 ALMA stacking considerations)
- deconvolver: _not stated_
- weighting robust: natural and uv-taper weightings  
  > "we applied two nominal weighting schemes, natural and taper, to the imaged (or `CLEAN`ed) datasets using `CASA`." (2.1 ALMA data)
- uv taper: t = 1.5 arcsec  
  > "For this work, we adopted a taper parameter of $t{=}1$$''$5." (2.1 ALMA data)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: analysis limited to pbcor > 0.5  
  > "we limited our analysis to regions of each mosaic with a PB-correction factor $pbcor {>} 0.5$" (2.1 ALMA data)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA data reduction and calibration details  
  > "details can be found in (cite: 2017A&A...597A..41G)." (2.1 ALMA data) [from (cite: 2017A&A...597A..41G)]
- LBG selection, GALFIT cluster-light removal, photometry  
  > "See (cite: 2015ApJ...803...34B) for more details on the applied photometric procedure." (2.2 LBG candidates) [from B19; (cite: 2015ApJ...803...34B)]
- Magnification computation  
  > "Magnification factors were obtained following the procedure from (cite: 2015ApJ...800...84C), coded as a public `Python` script." (2.5 Magnification factors) [from (cite: 2015ApJ...800...84C)]
- Stacked-image detection levels via iterative >5 sigma clipping  
  > "We calculated the detection levels for each stacked image using the procedure described by (cite: 2017A&A...597A..41G)" (3.2 Stacking) [from (cite: 2017A&A...597A..41G)]
- FDR simulation procedure  
  > "following the procedures outlined in (cite: 2018A&A...620A.125M), we generated 1000 simulated maps for each ALMA field" (2.10 ALMA peak fluxes) [from (cite: 2018A&A...620A.125M)]

### Not stated but needed to reproduce (our reading)

- CLEAN parameters (robust/threshold/niter/cell/image size, masking) for the mosaic images
- Exact B19 LBG catalog (in prep) needed to reproduce the sample
- Dust temperature formula parameters and SED normalization details
- STACKER run parameters
- Flux calibrators and flux scale uncertainty
- Exact bin assignment of the 4.0>=z<=7.0 boundary and how 1580 vs 1582 sources were handled
- Weights/treatment of upper-limit stacking beyond 3-sigma combination

## Analysis recipe

1. **Image mosaics and measure rms**: CLEAN mosaics with natural and tapered weighting; limit to pbcor>0.5  
  > "we applied two nominal weighting schemes, natural and taper, to the imaged (or `CLEAN`ed) datasets using `CASA`." (2.1 ALMA data)
   - software: CASA
   - parameter: taper t=1.5 arcsec  
  > "For this work, we adopted a taper parameter of $t{=}1$$''$5." (2.1 ALMA data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive LBG properties from HST photometry**: FAST++ photo-z and stellar mass/SFR; MCMC power-law fit for beta; magnification from CATS lens model capped at 10  
  > "we used the `C++` version[^5] of the code `FAST` (cite: 2009ApJ...700..221K) with a bin size of $\Delta z_{ph} {=} 0.001$ and $500$ Monte Carlo simulations per source" (2.4 Photometric redshifts)
   - software: FAST++, emcee
   - parameter: 2500 iterations x 100 walkers per source for beta  
  > "For each LBG candidate, $2500$ iterations were performed per each one of the $100$ "random-walkers" which were set for this procedure." (2.6 UV-continuum slope)
   - assumption: BC03 SEDs, Chabrier IMF, tau=1e11 yr, 0.2 Zsun, Calzetti law with 0<=A_V<=1  
  > "setting $\log_{10}{(\tau / \mathrm{yr})}{=}11$ with an exponentially declining star formation history (SFR ${\propto} \exp(-t/\tau)$) and a metallicity of $0.2 Z/Z_{\odot}$" (2.7 Stellar masses)
   - fitting: emcee with priors from maximum-likelihood estimator  
  > "As priors for the model fitting, we used the outputs of a simple maximum likelihood estimator with Eq." (2.6 UV-continuum slope)
   - validation: Photo-z compared to dropout bands and MUSE spec-z; mismatches removed  
  > "Among the 238 matches, only 14 candidates have strong differences between their photometric and spectroscopic redshifts; all 14 were removed." (2.4 Photometric redshifts)
3. **Measure individual ALMA peak fluxes and detections**: Max pixel in 0.5x0.5 arcsec box, pbcor-corrected; detection threshold S/N>=4.1 set via FDR simulations; otherwise n-sigma upper limits  
  > "we searched for the pixel with the maximum value within a 0.5$''$$\times$0.5$''$ box (i.e., comparable to one synthesized beam) centered at the position of each LBG candidate." (2.10 ALMA peak fluxes)
   - parameter: 1000 simulated maps per field  
  > "we generated 1000 simulated maps for each ALMA field with a normal distribution in units of signal-to-noise." (2.10 ALMA peak fluxes)
   - fitting: _not stated_
   - validation: FDR: S/N>~4.1 has <~15% chance of being false  
  > "Based on the FDRs, we find that sources with S/N${\gtrsim} 4.1$ have a relatively low ($\lesssim$15%) chance of being false." (2.10 ALMA peak fluxes)
4. **Derive IR luminosity and IRX**: Scale a graybody SED to ALMA flux, integrate 8-1000 um, correct for CMB; IRX = L_IR/L_UV  
  > "The best-fitted rest-frame SED is integrated between 8 $\mu$m and 1000 $\mu$m to yield the rest-frame IR luminosity." (2.12 IR luminosities)
   - parameter: mid-IR slope 2.0, emissivity 1.6  
  > "We also considered typical fixed values of 2.0 for the mid-IR power-law slope, and 1.6 for the emissivity (cite: 2012MNRAS.425.3094C)." (2.12 IR luminosities)
   - assumption: Redshift-dependent T_dust (~30-65 K) from Schreiber+18  
  > "The distribution of dust temperatures of our candidates ranges from ${\sim} 30$ K to ${\sim} 65$ K" (2.12 IR luminosities)
   - fitting: _not stated_
   - validation: Compared with Aravena+16 sources; within ~0.5 dex of magphys results  
  > "Our results lie within ${\sim} 0.5$ dex of theirs, which were obtained with `magphys`." (2.12 IR luminosities)
5. **Select stacking sample**: Remove beta outliers, sources near >=4 sigma detections, pbcor<0.5, the 2 detections, multiple images, low mass, redshift mismatches  
  > "We summarize our selection criteria in Table [1](#tab:filter), which resulted in a sample of $1580$ undetected LBG candidates to stack" (3.1 Target final sample)
   - fitting: _not stated_
   - validation: _not stated_
6. **Stack ALMA uv data and IRX**: STACKER uv-stacking with four weights (equal, pbcor^2, pbcor^2*F_UV^2, pbcor^2*mu^2) in bins of beta, M*, z; IRX stacked as mean of individual IRX; upper limits from stacked peak + n x error  
  > "We adopted four different weighting schemes for the stacking code and further analysis" (3.2 Stacking)
   - software: STACKER
   - parameter: 5 beta bins, 9 mass bins, 3 z bins  
  > "With UV-slope, targets were stacked in five bins and, for stellar mass, in nine bins." (3.2 Stacking)
   - assumption: No offset between HST and ALMA positions  
  > "no correction was performed regarding relative positional offsets." (2.3 ALMA stacking considerations)
   - fitting: _not stated_
   - validation: Test stacking of 12 robustly detected DSFGs recovers 39.1 sigma etc.  
  > "yields stacked detections of 39.1–$\sigma$, 37.3–$\sigma$, 29.9–$\sigma$, and 7.1–$\sigma$, for equal, $pbcor$, $F_{\mathrm{UV}}$, and $\mu$-weighting" (Appendix A)
7. **Fit M*-beta relation**: Third- and first-order polynomial fits to M* vs beta  
  > "applying a third-order polynomial fit to our $\mathrm{M}_{\bigstar}$ and $\beta$ values, we find" (5.1.5 M-beta correlation)
   - fitting: polynomial fit, method not stated  
  > "Nonetheless, applying a third-order polynomial fit to our $\mathrm{M}_{\bigstar}$ and $\beta$ values, we find" (Discussion, M-beta correlation)
   - validation: Consistent with Dunlop+17-type fit within 0.25 dex in mass-complete range  
  > "our fits appear to be consistent with that of , particularly in the low-redshift bin (within $0.25$ `dex`)" (5.1.5 M-beta correlation)

## Software

- **CASA** v4.2.2: Reduction, calibration and CLEAN imaging  
  > "Common Astronomy Software Applications (`CASA` v4.2.2; (cite: 2007ASPC..376..127M))" (2.1 ALMA data)
- **STACKER** : uv and image stacking  
  > "We used `STACKER` (cite: 2015MNRAS.446.3502L) to perform the stacking of our candidates in the ALMA images" (2.3 ALMA stacking considerations)
- **FAST++** : Photo-z, stellar mass, SFR  
  > "Stellar masses were estimated using `FAST++`, which fits stellar population synthesis templates to photometric data." (2.7 Stellar masses)
- **emcee** : Fitting UV slope beta  
  > "using the `Python` implementation of the Affine Invariant Markov chain Monte Carlo Ensemble sampler (cite: 2013PASP..125..306F)" (2.6 UV-continuum slope)
- **GALFIT** : Removing foreground cluster galaxies (B19)  
  > "Light from the foreground cluster galaxies and the intracluster medium was removed using GALFIT" (2.2 LBG candidates)
- **SExtractor** : Source catalogs  
  > "Source catalogs were then produced using SExtractor" (2.2 LBG candidates)
- **magphys** : Alternative SED fitting for comparison  
  > "We chose this method over `FAST++` or `magphys` (cite: 2008MNRAS.388.1595D) SED fitting" (2.12 IR luminosities)
- **Astropy** : General analysis  
  > "This research made use of `Astropy`, a community-developed core `Python` package for Astronomy" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Individually detected LBGs (S/N>4.1) | 2 | not stated | sources | 3 | Two (2) LBG candidates were individually detected above a significance of $4.1{-}\sigma$ |
| LBG candidates analysed | 1582 | not stated | sources | 5 | we investigate the properties of the $1582$ candidates located within the FoVs of five ALMA-observed FFs. |
| Undetected LBGs stacked | 1580 | not stated | sources | 5 | which resulted in a sample of $1580$ undetected LBG candidates to stack |
| Highest individual S/N among non-detections (AS1063) | 4.21 | not stated | dimensionless | 3 | with a maximum value of S/N$=4.21$ for a candidate in AS1063 |
| Best stacked bin S/N (227 F_UV-weighted, 4<=z<7, -2<=beta<-1, natural) | 4.24 | not stated | dimensionless | 6 | $227$ $F_{\mathrm{UV}}$-weighted sources in the range $4.0 {\leq} z {<} 7.0$ and $-2.0 {\leq} \beta {<} {-}1.0$ with $\mathrm{S/N}_{\mathrm{peak}}^{\mathrm{stack}} {=} 4.24$ |
| Lowest stacked rms | ~5 | not stated | uJy | 6 | we achieve stacked $rms$ values as low as $\approx$5 $\mu$Jy |
| Detected source L_IR range | 10^11.3 - 10^11.9 | not stated | Lsun | 4 | $L_{\mathrm{IR}}{\sim}10^{11.3}$–$10^{11.9}$ $\mathrm{L_{\odot}}$ |
| M*-beta cubic fit | beta = -0.99 + 0.62X + 0.13X^2 + 0.02X^3, X=log(M*/1e10 Msun) | not stated | dimensionless | 7 | \beta = -0.99 + 0.62X + 0.13X^{2} + 0.02X^{3}, |
| M*-beta linear fit | beta = -1.08 + 0.40X | not stated | dimensionless | 7 | \beta = -1.08 + 0.40X, |
| Source-plane area | ~8 | not stated | arcmin^2 | 0 | a total source-plane area of ${\sim} 8$ arcmin${}^{2}$ over the five FFs clusters. |

## Qualitative findings

- Vast majority of IRX 3-sigma limits lie above local IRX-beta and IRX-M* relations; only 3 below M99  
  > "only $\mathbf{3}$ LBGs are constrained to lie below the M99 IRX-$\beta$ relation and none of them below any of the discussed IRX-$M_{\bigstar}$ relations." (6 Summary)
- Clear smooth trend of beta with stellar mass extends to low mass and blue beta  
  > "We observe a clear and smooth trend between $\mathrm{M}_{\bigstar}$ and $\beta$" (abstract)

## Claim tuples

- H: Can ALMA FF mosaics individually detect IR emission from LBGs? | E: Peak flux search at HST positions with FDR-calibrated threshold | R: Two candidates above S/N 4.1 (both AS1063); rest upper limits | F: Intrinsic IR emission of LBGs is faint; only two tentative detections | **supported**
- H: Do stacked LBG samples show IR emission and constrain IRX relations? | E: uv stacking with four weightings in bins of z, beta, M* | R: Only one bin at S/N 4.24, not robust; stacked IRX upper limits mostly above relations | F: No robust stacked detection; limits mild tension only for some high-z bins | **partially**
- H: Is there an M*-beta correlation extending to low mass? | E: Polynomial fits of beta vs M* for the LBG sample | R: Smooth trend toward bluer beta at lower mass | F: Consistent with metallicity-driven evolution | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Stacking used because few individual detections expected; IRX stacked as average of individual IRX  
  > "given the low number of expected detections, as stacked-averages" (Introduction)
- Alternative: Constant T_dust=35 K tested; lowers IRX ~0.5 dex at z>4  
  > "resulting in IR luminosity and IRX values drops of ${\sim} 0.5$ dex" (5.2 The role of dust temperature)
- How they decided it was enough: _not stated_
- Limitation (authors): Stellar masses below ~10^8.5 Msun likely incomplete; selection biases at low mass  
  > "we could have strong selection effects that bias the resulting fitted relations at low stellar masses." (5.1.5 M-beta correlation)
- Limitation (authors): Stacked values biased toward high-weight sources  
  > "our stacked result can be biased toward the candidates with the highest weights." (3.3 Considerations on stacking weighting)
- Caveat (inferred, ours): Single-band IR luminosity relies on assumed T_dust evolution extrapolated beyond z=4
- Caveat (inferred, ours): Magnification cap at 10 and photo-z uncertainties affect L_UV, M*
- Caveat (inferred, ours): LBG catalog (B19) is unpublished
- Caveat (inferred, ours): Peak pixel in a box biases fluxes high
- Caveat (inferred, ours): Stellar mass and beta derived from same photometry

## Reproducibility

- Data public (paper): ALMA data acknowledged by project code (archive data); lens models public from MAST  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00999.S, ADS/JAO.ALMA#2015.1.01425.S." (Acknowledgements)
- Products in archive: _not stated_
- Code: Individual properties for remaining targets available online; FAST++ public on GitHub  
  > "Properties for the remaining targets are available online." (Appendix C)
- Missing: B19 LBG catalogs
- Missing: STACKER configuration and CLEAN settings
- Missing: T_dust prescription implementation details
- Data volume (inferred): ~100-300 GB raw for 5 mosaics (126 pointings each)
- Score (inferred): 3/5, Public ALMA data and clear recipe, but depends on unpublished LBG catalogs and missing imaging/stacking parameters.
- Rediscovery candidate: no, Requires unpublished B19 catalogs and unspecified imaging/stacking parameters; results mostly upper limits.

## Links

- Method: (cite: 2015MNRAS.446.3502L) Lindroos et al. 2015 (STACKER code)
- Method: (cite: 2017A&A...597A..41G) González-López et al. 2017b (ALMA FF data reduction and detection procedure)
- Method: (cite: 2018A&A...620A.125M) Muñoz Arancibia et al. 2018 (FDR procedure)
- Companion: (cite: 2017A&A...597A..41G) (ALMA Frontier Fields Survey I)
- Companion: (cite: 2017A&A...608A.138G) (ALMA Frontier Fields Survey data on A370/AS1063)
- Related: Hubble Frontier Fields
- Related: ALMA Frontier Fields Survey

## Checks

```json
{
 "quotes": 86,
 "quotes_ok": 86,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 108,
  "stated": 70,
  "rate": 0.648
 },
 "evidence_ok": true
}
```

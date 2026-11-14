# Compact Starbursts in z ∼ 3-6 Submillimeter Galaxies Revealed by ALMA

`2015ApJ...810..133I` | The Astrophysical Journal 2015 | first author: Ikarashi, Soh | arXiv: 1411.5038 | DOI: 10.1088/0004-637X/810/2/133

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Are the starburst regions of z~3-6 SMGs compact enough to be progenitors of z~2 compact quiescent galaxies, as measured by ALMA 1100-um continuum sizes?  
  > "we need to image more typical SMGs with $L_{\rm IR}\sim 10^{12}$ L$_{\odot}$." (Introduction); "We demonstrate that they have the compact starburst nuclei necessary to produce the small structures that typify cQGs." (Introduction)
- Target **13 ASXDF SMGs in SXDF (e.g. ASXDF1100.013.1, 027.1, 053.1)**: coordinates Per-source RA/Dec in Table 1 (e.g. 02:16:45.86, -5:03:47.2 for ASXDF1100.013.1)  
  > "we observed 30 AzTEC sources in the Subaru/XMM-Newton Deep field (SXDF), which includes the UKIDSS UDS field" (2 AzTEC-selected z>~3 SMGs); "| ASXDF1100.013.1    | 02:16:45.86        | $-$5:03:47.2       | 18.5 |" (Table 1); z/distance z_phot>=2.8 for 3 sources with photo-z; others lower limits from 4.5-um relation; z~3-6 assumed (stacked radio/mm colour gives z=4.0+/-0.4)  
  > "we observed 30 AzTEC sources in the Subaru/XMM-Newton Deep field (SXDF), which includes the UKIDSS UDS field" (2 AzTEC-selected z>~3 SMGs); "| ASXDF1100.013.1    | 02:16:45.86        | $-$5:03:47.2       | 18.5 |" (Table 1); distance from SED fitting following Caputi et al. 2012; 4.5um-z relation from ALESS; radio/mm colour (Carilli & Yun 1999)  
  > "we observed 30 AzTEC sources in the Subaru/XMM-Newton Deep field (SXDF), which includes the UKIDSS UDS field" (2 AzTEC-selected z>~3 SMGs); "| ASXDF1100.013.1    | 02:16:45.86        | $-$5:03:47.2       | 18.5 |" (Table 1)

## Data provenance

- ALMA projects: 2012.1.00326.S
- bands: _not stated_
- frequencies and spectral setup: continuum centered at 265 GHz (1100 um)  
  > "We measured the source sizes of our ASXDF sources using ALMA continuum data centered at 265 GHz." (3.1 Data, method and results)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: 25 12-m antennas (baselines up to 400 klambda, 440 m) for 7 sources; 28 antennas with extended baselines up to 1200 klambda (1320 m) for 6 sources  
  > "Seven of the 13 ASXDF sources were observed with 25 working 12-m antennas, mainly covering baselines up to 400 k$\lambda$, corresponding to physical baseline lengths of 440 m." (3.1 Data, method and results); "The remaining six sources were observed with three more 12-m antennas, deployed for tests on longer baselines, covering up to 1200 k$\lambda$ or 1320 m." (3.1 Data, method and results)
- baselines: _not stated_
- angular resolution: ~0.7" (baselines <=400 klambda); 0.23" x 0.19" (PA=21 deg) for high-res images (200-1200 klambda)  
  > "The synthesized beam size in our ALMA continuum images, using baselines up to 400 k$\lambda$, is $\sim 0''.7$ (FWHM)" (3.1 Data, method and results); "The resultant synthesized beam is 0$''$.23 $\times$ 0$''$.19 (PA $=$ 21$^{\circ}$)." (3.2 Ancillary long-baseline data)
- max recoverable scale: _not stated_
- sensitivity: rms 70-88 uJy/beam (<=400 klambda images)  
  > "sufficient to achieve r.m.s. noise levels of 70–88 $\mu$Jy beam$^{-1}$" (3.1 Data, method and results)
- time on source: 3.6-4.5 minutes  
  > "On-source observation times were 3.6–4.5 minutes" (3.1 Data, method and results)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **Herschel (PACS/SPIRE)**: Faintness selection and stacked FIR fluxes  
  > "We selected our ALMA targets based on their faintness in the $\it Herschel$ images (cite: oli12)" (2 AzTEC-selected z>~3 SMGs)
- Other facility **VLA 1.4 GHz**: Radio faintness selection and stacked flux (15.2+/-2.4 uJy)  
  > "Given a stacked VLA 1.4-GHz flux density of $15.2\pm 2.4$ $\mu$Jy" (2 AzTEC-selected z>~3 SMGs)
- Other facility **Optical-IRAC photometry (SXDF/UDS)**: 12-band SED photo-z  
  > "we have performed the spectral energy distribution (SED) analysis of our sources based on 12 bands" (2 AzTEC-selected z>~3 SMGs)
- Other facility **AzTEC/ASTE**: 1100-um parent map selecting the targets  
  > "The AzTEC 1100-$\mu$m map contains a total of 221 millimeter sources over a contiguous area of 950 arcmin$^2$." (2 AzTEC-selected z>~3 SMGs)
- External data: Local (U)LIRG and disk Sigma_SFR from surface IR luminosity densities  
  > "$\Sigma_{\rm SFR}$ for local merger-driven (U)LIRGs is 5–4500 M$_{\odot}$ yr$^{-1}$ kpc$^{-2}$ with a median of 29$^{+24}_{-12}$" (6 Surface SFR density) [from (cite: ruj11)]
- External data: High-z disk galaxy CO sizes (4 BzK and 14 disks)  
  > "We took four BzK galaxies at $z\sim$ 1.5 with CO $J$=2–1 sizes from (cite: dad10) and 14 high-redshift disk galaxies" (6 Surface SFR density) [from (cite: dad10); (cite: tac13)]
- External data: Radio and CO sizes of z~1-3 SMGs (~0.5")  
  > "median radius of 0$''$.5 or 2.5 kpc as measured via radio continuum – (cite: big08) – or $\sim 0''.5$ or 2 kpc as measured via high-$J$ CO emission – (cite: tac06)" (4 Are z~3-6 SMGs more compact) [from (cite: big08); (cite: tac06)]
- External data: NIR sizes of cQGs and cSFGs  
  > "We plot the sizes of $z\gtrsim3$ SMGs alongside the NIR sizes of compact star-forming galaxies (cSFGs) at $z\sim 2$–2.5 (cite: bar14) and cQGs (cite: kro13)" (5 progenitors of cQGs) [from (cite: bar14); (cite: kro13)]
- External data: ALESS average SED/template used for SFR, L_IR and 4.5um-z relation  
  > "The SFRs and $L_{\rm IR}$ are estimated from the average SMG SEDs." (2 AzTEC-selected z>~3 SMGs) [from (cite: sim14); (cite: swi14)]
- Simulation/model as data: Monte-Carlo: 82000 mock Gaussian sources in noisy visibilities to calibrate size measurement bias  
  > "We generated 82000 mock sources with a symmetric Gaussian profile in noisy visibility data" (3.1 Data, method and results)

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

- task: CASA clean for continuum images; imfit for image-plane fits  
  > "All of our sample shows the millimeter sizes of $\gtrsim2$ times smaller than the beam size by a CASA task, imfit" (3.1 Data, method and results)
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
- array combination: high-res images use only 200-1200 klambda baselines; extended-baseline data used as supplementary  
  > "we created high-angular-resolution ALMA millimeter continuum images (hereafter high-res images) using 200–1200 k$\lambda$ baselines" (3.2 Ancillary long-baseline data)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: high-res rms 122-126 uJy/beam individually; 88 (stacked faint), 67 (stacked all)  
  > "are 126, 124, 124, 122, 122, 126, 88 and 67 $\mu$Jy beam$^{-1}$, respectively" (3.2 Ancillary long-baseline data)

### Inherited from earlier work

- SED/photo-z method  
  > "using the same method described in (cite: cap12)" (2 AzTEC-selected z>~3 SMGs) [from (cite: cap12)]
- uv-amplitude Gaussian size-fitting approach  
  > "assuming a symmetrical Gaussian[^1] as was done in previous studies" (3.1 Data, method and results) [from (cite: ion06; you08; ivi10; ika11)]
- Visibility stacking with CASA code stacker  
  > "we stacked the visibility data of these four sources using the CASA code, stacker (cite: lin15)" (3.2 Ancillary long-baseline data) [from (cite: lin15)]
- Further program details deferred  
  > "Our ALMA program (2012.1.00326.S, P.I. Ikarashi; Ikarashi et al. in prep)" (2 AzTEC-selected z>~3 SMGs) [from Ikarashi et al. in prep]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration procedure (manual vs pipeline), calibrators and flux scale
- Clean parameters: weighting/robust, cell size, image size, masks, threshold
- Exact model fitting of uv-amp plots (binning, fit parameter errors, uv range)
- Details of the size-correction probability map from simulations
- Mock source parameter grid and noise generation
- Conversion from L_IR/SFR (SED template, T_d=32 K, IMF details) to SFR values
- Bootstrapping details for stacking and Sigma_SFR distribution
- Spectral setup/bandwidth and spectral windows

## Analysis recipe

1. **Select sample and estimate redshifts**: 13 of 17 sources with S/N>=10 selected with z_phot>=2.8 or IRAC-faint (F4.5>=22.75 mAB) and detected in <=4 bands; minimum z from 4.5um-z relation; stacked radio/mm colour gives z=4.0  
  > "we analyse here only the 13 (out of 17) sources that have photometric redshifts $z_{\rm phot}\geq2.8$" (2 AzTEC-selected z>~3 SMGs)
   - assumption: Average ALESS SMG template valid at z>3 (Td=32 K)  
  > "Here we are assuming that this template is also valid at $z\gtrsim3$–4." (2 AzTEC-selected z>~3 SMGs)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure sizes from uv-amplitude plots**: Fit symmetric Gaussian to visibilities (<=400 klambda) for >=10 sigma sources  
  > "we have measured source sizes using the visibility data directly – on $uv$–amplitude plots" (3.1 Data, method and results)
   - software: CASA
   - parameter: S/N>=10 threshold  
  > "we measure millimeter size of ASXDF sources with $\geq10\sigma$ continuum detections" (3.1 Data, method and results)
   - assumption: Symmetric Gaussian profile  
  > "assuming a symmetrical Gaussian" (3.1 Data, method and results)
   - fitting: _not stated_
   - validation: Monte-Carlo with 82000 mock sources  
  > "This plot demonstrates that our source size measurement is accurate to within 1$\sigma$" (3.1 Data, method and results)
3. **Correct sizes for measurement bias**: Use probability distribution of actual size for given S/N and measured size from simulations  
  > "the correction is done using the probability distribution of actual source size for the appropriate signal-to-noise ratio and measured size of each source" (3.1 Data, method and results)
   - fitting: _not stated_
   - validation: Ellipticity dependence tested with axis ratios 0.5-1.0; overestimate ~10% at 0.5  
  > "at an axis ratio of 0.5, the circularized size can be over-estimated about 10 percent" (3.1 Data, method and results)
4. **Check with long-baseline high-res images and stacking**: Image 200-1200 klambda data, imfit, compare image flux with visibility flux at 200 klambda; stack visibilities of faint sources  
  > "we compare fluxes measured using imfit on the high-res ALMA images with fluxes expected at a $uv$-distance of $\geq200$ k$\lambda$" (3.2 Ancillary long-baseline data)
   - software: CASA imfit, stacker
   - fitting: _not stated_
   - validation: Imfit ellipticity bias tested by Monte Carlo  
  > "imfit tends to return major/minor axis ratio of $<1$ even for input axis ratio of 1" (3.2 Ancillary long-baseline data)
5. **Convert to physical size, Sigma_SFR and compare with other populations**: Angular to physical size with uniform z=3-6 probability or photo-z error; Sigma_SFR from SFR and R_c,e; KS tests vs radio/CO sizes and local/high-z disks; bootstrapping  
  > "we assume uniform redshift probability at $z=$3–6 for sources without photo-$z$" (4 Are z~3-6 SMGs more compact)
   - assumption: H0=70, OmegaM=0.3, OmegaL=0.7  
  > "$H_{\rm 0}= 70$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_{\rm M}= 0.3$ and $\Omega_{\rm \Lambda}= 0.7$" (Introduction)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : imaging and imfit source fitting; stacker code runs in CASA  
  > "We measured their millimeter sizes and fluxes in the image using a CASA task, imfit" (3.2 Ancillary long-baseline data)
- **stacker** : visibility stacking of faint sources  
  > "using the CASA code, stacker (cite: lin15)" (3.2 Ancillary long-baseline data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median FWHM size | 0.20 | +0.03/-0.05 | arcsec | 3 | with a median of 0$''$.20$^{+0''.03}_{-0''.05}$ (FWHM) |
| Median circularized effective radius R_c,e | 0.67 | +0.13/-0.14 | kpc | 5 | 0.67$^{+0.13}_{-0.14}$ kpc |
| Median Sigma_SFR | 100 | +42/-26 | Msun/yr/kpc^2 | 5 | 100$^{+42}_{-26}$ M$_{\odot}$ yr$^{-1}$ kpc$^{-2}$ |
| Median SFR | 340 | +12/-13 | Msun/yr | 1 | 340$^{+12}_{-13}$ M$_{\odot}$ yr$^{-1}$ |
| Image/visibility flux ratio at 200 klambda | 1.07 | +0.08/-0.09 | dimensionless | 4 | F_{\rm image, 200\,k\lambda} = 1.07^{+0.08}_{-0.09} \times F_{\rm visibility, 200\,k\lambda} |
| Stacked radio/mm photometric redshift | 4.0 | +/-0.4 | dimensionless | 1 | we expect a photometric redshift, $z=4.0^{+0.4}_{-0.4}$ |
| KS probability, radio vs mm sizes (with 0.86 correction) | 3.5 | not stated | percent | 5 | gives 3.5 per cent that the differences between radio and millimeter sizes could arise by chance |

## Qualitative findings

- ~100% of rest-frame FIR emission in the sources comes from the compact component  
  > "This indicates that $\sim$ 100 percent of the rest-frame FIR emission in $z\gtrsim3$ ASXDF sources comes from the compact component" (3.2 Ancillary long-baseline data)
- Sigma_SFR is similar to local (U)LIRGs, not disks; merger vs disk-instability trigger cannot be distinguished  
  > "Thus at this stage we cannot distinguish the trigger of starbursts of $z\gtrsim3$ SMGs by their compact size." (6 Surface SFR density)

## Claim tuples

- H: z>~3 SMGs have compact star-forming regions smaller than z~1-3 SMGs | E: uv-amplitude Gaussian size fitting with Monte Carlo correction, compared with radio/CO sizes via KS test | R: median R_c,e 0.67 kpc, >2x smaller than radio/CO sizes; KS probability 3.5% | F: z>~3 SMGs have more compact star formation than z~1-3 SMGs | **supported**
- H: z>~3 SMGs are progenitors of z~2 compact quiescent galaxies | E: Compare SMG sizes with NIR sizes of cQGs and cSFGs | R: SMG sizes comparable to or smaller than cQG stellar sizes | F: Supports SMG to cQG to massive elliptical evolution | **supported**
- H: The compact starbursts resemble local merger-driven (U)LIRGs rather than extended disks | E: Sigma_SFR distribution vs local ULIRGs and disks with KS tests | R: median Sigma_SFR 100 vs 29 (ULIRGs); 0% KS match with disks | F: Compact nuclear starbursts like local (U)LIRGs | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Beam of ~0.7" too coarse to resolve; uv-amp fitting exploits long-baseline data for unresolved sources  
  > "too coarse to allow us to resolve any compact starburst nuclei in high-redshift SMGs" (3.1 Data, method and results)
- How they decided it was enough: _not stated_
- Limitation (authors): Large Sigma_SFR uncertainties for ~0.1" sources; only 13 sources; redshifts mostly lower limits  
  > "This large uncertainty comes from the limit of size measurement in our data set." (6 Surface SFR density)
- Caveat (inferred, ours): Most redshifts are not spectroscopic; distances assumed uniformly distributed over z=3-6
- Caveat (inferred, ours): Gaussian assumption and size correction depend on simulation priors
- Caveat (inferred, ours): Sample selected for S/N>=10, Herschel/radio faintness; possible biases
- Caveat (inferred, ours): Comparison with radio/CO sizes involves differing methods and luminosities

## Reproducibility

- Data public (paper): ALMA data acknowledged as ADS/JAO.ALMA#2012.1.00326.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00326.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Calibration and imaging parameters
- Missing: Details of simulation-based correction and Monte-Carlo grid
- Missing: SED templates and exact L_IR/SFR conversion
- Missing: Photometric catalogs
- Data volume (inferred): ~tens of GB (30 fields, short scans, 1 band)
- Score (inferred): 3/5, Public data and clear approach, but imaging, calibration and fitting details are missing and key methods are deferred to in-prep papers.
- Rediscovery candidate: no, Recipe incomplete (simulation correction, calibration unspecified) though data are public.

## Links

- Method: (cite: lin15) (visibility stacking code stacker)
- Method: (cite: cap12) (SED photo-z method)
- Companion: Ikarashi et al. in prep (program and SED analysis details)
- Companion: (cite: sim15) (ALMA 870um sizes of SCUBA2 SMGs for comparison)
- Related: ALESS
- Related: AzTEC SXDF survey
- Related: UKIDSS UDS

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 45,
  "rate": 0.556
 },
 "evidence_ok": true
}
```

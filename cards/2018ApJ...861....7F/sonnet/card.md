# ALMA 26 Arcmin<SUP>2</SUP> Survey of GOODS-S at One Millimeter (ASAGAO): Average Morphology of High-z Dusty Star-forming Galaxies in an Exponential Disk (n ≃ 1)

`2018ApJ...861....7F` | The Astrophysical Journal 2018 | first author: Fujimoto, Seiji | arXiv: 1802.02136 | DOI: 10.3847/1538-4357/aac6c4

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the average rest-frame FIR Sérsic index and effective radius of faint dusty star-forming galaxies at z=1-3, and how do they compare with the rest-frame optical morphology and with compact quiescent galaxies?  
  > "we perform $n_{\rm FIR}$ and $R_{\rm e,FIR}$ measurements for faint SMGs via the stacking technique on the $uv$-visibility plane" (1 Introduction)
- Target **ASAGAO sources in GOODS-S (33 at z=1-3 stacked; 42 in catalog)**: coordinates GOODS-S field (source positions in Table)  
  > "ALMA Band 6 observations over an area of $\sim$26 arcmin$^{2}$ in The Great Observatories Origins Deep Survey South" (2 Data and Reduction); z/distance z=0.66-4.36, median 1.97 (z=1-3 used for stacking)  
  > "ALMA Band 6 observations over an area of $\sim$26 arcmin$^{2}$ in The Great Observatories Origins Deep Survey South" (2 Data and Reduction); distance from ZFOURGE catalog photometric/spectroscopic redshifts (Straatman et al. 2016)  
  > "ALMA Band 6 observations over an area of $\sim$26 arcmin$^{2}$ in The Great Observatories Origins Deep Survey South" (2 Data and Reduction)
- Target **Archive bright SMGs (12 sources)**: coordinates see Additional Source Catalog table  
  > "We select 12 individual ALMA sources detected with S/N $>$ 15 in the natural-weighted ALMA maps with synthesized beam size of $<0.3\ensuremath{''}$" (3.6 Additional Sample from Archive); z/distance z=1-3 (z_phot in table)  
  > "We select 12 individual ALMA sources detected with S/N $>$ 15 in the natural-weighted ALMA maps with synthesized beam size of $<0.3\ensuremath{''}$" (3.6 Additional Sample from Archive); distance from optical-NIR counterparts, from Fujimoto et al. 2017 catalog  
  > "We select 12 individual ALMA sources detected with S/N $>$ 15 in the natural-weighted ALMA maps with synthesized beam size of $<0.3\ensuremath{''}$" (3.6 Additional Sample from Archive)

## Data provenance

- ALMA projects: 2015.1.00098.S, 2013.1.00781.S, 2012.1.00307.S, 2013.1.00576.S
- bands: Band 6 (1.14 and 1.18 mm tunings)  
  > "in the two tunings centered at 1.14 mm and 1.18mm" (2 Data and Reduction)
- frequencies and spectral setup: 244-248, 253-257, 259-263, 268-272 GHz  
  > "where the frequency coverages were 244$-$248 GHz, 253$-$257 GHz, 259$-$263 GHz, and 268$-$272 GHz" (2 Data and Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-6, 38-45 antennas  
  > "The array configuration was C40-6 with 38$-$45 antennas" (2 Data and Reduction)
- baselines: 15-3247 m  
  > "baseline length takes a range of 15$-$3247 m" (2 Data and Reduction)
- angular resolution: HR 0.21"x0.17"; LR (taper) 0.94"x0.67"  
  > "synthesized beam size of $0.21\ensuremath{''}\times0.17\ensuremath{''}$ and an rms noise level of 38 $\mu$Jy/beam" (2 Data and Reduction)
- max recoverable scale: _not stated_
- sensitivity: 38 uJy/beam (HR), 87 uJy/beam (LR)  
  > "rms noise level is 87 $\mu$Jy/beam" (2 Data and Reduction)
- time on source: 45 hours total observing time  
  > "with a total observing time of 45 hours" (2 Data and Reduction)
- observing dates: September 2016  
  > "In September 2016, the ASAGAO survey carried out ALMA Band 6 observations" (2 Data and Reduction)
- pi or archival as stated: ASAGAO PI K. Kohno; plus archival ALMA sources  
  > "ALMA project ID: 2015.1.00098.S, PI: K. Kohno" (2 Data and Reduction)
- Other facility **HST**: Rest-frame optical/UV morphology (van der Wel catalog, Kartaltepe classification, F606W stacking)  
  > "utilizing the NIR HST catalogs in GOODS-S" (3.3 Multi-wavelength Properties of Our Sample)
- Other facility **Spitzer/MIPS, Herschel PACS/SPIRE, ZFOURGE**: Multiwavelength photometry for SED fitting  
  > "include $Spitzer$/MIPS (Rieke et al. 2004, 24 $\mu$m), $Herschel$/PACS (Poglitsch et al. 2010, 100 and 160 $\mu$m)" (3.3 Multi-wavelength Properties of Our Sample)
- Other facility **Gaia DR1**: Astrometric offset calibration of ZFOURGE  
  > "which are calibrated by stars in the Gaia Data Release 1 catalog" (3.1 Source Detection and Catalog)
- External data: ZFOURGE optical-NIR catalog and redshifts  
  > "The values of $z_{\rm spec}$ and $z_{\rm phot}$ values are obtained from the ZFOURGE catalog" (3.3 Multi-wavelength Properties of Our Sample) [from Straatman et al. 2016 (cite: straatman2016)]
- External data: HST n_opt and Re_opt  
  > "cross-matched within a radius of $0.5\ensuremath{''}$ with the catalog of (cite: vanderwel2014)" (3.3 Multi-wavelength Properties of Our Sample) [from van der Wel et al. 2014 (cite: vanderwel2014)]
- External data: Visual morphological classification  
  > "we carry out the same cross-matching procedure with the NIR catalog of (cite: kartaltepe2015)" (3.3 Multi-wavelength Properties of Our Sample) [from Kartaltepe et al. 2015 (cite: kartaltepe2015)]
- External data: Archive ALMA source catalog (1034 sources)  
  > "We use the ALMA source catalog of (cite: fujimoto2017), where 1034 ALMA sources (S/N$\geq$5) are identified" (3.6 Additional Sample from Archive) [from Fujimoto et al. 2017 (cite: fujimoto2017)]

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

- task: tclean, CLEAN boxes at S/N>=5 peaks (manual)  
  > "The entire map was produced by the CLEAN algorithm with the tclean task." (2 Data and Reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting (HR)  
  > "The final natural-weighted image is characterized by a synthesized beam size" (2 Data and Reduction)
- uv taper: 160 klambda (LR map)  
  > "a $uv$-taper of 160 k$\lambda$" (2 Data and Reduction)
- cell size: _not stated_
- image size: _not stated_
- masking: circle radius 1.0" at peak pixels S/N>=5; cleaned to 2 sigma  
  > "For the CLEAN box, we adopt a circle with a radius of $1.0\ensuremath{''}$." (2 Data and Reduction)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.21"x0.17" HR; 0.94"x0.67" LR  
  > "final synthesized beam size is $0.94\ensuremath{''}\times0.67\ensuremath{''}$" (2 Data and Reduction)
- final rms: 38 uJy/beam HR; 87 uJy/beam LR; stacked 8.1 uJy/beam  
  > "where the rms noise achieves 8.1 $\mu$Jy/beam" (3.4 Visibility-based Stacking)

### Inherited from earlier work

- Calibration and reduction details  
  > "The details of the data calibration and reduction are described in Hatsukade et al. (in prep.)." (2 Data and Reduction) [from Hatsukade et al. (in prep.)]
- Source selection/counterpart process and SED properties  
  > "The details of the selection process are presented in Yamaguchi et al. (in prep.)." (3.1 Source Detection and Catalog) [from Yamaguchi et al. (in prep.)]
- Herschel SPIRE de-blending  
  > "where we perform the de-blending technique in almost the same manner as (cite: liu2018)" (3.3 Multi-wavelength Properties of Our Sample) [from (cite: liu2018); Wang et al. (in prep.)]
- L_IR for archive sources via modified blackbody Td=35 K, beta=1.8  
  > "we calculate $L_{\rm IR}$ in the same manner as (cite: fujimoto2017)" (3.6 Additional Sample from Archive) [from (cite: fujimoto2017)]

### Not stated but needed to reproduce (our reading)

- Robust/weighting details and channel selection for continuum imaging; calibration pipeline/CASA version
- Which archive projects map to which of the 12 additional sources
- Bootstrap details for galfit errors and exact MC correction tables
- Self-calibration and flux scale details
- gas fraction and SFR/Mstar profile model details for evolution calculation
- Stacker settings and weighting

## Analysis recipe

1. **Image ASAGAO HR and LR maps**: tclean natural weighting; LR with 160 klambda uv-taper  
  > "We also produced another map with a $uv$-taper of 160 k$\lambda$" (2 Data and Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Detect sources and build catalog**: 3.5 sigma peaks in LR map; ZFOURGE counterparts within 0.5" and magphys flux consistency within 3 sigma  
  > "We find that 42 out of 87 ALMA sources have reliable optical-NIR counterparts, which we refer to as the ASAGAO catalog." (3.1 Source Detection and Catalog)
   - software: magphys
   - fitting: _not stated_
   - validation: chance-projection probability P~0.03 gives ~19 expected spurious of 87  
  > "indicating that the ASAGAO catalog maintains a high purity of the real sources" (3.1 Source Detection and Catalog)
3. **Measure fluxes and positions**: aegean Gaussian fitting for flux; peak pixel positions in LR map chosen from MC test  
  > "We thus measure the ASAGAO source centers based on the peak pixel positions in the LR map." (3.2 Flux and Position Measurement)
   - software: aegean, BANE
   - fitting: _not stated_
   - validation: 1000 injected MC sources; average offset ~0.06" LR vs ~0.10" HR  
  > "the average offset is $\sim$$0.06\ensuremath{''}$ in the LR map and $\sim$$0.10\ensuremath{''}$ in the HR map" (3.2 Flux and Position Measurement)
4. **Stack 33 z=1-3 sources in uv plane**: visibility stacking centered on LR peak positions  
  > "we use only 33 ASAGAO sources that are located at $z=1-3$ for the stacking" (3.4 Visibility-based Stacking)
   - software: stacker
   - fitting: _not stated_
   - validation: 29 sigma peak  
  > "shows a 29$\sigma$ significance level" (3.4 Visibility-based Stacking)
5. **Fit Sérsic profile to stack**: galfit on 1.6"x1.6" HR map with synthesized beam image as PSF; cross-check with uvmultifit at n=1  
  > "We adopt $n=1$, $R_{\rm e}=0.2\ensuremath{''}$, total flux density of 1.0 mJy, axis ratio of 1.0, and position angle of 0 deg as initial parameters" (3.5 n_FIR and R_e,FIR Measurements)
   - software: galfit, uvmultifit
   - parameter: sky fixed at 0; center fixed at image center  
  > "where the sky value is fixed at 0. The source center is fixed at the image center." (3.5 n_FIR and R_e,FIR Measurements)
   - fitting: galfit chi-square; errors by bootstrap  
  > "where the errors are evaluated by the bootstrap method" (3.5 n_FIR and R_e,FIR Measurements)
   - validation: uvmultifit Re=0.10"+-0.03" consistent  
  > "The best-fit $R_{\rm e,FIR}$ is estimated to be $0.10\ensuremath{''}\pm0.03\ensuremath{''}$" (3.5 n_FIR and R_e,FIR Measurements)
6. **Correct for positional smoothing via MC**: inject 33 model sources with Gaussian offsets (mean 0.06", sd 0.01"), average profile, chi-square fit, 2000 trials over n=0.5-4, Re=0.04-0.4"  
  > "We repeat this process 2,000 times, changing the S$\acute{\rm e}$rsic profile of the model sources in the ranges of $n=0.5-4.0$ and $R_{\rm e}=0.04\ensuremath{''}-0.4\ensuremath{''}$." (3.5 n_FIR and R_e,FIR Measurements)
   - assumption: axis ratio 0.75 for model sources  
  > "create 33 model sources that have the same S$\acute{\rm e}$rsic profile with a fixed axis ratio of 0.75" (3.5 n_FIR and R_e,FIR Measurements)
   - fitting: minimum chi-square  
  > "Finally, we estimate the best-fit S$\acute{\rm e}$rsic profile to obtain $n$ and $R_{\rm e}$ by the minimum chi-square method for the average radial profile." (3.5 n_FIR and R_e,FIR Measurements)
   - validation: _not stated_
7. **Two-component fit for central compact component**: galfit bulge+disk and PS+disk fits  
  > "we conduct a two-component fitting with galfit for the $1.6\ensuremath{''}\times1.6\ensuremath{''}$ HR map of the stacked source" (5.1 Compact Dusty Bulge vs AGN)
   - software: galfit
   - fitting: disk Re fixed, positions fixed  
  > "where $R_{\rm e}$ of the disk component is fixed to obtain stable results. The central position of each component is also fixed at the image center." (5.1 Compact Dusty Bulge vs AGN)
   - validation: compared to AGN fraction from Dunlop+2017  
  > "a contribution of the AGN to the total flux density is estimated to be $\sim0.5\%$ at the $\sim$1-mm flux density by fitting the composite star-forming + AGN template for the 16 ALMA sources in (cite: dunlop2017)" (5.1 Compact Dusty Bulge vs AGN)
8. **Archive bright SMG sizes**: galfit individually, no stacking correction  
  > "The $n_{\rm FIR}$ and $R_{\rm e, FIR}$ values are individually estimated with galfit in the same manner as the stacked source" (3.6 Additional Sample from Archive)
   - software: galfit
   - fitting: _not stated_
   - validation: _not stated_
9. **Optical morphology and statistics**: van der Wel catalog n_opt, Re_opt; KS and Spearman tests; constant fits  
  > "We thus fit constant values to both $n_{\rm opt}$ and $R_{\rm e,opt}$ of the ASAGAO and the ALESS sources" (4.2 Optical Size and Morphology)
   - fitting: _not stated_
   - validation: _not stated_
10. **Model evolution to compact quiescent galaxies**: Sum of Sigma Mstar and Sigma SFR(UV+FIR) x dt; HST F606W stacking for UV profile  
  > "estimated from the sum of the $\Sigma M_{\rm star}$ and $\Sigma$SFR$_{\rm UV+FIR}$$\times$$\Delta t$" (5.2 Evolutions of Size and Morphology)
   - software: galfit
   - parameter: dt = depletion time (~640 and 210 Myr) or ~1.0 Gyr  
  > "The depletion times are estimated to be $\sim$ 640 and 210 ${\rm Myr}$ for the high-$z$ LIRGs and ULIRGs, respectively." (5.2 Evolutions of Size and Morphology)
   - assumption: constant SFR, no radial motions of stars  
  > "Assuming a constant SFR during a time scale $\Delta t$ and no radial motions of the stars" (5.2 Evolutions of Size and Morphology)
   - fitting: _not stated_
   - validation: compared with z~1-2 quiescent galaxy distributions  
  > "For comparison, the distributions of $z\sim2-3$ star-forming and $z\sim1$$-$2 quiescent galaxies are also presented with the blue and black shaded regions, respectively." (5.2 Evolutions of Size and Morphology)

## Software

- **CASA** : data reduction and tclean imaging  
  > "The data were reduced with the Common Astronomy Software Applications package" (2 Data and Reduction)
- **aegean** : flux density and noise  
  > "we use aegean (cite: hancock2012)" (3.2 Flux and Position Measurement)
- **BANE** : background and noise estimation  
  > "The background and noise are estimated with the BANE package" (3.2 Flux and Position Measurement)
- **magphys** : SED fitting for SFR, Mstar, LIR  
  > "derived with magphys (cite: dacunha2008)" (3.3 Multi-wavelength Properties of Our Sample)
- **stacker** : uv visibility stacking  
  > "We perform the stacking analysis with stacker (cite: lindroos2015)" (3.4 Visibility-based Stacking)
- **galfit** : Sérsic profile fitting  
  > "with galfit (cite: peng2010) which is a profile fitting tool on the image plane" (3.5 n_FIR and R_e,FIR Measurements)
- **uvmultifit** : uv-plane size fit with n=1  
  > "we also use uvmultifit (cite: marti2014)" (3.5 n_FIR and R_e,FIR Measurements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Stack n_FIR (galfit, uncorrected) | 0.96 | 0.10 | dimensionless | 5 | $n_{\rm FIR}=0.96\pm0.10$ and $R_{\rm e,FIR}=0.11\ensuremath{''}\pm0.02\ensuremath{''}$ |
| Stack n_FIR corrected | 1.2 | 0.2 | dimensionless | 6 | obtain $n=1.2\pm0.2$ and $R_{\rm e,FIR}=0.12\ensuremath{''}\pm0.03\ensuremath{''}$ |
| Stack R_e,FIR | 1.0 | 0.2 | kpc | 6 | $R_{\rm e,FIR}$ is estimated to be 1.0$\pm$0.2 kpc |
| Archive sample median n_FIR | 1.1 | 0.3 | dimensionless | 8 | $n_{\rm FIR}=1.1\pm0.3$ and $R_{\rm e, FIR}=1.3\pm0.8$ kpc |
| Archive sample median R_e,FIR | 1.3 | 0.8 | kpc | 8 | $n_{\rm FIR}=1.1\pm0.3$ and $R_{\rm e, FIR}=1.3\pm0.8$ kpc |
| n_opt best fit | 0.9 | 0.3 | dimensionless | 9 | $n_{\rm opt}=0.9\pm0.3$ and $R_{\rm e,opt}=3.2\pm0.6$ kpc |
| R_e,opt best fit | 3.2 | 0.6 | kpc | 9 | $n_{\rm opt}=0.9\pm0.3$ and $R_{\rm e,opt}=3.2\pm0.6$ kpc |
| Point-source flux fraction | 1.5 | 0.5 | % | 7 | we obtain the PS component contribution to the total flux density as $1.5\pm0.5\%$ |
| Stack S/N | 29 | not stated | sigma | 4 | shows a 29$\sigma$ significance level |

## Qualitative findings

- Dusty star-forming galaxies have exponential-disk FIR profiles, smaller than optical sizes; model reproduces size decrease but not n increase to cQGs.  
  > "The average FIR profile agrees with a morphology of an exponential-disk clearly distinguished from a deVaucouleurs-spheroidal profile" (abstract)

## Claim tuples

- H: Faint dusty SF galaxies have exponential-disk FIR morphology | E: uv stacking of 33 sources plus galfit with MC correction | R: n_FIR=1.2±0.2, Re=1.0±0.2 kpc | F: Exponential disk, n~1 | **supported**
- H: FIR and optical morphology differ | E: Compare with HST n_opt, Re_opt | R: n_opt=0.9±0.3, Re_opt=3.2±0.6 kpc | F: Compact dusty disk embedded in larger stellar disk | **supported**
- H: Central compact component origin is AGN or bulge | E: Two-component galfit fits | R: PS+disk equals bulge+disk; PS 1.5±0.5% | F: Likely AGN, bulge not excluded | **partially**
- H: Constant SFR in dusty SFGs builds cQGs | E: Mstar+SFR profile evolution model | R: Re decrease reproduced, n increase not | F: Other mechanisms such as dynamical dissipation needed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: LR map used for detection for surface brightness sensitivity; position from LR map due to lower offset  
  > "Here we use the LR map to improve the surface brightness sensitivity" (3.1 Source Detection and Catalog)
- Alternative: HR map positions rejected (larger offsets) in favour of LR  
  > "The MC simulation results show that the average offset is $\sim$$0.06\ensuremath{''}$ in the LR map and $\sim$$0.10\ensuremath{''}$ in the HR map." (3.2 Flux and Position Measurement)
- How they decided it was enough: _not stated_
- Limitation (authors): Cannot distinguish n~1 vs 4 beyond r>0.4"  
  > "one cannot conclude whether $n_{\rm FIR}\sim1$ or $n_{\rm FIR}\sim4$ is preferable in the range of radius $r>0.4\ensuremath{''}$" (3.5 n_FIR and R_e,FIR Measurements)
- Caveat (inferred, ours): Stack corrections depend on MC with assumed axis ratio and offset distribution
- Caveat (inferred, ours): Optical sample limited to H<24.5 (21 of 42)
- Caveat (inferred, ours): Stack of heterogeneous sizes assumed to represent a single profile

## Reproducibility

- Data public (paper): ALMA archive project codes given  
  > "This paper makes use of the following ALMA data: ADS/JAO. ALMA #2015.1.00098.S" (Acknowledgements)
- Products in archive: _not stated_
- Missing: Calibration/reduction in Hatsukade et al. (in prep.)
- Missing: Catalog selection and SED details in Yamaguchi et al. (in prep.)
- Missing: CASA version and robust/channel details
- Data volume (inferred): ~100-300 GB for ASAGAO uv data
- Score (inferred): 3/5, Public data and clear stacking/fitting recipe, but calibration and catalog details deferred to in-prep papers.
- Rediscovery candidate: no, Key steps (catalog, calibration) rely on unpublished companion papers and MC corrections are underspecified.

## Links

- Method: Lindroos et al. 2015 (cite: lindroos2015) (stacker uv stacking)
- Method: Peng et al. 2010 (cite: peng2010) (galfit)
- Companion: Hatsukade et al. (in prep.) (ASAGAO reduction and flux measurements)
- Companion: Yamaguchi et al. (in prep.) (ASAGAO catalog selection and physical properties)
- Companion: Fujimoto et al. 2017 (cite: fujimoto2017) (archive ALMA size catalog)
- Related: ASAGAO
- Related: ALESS
- Related: ZFOURGE
- Related: GOODS-S

## Checks

```json
{
 "quotes": 86,
 "quotes_ok": 86,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2012.1.00307.S",
  "2013.1.00576.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 101,
  "stated": 68,
  "rate": 0.673
 },
 "evidence_ok": true
}
```

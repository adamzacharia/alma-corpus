# An ALMA Survey of Sub-millimeter Galaxies in the Extended Chandra Deep Field South: Sub-millimeter Properties of Color-selected Galaxies

`2014ApJ...780..115D` | The Astrophysical Journal 2014 | first author: Decarli, R. | arXiv: 1311.2604 | DOI: 10.1088/0004-637X/780/2/115

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies
- Question: What are the sub-mm (344 GHz) properties, dust SEDs and SFRs of optical/NIR color-selected galaxies (K-selected, sBzK, ERO, DRG) in ALESS fields, as measured by stacking ALMA data?  
  > "We study the sub-mm properties of color–selected galaxies via a stacking analysis applied for the first time to interferometric data at sub-mm wavelengths." (abstract)
- Target **ALESS fields (LESS sources in the ECDFS)**: coordinates _not stated_; z/distance color-selected samples at 1<z<2.6 (mean z 1.5-1.9)  
  > "We base our study on 344 GHz ALMA continuum observations of $\sim20''$–wide fields centered on 86 sub-mm sources detected in the LABOCA Extended *Chandra* Deep Field South Sub-mm Survey (LESS)." (abstract); distance from photometric/spectroscopic redshifts from Simpson et al. 2014  
  > "We base our study on 344 GHz ALMA continuum observations of $\sim20''$–wide fields centered on 86 sub-mm sources detected in the LABOCA Extended *Chandra* Deep Field South Sub-mm Survey (LESS)." (abstract)

## Data provenance

- ALMA projects: 2011.1.00294.S
- bands: 344 GHz (870 um) continuum  
  > "These are 344 GHz observations of 122 sources." (The ALESS data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Cycle 0 compact configuration, longest baseline 125 m, mostly 15 antennas  
  > "with the array in ALMA Cycle 0’s compact configuration (longest baseline: 125m), mostly with 15 antennas." (The ALESS data)
- baselines: _not stated_
- angular resolution: ~1.6''x1.15''  
  > "The typical resolution element has a FWHM $\sim1.6''\times1.15''$." (The ALESS data)
- max recoverable scale: _not stated_
- sensitivity: typical central rms ≈0.4 mJy/beam  
  > "The typical central rms of the final maps is $\approx0.4$ mJy beam$^{-1}$." (The ALESS data)
- time on source: _not stated_
- observing dates: 18 Oct - 3 Nov 2011  
  > "Observations were carried out during ALMA Cycle 0 (‘Early Science’) between October 18 and November 3, 2011" (The ALESS data)
- pi or archival as stated: _not stated_
- Other facility **Herschel/SPIRE (HerMES)**: 250/350/500 um maps for stacking and dust SED  
  > "we repeat our stacking analysis on the *Herschel*/SPIRE maps of the ECDFS at 250, 350, and 500 $\mu$m." (4.3 Stacks of Herschel/SPIRE observations)
- Other facility **VLA 1.4 GHz**: 1.4 GHz ECDFS map (Miller et al.) for radio stacking  
  > "The map was obtained with the Very Large Array in extended (A) configuration, yielding a spatial resolution of $2.8''\times1.6''$ over a $32'\times32'$ wide region." (5.3.3 Radio fluxes)
- Other facility **MUSYC optical/NIR + IRAC**: photometric catalog for color selection  
  > "We base our analysis on the photometric catalog by (cite: simpson14), who capitalized on deep, optical/NIR archival data from various surveys of the ECDFS." (The optical/NIR dataset)
- External data: Photometric catalog, SED fits and photometric redshifts of ECDFS  
  > "We base our analysis on the photometric catalog by (cite: simpson14)" (The optical/NIR dataset) [from (cite: simpson14)]
- External data: Deblended SPIRE maps  
  > "We use the deblended SPIRE maps described in (cite: swinbank14)." (4.3 Stacks of Herschel/SPIRE observations) [from (cite: swinbank14)]
- External data: LABOCA stacking fluxes for comparison  
  > "Table [1](#tab_results) (bottom) reports the stacked fluxes obtained in G10 for their sub-mm faint sample" (5.3 Comparison with previous results at 870 um) [from (cite: greve10)]

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

- task: CASA, cleaned to 3-sigma  
  > "Data were reduced and cleaned down to a 3-$\sigma$ level using the Common Astronomy Software Application (CASA)." (The ALESS data)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: 128x128 pixels, 0.2'' per pixel  
  > "Final maps are $128\times128$ pixel, with a pixel scale of $0.2''$ per pixel." (The ALESS data)
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

- ALMA survey design, data reduction and cleaning  
  > "Details on the survey design, on the data reduction and the cleaning process are described in (cite: hodge13)." (The ALESS data) [from (cite: hodge13)]
- Good-quality map selection (rms<0.6 mJy/beam, axis ratio<2)  
  > "we focus only on the 86 ‘good quality’ maps with rms $<0.6$ mJy beam$^{-1}$ and beam axis ratio $<$ 2 (cite: hodge13)." (The ALESS data) [from (cite: hodge13)]
- K<20 selection and color cuts following G10/Daddi04  
  > "Following G10, we focus on the $K_{\rm Vega}<20$ mag (i.e., $K_{\rm AB}<21.83$ mag) galaxies, to ease the comparison with previous studies." (The optical/NIR dataset) [from (cite: greve10)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration details (in Hodge et al. 2013)
- Calibrated ALESS image products/primary beam models used
- Exact positions of pointings and catalog cross-match details
- Fitting method/priors for the modified blackbody and how SPIRE+344 GHz points were weighted
- Redshifts used for each galaxy in SED fits
- Radio stacking details (map weighting, median stack procedure)
- Procedure for rescaling SFRD by ALESS excess

## Analysis recipe

1. **Select galaxy samples**: Color/magnitude cuts on MUSYC catalog: K_Vega<20, sBzK, ERO, DRG  
  > "Distant Red Galaxies (DRGs), defined as $(J-K)>1.32$ (cite: franx03)." (The optical/NIR dataset)
   - parameter: only sources within 10.4'' (1.2x primary beam radius) of pointing centre  
  > "We keep only sources lying within $1.2\times$ the primary beam radius of each pointing (i.e., within $10.4''$ from each pointing center)" (4.1 Method)
   - fitting: _not stated_
   - validation: _not stated_
2. **Stack ALMA 344 GHz postage stamps**: Cut stamps, primary-beam correct, weighted average (weights = inverse square of PB correction); also median stacks  
  > "We align all the postage stamps, scale them to account for the primary beam attenuation computed at step #2, and then weight-average them." (4.1 Method)
   - parameter: flux cuts of 3.6, 1.8, 1.2 mJy; z>1 subsample; smoothing to 1.6'' circular beam test  
  > "We then progressively lower the flux cutoff to $S_{\nu}$(344 GHz)=$1.8$ mJy and $S_{\nu}$(344 GHz)=$1.2$ mJy, and repeat the experiment." (4.1 Method)
   - assumption: all maps have same depth within ~20%  
  > "Our working assumption is that all the maps have the same depth, which is true to within $\sim20$ % accuracy" (Footnote 4)
   - fitting: _not stated_
   - validation: Two independent stacking routines gave consistent results  
  > "The analysis is repeated with two different stacking routines, developed independently within our collaboration, finding consistent results." (4.1 Method)
3. **Estimate stacking uncertainties**: Stack N random positions per sample, 50 iterations; rms of stacked fluxes = noise  
  > "We perform 50 iterations, in order to gauge the variance of the random stacks." (4.2 Estimate of uncertainties)
   - assumption: maps are mostly source-free  
  > "The assumption here is that the maps are mostly “source-free”" (4.2 Estimate of uncertainties)
   - fitting: _not stated_
   - validation: Random-stack mean consistent with zero  
  > "we have verified that the average stacked values in the random iterations are always consistent with zero." (4.2 Estimate of uncertainties)
4. **Stack SPIRE maps and fit dust SED, derive L_IR and SFR**: Stack deblended SPIRE residual maps at z>1; fit modified blackbody; integrate 8-1000 um; SFR from Genzel+10 relation  
  > "We fit the observed SEDs as modified black bodies $S_\nu \propto \nu^{\beta} B_\nu(T_{\rm dust})$" (5.2 Herschel/SPIRE stacks)
   - parameter: T_dust=12-60 K, beta=1.4-2.0 range  
  > "$T_{\rm dust}=12-60$ K is the dust temperature, and $\beta=1.4-2.0$ sets the frequency dependence of the dust opacity" (5.2 Herschel/SPIRE stacks)
   - assumption: Chabrier IMF  
  > "This conversion implicitly assumes a (cite: chabrier03) initial mass function." (5.2 Herschel/SPIRE stacks)
   - fitting: _not stated_
   - validation: Compared with dust temperatures from other studies  
  > "These values are in agreement with the findings of similar studies" (5.2 Herschel/SPIRE stacks)
5. **Test ALESS-field bias with radio stacks, clustering and redshift distributions**: KS tests, Monte-Carlo clustering, 1.4 GHz median stacks, bootstrapping of field medians  
  > "This bootstrapping approach allows us to evaluate whether the discrepancy between the general field and ALESS-covered galaxies can be explained as an accidentally-bright realization" (5.3.3 Radio fluxes)
   - fitting: _not stated_
   - validation: ALESS medians >4-sigma outliers vs field bootstrap  
  > "represent $>4$-$\sigma$ outliers compared with the distribution of median stack values derived from bootstrapping the field sample." (5.3.3 Radio fluxes)
6. **Compute SFR density**: Average SFR x number of galaxies / comoving volume (34000 Mpc^3, 7.0 arcmin^2, 1<z<2.6), scaled down by ALESS radio excess  
  > "We compute SFRDs associated to our sample of galaxies by multiplying the average SFRs by the number of galaxies in each sample, and dividing the resulting ‘total’ SFRs by the volume sampled in our analysis." (5.4 Star formation rate density)
   - assumption: H0=70, Om=0.3, OL=0.7  
  > "$H_0=70$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_{\rm m}=0.3$ and $\Omega_{\Lambda}=0.7$" (1 Introduction)
   - fitting: _not stated_
   - validation: Compared with literature SFRD  
  > "Our estimates of the SFRD for $K$-selected galaxies are in broad agreement with previous work in the literature" (5.4 Star formation rate density)

## Software

- **CASA** : ALMA data reduction and cleaning (in Hodge et al. 2013)  
  > "Data were reduced and cleaned down to a 3-$\sigma$ level using the Common Astronomy Software Application (CASA)." (The ALESS data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Stacked 344 GHz flux, sBzK (all) | 1.88 | 0.11 | mJy | 2 | / sBzK              / 22         / 1.88       / 0.15       / 0.11       / |
| Stacked 344 GHz flux, K_Vega<20 (all) | 0.78 | 0.06 | mJy | 2 | / $K_{\rm Vega}<20$ / 100        / 0.78       / 0.06       / 0.06       / |
| Stacked 344 GHz flux, DRG (all) | 1.77 | 0.12 | mJy | 2 | / DRG               / 20         / 1.77       / 0.13       / 0.12       / |
| Stacked 344 GHz flux, ERO (all) | 1.11 | 0.10 | mJy | 2 | / ERO               / 26         / 1.11       / 0.09       / 0.10       / |
| Dust temperature, K<20 z>1 | 32 | +7/-2 | K | 4 | $32_{-2}^{+7}$ |
| SFR, ERO z>1 | 140 | +70/-40 | Msun/yr | 4 | $140_{-40}^{+70}$ |
| SFR, sBzK z>1 | 74 | +17/-19 | Msun/yr | 4 | $74_{-19}^{+17}$ |
| Dust emissivity index beta | 1.6 | not stated | dimensionless | 4 | We find $\beta=1.6$ and $T_{\rm dust}\approx 30$ K in all the cases. |
| Sky area analysed | 0.00193 | not stated | deg^2 | 6 | Our analysis covered $74 \times \pi (1.2 \times 17.3/2)^2$ arcsec$^2$ $\approx$ 0.00193 deg$^2$. |
| ALESS 1.4 GHz median stack K<20 | 10.0 | 1.0 | uJy | 5 | / $K_{\rm Vega}<20$ / $10.0 \pm1.0$ / $9.8 \pm1.0$  / $9.1 \pm1.0$  / $8.2 \pm1.0$  / $3.94\pm0.16$ / $2.5\pm0.3$  / |

## Qualitative findings

- ALMA stacked 344 GHz fluxes are a factor 2-3 higher than single-dish (G10) stacks; a similar excess seen at 1.4 GHz.  
  > "We compare our results with those of previous studies based on single-dish observations at 870 $\mu$m and find that our flux densities are a factor 2–3 higher than previous estimates." (abstract)

## Claim tuples

- H: Color-selected galaxies are detectable at 344 GHz by stacking ALMA data | E: Weighted and median stacks of K, sBzK, ERO, DRG at ALESS positions | R: >10-sigma detections in all classes; robust to flux cuts | F: Color-selected galaxies are detected even without individually detected SMGs | **supported**
- H: The ALMA-versus-single-dish flux discrepancy reflects intrinsic brightness of galaxies near SMGs | E: Radio stacks, clustering, z/luminosity distributions, photo-z association | R: 1.4 GHz fluxes also higher in ALESS fields; clustering consistent with field | F: Tentative evidence that galaxies associated with SMGs are brighter than average | **partially**
- H: Dust SED and SFR of color-selected z>1 galaxies | E: SPIRE+ALMA stacks fitted with modified blackbody | R: T_dust≈30 K, beta=1.6, L_IR (5-11)e11 Lsun, SFR 75-140 Msun/yr | F: Color-selected galaxies contribute one third to one sixth of SFRD at 1<z<2.6 | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Discrepancy as artifact of single-dish deblending judged unlikely  
  > "The first scenario seems unlikely, given that various groups have run different analyses based on independent approaches and routines" (5.3 Comparison with previous results at 870 um)
- How they decided it was enough: _not stated_
- Limitation (authors): Photometric redshift uncertainties large; physical association flag may be a by-product of similar redshift distributions  
  > "We note however that the uncertainties in the photometric redshifts used in this test are large." (5.3.4 Physical association vs. chance projection)
- Caveat (inferred, ours): Sample overlap between classes makes classes not independent
- Caveat (inferred, ours): Stacked flux measured as pixel maximum within 3'' (biased high)
- Caveat (inferred, ours): ALESS pointings selected on bright SMGs so biased by design
- Caveat (inferred, ours): SED fit has few data points, degenerate T and beta

## Reproducibility

- Data public (paper): Data available from ALMA and ESO archives  
  > "The data employed in this analysis are available from the ALMA and ESO archives." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Stacking code not released
- Missing: Calibrated ALESS maps and Simpson et al. catalog needed
- Missing: Fit procedure details
- Data volume (inferred): ~tens of GB raw for 86 Cycle 0 pointings; much smaller if calibrated maps used
- Score (inferred): 3/5, Stacking recipe clear and data public, but inputs from companion papers and fitting details missing.
- Rediscovery candidate: yes, Public data, simple stacking recipe, numeric results in tables; depends on companion catalogs.

## Links

- Method: (cite: hodge13) (ALESS survey design and data reduction)
- Method: (cite: greve10) (Stacking approach and comparison on LESS)
- Companion: (cite: simpson14) (Photometric catalog and redshifts)
- Companion: (cite: swinbank14) (Deblended SPIRE maps)
- Companion: (cite: karim13) (ALESS number counts)
- Related: ALESS
- Related: LESS
- Related: MUSYC
- Related: HerMES

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
 "codes_not_in_obscore": [
  "2011.1.00294.S"
 ],
 "obscore_codes_not_in_card": [
  "2011.0.00294.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 42,
  "rate": 0.519
 },
 "evidence_ok": true
}
```

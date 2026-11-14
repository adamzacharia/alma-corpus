# ALMA Resolves 30 Doradus: Sub-parsec Molecular Cloud Structure near the Closest Super Star Cluster

`2013ApJ...774...73I` | The Astrophysical Journal 2013 | first author: Indebetouw, Rémy | arXiv: 1307.3680 | DOI: 10.1088/0004-637X/774/1/73

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism, nearby_galaxies
- Question: How do dense molecular clump properties and CO/dust abundances in 30Dor-10, near the super star cluster R136, compare with Galactic clumps and with distance from R136?  
  > "With ALMA we can address how molecular cloud structure is affected by radiative feedback, and whether the dense star-forming structures in clouds are different in such extreme environments." (Introduction)
- Target **30Dor-10 cloud (30 Doradus, LMC)**: coordinates APEX map centre (05:38:47.8, -69:04:50.3)  
  > "At 50kpc (cite: walker11), R136 in 30 Doradus is the nearest SSC by an order of magnitude." (Introduction); z/distance 50 kpc  
  > "At 50kpc (cite: walker11), R136 in 30 Doradus is the nearest SSC by an order of magnitude." (Introduction); distance from walker11  
  > "At 50kpc (cite: walker11), R136 in 30 Doradus is the nearest SSC by an order of magnitude." (Introduction)

## Data provenance

- ALMA projects: 2011.0.00471.S
- bands: Band 6 (1.3 mm)  
  > "using the 1.3$\;$mm Band 6 recievers" (2.1 ALMA)
- frequencies and spectral setup: 4x1 GHz FDM windows centered at 218.5, 219.267, 230.767, 231.688 GHz; 244 kHz (~0.33 km/s) resolution  
  > "The spectral setup had 4$\times$1GHz FDM (frequency division mode) spectral windows centered at 218.5, 219.267, 230.767, and 231.688GHz with 244kHz ($\sim$0.33km$\;$s$^{-1}$) resolution." (2.1 ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~2.3"x1.5" = 0.56x0.36 pc for 12CO 2-1  
  > "The synthesized beam is $\simeq$2.3$''$$\times$1.5$''$ = 0.56pc$\times$0.36pc for $^{12}$CO$\;$2-1" (2.1 ALMA)
- max recoverable scale: 1.1" to 20" (0.28 to 5 pc)  
  > "The array configuration is sensitive to spatial scales from 1.1$''$ to 20$''$ (0.28 to 5$\,$pc)." (2.1 ALMA)
- sensitivity: 8-10 mJy/beam (~0.15 K) per 0.5 km/s channel away from strong lines  
  > "The expected RMS per channel is 8$\;$mJy$\;$bm$^{-1}$, and 8–10$\;$mJy$\;$bm$^{-1}$ $\simeq$0.15$\;$K is achieved away from strong lines" (2.1 ALMA)
- time on source: four execution blocks of ~27.7 min each  
  > "| uid://A002/X35edea/X228 | 13 | 2011-12-31 01:58:12 UT | 43$\deg$ | 3.5$\;$mm | 27.7min |" (Table 1)
- observing dates: 2011-12-31 and 2012-01-11  
  > "| uid://A002/X36a70f/X895 | 15 | 2012-01-11 03:49:04 UT | 41$\deg$ | 2.2$\;$mm | 27.7min |" (Table 1)
- pi or archival as stated: _not stated_
- Line: 12CO 2-1 (230.538 GHz)
- Line: 13CO 2-1 (220.399 GHz)
- Line: C18O 2-1 (219.560 GHz)
- Line: H30alpha RRL (231.90093 GHz)
- Other facility **APEX**: Single-dish 12CO, 13CO 2-1 maps for short-spacing combination  
  > "Observations with a single-dish telescope are necessary to recover the total flux on large spatial scales, which is resolved out by an interferometer." (2.2 APEX)
- Other facility **ATCA**: 6 cm and 3 cm continuum for free-free subtraction  
  > "Figure [2](#cont) compares the ALMA 1.3$\;$mm continuum to 6$\;$cm continuum imaged at similar resolution with the Australia Telescope Compact Array (cite: lazendic_cm)." (4.4 Continuum)
- Other facility **HST/Spitzer/SOFI archival**: NIR to mid-IR images for YSO/cluster association  
  > "Multiwavelength data was retrieved from various archives as listed in Table [2](#archival)." (2.3 Archival Data)
- External data: 6 cm and 3 cm ATCA continuum images  
  > "Figure [2](#cont) compares the ALMA 1.3$\;$mm continuum to 6$\;$cm continuum imaged at similar resolution with the Australia Telescope Compact Array (cite: lazendic_cm)." (4.4 Continuum) [from (cite: lazendic_cm)]
- External data: Galactic cloud and clump comparison data (Heyer 2009, Orion, CMZ, IRDC clumps)  
  > "Milky Way clouds measured using $^{12}$CO and $^{13}$CO$\;$1-0 are taken from Heyer et al. 2009" (Scaling Relations) [from (cite: heyer09); (cite: oka01); (cite: gibson09)]
- External data: Dust opacity 0.62 cm2/g and gas-to-dust ratio from LMC  
  > "We adopt $\kappa_d$=0.62$\pm$0.1$\;$cm$^2\;$g$^{-1}$, midway between 0.72$\;$cm$^2\;$g$^{-1}$ used by (cite: bot07) in the SMC" (5.2 H2 Mass from Dust Continuum Emission) [from (cite: bot07); (cite: galliano11)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto (Butler-JPL Horizons-2010); bandpass J0538-440, phase J0635-7516  
  > "Callisto was observed before the first observation on 2011-12-31, to set the absolute flux scale with estimated uncertainty of $15\%$ using the Butler-JPL Horizons-2010 model." (2.1 ALMA)
- flux scale uncertainty: 15%  
  > "to set the absolute flux scale with estimated uncertainty of $15\%$" (2.1 ALMA)
- self calibration: _not stated_

### Imaging

- task: CASA; APEX cube combined with feather, feathered image used as clean model  
  > "To mitigate these effects we used the feathered image as a model in clean deconvolution" (2.2 APEX)
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
- array combination: APEX + ALMA with CASA feather  
  > "The APEX image cube was combined with a cleaned ALMA cube using the CASA task `feather`" (2.2 APEX)
- smoothing: 6 cm and ALMA continuum convolved to 2.67"x2.0" for free-free subtraction  
  > "we spatiallly filtered the 6$\;$cm image to match it to ALMA’s spatial sensitivity, and then convolved both maps to 2.67$''$$\times$2.0$''$." (4.4 Continuum)
- final beam: _not stated_
- final rms: 8-10 mJy/beam (~0.15 K) per 0.5 km/s channel  
  > "8–10$\;$mJy$\;$bm$^{-1}$ $\simeq$0.15$\;$K is achieved away from strong lines" (2.1 ALMA)

### Inherited from earlier work

- Column density via LTE method with common assumptions  
  > "Column density was calculated from $^{12}$CO and $^{13}$CO$\;$2-1 using common assumptions (cite: rohlfs)" (5.1) [from (cite: rohlfs)]
- Clump radius convention r=1.91 sigma_x  
  > "We adopt the commonly used convention for a radial density profile $\rho\propto$r$^{-1}$ which yields r=1.91$\sigma_x$ (cite: srby; bolatto_araa)." (6.1 Cloud Decomposition) [from (cite: srby); (cite: bolatto_araa)]
- Local-maxima selection criteria of cprops in hybrid decomposition  
  > "We use a hybrid approach in which local maxima are chosen using the `cprops` criteria" (6.1) [from (cite: cprops_pasp)]
- CO 1-0/2-1 ratio 0.7  
  > "Applying the same ratio F($^{12}$CO$\;$1-0)/F($^{12}$CO$\;$2-1)=0.7 as (cite: sandstrom)" (6.3) [from (cite: sandstrom)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration procedure (manual vs pipeline), flagging
- tclean/clean parameters: weighting, robust, cell, image size, masks, threshold
- Continuum channel selection and continuum subtraction method
- Feather parameters and relative flux scaling applied
- Exact hybrid clump decomposition parameters (contrast, S/N, floor levels)
- Dust temperature = Tex assumption details and mass-map region
- Fit method for scaling relation and mass-function slopes

## Analysis recipe

1. **Combine ALMA and APEX CO cubes**: Feather APEX with cleaned ALMA cube, then use as clean model  
  > "To mitigate these effects we used the feathered image as a model in clean deconvolution" (2.2 APEX)
   - software: CASA, CLASS
   - parameter: APEX conversion Tmb to Jy/beam multiply by 39  
  > "The APEX data was converted from main beam temperature to Jy$\;$bm$^{-1}$ by multiplying by 39 (cite: apex)" (2.2 APEX)
   - fitting: _not stated_
   - validation: Varied relative flux calibration; <10% uncertainty in 12CO clump properties, <5% in 13CO  
  > "the image combination process results in less than 10% uncertainty of $^{12}$CO clump properties and less than 5% uncertainty of $^{13}$CO clump properties." (2.2 APEX)
2. **Remove free-free from 1.3 mm continuum**: Scale uv-matched 6 cm image by nu^-0.1 assuming optically thin free-free and subtract  
  > "The free-free contribution to the 1.3$\;$mm continuum can be subtracted by assuming that the 6$\;$cm continuum is 100% optically thin free-free emission, and scaling S$_\nu$ by $\nu^{-0.1}$." (4.4 Continuum)
   - fitting: _not stated_
   - validation: Repeated with 3 cm image, quantitatively similar  
  > "We also performed the free-free subtraction using the 3$\;$cm image from (cite: lazendic_cm), with quantitatively similar results." (4.4 Continuum)
3. **Derive Tex, 13CO column density and H2 mass from CO**: LTE: Tex from optically thick 12CO peak, 13CO opacity and column density, H2/13CO conversion  
  > "If it is further assumed that $^{13}$CO has the same excitation temperature as $^{12}$CO, the relative abundance is constant, and that CO is thermalized" (5.1)
   - parameter: H2/13CO = 5e6  
  > "We will use H$_2$/$^{13}$CO=5$\times$10$^6$" (5.1)
   - assumption: 13CO and 12CO share Tex; LTE; individual masses uncertain by a factor of two  
  > "We expect the analysis to be robust, but that individual masses may have uncertainties of a factor of two." (5.1)
   - fitting: _not stated_
   - validation: Checked against dust and virial masses  
  > "which as shown in section [2.3](#massmass) yields good agreement between several methods of calculating H$_2$ mass." (5.1)
4. **Derive dust mass**: I_nu = Sigma_gas kappa x_d B_nu(T_dust), with T_dust = 12CO Tex  
  > "If we assume that the CO excitation temperature calculated above from the $^{12}$CO$\;$2-1 brightness temperature equals the dust temperature, we can easily make a column density map." (5.2)
   - parameter: kappa=0.62±0.1 cm2/g; x_d=1/339  
  > "Scaling the gas-to-dust ratio by the LMC metallicity of 1/2 solar (cite: rolleston03; pagel03) yields $x_d$=1/339 (cite: galliano11)." (5.2)
   - fitting: _not stated_
   - validation: Compared with Herschel dust T of 55 K and literature masses  
  > "the dust temperature derived from *Herschel* data by Gordon et al. (2014) in prep. is 55K in the single resolution element containing 30Dor-10" (5.2)
5. **Decompose cube into clumps and measure properties**: Hybrid cprops-like decomposition on 13CO; intensity-weighted moments deconvolved by beam and channel width  
  > "Clump properties are measured from the intensity-weighted moments in space and velocity of the pixels assigned to each clump." (6.1)
   - software: cprops, clumpfind
   - parameter: no deconvolved radii <0.1 pc used  
  > "We do not use any deconvolved radii less than 0.1$\;$pc." (6.1)
   - fitting: _not stated_
   - validation: Trends robust over range of decomposition parameters  
  > "all of the trends below are robust to the decomposition method." (6.1)
6. **Scaling relations, virial masses, X-factor, mass function, trends with R136 distance**: Mvir=5 sigma^2 r/G compared to Mmol and Mdust; size-linewidth-surface density; power-law fits  
  > "the virial masses M$_{vir}$=5$\sigma_v^2r$/G and masses determined from CO (M$_{mol}$); in 30Dor-10 these are in rough agreement" (6.2)
   - assumption: Virial masses uncertain by at least factor 2  
  > "virial masses should be regarded as having at least a factor of 2 uncertainty" (6.2)
   - fitting: formal best-fit lines; sampler and priors not stated  
  > "The formal best-fit line is marked, M$_{vir}$/M$_{mol}$ =35$\;$M$_\odot\;$M$_{mol}^{-0.6}$." (Scaling Relations)
   - validation: _not stated_

## Software

- **CASA** : ALMA processing, imaging, feather combination  
  > "The data were processed in the Common Astrononomy Software Applications (CASA) package" (2.1 ALMA)
- **CLASS/GILDAS** : APEX baseline subtraction and gridding  
  > "further reduced in CLASS (<http://www.iram.fr/IRAMFR/GILDAS>) for baseline subtraction on individual spectra and gridding" (2.2 APEX)
- **Montage** : mosaicking NIR images  
  > "then background-matched and mosaicked using Montage" (2.3 Archival Data)
- **gasgano** : ESO data pipeline  
  > "We processed ESO data through the `gasgano` data pipeline" (2.3 Archival Data)
- **cprops** : basis of clump identification criteria  
  > "We use a hybrid approach in which local maxima are chosen using the `cprops` criteria" (6.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dust-derived total mass in map | 6±1e4 | ±1e4 | Msun | 4 | The total mass in the map derived from dust emission is 6$\pm$1$\times$10$^4\;$M$_\odot$ |
| Total CO-traced H2 mass | 8.9e4 | ±0.3e4 | Msun | 3 | the total calculated H$_2$ mass *traced by CO* in 30Dor-10 is 8.9$\pm$0.3$\times$10$^4\;$M$_\odot$ |
| Mmol/F(12CO 2-1) for clumps | 12 | ±4 | Msun pc-2 (K km/s)-1 | 6 | M$_{mol}$/F($^{12}$CO$\;$2-1) = 12$\pm$4$\;$M$_\odot\;$pc$^{-2}\;$(K$\;$km$\;$s$^{-1}$)$^{-1}$ |
| X-factor for clumps (CO 1-0) | 8.4 | ±3 | Msun pc-2 (K km/s)-1 | 6 | yields an X-factor of 8.4$\pm$3$\;$M$_\odot\;$pc$^{-2}\;$($^{12}$CO$\;$1-0$\;$K$\;$km$\;$s$^{-1}$)$^{-1}$ *for clumps* in 30Dor-10 |
| Free-free fraction of 1.3 mm flux removed | 39 | not stated | % | 2 | A total of 39% of the total flux in the 1.3$\;$mm image is removed as free-free contamination. |
| Mvir/Mmol vs Mmol fit | 35 Msun Mmol^-0.6 | not stated | dimensionless | 6 | M$_{vir}$/M$_{mol}$ =35$\;$M$_\odot\;$M$_{mol}^{-0.6}$ |
| Median clump velocity dispersion | 1.1 | not stated | km/s | 5 | with a median value of 1.1$\;$km$\;$s$^{-1}$(FWHM 2.6$\;$km$\;$s$^{-1}$) |
| Clump mass function slope (M>500 Msun, molecular mass) | -0.9 | ±0.2 | dimensionless | 6 | $\alpha$=-0.9$\pm$0.2 and 1.2$\pm$0.2 for molecular and virial masses, respectively |

## Qualitative findings

- Less diffuse 12CO than in Galactic W3, suggesting selective photodissociation of interclump CO  
  > "There is more diffuse $^{12}$CO emission in a Galactic region like W3 than in 30Dor-10." (3.1)
- Dust masses ~2x lower than CO or virial masses  
  > "showing that the dust masses are $\sim$2$\times$ lower than the virial or molecular masses" (6.3)

## Claim tuples

- H: Do sub-parsec clumps in 30 Doradus follow Galactic size-linewidth-surface density trends? | E: Clump decomposition of 13CO cube and comparison with Galactic data | R: Clumps have somewhat larger linewidths for given size and reach higher surface density | F: Similar to Galactic clumps/IRDCs, consistent with pressure confinement though not unique | **supported**
- H: Is the CO abundance or X-factor different in dense clumps at reduced metallicity? | E: Compare CO, dust and virial masses | R: X-factor 8.4±3, H2/13CO=5e6 gives agreement; dust ~2x lower | F: CO abundance not significantly different from LMC mean; dust abundance may be reduced by ~2 | **supported**
- H: Does R136 radiation affect clump properties with depth? | E: Plot clump properties against projected distance from R136 | R: No strong trends; modest trend to wider clump separation deeper in cloud | F: Dense clumps not strongly affected by external radiation | **partially**

## Reasoning

- Why this data: Cycle 0 pilot targeting the northern, more massive cloud 30Dor-10  
  > "we chose to observe the northern, more massive cloud 30Dor-10" (3)
- Why this method: _not stated_
- Alternative: clumpfind and gaussclumps considered; hybrid cprops-style approach chosen  
  > "We use a hybrid approach in which local maxima are chosen using the `cprops` criteria" (6.1)
- How they decided it was enough: _not stated_
- Limitation (authors): No single-dish continuum, so extended dust emission may be resolved out  
  > "we do not have single-dish continuum observations, and some large-scale diffuse emission may be resolved out" (4.4 Continuum)
- Limitation (authors): Clumps are approximately beam-sized; higher resolution will break them up  
  > "Higher resolution will likely break these clumps up into smaller substructures" (6)
- Caveat (inferred, ours): Dust temperature set equal to 12CO Tex may bias dust masses
- Caveat (inferred, ours): H2/13CO and gas-to-dust ratios degenerate; agreement partly tuned
- Caveat (inferred, ours): Clump properties are beam-limited and decomposition-dependent
- Caveat (inferred, ours): Cycle 0 data with few antennas and dynamic-range limits

## Reproducibility

- Data public (paper): ALMA project code cited; APEX and archival data from archives  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00471.S." (footnote 1)
- Products in archive: _not stated_
- Missing: Imaging parameters and CASA version
- Missing: APEX data reduction details and the feather weighting
- Missing: Hybrid decomposition parameters
- Missing: Continuum channel selection
- Data volume (inferred): ~50-100 GB raw (4 EBs, Cycle 0) plus APEX cubes
- Score (inferred): 3/5, Data public and analysis equations given, but imaging, calibration and decomposition parameters are largely unstated.
- Rediscovery candidate: no, Imaging and clump-decomposition recipes are incomplete, and the APEX data are not archived in an easily accessible form.

## Links

- Method: (cite: cprops_pasp) (clump identification criteria)
- Method: (cite: condon97) (minimum fittable clump size)
- Companion: Kepley et al. 2014, in prep (H30alpha analysis)
- Companion: Brogan et al. 2013, in prep (HCN, HCO+, CS, H40alpha 90 GHz data)
- Related: MAGMA
- Related: SAGE
- Related: Herschel HERITAGE

## Checks

```json
{
 "quotes": 74,
 "quotes_ok": 74,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2011.0.00273.S"
 ],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 87,
  "stated": 57,
  "rate": 0.655
 },
 "evidence_ok": true
}
```

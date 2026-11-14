# Protoplanetary Disk Properties in the Orion Nebula Cluster: Initial Results from Deep, High-resolution ALMA Observations

`2018ApJ...860...77E` | The Astrophysical Journal 2018 | first author: Eisner, J. A. | arXiv: 1805.03669 | DOI: 10.3847/1538-4357/aac3e2

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: What are the sub-mm continuum fluxes, dust masses and sizes of protoplanetary disks in the dense Orion Nebula Cluster, and how do they depend on stellar mass and distance from theta1 Ori C compared with low-density regions?  
  > "We find a correlation between disk flux and distance from the massive star $\theta^1$ Ori C, suggesting that disk properties in this region are influenced strongly by the rich cluster environment." (abstract)
- Target **Orion Nebula Cluster (central 1.5' x 1.5' mosaic)**: coordinates _not stated_; z/distance ~400 pc  
  > "We mapped the central $1.5' \times 1.5'$ region of the ONC. The map is comprised of 136 mosaicked pointings." (Observations and Data Reduction); "At the distance to Orion, $\sim 400$ pc (cite: SANDSTROM+07; MENTEN+07; KRAUS+07; HIROTA+07; KOUNKEL+17)" (Observations and Data Reduction); distance from Sandstrom+07; Menten+07; Kraus+07; Hirota+07; Kounkel+17  
  > "We mapped the central $1.5' \times 1.5'$ region of the ONC. The map is comprised of 136 mosaicked pointings." (Observations and Data Reduction); "At the distance to Orion, $\sim 400$ pc (cite: SANDSTROM+07; MENTEN+07; KRAUS+07; HIROTA+07; KOUNKEL+17)" (Observations and Data Reduction)

## Data provenance

- ALMA projects: 2015.1.00534.S
- bands: ~350 GHz, 850 um  
  > "The fields were observed at $\sim 350$ GHz frequency, corresponding to a wavelength of 850 $\mu$m." (Observations and Data Reduction)
- frequencies and spectral setup: Four spectral windows at 343, 345, 355, 358 GHz; two 2.0 GHz wide, two 1.875 GHz wide  
  > "We observed with four spectral windows centered at 343, 345, 355, and 358 GHz. Two windows covered 2.0 GHz bandwidth, and the other two covered 1.875 GHz." (Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.09 arcsec synthesized beam (~35 AU)  
  > "The synthesized beam FWHM is $0\rlap{.}''09$." (Observations and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: rms ~0.1 mJy in clean regions, up to 2.5 mJy in BN/KL  
  > "In “clean” regions of the image, the rms is $\sim 0.1$ mJy, while it rises as high as 2.5 mJy in the BN/KL region." (Results)
- time on source: _not stated_
- observing dates: 13 September 2016  
  > "Observations were taken on 13 September 2016." (Observations and Data Reduction)
- pi or archival as stated: _not stated_
- Line: CO 3-2 (345.796 GHz)
- Line: HCO+ 4-3 (356.734 GHz)
- Other facility **VLA (cm-wavelength archival surveys)**: cm fluxes used to constrain free-free emission  
  > "These surveys used the VLA, and have angular resolution comparable to the resolution in our ALMA observations." (Results)
- Other facility **HST**: proplyd catalog positions  
  > "We searched for 850 $\mu$m continuum emission towards the positions of HST-detected proplyds (cite: RRS08)" (Results)
- External data: Proplyd positions (HST)  
  > "positions of HST-detected proplyds (cite: RRS08) and near-IR detected sources (cite: HC00; EISNER+16)" (Results) [from (cite: RRS08)]
- External data: Near-IR source catalog  
  > "near-IR detected sources (cite: HC00; EISNER+16)" (Results) [from (cite: HC00; EISNER+16)]
- External data: cm-wavelength fluxes for free-free modeling  
  > "We used previous observations of the ONC at cm wavelengths (cite: FELLI+93a; FELLI+93b; ZAPATA+04; FORBICH+07; FORBRICH+16; SHEEHAN+16)" (Results) [from (cite: FELLI+93a; FELLI+93b; ZAPATA+04; FORBICH+07; FORBRICH+16; SHEEHAN+16)]
- External data: Stellar masses from spectroscopy  
  > "Stellar masses, determined spectroscopically, are available in the literature for about 60% of our ALMA-detected sample (cite: HILLENBRAND97; LUHMAN+00; SLESNICK+04; HILLENBRAND+13; INGRAHAM+14)." (Disk Properties as a function of Stellar Mass) [from Hillenbrand97; Luhman+00; Slesnick+04; Hillenbrand+13; Ingraham+14; Fang et al. in prep]
- External data: Disk masses, sizes of other regions for comparison  
  > "Mass distributions, computed in the same way, are available for Taurus (cite: ANDREWS+13), Lupus (cite: ANSDELL+16), Cham I (cite: PASCUCCI+16)" (Disk Mass Distribution) [from Andrews+13; Ansdell+16; Pascucci+16; Ansdell+17; Barenfeld+16; Tripathi+17; Tazzari+17]
- Simulation/model as data: RADMC-3D baseline disk models (Rc=25 AU, dust mass 1e-2 to 1e3 Earth masses) used to test the optically thin mass formula  
  > "Dust mass was varied between $10^{-2}$ M$_{\oplus}$ and $10^3$ M$_{\Earth}$." (Disk Mass Distribution)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline flux, passband, gain calibration; imaging done by hand  
  > "Adopting the flux, passband, and gain calibrated data, we completed the imaging process by hand." (Observations and Data Reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Self-cal using clean components of bright sources as starting model; rms improved a few percent  
  > "We used the clean components of bright sources as a starting model for self-calibration." (Observations and Data Reduction)

### Imaging

- task: CASA tclean  
  > "We imaged the continuum data using the CASA task `tclean`." (Observations and Data Reduction)
- deconvolver: Multiscale clean (0, 0.1", 0.3" scales) adopted over Hogbom  
  > "We made images with both Hogbom and multiscale (0, $0\rlap{.}''1$, and $0\rlap{.}''3$ scales) clean algorithms." (Observations and Data Reduction)
- weighting robust: robust = 0.5  
  > "employed a robust weighting parameter of 0.5" (Observations and Data Reduction)
- uv taper: uv cut at 100 klambda (optimal rms among 0-300 klambda)  
  > "The optimal rms across the mosaic is achieved with a $uv$ cut of 100 k$\lambda$." (Observations and Data Reduction)
- cell size: 0.02 arcsec  
  > "We generated images with cell sizes of $0\rlap{.}''02$, and employed a robust weighting parameter of 0.5." (Observations and Data Reduction)
- image size: _not stated_
- masking: Iterative clean boxes on all objects above 5 sigma  
  > "we placed boxes on all objects detected above 5$\sigma$, generated a cleaned image, then examined the residuals for additional detections." (Observations and Data Reduction)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: Channels with strong emission flagged per field; BN/KL and OMC1S more heavily flagged  
  > "We flagged spectral channels containing strong emission in each of the observed fields." (Observations and Data Reduction)
- primary beam correction: Applied to mosaic  
  > "Finally, we applied a primary beam correction to the mosaic." (Observations and Data Reduction)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.09 arcsec FWHM  
  > "The synthesized beam FWHM is $0\rlap{.}''09$." (Observations and Data Reduction)
- final rms: _not stated_

### Inherited from earlier work

- Free-free plus dust SED model with beta=1  
  > "optically-thin dust with $\beta=1$ (cite: EISNER+16)" (Results) [from (cite: EISNER+16)]
- Dust mass assumptions: kappa0=2 cm2/g at 1.3 mm, beta=1, T=20 K  
  > "$\kappa_0=2$ cm$^{2}$ g$^{-1}$ at 1.3 mm; $\beta=1.0$ (cite: HILDEBRAND83; BECKWITH+90); and $T_{\rm dust} = 20$ K (cite: AW05; CARPENTER02; WAW05)." (Disk Mass Distribution) [from (cite: HILDEBRAND83; BECKWITH+90; AW05; CARPENTER02; WAW05)]
- Bayesian linear regression with upper limits  
  > "We applied linear regression using the Bayesian analysis described in (cite: KELLY07)." (Disk Size Distribution) [from (cite: KELLY07)]

### Not stated but needed to reproduce (our reading)

- Which channels were flagged per field (line-free channel ranges)
- Self-calibration solution intervals and number of iterations
- Array configurations, baselines, number of execution blocks, time on source
- Number of clean iterations and thresholds
- Details of the Gaussian fit procedure and size-deconvolution errors
- Statistical test details for correlations (flux vs radius, stellar mass)
- Free-free model fit method (priors, fitter) and cm fluxes used
- Coordinates of phase center

## Analysis recipe

1. **Image the continuum mosaic**: tclean with multiscale clean, uv cut of 100 klambda, self-calibration, primary beam correction  
  > "Our final image thus uses this $uv$ cut, along with multi-scale cleaning and self-cal as described above." (Observations and Data Reduction)
   - software: CASA tclean
   - parameter: robust 0.5, cell 0.02"  
  > "employed a robust weighting parameter of 0.5" (Observations and Data Reduction)
   - fitting: _not stated_
   - validation: Tested uv cuts from 0 to 300 klambda; multiscale vs Hogbom compared  
  > "we generated images with $uv$ cuts ranging from 0 (i.e., keeping all data) to 300 k$\lambda$." (Observations and Data Reduction)
2. **Detect sources and measure fluxes**: Match to optical/near-IR positions within 0.5", detection threshold 4 sigma of local noise  
  > "We employed a detection threshold of 4$\sigma$ above the locally-determined noise level for each optical/near-IR source." (Results)
   - fitting: _not stated_
   - validation: Expected <<1 false detection; mean background verified zero  
  > "This threshold ensures that $\ll 1$ detection is expected from Gaussian noise fluctuations across the entire sample of known cluster members." (Results)
3. **Remove free-free contribution**: Fit model of thick+thin free-free plus beta=1 dust to cm-to-sub-mm photometry for 52 sources  
  > "we constructed a model that includes optically thick free-free emission past a turnover wavelength (typically $>1$–10 cm), thin free-free emission short-ward of that turnover, and optically-thin dust with $\beta=1$" (Results)
   - parameter: free parameters: turnover wavelength, free-free and dust fluxes at ALMA wavelength  
  > "Free parameters in the model are the turnover wavelength of free-free emission, and the free-free and dust fluxes at the observed ALMA wavelength." (Results)
   - fitting: _not stated_
   - validation: Residual cm non-detections imply <~0.03 mJy free-free  
  > "the potential free-free contribution at mm wavelengths, is $\ensuremath{\lesssim} 0.03$ mJy for these sources." (Results)
4. **Measure disk sizes**: 2D elliptical Gaussian fit to each source, beam-deconvolved; HWHM of major axis  
  > "we fitted a 2D elliptical Gaussian to each of the sub-images shown in Figure [2](#fig:detections). We used Gaussian deconvolution to remove the effect of the beam." (Results)
   - fitting: 2D Gaussian  
  > "To measure sizes, we fitted a 2D elliptical Gaussian to each of the sub-images shown in Figure [2](#fig:detections). We used Gaussian deconvolution to remove the effect of the beam." (Results)
   - validation: _not stated_
5. **Derive dust masses**: Optically thin isothermal formula M = S d^2/(kappa B(T))  
  > "To use this formula, we make the following assumptions: $d = 400$ pc; $\kappa_0=2$ cm$^{2}$ g$^{-1}$ at 1.3 mm; $\beta=1.0$" (Disk Mass Distribution)
   - assumption: d=400 pc, T_dust=20 K, beta=1, kappa0=2 cm2/g at 1.3 mm  
  > "$T_{\rm dust} = 20$ K (cite: AW05; CARPENTER02; WAW05)" (Disk Mass Distribution)
   - fitting: _not stated_
   - validation: Compared with RADMC-3D models; within factor 2 for most fluxes  
  > "Equation [\[eq:dustmass\]](#eq:dustmass) is within a factor of 2 of the radiative transfer results for most sub-mm fluxes seen in our sample." (Disk Mass Distribution)
6. **Test mass estimates with radiative transfer**: RADMC-3D models with Rc=25 AU, flaring H/R ∝ R^0.15, Sigma ∝ R^-1, M-star L=0.5 Lsun, Teff=3500 K, grains 0.05-10000 um slope -3.5  
  > "The dust grain sizes range from 0.05 $\mu$m to 10000 $\mu$m with power law slope of -3.5." (Disk Mass Distribution)
   - software: RADMC-3D
   - fitting: _not stated_
   - validation: _not stated_
7. **Correlation analysis**: Bayesian linear regression with upper limits for size vs flux; flux vs stellar mass and distance from theta1 Ori C  
  > "This technique takes into account heteroscedastic error bars on both parameters of interest, and uses available upper limits to constrain the regression." (Disk Size Distribution)
   - software: Kelly07 linmix
   - fitting: Bayesian regression (Kelly 2007)  
  > "We applied linear regression using the Bayesian analysis described in (cite: KELLY07)." (Disk Size Distribution)
   - validation: _not stated_

## Software

- **CASA** : tclean imaging and continuum split  
  > "We imaged the continuum data using the CASA task `tclean`." (Observations and Data Reduction)
- **RADMC-3D** : radiative transfer test of dust mass formula  
  > "we generated a small set of radiative transfer models using RADMC-3D (cite: DULLEMOND+12)" (Disk Mass Distribution)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Sources detected at 850 um | 104 | not stated | sources | 2 | sub-mm continuum emission above the 4$\sigma$ level was seen towards 104 cluster members |
| Proplyd detection rate | 48 of 61 (~80%) | not stated | dimensionless | 2 | We detected sub-mm continuum emission towards 48 of the known proplyds, a detection rate of $\sim 80\%$. |
| Dusty disk detection rate, proplyds | 65 | 10 | % | 3 | $65 \pm 10\%$ of proplyds have dusty disks, while $45 \pm 7\%$ of all cluster members in the region have dusty disks. |
| Synthesized beam FWHM | 0.09 | not stated | arcsec | 1 | The synthesized beam FWHM is $0\rlap{.}''09$. |
| Free-free dominated sources | 12 | not stated | sources | 3 | 12 are consistent with 100% of the sub-mm continuum flux arising from free-free emission. |
| Dust masses | 0.5 to 80 | not stated | Earth masses | 5 | the fluxes detected from dusty disks correspond to dust masses ranging from 0.5 to 80 Earth masses. |
| Average dust temperature of compact disks (RT models) | 40 | not stated | K | 6 | As shown in Figure [13](#fig:comprt), 40 K is more appropriate. |
| Gravitational radius | ~20 | not stated | AU | 0 | the gravitational radius is $\sim 20$ AU, similar to the disk radii inferred for our sample. |

## Qualitative findings

- ONC disks are compact, mostly HWHM 10-30 AU, none >60 AU  
  > "Most disks have Gaussian HWHM between 10 and 30 AU; no disks have radii $>60$ AU." (Conclusions)

## Claim tuples

- H: Disks in the dense ONC are smaller and lower in mass than in low-density regions | E: Compare ONC size and mass CDFs to Taurus, Oph, Lupus, Cham I, Upper Sco, sigma Ori | R: ONC lacks large and massive disks | F: ONC disks are truncated, likely by environment | **supported**
- H: Disk flux depends on stellar mass as steeply as elsewhere | E: Flux vs stellar mass for detections and non-detections | R: Weak correlation | F: Flatter than other regions | **supported**
- H: External photoevaporation by theta1 Ori C affects disks | E: Flux and size vs projected distance | R: Marginally significant flux correlation; lack of high-flux sources within 0.03 pc | F: Disks influenced by cluster environment | **partially**
- H: Optically thin isothermal masses are accurate | E: RADMC-3D models | R: Within factor 2 for most fluxes; underestimate up to ~10x for F>10 mJy | F: Masses uncertain | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Hogbom vs multiscale clean: multiscale gave slightly lower rms  
  > "the multiscale clean produced slightly lower rms and we therefore use products from that algorithm in our analysis." (Observations and Data Reduction)
- How they decided it was enough: uv cut chosen to minimize mosaic rms  
  > "The optimal rms across the mosaic is achieved with a $uv$ cut of 100 k$\lambda$." (Observations and Data Reduction)
- Limitation (authors): Dust masses are inaccurate due to optical depth and temperature assumptions  
  > "These masses are not accurate (see Figure [13](#fig:comprt) and discussion in Section [\[sec:mdist\]](#sec:mdist)), and are listed only to give a rough idea of how flux and mass are related." (Table 1)
- Caveat (inferred, ours): Gaussian size fits at beam scale are sensitive to noise and beam deconvolution
- Caveat (inferred, ours): Correlations are marginal and survival-analysis details are thin
- Caveat (inferred, ours): Projected rather than 3D distance from theta1 Ori C
- Caveat (inferred, ours): Detection threshold of 4 sigma with matching radius 0.5" may admit false matches in crowded regions

## Reproducibility

- Data public (paper): ALMA project code printed; data from ALMA archive  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA #2015.1.00534.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Flagged channel ranges
- Missing: Self-cal parameters
- Missing: Stellar masses from Fang et al. in prep
- Missing: Array configuration and exposure details
- Data volume (inferred): ~100-300 GB (136-pointing Band 7 mosaic, four spectral windows)
- Score (inferred): 3/5, Public data and a reasonably described imaging recipe with a complete source table, but flagged channels, self-cal settings and several fitting details are missing.
- Rediscovery candidate: yes, Public data, a described imaging recipe, and numeric fluxes, sizes and masses in tables that serve as answer keys.

## Links

- Method: (cite: EISNER+16) (Free-free plus dust model and previous ONC analysis)
- Method: (cite: KELLY07) (Bayesian linear regression with upper limits)
- Companion: (cite: EISNER+16) (Earlier ONC SMA/CARMA/ALMA survey)
- Related: Taurus, Lupus, Cham I, Upper Sco, sigma Ori disk surveys

## Checks

```json
{
 "quotes": 71,
 "quotes_ok": 71,
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
  "facts": 83,
  "stated": 53,
  "rate": 0.639
 },
 "evidence_ok": true
}
```

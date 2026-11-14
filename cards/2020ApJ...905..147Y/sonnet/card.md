# The ALPINE-ALMA [C II] Survey: [C II] 158 μm Emission Line Luminosity Functions at z ∼ 4-6

`2020ApJ...905..147Y` | The Astrophysical Journal 2020 | first author: Yan, Lin | arXiv: 2006.04835 | DOI: 10.3847/1538-4357/abc41c

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies
- Question: What is the [C II] 158 micron line luminosity function at z~4-6 from the UV-selected ALPINE sample, and what does it imply for evolution since z~0, models and the molecular gas density?  
  > "What is the volume density of [C II] emitters at $z \sim 4 - 6$? What is the [C II] line luminosity function (LF) at $z\sim 4 - 6$?" (Introduction)
- Target **ALPINE 118 UV-selected main-sequence galaxies in COSMOS and ECDF-S**: coordinates _not stated_; z/distance z ~ 4.40-4.58 and 5.14-5.85 (optical spectroscopic)  
  > "These 118 galaxies are chosen to have optical spectroscopic redshifts in two intervals, $z \sim 4.40 - 4.58$ and $z \sim 5.14 - 5.85$" (2.1 Summary of the ALPINE survey); distance from optical spectroscopic redshifts  
  > "These 118 galaxies are chosen to have optical spectroscopic redshifts in two intervals, $z \sim 4.40 - 4.58$ and $z \sim 5.14 - 5.85$" (2.1 Summary of the ALPINE survey)

## Data provenance

- ALMA projects: 2017.1.00428.L
- bands: Band 7 (275-373 GHz)  
  > "obtaining the [C II] spectral line and continuum observations with ALMA band 7 (275 - 373 GHz) for 118 main sequence galaxies" (2.1 Summary of the ALPINE survey)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: mean [C II] line flux RMS 0.14 Jy km/s  
  > "the mean [C II] line flux root mean square (RMS) is 0.14 Jy km/s for this sample" (2.2 The [C II] emission line measurements)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: [C II] 158 micron fine-structure line (not stated)
- Other facility **HST / COSMOS ancillary**: F814W non-detection check for a [C II] component  
  > "not detected in HST F814W band (cite: Koekemoer2007; Koekemoer2011), but detected in deep $K$-band" (4.1 Measurements based on the ALPINE UV sample)
- External data: z~4.5-5.5 UV luminosity function used for the C_UV incompleteness correction  
  > "as long as one trusts the accuracy of the state-of-the-art UV luminosity function calculation we use (cite: Ono2018)" (3.1 Luminosity function calculation) [from (cite: Ono2018)]
- External data: Total [C II] fluxes (f_fit, f_clipped) and noise estimates for all sources  
  > "This paper adopts the total [C II] flux measurements for all of the sources provided by (cite: Bethermin2020), without deblending" (2.2 The [C II] emission line measurements) [from (cite: Bethermin2020)]
- External data: Local z~0 [C II] LF benchmark  
  > "The recently published [C II] LF at $z\sim 0$ (cite: Hemmati2017) serves as the useful local bench-mark" (Introduction) [from (cite: Hemmati2017)]
- External data: 250 micron LF from SCUBA-2  
  > "We also use the 250$\mu$m LF from the SCUBA-2 survey (cite: Koprowski2017)." (4.3 Comparison with indirect observational expectations) [from (cite: Koprowski2017)]
- External data: CO(1-0) LF from ASPECS and CO(2-1) LF from COLDz  
  > "converted from the CO(1-0) LF published by the ALMA SPECtroscopic Survey (ASPECS, pink shaded region) (cite: Decarli2019)" (4.3 Comparison with indirect observational expectations) [from (cite: Decarli2019); (cite: Riechers2019)]
- External data: L_FIR/L_[CII] = 2.69 and L_IR/L_FIR = 1.3 for high-z galaxies  
  > "$\log_{10}(L_{FIR}/L_{[C\,II]}) = 2.69$ recently compiled for high-$z$ galaxies (cite: Zanella2018)" (4.3 Comparison with indirect observational expectations) [from (cite: Zanella2018)]
- External data: Molecular gas density model rho_mol(z)  
  > "we want to compare with the model for $\rho_{molgas}$ as a function of $z$ from (cite: Liu2019)" (4.5 Implications to the molecular gas mass density) [from (cite: Liu2019)]
- Simulation/model as data: Model [C II] LFs from Popping2016 and Lagache2018 compared with data  
  > "Figure [8](#fig:clfmodels) shows the model [C II] LFs from (cite: Popping2016) and (cite: Lagache2018) overlaid on the same data as shown in Figure [7](#fig:clf+fir+co)." (Comparison with theoretical predictions)

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

- ALPINE data reduction and line/continuum maps  
  > "The reduction of ALPINE data and the association with the extensive multi-wavelength ancillary data are presented in Béthermin et al. (2020) and (cite: Faisst2019), respectively." (2.1 Summary of the ALPINE survey) [from Béthermin et al. (2020)]
- Three noise estimates (aggressive, normal, secure)  
  > "which are described in Section 3.3 in (cite: Bethermin2020)" (3.2 Accounting for [C II] non-detections) [from (cite: Bethermin2020)]
- Serendipitous source sample and LF  
  > "Loiacono et al. (2020) carried out a blind search for all line emitters within the 118 data-cubes." (4.2 Comparison with the [C II] LFs based on serendipitous ALPINE sources) [from Loiacono et al. (2020)]

### Not stated but needed to reproduce (our reading)

- Table of per-source [C II] luminosities, M_UV and f_fit from Béthermin et al. 2020
- Exact Ono2018 UV LF parameters at each redshift
- Exact luminosity bin edges and the redshift-dependent maximum-redshift (V_max) values for the 8 shallower sources
- Schechter fit weighting, initial guesses and which data points entered
- Gruppioni et al. 2020 IR LF values
- Details of how the 4<z<6 geometric-mean combination was errored

## Analysis recipe

1. **Adopt total [C II] fluxes and luminosities**: Use f_fit total fluxes from Béthermin et al. 2020 without deblending; close components (<=1'') merged  
  > "For this paper, we computed the LFs using $f_{fit}$ and $f_{clipped}$." (2.2 The [C II] emission line measurements)
   - parameter: detection SNR_peak >= 3.5 (75 detections, 43 non-detections)  
  > "75 [C II] emission lines with the peak flux to noise ratio $\rm SNR_{peak}\geq3.5\sigma$ and 43 non-detections ($<3.5\sigma$)" (2.2 The [C II] emission line measurements)
   - fitting: _not stated_
   - validation: Compared f_clipped vs f_fit LFs; differences within errors  
  > "Figure [5] compares the LFs using $f_{fit}$ (which we adopt throughout this paper) and $f_{clipped}$. Within the errors, the difference is not significant." (4.1 Measurements based on the ALPINE UV sample)
2. **Compute [C II] LF with UV incompleteness correction**: Modified 1/Vmax: phi_i = 1/Δlog L × Σ C_UV,j / V_[CII],j, with C_UV from the ratio of expected UV galaxies (UV LF) to ALPINE UV galaxies per M_UV bin (width 0.5, interpolated)  
  > "The reader will note that this equation is just a modified $1/V_{max}$ method (cite: Schmidt1968). However, this is not the true $1/V_{max}$ method because the calculation is pegged directly to the published UV LF" (Luminosity function calculation)
   - parameter: redshift slices 4.403-4.585 and 5.135-5.85; luminosity bins 0.5 dex  
  > "$z_{lower}$ and $z_{upper}$ set as $4.403 - 4.585$ and $5.135 - 5.85$ respectively for the two slices" (3.1 Luminosity function calculation)
   - assumption: Area A=2 sq.deg (cancels out)  
  > "we adopted $A=2$ sq.deg (size of the COSMOS field) but this assumption cancels out in the LF calcualtion" (3.1 Luminosity function calculation)
   - fitting: _not stated_
   - validation: Alternative method spreading UV LF number density across L_[CII] bins via the M_UV-L_[CII] distribution gave fully consistent results; different binning consistent  
  > "The results are fully consistent with our method described above." (4.1 Measurements based on the ALPINE UV sample)
3. **Estimate LF uncertainties**: Error propagation of Poisson errors on N (Gehrels 1986) and C_UV error from 1000 Poisson draws per UV bin  
  > "the error on $C_{UV}$ is derived from the standard deviation of the expected number of galaxies per UV magnitude bin calculated from 1000 Poisson draws per bin" (3.1 Luminosity function calculation)
   - fitting: _not stated_
   - validation: _not stated_
4. **Add maximum contribution of non-detections**: Assign non-detections a luminosity of 3σ using whichever of aggressive/normal/secure noise maximizes counts in each bin; gives upper limits in the two lowest bins  
  > "we take the non-detections noise estimates, $\sigma$, and assign them a maximum luminosity of 3$\sigma$." (3.2 Accounting for [C II] non-detections)
   - fitting: _not stated_
   - validation: _not stated_
5. **Convert FIR and CO LFs to [C II] LFs**: L_IR/L_250um=38.5, L_IR/L_FIR=1.3, log(L_FIR/L_[CII])=2.69; CO(2-1)/CO(1-0)=1; log L'_CO/L_[CII]=0.9 from log(L_[CII]/L_CO(1-0))=3.6  
  > "we have the ratio of $\rm \log_{10}[L^{\prime}_{CO(1-0)}/L_{[CII]}] = 0.9$, which is used to convert the CO(1-0) LF" (Comparison with indirect observational expectations)
   - fitting: _not stated_
   - validation: _not stated_
6. **Fit Schechter function to combined LF estimates**: Schechter fit to this work, Loiacono et al. 2020, and converted FIR LFs  
  > "we perform a fit to the data assuming a Schechter function" (4.3 Comparison with indirect observational expectations)
   - software: scipy
   - fitting: scipy curve_fit  
  > "The fit was done using the curve$\_$fit function within the scipy package (cite: scipy)." (4.3 Comparison with indirect observational expectations)
   - validation: _not stated_
7. **Derive molecular gas mass density**: Integrate [C II] LF above L_[CII]~7e7 Lsun (from Liu2019 mu~2 and alpha_[CII]=30 Msun/Lsun) and convert with Zanella2018 relation  
  > "Therefore we start by integrating the [CII] luminosity function down to this limit giving us a luminosity density of $\mathscr{L}_{[CII]}$ is $1.2\times10^6 L_\odot$ Mpc$^{-3}$." (4.5 Implications to the molecular gas mass density)
   - assumption: alpha_[CII] ~30 Msun/Lsun with 0.3 dex scatter (M_mol/L_[CII]=15-60)  
  > "translating into a linear ratio $\rm M_{mol}/L_{[CII]} = 15 - 60\,M_\odot/L_\odot$" (4.5 Implications to the molecular gas mass density)
   - fitting: _not stated_
   - validation: Compared with Liu2019 model, ASPECS and COLDz  
  > "Within the 2$\sigma$ uncertainties, our results are consistent with those from COLDz and ASPECS." (4.5 Implications to the molecular gas mass density)

## Software

- **scipy** : Schechter function fit via curve_fit  
  > "The fit was done using the curve$\_$fit function within the scipy package (cite: scipy)." (4.3 Comparison with indirect observational expectations)
- **Astropy** : general research use  
  > "Our research made use of Astropy, a community-developed core Python package for Astronomy" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of [C II] detections / non-detections | 75 / 43 of 118 | not stated | sources | 1 | Of the 118 targets, 75 have significant [C II] detections and 43 are upper limits. |
| Schechter log L*_[CII] | 9.5 | ±0.6 | log10 Lsun | 6 | We derive $\rm log_{10}(L_{[CII]}^*/L_\odot) = 9.5\pm0.6$, $\phi^* = (8.4\pm8)\times10^{-4}$ Mpc$^{-3}$ dex$^{-1}$ and $\alpha=-1.1\pm0.3$ |
| Schechter phi* | 8.4e-4 | ±8e-4 | Mpc^-3 dex^-1 | 6 | $\phi^* = (8.4\pm8)\times10^{-4}$ Mpc$^{-3}$ dex$^{-1}$ |
| Schechter alpha | -1.1 | ±0.3 | dimensionless | 6 | $\alpha=-1.1\pm0.3$ |
| [C II] luminosity density above 7e7 Lsun | 1.2e6 | not stated | Lsun Mpc^-3 | 7 | $\mathscr{L}_{[CII]}$ is $1.2\times10^6 L_\odot$ Mpc$^{-3}$ |
| Molecular gas mass density z~4-6 (1σ) | (2-7)e7 | 1σ range | Msun Mpc^-3 | 7 | We calculate the cosmic volume averaged molecular mass density $\rho_{molgas}=(2 - 7)\times10^7M_\odot$/Mpc$^3$ at $z\sim 4 - 6$. |
| LF at z~4.5, log L=8.75 | 4.12 | ±0.76 | table units (not stated) | 2 | 8.75 & $4.12\pm0.76$ |

## Qualitative findings

- UV-selected LFs are lower limits, consistent with z~0 LF at 10^8.25-10^9.75 Lsun; indirect estimates exceed them above 10^9 Lsun  
  > "These additional LF estimates are largely above our LF at $L_{[CII]}>10^9L_{\odot}$" (abstract)
- Models of Popping2016 and Lagache2018 underestimate [C II] emitter densities  
  > "we find that available model predictions underestimate the number densities of [C II] emitters at $z\sim4-6$" (abstract)

## Claim tuples

- H: Does the [C II] LF at z~4-6 differ from z~0? | E: UV-corrected 1/Vmax LF from ALPINE targets compared with Hemmati2017 | R: Consistent with z~0 at 10^8.25-10^9.25 Lsun; possibly higher above 10^9.5 at 1-2σ | F: LFs are lower limits at least as high as z~0 | **partially**
- H: UV-faint [C II]-bright sources contribute significantly | E: Compared with serendipitous, FIR and CO converted LFs | R: Indirect LFs lie above the UV-selected LF at >10^9 Lsun | F: Strong evolution in luminous emitters is suggested | **supported**
- H: Do models reproduce the [C II] LF? | E: Overlay Popping2016 and Lagache2018 on the data | R: Popping2016 ruled out; Lagache2018 fails to match luminous emitters | F: Models underpredict | **supported**
- H: What is the molecular gas density at z~4-6? | E: Integrate LF and convert with alpha_[CII] | R: rho_mol=(2-7)e7 Msun/Mpc^3 | F: Consistent with Liu2019 and, within 2σ, with CO surveys | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Treating deimos_cosmos_818760 C and E separately was rejected as it would boost the highest bin; merged as the conservative choice  
  > "We choose to treat them as one source as the more conservative approach." (4.1 Measurements based on the ALPINE UV sample)
- How they decided it was enough: _not stated_
- Limitation (authors): UV selection misses UV-faint [C II]-bright sources, so LFs are strict lower limits; the Schechter fit has large errors  
  > "Thus, the calculated LF based on the UV-selected sample sets the lower bounds to the [C II] LF." (3.2 Accounting for [C II] non-detections)
- Caveat (inferred, ours): Schechter fit mixes lower limits, upper limits and indirect conversions, so its parameters are poorly defined
- Caveat (inferred, ours): Conversion factors (L_[CII]/L_CO, alpha_[CII]) are assumed with large scatter
- Caveat (inferred, ours): Highest bin is dominated by one UV-faint source with a large C_UV

## Reproducibility

- Data public (paper): ALMA Large Program 2017.1.00428.L; ALPINE data products are in companion papers  
  > "This paper is based on data obtained with the ALMA Observatory, under Large Program 2017.1.00428.L." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Per-source flux/luminosity catalogue (in Béthermin et al. 2020)
- Missing: Ono2018 UV LF parameters
- Missing: Schechter fit data set and weights
- Data volume (inferred): Low if using the published ALPINE catalogue (<1 GB); about 100 GB or more for re-reducing the 118 Band 7 cubes
- Score (inferred): 3/5, The LF method is clearly described and uses a public catalogue, but depends on external tables and the fit details are incomplete.
- Rediscovery candidate: no, Needs catalogues from companion papers and external LFs not given here, and the recipe omits several inputs.

## Links

- Method: Béthermin et al. (2020) (cite: Bethermin2020) (ALPINE data reduction, flux measurements, noise estimates)
- Method: (cite: Ono2018) (UV LF used for incompleteness correction)
- Companion: Loiacono et al. (2020) (serendipitous [C II] sources and LF)
- Companion: (cite: lefevre2019) (ALPINE survey description)
- Companion: (cite: Dessauges2020) (molecular gas content of ALPINE galaxies)
- Related: ALPINE
- Related: ASPECS
- Related: COLDz
- Related: A3COSMOS

## Checks

```json
{
 "quotes": 54,
 "quotes_ok": 54,
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
  "facts": 86,
  "stated": 39,
  "rate": 0.453
 },
 "evidence_ok": true
}
```

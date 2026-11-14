# Measuring the mixing scale of the ISM within nearby spiral galaxies

`2020MNRAS.499..193K` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Kreckel, Kathryn | arXiv: 2009.02342 | DOI: 10.1093/mnras/staa2743

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, milky_way_ism
- Question: How homogeneous is the 2D gas-phase metallicity distribution (after radial gradient subtraction) in nearby spiral galaxies, and over what scale are HII region metallicities correlated (the mixing scale)?  
  > "we examine the two-dimensional variation in abundances once the radial gradient is subtracted, $\Delta$(O/H), in order to quantify the homogeneity of the metal distribution and to measure the mixing scale" (abstract)
- Target **NGC 0628, NGC 1087, NGC 1672, NGC 2835, NGC 3627, NGC 4254, NGC 4535, IC 5332**: coordinates _not stated_; z/distance 9.77-16.8 Mpc (D<17 Mpc)  
  > "| NGC 0628 | $9.77\pm0.82$ | Sc | 10.2 | 0.26 | 20.9 | 8.7 | 47 | 1277 |" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00650.S, 2015.1.00925.S, 2015.1.00956.S, 2017.1.00392.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: CO(2-1) moment-zero maps at 1-2 arcsec  
  > "PHANGS-ALMA survey CO(2-1) moment-zero maps at 1-2$''$ resolution" (2.2 Ancillary data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (not stated)
- Other facility **VLT/MUSE (PHANGS-MUSE)**: Optical IFU data, HII region catalogues, metallicities, stellar masses, Halpha velocity dispersion  
  > "we use the Very Large Telescope/Multi Unit Spectroscopic Explorer (VLT/MUSE) to mosaic the central 4–8 kpc disc of 19 galaxies" (1 Introduction)
- Other facility **VLA (THINGS, VIVA, AU157)**: HI 21 cm maps for atomic gas mass  
  > "The atomic gas mass is measured from 21 cm H i emission observed at the Karl G. Jansky Very Large Array (VLA)" (2.2 Ancillary data)
- External data: HII region catalogues, metallicities and radial gradients  
  > "Images of all targets and associated H II region catalogues, along with details on the observing setup, data reduction, techniques for selecting H II regions" (2 Data) [from Kreckel2019 (Paper I)]
- External data: Rotation curve fits to CO kinematics (orbital time)  
  > "determined from high resolution rotation curve fits to the molecular gas kinematics, as traced by PHANGS-ALMA observations of CO (2-1) emission (cite: Lang2020)" (2.2 Ancillary data) [from Lang2020]
- External data: Feedback outflow velocities from CO/Halpha uncertainty principle analysis  
  > "These measurements are available globally (cite: Chevance2020; Kim2020) as well as in radial bins (cite: Chevance2020b)" (4 Measuring the correlation scale) [from Chevance2020; Kim2020; Chevance2020b]
- Simulation/model as data: Krumholz2018 stochastically forced diffusion model predictions of correlation scale and scatter, with system age 10 Gyr and f_d=0.5  
  > "we assume a fixed system age of 10 Gyr, consistent with their fiducial spiral and dwarf galaxy models, and a fraction of metals retained in the disc of $f_d$=0.5" (5.3 Comparison with mixing models)

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

- HII region selection, data reduction, metallicity prescriptions and radial gradient fits  
  > "are described in Paper I, and only briefly summarized here." (2 Data) [from Kreckel2019 (Paper I)]
- CO moment-zero maps and CO(2-1)/CO(1-0) ratio  
  > "(Leroy et al. in prep)" (2.2 Ancillary data) [from Leroy et al. in prep; den Brok et al. subm; Saito et al. in prep]
- CO velocity dispersion (moment 2) from PHANGS-ALMA  
  > "The CO velocity dispersion ($\sigma_{\rm CO}$) is measured from PHANGS-ALMA data (cite: Sun2018; Sun2020)." (2.2 Ancillary data) [from Sun2018; Sun2020]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, imaging and mask details of the PHANGS-ALMA CO maps
- Exact CO maps/products used and S/N cut
- Radial gradient fit parameters per galaxy (in Paper I)
- Binning details of correlation function
- Stellar mass maps are in prep

## Analysis recipe

1. **Compute metallicities and residuals**: Pilyugin2016 S-calibration on extinction-corrected HII region lines; subtract linear radial gradient to get Delta(O/H)  
  > "All metallicity calculations in this paper adopt the empirical (cite: Pilyugin2016) S-calibration (Scal)." (2.1 HII region metallicities)
   - assumption: Case B, Te=10^4 K, Fitzpatrick1999 law with R_V=3.1  
  > "assuming case B recombination and $T_{\rm e}=10^4$ K, we apply the (cite: Fitzpatrick1999) extinction law assuming a value of $R_V=3.1$" (2.1 HII region metallicities)
   - fitting: _not stated_
   - validation: Repeated with other calibrations in Appendix  
  > "In Appendix [7](#appendix), we repeat our calculations using other common metallicity calibrations." (2.1 HII region metallicities)
2. **Measure scatter vs spatial scale**: Standard deviation of Delta(O/H) in circular apertures of increasing diameter, min four HII regions, Cochran correction  
  > "we apply a correction based on Cochran’s theorem (assuming a normal distributions of values) when calculating $\sigma$(O/H)." (3.2 Trends with physical scale)
   - fitting: _not stated_
   - validation: Compared with 100 random shuffles of metallicities and bootstrapping over 100 realizations  
  > "We repeat this shuffling procedure 100 times for each galaxy, in order to determine the confidence interval of the signal we detect" (3.2 Trends with physical scale)
3. **Two-point correlation function and correlation scales**: Two-point correlation of Delta(O/H); scale where correlation falls to 50% and 30%  
  > "we parameterize these curves by the scale at which the metallicities remain correlated at the 30% or 50% level." (4 Measuring the correlation scale)
   - fitting: _not stated_
   - validation: Compared with randomized S_X null hypothesis  
  > "This is a significant result in all galaxies (including NGC 628) when compared to the null hypothesis, where we have randomized $S_X$." (4 Measuring the correlation scale)
4. **Relate correlation scale to local ISM properties in 2 kpc annuli**: Spearman rank correlations of 30% correlation scale with Sigma_SFR, orbital time, gas fraction, velocity dispersions (CO, Halpha), feedback velocity  
  > "Across all gas phases, significantly larger correlation scales are seen for annuli with higher gas velocity dispersion with high significance ($p<0.01$)." (4 Measuring the correlation scale)
   - parameter: Molecular gas: CO(2-1)/CO(1-0)=0.7, alpha_CO=4.4 Msun pc^-2/(K km/s) including helium  
  > "assuming a fixed CO(2-1)/CO(1-0) ratio of 0.7" (2.2 Ancillary data)
   - assumption: CO dispersion scaled to ~1 kpc scale height with sigma ∝ L^1/2  
  > "we assume a power law relation between scale length (L) and velocity dispersion as $\sigma \propto L^{1/2}$" (5.3 Comparison with mixing models)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compare with Krumholz2018 diffusion model**: Apply model per annulus using gas fraction, velocity dispersion, orbital time, age  
  > "we can apply their model directly to the annuli shown in Figures [8](#fig:pars) and [9](#fig:pars2) to predice both the correlation scale and the scatter in metallicity." (5.3 Comparison with mixing models)
   - assumption: sigma_3D^2 = 3 sigma_1D^2  
  > "$3 \times \sigma^2_{1D}= \sigma^2_{3D}$" (5.3 Comparison with mixing models)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **pPXF** : Stellar population fits to MUSE cubes for stellar mass  
  > "the stellar population is fit using the Penalized Pixel-Fitting method (pPXF; (cite: Cappellari2004; Cappellari2017))" (2.2 Ancillary data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Global scatter in Delta(O/H) | 0.03–0.05 | not stated | dex | 2 | We observe low (0.03–0.05 dex) scatter in $\Delta$(O/H) globally in all galaxies |
| Scatter on <600 pc scales | 0.02–0.03 | not stated | dex | 2 | significantly lower (0.02–0.03 dex) scatter on small ($<$600 pc) spatial scales |
| 30% correlation scale | 300–800 | not stated | pc | 3 | We measure 30% correlation scales of 300–800 pc |
| Spearman correlation of 30% scale with feedback velocity | 0.78 | p=0.005 | dimensionless | 4 | with a Spearman’s rank correlation coefficient of $\rho=0.78$ and high ($p=0.005$) significance |

## Qualitative findings

- Enhanced-abundance HII regions show no increased small-scale homogeneity, unlike reduced-abundance ones  
  > "the median $\sigma$(O/H) of H II regions with enhanced abundances show no such increased homogeneity on small scales" (5.1 Injection versus dilution of metals)

## Claim tuples

- H: Is the metallicity distribution homogeneous on small scales? | E: Scatter of Delta(O/H) in apertures vs scale, compared to shuffled nulls | R: Scatter drops to ~0.02 dex below 600 pc, consistent with errors | F: The ISM is chemically homogeneous on sub-kpc scales | **supported**
- H: What drives the mixing scale? | E: Spearman correlations of correlation scale with local properties | R: Strong correlation with gas velocity dispersion, weak with Sigma_SFR | F: Turbulence-driven mixing | **supported**
- H: Does the Krumholz2018 model reproduce observations? | E: Apply model to annuli | R: Good agreement in correlation scales; model scatter about twice observed | F: Broadly consistent | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): MUSE spectral resolution is larger than measured Halpha dispersions, so these are uncertain  
  > "without an extremely careful determination of the line spread function we caution against placing high confidence in these measurements" (2.2 Ancillary data)
- Caveat (inferred, ours): Strong-line calibration systematics may affect small-scale scatter
- Caveat (inferred, ours): Only 8 galaxies; correlation tests have small samples
- Caveat (inferred, ours): ALMA part is only ancillary and relies on unpublished products

## Reproducibility

- Data public (paper): Data available in Kreckel2019  
  > "The data underlying this article are available in (cite: Kreckel2019)." (Data Availability)
- Products in archive: _not stated_
- Missing: PHANGS-ALMA CO products (in prep)
- Missing: Paper I catalogues
- Missing: Stellar mass maps
- Data volume (inferred): Large for MUSE/ALMA cubes; only derived maps and catalogues needed
- Score (inferred): 3/5, MUSE-based catalogue analysis is described, but ALMA enters only via ancillary products and many inputs are in prep.
- Rediscovery candidate: no, ALMA is minor and the key inputs come from other papers.

## Links

- Method: Kreckel2019 (Paper I: HII region catalogue and metallicity methods)
- Method: Krumholz2018 (Stochastically forced diffusion model)
- Companion: Chevance2020 (Feedback outflow velocities)
- Related: PHANGS-MUSE
- Related: PHANGS-ALMA

## Checks

```json
{
 "quotes": 42,
 "quotes_ok": 42,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 28,
  "rate": 0.378
 },
 "evidence_ok": true
}
```

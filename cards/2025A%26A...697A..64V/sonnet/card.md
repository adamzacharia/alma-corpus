# Turbulence in protoplanetary disks: A systematic analysis of dust settling in 33 disks

`2025A&A...697A..64V` | Astronomy and Astrophysics 2025 | first author: Villenave, Marion | arXiv: 2503.05872 | DOI: 10.1051/0004-6361/202553822

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: How vertically settled and radially concentrated is millimeter dust in a uniform sample of 33 inclined, ringed protoplanetary disks, and what does this imply for turbulence strength, anisotropy and wide-orbit pebble accretion?  
  > "Here, we present the first uniform analysis of the vertical extent of millimeter dust for a representative sample of 33 protoplanetary disks" (abstract)
- Target **33 inclined, ringed protoplanetary disks (e.g. HD 163296, LkCa 15, V1094 Sco, DoAr 25, HD 142666, AS 209, HL Tau)**: coordinates _not stated_; z/distance distances 101-165 pc (per-disk values in the disk parameters table)  
  > "| HD163296  | HD163296   | 101       | 46.7       | 133.0      | 169       | 9333       | 17.0        | 1.58        | 2.04        | $10^{-7.4}$    | (1, 2)         |" (Table 1); distance from per-disk literature references listed in the disk parameters table  
  > "| HD163296  | HD163296   | 101       | 46.7       | 133.0      | 169       | 9333       | 17.0        | 1.58        | 2.04        | $10^{-7.4}$    | (1, 2)         |" (Table 1)

## Data provenance

- ALMA projects: 2016.1.00484.L, 2016.1.01164.S, 2016.1.01370.S, 2019.1.01051.S, 2018.1.01255.S
- bands: Band 6 (1.3 mm) or Band 7 (0.9 mm); wavelengths 0.89-1.33 mm  
  > "vertical extent of the particles emitting in band 6 (1.3mm) or band 7 (0.9mm)" (7 Conclusions)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ≲0.1'' (beams ~0.02-0.17'')  
  > "archival high-angular-resolution ($\lesssim0.1\ensuremath{''}$) ALMA dust observations" (abstract)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival data; some calibrated visibilities obtained from first publisher teams  
  > "we gathered calibrated visibility files either from the ALMA archive or directly from the first publisher team." (2.2 Data reduction)
- Other facility **VLT/SPHERE**: Published scattered-light images used in a qualitative comparison  
  > "these five disks have been observed with the VLT/SPHERE in scattered light." (4.5 Comparison with scattered light observations)
- External data: Stellar parameters (Teff, L*, M*, accretion rates), distances, inclinations, PAs  
  > "we compile the stellar masses and radii, which are input parameters required for the modeling" (2.1 Sample) [from references column of disk parameters table]
- External data: Gas radial widths for AS209 and HD163296 from molecular gas kinematics  
  > "We use such constraints for the two disks studied by (cite: Rosotti_2020): AS209 and HD163296." (5.2 Radial dust–gas coupling) [from (cite: Rosotti_2020)]
- External data: Disk gas sizes and gas masses used for alpha_acc  
  > "The first consists in fitting the disk rotation curve ((cite: Martire_2024) for AS209, GM Aur, HD163296" (6.2 Comparison with accretion turbulence) [from (cite: Martire_2024); (cite: Trapman_2023); (cite: Trapman_inprep); (cite: Stapper_2024)]
- External data: Lower limit on HD163296 inner ring scale height (H/R ≥ 0.056)  
  > "we consider it as the lower limit on the dust scale height of HD 163296, such that: $0.056 \leq H_{\text{d}, R}/R \leq 0.067$." (4.4 Comparison with previous millimeter studies) [from (cite: Doi_Kataoka_2021; Liu_2022)]
- External data: LkCa 15 dust ring width w_d  
  > "LkCa 15 (using $w_d$ value from (cite: Facchini_2020))" (5.2 Radial dust–gas coupling) [from (cite: Facchini_2020)]
- Simulation/model as data: MCFOST radiative transfer models (4 settling levels per disk) fit to the data and uploaded to zenodo  
  > "The final models have been uploaded to a zenodo repository ([zenodo.14056832](https://doi.org/10.5281/zenodo.14056832))." (3.3 Fitting the dust surface brightness)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 5.1.1-5 (for imaging)  
  > "using CASA version 5.1.1-5, consistently with the version used to generate the DSHARP images." (2.2 Data reduction)
- pipeline version: _not stated_
- archive products used as is: Calibrated visibilities taken from archive or first publisher teams  
  > "we gathered calibrated visibility files either from the ALMA archive or directly from the first publisher team." (2.2 Data reduction)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Data from first teams were already self-calibrated; archive data were self-calibrated with the NRAO automated script (successful for V1094 Sco and ISO-Oph 17)  
  > "we employed the automated self-calibration script developed at NRAO[^1], which was successful to improve the data quality of V1094 Sco and ISO-Oph 17." (2.2 Data reduction)

### Imaging

- task: tclean, mfs, nterms=1  
  > "All images were generated with the spectral model `mfs` and `nterms=1`." (2.2 Data reduction)
- deconvolver: multi-scale, cleaned to ~5σ  
  > "A multi-scale synthesis was used for all disks and the images were cleaned up to $\sim5\sigma$." (2.2 Data reduction)
- weighting robust: Briggs, robust between -0.5 and 0.5 (per disk in table)  
  > "We used a briggs weighting, with a `robust` parameter between -0.5 and 0.5" (2.2 Data reduction)
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
- final rms: per-disk rms ~0.8-10e-5 Jy/beam in tables  
  > "We also report the root mean square (rms) of the final images in those tables." (2.2 Data reduction)

### Inherited from earlier work

- Modeling approach (iterative surface density fit with MCFOST, settling prescription, Sc=1.5)  
  > "We follow the approach that (cite: Pinte_2016) developed for the case of HL Tau, and which was also used by (cite: Pizzati_2023) on 15 DSHARP disks." (3 Radiative transfer modeling) [from (cite: Pinte_2016); (cite: Pizzati_2023)]
- Imaging done consistently with DSHARP images  
  > "consistently with the version used to generate the DSHARP images." (2.2 Data reduction) [from (cite: Andrews_2018)]
- Settling prescription  
  > "We implement differential dust settling, using the prescription of (cite: Fromang_Nelson_2009)." (3.2 Disk structure) [from (cite: Fromang_Nelson_2009)]
- Upper/lower gas width limits for radial trapping  
  > "we follow the simpler approach of (cite: Dullemond_2018) in order to obtain a reasonable upper and lower limit for the radial width of the gas." (5.2 Radial dust–gas coupling) [from (cite: Dullemond_2018)]

### Not stated but needed to reproduce (our reading)

- Scale/pixel size and image size for tclean imaging
- Multiscale scales and masks used
- Exact data-reduction steps and self-calibration parameters for datasets from first publisher teams
- Details of the MCFOST setup (photon number, dust composition fractions, bulk density, grain porosity)
- Exact definition of azimuthal wedge positions and visual exclusion criteria for the best model
- Which fields/channels were used for combined multi-project datasets and any flux/astrometric alignment
- How 'peak/median' regions were chosen visually

## Analysis recipe

1. **Image archival visibilities**: Gather calibrated visibilities, self-calibrate if needed, image with tclean, deproject image using inclination  
  > "Finally, we generate a deprojected image based on the inclinations reported in" (2.2 Data reduction)
   - software: CASA, tclean
   - parameter: mfs, nterms=1, multiscale, robust -0.5 to 0.5, clean to ~5σ  
  > "All images were generated with the spectral model `mfs` and `nterms=1`." (2.2 Data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit dust surface density iteratively on major axis**: Initial Sigma_d from I/(B_nu kappa), then MCFOST models, ft + tclean synthetic images, deprojection, correction by data/model ratio until 5% agreement or 20 iterations; applied between 5 au and Rout  
  > "We repeat the steps until the model brightness profile agrees with the data within 5% or after 20 iterations, whichever is first." (3.3 Fitting the dust surface brightness)
   - software: mcfost, CASA
   - parameter: 30° wedge on major axis; 4 settling levels alpha_z,MCFOST 2e-4 to 0.2  
  > "using a wedge with an opening angle of 30$^\circ$, averaged on both sides" (3.3 Fitting the dust surface brightness)
   - assumption: Gas scale height 10 au at 100 au with exponent 1.1; grain sizes 0.005 µm-3 mm, n(a)∝a^-3.5, 100 bins; gas-to-dust 100; Sc=1.5; initial kappa=13.27 cm2/g, T=20(r/100au)^-q  
  > "The gas-to-dust ratio is constant within the disk and assumed to be 100." (3.2 Disk structure)
   - assumption: Stellar radius artificially increased for GO Tau, GW Lup, HL Tau, Oph163131 to warm models  
  > "We performed this by artificially increasing the stellar radius, and thus the stellar luminosity, in the modeling" (3.3 Fitting the dust surface brightness)
   - fitting: Iterative multiplicative correction of surface density (no sampler)  
  > "we produce a corrected dust surface density profile by multiplying the initial surface density profile by the ratio data over model." (3.3 Fitting the dust surface brightness)
   - validation: Model agrees with data within 5% on major axis  
  > "within 5% or after 20 iterations" (3.3 Fitting the dust surface brightness)
3. **Select best settling model from azimuthal cuts**: Compare data and model profiles in six 30° wedges using normalized chi2 and Hausdorff-distance metric plus visual check of gap, outer edge and ring effects  
  > "we obtained six wedges of 30$^\circ$. They go from the minor axis to 15$^\circ$ from the major axis" (3.4 Identifying the best model)
   - parameter: good models: chi2 ≤ 8 and S ≤ 1.2  
  > "we identify that models with $\chi^2 \leq 8$ and $\mathscr{S} \leq 1.2$ are generally good models." (3.4 Identifying the best model)
   - fitting: _not stated_
   - validation: Visual inspection combined with metrics  
  > "The constraints reported in [\[tab:results\]](#tab:results) reflect the combined use of the metrics and of our visual analysis to exclude models." (3.4 Identifying the best model)
4. **Derive dust scale height H_d/R**: Fit 1D Gaussian to MCFOST vertical distribution of the grain size emitting most at the observing wavelength, at each radius; average in region and divide by mean radius  
  > "we fit the `mcfost` vertical distribution of these grains, at each radius, with a 1D Gaussian." (3.5 Getting the dust scale height)
   - software: mcfost
   - fitting: 1D Gaussian fit  
  > "To estimate their dust scale height, we fit the `mcfost` vertical distribution of these grains, at each radius, with a 1D Gaussian." (3.5 Getting the dust scale height for the best model)
   - validation: _not stated_
5. **Vertical and radial dust-gas coupling and anisotropy**: alpha_z/St=[(Hg/Hd)^2-1]^-1 with Hg from model or hydrostatic equilibrium; alpha_r/St=[(wg/wd)^2-1]^-1 with wd from Gaussian fits to model surface density rings; ratio gives alpha_z/alpha_r  
  > "Assuming a balance between vertical stirring and settling, the ratio $\alpha_z/\text{St}$ relates to the dust and the gas scale height" (5.1 Vertical dust-gas coupling)
   - parameter: mu=2.3; wg,min=Hg,temp; wg,max=ring peak to gap minimum  
  > "we assume that the distance from the peak of the ring to the deepest point in the gap inside of the ring is the upper limit for the gas width" (5.2 Radial dust–gas coupling)
   - assumption: Rings are pressure maxima  
  > "Under the assumption that the rings correspond to pressure bumps" (5.2 Radial dust–gas coupling)
   - fitting: Gaussian fit to rings; uncertainty = std over four models  
  > "The uncertainties reported in [\[tab:radialTrapping\]](#tab:radialTrapping) correspond to the standard deviation of the fit for all four models of each disk." (5.2 Radial dust–gas coupling)
   - validation: Compared with previous studies for common rings  
  > "We find a good agreement in the resulting constraints for the dust rings in common between our sample and previous studies" (5.2 Radial dust–gas coupling)
6. **Fragmentation-limited turbulence and comparison with accretion alpha**: alpha_frag=(vfrag/cs) sqrt(zeta/3) with zeta=alpha_z/St; alpha_acc=(Mdot/Mdisk)(mu mp/kT) Omega Rc^2 for 14 regions  
  > "We assumed a fragmentation velocity of $v_\text{frag}=$ 1 ms$^{-1}$, and used $\zeta=\alpha_z/\text{St}$" (6.1 Estimating turbulence in the fragmentation limit)
   - parameter: vfrag = 1 m/s; T from MCFOST midplane averaged over constraint domain  
  > "we considered the midplane temperature in the `mcfost` models, averaged over the radial domain of the constraint" (6.1 Estimating turbulence in the fragmentation limit)
   - assumption: Dust size limited by fragmentation; vertical turbulence dominant or comparable to radial  
  > "Effectively, this assumes that vertical turbulence is dominant over, or comparable to radial turbulence." (6.1 Estimating turbulence in the fragmentation limit)
   - fitting: _not stated_
   - validation: Compared with Jiang et al. 2024 and Zagaria et al. 2023  
  > "We find that our results are consistent with their findings" (6.1 Estimating turbulence in the fragmentation limit)

## Software

- **CASA** 5.1.1-5: tclean imaging, ft for synthetic visibilities  
  > "This is done within CASA using the `ft` function." (3.3 Fitting the dust surface brightness)
- **mcfost** : radiative transfer modeling of disks  
  > "We use the radiative transfer code `mcfost` (cite: Pinte_2006; Pinte_2009) to model the brightness of the disks." (3.3 Fitting the dust surface brightness)
- **NRAO auto_selfcal** : automated self-calibration of archive data  
  > "we employed the automated self-calibration script developed at NRAO[^1]" (2.2 Data reduction)
- **CARTA** : listed as used software  
  > "`CARTA` ([10.5281/zenodo.3377984](https://zenodo.org/doi/10.5281/zenodo.3377984))." (Acknowledgements)
- **Matplotlib, Numpy, scipy** : listed as used software  
  > "`Matplotlib` (cite: Hunter_2007), `Numpy` (cite: Harris_2020), `scipy` (cite: Scipy_2022)" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disks with dust height constraints | 23 of 33 | not stated | disks | 3 | Our modeling allows us to constrain the dust vertical extent in 23 out of the 33 systems considered. |
| Outer-disk upper limit H_d/R (max over five thick-inner disks) | ≤ 0.046 | not stated | dimensionless | 4 | with an upper limit of $H_\text{d,R}/R \leq 0.046$ in all cases, but as low as $H_\text{d,R}/R \leq 0.005$ in the outer ring of HD163296 |
| HD163296 inner ring H_d/R | 0.006 - 0.067 | not stated | dimensionless | 4 | $0.006 \leq H_{\text{d}, R}/R\leq 0.067$ |
| Rings with alpha_r/St<1 (radial trapping) | 11 of 21 | not stated | rings | 5 | We find that 11 rings are consistent with radial dust trapping ($\alpha_r/\text{St}<1$), while the other 10 rings do not necessarily require strong trapping. |
| Upper limits on alpha_z/alpha_r median | 1.60 (range 0.06-8.57) | not stated | dimensionless | 5 | We find that the upper limits for $\alpha_z/\alpha_r$ vary between 0.06 and 8.57, with a median value of about 1.60. |
| alpha_frag upper limits median | 1.1e-3 (range 1.7e-4 to 5.8e-3) | not stated | dimensionless | 6 | reaches upper limits between $1.7\times 10^{-4}$ and $5.8 \times10^{-3}$, with a median of $1.1\times 10^{-3}$ |
| alpha_acc median | 3.0e-3 (range 3.0e-4 to 2.0e-2) | not stated | dimensionless | 6 | We find accretion turbulence levels between $3.0\times 10^{-4}$ and $2.0\times 10^{-2}$, with a median of $3.0\times 10^{-3}$. |
| Regions where alpha_frag < alpha_acc | 8 of 14 | not stated | cases | 6 | in 8 cases out of 14, the upper limits on turbulence we put in this paper are lower than what is required to drive accretion |

## Qualitative findings

- Outer parts of all 23 constrained disks are vertically settled; five show finite dust height in inner regions  
  > "In all 23 systems for which constraints could be obtained, we find that the outer parts of the disks are vertically settled." (abstract)
- VSI incompatible with most rings, SI or planet-disk interaction more plausible  
  > "The apparent turbulence anisotropy suggests that VSI is incompatible with most of the rings in our sample" (7 Conclusions)

## Claim tuples

- H: Are the outer parts of protoplanetary disks vertically settled? | E: MCFOST modeling of 33 disks with four settling levels compared in azimuthal cuts | R: Upper limits H_d/R ≲ 0.07 in all 23 constrained disks | F: Outer disks are vertically thin | **supported**
- H: Does dust thickness vary with radius? | E: Constraints within and outside ~half the dust radius | R: Five disks have lower limits inside; three clearly thicker inner ring | F: alpha_z/St decreases radially in these sources | **partially**
- H: Is turbulence anisotropic and is VSI viable? | E: Compare alpha_z/St and alpha_r/St in 20 rings | R: Vertical turbulence comparable to or weaker than radial in most rings | F: VSI incompatible with most rings | **supported**
- H: Can turbulence explain accretion? | E: Compare alpha_frag upper limits with alpha_acc | R: 8 of 14 regions have alpha_frag below alpha_acc | F: In a few sources turbulence cannot be the main accretion driver; no strong population-level conclusion | **partially**

## Reasoning

- Why this data: Inclined disks with rings and high-resolution archival ALMA data allow constraint of vertical and radial dust concentration  
  > "systems at intermediate inclinations that possess clear ring and gap features are favorable targets to constrain both the vertical" (1 Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Degeneracy between optical thickness and true scale height; fixed grain size distribution; Gaussian fit to one grain size; no radially variable settling or dust feedback  
  > "We note here the degeneracy between the optical thickness and the true scale height." (8.2 Caveats and future prospects)
- Limitation (authors): Assumption that rings are pressure maxima and that grains are fragmentation limited  
  > "First we assumed that the dust size is limited by fragmentation." (8.2 Caveats and future prospects)
- Caveat (inferred, ours): Results depend on fixed gas scale height and grain size distribution and Schmidt number
- Caveat (inferred, ours): Stellar radii artificially inflated in four disks affect temperature and masses
- Caveat (inferred, ours): Best-model selection partly visual and not statistically rigorous
- Caveat (inferred, ours): Mix of band 6/7 and varied resolutions across disks

## Reproducibility

- Data public (paper): Visibilities, cleaned images and reduction parameters on zenodo; models on zenodo  
  > "The data can be found on zenodo ([zenodo.14054952](https://doi.org/10.5281/zenodo.14054952)). The models are also available ([zenodo.14056832](https://doi.org/10.5281/zenodo.14056832))." (Data availability)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: Analysis scripts for metrics and wedge extraction
- Missing: MCFOST full parameter files (beyond zenodo models)
- Missing: Some datasets obtained privately from first teams
- Data volume (inferred): Hundreds of GB to ~1 TB for calibrated visibilities of ~22 projects (zenodo products smaller)
- Score (inferred): 3/5, Data and models are on zenodo and method is described, but model-selection is partly visual and many settings are unstated.
- Rediscovery candidate: no, Best model selection involves visual judgment and heavy radiative transfer iteration; setup details incomplete.

## Links

- Method: (cite: Pinte_2016) (Original modeling approach for HL Tau)
- Method: (cite: Pizzati_2023) (Same method applied to 15 DSHARP disks)
- Method: (cite: Doi_Kataoka_2021) (Ring azimuthal effect formula)
- Companion: (cite: Andrews_2018) (DSHARP data source for 15 disks)
- Companion: (cite: Long_2018) (Taurus survey data for several disks)
- Related: DSHARP
- Related: ODISEA
- Related: exoALMA
- Related: AGE-PRO

## Checks

```json
{
 "quotes": 75,
 "quotes_ok": 75,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 5,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2016.1.01370.S"
 ],
 "obscore_codes_not_in_card": [
  "2013.1.00498.S",
  "2015.1.00888.S",
  "2016.1.00460.S",
  "2016.1.00545.S",
  "2016.1.00771.S",
  "2016.1.01205.S",
  "2016.1.01239.S",
  "2017.1.01151.S",
  "2017.1.01167.S",
  "2017.1.01460.S",
  "2017.A.00006.S",
  "2018.1.00028.S",
  "2018.1.00689.S",
  "2018.1.00958.S",
  "2018.1.01230.S",
  "2018.1.01755.S",
  "2018.A.00030.S"
 ],
 "codes_printed_but_missing": [
  "2013.1.00498.S",
  "2015.1.00888.S",
  "2016.1.00460.S",
  "2016.1.00545.S",
  "2016.1.00771.S",
  "2016.1.01205.S",
  "2016.1.01239.S",
  "2017.1.01151.S",
  "2017.1.01167.S",
  "2017.1.01460.S",
  "2017.A.00006.S",
  "2018.1.00028.S",
  "2018.1.00689.S",
  "2018.1.00958.S",
  "2018.1.01230.S",
  "2018.1.01755.S",
  "2018.A.00030.S"
 ],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 91,
  "stated": 57,
  "rate": 0.626
 },
 "evidence_ok": true
}
```

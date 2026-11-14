# Star Formation Efficiencies at Giant Molecular Cloud Scales in the Molecular Disk of the Elliptical Galaxy NGC 5128 (Centaurus A)

`2019ApJ...887...88E` | The Astrophysical Journal 2019 | first author: Espada, D. | arXiv: 1906.01237 | DOI: 10.3847/1538-4357/ab262d

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars, milky_way_ism
- Question: What is the resolved Kennicutt-Schmidt star formation law and star formation efficiency at GMC scales (~40 pc) in the molecular disk of the elliptical galaxy Cen A?  
  > "The main goal of this paper is to provide the resolved KS SF law at giant molecular cloud (GMC) scales within the nearest giant elliptical and radio galaxy, NGC 5128 (Cen A)" (1 Introduction)
- Target **NGC 5128 (Centaurus A)**: coordinates _not stated_; z/distance 3.8 Mpc (1" = 18 pc)  
  > "Cen A is at a distance of $D$ $\simeq$ 3.8 Mpc ((cite: 2010PASA...27..457H), where 1$''$ = 18 pc)" (1 Introduction); distance from Harris et al. 2010 (cite: 2010PASA...27..457H)  
  > "Cen A is at a distance of $D$ $\simeq$ 3.8 Mpc ((cite: 2010PASA...27..457H), where 1$''$ = 18 pc)" (1 Introduction)

## Data provenance

- ALMA projects: 2013.1.00803.S
- bands: _not stated_
- frequencies and spectral setup: CO(1-0) SPW 937.5 MHz bandwidth (~2450 km/s), 1.2 km/s resolution (488.281 kHz); extra SPWs at 112.914, 100.999, 102.699 GHz with 1875 MHz bandwidth  
  > "had a bandwidth of $\sim$2450 km s$^{-1}$ (937.5 MHz) and a velocity resolution of 1.2 km s$^{-1}$ (488.281 kHz)." (2.1 ALMA CO(1–0) Observations)
- continuum bandwidth: _not stated_
- arrays: 12m (extended and compact), 7m, Total Power  
  > "The observations include 12m, 7m, and Total Power (TP) arrays, and thus the maps capture information from large to small spatial scales." (2.1 ALMA CO(1–0) Observations)
- configurations: _not stated_
- baselines: Longest baselines 650.3 m (extended 12m) and 348.5 m (compact 12m)  
  > "The extended and compact 12m array configurations had longest baseline lengths of 650.3 m and 348.5 m, respectively." (2.1 ALMA CO(1–0) Observations)
- angular resolution: ~1" (18 pc)  
  > "with high angular resolution ($\sim1\ensuremath{''}$, or 18 pc)" (abstract)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 27.8/13.9/57.2/116.2 min for extended 12m / compact 12m / 7m / TP  
  > "The total time on source for extended 12m / compact 12m / 7m and TP arrays were 27.8/13.9/57.2/116.2 min." (2.1 ALMA CO(1–0) Observations)
- observing dates: 2014-06 to 2015-04  
  > "The ALMA CO datasets were obtained during 2014 and 2015 as part of program 2013.1.00803.S (P.I. D. Espada)." (2.1 ALMA CO(1–0) Observations)
- pi or archival as stated: PI D. Espada program  
  > "as part of program 2013.1.00803.S (P.I. D. Espada)" (2.1 ALMA CO(1–0) Observations)
- Line: CO J=1-0 (115.271 GHz)
- Other facility **Spitzer IRAC/MIPS**: 3.6, 8, 24 um maps for SFR tracing  
  > "We compiled *Spitzer* 3.6 $\mu$m (emission mostly from the old stellar population), 8 $\mu$m" (2.2 Spitzer)
- Other facility **GALEX**: FUV image for SFR  
  > "investigated through the *Galaxy Evolution Explorer (GALEX)* (cite: 2005ApJ...619L...1M) image, delivered by (cite: 2007ApJS..173..185G)" (2.3 GALEX FUV Data)
- External data: 70 um flux and MIPS 24/70/160 um flux densities for Cen A  
  > "(from the 70 $\mu$m flux in (cite: 2012MNRAS.423..197B))" (4.2 Global SFR) [from (cite: 2012MNRAS.423..197B)]
- External data: IRAC 3.6 and 8 um maps  
  > "The IRAC 3.6 $\mu$m and 8 $\mu$m maps used in this paper were presented in (cite: 2006ApJ...641L..29Q) and (cite: 2006ApJ...645.1092Q)." (2.2 Spitzer) [from (cite: 2006ApJ...641L..29Q); (cite: 2006ApJ...645.1092Q)]
- External data: XCO for CND of 4e20 from LVG analysis motivating 5e20  
  > "$X_{\rm CO}$ = 4 $\times$ 10$^{20}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$" (3.2 Molecular Gas Mass) [from (cite: 2014A&A...562A..96I)]

## Processing

### Calibration

- pipeline or manual: Standard calibration with scriptForPI.py  
  > "The calibration scheme for all the datasets was standard." (2.1 ALMA CO(1–0) Observations)
- casa version: CASA 5.1.1  
  > "we opted to perform the data reduction under version 5.1.1 using the scriptForPI.py script provided by ALMA." (2.1 ALMA CO(1–0) Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ceres, Titan, Mars (per Table)  
  > "| uid://A002/X83dbe6/X9ec | 2014-06-11 | 27.8 | ext. 12m array | Ceres, J1427-4206, J1321-4342 |" (Table 1)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.2" pixel  
  > "(the size of a pixel is 0.2$''$ $\times$ 0.2$''$)" (2.1 ALMA CO(1–0) Observations)
- image size: _not stated_
- masking: Smoothed cube (20x20 pix Gaussian, 3 chan boxcar), 1sigma mask applied to original cube after visual inspection  
  > "Then we obtained masks for regions above a 1$\sigma$ threshold in the CO(1–0) smoothed datacube, which were then applied to the original datacube after visual inspection." (2.1 ALMA CO(1–0) Observations)
- multiscale scales: _not stated_
- continuum subtraction: Line-free continuum subtraction before concatenation  
  > "We calibrated each of the interferometric datasets independently and concatenated them after performing line-free continuum subtraction." (2.1 ALMA CO(1–0) Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12m, 7m and TP concatenated; TP converted with 41 Jy/K  
  > "A scaling factor of 41 Jy K$^{-1}$ between $T_a^{*}$ and flux density (Kelvin to Jy/beam factor) as obtained by the observatory using a bright quasar for band 3 was applied" (2.1 ALMA CO(1–0) Observations)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- XCO = 2e20 for outer disk and (5±2)e20 for CND derived with virial method  
  > "The factor for the external regions of the disk mass was obtained in Paper II using the virial method" (3.2 Molecular Gas Mass) [from Paper II (Miura et al. 2019) (cite: PaperII)]
- Molecular gas mass formula and conversion  
  > "Finally, we calculated the molecular gas masses as in (cite: 2013ARA&A..51..207B):" (3.2 Molecular Gas Mass) [from (cite: 2013ARA&A..51..207B)]
- SFR calibrations (FUV+24, 24, 70, TIR)  
  > "we use the homogenized SF calibrations compiled by (cite: 2013seg..book..419C)" (4.2 Global SFR) [from (cite: 2013seg..book..419C)]
- Local 24 um SFR recipe used to calibrate 8 um PAH  
  > "using the local recipe by (cite: 2007ApJ...666..870C) calibrated on 220 Hii knots in star forming regions from 33 nearby galaxies" (5 Spatially Resolved KS Law) [from (cite: 2007ApJ...666..870C)]

### Not stated but needed to reproduce (our reading)

- Imaging parameters (weighting, robust, tclean deconvolver, mosaic gridder, cleaning threshold) are not given
- Final synthesized beam and rms noise of the combined cube
- Line-free channels used for continuum subtraction
- How TP data were combined with interferometer data (feather vs joint deconvolution)
- Spitzer map convolution/regridding details and the AGN-contaminated pixel mask
- GMM initialisation seeds and details of the orthogonal regression fit
- Mask definitions of regions (CND, arms, parallelogram, outer disk)

## Analysis recipe

1. **Calibrate and combine ALMA 12m, 7m, TP CO(1-0) data and make moment maps**: Standard CASA calibration per dataset, concatenation after continuum subtraction, smoothing-based masking to produce moment maps  
  > "Finally, we produced moment maps." (2.1 ALMA CO(1–0) Observations)
   - software: CASA
   - parameter: CASA 5.1.1 with scriptForPI.py  
  > "we opted to perform the data reduction under version 5.1.1 using the scriptForPI.py script provided by ALMA." (2.1 ALMA CO(1–0) Observations)
   - fitting: _not stated_
   - validation: Compared combined cube profile to ALMA single dish profile  
  > "Fig. [\[co1-0spectra\]](#co1-0spectra) shows the good agreement between the ALMA single-dish CO(1–0) profile and that obtained from the masked combined CO(1–0) data cube." (2.1 ALMA CO(1–0) Observations)
2. **Derive CO luminosity and molecular gas mass**: L_CO from integrated flux; M_mol = 4.3 X2 L_CO including 1.36 helium factor  
  > "$$\begin{equation}
  M_{\rm mol} [{\rm M}_\odot] = 4.3 \times X_{\rm 2}~L_{\rm CO(1-0)} , 
 
\end{equation}$$" (3.2 Molecular Gas Mass)
   - parameter: XCO = 2e20 outer disk, 5e20 CND  
  > "$X_{\rm CO}$ = 5 $\times$ 10$^{20}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$ for the CND" (3.2 Molecular Gas Mass)
   - assumption: Distance 3.8 Mpc; factor 1.36 for heavy elements  
  > "Cen A is at a distance of $D$ $\simeq$ 3.8 Mpc" (1 Introduction)
   - fitting: _not stated_
   - validation: Compared to SEST luminosity and Israel et al. 2014 fluxes (within 10%)  
  > "agrees to within 10% (around 4500 Jy km s$^{-1}$)" (3.2 Molecular Gas Mass)
3. **Validate 8 um PAH as SFR tracer and calibrate it**: Pixel-to-pixel comparison of stellar-subtracted 8 um PAH with 24 um after convolving to 6"; linear fit  
  > "The 8 $\mu$m PAH map was convolved to the FWHM of the 24 $\mu$m map (6$''$)." (4.1 Validity)
   - parameter: PAH = 8um - 0.232 x 3.6um  
  > "$L_\nu\ ({\rm PAH}) = L_\nu\ (8\,\mu{\rm m}) - 0.232 \times L_\nu\ (3.6\,\mu{\rm m})$" (2.2 Spitzer)
   - assumption: 3.6 um traces stellar emission only  
  > "assuming that fluxes at 3.6 $\mu$m trace stellar emission only" (2.2 Spitzer)
   - fitting: Linear fit in log space, inner 10" excluded  
  > "only data points outside the inner 10$''$ are shown because of the difficulty to subtract the bright central AGN component" (4.1 Validity)
   - validation: Correlation coefficient 0.98 over two orders of magnitude  
  > "We find a very tight (with a correlation coefficient of 0.98) linear correlation" (4.1 Validity)
4. **Derive global SFR**: Apply FUV+24, 24, 70 um and TIR calibrations  
  > "All these estimates of global SFR lead to a consistent result for a SFR in Cen A of about 1 $M_\odot$ yr$^{-1}$." (4.2 Global SFR)
   - assumption: Kroupa IMF  
  > "given by the double-power law expression with slope $-1.3$ in the range $0.1-0.5\,M_\odot$" (4.2 Global SFR)
   - fitting: _not stated_
   - validation: Compared to IRAS-based literature SFRs  
  > "The SFRs we have obtained are also in agreement with previous measurements in the literature obtained from IRAS data." (4.2 Global SFR)
5. **Build resolved KS law and SFE maps at 43 pc**: Regrid CO and 8 um PAH to 2.4" pixels; SFR surface density via log Sigma_SFR = 0.844 log Sigma_L8 - 30.923; inclination correction 70 deg; fit orthogonal distance regression  
  > "The pixel size in our analysis is 2.4$''$ (or 43 pc, i.e. that of the 8 $\mu$m map)." (5 Spatially Resolved KS Law)
   - software: scikit-learn
   - parameter: Sigma_mol completeness ~4 Msun/pc2 (3 sigma, 10 km/s)  
  > "complete down to surface densities of $\Sigma_{\rm mol} \simeq 4\,M_\odot\,{\rm pc}^{-2}$" (5 Spatially Resolved KS Law)
   - assumption: Fixed inclination 70 deg  
  > "Our surface density maps have been corrected by a fixed inclination of 70$^\circ$." (5 Spatially Resolved KS Law)
   - fitting: Gaussian mixture model (2 components, full covariance chosen by BIC) after removing 19 AGN points; orthogonal distance regression  
  > "A Bayesian Information Criterion (BIC) selects the best model, which is the one obtained with the full covariance matrix" (5.1 KS Law)
   - validation: Compared fit with Boquien et al. 2011 calibration  
  > "The two fits have a very similar slope but the (cite: 2011AJ....142..111B) intercept is slightly higher than the one we find." (5 Spatially Resolved KS Law)

## Software

- **CASA** 5.1.1: Calibration and imaging of ALMA data  
  > "Data calibration and imaging were performed using the Common Astronomy Software Applications (cite: 2007ASPC..376..127M)." (2.1 ALMA CO(1–0) Observations)
- **scikit-learn** : Gaussian mixture model clustering  
  > "We use a Gaussian mixture model (GMM), based on an iterative expectation - maximization algorithm" (5.1 KS Law)
- **Astropy** : Data analysis  
  > "This research made use of Astropy, a community-developed core Python (http://www.python.org) package for Astronomy" (Acknowledgments)
- **MIPS Data Analysis Tool** : Processing MIPS post-BCD data  
  > "The MIPS data are post-BCD (higher-level products) processed using the MIPS Data Analysis Tool (cite: 2005PASP..117..503G)." (2.2 Spitzer)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(1-0) luminosity | 3.47e8 | not stated | K km/s pc^2 | 2 | $$L_{\rm CO(1-0)} = 3.47 \times 10^8\,{\rm K\,\mbox{km s$^{-1}$}\,  pc}^{2}  .$$ |
| Total molecular gas mass | 1.6e9 | not stated | Msun | 2 | The total molecular gas mass in the observed field is $M_{\rm mol}$ $\simeq$ 1.6 $\times$ 10$^{9}$ $M_\odot$. |
| SFR from FUV+24um | 1.13 | 0.09 | Msun/yr | 4 | ${\rm SFR_{\rm FUV+24\,\mu{\rm m}}} = 1.13 \pm 0.09\,M_\odot\,{\rm yr}^{-1}$ |
| SFR from 24um | 1.06 | 0.11 | Msun/yr | 4 | ${\rm SFR}_{24\,\mu{\rm m}} = 1.06 \pm 0.11\,M_\odot\,{\rm yr}^{-1}$ |
| SFR from TIR | 1.38 | 0.17 | Msun/yr | 4 | SFR$_{\rm TIR}$ = 1.38 $\pm$ 0.17 $M_\odot$ yr$^{-1}$ for Cen A |
| Global SFE | 0.6 (depletion time 1.5 Gyr) | not stated | Gyr^-1 | 5 | so the SFE is 0.6 Gyr$^{-1}$ (or depletion time $\tau =$ 1.5 Gyr) |
| KS slope (orthogonal regression), all data | 0.63 (intercept -2.4) | not stated | dimensionless | 5 | The slope of the orthogonal distance regression fit to the data points characterizing the SF law is $N$ = 0.63 (intercept is –2.4). |
| KS slope in CND | 0.28 (intercept -1.6) | not stated | dimensionless | 5 | for the CND $N$ = 0.28, and intercept –1.6 |
| Mean SFE CND / outer disk | 0.32 / 1.29 | stddev 0.24 / 0.93 | Gyr^-1 | 5 | / CND / 1.65 / 0.32 / 0.26 / 0.24 / |
| 8um PAH vs 24um linear fit slope | 1.01 (intercept 0.71) | not stated | dimensionless | 3 | \log F_\nu(\rm 8\,\mu{\rm m}\,PAH) = 1.01 \times \log F_\nu(24\,\mu{\rm m}) + 0.71 |

## Qualitative findings

- ALMA reveals filamentary molecular components more extended than previously seen  
  > "we reveal the presence of filamentary components more extended than previously seen, up to a radius of 4 kpc" (abstract)

## Claim tuples

- H: Is the global SFE of Cen A suppressed like other early-type galaxies? | E: Combined ALMA gas mass with Spitzer/GALEX SFR | R: M_mol 1.6e9 Msun, SFR ~1 Msun/yr, SFE 0.6 Gyr^-1 | F: Global SFE is similar to disk galaxies; not suppressed after the minor merger | **supported**
- H: Is the SFE in the CND enhanced like in other AGN circumnuclear regions? | E: Pixel-based SFE map at 40 pc | R: CND mean SFE 0.3 Gyr^-1 vs 1.3 in outer disk | F: CND SFE is lower by about a factor of 4, likely due to shear and AGN feedback | **supported**
- H: Is 8 um PAH a reliable SFR tracer in Cen A? | E: Pixel-to-pixel comparison to 24 um | R: Correlation 0.98, slope 1.01 | F: 8 um PAH is reliable and used for resolved SFR | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: 8 um chosen over 24 um for better angular resolution (2.4" vs 6.0")  
  > "we chose the 8 $\mu$m band for our analysis because of its higher angular resolution" (4.1 Validity)
- How they decided it was enough: _not stated_
- Limitation (authors): Large scatter, projection effects and warped disk uncertainty in the KS fits; XCO uncertainty in CND  
  > "We note however that the scatter is large" (5.1 KS Law)
- Caveat (inferred, ours): CND SFE depends strongly on assumed XCO (5e20) and on 8 um PAH calibration near the AGN
- Caveat (inferred, ours): Single fixed inclination of 70 deg for a warped disk
- Caveat (inferred, ours): 8 um PAH calibration is tied to the 24 um local recipe, with no independent check at 40 pc
- Caveat (inferred, ours): Hot AGN dust may contaminate the 8 um in the CND

## Reproducibility

- Data public (paper): ALMA program 2013.1.00803.S, Spitzer Heritage Archive, GALEX  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00803.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters and combination method for TP data
- Missing: Region definitions and exact AGN mask
- Missing: Spitzer/GALEX maps processing details
- Data volume (inferred): ~50-200 GB raw for ALMA 12m+7m+TP mosaic; plus small Spitzer/GALEX images
- Score (inferred): 5/5, Public data and clear formulae, but imaging parameters, array combination and region masks are not given.
- Rediscovery candidate: no, Imaging and combination recipe incomplete, and results depend on Spitzer data processing and Paper II inputs.

## Links

- Method: (cite: 2013seg..book..419C) (SFR calibrations)
- Method: (cite: 2007ApJ...666..870C) (Local 24 um SFR recipe)
- Companion: Miura et al. 2019 (Paper II) (cite: PaperII) (GMC census and XCO from virial method with the same CO cube)
- Related: ATLAS3D
- Related: SAURON

## Checks

```json
{
 "quotes": 70,
 "quotes_ok": 70,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 54,
  "rate": 0.667
 },
 "evidence_ok": true
}
```

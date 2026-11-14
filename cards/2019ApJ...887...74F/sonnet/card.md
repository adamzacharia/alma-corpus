# ALMA Reveals a Gas-rich, Maximum Starburst in the Hyperluminous, Dust-obscured Quasar W0533-3401 at z ∼ 2.9

`2019ApJ...887...74F` | The Astrophysical Journal 2019 | first author: Fan, Lulu | arXiv: 1910.10155 | DOI: 10.3847/1538-4357/ab5059

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: What are the molecular gas, dust, stellar and SMBH properties of the hyperluminous obscured quasar W0533-3401, and is it a gas-rich maximum starburst in a transition phase toward an unobscured quasar?  
  > "we can further derive the properties of each component in host galaxy and explore the potential relation between the assembly of host galaxy and the central SMBH accretion." (Introduction)
- Target **W0533-3401**: coordinates RA 05:33:58.44, Dec -34:01:34.5 (J2000, WISE)  
  > "| R.A.$_{\it WISE}$ (J2000) | 05:33:58.44 |" (Table 1); "| $z_{\rm opt}$ | 2.904 |" (Table 1); z/distance z_opt = 2.904; z_CO(3-2) = 2.9026 ± 0.0003  
  > "| R.A.$_{\it WISE}$ (J2000) | 05:33:58.44 |" (Table 1); "| $z_{\rm opt}$ | 2.904 |" (Table 1); distance from optical redshift from Tsai2015; CO redshift measured here  
  > "| R.A.$_{\it WISE}$ (J2000) | 05:33:58.44 |" (Table 1); "| $z_{\rm opt}$ | 2.904 |" (Table 1)

## Data provenance

- ALMA projects: 2017.1.00441.S
- bands: Band 3  
  > "using the band-3 receiver" (2 ALMA observations and data analysis)
- frequencies and spectral setup: LSB two SPWs at 87.418 and 89.219 GHz (960 channels each); USB two continuum SPWs at 99.421 and 101.221 GHz (128 channels each)  
  > "the lower sideband has two spectral windows tuned to 87.418 and 89.219 GHz with spectral line mode using 960 spectral channels each" (2 ALMA observations and data analysis)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 m to 2460 m, 45 antennas  
  > "using 45 antennas in a configuration with baseline length ranging from 15m to 2460m" (2 ALMA observations and data analysis)
- angular resolution: 0.61'' x 0.53'' (natural weighting), PA -78.4 deg  
  > "the angular resolution of the observations (clean beam size) is $0.61''\times0.53''$, at a position angle (P.A.) = $-78.4$ degrees" (2 ALMA observations and data analysis)
- max recoverable scale: _not stated_
- sensitivity: rms 0.43 mJy/beam in 53 km/s channels  
  > "the rms is 0.43 mJy/beam in 53 km s$^{-1}$ channels" (2 ALMA observations and data analysis)
- time on source: 517 s  
  > "The on-source integration time was 517s." (2 ALMA observations and data analysis)
- observing dates: 2017-Dec-20  
  > "The observations were carried out on 2017-Dec-20" (2 ALMA observations and data analysis)
- pi or archival as stated: _not stated_
- Line: CO J=3-2 (not stated)
- Other facility **DES DR1**: grizY photometry  
  > "Optical/near-infrared photometry in five broad bands, $grizY$, are retrieved from the first public data release of the Dark Energy Survey" (3.1 UV-to-millimeter SED)
- Other facility **SOAR/OSIRIS**: J-band photometry (from Assef2015)  
  > "Near-infrared $J$ band photometry has been obtained by SOAR/OSIRIS (cite: Assef2015)." (3.1 UV-to-millimeter SED)
- Other facility **WISE**: W1-W4 mid-IR photometry  
  > "The *WISE *W3 and W4 photometry of W0533$-$3401 are from the ALLWISE Data Release" (3.1 UV-to-millimeter SED)
- Other facility **Herschel PACS/SPIRE**: 70-500 micron FIR photometry from Fan2016b  
  > "PACS (cite: Poglitsch2010) at 70 and 160 $\mu$m and SPIRE (cite: Griffin2010) at 250, 350 and 500 $\mu$m in our previous work (cite: Fan2016b)" (3.1 UV-to-millimeter SED)
- External data: Herschel PACS/SPIRE photometry  
  > "in our previous work (cite: Fan2016b)" (3.1 UV-to-millimeter SED) [from Fan2016b]
- External data: Clumpy torus model SED database  
  > "the AGN torus emission is modeled independently with the extensive database" (3.2 Multiwavelength SED analysis) [from Nenkova2008a; Nenkova2008b]
- External data: Optical redshift z_opt=2.904  
  > "using the optical redshift $z_{\rm opt}=2.904$ (cite: Tsai2015)" (2 ALMA observations and data analysis) [from Tsai2015]

## Processing

### Calibration

- pipeline or manual: Observatory-delivered pipeline calibration checked, no further adjustments  
  > "We found that the calibration was sufficient and made no further adjustments." (2 ALMA observations and data analysis)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Calibration used as delivered; visibilities re-imaged  
  > "The calibrated visibilities were re-imaged using task `tclean`." (2 ALMA observations and data analysis)
- flux calibrator: J0538-4405 (bandpass and flux); J0522-3627 gain  
  > "were used for bandpass and flux calibration, and for gain calibration, respectively." (2 ALMA observations and data analysis)
- flux scale uncertainty: about 5%  
  > "The uncertainty on the absolute flux calibration was estimated to be about 5%." (2 ALMA observations and data analysis)
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "The calibrated visibilities were re-imaged using task `tclean`." (2 ALMA observations and data analysis)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "For natural weighting, the angular resolution of the observations" (2 ALMA observations and data analysis)
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
- final rms: 0.43 mJy/beam in 53 km/s channels  
  > "the rms is 0.43 mJy/beam in 53 km s$^{-1}$ channels" (2 ALMA observations and data analysis)

### Inherited from earlier work

- Dust mass absorption coefficient kappa_1THz = 20 cm2/g  
  > "$\kappa_{\rm 1THz}=20$ cm$^2$ g$^{-1}$ which is the same as in (cite: Wu2014) and (cite: Fan2016b)" (4.2 Dust properties) [from Wu2014; Fan2016b]
- AGN torus modeled as in earlier work  
  > "Finally, as in (cite: Fan2016b), the AGN torus emission is modeled independently" (3.2 Multiwavelength SED analysis) [from Fan2016b]

### Not stated but needed to reproduce (our reading)

- tclean parameters: cell size, image size, deconvolver, threshold, masking, niter
- line-free channels and continuum subtraction method
- CASA version and pipeline version
- moment-map thresholds and aperture used for line flux and spectrum extraction
- 3DBarolo settings beyond rings and width (free parameters, normalization, fit mask)
- bayesed sampler and likelihood details (forthcoming version not public)
- how the 12-parameter SED fit was run and how the 3 mm flux was incorporated
- diameter D used in the dynamical mass
- FIR-to-SFR conversion details and the SFR from the SED

## Analysis recipe

1. **Re-image ALMA data and measure continuum and CO(3-2)**: Re-image calibrated visibilities with tclean; fit elliptical Gaussian to velocity-integrated visibilities; single Gaussian fit to continuum-subtracted spectrum  
  > "We fit the velocity-integrated visibilities with an elliptical Gaussian function." (4.1 CO(3-2) line emission)
   - software: CASA, tclean
   - parameter: natural weighting; 53 km/s channels  
  > "the rms is 0.43 mJy/beam in 53 km s$^{-1}$ channels" (2 ALMA observations and data analysis)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive CO luminosity and molecular gas mass**: L'CO from Solomon & Vanden Bout Eq. 3; convert to CO(1-0) with r32/10=0.8; apply alpha_CO  
  > "We also adopt the CO-to-H$_2$ conversion factor, $\alpha_{\rm CO}=0.8~M_\odot$(K km s$^{-1}$ pc$^2$)$^{-1}$" (4.1 CO(3-2) line emission)
   - assumption: r32/10 = 0.8; alpha_CO = 0.8; flat LCDM H0=70, OmegaM=0.3  
  > "we adopt the excitation ratio between the CO$(3-2)$ and CO$(1-0)$ line of $r_{32/10} = 0.8$" (4.1 CO(3-2) line emission)
   - fitting: _not stated_
   - validation: _not stated_
3. **Kinematic modelling and dynamical mass**: 3D tilted-ring model with 3 rings of 0.2'' width, PA fixed at 330 deg, inclination 59 deg; M_dyn from Wang2013 relation  
  > "We assume a disc model with three rings and a ring width of 0.2$''$." (4.1 CO(3-2) line emission)
   - software: 3DBarolo
   - parameter: inclination 59 ± 14 deg from axis ratio  
  > "adopt an inclination of 59$^{\circ}\pm 14^{\circ}$, which is inferred from the observed ratio of minor to major axis" (4.1 CO(3-2) line emission)
   - assumption: gas in rotating disk  
  > "Assuming that the gas is distributed in a rotating disk" (4.1 CO(3-2) line emission)
   - fitting: _not stated_
   - validation: _not stated_
4. **UV-to-mm SED fitting**: Bayesian three-component fit (BC03 stars with Chabrier IMF, exponentially declining SFH, Calzetti attenuation; graybody dust; clumpy torus AGN), 12 free parameters, energy balance  
  > "In total, the three-component model, including stars, AGN and cold dust emissions, has 12 free parameters." (3.2 Multiwavelength SED analysis)
   - software: bayesed
   - parameter: Uniform priors (Table 3); lambda0 = 125 micron  
  > "$\lambda_0$ = 125$\,\mu$m" (3.2 Multiwavelength SED analysis)
   - fitting: Bayesian; uniform priors; sampler not stated  
  > "| $T_{\rm dust}/{\rm K}$         | Uniform                       | 10       | 100      | $78.1^{+5.9}_{-5.2}$   |" (Table 3)
   - validation: Test adding 1 Gyr SSP: old population contributes <=20% of stellar mass  
  > "the contribution of the old SSP to the derived stellar mass is not larger than 20%" (4.3 Stellar mass and star formation rate)
5. **Dust mass, gas-to-dust ratio, SFR, depletion time, BH properties**: Optically thin M_dust equation; f_gas, SFR from SED and from CO(5-4)-FIR relation; t_depl = M_gas/SFR; M_BH from L_AGN with Eddington ratio 1; Mdot_BH from L_AGN with eta/(1-eta)=0.1  
  > "adopting $\frac{\eta}{1-\eta}=0.1$" (4.4 Rapid growth of both the stellar component and the central SMBH)
   - assumption: kappa_1THz=20 cm2/g; lambda_Edd=1; L'CO(5-4)/L'CO(3-2)=0.7  
  > "by taking $L'_{\rm CO(5-4)}/L'_{\rm CO(3-2)}=0.7$" (4.3 Stellar mass and star formation rate)
   - fitting: _not stated_
   - validation: CO-based SFR consistent with SED SFR  
  > "which is generally consistent with the best-fit SED result" (4.3 Stellar mass and star formation rate)

## Software

- **CASA** : Data processing and imaging  
  > "The data were processed using CASA" (2 ALMA observations and data analysis)
- **tclean** : Re-imaging calibrated visibilities  
  > "The calibrated visibilities were re-imaged using task `tclean`." (2 ALMA observations and data analysis)
- **3DBarolo** : 3D tilted-ring fitting of CO(3-2) cube  
  > "a tool for fitting 3D tilted-ring models to emission-line data cubes" (4.1 CO(3-2) line emission)
- **bayesed** forthcoming version (Han et al., in prep): Multiwavelength Bayesian SED fitting  
  > "we use a forthcoming version (Han et al., in prep) of the Bayesian SED modeling and interpreting code bayesed" (3.2 Multiwavelength SED analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(3-2) line flux | 2.01 | 0.13 | Jy km/s | 1 | / $I_{\rm CO(3-2)}$ (Jy km s$^{-1}$) / 2.01 $\pm$ 0.13 / |
| CO(3-2) redshift | 2.9026 | 0.0003 | dimensionless | 1 | / $z_{\rm CO(3-2)}$ / $2.9026\pm0.0003$ / |
| CO(3-2) FWHM | 566 | 44 | km/s | 1 | / FWHM (km s$^{-1}$) $^{a}$ / 566 $\pm$ 44 / |
| 3 mm continuum flux density | 0.140 | 0.033 | mJy | 1 | / $S_{\rm 3mm}$ \[mJy\] / 0.140$\pm$0.033 / |
| L'CO(3-2) | 8.4e10 | 0.5e10 | K km/s pc^2 | 2 | $L'_{\rm CO(3-2)}=(8.4\pm0.5)\times10^{10}$ K km s$^{-1}$ pc$^2$ |
| Molecular gas mass | 8.4e10 | 0.5e10 | Msun | 2 | we obtain a molecular gas mass of $M_{\rm H_2}=(8.4\pm0.5)\times10^{10}\,M_\odot$ |
| Dynamical mass | 1.6e11 | not stated | Msun | 3 | This gives $M_{\rm dyn}=1.6\times10^{11}M_\odot$. |
| Dust mass | 8.9e7 | 1.6e7 | Msun | 5 | / $M_{\rm dust}$ / (8.9 $\pm$ 1.6) $\times 10^{7}$ / $M_\odot$ / \(11\) / |
| Gas-to-dust ratio | 944 | 77 | dimensionless | 5 | $\delta_{\rm GDR} = 944\pm77$ |
| Stellar mass | 3.5e10 | 0.9e10 | Msun | 4 | / $M_\star$ / (3.5 $\pm$ 0.9) $\times10^{10}$ / $M_\odot$ / \(1\) / |
| SFR (SED) | 6985 | 3006 | Msun/yr | 4 | / SFR / 6985 $\pm$ 3006 / $M_\odot$ yr$^{-1}$ / \(2\) / |
| Gas fraction | 0.71 | not stated | dimensionless | 5 | $f_{\rm gas}=M_{\rm H_2}/(M_{\rm H_2}+M_\star)=0.71$ |
| Dust temperature | 78.1 | 5.6 | K | 4 | / T$_{\rm dust}$ / 78.1 $\pm$ 5.6 / K / \(12\) / |
| Gas depletion time | 12-28 | not stated | Myr | 5 | We infer $t_{\rm depl}\sim 12-28$ Myr |
| BH mass growth rate | 49 | not stated | Msun/yr | 5 | We infer ${\dot{M}}_{\rm BH}$ = 49 $M_\odot$ yr$^{-1}$ |
| M_BH/M_star (lambda_Edd=1) | 0.063 | not stated | dimensionless | 5 | ($M_{\rm BH}/M_\star=0.063$) |

## Qualitative findings

- CO(3-2) is marginally resolved with a velocity gradient that could be a rotating disk, merger or outflow  
  > "The CO$(3-2)$ emission line is marginally resolved and has a velocity gradient, which is possibly due to a rotating gas disk, gas outflow or merger." (abstract)

## Claim tuples

- H: Is W0533-3401 gas-rich? | E: CO(3-2) luminosity converted to gas mass; SED stellar mass | R: M_gas=8.4e10 Msun, f_gas=0.71 | F: The quasar host is gas-rich | **supported**
- H: Is it a maximum starburst with short depletion time? | E: SED and CO-based SFR | R: SFR ~3000-7000 Msun/yr, sSFR 200/Gyr, t_depl 12-28 Myr | F: Maximum starburst | **supported**
- H: Is the SMBH growing rapidly and ahead of the host? | E: L_AGN-based Mdot_BH and M_BH/M_star | R: Mdot_BH=49 Msun/yr; M_BH/M_star over an order of magnitude above local | F: Rapid SMBH growth, transition toward unobscured quasar | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Gas excitation ratio chosen intermediate between SMGs and quasars, consistent with transition phase  
  > "consistent with the expectation that obscured quasars represent the transition phase from SMGs to unobscured quasars" (4.1 CO(3-2) line emission)
- How they decided it was enough: _not stated_
- Limitation (authors): Limited depth and resolution prevent distinguishing disk, merger and outflow  
  > "due to limited depth and resolution, we cannot make a solid conclusion" (4.1 CO(3-2) line emission)
- Limitation (authors): Dust mass depends strongly on the adopted kappa  
  > "the largest uncertainty can arise from the adopted $\kappa_{\nu_{\rm rest}}$ value" (4.2 Dust properties)
- Caveat (inferred, ours): 3 mm continuum is only a ~4.2 sigma marginal detection but feeds the SED
- Caveat (inferred, ours): Short 517 s observation gives limited S/N, so kinematic modelling with 3 rings is weakly constrained
- Caveat (inferred, ours): Black hole mass is assumed from Eddington ratio, not measured
- Caveat (inferred, ours): Inconsistency: summary gives M_dyn=1.6e10 vs 1.6e11 in the text
- Caveat (inferred, ours): alpha_CO and r32/10 choices dominate the gas mass uncertainty

## Reproducibility

- Data public (paper): ALMA data acknowledged by project code; DES public  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00441.S." (Acknowledgments)
- Products in archive: _not stated_
- Code: bayesed URL footnoted, but the version used is forthcoming  
  > "we use a forthcoming version (Han et al., in prep) of the Bayesian SED modeling and interpreting code bayesed" (3.2 Multiwavelength SED analysis)
- Missing: Imaging parameters for tclean
- Missing: Exact SED fitting code version and sampler
- Missing: Aperture and masks for line flux
- Missing: 3DBarolo configuration details
- Data volume (inferred): ~5-20 GB raw for a single short Band 3 execution
- Score (inferred): 3/5, Simple dataset and clear derivations, but missing imaging and fitting details and the SED code is unreleased.
- Rediscovery candidate: no, Key SED results depend on an unreleased code version and several imaging settings are unstated, though the CO measurements are numeric.

## Links

- Method: Di Teodoro & Fraternali 2015 (cite: DiTeodoro2015) (3DBarolo kinematic fitting)
- Method: Solomon & Vanden Bout 2005 (cite: solomon2005) (CO luminosity equation)
- Companion: Fan et al. 2016 (cite: Fan2016b) (Previous IR SED decomposition and Herschel photometry of W0533-3401)
- Companion: Tsai et al. 2015 (cite: Tsai2015) (Optical redshift and luminosity of the source)
- Related: WISE W1W2-dropout (hot DOG) selection
- Related: Dark Energy Survey DR1

## Checks

```json
{
 "quotes": 76,
 "quotes_ok": 76,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 16,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 51,
  "rate": 0.63
 },
 "evidence_ok": true
}
```

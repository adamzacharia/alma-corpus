# ALMA resolves molecular clouds in metal-poor Magellanic Bridge A

`2020A&A...641A..97V` | Astronomy and Astrophysics 2020 | first author: Valdivia-Mena, M. T. | arXiv: 2007.01319 | DOI: 10.1051/0004-6361/201937232

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation, milky_way_ism
- Question: What are the gas and dust properties of Magellanic Bridge A at sub-parsec resolution, and is the 870 um submillimeter excess also present at 1.3 mm?  
  > "Our goal is to characterize gas and dust emission in Magellanic Bridge A, the" (abstract)
- Target **Magellanic Bridge A**: coordinates RA 1:43:52.68, Dec -74:32:20.23 (FK5, J2000)  
  > "We measure the total emission coming from Magellanic Bridge A in an aperture with a radius $r=50\ensuremath{''}$, centered at $\alpha=$ 1:43:52.68, $\delta=$ -74:32:20.23 (FK5, J2000)." (3.1.1 Flux measurements); "we use the estimated distance to the SMC, 60 kpc, (cite: harries2003)" (3.4 Gas masses); z/distance 60 kpc  
  > "We measure the total emission coming from Magellanic Bridge A in an aperture with a radius $r=50\ensuremath{''}$, centered at $\alpha=$ 1:43:52.68, $\delta=$ -74:32:20.23 (FK5, J2000)." (3.1.1 Flux measurements); "we use the estimated distance to the SMC, 60 kpc, (cite: harries2003)" (3.4 Gas masses); distance from distance to the SMC (Harries et al. 2003)  
  > "We measure the total emission coming from Magellanic Bridge A in an aperture with a radius $r=50\ensuremath{''}$, centered at $\alpha=$ 1:43:52.68, $\delta=$ -74:32:20.23 (FK5, J2000)." (3.1.1 Flux measurements); "we use the estimated distance to the SMC, 60 kpc, (cite: harries2003)" (3.4 Gas masses)

## Data provenance

- ALMA projects: 2012.1.00683.S
- bands: Band 6 (1.3 mm, 230 GHz)  
  > "We use Band 6 observations taken with the 12m array and the 7m array (also known as Morita Array)" (2.1 ALMA observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12m array (Cycle 2) and 7m array (Cycle 1)  
  > "we used 7m array data taken during Cycle 1 and 12m array observations taken in Cycle 2." (2.1 ALMA observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: CO cube 1.22''x1.15''; continuum natural 1.54''x1.37''  
  > "an angular resolution of 1.22$''$$\times$1.15$''$ (PA$=$42$^\circ$)" (2.1.2 CO(2-1) line)
- max recoverable scale: 18.3'' (12m); 30.9'' combined  
  > "The MRS increases to 30.9$''$ after the 7m array data are combined with the 12m array observations." (2.1 ALMA observations)
- sensitivity: continuum rms 0.17 mJy/beam (natural); CO 22-36 mJy/beam per channel  
  > "variable rms through out the line cube with values ranging from 22 and 36 mJy/beam per channel." (2.1.2 CO(2-1) line)
- time on source: 12m: 107 min execution; 7m: 93.7 min  
  > "a total excecution time of 107 minutes." (2.1 ALMA observations); "a total integration time of 93.7 minutes." (2.1 ALMA observations)
- observing dates: _not stated_
- pi or archival as stated: PI M. Rubio, project 2012.1.00683.S  
  > "The datasets belong to project 2012.1.00683.S (PI M. Rubio)." (2.1 ALMA observations)
- Line: CO J=2-1 (not stated)
- Other facility **APEX LABOCA**: 870 um continuum  
  > "We use 870 $\mu m$ continuum observations of Magellanic Bridge A obtained with the Large APEX Bolometer Camera (LABOCA) on the APEX telescope." (2.2.1 0.87 mm continuum)
- Other facility **APEX SHeFI APEX-1**: CO(2-1) single-dish cube for combination  
  > "performed using the On-The-Fly mapping technique with the APEX$-$1 receiver of the Swedish Heterodyne Facility Instrument (SHeFI)" (2.2.2 CO(2-1) line)
- Other facility **Herschel HERITAGE**: 100-500 um maps  
  > "We use Herschel observations from the HERITAGE Herschel key project (cite: meixner2013), consisting of maps of the SMC at 100, 160, 250, 350 and 500 $\mu$m." (2.4 Complementary data)
- Other facility **Spitzer MIPS (SAGE-SMC)**: 160 um image  
  > "We also use the 160 $\mu m$ Spitzer image, obtained from the Multiband Imaging Photometer for Spitzer (MIPS)" (2.4 Complementary data)
- Other facility **SHASSA**: Halpha image for free-free correction  
  > "We use an H$\alpha$ image of the SMC from the Southern H$\alpha$ Sky Survey Atlas (SHASSA)" (2.4 Complementary data)
- External data: CO(3-2) peak intensity 0.93+-0.07 K km/s for LABOCA line correction  
  > "We use $I_{^{12}CO(3-2)}=0.93\pm 0.07$ K km s$^{-1}$" (3.1.2 Free-free and CO(3-2)) [from (cite: muller2014)]
- External data: Dust emissivity per H atom eps_d(345GHz)=3.94e-27 cm2  
  > "$\epsilon_d(345GHz)=(3.94\pm0.05)\times10^{-27}$ cm$^2$" (3.4 Gas masses) [from (cite: bot2010)]
- External data: NANTEN CO(1-0) luminosity 70+-8 K km/s pc2  
  > "$L_{CO(1-0)}=70 \pm 8$ K km s$^{-1}$ pc$^{2}$ (cite: mizuno2006)" (4.1 CO(2-1) comparison) [from (cite: mizuno2006)]
- External data: LABOCA 870 um image reduced earlier  
  > "We use the 870 $\mu m$ continuum image of Magellanic Bridge A presented in (cite: verdugo2012)." (2.2.1 0.87 mm continuum) [from (cite: verdugo2012)]

## Processing

### Calibration

- pipeline or manual: Reprocessed from raw data with ALMA archive standard scripts  
  > "We use the standard scripts provided by the ALMA Science Archive[^1] with the delivered raw data to recover the calibrated datasets." (2.1 ALMA observations)
- casa version: CASA 4.7  
  > "Common Astronomy Software Applications (CASA) package version 4.7" (2.1 ALMA observations)
- pipeline version: _not stated_
- archive products used as is: No; reprocessed from raw data  
  > "we decided to start from the raw data and reprocess completely both datasets, instead of using the delivered data products by ALMA." (2.1 ALMA observations)
- flux calibrator: Uranus (both arrays)  
  > "Uranus was used as flux calibrator, J0057$-$7040 as phase calibrator and J2357$-$5311 as bandpass calibrator." (2.1 ALMA observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean (continuum and line); concat, statwt for combination; feather for ALMA+APEX  
  > "We use the standard `clean` task on the 12m and 7m combined data to generate the 1.3 mm (230 GHz) continuum image" (2.1.1 1.3 mm continuum)
- deconvolver: _not stated_
- weighting robust: Natural used for continuum; Briggs robust 0.5 for CO cube  
  > "We use briggs weighting with a robust parameter of 0.5." (2.1.2 CO(2-1) line)
- uv taper: 5'' taper, then convolved to 22''  
  > "We apply a tapering of 5$''$, which results in an image with a resolution of $5.9\ensuremath{''} \times 4.7\ensuremath{''}$." (2.1.1 1.3 mm continuum)
- cell size: _not stated_
- image size: _not stated_
- masking: CO clean mask based on APEX CO(2-1) data  
  > "using a mask based on the APEX CO(2$-$1) data" (2.1.2 CO(2-1) line)
- multiscale scales: _not stated_
- continuum subtraction: CO line channels excluded from continuum  
  > "removing the spectral channels that contain the CO(2$-$1) line." (2.1.1 1.3 mm continuum)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: concat with freqtol 10 MHz, statwt weights; feather with APEX  
  > "the 12m array and 7m array data were combined using the `concat` task with a frequency tolerance of 10 MHz" (2 Observations and data reduction)
- smoothing: continuum convolved to 22'' to match LABOCA  
  > "we convolved the natural, uv-tapered image to reach a beam FWHM equal to 22$''$." (2.1.1 1.3 mm continuum)
- final beam: CO 1.22''x1.15'' (PA 42 deg), 0.5 km/s  
  > "a spatial resolution of $1.22\ensuremath{''}\times1.15\ensuremath{''}$ ($\approx0.3$ pc) and spectral resolution of 0.5 km s$^{-1}$" (2.3 Combined ALMA & APEX)
- final rms: continuum 0.17 mJy/beam natural; combined CO 30-36 mJy/beam per channel  
  > "with values between 30 and 36 mJy beam$^{-1}$ per channel depending on position." (2.3 Combined ALMA & APEX)

### Inherited from earlier work

- Gas mass from dust flux method  
  > "We use the same method to obtain the gas mass from dust flux used in (cite: bot2010) and (cite: rubio2004)." (3.4 Gas masses) [from (cite: bot2010); (cite: rubio2004)]
- 870 um LABOCA image reduction  
  > "We use the 870 $\mu m$ continuum image of Magellanic Bridge A presented in (cite: verdugo2012)." (2.2.1 0.87 mm continuum) [from (cite: verdugo2012)]
- Cloud size and linewidth measurement with deconvolution  
  > "We calculate the radius using the second moments of emission, as suggested in Section 2.1 of (cite: rosolowsky2006)" (4.2 Physical properties) [from (cite: rosolowsky2006)]

### Not stated but needed to reproduce (our reading)

- CO(2-1) cube clean threshold, niter, cell and image size
- line-free channels used for the continuum
- feather scaling/ single-dish calibration details and Jy/K conversion
- how the CO mask from APEX was built
- aperture photometry code and SED fit starting values
- APEX CO map size is printed in arcsec (likely arcmin), unclear
- statwt parameters

## Analysis recipe

1. **Reprocess and combine ALMA 12m and 7m data**: Archive scripts to calibrate, statwt weights, concat  
  > "We calculate the visibility weights of the 12m and 7m observations with the `statwt` task." (2 Observations and data reduction)
   - software: CASA
   - parameter: freqtol 10 MHz  
  > "using the `concat` task with a frequency tolerance of 10 MHz" (2 Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Image 1.3 mm continuum and CO(2-1) cube; feather with APEX**: clean with natural weighting/taper for continuum, briggs 0.5 for CO; feather with APEX CO  
  > "we use the `feather` task from the CASA software, which performs the combination in Fourier space." (2.3 Combined ALMA & APEX)
   - software: CASA, GILDAS/CLASS
   - parameter: APEX main beam efficiency 0.72  
  > "with a main beam efficiency $\eta_{mb} = 0.72$ for APEX$-$1" (2.2.2 CO(2-1) line)
   - fitting: _not stated_
   - validation: ALMA CO luminosity compared to APEX total  
  > "ALMA recovers, within the uncertainties, almost all the luminosity measured in the APEX CO(2-1) line cube" (4.2 Physical properties)
3. **Aperture photometry for SED and 1.3 mm upper limit**: Convolve to common resolution (43'' or 22''), aperture r=50'' or 11'' with sky annulus; upper limit = 3x photometric error  
  > "To do this, we use a value 3 times the photometric error $\epsilon$." (3.1.1 Flux measurements)
   - parameter: aperture correction factor 2 for North/South  
  > "we apply an aperture correction factor of 2 in the flux measurements." (3.1.1 Flux measurements)
   - fitting: _not stated_
   - validation: _not stated_
4. **Subtract free-free and CO(3-2) contamination**: Halpha-based free-free formula (Hunt 2004); CO(3-2) via Drabek 2012  
  > "We use $T_\mathrm{e}\sim1.7\times10^4$ K, the upper limit for the gas temperature reported in (cite: lehner2001)" (3.1.2 Free-free and CO(3-2))
   - assumption: n(He+)/n(H+)~0.08; Te~1.7e4 K; A_V=0.140  
  > "$n(He^+)/n(H^+)\sim 0.08$, which is the value estimated for low metallicity sources" (3.1.2 Free-free and CO(3-2))
   - fitting: _not stated_
   - validation: _not stated_
5. **Fit modified blackbody SED and compute excess and gas mass**: Single-component optically thin MBB, chi2 minimisation; excess = measured/predicted flux; gas mass from predicted 870 um flux  
  > "We use $\chi^2$ minimization to determine $C$, $\beta$ and $T_d$ that best fit the SED, using the scipy.optimize package (cite: scipy2020) function curve_fit." (3.2 SED modeling)
   - software: scipy.optimize curve_fit
   - parameter: beta fixed to 1.4 for North and South  
  > "we assume that the dust emissivity is the same as the one found for Magellanic Bridge A, and therefore fix $\beta=1.4$ for both sources." (3.2 SED modeling)
   - assumption: distance 60 kpc; dust-to-gas 1/6 solar; kappa_345GHz=1.26; mu=1.36  
  > "a dust-to-gas ratio 1/6 of the ratio in the solar neighborhood" (3.4 Gas masses)
   - fitting: chi2 least squares with curve_fit  
  > "We assume a single dust component and single $\beta$ dust emissivity index." (3.2 SED modeling)
   - validation: Alternative kappa_160 from Gordon 2014 gives masses within uncertainties  
  > "These values are within the uncertainties of those obtained using the (cite: bot2010) value." (3.4 Gas masses)
6. **Identify CO clouds, fit spectra, derive sizes, luminosities, virial masses, alpha_CO**: 3 sigma sources in integrated intensity (172-176 km/s), second moments, Gaussian least-squares to spectra, Rosolowsky & Leroy deconvolution, Mvir=190 R dv^2, alpha_CO=Mvir/L  
  > "We estimate the CO-to-H$_2$ conversion factor $\alpha_{CO}=M_{\mathrm{vir}}/L_{CO}$" (4.2 Physical properties)
   - parameter: L_CO=611.5 S dv D^2; R=1.91 sigma_r D  
  > "$L_{CO(2-1)} = 611.5 S_{CO(2-1)}\Delta v D^2$" (4.2 Physical properties)
   - assumption: spherical bound clouds with rho~r^-1; r21~1; D~60 kpc  
  > "This equation assumes spherical, gravitationally bound molecular clouds and a density profile $\rho \propto r^{-1}$." (4.2 Physical properties)
   - fitting: Gaussian least-squares  
  > "We adjust the gaussian model to the spectra through least squares fitting." (4.1 CO(2-1) molecular clouds spectra)
   - validation: _not stated_

## Software

- **CASA** 4.7: calibration, concat, statwt, clean, feather  
  > "We reduce, combine and image the data using the Common Astronomy Software Applications (CASA) package version 4.7" (2.1 ALMA observations)
- **GILDAS/CLASS** : APEX CO reduction  
  > "We reduce the APEX CO(2$-$1) line cube through the standard procedure of the CLASS software, Gildas" (2.2.2 CO(2-1) line)
- **BoA** : LABOCA reduction  
  > "The reduction of this continuum image was done with the Bolometric Array Analysis Software (BoA)" (2.2.1 0.87 mm continuum)
- **scipy.optimize curve_fit** : MBB chi2 fitting  
  > "using the scipy.optimize package (cite: scipy2020) function curve_fit" (3.2 SED modeling)
- **Astropy** : general analysis  
  > "This research made use of Astropy,[^9] a community-developed core Python package for Astronomy" (Acknowledgements)
- **APLpy** : plotting  
  > "This research made use of APLpy, an open-source plotting package for Python" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dust temperature, Bridge A | 22.4 | 3.4 | K | 5 | gives a dust temperature $T_d=22.4\pm3.4$ K and an emissivity index $\beta=1.4\pm0.5$ |
| Emissivity index beta, Bridge A | 1.4 | 0.5 | dimensionless | 5 | an emissivity index $\beta=1.4\pm0.5$ |
| E(870um) Bridge A | 6.9 | 1.6 | dimensionless | 5 | $E(870\,\mu m)=6.9\pm1.6$ |
| E(870um) North | 6.7 | 1.6 | dimensionless | 5 | For the North source, $E(870\,\mu m)=6.7\pm1.6$ |
| 1.3 mm flux upper limit, Bridge A | 16.5 | not stated | mJy | 3 | which gives a 1.3 mm flux upper limit for Magellanic Bridge A of 16.5 mJy |
| Gas mass from dust, North | 1.3e3 | 0.5e3 | Msun | 5 | $(1.3\pm0.5)\times 10^{3}$ M$_{\ensuremath{\odot}}$ |
| Virial mass North | 437.3 | 26.1 | Msun | 6 | The virial mass for CO source North is $437.3\pm26.1$ M$_{\ensuremath{\odot}}$ and for source South is $732.9\pm37.0$ M$_{\ensuremath{\odot}}$. |
| Virial mass South | 732.9 | 37.0 | Msun | 6 | for source South is $732.9\pm37.0$ M$_{\ensuremath{\odot}}$ |
| alpha_CO North | 6.5 | 0.7 | Msun (K km/s pc2)^-1 | 6 | $\alpha_{CO}=6.5\pm0.7$ M$_{\ensuremath{\odot}}$ (K kms$^{-1}$ pc$^2$)$^{-1}$ |
| alpha_CO South | 15.3 | 1.6 | Msun (K km/s pc2)^-1 | 6 | $\alpha_{CO}=15.3\pm1.6$ M$_{\ensuremath{\odot}}$ (K km s$^{-1}$ pc$^2$)$^{-1}$ |
| L_CO(2-1) North | 67.5 | 6.3 | K km/s pc2 | 6 | $L_{CO(2-1)}= 67.5 \pm 6.3$ K km s$^{-1}$ pc$^2$ for CO cloud North |
| Cloud radius North | 1.29 | 0.07 | pc | 6 | $1.29\pm0.07$ pc for cloud North and $1.04\pm0.04$ pc for cloud South |

## Qualitative findings

- No 1.3 mm continuum detected; upper limits compatible with MBB extrapolation  
  > "Our limits are compatible with the extrapolation of the MBB fits and therefore we cannot independently confirm the excess at this longer wavelength." (abstract)

## Claim tuples

- H: The 870 um excess in Bridge A extends to 1.3 mm | E: ALMA 12m+7m 1.3 mm continuum compared to MBB fit of FIR SED | R: No detection; upper limits <1.5, <3.7, <1.4 times predicted | F: Excess cannot be confirmed at 1.3 mm; either extended and resolved out or process peaking at 870 um | **partially**
- H: CO(2-1) emission resolves into compact dense clouds | E: ALMA+APEX CO(2-1) cube analysis | R: Two ~1 pc clouds with virial masses ~437 and 733 Msun | F: Densities higher than typical Milky Way bulk densities | **supported**
- H: Dust-derived gas mass exceeds CO-traced mass | E: Compare MBB gas masses to virial masses | R: Factor ~3-4 larger | F: Extended cold envelope not emitting in CO | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Natural weighting chosen for higher sensitivity  
  > "We decide to use natural weight for this work, as sensitivity tends to be higher for natural weighted images than briggs weighted ones." (2.1.1 1.3 mm continuum)
- Alternative: Gas mass with kappa_160 from Gordon 2014 instead of Bot 2010; consistent within uncertainties  
  > "We also estimated the gas masses using an absorption coefficient determined for dust emission at 160 $\mu$m by (cite: gordon2014)" (3.4 Gas masses)
- How they decided it was enough: _not stated_
- Limitation (authors): Virial equilibrium assumption may not be strictly correct  
  > "The assumption of virial, or self-gravitating equilibrium in the Magellanic Bridge A clouds may not be strictly correct" (4 Discussion)
- Caveat (inferred, ours): Single-component MBB with beta fixed for sub-sources and only 3 Herschel bands gives large temperature uncertainties
- Caveat (inferred, ours): Upper limit depends on aperture and resolved-out flux
- Caveat (inferred, ours): Several numerical inconsistencies in the text (typos in Td, E values, alpha_CO uncertainty)
- Caveat (inferred, ours): r21 and virial-based alpha_CO assumptions

## Reproducibility

- Data public (paper): ALMA project 2012.1.00683.S; Herschel/Spitzer from IRSA  
  > "All these images were taken from the NASA/IPAC Infrarred Science Archive[^7]." (2.4 Complementary data)
- Products in archive: _not stated_
- Missing: clean parameters (niter, threshold, cell, imsize)
- Missing: APEX CO and LABOCA raw data access/reduction details
- Missing: feather scaling details
- Data volume (inferred): ~50-100 GB raw ALMA (12m mosaic of 93 pointings plus 7m)
- Score (inferred): 3/5, Public ALMA data and clear analysis formulae, but imaging parameters and APEX data processing are partly unspecified.
- Rediscovery candidate: yes, ALMA data public, recipe largely given, results numeric (virial masses, alpha_CO, upper limits).

## Links

- Method: (cite: rosolowsky2006) (cloud size/linewidth deconvolution)
- Method: (cite: bot2010) (gas mass from dust)
- Companion: (cite: verdugo2012) (LABOCA 870 um excess in Bridge A)
- Companion: (cite: mizuno2006) (CO detection of Bridge A)
- Related: HERITAGE
- Related: SAGE-SMC
- Related: SHASSA

## Checks

```json
{
 "quotes": 87,
 "quotes_ok": 87,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 90,
  "stated": 65,
  "rate": 0.722
 },
 "evidence_ok": true
}
```

# A complete Herbig disk mass survey in Orion

`2025A&A...693A..49S` | Astronomy and Astrophysics 2025 | first author: Stapper, L. M. | arXiv: 2411.08959 | DOI: 10.1051/0004-6361/202450678

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: protoplanetary_disks
- Question: Is the ALMA coverage of Herbig disks biased toward massive disks? Measure the dust masses of a complete sample of Herbig disks in Orion with NOEMA (plus existing ALMA data) and compare with T Tauri disks in Orion and the all-sky ALMA Herbig sample  
  > "the question remains if the ALMA coverage of Herbig disks is biased toward well-known and" (Introduction); "In this work we present new Northern Extended Millimeter Array (NOEMA) observations of all Herbig disks in Orion." (Introduction)
- Target **35 Herbig disks in Orion (25 observed with NOEMA, 10 with existing ALMA data)**: coordinates per-disk coordinates in Table 1 (e.g. V1012 Ori 05:11:36.5 -02:22:48.5)  
  > "all parameters are taken from (cite: GuzmanDiaz2021), see this paper for their corresponding uncertainties." (Table 1 notes); "From this, we obtained a total of 35 Herbig disks located in the Orion star-forming region" (Data selection and reduction); z/distance 306-465 pc per disk (Table 1)  
  > "all parameters are taken from (cite: GuzmanDiaz2021), see this paper for their corresponding uncertainties." (Table 1 notes); "From this, we obtained a total of 35 Herbig disks located in the Orion star-forming region" (Data selection and reduction); distance from GuzmanDiaz2021 (Vioque2018 for V1012 Ori parameters)  
  > "all parameters are taken from (cite: GuzmanDiaz2021), see this paper for their corresponding uncertainties." (Table 1 notes); "From this, we obtained a total of 35 Herbig disks located in the Orion star-forming region" (Data selection and reduction)
- Target **V1012 Ori (ALMA archival product data)**: coordinates 05:11:36.5 -02:22:48.5 (Table 1)  
  > "For V1012 Ori, the parameters are taken from (cite: Vioque2018), and the continuum flux is determined from the ALMA pipeline product data." (Table 1 notes); z/distance 386 pc (Table 1)  
  > "For V1012 Ori, the parameters are taken from (cite: Vioque2018), and the continuum flux is determined from the ALMA pipeline product data." (Table 1 notes); distance from Vioque2018  
  > "For V1012 Ori, the parameters are taken from (cite: Vioque2018), and the continuum flux is determined from the ALMA pipeline product data." (Table 1 notes)

## Data provenance

- ALMA projects: 2021.1.01705.S
- bands: _not stated_
- frequencies and spectral setup: PolyFiX LSB 203.7-211.8 GHz, USB 219.2-227.3 GHz, 2 MHz channels; thirteen 62.5 kHz high-resolution windows on molecular lines  
  > "The wide-band correlator PolyFiX was tuned such that the lower side-band (LSB) and upper side-band (USB) ranged from 203.7 to 211.8 GHz and 219.2 to 227.3 GHz respectively with a channel width of 2 MHz ($\sim2.7$ km s$^{-1}$)." (Data selection and reduction); "thirteen high resolution spectral windows with a width of 62.5 kHz ($\sim86$ m s$^{-1}$) where centered on molecular emission lines" (Data selection and reduction)
- continuum bandwidth: _not stated_
- arrays: NOEMA (not ALMA) for 25 disks; C configuration  
  > "The observations were done in the C configuration." (Data selection and reduction)
- configurations: _not stated_
- baselines: setup 1: 20-309 m plus one antenna (#7) at 985-1397 m; setup 2: 20-321 m  
  > "have baselines ranging from 20 to 309 meters with one antenna (#7) at projected long baselines ranging from 985 to 1397 meters." (Data selection and reduction); "On 2022 December 7 and 2023 October 7 (setup 2), the baselines range from 20 to 321 meter." (Data selection and reduction)
- angular resolution: restoring beam ~1'' (NOEMA, 210 GHz)  
  > "and a restoring beam of $\sim1''$ is obtained." (Data selection and reduction)
- max recoverable scale: ~15'' at 210 GHz (NOEMA)  
  > "at 210 GHz the largest angular scale the data are sensitive to is $\sim15''$" (Data selection and reduction)
- sensitivity: _not stated_
- time on source: 15 to 30 minutes (NOEMA)  
  > "The on-source integration times ranged from 15 to 30 minutes." (Data selection and reduction)
- observing dates: NOEMA: 2022 December 7, 17 and 30 and 2023 October 7  
  > "The remaining 25 disks were observed with NOEMA on 2022 December 7 and 30, on 2022 December 17, and on 2023 October 7." (Data selection and reduction)
- pi or archival as stated: NOEMA project S22AU (PI: S. Grant); ALMA archival product data 2021.1.01705.S (PI: C. Ginski) for V1012 Ori  
  > "with project number S22AU (PI: S. Grant)" (Data selection and reduction); "product data (PI: C. Ginski, 2021.1.01705.S)" (Data selection and reduction)
- Line: CO isotopologues (names not legible in text) J=2-1 (not stated)
- Other facility **NOEMA**: Continuum and CO J=2-1 observations of the 25 Herbig disks without ALMA data  
  > "In this work we present the results of observations done with the Northern Extended Millimeter Array (NOEMA), with project number S22AU (PI: S. Grant)." (Data selection and reduction)
- Other facility **SPHERE/VLT (literature)**: Scattered-light survey of Orion disks (Valegard2024) used for comparison  
  > "published a survey of disks in Orion observed in scattered light imaging with SPHERE/VLT." (Comparison to scattered-light data)
- Other facility **Simbad**: Catalogue query for external ionizing stars (spectral types earlier than A0)  
  > "for stars with spectral types earlier than A0 within the region on the sky" (Impact of UV on Herbig disk masses)
- External data: Stellar and disk parameters (distance, luminosity, mass, spectral type) for the Herbig disks  
  > "all parameters are taken from (cite: GuzmanDiaz2021), see this paper for their corresponding uncertainties." (Table 1 notes) [from (cite: GuzmanDiaz2021); (cite: Vioque2018) for V1012 Ori]
- External data: Published ALMA continuum fluxes for the ten Herbig disks with existing ALMA data  
  > "For the remaining ten Herbig disks with existing ALMA data, we use the published fluxes as presented in (cite: Stapper2022) and (cite: vanTerwisga2022)" (Data selection and reduction) [from (cite: Stapper2022); (cite: vanTerwisga2022); (cite: Stapper2024)]
- External data: Dust mass distributions of NGC 2024, L1641/L1647, sigma Ori and lambda Ori  
  > "NGC 2024 (cite: vanTerwisga2020), L1641/L1647 (cite: vanTerwisga2022), $\sigma$ Ori (cite: Ansdell2017), and $\lambda$ Ori (cite: Ansdell2020)" (Dust mass distribution) [from (cite: vanTerwisga2020); (cite: vanTerwisga2022); (cite: Ansdell2017); (cite: Ansdell2020)]
- External data: All-sky ALMA Herbig disk sample with extra NOEMA sources  
  > "all-sky survey of Herbig disks with ALMA of (cite: Stapper2022) combined with the extra sources observed with NOEMA from (cite: Stapper2024)" (Comparison to the ALMA Herbig disks) [from (cite: Stapper2022); (cite: Stapper2024)]
- External data: Median age of the Herbig disks in Orion, 5.1+-4.1 Myr (range 0.5-17 Myr)  
  > "the median age of the Herbig disks in Orion, after removing upper limits, is 5.1±4.1 Myr (cite: GuzmanDiaz2021)" (Dust mass distribution) [from (cite: GuzmanDiaz2021)]
- External data: BHAC-15 isochrones and Castelli model spectra for FUV luminosities of ionizing stars  
  > "computed by using BHAC-15 isochrones (cite: Baraffe2015) and integrating model spectra (cite: Castelli2003) between 911.6 and 2066 Å." (Impact of UV on Herbig disk masses) [from (cite: Baraffe2015); (cite: Castelli2003)]
- External data: Dust masses of HD 97048 and HD 142527 (156 and 215 Earth masses)  
  > "HD 97048 and HD 142527 (156 $M_\oplus$ and 215 $M_\oplus$ respectively, (cite: Stapper2022))" (Comparison to the ALMA Herbig disks) [from (cite: Stapper2022)]
- Simulation/model as data: BHAC-15 pre-main-sequence isochrones and Castelli model spectra integrated over 911.6-2066 A to get FUV luminosities of ionizing stars  
  > "computed by using BHAC-15 isochrones (cite: Baraffe2015) and integrating model spectra (cite: Castelli2003) between 911.6 and 2066 Å." (Impact of UV on Herbig disk masses)

## Processing

### Calibration

- pipeline or manual: NOEMA standard pipeline calibration with CLIC (GILDAS)  
  > "The NOEMA data were calibrated using the standard pipeline calibration using the `CLIC` program of the Grenoble Image and Line Data Analysis Software" (Data selection and reduction)
- casa version: CASA 5.8.0 (analysis of exported uvfits)  
  > "The data were analyzed using the `Common Astronomy Software Applications` (CASA) application version 5.8.0" (Data selection and reduction)
- pipeline version: _not stated_
- archive products used as is: Yes for V1012 Ori: ALMA archive pipeline product data used for the continuum flux  
  > "the continuum flux is determined from the ALMA pipeline product data." (Table 1 notes); "for V1012 Ori we apply the same method as (cite: Stapper2022) on ALMA archive product data." (Data selection and reduction)
- flux calibrator: NOEMA: all calibrators used for flux calibration (setup 1: 2200+420, LkHalpha 101, 0923+392, 2010+723, 0458-020, J0542-0913; setup 2: LkHalpha 101, 3C84, J0509+056)  
  > "All calibrators were used for the flux calibration." (Data selection and reduction); "The calibrators for setup 2 were LkH$\alpha$ 101 and 3C84, which were used for the bandpass calibration, and J0509+056 was used for the phase and amplitude calibration." (Data selection and reduction)
- flux scale uncertainty: 20% for NOEMA, 10% for ALMA (absolute calibration error)  
  > "In addition to the fluxes there is an absolute calibration error, which is 10% for ALMA, and 20% for NOEMA." (Table 1 notes)
- self calibration: _not stated_

### Imaging

- task: No imaging for detections: Gaussian fitted to visibilities with uvmodelfit after fixvis phase-center shift  
  > "This Gaussian is fitted using the `uvmodelfit` task in CASA after changing the phase-center to be on the target using the `fixvis` task." (Data selection and reduction); "As all detections are unresolved, fitting a Gaussian to the visibilities is therefore a good approximation of the observations." (Data selection and reduction)
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
- array combination: LSB and USB combined into one continuum measurement set  
  > "the LSB and USB were both combined to make a continuum measurement set." (Data selection and reduction)
- smoothing: CO spectra binned by a factor of ten, ~0.9 km/s resolution  
  > "The spectra have been binned by a factor of ten, resulting in a $\sim0.9$ km s$^{-1}$ resolution." (Gas observations)
- final beam: ~1'' restoring beam (NOEMA)  
  > "and a restoring beam of $\sim1''$ is obtained." (Data selection and reduction)
- final rms: _not stated_

### Inherited from earlier work

- Dust mass assumptions (optically thin, opacity law, temperature scaling) same as earlier works  
  > "To obtain the dust masses, we use the same assumptions as other works (cite: Ansdell2016; Cazzoletti2019; Stapper2022)." (Data selection and reduction) [from (cite: Ansdell2016; Cazzoletti2019; Stapper2022)]
- Dust temperature scaling with stellar luminosity  
  > "we scale the dust temperature $T_\text{dust}$ using the approach of (cite: Andrews2013) via" (Data selection and reduction) [from (cite: Andrews2013)]
- Dust opacity normalisation (10 cm2/g at 1000 GHz)  
  > "such that it equals 10 cm$^2$ g$^{-1}$ at a frequency of 1000 GHz (cite: Beckwith1990)" (Data selection and reduction) [from (cite: Beckwith1990)]
- Flux measurement for V1012 Ori follows the Stapper2022 method  
  > "for V1012 Ori we apply the same method as (cite: Stapper2022) on ALMA archive product data." (Data selection and reduction) [from (cite: Stapper2022)]
- Cumulative dust mass distribution (survival analysis with lifelines)  
  > "Using the `lifelines` package (cite: DavidsonPilon2021) we obtain the cumulative distribution of the Herbig disks in Orion following (cite: Stapper2022)." (Dust mass distribution) [from (cite: Stapper2022)]
- Lognormal fit to cumulative distributions  
  > "A lognormal distribution is fitted through the cumulative distributions, following previous works (cite: Williams2019; Stapper2022; Stapper2024)" (Comparison to the ALMA Herbig disks) [from (cite: Williams2019; Stapper2022; Stapper2024)]
- Selection of external ionizing stars via Simbad query  
  > "The ionizing stars were found, following (cite: vanTerwisga2023), by querying" (Impact of UV on Herbig disk masses) [from (cite: vanTerwisga2023)]
- 10 pc projected distance cutoff for ionizing stars, no interstellar extinction  
  > "As was done by (cite: vanTerwisga2023), no stars beyond a projected distance of 10 pc from a given Herbig disk were taken into account" (Impact of UV on Herbig disk masses) [from (cite: vanTerwisga2023)]
- Target selection: Orion boundaries and Herbig compilations  
  > "Using the boundaries of Orion as given in (cite: Zari2017), we selected all Herbig disks in Orion based on the compilations of (cite: Vioque2018) and (cite: GuzmanDiaz2021)." (Data selection and reduction) [from (cite: Zari2017; Vioque2018; GuzmanDiaz2021)]

### Not stated but needed to reproduce (our reading)

- uvmodelfit starting model and fit settings (component type, initial flux/position/size) for each NOEMA source
- Which channels of the LSB/USB (line-free selection) went into the continuum measurement set
- How the rms of the 'empty image' used for upper limits was imaged (cell size, weighting, image size, region)
- GILDAS/CLIC version and the flux-calibrator model values used by CLIC
- Whether the NOEMA S22AU data are public in the IRAM archive and their proprietary status
- Names of the CO isotopologues and the other targeted molecular lines and their rest frequencies (blank in the text)
- V1012 Ori ALMA flux value and the exact Stapper2022 procedure applied to the pipeline product
- linmix settings (priors, chain length, treatment of upper limits) for the dust mass vs F_uv fit
- Stellar luminosities and distances per disk are only in Table 1 from GuzmanDiaz2021; adopted ages and masses for the BHAC-15 FUV calculation are not given
- Which sources were flagged or dropped per antenna/baseline beyond the quoted flagging fractions
- Definition of F_uv versus G0 used in the fit

## Analysis recipe

1. **select the complete Herbig sample in Orion**: Take Herbig disks within Orion boundaries from published compilations; 35 disks, ten with existing ALMA data, 25 observed with NOEMA  
  > "Using the boundaries of Orion as given in (cite: Zari2017), we selected all Herbig disks in Orion based on the compilations of (cite: Vioque2018) and (cite: GuzmanDiaz2021)." (Data selection and reduction); "Of these 35 disks, ten have existing ALMA interferometric data available" (Data selection and reduction)
   - software: SciPy
   - parameter: Kolmogorov-Smirnov test of stellar mass distribution vs all-sky sample gives p = 0.16  
  > "results in a $p$-value of 0.16." (Data selection and reduction)
   - fitting: _not stated_
   - validation: KS test shows the sample's stellar mass distribution is not significantly different from the all-sky sample  
  > "The stellar mass distribution for this sample is not significantly different compared to the all-sky sample of (cite: Stapper2022)" (Data selection and reduction)
2. **calibrate the NOEMA data**: Standard pipeline calibration with CLIC (GILDAS), then export to uvfits  
  > "The NOEMA data were calibrated using the standard pipeline calibration using the `CLIC` program of the Grenoble Image and Line Data Analysis Software" (Data selection and reduction); "After the calibration was done, the data were exported to `uvfits` files to be further analyzed." (Data selection and reduction)
   - software: CLIC, GILDAS
   - parameter: Setup 1 phase rms threshold 55 deg, seeing threshold not applied  
  > "For setup 1 the phase rms threshold was set to 55$\degree$, and the seeing threshold, normally applied to long baseline observations, was not included as only one antenna was at long baselines." (Data selection and reduction)
   - parameter: Setup 2 phase rms threshold default 70 deg  
  > "For setup 2 the phase rms threshold was set to the default value of 70$\degree$." (Data selection and reduction)
   - parameter: Flagged fractions: 10% (2022 Nov 30), 2% (2022 Dec 17), 43% (bad weather setup 2), 0% (2023 Oct 7)  
  > "Due to the reduced phase rms threshold for setup 1, 10% of the data taken on 2022 November 30 were flagged, while 2% was flagged for the data taken on 2022 December 17." (Data selection and reduction); "For the observations made on 2023 October 7 nothing was flagged." (Data selection and reduction)
   - fitting: _not stated_
   - validation: _not stated_
3. **measure continuum fluxes**: Combine LSB and USB, shift phase center with fixvis, fit a Gaussian to the visibilities with uvmodelfit; upper limits are 3x rms of the empty image for a single beam; V1012 Ori measured the Stapper2022 way on ALMA product data; other ten disks use published fluxes  
  > "To obtain the integrated fluxes in continuum, the LSB and USB were both combined to make a continuum measurement set." (Data selection and reduction); "This Gaussian is fitted using the `uvmodelfit` task in CASA after changing the phase-center to be on the target using the `fixvis` task." (Data selection and reduction); "For the non-detections, assuming the emission is coming from a singe beam, three times the rms noise from the empty image was used." (Data selection and reduction)
   - software: CASA 5.8.0, uvmodelfit, fixvis
   - assumption: All detections are unresolved, so a Gaussian fit to the visibilities approximates the observations  
  > "As all detections are unresolved, fitting a Gaussian to the visibilities is therefore a good approximation of the observations." (Data selection and reduction)
   - fitting: _not stated_
   - validation: _not stated_
4. **convert fluxes to dust masses**: Optically thin M_dust = F_nu d^2 / (kappa_nu B_nu(T_dust)) with kappa a power law of index beta = 1 normalised to 10 cm2/g at 1000 GHz and T_dust = 25 K (L/Lsun)^1/4  
  > "under the assumption of optical thin emission (cite: Hildebrand1983)." (Data selection and reduction); "The power-law index $\beta$ is assumed to be equal to 1." (Data selection and reduction); "T_\text{dust} = 25 \text{ K} \times \left(\frac{L_\star}{L_\odot}\right)^{1/4}." (Data selection and reduction)
   - parameter: kappa = 10 cm2/g at 1000 GHz, power-law beta = 1  
  > "such that it equals 10 cm$^2$ g$^{-1}$ at a frequency of 1000 GHz (cite: Beckwith1990)" (Data selection and reduction)
   - parameter: Flux calibration error 20% NOEMA, 10% ALMA propagated to mass error  
  > "For the error on the dust masses we use the recommended absolute flux calibration error of 20% for NOEMA, and 10% for ALMA." (Data selection and reduction)
   - assumption: Optically thin emission, likely the largest source of uncertainty  
  > "Nevertheless, the dust masses are calculated under the assumption of optically thin emission, which is likely the largest source of uncertainty." (Data selection and reduction)
   - fitting: _not stated_
   - validation: _not stated_
5. **build and compare dust mass distributions**: Cumulative distributions with lifelines (handles upper limits), compared with Orion regions and the all-sky ALMA Herbig sample using logrank and KS tests; lognormal fit to get PDFs  
  > "Using the `lifelines` package (cite: DavidsonPilon2021) we obtain the cumulative distribution of the Herbig disks in Orion following (cite: Stapper2022)." (Dust mass distribution); "we use two tests, the `lifelines` `logrank_test` and the Kolmogorov-Smirnov test from `SciPy` (cite: 2020SciPy-NMeth)." (Comparison to the ALMA Herbig disks)
   - software: lifelines, SciPy
   - fitting: Lognormal distribution fitted through the cumulative distributions (sampler/priors not stated)  
  > "A lognormal distribution is fitted through the cumulative distributions, following previous works (cite: Williams2019; Stapper2022; Stapper2024), to obtain probability density distributions." (Comparison to the ALMA Herbig disks)
   - validation: Two independent tests (logrank including upper limits, KS); same completeness at ~1 Earth mass compared with the all-sky ALMA sample  
  > "Indeed, the cumulative distributions shown in Fig. [4](#fig:cdf_herbig_compare) have the same completeness at a disk mass of $\sim1$ M$_\oplus$." (Comparison to the ALMA Herbig disks)
6. **extract CO isotopologue spectra**: Align phase center with fixvis, export visibility spectra averaged over time, baseline and scans with plotms, bin by a factor of ten  
  > "first the phase center was aligned on-target using the `fixvis` task, after which the `plotms` task was used to export the measured visibility spectra averaged over time, baseline, and scans." (Gas observations)
   - software: CASA 5.8.0, fixvis, plotms
   - parameter: Binning factor 10, ~0.9 km/s resolution  
  > "The spectra have been binned by a factor of ten, resulting in a $\sim0.9$ km s$^{-1}$ resolution." (Gas observations)
   - fitting: _not stated_
   - validation: _not stated_
7. **compute external FUV irradiation and fit dust mass vs UV**: Query Simbad for stars earlier than A0, limit distances to 300-475 pc, compute FUV luminosity from BHAC-15 isochrones and Castelli spectra (911.6-2066 A), sum G0 within 10 pc (or 30 pc) projected distance, floor G0 at 1; fit linear relation with linmix  
  > "The FUV luminosities of these stars were then computed by using BHAC-15 isochrones (cite: Baraffe2015) and integrating model spectra (cite: Castelli2003) between 911.6 and 2066 Å." (Impact of UV on Herbig disk masses); "The minimum UV irradiation was set at 1 $G_0$." (Impact of UV on Herbig disk masses); "package (cite: Kelly2007) to fit a linear relationship through the data." (Impact of UV on Herbig disk masses)
   - software: Simbad, linmix
   - parameter: Stars limited to 300-475 pc, projected distances only  
  > "The distances to the stars were limited to 300-475 pc, and as the uncertainties on these distances can be fairly large only projected distances are used." (Impact of UV on Herbig disk masses)
   - parameter: Cutoff 10 pc (alternative 30 pc), no interstellar extinction  
  > "no stars beyond a projected distance of 10 pc from a given Herbig disk were taken into account, but interstellar extinction was not included otherwise." (Impact of UV on Herbig disk masses)
   - assumption: G0 unit of 1.6e-3 erg cm-2 s-1 (Habing)  
  > "in terms of $G_0$ ($1.6\times10^{-3}$ erg cm$^{-2}$ s$^{-1}$, (cite: Habing1968))" (Impact of UV on Herbig disk masses)
   - fitting: linmix linear fit of M_dust vs log(F_uv) (priors and chain settings not stated)  
  > "we find a relation $M_\text{dust}=a\times \log (F_\text{uv}) + b$ with respective slopes of -7.6±3.6 and -8.5±4.5, and offsets of 29.4±6.7 and 32.8±8.7." (Impact of UV on Herbig disk masses)
   - validation: Slope compared with the T Tauri L1641/L1647 value; two distance cutoffs tested  
  > "Including irradiation of stars out to 30 pc primarily changes the $G_0$ of the least irradiated disks to at most a few 10s $G_0$." (Impact of UV on Herbig disk masses); "they agree with the latter value within $2\sigma$." (Impact of UV on Herbig disk masses)

## Software

- **CASA** 5.8.0: Analysis of NOEMA uvfits: fixvis, uvmodelfit continuum fits, plotms spectrum export  
  > "The data were analyzed using the `Common Astronomy Software Applications` (CASA) application version 5.8.0" (Data selection and reduction)
- **CLIC (GILDAS)** : Standard pipeline calibration of NOEMA data  
  > "The NOEMA data were calibrated using the standard pipeline calibration using the `CLIC` program of the Grenoble Image and Line Data Analysis Software" (Data selection and reduction)
- **SciPy** : Kolmogorov-Smirnov tests (stellar mass sample and dust mass distributions)  
  > "we use two tests, the `lifelines` `logrank_test` and the Kolmogorov-Smirnov test from `SciPy` (cite: 2020SciPy-NMeth)." (Comparison to the ALMA Herbig disks)
- **lifelines** : Cumulative distributions with upper limits and logrank test  
  > "Using the `lifelines` package (cite: DavidsonPilon2021) we obtain the cumulative distribution of the Herbig disks in Orion following (cite: Stapper2022)." (Dust mass distribution)
- **linmix** : Linear fit of dust mass versus UV irradiation  
  > "package (cite: Kelly2007) to fit a linear relationship through the data." (Impact of UV on Herbig disk masses)
- **Simbad** : Query for ionizing stars with spectral types earlier than A0  
  > "for stars with spectral types earlier than A0 within the region on the sky" (Impact of UV on Herbig disk masses)
- **Python** 3.9: Listed among the software used in this work (specific use not stated)  
  > "Python version 3.9, astropy (cite: astropy2013; astropy2018), lifelines (cite: DavidsonPilon2021)" (Acknowledgements)
- **astropy** : Listed among the software used in this work (specific use not stated)  
  > "Python version 3.9, astropy (cite: astropy2013; astropy2018), lifelines (cite: DavidsonPilon2021)" (Acknowledgements)
- **matplotlib** : Listed among the software used in this work (specific use not stated)  
  > "matplotlib (cite: Hunter2007), numpy (cite: Harris2020), and scipy (cite: 2020SciPy-NMeth)" (Acknowledgements)
- **numpy** : Listed among the software used in this work (specific use not stated)  
  > "matplotlib (cite: Hunter2007), numpy (cite: Harris2020), and scipy (cite: 2020SciPy-NMeth)" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median dust mass of Herbig disks in Orion (excluding upper limits) | 11.7 | standard deviation 26 | Earth masses | 5 | The median of the disk masses is 11.7 $M_\oplus$ with a standard deviation of 26 $M_\oplus$, excluding the upper limits. |
| Dust mass range of Herbig disks (HD 290764 maximum, HD 38087 upper limit) | 91 down to <1.2 | not stated | Earth masses | 4 | The dust masses of the Herbig disks range from 91 $M_\oplus$ for HD 290764 down to $<1.2$ $M_\oplus$ for HD 38087. |
| HD 288012 secondary disk flux and dust mass | 16.5 mJy; 65 Earth masses | not stated | mJy; Earth masses | 4 | the disk around the secondary is detected with a flux of 16.5 mJy, corresponding to a disk mass of 65 $M_\oplus$ |
| Fraction of Herbig disks with mass above 10 Earth masses | ~50 (other Orion regions ~25 or lower) | not stated | percent | 5 | is at around 50% for the Herbig disks. For the other regions this is $\sim25$% or lower. |
| Detection rate of Orion Herbig disks | 83 (6 of 35 not detected) | not stated | percent | 3 | Out of the 35 disks in the Orion sample, 6 are not detected, resulting in a 83% detection rate. |
| Logrank and KS p-values, Orion vs all-sky ALMA Herbig dust masses | p = 0.26 (logrank), p = 0.32 (KS) | not stated | dimensionless | 5 | We find $p$-values for the distributions of $p$=0.26 (logrank) and $p$=0.32 (KS) |
| Lognormal mean log10(M_dust/M_earth), Orion sample (all-sky ALMA sample 1.27+0.05/-0.05) | 0.94 | +0.06/-0.07 | dex (log10 Earth masses) | 5 | The mean value of the distributions are Log$_{10}$($M_\text{dust}(M_\oplus)$)=0.94$^{+0.06}_{-0.07}$ and 1.27$^{+0.05}_{-0.05}$ for the Orion sample and the sample of (cite: Stapper2022) respectively. |
| Lognormal width, Orion sample (all-sky ALMA sample 0.61+0.06/-0.06) | 0.59 | +0.07/-0.06 | dex | 5 | The width of the distributions are the same, 0.59$^{+0.07}_{-0.06}$ and 0.61$^{+0.06}_{-0.06}$ respectively. |
| Disks with CO isotopologue detection at peak S/N of 6 or higher | 6 | not stated | disks | 6 | For these six disks we detect emission at a peak signal-to-noise of 6 and higher. |

## Qualitative findings

- CO is detected over all UV irradiation values traced; Herbig stellar luminosity dominates disk temperature unless within ~0.3 pc of an O-star  
  > "CO is detected over all UV irradiation values traced" (Impact of UV on Herbig disk masses); "the Herbig disk needs to be within (a projected distance of) $\sim0.3$ pc of an O-star" (Impact of UV on Herbig disk masses)
- HD 245185 may be a chance alignment: at ~20 pc from the O-star its irradiance would drop to 2-4 G0, consistent with the trend  
  > "This would decrease the irradiance to negligible values of around 2-4 $G_0$, aligning the disk mass with the seen trend." (Impact of UV on Herbig disk masses)
- Massive Orion Herbig disks such as HD 97048 and HD 142527 are absent, suggesting the all-sky ALMA coverage was slightly biased to massive disks  
  > "This suggests that the ALMA all-sky coverage may have been slightly biased toward including the most massive disks" (Comparison to the ALMA Herbig disks)

## Claim tuples

- H: Herbig disks are more massive than T Tauri disks in the same star-forming complex | E: Compare the cumulative dust mass distribution of the 35 Orion Herbig disks with NGC 2024, L1641/L1647, sigma Ori and lambda Ori surveys | R: About 50% of Herbig disks exceed 10 Earth masses versus ~25% or lower elsewhere | F: Herbig disks are more massive than T Tauri disks in Orion despite their older median age | **supported**
- H: The Orion Herbig dust mass distribution differs from the all-sky ALMA Herbig sample | E: Logrank and KS tests, lognormal fits | R: p = 0.26 (logrank), p = 0.32 (KS); means 0.94 vs 1.27 with equal widths | F: No significant difference between the distributions | **supported**
- H: ALMA coverage of Herbig disks was biased toward massive, well-known objects | E: Compare the complete Orion sample to the all-sky ALMA sample | R: Orion lacks very massive disks (above ~150 Earth masses) present in the ALMA sample, but the distributions are statistically consistent | F: The all-sky ALMA coverage may have been slightly biased to the most massive disks | **partially**
- H: External UV irradiation lowers the dust masses of Herbig disks | E: Compute G0 from ionizing stars and fit dust mass vs log(F_uv) with linmix | R: Slopes of -7.6+-3.6 (10 pc) and -8.5+-4.5 (30 pc), within 2 sigma of the T Tauri slope | F: A trend of decreasing dust mass with increasing UV irradiation, with a steeper slope than for T Tauri disks | **partially**
- H: The largest scattered-light disks in Orion are linked to giant planet formation in massive Herbig disks | E: Compare the SPHERE resolved disks of Valegard2024 with the dust masses | R: Three of four resolved disks are Herbig disks and among the more massive in the sample | F: This could be related to giant exoplanet formation in these disks | **partially**

## Reasoning

- Why this data: Existing ALMA Herbig disk coverage is a heterogeneous, 64% complete sample, so a complete survey of one region tests for bias  
  > "the Herbig sample of (cite: Stapper2022) is constructed from Herbig disks studied in a variety of ALMA projects (still 64% complete including all nearby star-forming regions)" (Introduction)
- Why this method: Disks are unresolved, so a Gaussian fit to visibilities is adequate for the flux  
  > "As all detections are unresolved, fitting a Gaussian to the visibilities is therefore a good approximation of the observations." (Data selection and reduction)
- Alternative: Extending the ionizing-star cutoff from 10 pc to 30 pc was tested and changes G0 only for the least irradiated disks  
  > "Including irradiation of stars out to 30 pc primarily changes the $G_0$ of the least irradiated disks to at most a few 10s $G_0$." (Impact of UV on Herbig disk masses)
- Alternative: Flux distributions compared directly (Appendix) to avoid dust-mass conversion uncertainties  
  > "a comparison between only the fluxes is shown in Appendix [6](#app:flux_distributions)" (Dust mass distribution)
- How they decided it was enough: _not stated_
- Limitation (authors): Optically thin assumption is likely the largest source of uncertainty in dust masses  
  > "Nevertheless, the dust masses are calculated under the assumption of optically thin emission, which is likely the largest source of uncertainty." (Data selection and reduction)
- Limitation (authors): NOEMA data are less sensitive than ALMA, so detection rates compare only at matched sensitivity  
  > "However, the ALMA data are more sensitive, and at the NOEMA sensitivity the same detection rate of 83% would have been obtained for the sample of (cite: Stapper2022)." (Comparison to the ALMA Herbig disks)
- Limitation (authors): Part of the observations suffered bad weather with 43% flagged  
  > "Due to this, 43% of the data are flagged." (Data selection and reduction)
- Caveat (inferred, ours): Only projected distances to ionizing stars are used, so G0 may be strongly over- or underestimated (acknowledged for HD 245185)
- Caveat (inferred, ours): Single dust temperature law and fixed beta = 1 for all disks; no optical depth correction for compact bright Herbig disks
- Caveat (inferred, ours): Slope of dust mass vs UV is only about 2 sigma from the T Tauri value, so the 'steeper' conclusion is weakly supported
- Caveat (inferred, ours): Mixing NOEMA (20% calibration error, 1'' beam) and ALMA fluxes of different bands (HD 290764 Band 7) without stated band-dependent mass corrections

## Reproducibility

- Data public (paper): ALMA archival product data for V1012 Ori are public; NOEMA data public status not stated  
  > "we obtained publicly available ALMA archival" (Data selection and reduction)
- Products in archive: ALMA pipeline product data used for V1012 Ori  
  > "the continuum flux is determined from the ALMA pipeline product data." (Table 1 notes)
- Missing: Raw NOEMA S22AU data access and CLIC version/flux model
- Missing: uvmodelfit initial parameters per source and continuum channel selection
- Missing: Imaging settings for the empty-image rms upper limits
- Missing: Line names/rest frequencies of the CO spectra
- Missing: linmix and lognormal fit settings
- Missing: The ALMA V1012 Ori flux and Stapper2022 procedure details
- Data volume (inferred): NOEMA: roughly tens of GB of uvfits for 25 sources; ALMA: under ~1 GB of product data for one source (estimate)
- Score (inferred): 3/5, Final dust masses and statistics can be recomputed from Table 1 fluxes and stated formulae, but raw NOEMA reduction is only loosely specified and ALMA is a very minor input
- Rediscovery candidate: no, NOEMA data public status not stated and ALMA data play only a minor role; reduction recipe is incomplete

## Links

- Method: (cite: Stapper2022) (Flux measurement method, dust mass assumptions and cumulative distribution approach inherited from it)
- Method: (cite: vanTerwisga2023) (Method for computing external FUV irradiation G0)
- Method: (cite: GuzmanDiaz2021) (Stellar and disk parameters for the sample)
- Companion: (cite: Stapper2022) (All-sky ALMA Herbig disk sample compared against)
- Companion: (cite: Stapper2024) (Additional NOEMA Herbig fluxes and sources with CO detections)
- Companion: (cite: Valegard2024) (SPHERE scattered-light survey of Orion disks (DESTINYS))
- Related: NOEMA project S22AU
- Related: ALMA 2021.1.01705.S
- Related: SODA (L1641/L1647 survey)
- Related: DESTINYS

## Checks

```json
{
 "quotes": 133,
 "quotes_ok": 133,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 117,
  "stated": 90,
  "rate": 0.769
 },
 "evidence_ok": true
}
```

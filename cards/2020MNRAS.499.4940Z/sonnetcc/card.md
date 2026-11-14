# Unravelling the enigmatic ISM conditions in Minkowski's object

`2020MNRAS.499.4940Z` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Zovaro, Henry R. M. | arXiv: 2010.03139 | DOI: 10.1093/mnras/staa3121

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, agn_and_quasars, star_formation
- Question: What are the stellar population, ionisation and gas-phase metallicity conditions in Minkowski's Object (a jet-induced star-forming dwarf), and what do they imply for its origin?  
  > "Using optical integral field spectroscopy, we present an analysis of the ISM conditions in Minkowski’s Object" (abstract); "We hypothesise that Minkowski’s Object either (a) was formed as a result of jet-induced star formation in pre-existing gas clumps in the stellar bridge" (abstract)
- Target **Minkowski's Object (MO)**: coordinates _not stated_; z/distance z = 0.0189  
  > "Minkowski’s Object ($z = 0.0189$), a peculiar star-forming dwarf galaxy located in the path of a radio jet from the galaxy NGC 541." (abstract); "Due to its low redshift (cite: Croft2006), MO presents a critical opportunity to study an object formed by positive feedback in high resolution." (Introduction); distance from redshift attributed to (cite: Croft2006)  
  > "Minkowski’s Object ($z = 0.0189$), a peculiar star-forming dwarf galaxy located in the path of a radio jet from the galaxy NGC 541." (abstract); "Due to its low redshift (cite: Croft2006), MO presents a critical opportunity to study an object formed by positive feedback in high resolution." (Introduction)
- Target **NGC 541**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: _not stated_
- frequencies and spectral setup: ALMA: 106 GHz continuum image taken from an earlier study (used only for jet power). Main optical data are WiFeS: B3000 (3200-5000 A) and R7000 (5290-7060 A) gratings  
  > "Using the ALMA 106 GHz continuum image of , we used the minimum energy method" (Properties of the radio jet); "using the low-resolution B3000 (3200 Å–5000 Å" (Observations and data reduction); "the high-resolution R7000 (5290 Å–7060 Å" (Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: WiFeS (not ALMA): total effective exposure time 9600 s  
  > "The total effective exposure time was 9600 s." (Observations and data reduction)
- observing dates: WiFeS (not ALMA): 29 November and 1 December 2016  
  > "MO was observed on the 29th of November and 1st of December 2016 (PI Banfield, proposal ID 4160092)" (Observations and data reduction)
- pi or archival as stated: WiFeS (not ALMA): PI Banfield, proposal ID 4160092; ALMA image provenance not stated  
  > "(PI Banfield, proposal ID 4160092)" (Observations and data reduction)
- Other facility **WiFeS on ANU 2.3 m telescope (Siding Spring)**: Optical integral field spectroscopy cubes of MO (primary data of the paper)  
  > "We observed MO with the Wide-Field Spectrograph (cite: Dopita2007; Dopita2010) on the Australian National University 2.3 m telescope at Siding Spring Observatory, NSW, Australia." (Observations and data reduction)
- Other facility **VLT/VIMOS (Hamer et al. data of NGC 541)**: Spatially resolved emission line fluxes of NGC 541, used to estimate its gas-phase metallicity  
  > "(cite: Hamer2016) observed NGC 541 with VLT/VIMOS and obtained spatially resolved emission line fluxes, which we used to estimate the gas-phase metallicity." (Pre-existing enriched gas in the stellar bridge)
- External data: ALMA 106 GHz continuum image of the jet region (used for the jet-power estimate)  
  > "Using the ALMA 106 GHz continuum image of , we used the minimum energy method" (Properties of the radio jet) [from earlier study; citation not preserved in the paper text]
- External data: Molecular gas masses of MO from CO detections in four clumps  
  > "Molecular gas has been detected in four distinct clumps with intervening diffuse emission (cite: Lacy2017)" (Minkowski’s Object) [from (cite: Lacy2017)]
- External data: H I cloud mass of MO  
  > "MO is embedded in a cloud of neutral gas with an estimated mass" (Minkowski’s Object) [from citation not preserved in the paper text (Table reference a)]
- External data: SSP template models used for stellar population fitting  
  > "we used the SSP models of (cite: GonzalezDelgado2005) which have a fine age resolution at young stellar ages" (Stellar population analysis) [from (cite: GonzalezDelgado2005)]
- External data: Sample of typical H II regions in nearby spiral galaxies, for line-ratio comparison  
  > "we include the sample of ‘typical’ H II regions in nearby spiral galaxies from (cite: vanZee1998)" (Excitation mechanism) [from (cite: vanZee1998)]
- External data: VIMOS emission line fluxes of NGC 541 used for its gas-phase metallicity  
  > "(cite: Hamer2016) observed NGC 541 with VLT/VIMOS and obtained spatially resolved emission line fluxes" (Pre-existing enriched gas in the stellar bridge) [from (cite: Hamer2016)]
- External data: Theoretical metallicity and ionisation parameter diagnostics  
  > "using the theoretical diagnostics provided by (cite: KewleyNichollsSutherland2019)" (Metallicity and ionisation parameter) [from (cite: KewleyNichollsSutherland2019)]
- Simulation/model as data: Slow shock models (Dopita & Sutherland 2017) and fast shock models (Allen et al. 2008) overlaid on diagnostic diagrams  
  > "overlaid with the slow and fast shock models of (cite: Dopita&Sutherland2017) and (cite: Allen2008) respectively." (Shock excitation)
- Simulation/model as data: DIG photoionisation models of Mathis (1986) overlaid on a diagnostic diagram  
  > "we present a ODD diagram overlaid with the DIG photoionisation models of (cite: Mathis1986)" (Diffuse Ionised Gas)
- Simulation/model as data: MAPPINGS V H II region plane-parallel model grids (Kewley et al. 2019) used for line-ratio comparison and as NebulaBayes input  
  > "Grids from (cite: Kewley2019) representing MAPPINGS V (cite: Sutherland2018) H II region plane-parallel models" (Excitation mechanism)
- Simulation/model as data: STARBURST99 solar-metallicity instantaneous-burst SSP model with Salpeter IMF, used for supernova rate and surface-brightness fading  
  > "we used a STARBURST99 (cite: Leitherer1999) solar metallicity SSP model with a Salpeter IMF and an instantaneous SFH." (On the formation of Minkowski’s Object)

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

- Minimum energy method for the jet power  
  > "we used the minimum energy method, as detailed in section 5.1 of (cite: Zovaro2019a), to estimate the power of the Eastern jet." (Properties of the radio jet) [from section 5.1 of (cite: Zovaro2019a)]
- Hα star formation rate calibration  
  > "We calculated the global SFR using the same calibration used by" (Star formation rate) [from earlier study of MO (citation not preserved in the paper text)]
- PPXF regularisation parameter chosen by the standard method  
  > "was determined using the standard method (cite: Boardman2017)" (Stellar population analysis) [from (cite: Boardman2017)]
- Electron density from the [S II] doublet ratio  
  > "and eqn. 3 of (cite: Proxauf2014)" (Electron density) [from eqn. 3 of (cite: Proxauf2014)]
- Iterative metallicity and ionisation parameter estimation  
  > "We followed the iterative method of (cite: Kewley&Dopita2002) to simultaneously estimate the gas-phase oxygen abundance" (Metallicity and ionisation parameter) [from (cite: Kewley&Dopita2002)]

### Not stated but needed to reproduce (our reading)

- ALMA project code, observing setup, calibration and imaging of the 106 GHz continuum image; the paper only cites it from earlier work and takes a constant 30 uJy/beam from it
- Which earlier study provided the ALMA image, the HI mass, the stellar mass and the SFR calibration (citations are missing from the paper text)
- WiFeS cubes are not public; only available on request, so the reduced mosaic cannot be rebuilt from the archive
- PPXF settings not given: fitted wavelength range, velocity and dispersion starting values, emission line list in the fit, final regul value, number of templates in the Geneva grid used per metallicity
- Width of the emission-line fitting window and the rule used to pick sky-only regions and the sky lines used for scaling
- Exact spaxel binning scheme for the factor-of-three binned reddening map
- How the iterative Kewley and Dopita solver was implemented (code, convergence criterion) and how metallicity uncertainties of 0.01 dex were derived

## Analysis recipe

1. **Reduce and mosaic the WiFeS cubes**: PyWiFeS reduction; sky spectrum from source-free regions scaled to sky lines; cube scaling by least squares on overlaps; sigma-clipped median mosaic; Galactic extinction correction  
  > "The observations were reduced in the standard way using PYWIFES, the data reduction pipeline for WiFeS (cite: Childress2014)." (Data reduction); "Mosaics were created by spatially shifting the scaled data cubes and combining them by taking the sigma-clipped median of each pixel." (Data reduction)
   - software: PyWiFeS
   - parameter: Galactic A_V = 0.1198 from the Schlafly & Finkbeiner extinction map  
  > "the data cubes were corrected for Galactic extinction using the extinction map of (cite: Schlafly&Finkbeiner2011) which gives $A_V = 0.1198$." (Data reduction)
   - parameter: No sky frames taken; sky from empty regions of the field of view  
  > "we did not take sky frames during our observing campaign." (Data reduction)
   - assumption: Fitzpatrick & Massa (2007) reddening curve with R_V = 3.1  
  > "we used reddening curve of (cite: Fitzpatrick&Massa2007) with $R_V = 3.1$." (Data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit the integrated stellar continuum for age and metallicity**: PPXF full spectral fitting of SSP templates (Geneva isochrones) to the B3000 spectrum summed over bright Halpha spaxels, with simultaneous Gaussian emission lines, regularised weights  
  > "by fitting combinations of simple stellar population (SSP) templates to the stellar continuum." (Stellar population analysis); "hence we only analysed our B3000 data with PPXF." (Stellar population analysis)
   - software: PPXF
   - parameter: Integrated spectrum from spaxels with Halpha flux above 1.5e-15 erg/s/cm2  
  > "We therefore created an integrated spectrum by summing the spaxels in which the H$\upalpha$ flux exceeded $1.5 \times 10^{-15} \rm \, erg\,s^{-1}\,cm^{-2}$." (Stellar population analysis)
   - parameter: Median S/N about 7.5 per spectral pixel  
  > "The median S/N in the resulting spectrum was approximately 7.5 per spectral pixel." (Stellar population analysis)
   - parameter: 46 age bins from 1 Myr to 10 Gyr, five metallicities (Geneva)  
  > "spanning an age range 1 Myr to 10 Gyr divided into 46 bins with five metallicities for the Geneva isochrones" (Stellar population analysis)
   - parameter: 4th-order multiplicative polynomial  
  > "A 4th-order multiplicative polynomial was included in the fit to compensate for extinction and calibration errors." (Stellar population analysis)
   - parameter: Regularisation toward the smoothest solution consistent with the data  
  > "was used to bias the best-fit template weights towards the smoothest solution consistent with the data" (Stellar population analysis)
   - assumption: Salpeter IMF in the SSP templates  
  > "The SSP templates were generated using both the Geneva and the Padova isochrones with a Salpeter IMF" (Stellar population analysis)
   - fitting: Continuum and emission lines fitted simultaneously with independent velocity components; emission lines as Gaussians  
  > "the stellar continuum and the emission lines were fitted simultaneously, adopting independent velocity components for each, where emission lines were fit using Gaussian profiles." (Stellar population analysis)
   - validation: Repeated with Padova isochrones and fixed-metallicity templates; individual SSP fits show minimum reduced chi2 at young ages  
  > "We confirmed that this did not bias our results by repeating our analysis using the Padova isochrones, which yielded very similar results" (Stellar population analysis); "We therefore repeated our analysis using templates with fixed metallicities, yielding similar results" (Stellar population analysis)
3. **Measure emission line fluxes per spaxel**: Simultaneous single-Gaussian fits to all lines plus a linear continuum, with shared velocity and dispersion, then spaxel selection and LSF correction  
  > "to estimate line fluxes in each spaxel by simultaneously fitting a single Gaussian profile to each emission line and a linear component to fit the stellar continuum." (Emission line fitting); "All emission lines were fitted simultaneously and were constrained to have the same systemic velocity and velocity dispersion." (Emission line fitting)
   - software: MPFIT
   - parameter: Keep spaxels with reduced chi2 < 2 and S/N > 3 in the main lines  
  > "we only include spaxels in which the fit has a reduced-$\chi^2 < 2$ and $\rm S/N > 3$" (Emission line fitting)
   - parameter: Instrumental width from sky lines subtracted in quadrature  
  > "the instrumental resolution was accounted for by subtracting the width of the line spread function (LSF) in quadrature from the width of the fitted Gaussian" (Emission line fitting)
   - assumption: Stellar continuum not subtracted before line fitting; stellar absorption judged minor  
  > "we did not subtract the best-fit stellar continuum from spaxels before fitting emission lines." (Emission line fitting)
   - fitting: MPFIT Levenberg-Marquardt least squares  
  > "We used MPFIT (cite: Markwardt2009), a PYTHON implementation of the Levenberg-Marquardt algorithm" (Emission line fitting)
   - validation: Stellar absorption estimated from PPXF and STARBURST99 equivalent widths, found to be a small fraction of the line flux  
  > "confirming that this has a minimal effect on our reported emission line fluxes." (Emission line fitting)
4. **Derive extinction and electron density**: Halpha/Hbeta Balmer decrement per spaxel for A_V (also on cubes binned by three); [S II] 6716/6731 ratio for electron density  
  > "After correcting for foreground extinction, we used the H$\upalpha$ and H$\upbeta$ fluxes to estimate the extinction." (Reddening); "we repeated the above process after spatially binning the data cube by a factor of three" (Reddening)
   - parameter: Only spaxels with S/N > 3 in the Halpha/Hbeta ratio kept for A_V  
  > "Only spaxels in which the S/N in the H$\upalpha$/H$\upbeta$ ratio exceeds 3 are shown." (Reddening)
   - assumption: Fitzpatrick & Massa reddening curve, R_V = 3.1; case B Balmer decrement 2.85  
  > "we have used the reddening curve of (cite: Fitzpatrick&Massa2007) with $R_V = 3.1$." (Reddening); "which was estimated assuming the case B recombination Balmer decrement" (X-ray photoionisation)
   - fitting: _not stated_
   - validation: _not stated_
5. **Diagnose the excitation mechanism**: Optical diagnostic diagrams compared with H II region sample, MAPPINGS grids, shock models, DIG models and NebulaBayes; non-stellar fraction bounded using Kewley & Ellison (2008)  
  > "To determine the excitation mechanism of the emission line gas, we use optical diagnostic diagrams (cite: Baldwin1981; Veilleux&Osterbrock1987; Kewley2001; Kauffmann2003; Kewley2006)" (Excitation mechanism)
   - software: NebulaBayes, MAPPINGS V
   - parameter: Slow shock models v_s = 70-170 km/s  
  > "The slow shock models are shown for shock speeds $v_s = 70 - 170 \,\rm km\,s^{-1}$" (Shock excitation)
   - parameter: NebulaBayes pressure grid log(P/k) = 4.0 to 9.0  
  > "with $\log(P/k)$ varying from $\log(P/k) = 4.0$ to $\log(P/k) = 9.0$" (Excitation mechanism)
   - assumption: MAPPINGS grids at log(P/k) = 5.0 for typical H II regions  
  > "Grids from (cite: Kewley2019) representing MAPPINGS V (cite: Sutherland2018) H II region plane-parallel models" (Excitation mechanism)
   - fitting: NebulaBayes Bayesian fit, also with a log-normal prior on pressure centred on log(P/k) <= 5.0  
  > "Using NEBULABAYES with a log-normal prior on the ISM pressure centred on $\log(P/k) \leq 5.0$" (Excitation mechanism)
   - validation: Upper limit of 15 per cent non-stellar contribution from Kewley & Ellison (2008) threshold and few spaxels above the starburst line  
  > "found that only an AGN photoionisation contribution greater than $15 \,\rm per \, cent$ can produce line ratios lying above the maximum starburst line of" (Excitation mechanism)
6. **Estimate the star formation rate and depletion times**: Halpha luminosity to SFR calibration of an earlier study, with a lower limit taking 15 per cent of Halpha as non-stellar; depletion times from HI and H2 masses  
  > "We therefore estimate a conservative lower limit by assuming 15 per cent of the H$\upalpha$ flux is due to ionisation sources other than star formation" (Star formation rate)
   - parameter: Systematic uncertainty of about 30 per cent from the IMF high-mass shape  
  > "has a systematic uncertainty of approximately $30 \rm \, per \, cent$ due to uncertainty in the shape of the IMF at the high-mass end" (Star formation rate)
   - assumption: H0 = 70 km/s/Mpc, Omega_M = 0.3, Omega_Lambda = 0.7  
  > "we assume a cosmology with $H_0 = 70\rm\,km\,s^{-1}\,Mpc^{-1}$" (Introduction)
   - fitting: _not stated_
   - validation: Compared with an earlier estimate of the same quantity and with van Breugel et al. Halpha+[N II] flux  
  > "Our flux estimate is closer to that of (cite: vanBreugel1985)" (Star formation rate)
7. **Derive gas-phase metallicity and ionisation parameter maps**: Iterative Kewley & Dopita method with Kewley et al. 2019 diagnostics: N2O2 for metallicity, O3O2 for log U; other diagnostics (N2, O2S2, O3N2, R23) as comparison  
  > "We followed the iterative method of (cite: Kewley&Dopita2002) to simultaneously estimate the gas-phase oxygen abundance" (Metallicity and ionisation parameter)
   - parameter: Constant pressure log(P/k) = 5.0  
  > "assuming a constant pressure $\log(P/k) = 5.0$, which is appropriate for typical H II regions." (Metallicity and ionisation parameter)
   - assumption: N2O2 diagnostic robust to AGN contamination at the estimated contamination level; shocks and DIG assumed to act similarly  
  > "We expect the harder radiation fields from shocks and DIG to have a similar effect on the \[N II\]/\[O II\] ratio." (Metallicity and ionisation parameter)
   - fitting: _not stated_
   - validation: Variation checked with four other diagnostics, which show similar variations  
  > "The magnitudes of the measured metallicity variations for the N2O2, R23, O2S2, N2 and O3N2 diagnostics are 0.55 dex, 0.43 dex, 0.62 dex, 0.33 dex and 0.36 dex respectively" (Metallicity and ionisation parameter)
8. **Estimate the Eastern jet power from the ALMA 106 GHz image**: Minimum energy method on a truncated cone jet volume using the ALMA 106 GHz continuum flux density  
  > "The jet volume was approximated as a truncated cone, with length 21 kpc and end surface radii of 1.5 kpc and 6 kpc" (Properties of the radio jet)
   - parameter: Constant flux density 30 uJy/beam  
  > "was assumed to have a constant flux density of $30 \,\rm \upmu Jy \, beam^{-1}$" (Properties of the radio jet)
   - parameter: Spectral index 0.8  
  > "with a spectral index $\alpha = 0.8$" (Properties of the radio jet)
   - assumption: Jet age 1e7 yr, matched to the MO stellar age  
  > "A jet age of $10^7\,\rm yr$ was adopted, chosen to be consistent with the age of the stellar population of MO" (Properties of the radio jet)
   - fitting: _not stated_
   - validation: _not stated_
9. **Test whether stellar enrichment explains the metallicity variation**: SSP chemical enrichment model giving oxygen yield per stellar mass versus age and metallicity  
  > "we used an SSP model to estimate the oxygen yield per stellar mass for stars of a given age and metallicity." (Enrichment from star formation)
   - parameter: Kroupa IMF slope 1.3, 0.01-120 Msun, core-collapse upper mass limit 50 Msun  
  > "We assume a (cite: Kroupa2001) IMF (slope $\alpha = 1.3$) in the range $0.01-120\,\rm M_\odot$, with an upper mass limit for core-collapse supernovae of $50\,\rm M_\odot$." (Enrichment from star formation)
   - assumption: Age spread of a few Myr from the PPXF fit  
  > "with a spread of only $1-2$ Myr" (Enrichment from star formation)
   - fitting: _not stated_
   - validation: _not stated_
10. **Model supernova rate and fading of MO with STARBURST99**: STARBURST99 solar-metallicity instantaneous-burst SSP with Salpeter IMF for the supernova rate and surface-brightness evolution  
  > "we used a STARBURST99 (cite: Leitherer1999) solar metallicity SSP model with a Salpeter IMF and an instantaneous SFH." (On the formation of Minkowski’s Object)
   - software: STARBURST99
   - parameter: Present-day V-band surface brightness 22.7 mag/arcsec2 as starting point  
  > "Given the present-day $V$ band surface brightness of $\mu_V = 22.7 \,\rm mag \, arcsec^{-2}$" (On the formation of Minkowski’s Object)
   - assumption: Solar metallicity, instantaneous burst, Salpeter IMF  
  > "with an instantaneous burst SFH and a Salpeter IMF using STARBURST99 (cite: Leitherer1999)" (Star formation rate)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **PyWiFeS** : Reduction of the WiFeS data  
  > "The observations were reduced in the standard way using PYWIFES, the data reduction pipeline for WiFeS (cite: Childress2014)." (Data reduction)
- **PPXF** : Stellar population fitting of the integrated spectrum  
  > "by fitting combinations of simple stellar population (SSP) templates to the stellar continuum." (Stellar population analysis)
- **MPFIT** : Per-spaxel emission line fitting  
  > "We used MPFIT (cite: Markwardt2009), a PYTHON implementation of the Levenberg-Marquardt algorithm" (Emission line fitting)
- **NebulaBayes** : Bayesian check of line ratios against H II region model grids  
  > "a PYTHON package that uses a Bayesian method to estimate ISM conditions from observed emission line fluxes using input model grids." (Excitation mechanism)
- **STARBURST99** : Halpha EW, supernova rate and fading predictions for MO  
  > "we used a STARBURST99 (cite: Leitherer1999) solar metallicity SSP model with a Salpeter IMF and an instantaneous SFH." (On the formation of Minkowski’s Object)
- **MAPPINGS V** V: Source of H II region model grids compared with the data  
  > "representing MAPPINGS V (cite: Sutherland2018) H II region plane-parallel models" (Excitation mechanism)
- **SED@** : Generated SSP templates used in the stellar population fit  
  > "Model generated with SED@.0 code" (Acknowledgements)
- **QFitsView** : Named as used in the research (specific use not stated)  
  > "a software package for reducing astronomical data written by Thomas Ott" (Acknowledgements)
- **NumPy** : Named as used in the research (specific use not stated)  
  > "the PYTHON packages NUMPY" (Acknowledgements)
- **SciPy** : Named as used in the research (specific use not stated)  
  > "(cite: Scipy2001), and ASTROPY" (Acknowledgements)
- **Astropy** : Named as used in the research (specific use not stated)  
  > "a community-developed core package for Astronomy (cite: Astropy2013; Astropy2018)" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Young stellar population age | 4-5 Myr (and an older population at 1 Gyr) | not stated | Myr | 2 | There are two clear stellar populations in MO, with approximate ages of $4-5 \,\rm Myr$ and $1 \,\rm Gyr$. |
| Median S/N of integrated spectrum | 7.5 | not stated | per spectral pixel | 2 | The median S/N in the resulting spectrum was approximately 7.5 per spectral pixel. |
| Mean A_V in MO | 0.17 | 0.04 | mag | 4 | The mean $A_V = 0.17 \pm 0.04$, which is slightly higher than the value of |
| Mean [S II] 6716/6731 ratio R | 1.35 | 0.03 | dimensionless | 4 | with the mean $R  = 1.35 \pm 0.03$ |
| Total Halpha flux | 4.79e-14 | 0.1e-14 | erg s^-1 cm^-2 | 3 | Our SFR estimate and total H$\upalpha$ flux ($\left(4.79 \pm 0.1\right) \times 10^{-14}\rm\,erg\,s^{-1}\,cm^{-2}$) |
| Halpha velocity dispersion | about 15 in most regions, peaking at about 30 in the West | not stated | km/s | 3 | with values around $15\,\rm km\,s^{-1}$ in most parts of the object, peaking in the West with $\sigma \approx 30 \,\rm km\,s^{-1}$. |
| Upper limit on non-stellar ionisation contribution | 15 per cent | not stated | per cent | 5 | we therefore place an upper limit of $15 \,\rm per \, cent$ on the contribution of non-stellar ionisation sources in MO. |
| Global SFR (total Halpha flux) | 0.28 | 0.09 | Msun/yr | 6 | Using the total H$\upalpha$ flux gives $\rm SFR = 0.28 \pm 0.09 \,\rm M_\odot\,yr^{-1}$. |
| HI depletion time | 1.7-2.0 | not stated | Gyr | 6 | This corresponds to a H I depletion time $t_{\rm dep, \, H\,I} \sim 1.7 - 2.0 \,\rm Gyr$ |
| Metallicity variation (N2O2 diagnostic) | 0.55 | not stated | dex | 7 | The magnitudes of the measured metallicity variations for the N2O2, R23, O2S2, N2 and O3N2 diagnostics are 0.55 dex, 0.43 dex, 0.62 dex, 0.33 dex and 0.36 dex respectively |
| Metallicity variation (R23, O2S2, N2, O3N2) | 0.43, 0.62, 0.33, 0.36 | not stated | dex | 7 | are 0.55 dex, 0.43 dex, 0.62 dex, 0.33 dex and 0.36 dex respectively |
| Typical per-spaxel uncertainty of N2O2 metallicity | 0.01 | not stated | dex | 7 | The typical uncertainty in each spaxel is $0.01 \,\rm dex$. |
| Eastern jet power | 1.2e43 | not stated | erg s^-1 | 8 | These parameters yield a jet power of approximately $1.2 \times 10^{43}\,\rm erg \, s^{-1}$. |
| Oxygen yield increase over 5 Myr | factor of 2 | not stated | dimensionless | 9 | the oxygen yield increases by only a factor of 2 over a period of 5 Myr |
| Predicted V-band surface brightness after 100 Myr and 1 Gyr | 24.2 and 25.7 | not stated | mag/arcsec2 | 10 | we predict MO to fade to $\mu_V = 24.2 \,\rm mag \, arcsec^{-2}$ and $\mu_V = 25.7 \,\rm mag \, arcsec^{-2}$ in approximately 100 Myr and 1 Gyr respectively |

## Qualitative findings

- Radial velocities increase from South to North, consistent with CO and HI  
  > "The radial velocities increase from South to North, which is consistent with those of the CO and H I" (Kinematics and morphology)
- Halpha emission follows the stellar distribution, concentrated along the central bar  
  > "The H$\upalpha$ emission appears to follow the stellar distribution, which can be seen in the bottom panel of Fig." (Kinematics and morphology)
- Formation of MO directly from the ICM is unlikely  
  > "it therefore appears unlikely that MO formed directly from the ICM." (On the formation of Minkowski’s Object)
- Supernova 2010ib is consistent with a conventional IMF  
  > "Therefore, SN explosion 2010ib is consistent with MO having a conventional IMF." (Star formation rate)

## Claim tuples

- H: Is the stellar mass of MO dominated by a young population formed in a recent jet interaction? | E: PPXF fitting of GonzalezDelgado SSP templates to the integrated WiFeS B3000 spectrum | R: Dominant young population about 10 Myr old (4-5 Myr and 1 Gyr components in the best fit) | F: The bulk of the stellar mass formed during a recent jet interaction | **supported**
- H: Are the emission line ratios in MO consistent with star formation alone? | E: Spaxel-by-spaxel diagnostic diagrams, comparison with H II region, shock and DIG models and NebulaBayes | R: Mostly star formation, with enhanced [S II]/Halpha and [O I]/Halpha in some spaxels; contamination bounded at 15 per cent | F: Star formation dominates, with a low-level non-stellar contribution; shocks and DIG alone do not explain the enhanced ratios | **supported**
- H: What causes the large gas-phase metallicity variation across MO? | E: Strong-line diagnostics per spaxel, plus tests with an SSP oxygen yield model, jet outflow argument and NGC 541 metallicity | R: Metallicity varies by about 0.5 dex (N2O2 0.55 dex); stellar enrichment, jet outflow and stellar-bridge enrichment cannot explain it | F: Origin of the variation is unexplained, and the size may be overestimated by contamination | **partially**
- H: How did MO form? | E: Comparison of MO properties with jet-induced star formation from ICM, stellar-bridge gas clouds and infalling gas-rich dwarf scenarios | R: ICM and cooling filaments disfavoured; two scenarios remain | F: MO formed either from pre-existing HI clouds in the stellar bridge or is a gas-rich dwarf with jet-elevated star formation | **partially**

## Reasoning

- Why this data: Integral field spectroscopy allows spatially resolved ISM conditions, unlike earlier photometry and slit spectra  
  > "this work utilises integral field spectroscopy, enabling us to spatially resolve the ISM conditions in this object for the first time." (Introduction)
- Why this method: Geneva isochrones chosen because their templates reach lower metallicities than Padova  
  > "we used the Geneva isochrones for which the stellar templates extend to lower metallicities than the Padova isochrones." (Stellar population analysis)
- Alternative: Padova isochrones and fixed-metallicity templates tried and gave similar results  
  > "The results are very similar to those obtained using the Geneva isochrones." (Additional PPXF fits)
- Alternative: Shocks and DIG rejected as the main cause of enhanced [S II] and [O I]  
  > "We therefore rule out DIG as the main contributor to the unusual line ratios in MO." (Diffuse Ionised Gas); "However, we cannot rule out the presence of shocks that are too slow to contribute to the optical line emission." (Shock excitation)
- Alternative: AGN photoionisation modelling not done, left to future work  
  > "which will be the subject of future work." (X-ray photoionisation)
- How they decided it was enough: _not stated_
- Limitation (authors): Metallicity estimates uncertain because non-stellar contamination cannot be quantified  
  > "we note that our metallicity estimates are uncertain because we are unable to quantify the amount of contamination from sources other than star formation." (Metallicity and ionisation parameter)
- Limitation (authors): Data lacked S/N to fit ages and metallicities per spaxel  
  > "our data cubes lacked the S/N to recover ages and metallicities in each spaxel." (Stellar population analysis)
- Limitation (authors): Rotation curve and gravitational mass of MO cannot be constrained  
  > "meaning we cannot constrain the gravitational mass of MO from its rotation curve." (On the formation of Minkowski’s Object)
- Caveat (inferred, ours): Ages come from one integrated spectrum with median S/N about 7.5, no uncertainties on the age weights are given
- Caveat (inferred, ours): The 15 per cent non-stellar limit is borrowed from an AGN mixing result and applied to shocks and DIG without direct test
- Caveat (inferred, ours): Metallicity variation depends on N2O2 correlating with S2, which may itself trace non-stellar ionisation
- Caveat (inferred, ours): ALMA data play only a supporting role and its details are not given, so the jet power cannot be checked from this paper

## Reproducibility

- Data public (paper): Data available on reasonable request only  
  > "The data underlying this article will be shared on reasonable request to the corresponding author." (Data availability)
- Products in archive: _not stated_
- Missing: Reduced WiFeS cubes (on request only)
- Missing: ALMA project code and processing of the 106 GHz image
- Missing: PPXF configuration and final regularisation value
- Missing: Emission line fit window widths and sky region selection
- Data volume (inferred): Small (below 1 GB) for the WiFeS cubes; the ALMA image is not reprocessed in this paper
- Score (inferred): 2/5, Main optical data are not public, ALMA use is a single borrowed image without project code, though the analysis methods are largely described.
- Rediscovery candidate: no, Data are only available on request and the ALMA part is not identified, so the main numbers cannot be redone from public data.

## Links

- Method: (cite: Childress2014) (PyWiFeS reduction pipeline)
- Method: (cite: Cappellari&Emsellem2004; Cappellari2017) (PPXF method and implementation)
- Method: (cite: Zovaro2019a) (Minimum energy jet power method)
- Method: (cite: KewleyNichollsSutherland2019) (Metallicity and ionisation parameter diagnostics)
- Method: (cite: Kewley&Dopita2002) (Iterative metallicity and ionisation parameter method)
- Companion: (cite: Salome2015) (CO measurements and properties of MO and NGC 541)
- Companion: (cite: Lacy2017) (CO molecular gas detection in MO)
- Companion: (cite: Hamer2016) (VIMOS observations of NGC 541 used for its metallicity)

## Checks

```json
{
 "quotes": 130,
 "quotes_ok": 130,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2015.1.00570.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 15,
 "numeric_problems": 0,
 "fill": {
  "facts": 143,
  "stated": 95,
  "rate": 0.664
 },
 "evidence_ok": true
}
```

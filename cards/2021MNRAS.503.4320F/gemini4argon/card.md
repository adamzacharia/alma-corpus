# ALMA-IRDC - II. First high-angular resolution measurements of the <SUP>14</SUP>N/<SUP>15</SUP>N ratio in a large sample of infrared-dark cloud cores

`2021MNRAS.503.4320F` | Monthly Notices of the Royal Astronomical Society 2021 | first author: Fontani, F. | arXiv: 2103.09123 | DOI: 10.1093/mnras/stab700

Card schema 1.0 | model gemini-4-argon | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry, milky_way_ism
- Question: What is the $^{14}$N/$^{15}$N ratio in N$_{2}$H$^{+}$ at high angular resolution across dense cores in infrared-dark clouds, and how does it relate to surrounding diffuse gas and core physical or evolutionary properties?  
  > "In this paper, we present the first interferometric study of the $^{14}$N/$^{15}$N ratio towards a large sample of IRDC cores in N$_{2}$H$^{+}$ at high-angular resolution." (Introduction); "In particular, because each core is classified as starless or star-forming within each cloud, we are also able to compare the $^{14}$N/$^{15}$N ratios with the presence/absence of protostellar activity." (Introduction)
- Target **Cloud C (G028.37+00.07)**: coordinates 18:42:50.03 -04:03:23.4  
  > "| C | G028.37+00.07 | 18:42:50.03 | –04:03:23.4 | 78 | 5.0 |" (Observations and data reduction); z/distance d = 5.0 kpc, V_sys = 78 km s^-1  
  > "| C | G028.37+00.07 | 18:42:50.03 | –04:03:23.4 | 78 | 5.0 |" (Observations and data reduction); distance from _not stated_
- Target **Cloud D (G028.53–00.25)**: coordinates 18:44:16.94 -03:59:40.8  
  > "| D | G028.53–00.25 | 18:44:16.94 | –03:59:40.8 | 86 | 5.7 |" (Observations and data reduction); z/distance d = 5.7 kpc, V_sys = 86 km s^-1  
  > "| D | G028.53–00.25 | 18:44:16.94 | –03:59:40.8 | 86 | 5.7 |" (Observations and data reduction); distance from _not stated_
- Target **Cloud F (G034.43+00.24)**: coordinates 18:53:18.43 +01:27:13.5  
  > "| F | G034.43+00.24 | 18:53:18.43 | +01:27:13.5 | 57 | 3.7 |" (Observations and data reduction); z/distance d = 3.7 kpc, V_sys = 57 km s^-1  
  > "| F | G034.43+00.24 | 18:53:18.43 | +01:27:13.5 | 57 | 3.7 |" (Observations and data reduction); distance from _not stated_
- Target **Cloud H (G035.39–00.33)**: coordinates 18:57:09.42 +02:08:05.4  
  > "| H | G035.39–00.33 | 18:57:09.42 | +02:08:05.4 | 43 | 2.9 |" (Observations and data reduction); z/distance d = 2.9 kpc, V_sys = 43 km s^-1  
  > "| H | G035.39–00.33 | 18:57:09.42 | +02:08:05.4 | 43 | 2.9 |" (Observations and data reduction); distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.00687.S, 2018.1.00850.S
- bands: 3 mm  
  > "We present the first interferometric survey of the $^{14}$N/$^{15}$N ratio in N$_{2}$H$^{+}$ obtained with Atacama Large Millimeter Array observations towards four infrared-dark clouds harbouring 3 mm continuum cores associated with different physical properties." (Abstract)
- frequencies and spectral setup: N2H+ (1-0) at 93171.88-93176.13 MHz (channel spacing ~0.05 km/s); N15NH+ (1-0) at 91204.26-91208.52 MHz (channel spacing ~0.1 km/s); spectral resolution is twice the channel spacing  
  > "| C | G028.37+00.07 | 18:42:50.03 | –04:03:23.4 | 78 | 5.0 | $\sim 0.05$ | $\sim 0.1$ | | 3.5$^{\prime\prime}$$\times 3.1$$^{\prime\prime}$ | 3.5$^{\prime\prime}$$\times 3.2$$^{\prime\prime}$ | | $\sim 11$ | $\sim 9$ |" (Observations and data reduction); "$^{(a)}$ the spectral resolution of the clean cubes corresponds to twice the channel spacing ($\Delta V$);" (Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: 12m, 7m, and total power  
  > "The 12m, 7m, and total power observations were combined using the feather function in casa (version 4.7.0) with the default parameter set (i.e. effective dish size, single-dish scaling, and low-pass filtering of the single-dish observations)." (Observations and data reduction)
- configurations: _not stated_
- baselines: smallest 7m baseline of 8.9 m  
  > "The maximum recoverable scale was set by the size of the smallest 7m baseline of 8.9 m, which corresponds to $\sim 70$$^{\prime\prime}$ at 93.2 GHz." (Observations and data reduction)
- angular resolution: 3.4" x 3.0" to 4.0" x 3.1" (interferometric); ~70" (total power)  
  > "| F | G034.43+00.24 | 18:53:18.43 | +01:27:13.5 | 57 | 3.7 | $\sim 0.05$ | $\sim 0.1$ | | 3.9$^{\prime\prime}$$\times 3.1$$^{\prime\prime}$ | 4.0$^{\prime\prime}$$\times 3.1$$^{\prime\prime}$ | | $\sim 11$ | $\sim 9$ |" (Observations and data reduction); "| H | G035.39–00.33 | 18:57:09.42 | +02:08:05.4 | 43 | 2.9 | $\sim 0.05$ | $\sim 0.1$ | | 3.4$^{\prime\prime}$$\times 3.0$$^{\prime\prime}$ | 3.4$^{\prime\prime}$$\times 3.1$$^{\prime\prime}$ | | $\sim 12$ | $\sim 9$ |" (Observations and data reduction); "The half power beam width of the total power data is $\sim 70$$^{\prime\prime}$ for both N$^{15}$NH$^+$ and N$_{2}$H$^{+}$ (1–0), so that the spectra extracted from one position can contain the contribution of nearby cores." (4.1 $^{14}$N/$^{15}$N ratios in the continuum cores)
- max recoverable scale: ~70" at 93.2 GHz (7m array before TP combination)  
  > "The maximum recoverable scale was set by the size of the smallest 7m baseline of 8.9 m, which corresponds to $\sim 70$$^{\prime\prime}$ at 93.2 GHz." (Observations and data reduction)
- sensitivity: 1 sigma rms ~11-12 mJy beam^-1 (N2H+) and ~9 mJy beam^-1 (N15NH+)  
  > "| C | G028.37+00.07 | 18:42:50.03 | –04:03:23.4 | 78 | 5.0 | $\sim 0.05$ | $\sim 0.1$ | | 3.5$^{\prime\prime}$$\times 3.1$$^{\prime\prime}$ | 3.5$^{\prime\prime}$$\times 3.2$$^{\prime\prime}$ | | $\sim 11$ | $\sim 9$ |" (Observations and data reduction); "| D | G028.53–00.25 | 18:44:16.94 | –03:59:40.8 | 86 | 5.7 | $\sim 0.05$ | $\sim 0.1$ | | 3.8$^{\prime\prime}$$\times 3.0$$^{\prime\prime}$ | 3.8$^{\prime\prime}$$\times 3.1$$^{\prime\prime}$ | | $\sim 12$ | $\sim 9$ |" (Observations and data reduction)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PI: A.T. Barnes  
  > "The project IDs are 2017.1.00687.S and 2018.1.00850.S (PI: A.T. Barnes)." (Observations and data reduction)
- Line: N2H+ (1-0) (93171.88 MHz (F1=1-1), 93173.70 MHz (F1=2-1), 93176.13 MHz (F1=0-1))
- Line: N15NH+ 1-0 (91204.26 MHz (F=1-1), 91205.99 MHz (F=2-1), 91208.52 MHz (F=0-1))
- Other facility **Herschel**: Dust temperature (T_dust) and H2 column density (N(H2)^Her) maps resampled to ALMA resolution  
  > "This temperature range includes the dust temperature estimates obtained from Herschel for all clouds (see paper I), and the kinetic temperature estimates obtained in Cloud H ($\sim 10-20$ K, Sokolov et al. (cite: sokolov17))." (3.1.4 Derivation of the total column densities); "The parameters derived from the Herschel maps (i.e. $T_{\rm dust}$ and $N{\rm (H_2)}^{\rm Her}$) were obtained by resampling the Herschel maps to the higher resolution of the ALMA data via a bilinear interpolation." (4.4 Relation between $^{14}$N/$^{15}$N and core properties)
- Other facility **Spitzer**: Combined near- and mid-infrared extinction maps for mass surface density Sigma  
  > "The N$_{2}$H$^{+}$ emission morphology is shown in Fig. 2, in which we plot for each cloud the peak intensity of the N$_{2}$H$^{+}$(1–0) line superimposed on the mass (H$_2$) surface density map, $\Sigma$, obtained from combined Spitzer near- and mid-infrared extinction maps (Kainulainen & Tan (cite: ket13)):" (Results)
- External data: Spectroscopic parameters of N2H+ (1-0) from CDMS  
  > "$^{(a)}$ from the Cologne Database for Molecular Spectroscopy (CDMS; Endres et al. (cite: endres));" (Table 1) [from Endres et al. (cite: endres)]
- External data: Spectroscopic parameters of N15NH+ (1-0)  
  > "$^{(b)}$ from Dore et al. ((cite: dore09));" (Table 1) [from Dore et al. ((cite: dore09))]
- External data: Combined Spitzer near- and mid-infrared extinction mass surface density maps  
  > "superimposed on the mass (H$_2$) surface density map, $\Sigma$, obtained from combined Spitzer near- and mid-infrared extinction maps (Kainulainen & Tan (cite: ket13)):" (Results) [from Kainulainen & Tan (cite: ket13)]
- External data: Closer core identifications for naming N2H+ cores  
  > "we identify the closer core in Butler & Tan ((cite: bet12)), to which we add the label "n2hp", followed by a sequential number in case more than one core can be associated with the same Butler & Tan ((cite: bet12)) core." (3.2 Spectra towards the N$_{2}$H$^{+}$ cores) [from Butler & Tan ((cite: bet12))]
- External data: N2D+ cores associated with N2H+ cores  
  > "In Table [\[tab:columns-letters\]](#tab:columns-letters) we also list the N$_{2}$D$^{+}$ cores identified in Kong et al. ((cite: kong17)) which can be associated with the N$_{2}$H$^{+}$ cores." (3.2 Spectra towards the N$_{2}$H$^{+}$ cores) [from Kong et al. ((cite: kong17))]
- External data: Kinetic temperature estimates in Cloud H (~10-20 K)  
  > "and the kinetic temperature estimates obtained in Cloud H ($\sim 10-20$ K, Sokolov et al. (cite: sokolov17))." (3.1.4 Derivation of the total column densities) [from Sokolov et al. (cite: sokolov17)]
- External data: Galactocentric distances for the four clouds (~4.6 to ~6.3 kpc)  
  > "Assuming Galactocentric distances for the four clouds in between $\sim 4.6$ and $\sim 6.3$ kpc (Zeng et al. (cite: zeng17))," (4.1 $^{14}$N/$^{15}$N ratios in the continuum cores) [from Zeng et al. (cite: zeng17)]
- External data: Galactocentric trend of ISM 14N/15N ratio (~300-330 at 4.6-6.3 kpc)  
  > "the present-day $^{14}$N/$^{15}$N ratio of the ISM at the Galactocentric distance of the sources is $\sim 300-330$, estimated from the trend derived by Colzi et al. ((cite: colzi19), see their Eqs. 5 and 6) from HCN and HNC isotopologues." (4.1 $^{14}$N/$^{15}$N ratios in the continuum cores) [from Colzi et al. ((cite: colzi19))]
- External data: 3 mm continuum core identification, angular diameters, starless/star-forming classification, and physical properties (R_eff, M, T_dust, M_S, alpha_vir, n(H2), N(H2))  
  > "The parameter set and method for determination of the continuum dendrogram structure is described in Paper I." (Results); "In Figs. 6 and 7, we compare the $^{14}$N/$^{15}$N ratios in the 17 continuum cores detected in N$^{15}$NH$^+$ with some physical properties that were derived in paper I, namely: radius ($R_{\rm eff}$), gas mass ($M$), dust temperature ($T_{\rm dust}$, used to compute $M$), sonic Mach number ($\mathcal{M}_{\rm S}$), virial parameter ($\alpha_{\rm vir}$), H$_2$ volume density ($n{\rm (H_2)}$), and H$_2$ column density ($N{\rm (H_2)}$)." (4.4 Relation between $^{14}$N/$^{15}$N and core properties) [from Barnes et al. in prep. (paper I)]

## Processing

### Calibration

- pipeline or manual: pipeline  
  > "Calibration, imaging, and deconvolution of the interferometric data were performed with the Common Astronomy Software Calibration (casa) package (McMullin et al. (cite: mcmullin07)), using the casa-pipeline (version: 5.4.0-70)." (Observations and data reduction); "These single-dish observations were also reduced using the casa-pipeline tool (version: 5.4.0-70)." (Observations and data reduction)
- casa version: 5.4.0-70 (calibration/imaging pipeline), 4.7.0 (feather)  
  > "Calibration, imaging, and deconvolution of the interferometric data were performed with the Common Astronomy Software Calibration (casa) package (McMullin et al. (cite: mcmullin07)), using the casa-pipeline (version: 5.4.0-70)." (Observations and data reduction); "The 12m, 7m, and total power observations were combined using the feather function in casa (version 4.7.0) with the default parameter set (i.e. effective dish size, single-dish scaling, and low-pass filtering of the single-dish observations)." (Observations and data reduction)
- pipeline version: 5.4.0-70  
  > "Calibration, imaging, and deconvolution of the interferometric data were performed with the Common Astronomy Software Calibration (casa) package (McMullin et al. (cite: mcmullin07)), using the casa-pipeline (version: 5.4.0-70)." (Observations and data reduction)
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
- continuum subtraction: subtracted in the (u,v)-domain using line-free channels around the lines in each spectral window  
  > "Continuum subtraction was performed by taking the line-free channels around the lines in each individual spectral window (the results of the pipeline were checked), and subtracted from the data directly in the *(u,v)*-domain." (Observations and data reduction)
- line free channels: line-free channels around the lines in each individual spectral window (pipeline results checked)  
  > "Continuum subtraction was performed by taking the line-free channels around the lines in each individual spectral window (the results of the pipeline were checked), and subtracted from the data directly in the *(u,v)*-domain." (Observations and data reduction)
- primary beam correction: _not stated_
- array combination: 12m, 7m, and total power combined using feather in CASA 4.7.0 with default parameter set  
  > "The 12m, 7m, and total power observations were combined using the feather function in casa (version 4.7.0) with the default parameter set (i.e. effective dish size, single-dish scaling, and low-pass filtering of the single-dish observations)." (Observations and data reduction)
- smoothing: smoothed to a uniform spectral resolution of ~0.4 km s^-1  
  > "The N$_{2}$H$^{+}$(1–0) line was clearly detected with excellent signal to noise ($\geq 20$) in all clouds (see Figs. 8 – 11) after smoothing to a uniform spectral resolution of $\sim 0.4$ km s$^{-1}$." (Results)
- final beam: Cloud C: 3.5"x3.1" (N2H+), 3.5"x3.2" (N15NH+); Cloud D: 3.8"x3.0" (N2H+), 3.8"x3.1" (N15NH+); Cloud F: 3.9"x3.1" (N2H+), 4.0"x3.1" (N15NH+); Cloud H: 3.4"x3.0" (N2H+), 3.4"x3.1" (N15NH+)  
  > "| C | G028.37+00.07 | 18:42:50.03 | –04:03:23.4 | 78 | 5.0 | $\sim 0.05$ | $\sim 0.1$ | | 3.5$^{\prime\prime}$$\times 3.1$$^{\prime\prime}$ | 3.5$^{\prime\prime}$$\times 3.2$$^{\prime\prime}$ | | $\sim 11$ | $\sim 9$ |" (Observations and data reduction); "| D | G028.53–00.25 | 18:44:16.94 | –03:59:40.8 | 86 | 5.7 | $\sim 0.05$ | $\sim 0.1$ | | 3.8$^{\prime\prime}$$\times 3.0$$^{\prime\prime}$ | 3.8$^{\prime\prime}$$\times 3.1$$^{\prime\prime}$ | | $\sim 12$ | $\sim 9$ |" (Observations and data reduction); "| F | G034.43+00.24 | 18:53:18.43 | +01:27:13.5 | 57 | 3.7 | $\sim 0.05$ | $\sim 0.1$ | | 3.9$^{\prime\prime}$$\times 3.1$$^{\prime\prime}$ | 4.0$^{\prime\prime}$$\times 3.1$$^{\prime\prime}$ | | $\sim 11$ | $\sim 9$ |" (Observations and data reduction)
- final rms: ~11-12 mJy beam^-1 for N2H+; ~9 mJy beam^-1 for N15NH+  
  > "| C | G028.37+00.07 | 18:42:50.03 | –04:03:23.4 | 78 | 5.0 | $\sim 0.05$ | $\sim 0.1$ | | 3.5$^{\prime\prime}$$\times 3.1$$^{\prime\prime}$ | 3.5$^{\prime\prime}$$\times 3.2$$^{\prime\prime}$ | | $\sim 11$ | $\sim 9$ |" (Observations and data reduction); "| H | G035.39–00.33 | 18:57:09.42 | +02:08:05.4 | 43 | 2.9 | $\sim 0.05$ | $\sim 0.1$ | | 3.4$^{\prime\prime}$$\times 3.0$$^{\prime\prime}$ | 3.4$^{\prime\prime}$$\times 3.1$$^{\prime\prime}$ | | $\sim 12$ | $\sim 9$ |" (Observations and data reduction)

### Inherited from earlier work

- Complete source sample description and observational details  
  > "Observations have been performed with the Atacama Large Millimeter Array (ALMA) towards the sample of IRDCs described in Barnes et al. in prep. (hereafter paper I)." (Observations and data reduction); "We refer to that work for the complete source sample description and for any observational detail." (Observations and data reduction) [from Barnes et al. in prep. (paper I)]
- Parameter set and method for 3 mm continuum 2D dendrogram structure, core equivalent angular diameters, and starless/star-forming core classification  
  > "The parameter set and method for determination of the continuum dendrogram structure is described in Paper I." (Results); "In particular, the cores have been classified as starless or star-forming based on the identification of an infrared source inside the core boundaries (paper I)." (Results); "where $\nu$ is the rest frequency of the transition (see Table 1) and $\Theta$ is the observed angular equivalent diameter (i.e. the diameter of the equivalent circle) of each core (paper I)." (3.1.1 Extraction of the spectra and line detection) [from Barnes et al. in prep. (paper I)]
- Derivation of core physical properties (R_eff, M, T_dust, M_S, alpha_vir, n(H2), N(H2))  
  > "In Figs. 6 and 7, we compare the $^{14}$N/$^{15}$N ratios in the 17 continuum cores detected in N$^{15}$NH$^+$ with some physical properties that were derived in paper I" (4.4 Relation between $^{14}$N/$^{15}$N and core properties); "The methods used to derive each parameter are described in paper I." (4.4 Relation between $^{14}$N/$^{15}$N and core properties) [from Barnes et al. in prep. (paper I)]
- Equation (A4) for calculating total column density from integrated intensity under optically thin LTE assumptions  
  > "Then, the total column density was calculated from the total integrated intensity using Eq. (A4) of Caselli et al. ((cite: caselli02)), which assumes optically thin emission and same (and constant) excitation temperature, $T_{\rm ex}$, for all rotational transitions (and all hyperfine components within each transition)." (3.1.4 Derivation of the total column densities) [from Caselli et al. ((cite: caselli02))]
- 2D dendrogram method for structure identification  
  > "focus the $^{14}$N/$^{15}$N analysis first on the 3 mm continuum sources identified in each IRDC using the 2D dendrogram method (Rosolowsky et al. (cite: rosolowsky08))." (Results) [from Rosolowsky et al. (cite: rosolowsky08)]

### Not stated but needed to reproduce (our reading)

- Deconvolver, weighting scheme (e.g. Briggs robust parameter), cell size, image size, and cleaning mask/stopping criteria used in the CASA imaging pipeline (deferred to Barnes et al. in prep. / Paper I)
- Exact coordinates, boundary contours, and equivalent angular diameters (Theta) for all 62 3 mm continuum cores and 30 N2H+ cores (only shown graphically in Figure 1 or deferred to unpublished Paper I)
- Exact velocity integration windows used for the N2H+ (1-0) F1=0-1 component and N15NH+ (1-0) transitions in each core

## Analysis recipe

1. **Calibrate, continuum-subtract, image, and feather the ALMA 12m, 7m, and Total Power cubes**: Calibrate and image interferometric and single-dish data with the CASA pipeline, subtract continuum in the (u,v)-domain using line-free channels, and combine 12m, 7m, and total power cubes using CASA feather  
  > "Calibration, imaging, and deconvolution of the interferometric data were performed with the Common Astronomy Software Calibration (casa) package (McMullin et al. (cite: mcmullin07)), using the casa-pipeline (version: 5.4.0-70)." (Observations and data reduction); "Continuum subtraction was performed by taking the line-free channels around the lines in each individual spectral window (the results of the pipeline were checked), and subtracted from the data directly in the *(u,v)*-domain." (Observations and data reduction); "The 12m, 7m, and total power observations were combined using the feather function in casa (version 4.7.0) with the default parameter set (i.e. effective dish size, single-dish scaling, and low-pass filtering of the single-dish observations)." (Observations and data reduction)
   - software: CASA, casa-pipeline
   - parameter: feather default parameter set (effective dish size, single-dish scaling, low-pass filtering)  
  > "The 12m, 7m, and total power observations were combined using the feather function in casa (version 4.7.0) with the default parameter set (i.e. effective dish size, single-dish scaling, and low-pass filtering of the single-dish observations)." (Observations and data reduction)
   - fitting: _not stated_
   - validation: Pipeline line-free channel selection results were checked  
  > "Continuum subtraction was performed by taking the line-free channels around the lines in each individual spectral window (the results of the pipeline were checked), and subtracted from the data directly in the *(u,v)*-domain." (Observations and data reduction)
2. **Identify 3 mm continuum cores and N2H+ intensity peak cores using 2D dendrograms**: Apply 2D dendrogram analysis to 3 mm continuum maps (from Paper I) and to 2D integrated intensity maps of N2H+ (1-0)  
  > "focus the $^{14}$N/$^{15}$N analysis first on the 3 mm continuum sources identified in each IRDC using the 2D dendrogram method (Rosolowsky et al. (cite: rosolowsky08))." (Results); "These have been identified here by conducting the dendrogram analysis on the (2D) integrated intensity maps of N$_{2}$H$^{+}$ (see paper I)." (Results)
   - parameter: For N2H+ dendrogram: min_value = 30 sigma ~ 4.5 K km/s, min_delta = 30 sigma, min_pix = 3 beam ~ 150 pixels  
  > "The following set of parameters are used for determination of the dendrogram structure: min_value = 30 $\sigma$ $\sim$ 4.5 K kms (the minimum intensity considered in the analysis); min_delta = 30 $\sigma$(the minimum spacing between isocontours); min_pix = 3 beam $\sim$ 150 pixels (the minimum number of pixels contained within a structure)." (Results)
   - fitting: _not stated_
   - validation: Choice of input parameters in the continuum dendrogram analysis does not significantly affect core identification as demonstrated in Paper I  
  > "We point out that the choice of the input parameters in the dendrogram analysis does not significantly affect the identification of the cores as demonstrated in paper I." (Results)
3. **Extract spectra from core contours and convert flux density to brightness temperature**: Convert clean cubes to FITS format, extract spectra over continuum core contours, N2H+ core contours, and total power beam positions using GILDAS MAPPING, smooth to ~0.4 km/s resolution, and convert integrated flux density F_nu to brightness temperature T_B using Eq. 1  
  > "Clean cubes extracted around the lines of interest were then converted into fits format and further analysed with packages of the gildas software. In particular, the spectra of N$_{2}$H$^{+}$ and N$^{15}$NH$^+$(1–0) were extracted with mapping, and analysed in the way described in Sect. 3 with class." (Observations and data reduction); "The integrated flux density, $F_{\nu}$, of each spectrum has been converted to brightness temperature units via the formula: $$\begin{equation} T_{\rm B}(K) \simeq 1222 F_{\nu}{\rm (mJy)}/[ \nu^2{\rm (GHz)}\Theta^2 (\prime \prime)] \;, \label{eq:conversion} \end{equation}$$" (3.1.1 Extraction of the spectra and line detection)
   - software: GILDAS, MAPPING, CLASS
   - parameter: Spectral smoothing to ~0.4 km s^-1; Total power HPBW ~ 70"  
  > "The N$_{2}$H$^{+}$(1–0) line was clearly detected with excellent signal to noise ($\geq 20$) in all clouds (see Figs. 8 – 11) after smoothing to a uniform spectral resolution of $\sim 0.4$ km s$^{-1}$." (Results); "The half power beam width of the total power data is $\sim 70$$^{\prime\prime}$ for both N$^{15}$NH$^+$ and N$_{2}$H$^{+}$ (1–0), so that the spectra extracted from one position can contain the contribution of nearby cores." (4.1 $^{14}$N/$^{15}$N ratios in the continuum cores)
   - assumption: Eq. 1 is valid for non-spherical sources using equivalent circle angular diameter Theta  
  > "We stress that Eq.([\[eq:conversion\]](#eq:conversion)) is valid also for non-spherical sources as long as $\Theta$ is the source equivalent angular diameter." (3.1.1 Extraction of the spectra and line detection)
   - fitting: _not stated_
   - validation: Checked consistency of detections between continuum and N2H+ cores and examined noise levels in H3-n2hp-2 vs H3c3  
  > "Furthermore, and most importantly, the noise in the H3-n2hp-2 spectrum is about 5 times higher than that in the H3c3 one (see Fig. 3), and the hint of a possible line under the noise level is apparent in H3-n2hp-2 as well." (3.2 Spectra towards the N$_{2}$H$^{+}$ cores)
4. **Fit N15NH+ (1-0) and N2H+ (1-0) spectral lines and integrate hyperfine components**: Fit N15NH+ (1-0) with a single Gaussian to the main F=2-1 component (or simultaneous hyperfine fit using CLASS method hfs in D5c5/6/7, F1c3, F4c5, F4c7); evaluate N2H+ (1-0) isolated F1=0-1 component by comparing peak velocities with N15NH+ to distinguish multiple velocity components from self-absorption, and integrate either the strongest velocity feature or the whole F1=0-1 component  
  > "Therefore, the main components have been fitted with a single Gaussian, except in the four cores mentioned above, for which we have fitted simultaneously all components using the CLASS software (method hfs in CLASS):" (3.1.2 Line fits: N$^{15}$NH$^+$ (1–0)); "Therefore, we have estimated the N$_{2}$H$^{+}$ total column density, $N_{\rm tot}$(N$_{2}$H$^{+}$), from the integrated intensity of the hyperfine component F$_1 = 0-1$, which is well separated in velocity from the others and intrinsically the faintest one" (3.1.4 Derivation of the total column densities); "when we could determine that the profile is due to multiple velocity features, we have integrated only the strongest velocity component, (e.g. the three cores in Cloud C, or D6c4, D5c5/6 and D8c1 in cloudD, see Sect. 3.1.3); when the line profile was attributed more likely to self-absorption (e.g. in the cores D6c6, D7c1 and D7c2), we have integrated the whole component" (3.1.4 Derivation of the total column densities)
   - software: GILDAS, CLASS
   - parameter: Relative strength of N2H+ F1=0-1 component is 1/9 of total (multiply by 9); relative strength of N15NH+ F=2-1 component is 0.555 (divide by 0.555)  
  > "This was then converted to the total integrated intensity of the line by multiplying it by 9, which is the relative strength of the sum of all components with respect to the F$_1 = 0-1$ one (see Table 1)." (3.1.4 Derivation of the total column densities); "for the spectra in which the main hyperfine component only is detected, i.e. the F$=2-1$ one (see Table 1), we have estimated the total integrated intensity by dividing the integral of this component for its relative strength (i.e. $\sim 0.555$, Table 1)." (3.1.4 Derivation of the total column densities)
   - assumption: Velocity separation of hyperfine components fixed to laboratory values; all components have the same T_ex and FWHM  
  > "the method considers that the velocity separation of the components is fixed to the laboratory values, and that all components have the same excitation temperature ($T_{\rm ex}$) and the same line full width at half maximum (FWHM)." (3.1.2 Line fits: N$^{15}$NH$^+$ (1–0))
   - fitting: Single or multiple Gaussian fits and CLASS hfs hyperfine structure fits  
  > "Therefore, the main components have been fitted with a single Gaussian, except in the four cores mentioned above, for which we have fitted simultaneously all components using the CLASS software (method hfs in CLASS):" (3.1.2 Line fits: N$^{15}$NH$^+$ (1–0))
   - validation: Compared N15NH+ velocity peak with candidate velocity features in the isolated F1=0-1 component of N2H+ to distinguish multiple velocity components from self-absorption  
  > "Then, we have compared the N$^{15}$NH$^+$ line velocity peak with that of the two candidate velocity features in the isolated hyperfine component F$_1 = 0-1$ of N$_{2}$H$^{+}$(1–0):" (3.1.3 Line fits: N$_{2}$H$^{+}$(1–0))
5. **Derive total column densities N_tot(N2H+) and N_tot(N15NH+) and 14N/15N ratios**: Calculate total column densities from total integrated intensities using Eq. (A4) of Caselli et al. (2002) at T_ex = 10 K and 50 K, compute 3-sigma upper limits using Eq. 2 for non-detections, and take the ratio N_tot(N2H+)/N_tot(N15NH+)  
  > "Then, the total column density was calculated from the total integrated intensity using Eq. (A4) of Caselli et al. ((cite: caselli02)), which assumes optically thin emission and same (and constant) excitation temperature, $T_{\rm ex}$, for all rotational transitions (and all hyperfine components within each transition)." (3.1.4 Derivation of the total column densities); "Finally, in the cores undetected in N$^{15}$NH$^+$, we have evaluated the upper limit on $N_{\rm tot}$(N$^{15}$NH$^+$) from the upper limit on the integrated intensity, estimated through: $$\begin{equation} \int T_{\rm B}d{\rm v} = \frac{1}{0.555}3\sigma\frac{\sqrt{\pi}}{2\sqrt{{\rm ln2}}}{\rm FWHM}\;, \label{eq:upper} \end{equation}$$" (3.1.4 Derivation of the total column densities); "the $^{14}$N/$^{15}$N values derived from the column density ratio $N$(N$_{2}$H$^{+}$)/$N$(N$^{15}$NH$^+$) in all studied regions are in the range $\sim 80 - 400$" (Conclusions)
   - parameter: T_ex = 10 K and 50 K; 3 sigma threshold for upper limits with mean cloud FWHM  
  > "Because the adopted approach does not allow to estimate the excitation temperature, $T_{\rm ex}$, we have assumed a range of $T_{\rm ex}$ which can be considered typical or reasonable for IRDC cores, i.e. $\sim 10 -50$ K." (3.1.4 Derivation of the total column densities); "The assumed FWHM is the mean value measured from the N$^{15}$NH$^+$ lines detected in each cloud." (3.1.4 Derivation of the total column densities)
   - assumption: Optically thin emission and identical, constant excitation temperature T_ex (10 K to 50 K) for N2H+ and N15NH+ and all hyperfine components  
  > "which assumes optically thin emission and same (and constant) excitation temperature, $T_{\rm ex}$, for all rotational transitions (and all hyperfine components within each transition)." (3.1.4 Derivation of the total column densities); "The N$_{2}$H$^{+}$ and N$^{15}$NH$^+$ column densities have been calculated assuming that N$_{2}$H$^{+}$ and N$^{15}$NH$^+$ (1–0) have the same $T_{\rm ex}$ based on the assumption that the two transitions have very similar critical densities, and hence similar excitation conditions." (3.1.4 Derivation of the total column densities)
   - fitting: _not stated_
   - validation: Assessed non-LTE hyperfine excitation anomalies via Daniel et al. (2006) at core volume densities (~3.4-7.6 x 10^5 cm^-3) and evaluated optical depth correction tau/(1-exp(-tau)) ~ 1.7 for core H5c3  
  > "In our cores, the average H$_2$ volume density is $n_\mathrm{H_2} = 7.6_{-2.6}^{+5.2}\times10^5$ cm$^3$, or when using the background subtracted mass $n^\mathrm{b}_\mathrm{H_2} = 3.4_{-1.8}^{+2.4}\times10^5$ cm$^3$ (paper I), for which the predicted deviations from the equilibrium $T_{\rm ex}$ is negligible (Fig. 6 in Daniel et al. (cite: daniel06))." (3.1.4 Derivation of the total column densities); "The fit to the hyperfine structure of this line provides an optical depth of the main component $\tau \sim 8$, and hence $\tau$ of the F$_1=0-1$ component would be $\sim 0.89$ (Fig. 11). This would introduce a correction $\tau/(1-{\rm exp}(-\tau))\sim 1.7$ in the N$_{2}$H$^{+}$ column density, and hence the $^{14}$N/$^{15}$N would become $\sim 140$" (4.1 $^{14}$N/$^{15}$N ratios in the continuum cores)
6. **Compare 14N/15N ratios with star-formation activity and core physical properties**: Compare mean 14N/15N between starless and star-forming cores and perform non-parametric statistical tests and Pearson's r correlation analysis between 14N/15N and core physical parameters (R_eff, M, T_dust, M_S, alpha_vir, n(H2), N(H2))  
  > "Among the 13 detections, we find five starless and 12 star-forming cores, respectively. The average $^{14}$N/$^{15}$N ratio is slightly lower ($\sim 190$) in the starless cores than in the protostellar objects ($\sim 220$)." (4.3 Relation between $^{14}$N/$^{15}$N and star-formation activity); "However, non-parametric statistical tests suggest very tentative positive correlations with the H$_2$ column density derived from the 3 mm continuum (in Fig. 7). The Pearson’s $r$ correlation coefficient is: $r\sim 0.61$ with $N{\rm (H_2)^{Her}}$ ($p-$value 0.001); $r\sim 0.58$ with $N{\rm (H_2)^{mean}}$ ($p-$value 0.007); $r\sim 0.54$ with $N{\rm (H_2)^{peak}}$ ($p-$value 0.01)." (4.4 Relation between $^{14}$N/$^{15}$N and core properties)
   - assumption: Adopted non-background-subtracted core masses and volume densities; Herschel maps resampled to ALMA resolution via bilinear interpolation  
  > "For quantities that in paper I have been derived from background subtracted and non-subtracted data, such as the mass and the H$_2$ volume density, we have adopted the non-subtracted data." (4.4 Relation between $^{14}$N/$^{15}$N and core properties); "The parameters derived from the Herschel maps (i.e. $T_{\rm dust}$ and $N{\rm (H_2)}^{\rm Her}$) were obtained by resampling the Herschel maps to the higher resolution of the ALMA data via a bilinear interpolation." (4.4 Relation between $^{14}$N/$^{15}$N and core properties)
   - fitting: Pearson's r correlation coefficient and non-parametric statistical tests  
  > "However, non-parametric statistical tests suggest very tentative positive correlations with the H$_2$ column density derived from the 3 mm continuum (in Fig. 7). The Pearson’s $r$ correlation coefficient is: $r\sim 0.61$ with $N{\rm (H_2)^{Her}}$ ($p-$value 0.001);" (4.4 Relation between $^{14}$N/$^{15}$N and core properties)
   - validation: Noted sensitivity to outlier sources F1c1 and F1c2 and low S/N (3-5) of N15NH+ detections  
  > "However, all trends are strongly influenced by sources F1c1 and F1c2 (Figs. 6 and 7). Moreover, most N$^{15}$NH$^+$ lines are detected with a signal to noise ratio in between 3 and 5, and hence any trend that can be found from the plots in Figs. 6 and 7 must be taken with caution." (4.4 Relation between $^{14}$N/$^{15}$N and core properties)

## Software

- **CASA** 5.4.0-70, 4.7.0: Calibration, imaging, deconvolution, continuum subtraction (pipeline version 5.4.0-70), and feathering 12m, 7m, and total power data (version 4.7.0)  
  > "Calibration, imaging, and deconvolution of the interferometric data were performed with the Common Astronomy Software Calibration (casa) package (McMullin et al. (cite: mcmullin07)), using the casa-pipeline (version: 5.4.0-70)." (Observations and data reduction); "The 12m, 7m, and total power observations were combined using the feather function in casa (version 4.7.0) with the default parameter set (i.e. effective dish size, single-dish scaling, and low-pass filtering of the single-dish observations)." (Observations and data reduction)
- **casa-pipeline** 5.4.0-70: Calibration, imaging, and reduction of interferometric and single-dish total power observations  
  > "Calibration, imaging, and deconvolution of the interferometric data were performed with the Common Astronomy Software Calibration (casa) package (McMullin et al. (cite: mcmullin07)), using the casa-pipeline (version: 5.4.0-70)." (Observations and data reduction); "These single-dish observations were also reduced using the casa-pipeline tool (version: 5.4.0-70)." (Observations and data reduction)
- **GILDAS** : Further analysis of FITS clean cubes using MAPPING and CLASS packages  
  > "Clean cubes extracted around the lines of interest were then converted into fits format and further analysed with packages of the gildas software. In particular, the spectra of N$_{2}$H$^{+}$ and N$^{15}$NH$^+$(1–0) were extracted with mapping, and analysed in the way described in Sect. 3 with class." (Observations and data reduction)
- **MAPPING** : Extraction of N2H+ (1-0) and N15NH+ (1-0) spectra from clean cubes  
  > "In particular, the spectra of N$_{2}$H$^{+}$ and N$^{15}$NH$^+$(1–0) were extracted with mapping, and analysed in the way described in Sect. 3 with class." (Observations and data reduction)
- **CLASS** : Spectral line analysis and simultaneous hyperfine structure fitting (method hfs)  
  > "In particular, the spectra of N$_{2}$H$^{+}$ and N$^{15}$NH$^+$(1–0) were extracted with mapping, and analysed in the way described in Sect. 3 with class." (Observations and data reduction); "for which we have fitted simultaneously all components using the CLASS software (method hfs in CLASS):" (3.1.2 Line fits: N$^{15}$NH$^+$ (1–0))

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of 3 mm continuum cores detected in N15NH+ (1-0) | 17 out of 62 | not stated | dimensionless | 3 | among the 3 mm continuum cores embedded in each IRDC and identified in paper I, we detect 17 out of 62 cores in N$^{15}$NH$^+$; |
| N15NH+ (1-0) detection fraction in continuum cores by cloud | Cloud C: 3 (~19%), Cloud D: 6 (~38%), Cloud F: 6 (~30%), Cloud H: 2 (~20%) | not stated | dimensionless | 3 | We extracted N$^{15}$NH$^+$(1–0) spectra from the continuum sources identified in paper I, and detected significant emission towards three cores in Cloud C ($\sim 19\%$), six cores in Cloud D ($\sim 38\%$), six cores in Cloud F ($\sim 30\%$), and two cores in Cloud H ($\sim 20\%$). |
| N_tot(N2H+) in 3 mm continuum cores (T_ex = 10 K) | 0.8 - 14 x 10^13 | not stated | cm^-2 | 5 | The corresponding range of values for $N_{\rm tot}$(N$_{2}$H$^{+}$) is $\sim 0.8 - 14 \times 10^{13}$ cm$^{-2}$ at $T_{\rm ex}$= 10 K, and $\sim 2.4 - 41 \times 10^{14}$ cm$^{-2}$ at $T_{\rm ex}$= 50 K. |
| N_tot(N15NH+) in 3 mm continuum cores (T_ex = 10 K) | 1.3 - 7 x 10^11 | not stated | cm^-2 | 5 | We find $N_{\rm tot}$(N$^{15}$NH$^+$) in the range $\sim 1.3 - 7 \times 10^{11}$ cm$^{-2}$ at $T_{\rm ex}$= 10 K, and $\sim 4-19 \times 10^{11}$ cm$^{-2}$ at $T_{\rm ex}$= 50 K. |
| N_tot(N15NH+) in 3 mm continuum cores (T_ex = 50 K) | 4 - 19 x 10^11 | not stated | cm^-2 | 5 | We find $N_{\rm tot}$(N$^{15}$NH$^+$) in the range $\sim 1.3 - 7 \times 10^{11}$ cm$^{-2}$ at $T_{\rm ex}$= 10 K, and $\sim 4-19 \times 10^{11}$ cm$^{-2}$ at $T_{\rm ex}$= 50 K. |
| 14N/15N ratio range in 3 mm continuum cores | 80 - 400 | not stated | dimensionless | 5 | The $^{14}$N/$^{15}$N values measured towards the millimeter continuum cores range from a minimum of $\sim 80$ up to a maximum of $\sim 400$.; Their ratios, $^{14}$N/$^{15}$N (shown in Table 2), are in between $\sim 80$ and $\sim 400$, with little statistically significant differences among the clouds: |
| Average 14N/15N ratio across all detected continuum cores | 210 | not stated | dimensionless | 5 | The average $^{14}$N/$^{15}$N ratio of $\sim 210$ is also lower than the interstellar value at the Galactocentric distance of the clouds ($\sim 300-330$); (2) an average $^{14}$N/$^{15}$N of $\sim 210$, very similar to the terrestrial one (Marty et al. (cite: marty09)). |
| Average 14N/15N ratio in Cloud C continuum cores | 230 | 50 | dimensionless | 5 | the average $^{14}$N/$^{15}$N is $230\pm 50$ for Cloud C, $180\pm 100$ for Cloud D, 260$\pm 100$ for Cloud F, and 120$\pm 40$ for Cloud H. |
| Average 14N/15N ratio in Cloud D continuum cores | 180 | 100 | dimensionless | 5 | the average $^{14}$N/$^{15}$N is $230\pm 50$ for Cloud C, $180\pm 100$ for Cloud D, 260$\pm 100$ for Cloud F, and 120$\pm 40$ for Cloud H. |
| Average 14N/15N ratio in Cloud F continuum cores | 260 | 100 | dimensionless | 5 | the average $^{14}$N/$^{15}$N is $230\pm 50$ for Cloud C, $180\pm 100$ for Cloud D, 260$\pm 100$ for Cloud F, and 120$\pm 40$ for Cloud H. |
| Average 14N/15N ratio in Cloud H continuum cores | 120 | 40 | dimensionless | 5 | the average $^{14}$N/$^{15}$N is $230\pm 50$ for Cloud C, $180\pm 100$ for Cloud D, 260$\pm 100$ for Cloud F, and 120$\pm 40$ for Cloud H. |
| 14N/15N ratio in continuum core C2c3/5 | 240 | 100 | dimensionless | 5 | / C2c3/5 / 37.6(0.3) / 5.1(0.6) / 14.8(1.6) / / 0.15(0.03) / 2.1(0.7) / 6(2) / $240 \pm 100$ / 6 / |
| 14N/15N ratio in continuum core C2c4 | 260 | 120 | dimensionless | 5 | / C2c4 / 46.7(0.3) / 6.3(0.7) / 18(2) / / 0.17(0.05) / 2.4(0.9) / 7(3) / $260 \pm 120$ / 7 / |
| 14N/15N ratio in continuum core C2c6 | 180 | 80 | dimensionless | 5 | / C2c6 / 34.8(0.2) / 4.7(0.5) / 13.7(1.5) / / 0.19(0.04) / 2.6(0.9) / 8(3) / $180 \pm 80$ / 8 / |
| 14N/15N ratio in continuum core D6c4 | 120 | 70 | dimensionless | 5 | / D6c4 / 18.8(0.3) / 2.5(0.3) / 7.4(0.9) / / 0.15(0.05) / 2.0(0.9) / 6(3) / $120 \pm 70$ / 4 / |
| 14N/15N ratio in continuum core D6c6 | 230 | 160 | dimensionless | 5 | / D6c6 / 24.0(0.5) / 3.2(0.4) / 9.5(1.1) / / 0.10(0.05) / 1.4(0.8) / 4(2) / $230 \pm 160$ / 7 / |
| 14N/15N ratio in continuum core D7c1 | 170 | 90 | dimensionless | 5 | / D7c1 / 21.2(0.2) / 2.9(0.3) / 8.4(0.9) / / 0.12(0.04) / 1.7(0.7) / 5(2) / $170 \pm 90$ / 8 / |
| 14N/15N ratio in continuum core D7c2 | 130 | 70 | dimensionless | 5 | / D7c2 / 21.6(0.2) / 2.9(0.3) / 8.5(0.9) / / 0.16(0.05) / 2.2(0.9) / 6(3) / $130 \pm 70$ / 9 / |
| 14N/15N ratio in continuum core D5c5/6 | 170 | 100 | dimensionless | 5 | / D5c5/6 / 16.6(0.1) / 2.2(0.2) / 6.5(0.7) / / 0.09(0.04) / 1.3(0.7) / 4(2) / $170 \pm 100$ / 11 / |
| 14N/15N ratio in continuum core D8c1 | 280 | 120 | dimensionless | 5 | / D8c1 / 28.9(0.1) / 3.9(0.4) / 11.4(1.2) / / 0.10(0.02) / 1.4(0.4) / 4.0(1.3) / $280 \pm 120$ / 13 / |
| 14N/15N ratio in continuum core F1c1 | 390 | 130 | dimensionless | 5 | / F1c1 / 104.2(0.3) / 14.0(1.4) / 41(4) / / 0.26(0.03) / 3.6(0.8) / 11(2) / $390 \pm 130$ / 1 / |
| 14N/15N ratio in continuum core F1c2 | 400 | 190 | dimensionless | 5 | / F1c2 / 89.6(0.5) / 12.1(1.3) / 35(4) / / 0.21(0.06) / 3.0(1.1) / 9(3) / $400 \pm 190$ / 2 / |
| 14N/15N ratio in continuum core F1c3 | 150 | 60 | dimensionless | 5 | / F1c3 / 74.7(0.5) / 10.1(1.1) / 29(3) / / 0.47(0.09) / 7(2) / 19(6) / $150 \pm 60$ / 3 / |
| 14N/15N ratio in continuum core F1c4 | 270 | 140 | dimensionless | 5 | / F1c4 / 39.8(0.2) / 5.4(0.6) / 15.7(1.6) / / 0.14(0.04) / 2.0(0.8) / 6(2) / $270 \pm 140$ / 4 / |
| 14N/15N ratio in continuum core F4c5 | 175 | 90 | dimensionless | 5 | / F4c5 / 25.8(0.2) / 3.5(0.4) / 10.2(1.1) / / 0.14(0.05) / 2.0(0.8) / 6(2) / $175 \pm 90$ / 12 / |
| 14N/15N ratio in continuum core F4c7 | 190 | 90 | dimensionless | 5 | / F4c7 / 52.8(0.3) / 7.1(0.8) / 21(2) / / 0.27(0.7) / 3.8(1.4) / 11(4) / $190 \pm 90$ / 14 / |
| 14N/15N ratio in continuum core H3c3 | 160 | 70 | dimensionless | 5 | / H3c3 / 20.7(0.3) / 2.8(0.3) / 8.1(0.9) / / 0.12(0.03) / 1.7(0.6) / 5.1(1.8) / $160 \pm 70$ / 4 / |
| 14N/15N ratio in continuum core H5c3 | 80 | 30 | dimensionless | 5 | / H5c3 / 26.1(0.2) / 3.5(0.4) / 10.3(1.1) / / 0.31(0.06) / 4.3(1.3) / 13(4) / $80 \pm 30$ / 9 / |
| 14N/15N ratio in total power data towards C2c4, D6c4, D8c1, F1c1, F4c7, H3c3, H5c3 | C2c4: 500(150), D6c4: 370(100), D8c1: 330(100), F1c1: 420(130), F4c7: 390(140), H3c3: 290(100), H5c3: 280(100) | see values | dimensionless | 5 | / C2c4 / 34.5(0.2) / 4.2(0.4) / 12.2(1.3) / / 0.33(0.03) / 8.3(1.6) / 24(5) / 500(150) /; / D6c4 / 26.7(0.2) / 3.2(0.3) / 9.5(1.0) / / 0.35(0.03) / 8.8(1.6) / 26(5) / 370(100) /; / H5c3 / 14.0(0.2) / 1.7(0.2) / 5.0(0.6) / / 0.24(0.04) / 6.0(1.6) / 18(5) / 280(100) / |
| 14N/15N ratio range in N2H+ cores | 130 - 390 | not stated | dimensionless | 5 | the range of $^{14}$N/$^{15}$N is $\sim 130 - 390$, consistent with the one found in the continuum cores (compare Fig. 4 and Fig. 5). |
| Average 14N/15N ratio in starless vs star-forming continuum cores | starless: ~190, star-forming: ~220 | not stated | dimensionless | 6 | The average $^{14}$N/$^{15}$N ratio is slightly lower ($\sim 190$) in the starless cores than in the protostellar objects ($\sim 220$). |
| Pearson's r correlation coefficient between 14N/15N and H2 column densities | r ~ 0.61 (p=0.001) with N(H2)^Her; r ~ 0.58 (p=0.007) with N(H2)^mean; r ~ 0.54 (p=0.01) with N(H2)^peak | not stated | dimensionless | 6 | The Pearson’s $r$ correlation coefficient is: $r\sim 0.61$ with $N{\rm (H_2)^{Her}}$ ($p-$value 0.001); $r\sim 0.58$ with $N{\rm (H_2)^{mean}}$ ($p-$value 0.007); $r\sim 0.54$ with $N{\rm (H_2)^{peak}}$ ($p-$value 0.01). |
| Pearson's r correlation coefficient between 14N/15N and sonic Mach number M_S and T_dust in star-forming cores | r ~ 0.76 (p=0.004) with M_S; r ~ 0.6 (p=0.04) with T_dust | not stated | dimensionless | 6 | If we analyse only the star-forming cores, however, we find a tentative positive correlation between $^{14}$N/$^{15}$N and the sonic Mach number $\mathcal{M}_{\rm S}$ ($r\sim 0.76$, $p-$value 0.004).; A very tentative one can be also found between $^{14}$N/$^{15}$N and $T_{\rm dust}$ ($r\sim 0.6$, $p-$value 0.04). |

## Qualitative findings

- N15NH+ (1-0) emission is preferentially detected towards cores with strong 3 mm continuum emission, typically located in the central parts of the clouds (except in Cloud F).  
  > "The N$^{15}$NH$^+$ emission is preferentially detected towards cores with strong continuum emission (cores C2c3/5, C2c4, C2c6 in Cloud C; core D7c3 in Cloud D; Cores F1c1, F1c2, F1c3, F4c5, F4c7 in Cloud F; cores H3c3 and H5c3 in Cloud H), and are usually located in the central part of the cloud, with the exception of the cores in Cloud F, located at the southern and northern edge of the cloud (Fig. 1)." (3.1.1 Extraction of the spectra and line detection)
- The 14N/15N ratio in compact dense continuum cores is lower on average (~210) and spans a narrower range (~80-400) than in single-dish surveys or the ALMA total power data alone, indicating that 14N/15N is higher in the diffuse surrounding envelopes due to selective photodissociation.  
  > "The spread of values is narrower than that found in any previous single-dish survey of high-mass star-forming regions, and than that obtained using the total power data only. This suggests that the $^{14}$N/$^{15}$N ratio is on average higher in the diffuse gaseous envelope of the cores" (Abstract); "In all cores except F1c1, which is the most extended one, the beam-averaged $^{14}$N/$^{15}$N ratios are larger by a factor $\sim 1.5 - 3$ than those obtained in the embedded cores at higher angular resolution." (4.1 $^{14}$N/$^{15}$N ratios in the continuum cores)
- Evolutionary stage (starless vs star-forming classification) does not play a significant role in nitrogen fractionation of N2H+.  
  > "However, given the large dispersions, we confirm overall the result suggested by previous works (Fontani et al. (cite: fontani15), Zeng et al. (cite: zeng17), Colzi et al. (cite: colzi18a), (cite: colzi18b)): time does not seem to play a role in the enrichment, or depletion, of $^{15}$N in N$_{2}$H$^{+}$." (4.3 Relation between $^{14}$N/$^{15}$N and star-formation activity)
- There are no strong correlations between 14N/15N and core physical properties, consistent with gas-phase chemical models (Roueff et al. 2015; Loison et al. 2019), aside from tentative positive trends with H2 column density and (in star-forming cores) sonic Mach number and dust temperature.  
  > "Overall, the fact that we find either no or little correlation between $^{14}$N/$^{15}$N and core properties confirm the chemical models of Roueff et al. ((cite: roueff15)) and Loison et al. ((cite: loison19)), in which enrichment in $^{15}$N is always very low or even negligible for all species formed in the gas phase like N$_{2}$H$^{+}$." (4.4 Relation between $^{14}$N/$^{15}$N and core properties)

## Claim tuples

- H: The 14N/15N ratio in N2H+ is lower in dense embedded IRDC cores than in their surrounding diffuse gaseous envelopes, as expected from selective photodissociation. | E: Measured N2H+ (1-0) and N15NH+ (1-0) column densities and 14N/15N ratios in compact 3 mm continuum cores using feathered 12m+7m+TP ALMA cubes (~3-4" resolution) and compared them to values derived from more extended N2H+ cores, ALMA Total Power data alone (~70" resolution), and prior single-dish surveys. | R: In continuum cores, 14N/15N ranges from ~80 to ~400 (mean ~210), whereas Total Power data towards the same cores yield ratios a factor ~1.5-3 higher (280-500), and extended N2H+ cores have ratios similar to or up to ~1.5-2 times higher than embedded continuum cores (except F1-n2hp-1). | F: The 14N/15N ratio tends to be higher in the diffuse envelope than in dense embedded cores, consistent with selective photodissociation by external UV photons, although sensitivity limits preclude detecting ratios >400 at small scales. | **partially**
- H: Nitrogen fractionation in N2H+ varies with the evolutionary stage (starless vs star-forming) of IRDC cores. | E: Compared the 14N/15N ratios measured in 5 starless and 12 star-forming 3 mm continuum cores classified via embedded infrared emission. | R: The average 14N/15N ratio is ~190 in starless cores and ~220 in star-forming cores, with large dispersions. | F: Evolutionary stage (time) does not play a significant role in the enrichment or depletion of 15N in N2H+. | **refuted**
- H: The 14N/15N ratio in IRDC cores correlates with core physical properties (radius, mass, dust temperature, sonic Mach number, virial parameter, volume density, and H2 column density). | E: Performed non-parametric statistical tests and Pearson's r correlation analysis between 14N/15N and core physical parameters derived in Paper I for the 17 detected continuum cores. | R: No strong correlations were found overall; tentative positive correlations were found with H2 column density (r ~ 0.54-0.61, p = 0.001-0.01) and, among star-forming cores only, with sonic Mach number (r ~ 0.76, p = 0.004) and dust temperature (r ~ 0.6, p = 0.04), heavily influenced by F1c1 and F1c2. | F: Little or no correlation exists between 14N/15N and core properties, confirming gas-phase chemical models predicting negligible 15N enrichment at T > 10 K, while tentative positive trends with column density, Mach number, and temperature may reflect selective photodissociation. | **partially**

## Reasoning

- Why this data: Previous single-dish surveys provided average 14N/15N values over ~0.1-1 pc scales that mix gas with different physical and chemical conditions; high-angular resolution interferometric observations with ALMA towards well-studied IRDCs are needed to resolve dense cores (<= 0.1 pc) and relate 14N/15N to core properties and star-formation activity.  
  > "However, the observations mentioned above were obtained with single-dish telescopes, thus providing average values of the $^{14}$N/$^{15}$N ratio on linear scales of $\sim 0.1 - 1$ pc, which can contain gas with different conditions, due to the inner physical and chemical complexity of high-mass star-forming cores." (Introduction); "The $^{14}$N/$^{15}$N ratio is derived from observations of N$_{2}$H$^{+}$ and N$^{15}$NH$^+$ (1–0) towards the dense cores of four clouds in which the physical and chemical structure has already been extensively studied at various wavelengths" (Introduction)
- Why this method: Used 2D dendrogram contours on 3 mm continuum and N2H+ integrated intensity maps to focus on dense cores and N2H+ peaks given the faintness of N15NH+ and morphological complexity; integrated the isolated and weakest F1=0-1 hyperfine component of N2H+ (1-0) to minimize optical depth, self-absorption, and multiple velocity component blending.  
  > "The faintness of the N$^{15}$NH$^+$ emission, and the large angular extension and morphological complexity of the target clouds, suggested us to focus the $^{14}$N/$^{15}$N analysis first on the 3 mm continuum sources identified in each IRDC using the 2D dendrogram method (Rosolowsky et al. (cite: rosolowsky08))." (Results); "Therefore, we have estimated the N$_{2}$H$^{+}$ total column density, $N_{\rm tot}$(N$_{2}$H$^{+}$), from the integrated intensity of the hyperfine component F$_1 = 0-1$, which is well separated in velocity from the others and intrinsically the faintest one, and hence potentially the least affected by optical depth effects, self-absorption, or contribution of secondary faint velocity features." (3.1.4 Derivation of the total column densities)
- Alternative: Showing integrated intensity maps of N15NH+ (1-0) was rejected due to the faintness of the N15NH+ lines.  
  > "Due to the faintness of the N$^{15}$NH$^+$ lines, we do not show integrated maps of the N$^{15}$NH$^+$ emission." (Results)
- Alternative: Fitting the full hyperfine structure of N15NH+ (1-0) was rejected in all but four cores because the satellite components were undetected.  
  > "In all but four cores, D5c5/6/7, F1C3, F4c5, and F4c7, the hyperfine structure cannot be fitted because the satellites are undetected. Therefore, the main components have been fitted with a single Gaussian" (3.1.2 Line fits: N$^{15}$NH$^+$ (1–0))
- Alternative: Deriving N2H+ column densities from full hyperfine structure fits was rejected because complex line profiles (multiple velocity components, self-absorption, and optical depth) yielded high fit residuals.  
  > "The complexity of the N$_{2}$H$^{+}$(1–0) line profiles, clearly seen in the spectra of Figs. 8 – 11, and described in Sect. 3.1.3, makes it difficult to obtain fits with low residuals. Therefore, we have estimated the N$_{2}$H$^{+}$ total column density, $N_{\rm tot}$(N$_{2}$H$^{+}$), from the integrated intensity of the hyperfine component F$_1 = 0-1$" (3.1.4 Derivation of the total column densities)
- How they decided it was enough: _not stated_
- Limitation (authors): Sensitivity of the ALMA observations does not allow detection of N15NH+ in cores with 14N/15N higher than ~400, so it is uncertain whether the narrower range of 14N/15N compared to single-dish studies is partly due to limited sensitivity.  
  > "This means that our interferometric observations are not sensitive to N$^{15}$NH$^+$ emission in cores with $^{14}$N/$^{15}$N higher than $\sim 400$, and hence we cannot conclude if the narrower range of isotopic ratios measured in this work depends also on our limited sensitivity." (4.1 $^{14}$N/$^{15}$N ratios in the continuum cores)
- Limitation (authors): Non-negligible optical depth or self-absorption in the F1=0-1 component of N2H+ (1-0) can lead to underestimating N_tot(N2H+) and the 14N/15N ratio (e.g., in D6c6, D7c1, D7c2, and H5c3).  
  > "when the line profile was attributed more likely to self-absorption (e.g. in the cores D6c6, D7c1 and D7c2), we have integrated the whole component, bearing in mind that this will provide a lower limit on $N_{\rm tot}$(N$_{2}$H$^{+}$), and hence a lower limit on the associated $^{14}$N/$^{15}$N as well." (3.1.4 Derivation of the total column densities); "Another caveat on the $^{14}$N/$^{15}$N ratios arises from the possible non negligible optical depth of the F$_1=0-1$ component of N$_{2}$H$^{+}$(1–0), which could lead us to underestimate $N_{\rm tot}$(N$_{2}$H$^{+}$) and, from this, the $^{14}$N/$^{15}$N ratio." (4.1 $^{14}$N/$^{15}$N ratios in the continuum cores)
- Limitation (authors): Low number of N2H+ cores associated with N2D+ cores and detected in N15NH+ (only 4) prevents statistical analysis of the relation between nitrogen and deuterium fractionation.  
  > "A few of them are indeed associated, but unfortunately only 4 of those are also detected in N$^{15}$NH$^+$, and thus the statistics is too low to discuss possible relations between nitrogen and deuterium fractionation." (3.2 Spectra towards the N$_{2}$H$^{+}$ cores)
- Limitation (authors): Starless cores may not be truly pre-stellar or may contain unresolved star-forming fragments undetected in IR images.  
  > "In fact, first the nature of our starless cores could not be "pre–stellar" but just starless or star-forming in a very early stage of star-formation activity; second, some cores are extended and could contain smaller fragments in different evolutionary stages." (4.3 Relation between $^{14}$N/$^{15}$N and star-formation activity)
- Limitation (authors): Tentative correlations with core properties are strongly influenced by two sources (F1c1 and F1c2), rely on low S/N (3-5 sigma) N15NH+ detections, and use Herschel dust temperatures measured at coarser angular resolution than the individual cores.  
  > "However, all trends are strongly influenced by sources F1c1 and F1c2 (Figs. 6 and 7). Moreover, most N$^{15}$NH$^+$ lines are detected with a signal to noise ratio in between 3 and 5, and hence any trend that can be found from the plots in Figs. 6 and 7 must be taken with caution." (4.4 Relation between $^{14}$N/$^{15}$N and core properties); "However, the temperature of our cores at the scales studied by us is always above $\sim 10$ K, in agreement with the lack of $^{15}$N enrichment, although the temperature measurement is taken over an angular scale (i.e. the Herschel beam) larger than that of the individual cores." (4.4 Relation between $^{14}$N/$^{15}$N and core properties)
- Caveat (inferred, ours): Dependence on an unpublished companion paper (Barnes et al. in prep., Paper I) for core coordinates, angular sizes, continuum dendrogram parameters, and core physical properties makes standalone verification of the extracted spectra and correlation plots impossible without external data.
- Caveat (inferred, ours): Assuming optically thin emission for the F1=0-1 hyperfine component of N2H+ (1-0) in high-column-density IRDC cores systematically biases N_tot(N2H+) and 14N/15N downward when tau(F1=0-1) is moderate to high, as demonstrated by the factor of ~1.7 correction in H5c3.

## Reproducibility

- Data public (paper): Data will be shared on reasonable request to the corresponding author; ALMA project IDs 2017.1.00687.S and 2018.1.00850.S are stated.  
  > "Data used within this work will be shared on reasonable request to the corresponding author." (Data availability); "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00687.S & ADS/JAO.ALMA#2018.1.00850.S." (Conclusions)
- Products in archive: _not stated_
- Missing: Exact pixel/sky masks or polygon contours and equivalent diameters (Theta) for the 62 3 mm continuum cores and 30 N2H+ dendrogram cores (deferred to Barnes et al. in prep.)
- Missing: Imaging parameters used in the CASA pipeline (weighting/robust, cell size, image size, cleaning threshold/masking, deferred to Barnes et al. in prep.)
- Missing: Exact velocity intervals over which the N2H+ F1=0-1 component and N15NH+ lines were integrated for each core
- Data volume (inferred): ~50-200 GB (12m, 7m, and Total Power spectral line cubes and visibilities across 4 IRDC mosaics from two ALMA projects)
- Score (inferred): 5/5, The ALMA project codes, CASA pipeline/feather versions, spectroscopic constants, column density equations, and per-core integrated intensities and column densities are thoroughly tabulated. However, critical observational and imaging parameters and the exact 3 mm continuum core definitions/apertures (Theta and contours) are deferred to an unpublished companion paper (Barnes et al. in prep.).
- Rediscovery candidate: yes, Raw and pipeline-reduced ALMA data for 2017.1.00687.S and 2018.1.00850.S are public in the ALMA archive, the spectral line analysis recipe (feathering, dendrogram extraction, F1=0-1 and F=2-1 integration, LTE column density ratios) is clearly specified, and the main results are numeric tables of integrated intensities, column densities, and 14N/15N ratios.

## Links

- Method: Rosolowsky et al. (cite: rosolowsky08) (2D dendrogram method used to identify 3 mm continuum and N2H+ cores)
- Method: Caselli et al. ((cite: caselli02)) (Equation (A4) used to compute total column densities from integrated line intensities under optically thin LTE assumptions)
- Companion: Barnes et al. in prep. (paper I) (ALMA-IRDC Paper I providing the complete source sample description, observational and imaging details, 3 mm continuum dendrogram core catalog, starless/star-forming classification, and core physical properties)
- Related: ALMA-IRDC

## Checks

```json
{
 "quotes": 180,
 "quotes_ok": 180,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 31,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 33,
 "numeric_problems": 0,
 "fill": {
  "facts": 112,
  "stated": 85,
  "rate": 0.759
 },
 "evidence_ok": true
}
```

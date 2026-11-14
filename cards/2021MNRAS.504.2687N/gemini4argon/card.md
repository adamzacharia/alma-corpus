# Morpho-kinematics of the circumstellar envelope of the AGB star R Dor: a global view

`2021MNRAS.504.2687N` | Monthly Notices of the Royal Astronomical Society 2021 | first author: Nhung, P. T. | arXiv: 2101.05455 | DOI: 10.1093/mnras/stab954

Card schema 1.0 | model gemini-4-argon | depth full | type archival_reuse

## Science

- Fields: evolved_stars, astrochemistry
- Question: Characterise the global morpho-kinematics (rotation, expansion, turbulence, absorption, south-eastern blue-shifted stream, and broad outflows) of the circumstellar envelope of the oxygen-rich AGB star R Dor from the stellar surface up to ~100 au.  
  > "We analyse new ALMA observations of the $^{29}$SiO ($\nu$=0, $J$=8$-$7) and SO$_2$($\nu$=0, $34_{3,31}$$-$$34_{2,32}$) line emissions of the circumstellar envelope (CSE) of the oxygen-rich AGB star R Dor." (Abstract); "With a spatial resolution of $\sim$2.3 au, they cover distances below $\sim$30 au from the star providing a link between earlier observations and clarifying some open issues." (Abstract)
- Target **R Dor**: coordinates _not stated_; z/distance ~59 pc; systemic velocity 7 km s^-1  
  > "it is close to the Sun, at a distance of only $\sim$59 pc (cite: Knapp2003)" (Introduction); "The systemic velocity of R Dor (7 km s$^{-1}$) is taken as origin." (Observations and data reduction); distance from (cite: Knapp2003)  
  > "it is close to the Sun, at a distance of only $\sim$59 pc (cite: Knapp2003)" (Introduction); "The systemic velocity of R Dor (7 km s$^{-1}$) is taken as origin." (Observations and data reduction)

## Data provenance

- ALMA projects: 2017.1.00191.S, 2013.1.00166.S, 2017.1.00824.S
- bands: Band 7 (2017.1.00191.S, 2013.1.00166.S); Band 6 (2017.1.00824.S)  
  > "The data are retrieved from ALMA archives, project 2017.1.00191.S, observed in November 2017 in band 7 with antennas in the C43-9 configuration." (Observations and data reduction); "They are from project 2013.1.00166.S observed in summer 2015 in band 7 with an average of 35 antennas in the C34-7 configuration." (Observations and data reduction); "These are from project 2017.1.00824.S observed in December 2017 in band 6 with an average of 45 antennas." (Overall picture of the morpho-kinematics as seen from SO emission)
- frequencies and spectral setup: 81 channels covering 69 km s^-1 with 0.854 km s^-1 bins (for 29SiO at 342.98 GHz and SO2 at 342.76 GHz); 28SiO at 347.3 GHz, CO at 345.8 GHz, HCN at 354.5 GHz, SO at 251.8 GHz  
  > "We select a frequency interval of 81 channels corresponding to a Doppler velocity interval of 69 km s$^{-1}$, each Doppler velocity bin being 0.854 km s$^{-1}$ wide." (Observations and data reduction); "$^{29}$SiO | $\nu$=0, $J$=8$-$7 | 342.98084800 | 74.08" (Table 1); "$^{28}$SiO II | 347.3 | 220$\times$170 | 80 | 38 | 18 | Aug 2015 | 21 mn" (Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: 12m array (44-45 antennas for 2017.1.00191.S; average 35 antennas for 2013.1.00166.S; average 45 antennas for 2017.1.00824.S)  
  > "The observations were made in two blocks using 44 and respectively 45 antennas." (Observations and data reduction); "They are from project 2013.1.00166.S observed in summer 2015 in band 7 with an average of 35 antennas in the C34-7 configuration." (Observations and data reduction); "These are from project 2017.1.00824.S observed in December 2017 in band 6 with an average of 45 antennas." (Overall picture of the morpho-kinematics as seen from SO emission)
- configurations: C43-9 (2017.1.00191.S); C34-7 (2013.1.00166.S)  
  > "The data are retrieved from ALMA archives, project 2017.1.00191.S, observed in November 2017 in band 7 with antennas in the C43-9 configuration." (Observations and data reduction); "They are from project 2013.1.00166.S observed in summer 2015 in band 7 with an average of 35 antennas in the C34-7 configuration." (Observations and data reduction)
- baselines: 100 m to 12 km, effective minimal baseline 300 m (2017.1.00191.S)  
  > "Baselines span between 100 m and 12 km (Figure 2) and the maximal recoverable scale, evaluated for a wavelength of 0.87 mm and an effective minimal baseline of 300 m, is 0.36 arcsec." (Observations and data reduction)
- angular resolution: ~2.3 au (34x25 mas^2 in CASA, 41x35 mas^2 in GILDAS for 29SiO/SO2); 220x170 mas^2 (28SiO II), 180x140 mas^2 (CO), 157x145 mas^2 (HCN), 154x147 mas^2 / 9 au (SO)  
  > "With a spatial resolution of $\sim$2.3 au, they cover distances below $\sim$30 au from the star providing a link between earlier observations and clarifying some open issues." (Abstract); "The beams obtained with CASA and GILDAS (FWHM) were 34$\times$25 mas$^2$ and 41$\times$35 mas$^2$ respectively." (Observations and data reduction); "$^{28}$SiO II | 347.3 | 220$\times$170 | 80 | 38 | 18 | Aug 2015 | 21 mn" (Observations and data reduction)
- max recoverable scale: 0.36 arcsec (2017.1.00191.S); 80 au (28SiO II, CO), 78 au (HCN), 136 au (SO)  
  > "Baselines span between 100 m and 12 km (Figure 2) and the maximal recoverable scale, evaluated for a wavelength of 0.87 mm and an effective minimal baseline of 300 m, is 0.36 arcsec." (Observations and data reduction); "$^{28}$SiO II | 347.3 | 220$\times$170 | 80 | 38 | 18 | Aug 2015 | 21 mn" (Observations and data reduction); "SO | 251.8 | 154$\times$147 | 136 | 45 | 1.2 | Dec 2017 | 2.7 hr" (Observations and data reduction)
- sensitivity: 1.4 mJy beam^-1 (29SiO), 1.1 mJy beam^-1 (SO2), 18 mJy beam^-1 (28SiO II), 14 mJy beam^-1 (CO), 8 mJy beam^-1 (HCN), 1.2 mJy beam^-1 (SO)  
  > "Brightness distributions (Figure 2) show a noise level (1$\sigma$) of 1.4 mJy beam$^{-1}$ for $^{29}$SiO and 1.1 mJy beam$^{-1}$ for SO$_2$." (Observations and data reduction); "$^{28}$SiO II | 347.3 | 220$\times$170 | 80 | 38 | 18 | Aug 2015 | 21 mn" (Observations and data reduction); "SO | 251.8 | 154$\times$147 | 136 | 45 | 1.2 | Dec 2017 | 2.7 hr" (Observations and data reduction)
- time on source: 90 min (2 blocks of 45 min for 29SiO/SO2); 21 min (28SiO II, CO), 26 min (HCN), 2.7 hr (SO)  
  > "The total time on source was 90 min, 45 min for each block." (Observations and data reduction); "HCN | 354.5 | 157$\times$145 | 78 | 34 | 8 | Aug 2015 | 26 mn" (Observations and data reduction); "SO | 251.8 | 154$\times$147 | 136 | 45 | 1.2 | Dec 2017 | 2.7 hr" (Observations and data reduction)
- observing dates: November 2017 (2017.1.00191.S); August 2015 (28SiO II, HCN), September 2015 (CO); December 2017 (SO)  
  > "The data are retrieved from ALMA archives, project 2017.1.00191.S, observed in November 2017 in band 7 with antennas in the C43-9 configuration." (Observations and data reduction); "CO | 345.8 | 180$\times$140 | 80 | 32 | 14 | Sep 2015 | 21 mn" (Observations and data reduction); "SO | 251.8 | 154$\times$147 | 136 | 45 | 1.2 | Dec 2017 | 2.7 hr" (Observations and data reduction)
- pi or archival as stated: Archival data; PIs: Theo Khouri (2017.1.00191.S), Leen Decin (2017.1.00824.S and 2013.1.00166.S)  
  > "The data are retrieved from ALMA archives, project 2017.1.00191.S, observed in November 2017 in band 7 with antennas in the C43-9 configuration." (Observations and data reduction); "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00191.S (PI: Theo Khouri), ADS/JAO.ALMA#2017.1.00824.S (PI: Leen Decin) and ADS/JAO.ALMA#2013.1.00166.S (PI: Leen Decin)." (Acknowledgements)
- Line: 29SiO v=0, J=8-7 (342.98084800 GHz)
- Line: SO2 v=0, 34_{3,31}-34_{2,32} (342.76162320 GHz)
- Line: 28SiO 8-7 (347.3 GHz)
- Line: CO 3-2 (345.8 GHz)
- Line: HCN 4-3 (354.5 GHz)
- Line: SO J_K=6_5-5_4 (251.8 GHz)
- Other facility **JVO/NAOJ portal**: Retrieval of SO data  
  > "The SO data are retrieved from the JVO/NAOJ portal." (Acknowledgements)
- External data: Mass-loss rate of R Dor (~1.6 10^-7 M_sun yr^-1)  
  > "a mass-loss rate of $\sim$1.6 10$^{-7}$ M$_\odot$yr$^{-1}$ (cite: Ramstedt2014; Maercker2016)" (Introduction) [from (cite: Ramstedt2014; Maercker2016)]
- External data: Distance of R Dor (~59 pc)  
  > "it is close to the Sun, at a distance of only $\sim$59 pc (cite: Knapp2003)" (Introduction) [from (cite: Knapp2003)]
- External data: Stellar disc radius at mm wavelength (~1.8 au / 0.03 arcsec)  
  > "The stellar disc, known to have a radius of $\sim$1.8 au (0.03 arcsec) at mm wavelength (cite: Vlemmings2018), is here represented with a radius of 0.035 arcsec." (The inner layer) [from (cite: Vlemmings2018)]
- External data: Temperature profile (~1100 K at 6 au, decreasing as r^-0.65)  
  > "The high excitation energy of the SO$_2$ line prevents it from populating the outer CSE as the temperature can be expected to take a value of $\sim$1100 K at 6 au from the star and to decrease as $r^{-0.65}$ (cite: Decin2018; Homan2018; VandeSande2018)." (Overall picture of the CSE) [from (cite: Decin2018; Homan2018; VandeSande2018)]
- External data: 28SiO/H2 abundance of 5.5 10^-5 and relative abundances of CO, HCN  
  > "We use a column density $N$ \[molecules cm$^{-3}$ arcsec\]=0.7 obtained by integration from $r$=0.8 to 1.0 arcsec for a $^{28}$SiO/H$_2$ abundance of 5.5 10$^{-5}$ (cite: VandeSande2018)" (Absorption over the stellar disc) [from (cite: VandeSande2018)]
- External data: Isotopic ratio 29Si/28Si = 8%  
  > "an isotopic ratio $^{29}$Si/$^{28}$Si=8% (cite: DeBeck2018)" (Absorption over the stellar disc) [from (cite: DeBeck2018)]
- External data: SO2 and SO abundances relative to H2  
  > "The abundance relative to H$_2$ is now of the form 5 10$^{-6}\exp[-(r/1.78)^2]$ (cite: Danilovich2016; Danilovich2020)" (Absorption over the stellar disc); "Using abundances relative to H$_2$ given by (cite: VandeSande2018) and (cite: Danilovich2016) and an H$_2$ density corresponding to a mass-loss rate of $\sim$1.6 10$^{-7}$ M$_\odot$ year$^{-1}$ as was done in Section 3.2" (Overall picture of the morpho-kinematics from a comparison between SO, 28SiO, CO and HCN line emissions) [from (cite: Danilovich2016; Danilovich2020)]
- External data: Star mass M = 1.4 M_sun  
  > "for a star mass $M$=1.4 M$_\odot$ (cite: Danilovich2017; DeBeck2018), $d$=$14.6\cos\theta_{\rm{bs}}/\sqrt{\sin\theta_{\rm{bs}}}$ au." (The blue stream: a possible companion?) [from (cite: Danilovich2017; DeBeck2018)]
- Simulation/model as data: Simulated visibilities created using CASA SIMOBSERVE for three toy models of sky brightness (continuum disc, absorbed CSE disc, unabsorbed disc+CSE) to test the impact of short spacing on absorption beyond the stellar disc.  
  > "visibilities $U$ corresponding to the actual antenna configuration illustrated in Figure" (6.1 Absorption of the 29SiO line emission beyond the stellar disc); "Using SIMOBSERVE in CASA, http//casa.nrao.edu" (Overall picture of the morpho-kinematics from a comparison between SO, 28SiO, CO and HCN line emissions)

## Processing

### Calibration

- pipeline or manual: Calibrated using scripts provided by ALMA staff  
  > "We calibrated the data using the scripts provided by the ALMA staff." (Observations and data reduction); "The data were reduced using standard scripts for continuum emission and two line emissions: $^{29}$SiO($\nu$=0, $J$=8$-$7) and SO$_2$($34_{3,31}$$-$$34_{2,32}$)." (Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: Deconvolution and cleaning in CASA and GILDAS  
  > "Deconvolution and cleaning were done with natural weighting using two different codes: CASA and GILDAS." (Observations and data reduction)
- weighting robust: natural weighting  
  > "Deconvolution and cleaning were done with natural weighting using two different codes: CASA and GILDAS." (Observations and data reduction); "As the $uv$ coverage for short baselines is poor, we reduced these data anew, using GILDAS with natural weighting and without continuum subtraction." (Observations and data reduction)
- uv taper: _not stated_
- cell size: 5x5 mas^2 (for 29SiO and SO2)  
  > "In both cases we use pixels of 5$\times$5 mas$^2$." (Observations and data reduction)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Processed without continuum subtraction (both 2017.1.00191.S and re-reduced 2013.1.00166.S)  
  > "The line data were processed without continuum subtraction." (Observations and data reduction); "As the $uv$ coverage for short baselines is poor, we reduced these data anew, using GILDAS with natural weighting and without continuum subtraction." (Observations and data reduction)
- line free channels: Two sets of 9 frequency channels each (7.7 km s^-1) at the beginning and end of the frequency band used to measure continuum visibilities for 29SiO  
  > "Turning now to the actual $^{29}$SiO observations, we select the two frequency intervals covering $V_z$=$\pm$4 km s$^{-1}$ and define a third interval, meant to measure continuum emission, made of two sets of 9 frequency channels each (7.7 km s$^{-1}$) at the beginning and end of the frequency band." (Absorption of the 29SiO line emission beyond the stellar disc)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 29SiO data smeared to match larger 28SiO beam size for direct comparison  
  > "Figure 1 compares the $R$ distributions of the emission of both isotopologues, the $^{29}$SiO data having been smeared to account for the larger $^{28}$SiO beam size and the $^{28}$SiO data having been multiplied by 0.08 to account for the isotopic ratio." (Absorption of SiO emission)
- final beam: 34x25 mas^2 (CASA) and 41x35 mas^2 (GILDAS) for 29SiO/SO2; 220x170 mas^2 (28SiO II), 180x140 mas^2 (CO), 157x145 mas^2 (HCN), 154x147 mas^2 / 9 au circular (SO)  
  > "The beams obtained with CASA and GILDAS (FWHM) were 34$\times$25 mas$^2$ and 41$\times$35 mas$^2$ respectively." (Observations and data reduction); "$^{28}$SiO II | 347.3 | 220$\times$170 | 80 | 38 | 18 | Aug 2015 | 21 mn" (Observations and data reduction); "Distances from the star reaching up to some $\sim$120 au are probed with a circular beam of 9 au FWHM." (Overall picture of the morpho-kinematics as seen from SO emission)
- final rms: 1.4 mJy beam^-1 (29SiO), 1.1 mJy beam^-1 (SO2), 18 mJy beam^-1 (28SiO II), 14 mJy beam^-1 (CO), 8 mJy beam^-1 (HCN), 1.2 mJy beam^-1 (SO)  
  > "Brightness distributions (Figure 2) show a noise level (1$\sigma$) of 1.4 mJy beam$^{-1}$ for $^{29}$SiO and 1.1 mJy beam$^{-1}$ for SO$_2$." (Observations and data reduction); "$^{28}$SiO II | 347.3 | 220$\times$170 | 80 | 38 | 18 | Aug 2015 | 21 mn" (Observations and data reduction); "SO | 251.8 | 154$\times$147 | 136 | 45 | 1.2 | Dec 2017 | 2.7 hr" (Observations and data reduction)

### Inherited from earlier work

- SO(J_K=6_5-5_4) data reduction, channel maps, and initial identification of outflows and ring cavities  
  > "Paper I has presented a detailed study of the morpho-kinematics of the CSE using ALMA observations of the emission of the SO($J_K$=6$_5$$-$5$_4$) line of which channel maps were displayed in the supplementary material." (Overall picture of the morpho-kinematics as seen from SO emission); "Finally, a detailed study of the outer region of the CSE, beyond some 25 au, shows the presence of outflows and of cavities suggesting a complex history of mass ejection (cite: Nhung2019)." (Introduction) [from Paper I (cite: Nhung2019)]

### Not stated but needed to reproduce (our reading)

- Exact versions of CASA and GILDAS used for calibration, imaging, and simulation
- Specific cleaning thresholds, loop gain, number of iterations, and masking strategy in CASA and GILDAS
- Image sizes (number of pixels) and pixel sizes for the 28SiO, CO, HCN, and SO cubes
- Whether primary beam correction was applied to the cubes
- Optimization algorithm / fitting routine used for the custom morpho-kinematic radiative transfer models in Sections 4 and 6.4

## Analysis recipe

1. **Calibrate and image high-resolution 29SiO and SO2 data and re-image archival 28SiO, CO, and HCN data**: Average visibilities over 20 s intervals, select 81 channels (69 km s^-1), calibrate with ALMA scripts, and deconvolve/clean with natural weighting and no continuum subtraction in both CASA and GILDAS (using GILDAS as default). Re-reduce 2013.1.00166.S lines in GILDAS without continuum subtraction.  
  > "Visibilities are averaged over 20 s wide time intervals." (Observations and data reduction); "Deconvolution and cleaning were done with natural weighting using two different codes: CASA and GILDAS." (Observations and data reduction); "As the $uv$ coverage for short baselines is poor, we reduced these data anew, using GILDAS with natural weighting and without continuum subtraction." (Observations and data reduction)
   - software: CASA, GILDAS
   - parameter: time averaging = 20 s; 81 channels = 69 km s^-1 (0.854 km s^-1 bin); pixel size = 5x5 mas^2; natural weighting; no continuum subtraction  
  > "We select a frequency interval of 81 channels corresponding to a Doppler velocity interval of 69 km s$^{-1}$, each Doppler velocity bin being 0.854 km s$^{-1}$ wide." (Observations and data reduction); "In both cases we use pixels of 5$\times$5 mas$^2$." (Observations and data reduction)
   - assumption: Systemic velocity of R Dor is 7 km s^-1  
  > "The systemic velocity of R Dor (7 km s$^{-1}$) is taken as origin." (Observations and data reduction)
   - fitting: _not stated_
   - validation: Compared CASA and GILDAS imaging results and checked visibility distributions of 28SiO I vs II to restrict analysis to r <= 60 au.  
  > "In what follows we use the GILDAS results as default but we checked their consistency with the CASA results whenever possibly relevant." (Observations and data reduction); "Accordingly, we restrict the analysis to distances from the star not exceeding 60 au (1 arcsec)." (Observations and data reduction)
2. **Extract and fit Doppler velocity spectra and azimuthal profiles in the inner layer (0.05 < R < 0.20 arcsec)**: Divide inner CSE into concentric rings (0.05 arcsec wide) and quadrants; fit spectra with a continuum term plus Gaussian emission minus Gaussian outer-layer absorption at -4.0 km s^-1; fit azimuthal intensity and mean Doppler velocity distributions with sine waves A + B sin(omega - omega_0).  
  > "Good fits to both $^{29}$SiO and SO$_2$ spectra are accordingly obtained using the simple form $$\begin{align} &I=I^*+I_0G(V_{z},V_{z0},\sigma_0)-A G(V_{z},-4.0,1.2) \nonumber \\ \mbox{where\,}& G(V_{z},a,b)=\exp(-\sfrac{1}{2}[V_{z}-a]^2/b^2).\nonumber \end{align}$$" (The inner layer); "Parameters of the sine wave fits of the form $A+B\sin(\omega-\omega_0)$ to the mean Doppler velocity distributions displayed in Figure 9." (Table 2)
   - parameter: Rings: 50-100, 100-150, 150-200 mas; absorption center = -4.0 km s^-1, width sigma = 1.2 km s^-1; 3 sigma cut and |V_z| < 12 km s^-1 for sine fits  
  > "$A$ is set to zero in the SO$_2$ case and is such that the xabsorption be total at $V_{z}=-4.0$ km s$^{-1}$ in the $^{29}$SiO case, namely $A=I^*+I_0G(V_{z},-4.0,1.2)$; the width of the absorption term is fixed with a $\sigma$ of 1.2 km s$^{-1}$." (The inner layer); "A cut of 3$\sigma$ has been applied to the data; the intensity is integrated and the Doppler velocity averaged over the \|$V_z$\|\<12 km s$^{-1}$ interval." (Table 2)
   - assumption: Total absorption at V_z = -4.0 km s^-1 for 29SiO and zero outer absorption (A=0) for SO2  
  > "$A$ is set to zero in the SO$_2$ case and is such that the xabsorption be total at $V_{z}=-4.0$ km s$^{-1}$ in the $^{29}$SiO case, namely $A=I^*+I_0G(V_{z},-4.0,1.2)$; the width of the absorption term is fixed with a $\sigma$ of 1.2 km s$^{-1}$." (The inner layer)
   - fitting: Gaussian spectral profile fitting and sine wave fitting  
  > "Parameters of the sine wave fits of the form $A+B\sin(\omega-\omega_0)$ to the mean Doppler velocity distributions displayed in Figure 9." (Table 2)
   - validation: Tested linear interpolation across the absorbed V_z interval in the PV map vs keeping the absorbed interval untouched.  
  > "In each $\omega$ bin, the brightness in the $V_z$ absorption interval has been interpolated linearly between its values taken just above and just below. The result is essentially the same as if one keeps the absorbed interval untouched: a fit of the form $A+B\sin(\omega-\omega_0)$ gives $B$=3.6 km s$^{-1}$ and $\omega_0$=191$^\circ$ instead of 3.6 km s$^{-1}$ and 190$^\circ$." (The inner layer, rotation and line width)
3. **Evaluate LTE radiative transfer and optical depth over the stellar disc**: Calculate LTE unabsorbed emission epsilon and optical depth tau over 0.2 < r < 1.0 arcsec for 29SiO and SO2 and compare predicted self-absorbed emission against the observed 3-sigma upper limit over the stellar disc (R < 0.035 arcsec) at V_z ~ -4 km s^-1.  
  > "Quantitatively, we can safely place a 3-$\sigma$ upper limit of 4.2 mJy beam$^{-1}$ (10 mJy over the stellar disc) on the brightness measured at maximal absorption, $V_{z}$$\sim$$-$4 km s$^{-1}$, over the stellar disc ($R$\<0.035 arcsec)." (Absorption over the stellar disc); "We first calculate $\varepsilon$ and $\tau$ at a temperature $T$$\sim$270 K using Relations 2 and 3 for $^{29}$SiO." (Absorption over the stellar disc)
   - parameter: Stellar disc R < 0.035 arcsec; T = 270 K; Delta V = 2.8 km s^-1  
  > "Namely, at $T$=270 K, $\varepsilon$=8.2 Jy arcsec$^{-2}$ and $\tau$=0.36 for $\Delta{V}$=2.8 km s$^{-1}$: the self-absorbed emission is $\sim$27 mJy over the stellar disc, nearly 3 times the upper limit placed on the observed emission." (Absorption over the stellar disc)
   - assumption: LTE, 28SiO/H2 = 5.5 10^-5, 29Si/28Si = 8%, H2 density = 1.6 10^7 (r/0.2)^-2 cm^-3 (mass-loss rate ~1.6 10^-7 M_sun yr^-1), SO2/H2 = 5 10^-6 exp(-(r/1.78)^2)  
  > "We use a column density $N$ \[molecules cm$^{-3}$ arcsec\]=0.7 obtained by integration from $r$=0.8 to 1.0 arcsec for a $^{28}$SiO/H$_2$ abundance of 5.5 10$^{-5}$ (cite: VandeSande2018), an isotopic ratio $^{29}$Si/$^{28}$Si=8% (cite: DeBeck2018) and an H$_2$ density of the form 1.6 10$^{7}$ $(r/0.2)^{-2}$ \[molecules cm$^{-3}$\], meaning a mass-loss rate of $\sim$1.6 10$^{-7}$ M$_\odot$ yr$^{-1}$." (Absorption over the stellar disc); "The abundance relative to H$_2$ is now of the form 5 10$^{-6}\exp[-(r/1.78)^2]$ (cite: Danilovich2016; Danilovich2020), $E_{\rm{u}}$=581.92 K and $A_{\rm{ji}}$=3.45 10$^{-4}$ s$^{-1}$, but the relation $\tau$$\sim$11.8$\varepsilon/T$ still applies." (Absorption over the stellar disc)
   - fitting: _not stated_
   - validation: _not stated_
4. **Measure kinematics and pointing of the south-eastern blue stream and test planetary companion hypothesis**: Measure stream position in each frequency channel separately, fit straight lines to determine position angle, pointing offset from the star, and linear acceleration dV_z/dR; evaluate orbital travel distance of a putative companion during the gas transit time.  
  > "In order to define it precisely we measure for each line its position in each frequency interval separately and fit straight lines through the points." (The blue stream); "During this time, the companion, assumed to be on a circular orbit of radius $R_1/\sin\theta_{\rm{bs}}$, covers a distance $d$=$tV_{\rm{orb}}$ where $V_{\rm{orb}}$\[au yr$^{-1}$\]=$2\pi\sqrt{(M/\mbox{M$_\odot$})\sin\theta_{\rm{bs}}/R_1[\mbox{au}]}$ is the orbital velocity; for a star mass $M$=1.4 M$_\odot$ (cite: Danilovich2017; DeBeck2018), $d$=$14.6\cos\theta_{\rm{bs}}/\sqrt{\sin\theta_{\rm{bs}}}$ au." (The blue stream: a possible companion?)
   - parameter: PA = 140 deg; PV slit width = +/- 3 au; R_1 ~ 10 au, R_2 ~ 30 au; |V_z1| ~ 7 km s^-1, |V_z2| ~ 18 km s^-1  
  > "Panel c of Figure 13 displays a Position-Velocity (PV) diagram along a $\pm$3 au wide slit at position angle 140$^\circ$." (The blue stream); "The present data show that, in projection on the plane of the sky, gas flows radially from $R_1$$\sim$10 au to $R_2$$\sim$30 au with mean Doppler velocity increasing from \|$V_{z1}$\|$\sim$7 km s$^{-1}$ to \|$V_{z2}$\|$\sim$18 km s$^{-1}$." (The blue stream: a possible companion?)
   - assumption: Circular orbit of companion around a 1.4 M_sun star; orbital axis aligned with gas rotation axis (PA = 10 +/- 5 deg)  
  > "Assuming that the orbital axis is at the same time the rotation axis of the volume of gas we retain a value $\omega_R$=10$^\circ$$\pm$5$^\circ$ east of north" (5 The blue stream: a possible companion?)
   - fitting: Straight-line fits to channel-by-channel positions and velocity vs R  
  > "In order to define it precisely we measure for each line its position in each frequency interval separately and fit straight lines through the points." (The blue stream)
   - validation: _not stated_
5. **Model inner-layer 29SiO morpho-kinematics (rotation, expansion, turbulence, density, temperature)**: Fit a 3D morpho-kinematic model of 29SiO emission across four concentric rings to constrain density n_0 and temperature T_0 at r = 0.1 arcsec (6 au), radial expansion, and Gaussian turbulent line broadening.  
  > "We study this with the help of a crude model of the morpho-kinematics of the $^{29}$SiO emission of the inner layer." (The inner layer, rotation and line width); "Temperature and density are assumed to depend on distance as $r^{-0.65}$ and $r^{-2}$ respectively, their values at $r$=0.1 arcsec (6 au), $T_0$ and $n_0$ respectively, being varied to optimize the fit." (The inner layer, rotation and line width)
   - parameter: V_rot = 64 r (1 - 4r) km s^-1 for r <= 0.25 arcsec and 0 beyond; rotation axis PA = 10 deg, inclination = 20 deg  
  > "Rotation is assumed to proceed about an axis projecting 10$^\circ$ east of north with a velocity depending on $r$ \[arcsec\] as $V_{\rm{rot}}$ \[km s$^{-1}$\]=64$r(1-4r)$ and $V_{\rm{rot}}$=0 beyond $r$=0.25 arcsec.The inclination of the rotation axis with respect to the plane of the sky is taken to be 20$^\circ$." (The inner layer, rotation and line width)
   - assumption: T propto r^-0.65, n propto r^-2, Gaussian turbulent dispersion sigma_turb = V_turb exp(-0.5 (r - r_turb)^2 / Delta r_turb^2)  
  > "Temperature and density are assumed to depend on distance as $r^{-0.65}$ and $r^{-2}$ respectively, their values at $r$=0.1 arcsec (6 au), $T_0$ and $n_0$ respectively, being varied to optimize the fit." (The inner layer, rotation and line width); "Line broadening is described as a Gaussian of dispersion $\sigma_{\rm{turb}}$=$V_{\rm{turb}}\exp[-\sfrac{1}{2}(r-r_{\rm{turb}})^2/\Delta{r_{\rm{turb}}}^2]$ having itself a Gaussian radial dependence." (The inner layer, rotation and line width)
   - fitting: Optimization of n_0, T_0, expansion, and turbulence parameters against ring spectra  
  > "The best fit, illustrated in Figure 1, gives $n_0=130^{+90}_{-40}$ molecules cm$^{-3}$ and $T_0$=$450^{+130}_{-90}$ K: the density is $(40^{+30}_{-10})$% and the temperature $(40^{+12}_{-8})$% of the values quoted by (cite: VandeSande2018)." (The inner layer, rotation and line width)
   - validation: _not stated_
6. **Test whether extended 29SiO absorption is an interferometric short-spacing artefact**: Simulate visibilities with CASA SIMOBSERVE for three isotropic sky brightness models (case 1: stellar continuum disc R < 0.04 arcsec; case 2: CSE disc R < 0.3 arcsec with absorbed stellar disc; case 3: sum of cases 1 and 2) using the actual antenna configuration, and compare baseline-dependent visibility amplitudes against real 29SiO visibilities at V_z = -4, +4 km s^-1, and continuum.  
  > "visibilities $U$ corresponding to the actual antenna configuration illustrated in Figure" (6.1 Absorption of the 29SiO line emission beyond the stellar disc); "Turning now to the actual $^{29}$SiO observations, we select the two frequency intervals covering $V_z$=$\pm$4 km s$^{-1}$ and define a third interval, meant to measure continuum emission, made of two sets of 9 frequency channels each (7.7 km s$^{-1}$) at the beginning and end of the frequency band." (Absorption of the 29SiO line emission beyond the stellar disc)
   - software: CASA, SIMOBSERVE
   - parameter: Case 1: 1 Jy/pixel for R < 0.04 arcsec; Case 2: 0.1 Jy/pixel for 0.04 < R < 0.3 arcsec; Case 3: Case 1 + Case 2  
  > "The first model, case 1, shown in blue, represents continuum emission and is described as a uniform brightness of 1 Jy/pixel over the stellar disc ($R$\<0.04 arcsec)." (Absorption of the 29SiO line emission beyond the stellar disc); "The second model, case 2, in red, shows a disc of uniform brightness, arbitrarily set to 0.1 Jy/pixel, and having a radius of 0.3 arcsec, meant to represent the emission of the CSE." (Absorption of the 29SiO line emission beyond the stellar disc)
   - assumption: Isotropic sky brightness distributions  
  > "It assumes the isotropy of the brightness in the plane of the sky and considers three different models, each defined by a simple radial dependence of the brightness as illustrated in Figure 3a." (Absorption of the 29SiO line emission beyond the stellar disc)
   - fitting: Rayleigh noise distribution fit |U| exp(-0.5 |U|^2 / sigma^2) to visibility amplitudes  
  > "The noise is well described by a form \|$U$\|$\exp(-\sfrac{1}{2}|$$U$$|^2/\sigma^2)$, meaning a Gaussian distribution in each of Re($U$) and Im($U$) with a common rms value, $\sigma$, measured to be 0.62 Jy." (Absorption of the 29SiO line emission beyond the stellar disc)
   - validation: Direct comparison of raw visibility amplitudes between V_z = +4 km s^-1 and V_z = -4 km s^-1 channels where uv coverage, noise, and calibration are identical.  
  > "The short spacing problem is precisely the same for the $V_z$=$+$4 km s$^{-1}$ and $V_z$=$-$4 km s$^{-1}$ cases; the noise is the same; the calibration uses only observations made for this purpose and is also the same for the two channels." (Absorption of the 29SiO line emission beyond the stellar disc)
7. **Reconstruct 3D outflow geometry and model outer SiO self-absorption using SO, 28SiO, CO, and HCN**: Deproject SO, 28SiO, CO, and HCN data cubes onto perpendicular outflow planes P1 (PA = 60 deg) and P2 (PA = 150 deg) using a radial velocity law V = V_term r / (r + r_1/2); compare observed radial flux profiles to optically thin LTE predictions; fit a radiative transfer model to 28SiO spectra in rings 0.35 < R < 0.55 arcsec and 0.65 < R < 0.85 arcsec.  
  > "Using the law introduced in the preceding paragraph with $V_{\rm{term}}$=7 km s$^{-1}$ and $r_{\sfrac{1}{2}}$=30 au (0.5 arcsec) the map of the intensity projected on P1, displayed in panel b of Figure 6, gives $\varphi$$\sim$45$^\circ$." (Overall picture of the morpho-kinematics as seen from SO emission); "Finally, we model the $^{28}$SiO emission over two rings, 0.35\<$R$\<0.55 arcsec and 0.65\<$R$\<0.85 arcsec, far enough from the stellar disc for continuum emission to be negligible." (Absorption of SiO emission)
   - parameter: V_term = 7 km s^-1, r_1/2 = 30 au (0.5 arcsec) for deprojection; rings 0.35-0.55 and 0.65-0.85 arcsec for 28SiO fit  
  > "Using the law introduced in the preceding paragraph with $V_{\rm{term}}$=7 km s$^{-1}$ and $r_{\sfrac{1}{2}}$=30 au (0.5 arcsec) the map of the intensity projected on P1, displayed in panel b of Figure 6, gives $\varphi$$\sim$45$^\circ$." (Overall picture of the morpho-kinematics as seen from SO emission); "Finally, we model the $^{28}$SiO emission over two rings, 0.35\<$R$\<0.55 arcsec and 0.65\<$R$\<0.85 arcsec, far enough from the stellar disc for continuum emission to be negligible." (Absorption of SiO emission)
   - assumption: V = V_term r / (r + r_1/2); density propto r^-2; temperature T = T_0.5 r^-p; LTE radiative transfer  
  > "in particular for an acceleration law of the form $V$=$V_{\rm{term}}r/(r+r_{\sfrac{1}{2}})$, tending asymptotically to the terminal velocity $V_{\rm{term}}$ when $r$ tends to infinity and reaching the value $\sfrac{1}{2}V_{\rm{term}}$ for $r$=$r_{\sfrac{1}{2}}$" (Overall picture of the morpho-kinematics as seen from SO emission); "It assumes a $r^{-2}$ radial dependence of the density. The temperature is taken of the form $T$=$T_{0.5}r^{-p}$." (Absorption of SiO emission)
   - fitting: Adjustment of r_1/2, N_0.5, line width parameters, T_0.5, and p to match 28SiO ring spectra  
  > "The parameters being adjusted are the expansion parameter $r_{\sfrac{1}{2}}$, the density $N_{0.5}$ at $r$=0.5 arcsec, the line width parameters and the temperature parameters $T_{0.5}$ and $p$." (Absorption of SiO emission)
   - validation: Sensitivity test varying r_1/2 between 0.25 and 0.75 arcsec; comparison of smeared 29SiO to scaled 28SiO radial distributions.  
  > "The value of $r_{\sfrac{1}{2}}$ can be chosen anywhere between 0.25 and 0.75 arcsec (15 and 45 au) without $\varphi$ changing by more than $\pm$5$^\circ$." (Overall picture of the morpho-kinematics as seen from SO emission); "The observed increase of absorption between $^{29}$SiO and $^{28}$SiO is $\sim$5 in the red hemisphere and $\sim$10 in the blue hemisphere, well bracketing the predicted value of 7.7." (Absorption of SiO emission)

## Software

- **CASA** : Calibration, deconvolution and cleaning of 29SiO and SO2 data, and visibility simulations using SIMOBSERVE  
  > "Deconvolution and cleaning were done with natural weighting using two different codes: CASA and GILDAS." (Observations and data reduction); "Using SIMOBSERVE in CASA, http//casa.nrao.edu" (Overall picture of the morpho-kinematics from a comparison between SO, 28SiO, CO and HCN line emissions)
- **GILDAS** : Deconvolution and cleaning of 29SiO, SO2, 28SiO, CO, and HCN data (used as default imaging code)  
  > "Deconvolution and cleaning were done with natural weighting using two different codes: CASA and GILDAS." (Observations and data reduction); "In what follows we use the GILDAS results as default but we checked their consistency with the CASA results whenever possibly relevant." (Observations and data reduction); "As the $uv$ coverage for short baselines is poor, we reduced these data anew, using GILDAS with natural weighting and without continuum subtraction." (Observations and data reduction)
- **SIMOBSERVE** : Simulating visibilities for toy models of sky brightness to test short-spacing effects on extended absorption  
  > "Using SIMOBSERVE in CASA, http//casa.nrao.edu" (Overall picture of the morpho-kinematics from a comparison between SO, 28SiO, CO and HCN line emissions)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Maximal rotation velocity of inner CSE | 5 to 7 | not stated | km s^-1 | 2 | i) Rotation is seen to reach a maximal velocity of $\sim$5 to 7 km s$^{-1}$ at some 8$\pm$2 au from the centre of the star, where the Keplerian orbital velocity around a 1.4 M$_\odot$ star is $\sim$13 km s$^{-1}$. |
| Radius of maximal rotation velocity | 8 | 2 | au | 2 | i) Rotation is seen to reach a maximal velocity of $\sim$5 to 7 km s$^{-1}$ at some 8$\pm$2 au from the centre of the star, where the Keplerian orbital velocity around a 1.4 M$_\odot$ star is $\sim$13 km s$^{-1}$. |
| Position angle of rotation axis projection | 10 | 5 | deg | 2 | We retain a value of 10$\pm$5$^\circ$ for the projection angle of the rotation axis, in agreement with the value of 7$\pm$6$^\circ$ obtained by (cite: Vlemmings2018).; Its axis projects on the plane of the sky at a position angle of 10$\pm$5$^\circ$ and makes an unknown angle with the plane of the sky |
| 3-sigma upper limit on 29SiO brightness at maximal absorption (V_z ~ -4 km s^-1) over stellar disc | 4.2 | not stated | mJy beam^-1 | 3 | Quantitatively, we can safely place a 3-$\sigma$ upper limit of 4.2 mJy beam$^{-1}$ (10 mJy over the stellar disc) on the brightness measured at maximal absorption, $V_{z}$$\sim$$-$4 km s$^{-1}$, over the stellar disc ($R$\<0.035 arcsec). |
| 3-sigma upper limit on 29SiO flux density at maximal absorption over stellar disc | 10 | not stated | mJy | 3 | Quantitatively, we can safely place a 3-$\sigma$ upper limit of 4.2 mJy beam$^{-1}$ (10 mJy over the stellar disc) on the brightness measured at maximal absorption, $V_{z}$$\sim$$-$4 km s$^{-1}$, over the stellar disc ($R$\<0.035 arcsec). |
| Mean position angle of the blue stream | 140 | not stated | deg | 4 | It covers projected distances from the star reaching $\sim$30 au for the former (Figure \[figA1\]) and $\sim$20 au for the latter (Figure \[figA2\]) at a mean position angle of $\sim$140$^\circ$. |
| Projected acceleration of the blue stream | 39.2 | 0.5 | km s^-1 arcsec^-1 | 4 | To a good approximation it displays a constant projected acceleration of 39.2$\pm$0.5 km s$^{-1}$ arcsec$^{-1}$.; iii) The blue stream is observed at $\sim$140$^\circ$ position angle to extend radially from $\sim$10 au to $\sim$30 au with a mean projected acceleration of 39.2$\pm$0.9 km s$^{-1}$ arcsec$^{-1}$. |
| Pointing offset of the blue stream from the star (south-west) | 1.5 | 1.5 | au | 4 | Figures 12 and 13 show that the stream nearly points to the star; more precisely it points 1.5$\pm$1.5 au south-west of the star. |
| Best-fit 29SiO density n_0 at r = 0.1 arcsec (6 au) | 130 | +90/-40 | molecules cm^-3 | 5 | The best fit, illustrated in Figure 1, gives $n_0=130^{+90}_{-40}$ molecules cm$^{-3}$ and $T_0$=$450^{+130}_{-90}$ K: the density is $(40^{+30}_{-10})$% and the temperature $(40^{+12}_{-8})$% of the values quoted by (cite: VandeSande2018). |
| Best-fit temperature T_0 at r = 0.1 arcsec (6 au) | 450 | +130/-90 | K | 5 | The best fit, illustrated in Figure 1, gives $n_0=130^{+90}_{-40}$ molecules cm$^{-3}$ and $T_0$=$450^{+130}_{-90}$ K: the density is $(40^{+30}_{-10})$% and the temperature $(40^{+12}_{-8})$% of the values quoted by (cite: VandeSande2018). |
| Turbulent velocity dispersion V_turb in the inner layer (r < 12 au) | 4.3 | 1.1 | km s^-1 | 5 | The best fit does not allow for significant expansion below $r$$\sim$10 au and requires a turbulence confined to the $r$\<12 au region with $V_{\rm{turb}}=4.3\pm1.1$ km s$^{-1}$. |
| Visibility noise rms sigma for 29SiO | 0.62 | not stated | Jy | 6 | The noise is well described by a form \/$U$\/$\exp(-\sfrac{1}{2}/$$U$$/^2/\sigma^2)$, meaning a Gaussian distribution in each of Re($U$) and Im($U$) with a common rms value, $\sigma$, measured to be 0.62 Jy. |
| Position angle of common back-to-back outflow axis projection | 60 | 5 | deg | 7 | A very crude model of two back-to-back outflows is used to evaluate the orientation of the common outflow axis: it projects on the plane of the sky 60$^\circ$$\pm$5$^\circ$ east of north. |
| Angle phi of the outflow axis with the plane of the sky | 45 | 5 | deg | 7 | Using the law introduced in the preceding paragraph with $V_{\rm{term}}$=7 km s$^{-1}$ and $r_{\sfrac{1}{2}}$=30 au (0.5 arcsec) the map of the intensity projected on P1, displayed in panel b of Figure 6, gives $\varphi$$\sim$45$^\circ$.; The value of $r_{\sfrac{1}{2}}$ can be chosen anywhere between 0.25 and 0.75 arcsec (15 and 45 au) without $\varphi$ changing by more than $\pm$5$^\circ$. |
| Modelled 28SiO temperature T_0.5 at r = 0.5 arcsec | 315 | not stated | K | 7 | The fit requires again a much steeper radial dependence of the temperature than used in earlier works: the fits displayed in Figure 1 are for $T_{0.5}$=315 K and a 1/$r$ dependence ($p$=1) meaning $T$=158 K at $r$=1 arcsec. |
| Modelled 28SiO density at r = 0.5 arcsec | 1625 | not stated | molecules cm^-3 | 7 | The density at $r$=0.5 arcsec is 1625 molecules per cm$^3$, in agreement with the value found for the $^{29}$SiO fit, $\sim$40% of that given by (cite: VandeSande2018). |

## Qualitative findings

- Rotation of the inner CSE is confined below ~15 au, reaches its maximum below 10 au, and shows no disc-like equatorial flattening, reconciling the solid-body (Vlemmings et al. 2018) and sub-Keplerian (Homan et al. 2018) models.  
  > "1) Rotation is confined below $\sim$15 au from the star, with velocity reaching a maximum below 10 au and morphology showing no significant disc-like flattening." (Abstract); "The picture obtained from the analysis of the present observations reconciles those presented earlier by (cite: Vlemmings2018) and (cite: Homan2018), claimed to be in conflict by the former authors." (Summary and conclusions)
- High Doppler velocity wings near the line of sight to the stellar disc are well separated from the blue stream and are caused by turbulent/shock line broadening below ~12 au.  
  > "Significant line broadening occurs below $\sim$12 au from the star and causes the presence of high Doppler velocity components near the line of sight pointing to the centre of the star." (Abstract); "iv) The high Doppler velocity wings studied earlier have been shown to be well separated from the blue stream and to be caused by a significant line broadening occurring within the inner layer of the CSE, below 12 au from the star." (Summary and conclusions)

## Claim tuples

- H: The rotating inner CSE of R Dor has a flattened, nearly edge-on disc morphology and either solid-body or sub-Keplerian rotation. | E: Measure azimuthal distributions of integrated intensity and mean Doppler velocity of 29SiO and SO2 in concentric rings from 0.05 to 0.20 arcsec (3 to 12 au) and out to 0.60 arcsec. | R: Mean Doppler velocity follows a dipole sine wave with rotation axis at PA 10 +/- 5 deg, reaching a maximum of ~5-7 km s^-1 at 8 +/- 2 au and vanishing around 15 au; azimuthal intensity shows a ~20% dipole oscillation peaking in the NW and no quadrupole cos(2*omega) flattening term. | F: Rotation increases from the stellar surface to ~8 au and declines to zero by ~15 au (reconciling solid-body and sub-Keplerian descriptions), with no evidence for an edge-on flattened disc. | **refuted**
- H: The south-eastern blue-shifted high-velocity gas stream is a trail of gas behind an evaporating planetary companion in circular orbit. | E: Trace the blue stream position across frequency channels in 29SiO and SO2 to measure its trajectory, pointing offset, and projected acceleration, and calculate the orbital motion of a companion during the gas transit time. | R: The stream extends radially from ~10 to ~30 au at PA ~140 deg with linear acceleration 39.2 +/- 0.5 km s^-1 arcsec^-1 and points within 1.5 +/- 1.5 au of the star, requiring either stream inclination > 84 deg (space velocity > 100 km s^-1) or producing a curved spiral offset much larger than 1.5 au. | F: It is difficult to associate the blue stream with gas trailing an orbiting companion; local acceleration by an enhanced density of aluminium-rich dust at ~12 au is more natural. | **refuted**
- H: Strong absorption of 29SiO emission at V_z ~ -4 km s^-1 extending well beyond the stellar disc is a real physical self-absorption by a cold outer SiO layer rather than an interferometric short-spacing artefact. | E: Simulate visibilities in CASA SIMOBSERVE for toy brightness models, compare raw visibility amplitudes at V_z = -4 and +4 km s^-1, and model multiline (29SiO, 28SiO, SO, CO, HCN) radiative transfer out to ~100 au. | R: Raw visibilities at V_z = -4 km s^-1 are suppressed down to short baselines compared to +4 km s^-1, and 28SiO emission is strongly suppressed (~factor 5-10 relative to 29SiO) requiring an optically thick, cooler SiO layer extending from ~0.2 to >1 arcsec (up to ~60 au). | F: The extended absorption is real and caused by self-absorption in a cold, optically thick SiO layer expanding at ~4 km s^-1 up to ~60 au from the star. | **supported**
- H: High Doppler velocity wings observed near the centre of the stellar disc are produced by inner-layer line broadening rather than by the south-eastern blue stream. | E: Extract Doppler velocity spectra integrated over small central circles (R < 0.1 and < 0.2 arcsec) in 29SiO and SO2 and fit a morpho-kinematic model with radially dependent turbulence. | R: High-velocity wings are well separated from the blue stream, approximated by a Gaussian of sigma ~ 5.5 km s^-1, and reproduced by inner-layer turbulence V_turb = 4.3 +/- 1.1 km s^-1 confined to r < 12 au with negligible radial expansion below ~10 au. | F: High-velocity wings near the stellar line of sight result from significant line broadening (shocks/turbulence/pulsations) confined below ~12 au. | **supported**

## Reasoning

- Why this data: The 29SiO and SO2 lines at ~2.3 au resolution cover distances below ~30 au, linking earlier high-resolution inner-layer studies and lower-resolution outer-envelope studies; SO, 28SiO, CO, and HCN probe larger distances up to ~100 au to explain the outer SiO absorption.  
  > "With a spatial resolution of $\sim$2.3 au, they cover distances below $\sim$30 au from the star providing a link between earlier observations and clarifying some open issues." (Abstract); "Section 6 explores the CSE to larger distances from the star using other molecular line emissions as probes with the aim of explaining what causes the strong absorption of the SiO lines." (Introduction)
- Why this method: Data were re-reduced without uv-plane continuum subtraction because poor short-baseline uv coverage makes continuum subtraction unreliable and could distort absorption; PV maps in V_z vs omega and V_z vs R planes allow clear visualization and 3D deprojection of complex, anisotropic wind structures.  
  > "As the $uv$ coverage for short baselines is poor, we reduced these data anew, using GILDAS with natural weighting and without continuum subtraction." (Observations and data reduction); "We find that PV maps displaying the brightness in the Doppler velocity ($V_z$) vs position angle ($\omega$) or vs projected distance ($R$) planes, are particularly convenient for this purpose." (Overall picture of the morpho-kinematics as seen from SO emission)
- Alternative: Disregarded the 28SiO I dataset from project 2013.1.00166.S because it lacked a few short baselines compared to 28SiO II and added no significant information.  
  > "Moreover, we disregard the $^{28}$SiO I set of data as not adding significant information to that obtained from the $^{28}$SiO II set." (Observations and data reduction)
- Alternative: Rejected interferometric short-spacing artefacts as the cause of the extended 29SiO absorption at V_z = -4 km s^-1 by comparing simulated visibilities and symmetric V_z = +4 km s^-1 visibilities.  
  > "The global blank out of the $V_z$=$-$4 km s$^{-1}$ observations is therefore shown to be present at raw data level already and we must conclude that it is real and not the result of some instrumental artefact." (Absorption of the 29SiO line emission beyond the stellar disc)
- Alternative: Rejected edge-on flattened disc model (Homan et al. 2018) and evaporating planetary companion trail model for the blue stream.  
  > "The absence of a quadripolar term sheds doubts on the previously suggested evidence for the presence of an edge-on disc." (The inner layer); "It is difficult to conceive a sensible scenario that would simply relate the presence of the blue stream to that of an evaporating planetary companion, as suggested earlier by (cite: Decin2018; Homan2018) and (cite: Vlemmings2018)." (Summary and conclusions)
- How they decided it was enough: _not stated_
- Limitation (authors): LTE assumption and morpho-kinematic models are crude and oversimplified (e.g., modelling shock/pulsation broadening as Gaussian fluctuations and assuming simple power-law radial profiles).  
  > "While local thermal equilibrium (LTE) is not expected to provide a reliable description of the CSE, in particular in the close neighbourhood of the star, its prediction provides a useful reference with which to compare observations." (Absorption over the stellar disc); "Its modelling as Gaussian fluctuations is a grossly oversimplified approximation." (The inner layer, rotation and line width); "The model is too simple and makes too many simplifying assumptions for these numbers to be taken at face value." (Absorption of SiO emission)
- Limitation (authors): Poor uv coverage at short baselines for the 2013.1.00166.S (28SiO, CO, HCN) data limits reliable analysis to r <= 60 au (1 arcsec) and prevents quantitative statements at larger radii.  
  > "Accordingly, we restrict the analysis to distances from the star not exceeding 60 au (1 arcsec)." (Observations and data reduction); "A quantitative reliable modelling would require observations of higher sensitivity and better $uv$ coverage than currently available." (Absorption of SiO emission)
- Limitation (authors): The 3D inclination angle of the blue stream with the line of sight and the inclination of the rotation axis with the plane of the sky are unknown.  
  > "The angle made by the stream with the line of sight is unknown." (The blue stream); "Its axis projects on the plane of the sky at a position angle of 10$\pm$5$^\circ$ and makes an unknown angle with the plane of the sky; yet, qualitative considerations favour a low value, typically 20$^\circ$$\pm$20$^\circ$ as suggested by the analysis of (cite: Homan2018)." (Summary and conclusions)
- Caveat (inferred, ours): Non-LTE radiative transfer (including infrared radiative pumping of SiO and sub-thermal excitation in the outer envelope) is neglected in the analytical LTE slab approximations, which could significantly alter the inferred kinetic temperature and density profiles.
- Caveat (inferred, ours): 3D deprojection of the outer outflows assumes an isotropic, monotonic radial velocity law V(r), which may conflate velocity variations (shocks, turbulence, non-radial motions) with spatial density structures.

## Reproducibility

- Data public (paper): Raw data are publicly available on the ALMA archive (2017.1.00191.S, 2017.1.00824.S, 2013.1.00166.S) and SO data on the JVO/NAOJ portal; calibrated and imaged data available on reasonable request.  
  > "The raw data are available on the ALMA archive ADS/JAO.ALMA#2017.1.00191.S, ADS/JAO.ALMA# 2017.1.00824.S, ADS/JAO.ALMA#2013.1.00166.S. The calibrated and imaged data underlying this article will be shared on reasonable request to the corresponding author." (Data Availability); "The SO data are retrieved from the JVO/NAOJ portal." (Acknowledgements)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: Custom radiative transfer and morpho-kinematic fitting scripts used in Sections 4 and 6.4
- Missing: Exact CASA and GILDAS versions and cleaning parameters (stopping thresholds, iterations, masks)
- Missing: Exact rest frequencies and spectral channel binning for the 28SiO, CO, HCN, and SO datasets
- Data volume (inferred): ~50-150 GB of raw archival visibility data across three ALMA projects (including long-baseline C43-9 observations), <5 GB for reduced spectral cubes.
- Score (inferred): 7/5, All three ALMA project codes are public, spectral setups and imaging choices (natural weighting, 5 mas pixels, no continuum subtraction, channel widths) are clearly stated, and analytical equations and best-fit parameter tables are given in full; however, custom modelling scripts and exact cleaning thresholds are not released.
- Rediscovery candidate: yes, Public archival ALMA data with well-defined geometric ring/quadrant spectral extractions, analytic Gaussian/sine fitting formulas, and explicit numeric tables (Tables 2, A1, A2) make the kinematic and absorption measurements straightforward to reproduce.

## Links

- Method: (cite: Gueth1997) (Cited for the interferometric short-spacing problem discussed in Section 6.1)
- Companion: Paper I (cite: Nhung2019) (Earlier paper by the same team studying the outer CSE of R Dor primarily via the SO(6_5-5_4) line and introducing the 28SiO, CO, and HCN datasets)

## Checks

```json
{
 "quotes": 182,
 "quotes_ok": 182,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 14,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 16,
 "numeric_problems": 0,
 "fill": {
  "facts": 101,
  "stated": 78,
  "rate": 0.772
 },
 "evidence_ok": true
}
```

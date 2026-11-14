# Direct detection of quasar feedback via the Sunyaev-Zeldovich effect

`2019MNRAS.483L..22L` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Lacy, Mark | arXiv: 1811.05023 | DOI: 10.1093/mnrasl/sly215 | **HELD OUT (benchmark)**

Card schema 1.0 | model claude-opus-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, galaxy_clusters_and_sz
- Question: Can the Sunyaev-Zeldovich effect from a hot thermal wind bubble around a hyperluminous radio-quiet quasar be detected directly with ALMA, and what does it imply for the wind energetics?  
  > "The nature and energetics of feedback from thermal winds in quasars can be constrained via observations of the Sunyaev-Zeldovich Effect (SZE) induced by the bubble of thermal plasma blown into the intergalactic medium by the quasar wind." (abstract); "We selected the most luminous radio-quiet quasar we could find in the literature that had good visibility to ALMA, HE 0515-4414" (Introduction)
- Target **HE 0515-4414**: coordinates RA 05:17:07.614, Dec -44:10:55.64 (QSO position in point-source model table)  
  > "HE 0515-4414 ($z=1.71$; Reimers et al. 1998)" (Introduction); "05:17:07.614" (Table 1); "-44:10:55.64" (Table 1); z/distance z = 1.71  
  > "HE 0515-4414 ($z=1.71$; Reimers et al. 1998)" (Introduction); "05:17:07.614" (Table 1); "-44:10:55.64" (Table 1); distance from Reimers et al. 1998  
  > "HE 0515-4414 ($z=1.71$; Reimers et al. 1998)" (Introduction); "05:17:07.614" (Table 1); "-44:10:55.64" (Table 1)

## Data provenance

- ALMA projects: 2016.1.00309.S
- bands: Band 4  
  > "The peak intensity of the thermal SZE decrement is seen at $\approx 130$ GHz (Sunyaev & Zeldovich 1972), which lies in ALMA band-4." (ALMA)
- frequencies and spectral setup: Single pointing on the quasar; four 2 GHz basebands centred at 133, 135, 145 and 147 GHz  
  > "Our observations were of a single pointing centered on the quasar using four 2 GHz basebands centered at 133, 135, 145, and 147 GHz." (ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Two scheduling blocks: one executed once in a relatively large configuration (~0.7 arcsec) to measure point sources, one executed 14 times in a compact configuration (~2.7 arcsec)  
  > "Two scheduling blocks were made: one executed once in a relatively large configuration" (ALMA); "one executed 14 times in a compact configuration" (ALMA)
- baselines: _not stated_
- angular resolution: ~0.7 arcsec (large configuration); ~2.7 arcsec (compact configuration)  
  > "delivering $\theta_{\rm FWHM}$ $\approx$0.7$''$) to measure the point source contribution" (ALMA); "delivering $\theta_{\rm FWHM}$ $\approx$2.7$''$) to maximize our response to the SZE" (ALMA)
- max recoverable scale: _not stated_
- sensitivity: Natural weighting RMS 3.5 uJy/beam; tapered image RMS 6.6 uJy/beam  
  > "with an RMS of $\sigma =$ 3.5 $\mu$Jy beam$^{-1}$" (ALMA); "produced an image with $\sigma =$ 6.6 $\mu$Jy beam$^{-1}$" (ALMA)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PI observations ("Our observations")  
  > "Our observations were of a single pointing centered on the quasar" (ALMA)
- Other facility **Spitzer Space Telescope (IRAC 3.6 and 4.5 um)**: NIR imaging from DDT program PID 13221, used for host and environment  
  > "*Spitzer* observations were obtained in a DDT program (PID 13221)." (Optical and Infrared)
- Other facility **Gemini (GMOS, FLAMINGOS-2)**: Z, J and Ks imaging, program GS-2017B-FT-12  
  > "Gemini fast turnaround observations were obtained in program GS-2017B-FT-12 using the GMOS and FLAMINGOS-2 instruments." (Optical and Infrared)
- Other facility **HST WFC3 (archival)**: F140W/F160W imaging and G141 grism spectra from program 14594  
  > "*HST* observations of the field of HE 0515-4414 from program 14594 (P.I. R. Bielby) using the WFC3 instrument were recently made available in the *HST* archive." (Optical and Infrared)
- External data: 2MASS J-band continuum flux for the black hole mass estimate  
  > "flux from 2MASS $J$-band data (Skrutskie et al. 2006) using the formulation of Bennert et al. (2015)." (Optical and Infrared) [from Skrutskie et al. 2006 (ref: 2006AJ....131.1163S)]
- External data: Poor cluster at z=0.28 in the field, mass 6e12 Msun  
  > "Bielby et al. (2017) find a poor cluster at $z=0.28$ in the field based on absorption lines in the spectrum of the quasar and follow-up integral field spectroscopy." (The quasar host galaxy and its environment) [from Bielby et al. 2017 (ref: 2017MNRAS.468.1373B)]
- External data: SUMSS 843 MHz radio upper limit (<6 mJy)  
  > "HE 0515$-$4414 is undetected in the cm radio ($<$6 mJy at 843 MHz in the SUMSS survey, Mauch et al. 2003" (Thermal Plus Kinetic SZE Model) [from Mauch et al. 2003 (ref: 2003MNRAS.342.1117M)]
- External data: Quasar redshift z=1.71  
  > "HE 0515-4414 ($z=1.71$; Reimers et al. 1998)" (Introduction) [from Reimers et al. 1998 (ref: 1998A&A...334...96R)]
- Simulation/model as data: Rowe & Silk (2011) self-similar wind bubble model (based on Weaver et al. 1977), including its y profile in Figure 1, used to relate R and y_max to L_W and t  
  > "We base our treatment of the expansion of the wind bubble on the model in RS11, which uses the self-similar stellar wind bubble solution of Weaver et al. (1977)." (Thermal SZE Model); "Comparison to the $y$ profile in Figure 1 in RS11 shows that the gentle pressure increase in the outer regions of the bubble leads to a correction of 8%." (Thermal SZE Model)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline  
  > "Calibration of the data was performed with the ALMA pipeline." (ALMA (footnote 1))
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~5% amplitude calibration accuracy  
  > "A standard calibration strategy was used resulting in an amplitude calibration accuracy of $\approx 5$%" (ALMA)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "No clear signal was readily apparent in the naturally-weighted map" (ALMA)
- uv taper: Taper chosen to give a beam best matched to the signal size (6.7x6.4 arcsec); also tapered to 20 arcsec when searching for SZE at the quasar  
  > "The taper with a beam best matched to the size of the signal" (ALMA); "we detect no SZE from the quasar (even after tapering the beam to 20$''$)" (Thermal Plus Kinetic SZE Model)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Point-source models of the quasar and sources A1, A3, A5 subtracted in the uv-plane  
  > "the subtraction of point source models in the $uv$-plane" (ALMA)
- line free channels: _not stated_
- primary beam correction: 12% primary beam correction applied to decrement peak  
  > "After a 12% correction for the response of the primary beam, this peak value of the decrement becomes $-25.9 \, \mu$Jy." (ALMA)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: Natural: 3.2x2.3 arcsec, PA 106 deg; tapered: 6.7x6.4 arcsec, PA 110 deg  
  > "a synthesized beam of $\theta_{\rm FWHM} =$ 3.2$''$$\times$2.3$''$ at a position angle of PA = 106$^{\circ}$" (ALMA); "$\theta_{\rm FWHM} =$ 6.7$''$$\times$6.4$''$ at PA $= 110^{\circ}$" (ALMA)
- final rms: 3.5 uJy/beam (natural); 6.6 uJy/beam (tapered)  
  > "with an RMS of $\sigma =$ 3.5 $\mu$Jy beam$^{-1}$" (ALMA); "produced an image with $\sigma =$ 6.6 $\mu$Jy beam$^{-1}$" (ALMA)

### Inherited from earlier work

- Wind bubble expansion model and radius/y relations (equations 6 & 7 of RS11), including cooling prescription  
  > "Then, equations (6) & (7) in RS11 imply that the outer radius of the SZE bubble is:" (Thermal SZE Model); "RS11 give a prescription for estimating the cooling in their model." (Thermal Plus Kinetic SZE Model) [from Rowe & Silk 2011 (RS11) (ref: 2011MNRAS.412..905R)]
- Self-similar stellar wind bubble solution  
  > "uses the self-similar stellar wind bubble solution of Weaver et al. (1977)." (Thermal SZE Model) [from Weaver et al. 1977 (ref: 1977ApJ...218..377W)]
- SZE intensity change formula including thermal and kinetic terms  
  > "The change in the intensity of the CMB due to the SZE is given by (e.g. Sazonov & Sunyaev 1998):" (Interpretation of the SZE Signal) [from Sazonov & Sunyaev 1998 (ref: 1998AstL...24..553S)]
- Black hole mass formulation from Hbeta width and continuum  
  > "using the formulation of Bennert et al. (2015)." (Optical and Infrared) [from Bennert et al. 2015 (ref: 2015ApJ...809...20B)]
- Equipartition time between protons and electrons  
  > "The equipartition time between protons and electrons is short, $\approx 4000$ yr (e.g., Wong & Sarazin 2009)." (Thermal Plus Kinetic SZE Model) [from Wong & Sarazin 2009 (ref: WS09)]

### Not stated but needed to reproduce (our reading)

- CASA and ALMA pipeline versions
- Imaging task, cell size, image size and deconvolution/cleaning settings
- Exact uv-taper value used for the 6.7x6.4 arcsec image
- How the point-source fluxes in Table 1 were fitted (which SB, joint fit, uvmodelfit or other) and whether spectral index was modelled across 133-147 GHz
- Configuration names, baselines, time on source and observing dates
- Method for measuring bubble radius, peak offset and outer edge, and the beam-correction procedure
- IGM density / quasar bias and halo over-density values adopted in the RS11 model
- Mean molecular weight mu and exact numerical solution procedure for the tSZE+kSZE model (velocity sign and projection)
- How the 3.5 sigma significance was assessed (e.g. noise statistics in tapered map, number of independent beams searched)
- Source of the bolometric luminosity 1.3e15 Lsun
- Frequency adopted for converting flux density to brightness temperature

## Analysis recipe

1. **calibrate ALMA data**: Standard calibration with the ALMA pipeline  
  > "Calibration of the data was performed with the ALMA pipeline." (ALMA (footnote 1))
   - software: ALMA pipeline
   - fitting: _not stated_
   - validation: _not stated_
2. **remove compact sources**: Subtract point source models of the quasar and sources A1, A3, A5 in the uv-plane; large-configuration data used to measure point source contribution  
  > "Fortunately, all sources were unresolved in the smaller configuration data, and the subtraction of point source models in the $uv$-plane" (ALMA); "Point source emission model subtracted from the ALMA data" (Table 1)
   - parameter: Sources brighter than 20 uJy subtracted  
  > "the three other bright ($>20\, \mu$Jy) sources in the field (A1, A3, and A5" (ALMA)
   - assumption: Sources unresolved in compact data  
  > "all sources were unresolved in the smaller configuration data" (ALMA)
   - fitting: _not stated_
   - validation: Possible residual diffuse emission from A5 noted  
  > "with the possible exception of a small amount of diffuse extended emission associated with the brightest source, A5." (ALMA)
3. **image and detect SZE decrement**: Natural-weighted imaging, then uv-tapering to match signal size; measure decrement and apply primary beam correction  
  > "so tapering was applied to improve the surface brightness sensitivity of the image." (ALMA)
   - parameter: Tapered beam 6.7x6.4 arcsec, rms 6.6 uJy/beam  
  > "$\theta_{\rm FWHM} =$ 6.7$''$$\times$6.4$''$ at PA $= 110^{\circ}$" (ALMA)
   - fitting: _not stated_
   - validation: Corroborated by extended [OIII] emission at same position angle; no SZE at quasar position even with 20 arcsec taper  
  > "The SZE detection is corroborated by the presence of extended emission line gas at the same position angle as the wind." (abstract)
4. **characterise host, warm wind and black hole mass**: Reduce Gemini/HST/Spitzer imaging; extract HST grism spectra; BH mass from Hbeta width and 2MASS J continuum  
  > "The broad-band images were combined using astrodrizzle, and the aXe software (Kümmel et al. 2009) was used to extract the grism spectra." (Optical and Infrared); "We used the *HST* grism spectrum of the quasar to estimate the mass of the black hole" (Optical and Infrared)
   - software: IRAF (Gemini/GMOS package), astrodrizzle, aXe
   - parameter: Hbeta width 9440 km/s  
  > "based on the width of the H$\beta$ line (9440 km s$^{-1}$)" (Optical and Infrared)
   - fitting: _not stated_
   - validation: _not stated_
5. **check for cluster/group contamination**: Use NIR imaging and literature cluster to argue against ICM/IGrM contamination  
  > "The lack of any other obvious group or cluster in the field argues against significant contamination of the SZE signal" (The quasar host galaxy and its environment)
   - fitting: _not stated_
   - validation: _not stated_
6. **convert decrement to y, pressure and enthalpy**: Pure thermal SZE: decrement to Compton y, electron pressure, enthalpy (5/2) n k T V  
  > "The minimum amount of energy injected into the bubble by the wind is given by the enthalpy" (Thermal SZE Model)
   - parameter: Bubble projected radius 3.9 arcsec = 33 kpc  
  > "The average projected radius of the bubble is $r \approx 3.9\ensuremath{''} = 33$ kpc." (Interpretation of the SZE Signal)
   - assumption: n ~ 1.92 n_e; equipartition of ions and electrons (T = T_e)  
  > "we assume equipartition of ions and electrons, so that $T = T_e$" (Thermal SZE Model)
   - assumption: LambdaCDM H0=70, Om=0.3, OL=0.7  
  > "We assume a $\Lambda$ CDM cosmology with" (Introduction)
   - fitting: _not stated_
   - validation: _not stated_
7. **conical RS11 thermal-SZE bubble model**: Solve RS11 radius and y_max relations for L_W and t in a conical geometry; derive shock speed and temperature  
  > "Equations ([\[eqn:radius\]](#eqn:radius)) and ([\[eqn:ymax\]](#eqn:ymax)) are two relations with two unknowns." (Thermal SZE Model)
   - parameter: Cone half angle 30 deg; f_Omega ~0.067  
  > "We estimate the half angle of the cone in our system to be $\theta = 30^{\circ}$" (Thermal SZE Model)
   - parameter: Outflow axis at 45 deg to line of sight  
  > "We further assume that the axis of the outflow is at an angle of 45$^{\circ}$ to the outward extension of our line of sight." (Thermal SZE Model)
   - assumption: Negligible cooling; IGM density from quasar bias and halo over-density; cone expands as portion of spherical outflow  
  > "The first is that cooling of the hot phase gas is negligible." (Thermal SZE Model); "We assume that the conical bubble expands in the same manner that it would as a portion of a spherically symmetric outflow." (Thermal SZE Model)
   - assumption: Strong shock jump condition  
  > "The temperature behind the shock front, $T_s$, is given by the strong shock jump condition" (Thermal SZE Model)
   - fitting: Analytic solution of two equations  
  > "Equations ([\[eqn:radius\]](#eqn:radius)) and ([\[eqn:ymax\]](#eqn:ymax)) are two relations with two unknowns." (Thermal SZE Model)
   - validation: _not stated_
8. **thermal plus kinetic SZE model**: Add kSZE term to y_max relation to explain one-sided decrement; re-solve for L_W and t  
  > "We thus consider a model in which the observed SZE decrement is due to significant contributions from both the tSZE and kSZE." (Thermal Plus Kinetic SZE Model)
   - assumption: Outflow intrinsically one-sided for tabulated values  
  > "Assumes an intrinsically one-sided outflow and should be doubled for a two-sided outflow." (Table 2)
   - fitting: _not stated_
   - validation: Agreement of total energy among three methods  
  > "the fair agreement in the total energy estimate between the three different methods (total enthalpy, tSZE only and kSZE+tSZE) suggests that our estimate of that quantity at least is fairly robust." (Thermal Plus Kinetic SZE Model)
9. **check cooling, equipartition and starburst origin**: RS11 bremsstrahlung cooling prescription; equipartition time; starburst wind energetics  
  > "The relatively long lifetime of the wind bubble means that the possibility of cooling (dominated by bremsstrahlung) needs to be considered." (Thermal Plus Kinetic SZE Model)
   - assumption: Mass loading factor unity, wind velocity 1000 km/s for starburst case  
  > "assuming a mass loading factor of unity and a wind velocity of 1000 km s$^{-1}$" (Thermal Plus Kinetic SZE Model)
   - fitting: _not stated_
   - validation: _not stated_
10. **compare wind power with quasar output and theory**: Ratio of wind luminosity to bolometric luminosity and of E_W to total radiated energy of BH  
  > "we can compare $E_{\rm W}$ to the total radiative energy of the black hole (assuming a radiative efficiency of $\eta=0.1$)." (Discussion)
   - assumption: Radiative efficiency eta = 0.1  
  > "assuming a radiative efficiency of $\eta=0.1$" (Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **ALMA pipeline** : Calibration of ALMA data  
  > "Calibration of the data was performed with the ALMA pipeline." (ALMA (footnote 1))
- **IRAF (Gemini GMOS/IRAF package)** : Reduction of GMOS and FLAMINGOS-2 imaging  
  > "We used the standard GMOS data reduction package in IRAF to subtract the bias, apply the flat field, and coadd the final images." (Optical and Infrared)
- **astrodrizzle** : Combining HST broad-band images  
  > "The broad-band images were combined using astrodrizzle" (Optical and Infrared)
- **aXe** : Extracting HST grism spectra  
  > "the aXe software (Kümmel et al. 2009) was used to extract the grism spectra." (Optical and Infrared)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Quasar point source flux density (Band 4) | 66.2 | not stated | uJy | 2 | 66.2 |
| SZE decrement peak in tapered image | -23.1 | 3.5 sigma significance (sigma = 6.6 uJy/beam) | uJy | 3 | recovers an apparent dip of flux density of $-23.1\,\mu$Jy, significant at the 3.5$\sigma$ level, to the SW of the quasar position. |
| Primary-beam-corrected decrement peak | -25.9 | not stated | uJy | 3 | this peak value of the decrement becomes $-25.9 \, \mu$Jy. |
| Peak brightness temperature change | -37.7 | not stated | uK | 6 | corresponds to a brightness temperature change of $\Delta T_{\rm b,peak} = -37.7$ $\mu$K. |
| Outer edge distance of bubble from QSO (projected) | 108 | not stated | kpc | 6 | The distance from the QSO to the outer edge of the bubble is about $R  \approx 12.8\ensuremath{''} = 108$ kpc. |
| Compton parameter y (pure thermal) | 2.08e-5 | not stated | dimensionless | 6 | this gives a Compton parameter $y=\tau k_{\rm B} T_{\rm e}/(m_{\rm e}c^2) \approx 2.08  \times 10^{-5}$. |
| Electron pressure in bubble | 1.26e-11 | not stated | Pa | 6 | \approx 1.26 \times 10^{-11}$ Pa. |
| Bubble enthalpy E_Bub | 2.67e53 | not stated | W (as printed) | 6 | E_{\rm Bub} \approx 2.67 \times 10^{53} |
| Wind kinetic power L_W (tSZE only / tSZE+kSZE) | 1.70 / 0.429 | not stated | 10^11 Lsun | 7 | tSZE only / 1.70 / 8.13 / 1.68 / 807 / 0.91 / 0.95; tSZE plus kSZE / 0.429 / 12.87 / 0.67 / 510 / 0.36 / 1.50 |
| Bubble age t (tSZE only / tSZE+kSZE) | 8.13 / 12.87 | not stated | 10^7 yr | 8 | tSZE plus kSZE / 0.429 / 12.87 / 0.67 / 510 / 0.36 / 1.50 |
| Wind energy E_W (tSZE only / tSZE+kSZE) | 1.68 / 0.67 | not stated | 10^53 J | 8 | tSZE only / 1.70 / 8.13 / 1.68 / 807 / 0.91 / 0.95 |
| Shock speed (tSZE only / tSZE+kSZE) | 807 / 510 | not stated | km/s | 8 | tSZE plus kSZE / 0.429 / 12.87 / 0.67 / 510 / 0.36 / 1.50 |
| Fraction of decrement due to kSZE in combined model | 60 | not stated | % | 8 | In this model, about 60% (40%) of the SZE decrement is due to the kSZE (tSZE). |
| Electron density in bubble | 0.16 | not stated | cm^-3 | 9 | The average pressure in the bubble implies $n_e \approx 0.16$ cm$^{-3}$. |
| Cooling time | ~0.6 | not stated | Gyr | 9 | This corresponds to a cooling time of $\sim$0.6 Gyr, suggesting that cooling effects can be ignored. |
| Black hole mass | 4.3e10 | not stated | Msun | 4 | $M_{\bullet}\approx 4.3\times 10^{10}\,M_{\odot}$ |
| Wind luminosity as fraction of bolometric luminosity | 0.003 | not stated | % | 10 | it is only a small fraction ($\approx 0.003$%) of the bolometric luminosity of the quasar |
| E_W / (eta M_BH c^2) | 0.01 (0.02 if two-sided) | not stated | % | 10 | This fraction, $E_{\rm W}/(\eta M_{\bullet} c^2)\approx 0.01$% (0.02% if the wind is two-sided), is still low compared to the models. |
| Starburst SFR that could produce the signal | ~500 for 1.3e8 yr | not stated | Msun/yr | 9 | a star formation rate of approximately $500 \, M_\odot$ yr$^{-1}$ sustained for $1.3 \times 10^8$ yr could produce our observed signal. |

## Qualitative findings

- The SZE decrement appears only on the SW side of the quasar, explained naturally by combined tSZE and kSZE  
  > "Our detection appears on only one side of the quasar, consistent with the SZE signal arising from a combination of thermal and kinetic contributions." (abstract)
- Extended [OIII] emission with velocity gradient in C1 is consistent with a warm wind component  
  > "This is consistent with a warm component to the" (The quasar host galaxy and its environment)
- A starburst origin for the wind cannot currently be ruled out  
  > "In the absence of constraints on the star formation rate in this object, we cannot currently rule out a starburst origin." (Thermal Plus Kinetic SZE Model)

## Claim tuples

- H: The hot thermal wind bubble of a hyperluminous quasar produces a detectable SZE decrement with ALMA | E: Band 4 compact-configuration imaging with point-source subtraction and uv tapering | R: -23.1 uJy decrement at 3.5 sigma SW of the quasar | F: Evidence for first detection of a quasar wind SZE bubble | **partially**
- H: The one-sided appearance results from kinetic SZE adding/cancelling with thermal SZE | E: Conical RS11 bubble model with combined tSZE+kSZE | R: ~60% of decrement due to kSZE; L_W 0.429e11 Lsun, t 12.87e7 yr | F: Combined model gives a natural explanation for one-sided signal | **partially**
- H: Quasar wind kinetic luminosity is ~1-10% of bolometric luminosity as models predict | E: Compare derived L_W and E_W with L_bol and eta M_BH c^2 | R: ~0.003% of L_bol; E_W/(eta M c^2) ~0.01% | F: Wind luminosity is at the low end of theoretical predictions, ~0.01% of quasar luminosity | **refuted**
- H: Thermal wind bubbles persist long enough to provide feedback between quasar episodes | E: Estimate bubble age and bremsstrahlung cooling time | R: Age ~0.1 Gyr, cooling time ~0.6 Gyr | F: Such bubbles may provide feedback between bursts of quasar activity | **supported**

## Reasoning

- Why this data: Thermal SZE decrement peaks near 130 GHz (Band 4); compact ALMA configurations match the expected 1-10 arcsec signal size; most luminous radio-quiet quasar visible to ALMA chosen  
  > "The peak intensity of the thermal SZE decrement is seen at $\approx 130$ GHz (Sunyaev & Zeldovich 1972), which lies in ALMA band-4." (ALMA); "is well matched to the" (Introduction)
- Why this method: Tapering applied because no signal seen in natural map; taper improves surface brightness sensitivity  
  > "so tapering was applied to improve the surface brightness sensitivity of the image." (ALMA)
- Alternative: Intrinsically one-sided outflow or counter-flow blocked by dense ISM as alternatives to kSZE explanation  
  > "There are a number of possible explanations, including an intrinsically one-sided outflow, or the counter-flow being blocked by a higher ISM density in its path." (Thermal Plus Kinetic SZE Model)
- Alternative: Contamination by foreground z=0.28 cluster rejected because its mass is too small  
  > "The estimated mass of this cluster, $6\times 10^{12}M_{\odot}$ is much too small for it to contribute to the observed SZE though." (The quasar host galaxy and its environment)
- Alternative: Starburst-driven wind considered and not excluded  
  > "Given the relatively low power of the wind, it is also worth investigating whether it can be produced by a starburst in the quasar host galaxy." (Thermal Plus Kinetic SZE Model)
- How they decided it was enough: _not stated_
- Limitation (authors): RS11 model is spherically symmetric whereas outflow is not  
  > "Third, the model is spherically symmetric, which our outflow clearly is not." (Thermal SZE Model)
- Limitation (authors): Strong shock assumption may fail in a massive halo  
  > "the assumption of a strong shock may not be valid." (Thermal Plus Kinetic SZE Model)
- Limitation (authors): Single object; more needed  
  > "We emphasize though that this is only a single object, and that studies of further objects are needed to confirm this in the general quasar population." (Discussion)
- Limitation (authors): Possible residual diffuse emission from A5 after subtraction  
  > "with the possible exception of a small amount of diffuse extended emission associated with the brightest source, A5." (ALMA)
- Limitation (authors): Radio AGN contribution not constrained  
  > "Further radio continuum observations are therefore needed to better constrain any radio AGN activity that might be contributing to feedback." (Thermal Plus Kinetic SZE Model)
- Caveat (inferred, ours): A 3.5 sigma single-peak detection in a tapered map, chosen a posteriori, carries look-elsewhere risk; no noise-statistics or jackknife test is shown
- Caveat (inferred, ours): Taper was tuned to the signal size, which can inflate significance
- Caveat (inferred, ours): Residual extended emission from the bright A5 source (188 uJy) near the decrement could bias it
- Caveat (inferred, ours): Cone half-angle and 45 deg inclination are assumed, not measured; L_W and t depend on them
- Caveat (inferred, ours): The energy formula is printed with units of W, apparently meaning J

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Project code 2016.1.00309.S given; public availability not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00309.S." (Acknowledgments)
- Missing: uv-taper value and imaging parameters (cell, image size, deconvolution)
- Missing: CASA/pipeline versions
- Missing: Point-source fitting procedure
- Missing: Method for measuring bubble geometry and beam correction
- Missing: RS11 model input parameters (IGM density, bias, mu)
- Missing: Details of solving the kSZE+tSZE model
- Data volume (inferred): 15 Band 4 executions (1 extended, 14 compact) with 4 continuum basebands; likely tens of GB of raw data
- Score (inferred): 5/5, Observational setup and key image numbers are given, but the imaging parameters (taper, cleaning) and the modelling inputs are thin. The detection is marginal and sensitive to these choices.
- Rediscovery candidate: yes, The project code is printed and the archive links the data. The main numbers (decrement, rms, beams, y and model parameters) are numeric and can be recomputed from the formulas given, though the taper must be re-tuned.

## Links

- Method: Rowe & Silk 2011 (RS11) (ref: 2011MNRAS.412..905R) (Wind bubble SZE model and cooling prescription)
- Method: Weaver et al. 1977 (ref: 1977ApJ...218..377W) (Self-similar wind bubble solution)
- Method: Sazonov & Sunyaev 1998 (ref: 1998AstL...24..553S) (SZE intensity formula)
- Method: Bennert et al. 2015 (ref: 2015ApJ...809...20B) (Black hole mass formulation)
- Method: Kümmel et al. 2009 (ref: 2009PASP..121...59K) (aXe grism extraction software)
- Companion: Bielby et al. 2017 (ref: 2017MNRAS.468.1373B) (Foreground cluster in the HE 0515-4414 field)
- Related: Spitzer DDT PID 13221
- Related: Gemini GS-2017B-FT-12
- Related: HST program 14594
- Related: 2MASS
- Related: SUMSS

## Checks

```json
{
 "quotes": 124,
 "quotes_ok": 124,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 19,
 "numeric_problems": 0,
 "fill": {
  "facts": 115,
  "stated": 77,
  "rate": 0.67
 },
 "evidence_ok": true
}
```

# WISDOM project - XI. Star formation efficiency in the bulge of the AGN-host Galaxy NGC 3169 with SITELLE and ALMA

`2022MNRAS.514.5035L` | Monthly Notices of the Royal Astronomical Society 2022 | first author: Lu, Anan | arXiv: 2206.03316 | DOI: 10.1093/mnras/stac1583

Card schema 1.0 | model gemini-4-argon | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars, star_formation
- Question: How does the star formation efficiency (and molecular gas depletion time) vary across the bulge of the AGN-host galaxy NGC 3169, and what physical mechanisms (AGN feedback, bulge morphology, or dynamics) govern it?  
  > "Here, we use spatially-resolved observations of warm ionised gas emission lines (H$\beta$, \[O iii\] $\lambda\lambda$4959,5007, \[N ii\] $\lambda\lambda$6548,6583, H$\alpha$ and \[S ii\] $\lambda\lambda$6716,6731) from the imaging Fourier transform spectrograph SITELLE at the Canada-France-Hawaii Telescope (CFHT) and cold molecular gas (^12^CO(2-1)) from the Atacama Large Millimeter/sub-millimeter Array (ALMA) to study the SFE in the bulge of the AGN-host galaxy NGC 3169." (Abstract); "To distinguish these different mechanisms in the inner regions of galaxies, we have initiated a project to measure the SFEs of galaxy bulges in a spatially-resolved manner, combining high-spatial resolution ^12^CO(2-1) measurements (by a cold gas indicator) from the Atacama Large Millimeter/sub-millimeter Array (ALMA) with ionised hydrogen emission-line measurements (by a SFR indicator) from the imaging Fourier transform spectrograph SITELLE at the Canada-France-Hawaii Telescope (CFHT)." (Introduction)
- Target **NGC 3169**: coordinates R.A. (J2000) = 10h14m15.05s, Dec. (J2000) = 3d27m57.90s  
  > "The observations were centred at R.A. (J2000)$=10^{\rm h}14^{\rm m}15.05s$ and Dec. (J2000)$=3^\circ27\ensuremath{'}57.90\ensuremath{''}$." (Ionised gas data); "NGC 3169 is an S(a) spiral galaxy at a distance $D=18.7$ Mpc, according to the NASA Extragalactic Database redshift-independent distance catalogue (cite: steer2016redshift)." (NGC 3169); "It has an inclination $i=54^\circ$, a position angle $PA=45^\circ$ and a systemic heliocentric velocity $V_{\rm sys}=1232$ km s$^{-1}$ (from the H i $21$-cm observations of (cite: lee2012pre), consistent with the best-fitting systemic velocity derived from our own CO data discussed in Section \[vfield\])." (NGC 3169); z/distance D = 18.7 Mpc; V_sys = 1232 km s^-1  
  > "The observations were centred at R.A. (J2000)$=10^{\rm h}14^{\rm m}15.05s$ and Dec. (J2000)$=3^\circ27\ensuremath{'}57.90\ensuremath{''}$." (Ionised gas data); "NGC 3169 is an S(a) spiral galaxy at a distance $D=18.7$ Mpc, according to the NASA Extragalactic Database redshift-independent distance catalogue (cite: steer2016redshift)." (NGC 3169); "It has an inclination $i=54^\circ$, a position angle $PA=45^\circ$ and a systemic heliocentric velocity $V_{\rm sys}=1232$ km s$^{-1}$ (from the H i $21$-cm observations of (cite: lee2012pre), consistent with the best-fitting systemic velocity derived from our own CO data discussed in Section \[vfield\])." (NGC 3169); distance from NASA Extragalactic Database redshift-independent distance catalogue (cite: steer2016redshift)  
  > "The observations were centred at R.A. (J2000)$=10^{\rm h}14^{\rm m}15.05s$ and Dec. (J2000)$=3^\circ27\ensuremath{'}57.90\ensuremath{''}$." (Ionised gas data); "NGC 3169 is an S(a) spiral galaxy at a distance $D=18.7$ Mpc, according to the NASA Extragalactic Database redshift-independent distance catalogue (cite: steer2016redshift)." (NGC 3169); "It has an inclination $i=54^\circ$, a position angle $PA=45^\circ$ and a systemic heliocentric velocity $V_{\rm sys}=1232$ km s$^{-1}$ (from the H i $21$-cm observations of (cite: lee2012pre), consistent with the best-fitting systemic velocity derived from our own CO data discussed in Section \[vfield\])." (NGC 3169)

## Data provenance

- ALMA projects: 2015.1.00598.S, 2016.2.00053.S
- bands: _not stated_
- frequencies and spectral setup: 230 GHz; 2015.1.00598.S: correlator window of 1.875 GHz (2450 km s^-1), intrinsic channel width 1.27 km s^-1 (977 kHz); 2016.2.00053.S: correlator window of 2 GHz  
  > "The intrinsic channel width was $1.27$ km s$^{-1}$ ($977$ kHz). The line was covered by a correlator window of $1.875$ GHz, equivalent to $2450$ km s$^{-1}$." (Molecular gas data); "The line was covered by a correlator window of $2$ GHz." (Molecular gas data)
- continuum bandwidth: _not stated_
- arrays: thirty-eight 12-m antennae and eight 7-m antennae  
  > "The first observation (2015.1.00598.S) obtained $605$ s on the source using thirty-eight $12$-m antennae, resulting in a primary beam (FWHM) of $27.4\ensuremath{''}$ and a maximum recoverable scale of $5.8\ensuremath{''}$." (Molecular gas data); "The second observation obtained $1120$ s on source using eight $7$-m antennae, that extended the primary beam (FWHM) to $45.7\ensuremath{''}$ and the maximum recoverable scale to $36.4\ensuremath{''}$." (Molecular gas data)
- configurations: C36-4 and 7M  
  > "The NGC 3169 molecular gas data used were obtained in the $^{12}$CO(2-1) line (230 GHz) using ALMA in January 2015 (configuration: C36-4; programme: 2015.1.00598.S; PI: Bureau) and January 2016 (configuration: 7M; programme: 2016.2.00053.S; PI: Liu), as part of the mm-Wave Interferometric Survey of Dark Object Masses (WISDOM) project (cite: onishi2017wisdom)." (Molecular gas data)
- baselines: _not stated_
- angular resolution: 0.99'' x 0.84'' (89 pc x 76 pc) at PA = -58 deg before smoothing; convolved to circular FWHM 1.1'' (99 pc); highest native resolution 0.58'' x 0.58'' (52 pc x 52 pc) with robust 0.5  
  > "The data were then imaged using the `CASA` task `tclean` (version 5.6.1), adopting a channel width of $2$ km s$^{-1}$, a Briggs’ weighting robust parameter of $2.0$ and a $uv$-taper of $0.7\ensuremath{''}$, thus achieving a synthesised beam size (FWHM) of $0.99\ensuremath{''}\times0.84\ensuremath{''}$ ($89$ pc$\times76$ pc) at a position angle of $-58^\circ$, roughly matching the seeing of the H$\alpha$ observations." (Molecular gas data); "Finally, we convolved this datacube spatially by a narrow and slightly elongated two-dimensional Gaussian, to achieve a perfectly circular synthesized beam of FWHM $1.1\ensuremath{''}$, thus perfectly matching the seeing of the H$\alpha$ observations." (Molecular gas data); "Stand-alone GMC analyses should however be performed at the highest angular resolution possible for the CO data, here $0.58\ensuremath{''}\times0.58\ensuremath{''}$ ($52$ pc$\times52$ pc), when adopting a more standard Briggs’ robust parameter of 0.5 and no taper." (Molecular gas data)
- max recoverable scale: 5.8'' (12-m) and 36.4'' (with 7-m)  
  > "The first observation (2015.1.00598.S) obtained $605$ s on the source using thirty-eight $12$-m antennae, resulting in a primary beam (FWHM) of $27.4\ensuremath{''}$ and a maximum recoverable scale of $5.8\ensuremath{''}$." (Molecular gas data); "The second observation obtained $1120$ s on source using eight $7$-m antennae, that extended the primary beam (FWHM) to $45.7\ensuremath{''}$ and the maximum recoverable scale to $36.4\ensuremath{''}$." (Molecular gas data)
- sensitivity: mean RMS noise level of 3.06 mJy beam^-1 per 2 km s^-1 channel  
  > "This produced our final fully calibrated and continuum-subtracted $^{12}$CO(2-1) datacube of NGC 3169, with a mean RMS noise level of $3.06$ mJy beam$^{-1}$ per $2$ km s$^{-1}$ channel, although we also performed primary beam correction for the imaging of moment maps." (Molecular gas data)
- time on source: 605 s (12-m) and 1120 s (7-m)  
  > "The first observation (2015.1.00598.S) obtained $605$ s on the source using thirty-eight $12$-m antennae, resulting in a primary beam (FWHM) of $27.4\ensuremath{''}$ and a maximum recoverable scale of $5.8\ensuremath{''}$." (Molecular gas data); "The second observation obtained $1120$ s on source using eight $7$-m antennae, that extended the primary beam (FWHM) to $45.7\ensuremath{''}$ and the maximum recoverable scale to $36.4\ensuremath{''}$." (Molecular gas data)
- observing dates: January 2015 and January 2016  
  > "The NGC 3169 molecular gas data used were obtained in the $^{12}$CO(2-1) line (230 GHz) using ALMA in January 2015 (configuration: C36-4; programme: 2015.1.00598.S; PI: Bureau) and January 2016 (configuration: 7M; programme: 2016.2.00053.S; PI: Liu), as part of the mm-Wave Interferometric Survey of Dark Object Masses (WISDOM) project (cite: onishi2017wisdom)." (Molecular gas data)
- pi or archival as stated: PI: Bureau (2015.1.00598.S) and PI: Liu (2016.2.00053.S), WISDOM project  
  > "The NGC 3169 molecular gas data used were obtained in the $^{12}$CO(2-1) line (230 GHz) using ALMA in January 2015 (configuration: C36-4; programme: 2015.1.00598.S; PI: Bureau) and January 2016 (configuration: 7M; programme: 2016.2.00053.S; PI: Liu), as part of the mm-Wave Interferometric Survey of Dark Object Masses (WISDOM) project (cite: onishi2017wisdom)." (Molecular gas data)
- Line: 12CO (2-1) (230 GHz)
- Other facility **SITELLE at the Canada-France-Hawaii Telescope (CFHT)**: Optical imaging Fourier transform spectrograph datacubes (programme 20Bc25, 2020B semester) in SN3 (6480-6860 A, R~2000; [N II] 6548,6583, Halpha, [S II] 6716,6731) and SN2 (4840-5120 A, R~900; Hbeta, [O III] 4959,5007) with 0.31'' x 0.31'' spaxels and 1.1'' seeing.  
  > "NGC 3169 was observed with SITELLE (cite: drissen2019sitelle) at CFHT during the 2020B semester (programme number 20Bc25)." (Ionised gas data); "Two datacubes were obtained: one centred on the emission lines of \[N ii\]$\lambda6548$, H$\alpha$, \[N ii\]$\lambda6583$, \[S ii\]$\lambda6716$ and \[S ii\]$\lambda6731$ with the SN3 filter ($6480$–$6860$ Å) at a mean spectral resolution of $R\approx2000$; the other centred on the emission lines of H$\beta$, \[O iii\]$\lambda4959$ and \[O iii\]$\lambda5007$ with the SN2 filter ($4840$–$5120$ Å) at a mean spectral resolution $R\approx900$." (Ionised gas data)
- External data: Galaxy morphology SA(s)a pec  
  > "(1) Morphology of the galaxy taken from (cite: 1991rc3..book.....D)." (Table 1) [from (cite: 1991rc3..book.....D)]
- External data: Distance D = 18.7 Mpc  
  > "NGC 3169 is an S(a) spiral galaxy at a distance $D=18.7$ Mpc, according to the NASA Extragalactic Database redshift-independent distance catalogue (cite: steer2016redshift)." (NGC 3169) [from (cite: steer2016redshift)]
- External data: Inclination i = 54 deg, position angle PA = 45 deg, systemic heliocentric velocity V_sys = 1232 km s^-1, and H I gas mass (4.2 +/- 0.5) x 10^9 M_sun  
  > "It has an inclination $i=54^\circ$, a position angle $PA=45^\circ$ and a systemic heliocentric velocity $V_{\rm sys}=1232$ km s$^{-1}$ (from the H i $21$-cm observations of (cite: lee2012pre), consistent with the best-fitting systemic velocity derived from our own CO data discussed in Section \[vfield\])." (NGC 3169); "The H i gas mass of NGC 3169 is $(4.2\pm0.5)\times10^{9}$ M$_\odot$ (cite: lee2012pre)." (NGC 3169) [from (cite: lee2012pre)]
- External data: Stellar mass log(M_*/M_sun) = 10.84 and total star formation rate log(SFR/M_sun yr^-1) = 0.29  
  > "The ultraviolet and infrared images from the *Wide-field Infrared Survey Explorer* (*WISE*) and *Galaxy Evolution Explorer* (*GALEX*) missions (cite: leroy2019z) indicate a stellar mass of $\log (M_\star/{\rm M_\odot})\approx10.84$ and a star formation rate $\log(\rm SFR/{\rm M_\odot~yr^{-1}})\approx0.29$ within a central aperture of diameter $\approx19\ensuremath{'}$." (NGC 3169) [from (cite: leroy2019z)]
- External data: Stellar velocity dispersion sigma_* = 163 km s^-1  
  > "(8) Stellar velocity dispersion taken from (cite: heraudeau1999stellar)." (Table 1) [from (cite: heraudeau1999stellar)]
- External data: K_s-band effective radius R_e,KS = 85.7''  
  > "(11) $K_s$-band effective radius estimated from the $2~\mu$m all-sky survey (2MASS; (cite: jarrett20032mass))." (Table 1) [from 2MASS; (cite: jarrett20032mass)]
- External data: 2MASS K_s-band bulge-disc decomposition (m_bul = 7.52, m_disc = 8.42, bulge effective radius 15.7'' or 1.4 kpc, Sersic index ~4.17)  
  > "This galaxy has a dense bulge (with an effective radius $\approx1.4$ kpc and a Sérsic index of $\approx4.17$; from (cite: dong2006low)) and a low-luminosity AGN (LLAGN; e.g. (cite: ghosh2008low; mathur2008finding)), making it ideal for a deep investigation of various quenching mechanisms." (Introduction); "They reported bulge and disc $K_{\rm s}$-band integrated apparent magnitudes $m_{\rm bul}=7.52$ and $m_{\rm disc}=8.42$. The effective radius of the bulge component is $15.7\ensuremath{''}$ or $1.4$ kpc at our assumed distance." (NGC 3169) [from (cite: dong2006low)]
- External data: Eddington luminosity L_Edd ~ 10^46 erg s^-1 and Chandra X-ray properties of the LLAGN  
  > "(14) Estimated Eddington luminosity of the supermassive black hole, taken from (cite: ghosh2008low)." (Table 1) [from (cite: ghosh2008low)]
- Simulation/model as data: Hydrodynamical simulations of bulgeless galaxies and galaxies with bulges from Gensior et al. (2020, 2021) compared against observed radial SFE trends and sSFR.  
  > "In particular, (cite: gensior2020heart) and (cite: gensior2021elephant) simulated the influence of a bulge on the radial variations of the SFE." (Quenching from bulge dynamics); "Here, we attempt to compare the radial trend of $\Sigma_{\rm SFR}/\Sigma_{\rm H_2}$ of both our NGC 3169 data and simulations of galaxies with dense bulges." (Quenching from bulge dynamics)

## Processing

### Calibration

- pipeline or manual: pipeline  
  > "The raw ALMA data were reduced using the Common Astronomy Software Applications (`CASA`) pipeline (version 5.3), which automatically processes the data by performing basic flagging and calibration (cite: mcmullin2007casa)." (Molecular gas data)
- casa version: 5.3 (pipeline calibration) and 5.6.1 (tclean imaging)  
  > "The raw ALMA data were reduced using the Common Astronomy Software Applications (`CASA`) pipeline (version 5.3), which automatically processes the data by performing basic flagging and calibration (cite: mcmullin2007casa)." (Molecular gas data); "The data were then imaged using the `CASA` task `tclean` (version 5.6.1), adopting a channel width of $2$ km s$^{-1}$, a Briggs’ weighting robust parameter of $2.0$ and a $uv$-taper of $0.7\ensuremath{''}$, thus achieving a synthesised beam size (FWHM) of $0.99\ensuremath{''}\times0.84\ensuremath{''}$ ($89$ pc$\times76$ pc) at a position angle of $-58^\circ$, roughly matching the seeing of the H$\alpha$ observations." (Molecular gas data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "The data were then imaged using the `CASA` task `tclean` (version 5.6.1), adopting a channel width of $2$ km s$^{-1}$, a Briggs’ weighting robust parameter of $2.0$ and a $uv$-taper of $0.7\ensuremath{''}$, thus achieving a synthesised beam size (FWHM) of $0.99\ensuremath{''}\times0.84\ensuremath{''}$ ($89$ pc$\times76$ pc) at a position angle of $-58^\circ$, roughly matching the seeing of the H$\alpha$ observations." (Molecular gas data)
- deconvolver: _not stated_
- weighting robust: Briggs' weighting robust = 2.0 (also mentions robust = 0.5 for highest angular resolution)  
  > "The data were then imaged using the `CASA` task `tclean` (version 5.6.1), adopting a channel width of $2$ km s$^{-1}$, a Briggs’ weighting robust parameter of $2.0$ and a $uv$-taper of $0.7\ensuremath{''}$, thus achieving a synthesised beam size (FWHM) of $0.99\ensuremath{''}\times0.84\ensuremath{''}$ ($89$ pc$\times76$ pc) at a position angle of $-58^\circ$, roughly matching the seeing of the H$\alpha$ observations." (Molecular gas data); "Stand-alone GMC analyses should however be performed at the highest angular resolution possible for the CO data, here $0.58\ensuremath{''}\times0.58\ensuremath{''}$ ($52$ pc$\times52$ pc), when adopting a more standard Briggs’ robust parameter of 0.5 and no taper." (Molecular gas data)
- uv taper: 0.7''  
  > "The data were then imaged using the `CASA` task `tclean` (version 5.6.1), adopting a channel width of $2$ km s$^{-1}$, a Briggs’ weighting robust parameter of $2.0$ and a $uv$-taper of $0.7\ensuremath{''}$, thus achieving a synthesised beam size (FWHM) of $0.99\ensuremath{''}\times0.84\ensuremath{''}$ ($89$ pc$\times76$ pc) at a position angle of $-58^\circ$, roughly matching the seeing of the H$\alpha$ observations." (Molecular gas data)
- cell size: 0.31'' x 0.31'' (matched to SITELLE spaxel size; also states ~35 pc CO spaxel size in Section 4.4)  
  > "The field of view (FOV) is $11\ensuremath{'}\times11\ensuremath{'}$, resulting in a mean spaxel size on the sky of $0.31\ensuremath{''}\times0.31\ensuremath{''}$ (or $28\times28$ pc$^2$)." (Ionised gas data); "Sky coordinates and spaxel size of the datacube were also matched to those of the SITELLE datacubes." (Molecular gas data); "As a comparison, we also estimate the molecular gas virial parameter on the cloud scale, which is equivalent to the CO spaxel size of $\approx35$ pc." (Virial parameters)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub in the uv plane over the full line-free bandwidth  
  > "Continuum emission was detected, measured over the full line-free bandwidth, and then subtracted from the data in the $uv$ plane using the `CASA` task `uvcontsub`." (Molecular gas data)
- line free channels: _not stated_
- primary beam correction: performed for the imaging of moment maps  
  > "This produced our final fully calibrated and continuum-subtracted $^{12}$CO(2-1) datacube of NGC 3169, with a mean RMS noise level of $3.06$ mJy beam$^{-1}$ per $2$ km s$^{-1}$ channel, although we also performed primary beam correction for the imaging of moment maps." (Molecular gas data)
- array combination: concat in CASA (combining 12-m C36-4 and 7-m observations)  
  > "The two ALMA observations were then combined using the `CASA` task `concat`." (Molecular gas data)
- smoothing: convolved spatially by a narrow and slightly elongated 2D Gaussian to achieve a circular beam of FWHM 1.1''  
  > "Finally, we convolved this datacube spatially by a narrow and slightly elongated two-dimensional Gaussian, to achieve a perfectly circular synthesized beam of FWHM $1.1\ensuremath{''}$, thus perfectly matching the seeing of the H$\alpha$ observations." (Molecular gas data)
- final beam: 0.99'' x 0.84'' at PA -58 deg before convolution; circular FWHM 1.1'' (99 pc) after convolution  
  > "The data were then imaged using the `CASA` task `tclean` (version 5.6.1), adopting a channel width of $2$ km s$^{-1}$, a Briggs’ weighting robust parameter of $2.0$ and a $uv$-taper of $0.7\ensuremath{''}$, thus achieving a synthesised beam size (FWHM) of $0.99\ensuremath{''}\times0.84\ensuremath{''}$ ($89$ pc$\times76$ pc) at a position angle of $-58^\circ$, roughly matching the seeing of the H$\alpha$ observations." (Molecular gas data); "Finally, we convolved this datacube spatially by a narrow and slightly elongated two-dimensional Gaussian, to achieve a perfectly circular synthesized beam of FWHM $1.1\ensuremath{''}$, thus perfectly matching the seeing of the H$\alpha$ observations." (Molecular gas data)
- final rms: 3.06 mJy beam^-1 per 2 km s^-1 channel  
  > "This produced our final fully calibrated and continuum-subtracted $^{12}$CO(2-1) datacube of NGC 3169, with a mean RMS noise level of $3.06$ mJy beam$^{-1}$ per $2$ km s$^{-1}$ channel, although we also performed primary beam correction for the imaging of moment maps." (Molecular gas data)

### Inherited from earlier work

- Halpha extinction correction method and reddening curve  
  > "following (cite: nelson2016spatially), where $k(\lambda)$ is the reddening curve of (cite: fitzpatrick1986average) and $k(\lambda_{\rm H\alpha})$ and $k(\lambda_{\rm H\beta})$ are evaluated at the wavelengths of H$\alpha$ and H$\beta$, respectively." (SFR surface densities) [from (cite: nelson2016spatially); (cite: fitzpatrick1986average)]
- Halpha luminosity to SFR conversion relation  
  > "This extinction-corrected H$\alpha$ flux is converted to a SFR using the relation of (cite: kennicutt2012star):" (SFR surface densities) [from (cite: kennicutt2012star)]
- H II region identification algorithm from SITELLE Halpha data  
  > "To take a more in-depth look at the star formation on cloud scales, we identified H ii regions using the SITELLE H$\alpha$ data and algorithms developed by (cite: rousseau2018ngc628), summarised below." (Virial parameters) [from (cite: rousseau2018ngc628)]
- Cloud-scale molecular gas virial parameter calculation  
  > "The molecular gas virial parameter ($\alpha_{\rm vir,\,H_2}$) can be calculated following the method from (cite: rosolowsky2006bias) that is recently adopted by (cite: sun2020molecular):" (Virial parameters) [from (cite: rosolowsky2006bias); (cite: sun2020molecular)]
- Statistical analysis of CO and Halpha snapshots to infer GMC lifecycle timescales and separation length using the HEISENBERG code and Fourier filtering of diffuse emission  
  > "To infer these quantities, we adopt here the methods developed by (cite: 2018MNRAS.479.1866K) and use the associated `HEISENBERG` code." (Molecular cloud timescales); "More specifically, the emission in each line is transformed into Fourier space, and a Gaussian high-pass filter is then applied centred at zero Fourier frequency, using the best-fitting $\lambda$ (the separation lengthscale) in an iterative process (cite: hygate2019uncertainty)." (Molecular cloud timescales) [from (cite: 2018MNRAS.479.1866K); (cite: hygate2019uncertainty)]

### Not stated but needed to reproduce (our reading)

- Exact frequency ranges / channel selections used as line-free channels in uvcontsub
- tclean stopping threshold, niter, deconvolver, and masking strategy during ALMA cube and continuum imaging
- Relative weighting of 12-m and 7-m visibilities during concat/tclean
- Method and clipping thresholds used to generate the CO moment-0, moment-1, and moment-2 maps
- Exact ring radii, ring width, and fixed dynamical centre / inclination values adopted in the 3DBarolo fit
- Specific input parameter values for the HEISENBERG code (besides t_star,ref = 4.3 Myr)

## Analysis recipe

1. **Calibrate, combine, continuum-subtract, and image ALMA CO(2-1) data**: Calibrate raw ALMA data with the CASA pipeline, combine 12-m and 7-m datasets with concat, subtract continuum in the uv plane using uvcontsub over line-free bandwidth, image with tclean at 2 km s^-1 (and 15 km s^-1 for kinematics) with Briggs robust=2.0 and 0.7'' uv-taper, convolve with a 2D Gaussian to a 1.1'' circular beam, and regrid to match SITELLE spaxels.  
  > "The raw ALMA data were reduced using the Common Astronomy Software Applications (`CASA`) pipeline (version 5.3), which automatically processes the data by performing basic flagging and calibration (cite: mcmullin2007casa). The two ALMA observations were then combined using the `CASA` task `concat`." (Molecular gas data); "The data were then imaged using the `CASA` task `tclean` (version 5.6.1), adopting a channel width of $2$ km s$^{-1}$, a Briggs’ weighting robust parameter of $2.0$ and a $uv$-taper of $0.7\ensuremath{''}$, thus achieving a synthesised beam size (FWHM) of $0.99\ensuremath{''}\times0.84\ensuremath{''}$ ($89$ pc$\times76$ pc) at a position angle of $-58^\circ$, roughly matching the seeing of the H$\alpha$ observations." (Molecular gas data); "Finally, we convolved this datacube spatially by a narrow and slightly elongated two-dimensional Gaussian, to achieve a perfectly circular synthesized beam of FWHM $1.1\ensuremath{''}$, thus perfectly matching the seeing of the H$\alpha$ observations." (Molecular gas data)
   - software: CASA, concat, uvcontsub, tclean
   - parameter: channel width = 2 km s^-1 (and 15 km s^-1 for kinematics)  
  > "Finally, another datacube was produced following the same procedure but with a channel width of $15$ km s$^{-1}$, to enhance the S/N for the purpose of the gas kinematics analyses carried out in Section \[vfield\]." (Molecular gas data)
   - parameter: Briggs robust = 2.0, uv-taper = 0.7'', final circular beam FWHM = 1.1''  
  > "The data were then imaged using the `CASA` task `tclean` (version 5.6.1), adopting a channel width of $2$ km s$^{-1}$, a Briggs’ weighting robust parameter of $2.0$ and a $uv$-taper of $0.7\ensuremath{''}$, thus achieving a synthesised beam size (FWHM) of $0.99\ensuremath{''}\times0.84\ensuremath{''}$ ($89$ pc$\times76$ pc) at a position angle of $-58^\circ$, roughly matching the seeing of the H$\alpha$ observations." (Molecular gas data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Reduce SITELLE IFTS cubes and extract optical emission-line maps**: Reduce raw SITELLE interferograms with ORBS, calibrate wavelength using OH sky lines, subtract median sky spectrum from a 200x200 spaxel region, and fit sinc-Gauss emission line profiles per spaxel using ORCS with a 3-sigma detection threshold on Halpha+[N II] flux.  
  > "The data reduction was performed with the `ORBS` software developed for SITELLE (cite: martin2015orbs; martin2021data)." (Ionised gas data); "The emission lines in each spaxel were then fitted using the extraction software `ORCS` (cite: martin2015orbs)." (Ionised gas data); "A detection threshold was then applied based on the $3\sigma$ noise level of the H$\alpha$+\[N ii\] flux." (Ionised gas data)
   - software: ORBS, ORCS
   - parameter: sky region = 200 x 200 spaxels; detection threshold = 3 sigma on Halpha+[N II] flux  
  > "As a final pre-processing step, sky background subtraction was performed using a median sky spectrum extracted from a $200\times200$ spaxels region located far away from the galaxy disc." (Ionised gas data); "A detection threshold was then applied based on the $3\sigma$ noise level of the H$\alpha$+\[N ii\] flux." (Ionised gas data)
   - fitting: sinc-Gauss profile fitting in ORCS  
  > "Modelling the sinc-Gauss profile of the emission lines allows to measure velocity dispersions much smaller than the nominal spectral resolution, provided that the $S/N$ is sufficient (cite: martin2016optimal)." (Ionised gas data)
   - validation: Seeing measured to be 1.1'' from FWHM of Gaussian fits to foreground Gaia stars  
  > "The seeing was measured to be $1.1\ensuremath{''}$ (or $99$ pc) from the full-width at half-maxima (FWHM) of Gaussian fits to foreground stars from the Gaia catalogue (cite: lindegren2018gaia)." (Ionised gas data)
3. **Derive extinction-corrected SFR surface density map**: Compute Balmer decrement E(Hbeta-Halpha) where both Halpha and Hbeta are >=3 sigma, adopt nearest-neighbour A_Halpha where Hbeta is <3 sigma, correct F_Halpha for extinction, convert L_Halpha to SFR and divide by spaxel area.  
  > "We correct the observed H$\alpha$ fluxes ($F_{\rm H\alpha,obs}$) for extinction using the observed H$\beta$ fluxes ($F_{\rm H\beta,obs}$) and the assumed Balmer decrement described below." (SFR surface densities); "For each spaxel with a $3\sigma$ H$\alpha$ detection but no $3\sigma$ H$\beta$ detection, we adopt the H$\alpha$ extinction of the nearest reliable spaxel." (SFR surface densities); "The $\Sigma_{\rm SFR}$ is then calculated as the SFR within each spaxel divided by the spaxel area." (SFR surface densities)
   - parameter: 3 sigma detection threshold for Halpha and Hbeta  
  > "For each spaxel with both the H$\alpha$ and H$\beta$ lines satisfying the $3\sigma$ detection threshold, the "color excess" of H$\alpha$ over H$\beta$ is defined as" (SFR surface densities)
   - assumption: Intrinsic Balmer decrement (Halpha/Hbeta)_init = 2.86 for case B recombination at T = 10^4 K (Osterbrock & Ferland 2006)  
  > "where we assume $({\rm H\alpha}/{\rm H\beta})_{\rm init}=2.86$, as expected for the case B recombination at a temperature of $10^4$ K (cite: osterbrock2006astrophysics)." (SFR surface densities)
   - assumption: Fitzpatrick (1986) reddening curve k(lambda) and Kennicutt & Evans (2012) log(SFR) = log(L_Halpha) - 41.27 conversion with D = 18.7 Mpc  
  > "following (cite: nelson2016spatially), where $k(\lambda)$ is the reddening curve of (cite: fitzpatrick1986average) and $k(\lambda_{\rm H\alpha})$ and $k(\lambda_{\rm H\beta})$ are evaluated at the wavelengths of H$\alpha$ and H$\beta$, respectively." (SFR surface densities); "This extinction-corrected H$\alpha$ flux is converted to a SFR using the relation of (cite: kennicutt2012star): $$\begin{equation}
  \log({\rm SFR}\,/\,{\rm M}_\odot\,{\rm yr}^{-1})=\log(L_{\rm H\alpha}\,/\,{\rm ergs}\,{\rm s}^{-1})-41.27~,
\end{equation}$$" (SFR surface densities)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive molecular gas mass surface density map from CO(2-1)**: Divide CO(2-1) moment-0 flux by synthesised beam area in spaxels, convert F_CO(2-1) to luminosity L_CO(2-1), convert to M_H2 using M_H2/M_sun = 6.325 L_CO(2-1), and divide by spaxel area.  
  > "First, the CO flux ($F_{\rm CO(2-1)}$) within each spaxel is obtained from the moment-0 map fluxes (in Jy beam$^{-1}$ km s$^{-1}$) by dividing by the synthesised beam area in spaxels." (Molecular gas mass surface densities); "The complete conversion thus becomes $$\begin{equation}
  \frac{M_{\rm H_2}}{{\rm M}_\odot}=6.325\,\left(\frac{L_{\rm CO(2-1)}}{\rm K~km~s^{-1}~pc^2}\right).
\end{equation}$$ The molecular gas mass surface density is then calculated as $M_{\rm H_2}$ divided by the spaxel area." (Molecular gas mass surface densities)
   - assumption: CO(2-1)/CO(1-0) brightness temperature ratio = 0.8 and X_CO = 2.3 x 10^20 cm^-2 (K km s^-1)^-1 including helium  
  > "We adopt a CO(2-1)/CO(1-0) ratio of $0.8$ (in brightness temperature units), typical of spiral galaxies (cite: lamperti2020co), and $X_{\rm CO}=2.3\times10^{20}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$." (Molecular gas mass surface densities); "The mass contribution from helium is considered and included in the coefficient (cite: strong1988radial; bolatto2013co)." (Molecular gas mass surface densities)
   - fitting: _not stated_
   - validation: _not stated_
5. **Classify ionisation mechanisms per spaxel using BPT diagnostics and compute depletion times**: Classify spaxels into H II (star-forming), composite, and AGN-ionised regions using O3N2 ([O III]/Hbeta vs [N II]/Halpha) and O3S2 ([O III]/Hbeta vs [S II]/Halpha) BPT diagrams with Kewley et al. (2006) and Law et al. (2021) demarcation lines, then compute depletion time tau_dep = Sigma_H2 / Sigma_SFR per spaxel and in radial annuli (width 200 pc, step 100 pc).  
  > "We applied the classification lines of (cite: kewley2006host) to separate and thus uniquely identify H ii, AGN-ionised and composite regions using the O3N2 diagram, and to separate H ii and Seyfert/LINER-ionised regions using the O3S2 diagram." (Emission-line ratios); "Figure 5 shows the spatially-resolved depletion time map, constructed from the ratio of the SFR and molecular gas mass surface densities ($\tau_{\rm dep}\equiv\Sigma_{\rm H_2}/\Sigma_{\rm SFR}$)." (Spatially-resolved depletion times); "Figure 7 shows $\tau_{\rm dep}$ as a function of deprojected galactocentric radius, where individual spaxels are shown as purple datapoints, and the running mean for each case discussed in Section 3.3 is shown in the associated colour, using annuli of width $200$ pc and a step size of $100$ pc." (Radial trend of depletion time)
   - parameter: S/N > 3 threshold for Halpha and CO; radial annuli width = 200 pc, step = 100 pc  
  > "For spaxels where both $\Sigma_{\rm SFR}$ and $\Sigma_{\rm H_2}$ are reliably measured (i.e. where both H$\alpha$ and CO are detected with $S/N>3$), $\tau_{\rm dep}$ is calculated by simply dividing the two surface densities." (Spatially-resolved depletion times); "using annuli of width $200$ pc and a step size of $100$ pc." (Radial trend of depletion time)
   - fitting: _not stated_
   - validation: Checked consistency with 3D BPT diagnostic diagrams of Law et al. (2021) in Appendix A  
  > "We include this alternative analysis in Appendix \[app_3DBPT\], which confirms the nature of H ii regions while showing that the composite regions are likely AGN-ionised." (Emission-line ratios)
6. **Identify H II regions and compute ionised and molecular gas virial parameters**: Identify Halpha flux peaks and zone boundaries following Rousseau-Nepton et al. (2018), fit a 2D Gaussian to each H II region to obtain L_HII and R_HII, fit binned spectra with ORCS to measure sigma_HII, and calculate virial parameters alpha_vir,HII and cloud-scale alpha_vir,H2.  
  > "To take a more in-depth look at the star formation on cloud scales, we identified H ii regions using the SITELLE H$\alpha$ data and algorithms developed by (cite: rousseau2018ngc628), summarised below." (Virial parameters); "For each H ii region, a two-dimensional (2D) Gaussian fit is then carried out and the luminosity ($L_{\rm H ii}$ based on H$\alpha$ flux) and size (half-width at half-maximum $R_{\rm H ii}$) of the best-fitting Gaussian are calculated (and taken as those of the H ii region). Furthermore, the spectra from the SITELLE H$\alpha$ datacube are binned around the best-fitting peak of each H ii region, according to the size of the region, and the resulting spectrum is fit with `ORCS` to derive the velocity dispersion ($\sigma_{\rm H ii}$) of the region." (Virial parameters); "As a comparison, we also estimate the molecular gas virial parameter on the cloud scale, which is equivalent to the CO spaxel size of $\approx35$ pc." (Virial parameters)
   - software: ORCS
   - parameter: Peak criteria: >5 surrounding spaxels, 3x3 box > 3 sigma, minimum separation >= 1.1'' (99 pc); D_spaxel ~ 35 pc for CO virial parameter  
  > "The H$\alpha$ flux peaks are first identified, based on the following criteria: (1) the flux of the peak spaxel is greater than the flux of at least five immediately surrounding spaxels, (2) the total flux in a $3\times3$ spaxels box centred on the emission peak is above the $3\sigma$ detection threshold and (3) if two emission peaks are separated by a distance smaller than the seeing ($1.1\ensuremath{''}$ or $99$ pc in this case), only the brightest peak is preserved." (Virial parameters)
   - assumption: Spherical geometry and ionising photons from hot/massive stars to derive M_HII from L_HII and R_HII (Zaragoza-Cardiel et al. 2015)  
  > "This ionised-gas mass assumes that the mean electron number volume density can be derived from $L_{\rm H ii}$ assuming a spherical geometry, and that all ionising photons are from hot/massive stars." (Virial parameters)
   - fitting: 2D Gaussian fit to each H II region and ORCS spectral fit to binned H II region spectra  
  > "For each H ii region, a two-dimensional (2D) Gaussian fit is then carried out and the luminosity ($L_{\rm H ii}$ based on H$\alpha$ flux) and size (half-width at half-maximum $R_{\rm H ii}$) of the best-fitting Gaussian are calculated (and taken as those of the H ii region)." (Virial parameters)
   - validation: _not stated_
7. **Model molecular and ionised gas kinematics and non-circular motions**: Fit tilted-ring models to the 3D ALMA CO datacube using 3DBarolo (first with all parameters free, then fixing dynamical centre and inclination while allowing PA to vary), and fit tangential and radial velocity components of the Halpha velocity field using EMCEE with dynamical centre, inclination, and PA fixed to the 3DBarolo CO values.  
  > "For the molecular gas, we use the `3DBarolo` software of (cite: teodoro20153d), that fits tilted-ring models to three-dimensional (3D) emission-line datacubes, taking advantage of the high spectral and spatial resolutions of the ALMA CO observations. Following a first fit with all parameters free, we fix the dynamical centre (spatially and spectrally)and inclination, while letting the position angle (PA) vary to account for warping of the disc." (Non-circular motions); "The Bayesian inferences are done using the Python library EMCEE (cite: foreman2013emcee), fixing the dynamical centre, inclination and PA of the H$\alpha$ velocity field as the best-fitting values obtained from the 3DBarolo for the CO gas." (Non-circular motions)
   - software: 3DBarolo, EMCEE
   - parameter: 15 km s^-1 channel width CO cube used for kinematics; dynamical centre and inclination fixed after initial free fit  
  > "Finally, another datacube was produced following the same procedure but with a channel width of $15$ km s$^{-1}$, to enhance the S/N for the purpose of the gas kinematics analyses carried out in Section \[vfield\]." (Molecular gas data)
   - fitting: 3D tilted-ring fitting in 3DBarolo for CO; MCMC Bayesian fitting with EMCEE (including a line-of-sight velocity scatter nuisance parameter) for Halpha  
  > "We use another method to determine the rotation and radial velocity profiles of the ionised gas, by performing Markov Chain Monte Carlo (MCMC) fits of the tangential and radial velocity components. A nuisance parameter is also applied, which corresponds to the line-of-sight velocity scatter in the axi-symmetric modelling of the observed asymmetric kinematics." (Non-circular motions)
   - validation: Inspect velocity residual maps and position-velocity profiles  
  > "As a reference, the corresponding position-velocity (PV) profile and best-fitting reults of all the relevant parameters are in Appendix \[app_CO_Vrad\]." (Non-circular motions)
8. **Measure molecular cloud lifecycle timescales and separation length**: Measure CO-to-Halpha flux ratios in apertures of varying sizes centred on CO and Halpha emission peaks and fit with the analytical model in the HEISENBERG code across three masking/filtering cases (Case A: full FOV; Case B: central 650 pc masked; Case C: central 650 pc masked plus diffuse emission removed via iterative Gaussian high-pass Fourier filtering).  
  > "To infer these quantities, we adopt here the methods developed by (cite: 2018MNRAS.479.1866K) and use the associated `HEISENBERG` code." (Molecular cloud timescales); "We fit the observed CO-to-H$\alpha$ flux ratio with the analytical model presented in (cite: 2018MNRAS.479.1866K) to constrain $\lambda$ and the ratios $t_{\rm gas}/t_{\rm star}$ and $t_{\rm fb}/t_{\rm star}$." (Molecular cloud timescales); "For Case C, in addition to removing the central region, diffuse emissions is also removed across the field, achieved by tapering large-scale emission in Fourier space." (Molecular cloud timescales)
   - software: HEISENBERG
   - parameter: Central mask radius = 650 pc (Cases B and C); 77 CO flux peaks and 80 Halpha flux peaks identified  
  > "For Case B, a central region of $650$ pc radius is masked out." (Molecular cloud timescales); "However, the number of flux peaks identified, 77 for CO flux and 80 for H$\alpha$ flux, is not large enough to constrain timescale radial trends." (Molecular cloud timescales)
   - assumption: Reference isolated stellar phase timescale t_star,ref = 4.3 Myr (Haydon et al. 2020)  
  > "Assuming a reference timescale $t_{\rm star,~ref} = 4.3$ Myr for the isolated stellar phase (the appropriate timescale when using continuum-subtracted H$\alpha$ emission as the SFR tracer; see (cite: haydon2020uncertainty)), we convert these timescale ratios into absolute values." (Molecular cloud timescales)
   - fitting: Analytical model fitting of aperture-dependent CO-to-Halpha flux ratios in HEISENBERG  
  > "We fit the observed CO-to-H$\alpha$ flux ratio with the analytical model presented in (cite: 2018MNRAS.479.1866K) to constrain $\lambda$ and the ratios $t_{\rm gas}/t_{\rm star}$ and $t_{\rm fb}/t_{\rm star}$." (Molecular cloud timescales)
   - validation: Checked that separation length lambda > 100 pc (1.5x spatial resolution) and evaluated region filling factor zeta ~ 0.7  
  > "The fact that the separation lengths are $1.5$ times larger than the spatial resolution of our data (i.e. $\lambda>100$ pc) gives us confidence that the spatial resolution of our maps is sufficient for this analysis." (Molecular cloud timescales); "This is characterized with a region filling factor $\zeta$ described in (cite: 2018MNRAS.479.1866K), which is $\approx0.7$ in our best-fitting result that prevent the accurate measurement of $t_{\rm fb}$ within a few Myr (cite: 2022MNRAS.509..272C)." (Molecular cloud timescales)

## Software

- **CASA** 5.3 and 5.6.1: Pipeline calibration (v5.3), combining datasets (concat), uv-plane continuum subtraction (uvcontsub), and imaging (tclean v5.6.1) of ALMA CO(2-1) data.  
  > "The raw ALMA data were reduced using the Common Astronomy Software Applications (`CASA`) pipeline (version 5.3), which automatically processes the data by performing basic flagging and calibration (cite: mcmullin2007casa)." (Molecular gas data); "The data were then imaged using the `CASA` task `tclean` (version 5.6.1), adopting a channel width of $2$ km s$^{-1}$, a Briggs’ weighting robust parameter of $2.0$ and a $uv$-taper of $0.7\ensuremath{''}$, thus achieving a synthesised beam size (FWHM) of $0.99\ensuremath{''}\times0.84\ensuremath{''}$ ($89$ pc$\times76$ pc) at a position angle of $-58^\circ$, roughly matching the seeing of the H$\alpha$ observations." (Molecular gas data)
- **ORBS** : Data reduction of raw SITELLE optical IFTS observations.  
  > "The data reduction was performed with the `ORBS` software developed for SITELLE (cite: martin2015orbs; martin2021data)." (Ionised gas data)
- **ORCS** : Fitting emission lines in each SITELLE spaxel and in binned H II region spectra to extract flux, velocity, and velocity dispersion.  
  > "The emission lines in each spaxel were then fitted using the extraction software `ORCS` (cite: martin2015orbs)." (Ionised gas data); "Furthermore, the spectra from the SITELLE H$\alpha$ datacube are binned around the best-fitting peak of each H ii region, according to the size of the region, and the resulting spectrum is fit with `ORCS` to derive the velocity dispersion ($\sigma_{\rm H ii}$) of the region." (Virial parameters)
- **3DBarolo** : Fitting 3D tilted-ring kinematic models to the ALMA CO(2-1) datacube.  
  > "For the molecular gas, we use the `3DBarolo` software of (cite: teodoro20153d), that fits tilted-ring models to three-dimensional (3D) emission-line datacubes, taking advantage of the high spectral and spatial resolutions of the ALMA CO observations." (Non-circular motions)
- **EMCEE** : MCMC Bayesian fitting of the tangential and radial velocity components of the Halpha velocity field.  
  > "The Bayesian inferences are done using the Python library EMCEE (cite: foreman2013emcee), fixing the dynamical centre, inclination and PA of the H$\alpha$ velocity field as the best-fitting values obtained from the 3DBarolo for the CO gas." (Non-circular motions)
- **HEISENBERG** : Statistical analysis of CO and Halpha emission peaks to constrain molecular cloud lifetime, stellar phase duration, feedback timescale, and separation length.  
  > "To infer these quantities, we adopt here the methods developed by (cite: 2018MNRAS.479.1866K) and use the associated `HEISENBERG` code." (Molecular cloud timescales)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Molecular gas mass within ALMA FOV log(M_H2/M_sun) | 9.32 | not stated | dex (M_sun) | 4 | / \(5\) / $\log({\rm M_{H_2}~/~M_\odot})$ / $9.32$ / |
| Mean molecular gas surface density within inner 2 kpc log(Sigma_H2, 2 kpc / M_sun pc^-2) | 2.31 | not stated | dex (M_sun pc^-2) | 4 | / \(6\) / $\log({\rm \Sigma_{H_2,~2~kpc}~/~M_\odot~pc^{-2}})$ / $2.31$ /; The mean $\Sigma_{\rm H_2}$ in the central region of NGC 3169, $\log({\rm \Sigma_{\rm H_2,~2~kpc}~/~M_\odot~pc^{-2}}) = 2.31$, is calculated from the total molecular gas mass within a radius of $\approx 1.8$ kpc, as listed in Table 1. |
| Mean SFR surface density within inner 2 kpc log(Sigma_SFR, 2 kpc / M_sun yr^-1 kpc^-2) | -0.67 | not stated | dex (M_sun yr^-1 kpc^-2) | 3 | / \(13\) / $\log({\rm \Sigma_{SFR,~2~kpc}~/~M_\odot~yr^{-1}~kpc^{-2}})$ / $-0.67$ /; The mean $\Sigma_{\rm SFR}$ in the central region of NGC 3169, $\log({\rm \Sigma_{SFR,~2~kpc}~/~M_\odot~yr^{-1}~kpc^{-2}}) = -0.67$, is calculated from the total SFR within a radius of $\approx 1.8$ kpc, as listed in Table 1. |
| Integrated 230 GHz continuum flux at galaxy centre | 8.5 | not stated | mJy | 1 | The $230$ GHz continuum map is also shown in Figure 3 and reveals a bright region at the galaxy centre, slightly extended along the disc major axis and with an integrated flux of $8.5$ mJy, that could be explained by dust or a jet from the LLAGN. |
| Global molecular gas depletion time within ALMA FOV (radius ~ 1.8 kpc) | 0.9 | not stated | Gyr | 5 | For reference, the global depletion time ($0.9$ Gyr) is indicated by a grey horizontal line, calculated from the ratio of the total SFR to the total molecular gas mass within a radius of $\approx1.8$ kpc that is the ALMA FOV. |
| Average molecular gas depletion time in the star-forming ring (1.25 +/- 0.6 kpc) | 0.3 | not stated | Gyr | 5 | We identify a star-forming ring located at radii $1.25\pm0.6$ kpc with an average $\tau_{\rm dep}$ of 0.3 Gyr. |
| Molecular gas depletion time in star-forming regions at radius ~ 500 pc | 2.3 | not stated | Gyr | 5 | At radii $<0.9$ kpc, however, the molecular gas surface densities and depletion times increase with decreasing radius, the latter reaching approximately $2.3$ Gyr at a radius $\approx500$ pc.; For exclusively star-forming regions (orange curve in Figure \[fig:dept_rad\]), the mean $\tau_{\rm dep}$ reaches $\approx2.3$ Gyr at a radius of $\approx500$ pc. |
| CO rotation velocity in the star-forming ring (r > 650 pc) | 240-260 | not stated | km s^-1 | 7 | Beyond the radius of $\approx650$ pc, the derived rotation curve of CO gas suggests roughly constant rotation velocities of $240$–$260$ km s$^{-1}$ in the star-forming ring. |
| Halpha rotation velocity across the star-forming ring (650 to 1700 pc) | 200 to 280 | not stated | km s^-1 | 7 | The rotation curve of H$\alpha$ gas, however, increases from $200$ km s$^{-1}$ at $650$ pc to $280$ km s$^{-1}$ at $1700$ pc. |
| Central molecular gas velocity dispersion | 70 | not stated | km s^-1 | 7 | As shown in Figure \[fig:vel_field_app\], the molecular gas velocity dispersions are high throughout ($\sigma_{\rm gas}\gtrsim20$ km s$^{-1}$) and rise rapidly with decreasing radius within the inner disc, reaching $\approx70$ km s$^{-1}$ in the very centre. |
| Molecular gas lifetime t_gas (Case C, reference case) | 6.7 | +5.0/-1.4 | Myr | 8 | / $t_{\rm gas}$ (Myr) / $7.1^{+5.3}_{-2.1}$ / $10.5^{+4.2}_{-2.6}$ / $6.7^{+5.0}_{-1.4}$ / |
| Feedback phase duration t_fb (Case C, reference case) | <=1.5 | not stated | Myr | 8 | / $t_{\rm fb}$ (Myr) / $\leq2.9$ / $\leq3.3$ / $\leq1.5$ / |
| Young stellar phase duration t_star (Case C, reference case) | 4.4 | +1.4/-0.16 | Myr | 8 | / $t_{\rm star}$ (Myr) / $5.5^{+1.5}_{-0.9}$ / $5.9^{+1.7}_{-0.9}$ / $4.4^{+1.4}_{-0.16}$ / |
| Characteristic separation length lambda (Case C, reference case) | 163 | +33/-21 | pc | 8 | / $\lambda$ (pc) / $145^{+59}_{-38}$ / $148^{+53}_{-28}$ / $163^{+33}_{-21}$ / |

## Qualitative findings

- AGN photoionisation dominates the inner 400-650 pc of NGC 3169, while composite ionisation extends beyond 2 kpc in diffuse gas surrounding Halpha peaks.  
  > "While the spaxels within the central $650$ pc radius also appear to be affected by AGN ionisation, the composite regions are much more extended, encompassing $\approx50\%$ of the spaxels in the central region and reaching beyond a radius of $2$ kpc from the galaxy centre." (Emission-line ratios); "While H$\alpha$ emissions reaches the centre of the galaxy, the inner $400$ pc in radius are dominated by AGN ionisation." (Radial trend of depletion time)
- Both CO and Halpha rotation curves exhibit a characteristic 'double-hump' profile and out-of-phase radial velocity oscillations in the inner disc (r < 650 pc), indicative of a small-scale bar and non-circular inflow/outflow motions.  
  > "The resulting rotation curve resembles those of many barred galaxies, with a characteristic “double-hump” (i.e., a steep inner rise of the rotation velocities, followed by a decrease and local minimum before a second increase to the flat part of the rotation curve; e.g. (cite: bureau1999nature; athanassoula1999bar))." (Non-circular motions); "In particular, the oscillations of CO and H$\alpha$ are out of phase, indicating complex non-circular motions." (Non-circular motions)
- A weak positive correlation exists between the virial parameters of H II regions and their molecular gas depletion times, linking higher velocity dispersion (turbulence) to suppressed star formation.  
  > "As should then be expected, there is a weak correlation between $\alpha_{\rm vir,H ii}$ and $\tau_{\rm dep}$, shown in the left panel of Figure 1." (Virial parameters); "There is a weak correlation between the molecular gas depletion times and the virial parameters of the associated H ii regions. As large virial parameters are generally associated with high velocity dispersions, this suggests that the SFEs in the bulge of NGC 3169 are affected by turbulence." (Conclusions)

## Claim tuples

- H: Star formation efficiency is suppressed in the central bulge region of NGC 3169 compared to its surrounding star-forming ring. | E: Combine ALMA 12CO(2-1) and CFHT SITELLE optical emission line observations at ~100 pc resolution, separate star-forming from AGN/composite spaxels via BPT diagnostics, and measure radial profiles of molecular gas depletion time tau_dep. | R: A star-forming ring at 0.65-1.8 kpc has a short mean depletion time of ~0.3 Gyr, whereas inside r < 0.9 kpc the depletion time increases steadily with decreasing radius, reaching ~2.3 Gyr at r ~ 500 pc for star-forming spaxels (and >= age of the Universe in the central few hundred parsecs). | F: There is a clear transition from starburst-like efficient star formation in the ring to quenched star formation within the central ~500 pc despite high molecular gas surface densities. | **supported**
- H: Bulge morphology and dynamics alone can account for the observed star formation suppression in the central region of NGC 3169. | E: Compare the observed radial profile of Sigma_SFR / Sigma_H2 and the observed global sSFR against hydrodynamical simulations of galaxies with bulges from Gensior et al. (2020, 2021). | R: Simulations of bulges reproduce a similar qualitative radial decline in Sigma_SFR / Sigma_H2, but the simulated bulges are much denser (B/T ~ 0.9 vs ~0.1 in NGC 3169), and the empirical relation from the simulations predicts log(sSFR/Gyr^-1) = -0.68 compared to the observed -1.55. | F: Bulge dynamics contribute to the radial SFE trend, but are not the sole source of star formation suppression in NGC 3169; additional mechanisms are required. | **partially**
- H: Turbulence driven by AGN feedback and non-circular bar streaming motions contributes to suppressing star formation in the inner disc of NGC 3169. | E: Map BPT ionisation mechanisms, calculate H II region and cloud-scale virial parameters, and model CO and Halpha kinematics using 3DBarolo and EMCEE. | R: The inner <650 pc is dominated by AGN ionisation, exhibits a double-humped rotation curve, spiral-like velocity residuals from a small-scale bar, high CO velocity dispersions rising to ~70 km s^-1, and a positive correlation between H II region virial parameter and depletion time. | F: AGN feedback and inflow/outflow streaming motions from the small-scale bar enhance turbulence in the inner disc and act together with bulge dynamics to regulate the radial SFE profile. | **supported**

## Reasoning

- Why this data: Combining high-spatial-resolution ALMA 12CO(2-1) cold gas data with CFHT SITELLE optical IFTS ionised gas emission lines in NGC 3169 (which hosts a dense bulge, a small-scale bar, and a well-characterised LLAGN) allows separating AGN from star-forming ionisation via BPT ratios and measuring SFE at ~100 pc cloud scales.  
  > "To distinguish these different mechanisms in the inner regions of galaxies, we have initiated a project to measure the SFEs of galaxy bulges in a spatially-resolved manner, combining high-spatial resolution ^12^CO(2-1) measurements (by a cold gas indicator) from the Atacama Large Millimeter/sub-millimeter Array (ALMA) with ionised hydrogen emission-line measurements (by a SFR indicator) from the imaging Fourier transform spectrograph SITELLE at the Canada-France-Hawaii Telescope (CFHT)." (Introduction); "It hosts a complex central region, consisting of a dense and clear bulge, a small-scale bar, an AGN and a young nucleus, making it possible to probe multiple components that can affect local SFE." (NGC 3169)
- Why this method: BPT diagrams separate star-forming spaxels from AGN/composite contamination; 3DBarolo accounts for beam smearing in 3D CO kinematics while EMCEE incorporates individual spaxel velocity errors for Halpha; HEISENBERG statistical analysis constrains cloud lifetimes from spatial de-correlation of CO and Halpha peaks.  
  > "To accurately determine the SFEs in this region, we must distinguish the different ionisation mechanisms and confidently identify the H ii regions. Here, we utilise Baldwin, Phillips $\&$ Terlevich (BPT) diagrams (cite: baldwin1981classification) to assess the extent of the AGN impact." (Emission-line ratios); "This way, we use the same set of kinematic parameters for both gaseous components to assist the comparisons, while taking into account the individual errors on the line-of-sight H$\alpha$ velocities, which are unique to the SITELLE datacubes." (Non-circular motions); "A statistical analysis of CO and H$\alpha$ snapshots of these regions therefore allows us to estimate the characteristic lifetime of the molecular gas ($t_{\rm gas}$), the duration of the young stellar phase ($t_{\rm star}$), duration of the overlapping/feedback phase ($t_{\rm fb}$), as well as the characteristic separation length of individual regions ($\lambda$)." (Molecular cloud timescales)
- Alternative: 3D BPT diagnostic diagrams (Law et al. 2021) were tested in Appendix A as an alternative to 2D O3N2 and O3S2 BPT classifications, confirming the H II region identifications and showing composite regions are likely AGN-ionised.  
  > "We also note that recent studies (cite: law2021sdss) proposed using 3D diagnostic diagrams in the parameter space of \[O iii\]/H$\beta$, \[N ii\]/H$\alpha$ and \[S ii\]/H$\alpha$, to address the difference between the O3S2 and O3N2 diagrams. We include this alternative analysis in Appendix \[app_3DBPT\], which confirms the nature of H ii regions while showing that the composite regions are likely AGN-ionised." (Emission-line ratios)
- Alternative: Imaging CO(2-1) at the highest native resolution (0.58'' x 0.58'', robust = 0.5, no taper) was noted as appropriate for stand-alone GMC analyses, whereas robust = 2.0 with a 0.7'' taper and Gaussian convolution to 1.1'' was chosen to match the Halpha seeing.  
  > "Stand-alone GMC analyses should however be performed at the highest angular resolution possible for the CO data, here $0.58\ensuremath{''}\times0.58\ensuremath{''}$ ($52$ pc$\times52$ pc), when adopting a more standard Briggs’ robust parameter of 0.5 and no taper." (Molecular gas data)
- How they decided it was enough: _not stated_
- Limitation (authors): Hbeta 3-sigma detections only cover 52% of the 3-sigma Halpha spaxels, requiring nearest-neighbour adoption of A_Halpha for the remaining spaxels and making AGN-like vs LINER-like distinction uncertain.  
  > "Due to differences in the spectral resolutions and observing conditions of the two SITELLE datacubes, the H$\beta$ spaxels that satisfy a $3\sigma$ detection threshold only constitute $52\%$ of the H$\alpha$ spaxels satisfying that same condition." (SFR surface densities); "The distinction between AGN-like and LINER-like ionisation mechanisms is unclear, due to insufficient $S/N$ of the H$\beta$ and O iii lines." (Emission-line ratios)
- Limitation (authors): The Kennicutt & Evans (2012) Halpha-to-SFR conversion relation can break down on spatial scales smaller than 500 pc.  
  > "We note that when probing spatial scales smaller than $500$ pc, this conversion relation can break down, as seen in examples of (cite: kennicutt2012star)." (SFR surface densities)
- Limitation (authors): In composite and AGN-ionised regions, the exact fraction of star-formation ionisation is unknown, so derived SFRs are upper limits and depletion times are lower limits.  
  > "For spaxels identified as composite or AGN-ionised based on their emission-line ratios (see Section 3.3), the SFR is therefore likely an upper limit. In turn, the derived depletion times measurements are likely lower limits." (Spatially-resolved depletion times)
- Limitation (authors): Single-spaxel molecular gas virial parameters and ionised-gas virial parameters have large systematic uncertainties (ionised gas is only a fraction of total cloud mass; spaxel values do not resolve individual GMCs) and are also affected by beam smearing where the rotation curve changes steeply.  
  > "However, none of the mean molecular mass surface density, velocity dispersion and/or size is accurately estimated from that within a single spaxel, so the virial parameters evaluated using equation (10) should not be taken nor interpreted literally." (Virial parameters); "However, it is important to note that beam smearing may have a large impact here due to the rapid changes of rotation curve slopes shown in Section \[vfield\]." (AGN feedback)
- Limitation (authors): In the HEISENBERG analysis, the small number of emission peaks (77 CO, 80 Halpha) prevents constraining radial trends in cloud timescales, and peak blending (filling factor zeta ~ 0.7) allows only upper limits on the feedback timescale t_fb.  
  > "However, the number of flux peaks identified, 77 for CO flux and 80 for H$\alpha$ flux, is not large enough to constrain timescale radial trends. The blending of the CO and H$\alpha$ peaks also results in significant uncertainties on the feedback timescale $t_{\rm fb}$." (Molecular cloud timescales)
- Limitation (authors): The nominal spatial resolution of the CO observations (~65 pc) is not sufficient for detailed dynamical modelling of individual GMCs in the galactic potential.  
  > "However, the nominal spatial resolution of the current CO observations ($\approx65$ pc) is not sufficient for this purpose." (Quenching from the bar)
- Caveat (inferred, ours): Constant X_CO and CO(2-1)/CO(1-0) ratio = 0.8 are assumed across both the starburst ring and the AGN-dominated bulge, where higher gas temperatures, velocity dispersions, or metallicity gradients could lower X_CO or increase R_21, potentially overestimating Sigma_H2 and tau_dep in the centre.
- Caveat (inferred, ours): Adopting nearest-neighbour Balmer decrement extinction across the 48% of spaxels lacking 3-sigma Hbeta detections may introduce systematic biases in Sigma_SFR in dusty central regions.

## Reproducibility

- Data public (paper): Raw data are publicly available on the NRAO and CFHT archives; analysed data are available in the article and upon request.  
  > "The raw data underlying this article are publicly available on NRAO and CFHT archive. All analysed data are available in the article and upon request." (Data Availability)
- Products in archive: _not stated_
- Missing: Exact line-free frequency channels for uvcontsub and masking/threshold parameters for tclean
- Missing: Moment map generation thresholds and velocity integration ranges for the CO(2-1) cube
- Missing: Reduced SITELLE SN2 and SN3 datacubes or exact ORBS/ORCS configuration files
- Missing: Exact 3DBarolo parameter file and fixed dynamical centre / inclination values
- Missing: Complete HEISENBERG input configuration file
- Data volume (inferred): ~10-30 GB (one 12-m ALMA Execution Block with 605 s on-source and one 7-m dataset with 1120 s on-source, plus two SITELLE IFTS spectral cubes)
- Score (inferred): 72/5, Both ALMA project codes (2015.1.00598.S, 2016.2.00053.S) and the CFHT SITELLE programme (20Bc25) are stated and publicly archived, CASA versions and major imaging parameters (robust=2.0, taper=0.7'', 1.1'' smoothed beam, 2 and 15 km/s channels, rms=3.06 mJy/beam) are clearly specified, and all conversion equations and analysis codes (ORBS, ORCS, 3DBarolo, EMCEE, HEISENBERG) are named. Some low-level imaging/moment-map thresholds and kinematics/HEISENBERG configuration parameters are omitted.
- Rediscovery candidate: yes, Public ALMA datasets with clear project codes, well-defined conversion recipes for molecular gas mass and continuum flux, and explicit numeric targets (log M_H2 = 9.32, log Sigma_H2 = 2.31, 230 GHz continuum flux = 8.5 mJy, CO rotation curve = 240-260 km/s) make the ALMA portion a strong rediscovery benchmark.

## Links

- Method: (cite: martin2015orbs; martin2021data) (ORBS and ORCS data reduction and spectral extraction software for SITELLE IFTS observations)
- Method: (cite: rousseau2018ngc628) (Algorithm for identifying H II region peaks and spatial zones from SITELLE Halpha maps)
- Method: (cite: teodoro20153d) (3DBarolo tilted-ring kinematic modelling code used for the ALMA CO datacube)
- Method: (cite: foreman2013emcee) (EMCEE Python library used for MCMC fitting of the Halpha velocity field)
- Method: (cite: 2018MNRAS.479.1866K) (HEISENBERG statistical method and code for measuring GMC lifetimes, feedback timescales, and cloud separation lengths)
- Method: (cite: hygate2019uncertainty) (Iterative Gaussian high-pass Fourier filtering method to remove diffuse emission for HEISENBERG analysis)
- Companion: (cite: onishi2017wisdom) (WISDOM project foundational paper)
- Companion: (cite: liu2021wisdom) (Earlier WISDOM project paper analysing GMC dynamics in NGC 4429)
- Companion: Elford et al. ,in prep (Companion SED analysis of the central continuum source in NGC 3169)
- Related: mm-Wave Interferometric Survey of Dark Object Masses (WISDOM)

## Checks

```json
{
 "quotes": 170,
 "quotes_ok": 170,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 51,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 112,
  "stated": 89,
  "rate": 0.795
 },
 "evidence_ok": true
}
```

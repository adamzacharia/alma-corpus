# 3D insights into SN 1987A: ALMA observations compared to hydrodynamical explosion simulations

`2026MNRAS.548ag325W` | Monthly Notices of the Royal Astronomical Society 2026 | first author: Wesson, R. | arXiv: 2602.11259 | DOI: 10.1093/mnras/stag325

Card schema 1.0 | model gemini-4-argon | depth full | type observational_alma_primary

## Science

- Fields: transients, astrochemistry, milky_way_ism
- Question: How do the three-dimensional spatial and velocity distributions of CO and SiO molecules in the ejecta of SN 1987A observed with ALMA compare with long-time 3D hydrodynamical supernova explosion simulations across different progenitor models, and what do they imply for the neutron-star kick direction?  
  > "From these 3D maps, we reconstruct the 3D mass distributions of the ejecta in CO and SiO molecules, which we compare with those obtained by state-of-the-art, long-time hydrodynamical supernova explosion models" (Abstract); "Associating the densest ejecta with the region of the strongest emission allows us to tentatively estimate the kick direction expected in SN 1987A to be towards the observer and roughly $45^\circ$ northward." (Introduction)
- Target **SN 1987A**: coordinates 05:35:27.9875(11) -69:16:11.107(4) (ICRF J2015.0)  
  > "SN 1987A is the nearest supernova explosion detected in the last 400 years, at a distance of 51.4$\pm1.2$ kpc (cite: Panagia.1999)." (Introduction); "Finally, the velocities are shifted to the reference frame of SN 1987A, which has a heliocentric velocity of $+$287 km s$^{-1}$ ((cite: Groningsson:2008jb))." (ALMA observations); "They calculated a best-fitting position of $\alpha$=05:35:27.9875(11), $\delta$=$-69$:16:11.107(4) (ICRF J2015.0)." (3D plots); z/distance 51.4 +/- 1.2 kpc; v_hel = +287 +/- 3 km s^-1  
  > "SN 1987A is the nearest supernova explosion detected in the last 400 years, at a distance of 51.4$\pm1.2$ kpc (cite: Panagia.1999)." (Introduction); "Finally, the velocities are shifted to the reference frame of SN 1987A, which has a heliocentric velocity of $+$287 km s$^{-1}$ ((cite: Groningsson:2008jb))." (ALMA observations); "They calculated a best-fitting position of $\alpha$=05:35:27.9875(11), $\delta$=$-69$:16:11.107(4) (ICRF J2015.0)." (3D plots); distance from (cite: Panagia.1999); (cite: Meaburn.1995; Groningsson:2008jb); (cite: Alp.2018)  
  > "SN 1987A is the nearest supernova explosion detected in the last 400 years, at a distance of 51.4$\pm1.2$ kpc (cite: Panagia.1999)." (Introduction); "Finally, the velocities are shifted to the reference frame of SN 1987A, which has a heliocentric velocity of $+$287 km s$^{-1}$ ((cite: Groningsson:2008jb))." (ALMA observations); "They calculated a best-fitting position of $\alpha$=05:35:27.9875(11), $\delta$=$-69$:16:11.107(4) (ICRF J2015.0)." (3D plots)

## Data provenance

- ALMA projects: 2013.1.00280.S, 2015.1.00631.S, 2017.1.00789.S, 2018.1.00717.S
- bands: Band 7 (for dust continuum); others not stated by band number  
  > "To estimate the effect this might have when comparing the observations to theory, we calculated the distribution of dust mass with velocity using ALMA band 7 continuum data" (3D distribution of dust emission)
- frequencies and spectral setup: CO J=2-1 (230.54 GHz, 100 km/s), CO J=6-5 (691.47 GHz, 100 km/s), SiO J=5-4 (217.10 GHz, 100 and 300 km/s), SiO J=6-5 (260.52 GHz, 100 and 300 km/s), Continuum (315 GHz)  
  > "The data cube was constructed at 300 km s$^{-1}$ resolution in the line of sight." (ALMA observations); "CO $J$=2–1 | 230.54 | 1 | 2014 Sep 02 | 10 053 |   8.6 | $\left.\begin{array}{l} \end{array}\right\rbrace 0.057 \times 0.042$ | 27 | 6 | 100 | 0.04" (Table 1); "Continuum | 315 | 1 | 2015 Jun 28 | 10 352" (Table 1)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 0.04–5.8 km (2019 SiO J=6-5); 0.09–12.6 km (2017 SiO J=5-4)  
  > "The baseline lengths ranged from 0.04–5.8 km, with a maximum recoverable scale of 1.8$''$, sufficient to cover the entire ejecta." (ALMA observations); "The baseline lengths were 0.09–12.6 km, resulting in a maximum recoverable scale of 1.3$''$, again large enough to cover the entire ejecta." (ALMA observations)
- angular resolution: 0.03–0.06 arcsec (up to ~0.11 arcsec for epoch 2 SiO 6-5 and CO 6-5)  
  > "We obtain three-dimensional distributions of CO and SiO molecules from high spatial resolution (0.03–0.06") ALMA observations of SN 1987A at two different epochs." (Abstract); "CO $J$=6–5 | 691.47 | 1 | 2015 Sep 25 | 10 441 |  12.1 | $0.088 \times 0.064$ | 175 | 6 | 100 | 2.82" (Table 1)
- max recoverable scale: 1.8 arcsec (2019 SiO J=6-5); 1.3 arcsec (2017 SiO J=5-4)  
  > "The baseline lengths ranged from 0.04–5.8 km, with a maximum recoverable scale of 1.8$''$, sufficient to cover the entire ejecta." (ALMA observations); "The baseline lengths were 0.09–12.6 km, resulting in a maximum recoverable scale of 1.3$''$, again large enough to cover the entire ejecta." (ALMA observations)
- sensitivity: 0.04 mJy/beam (CO 2-1 ep1), 2.82 mJy/beam (CO 6-5 ep1), 0.05 mJy/beam (SiO 5-4 ep1), 0.033 mJy/beam (SiO 5-4 ep2), 0.06 mJy/beam (SiO 6-5 ep1), 0.055 mJy/beam (SiO 6-5 ep2)  
  > "The root mean square (rms) of $\sim0.055$ mJy per beam was measured in the area which is clear of SiO emission." (ALMA observations); "The rms level, measured in a region with no SiO emission, was $\sim0.033$ mJy per beam." (ALMA observations)
- time on source: CO 2-1 ep1: 8.6 + 71.7 min; CO 6-5 ep1: 12.1 min; SiO 5-4 ep1: 9.1 + 84.1 min; SiO 5-4 ep2: 208.9 min; SiO 6-5 ep1: 9.1 + 86.2 min; SiO 6-5 ep2: 95.6 min  
  > "CO $J$=6–5 | 691.47 | 1 | 2015 Sep 25 | 10 441 |  12.1 | $0.088 \times 0.064$ | 175 | 6 | 100 | 2.82" (Table 1); "2 | 2017 Nov 07 | 11 215 | 208.9 | $0.056 \times 0.034$ | 47 | 5 | 300 | 0.033" (Table 1); "2 | 2019 Aug 07-08 | 11 854 |  95.6 | $0.106 \times 0.101$ | 70 | 10 | 300 | 0.055" (Table 1)
- observing dates: 2014 Sep 02, 2015 Jun 28, 2015 Sep 25, 2015 Nov 01-02, 2017 Nov 07, 2019 Aug 07-08  
  > "More recently, SiO $J$=6–5 observations were taken in 2019, while a second epoch of SiO $J$=5–4 was taken in 2017." (ALMA observations); "CO $J$=6–5 | 691.47 | 1 | 2015 Sep 25 | 10 441 |  12.1 | $0.088 \times 0.064$ | 175 | 6 | 100 | 2.82" (Table 1); "Continuum | 315 | 1 | 2015 Jun 28 | 10 352" (Table 1)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (230.54 GHz)
- Line: CO J=6-5 (691.47 GHz)
- Line: SiO J=5-4 (217.10 GHz)
- Line: SiO J=6-5 (260.52 GHz)
- Other facility **JWST**: 3D map of [Fe I] emission in the ejecta from literature for morphological comparison  
  > "Interestingly, (cite: 2023ApJ...949L..27L) find that \[Fe i\] emission in the ejecta resembles a broken dipole, with two large clumps at velocities of approximately 2300 km s$^{-1}$." (Comparison of SiO and CO morphologies); "In Fig. 16, we show their 3D map of \[Fe i\] emission together with our CO and SiO distributions." (Comparison of SiO and CO morphologies)
- External data: Distance to SN 1987A of 51.4 +/- 1.2 kpc  
  > "To convert angular distances to physical distances in the $x$-$y$ plane, we adopt the distance to SN 1987A of 51.4 kpc found by (cite: Panagia.1999)" (3D plots) [from (cite: Panagia.1999)]
- External data: Systemic heliocentric velocity of SN 1987A / LMC of +287 +/- 3 km s^-1  
  > "In the $z$-direction, we first subtracted the systemic velocity of the LMC, $v_{\rm hel}$=+287$\pm$3 km s$^{-1}$ (cite: Meaburn.1995; Groningsson:2008jb) from the observed velocity values." (3D plots) [from (cite: Meaburn.1995; Groningsson:2008jb)]
- External data: Geometric centre of the equatorial ring as explosion origin: alpha=05:35:27.9875(11), delta=-69:16:11.107(4) (ICRF J2015.0)  
  > "We use the position determined by (cite: Alp.2018), who calculated the geometric centre of the equatorial ring by fitting an ellipse to the locations of the centroids of its bright clumps." (3D plots) [from (cite: Alp.2018)]
- External data: Inclination of the equatorial ring (~43 deg to the plane of the sky)  
  > "The equatorial ring appears elliptical as it is inclined at $\sim$43$^\circ$ to the plane of the sky ((cite: 2011A&A...527A..35T))." (Spectral grids) [from (cite: 2011A&A...527A..35T)]
- External data: 3D map of [Fe I] emission in the ejecta of SN 1987A  
  > "Interestingly, (cite: 2023ApJ...949L..27L) find that \[Fe i\] emission in the ejecta resembles a broken dipole, with two large clumps at velocities of approximately 2300 km s$^{-1}$." (Comparison of SiO and CO morphologies) [from (cite: 2023ApJ...949L..27L); (cite: larsson2023)]
- Simulation/model as data: 15 core-collapse supernova 3D hydrodynamical explosion simulations across 10 progenitor models (single-star RSG and BSG, binary-merger BSG, and RSG models) computed up to ~1 yr with the PROMETHEUS-HOTB code  
  > "which we compare with those obtained by state-of-the-art, long-time hydrodynamical supernova explosion models computed with the PROMETHEUS-HOTB code for 10 different progenitors, including both red and blue supergiants." (Abstract); "We compare our observations with the results of 15 simulations of the core-collapse supernova. The 10 underlying progenitor models that were exploded can be divided into three groups." (Hydrodynamical models)
- Simulation/model as data: 13 RSG explosion models from Giudici et al. (2025a,b) used to test the correlation between neutron-star kick direction and C+O centre-of-mass direction  
  > "In order to further strengthen our findings, we analysed all 13 RSG models of (cite: Giudici2025a; Giudici2025b), of which our group 3 is a subset, in the same way" (Neutron star kick geometry in theoretical models)

## Processing

### Calibration

- pipeline or manual: ALMA calibration pipeline and CASA processing as described in Cigan et al. (2019)  
  > "The observations were carried out using standard ALMA observing procedures, and processed as described in (cite: Cigan:2019cl), using CASA (cite: 2007ASPC..376..127M) and the ALMA calibration pipeline (cite: hunter23)." (ALMA observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~7%  
  > "the astrometric accuracy at S/N 5–10 is about 15 mas at the lower resolution and 10 mas at the higher resolution and the flux scale accuracy is $\sim$7% ." (ALMA observations)
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "The natal weighting for the CASA clean process produces a synthesised beam of 115$\times$108 mas$^2$ at position angle (PA) 61$^{\circ}$." (ALMA observations)
- deconvolver: _not stated_
- weighting robust: natural weighting (written as 'natal weighting' for 2019 SiO J=6-5)  
  > "The natal weighting for the CASA clean process produces a synthesised beam of 115$\times$108 mas$^2$ at position angle (PA) 61$^{\circ}$." (ALMA observations)
- uv taper: _not stated_
- cell size: 6 mas (Epoch 1 CO 2-1, CO 6-5, SiO 5-4, SiO 6-5), 5 mas (Epoch 2 SiO 5-4), 10 mas (Epoch 2 SiO 6-5)  
  > "CO $J$=6–5 | 691.47 | 1 | 2015 Sep 25 | 10 441 |  12.1 | $0.088 \times 0.064$ | 175 | 6 | 100 | 2.82" (Table 1); "2 | 2017 Nov 07 | 11 215 | 208.9 | $0.056 \times 0.034$ | 47 | 5 | 300 | 0.033" (Table 1); "2 | 2019 Aug 07-08 | 11 854 |  95.6 | $0.106 \times 0.101$ | 70 | 10 | 300 | 0.055" (Table 1)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: subtracted using identified line-free continuum channels  
  > "After applying all respective observatory calibrations at each epoch, line-free continuum channels are identified and used to subtract continuum emission." (ALMA observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: High angular resolution (2015.1.00631.S) and lower angular resolution (2013.1.00280.S) data combined in Epoch 1; 2017.1.00789.S and 2018.1.00717.S in Epoch 2  
  > "For epoch 1, the data from the program code 2015.1.00631S are high angular resolution images (cite: Abellan:2017by), while those from the program code 2013.1.00280.S are from lower angular resolution images (cite: Matsuura:2017cf), and these data were combined during the data reduction process" (ALMA observations)
- smoothing: _not stated_
- final beam: CO 2-1 ep1: 0.057x0.042" PA 27 deg; CO 6-5 ep1: 0.088x0.064" PA 175 deg; SiO 5-4 ep1: 0.058x0.042" PA 21 deg; SiO 5-4 ep2: 0.056x0.034" PA 47 deg; SiO 6-5 ep1: 0.041x0.034" PA 172 deg; SiO 6-5 ep2: 0.106x0.101" PA 70 deg (115x108 mas^2 PA 61 deg in text)  
  > "The natal weighting for the CASA clean process produces a synthesised beam of 115$\times$108 mas$^2$ at position angle (PA) 61$^{\circ}$." (ALMA observations); "The synthesised beam was 56$\times$34 mas with PA 47$^{\circ}$." (ALMA observations); "CO $J$=6–5 | 691.47 | 1 | 2015 Sep 25 | 10 441 |  12.1 | $0.088 \times 0.064$ | 175 | 6 | 100 | 2.82" (Table 1)
- final rms: CO 2-1 ep1: 0.04 mJy/beam; CO 6-5 ep1: 2.82 mJy/beam; SiO 5-4 ep1: 0.05 mJy/beam; SiO 5-4 ep2: 0.033 mJy/beam; SiO 6-5 ep1: 0.06 mJy/beam; SiO 6-5 ep2: 0.055 mJy/beam  
  > "The root mean square (rms) of $\sim0.055$ mJy per beam was measured in the area which is clear of SiO emission." (ALMA observations); "The rms level, measured in a region with no SiO emission, was $\sim0.033$ mJy per beam." (ALMA observations); "CO $J$=6–5 | 691.47 | 1 | 2015 Sep 25 | 10 441 |  12.1 | $0.088 \times 0.064$ | 175 | 6 | 100 | 2.82" (Table 1)

### Inherited from earlier work

- Epoch 1 observation details and data reduction procedures  
  > "High angular resolution ALMA observations of CO and SiO in SN 1987A were taken in 2012–2015, and the details of the observations and the data reduction were reported in (cite: Abellan:2017by) and (cite: Cigan:2019cl)." (ALMA observations); "The observations were carried out using standard ALMA observing procedures, and processed as described in (cite: Cigan:2019cl), using CASA (cite: 2007ASPC..376..127M) and the ALMA calibration pipeline (cite: hunter23)." (ALMA observations) [from (cite: Abellan:2017by); (cite: Cigan:2019cl); (cite: Matsuura:2017cf)]
- Hydrodynamical explosion simulations up to shock breakout and ~1 yr for Group 1, 2, and 3 progenitors  
  > "The explosions of these stars have been described in detail in (cite: Wongwathanarat:2015jv) and (cite: Gabler2021)." (Hydrodynamical models); "These binary-merger BSG (bBSG) models were evolved up to shock breakout in (cite: Utrobin2021), and continued until about 1 year for this work." (Hydrodynamical models); "We present a selection of these models that span the widest ranges in the distributions of the elements Si, O and C (cite: Giudici2025a; Giudici2025b)." (Hydrodynamical models) [from (cite: Wongwathanarat2013); (cite: Wongwathanarat:2015jv); (cite: Gabler2021); (cite: Utrobin2021); (cite: Giudici2025a); (cite: Giudici2025b)]

### Not stated but needed to reproduce (our reading)

- Exact CASA and ALMA pipeline versions used for calibration and imaging
- Specific frequency/channel ranges used as line-free channels for continuum subtraction
- Deconvolver, weighting scheme (for 2017 SiO 5-4 and Epoch 1), masking, and threshold parameters in CASA clean
- Exact coordinates of the four off-source regions outside the equatorial ring used to calculate the MAD noise threshold
- How the 2017.1.00789.S and 2018.1.00717.S datasets in Epoch 2 were weighted or combined (and why Table 1 lists one date per Epoch 2 line)
- Exact viewing angles (Euler angles) manually selected to orient the 3D hydrodynamic simulation grids to match SN 1987A sky coordinates

## Analysis recipe

1. **Grid the ejecta region, determine noise threshold, and extract integrated line profiles**: Select a 0.6" x 0.6" region covering the ejecta (excluding the equatorial ring) and divide it into a 10x10 grid of 0.06" x 0.06" cells. Estimate the noise threshold by taking four regions outside the equatorial ring, dividing each into 10x10 cells, computing the mean absolute deviation (MAD) in each cell, and taking the mean of all MAD values. Mask out data below this threshold and integrate the spectrum over all spatial cells.  
  > "The analysed region covers 0.6"$\times$0.6". We divide this region into a grid of 10$\times$10 cells, corresponding to 0.06"$\times$0.06" per cell, which is comparable to the beam size in all data sets." (Spectral grids); "These regions were also divided into 10$\times$10 grid cells, and the mean absolute deviation (MAD) in each cell was calculated. The mean of all MAD values thus calculated in each dataset is taken as a base level of emission" (Spectral grids); "As a first step, we integrate the spectrum over all spatial cells shown in Fig. 1. During this integration, we remove data below the previously calculated noise limit." (Integrated line profiles)
   - parameter: 0.6" x 0.6" region, 10x10 grid (0.06" x 0.06" per cell), velocity binning 100 or 300 km s^-1  
  > "We divide this region into a grid of 10$\times$10 cells, corresponding to 0.06"$\times$0.06" per cell, which is comparable to the beam size in all data sets." (Spectral grids); "rather than the velocity channel, which we bin to a resolution of 100 or 300 km s$^{-1}$, depending on the dataset." (Spectral grids)
   - assumption: Four off-source regions outside the equatorial ring contain no signal from circumstellar material  
  > "We estimate the noise amplitude in four regions outside the equatorial ring, which are assumed to contain no signal from the circumstellar material." (Spectral grids)
   - fitting: _not stated_
   - validation: Q-Q plots of pixel values in signal-free regions outside the equatorial ring to check for Gaussian noise characteristics  
  > "Fig. 22 shows one of the Q-Q plots that we produced when analysing the noise in each dataset. We analysed regions of the data outside the equatorial ring where no signal should be present." (Noise characteristics)
2. **Construct 3D spatial maps of CO and SiO emission and measure hemispheric asymmetries**: Convert sky pixel coordinates (x, y) to physical distances relative to the explosion centre using d = 51.4 kpc. Subtract systemic heliocentric velocity (+287 km s^-1) and multiply line-of-sight velocity by time since explosion to get z distance. Divide data cubes into N/S, E/W, Near/Far, and Below/Above (relative to equatorial ring plane) hemispheres to compute fractional emission.  
  > "To convert angular distances to physical distances in the $x$-$y$ plane, we adopt the distance to SN 1987A of 51.4 kpc found by (cite: Panagia.1999)" (3D plots); "The distance from a point to the $x$-$y$ plane is then simply the velocity multiplied by the time since explosion." (3D plots); "To quantify the asymmetry of the different molecules at the different epochs, we divide the data cubes into north/south, east/west, and approaching/receding hemispheres with the position of the progenitor lying on the dividing plane." (3D plots)
   - parameter: Explosion centre alpha=05:35:27.9875(11), delta=-69:16:11.107(4) (ICRF J2015.0); threshold 1x or 2x noise level  
  > "They calculated a best-fitting position of $\alpha$=05:35:27.9875(11), $\delta$=$-69$:16:11.107(4) (ICRF J2015.0)." (3D plots); "To directly compare the relative spatial distributions of CO and SiO obtained with ALMA, we plot both molecules with different colour maps using a minimum intensity threshold set to twice the estimated noise level in Fig. 15." (Comparison of SiO and CO morphologies)
   - assumption: Homologous (free) expansion since the explosion; distance = 51.4 kpc; systemic velocity = +287 km s^-1  
  > "Then, we assume that the ejecta have been freely expanding since the explosion." (3D plots)
   - fitting: _not stated_
   - validation: Compare 3D morphologies across two epochs and multiple transitions  
  > "In general, the maps of both SiO and CO show qualitatively similar results in all transition lines and at both epochs." (3D plots)
3. **Derive observational fractional mass-velocity distributions and summary velocity parameters**: Convert 3D spatial distances to 3D radial velocities by dividing radial distance by time since explosion. Bin fractional intensities in increments of 100 or 300 km s^-1. Apply a 3-point moving average and compute v_peak, width (difference between 25th and 75th percentiles), and v_max (95th percentile of molecular mass) with uncertainties via a 1000-iteration Monte Carlo simulation.  
  > "Under these assumptions, the fractional mass at a given velocity is proportional to the fractional intensity." (Mass distributions); "Depending on the spectral resolution of the respective data set, the radial velocity was binned in increments of $100\,$km s$^{-1}$ or $300\,$km s$^{-1}$." (Mass distributions); "To estimate these parameters and their uncertainties for the observed mass distributions, we carry out a Monte Carlo analysis in which we generate 1000 variations of the mass distribution." (Mass distributions)
   - parameter: 1000 Monte Carlo iterations, 20% standard deviation per data point, 3-point moving average, percentiles: 25th, 75th, 95th  
  > "For each data point, we draw values from a normal distribution centred on the observed value, with a standard deviation of 20%, which corresponds to the uncertainty values estimated in Appendix 8 from both statistical and systematic effects." (Mass distributions); "To reduce the influence of small-scale noise, we apply a 3-point moving average before calculating $v_\mathrm{peak}$ and width." (Mass distributions)
   - assumption: Ejecta are optically thin at the observed wavelengths, in local thermodynamic equilibrium (LTE), and at a uniform temperature; constant expansion velocity  
  > "To derive these mass distributions, we assume that the ejecta has the following properties: 1. it is optically thin at the observed wavelengths; 2. it is in local thermodynamic equilibrium (LTE); 3. it has a uniform temperature." (Mass distributions)
   - fitting: Monte Carlo sampling (1000 iterations) from normal distribution with 20% standard deviation  
  > "For each data point, we draw values from a normal distribution centred on the observed value, with a standard deviation of 20%" (Mass distributions)
   - validation: Dedicated sensitivity tests in Appendix: varying explosion centre by +/-5 pixels (1000 realizations), adding synthetic Gaussian-filtered (sigma=3 pixels) noise (1000 realizations), and varying noise threshold by x0.5 to x2  
  > "We estimate the associated error by varying the assumed centre of the explosion by up to $\pm5$ pixels N/S and E/W." (Position of the explosion site); "We create the synthetic noise by first generating pure uncorrelated normally-distributed noise values in each pixel, and then applying a Gaussian filter with a standard deviation of 3 pixels." (Image noise); "To estimate the magnitude of this, we vary the value used in the analysis from our fiducial value by factors between $\times$0.5 and $\times$2." (Noise threshold)
4. **Estimate 3D dust mass-velocity distribution from ALMA Band 7 continuum**: Using ALMA Band 7 continuum data (315 GHz), compute dust mass vs velocity under two approximations: (1) all dust velocities are in the plane of the sky; (2) ballistic expansion up to 3500 km s^-1 with dust density declining as r^-2 along the line of sight.  
  > "To estimate the effect this might have when comparing the observations to theory, we calculated the distribution of dust mass with velocity using ALMA band 7 continuum data" (3D distribution of dust emission); "A simple limiting case then assumes that all dust velocities are in the plane of the sky." (3D distribution of dust emission); "To proceed, we assume that the dust density declines proportionally to r$^{-2}$ with distance $r$ from the supernova explosion." (3D distribution of dust emission)
   - parameter: Maximum shell velocity = 3500 km s^-1; radial density profile proportional to r^-2  
  > "At a given pixel position, if the dust shell is expanding with a velocity proportional to distance from the explosion point (ballistic expansion), then the dust velocities lie between the plane-of-sky velocity of the point and the maximum velocity of the shell, estimated at 3500 km s$^{-1}$." (3D distribution of dust emission)
   - assumption: Dust has uniform temperature and negligible optical depth; ballistic expansion; r^-2 density profile  
  > "We assume that the dust is at a uniform temperature, and that its optical depth is negligible, such that the dust mass along a given line of sight is directly proportional to the observed flux." (3D distribution of dust emission)
   - fitting: _not stated_
   - validation: Comparison of plane-of-sky limiting case with 1/r^2 line-of-sight velocity distribution  
  > "The left-hand panel assuming no velocity along the line of sight will systematically underestimate total velocities." (3D distribution of dust emission)
5. **Compute C+O and Si+O mass-velocity distributions and 3D maps from hydrodynamical explosion simulations**: Evolve 15 core-collapse SN models to ~1 yr with PROMETHEUS-HOTB. In each cell, compute maximal C+O mass from min(C, O) stoichiometry, then react remaining O* with Si to form Si+O. Integrate over cell volumes and bin by velocity. For 3D visual comparison, map 3D spherical simulations at t ~ 1 yr onto a 512^3 Cartesian grid, smooth by 8^3 grid cells, interpolate onto a 160^3 grid, and plot every second point in the line-of-sight direction.  
  > "For the hydrodynamic simulations of all the models, we use the PROMETHEUS-HOTB code (cite: Gabler2021)." (Hydrodynamical models); "In each numerical cell, we first estimate the maximal mass available for CO molecules depending on the relation of the mass fractions of carbon $X_\text{C}$ and oxygen $X_\text{O}$" (Hydrodynamical models); "As a first step, we map the results of the 3D spherical simulations at $t\sim1$yr onto a $512^3$ Cartesian grid. These mapped data are then smoothed to cubes of size $8^3$ grid cells in order to approximate the beam size of the observations." (3D maps of C+O and Si+O of theoretical models)
   - software: PROMETHEUS-HOTB
   - parameter: Simulation time ~321-373 days (~1 yr); tracer 56X fraction = 0%, 50%, or 100%; Cartesian grid 512^3 smoothed by 8^3 and interpolated to 160^3  
  > "The simulations of model groups 2 and 3 have been performed assuming that $50\%$ of the tracer material is $^{56}$Ni and contributes to the $\beta$ decay" (Hydrodynamical models); "The smoothed data are subsequently interpolated onto a $160^3$-point grid to facilitate comparison with the observations." (3D maps of C+O and Si+O of theoretical models)
   - assumption: Carbon binds with oxygen first to form C+O, and only remaining oxygen reacts with silicon to form Si+O; homologous expansion after t ~ 1 yr  
  > "At about 1 year, homology is reached. We then extrapolate the models to the current time of SN 1987A and assume that the ejecta velocities do not change significantly." (Hydrodynamical models); "In our approximation, we assume that C first attract sall available O, thus leaving less O for forming Si+O." (Velocity vs mass distributions)
   - fitting: Manual search for best viewing angle to match 3D morphology  
  > "Because there is no correspondence between the coordinates of the simulated 3D map and the sky coordinates of SN 1987A, we attempt to find a viewing angle that best represents the features of the observational data manually." (3D maps of C+O and Si+O of theoretical models)
   - validation: Compare three beta-decay treatments in model B15 (no beta-decay, without tracer, 100% tracer X)  
  > "using the three variants of model B15, which have respectively no decay, without tracer and with" (Hydrodynamical models)
6. **Fit plane to the punctured CO shell and estimate neutron-star kick direction from C+O / CO centre of mass**: Fit a 3D plane a(x-x0) + b(y-y0) + c(z-z0) = 0 to the CO data via least-squares minimisation of point-to-plane distances (both fixed to origin and free) and compute angle to the equatorial ring. In simulations, correlate NS kick direction (at t_pb = 2.5 s) with the centre-of-mass direction of C+O above density thresholds F_rho(C+O) = [0.2, 0.15, 0.1, 0.05, 0.01] at t ~ 1 yr. Compute the emission-weighted centre of observed CO to infer the SN 1987A kick vector.  
  > "We applied this procedure using several fractions of the threshold density, expressed as percentages of the maximum density found in the simulations: F$_{\rho\mathrm{(C+O)}}=[0.2,0.15,0.1,0.05,0.01]$." (Neutron star kick geometry in theoretical models); "We now employ this correlation to estimate the neutron star kick in SN 1987A, using ALMA measured CO distributions." (Indications for kick direction in SN 1987A from CO emission centre); "To determine the inclination of this plane, we calculated the distance of each point in the CO data from the assumed plane, and carried out a least-squares minimisation of the distance to determine the optimal parameters of the plane equation" (Calculation of plane parameters)
   - parameter: Density thresholds F_rho(C+O) = [0.2, 0.15, 0.1, 0.05, 0.01] (fiducial 15% of maximum density); NS kick evaluated at t_pb = 2.5 s  
  > "Here, we have considered only the cells whose C+O density reaches at least $15\%$ of the maximal density in the grid." (Neutron star kick geometry in theoretical models); "determining the kick direction of the neutron star (at $t_\mathrm{pb}=2.5$s) and that of the centre of mass of the C+O with densities above a certain fraction of the maximal density in the grid (at $t\sim1\,$yr)." (Neutron star kick geometry in theoretical models)
   - assumption: Correlation between the centre of mass of the densest C+O ejecta and the NS kick direction in simulations applies to the observed CO emission in SN 1987A  
  > "If such a correlation also applies to the CO emission in the ejecta of SN 1987A, the kick of the compact remnant is expected to point towards the observer, at an angle of approximately $45^\circ$ to the north." (Abstract)
   - fitting: Least-squares minimisation for 3D plane fitting; linear regression in latitude and longitude for kick vs C+O centre-of-mass correlation  
  > "For a sufficiently high density threshold, we obtain a relatively good fit with a $R^2$ coefficient of the order of $0.65-0.86$." (Neutron star kick geometry in theoretical models); "and carried out a least-squares minimisation of the distance to determine the optimal parameters of the plane equation" (Calculation of plane parameters)
   - validation: Test correlation robustness across density thresholds from 1% to 20% of maximum density and across both fixed-origin and free-origin plane fits  
  > "We have tested whether correlations between kick and C+O depend on the particular value of the minimal density considered, by changing the threshold between $5\%$ and $20\%$." (Neutron star kick geometry in theoretical models)

## Software

- **CASA** : Calibration, continuum subtraction, and clean imaging of ALMA observations  
  > "The observations were carried out using standard ALMA observing procedures, and processed as described in (cite: Cigan:2019cl), using CASA (cite: 2007ASPC..376..127M) and the ALMA calibration pipeline (cite: hunter23)." (ALMA observations); "The natal weighting for the CASA clean process produces a synthesised beam of 115$\times$108 mas$^2$ at position angle (PA) 61$^{\circ}$." (ALMA observations)
- **ALMA calibration pipeline** : Calibration of ALMA observations  
  > "The observations were carried out using standard ALMA observing procedures, and processed as described in (cite: Cigan:2019cl), using CASA (cite: 2007ASPC..376..127M) and the ALMA calibration pipeline (cite: hunter23)." (ALMA observations)
- **PROMETHEUS-HOTB** : 3D hydrodynamical supernova explosion simulations  
  > "which we compare with those obtained by state-of-the-art, long-time hydrodynamical supernova explosion models computed with the PROMETHEUS-HOTB code for 10 different progenitors, including both red and blue supergiants." (Abstract); "For the hydrodynamic simulations of all the models, we use the PROMETHEUS-HOTB code (cite: Gabler2021)." (Hydrodynamical models)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO J=2-1 mass distribution peak velocity (v_peak) | 1830 | 210 | km s^-1 | 3 | CO $J$=2-1 / 1830$\pm$210 / 1210$\pm$70 / 3980$\pm$40 |
| CO J=2-1 mass distribution velocity width | 1210 | 70 | km s^-1 | 3 | CO $J$=2-1 / 1830$\pm$210 / 1210$\pm$70 / 3980$\pm$40 |
| CO J=2-1 mass distribution maximal velocity (v_max, 95% mass) | 3980 | 40 | km s^-1 | 3 | CO $J$=2-1 / 1830$\pm$210 / 1210$\pm$70 / 3980$\pm$40 |
| SiO J=5-4 epoch 1 mass distribution peak velocity (v_peak) | 1730 | 190 | km s^-1 | 3 | SiO $J$=5-4 ep.1 / 1730$\pm$190 / 1180$\pm$60 / 3600$\pm$30 |
| SiO J=5-4 epoch 1 mass distribution velocity width | 1180 | 60 | km s^-1 | 3 | SiO $J$=5-4 ep.1 / 1730$\pm$190 / 1180$\pm$60 / 3600$\pm$30 |
| SiO J=5-4 epoch 1 mass distribution maximal velocity (v_max) | 3600 | 30 | km s^-1 | 3 | SiO $J$=5-4 ep.1 / 1730$\pm$190 / 1180$\pm$60 / 3600$\pm$30 |
| SiO J=5-4 epoch 2 mass distribution peak velocity (v_peak) | 1600 | 80 | km s^-1 | 3 | SiO $J$=5-4 ep.2 / 1600$\pm$80 / 870$\pm$60 / 3110$\pm$60 |
| SiO J=5-4 epoch 2 mass distribution velocity width | 870 | 60 | km s^-1 | 3 | SiO $J$=5-4 ep.2 / 1600$\pm$80 / 870$\pm$60 / 3110$\pm$60 |
| SiO J=5-4 epoch 2 mass distribution maximal velocity (v_max) | 3110 | 60 | km s^-1 | 3 | SiO $J$=5-4 ep.2 / 1600$\pm$80 / 870$\pm$60 / 3110$\pm$60 |
| SiO J=6-5 epoch 1 mass distribution peak velocity (v_peak) | 1820 | 190 | km s^-1 | 3 | SiO $J$=6-5 ep.1 / 1820$\pm$190 / 930$\pm$60 / 3220$\pm$50 |
| SiO J=6-5 epoch 1 mass distribution velocity width | 930 | 60 | km s^-1 | 3 | SiO $J$=6-5 ep.1 / 1820$\pm$190 / 930$\pm$60 / 3220$\pm$50 |
| SiO J=6-5 epoch 1 mass distribution maximal velocity (v_max) | 3220 | 50 | km s^-1 | 3 | SiO $J$=6-5 ep.1 / 1820$\pm$190 / 930$\pm$60 / 3220$\pm$50 |
| SiO J=6-5 epoch 2 mass distribution peak velocity (v_peak) | 1530 | 100 | km s^-1 | 3 | SiO $J$=6-5 ep.2 / 1530$\pm$100 / 1000$\pm$50 / 3510$\pm$70 |
| SiO J=6-5 epoch 2 mass distribution velocity width | 1000 | 50 | km s^-1 | 3 | SiO $J$=6-5 ep.2 / 1530$\pm$100 / 1000$\pm$50 / 3510$\pm$70 |
| SiO J=6-5 epoch 2 mass distribution maximal velocity (v_max) | 3510 | 70 | km s^-1 | 3 | SiO $J$=6-5 ep.2 / 1530$\pm$100 / 1000$\pm$50 / 3510$\pm$70 |
| SiO average mass distribution peak velocity (v_peak) | 1600 | 110 | km s^-1 | 3 | SiO (average) / 1600$\pm$110 / 1080$\pm$70 / 3560$\pm$50 |
| SiO average mass distribution velocity width | 1080 | 70 | km s^-1 | 3 | SiO (average) / 1600$\pm$110 / 1080$\pm$70 / 3560$\pm$50 |
| SiO average mass distribution maximal velocity (v_max) | 3560 | 50 | km s^-1 | 3 | SiO (average) / 1600$\pm$110 / 1080$\pm$70 / 3560$\pm$50 |
| Inclination angle of best-fit CO shell plane to the equatorial ring | 84 | 11 | deg | 6 | Indeed, when determining the parameters of the best-fit plane to the two-punctured shell in Appendix 10 we find an inclination angle to the equatorial ring of 84$\pm$11$^\circ$.; Propagating the uncertainties on the plane parameters into the angle between this plane and the equatorial ring, we obtain a value of 84$\pm$11$^\circ$. |
| Emission-weighted centre of CO (East, North, in front of explosion site) | 155, 1240, 1100 (r = 1660) | not stated | AU | 6 | The direction of the emission-weighted centre of CO lies 155 AU east, 1240 AU north and 1100 AU in front of the SN explosion site; Its polar coordinates, where $\Theta=0$, $\phi=0$ corresponds to the line of sight, are $\Theta=8.0^\circ, \phi=48.1^\circ, r=1660$ AU. |
| Polar coordinates (Theta, phi) of emission-weighted centre of CO (inferred NS kick direction) | 8.0, 48.1 (approx 45 deg north towards observer) | not stated | deg | 6 | If such a correlation also applies to the CO emission in the ejecta of SN 1987A, the kick of the compact remnant is expected to point towards the observer, at an angle of approximately $45^\circ$ to the north.; Its polar coordinates, where $\Theta=0$, $\phi=0$ corresponds to the line of sight, are $\Theta=8.0^\circ, \phi=48.1^\circ, r=1660$ AU. |
| Angle alpha between NS kick direction and centre of mass of densest 15% C+O in bBSG models (M157b-1, M157b-2, M157b-3, M157b-4, M158b-1) | 26, 33, 2, 11, 43 | not stated | deg | 6 | The corresponding angles between kick and C+O centre of mass $\alpha$ are given in the last column of Table 4. They are generally lower than $\alpha<33^\circ$.; M157b-3 / 1.587 / 373 / -415 / 377 / 673 / 2; M157b-4 / 1.492 / 158 / 281 / -746 / 813 / 11 |

## Qualitative findings

- Comparison of two epochs of SiO observations shows no significant time evolution in the 3D structure and mass-velocity distributions, confirming homologous (free) expansion and optically thin emission.  
  > "In summary, the agreement between the mass distributions and 3D structures at both epochs supports the assumption that the ejecta are freely expanding, and additionally provides evidence that they are optically thin." (Mass distributions)
- At a threshold of twice the noise level, CO exhibits a clumpy two-punctured shell morphology oriented nearly perpendicular (84 +/- 11 deg) to the equatorial ring, while SiO is dominated by a single large clump lying in a void of the CO shell.  
  > "We find a clumpy, shell-like structure that appears disrupted in two opposite facing directions for CO (red)." (Comparison of SiO and CO morphologies); "With the new threshold, the SiO morphology (blue) is dominated by one large clump, which lies in one of the voids between major clumps forming the CO shell." (Comparison of SiO and CO morphologies)
- Binary-merger blue supergiant (bBSG) models (particularly M15-7b-2, M15-7b-3, and M15-7b-4) best reproduce both the observed CO velocity distribution and the 3D punctured-shell morphology, whereas all bBSG models underpredict high-velocity SiO.  
  > "The models which best match the mass distributions correspond to explosions of binary-merger blue supergiant progenitors; at least two such models approximately reproduce the observed CO morphology." (Abstract); "In contrast, the SiO velocity distribution and morphology are not as well reproduced in these models, indicating insufficient mixing of Si into the outer layers already at the progenitor stage." (Abstract)
- In 3D explosion models, fast-moving Fe-rich plumes puncture and displace the overlying C+O shell, causing the densest C+O clumps to be anti-aligned with the Fe plumes and strongly correlated with the neutron-star kick direction.  
  > "As a result, the densest C+O regions tend to lie in directions where the Fe-rich plumes do not penetrate, leading to the observed anti-correlation between the Fe-rich plumes and the densest C+O clumps." (Summary and discussion); "Since the kick and the densest ejecta rich in lighter elements are expected to be anti-aligned with the most extended Fe-rich structures, a correlation between the directions of the NS kick and densest C+O ejecta seems natural." (Summary and discussion)

## Claim tuples

- H: The molecular ejecta of SN 1987A are expanding homologously (freely) and are optically thin at millimeter wavelengths between 10,000 and 11,854 days post-explosion. | E: Reconstruct 3D spatial maps and fractional mass-velocity distributions of SiO J=5-4 and J=6-5 across two ALMA epochs separated by 2–4 years (volume increase by factors of 1.40 and 1.64) and compare them. | R: The 3D morphologies and fractional mass-velocity distributions between Epoch 1 and Epoch 2 agree within the estimated uncertainties (SiO average v_peak = 1600 +/- 110 km s^-1, v_max = 3560 +/- 50 km s^-1). | F: The ejecta are in homologous free expansion and were already optically thin prior to Epoch 1. | **supported**
- H: 3D neutrino-driven explosion simulations of binary-merger blue supergiant (bBSG) progenitors can reproduce the observed 3D morphology and velocity distributions of both CO and SiO in SN 1987A. | E: Compare ALMA-derived CO and SiO fractional mass-velocity curves and 3D maps against C+O and Si+O distributions from 15 PROMETHEUS-HOTB 3D hydrodynamical simulations spanning single-star BSGs, RSGs, and binary-merger BSGs. | R: bBSG models (especially M15-7b-4 with v_peak = 1550 km s^-1, v_max = 3550 km s^-1) closely match the CO velocity tail and 3D two-punctured shell morphology, but severely underpredict Si+O peak and maximum velocities (M15-7b-4 Si+O v_peak = 1250 km s^-1, v_max = 2650 km s^-1 vs observed 3560 +/- 50 km s^-1). | F: bBSG models reproduce the CO distribution well, but fail to reproduce high-velocity SiO, indicating insufficient silicon in the outer layers of the progenitor models prior to explosion. | **partially**
- H: The direction of the neutron-star kick correlates with the centre of mass of the densest C+O ejecta, allowing an estimate of the compact remnant kick direction in SN 1987A from ALMA CO observations. | E: Measure the angle between the NS kick vector and the centre of mass of the densest C+O ejecta across bBSG and RSG 3D explosion simulations, and compute the emission-weighted centre of CO in the ALMA 3D cube of SN 1987A. | R: In asymmetric bBSG models, the angle between the NS kick and the densest 15% C+O centre of mass is alpha = 2–33 deg (R^2 = 0.65–0.86 across bBSG and RSG models). The observed CO emission centre lies at r = 1660 AU (Theta = 8.0 deg, phi = 48.1 deg). | F: There is a strong correlation between the densest C+O centre of mass and the NS kick direction; if applicable to SN 1987A, the compact object kick points towards the observer at ~45 deg to the north. | **supported**

## Reasoning

- Why this data: SN 1987A is young and freely expanding so its 3D molecular ejecta retain the imprint of early explosion dynamics; high-resolution (<100 mas) multi-epoch ALMA spectral cubes allow direct 3D spatial reconstruction via velocity-to-distance conversion.  
  > "Unlike older SN remnants which have interacted with the interstellar and circumstellar material, the expanding ejecta retains the imprint of the dynamics during the early days after the supernova explosion" (Introduction); "In particular, the free expansion allows radial velocities to be translated into the third spatial dimension with much greater confidence than in e.g. turbulent molecular clouds." (Introduction)
- Why this method: Comparing both 1D fractional mass-velocity distributions and 3D spatial maps across 15 long-time (~1 yr) 3D hydrodynamical simulations is necessary because models with similar 1D velocity distributions can have completely different 3D morphologies.  
  > "Although velocity distributions enable quantitative comparisons between observed and simulated data, these 3D plots show that a similar mass distribution does not guarantee qualitatively similar 3D morphologies." (3D maps of C+O and Si+O of theoretical models)
- Alternative: Single-star BSG (B15, N20) and RSG (L15, W15, WH12.5, SW19.8, SW20.8, SW27.3) progenitor models were tested and rejected as matches for SN 1987A because they either fail to match the velocity distribution or fail to match the 3D morphology and progenitor constraints.  
  > "Model B15 does not closely reproduce the ALMA measured velocity distributions of molecules in SN 1987A" (Velocity vs mass distributions); "From Fig.9, it appears that model SW20.8 represents best the mass fraction vs velocity distribution of SiO. However, when plotting the 3D morphology in Fig. 14, we note that the distribution of Si+O does not resemble the observed 3D morphology at all." (3D maps of C+O and Si+O of theoretical models)
- Alternative: Condensation of gas-phase molecules into dust was tested via ALMA Band 7 continuum modeling as an explanation for the discrepancy between models and observations at <1000 km s^-1 and >3000 km s^-1, and rejected as insufficient.  
  > "Where many of the theoretical models have problems matching the observed molecular distributions is at velocities of $<$1000 km s$^{-1}$, where a number of them predict more material than is observed, and at $>$3000 km s$^{-}$ where they predict less material than observed. Condensation of molecules into dust therefore does not help us to resolve these discrepancies." (3D distribution of dust emission)
- How they decided it was enough: _not stated_
- Limitation (authors): SiO J=5-4 Epoch 2 cube is truncated at +2000 km s^-1 on the receding side due to insufficient spectral bandwidth.  
  > "it can also be seen that the SiO 5–4 data from the second epoch of observations (green line, bottom panel) is truncated on the far side at a velocity of +2000 kms$^{-1}$, due to the bandwidth not being sufficient to cover the entire range of velocities." (Integrated line profiles)
- Limitation (authors): High-velocity molecular emission in the ALMA cubes may be buried in noise or excluded by the spatial cut-off used to avoid contamination from the equatorial ring.  
  > "Too high model predictions for the velocity could simply mean that the material is not detected, because it is either buried in the noise, or it is at such high velocities that the ejecta are excluded by the truncation of the data to avoid contamination from the ring of SN 1987A." (Summary and discussion)
- Limitation (authors): Explosion energy and energy deposition timescale are free parameters in the approximate ray-by-ray neutrino transport scheme, and 56Ni yields have uncertainties due to the electron fraction Ye.  
  > "Our approximate approach of the neutrino transport allows us to choose the explosion energy (and the energy deposition time scale) as a free parameter, and it is not calculated self-consistently." (Summary and discussion); "Since our model comes with uncertainties with respect to the total amount of radioactive $^{56}$Ni synthesized, the discrepancies of too low peak velocities can be cured (partially) by assuming a larger production of $^{56}$Ni." (Summary and discussion)
- Limitation (authors): Simulations do not include self-consistent chemical networks for molecule formation/destruction or dust condensation, relying instead on local elemental stoichiometry (C+O first, then Si+O).  
  > "The simulations do not yet offer the possibility to calculate the formation of molecules self-consistently. We approximated the molecule distribution as described in Section 3." (Summary and discussion)
- Limitation (authors): Converting observed line intensities into fractional masses assumes optical thinness, LTE, and uniform temperature across the ejecta without full radiative transfer.  
  > "However, in particular, the assumption of LTE and constant temperature may not apply perfectly in the central regions of the ejecta." (Summary and discussion)
- Limitation (authors): Progenitor and explosion models do not include initial stellar rotation or magnetic fields.  
  > "In particular, our simulations were performed without initial rotation and without magnetic fields." (Summary and discussion)
- Caveat (inferred, ours): In the model stoichiometry, carbon is assumed to consume 100% of available local oxygen before any SiO can form, which could artificially suppress simulated Si+O in C-rich zones.
- Caveat (inferred, ours): The 3D orientation of the hydrodynamic simulation grids relative to the sky was chosen manually by visual inspection rather than through an objective 3D cross-correlation metric.
- Caveat (inferred, ours): In Table 1, rest frequencies are labelled in [Hz] in the column header but printed numerically in GHz (e.g. 230.54).
- Caveat (inferred, ours): For the 2019 SiO J=6-5 dataset, the text states a beam of 115x108 mas^2 at PA 61 deg whereas Table 1 lists 0.106x0.101 arcsec at PA 70 deg.

## Reproducibility

- Data public (paper): Raw ALMA data are publicly available from the ALMA archive; simulation data will be made available on the Garching SN archive.  
  > "The raw ALMA data are available from the ALMA archive." (Data availability); "Data of simulations will be made available on the Garching SN archive (https://wwwmpa.mpa-garching.mpg.de/ccsnarchive/)." (Data availability)
- Products in archive: Reduced data products are available on request to the authors.  
  > "Reduced data products will be made available on request to the authors." (Data availability)
- Missing: Custom analysis scripts used for 3D coordinate transformation, noise thresholding, mass-velocity histogram generation, and plane fitting
- Missing: Exact CASA imaging scripts and uv-combination weights for merging high- and low-resolution ALMA executions
- Missing: Exact coordinates of the four off-source noise estimation boxes
- Missing: Exact Euler rotation angles applied to the 3D simulation cubes for each figure
- Data volume (inferred): tens of GB (raw visibilities for 4 ALMA projects across multiple configurations plus 512^3 3D hydrodynamic simulation outputs)
- Score (inferred): 65/5, Raw ALMA project codes and simulation archive URL are clearly stated, and the mathematical recipes for 3D mapping, C+O/Si+O stoichiometry, and uncertainty analysis are well documented. However, reduced cubes are only available on request, analysis scripts are not released, some CASA imaging details are deferred to earlier papers or omitted, and 3D model viewing angles were chosen manually.
- Rediscovery candidate: yes, All four ALMA project codes are public in the ALMA archive, the transformation from spectral line cubes to 3D maps and 1D fractional mass-velocity distributions is straightforward and well-specified, and the summary velocity statistics (v_peak, width, v_max), hemispheric emission ratios, and plane inclination angle provide clear quantitative answer keys.

## Links

- Method: (cite: Gabler2021) (Describes the PROMETHEUS-HOTB code and long-time (~1 yr) 3D supernova simulation methodology including radioactive 56Ni heating)
- Method: (cite: Wongwathanarat2013); (cite: Wongwathanarat:2015jv) (Describes the ray-by-ray neutrino transport scheme and 3D hydrodynamic simulation setup up to shock breakout)
- Method: (cite: Utrobin2021) (Describes the binary-merger blue supergiant (bBSG) explosion setups evolved to shock breakout)
- Method: (cite: Giudici2025a); (cite: Giudici2025b) (Describes the Group 3 RSG explosion simulations)
- Companion: (cite: Abellan:2017by) (Presented the Epoch 1 high-resolution ALMA CO and SiO 3D observations and data reduction)
- Companion: (cite: Cigan:2019cl) (Presented the Epoch 1 ALMA observations, data reduction pipeline, and dust/molecular analysis)
- Companion: (cite: Matsuura:2017cf) (Presented the lower angular resolution Epoch 1 ALMA observations (2013.1.00280.S))
- Related: Garching Core-Collapse Supernova Archive

## Checks

```json
{
 "quotes": 184,
 "quotes_ok": 184,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 7,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 22,
 "numeric_problems": 0,
 "fill": {
  "facts": 98,
  "stated": 77,
  "rate": 0.786
 },
 "evidence_ok": true
}
```

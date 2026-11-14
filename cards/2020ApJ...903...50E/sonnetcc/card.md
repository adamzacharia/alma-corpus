# Super Star Clusters in the Central Starburst of NGC 4945

`2020ApJ...903...50E` | The Astrophysical Journal 2020 | first author: Emig, Kimberly L. | arXiv: 2009.05154 | DOI: 10.3847/1538-4357/abb67d

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: star_formation, nearby_galaxies, agn_and_quasars
- Question: Identify and characterize candidate super star clusters (size, ionizing photon rate, stellar mass, gas mass) in the central starburst of NGC 4945 using 93 GHz free-free continuum and H40alpha/H42alpha recombination lines, and constrain ionizing photons from the AGN  
  > "We identify candidate star clusters and estimate properties relating to their size, ionizing photon luminosity, stellar mass, and gas mass." (Introduction); "We do not detect recombination line emission from the AGN and place an upper limit on the ionizing photons which leak into the starburst region of $Q_0 < 10^{52}$ s$^{-1}$." (abstract)
- Target **NGC 4945**: coordinates brightest 93 GHz peak (presumed AGN core): 13h05m27.4798s, -49d28m05.404s  
  > "NGC 4945 is a nearby (3.8 Mpc) galaxy hosting a nuclear starburst and Seyfert Type 2 AGN." (abstract); "At the distance of 3.8 Mpc, 0.1$''$ corresponds to 1.84 pc." (Introduction); "The brightest peak at 93 GHz, centered at $(\alpha, \delta)_{93} = (13\mathrm{h}\, 05\mathrm{m}\, 27.4798 \mathrm{s} \pm 0.004 \mathrm{s}, -49^{\circ}\, 28\ensuremath{'}\, 05.404\ensuremath{''} \pm 0.06\ensuremath{''})$" (3 Continuum Emission); z/distance 3.8 Mpc  
  > "NGC 4945 is a nearby (3.8 Mpc) galaxy hosting a nuclear starburst and Seyfert Type 2 AGN." (abstract); "At the distance of 3.8 Mpc, 0.1$''$ corresponds to 1.84 pc." (Introduction); "The brightest peak at 93 GHz, centered at $(\alpha, \delta)_{93} = (13\mathrm{h}\, 05\mathrm{m}\, 27.4798 \mathrm{s} \pm 0.004 \mathrm{s}, -49^{\circ}\, 28\ensuremath{'}\, 05.404\ensuremath{''} \pm 0.06\ensuremath{''})$" (3 Continuum Emission); distance from _not stated_

## Data provenance

- ALMA projects: 2018.1.01236.S, 2016.1.01135.S
- bands: Band 3 (93 GHz, 3.2 mm; project 2018.1.01236.S); archival 350 GHz (850 um) continuum from project 2016.1.01135.S  
  > "We used the ALMA Band 3 receivers to observe NGC 4945 as part of the project 2018.1.01236.S (PI: A. Leroy)." (Observations); "We compare the continuum emission at 3 mm with archival ALMA imaging of the $\nu = 350$ GHz ($\lambda \sim 850~\mu$m) continuum (project 2016.1.01135.S, PI: N. Nagar)." (Observations)
- frequencies and spectral setup: Four Band 3 spectral windows centered at 86.2, 88.4, 98.4, 100.1 GHz covering H42alpha and H40alpha; spws span 15 GHz; native channel width 0.488 MHz  
  > "Four spectral windows in Band 3 – centered at 86.2, 88.4, 98.4, and 100.1 GHz" (Observations); "The spectral windows span 15 GHz, which we set up to have a large fractional bandwidth." (3.3.1 Band 3 Spectral Index); "We boxcar smoothed the spectral cubes from the native 0.488 MHz channel width to 2.93 MHz." (Observations)
- continuum bandwidth: full bandwidth of line-free channels (fiducial frequency 93.2 GHz); also per-spectral-window continuum images  
  > "Then we create a continuum image using the full bandwidth of the line-free channels. We also make continuum images for each spectral window." (Observations); "the fiducial frequency is $\nu = 93.2$ GHz" (Observations)
- arrays: 12 m array  
  > "We observed NGC 4945 with the main 12 m array telescopes in intermediate and extended configurations." (Observations)
- configurations: 8 km extended configuration (used for main analysis) and 1 km intermediate configuration (comparison)  
  > "We image the data from an 8 km extended configuration" (Observations); "we compare the high resolution data with observations taken in a 1 km intermediate configuration as part of the same observing project" (Observations)
- baselines: _not stated_
- angular resolution: 93 GHz continuum 0.12 arcsec (2.2 pc) after circularizing from 0.097 x 0.071 arcsec; H40alpha/H42alpha cubes 0.20 arcsec; intermediate configuration 0.7 arcsec; 350 GHz matched to 0.12 arcsec  
  > "Before convolution to a round beam, the beam had a major and minor FWHM of 0.097$''$ $\times$ 0.071$''$." (Observations); "For the H40$\alpha$ and H42$\alpha$ spectral cubes, the final FWHM beam size is 0.20$''$, convolved from 0.097$''$ $\times$ 0.072$''$ and from 0.11$''$ $\times$ 0.083$''$, respectively." (Observations); "However, the lower end may reflect the resolution limit of our beam, with a FWHM size of 2.2 pc." (5.1 Size)
- max recoverable scale: extended configuration sensitive to spatial scales of 0.07-6 arcsec (2-100 pc)  
  > "We image the data from an 8 km extended configuration, which are sensitive to spatial scales of 0.07$''$–6$''$ (2–100 pc)" (Observations)
- sensitivity: 93 GHz continuum rms ~0.017 mJy/beam; H40alpha cube 0.50 mJy/beam per 8.9 km/s channel; H42alpha cube 0.48 mJy/beam per 10.3 km/s channel; 350 GHz rms 0.7 mJy/beam; intermediate-config continuum rms 0.15 mJy/beam  
  > "The rms noise away from the source is $\approx$0.017 mJy beam$^{-1}$, equivalent to 0.2 K in Rayleigh-Jeans brightness temperature units." (Observations); "The typical rms in the H40$\alpha$ cube is 0.50 mJy beam$^{-1}$ per 8.9 km s$^{-1}$ channel." (Observations); "The typical rms in the H42$\alpha$ cube is 0.48 mJy beam$^{-1}$ per 10.3 km s$^{-1}$ channel." (Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: 2018.1.01236.S PI A. Leroy (new data); 2016.1.01135.S PI N. Nagar, described as archival  
  > "We used the ALMA Band 3 receivers to observe NGC 4945 as part of the project 2018.1.01236.S (PI: A. Leroy)." (Observations); "We compare the continuum emission at 3 mm with archival ALMA imaging of the $\nu = 350$ GHz ($\lambda \sim 850~\mu$m) continuum (project 2016.1.01135.S, PI: N. Nagar)." (Observations)
- Line: H I (hydrogen recombination line) H40alpha (n=40, Delta n=1) (99.0230 GHz)
- Line: H I (hydrogen recombination line) H42alpha (n=42, Delta n=1) (85.6884 GHz)
- Line: H I (hydrogen recombination line) effective H41alpha (synthesized by averaging H40alpha and H42alpha) (92.034 GHz)
- Other facility **Australian Long Baseline Array (LBA) 2.3 GHz**: 2.3 GHz continuum images (synchrotron tracer), Epoch 2, beam 0.080 x 0.032 arcsec, rms 0.082 mJy/beam, provided courtesy of E. Lenc  
  > "We compare the ALMA data with Australian Long Baseline Array (LBA) imaging of $\nu = 2.3$ GHz continuum emission (cite: Lenc2009)." (Observations); "We use the Epoch 2 images (courtesy of E. Lenc) that have a native angular resolution slightly higher than the 3 mm ALMA data" (Observations)
- Other facility **Spitzer IRAC 8 um**: 8 um image of the whole disk (Program 40410, PI G. Rieke) for context figure  
  > "The whole disk of NGC 4945, as traced by *Spitzer* IRAC 8 $\mu$m emission (Program 40410, PI: G. Rieke)" (3 Continuum Emission)
- Other facility **HST Pa-alpha**: Pa-alpha emission image shown for comparison  
  > "Paul van der Werf for the HST Pa-$\alpha$ data" (Acknowledgments)
- External data: 2.3 GHz LBA continuum images and low-frequency SED/free-free opacity modeling of compact radio sources  
  > "We take the model fit by (cite: Lenc2009) and normalize it to the 2.3 GHz flux that we extract as an example" (3.2 Point Source Flux Extraction); "Using the optical depths derived in (cite: Lenc2009) and our fiducial electron temperature, we solve for the density through the relation," (5.4 Ionized Gas: Emission Measure, Density and Mass) [from (cite: Lenc2009)]
- External data: Non-LTE departure coefficient b_n = 0.73  
  > "take $b_{\mathsf{n}} = 0.73$ (cite: Storey1995)" (5.3 Temperature and Metallicity) [from (cite: Storey1995)]
- External data: Helium ionization ratio y = 0.10  
  > "which we fix as $y = 0.10$ (cite: DePree1996; Mills2020)." (5.3 Temperature and Metallicity) [from (cite: DePree1996; Mills2020)]
- External data: Starburst99 ionizing photon output for a 5 Myr old population  
  > "We use Starburst99 calculations (cite: Leitherer1999) to infer the stellar mass from the ionizing photon output of a 5 Myr old stellar population" (5.5 Ionizing Photon Production and Stellar Mass) [from (cite: Leitherer1999)]
- External data: Dust temperature of 130 K  
  > "We assume a dust temperature of $T_{\mathrm{dust}} = 130$ K, as has been determined for the gas kinetic temperature in the forming super star clusters in NGC 253 (cite: Gorski2017)." (5.6 Gas Mass from Dust) [from (cite: Gorski2017)]
- External data: Dust mass absorption coefficient kappa = 1.9 cm2/g at 350 GHz  
  > "We adopt $\kappa = 1.9$ cm$^2$ g$^{-1}$ which should be appropriate for $\nu \sim 350$ GHz and dust mixed with gas at a density of $\sim 10^5 - 10^6$ cm$^{-3}$ (cite: Ossenkopf1994)" (5.6 Gas Mass from Dust) [from (cite: Ossenkopf1994)]
- External data: Dust-to-gas mass ratio of 1/100  
  > "an adopted dust-to-gas mass ratio (DGR) of 1-to-100, approximately the Milky Way value and similar to the value found for starburst galaxies by (cite: Wilson2008)" (5.6 Gas Mass from Dust) [from (cite: Wilson2008)]
- External data: Electron temperature to oxygen abundance relation  
  > "(cite: Shaver1983) established a relation," (5.3 Temperature and Metallicity) [from (cite: Shaver1983)]
- External data: Disk metallicity 12+log(O/H) = 8.5 +/- 0.1 from strong-line ratios in 15 star-forming regions  
  > "(cite: Stanghellini2015) determined in 15 star-forming regions in the galactic plane of NGC 4945" (5.3 Temperature and Metallicity) [from (cite: Stanghellini2015)]
- External data: Lower-resolution H42alpha analysis (2.3 arcsec) used for flux/profile comparison; Te = 5400 +/- 600 K; Lbol = (2.0 +/- 0.2)e10 Lsun from FIR  
  > "which finds $T_e = (5400 \pm 600)$ K (cite: Bendo2016)." (5.3 Temperature and Metallicity); "$L_{\mathrm{bol}} = (2.0 \pm 0.2) \times 10^{10}$ L$_{\odot}$ (cite: Bendo2016)" (6.5 Total Burst of Star-formation) [from (cite: Bendo2016)]
- External data: NGC 253 cluster population properties and mass function for comparison  
  > "We include the SSCs of NGC 253, with stellar mass properties determined on similar spatial scales ($\sim$2 pc resolution) and through H40$\alpha$ recombination lines for a zero-age main sequence population (cite: Leroy2018; Mills2020)." (6.3 Cluster Mass Function) [from (cite: Leroy2018; Mills2020)]
- External data: Cluster mass function slope of beta = -2.0 +/- 0.3 across six galaxies  
  > "A main result from (cite: Mok2020) is that the cluster mass functions across the six galaxies are consistent with slopes of $\beta = -2.0 \pm 0.3$." (6.3 Cluster Mass Function) [from (cite: Mok2020)]
- External data: AGN bolometric luminosity from X-ray luminosity (Lbol ~ 20 Lx) and ionizing fraction (Lbol/Lion ~ 3, 113 eV photons)  
  > "which we determined using the relation for Seyfert AGN of $L_{\mathrm{bol}} \sim 20 L_{\mathrm{X}}$ (cite: Hopkins2007)" (6.5 Role of the AGN); "We use the standard relation of (cite: Elvis1994), which posits $L_{\mathrm{bol}} / L_{\mathrm{ion}} \sim 3$ with an average ionizing photon energy of 113 eV." (6.5 Role of the AGN) [from (cite: Hopkins2007); (cite: Elvis1994)]
- Simulation/model as data: Starburst99 single 1e6 Msun population (Kroupa IMF, max mass 100 Msun, default tracks) giving 5 Myr ionizing photon output used to convert Q0 to stellar mass  
  > "We arrive at this value by simulating a single $10^6$ M$_{\odot}$ stellar population, with the initial mass function (IMF) of (cite: Kroupa2001), a maximum stellar mass of 100 M$_{\odot}$, and the default stellar evolution tracks and tuning parameters." (5.5 Ionizing Photon Production and Stellar Mass)

## Processing

### Calibration

- pipeline or manual: observatory-provided calibrated visibilities (calibration details not given)  
  > "We analyze the observatory-provided calibrated visibilities using version 5.4.0 of the Common Astronomy Software Application (cite: McMullin2007)." (Observations)
- casa version: CASA 5.4.0 (used to analyze the calibrated visibilities)  
  > "We analyze the observatory-provided calibrated visibilities using version 5.4.0 of the Common Astronomy Software Application (cite: McMullin2007)." (Observations)
- pipeline version: _not stated_
- archive products used as is: observatory-calibrated visibilities used; 1 km configuration continuum image taken from the observatory pipeline  
  > "We analyze the observatory-provided calibrated visibilities using version 5.4.0 of the Common Astronomy Software Application (cite: McMullin2007)." (Observations); "We use the continuum image provided by the observatory pipeline, which we convolve to have a circular beam FWHM of 0.7$''$" (Observations)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean named for in-band spectral index comparison; imaging task settings otherwise not given  
  > "The spectral indices measured in this way were consistent for the brightest sources with the index determined by `CASA tclean`" (3.3.1 Band 3 Spectral Index)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5 for 93 GHz continuum and line cubes; robust = -2 for the 350 GHz image  
  > "For all images, we use Briggs weighting with a robust parameter of $r=0.5$." (Observations); "We imaged the calibrated visibilities with a Briggs robust parameter of $r=-2$ (towards uniform weighting)" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: CLEAN mask (all channels) derived from the full-bandwidth continuum image, for line cubes  
  > "Then, we image by applying a CLEAN mask (to all channels) derived from the full-bandwidth continuum image." (Observations)
- multiscale scales: _not stated_
- continuum subtraction: uv-plane first-order polynomial fit  
  > "When imaging the two spectral lines of interest, we first subtract the continuum in $uv$ space through a first order polynomial fit." (Observations)
- line free channels: channels with strong spectral lines flagged for continuum imaging; channel ranges not given  
  > "When imaging the continuum, we flag channels with strong spectral lines." (Observations)
- primary beam correction: _not stated_
- array combination: no joint imaging of configurations; extended and 1 km configurations imaged separately  
  > "We do not jointly image the configurations because our main science goals are focused on compact, point-like objects." (Observations)
- smoothing: convolved to circular beams; cubes boxcar smoothed from 0.488 MHz to 2.93 MHz channels  
  > "After imaging, we convolved the continuum and line images to convert from an elliptical to a round beam shape." (Observations); "We boxcar smoothed the spectral cubes from the native 0.488 MHz channel width to 2.93 MHz." (Observations)
- final beam: continuum 0.12 arcsec circular; H40alpha/H42alpha cubes 0.20 arcsec circular  
  > "For the H40$\alpha$ and H42$\alpha$ spectral cubes, the final FWHM beam size is 0.20$''$, convolved from 0.097$''$ $\times$ 0.072$''$ and from 0.11$''$ $\times$ 0.083$''$, respectively." (Observations); "the final full-width half maximum (FWHM) beam size is $\theta = 0.12$$''$" (Observations)
- final rms: continuum ~0.017 mJy/beam; H40alpha 0.50 mJy/beam per 8.9 km/s; H42alpha 0.48 mJy/beam per 10.3 km/s  
  > "The rms noise away from the source is $\approx$0.017 mJy beam$^{-1}$, equivalent to 0.2 K in Rayleigh-Jeans brightness temperature units." (Observations); "The typical rms in the H40$\alpha$ cube is 0.50 mJy beam$^{-1}$ per 8.9 km s$^{-1}$ channel." (Observations)

### Inherited from earlier work

- Helium ionization ratio y = 0.10 adopted from earlier work  
  > "which we fix as $y = 0.10$ (cite: DePree1996; Mills2020)." (5.3 Temperature and Metallicity) [from (cite: DePree1996; Mills2020)]
- Comparison apertures (N, C, S) matched to those of an earlier H42alpha analysis  
  > "We approximately matched the locations of these apertures to those defined in (cite: Bendo2016), in which H42$\alpha$ was analyzed at 2.3$''$ resolution" (4.2.2 H42alpha Contamination) [from (cite: Bendo2016)]
- Free-free absorption models of synchrotron sources taken from LBA 2.3 GHz work and associated by position (within 0.06 arcsec)  
  > "When a source identified by (cite: Lenc2009) lies within 0.06$''$ (half the beam FWHM) of the 93 GHz source, we associate the low-frequency modeling with the 93 GHz source." (3.2 Point Source Flux Extraction) [from (cite: Lenc2009)]
- NGC 4945 is the second object of an ALMA campaign on massive star clusters in starbursts; NGC 253 analysis used as comparison and methodological parent  
  > "NGC 4945 is the second object we target in a campaign to characterize massive star clusters in local starbursts with ALMA." (Introduction) [from (cite: Leroy2018; Mills2020)]

### Not stated but needed to reproduce (our reading)

- Calibration details: pipeline vs manual, CASA/pipeline version used for calibration, flux/bandpass/phase calibrators, flux scale uncertainty, any self-calibration
- tclean parameters: deconvolver, niter/threshold, cell size, image size, CLEAN mask threshold and construction, number of Taylor terms, restoring beam commands
- Which channels were treated as line-free for continuum imaging and for the uv-plane polynomial continuum subtraction, and which spectral lines were flagged
- Details of how the 350 GHz and 2.3 GHz images were aligned astrometrically and convolved, and the 350 GHz cell/image settings
- The simulation used to decompose the in-band spectral index into free-free, synchrotron and dust fractions: assumed intrinsic indices and distributions, how errors on f_ff, f_syn, f_d were derived (referenced only to Section 3.3)
- PyBDSF parameters beyond the island (7 sigma) and peak (10 sigma) thresholds (rms box, adaptive rms, fitting options)
- Fitting method for the cluster mass function power law (binning, estimator, completeness limit values, error propagation)
- Starburst99 version and input parameters beyond IMF/maximum mass (metallicity, tracks, atmosphere models)
- Source of the adopted 3.8 Mpc distance
- Exact list of ALMA execution blocks / observation dates and total integration time per configuration

## Analysis recipe

1. **Image continuum and recombination line cubes**: Line-free-channel full-bandwidth continuum image plus per-spw images; uv-plane polynomial continuum subtraction for lines; CLEAN mask from continuum; Briggs r=0.5; convolve to circular beams; boxcar-smooth cubes  
  > "Then we create a continuum image using the full bandwidth of the line-free channels." (Observations); "Then, we image by applying a CLEAN mask (to all channels) derived from the full-bandwidth continuum image." (Observations); "After imaging, we convolved the continuum and line images to convert from an elliptical to a round beam shape." (Observations)
   - software: CASA 5.4.0
   - parameter: Briggs robust = 0.5  
  > "For all images, we use Briggs weighting with a robust parameter of $r=0.5$." (Observations)
   - parameter: line cubes smoothed to 2.93 MHz channels (8.9 and 10.3 km/s)  
  > "We boxcar smoothed the spectral cubes from the native 0.488 MHz channel width to 2.93 MHz." (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify candidate clusters as compact 93 GHz sources**: PyBDSF island/Gaussian finding with 7 sigma island and 10 sigma peak thresholds; remove sources outside starburst, blended sources, and those below 10 sigma after aperture photometry  
  > "Islands are defined as contiguous pixels above a threshold of seven times the global rms value of $\sigma \approx 0.017$ mJy beam$^{-1}$." (3.1 Point Source Identification); "Within each island, multiple Gaussians may be fit, each with a peak amplitude greater than the peak threshold, a threshold of ten times the global rms." (3.1 Point Source Identification); "As a result, we analyze 29 sources as candidate star clusters." (3.1 Point Source Identification)
   - software: PyBDSF
   - parameter: island threshold 7 x rms; peak threshold 10 x rms; blend rejection for offsets < 0.12 arcsec  
  > "We also removed $3$ sources that appeared blended, with an offset $<0.12$$''$ from another source." (3.1 Point Source Identification)
   - assumption: Compact 93 GHz sources are candidate massive star clusters, with possible contamination by synchrotron-dominated supernova remnants or dusty protoclusters  
  > "We take into consideration the point-like sources detected at 93 GHz as candidate massive star clusters, though some contamination by synchrotron-dominated supernova remnants or dusty protoclusters may still be possible." (3 Continuum Emission)
   - fitting: Gaussians fitted and subtracted starting from the brightest peak  
  > "Starting with the brightest peak, Gaussians are fit and cleaned (i.e., subtracted)." (3.1 Point Source Identification)
   - validation: Visual comparison  
  > "The sources match well with what we would identify by eye." (3.1 Point Source Identification)
3. **Measure source flux densities at 2.3, 93 and 350 GHz**: Aperture photometry at the source peak with local median annulus background subtraction after convolving to common 0.12 arcsec resolution; 3 sigma upper limits for non-detections  
  > "Before extracting the continuum flux at 2.3 GHz, we convolve the image to the common resolution of 0.12$''$." (3.2 Point Source Flux Extraction); "Then we subtract the extended background continuum that is local to the source by taking the median flux density within an annulus of inner diameter 0.24$''$ and outer diameter 0.30$''$" (3.2 Point Source Flux Extraction)
   - parameter: aperture diameter 0.24 arcsec; background annulus 0.24-0.30 arcsec  
  > "We extract the flux density at the location of the peak source within an aperture diameter of 0.24$''$." (3.2 Point Source Flux Extraction)
   - parameter: 3 sigma upper limit when flux < 3 x global rms  
  > "When the extracted flux density within an aperture is less than three times the global rms noise , we assign a three sigma upper limit to that flux measurement." (3.2 Point Source Flux Extraction)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive in-band spectral index and free-free, synchrotron, dust fractions**: First-order polynomial fit to five continuum flux measurements (four spws plus full band) per source; mixtures of the three emission mechanisms are simulated to match the observed in-band index and give fractional contributions  
  > "We fit a first order polynomial to the five continuum measurements – four from each spectral window, one from the full bandwidth image." (3.3.1 Band 3 Spectral Index); "To do this, we simulate how mixtures of synchrotron, free-free, and dust emission could combine to create the observed in-band index." (3.3.2 Decomposing the fractional contributions of emission type)
   - software: CASA
   - parameter: Same apertures as flux extraction; median uncertainty of spectral indices 0.13  
  > "The median uncertainty of the spectral indices is 0.13." (3.3.1 Band 3 Spectral Index)
   - assumption: Free-free fraction defined via S_ff = f_ff * S_93  
  > "We will determine a free-free fraction, $f_{\mathrm{ff}}$, and let $S_{\mathrm{ff}} = f_{\mathrm{ff}} S_{93}$." (3.3 Free-free Fraction at 93 GHz)
   - fitting: Linear (first order) polynomial fit, 1 sigma uncertainty from fit  
  > "The fit to the in-band spectral index is listed in Table [\[tab:continuum\]](#tab:continuum) with the one sigma uncertainty to the fit." (3.3.1 Band 3 Spectral Index)
   - validation: Compared with the tclean spectral index for bright sources  
  > "The spectral indices measured in this way were consistent for the brightest sources with the index determined by `CASA tclean`" (3.3.1 Band 3 Spectral Index)
5. **Extract and fit recombination line spectra of individual sources**: Extract H40alpha and H42alpha spectra in 0.4 arcsec apertures, interpolate to a 10.3 km/s grid, weight by inverse variance and average to an effective H41alpha profile, fit Gaussians  
  > "We extract H40$\alpha$ and H42$\alpha$ spectra at the location of each source with an aperture diameter of 0.4$''$, or twice the beam FWHM." (4 Recombination Line Emission); "weight each spectrum by $\sigma_{\mathrm{rms}}^{-2}$ where $\sigma_{\mathrm{rms}}$ is the spectrum standard deviation, and average the spectra together lowering the final noise." (4 Recombination Line Emission)
   - software: CASA
   - parameter: detection threshold: integrated signal > 5 sigma_rms  
  > "We report on detections with an integrated signal of $>5\sigma_{\mathrm{rms}}$." (4 Recombination Line Emission)
   - assumption: H40alpha and H42alpha spectra are virtually identical and can be averaged  
  > "In principle, we expect the spectra to be virtually identical, which is why we average them to improve the signal-to-noise at high-resolution." (4.2.2 H42alpha Contamination)
   - fitting: Single Gaussian per feature; integrated S/N within +/- 1 sigma of the fit  
  > "We fit spectral features with a Gaussian profile." (4 Recombination Line Emission)
   - validation: Central velocities compared with disk rotation and the 0.7 arcsec H40alpha spectra  
  > "To do this, we overlay our spectra on H40$\alpha$ spectra extracted from the intermediate configuration observations (0.7$''$ resolution)." (4 Recombination Line Emission)
6. **Measure total line flux of the starburst and test H42alpha contamination**: Optimize elliptical aperture templates (T1 for extended, T2 for intermediate configuration) from a 2D Gaussian fit to the 0.7 arcsec continuum, extract total H40alpha spectra, fit two Gaussians; compare H40alpha and H42alpha fluxes in N, C, S apertures  
  > "We independently vary the major and minor axes (in multiples of $0.5\sigma_{\mathrm{maj}}$ and $0.5\sigma_{\mathrm{min}}$, respectively) in order to determine the aperture which maximizes the total integrated signal in channels within $\pm 170$ km s$^{-1}$." (4.2.1 Total Emission from the Starburst Region); "We fit the features with two Gaussians." (4.2.1 Total Emission from the Starburst Region)
   - software: CASA
   - parameter: T1 aperture 8.4 x 1.5 arcsec (extended cube); T2 aperture 12.0 x 2.9 arcsec (intermediate cube)  
  > "we find the largest integrated line emission with an aperture of 8.4$''$ $\times$ 1.5$''$, which we refer to as T1." (4.2.1 Total Emission from the Starburst Region)
   - fitting: Two Gaussian components for double-horn profiles  
  > "We fit the spectrum using the sum of two Gaussian components." (4 Recombination Line Emission)
   - validation: H42alpha fluxes consistent within 2 sigma with an earlier 2.3 arcsec analysis  
  > "the integrated line emission is also consistent (within 2$\sigma$)" (4.2.2 H42alpha Contamination)
7. **Derive electron temperature and metallicity**: Solve the line-to-continuum flux ratio (using the free-free fraction re-evaluated at 0.2 arcsec) for Te for 5 bright, well-fit sources; adopt mean Te; convert to O/H via the Shaver relation  
  > "Dependencies on the distance, emission measure, and (possible) beam-filling effects cancel out under the assumption that the two tracers arise in the same volume of gas." (5.3 Temperature and Metallicity); "To derive the temperatures, we re-evaluate the continuum (fraction of) free-free emission at the resolution of 0.2$''$, since the free-free fraction may change with resolution." (5.3 Temperature and Metallicity)
   - parameter: b_n = 0.73; y = 0.10; 5 sources with peak S/N > 4.7 sigma  
  > "take $b_{\mathsf{n}} = 0.73$ (cite: Storey1995)" (5.3 Temperature and Metallicity); "We focus on the 5 sources with bright (peak S/N $>4.7\sigma$) and well-fit recombination line emission." (5.3 Temperature and Metallicity)
   - assumption: Line and continuum arise in the same gas volume; b_n iterated once  
  > "We iterate (once) on the input $b_{\mathsf{n}}$ and output temperature." (5.3 Temperature and Metallicity)
   - fitting: _not stated_
   - validation: Te consistent with 5400 +/- 600 K from a 2.3 arcsec analysis  
  > "which finds $T_e = (5400 \pm 600)$ K (cite: Bendo2016)." (5.3 Temperature and Metallicity)
8. **Derive emission measure, electron density and ionized gas mass**: EM from the free-free continuum (and line) using Te; density assuming a sphere of radius FWHM/2; ionized mass M = 1.36 m_H n V  
  > "We use the emission measure determined from the free-free continuum, assume $n_e = n_+$, and consider a spherical volume with $r = \mathrm{FWHM_{size}} / 2$." (5.4 Ionized Gas: Emission Measure, Density and Mass)
   - parameter: Te = 6000 K; uncertainty ~0.4 dex dominated by free-free fraction  
  > "The uncertainty in the emission measures is $\sim$0.4 dex and is dominated by the errors of the free-free fraction." (5.4 Ionized Gas: Emission Measure, Density and Mass)
   - assumption: 1.36 factor for helium by mass; spherical geometry with r = FWHM/2  
  > "where we have assumed a 1.36 contribution of helium by mass and we let $r = \mathrm{FWHM_{size}} / 2$." (5.4 Ionized Gas: Emission Measure, Density and Mass)
   - fitting: _not stated_
   - validation: Density cross-checked using free-free optical depths of five matched 2.3 GHz sources  
  > "This agrees well with the values we separately derive." (5.4 Ionized Gas: Emission Measure, Density and Mass)
9. **Compute ionizing photon rate and stellar mass**: Q0 from continuum EM with case B recombination coefficient; stellar mass from Q0 using Starburst99 5 Myr output per unit mass  
  > "From the emission measure of ionized gas and the temperature-dependent recombination coefficient for case B recombination, the rate of ionizing photons" (5.5 Ionizing Photon Production and Stellar Mass); "Then we divide the ionizing photon output at 5 Myr by the initial mass of the stellar population." (5.5 Ionizing Photon Production and Stellar Mass)
   - software: Starburst99
   - parameter: Kroupa IMF, max stellar mass 100 Msun, default tracks, 1e6 Msun population  
  > "We arrive at this value by simulating a single $10^6$ M$_{\odot}$ stellar population, with the initial mass function (IMF) of (cite: Kroupa2001), a maximum stellar mass of 100 M$_{\odot}$, and the default stellar evolution tracks and tuning parameters." (5.5 Ionizing Photon Production and Stellar Mass)
   - assumption: Instantaneous burst about 5 Myr ago (uncertainty ~1 Myr)  
  > "Throughout our analysis, we assume that the candidate star clusters formed in an instantaneous burst of star-formation roughly 5 Myr ago (with a likely uncertainty of $\sim$1 Myr)." (5.2 Age)
   - fitting: _not stated_
   - validation: Admitted rough approximation, no correction for dust absorption, mass ejection or binaries  
  > "We note that this is a rough approximation which has not accounted for the amount of ionizing photons absorbed by dust, mass ejected from the system, and/or enhanced emission from stellar binaries." (5.5 Ionizing Photon Production and Stellar Mass)
10. **Estimate gas mass from 350 GHz dust emission**: Convert 350 GHz flux to intensity, solve optical depth with Planck function at Tdust, convert to gas surface density with kappa and DGR, multiply by source area  
  > "We determine the dust optical depth by comparing the measured intensity with that expected from an estimate of the true dust temperature." (5.6 Gas Mass from Dust); "We determine the gas mass by multiplying the gas surface density by the two dimensional area of the source size" (5.6 Gas Mass from Dust)
   - parameter: Tdust = 130 K  
  > "We assume a dust temperature of $T_{\mathrm{dust}} = 130$ K" (5.6 Gas Mass from Dust)
   - parameter: kappa = 1.9 cm2/g  
  > "We adopt $\kappa = 1.9$ cm$^2$ g$^{-1}$" (5.6 Gas Mass from Dust)
   - parameter: DGR = 1/100  
  > "an adopted dust-to-gas mass ratio (DGR) of 1-to-100" (5.6 Gas Mass from Dust)
   - assumption: Optically thin dust emission (tau_350 ~0.02-0.10)  
  > "We measure optical depths in the range $\tau_{350} \sim$ 0.02 – 0.10, with a median value of $\tau_{350} \sim 0.04$, justifying our optically thin assumption." (5.6 Gas Mass from Dust)
   - fitting: _not stated_
   - validation: Admitted factor-of-2 kappa uncertainty; Tdust an approximation  
  > "but we do note the large (factor of 2) uncertainties on this value." (5.6 Gas Mass from Dust)
11. **Compute total mass, surface density and free-fall time**: M_Tot = M_gas + M_star; surface density within FWHM; t_ff = (pi r^3 / 8 G M_Tot)^(1/2)  
  > "We estimate the current total mass of each candidate star cluster as the sum of the gas and star masses, where $M_{\mathrm{Tot}} = M_{\mathrm{gas}} + M_{\star}$." (5.7 Total Mass from Gas and Stars); "we estimate the gravitational free fall time of the clusters, $t_{\mathrm{ff}} = \left( \frac{ \pi r^3 }{ 8 G M_{\mathrm{Tot}} } \right)^{1/2}$." (5.7 Total Mass from Gas and Stars)
   - parameter: Sources not detected at 350 GHz: only stellar mass used in total  
  > "we only consider the stellar mass." (5.7 Total Mass from Gas and Stars)
   - assumption: Free-fall time assumes gas with no support and the whole cluster mass in gas  
  > "This is the gravitational free fall time that would be experienced by gas with no support if all of the cluster mass were gas." (5.7 Total Mass from Gas and Stars)
   - fitting: _not stated_
   - validation: _not stated_
12. **Fit the cluster stellar-mass function**: Power-law fit to the cluster mass distribution of 22 sources above the completeness limit; compare with NGC 253 and literature slopes  
  > "A power-law fit to the cluster mass distribution, of 22 sources down to $M_{\star} = 2.4 \times 10^5$ M$_{\odot}$, in NGC 4945 results in a slope of $\beta = -1.8 \pm 0.4$." (6.3 Cluster Mass Function)
   - parameter: completeness limit 2.4e5 Msun; adopted conservative uncertainty reflecting 0.4 dex mass error  
  > "Note that the fit to the data results in $\beta = -1.76 \pm 0.07$, but given the uncertainty in our mass estimates (0.4 dex), we adopt the conservative figure." (6.3 Cluster Mass Function)
   - fitting: Power law; estimator, binning and priors not stated  
  > "A power-law fit to the cluster mass distribution, of 22 sources down to $M_{\star} = 2.4 \times 10^5$ M$_{\odot}$" (6.3 Cluster Mass Function)
   - validation: Completeness limits estimated by eye; slope compared with NGC 253 and Mok et al.  
  > "We estimated the completeness limits by eye." (6.3 Cluster Mass Function)
13. **Compare cluster ionizing photons with the total burst, diffuse gas and AGN limit**: Convert T1 and T2 H40alpha fluxes to Q with Te = 6000 K; compare cluster sum with T1/T2; test AGN contribution in 7 apertures along the major axis; AGN leakage limit from Q0 of the 93 GHz point source versus expected Lion from X-ray Lbol  
  > "Assuming the temperature of $T_e = (6000\pm400)$ K from Section [5.3](#sec:temp), the total ionized content, which accounts for the full star-formation rate of the starburst, yields an ionizing photon rate of $Q_{\mathrm{T2}} = (3.9 \pm 0.3) \times 10^{53}$ s$^{-1}$." (6.4 Ionizing Photons and Diffuse Ionized Gas); "We test this scenario by extracting spectra from the 0.7$''$ intermediate-configuration data and the 0.2$''$ extended-configuration data in 7 non-overlapping apertures of 3$''$ diameter consecutively distributed along the major axis of the starburst region." (6.4 Ionizing Photons and Diffuse Ionized Gas)
   - parameter: AGN: Lbol ~ 20 Lx; Lbol/Lion ~ 3; Te = 6000 or 30000 K  
  > "If we assume a temperature of $T_e = 6000$ (30 000) K this would correspond to $Q_0 = 1.1 \,(0.5) \times 10^{52}$ s$^{-1}$." (6.5 Role of the AGN)
   - assumption: Additional intermediate-configuration line emission assumed to come from a 5 Myr old population  
  > "Also, this calculation assumes the source of the additional recombination line emission in the intermediate-configuration data is also characterized by a 5 Myr old stellar population." (6.5 Total Burst of Star-formation)
   - fitting: _not stated_
   - validation: Missing line flux in extended data treated as an upper limit because of low S/N and uv coverage  
  > "However, a missing 70% of line flux in the 0.2$''$ resolution data should be considered as an upper limit." (6.4 Ionizing Photons and Diffuse Ionized Gas)

## Software

- **CASA** 5.4.0: analysis/imaging of the observatory-calibrated visibilities  
  > "We analyze the observatory-provided calibrated visibilities using version 5.4.0 of the Common Astronomy Software Application (cite: McMullin2007)." (Observations)
- **tclean (CASA)** : comparison spectral index for bright sources  
  > "The spectral indices measured in this way were consistent for the brightest sources with the index determined by `CASA tclean`" (3.3.1 Band 3 Spectral Index)
- **PyBDSF** : source finding and 2D Gaussian size fits of 93 GHz sources  
  > "The sources identified through `PyBDSF` in the 93 GHz continuum image are fit with two dimensional Gaussians." (5.1 Size)
- **Starburst99** : ionizing photon output per unit stellar mass at 5 Myr; Lbol/L0 and mechanical output of the clusters  
  > "We use Starburst99 calculations (cite: Leitherer1999) to infer the stellar mass from the ionizing photon output of a 5 Myr old stellar population" (5.5 Ionizing Photon Production and Stellar Mass)
- **Astropy** : listed in the Software section; specific use not stated  
  > "APLpy (cite: Robitaille2012), Astropy (cite: Astropy2018), CASA (cite: McMullin2007), CRRLpy (cite: Salas2016), Matplotlib (cite: Hunter2007), PyBDSF (cite: Mohan2015)." (Software)
- **APLpy** : listed in the Software section; specific use not stated  
  > "APLpy (cite: Robitaille2012), Astropy (cite: Astropy2018), CASA (cite: McMullin2007), CRRLpy (cite: Salas2016), Matplotlib (cite: Hunter2007), PyBDSF (cite: Mohan2015)." (Software)
- **CRRLpy** : listed in the Software section; specific use not stated  
  > "APLpy (cite: Robitaille2012), Astropy (cite: Astropy2018), CASA (cite: McMullin2007), CRRLpy (cite: Salas2016), Matplotlib (cite: Hunter2007), PyBDSF (cite: Mohan2015)." (Software)
- **Matplotlib** : listed in the Software section; specific use not stated  
  > "APLpy (cite: Robitaille2012), Astropy (cite: Astropy2018), CASA (cite: McMullin2007), CRRLpy (cite: Salas2016), Matplotlib (cite: Hunter2007), PyBDSF (cite: Mohan2015)." (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of candidate super star clusters | 27 | not stated | dimensionless | 2 | Our observations reveal 27 bright, compact sources with FWHM sizes of 1.4–4.0 pc, which we identify as candidate super star clusters. |
| FWHM sizes of candidate clusters | 1.4-4.0 | not stated | pc | 2 | Our observations reveal 27 bright, compact sources with FWHM sizes of 1.4–4.0 pc, which we identify as candidate super star clusters. |
| Sources with detected recombination lines | 15 | not stated | dimensionless | 5 | Recombination line emission, tracing the ionizing photon rate of the candidate clusters, is detected in 15 sources, 6 of which have a significant synchrotron component to the 93 GHz continuum. |
| Median free-free fraction at 93 GHz | 0.62 | not stated | dimensionless | 4 | We find, at this 0.12$''$ resolution, the median free-free fraction of sources is $f_{\mathrm{ff}} = 0.62$ . |
| Median synchrotron fraction at 93 GHz | 0.36 | not stated | dimensionless | 4 | with a median fraction of $f_{\mathrm{syn}} = 0.36$ |
| Electron temperature (mean of 5 sources) | 6000 | +/-400 | K | 7 | We take the mean and standard deviation values of $T_e = (6000 \pm 400)$ K as a representative electron temperature of the ionized plasma in the candidate star clusters. |
| Representative metallicity 12+log10(O/H) | 8.9 | 0.1 | dex | 7 | We find a representative O/H metallicity of $12 + \log_{10}(\mathrm{O/H}) = 8.9 \pm 0.1$. |
| Continuum emission measure range (log EM_C) | 7.3-8.7 (median 8.4) | ~0.4 dex | cm^-6 pc^3 | 8 | Emission measures that we determine from the free-free continuum range from $\log_{10} (EM_{\mathrm{C}} / \mathrm{cm^{-6} \, pc^3}) \sim 7.3$ – 8.7, with a median value of 8.4. |
| Electron density range (log n_e) | 3.1-3.9 (median 3.5) | not stated | cm^-3 | 8 | We arrive at densities between $\log_{10} (n_e/\mathrm{cm}^{-3})= 3.1$–3.9 with a median value of 3.5. |
| Ionized gas mass range (log M+) | 2.7-3.5 (median 3.1) | not stated | Msun | 8 | The ionized gas masses of the candidate star clusters range from $\log_{10} (M_+$ / M$_{\odot}$) = 2.7 – 3.5 with a median value of 3.1. |
| Ionizing photon rate range (log Q0) | 50.4-51.8 | ~0.4 dex | s^-1 | 9 | Our candidate star clusters have ionizing photon rates in the range $\log_{10} (Q_0 / \mathrm{s}^{-1}) \sim 50.4$ – 51.8. |
| Sum of Q0 over all candidate clusters | 5.3e52 | not stated | s^-1 | 9 | The sum of the ionizing photon rate over all candidate, massive star clusters is $5.3 \times 10^{52}$ s$^{-1}$. |
| Cluster stellar mass range (log M*) | 4.7-6.1 (median 5.5) | ~0.4 dex | Msun | 9 | Our candidate star clusters have stellar masses in the range $\log_{10} ( M_{\star} / \mathrm{M_{\odot}} ) \sim$ 4.7–6.1 (see Table [\[tab:props\]](#tab:props)) with a median of 5.5. |
| Sum of cluster stellar masses | 1.1e7 | not stated | Msun | 9 | The sum of the stellar masses of the candidate stars clusters is $\approx 1.1 \times 10^7$ M$_{\odot}$. |
| Gas mass range (log M_gas) | 4.4-5.1 (median 4.7) | not stated | Msun | 10 | We find values in the range of $\log_{10} (M_{\mathrm{gas}}$ / M$_{\odot}$) = 4.4 – 5.1 with a median value of 4.7. |
| 350 GHz dust optical depth | 0.02-0.10 (median 0.04) | not stated | dimensionless | 10 | We measure optical depths in the range $\tau_{350} \sim$ 0.02 – 0.10, with a median value of $\tau_{350} \sim 0.04$ |
| Gas mass fraction M_gas/M_Tot | 0.04-0.22 (median 0.13) | not stated | dimensionless | 11 | we find low gas mass fractions of $M_{\mathrm{gas}} / M_{\mathrm{Tot}} =$ 0.04 – 0.22 and a median of 0.13 |
| Free-fall time (log t_ff) | 4.3-5.2 (median 4.6) | not stated | yr | 11 | range from $\log_{10} (t_{\mathrm{ff}}$ / yr ) = 4.3 – 5.2 with a median of 4.6 |
| Total mass within candidate clusters | 1.5e7 | not stated | Msun | 11 | Summing all sources, we find a total mass within the candidate clusters of $M_{\mathrm{Tot}} \approx 1.5 \times 10^7$ M$_{\odot}$. |
| Cluster mass function slope beta (NGC 4945) | -1.8 | 0.4 | dimensionless | 12 | We fit a slope to the cluster mass distribution and find $\beta = -1.8 \pm 0.4$. |
| Cluster mass function slope beta (NGC 253) | -1.6 | 0.3 | dimensionless | 12 | A power-law fit to the cluster mass distribution of NGC 253, including 12 star clusters down to $M_{\star} = 7.9\times 10^4$ M$_{\odot}$, results in a slope of $\beta = -1.6 \pm 0.3$. |
| Total H40alpha flux in T2 aperture (0.7 arcsec data) | 6.4 | 1.0 | Jy km/s | 6 | The sum total of their integrated line flux is ($6.4 \pm 1.0$) Jy km s$^{-1}$. |
| Total H40alpha flux in T1 aperture (0.2 arcsec data) | 2.1 | 0.6 | Jy km/s | 6 | The sum total area of the fits is ($2.1\pm0.6$) Jy km s$^{-1}$. |
| Total ionizing photon rate of the burst (T2) | 3.9e53 | 0.3e53 | s^-1 | 13 | yields an ionizing photon rate of $Q_{\mathrm{T2}} = (3.9 \pm 0.3) \times 10^{53}$ s$^{-1}$. |
| Ionizing photon rate in T1 aperture | 1.2e53 | 0.4e53 | s^-1 | 13 | the integrated line flux corresponds to an ionizing photon rate of $Q_{\mathrm{T1}} = (1.2 \pm 0.4) \times 10^{53}$ s$^{-1}$. |
| Fraction of total ionizing photons attributed to the candidate SSCs | 20-44 | not stated | percent | 13 | we conclude that 20% to 44% of the total ionizing photons in the starburst can be attributed to the candidate super star clusters identified in NGC 4945. |
| Ratio of line flux in intermediate to extended configuration (7 apertures) | 2.3 | 0.5 | dimensionless | 13 | the ratios in the seven regions have a mean and standard deviation of $2.3 \pm 0.5$. |
| In-band spectral index of the presumed AGN (alpha_93) | -0.85 | 0.05 | dimensionless | 4 | The Band 3 spectral index we derive is $\alpha_{93} = -0.85 \pm 0.05$ |
| AGN 93 GHz flux density | 9.7 | 1.0 | mJy | 3 | The flux of $9.7 \pm 1.0$ mJy that we extract from the source is $\sim10$% of the total continuum ($\sim$120 mJy) flux in the 0.12$''$ resolution data. |
| Upper limit on AGN ionizing photons leaking into the starburst | <1e52 | not stated | s^-1 | 13 | We do not detect recombination line emission from the AGN and place an upper limit on the ionizing photons which leak into the starburst region of $Q_0 < 10^{52}$ s$^{-1}$. |
| Inferred total stellar mass of the burst | 8.5e7 | not stated | Msun | 13 | the inferred total stellar mass of the population is $\sim 8.5 \times 10^7$ M$_{\odot}$. |
| H42alpha / H40alpha integrated flux ratio over entire starburst | ~2 | not stated | dimensionless | 6 | We find that the integrated line emission of H42$\alpha$ is enhanced compared with H40$\alpha$, reaching a factor of 2 greater when integrated over the entire starburst region. |

## Qualitative findings

- Candidate clusters are already largely converted to stars (low gas fractions, short free-fall times) and are likely to remain bound at least initially  
  > "The fact that the gas mass fractions are low and that the age appears longer than the free fall time adds support to the idea that these clusters have mostly already formed." (5.7 Total Mass from Gas and Stars); "these star clusters will likely remain bound, at least initially." (6.2 Super Star Clusters)
- Much of the recombination line flux in the low-resolution data comes from scales >100 pc, possibly diffuse ionized gas or low-mass clusters, and cannot be directly attributed to the AGN  
  > "we find that up to $\sim$70% of the total radio recombination line flux may originate on scales larger than $\sim$100 pc; this emission cannot be directly attributed to the AGN." (6.4 Ionizing Photons and Diffuse Ionized Gas)
- H42alpha is likely contaminated by another species (possibly c-C3H2) in low-resolution/broad profiles, overestimating recombination flux by about a factor of 2  
  > "we find this spectral line is likely contaminated by line emission from other species, resulting in the recombination line flux (and star-formation rates derived from it) being overestimated by a factor of $\sim$2, when compared to a similar analysis of H40$\alpha$." (Summary)
- Neither energetics nor momentum of the warm ionized outflow rule out it being driven by the star clusters  
  > "Therefore, neither the energetics nor the inferred momentum of the outflow prevent it from being driven solely by the star clusters in NGC 4945, although there are very considerable uncertainties associated with this calculation." (6.6 Star Clusters and the Central Wind)

## Claim tuples

- H: Compact 93 GHz sources in the NGC 4945 nuclear starburst are young massive (super) star clusters | E: Source finding in 0.12 arcsec ALMA Band 3 continuum, size fits, free-free/recombination-line derived ionizing photon rate and stellar mass | R: 27 sources with FWHM 1.4-4.0 pc, log M* 4.7-6.1, RRLs detected in 15 | F: The sources meet criteria for super star clusters | **supported**
- H: The cluster mass function of NGC 4945 resembles that of NGC 253 and other galaxies | E: Power-law fit to the stellar mass distribution of 22 clusters above the completeness limit | R: beta = -1.8 +/- 0.4 versus -1.6 +/- 0.3 in NGC 253 and -2.0 +/- 0.3 for six galaxies from the literature | F: Slopes are consistent | **supported**
- H: The candidate clusters have already converted much of their natal gas into stars | E: Gas masses from 350 GHz dust emission compared with stellar masses; free-fall times from total mass | R: Gas mass fractions 0.04-0.22 (median 0.13); log t_ff 4.3-5.2 yr | F: Clusters have converted a large fraction of dense natal material to stars and are surviving an early volatile phase | **supported**
- H: The candidate clusters account for the ionizing photons of the whole starburst | E: Compare summed cluster Q0 with total H40alpha line flux in extended (0.2 arcsec) and intermediate (0.7 arcsec) configurations | R: Clusters account for 20-44% of Q; intermediate data show ~2.3x more line flux than extended data | F: A large part of the ionizing photons comes from larger scales (diffuse gas or low-mass clusters), not the clusters or AGN; treated as an upper limit | **partially**
- H: The AGN contributes ionizing photons to the surrounding starburst | E: Identify the 93 GHz point source, measure its spectral index, search for recombination lines, estimate leakage vs expected Lion from X-ray Lbol | R: alpha_93 = -0.85 +/- 0.05; no RRL detection; Q0 < 1e52 s^-1; <10% of expected AGN ionizing luminosity escapes | F: UV ionizing radiation from the AGN is heavily obscured in all directions | **supported**
- H: H42alpha is a reliable low-resolution tracer of ionizing radiation | E: Compare H40alpha and H42alpha profiles and fluxes in the 0.7 arcsec data in N, C, S and total regions | R: H42alpha/H40alpha flux ratios 1.4-2.0 with extra emission at +100 to +250 km/s | F: H42alpha is contaminated by other species at low resolution and for broad profiles | **supported**

## Reasoning

- Why this data: Free-free continuum and recombination lines are extinction-free probes of ionized gas around young clusters, and ALMA gives the resolution needed to resolve cluster scales  
  > "offer an alternative, extinction-free probe of the ionizing gas surrounding young star clusters" (Introduction); "has only recently become possible thanks to the Atacama Large Millimeter/submillimeter Array (ALMA)." (Introduction)
- Why this method: Briggs robust 0.5 chosen as a resolution/sensitivity compromise; 10 sigma peak threshold chosen so sources are identifiable in per-spw continuum images  
  > "which represents a good compromise between resolution and surface brightness sensitivity" (Observations); "We chose this peak threshold to ensure that significant emission can also be identified in the continuum images made from individual spectral windows." (3.1 Point Source Identification)
- Alternative: Missing line flux in extended-configuration data attributed primarily to low-mass clusters: judged unlikely  
  > "We do not find it likely that the deficit of line emission in the extended-configuration data can be attributed primarily to low mass clusters." (6.4 Ionizing Photons and Diffuse Ionized Gas)
- Alternative: Extra H42alpha emission as maser-like hydrogen recombination emission: rejected  
  > "It is not likely to be a maser-like component of hydrogen recombination emission since the relative flux does not greatly vary in different extraction regions" (4.2.2 H42alpha Contamination)
- Alternative: tclean in-band spectral index versus the five-point polynomial fit: latter preferred for faint sources  
  > "however, we found our method to be more reliable for the fainter sources." (3.3.1 Band 3 Spectral Index)
- How they decided it was enough: _not stated_
- Limitation (authors): Free-free fraction assumptions, especially synchrotron, affect individual clusters at ~30% level  
  > "Overall, the assumptions , especially regarding synchrotron emissions, likely affect individual clusters at the $\sim 30\%$ level." (6.1 Discussion of uncertainties)
- Limitation (authors): Assumed 5 Myr age is a large systematic: 1 Myr uncertainty changes stellar mass by a factor of four  
  > "An uncertainty of $\sim$1 Myr about an age of 5 Myr of a star cluster results in an uncertainty in the inferred stellar mass by a factor of four." (6.1 Discussion of uncertainties)
- Limitation (authors): Dust opacity uncertain by a factor of 2 and dust temperature approximate  
  > "but we do note the large (factor of 2) uncertainties on this value." (5.6 Gas Mass from Dust); "This is an approximation, though the uncertainty is linear." (5.6 Gas Mass from Dust)
- Limitation (authors): Missing line flux at high resolution is an upper limit because of low S/N and incomplete uv coverage; negative bowls from missing short spacings  
  > "However, a missing 70% of line flux in the 0.2$''$ resolution data should be considered as an upper limit." (6.4 Ionizing Photons and Diffuse Ionized Gas); "The extended, faint negative bowls flanking the main disk likely reflect the short spacing data missing from this image." (3 Continuum Emission)
- Limitation (authors): Stellar mass conversion is a rough approximation; sources may break apart at higher resolution  
  > "We note that this is a rough approximation which has not accounted for the amount of ionizing photons absorbed by dust, mass ejected from the system, and/or enhanced emission from stellar binaries." (5.5 Ionizing Photon Production and Stellar Mass); "Based on high-resolution imaging of embedded clusters in the nucleus of the Milky Way and NGC 253, some of these clusters might break apart at higher resolution" (5.1 Size)
- Caveat (inferred, ours): Stellar masses rest on a single assumed 5 Myr age and an unmodelled dust/leakage correction, so mass-function slope and gas fractions inherit a systematic offset not captured by the 0.4 dex random error
- Caveat (inferred, ours): The spectral-index decomposition into free-free/synchrotron/dust is not specified well enough to reproduce, and the median uncertainty on alpha (0.13) is large for faint sources
- Caveat (inferred, ours): Electron temperature rests on only 5 sources with S/N ~5 and a single b_n value, and feeds all downstream EM, Q0 and mass numbers
- Caveat (inferred, ours): Dust-derived gas masses assume a single Tdust of 130 K taken from NGC 253, a fixed kappa and DGR, and a source size from a Gaussian fit near the resolution limit
- Caveat (inferred, ours): The 20-44% cluster ionizing photon fraction relies on recovering flux between configurations that were imaged separately, with possible deconvolution losses acknowledged by the authors
- Caveat (inferred, ours): Mass function fit is on 22 sources with a completeness limit set by eye and an inflated error

## Reproducibility

- Data public (paper): 2016.1.01135.S described as archival ALMA imaging; public status of 2018.1.01236.S not stated; LBA 2.3 GHz images supplied courtesy of E. Lenc  
  > "We compare the continuum emission at 3 mm with archival ALMA imaging of the $\nu = 350$ GHz ($\lambda \sim 850~\mu$m) continuum (project 2016.1.01135.S, PI: N. Nagar)." (Observations); "We use the Epoch 2 images (courtesy of E. Lenc) that have a native angular resolution slightly higher than the 3 mm ALMA data" (Observations)
- Products in archive: observatory-provided calibrated visibilities and observatory pipeline continuum image used  
  > "We analyze the observatory-provided calibrated visibilities using version 5.4.0 of the Common Astronomy Software Application (cite: McMullin2007)." (Observations); "We use the continuum image provided by the observatory pipeline, which we convolve to have a circular beam FWHM of 0.7$''$" (Observations)
- Missing: Spectral-index decomposition (free-free/synchrotron/dust fraction) recipe and its error model
- Missing: Full tclean settings and line-free channel ranges
- Missing: LBA 2.3 GHz Epoch 2 images (provided privately by E. Lenc) and their alignment with ALMA
- Missing: Starburst99 run configuration beyond IMF/max mass
- Missing: Mass-function fitting code/method details and completeness limit
- Missing: No analysis code or machine-readable tables explicitly released
- Data volume (inferred): Order 100-300 GB of raw measurement sets for two Band 3 configurations plus one Band 7 project (rough inference, not stated in paper)
- Score (inferred): 3/5, ALMA projects are identified and many numeric results and equations are given, but the decomposition recipe, imaging parameters, calibration details and the private LBA data limit exact reproduction
- Rediscovery candidate: no, Public status of the main 3 mm data is not stated in the paper and the key spectral-index decomposition and imaging recipe are incomplete, although results are numeric

## Links

- Method: McMullin2007 (CASA) (Software used to process calibrated visibilities)
- Method: Mohan2015 (PyBDSF) (Source finder used to identify clusters and fit sizes)
- Method: Lenc2009 (2.3 GHz LBA data and free-free absorption SED models for compact radio sources)
- Method: Bendo2016 (Prior H42alpha analysis at 2.3 arcsec used to validate fluxes and apertures)
- Companion: Leroy2018 (Companion NGC 253 ALMA super star cluster analysis used for comparison)
- Companion: Mills2020 (NGC 253 super star cluster properties and recombination line methods)
- Companion: Mok2020 (Homogeneous cluster mass distributions in other galaxies used for slope comparison)
- Related: 2018.1.01236.S (PI A. Leroy)
- Related: 2016.1.01135.S (PI N. Nagar)
- Related: Spitzer IRAC Program 40410 (PI G. Rieke)

## Checks

```json
{
 "quotes": 214,
 "quotes_ok": 214,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 1,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 32,
 "numeric_problems": 0,
 "fill": {
  "facts": 149,
  "stated": 123,
  "rate": 0.826
 },
 "evidence_ok": true
}
```

# ALMA twenty-six arcmin<SUP>2</SUP> survey of GOODS-S at one millimeter (ASAGAO): Source catalog and number counts

`2018PASJ...70..105H` | Publications of the Astronomical Society of Japan 2018 | first author: Hatsukade, Bunyo | arXiv: 1808.04502 | DOI: 10.1093/pasj/psy104

Card schema 1.0 | model claude-opus-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies
- Question: Obtain an unbiased census of faint 1.2 mm sources in a contiguous GOODS-S field, derive number counts, the resolved fraction of the 1.2 mm EBL, IR luminosity functions at z=1-3 and their contribution to the cosmic SFR density at z~2.  
  > "The primary goal of this survey is to obtain a census of galaxies with $L_{\rm IR} \gtrsim 3 \times 10^{11}$ $L_{\odot}$ or SFR $\gtrsim 50$ $M_{\odot}$ yr$^{-1}$ for the understanding of the dust-obscured star-formation history of the Universe." (Introduction); "It is necessary to conduct “unbiased” surveys in a contiguous field rather than collecting discrete fields in order to obtain a census on the population of faint submm sources." (Introduction)
- Target **GOODS-S field (ASAGAO 26 arcmin^2 region, ~5' x 5', 9 tiles)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00098.S, 2012.1.00173.S, 2015.1.00543.S
- bands: Band 6 (1.2 mm); archival HUDF at 1.3 mm and GOODS-ALMA at 1.13 mm  
  > "ALMA band 6 observations of the GOODS-S field were conducted in September 02–29, 2016 for the Cycle 3 program" (Observations); "we also use the ALMA archival data of 1-mm (band 6) surveys in the GOODS-S field of HUDF (cite: dunl17) and GOODS-ALMA (cite: fran18)." (ALMA Archival Data)
- frequencies and spectral setup: Two tunings centred at 262.56 GHz and 253.56 GHz; TDM; 4 basebands per tuning, 2000 MHz spw (15.625 MHz x 128 channels); combined map representative frequency 243.047 GHz  
  > "The center frequencies of the tunings are 262.56 GHz (1.14 mm) and 253.56 GHz (1.18 mm), which were selected to avoid strong atmospheric absorption lines" (Observations); "The correlator was used in the time domain mode (TDM)." (Observations); "The representative frequency of the map is 243.047 GHz (1.23 mm)." (Combined Map)
- continuum bandwidth: 16 GHz nominal (15 GHz effective) centred at 258.6 GHz; ~27 GHz effective in combined data  
  > "providing a total nominal bandwidth of 16 GHz (effective bandwidth of 15 GHz) centered at 258.6 GHz (1.16 mm)." (Observations); "to make a deeper map with the total effective frequency coverage of $\sim$27 GHz" (Combined Map)
- arrays: _not stated_
- configurations: C40-6, 37 execution blocks, 38-45 antennas  
  > "The observations were done in 37 execution blocks in the C40-6 array configuration" (Observations); "The number of available antenna was 38–45." (Observations)
- baselines: 15.065 m to 1770-3247 m  
  > "with a minimum baseline length of 15.065 m and a maximum baseline length ranging from 1770 m to 3247 m." (Observations)
- angular resolution: ASAGAO-only 250 klambda-tapered: 0.51" x 0.45"; combined 250 klambda: 0.59" x 0.53"; untapered 0.30" x 0.24"; 160 klambda 0.83" x 0.72"  
  > "for a 250 k$\lambda$-tapered map with a synthesized beam size of $0.51\ensuremath{''} \times 0.45\ensuremath{''}$" (abstract); "Maps without $uv$-taper (synthesized beam size of $0.30\ensuremath{''} \times 0.24\ensuremath{''}$) and with a $uv$-taper of 160 k$\lambda$ ($0.83\ensuremath{''} \times 0.72\ensuremath{''}$) were also created" (Combined Map)
- max recoverable scale: ~1.2 arcsec  
  > "(maximum recoverable scale of $\theta_{\rm MRS} \approx 1.2\ensuremath{''}$)" (Observations)
- sensitivity: ASAGAO-only 1sigma ~61 uJy/beam (250 klambda); combined ~30 uJy/beam deep region, deepest ~26 uJy/beam  
  > "ASAGAO is a deep ($1\sigma \sim 61$ $\mu$Jy beam$^{-1}$ for a 250 k$\lambda$-tapered map" (abstract); "the central deeper area (the deepest region has $1\sigma \sim 26$ $\mu$Jy beam$^{-1}$) and the rest" (Combined Map)
- time on source: 29 hours on-source (45 hours total)  
  > "The total observing time is 45 hours, and the on-source integration time is 29 hours." (Observations)
- observing dates: September 02-29, 2016  
  > "ALMA band 6 observations of the GOODS-S field were conducted in September 02–29, 2016" (Observations)
- pi or archival as stated: PI program (K. Kohno) plus archival HUDF (PI J. Dunlop) and GOODS-ALMA (PI D. Elbaz) data  
  > "In addition to our data, we also use the ALMA archival data of 1-mm (band 6) surveys in the GOODS-S field of HUDF (cite: dunl17) and GOODS-ALMA (cite: fran18)." (ALMA Archival Data)
- Other facility **VLA (5 cm / 6 GHz survey)**: Radio source positions used to check ALMA astrometry  
  > "the positions of the 5$\sigma$ sources are cross-matched with sources detected in the VLA 5-cm survey ((cite: rujo16), Rujopakarn et al. in prep.)." (Astrometry)
- Other facility **Magellan/FourStar (ZFOURGE)**: K_S-selected counterpart catalog with spectroscopic/photometric redshifts  
  > "We identify $K_S$-band selected sources from the catalog of the `FourStar` galaxy evolution survey (ZFOURGE; (cite: stra16))." (IR Luminosity Function of ASAGAO Sources)
- Other facility **ASTE/AzTEC**: 1.1 mm single-dish sources (GS18, GS21) compared with ASAGAO sources  
  > "Two AzTEC sources identified in (cite: scot10) (AzTEC/GS18 and 21) are located inside the ASAGAO region, and detected as multiple sources in our 4.5$\sigma$ source catalog." (Comparison with AzTEC Sources)
- Other facility **Planck**: EBL measurements at 217 and 353 GHz interpolated to 1.2 mm  
  > "The EBL at 1.2 mm (243 GHz) is estimated from the measurements by the *Planck* satellite (cite: plan14) following (cite: arav16) and (cite: muno17)." (Contribution to Extragalactic Background Light)
- External data: ALMA HUDF 1.3 mm survey visibilities and source list  
  > "The archival data sets of HUDF (cite: dunl17) and GOODS-ALMA (cite: fran18) are combined to the original ASAGAO data to make a deeper map" (Combined Map) [from (cite: dunl17)]
- External data: GOODS-ALMA 1.13 mm survey visibilities and source list  
  > "A wider area of 69 arcmin$^2$ ($\sim$$10' \times 7'$) was observed in the GOODS-ALMA survey (cite: fran18) at 1.13 mm during Cycle 3" (ALMA Archival Data) [from (cite: fran18)]
- External data: ZFOURGE K_S catalog and redshifts  
  > "The spectroscopic or photometric redshifts are available in the ZFOURGE catalog." (IR Luminosity Function of ASAGAO Sources) [from (cite: stra16)]
- External data: Counterpart identification and magphys SED fitting (IR luminosities)  
  > "The counterpart identification and SED fitting are described in detail in (cite: yama18), and here we just give a brief explanation." (IR Luminosity Function of ASAGAO Sources) [from (cite: yama18)]
- External data: Planck EBL measurements at 217 and 353 GHz  
  > "By interpolating the measurements at 217 and 353 GHz, the EBL at 1.2 mm is calculated to be $15.1 \pm 0.59$ Jy deg$^{-2}$." (Contribution to Extragalactic Background Light) [from (cite: plan14)]
- External data: 870 um follow-up number counts of single-dish sources for bright end of Schechter count fit, plus previous ALMA counts  
  > "the results of 870-$\mu$m follow-up observations of single dish sources (cite: kari13; stac18) for the bright end by scaling the flux densities from 870-$\mu$m to 1.2 mm." (1.2mm Number Counts) [from (cite: kari13; stac18)]
- External data: IR luminosity function data points fitted jointly with ASAGAO LF at 1.5<z<2.5  
  > "We fit the IR LFs at $1.5 < z < 2.5$ obtained from the ASAGAO sources and the results of (cite: kopr17) with a Schechter function" (Comparison with Previous Studies) [from (cite: kopr17)]
- External data: AzTEC 1.1 mm flux densities of GS18 and GS21  
  > "which is consistent with the flux density of the AzTEC source, $S_{\rm 1.1mm} = 3.2 \pm 0.6$ mJy (cite: down12)" (Comparison with AzTEC Sources) [from (cite: down12)]
- External data: Total UV+IR SFRD at z~2 for comparison  
  > "0.13 $M_{\odot}$ yr$^{-1}$ Mpc$^{-3}$ at $z = 2$ by (cite: mada14), or 0.11–0.12 $M_{\odot}$ yr$^{-1}$ Mpc$^{-3}$ at $z =$ 1.8–2.25 by (cite: burg13)." (Contribution to the Cosmic SFR Density) [from (cite: mada14); (cite: burg13)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0334-4008 and J2357-5311 (bandpass: J0522-3627, J0238+1636, J0334-4008; phase: J0348-2749)  
  > "J0334$-$4008 and J2357$-$5311 were observed as flux calibrators." (Observations); "The bandpass was calibrated with quasars J0522$-$3627, J0238+1636, and J0334$-$4008, and the phase was calibrated with J0348$-$2749." (Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA  
  > "The combined map was produced with CASA with the same parameters adopted in Sec" (Combined Map)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: 250 klambda (main); also untapered and 160 klambda maps  
  > "We adopt an $uv$-taper of 250 k$\lambda$ to weight extended components" (Combined Map)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Detection on non-PB-corrected signal map; fluxes reported PB-corrected  
  > "Source detection is conducted on the signal map before correcting for the primary beam attenuation." (Source Detection)
- array combination: ASAGAO + HUDF + GOODS-ALMA uv data combined after J2000->ICRS relabelling and identical averaging (32 channels, 10.08 s)  
  > "The $uv$ data sets are averaged in frequency and time directions (32 channels and 10.08 sec) in the same manner as the original ASAGAO data." (Combined Map)
- smoothing: _not stated_
- final beam: 0.59" x 0.53" (combined, 250 klambda taper)  
  > "which gives a final synthesized beam size of $0.59\ensuremath{''} \times 0.53\ensuremath{''}$." (Combined Map)
- final rms: deepest ~26 uJy/beam; Gaussian fit to pixel histogram 34 uJy/beam  
  > "The dashed curve represents the result of a Gaussian fit, which gives $1\sigma$ of 34 $\mu$Jy beam$^{-1}$." (Combined Map)

### Inherited from earlier work

- Combined map imaging parameters taken from the ASAGAO-only reduction section (not reproduced in given text)  
  > "The combined map was produced with CASA with the same parameters adopted in Sec" (Combined Map) [from Sec. subsec:reduction (this paper)]
- Background/noise estimation with BANE as in the reduction section  
  > "The background and noise estimation are done with the BANE package in the same manner as described in Sec." (Source Detection) [from Sec. subsec:reduction (this paper)]
- EBL at 1.2 mm estimated from Planck  
  > "The EBL at 1.2 mm (243 GHz) is estimated from the measurements by the *Planck* satellite (cite: plan14) following (cite: arav16) and (cite: muno17)." (Contribution to Extragalactic Background Light) [from (cite: arav16) and (cite: muno17)]
- Vmax with non-uniform noise effective solid angle  
  > "Following the description of (cite: nova17), where they construct radio LFs taking into account a nonuniform noise in their radio maps, we calculate $V_{\rm max}$" (IR Luminosity Function of ASAGAO Sources) [from (cite: nova17)]
- Counterpart identification and SED fitting  
  > "The counterpart identification and SED fitting are described in detail in (cite: yama18)" (IR Luminosity Function of ASAGAO Sources) [from (cite: yama18)]
- J2000 to ICRS relabelling of Cycle 1/2 data  
  > "we relabel the coordinates of Cycle 1 and 2 data from J2000.0 to the International Celestial Reference System (ICRS) by using a CASA script offered by the ALMA project" (Combined Map) [from CASA script offered by the ALMA project]
- Poisson confidence limits of 84.13%  
  > "The uncertainties from Poisson fluctuations is estimated from Poisson confidence limits of 84.13% (cite: gehr86)" (1.2mm Number Counts) [from (cite: gehr86)]

### Not stated but needed to reproduce (our reading)

- CASA version and whether pipeline or manual calibration was used
- tclean deconvolver, weighting/robust value, cell size, image size, clean threshold and masking (referenced section not in text)
- Relative weighting of the three projects' visibilities in the combination
- Field centre coordinates (blank in text) and the exact map region/mask used
- BANE and Aegean parameter settings
- Functional forms and best-fit parameters of the negative fraction, completeness and flux-boosting fits
- Effective area vs flux density curve
- magphys SED fit details and resulting L_IR per source (deferred to yama18)
- Bin edges/scaling used to convert 870 um counts to 1.2 mm beyond beta/T/z assumptions

## Analysis recipe

1. **average and combine uv data**: Average in frequency and time; relabel Cycle 1/2 coordinates to ICRS; combine ASAGAO, HUDF and GOODS-ALMA visibilities  
  > "we average the data in frequency and time directions with 32 channels ($\Delta \nu = 0.5$ GHz) and 10.08 sec, respectively." (Data Reduction)
   - software: CASA
   - parameter: 32 channels (0.5 GHz), 10.08 s  
  > "The $uv$ data sets are averaged in frequency and time directions (32 channels and 10.08 sec) in the same manner as the original ASAGAO data." (Combined Map)
   - fitting: _not stated_
   - validation: Bandwidth smearing <1%; time averaging effect checked on bandpass calibrator  
  > "We also confirm that the effect of the time averaging on the flux density is negligible based on the imaging of the bandpass calibrator." (Data Reduction)
2. **image continuum with tapers**: CASA imaging with 250 klambda taper, plus untapered and 160 klambda maps to test source extent  
  > "were also created to see whether detected sources are spatially resolved." (Combined Map)
   - software: CASA
   - parameter: uv-taper 250 klambda  
  > "We adopt an $uv$-taper of 250 k$\lambda$ to weight extended components" (Combined Map)
   - fitting: _not stated_
   - validation: Gaussian fit to pixel histogram  
  > "The dashed curve represents the result of a Gaussian fit, which gives $1\sigma$ of 34 $\mu$Jy beam$^{-1}$." (Combined Map)
3. **detect sources and measure fluxes**: Aegean with BANE background/noise; 2D elliptical Gaussian fits; S_int = S_peak ab/(theta_maj theta_min), S_peak adopted if S_int<S_peak  
  > "We adopt the source-finding algorithm called Aegean (cite: hanc12; hanc18), which achieves high reliability and completeness performance for radio maps." (Source Detection); "When $S_{\rm int} < S_{\rm peak}$, we adopt $S_{\rm peak}$, since it is possible that the source fitting failed due to the low SN." (Source Detection)
   - software: Aegean, BANE
   - parameter: peak SN >= 5 and >= 4.5 thresholds  
  > "We find 25 (45) sources with a peak SN of $\ge$5$\sigma$ ($\ge$4.5$\sigma$)." (Source Detection)
   - fitting: 2D elliptical Gaussian  
  > "The detected sources are fitted with a 2D elliptical Gaussian to estimate the source size and integrated flux density." (Source Detection)
   - validation: Negative peak counts; 88% of 5sigma sources have multiwavelength counterparts  
  > "The actual number of negative peaks in the combined map is 1 at $\ge$5$\sigma$ and 8 at 4.5–5$\sigma$." (Source Detection); "Actually, 22 out of the 25 5$\sigma$ sources (88%) have counterparts at optical, *Spitzer*/IRAC, radio, or ALMA 850 $\mu$m (cite: cowi18)" (Source Detection)
4. **check astrometry and cross-match with other surveys**: Cross-match 5sigma sources with VLA 5 cm sources within 0.5"; compare fluxes with HUDF, GOODS-ALMA, ASPECS and AzTEC sources  
  > "The radio counterparts are found for 20 out of the 25 ASAGAO 5$\sigma$ sources within a 0.5$''$ search radius" (Astrometry)
   - parameter: 0.5" search radius  
  > "within a 0.5$''$ search radius" (Astrometry)
   - assumption: Modified blackbody beta=1.5, T=35 K, z=2 for flux scaling between wavelengths  
  > "assuming a modified black body with a dust emissivity index of $\beta = 1.5$, a dust temperature of 35 K, and $z = 2$" (Comparison with ALMA 1-mm Sources in GOODS-S)
   - fitting: _not stated_
   - validation: Offsets within expected ~0.1" uncertainty  
  > "which is within the expected positional uncertainty between the ALMA and the radio sources of $\sim$0.1$''$" (Astrometry)
5. **estimate completeness and flux boosting**: Inject 30000 artificial Gaussian sources one at a time into the PB-corrected signal map, convolved with 0.01-0.5" Gaussians, fluxes 0.05-2 mJy; recover with same extraction at SN>=4.5; separately for coverage >0.6 and <0.6  
  > "We input 30000 artificial sources into the signal map one at a time, each with an integrated flux density randomly selected from 0.05–2 mJy by considering the flux range of detected sources." (Completeness and Flux Boosting); "In the completeness calculation, we take a convolving beam size to be uniformly distributed from 0.01$''$–0.5$''$." (Completeness and Flux Boosting)
   - software: Aegean
   - parameter: recovery threshold peak SN >= 4.5  
  > "When the input source is detected with a peak SN $\ge 4.5$, the source is considered to be recovered." (Completeness and Flux Boosting)
   - assumption: Faint sources have smaller sizes (supported by uv stacking of fuji18)  
  > "This is proved to be valid for the ASAGAO sources based on $uv$-visibility stacking analysis (cite: fuji18)." (Completeness and Flux Boosting)
   - fitting: _not stated_
   - validation: No significant difference between coverage regions  
  > "The completeness calculated in regions with different coverage are consistent within errors and we do not find a significant difference." (Completeness and Flux Boosting)
6. **construct number counts and fit Schechter function**: dN/dS = (1/dS) sum (1-f_neg)/(A C) with deboosted fluxes and SNs; Poisson 84.13% limits; Schechter fit to ASAGAO plus literature counts  
  > "To create number counts, we correct for the contamination of spurious sources, the effective area, and the completeness as follows:" (1.2mm Number Counts); "The differential number counts obtained in this study and previous studies are fitted to a Schechter function of the form," (1.2mm Number Counts)
   - parameter: 45 4.5sigma sources  
  > "Number counts are constructed by using the 45 4.5$\sigma$ sources." (Number Counts)
   - assumption: 870 um to 1.2 mm scaling with beta=1.5, T=35 K, z=2  
  > "Here we assume a modified black body with a dust emissivity index of $\beta = 1.5$, dust temperature of 35 K, and $z = 2$." (1.2mm Number Counts)
   - fitting: Schechter function fit (method not stated)  
  > "The differential number counts obtained in this study and previous studies are fitted to a Schechter function of the form," (1.2mm Number Counts)
   - validation: Compared to previous ALMA blank-field and serendipitous counts  
  > "We find that our number counts are consistent with those of the previous ALMA blank-field surveys." (Comparison with Previous ALMA Studies)
7. **resolved EBL fraction**: Integrate differential counts above 135 uJy and divide by Planck-interpolated EBL  
  > "By using the derived differential number counts, we calculate the fraction of the EBL resolved into discrete sources in this survey." (Contribution to Extragalactic Background Light)
   - fitting: _not stated_
   - validation: _not stated_
8. **identify counterparts and derive IR luminosities**: Cross-match with ZFOURGE (0.5" for point-like, up to half-light radius for extended); magphys SED fitting with 0.4-500 um data and ALMA photometry  
  > "By using ancillary multi-wavelength data (0.4–500 $\mu$m) and our ALMA photometry, SED fitting with the magphys model (cite: dacu08; dacu15) is performed." (IR Luminosity Function of ASAGAO Sources)
   - software: magphys
   - parameter: IR luminosity over rest-frame 8-1000 um  
  > "IR luminosities (measured in the rest-frame 8–1000 $\mu$m) are derived in the SED fitting." (IR Luminosity Function of ASAGAO Sources)
   - assumption: Bruzual & Charlot 2003 templates, Charlot & Fall 2000 dust model  
  > "The SED templates of (cite: bruz03) and the dust extinction model of (cite: char00) are adopted." (IR Luminosity Function of ASAGAO Sources)
   - fitting: magphys SED fitting  
  > "By using ancillary multi-wavelength data (0.4–500 $\mu$m) and our ALMA photometry, SED fitting with the magphys model (cite: dacu08; dacu15) is performed." (IR Luminosity Function of ASAGAO Sources)
   - validation: _not stated_
9. **build IR luminosity functions**: Vmax method with completeness and effective solid angle for SN>5; overlapping redshift bins of width 1.0; Delta log L = 0.6  
  > "To construct the LFs, we adopt the $V_{\rm max}$ method (cite: schm68)." (IR Luminosity Function of ASAGAO Sources); "We adopt a luminosity bin width of $\Delta\log{(L)} = 0.6$." (IR Luminosity Function of ASAGAO Sources)
   - parameter: 6, 9, 13 sources in 1.0-2.0, 1.5-2.5, 2.0-3.0  
  > "by using 6 (mean redshift of $z_{\rm mean} = 1.55$), 9 ($z_{\rm mean} = 2.12$), and 13 ($z_{\rm mean} = 2.49$) sources, respectively." (IR Luminosity Function of ASAGAO Sources)
   - assumption: H0=70, Om=0.3, OL=0.7, Chabrier IMF  
  > "Throughout the paper, we adopt a cosmology with $H_0=70$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_{\rm{M}}=0.3$, and $\Omega_{\Lambda}=0.7$, and a (cite: chab03) IMF." (Introduction)
   - fitting: _not stated_
   - validation: Compared with Koprowski et al. 2017 and Herschel LFs  
  > "We find that the ASAGAO LFs are consistent with those of (cite: kopr17) within the errors" (Comparison with Previous Studies)
10. **fit LF and derive SFRD contribution**: Schechter fit to ASAGAO + Koprowski LF at 1.5<z<2.5; integrate down to log L=11.78; convert with Kennicutt 1998 corrected to Chabrier IMF  
  > "SFR is converted from IR luminosity by using the relation of (cite: kenn98) and corrected to a (cite: chab03) IMF." (Contribution to the Cosmic SFR Density)
   - parameter: integration limit log(L_IR/Lsun)=11.78  
  > "The integration of the best-fitting luminosity function down to the lowest luminosity of the sources ($\log{(L_{\rm IR}/L_{\odot})} = 11.78$)" (Contribution to the Cosmic SFR Density)
   - fitting: Schechter function fit (method not stated)  
  > "We fit the IR LFs at $1.5 < z < 2.5$ obtained from the ASAGAO sources and the results of (cite: kopr17) with a Schechter function of the form of equation" (Comparison with Previous Studies)
   - validation: Consistent with yama18 SFRD from individual sources  
  > "This is consistent with the results of (cite: yama18), where they derived the SFRD by counting the contribution from individual ASAGAO sources." (Contribution to the Cosmic SFR Density)

## Software

- **CASA** : imaging the combined map and J2000->ICRS relabelling script  
  > "The combined map was produced with CASA with the same parameters adopted in Sec" (Combined Map)
- **Aegean** : source finding  
  > "We adopt the source-finding algorithm called Aegean (cite: hanc12; hanc18)" (Source Detection)
- **BANE** : background and noise estimation  
  > "The background and noise estimation are done with the BANE package" (Source Detection)
- **magphys** : SED fitting for IR luminosities  
  > "SED fitting with the magphys model (cite: dacu08; dacu15) is performed." (IR Luminosity Function of ASAGAO Sources)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| number of sources >=5 sigma | 25 | not stated | sources | 3 | We find 25 (45) sources with a peak SN of $\ge$5$\sigma$ ($\ge$4.5$\sigma$). |
| number of sources >=4.5 sigma | 45 | not stated | sources | 3 | We find 25 (45) sources with a peak SN of $\ge$5$\sigma$ ($\ge$4.5$\sigma$). |
| negative peaks at >=5 sigma / 4.5-5 sigma | 1 / 8 | not stated | peaks | 3 | The actual number of negative peaks in the combined map is 1 at $\ge$5$\sigma$ and 8 at 4.5–5$\sigma$. |
| median S_int/S_peak | 1.3 | 0.8 | dimensionless | 3 | The median ratio between integrated flux and peak flux is $S_{\rm int}/S_{\rm peak} = 1.3 \pm 0.8$. |
| median S_int(250k)/S_int(160k) | 0.86 | 0.24 | dimensionless | 3 | $S_{\rm int}^{\rm 250k\lambda}/S_{\rm int}^{\rm 160k\lambda} = 0.86 \pm 0.24$ |
| median ALMA-VLA offset (dRA, dDec) | (+0.03, -0.01) | (0.08, 0.06) | arcsec | 4 | The median offset is ($\Delta \alpha$, $\Delta \delta$) $= (+0.03\ensuremath{''} \pm 0.08\ensuremath{''}, -0.01\ensuremath{''} \pm 0.06\ensuremath{''})$ |
| median flux ratio ASAGAO/HUDF | 1.15 | 0.64 | dimensionless | 4 | $S_{\rm 243GHz}^{\rm ASAGAO}/S_{\rm 221GHz}^{\rm HUDF} = 1.15 \pm 0.64$ |
| median flux ratio ASAGAO/GOODS-ALMA | 0.89 | 0.13 | dimensionless | 4 | $S_{\rm 243GHz}^{\rm ASAGAO}/S_{\rm 265GHz}^{\rm GOODS-ALMA} = 0.89 \pm 0.13$ |
| total flux of ASAGAO counterparts of AzTEC/GS18 | 2.16 | 0.06 | mJy | 4 | the total flux of the three sources is $S_{\rm 1.2mm} = 2.16 \pm 0.06$ mJy |
| total flux of ASAGAO counterparts of AzTEC/GS21 | 1.97 | 0.19 | mJy | 4 | The total flux of the two ALMA sources is $S_{\rm 1.2mm} = 1.97 \pm 0.19$ mJy |
| completeness at SN=4.5 | 60 | not stated | % | 5 | The completeness is 60% at SN $= 4.5$, and 100% at SN $\gtrsim 7$. |
| mean flux boosting for SN>=4.5 | <15 | not stated | % | 5 | The effect of flux boosting for the sources with SN $\ge 4.5$ is on average less than 15%, and the deboosted flux densities range from 135 $\mu$Jy to 1.97 mJy. |
| cumulative counts N(>0.135 mJy) | 213 | +64/-43 | 10^2 deg^-2 | 6 | / 0.180 /   6   /      $924^{+552}_{-366}$       / 0.135 /  45   /  $213^{+64}_{-43}$  / |
| integrated differential counts (S>135 uJy) | 7.7 | +1.7/-1.2 | Jy deg^-2 | 7 | The integration of the ASAGAO differential number counts yields $7.7^{+1.7}_{-1.2}$ Jy deg$^{-2}$ ($S_{\rm 1.2mm} > 135$ $\mu$Jy). |
| EBL at 1.2 mm | 15.1 | 0.59 | Jy deg^-2 | 7 | the EBL at 1.2 mm is calculated to be $15.1 \pm 0.59$ Jy deg$^{-2}$. |
| resolved EBL fraction at S>135 uJy | 52 | +11/-8 | % | 7 | We find that $52^{+11}_{-8}$% of the EBL at 1.2 mm is resolved into discrete sources in the ASAGAO map. |
| flux where Schechter count integral reaches 100% EBL | ~20 | not stated | uJy | 7 | The integration of the best-fitting function in the form of Schechter function reaches 100% at $S_{\rm 1.2mm} \sim 20$ $\mu$Jy |
| LF faint-end slope alpha at 1.5<z<2.5 | -0.22 | 0.28 | dimensionless | 10 | The derived spectral slope of $\alpha = -0.22 \pm 0.28$ is flatter than $\alpha = -0.4$ derived by (cite: kopr17), but consistent within the errors. |
| SFRD from LF integration (log L_IR>11.78) | 7.2e-2 | +3.0/-1.9 e-2 | Msun yr^-1 Mpc^-3 | 10 | gives a SFRD of $7.2^{+3.0}_{-1.9} \times 10^{-2}$ $M_{\odot}$ yr$^{-1}$ Mpc$^{-3}$. |
| fraction of z~2 SFRD from ASAGAO sources | 60-90 | not stated | % | 10 | The fraction of SFRD contributed by the ASAGAO sources is $\approx$60–90% at $z \sim 2$ |

## Qualitative findings

- Sources appear resolved by the beam in the 250 klambda-tapered and untapered maps  
  > "These suggest that sources are resolved by the synthesized beam in the 250 k$\lambda$-tapered and the untapered maps." (Source Detection)
- Single-dish AzTEC sources break up into multiple ALMA sources  
  > "AzTEC/GS18 is detected as three ASAGAO sources (ID1, 4, and 14)" (Comparison with AzTEC Sources)
- 5sigma sources without K_S counterparts likely at z>~4-5  
  > "Note that the 5$\sigma$ sources without counterparts are likely to be at higher redshifts ($z \gtrsim$4–5)" (IR Luminosity Function of ASAGAO Sources)

## Claim tuples

- H: A deep contiguous 1.2 mm ALMA mosaic combined with archival data yields a large unbiased faint-source sample | E: Combined ASAGAO, HUDF, GOODS-ALMA uv data, imaged at 250 klambda taper, Aegean extraction | R: 25 sources >=5sigma, 45 >=4.5sigma; only 1 negative peak >=5sigma | F: Largest source catalog among ALMA blank-field surveys | **supported**
- H: ASAGAO 1.2 mm number counts agree with previous ALMA determinations | E: Corrected differential/cumulative counts compared with SXDF, ASPECS, HUDF, GOODS-ALMA and serendipitous counts | R: Counts consistent within errors with smaller Poisson uncertainties | F: Counts connect faint ALMA-deep and bright single-dish follow-up regimes | **supported**
- H: Faint ALMA sources resolve a large fraction of the 1.2 mm EBL | E: Integration of differential counts vs Planck-based EBL | R: 52 +11/-8 % at S>135 uJy; Schechter extrapolation reaches 100% at ~20 uJy | F: About half the EBL is resolved; deeper surveys needed for the rest | **supported**
- H: IR LFs from ASAGAO support positive luminosity and negative density evolution | E: Vmax LFs in three z bins from 5sigma sources with ZFOURGE counterparts, compared with Koprowski et al. 2017 | R: Consistent within errors; small samples limit further constraints | F: Supports Koprowski evolution, but cannot discuss density/luminosity evolution further | **partially**
- H: Obscured star formation in log L_IR>~11.8 sources dominates z~2 SFRD | E: Integrate best-fit Schechter LF to log L=11.78, convert to SFRD, compare with total UV+IR SFRD | R: SFRD 7.2 +3.0/-1.9 x10^-2; 60-90% of total | F: Major portion of z~2 SFRD is obscured star formation from such sources | **supported**

## Reasoning

- Why this data: Contiguous unbiased field avoids biases of serendipitous-source counts; area matches deepest VLA and HAWK-I data  
  > "These studies are based on serendipitous sources detected in fields where faint submm sources are not the main targets, which could introduce biases due to the clustering of sources around the targets or sidelobes caused by bright targets." (Introduction); "The observing area matches the deepest VLA C-band 5 cm (6 GHz) observations ((cite: rujo16); Rujopakarn et al. in prep.) and the ultra-deep VLT/HAWK-I $K_S$-band images." (Introduction)
- Why this method: VLA radio used for astrometry since resolution comparable and traces obscured parts; 5sigma sources used for LFs due to counterpart completeness  
  > "The radio sources are more suitable for evaluating the astrometry of the ALMA sources compared to optical sources because (i) the angular resolution and positional accuracy are comparable to those of the ALMA observations" (Astrometry); "We use the 5$\sigma$ sources for constructing IR LFs by considering the completeness of the counterpart identification." (IR Luminosity Function of ASAGAO Sources)
- Alternative: ASPECS data not combined because of very different beam  
  > "We do not use the data set of ASPECS, where the synthesized beam size ($1.68\ensuremath{''} \times 0.92\ensuremath{''}$) is largely different from those of the others ($\lesssim 0.5''$)." (ALMA Archival Data)
- Alternative: Gaussian-statistics estimate of spurious sources rejected in favour of negative peak counts  
  > "However, it is reported that this estimation underestimates the negative peaks in previous studies based on ALMA images (cite: dunl17; vio16; vio17)." (Source Detection)
- How they decided it was enough: Low number of negative peaks at >=5sigma taken as evidence of robustness  
  > "The small number of negative peaks at $\ge$5$\sigma$ suggests the robustness of the 5$\sigma$ sources." (Source Detection)
- Limitation (authors): Large uncertainty extrapolating count Schechter fit to faint fluxes  
  > "although we note that there is a large uncertainty to extend the function to the faint flux regime." (Contribution to Extragalactic Background Light)
- Limitation (authors): Small LF sample size and limited IR luminosity coverage  
  > "In order to constrain the redshift evolution of LFs, it is essential to conduct wider-area surveys for obtaining a larger sample in a wide range of IR luminosity." (Comparison with Previous Studies)
- Limitation (authors): Some sources undetected in untapered map due to lack of sensitivity to extended structure  
  > "This can be due to the lack of sensitivity for spatially extended structures or clumpy structures and multiple peaks" (Source Detection)
- Caveat (inferred, ours): Completeness simulations assume sizes 0.01-0.5"; results could depend on true faint-source size distribution
- Caveat (inferred, ours): Single modified blackbody (beta=1.5, T=35 K, z=2) used for all wavelength scalings
- Caveat (inferred, ours): LFs rely on only 6-13 sources per overlapping (non-independent) redshift bin
- Caveat (inferred, ours): Combined map has non-uniform depth and mixed frequencies (1.13-1.3 mm), so flux definition at 243 GHz depends on source SEDs
- Caveat (inferred, ours): SFRD integration limit set at the faintest detected luminosity, so the 60-90% fraction depends on that cut

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Raw ALMA data from three listed projects used; no statement on released products  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00098.S, #2012.1.00173.S, and #2015.1.00543.S." (Conclusions)
- Missing: Imaging parameters (weighting, cell, clean depth, mask) from the referenced reduction section
- Missing: CASA version and calibration approach
- Missing: Field centre coordinates
- Missing: Data weights in combination
- Missing: Aegean/BANE settings
- Missing: Fitted functions for f_neg, completeness, boosting and effective area
- Missing: Per-source L_IR and SED fits (in yama18)
- Data volume (inferred): ~37 ASAGAO execution blocks plus HUDF and GOODS-ALMA archival mosaics; likely several hundred GB to ~1 TB raw
- Score (inferred): 6/5, Observational setup, combination and statistical corrections are well described, but core imaging parameters are deferred to a section not in the text and SED/counterpart work is deferred to a companion paper.
- Rediscovery candidate: no, Results are numeric and data are archival ALMA projects, but imaging parameters and correction functions are not given, so the recipe is not complete enough to redo exactly.

## Links

- Method: (cite: hanc12; hanc18) (Aegean source finder)
- Method: (cite: schm68) (Vmax method)
- Method: (cite: nova17) (Vmax with nonuniform noise)
- Method: (cite: gehr86) (Poisson confidence limits)
- Method: (cite: dacu08; dacu15) (magphys SED fitting)
- Method: (cite: kenn98) (L_IR to SFR conversion)
- Method: (cite: ivis07) (positional uncertainty formula)
- Companion: (cite: yama18) (multi-wavelength identifications, SED fitting and SFRD of ASAGAO sources)
- Companion: (cite: ueda18) (X-ray AGN properties of ASAGAO sources)
- Companion: (cite: fuji18) (morphology / uv stacking source sizes)
- Companion: Yoshimura et al. (in prep.) (clustering analysis)
- Related: HUDF ALMA survey (Dunlop et al. 2017)
- Related: GOODS-ALMA
- Related: ASPECS
- Related: SXDF-ALMA
- Related: ZFOURGE
- Related: VLA 5 cm GOODS-S survey
- Related: AzTEC/ASTE GOODS-S
- Related: S2CLS
- Related: Herschel PEP/HerMES

## Checks

```json
{
 "quotes": 137,
 "quotes_ok": 137,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 20,
 "numeric_problems": 0,
 "fill": {
  "facts": 119,
  "stated": 91,
  "rate": 0.765
 },
 "evidence_ok": true
}
```

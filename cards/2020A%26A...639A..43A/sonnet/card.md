# Cold molecular gas and PAH emission in the nuclear and circumnuclear regions of Seyfert galaxies

`2020A&A...639A..43A` | Astronomy and Astrophysics 2020 | first author: Alonso-Herrero, A. | arXiv: 2005.11959 | DOI: 10.1051/0004-6361/202037642

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies, agn_and_quasars, astrochemistry
- Question: Does cold molecular gas (CO(2-1) mass and column density) in Seyfert nuclei relate to nuclear detection of the 11.3 micron PAH feature, and how does it affect PAH survival against X-rays?  
  > "The main goal of this paper is to investigate the role of cold molecular gas in shielding PAH molecules from the AGN radiation field." (Introduction)
- Target **22 nearby Seyfert galaxies (e.g. NGC 1068, NGC 1365, NGC 7469, NGC 7582)**: coordinates 1.3 mm peak coordinates given per galaxy in appendix table  
  > "Luminosity distances and angular scales are taken from the NASA/IPAC Extragalactic Database (NED) for $H_0=73\,{\rm km\,s}^{-1}\,{\rm Mpc}^{-1}$" (Table 1 notes); z/distance 14.0-67.9 Mpc  
  > "Luminosity distances and angular scales are taken from the NASA/IPAC Extragalactic Database (NED) for $H_0=73\,{\rm km\,s}^{-1}\,{\rm Mpc}^{-1}$" (Table 1 notes); distance from NED luminosity distances, H0=73  
  > "Luminosity distances and angular scales are taken from the NASA/IPAC Extragalactic Database (NED) for $H_0=73\,{\rm km\,s}^{-1}\,{\rm Mpc}^{-1}$" (Table 1 notes)

## Data provenance

- ALMA projects: 2017.1.00255.S, 2013.1.01161.S, 2012.1.00474.S, 2017.1.00984.S, 2015.1.00086.S, 2016.1.00254.S, 2013.1.00243.S, 2015.1.00116.S, 2017.1.00395.S
- bands: Band 6 (1.3 mm), CO(2-1) and continuum  
  > "We downloaded the band 6 CO(2-1) and adjacent continuum raw data from the ALMA archive." (2.1 CO(2-1) and continuum 1.3mm observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.2-1.1 arcsec CO(2-1) beams (ALMA and NOEMA)  
  > "we use high ($\simeq 0.2-1.1\ensuremath{''}$) angular resolution observations of the CO(2-1) transition" (Introduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (not stated)
- Other facility **NOEMA**: CO(2-1) for Mrk 1066, NGC 2273, NGC 4253, NGC 4388, NGC 7465  
  > "The NOEMA observations and data reduction for the galaxies in our sample (see Table [\[tab:CO21obs\]](#tab:CO21obs)) are described in detail in (cite: DominguezFernandez2020)." (2.1 CO(2-1) and continuum 1.3mm observations)
- Other facility **Spitzer/IRS**: Archival 5-40 micron spectra for circumnuclear PAH ratios  
  > "To study the PAH emission on circumnuclear scales we use archival *Spitzer* observations taken with IRS" (2.3 Spitzer/IRS observations)
- Other facility **Ground-based mid-IR spectrographs (T-ReCS, CanariCam, Michelle, VISIR)**: Published nuclear 11.3 micron PAH detections  
  > "All the ground-based mid-IR spectroscopic observations used in this work have been published previously" (2.2 Ground-based mid-IR spectroscopy)
- External data: NGC 1068 nuclear CO(2-1) flux  
  > "The nuclear flux is from (cite: GarciaBurillo2019) measured through an elliptical aperture" (Table 5 notes) [from (cite: GarciaBurillo2019)]
- External data: NGC 1320 and NGC 2992 nuclear CO(2-1) fluxes (0.5x0.5 arcsec)  
  > "The nuclear CO(2-1) fluxes for NGC 1320 and NGC 2992 within $0.5\ensuremath{''} \times 0.5\ensuremath{''}$ apertures were provided by J. A. Fernández Ontiveros (private communication)." (3.2 CO(2-1) aperture photometry) [from private communication, J. A. Fernández Ontiveros]
- External data: 2-10 keV intrinsic luminosities  
  > "The hard X-ray luminosities are intrinsic (i.e., corrected for absorption), and the last column indicates the reference." (Table 1 notes) [from references in Table 1]
- External data: Naphthalene photodissociation cross-section at 2.5 keV  
  > "This PAH molecule among those studied by (cite: Monfredini2019) has the smallest photodissociation cross-section when exposed to hard X-ray photons at $E=2.5\,$keV." (4.3 Half-life) [from (cite: Monfredini2019)]
- External data: Nuclear 11.3 micron PAH detections and slit widths  
  > "The last column provides the reference of the published mid-IR spectrum for each galaxy." (Table 2 notes) [from Table 2 references]

## Processing

### Calibration

- pipeline or manual: Standard pipeline calibration  
  > "The raw data were then calibrated using the standard pipeline calibration within the Common Astronomy Software Applications (CASA) v5.1" (2.1 CO(2-1) and continuum 1.3mm observations)
- casa version: CASA v5.1  
  > "The raw data were then calibrated using the standard pipeline calibration within the Common Astronomy Software Applications (CASA) v5.1" (2.1 CO(2-1) and continuum 1.3mm observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10-15% in band 6  
  > "which in band 6 is typically $10-15\%$." (3.2 CO(2-1) aperture photometry)
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "used the CASA clean task to generate the CO(2-1) data cubes." (2.1 CO(2-1) and continuum 1.3mm observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robustness b = 0.5  
  > "We used a Briggs weighting (cite: Briggs1995), with a robustness parameter of $b = 0.5$." (2.1 CO(2-1) and continuum 1.3mm observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: moment 0 from pixels >4 sigma (2 sigma for NGC 1365, NGC 3081, NGC 7213; NOEMA >3 sigma)  
  > "we produced maps of the integrated CO(2-1) intensity as the zeroth-order moment using pixels at all frequencies with detections $>4\sigma$." (2.1 CO(2-1) and continuum 1.3mm observations)
- multiscale scales: _not stated_
- continuum subtraction: uv-plane subtraction using line-free channels  
  > "we subtracted the continuum using the line-free channels in the uv visibility data" (2.1 CO(2-1) and continuum 1.3mm observations)
- line free channels: _not stated_
- primary beam correction: applied to continuum images  
  > "We applied a primary beam correction, although the effect on the regions covered by the nuclear slits is negligible." (2.1 CO(2-1) and continuum 1.3mm observations)
- array combination: _not stated_
- smoothing: NGC 7582 smoothed to ~0.4-0.5 arcsec  
  > "We thus smoothed the ALMA CO(2-1) image to an approximately angular resolution of 0.4-0.5$\ensuremath{''}$ to match that of the mid-IR observations." (3.2 CO(2-1) aperture photometry)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- NOEMA observations and data reduction  
  > "The NOEMA observations and data reduction for the galaxies in our sample (see Table [\[tab:CO21obs\]](#tab:CO21obs)) are described in detail in (cite: DominguezFernandez2020)." (2.1 CO(2-1) and continuum 1.3mm observations) [from (cite: DominguezFernandez2020)]
- Mass formula for H2 from CO(1-0) flux  
  > "To derive the molecular gas masses, we used the following expression derived by (cite: Sakamoto1999):" (3.3 Nuclear molecular gas masses) [from (cite: Sakamoto1999)]
- X-ray photon flux and half-life formalism  
  > "Following (cite: Monfredini2019), at a given distance from the AGN ($r_{\rm AGN}$), the X-ray photon flux on a PAH molecule for a given photon energy is" (4.2 Dependence on AGN luminosity) [from (cite: Monfredini2019)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and spectral windows used for continuum subtraction
- CLEAN threshold, niter, masks, and image sizes per galaxy
- Velocity range/channel width of the moment-0 maps
- X-ray photoabsorption cross-section sigma_H(E) source and value
- Naphthalene photodissociation cross-section numeric value
- PAH model track details (Rigopoulou et al. in prep.)
- Choice of aperture position angles and exact aperture placement
- pahfit modifications and fit settings

## Analysis recipe

1. **Image CO(2-1) and 1.3 mm continuum**: Pipeline calibration in CASA, uv continuum subtraction, clean with Briggs weighting, moment 0 maps  
  > "Then, we subtracted the continuum using the line-free channels in the uv visibility data and used the CASA clean task to generate the CO(2-1) data cubes." (2.1 CO(2-1) and continuum 1.3mm observations)
   - software: CASA
   - parameter: robust = 0.5  
  > "with a robustness parameter of $b = 0.5$." (2.1 CO(2-1) and continuum 1.3mm observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Locate AGN position**: Centroid of the 1.3 mm continuum peak converted to ICRS  
  > "we obtained the centroid of the source at $1.3\,$mm in the plane of the sky and converted the pixel position into the International Coordinate Reference System (ICRS)" (3.1 Identification of the AGN position)
   - software: astropy
   - assumption: 1.3 mm peak traces the AGN  
  > "We therefore assumed that the peak of the 1.3 mm can be used to locate the position of the AGN" (3.1 Identification of the AGN position)
   - fitting: _not stated_
   - validation: Compared with radio peaks from the literature  
  > "the peak coordinates agree well with the radio peaks listed in the literature" (Appendix)
3. **Aperture photometry of CO(2-1) matching mid-IR slits**: Rectangular apertures with slit width on one side, rotated to slit PA, on integrated intensity maps  
  > "We defined rectangular apertures to simulate the nuclear extraction aperture of the mid-IR spectra." (3.2 CO(2-1) aperture photometry)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive nuclear H2 mass, surface density and column density**: M_H2 = 1.18e4 D_L^2 S_CO(1-0) X_CO  
  > "M_{H_{2}}(M_{\odot}) = 1.18 \times 10^{4} \times D^{2}_{\rm L} \times S_{\rm CO(1-0)} \times X_{\rm CO}" (3.3 Nuclear molecular gas masses)
   - parameter: r21 = 1  
  > "We took an $r_{21}=$CO(2–1)/CO(1–0) brightness temperature ratio of one" (3.3 Nuclear molecular gas masses)
   - assumption: Galactic X_CO = 2e20 cm-2 (K km/s)-1  
  > "we used the Galactic value of $X_{\rm CO} = 2\times10^{20}\,{\rm cm}^{-2} ({\rm K\,km\,s}^{-1})^{-1}$" (3.3 Nuclear molecular gas masses)
   - fitting: _not stated_
   - validation: Discussed r21 and X_CO uncertainties; masses may be upper limits  
  > "the assumed value of $r_{21}=1$ for the nuclear or circumnuclear regions of Seyfert galaxies might be a lower limit" (3.3 Nuclear molecular gas masses)
5. **Compare PAH-detected vs non-detected nuclei**: Medians and K-S tests of M(H2) and N(H2)  
  > "A Kolmogorov-Smirnov (K-S) test indicates that there is a probability of 2% that the two distributions of cold molecular gas are drawn from the same parent population." (4.1 Dependence on molecular gas)
   - fitting: _not stated_
   - validation: _not stated_
6. **Compute naphthalene half-life**: t1/2 = ln2/(F_X sigma), F_X = L_X/(4 pi r^2 h nu) exp(-tau_X), tau_X from molecular gas only  
  > "t_{\rm 1/2} = \frac{\ln 2}{F_{\rm X}(E).\sigma_{\rm ph-d}(E)}" (4.3 Half-life)
   - parameter: E = 2.5 keV; r_AGN = half slit width  
  > "hard X-ray photons at $E=2.5\,$keV." (4.3 Half-life)
   - assumption: Only molecular gas absorbs; PAHs in the nuclear disk/torus plane  
  > "we only considered the molecular gas contribution to the X-ray absorption" (4.2 Dependence on AGN luminosity)
   - fitting: _not stated_
   - validation: Compared with PAH injection time and ISM lifetime  
  > "For comparison we show the values of the PAH injection time by AGB stars into the ISM from" (4.3 Half-life)
7. **Measure Spitzer/IRS PAH fluxes and ratios**: Full 5-40 micron fit with modified pahfit; ratios 11.3/7.7 and 6.2/7.7  
  > "We used a modified version of the pahfit code (cite: Smith2007) to obtain the fluxes of different PAH features." (2.3 Spitzer/IRS observations)
   - software: pahfit, CUBISM
   - fitting: pahfit with continuum, PAH and 10 micron silicate in emission or absorption  
  > "This version fits the mid-IR spectrum with a continuum, PAH emission, and the $10\,\mu$m silicate feature in emission or absorption." (2.3 Spitzer/IRS observations)
   - validation: Tested effect of silicate emission on NGC 7469 ratios  
  > "We illustrate this in Figure [2](#fig:NGC7469pahfit) for NGC 7469." (2.3 Spitzer/IRS observations)

## Software

- **CASA** 5.1: Calibration and imaging  
  > "calibrated using the standard pipeline calibration within the Common Astronomy Software Applications (CASA) v5.1" (2.1 CO(2-1) and continuum 1.3mm observations)
- **pahfit** modified version: PAH feature fluxes from IRS spectra  
  > "We used a modified version of the pahfit code (cite: Smith2007)" (2.3 Spitzer/IRS observations)
- **CUBISM** : Reduce IRS mapping data and extract spectra  
  > "We used cubism (cite: Smith2007cubism) to fully reduce the observations and extract the circumnuclear spectra." (2.3 Spitzer/IRS observations)
- **astropy** : WCS conversion of continuum peak positions  
  > "using the WCS header information and astropy routines (cite: Astropy2018)" (3.1 Identification of the AGN position)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median nuclear M(H2), PAH detected | 1.6e7 | not stated | Msun | 4 | the median values for galaxies with nuclear detections of the $11.3\,\mu$m PAH feature are higher ($1.6\times 10^7\,M_\odot$) than for those without detections ($2\times 10^6\,M_\odot$) |
| Median nuclear M(H2), no detection | 2e6 | not stated | Msun | 4 | than for those without detections ($2\times 10^6\,M_\odot$) |
| K-S probability, M(H2) same parent | 2 | not stated | % | 5 | there is a probability of 2% that the two distributions of cold molecular gas are drawn from the same parent population |
| Median N(H2), PAH detected | 2e23 | not stated | cm-2 | 4 | have a median of $N({\rm H}_2) = 2 \times 10^{23}\,{\rm cm}^{-2}$ |
| Median N(H2), no detection | 4e22 | not stated | cm-2 | 4 | compared to a median of $N({\rm H}_2) = 4 \times 10^{22}\,{\rm cm}^{-2}$ for those without a detection |
| K-S probability, N(H2) same parent | 0.8 | not stated | % | 5 | there is a probability of 0.8% that the two $N({\rm H}_2)$ distributions are drawn from the same parent population |
| NGC 7469 f(11.3)/f(7.7) with silicate emission | 0.21 | not stated | dimensionless | 7 | whereas we obtained $f(11.3\,\mu$m)/$f(7.7\,\mu$m)= 0.21 and $f(6.2\,\mu$m)/$f(7.7\,\mu$m)=0.16 when it was included. |
| Sample average N(H2) | 2e23 | not stated | cm-2 | 4 | The average value for our sample is $N({\rm H}_2) = 2\times10^{23}\,{\rm cm}^{-2}$. |

## Qualitative findings

- Nuclei with 11.3 micron PAH detection have higher gas mass and column density; AGN luminosity and r_AGN differ little  
  > "There is little dependence of the detection of nuclear $11.3\,\mu$m PAH emission on either AGN luminosity or distance from the AGN." (4.2 Dependence on AGN luminosity)
- IRS PAH ratios do not trend with nuclear N(H2) because CO is mostly not centrally peaked  
  > "There is no clear dependence of the *Spitzer*/IRS PAH ratios on the nuclear column density" (5.1 Spitzer/IRS PAH emission)

## Claim tuples

- H: Molecular gas shields PAHs in Seyfert nuclei | E: Compare CO(2-1) gas mass and N(H2) in slit regions between PAH-detected and non-detected nuclei | R: Medians 1.6e7 vs 2e6 Msun; N(H2) 2e23 vs 4e22 cm-2; K-S 2% and 0.8% | F: High N(H2) plays a role in protecting PAHs | **supported**
- H: X-ray dissociation half-life differs with PAH detection | E: Naphthalene half-life at 2.5 keV from N(H2), L_X, r_AGN | R: Shorter half-lives in nuclei without detection | F: Half-lives are shorter in non-detections, but mostly shorter than injection timescales | **supported**
- H: High nuclear N(H2) implies more neutral PAHs on circumnuclear scales | E: Compare IRS PAH ratios with nuclear N(H2) | R: No clear dependence | F: Not generally closer to neutral tracks, as CO is not centrally peaked | **refuted**

## Reasoning

- Why this data: _not stated_
- Why this method: Full 5-40 micron fit chosen because the mid-IR continuum is complicated  
  > "instead of using a local continuum we chose to perform a full fit of the $5-40\,\mu$m spectral range." (2.3 Spitzer/IRS observations)
- How they decided it was enough: _not stated_
- Limitation (authors): Half-lives are indicative only; uncertain H2 masses, averaged N(H2), only naphthalene, dehydrogenation ignored  
  > "We remark that these half-lives are only indicative of the general behavior." (4.3 Half-life)
- Limitation (authors): r21 and X_CO uncertain  
  > "However, we note that this ratio is rather uncertain." (3.3 Nuclear molecular gas masses)
- Caveat (inferred, ours): Small sample (22) with heterogeneous ALMA/NOEMA beams and mid-IR slits
- Caveat (inferred, ours): Detection of PAH depends on sensitivity and continuum of each mid-IR spectrum
- Caveat (inferred, ours): Constant r21=1 and Galactic X_CO may bias masses
- Caveat (inferred, ours): Naphthalene is a poor proxy for the large PAHs dominating emission

## Reproducibility

- Data public (paper): ALMA data downloaded from archive; some fluxes private  
  > "We downloaded the band 6 CO(2-1) and adjacent continuum raw data from the ALMA archive." (2.1 CO(2-1) and continuum 1.3mm observations)
- Products in archive: _not stated_
- Missing: Naphthalene cross-section and sigma_H values
- Missing: Private-communication CO fluxes for NGC 1320, NGC 2992
- Missing: Mid-IR PAH detection flags from published papers
- Missing: Imaging details beyond robust=0.5
- Data volume (inferred): ~100-300 GB raw for 9 ALMA projects
- Score (inferred): 3/5, ALMA data public and mass method simple, but several inputs (cross-sections, private fluxes, aperture details) are missing.
- Rediscovery candidate: no, Half-life inputs and some CO fluxes are not fully given, and the multi-instrument setup is heavy.

## Links

- Method: (cite: Sakamoto1999) (H2 mass formula from CO)
- Method: (cite: Monfredini2019) (X-ray PAH photodissociation and half-life formalism)
- Method: (cite: Smith2007) (pahfit)
- Companion: (cite: DominguezFernandez2020) (NOEMA observations and reduction)
- Companion: (cite: GarciaBurillo2019) (NGC 1068 ALMA CO(2-1))
- Related: 12 micron ALMA program (PI M. Malkan)

## Checks

```json
{
 "quotes": 76,
 "quotes_ok": 76,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 9,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 89,
  "stated": 54,
  "rate": 0.607
 },
 "evidence_ok": true
}
```

# The ALPINE-ALMA [CII] survey. Circumgalactic medium pollution and gas mixing by tidal stripping in a merging system at z ∼ 4.57

`2020A&A...643A...7G` | Astronomy and Astrophysics 2020 | first author: Ginolfi, M. | arXiv: 2004.13737 | DOI: 10.1051/0004-6361/202038284

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, star_formation
- Question: Does a merging galaxy system at z~4.57 host extended [CII] emission on circumgalactic scales, and does it arise from tidal stripping, outflows or faint satellites?  
  > "In this paper we present a study of the morpho-kinematic properties of [CII] emission in/around a major merging system at $z\sim4.57$" (Introduction)
- Target **VC_9780 (#A) and C15_705574 (#B) merging system**: coordinates RA 10h01m33.45s, Dec +02d22m10.19s  
  > "The phase was centered at the rest-frame UV position of $\rm VC\_9780$ (see Sec. [3.1](#sec:ancillary); $\rm RA: 10h01m33.45s$; $\rm DEC:  +02d22m10.19s$)." (2 ALMA Observations); "At the redshift of our target vuds_cosmos_5101209780 ($\rm VC\_9780$; $z_{\rm [CII]}$ = 4.573), 1 arcsecond corresponds to 6.55 proper kpc." (Introduction); z/distance z_[CII] = 4.573 (#A), 4.568 (#B)  
  > "The phase was centered at the rest-frame UV position of $\rm VC\_9780$ (see Sec. [3.1](#sec:ancillary); $\rm RA: 10h01m33.45s$; $\rm DEC:  +02d22m10.19s$)." (2 ALMA Observations); "At the redshift of our target vuds_cosmos_5101209780 ($\rm VC\_9780$; $z_{\rm [CII]}$ = 4.573), 1 arcsecond corresponds to 6.55 proper kpc." (Introduction); distance from ALPINE [CII] redshift  
  > "The phase was centered at the rest-frame UV position of $\rm VC\_9780$ (see Sec. [3.1](#sec:ancillary); $\rm RA: 10h01m33.45s$; $\rm DEC:  +02d22m10.19s$)." (2 ALMA Observations); "At the redshift of our target vuds_cosmos_5101209780 ($\rm VC\_9780$; $z_{\rm [CII]}$ = 4.573), 1 arcsecond corresponds to 6.55 proper kpc." (Introduction)

## Data provenance

- ALMA projects: 2017.1.00428.L
- bands: Band 7  
  > "ALMA observations of the merging system studied in this work were conducted in Band 7 on 2 June 2018" (2 ALMA Observations)
- frequencies and spectral setup: two sidebands, each two spws of 1.875 GHz, 15.6 MHz channels; lower sideband on [CII]  
  > "The spectral setup consisted of two sidebands, each composed of two spectral windows with total bandwidths of 1.875 GHz and channel width resolutions of 15.6 MHz." (2 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-2, 45 antennae  
  > "using a C43-2 array configuration with 45 antennae, and a total on-source time of 20 minutes." (2 ALMA Observations)
- baselines: _not stated_
- angular resolution: 1.21'' x 0.77'', PA -61 deg  
  > "The synthesized beam in our final data-products is $1.21''  \times 0.77"$, with a position angle of $-61^{\circ}$." (2 ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: 14 mJy/beam per 25 km/s channel; 60 uJy/beam continuum  
  > "$\sigma_{\rm cube} \sim 14$ mJy beam$^{-1}$" (2 ALMA Observations)
- time on source: 20 minutes  
  > "a total on-source time of 20 minutes" (2 ALMA Observations)
- observing dates: 2 June 2018  
  > "conducted in Band 7 on 2 June 2018" (2 ALMA Observations)
- pi or archival as stated: ALPINE Large Program, PI O. Le Fèvre  
  > "project 2017.1.00428.L, PI O. Le Fèvre" (2 ALMA Observations)
- Line: [CII] 158 um (not stated)
- Other facility **HST/ACS F814W and WFC3 F160W**: rest-frame UV images  
  > "see an HST/ACS F814W cutout in Fig. [1](#fig:fig1)a" (3.1)
- Other facility **Keck II/DEIMOS**: new spectroscopic redshifts, 106 new galaxies near the protocluster  
  > "which resulted in the spectroscopic confirmation of 106 new galaxies in the region in and around ${\rm PCl J1001+0220}$" (3.2)
- Other facility **UltraVISTA DR4 Ks**: rest-frame optical image  
  > "we display the UltraVista Ks-Band image from the fourth data release" (3.1)
- External data: M* and SFR of VC_9780  
  > "(see (cite: Faisst2019))" (3.1) [from (cite: Faisst2019)]
- External data: M* and SFR of C15_705574 from COSMOS2015  
  > "(from the COSMOS2015 catalogue [^2] ; (cite: Laigle2016))" (3.1) [from (cite: Laigle2016)]
- External data: L_[CII]-M_gas relation  
  > "Using the $L_{\rm [CII]}-M_{\rm gas}$ relation calibrated by (cite: Zanella2018)" (4.2) [from (cite: Zanella2018)]
- External data: typical mass outflow rate ~30 Msun/yr  
  > "typical mass outflow rates of $\dot{M}_{\rm out} \sim 30 ~ {\rm M_\odot ~ yr^{-1}}$ (as measured by (cite: Ginolfi2020)" (4.2) [from (cite: Ginolfi2020)]

## Processing

### Calibration

- pipeline or manual: automatic CASA pipeline, no additional flagging  
  > "No additional flagging was needed as the pipeline calibration output did not show any issue." (2 ALMA Observations)
- casa version: 5.4.0  
  > "version 5.4.0" (2 ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean, MFS for continuum  
  > "The continuum map was obtained running the `CASA` task `tclean` (multi-frequency synthesis mode) over the line-free visibilities in all spectral windows." (2 ALMA Observations)
- deconvolver: 500 iterations, S/N threshold 3 sigma  
  > "500 iterations and a signal-to-noise ratio (S/N) threshold of $\sigma_{\rm clean} = 3$ in the cleaning algorithm" (2 ALMA Observations)
- weighting robust: natural  
  > "we adopted a natural weighting of the visibilities to maximise the sensitivity." (2 ALMA Observations)
- uv taper: _not stated_
- cell size: 0.15''  
  > "a pixel size of 0.15$''$ and a spectral binning of 25 km s$^{-1}$" (2 ALMA Observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub  
  > "The [CII] datacube was generated from the continuum-subtracted visibilities (CASA task `uvcontsub`)" (2 ALMA Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.21'' x 0.77'', PA -61 deg  
  > "The synthesized beam in our final data-products is $1.21''  \times 0.77"$" (2 ALMA Observations)
- final rms: 14 mJy/beam (25 km/s), 60 uJy/beam continuum  
  > "$\sigma_{\rm cont} \sim 60$ $\mu$Jy beam$^{-1}$ in the continuum image" (2 ALMA Observations)

### Inherited from earlier work

- ALPINE data processing strategy  
  > "Additional information on the overall ALPINE data-processing strategy (including data quality assessment) can be found in (cite: Bethermin2020)." (2 ALMA Observations) [from (cite: Bethermin2020)]
- VMC density mapping technique  
  > "As in (cite: lemaux2018), we use the full VUDS and zCOSMOS" (3.2) [from (cite: lemaux2018)]
- size-fitting procedure for ALPINE galaxies  
  > "see (cite: Fujimoto2020) for an accurate description of the size-fitting procedure for ALPINE galaxies" (3.1) [from (cite: Fujimoto2020)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for continuum and uvcontsub
- Image size and clean mask
- Gaussian fit and aperture details for spectra and uncertainty estimation
- Conversion from flux to L_[CII] and L_[CII]-SFR relation parameters
- Aperture/contour used for the total spectrum (1-sigma contour definition and noise)
- PV diagram slit widths and angles

## Analysis recipe

1. **Image continuum and [CII] cube**: tclean MFS continuum; uvcontsub then cube with natural weighting, 25 km/s channels  
  > "For both continuum and [CII] datacube we adopted a natural weighting of the visibilities to maximise the sensitivity." (2 ALMA Observations)
   - software: CASA
   - parameter: 0.15'' pixels, 500 iterations, 3 sigma threshold  
  > "a pixel size of 0.15$''$ and a spectral binning of 25 km s$^{-1}$ ($\sim 29$ MHz)" (2 ALMA Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract spectra and moment maps of #A and #B**: 1'' diameter aperture spectra, Gaussian model, collapse cube over f_cen±sigma_G, fit 2D Gaussian to maps, re-extract with FWHM ellipses  
  > "We then estimate the spatial extent of the [CII]-emission arising from $\#A$ and $\#B$ by fitting a simple 2D Gaussian model to the velocity-integrated maps" (3.3)
   - fitting: 3-Gaussian modelling of #B spectrum to separate #C and #D  
  > "The line properties of $\#B$, $\#C$ and $\#D$ (total flux, centroid and FWHM) are estimated from a 3-Gaussian modelling of the spectrum." (3.3)
   - validation: 1'' aperture on [CII] peaks gives virtually unchanged results  
  > "we tested a 1$''$-aperture centred on the [CII] peaks, and the results are virtually unchanged" (footnote 6)
3. **Map total [CII] structure and PV diagrams**: velocity-integrated map over [-500,+500] km/s about z_ref=4.570; PV diagrams along A-B axis and orthogonal  
  > "we produce a velocity-integrated flux map by collapsing the spectral channels in the velocity range $[-500 : +500]$ km s$^{-1}$" (3.3)
   - fitting: _not stated_
   - validation: _not stated_
4. **Partition galaxy vs CGM [CII] luminosity**: compare spectrum within 1-sigma contour of total map with sum of the four galaxy spectra  
  > "we extract a spectrum of the total [CII]-emitting system from a region within the 1-$\sigma$ contour of the velocity-integrated map" (3.3)
   - fitting: _not stated_
   - validation: _not stated_
5. **Test origin of CGM [CII]**: outflow timescale from Zanella2018 gas mass and Mdot_out~30; UV diffuse SFR vs L_[CII]-SFR relations  
  > "we find that outflows would require at least $\sim$ 0.6 Gyr to expel the estimated amount of dense gas in the CGM" (4.2)
   - assumption: no re-accretion; both #A and #B drive outflows  
  > "(i) re-accretion does not occur, and (ii) both $\#A$ and $\#B$ have constantly had during their past growth a sufficient SFR" (4.2)
   - fitting: _not stated_
   - validation: three SFR calibrations give consistent results  
  > "We used three different calibrations, which give consistent results" (footnote 9)

## Software

- **CASA** 5.4.0: pipeline calibration, tclean, uvcontsub  
  > "version 5.4.0" (2 ALMA Observations)
- **LePHARE** : SED modelling for M* and SFR  
  > "measured through the spectral energy distribution (SED) modelling code `LePHARE`" (3.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| L_[CII] of #A | 3.5e8 | ±0.3e8 | Lsun | 2 | $L_{\rm [CII]}^{\#A} = 3.5 ~(\pm 0.3) \times 10^8 ~ {\rm L_\odot}$ |
| L_[CII] of #B | 6.6e8 | ±0.4e8 | Lsun | 2 | $L_{\rm [CII]}^{\#B} = 6.6 ~(\pm 0.4) \times 10^8 ~ {\rm L_\odot}$ |
| total L_[CII] | 2.3e9 | ±0.2e9 | Lsun | 4 | $L_{\rm [CII]}^{tot} = 2.3~(\pm 0.2) \times 10^9 ~ {\rm L_\odot}$ |
| L_[CII] of CGM | 1.1e9 | ±0.2e9 | Lsun | 4 | $L_{\rm [CII]}^{CGM} = 1.1 ~(\pm 0.2) \times 10^9 ~ {\rm L_\odot}$ |
| CGM gas mass | ~3e10 | not stated | Msun | 5 | $M_{\rm gas}^{\rm CGM} \sim  3\times 10^{10} ~{\rm M_\odot}$ |
| UV-based diffuse SFR in CGM | 13 | ±5 | Msun/yr | 5 | ${\rm SFR}_{\tiny{CGM}}^{\tiny{UV}}= 13 \pm 5 ~{\rm M_\odot ~ yr^{-1}}$ |
| [CII]-predicted CGM SFR | ~125 | not stated | Msun/yr | 5 | ${\rm SFR}_{\tiny{CGM}}^{\tiny{[CII]}} \sim 125~ {\rm M_\odot ~ yr^{-1}}$ |

## Qualitative findings

- [CII] structure of ~30 kpc diameter surrounds the system, with emission displaced >=10 kpc from UV/optical counterparts  
  > "with a projected diameter of $\sim 30$ kpc" (3.3)
- System lies at an overdensity peak of the protocluster PCl J1001+0220  
  > "our merging system at $z\sim4.57$ is nearly coincident with the overdensity peak of the N-E sub-component" (3.2)

## Claim tuples

- H: Does the merging system host a large CGM [CII] envelope? | E: Compared total [CII] spectrum with sum of galaxy spectra | R: About 50% of L_[CII] lies between the components | F: A metal-enriched circumgalactic envelope exists | **supported**
- H: Is the envelope from tidal stripping rather than outflows or faint satellites? | E: Outflow timescale estimate and UV vs [CII]-based SFR comparison | R: Outflows need >=0.6 Gyr; UV SFR ~10x lower than expected | F: Stripping dominates, with outflows and satellites contributing less | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Outflows rejected as dominant: would need >=0.6 Gyr  
  > "outflows might not be the dominant mechanism for injecting the large amount of circumgalactic cold gas observed in our system" (4.2)
- Alternative: Faint satellites do not significantly account for the CGM [CII]  
  > "small faint satellites do not significantly account for the detected large circumgalactic [CII] emission" (4.3)
- How they decided it was enough: _not stated_
- Limitation (authors): Resolution insufficient to tell if the [CII] tail is a dusty star-forming region within #A or a dusty neighbour  
  > "With the currently available ALMA resolution, it is unclear whether this [CII] tail is produced by a dust-obscured star-forming region within $\#A$" (3.3)
- Caveat (inferred, ours): Single short 20 min observation at ~1 arcsec resolution; CGM/galaxy split depends on aperture choices
- Caveat (inferred, ours): Gas mass and outflow estimates are rough with no uncertainties
- Caveat (inferred, ours): Stripping favoured by elimination, not directly tested; shocks not constrained

## Reproducibility

- Data public (paper): ALPINE Large Program 2017.1.00428.L; ALPINE data processing described in Bethermin2020  
  > "This paper is based on data obtained with the ALMA Observatory, under Large Program 2017.1.00428.L." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Exact apertures and contour for total spectrum
- Missing: Line-free channel selection
- Missing: DEIMOS and HST F160W data unpublished (in prep.)
- Data volume (inferred): ~5-10 GB for the single ALPINE Band 7 execution
- Score (inferred): 3/5, Public ALMA data and clear imaging settings, but spectral extraction details and some ancillary data are not provided.
- Rediscovery candidate: yes, Public ALPINE data, numeric luminosities, and a moderately complete recipe.

## Links

- Method: (cite: Bethermin2020) (ALPINE ALMA data processing)
- Method: (cite: lemaux2018) (VMC mapping technique and protocluster)
- Companion: (cite: LeFevre2020) (ALPINE survey overview)
- Companion: (cite: Faisst2019) (ALPINE ancillary dataset)
- Companion: (cite: Fujimoto2020) ([CII] halos in ALPINE)
- Related: ALPINE
- Related: VUDS
- Related: COSMOS

## Checks

```json
{
 "quotes": 64,
 "quotes_ok": 64,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 49,
  "rate": 0.636
 },
 "evidence_ok": true
}
```

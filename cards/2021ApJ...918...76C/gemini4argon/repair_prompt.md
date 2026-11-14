# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2021ApJ...918...76C\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# Towards a More Complex Understanding of Natal Super Star Clusters with Multiwavelength Observations

## Abstract

Henize 2-10 (He 2-10) is a nearby (D = 9 Mpc) starbursting blue compact dwarf galaxy that boasts a high star formation rate and a low luminosity AGN (cite: Reines:2011; Reines:2016). He 2-10 is also one of the first galaxies in which embedded superstar clusters (SSCs) were discovered. SSCs are massive, compact star clusters that will impact their host galaxies dramatically when their massive stars evolve. Here, we discuss radio, submillimeter, and infrared observations of He 2-10 from 1.87 $\mu$m to 6 cm in high angular resolution ($\sim$0.3$''$), which allows us to disentangle individual clusters from aggregate complexes as identified at lower resolution. These results indicate the importance of spatial resolution to characterize SSCs, as low resolution studies of SSCs average over aggregate complexes that may host SSCs at different stages of evolution. We explore the thermal, non-thermal, and dust emission associated with the clusters along with dense molecular tracers to construct a holistic review of the natal SSCs that have yet to dramatically disrupt their parent molecular clouds. We assess the production rate of ionizing photons, extinction, total mass, and the star formation efficiency associated with the clusters. Notably, we find that the star formation efficiency for the some of the natal clusters is high ($>$ 70$\%$), which suggests that these clusters could remain bound even after the gas is dispersed from the system from stellar feedback mechanisms. If they remain bound, these SSCs could survive to become objects indistinguishable from globular clusters.

# Introduction

Rich clusters of stars significantly impact their host galaxies, as the massive stars can undergo nearly simultaneous supernovae, driving outflows into the interstellar medium and potentially into the intergalactic medium (cite: Johnson:2000; Heckman:2001; Martin:2002; Gilbert:2007). Super star clusters (SSCs) are an example of some of the most extreme types of stellar systems with stellar densities that can be orders of magnitudes higher than a typical open cluster. We adopt as description of SSCs that they are massive ($\gtrsim$ 10$^{4.5}$ $\textrm{M}_{\odot}$) compact ($r$ $\leq$ 3 pc) star clusters with stellar densities often exceeding 10$^4$ stars pc$^{-3}$ in their cores ((cite: Ryon:2017) and references therein; (cite: Johnson:2018)).

Merging and starbursting galaxies in the current universe may host similar environments to those that formed globular clusters (GCs), e.g., gas-rich, high pressure disks, and turbulent (cite: Portegies:2010; Keller:2020), and SSCs are found in such environments. Whether SSCs are consistent with being progenitors of GCs has been an ongoing line of study (e.g., (cite: Holtzman:1992; Whitmore:1995; Whitmore:2000; Harris:2003; Portegies:2010; Longmore:2014; Horta:2021)). If SSCs are local analogs to GC precursors, then nearby SSCs provide an opportunity to study the physical conditions necessary for GCs to form. The infant mortality rate of GCs is likely to be quite high (possibly as high as 99$\%$; (cite: Fall:2001)), which suggests that this mode formation may have been critical, and perhaps dominant, in the time of galaxy assembly in order to account for the population of GCs we observe today. Recent simulations (e.g., (cite: Keller:2020; Horta:2021)) suggest that GC formation is not primarily due to an exotic formation scenario (e.g., dark matter mini halos) but instead it is the extreme end of a continuous distribution. Observations of SSCs in merging or starbursting galaxies can provide insight to the formation process, the conditions of the local interstellar medium, and perhaps what characteristics are important to enable a cluster to remain bound such that it will persist for billions of years. While much is known about adolescent SSCs with ages between $\sim$3 – 10 Myr, these clusters have already emerged from their birth material to be clearly visible at optical wavelengths, thus erasing their birth conditions as the clusters themselves have already undergone significant evolution. We need to probe SSCs which have yet to emerge from their parent molecular environments to fully characterize this mode of star formation.

The starbursting dwarf galaxy Henzie 2-10 (He 2-10; R.A. = 08$^h$ 36$^m$ 15.120$^s$, decl = –26$^{\circ}$ 24$'$ 34.157$''$) is one of the nearest galaxies (D = 9 Mpc; (cite: Johansson:1987)) known to host a multitude of SSCs at varying stages of evolution. From Hubble Space Telescope (HST) data, (cite: Johnson:2000) determined masses for the optically visible adolescent SSCs in He 2-10. They found that SSCs in the central region of He 2-10 (their region ‘A’) have masses between 1.6 – 2.6 $\times$ 10$^6$ $\textrm{M}_{\odot}$ while adolescent SSCs in a region $\sim$ 9$''$ east have lower masses between 2.6 – 6.6 $\times$ 10$^4$ $\textrm{M}_{\odot}$ (their region ‘B’). Within $\sim$ 5$''$ of the nominal center of He 2-10, (cite: Kobulnicky:1999) identified radio sources at 6 cm that are consistent with being Ultra Dense (UD) H ii regions. UD H ii regions are dense (n$_e$ $\gtrsim$ 10$^4$ cm$^{-3}$) ionized structures of a few parsecs in size that host a massive stellar cluster (cite: Kobulnicky:1999; Vacca:2002). They are extragalactic scaled up versions of galactic Ultra Compact (UC) H ii regions, which are typically excited by a single massive star and are $\lesssim$ 0.1 pc in size (cite: Wood:1989). (cite: Kobulnicky:1999) suggested further that these UD H ii regions host the young precursors to optically visible SSCs: natal SSCs.

![](f1.pdf)

(cite: Kobulnicky:1999) labeled these radio sources Knots 1, 2, 3, 4, and 5 (Figure [1](#fig:radioknots)), and since their identification, the radio knots have inspired multiwavelength studies to assess the properties of the natal SSCs and their environments. With the historical Very Large Array, (cite: Johnson:2003) modeled the spectral energy distributions (SEDs) of the knots between 5 and 43 GHz; they estimated stellar masses of (1.2, 1.6, 4.3, and 1.3) $\times$ 10$^{5}$ $\textrm{M}_{\odot}$ for Knots 1, 2, 4, and 5, respectively, and modeled the physical properties of the UD H ii regions. From infrared (IR) observations with the Very Large Telescope (VLT) at 2.2, 3.8, and 4.8 $\mu$m as well as HST data, (cite: Cabanac:2005) confirmed the classification of Knots 1, 2, and 5 as UD H ii regions and reported that the clusters are young ($\lesssim$ 6 Myr). (cite: Cabanac:2005) identified a number of optical sources spatially coincident with Knot 4, labeled in their Figure 2a as L4a – L4d, which they interpreted as Knot 4 being a mix of normal H ii regions and supernova remnants (SNRs) instead of an UD H ii region. (cite: Reines:2012) also reported a SNR in Knot 4 that is spatially coincident with the most optically-luminous SSC in their Very Long Baseline Interferometry (VLBI) observations.

(cite: Johnson:2003) found that Knot 3 had a spectral index consistent with having significant non-thermal emission, and in more recent work, (cite: Reines:2011), (cite: Reines:2012), (cite: Reines:2016), and (cite: Riffel:2020) identified the low luminosity central black hole of He 2-10 hosted in Knot 3 from VLA, VLBI, and *Chandra* observations. (cite: Hebbar:2019) suggest Knot 3 may be a supernova remnant based on their reanalysis of the X-ray spectrum first presented by (cite: Reines:2016). They argue that a hot plasma model fits the X-ray spectrum better than a power-law model, with the former and latter typically used for supernova remnants and luminous AGNs, respectively. However, (cite: Reines:2016) note that the soft X-ray spectrum is similar to other low-luminosity AGNs radiating at low Eddington ratios (cite: Constantin:2009; Baganoff:2003). The X-ray spectrum also shows evidence for variability on hour-long timescales, which is incompatible with a supernova remnant (cite: Reines:2016).

He 2-10 also hosts dense molecular precursor clouds, which may have the potential to form SSCs. (cite: Johnson:2018) mapped CO with the Submillimeter Array (SMA) and dense molecular tracers such as HCN, HNC, CCH, and HCO$^+$ in He 2-10 with the Atacama Large Millimeter/submillimeter Array (ALMA). They discuss the molecular morphology of these dense clouds and how the molecular lines are correlated with the evolutionary state of the natal clusters. Near the optical SSCs and the AGN, there is a a valley in CO and dense gas tracers (cite: Johnson:2018; Beck:2018); however, the embedded natal SSCs appear to coincide with peaks in the denser molecular tracers (cite: Johnson:2018). (cite: Imara:2019) also presented a study of CO to characterize differences in stellar nurseries between He 2-10 and the Milky Way. They reported that the most massive Giant Molecular Clouds He 2-10 are gravitationally bound, which suggests that He 2-10 can continue to form SSCs. He 2-10 hosts natal and adolescent SSCs and has the potential to continue to form them, making it an ideal laboratory to understand this mode of star formation.

In this work, we discuss the results of radio, mm, submm, and IR observations of the radio knots in He 2-10 with high resolution data that allow us to disentangle individual clusters from aggregate complexes as identified at lower resolution (e.g., (cite: Kobulnicky:1999)). We present archival Karl G. Jansky Very Large Array[^1] (VLA) and ALMA data to construct SEDs of the radio knots to characterize the environments that host the natal SSCs. In Section [\[sec:kaobs\]](#sec:kaobs), we present new VLA 33 GHz observations of He 2-10 from VLA program 15B-197. In addition, there is a wealth of continuum data not yet analyzed in the VLA and ALMA archives, though some of the data have been published for other purposes (e.g., spectral lines). In Section [\[sec:vlaold\]](#sec:vlaold), we discuss pre-upgrade VLA 5 and 8 GHz observations and more recent 15 and 22 GHz archival observations. In Section [\[sec:almaobs\]](#sec:almaobs), we present an overview of the archival observations of He 2-10 with ALMA, and in Section [\[sec:nicmosobs\]](#sec:nicmosobs), we discuss archival HST/NICMOS observations at 1.8756 $\mu$m. Section [\[sec:photom\]](#sec:photom) presents the source finding and photometry of the radio knots. In Section [\[sec:SED\]](#sec:SED), we discuss the SED model and results. We present estimates of the production rate of the ionizing photons and the stellar masses of the sources in Section [\[sec:qly\]](#sec:qly) and in Section [\[sec:extinction\]](#sec:extinction), the extinction estimates. Section [\[sec:dustmass\]](#sec:dustmass) presents our analysis of the dust mass associated with the knots, and Section [\[sec:SFE\]](#sec:SFE) discusses the star formation efficiency of the knots. Finally in Section [\[sec:dis\]](#sec:dis), we provide an overview of our results and characteristics of the radio knots of He 2-10.

# Observations and Data Reduction

A range of new and archival long wavelength data are available from observations spanning the last two decades. These data have not yet been systematically evaluated and analyzed in conjunction. Here, we summarize the archival data and recent observations of He 2-10 at radio, mm, and submm wavelengths.

## New VLA Observations

With the VLA, we observed He 2-10 at Ka-band (28$\;$GHz – 36$\;$GHz) in A configuration between August and September of 2015. Table [1](#tab:obs) gives the details of the observations. We used the source J1331+3030 (3C286) as the flux density calibrator, J1229+0203 (3C273) as the bandpass calibrator, and J0836-2016 as the complex gain calibrator. Due to the high frequency of the observations and array configuration, scans of the complex gain calibrator were interleaved with scans of the program source in intervals of $\sim$2 minutes and pointing scans were completed every hour. With the 3-bit correlator configuration, we obtained a total bandwidth of $\sim$8$\;$GHz across Ka-band.

|  |  |
|:---|:---|
| VLA Project Code | 15B-197 |
| Date of Observations | 2015 Aug 31; 2015 Sept 1, 8, 19, $\&$ 24 |
| Number of Scheduling Blocks | 4 |
| Duration of Scheduling Blocks (hr) | 1.5 |
| Frequencies Observed (GHz) | 30; 32; 34; 36 |
| Number of Frequency Channels per IF | 2048 |
| Channel Width (MHz) | 1 |
| VLA configuration | A |
| Total Integration Time on Source (hr) | 2.4 |

: Log of Observations

These were 3-bit observations that had 2.048$\;$GHz wide intermediate frequency bands (IFs) centered on the frequencies listed. Each IF was composed of sixteen 128$\;$MHz wide subbands.

The data were reduced and imaged using the NRAO Common Astronomy Software Applications (CASA) version 5.4.2 ([casa.nrao.edu](casa.nrao.edu); (cite: McMullin:2007)). We checked the flux calibration by using 3C286 as the flux and bandpass calibrator and calibrating the 3C273 as a science target; the reported flux density of 3C273 was consistent with the VLA Calibrator Manual[^2], and the two methods of calibration produced similar results within the uncertainties. Four 1.5 hr observations were completed in A array yielding $\sim$2.4 hr integrated time on source[^3]. *Natural* weighting was employed in the CASA task tclean to recover the best signal/noise ratio possible at the expense of resolution. He 2-10 is a low declination source ($\sim$ –26$^{\circ}$), so we down-weighted the E-W arms and used a taper of 800k$\lambda$ $\times$ 4000k$\lambda$ $\times$ 90$^{\circ}$, resulting in a synthesized beam of 0.162$''$ $\times$ 0.140$''$. While we do achieve the theoretical rms for the 2.4 hr integration time, there are still significant artifacts in the map despite these efforts. High frequency observing is sensitive to the weather conditions, and given the low declination of the source, we believe the data suffer from significant decorrelation. Thus, the flux densities reported here are treated as a lower limit thorough this work.

## VLA Archival Observations

At longer radio wavelengths, we selected the newest observations of the appropriate resolution from the VLA archive. The most recent 4 GHz (C-band) and 8 GHz (X-band) observations available for He 2-10 are in program AJ314, which are from 2004 and before the VLA was upgraded. These observations included the Pie Town up-link. These data were initially published in (cite: Reines:2011) with focus on properties of the AGN. The flux density calibrator was 3C286, and the complex gain calibrator was J0836-2016. The data were re-imaged using CASA 5.4.2. Table [2](#tab:alldataprop) lists the final beam, the peak intensity, and the rms of the final images for this program and the ones that follow below. VLA program 16B-067 contains 14 GHz (Ku-band) and 22 GHz (K-band) continuum data, which we reprocessed and imaged using the VLA pipeline in CASA 5.4.2. We applied a taper of 600k$\lambda$ $\times$ 3000k$\lambda$ $\times$ 90$^{\circ}$ during imaging in both cases. These data have not been published to our knowledge. For these data, 3C138 was the flux density and bandpass calibrator, and J0836-2016 was the complex gain calibrator.

## ALMA Archival Observations

Here, we detail the archival ALMA observations that we include in our analysis of He 2-10. The calibrated data were retrieved from the archive and restored using the delivered scripts from NRAO. Properties of the images are given in Table [2](#tab:alldataprop).

The $^{12}$CO$\;$(1-0) and 113$\;$GHz continuum data were obtained for the related projects 2015.1.01569 and 2016.1.00027, with an originally proposed resolution of 0.6$''$. Fortunately, the 2016.1.00027 data were taken while ALMA was between configurations, so some longer baselines were included in the array at the time of observation. Thus, we were able to re-image the data at higher angular resolution.

Project 2015.1.01569 was observed twice with 39 antennas each time; on 2016 July 31, J1037-2934 (900 mJy) was used as the amplitude and bandpass calibrator and J0826-2230 (750 mJy) as the phase calibrator. On 2016-08-02, J1107-4449 (1.1 Jy), J1037-2934, and J0826-2230 were used as the amplitude, bandpass, and phase calibrators, respectively. The data were calibrated with the ALMA data pipeline Pipeline-Cycle3-R4-B, v.36660 (cite: Davis:2020), packaged with CASA 4.5.3. These data were initially published in (cite: Imara:2019).

Project 2016.1.00027 was observed twice on 2017 July 13 with 42 antennas; the first time was using J0538-4405 (1.2 Jy) as the amplitude calibrator, J1037-2934 (1.3 Jy) as the bandpass calibrator, and J0846-2607 (330mJy) as the phase calibrator. The second execution used J1037-2934 as the amplitude and bandpass calibrator and J0846-2607 as the phase calibrator. The data were calibrated with Pipeline-Cycle4-R2-B v.39732 packaged with CASA 4.7.2 and imaged in CASA 5.6.1-8.

At 250 GHz, project 2012.1.00413 was observed 5 times between 2015 Sept 05 and 2015 Sept 29 with 30-35 antennas. J1037-295 (650 mJy) or J0538-4405 (1.3 Jy) were used for the amplitude calibration, J0750+1231 (570 mJy), J0538-4405, or J1058+0133 (3.3 Jy) for the bandpass calibration, and J0747-3310 (500 mJy) or J0826-2230 (300-450 mJy) for the phase calibration. The data were calibrated with Pipeline-Cycle3-R1-B v.34044 in CASA 4.3.1 and imaged in CASA 5.6.1-8. These data were initially published in (cite: Johnson:2018).

Finally at 340 GHz, project 2016.1.00492 was observed on 2016-11-15, using J0538-4405 (340 mJy) for the amplitude and bandpass calibration and J0846-2607 (210 mJy) for the phase calibration. The data were calibrated with Pipeline-Cycle4-R2-B v.38377 in CASA 4.7.0 and re-imaged with CASA 5.6.1-8. The data were initially published in (cite: Beck:2018) with a focus on the $^{12}$CO$\;$(3-2) data.

+:------------------+:----------------:+:------:+:--------------------:+:----------------:+:----------------:+
| Project           | $\nu$            | Robust | Beam                 | Peak             | rms              |
|                   +------------------+        +----------------------+------------------+------------------+
|                   | (GHz)            |        | ($''$)               | (mJy bm$^{-1}$)  | (mJy bm$^{-1}$)  |
+-------------------+------------------+--------+----------------------+------------------+------------------+
| VLA AJ314         | 5                | 0.0    | 0.620 $\times$ 0.248 | 1.06             | 0.015            |
|                   |                  |        +----------------------+------------------+------------------+
|                   |                  |        | 0.300                | 0.95             | 0.018            |
+-------------------+------------------+--------+----------------------+------------------+------------------+
| VLA AJ314         | 8                | 0.5    | 0.366 $\times$ 0.150 | 0.57             | 0.012            |
|                   |                  |        +----------------------+------------------+------------------+
|                   |                  |        | 0.300                | 0.65             | 0.012            |
+-------------------+------------------+--------+----------------------+------------------+------------------+
| VLA 16B-067       | 15               | 0.5    | 0.322 $\times$ 0.210 | 0.35             | 0.017            |
|                   |                  |        +----------------------+------------------+------------------+
|                   |                  |        | 0.300                | 0.39             | 0.024            |
+-------------------+------------------+--------+----------------------+------------------+------------------+
| VLA 16B-067       | 22               | 0.5    | 0.192 $\times$ 0.152 | 0.31             | 0.023            |
|                   |                  |        +----------------------+------------------+------------------+
|                   |                  |        | 0.300                | 0.48             | 0.023            |
+-------------------+------------------+--------+----------------------+------------------+------------------+
| VLA 15B-197       | 33               | 2.0    | 0.162 $\times$ 0.140 | 0.08             | 0.012            |
|                   |                  |        +----------------------+------------------+------------------+
|                   |                  |        | 0.300                | 0.16             | 0.019            |
+-------------------+------------------+--------+----------------------+------------------+------------------+
| ALMA 2016.1.00027 | 113              | 0.0    | 0.381 $\times$ 0.206 | 0.30             | 0.017            |
|                   |                  |        +----------------------+------------------+------------------+
|                   |                  |        | 0.300                | 0.29             | 0.019            |
+-------------------+------------------+--------+----------------------+------------------+------------------+
| ALMA 2012.1.00413 | 250              | 2.0    | 0.191 $\times$ 0.157 | 0.14             | 0.013            |
|                   |                  |        +----------------------+------------------+------------------+
|                   |                  |        | 0.300                | 0.28             | 0.025            |
+-------------------+------------------+--------+----------------------+------------------+------------------+
| ALMA 2016.1.00492 | 340              | 0.5    | 0.306 $\times$ 0.265 | 0.39             | 0.052            |
|                   |                  |        +----------------------+------------------+------------------+
|                   |                  |        | 0.300                | 0.47             | 0.048            |
+-------------------+------------------+--------+----------------------+------------------+------------------+
| HST/NICMOS        | $\lambda_{peak}$ | ...    | FWHM                 | 0.42             | 0.014            |
+-------------------+------------------+        +----------------------+------------------+------------------+
| F187N             | 1.8756 $\mu$m    |        | 0.0191 $\mu$m        | mJy pixel$^{-1}$ | mJy pixel$^{-1}$ |
+-------------------+------------------+--------+----------------------+------------------+------------------+

: Log of Projects Used in this Work

The top row associated with each project code lists the image properties, and the following row gives the image properties of the convolved map.

Robust of 2.0 is nearly equivalent to *natural* weighting.

## HST NICMOS Archival Observations 

The Near Infrared Camera and Multi-Object Spectrometer (NICMOS) data from our project 10894 were retrieved from the Hubble Legacy Archive. These data were initially published in (cite: Reines:2011), which focused on properties of the AGN. At He 2-10’s radial velocity of 873 km s$^{-1}$, the narrow-band filters F190N and F187N have transmission at Paschen $\alpha$ (Pa$\alpha$) of 0.016 and 0.22 (close to the maximum for that filter), respectively. The images required a shift of 1.33$''$ to match the radio data; we estimate a positional uncertainty of 0.1$''$. The images were converted to flux density units (Jansky pixel$^{-1}$). If the SEDs of the SSC are Rayleigh-jeans tails of hot star SEDs, the continuum in F187N will be 3$\%$ brighter than in F190N. If the SED shape is different, for example with a hot dust contribution, that number will differ. In the subsequent analysis, we scaled the F187N filter down by the theoretical scale of 3$\%$ before subtracting it from the F190N filter.

## Source Extraction and Photometry

Ideally for photometry, the maps across all frequencies would be convolved to a common resolution that is set by the largest resolution available. The largest resolution is the C-band (5 GHz) map at 0.620$''$ $\times$ 0.248$''$. While this resolution is an improvement on previous work in (cite: Johnson:2003), the majority of the maps have a better (higher) resolution than the older 2004 C- and X-band data. We convolved the maps to a common synthesized beam of 0.3$''$, which is roughly the synthesized beam at a robust of 0.5, excluding the two historical VLA programs. These maps are shown in Figure [2](#fig:all1). For C-band, this is a significant super-resolution of the data in the declination direction. The images are cleaned deeply, and we estimate from comparing the model and residuals from clean that only 5$\%$ of the flux density remains in the residuals. This uncertainly is less than uncertainty due to the flux calibration. For X-band, this enforced restoring beam amounts to beam reshaping and modest super-resolution in the declination direction. Similarly, for the ALMA Band 3 (113 GHz) map, the forced restored image at a 0.3$''$ round beam amounts to moderate super-resolution in the declination direction. We note again that the 33 GHz data suffers from decorrelation; we treat the extracted flux densities from the 33 GHz data as a lower limit.

(cite: Johnson:2003) convolved the maps to a common synthesized beam of 0.95$''$ $\times$ 0.44$''$ for their analysis of five radio knots. With our higher resolution maps, the morphologies of the radio knots are different, and in some cases, we identify multiple components within a knot. Because the photometry apertures used in this work are not identical to those of (cite: Johnson:2003), we expect that our reported flux densities may not agree with those reported by (cite: Johnson:2003). However, we expect the differences to be a dependent on the aperture used and not absolute flux calibration. As a check, we convolved the 5, 8, and 15 GHz maps from programs AJ314 and 16B-067 to the synthesized beam from (cite: Johnson:2003) to compare the flux calibrations against their 1995 AK0400 program. We are in possession of the original FITS images used in (cite: Johnson:2003) and are able to make a direct comparison without needing to re-reduce the data from the archive.

We find that for any given size of aperture, our 2004 AJ314 5 GHz map is $\sim$2$\times$ higher in flux density than the 1995 AK0400 5 GHz map, which was previously noted by (cite: Reines:2011). This is cause for concern, as there is disagreement between the data sets despite the similar observing configurations. Fortunately, both observing programs included a secondary calibrator that can be used as a check on the flux calibration. When calibrated as a science target, the secondary calibrator (J1146+399) in the 1995 AK0400 data has a flux is a factor of 2 lower than the reported flux density in the updated VLA Calibrator Manual. However, the secondary calibrator (J0713+438) in the 2004 AJ314 data agrees with the VLA Calibrator Manual. We re-reduced the 1995 data to verify the calibration and found similar results. It is understood, however, that the VLA calibrator manual may be out of date due to time variability of the flux densities of the calibrators. The flux densities reported in Table [\[tab:fluxcontour\]](#tab:fluxcontour) are not modified, i.e., they are the values extracted from the calibrated 2004 AJ314 data. However to account for the discrepancy between the calibrations, we adjust the flux density and error bars when we model the spectral energy distribution in Section [\[sec:SED\]](#sec:SED). We discuss this modification further in that section.

Similarly, the 15 GHz data does not agree between the two data sets. We convolved the 16B-067 15 GHz map to the resolution of the AK0400 map, and for any aperture size we use between the two, the 16B-067 15 GHz map flux density is $\sim$1.4$\times$ lower than that of the AK0400 map. Neither the 15 GHz AK0400 nor the 16B-067 program observed a secondary flux calibrator, so we cannot check the calibration against the calibrator manual. As with the 5 GHz data, we modify the 15 GHz flux densities for the SED analysis in Section [\[sec:SED\]](#sec:SED). We did not find similar inconsistence between the 2004 AJ314 8 GHz data and the AK0400 8 GHz map; the flux densities extracted for any given aperture size from both data sets agree within the errors.

### Source Identification and Photometry for Sources Extracted from the Convolved Maps

(cite: Kobulnicky:1999) and (cite: Johnson:2003) identify five radio knots in their low resolution maps, 0.8$''$ $\times$ 0.4$''$ and 0.95$''$ $\times$ 0.44$''$, respectively. At a distance of 9 Mpc, the low resolution maps probe spatial scales of $\sim$35 pc. Our maps convolved to a common synthesized beam of 0.3$''$ (13 pc) are $\sim$3$\times$ higher in resolution, and by inspection of the maps in their native resolutions, we identify additional sources from the aggregate complexes initially identified by (cite: Kobulnicky:1999). Comparison of our maps and Figure 1 of (cite: Johnson:2003) shows that their Knot 4 is at least two sources, which we label as Knot 4a and 4b. Knots 1 and 2 appear to also have an addition component in their vicinity. We label these three sources as Knot 1a, 1b, and 2; however, it is difficult to disentangle Knot 1b in relation to Knots 1 and 2 of the original maps. We could have just as easily called Knot 1b as Knot 2b and direct comparison between our Knot 2 and the original Knot 2 in (cite: Johnson:2003) needs to be done cautiously.

For photometry, we stacked the convolved 0.3$''$ maps, which includes all the maps listed in Table [2](#tab:alldataprop), except for the HST/NICMOS map. The stacked image reinforces persistent sources over the wide range of frequencies, but it likely poorly preserves morphological differences and may only capture the high surface brightness features. We overlaid contours of the stacked image and selected the contour of 20$\times$ the rms (73 $\mu$Jy bm$^{-1}$) of the stacked map. All seven sources are present in the stacked map. In the individual maps, the contour level chosen corresponds to at least a 5$\sigma$ contour, except for the 340 GHz map. In the 340 GHz map, this would be equivalent to a 3$\sigma$ contour. We manually inspected a range of contour levels in the stacked and individual maps; we concluded that a 20$\sigma$ contour best represents the morphology of the sources across all the frequency maps and maximizes the flux included in the analysis while minimizing contamination from noise. The contours have sharp edges in crowded regions because we generously masked sources to not double count extended faint emission in the pixels between the sources. While we employed a mask by manually inspecting the emission in the maps, our choice of pixel assignment in the fainter emission does not significantly change the results. The errors reported on the flux densities are dominated by uncertainties in the flux calibration.

Figure [3](#fig:stacked) shows the contours that delineate the extent of the sources in the stacked map. We identify seven sources, whose labels and coordinates are given in Table [\[tab:coords\]](#tab:coords). The semi-major and -minor axes in columns 4 and 5 are a 2D Gaussian model of the region extracted by the contour to approximate the size of each source. The errors reported on the flux density follow (cite: Condon:1997) for elliptical Gaussian fits and incorporate the systematic errors from the telescopes. For the ALMA bands, the systematic errors are 10$\%$ (cite: Fomalont:2014), and for the VLA, 5$\%$ for frequencies $<$ 15 GHz and otherwise 15$\%$[^4]. We used the same contour footprint in each map to calculate the integrated flux density in the same manner as CASA[^5]. To briefly summarize, we sum the intensity across the pixels associated with the source and divide it by the beam area. The beam area is defined as $\textrm{beam area} = \frac{\pi}{4\ln{2}} \theta_{maj} \theta_{min},$ where $\theta_{maj}$ and $\theta_{min}$ are the major and minor axes of the beam respectively. For the background subtraction, we masked the sources and calculated the median intensity of the image. We then multiplied the median background intensity by the number of beam areas for the source to find a background flux density. Table [\[tab:fluxcontour\]](#tab:fluxcontour) lists the background subtracted flux densities for extracted sources.

![](f3.pdf)

P2cmP2cmP3cmP1cmP1cm & & & a$_{maj}$ & b$_{min}$\
& & & ($''$) & ($''$)\
1a & 8$^{h}$36$^{m}$15.01$^{s}$ & –26$^{\circ}$24$'$33.66$''$ & 0.23 & 0.17\
1b & 8$^{h}$36$^{m}$15.01$^{s}$ & –26$^{\circ}$24$'$34.10$''$ & 0.22 & 0.17\
2 & 8$^{h}$36$^{m}$15.05$^{s}$ & –26$^{\circ}$24$'$33.86$''$ & 0.37 & 0.20\
3 & 8$^{h}$36$^{m}$15.12$^{s}$ & –26$^{\circ}$24$'$34.16$''$ & 0.19 & 0.17\
4a & 8$^{h}$36$^{m}$15.22$^{s}$ & –26$^{\circ}$24$'$33.86$''$ & 0.36 & 0.27\
4b & 8$^{h}$36$^{m}$15.24$^{s}$ & –26$^{\circ}$24$'$34.50$''$ & 0.31 & 0.27\
5 & 8$^{h}$36$^{m}$15.30$^{s}$ & –26$^{\circ}$24$'$34.90$''$ & 0.34 & 0.20\

Approximate semi-major (a$_{maj}$) and semi-minor (b$_{min}$) axes from the contoured regions in Figure [3](#fig:stacked).

P1.3cmP1.7cmP1.7cmP1.7cmP1.7cmP1.7cmP1.7cmP1.6cm Freq &\
(GHz) & 1a & 1b & 2 & 3 & 4a & 4b & 5\

5 & 0.27 $\pm$ 0.03 & 0.38 $\pm$ 0.03 & 0.74 $\pm$ 0.06 & 0.66 $\pm$ 0.04 & 1.35 $\pm$ 0.09 & 1.07 $\pm$ 0.07 & 0.89 $\pm$ 0.06\
8 & 0.31 $\pm$ 0.05 & 0.28 $\pm$ 0.05 & 0.61 $\pm$ 0.10 & 0.46 $\pm$ 0.07 & 1.07 $\pm$ 0.17 & 0.86 $\pm$ 0.13 & 0.75 $\pm$ 0.12\
15 & 0.23 $\pm$ 0.04 & 0.25 $\pm$ 0.04 & 0.38 $\pm$ 0.08 & 0.24 $\pm$ 0.03 & 0.57 $\pm$ 0.10 & 0.71 $\pm$ 0.08 & 0.42 $\pm$ 0.07\
22 & 0.29 $\pm$ 0.06 & 0.27 $\pm$ 0.06 & 0.54 $\pm$ 0.11 & 0.26 $\pm$ 0.05 & 0.77 $\pm$ 0.14 & 0.81 $\pm$ 0.14 & 0.61 $\pm$ 0.11\
33 & 0.10 $\pm$ 0.04 & 0.11 $\pm$ 0.04 & 0.16 $\pm$ 0.06 & 0.08 $\pm$ 0.02 & 0.28 $\pm$ 0.07 & 0.25 $\pm$ 0.06 & 0.16 $\pm$ 0.05\
113 & 0.19 $\pm$ 0.04 & 0.17 $\pm$ 0.04 & 0.38 $\pm$ 0.08 & 0.13 $\pm$ 0.03 & 0.55 $\pm$ 0.09 & 0.57 $\pm$ 0.09 & 0.40 $\pm$ 0.06\
258 & 0.24 $\pm$ 0.05 & 0.22 $\pm$ 0.05 & 0.47 $\pm$ 0.09 & 0.07 $\pm$ 0.03 & 0.51 $\pm$ 0.10 & 0.44 $\pm$ 0.10 & 0.37 $\pm$ 0.08\
340 & 0.36 $\pm$ 0.09 & 0.37 $\pm$ 0.08 & 0.77 $\pm$ 0.16 & 0.13 $\pm$ 0.05 & 0.75 $\pm$ 0.17 & 0.71 $\pm$ 0.15 & 0.62 $\pm$ 0.15\

$\lambda$1.876 & & & & & & &\
$\mu$m &\

All numerical entries given in mJy except for column one.

Flux density in Pa$\alpha$ map for each knot.

### Photometry in Pa$\alpha$ Map 

Figure [4](#fig:nicmos) is a continuum subtracted HST/NICMOS Pa$\alpha$ map; the raster scale is normalized to the peak in the convolved 8 GHz map for ease of comparison between this figure and Figure [2](#fig:all1). We initially extracted the flux density for each source using the contours from the stacked image, similar to the photometry in the other maps. With these apertures, the extracted regions for Knots 4a, 4b, and 5 include features in the Pa$\alpha$ map that may not actually be associated with the radio knots. Of particular note is the bright Pa$\alpha$ feature located near Knot 4b. This compact feature appears to have optical counterparts, such as those seen in Figure 3 of (cite: Cabanac:2005), but is offset from the radio peak. Inclusion of this compact feature alone significantly boosts the flux density by a factor of $\sim$2.6 for Knot 4b, which has undesirable consequences in our calculation of the extinction in Section [\[sec:extinction\]](#sec:extinction): namely, it produces a negative extinction value for this line of sight.

To avoid unphysical extinction values, we extracted the flux density for a region that corresponds to the half light radius of each source in the 33 GHz map, which roughly corresponds to a 2$\sigma$ contour. The apertures are approximately 30$\%$ smaller with this treatment. The main motivation in using the half light radius is the morphology of the 33 GHz data for Knots 4a and 5 because the bright features in the Pa$\alpha$ map are not included in the half light contour. We believe that examination of Figure [4](#fig:nicmos) supports this decision, but the best method of extraction likely lies between these two approaches. We compared the results of the methods as a sanity check; the change in aperture approximately acts like a scale factor to the calculated values and does not ultimately change our interpretation of the results. We also performed similar photometry using the unconvolved 22 GHz maps to set the contours (Figure [4](#fig:nicmos) right) because of the data reduction concerns in the 33 GHz data. The extracted flux density using the 22 GHz contours have a factor 2 difference for Knots 2 and 4a; the other sources are consistent within the errors. The final interpretation remains unchanged, so we retain the use of the 33 GHz contours in the subsequent analysis. We make note of this approach in latter sections when appropriate to remind the reader that photometry of extended sources is an art.

Regardless of the method used, we place an annulus around the source with an inner and outer radii of 1.5 and 2 times the size of the source for the background estimate. The exception is Knot 4b, for which we used an annulus with an inner and outer radii of 2 and 3 times the size of the source to not include the nearby bright, compact feature in the background subtraction. Table [\[tab:fluxcontour\]](#tab:fluxcontour) gives the background subtracted flux density of the sources using the half light contour approach.

## Remarks on Photometry

Robust photometry of extended sources is challenging, particularly in crowded fields, but it is crucial to recover low surface brightness features to fully characterize the extended sources. We investigated two additional methods of source identification and source extraction beyond what we have discussed above. In addition to the contour method, we used the CASA task imfit to extract sources from manually drawn polygonal regions. We also utilized an automated source identification program in the Python package *Photoutils*[^6] v0.7.2 (cite: Bradley:2019) to identify sources. The Photoutils $detect\_sources$ module detects both point-like and extended sources and then deblends overlapping sources with the $deblend\_sources$ module. The output from the $detect\_sources$ module was then used as initial guesses for a 2D Gaussian fitting routine to extract the best fit 2D Gaussian model for the source at each frequency.

The extraction of extended sources is complicated and particularly sensitive to the size of aperture used, regardless of the method. Accounting for the extended emission and disentangling crowded fields is difficult to achieve without some level of subjectivity. We compared the results of these routines, and we determined that the extraction based on a contour level was the least dependent on user input, once the initial level was specified. This method best mitigated the subjectivity in the uncertainties inherent to extracting extended structures.

# Results and Discussion

## Spectral Energy Distributions from 0.9 mm to 6 cm

UD H ii regions at radio wavelengths are described by a thermal model with a turnover frequency $\gtrsim$ 5 GHz (cite: Wood:1989; Johnson:2003), but the presence of SNRs in the vicinity may introduce a non-thermal component. For completeness, we allow for this possibility by including a non-thermal component given that low-level non-thermal emission could be present. The ALMA data will probe the dust emission associated with the sources, so we include a dust component as well to disentangle the non-thermal, thermal, and dust emission, as only the thermal emission will provide an estimate of the rate of ionizing photons and thus the stellar content of the sources. *A priori*, we expect each component to follow a power law. The free-free emission is likely optically thin with a spectral index of $\alpha_{ff}$ = –0.1 above 5 GHz (cite: Allen:1998; Kobulnicky:1999). We adopt an optically thin dust component of $\alpha_{dust}$ = 4 (cite: Scoville:2014). SNRs can have $\alpha_{nth} \lesssim$ –0.5 or steeper, depending on the age of SNR (cite: Weiler:1986; Bell:2011; Dubner:2015). We compared the models with $\alpha_{nth}$ = –0.7, which is a typical synchrotron spectral index, and $\alpha_{nth}$ = –0.5 and found that the reduced chi-squared, $\chi_{\nu}^2$, of $\alpha_{nth}$ = –0.7 models are slightly better (i.e., closer to 1) than the models with –0.5, thus we only show the results of $\alpha_{nth}$ = –0.7 in the sections below. The exception is Knot 3; for both the 2 and 3 component models, $\alpha_{nth}$ = –0.5 is a better fit to the data.

We fix the spectral indices to the values listed above, and the model describing the 3 components is $$\begin{equation}
 \log{} S_{model} = \log{ (S_{0,nth}\;\nu^{\alpha_{nth}} +S_{0,ff}\; \nu^{\alpha_{ff}}+S_{0,dust}\;\nu^{\alpha_{dust}}  )}, 
 \label{eq:SED}
 
\end{equation}$$ where the subscripts *nth*, $ff$, and $dust$ denote non-thermal, free-free, and dust, respectively. We perform a $\chi^2$ minimization for the three free parameters $S_{0,nth}$, $S_{0,ff}$, and $S_{0,dust}$. Table [\[tab:chicontour\]](#tab:chicontour) gives the fit parameters and $\chi_{\nu}^2$ of the models, and the left column of Figures [5](#fig:contour1) and [6](#fig:contour2) shows the SEDs with the best fit parameters for the 3 component model from Table [\[tab:chicontour\]](#tab:chicontour).

Due to the short lifespans of UD H ii regions, we do not expect even the most massive of stars associated with the UD H ii region to have undergone a supernova event yet. A two component fit, with just free-free and dust emission, may be more appropriate than one that includes a non-thermal one. Equation ([\[eq:SED\]](#eq:SED)) is easily modified for just two terms to model this. Table [\[tab:chicontour\]](#tab:chicontour) also gives the fit parameters for the 2 component model, and the right column of Figures [5](#fig:contour1) and [6](#fig:contour2) shows the corresponding SED plots.

There are two important notes about the SED models. First, the 33 GHz flux density was excluded from both the two and three component models as it is a lower limit. Second, the 5 and 15 GHz flux densities and errors were modified for the SED models to account for the calibration discrepancies between the data in this study and that of AK0400 (see discussion in Section [\[sec:photom\]](#sec:photom)). Because the original flux densities reported in (cite: Johnson:2003) employed different aperture sizes than ours here and our 3$\times$ higher angular resolution maps identify multiple components to some sources, we cannot simply include the flux densities from (cite: Johnson:2003) for these sources into the SED models. Instead, we compared the flux densities between the AK0400 maps and ours, when convolved to a common beam, to implement a suitable scaling factor to apply to our flux densities. At 5 GHz, our maps have flux densities $\sim$2$\times$ higher than the AK0400 maps, and at 15 GHz, the 16B-076 data have flux densities $\sim$1.4$\times$ lower than the AK0400 data. The modified flux density at 5 GHz is the midpoint between the flux density in Table [\[tab:fluxcontour\]](#tab:fluxcontour) and half that value, and the error is the distance between the midpoint and the 5 GHz flux density. Similarly, the modified flux density at 15 GHz is the midpoint between the flux density in Table [\[tab:fluxcontour\]](#tab:fluxcontour) at 15 GHz and 1.4$\times$ that value; the errors are the distance between those two values. By modifying the data for the SED models in this way, we can incorporate the discrepancies between the two data sets.

P1cmP1cmP1cmP1cmP1cmP1cmP1.5cmP1cmP2cm & & S$_{0,nth}$ & & S$_{0,ff}$ & & S$_{0,dust}$ & & No. of\
& & (mJy) & & (mJy) & & (mJy) & & Components\
& -0.7 & 0.01 & -0.1 & 0.35 & 4 & 1.2e-11 & 2.3 & 3\
&...& ...& -0.1 & 0.35 & 4 & 1.2e-11 & 1.8 & 2\
& -0.7 & 0.27 & -0.1 & 0.29 & 4 & 1.4e-11 & 3.9 & 3\
&...& ...& -0.1 & 0.34 & 4 & 1.2e-11 & 2.2 & 2\
& -0.7 & 0.45 & -0.1 & 0.58 & 4 & 3.2e-11 & 5.2 & 3\
&...& ...& -0.1 & 0.66 & 4 & 2.7e-11 & 3.1 & 2\

& -0.5 & 1.23 & -0.1 & 0.0 & 4 & 3.8e-12 & 0.9 & 3\
& -0.5 & 1.22 &...& ...& 4 & 3.3e-12 & 0.7 & 2\
& -0.7 & 1.59 & -0.1 & 0.74 & 4 & 2.1e-11 & 2.0 & 3\
&...& ...& -0.1 & 0.88 & 4 & 8.5e-12 & 1.3 & 2\
& -0.7 & 0.85 & -0.1 & 0.86 & 4 & 1.2e-11 & 1.1 & 3\
&...& ...& -0.1 & 1.01 & 4 & 5.6e-12 & 0.8 & 2\
& -0.7 & 1.05 & -0.1 & 0.56 & 4 & 1.8e-11 & 2.3 & 3\
&...& ...& -0.1 & 0.74 & 4 & 9.9e-12 & 1.4 & 2\

(cite: Johnson:2003) fit a purely thermal component with a turnover at $\gtrsim$ 5 GHz for all of the radio knots except Knot 3, which hosts the AGN. As noted in Section [\[sec:photom\]](#sec:photom), there are inconsistencies between the flux calibrations between the AJ314 program and the one used in their study, so we have set the uncertainties at 5 GHz accordingly to reflect this discrepancy. With our modified (larger) uncertainties at 5 and 15 GHz, nearly all of these knots could be consistent with a turnover $\gtrsim$ 5 GHz. We have not modeled it because the 5 GHz data from AJ314 without this modification of the uncertainties are not consistent with such a turnover. Upon first inspection of the unmodified 5 GHz flux densities, it appeared as if a non-thermal component would be necessary to characterize the SED; however, we cannot be sure the AJ314 calibration is accurate. New observations at 5 GHz and S-band (2 – 4 GHz) would clarify if there is a turnover consistent with typical UD H ii region SEDs or whether a non-thermal component is indeed real. If these are truly UD H ii regions, we would not expect a significant non-thermal component. Nevertheless, here we consider possible explanations for a non-thermal component in the SED model.

1.  If stars within a UD H ii region are not formed quasi-instantaneously, there could be more evolved stars that have undergone a supernova event within them that are not taken into account in a simple formation scenario.

2.  While natal SSCs are not expected to yet host supernova events given their extremely young ages, evolved stars in nearby SSCs may have done so. A small non-thermal component may be residual, non-subtracted background from these more evolved SSCs in the vicinity. He 2-10 has a number of optically identified adolescent SSCs, which could be providing the contaminating non-thermal emission, e.g., Knot 4a, which is known to host a SNR (cite: Reines:2012).

3.  Young stellar objects can be associated with jets, which could be sources of non-thermal emission (cite: Garay:2003; Purser:2016). (cite: Purser:2016) find 22 ionized jets and jet candidates associated with massive star formation. They suggest that a jet may persist for a short time after an H ii region has formed because they associate some of the ionized jets in their sample with hyper compact, ultra compact, and normal H ii regions. (cite: Cecere:2016) report that there is non-negligible synchrotron emission associated with proto-stellar jets in their models. If there is a population of young stellar objects with jets in these UD H ii regions, this may be a source of non-thermal emission.

The 2 and 3 component SED models have different degrees of freedom, so we cannot directly compare the $\chi_{\nu}^2$ values to determine which model is favored. For this work, we visually inspect the models and leverage the available knowledge at other wavelengths to determine which model and interpretation is more appropriate for each knot. A visual comparison of the two and three component models suggests that Knots 1a, 1b, 2, and 5 may be consistent with only thermal+dust components. At shorter wavelengths, (cite: Cabanac:2005) do not find optical sources associated with these knots, and from CO(2-1) observations, (cite: Johnson:2018) report that the knots are associated with molecular material. Given these results, we believe that Knots 1a, 1b, 2, and 5 should retain the classification of UD H ii regions, agreeing with the conclusions of (cite: Johnson:2003) and (cite: Cabanac:2005). For these sources, we use the 2 component SED model, i.e., one without a non-thermal component, in the remaining sections of this work.

Knot 3, which hosts the central AGN of He 2-10, is not the primary focus of this work because it is not a SSC. For completeness, we have included it in the SED models because it does serve as a sanity check and might be useful to other research programs. Knot 3 does have a stronger non-thermal component than the other knots, which is to be expected. The 3 component SED models are not well constrained, likely because of the adjustment to the 5 GHz flux density and uncertainties. The 2 component fit has non-thermal+dust components, though we did fit thermal+dust component for completeness only to discarded it given the nature of the source and the poor fit.

Knots 4a and 4b originally were identified as one source, Knot 4, in (cite: Kobulnicky:1999). Knot 4a and 4b are associated with strong optical and IR emission in the maps of (cite: Cabanac:2005) but is depleted in CO(2-1) compared to the other regions (cite: Johnson:2018). These knots may be a combination of normal H ii regions and SNRs (point 1 above), as suggested by (cite: Cabanac:2005). Alternatively, there are bright and optically visible SSCs located near Knots 4a and 4b, and VLBI observations from (cite: Reines:2012) report a SNR associated with the optical SSC near to Knot 4a, which could be contaminating the photometry results (point 2). We cannot discriminate between these two scenarios without first resolving the calibration concerns at 5, 15, and 33 GHz and without higher resolution and higher sensitivity maps at longer wavelengths to fully characterize the SED. Similarly, we do not have ancillary data to discern if proto-stellar jets (point 3) are contributing to the non-thermal emission. In the absence of lower frequency observations to rule out a turnover in the spectral index, higher resolution observations on scales of 1 – 2 pc to further disentangle these crowded regions, or observations to probe the kinematics of these regions, we leave this question for future research. For this analysis, we use the 3 component SED and retain the classification from (cite: Cabanac:2005) for these knots.

Table [\[tab:finalmodel\]](#tab:finalmodel) summarizes these results and gives the modeled, thermal flux density (S$_{ff,fit}$) at 33 GHz from the SED model. The uncertainties are propagated from the fit. Finally, we note that a more robust statistical analysis and SED model would ultimately bring clarity to these classifications; however, given the legitimate concerns about the 5, 15, and 33 GHz calibrations, we believe that such an analysis is not warranted at this time, and we leave it to future work when a multiwavelength observing campaign with better matched synthesized beams can be undertaken.

P1cmP5cmP4cmP2cmP2cm &SED & & S$_{ff,fit}$ & S$_{dust,fit}$\
& Components & & (mJy) & (mJy)\

1a & thermal+dust & UD H ii region & 0.25 $\pm$ 0.02 & 0.15 $\pm$ 0.08\
1b & thermal+dust & UD H ii region & 0.24 $\pm$ 0.02 & 0.16 $\pm$ 0.07\
2 & thermal+dust & UD H ii region & 0.47 $\pm$ 0.04 & 0.37 $\pm$ 0.14\
4a & non-thermal+thermal+dust & H ii region + SNR & 0.52 $\pm$ 0.11 & 0.27 $\pm$ 0.18\
4b & non-thermal+thermal+dust& H ii region + SNR & 0.61 $\pm$ 0.11 & 0.15 $\pm$ 0.14\
5 & thermal+dust & UD H ii region & 0.52 $\pm$ 0.04 & 0.13 $\pm$ 0.12\

## Production Rate of Ionizing Photons and Mass of the Clusters 

If there is a purely thermal estimate of the flux density, we can determine the stellar mass of the embedded clusters hosted in the radio knots. We first estimate the production rate of Lyman continuum photons, Q$_{Lyc}$, with the specific thermal radio luminosity, $L_{therm} = 4\pi D^2 \times S_{\nu}$, where D is the distance in cm and S$_{\nu}$ is the flux density in erg s$^{-1}$ cm$^{-2}$ Hz$^{-1}$. Q$_{Lyc}$ is then $$\begin{equation}
    Q_{Lyc} \geq 6.3 \times 10^{52} \left(\frac{T_e}{10^4 \textrm{ K}}\right)^{-0.45}\left(\frac{\nu}{\textrm{GHz}}\right)^{0.1}\left(\frac{L_{therm}}{10^{27}\textrm{ ergs s$^{-1}$ Hz$^{-1}$}}\right) \textrm{ s}^{-1},
    \label{eq:qlyman}
\end{equation}$$ where T$_e$ is the electron temperature in Kelvin and $\nu$ is frequency in GHz (cite: Condon:1992; Johnson:2003). We adopt 10$^4$ K as the typical temperature of an H ii region. Given the concerns about the 33 GHz data from the 15B-197 program, we utilize the thermal flux density modeled from the SED fit listed in Table [\[tab:finalmodel\]](#tab:finalmodel) to estimate Q$_{Lyc}$.

We estimate the stellar mass using Starburst99 models (cite: Leitherer:1999; Vazquez:2005; Leitherer:2010; Leitherer:2014). The 2014 update to the Starburst99[^7] package includes synthesizing stellar populations with rotating stars, which are more luminous than non-rotating stars. Additionally, we can select the metallicity, the choice of initial mass function (IMF), and the mass cutoffs to estimate Q$_{Lyc}$. In the Starburst99 package, we synthesized Q$_{Lyc}$ values for Z = 0.014 and Z = 0.008. This is motivated by the results of (cite: Cresci:2017), who mapped the metallicity of He 2-10 from their MUSE (Multi Unit Spectroscopic Explorer) observations. They report a range of metallicities (12 + log(O/H) = 8.25 – 8.55) across He 2-10, which is in agreement with other estimates that averaged over the galaxy (e.g., 12 + log(O/H) = 8.55 $\pm$ 0.02; Z $\sim$ 0.0098; (cite: Esteban:2014)). These two cases represent limits in Q$_{Lyc}$ for natal clusters in He 2-10. We used a Kroupa IMF (cite: Kroupa:2001) with two components (1.3 and 2.3) and with mass cutoffs of 0.1, 0.5, 100 $\textrm{M}_{\odot}$ as well as a Salpeter IMF (cite: Salpeter:1955) with mass cutoffs of 1 and 100 $\textrm{M}_{\odot}$. For a 10$^6$ $\textrm{M}_{\odot}$ cluster that is less than 1 Myr old, the values of Q$_{Lyc}$ vary less than a factor of 2 for the choice of the metallicity, IMF, and rotation. We select a representative value of Q$_{Lyc}$ $\approx$ 5.3 $\times$10$^{52}$ photons s$^{-1}$ for a 10$^6$ $\textrm{M}_{\odot}$ cluster, with a standard deviation of 1.2 $\times$10$^{52}$ photons s$^{-1}$ which we treat as a systematic uncertainty in our analysis. In Table 7, columns 2 and 3 list Q$_{Lyc,fit}$ and the cluster mass, M$_{fit}$. The uncertainties are propagated through the equations. Finally, we note that these Q$_{Lyc}$ estimates, and thus the mass estimates, are lower limits because the ionizing photons from the UD H ii regions can be absorbed by dust.

The Pa$\alpha$ flux density also provides a lower limit on Q$_{Lyc}$, as it traces ionized gas but can suffer from extinction in extremely dense and massive dust clouds. The thermal flux density can be estimated from the line flux following Equation (3) of (cite: Condon:1992) $$\begin{equation}
\frac{S_{T}}{\textrm{mJy}} \approx  \left(\frac{1}{0.28}\right) \left(\frac{\textrm{F(H}\beta)}{10^{-12} \textrm{ erg/s/cm$^2$}} \right) \left(\frac{T_e}{10^4 \textrm{ K}}\right)^{0.52}\left(\frac{\nu}{\textrm{GHz}}\right)^{-0.1},
\label{eq:lineflux}
\end{equation}$$ where F(H$\beta$) is the H$\beta$ line flux. From photometry, we estimate the Pa$\alpha$ flux density for each source. The flux density is multiplied by the FWHM of the filter (Table [2](#tab:alldataprop)) to calculate the Pa$\alpha$ line flux, F(Pa$\alpha$). The ratio of the Pa$\alpha$ line flux to the H$\beta$ line flux at T$_e$ = 10$^4$ K is $$\begin{equation}
\frac{\textrm{F(Pa}\alpha)}{\textrm{F(H}\beta)}  = 0.317,
\label{eq:ratio}
\end{equation}$$ for line intensities from Table 4.4 of (cite: Osterbrock:1989), assuming Case B and n$_e$ = 10$^6$ cm$^{-3}$. With Equations ([\[eq:qlyman\]](#eq:qlyman)) – ([\[eq:ratio\]](#eq:ratio)), we can estimate Q$_{Lyc}$ at 33 GHz from F(Pa$\alpha$), assuming an electron temperature of 10$^4$ K and optically thin gas. Column 4 of Table [\[tab:propertiescontour\]](#tab:propertiescontour) lists the calculated values of Q$_{Lyc,\textrm{Pa}\alpha}$ from the Pa$\alpha$ flux densities in Table [\[tab:fluxcontour\]](#tab:fluxcontour). For any embedded cluster or line of sight that is heavily extincted, the mass calculated from the thermal radio flux density should be higher than the mass from the Pa$\alpha$ flux density. Any discrepancy between the values inferred from radio and Pa$\alpha$ can be used to constrain either the extinction of Pa$\alpha$ and/or excess emission due to a non-thermal component in the radio flux. Q$_{Lyc,fit}$ is higher than Q$_{Lyc,\textrm{Pa}\alpha}$ for the radio knots, indicating that the Pa$\alpha$ map is affected by extinction towards these lines of sight.

As discussed in Section [\[sec:photnicmos\]](#sec:photnicmos), the extracted flux density is sensitive to the choice of aperture and treatment of the background subtraction. The region near Knots 4a and 4b has optically visible sources as well as bright features in the Pa$\alpha$ map that are not associated with the peaks in the radio emission (Figure [4](#fig:nicmos)). Particularly for Knot 4b, an aperture of equivalent size to the ones used to extract the radio flux densities will include the brightest feature in the Pa$\alpha$ map. However, this feature is not coincident with the peak in the 33 GHz map and is coincident with optical sources, as seen in the H$\alpha$ and other HST maps in Figure 3 of (cite: Cabanac:2005). Inclusion of this bright feature returns a negative extinction value for Knot 4b, which is unphysical. Because the 33 GHz data were of dubious quality, we rely on the SED model to provide the thermal flux density value for our radio mass estimate. Given the 22 GHz and 113 GHz flux densities, we believe the modeled thermal flux density to be reasonable. However, it is still possible that the SED model and extracted flux densities for this source may be suspect. If the bright feature near Knot 4b is associated with the radio source, then an underestimated thermal flux might explain this discrepancy.

P0.8cmP2cmP2cmP2cmP1cm

& Q$_{Lyc,fit}\tnote{a}$ & M$_{fit}$ & Q$_{Lyc,\textrm{Pa}\alpha}$ &\
& $\times$10$^{51}$ & $\times$10$^{5}$ & $\times$10$^{51}$ &\
& (photons s$^{-1})$ & ($\textrm{M}_{\odot}$) & (photons s$^{-1}$) &\

1a & 2.12 $\pm$ 0.18 & 0.40 $\pm$ 0.10 & 0.34 $\pm$ 0.26 & 14\
1b & 2.10 $\pm$ 0.18 & 0.40 $\pm$ 0.10 & 1.17 $\pm$ 0.24 & 4.5\
2 & 4.05 $\pm$ 0.34 & 0.77 $\pm$ 0.19 & 2.67 $\pm$ 0.27 & 3.2\
4a & 4.51 $\pm$ 0.92 & 0.86 $\pm$ 0.26 & 3.41 $\pm$ 0.28 & 2.2\
4b & 5.25 $\pm$ 0.95 & 1.00 $\pm$ 0.29 & 3.38 $\pm$ 0.27 & 3.4\
5 & 4.51 $\pm$ 0.35 & 0.86 $\pm$ 0.21 & 0.60 $\pm$ 0.23 & 16\

Calculated using the modeled thermal flux density at 33 GHz (S$_{ff,fit}$) in Table [\[tab:finalmodel\]](#tab:finalmodel).

Calculated using the Pa$\alpha$ flux density in Table [\[tab:fluxcontour\]](#tab:fluxcontour).

## Extinction

The Pa$\alpha$ map may be affected by extinction due to extremely dense and massive dust clouds. We can estimate the extinction, A$_V$, by comparing the radio and Pa$\alpha$ results. (cite: Indebetouw:2005) present an analysis of the wavelength dependence of interstellar extinction between 1.25 – 8.0 $\mu$m and describe the behavior of $A_{\lambda}/A_K$ in this wavelength range, where A$_K$ is the infrared $K$ band (2.2 $\mu$m) extinction. From Equation (4) of (cite: Indebetouw:2005), we expect A$_{\textrm{Pa}\alpha}$/A$_K$ $\sim$1.24 and for R$_V$ = 3.1, A$_V$/A$_K$ $\sim$8.8 (cite: Cardelli:1989). If we assume the radio Q$_{Lyc,fit}$ value is purely thermal and any decrement in Q$_{Lyc}$ between the radio and Pa$\alpha$ values is due to extinction, then $$\begin{equation}
\textrm{A}_V \approx -17.7 \log\left(\frac{\textrm{Q}_{Lyc, Pa\alpha}}{\textrm{Q}_{Lyc, fit}}\right).
\end{equation}$$ The last column of Table [\[tab:propertiescontour\]](#tab:propertiescontour) gives the estimates of the extinction values towards the radio knots, which is between 2.2 – 16. (cite: Cabanac:2005) find an extinction of A$_V$ = 10.5 from the ratio of Br$\gamma$/Br10 using the line fluxes from (cite: Vanzi:1997). The observations of (cite: Vanzi:1997) were long slit observations with the 23 m Bok telescope of Steward Observatory with an aperture of 2.4$''$ $\times$ 15.6$''$. Our estimates of the extinction are more localized but the range is consistent with the extinction reported by (cite: Cabanac:2005). Given that both the Pa$\alpha$ and radio flux densities are lower limits, the extinction values we derive are also lower limits and the actual values could be higher. We discuss the variation in the extinction between the radio knots in Section [\[sec:dis\]](#sec:dis).

## Submillimeter Emission, Dust Mass, and Total Mass

The 340 GHz flux density can provide a probe of the dust mass associated with the radio knots. Star forming galaxies can have dust temperatures between 25 – 40 K but active galaxies can have higher T$_d$ (cite: Scoville:2014). (cite: Gorski:2017) report a gas temperature near forming SSCs in NGC 253 of 130 K. In the absence of short wavelength observations of similar spatial resolution to the radio data to determine the dust tempertature, we adopt a range of dust temperatures of T$_d$ = (25, 40, 100) K, which are similar to the values discussed in (cite: Vacca:2002) for cocoons of dust enveloping SSCs in He 2-10. Though, (cite: Vacca:2002) note that a single blackbody is a not a good representation of the dust SED between 10.8 – 100 $\mu$m. From the SED models, we can estimate the flux density due to the dust emission, S$_{dust,fit}$, that is not contaminated by free-free or non-thermal emission. Column 5 of Table [\[tab:finalmodel\]](#tab:finalmodel) lists these values. Comparing the modeled dust emission, S$_{dust,fit}$ to the measured flux density at 340 GHz, we estimate that 48 – 68$\%$ of the 340 GHz flux density is due to free-free emission. This agrees with other estimates from (cite: Hirashita:2013), who extrapolated the (cite: Johnson:2003) 5 GHz flux density to 340 GHz and estimated from their 340 GHz observations that 45 – 64$\%$ of the 340 GHz emission was due to free-free emission. With S$_{dust,fit}$, we calculate the specific luminosity, L$_{\nu}$, and then the dust mass, M$_d$, is

$$\begin{equation}
\textrm{M}_d = \frac{\textrm{L}_{\nu}}{4\pi\,\kappa_{\nu}\,\textrm{B}_{\nu}(\textrm{T}_d)},
\end{equation}$$ where the value of B$_{\nu}$(T$_{d}$) is in erg s$^{-1}$ cm$^{-2}$ Hz$^{-1}$ from the Planck function at 340 GHz. The absorption coefficient of dust is $$\kappa_{\nu} = \kappa_o \left(\frac{\nu}{\nu_o}\right)^{\beta},$$ where $\nu$ = $\nu_o$ in this case and $\beta = \alpha_{dust} - 2$. We adopt $\kappa_o$ = 1.3 cm$^2$ g$^{-1}$ at $\nu_o$ = 340 GHz (cite: Whitcomb:1981; Hildebrand:1983) but note that the uncertainty can be as large as a factor of 2. Table [\[tab:dustmass\]](#tab:dustmass) gives the calculated dust mass for T$_d$ = (25, 40, 100) K. Adopting a dust-to-gas ratio of 1:100 (cite: Wilson:2008) and assuming M$_{fit}$ is the stellar contribution to the total mass, the knots have total masses between 0.5 – 1.1 $\times$ 10$^5$ $\textrm{M}_{\odot}$ for T$_d$ = 100 K. For colder dust, the total mass estimate will increase slightly.

P1cmP2cmP2cmP2cm

&\
& T$_d$ = 25 K & T$_d$ = 40 K & T$_d$ = 100 K\

1a & 0.7 & 0.4 & 0.1\
1b & 0.7 & 0.4 & 0.1\
2 & 1.6 & 0.9 & 0.3\
4a & 1.2 & 0.7 & 0.2\
4b & 0.7 & 0.4 & 0.1\
5 & 0.6 & 0.3 & 0.1\

## Star Formation Efficiency 

A broader interest in SSCs is as a local analog to globular clusters. SSCs must remain bound in order to evolve into a globular cluster, and the star formation efficiency (SFE) of the cluster is one measure of the cluster’s ability to remain bound. If most of the cluster’s mass is in the form of gas, then when the gas is expelled from the cluster through stellar feedback mechanisms, the cluster may no longer remain bound. The threshold to remain bound, as traced by the SFE, has varied in the literature over the years. One conservative estimate is SFE $>$ 90$\%$ (cite: Hills:1980), but (cite: Baumgardt:2007) and (cite: Pelupessy:2012) suggest that it could be as low as 5 – 10$\%$ if the timescale over which the gas is removed is long. Alternatively, (cite: Geyer:2001) suggest SFE $>$ 50$\%$ in order to form bound clusters. (cite: Matthews:2018) provide a review of the SFE in this context and in the merging environment of the Antennae galaxies, which also host SSCs. In the Antennae galaxies, they found few clusters with SFE $>$ 20$\%$ but note that their analysis was not sensitive to embedded clusters.

Following the treatment of the SFE from (cite: Matthews:2018), the instantaneous mass ratio is $$\begin{equation}
\textrm{IMR(t)} = \left(1+\frac{M_{*}}{M_{gas}}\right)^{-1},
\end{equation}$$ where M$_{*}$ is the stellar mass and M$_{gas}$ is the gas mass. The IMR is a function of time over the evolution of the cluster. When the cluster is still forming stars, the IMR $<$ 1, and when star formation ceases but the natal molecular cloud is not yet disrupted, the IMR approaches unity and is then equal to the SFE. With S$_{ff,fit}$ as an estimate for M$_*$ and S$_{dust,fit}$ with a 1:100 dust-to-gas ratio for M$_{gas}$, we can estimate the IMR for the radio knots. For T$_d$ = 100 K, the IMR is between $\sim$71 – 88$\%$ for the radio knots; for colder dust (25 K), the IMR is $\sim$32 – 60$\%$. For a larger dust-to-gas ratio, the IMR will decrease; for example, a dust-to-gas ratio of 1:300 yields IMR $\sim$45 – 72$\%$ for T$_d$ = 100 K and IMR $\sim$ 14 – 33$\%$ for T$_d$ = 25 K. For warm dust and a 1:100 dust-to-gas ratio, high IMR suggests that the natal SSCs in He 2-10 could potentially remain bound even after the gas is dispersed through stellar feedback processes. If the dust is cold or the dust-to-gas ratio is larger however, the clusters may not remain bound.

## Discussion

From the analysis of the SEDs for the radio knots, we have presented estimates of the production rate of ionizing photons, the extinction towards the radio knots from the Pa$\alpha$ and thermal radio emission, and the emission associated with dust, as traced by the 340 GHz data. The bottom three panels of Figure [7](#fig:normpar) display these parameters with respect to their spatial distribution across He 2-10; the top panels show a HST/WFPC2 F814W raster map with 22[^8] and 340 GHz continuum in black and red contours, respectively, and the white contours show ([7](#fig:normpar)a) SMA $^{12}$CO(2-1), ([7](#fig:normpar)b) ALMA HCO$^+$(1-0), and ([7](#fig:normpar)c) ALMA HCN(1-0) velocity-integrated intensity (moment 0) maps from (cite: Johnson:2018). With these results, we discuss here general trends as traced by the radio knots in He 2-10.

The western and eastern regions of He 2-10, as traced by Knots 1a and 5 have higher A$_V$ values but are not submm bright. In the absence of observations at shorter wavelengths to determine the dust temperature, the simple assumption is that T$_d$ is the same for each knot; however, the geometry of the dust with respect to the cluster impacts the observed submm brightness and A$_V$. Given the low submm emission but higher A$_V$ values, the dust could be cold and far from these clusters, perhaps in form of a foreground dust screen; though, the dust could also be much hotter and peaking at shorter wavelengths. From their HNC(1-0) and HCN(1-0) observations of the natal SSCs, (cite: Johnson:2018) report that the molecular material near Knots 1a, 1b, and 2 are the warmest in the region while the region near Knot 5 is cooler. If the dust and molecular material is cospatial, then the observations and analysis presented here are not sensitive to the peak of the dust emission near Knots 1a, 1b, and 2. The closely spaced lines of sight to Knots 1a, 1b, and 2 and the variation in A$_V$ between them suggests that the dust distribution may be patchy in this region as well. The knots are also associated with peaks in the CO(2-1) and HCN(1-0) emission. CO is a “generic” molecular gas tracer; it is easily photodissociated by young massive stars, requiring only 11.09 eV to do so. HCN(1-0), however, is a cold, dense gas tracer with a critical density of $n_{\textrm{crit}}$ = 1.7 $\times$ 10$^5$ cm$^{-3}$ at 50 K for optically thin gas (cite: Shirley:2015). These clusters appear to be consistent with being embedded and young, as previously reported by (cite: Johnson:2003) and (cite: Cabanac:2005), and Knot 5 may be the youngest and most embedded of the group.

Knots 4a and 4b are bright in the submm and have the lowest A$_V$ values. The dust is unlikely to be in a foreground screen but instead close to the cluster and warm. The submm emission closely follows the morphology of the thermal emission, indicating that the submm emission is not a spatially extended feature of this region. The evolved SSCs in the vicinity of these knots complicates the interpretation of the region however. We included a non-thermal component in the SED models for these knots, but this could be due to contamination from the evolved SSCs in the vicinity. The contaminating non-thermal emission would lower the estimated thermal flux, which in turn decreases A$_V$. Because of the lack of optical counterparts coincident with the radio emission, these knots appear to be consistent with being embedded clusters. However, they are not associated with peaks in the CO(2-1) and HCN(1-0) maps, suggesting that the knots are not as embedded, or as young, as Knots 1a, 1b, and 5. Alternatively, these knots could be of a similar age if the more evolved SSCs in the vicinity were almost entirely responsible for destroying the natal material in this region.

The central region of He 2-10, as traced by Knots 4a and 4b and the optical clusters, appears to be in a distinct evolutionary state compared to the most eastern and western sides, where the latter two may host younger, more embedded clusters. Previous studies have noted an age gradient across He 2-10 (e.g., (cite: Johnson:2000), (cite: Cabanac:2005), (cite: Chandar:2003)). Knot 4a[^9] may have an age $>$ 6 Myr (cite: Johnson:2003; Cabanac:2005), though (cite: Chandar:2003) suggest that the optical cluster near Knot 4a may be $<$ 6 Myr because of a P Cygni profile associated with that cluster, which puts a upper limit on the age. Knots 1 (as identified in the lower resolution maps), 2, and 5 are younger by comparison, with ages $\leq$ 5 Myr (cite: Cabanac:2005).

(cite: Johnson:2018) report HCN(1-0), HCO$^+$(1-0), and CO(2-1) line strengths for nineteen 0.8$''$ apertures, chosen to probe peaks in their ALMA and SMA maps of He 2-10. The HCO$^+$(1-0) line traces warmer, moderately dense gas ($n_{\textrm{crit}}$ = 2.9 $\times$ 10$^4$ cm$^{-3}$; (cite: Shirley:2015)) and is commonly associated with photodissociation regions. HCO$^+$ does not seem to vary across the radio knots, unlike the CO and HCN maps. He 2-10 appears to have moderately dense, warm gas present in the central region, while the colder, denser gas traced by HCN(1-0) is more patchy and peaks preferentially on the edges of the central region. From a principle component analysis of these lines and others for clouds in He 2-10, (cite: Johnson:2018) suggest that the ratios of HCN/HCO$^+$ and HCO$^+$/CO are correlated with the evolutionary state of the cluster. In Figure [8](#fig:molratios), we show an adaptation of Figure 13 from (cite: Johnson:2018) and Figure 13 of (cite: Finn:2019) to show this trend. The emerging clusters are at the bottom right (higher HCO$^+$/CO, low HCN/HCO$^+$) and as the HCO$^+$/CO ratio decreases and HCN/HCO$^+$ increases, the clusters are thought to be more embedded and younger. At the upper left of the plot are the precursor molecular clouds that have the potential to form SSCs but have not yet begun doing so. An example of such a cloud is the Firecracker in the Antennae galaxies (cite: Finn:2019).

![](f7.pdf)

In Figure [8](#fig:molratios), we highlight the apertures from (cite: Johnson:2018) that are associated with the radio knots. Knots 4a and 4b appear in the bottom right and Knot 5 is to the left of them, which is consistent with our interpretation of the degree to which these knots are embedded. With the resolution of the HCN(1-0), HCO$^+$(1-0), and CO(2-1) maps ($\sim$1.7$''$, $\sim$74 pc), Knots 1a, 1b, and 2 are in a single beam and we cannot differentiate physical conditions between the knots in the ALMA maps. From the available continuum data, Knot 1a is similar to Knot 5, so we expect that in higher resolution data, this knot would be closer to Knot 5 in this figure. The curiosity is Knot 2, however, in that the A$_V$ is low and it is submm bright like Knots 4a and 4b; however, it is associated with peaks in the HCN(1-0) and CO(2-1) maps, suggesting that it is embedded like Knots 1a, 1b, and 5. Higher resolution observations of the dense gas tracers will be able to disentangle the characteristics of these knots further. Generally, our analysis of the non-thermal, thermal, and dust emission presented here supports the empirical correlation between the molecular ratios of HCN/HCO$^+$ and HCO$^+$/CO and the evolutionary state of the cluster as suggested by (cite: Johnson:2018).

## Concluding Remarks

With higher resolution data and additional wavelength coverage, we are beginning to move away from the early simple models of the formation of SSCs. Complexities are emerging, which may include amorphous morphologies, non-instantaneous star formation, etc. As we probe finer spatial scales, we may find smaller H ii regions, corresponding to a cluster formation scenario that is hierarchical and fragmented instead of one that undergoes monolithic collapse. This may present, for example, as a bound cluster composed of UC H ii regions instead of a single diffuse H ii region encompassing the cluster. As future telescopes such as the Next Generation VLA (ngVLA) and the James Space Webb Telescope (JWST) are able to probe smaller spatial scales and provide complementary multiwavelength observations, studies will offer new insights and constraints on star formation theory.

# Summary

We present observations of He 2-10 from 1.87 $\mu$m to 6 cm to constrain the properties of 7 radio knots in the most complete multiwavelength survey on parsec scales to date of He 2-10. Our conclusions are as follows.

- We present maps at 5, 8, 15, 22, 33, 113, 250, and 340 GHz and 1.87 $\mu$m of He 2-10. We discuss photometry results for the radio knots, which were initially identified in (cite: Kobulnicky:1999) and (cite: Johnson:2003). With the higher resolution of these maps compared to previous studies, we extract individual clusters from aggregate complexes as identified at lower resolution. In total, we identify seven knots: Knots 1a, 1b, 2, 3, 4a, 4b, and 5. Knot 3 is known to host the AGN (cite: Reines:2011; Reines:2012; Reines:2016).

- We construct spectral energy distributions from radio to submillimeter wavelengths and model the SED to disentangle the non-thermal, thermal, and dust components. The key figures and table showing these results are Figures [5](#fig:contour1) and [6](#fig:contour2) and Table [\[tab:finalmodel\]](#tab:finalmodel). Knots 1a, 1b, 2, and 5 are consistent with being UD H ii regions, as initially concluded by (cite: Johnson:2003) and (cite: Cabanac:2005). The SEDs for Knots 4a and 4b appear to have a non-negligible non-thermal component. These knots may be a mixture of normal H ii regions and SNRs as suggested by (cite: Cabanac:2005) or the evolved SSCs in the vicinity may be contributing the contaminating non-thermal emission. These knots are not associated with optical counterparts, so the clusters do not appear to have completely emerged yet from their natal material.

- From the SED model, we calculate the rate of ionizing photons from the thermal flux density, which can provide an estimate for the mass of the cluster, and we find stellar masses between 0.4 – 1.0 $\times$ 10$^5$ $\textrm{M}_{\odot}$ for the natal SSCs hosted in the radio knots. The range of masses for the natal SSCs is consistent with estimates of stellar masses for adolescent SSCs in He 2-10 from (cite: Johnson:2000). From the HST/NICMOS F187N observations, the Pa$\alpha$ flux densities for the radio knots provide a lower limit on the ionizing fluxes as well. Pa$\alpha$ can suffer from extinction in extremely dense and massive dust clouds, so we estimate the extinction along the line of sight by comparing the radio and Pa$\alpha$ estimates. We find A$_V$ values between 2.2 – 16 for the radio knots. Table [\[tab:propertiescontour\]](#tab:propertiescontour) lists these values.

- In Section [\[sec:dustmass\]](#sec:dustmass), we estimate the dust content associated with the knots from the SED models to be 0.1 – 0.3 $\times$ 10$^3$ $\textrm{M}_{\odot}$ at 100K. If the dust temperature is cooler, the dust mass estimates will increase. Assuming a dust-to-gas ratio of 1:100 and the stellar mass estimated from the thermal flux density, we find total masses between 0.5 – 1.1 $\times$ 10$^5$ $\textrm{M}_{\odot}$. In Section [\[sec:SFE\]](#sec:SFE), we estimate the instantaneous mass ratio (IMR), which is related to the star formation efficiency, and find a range of 71 – 88$\%$ for the radio knots. For 100 K dust and a 1:100 dust-to-gas ratio, high IMR suggests that the natal SSCs in He 2-10 could potentially remain bound even after the gas is dispersed through stellar feedback processes, perhaps allowing these clusters to evolve into objects similar to globular clusters. If the dust is cold or the dust-to-gas ratio is larger however, the clusters may not remain bound.

- In Section [\[sec:dis\]](#sec:dis), we discuss characteristics of the radio knots based on the results of this study and previous ones to construct a holistic picture of the radio knots in He 2-10. Knots 4a and 4b appear to be still marginally embedded, as they do not have optical counterparts, and the dust near these knots is likely compact and warm. Knots 1a and 5 are characterized by high A$_V$ values but relatively little emission at 340 GHz, suggesting that they are embedded and cold dust may exist in a patchy, foreground screen. Generally, the central region of He 2-10, as traced by Knots 4a and 4b and the optical SSCs, appears to be more evolved than the eastern and western regions. We compare our interpretation to ALMA maps of dense gas tracers such as CO, HCN, and HCO$^+$ in Figures [7](#fig:normpar) and [8](#fig:molratios). Our multiwavelength analysis supports the empirical correlation between these dense gas tracers and the cluster evolution scenario proposed by (cite: Johnson:2018).

# Acknowledgments

This paper makes use of the following ALMA data: ADS/JAO. ALMA$\#$2012.1.00413.S., 2015.1.01569.S, 2016.1.00027.S, and 2016.1.00419.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. AER gratefully acknowledges support for this work provided by NASA through EPSCoR grant number 80NSSC20M0231. This research made use of Photutils, an Astropy package for detection and photometry of astronomical sources (cite: Bradley:2019). The majority of this paper was written during the 2020 lockdown in the workspace of home, so we thank those around us who patiently supported and encouraged us. Finally, we thank the referee of this paper for a helpful and collegial review

VLA, ALMA

natexlab

(ref: Allen:1998) Allen, M. L., & Kronberg, P. P. 1998, ApJ, 502, 218, doi: [`10.1086/305894`](http://doi.org/10.1086/305894)

(ref: Baganoff:2003) Baganoff, F. K., Maeda, Y., Morris, M., et al. 2003, ApJ, 591, 891, doi: [`10.1086/375145`](http://doi.org/10.1086/375145)

(ref: Baumgardt:2007) Baumgardt, H., & Kroupa, P. 2007, MNRAS, 380, 1589, doi: [`10.1111/j.1365-2966.2007.12209.x`](http://doi.org/10.1111/j.1365-2966.2007.12209.x)

(ref: Beck:2018) Beck, S. C., Turner, J. L., & Consiglio, S. M. 2018, ApJ, 867, 165, doi: [`10.3847/1538-4357/aae481`](http://doi.org/10.3847/1538-4357/aae481)

(ref: Bell:2011) Bell, A. R., Schure, K. M., & Reville, B. 2011, MNRAS, 418, 1208, doi: [`10.1111/j.1365-2966.2011.19571.x`](http://doi.org/10.1111/j.1365-2966.2011.19571.x)

(ref: Bradley:2019) Bradley, L., Sipőcz, B., Robitaille, T., et al. 2019, astropy/photutils: v0.6, doi: [`10.5281/zenodo.2533376`](http://doi.org/10.5281/zenodo.2533376)

(ref: Cabanac:2005) Cabanac, R. A., Vanzi, L., & Sauvage, M. 2005, ApJ, 631, 252, doi: [`10.1086/432534`](http://doi.org/10.1086/432534)

(ref: Cardelli:1989) Cardelli, J. A., Clayton, G. C., & Mathis, J. S. 1989, ApJ, 345, 245, doi: [`10.1086/167900`](http://doi.org/10.1086/167900)

(ref: Cecere:2016) Cécere, M., Velázquez, P. F., Araudo, A. T., et al. 2016, ApJ, 816, 64, doi: [`10.3847/0004-637X/816/2/64`](http://doi.org/10.3847/0004-637X/816/2/64)

(ref: Chandar:2003) Chandar, R., Leitherer, C., Tremonti, C., & Calzetti, D. 2003, ApJ, 586, 939, doi: [`10.1086/367956`](http://doi.org/10.1086/367956)

(ref: Condon:1992) Condon, J. J. 1992, ARA&A, 30, 575, doi: [`10.1146/annurev.aa.30.090192.003043`](http://doi.org/10.1146/annurev.aa.30.090192.003043)

(ref: Condon:1997) —. 1997, PASP, 109, 166, doi: [`10.1086/133871`](http://doi.org/10.1086/133871)

(ref: Constantin:2009) Constantin, A., Green, P., Aldcroft, T., et al. 2009, ApJ, 705, 1336, doi: [`10.1088/0004-637X/705/2/1336`](http://doi.org/10.1088/0004-637X/705/2/1336)

(ref: Cresci:2017) Cresci, G., Vanzi, L., Telles, E., et al. 2017, A&A, 604, A101, doi: [`10.1051/0004-6361/201730876`](http://doi.org/10.1051/0004-6361/201730876)

(ref: Davis:2020) Davis, e. in prep, in prep, 1, 1, doi: [`1`](http://doi.org/1)

(ref: Dubner:2015) Dubner, G., & Giacani, E. 2015, A&ARv, 23, 3, doi: [`10.1007/s00159-015-0083-5`](http://doi.org/10.1007/s00159-015-0083-5)

(ref: Esteban:2014) Esteban, C., Garcı́a-Rojas, J., Carigi, L., et al. 2014, MNRAS, 443, 624, doi: [`10.1093/mnras/stu1177`](http://doi.org/10.1093/mnras/stu1177)

(ref: Fall:2001) Fall, S. M., & Zhang, Q. 2001, ApJ, 561, 751, doi: [`10.1086/323358`](http://doi.org/10.1086/323358)

(ref: Finn:2019) Finn, M. K., Johnson, K. E., Brogan, C. L., et al. 2019, ApJ, 874, 120, doi: [`10.3847/1538-4357/ab0d1e`](http://doi.org/10.3847/1538-4357/ab0d1e)

(ref: Fomalont:2014) Fomalont, E., van Kempen, T., Kneissl, R., et al. 2014, The Messenger, 155, 19

(ref: Garay:2003) Garay, G., Brooks, K. J., Mardones, D., & Norris, R. P. 2003, ApJ, 587, 739, doi: [`10.1086/368310`](http://doi.org/10.1086/368310)

(ref: Geyer:2001) Geyer, M. P., & Burkert, A. 2001, MNRAS, 323, 988, doi: [`10.1046/j.1365-8711.2001.04257.x`](http://doi.org/10.1046/j.1365-8711.2001.04257.x)

(ref: Gilbert:2007) Gilbert, A. M., & Graham, J. R. 2007, ApJ, 668, 168, doi: [`10.1086/520910`](http://doi.org/10.1086/520910)

(ref: Gorski:2017) Gorski, M., Ott, J., Rand, R., et al. 2017, ApJ, 842, 124, doi: [`10.3847/1538-4357/aa74af`](http://doi.org/10.3847/1538-4357/aa74af)

(ref: Harris:2003) Harris, W. E. 2003, in A Decade of Hubble Space Telescope Science, ed. M. Livio, K. Noll, & M. Stiavelli, Vol. 14, 78–100

(ref: Hebbar:2019) Hebbar, P. R., Heinke, C. O., Sivakoff, G. R., & Shaw, A. W. 2019, MNRAS, 485, 5604, doi: [`10.1093/mnras/stz553`](http://doi.org/10.1093/mnras/stz553)

(ref: Heckman:2001) Heckman, T. M. 2001, in Astronomical Society of the Pacific Conference Series, Vol. 240, Gas and Galaxy Evolution, ed. J. E. Hibbard, M. Rupen, & J. H. van Gorkom, 345. [`https://arxiv.org/abs/astro-ph/0009075`](https://arxiv.org/abs/astro-ph/0009075)

(ref: Hildebrand:1983) Hildebrand, R. H. 1983, QJRAS, 24, 267

(ref: Hills:1980) Hills, J. G. 1980, ApJ, 235, 986, doi: [`10.1086/157703`](http://doi.org/10.1086/157703)

(ref: Hirashita:2013) Hirashita, H. 2013, MNRAS, 429, 3390, doi: [`10.1093/mnras/sts602`](http://doi.org/10.1093/mnras/sts602)

(ref: Holtzman:1992) Holtzman, J. A., Faber, S. M., Shaya, E. J., et al. 1992, AJ, 103, 691, doi: [`10.1086/116094`](http://doi.org/10.1086/116094)

(ref: Horta:2021) Horta, D., Hughes, M. E., Pfeffer, J. L., et al. 2021, MNRAS, 500, 4768, doi: [`10.1093/mnras/staa3522`](http://doi.org/10.1093/mnras/staa3522)

(ref: Imara:2019) Imara, N., & Faesi, C. M. 2019, ApJ, 876, 141, doi: [`10.3847/1538-4357/ab16cc`](http://doi.org/10.3847/1538-4357/ab16cc)

(ref: Indebetouw:2005) Indebetouw, R., Mathis, J. S., Babler, B. L., et al. 2005, ApJ, 619, 931, doi: [`10.1086/426679`](http://doi.org/10.1086/426679)

(ref: Johansson:1987) Johansson, I. 1987, A&A, 182, 179

(ref: Johnson:2018) Johnson, K. E., Brogan, C. L., Indebetouw, R., et al. 2018, ApJ, 853, 125, doi: [`10.3847/1538-4357/aa9ff8`](http://doi.org/10.3847/1538-4357/aa9ff8)

(ref: Johnson:2003) Johnson, K. E., & Kobulnicky, H. A. 2003, ApJ, 597, 923, doi: [`10.1086/378585`](http://doi.org/10.1086/378585)

(ref: Johnson:2000) Johnson, K. E., Leitherer, C., Vacca, W. D., & Conti, P. S. 2000, AJ, 120, 1273, doi: [`10.1086/301541`](http://doi.org/10.1086/301541)

(ref: Keller:2020) Keller, B. W., Kruijssen, J. M. D., Pfeffer, J., et al. 2020, MNRAS, 495, 4248, doi: [`10.1093/mnras/staa1439`](http://doi.org/10.1093/mnras/staa1439)

(ref: Kobulnicky:1999) Kobulnicky, H. A., & Johnson, K. E. 1999, ApJ, 527, 154, doi: [`10.1086/308075`](http://doi.org/10.1086/308075)

(ref: Kroupa:2001) Kroupa, P. 2001, MNRAS, 322, 231, doi: [`10.1046/j.1365-8711.2001.04022.x`](http://doi.org/10.1046/j.1365-8711.2001.04022.x)

(ref: Leitherer:2014) Leitherer, C., Ekström, S., Meynet, G., et al. 2014, ApJS, 212, 14, doi: [`10.1088/0067-0049/212/1/14`](http://doi.org/10.1088/0067-0049/212/1/14)

(ref: Leitherer:2010) Leitherer, C., Ortiz Otálvaro, P. A., Bresolin, F., et al. 2010, ApJS, 189, 309, doi: [`10.1088/0067-0049/189/2/309`](http://doi.org/10.1088/0067-0049/189/2/309)

(ref: Leitherer:1999) Leitherer, C., Schaerer, D., Goldader, J. D., et al. 1999, ApJS, 123, 3, doi: [`10.1086/313233`](http://doi.org/10.1086/313233)

(ref: Longmore:2014) Longmore, S. N., Kruijssen, J. M. D., Bastian, N., et al. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 291, doi: [`10.2458/azu_uapress_9780816531240-ch013`](http://doi.org/10.2458/azu_uapress_9780816531240-ch013)

(ref: Martin:2002) Martin, C. L., Kobulnicky, H. A., & Heckman, T. M. 2002, ApJ, 574, 663, doi: [`10.1086/341092`](http://doi.org/10.1086/341092)

(ref: Matthews:2018) Matthews, A. M., Johnson, K. E., Whitmore, B. C., et al. 2018, ApJ, 862, 147, doi: [`10.3847/1538-4357/aac958`](http://doi.org/10.3847/1538-4357/aac958)

(ref: McMullin:2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Osterbrock:1989) Osterbrock, D. E. 1989, Astrophysics of gaseous nebulae and active galactic nuclei

(ref: Pelupessy:2012) Pelupessy, F. I., & Portegies Zwart, S. 2012, MNRAS, 420, 1503, doi: [`10.1111/j.1365-2966.2011.20137.x`](http://doi.org/10.1111/j.1365-2966.2011.20137.x)

(ref: Portegies:2010) Portegies Zwart, S. F., McMillan, S. L. W., & Gieles, M. 2010, ARA&A, 48, 431, doi: [`10.1146/annurev-astro-081309-130834`](http://doi.org/10.1146/annurev-astro-081309-130834)

(ref: Purser:2016) Purser, S. J. D., Lumsden, S. L., Hoare, M. G., et al. 2016, MNRAS, 460, 1039, doi: [`10.1093/mnras/stw1027`](http://doi.org/10.1093/mnras/stw1027)

(ref: Reines:2012) Reines, A. E., & Deller, A. T. 2012, ApJL, 750, L24, doi: [`10.1088/2041-8205/750/1/L24`](http://doi.org/10.1088/2041-8205/750/1/L24)

(ref: Reines:2016) Reines, A. E., Reynolds, M. T., Miller, J. M., et al. 2016, ApJL, 830, L35, doi: [`10.3847/2041-8205/830/2/L35`](http://doi.org/10.3847/2041-8205/830/2/L35)

(ref: Reines:2011) Reines, A. E., Sivakoff, G. R., Johnson, K. E., & Brogan, C. L. 2011, Nature, 470, 66, doi: [`10.1038/nature09724`](http://doi.org/10.1038/nature09724)

(ref: Riffel:2020) Riffel, R. A. 2020, MNRAS, 494, 2004, doi: [`10.1093/mnras/staa903`](http://doi.org/10.1093/mnras/staa903)

(ref: Ryon:2017) Ryon, J. E., Gallagher, J. S., Smith, L. J., et al. 2017, ApJ, 841, 92, doi: [`10.3847/1538-4357/aa719e`](http://doi.org/10.3847/1538-4357/aa719e)

(ref: Salpeter:1955) Salpeter, E. E. 1955, ApJ, 121, 161, doi: [`10.1086/145971`](http://doi.org/10.1086/145971)

(ref: Scoville:2014) Scoville, N., Aussel, H., Sheth, K., et al. 2014, ApJ, 783, 84, doi: [`10.1088/0004-637X/783/2/84`](http://doi.org/10.1088/0004-637X/783/2/84)

(ref: Shirley:2015) Shirley, Y. L. 2015, PASP, 127, 299, doi: [`10.1086/680342`](http://doi.org/10.1086/680342)

(ref: Vacca:2002) Vacca, W. D., Johnson, K. E., & Conti, P. S. 2002, AJ, 123, 772, doi: [`10.1086/338644`](http://doi.org/10.1086/338644)

(ref: Vanzi:1997) Vanzi, L., & Rieke, G. H. 1997, ApJ, 479, 694, doi: [`10.1086/303911`](http://doi.org/10.1086/303911)

(ref: Vazquez:2005) Vázquez, G. A., & Leitherer, C. 2005, ApJ, 621, 695, doi: [`10.1086/427866`](http://doi.org/10.1086/427866)

(ref: Weiler:1986) Weiler, K. W., Sramek, R. A., Panagia, N., van der Hulst, J. M., & Salvati, M. 1986, ApJ, 301, 790, doi: [`10.1086/163944`](http://doi.org/10.1086/163944)

(ref: Whitcomb:1981) Whitcomb, S. E., Gatley, I., Hildebrand, R. H., et al. 1981, ApJ, 246, 416, doi: [`10.1086/158939`](http://doi.org/10.1086/158939)

(ref: Whitmore:2000) Whitmore, B. C. 2000, arXiv e-prints, astro. [`https://arxiv.org/abs/astro-ph/0012546`](https://arxiv.org/abs/astro-ph/0012546)

(ref: Whitmore:1995) Whitmore, B. C., & Schweizer, F. 1995, AJ, 109, 960, doi: [`10.1086/117334`](http://doi.org/10.1086/117334)

(ref: Wilson:2008) Wilson, C. D., Petitpas, G. R., Iono, D., et al. 2008, ApJS, 178, 189, doi: [`10.1086/590910`](http://doi.org/10.1086/590910)

(ref: Wood:1989) Wood, D. O. S., & Churchwell, E. 1989, ApJS, 69, 831, doi: [`10.1086/191329`](http://doi.org/10.1086/191329)

[^1]: The Karl G. Jansky Very large Array is an instrument of the National Radio Astronomy Observatory (NRAO). The NRAO is a facility of the National Science Foundation, operated under cooperative agreement with Associated Universities, Inc.

[^2]: <https://science.nrao.edu/facilities/vla/observing/callist>

[^3]: Six additional observations were completed while the VLA configuration was transitioning to D array in September 2015. The resulting u-v coverage in these latter observations proved to be un-imageable because the u-v coverage was so irregular. Thus, the data in these 6 scheduling blocks were discarded.

[^4]: <https://science.nrao.edu/facilities/vla/docs/manuals/oss/performance/fdscale>

[^5]: <https://casa.nrao.edu/casadocs-devel/stable/global-task-list/task_imstat/about>

[^6]: <https://photutils.readthedocs.io/en/stable/index.html>

[^7]: <https://www.stsci.edu/science/starburst99/docs/default.htm>

[^8]: We use the unconvolved 22 GHz map to trace the thermal emission instead of the 33 GHz map in Figure [7](#fig:normpar) because of the calibration concerns in the 33 GHz data. The morphology in the 22 and 33 GHz maps is similar, as seen by comparing the contours in Figure [4](#fig:nicmos).

[^9]: The studies of (cite: Johnson:2000), (cite: Johnson:2003), (cite: Cabanac:2005), and (cite: Chandar:2003) do not use the nomenclature of Knot 4a, and in the latter two, they do not necessary assess properties of the radio knots directly, focusing on the nearby optical and IR sources instead. We specifically are referring to radio sources, which lack optical counterparts, when we use the “knot” terminology. In the crowded regions of Knot 4a and 4b, the resolutions of these older studies and the apertures the authors selected likely include both radio knots and optical sources. Age estimates that rely on optical and IR tracers, like those of (cite: Cabanac:2005) and (cite: Chandar:2003), may not be accurate for the radio knots and comparison of the optical clusters and radio sources needs to be done carefully, as we have tried to do here.

</paper>

## Items to check

```json
[
 {
  "path": "data.observing_dates.evidence[2]",
  "value": "2015.1.01569: 2016 July 31, 2016-08-02; 2016.1.00027: 2017 July 13; 2012.1.00413: 2015 Sept 05 to 2015 Sept 29; 2016.1.00492: 2016-11-15",
  "failed_quote": "At 250 GHz, project 2012.1.00413 was observed 5 times between 2015 Sept 05 and 2015 Sept 29 with 30-35 antennas. Finally at 340 GHz, project 2016.1.00492 was observed on 2016-11-15"
 },
 {
  "path": "processing.calibration.casa_version.evidence[2]",
  "value": "CASA 4.5.3 (2015.1.01569), CASA 4.7.2 (2016.1.00027), CASA 4.3.1 (2012.1.00413), CASA 4.7.0 (2016.1.00492); VLA calibrated/imaged in CASA 5.4.2",
  "failed_quote": "The data were calibrated with Pipeline-Cycle3-R1-B v.34044 in CASA 4.3.1 and imaged in CASA 5.6.1-8. Finally at 340 GHz, project 2016.1.00492 was observed on 2016-11-15... The data were calibrated with Pipeline-Cycle4-R2-B v.38377 in CASA 4.7.0"
 },
 {
  "path": "processing.calibration.pipeline_version.evidence[2]",
  "value": "Pipeline-Cycle3-R4-B v.36660 (2015.1.01569), Pipeline-Cycle4-R2-B v.39732 (2016.1.00027), Pipeline-Cycle3-R1-B v.34044 (2012.1.00413), Pipeline-Cycle4-R2-B v.38377 (2016.1.00492)",
  "failed_quote": "The data were calibrated with Pipeline-Cycle3-R1-B v.34044 in CASA 4.3.1 and imaged in CASA 5.6.1-8. Finally at 340 GHz, project 2016.1.00492... The data were calibrated with Pipeline-Cycle4-R2-B v.38377 in CASA 4.7.0"
 },
 {
  "path": "analysis_steps[0].method.evidence[0]",
  "value": "Convolve all VLA and ALMA maps to a 0.3'' circular beam, stack the 8 convolved maps, define source footprints using the 20-sigma (73 uJy/bm) contour of the stacked map with manual masking in crowded regions, sum intensity divided by beam area, subtract median masked background; for HST/NICMOS Pa-alpha, shift by 1.33'', scale F187N by 3% and subtract F190N, and extract using the 33 GHz half-light r",
  "failed_quote": "For photometry, we stacked the convolved 0.3$''$ maps, which includes all the maps listed in Table [2](#tab:alldataprop), except for the HST/NICMOS map. We overlaid contours of the stacked image and selected the contour of 20$\\times$ the rms (73 $\\mu$Jy bm$^{-1}$) of the stacked map."
 },
 {
  "path": "analysis_steps[0].method.evidence[1]",
  "value": "Convolve all VLA and ALMA maps to a 0.3'' circular beam, stack the 8 convolved maps, define source footprints using the 20-sigma (73 uJy/bm) contour of the stacked map with manual masking in crowded regions, sum intensity divided by beam area, subtract median masked background; for HST/NICMOS Pa-alpha, shift by 1.33'', scale F187N by 3% and subtract F190N, and extract using the 33 GHz half-light r",
  "failed_quote": "To briefly summarize, we sum the intensity across the pixels associated with the source and divide it by the beam area. For the background subtraction, we masked the sources and calculated the median intensity of the image."
 },
 {
  "path": "analysis_steps[0].assumptions[0].evidence[0]",
  "value": "Rayleigh-Jeans tail of hot star SEDs makes continuum in F187N 3% brighter than in F190N",
  "failed_quote": "If the SEDs of the SSC are Rayleigh-jeans tails of hot star SEDs, the continuum in F187N will be 3$\\%$ brighter than in F190N. In the subsequent analysis, we scaled the F187N filter down by the theoretical scale of 3$\\%$ before subtracting it from the F190N filter."
 },
 {
  "path": "analysis_steps[2].validation.evidence[0]",
  "value": "Compared derived A_V range (2.2 - 16) with literature large-aperture value A_V = 10.5 from (cite: Cabanac:2005).",
  "failed_quote": "(cite: Cabanac:2005) find an extinction of A$_V$ = 10.5 from the ratio of Br$\\gamma$/Br10 using the line fluxes from (cite: Vanzi:1997). Our estimates of the extinction are more localized but the range is consistent with the extinction reported by (cite: Cabanac:2005)."
 }
]
```

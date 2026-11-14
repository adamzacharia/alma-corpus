# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2023ApJ...948..110Y\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# Multiple Rings and Asymmetric Structures in the Disk of SR 21

## Abstract

Crescent-like asymmetric dust structures discovered in protoplanetary disks indicate dust aggregations. Thus, the research on them helps us understand the planet formation process. Here we analyze the ALMA data of the protoplanetary disk around the T-Tauri star SR 21, which has asymmetric structures detected in previous sub-millimeter observations. Imaged at ALMA Band 6 (1.3 mm) with a spatial resolution of about 0.$\ensuremath{''}$04, the disk is found to consist of two rings and three asymmetric structures, with two of the asymmetric structures being in the same ring. Compared to the Band 6 image, the Band 3 (2.7 mm) image also shows the three asymmetric structures but with some clumps. The elongated asymmetric structures in the outer ring could be due to the interactions of a growing planet. By fitting the Band 3 and Band 6 dust continuum data, two branches of solutions of maximum dust size in the disk are suggested: one is larger than 1 mm, and the other is smaller than 300 $\mu m$. High-resolution continuum observations at longer wavelengths as well as polarization observations can help break the degeneracy. We also suggest that the prominent spiral previously identified in VLT/SPHERE observations to the south of the star at 0.$\ensuremath{''}$25 may be the scattered light counterpart of the Inner Arc, and the structure is a dust-trapping vortex in nature. The discovered features in SR 21 make it a good target for studying the evolution of asymmetric structures and planet formation.

# Introduction

In recent years high angular resolution observations in the sub-millimeter band using instruments such as the Atacama Large Millimeter/submillimeter Array (ALMA) have discovered that some protoplanetary disks show asymmetric structures, such as HD 142527 (cite: Fukagawa2013-da; Casassus2013-nm; Boehler2017), Oph IRS 48 (cite: VanderMarel2013), SAO 206462 (HD 135344B) (cite: Perez2014; Cazzoletti2018-gi) and MWC 758 (cite: Dong2018-ve). (cite: Francis2020-jv) discovered that in a sample of 38 transition disks, the fraction of asymmetric disks is 24%, while the occurrence rate of asymmetric structures in all kinds of disks remains unknown. It is believed that dust is "trapped" in these structures due to pressure bumps in the disk, which accelerate dust growth and promote planet formation processes (cite: Barge1995-nw; Klahr1997-qv; Regaly2012-zz). Therefore, research on these asymmetric structures in the protoplanetary disks is vital for us to learn about the planet formation process in protoplanetary disks.

Several scenarios have been suggested for the formation of asymmetric structures. One popular scenario suggests that such asymmetry is caused by Rossby Wave Instability (RWI) vortex (cite: Zhu2014). Under a low viscosity ($\alpha\sim10^{-5}-10^{-4}$), the vortices, as well as the asymmetric structures, can be sustained for a few Myrs (cite: Fu2014-zt). Besides, other scenarios, such as an eccentric cavity (cite: Ataiee2013) and "horseshoe structures" (cite: Ragusa2017-is), could also be responsible for these structures. Understanding the formation mechanisms of such asymmetric structures will no doubt improve our understanding of planet formation and evolution.

It is believed that the asymmetric structures will finally dissipate, and they elongate and break with the interaction of a growing planet (cite: Hammer2019) or due to the dust back reaction onto gas (cite: Fu2014-zt). Above all, we still know little about how asymmetric structures evolve and how the planets form from them. Observing disks with asymmetric structures, and trying to understand their dust sizes, is quite necessary for constraining theoretical models.

Asymmetric structures are also related to other asymmetric structures. They could appear in multiple-ring systems (e.g., SAO 206462 (cite: Perez2014; Cazzoletti2018-gi), HD 143006 (cite: Perez2018-rm)), and (cite: Garufi2018-ew) found out that all asymmetric disks seen in ALMA have spiral arms in the near-infrared band. (cite: Van_der_Marel2021-vr) suggested that asymmetric dust structures could be linked to a low local gas surface density through the observational Stokes number, which can explain why the asymmetric features in multi-ring systems tend to appear in the outer ring, such as SAO 206462 and HD 143006, and can also be linked to either vortices (for $\alpha\lesssim10^{-4}$ in disks) or spiral arms.

SR 21 is a T-Tauri star located in the Ophiuchus Molecular Cloud at a distance of about 138.4$\pm$1.1 pc from Earth (cite: GAIA2018). (cite: Herczeg2014-dm) suggested that this F7 type star has a stellar mass of about 1.67 $M_\odot$, luminosity of about 7.4 $L_\odot$ and an age of about 10 Myr through a low-resolution spectroscopic study. Previous near-infrared and sub-millimeter observations (cite: Andrews2011; Follette2013; Muro-Arena2020) have shown that it holds a circumstellar disk, which has a cavity in sub-millimeter continuum emission but not in near-infrared scattered light, suggesting segregation of dust of different sizes (cite: dong12). (cite: Perez2014) revealed that it has an asymmetric structure in submillimeter observations at a spatial resolution of about 0.$\ensuremath{''}$3 using ALMA Band 9 (0.45 mm). (cite: Perez2014) also pointed out that its inclination is about 15$^\circ$ and position angle is about 16$^\circ$, so it is a nearly face-on disk and suitable for asymmetric structure study. Near Infrared observations using the Spectro-Polarimetric High-contrast Exoplanet REsearch (cite: Beuzit2019-um) mounted on the Very Large Telescope (VLT) showed that it has complex structures including rings and spiral arms, under a spatial resolution of about 0.05$\ensuremath{''}$ (cite: Muro-Arena2020). (cite: Muro-Arena2020) also pointed out that the spiral arms of SR 21 are inside an outer ring and quite tight (pitch angles close to zero at a radius of $\sim0.\ensuremath{''}2$), while the spiral arms in other targets like HD 135344B and MWC 758 are the outer-most visible structures and relatively loose (pitch angles$\sim10^\circ-16^\circ$). While previous observations of SR 21 in sub-millimeter bands have spatial resolutions of only about 0.2$\ensuremath{''}$-0.3$\ensuremath{''}$, it is not enough to understand the corresponding structures of large dust in the disk. Therefore, higher-resolution observations in the sub-millimeter band are pretty necessary.

This paper will show our new observational results of SR 21 via ALMA at a higher resolution. In Section 2, we will describe our observations; in section 3, we will explain our results; in section 4, we will give some discussions by combining our observation results and previous results; and in section 5, we will make a summary.

# Observations and Data Reduction

We have carried out the ALMA observations towards SR 21 (2018.1.00689.S, PI: T. Muto) at Band 6 in 2019, in the C43-6 (short-spacing; August 24; $\sim$10 minutes on source) and C43-9 (long baseline; June 24; $\sim$48 minutes on source) array configurations. The C43-6 and C43-9 configuration observations covered the baseline ranges of $\sim$40–3400 and $\sim$80–13640 meters, respectively. The average precipitable water vapor (PWV) during the C43-6 and C43-9 observations were 1.0 and 0.5 mm, respectively.

Our correlator setup employed five spectral windows: there were two continuum spectral windows (1.875 GHz bandwidth, 43 km s$^{-1}$ velocity resolution) centering at the rest frequencies of 217 GHz and 233 GHz; two spectral windows were centering at the rest frequencies of $^{13}$CO 2-1 (220.398684 GHz) and C$^{18}$O 2-1 (219.560358 GHz) of which the bandwidth and velocity resolution are 468.75 MHz and $\sim$0.665 km s$^{-1}$, respectively; there was one spectral window centering at the request frequency of CO 2-1 (230.538000 GHz) of which the bandwidth and velocity resolution are 937.50 MHz and $\sim$0.635 km s$^{-1}$, respectively.

The basic calibration was carried out using the pipeline in the Common Astronomy Software Applications (CASA) package 5.4.0-70. We derived the Bandpass and complex gain calibration solutions based on the observations on J1517-2422 and J1633-2557, respectively. The absolute flux scaling was derived based on referencing the ALMA calibrator grid survey on J1517-2422. We quote the proper motion of the SR 21 from GAIA DR2 (cite: GAIA2018). To allow joint imaging of all data, we used the CASA task `fixplanets` to shift the target source to the expected coordinates on June 23, 2019.

We used the CASA task `uvcontsub` to separate the continuum and spectral line data. We perform phase self-calibration on the continuum data only and then apply these solutions to the line emission. We combined all spectral windows when deriving self-calibration solutions. In addition, we combined the two polarizations (i.e., XX and YY) for the long baseline observations to avoid massive flagging due to the limited signal-to-noise ratios. The solution intervals for the C43-6 and C43-9 configuration observations were 30 seconds and 540 seconds, respectively. The longer solution interval for the C43-9 configuration observations was due to the lower signal-to-noise ratios. The command `tclean` provided by CASA was used to image the continuum data, with Briggs weighting and robust parameter 0.5. While we used the MIRIAD software package (cite: Sault1995) to perform naturally weighted imaging for the CO 2-1, $^{13}$CO 2-1, and C$^{18}$O 2-1 lines.

# Results

## ALMA Band 6 Continuum image

The Band 6 continuum image of SR 21 is shown in Figure [1](#fig:fig1)(a). The beam size is $0.\ensuremath{''}050\times0.\ensuremath{''}047$ with a position angle 94$^\circ$. From the image, one can see two rings. The outer ring ($>25\sigma$, 1$\sigma\sim1.7\times10^{-5}$Jy/beam) extends between a radial separation from the central star of 0.34$\ensuremath{''}$ to 0.48$\ensuremath{''}$ (47-66 au). As for the inner ring, it extends between a radial separation of 0.14$\ensuremath{''}$ to 0.28$\ensuremath{''}$ (19.5-39 au), the faintest part on the north side reaches $5\sigma$ while its brightest part on the south side is higher than $\sim20\sigma$.

Asymmetric structures can be found in the inner and outer rings. The outer ring has two asymmetric structures: South Arc (peak located at $\sim170^\circ$) and North Arc (peak located at $\sim305^\circ$). While for the asymmetric structures of the inner ring, we refer to it as the Inner Arc (peak located at $\sim165^\circ$). We notice that actually, the Inner Arc’s radius is only from 0.$\ensuremath{''}$18 to 0.$\ensuremath{''}$28, and the ring structure between 0.$\ensuremath{''}$14 to 0.$\ensuremath{''}$18 near the Inner Arc is significantly fainter, which may indicate that the inner ring consists of two "sub-rings": one standard ring and one ring with the Inner Arc. In this paper, we do not distinguish between them and simply regard them as the "inner ring".

### Comparison with ALMA Band 3 image

We compare our Band 6 observations with some previous observations. Firstly we compared our Band 6 image with ALMA Band 3 (107.01 - 110.67 GHz, 2.7-2.8 mm) continuum image. The Band 3 image (Project ID: 2017.1.00884.S, PI: Pinilla) shown in Figure [1](#fig:fig1)(b) is the same as the image in (cite: Muro-Arena2020), with the baseline ranging from 138 m to 13.8 km ( 50-5000 $k\lambda$). The inner and the outer ring are barely resolved under a beam size of 0.$\ensuremath{''}$10$\times$0.$\ensuremath{''}$09, and the South Arc and North Arc ($>20\sigma$, $1\sigma\sim1.4\times10^{-5}$Jy/beam) in the outer ring can also be seen. In Band 3, the outer ring has several small "clumps", which differs from the Band 6 image. Some notable clumps and their parameters are summarized in Table [\[table:table1\]](#table:table1).

|  Outer Ring   |  I  | II  | III | IV  |  V  |
|:-------------:|:---:|:---:|:---:|:---:|:---:|
| PA($^\circ$)  | 60  | 120 | 165 | 225 | 265 |
| SNR($\sigma$) | 12  | 14  | 16  | 12  | 10  |
|  Inner Ring   |  A  | B1  | B2  |  C  |  D  |
| PA($^\circ$)  | 65  | 145 | 195 | 245 | 320 |
| SNR($\sigma$) |  7  |  9  | 10  |  7  |  5  |

: Notable Clumps detected in Band 3 Image

To have a detailed comparison of the asymmetric structures in the two different bands, we draw the azimuthal profiles of the inner ring and the outer ring in Band 3 and Band 6 (Figure [2](#fig:fig3)). The profile is drawn by averaging over bins of 10$^\circ$ widths. Figure [2](#fig:fig3)(a) compares the azimuthal profile of the inner ring (0.14$\ensuremath{''}$-0.28$\ensuremath{''}$). For the Band 6 data, an obvious peak B is located at $165^\circ$ corresponding to the Inner Arc. While for Band 3 data, its highest peak ($>8\sigma$) corresponding to the Inner Arc has two sub-peaks, located at 145$^\circ$ and 195$^\circ$, respectively, so this peak centers at 170$^\circ$. Besides, there are three other obvious peaks, A ($\sim7\sigma$) and C($\sim7\sigma$), located at $\sim65^\circ$ and $\sim245^\circ$, and a relatively faint peak D ($\sim5\sigma$) detected at PA $\sim320^\circ$ in Band 3, but in Band 6 no corresponding structures can be found.

The azimuthal profiles of the outer ring (0.$\ensuremath{''}$34-0.$\ensuremath{''}$48) are shown in Figure [2](#fig:fig3)(b). Band 6 clearly shows two peaks, one ranges from 40$^\circ$ to 250$^\circ$, and its peak locates at 170$^\circ$, corresponding to the South Arc, while the other peak locates at 305$^\circ$, corresponding to the North Arc. From this figure, it can be seen that the profiles of the arcs are asymmetric: their peaks are not at their center positions of them. As for Band 3, its azimuthal profile shows five small peaks located at 60$^\circ$, 120$^\circ$, 165$^\circ$, 225$^\circ$, 265$^\circ$ corresponding to the clumps I-V mentioned above, and the highest of them locates at about $165^\circ$. As for the North Arc in Band 3, it locates at about $300^\circ$.

These clumps show higher contrasts at Band 3, which may be partly due to the lower optical depths at this Band. On the other hand, some of the clumps detected at $\lesssim$2-$\sigma$ have a 5% chance to be spurious. To assess whether or not a clump may be spurious, we measured the brightness contrast between its peak and the "valleys" with the lowest intensity in the inter-clump regions. For the outer ring, I and V are only 2$\sigma$ brighter than their adjacent valleys; II is 4$\sigma$ brighter; IV is 2$\sigma$ brighter than the valley between III and IV but is 4$\sigma$ brighter than the valley between IV and V. In light of this, we consider II could be more robust than I, IV and V. As for the inner ring, D is only about 2$\sigma$ brighter; A is 4$\sigma$ brighter than the valley between A and D, but is only 2$\sigma$ brighter than the valley between A and B; C is 4$\sigma$ brighter than the valley between C and D, but only 2$\sigma$ brighter than the valley between C and B. The two sub-peaks of B are only about 1-2$\sigma$ brighter than the valley between them. So despite the North Arc and the South Arc (III) as well as the Inner Arc (B), which are indeed localized clumps since they are observed in both two Bands, we suggest that other clumps, I, IV, V, A, C, D, as well as the two sub-peaks of B, may be spurious, while II could represent the actual structure since it is 4$\sigma$ brighter than its nearby valleys. More profound observations at longer wavelength bands are required to confirm these clumps.

### Comparison with VLT/SPHERE H-Band image

We also compared our data with the previous H-Band ($\sim$1.6 $\mu$m) image taken by VLT/SPHERE. The SPHERE archival data were reduced by the IRDAP (IRDIS Data reduction for Accurate Polarimetry) pipeline (cite: 2020A&A...633A..64V; 2017SPIE10400E..15V), the same as (cite: Muro-Arena2020). We overplotted our Band 6 data on the SPHERE data, shown in Figure [3](#fig:fig4). From the image, it can be seen that for the inner ring, our Inner Arc is generally consistent with the Spiral 1 structure reported by (cite: Muro-Arena2020), indicating some relationship between this asymmetric structure and the spiral arm. As for the outer ring, the South Arc fits well with Arc 1, while the North Arc corresponds to Arc 2.

As mentioned in Section 1, it is common that spiral arms seen in the near-infrared band accompanied by asymmetric structures in the sub-millimeter band, such as HD 135344B (cite: Cazzoletti2018-gi) and MWC 758 (cite: Dong2018-ve). However, for SR 21, there are some differences. Despite the tight spiral arm (cite: Muro-Arena2020) has pointed out, we also noticed that the asymmetric structure of the Inner Arc corresponds to two spiral arms: Spiral 1 and Spiral 2, and their positions fit quite well without obvious offset; this is also different from other targets: the asymmetric structures in HD 135344B and V1247 Ori (cite: Kraus2017-uf) only connect the tip of the spiral arms, while in HD 100546 (cite: Rosotti2020-rk) the asymmetric structure only locates at the start of the spiral arm, and in MWC 758, two asymmetric structures correspond to only one spiral arm.

## ALMA Band 6 CO Isotopologue Emissions

Three CO lines, $^{12}$CO, $^{13}$CO, and C$^{18}$O (2-1) were observed in our research. Their beam sizes are $0.\ensuremath{''}103\times0.\ensuremath{''}100$ with PA=59$^\circ$, $0.\ensuremath{''}104\times0.\ensuremath{''}103$ with PA=64$^\circ$ and $0.\ensuremath{''}104\times0.\ensuremath{''}103$ with PA=65$^\circ$, respectively. Their spectral resolutions of them are 0.6 km/s. We made the moment 0 (intensity) maps of them using the command `immoments`, and they are shown in Figure [4](#fig:figco1). The start(end) of the channels used to make moment maps are chosen by checking that if a bright source ($>4\sigma, 1\sigma=0.001 Jy/beam$) within 0.5” from the central stars appears/disappears. In detail, for the $^{12}$CO line, the channels between -1.96km/s and 8.09 km/s are chosen, for $^{13}$CO line, the channels between -1.96km/s and 6.75 km/s are chosen, and for C$^{18}$O line the channels between -0.62km/s and 6.75 km/s are chosen. The root mean squared (RMS) noise levels of the moment 0 maps are 0.035, 0.03, and 0.04 Jy/beam for $^{13}$CO, C$^{18}$O, and $^{12}$CO images, respectively. Generally, the observed gas structures in protoplanetary disks should be more extended than observed dust structures due to different optical depths (cite: Facchini2017-hy). However, in these figures, the CO features are quite compact, and the emissions mostly come from inside the inner ring, i.e., $<$0.$\ensuremath{''}$28. One exception is the $^{12}$CO 2-1 image, which shows an extended structure to about 0.$\ensuremath{''}$8 in the northeast, although it only has 2-3 $\sigma$.

The $^{13}$CO and C$^{18}$O images show two cores in the north and south. Their positions are slightly shifted in different wavelengths: for the $^{13}$CO image, they have position angles of about 0 and 210$^\circ$, and for the C$^{18}$O image, they have position angles of about -40 and 200$^\circ$. As for the $^{12}$CO image, only the north core (PA$\sim10^\circ$) is apparent.

The compact features in the CO isotopologue emissions seem to indicate the depletion of gas outside of $0.\ensuremath{''}28$. However, considering the large extinctions of SR 21 ($A_V$=6.2, (cite: Herczeg2014-dm)), one more reasonable explanation is that they are affected by the foreground adsorptions. The emission component can be approximated by a Gaussian curve since SR 21 seems close in face-on. To determine the strengths, velocity, and width of the emission and absorption lines, we fit the spectra with the following equation (cite: Kim2020-qi):

$$\begin{equation}
    I_v=A_{emit}\mbox{exp}(-\frac{(V-V_{emis})^2}{2\Delta V_{emis}^2})+A_{abs}\mbox{exp}(-\frac{(V-V_{abs})^2}{2\Delta V_{abs}^2})
\end{equation}$$

|  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Species | $A_{emis}$ | $V_{emis}$ | $\Delta V_{emis}$ | $A_{abs}$ | $V_{abs}$ | $\Delta V_{abs}$ |
|  | (mJy/beam) | (km/s) | (km/s) | mJy/beam | (km/s) | (km/s) |
| $^{12}$CO | 7.354$\pm$3.588 | 2.500$\pm$0.284 | 0.616$\pm$0.059 | -8.000$\pm$3.591 | 3.134$\pm$0.121 | 0.980$\pm$0.162 |
| $^{13}$CO | 4.065$\pm$0.893 | 2.841$\pm$0.055 | 0.626$\pm$0.040 | -4.346$\pm$0.870 | 3.039$\pm$0.032 | 1.144$\pm$0.096 |
| C$^{18}$O | 2.129$\pm$1.231 | 3.051$\pm$0.128 | 0.639$\pm$0.116 | -1.716$\pm$1.196 | 3.167$\pm$0.108 | 1.216$\pm$0.381 |

: Fitting Results of the CO Isotopic Lines

The fitting is done by using SciPy *curve_fit* command, with Trust Region Reflective algorithm. Since the disk is nearly face-on, we used intensities within $0.\ensuremath{''}5$ for the fitting. The result is shown in Figure [5](#fig:figco2) and summarized in Table [\[tab:tab1\]](#tab:tab1). The fitting results show that the emission lines center at Kinematic Local Standard of Rest (LSRK) velocity about 2.8 km/s, corresponding to barycentric velocity about -7.7 km/s, which is consistent with the radial velocity -7.3$\pm$1.64 km/s calibrated by GAIA (cite: GAIA2018). The absorption features center at about 3.1 km/s, corresponding to a barycentric velocity of about -7.4 km/s resulting from foreground absorption. This absorption can be seen in the channel maps, especially for $^{13}$CO and CO line emissions (Figure [6](#fig:figchannelmap)). According to the barycentric velocities, the absorption body is moving toward the disk. Besides, it should be noted that from the channel maps, the north structures (e.g., the 1.39km/s and 2.06km/s channels of $^{12}$CO map) are more extended than the south structures (e.g., the 5.4km/s and 6.08 km/s channels of $^{12}$CO map), this may indicate the gas structures in the disk are asymmetric.

Then we take some steps to estimate the Toomre Q parameters (cite: 1964ApJ...139.1217T) to help understand the gravitational stability status inside the inner disk ($<$0.$\ensuremath{''}$28). For calculation, we unite the beam sizes of CO isotopologue images to $0.\ensuremath{''}105\times0.\ensuremath{''}105$ using the `imsmooth` command. Firstly, we make the moment 8 map of $C^{18}O$ (Figure [7](#fig:figco3)(a)), which shows the peak intensities of every pixel. The CO isotopologue abundance ratio of the interstellar medium is $^{13}CO:^{12}CO=1:69$ and $C^{18}O:^{12}CO=1:570$ (i.e., $C^{18}O:^{13}CO\approx1:8$), as for protoplanetary disks, the abundance ratio in the protoplanetary disk of HD 163296 is $^{13}CO:^{12}CO=1:67$ and $C^{18}O:^{13}CO=1:7$ (cite: Qi2011-fb) and (cite: Yoshida2022-jd) founded out that in the disk around TW Hya, the $^{13}CO:^{12}CO=1:21$ at disk radius of 70-110 AU and $^{13}CO:^{12}CO=1:84$ for disk radius larger than 130 AU. These results are all significantly smaller than the ratios in our observations. Therefore, the $^{12}CO$ and $^{13}CO$ lines are optically thick, and we can use their brightness temperatures as gas temperatures. Here we use the moment 8 map of $^{13}$CO with continuum (Figure [7](#fig:figco3)(b)) to calculate the brightness temperature $T_{^{13}CO}$ using the Planck function $I_{^{13}CO,peak}=B(\nu_{^{13}CO},T_{^{13}CO})$. Then the peak optical depth of C$^{18}$O emission $\tau_{C^{18}O, peak}$ can be derived via the radiative transfer equation:

$$\begin{equation}
    I_{C^{18}O,peak}=B(\nu_{C^{18}O},T_{^{13}CO})(1-\mbox{exp}(-\tau_{C^{18}O,peak}))
\end{equation}$$

After that, we derive the $C^{18}O$ column density $N_{C^{18}O}$ using the equation given by (cite: Mangum2015-ud):

$$\begin{equation}
    N_{C^{18}O}=\frac{3h}{8\pi^3\mu^2J_u}(\frac{kT_{ex}}{hB_0}+1/3)\mbox{exp}(\frac{E_{J_u}}{kT_{ex}})[\mbox{exp}(\frac{h\nu}{kT_{ex}})-1]^{-1}\int \tau dv
\end{equation}$$

Here $\mu$, $J_u$, and $B_0$ are the dipole moment, the rotational quantum number of the line transition upper level, and the rigid rotor rotational constant, respectively. The excitation temperature $T_{ex}$ equals the gas temperature. We assume that the line optical depth has a Gaussian profile with the peak value of $\tau_{peak}$ and the width of $\Delta v$ then $\int \tau dv\approx\sqrt{2\pi}\tau_{peak}\Delta v$, and $\Delta v=2\sqrt{2 \mbox{ln} 2}\Delta V_{emis}$. After knowing the column density, the gas (hydrogen) surface density $\Sigma_g$ can be calculated via: $$\begin{equation}
    \Sigma_g=m_{H_2}N_{C^{18}O}/\chi
\end{equation}$$ here $\chi$ is the ratio of $C^{18}O$ to $H_2$, and we use the interstellar abundance 1.79$\times10^{-7}$ (cite: 1999RPPh...62..143W). Assuming that the disk surface density $\Sigma$ is dominated by the gas surface density, i.e., $\Sigma\approx\Sigma_g$, then the Toomre Q parameter can be derived from: $$\begin{equation}
    Q=\frac{c_k\Omega_k}{\pi G \Sigma_g}
\end{equation}$$

Here $c_k=\sqrt{kT/m_{H_2}}$ is the sound speed, and $\Omega_k$ is the epicyclic frequency, which we assume that it equals the angular velocity, i.e., $\Omega_k=\sqrt{GM_{star}/r^3}$. The result is shown in Figure [8](#fig:figco4)(c), considering that Q$\gg$1, the inner disk is gravitational stable.

There are some caveats in this calculation, though. Firstly, emission from these three tracers CO, $^{13}$CO, C$^{18}$O is likely coming from different vertical heights in the disc, thus using $^{13}$CO and C$^{18}$O together to calculate $I_{C^{18}O, peak}$ assumes the two are tracing similar parts of the disc, which is not necessarily true. Secondly, we assume that the ratio of $C^{18}O$ to $H_2$ is the same as the interstellar abundance, which is also not necessarily true: the CO molecules suffer from several effects such as CO freeze-out (cite: Qi2011-fb), isotope-selective photodissociation (cite: Miotello2016-gw; Miotello2018-lt) and CO depletion (cite: Krijt2020-oe), these effects will lower the observed abundance of CO molecules; thus the actual disk mass could be higher, and Q parameter could be smaller than our calculation.

# Discussions

## Disk Morphology

The two asymmetric structures in the outer ring are quite elongated, making them the elongated vortices suggested in previous studies, which could be caused by dead zone (cite: Regaly2012-zz) or a slow-growing planet (cite: Hammer2017-dq; Hammer2019). (cite: Hammer2019) suggested that compared to dead zone-induced elongated vortices, planet-induced elongated vortices frequently have off-center peaks due to repeated perturbations from the planet’s spiral arms. In the outer ring, two peaks of the asymmetric structures (the North Arc and the South Arc) exist. Their azimuthal profiles are both asymmetric, consistent with the characteristics of planet-induced vortices suggested by (cite: Hammer2019). Therefore, we suggested that the two asymmetric structures in the outer ring are induced by a growing planet between the rings rather than a dead zone. Furthermore, (cite: Hammer2019) pointed out that such elongated asymmetric structures may also be accompanied by trojan dust that is co-orbital with the planet at the L5 Lagrange point, and the azimuthal profile could be changed by the interaction between the planet’s spiral density waves and its associated vortex. Our sub-millimeter observations do not catch obvious structures which could be related to trojan dust, while (cite: Muro-Arena2020) caught one "kink" structure between the gap, indicating a planet there. Here we suggested that this "kink" may also be the trojan dust induced by the planet, and further study is needed to confirm this. As for the latter, (cite: Hammer2019) suggested the change could happen for a planet at Jupiter’s separation from the Sun in a few years. Considering the planet of SR 21 is farther from the star and less massive (see Section 4.3), it may take more time for the azimuthal profile to change.

Despite (cite: Hammer2019), (cite: Li2020-pt) suggested that one original large asymmetric structure will break into small clumps due to the feedback of formed dust onto the gas, and the broken clumps can be more prominent at a longer wavelength, which could help explain the multiple clumps observed in Band 3. However, as discussed in Section 3.1.1, the clump structures may not be real; future observations are needed to confirm them.

In addition, previous research like (cite: Baruteau2015-gj) suggested that the peaks of asymmetric structures in different dust sizes will have offsets if they are vortices triggered by the RWI; thus the peaks of the asymmetric structures will be different in different wavelengths. (cite: Cazzoletti2018-gi) confirmed offsets of the asymmetric structures in the disk around HD 135344B between different wavelengths, but the offset is in the opposite direction of the theoretical prediction. As for SR 21, the peak of North Arc in Band 3 is $300^\circ\pm5^\circ$, while in Band 6, it is $305^\circ\pm5^\circ$, so in Band 6, the peak is $5^\circ\pm5^\circ$ ahead of Band 3. The South Arc has a similar case: in Band 6, the peak is $5^\circ\pm5^\circ$ ahead of Band 3 (170$^\circ\pm5^\circ$ vs. 165$^\circ\pm5^\circ$). While for the Inner Arc, the peak in Band 6 is $5^\circ\pm5^\circ$ below the peak in Band 3 (165$^\circ\pm5^\circ$ vs. 170$^\circ\pm5^\circ$). The SR 21 disk is nearly face-on, so it is hard to judge which side is nearer to us, then it is hard to know whether the gas in the disk rotates clockwise or counterclockwise. Therefore it is hard to judge if the observed offsets are consistent with the theoretical prediction. The peak offset of the asymmetric structure in HD 135344B between Band 3 and Band 4 is about 25$^\circ$, and about 40$^\circ$ between Band 3 and Band 7. Compared to this, the peak offsets in SR 21’s asymmetric structures are pretty smaller than HD 135344B. One possible explanation for this is that the asymmetric structures in SR 21 are newly formed, and it may still need some time to develop a significant peak shift as HD 135344B.

## Dust Size

We derived the spectral indices map using the Band 3 and 6 data to estimate the maximum dust size ($a_{max}$). In this step, we re-image the Band 6 data to make sure it has the same beam size (0.$\ensuremath{''}$10$\times$0.$\ensuremath{''}$09, and PA=90$^\circ$) and UV-distance ($50-5000$ k$\lambda$) as the Band 3 data, and register the two images based on the proper motion data got by (cite: GAIA2018). The spectral indices $\alpha$ were calculated by:

$$\begin{equation}
    \alpha=\frac{log(L_{3}/L_{6})}{log(\nu_{3}/\nu_{6})}
    \label{spectral_index}
\end{equation}$$

Here $L_{3}$ and $L_{6}$ are the intensities of Band 3 and Band 6 images. $\nu_{3}$=110.2 GHz and $\nu_{6}$=217.0 GHz are the rest frequencies of Band 3 and 6 observations, respectively. Only the pixels brighter than 4$\sigma$ are used to calculate the index. In addition, the errors $\Delta\alpha$ were given by:

$$\begin{equation}
    \Delta\alpha=\sqrt{(\frac{\partial\alpha}{\partial L_{3}})^2\Delta L_{3}^2+(\frac{\partial\alpha}{\partial L_{6}})^2\Delta L_{6}^2}
    \label{spectral_index_error}
\end{equation}$$

Here $\Delta L_{3}=1.4\times10^{-5}$Jy/beam and $\Delta L_{6}=3\times10^{-5}$Jy/beam are the RMS noise level of Band 3 and 6 images used here. The results are shown in Figure [9](#fig:fig5). From the figures, one can see that the spectral indices of the disk are mainly between 3.0 and 4.0. At the clumps, the spectral indices are generally smaller than 3.5, smaller than other places, which indicates larger grain sizes at the locations of the clumps. This can be seen more clearly in the azimuthal profiles of the inner ring (Figure [9](#fig:fig5)(e)) and the outer ring (Figure [9](#fig:fig5)(f)): the lowest spectral index in the inner ring is at clump D, about 3.0, while the lowest spectral index in the outer ring is at clump I, about 3.3. Note that for the azimuthal profile of the inner ring, the values between PA 0-30$^\circ$ are not drawn because the flux in Band 3 here is smaller than 4$\sigma$, and the Band 3 flux around PA 280$^\circ$ is also smaller than 4 $\sigma$, so one can see there is one drop at this position angle. Based on the simulations like (cite: Birnstiel2018-jb), spectral indices $\sim$3-4 generally correspond to $cm$ size of $a_{max}$ when q=3.5 is assumed in the dust size distribution $n(a)\propto a^{-q}$.

Estimating $a_{max}$ from spectral indices is not accurate when the disk is optically thick and/or dust scattering cannot be neglected ((cite: Liu2019ApJ...877L..22L)). Therefore, we used the azimuthal profiles of the inner ring and the outer ring in Band 3 and 6 to perform fittings, hoping to understand the dust distributions of the rings. We use the method developed by (cite: Carrasco-Gonzalez2019-mq) and (cite: Sierra2020-zs). When the dust scattering is taken into account, the intensity of the disk can be written as:

$$\begin{equation}
    I_\nu=B_\nu(T)[(1-\mathrm{exp}(-\tau_\nu/\mu))+\omega_\nu F(\tau_\nu,\omega_\nu)]
    \label{intensity}
\end{equation}$$

here $\tau_\nu=\Sigma_d (\kappa_\nu+\sigma_\nu)$ is the optical depth. $\Sigma_d$ is the dust surface density, $\kappa_\nu$, and $\sigma_\nu$ represents the absorption and scattering coefficient respectively. Note that for the scattering coefficient, we use the effective scattering coefficient defined as $\sigma^{eff}_{\nu}=(1-g_\nu)\sigma_\nu$, here $g_\nu$ is the asymmetry parameter. $\omega_\nu=\sigma_\nu/(\kappa_\nu+\sigma_\nu)$ is the dust albedo, $\mu=cos(i)$ is the cosine of the inclination angle $i=15^\circ$. $F(\tau_\nu,\omega_\nu)$ is defined as:

$$\begin{equation}
    F(\tau_\nu,\omega_\nu)=\frac{1}{\mathrm{exp}(-\sqrt{3}\epsilon_\nu \tau_\nu)(\epsilon_\nu-1)-(\epsilon_\nu+1)}\times[\frac{1-\mathrm{exp}(-(\sqrt{3}\epsilon_\nu+1/\mu)\tau_\nu)}{\sqrt{3}\epsilon_\nu\mu+1}+\frac{\mathrm{exp}(-\tau_\nu/\mu)-\mathrm{exp}(-\sqrt{3}\epsilon_\nu\tau_\nu)}{\sqrt{3}\epsilon_\nu\mu-1}]
\end{equation}$$

here $\epsilon_\nu=\sqrt{1-\omega_\nu}$. We assumed q=3.5 in our fitting, then equation [\[intensity\]](#intensity) will depend on only three parameters: $T_d$, $\Sigma_d$ and $a_{max}$. And since we only have two bands, we fixed the dust temperature at the inner ring (at 0.$\ensuremath{''}$21) and the outer ring (at 0.$\ensuremath{''}$41) so that there are only two free parameters. By assuming that the temperature of grown dust is equal to the disk mid-plane temperature, we calculated the dust temperature using Equation (3) in (cite: Huang2018-sa), which approximates the mid-plane temperature profile of a passively heated, flared disk in radiative equilibrium. The DSHARP dust optical constants ((cite: Birnstiel2018-jb)) are employed in our fitting. In details, we explored a series of $\Sigma_d$ and $a_{max}$ values, calculating the flux $I_{\nu,model}$ in different wavelengths using equation [\[intensity\]](#intensity), then derived the probability via the following equation:

$$\begin{equation}
    p\propto\mathrm{exp}(-\sum_{\nu}(I_{\nu}-I_{\nu,model})/2\sigma_\nu^2)
\end{equation}$$

Here $\sigma_\nu$ is the standard deviation of the azimuthal profiles. The explored parameter space is a logarithmically spaced grid between $10\mu m\leqslant a_{max} \leqslant 1 cm$ and $0.001 g/cm^2 \leqslant \Sigma_d \leqslant 10 g/cm^2$, each divided into 1000 bins.

The fitting result is shown in Figure [10](#fig:fig6). At each position, the fittings generally lead to two families of probable solutions, one with $a_{max}\lesssim$300 $\mu m$ and a higher surface density (small dust solution), and the other with $a_{max}\gtrsim1 mm$ and lower surface density (large dust solution). Such a degeneracy in the SED fittings is also pointed out by the recent case studies on the CW Tau disk ((cite: Ueda2022arXiv220316236U)). We also draw the positions of the clumps in the images (dashed line). Generally, for the large dust solutions, the clumps correspond to larger solutions than other places, while for the small dust solutions, the clumps correspond to smaller solutions.

Theoretical studies favor the large dust solutions at the peaks of asymmetric structures and clumps; however, from the observational view, it is hard to judge which solution is proper. The actual case could be a mixture of these two solutions: in some places, the large-dust solution is proper, while in other places, the small-dust solution is proper. Future observations from longer wavelengths or polarization observations can help distinguish these possibilities.

## Potential Planet

(cite: Muro-Arena2020) suggested that a potential planet could cause the gap between the inner and outer rings. They suggested that the planet favors a low mass ($\sim 1M_{Jup}$) based on the simulation results of (cite: De_Juan_Ovelar2013-zg) after comparing the ring location in the near-infrared band and sub-millimeter band. Keck L-band (3.426–4.126 $\mu$m) observations have excluded companions more massive than 13 $M_{Jup}$. In the results of (cite: De_Juan_Ovelar2013-zg), the simulated sub-millimeter image of the disk does not show a bright inner ring, which is different from the observation. Therefore, based on our observation data, we consider re-constraining the potential planet mass. In our Band 6 data, the gap size is about 0.$\ensuremath{''}$06, and its center is about 0.$\ensuremath{''}$31, so we tried to constrain the potential planet mass from the disk gap sizes. From our observation result, it is hard to judge whether the planet opens a gas gap, so that we will discuss them separately. If the planet only opens a dust gap, the gap size will be proportional to the planet Hill radius $R_H$ (cite: Lodato2019-nq):

$$\begin{equation}
    R_H=(\frac{M_p}{3M_*})^{1/3}R_{gap}
    \label{Hill_radius}
\end{equation}$$

and the planet’s mass can be derived by:

$$\begin{equation}
    M_{p,dust}(R_{gap})=M_*(\frac{\Delta_{gap}}{CR_{gap}})^3
    \label{dust_gap}
\end{equation}$$

here $\Delta_{gap}$ and $R_{gap}$ represent the width and location (radius) of the gap, respectively. $4.5<C<7$ is the proportional constant (cite: Rosotti2016-zs). Based on this, we can estimate the planet which opens the gap should be about 12-44$M_\oplus$.

As for the case that the planet opens a dust gap and a gas gap, we assume that the gas gap is equal to the dust gap, then according to the empirical equation given by (cite: Kanagawa2016-cf), the planet mass should be:

$$\begin{equation}
    M_{p,gas}(R_{gap})=2.1\times10^{-3}M_*(\frac{\Delta_{gap}}{R_{gap}})^2(\frac{h_{gap}/R_{gap}}{0.05})^{3/2}(\frac{\alpha}{10^{-3}})^{1/2}
    \label{gas_gap}
\end{equation}$$

here $h_{gap}$ and $\alpha$ represent the scale height and viscosity at the gap, respectively. The aspect ratio $h_{gap}/R_{gap}$ can be derived as:

$$\begin{equation}
    h_{gap}/R_{gap}=c_k/\Omega
    \label{aspect_ratio}
\end{equation}$$

here $c_k$ is the sound speed and $\Omega$ is the angular velocity. Using Equation (3) in (cite: Huang2018-sa), the temperature at $0.\ensuremath{''}31$ is about 31 K, and then we can derive the aspect ratio here is about 0.06. As for the viscosity $\alpha$, since the asymmetric structure we detected could be the result of RWI vortices, which requires low viscosity ($\alpha\lesssim10^{-4}$) (cite: Regaly2012-zz) for the vortices to survive. So we assume $\alpha\sim10^{-4}-10^{-3}$, and the result will be about 18-58 $M_\oplus$ (0.06-0.18 $M_{Jup}$).

The criteria to judge if the planet opens a gas gap is to see if the planet reaches pebble isolation mass (cite: Morbidelli2012-dw; Lambrechts2014-fi; Birnstiel2018-jb). Planet mass below pebble isolation mass could not or can only open a shallow gas gap. According to equations 10 and 11 in (cite: Birnstiel2018-jb), the pebble isolation mass for SR 21 could be about 30-50 $M_\oplus$; thus, one gas gap opened by the planet may exist. Confirming the gas gap size using sub-millimeter observations in the future could help better constrain the planet’s mass.

Planets excite density waves, which may look like spiral arms in scattered light (cite: Dong2015-bh). However, the density waves excited by a sub-Saturn mass planet are probably too weak to be visible in current observations, which typically require (multi-)Jupiter mass planets (cite: Dong2017-ps). In addition, if the two spirals identified in (cite: Muro-Arena2020) are produced by one planet, their large azimuthal separation suggests a multi-$M_{Jup}$ planet too (cite: Fung15). Thus, the predicted gap-opening planet cannot explain the spiral arm-like features seen in (cite: Muro-Arena2020). While the gravitational instability may also produce spiral arms in scattered light (cite: dong15giarm), it is unlikely the cause of the spirals in this case (Section 3.2).

We propose that the most prominent spiral arm-like feature identified in the SPHERE observation, Spiral 1 (Figure [3](#fig:fig4)), could be the scattered light counterpart of the Inner Arc, which itself is a dust-trapping vortex. As shown in (cite: Marr22), vortices appear as arcs in scattered light, which may look like spirals in inclined disks. The excellent position coincidence between Spiral 1 and Inner Arc supports this hypothesis. In addition, vortices can cast shadows in the outer ring due to their elevated surface height. Meanwhile, the region outside Spiral 1 in scattered light appears fainter than other regions at the same radius, matching the shadow prediction as well. This could help explain why the spiral arm in SR 21 looks so different from other targets.

There are some caveats in this estimation, though. Firstly, the gap may be triggered by just one planet inside the central cavity. In the simulation work done by (cite: Gomes2015-qy), they showed that one planet inside the central cavity of the transitional disk could successfully induce two vortices and the gap between them. However, considering the planet’s orbit is hard to constrain, it is hard to estimate its mass under this scenario. Secondly, our calculation is aspect-ratio dependent, and the aspect-ratio is dependent on the temperature of the disk middle plane. The result will also change if the actual temperature deviates from Equation (3) in (cite: Huang2018-sa). The estimation result can be improved by a better understanding the temperature profile.

# Conclusions

The protoplanetary disk around SR 21 holds many characteristics that could help us understand disk evolution and planet formation. By combining observation results in different wavelengths, the main conclusions are listed below:

1\. Based on the ALMA Band 3 and Band 6 dust continuum images, the protoplanetary disk around SR 21 under sub-millimeter bands consists of two rings with a radius of about 0.$\ensuremath{''}$14-0.$\ensuremath{''}$28 and 0.$\ensuremath{''}$34-0.$\ensuremath{''}$48. Three crescent-like asymmetric structures, one in the inner ring and two in the outer ring, are detected, while CO isotopologues images of Band 6 show that the emissions are mainly inside the inner ring ($\leqslant0.\ensuremath{''}28$), which could be due to the foreground absorption; the $^{12}$CO gas structure in the north is more extended than the south, this may indicate that the gas distribution in the disk is asymmetric;

2\. The asymmetric structures in the outer ring are elongated, and their azimuthal profiles are asymmetric, and in Band 3 data, some small clumps in the rings may exist. Features like off-center peaks of the asymmetric structures indicate that the asymmetric structures are elongated due to the interaction of a slow-growing planet rather than dead zone, as (cite: Hammer2017-dq; Hammer2019) suggested;

3\. The fitting using Band 3 and Band 6 data suggests two solutions of the maximum dust sizes in the disk: small dust ($a_{max}\lesssim$300 $\mu m$) solution and large dust ($a_{max}\gtrsim 1 mm$) solution. Future observations from longer wavelengths or polarization observations can help distinguish them;

4\. According to the gap size and the derived aspect ratio, the potential planet in the gap between the inner and outer rings should reach 18-58$M_\oplus$ corresponding to the viscosity $\alpha\sim10^{-4}-10^{-3}$. Planet at this mass is hard to trigger visible spiral arms in the near-infrared band, and we propose that the spiral arm-like features identified in the SPHERE observation could just be the scattered light counterpart of the Inner Arc.

# Acknowledgments

We would like to thank the insightful and constructive comments from an anonymous referee that greatly improved the quality of this manuscript. This paper makes use of the following ALMA data: ADSJAO.ALMA#2018.1.00689.S and #2017.1.00884.S. ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), MOST, and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under a cooperative agreement by Associated Universities, Inc. We also thank Prof. Pinilla, Paola for sharing her reduced ALMA Band 3 data, and Anibal Sierra for sharing his code and useful discussions. This work was supported by NAOJ ALMA Scientific Research Grant Numbers 2019-12A. M.T. is supported by JSPS KAKENHI grant Nos.18H05442,15H02063,and 22000005. Y.H. is supported by the Jet Propulsion Laboratory, California Institute of Technology, under a contract with the National Aeronautics and Space Administration (80NM0018D0004).

# Facilities

ALMA

# Software

CASA

natexlab

(ref: Andrews2011) Andrews, S. M., Wilner, D. J., Espaillat, C., et al. 2011, ApJ, 732, 42, doi: [`10.1088/0004-637X/732/1/42`](http://doi.org/10.1088/0004-637X/732/1/42)

(ref: Ataiee2013) Ataiee, S., Pinilla, P., Zsom, A., et al. 2013, A&A, 553, 1, doi: [`10.1051/0004-6361/201321125`](http://doi.org/10.1051/0004-6361/201321125)

(ref: Barge1995-nw) Barge, P., & Sommeria, J. 1995, Astron. Astrophys., 295, L1

(ref: Baruteau2015-gj) Baruteau, C., & Zhu, Z. 2015, MNRAS, 458, 3927

(ref: Beuzit2019-um) Beuzit, J.-L., Vigan, A., Mouillet, D., et al. 2019, A&A, 631, A155

(ref: Birnstiel2018-jb) Birnstiel, T., Dullemond, C. P., Zhu, Z., et al. 2018, ApJL, 869, L45

(ref: Boehler2017) Boehler, Y., Weaver, E., Isella, A., et al. 2017, ApJ, 840, 60, doi: [`10.3847/1538-4357/aa696c`](http://doi.org/10.3847/1538-4357/aa696c)

(ref: Carrasco-Gonzalez2019-mq) Carrasco-González, C., Sierra, A., Flock, M., et al. 2019, ApJ, 883, 71

(ref: Casassus2013-nm) Casassus, S., Van Der Plas, G., Sebastian Perez, M. S. P., et al. 2013, Nature, 493, 191

(ref: Cazzoletti2018-gi) Cazzoletti, P., Van Dishoeck, E. F., Pinilla, P., et al. 2018, A&A, 619, 1

(ref: De_Juan_Ovelar2013-zg) de Juan Ovelar, M., Min, M., Dominik, C., et al. 2013, A&A, 560, A111

(ref: Dong2017-ps) Dong, R., & Fung, J. 2017, ApJ, 835, 38

(ref: dong15giarm) Dong, R., Hall, C., Rice, K., & Chiang, E. 2015, ApJL, 812, L32, doi: [`10.1088/2041-8205/812/2/L32`](http://doi.org/10.1088/2041-8205/812/2/L32)

(ref: Dong2015-bh) Dong, R., Zhu, Z., Rafikov, R. R., & Stone, J. M. 2015, ApJL, 809, L5

(ref: dong12) Dong, R., Rafikov, R., Zhu, Z., et al. 2012, ApJ, 750, 161, doi: [`10.1088/0004-637X/750/2/161`](http://doi.org/10.1088/0004-637X/750/2/161)

(ref: Dong2018-ve) Dong, R., Liu, S.-Y., Eisner, J., et al. 2018, ApJ, 860, 124

(ref: Facchini2017-hy) Facchini, S., Birnstiel, T., Bruderer, S., & van Dishoeck, E. F. 2017, A&A, 605, A16

(ref: Follette2013) Follette, K. B., Tamura, M., Hashimoto, J., et al. 2013, ApJ, 767, 10, doi: [`10.1088/0004-637X/767/1/10`](http://doi.org/10.1088/0004-637X/767/1/10)

(ref: Francis2020-jv) Francis, L., & van der Marel, N. 2020, ApJ, 892, 111

(ref: Fu2014-zt) Fu, W., Li, H., Lubow, S., & Li, S. 2014, ApJL, 788, L41

(ref: Fukagawa2013-da) Fukagawa, M., Tsukagoshi, T., Momose, M., et al. 2013, PASJ, 65, L14

(ref: Fung15) Fung, J., & Dong, R. 2015, ApJL, 815, L21, doi: [`10.1088/2041-8205/815/2/L21`](http://doi.org/10.1088/2041-8205/815/2/L21)

(ref: GAIA2018) Gaia Collaboration, Brown, A. G. A., Vallenari, A., et al. 2018, A&A, 616, A1, doi: [`10.1051/0004-6361/201833051`](http://doi.org/10.1051/0004-6361/201833051)

(ref: Garufi2018-ew) Garufi, A., Benisty, M., Pinilla, P., et al. 2018, Astron. Astrophys. Suppl. Ser., 620, A94

(ref: Gomes2015-qy) Gomes, A. L., Klahr, H., Uribe, A. L., Pinilla, P., & Surville, C. 2015, Astrophys. J., 810, 94

(ref: Hammer2017-dq) Hammer, M., Kratter, K. M., & Lin, M.-K. 2017, MNRAS, 466, 3533

(ref: Hammer2019) Hammer, M., Pinilla, P., Kratter, K. M., & Lin, M.-K. 2019, MNRAS, 482, 3609, doi: [`10.1093/mnras/sty2946`](http://doi.org/10.1093/mnras/sty2946)

(ref: Herczeg2014-dm) Herczeg, G. J., & Hillenbrand, L. A. 2014, ApJ, 786, 97

(ref: Huang2018-sa) Huang, J., Andrews, S. M., Dullemond, C. P., et al. 2018, ApJL, 869, L42

(ref: Kanagawa2016-cf) Kanagawa, K. D., Muto, T., Tanaka, H., et al. 2016, PASJ, 68

(ref: Kim2020-qi) Kim, S., Takahashi, S., Nomura, H., et al. 2020, Astrophys. J., 888, 72

(ref: Klahr1997-qv) Klahr, H. H., & Henning, T. 1997, Icarus, 128, 213

(ref: Kraus2017-uf) Kraus, S., Kreplin, A., Fukugawa, M., et al. 2017, ApJL, 848, L11

(ref: Krijt2020-oe) Krijt, S., Bosman, A. D., Zhang, K., et al. 2020, ApJ, 899, 134

(ref: Lambrechts2014-fi) Lambrechts, M., Johansen, A., & Morbidelli, A. 2014, A&A, 572, A35

(ref: Li2020-pt) Li, Y.-P., Li, H., Li, S., et al. 2020, ApJL, 892, L19

(ref: Liu2019ApJ...877L..22L) Liu, H. B. 2019, ApJL, 877, L22, doi: [`10.3847/2041-8213/ab1f8e`](http://doi.org/10.3847/2041-8213/ab1f8e)

(ref: Lodato2019-nq) Lodato, G., Dipierro, G., Ragusa, E., et al. 2019, MNRAS, 486, 453

(ref: Mangum2015-ud) Mangum, J. G., & Shirley, Y. L. 2015, PASP, 127, 266

(ref: Marr22) Marr, M., & Dong, R. 2022, ApJ, 930, 80, doi: [`10.3847/1538-4357/ac63ab`](http://doi.org/10.3847/1538-4357/ac63ab)

(ref: Miotello2018-lt) Miotello, A., Facchini, S., van Dishoeck, E. F., & Bruderer, S. 2018, Probing the protoplanetary disk gas surface density distribution with $^{13}$CO emission

(ref: Miotello2016-gw) Miotello, A., van Dishoeck, E. F., Kama, M., & Bruderer, S. 2016, A&A, 594, A85

(ref: Morbidelli2012-dw) Morbidelli, A., & Nesvorny, D. 2012, A&A, 546, A18

(ref: Muro-Arena2020) Muro-Arena, G. A., Ginski, C., Dominik, C., et al. 2020, A&A, 636, L4, doi: [`10.1051/0004-6361/202037656`](http://doi.org/10.1051/0004-6361/202037656)

(ref: Perez2014) Pérez, L. M., Isella, A., Carpenter, J. M., & Chandler, C. J. 2014, ApJL, 783, doi: [`10.1088/2041-8205/783/1/L13`](http://doi.org/10.1088/2041-8205/783/1/L13)

(ref: Perez2018-rm) Pérez, L. M., Benisty, M., Andrews, S. M., et al. 2018, ApJL, 869, L50

(ref: Qi2011-fb) Qi, C., D’Alessio, P., Öberg, K. I., et al. 2011, ApJ, 740, 84

(ref: Ragusa2017-is) Ragusa, E., Dipierro, G., Lodato, G., Laibe, G., & Price, D. J. 2017, MNRAS, 464, 1449

(ref: Regaly2012-zz) Regály, Z., Juhász, A., Sándor, Z., & Dullemond, C. P. 2012, Mon. Not. R. Astron. Soc., 419, 1701

(ref: Rosotti2016-zs) Rosotti, G. P., Juhasz, A., Booth, R. A., & Clarke, C. J. 2016, MNRAS, 459, 2790

(ref: Rosotti2020-rk) Rosotti, G. P., Benisty, M., Juhász, A., et al. 2020, MNRAS, 491, 1335

(ref: Sault1995) Sault, R. J., Teuben, P. J., & Wright, M. C. H. 1995, in Astronomical Society of the Pacific Conference Series, Vol. 77, Astronomical Data Analysis Software and Systems IV, ed. R. A. Shaw, H. E. Payne, & J. J. E. Hayes, 433

(ref: Sierra2020-zs) Sierra, A., & Lizano, S. 2020, ApJ, 892, 136

(ref: 1964ApJ...139.1217T) Toomre, A. 1964, ApJ, 139, 1217, doi: [`10.1086/147861`](http://doi.org/10.1086/147861)

(ref: Ueda2022arXiv220316236U) Ueda, T., Kataoka, A., & Tsukagoshi, T. 2022, arXiv e-prints, arXiv:2203.16236. [`https://arxiv.org/abs/2203.16236`](https://arxiv.org/abs/2203.16236)

(ref: VanderMarel2013) van der Marel, N., van Dishoeck, E. F., Bruderer, S., et al. 2013, Science, 340, 1199, doi: [`10.1126/science.1236770`](http://doi.org/10.1126/science.1236770)

(ref: Van_der_Marel2021-vr) van der Marel, N., Birnstiel, T., Garufi, A., et al. 2021, ApJ, 161, 33

(ref: 2017SPIE10400E..15V) van Holstein, R. G., Snik, F., Girard, J. H., et al. 2017, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 10400, Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, 1040015, doi: [`10.1117/12.2272554`](http://doi.org/10.1117/12.2272554)

(ref: 2020A&A...633A..64V) van Holstein, R. G., Girard, J. H., de Boer, J., et al. 2020, A&A, 633, A64, doi: [`10.1051/0004-6361/201834996`](http://doi.org/10.1051/0004-6361/201834996)

(ref: 1999RPPh...62..143W) Wilson, T. L. 1999, Reports on Progress in Physics, 62, 143, doi: [`10.1088/0034-4885/62/2/002`](http://doi.org/10.1088/0034-4885/62/2/002)

(ref: Yoshida2022-jd) Yoshida, T. C., Nomura, H., Furuya, K., Tsukagoshi, T., & Lee, S. 2022, ApJ, 932, 126

(ref: Zhu2014) Zhu, Z., & Stone, J. M. 2014, ApJ, 795, doi: [`10.1088/0004-637X/795/1/53`](http://doi.org/10.1088/0004-637X/795/1/53)

</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[3].assumptions[0].evidence[0]",
  "value": "Power-law dust size distribution index q = 3.5; DSHARP dust optical constants; inclination i = 15 deg; dust temperature fixed to passively heated flared disk mid-plane temperature profile of Huang et al. (2018).",
  "failed_quote": "We assumed q=3.5 in our fitting, then equation [intensity] will depend on only three parameters: $T_d$, $\\Sigma_d$ and $a_{max}$."
 },
 {
  "path": "analysis_steps[3].fitting.evidence[0]",
  "value": "Logarithmically spaced 1000x1000 grid search evaluating Gaussian likelihood p ∝ exp(-sum((I_nu - I_nu,model)/2*sigma_nu^2))",
  "failed_quote": "In details, we explored a series of $\\Sigma_d$ and $a_{max}$ values, calculating the flux $I_{\\nu,model}$ in different wavelengths using equation [intensity], then derived the probability via the following equation:"
 }
]
```

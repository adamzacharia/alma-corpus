# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2018ApJ...867L..29W\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# Revealing environmental dependence of molecular gas content in a distant X-ray cluster at $\MakeLowercase{z}=2.51$

## Abstract

We present a census of the molecular gas properties of galaxies in the most distant known X-ray cluster, CLJ1001, at z=2.51, using deep observations of CO(1-0) with JVLA. In total 14 cluster members with $M_{*} > 10^{10.5} M_{\odot}$ are detected, including all the massive star-forming members within the virial radius, providing the largest galaxy sample in a single cluster at $z > 2$ with CO(1-0) measurements. We find a large variety in the gas content of these cluster galaxies, which is correlated with their relative positions (or accretion states), with those closer to the cluster core being increasingly gas-poor. Moreover, despite their low gas content, the galaxies in the cluster center exhibit an elevated star formation efficiency (SFE=SFR/$M_{\rm gas}$) compared to field galaxies, suggesting that the suppression on the SFR is likely delayed compared to that on the gas content. Their gas depletion time is around $t_{\rm dep} \sim 400$ Myrs, comparable to the cluster dynamical time. This implies that they will likely consume all their gas within a single orbit around the cluster center, and form a passive cluster core by $z\sim2$. This result is one of the first direct pieces of evidence for the influence of environment on the gas reservoirs and SFE of $z > 2$ cluster galaxies, thereby providing new insights into the rapid formation and quenching of the most massive galaxies in the early universe.

# Introduction

Galaxy clusters in the present-day universe are dominated by a population of massive, and quiescent galaxies in their center (cite: Dressler:1997). The formation mechanisms of these massive galaxies and the influence environment plays in this process remain open questions. These issues are difficult to address in the local universe, as most of the massive galaxies have already been in place for 10 Gyrs and signatures of their formation history have been largely erased. Contrary to mature clusters at low redshifts, a significant population of (proto)clusters with active star formation has been found at $z > 2-4$, the peak formation epoch of massive cluster galaxies (cite: Thomas:2005). With a large number of massive star-forming galaxies (SFGs) in a cluster-like environment, these structures provide ideal laboratories to explore the environmental dependence of massive galaxy formation.

The different properties, e.g., star formation rates (SFR), of galaxies in $z > 2$ (proto-)clusters and field have been extensively studied. While a higher fraction of quiescent galaxies in dense environments is well established, no significant difference has been found on the average SFR of star-forming galaxies, i.e., the normalization of the star-forming main sequence (MS), at $z \sim 2$ (cite: Koyama:2013; Shimakawa:2017). A few studies show an enhanced fraction of starburst galaxies in (proto-)clusters at both the bright (cite: WangT:2016b; Casey:2016) and faint end of the stellar mass function (cite: Hayashi:2016), however, statistical samples are still required to confirm these findings. Overall, this lack of strong environmental dependence of star formation may indicate that there is significant delay between the first infall of cluster galaxies and substantial reduction in their star formation rates (SFR), which likely only take place close to the cluster core (cite: Wetzel:2013).

While it is not yet fully clear how SFR of star-forming galaxies depends on environment, ample evidence exists for the deficit of cold gas, the fuel of star formation, for galaxies in dense environments (cite: Boselli:2006). Both neutral hydrogen (HI), molecular gas, and even dust, in cluster galaxies can be severely impacted by their local environment through, e.g., ram-pressure stripping and tidal stripping, at least in the vicinity of the cluster core (cite: Cortese:2010; Davis:2013; Jachym:2014; Jachym:2017). On the other hand, while pioneering studies on molecular gas content in high-z clusters ($z \sim 1.5-2$) have been recently performed, there is still no consensus on the influence of environment on galaxies’ gas content (cite: Aravena:2012; Wagg:2012; Casasola:2013; Stach:2017; Noble:2017; Coogan:2018). This is mainly driven by the limited number of detections, which is often biased towards the most gas-rich members except for a few cases (cite: Rudnick:2017; Hayashi:2017). In addition, most of these targeted clusters appear to be already dominated by massive quiescent galaxies in the core, but little is known about their gas and star formation properties during the epoch of their formation/quenching. Though studies of molecular gas properties in dense environments exist at $z > 2$, they only detected some of the brightest member galaxies (cite: Tadaki:2014; LeeM:2017; Dannerbauer:2017), inhibiting a comprehensive understanding of the gas content of cluster galaxies.

In this paper, we present a census of molecular gas properties of 14 massive SFGs in the most distant known X-ray cluster, CLJ1001, at $z=2.51$ (cite: WangT:2016b), based on CO(1-0) observations with JVLA. CLJ1001 is estimated to have total mass of $M \sim10^{13.9\pm0.2} M_{\odot}$ and virial radius of $R_{\rm 200c} \sim$ 340 kpc based on its X-ray emission and velocity dispersion (W16). Our recent deep narrow-band (NB) imaging further reveals a large number of H$\alpha$-emitters at $z=2.51$ in the cluster, providing further evidence that this is a different structure with respect to the protocluster/large-scale structure found, in the same region of the sky, by (cite: Casey:2015) at $z = 2.47$. Despite its extended X-ray emission, this cluster is dominated by massive SFGs in the core, which are all detected in CO(1-0), allowing us, for the first time, to probe the gas content and star formation efficiency for a complete sample of massive cluster members (down to $M_{*} > 10^{10.5} M_{\odot}$) at $z > 2$. Throughout the paper, we assume cosmological parameters of $H_{0}$ = 70 km s$^{-1}$ Mpc$^{-1}$, $\Omega_{M}$ = 0.3, and $\Omega_{\Lambda}$ = 0.7. A (cite: Chabrier:2003) initial mass function is adopted to derive stellar masses and SFRs.

# Observations

![image](fig1a.pdf) ![image](fig1b.pdf)

## JVLA CO(1-0) observations

Our JVLA observations of CLJ1001 were performed in December 2015 under the program 15B-290 (PI: Tao Wang). Part of the data has been already presented in W16 (including example CO(1-0) spectra), which were only used to confirm cluster members. In detail, the observations were carried out in the Ka-band with the D configuration, with an effective frequency coverage of 32.2-33.59 GHz, corresponding to $z\sim 2.43-2.58$ for CO(1-0). The observations were done in excellent weather conditions with Precipitable Water Vapor as low as 2.0 mm and wind speed 0.3-1.5 km/s, therefore the achieved system temperature ($T_{\mathrm{sys}}$) is about or even below 40 K, while typical $T_{\mathrm{sys}}$ is about 50 K at Ka band in winter. The full width half power (FWHP) size of the primary beam is 1.37$\ensuremath{'}$ at 32.878 GHz (z=2.506 for CO(1-0)). We observed 3C147 for flux calibration during the full observations, and a point source J1024-0052 near our target for phase calibration during each scan loop (every $\sim$8 mins). The total integration time is $\sim$13 hours. The data were reduced using the Common Astronomy Software Application (CASA) package (cite: McMullin:2007) with a standard pipeline. We chose 0.5$^{\prime\prime}$ pixels and a spectral resolution of 30 km s$^{-1}$ with a natural weighting scheme for imaging. Image deconvolution was performed with a CLEAN threshold of 3$\sigma$ of each cube. The resulting data cube has synthesized beam size of $\sim2.88^{\prime\prime} \times 2.52^{\prime\prime}$ with a rms of $\sim 33-40~\mu$Jy beam$^{-1}$ per channel at the phase center.

![](fig2.pdf)

## Subaru/MOIRCS narrow-band imaging

To have a complete census of cluster (star-forming) members, we have recently conducted a deep narrow-band (NB) survey towards CLJ1001 with Subaru/MOIRCS. The NB survey employed the “CO” filter centered at 2.3$\mu$m to identify H$\alpha$ emitters at $z=2.49-2.52$, combined with the already available deep $K_{s}$-band data in COSMOS from the UltraVista survey (cite: McCracken:2012; Muzzin:2013a; Laigle:2016). With 4.4 hours of integration, we have detected 49 H$\alpha$ emitters with line flux down to 1.5 $\times 10^{-17}$ erg s$^{-1}$ cm$^{-2}$. This corresponds to a dust-free SFR of $\sim$ 5 $M_{\odot}$ yr$^{-1}$ at $z$=2.51 (cite: Kennicutt:1998). Details of data reduction and star formation properties of these H$\alpha$ emitters will be discussed in a forthcoming paper. Here we only use their positions to search for CO(1-0) line emissions.

## Extraction of CO(1-0) emitters

We extract CO(1-0) spectra at the position of the cluster members (H$\alpha$-emitters) out to $2 \times$ the full width half power (FWHP) of the primary beam (PB). This approach allows us to detect sources with fainter fluxes and with higher fidelity than a blind search. In total 14 H$\alpha$-emitters are detected with S/N $>$ 3 (Figure [1](#Fig:sky)). We measured the CO(1-0) line fluxes for each object by running a 2-D Gaussian fit with CASA (IMFIT) on the velocity-integrated (moment-0) map. The velocity range used to create the moment-0 map of each object was determined so to maximize the signal-to-noise of the detection. During this process the spatial position of the targets was kept fixed based on the coordinates found from the HST/F160W (if available) or NB ancillary images, in order to minimize false detections due to noise fluctuations. 13 out of these 14 galaxies (except ID-14) are also covered by our ALMA band-3 observations, and they are all detected in CO(3-2) at roughly the same velocity (Wang et al., in preparation). In the case of low S/N with CO(1-0), CO(3-2) data is combined with CO(1-0) to determine the velocity range of the line emission. For a sanity check, we have also measured directly their total fluxes in the *uv*-plane with GILDAS[^1], a procedure that gives consistent results. The measured integrated CO(1-0) line intensities, after primary beam correction, are listed in Table [\[Tab:measurements\]](#Tab:measurements). The 14 detections include all but one massive galaxy (ID-131651 in W16) with $M_{*} > 10^{10.5} M_{\odot}$ within the PB, which is classified as a passive galaxy in W16 based on its rest-frame colors, suggesting that the H$\alpha$ emission mostly likely originates from an (radio)AGN, as further supported by the non-detection of CO(1-0).

## Molecular gas masses from CO(1-0)

The use of CO(1-0) avoids the uncertainty in the CO excitation, and serves as the most extensively used way in obtaining the total molecular gas mass, $M(H_{2})$. The conversion involves the integrated CO emission intensity ($L_{\mathrm{CO(1-0)}}^{\prime}$) and a conversion factor $\alpha_{\rm CO}$ (cite: Bolatto:2013), through $M(H_{2}) = \alpha_{\rm CO} L_{\rm CO}^{\prime}$, with the CO line luminosity $L_{\mathrm{CO(1-0)}}^{\prime}$ derived following (cite: Solomon:2005). We determine $\alpha_{\rm CO}$  for the cluster galaxy sample following (cite: Genzel:2015) and (cite: Tacconi:2018). The same mass-metallicity relation used in (cite: Genzel:2015) is also applied to determine the metallicity for the CO-detected galaxies in our sample, which is close to solar given their large stellar masses. As a result, the derived $\alpha_{\rm CO}$ is close to the Milky value for this sample (Table [\[Tab:measurements\]](#Tab:measurements)).

# Results

![](fig3.pdf)

![](fig4.pdf)

## Star formation efficiency

The combination of the CO line luminosity ($L_{\mathrm{CO(1-0)}}^{\prime}$), tracing total molecular gas, and the total infrared luminosity ($L_{\rm IR}$), tracing newly formed stars, provides a crucial constraint on the star formation efficiency (SFE), with $L_{\rm IR}$/$L_{\mathrm{CO(1-0)}}^{\prime}$$\propto$ SFR/$M_{\rm gas} \equiv$ SFE. Moreover, the use of $L_{\rm IR}$/$L_{\mathrm{CO(1-0)}}^{\prime}$ as an approximation of SFE allows us not have to account for the different prescriptions for the CO-to-H$_{2}$ conversion factor, enabling direct comparisons between different samples. As shown in W16 (cite: Bussmann:2015), five cluster members are detected at 870 $\mu$m with ALMA, for which we derive their infrared luminosities, $L_{\rm IR}$, by fitting the full infrared SED. For the other galaxies without 870$\mu$m detection, we derive $L_{IR}$ based on their 24 $\mu$m fluxes (cite: Muzzin:2013a) and 3 GHz (cite: Smolcic:2017) radio continuum by using the average infrared SED templates for galaxies at $z\sim 2.5$ (cite: Schreiber:2018a) and FIR-radio relation (cite: Delhaize:2017). We have verified this approach through comparisons of IR-SED derived and 3 GHz derived $L_{\rm IR}$ for four out of the five ALMA-detected sources (excluding ID-4, which is a radio AGN), which are in good agreement. Only one source (ID-12) does not have either 24$\mu$m or 3 GHz detections, for which we derive $L_{\rm IR}$ based on its SFR estimated from extinction-corrected H$\alpha$ following (cite: Kennicutt:1998). The best-estimated $L_{\rm IR}$ for cluster members are listed in Table. [\[Tab:measurements\]](#Tab:measurements).

Figure [2](#Fig:SFE) presents the comparison of $L_{\rm IR}$ and $L_{\mathrm{CO(1-0)}}^{\prime}$ \
between member galaxies in CLJ1001 and other galaxy populations in high-z clusters ($z \sim 1.5-2$) and field. The CLJ1001 galaxies exhibit a large variety in their SFE as traced by $L_{\rm IR}$/$L_{\mathrm{CO(1-0)}}^{\prime}$, including members with high, starburst-like SFE and also members with SFE even below MS-like galaxies. To examine whether this large variety in SFE is solely driven by their different star formation modes (starburst versus MS), we further show the variation of $L_{\rm IR}$/$L_{\mathrm{CO(1-0)}}^{\prime}$ as a function of their distance to the MS, which is defined as $\Delta$MS = SFR/SFR$_{\rm MS}$ with SFR$_{\rm MS}$ for each galaxy derived using the MS relation at z=2.5 (cite: Schreiber:2015) at the same stellar mass (the right panel of Figure [2](#Fig:SFE)), which is nearly identical to the MS relation used in (cite: Tacconi:2018). Consistent with field galaxies, a general trend towards increasing SFE with enhanced star formation activity (relative to the MS) is observed in CLJ1001. However, in contrast to field galaxies, a large dispersion of SFE is present for these cluster galaxies. Most prominently, a population of cluster galaxies with MS-like SFR ($|\Delta {\rm MS}| < 0.5$) exhibit significantly different SFE compared to field galaxies. This suggests that the large variation in SFE for these cluster galaxies is not driven by the variation in SFR, instead, some other mechanisms, most likely related to the dense environment, may play an important role.

## Clustercentric radius dependence of star formation and molecular gas content

In order to gain further insights into the origin of the gas and star formation properties of the cluster galaxies, we examine the relation between these properties and their positions in the cluster. Specifically, we employ the line-of-sight velocity versus clustercentric radius phase-space diagram to illustrate the relative distribution of member galaxies within the cluster. The phase-space diagram characterizes the accretion state of cluster member galaxies, which minimizes projection effects of their 2D positions with respect to the cluster center (cite: Noble:2013). In this diagram, galaxies that are recently accreted to the cluster tend to have large relative velocities and/or large clustercentric radius, which are offset from the central virialized region. As shown in the left panel of Figure [3](#Fig:phase), we observe a clear trend of decreasing gas content ($\mu_{\rm gas} = M_{\rm gas}/M_{*}$) with proximity to the cluster core. This is more clearly illustrated in the right panel of Figure [3](#Fig:phase), in which we plot $\mu_{\rm gas}$ versus $k_{b} = (|\Delta v|/\sigma_{\rm cluster}) \times (R/R_{200c})$ for the cluster galaxies. The parameter $k_{b}$ converts the phase-space diagram into one dimension (cite: Noble:2013). Galaxies with lower $k_{b}$ are more closely bounded to the cluster, hence are likely accreted at earlier times. Figure [3](#Fig:phase) reveals clearly a trend that galaxies with high gas fraction (relative to the MS) have entered the cluster more recently than the gas-poor members. This remains true even when the normalized gas fraction, $\mu_{\rm gas}/\mu_{\rm gas, \Delta MS}$, is adopted. While galaxies in the outskirts of the cluster exhibit a large scatter in their gas fraction (compared to field galaxies), galaxies in the cluster center ($k_{b} \lesssim 0.1$) show exclusively a deficit of molecular gas. The transition between the gas-rich and -poor populations takes place at around $k_{b} \sim 0.1$. This rapid transition may suggest that whatever environmental effects are involved, this process must be very efficient in reducing the gas content of cluster galaxies.

|  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| ID | ID(W16[^2] ) | $z_{\rm CO}$ | log $M_{*}$ | log $L_{\rm IR}$ | FWHM | $L^{\prime}_{\rm CO(1-0)}$ | $\alpha_{\rm CO}$ | $M_{\rm gas}$ | $t_{\rm dep}$ |  |
|  |  |  | $M_{\odot}$ | $L_{\odot}$ | 10$^{2}$ km s$^{-1}$ | 10$^{10}$ K km s$^{-1}$ pc$^{2}$ | $M_{\odot}$/(K km s$^{-1}$ pc$^{2}$) | $10^{10} M_{\odot}$ | Gyrs |  |
| 1 | 130949 | 2.503 | 11.36$\pm$0.15 | 12.55$\pm$0.14 | 5.0$\pm$0.5 | 2.3$\pm$0.2 | 4.06 | 9.2$\pm$0.9 | 0.26 |  |
| 2 | 130901 | 2.507 | 11.35$\pm$0.15 | 12.04$\pm$0.21 | 6.8$\pm$0.9 | 1.8$\pm$0.3 | 4.06 | 7.4$\pm$1.1 | 0.68 |  |
| 3 | 131079 | 2.514 | 11.13$\pm$0.15 | 11.88$\pm$0.20 | 2.8$\pm$1.2 | 0.6$\pm$0.1 | 4.08 | 2.4$\pm$0.3 | 0.32 |  |
| 4 | 130933 | 2.501 | 11.06$\pm$0.15 | 12.09$\pm$0.16 | 6.9$\pm$1.6 | 0.6$\pm$0.1 | 4.08 | 2.6$\pm$0.5 | 0.21 |  |
| 5 | 130359 | 2.508 | 11.03$\pm$0.15 | 12.44$\pm$0.13 | 2.4$\pm$0.4 | 2.7$\pm$0.4 | 4.08 | 11.1$\pm$1.5 | 0.40 |  |
| 6 | 131077 | 2.494 | 10.93$\pm$0.15 | 12.87$\pm$0.13 | 5.5$\pm$0.4 | 4.9$\pm$0.4 | 4.09 | 20.2$\pm$1.7 | 0.27 |  |
| 7 | 132044 | 2.505 | 10.90$\pm$0.15 | 12.08$\pm$0.18 | 6.8$\pm$1.6 | 2.8$\pm$0.8 | 4.09 | 11.3$\pm$3.5 | 0.94 |  |
| 8 | 130891 | 2.513 | 10.83$\pm$0.15 | 12.62$\pm$0.13 | 3.4$\pm$0.2 | 3.2$\pm$0.3 | 4.10 | 13.3$\pm$1.4 | 0.32 |  |
| 9 | 131661 | 2.500 | 10.80$\pm$0.15 | 11.97$\pm$0.19 | 0.9$\pm$0.4 | 0.5$\pm$0.1 | 4.10 | 1.9$\pm$0.3 | 0.20 |  |
| 10 | 131904 | 2.506 | 10.80$\pm$0.15 | 11.78$\pm$0.25 | 6.9$\pm$3.7 | 1.0$\pm$0.3 | 4.10 | 4.2$\pm$1.1 | 0.70 |  |
| 11 | 132627 | 2.506 | 10.73$\pm$0.15 | 12.27$\pm$0.16 | 6.0$\pm$1.9 | 12.7$\pm$4.2 | 4.10 | 52.2$\pm$17.4 | 2.83 |  |
| 12 | 130842 | 2.515 | 10.67$\pm$0.15 | 11.10$\pm$0.20 | 0.9$\pm$0.3 | 0.3$\pm$0.1 | 4.11 | 1.4$\pm$0.3 | 1.07 |  |
| 13 | – | 2.505 | 10.67$\pm$0.15 | 12.31$\pm$0.20 | 5.3$\pm$0.8 | 2.0$\pm$0.3 | 4.11 | 8.4$\pm$ 1.3 | 0.41 |  |
| 14 | 129444 | 2.515 | 10.54$\pm$0.15 | 11.95$\pm$0.25 | 1.4$\pm$0.3 | 13.4$\pm$2.7 | 4.12 | 55.0$\pm$11 | 6.17 |  |

We further present the variation of SFR and SFE as a function of $k_{b}$ in Figure [4](#Fig:fgas_SFE_kb), showing that both SFR and SFE also varies with clustercentric radius. While galaxies in the outskirts of the cluster exhibit a large scatter in their SFR, most member galaxies in the center tend to fall below the MS. On the other hand, these galaxies in the center show an significant enhancement in their SFE compared to those in the outskirts and field galaxies. Despite their low gas fraction, their normal or suppressed SFR suggests that their enhanced SFE is mainly caused by their deficit of molecular gas (instead of an enhanced SFR). This indicates that the suppression on the SFR from the dense environment is likely delayed compared to that on the gas content. This high SFE ensures that most of these galaxies will likely consume all their gas in a short time scale. Their gas depletion time ($t_{\rm dep}$ = 1/SFE) is around $t_{\rm dep} \sim 0.4$Gyrs, a factor of two shorter than field galaxies with the same $\Delta$MS (Figure [2](#Fig:SFE)). This time scale is comparable to the cluster dynamical time (approximated by the crossing time), $t_{\rm dyn} \sim R_{200c}/\sigma_{\rm cluster} \sim 0.5$ Gyr, suggesting that most of these cluster galaxies may consume all their gas within a single orbit around the cluster center, and form a passive cluster core by $z \sim 2$.

It should be noted that because the sensitivity of the CO(1-0) observation decreases towards larger radius from the cluster center (phase center), only gas-rich systems can be detected at large radii. However, as shown in Figure [1](#Fig:sky), our CO(1-0) detected sample comprise a mass-complete sample of cluster member galaxies, i.e., we are not missing massive star-forming yet gas-poor galaxies up to 2 $\times$ FWHM. Hence our result is not affected by this observational bias.

# Discussion and Conclusions

We have obtained CO(1-0) for 14 massive SFGs in the z=2.51 cluster CLJ1001, the largest sample of galaxies within a single cluster with gas content constraints at $z>2$. These CO-detected galaxies include nearly all the massive SFGs within 2$R_{200c}$, enabling a highly complete census of gas content in massive cluster galaxies. Here we first summarize our main results and then discuss their implications for the formation of massive galaxies in clusters. Our main results are summarized as follows:

– Our cluster galaxies exhibit large differences in their star formation activity and gas masses: some are gas-poor, low-SFR, others are gas-rich, starbursting systems. We show that this large variety of properties mainly correlates with the location of galaxies in the cluster (e.g. with their distance from the cluster core and their accretion state). This is particularly clear when considering the phase-space diagram, which shows that while galaxies remain relatively gas-rich when they first enter the cluster, their gas content is rapidly reduced as they approach the cluster center (enter the virial radius).

– Despite their varieties in gas content and SFR, most cluster galaxies are found to exhibit elevated star formation efficiency with typical gas depletion time of $\sim 400$ Myrs. This gas depletion time is comparable to the dynamical time of the cluster, suggesting that most galaxies may loose their gas (and become quiescent) within a single round-up around the center of the cluster, as further supported by the absence of gas-rich galaxies in the core of this young cluster.

The strong dependence on clustercentric radius of gas content and SFE for these massive SFGs provide evidence that the dense environment plays an important role in shaping the formation/evolution of the most massive cluster galaxies. The significant suppression of molecular gas for all the massive cluster galaxies close to the center (within virial radius) is direct indication that environmental effects helping to stop gas accretion and/or reduce/remove gas content must have taken place. Various mechanisms have been proposed in the literature to reduce the gas content of cluster member galaxies such as starvation (namely, further gas accretion is stopped) or ram pressure and tidal stripping (the gas is removed from the galaxies). The rapid transition between gas-rich and gas-poor systems in the cluster takes place close to the cluster center with $k_{b} \sim 0.1$, supporting the idea that the main mechanisms involved may be ram pressure and tidal stripping, which happen close to the deep cluster potential (cite: Treu:2003). Moreover, the short gas depletion time scale ($\sim$ 0.4 Gyrs, comparable to the dynamical time of the cluster) is also consistent with simulations showing that ram pressure stripping could remove all the gas of cluster members within a single radial orbit around the cluster center (cite: Cen:2014). While current observations suffer from relative poor resolutions, future deep, high-resolution observations of both stellar and gas distribution, as well as kinematics would provide more insights into the main environmental mechanisms at work in this young cluster.

# Acknowledgements

We thank the referee for his/her very constructive comments which help improve the quality and clarity of the paper. We thank Zhi-Yu Zhang for useful discussion on data reduction. This paper makes use of the data from Karl G. Jansky Very Large Array, operated by the National Radio Astronomy Observatory. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.01155.S and #2011.0.00539.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This study was supported by the JSPS Grant-in-Aid for Scientific Research (S) JP17H06130 and the NAOJ ALMA Scientific Research Grant Number 2017-06B. T.W acknowledges the support by the the European Commission through the FP7 SPACE project ASTRODEEP (Ref.No: 312725).

Facilites: VLA, HST, Subaru

natexlab

(ref: Aravena:2012) Aravena, M., Carilli, C. L., Salvato, M., et al. 2012, MNRAS, 426, 258

(ref: Bolatto:2013) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207

(ref: Boselli:2006) Boselli, A., & Gavazzi, G. 2006, PASP, 118, 517

(ref: Bussmann:2015) Bussmann, R. S., Riechers, D., Fialkov, A., et al. 2015, ApJ, 812, 43

(ref: Casasola:2013) Casasola, V., Magrini, L., Combes, F., et al. 2013, A&A, 558, A60

(ref: Casey:2016) Casey, C. M. 2016, ApJ, 824, 36

(ref: Casey:2015) Casey, C. M., Cooray, A., Capak, P., et al. 2015, ApJL, 808, L33

(ref: Cen:2014) Cen, R. 2014, ApJ, 781, 38

(ref: Chabrier:2003) Chabrier, G. 2003, PASP, 115, 763

(ref: Coogan:2018) Coogan, R. T., Daddi, E., Sargent, M. T., et al. 2018, MNRAS, 479, 703

(ref: Cortese:2010) Cortese, L., Davies, J. I., Pohlen, M., et al. 2010, A&A, 518, L49

(ref: Dannerbauer:2017) Dannerbauer, H., Lehnert, M. D., Emonts, B. H. C., et al. 2017, ArXiv e-prints, arXiv:1701.05250

(ref: Davis:2013) Davis, T. A., Alatalo, K., Bureau, M., et al. 2013, MNRAS, 429, 534

(ref: Delhaize:2017) Delhaize, J., Smolčić, V., Delvecchio, I., et al. 2017, A&A, 602, A4

(ref: Dressler:1997) Dressler, A., Oemler, Jr., A., Couch, W. J., et al. 1997, ApJ, 490, 577

(ref: Genzel:2015) Genzel, R., Tacconi, L. J., Lutz, D., et al. 2015, ApJ, 800, 20

(ref: Hayashi:2016) Hayashi, M., Kodama, T., Tanaka, I., et al. 2016, ApJL, 826, L28

(ref: Hayashi:2017) Hayashi, M., Kodama, T., Kohno, K., et al. 2017, ApJL, 841, L21

(ref: Jachym:2014) Jáchym, P., Combes, F., Cortese, L., Sun, M., & Kenney, J. D. P. 2014, ApJ, 792, 11

(ref: Jachym:2017) Jáchym, P., Sun, M., Kenney, J. D. P., et al. 2017, ApJ, 839, 114

(ref: Kennicutt:1998) Kennicutt, Jr., R. C. 1998, ARA&A, 36, 189

(ref: Koyama:2013) Koyama, Y., Kodama, T., Tadaki, K.-i., et al. 2013, MNRAS, 428, 1551

(ref: Laigle:2016) Laigle, C., McCracken, H. J., Ilbert, O., et al. 2016, ApJS, 224, 24

(ref: LeeM:2017) Lee, M. M., Tanaka, I., Kawabe, R., et al. 2017, ApJ, 842, 55

(ref: Magdis:2012b) Magdis, G. E., Daddi, E., Béthermin, M., et al. 2012, ApJ, 760, 6

(ref: McCracken:2012) McCracken, H. J., Milvang-Jensen, B., Dunlop, J., et al. 2012, A&A, 544, A156

(ref: McMullin:2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Muzzin:2013a) Muzzin, A., Marchesini, D., Stefanon, M., et al. 2013, ApJS, 206, 8

(ref: Noble:2013) Noble, A. G., Webb, T. M. A., Muzzin, A., et al. 2013, ApJ, 768, 118

(ref: Noble:2017) Noble, A. G., McDonald, M., Muzzin, A., et al. 2017, ApJL, 842, L21

(ref: Rudnick:2017) Rudnick, G., Hodge, J., Walter, F., et al. 2017, ApJ, 849, 27

(ref: Sargent:2014) Sargent, M. T., Daddi, E., Béthermin, M., et al. 2014, ApJ, 793, 19

(ref: Schreiber:2018a) Schreiber, C., Elbaz, D., Pannella, M., et al. 2018, A&A, 609, A30

(ref: Schreiber:2015) Schreiber, C., Pannella, M., Elbaz, D., et al. 2015, A&A, 575, A74

(ref: Shimakawa:2017) Shimakawa, R., Kodama, T., Hayashi, M., et al. 2017, ArXiv e-prints, arXiv:1708.06369

(ref: Silverman:2015) Silverman, J. D., Daddi, E., Rodighiero, G., et al. 2015, ApJL, 812, L23

(ref: Smolcic:2017) Smolčić, V., Novak, M., Bondi, M., et al. 2017, A&A, 602, A1

(ref: Solomon:2005) Solomon, P. M., & Vanden Bout, P. A. 2005, ARA&A, 43, 677

(ref: Stach:2017) Stach, S. M., Swinbank, A. M., Smail, I., Hilton, M., & Simpson, J. M. 2017, ArXiv e-prints, arXiv:1705.03479

(ref: Tacconi:2018) Tacconi, L. J., Genzel, R., Saintonge, A., et al. 2018, ApJ, 853, 179

(ref: Tadaki:2014) Tadaki, K.-i., Kodama, T., Tamura, Y., et al. 2014, ApJL, 788, L23

(ref: Thomas:2005) Thomas, D., Maraston, C., Bender, R., & Mendes de Oliveira, C. 2005, ApJ, 621, 673

(ref: Treu:2003) Treu, T., Ellis, R. S., Kneib, J.-P., et al. 2003, ApJ, 591, 53

(ref: Wagg:2012) Wagg, J., Pope, A., Alberts, S., et al. 2012, ApJ, 752, 91

(ref: WangT:2016b) Wang, T., Elbaz, D., Daddi, E., et al. 2016, ApJ, 828, 56

(ref: Wetzel:2013) Wetzel, A. R., Tinker, J. L., Conroy, C., & van den Bosch, F. C. 2013, MNRAS, 432, 336

[^1]: http://www.iram.fr/IRAMFR/GILDAS

[^2]: IDs are from the $K_{s}$-selected catalog in (cite: Muzzin:2013a)

</paper>

## Items to check

```json
[
 {
  "path": "results_numeric[3].evidence[0]",
  "value": "k_b of gas-rich to gas-poor transition = ~0.1 dimensionless",
  "failed_quote": "The transition between gas-rich and -poor populations takes place at around $k_{b} \\sim 0.1$."
 }
]
```

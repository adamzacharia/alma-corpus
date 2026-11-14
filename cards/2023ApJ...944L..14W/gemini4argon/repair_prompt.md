# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2023ApJ...944L..14W\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# PHANGS-JWST First Results: Massive Young Star Clusters and New Insights from JWST Observations of NGC 1365

## Abstract

A primary new capability of JWST is the ability to penetrate the dust in star forming galaxies to identify and study the properties of young star clusters that remain embedded in dust and gas. In this paper we combine new infrared images taken with JWST with our optical HST images of the star-bursting barred (Seyfert2) spiral galaxy NGC 1365. We find that this galaxy has the richest population of massive young clusters of any known galaxy within 30 Mpc, with $\sim$ 30 star clusters that are more massive than $10^{6}~M_{\odot}$ and younger than 10 Myr. Sixteen of these clusters are newly discovered from our JWST observations. An examination of the optical images reveals that 4 of 30 ($\sim 13$%) are so deeply embedded that they cannot be seen in the Hubble I band ($A_V \mathrel{>\kern-1.0em\lower 0.9ex\hbox{$\sim$}}10$ mag), and that 11 of 30 ($\sim37$%) are missing in the HST B band, so age and mass estimates from optical measurements alone are challenging. These numbers suggest that massive clusters in NGC 1365 remain completely obscured in the visible for $\sim1.3\pm0.7$ Myr, and are either completely or partially obscured for $\sim3.7\pm1.1$ Myr. We also use the JWST observations to gain new insights into the triggering of star cluster formation by the collision of gas and dust streamers with gas and dust in the bar. The JWST images reveal previously unknown structures (e.g., bridges and overshoot regions from stars that form in the bar) that help us better understand the orbital dynamics of barred galaxies and associated star-forming rings. Finally, we note that the excellent spatial resolution of the NIRCAM F200W filter provides a better way to separate barely resolved compact clusters from individual stars based on their sizes.

# Introduction and Motivation

The discovery that massive young Super Star Clusters (SSCs) are forming in merging and starbursting galaxies was one of the earliest results from the Hubble Space Telescope (e.g., (cite: holtzman92), (cite: whitmore93),

(cite: O’connell94), (cite: barth95)). This discovery provided a direct observational window into the conditions needed to form massive clusters, some of which

will likely evolve into globular clusters (e.g., (cite: ashman92), (cite: elmegreen97), (cite: kruijssen2015)). Many of these SSCs form in dusty regions, including luminous infrared galaxies (e.g., (cite: Adamo20), (cite: Linden21))

with radio observations identifying some of the youngest, most embedded ones (e.g., (cite: sandqvist95), (cite: whitmore02), (cite: Johnson03), (cite: He22)).

The dusty, barred spiral galaxy NGC 1365, at a distance of 19.57 $\pm$ 0.78 Mpc ((cite: gagandeep21)), has one of the highest rates of star formation (16.9 M$_{\odot}~\mbox{yr}^{-1}$) of any galaxy within 20 Mpc (the next highest in the PHANGS-HST sample of 38 galaxies is 7.6 M$_{\odot}~\mbox{yr}^{-1}$ - (cite: lee22)), and is known to have recently (past $\approx10$ Myr) formed very massive ($\mathrel{>\kern-1.0em\lower 0.9ex\hbox{$\sim$}}10^6~M_{\odot}$) clusters (cite: kristen97; galliano08).

The main goal of this paper is to use new infrared imaging of NGC 1365, taken with the recently launched

JWST, plus our optical HST images to collect a complete census of these very young massive clusters, with a focus on discovering clusters missed by previous optical studies because they are enshrouded in dust.

The rest of this paper is organized as follows. Section [2](#sec:data) describes the observations and photometric reductions. Section [3](#sec:reg_1) examines various objects in Region 1, the northern half of the central star-forming ring,

and compiles a census of massive star clusters.

Section [4](#sec:reg_2)

examines some interesting features in Region 2, just outside the central region along the eastern bar.

Our main findings are summarized in Section [5](#sec:conclusions).

# Observations and Reductions

The primary datasets used in this paper are from the PHANGS-JWST Treasury Proposal (PI: J.C. Lee, GO-2107), and the PHANGS-HST project (PI: J.C. Lee, GO-15654).

PHANGS-HST is a Cycle 26 HST Treasury program which obtained imaging for 38 nearby spiral galaxies in the following five filters: F275W (NUV), F336W (U), F438W (B), F555W (V) and F814W (I), with the WFC3 camera (or ACS in cases where archival data was available). See (cite: lee22)[^1] for details about PHANGS-HST.

PHANGS-JWST is a Cycle 1 JWST Treasury program which obtained imaging for the 19 (out of 38) PHANGS-HST galaxies that have IFU maps obtained with VLT/MUSE (cite: emsellem22). ALMA CO(2-1) observations are available for a larger set of 90 PHANGS-ALMA (cite: leroy21) galaxies that include all 19 of the PHANGS-JWST subset. The JWST observations were made in the NIRCAM filters F200W, F300M, F335M, and F360M; and in the MIRI filters F770W, F1000W, F1130W, and F2100W. See (cite: lee22b) for additional details about the observations and basic reductions.

Aperture photometry was performed using a $0.155\ensuremath{''}$ radius aperture with a sky annulus between $0.217\ensuremath{''}$ and $0.310\ensuremath{''}$, as described in (cite: rodriguez22). This subtends a five pixel radius for the F200W NIRCAM observations, and includes approximately 75 % of the light from a point source, but smaller percentages at longer wavelengths (e.g., $\sim40$ % for the F1000W filter and $\sim10$ % for F2100W). For this reason, the JWST magnitudes are used in a relative rather than absolute sense throughout this paper. Magnitudes from Hubble are referred to as NUV, U, B, V, I and those from JWST are referred to by their filter names in order to avoid confusion.

Source selection was performed based on the F335M image, and the corresponding positions were then measured in the other bands. The ABmag system is used throughout.

In the future, aperture corrections will be determined for both stars and clusters. A variety of other observational parameters

will also improve with time, including image alignment and geometric solutions, photometric zeropoints, and background subtraction, as discussed in (cite: lee22b). For these reasons the data and massive cluster catalog we compile here should be considered preliminary. A more definitive treatment will be provided in future papers.

# Region 1: Massive Young Star Clusters

Figure [1](#fig:full_galaxy) shows the locations of

several parts of NGC 1365 that will be discussed in this paper. Our primary focus will be on the central $28\ensuremath{''} \times 26\ensuremath{''}$, or 2.7 kpc $\times$ 2.5 kpc, at the assumed distance of 19.57 Mpc, denoted as the “central finding chart” in Figure [1](#fig:full_galaxy) and shown in more detail in Figure [2](#fig:reg_1_finding). Region 1 is in the northern part of this region,

where some of the most massive young clusters in the nearby universe have formed ((cite: galliano08), (cite: galliano2012)).

![](ngc1365_full_nov_23_trim.pdf)

![](ngc1365_finding_nov_20_2022.pdf)

![](ngc1365_7plot_nov_23.pdf)

## A Compilation of Massive Young Clusters in NGC 1365

In order to build a complete census of massive, young clusters in NGC 1365, we start by identifying all optically selected clusters that have estimated ages younger than 10 Myr and masses higher than $10^6~M_{\odot}$, from the cluster catalog and age-dating analysis based on multi-band HST optical images presented in (cite: turner21) and Whitmore et al. (2022, submitted). Three clusters are removed from the original list since they have very faint F2100W magnitudes indicative of old populations, unlike the rest of the young clusters in our final sample that are all very bright in F2100W. We find 19 clusters which satisfy our criteria (these are the 19 clusters in Table [\[tab:table_1\]](#tab:table_1) that have Cluster ID’s in column 2).

To this list, we add 2 “historical" clusters (M4 and M6) that were previously discovered in radio continuum images (e.g., (cite: sandqvist82), (cite: sandqvist95)), with estimated ages less than 10 Myr and masses in the range 3 $\times~10^6$ to $10^7~M_{\odot}$ ((cite: galliano08), (cite: galliano2012)).

These are comparable to the most massive, recently formed clusters in the merging Antennae (cite: whitmore10) and NGC 3256 ((cite: zepf99), (cite: mulia16), (cite: adamo21)) galaxies.

Finally, we add 16 new, partly or heavily embedded massive young clusters identified in the new JWST images. These have been selected to be brighter than 20.0 mag in at least one of the three filters which contain PAH emission (F335M, F770W and F1130W). As shown in Table [\[tab:table_1\]](#tab:table_1), many sources meet this criterion in all three filters, but a few only qualify in one or two.

We determined the magnitude limit of 20.0 mag to be included in our sample by requiring that

the 19 clusters detected from HST (with one or two exceptions) be included. As will be discussed in Section [3.2.1](#sec:size),

we also require the F200W magnitude to be brighter than 20.0 mag, to insure there is a bright stellar continuum source present, rather than just a dense cloud of gas/dust energized by nearby sources.

We also require that the Concentration Index (CI - defined as the magnitude difference measured in 1 and 4 pixel aperture radii) in the F200W band to be larger than that of a point source: CI$_{\rm F200W} > 1.4$ mag.

Different cluster selection criteria are possible, and in fact several other works within the PHANGS consortium have selected clusters using a single filter: the F335M filter

(cite: rodriguez22), F1000W (Schinnerer et al. 2022, this volume), and the F2100W filter (cite: hassani22). In a future paper we will examine the impact of using different selection strategies in more detail.

Our final census of 37 massive (Mass $\mathrel{>\kern-1.0em\lower 0.9ex\hbox{$\sim$}}10^6~M_{\odot}$), young (Age $\mathrel{<\kern-1.0em\lower 0.9ex\hbox{$\sim$}}$ 10 Myr) candidate clusters in NGC 1365 is compiled in Table [\[tab:table_1\]](#tab:table_1) and shown in Figure [2](#fig:reg_1_finding). Most of the clusters are in an inner star forming ring, as discussed by Schinnerer et al. (2022, this volume), while a few more are in the bar just to the NE of this ring (i.e., objects 33 through 37).

We find that NGC 1365, at a distance of about 20 Mpc, has the richest population of massive young clusters of any known galaxy within 30 Mpc, with about 30 clusters in this mass and age range compared with roughly a dozen in the merging Antennae galaxies ((cite: whitmore10)), located at $\sim22$ Mpc. More distant galaxies with comparable populations are NGC 3256 (65 clusters, distance of 38 Mpc) and NGC 3690 (27 clusters, distance of 42 Mpc), according to (cite: Adamo20). Both of these are ULIRGs and on-going merging systems, with estimated SFRs $\approx40$ M$_{\odot}$ yr$^{-1}$, roughly twice as large as in NGC 1365 (cite: lee22).

We are now ready to address the question: “how many massive young clusters are so enshrouded in dust that they are missing at optical wavelengths?" From column 11 of Table [\[tab:table_1\]](#tab:table_1) we find only 4 out of 37 (11%) of our cluster catalog are so dusty that they are not clearly visible in the I-band image (longest wavelength observed from HST). However, age and mass estimates are quite challenging without photometry in at least three optical bands, which means clusters that are not also detected in the B and V filters are unlikely to be included in optically-selected cluster catalogs, and hence might be considered missing in some cases. For NGC 1365, we find that 9 of 37 ($\sim24$ %) clusters are “missing" in the V band, and 11 of 37 ($\sim30$ %) are “missing" in the B band. *We therefore find that between $\sim11-30$% of the clusters are “missing" from optical catalogs because they are embedded at some level.* This is similar to the situation in the Antennae, where only 2/13 = 15 % of bright thermal radio continuum sources were “missing" at optical wavelengths, and 38 % of fainter clusters (with S $>$ 70 $\mu$Jy) were missing (cite: whitmore02).

![](ngc1365_properties_4plot_nov_23.pdf)

 

Figure [3](#fig:reg_1) reveals a number of interesting features in Region 1. The top-left panel shows the strong dust lane cutting through an optical IVB image taken with HST. Three different JWST$+$HST filter combinations (as indicated along the top right corner of each panel) reveal embedded young clusters, some of which are very bright and saturated (e.g., M4, M5, M6 in the F2100W and F770W images), as well as some blue, slightly older clusters outside the dust lane.

All three of these saturated clusters are also strong radio continuum sources (corresponding to sources D, E, G, respectively in (cite: sandqvist95)).

There are also very thin, dark filaments visible in the F335M/F200W/I-band image; a few are labeled in Figure [3](#fig:reg_1). These are typically found along the inside edge of some of the strongest F335M PAH (Polycyclic Aromatic Hydrocarbons) ridges, and have widths of a few tens of parsecs and lengths of a few hundred parsecs, similar to the massive filaments found in the Milky Way (cite: hacar2022), normal spiral galaxies (e.g., Thilker et al. 2022, this volume, (cite: Meidt22)) as well as other star bursting galaxies such as the Antennae (cite: whitmore14).

## Estimate of Star Cluster Properties

Figure [4](#fig:size) presents four diagnostic diagrams that will be used in this section to estimate several basic properties of the clusters. These include a color-magnitude diagram, color-color diagram, and two flux vs. concentration index diagrams using different bands. A visual estimate of the level of embeddedness is included in Table [\[tab:table_1\]](#tab:table_1): Class 1 = largely unobscured (A$_V \mathrel{<\kern-1.0em\lower 0.9ex\hbox{$\sim$}}3$), Class 2 = partly embedded ( 3 $\mathrel{<\kern-1.0em\lower 0.9ex\hbox{$\sim$}}$ A$_V \mathrel{<\kern-1.0em\lower 0.9ex\hbox{$\sim$}}$ 10), and Class 3 = embedded (A$_V \mathrel{>\kern-1.0em\lower 0.9ex\hbox{$\sim$}}10$). The location of data points for three clusters are shown in each panel to help demonstrate the properties of a largely unobscured cluster (M3, shown in blue), a partially embedded cluster (obj 34, shown in orange), and an embedded cluster (M6, shown in red). Arrows show how properties track in the diagram, including PAH emission strength (youngest clusters), extinction (dustiest clusters), and size (to help separate stars from barely resolved clusters).

We create several different training sets to illustrate a number of features. These include the 37 massive young clusters discussed in Section [3.1](#sec:compilation), now broken into three subsamples:

unobscured, partly embedded and embedded. Other training sets include older clusters (with ages around 300 Myr), a set of largely embedded F200W sources in the dust lane around M4 (see Figure [3](#fig:reg_1)), and objects that are likely to be red super giants (RSG) in a stellar association near the eastern end of the bar. The color coding for the different samples is shown in the upper left panel of Figure [4](#fig:size).

In the next subsections, we show how we separate individual stars from clusters, and then describe methods to estimate the extinction (Section 3.2.2), mass (Section 3.2.3), and age of embedded clusters (Section 3.2.4). We adopt the estimated

properties of relatively unobscured clusters determined in Whitmore et al. (2022, submitted) using Hubble data, as included in Table [\[tab:table_1\]](#tab:table_1), to establish correlations that allow us to estimate properties for the more deeply embedded clusters observed primarily in the JWST bands.

### Separation of Clusters and Stars

The bottom two panels in Figure [4](#fig:size) show that the F200W filter provides a powerful new way to differentiate stars from barely resolved clusters, and to eventually estimate the sizes of the clusters. The scatter in the Concentration Index for stars (black points) using the F200W filter on JWST is dramatically less than from the I filter on HST. If we use the V filter from HST instead the results are intermediate between F200W and I, but we are not able to penetrate the dust as well. This better resolving power might be expected since the resolution with JWST in the F200W band is approximately $0.05\ensuremath{''}$, while it is approximately $0.08\ensuremath{''}$ in I using Hubble. In addition, the sampling is better with $0.031\ensuremath{''}~\mbox{pix}^{-1}$ for the F200W filter compare to $0.040\ensuremath{''}~\mbox{pix}^{-1}$ for the I filter, and the former provides these measurements even in dusty regions.

Figure [4](#fig:size) shows that while there is a large overlap between stars and clusters in CI$_{\rm I}$, there is no overlap using the CI$_{\rm F200W}$ measurements, and the orange line is able to cleanly separate stars from clusters in all cases for our training sets. In the future, we plan to use this new capability to improve the size measurements of star clusters as well.

This improved performance also shows that while some of the embedded F200W objects (green points) in the bottom left panel of Figure [3](#fig:reg_1) are likely to be stars, most (particularly the brighter ones) appear to be clusters, probably with

Mass in the range 10$^5$ to 10$^6$ M$_\odot$.

### Extinction Estimates for Embedded Clusters

There are two approaches we can take to estimate extinction. The first is to use the Galactic extinction law from (cite: Fitzpatrick99). The I - F360M vs. F300M - F335M diagram shown in the upper right panel of Figure [4](#fig:size) demonstrates the range of extinction (A$_V$) values found in our sample.

A reddening vector following a Galactic extinction law is shown for $A_v = 10$ mag. We find that this predicts 4.75 mag of reddening in I - F360M, hence the coefficient connecting $A_v$ and I - F360M is 10 / 4.75 = 2.11. Very small deviations from exactly vertical are ignored since the horizontal dimension is primarily an indication of PAH emission strength rather than reddening. For example, both M6 and obj 34 are found in regions with strong F335M emission, explaining their positions on the right side of both the color-magnitude and color-color diagrams. We find that the majority of the clusters have A$_V$ values less than 10 mag.

The underlying assumption needed to estimate extinction using the I - F360M color index is that all the (young) clusters in our sample have similar intrinsic colors, hence the redder color is caused by extinction rather than due to age. The fact that unobscured clusters (blue points) all have I- F360M values around 0 supports this assumption.

A second approach is to use the empirical correlation between the E(B-V) values from the SED-fitting based on Hubble data vs. I - F360M, as shown in the bottom panel of Figure [5](#fig:mass_ebv_2plot).

We use the sample of class 1 and 2 (symmetric and asymmetric clusters, human classified sample - see (cite: whitmore21)) in NGC 1365 to make this determination. (cite: turner21) describe the basic SED age-dating method used in the PHANGS-HST pipeline. More recently, Whitmore et al. (2022, submitted) describe modifications which identify and correct the age estimates for old globular clusters in the pipeline; many old globular clusters have incorrect age estimates in the default pipeline due to challenges in disentangling age/reddening/metallicity. This helps remove interlopers that might otherwise pollute our young clusters sample. The fraction of clusters with incorrect age estimates in NGC 1365 are reduced from $\approx20$ % to $\approx10$ % according to Whitmore et al. (2022, submitted).

Only the log Age $<$ 6.7 clusters are included to make the sample similar to our program sample of young massive clusters in NGC 1365. The RMS scatter (0.95 mag) is relatively large and the correlation coefficient (0.49) is only fair, hence our estimates of extinction will only be approximate. The resulting formula is:

$A_V (\mbox{JWST) = [(m$_I$ - m$_{F360M}$)}  \times 0.810 + 0.99] \times 3.1$, which provides estimates of extinction for our partially embedded clusters. Hence the coefficient connecting $A_v$ and I - F360M is 0.810 $\times$ 3.1 = 2.51, relatively similar to the estimate from the Galactic extinction law discussed above (i.e., 2.11). This is the formula we will use in Table [\[tab:table_1\]](#tab:table_1).

In principle it would be advantageous to use only JWST observations to determine the correlation, since four of our clusters do not have I band photometry. However, we found that the smaller baseline resulted in considerably more scatter, and hence was not practical. We note that the relationship we derive is specific to the analysis presented here since aperture corrections have not been made to our data yet; other researchers will need to determine the constants from their own photometry.

Table [\[tab:table_1\]](#tab:table_1) shows that the highest estimated extinction value is for the intrinsically bright object 28 (= M6/G, e.g., saturated in the F770W and F2100W filter observations, as shown in Figure [3](#fig:reg_1)), which has an estimate of A$_V$ = 19.3 mag. The value would be about A$_V$ = 15 mag if the Galactic extinction formula was used instead. This extinction is even larger than WS80, a deeply embedded star cluster in the Antennae galaxies (cite: whitmore02) that is the strongest CO and 15 micron source in that system, and has an estimated age of 2 Myr, A$_V\approx8$ mag, and log Mass$~\approx 6.6$. This indicates that the very different environments of a chaotic merger, and the central region of a barred spiral galaxy, can both produce very massive, heavily extincted, young clusters.

### Mass Estimates for Embedded Clusters

To estimate masses for our embedded clusters we use the approach developed by (cite: rodriguez22) who show that there is a good correlation between the F200W flux and the HST-based mass estimates for clusters in NGC 7496, when limited to very young clusters. A similarly good correlation is seen for F335M.

This is because similar age clusters have similar mass-to-light ratios.

As shown in the top panel in Figure [5](#fig:mass_ebv_2plot) we find a very good correlation in NGC1365 as well, with a correlation coefficient of 0.90, and an RMS scatter of just 0.35 dex. The resulting formula is

$\mbox{log}~(M/M_{\odot}) = - 0.4068 \times m_{\rm F200W} + 13.83$. We again use the sample with log Age $<$ 6.7 clusters to make it similar to our sample of young massive clusters in NGC 1365. A version of this fit based on the F300M magnitude is nearly as good: $\mbox{log}~(M/M_{\odot}) = - 0.3639 \times m_{\rm F300M} + 13.25$, with correlation coefficient = 0.87. If the mass-to-light ratios were exactly equal for all the objects we would find the coefficient in the formulae would be the inverse of 2.5 in the definition of magnitudes (i.e., -2.5 log flux), hence it would be 1 / 2.5 = 0.40. We note that this is true, with our empirically determined coefficients approximately equal to 0.41 and 0.36. The final mass values included in Table [\[tab:table_1\]](#tab:table_1) use the mean of these two mass estimates.

Our estimates for clusters M4, M5, and M6 range from log Mass = 6.0 to 6.6, in fair agreement with (cite: galliano08) who estimate values “on the order of 10$^7$ M$_{\odot}$" for the three clusters. We note that in (cite: galliano2012), the estimates are slightly lower, ranging from log Mass = 6.5 to 7.0,

which are in better agreement with our values.

We find that

7 of the 37 clusters in Table 1 have estimated masses that are somewhat below log Mass = 6.0. This is because there are uncertainties at the factor of $\sim2-3$ level associated with each cluster mass. Going forward, for various estimates we assume that 30 clusters from our sample have masses of at least log Mass $\mathrel{>\kern-1.0em\lower 0.9ex\hbox{$\sim$}}$ 6.0.

### Age Estimates for Embedded Clusters

In the future, we will combine HST and JWST bands to improve age estimates, especially for partially embedded clusters. For now, we will use the same basic approach as in the previous two subsections

to estimate the ages of the embedded and partly embedded clusters based on HST estimates.

As shown in Figure [6](#fig:age_335), the age estimates are somewhat more complicated than extinction and mass estimates, with more scatter and a nonlinear dependence. This figure plots HST-based ages vs. source brightness in the F335M filter, which includes the 3.3$\mu$m PAH feature and also continuum emission. While there appears to be a possible correlation for ages between log Age = 6 and 8.3 (e.g., correlation coefficient = 0.44), there is essentially no correlation at older ages.

However, at the bright end (i.e., with F335M $<$ 20.0 mag) we find that most sources are young, with log Age less than 7. A visual examination of the clusters in the upper right part of the diagram show that five of the six (circled) are in regions with strong H$\alpha$ emission and are likely to be young; hence the HST-based age estimates are likely to be incorrect. An example is M5 (object 28), which is a very strong radio source which has been age dated using spectral observations indicating that it is clearly younger than 10 Myr (cite: galliano2012). We note that the plots for other PAH bands, notably F770W and F1130W, look very similar to that for F335M.

Based on this evidence, we believe at least 90 % of the objects with F335M brighter than 20 mag are younger than 10 Myr. We note that this would be compatible with the results from Whitmore et al. 2022 - in prep) who find that approximately 10 % of the HST-based age estimates of clusters in the inner region of NGC 1365 are overestimated, due to the large amount of dust that makes the clusters appear red, and potentially old. While low-resolution (0.8 arcsec) H$\alpha$ imaging from MUSE (cite: emsellem22) has been used in Whitmore et al. 2022 (submitted) to improve the age dating to some extent, this is not as good as having high resolution Hubble H$\alpha$ imaging.

Figure [7](#fig:pah_profiles) shows there are physical reasons why we expect most of the brightest PAH emitters to be young. This figure shows a normalized (at 1 Myr) plot of predicted flux values in various MIRI bands from the Draine models of interstellar dust emission ((cite: draine21)). There are similar profiles for the NUV and FUV emission that are the main driver of the PAH emission. In all these cases the peak flux occurs for ages around 2 to 4 Myr, with relatively rapid declines within just 10 Myr.

As expected, the nebular emission (purple line) shows an even more rapid drop off, falling to just a few percent by 6 or 7 Myr. This is why nebular lines, such as H$\alpha$, are so valuable for age dating; if you see strong emission associated with a cluster, the source is young (e.g., (cite: whitmore02), (cite: anders03), (cite: chandar10a), (cite: fouesneau12)). The PAH band strengths have a similar predicted time evolution, although they typically drop to only $\sim20$ % of their initial flux by 10 Myr. This is why the PAH emission is

correlated with young cluster ages in Figure [6](#fig:age_335). We note that this drop off in PAH strength as a function of time also appears to be compatible with the results of (cite: lin20) for LEGUS galaxies.

Since the scatter in the relationship between F335M magnitudes and log Age based on HST is fairly large ($\sim$0.6 dex), we have chosen to simply assign log Age values of 6.5 (3 Myr) for the clusters without HST age estimates. This is consistent with the results from Figure [6](#fig:age_335), the flux profiles in Figure [7](#fig:pah_profiles), and the comparison with Hubble age estimates in Table [\[tab:table_1\]](#tab:table_1). Hence, our final age estimates are included as the second entry in column 6 in Table [\[tab:table_1\]](#tab:table_1), and are either the HST-based SED fitting value if it exists, or log Age = 6.5 (3 Myr) for the clusters without estimates from Hubble.

![image](ngc1365_mass_ebv_nov_20_2020.pdf)  

![image](ngc1365_age_335_dec_19_2022.pdf)  

![image](pah_profiles_normalized_dec_17_2022.pdf)  

## Duration of the Embedded Phase

A complete census of massive clusters from the optical and infrared allows us to estimate the time that clusters remain in the deeply embedded phase, specifically the length of time they are not detectable at optical wavelengths. While early estimates (e.g., (cite: kawamura09)) were longer than 10 Myr, more recent values have generally been in the range 1 - 5 Myr (e.g., (cite: lada03), (cite: whitmore14), (cite: hollyhead15), (cite: grasha18), (cite: chevance20), (cite: kim21), (cite: hannon22), (cite: He22), and Kim et al. 2022, this volume).

NGC 1365 provides a particularly interesting case because of the large amount of gas and dust which might, in principle, result in longer timescales. It also provides a unique view of the embedded phase of extremely massive ($\geq 10^6~M_{\odot}$) clusters, which can eventually be compared with results from lower-mass clusters to assess whether or not the duration of this phase has any dependence on cluster mass.

We calculate the duration of the deeply embedded phase for massive clusters in NGC 1365 as: #missing $/$ total $\times$ Age (i.e., sample interval) = 4/30 $\times$10 Myr = 1.3 $\pm$ 0.7 Myr, a very short timescale.

If we instead consider the timescale for massive clusters to be detectable in the B, V, and I bands (a minimum needed for most optically-based age-dating methods), we find a somewhat longer timescale #missing $/$ total $\times$ Age = 11/30 $\times$ 10 Myr = 3.7 $\pm$ 1.1 Myr.

Our estimates for how long very massive clusters in NGC 1365 remain embedded in their natal ISM are consistent with those found by previous works, without being obviously longer or shorter relative to estimates made for lower mass clusters in other galaxies. It is important to establish if the length of the embedded phase depends on cluster mass or not, because this provides direct constraints on early feedback processes which may be important for

limiting the masses of clusters.

![](ngc1365_region_2_nov_22_2022_trim.pdf)

![](ngc1365_triggering_4plot_nov_23.pdf)

# Region 2: Star Formation Triggered by Collisions of Gas and Dust Streamers

## Triggered Star Formation

While the strongest star formation in NGC 1365 is occurring in the inner region (i.e., 36 of the 37 youngest most massive clusters as we saw in Section [3.1](#sec:compilation)),

a moderate amount is also taking place along the bar, an example of which is shown in Figure [8](#fig:reg_2). In particular, Bubble 1 is object 37 from Table 1, with a log Mass = 6.6.

Much of the star formation in Region 2 appears to be triggered by dust and molecular gas from dark filamentary “streamers" that reach the bar, colliding and merging with the gas and dust as illustrated in the lower panel of Figure [8](#fig:reg_2), and as discussed in (cite: elmegreen09). Another excellent candidate for this type of triggered cluster formation

is Bubble 2 (3 Myr, $A_V = 2.2$ mag; age and extinction estimates from Whitmore et al. 2022, submitted), as shown in Figure [8](#fig:reg_2). A careful look at Figure [1](#fig:full_galaxy) shows several other examples of regions of star formation near the intersection of streamers and the bar.

Previous kinematic work has shown strong streaming motions due to the bar in NGC 1365 (e.g., (cite: sakamoto07), (cite: lindblad96), Schinnerer et al. 2022, this volume). Simulations provide a more visual way to understand the dynamics of streamers of gas as they approach, interact with, and sometimes overshoot the bar lane. We encourage interested readers to watch this video.[^2] Figure 11 in (cite: sormani20) also provides insight to understand the dynamics and the role of streamers as they interact with the bar, potentially triggering star formation. One key new result from JWST observations is how ubiquitous these streamers are in spiral galaxies (see

(cite: Meidt22) and Thilker et al. 2022 this volume).

Figure [9](#fig:triggering_4plot) shows a larger field of view around Region 2 (i.e., “Region 2 extended" from Figure [1](#fig:full_galaxy)) and contains additional kinematic information which can be used to help test the triggering hypothesis. A full kinematic analysis is beyond the scope of the current paper, however.

The top panel shows a IVB Hubble image which highlights the dust lanes and regions of young stars. Besides the streamer we show in Figure [8](#fig:reg_2), which is labeled Streamer 1, we find several other candidate streamers. The second panel uses the F770W PAH emission filter (shown in the red) to highlight the youngest star forming regions. The third panel shows CO (2-1) moment-1 velocity from the PHANGS-ALMA observations (cite: leroy21), color-coded from -220 km/sec (dark blue) to +220 km/sec (dark red and white). CO clouds are marked using ellipses and box-circle symbols. Ellipses are sized to represent the deconvolved major/minor cloud axes (FWHM), whereas box-circles indicate unresolved clouds (Rosolowsky et al. 2022 - this volume).

We first note the large number of CO clouds in Streamer 1, indicating that much of the gas and dust feeding into the bar, and eventually into the inner region of the galaxy, is coming from the streamers rather than from the bar itself. This figure shows that the gas velocities along Streamer 1 are similar (i.e., this feature appears as a uniform, green color, indicative of velocities around 0 km/s), as expected for a coherent physical component.

Gas velocities along the bar (the upper blue arrows) are more mixed, with values $\approx -100$ to $-200~{\rm km~s}^{-1}$ along most of the bar, but with velocities $\approx -50~{\rm km~s}^{-1}$ in regions where the streamers intersect the bar. This appears to be what is happening in the region of Bubble 2, with the velocities shown by a light blue-green color indicating a velocity that is intermediate between that of the bar and Streamer 1, as we would expect if this formed from the collision of the two components. The situation is less clear for Bubble 1, but the color appears to be light blue ($\approx -100~{\rm km~s}^{-1}$), as expected if it is a combination of dark blue (just to the north and south) and green from Streamer 1.

We also find a less CO-populated streamer farther out in the bar, which we have labeled Streamer 2. It appears to be associated with three or four small star formation regions rather than a large event like the formation of Bubbles 1 and 2. However, we find that it has a similar morphology with uniform green colors until it mixes with the bar, and then shows a combination of green and blue velocities beyond that point.

The bottom panel of Figure [9](#fig:triggering_4plot) shows the CO velocity residuals based on a model of the inner rotating disk (Schinnerer et al. 2022 - this volume). This supports the same basic interpretation, but provides an even stronger connection between Streamer 1 and the feeding of the inner region, with a relatively uniform, narrow red component all the way into the central region. We also note that the association of Bubble 1 with the streamer is clearer in the residual velocity image than the original velocity map just above it.

## Clues to Orbital Dynamics in NGC 1365 - the NE Bridge and other Overshoot Regions

An important capability of JWST is the ability to penetrate through the dust and identify structures that are not observable at optical wavelengths. An example

is the NE Bridge, which is identified in the top panel of Figure [8](#fig:reg_2), but is much less obvious in the HST image in Figure [1](#fig:full_galaxy). Features like this bridge are often seen in hydro-dynamical simulations of bars (e.g., (cite: sormani20), (cite: tress2020), (cite: henshaw2022), Schinnerer et al. 2022, this volume).

Gas in a barred potential travels almost radially along the bar dust lanes (in the frame co-rotating with the bar) towards the inner parts of the galaxy.

However, not all the gas transitioning from the dust lanes to the inner regions does so smoothly - some overshoots and collides with gas travelling down the opposite dust lane.

We believe the NE bridge feature is a clear example of material that has overshot the

inner ring after falling towards the center along the southern bar dust lane (bottom-right of Fig 1).

When the material reaches the inner ring, gas and stars behave differently because they obey different equations of motion. Gas is affected by cloud collisions and thus dissipates some of its energy and eventually ends up accreting onto the inner ring. Stars, on the other hand, do not feel pressure forces and are unaffected by cloud collisions, so they fly undisturbed through the gas clouds and continue on their ballistic orbits towards the bar lane on the opposite (northern) bar lane, as appears to be the case with the NE Bridge.

These, and several other features obvious in the new JWST observations (e.g., the overshoot regions marked in Figure [3](#fig:reg_1) and [2](#fig:reg_1_finding)), provide important insights into how the orbits of stars and gas vary depending on where they form, and how this results in the population of older clusters outside the inner star-formation ring. A related phenomena is discussed in Whitmore et al. 2022, submitted (i.e., the “300 My" overshoot region, as identified in Figure [2](#fig:reg_1_finding)).

# Summary and Conclusions

In this work, we have presented new infrared JWST NIRCAM and MIRI imaging of the highly star-forming barred spiral galaxy NGC 1365 in the F200W, F300M, F335M, F360M, F770W, F1000W, F1130W, and F2100W filters. These images show not only the same compact star clusters and individual stars observable in optical Hubble images, but also reveal recently formed clusters that remain deeply embedded in gas and dust, PAH emission, and new (likely dynamical) structures like the NE bridge and dark thin filaments. From measurements of the concentration index

we found that the F200W filter on JWST gives more accurate size measurement for stellar sources than the I filter on Hubble, resulting in a cleaner separation of stars and clusters.

We have compiled a comprehensive catalog of 37 massive $(M \mathrel{>\kern-1.0em\lower 0.9ex\hbox{$\sim$}}10^6~M_{\odot})$, young (Age $\mathrel{<\kern-1.0em\lower 0.9ex\hbox{$\sim$}}10$ My) clusters in NGC 1365, all but one located in the $28\ensuremath{''} \times 26\ensuremath{''}$ (2.7 kpc × 2.5 kpc) region around the central star-forming ring. We found that 4 of 30 ($\sim13$%) (i.e., including only the 30 objects with measured values below $10^6~M_{\odot}$ in Table [\[tab:table_1\]](#tab:table_1)) are so deeply embedded that they cannot be easily seen in the optical images taken by HST, even in the I filter, while 11 of 30 ($\sim37$%) do not have mass estimates from HST because they are missing in the HST B-band images, and hence their ages cannot be easily determined in the visible using SED-fitting techniques. These statistics imply that the massive clusters in NGC 1365 remain deeply embedded (not detectable in the I-band) for $1.3\pm0.7$ My, and sufficiently embedded that they are not detectable in the B-band for $3.7\pm1.1$ My. Hence, we find that NGC 1365 contains the richest known population of massive young clusters in any galaxy within 30 Mpc, even larger than the populations formed in the merging Antennae galaxy.

We also identified several interesting new features near the intersection between the bar and streamers of gas and dust that appear to be colliding and triggering star formation. Other new features include a NE bridge, which may be created by material that dynamically overshot the star-forming ring after falling towards the inner regions along the dust lane in the southern bar.

The age, mass, and extinction estimates in this paper are approximate and preliminary, since they are based on correlations between optical estimates and JWST observations for the more embedded clusters. In the future we expect to obtain better age estimates using SED fitting techniques using both the HST and JWST observations.

# Acknowledgements

This work is based on observations made with the NASA/ESA/CSA JWST and Hubble Space Telescopes. The data were obtained from the Mikulski Archive for Space Telescopes at the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5-03127 for JWST and NASA contract NAS 5-26555 for HST. The JWST observations are associated with program 2107, and those from HST with program 15454.

# Facilities

*HST* (Hubble Space Telescope), *JWST*, ALMA (Atacama Large Millimeter/submillimeter Array), VLT-MUSE (Very Large Telescope - Multi Unit Spectroscopic Explorer).

We would like to thank the referee for several useful and constructive comments that lead to improvements in the paper. ATB would like to acknowledge funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (grant agreement No.726384/Empire). FB would like to acknowledge funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (grant agreement No.726384/Empire) JMDK gratefully acknowledges funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme via the ERC Starting Grant MUSTANG (grant agreement number 714907). COOL Research DAO is a Decentralized Autonomous Organization supporting research in astrophysics aimed at uncovering our cosmic origins. MC gratefully acknowledges funding from the DFG through an Emmy Noether Research Group (grant number CH2137/1-1).

TGW acknowledges funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (grant agreement No. 694343). This research was supported by the Excellence Cluster ORIGINS which is funded by the Deutsche Forschungsgemeinschaft (DFG, German Research Foundation) under Germany’s Excellence Strategy - EXC-2094-390783311. Some of the simulations in this paper have been carried out on the computing facilities of the Computational Center for Particle and Astrophysics (C2PAP). We are grateful for the support by Alexey Krukau and Margarita Petkova through C2PAP.

This paper makes use of the following ALMA data:1447 ADS/JAO.ALMA#2013.1.01161.S. Based on observations collected at the European1459 Southern Observatory under ESO programmes 1100.B-1460 0651 (PHANGS-MUSE; PI: Schinnerer), as well as1461 094.B-0321 (MAGNUM; PI: Marconi).

# Data Availability

The imaging observations underlying this article can be retrieved from the Mikulski Archive for Space Telescopes at <https://archive.stsci.edu/hst/search_retrieve.html> under proposal GO-15654. High level science products, including science ready mosaicked imaging, associated with HST GO-15654 are provided at <https://archive.stsci.edu/hlsp/phangs-hst>. The specific PHANGS-JWST observations analyzed can be accessed via and PHANGS-HST images accessed via .

natexlab

(ref: Adamo20) Adamo, A., Hollyhead, K., Messa, M., et al. 2020a, MNRAS, 499, 3267, doi: [`10.1093/mnras/staa2380`](http://doi.org/10.1093/mnras/staa2380)

(ref: adamo21) Adamo, A., Zeidler, P., Kruijssen, J. M. D., et al. 2020b, Space Sci. Rev., 216, 69, doi: [`10.1007/s11214-020-00690-x`](http://doi.org/10.1007/s11214-020-00690-x)

(ref: gagandeep21) Anand, G. S., Lee, J. C., Van Dyk, S. D., et al. 2021, MNRAS, 501, 3621, doi: [`10.1093/mnras/staa3668`](http://doi.org/10.1093/mnras/staa3668)

(ref: anders03) Anders, P., & Fritze-v. Alvensleben, U. 2003, A&A, 401, 1063, doi: [`10.1051/0004-6361:20030151`](http://doi.org/10.1051/0004-6361:20030151)

(ref: ashman92) Ashman, K. M., & Zepf, S. E. 1992, ApJ, 384, 50, doi: [`10.1086/170850`](http://doi.org/10.1086/170850)

(ref: barth95) Barth, A. J., Ho, L. C., Filippenko, A. V., & Sargent, W. L. 1995, AJ, 110, 1009, doi: [`10.1086/117580`](http://doi.org/10.1086/117580)

(ref: Boquien19) Boquien, M., Burgarella, D., Roehlly, Y., et al. 2019, A&A, 622, A103, doi: [`10.1051/0004-6361/201834156`](http://doi.org/10.1051/0004-6361/201834156)

(ref: chandar10a) Chandar, R., Fall, S. M., & Whitmore, B. C. 2010, ApJ, 711, 1263, doi: [`10.1088/0004-637X/711/2/1263`](http://doi.org/10.1088/0004-637X/711/2/1263)

(ref: chevance20) Chevance, M., Kruijssen, J. M. D., Hygate, A. P. S., et al. 2020, MNRAS, 493, 2872, doi: [`10.1093/mnras/stz3525`](http://doi.org/10.1093/mnras/stz3525)

(ref: draine21) Draine, B. T., Li, A., Hensley, B. S., et al. 2021, ApJ, 917, 3, doi: [`10.3847/1538-4357/abff51`](http://doi.org/10.3847/1538-4357/abff51)

(ref: elmegreen97) Elmegreen, B. G., & Efremov, Y. N. 1997, ApJ, 480, 235, doi: [`10.1086/303966`](http://doi.org/10.1086/303966)

(ref: elmegreen09) Elmegreen, B. G., Galliano, E., & Alloin, D. 2009, ApJ, 703, 1297, doi: [`10.1088/0004-637X/703/2/1297`](http://doi.org/10.1088/0004-637X/703/2/1297)

(ref: emsellem22) Emsellem, E., Schinnerer, E., Santoro, F., et al. 2022, A&A, 659, A191, doi: [`10.1051/0004-6361/202141727`](http://doi.org/10.1051/0004-6361/202141727)

(ref: Fitzpatrick99) Fitzpatrick, E. L. 1999, PASP, 111, 63, doi: [`10.1086/316293`](http://doi.org/10.1086/316293)

(ref: fouesneau12) Fouesneau, M., Lançon, A., Chandar, R., & Whitmore, B. C. 2012, ApJ, 750, 60, doi: [`10.1088/0004-637X/750/1/60`](http://doi.org/10.1088/0004-637X/750/1/60)

(ref: galliano2012) Galliano, E., Kissler-Patig, M., Alloin, D., & Telles, E. 2012, A&A, 545, A10, doi: [`10.1051/0004-6361/201218812`](http://doi.org/10.1051/0004-6361/201218812)

(ref: galliano08) Galliano, F., Dwek, E., & Chanial, P. 2008, ApJ, 672, 214, doi: [`10.1086/523621`](http://doi.org/10.1086/523621)

(ref: grasha18) Grasha, K., Calzetti, D., Bittle, L., et al. 2018, MNRAS, 481, 1016, doi: [`10.1093/mnras/sty2154`](http://doi.org/10.1093/mnras/sty2154)

(ref: hacar2022) Hacar, A., Clark, S., Heitsch, F., et al. 2022, arXiv e-prints, arXiv:2203.09562. [`https://arxiv.org/abs/2203.09562`](https://arxiv.org/abs/2203.09562)

(ref: hannon22) Hannon, S., Lee, J. C., Whitmore, B. C., et al. 2022, MNRAS, 512, 1294, doi: [`10.1093/mnras/stac550`](http://doi.org/10.1093/mnras/stac550)

(ref: hassani22) Hassani, H., Rosolowsky, E., Leroy, A. K., et al. 2022, arXiv e-prints, arXiv:2212.01526. [`https://arxiv.org/abs/2212.01526`](https://arxiv.org/abs/2212.01526)

(ref: He22) He, H., Wilson, C., Brunetti, N., et al. 2022, ApJ, 928, 57, doi: [`10.3847/1538-4357/ac5628`](http://doi.org/10.3847/1538-4357/ac5628)

(ref: henshaw2022) Henshaw, J. D., Barnes, A. T., Battersby, C., et al. 2022, arXiv e-prints, arXiv:2203.11223. [`https://arxiv.org/abs/2203.11223`](https://arxiv.org/abs/2203.11223)

(ref: hollyhead15) Hollyhead, K., Bastian, N., Adamo, A., et al. 2015, MNRAS, 449, 1106, doi: [`10.1093/mnras/stv331`](http://doi.org/10.1093/mnras/stv331)

(ref: holtzman92) Holtzman, J. A., Faber, S. M., Shaya, E. J., et al. 1992, AJ, 103, 691, doi: [`10.1086/116094`](http://doi.org/10.1086/116094)

(ref: Johnson03) Johnson, K. E., & Kobulnicky, H. A. 2003, ApJ, 597, 923, doi: [`10.1086/378585`](http://doi.org/10.1086/378585)

(ref: kawamura09) Kawamura, A., Mizuno, Y., Minamidani, T., et al. 2009, ApJS, 184, 1, doi: [`10.1088/0067-0049/184/1/1`](http://doi.org/10.1088/0067-0049/184/1/1)

(ref: kim21) Kim, J., Chevance, M., Kruijssen, J. M. D., et al. 2021, MNRAS, 504, 487, doi: [`10.1093/mnras/stab878`](http://doi.org/10.1093/mnras/stab878)

(ref: kristen97) Kristen, H., Jorsater, S., Lindblad, P. O., & Boksenberg, A. 1997, A&A, 328, 483

(ref: kruijssen2015) Kruijssen, J. M. D. 2015, MNRAS, 454, 1658, doi: [`10.1093/mnras/stv2026`](http://doi.org/10.1093/mnras/stv2026)

(ref: lada03) Lada, C. J., & Lada, E. A. 2003, ARA&A, 41, 57, doi: [`10.1146/annurev.astro.41.011802.094844`](http://doi.org/10.1146/annurev.astro.41.011802.094844)

(ref: lee22) Lee, J. C., Whitmore, B. C., Thilker, D. A., et al. 2022a, ApJS, 258, 10, doi: [`10.3847/1538-4365/ac1fe5`](http://doi.org/10.3847/1538-4365/ac1fe5)

(ref: lee22b) Lee, J. C., Sandstrom, K. M., Leroy, A. K., et al. 2022b, arXiv e-prints, arXiv:2212.02667. [`https://arxiv.org/abs/2212.02667`](https://arxiv.org/abs/2212.02667)

(ref: leroy21) Leroy, A. K., Schinnerer, E., Hughes, A., et al. 2021, ApJS, 257, 43, doi: [`10.3847/1538-4365/ac17f3`](http://doi.org/10.3847/1538-4365/ac17f3)

(ref: lin20) Lin, Z., Calzetti, D., Kong, X., et al. 2020, ApJ, 896, 16, doi: [`10.3847/1538-4357/ab9106`](http://doi.org/10.3847/1538-4357/ab9106)

(ref: lindblad96) Lindblad, P. A. B., Lindblad, P. O., & Athanassoula, E. 1996, A&A, 313, 65

(ref: Linden21) Linden, S. T., Evans, A. S., Larson, K., et al. 2021, ApJ, 923, 278, doi: [`10.3847/1538-4357/ac2892`](http://doi.org/10.3847/1538-4357/ac2892)

(ref: Meidt22) Meidt, S. E., Rosolowsky, E., Sun, J., et al. 2022, arXiv e-prints, arXiv:2212.06434. [`https://arxiv.org/abs/2212.06434`](https://arxiv.org/abs/2212.06434)

(ref: mulia16) Mulia, A. J., Chandar, R., & Whitmore, B. C. 2016, ApJ, 826, 32, doi: [`10.3847/0004-637X/826/1/32`](http://doi.org/10.3847/0004-637X/826/1/32)

(ref: O’connell94) O’Connell, R. W., Gallagher, John S., I., & Hunter, D. A. 1994, ApJ, 433, 65, doi: [`10.1086/174625`](http://doi.org/10.1086/174625)

(ref: rodriguez22) Rodriguez, J., Lee, J., Whitmore, B., et al. 2022, arXiv e-prints, arXiv:2211.13426. [`https://arxiv.org/abs/2211.13426`](https://arxiv.org/abs/2211.13426)

(ref: sakamoto07) Sakamoto, K., Ho, P. T. P., Mao, R.-Q., Matsushita, S., & Peck, A. B. 2007, ApJ, 654, 782, doi: [`10.1086/509775`](http://doi.org/10.1086/509775)

(ref: sandqvist95) Sandqvist, A., Joersaeter, S., & Lindblad, P. O. 1995, A&A, 295, 585

(ref: sandqvist82) Sandqvist, A., Jorsater, S., & Lindblad, P. O. 1982, A&A, 110, 336

(ref: sormani20) Sormani, M. C., Tress, R. G., Glover, S. C. O., et al. 2020, MNRAS, 497, 5024, doi: [`10.1093/mnras/staa1999`](http://doi.org/10.1093/mnras/staa1999)

(ref: tress2020) Tress, R. G., Sormani, M. C., Glover, S. C. O., et al. 2020, MNRAS, 499, 4455, doi: [`10.1093/mnras/staa3120`](http://doi.org/10.1093/mnras/staa3120)

(ref: turner21) Turner, J., Lee, J., Van Dyk, S., et al. 2021

(ref: whitmore93) Whitmore, B. C., Schweizer, F., Leitherer, C., Borne, K., & Robert, C. 1993, AJ, 106, 1354, doi: [`10.1086/116732`](http://doi.org/10.1086/116732)

(ref: whitmore02) Whitmore, B. C., & Zhang, Q. 2002, AJ, 124, 1418, doi: [`10.1086/341822`](http://doi.org/10.1086/341822)

(ref: whitmore10) Whitmore, B. C., Chandar, R., Schweizer, F., et al. 2010, AJ, 140, 75, doi: [`10.1088/0004-6256/140/1/75`](http://doi.org/10.1088/0004-6256/140/1/75)

(ref: whitmore14) Whitmore, B. C., Brogan, C., Chandar, R., et al. 2014, ApJ, 795, 156, doi: [`10.1088/0004-637X/795/2/156`](http://doi.org/10.1088/0004-637X/795/2/156)

(ref: whitmore21) Whitmore, B. C., Lee, J. C., Chandar, R., et al. 2021, MNRAS, 506, 5294, doi: [`10.1093/mnras/stab2087`](http://doi.org/10.1093/mnras/stab2087)

(ref: zepf99) Zepf, S. E., Ashman, K. M., English, J., Freeman, K. C., & Sharples, R. M. 1999, AJ, 118, 752, doi: [`10.1086/300961`](http://doi.org/10.1086/300961)

|  |  |  |  |  |  |  |  |  |  |  |  |
|:---|:---|:---|:---|:---|---:|---:|---:|:---|:---|---:|---:|
| ID | Cl ID$^a$ | Other ID | RA | DEC | log Age$^b$ | log Mass$^c$ | Av$^d$ | CI$_{200}^e$ | Class$^f$ | Detected$^g$ | Detected$^h$ |
|  |  |  | (J2000) | (J2000) | (H, H-JW) | (H, JW) | (H, JW) |  |  | B, V, I | PAHs |
|  |  |  | (deg) | (deg) | (Myr) | (M$_\odot$) | (mag) | (mag) |  |  |  |
| 1 | — | — | 53.400281 | -36.142577 | —, 6.5 | —, 6.2 | —, 12.5 | 2.05 | 3 | —, —, I | 3.3, 7.7, 11.3 |
| 2 | 996 | — | 53.399891 | -36.142575 | 6.0, 6.0 | 7.1, 6.6 | 4.6, 4.4 | 1.83 | 2 | B, V, I | 3.3, 7.7, 11.3 |
| 3 | 1051 | J$^i$ | 53.400691 | -36.142127 | 6.0, 6.0 | 7.2, 6.9 | 4.6, 5.4 | 1.70 | 2 | B, V, I | 3.3, 7.7, 11.3 |
| 4 | 1064 | — | 53.399386 | -36.142085 | 6.6, 6.6 | 6.1 6.2 | 3.1, 4.3 | 1.69 | 2 | B, V, I | 3.3, 7.7, 11.3 |
| 5 | — | — | 53.400338 | -36.142072 | —, 6.5 | —, 6.00 | —, 4.9 | 1.64 | 2 | B, V, I | 3.3, 7.7, 11.3 |
| 6 | — | — | 53.399056 | -36.141991 | —, 6.5 | —, 5.8 | —, — | 1.53 | 3 | —, —, — | 3.3, 7.7, 11.3 |
| 7 | 1116 | M2$^j$, SSC3$^k$ | 53.399870 | -36.141833 | 6.5, 6.5 | 6.9, 6.6 | 1.7, 1.0 | 1.45 | 1 | B, V, I | 3.3, 7.7, 11.3 |
| 8 | 1141 | — | 53.401402 | -36.141753 | 6.7, 6.7 | 6.6, 6.5 | 5.4, 4.6 | 2.05 | 2 | B, V, I | 3.3, 7.7, 11.3 |
| 9 | 1251 | — | 53.400184 | -36.141315 | 6.0, 6.0 | 6.9, 6.6 | 4.6, 6.3 | 1.88 | 2 | B, V, I | 3.3, 7.7, 11.3 |
| 10 | 1259 | — | 53.402834 | -36.141274 | 6.7, 6.7 | 6.0, 6.2 | 4.9, 5.8 | 1.59 | 2 | B, V, I | 3.3, —, — |
| 11 | — | — | 53.399771 | -36.141127 | —, 6.5 | —. 6.5 | —, 4.5 | 1.66 | 2 | B, V, I | 3.3, 7.7, 11.3 |
| 12 | 1296 | M3$^j$, SSC6$^k$ | 53.399552 | -36.141121 | 6.5, 6.5 | 6.6, 6.6 | 1.2, 2.0 | 1.62 | 1 | B, V, I | 3.3, 7.7, 11.3 |
| 13 | — | — | 53.402935 | -36.140825 | —, 6.5 | —, 5.9 | —, — | 1.39 | 3 | —, —, — | 3.3, 7.7, — |
| 14 | — | — | 53.402318 | -36.140610 | —, 6.5 | —, 5.8 | —, 3.8 | 2.69 | 1 | B, V, I | —, 7.7, 11.3 |
| 15 | — | — | 53.403212 | -36.140610 | —, 6.5 | —, 6.3 | —, 12.2 | 1.52 | 3 | —, —, I | 3.3, 7.7, — |
| 16 | — | — | 53.402911 | -36.140455 | —, 6.5 | —, 5.8 | —, 8.0 | 1.73 | 2 | B, V, I | 3.3, 7.7, 11.3 |
| 17 | — | — | 53.402548 | -36.140381 | —, 6.5 | —, 6.0 | —, — | 1.79 | 3 | —, —, — | 3.3, 7.7, 11.3 |
| 18 | 1506 | — | 53.403394 | -36.140211 | 6.0, 6.0 | 6.4 6.2 | 4.6, 6.5 | 1.76 | 2 | B, V, I | 3.3, —, — |
| 19 | — | — | 53.399524 | -36.140090 | —, 6.5 | —, 6.5 | —, 8.4 | 1.89 | 3 | —, V, I | 3.3, 7.7, 11.3 |
| 20 | 1528 | — | 53.403379 | -36.140083 | 6.5, 6.5 | 6.2, 6.1 | 4.6, 6.1 | 1.74 | 2 | B, V, I | 3.3, 7.7, — |
| 21 | — | — | 53.403331 | -36.139860 | —, 6.5 | —, 6.2 | —, 6.9 | 1.52 | 2 | B, V, I | 3.3, 7.7, 11.3 |
| 22 | — | — | 53.400461 | -36.139849 | —, 6.5 | —, 6.7 | —, 7.4 | 1.72 | 2 | B, V, I | 3.3, 7.7, 11.3 |
| 23 | —- | — | 53.403374 | -36.139568 | —, 6.5 | —, 6.3 | —, 5.6 | 1.74 | 2 | B, V, I | 3.3, 7.7, — |
| 24 | 1640 | — | 53.399837 | -36.139432 | 6.0, 6.0 | 6.3, 5.8 | 4.6, 2.4 | 2.03 | 1 | B, V, I | 3.3, —, — |
| 25 | — | — | 53.400928 | -36.139100 | —, 6.5 | —, 6.7 | —, — | 1.84 | 3 | —, —, I | 3.3, —, 11.3 |
| 26 | 1700 | C1$^i$ | 53.404026 | -36.139017 | 6.7, 6.7 | 6.9, 6.7 | 4.6, 2.9 | 1.75 | 1 | B, V, I | 3.3, 7.7, 11.3 |
| 27 | — | — | 53.402918 | -36.138860 | —, 6.5 | —, 6.6 | —, 9.5 | 1.79 | 3 | —, —, I | 3.3, —, — |
| 28 | — | M6$^j$, G$^i$ | 53.403181 | -36.138475 | —, 6.5 | —, 6.6 | —, 19.3 | 1.85 | 3 | —, —, I | 3.3, SAT, 11.3 |
| 29 | — | M4$^j$, D$^i$ | 53.401702 | -36.138433 | —, 6.5 | —, 6.0 | —, — | 1.62 | 3 | —, —, — | 3.3, SAT, 11.3 |
| 30 | 1782 | — | 53.400982 | -36.138416 | 6.5, 6.5 | 6.2, 6.3 | 4.9, 7.5 | 1.55 | 2 | B, V, I | 3.3, 7.7, 11.3 |
| 31 | 1794 | — | 53.401669 | -36.138367 | 6.6, 6.6 | 6.1, 6.0 | 4.6, 5.8 | 1.68 | 2 | B, V, I | 3.3, 7.7, 11.3 |
| 32 | 1810 | — | 53.401369 | -36.138271 | 6.9, 6.9 | 6.2, 6.8 | 4.6, 7.7 | 1.97 | 2 | —, V, I | 3.3, —, — |
| 33 | 1920 | M5$^j$, E$^i$ | 53.402514 | -36.137680 | —, 6.5 | —, 6.6 | —, 4.3 | 1.55 | 2 | B, V, I | 3.3, SAT , 11.3 |
| 34 | 1932 | — | 53.402534 | -36.137596 | 6.7, 6.7 | 6.4, 5.8 | 5.0, 7.4 | 1.45 | 2 | B, V, I | 3.3, 7.7, 11.3 |
| 35 | 1948 | — | 53.403066 | -36.137494 | 6.5 6.5 | 6.5, 5.8 | 6.9, 6.6 | 1.57 | 2 | B, V, I | 3.3, 7.7, 11.3 |
| 36 | — | — | 53.403115 | -36.137151 | —, 6.5 | —, 6.3 | —, 6.4 | 1.42 | 2 | B, V, I | 3.3, 7.7, 11.3 |
| 37 | 2242 | — | 53.407333 | -36.135815 | 6.6, 6.5 | 6.2, 6.3 | 2.0, 2.6 | 1.71 | 1 | B, V, I | 3.3, 7.7, 11.3 |

$^a$ - Cluster ID from the NGC 1365 compact cluster catalog, as found at https://archive.stsci.edu/hlsp/phangs-hst.\
$^b$ - Log Age - First column: Hubble value from Whitmore et al. 2022 (submitted). Typical errors are 0.4 dex. Second column: Adopted value from first column if available (Hubble), or 6.5 otherwise (JWST - typical errors are 0.6 dex). See Section [3.2.4](#sec:ages_for_embedded) for discussion.\
$^c$ - Log Mass - First column: Hubble value from Whitmore et al. 2022 (submitted). Second column: Value from mean of values based on F200W formula (i.e., $\mbox{log}~(M/M_{\odot}) = - 0.4068 \times m_{\rm F200W} + 13.83$) and F300M formulae (i.e., $\mbox{log}~(M/M_{\odot}) = - 0.3639 \times m_{\rm F300M} + 13.25$). Typical errors are 0.35 dex. See Section [3.2.3](#sec:mass).\
$^d$ - Extinction (A$v$) - First column: Hubble value from Whitmore et al. 2022 (submitted). Second column: Value from formula $A_V (\mbox{JWST) = [(m$_I$ - m$_{F360M}$)}  \times 0.810 + 0.99] \times 3.1$. Typical errors are 1.0 mag). See Section [3.2.2](#sec:extinction).\
$^e$ - Concentration Index (CI) using the difference in aperture magnitudes in the F200W filter using radii of 1 and 4 pixels. See Section [3.2.1](#sec:size).\

Notes from table (continued):

$^f$ - Visual estimate of how embedded the cluster is. Class 1 = largely unobscurred (A$_V \mathrel{<\kern-1.0em\lower 0.9ex\hbox{$\sim$}}$ 3 mag) , Class 2 = partly embedded (3 $\mathrel{<\kern-1.0em\lower 0.9ex\hbox{$\sim$}}A_V \mathrel{<\kern-1.0em\lower 0.9ex\hbox{$\sim$}}$ 10 mag), Class 3 = embedded (A$_V \mathrel{>\kern-1.0em\lower 0.9ex\hbox{$\sim$}}$ 10 mag).\
$^g$ - Brighter than 26th mag in relevant band.\
$^h$ - Brighter than 20th mag in relevant band.\
$^i$ - Radio Source ID - (cite: sandqvist95).\
$^j$ - MID IR ID - ((cite: galliano08)).\
$^k$ - SSC = Super Star Cluster ID - (cite: kristen97).\

[^1]: <https://archive.stsci.edu/hlsp/phangs-hst>

[^2]: https://www.youtube.com/watch?v=1elJ81GlIlA&list=PLlsb6ZGKWbI6QOFPd6OYU4zLXCmBa6uxx&index=5

</paper>

## Items to check

```json
[
 {
  "path": "data.other_facilities[3].provided.evidence[1]",
  "value": "Archive for JWST and HST imaging and PHANGS-HST high level science products",
  "failed_quote": "High level science products, including science ready mosaicked imaging, associated with HST GO-15654 are provided at https://archive.stsci.edu/hlsp/phangs-hst."
 },
 {
  "path": "results_numeric[0].evidence[0]",
  "value": "Number of candidate massive young star clusters compiled in catalog = 37 dimensionless",
  "failed_quote": "Our final census of 37 massive (Mass $\\mathrel{>\\kern-1.0em\\lower 0.9ex\\hbox{$\\sim$}}10^6~M_{\\odot}$), young (Age $\\mathrel{<\\kern-1.0em\\lower 0.9ex\\hbox{$\\sim$}}$ 10 Myr) candidate clusters in NGC 1365 is compiled in Table [tab:table_1]"
 },
 {
  "path": "results_numeric[7].evidence[0]",
  "value": "Maximum estimated visual extinction A_V (for cluster M6 / object 28) = 19.3 mag",
  "failed_quote": "Table [tab:table_1] shows that the highest estimated extinction value is for the intrinsically bright object 28 (= M6/G, e.g., saturated in the F770W and F2100W filter observations, as shown in Figure 3), which has an estimate of A$_V$ = 19.3 mag."
 },
 {
  "path": "reproducibility.data_public_as_stated.evidence[0]",
  "value": "HST data and PHANGS-HST high-level science products are public at MAST; PHANGS-JWST and PHANGS-HST DOIs are referenced (though blank in the manuscript text).",
  "failed_quote": "The imaging observations underlying this article can be retrieved from the Mikulski Archive for Space Telescopes at https://archive.stsci.edu/hst/search_retrieve.html under proposal GO-15654. High level science products, including science ready mosaicked imaging, associated with HST GO-15654 are provided at https://archive.stsci.edu/hlsp/phangs-hst."
 },
 {
  "path": "reproducibility.products_in_archive.evidence[0]",
  "value": "PHANGS-HST mosaicked imaging and compact cluster catalog are available as HLSP at MAST.",
  "failed_quote": "High level science products, including science ready mosaicked imaging, associated with HST GO-15654 are provided at https://archive.stsci.edu/hlsp/phangs-hst."
 }
]
```

# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2023MNRAS.520...63W\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
## Abstract

A long-standing problem when deriving the physical properties of stellar populations is the degeneracy between age, reddening, and metallicity. When a single metallicity is used for all star clusters in a galaxy, this degeneracy can result in "catastrophic" errors for old globular clusters. Typically, approximately 10 – 20 % of all clusters detected in spiral galaxies can have ages that are incorrect by a factor of ten or more. In this paper we present a pilot study for four galaxies (NGC 628, NGC 1433, NGC 1365, and NGC 3351) from the PHANGS-HST survey. We describe methods to correct the age-dating for old globular clusters, by first identifying candidates using their colors, and then reassigning ages and reddening based on a lower metallicity solution. We find that young ‘Interlopers’ can be identified from their H$\alpha$ flux. CO (2-1) intensity or the presence of dust can also be used, but our tests show that they do not work as well. Improvements in the success fraction are possible at the $\approx15$ % level (reducing the fraction of catastrophic age-estimates from between 13 - 21 % to 3 - 8 %). A large fraction of the incorrectly age-dated globular clusters are systematically given ages around 100 Myr, polluting the younger populations as well. Incorrectly age-dated globular clusters significantly impact the observed cluster age distribution in NGC 628, which affects the physical interpretation of cluster disruption in this galaxy. For NGC 1365, we also demonstrate how to fix a second major age-dating problem, where very dusty young clusters with $E(B-V)>1.5$ mag are assigned old, globular-cluster like ages. Finally, we note the discovery of a dense population of $\approx300$ Myr clusters around the central region of NGC 1365. and discuss how this results naturally from the dynamics in a barred galaxy.

galaxies: star formation – galaxies: star clusters: general

# Introduction

Estimating the ages of star clusters provides direct insight into the star formation process and the structure and evolution of galaxies. Clusters provide clocks for measuring a number of physical mechanisms that are fundamental to understand how galaxies operate, such as the timescales for giant molecular clouds to form star clusters, the timescales for feedback to stop star formation and hence conserve gas for the longer term evolution of the galaxy, and the timescales for the disruption of star clusters as they return their member stars into the field population of the galaxy ((cite: lada03), (cite: chandar06), (cite: whitmore07), (cite: kawamura09), (cite: bastian12a), (cite: fall12), (cite: whitmore14), (cite: grasha15), (cite: kruijssen19), (cite: chevance20), (cite: barnes20), (cite: kim22)).

A variety of increasingly sophisticated stellar population models have been developed to predict the observed color evolution and ages of clusters. These include models by (cite: charlot91), (cite: leitherer99), (cite: bruzual03), (cite: Vazdekis10), (cite: maraston11), (cite: zackrisson11), (cite: krumholz15), and (cite: eldridge17).

Similarly, a variety of increasingly sophisticated methods have been developed to age-date clusters, including: isochrone synthesis - (cite: charlot91), reddening-free Q parameters - (cite: whitmore99), hybrid color-color diagrams - (cite: whitmore02), maximum likelihood fits - (cite: chandar10a), (cite: adamo17), stochastically sampled probabalistic models - (cite: fouesneau10), (cite: krumholz15), (cite: ashworth17) and Bayesian analysis - (cite: Boquien19). Each of these approaches has its own strengths and weaknesses.

In general, the results from different approaches agree reasonably well

(e.g., (cite: degrijs05)). On the near horizon is an increase in the wavelength range and sensitivity

promised by JWST observations, which will allow us to identify and study the embedded cluster population and improve our ability to accurately age-date clusters.

However, all of these models and approaches share a common problem, which in many cases introduces major systematic uncertainties which can seriously affect the science results. This is the long-standing age/metallicity/reddening degeneracy problem. The basic reason for the degeneracy is that integrated stellar populations can change from blue to red colors for three independent reasons; the age increases, reddening due to dust increases, or the metallicity increases. In a color-color diagram, this problem is seen by the fact that the predicted colors of aging clusters move from the blue (young) corner to the red (old) corner along a roughly diagonal line that has about the same slope as the direction that reddening moves clusters in this space (e.g., (cite: whitmore02), (cite: chandar04), (cite: smith07), (cite: Cockcroft11), (cite: forbes22)).

To help break the degeneracies, people use several (generally three or more) photometric bands, which add structure to the shape of the Spectral Energy Distribution (SED) and help distinguish it from a straight line. The addition of the U-band is particularly important for this ((cite: anders04a), (cite: smith06), (cite: smith07)). In many cases, follow-up spectroscopy provides more robust age estimates than is possible from photometry alone (e.g., (cite: chandar04), (cite: annibali18), (cite: whitmore20), (cite: forbes22)). Other observational measurements (e.g., H$\alpha$ flux) can also help break the degeneracies (e.g., (cite: whitmore02), (cite: anders03), (cite: chandar10a), (cite: fouesneau12), (cite: ashworth17), (cite: barnes21)).

In many cases the techniques used to help break the degeneracies are not enough, as demonstrated in (cite: whitmore20) for the LEGUS (Legacy Extragalactic UV Survey - (cite: calzetti15a)) galaxy NGC4449.

By comparing ages estimated from spectra of verified old globular clusters, with those estimated using a standard SED-fitting approach, the authors found that ages for most old globular clusters were underestimated by a factor of 50 to 1000. Instead of giving age estimates around 10 Gyr ages, most of the globular clusters were assigned ages between 5 and 500 Myr. In the current paper, we show that this problem can be understood by looking at the shape of Simple Stellar Population (SSP) models in a color-color diagram. Other recent papers that discuss this problem for PHANGS-HST (Physics at High Angular Resolution in Nearby Galaxies with the Hubble Space Telescope project; PI: J.C. Lee, GO-15654) and LEGUS galaxies are (cite: turner21), (cite: deger22), and (cite: hannon22). This problem appears to be endemic to a large number of studies from the past several decades, as discussed in more detail in Section [9](#sec:conclusions).

This, and other related age-dating problems, are investigated in the current paper. We develop methods which improve the age-dating results for 10 to 20 % of the overall cluster populations in four PHANGS-HST spiral galaxies. While this is a relatively small improvement in terms of the overall percentage of affected clusters, the improvements are quite important for studies of old globular clusters, and can also impact a variety of important diagnostics for younger clusters since most of the old clusters are *systematically* redistributed to have ages around either 5 or 100 Myr. Examples of science results that may be affected by this problem are:

the power-law index of cluster age distributions (e.g., see Section [7](#sec:age_and_mass)), the presence or absences of a downturn at the upper end of the cluster mass function (e.g., (cite: adamo17), (cite: mok19)), the fraction of stars that form in clusters (i.e., $\Gamma$ - (cite: bastian08), (cite: kruijssen12), (cite: chandar17)), and the specific frequency of old globular clusters in spiral galaxies (cite: harris91). We examine the impact on the age distribution in this paper

for one galaxy, NGC 628, as an example.

The current paper is a pilot project using four PHANGS-HST galaxies (NGC 628, NGC 1365, NGC 1433, and NGC 3351, as shown in Figure [1](#fig:4x2_image)). The project is designed to identify and fix the most common problems in the determination of cluster ages, masses, and reddening as performed in the PHANGS-HST data reduction pipeline (i.e., (cite: turner21)). The development of more sophisticated methods to optimize age estimates for the full sample will be briefly discussed, and its incorporation into the PHANGS-HST pipeline will be described in a future paper.

Our approach in this paper is to first identify a set of clusters with age estimates which are clearly incorrect. We then experiment with how to objectively identify them in a color-color diagram, and establish rules that fix the ages for most of these clusters. The few remaining exceptions (e.g., primarily young clusters with significant reddening due to dust that gives them colors similar old globular clusters) are then corrected using information from either H$\alpha$, CO intensity, or dust morphology. We find that, perhaps not surprisingly, H$\alpha$ emission offers the most direct and powerful way to establish the presence of young stars, but in the absence of such data, tracers that indicate the presence of dust,

such as CO or dust morphology, can also be used.

The rest of this paper is organized as follows. Section [2](#sec:data) describes the data and sample. In Section [3](#sec:problems) we present and discuss the primary age-dating problems we want to solve.

In Section [4](#sec:approach) we describe the procedure used to identify "bad ages" and investigate where they are generally found in the log Age vs. $E(B-V)$ diagram and the U-B vs. V-I diagram. In Section [5](#sec:solutions) we describe how we build the hybrid age-solutions for clusters in the four program galaxies, starting with the easiest galaxies (NGC 1433 - low Star Formation Rate, hereafter SFR, and relatively minor reddening) and finishing with the most challenging (NGC 1365 - high SFR and extensive dust).

Section

[6](#sec:halpha_co_dust) examines how well H$\alpha$ flux, CO intensity, and dust morphology work to

identify exceptions to our basic rules (i.e. "interlopers").

Section

[7](#sec:age_and_mass) examines the impact of the new age-dating solutions on science results, in particular on the age distribution and fraction of stars found in clusters for NGC 628. Section [8](#sec:future_work) describes future work while Section [9](#sec:conclusions) provides a summary and conclusions.

![](sed_paper_4x2_image_jan_2_2022_trim.pdf)

# Sample and Related Datasets

## Pilot Galaxy Sample

Four galaxies from the PHANGS-HST survey (cite: lee22) have been chosen for this exploratory study. These include galaxies that span the range from low SFR and low dust content, to high SFR and dust content.

The galaxies are NGC 1433 (a relatively dust-free, low SFR barred spiral), NGC 3351 (a barred spiral with low dust content and SFR in the outer region, but a high SFR ring with extensive dust in the inner region), NGC 628 (a grand-design spiral with moderate SFR and dust), and NGC 1365 (a dusty barred galaxy with very high SFR). Galaxy distances range from 10 Mpc (NGC 628 and NGC 3351), to 18 Mpc for NGC 1433, and 20 Mpc for NGC 1365 (cite: gagandeep21).

The four galaxies are shown in Figure [1](#fig:4x2_image) in the order they will be discussed in this paper, from the lowest SFR (0.56 M$_\odot$/yr), least dusty galaxy (NGC 1433) to the highest SFR (16.90 M$_\odot$/yr) dustiest galaxy (NGC 1365). The top panels show the F814W, F555W, F438W composite color image using software adopted from the Hubble Legacy Archive (cite: whitmore16), while the bottom panels show versions with the ALMA CO (2-1) emission in red (cite: leroy21). The red circles are class 1 (symmetric, centrally peaked: hereafter C1) clusters, while the green circles show the class 2 (asymmetric, centrally peaked: hereafter C2) clusters, as discussed in (cite: whitmore21). These will be the only two classes included in the current study (i.e., class 3 and multi-scale associations - (cite: larson22), are not included).

## HST Observations

The primary datasets used in this paper are from the PHANGS-HST project (PI: J.C. Lee, GO-15654)

(cite: lee22).[^2] PHANGS-HST is a Cycle 26 Treasury program which obtained multi-band imaging for 38 nearby spiral galaxies in the following five filters: F275W (NUV), F336W (U), F438W (B), F555W (V), F814W (I), with the WFC3 camera (or ACS in some cases with existing data).

The PHANGS-HST catalogs of compact star clusters are one of the key data products from the project. Cluster candidates are selected using a Multi-Concentration-Index (MCI), as described in (cite: thilker22). They are then classified into four classes based on visual examination (see (cite: whitmore21)). In this work, we use only the human classified, C1

and C2

clusters. These human classified clusters have also been used to train a convolutional neural network to obtain machine learning classifications for a larger (fainter) sample of star clusters (see (cite: wei20), (cite: whitmore21), and Hannon et al. 2023 - in preparation).

The numbers of objects for each target galaxy are compiled in Table [1](#tab:table1) and range from N = 191 for NGC 1433 to N = 635 for NGC 1365.

The age-dating results presented throughout this paper are based on SED fits between cluster photometry in the NUV, U, B, V, and I bands and the Bruzual & Charlot (2003) stellar population models, through the CIGALE fitting software (cite: Boquien19). For the original baseline solution, we adopted a fixed solar metallicity ($Z=0.02$) model, and fit for the best combination of age and reddening, where the ages range from

log Age = 6.0-10.2 yr, and the reddening between $0.0 - 1.5$ mag. For the hybrid solutions that will be discussed later in this paper, we also performed fits with 1/50th solar metallicity ($Z=0.0004$), that are used for likely old globular clusters. The (cite: fitzpatrick99) reddening law with R$_{V}$ = 3.1 is used. This has been shown to better match clusters in spiral galaxies when using deterministic predictions like the Bruzual & Charlot models. Cluster age and reddening estimates from SED fitting are not very sensitive to the adopted extinction law in general. For example, the estimated ages for only a handful of clusters change by $\sim \pm0.1$ in log age when the Calzetti attenuation curve is adopted instead.

As described in (cite: turner21), about 20 % of the clusters

have bimodal probability distributions indicative of the age/reddening degeneracy problem discussed in the current paper. If these objects are excluded, the average uncertainty in our cluster age estimates is about 0.3 dex. An example of a bimodal probability distribution is shown in Section [3.2](#sec:common_problem_2).

Age estimates from Version 1.1 of the PHANGS-HST pipeline are used in this study. The primary difference from Version 1, which is described in (cite: turner21), is the use of developmental software to include upper limits for the fluxes in cases where the values are less than $1\sigma$ of the photometric error estimate, as described in more detail in Deger et al. (2023 - in preparation). This is primarily relevant for the NUV (F275W) and U (F336W) photometry, and affects only a few percent of the class 1 and class 2 clusters. Catalogs developed as part of the current paper will be published in the PHANGS-HST archives and new updated catalogs will be made available as the PHANGS-HST pipeline evolves. Archival H$\alpha$ imaging from HST for NGC 628, NGC 1433, and NGC 3351 were also examined and used to make snapshots to illustrate various points in this paper. Unfortunately, no HST H$\alpha$ imaging is available for NGC 1365.

PHANGS-HST is creating new dust extinction maps (as described in (cite: thilker23)), which we use in the current paper. Dust lanes are identified as dark, filamentary structures in each galaxy using a machine learning approach (specifically: U-Net), operating on the F336W, F438W, and F555W images. At the time of submission,

the project had not yet generated extinction maps ($A_V$ versus position). Instead, we use masks which identify the dust features (0 or 1, depending on the presence of a dust lane) from early versions of the project. These are discussed in Section [6.2](#sec:dust_halpha), where we use them to test how well they identify interlopers.

## MUSE and ALMA Observations

Since high-resolution, H$\alpha$ images with HST are not currently available for most of the galaxies in the PHANGS-HST sample, H$\alpha$ measurements at the locations of all cluster candidates from PHANGS-MUSE (for 19 of the 38 PHANGS-HST galaxies) are used in this paper. While this provides a uniform dataset, it has the disadvantages of lower resolution (approximately 0.8$\ensuremath{''}$ for MUSE, compared to $0.1\ensuremath{''}$ for HST). The lower resolution, for both the MUSE H$\alpha$

and the CO observations ($\approx1.2\ensuremath{''}$), is one of the primary limitations of our pilot study. The H$\alpha$ flux measurements are determined from the MUSE images using aperture photometry with a radius that matches the MUSE resolution. No continuum or annular sky subtraction is performed.

See (cite: emsellem22) for further details about the MUSE project.

Similar integrated CO(2-1) line intensity measurements at the locations of the cluster candidates were made using the ALMA observations, as described in (cite: leroy21). Given that the ALMA resolution element is much larger than the circular aperture used for HST photometry, we simply extract the CO intensity on the ALMA map at the pixel nearest to the cluster sky position.  For a typical PHANGS-HST galaxy at 16 Mpc median distance, the 1.2 arcsec ALMA beam size corresponds to approximately 90 pc.

Hence, the CO intensity at the positions of the clusters is often under or over estimated due to smoothing effects. This will be discussed in more detail in Section [\[sec:best-interloper\]](#sec:best-interloper).

# The Primary Problems When Age-dating Star Cluster Populations

![](sinan_cc_17_aper_correction_jul_23_2022.pdf)

## Problem 1: Star clusters do not all have the same metallicity

Most studies that perform SED age-dating for stellar clusters assume a single metallicity, generally solar or near solar for spirals,

and subsolar for dwarfs and irregulars. This is a natural choice since the focus is generally on recently formed clusters, which have higher metallicity than ancient clusters. If old globular clusters are included in the fitting, there can be a mismatch between some of their observed colors and the higher metallicity predictions,

which can result in incorrect

age and reddening determinations. These incorrect results for ancient clusters pollute the young and intermediate age populations. The broad wavelength coverage of the PHANGS-HST survey makes our dataset well-suited for studying both young and old clusters. In order to provide accurate estimates for clusters of all ages, we need to include fits to both high and low metallicity models in our age-dating procedure.

Figure [2](#fig:cc_3metal) illustrates the age-metallicity degeneracy by showing the measured colors of bright, isolated clusters (used to determine aperture corrections) in 17 PHANGS-HST galaxies from (cite: deger22). These are often old globular clusters in the outskirts of galaxies. The clump of points around $V-I = 1.1$, $U-B = -0.2$ in Figure [2](#fig:cc_3metal) (i.e., within the yellow oval) are nearly all old globular clusters, based on visual examination (they are yellowish in color, generally isolated, and show no evidence of dust or H$\alpha$ emission). Note how far away they are from the the end of the orange (solar metallicity) SED model at $V-I = 1.4$, $U-B = 0.5$ (that they are being fit to in the PHANGS age-dating pipeline), and how close they are to the

end of the 1/50th solar metallicity shown by the green line.

Redder, more metal-rich, globular cluster (for example those associated with bulges) are also probably present, but fall along the solar metallicity BC03 model predictions, and hence are much more likely to be age-dated correctly. While second parameter effects, such as horizontal branch structure, may also have some impact on the colors of globular clusters, these do not impact our primary goal of identifying old globular clusters and developing methods that allow us to approximately age-date them correctly.

In what follows, we will assume solar metallicity for the young clusters and 1/50th metallicity for objects we believe to be old globular clusters. In principle, we could attempt to use different metallicities for different galaxies, e.g., using the values in (cite: santoro22). However, the grid of available metallicity models is fairly coarse, and nearly all of the galaxies in our sample would use the solar metallicity model in any case. Similarly, since there is a gradient in the metallicities as a function of radius for many spiral galaxies (e.g., (cite: sanchez14), (cite: kreckel19), (cite: williams22)), we could attempt to include this dependency. However, the gradient is generally weak, and represents a much smaller issue than the age/reddening/metallicity degeneracy which is the main focus of this paper. We plan to make a more detailed study, with more finely sampled metallicity values, as part of the future work discussed in Section [8](#sec:future_work).

The metallicities for old globular clusters in our galaxies are essentially unknown, hence we will use the relatively good agreement between the clump of points in Figure [2](#fig:cc_3metal) and the bottom end of the 1/50th metallicity track as justification for using the same value for all of our galaxies. This is a typical value for normal spiral galaxies. For example, (cite: lomel22) use a range of 1/20 to 1/50 solar metallicity to fit their sample of old globular clusters in spiral galaxies. Several studies find that changing metallicities by only a factor of a few has relatively minor effects on the results (e.g., (cite: whitmore20), (cite: messa21)). It is primarily when changes on the order of ten or more are made, as in the current paper, that large differences in age estimates are found.

## Problem 2: Allowing reddening to be a free parameter can result in large errors 

Most SED age-dating software constructs a grid of luminosity and color predictions spanning a range of age, reddening ($E(B-V)$) or extinction ($A_V$), and metallicity, then finds the combination of these parameters that minimizes the difference between observed and predicted fluxes in a number of photometric bands (generally four or more). In most recent studies, the metallicity is fixed while age and reddening are free parameters, albeit within some limits.

If the assumed population synthesis model is not appropriate for the objects, for example adopting a solar metallicity model while trying to fit globular clusters with low metallicity, the cluster properties can be sufficiently different from the predictions that the program is unable to find the correct age (and reddening) solution. In this specific case, the fitting program will often find an apparent solution "up the reddening vector" where a combination of age, and moderate to high reddening, gives a better match to the observed colors, rather than finding the correct age.

Figure [3](#fig:degen) demonstrates how the combination of a mismatch in metallicity, the inherent age-metallicity degeneracy, and the option to fit $E(B-V)$ reddening as a free parameter, can lead to many incorrect age solutions for old globular clusters. Using Figures 2 and 3 from (cite: deger22) as the base figures, we again note the location of old globular clusters in the color-color diagram shown in Figure [2](#fig:cc_3metal), with the yellow circle around them.

![](sinan_2plot_dec_6_2022.pdf)

As graphically illustrated[^3] in Figure [3](#fig:degen), SED-fitting generally selects between three potential age-reddening combinations for these old globular clusters. The first solution (the red arrow originating from the position of the old globular clusters in the left panel and the red oval in the right panel) is a combination of old age (typically approximately 1 Gyr for solar metallicity) and very low reddening, where the fit effectively jumps down to the nearest position on the solar metallicity SED track.

The resulting position in the log Age - $E(B-V)$ plot is shown by the red oval in the right panel of Figure [3](#fig:degen). Note that estimated ages of $\approx1$ Gyr are still far from the correct answer of $\sim10$ Gyr.

In our pilot study, we find the most common solution is an intermediate age ($\approx100$ Myr) and reddening ($E(B-V)$ $\approx0.5$ mag), which is shown by the green arrow and corresponding green oval in Figure [3](#fig:degen). This solution backtracks up the reddening vector until it hits the solar metallicity track at an intermediate age. This results in $E(B-V)$ values of $\approx$ 0.5 mag; clearly too high based on visual examination which show little dust around nearly all globular clusters. Roughly 60 % of the old globular clusters in our sample are assigned incorrect ages in this intermediate range.

The third possible solution (shown by the blue arrow and corresponding blue oval) is a combination of very young age (Age $\approx$ 3 Myr) and high reddening ($E(B-V)$ $\approx1$ mag). In this case, the fitting has backtracked all the way up the reddening vector, to the youngest end of the SED track. Though less common in our sample, this solution is still preferred by the fitting software between 10 and 20 % of the time for old globular clusters. For example, for NGC 4449 the LEGUS age estimates based on a similar filter combination ((cite: calzetti15a) assigns 2 of 6 spectroscopically-confirmed old globular clusters to this age range (cite: whitmore20).

The right panel in Figure [3](#fig:degen) shows that these three incorrect solutions populate a diagonal region in the log Age - $E(B-V)$ diagram above the rest of the cluster population, essentially showing the intersection of the ’backtracked’ reddening vector and the SED track.

There are a number of other examples and recent discussions of this behavior in the literature, for example (cite: turner21), (cite: deger22), (cite: hannon22) and (cite: moeller22). We examine the scientific impacts that this type of incorrect age-dating can have by examining the case of NGC 628 in Section [7](#sec:age_and_mass).

![](bimodal_pdf_dec_6_2022.pdf)

Another useful tool for visualizing the three possible solutions

is a probability distribution plot, as derived from the CIGALE output. These plots will be one of the primary tools used in the followup to the current pilot study, as discussed in Section [8](#sec:future_work) (see also (cite: turner21)). An example of a probability distribution plot is shown in Figure [4](#fig:bimodal) for object \# 687, a candidate globular cluster in NGC 1365 (see discussion and snapshot in Section [5](#sec:solutions)). The three peaks correspond to the three potential age-reddening solutions shown in Figure [3](#fig:degen).

The top plot in Figure [4](#fig:bimodal) shows that the strongest likelihood peak is the youngest one, at log Age = 6.8 (i.e., 7 Myr), and that is what is reported, incorrectly, as the minimum $\chi^{2}$ result by CIGALE. However, the best solution, since visual inspection shows that these are generally old globular clusters given the absence of gas or dust in their vicinity, is actually the oldest solution at log Age = 9.4. The lower value of the likelihood in the top panel of Figure [4](#fig:bimodal) for this older solution is due to the mismatch in metallicity between old globular clusters and the solar metallicity being used for the fit (i.e., Problem #1). The bottom plot in Figure [4](#fig:bimodal) again demonstrates how old globular clusters with bad age estimates result in points above a diagonal in a log Age - $E(B-V)$ diagram. Notice the similarity with the right panel of Figure [3](#fig:degen).

## Problem 3: Some heavily reddened clusters require higher $E(B-V)$ limits

For most galaxies in the PHANGS-HST and LEGUS samples, assuming a maximum reddening of around $E(B-V)$ = 1.5 is appropriate, since these systems contain a small to moderate amount of dust. This assumption works reasonably well for three (NGC 628, NGC 1433, NGC 3351) of the four galaxies studied in this work. However, for a few galaxies, the spiral arms and central regions can be sufficiently dusty that a higher limit is needed.

This particular issue will be examined for NGC 1365 in Section [5.5](#sec:hybrid-1365).

This case results in the opposite issue from problems 1 and 2: the ages of young, dust-embedded clusters can be overestimated by factors of $\sim1000$, as also seen in (cite: hannon22).

This third problem will become more relevant in the future, when JWST will allow researchers to study more heavily reddened and embedded clusters.

# Identifying Incorrect Age Results

## Visual Examination to Identify Bad Ages

A brief look at the bulges of many spiral galaxies immediately reveals the clear presence of a population of old globular clusters. The clusters are uniformly yellow, isolated, and there are no blue objects nearby. NGC 1433 and NGC 3351 provide particularly good examples of bulge globular clusters. These regions provide an initial training set of the properties of old globular clusters and how they appear in the HST images.

Based on these initial training sets, our first step

is to perform a manual, systematic search for clusters with "bad ages" in the four PHANGS-HST galaxies studied here. This search was performed by co-author M. Floyd, who visually inspected color images (to check for the presence of dust that would be consistent with large $E(B-V)$ values)), and inspected H$\alpha$ and ALMA CO (2-1) images (to check for the presence of ionized and molecular gas that would be consistent with stellar populations younger than approximately 10 Myr). He also compared the measured $B-V$ vs. $V-I$ colors with BC03 model predictions, and examined the environment and isolation of each cluster. The visual inspections were performed using the Hubble Legacy Archive and custom software (cite: whitmore16). This part of the project is discussed in more detail in Floyd et al. 2023 (in prep).

A designation of "bad age" requires a difference of a factor of ten or more between the visually estimated age and the version 1.0 SED age estimate, as described in (cite: turner21). The most common age-dating mistake, as expected, are objects that are most likely old globular clusters (e.g., yellowish, no emission-line flux, no evidence of dust, often in the bulge or towards the outer portion of the galaxy, generally with $V-I > 0.9$ and $U-B > -0.5$), but are best fit by ages $\mathrel{<\kern-1.0em\lower 0.9ex\hbox{$\sim$}}500$ Myr and reddening $E(B-V)$$\mathrel{>\kern-1.0em\lower 0.9ex\hbox{$\sim$}}0.4$ mag.

A similar examination was made in NGC 1433 by (cite: hannon22), and eight clusters with underestimated ages were identified.

Seven out of the same eight clusters are also identified as having bad ages in the current work, while the eighth source has a reasonable best fit age of

4 Gyr in the PHANGS-HST fitting procedure (i.e., it does not qualify as having a bad age) while the LEGUS pipeline assigned a best fit age of 3 Myr for this object, and hence it was included in the (cite: hannon19) review. Similar examples of underestimated ages for old globular clusters

are reported and discussed in detail for NGC 4449 in (cite: whitmore20).

Figure [5](#fig:poster) shows an example of an old globular cluster (top panels) and a "young interloper" (bottom panels - i.e. a young cluster with enough reddening from dust to give it colors similar to an old globular cluster). The three columns show an optical Hubble B-V-I color image (left), a B-V-H$\alpha$ map (middle), and a B-V-CO (right) image. The old globular cluster is intrinsically yellow and has very little dust or CO associated with it. In addition, the old globular cluster is quite isolated, and in a region with a smooth background, i.e., the bulge of NGC 3351.

The young interloper has extensive H$\alpha$ around it, hence it is young ($<$ 10 Myr) and intrinsically blue, but has enough dust around it to give it $U-B$ and $V-I$ colors that are similar to a globular cluster, as listed in the figure. In addition, the young interloper has many other sources near it, some with blue colors indicative of young stars, as well as extensive CO, another indicator of a young age.

![](n3351_6plot_trim.pdf)

## Mapping Bad Ages to the log Age - $E(B-V)$ and Color-Color Diagrams

![](sed2_n1433_4plot.pdf)

Figure [6](#fig:n1433_cc_bad12) shows the locations of the bad-age objects (generally old globular clusters) identified in NGC 1433. The upper left panel shows a B-V-I color image. The bottom-left panel shows the bad-age objects in gold. This highlights the fact that there are many bad age clusters in the bulge region.

The upper right panel shows that in NGC 1433, nearly all of the bad-age objects are in the same region of the color-color diagram, highlighted by the red box. This box covers the $U-B$ range from -0.6 to 1.2, and $V-I$ range from 0.95 to 1.7. The size of the box has been chosen to be large enough to contain all but two of the clusters (with large uncertainties) that were determined to have bad ages. The strongest concentration of points is found just above the solar model predictions, as also demonstrated in Figure [2](#fig:cc_3metal) for a different sample, namely 17 galaxies that have been used to determine aperture corrections (see (cite: deger22)). The box is somewhat wider than the concentration of lower-metallicity globular clusters in Figure [2](#fig:cc_3metal) to accomodate some of the lower S/N points (primarily due to larger uncertainties in the U-band), and the possibility of small amounts of reddening from dust. As will be demonstrated later in the paper, this works well for three of the four galaxies (NGC 1433, NGC 3351, and NGC 628), but will be modified somewhat in the case of NGC 1365 for a variety of reasons. We refer to this as the ’Old Globular Cluster’ box (hereafter OGC-box) for the rest of the paper.

The strong concentration of bad age points just above the solar model is the primary reason we are able to fix the age-metallicity problem for old globular clusters by adopting the 1/50th solar metallicity solution for clusters in this region of color-color space. Most of the few remaining red points in the OGC-box have age estimates around log Age = 9.5, and hence are not identified as bad ages since they are not a factor of 10 different from the typical age of an old globular cluster, which should have

log Age $\approx 10$. None of the red points in the OGC-box for NGC 1433 in Figure [6](#fig:n1433_cc_bad12) are "young interlopers" (young, reddened objects which mimic the colors of old globular clusters). However, we will find that NGC 3351 and NGC 628 do have small numbers of young interlopers, as discussed in Sections [5.3](#sec:hybrid-3351) and [5.4](#sec:hybrid-628).

![](sed_paper_co_4plot.pdf)

The bottom right plot shows an even more dramatic result, namely that all of the bad ages identified manually, and completely independently, are above a diagonal line that runs from (log Age, $E(B-V)$) = (6, 1.0) to (9, 0.1). This diagonal line

works well not only for all four galaxies studied here but for the globular cluster populations in 18 PHANGS-HST galaxies studied by Floyd et al., 2023, and also for the multi-modal probability distributions shown in Figure [4](#fig:bimodal). Hence, these two diagrams together provide an excellent way to identify clusters with potentially bad age estimates.

## $U-B$ vs. $V-I$ Diagrams as a Function of CO Flux 

Figure [7](#fig:cc_4plot) shows the $U-B$ vs $V-I$ color-color diagram of clusters in all four target galaxies. Here, the color coding shows the strength of the CO flux measured around each object. This provides a useful backdrop for the following discussion.

We first note that NGC 1433

has very little dust and CO emission, with most of it associated with the youngest clusters in the upper left portion of the plot, as expected. This therefore provides a good starting point for our study since we expect reddening to have little affect on observed cluster colors. NGC 3351 and NGC 628 both show a bit more CO emission, some of which appears to be associated with a few clusters in the OGC-box (the dark circles in this box).

NGC 1365 looks dramatically different than the other three galaxies, both because of the very small number of young clusters in the upper left portion of the diagram, and also because a fair number of points are below or to the right of the OGC-box. Nearly all of these very red objects have strong CO (dark circles). This immediately shows that most of the objects in the bottom right part of the diagram are likely to be young, heavily reddened objects rather than old globular clusters. Because of this we will treat NGC 1365 differently than the other three galaxies.

# Identifying and Fixing Incorrect Ages of Old Globular Clusters

Three out of four spiral galaxies studied here (and all but a few in the 38 PHANGS-HST sample) should have few intrinsically correct intermediate-age clusters with high reddening (i.e., above the diagonal line in a log Age vs $E(B-V)$ diagram), since they do not have much dust around them. When data points are seen above the diagonal, these are usually due to the incorrect age estimates resulting from the age/reddening degeneracy, with old globular clusters being mistaken for intermediate-age clusters with large reddening. In the next section we show how various hybrid solutions can be constructed to remove most of the age-dating errors and improve the success fractions by 10 to 20 %, reaching values near 100 % in most cases.

## Procedures

Here we present the techniques used to correct the age estimates (and associated estimates of reddening and mass) that suffer from the problems described in Section [3](#sec:problems). For most of the young clusters, the original age estimates are reasonably accurate (i.e., within 0.3 dex as discussed in Section [2.2](#sec:hst_data)), and we use the original solar metallicity fits from (cite: turner21). However, for the likely old globular clusters we use a different set of rules.

![](ngc1433_7plot_may_16_2022.pdf)

For NGC 1433, NGC 3351, and NGC 628 we use three additional steps to fix most of the incorrect globular cluster ages:

1). Identify clusters which

are likely to be old globular clusters due to their position in the $U-B$ vs. $V-I$ color-color diagram (i.e., the OGC-box solution, where $-0.7 < U-B < 1.2$ and $0.95 < V-I < 1.7$), or their $V - I$ value (i.e., the VI-limit solution, where $V-I > 0.95$).

2). Fix ages for the identified clusters using a low-metallicity (1/50th solar) model and low maximum allowed $E(B-V) < 0.1$ mag, appropriate for most old globular clusters.

3). Identify potential young interlopers (i.e., young clusters with enough dust to give them colors similar to old globular clusters) using either H$\alpha$ flux (i.e., with H$\alpha > 3.0 \times 10^{-16}$ erg/s/cm$^2$/pixel, where pixel refers to MUSE pixels), CO intensities, or the presence of dust based on the HST image (see Section [6](#sec:halpha_co_dust)). We use ages from the original solar metallicity model for these young interlopers.

For the very dusty NGC 1365 we use a slightly different method:

1). Use a smaller OGC-box to identify old globular cluster candidates (i.e., the orange box in the bottom right panel of Figure [7](#fig:cc_4plot); $-0.6 < U-B < 0.5$ and $0.95 < V-I < 1.5$). We use the same methods described in steps 2 and 3 above to infer appropriate ages for these objects.

2). Identify the high reddening objects (i.e., V-I $>$ 1.5), which are nearly all young, dusty clusters, and use a solar metallicity model, *but require higher values of $E(B-V)$* (1.5 $<$ $E(B-V)$ $2.5$ mag). This allows the reddest, dustiest clusters to reach the young ages that are correct for them.

3). Identify "old interlopers" present in the sample of high reddening objects using H$\alpha$ flux (i.e., H$\alpha < 3.0 \times 10^{-16}$ erg/s/cm$^2$/pixel - note the inequality is in the opposite sense compared to young interlopers), CO intensities, or the presence of dust. We use the original solar metallicity model solution for these objects.

In principle, we expect H$\alpha$ to provide the best means of identifying interlopers, since it is generated by photo-ionization driven by massive young stars in the clusters themselves, while CO and dust are found in region that are statistically more likely to have

young stars and clusters. We will revisit this question in Section [6.2](#sec:dust_halpha).

More details used to illustrate these steps are included in the next subsection. We will refer to the results from these procedures as

’hybrid’ solutions. It is important to note that the results presented in this paper are specific to the PHANGS-HST pipeline, including filters, assumed SSP model, etc, and that other works may have different numbers of objects with bad ages and different levels of improvement.

## Solutions for NGC 1433 - improvement by $\approx$18% in the overall success fraction

Figure [8](#fig:7plot-n1433) shows an example of the primary diagram that will be used in this section of the paper to illustrate the success of the hybrid solutions. We show two different hybrid solutions: one based on the OGC-box, and one on the VI-limit solution. The VI-limit solution turns out to be slightly superior for all four galaxies. The OGC-box approach is retained in the paper to help demonstrate a number of important points.

The top left panel shows the log Age vs. $E(B-V)$ diagrams for the original pipeline solution; the top-middle panel shows the hybrid OGC-box solution; and the top-right panel shows the hybrid-VI-limit solution. The central plot shows the $U-B$ vs $V-I$ color-color diagram, with the blue objects in the OGC-box highlighted throughout the figure. The bottom panels show the log Age vs. log Mass diagrams. Snapshots of various objects are also shown and labeled throughout the diagram to illustrate various points.

We first note that clusters with colors within the OGC-box clearly dominate the region above the diagonal line in the original log Age vs. $E(B-V)$ diagram, with one clump at very young

ages (log Age $\mathrel{<\kern-1.0em\lower 0.9ex\hbox{$\sim$}}$ 7), and a second near log Age $\approx$ 8. It turns out nearly every single one of these clusters was identified as having a bad pipeline age through the independent visual examination described in Section [4](#sec:approach) and shown in Figure [6](#fig:n1433_cc_bad12).

We next examine the top-middle panel that shows results using the OGC-box solution. Here, the OGC-box clusters are no longer above the diagonal line, and all but three objects have moved to ages older than log Age = 9 where they belong, with the largest concentration having log Age = 10.1. The number of old globular clusters (i.e., with log Age greater than 9.5) has gone from 1 to 43; a much more realistic result (e.g., see (cite: lomel22)).

We find that the limiting issue for the hybrid OGC-box approach is the lack of reliable U-band photometry, which appears to be the issue for the three objects (# 900, # 1689, and # 2250) which remain above the diagonal line when using this approach.

The snapshot of # 1689 shows this it is an old globular cluster, but with colors outside the OGC-box (possibly due to large U-band uncertainties), so its age has not been corrected. This lead us to identify old globular clusters using a simpler $V-I$ $>$ 0.95 cut, as shown by the cyan points and the upper-right panel. All three of the clusters remaining above the diagonal from the OGC-box solution now move to older ages, and we reach a 40$/40=100$ % success rate for the objects above the diagonal! Hence the VI-limit approach to identify potential bad ages works extremely well for NGC 1433. This is because there is insufficient dust to redden young objects enough to reach the OGC-box.

There are 191 total Class $1 + 2$ clusters in Figure [8](#fig:7plot-n1433). If we assume that all objects below the diagonal have correct ages, the hybrid OGC-box solution goes from an overall correct age fraction of 79 % = (191 - 40) / 191 = 151/191, to 98 % = (191 - 3) / 191 = 188/191.

For the hybrid $V-I$-limit solution the result is 191/191 = 100%; a 21 % improvement from the original solution.

We have checked our assumption that all clusters below the diagonal have correct ages by manually examining all the objects in NGC 1433. Based primarily on a visual examination of the HST image for the presence or absence of H$\alpha$ emission, we estimate that three objects appear to have ages that are overestimated while three others are underestimated, hence the correct percentage below the diagonal is (141 - 6) / 140 = 96 % for NGC 1433. Taking this into account would therefore only reduce the overall success fraction by about 3 %, as summarized in Table [1](#tab:table1).

A comparison of the bottom-left panel in Figure [8](#fig:7plot-n1433) with the two hybrid solutions to the right shows that

roughly 20 clusters have changed age estimates from log Age $\approx 8$

to older than log Age $\approx 9$, and most of these are at the high mass end. Therefore the improved age solutions from the OGC-box and VI-limit approaches will likely affect the overall age and mass distributions at a significant level. We will examine the impact of age corrections on the NGC 628 cluster population in Section [7](#sec:age_and_mass).

![](ngc3351_7plot_may_16_2022_trim.pdf)

## Solutions for NGC 3351 - improvement by $\approx$9 % in the overall success fraction

Figure [9](#fig:7plot-n3351) shows results for NGC 3351, which has the second lowest SFR in our sample but a fair amount of dust, especially in the inner starburst ring. We find 41 of 317 clusters have pipeline age-dating results that put them above the diagonal in the top-left panel. These clusters have questionable ages, as discussed earlier. The log Age vs. $E(B-V)$ plot when ages of clusters in the OGC-Box (blue points) have been corrected is shown in the top-middle panel. While most of the blue points have moved from above the diagonal to the bottom right, appropriate for old globular clusters (e.g. object # 3815), 12 points remain above the diagonal.

These are evaluated below, and the numbers are summarized in Table [1](#tab:table1).

![](ngc628_7plot_may_16_2022.pdf)

Four of the six red points (i.e., with colors that are not in the OGC-box) above the diagonal in the top middle panel have very faint or missing U-band measurements, so are not identified as potentially having bad ages using the OGC-box selection because of the lack of a $U - B$ value.

The ages for these clusters do get fixed (changed from young ages to old), however, if we select objects using the VI-limit method (top -right panel). This is the primary reason the hybrid VI-limit solution looks better, with only seven points remaining above the diagonal.

On the other hand, there are five young "interlopers" in the OGC-box and VI-limit solutions, since they have values of H$\alpha$ $>$ $3.0 \times 10^{-16}$ erg/s/cm$^2$/pixel (e.g., see snapshot of # 2565). These are the five blue or cyan points that remain above the diagonal in the top middle and top-right panels.

One of these objects (# 2881) turns out to be a "false interloper": the lower resolution MUSE observations indicate this cluster has H$\alpha$ emission (picked up from nearby regions), while the higher resolution HST H$\alpha$ observations shows there is no associated line emission at the location of the cluster itself.

This "resolution problem" is one of the primary failure modes of our current approach, and happens in approximately 20 % of the cases where the H$\alpha$ flux indicates the presence of a young interloper. Future, high resolution H$\alpha$ observations from HST for the entire PHANGS galaxy sample, would solve this particular problem, and significantly improve the age-dating. H$\alpha$ observations using HST are now planned for 19 of the 38 galaxies in cycle 30 (i.e., the MUSE galaxies in the PHANGS-HST sample: proposal 17126 - PI = Chandar).

The remaining objects above the diagonal in the hybrid OGC-box solution are more of a mixed-bag, as summarized in the notes to Table [1](#tab:table1). They include a background galaxy, another object with the resolution problem discussed for object \# 2881, and an object with $V - I$ = 0.94 (i.e., just missing the color cutoff for the OGC-box).

Turning our attention to the log Age vs log Mass diagrams in Figure [9](#fig:7plot-n3351), we can see that many clusters now have shifted from estimated ages between 8 $<$ log Age $<$ 9 to older ages with log Age $>$ 9. The apparent deficit of clusters between 10 and 50 Myr is a well-known age-dating bias, which results when the model predictions reverse direction and loop back on themselves, giving similar predicted colors over a broad age range (e.g., (cite: chandar10b)). The resulting ‘gap’ is observed at some level in all four galaxies. This particular artifact only shifts age estimates by up to $\pm 0.3$ in log age, significantly less than the factor of ten we define as "catastrophic" errors in our accounting.

The total number of clusters in Figure [9](#fig:7plot-n3351) is 317. If we again assume that ages for all objects below the diagonal line are correct, and four of the objects above the diagonal have good ages (as indicated from the VI-limit solution) the success fraction goes from being 88 % correct

for the original pipeline solution, to 97 %

for the hybrid OGC-box solution, and 99 %

for the hybrid VI-limit solution (this solution drops to 97% if we account for a handful of incorrect age estimates below the diagonal line based on our review of NGC 1433). Hence we have improved the overall age dating by $\approx$ 9 %.

Similarly the number of old globular clusters (i.e., with log Age $>$ 9.5) increases from just 7 to 44 for the hybrid OGC-box solution, and to 50 for the hybrid VI-limit.

## Solutions for NGC 628 - improvement by $\approx$9 % in the overall success fraction

Figure [10](#fig:7plot-n628) shows the results for NGC 628, the galaxy with the second highest SFR in our sample. We find 70 out of 489 data points above the diagonal in the standard model in the top left panel, which represent questionable age estimates. As we found for NGC 1433 and NGC 3351, many of the objects left above the diagonal line after identifying and correcting ages in the OGC-box are those missing U-band measurements (11 of 23), although for NGC 628 most of these are because they are outside the field of view. This is why the VI-limit model is more successful at moving points above the diagonal to older ages than the OGC-box method for NGC 628.

There are only three remaining young interlopers in NGC 628 for the VI-limit model based on H$\alpha$ emission values greater than $3.0 \times 10^{-16}$ erg/s/cm$^2$/pixel (i.e., the cyan points above the diagonal in the upper right panel). One of these (object \# 1206) is questionable, since it is near the outskirts of a

nearby young association (see snapshot in Figure [10](#fig:7plot-n628)), but may not be associated with it.

![](7plot_ngc1365.pdf)

The next set of objects ($N = 8$) we consider are barely above the diagonal line in the upper left panel and have V-I colors just blueward of the $V-I$ $>$ 0.95 mag cutoff, ranging from 0.75 to 0.93 mag. Hence these objects are not selected by either the OGC-box or VI-limit criteria for age-correction. Seven of the eight are assigned log Age $\approx 8.5$, which appears to be correct based on the absence of H$\alpha$ emission in these objects. Hence the placement of the cutoff at $V-I$ $>$ 0.95 mag appears to be accurate these objects. Table [1](#tab:table1) summarizes the various objects above the diagonal, and whether they appear to be good or bad age estimates.

If we assume that all ages below the diagonal are correct, plus nine additional objects above the diagonal are correct as discussed above,

the success fraction improves from 88 %

for the original pipeline solution, to 98 %

for the hybrid OGC-box solution, and 99 %

for the hybrid VI-limit solution (97 % if we account for a few incorrect age estimates below the diagonal line based on our NGC 1433 visual review). Hence we have improved the success fraction by $\approx$ 9 %.

The number of old globular clusters (i.e., with log Age greater than 9.5) increase from none in the original pipeline solution to 53 (65) for the hybrid OGC-box (hybrid VI-limit) methods, again yielding much more realistic figures.

## Solution for NGC 1365 - improvement by $\approx$13 % in the overall success fraction

Figure [11](#fig:7plot-n1365) shows the results for NGC 1365, which has the highest SFR in our sample and in the entire PHANGS-HST sample (cite: lee22). We find 128/635 = 20 % of the data points are above the diagonal in the top left panel. Unlike the other galaxies, most of these clusters belong here, since they are young and dusty.

Because of this,

we use a somewhat different approach for correcting bad cluster ages in NGC 1365, as described in Section [4](#sec:approach).

The first difference is how we select potential old globular clusters. We use a smaller OGC box, with $-0.6 < U-B < 0.5$ and $0.95 < V-I = < 1.5$ to avoid the ‘300 Myr plume’ just below the OGC-box in Figure [11](#fig:7plot-n1365). This is discussed in more detail in Section [5.6](#sec:300myr). We then identify clusters redder than $V-I = 1.5$ on the right side since these very red clusters appear to nearly all be young, unlike the other galaxies. Their youth is indicated by strong CO emission (black points) for nearly all clusters with $V-I$ measurements $>$ 1.5 mag in Figure [7](#fig:cc_4plot). We call these the "high-red" objects in what follows.

The second change allows the SED-fitting routine to reach the correct young age solution for the highly reddened, young clusters by restricting $E(B-V)$ values to be in the range 1.5 - 2.5 mag

(i.e., addressing Problem \# 3 in Section [3.3](#sec:common_problem_3), and using the procedure described in Section [5.1](#sec:procedure)).

A visual examination of these high-red objects confirms that nearly all are very young, with strong H$\alpha$, strong CO, and large amounts of dust around them.

Cluster \# 1567 (see Figure [11](#fig:7plot-n1365)) illustrates the problem. It is in the very dusty central region of NGC 1365, has strong H$\alpha$ and CO emission, and lots of young blue $\approx$few Myr objects nearby. The original pipeline SED solution assigned it a log Age = 9.1 and a reddening $E(B-V)$$=1.47$ mag (near the adopted maximum of 1.5 mag).

For the solution to reach its likely age of $\approx 5$ Myr, an $E(B-V)$ around 2.5 mag is required. So for clusters with very red V-I colors in NGC 1365 (i.e., the green points in Figure [11](#fig:7plot-n1365)), we adopt SED-fitting solutions with solar metallicity and values of $E(B-V)$ between 1.5 and 2.5 mag. This fitting finds a solution of log Age = 6.48 and $E(B-V)$ = 2.36, for object \# 1567, a much better estimate for this cluster. Most of the other highly reddened objects that were originally given old ages are now correctly fit with ages $\approx 5$ Myr plus high reddening.

Because most of the objects in the high-reddening subsample are young rather than old, we switch the direction of the inequality used to identify "young interlopers" in the OGC-box and now identify "old interlopers" in the high-reddening subsample instead. These are defined as objects with weak H$\alpha$ flux (H$\alpha <  3.0 \times 10^{-16}$ erg/s/cm$^2$/pixel - i.e., old globular clusters). In these cases we use the original SED solution for the age, $E(B-V)$, and mass of the cluster. This leads to only 8 of the 43 high-red clusters being assigned ages older than log Age = 7.5; the other 35 are all assigned ages younger than 10 Myr (upper-right panel in Figure [11](#fig:7plot-n1365)), which is supported by visual examination.

NGC 1365 has essentially the same number of clusters above the diagonal after age corrections are made (i.e., N = 120), as before (i.e., N = 128), unlike the first three galaxies where most of the objects above the diagonal are moved to older ages in the hybrid solutions. While roughly 30 old globular clusters change from intermediate pipeline ages to old ages (blue points), an approximately equal number of clusters which were originally given incorrect old and intermediate ages by the PHANGS pipeline have hybrid solutions which move them in the opposite direction, to very young ages (green points). The bottom plots in Figure [11](#fig:7plot-n1365) show the log Age vs. log Mass diagram for the standard (solar) solution on the left and the hybrid solution on the right. The number of old globular clusters (i.e., with log Age greater than 9.5) in the hybrid solution

is 55, similar to the other three galaxies in this pilot study.

A possible contaminant in our sample of very red clusters might be background galaxies. Since our candidate clusters have been selected based on human classifications (cite: whitmore21) we expect this to be a rare occurrence. In addition, a secondary visual check of all the cluster candidates in the inner region of NGC 1365, where the reddest objects are found, resulted in only one object that appeared to be a possible background galaxy.

The total number of clusters in Figure [11](#fig:7plot-n1365) is 635. It is more difficult to estimate the improvement in the success fraction for NGC 1365 since objects are moving both into and out of the region above the diagonal line. However, a rough estimate can be made based on the census of good and bad ages in Table [1](#tab:table1). This leads to estimates of 84 %

for the original pipeline solution and 97 %

for the hybrid ogc/high-reddening estimate, an improvement of 13 %.

In addition, our estimate of 96 % for the success rate below the diagonal based on a visual check in NGC 1433 is clearly too high for NGC 1365 due to the high level of chaotic dust in the inner region of this galaxy. A spot check of the success fraction below the diagonal line indicates that a value of 90 % is more appropriate. In this case, our overall success fraction would fall from 97 % to about 92 %, as reported in Table [1](#tab:table1).

The recent JWST observations of NGC 1365 ((cite: whitmore22),

(cite: lee22b)) provide an additional check on our age estimates. One result from this work is the finding that 21 micron flux is an excellent predictor of whether a cluster is old (faint or missing at 21 micron) or young (bright at 21 micron). A check of all young class 1 and 2 clusters from the human classified compact cluster catalog (cite: whitmore21) with hybrid OGC/high-red age estimates log Age $<$ 7 and log Mass $>$ 6, finds that 21/24 = 88 % clusters have a value of 21 micron brightness $<$ 23 mag (abmag, 0.15 arcsec radius aperture, see (cite: whitmore22) for details), as expected. Similarly, 17/20 = 85 % of the old log Age $>$ 9.5 and log Mass $>$ 6 clusters have a a values of 21 micron brightness $>$ 23 mag, as expected. Combining these two estimates yields 38/44 = 86 $\pm$ 6 %, in reasonable agreement with the estimate of 92 % accuracy in Table [1](#tab:table1).

![](300myr_4plot_trim.pdf)

## The 300 Myr ‘plume’ in NGC 1365

As briefly mentioned above, and shown in Figures [7](#fig:cc_4plot), [11](#fig:7plot-n1365), and [12](#fig:300myr_plume), another somewhat unique characteristic of NGC 1365

is the large number of intermediate age clusters,

many of which form a reddening ‘plume’ trailing from a position on the SED track appropriate for 300 Myr clusters toward the bottom right of the $U-B$ vs. $V-I$ diagram. A visual examination shows that most of these are located just outside strong dust lanes in the inner region of the galaxy, which explains their relatively high reddening values.

There are approximately 60 of these $\approx$300 Myr clusters (log Age around 8.7 in the upper right panel in Figure [11](#fig:7plot-n1365)).

We believe this configuration of intermediate-age clusters is a feature of how barred spiral galaxies create new clusters (e.g., (cite: sormani20), (cite: whitmore22), (cite: schinnerer22)).

As the gas and dust move inward

along the bar it triggers star formation, primarily in the outer edge of the dust lane. After the stars and star clusters form they fairly rapidly decouple from the dust and gas,

since the stellar components have less dissipation than the gas. (cite: sormani20) estimates that it only takes about 5 Myr to decouple. While the gas spirals into the central region, creating the star-forming ring and inner disk, most of the stars and star clusters traverse slightly outside the region of gas and dust, populating what are called "overshoot" regions. The orbits of the star clusters formed in this way can take many shapes, as shown in Figure 8 of (cite: sormani20). For example, a large fraction of the stars will follow X-shaped box orbits, precessing to occupy regions which are roughly 45 degrees from the plane of the inner disk after several orbits.

This puts the intermediate-age clusters near, but not behind, the dust lanes for a large fraction of their orbit.

Figure [12](#fig:300myr_plume) shows two regions where intermediate-age clusters are enhanced, roughly 45 degrees from the plane of the inner star forming disk. The corresponding region in the color-color diagrams are also shown. We find that all of the objects in Region 1 are consistent with being roughly 300 Myr intermediate-age clusters. In addition, the objects in Region 3 (the far side of the galaxy - see Figure [12](#fig:300myr_plume) and (cite: elmegreen09) ) appear to have more dust, as expected, hence explaining the higher reddening, as shown by their position in the 300 Myr plume in the color-color diagram. Other younger overshoot regions near the top of Figure [12](#fig:300myr_plume) are discussed in Whitmore et al. 2022 in press, and Schinnerer et al. 2022 in press.

A younger region in the inner star formation ring (Region 2) is shown by the red outline and points in the color-color diagram. Most of these are consistent with ages in the range 1 to 10 Myr, with values of reddening from zero to about A$_V$ = 4 mag.

![](sed_2_halpha_vs_co_jun_11_2022.pdf)

# Using H$\alpha$, CO, or Dust to Identify and Fix Incorrect Ages of Interlopers

We have shown throughout this work that young, reddened clusters and old globular clusters can have similar broad-band colors, and that additional information is needed to separate the two.

In this section we explore how well the following star-forming tracers distinguish between the two cases: H$\alpha$ flux from MUSE, the CO intensity from ALMA, and the dust strength from HST images.

## Comparison between H$\alpha$ and CO Flux

Here we assess whether H$\alpha$ flux or CO intensity is better at identifying young interlopers.

We are fortunate to have high resolution, archival H$\alpha$ images from HST for three of our pilot galaxies (NGC 628, NGC 1433, and NGC 3351), which we use as a starting point. Over half of the PHANGS-HST sample also have H$\alpha$ measurements from ground-based MUSE IFU observations, including all the galaxies studied here, so we will use the MUSE H$\alpha$ measurements as our primary tool for the broader sample, even though they are a factor of $\approx$10 lower resolution than the HST observations.

Figure [13](#fig:co_halpha_4plot) shows the MUSE H$\alpha$ flux vs. ALMA CO intensity measured at the location of each cluster for all four galaxies (red points). Note that a number of clusters are missing from this diagram because no CO flux is measured. An examination shows that the missing sources are generally found between spiral arms or in the bulge, hence they are unlikely to be young interlopers in any case. Clusters with broad-band HST colors that place them in the OGC-box (defined in Section [4](#sec:approach))

are shown as the blue points.

### NGC 1433

We start by visually inspecting ten clusters in NGC 1433 with very faint H$\alpha$ emission (i.e. HII regions) in the HST images, to get a feel for the faintest detectable level of H$\alpha$ emission in the data. Overall, we found a good correspondence between the presence of H$\alpha$ emission in the high resolution HST images and the lower resolution MUSE observations - when we see H$\alpha$ emission in one, we can also detect it in the other. From this visual inspection, we set an approximate flux limit for the number of counts that separates clusters with and without H$\alpha$ emission (dashed green horizontal line in the upper left panel in Figure [13](#fig:co_halpha_4plot)); *clusters above this line are all expected to be young*. In NGC 1433 this separation was originally set at $2.0 \times 10^{-16}$ erg/s/cm$^2$/pixel, as shown in Figure [13](#fig:co_halpha_4plot). While there is some variation in the exact flux limit from galaxy to galaxy, we always find values close to $\approx3.0 \times 10^{-16}$ erg/s/cm$^2$/pixel, and hence adopt this value during final processing, as described in Section [4](#sec:approach).

For NGC 1433, in the upper left panel of Figure [13](#fig:co_halpha_4plot), we find that no clusters shown as blue points from the OGC-box are H$\alpha$ emitters, because they are all below the green horizontal line. This is consistent with our discussion in Section [5.2](#sec:hybrid-1433), where all NGC 1433 objects in the OGC-box appear to be old globular clusters: there are no reddened, young interlopers.

A criteria of H$\alpha > 3.0 \times 10^{-16}$ erg/s/cm$^2$/pixel identifies young interlopers correctly 100 % of the time in NGC 1433.

We make a similar estimate for CO intensity using the same ten clusters with weak H$\alpha$, and show the lowest value as the vertical yellow line. Here, *clusters above a CO intensity value of 2 K km s$^{-1}$ are predicted to be young*. In this case, however, the CO measurements predict that four clusters in the OGC-box shown as blue points fall to the right of the line, i.e. they should be young interlopers, at least according to the CO intensity. Visual examination indicates that these are actually all likely to be old globular clusters, and the CO emission is not actually associated with the clusters.

We illustrate this situation in the snapshots of source \# 1687 in the upper left panel of Figure [13](#fig:co_halpha_4plot).

The top snapshot shows the B-V-I image. We find the object is isolated, and has a yellow color typical of old globular clusters. The middle diagram shows the H$\alpha$. We find weak H$\alpha$ emission (in red) spread evenly throughout the image, i.e., there is no evidence that the source has an HII region associated with it. The bottom snapshot shows the CO intensity in red. We find that the object is on the edge of a strong CO region just as it intersects with the central CO ring of NGC 1433. Hence, at least in NGC 1433, our experiments indicate that H$\alpha$ is much better at identifying young, reddened interlopers than is CO. This makes sense, since H$\alpha$ emission is more closely associated with recently formed clusters than CO emission is (e.g., (cite: chevance22)).

### NGC 3351

![](ngc3351_hst_halpha_vs_muse_2plot_trim.pdf)

The upper right panel in Figure [13](#fig:co_halpha_4plot) includes the same diagram for clusters in NGC 3351. The distribution of cluster measurements looks quite different than in NGC 1433, being nearly bimodal rather than continuous. This is due to clusters found in the inner star forming ring (see Figures [1](#fig:4x2_image) and [14](#fig:Halpha_2plot-n3351)) having higher CO and H$\alpha$ values

than nearly all the clusters in the outer part of the galaxy.

The separation of H$\alpha$ (CO) emitting vs. non-emitting clusters shown as the green horizontal line (yellow vertical line) was determined using the procedure described above for NGC 1433, this time for NGC 3351. In the lower ‘clump’ of points, we find two sources in blue above the green line, which are predicted to be reddened young clusters (i.e., young interlopers) within the OGC-box. We include snapshots for the object # 2565 (see also Figure [9](#fig:7plot-n3351)). These show clear H$\alpha$ emission in the middle snapshot, supporting the idea that this is a young, reddened cluster, or young interloper. This object’s location to the right of the vertical yellow line indicates that the CO measurement would also suggest it is a reddened, young cluster, as confirmed by the bottom snapshot for # 2565.

Next we examine object # 3723 in Figure [13](#fig:co_halpha_4plot). The three associated HST snapshots

show the object is in a very dusty, H$\alpha$ and CO-rich area, and hence is a clear young interloper, as also appropriate for its location relative to the green and yellow lines. It is located in the strongly star-forming ring near the center of NGC 3351.

While these two objects would be correctly identified as young interlopers using both the green and yellow lines, we note the presence of five objects near the bottom of the panel for NGC 3351 that would be incorrectly identified as young interlopers by the CO intensities since they are to the right of the yellow line.

### H${\alpha}$ measurements in NGC 3351: MUSE vs. HST

We now assess how well the lower-resolution MUSE H$\alpha$ observations perform in identifying young interlopers compared with high resolution HST-H$\alpha$ images in the crowded star-forming ring of NGC 3351. In Figure [14](#fig:Halpha_2plot-n3351) we compare the MUSE HA6562_FLUX values from Figure [13](#fig:co_halpha_4plot) with HST F657N (H$_{\alpha}$) measurements made from 2 pixel aperture photometry. In order to (approximately) subtract out the continuum and identify sources with H$_{\alpha}$ line emission, we subtract the F814W HST magnitude, and normalize the measurements so objects with no line emission

have a positive F657N - F814W magnitude, as shown by the orange dashed line.

The left panel of Figure [14](#fig:Halpha_2plot-n3351) shows that two clusters are identified as young interlopers based on HST H$_{\alpha}$ measurements, the blue points to the right of the vertical orange line. One of these (# 3752) clearly has strong H$_{\alpha}$ emission in the H$\alpha$-I-B

image shown on the right, while the other is in the outer part of the galaxy and also shows clear but weaker line emission.

These are the only two young interlopers within the OGC-box identified from higher resolution HST H$_{\alpha}$ imaging, and contrasts with the eight, mainly incorrect identifications, made from the MUSE HA6562_FLUX (blue points above the green horizontal line).

We examine these sources in the high resolution HST image shown on the right in Figure [14](#fig:Halpha_2plot-n3351). Three of these clusters (2881, 3529, and 3835) have measured H$\alpha$ emission from MUSE but not from HST images. All three appear to be old globular clusters and not young interlopers at higher resolution.

Two other clusters however, (3724 and 3729) have uncertain classifications, even at HST resolution. These do not have associated H$_\alpha$ emission, but are in crowded regions with other very young, H$_{\alpha}$ emitting sources. The last 2 clusters are further out in NGC 3351 (not shown in Figure [14](#fig:Halpha_2plot-n3351)), with H$_{\alpha}$ in the region but not directly associated with the source, and hence are unlikely to be young interlopers. For comparison, we point out two young, H$_{\alpha}$ emitting clusters which do not have colors in the OGC-box: cluster \# 3009 has an estimated age of 3 Myr and strong H$_\alpha$ emission in the HST image, and cluster \# 3300 is somewhat older at $\approx8$ Myr, and has had time to clear out the H$_\alpha$ emission around it.

In summary, we find that higher resolution H$_{\alpha}$ observations from Hubble improve the age estimates for five of eight clusters in the OGC-box within NGC 3351 by showing that while there is H$_{\alpha}$ emission in the region, it is not directly associated with the clusters. The age estimate for one cluster is identical between HST and MUSE, while for two others it remains ambiguous. NGC 1433 and NGC 628 have almost no clusters in the OGC-box with H$_\alpha$ emission detected by MUSE (none in NGC 1433 and only one in NGC 628), so the lower resolution H$_{\alpha}$ imaging does not have much impact in these galaxies.

There would likely be a major improvement in identifying young interlopers in NGC 1365 however.

We plan to use the PAH-emission from high resolution F335W JWST observations ((cite: lee22b), (cite: whitmore22)) to improve cluster age-dating in NGC 1365.

### NGC 628

The CO intensity vs. H$\alpha$ flux diagram for NGC 628 is shown in the lower left panel of Figure [13](#fig:co_halpha_4plot). It is fairly similar to the one for NGC 1433, but with even more clusters that would be incorrectly identified as young interlopers based on CO intensity.

The snapshots of object # 3829 show only a few small patches of H$\alpha$ which may or may not be associated with the cluster, and a position on the edge of strong CO flux, probably due to the resolution problem.

One object of particular note is the object in the far upper right of the panel.

This source has the highest CO and H$\alpha$ emission by a large margin. This is the "Headlight Cloud", as studied in (cite: herrera20).

### NGC 1365

The lower right panel in Figure [13](#fig:co_halpha_4plot) shows the distribution of clusters for NGC 1365. As expected based on our earlier discussion, this population looks quite different from those in the other three galaxies, with a large number of young interlopers indicated by both H$\alpha$ and CO intensities.

The snapshots only include B-V-I and CO for this galaxy since there is no HST H$\alpha$ image for NGC 1365. Object # 3723 is a typical example of a young interloper with both strong H$\alpha$ and CO. Object # 2476 shows a less obvious example

with a relatively small amount of dust and likely foreground CO. Hence the designation of this object as an interloper is uncertain. This source is close to the crossing of the yellow and green lines used to define young interlopers, as might be expected for an object with an uncertain designation.

In the case of NGC 1365 there are roughly 20 objects near the bottom right of the panel that would be incorrectly identified as young interlopers by the CO intensities since they are to the right of the yellow line but have no clear H$\alpha$ emission . Hence in all four of our target galaxies, using CO instead of H$\alpha$ to identify interlopers would result in more incorrect ages, ranging from 2 % more for NGC 1433 and NGC 3351 to 4 % more incorrect for NGC 628 and NGC 1365.

![](sed2_dust_halpha_4plot.pdf)

## Comparison between H$\alpha$ and Dust

In the previous section we found that H$\alpha$ emission is better at identifying reddened young interlopers that fall in the OGC-Box than CO emission at comparable resolution. Here, we assess how well a measure of dust from high-resolution HST-based maps ((cite: thilker23) - see Section [2](#sec:data)) compares with lower-resolution MUSE-based H$\alpha$ measurements at this same task. In principle, a measure of the dust should have several advantages over H$\alpha$ and CO. First, the structures can be identified and measured at the same physical scales as the clusters themselves since they are both from the the HST images. Second, we can assess the dust using the same HST images used for the photometry rather than requiring additional H$\alpha$ or CO observations. In particular for our project, the dust maps are available for all 38 PHANGS-HST galaxies rather than just the 19 galaxies with H$\alpha$ observed as part of PHANGS-MUSE.

Starting with NGC 1433 in the upper left panel of Figure [15](#fig:ha_co_4plot), we find the H$\alpha$ vs. dust diagram looks relatively similar to the H$\alpha$ vs. CO shown in Figure [13](#fig:co_halpha_4plot). There are no young interlopers according to the H$\alpha$ flux (i.e., no blue points above the green line), but five young interlopers according to our dust measurements (the five blue points to the right of the yellow line). A visual examination again confirms that none of these five are actually young clusters. We note that

cluster \# 1687 is the same false interloper seen in Figure [8](#fig:7plot-n1433) using CO, but in this case is triggered by a moderate amount of dust at the edge of the inner star formation region in NGC 1433, rather than by the presence of H$\alpha$ from the MUSE measurement.

In NGC 628 and NGC 3351, the dust measurements are again found to be less reliable than the H$\alpha$ measurements, but similar to CO at identifying young interlopers in the OGC-box (i.e. there are roughly a half dozen more candidates according to the yellow line which are below the H$\alpha$ criteria shown by the green line). NGC 1365 shows a large number of young interlopers using both H$\alpha$ and dust as a criteria.

We also note that in both NGC 3351 and NGC 1365 there is a tendency for the objects with the highest values of H$\alpha$ flux to have low dust values (i.e., they turn back toward the upper left in Figure [15](#fig:ha_co_4plot)). We believe this is due to a saturation problem since these objects are usually in the densest dust lanes.

We are currently investigating potential ways to improve this situation for our dust estimates, but for now we conclude that H$\alpha$ provides the best way to identify interlopers.

*Overall, we find that H$\alpha$ emission from MUSE, even at $\approx$factor of 10 lower resolution than the HST images, is better able to identify reddened, young clusters which are interlopers in the OGC-box or the VI-limit region, than CO intensity or relative dust strength*. This is probably because H$\alpha$ emission is directly tied to the recently formed clusters, whereas molecular gas and dust, which will form the next generation of clusters, has a weaker spatial association with the current generation of young clusters (e.g., (cite: schruba2010), (cite: kruijssen14), (cite: kreckel18), (cite: kruijssen19)).

Although the focus in this section has been on young interlopers, we note that with a change in the inequality sign (see Sections [4](#sec:approach) and [5](#sec:solutions)), H$\alpha$ (and CO and dust to a lesser extent) can also be used to identify old interlopers in the high-reddening region of the color-color diagram for NGC 1365.

![](sed2_n628_2plot.pdf)

# Impact of Incorrect Ages and Masses on Measurements of Cluster Distributions

## Age Distribution in NGC 628

In the previous sections we show that old globular clusters can often be incorrectly assigned young ages, with moderate to high reddening values, and that reddened young clusters can be mistaken for old globular clusters when standard SED-fitting techniques are applied to cluster populations. The resulting incorrect ages and masses can potentially impact cluster demographics, especially cluster age distributions. As an example, in this section we assess the impact on the cluster population in NGC 628, which was included in both the PHANGS-HST and LEGUS surveys.

We consider three sets of results: (i) the original age and mass estimates from the PHANGS-HST pipeline, which assume solar metallicity; (ii) the revised age and mass estimates where young interlopers were identified using the OGC-box; and (iii) the revised age and mass estimates where young interlopers were identified using the VI-limit approach.

Figure [16](#fig:n628_mass_age) shows the age distributions in NGC 628 (top panels) for the three different sets of results, and the corresponding age-mass diagrams (bottom panels). The dashed line along the lower edge of the age-mass diagrams shows how the luminosity limit of the sample translates into the age-mass plane. The dashed vertical and horizontal lines show that the regime used for the age distributions stays above this luminosity limit, so incompleteness should not play a role in the plotted distributions. The age bins used for each distribution are identical to those presented by (cite: adamo17) for NGC 628 based on the LEGUS survey (more details below).

It is clear from the bottom panels that the three different age-dating methods discussed in this paper impact the overall demographics. In particular, correcting the ages of clusters found in the OGC-Box, or via the VI-limit,

correctly moves a number of massive clusters originally found to have

log Age $\approx 8$ (i.e., the objects in the red oval) to older ages which are far more appropriate for old globular clusters. The resulting change in the age distribution is particularly noticeable for clusters more massive than log $(M/M_{\odot})>4.5$.

When fit to a power law $dN/d\tau \propto \tau^{\gamma}$, where $\tau$ = Age and $\gamma$ is the power law index, the original distribution (with incorrect ages for old globular clusters) has a best value of $\gamma=-0.18\pm0.02$ (top-left panel of Figure [16](#fig:n628_mass_age)).

However, after either of the two hybrid methods used to identify and correct the ages of red clusters are applied, this distribution is significantly steeper, with $\gamma \approx -0.7$ (top-middle and right panels). This shows that the determination of the power-law index of the age distribution can be quite sensitive to age-dating results.

Interestingly, the age distribution for lower-mass log $(M/M_{\odot})=4.2-4.5$ clusters is essentially unaffected by the age corrections (with best fits of $-0.59$ in all 3 cases), at least in NGC 628, because old, globular clusters tend to populate the high mass end around

log Age $\approx8$ (see Figure [10](#fig:7plot-n628) with color coding).

In Figure [17](#fig:n628_dndt2), we present the age distribution for our best cluster catalog (VI-limit), with double the number of

bins shown in Figure [16](#fig:n628_mass_age). Here, we are able to plot the age distribution out to log Age = 9.2 (above the completeness limit), as opposed to only out to log Age = 8.4 as used in (cite: adamo17) and Figure [16](#fig:n628_mass_age), due to the improved treatment of older ages. In addition, we include bins at lower ages than (cite: adamo17); noting that they follow the trend from the older points quite well. These longer baseline fits also show steep power law fits for the hybrid age-dating solutions, with $\gamma=-0.78\pm0.07$ for the high mass fit and $\gamma=-0.67\pm0.10$ for the low mass fit. If we remove the youngest age bin from the fit, due to concerns about potential inclusion of unbound associations (cite: bastian12b), the fits are only weakly affected, with $\gamma=-0.74\pm0.07$ for the high mass fit and $\gamma=-0.50\pm0.05$ for the low mass fit.

## Comparison with LEGUS Results for NGC 628

The cluster population in NGC 628 was studied previously by the LEGUS project; see (cite: grasha15) and (cite: adamo17). That collaboration used the same HST data (pointings and set of five filters) as used in this work, but use the Yggdrasil SED models (cite: zackrisson11). Several different combinations of SEDs, extinction laws and aperture corrections are provided in the LEGUS study. We have chosen to use the Padova isochrones, a Milky Way extinction law, and mean aperture corrections. The results do not vary much for the other combinations. The cluster properties discussed here can be directly compared with our own result from Figures [16](#fig:n628_mass_age) and [17](#fig:n628_dndt2), and Section [7.1](#sec:age_and_mass_phangs).

We find that 134 out of 864 (16%) class 1$+$2 human-classified LEGUS clusters are found in the

OGC-box.

This is similar to the 13% we find in the original PHANGS-HST pipeline results, as listed in Table [1](#tab:table1). The log Age vs. $E(B-V)$ diagram for LEGUS (not shown) is very similar to the upper left panel of our Figure [10](#fig:7plot-n628).

Nearly all of the clusters in the OGC-Box for the LEGUS results are above the diagonal, just like the results we presented earlier for the original PHANGS-HST pipeline age dating. In addition, there is only one object with log Age $>$ 9.5, similar to the zero objects with log Age $>$ 9.5 for the original PHANG-HST ages. This indicates that the LEGUS age-mass results have the same problems as the PHANGS-HST pipeline catalogs, which is reasonable since they adopted

similar fitting techniques and maximum reddening. This also suggests that the effects on their science results will be similar to those discussed in Section [7.1](#sec:age_and_mass_phangs).

(cite: adamo17) find a shallow power-law index for their (Class $1+2$) cluster age distribution, $-0.19 \pm 0.07$, based on the same three age intervals shown in the bottom panels of Figure [16](#fig:n628_mass_age).

We found essentially identical results at the high mass end (notwithstanding the systematic $\sim$0.4 dex difference in mass estimates) when we use the original PHANGS-HST catalog (top-left panel of Figure [16](#fig:n628_mass_age), which made similar assumptions during the age-dating procedure.

Hence, we find that the original PHANGS-HST log Age vs. $E(B-V)$ diagram, as well as the original PHANGS-HST log Age vs. log Mass and log Age vs. dN/dT diagrams, all look essentially identical to the LEGUS versions, showing that both studies are affected by the age/metallicity/degeneracy problem. Fixing this problem using the hybrid solutions introduced in the current paper results in steeper age distributions due to correctly moving $\approx30$ old globular clusters from their original ages of

log Age $\approx 8$ to ages log Age $> 9.5$.

The corrected age distributions for clusters in NGC 628 have important implications for the disruption of the clusters. We find that these distributions decline more-or-less continuously starting at very young ages, and have a similar shape for clusters at different masses. The simplest interpretation of this result is that the initial masses of the clusters do not strongly impact their dissolution time, often referred to as mass-independent disruption (cite: fall12; bastian12b). However, this is not a unique interpretation. Simulations using the MOSAICS framework (cite: kruijssen11) have shown that the disruption rate of clusters changes over time and with location, as clusters migrate from more to less disruptive environments after they form. Including these variations in the disruption rate often also results in a steep age-distribution, with only a weak dependence on the cluster mass, even when mass-dependent cluster disruption models are adopted (cite: kruijssen11; Miholics17). In any case, it is critical that observational works accurately establish the shape of the cluster age distribution in different galaxies, and in particular that they correct mistakes in the age-dating of old globular clusters.

![](dndt_n628_vilimit.pdf)

## Impact on Other Works

Our results make it clear that contamination by globular clusters may have had a significant impact on previous studies of cluster populations in star-forming galaxies. We have examined several previous papers on cluster demographics and found that many others were affected, at least at some level, by the same age/reddening/metallicity degeneracy challenges discussed in this work. These include (cite: whitmore99), (cite: hunter03), (cite: larsen04), (cite: fall05), (cite: gieles05), (cite: whitmore10), (cite: bastian12b), (cite: adamo17),

and (cite: moeller22), to list a few. This is not meant to be a comprehensive list; we expect that most works that rely on the results of age-dating stellar clusters that do not include H$\alpha$ or some other narrow-band measurement directly in the fits may be affected by these issues at some level. A systematic technique to identify ancient globular clusters using multi-band SED fits will be important going forward.

We recommend that in the future, authors consider including the following graphics in their manuscripts to make it clear to what degree their results might be affected by the age/reddening/metallicity degeneracies: (1) log Age vs. $E(B-V)$ diagrams, (2) color-color diagrams, (3) log Age vs. log Mass diagrams, (4) and color images of a few relevant objects.

Many early papers, like (cite: whitmore99) observations of the Antennae galaxies, relied on the WFPC2 camera for U-band photometry. The poor quantum efficiency of this instrument at shorter wavelengths, roughly a factor of ten less than for WFC3 at F336W, limited the scope of the problem because most old globular clusters have sufficiently faint U-band fluxes that they fell out of the samples. However, with the significant improvement to the blue imaging capabilities with the ACS/HRC and WFC3 cameras, many globular clusters now have measurements at shorter wavelengths which can lead to the problems highlighted in the current work.

Earlier in this Section, we described how incorrect age-dating can affect the steepness of the age distribution for star clusters. The preferential impact this problem appears to have on the high mass end (see Figure [10](#fig:7plot-n628) and the discussion in Section [7.1](#sec:age_and_mass_phangs)) could potentially also affect the conclusion of whether cluster destruction is mass-dependent or mass-independent, as discussed in a variety of papers (e.g., (cite: bastian12b), (cite: fall12), (cite: krumholz15)). Other potential results that may be affected are whether the upper end of the cluster mass function is best described by a power law or by a Schechter function (e.g., (cite: fall01), (cite: gieles09), (cite: adamo15), (cite: Messa18), (cite: mok19)), and estimates of the fraction of stars that are born in clusters, commonly known as $\Gamma$ ((cite: bastian08), (cite: kruijssen12), (cite: adamo15), (cite: chandar17)), among other important results.

These and other issues related to the effect of using the improved hybrid ages will be quantified in upcoming papers (Mok et al, and Chandar et al., in preparation).

# Future Work

The current study is a pilot program that will help improve the PHANGS-HST pipeline results for cluster ages, masses, and reddening. The solutions developed as part of the current paper are included as online MNRAS data products associated with this article. The original version 1 catalogs (cite: turner21), as well as those developed from the future PHANGS-HST pipeline, will all be included in the PHANGS-HST archives at <https://archive.stsci.edu/hlsp/phangs-cat>.

The techniques developed in the current paper might be described as a "post-facto" approach, that is, running multiple CIGALE models with a variety of metallicities and $E(B-V)$ limits, and then using other information (i.e., colors, CO intensities, H$\alpha$ flux, dust) to decide which solution is most appropriate for a given star cluster "after the fact". We are currently developing a more "ab-initio" approach, where priors, partially developed from the current study, will be used by the CIGALE software early in the process to select the correct peak (age/reddening/metallicity combination) in a multi-modal probability distribution

(see Figure [4](#fig:bimodal)).

One advantage of the ab-initio approach is that it will seamlessly make corrections for all the clusters, not just the ones with the most obvious problems (i.e., old globular clusters, heavily reddened clusters), as discussed in the current paper. Similarly, in the current approach there are discontinuities at the edges of regions identified in color-color space that can be eliminated.

One of the primary problems for the current project was the poor resolution of the CO and MUSE H$\alpha$ observations, as discussed in Section [5](#sec:solutions). H$\alpha$ observations using the Hubble Space Telescope for the missing galaxies will significantly improve this aspect (i.e., proposal 17126 - PI = Chandar). Similarly, improvements in the newly developed dust maps (e.g., Thilker et al. 2022) might also make this parameter more useful for measuring ages. In principle, it may be possible to use a wide variety of information (e.g., H$\alpha$, CO, dust, $E(B-V)$ Balmer decrement, etc.) simultaneously, rather than just H$\alpha$. In addition, we plan to make extensive tests of the effects of a variety of different parameters including metallicity, reddening laws, and the presence of binaries and horizontal branch stars, to name just a few.

Finally, results which include near-infrared photometry from JWST observations (cite: lee22b)

will be presented in future catalogs. This should be especially valuable for the population of deeply embedded clusters in dusty galaxies like NGC 1365, and will also help with age-dating since PAH emission is primarily associated with young regions ((cite: papovich07), (cite: popescu11)).

# Summary and Conclusions

New techniques have been developed to improve SED age estimates of star clusters for four galaxies from the PHANGS-HST survey. The project is designed as a pathfinder for the future development of an improved PHANGS-HST pipeline, and will eventually incorporate new measurements from JWST observations. The primary focus is to reduce or eliminate effects of the age/reddening/metallicity degeneracy for the two most pressing problems: 1) old globular clusters with age estimates that are too young (and reddening that is too high), and 2) highly reddened young clusters with age estimates that are too old (and reddening that is too low).

A problem with most current age-dating studies is the use of a single metallicity, generally solar. This results in a mismatch between the observations and SED models that invalidates the fitting process at the first step for many objects. In particular, old globular clusters have low metallicity that puts them above the solar SED models in a $U-B$ vs. $V-I$ diagram. The primary strategy used in the current paper is to identify likely old globular clusters from their position in a color-color diagram, and use 1/50th metallicity models with $E(B-V)$ constrained to be less than 0.1 mag.

Interlopers (generally young objects reddened by dust rather than age) are identified using H$\alpha$ flux information and are given the original solar metallicty solution. CO intensities and dust maps were also examined for this purpose, but found to be less effective.

The CIGALE software (cite: Boquien19) is used with Bruzual-Charlot models as the primary software tool. The observational inputs are five color (F275W, F336W, F435W, F555W, F814W) HST photometry from Version 1.1 of the PHANGS-HST pipeline (cite: turner21), and H$\alpha$ flux values from MUSE (cite: emsellem22). Secondary information is provided in the form of CO observations from ALMA (as part of the PHANGS consortium (cite: leroy21)), and dust models from (cite: thilker23).

The primary results are:

1\. Age-dating success fractions

are improved for the program galaxies by approximately 9 % (NGC 628), 9 % (NGC 3351), 13 % (NGC 1365), and 18 % (NGC 1433). Success is defined as limiting differences between manually estimated and predicted ages to less than a factor of ten. While these may seem to be relatively small improvements, for certain objects (e.g., old globular clusters) the difference can be 100 %. For example, the increase in the number of old globular clusters (i.e., log Age \> 9.5) goes from 0 to 65 for NGC 628. In addition, the majority of the incorrect ages for old globular clusters are systematically assigned values in the range 5 to 500 Myr. This can pollute the study of young and intermediate age cluster populations, impacting a variety of key science results.

2\. Two approaches are used for the three relatively dust-free galaxies (NGC 1433, NGC 3351, NGC 628). The first uses positions in the $U-B$ vs. $V-I$ diagram to identify potential Old Globular Clusters (i.e., the OGC-box approach). The second uses the VI-limit approach, so that U-band measurements are not required. The VI-limit approach appears to be better in all three galaxies, with overall success fractions of approximately 97 %. This method is expected to work well for all but a few of the dustiest PHANGS-HST galaxies.

3\. A somewhat different approach is used for the very dusty, high SFR galaxy NGC 1365. The primary differences are the use of a smaller OGC-box, and the inclusion of an additional high-reddening region of the color-color diagrams (i.e., where young clusters are often given incorrect estimates of old ages and low reddening - opposite to the problem with old globular clusters in the OGC-box). The overall success fraction for the new hybrid age estimates for NGC 1365 is approximately 92%.

4\. H$\alpha$ emission currently provides the best method of identifying and correcting "interlopers" from the default procedures outlined above (i.e. young interlopers in the OGC-box or VI-limit approach; old interlopers in the high-red region for NGC 1365).

This may be because H$\alpha$ emission is directly tied to the recently formed clusters, whereas molecular gas and dust has a weaker spatial association with the current generation of young clusters.

5\. An interesting aspect of NGC 1365 is a large number of $\approx300$ Myr clusters, and a reddening vector ‘plume’ of points from this population clearly visible in the $U-B$ vs.$V-I$ diagram. We believe this is a natural result of extensive star formation along the bar which eventually separates itself from the gas and dust which tends to spiral into the central region due to dissipation.

6\. The errors in age estimates from the age/reddening/metallicity degeneracy result in systematic rather than random errors. As such, they can affect a wide variety of science results. To demonstrate, we examine the power law index of the age distribution in NGC 628 and find it steepens by approximately 0.5 for high mass clusters. The improved ages also allow us to push to larger values of log Age, and hence increase the number of data points used in fits for various correlations.

The problems described in this paper are potentially endemic to a large number of studies from the past several decades. They are especially prevalent after WFC3 became available in 2010 with its excellent UV sensitivity and wide field of view. Before this, most old globular clusters fell out of age-dating star cluster samples in external galaxies due to the faint UV flux from their old populations. The effects of these problems may be quite widespread. Examples include the steepness of the age functions (e.g., see Section [7](#sec:age_and_mass)), the apparent cutoff at the high end of the mass function, the fraction of stars that form in clusters, and the specific frequency of old globular clusters in galaxies.

Potential evidence of the effects of the age/reddening/metallicity degeneracy in a sample of star clusters include: 1) the lack of old globular clusters in a sample (i.e., few or none beyond log Age = 9.5), and 2) a large number of intermediate-age clusters with high values of reddening (i.e., above a ‘diagonal’ running from log Age, $E(B-V)$ = (6.0, 1.0) to (9.0, 0.1)) .

We encourage authors to include diagrams such as color-color, log Age vs. $E(B-V)$, and log Age vs. log Mass plots to help identify the effects of this problem in different studies.

The original version 1 cluster catalogs developed by (cite: turner21) are available through the PHANGS-HST archives at <https://archive.stsci.edu/hlsp/phangs-hst>. The catalogs developed as part of the current paper are included as online MNRAS data products associated with this article.

The PHANGS-HST pipeline will use the lessons learned in this pilot study to develop an "ab-initio" approach within CIGALE, selecting peaks from the multi-modal probability distributions, as briefly described in Section [8](#sec:future_work). These new catalogs will be included in the PHANGS-HST archives at <https://archive.stsci.edu/hlsp/phangs-cat>.

# Acknowledgements

We thank the referee for several useful and constructive comments that lead to improvements in the paper. Based on observations made with the NASA/ESA Hubble Space Telescope, obtained from the data archive at the Space Telescope Science Institute. STScI is operated by the Association of Universities for Research in Astronomy, Inc. under NASA contract NAS 5-26555. Support for Program number 15654 was provided through a grant from the STScI under NASA contract NAS5-26555. FB and AB would like to acknowledge funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (grant agreement No.726384/Empire). MB gratefully acknowledges support by the ANID BASAL project FB210003 and from the FONDECYT regular grant 1211000. EW acknowledges support from the DFG via SFB 881 ‘The Milky Way System’ (project-ID 138713538; subproject P01). FB acknowledges funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (grant agreement No.726384/Empire). HAP acknowledges support by the National Science and Technology Council of Taiwan under grant 110-2112-M-032-020-MY3. JMDK acknowledges funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme via the ERC Starting Grant MUSTANG (grant agreement number 714907). COOL Research DAO is a Decentralised Autonomous Organisation supporting research in astrophysics aimed at uncovering our cosmic origins.

KG is supported by the Australian Research Council through the Discovery Early Career Researcher Award (DECRA) Fellowship DE220100766 funded by the Australian Government. KK and FS gratefully acknowledge funding from the German Research Foundation (DFG) in the form of an Emmy Noether Research Group (grant No. KR4598/2-1, PI Kreckel). PSB acknowledges financial support from the Spanish Ministry of Science, Innovation and Universities under grant number PID2019-107427GB-C31. RSK and MCS are thankful for support from the Deutsche Forschungsgemeinschaft (DFG) via the Collaborative Research Center (SFB 881, Project-ID 138713538) “The Milky Way System” (sub-projects A1, B1, B2 and B8) and from the Heidelberg Cluster of Excellence (EXC 2181 - 390900948) “STRUCTURES: A unifying approach to emergent phenomena in the physical world, mathematics, and complex data”, funded by the German Excellence Strategy. RSK and MSC also acknowledge funding from the European Research Council in the ERC Synergy Grant “ECOGAL – Understanding our Galactic ecosystem: From the disk of the Milky Way to the formation sites of stars and planets” (project ID 855130). TGW acknowledges funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (grant agreement No. 694343).

# Data Availability

The imaging observations underlying this article can be retrieved from the Mikulski Archive for Space Telescopes at <https://archive.stsci.edu/hst/search_retrieve.html> under proposal GO-15654. High level science products, including science ready mosaicked imaging, associated with HST GO-15654 are provided at <https://archive.stsci.edu/hlsp/phangs-hst> with digital object identifier

| Galaxy (star formation rate) | N 1433 (SFR = 0.56) | N 3351 (SFR = 0.87) | N 628 (SFR = 0.93) | N 1365 (SFR = 16.9) |  |
|:---|:--:|:--:|:--:|:--:|:--:|
|  |  |  |  |  |  |
| number of class 1 and 2 clusters (human classification) | 191 | 317 | 489 | 635 |  |
| number in OGC-Box (mainly old globular clusters) | 49/191 = 26 % | 56/317 = 18 % | 63/489 = 13 % | 88/635 = 14 % |  |
| number in VI limit region | 58/191 = 40 % | 75/317 = 24 % | 96/489 = 20 % |  |  |
| number in high red region (mainly young, dusty) |  |  |  | 43/635 = 7 % |  |
|  |  |  |  |  |  |
| standard solution, above diagonal (i.e., ages suspect) | 40/191 = 21 % | 41/317 = 13 % | 70/489 = 14 % | 128/635 = 20 % |  |
| hybrid OGC-box solution, above diagonal (i.e., ages suspect) | 3/191 = 2 % | 12/317 = 4 % | 23/489 = 5 % |  |  |
| hybrid VI-limit solution, above diagonal (i.e., ages suspect) | 0/191 = 0 % | 7/317 = 2 % | 12/489 = 2 % |  |  |
| NGC1365 solution, above diagonal (i.e., ages suspect) |  |  |  | 120/635 = 19 % |  |
|  |  |  |  |  |  |
| standard solution, old globular clusters (log Age $>$ 9.5) | 1/191 = 1 % | 7/317 = 2 % | 0/489 = 0 % | 22/635 = 3 % |  |
| hybrid OGC-box solution, old globular clusters log Age $>$ 9.5) | 43/191 = 23 % | 44/317 = 14 % | 53/489 = 11 % |  |  |
| hybrid VI-limit solution, old globular clusters (log Age $>$ 9.5) | 47/191 = 25 % | 50/317 = 16 % | 65/489 = 13 % |  |  |
| hybrid (NGC1365), old globular clusters (log Age $>$ 9.5) |  |  |  | 55/635 = 9 % |  |
|  |  |  |  |  |  |
|  |  |  |  |  |  |
| Reason remaining above diagonal using hybrid approach: |  |  |  |  |  |
|  |  |  |  |  |  |
| case \# 1 - Unreliable U-band - GOOD/BAD$^a$ age | OGC: 3/0, VI: 0/0 | OGC: 0/4, VI: 0/0 | OGC$^b$: 3/8, VI$^b$: 1/1 | 4/1 |  |
|  |  |  |  |  |  |
| case \# 2 - OGC-box interloper: - GOOD/BAD age | OGC: 0/0, VI: 0/0 | OGC: 3/3, VI: 3/2 | OGC: 1/0, VI: 1/0 | 14/4 |  |
|  |  |  |  |  |  |
| case \# 3 - VI-limit interloper: - GOOD/BAD age | OGC: 0/0, VI: 0/0 | OGC: 0/0, VI: 0/0 | OGC: 1/0, VI: 1/0 | 3/2 |  |
|  |  |  |  |  |  |
| case \# 4 - High red (N1365): - GOOD/BAD age |  |  |  | 32/7 |  |
|  |  |  |  |  |  |
| case \# 5 - $~$ 300 Myr plume (N1365): - GOOD/BAD age |  |  |  | 34/4 |  |
|  |  |  |  |  |  |
| case \# 6 - Resolution problem- GOOD/BAD age | OGC: 0/0, VI: 0/0 | OGC: 0/1, VI: 0/1 | OGC: 0/0, VI: 0/0 | 3/2 |  |
|  |  |  |  |  |  |
| case \# 7$^c$ - Artifact - GOOD/BAD age | OGC: 0/0, VI: 0/0 | OGC: 1/1, VI: 1/0 | OGC: 7/2, VI: 6/3 | 10/5 |  |
|  |  |  |  |  |  |
| Summary - OGC-box (remaining BAD ages above diag.) | 3/191 = 2 % | 9/317 = 3 % | 10/489 = 2 % |  |  |
| Summary - VI-limit (remaining BAD ages above diag.) | 0/191 = 0 % | 3/317 = 1 % | 5/489 = 1 % |  |  |
| Summary - N1365 (remaining BAD ages above diag.) |  |  |  | 24/635 = 4 % |  |
|  |  |  |  |  |  |
| Success % (assume 96 % and 90 % \[n1365\] below diag.) | 97 % | 97 % | 97 % | 92 % |  |

: Statistics for the Four Program Galaxies

$^a$ - Evaluation of whether good or bad age estimate (i.e., within a factor of ten). Based on a visual review of the B-V-I, H$\alpha$, and CO images.\
$^b$ - Unreliable U-band because off the edge of the image.\
$^c$ - Artifacts include cluster misclassifications (e.g., slightly saturated stars, close pairs of stars, background galaxies, ...), objects with colors that place them just outside of the color criteria so no correction is made, but should have been made (e.g., $V-I$ = 0.94), objects where the solution reverts to the original solar metallicity solution and that turns out to be wrong (e.g., an object with strong H$\alpha$ given an age of 100 Myr).

[^1]: Contact e-mail:<whitmore@stsci.edu>

[^2]: <https://archive.stsci.edu/hlsp/phangs-hst>

[^3]: It is important to note that most age-dating methods perform SED fits to age and reddening using all available photometric bands (e.g., F275W, F336W, F435W, F555W, F814W in our PHANGS-HST project), rather than fitting in the 2-dimensional color-color diagrams shown throughout this paper. The two color diagrams, however, often make it easier to visualize what is happening in the fit, and hence are used extensively in the current paper.

</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[1].key_parameters[0].evidence[0]",
  "value": "Bad age threshold = factor of 10 or more difference",
  "failed_quote": "A designation of \"bad age\" requires a factor of ten or more between the visually estimated age and the version 1.0 SED age estimate, as described in (cite: turner21)."
 },
 {
  "path": "reproducibility.data_public_as_stated.evidence[0]",
  "value": "HST imaging and high-level science products are public at MAST under GO-15654 and the PHANGS-HST archive.",
  "failed_quote": "The imaging observations underlying this article can be retrieved from the Mikulski Archive for Space Telescopes at https://archive.stsci.edu/hst/search_retrieve.html under proposal GO-15654."
 },
 {
  "path": "reproducibility.products_in_archive.evidence[0]",
  "value": "Original Version 1 catalogs are in the PHANGS-HST MAST archive, and the revised hybrid catalogs from this paper are included as online MNRAS data products and in the PHANGS-HST archive.",
  "failed_quote": "The original version 1 cluster catalogs developed by (cite: turner21) are available through the PHANGS-HST archives at https://archive.stsci.edu/hlsp/phangs-hst. The catalogs developed as part of the current paper are included as online MNRAS data products associated with this article."
 }
]
```

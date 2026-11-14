# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2020A%26A...643A...7G\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
#            The ALPINE-ALMA \[CII\] Survey:\
CGM pollution and gas mixing by tidal stripping in a merging system at $z\sim4.57$

# Introduction

Modern theories of galaxy evolution and cosmological numerical simulations predict that high-$z$ galaxies assembled their mass through a combination of cold gas accretion from the intergalactic/circumgalactic medium (IGM/CGM) and merging activity (e.g., (cite: Bower2006; Dekel2009; Hopkins2010; Vogelsberger2014; Schaye2015)).

Continuous baryonic flows are needed to replenish the gas content, fuel the star formation and drive the evolution of galaxies on the star-forming Main Sequence (e.g., (cite: Daddi2010; Rodighiero2011; Lilly2013; Speagle2014; Scoville2016)).

On the other hand strong dynamical interactions between galaxies, such as major mergers, can efficiently drive a significant amount of gas into the central regions (e.g., (cite: Barnes1991)) and both (i) boost the efficiency of star formation (see (cite: Elmegreen2000)), triggering starbursts (e.g., (cite: Sanders1996; Hopkins2006; DiMatteo2008; Bournaud2011)), and (ii) feed the growth of super massive black holes (SMBHs), thereby powering Active Galactic Nuclei (AGN) activity (e.g., (cite: GarciaBurillo2005; DiMatteo2005; Ginolfi2019)).

Moreover, mergers can significantly disturb and shape the morphologies of the galaxies involved, leading to the formation of tidal tails. Similarly to the ram pressure stripping ((cite: Gunn1972)) extensively observed in nearby galaxy clusters (e.g., (cite: Boselli2006; Moretti2018; Poggianti2019; Fossati2019)), tidal tails in merging systems are made of gas stripped from outer regions of galaxies, and extend well beyond the disks, on circumgalactic scales (e.g., (cite: Bridge2010; Wen2016; Guo2016; Stewart2011)). As a result, strong dynamical interactions between galaxies contribute to the intergalactic transfer of processed material as shown by recent simulations (e.g., (cite: Nelson2015; Angles2017; Hani2018)), and, at the same time, to the chemical enrichment of the CGM (e.g., (cite: Bournaud2011; Graziani2020)).

While tidal tails are well studied at different wavelengths in the local and in the intermediate redshift Universe (e.g., (cite: Poggianti2017; Vulcani2017)),

similar observations become challenging at higher redshift, mainly because of the diffuse and faint nature of the stripped gas.

A solution comes from the Atacama Large Millimeter/submillimeter Array (ALMA),

which enables us to possibly study the efficiency of tidal gas stripping and circumgalactic gas mixing in the Early Universe, by mapping the morphology and the kinematics of the CGM around merging systems, using bright far-infrared (FIR) lines, such as \[CII\] 158 $\mu$m (hereafter \[CII\]; see (cite: Carilli2013)).

\[CII\] has been recently detected in several star-forming galaxies at $z>4$ (e.g., (cite: Capak2015; Inoue2016; Pentericci2016; Bradac2017; Carniani2018; Matthee2019; Schaerer2020; Carniani2020)), some of which are experiencing major merger events (e.g., (cite: Oteo2016; Riechers2017; Pavesi2018; Marrone2018; Decarli2019; Jones2020)), or less disruptive gravitational interactions, usually revealed in combination with clumpy morphologies (e.g., (cite: Maiolino2015; Matthee2017; Jones2017; Carniani2018b)).

\[CII\] is generally emitted from multiple phases (ionized, neutral and molecular gas) of the interstellar medium (ISM; e.g., (cite: Vallini2013; Vallini2017; Lagache2018; Ferrara2019)), and it has been shown to be a good tracer of shock-induced emission in the surroundings of local interacting galaxies (e.g., (cite: Cormier2012; Appleton2013; Velusamy2014)).

In this paper we present a study of the morpho-kinematic properties of \[CII\] emission in/around a major merging system at $z\sim4.57$, observed as a part of the *ALMA Large Program to Investigate C$^+$ at Early Times* (ALPINE) survey, that measured \[CII\] and FIR-continuum emission in a statistical sample of more than a hundred normal galaxies with spectroscopic redshifts between $4<z<6$ (see (cite: LeFevre2020), (cite: Bethermin2020) and (cite: Faisst2019) for descriptions of (i) the survey objectives, (ii) the ALMA data-processing, and (iii) the multi-wavelength ancillary dataset, respectively).

The paper is organized as follows. In Sec. [2](#sec:Observations) we describe the ALMA data reduction process, in Sec. [3](#sec:Results) we report our results, and in Sec. [4](#sec:discussion) we discuss their implications. Conclusions are summarized in Sec. [5](#sec:conclusions). Throughout the paper we assume a flat $\Lambda$CDM cosmology ($\Omega_\Lambda = 0.7$, $\Omega_m = 0.3$, $H_0 = 70$ km s$^{-1}$ Mpc$^{-1}$), and adopt a Chabrier initial mass function (IMF; (cite: Chabrier2003)). At the redshift of our target vuds_cosmos_5101209780 ($\rm VC\_9780$; $z_{\rm [CII]}$ = 4.573), 1 arcsecond corresponds to 6.55 proper kpc.

# ALMA Observations

ALMA observations of the merging system studied in this work were conducted in Band 7 on 2 June 2018, during Cycle 5 (project 2017.1.00428.L, PI O. Le Fèvre), using a C43-2 array configuration with 45 antennae, and a total on-source time of 20 minutes.

The spectral setup consisted of two sidebands, each composed of two spectral windows with total bandwidths of 1.875 GHz and channel width resolutions of 15.6 MHz. The lower sideband was tuned to the expected \[CII\] redshifted frequency, according to the spectroscopic redshift extracted from the rest-frame UV spectrum (drawn from the VUDS survey; (cite: LeFevre2015; Tasca2017)). The upper sideband is used to search for FIR-continuum emission. The phase was centered at the rest-frame UV position of $\rm VC\_9780$ (see Sec. [3.1](#sec:ancillary); $\rm RA: 10h01m33.45s$; $\rm DEC:  +02d22m10.19s$).

The data were calibrated using the automatic pipeline provided by the Common Astronomy Software Applications package (`CASA`; (cite: McMullin2007)), version 5.4.0. No additional flagging was needed as the pipeline calibration output did not show any issue. The continuum map was obtained running the `CASA` task `tclean` (multi-frequency synthesis mode) over the line-free visibilities in all spectral windows.

The \[CII\] datacube was generated from the continuum-subtracted visibilities (CASA task `uvcontsub`), using the following setting: 500 iterations and a signal-to-noise ratio (S/N) threshold of $\sigma_{\rm clean} = 3$ in the cleaning algorithm, a pixel size of 0.15$''$ and a spectral binning of 25 km s$^{-1}$ ($\sim 29$ MHz). For both continuum and \[CII\] datacube we adopted a natural weighting of the visibilities to maximise the sensitivity.

We reach an average root mean square (RMS) noise level at the phase center of $\sigma_{\rm cube} \sim 14$ mJy beam$^{-1}$

for a 25 km s$^{-1}$ spectral channel in the \[CII\] datacube, and of $\sigma_{\rm cont} \sim 60$ $\mu$Jy beam$^{-1}$ in the continuum image. The synthesized beam in our final data-products is $1.21''  \times 0.77"$, with a position angle of $-61^{\circ}$.

Additional information on the overall ALPINE data-processing strategy (including data quality assessment) can be found in (cite: Bethermin2020).

# Analysis and Results

![](fig1)

![](fig2)

![](fig3)

## A major merging system at $z\sim 4.57$

Using the available ancillary data and catalogues we first identify the system studied in this paper to be composed of two massive and rest-frame UV bright galaxies (see an HST/ACS F814W cutout in Fig. [1](#fig:fig1)a), at a mutual projected distance of $\sim$ 13 kpc:

\(1\) $\rm VC\_9780$, a Lyman-break galaxy at $z_{\rm UV} = 4.57$ (confirmed $z_{\rm [CII]} = 4.573$, by ALPINE), with a stellar mass of $M_{\star} = 1.1^{+0.4}_{-0.3} \times 10^{10} ~ {\rm M_\odot}$ and a star formation rate of ${\rm SFR} = 38^{+29}_{-14} ~ {\rm M_\odot ~ yr^{-1}}$ (see (cite: Faisst2019));

\(2\) $\rm C15\_705574$ [^1] , at a photometric redshift $z_{\rm phot} = 4.62$ (confirmed $z_{\rm [CII]} = 4.568$, by ALPINE), with $M_{\star} = 1.2^{+1.0}_{-0.2} \times 10^{10} ~ {\rm M_\odot}$ and ${\rm SFR} = 106^{+9}_{-65} ~ {\rm M_\odot ~ yr^{-1}}$ (from the COSMOS2015 catalogue [^2] ; (cite: Laigle2016)). To simplify the reading, we dub $\rm VC\_9780$ and $\rm C15\_705574$ as $\#A$ and $\#B$, respectively.

For both objects, $M_{\star}$ and SFR are measured through the spectral energy distribution (SED) modelling code `LePHARE` ((cite: Arnouts1999; Ilbert2006; Arnouts2011)) ran over the broadband photometry (including ground- and space-based imaging from the rest-frame UV to the near-IR; see (cite: Faisst2019)) available for the well-studied *COSMOS* field ((cite: Scoville2007)).

From the HST/ACS F814W image, modelling the light profiles with a Sérsic function ((cite: Sersic1963)) and assuming a Sérsic index n=1 (i.e., an exponential-disk profile), we estimate rest-frame UV effective radii of $r_{\rm e,UV} = 1.0 \pm 0.24$ kpc and $r_{\rm e,UV} = 1.1 \pm 0.3$ kpc for $\#A$ and $\#B$, respectively (see (cite: Fujimoto2020) for an accurate description of the size-fitting procedure for ALPINE galaxies).

In Fig. [1](#fig:fig1)b we show a HST/WFC3 F160W cutout of the system [^3] (rest-frame $\lambda_{\rm rest}\sim2800 ~\AA$), while in Fig. [1](#fig:fig1)c we display the UltraVista Ks-Band image from the fourth data release ($\rm DR4$ [^4] ; rest-frame $\lambda_{\rm rest}\sim4000 ~\AA$), showing a faint elongation of $\#A$ towards the South-East (S-E; see also Sec. [3.3](#sec:almaAnalysis)).

The close separation both in spatial projected distance ($\sim 13$ kpc in the HST rest-frame UV images) and redshift ($|\Delta z| = 0.004$, corresponding to an absolute velocity offset of only 270 km s$^{-1}$; see Sec. [3.3](#sec:almaAnalysis)) suggests that $\#A$ and $\#B$ are gravitationally bound. Moreover, the ratio of their stellar masses, $r_{\rm mass}  \sim 0.9$, is very close to unity, indicating that the galaxy system is undergoing a close major merger event (e.g., (cite: Stewart2009; Lotz2010; Jones2020)).

## Location at the density peak of a protocluster environment

In order to explore the larger context in which this merging event is occurring, we relied on the wealth of other spectroscopic and photometric data available in the COSMOS field to map out the large-scale galaxy density surrounding our system.

The mapping was done using the Voronoi Monte Carlo (VMC) technique, first presented in (cite: tomczak2017), (cite: lemaux2017; lemaux2019), and (cite: hung2020) for use at $z\sim1$, and adapted for studies at higher redshift ($2 \leq z \leq 5$) in (cite: cucciati2018) and (cite: lemaux2018).

This technique statistically combines both spectroscopic and photometric redshifts to generate a suite of overlapping two-dimensional density maps in fine redshift slices over an arbitrary redshift range, and it has been shown to have high fidelity, precision, and accuracy in reconstructing the galaxy density field at a variety of different redshifts and for a variety of different observational data (see (cite: lemaux2018); Lemaux et al., in prep.). While we refer to the works cited above for more details, we briefly describe the method in the Appendix [6](#sec:appendix1).

Our system is located in close projected spatial and redshift proximity to the massive proto-cluster ${\rm PCl J1001+0220}$ at $z\sim4.57$, discovered by (cite: lemaux2018). Thus, we focus here on generating a map that spans the fiducial redshift boundaries of ${\rm PCl J1001+0220}$ ($4.53 \le z \le 4.60$). Such a redshift range corresponds to 7.5 $h_{70}^{-1}$ proper kpc, or $\sim3750$ km s$^{-1}$.

As in (cite: lemaux2018), we use the full VUDS and zCOSMOS ((cite: lilly2007; lilly2009; diener2013; diener2015); Lilly et al., in prep.) catalogs as our primary spectroscopic catalogs, with photometric redshifts derived from fitting to the photometry presented in the COSMOS2015 catalog ((cite: Laigle2016)). In addition to the VUDS and zCOSMOS catalogs, we incorporate here new Keck$\;$II/Deep Imaging Multi-Object Spectrograph (DEIMOS, (cite: faber2003)) observations of ${\rm PCl J1001+0220}$ (see a description of the observations in Lemaux et al., in prep.) which resulted in the spectroscopic confirmation of 106 new galaxies in the region in and around ${\rm PCl J1001+0220}$.

Shown in Fig. [2](#fig:fig2) is the resultant VMC galaxy overdensity map for the north-east (N-E) region of the ${\rm PCl J1001+0220}$ proto-cluster.

Also shown are the original VUDS spectral members of the system (see (cite: lemaux2018) for more details), as well as our $\#A$ – $\#B$ system.

One of the new members confirmed by the DEIMOS observations ($ID= 705080$) is also shown.

This galaxy, with a $M_{\star} = 5.3^{+2.5}_{-2.1}\times10^9 ~{\rm M_\odot}$ and a ${\rm SFR} = 22.2^{+17.1}_{-8.7} ~ {\rm M_\odot ~ yr^{-1}}$, is located at $\sim35$ $h_{70}^{-1}$ proper kpc from our merging system, although it is not detected by ALMA, neither in \[CII\] nor in the rest-frame FIR continuum. Measuring its Ly$\alpha$ we determine a redshift $z_{Ly\alpha}=4.5769$, corresponding to a velocity offset of $\Delta v \sim 260 ~ {\rm km~s^{-1}}$ with respect to $\#A$ and $\Delta v \sim 580 ~ {\rm km~s^{-1}}$ with respect to $\#B$ [^5].

Such a close projected spatial and redshift proximity to $\#A$ – $\#B$ suggests that DEIMOS $ID= 705080$ is possibly associated to them.

As can be seen in Fig. [2](#fig:fig2), our merging system at $z\sim4.57$ is nearly coincident with the overdensity peak of the N-E sub-component of the proto-cluster ${\rm PCl J1001+0220}$, and lie within $\leq$ 385 pkpc from the barycenter of this sub-component. The average overdensity across this region is $\log(1+\langle \delta_{gal}\rangle)=1.5$, comparable to the cores of $z\sim1$ groups or the outskirts of massive clusters (e.g., (cite: lemaux2017; tomczak2017)).

Altogether these findings indicate that the merging system presented in this paper belongs to a large-scale dense and complex proto-cluster environment. In Sec. [4](#sec:discussion) we discuss possible implications of this scenario in the interpretation of our results.

In the next section we describe the results of ALMA observations of our system.

![](fig4)

## ALMA morpho-kinematics analysis

|  |  |  |  |  |  |
|:---|:---|:---|:---|:---|:---|
|   |   |   |   |   |   |
|   | $M_{\star}$ \[${\rm M_\odot}$\] | ${\rm SFR}$ \[${\rm M_\odot ~ yr^{-1}}$\] | $L_{\rm [CII]}$ \[${\rm L_\odot}$\] | ${\rm FWHM}_{\rm [CII]}$ \[km s$^{-1}$\] | $z_{\rm [CII]}$ |
|   |   |   |   |   |   |
| $\rm VC\_9780$ ($\#A$) | $1.1^{+0.4}_{-0.3} \times 10^{10}$ | $38^{+29}_{-14}$ | $3.5 ~(\pm 0.3) \times 10^8$ | $190$ | 4.573 |
| $\rm C15\_705574$ ($\#B$) | $1.2^{+1.0}_{-0.2} \times 10^{10}$ | $106^{+9}_{-65}$ | $6.6 ~(\pm 0.4) \times 10^8$ | $260$ | 4.568 |
| $\#C$ | – | – | $7.7 ~\pm 1.5 \times 10^7$ | 40 | 4.562 |
| $\#D$ | – | – | $8.4 ~\pm 1.9 \times 10^7$ | 57 | 4.573 |
|   |   |   |   |   |   |

We use our ALPINE ALMA observations (see Sec. [2](#sec:Observations)) of the \[CII\] line emission to perform a three-dimensional (3D) morpho-spectral decomposition of our merging system.

We start by extracting two spectra from large

1$''$ (diameter)-apertures centered on the rest-frame UV centroids of $\#A$ and $\#B$.

We then produce velocity-integrated maps of the \[CII\] emission in/around $\#A$ and $\#B$ (see Fig. [3](#fig:fig3)) by collapsing the cube-channels included in the spectral range \[$f_{\rm cen} - \sigma_{\rm G}$, $f_{\rm cen} + \sigma_{\rm G}$\], where $f_{\rm cen}$ and $\sigma_{\rm G}$ are the central frequency and the standard deviation from a Gaussian model of the spectra.

The corresponding velocity ranges are labelled in the top-left corners of both panels of Fig. [3](#fig:fig3), defined adopting a zero-velocity reference at $z_{\rm ref} = 4.570$ (see next paragraphs of this Section).

Although this will be discussed in detail further on by means of tailored analyses, we note that maps in Fig. [3](#fig:fig3) already suggest a disturbed morphology of the system, showing the presence of complex resolved extended emission around the sources.

We then estimate the spatial extent of the \[CII\]-emission arising from $\#A$ and $\#B$ by fitting a simple 2D Gaussian model to the velocity-integrated maps (Fig. [3](#fig:fig3)), and use the ${\rm FWHM}_x \times {\rm FWHM}_y$ ellipses as apertures to extract the correct spectral information

[^6].

This three-step process is needed to allow for any peculiar geometry or spatial offset between the \[CII\] and the rest-frame UV emission. Indeed, we note that the \[CII\] peak of $\#A$ is offset by $\gtrsim 0.5''$ from its HST centroid (see similar cases in e.g., (cite: Maiolino2015; Carniani2018)), with a clear elongation toward the S-E (see Fig. [3](#fig:fig3)a). This \[CII\] tail is HST-dark, although a faint spike is possibly detected in the HST/WFC3 F160W image (see Fig. [1](#fig:fig1)b).

It is also broadly coincident with the rest-frame optical counterpart (see UltraVista DR4 Ks-band image in Fig. [1](#fig:fig1)c), indicating a UV slope steeply rising towards longer wavelengths and therefore a significant presence of obscuring dust (see e.g., (cite: Calzetti2000)), as also suggested by the $\gtrsim 4 \sigma$ ALMA detection of co-spatial FIR-continuum emission (see Fig. [3](#fig:fig3)a).

With the currently available ALMA resolution, it is unclear whether this \[CII\] tail is produced by a dust-obscured star-forming region within $\#A$, or it is associated to a dusty neighbour at the same redshift.

\

![](fig5)

The final \[CII\] spectra of $\#A$ and $\#B$ are shown in Fig. [4](#fig:fig4)a (upper and lower panel, respectively), where we choose an intermediate redshift $z_{\rm ref} = 4.570$ as a common zero-velocity reference for the system [^7].

Galaxy $\#A$, at $z_{\rm [CII]}^{\#A} = 4.573$, has a \[CII\]-luminosity of $L_{\rm [CII]}^{\#A} = 3.5 ~(\pm 0.3) \times 10^8 ~ {\rm L_\odot}$, and a ${\rm FWHM}_{\#A} = 190$ km s$^{-1}$, while $\#B$, at $z_{\rm [CII]}^{\#B} = 4.568$ (blueshifted by $\rm \Delta v_{BA} = -270$ km s$^{-1}$ with respect to $\#A$) is broader (${\rm FWHM}_{\#B} = 260$ km s$^{-1}$) and $\sim 2 \times$ more luminous, $L_{\rm [CII]}^{\#B} = 6.6 ~(\pm 0.4) \times 10^8 ~ {\rm L_\odot}$.

Interestingly, the second spectrum (see lower panel of Fig. [4](#fig:fig4)a) shows two additional \[CII\] emitters, dubbed $\#C$ and $\#D$, spectrally offset by a few hundreds of km s$^{-1}$, and spatially close to $\#B$ (less than a $\sim 1''$-beam in projection; see velocity integrated map in the Appendix [7](#sec:appendix2)).

The line properties of $\#B$, $\#C$ and $\#D$ (total flux, centroid and FWHM) are estimated from a 3-Gaussian modelling of the spectrum.

Although their integrated flux is detected at $> 4 \sigma$ (see also Appendix [7](#sec:appendix2)), $\#C$ and $\#D$ are very faint ($L_{\rm [CII]}^{\#C} = 7.7 ~\pm 1.5 \times 10^7 ~ {\rm L_\odot}$, $L_{\rm [CII]}^{\#D} = 8.4 ~\pm 1.9 \times 10^7 ~ {\rm L_\odot}$), and narrow (${\rm FWHM}_{\#C} = 40$ km s$^{-1}$, ${\rm FWHM}_{\#D} = 57$ km s$^{-1}$), and are most likely small satellite galaxies (or gas clumps) orbiting around or accreting onto $\#B$.

\

To visualize the total \[CII\] emission arising from the full system we produce a velocity-integrated flux map by collapsing the spectral channels in the velocity range $[-500 : +500]$ km s$^{-1}$, using a consistent $z_{\rm ref}$ as discussed above. Such a broad velocity domain is needed to safely include the four detected \[CII\]-emitting galaxies (see spectra in Fig. [4](#fig:fig4)a). The resulting velocity-integrated \[CII\] map is shown in Fig. [4](#fig:fig4)b.

We find a very large \[CII\]-emitting structure extending on circumgalactic scales, with a projected diameter of $\sim 30$ kpc. Such a metal-enriched gaseous structure encloses the single galaxy components, and shows a large amount of \[CII\] arising from regions significantly displaced ($\gtrsim 10$ kpc) from the rest-frame UV / optical counterparts, especially along the direction orthogonal to the $\#A$ - $\#B$ axis.

However, because of its 2D nature, the \[CII\] flux map shown in Fig. [4](#fig:fig4)b suffers from the dilution of signal emitted by sources with a width much narrower than the velocity-filter adopted for the spectral integration.

Therefore, to better visualize the 3D distribution of the gaseous structure we produce two position-velocity (PV) diagrams, one extracted along the $\#A$ - $\#B$ axis (Fig. [5](#fig:fig5)a), and the other along the orthogonal direction, centred on $\#B$ (Fig. [5](#fig:fig5)b). Both diagrams highlight the complex morpho-kinematic structure of the system, clearly showing the presence of circumgalactic tails around the interacting galaxies (see e.g., the \[CII\]-emitting regions labelled as $'$CGM$'$ in both panels of Fig. [5](#fig:fig5)).

One important piece of information is the net contribution of the four interacting galaxies themselves to the overall \[CII\] emission arising from the extended gaseous structure. To distinguish between the relative $'$galaxy$'$ and $'$CGM$'$ \[CII\] budgets, we extract a spectrum of the total \[CII\]-emitting system from a region within the 1-$\sigma$ contour of the velocity-integrated map (see grey solid line in Fig. [4](#fig:fig4)b), and compare it with the sum of the single $\#A$, $\#B$, $\#C$ and $\#D$ spectra (see Fig. [6](#fig:fig6)a).

We note that, due to the dynamical complexity of our object, such a procedure is more accurate than extracting relative budgets directly from the velocity-integrated map, because of the limitations of the latter, as discussed above.

We find that the full \[CII\]-emitting structure has a total luminosity of $L_{\rm [CII]}^{tot} = 2.3~(\pm 0.2) \times 10^9 ~ {\rm L_\odot}$, i.e., $\sim2$ times larger than the sum of the \[CII\]-emitting galaxies. This implies that about $50 ~(\pm6) ~\%$ (see Fig. [6](#fig:fig6)b) of the total \[CII\] luminosity resides *between* the individual components, $L_{\rm [CII]}^{CGM} = 1.1 ~(\pm 0.2) \times 10^9 ~ {\rm L_\odot}$, in a sort of circumgalactic and metal-rich gaseous *envelope* around the merging galaxies.

This fraction of \[CII\] emission arising from the CGM is larger than what typically found around the few individual normal isolated galaxies (i.e., with not evident signs of major/minor mergers) that show a \[CII\]-halo (see (cite: Fujimoto2020)), suggesting a link with the merging-nature of our system.

In the next section we discuss possible mechanisms responsible for such large amount of circumgalactic \[CII\] emission.

![](fig6)

# Discussion: gas mixing in the CGM

## Dynamical interactions and shocks

A natural scenario to explain the origin of the luminous gaseous envelope is that the circumgalactic \[CII\] traces gas stripped during gravitational encounters occurring in the dense merging system. Strong dynamical interactions between the four galaxies might therefore remove a significant amount of interstellar gas from their outer regions, polluting the CGM with chemically enriched material, and producing the complex morphology (see Fig. [3](#fig:fig3) and Fig. [4](#fig:fig4)a) and kinematics (see Fig. [5](#fig:fig5)) observed.

In this scenario, our observations could be a high-$z$ analogue of local studies of circumgalactic stripped \[CII\] in local groups.

For instance (cite: Appleton2013) detect a broad \[CII\] emission arising from an extended shocked filament ($\sim 35$ kpc) produced by supersonic collisions between galaxies in the compact local group Stephan’s Quintet. They observe very large \[CII\]/Polycyclic Aromatic Hydrocarbon (PAH) and \[CII\]/FIR ratios, which cannot be accounted for by \[CII\] emission originating from photo-dissociation regions (PDRs; (cite: Stacey1991; Stacey2010)) only, and suggest that circumgalactic \[CII\] can be excited by the dissipation of mechanical energy (turbulence and shocks) injected by strong dynamical interactions.

Such a mechanism is expected to be more frequent and more disruptive at high-$z$ because of (i) higher merger rates (e.g., (cite: Conselice2006; Wetzel2009; Lotz2011)) and (ii) generally higher gas fractions (e.g., (cite: Santini2014; Dessauges2017; Schinnerer2016; Scoville2017; Tacconi2018)),

and might also explain previous similar observations of extended \[CII\] emission around multi-component systems at $z\sim5$ (see ${\rm HZ6}$ and ${\rm HZ8}$ in (cite: Capak2015; Faisst2017)).

We will further explore this hypothesis by extending similar morpho-spectral decomposition analyses presented in this paper to other major/minor merging systems in the ALPINE survey (see a discussion on ALPINE mergers in (cite: LeFevre2020) and (cite: Jones2020)) in future works.

Interestingly, since as discussed in Sec. [3.2](#sec:protocluster) our merging system is close to an overdensity peak of the proto-cluster ${\rm PCl J1001+0220}$ at $z\sim4.57$ (see (cite: lemaux2018)), the merger-induced CGM pollution might be a natural channel to feed and enrich the nascent proto- intra-cluster-medium (ICM; see e.g., (cite: Cucciati2014), (cite: Tozzi2003), and a recent review by (cite: Overzier2016)). Thus, our results could be some of the first observational evidence at high redshift that mergers and gas stripping are key mechanisms in driving the build-up and the chemical evolution of the ICM, as predicted by models and numerical simulations (see e.g., (cite: Gnedin1998; Toniazzo2001; Tornatore2004; DeLucia2004; Kapferer2007)).

Also, the peculiar location of our system within a large-scale overdense structure suggests that it sits in proximity of a cosmic web node where several filaments from the IGM might be feeding into it. Shocks are predicted to occur as the intergalactic gas accretes onto massive galaxies and mixes with their CGM (see e.g., (cite: Birnboim2003; Keres2009)), and they likely contribute to the \[CII\] excitation. To quantitatively assess this scenario we will need new deep observations of the large-scale environment tracing the hydrogen gas, representing the bulk of the intergalactic streams, that can be traced e.g., through Ly$\alpha$ with MUSE (which has a field of view of $\sim 400$ kpc at this redshift).\

## Galactic outflows

Another possible contributing scenario is that a fraction of the circumgalactic metal-enriched gas traced by the extended \[CII\] envelope is expelled from the internal ISM of galaxies through galactic outflows. Evidence of star formation-driven winds has been recently observed at $z>4$ (see (cite: Sugahara2019; Faisst2019; Ginolfi2020; Cassata2020)), and repeated episodes of outflows are thought to be responsible for the origin of diffuse \[CII\]-*halos* ($\sim 20$ kpc) detected around isolated massive star-forming high-$z$ galaxies (see (cite: Faisst2017; Fujimoto2019; Ginolfi2020; Pizzati2020; Fujimoto2020)).

However, a rough estimate suggests that outflows might not be the dominant mechanism for injecting the large amount of circumgalactic cold gas observed in our system (see Fig. [4](#fig:fig4)b and Fig. [6](#fig:fig6)).

Using the $L_{\rm [CII]}-M_{\rm gas}$ relation calibrated by (cite: Zanella2018) and the \[CII\] luminosity arising from the CGM (i.e., about $50\%$ of the total $L_{\rm [CII]}$ (see last paragraph of Sec. [3.3](#sec:almaAnalysis)) we obtain a rough estimate of the dense mass of in the \[CII\] gaseous envelope, $M_{\rm gas}^{\rm CGM} \sim  3\times 10^{10} ~{\rm M_\odot}$.

Then, using typical mass outflow rates of $\dot{M}_{\rm out} \sim 30 ~ {\rm M_\odot ~ yr^{-1}}$ (as measured by (cite: Ginolfi2020) in the sub-sample of highly star-forming ALPINE galaxies), and assuming that both $\#A$ and $\#B$ significantly contribute to gas-expulsion [^8] , we find that outflows would require at least $\sim$ 0.6 Gyr to expel the estimated amount of dense gas in the CGM. We note that this estimate is very conservative, since it is derived under the unlikely assumptions that (i) re-accretion does not occur, and (ii) both $\#A$ and $\#B$ have constantly had during their past growth a sufficient SFR to produce powerful outflows.\

## Small faint satellites

A third complementary process would be that part of the extended \[CII\] emission is induced by the star formation of several small satellites, which are unresolved by our ALMA observations and faint in the rest-frame UV HST images (the few light spots around $\#A$ and $\#B$ in the HST maps, see Fig. [1](#fig:fig1)a and Fig. [1](#fig:fig1)b, may belong to this category).

To estimate the efficiency of this mechanism we estimate the possible diffuse SFR produced by faint satellites by integrating the rest-frame UV light within an aperture defined as the 1$\sigma$ level of the \[CII\] full structure (see grey line in Fig. [1](#fig:fig1)a and Fig. [4](#fig:fig4)b), and then subtracting the UV flux arising from regions defined as the blue ellipses (see Sec. [3.3](#sec:almaAnalysis) and Fig. [4](#fig:fig4)b) associated with the individual galaxy components $\#A$, $\#B$, $\#C$ and $\#D$.

Using a standard (cite: Kennicutt2012) calibration, we estimate a total diffuse UV-based ${\rm SFR}_{\tiny{CGM}}^{\tiny{UV}}= 13 \pm 5 ~{\rm M_\odot ~ yr^{-1}}$,

which is about one order of magnitude lower than expected assuming a $L_{\rm [CII]} - {\rm SFR}$ relation [^9] (see e.g., (cite: DeLooze2014; Lagache2018; Schaerer2020); see a similar calculation in (cite: Fujimoto2019)), ${\rm SFR}_{\tiny{CGM}}^{\tiny{[CII]}} \sim 125~ {\rm M_\odot ~ yr^{-1}}$.

This suggests that, unless the diffuse SFR was exceptionally dust-obscured, which is disfavoured by the non-detection of ALMA FIR-continuum (see also (cite: Fudamoto2020), showing that low-mass objects are not expected to have high $L_{\rm IR} / L_{\rm UV}$), small faint satellites do not significantly account for the detected large circumgalactic \[CII\] emission.\
\

Altogether, gas stripping by dynamical interactions and (with a possibly relative lower efficiency) galactic outflows and small faint satellites jointly contribute to the gas mixing and the metal enrichment of the CGM around high-$z$ merging systems.

To resolve these mechanisms and quantitatively assess their relative efficiencies, we urge (i) deeper/ higher-resolution ALMA FIR-lines mapping and (ii) future rest-frame optical emission line observations with JWST, to be interpreted with tailored zoom-in cosmological simulations (e.g., (cite: Kohandel2019; Pallottini2019; Graziani2020)).

# Conclusions

In this work we present ALMA observations of \[CII\] and FIR-continuum emission in/around a merging system at $z\sim4.57$, observed as a part of the ALPINE survey (see (cite: LeFevre2020; Faisst2019; Bethermin2020)). Combining information from a rich set of panchromatic ancillary data (including imaging and spectroscopy from rest-frame UV to the near-IR; (cite: Faisst2019)) with a morpho-spectral decomposition of the ALMA data (see Sec. [3.3](#sec:almaAnalysis)), we find the results summarised below.

- $\rm VC\_9780$ (dubbed $\#A$) and $\rm C15\_705574$ (dubbed $\#B$), with star formation rates ${\rm SFR}_{\#A} = 38^{+29}_{-14} ~ {\rm M_\odot ~ yr^{-1}}$ and ${\rm SFR}_{\#B} = 106^{+9}_{-65} ~ {\rm M_\odot ~ yr^{-1}}$ respectively, and similar stellar masses of $M_{\star} \sim 10^{10} ~ {\rm M_\odot}$, are undergoing a major merger (stellar mass ratio $r_{\rm mass} \sim 0.9$; see Sec. [3.1](#sec:ancillary)), at a close projected separation of $\sim 13$ kpc (see Fig. [1](#fig:fig1)), with a small velocity offset of $\Delta v \sim 270 ~ {\rm km~s^{-1}}$. ALMA data reveal the presence of two faint and narrow (${\rm FWHM} \sim 50 ~ {\rm km~s^{-1}}$) \[CII\]-emitting satellites (see Fig. [4](#fig:fig4)) close to $\#B$, and most likely in the process of orbiting around (or accreting into) it. We find that our merging system belongs to the proto-cluster ${\rm PCl J1001+0220}$ ((cite: lemaux2018); see Sec. [3.2](#sec:protocluster)), and it is coincident to one of its overdensity peaks (see Fig. [2](#fig:fig2)).\

- We produce a velocity-integrated map collapsing the broad velocity range $\rm [-500 : +500] ~ {\rm km~s^{-1}}$ to visualize the total \[CII\] emission arising from the full system, and find a very large structure extending over circumgalactic scales, out to a diameter-scale of $\sim$ 30 kpc (see Fig. [4](#fig:fig4)), surrounding the galaxy components. A fraction of \[CII\] flux appears significantly displaced ($\gtrsim 10$ kpc) from the rest-frame UV counterparts of $\#A$ and $\#B$. Both flux maps (see Fig. [3](#fig:fig3), Fig. [4](#fig:fig4)) and PV diagrams (see Fig. [5](#fig:fig5)) indicate a disturbed morphology and complex kinematics of the overall gas structure.\

- We compare the flux arising from the extended \[CII\]-emitting region with the sum of \[CII\] fluxes emitted by single galaxies, and find that about $50 ~\%$ of the total emission arises from a gaseous envelope distributed between the individual components of the system (see Fig. [6](#fig:fig6); see also discussion about possibly similar objects in (cite: Faisst2017)).

  While a contribution of processed material expelled by galactic outflows (see e.g., (cite: Ginolfi2020; Fujimoto2020)) and SFR-induced \[CII\] emitted by small faint satellites should be not negligible, we argue that most of the detected circumgalactic emission originates from the effect of gas stripping induced by strong gravitational interactions (see a discussion in Sec. [4](#sec:discussion)), in analogy with observations of tidal tails of shock-excited \[CII\] in local compact groups (e.g., (cite: Appleton2013)). This might also represent a natural channel to feed and enrich the ICM in the large-scale proto-cluster environment surrounding our system (see Sec. [3.2](#sec:protocluster) and Fig. [2](#fig:fig2)).\

Altogether our findings suggest that dynamical interactions at high-$z$ can be an efficient mechanism for extracting gas out of galaxies and mixing the CGM with chemically evolved material. Deeper and higher resolution ALMA data, as well as future JWST rest-frame optical emission line observations, will be necessary to study more in details the key role of mergers in the baryon cycle of distant galaxies.

# Acknowledgements

The authors would like to thank the anonymous referee for her/his useful suggestions. This paper is based on data obtained with the ALMA Observatory, under Large Program 2017.1.00428.L. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. G.C.J.and R.M. acknowledge the ERC Advanced Grant 695671 "QUENCH” and support by the Science and Technology Facilities Council (STFC). C.G. and M.T. acknowledge the support from a grant PRIN MIUR 2017. S.C. acknowledges support from the ERC Advanced Grant INTERSTELLAR H2020/740120. The Cosmic Dawn Center is funded by the Danish National Research Foundation under grant No. 140. Some of the material presented in this paper is based upon work supported by the National Science Foundation under Grant No. 1908422.

This program receives financial support from the French CNRS-INSU Programme National Cosmologie et Galaxies.

This paper is dedicated to the memory of Olivier Le Fèvre, PI of the ALPINE survey.

# Description of the VMC mapping technique

Here we briefly describe the VMC mapping technique used to produce Fig. [2](#fig:fig2), discussed in Sec. [3.2](#sec:protocluster). We refer to (cite: lemaux2018) (and reference therein) for more details.

To reconstruct the density field in a given redshift range, a large number of Monte Carlo iterations of the input spectroscopic and photometric catalogs are run. For each Monte Carlo realization, we begin with all objects that have spectroscopic information, sampling a random uniform distribution for each object. For a given object, if the sample exceeds the value of a predetermined reliability flag for that redshift, we throw away the spectral redshift and, for that Monte Carlo realization, rely on the photometric redshift information. If the uniform sampling does not exceed the reliability threshold, we retain the spectral information for that object in that realization. For those objects where the spectral information was disavowed along with those objects that had no spectral information then have their photometric redshifts tweaked by sampling a reconstruction of their full $P(z)$. Thus, at the end of a given iteration, all objects in the combined spectral and photometric catalog have a set redshift. We then set a redshift boundary to generate the two-dimensional map and Voronoi tessellate over all objects whose redshifts, spectral or photometric, fall within the redshift boundaries. The local density value, $\Sigma_{VMC}$, of a given object for a given iteration is the inverse of the area of the Voronoi cell surrounding it. This process is repeated for the set number of Monte Carlo realizations, with the density values of each realization sampled by a standardized grid of 75$\times$75 $h_{70}^{-1}$ proper kpc, and the pixel values from all realizations are then median combined. As in other works, we rely here on local overdensity rather than local density as the former has been found to be less sensitive to observational effects. The local overdensity value for each grid point is then computed as $\log(1+\delta_{gal}) \equiv \log(1+ (\Sigma_{VMC}-\tilde{\Sigma}_{VMC})/\tilde{\Sigma}_{VMC})$, where $\tilde{\Sigma}_{VMC}$ is the median $\Sigma_{VMC}$ for all grid points over which the map was defined, i.e., excluding an $\sim1$ arcmin wide border region to mitigate edge effects.

# \[CII\] flux maps of $\#C$ and $\#D$

![](figAppendix)

125 natexlab

(ref: Angles2017) Anglés-Alcázar, D., Faucher-Giguère, C.-A., Kereš, D., et al. 2017, MNRAS, 470, 4698

(ref: Appleton2013) Appleton, P. N., Guillard, P., Boulanger, F., et al. 2013, ApJ, 777, 66

(ref: Arnouts1999) Arnouts, S., Cristiani, S., Moscardini, L., et al. 1999, MNRAS, 310, 540

(ref: Arnouts2011) Arnouts, S. & Ilbert, O. 2011, LePHARE: Photometric Analysis for Redshift Estimate

(ref: Barnes1991) Barnes, J. E. & Hernquist, L. E. 1991, ApJL, 370, L65

(ref: Bethermin2020) Bethermin, M., Fudamoto, Y., Ginolfi, M., et al. 2020, arXiv e-prints, arXiv:2002.00962

(ref: Birnboim2003) Birnboim, Y. & Dekel, A. 2003, MNRAS, 345, 349

(ref: Boselli2006) Boselli, A., Boissier, S., Cortese, L., et al. 2006, ApJ, 651, 811

(ref: Bournaud2011) Bournaud, F., Chapon, D., Teyssier, R., et al. 2011, ApJ, 730, 4

(ref: Bower2006) Bower, R. G., Benson, A. J., Malbon, R., et al. 2006, MNRAS, 370, 645

(ref: Bradac2017) Bradač, M., Garcia-Appadoo, D., Huang, K.-H., et al. 2017, ApJL, 836, L2

(ref: Bridge2010) Bridge, C. R., Carlberg, R. G., & Sullivan, M. 2010, ApJ, 709, 1067

(ref: Calzetti2000) Calzetti, D., Armus, L., Bohlin, R. C., et al. 2000, ApJ, 533, 682

(ref: Capak2015) Capak, P. L., Carilli, C., Jones, G., et al. 2015, Nature, 522, 455

(ref: Carilli2013) Carilli, C. L. & Walter, F. 2013, ARA&A, 51, 105

(ref: Carniani2020) Carniani, S., Ferrara, A., Maiolino, R., et al. 2020, arXiv e-prints, arXiv:2006.09402

(ref: Carniani2018b) Carniani, S., Maiolino, R., Amorin, R., et al. 2018a, MNRAS, 478, 1170

(ref: Carniani2018) Carniani, S., Maiolino, R., Smit, R., & Amorı́n, R. 2018b, ApJL, 854, L7

(ref: Cassata2020) Cassata, P., Morselli, L., Faisst, A., et al. 2020, arXiv e-prints, arXiv:2002.00967

(ref: Chabrier2003) Chabrier, G. 2003, PASP, 115, 763

(ref: Conselice2006) Conselice, C. J. 2006, ApJ, 638, 686

(ref: Cormier2012) Cormier, D., Lebouteiller, V., Madden, S. C., et al. 2012, A&A, 548, A20

(ref: cucciati2018) Cucciati, O., Lemaux, B. C., Zamorani, G., et al. 2018, A&A, 619, A49

(ref: Cucciati2014) Cucciati, O., Zamorani, G., Lemaux, B. C., et al. 2014, A&A, 570, A16

(ref: Daddi2010) Daddi, E., Elbaz, D., Walter, F., et al. 2010, ApJL, 714, L118

(ref: DeLooze2014) De Looze, I., Cormier, D., Lebouteiller, V., et al. 2014, A&A, 568, A62

(ref: DeLucia2004) De Lucia, G., Kauffmann, G., & White, S. D. M. 2004, MNRAS, 349, 1101

(ref: Decarli2019) Decarli, R., Dotti, M., Bañados, E., et al. 2019, ApJ, 880, 157

(ref: Dekel2009) Dekel, A., Birnboim, Y., Engel, G., et al. 2009, Nature, 457, 451

(ref: Dessauges2017) Dessauges-Zavadsky, M., Zamojski, M., Rujopakarn, W., et al. 2017, A&A, 605, A81

(ref: DiMatteo2008) Di Matteo, P., Bournaud, F., Martig, M., et al. 2008, A&A, 492, 31

(ref: DiMatteo2005) Di Matteo, T., Springel, V., & Hernquist, L. 2005, Nature, 433, 604

(ref: diener2013) Diener, C., Lilly, S. J., Knobel, C., et al. 2013, ApJ, 765, 109

(ref: diener2015) Diener, C., Lilly, S. J., Ledoux, C., et al. 2015, ApJ, 802, 31

(ref: Elmegreen2000) Elmegreen, B. G. 2000, ApJ, 530, 277

(ref: faber2003) Faber, S. M., Phillips, A. C., Kibrick, R. I., et al. 2003, Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 4841, The DEIMOS spectrograph for the Keck II Telescope: integration and testing, ed. M. Iye & A. F. M. Moorwood, 1657–1669

(ref: Faisst2017) Faisst, A. L., Capak, P. L., Yan, L., et al. 2017, ApJ, 847, 21

(ref: Faisst2019) Faisst, A. L., Schaerer, D., Lemaux, B. C., et al. 2020, ApJS, 247, 61

(ref: Ferrara2019) Ferrara, A., Vallini, L., Pallottini, A., et al. 2019, MNRAS, 489, 1

(ref: Fossati2019) Fossati, M., Fumagalli, M., Gavazzi, G., et al. 2019, MNRAS, 484, 2212

(ref: Fudamoto2020) Fudamoto, Y., Oesch, P. A., Faisst, A., et al. 2020, arXiv e-prints, arXiv:2004.10760

(ref: Fujimoto2019) Fujimoto, S., Ouchi, M., Ferrara, A., et al. 2019, ApJ, 887, 107

(ref: Fujimoto2020) Fujimoto, S., Silverman, J. D., Bethermin, M., et al. 2020, arXiv e-prints, arXiv:2003.00013

(ref: GarciaBurillo2005) Garcı́a-Burillo, S., Combes, F., Schinnerer, E., Boone, F., & Hunt, L. K. 2005, A&A, 441, 1011

(ref: Ginolfi2020) Ginolfi, M., Jones, G. C., Béthermin, M., et al. 2020, A&A, 633, A90

(ref: Ginolfi2019) Ginolfi, M., Schneider, R., Valiante, R., et al. 2019, MNRAS, 483, 1256

(ref: Gnedin1998) Gnedin, N. Y. 1998, MNRAS, 294, 407

(ref: Graziani2020) Graziani, L., Schneider, R., Ginolfi, M., et al. 2020, MNRAS, 494, 1071

(ref: Gunn1972) Gunn, J. E. & Gott, J. Richard, I. 1972, ApJ, 176, 1

(ref: Guo2016) Guo, R., Hao, C.-N., Xia, X. Y., Mao, S., & Shi, Y. 2016, ApJ, 826, 30

(ref: Hani2018) Hani, M. H., Sparre, M., Ellison, S. L., Torrey, P., & Vogelsberger, M. 2018, MNRAS, 475, 1160

(ref: Hopkins2010) Hopkins, P. F., Bundy, K., Croton, D., et al. 2010, ApJ, 715, 202

(ref: Hopkins2006) Hopkins, P. F., Hernquist, L., Cox, T. J., et al. 2006, ApJS, 163, 1

(ref: hung2020) Hung, D., Lemaux, B. C., Gal, R. R., et al. 2020, MNRAS, 491, 5524

(ref: Ilbert2006) Ilbert, O., Arnouts, S., McCracken, H. J., et al. 2006, A&A, 457, 841

(ref: Inoue2016) Inoue, K. T., Minezaki, T., Matsushita, S., & Chiba, M. 2016, MNRAS, 457, 2936

(ref: Jones2020) Jones, G. C., Béthermin, M., Fudamoto, Y., et al. 2020, MNRAS, 491, L18

(ref: Jones2017) Jones, G. C., Carilli, C. L., Shao, Y., et al. 2017, ApJ, 850, 180

(ref: Kapferer2007) Kapferer, W., Kronberger, T., Weratschnig, J., et al. 2007, A&A, 466, 813

(ref: Kennicutt2012) Kennicutt, R. C. & Evans, N. J. 2012, ARA&A, 50, 531

(ref: Keres2009) Kereš, D., Katz, N., Fardal, M., Davé, R., & Weinberg, D. H. 2009, MNRAS, 395, 160

(ref: Koekemoer2007) Koekemoer, A. M., Aussel, H., Calzetti, D., et al. 2007, ApJS, 172, 196

(ref: Kohandel2019) Kohandel, M., Pallottini, A., Ferrara, A., et al. 2019, MNRAS, 487, 3007

(ref: Lagache2018) Lagache, G., Cousin, M., & Chatzikos, M. 2018, A&A, 609, A130

(ref: Laigle2016) Laigle, C., McCracken, H. J., Ilbert, O., et al. 2016, ApJS, 224, 24

(ref: LeFevre2020) Le Fèvre, O., Béthermin, M., Faisst, A., et al. 2019, arXiv e-prints, arXiv:1910.09517

(ref: LeFevre2015) Le Fèvre, O., Tasca, L. A. M., Cassata, P., et al. 2015, A&A, 576, A79

(ref: lemaux2018) Lemaux, B. C., Le Fèvre, O., Cucciati, O., et al. 2018, A&A, 615, A77

(ref: lemaux2019) Lemaux, B. C., Tomczak, A. R., Lubin, L. M., et al. 2019, MNRAS, 490, 1231

(ref: lemaux2017) Lemaux, B. C., Tomczak, A. R., Lubin, L. M., et al. 2017, MNRAS, 472, 419

(ref: Lilly2013) Lilly, S. J., Carollo, C. M., Pipino, A., Renzini, A., & Peng, Y. 2013, ApJ, 772, 119

(ref: lilly2009) Lilly, S. J., Le Brun, V., Maier, C., et al. 2009, ApJS, 184, 218

(ref: lilly2007) Lilly, S. J., Le Fèvre, O., Renzini, A., et al. 2007, ApJS, 172, 70

(ref: Lotz2011) Lotz, J. M., Jonsson, P., Cox, T. J., et al. 2011, ApJ, 742, 103

(ref: Lotz2010) Lotz, J. M., Jonsson, P., Cox, T. J., & Primack, J. R. 2010, MNRAS, 404, 575

(ref: Maiolino2015) Maiolino, R., Carniani, S., Fontana, A., et al. 2015, MNRAS, 452, 54

(ref: Marrone2018) Marrone, D. P., Spilker, J. S., Hayward, C. C., et al. 2018, Nature, 553, 51

(ref: Matthee2019) Matthee, J., Sobral, D., Boogaard, L. A., et al. 2019, ApJ, 881, 124

(ref: Matthee2017) Matthee, J., Sobral, D., Boone, F., et al. 2017, ApJ, 851, 145

(ref: McCracken2012) McCracken, H. J., Milvang-Jensen, B., Dunlop, J., et al. 2012, A&A, 544, A156

(ref: McMullin2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, Astronomical Society of the Pacific Conference Series, Vol. 376, CASA Architecture and Applications, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Moretti2018) Moretti, A., Paladino, R., Poggianti, B. M., et al. 2018, MNRAS, 480, 2508

(ref: Nelson2015) Nelson, D., Genel, S., Vogelsberger, M., et al. 2015, MNRAS, 448, 59

(ref: Oteo2016) Oteo, I., Ivison, R. J., Dunne, L., et al. 2016, ApJ, 827, 34

(ref: Overzier2016) Overzier, R. A. 2016, A&ARv, 24, 14

(ref: Pallottini2019) Pallottini, A., Ferrara, A., Decataldo, D., et al. 2019, MNRAS, 487, 1689

(ref: Pavesi2018) Pavesi, R., Riechers, D. A., Sharon, C. E., et al. 2018, ApJ, 861, 43

(ref: Pentericci2016) Pentericci, L., Carniani, S., Castellano, M., et al. 2016, ApJL, 829, L11

(ref: Pizzati2020) Pizzati, E., Ferrara, A., Pallottini, A., et al. 2020, arXiv e-prints, arXiv:2001.10547

(ref: Poggianti2017) Poggianti, B. M., Gullieuszik, M., Moretti, A., et al. 2017, The Messenger, 170, 29

(ref: Poggianti2019) Poggianti, B. M., Ignesti, A., Gitti, M., et al. 2019, ApJ, 887, 155

(ref: Riechers2017) Riechers, D. A., Leung, T. K. D., Ivison, R. J., et al. 2017, ApJ, 850, 1

(ref: Rodighiero2011) Rodighiero, G., Daddi, E., Baronchelli, I., et al. 2011, ApJL, 739, L40

(ref: Sanders1996) Sanders, D. B. & Mirabel, I. F. 1996, ARA&A, 34, 749

(ref: Santini2014) Santini, P., Maiolino, R., Magnelli, B., et al. 2014, A&A, 562, A30

(ref: Schaerer2020) Schaerer, D., Ginolfi, M., Bethermin, M., et al. 2020, arXiv e-prints, arXiv:2002.00979

(ref: Schaye2015) Schaye, J., Crain, R. A., Bower, R. G., et al. 2015, MNRAS, 446, 521

(ref: Schinnerer2016) Schinnerer, E., Groves, B., Sargent, M. T., et al. 2016, ApJ, 833, 112

(ref: Scoville2007) Scoville, N., Aussel, H., Brusa, M., et al. 2007, ApJS, 172, 1

(ref: Scoville2017) Scoville, N., Lee, N., Vanden Bout, P., et al. 2017, ApJ, 837, 150

(ref: Scoville2016) Scoville, N., Sheth, K., Aussel, H., et al. 2016, ApJ, 820, 83

(ref: Sersic1963) Sérsic, J. L. 1963, Boletin de la Asociacion Argentina de Astronomia La Plata Argentina, 6, 41

(ref: Shapley2003) Shapley, A. E., Steidel, C. C., Pettini, M., & Adelberger, K. L. 2003, ApJ, 588, 65

(ref: Speagle2014) Speagle, J. S., Steinhardt, C. L., Capak, P. L., & Silverman, J. D. 2014, ApJS, 214, 15

(ref: Stacey1991) Stacey, G. J., Geis, N., Genzel, R., et al. 1991, ApJ, 373, 423

(ref: Stacey2010) Stacey, G. J., Hailey-Dunsheath, S., Ferkinhoff, C., et al. 2010, ApJ, 724, 957

(ref: Stewart2009) Stewart, K. R., Bullock, J. S., Barton, E. J., & Wechsler, R. H. 2009, ApJ, 702, 1005

(ref: Stewart2011) Stewart, K. R., Kaufmann, T., Bullock, J. S., et al. 2011, ApJ, 738, 39

(ref: Sugahara2019) Sugahara, Y., Ouchi, M., Harikane, Y., et al. 2019, ApJ, 886, 29

(ref: Tacconi2018) Tacconi, L. J., Genzel, R., Saintonge, A., et al. 2018, ApJ, 853, 179

(ref: Tasca2017) Tasca, L. A. M., Le Fèvre, O., Ribeiro, B., et al. 2017, A&A, 600, A110

(ref: tomczak2017) Tomczak, A. R., Lemaux, B. C., Lubin, L. M., et al. 2017, MNRAS, 472, 3512

(ref: Toniazzo2001) Toniazzo, T. & Schindler, S. 2001, MNRAS, 325, 509

(ref: Tornatore2004) Tornatore, L., Borgani, S., Matteucci, F., Recchi, S., & Tozzi, P. 2004, MNRAS, 349, L19

(ref: Tozzi2003) Tozzi, P., Rosati, P., Ettori, S., et al. 2003, ApJ, 593, 705

(ref: Trainor2015) Trainor, R. F., Steidel, C. C., Strom, A. L., & Rudie, G. C. 2015, ApJ, 809, 89

(ref: Vallini2017) Vallini, L., Ferrara, A., Pallottini, A., & Gallerani, S. 2017, MNRAS, 467, 1300

(ref: Vallini2013) Vallini, L., Gallerani, S., Ferrara, A., & Baek, S. 2013, MNRAS, 433, 1567

(ref: Velusamy2014) Velusamy, T. & Langer, W. D. 2014, A&A, 572, A45

(ref: Verhamme2018) Verhamme, A., Garel, T., Ventou, E., et al. 2018, MNRAS, 478, L60

(ref: Vogelsberger2014) Vogelsberger, M., Genel, S., Springel, V., et al. 2014, MNRAS, 444, 1518

(ref: Vulcani2017) Vulcani, B., Moretti, A., Poggianti, B. M., et al. 2017, ApJ, 850, 163

(ref: Wen2016) Wen, Z. Z. & Zheng, X. Z. 2016, ApJ, 832, 90

(ref: Wetzel2009) Wetzel, A. R., Cohn, J. D., & White, M. 2009, MNRAS, 395, 1376

(ref: Zanella2018) Zanella, A., Daddi, E., Magdis, G., et al. 2018, MNRAS, 481, 1976

[^1]: $ID=705574$ in the COSMOS2015 catalogue ((cite: Laigle2016)).

[^2]: The physical properties of $\rm C15\_705574$ reported in the COSMOS2015 catalogue are computed adopting the photometric redshift. However, given the high accuracy of the latter ($|z_{\rm phot} - z_{\rm [CII]}| \sim0.05$; see text) we assume $M_{\star}$ and ${\rm SFR}$ to be correct within their uncertainties.

[^3]: Data drawn from a recently approved mid-cycle-26 HST program (Faisst et al., in prep.).

[^4]: <http://www.eso.org/rm/api/v1/public/releaseDescriptions/132>

[^5]: We note that the actual velocity offsets are likely to be even lower, since the redshift measured through Ly$\alpha$ can be off by few hundreds of ${\rm km~s^{-1}}$ toward the red (see e.g., (cite: Shapley2003; Trainor2015; Verhamme2018; Cassata2020)).

[^6]: As an alternative spectra-extraction procedure, we tested a 1$''$-aperture centred on the \[CII\] peaks, and the results are virtually unchanged, not affecting our interpretation.

[^7]: This choice helps when comparing the single galaxy spectra with the emission line profile of the full \[CII\] emitting system, as discussed further on, whose centroid corresponds to a $z_{\rm ref} = 4.570$.

[^8]: We assume that the contribution from the satellite galaxies $\#C$ and $\#D$ to gas-pollution through outflows is negligible. Indeed, from their $L_{\rm [CII]}$, using the $L_{\rm [CII]} - {\rm SFR}$ relation calibrated by (cite: Schaerer2020), we find ${\rm SFRs}  \lesssim 10 ~{\rm M_\odot ~ yr^{-1}}$, and galaxies with such a low SFR at high-$z$ have been reported to not show signatures of prominent outflows (e.g., (cite: Ginolfi2020)), nor signs of significant amount of circumgalactic emission (e.g., (cite: Ginolfi2020; Fujimoto2020)).

[^9]: We used three different calibrations, which give consistent results: (i) ${\rm SFR}_{\tiny{CGM}}^{\tiny{[CII]}} \sim 129 \pm 46 ~{\rm M_\odot ~ yr^{-1}}$ from (cite: Schaerer2020), calibrated for galaxies at $4<z<6$; (ii) ${\rm SFR}_{\tiny{CGM}}^{\tiny{[CII]}} \sim 124 \pm 40 ~{\rm M_\odot ~ yr^{-1}}$ from (cite: DeLooze2014), calibrated for local galaxies; (iii) ${\rm SFR}_{\tiny{CGM}}^{\tiny{[CII]}} \sim 125 ~{\rm M_\odot ~ yr^{-1}}$ from the model of (cite: Lagache2018). Errors on the SFR are computed using the uncertainties on the parameters of the relations.

</paper>

## Items to check

```json
[
 {
  "path": "results_numeric[4].evidence[0]",
  "value": "CGM fraction of [CII] = 50 %",
  "failed_quote": "about $50 ~(\\pm6) ~\\%$ (see Fig. [6](#fig:fig6)) of the total [CII] luminosity resides *between* the individual components"
 },
 {
  "path": "claims[0].evidence[0]",
  "value": "A metal-enriched circumgalactic envelope exists",
  "failed_quote": "about $50 ~(\\pm6) ~\\%$ (see Fig. [6](#fig:fig6)) of the total [CII] luminosity resides *between* the individual components"
 }
]
```

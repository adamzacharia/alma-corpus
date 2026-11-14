# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2023MNRAS.523...23W\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
MNRAS **000**, 1–18 (2022) Preprint 10 May 2023 Compiled using MNRAS L [A] TEX style file v3.0

## **ALMA High-Level Data Products: Submillimetre counterparts of SDSS** **quasars in the ALMA footprint**


A. Wong [1] _[,]_ [2], E. Hatziminaoglou [1] _[★]_, A. Borkar [3], G. Popping [1], I. Pérez-Fournon [4] _[,]_ [5], F. Poidevin [4] _[,]_ [5],
F. Stoehr [1], H. Messias [6] _[,]_ [7]

1 _ESO, Karl-Schwarzschild-Str. 2, 85748 Garching bei München, Germany_
2 _Nanyang Technological University, 50 Nanyang Avenue, 639798 Singapore_
3 _Astronomical Institute, Czech Academy of Sciences, Bocní II 1401, 141 00 Prague, Czech Republic_
4 _Instituto de Astrofísica de Canarias, E-38205 La Laguna, Tenerife, Spain_
5 _Departamento de Astrofísica, Universidad de La Laguna, E-38206 La Laguna, Tenerife, Spain_
6 _Joint ALMA Observatory, Alonso de Córdova 3107, Vitacura 763-0355, Santiago, Chile_
7 _European Southern Observatory, Alonso de Córdova 3107, Vitacura, Casilla 19001, Santiago de Chile, Chile_


Accepted XXX. Received YYY; in original form ZZZ


**ABSTRACT**

The Atacama Large Millimetre/submillimetre Array (ALMA) is the world’s most advanced radio interferometric facility,
producing science data with an average rate of about 1 TB per day. After a process of calibration, imaging and quality assurance,
the scientific data are stored in the ALMA Science Archive (ASA), along with the corresponding raw data, making the ASA
an invaluable resource for original astronomical research. Due to their complexity, each ALMA data set has the potential for
scientific results that go well beyond the ideas behind the original proposal that led to each observation. For this reason, the
European ALMA Regional Centre initiated the High-Level Data Products initiative to develop science-oriented data products
derived from data sets publicly available in the ASA, that go beyond the formal ALMA deliverables. The first instance of this
initiative is the creation of a catalogue of submillimetre (submm) detections of Sloan Digital Sky Survey (SDSS) quasars from the
SDSS Data Release 14 that lie in the aggregate ALMA footprint observed since ALMA Cycle 0. The ALMA fluxes are extracted
in an automatic fashion, using the ALMA Data Mining Toolkit. All extractions above a signal-to-noise cut of 3.5 are considered,
they have been visually inspected and the reliable detections are presented in a catalogue of 376 entries, corresponding to 275
unique quasars. Interesting targets found in the process, i.e. lensed or jetted quasars as well as quasars with nearby submm
counterparts are highlighted, to facilitate further studies or potential follow up observations.


**Key words:** quasars: general – submillimetre: galaxies – catalogues



**1** **INTRODUCTION**


Scientific archives are not only the legacy of their facilities, guaranteeing the fundamental scientific principle of the reproducibility
of the results, but a primary resource for new, independent research.
Archival data complement present-day research, as they provide the
foundation on which knowledge can be progressively built on. As the
interpretation of information evolves over time, thanks to improved
or new methodologies, archive contents allow for the re-evaluation
of earlier data sets and results, with the capacity to influence the
research done in the present. All the above are especially true for
data sets that are as rich as those produced by the Atacama Large
Millimetre/submillimetre Array (ALMA), where the original publication by the Principal Investigator (PI) often enough only partially
exploits the full potential of the entire data set. While valid for each
individual data set, this statement is particularly true for the combined body of all data sets that have been observed by a facility over
time. That combined body forms a new data set in its own right


_★_ E-mail: ehatzimi@eso.org


© 2022 The Authors



enabling cross-project research, such as statistical analyses or deep
data combination.


After a decade of observations, the ALMA Science Archive (ASA)
contains more than 19000 Member Observation Unit Sets (MOUSs).
An MOUS roughly corresponds to a Science Goal defined in a proposal at the time of submission, split per array, configuration or
spectral tuning. Here we define the “ALMA footprint” as the aggregate region of the sky with at least one ALMA exposure (i.e.
MOUS) that has been observed as part of PI observations since the
start of ALMA operations (Cycle 0) all the way to Cycle 8, including
all observations with proprietary time that expired by November 1,
2022. The ALMA footprint is shown in Fig. 1. ALMA is currently
producing between 300 and 400 TB of raw and reduced data per year.
The potential for archival research is steadily increasing with time as
more observations get added. This is also evidenced by the raising
fraction of ALMA publications that make use of ALMA archival
data: In 2021, 28% of all ALMA peer-reviewed publications were
(partially) based on archival data (Stoehr et al. 2022). ALMA data
are used over and over again to produce original science, as shown in
Fig. 2, with some ALMA projects having been used in more than 20

2 _A. Wong et al._


**Figure 1.** The ALMA science target observations footprint (calibration fields
are not included). Note that, in most cases, the ALMA field of view is smaller
than the pixel.


10 [3]


10 [2]


10 [1]


10 [0]


0 10 20 30

Number of times a project has been used in a publication


**Figure 2.** Re-usage statistics of ALMA projects.


publications. At the same time, the over-subscription for ALMA PI
observations has never been higher, with the pressure reaching above
7 in Cycle 9 in Europe [1] . Therefore, while it is increasingly difficult
to obtain PI data due to the over-subscription, the potential of conducting archival research is growing. The usage of ALMA archival
data is supported by the ALMA Regional Centres (ARCs) in Europe,
North America and East Asia, that continuously assist ALMA users
also through face-to-face visits, in making optimal use of the wealth
of the ASA to conduct original, high-impact research.
One of the key strategic goals of ALMA is to further increase
the scientific usage of the ASA [2] and the development of scienceoriented, curated data products to further facilitate the scientific
exploitation of the ASA. In response to this, the European ARC
network (Hatziminaoglou et al. 2015) launched the High-Level Data
Products (HLDP) initiative. The goal of the initiative is to develop
such science-oriented data products of interest to the community and
to develop, internally, the knowledge to support the community with
a diverse range of archival science cases. The current efforts within


1 https://almascience.eso.org/documents-and-tools/cycle9/cycle-9proposal-submission-statistics
2 https://www.eso.org/sci/facilities/alma/announcements/20180712-almadevelopment-roadmap.pdf


MNRAS **000**, 1–18 (2022)



the HLDP initiative include the creation of new image products and
catalogues based on information stored in the ASA, as well as tools
that facilitate the interaction with the ASA.

As a demonstration of the capabilities of HLDP-like initiatives,
we present in this paper a catalogue of ALMA detections of Sloan
Digital Sky Survey (SDSS) quasars within the ALMA footprint. The
paper is structured as follows: Section 2 describes the SDSS quasar
sample in the ALMA footprint. Section 3 delineates the methodology
of the extraction of the ALMA fluxes from the fits products in the
ASA and subsequent visual inspection. The astroquery script used
for the identification of SDSS quasars in the ALMA footprint is given
in Appendix A. Section 4 discuses the contents of the catalogue of
submillimetre (submm) counterparts of the SDSS quasars. Section
5 presents sources of particular interest found during the analysis,
i.e. jetted and lensed quasars as well as objects with nearby submm
companions, while Sec. 6 summarises the outcomes of this work and
indicates how quasar research could benefit from such data sets. All
the tables produced by this work are presented in Appendix B.


**2** **SDSS QUASARS IN THE ALMA FOOTPRINT**


The parent sample for the present study is the SDSS Data Release 14
(DR14) catalogue of AGN and quasars (DR14Q; Pâris et al. 2018).
The DR14Q consists of 526,356 spectroscopically confirmed quasars
from all SDSS data releases up until DR14, which have confirmed
redshift, spectral properties and black hole masses (Rakshit et al.
2020). Setting aside sources with a declination above 40 deg, that
are not observable by ALMA, results in a list of 357,392 objects to
be considered.

These sources were matched against the metadata of the ASA to
identify the objects within the ALMA footprint, among observations
taken under scientific categories “Active galaxies”, “Cosmology”,
“Galaxy evolution” and “Local Universe”, using the script presented
in Appendix A. Categories “Disks and planet formation”, “ISM and
Star Formation”, “Stars and Stellar Evolution” and “Solar System”
were left out of this pilot project, as many of these have complex
continuum images with overlapping structures. The aim of the work
presented here was to put together an automated methodology that
has the potential to be repeated in regular intervals, with minimum
requirements for visual inspection of every single extraction. Future
attempts for an updated catalogue may include images from the
remaining science categories, too. The SDSS quasars may have been
the primary target of each observation or they may be lying in a
region observed by ALMA while targeting different objects. The
match resulted in a total of 1295 entries, i.e. 1295 instances of SDSS
quasars falling within the ALMA footprint. This corresponds to 732
unique sources within the regions covered by 288 unique ALMA
projects, with a total of 790 MOUSs.
Note that, in addition to the objects presented here, hundreds of
DR14Q quasars have been observed by ALMA as calibrators. The
analysis of the submm continuum emission of these calibrators has
been discussed in Bonato et al. 2018 and are not included in this

work.


**3** **EXTRACTION OF SUBMM COUNTERPARTS**


To extract the submm continuum counterparts of SDSS quasars in
the ALMA footprint in an automated fashion, we made use of the

ALMA Data Mining Toolkit (ADMIT [3] ; Teuben et al. 2015). ADMIT
is a python-based execution environment and set of tools designed
for analysing image data cubes. Running ADMIT was not limited to
the region around the SDSS coordinates but it was run, instead, on
the full images. To search for continuum emission we made use of
the task `Sfind2D_AT`, which is based on the CASA `findsources`
task. This task searches for point-like sources in continuum images,
by identifying emission peaks brighter than _𝑁_ times the typical 1
_𝜎_ noise (signa-to-noise or SNR) limit of the data, where _𝑁_ is predefined by the user. In this work we require that the emission peaks
have a flux of at least _𝑁_ = 3.5 times the 1 _𝜎_ noise limit of the data.
Once an emission peak is identified, the `Sfind2D_AT` task then fits
the region around the brightest pixel value with a two-dimensional
Gaussian to obtain integrated flux and shape (major and minor axis
size and position angle) information. In general the `Sfind2D_AT` task
does not recover highly resolved sources with complex structures well
(e.g., rings or arms), breaking these down into multiple (sometimes
overlapping) Gaussians. These cases were assessed at the time of the
visual inspection.
The initial search for a bright peak is performed on primary-beam
uncorrected images to ensure a coherent noise profile throughout the
image. The Gaussian fit and flux determination is performed on the
primary-beam corrected image. In the few cases where no primarybeam information was available for an MOUS in the ASA (this can
happen for some data taken during the early ALMA observing cycles), the source finding and fitting procedures were both performed
on the primary-beam corrected image available in the ASA. The final
ADMIT output consists of a full list of sources detected within each
ALMA image that contains coordinates of at least one SDSS quasar.
To identify the submm source associated with each of the SDSS
quasars, we cross-matched the ADMIT list with the reduced DR14Q
catalogue, using a matching radius of 5 [′′] centred on the SDSS coordinates. All of the extraction within this 5 [′′] radius were then visually
inspected.


**3.1** **Visual inspection**


The veracity of the ADMIT extractions was determined through visual inspection. A total of 1707 ALMA extractions were returned
after the cross-matching between the ADMIT list and DR14Q catalogue, applying a 5 [′′] search radius around the SDSS coordinates. All
ALMA images containing one of these extractions were inspected
using CARTA [4], to identify image artefacts, unreliable extractions or
extractions that did not correspond to the SDSS quasar.
Figure 3 showcases the main scenarios that were encountered
during visual inspection. Example (a) shows a confirmed submm
counterpart to an SDSS quasar. Of the 1707 extractions, 1225 were
deemed non-reliable ALMA counterparts of the SDSS quasars because of one of the following three cases: _𝑖_ ) 107 extractions, corresponding to 25 unique objects, occurring in the outer and noisier
parts of the ALMA images (see e.g. Fig. 3 panels (b) and (c), showing
non-reliable extractions coinciding (or not) with the location of the
quasar); _𝑖𝑖_ ) while no submm counterpart was visible at the location
of the quasar, an ADMIT extraction occurred in the vicinity of the
quasar (for example Fig. 3, panel (d)); and _𝑖𝑖𝑖_ ) four occasions (four
unique objects) for which, while an obvious ALMA counterpart was
located right at the position of the SDSS quasar, no automatic flux
extraction was performed (see Fig. 3, panel (e) for an example). This


3 https://admit.astro.umd.edu/
4 https://cartavis.org



_ALMA counterparts of SDSS quasars_ 3


was due to the lack of a primary beam response curve associated
to the corresponding images discussed in the previous section. In
these cases, the (high) noise level at the outer edges of the image
dominated the noise level of the whole image, causing sources that
were clearly visible on the images to fail the SNR cut of 3.5. These
four sources were not included in Table B1 but we provide their
information separately, in Table B5.
The best differentiator found to distinguish between reliable and
unreliable detection was the ratio of the separation between the optical and submm coordinates and the beam major axis, _𝛼_ _𝑚𝑎𝑥_ _[𝑏]_, as shown
in Fig. 4. Visual inspection indicated that a submm extraction was
associated to the SDSS quasar if the ALMA and SDSS coordinates
coincide within 1.5× _𝛼_ _𝑚𝑎𝑥_ _[𝑏]_, a value slightly above the minimum of
∼1 seen in the bimodal distribution of this quantity in Fig. 4. Only
2.5% of the non-reliable detections (filled grey histogram) have a
ratio below 1.5, with the fraction dropping to 1% when a cut at a
ratio of 1.0 is applied. At the same time, only 1.5% of all reliable
detections (blue histogram) have a value above 1.0. In other words,
in order to fully automate the method without further need for visual
inspection, a cut at Separation / _𝛼_ _𝑚𝑎𝑥_ _[𝑏]_ = 1.0 could be imposed, ensuring minimum contamination and maximum completeness of the
resulting catalogue.
For some cases (122 in total, corresponding to 34 unique quasars),
ADMIT performed multiple extractions on the same source (red
spikes in Fig. 4. In these cases, the extraction centred closer to the
SDSS coordinates was kept. In the few (six) cases where two extractions were performed on exactly the same point in the image,
the extraction with the highest peak SNR was kept. The multiple
extractions are shown in red spikes in Fig. 4. 36% of those cases have
Separation / _𝛼_ _𝑚𝑎𝑥_ _[𝑏]_ _>_ 1 _._ 0. The remaining ones, for a full automation
of the process, can be removed by simply applying the minimum
separation and peak SNR criteria described above.


**4** **THE ALMA COUNTERPARTS OF SDSS QUASARS**


Following the visual inspection, the submm counterparts of SDSS
quasars in the DR14Q catalogue were identified. A total of 376
reliable detections of 275 unique objects from 84 unique projects
were found, from observations taken between July 18, 2014 and
September 25, 2021, and with a proprietary time that expired before
November 1, 2022. Of those 376 observations, 87% were targeting
the SDSS quasar (i.e. the observations are centred on the quasar),
while for the remaining cases the quasar just happened to be on
an ALMA image centred on a different target. Lensed quasars are
not included in these numbers, as they break into multiple submm
detections but are discussed separately in Sec. 5.2.
The sky distribution of the SDSS quasars with ALMA counterparts identified in this work and the distribution separations (in arcsec) between the SDSS and ALMA positions are shown in Figs. 5
and 6, respectively. Fig. 7 shows the distribution of the bolometric
luminosities, L _𝑏𝑜𝑙_, of quasars with submm detections as a function
of rest frequency of the submm observations, corresponding to the
representative frequency of each ALMA band shifted to _𝑧_ = 0. The
figure provides a representation of the parameter space sampled by
the continuum observations with ALMA of the SDSS quasars with
L _𝑏𝑜𝑙_ between 10 [45] and 10 [48] erg/s, indicating that most of the observations targetted the star formation in the hosts of quasars at ∼790
GHz rest frequency (or ∼320 micron).
ALMA counterparts of SDSS quasars were found in observations
carried out in bands 3 to 9, with the band distribution shown in Fig.
8. Most of the observations were done in bands 3, 6 and 7, with


MNRAS **000**, 1–18 (2022)

4 _A. Wong et al._



(a) (b) (c)


(d) (e)


**Figure 3.** Examples of cases encountered during the visual inspection of ALMA images, performed to determine the veracity of the ADMIT extractions. The
black square and red circle correspond to the coordinates of the submm ALMA source and the SDSS quasar respectively. The circles are (a) SDSS and ALMA
counterparts coinciding within 1.5× _𝛼_ _𝑚𝑎𝑥_ _[𝑏]_ . (b) and (c) illustrate cases of spurious ALMA extractions. (d) Shows the case of a submm source extraction in the
vicinity of the SDSS quasar while the quasar itself does not emit in the submm. Finally, (e) shows a missed ADMIT extraction, with a visible submm source at
the exact location of the SDSS quasar. The sizes of the circles and squares are 4 [′′] and 2 [′′] across respectively.



80


70


60


50


40


30


20


10


0



0 _:_ 01 0 _:_ 1 1 10
Separation _=®_ max [b]



**Figure** **4.** Distribution of the ratio between the separation of the SDSS coordinates from the ALMA coordinates and _𝛼_ _𝑚𝑎𝑥_ _[𝑏]_ for each extraction, for
the reliable extractions (blue), the multiple extractions occurring on the same
sources (red) and the non-reliable detections (grey). The histogram in black

is the sum of all.


MNRAS **000**, 1–18 (2022)



40


30


20


10


0


_−_ 10


0 50 100 150 200 250 300 350


SDSS RA [deg]


**Figure** **5.** SDSS coordinates of quasars with submm counterparts in the
ALMA footprint.


51, 190 and 106 observations, respectively. 6% (2%) of the objects
had ALMA counterparts in two (three) bands and one object was
observed in four ALMA bands.

Fig. 9 presents the integrated flux as a function of redshift, for
bands 3 (blue circles), 4 (yellow squares), 6 (red stars) and 7 (green

30


25


20


15


10


5


0

10 _[−]_ [2] 10 _[−]_ [1] 10 [0]


Separation [arcsec]


**Figure** **6.** The distribution of the separation between the optical (SDSS)
and submm (ALMA) coordinates of the quasars with submm counterparts
confirmed by visual inspection.



100


50


0


10 [3]


10 [2]


10 [1]


10 [0]


10 _[−]_ [1]



_ALMA counterparts of SDSS quasars_ 5


|Col1|Col2|Col3|Col4|
|---|---|---|---|
|B3<br>B4<br>B6<br>B7|B3<br>B4<br>B6<br>B7|B3<br>B4<br>B6||
|B3<br>B4<br>B6<br>B7|B3<br>B4<br>B6<br>B7|B3<br>B4<br>B6||
|B3<br>B4<br>B6<br>B7|B3<br>B4<br>B6<br>B7|B3<br>B4<br>B6||
|B3<br>B4<br>B6<br>B7|B3<br>B4<br>B6<br>B7|B3<br>B4<br>B6||
|B3<br>B4<br>B6<br>B7|B3<br>B4<br>B6<br>B7|B3<br>B4<br>B6||
|B3<br>B4<br>B6<br>B7|B3<br>B4<br>B6<br>B7|B3<br>B4<br>B6||
|B3<br>B4<br>B6<br>B7|B3<br>B4<br>B6<br>B7|B3<br>B4<br>B6||



0 1 2 3 4 5

Redshift



0 50

Counts



48


47


46


45



30


25


20


15


10


5



0


2 _._ 2 2 _._ 4 2 _._ 6 2 _._ 8 3 _._ 0 3 _._ 2


log frequency [GHz]


**Figure 7.** Distribution of the L _𝑏𝑜𝑙_ as a function of the rest frequency, corresponding to the representative frequency of each band shifted to _𝑧_ = 0, for all
the submm counterparts of the SDSS quasars.


150


100


50


3 4 5 6 7 8 9

ALMA band


**Figure 8.** Number of submm counterparts of SDSS quasars per band.


diamonds). The adjacent histograms show the distribution of the two
parameters. 70% of the objects are in the redshift range between 1
and 3, encompassing the peak of quasar activity. The sample is in no
way complete or statistical and any trends seen in this figure are not
representative of the quasar population. The bright fluxes in bands
3 and 4 (above a couple tens of mJy) are indicative of synchrotron



**Figure 9.** Integrated flux per band as a function of redshift, for the four bands
with the larger number of ALMA observations. The histograms show the
number of sources in each redshift bin (top histogram) and in each flux bin
(right histogram). The dotted lines mark the bin edges.


emission out to redshifts of ∼2, while the bulk of bands 6 and 7
emission (at redhifts above ∼1.3) traces star formation in the hosts
of the quasars.
The ALMA submm counterparts of DR14Q quasars were compiled into a catalogue, an excerpt of which is shown in Table B1. The
table contains the SDSS object name and coordinates; the optical
redshift; the ALMA source coordinates; the separation between the
two sets of coordinates; the ALMA band and array (12-m or 7-m, the
latter including TP observations); the angular resolution and continuum sensitivity of the image from which the submm counterpart was
extracted; the peak and integrated fluxes with their respective errors;
the major and minor axes of the extracted ellipse and associated position angle; the beam major and minor axes and position angle; the
image RMS; the date of observation; the project code and MOUS ID;
and a column indicating whether an entry is among with ALMACAL
objects. Indeed, of the 276 unique quasars in the catalogue, 19 are
in common with the 754 calibrators in the ALMACAL catalogue
(Bonato et al. 2018). 54 unique objects were observed more than
once in the same band as part of different projects. In such cases, all
detections are included in the table. The full catalogue is available as
online material.

Non-detection information has a scientific value, when e.g. looking
for detection limits. For this reason, we compiled the list of DR14Q
quasars within the ALMA footprint for which no detection above
an SNR cut of 3.5 was found on any of the images that contained
them. The objects are listed in Table B4. Other than the SDSS ID,
coordinates and redshift, the table includes the ALMA band and
array, the angular resolution and continuum sensitivity, the project
code and the MOUS ID of the data set including the individual
quasars’ coordinates.


**5** **NOTES ON INDIVIDUAL OBJECTS**


The visual inspection of the list of SDSS quasars with ALMA counterparts revealed a number of interesting sources, presented in this


MNRAS **000**, 1–18 (2022)

6 _A. Wong et al._


section, namely jetted quasars (Sec. 5.1), lensed quasars (Sec. 5.2)
and quasars with more than one submm counterparts (physical or
projected) within 5 [′′] (Sec. 5.3). Each object is described briefly and
CARTA cutouts for each object are shown in Figs. 10, 11 and 12,
for jetted, lensed and objects with multiple submm counterparts,
respectively.


**5.1** **Jetted quasars**


Five SDSS quasars revealed submm jets in the ALMA images, shown
in Fig. 10. For these objects, the main catalogue (Table B1) only
includes the fluxes of the nucleus - not those from the various parts
of the jet. Some details about the jetted quasars are given below.
SDSS_J002025.22+154054.7 (3C 9) is a radio-loud quasar at a
redshift of 2.019, with radio and X-ray jets pointing to the north-west
and to the south-east of the quasar. The X-ray emission of this object
exceeds the radio emission by a factor five. Several mechanisms have
been suggested to explain the X-ray emission, namely non-thermal
synchrotron, non-thermal inverse Compton and thermal emission
(Fabian et al. 2003). Compared to the 4.9 GHz map (Bridle et al.
1994), only the knots in the south-east jet are detected on the ALMA
band 3 image (labelled as F, G, H, and I in Bridle et al. 1994), in
addition to the central feature matching the optical quasar (feature
D). Interestingly, the knot with the highest polarization fraction (G
with ∼30%) is also the only one that is resolved on the ALMA image.
Direct comparison with the 4.9 GHz map to retrieve a spectral-index
map is needed in order to establish whether there is evidence for
the location in which the jet goes through realignment as well as its
origin (see Bridle et al. 1994; Dennett-Thorpe et al. 2002). Finally,
although hot-spot A is located at the edge of the primary beam, its
non-detection, as well as that of hot spot K, is related to the fact that
they likely comprise older (less energised) electrons, hence harder to
detect at mm wavelengths. The ALMA data were part of the sample
analysed by Keenan et al. (2021).
SDSS_J085841.44+140944.8 (3C 212), also part of the Keenan
et al. (2021) sample, is a radio-loud red quasar at a redshift of 1.049
(Aldcroft et al. 2003), with an X-ray absorption system intrinsic to
the quasar itself or its host galaxy (Aldcroft et al. 2002). The spatial
resolution on the ALMA image is coarser than that of the 3.6 cm VLA
map. Nevertheless, one can still identify the emission associated with
the three jet knots in the north-east direction, as well as the two lobe

∼
hot spots farther out ( 40 projected kpc). The latter may be related
to ongoing supply of energetic electrons and magnetic field to these
regions (e.g., Machalski et al. 2016), but a multi-frequency analysis
is required to confirm this scenario.
SDSS_J123200.01-022404.7 (4C -02.55) is a quasar at a redshift
of 1.05 observed in band 6 (Szakacs et al. 2021). Comparing with
FIRST (1.4 GHz) and VLASS (2–4 GHz) imaging, there is a clear
morphological difference between mm and cm wavelengths. While
ALMA shows four jet knots to the west of the location of the quasar,
the VLA image reveals a bright central emission and a fainter source
(a jet knot or lobe) to the east of the quasar. This feature falls outside
the ALMA field of view. Given the distinct spatial resolutions of each
image (i.e. all the structure detectable by ALMA is within a FIRST
survey synthesized beam), it is impossible to determine whether this
morphology is related to significant jet realignment (i.e. the closest
jet component goes from being that in the eastern side to the one in the
western side), nevertheless this is the most likely scenario. We finally
note that the jet emission detectable by ALMA is co-spatial with the
extended emission seen in VLASS Quicklook image, but improved
imaging of these data is required to confirm this association.
SDSS_J135706.53+253724.4 (7C 1354+2552), is a radio-loud


MNRAS **000**, 1–18 (2022)



quasar at a redshift of 2.007, with two jets that are perpendicular
to each other (Lonsdale et al. 1993). While the north-south direction comprises two isolated lobes (detected only at 1.4 GHz) whose
intermediate point does not coincide with the quasar position, the
east-west oriented component is a one-sided jet (to the west of the
quasar) and shows remarkable resemblance in 1.4, 5, and 146 GHz.
As reported in Lonsdale et al. (1993), the east-west jet is bent (also
visible on the ALMA image) and potentially connects with the southern lobe, hinting at a complex nature of the north-south lobes. Molecular gas emission towards the north-east is reported by Vayner et al.
(2021b,a). As there is no evidence for cold outflows at the sensitivities of the observations, the molecular gas emission might be related
to a merging galaxy.
Finally, SDSS_J170955.01+223655.7 (4C 22.44) is a radio-loud
quasar at a redshift of 1.549. Its radio jets extend out to 7 [′′] along
the east–west direction and the two lobes dominate the emission at

3 GHz as seen in the VLASS Quicklook image (Lacy et al. 2020). In
the ALMA band 4 image one can also see a bright core emission at
the location of quasar’s optical coordinates (Vayner et al. 2021b). The
detected source to the north of the quasar does not have a counterpart
on the SDSS image and could be a close companion or a chance
projection.


**5.2** **Lensed quasars**


Among the quasars in the ALMA footprint, six were already known
lensed quasars, with multiple images also visible on the ALMA data,
shown in Fig. 11. The fluxes of these objects are not included in
Table B1. As noted in Sec. 3, ADMIT does not perform well in the
case of complex structures. As a result, the automated extraction does
not guarantee reliable fluxes for all the images. These sub-structures
extracted by ADMIT do not always coincide with the real lensed
images, or at times a single elongated image (arc) has been broken
into more than one sources by the the ADMIT source extraction.
Table B3 includes all reliable ADMIT extractions, based on visual
inspection.
SDSS_J081331.28+254503.0 (HS 0810+2554), is a radio-quiet
quadruply lensed quasar at a redshift of 1.508, observed with ALMA
in bands 3 and 4 continuum and CO (3-2) (Chartas et al. 2020;
Stacey et al. 2021). For this object, Fig. 11 we chose a band 6
image found in the archive, where the multiple images are clearly
visible. Observations of this quasar in Chandra and XMM-Newton
have revealed highly ionized and relativistic outflows (Chartas et al.
2016), while VLBI observations revealed a faint jet to dominate the
radio emission (Hartley et al. 2019).
SDSS_J091127.61+055054.1 (RXJ0911.4+0551) is also a
quadruply lensed quasar at _𝑧_ =2.796 observed with ALMA in band
4, targeting also the CO (5-4) transition. Both continuum and CO
emission were found to be similarly compact (Stacey et al. 2021). It
was found to have a molecular-gas mass and far-infrared luminosity
an order of magnitude lower compared to other quasars. A detailed
analysis of the size and morphology of the galaxy (Anh et al. 2013)
showed that it was intrinsically a lower mass galaxy rather than an
evolved galaxy that had depleted its gas reservoir.
SDSS_J092455.79+021924.9, is a redshift 1.524 radio-quiet
quasar quadruply imaged by a z=0.394 early-type galaxy. The four
images are clearly visible in the targeted CO(5-4) line as well as in
the band 6 continuum (Badole et al. 2020). Broad line flux ratios
anomalies detected by HST are most likely caused by microlensing
effects (Morgan et al. 2006; MacLeod et al. 2015).
SDSS_J111816.94+074558.2 (PG1115_80), is a redshift 1.735
quasar observed with ALMA in band 7, where the four images are

_ALMA counterparts of SDSS quasars_ 7


SDSS_J002025.22+154054.7 [3] SDSS_J085841.44+140944.8 [3] SDSS_J123200.01-022404.7 [6]


SDSS_J135706.53+253724.4 [4] SDSS_J170955.01+223655.7 [4]


**Figure 10.** ALMA cutouts of the jetted SDSS quasars in the ALMA footprint. The location of the optical quasar is indicated with a red circle. The corresponding
ALMA band is indicated in square brackets next to the name of each object. All cutouts measure 20 [′′] in diameter while the red circles are 3 [′′] across.



clearly visible (Stacey et al.2021).Its dustemissionwas verycompact
with no apparent clumpy features. While no radio jets have been
detected, its radio luminosity indicates signs of star formation.
SDSS_J133018.64+181032.1 is a lensed quasar with a quadruple
configuration, at _𝑧_ =1.393, observed with ALMA in band 7.
Finally, SDSS_J141546.24+112943.4 (H1413+117), also known
as the Cloverleaf quasar, is a broad absorption line quasar at _𝑧_ =2.558,
lensed by a galaxy at an unknown redshift. The band 7 continuum
clearly shows the four counter-images (Stacey et al. 2021).
Note that the issue of the missing flux may affect some of the
reported fluxes, especially for the more diffuse counterparts. This is
a problem inherent to interferometric observations, far from trivial
(Plunkett et al. 2023), and addressing it is well outside the scope of
the present work.


**5.3** **Quasars with possible nearby submm counterpart**


During visual inspection 31 unique SDSS quasars with confirmed
ALMA counterparts were found to have at least one other ALMA
detection within 5 [′′] of the ALMA coordinates. These secondary
counterparts could be either close companions in proximity to the
primary source or chance associations. Table B2 lists the properties of
the primary and secondary counterparts in the same format as Table
B1. Cutouts around these objects are displayed in Fig. 12. Objects



with counterparts already confirmed in the literature are specifically
discussed below.


SDSS_J003011.76+004749.9, SDSS_J015017.71+002902.4 and
SDSS_J235944.94+022906.8 were part of the quasars sample observed by Hatziminaoglou et al. (2018) in the search for multiplicities of the ALMA Compact Array (ACA) counterparts of farinfrared bright quasars. The properties of the counterparts are given
in their work, however redshifts of the secondary counterparts were
not known and chance associations could not be ruled out.


SDSS_J074110.70+311200.2 was found to have two damped
Lyman− _𝛼_ (DLA) quasar absorption line systems, one at a redshift of
0.091 and the other at a redshift of 0.221. They were observed and
analysed in the optical and infrared wavelength by Turnshek et al.
(2001) and were found to have the lowest redshift of any confirmed
DLA absorption-line systems at the time. In Fig. 12, only the DLA
system at a redshift of 0.2212 is visible and labelled. The other object
is not visible, possibly because of its low surface brightness.


SDSS_J101549.00+002020.0 was found to have multiple close
sources that were detected in band 7 continuum and [CII] line emission less than 4 [′′] away (Bischetti et al. 2018). Several of these with
detected line emission had small velocity shifts with respect to the
line emission of the main quasar, and hence were considered close
companions. In the cutout shown in Fig. 12, only one such companion is visible. This companion was reported by Bischetti et al. (2018)
to have a separation from the main quasar of 3.5 [′′] and to have a


MNRAS **000**, 1–18 (2022)

8 _A. Wong et al._


SDSS_J081331.28+254503.0 [6] SDSS_J091127.61+055054.1 [4] SDSS_J092455.79+021924.9 [7]


SDSS_J111816.94+074558.2 [7] SDSS_J133018.64+181032.1 [7] SDSS_J141546.24+112943.4 [7]


**Figure 11.** ALMA cutouts of the lensed SDSS quasars in the ALMA footprint. The corresponding ALMA band is indicated in square brackets next to the name
of each object. All cutouts measure 20 [′′] in diameter while the squares are 1.4 [′′] across.



continuum flux of 1252±76 _𝜇_ Jy. The other detected companions had
continuum fluxes _<_ 400 _𝜇_ Jy. The low SNR of these detections is the
cause of their non-extraction by ADMIT.

SDSS_J141908.17+062834.8 was investigated by Vayner et al.
(2017). They found a kinematic feature located to the south-east of
the quasar and offset from by 1.06 [′′], providing evidence of a merging
disc system.

SDSS_J151155.98+040802.9 was observed by Trakhtenbrot et al.
(2017) in band 7 and was confirmed to have two sub-mm companions within 4 [′′] of the main quasar. Both are clearly visible in the
continuum image in Fig. 12. It was concluded that the closer companion was an interacting companion, while the further companion
was likely to be a chance association or a minor merger.

SDSS_J154938.71+124509.1 was observed by Bischetti et al.
(2021) and was found to have two line emitting companion sources
within 2.4 [′′] of the quasar. Only the further companion was extracted
on Fig. 12 as it is the brighter source. The second fainter companion
is located North of the quasar but it is not visible on the image cutout.

Band 8 observations of SDSS_J223619.19+132620.3 revealed two
nearby submm galaxies (Ogura et al. 2020). One of them was about
4 [′′] away from the quasar, while the other was about 10 [′′] away. Both
sources are also seen in the respective continuum image in Fig. 12.
Since no data in other wavelengths nor spectroscopic redshifts for
these objects were available, it was not possible to confirm whether
they were physical companions.


MNRAS **000**, 1–18 (2022)



**6** **DISCUSSION**


This paper describes the first instance of the High-Level Data Products initiative run at the European ALMA Regional Centre. This
initiative aims at producing advanced, science-oriented products by
combining the ALMA images and cubes publicly available in the
ALMA Science Archive. The result of this first instance of HLDP
is the creation of a catalogue of 376 submm detections of SDSS
DR14 quasars, corresponding to 275 unique quasars, in the ALMA
footprint.

The ALMA observations of the quasars in this work cover, depending on redshift and band, the restframe wavelengths between
∼ 190 _𝜇_ m and ∼1.8 mm for the majority of the sample (Fig. 7).
The main contributor to the emission at these wavelengths is dust,
heated by star formation processes in the quasar hosts, with some
contribution from the circumnuclear dust heated by the AGN (e.g.
Hatziminaoglou et al. 2010). Non-thermal (synchrotron) emission
from the nucleus, at least in the case of radio-loud quasars, may pitch
in to the mm wavelengths, however with single measurements per
object it is not possible to distinguish between the thermal and nonthermal components. Nevertheless, the flux measurements provided
in the catalogue are relevant to a number of AGN-related studies.

Most of our current knowledge on the far-infrared (FIR) to mm
properties of quasars is based on observations with poor spatial resolution, with e.g. SCUBA-2 or _Herschel_ /SPIRE (7.9 [′′] at 450 _𝜇_ m,
Dempsey et al. 2013 and 18 [′′] at 250 _𝜇_ m, Griffin et al. 2010, respec

_ALMA counterparts of SDSS quasars_ 9


SDSS_003011.76+004749.9 [7] SDSS_J005021.22+005135.0 [4] SDSS_J005233.67+014040.8 [4]


SDSS_010116.53+020157.3 [4] SDSS_J013825.53-000534.5 [4] SDSS_J015017.70+002902.4 [7]


SDSS_J021727.65-051502.8 [6] SDSS_J021757.30-050808.6 [7] SDSS_J074110.70+311200.2 [5]


**Figure** **12.** Cutouts of SDSS quasars with confirmed ALMA counterparts and secondary ALMA detections at or above a SNR of 3.5 within 5 [′′] of the main
quasar counterpart. The corresponding ALMA band is shown in square brackets next to the SDSS name of each object. All cutouts are 20 [′′] . The optical
coordinates if the quasars are indicated with a red circle, while the potential submm companions are marked with letters. The circles are 3 [′′] across except for
SDSS_J074110.70+311200.2 (2 [′′] ), SDSS_J141908.17+062834.8 (1.2 [′′] ) and SDSS_J225134.72+184840.0 (0.5 [′′] ).



tively). Because of the poor spatial resolution, identifying counterparts of FIR sources at other wavelengths has long been an issue
(e.g. Wang et al. 2014; Hurley et al. 2017). This in turns means that
the spectral energy distributions (SEDs) of quasars at wavelengths
beyond a few tens of micron are often poorly defined, consequently
affecting properties derived from those SEDs, such as SFRs in quasar
hosts, dust temperatures etc.



Thanks to their high spatial resolution, ALMA observations of
FIR-bright quasars can confirm the source of the FIR/submm emission (e.g. Hatziminaoglou et al. 2018), help evaluate the accuracy of
the FIR fluxes and add data points to the FIR SEDs. This, in turn,
results in a more accurate estimate of the total FIR emission and,
subsequently, to the calibration of the FIR-derived SFRs. In case of
multiple submm counterparts to the FIR sources, the FIR emission


MNRAS **000**, 1–18 (2022)

10 _A. Wong et al._


SDSS_J095923.55+022227.2 [6] SDSS_J100038.01+020822.4 [9] SDSS_J101549.00+002020.0 [7]


SDSS_J110045.23+112239.1 [7] SDSS_J111200.93+065530.1 [6] SDSS_J120110.31+211758.4 [8]


SDSS_J125353.35+104603.1 [7] SDSS_J134131.14+235043.3 [6] SDSS_J141546.24+112943.4 [7]


**Figure 12.** Continued



can be redistributed among those counterparts and the SEDs can be
improved, with a subsequent improvement of the SFR estimates.


And this is only a tiny sample of science cases that can be addressed
with data sets like the one produced in this work. Upcoming instances
of ALMA HLDP and HLDP-like initiatives will cater for a large
palette of science cases. The potential for the creation of valueadded, science-ready data products is large and it is increasing as
more data are added to the ASA every day, continuously providing
new possibilities for original, ground-breaking research.


MNRAS **000**, 1–18 (2022)



**ACKNOWLEDGEMENTS**


AW would like to thank the IAC and ESO for their hospitality
for a three- and a four-month visiting periods, respectively, during
which part of this work was pursued, and Nanyang Technological
University and the CN Yang Scholarship Programme for funding
his expenses for this project. EH acknowledges support from the
Fundación Jesús Serra and the Instituto de Astrofísica de Canarias

(IAC) under the Visiting Researcher Programme 2020-2022 agreed
between both institutions. AB acknowledges the support of the EUARC.CZ Large Research Infrastructure grant project LM2023059

_ALMA counterparts of SDSS quasars_ 11


SDSS_J141819.22+044135.0 [6] SDSS_J141908.17+062834.8 [4] SDSS_J151155.98+040802.9 [7]


SDSS_J154938.71+124509.1 [6] SDSS_J170955.01+223655.7 [4] SDSS_J213006.21+001256.6 [6]


SDSS_J214443.65+002327.9 [6] SDSS_J223619.19+132620.3 [8] SDSS_J224649.29-004954.3 [7]


**Figure 12.** Continued



of the Ministry of Education, Youth and Sports of the Czech
Republic and the Czech Science Foundation project No.19-05599Y.
IPF and FP acknowledge support from the Spanish State Research
Agency (AEI) under grant numbers PID2019-105552RB-C43.
This work makes use of TOPCAT, “TOPCAT & STIL: Starlink
Table/VOTable Processing Software”, M. B. Taylor, in Astronomical
Data Analysis Software and Systems XIV, eds. P Shopbell et al.,
ASP Conf. Ser. 347, p. 29, 2005; Astropy (Astropy Collaboration et
al. 2013, 2018); Numpy (Harris et al. 2020 https://numpy.org/citingnumpy/); Matplotlib (Hunter 2007). This paper makes use of the



following ALMA data: ADS/JAO.ALMA#2012.1.00175.S, ADS/JAO.ALMA#2012.1.00611.S, ADS/JAO.ALMA#2013.1.00535.S,
ADS/JAO.ALMA#2013.1.00576.S, ADS/JAO.ALMA#2013.1.01153.S, ADS/JAO.ALMA#2013.1.01178.S,
ADS/JAO.ALMA#2013.1.01342.S, ADS/JAO.ALMA#2013.1.01359.S, ADS/JAO.ALMA#2015.1.00137.S,
ADS/JAO.ALMA#2015.1.00260.S, ADS/JAO.ALMA#2015.1.00305.S, ADS/JAO.ALMA#2015.1.00329.S,
ADS/JAO.ALMA#2015.1.00582.S, ADS/JAO.ALMA#2015.1.00754.S, ADS/JAO.ALMA#2015.1.00856.S,


MNRAS **000**, 1–18 (2022)

12 _A. Wong et al._


SDSS_J225134.72+184840.0 [7] SDSS_J235637.86+005859.3 [6] SDSS_J235737.30+003546.2 [6]


SDSS_J235944.94+022906.8 [7]


**Figure 12.** Continued



ADS/JAO.ALMA#2015.1.00932.S, ADS/JAO.ALMA#2015.1.01034.S, ADS/JAO.ALMA#2015.1.01090.S,
ADS/JAO.ALMA#2015.1.01147.S, ADS/JAO.ALMA#2015.1.01148.S, ADS/JAO.ALMA#2015.1.01309.S,
ADS/JAO.ALMA#2015.1.01362.S, ADS/JAO.ALMA#2015.1.01366.S, ADS/JAO.ALMA#2015.1.01452.S,
ADS/JAO.ALMA#2015.1.01469.S, ADS/JAO.ALMA#2015.1.01564.S, ADS/JAO.ALMA#2016.1.00434.S,
ADS/JAO.ALMA#2016.1.00463.S, ADS/JAO.ALMA#2016.1.00569.S, ADS/JAO.ALMA#2016.1.00718.S,
ADS/JAO.ALMA#2016.1.00735.S, ADS/JAO.ALMA#2016.1.00798.S, ADS/JAO.ALMA#2016.1.00864.S,
ADS/JAO.ALMA#2016.1.01326.S, ADS/JAO.ALMA#2016.1.01481.S, ADS/JAO.ALMA#2016.1.01515.S,
ADS/JAO.ALMA#2016.2.00060.S, ADS/JAO.ALMA#2017.1.00102.S, ADS/JAO.ALMA#2017.1.00297.S,
ADS/JAO.ALMA#2017.1.00345.S, ADS/JAO.ALMA#2017.1.00358.S, ADS/JAO.ALMA#2017.1.00478.S,
ADS/JAO.ALMA#2017.1.00560.S, ADS/JAO.ALMA#2017.1.00571.S, ADS/JAO.ALMA#2017.1.00963.S,
ADS/JAO.ALMA#2017.1.01027.S, ADS/JAO.ALMA#2017.1.01052.S, ADS/JAO.ALMA#2017.1.01081.S,
ADS/JAO.ALMA#2017.1.01232.S, ADS/JAO.ALMA#2017.1.01324.S, ADS/JAO.ALMA#2017.1.01332.S,
ADS/JAO.ALMA#2017.1.01368.S, ADS/JAO.ALMA#2017.1.01492.S, ADS/JAO.ALMA#2017.1.01527.S,


MNRAS **000**, 1–18 (2022)



ADS/JAO.ALMA#2017.1.01559.S, ADS/JAO.ALMA#2017.1.01572.S, ADS/JAO.ALMA#2017.1.01676.S,
ADS/JAO.ALMA#2018.1.00526.S, ADS/JAO.ALMA#2018.1.00583.S, ADS/JAO.ALMA#2018.1.00585.S,
ADS/JAO.ALMA#2018.1.00681.S, ADS/JAO.ALMA#2018.1.00699.S, ADS/JAO.ALMA#2018.1.00828.S,
ADS/JAO.ALMA#2018.1.00859.S, ADS/JAO.ALMA#2018.1.00932.S, ADS/JAO.ALMA#2018.1.00992.S,
ADS/JAO.ALMA#2018.1.01008.S, ADS/JAO.ALMA#2018.1.01044.S, ADS/JAO.ALMA#2018.1.01368.S,
ADS/JAO.ALMA#2018.1.01447.S, ADS/JAO.ALMA#2018.1.01464.S, ADS/JAO.ALMA#2018.1.01476.S,
ADS/JAO.ALMA#2018.1.01575.S, ADS/JAO.ALMA#2018.1.01591.S, ADS/JAO.ALMA#2018.1.01784.S,
ADS/JAO.ALMA#2018.1.01806.S, ADS/JAO.ALMA#2018.1.01817.S, ADS/JAO.ALMA#2018.1.01830.S,
ADS/JAO.ALMA#2019.1.00403.S, ADS/JAO.ALMA#2019.1.00411.S, ADS/JAO.ALMA#2019.1.00477.S
ADS/JAO.ALMA#2019.1.00840.S, ADS/JAO.ALMA#2019.1.00883.S, ADS/JAO.ALMA#2019.1.00946.S,
ADS/JAO.ALMA#2019.1.00948.S, ADS/JAO.ALMA#2019.1.00959.S, ADS/JAO.ALMA#2019.1.01022.S,
ADS/JAO.ALMA#2019.1.01070.S, ADS/JAO.ALMA#2019.1.01251.S, ADS/JAO.ALMA#2019.1.01422.S,
ADS/JAO.ALMA#2019.1.01514.S, ADS/JAO.ALMA#2019.1.01587.S, ADS/JAO.ALMA#2019.1.01709.S,

ADS/JAO.ALMA#2019.1.01802.S, ADS/JAO.ALMA#2019.2.00034.S, ADS/JAO.ALMA#2019.2.00085.S.
ALMA is a partnership of ESO (representing its member states),
NSF (USA) and NINS (Japan), together with NRC (Canada),
MOST and ASIAA (Taiwan), and KASI (Republic of Korea),
in cooperation with the Republic of Chile. The Joint ALMA
Observatory is operated by ESO, AUI/NRAO and NAOJ.


**DATA AVAILABILITY**


Thefull versions of the cataloguesproducedin thispaperareavailable
as online supplementary material. The ALMA data used to produce
the catalogues are all available in the ASA.


**REFERENCES**


Aldcroft T. L., Murray S. S., Elvis M., 2002, in Crenshaw D. M., Kraemer
S. B., George I. M., eds, Astronomical Society of the Pacific Conference
Series Vol. 255, Mass Outflow in Active Galactic Nuclei: New Perspectives. p. 37
Aldcroft T., Siemiginowska A., Elvis M., Mathur S., Nicastro F., Murray S.,
2003, The Astrophysical Journal, 597, 751
Anh P. T., Boone F., Hoai D. T., Nhung P. T., Weiß A., Kneib J. P., Beelen
[A., Salomé P., 2013, A&A, 552, L12](http://dx.doi.org/10.1051/0004-6361/201321363)
Badole S., Jackson N., Hartley P., Sluse D., Stacey H., Vives-Arias H., 2020,

[MNRAS, 496, 138](http://dx.doi.org/10.1093/mnras/staa1488)

[Bischetti M., et al., 2018, A&A, 617, A82](http://dx.doi.org/10.1051/0004-6361/201833249)

[Bischetti M., et al., 2021, A&A, 645, A33](http://dx.doi.org/10.1051/0004-6361/202039057)

[Bonato M., et al., 2018, MNRAS, 478, 1512](http://dx.doi.org/10.1093/mnras/sty1173)
Bridle A. H., Hough D. H., Lonsdale C. J., Burns J. O., Laing R. A., 1994,

[AJ, 108, 766](http://dx.doi.org/10.1086/117112)
Chartas G., Cappi M., Hamann F., Eracleous M., Strickland S., Giustini M.,
[Misawa T., 2016, ApJ, 824, 53](http://dx.doi.org/10.3847/0004-637X/824/1/53)
[Chartas G., et al., 2020, MNRAS, 496, 598](http://dx.doi.org/10.1093/mnras/staa1534)
[Dempsey J. T., et al., 2013, MNRAS, 430, 2534](http://dx.doi.org/10.1093/mnras/stt090)
Dennett-Thorpe J., Scheuer P. A. G., Laing R. A., Bridle A. H., Pooley G. G.,
[Reich W., 2002, MNRAS, 330, 609](http://dx.doi.org/10.1046/j.1365-8711.2002.05106.x)

[Fabian A. C., Celotti A., Johnstone R. M., 2003, MNRAS, 338, L7](http://dx.doi.org/10.1046/j.1365-8711.2003.06111.x)
[Griffin M. J., et al., 2010, A&A, 518, L3](http://dx.doi.org/10.1051/0004-6361/201014519)
[Hartley P., Jackson N., Sluse D., Stacey H. R., Vives-Arias H., 2019, MNRAS,](http://dx.doi.org/10.1093/mnras/stz510)

[485, 3009](https://ui.adsabs.harvard.edu/abs/2019MNRAS.485.3009H)
[Hatziminaoglou E., et al., 2010, A&A, 518, L33](http://dx.doi.org/10.1051/0004-6361/201014679)
[Hatziminaoglou E., et al., 2015, The Messenger, 162, 24](https://ui.adsabs.harvard.edu/abs/2015Msngr.162...24H)
Hatziminaoglou E., Farrah D., Humphreys E., Manrique A., Pérez-Fournon
[I., Pitchford L. K., Salvador-Solé E., Wang L., 2018, MNRAS, 480, 4974](http://dx.doi.org/10.1093/mnras/sty2073)
[Hurley P. D., et al., 2017, MNRAS, 464, 885](http://dx.doi.org/10.1093/mnras/stw2375)
Keenan M., Meyer E. T., Georganopoulos M., Reddy K., French O. J., 2021,

[MNRAS, 505, 4726](http://dx.doi.org/10.1093/mnras/stab1182)
[Lacy M., et al., 2020, PASP, 132, 035001](http://dx.doi.org/10.1088/1538-3873/ab63eb)
[Lonsdale C. J., Barthel P. D., Miley G. K., 1993, ApJS, 87, 63](http://dx.doi.org/10.1086/191799)
[MacLeod C. L., et al., 2015, ApJ, 806, 258](http://dx.doi.org/10.1088/0004-637X/806/2/258)
[Machalski J., Jamrozy M., Stawarz Ł., Weżgowiec M., 2016, A&A, 595, A46](http://dx.doi.org/10.1051/0004-6361/201629249)
[Morgan C. W., Kochanek C. S., Morgan N. D., Falco E. E., 2006, ApJ, 647,](http://dx.doi.org/10.1086/505569)

[874](https://ui.adsabs.harvard.edu/abs/2006ApJ...647..874M)

[Ogura K., et al., 2020, PASJ, 72, 29](http://dx.doi.org/10.1093/pasj/psaa004)
[Pâris I., et al., 2018, A&A, 613, A51](http://dx.doi.org/10.1051/0004-6361/201732445)
[Plunkett A., et al., 2023, arXiv e-prints, p. arXiv:2303.02177](http://dx.doi.org/10.48550/arXiv.2303.02177)
[Rakshit S., Stalin C. S., Kotilainen J., 2020, ApJS, 249, 17](http://dx.doi.org/10.3847/1538-4365/ab99c5)
[Stacey H. R., et al., 2021, MNRAS, 500, 3667](http://dx.doi.org/10.1093/mnras/staa3433)
[Stoehr F., et al., 2022, The Messenger, 187, 25](http://dx.doi.org/10.18727/0722-6691/5267)
[Szakacs R., et al., 2021, MNRAS, 505, 4746](http://dx.doi.org/10.1093/mnras/stab1434)
Teuben P., Pound M., Mundy L., Rauch K., Friedel D., Looney L., Xu L.,
Kern J., 2015, in Taylor A. R., Rosolowsky E., eds, Astronomical Society
of the Pacific Conference Series Vol. 495, Astronomical Data Analysis
Software an Systems XXIV (ADASS XXIV). p. 305



_ALMA counterparts of SDSS quasars_ 13


Trakhtenbrot B., Lira P., Netzer H., Cicone C., Maiolino R., Shemmer O.,
[2017, ApJ, 836, 8](http://dx.doi.org/10.3847/1538-4357/836/1/8)
Turnshek D. A., Rao S., Nestor D., Lane W., Monier E., Bergeron J., Smette
[A., 2001, ApJ, 553, 288](http://dx.doi.org/10.1086/320660)
Vayner A., Wright S. A., Murray N., Armus L., Larkin J. E., Mieda E., 2017,

[ApJ, 851, 126](http://dx.doi.org/10.3847/1538-4357/aa9c42)
[Vayner A., et al., 2021a, ApJ, 919, 122](http://dx.doi.org/10.3847/1538-4357/ac0f56)
Vayner A., Zakamska N., Wright S. A., Armus L., Murray N., Walth G.,
[2021b, ApJ, 923, 59](http://dx.doi.org/10.3847/1538-4357/ac2b9e)
[Wang L., et al., 2014, MNRAS, 444, 2870](http://dx.doi.org/10.1093/mnras/stu1569)


**APPENDIX A:** **QUERYING THE ALMA ARCHIVE USING**
**ASTROQUERY**


The astroquery commands below allow for the retrieval of the
MOUS IDs that include SDSS quasar positions.

```
import astropy.units as u
from astropy import coordinates
from astropy.io import ascii
import pyvo
import pandas as pd

service = pyvo.dal.TAPService(
  "https://almascience.eso.org/tap")

# Define input dataset
fileDir = ’/your/input/directory/’
fileName = ’input_file.csv’

# Define output dataset
outfile = ’output_file.csv’

# Read in the input dataset
reader = ascii.read(fileDir+fileName, format=’basic’,

  delimiter=’,’)

# Selecting relevant parameters from the input dataset

name = reader[’SDSS’] # SDSS name

coord = coordinates.SkyCoord(ra=reader[’RAJ2000’],

             dec=reader[’DEJ2000’],

             frame=’icrs’, unit=(u.deg,
                u.deg))

# Function to query ALMA archive using coordinates and

  save as Pandas DataFrame

# Sources observed as or in the field of view of TARGET

  observations

def query_coord(service, ra, dec, radius):
  """ra, dec and radius in decimal degrees """

  query = f"""

     SELECT *

     FROM ivoa.obscore

     WHERE INTERSECTS(CIRCLE(’ICRS’,{ra},{dec},

        {radius}),

        s_region)=1

     and scan_intent like ’%TARGET%’"""

  return service.search(query).to_table().to_pandas()

# Sources observed as or in the field of view of

  calibrator observations

```

MNRAS **000**, 1–18 (2022)

14 _A. Wong et al._

```
def query_coord_cal(service, ra, dec, radius):
  """ra, dec and radius in decimal degrees """

  query = f"""

     SELECT *

     FROM ivoa.obscore

     WHERE INTERSECTS(CIRCLE(’ICRS’,{ra},{dec},

        {radius}),

        s_region)=1

     and scan_intent not like ’%TARGET%’"""

  return service.search(query).to_table().to_pandas()

# Initiate importat ALMA parameter columns to save

SDSS_ind = []

ra = []

dec = []

propIDs = []

SBs = []

bands = []

MOUSs = []

URLs = []

keys = []
sci_cats = [’Active galaxies’, ’Cosmology’,
     ’Galaxy evolution’, ’Local Universe’]

non_AGN = []

for j in range(0, len(ind), 100):
  # query 100 objects at a time to not overwhelm the

    servers.

  for i, CQ in zip(ind[j:j+100], coord[j:j+100]):
  AQ = query_coord(service, CQ.ra.degree,
    CQ.dec.degree, 0.0084)
  if len(AQ) > 0 and str(AQ[’scientific_category’][0])

    in sci_cats:

    SDSS_ind.extend([i] * len(AQ))

    ra.extend([CQ.ra.degree] * len(AQ))
    dec.extend([CQ.dec.degree] * len(AQ))
    propIDs.extend(AQ[’proposal_id’])

    SBs.extend(AQ[’schedblock_name’])

    bands.extend(AQ[’band_list’])

    MOUSs.extend(AQ[’member_ous_uid’])

    keys.extend(AQ[’scientific_category’])
    URLs.extend(AQ[’access_url’])

  if len(AQ) > 0 and str(AQ[’scientific_category’][0])

    not in sci_cats:

    non_AGN.extend([i] * len(AQ))

# Create a pandas DataFrame from the selected columns
T = pd.DataFrame({’SDSS_index’: SDSS_ind,

        ’SDSS_RA’: ra,

        ’SDSS_DEC’: dec,

        ’proposal_id’: propIDs,

        ’schedblock_name’: SBs,

        ’band_list’: bands,

        ’member_ous_uid’: MOUSs,

        ’access_url’: URLs,

        ’scientific_category’:
           keys}).drop_duplicates()

# Save the DataFrame

T.to_csv(outfile, index=False)

pd.DataFrame({’non_AGN_index’:

  non_AGN}).to_csv(’non_AGN_index.csv’, index=False)

```

MNRAS **000**, 1–18 (2022)



**APPENDIX B:** **CATALOGUES**


The tables discussed in the paper are presented in his appendix.
Table B1 contains the first 20 entries of the full catalogue of submm
detections of DR14Q quasars in the ALMA footprint. Table B2 shows
the first 21 lines of the list of DR14Q quasars in the ALMA footprint
with more than one submm counterparts extracted within 5 [′′] from
the optical coordinates of the quasar. There are cases for which more
counterparts are visible on the images than the ones identified by the
automated extraction method. The number in parenthesis next to the
SDSS name indicates, for each object, how many of those counterparts without flux measurements are visible on the image. Table B3
lists the flux of the various visually confirmed sub-structures identified on the images of and around the lensed quasars discussed in Sec.
5.2. Table B4 lists the first 20 of the DR14Q quasars in the ALMA
footprint for which no submm counterpart was extracted. Finally,
Table B5 contains the four quasars with visible submm counterparts
for which no primary-beam correction curve was available and for
which the automated extraction did not return any information. For
a description of the columns in the various catalogues see the table
captions.

_ALMA counterparts of SDSS quasars_ 15


MNRAS **000**, 1–18 (2022)

16 _A. Wong et al._


MNRAS **000**, 1–18 (2022)

_ALMA counterparts of SDSS quasars_ 17


MNRAS **000**, 1–18 (2022)

18 _A. Wong et al._


This paper has been typeset from a TEX/L [A] TEX file prepared by the author.


MNRAS **000**, 1–18 (2022)

_ALMA counterparts of SDSS quasars_ 19


**Table B4.** The first 20 lines in the catalogue of SDSS quasars that were not detected by ALMA. The columns are SDSS Name, RA and Dec; redshift ( _𝑧_ ); ALMA
band; angular resolution (Ang. res.) in [′′] ; continuum sensitivity (Sens.) in mJy, project code and MOUS ID.


SDSS Band Array Ang. res. Sens. Project code MOUS ID
Name RA Dec _𝑧_ ( [′′] ) (mJy)

00000-00000 02:30:24.47 -04:09:13.4 2.241 3 12m 1.02 0.020 2016.1.00798.S uid://A001/X87d/X741

000746.19+122223.9 00:07:46.20 +12:22:23.9 2.429 6 12m 0.49 0.014 2017.1.00478.S uid://A001/X12d1/X1ba

000826.77-050636.4 00:08:26.77 -05:06:36.5 2.172 7 7m 3.44 0.963 2016.2.00060.S uid://A001/X124a/X16e

001602.40-001225.1 00:16:02.40 -00:12:25.1 2.085 4 12m 1.68 0.011 2017.1.01558.S uid://A001/X1289/X238

002235.96+001850.0 00:22:35.96 +00:18:50.0 0.522 7 12m 0.10 0.065 2016.1.01523.S uid://A001/X87c/X293

002241.14+143112.6 00:22:41.15 +14:31:12.6 2.729 3 12m 0.08 0.014 2016.1.01231.S uid://A001/X1262/X36

6 12m 1.15 0.038 2013.1.00262.S uid://A001/X145/Xa2

3 12m 1.68 0.011 2019.1.00790.S uid://A001/X1467/X2af

4 12m 1.17 0.018 2015.1.01157.S uid://A001/X2f7/Xd5

6 12m 0.80 0.018 2015.1.01157.S uid://A001/X2f7/Xdd

002245.15+001822.5 00:22:45.15 +00:18:22.5 1.754 7 12m 0.10 0.065 2016.1.01523.S uid://A001/X87c/X293

003703.73+011707.6 00:37:03.73 +01:17:07.6 2.198 3 12m 1.76 0.028 2019.1.01257.S uid://A001/X1467/X68

3 12m 1.70 0.032 2019.1.01257.S uid://A001/X1467/X87

3 12m 1.63 0.031 2019.1.01257.S uid://A001/X1467/Xa6

3 12m 1.50 0.036 2019.1.01257.S uid://A001/X1467/Xc5

3 12m 1.47 0.037 2019.1.01257.S uid://A001/X1467/Xe4

003705.89+011611.4 00:37:05.90 +01:16:11.4 0.651 3 12m 1.76 0.028 2019.1.01257.S uid://A001/X1467/X68

3 12m 1.70 0.032 2019.1.01257.S uid://A001/X1467/X87

3 12m 1.63 0.031 2019.1.01257.S uid://A001/X1467/Xa6

3 12m 1.50 0.036 2019.1.01257.S uid://A001/X1467/Xc5


**Table** **B5.** The four objects whose images did not have a primary beam response curve and for which the automatic flux extraction did not return any flux

measurement. The columns are as in Table B4.


SDSS Band Array Ang. res. Sens. Project code MOUS ID
Name RA Dec _𝑧_ ( [′′] ) (mJy)

094932.26+033531.7 09:49:32.27 +03:35:31.8 4.107 9 12m 0.14 1.088 2012.1.00604.S uid://A002/X5ce05d/X10d

100711.80+053208.8 10:07:11.81 +05:32:09.0 2.148 9 12m 0.14 0.993 2012.1.00604.S uid://A002/X5ce05d/X10d

131341.19+144140.5 13:13:41.20 +14:41:40.6 1.897 9 12m 0.18 0.269 2013.1.00526.S uid://A001/X11e/Xf

135559.03-002413.6 13:55:59.04 -00:24:13.7 2.332 6 12m 0.45 0.064 2018.1.01817.S uid://A001/X137b/X59


MNRAS **000**, 1–18 (2022)


</paper>

## Items to check

```json
[
 {
  "path": "science.targets[9].coordinates.evidence[0]",
  "value": "11:18:16.94 +07:45:58.2",
  "failed_quote": "SDSS_J111816.94+074558.2 (PG1115_80), is a redshift 1.735 quasar observed with ALMA in band 7, where the four images are clearly visible (Stacey et al.2021)."
 },
 {
  "path": "science.targets[9].redshift_or_distance.evidence[0]",
  "value": "z = 1.735",
  "failed_quote": "SDSS_J111816.94+074558.2 (PG1115_80), is a redshift 1.735 quasar observed with ALMA in band 7, where the four images are clearly visible (Stacey et al.2021)."
 },
 {
  "path": "science.targets[9].distance_source.evidence[0]",
  "value": "SDSS DR14Q",
  "failed_quote": "SDSS_J111816.94+074558.2 (PG1115_80), is a redshift 1.735 quasar observed with ALMA in band 7, where the four images are clearly visible (Stacey et al.2021)."
 },
 {
  "path": "data.alma_project_codes[17].evidence[0]",
  "value": "2015.1.00856.S",
  "failed_quote": "ADS/JAO.ALMA#2015.1.00856.S, ADS/JAO.ALMA#2015.1.00932.S, ADS/JAO.ALMA#2015.1.01034.S"
 },
 {
  "path": "data.alma_project_codes[18].evidence[0]",
  "value": "2015.1.00932.S",
  "failed_quote": "ADS/JAO.ALMA#2015.1.00856.S, ADS/JAO.ALMA#2015.1.00932.S, ADS/JAO.ALMA#2015.1.01034.S"
 },
 {
  "path": "data.alma_project_codes[19].evidence[0]",
  "value": "2015.1.01034.S",
  "failed_quote": "ADS/JAO.ALMA#2015.1.00856.S, ADS/JAO.ALMA#2015.1.00932.S, ADS/JAO.ALMA#2015.1.01034.S"
 },
 {
  "path": "data.alma_project_codes[59].evidence[0]",
  "value": "2017.1.01527.S",
  "failed_quote": "ADS/JAO.ALMA#2017.1.01527.S, ADS/JAO.ALMA#2017.1.01559.S, ADS/JAO.ALMA#2017.1.01572.S"
 },
 {
  "path": "data.alma_project_codes[61].evidence[0]",
  "value": "2017.1.01559.S",
  "failed_quote": "ADS/JAO.ALMA#2017.1.01527.S, ADS/JAO.ALMA#2017.1.01559.S, ADS/JAO.ALMA#2017.1.01572.S"
 },
 {
  "path": "data.alma_project_codes[62].evidence[0]",
  "value": "2017.1.01572.S",
  "failed_quote": "ADS/JAO.ALMA#2017.1.01527.S, ADS/JAO.ALMA#2017.1.01559.S, ADS/JAO.ALMA#2017.1.01572.S"
 },
 {
  "path": "data.bands.evidence[1]",
  "value": "Bands 3 to 9 (mainly Bands 3, 6, and 7)",
  "failed_quote": "Most of the observations were done in bands 3, 6 and 7, with 51, 190 and 106 observations, respectively."
 },
 {
  "path": "processing.imaging.primary_beam_correction.evidence[2]",
  "value": "Initial peak search on primary-beam uncorrected images; 2D Gaussian fit and flux determination on primary-beam corrected images (or both on primary-beam corrected image when PB curve unavailable)",
  "failed_quote": "In the few cases where no primary-beam information was available for an MOUS in the ASA (this can happen for some data taken during the early ALMA observing cycles), the source finding and fitting procedures were both performed on the primary-beam corrected image available in the ASA."
 },
 {
  "path": "results_numeric[8].evidence[0]",
  "value": "Reliable detections in Band 3 = 51 dimensionless",
  "failed_quote": "Most of the observations were done in bands 3, 6 and 7, with 51, 190 and 106 observations, respectively."
 },
 {
  "path": "results_numeric[9].evidence[0]",
  "value": "Reliable detections in Band 6 = 190 dimensionless",
  "failed_quote": "Most of the observations were done in bands 3, 6 and 7, with 51, 190 and 106 observations, respectively."
 },
 {
  "path": "results_numeric[10].evidence[0]",
  "value": "Reliable detections in Band 7 = 106 dimensionless",
  "failed_quote": "Most of the observations were done in bands 3, 6 and 7, with 51, 190 and 106 observations, respectively."
 }
]
```

---
title: 'GNSS2CHORDS: A new tool for connecting UNAVCO Real-Time GNSS Data Services to CHORDS' 

tags:
  - Python
  - GNSS/GPS
  - Real-Time Data
  - UNAVCO
  - EarthCube CHORDS

authors:
  - J. Robert Jones^[corresponding author: joshj55@vt.edu]
    orcid:0000-0002-6078-4287
    affiliation: "1"
  - D. Sarah Stamps
    orcid:0000-0002-3531-1752
    affiliation: "1"
  - Michael Daniels
    orcid:0000-0003-1889-4084
    affiliation: "2"
  - Charlie Martin 
    orcid:0000-0001-5627-6266
    affiliation: "2"
  - David Mencin
    orcid:0000-0001-9984-6724
    affiliation: "3"
  - ThaoVy Nguyen
    affiliation: "1"

affiliations:
  - name: Virginia Tech, Blacksburg, VA
    index: 1
  - name: University Corporation for Atmospheric Research, Boulder, CO
    index: 2
  - name: UNAVCO, Boulder, CO
    index: 3

date: 11 January 2020

bibliograpy: paper.bib
---

# Summary

Modern instruments used in the geosciences often include the capabilities to record and stream data in real or near-real-time.  Real-time data collection can be valuable in addressing scientific questions and for developing hazard assessment approaches. In this work, we present a real-time data broker application called GNSS2CHORDS, which provides the ability to broker streaming positioning data from UNAVCO Real-Time GNSS Data Services into a CHORDS portal. The NSF EarthCube project CHORDS, Cloud HOsted Real-time Data Services for the Geosciences, is an open-source cyberinfrastructure designed so that users can easily manage and visualize streaming real-time data (Cloud-Hosted Real-time Data Services; http://chordsrt.com [@kerkez2016cloud], [@danels2016cloud]). We created the data broker application GNSS2CHORDS to access Global Navigation Satellite System (GNSS) sites streaming real-time data through UNAVCO Real-Time Data Services that uses the BKG Ntrip Client program [@sturze2016new]; and relay that data into a CHORDS portal (\autoref{fig:Figure_1_gnss2chords_workflow}). GNSS2CHORDS is designed to help remove technical barriers for scientists utilizing UNAVCO Real-Time GNSS Data Services. Linking real-time GNSS data with CHORDS increases data access through simple web services (URLs) and data services (i.e. visualization and analysis). GNSS2CHORDS also enables the application of FAIR Data Principles to real-time GNSS data. Several geoscience disciplines already integrate CHORDS into their workflows. For example, Gooch and Chandrasekar `@gooch2017integration` describe how atmospheric radar data can be streamed through CHORDS.  In this work, we utilized the [TZVOLCANO GNSS Network CHORDS portal] (http://tzvolcano.chordsrt.com) to test and validate our broker [@TZV2016]; Figure \autoref{fig:Figure_2_chords_portal}A). The most recent 3 months of data from TZVOLCANO that are parsed by GNSS2CHORDS for longitude, latitude, and height can be downloaded from the TZVOLCANO CHORDS portal [data page](http://tzvolcano.chordsrt.com/data). The data (latitude, longitude, and height) can be downloaded in both JSON (GeoJSON) and CSV (GeoCSV) file formats. The TZVOLCANO real-time GNSS data streams can also be accessed through the [UNAVCO Real-Time GNSS Data Services](https://www.unavco.org/data/gps-gnss/real-time/real-time.html) [@hodgkinson2020evaluation] in the NMEA string format. The full CHORDS code and another copy of the GNSS2CHORDS package is available through the [CHORDS GitHub repository](https://github.com/earthcubeprojects-chords/chords/tree/master/bin/gnss2chords) [@danels2016cloud].

# Statement of Need

Tectonic processes in numerous active settings have been observed to occur over a wide range of time-scales. Examples include fault rupture occurring over time periods of less than a day [@hoechner2013instant], postseismic slow-slip events that continue for several days, and volcanic reservoir inflation and deflation lasting weeks or months. Seismometers have been used for several decades to capture seismic events across the globe allowing for the development of near-real-time hazard alerts. More recently, GNSS instruments have become capable of recording 1 Hz positioning data (hereafter referred to as “real-time” data). Accessibility to real-time GNSS data allows for the development of hazard assessments using information about surface displacements, rather than seismic wave velocities, which is beneficial when seismic stations and associated seismology-based hazard assessment tools are not readily available, are saturated by large events, or are subject to long latencies.  Researchers have recognized various technical obstacles associated with the use of real-time data. As a result, scientific communities (i.e. Open Geoscience Consortium (OGC), Open Sensor Hub, Unidata) and standards (i.e. OGC Sensor Web Enablement, National Marine Electronics Association (NMEA) strings) have formed to streamline the construction of real-time data interfaces for a broad set of disciplines. Although numerous tools have been developed using the existing standards to stream and evaluate real-time data, many research groups face barriers implementing real-time data visualization, analysis, and/or hazard assessments with these tools due to the lack of resources or technical limitations [@kerkez2016cloud].

# Discussion

The application of GNSS2CHORDS for real-time GNSS data streams opens up two key functionalities: data access and data services. The workflow, shown in \autoref{fig:Figure_3_adjusted_workflow}, represents how the use of the GNSS2CHORDS package can help access a suite of data services, such as visualization and statistical analysis, and the use of community standards and best practices. GNSS2CHORDS was validated by streaming real-time GNSS data available through UNAVCO into the TZVOLCANO GNSS Network CHORDS portal, which provides a use-case for demonstrating the value of incorporating GNSS2CHORDS into a workflow. 

Regarding data access, ~3-5 cm precision positions [@leandro2011rtx] for specified time-frames provided as longitude, latitude, and height become easily downloadable through URLs or through the CHORDS GUI (\autoref{fig:Figure_2_chords_portal}B) in formats commonly used by geoscientists (i.e. GeoCSV, http://geows.ds.iris.edu/documents/GeoCSV.pdf and GeoJSON, geojson.org). For data services, CHORDS connects with the open-source platform Grafana via InFluxDB. Grafana provides tools for automated data analysis and functions such as issuing user-defined alerts when data meet a certain criteria and visualization of the data streams at 5-second intervals.  In addition, implementing GNSS2CHORDS in a real-time GNSS workflow helps users align their data streams with FAIR Data Principles [@wilkinson2016fair]. FAIR data is findable, accessible, interoperable, and reusable. GNSS2CHORDS provides a mechanism to make positioning data publicly accessible. Anyone with internet access has the ability to view and download positioning data provided by GNSS2CHORDS. Given the simplicity of the positioning data (latitude, longitude, and height), the data can be compared with other streaming datasets, such as gas measurements, which would increase interoperability and reusability. The successful deployment and integration of a CHORDS portal with UNAVCO’s Real-Time Data Services through the implementation of GNSS2CHORDS provides a utility for the GNSS workflow offering simple adjustments, standards-based outputs, and iterative analysis capabilities via Grafana. Creating GNSS2CHORDS and similar programs may spur innovation in the geosciences pushing the development of more uses of real-time data and open data capabilities.

# Acknowledgements

This work was funded by the National Science Foundation EarthCube program under grants 1639554 and 1639750. Additional funding was provided through National Geographic Society Grant CP-037R-17 for the installation of GNSS stations at the TZVOLCANO GNSS Network. This material is also based on services provided by the GAGE Facility, operated by UNAVCO, Inc., with support from the National Science Foundation and the National Aeronautics and Space Administration under NSF Cooperative Agreement EAR-1724794. We thank the EarthCube community for early feedback on preliminary work. We also thank Nathan Hook from the University Consortium of Atmospheric Research (UCAR) Computational and Information System Lab (CISL).

# Figures

![Figure 1. The workflow of the data broker application designed to connect UNAVCO Real-Time data services to an active CHORDS Portal. Presented in a format of a three tier architecture consisting of private data tier (not accessible to users), processing tier (can be edited by user), and the public tier (visible and accessible by user’s audience). The data broker application begins with the user editing the parameter file and initializing the application. Following the red arrows first, the data broker application moves into the private or UNAVCO tier accessing the real-time data services. Next, following the green arrows the data is continuously streamed through the Ntrip Client and into the CHORDS Portal.  \label{fig:Figure_1_gnss2chords_workflow}](figure_1_gnss2chords_workflow.png)

![Figure 2. The TZVOLCANO GNSS Network CHORDS portal Dashboard (A) and Data Functions interface (B).  A: (1) Number of measurements or data points temporarily stored in the CHORDS Portal. (2) Number of instruments currently set up to stream data. (3) Number of sites (important when multiple instruments are set up in one location). (4) Amount of storage space used in the online Portal instance. (5) Date when data will be deleted. (6) Time since the last software update. (7) Red dots represent sites currently not streaming and green dots represent sites that are actively streaming data. (8) Number of samples per minute in bar graph format. (9) Number of samples per hour in bar graph format. (10) Samples per day in bar graph format. Each color in 8-10 corresponds with a distinct instrument.  B: Data Functions interface that allows for direct file download. Data URL format structures are also found through this interface. \label{fig:Figure_2_chords_portal}](figure_2_chords_portal.png)

![ Figure 3. A representation of two different workflows for real-time GNSS data streaming through UNAVCO Real-time GNSS Data Services. The green arrow represents the processes executed in GNSS2CHORDS as explained in the methods section. (A) A typical workflow that does not utilize GNSS2CHORDS. In this case, institutions are responsible for all data analysis, visualization, and hazard assessment. (B) A revised workflow that employs GNSS2CHORDS such that a CHORDS portal can be utilized for data analysis, visualization, and automated hazard assessment. \label{fig:Figure_3_adjusted_workflow}](figure_3_adjusted_workflow.png)


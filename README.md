# InSight Seismic Data Downloader

[![DOI](https://zenodo.org/badge/362388409.svg)](https://zenodo.org/badge/latestdoi/362388409)

This repository contains scripts for InSight seismic data download and processing. The scripts download the VBB SEIS instrument data for the seismic events that are listed in the Marsquake Catalog. The scripts are developed by the University of Maryland InSight group, whereas the instrument and marsquake events information are provided by working groups of the InSight team and should be cited appropriately, according to the information provided below.

## Contributors
Foivos Karakostas, Doyeon Kim, Ross Maguire, Aisha Khatib, Quancheng Huang, Angela Marusiak, Nicholas Schmerr, Ved Lekić - the University of Maryland, College Park, InSight group

## Dependencies

In order to use this suite, a python3 installation in your system is necessary, as well as the [ObsPy](https://github.com/obspy/obspy/wiki) open sourced framework. Please acknowledge and cite the ObsPy references accordingly.

## Contents

This repository contains:

1. The 12th version of the Marsquakes Catalog. Citation: InSight Marsquake Service (2022). Use the link for the download and cite accordingly.
2. The ELYSE station dataless file. Citation: InSight MARS SEIS Data Service (2019). Use the link for the download and cite accordingly.
3. The python script **make_seismic_catalog.py** that creates the text file of the catalog, needed for the event data downloaders.
4. The python script **eventdownloader.py**, which is used for downloading and processing of a unique event data.
5. The python script **massivedownloader.py**, which is used for downloading and processing of events' data of a specific event Type and Quality (see Clinton et al., 2021 for details).

## How to use

**make_seismic_catalog.py**: Just run the script and the SeismicCatalog text file will be generated.

**eventdownloader.py**: When asked to input the event, write the full event name. For example, to download the S1222a event, write *S1222a*.

**massivedownloader.py**: When asked to input the Quality, write *A, B, C, or D*. When asked to input the Class, write the name of the class in the way that it is written in the SeismicCatalog text file, which means *LOW_FREQUENCY, BROADBAND, 2.4_HZ, HIGH_FREQUENCY, and VERY_HIGH_FREQUENCY*. For example, to download the A quality BROADBAND events, write *A* for the Quality input, and *BROADBAND* for the Class input.

## Output files

The output files of the suite are saved in a directory that has the following format in your system: **DATA/Event_Type/Event_Quality/Event_Name/**. There are 4 mseed files:

* The raw data mseed file, named **Event_Name.mseed**
* The event data with instrument response removal, rotation to Z, N, E and the application of a Tukey window filter, with the 5% of the timeseries within the sinusoidal function, named **Event_Name_DISP.mseed** for displacement, **Event_Name_VEL.mseed** for velocity and **Event_Name_ACC.mseed** for acceleration.

The Event_Name is given in the Marsquake Catalog and is defined by an alphanumeric digit for the type of the Event (S for seismic events), 4 digits for the Sol (Martian Day of InSight operations) and one alphanumeric digit for the order of the event within the indicated sol.

The Event_Type and the Event_Quality are the Type and Quality of the event respectively, as defined by Clinton et al., 2021.

## Citations and acknowledgements

The scripts of this repository download Mars InSight seismic data from IRIS. It is developped by Foivos Karakostas, Doeyeon Kim, Ross Maguire, Aisha Khatib, Quancheng Huang, Angela Marusiak, Nicholas Schmerr, Ved Lekić and the University of Maryland InSight group. Please acknowledge.

When you use InSight SEIS Data, please follow the [citation instructions](https://www.seis-insight.eu/en/science/seis-data/seis-citation-information) that are also copied here:

*SEIS data must be cited as reference in the following way:*

*Citation in text :*

*InSight Mars SEIS Data Service. (2019). SEIS raw data, Insight Mission. IPGP, JPL, CNES, ETHZ, ICL, MPS, ISAE-Supaero, LPG, MFSC. https://doi.org/10.18715/SEIS.INSIGHT.XB_2016*

*In addition an acknowledgement must also be provided to the SEIS operators as follows:*

*"We acknowledge NASA, CNES, their partner agencies and Institutions (UKSA, SSO, DLR, JPL, IPGP-CNRS, ETHZ, IC, MPS-MPG) and the flight operations team at JPL, SISMOC, MSDS, IRIS-DMC and PDS for providing SEED SEIS data."*

*Furthermore, the SEIS experiment paper (Lognonné et al., 2019) must be used as reference for describing the instrument, in addition to the SEIS team papers used by the user for the analysis. For a collection of SEIS papers, see Banerdt and Russel, 2017 and Banerdt and Russel, 2019.*

## References

1. Clinton, J. F., Ceylan, S., van Driel, M., Giardini, D., Stähler, S. C., Böse, M., … Stott, A. E. (2021). The Marsquake catalogue from InSight, sols 0–478. Physics of the Earth and Planetary Interiors, 310, 106595. https://doi:10.1016/j.pepi.2020.106595
2. InSight Mars SEIS Data Service. (2019). SEIS raw data, Insight Mission. IPGP, JPL, CNES, ETHZ, ICL, MPS, ISAE-Supaero, LPG, MFSC. https://doi.org/10.18715/SEIS.INSIGHT.XB_2016
3. InSight Marsquake Service (2022). Mars Seismic Catalogue, InSight Mission; V12 2022-10-01. ETHZ, IPGP, JPL, ICL, MPS, Univ. Bristol. https://doi.org/10.12686/a18
4. Lognonné, P., Banerdt, W.B., Giardini, D. et al. (2019). SEIS: Insight’s Seismic Experiment for Internal Structure of Mars. Space Sci Rev 215, 12. https://doi.org/10.1007/s11214-018-0574-6
 

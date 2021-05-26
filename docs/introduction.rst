.. _introduction:

Introduction
============

Overview
++++++++++++

There is a strong dual trend in scientific research which sees increasing 
prevalence of **data commons** environments and **adoption of FAIR principles**
to facilitate finding scientific data, promote collaboration, and ultimately 
enable new scientific discoveries.  This document provides a coarse overview of 
data commons and FAIR principles, an impetus for why RTI is investigating these 
concepts (and thus impetus for creation for this guide), and finally walks 
through implementation and use of a Gen3 data commons and FAIR tooling 
step-by-step.

What are Data Commons?
++++++++++++++++++++++

Data Commons are software platforms that collocate data, cloud-based 
computing infrastructure, and commonly-used software applications, tools, and 
services to create a resources for securely managing, analyzing, integrating, 
and sharing data with a research community while protecting privacy. [1]_   Gen3 
is a popular example of a data commons platform used by many institutions to 
create their own data commons.  `NHLBI BioData Catalyst <https://gen3.biodatacatalyst.nhlbi.nih.gov/>`_, 
`NHGRI AnVIL <https://gen3.theanvil.io/>`_, `Gabriella Miller Kids First <https://data.kidsfirstdrc.org/login>`_, 
and `NIH Cancer Research Data Commons (CRDC) <https://nci-crdc.datacommons.io/>`_ are all examples of Gen3 
implementations.

What is FAIR?
+++++++++++++
**FAIR** stands for Findable, Accessible, Interoperable, and Repeatable.  It is
a set of principles for data to which researchers and institutions *should* adhere 
to maximize the value of their data assets. [2]_   FAIR tools are 
pplications or systems which attempt to assess FAIR-ness of data assets.  
The goal of applying FAIR tools to data assets is to assess the FAIRness of 
data and subsequently make any necessary changes to better adhere to FAIR 
principles.


Why Investigate Data Commons & FAIR Tools?
++++++++++++++++++++++++++++++++++++++++++
It is of critical importance for RTI competency in Data Commons and FAIR tools 
for 2 primary reasons:

**1. Improve RTI Competency in data commons implementation with current clients.**  Current 
RTI RCD clients (e.g. BioData Catalyst, NIH HEAL) are using data commons
built on Gen3.  RTI does not have the experience to assist with implementation 
and technical challenges; this creates a dependence upon the Gen3 team and has 
become a bottleneck of success for these clients.

**2. Strategically position RTI for future opportunities.**  Funding institutions 
and federal guidelines encourage or require elements of 
FAIR and practices that are enabled by a data commons architecture.  
See the `NIH Strategic Plan for Data 
Science (2018) <https://datascience.nih.gov/sites/default/files/NIH_Strategic_Plan_for_Data_Science_Final_508.pdf>`_ 
and the `Federal Data Strategy Framework (2020) <https://strategy.data.gov/assets/docs/2020-federal-data-strategy-framework.pdf>`_.

Thus, the creation of this guide is an attempt to fill the gap in RTI's
technical competency in data commons and FAIR tools to strategically position 
ourselves for current and future work within these domains.

Audience and Purpose of this Guide
++++++++++++++++++++++++++++++++++

This guide is intended for a computer-savvy user with minimal DevOps experience 
and some familiarity with the Cloud.  The goal of this guide is to stand up a 
Gen3 implementation, understand critical workflows in Gen3, execute those 
workflows, work with data within the context of Gen3, and evaluate the FAIRness 
of the data assets with FAIR tools.  In essence, this is a guidebook for quickly 
building a Gen3 sandbox environment, which may be critical in future RTI endeavors 
that require hands-on implementation experience with data commons environments.

References
++++++++++

.. [1] Robert L. Grossman, Data Lakes, Clouds, and Commons: 
   A Review of Platforms for Analyzing and Sharing Genomic Data, 
   Trends in Genetics 35, 2019, pages 223-234. PMID: 30691868 PMCID: PMC6474403

.. [2] Wilkinson, M., Dumontier, M., Aalbersberg, I. et al. 
   The FAIR Guiding Principles for scientific data management and stewardship. 
   Sci Data 3, 160018 (2016).


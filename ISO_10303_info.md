# Information on the ISO 10303 STEP standard

## Overview

-   Wikipedia: https://en.wikipedia.org/wiki/ISO_10303
    -   ISO 10303 (Automation systems and integration — Product data
        representation and exchange) is a family of ISO standards for
        computer-interpretable representation (description) and exchange of
        product manufacturing information (PMI). It aims to provide
        interoperability between various computer-aided design (CAD) software,
        assist with automation in computer-aided manufacturing (CAM), and
        allows long-term archival of 3D, CAD and PDM data. It is known
        informally as "STEP", which stands for "Standard for the Exchange of
        Product model data". Due to a large scope ISO 10303 is subdivided into
        approximately 700 underlying standards total.

-   Like other ISO and IEC standards, STEP is copyright by ISO and is not
    freely available. However, the 10303 EXPRESS schemas are freely available,
    as are the recommended practices for implementers.

-   Relevant ISO 10303 parts: https://en.wikipedia.org/wiki/List_of_STEP_(ISO_10303)_parts
    -   Part 1 Overview and fundamental principles
    -   Part 2 Vocabulary
    -   Parts 11 to 19 : Description methods: EXPRESS, EXPRESS-X
        -   **Part 11 - EXPRESS language reference manual**
        -   Part 12 - EXPRESS -I language reference manual (withdrawn)
        -   Part 14 - EXPRESS -X language reference manual
        -   Part 15 - SysML XMI to XSD transformation
    -   Parts 21 to 29 : Implementation methods: STEP-File, STEP-XML, SDAI, C/C++/Java language bindings interfaces,
        -   **Part 21 - STEP-File Clear text encoding of the exchange structure**
        -   Part 22 - SDAI Standard data access interface specification
        -   Part 23 - C++ language binding of the standard data access interface
        -   Part 24 - C language binding of the standard data access interface
        -   Part 25 - EXPRESS to OMG XMI binding
        -   Part 26 - Binary representation of EXPRESS-driven data using HDF5
        -   Part 27 - Java TM programming language binding to the standard data access interface with Internet/Intranet extensions
        -   **Part 28 - STEP-XML XML representation for EXPRESS-driven data**
    -   Parts 201 to 299 : Application protocols (AP)
        -   **Part 210 - Electronic assembly, interconnect and packaging design. The most complex and sophisticated STEP AP.**
        -   Part 212 - Electrotechnical design and installation. Designed as a complement for AP214, but not fully harmonized with it.
        -   Part 214 - Core data for automotive mechanical design processes
        -   Part 221 - Functional data and their schematic representation for process plant
        -   Part 224 - Mechanical product definition for process plans using machining features
        -   Part 232 - Technical data packaging core information and exchange
        -   Part 233 - Systems engineering
        -   **Part 239 - Product life cycle support**
        -   **Part 242 - Managed model-based 3D engineering**: https://www.iso.org/standard/84300.html
    -   Part 400 : Reference schema for SysML mapping
    -   Parts 401 to 499 : Application protocol modules (Implementation modules for APs)
    -   Part 4000 : Core model
    -   Parts 4401 to 4499 : Domain models

-   Notable Application Protocols include:
    -   AP 238 (STEP-NC) — an underlying standard for CAD-model based CAM and automated CNC machining.
    -   AP 203 and AP 242 — a standard for CAD related data models for CAD data exchange.
    -   AP 242 was created by merging the following two Application protocols:
        -   AP 203, Configuration controlled 3D designs of mechanical parts and assemblies (as used by the Aerospace Industry).
        -   AP 214, Core data for automotive mechanical design processes (used by the Automotive Industry).
    -   Two APs had been modified to be directly based on AP 242, and thus became supersets of it:
        -   AP 209, Composite and metallic structural analysis and related design
        -   AP 210, Electronic assembly, interconnect and packaging design. This is the most complex and sophisticated STEP AP.
    -   AP 242 edition 2, published in April 2020, extends edition 1 domain by
        the description of Electrical Wire Harnesses and introduces an
        extension of STEP modelisation and implementation methods based on
        [SysML](#sysml-systems-modeling-language) and system engineering with
        an optimized XML implementation method.

-   For complex areas more than one APs are needed to cover all major aspects:
    -   AP 212 and 242 for electro-mechanical products such as a car or a
        transformer. This will be addressed by the second edition of AP 242
        that is currently under development
    -   AP 242, 209 and 210 for electro/electronic-mechanical products

-   EXPRESS data modeling language:
    -   Wikipedia: https://en.wikipedia.org/wiki/EXPRESS_(data_modeling_language)
    -   EXPRESS Language Foundation: https://www.expresslang.org/
        -   EXPRESS grammar in BNF form: https://www.expresslang.org/references/
            -   ISO 10303-11:2004 BNF (raw)
            -   ISO 10303-11:2004 BNF
            -   ISO 10303-14 BNF (raw)
            -   ISO 10303-14 BNF
            -   ISO 10303-21:1994 BNF
            -   ISO 10303-21:2002 BNF
            -   ISO 10303 patch schema BNF

-   ISO 10303-21 STEP file: https://en.wikipedia.org/wiki/ISO_10303-21
    > STEP-file is a widely used data exchange form of STEP. ISO 10303 can
    > represent 3D objects in computer-aided design (CAD) and related
    > information. A STEP-file is ASCII text with the format defined in ISO
    > 10303-21 Clear Text Encoding of the Exchange Structure.
    -   Possibly the only advantage of STEP files is that they are widely adopted
        in many CAD software. On the other hand, its format, and specially the
        EXPRESS data modelling language has a few disadvantages
        -   The specification is not freely available (you have to pay for it)
        -   The format is not well-defined. For example the same triangle can be
            encoded in a STEP file in many different ways (with FACET_BREP,
            ADVANCED_FACE, POLY_LOOP, EDGE_LOOP, as a
            MANIFOLD_SOLID_REPRESENTATION or as a SHELL_BASED_REPRESENTATION,
            etc.). An importer needs to recognize all variants in order to read a
            STEP file consistently. Most CAD software does not support the full
            set of STEP entries, and as such, are limited to a specific subset of
            STEP entities. For example Autodesk Help, list of supported STEP
            entities.
        -   As a result, most CAD software have some sort of "repair geometry data
            after import" feature, which may or may not work.

### ISO 10303-28 STEP-XML

-   ISO 10303-28 STEP-XML: https://en.wikipedia.org/wiki/ISO_10303-28
    >   STEP-XML specifies the use of the Extensible Markup Language (XML)
    >   to represent EXPRESS schema (ISO 10303-11) and the data that is
    >   governed by those EXPRESS schema. It is an alternative method to
    >   STEP-File for the exchange of data according to ISO 10303.

-   STEP/EXPRESS and XML: https://xml.coverpages.org/stepExpressXML.html
    >   Last modified: March 29, 2002

---

## Tools

### Software

#### STEP AP242 Project

-   Website: https://www.ap242.org/
    >   The goal of this web site is to ensure the communication and awareness
    >   related to the common development and the primary use by the
    >   automotive and aerospace industries of the AP242 standard.


#### STEP Viewers

-   Website: https://www.mbx-if.org/home/mbx/resources/
    | Vendor                   | Viewer                        | URL                                 | License                        |
    |--------------------------|-------------------------------|-------------------------------------|-------------------------------|
    | Actify                   | SpinFire                      | www.actify.com                      | paid license, free trial      |
    | Autodesk                 | Viewer                        | viewer.autodesk.com                 | online; free registration     |
    | C3D Labs                 | C3D Viewer                    | www.c3dlabs.com                     | free and paid license         |
    | CADCAM-e                 | EnSuite-View                  | www.cadcam-e.com                    | free license                  |
    | CADEX                    | CAD Exchanger                 | www.cadexchanger.com                | paid license, free trial      |
    | CadSoftTools             | ABViewer                      | www.cadsofttools.com                | paid license, free trial      |
    | Capvidia                 | MBDvidia                      | www.capvidia.com                    | paid license, free trial      |
    | Clari3D                  | Clari3D                       | www.clari3d.com                     | paid license, free trial      |
    | CT CoreTechnologie       | 3D_Analyzer                   | www.coretechnologie.de              | paid license                  |
    | Dassault Systèmes        | 3DEXPERIENCE 3DPlay           | www.3ds.com                         | paid license                  |
    | Dassault Systèmes        | SOLIDWORKS eDrawings          | www.solidworks.com                  | free license                  |
    | Elysium                  | 3D-SUITE                      | www.elysium-global.com              | paid license                  |
    | Fougue Ltd.              | Mayo                          | www.github.com                      | Open Source                   |
    | FreeCAD Team             | FreeCAD                       | www.freecadweb.org                  | free license (LGPL/CC)        |
    | Glovius                  | Glovius Viewer                | www.glovius.com                     | paid license, free trial      |
    | Jotne                    | EDMopenSimDM (AP209 Ed2)      | www.jotneit.no                      | paid license                  |
    | Kisters                  | 3DViewStation                 | viewer.kisters.de                   | paid license, free trial      |
    | Kubotek Kosmos           | View / Convert                | www.kubotekkosmos.com               | paid license, free trial      |
    | LKSoft                   | IDA-STEP                      | www.ida-step.net                    | free and paid license         |
    | Machine Research         | STEP Viewer                   | www.machineresearch.com             | paid license, free trial      |
    | NIST                     | STEP File Analyzer and Viewer | www.nist.gov                        | free license                  |
    | OpenCascade              | CAD Assistant                 | www.opencascade.com                 | free license                  |
    | Open Design Alliance     | Open STEP Viewer              | openstepviewer.com                  | free license                  |
    | RDF                      | STEP Viewer                   | rdf.bg                              | free license                  |
    | Siemens PLM              | TC Visualization              | www.plm.automation.siemens.com      | free and paid license         |
    | SolidView                | STEP Viewer                   | www.solidview.com                   | paid license, free trial      |
    | Theorem Solutions        | CAD Viewer                    | www.theorem.co.uk                   | paid license                  |
    | Threedy                  | instant3Dhub                  | www.threedy.io                      | paid license                  |
    | TransMagic               | SuperView – 3D CAD Viewer     | www.transmagic.com                  | paid license, free trial      |
    | VariCAD                  | VariCAD Viewer                | www.varicad.com                     | free and paid licenses        |
    | Virtual Systems Engineering | PREVIEW Viewer             | www.virtualsystemsengineering.com   | paid license, free trial      |
    | ZWSOFT                   | CADbro                        | www.cadbrother.com                  | paid license, free trial      |
    | 3DTool                   | 3DTool                        | www.3d-tool.com                     | paid license                  |

---

#### STEP Tools, Inc.

>   Our mission is to make US manufacturing 15% more efficient. We do so
>   by connecting manufacturing machines to simulation servers that enable
>   real time analysis and correction of machining results.

-   Webpage: https://www.steptools.com/
    >   STEP, the Standard for the Exchange of Product Model Data, is a
    >   comprehensive ISO standard (ISO 10303) that describes how to represent
    >   and exchange digital product information.
-   Standards: https://www.steptools.com/stds/step/
    >   AP242: Managed Model-Based 3D Engineering. STEP AP242 replaces AP203e2
    >   and AP214 for CAD data. It was published in 2014 as ISO
    >   10303-242:2014(E). A second edition is under development with new
    >   geometric capabilities and additive manufacturing setup information.
-   Software: https://www.steptools.com/support/
    -   STEP Python Interface for Digital Twin Manufacturing:
        https://www.steptools.com/docs/stpython/
        -   STEP and STEP-NC (ISO 10303) native extension for large CAD/CAM/CAE
            models and machine tool interfaces: https://pypi.org/project/steptools/
    -   JSON From STEP-NC: https://www.steptools.com/docs/stpython/example/make_json/
    -   AP238.org: https://ap238.org/
        >   STEP neutral data standard for CAD data
    -   STEP Tools Utility Reference: https://www.steptools.com/docs/devtools/index.html
        -   AP203, AP209 and AP214 Conformance Checkers: https://www.steptools.com/docs/devtools/ap2xxcheck.html
        -   General STEP Conformance Checker: https://www.steptools.com/docs/devtools/apconform.html
        -   STEP Part 21 File Browser: https://www.steptools.com/docs/devtools/stepbrws.html
        -   STEP Part 28 XML Browser: https://www.steptools.com/docs/devtools/p28view.html
-   Integrated generic resource: Geometric and topological representation:
    https://www.steptools.com/stds/smrl/data/resource_docs/geometric_and_topological_representation/sys/6_schema.htm
-   ISO 10303-21: https://www.steptools.com/stds/step/IS_final_p21e3.html
    >   Part 21: Implementation methods: Clear text encoding of the exchange structure

---

#### Stepcode

>   STEPcode reads ISO-10303-11 EXPRESS schemas and generates C++ source code that
>   can read and write Part 21 files conforming to that schema. In addition to
>   C++, SC includes experimental support for Python.

-   GitHub: https://github.com/stepcode/stepcode
-   Doc: https://stepcode.github.io/
    -   exp2python: generates Python code. Formerly fedex_python.
        https://stepcode.github.io/docs/executables/#exp2python


#### NIST STEP to OWL Translator

-   STP2OWL: https://github.com/usnistgov/stp2owl
    >   The NIST STEP to OWL Translator (STP2OWL) is an open-source software,
    >   and an improved implementation of OntoSTEP. STP2OWL translates STEP
    >   schemas (EXPRESS) and instance files (P21) into Web Ontology Language
    >   (OWL) files in a faster and more flexible way, thus furthering the
    >   adoption of the full capabilities of ISO 10303. Developed at the
    >   National Institute of Standards and Technology (NIST), the software is
    >   based on the STEPcode and written in C++.
    -   A windows executable and required DLLs to run the software:
        https://github.com/usnistgov/STP2OWL/releases/tag/v1.0

#### Fougue Mayo

-   GitHUb: https://github.com/fougue/mayo
    >   Open source 3D CAD viewer and converter
    -   Supported formats: https://github.com/fougue/mayo/wiki/Supported-formats
        | Format      | Import | Export | Notes                                                                                   |
        |-------------|:------:|:------:|-----------------------------------------------------------------------------------------|
        | STEP        |   ✔    |   ✔    | AP203, 214, 242 (some parts)                                                           |
        | IGES        |   ✔    |   ✔    | v5.3                                                                                   |
        | BREP        |   ✔    |   ✔    | OpenCascade native format                                                              |
        | DXF         |   ✔    |   ❌   |                                                                                        |
        | OBJ         |   ✔    |   ✔    | Import: OpenCascade ≥ v7.4.0<br>Export: OpenCascade ≥ v7.6.0                           |
        | glTF        |   ✔    |   ✔    | Supports 1.0, 2.0, GLB<br>Import: OpenCascade ≥ v7.4.0<br>Export: OpenCascade ≥ v7.5.0 |
        | VRML        |   ✔    |   ✔    | v2.0 UTF8<br>Import: OpenCascade ≥ v7.7.0                                              |
        | STL         |   ✔    |   ✔    | ASCII/binary                                                                           |
        | PLY         |   ✔    |   ✔    | ASCII/binary (little and big endian)<br>Colors and point clouds supported              |
        | OFF         |   ✔    |   ✔    | Vertex colors supported                                                                |
        | AMF         |   ✔    |   ✔    | Import: Assimp library<br>Export: gmio ≥ v0.4.0<br>Export format: v1.2 Text/ZIP        |
        | 3MF         |   ✔    |   ❌   | Requires Assimp library                                                                |
        | 3DS         |   ✔    |   ❌   | Requires Assimp library                                                                |
        | FBX         |   ✔    |   ❌   | Animations not supported<br>Requires Assimp library                                    |
        | Collada     |   ✔    |   ❌   | Requires Assimp library                                                                |
        | X3D         |   ✔    |   ❌   | Requires Assimp library                                                                |
        | X (DirectX) |   ✔    |   ❌   | Animations not supported<br>Requires Assimp library                                    |
        | Image       |   ❌   |   ✔    | PNG, JPEG, BMP, GIF, ...                                                               |


#### Nara STEP File Browser

-   nara-stepbrowser: https://github.com/fdesjardins/nara-stepbrowser
    >   A simple file browser for navigating the relationships between ISO
    >   10303 (STEP) files.


#### IFC Parser

-   IFC Parser: https://github.com/gsimon75/IFC_parser
    >   A full python parser for ISO 10303-11 / EXPRESS schemas and IFC files

#### NIST STEP File Analyzer and Viewer

-   STEP File Analyzer and Viewer: https://www.nist.gov/services-resources/software/step-file-analyzer-and-viewer
    >   Last Updated 09/10/2025
    >
    >   All commonly used STEP file formats, also known as Application Protocols (AP), are supported.
    -   Download: https://www.nist.gov/system/files/documents/noindex/2025/09/10/SFA-5.33.zip

#### NIST easyEXPRESS

-   easyEXPRESS: https://marketplace.visualstudio.com/items?itemName=usnistgov.easyEXPRESS
    >   easyEXPRESS is a Visual Studio Code extension that aims at providing
    >   advanced editing capabilities to EXPRESS developers and help them
    >   efficiently write valid EXPRESS information models.

#### NEST STEP to X3D Translator

-   STEP to X3D Translator: https://www.nist.gov/services-resources/software/step-x3d-translator
    >   The NIST STEP to X3D Translator (STP2X3D) is an open-source software
    >   that translates a STEP (ISO 10303) Part 21 file (.stp or .step) to an
    >   X3D (ISO/IEC 19776) file (.x3d) or X3DOM file (.html). X3DOM files can
    >   be displayed in a web browser.
-   GitHub: https://github.com/usnistgov/STP2X3D
    >   The NIST STEP to X3D Translator is an open-source software that
    >   translates a STEP (ISO 10303) Part 21 file (.stp or .step) to an X3D
    >   (ISO/IEC 19776) file (.x3d) or X3DOM file (.html). Developed at the
    >   National Institute of Standards and Technology (NIST), the software is
    >   based on the Open CASCADE STEP Processor and written in C++.
    -   Release: https://github.com/usnistgov/STP2X3D/releases/tag/v1.50

---

## Download sources

-   ISO Online Browsing Platform: https://www.iso.org/obp/ui/en/#iso:std:iso:10303:-1:ed-3:v1:en
    >   Only informative sections of standards are publicly available. To view
    >   the full content, you will need to purchase the standard.

### ISO Standards Maintenance Portal

-   STEP Parts List: https://standards.iso.org/iso/10303/STEP_Parts_List.htm
-   home iso 10303 smrl v11 tech: https://standards.iso.org/iso/10303/smrl/v11/tech/
    -    [smrlv11.zip](https://standards.iso.org/iso/10303/smrl/v11/tech/smrlv11.zip)

#### ISO 10303-15

-   home > iso > ts 10303 > -15 > ed-2 > en: https://standards.iso.org/iso/ts/10303/-15/ed-2/en/
 	-   ISO_CD TS 10303-15 ed.2 - id.86075 Approval Canonical_xmi_example_input.xmi
	-   ISO_CD TS 10303-15 ed.2 - id.86075 Approval Schematron_example_output.sch
	-   ISO_CD TS 10303-15 ed.2 - id.86075 Approval XSD_example_output.xsd
-   Approval XSD_example_output: https://standards.iso.org/iso/ts/10303/-15/ed-2/en/ISO_CD%20TS%2010303-15%20ed.2%20-%20id.86075%20Approval%20XSD_example_output.xsd



## Other links

-   http://cvs.boost-lab.net/sphinx/STEPlib_User_Guide/html/pages/howto/howtoReferenceData.html
-   http://cvs.boost-lab.net/sphinx/STEPlib_User_Guide/html/pages/howto/howtoScriptOWL.html
-   https://www.nist.gov/publications/process-specification-language-psl-overview-and-version-10-specification
-   https://www.nist.gov/pml/special-publication-330
-   https://www.nist.gov/ctl/smart-connected-systems-division/smart-connected-manufacturing-systems-group/step-nist/step-1

### Library of Congress Collections

-   STEP-file, ISO 10303-21: https://www.loc.gov/preservation/digital/formats/fdd/fdd000448.shtml
    >   **Relationship between ISO 10303-21 and ISO 10303-11**: The EXPRESS data
    >   modeling language (specified in ISO 10303-11) is used to define
    >   schemas, and constraints on the entities in those schemas, to
    >   represent the data model for the design and characteristics of a
    >   "product." A product might be a single component or an entire building
    >   structure. Given an EXPRESS model for a product, ISO 10303-21 defines
    >   an encoding and file format (the plain text STEP-file) for an instance
    >   conforming to that model. The instance is known as an "exchange
    >   structure."

### SysML: Systems modeling language

-   Wikipedia: https://en.wikipedia.org/wiki/Systems_modeling_language
    >   SysML models are designed to be exchanged using the XML Metadata
    >   Interchange (XMI) standard. Architectural alignment work is underway
    >   to support the ISO 10303 (also known as STEP, the Standard for the
    >   Exchange of Product model data) AP-233 standard for exchanging and
    >   sharing information between systems engineering software applications
    >   and tools.

### ISO 15926

-   ISO 15926-4: https://www.iso.org/obp/ui/en/#iso:std:iso:ts:15926:-4:ed-3:v1:en
    >   ISO/TS 15926-4:2024(en) Industrial automation systems and integration
    >   — Integration of life-cycle data for process plants including oil and
    >   gas production facilities — Part 4: Core reference data

---
title: 'Soundata: Python library for reproducible usage of sound datasets'
tags:
  - python
  - audio
  - dataset
  - environmental-sound
authors:
  - name: Magdalena Fuentes
    orcid: 0000-0003-4506-6639
    affiliation: 1, *
  - name: Justin Salamon
    orcid: 
    affiliation: 2, *
  - name: Pablo Zinemanas
    orcid: 
    affiliation: 3
  - name: Martín Rocamora
    orcid: 
    affiliation: 4
  - name: Genís Plaja
    orcid: 
    affiliation: 3
  - name: Irán Román
    orcid: 
    affiliation: 1
  - name: Rachel Bittner
    orcid: 
    affiliation: 5
  - name: Xavier Serra
    orcid: 
    affiliation: 3
  - name: Juan Pablo Bello
    orcid: 
    affiliation: 1
affiliations:
 - name: equal contribution
   index: *
 - name: MARL, New York University
   index: 1
 - name: Adobe Research
   index: 2
 - name: MTG, Universitat Pompeu Fabra
   index: 3
 - name: GPA, Universidad de la República
   index: 4
 - name: Spotify
   index: 5
date: 14 September 2021
bibliography: paper.bib
---

# Summary

Soundata is a Python library for loading and working with audio datasets in a standarized way, removing the need for writing custom loaders in every project, and improving reproducibility by providing tools validate data against a canonical version. It speeds up research pipelines by allowing you to quickly download a dataset, load it into memory in a standarized and reproducible way, validate that the dataset is complete and correct, and more.

Soundata is based and inspired on mirdata [@bittner_fuentes_2019_mirdata], and was created following these desig principles:

- Easy to use: Soundata is designed to be easy to use and to simplify the research pipeline considerably. Check out the examples in the Getting started page.

- Easy to contribute to: we welcome and encourage contributions, especially new datasets. You can contribute following the instructions in our Contributing page.

- Increase reproducibility: by providing a common framework for researchers to compare and validate their data, when mistakes are found in annotations or audio versions change, using Soundata the audio community can fix mistakes while still being able to compare methods moving forward.

- Standarize usage of sound datasets: we standarize common attributes of sound datasets such as audio or tags to simplify audio research pipelines, while preserving each dataset’s idiosyncracies: if a dataset has ‘non-standard’ attributes, we include them as well.

# Statement of need

### What is there already

Data utility libraries exist for other fields such as text,
video and image analysis [1, 10, 27, 28] which allow a user
to download a dataset and load it into memory for ease
of use in experimentation and consistent results. TensorFlow [1], a deep learning framework, includes a variety
of datasets covering images, text, language translation and
video 3
. In order to ensure the integrity of the data, TensorFlow hard codes expected file sizes and SHA256 checksums of each file in their library, as well as paths of the
data included with the dataset. If the expected values do
not match what is downloaded, the local dataset is not considered valid and is not available for usage in the library.
Scikit-Learn [28], a popular machine learning library
for Python, includes their own set of dataset loading utilities 4
. Some small datasets, known as “toy datasets”, are
included directly in the library. Larger datasets, known
as “real-world datasets” are downloaded and stored in a
“data home” directory on the local machine. Like TensorFlow, Scikit-Learn checks for dataset integrity based on a
SHA256 checksum, but only checks the downloaded zip or
tar file itself. This approach requires that users download
the entirety of the Scikit-Learn library in order to use the
dataset loaders.
MLDatasets 5
acts as a specification for how datasets
should be managed. DataDeps [36] specifies dataset metadata that conforms to a management system. This method
allows for multiple people to maintain their own dataset repositories or for a single organization to set up multiple,
independent libraries, each for one dataset.
There are few examples of dataset utility libraries for
music. However, the python library Nussl [19] for source
separation contains some dataset utilities. Unlike the other
libraries previously mentioned, Nussl does not include
any utilities for dataset retrieval and expects the user to
have the datasets locally on the machine before use. However, it includes expected checksums for the dataset audio
and logic to check for validity and existence of the dataset
as well as simple utilities for loading the data.
Software also exists for loading particular types of
(music-centric) annotations, including pretti midi 6
for MIDI data, JAMS [17] for data released in JAMS format, and Music21 7
for MIDI and MusicXML data. When
annotations are released in these formats, custom loading
code is less necessary. However, many annotations are released in other formats and require custom loading code.


## Regarding audio datasets

### Why not including everything in mirdata already? 

Musical datasets are extremely complex compared to other
audio datasets. They usually convey much more metadata information and their annotations are 
of several different types, reflecting the several different tasks that there are in Music Information Research
 (e.g melody estimation, beat tracking, chord estimation, etc). Besides, music  datasets have
 much more variaty of annotation formats and detail, e.g. chords can be annotated in many different 
 forms (example?). Dedicating the same repository for music and other purpose audio datasets 
 would converge to a very complex, hard to manage repository, which would be hard to scale. 
 Instead, we propose to adapt mirdata to simpler, more standarized datasets and introduce the annotation 
 types and formats that the communities working with environmental sound, bioacoustics and speech
 would need. 
 
### Why a separated library to handle datasets?

There are other libraries that handle datasets, like Tensorflow, Scickit learn, DCASE models. However, 
using datasets in the context of those libraries makes it difficult to exchange models and software, as 
data loaders are designed to work with those environments only. Instead, we think this should be handled
separately, as a standalone library that can easily be plugged in different work pipelines, 
as we show in our documentation examples.


# Acknowledgements



# References
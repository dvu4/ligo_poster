# ligo_poster


### 1. Abstract
Extracting meaningful signals of GW150914 event, an astrophysical event observed by the gravitational-wave detectors from the LIGO Hanford and LIGO Livingston observatories is a huge effort, and there is a need to reproduce the LIGO collaboration on these quantative results.

Query language for data provenance, Prolog, is useful in computing provenance or lineage, then use this to derive and answer some useful information about the data;
#### Creating a workflow graph for a script

Generated “combined view” in YW

    $ yw graph GW150914_tutorial_uri.py -config graph.view=combined -config graph.layout=tb | dot -Tpng -o GW150914_tutorial_uri.png && open GW150914_tutorial_uri.png
    
    
#### YesWorkflow output

The image below was produced by YesWorkflow using the YW comments added to a conventional (non-dataflow oriented) python script ([GW150914_tutorial_uri.py](https://github.com/idaks/ligo/blob/master/GW150914_tutorial_uri.py "GW150914_tutorial_uri.py")):

![example](https://raw.githubusercontent.com/idaks/ligo/master/GW150914_tutorial_uri.png)

The green blocks represent stages in the computation performed by the script. The labels on arrows name the input, intermediate, and final data products of the script.


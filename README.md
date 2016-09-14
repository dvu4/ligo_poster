# ligo_poster


### 1. Abstract
Extracting meaningful signals of GW150914 event, an astrophysical event observed by the gravitational-wave detectors from the LIGO Hanford and LIGO Livingston observatories is a huge effort, and there is a need to reproduce the LIGO collaboration on these quantative results.

Query language for data provenance, Prolog, is useful in computing provenance or lineage, then use this to derive and answer some useful information about the data;


### 2. Purpose
Query data provenance on LIGO script which is exploring signal processing with LIGO GW150914 open data.

Some ([tutorials](https://losc.ligo.org/tutorials/ "GW150914_tutorial_uri.py")) of GW150914 event.

Run LIGO ([code](https://github.com/minrk/ligo-binder "GW150914_tutorial_uri.py")) on binder.

![example](https://raw.githubusercontent.com/idaks/ligo/master/GW150914_tutorial_uri.png)






### 3. Graph Query

Q2-pro : "List the script inputs that are upstream of a given data product D".

        bash yw_prospective_lineage.sh filtered_white_noise_data > graph/yw_prospective_lineage_filtered_white_noise_data.gv
        
        bash yw_prospective_lineage.sh shifted_wavefile > graph/yw_prospective_lineage_shifted_wavefile.gv
        
        bash yw_prospective_lineage.sh whitened_bandpass_wavefile > graph/yw_prospective_lineage_whitened_bandpass_wavefile.gv
        
        
         
        
Q1-pro : Render everything upstream of a given data product D”, where D can be any one (output or intermediate) data element of the YW model of the script:


        dot -Tpdf yw_prospective_lineage_filtered_white_noise_data.gv -o yw_prospective_lineage_filtered_white_noise_data.pdf
        dot -Tpng yw_prospective_lineage_filtered_white_noise_data.gv -o yw_prospective_lineage_filtered_white_noise_data.png
        
        ![example](https://raw.githubusercontent.com/dvu4/ligo_poster/master/yw_prospective_lineage_filtered_white_noise_data.png)        
        
        
        dot -Tpdf yw_prospective_lineage_shifted_wavefile.gv -o yw_prospective_lineage_shifted_wavefile.pdf
        dot -Tpng yw_prospective_lineage_shifted_wavefile.gv -o yw_prospective_lineage_shifted_wavefile.png
        
        ![example](https://raw.githubusercontent.com/dvu4/ligo_poster/master/yw_prospective_lineage_shifted_wavefile.png)
        
        
        dot -Tpdf yw_prospective_lineage_whitened_bandpass_wavefile.gv -o yw_prospective_lineage_whitened_bandpass_wavefile.pdf
        dot -Tpng yw_prospective_lineage_whitened_bandpass_wavefile.gv -o yw_prospective_lineage_whitened_bandpass_wavefile.png
        
        ![example](https://raw.githubusercontent.com/dvu4/ligo_poster/master/yw_prospective_lineage_whitened_bandpass_wavefile.png)

![example](https://raw.githubusercontent.com/dvu4/ligo_poster/master/yw_prospective_lineage_strain_L1_filt.png)




### 4. List Query


        ---------------------------------------------------------------------------------------------------
        YW_Q7 : Which final outputs depend on the input FN_H1 ?

        yw_q7(FN_H1, NewDataName)
        ...................................................................................................
        yw_q7('FN_H1',strain_H1).
        yw_q7('FN_H1','GGW150914_L1_spectrogram_whitened.png').
        yw_q7('FN_H1',strain_L1).
        yw_q7('FN_H1',strain_16).
        yw_q7('FN_H1','GW150914_H1_spectrogram.png').
        yw_q7('FN_H1',strain_4).
        yw_q7('FN_H1','GW150914_L1_spectrogram.png').
        yw_q7('FN_H1','GW150914_filter.png').
        yw_q7('FN_H1','GW150914_strain_whitened.png').
        yw_q7('FN_H1','GW150914_H1_strain_filtered.png').
        yw_q7('FN_H1','GW150914_H1_strain_unfiltered.png').
        yw_q7('FN_H1','GW150914_H1_shifted.wav').
        yw_q7('FN_H1','GW150914_ASDs.png').
        yw_q7('FN_H1','GW150914_L1_shifted.wav').
        yw_q7('FN_H1','GW150914_H1_ASD_16384.png').
        yw_q7('FN_H1','GW150914_H1_whitenbp.wav').
        yw_q7('FN_H1','GW150914_H1_ASD_16384_zoom.png').
        yw_q7('FN_H1','GW150914_L1_whitenbp.wav').
        yw_q7('FN_H1','GW150914_H1_ASD_4096_zoom.png').
        yw_q7('FN_H1','GGW150914_H1_spectrogram_whitened.png').


        ---------------------------------------------------------------------------------------------------
        YW_Q8 : Which final outputs and intermediate outputs depend on the input FN_H1 ?

        yw_q8(AncestorData, ChildData)
        ...................................................................................................
        yw_q8('FN_H1',strain_H1).
        yw_q8('FN_H1','GGW150914_L1_spectrogram_whitened.png').
        yw_q8('FN_H1',strain_L1).
        yw_q8('FN_H1',strain_16).
        yw_q8('FN_H1','GW150914_H1_spectrogram.png').
        yw_q8('FN_H1',strain_4).
        yw_q8('FN_H1','GW150914_L1_spectrogram.png').
        yw_q8('FN_H1','PSD_H1').
        yw_q8('FN_H1','PSD_L1').
        yw_q8('FN_H1','GW150914_filter.png').
        yw_q8('FN_H1',strain_H1_whiten).
        yw_q8('FN_H1',strain_L1_whiten).
        yw_q8('FN_H1','GW150914_strain_whitened.png').
        yw_q8('FN_H1',strain_H1_whitenbp).
        yw_q8('FN_H1','GW150914_H1_strain_filtered.png').
        yw_q8('FN_H1',strain_L1_whitenbp).
        yw_q8('FN_H1','GW150914_H1_strain_unfiltered.png').
        yw_q8('FN_H1',strain_H1_filt).
        yw_q8('FN_H1','GW150914_H1_shifted.wav').
        yw_q8('FN_H1','GW150914_ASDs.png').
        yw_q8('FN_H1',strain_L1_filt).
        yw_q8('FN_H1','GW150914_L1_shifted.wav').
        yw_q8('FN_H1','GW150914_H1_ASD_16384.png').
        yw_q8('FN_H1',strain_H1_shifted).
        yw_q8('FN_H1','GW150914_H1_whitenbp.wav').
        yw_q8('FN_H1','GW150914_H1_ASD_16384_zoom.png').
        yw_q8('FN_H1',strain_L1_shifted).
        yw_q8('FN_H1','GW150914_L1_whitenbp.wav').
        yw_q8('FN_H1','GW150914_H1_ASD_4096_zoom.png').
        yw_q8('FN_H1','GGW150914_H1_spectrogram_whitened.png').


        ---------------------------------------------------------------------------------------------------
        YW_Q9 : Which inputs does the output GW150914_H1_whitenbp.wav depend on ?

        yw_q9(DataNameIn, GW150914_H1_whitenbp.wav)
        ...................................................................................................

        WorkflowName = GRAVITATIONAL_WAVE_DETECTION
        AncestorData = FN_H1yw_q9(strain_H1_whitenbp,'GW150914_H1_whitenbp.wav').
        yw_q9(strain_L1_whitenbp,'GW150914_H1_whitenbp.wav').
        yw_q9('FN_H1','GW150914_H1_whitenbp.wav').
        yw_q9('FN_L1','GW150914_H1_whitenbp.wav').
        yw_q9('FN_16','GW150914_H1_whitenbp.wav').
        yw_q9('FN_4','GW150914_H1_whitenbp.wav').
        yw_q9(fs,'GW150914_H1_whitenbp.wav').


        ---------------------------------------------------------------------------------------------------
        YW_1Q : What programs have input ports that receive data strain_H1_whitenbp ?

        yw_q10(DataNameIn, GW150914_H1_whitenbp.wav)
        ...................................................................................................
        yw_q10(strain_H1_whitenbp,'SHIFT_FREQUENCY_BANDPASSED').
        yw_q10(strain_H1_whitenbp,'WAVE_FILE_GENERATOR_FOR_WHITENED_DATA').
        yw_q10(strain_H1_whitenbp,'STRAIN_WAVEFORM_FOR_WHITENED_DATA').

        ---------------------------------------------------------------------------------------------------
        YW_Q16 : The Lowest Common Ancestor (LCA) of a pair of nodes GW150914_H1_whitenbp.wav and GW150914_L1_whitenbp.wav

        yw_q16(GW150914_H1_whitenbp.wav,GW150914_L1_whitenbp.wav, AncestorData) 
        ...................................................................................................
        yw_q16('GW150914_H1_whitenbp.wav','GW150914_L1_whitenbp.wav',strain_L1_whitenbp).
        yw_q16('GW150914_H1_whitenbp.wav','GW150914_L1_whitenbp.wav',strain_H1_whitenbp).
        yw_q16('GW150914_H1_whitenbp.wav','GW150914_H1_shifted.wav',strain_L1_whitenbp).
        yw_q16('GW150914_H1_whitenbp.wav','GW150914_H1_shifted.wav',strain_H1_whitenbp).
        yw_q16('GW150914_H1_whitenbp.wav','GW150914_H1_ASD_16384.png','FN_H1').
        yw_q16('GW150914_H1_whitenbp.wav','GW150914_H1_ASD_16384.png','FN_L1').
        yw_q16('GW150914_H1_whitenbp.wav','GW150914_H1_ASD_16384.png','FN_16').
        yw_q16('GW150914_H1_whitenbp.wav','GW150914_H1_ASD_16384.png','FN_4').
        yw_q16('GW150914_H1_whitenbp.wav','GW150914_H1_ASD_16384.png',fs).
        yw_q16('GW150914_H1_strain_filtered.png','GW150914_filter.png',strain_H1).
        yw_q16('GW150914_H1_strain_filtered.png','GW150914_filter.png',strain_L1).
        yw_q16('GW150914_H1_strain_filtered.png','GW150914_filter.png','COEFFICIENTS').

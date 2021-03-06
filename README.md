# ETL-Public v0.1

Version 0.1 of the KC7 crosscut metadata model, consisting of a
partial mapping of GTEx v7 metadata into DATS JSON. See the
`releases/` subdirectory for the JSON files (in BDBag format) and
accompanying release notes.

To run the (preliminary) GTEx v7 to DATS converter (`gtex_v7_to_dats.py`)
download the two tab-delimited GTEx public metadata files from 
https://www.gtexportal.org/home/datasets. The script expects to find
them in the current working directory:

* GTEx_v7_Annotations_SampleAttributesDS.txt
* GTEx_v7_Annotations_SubjectPhenotypesDS.txt

Running the conversion script with the `--print_sample_histogram` flag
will parse the two metadata files and display a histogram showing how
many subjects/patients (`n_subjects`, column 2) are linked to the
indicated number of samples (`n_samples`, column 1). For example:

    bash-3.2$ ./bin/gtex_v7_to_dats.py --print_sample_histogram
    INFO:root:Read 752 subject(s) from GTEx_v7_Annotations_SubjectPhenotypesDS.txt
    INFO:root:Read 15598 sample(s) from GTEx_v7_Annotations_SampleAttributesDS.txt
    Histogram of number of subjects that have a given number of samples
    n_samples	n_subjects
    1	14
    2	13
    3	11
    4	2
    5	9
    6	7
    8	8
    7	10
    9	14
    10	12
    11	13
    12	19
    13	21
    14	31
    15	21
    16	18
    17	28
    18	24
    19	32
    20	48
    21	27
    22	35
    23	43
    24	39
    25	44
    26	33
    27	30
    28	34
    29	22
    30	24
    31	12
    32	5
    33	9
    34	7
    35	7
    36	1
    37	3
    38	3
    39	3
    40	3
    41	1
    43	1
    44	5
    45	1
    53	1
    56	1
    57	1
    68	1
    160	1
    n_total_samples=15598
    n_total_subjects=752
    bash-3.2$ 

Running the conversion script as follows currently generates a single JSON file for each RNA-Seq 
sample in GTEx v7. In subsequent releases the samples will be linked directly to the DATS
Datasets:

    mkdir -p gtex_rnaseq_json
    ./bin/gtex_v7_to_dats.py --smafrze=RNASEQ --output_dir=gtex_rnaseq_json





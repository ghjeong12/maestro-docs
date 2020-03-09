.. _Getting Started:

===============
Running MAESTRO
===============

.. _Parameters Input to MAESTRO:

Parameters Input to MAESTRO
---------------------------

.. code-block:: none

	--print_res=true/false : If set true, MAESTRO prints out detailed cost information to the screen

	--print_res_csv_file=true/false : If set true, MAESTRO prints out a csv file that contains various statistics

	--print_log_file=true/false : If set true, MAESTRO prints out a log file that contains various information of detailed computation patterns to "log.txt"

	--Mapping_file='data/mapping/Resnet50_dla.m' : Specify the target dataflow and layer description file

	--HW_file='./hw_parameters.m' : Specify the Hardware parameters file

	--noc_bw=64 : NoC bandwidth

	--noc_hop_latency=1 : NoC latency per hops

	--noc_mc_support=true : NoC multicast support (In current dev version it's always on)

	--num_pes=256 : Number of PEs

	--num_pe_alus=1 : PE ALU vector width

	--l1_size=32 : l1 buffer size

	--l2_size=512 : l2 buffer size

.. _Hardware Description:

Hardware Description File
--------------------------

The Hardware Description file is provided as an input to MAESTRO as:

.. code-block:: none

	--HW_file='./hw_parameters.m' : Specify the Hardware parameters file

This file contains Hardware Description as follows:


===============  ======================
NumPEs: 1024     **Number of PEs**
L1Size: 256	     **l1 buffer size**
L2Size: 4096     **l2 buffer size**
NoC_BW: 64       **NoC bandwidth**
===============  ======================

.. note::
   For more information on the Hardware Supported, please see
   :ref:`Hardware Supported`.

.. _Mapping Definition:

Mapping Definition
------------------

A mapping is a MAESTRO input file which contains a DNN model and the dataflow for each layer.

.. code-block:: none

	Network MobileNetV2 {
        Layer CONV1 {
                Type: CONV
                Stride { X: 2, Y: 2 }
                Dimensions { K: 32, C: 3, R: 1, S: 1, Y:224, X:224 }
                Dataflow {
                        SpatialMap(1,1) K;
                        TemporalMap(64,64) C;
                        TemporalMap(Sz(R),Sz(R)) R;
                        TemporalMap(Sz(S),Sz(S)) S;
                        TemporalMap(Sz(R),1) Y;
                        TemporalMap(Sz(S),1) X;
                        Cluster(64, P);
                        SpatialMap(1,1) C;
                        TemporalMap(Sz(R),1) Y;
                        TemporalMap(Sz(S),1) X;
                        TemporalMap(Sz(R),Sz(R)) R;
                        TemporalMap(Sz(S),Sz(S)) S;
                }
        }



===================================================  =========================================================
Network MobileNetV2                                  **DNN MODEL NAME**
Layer CONV1                                          **LAYER NAME**
Type: CONV                                           **TYPE OF CONVOLUTION**
Dimensions { K: 32, C: 3, R: 1, S: 1, Y:224, X:224}  **LAYER DIMENSIONS**
Dataflow                                             **DATAFLOW FOR THE LAYER IN MAESTRO COMPILER DIRECTIVES**
===================================================  =========================================================


.. _How to generate a Mapping:

How to generate a Mapping
--------------------------

This tutorial is written to provide an easy way to generate a mapping from a PyTorch/Keras model.

1. :ref:`Generate a MAESTRO DNN Model file from a Pytorch/Keras model`
2. :ref:`Generate a MAESTRO Mapping file with the Maestro DNN Model file and specific dataflow`
3. :ref:`Run MAESTRO with the generated mapping`




.. _Generate a MAESTRO DNN Model file from a Pytorch/Keras model:

Generate a MAESTRO DNN Model file from a Pytorch/Keras model
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: bash

   cd tools/frontend

Check the messages from the help for the future reference

.. code:: bash

	python frameworks_to_modelfile_maestro.py --help

.. code:: bash

	python frameworks_to_modelfile_maestro.py --api_name pytorch --input_size 3,224,224 --model mobilenet_v2 --outfile dnn_model.m

.. code-block:: none

	--api_name: the API name, choose from "pytorch, keras"

	--input_size: the input image size of the first layer

	--model: the model name from torchvision.models (or tensorflow.keras.applications)
         TO use a custom model, enter custom for this argument.

	--custom: Enter the custom network python file name here.
          The file should have a function whose name is same as the file name and returns the model.
          (This option is working only for keras now)

	--outfile: the MAESTRO model output file name


The MAESTRO DNN Model, dnn_model.m, will be generated in ../../data/model




.. _Generate a MAESTRO Mapping file with the Maestro DNN Model file and specific dataflow:

Generate a MAESTRO Mapping file with the Maestro DNN Model file and specific dataflow
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Check the messages from the help for the future reference

.. code:: bash

	python modelfile_to_mapping.py --help
	python modelfile_to_mapping.py --model_file dnn_model.m --dataflow os --outfile out.m

.. code-block:: none

	--model_file: The model file supported by MAESTRO as specified by the user or generated by the above given script.

	--dataflow: the dataflow for each layer, choose from "os, ws, rs, dla"

	--outfile: the MAESTRO Mapping output file

The mapping file, out.m, will be generated in ../../data/mapping



.. _Run MAESTRO with the generated mapping:

Run MAESTRO with the generated mapping
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Go back to the maestro-dev directory

.. code:: bash

	cd ../../

Change the contents of "run.sh" to use the mapping file generated

.. code-block:: none

	--Mapping_file='data/mapping/out.m'

Run MAESTRO

.. code:: bash

	./run.sh

## 1. Introduction
This module contains workloads to evaluate the system performance using use cases related to image classification and object detection using TensorFlow. It has workloads “ResNet50_v1” and “ssd_mobilenet” and can run single, multi-batch, and multi-instance scenarios.
Workloads are built and tested using TensorFlow (version 1.14) framework. For more information about TensorFlow please follow the link: https://www.tensorflow.org. Workloads run with fp32 precision by default.

## 2. System Requirements
   * This module can run on all the systems supported by TensorFlow.
   * Note: When running tensorflow-gpu on Ubuntu, we recommend running Ubuntu 18.04.1.

## 3. Run the Benchmark

##### Steps to configure the machine

####### Ubuntu

1. Download or clone the AIXPRT repository.

2. Install dependencies:

    ```
    sudo apt-get update
    sudo apt-get install python3 python3-numpy python3-pil python3-opencv
    sudo apt-get install python python-numpy python-pil
    sudo apt install python3-pip
    sudo pip3 install opencv-python
    ```
3. Install TensorFlow 1.14.

   * Note: Workloads are built and tested with TensorFlow 1.14 and do not support the latest TensorFlow 2.0 version.

   * For instructions on how to install on Intel CPUs and AMD CPUs, follow the instructions on the [TensorFlow website](https://www.tensorflow.org/install/). For NVIDIA GPUs, follow the instructions on the NVIDIA [TensorFlow GPU website](https://www.tensorflow.org/install/gpu)

   * To install TensorFlow with AMD ROCm support follow the instructions [AMD ROCM TensorFlow](https://rocm.github.io/dl.html)
   NOTE: on AMD-GPU, Ubuntu 18.04 has the support for latest drivers and is recommend to use Ubuntu 18.04.

   * Below are some simple instructions for running the benchmark. However, users are free to install any different type of TensorFlow according to the system they are running on.


    ```
    # CPU
    sudo apt-get install python3-pip
    pip3 install tensorflow

   ```



   ```

    # GPU
    ## Install the CUDA tools and cuDNN as requireed by TensorFlow
    ## When installing cuDNN on Ubuntu add these exports to .bashrc
    export PATH=/usr/local/cuda-{version}/bin${PATH:+:${PATH}}
    export LD_LIBRARY_PATH=/usr/local/cuda-{version}/lib64:$LD_LIBRARY_PATH
    export PATH=/usr/local/cuda/bin${PATH:+:${PATH}}
    export LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH

    sudo apt-get install python3-pip
    pip3 install tensorflow-gpu

   ```

##### Steps to run the benchmark
 1. Navigate to directory:

    ```
    cd AIXPRT/Harness
    ```

 2. Run the benchmark:

    ```
    python3 index.py

    ```

 3. If running on GPU target, please edit AIXPRT/Config/{filename.json} to set "hardware" to gpu .  


## 3. Results

When the test is complete, the benchmark saves the results to AIXPRT/Results in JSON format, and also generates CSV files with the name {ConfigName}_RESULTS_SUMMARY.csv
To submit results, please follow the instructions in AIXPRT/ResultSubmission.md or at [AIXPRT Results Submission](https://github.com/BenchmarkXPRT/Public-AIXPRT-Resources/blob/master/OtherDocuments/ResultSubmission.md)


##### Sample results summary file <br/>

   Each results summary file has three sections: SYSTEM INFORMATION, RESULTS SUMMARY and DETAILED RESULTS.<br/>
   1. SYSTEM INFORMATION <br/>
   This section provides basic information about the system under test. <br/>

   ![alt text](https://github.com/BenchmarkXPRT/Public-AIXPRT-Resources/blob/master/assets/tensorflow_systemInfo.png)

   2. RESULTS SUMMARY <br/>
   AIXPRT measures inference latency and throughput for image recognition (ResNet-50) and object detection (SSD-MobileNet) tasks. batching tasks allows AI applications to achieve higher levels of throughput, but higher throughput may come at the expense of increased latency per task. In real-time or near real-time use cases like performing image recognition on individual photos being captured by a camera, lower latency is important to enable better user experience. In other cases, like performing image recognition on a large library of photos, higher throughput through batching images or concurrent instances may allow faster completion of the overall workload. The achieve optimal latency and/or throughput levels, AI applications often tune batch sizes and/or concurrent instances according to a system’s hardware capabilities, such as the number of available processor cores and threads.To represent a spectrum of common tunings, AIXPRT tests AI tasks in different batch sizes (1 - 128 is the default in this package) that are relevant to the target test system.
   AIXPRT then reports the maximum throughput and minimum latency for image recognition (ResNet-50) and object detection (SSD-MobileNet v1)usages.<br/>
   The AIXPRT results summary (example below) makes it easier to quickly identify relevant comparisons between systems. <br/>

   ![alt text](https://github.com/BenchmarkXPRT/Public-AIXPRT-Resources/blob/master/assets/results_summary.png)


   3. DETAILED RESULTS <br/>
   This section shows the throughput and latency results for each AI task configuration tested by the benchmark.
   AIXPRT runs each AI task (e.g. ResNet-50, batch1, on CPU) multiple times and reports the average inference throughput and corresponding latency percentiles.

   ![alt text](https://github.com/BenchmarkXPRT/Public-AIXPRT-Resources/blob/master/assets/detailed_results.png)

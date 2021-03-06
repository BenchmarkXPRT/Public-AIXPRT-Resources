## 1. Introduction
This module contains workloads to evaluate the system performance of use cases related to recommendation using MXNet.
It can run single-batch, multi-batch, and multi-instance scenarios.

## 2. System Requirements
* Operating System: Ubuntu 18.04 LTS
* CPU:  AMD, Intel
* GPU: NVIDIA


## 3. Run the Benchmark

#### Steps to configure machine
1. Install dependencies
 * Install Python 3
 *
        ```
        sudo apt-get install python3
        sudo apt-get -y install python3-pip python3-opencv
        pip3 install opencv-python
        ```

 * Install [MXNET](https://mxnet.incubator.apache.org/get_started) <br/>

    Choose the required installation of MXNet depending on your hardware ( CPU /GPU). Please install the python3 version of MXNet with pip3.


#### Steps to run the benchmark

1. Navigate to directory:

        ```
        cd AIXPRT/Harness
        ```

2. Run the benchmark

THIS PARTICULAR WORKLOAD REQUIRES KAGGLE'S SERVICES and IS SUBJECT TO THE TERMS: https://www.kaggle.com/terms
IF YOU DO NOT AGREE TO ALL OF THEM, YOU MAY NOT EXECUTE THE WORKLOAD OR ACCESS KAGGLE'S SERVICES IN ANY MANNER.

        ```
        python3 index.py
        ```

## Results

When the test is complete, the benchmark saves the results to AIXPRT/Results in JSON format, and also generates CSV files with the name {ConfigName}_RESULTS_SUMMARY.csv
To submit results, please follow the instructions in AIXPRT/ResultSubmission.md or at https://www.principledtechnologies.com/benchmarkxprt/aixprt/2019/submit-results.php.


##### Sample results summary file <br/>

Each results summary file has three sections: SYSTEM INFORMATION, RESULTS SUMMARY, and DETAILED RESULTS.<br/>
 1. SYSTEM INFORMATION <br/>
    This section provides basic information about the system under test. <br/>
    ![alt text](https://github.com/BenchmarkXPRT/Public-AIXPRT-Resources/blob/master/assets/mxnet_systeminfo.png)

 2. RESULTS SUMMARY <br/>
    AIXPRT measures inference latency and throughput for the Wide and Deep Recommendation task. batching allows AI applications to achieve
higher levels of throughput, but higher throughput may come at the expense of increased latency per task.
AIXPRT then reports the maximum throughput and minimum latency for Wide and Deep Recommendation usages.<br/>
The AIXPRT results summary (example below) makes it easier to quickly identify relevant comparisons between systems. <br/>

 ![alt text](https://github.com/BenchmarkXPRT/Public-AIXPRT-Resources/blob/master/assets/mxnet_results_sumary.png)


 3. DETAILED RESULTS <br/>
   This section shows the throughput and latency results for each AI task configuration tested by the benchmark.
AIXPRT runs each AI task (e.g. ResNet-50, batch1, on CPU) multiple times and reports the average inference throughput and corresponding latency percentiles.

![alt text](https://github.com/BenchmarkXPRT/Public-AIXPRT-Resources/blob/master/assets/mxnet_result_details.png)

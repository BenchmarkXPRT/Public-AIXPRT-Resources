### How to edit config

AIXPRT application runs on a default configuration provided by the workloads. However once a default config file is available/generated, the user can edit this config to change the workload behavior.

Note: Please perform at least 1 run of the benchmark so that a default config is generated at AIXPRT/Config/ or use one of the provided config file by copying to AIXPRT/Config/

1. If you wish to run same config for 'n' times, navigate to AIXPRT/Config open the configuration JSON file and edit the “iterations” value to the number you want. Save the file and run the benchmark. Application generates results for each iteration in different result files.

2. If you have multiple configuration JSON files present in AIXPRT/Config folder, the application will run all of the configurations and generate a separate result file for each config. This is mainly intended for automation purposes. If you do not want this to happen, simple delete the unwanted configuration JSON files.

3. If you wish to run only a specific workload/workloads in a config, please navigate to AIXPRT/Config/jsonFileYouWantToRun.json. Under the key “workloads_config,” each item is a workload. Delete the workloads you do not want to run.

Example  :  The JSON below has only ResNet-50 workload.

```
{
    "iteration": 1,
    "module": "Deep-Learning",
    "workloads_config": [
        {
            "batch_sizes": [
                1,
                2,
                4,
                8
            ],
            "hardware": "cpu",
            "iterations": 10,
            "name": "ResNet-50",
            "precision": "fp32",
            "runtype": "performance"
        }
    ]
}
```
4. Each workload item has keys like "hardware" and "precision" which are configurable. Here are the options each can take
* "hardware":"cpu" (or) "hardware":"gpu" (or) "hardware":"myriad"
* "precision": "fp32" (or) "precision": "fp16" (or) "precision": "int8"


5. Below is an explanation of each key: value in the config files <br/>
![alt text](https://github.com/BenchmarkXPRT/Public-AIXPRT-Resources/blob/master/assets/config_details.png)

<br/> Along with above tags, some workloads also have support for extra keys as below: <br/>
![alt text](https://github.com/BenchmarkXPRT/Public-AIXPRT-Resources/blob/master/assets/additional_config_keys.png)

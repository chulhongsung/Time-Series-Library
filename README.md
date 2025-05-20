This library is built upon TSLib, an open-source library for implementing benchmarks of ''Non-Parametric Time-series Forecasting with Global and Local Standardization''.   
In particular, our implementation focuses on the long-term forecasting task and analysis of standardization strategies.
 

1. Install Python=3.11 and torch=2.4. Then, install other libraries. 

For convenience, execute the following command.

```
pip install -r requirements.txt
pip install reformer-pytorch=1.4.4 # if needed
``` 

2. Data Preparation
- Download datasets (`ETT-small`, `Electricity`, `Weather`, `Traffic`) from the following GitHub repository: [https://github.com/thuml/Time-Series-Library](https://github.com/thuml/Time-Series-Library).
- Add downloaded datasets to `./data` folder.

3. Train and evaluate benchmarks. All scripts for all benchmarks are under the folder `./scripts/`. The experimental results can be reproduced by running the following command:

```
./scripts/long_term_forecast/{dataset}/{model}.sh
```
- `{dataset}` options: `ETT_script`, `ECL_script`, `Weather_script`, `Traffic_script`

For example, the results of TimeMixer can be reproduced by running following commands:
```
# long-term forecast
bash ./scripts/long_term_forecast/ETT_script/TimeMixer_ETTh1.sh
bash ./scripts/long_term_forecast/ETT_script/TimeMixer_ETTm1.sh
bash ./scripts/long_term_forecast/ETT_script/TimeMixer_ETTh2.sh
bash ./scripts/long_term_forecast/ETT_script/TimeMixer_ETTm2.sh

bash ./scripts/long_term_forecast/ECL_script/TimeMixer.sh
bash ./scripts/long_term_forecast/Weather_script/TimeMixer.sh
bash ./scripts/long_term_forecast/Traffic_script/TimeMixer.sh
```

For analysis of standardization strategies in Section 4.2, the experimental results of can be reproduced by running following commands:

```
./scripts/long_term_forecast/{dataset}/{model}_{strategy}.sh
```
- `{dataset}` options: `ETT_script (only ETTh1)` , `ECL_script`, `Weather_script`
- `{model}` options: `Transformer`, `TSMixer`, `DLinear`
- `{strategy}` options: `gls`, `revin`, `gls_revin`

For example, 
```
# standardization analysis
bash ./scripts/long_term_forecast/ETT_script/Transformer_ETTh1.sh # default
bash ./scripts/long_term_forecast/ETT_script/Transformer_ETTh1_gls.sh
bash ./scripts/long_term_forecast/ETT_script/Transformer_ETTh1_revin.sh
bash ./scripts/long_term_forecast/ETT_script/Transformer_ETTh1_gls_revin.sh
```

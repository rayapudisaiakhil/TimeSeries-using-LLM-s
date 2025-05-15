## Time Series Forecasting using Large Language Models
# Overview
If Large Language Models can find patterns within textual data and produce the next words in an autoregressive way, can we make Large Language Models to predict the value of a variable in a future timestep given its historical data. We set out to investigate the capability of Large Language Models (LLMs) to perform multivariate time-series forecasting, benchmarking their performance against classical methods (e.g., Prophet) and specialized time-series foundation models​. Our study encompasses a range of LLM-based approaches—including single-pass prompts, sliding-window forecasting, multivariate input sequences, diffusion-inspired denoising, and hybrid reprogramming layers
# Features
1. Implementation of time series tokenization techniques for LLMs
2. Prompt engineering strategies tailored for time series data
3. Methods for aligning time series embeddings with language space
4. Evaluation framework for comparing LLM-based approaches with traditional forecasting methods
5. Adaptations of popular LLM architectures for time series tasks
# Key Methods
1. Prompt Engineering : We frame forecasting as a plain-language instruction:
“Given the past LOOKBACK hourly temperatures: […], predict the next HORIZON hourly temperatures. Reply with a comma-separated list of numbers.” ​
2. Data Splitting: Different approaches to splitting the data for training the LLM and generating a prediction
- a. Batch Processing: In the simplest setup, we feed one contiguous year (8,640 hours) of raw temperature values to the quantized Mistral-7B model and request a 30-day (720-hour) forecast in a single pass
-  b. Sliding-Window Forecasting: To mitigate long-horizon drift, we implement a sliding-window strategy: partition the historical series into overlapping segments of fixed length (e.g., 168 hours for a 7-day lookback) and iteratively predict the next window (24 hours), appending each prediction to the input for the subsequent step
3. Post Prediciton Corrections: To correct systematic biases in LLM outputs, we explore two residual‐correction strategies correcting the generated outputs of LLM based on residuals
4. Diffusion based models: Taking inspiration from predictor-corrector networks in diffusion models, we have applied Score based diffusion models to correct time series outputs
# Results
We have seen that LLM+Score based diffusion models had higher accuracy compared to Large Language models and traditional time series models. Further analysis has to be performed on different types of data and huge volumes of data validate the scalability of these models.
For more information look into Project Report.pdf - https://github.com/rayapudisaiakhil/TimeSeries-using-LLM-s/blob/main/IE%207374%20Gen%20AI%20-%20Project%20Report.pdf

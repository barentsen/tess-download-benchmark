# tess-download-benchmark

**How fast can you access data from NASA's TESS Data Archive?**

This repository contains a
[simple Python notebook](https://github.com/barentsen/tess-download-benchmark/blob/master/tess-download-benchmark.ipynb)
which measures the time it takes to download ~1 GB of images from NASA's TESS Data Archive
using three different methods:
* from MAST via HTTP;
* from AWS S3 via HTTP;
* from AWS S3 via the `boto3` client library.

Over time, this repository may turn into a more comprehensive benchmarking tool,
but for now it is a toy notebook!


## Typical results

The table below shows the typical time it takes to sequentially download
30 TESS Full Frame Images (~1 GB) in three different environments.
These results are a snapshot obtained at a single point in time on Feb 23, 2021.

| Environment  | Data location | Client | Time | Speed    | Diff |
| ------------ | ------ | ------ | ----------: | -------: | ---: |
| Jupyter on AWS (TIKE) | AWS    | boto3  | 9s          | 907 Mbps | 1x   |
| Jupyter on AWS (TIKE)    | AWS    | httpx  | 16s         | 510 Mbps | 2x
| Jupyter on AWS (TIKE)    | MAST   | httpx  | 1m13s       | 112 Mbps | 8x   |
| Google Colab | AWS    | boto3  | 33s         | 247 Mbps | 4x   |
| Google Colab | AWS    | httpx  | 1m53s       | 72 Mbps  | 13x  |
| Google Colab | MAST   | httpx  | 8m27s       | 16 Mbps  | 56x  |
| Jupyter on Geert's WiFi | AWS    | boto3  | 5m49s       | 23 Mbps  | 39x  |
| Jupyter on Geert's WiFi | AWS    | httpx  | 11m31s      | 12 Mbps  | 77x  |
| Jupyter on Geert's WiFi | MAST   | httpx  | 14m05s      | 10 Mbps  | 94x  |

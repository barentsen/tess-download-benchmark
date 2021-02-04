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
These results are a snapshot obtained at a single point in time on Feb 3, 2021.

| Environment  | Data location | Client | Time | Diff |
| ------------ | ------ | ------ | ----------: | ---: |
| TIKE         | AWS    | boto3  | 9s          | 1x   |
| TIKE         | AWS    | httpx  | 16s         | 2x   |
| TIKE         | MAST   | httpx  | 1m13s       | 8x   |
| Google Colab | AWS    | boto3  | 33s         | 4x   |
| Google Colab | AWS    | httpx  | 1m53s       | 13x  |
| Google Colab | MAST   | httpx  | 8m27s       | 56x  |
| Geert's WiFi | AWS    | boto3  | 5m49s       | 39x  |
| Geert's WiFi | AWS    | httpx  | 11m31s      | 77x  |
| Geert's WiFi | MAST   | httpx  | 14m05s      | 94x  |


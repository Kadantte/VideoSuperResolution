# Benchmark
_NOTE: all results are evaluated from retrained model here._

## SISR (Single-Image Super-Resolution)*

|Model   |Scale Factor | Set5       | Set14      | BSD100     | Urban100   | Framework |
|:-------|:------------|:-----------|:-----------|:-----------|:-----------|:----------|
|Bicubic |     x2      |33.66/0.9299|30.24/0.8688|29.56/0.8431|26.88/0.8403|     -     |
|--------|-------------|------------|------------|------------|------------|-----------|
|Bicubic |     x4      |28.42/0.8104|26.00/0.7027|25.96/0.6675|23.14/0.6577|     -     |
|SRCNN   |     x4      |30.03/0.8514|26.94/0.7453|26.70/0.7054|24.08/0.7048|PyTorch    |
|ESPCN   |     x4      |29.01/0.8324|26.38/0.7348|26.34/0.7002|23.62/0.6872|PyTorch    |
|VDSR*   |     x4      |28.39/0.8108|25.76/0.7056|25.95/0.6698|23.12/0.6591|PyTorch    |
|DRCN    |     x4      |30.90/0.8748|27.59/0.7650|27.11/0.7204|    -/-     |PyTorch    |
|DRRN    |     x4      |31.07/0.8771|27.62/0.7663|27.15/0.7221|24.94/0.7438|PyTorch    |
|SRCNN   |     x4      |29.78/0.8441|26.83/0.7409|26.61/0.7014|23.94/0.6984|Tensorflow |
|VDSR*   |     x4      |28.38/0.8104|25.84/0.7054|25.95/0.6694|23.12/0.6590|Tensorflow |

* **Training hyper-params:**
   - Steps: 40k
   - Dataset: DIV2K
   - Batch: [16,96,96,3] (HR)
* VDSR seems fail to reach its global minima.

## VSR (Video Super-Resolution)
|Model   |Scale| VID4       | TBD..      | TBD..      | TBD..      | Framework |
|:-------|:----|:-----------|:-----------|:-----------|:-----------|:----------|
|Bicubic |x4   |23.58/0.6363| | | |     -     |
|Bayesian|x4   |26.04/0.8151| | | |Matlab     |
|VESPCN-1|x4   |25.46/0.7432| | | |Tensorflow |
|VESPCN-3|x4   |25.04/0.7143| | | |PyTorch    |
|SPMC    |x4   |25.65/0.7513| | | |PyTorch    |
|SOFVSR  |x4   |26.04/0.7753| | | |PyTorch    |
|FRVSR   |x4   |26.10/0.7755| | | |PyTorch    |
|RBPN    |x4   |26.23/0.7843| | | |PyTorch    |

* Compare Y-channel only, no border pixel shaved off.

## Image Denoise
|Model   | AWGN Level | BSD68      | Set12      | Urban100   |
|:-------|:-----------|:-----------|:-----------|:-----------|
|BM3D    |     15     |31.08/0.8722|32.37/0.8952|32.35/0.9220|
|--------|------------|------------|------------|------------|
|BM3D    |     25     |28.57/0.8013|29.97/0.8504|29.70/0.8777|
|--------|------------|------------|------------|------------|
|BM3D    |     50     |25.62/0.6864|26.72/0.7676|25.95/0.7791|

## Degradation Image Super-Resolution
|Model   | Scale | AWGN | Set5       | Set14      | Urban100   | BSD100     |
|:-------|:------|:-----|:-----------|:-----------|:-----------|:-----------|
|VDSR    |  x4   | 15   |26.11/0.7400|24.01/0.6293|22.11/0.6365|24.23/0.6037|
|VDSR-B  |  x4   | 15   |25.73/0.7232|23.63/0.6090|21.82/0.6196|24.03/0.5915|
|--------|-------|------|------------|------------|------------|------------|
|VDSR    |  x4   | 25   |24.66/0.6912|22.93/0.5818|21.27/0.5915|23.35/0.5611|
|VDSR-B  |  x4   | 25   |24.31/0.6729|22.50/0.5602|21.03/0.5742|23.13/0.5485|
|--------|-------|------|------------|------------|------------|------------|
|VDSR    |  x4   | 50   |22.27/0.5977|20.92/0.5005|19.74/0.5049|21.73/0.4907|
|VDSR-B  |  x4   | 50   |22.02/0.5811|20.52/0.4792|19.53/0.4862|21.53/0.4783|


## TF v.s. Torch (x4)
|TF/Torch | Set5       | Set14      | BSD100     | Urban100   |
|:--------|:-----------|:-----------|:-----------|:-----------|
|Baseline |28.42       |26.00       |25.96       |23.14       |

**Winner:** TF(), Torch()
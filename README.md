### SLS ReID
![](./images/cmc_curve.jpg)
### Datasets
- Download [Market1501 Dataset](http://www.liangzheng.org/Project/project_reid.html)
- Download [DukeMTMC-reID Dataset](https://github.com/layumi/DukeMTMC-reID_evaluation)
- Download [CUHK03 Dataset](http://www.ee.cuhk.edu.hk/~xgwang/CUHK_identification.html)
- Download [VIPeR Dataset](https://vision.soe.ucsc.edu/node/178)

### Training
- Train the baseline
```bash
python train.py --use_dense
```
- Train SLS_ReID
```bash
python sls_train.py --use_dense
```

### Pre-trained models

| Dataset | Baselines | SLS_ReID |
| --- | --- | ---|
| Market-1501 | [market/model.pth]() | [market/slsreid.pth]() | 
| CUHK03 | [cuhk03/model.pth]() | [cuhk03/slsreid.pth]() | 
| VIPeR | [viper/model.pth]() | [viper/slsreid.pth]() | 
| DukeMTMCReID | [duke/model.pth]() | [duke/slsreid.pth]() | 

### Testing

```bash
python test_cuhk03.py --model_path ./cuhk03/model.pth --use_dense
python eval_cuhk03.py
----------
python test_viper.py --model_path ./viper/model.pth --use_dense
%Add --re_rank to get re-ranking with k-reciprocal encoding
----------
python test.py --model_path ./market/model.pth --use_dense
python evaluate.py
python evaluate_rerank.py 
%Add --multi for multi-query evaluation
```

### Currents results

| Dataset | Rank 1 | Rank 5 | Rank 10 | Rank 20 | mAP |
| --- | --- | --- | --- | --- | --- |
| `CUHK03-Dense Baseline` | 0.679181 | 0.909378 | 0.953513 | 0.977772 | 0.781033 |
| `CUHK03-Dense SLS_ReID` | 0.843203 | 0.971337 | 0.989171 | 0.996290 | 0.899174 |
| `CUHK03-ResNet Baseline` |0.750155 | 0.950839 | 0.979171 | 0.991119 | 0.838676 |
| `CUHK03-ResNet SLS_ReID` | 0.909938 | 0.982435 | 0.992477 | 0.997420 | 0.941790 |
| `VIPeR-Dense Baseline` | 63.45% | 72.78% | 79.11% | 86.23% | - |
| `VIPeR-Dense SLS_ReID` | 67.41% | 81.01% | 88.61% | 93.51% | - |






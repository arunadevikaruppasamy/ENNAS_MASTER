
## Requirements
```
Python == 3.6.5, PyTorch == 1.0.1.post2
```


## Pretrained models

* Test on CIFAR10

* model with 600 training epochs
```
cd CNN && python test.py --auxiliary --model_path ./ENNAS_CIFAR_RESULT/cifar10_600.pt
```
Expected result: 2.64% test error rate with 3.08M model params.
The results could be found in ./ENNAS_CIFAR_RESULT/log.txt


* model with 1000 training epochs
```
cd CNN && python test.py --auxiliary --model_path ./ENNAS_CIFAR_RESULT_1000/cifar10_1000.pt

```

* Test on ImageNet
```
cd CNN && python test_imagenet.py --auxiliary --model_path ./ENNAS_ImageNet/model_best.pth.tar

```


###############################################
* Test on PTB

* ENNAS without PR
```
cd RNN && python test.py --model_path ./ENNAS_RESULT_ON_PTB/model.pt
```


* ENNAS with PR
```
cd RNN && python test.py --model_path ./ENNAS_PR_RESULT_ON_PTB/model.pt
```


* Test on WT2
```
cd RNN && python test.py --data /data/mzhang3/ENNAS_master/data/wikitext-2 --dropouth 0.15 --emsize 700 --nhidlast 700 --nhid 700 --wdecay 5e-7 --model_path ./ENNAS_WT2RESULT2/model.pt
```


## Architecture search

```
cd CNN && python ENNAS.py    # for conv cells on CIFAR-10
cd RNN && python ENNAS.py    # for recurrent cells on PTB
```

## Architecture evaluation

To evaluate our best cells by training from scratch, run
```
cd CNN && python train.py --auxiliary --cutout            # CIFAR-10
cd RNN && python train.py                                 # PTB
cd CNN && python train_imagenet.py --auxiliary            # ImageNet
cd RNN && python train.py --data ./data/wikitext-2 --dropouth 0.15 --emsize 700 --nhidlast 700 --nhid 700 --wdecay 5e-7  # WT2
```

## Architecture Visualization

Package graphviz is required to visualize the learned cells
```
cd CNN && python visualize.py ENNAS
cd CNN && python visualize.py ENNAS_PR
cd RNN && python visualize.py ENNAS
cd RNN && python visualize.py ENNAS_PR
```


## CUDA
- Compute Unified Device Architecture, it's a full development framework for any type of computation on a GPU. It's programming language, computing platform, api, extension of C or C++. Has all these frameworks and libraries built on top of it. High abstraction layer to develop over it.
- Over 150+ SDK that powers gaming, science, drug discovery, cyber security, robotics. Nvidia never charged money to use CUDA. It's closed source, exclusively for Nvidia's hardware, only deploy it on Nvidia chips. It just doesn't work on AMD by design and integrated with hardware. Similar to ios and deploying on Windows. It's pretty similar to Apple.
- CUDA development started in 2006, it took 6+ years to have a useful product
- Have 1100+ CUDA developers at Nvidia. One of the boldest bets in tech history, as stock dropped 80% because of it.

## Nvidia
- NVIDIA RTX 3090
- NVIDIA GTX 1070
- K80
- P4
- T4 (inference)
- Nvidia Pascal P100
- Nvidia Volta V100
- NVIDIA Ampere A100  (training)
- Nvidia Data-Centers
- Nvidia HOPPER H100 (HGX & DGX)
- T4 Cloud-based GPU

## Cloud vs. In House
- ML training is storage and GPUs, that's why clouds are a rip off for ML. Cloud for CPU is good deal.

## Commands
```
$ nvidia-smi // to check CUDA version, gpu usage, gpu type, etc
$ nvidia-smi --gpu-reset // important command, still don't understand it
```

## To check if CUDA is enabled
```
$ ipython
$ import torch
$ torch.cuda.is_available()
```

## CUDA Versions
```
$ cat /usr/local/cuda/version.txt
```

# 阅读笔记📕

一些水文模型模型开发的论文

## [1] [Wflow_sbm v0.7.3, a spatially distributed hydrological model: from global data to local applications](https://gmd.copernicus.org/articles/17/3199/2024/)[⭐⭐⭐]

- The wflow_sbm model aims to strike a balance between low-resolution, low-complexity and high-resolution, high-complexity hydrological models
- Wflow_sbm models can be set a priori for any catchment with the Python tool HydroMT-Wflow based on globally available datasets and through the use of point-scale (pedo)transfer functions and suitable upscal￾ing rules
- Wflow_sbm includes relevant hydrological processes such as glacier and snow processes, evapotranspiration processes,
  unsaturated zone dynamics, (shallow) groundwater, and surface flow routing including lakes and reservoirs.
- Free and open-source spatially distributed hydrological models that require a low calibration effort (parameters based on physical characteristics) and have fast runtimes applicable to large-scale high-resolution modelling (medium complexity) are not available
- the vertical hydrological simple bucket model: SBM, have different lateral concepts that control how water is routed for example over the land or river domain; makes use of the kinematic-wave approach for river, overland and lateral subsurface flow
- Wflow_sbm strikes a balance between low-resolution, low￾complexity and high-resolution, high-complexity hydrological models,
- uses a 1-D kinematic￾wave approach for channel, overland and lateral subsurface flows
- The switch to the programming language Julia was made because Julia offers high performance (speed of C), required
  for large-scale high-resolution hydrological model applications, and is an “easy-to-use” language. Julia also opens up
  opportunities to parallelize the code for further improved computational performance.
- water being routed downstream over an eight-direction (D8) network, instead of the element network being based on contour lines and trajectories
- improved accuracy with IHU-upscaled flow direction maps, applied to MERIT Hydro
- Following a multiscale parameter regionalization (MPR) technique (Samaniego et al., 2010), parameters were estimated at the original data resolution (“level 0”), and upscaled to the model resolution (“level 1”) with upscaling operators.

* spatially distributed (gridded) hydrological models
* spatially lumped models

这篇论文介绍了分布式水文模型Wflow.jl，其数据准备可以通过hydromt和

这篇论文的模型结构机理是相对简单的，即将水文模型的参数作为一种类似于神经网络参数的一种可微分计算(梯度计算)的参数，论文将梯度下降算法用于模型参数优化，并于Monto Carlo和贝叶斯的梯度优化算法进行对比，讨论了三个问题：

1. 深度学习框架反向计算的概念水温模型参数的可行性
2. 基于梯度的参数率定方法相比其他算法的准备性和适用性
3. 基于梯度的参数率定方法能否应用于参数较多的场景，如参数较多的分布式水文模型
   论文所解决的问题似乎与通常的径流预测有所差别，论文首先构建了一个随机降雨径流模型
   ![img](picture/paper1_f1.png)
   然后论文采用ADVI(Bayesian)以及三种Markov chain Monte Carlo方法，用于率定模型中的参数$`P_t`$和$`r_t`$，从而 `reconstruct precipitation over several decades`
   论文首先对比了不同长度下的降雨序列重构的方法率定性能，表明ADVI在较长的序列重构中比MCMC性能更强
   然后将ADVI用于真实事件中的降雨序列重构，对比了1、10、30天尺度下的重构精度
   这篇论文更多侧重于参数估计、不确定性领域，数学统计学概念较多，读起来有丢丢费力

## [2] [A Differentiable Hydrology Approach for Modeling With Time-Varying Parameters](https://agupubs.onlinelibrary.wiley.com/doi/10.1029/2021WR031377)

to be continue!

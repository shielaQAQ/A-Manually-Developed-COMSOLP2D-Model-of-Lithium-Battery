# A Manually Developed COMSOL P2D Model of Lithium Battery

本仓库公开一套手工搭建的COMSOL锂离子电池 P2D（Pseudo-Two-Dimensional）电化学模型及相关程序，主要包括：

- COMSOL 中建立的基础 P2D 模型；
- COMSOL 与 MATLAB 联合仿真程序；
- 简化 SP2D 模型的 MATLAB 实现；
- 在基础 P2D 模型上加入析锂反应的 COMSOL 模型。

本项目主要用于锂离子电池电化学建模学习、模型复现和科研交流。

---

## 1. Repository Contents

| File | Description |
|---|---|
| `matlab_comsol.7z` | 基础锂离子电池 P2D 电化学模型，使用 COMSOL Multiphysics 建立 |, | 在基础 P2D 模型上加入析锂反应的 COMSOL 模型 |, | 在基础 P2D 模型上加入析锂反应的 COMSOL 模型 |.
| `SP2D_MODEL.7z` | 简化 SP2D 模型的 MATLAB 程序，主运行文件为 `SP2D.m` |

---

## 2. Model Description

P2D 模型基于多孔电极理论和浓溶液理论，对锂离子电池内部主要电化学过程进行建模，涉及：

- 正极和负极固相锂扩散；
- 电解液中锂离子的扩散与迁移；
- 固相电势分布；
- 电解液电势分布；
- Butler–Volmer 电化学反应动力学；
- 电池端电压响应；
- 高倍率脉冲放电工况；
- 析锂副反应过程。

其中，`P2D-Model-lithium.mph` 在基础模型上进一步加入析锂相关方程，用于分析特定工况下的析锂行为。

---

## 3. Software Requirements

建议使用以下软件环境：

- COMSOL Multiphysics 5.6
- Batteries & Fuel Cells Module
- LiveLink for MATLAB
- MATLAB：R2021b

> 不同版本的 COMSOL 或 MATLAB 可能存在兼容性差异。  
> 使用前请确认相关物理场模块和 LiveLink 已正确安装。

---

## 4. Running the COMSOL P2D Model

### Basic P2D model

1. 打开 COMSOL Multiphysics；
2. 加载文件：

```text
P2D-Model.mph
```

3. 检查模型参数、材料属性和初始条件；
4. 依次执行：

```text
Build All Geometry
Build All Mesh
Compute
```

5. 在 `Results` 中查看端电压、固相浓度、电解液浓度和电势分布等结果。

### Lithium-plating model

打开：

```text
P2D-Model-lithium.mph
```

该模型在基础 P2D 模型上加入析锂副反应。运行前请重点检查：

- 析锂反应交换电流密度；
- 析锂平衡电位；
- 析锂反应动力学参数；
- 初始条件；
- 求解器设置；
- 仿真工况。

---

## 5. Running the COMSOL–MATLAB Coupled Model

1. 解压：

```text
matlab_comsol.7z
```

2. 启动 `COMSOL with MATLAB`；
3. 将 MATLAB 当前工作目录切换到解压后的程序文件夹；
4. 找到并运行联合仿真的主程序；
5. 根据代码中的注释修改模型路径、参数和工况。

运行前请检查程序中是否存在本地绝对路径，例如：

```matlab
C:\Users\username\Desktop\...
```

建议将其修改为相对路径。

---

## 6. Running the Simplified SP2D MATLAB Model

1. 解压：

```text
SP2D_MODEL.7z
```

2. 打开 MATLAB；
3. 将当前工作目录切换到解压后的文件夹；
4. 运行主文件：

```matlab
SP2D
```

或：

```matlab
run('SP2D.m')
```

`SP2D.m` 是简化 SP2D 模型的主运行文件。程序运行时可能调用同一文件夹中的其他 `.m`、`.mat`、`.xlsx` 或数据文件，因此请保持原始文件夹结构不变。

---

## 7. Expected Outputs

模型可用于获得以下结果：

- 电池端电压；
- 正负极固相锂浓度；
- 电解液浓度；
- 固相电势；
- 电解液电势；
- 电化学反应电流密度；
- 电极颗粒内部浓度分布；
- 高倍率脉冲放电响应；
- 析锂反应电流和析锂量。

由于参数设置、网格划分、求解器选项和软件版本不同，复现结果可能存在一定差异。

---

## 8. Related Publications

本仓库中的模型与下列论文和学位论文相关：

1. Zhou X, Wang Z, Zhang W, et al. Construction of simplified impedance model based on electrochemical mechanism and identification of mechanism parameters[J]. *Journal of Energy Storage*, 2024, 76: 109673.

2. Wang Z, Zhou X, Sun B, et al. Model construction and dominant mechanism analysis of li-ion batteries under periodic excitation[J]. *Space: Science & Technology*, 2024, 4: 0129.

3. Wang Z, Zhou X, Zhang W, et al. Parameter sensitivity analysis and parameter identifiability analysis of electrochemical model under wide discharge rate[J]. *Journal of Energy Storage*, 2023, 68: 107788.

4. 王志豪. 锂离子电池瞬时高倍率放电脉冲工况下电化学建模研究[D]. 北京交通大学, 2024. DOI: 10.26944/d.cnki.gbfju.2024.001469.

---

## 9. Suggested Citation

若本仓库中的 COMSOL P2D 模型、SP2D 程序或相关代码对你的研究有帮助，建议引用对应论文或学位论文。


```text
1. Zhou X, Wang Z, Zhang W, et al. Construction of simplified impedance model based on electrochemical mechanism and identification of mechanism parameters[J]. *Journal of Energy Storage*, 2024, 76: 109673.

2. Wang Z, Zhou X, Sun B, et al. Model construction and dominant mechanism analysis of li-ion batteries under periodic excitation[J]. *Space: Science & Technology*, 2024, 4: 0129.

3. Wang Z, Zhou X, Zhang W, et al. Parameter sensitivity analysis and parameter identifiability analysis of electrochemical model under wide discharge rate[J]. *Journal of Energy Storage*, 2023, 68: 107788.

4. 王志豪. 锂离子电池瞬时高倍率放电脉冲工况下电化学建模研究[D]. 北京交通大学, 2024. DOI: 10.26944/d.cnki.gbfju.2024.001469.
```

同时，可根据所使用的具体模型内容引用上述相关期刊论文。

---

## 10. Notes

- 本仓库内容主要用于学习和科研交流；
- COMSOL 模型文件为二进制文件，GitHub 无法直接在线预览；
- `.7z` 压缩包需下载并解压后使用；
- 使用模型前请核对参数单位和模型假设；
- 部分代码可能需要根据本机软件安装路径进行调整；
- 本模型不保证适用于所有电芯体系和运行工况；
- 在正式科研或工程应用中，应使用实验数据对参数和模型结果进行校准。

---


## 11. License

请根据模型和代码的知识产权归属选择合适的开源许可证。

在许可证尚未确定前，默认保留全部权利。未经许可，不建议将本仓库内容用于商业用途或再次分发。

---

## 13. Disclaimer

本项目按“现状”公开，不对模型的准确性、完整性、稳定性或特定用途适用性作出保证。使用者应自行检查模型假设、参数来源、计算设置和结果可靠性。

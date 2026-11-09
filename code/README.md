# 项目代码

在此目录存放数据处理、分析和绘图代码。

## 运行环境

使用 Python 3.11、PyTorch 2.6.0（CUDA 12.4）和 MONAI 1.5.2。此配置适用于带有兼容 NVIDIA 驱动的 x86-64 Windows 和 Linux 环境。PyTorch 和 torchvision 从 PyTorch 官方 CUDA 12.4 源安装，其余依赖从 PyPI 安装。

- NiBabel 和 pydicom 用于读取 NIfTI 和 DICOM。
- NumPy、SciPy 和 pandas 用于数值计算和表格分析，Matplotlib 用于绘图，tqdm 用于显示进度。

安装 uv 后，从项目根目录运行以下命令，按 `uv.lock` 创建并验证环境。

```sh
cd code
uv sync --locked
uv run python -c "import monai, torch; print(monai.__version__, torch.__version__, torch.version.cuda); assert torch.cuda.is_available(); print(torch.cuda.get_device_name())"
```

## 运行步骤

<!-- 填写运行入口、所需输入和结果的输出位置。 -->

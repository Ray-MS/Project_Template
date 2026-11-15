# 项目代码

在此目录存放数据处理、分析和绘图代码。

## 运行环境

两套环境均使用 Python 3.11 和 MONAI 1.5.2，面向 x86-64 Windows 和 Linux。每套配置有独立的 `uv.lock` 和 `.venv`。

| GPU | CUDA | PyTorch | torchvision | uv 项目目录（相对 `code/`） |
| --- | --- | --- | --- | --- |
| NVIDIA A800 | 12.4 | `2.6.0+cu124` | `0.21.0+cu124` | `.` |
| GeForce RTX 5090 | 12.8 | `2.8.0+cu128` | `0.23.0+cu128` | `environments/rtx5090` |

PyTorch 和 torchvision 从各自的官方 CUDA 索引安装，其余依赖来自 PyPI。RTX 5090 需要支持该卡的 NVIDIA 驱动，Linux 上的 PyTorch wheel 需要 glibc 2.28 或更高版本。

- NiBabel 和 pydicom 用于读取 NIfTI 和 DICOM。
- NumPy、SciPy 和 pandas 用于数值计算和表格分析，Matplotlib 用于绘图，tqdm 用于显示进度。

安装 uv 后，先进入 `code/`，再为目标 GPU 选择对应的命令。

```sh
cd code
```

```sh
# A800
uv sync --locked
uv run --locked python -c "import monai, torch; print(monai.__version__, torch.__version__, torch.version.cuda); print(torch.ones(1, device='cuda'), torch.cuda.get_device_name())"
```

```sh
# RTX 5090
uv sync --locked --project environments/rtx5090
uv run --locked --project environments/rtx5090 python -c "import monai, torch; print(monai.__version__, torch.__version__, torch.version.cuda); print(torch.ones(1, device='cuda'), torch.cuda.get_device_name())"
```

运行项目脚本时，A800 使用 `uv run --locked python path/to/script.py`，RTX 5090 使用 `uv run --locked --project environments/rtx5090 python path/to/script.py`。脚本路径相对于当前的 `code/` 目录。

## 运行步骤

<!-- 填写运行入口、所需输入和结果的输出位置。 -->

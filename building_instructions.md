## Ubuntu instructions

Install system-wide requirements

```bash
sudo apt update
sudo apt install build-essential cmake libboost-all-dev libtbb-dev
sudo apt install python3.11-dev
```

Clone (forked) repo

```bash
git clone https://github.com/L4rralde/gtsam_sl4_affine.git gtsam
cd gtsam
```

Create virtual environment.

```bash
python3.11 -m venv gtsam.venv
source gtsam.venv/bin/activate
```

Install gtsam python requirements
```bash
pip install --upgrade pip
pip install -r python/dev_requirements.txt
```

Build the repo

```bash
mkdir build && cd build
cmake .. \
  -DCMAKE_BUILD_TYPE=Release \
  -DGTSAM_BUILD_PYTHON=ON \
  -DPYTHON_EXECUTABLE=$(which python) \
  -DGTSAM_WITH_TBB=ON
make -j$(nproc)
```

Install gtsam python package

```bash
make python-install
```
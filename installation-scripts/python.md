# Python

```bash
sudo apt install -y \
python3-dev \
python3-pip \
python3-setuptools \
build-essential \
cmake

# Only need Python3?
echo "alias python=python3" >> ~/.bashrc
echo "alias pip=pip3" >> ~/.bashrc

source ~/.bashrc

pip install wheel setuptools
pip install virtualenv
```




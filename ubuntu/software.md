# Ubuntu Software

## Miniconda

### Installation

- Get Installation Package

```shell
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
```

- Setup `Miniconda` in batch mode
```shell
bash Miniconda3-latest-Linux-x86_64.sh -b
```

- Make `conda` executable
```shell
# replace below command with your actual path
sudo ln -s $HOME/miniconda3/bin/conda /usr/bin/conda
```

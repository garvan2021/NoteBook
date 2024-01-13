# Ubuntu

## Commands

### look up running process

- `top` (using `shift` + `v` to enable tree view)
- `pstree`

### checkout tpc server state
- using `netstat`
```shell
netstat -an
```
- using `lsof`
```shell
lsof -i -n
```

### create a sudo user

- Crerate a user to system
here replace "kelvin" to your favourite
```shell
sudo adduser kelvin
```

- Add user to sudo group
here replace "kelvin" to your favourite
```shell
sudo usermod -aG sudo kelvin
```

- Switch to user just created
```shell
su - kelvin
```

## Software

### Minicanda Installation

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


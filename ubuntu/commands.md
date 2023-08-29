# Ubuntu Commands
[return](./Ubuntu.md)

## adduser

### Create a sudo user

- Crerate a user to system
here replace `kelvin` as your favourite
```shell
sudo adduser kelvin
```

- Add user to sudo group
here replace `kelvin` as your favourite
```shell
sudo usermod -aG sudo kelvin
```

- Switch to user just created
```shell
su - kelvin
```

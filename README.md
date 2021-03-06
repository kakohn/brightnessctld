# brightnessctld
Brightnessctl sirve para leer y controlar el brillo del dispositivo.

#### Crear servicio brightnessctld:
```
# mkdir /etc/sv/brightnessctld
# cd /etc/sv/brightnessctld/ && touch run finish
```
#### Dentro de /etc/sv/brightnessctld/run:
```
#!/bin/sh
[ -r brightness ] && brightnessctl -q set "$(cat brightness)"
exec chpst -u nobody:video -b brightnessctl pause

```
#### Dentro de /etc/sv/brightnessctl/finish:
```
#!/bin/sh
brightnessctl get > brightness
```
#### Permisos:
```
chmod +x -R /etc/sv/brightnessctld/
```
#### Iniciar servicio:
```
ln -s /etc/sv/brightnessctld/ /var/service/
```
## Créditos:
- [KZWG63TF](https://www.reddit.com/user/KZWG63TF/)


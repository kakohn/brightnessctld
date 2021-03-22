# brightnessctld (Void Linux)
Brightnessctl sirve para leer y controlar el brillo del dispositivo.

#### Instalar brightnessctl
```
# xbps-install -Su
# xbps-install -S brightnessctl
```
#### Crear servicio brightnessctld:
```
# mkdir /etc/sv/brightnessctld
# cd /etc/sv/brightnessctld/ && touch run finish
```
#### Dentro de /etc/sv/brightnessctld/run:
```
#!/bin/sh
[ -r brillo ] && brightnessctl -q set "$(cat brillo)"
exec pause
```
#### Dentro de /etc/sv/brightnessctl/finish:
```
#!/bin/sh
brightnessctl get > brillo
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
- [KZWG63TF](https://www.reddit.com/user/KZWG63TF/): Idea central.
  - [Hilo de conversación](https://www.reddit.com/r/voidlinux/comments/hl29e1/how_to_reduce_brightness_on_boot/)


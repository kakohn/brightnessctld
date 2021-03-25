# brightnessctld (Runit/Void Linux)
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
#### Dentro de /etc/sv/brightnessctld/run: (encargado de leer brillo al encender del dispositivo)

    #!/bin/sh
    [ -r brillo ] && brightnessctl -q set "$(cat brillo)"
    exec chpst -b brightnessctl pause

#### Dentro de /etc/sv/brightnessctl/finish: (encargado de escribir el brillo al apagar el dispositivo)
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


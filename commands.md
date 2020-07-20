# Lista de comandos para Shell Script

## Buscar programa pelo terminal (( p/ Ubuntu/Debian e derivados ))

```sh
sudo apt-cache search <programa>
```

## Buscar programa pelo terminal (( p/ Fedora/CentOS e derivados ))

```sh
sudo dnf search <programa>
```

## Buscar programa pelo terminal (( p/ Arch Linux e derivados ))

```sh
sudo pacman -Ss <programa>
```

## Instalar programa pelo terminal (( p/ Ubuntu/Debian e derivados ))

```sh
sudo apt-get update
```

```sh
sudo apt-get install <programa>
```

## Instalar programa pelo terminal (( p/ fedora e derivados ))

```sh
sudo dnf install <programa>
```

## instalar programa pelo terminal (( p/ Arch Linux e derivados ))

```sh
sudo pacman -Sy <programa>
```

## Instalar pacote deb

```sh
sudo dpkg -i <pacote>.deb
```

```sh
sudo apt-get install -f
```

## Instalar pacote e dependências automaticamente de um rpm

```sh
sudo dnf install --nogpgcheck <pacote>
```

## Instalar pacote tar.pkg (p/ Arch Linux e derivados)

```sh
sudo pacman -U <pacote>.tar.pkg
```

## Instalar pacote AUR

```sh
git clone <repositorio_do_aur>
```

```sh
cd <pasta_criada>
```

```sh
makepkg -cis
```

## Instalar programa de código fonte

```sh
cat README* | less # ler as instruções se houver
```

```sh
./configure # se houver
```

```sh
make
```

```sh
sudo make install
```

## Instalar driver de wifi para placas rtl8723be
```sh
lspci
```

```sh
sudo apt-get install git linux-headers-generic build-essentialgit dkms # p/ Ubuntu e derivados
```

```sh
sudo dnf install git kernel-devel-$(uname -r) # p/ derivados de rpm
```

```sh
sudo pacman -S base-devel git linux-headers iw rfkill wireless_tools net-tools # p/ Arch Linux
```

```sh
git clone http://github.com/lwfinger/rtlwifi_new.git
```

```sh
cd rtlwifi_new && make
```

```sh
sudo make install
```

```sh
make clean
```

```sh
sudo nano /etc/modprobe.d/rtl8723be.conf # Escrever "options rtl8723be fwlps=0 swlps=0"
```

## Verificar se ext glob (ex do ext glob: rm !(*.zip|*.iso)) está ativado

```sh
shopt extglob
```

## Ativa ext glob

```sh
shopt -s extglob
```

## Desligar webcam

```sh
sudo modprobe -r uvcvideo
```

## Ligar webcam

```sh
sudo modprobe uvcvideo
```

## Mudar ordem de grub

```sh
sudo nano /etc/default/grub
```

```sh
sudo update-grub # p/ Ubuntu e derivados
```

```sh
sudo grub-mkconfig -o /boot/grub/grub.cfg # p/ linux em geral
```

## Alterar senha de usuário

```sh
sudo passwd <usuário>
```

## Criar lançador de aplicativo no menu

```sh
su
```

```sh
cd /usr/share/applications
```

```sh
echo \
"[Desktop Entry]
Encoding=UTF-8
Type=Application
Terminal=true
Name=<Nome de exibição da aplicação>
Exec=<Comando para executar aplicação>
Icon=<Ícone da aplicação>
Categories=<Categoria 1>;<Categoria 1>
" >> <arquivo>.desktop
```

## Montar iso

```sh
mount -o loop <sua_Imagem.iso> /media/<diretorio_ISO>
```

## Permitir acesso root ao vlc

```sh
sudo sed -i 's/geteuid/getppid/' /usr/bin/vlc
```

## Remover conta de convidado

```sh
sudo nano /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf # Escrever "allow-guest=false"
```

## Dar permissão para usuário usar a impressora

```sh
sudo gpasswd -a <seu usuario> lp
```

```sh
sudo gpasswd -a <seu usuario> sys
```

```sh
sudo gpasswd -a <seu usuario> scanner
```

## Instalar driver HP (( p/ Ubuntu/Debian e derivados ))

```sh
sudo apt-get install cups python-imaging ghostscript hplip cups-filters ghostscript gsfonts simple-scan python-pillow
```

```sh
systemctl enable org.cups.cupsd.service
```

```sh
systemctl daemon-reload
```

```sh
systemctl start org.cups.cupsd.service
```

```sh
sudo hp-setup -i
```

## Instalar driver hp (( p/ Arch Linux ))

```sh
sudo pacman -S cups python-imaging ghostscript hplip cups-filters ghostscript gsfonts simple-scan python-pillow
```

```sh
systemctl enable org.cups.cupsd.service
```

```sh
systemctl daemon-reload
```

```sh
systemctl start org.cups.cupsd.service
```

```sh
sudo hp-setup -i
```

## Instalar impressora HP

```sh
hp-setup -i
```

## Instalar chave pública

```sh
gpg --recv-keys <chave>
```

## Arch inserir linguagens
```sh
nano /etc/locale.gen # Descomente a linguagem desejada. Recomendp deixar também o inglês
```

```sh
sudo locale-gen
```

## Substituir texto em multiplos arquivos

```sh
find <pasta> -iname <nome do arquivo> -type f -print0 | xargs -0 sed -i 's/<texto1>/<texto2>/g'
```

## Substituir texto em multiplos arquivos com confirmação

```sh
find ./ -name <arquivo> -exec vim '+%s/<texto>/<texto da substitução>/gc' {} \;
```

## Substituir texto em multiplos arquivos com confirmação sem recursao

```sh
find ./ -maxdepth 1 -name <arquivo> -exec vim '+%s/<texto>/<texto da subistituicao>/gc' {} \;
```

## Busca as linhas dos arquivos que comtem uma string especificada

```sh
find ./ -type f -name <arquivo> -exec grep -l -i <texto> {} \;
```

## Alterar ação do fechamento da tampa (( Gnome ))

```sh
sudo nano /etc/systemd/logind.conf # procurar/inserir o texto "HandleLidSwitch='ops'" ops: "ignore" "poweroff" "reboot" "suspend" "hibernate" "lock"
```

```sh
systemctl restart systemd-logind
```

## Encerrar Sessão

```sh
sudo pkill -9 -u username
```

## Encerrar Sessão (( Gnome ))

```sh
gnome-session-quit
```

## Conectar à internet cabeada

```sh
ifconfig -a
```

```sh
dhcpcd <interface> # Opção 1
```


```sh
dhclient <interface> # Opção 2
```

```sh
Systemctl start dhcpcd #Opção 3
```

## Conectar a wifi

```sh
iwconfig
```

```sh
iwlist scan # se nao funcionar antes digite ifup <interface> ctrl + c
```

### Rede aberta (OPN)

```sh
iwconfig <interface> essid <nome da rede>
```

```sh
dhclient <interface>
```

### Rede encriptada (WEP)

```sh
iwconfig <interface> mode managed key <senha>
```

```sh
iwconfig <interface> essid <nome da rede>
```

```sh
dhclient <interface>
```

### Rede encriptada 2 (WPA/WPA2)

```sh
wpa_passphrase <nome da rede> > /<caminho do arquivo>.conf
```

```sh
wpa_supplicant -Dwext -i<interface> -c /<caminho do arquivo>.conf # se der certo dê ctrl + c
```

```sh
wpa_supplicant -Dwext -i<interface> -c /<caminho do arquivo>.conf -B
```

```sh
dhclient -r
```

```sh
dhclient <interface>
```

## Criar arquivo de texto com os binários de outro arquivo

```sh
od -An -vtx1 <arquivo> > <arquivo>.txt
```

## Gerar arquivo pelos seus binários escritos em um arquivo de texto

```sh
LC_ALL=C tr -cd 0-9a-fA-F < <arquivo>.txt | xxd -r -p > <arquivo>
```

## Criar live pendriven de ISO (recuperação não tão simples)

```sh
sudo dd if=<path>.iso of=/dev/sd<X> bs=<8M> status=progress oflag=direct
```

## Criar ISO de arquivos

```sh
mkisofs -o <path>.iso <diretório de arquivos>
```

## Criar ISO de CD/DVD

```sh
dd if=/dev/<cdrom> of=<path>.iso
```

## Reinstalar drivers de som (( p/ Ubuntu/Debian e derivados ))

```sh
sudo apt-get remove alsa-utils alsamixer pulseaudio
```

```sh
sudo apt-get purge pulseaudio
```

```sh
sudo apt-get clean
```

```sh
sudo apt-get autoremove
```

```sh
rm -rf ~/.pulse ~/.asound* ~/.pulse-cookie ~/.config/pulse
```

```sh
sudo apt-get install alsa-utils alsamixer pulseaudio
```

```sh
sudo alsa force-reload pavucontrol
```

## Descompactar arquivos compactados

### tar.gz

```sh
tar -xvzf <arquivo>.tar.gz -C <path destino>
```

### tar.bz2

```sh
tar -xvjf <arquivo>.tar.bz2 -C <path destino>
```

### tar.xz (( precisa do pacote xz-utils ))

```sh
tar -xvJf <arquivo>.tar.xz -C <path destino>
```

### zip

```sh
unzip <arquivo>.zip -d <path destino>
```

### rar

```sh
unrar e <arquivo>.rar <pathdestino> # Opção 1
```

```sh
unrar x <arquivo>.rar # Opção 2
```

## Compactar arquivos

### tar.gz - Opção 1

```sh
tar -cvzf <arquivo>.tar.gz <arquivo ou pasta a compactar>
```

### tar.gz - Opção 2

```sh
tar -cvf <arquivo>.tar <arquivo ou pasta a compactar>
```

```sh
gzip -9 <arquivo>.tar
```

### tar.bz2 - Opção 1

```sh
tar -cvjf <arquivo>.tar.bz2 <arquivo ou pasta a compactar>
```

### tar.bz2 - Opção 2

```sh
tar -cvf <arquivo>.tar <arquivo ou pasta a compactar>
```

```sh
bzip2 <arquivo>.tar
```

### tar.xz

```sh
tar -cvJf <arquivo>.tar.xz <arquivo ou pasta a compactar>
```

### zip

```sh
zip <arquivo>.zip <arquivo ou pasta a compactar> # Opção 1
```

```sh
zip -r <arquivo>.zip <arquivo ou pasta a compactar> # Opção 2
```

### rar

```sh
rar a <arquivo>.rar <arquivo ou pasta a compactar>
```

## Desativar temporariamente um dispositivo de entrada

```sh
xinput list # lista os dispositivos de entrada
```

```sh
xinput float <id> # Desativa temporariamente o dispositivo com o id informado
```

```sh
xinput reattach <id> <slave keyboard> # ativa o dispositivo com o id informado e com o numero slave keybord informado
```

## Desativar permanentemente um dispositivo de entrada

```sh
sudo cp /etc/default/grub /etc/default/grub.original # Cria um arquivo de backup para reverter o processo
```

```sh
sudo nano /etc/default/grub # Localize a linua 'GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"' e substitua por 'GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.nokbd"'
```

```sh
sudo update-grub
```

## Reverter o procedimento anterior

```sh
sudo cp /etc/default/grub.original /etc/default/grub
```

```sh
sudo update-grub
```

## Listar Processos Abertos

```sh
top
```

## Listar portas usadas no linux

```sh
netstat -antp
```

## Listar aplicações de uma porta expecífica

```sh
lsof -w -n -i tcp:<porta> # Opção 1
```

```sh
fuser -n tcp <porta> # Opção 2
```

```sh
netstat -anp | grep :<porta> # Opção 3
```

## Matar Processo com PID

```sh
kill -9 <pid>
```

## Matar Processo com nome

```sh
killall <nome do processo>
```

## Instalar flex e bison

```sh
sudo apt install flex bison
```

```sh
sudo apt install libfl2 libfl-dev
```

## Ver tamanho usado de pasta / arquivo

```sh
du -hs <arquivo>
```

## Ver Tamanho livre das partições

```sh
df -h
```

## Verificar se o servidor gráfico é X11 ou Wayland

```sh
echo $XDG_SESSION_TYPE
```


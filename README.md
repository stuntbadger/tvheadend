guide 
-----

sudo apt-get update; sudo apt-get upgrade

curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh

sudo usermod -aG docker pi

mkdir tvheadend 
mkdir record 

docker run --restart=always --name tvheadend -p 9981:9981 -p 9982:9982 -v /home/pi/tvheadend:/config -v /home/pi/tvheadend/record:/records --privileged romainf/rpi-tvheadend

wget https://github.com/OpenELEC/dvb-firmware/blob/master/firmware/dvb-demod-si2168-02.fw?raw=true -O /lib/firmware/dvb-demod-si2168-02.fw
wget http://palosaari.fi/linux/v4l-dvb/firmware/M88DS3103/3.B/dvb-demod-m88ds3103.fw -O /lib/firmware/dvb-demod-m88ds3103.fw
wget https://github.com/OpenELEC/dvb-firmware/blob/master/firmware/dvb-demod-si2168-b40-01.fw -O /lib/firmware/dvb-demod-si2168-b40-01.fw

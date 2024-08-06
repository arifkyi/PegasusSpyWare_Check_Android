# SpyWare Check for Android

<b>you can see the video here:</b>

https://www.youtube.com/watch?v=Yk7pUPjlU4U

<b>  Background : </b>

Although the title is about Pegasus spyware, but the scope is also checking others spyware, such as Cytrox,
Stalkerware, RCS Lab etc.


# Enable the ADB Mode in your android 

<b> before Enable the ADB Mode in your Android, you need to enable the USB debug mode 
  with the guidance in this video:</b> <br> 
  https://www.youtube.com/shorts/6yeNltxuEiQ <br>

After enable the USB Debug mode then we good to go for ADB Mode in Android, then follow these steps <br>

1. connect your android phone to your laptop with cable data
2. run this command: "adb tcpip 5555"
3. and run this again : "adb connect YourAndroidWlanIP"
4. unplug the cable


# Prepare the verification tools
<b> Pull Image from Docker </b>

https://docs.mvt.re/en/latest/docker/

git clone https://github.com/mvt-project/mvt.git

cd mvt

docker build -t mvt .

docker run --rm -it --network host mvt

or if you want to mounting directory you can use this command <br>
docker run --rm -it --network host -v "$PWD:/mnt/tmp" mvt
# Alternatively if The DockerFile above not Work For Build
Pull from my Image Repository https://hub.docker.com/r/arifkyi/mvt to build

docker run --rm -it --network host -v "$PWD:/mnt/tmp" arifkyi/mvt
the rest of the steps are the same
# Usage

<b> Now download the IOCS STIX files </b>

mvt-android download-iocs

# If just in case in the future:
download IOCSnot work, i already backup in this repository in Zip file Android_IOCS_STIX2.zip

<b> indicators "NSO Group Pegasus Indicators of Compromise" to </b>

/root/.local/share/mvt/indicators/raw.githubusercontent.com_AmnestyTech_investigations_master_2021-07-18_nso_pegasus.stix2

<b> indicators "Cytrox Predator Spyware Indicators of Compromise" to </b>

/root/.local/share/mvt/indicators/raw.githubusercontent.com_AmnestyTech_investigations_master_2021-12-16_cytrox_cytrox.stix2

<b> indicators "RCS Lab Spyware Indicators of Compromise" to </b> 

/root/.local/share/mvt/indicators/raw.githubusercontent.com_mvt-project_mvt-indicators_main_2022-06-23_rcs_lab_rcs.stix2

<b> indicators "Stalkerware Indicators of Compromise" to </b> 

/root/.local/share/mvt/indicators/raw.githubusercontent.com_AssoEchap_stalkerware-indicators_master_generated_stalkerware.stix2
***************************************

<b> Check one by one by fire these commands below:</b> </br>

mvt-android check-adb --serial AndroidWlanIP:5555 --output /home/output --iocs [full path name of the stix file you need to look from the output of command above]

<b> example if you want to check the Pegasus Spyware : </b> <br>

mvt-android check-adb --serial 192.168.1.21:5555 --output /home/output --iocs /root/.local/share/mvt/indicators/raw.githubusercontent.com_AmnestyTech_investigations_master_2021-07-18_nso_pegasus.stix2


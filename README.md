# SpyWare Check for Android

<b>you can see the video here:</b>

https://www.youtube.com

<b>  Background : </b>

Although the title is about Pegasus spyware, but the scope is also checking others spyware, such as Cytrox,
Stalkerware, RCS Lab etc.


<b> Enable the ADB Mode in your android </b>

<b> Enable the ADB Mode in your Android with this video:</b> https://www.youtube.com/shorts/6yeNltxuEiQ <br>

after you enable the ADB Mode in your Android, then follow these steps <br>

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

# Usage

<b> Now download the IOCS STIX files </b>

mvt-android download-iocs

<b> indicators "NSO Group Pegasus Indicators of Compromise" to </b>

/root/.local/share/mvt/indicators/raw.githubusercontent.com_AmnestyTech_investigations_master_2021-07-18_nso_pegasus.stix2

<b> indicators "Cytrox Predator Spyware Indicators of Compromise" to </b>

/root/.local/share/mvt/indicators/raw.githubusercontent.com_AmnestyTech_investigations_master_2021-12-16_cytrox_cytrox.stix2

<b> indicators "RCS Lab Spyware Indicators of Compromise" to </b> 

/root/.local/share/mvt/indicators/raw.githubusercontent.com_mvt-project_mvt-indicators_main_2022-06-23_rcs_lab_rcs.stix2

<b> indicators "Stalkerware Indicators of Compromise" to </b> 

/root/.local/share/mvt/indicators/raw.githubusercontent.com_AssoEchap_stalkerware-indicators_master_generated_stalkerware.stix2
***************************************

Check one by one by fire these commands below:

mvt-ios check-backup --output /home/output/ /home/cases/ --iocs   <full path name of the stix file you need to look from the output of command above>

example if you want to check the Pegasus Spyware : <br>

mvt-android check-adb --serial 192.168.1.21:5555 --output /home/output --iocs 5. /root/.local/share/mvt/indicators/raw.githubusercontent.com_AmnestyTech_investigations_master_2021-07-18_nso_pegasus.stix2


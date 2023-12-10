# NTP

<h2>Description</h2>
Configure NTP on R1, R2, and R3. Verify results.

<h2>Environments Used </h2>

- <b>Cisco Packet Tracer</b> (2.2.43) <br />

- <b>Cisco IOS C2900 Software Version 15.1(4)M5<br />

<h2>Diagram </h2>
<img src="https://i.imgur.com/neRWePh.png" height="80%" width="80%" />

<h2>Walk-through:</h2>
Configure R1 with clock timezone settings, 1.1.1.1 NTP server, master and authentication.
R1#clock set 12:00:00 Dec 30 2020
R1#conf t<br />
R1(config)#clock timezone EST -5<br />
R1(config)#ntp server 1.1.1.1<br />
R1(config)#ntp master<br />
R1(config)#ntp authenticate<br />
R1(config)#ntp authentication-key 1 md5 <br />
R1(config)#ntp trusted-key 1<br />
<img src="https://i.imgur.com/crPBeGE.png" height="80%" width="80%" /> <br />
<br />
<br />
Configure on R2 and R3 with clock timezone settings, R1 interface as NTP server, and authentication to R1's NTP server. <br />
R2#clock set 12:00:00 Dec 30 2020<br />
R2#conf t<br />
R2(config)#clock timezone EST -5<br />
R2(config)#ntp authenticate<br />
R2(config)#ntp authentication-key 1 md5 ccna<br />
R2(config)#ntp trusted-key 1<br />
R2(config)#ntp server 192.168.12.1 key 1<br />
R2(config)#ntp update-calendar<br />
R2 Results:
<img src="https://i.imgur.com/KhaU1TS.png" height="80%" width="80%" /> <br />
R3 Results:
<img src="https://i.imgur.com/wyZO8PN.png" height="80%" width="80%" /> <br />

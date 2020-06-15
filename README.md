# tweetStats
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/1451288d3ab84c5385cb3b5f75f37eb0)](https://www.codacy.com/manual/mwoolweaver/tweetStats?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=mwoolweaver/tweetStats&amp;utm_campaign=Badge_Grade) [![Codacy Badge](https://api.codacy.com/project/badge/Coverage/1451288d3ab84c5385cb3b5f75f37eb0)](https://www.codacy.com/manual/mwoolweaver/tweetStats?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=mwoolweaver/tweetStats&amp;utm_campaign=Badge_Coverage)
Send a daily tweet with your Pi-Hole statistics and other system information!

## How to use
### Prerequisites

*   Pi-hole

    *   install Pi-hole <https://install.pi-hole.net>
    *   `api_path` = Path to <http://pi.hole/admin/api.php> of Pi-Hoe (if you're running this script from the machine running Pi-hole that URL should work)

*   Twitter

    *   Tokens: Create an application [here](https://apps.twitter.com/)

*   ipstack.com api key

    *   `access_key` = get this from <https://ipstack.com/signup/free>
### Guided Setup (install script)

```bash
wget https://raw.githubusercontent.com/mwoolweaver/tweetStats/master/install.sh
chmod +x install.sh
./install.sh
```
### Manual Setup (no install script)

1.  `git clone https://github.com/mwoolweaver/tweetStats.git`
2.  Install Python 3
3.  `pip3 install -U -r requirements.txt`
4.  `cp config.json.example config.json` and adjust it
5.  Run it! `python3 tweetStats.py` or `python3 tweetStats.py -h` for help
6.  ???
7.  Profit
## cmd line args for testing

*   -db will print the tweet to be sent and all other variables that are used in the proccess.
*   -dbl will test your twitter credentials to test a successful login.
*   -dbp will make sure the pi-hole api can be reached.
## Cronjob
### Use Install Script
or 
### Manual Setup

creaate file ```/etc/cron.daily/tweetStats``` with the following contents

```bash
#!/bin/bash
cd /path/to/folder/containing/tweetStats.py/
python3 ./tweetStats.py >> tweetStats.txt

```

test cron job w/ `sudo run-parts /etc/cron.daily`
## How it looks

https://twitter.com/sundered_heart_/status/1202952580504141824

```bash
Tweet 1
#PiHoleStats
Blocklist Size: 761,313
Total Queries: 25,137
Queries Blocked: 0|0%
Queries Forwarded: 509
Queries Cached: 24,628
Unique Clients: 1
Privacy Level: 2
Gravity Last Updated: 2019-07-16 18:03
#Python

 Tweet 2
#SystemStats
CPU Load AVG: 0.08, 0.02, 0.01
Ram Usage: 483M/1G|39.3%
Disk Usage: 9G/28G|32.14%
Network Interfaces: ens4, tun0, tun1
Kernel && OS: Linux-5.0.0-1010-gcp-x86_64-with-Ubuntu-19.10-eoan
Boot Time: 2019-07-16 18:12
#Ubuntu

 Tweet 3
#NetStats
Ping: 38.68 ms
Down/Up Speed: 994.81 Mbps/409.19 Mbps
Data Used (dl/ul): 390.41 MB/144.5 MB
IP: 35.222.xx.xx
ISP: Google Cloud
Region: Virginia
Continent: North America
Share: http://www.speedtest.net/result/8438272507.png
#Speedtest
```
![example](.github/tweetStats.gif)

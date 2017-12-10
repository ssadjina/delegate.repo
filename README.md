# delegate.repo
Pool delegate for RISE/OXY

# Prerequisites
```
sudo apt-get install python3
sudo apt-get install python3-requests
sudo apt-get install curl
```

## Download / clone repo
```
git clone https://github.com/ssadjina/delegate.repo
```
Rename the directory (optional).

## Configuration
Edit liskpool.py and modify the first lines with your settings:

- NODE: the node where you get forging info (e.g. https://wallet.rise.vision)
- NODEPAY: the node used for payments (also requires the port, e.g. http://localhost:5555 for RISE or http://localhost:10000 for OXY)
- PUBKEY: your delegate pubkey (can be found via explorer, e.g. https://explorer.rise.vision/)
- PERCENTAGE: percentage to distribute
- TRANSACTIONFEE: specify the transaction fee amount
- RISEPERDAY: number of tokens forged per day on average (e.g. for OXY: 143.2835820895522388)
- MINPAYOUT: the minimum amount for a payout
- SECRET: your secret
- SECONDSECRET: your second

Modify the text output as needed (now RISE, change to OXY, for example).

Edit batch.sh to include the correct directories, then change the access permissions:
```
chmod 774 batch.sh
```

Now run the script once and save (enter "y" afterexecution):
```
sudo python3 liskpool.py
```

## Website
Install apache:
```
sudo apt-get install apache2
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
```
Go into docs directory and copy it:
```
sudo cp ./* /var/www/html/
cd /var/www/html/
```
Edit app.js. Go to the line
```
$http.get ('https://wallet.shiftnrg.org/api/deleg...
```
(or similar) and make sure it's correct for your coin (e.g. https://wallet.rise.vision/api/delegates/get?username=[POOL NAME]).
Then edit index.html to your liking. Find inspiration at http://rise.the-viking.online.

## Automate
```
crontab -e
```
and add
```
0 * * * * ~/[DELEGATE_DIRECTORY]/batch.sh >> ~/[DELEGATE_DIRECTORY]/batch.log 2>&1
```
making sure to replace [DELEGATE_DIRECTORY] with the name you gave it ;)

## License
Copyright 2017 Davide Gessa

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.


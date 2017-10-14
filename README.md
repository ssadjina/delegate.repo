# Shift pool distribution software
This software is created by lisk delegate "dakk", please consider a small donation if you
use this software: "2324852447570841050L" for lisk or "7725849364280821971S" for shift.
@Seatrips also likes beer :) "2675385658327038858S" for the changes

## Prerequisitions
```
sudo apt-get install python3
sudo apt-get install python3-requests
sudo apt-get install curl
```
## Download / clone repo
```
git clone https://www.github.com/seatrips/delegatepool.seatrips.nl
```
then rename folder to your own pool site

## Configuration
Fork this repo; edit liskpool.py and modify the first lines with your settings:

- PUBKEY: your delegate pubkey
- PERCENTAGE: percentage to distribute
- SECRET: your secret
- SECONDSECRET: your second
- NODE: the lisk node where you get forging info
- NODEPAY: the lisk node used for payments
- MINPAYOUT: the minimum amount for a payout

- You will also need to edit app.js in the /docs or /html folder

Now edit /docs/index.html and customize the webpage.
When using a dedicated server just put the content of docs in /var/www/html

Finally edit poollogs.json and put in lastpayout the unixtimestamp (http://www.unixtimestamp.com/) of your last payout or the
date of pool starting and donations adress and amount then copy to /docs folder or /html folder when using your own dedicated server


## Running it

`python3 liskpool.py`

It produces a file "payments.sh" with all payments shell commands. Run this file with:

`bash payments.sh`

The payments will be broadcasted (every 10 seconds). At the end you can move your generated
poollogs.json to docs/poollogs.json and send the update to your git repo.

To display the pool frontend, enable docs-site on github repository settings.


## Batch mode

The script is also runnable by cron using the -y argument:

```
python3 liskpool.py -y`
```
or
```
bash batch.sh
```

This 'batch.sh' file will run liskpool, then payments.sh and copy the poollogs.json
in the docs folder.

## For easy documentation for running this on your own server 
check https://github.com/seatrips/easy-apache2-site


## License
Copyright 2017 Davide Gessa

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.


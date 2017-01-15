# shift-checker
This script checks the status of your Shiftnrg Delegate by using PHP.<br>
Feel free to rewrite in Python or Bash. 
 
This script will also check whether your node has forked or not.<br>
When forked, it will stop Shift, restore to previous snapshot, and start Shift again.
  
There are some echo lines in this file.<br>
When you redirect output to a log file in your crontab, these lines will show up. <br>
See section Example crontab for more information.

Be sure to run this script after:
* You have installed shift-snapshot
* You have created a snapshot with shift-snapshot

## Prerequisites
Be sure that your php.ini allows passthru(). It's default that it does though, so just check if this script is not working.
```
sudo apt install php php-cli php-mbstring php-sqlite3
```
* shift-snapshot.sh: https://github.com/mrgrshift/shift-snapshot

## Installation
You can clone this into every directory of your choosing. I usually just clone it into my home folder.
```
git clone https://github.com/lepetitjan/shift-checker.git
```
* Change settings inside checkdelegate.php to match your needs
* Edit your crontab with the example below

## Example crontab
```
* * * * * php ~/shift-checker/checkdelegate.php >> ~/shift-checker/logs/checkdelegate.log 2>&1
```

## Telegram bot
Shift-Checker comes with Telegram functionality which will allow shfit-checker to send you a message if anything requires your attention. It's very easy to set up: 
* Open Telegram and start a conversation with: <b>userinfobot</b>
* Put your ID inside variable $telegramId. 
```
$telegramId = "12345678";
```
* Start a conversation with: <b>botfather</b>
* Say: /newbot
* Tell botfather your bot's name
* Tell botfather your bot's username
* Botfather will say "Congratulations!" and give you a token
* Put your token inside variable $telegramApiKey. 
```
$telegramApiKey 	= "1122334455:AAEhBOweik6ad9r_QXMENQjcrGbqCr4K-bs";
```
* Edit the telegram toggle (true/false)
* Start a conversation with your bot (username) to enable communication between you two

## Transfer balance
Shift-Checker now comes with the option to transfer the balance from your delegate to your private wallet when $maxBalance is reached.<br>
```
$checkBalance		= false;							// Enable (true) or disable (false) the balance checker
$nodeAddress 		= "http://127.0.0.1:9305";			// Address of your node to check your balance and send transactions omitting final /
$myDelegate 		= "";								// SHIFT address of your delegate
$firstPass			= "";								// Passphrase of your delegate
$secondPass			= "";								// Your second passphrase if you have it..otherwise leave blank!
$myPrivateWallet	= "";								// SHIFT address of your private wallet
$maxBalance			= 10;								// Max of balance to keep in your delegate wallet
```

## Common errors
Some users get the error:
```
sudo: no tty present and no askpass program specified
```
To fix it, follow these steps:
```
1. $ sudo nano /etc/sudoers.d/yourusername
2. Insert this: yourusername ALL=(ALL) NOPASSWD:ALL
```
Now your user does not have to type a sudo password anymore when shift-snapshot asked for one.

## Contact 
* Twitter: [@lepetitjan](https://twitter.com/lepetitjan) 
* Shiftnrg Slack: https://shiftnrg.slack.com/team/jan 

## Donations
Do you like/use my script(s)? Please consider donating the amount of a cup of coffee :-)<br>
SHIFT: 7970982857025266480S<br>
BTC: 1GbAWBiGyuybXJcjtyTvtH6hB5iezXNVdP

## Contributors
Seatrips (create snapshot when status is okay)
* Twitter: [@seatrips<br>](https://twitter.com/seatrips)
* Shiftnrg Slack: https://shiftnrg.slack.com/team/seatrips

Mrgr (Shift snapshots)
* Shiftnrg Slack: https://shiftnrg.slack.com/team/mrgr
* Github: https://github.com/mrgrshift

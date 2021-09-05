py-feedr  
=============  
  
feedr is a non-asynchronous, WTFPLv2-licensed Python parser to tweet the latest updates from multiple RSS feeds.  
  
__Sorry, what does it do?__  
  
feedr tweets the newest element from a RSS feed to the Twitter account of your choice, and stores it in a database.  
  
It's pretty easy: you _feed_ it with a list with links to RSS feeds, then it does a bit of formatting to create a nice, readable message, and it _tweets_ it.  
  
__A note on feedr's behaviour__  
  
feedr tries to stick as much as possible to the RSS feeds it handles but avoids redundancy, all of this without taking too much system resources.  
  
To keep it simple and do just that, it will only care about the latest element in a RSS feed. If it is found to be a duplicate of the last (n-1) element that feedr has already handled, then it will only keep this new element and delete the previous one on Twitter (and in the database).  
  
__Not convinced?__  
  
If you're unsure whether feedr is the solution you need, check out [this Twitter account](https://twitter.com/M157q_News_RSS) which uses feedr.  
  
### Installation  
----------------  
  
feedr can either be installed through pip (stable version) or manually (dev or stable version).  
  
Using pip:  
```  
$ (sudo) pip install py-feedr  
```  
  
Manually:  
  
* Stable version: download the [latest release version](https://github.com/gregorycoleman/py-feedr/releases/latest)  
* Development version: clone this git repository (`$ git clone https://github.com/M157q/py-feedr.git`)  
  
Then run `$ (sudo) python setup.py install` to install imgur-scraper.  
  
### Requirements  
----------------  
  
Installation requirements:  
  
* Python 3  
* [feedparser](https://pypi.python.org/pypi/feedparser)  
* [requests](https://github.com/kennethreitz/requests)  
* [twitter](https://github.com/sixohsix/twitter)  
  
Runtime requirements:  
  
* A [Twitter account](https://twitter.com/signup)  with valid [API credentials](https://apps.twitter.com).  
  
### Usage  
---------  
  
feedr needs to be given an [INI configuration file](https://github.com/M157q/py-feedr/blob/master/bin/feedr.ini), which contains amongst other parameters a path to a JSON feedlist of RSS feeds that follows the [example format](https://github.com/M157q/py-feedr/blob/master/bin/feedlist.json).  
  
Then simply invoke feedr:  
  
```bash  
usage: feedr [-h] config  
  
positional arguments:  
  config      path to the feedr configuration file  
  
  optional arguments:  
    -h, --help  show this help message and exit  
```  
  
You can setup a cron job that runs every minute if you need to call feedr regularly:  
`*/1 * * * * /usr/bin/bash -c "/usr/bin/python3 ${FEEDR_DIR}/bin/feedr ${FEEDR_DIR}/bin/feedr.ini" >> /home/feedr/feedr.log 2>&1`  
  
### License  
-----------  
  
py-feedr is licensed under the WTFPLv2 license; refer to the LICENSE file.  

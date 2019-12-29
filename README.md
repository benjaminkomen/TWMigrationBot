# TWMigrationBot

## Supported environments
This bot is only designed to work on Ubuntu 16.04 using Python 3.7.3. Limited support will be provided for other operating environments.


## Setting up

### Pywikibot
To start, download pywikibot. Instructions can be found [here](https://www.mediawiki.org/wiki/Manual:Pywikibot/Installation#Install_Python).
For Unix-based operations systems like Ubuntu or Mac OS X you can do the following:
- have Python installed (i.e. via `apt-get` or `brew`)
- execute `pip install requests` in your terminal
- create a directory `~/github.com` and navigate to it in your terminal
- execute `git clone --recursive --branch stable https://gerrit.wikimedia.org/r/pywikibot/core.git pywikibot`
- execute `cd pywikibot` and `git pull origin stable --recurse-submodules` 

To use pywikibot, ensure pywikibot.pywikibot is in the PYTHONPATH.

```export PYTHONPATH="$PYTHONPATH:PATH_TO_PYWIKIBOT"```
    
This export statement could be added to your `~/.zshrc` by doing:
- execute `~/.zshrc` and add the line `export PYTHONPATH="${PYTHONPATH}:~/github.com/pywikibot"`
- reload your changed Bash configuration `. ~/.zshrc`
- if in a later step you get an error "raise ValueError, 'unknown locale: %s' % localename" then you need to add
the following lines to your bash configuration file as well:
```$bash
export LC_ALL=en_US.UTF-8
export LANG=en_US.UTF-8
```

Now pywikibot is installed on your machine, we need to configure it to connect
to TibiaWiki:
- still in your pywikibot folder execute `python pwb.py generate_family_file`
- For the url enter: `https://tibia.fandom.com/wiki/Main_Page tibiawiki`
- For the short name enter: `tibiawiki`
- Don't make interwiki links, just be happy with the one `en` language option
- Now execute `python pwb.py generate_user_files`
- For the family of sites enter: `tibiawiki` (if it's not in the list the generation of the family file failed)
- For the language code enter: `en`
- For the username enter your bot's username
- Enter `y` when asked to add a bot password
- Enter your bot name again
- Enter your bot password

### Helpful configurations
In user-config.py some settings can be changed to make the bot operate faster: these should be reasonably high to avoid overloading the server.

    minthrottle = 0
    maxthrottle = 5
    put_throttle = 2

### Running TWMigrationBot
Now the Pywikibot is successfully set up, we can setup the TWMigrationBot:
- navigate to a folder where you want to clone, e.g. `cd ~/github.com`
- execute `git clone git@github.com:Sixish/TWMigrationBot.git`

Normally dependencies are installed in e.g. `/usr/local/lib/python3.7/site-packages`.
However, you want the TWMigrationBot to use the pywikibot dependency from the location
where you installed and configured it.
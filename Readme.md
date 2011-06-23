#Symbox

I’ve always had trouble keeping various files synced on my three computers. This makes setting up projects that I am working on a chore. That’s where Dropbox comes in. After figuring out that I can just symlink my projects to Dropbox, I rarely have to setup anything. It still felt a bit redundant though, so I built a utility that automates the setup of all the links between folders on Dropbox and my various computers.

Symbox is a script that lets you symlink folders without thinking about it. It requires nodejs, which you can get here. If you have npm you can simply run

	npm install symbox -g

Otherwise you can install npm in one line and then run the above command.

	curl http://npmjs.org/install.sh | sh

Then you want to locate your symbox config by running.

	symbox --config

This will return the location of the config for easy editing.

The default config should resemble the following.

	{
		"root": "~/Dropbox",
		"sync": {
			// provide a key of the relative folder path to the dropbox root
			// and a value of the folder on the current computer
			// "foo": "~/Desktop/foo"
		}
	}

Under the ‘sync’ object you’ll want to add any folders that you want to move into Dropbox and symlink back into place. A simple example of this for me is my nginx server configuration. In order to sync my nginx configuration on all my computers I setup my Symbox config like so.

	{
		"root": "~/Dropbox",
		"sync": {
			"nginx": "/usr/local/etc/nginx"
		}
	}

After I have modified my Symbox config, I can update my folders by running the following in terminal.

	symbox

Symbox will then move the nginx folder to my “root” Dropbox folder and add the symlink for me. All I have to do now is copy my configuration file to my other computers and run through the previous steps then voila my nginx config is the same on all my computers!
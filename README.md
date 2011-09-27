Add Support for HTTPS exposed Git Repositories to OSX Lion Server

These two configuration files add remote git support to any OSX Lion Server installation. Simply put these files into your _/etc/apache2/_ directories and tweak the file paths in _http_git.conf_. On my local system, i'll use _/Volumes/Daten/git_ as the storage location for my repositories. You may decide to use another place.

After you made your modifications on these files, the web application should be started using the following command on your OSX Lion Server:

      webappctl start de.reswi.git.plist

To create a new repository on your server, execute the following commands:

       mkdir /Volumes/Daten/git
       cd /Volumes/Daten/git
       git init --bare newRepository.git
       chown -R _www:_www newRepository.git

On your client side, i recommend to add additional git options:

       git config --global http.sslverify false
       git config --global http.postBuffer 512000000

You may access the new repositories like this:
   
       git clone https://user@local.server/git/newRepository.git

Have fun.

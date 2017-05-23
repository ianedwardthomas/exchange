HowTo Install
=============

__WARNING: under construction__

First  create a boundless directory:
```bash
mkdir ~/git/boundless ; cd $_
```

RMIT blocks port 9418 used by git protocol so we use this workaround:
```
git config --global url."https://".insteadOf git://
```

Now we will checkout and install Maploom:
```
sudo npm config set prefix /usr/local
git clone https://github.com/ianedwardthomas/MapLoom.git —-branch prod # includes all maploop fixes
cd MapLoom
sudo npm install -g grunt-cli karma bower
sudo npm install
bower install
grunt watch -v
cd ..
```

Now install geonode (which includes all fixes):
```
git clone https://github.com/ianedwardthomas/geonode —-branch prod
```

Finally install prod version of exchange:
```
git clone https://github.com/ianedwardthomas/exchange.git —-branch prod2
```

Next change the ```GEOIP``` variable in the ```.env``` file to point to external address for your host, then:
```
cd exchange
docker-compose build
docker-compose up -d
```


Run the following command to see all the changes that have happened on prod branch since it was started:
```
git diff master...
```


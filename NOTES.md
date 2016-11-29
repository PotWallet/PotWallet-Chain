# *Notes*

- Having Node version 0.10.x is the key here.  Insight says it is based on 0.12.x or higher, but this isn't the case.
Simply installing node and npm will not do. You need to install nvm so you can set what node environment to build in.

NVM can be found here

    $ https://raw.githubusercontent.com/creationix/nvm/

I used the tutorial here

    $ https://www.liquidweb.com/kb/how-to-install-nvm-node-version-manager-for-node-js-on-centos-7/

When doing the install on CentOS.


## Simple changes

Now that the environment is applicable, we made our fork of reddcore public with the name changes made by Elazar.
This simply isn't enough as the package.json file in (I believe) api is looking for potcore.  So, to fix this,
when it error'd out, I simply did 

    $ mv potwallet-chain/node_modules/potchain-api/node_modules/reddcore potwallet-chain/node_modules/potchain-api/node_modules/potcore 

and moved on.

Inside the potwallet-chain/node_modules/potchain-api/node_modules/potcore directory there is networks.js.  This is where you setup the coin
information.  This information is found in the coins source.



## Problems

The chain syncs when running the start command against the executable script and makes it to 27% then errors complaining that the 'magic prefix'
no longer matches the chain.  This is around block 480,000.  The prefix set in networks.js works up until then, then simply stops.

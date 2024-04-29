#Update
sudo apt update
sudo apt upgrade -y

#Install Node.js & Angular
cd ~
curl -sL https://deb.nodesource.com/setup_18.x -o nodesource_setup.sh
sudo bash nodesource_setup.sh
sudo apt install nodejs
npm install -g @angular/cli@16

#Install ZAC
git clone https://github.com/openziti/ziti-console.git "${ZITI_HOME}/ziti-console"
cd "${ZITI_HOME}/ziti-console"
npm install
    export NODE_OPTIONS="--max-old-space-size=8192"
    --> Fixed heap out of memory
ng build ziti-console-lib
ng build ziti-console-node



sudo apt install tar hostname jq curl

PW: sHn4FDIBwrLv8BcTdChUUt0jF-9zKzN_
# Tutorials
Guia pessoal

## Como instalar o python no mac:
```console
#instalar o xcode.

#instalar o homebrew
#caso já tenha o homebrew instalado basta atualiza-lo:
brew update
brew upgrade

#intalar o pyenv pelo homebrew.
brew install pyenv
pyenv install -l #> para ver as versões disponíveis para o python!
pyenv install 3.5.2 #> instalando a versão mais recente até o momento.
pyenv global 3.5.2
python -V

#caso não funcione faça o seguinte:
vi ~/.bash_profile
#cole no arquivo:
if which pyenv > /dev/null; then eval "$(pyenv init -)"; fi
source ~/.bash_profile
python -V
```

## Como instalar o python no ubuntu
```console
# Verificar a versão do python
python -V

# Instalar as dependências do pyenv
sudo apt-get install -y make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev git

# Instalar as dependências do pandas
sudo apt-get install liblzma-dev

# Instalar o pyenv e copiar as 3 ultimas linhas da instalação
curl -L https://raw.githubusercontent.com/yyuu/pyenv-installer/master/bin/pyenv-installer | bash

# Como atualizar o pyenv
pyenv update

# Editar o arquivo bashrc e profile, colar as linhas copiadas, salvar, sair e reiniciar o terminal
gedit ~/.bashrc
export PATH="$HOME/.pyenv/bin:$PATH"
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"

gedit ~/.profile
export PATH="$HOME/.pyenv/bin:$PATH"
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"

# Para ver se esta tudo certo basta digitar:
# Caso o comando abaixo não funcione reinicie a máquina e tente novamente...
pyenv

# Para listar as versões de python estão instaladas basta digitar:
pyenv versions

# Para listar as versões possíveis basta digitar:
pyenv install -l

# Para instalar o python desejado e torna-lo padrão basta digitar:
pyenv install 3.6.1
pyenv global 3.6.1

# Caso esteja tudo correto ao digitar o comando abaixo a versão que acabamos de instalar estará com um asterisco:
pyenv versions
```

## Como criar projetos em django usando pipenv
```console
mkdir pasta_do_projeto
cd pasta_do_projeto

# Para instalar o pipenv:
  # MAC
  brew install pipenv
  # Linux
  pip install --upgrade pip
  pip install pipenv

pip install --upgrade pip
pip install --upgrade pipenv
pipenv --three
pipenv install django
pipenv install python-decouple
pipenv install dj-database-url
pipenv install dj-static
pipenv install django-extensions
pipenv install django-test-without-migrations
pipenv install django-debug-toolbar
pipenv shell
django-admin startproject nome_do_projeto .
#alias manage='python $VIRTUAL_ENV/../manage.py'
cd nome_do_projeto/
manage startapp core

#git:
git init
#Configurar o arquivo .gitignore
git add .gitignore
git commit -m "Initial commit"
git add .
git commit -m "Import project"
```


## Como criar projetos em django usando virtualenv e pip requirements
```console
mkdir pasta_do_projeto
cd pasta_do_projeto
python -m venv .venv
source .venv/bin/activate
which python #isso é para confirmar se está usando o python certo
pip install --upgrade pip
pip install django
pip install python-decouple
pip install dj-database-url
pip install dj-static
pip install django-extensions
pip install django-test-without-migrations
pip install django-debug-toolbar
pip freeze > requirements.txt
django-admin startproject nome_do_projeto .
#alias manage='python $VIRTUAL_ENV/../manage.py'
cd nome_do_projeto/
manage startapp core

#git:
git init
#Configurar o arquivo .gitignore
git add .gitignore
git commit -m "Initial commit"
git add .
git commit -m "Import project"
```

## Deploy no heroku
```console
heroku login
heroku apps:create nome_do_projeto
heroku plugins:install heroku-config
heroku config:push -a nome_do_projeto
git push heroku master --force
heroku run python manage.py migrate

#github:
git remote add origin https://github.com/sandrofolk/nome_do_projeto.git
git pull origin master
git push -u origin master

#Ativar envio de email no heroku
#(com cartão de crédito)heroku addons:create send grid:starter
#(sem informar cartão)Fazer conta no site do sendgrid(www.sendgrid.com)
heroku config:set EMAIL_BACKEND=django.core.mail.backends.smtp.EmailBackend EMAIL_HOST=smtp.sendgrid.net EMAIL_PORT=587 EMAIL_USE_TLS=True EMAIL_HOST_USER=[USERNAME CRIADO NO SENDGRID.COM] EMAIL_HOST_PASSWORD=[PASSWORD CRIADO NO SENDGRID.COM]
```

---

## FRONTEND

Visualizar limite dos objetos:
 - Abra o console do navegador e cole o código abaixo...
```
javascript: (function() { var elements = document.body.getElementsByTagName(''); var items = []; for (var i = 0; i < elements.length; i++) { if (elements[i].innerHTML.indexOf(' { background:#000!important;color:#0f0!important;outline:solid #f00 1px!important; background-color: rgba(255,0,0,.2) !important; }') != -1) { items.push(elements[i]); } } if (items.length > 0) { for (var i = 0; i < items.length; i++) { items[i].innerHTML = ''; } } else { document.body.innerHTML += '<style>* { background:#000!important;color:#0f0!important;outline:solid #f00 1px!important; background-color: rgba(255,0,0,.2) !important; }\             * * { background-color: rgba(0,255,0,.2) !important; }\             * * * { background-color: rgba(0,0,255,.2) !important; }\             * * * * { background-color: rgba(255,0,255,.2) !important; }\             * * * * * { background-color: rgba(0,255,255,.2) !important; }\             * * * * * * { background-color: rgba(255,255,0,.2) !important; }\             * * * * * * * { background-color: rgba(255,0,0,.2) !important; }\             * * * * * * * * { background-color: rgba(0,255,0,.2) !important; }\             * * * * * * * * * { background-color: rgba(0,0,255,.2) !important; }</style>'; } })();
```

## VueJS 2

### Instalação

#### Linux
```console
# Primeiro vamos ter que instalar o nvm que é o gerenciador de versões do node
# https://github.com/nvm-sh/nvm
wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/VERSAO_ATUAL/install.sh | bash

# Fechar e abrir o terminal
# Para verificar se deu certo rodar o seguinte comando:
command -v nvm
# Resultado deve ser "nvm"

# Para verificar as versões disponíveis:
nvm ls-remote

# Para instalar uma versão específica:
nvm install vx.x.x
# ou
nvm install --lts
# Prefira a versão LTS

# Para verificar as versões instaladas:
nvm ls

# Instalar o Vue CLI:
# https://cli.vuejs.org/guide/installation.html
npm install -g @vue/cli
```

### Criando projetos em VueJS2
```console
# Pelo terminal digite o seguinte comando de dentro da pasta de projetos:
vue ui
# ou então usando linha de comando:
vue create nome-do-projeto

# Depois acesse a pasta do projeto e suba o servidor:
cd nome-do-projeto
yarn serve
ou
vue ui
```

### Consumindo Json
```console
# Você pode usar um serviço pronto:
https://jsonplaceholder.typicode.com/

# ou então pode subir um server local usando json-server:
https://github.com/typicode/json-server
```

Ferramenta WebStorm:  
https://www.jetbrains.com/webstorm/nextversion/

Instalar através do ToolBox:  
https://www.jetbrains.com/toolbox/app/

https://www.jetbrains.com/help/pycharm/installation-guide.html#toolbox

- Erro "external file changes sync may be slow the current inotify(7) watch limit is too low"
https://confluence.jetbrains.com/display/IDEADEV/Inotify+Watches+Limit

Erro:
> SyntaxError: Failed to load plugin 'unicorn' declared in '.eslintrc.js ...

É um erro de IDE se você estiver usando o JetBrains.
Você precisa definir manualmente o interpretador do "node" na configuração do ESLint e também dos comandos rápidos!

![Config. Projeto](captura-de-tela-de-2020-04-09-12-18-08.png)

![Config. Atalho](captura-de-tela-de-2020-04-09-14-46-53.png)

---

## CI / CD (Heroku + Gitlab + Django + VueJS)

Com seu projeto criado no GitLab contendo duas pastas, uma para o backend em Django e uma para o frontend em VueJS você deve criar dois apps no Heroku:
- nome-do-projeto-staging
- nome-do-projeto-production

Em seguida você deverá acessar suas configurações de conta do heroku e copiar o valor de sua API KEY:
https://dashboard.heroku.com/account

Feito isso vá para as configurações do projeto no GitLab na opção "CI / CD".  
Lá você deverá localizar a opção de variáveis e criar três variáveis com os seguintes nomes:  
HEROKU_API_KEY : Contendo o valor da chave da sua conta no Heroku que você copiou no passo anterior;  
HEROKU_APP_PRODUCTION : contendo o nome do aplicativo para produção (Ex .: nome-do-projeto-production);  
HEROKU_APP_STAGING : Contendo o nome do aplicativo para produção (Ex .: nome-do-projeto-staging).

Agora você deve iniciar o git Flow em seu repositório para que possa existir a branch "release".
```
# Dentro do repositório do projeto basta executar o seguinte comando:
git flow init
```

Agora vamos criar nosso arquivo ".gitlab-ci.yml" na raiz do projeto com o seguinte conteúdo:
```console
build:backend:
  image: python:3.8
  script:
  - python -V
  - pipenv shell
  - pipenv install
  - python manage.py test

build:frontend:
  image: node:stable
  cache:
    paths:
      - node_modules/
      - .yarn
  script:
  - yarn install --production
  - yarn test
  - yarn build
  artifacts: 
    paths: 
    - dist/

staging:
  stage: deploy
  script:
  - gem install dpl
  - dpl --provider=heroku --app=nome-do-projeto-staging --api-key=$HEROKU_API_KEY
  only:
  - master

production:
  stage: deploy
  script:
  - gem install dpl
  - dpl --provider=heroku --app=nome-do-projeto-production --api-key=$HEROKU_API_KEY
  only:
  - tags
```

---

## Como instalar ionic2 no MAC
```console
#Install Cordova
npm install -g cordova

#Install Ionic CLI
npm uninstall -g ionic
npm cache clean
npm install -g ionic
ionic info

#Install Typescript
npm install -g typescript

#Using NG2-Translate
npm install ng2-translate --save

#Start an App
ionic start --v2 myApp sidemenu

#Run app
cd myApp
ionic serve -l

#Add Android platform
ionic platform add android

#Add ios platform
ionic platform add ios

#Create Pages
ionic g page nome_da_pagina

#Tutorial
https://scotch.io/tutorials/build-a-mobile-app-with-angular-2-and-ionic-2

#Install JWT for Token
#npm install angular2-jwt

#Install Ionic Cloud
npm install @ionic/cloud-angular --save
```

## ELM:
```console
npm install -g elm
```

## Angular 4:
```console
# Como instalar:
## Instalar o node.js:
https://nodejs.org/
## Verificar se instalou:
node -v
## Instalar o CLI:
npm install -g @angular/cli
## Verificar se instalou:
ng -v
## Instalar o typescript:
npm install typescript -g
## Verificar se instalou:
tsc -v
## Instalar o json-server para mockar servidor local com arquivos json:
npm install -g json-server
## Para emular o servidor:
json-server db.json

# Como inicializar um projeto npm em um repositório existente:
npm init -f    # "-f" é para forçar os valores padrões... sem ele o terminal questiona os valores...

# Como criar um projeto novo em Angular usando o CLI:
ng new nome-do-projeto --prefix=sigla-do-projeto

# Como criar um novo componente usando o CLI
ng g c nome-do-componente

# Comando úteis:
npm start                       # Sobe um servidor do projeto na máquina
ng build --prod                 # Prepara a aplicação para ser enviada em produção
ng build --prod --bh=/nomexxx/  # Prepara a aplicação para ser enviada em produção em uma sub-pasta
python -m http.server           # Sobe um servidor http local para rodar a pasta dist

# Como instalar pacotes:
npm install --save nome_do_pacote        # "--save" instala para desenvolvimento e produção
npm install --save-dev nome_do_pacote    # "--save-dev" instala apenas para o modo de desenvolvimento
# Exemplo:
npm install --save @angular/animations@4.0.0  # "@4.0.0" serve para fixar a versão que deseja usar!
```

## Atom editor de texto
```console
# Packages uteis
autoclose-html
atom-typescript
```

## BuildOut Odoo10 no UbuntuServer 16.04:
```console
# Install pyenv
sudo apt-get update
sudo apt-get install -y make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev git
curl -L https://raw.githubusercontent.com/yyuu/pyenv-installer/master/bin/pyenv-installer | bash
sudo vi ~/.bashrc

# Coloque as 3 próximas linhas no .bashrc
export PATH="~/.pyenv/bin:$PATH"
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"

#fechar e abrir o terminal!

mkdir odoo10
cd odoo10
sudo apt-get install python-dev python-setuptools
sudo apt-get install python-virtualenv
sudo easy_install pip
virtualenv . --system-site-packages
bin/pip install -U pip zc.buildout
printf "[buildout]\n\nextends =  https://raw.githubusercontent.com/odoo-brazil/odoo-brazil-buildout/10.0/default.cfg" >> common.cfg
printf "[buildout]\n\nextends = common.cfg" >> buildout.cfg

sudo apt-get install -y tig binutils build-essential bzr ca-certificates cpp gcc dpkg-dev fontconfig fontconfig-config gir1.2-glib-2.0 git git-core git-man libapparmor1 libc-dev-bin libc6-dev libcloog-isl4 libcurl3-gnutls libdatrie1 libdbus-glib-1-2 libdpkg-perl libelf1 liberror-perl libexpat1-dev libfontconfig1 libfontenc1 libfreetype6 libfreetype6-dev  libhcrypto4-heimdal libheimbase1-heimdal libheimntlm0-heimdal libhx509-5-heimdal libice6 libidn11 libjpeg-dev libjpeg-turbo8 libjpeg-turbo8-dev libjpeg62 libjpeg8 libjpeg8-dev libjs-jquery libk5crypto3 libkeyutils1 libkrb5-26-heimdal libkrb5-3 libkrb5support0 libldap-2.4-2 libldap2-dev libltdl7 libmpfr4 liborc-0.4-0 libpciaccess0 libpixman-1-0 libpng12-dev libpq-dev libpq5 libroken18-heimdal libsasl2-2 libsasl2-dev libsasl2-modules libsm6 libssl-dev libssl-doc libsvn1 libwind0-heimdal libxml2 libxml2-dev libyaml-0-2 libyaml-dev linux-libc-dev make mercurial mercurial-common python-bzrlib python-configobj python-crypto python-dev python-gi python-httplib2 python-keyring python-pkg-resources python-simplejson python-wadllib python2.7-dev rsync shared-mime-info subversion python-dateutil python-feedparser python-ldap python-libxslt1 python-lxml python-mako python-openid python-psycopg2 python-pybabel python-pychart python-pydot python-pyparsing python-reportlab python-tz python-vatnumber python-vobject python-webdav python-werkzeug python-xlwt python-yaml python-zsi python-docutils python-psutil python-mock python-unittest2 python-jinja2 python-pypdf python-decorator python-requests python-passlib python-software-properties libxslt1-dev python-pip python-libxml2 libxmlsec1-dev openjpeg-tools libopenjpeg-dev zlibc zlib1g-dev liblcms2-dev libwebp-dev tcl8.5-dev tk8.5-dev python-tk screen libxrender1 libxt6 tar zip gzip  zlib1g xfonts-75dpi xfonts-base python-genshi python-cairo python-cairo-dev libcups2-dev python-cups node-less libffi-dev

bin/buildout
bin/start_odoo
```

## Util:

replace com expressão regular:
	(src|href)="((img|css|js).*?)"
	$1="{% static ''$2 %}"

# Tutorials
Guia pessoal

## Como instalar o python no mac:
```console
#instalar o xcode.
#instalar o homebrew
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

## Como criar projetos em django
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
heroku plugins:install git://github.com/ddollar/heroku-config.git
heroku config:push
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

## Util:

replace com expressão regular:
	(src|href)="((img|css|js).*?)"
	$1="{% static ''$2 %}"

# odoo 12

Ubuntu 18.04.4

```
git clone -b 12.0 git@github.com:odoo/odoo.git
cd odoo
pyenv local 3.7.X
python -m venv .venv
source .venv/bin/activate
sudo apt-get install libxml2-dev libxslt-dev python-dev libsasl2-dev libldap2-dev
pip install --upgrade pip
pip install -r requirements.txt
wget https://github.com/wkhtmltopdf/packaging/releases/download/0.12.6-1/wkhtmltox_0.12.6-1.bionic_amd64.deb
sudo dpkg -i wkhtmltox_0.12.6-1.bionic_amd64.deb
# caso falte alguma dependência rodar o comando abaixo e repetir o comando acima:
  sudo apt-get -f install
rm -R wkhtmltox_0.12.6-1.bionic_amd64.deb
```

Criar o arquivo ".odoorc" com o seguinte conteúdo:
<pre>
[options]
db_host=localhost
db_user=odoo
db_password=odoo
</pre>

Rodar o projeto:

```
./odoo-bin -c .odoorc
```

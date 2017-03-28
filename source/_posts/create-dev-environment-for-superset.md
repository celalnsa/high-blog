---
title: 创建Superset开发环境
date: 2017-03-27 21:55:40
tags: 
    - superset
    - python
categories:
    - 写代码
---

本篇文章记录如何创建一个superset的开发环境
[了解superset](https://github.com/airbnb/superset)

<!-- more -->

准备virtualenv
------------

创建一个virtualenv, ${superset_env}
```bash
virtualenv ${superset_env}
```
安装依赖, 参考末尾的[requirements.txt](#requirements.txt)
```bash
cd ${superset_env}
pip install -r requirements.txt
. bin/activate
```


cd到代码目录 举例: ${superset_source}
```bash
cd ${superset_source}
cd superset/static/assets
npm install
npm run prod
cd ${superset_source}
export PYTHONPATH=.:${PYTHONPATH}
```


跑起来
------------
```bash
cd ${superset_source}
superset/bin/superset runserver -p 12306
```

新的terminal
------------

```bash
cd ${superset_source}
. ${superset_env}/bin/activate
export PYTHONPATH=.:${PYTHONPATH}
superset/bin/superset runserver -p 12306
```


requirements.txt
------------

```
alembic==0.9.1
amqp==1.4.9
anyjson==0.3.3
appdirs==1.4.3
Babel==2.4.0
billiard==3.3.0.23
boto3==1.4.4
botocore==1.5.29
celery==3.1.23
cffi==1.10.0
click==6.7
colorama==0.3.7
cryptography==1.7.2
docutils==0.13.1
enum34==1.1.6
Flask==0.12
Flask-AppBuilder==1.8.1
Flask-Babel==0.11.1
Flask-Cache==0.13.1
Flask-Login==0.2.11
Flask-Migrate==1.5.1
Flask-OpenID==1.2.5
Flask-Script==2.0.5
Flask-SQLAlchemy==2.0
Flask-Testing==0.6.1
Flask-WTF==0.14.2
future==0.16.0
futures==3.0.5
gunicorn==19.6.0
humanize==0.5.1
idna==2.5
ipaddress==1.0.18
itsdangerous==0.24
Jinja2==2.9.5
jmespath==0.9.2
kombu==3.0.37
Mako==1.0.6
Markdown==2.6.8
MarkupSafe==1.0
numpy==1.12.1
packaging==16.8
pandas==0.18.1
parsedatetime==2.0
pyasn1==0.2.3
pycparser==2.17
pydruid==0.3.1
PyHive==0.2.1
pyparsing==2.2.0
python-dateutil==2.6.0
python-editor==1.0.3
python-openid==2.2.5
pytz==2016.10
requests==2.13.0
s3transfer==0.1.10
sasl==0.2.1
simplejson==3.10.0
six==1.10.0
SQLAlchemy==1.1.5
SQLAlchemy-Utils==0.32.12
sqlparse==0.1.19
superset==0.17.1
thrift==0.10.0
thrift-sasl==0.2.1
Werkzeug==0.11.15
WTForms==2.1
```
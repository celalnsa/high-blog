---
title: Create dev environment for superset
date: 2017-03-27 21:55:40
tags: 
    - superset
    - python
---


创建一个virtualenv, 叫做${superset_source}
```bash
virtualenv superset_source
```
安装依赖
```bash
cd superset_source
pip install -r requirements.txt
. bin/activate
```


cd到代码目录${Code} 举例: ~/git/third_part/airbnb_superset
```bash
cd ~/git/third_part/airbnb_superset
cd superset/static/assets
npm install
npm run prod
export PYTHONPATH=.:${PYTHONPATH}
```


跑起来
```bash
superset/bin/superset runserver -p 12306
```

每次在新的terminal启动
```bash
cd ~/git/third_part/airbnb_superset
cd superset/static/assets
export PYTHONPATH=.:${PYTHONPATH}
superset/bin/superset runserver -p 12306
```

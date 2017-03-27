---
title: Create dev environment for superset
date: 2017-03-27 21:55:40
tags: superset, python
---

```bash
# 在某个目录创建一个virtualenv, 叫做superset_source
virtualenv superset_source
# 安装依赖
cd superset_source
pip install -r requirements.txt
. bin/activate
# cd到代码目录${Code} 举例: ~/git/third_part/airbnb_superset
cd ~/git/third_part/airbnb_superset
cd superset/static/assets
npm install
npm run prod
export PYTHONPATH=.:${PYTHONPATH}
# 跑起来
superset/bin/superset runserver -p 12306



# 每次在新的terminal启动
cd ~/git/third_part/airbnb_superset
cd superset/static/assets
export PYTHONPATH=.:${PYTHONPATH}
superset/bin/superset runserver -p 12306
```

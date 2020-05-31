# Superset Labs

Some Dev Labs About Superset Just Focus On My Stacks

一些关于 Superset 的实验，针对🇨🇳地区优化

## Setup

```
pip install -i https://mirrors.aliyun.com/pypi/simple/ -r ../incubator-superset/requirements.txt
pip install -i https://mirrors.aliyun.com/pypi/simple/ -r ../incubator-superset/requirements-dev.txt
pip install -e ../incubator-superset
```

```
export SUPERSET_CONFIG_PATH=./superset_config.py
superset fab babel-compile --target ../incubator-superset/superset/translations
FLASK_ENV=development gunicorn "superset.app:create_app()" -b 127.0.0.1:8088 --reload
celery worker --app=superset.tasks.celery_app:app --pool=prefork -Ofair -c 4
```


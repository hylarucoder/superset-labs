# Superset Labs

Some Dev Labs About Superset Just Focus On My Stacks

一些关于 Superset 的实验，针对🇨🇳地区优化

## Setup

### Project Structure

```
.
├── incubator-superset
│   ├── superset
│   ├── tests
│   └── tox.ini
└── superset-labs
    ├── README.md
    ├── superset_config.py
    └── venv
```

```
cd superset-labs/
pip install -i https://mirrors.aliyun.com/pypi/simple/ -r ../incubator-superset/requirements.txt
pip install -i https://mirrors.aliyun.com/pypi/simple/ -r ../incubator-superset/requirements-dev.txt
pip install -e ../incubator-superset
```

```
export SUPERSET_CONFIG_PATH=./superset_config.py
export FLASK_ENV=development

# 修复中文翻译
superset fab babel-compile --target ../incubator-superset/superset/translations
# 开发
gunicorn "superset.app:create_app()" -b 127.0.0.1:8088 --reload
# 启用 worker
celery worker --app=superset.tasks.celery_app:app --pool=prefork -Ofair -c 4
```


# Magento-2.0-Docker-Environment
PHP Environment for Magento 2.0


How To setup Magento
---

```wget https://github.com/magento/magento2/archive/2.0.zip```

extract to ```source``` directory and start compose: 

```docker-compose -f compose.yaml up -d```

enter in container:

```docker exec -it [CONTAINER ID] bash```

run php composer to install dependancy

```composer install```

and set permission to ```var directory```

```chmod -R a+w *```

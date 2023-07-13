```python

docker build . -t flask_app_dev
docker run flask_app_dev
docker run -p 5000:5000 -e DEBUG=1 flask_app_dev
```

Docker compose

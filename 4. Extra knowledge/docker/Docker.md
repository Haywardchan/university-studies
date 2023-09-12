```python

docker build . -t flask_app_dev
docker run flask_app_dev
docker run -p 5000:5000 -e DEBUG=1 flask_app_dev
docker-compose up
```

Docker compose

android   1:176386425985:android:eb10de932f18bac9d7b980
ios       1:176386425985:ios:acefa5b3a8adbb11d7b980
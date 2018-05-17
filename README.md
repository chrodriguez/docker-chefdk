# Mi chefdk

Este repo tiene chedfk con soporte de git. Mi idea es usarlo a través de un
shell script wrapper como el siguiente:

```bash
#!/bin/bash
docker run --rm -it \
  -v /etc/passwd:/etc/passwd:ro \
  -v /etc/group:/etc/group:ro \
  -u $(id -u):$(id -g) \
  -v $PWD:$PWD \
  -w $PWD chrodriguez/chefdk $@
```

Luego, es posible utilizar el comando de la siguiente forma:

```
chef-docker berks install
chef docker chef generate cookbook prueba
```



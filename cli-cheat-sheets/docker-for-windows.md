# Docker for Windows

Run a docker container \(in this case ruby\), mount current directory to `/app` and open bash:

```bash
$ docker run -v ${pwd}:/app -it ruby /bin/bash`
```


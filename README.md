◆Drone.io 参考文献
・ドキュメント https://0-8-0.docs.drone.io/
・secrets https://docs.drone.io/config/pipeline/secrets/#secrets
・services https://docs.drone.io/config/pipeline/services/#services
・group http://ashphy.hateblo.jp/entry/drone-parallel-build
・kubernetes deployments http://plugins.drone.io/mactynow/drone-kubernetes/
・/var/run/docker.sock https://rimuru.lunanet.gr.jp/notes/post/how-to-root-from-inside-container/


Drone is a Continuous Delivery system built on container technology. Drone uses a simple YAML configuration file, a superset of docker-compose, to define and execute Pipelines inside Docker containers. 

<br/>

<img src="https://github.com/drone/brand/blob/master/screenshots/screenshot_build_success.png" style="max-width:100px;" />

Sample Pipeline Configuration:

```yaml
pipeline:
  backend:
    image: golang
    commands:
      - go get
      - go build
      - go test

  frontend:
    image: node:6
    commands:
      - npm install
      - npm test

  publish:
    image: plugins/docker
    repo: octocat/hello-world
    tags: [ 1, 1.1, latest ]
    registry: index.docker.io

  notify:
    image: plugins/slack
    channel: developers
    username: drone
```

Documentation and Other Links:

* Setup Documentation [docs.drone.io/installation](http://docs.drone.io/installation/)
* Usage Documentation [docs.drone.io/getting-started](http://docs.drone.io/getting-started/)
* Plugin Index [plugins.drone.io](http://plugins.drone.io/)
* Getting Help [docs.drone.io/getting-help](http://docs.drone.io/getting-help/)

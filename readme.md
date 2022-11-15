
Overview
----
docker compose快速部署开发依赖


#### 启动示例

- docker-compose -f docker-compose-rocketmq.yml -p localdev up -d
- docker-compose -f docker-compose-nacos-mysql-sentinel-rabmq.yml -p localdev up -d
- docker-compose -f docker-compose-gitlabce.yml -p gitlabce up -d

#### 已调试内容
 
- nacos
- mysql
- sentinel
- redis
- rocketmq (权限问题直接映射了磁盘目录)
- gitlabce

network及 volume 设置
----

- network
```
为了让各组件都能互相访问,统一使用localdev网络
服务中使用:
networks:
    - localdev

定义
networks:
  localdev:
    name: localdev
    driver: bridge
    external: true
```

- volume
```
卷都采用申明
volumes:
  redisdata:
    driver: local
```


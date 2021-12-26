.ONESHELL:

inet:
	INET=$$(ip a | grep inet | grep wlp8s0 | awk '{print $$2}' | awk -F '/' '{print $$1}')  # 内网地址 wlp8s0 网卡 需要根据自己的修改
	echo $${INET}

mongodb:
	docker run --name my-mongo \
		--restart always \
		-v ${PWD}/vols/mongodb/configdb:/data/configdb \
		-v ${PWD}/vols/mongodb/db:/data/db \
		-e MONGO_INITDB_ROOT_USERNAME=mongoadmin \
		-e MONGO_INITDB_ROOT_PASSWORD=secret \
		-p 0.0.0.0:27017:27017 \
		-d mongo \
		#--auth


mysqldb:
	docker run --name my-mysql \
		--restart always \
		-v ${PWD}/vols/mysqldb:/var/lib/mysql \
		-e MYSQL_ROOT_PASSWORD=secret \
		-p 0.0.0.0:3306:3306 \
		-d mysql
redisdb:
	docker run --name my-redis \
		--restart always \
		-v ${PWD}/vols/redisdb/data:/data \
		-p 0.0.0.0:6379:6379 \
		-d redis redis-server --save 60 1
rabbitmq:
	docker run -d --name my-rabbit \
		--restart always \
		-v ${PWD}/vols/rabbitmq:/var/lib/rabbitmq \
		-p 0.0.0.0:5672:5672 \
		-p 0.0.0.0:15672:15672 \
		rabbitmq:3-management

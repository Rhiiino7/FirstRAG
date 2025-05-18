# 启动milvus
# 拉取最新稳定版镜像
docker pull milvusdb/milvus:v2.3.4

# 启动服务（自动加载所需组件）
docker run -d \
  --name milvus \
  -p 19530:19530 \  # 客户端连接端口
  -p 9091:9091 \    # 监控端口
  -v ~/milvus_data:/var/lib/milvus \  # 数据持久化
  milvusdb/milvus:v2.3.4

# 验证是否运行成功
docker logs -f milvus  
# 看到 "Successfully loaded config" 即正常


#################################################
# 第一次运行（拉取镜像+启动）
docker pull milvusdb/milvus:v2.3.4
docker run -d --name milvus -p 19530:19530 -p 9091:9091 -v milvus_data:/var/lib/milvus milvusdb/milvus:v2.3.4

# 日常使用
docker start milvus  # 启动
docker stop milvus   # 停止

# 彻底删除
docker rm -f milvus
docker volume rm milvus_data
################################################
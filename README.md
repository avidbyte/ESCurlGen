# ESCurlGen
由于经常重复的写查询，修改查询条件，改索引名称等操作，于是用 AI 生成了这款web工具，用于生成 es curl 命令
![工具截图](https://github.com/avidbyte/ESCurlGen/blob/main/Snipaste_2024-10-15_17-44-58.png "可选标题")
目前仅查询类型可用，剩余的后续优化 2024/10/15




# 示例

## 创建索引
```json
{
  "settings": {
    "number_of_shards": 1,
    "number_of_replicas": 1
  },
  "mappings": {
    "properties": {
      "name": { "type": "text", "fields": { "keyword": { "type": "keyword" } } },
      "phone": { "type": "text", "fields": { "keyword": { "type": "keyword" } } },
      "birthday": { "type": "date" },
      "createTime": { "type": "date" }
    }
  }
}
```


## 新增索引字段
```json
{
  "properties": {
    "address": { "type": "text", "fields": { "keyword": { "type": "keyword" } } }
  }
}
```



## 新增数据
```json
{
  "name": "John Doe",
  "phone": "123-456-7890",
  "birthday": "1990-01-01",
  "createTime": "2023-10-10T00:00:00Z"
}
```
```json
{
  "name": "Jane Smith",
  "phone": "098-765-4321",
  "birthday": "1985-05-05",
  "createTime": "2023-10-11T00:00:00Z"
}
```

## 根据 ID 更新数据
```json
{
  "doc": {
    "phone": "555-555-5555",
    "createTime": "2024-10-17T00:00:00Z"
  }
}
```
# ESCurlGen
由于经常重复的写查询，修改查询条件，改索引名称等操作，于是用 AI 生成了这款web工具，用于生成 es curl 命令
![工具截图](https://github.com/avidbyte/ESCurlGen/blob/main/Snipaste_2024-10-15_17-44-58.png "可选标题")


# 测试示例 my_user_index 索引

## 1.创建索引
```json
{
  "mappings": {
    "properties": {
      "id": { "type": "keyword" },
      "name": { "type": "text", "fields": { "keyword": { "type": "keyword" } } },
      "phone": { "type": "text", "fields": { "keyword": { "type": "keyword" } } },
      "birthday": { "type": "date" },
      "createTime": { "type": "date" }
    }
  }
}
```


## 2.新增索引字段
```json
{
  "properties": {
    "address": { "type": "text", "fields": { "keyword": { "type": "keyword" } } }
  }
}
```

## 3.查询 settings
## 4.查询 Mapping

## 5.新增数据
```json
{
  "id": "1",
  "name": "John Doe",
  "phone": "123-456-7890",
  "birthday": "1990-01-01",
  "createTime": "2023-10-10T08:00:00Z",
  "address": "123 Main St"
}
```
```json
{
  "id": "2",
  "name": "Jane Smith",
  "phone": "098-765-4321",
  "birthday": "1985-05-05",
  "createTime": "2023-10-11T09:00:00Z",
  "address": "456 Oak Ave"
}
```

## 6.批量操作（批量新增）

```json lines
{ "index": { "_id": "3" } }
{ "name": "User One", "phone": "1234567890", "birthday": "1995-05-05", "createTime": "2024-10-17T10:00:00", "address": "789 Elm St" }
{ "index": { "_id": "4" } }
{ "name": "User Two", "phone": "0987654321", "birthday": "1988-07-15", "createTime": "2024-10-17T11:00:00", "address": "1234 Oak St" }
```


## 7.查询索引数据条数

## 8.根据条件查询
```json
{
  "query": {
    "match": {
      "name": "John Doe"
    }
  }
}
```
## 9.根据 ID 查询

## 10.滚动查询
```json
{
  "size": 100,
  "query": {
    "match_all": {
    }
  }
}
```
在初次滚动查询后，您需要使用 scroll_id 进行后续请求：
```json
{
  "scroll": "1m",
  "scroll_id": "DXF1ZXJ5QW5kRmV0Y2gBAAAAAA..."
}
```

## 11.根据 ID 更新数据
```json
{
  "doc": {
    "phone": "555-555-5555",
    "createTime": "2024-10-17T00:00:00Z"
  }
}
```


## 12.根据自定义条件更新数据
```json
{
  "query": {
    "match": {
      "name": "John Doe"
    }
  },
  "script": {
    "source": "ctx._source.phone = '111-111-1111'",
    "lang": "painless"
  }
}

```

## 13.根据 ID 删除数据

## 14.根据自定义条件删除数据
```json
{
  "query": {
    "match": {
      "name": "Alice Johnson"
    }
  }
}
```

## 15.删除索引
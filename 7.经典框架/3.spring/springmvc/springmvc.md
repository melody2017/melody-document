## 说明


# 重点类介绍
## ResponseEntity
ResponseEntity 可以定义返回的HttpHeaders和HttpStatus
```
@RequestMapping(value = "/User", method = RequestMethod.POST)
public @ResponseBody ResponseEntity<ResponseOutNorth> getUser(@RequestBody RequestInNorth request) {
  
  HttpHeaders headers = new HttpHeaders();  
  headers.setContentType(MediaType.APPLICATION_JSON);
  headers.add("iag-keep", "alive");
  
  ResponseOutNorth body = new ResponseOutNorth();
  body.setResponseId("421010");
  ResponseEntity<ResponseOutNorth> entity = new ResponseEntity<ResponseOutNorth>(body,headers, HttpStatus.NOT_FOUND);
  return entity;
}
}
```
#### 1. HttpHeaders
可以设置http请求头和响应头
```
    HttpHeaders headers = new HttpHeaders();  
    headers.setContentType(MediaType.APPLICATION_JSON);
    headers.add("iag-keep", "alive");
```
#### 2. HttpStatus
枚举，包含了http各种状态码，可以在返回时根据情况选择。

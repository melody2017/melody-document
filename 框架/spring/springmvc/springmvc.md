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

## HandlerMethodReturnValueHandler 
HandlerMethodReturnValueHandler是RequestMappingHandlerAdapter用来处理当含有@RequestMapping的方法调度完成后，后面要进行的事情。
```
/**
 * 策略模式接口：处理 Controller 方法返回值
 */
public interface HandlerMethodReturnValueHandler {

    /**
     * 该处理程序是否支持给定的方法返回类型(只有返回true才回去调用handleReturnValue)
     */
    boolean supportsReturnType(MethodParameter returnType);

    /**
     * 处理给定的返回值
     * 通过向 ModelAndViewContainer 添加属性和设置视图或者
     * 通过调用 ModelAndViewContainer.setRequestHandled(true) 来标识响应已经被直接处理(不再调用视图解析器)
     */
    void handleReturnValue(Object returnValue, MethodParameter returnType,
            ModelAndViewContainer mavContainer, NativeWebRequest webRequest) throws Exception;

}
```

1. 定义返回值拦截器，继承HandlerMethodReturnValueHandler接口
```

```
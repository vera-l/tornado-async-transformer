# Tornado Async Transformer

![](https://github.com/zhammer/tornado-async-transformer/workflows/CI/badge.svg)

A [libcst](https://github.com/Instagram/LibCST) transformer for updating tornado @gen.coroutine syntax to python3.5+ native async/await.

Read [the article](https://chairnerd.seatgeek.com/refactoring-python-with-libcst/) about this tool.

[Check out the demo.](https://tornado-async-transformer.zhammer.now.sh/)

### Usage
You can either:
- Add `tornado_async_transformer.TornadoAsyncTransformer` to your existing libcst codemod or just install the package `python3 setup.py install`
- Or run `python -m tornado_async_transformer.tool my_project/` from the commandline.

#### Example
```diff
 """
 A simple coroutine.
 """
 from tornado import gen


-@gen.coroutine
-def call_api():
-    response = yield fetch()
+async def call_api():
+    response = await fetch()
     if response.status != 200:
         raise BadStatusError()
-    raise gen.Return(response.data)
+    return response.data
```

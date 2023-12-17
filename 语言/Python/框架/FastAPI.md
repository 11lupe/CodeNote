

[官方文档]([FastAPI (tiangolo.com)](https://fastapi.tiangolo.com/zh/))



python版本：>=3.6





# 简单实例

```python
#!/usr/bin/env python3
# -*- encoding: utf-8 -*-
"""
pipenv shell
pipenv  install fastapi
pipenv install uvicorn
"""

from fastapi import FastAPI

app = FastAPI()


@app.get("/")
def read_root():
    return {"Hello": "World"}


if __name__ == '__main__':
    import uvicorn
    host = "0.0.0.0"
    port = 8000  # 默认8000
    # 127.0.0.1:{port}访问
    # 127.0.0.1:{port}/docs查看在线接口文档
    uvicorn.run(app, host="0.0.0.0", port=port, reload=False)

```

测试实例

```python
import unittest

from starlette.testclient import TestClient

from simple_server.faskapi_server import app


class FastAPITestCase(unittest.TestCase):

    def setUp(self):
        self.client = TestClient(app)

    def test_request(self):
        response = self.client.get("/")
        self.assertEqual(response.status_code, 200)
        self.assertEqual(response.json(), {"Hello": "World"})


if __name__ == '__main__':
    unittest.main()
```

访问地址：127.0.0.1:8000

交互式 API 文档：127.0.0.1:8000/docs

可选的 API 文档：127.0.0.1:8000/redoc


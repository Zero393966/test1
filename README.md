# OpenAPI 3.1 规范示例

这是一个OpenAPI 3.1规范的示例项目，展示了如何使用外部文件来组织组件定义。

## 项目结构

```
reference-files/
├── openapi.yaml              # 主OpenAPI规范文件
├── components/
│   └── schemas.yaml          # 数据模型组件定义
└── README.md                 # 项目说明文档
```

## 文件说明

### openapi.yaml
主OpenAPI规范文件，包含：
- API基本信息（标题、版本、联系方式等）
- 服务器配置（生产环境和测试环境）
- 路径定义（当前包含一个用户查询端点）
- 安全方案定义（Bearer Token和API Key认证）

### components/schemas.yaml
包含所有数据模型组件定义：
- `User`: 用户基本信息模型
- `UserProfile`: 用户档案信息模型
- `UserResponse`: 用户信息响应模型
- `ErrorResponse`: 错误响应模型
- `PaginationInfo`: 分页信息模型

## API端点

### GET /users/{userId}
获取指定用户的详细信息

**参数：**
- `userId` (path): 用户ID，必须为8位或以上的字母数字组合
- `includeProfile` (query): 是否包含用户档案信息，可选，默认为false

**响应：**
- `200`: 成功获取用户信息
- `400`: 请求参数错误
- `404`: 用户不存在
- `500`: 服务器内部错误

**认证：**
支持Bearer Token和API Key两种认证方式

## 使用外部组件的优势

1. **模块化**: 将数据模型定义分离到独立文件中，便于维护
2. **可重用性**: 组件可以在多个API规范中重复使用
3. **清晰性**: 主规范文件更简洁，专注于API路径和操作定义
4. **团队协作**: 不同团队成员可以并行编辑不同的组件文件

## 验证和测试

您可以使用以下工具来验证和测试这个OpenAPI规范：

1. **Swagger Editor**: 在线编辑和预览
2. **Swagger UI**: 生成交互式API文档
3. **OpenAPI Generator**: 根据规范生成客户端代码
4. **Postman**: 导入OpenAPI规范进行API测试

## 示例请求

```bash
# 获取用户基本信息
curl -X GET "https://api.example.com/v1/users/user12345" \
  -H "Authorization: Bearer your-jwt-token"

# 获取用户信息（包含档案）
curl -X GET "https://api.example.com/v1/users/user12345?includeProfile=true" \
  -H "X-API-Key: your-api-key"
```

## 扩展建议

1. 添加更多端点（POST、PUT、DELETE操作）
2. 增加请求体模型定义
3. 添加更多响应示例
4. 定义更多的安全方案
5. 添加标签和分组来组织API


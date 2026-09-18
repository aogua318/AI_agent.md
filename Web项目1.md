# **MyApp 项目**

MyApp 是一个全栈 Web 应用，前端采用 TypeScript，后端采用 Node.js。核心功能位于 `src/` 文件夹下，分为客户端（`client/`）和服务端（`server/`）两部分。

## **构建与命令**

- 类型检查与代码检查：`pnpm check`
- 自动修复格式与 lint 问题：`pnpm check:fix`
- 运行测试：`pnpm test --run --no-color`
- 运行单个测试文件：`pnpm test --run src/file.test.ts`
- 启动开发服务器：`pnpm dev`
- 构建生产版本：`pnpm build`
- 预览生产构建结果：`pnpm preview`

### **开发环境**

- 前端开发服务器：[http://localhost:3000](http://localhost:3000/)
- 后端开发服务器：[http://localhost:3001](http://localhost:3001/)
- 数据库端口：5432
- Redis 缓存端口：6379

## **代码风格**

- TypeScript：启用严格模式，包含 `exactOptionalPropertyTypes`、`noUncheckedIndexedAccess`
- 缩进使用制表符（Tab），YAML / JSON / MD 文件使用 2 个空格
- 单引号、不写分号、保留尾随逗号
- TypeScript 类型定义使用 JSDoc 文档注释，避免使用 `//` 注释
- 行宽限制为 100 字符
- 导入语句：使用 `consistent-type-imports`
- 变量与函数名需具有描述性
- 驼峰命名中缩写一律大写：使用 `URL`（而非 `Url`）、`API`（而非 `Api`）、`ID`（而非 `Id`）
- 优先采用函数式编程风格
- 公共 API 使用 TypeScript 接口（interface）定义
- **绝不允许**使用 `@ts-expect-error` 或 `@ts-ignore` 压制类型错误

## **测试**

- 单元测试：Vitest
- 组件测试：Testing Library
- E2E 测试：Playwright
- 编写测试时一次只写一个测试用例
- 使用 `expect(VALUE).toXyz(...)` 直接断言，不要先存入变量
- 测试名称中省略“should”（例如写 `it("validates input")`，不要写 `it("should validate input")`）
- 测试文件命名：`*.test.ts` 或 `*.spec.ts`
- 外部依赖需进行恰当的 mock

## **架构**

- 前端：React + TypeScript
- 后端：Express.js + TypeScript
- 数据库：PostgreSQL + Prisma ORM
- 状态管理：Zustand
- 样式：Tailwind CSS
- 构建工具：Vite
- 包管理器：pnpm

## **安全**

- 使用合适的数据类型，限制敏感信息的暴露面
- 绝不向仓库提交密钥或 API Key
- 敏感数据一律通过环境变量传入
- 客户端与服务端均需校验所有用户输入
- 生产环境强制使用 HTTPS
- 定期更新依赖
- 遵循最小权限原则

## **Git 工作流**

- 提交前**必须**执行 `pnpm check`
- 使用 `pnpm check:fix` 修复 lint 错误
- 执行 `pnpm build` 确认类型检查通过
- **绝不**在主分支上使用 `git push --force`
- 功能分支如需强制推送，请使用 `git push --force-with-lease`
- 执行强制操作前务必确认当前所在分支

## **配置**

新增配置项时，必须同步更新以下所有位置：

1. `.env.example` 中的环境变量
2. `src/config/` 中的配置 schema
3. README.md 中的相关文档

所有配置键名须保持命名一致，且**必须**附带文档说明。
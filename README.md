# 全局安装 NestJS CLI
npm install -g @nestjs/cli

# 创建新的 Nest 项目
nest new nest-prisma-postgres
cd nest-prisma-postgres

# 安装 Prisma 客户端和 CLI 工具
npm install @prisma/client
npm install prisma --save-dev

# 安装 PostgreSQL 客户端库
npm install pg

# 安装 @nestjs/config 用于环境变量管理（可选）
npm install @nestjs/config

# 初始化 Prisma 配置文件
npx prisma init
DATABASE_URL="postgresql://<user>:<password>@localhost:5432/nestdb?schema=public"


# 创建并应用迁移
npx prisma migrate dev --name init

# 生成 Prisma Client
npx prisma generate

# 创建 prisma 目录
mkdir src/prisma



# 创建 Prisma Module 和 Service 文件
touch src/prisma/prisma.module.ts
touch src/prisma/prisma.service.ts


npx prisma migrate dev --name init
npx prisma generate


# 生成用户模块和服务
nest generate module user
nest generate service user
nest generate controller user


npm run start:dev

curl -X POST http://localhost:3000/users -H "Content-Type: application/json" -d '{"email": "test@example.com", "name": "Test User"}'
curl http://localhost:3000/users
curl http://localhost:3000/users/1
curl -X PUT http://localhost:3000/users/1 -H "Content-Type: application/json" -d '{"name": "Updated User"}'
curl -X DELETE http://localhost:3000/users/1
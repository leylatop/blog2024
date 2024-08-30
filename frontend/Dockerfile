# 使用官方的 Node.js 镜像作为基础镜像
FROM node:14

# 设置工作目录
WORKDIR /app

# 复制 package.json 和 package-lock.json
COPY package*.json ./

# 安装依赖
RUN npm install

# 复制所有文件到工作目录
COPY . .

# 构建应用
RUN npm run build

# 使用 Nginx 作为前端服务器
FROM nginx:alpine
COPY --from=0 /app/dist /usr/share/nginx/html

# 暴露端口
EXPOSE 80

# 启动 Nginx
CMD ["nginx", "-g", "daemon off;"]
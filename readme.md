#My React

1.สร้าง git repo ใน github และทำการ Clone repo ผ่าน VSCODE

2.ติดตัง React ด้วย Vite
```
$npm create vite@latest 
  create-vite@4.0.0
  Ok to proceed? (y) y
? Project name: › .      ///พิมพ์ . ลงไปเพื่อให้ Project ติดตั้งใน current folder เลย ไม่ต้องสรา้งไหม
```
2.1 เลือก
```
? Select a framework: › - Use arrow-keys. Return to submit.
    Vanilla
    Vue
❯   React
    Preact
    Lit
    Svelte
    Others
```
2.2 เลือก
```
   ? Select a variant: › - Use arrow-keys. Return to submit.
❯   JavaScript
    TypeScript
    JavaScript + SWC
    TypeScript + SWC

Scaffolding project in /Volumes/Server/nodejs/myreact...

Done. Now run:

  npm install
  npm run dev

```
2. ทดสอบ push ขึ้น repo ที่สร้าง
3.สร้าง Docker  สำหรับเตริยม Enviroment ไว้ทดสอบ

3.1 สรา้งไฟล์ docker-compose.yml

```
version: '3.9'

# Network
networks:
  web_network:
    name: reactvitewebapi
    driver: bridge

services:
  # React App Service
  reactapp:
    build:
      context: .
      dockerfile: Dockerfile
    container_name: react_vite_webapi
    restart: always
    volumes:
      - ./:/usr/app
      - /usr/app/node_modules
    ports:
      - 5173:5173
    environment:
      - CHOKIDAR_USEPOLLING=true
    networks:
      - web_network

  ```
  
  3.2 สร้าง ไฟล์ Dockerfile
 
```
# Pull the base image
FROM node:16.14.2-alpine

# Set the working directory
WORKDIR /usr/app

# Copy app dependencies to container
COPY ./package*.json ./

# Install dependencies
RUN npm install

# Copy code from host to container
COPY . .

# Expose Port
EXPOSE 5173

# Deploy app for local development
CMD [ "npm","run","dev" ]

```
-----------------------------
Vscode Extention ที่เตรียมไว้ดังนี้
```
1.Color Picker  by anseki
2.Material Icon Theme  by Philipp Kief
3.ES7 React/Redux/GraphQL/React-Native snippets by dsznajder
4.html to JSX by Riaz Laskar
5.Prettier - Code formatter by Prettier
6.Docker by Microsoft
7.Bracket Pair Colorizer by CoenraadS
8.Auto Import by steoates 
9.One Dark Pro by binaryify
```

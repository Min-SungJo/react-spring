### 1. React
// yarn 설치
npm install --global yarn
// yarn 버전 확인
yarn --version
// react 설치 프로젝트 이름: react_project
yarn create react-app react_project
// 프로젝트 경로로 진입 후 프로젝트 실행
cd react_project
yarn start
// 프로젝트 빌드
yarn build

// nginx defalut 제거
rm /etc/nginx/sites-available/default
rm /etc/nginx/sites-enabled/default
// nginx 설정
vi /etc/nginx/sites-available/react_project.conf

server {
  listen 80;
  server_name localhost;
  location / {
    root   ~/react-spring/react_project/build; // react_project build 폴더 경로
    index  index.html index.htm;
    try_files $uri $uri/ /index.html;
    proxy_pass http://localhost:8080;
  }
}

// nginx 실행으로 react_project 가동 확인
service nginx start

// package.json proxy 설정 추가
"proxy": "http://localhost:8080/",

### 2. SpringBoot
// restController 구성

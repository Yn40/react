# ๐ก Strapi application

strapi๋ฅผ ํฉ์ฉํ๋ฉด ์ฝ๋ ํ์ค ์์ด rest api์๋ฒ๋ฅผ ๊ตฌ์ถ๊ฐ๋ฅํ๋ค. <br>
react ๊ณต๋ถํ๋ค ๋ณด๋ฉด ๋ฐ์ดํฐ๋ db์ ์ ์ฅํ๊ณ  ์ถ๊ณ , ํ์๊ฐ์ ๊ธฐ๋ฅ๋ ๋ฃ๊ณ  ์ถ์๋๋ฐ, ํ ์ด ํ๋ก์ ํธ์ ์ ์ฉํ๋ฉด ๋๋ฐ์ด๋ค ์ถ์ด์ ํ๋ฒ ์ด์ง ๊ณต๋ถํด๋ด
<br><br>

`* mongodb ์ฐ๋ํ๊ณ  heroku๋ก ๋ฐฐํฌ ์์ `
<br><br>

- Strapi Dosc - https://strapi.io/documentation/developer-docs/latest/getting-started/introduction.html 

- mongodb ํด๋ผ์ฐ๋ ์๋ฒ - https://www.mongodb.com/

- heroku ์๋ฒ - https://dashboard.heroku.com/

- ์ฐธ๊ณ  ์ฌ์ดํธ - https://puzzle-puzzle.tistory.com/entry/strapi-strapi%EC%99%80-mongodb-atlas-%EC%97%B0%EA%B2%B0%ED%95%98%EA%B8%B0

<br><br><br><br>

## ๐ mongdb 
nosql ๋ํ db๋ก ๋ฌด๋ฃ ํด๋ผ์ฐ๋๋ฅผ ์ด์ฉํด์ ์ฌ์ฉ ๊ฐ๋ฅํ๋ค
<br><br>
## ๐ heroku
git์ ์ด์ฉํ์ฌ ๋ฐฐํฌํ๋ ์๋ฒ๋ก ์ฌ์ฉ์๋ง ๊ตฌ๋๋๋ค. <br>
์ญ์ ๋ฌด๋ฃ ์ฌ์ฉ ๊ฐ๋ฅ<br><br><br>


## ๐ Strapi ์ค์น
--quickstart ํ๋ฉด ๊ธฐ๋ณธ sqLite ์ค์น ๋๋ค.<br> 
ํด๋น ๋ช๋ น์ด๋ฅผ ์ฌ์ฉํ์ง ์์ผ๋ฉด db๋ฅผ ์ ํ๊ฐ๋ฅํ๋ค. <br>
mongodb๋ฅผ ๋ฐ๋ก ์ฐ๊ฒฐํ๋ ค ํ๋๋ฐ ์๋์ ์ผ๋จ quickstart๋ก ์ค์น ํ ์๋์ผ๋ก ์ฐ๋ ์์  <br>

```java

npx create-strapi-app ํ๋ก์ ํธ์ด๋ฆ --quickstart

```

์ค์ ์ด ๋๋๋ฉด ์๋์ผ๋ก ์คํ๋๋๋ฐ, ๊ฐ๋ฐ์์ฉ์ผ๋ก ์ค์ ์ ๋ณ๊ฒฝํด์ผ npm start ํ์๋ ํ์ด๋ธ ์ถ๊ฐ ์์ ์ด ๊ฐ๋ฅํจ
<br><br><br>
## ๐  develop ๋ชจ๋๋ก ๋ณ๊ฒฝํ๊ธฐ! - ์ค์  ํ์ผ ์์ 
`package.json`<br>
๋ฑํ start๋ก ์๋ํ์ง ์์๊ฒ ๊ฐ์์ ๋ณ๊ฒฝํจ ํ์ง๋ง ์ฌ๋งํ๋ฉด config/server.js ํ์ผ์ ์์ ํ๊ธฐ!<br>
ํด๋น ํ๋ก์ ํธ๋ ๋์ ๋ณ๊ฒฝํจ <br>

```java
 "scripts": {
    "develop": "strapi develop",
    "start": "strapi develop",
    "build": "strapi build",
    "strapi": "strapi"
  },
```
`config/server.js`
```java
 module.exports = ({ env }) => ({
  host: env('HOST', '0.0.0.0'),
  ...
  autoReload: {
    'enabled': true
  },
});

```
<br><br><br><br>
## ๐  mongodb Atlas ์ค์น
๊ตฌ๊ธ๋ณด๊ณ  cluster๋ง๋ค๋ฉด ๋๋ค<br><br>
์ฐธ๊ณ  - https://puzzle-puzzle.tistory.com/entry/strapi-strapi%EC%99%80-mongodb-atlas-%EC%97%B0%EA%B2%B0%ED%95%98%EA%B8%B0 <br><br>


 `create cluster `<br>
 google > tokyo ์ ํ<br>

 ํธ์คํธ 0.0.0.0 ์ผ๋ก ํ์ง ์ด์ด์ฃผ๊ณ  user ์์ฑ๋ ํจ (strapi ์ฐ๊ฒฐํ ๋ ์ฌ์ฉํ๋ค)
 
<br><br><br>
## ๐  strapi, mongodb ์ฐ๋ - ์ค์  ํ์ผ ์์ 

`config/database.js`
```java
module.exports = ({ env }) => ({
  defaultConnection: 'default',
  connections: {
    default: {
      connector: 'mongoose',
      settings: {
        uri: env('DATABASE_URI'),
      },
      options: {
        ssl: true,
      },
    },
  },
});
```
`.env`
```java
DATABASE_URI=mongodb+srv://id:pw@cluster์ด๋ฆ.mongodb.net/myFirstDatabase?retryWrites=true&w=majority
```


```java
//์ถ๊ฐ ์ค์น
npm install --save strapi-connector-mongoose
// develop ์คํ
npm start
```

<br><br><br>
## ๐ heroku ์ฐ๋
์ฐธ๊ณ  - https://minify.tistory.com/25 <br>

`heroku ํ์๊ฐ์ ํ create new app์ผ๋ก ์๋ก์ด ์ฑ ๋ง๋ฌ`<br><br>
`์๋ url์์ heroku-cli ์ค์น`<br>
https://devcenter.heroku.com/articles/heroku-cli<br>

strapi ํ๋ก์ ํธ์์ ์๋ ๋ช๋ น์ด ์๋ ฅ

```java
//enter์น๋ฉด ๋ก๊ทธ์ธ ํ์ด์ง ์ฐ๊ฒฐ
heroku login

```
์ฐ๊ฒฐ ํ git ์ฐ๋ (heroku git ์ฌ์ฉ ์์ )
```java
git init
heroku git:remote -a yn-project 
git add.
git commit -am "my app deploy"
git push heroku master //ํ์ฐธ ๊ธฐ๋ค๋ฆฌ๋ฉด ๋ฐฐํฌ ์๋ฃ๋จ 
```java
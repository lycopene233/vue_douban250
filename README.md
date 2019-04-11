# vue-douban250

### 概要

- 人気映画（豆瓣250）のリストページ
- 初めてのvueチャレンジ

### 実装機能

- 豆瓣250というapiから人気映画の情報を取ってくる
- 映画のリストページ作成
- 画面の一番下までスクロールすると、映画情報を30本ずつ取ってくる
- ソート機能（新しい順｜古い順｜評価順）
- お気に入りの登録機能＆フィルター機能

### 技術チャンレンジ

- vue-cli (webpack)
- vue-resource (jsonp)
- referrerのmetaタグ 

### スクショ

- 一覧画面
<img width="350" alt="屏幕快照 2019-04-12 上午12 41 57" src="https://user-images.githubusercontent.com/34592922/55972349-4f91af00-5cbe-11e9-9382-ba8b68df29cc.png">

- loading中のUI
<img width="352" alt="屏幕快照 2019-04-12 上午12 41 49" src="https://user-images.githubusercontent.com/34592922/55972352-515b7280-5cbe-11e9-9af9-dbd16e9a3085.png">

- ソート
<img width="348" alt="屏幕快照 2019-04-12 上午12 42 21" src="https://user-images.githubusercontent.com/34592922/55972359-54566300-5cbe-11e9-97b4-864cb241e4f5.png">

- お気に入り映画の抽出
<img width="351" alt="屏幕快照 2019-04-12 上午12 44 47" src="https://user-images.githubusercontent.com/34592922/55972369-56b8bd00-5cbe-11e9-8be0-e72d87e5df43.png">

### 作成時間
約5時間

### 次でチャレンジしたい項目
- vue-router
- Nuxt.js
- vueのanimation
- node.js & database との連携

<br><br>

> A Vue.js project

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).

# Simple Car WebApp

## 介紹
初次使用Nuxt開發WebApp，雖然算是Vue系列的框架，不過還是有些地方使用上不太一樣，花了一些時間查看Nuxt文件，
為了滿足test List項目，主題設定為中古車的網站，串接得mockAPI為回傳中古車的資訊。

[fireBaseHosting](https://car-project-3ebad.web.app/) <--點擊進入部署頁面

## test task

1. 用Vue Cli或Nuxt 完成以下功能 (O)
2. 以scss撰寫內容樣式 (O)
3. 應用component功能 (O)
4. 應用computed功能 (O)
5. 製作 輸入類型 text, radio, select 、同一component切換prop來改變對應的輸入類型，並可套用v-model  (O)
6. 可切換頁面 (O)
7. 設定頁面title, description  (X ，不清楚頁面title,description的作用)
8. 設定Global參數、讓頁面的顏色、主題會隨著更換 (O)
9. 串接一組列表資料api (O)
10. 程式架構做到最大的沿用性、維護性，並於Readme說明你的想法 (O)
11. 使用Firebase Hosting，提供連結給我們進行瀏覽 (O)
12. 提供Github程式碼 (O)

## 程式架構說明
### components:
- BaseButton 作為Button UI component ，能夠使 使用的元件 自定義四件處理，接收@handleClick事件。
- BaseInput 傳入對應的formItem，依照formItem提供的type屬性，產生相對應的label與input。
- CarCard 主頁面展示車輛資訊的Card Component，外層使用grid與minmax達成不需設定RWD也會自動排成合適的排版。
- Header 主要使用在layouts，使其他頁面只要選擇layoutName，就能直接夠套上使用(這個功能很棒，之前使用Vue必須自行另外將Layout import進component)。
- Home 剛進入網頁第一個看到的畫面，透過動畫增加體驗。
- Navbar 因將其規劃在主瀏覽頁顯示，故沒有放進layout，而是需要的畫面直接使用及可。
- NuxtLogo nuxt create專案時的Component，因為蠻好看就當作home的元件之一。
### Pages:
`Nuxt建構route是採用依照pages結構，而不是自己寫的，用起來不太習慣，但是確實是很好的方式`
- index 
- cars nuxt-child產生巢狀路由
  - index  
  - _id    
  - new

### assets
- scss
  - color.scss 共用顏色
  - reset.scss 清除預設樣式 
  
## Project Setup

```bash

# clone repo
$ git clone https://github.com/ZheAnZheng/Nuxt_sideproject.git

# install dependencies
$ npm install

# serve with hot reload at localhost:3000
$ npm run dev

```

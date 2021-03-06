# dc4rd-fr0n73nd-7357-2020

API: https://ptx.transportdata.tw/MOTC/v2/Tourism/ScenicSpot?$top=10&$skip=10

https://ptx.transportdata.tw/MOTC?t=Tourism&v=2#/

實作全部景點列表
- route 必須要是 /scenicSpot
- 串接 GET /v2/Tourism/ScenicSpot 回傳的資料
    - 第一次只能載入 30 個景點
    - 列表在滾到頁面底部時要再自動發送 API 請求 (stop 與 skip),載入額外 30 個景點,直到沒有更多景點
- 列表內的項目至少需顯示:景點名稱 Name、景點特色精簡說明 Description

實作縣市景點列表
- route 必須要是 /scenicSpot/{City}
- 串接 GET /v2/Tourism/ScenicSpot/{City} 回傳的資料
    - 第一次只能載入 30 個景點
    - 列表在滾到頁面底部時要再自動發送 API 請求 (stop 與 skip),載入額外 30 個景點,直到沒有更多景點
- 例: /scenicSpot/LienchiangCounty 頁面就只會顯示連江縣的景點

- 切換頁面按鈕
    - 要有能切換去全部景點列表與不同縣市景點列表的功能,UI 可以是任何形式, e.g. Header, NavBar, Drawer, Filter...
    - 所有頁面都要有這個功能

- 請在文件內說明如何啟動

只看效能，請求、避免 component rerender consider `Componentwillunmount`

Reference:

[1] https://sergiodxa.com/articles/swr/pagination#introducing-useswrpages

[2] https://www.ibrahima-ndaw.com/blog/data-fetching-in-nextjs-using-useswr/

## How to run

Just open terminal then type: `npm run start`

And visit localhost:3000 and click the link on NavBar

## Structure

1. Page part: ScenicSpot.js, [id].js
    - Render all spot in main page
    - in [id].js, i use react route to pass the route name and get the city data.
2. lib park: useRequest
    - Fetching data with swr, it helps to create cache and improve performance, since the original api is not provided page part, so i create a variable for computing the times of loading data
3. Components: Navbar.js and Post.js
    - Create a navbar to nav
    - Create a Post component to render spot 
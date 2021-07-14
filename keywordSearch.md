# 檔案關鍵字搜尋系統

## 計畫目標與範圍
### 目標
搜尋特定檔案夾裡的檔案, 列出據有關鍵字的檔案. 

### 範圍
+ 檔案數小於 10000
+ 單次搜尋時間小於 2 小時
+ 限定中英搜尋
+ 使用者界面: Command Line
+ OS: ubuntu
+ 支援檔案: 
    + pdf/docx/cvs 
    + 無加密或密碼
    + 無特殊編碼 (UTF-8)
+ 搜尋範圍: 可轉換成文字部份
+ 硬體方面: 建議 core 7i /  memory 16G (不要差太多就好)

## 流程

### 資料庫
+ 關鍵字資料庫: 紀錄所有搜尋過的關鍵字的資料庫
+ 檔案關鍵字資料庫: 特定資料夾裡的檔案以及與檔案連結的關鍵字

### 主流程

```flow
st=>start: 關鍵字搜尋系統
op1=>operation: 在terminal輸入指令
dbkeyword=>inputoutput: 關鍵字資料庫
issr=>condition: 曾經搜尋過
dbrecord1=>inputoutput: 檔案關鍵字資料庫
op2=>operation: 從資料庫取出結果
op3=>operation: 對所有檔案進行關鍵字搜尋
rt=>inputoutput: 檔案列表
end=>end: 顯示檔案列表

st->op1->dbkeyword->issr
issr(no)->op3->rt->end
issr(yes)->dbrecord1->op2->rt->end

```

### 例行流程

```flow

st=>start: 自動搜尋例行服務
dbkeyword=>inputoutput: 關鍵字資料庫
dbrecord1=>inputoutput: 檔案關鍵字資料庫
dbrecord2=>inputoutput: 檔案關鍵字資料庫
op1=>operation: 搜尋特定檔案夾裡的檔案
isnew=>condition: 新檔案
op2=>operation: 新檔寫入檔案資料庫
op3=>operation: 在新檔案搜尋所有關鍵字
op4=>operation: 將關鍵字寫入檔案關鍵字資料庫
end=>end: 中止

st->op1->isnew
isnew(no)->end
isnew(yes)->dbrecord1->op2->dbkeyword->op3->op4->end

```

## 測試與審核


###### tags: `outsourcing` `keyword search`
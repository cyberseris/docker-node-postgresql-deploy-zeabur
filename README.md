# Zeabur 部署(docker, nodejs, postgresql)
環境建置分 一、資料庫建置跟 二、github 專案建置兩個階段

一、資料庫建置
===

**1. 點擊建立服務**

![zeabur (1)](https://hackmd.io/_uploads/rJQ_6Enllg.png)

**2. 選擇 Docker 容器映像**

![zeabur (2)](https://hackmd.io/_uploads/ByCgs72gex.png)


**3. 輸入 posgres, 一鍵部署**

![zeabur (4)](https://hackmd.io/_uploads/rJRloQhgle.png)

**4. 點擊檔案，可檢視系統檔案**

![zeabur (5)](https://hackmd.io/_uploads/r1AgsX3glg.png)

![zeabur (9)](https://hackmd.io/_uploads/Bypxo72lll.png)

**5. 點擊紀錄，可檢視環境建置 log**

![zeabur (6)](https://hackmd.io/_uploads/HkAxj72ggg.png)

![zeabur (10)](https://hackmd.io/_uploads/Hy0lsXhlgg.png)

**6. 點擊指令，可輸入指令**

![zeabur (7)](https://hackmd.io/_uploads/SJCxjQ3llx.png)

![zeabur (11)](https://hackmd.io/_uploads/rkaeoXnlex.png)

**7. posgresql 環境建置完成**

![zeabur (8)](https://hackmd.io/_uploads/rJCeim3ggl.png)

**8. 檢視環境變數，紅框變數資料將在第二階段 github 專案建置時使用**

![zeabur (12)](https://hackmd.io/_uploads/rJAgjX3exx.png)

**9. 檢視網路，網域跟連接埠將在第二階段 github 專案建置時使用**

![zeabur (13)](https://hackmd.io/_uploads/ByAlom3llg.png)


二、github 專案建置
===

**10. 點擊建立服務**

![image](https://hackmd.io/_uploads/BJx6fZE2xlx.png)

**11. 選擇 Github**

![zeabur (18)](https://hackmd.io/_uploads/B10ximhxgx.png)

**12. 設定 Github 儲存庫**

![zeabur (19)](https://hackmd.io/_uploads/Hy0go73ele.png)

**13. 輸入 github 密碼**

![zeabur (20)](https://hackmd.io/_uploads/Syago73lxg.png)

**14. Select repositories 選擇要部署的 github 專案**

![zeabur (21)](https://hackmd.io/_uploads/Hk0xo72ele.png)

**15. 回到 zeabur，選擇剛剛選取的 github 專案**

![image](https://hackmd.io/_uploads/H1NAW43gel.png)

**16. 點擊部署**

![zeabur (23)](https://hackmd.io/_uploads/rJCximnglx.png)

**17. github 專案環境建置中**

![zeabur (24)](https://hackmd.io/_uploads/S1x0xom3xgx.png)

**18. 點擊設定**

![image](https://hackmd.io/_uploads/S18SzV3xgg.png)

**19. 設定預算**

![zeabur (26)](https://hackmd.io/_uploads/rJg0gsm2xex.png)

**20. 因為 github 專案還未設定環境變數，會顯示崩潰重試中**

![zeabur (27)](https://hackmd.io/_uploads/SJxAljX2exx.png)

**21. 回到剛剛建置的 postgresql 環境，檢視環境變數，記下紅框變數資料**

![zeabur (28)](https://hackmd.io/_uploads/HyCxs73ggg.png)

**22. 檢視網路，記下網域跟連接埠資料**

![zeabur (29)](https://hackmd.io/_uploads/rkeAeoQ3xle.png)

**23. 回到 github 專案環境**

![zeabur (30)](https://hackmd.io/_uploads/rkxAxsX2xle.png)

**24. 檢視網路，點擊綁定 Zeaburu 子網域，Zeabur 有提供免費網域，設定網域，點擊確認綁定**

![zeabur (31)](https://hackmd.io/_uploads/r1xCxi7heel.png)

**25. 網域綁定成功，之後要設定新網域，刪除舊網域重新設定新的就可以**

![image](https://hackmd.io/_uploads/H1ze4V2exl.png)

**26. google 第三方登入設定剛剛綁定的網域網址**

![zeabur (33)](https://hackmd.io/_uploads/SJAeoXhexx.png)

**27. Google Cloud Platform API 服務，設定 google 第三方登入 callback 網址，點擊編輯按鈕(紅框)**

![image](https://hackmd.io/_uploads/rJYs442ggl.png)

**28. 設定重新導向 URI**

![image](https://hackmd.io/_uploads/Bka41B3lle.png)

**29. 回到 github 環境專案環境，設定環境變數**

```
DB_DATABASE = (Zeabur postgresql 環境的 DB 名稱，變數值位置: 環境變數 => POSTGRES_DB 值)

DB_ENABLE_SSL = false

DB_HOST = (Zeabur postgresql 環境的網域，變數值位置: 網路=>網域)

DB_PASSWORD = (Zeabur postgresql 環境的 DB 名稱，變數值位置: 環境變數 => PASSWORD 值)

DB_PORT = (Zeabur postgresql 環境的網域，變數值位置: 網路=>連接埠)

DB_SYNCHRONIZE = true

DB_USERNAME = (Zeabur postgresql 環境的網域，變數值位置: 環境變數 => POSTGRES_USER 值)

GOOGLE_CALLBACK_URL = http://butter-sugar-test.zeabur.app/api/v1/users/auth/google/callback

GOOGLE_CLIENT_ID = (Google Cloud Platform API 服務憑證設定值)

GOOGLE_CLIENT_SECRET = (Google Cloud Platform API 服務憑證設定值)

JWT_SECRET = (自己設個亂數)

LOG_LEVEL = debug

SESSION_SECRET = (自己設個亂數)
```

![zeabur (36)](https://hackmd.io/_uploads/rygRgimhexx.png)

**30. 環境變數設定完後，點擊重啟目前版本重新部署**

![zeabur (38)](https://hackmd.io/_uploads/ByeRgom2xeg.png)

**31. 重新部署中**

![zeabur (39)](https://hackmd.io/_uploads/HJgAxo72lgg.png)

**32. 發現 crash**

![zeabur (40)](https://hackmd.io/_uploads/SJeReiQ2geg.png)

**33. 檢視 log，發現資料庫出現問題**

![zeabur (41)](https://hackmd.io/_uploads/rygAesm2xel.png)

**34. 回到 postgresql-tic 環境，儀錶板會顯示重新建置按鈕，點擊後，重新生成 postgresql-que 環境**

![zeabur (39)](https://hackmd.io/_uploads/HJgAxo72lgg.png)

**35. 回到 github 專案，點擊重新部署**

![zeabur (39)](https://hackmd.io/_uploads/HJgAxo72lgg.png)

**36. github 專案部署成功**

![zeabur (43)](https://hackmd.io/_uploads/HJCes72exe.png)

**37. 簡易前端測試， Open with Live Server**

![zeabur (44)](https://hackmd.io/_uploads/rygRxjXnexl.png)

**38. 選擇要登入的 Email**

![zeabur (45)](https://hackmd.io/_uploads/H1TlsXhggx.png)

**39. 登入成功**

![zeabur (46)](https://hackmd.io/_uploads/r1aloQ2xxx.png)

**40. Postman 測試 API - 取得學生資料**

![zeabur (47)](https://hackmd.io/_uploads/ryJbom3leg.png)

**41. Postman 測試 API - 更新學生資料**

![zeabur (48)](https://hackmd.io/_uploads/ByJWsm3lgx.png)

**42. Postman 測試 API - 更新的學生資料**

![zeabur (49)](https://hackmd.io/_uploads/Byy-sQhgex.png)

**43. Postman 測試 API - 驗證是否登入**

![zeabur (50)](https://hackmd.io/_uploads/Bk1WsQ3gex.png)

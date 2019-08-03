## 打包未簽名ipa

1. scheme 選 真機(或 ios device)
2. build
3. 在 Products 裡面找到 .app 檔案
4. 新建一資料夾取名為 Payload
5. 將 .app 放入 Payload, .app 檔案保持原名
6. 在與 Payload 資料夾同個地方 加入一個 app icon 圖片檔案, 取名為 iTunesArtwork, 不要副檔名
7. app icon 解析度需為 512 x 512
8. 將 iTunesArtwork 以及 Payload 壓成zip
9. 將 zip 副檔名改為 .ipa

[圖解1]()
[圖解2]()

未簽名包至此完成

## 企業包下載

需要(檔名無所謂)
1. app.ipa
2. app.plist 

假設 ipa 跟 plist 的 url 是
ipa   - https://www.example.com/app.ipa
plist - https://www.example.com/app.plist

ios 安裝 ipa 的 url 即是
```
itms-services:///?action=download-manifest&url=https://www.example.com/app.plist
```

直接貼到 safari 的網址列即可下載(但其他瀏覽器無法這樣做)

其他瀏覽器 需以網頁開啟超連結方式

browser_download.html - 
```
<html>
<body>
	<a href="itms-services:///?action=download-manifest&url=https://www.example.com/app.plist">點此安裝ios app</a>
</body>
</html>
```

app.plist 內容 - 

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
	<key>items</key>
	<array>
		<dict>
			<key>assets</key>
			<array>
				<dict>
					<key>kind</key>
					<string>software-package</string>
					<key>url</key>
					<string>https://www.example.com/app.ipa</string>
				</dict>
			</array>
			<key>metadata</key>
			<dict>
				<key>bundle-identifier</key>
				<string>com.example.www</string>
				<key>bundle-version</key>
				<string>1.0</string>
				<key>kind</key>
				<string>software</string>
				<key>subtitle</key>
				<string>副標題名稱</string>
				<key>title</key>
				<string>標題名稱</string>
			</dict>
		</dict>
	</array>
</dict>
</plist>
```




# Stable-Diffusion-For-UKIYOE
Stable Diffusion WebUI本地佈署及其應用——基於Windows系統64位

I. 前言
本文檔目的為方便閣下通過Artificial intelligent (AI)去生產圖片/修改圖片，包括但不限於生成概念圖、LOGO美化、修復低位數圖像。故此通過本教程可使用個人辦公電腦進行低算力的圖像工作。希望此教程能夠一定限度減少閣下工作量。

此文僅對官方文檔安裝教程作一定優化，包括規避一些BUG出現、增加步驟使其更明晰並規避安裝出現的報錯解決方法。

NOTE：
a.此文僅適用於Nvidia 40/30系列顯卡，如需佈署於Nvidia RTX50系列，請留意顯卡CUDA版本及其python 版本等驅動/文件。如需協助，請聯繫本文作者。

b.因各電腦系統版本、顯卡驅動版本等差異，本文可能無法覆蓋所有電腦在安裝過程中所出現之問題，敬請諒解。所出現的問題，請回覆至本文「評論」處，如有解決辦法，將會盡早答覆閣下。

STATEMENT：
本文於2025年8月1日就生成式人工智慧工具Stable Diffusion之技術應用提供內部培訓文檔（下稱“該培訓文檔”）。 該培訓文檔旨在提升員工對新興技術之認知及合法應用能力，以推動業務創新。

需要特別强調的是：
技術能力的掌握，絕不代表被授權將工具用於任何違反所在地法律法規或道德準則的行爲。該培訓文檔僅限技術操作指引，不構成任何形式之法律授權或豁免。

嚴令禁止將所學技術用於：
i.製作或傳播煽動暴力、淫穢、歧視性内容；
ii.侵犯知識產權；
iii.僞造身份文件、簽名或他人肖像；
iv.用於任何違反公序良俗或社會倫理之用途。

如閣下違反AI使用規定，可面臨包括並不限於即時紀律聆訊、經濟責任追溯，嚴重者可能面臨刑事檢控。

II. 安裝前檢查
硬盤：≥450GB 不建議佈署在機械硬盤/SATA端口的固態硬盤中；
CPU：Intel i5、i7、i9 13代及其以上；
顯卡：Nvidia-GPU 記憶體≥8G 4070及其以上；
網絡：確保鏈接 Github.com；
記憶體：DDR4 3200MHz 16GB；
驅動：請保持最新版本Nvidia GeForce Game Ready 驅動程式
[圖片]
III. 環境設定
i.git 安裝
https://git-scm.com/
選擇Downloads
[圖片]
選擇Windows
[圖片]
選擇Git for Windows/x64 Setup
[圖片]
下載後常規安裝即可，可佈署在非系統盤符

NOTE：Git 安裝教程及其本文檔其他軟件安裝教程，請務必保證所有本地地址不能包含任何中文字符或特殊字符：@#￥%……&*（）_+等。
E.g. 正確的不含中文地址爲E:\Software\Git

可根據以下動畫檢查地址欄是否存在中文
[圖片]
ii.Python安裝
https://www.python.org/downloads/release/python-3106/
請打開此網站或直接下載本文附上的安裝包。請核實版本號是否為Python Release Python 3.10.6
暫時無法在飛書文件外展示此內容
請注意，安裝第一步，請務必勾選Add python.exe to PATH
[圖片]
後續請默認安裝，應爲在C盤符（系統盤）
安裝完成後請檢查電腦是否安裝成功，並再次核查版本號。
快捷鍵 Win+R呼出執行窗口，并輸入cmd後確定。
[圖片]
在cmd中輸入代碼
python  --version
應出現python + 版本號3.10.6
[圖片]
iii.安裝Stable Diffusion WebUI
a.請在≥450GB的盤符目錄根下創建“Stable Diffusion”文件夾
b.請打開文件夾，并點擊一次目錄位置，出現全選后，刪除内容，並輸入cmd
[圖片]
輸入以下代碼
git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui.git
完成後應如下圖所示
[圖片]
點擊文件夾内名爲webui-user.bat的文件，此時請勿關閉cmd窗口。
[圖片]
中途如程序提示“請按任意鍵繼續”，關閉cmd窗口，檢查網絡是否能夠鏈接GitHub.com并重新打開webui-user.bat
如有任何問題，請附言於本文評論處。
IV. 模型下載
https://huggingface.co/models?pipeline_tag=text-to-image&sort=downloads
https://civitai.com/
可進入此網站下載開源模型
如 Stable-diffusion-v1-5、majicMIX realistic麥橘寫實等。
於搜索框輸入Stable-diffusion-v1-5
[圖片]
切換至Files and versions界面，並下載V1-5 pruned.ckpt，放置於
E:\Stable Diffusion\stable-diffusion-webui\models\Stable-diffusion
[圖片]
并下載VAE文件，放置于E:\Stable Diffusion\stable-diffusion-webui\models\VAE
[圖片]
[圖片]
請務必檢查安裝的模型是否放置在正確位置。
V.Stable Diffusion中文界面設置
[圖片]
前往Extensions頁面
[圖片]
前往 Available子頁面、點擊Load From，並取消勾選“Localization”
[圖片]
於輸入框中寫入"Hans"        zh_Hant為繁體中文 zh_Hans為簡體中文
[圖片]
切換至Settings界面-并找到User interface
[圖片]
先點擊右上角藍色刷新按鈕，并在下拉框中選擇您所需要的語言版本。
[圖片]
點擊Apply Settings 再點擊 Reload UI
[圖片]
如無法顯示模型，請按藍色刷新按鈕或檢查模型放置地址是否正確
[圖片]
Note：Stable Diffusion WebUI為開源平臺，可加載所需要的模型、插件等，來實現不同的功能。
VI.Stable Diffusion應用
i.生圖功能
[圖片]
請注意，不同的模型所生產的圖片風格均有不同。
請自行嘗試。
ii.修復低像素畫面
切換附加功能頁面-上傳低像素畫面，請選擇majicMIX realistic麥橘寫實模型，並設置Automatic的VAE。只需勾選圖像放大，放大演算法1,可使用Lanczos或者其他，選擇等比縮放，如2.0，則爲兩倍（1000*1000px變爲2000*2000px）,請自行計算縮放后像素。
[圖片]
iii.換裝
選擇圖生圖頁面-并選擇區域重繪，上傳圖片，用鼠標塗抹不需要更改的區域，例如頭和手和背景。
并在遮罩模式點選—重繪非遮罩内容，并在正向提示詞輸入：change cloth, suit, do not change hands and background
[圖片]
并準備一張西裝的PNG，並勾選啓用、完美像素、上傳獨立的控制圖像，上傳圖片至ControNet界面，具體可參考下圖。
[圖片]
完成後並回到網頁頂端，點擊“產生”，如遇圖片生成效果差，請再次點擊或者重新嘗試調整數據。
[圖片]

iv.logo轉3D效果
請選擇文生圖界面，選擇revAnimated_v2Rebirth.safetensors模型，如無，請前往本文IV章節。
[圖片]
[圖片]
[圖片]
請參考
[圖片]
E.g. 
正向提示詞：Gold, uneven texture, bright image, rock rendered on white background, uneven rock texture, studio lighting, high resolution photo, extremely detailed masterpiece, best quality, symbol
反向提示詞：low resolution, bad anatomy, hard edges, neat edges, text, errors, complex background, worst quality, low quality, normal quality, jpeg artifacts, signature, watermark, username, blur
[圖片]
[圖片]
v.換臉
詳情參考
https://zhuanlan.zhihu.com/p/681271763

FAQs
遇到問題請在此尋找解決方案
如需協助，請聯係woo-zingzeon@outlook.com

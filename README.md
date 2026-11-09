# おさかなキーボード  
これは、[おさかなキーボード](https://o24.works/fish/)のためのZMK Firmareの設定リポジトリです。  
キーマップを書き換えておさかなを更新する手順は[ユーザーガイド](https://o24.works/fish/guide/)を参照してください。  
  
## 書き換えていいファイル  
### [fish.keymap](config/boards/shields/fish/fish.keymap)  
キーの割り当てや入力の内容を設定できます。このファイルを視覚的に編集できる[キーマップエディター](https://o24.works/fish/editor/)も活用してください。  
### [fish.conf](config/fish.conf)  
スリープ時間、検出名など、キーボード本体の挙動を設定できます。  
### [Kconfig.defconfig](config/boards/shields/fish/Kconfig.defconfig)
親機の左右を変えることができます。  

## Eyelash ドングルを使う
[Eyelash ドングル](https://github.com/a741725193/zmk-corne-dongle)（nice!nano + OLED）を親機にして、左右のおさかなを両方とも子機として使えます。  
GitHub Actions でビルドされるファームウェアのうち、次の3つを書き込みます。

| 書き込み先 | ファームウェア |
| --- | --- |
| ドングル | `fish_dongle.uf2` |
| 左 | `fish_left_peripheral.uf2` |
| 右 | `fish_right-xiao_ble_zmk-zmk.uf2`（ドングルなしの時と同じ） |

ドングルなしの構成から切り替える時は、3台とも先にリセット用のファームウェアを書き込んでペアリング情報を消してください（左右は `settings_reset-xiao_ble_zmk-zmk.uf2`、ドングルは `settings_reset-nice_nano.uf2`）。  
### [fish_dongle.conf](config/fish_dongle.conf)
ドングルの挙動や画面表示を設定できます。

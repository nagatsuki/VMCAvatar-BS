# VMCAvatar
![logo](https://user-images.githubusercontent.com/6268224/88315584-6c39e500-cd51-11ea-90ee-dec8e7ace307.png)  
![VMCProtocol logo](https://user-images.githubusercontent.com/6268224/88319874-bde56e00-cd57-11ea-9fb4-f0be850cdc95.png)  

VMCAvatarは[バーチャルモーションキャプチャー](https://github.com/sh-akira/VirtualMotionCapture)からモーションデータを受け取って[Beat Saber](https://beatsaber.com/)内にアバターを表示するModです。


## ダウンロード

- [リリース版バイナリ](https://github.com/nagatsuki/VMCAvatar-BS/releases)


## インストール

1. バーチャルモーションキャプチャー v0.42以降のOSC送信に対応したバージョン(2020/04/11現在、**pixivFANBOX版のみ**)に更新する
2. VMCAvatar.dllをBeat SaberのインストールフォルダにあるPluginsフォルダへコピーする
3. バーチャルモーションキャプチャーの「詳細設定」→「OSCでモーション送信を有効にする」のチェックを入れる
4. VRMファイルを読み込む(VRoid Hubからの読み込みは非対応)
5. キャリブレーションをMRモード(下の二つのどちらか)で実行する


## 設定項目

Mod Settings→VMC Avatar

- **Avatar visible in first person(default: ON)** - OFFにすると、HMD内にアバターが表示されなくなります。
袖が大きすぎて視界が塞がれてプレイに支障が出るような状況で使うことを想定しています。
- **TrueVR Mode(default: OFF)** - 通常はプレイヤーの腕の長さと高さを基準にアバターのサイズを変更しますが、ONにするとアバターの腕の長さと高さにプレイヤーのサイズを変更します。
ゲーム内の身長設定を適宜調整してください。(身長10cm変更するとノーツや壁の高さは約5cm変わります)
**「お前がアバターになるんだよ！」 by 猫井夕菜**
- **Enable VRMBlendShape(default: ON)** - BlendShape(まばたき、表情変更等)の機能を停止します。
- **Enable VRMSpringBone(default: ON)** - SpringBone(髪、スカート、尻尾等の揺れ)の機能を停止します。


## トラブルシューティング

### アバターが真っ白になる

現在の制限事項です。
「Settings」→「Advanced Graphics」→「Bloom Post Process」をOFFにしてください。


### プチフリ(数十秒おきに数十～数百ミリ秒の停止)が発生する

ガベージコレクション(GC、メモリの解放処理)が行われるためです。
[TrashMan](https://github.com/monkeymanboy/BeatSaberTrashMan)(ModAssistantでインストール可能)を入れて”Disable GC during gameplay”をONにすると、楽曲のプレイ中はGCが行われなくなります。


### 重い

Unityの仕様上、11.1ミリ秒(Vive系、初代Oculus Riftなど90Hzの場合)以内にBeat Saber本体の処理 + 他のModの処理 + VMCAvatarの処理 + Unityの処理を一つのスレッドで処理しないとならないのでCPU処理が非常にシビアです。
VRChat向けで販売されているモデルなどは改変のしやすさ優先で最適化されていないのでかなり重いので最適化を行ってみてください。
もしくはよりCPU性能の高いPCへ買い換えを検討してください。


### 地面に足がめり込む

[アバターとプレイヤーとの体型の差に由来するバーチャルモーションキャプチャーの仕様](https://twitter.com/sh_akira/status/1248486700621238277)です。
重ね合わせが不完全なため目立ちませんが、LIVやCameraPlus + OBSでも発生します。
TrueVRモードがONの時には特殊な補正をかけてるため発生しません。
[0.3.0で通常モードでも対策を入れます](https://twitter.com/ngtkd/status/1244635367602417666)。


### セイバーと手の位置が合わない

- MRモードでキャリブレーションをしていない。
- OpenVR Input Emulator等でコントローラーの位置をずらしている。
- Room Adjustでプレイエリアをずらしている。
- 公式機能やSaber Tailorでセイバーの位置をずらしている。


### 他

<Beat Saberインストール先>\Logs直下にあるログファイル(日付_時間.log)を送ってくれれば原因究明できるかもしれません。


## ライセンス

### VMCAvatar(MIT License)

[https://github.com/nagatsuki/VMCAvatar-BS](https://github.com/nagatsuki/VMCAvatar-BS)  
Copyright (c) 2019 Yukina Nagatsuki

### VMCAvatarロゴ

[https://twitter.com/hibit_at/status/1256418736191373313](https://twitter.com/hibit_at/status/1256418736191373313)  
[https://twitter.com/hibit_at/status/1256418736191373313](https://twitter.com/hibit_at/status/1256418736191373313)  
Copyright (c) 2020 hibit

### UniVRM(MIT License)

[https://github.com/vrm-c/UniVRM](https://github.com/vrm-c/UniVRM)  
Copyright (c) 2018 DWANGO Co., Ltd. for UniVRM  
Copyright (c) 2018 ousttrue for UniGLTF, UniHumanoid  
Copyright (c) 2018 Masataka SUMI for MToon

### OSCJack(Public Domain)

[https://github.com/keijiro/OscJack](https://github.com/keijiro/OscJack)

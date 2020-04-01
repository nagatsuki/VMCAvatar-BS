# VMCAvatar

VMCAvatarは[バーチャルモーションキャプチャー](https://github.com/sh-akira/VirtualMotionCapture)からモーションデータを受け取って[Beat Saber](https://beatsaber.com/)内にアバターを表示するModです。


## ダウンロード

- [リリース版バイナリ](https://github.com/nagatsuki/VMCAvatar-BS/releases)


## インストール

1. バーチャルモーションキャプチャーv0.42以降に更新する
2. VMCAvatar-x.x.x.zipをBeat Saberのインストールフォルダへ展開する
3. バーチャルモーションキャプチャーの「詳細設定」→「OSCでモーション送信を有効にする」のチェックを入れる
4. キャリブレーションをMRモード(下の二つのどちらか)で実行する


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

アバターとプレイヤーとの体型の差に由来するバーチャルモーションキャプチャーの仕様です。
重ね合わせが不完全なため目立ちませんが、LIVやCameraPlus + OBSでも発生します。
TrueVRモードがONの時には特殊な補正をかけてるため発生しません。


### 他

<Beat Saberインストール先>\Logs直下にあるログファイル(日付_時間.log)を送ってくれれば原因究明できるかもしれません。


## ライセンス

MIT license

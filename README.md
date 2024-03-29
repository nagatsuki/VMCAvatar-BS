# VMCAvatar
![logo](https://user-images.githubusercontent.com/6268224/88315584-6c39e500-cd51-11ea-90ee-dec8e7ace307.png)  
![VMCProtocol logo](https://user-images.githubusercontent.com/6268224/88319874-bde56e00-cd57-11ea-9fb4-f0be850cdc95.png)  

VMCAvatarは[バーチャルモーションキャプチャー](https://github.com/sh-akira/VirtualMotionCapture)からモーションデータを受け取って[Beat Saber](https://beatsaber.com/)内にアバターを表示するModです。


## ダウンロード

- [リリース版バイナリ](https://github.com/nagatsuki/VMCAvatar-BS/releases)


## 関連ソフトウェア

- [必須] [バーチャルモーションキャプチャー](https://vmc.info/) - モーションの送信に使用します
- [必須] [BSIPA](https://github.com/bsmg/BeatSaber-IPA-Reloaded)(ModAssistantでインストール可) - Beat SaberでModをロードするために必要になります
- [必須] [BSML](https://github.com/monkeymanboy/BeatSaberMarkupLanguage)(ModAssistantでインストール可) - UIの表示に必要になります
- [CameraPlus](https://github.com/Snow1226/CameraPlus) - 三人称視点での表示に必要になります
- [VMCAvatarMaterialChange](https://github.com/Reiya1013/VMCAvatarMaterialChange) - Bloomエフェクトを使用したい場合に必要になります
- [NalulunaModifier](https://github.com/nalulululuna/NalulunaModifier) - Feet Saber等をプレイしたい場合に必要になります


## インストール

1. バーチャルモーションキャプチャー v0.42以降のOSC送信に対応したバージョン(2020/04/11現在、**pixivFANBOX版のみ**)に更新する
2. VMCAvatar.dllをBeat Saberのインストールフォルダ**直下**にあるPluginsフォルダへコピーする(Beat Saber\Beat Saber_Data\Plugins**ではありません**)
3. バーチャルモーションキャプチャーの「詳細設定」→「OSCでモーション送信を有効にする」のチェックを入れる
4. VRMファイルを読み込む(VRoid Hubからの読み込みは非対応)
5. キャリブレーションをMRモード(下の二つのどちらか)で実行する


## 設定項目

Mod Settings→VMC Avatar

- **Avatar visible in first person(default: ON)** - OFFにすると、HMD内にアバターが表示されなくなります。
袖が大きすぎて視界が塞がれてプレイに支障が出るような状況で使うことを想定しています。
- **TrueVR Mode(default: OFF)** - VRchatのようにユーザーがアバターサイズになるモードです。通常はプレイヤーの腕の長さと高さを基準にアバターのサイズを変更しますが、ONにするとアバターの腕の長さと高さにプレイヤーのサイズを変更します。
- **Enable VRMBlendShape(default: ON)** - OFFにすると、BlendShape(まばたき、表情変更等)の機能を停止します。
- **Enable VRMSpringBone(default: ON)** - OFFにすると、SpringBone(髪、スカート、尻尾等の揺れ)の機能を停止します。


## トラブルシューティング

### アバターが真っ白になる

アルファチャンネルをBloomエフェクト(光るエフェクト)の強度として扱うBeat Saber側の制限による仕様です。
Beat Saber のゲーム内画面にて、「Settings」→「Advanced Graphics」→「Bloom Post Process」をOFFにするか、[VMCAvatarMaterialChange](https://github.com/Reiya1013/VMCAvatarMaterialChange)を併用してください。


### 重い

Unityの仕様上、11.1ミリ秒(Vive系、初代Oculus Riftなど90Hzの場合)以内にBeat Saber本体の処理 + 他のModの処理 + VMCAvatarの処理 + Unityの処理を一つのスレッドで処理しないとならないのでCPU処理が非常にシビアです。VRMモデルの最適化を検討してください。
- VRChat向けで販売されているモデルなどは改変のしやすさ優先となっていることが多いです。これは最適化されていない状態のため重いです。
- 例えば、MeshBakerなどを用いてメッシュ削減を行うなどです。
- VRMFirstPersonがautoですと2倍重いです。適切に設定することで削減することができます。
- CPU性能の高いPCへ買い換えを検討してください。

### 地面に足がめり込む(0.2.0以前)

[アバターとプレイヤーとの体型の差に由来するバーチャルモーションキャプチャーの仕様](https://twitter.com/sh_akira/status/1248486700621238277)です。
重ね合わせが不完全なため目立ちませんが、LIVやCameraPlus + OBSでも発生します。
TrueVRモードがONの時には特殊な補正をかけてるため発生しません。
0.3.0以降は床の高さを調整してめり込まなくなっています。


### セイバーと手の位置が合わない

- MRモードでキャリブレーションをしていない。
- OpenVR Input Emulator等でコントローラーの位置をずらしている。
- ~~Room Adjustでプレイエリアをずらしている。~~(0.4.0以降では発生しません)
- 公式機能やSaber Tailorでセイバーの位置をずらしている。


### 他

- CustomAvatar MODに付属してるCameraPlusは改変版となっており正常に表示できません。公式版に変更してください。
- <Beat Saberインストール先>\Logs直下にあるログファイル(日付_時間.log)を送ってくれれば原因究明できるかもしれません。

## 連絡先
- Twitter - [@ngtkd](https://twitter.com/ngtkd)
- Discord - 長月ゆきな#9672


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

### GlassPad3CameraBehavior(MIT License)

[https://github.com/Ibodan/GlassPad3CameraBehavior](https://github.com/Ibodan/GlassPad3CameraBehavior)  
Copyright (c) 2020 Ibodan

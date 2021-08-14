# google-drive-with-linux
Linux(Ubuntu20.04LTS)で google driveをマウントして利用する方法についてのメモ

## 初期設定
* 以下の手順でライブラリインストールを行う。
```
sudo add-apt-repository ppa:alessandro-strada/ppa
sudo apt-get update
sudo apt-get install google-drive-ocamlfuse
```
*  gdfuseの設定ファイルを編集する。
```
cd ~/.gdfuse
rsync -avz default/  [your_label]
```
この後、~/.gdfuse/[your_label]/config の中で root_folder と team_drive_id の値を編集する。
```
...
root_folder=[TEAM_DRIVE_ROOT_FOLDER_ID]
...
team_drive_id=[TEAM_DRIVE_FOLDER_ID]
...
```

** 利用手順

* 以下コマンドで認証を行う (Googleログインのブラウザが現れた場合には ID, パスワードを入力)。
```
google-drive-ocamlfuse
```

* マウント実行
```
google-drive-ocamlfuse -label [your_label] [mount_directory]
```

* マウント解除
```
fusermount -u [mount_directory]
```


## 参考資料
* [LinuxでGoogleDriveを利用する](https://minokamo.tokyo/2020/11/21/2945/)
* [google-drive-ocamlfuseでGoogleドライブをマウント](https://qiita.com/cabbage_lettuce/items/c4544b3e5cd28caf04bc)
* [ColaboratoryでGoogleチームドライブをマウントする方法](https://qiita.com/d_desuyon/items/b04d847e4c7eb6811ec8)

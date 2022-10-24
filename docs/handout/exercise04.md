# Exercise4: Blob診断設定

## 【目次】

![](images/ex04-0000-blob.png)

1. [Blobのログ出力設定](#blobのログ出力設定)
2. [ファイル書き込み](#ファイル書き込み)
3. [Monitorでログを確認](#monitorでログを確認)


## Blobのログ出力設定

1. Azureポータル上部の検索窓で「ストレージアカウント」を検索、開く

1. 一覧から環境構築時に作成したストレージアカウントを探して開く

1. [監視]-[診断設定] を開き、Blob を選択

    ![](images/ex04-0101-blob.png)

1. 「診断設定を追加する」を選択

    ![](images/ex04-0102-blob.png)

1. 診断設定を設定して「保存」

    * ログ： `StorageRead`, `StorageWrite`, `StorageDelete`
    * 宛先の詳細： `Log Analytics ワークスペースへの送信` をチェックして 作成済みの Log Analytics ワークスペースを指定

    ![](images/ex04-0103-blob.png)

## ファイル書き込み

1. [データストレージ]-[コンテナー] へ移動

1. 「コンテナー」を選択して「新しいコンテナー」を作成

    * 名前： `share`
    * パブリックアクセスレベル： `プライベート`

    ![](images/ex04-0201-blob.png)

1. 作成したコンテナーに入り、適当なファイルをアップロード

    ![](images/ex04-0202-blob.png)

## Monitorでログを確認

1. Azureポータル上部の検索窓で「モニター」を検索、開く

1. [ログ]を開く

1. 「スコープを選択する」を開き、ストレージアカウントを選択

    ![](images/ex04-0301-blob.png)

1. 範囲の選択にてストレージアカウントを選択して「適用」を押下

    ![](images/ex04-0302-blob.png)

1. 以下のクエリを実行して Blob への書き込みログを確認

        StorageBlobLogs
        | where Category == "StorageWrite"
        | limit 100

    ![](images/ex04-0303-blob.png)


# 次の Exercise へ

* [NSG フローログ](exercise05.md)

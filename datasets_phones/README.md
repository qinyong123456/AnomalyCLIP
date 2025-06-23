# datasets_phones

このディレクトリには画面が割れたスマートフォンの写真300枚を配置してください。
以下のような構造を想定しています。

```
datasets_phones/
    phone/
        train/
            broken/
                xxx.png
                ... (200枚程度)
        test/
            broken/
                yyy.png
                ... (100枚程度)
        ground_truth/
            broken/
                yyy_mask.png
```

`ground_truth` には各テスト画像に対応するマスク画像を配置してください。
マスクが無い場合は空ディレクトリでも構いません。


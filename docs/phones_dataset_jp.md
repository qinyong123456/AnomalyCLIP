# datasets_phones を用いた学習手順

このドキュメントでは、`datasets_phones` ディレクトリに保存された
画面割れスマートフォン画像 300 枚を使って AnomalyCLIP を学習する手順を説明します。

## 1. データセットの準備

以下の構造で画像を配置します。`broken` フォルダには異常画像、`good`
フォルダには正常画像を入れてください。正常画像がない場合、`good` は空でも構いません。

```
AnomalyCLIP/
  datasets_phones/
    phone/
      train/
        broken/
          *.png
        good/    (任意)
      test/
        broken/
          *.png
        good/    (任意)
      ground_truth/
        broken/
          *_mask.png (必要に応じて)
```

画像を配置したら `generate_dataset_json/phones.py` を実行して
`meta.json` を生成します。

```bash
cd generate_dataset_json
python phones.py
```

## 2. 学習の実行

`train.py` を以下のように実行することで学習を開始できます。

```bash
python train.py \
    --dataset phones \
    --train_data_path ./datasets_phones \
    --save_path ./checkpoints/phones_model \
    --features_list 24 \
    --image_size 518 \
    --batch_size 8 \
    --epoch 15
```

学習が完了すると `--save_path` で指定したディレクトリに重みファイルが保存されます。

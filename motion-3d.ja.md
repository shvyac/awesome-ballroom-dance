# 社交ダンス向け 3D モーション・アニメーションツール

[English](motion-3d.md) · [Awesome Ballroom Dance（日本語）に戻る](README.ja.md)

社交ダンス（スタンダード／ラテン）を **3D モーションデータと教材動画** にするためのオープンソースツール集。10ダンスのフットワーク、フロアの進行、ボディのスウェイ・回転を見せる用途を想定。⭐ バッジは GitHub のスター数をリアルタイム表示します(shields.io)。

10ダンス全種目をそろえた公開プロジェクトはまだない。現実的な流れは **撮影（動画→3D モーション）** → **使える社交ダンスのモーションデータを活用** → **描画（Blender またはブラウザ）で足型・スウェイの矢印・カウントを重ねる**。

## 目次

- [動画から 3D モーションへ（モーションキャプチャ）](#動画から-3d-モーションへモーションキャプチャ)
- [社交ダンス・ペアダンスのモーションデータ／研究](#社交ダンスペアダンスのモーションデータ研究)
- [描画・教材動画づくり](#描画教材動画づくり)
- [音楽からのダンス生成（参考）](#音楽からのダンス生成参考)
- [おすすめの手順](#おすすめの手順)

---

## 動画から 3D モーションへ（モーションキャプチャ）

先生のデモ動画から骨格の動き（SMPL / BVH / FBX）を取り出す。スウェイを見せるには、重力や床に対する体幹の傾きまで推定できる手法を選ぶ。

- [GVHMR（英語）](https://github.com/zju3dv/GVHMR) ![GitHub stars](https://img.shields.io/github/stars/zju3dv/GVHMR?style=flat&label=%E2%AD%90) - 単眼動画から重力方向を基準に人体の動きを復元（SIGGRAPH Asia 2024）。重力に対する体の傾きが分かるため、スウェイの可視化に向く。
- [WHAM（英語）](https://github.com/yohanshin/WHAM) ![GitHub stars](https://img.shields.io/github/stars/yohanshin/WHAM?style=flat&label=%E2%AD%90) - 単眼動画から 3D の動きと床上の移動軌跡を復元。ステップの進行方向の確認に便利。
- [4D-Humans（英語）](https://github.com/shubham-goel/4D-Humans) ![GitHub stars](https://img.shields.io/github/stars/shubham-goel/4D-Humans?style=flat&label=%E2%AD%90) - 動画内の複数人を Transformer で復元・追跡（HMR 2.0）。カップルにも対応。
- [FreeMoCap（英語）](https://github.com/freemocap/freemocap) ![GitHub stars](https://img.shields.io/github/stars/freemocap/freemocap?style=flat&label=%E2%AD%90) - 普通のカメラ複数台で使える無料マーカーレスモーキャプ。Blender への書き出しあり。スタジオ撮影向け。
- [EasyMocap（英語）](https://github.com/zju3dv/EasyMocap) ![GitHub stars](https://img.shields.io/github/stars/zju3dv/EasyMocap?style=flat&label=%E2%AD%90) - 多視点マーカーレスモーキャプのツールボックス。より高精度。

## 社交ダンス・ペアダンスのモーションデータ／研究

- [Dancing Points（英語）](https://github.com/PeizhuoLi/dancing-points) ![GitHub stars](https://img.shields.io/github/stars/PeizhuoLi/dancing-points?style=flat&label=%E2%AD%90) - VR の3点入力からリーダーとフォロワーの全身の社交ダンスモーションを合成（Computer Graphics Forum 2026）。カップルのモーキャプデータを FBX で公開（チャチャチャ、フォックストロット、ヴェニーズワルツを含む）。再生用の [Unity プロジェクト](https://github.com/PeizhuoLi/dancing-points-unity) ![GitHub stars](https://img.shields.io/github/stars/PeizhuoLi/dancing-points-unity?style=flat&label=%E2%AD%90) もあり。
- [Duolando（英語）](https://github.com/lisiyao21/Duolando) ![GitHub stars](https://img.shields.io/github/stars/lisiyao21/Duolando?style=flat&label=%E2%AD%90) - デュエットダンスのフォロワー動作生成（ICLR 2024）。デュエットデータセット DD100 付き。
- [interDance_API（英語）](https://github.com/inter-dance/interDance_API) ![GitHub stars](https://img.shields.io/github/stars/inter-dance/interDance_API?style=flat&label=%E2%AD%90) - デュエットダンスデータセット InterDance の描画用コード（[論文](https://arxiv.org/abs/2412.16982)）。
- [BDD（英語）](https://github.com/matsuyhit/BDD) ![GitHub stars](https://img.shields.io/github/stars/matsuyhit/BDD?style=flat&label=%E2%AD%90) - HASC 社交ダンスデータセットの紹介と分析。

## 描画・教材動画づくり

- [Blender（英語）](https://github.com/blender/blender) ![GitHub stars](https://img.shields.io/github/stars/blender/blender?style=flat&label=%E2%AD%90) - FBX / BVH を読み込んで動画を作成。Python スクリプトで床の足型、骨盤・頭の軌跡、背骨の傾き（スウェイ）の矢印、S・Q・& のカウント字幕を追加できる。
- [three.js（英語）](https://github.com/mrdoob/three.js) ![GitHub stars](https://img.shields.io/github/stars/mrdoob/three.js?style=flat&label=%E2%AD%90) - ブラウザ用 3D ライブラリ。視点回転・スロー再生・フィガーのループ再生ができる教材に。
- [three-vrm（英語）](https://github.com/pixiv/three-vrm) ![GitHub stars](https://img.shields.io/github/stars/pixiv/three-vrm?style=flat&label=%E2%AD%90) - three.js で VRM アバターを使い、キャラクターでダンスの動きを見せる。

## 音楽からのダンス生成（参考）

音楽からダンスを生成するが、主にソロのストリート／ポップダンス（AIST++）で学習しているため、10ダンスの正しいフィガーやスウェイは出せない。教材には撮影データやモーキャプデータを使うこと。

- [EDGE（英語）](https://github.com/Stanford-TML/EDGE) ![GitHub stars](https://img.shields.io/github/stars/Stanford-TML/EDGE?style=flat&label=%E2%AD%90) - 拡散モデルによる編集可能な音楽→ダンス生成（CVPR 2023）。
- [Bailando（英語）](https://github.com/lisiyao21/Bailando) ![GitHub stars](https://img.shields.io/github/stars/lisiyao21/Bailando?style=flat&label=%E2%AD%90) - Actor-Critic GPT と振付メモリによる 3D ダンス生成（CVPR 2022）。

## おすすめの手順

1. 先生のお手本を 2〜4 台のカメラ（FreeMoCap）または 1 台（GVHMR）で撮影する。
2. 書き出したモーションを Blender に読み込む。
3. 足型・スウェイの角度・カウントを重ねる。
4. ダンス・フィガーごとに動画にする。

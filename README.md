# Conflictマージ等の失敗で失われた歴史を取り戻すテスト

## edit/A

target.md を編集しつつ AdditionalFileA.md を追加

## edit/B

target.md を編集しつつ AdditionalFileB.md を追加

## illegalWorld

- edit/B ブランチに edit/A をマージ
- target.md の衝突を解消しつつも
「見知らぬファイル」として、AdditionalFileA.md をステージからよけてしまった状態
- edit/A ブランチはもうマージできない

## temporary

- illegalWorldに edit/A を再度取り込むためのブランチ
- 問題のcommitの一つ前から分岐して、あらためて edit/A をマージする
  - illegalWorld で起きた不正なマージをやりなおすブランチ

## fixedWorld

- illegalWorldに対して、temporaryで作ったマージcommitをcherry-pick して適用したブランチ
- cherry-pickした場合はマージではなく、差分取り込みなので合流が可能

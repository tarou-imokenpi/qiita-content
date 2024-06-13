---
title: Fabric for Minecraft 1.21 日本語訳
tags:
  - minecraft
private: true
updated_at: '2024-06-13T22:57:25+09:00'
id: b6f933ab297828d677e3
organization_url_name: null
slide: false
ignorePublish: false
---
Minecraft 1.21用のFabric
2024年5月31日

Minecraft 1.21は6月13日にリリースされる予定で、モッド開発者に影響を与える重要な変更がいくつかあります。

前回のブログ投稿からわずか1か月半しか経っていませんが、このアップデートは小さなものではありません。多くのモッドに影響を与える可能性があります。

いつものように、すべてのプレイヤーに対して、モッド開発者が新しいバージョンに更新する時間を与えるようにお願いしています。彼らを急かさないようご協力をお願いします。また、すべてのプレイヤーがワールドのバックアップを作成することをオススメします。

このバージョンでの主なモッド制作者向けの変更点のリストは以下の通りです。すべてのコードリファレンスはYarnマッピングを使用しています。別のマッピングを使用するモッダーは、異なる名前を使用する必要があるかもしれません。

### Fabricの変更点
Minecraft 1.21用のモッドを開発するには、開発者はLoom 1.6（執筆時点）を使用する必要があります。プレイヤーは最新の安定版Fabric Loader（現在は0.15.11）をインストールする必要があります。

### 新しいFabric APIの変更点
多くの貢献者の協力により、Fabric APIには前回のアップデートブログ投稿以来、新しい機能が追加されました：

- **Conventional Tags**: c名前空間タグのデフォルト英語翻訳（TelepathicGrunt）
- **Data Generation**: datagenで動的レジストリを拡張するサポート（SquidDev）
- **Item API**: デフォルトのアイテムコンポーネントを変更するAPIの追加（modmuss50）
- **Resource Conditions**: 配列ではなく単一のリソース条件の読み込みサポート（Apollo）
- **Resource Conditions**: レジストリリソース条件（SquidDev）
- **Removed Herobrine** (Tiny Potato)

### タグの翻訳
提供するアイテムタグの英語翻訳を提供することが強く推奨されます。たとえば、`test:potatoes`の翻訳は以下のように宣言されるべきです：

```json
{
    "tag.item.test.potatoes": "Potatoes"
}
```
これらはAPI自体では使用されませんが、他のモッド（レシピビューアなど）が正しく表示するために依存しています。

### 破壊的な変更
注：バニラの変更に関連する破壊的な変更は以下で別途取り上げられています。

1つの非推奨モジュールが削除されました：`fabric-models-v0`。

Item APIでは、`EquipmentSlotProvider#getPreferredEquipmentSlot`が`LivingEntity`を引数として受け取るようになりました。実装はスロットが使用可能かどうかを`entity.canUseSlot(EquipmentSlot)`を使用してチェックすることが期待されます。`FabricItem#getAttributeModifiers`は削除され、`Default Components API`を使用する必要があります。

レジストリ同期は以前より早い段階でレジストリを凍結します。これは`ModInitializers`で物を登録するモッドには影響しませんが、より複雑なモッドに影響する可能性があります。すべてを`ModInitializer`中に登録するようにしてください。

### Minecraftの変更点
このバージョンでは、データ駆動のエンチャントを含む多くの破壊的な変更が行われました。データパック構造も変わり、多くの場所で複数形から単数形に変更されました。

#### Identifier
`Identifier`コンストラクターは現在保護されています。`Identifier`を構築するには、静的メソッド`of`または`ofVanilla`を使用します。テキストエディタやIDEを使用して`new Identifier`を`Identifier.of`に置き換えるだけで十分です。

```java
- var id = new Identifier("example", "foo_bar");
- var id2 = new Identifier("test:single_argument");
- var creeper = new Identifier("minecraft", "creeper");
- @Nullable var customId = Identifier.of("namespace", unsanitizedInput);
+ var id = Identifier.of("example", "foo_bar");
+ var id2 = Identifier.of("test:single_argument");
+ var creeper = Identifier.ofVanilla("creeper"); // very slightly improved performance
+ @Nullable var customId = Identifier.tryParse("namespace", unsanitizedInput);
```

プロのヒント：モッドの名前空間用に`Identifier`を構築するメソッドを作成し、あとで`import static`を使用してインポートしてコードを短縮できます。

```java
public static Identifier id(String path) {
    return Identifier.of("mod_namespace", path);
}
```

#### エンチャント
エンチャントは現在データ駆動です。つまり、もはやハードコードされていません。データパックの一部です。その結果、モッドがエンチャントを処理する方法にいくつかの重要な変更があります。

一般的に、エンチャントは「何かをする」（例：爆発を引き起こす）か「値を変更する」（例：攻撃ダメージ）いずれかです。たとえば、プレイヤーが棘のエンチャントを持っているかどうかをチェックして攻撃者にダメージを与えるのではなく、現在は`EnchantmentHelper#onTargetDamaged`を呼び出す必要があります。もう1つの例として、ノックバックのレベルをチェックするのではなく、現在は`EnchantmentHelper#modifyKnockback`を呼び出す必要があります。

ときどき、コードはアイテムが特定のエンチャントを持っているかどうかをチェックする必要があります。エンチャントがもはやハードコードされていないため、これはエンチャントタグを使用して行われます。たとえば、シルクタッチで蜂の巣を壊すと、蜂が放たれません。以前はシルクタッチのエンチャントをチェックして行っていましたが、現在は`EnchantmentHelper#hasAnyEnchantmentsIn(stack, EnchantmentTags#PREVENTS_BEE_SPAWNS_WHEN_MINING)`を呼び出すことで行われます。

#### エンチャントのコード構造
エンチャントは、ダイナミックレジストリによって定義されるため、`RegistryEntry<Enchantment>`として扱われます。これらは動的レジストリから取得でき、たとえば`world.getRegistryManager()`や、さまざまなメソッドに渡される`registryLookup`から取得できます。

エンチャントには効果コンポーネントがあり、これは効果タイプと効果のリストのマップです。効果タイプは、エンチャントが動作を定義できる事前定義されたキーです。たとえば、エンチャントがDAMAGE効果タイプの「2倍にする」動作や、POST_ATTACK効果タイプの「爆発する」動作を追加したい場合があります。これらは`EnchantmentEffectComponentTypes`で定義されています。

効果コンポーネントの値は`EnchantmentEffectEntry`です。これは効果と任意の条件のペアです。`LootCondition`はこの目的で再利用されます。

エンチャント効果は3つのカテゴリーに分類されます：

- **EnchantmentValueEffect**: 値が与えられると、その値を計算して変更します。例としては、プロテクション（DAMAGE_PROTECTIONを変更）、ルアー（FISHING_LUCK_BONUS）、耐久力（ITEM_DAMAGE）、マルチショット（PROJECTILE_COUNT）があります。
- **EnchantmentEntityEffect**: トリガーされたときに何かを行います。例としては、棘やチャネリング（POST_ATTACK）、フレイム（PROJECTILE_SPAWNED）があります。
- **AttributeEnchantmentEffect**: エンティティに属性を追加します。エンティティ効果とは異なり、属性はエンチャントが適用されなくなるまで持続します。

`EnchantmentLocationBasedEffect`は`EnchantmentEntityEffect`および`AttributeEnchantmentEffect`によって実装されるインターフェースです。さらに、いくつかのエンチャント効果タイプは、単に効果値を直接指定する必要があります。たとえば、CROSSBOW_CHARGING_SOUNDSはサウンドのリストです。一

部の効果（例：PREVENT_ARMOR_CHANGE）はさらに構成できません。

#### バニラのエンチャントの使用
`EnchantmentHelper`メソッドは、バニラのエンチャントを処理するために使用できます。

```java
// 値を変更する例
float newDamage = EnchantmentHelper.getDamage(
    world,
    stack,
    attackTarget,
    damageSource,
    baseDamage
);

// 基本値がない場合（例：プロテクション）の場合
float protection = EnchantmentHelper.getProtectionAmount(
    world,
    user,
    damageSource
);

// エンティティベースの効果
EnchantmentHelper.onTargetDamaged(
    world,
    attackTarget,
    damageSource,
    weapon
);

// ItemStackが特定のエンチャントを持っているかどうかをチェックする
if (EnchantmentHelper.hasAnyEnchantmentsIn(
    stack,
    EnchantmentTags.PREVENTS_BEE_SPAWNS_WHEN_MINING
)) {
    return;
}

// 非構成可能な効果のチェック
// 例：束縛の呪いのチェック
if (EnchantmentHelper.hasAnyEnchantmentsWith(
    stack,
    EnchantmentEffectComponentTypes.PREVENT_ARMOR_CHANGE
)) {
    return;
}
```

### 新しいエンチャントの追加
新しいエンチャントの追加は、JSONファイルを書くことで行います。データ生成を使用して、エンチャントを簡単に生成できます。

エンチャントは、多くのタスクを実行できます。たとえば、属性を適用する、ブロックを置き換える、エンティティを召喚するなどです。ただし、すべてのことが可能ではありません。カスタム効果タイプを追加するには、新しい効果クラスを作成し、そのコーデックを登録する必要があります。効果タイプはクライアントとサーバーの両方に存在する必要があります。

エンチャントタグは、排他的なエンチャント（例：幸運とシルクタッチ）やエンチャントが取得できる場所を指定するために使用されます。エンチャントをこれらのタグに追加することを忘れないでください。

### エンチャント関連のFabric APIの変更点
次のイベントコールバックは、`Enchantment`の代わりに`RegistryEntry<Enchantment>`を渡します：

- `EnchantmentEvents.AllowEnchanting#allowEnchanting`
- `FabricItem#canBeEnchantedWith`
- `FabricItemStack#canBeEnchantedWith`

`EnchantmentContext`は再構築されました。以前は、コンテキストは`RANDOM_ENCHANTMENT`、`ANVIL`、`ENCHANT_COMMAND`、または`LOOT_RANDOM_ENCHANTMENT`のいずれかでした。その目的を明確にするために、現在は`ACCEPTABLE`（例：アンビル）または`PRIMARY`（例：エンチャントテーブル）のいずれかです。例えば、ヘルメットはアンビルで棘のエンチャントを付けることができますが、エンチャントテーブルではできません。なぜなら、棘のエンチャントの`PRIMARY`はチェストプレートだけだからです。

### テレポーテーション
次元内および次元間のテレポーテーションは、現在`Entity#teleportTo`（以前は`moveToWorld`として知られていました）を使用して実行できます。`TeleportTarget`には、目的地のワールドと位置が含まれます。

`FabricDimensions`は削除されました。唯一のAPIである`teleport`は、事実上`Entity#teleportTo`に取って代わられました。

### データパスのパス
データパックは、次のパスで単数名詞を使用します：

- タグのサブディレクトリ（`tags/blocks`、`tags/entity_types`、`tags/functions`など）は`tags/block`、`tags/entity_type`、`tags/function`に変更されました。タグディレクトリ自体は複数形のままです。
- 実績（以前は`advancements`、現在は`advancement`）。
- 関数（`functions`から`function`）。
- アイテム修飾子/ルート関数（`item_modifiers`から`item_modifier`）。
- ルートテーブル（`loot_tables`から`loot_table`）。
- 条件/ルート条件（`predicates`から`predicate`）。
- レシピ（`recipes`から`recipe`）。
- 構造（`structures`から`structure`）。

Fabric APIニュースでは、GameTest構造ディレクトリも単数形に変更されました。以前は`gametest/structures`でしたが、現在は`gametest/structure`に配置されています。

### レンダリングの変更点
Fabric Rendering APIでは、`HudRenderCallback`が`tickDelta`の代わりに`RenderTickCounter`を渡すようになりました。`tickDelta`はカウンターから取得できます。`WorldRenderContext`の`tickDelta`および`limitTime`メソッドも`tickCounter`に置き換えられました。

レンダリングに関する他の重要な内部リファクタリングもあります。たとえば、`BufferBuilder#next()`は削除され、ビルドプロセスを開始または終了するメソッドが変更されました：

```java
- BufferBuilder builder = tessellator.getBuffer();
- builder.begin(...);
+ BufferBuilder builder = tessellator.begin(...);
- builder.vertex(...).texture(...).color(...).next();
+ builder.vertex(...).texture(...).color(...);
- tessellator.draw();
+ BufferRenderer.drawWithGlobalProgram(builder.end());
```

### その他
`FabricCodecProvider`は、ディレクトリ名の代わりに`RegistryKey`を取る新しいコンストラクターを持っています。これを使用して、たとえばアイテム修飾子プロバイダーなどを使用できます。旧コンストラクターは非登録コーデックにはまだ使用できます。

---
title: paper-api 1.20.4-R0.1-SNAPSHOT API イベントクラス一覧と説明
tags:
  - API
  - minecraft
  - Plugin
  - PaperMC
private: false
updated_at: '2024-06-10T21:41:37+09:00'
id: 88d9bc544966f620197d
organization_url_name: null
slide: false
ignorePublish: false
---
# paper-api 1.20.4-R0.1-SNAPSHOT API イベントクラス一覧と説明
イベントの種類についてのメモです。

https://jd.papermc.io/paper/1.20.4/org/bukkit/event/package-summary.html

### ブロックに関するイベント
| クラス名 | 説明 |
|----|----|
| BellResonateEvent | ベルが鳴った後、近くの襲撃者をハイライトするために共鳴したときに呼び出されます。 |
| BellRingEvent | ベルが鳴らされているときに呼び出されます。 |
| BlockBreakEvent | プレイヤーによってブロックが破壊されたときに呼び出されます。 |
| BlockBurnEvent | ブロックが火によって焼失したときに呼び出されます。 |
| BlockCanBuildEvent | ブロックを置こうとしたときに、ここに建てることができるかどうかを確認するために呼び出されます。 |
| BlockCookEvent | ブロックでアイテムスタックが正常に調理されたときに呼び出されます。 |
| BlockDamageAbortEvent | プレイヤーがブロックの破壊を中止したときに呼び出されます。 |
| BlockDamageEvent | プレイヤーがブロックを破壊したときに呼び出されます。 |
| BlockDispenseArmorEvent | ブロックから装備可能なアイテムが放出され、近くのエンティティに装備されたときに呼び出されます。 |
| BlockDispenseEvent | ブロックからアイテムが放出されたときに呼び出されます。 |
| BlockDropItemEvent | プレイヤーによってブロックが破壊され、潜在的なドロップが計算された後、ドロップが存在しない場合でも呼び出されます。 |
| BlockEvent | ブロックに関連するイベントを表します。 |
| BlockExpEvent | ブロックが経験値を与えるときに呼び出されるイベント。 |
| BlockExplodeEvent | ブロックが爆発したときに呼び出されます。 |
| BlockFadeEvent | ブロックが消失、溶解、または世界の条件に基づいて消えるときに呼び出されます。 |
| BlockFertilizeEvent | プレイヤーがボーンミールを使用して特定のブロックを肥料にした結果生じるブロックの変化に呼び出されます。 |
| BlockFormEvent | ブロックが世界の条件に基づいて形成または拡散したときに呼び出されます。 |
| BlockFromToEvent | ソースブロックとデスティネーションブロックを持つイベントを表します。現在は液体（溶岩と水）およびテレポートするドラゴンの卵にのみ適用されます。 |
| BlockGrowEvent | ブロックが自然に成長したときに呼び出されます。 |
| BlockIgniteEvent | ブロックが点火されたときに呼び出されます。 |
| BlockMultiPlaceEvent | プレイヤーの1つのブロック配置アクションが複数のブロックの生成を引き起こしたときに発生します（例：） |
| BlockPhysicsEvent | ブロック物理チェックが呼び出されたときに投げられます。 |
| BlockPistonEvent | ピストンブロックがトリガーされたときに呼び出されます。 |
| BlockPistonExtendEvent | ピストンが拡張されたときに呼び出されます。 |
| BlockPistonRetractEvent | ピストンが収縮されたときに呼び出されます。 |
| BlockPlaceEvent | プレイヤーがブロックを配置したときに呼び出されます。 |
| BlockReceiveGameEvent | スカルクセンサーがゲームイベントを受信し、アクティブになる可能性があるときに呼び出されます。 |
| BlockRedstoneEvent | レッドストーン電流が変化したときに呼び出されます。 |
| BlockShearEntityEvent | ディスペンサーが近くの羊の毛を刈ったときに発生するイベント。 |
| BlockSpreadEvent | ブロックが世界の条件に基づいて拡散したときに呼び出されます。 |
| BrewingStartEvent | 醸造スタンドが醸造を開始したときに呼び出されます。 |
| CampfireStartEvent | キャンプファイヤーが調理を開始したときに呼び出されます。 |
| CauldronLevelChangeEvent | |
| EntityBlockFormEvent | エンティティによってブロックが形成されたときに呼び出されます。 |
| FluidLevelChangeEvent | 隣接するブロックの変化によりブロックの流体レベルが変化したときに呼び出されます。 |
| InventoryBlockStartEvent | 使用される場合：かまどが製錬を開始したとき（FurnaceStartSmeltEvent）醸造スタンドが醸造を開始したとき（BrewingStartEvent）キャンプファイヤーが調理を開始したとき（CampfireStartEvent） |
| LeavesDecayEvent | 葉が自然に崩壊したときに呼び出されます。 |
| MoistureChangeEvent | 土壌ブロックの湿度レベルが変化したときに呼び出されます。 |
| NotePlayEvent | ノートブロックがプレイヤーの操作やレッドストーン電流を通じて再生されるときに呼び出されます。 |
| SculkBloomEvent | スカルクキャタリストによって新しいカーソルが作成されたときに発生するイベント。 |
| SignChangeEvent | プレイヤーによってサインが変更されたときに呼び出されます。 |
| SpongeAbsorbEvent | スポンジが世界から水を吸収したときに呼び出されます。 |
| TNTPrimeEvent | 世界のTNTブロックが点火されたときに呼び出されます。 |

### コマンドに関するイベント

| クラス名 | 説明 |
|----|----|
| UnknownCommandEvent | プレイヤーが定義されていないコマンドを実行したときに投げられます。 |

### エンチャントに関するイベント

| クラス名 | 説明 |
|----|----|
| EnchantItemEvent | アイテムスタックがエンチャントテーブルで成功裏にエンチャントされたときに呼び出されます。 |
| PrepareItemEnchantEvent | アイテムスタックがエンチャントテーブルに挿入されたときに呼び出されます - 複数回呼び出される可能性があります。 |

### エンティティに関するイベント

| クラス名 | 説明 |
|----|----|
| AreaEffectCloudApplyEvent | 持続効果ポーションがその効果を適用したときに呼び出されます。 |
| ArrowBodyCountChangeEvent | 矢がエンティティの体に入り込むか出るときに呼び出されます。 |
| BatToggleSleepEvent | コウモリが眠ろうとするか、眠りから覚めようとするときに呼び出されます。 |
| CreatureSpawnEvent | 生物が世界にスポーンしたときに呼び出されます。 |
| CreeperPowerEvent | クリーパーが雷に打たれたときに呼び出されます。 |
| EnderDragonChangePhaseEvent | エンダードラゴンがコントローラーフェーズを切り替えたときに呼び出されます。 |
| EntityAirChangeEvent | エンティティの残りの空気量が変化したときに呼び出されます。 |
| EntityBreakDoorEvent | エンティティがドアを破壊したときに呼び出されます。 |
| EntityBreedEvent | エンティティが他のエンティティと繁殖したときに呼び出されます。 |
| EntityChangeBlockEvent | エンティティがブロックを変更し、より具体的なイベントが利用できないときに呼び出されます。 |
| EntityCombustByBlockEvent | ブロックがエンティティを燃焼させたときに呼び出されます。 |
| EntityCombustByEntityEvent | エンティティが他のエンティティを燃焼させたときに呼び出されます。 |
| EntityCombustEvent | エンティティが燃焼したときに呼び出されます。 |
| EntityCreatePortalEvent | **非推奨。** PortalCreateEventを使用してください。 |
| EntityDamageByBlockEvent | エンティティがブロックによってダメージを受けたときに呼び出されます。 |
| EntityDamageByEntityEvent | エンティティが他のエンティティによってダメージを受けたときに呼び出されます。 |
| EntityDamageEvent | ダメージイベントのデータを格納します。 |
| EntityDeathEvent | 生きているエンティティが死亡したときに投げられます。 |
| EntityDismountEvent | エンティティが他のエンティティから降りたときに呼び出されます。 |
| EntityDropItemEvent | エンティティがアイテムをドロップしたときに投げられます。 |
| EntityEnterBlockEvent | エンティティがブロックに入り、そのブロックに格納されるときに呼び出されます。 |
| EntityEnterLoveModeEvent | エンティティがラブモードに入ったときに呼び出されます。 |
| EntityEvent | エンティティに関連するイベントを表します。 |
| EntityExhaustionEvent | 人間のエンティティが疲労を感じたときに呼び出されます。 |
| EntityExplodeEvent | エンティティが爆発し、ブロックと相互作用したときに呼び出されます。 |
| EntityInteractEvent | エンティティがオブジェクトと対話したときに呼び出されます。 |
| EntityKnockbackByEntityEvent | **非推奨、削除予定：** このAPI要素は将来のバージョンで削除される予定です。 EntityKnockbackByEntityEventを使用してください。 |
| EntityKnockbackEvent | **非推奨、削除予定：** このAPI要素は将来のバージョンで削除される予定です。 EntityKnockbackEventを使用してください。 |
| EntityMountEvent | エンティティが他のエンティティに乗ろうとしたときに呼び出されます。 |
| EntityPickupItemEvent | エンティティが地面からアイテムを拾い上げたときに投げられます。 |
| EntityPlaceEvent | プレイヤーがアイテムをブロックに置いてエンティティを作成したときにトリガーされます。 |
| EntityPortalEnterEvent | エンティティがポータルに接触したときに呼び出されます。 |
| EntityPortalEvent | プレイヤー以外のエンティティがポータルに接触してテレポートしようとする直前に呼び出されます。 |
| EntityPortalExitEvent | エンティティがポータルから出ようとする直前に呼び出されます。 |
| EntityPoseChangeEvent | エンティティが姿勢を変えたときに呼び出されます。 |
| EntityPotionEffectEvent | エンティティに対するポーション効果が変更されたときに呼び出されます。 |
| EntityRegainHealthEvent | 健康回復イベントのデータを格納します。 |
| EntityRemoveEvent | **非推奨、削除予定：** このAPI要素は将来のバージョンで削除される予定です。 代わりにEntityRemoveFromWorldEventを使用してください。 |
| EntityResurrectEvent | エンティティが死亡し、復活する可能性があるときに呼び出されます。 |
| EntityShootBowEvent | 生きているエンティティが弓を射って矢を発射したときに呼び出されます。 |
| EntitySpawnEvent | エンティティが世界にスポーンしたときに呼び出されます。 |
| EntitySpellCastEvent | 呪文を唱えるエンティティが呪文を唱えたときに呼び出されます。 |
| EntityTameEvent | 生きているエンティティが飼いならされたときに投げられます。 |
| EntityTargetEvent | 生物が他のエンティティをターゲットにしたり、ターゲットから外したりしたときに呼び出されます。 |
| EntityTargetLivingEntityEvent | エンティティが生きているエンティティをターゲットにし、ターゲットにできるのが生きているエンティティのみの場合に呼び出されます。 |
| EntityTeleportEvent | プレイヤー以外のエンティティが一つの場所から別の場所にテレポートされたときに投げられます。 |
| EntityToggleGlideEvent | エリトラを使ってエンティティの滑空ステータスが切り替えられたときに送信されます。 |
| EntityToggleSwimEvent | エンティティの泳ぎステータスが切り替えられたときに送信されます。 |
| EntityTransformEvent | エンティティが他のエンティティに置き換えられようとするときに呼び出されます。 |
| EntityUnleashEvent | エンティティが解放される直前に呼び出されます。 |
| ExpBottleEvent | 投げられた経験値瓶が命中し、経験値を放出したときに呼び出されます。 |
| ExplosionPrimeEvent | エンティティが爆発を決定したときに呼び出されます。 |
| FireworkExplodeEvent | 花火が爆発したときに呼び出されます。 |
| FoodLevelChangeEvent | 人間のエンティティの食糧レベルが変化したときに呼び出されます。 |
| HorseJumpEvent | 馬がジャンプしたときに呼び出されます。 |
| ItemDespawnEvent | アイテムが5分間存在したために世界から削除されたときに呼び出されます。 |
| ItemMergeEvent | |
| ItemSpawnEvent | アイテムが世界にスポーンしたときに呼び出されます。 |
| LingeringPotionSplashEvent | 持続効果ポーションがエリアに命中したときに呼び出されます。 |
| PiglinBarterEvent | ピグリンとの物々交換のデータをすべて格納します。 |
| PigZapEvent | 豚が電撃を受けたときのデータを格納します。 |
| PigZombieAngerEvent | 豚のゾンビが他のエンティティに怒ったときに呼び出されます。 |
| PlayerDeathEvent | プレイヤーが死亡したときに投げられます。 |
| PlayerLeashEntityEvent | プレイヤーが生物をリードでつなぐ直前に呼び出されます。 |
| PotionSplashEvent | スプラッシュポーションがエリアに命中したときに呼び出されます。

### 吊られたエンティティに関するイベント

| クラス名 | 説明 |
|----|----|
| HangingBreakByEntityEvent | 吊るされたエンティティが他のエンティティによって削除されたときにトリガーされます。 |
| HangingBreakEvent | 吊るされたエンティティが削除されたときにトリガーされます。 |
| HangingEvent | 吊るされたエンティティに関連するイベントを表します。 |
| HangingPlaceEvent | 吊るされたエンティティが世界に作成されたときにトリガーされます。 |

### インベントリ操作に関するイベント

| クラス名 | 説明 |
|----|----|
| BrewEvent | 醸造台内の内容物の醸造が完了したときに呼び出されます。 |
| BrewingStandFuelEvent | アイテムスタックが醸造台の燃料レベルを増加させる直前に呼び出されます。 |
| CraftItemEvent | アイテムのレシピが作業台内で完成したときに呼び出されます。 |
| FurnaceBurnEvent | アイテムスタックがかまどのようなブロック（例：かまど、燻製機、高炉）で燃料として正常に燃焼されたときに呼び出されます。 |
| FurnaceExtractEvent | プレイヤーがかまどのようなブロック（例：かまど、燻製機、高炉）からアイテムを取り出すときに呼び出されます。 |
| FurnaceSmeltEvent | アイテムスタックがかまどのようなブロック（例：かまど、燻製機、高炉）で正常に製錬されたときに呼び出されます。 |
| FurnaceStartSmeltEvent | かまどのようなブロックが製錬を開始したときに呼び出されます。 |
| HopperInventorySearchEvent | ホッパーがその供給元/接続されたコンテナを見つけようとするたびに呼び出されるイベント。 |
| InventoryClickEvent | プレイヤーがインベントリ内でクリックしたときに呼び出されます。 |
| InventoryCloseEvent | プレイヤーがインベントリを閉じたときに呼び出されます。 |
| InventoryCreativeEvent | クリエイティブモードのプレイヤーがインベントリ/ホットバーにアイテムを置くまたは拾う、またはクリエイティブモード中にインベントリからアイテムをドロップしたときに呼び出されます。 |
| InventoryDragEvent | プレイヤーがカーソルでアイテムをインベントリ内でドラッグしたときに呼び出されます。 |
| InventoryEvent | プレイヤー関連のインベントリイベントを表します。 |
| InventoryInteractEvent | HumanEntityとインベントリの内容物との間の相互作用を記述するイベントの抽象基底クラス。 |
| InventoryMoveItemEvent | 一部のエンティティまたはブロックがアイテムを移動させるときに呼び出されます。 |
| InventoryOpenEvent | プレイヤーがインベントリを開いたときに呼び出されます。 |
| InventoryPickupItemEvent | ホッパーまたはホッパートロッコがドロップされたアイテムを拾ったときに呼び出されます。 |
| PrepareAnvilEvent | アイテムが金床の修理スロットに置かれたときに呼び出されます。 |
| PrepareGrindstoneEvent | アイテムが砥石の修理またはエンチャント解除スロットに置かれたときに呼び出されます。 |
| PrepareInventoryResultEvent | **非推奨。** PrepareResultEventを使用してください。 |
| PrepareItemCraftEvent | アイテムのクラフト準備が完了したときに呼び出されます。 |
| PrepareSmithingEvent | アイテムが鍛冶台のアップグレードスロットに置かれたときに呼び出されます。 |
| SmithItemEvent | アイテムのレシピが鍛冶台内で完成したときに呼び出されます。 |
| TradeSelectEvent | プレイヤーがトレードサイドバーで新しいトレードをクリックするたびに呼び出されます。 |

### プレイヤーに関するイベント

| クラス名 | 説明 |
|----|----|
| AsyncPlayerChatEvent | **非推奨。** 代わりにAsyncChatEventを使用してください。 |
| AsyncPlayerChatPreviewEvent | **非推奨。** チャットプレビューは削除されました。 |
| AsyncPlayerPreLoginEvent | ログインしようとしているプレイヤーの詳細を格納します。 |
| PlayerAdvancementDoneEvent | プレイヤーが進捗をすべて達成したときに呼び出されます。 |
| PlayerAnimationEvent | プレイヤーのアニメーションイベントを表します。 |
| PlayerArmorStandManipulateEvent | プレイヤーが防具立てを操作し、アイテムを交換、取得、または配置しようとしたときに呼び出されます。 |
| PlayerAttemptPickupItemEvent | プレイヤーが地面からアイテムを拾おうとしたときに投げられます。 |
| PlayerBedEnterEvent | プレイヤーがベッドに入ろうとしているときに呼び出されます。 |
| PlayerBedLeaveEvent | プレイヤーがベッドから離れるときに呼び出されます。 |
| PlayerBucketEmptyEvent | プレイヤーがバケツを空にしたときに呼び出されます。 |
| PlayerBucketEntityEvent | プレイヤーがバケツでエンティティを捕獲したときに呼び出されます。 |
| PlayerBucketEvent | プレイヤーがバケツと相互作用したときに呼び出されます。 |
| PlayerBucketFillEvent | プレイヤーがバケツを満たしたときに呼び出されます。 |
| PlayerBucketFishEvent | **非推奨。** 代わりにPlayerBucketEntityEventを使用してください。 |
| PlayerChangedMainHandEvent | プレイヤーがクライアント設定でメインハンドを変更したときに呼び出されます。 |
| PlayerChangedWorldEvent | プレイヤーが別の世界に移動したときに呼び出されます。 |
| PlayerChannelEvent | プレイヤーが新しいプラグインチャネルを登録または登録解除した後に呼び出されます。 |
| PlayerChatEvent | **非推奨。** このイベントをリッスンすると、チャットがメインスレッドを待つことになり、チャットメッセージが遅延します。 |
| PlayerChatTabCompleteEvent | **非推奨。** クライアントの変更により、このイベントは発生しなくなりました。 |
| PlayerCommandPreprocessEvent | プレイヤーがスラッシュで始まるメッセージを送信したときに呼び出されます。 |
| PlayerCommandSendEvent | 利用可能なサーバーコマンドのリストがプレイヤーに送信されるときに呼び出されます。 |
| PlayerDropItemEvent | プレイヤーがインベントリからアイテムをドロップしたときに投げられます。 |
| PlayerEditBookEvent | プレイヤーが本と羽ペンアイテムを編集またはサインしたときに呼び出されます。 |
| PlayerEggThrowEvent | プレイヤーが卵を投げ、孵化する可能性があるときに呼び出されます。 |
| PlayerEvent | プレイヤーに関連するイベントを表します。 |
| PlayerExpChangeEvent | プレイヤーの経験値が自然に変化したときに呼び出されます。 |
| PlayerExpCooldownChangeEvent | プレイヤーの経験値クールダウンが変化したときに呼び出されます。 |
| PlayerFishEvent | プレイヤーが釣りをしているときに投げられます。 |
| PlayerGameModeChangeEvent | プレイヤーのゲームモードが変更されたときに呼び出されます。 |
| PlayerHarvestBlockEvent | プレイヤーがブロックを収穫するときに呼び出されます。 |
| PlayerHideEntityEvent | プレイヤーから見えるエンティティが隠されたときに呼び出されます。 |
| PlayerInteractAtEntityEvent | プレイヤーがエンティティを右クリックしたときに呼び出され、エンティティがクリックされた場所も含まれます。 |
| PlayerInteractEntityEvent | プレイヤーがエンティティを右クリックしたときに呼び出されます。 |
| PlayerInteractEvent | プレイヤーがオブジェクトや空気と相互作用したときに呼び出され、各手ごとに一度発生する可能性があります。作物を植えようとする動作も検知可能 |
| PlayerItemBreakEvent | プレイヤーのアイテム（シャベルや火打ち石と鋼など）が壊れたときに発生します。 |
| PlayerItemConsumeEvent | プレイヤーがアイテム（食べ物、ポーション、ミルクバケツなど）を消費し終えたときに呼び出されます。 |
| PlayerItemDamageEvent | プレイヤーが使用したアイテムが耐久度ダメージを受けたときに呼び出されます。 |
| PlayerItemHeldEvent | プレイヤーが現在持っているアイテムを変更したときに発生します。 |
| PlayerItemMendEvent | プレイヤーが修繕エンチャントを使ってアイテムを修理したときに発生します。 |
| PlayerJoinEvent | プレイヤーがサーバーに参加したときに呼び出されます。 |
| PlayerKickEvent | プレイヤーがサーバーからキックされたときに呼び出されます。 |
| PlayerLevelChangeEvent | プレイヤーのレベルが変化したときに呼び出されます。 |
| PlayerLocaleChangeEvent | プレイヤーがクライアント設定でロケールを変更したときに呼び出されます。 |
| PlayerLoginEvent | ログインしようとしているプレイヤーの詳細を格納します。 |
| PlayerMoveEvent | プレイヤーの移動イベントの情報を保持します。 |
| PlayerPickupArrowEvent | プレイヤーが地面から矢を拾い上げたときに投げられます。 |
| PlayerPickupItemEvent | **非推奨。** EntityPickupItemEventを使用してください。 |
| PlayerPortalEvent | プレイヤーがポータルに接触してテレポートしようとする直前に呼び出されます。 |
| PlayerPreLoginEvent | **非推奨。** このイベントはログインスレッドの同期を引き起こします。セカンダリスレッドの非同期を保つためにAsyncPlayerPreLoginEventが推奨されます。 |
| PlayerQuitEvent | プレイヤーがサーバーを離れるときに呼び出されます。 |
| PlayerRecipeBookClickEvent | **非推奨、削除予定：** このAPI要素は将来のバージョンで削除される予定です。 PlayerRecipeBookClickEventを使用してください。 |
| PlayerRecipeBookSettingsChangeEvent | プレイヤーがレシピブックの設定を変更したときに呼び出されます。 |
| PlayerRecipeDiscoverEvent | プレイヤーがレシピブックで新しいレシピを発見したときに呼び出されます。 |
| PlayerRegisterChannelEvent | プレイヤーがプラグインチャネルを登録した直後に呼び出されます。 |
| PlayerResourcePackStatusEvent | プレイヤーがリソースパックリクエストに対してアクションを取ったときに呼び出されます。 |
| PlayerRespawnEvent | プレイヤーがリスポーンしたときに呼び出されます。 |
| PlayerRiptideEvent | プレイヤーがトライデントのリップタイドエンチャントを使用して空中に飛び出したときに発生します。 |
| PlayerShearEntityEvent | プレイヤーがエンティティの毛を刈るときに呼び出されます。 |
| PlayerShowEntityEvent | プレイヤーに対して隠されていたエンティティが表示されたときに呼び出されます。 |
| PlayerSignOpenEvent | **非推奨、削除予定：** このAPI要素は将来のバージョンで削除される予定です。 PlayerOpenSignEventを使用してください。 |
| PlayerSpawnChangeEvent | **非推奨、削除予定：** このAPI要素は将来のバージョンで削除される予定です。 PlayerSetSpawnEventを使用してください。 |
| PlayerStatisticIncrementEvent | プレイヤーの統計が増加したときに呼び出されます。 |
| PlayerSwapHandItemsEvent | プレイヤーがメインハンドとオフハンドのアイテムをホットキーで交換したときに呼び出されます。 |
| PlayerTakeLecternBookEvent | プレイヤーが書見台から本を取るボタンをクリックしたときに呼び出されます。 |
| PlayerTeleportEvent | プレイヤーのテレポートイベントの情報を保持します。 |
| PlayerToggleFlightEvent | プレイヤーが飛行状態を切り替えたときに呼び出されます。 |
| PlayerToggleSneakEvent | プレイヤーがしゃがみ状態を切り替えたときに呼び出されます。 |
| PlayerToggleSprintEvent | プレイヤーがスプリント状態を切り替えたときに呼び出されます。 |
| PlayerUnleashEntityEvent | プレイヤーのアクションによってエンティティのリードが外れる前に呼び出されます。 |
| PlayerUnregisterChannelEvent | プレイヤーがプラグインチャネルの登録を解除した直後に呼び出されます。 |
| PlayerVelocityEvent | プレイヤーの速度が変化したときに呼び出されます。 |

### レイドに関するイベント

| クラス名 | 説明 |
|----|----|
| RaidEvent | 襲撃に関連するイベントを表します。 |
| RaidFinishEvent | 襲撃が明確な結果で完了したときに呼び出されます。 |
| RaidSpawnWaveEvent | 襲撃の波がスポーンしたときに呼び出されます。 |
| RaidStopEvent | 襲撃が停止されたときに呼び出されます。 |
| RaidTriggerEvent | 襲撃がトリガーされたときに呼び出されます（例：不吉な予感の効果を持つプレイヤーが村に入る）。 |

### サーバー上のプログラム状態の変更に関するイベント

| クラス名 | 説明 |
|----|----|
| BroadcastMessageEvent | Server.broadcast(net.kyori.adventure.text.Component) (String, String)}などのサーバーブロードキャストメッセージのためにトリガーされるイベント。 |
| MapInitializeEvent | マップが初期化されたときに呼び出されます。 |
| PluginDisableEvent | プラグインが無効化されたときに呼び出されます。 |
| PluginEnableEvent | プラグインが有効化されたときに呼び出されます。 |
| PluginEvent | プラグインの有効化および無効化イベントに使用されます。 |
| RemoteServerCommandEvent | RCON経由でコマンドが受信されたときに呼び出されます。 |
| ServerCommandEvent | プレイヤー以外によってコマンドが実行されたときに呼び出されます。 |
| ServerEvent | その他のサーバーイベント。 |
| ServerListPingEvent | サーバーリストのピングが来たときに呼び出されます。 |
| ServerLoadEvent | サーバーの起動またはリロードが完了したときに呼び出されます。 |
| ServiceEvent | 登録されたサービスに関連するイベント。 |
| ServiceRegisterEvent | サービスが登録されたときに呼び出されます。 |
| ServiceUnregisterEvent | サービスが登録解除されたときに呼び出されます。 |
| TabCompleteEvent | 任意のCommandSender（プレイヤーやコンソールなど）がタブ補完を試みたときに呼び出されます。 |

### 乗り物エンティティに関するイベント

| クラス名 | 説明 |
|----|----|
| VehicleBlockCollisionEvent | 車両がブロックに衝突したときに発生します。 |
| VehicleCollisionEvent | 車両が衝突したときに発生します。 |
| VehicleCreateEvent | 車両が作成されたときに発生します。 |
| VehicleDamageEvent | 車両がダメージを受けたときに発生します。 |
| VehicleDestroyEvent | 車両が破壊されたときに発生します（プレイヤーまたは環境によって引き起こされる可能性があります）。 |
| VehicleEnterEvent | エンティティが車両に乗り込んだときに発生します。 |
| VehicleEntityCollisionEvent | 車両がエンティティと衝突したときに発生します。 |
| VehicleEvent | 車両に関連するイベントを表します。 |
| VehicleExitEvent | 生きているエンティティが車両から降りたときに発生します。 |
| VehicleMoveEvent | 車両が移動したときに発生します。 |
| VehicleUpdateEvent | 車両が更新されたときに呼び出されます。 |

### 天気に関するイベント

| クラス名 | 説明 |
|----|----|
| LightningStrikeEvent | 雷が落ちた際のデータを格納します。 |
| ThunderChangeEvent | 世界の雷の状態が変化した際のデータを格納します。 |
| WeatherChangeEvent | 世界の天気が変化した際のデータを格納します。 |
| WeatherEvent | 天気に関連するイベントを表します。 |


### ワールドに関するイベント

| クラス名 | 説明 |
|----|----|
| AsyncStructureGenerateEvent | このイベントは、トリガー方法によっては同期的に発生することがあります。 |
| AsyncStructureSpawnEvent | 構造物が世界に自然に生成されたときに呼び出されます。 |
| ChunkEvent | チャンクに関連するイベントを表します。 |
| ChunkLoadEvent | チャンクがロードされたときに呼び出されます。 |
| ChunkPopulateEvent | 新しく生成されたチャンクのポピュレートが完了したときに投げられます。 |
| ChunkUnloadEvent | チャンクがアンロードされたときに呼び出されます。 |
| EntitiesLoadEvent | エンティティがロードされたときに呼び出されます。 |
| EntitiesUnloadEvent | エンティティがアンロードされたときに呼び出されます。 |
| GenericGameEvent | 一般的なMojangのゲームイベントを表します。 |
| LootGenerateEvent | インベントリホルダー用のLootTableが世界で生成されたときに呼び出されます。 |
| PortalCreateEvent | ポータルが作成されたときに呼び出されます。 |
| SpawnChangeEvent | 世界のスポーンが変更されたときに呼び出されるイベント。 |
| StructureGrowEvent | 有機的な構造（苗木 -> 木、キノコ -> 大きなキノコ）が自然にまたは骨粉を使って成長しようとするときに呼び出されるイベント。 |
| TimeSkipEvent | 世界の時間がスキップされたときに呼び出されます。 |
| WorldEvent | 世界内のイベントを表します。 |
| WorldInitEvent | 世界が初期化されているときに呼び出されます。 |
| WorldLoadEvent | 世界がロードされたときに呼び出されます。 |
| WorldSaveEvent | 世界が保存されたときに呼び出されます。 |
| WorldUnloadEvent | 世界がアンロードされたときに呼び出されます。 |

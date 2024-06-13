---
title: Fabric 1.20.6 Blockクラスのオーバーライド可能なメソッド一覧
tags:
  - minecraft
private: true
updated_at: ''
id:
organization_url_name: null
slide: false
ignorePublish: false
---

# Blockクラスのオーバーライド可能なメソッド一覧

Fabric 1.20.6のBlockクラスでオーバーライド可能なメソッドのまとめです。


| メソッド名 | 説明 |
| --- | --- |
| onBlockAdded(BlockState state, World world, BlockPos pos, BlockState oldState, boolean notify) | ブロックがワールドに追加された際に呼ばれます。 |
| onPlaced(World world, BlockPos pos, BlockState state, LivingEntity placer, ItemStack itemStack) | ブロックが配置されたときに呼ばれます。 |
| getPlacementState(ItemPlacementContext context) | ブロックの配置状態を取得します。 |
| canPlaceAt(BlockState state, WorldView world, BlockPos pos) | ブロックが特定の位置に配置可能かどうかをチェックします。 |
| getStateForNeighborUpdate(BlockState state, Direction direction, BlockState neighborState, WorldAccess world, BlockPos pos, BlockPos neighborPos) | 隣接ブロックの状態が変化した際に呼ばれます。 |
| onBreak(World world, BlockPos pos, BlockState state, PlayerEntity player) | ブロックが壊された際に呼ばれます。 |
| onStateReplaced(BlockState state, World world, BlockPos pos, BlockState newState, boolean moved) | ブロックの状態が別の状態に置き換えられたときに呼ばれます。 |
| onBlockBreakStart(BlockState state, World world, BlockPos pos, PlayerEntity player) | プレイヤーがブロックの破壊を開始した際に呼ばれます。 |
| afterBreak(World world, PlayerEntity player, BlockPos pos, BlockState state, BlockEntity blockEntity, ItemStack stack) | ブロックが破壊された後に呼ばれます。 |
| onEntityCollision(BlockState state, World world, BlockPos pos, Entity entity) | エンティティがブロックに衝突したときに呼ばれます。 |
| onSteppedOn(World world, BlockPos pos, BlockState state, Entity entity) | エンティティがブロックの上を歩いたときに呼ばれます。 |
| onLandedUpon(World world, BlockPos pos, BlockState state, Entity entity, float fallDistance) | エンティティがブロックに着地したときに呼ばれます。 |
| onUse(BlockState state, World world, BlockPos pos, PlayerEntity player, Hand hand, BlockHitResult hit) | プレイヤーがブロックを使用したときに呼ばれます。 |
| onProjectileHit(World world, BlockState state, BlockHitResult hit, ProjectileEntity projectile) | ブロックにプロジェクタイルが当たったときに呼ばれます。 |
| randomTick(BlockState state, ServerWorld world, BlockPos pos, Random random) | ブロックがランダムにティックされたときに呼ばれます。 |
| scheduledTick(BlockState state, ServerWorld world, BlockPos pos, Random random) | スケジュールされたティックが実行されるときに呼ばれます。 |
| neighborUpdate(BlockState state, World world, BlockPos pos, Block sourceBlock, BlockPos sourcePos, boolean notify) | 隣接するブロックが更新されたときに呼ばれます。 |
| prepare(BlockState state, WorldAccess world, BlockPos pos, int flags, int maxUpdateDepth) | ブロック状態が変更されたときに呼ばれます。 |
| getCollisionShape(BlockState state, BlockView world, BlockPos pos, ShapeContext context) | ブロックの衝突形状を取得します。 |
| getOutlineShape(BlockState state, BlockView world, BlockPos pos, ShapeContext context) | ブロックのアウトライン形状を取得します。 |

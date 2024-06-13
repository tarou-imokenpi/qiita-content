---
title: mc-mod
tags:
  - minecraft
private: true
updated_at: '2024-06-11T22:47:21+09:00'
id: 24fccb367cc15cafc6eb
organization_url_name: null
slide: false
ignorePublish: false
---
# アイテムの登録

```java
package com.technocraft_engineering;

import net.fabricmc.api.ModInitializer;
import net.minecraft.item.Item;
import net.minecraft.registry.Registries;
import net.minecraft.registry.Registry;
import net.minecraft.util.Identifier;

public class TechnoCraftEngineering implements ModInitializer {
    public static final Item CUSTOM_ITEM = new Item(new Item.Settings());

    @Override
    public void onInitialize() {
        // アイテムの登録
        Registry.register(Registries.ITEM,new Identifier("technocraft_engineering","custom_item"),CUSTOM_ITEM);

    }
}
```
こう書ける

```java
package com.technocraft_engineering;

import net.fabricmc.api.ModInitializer;
import net.minecraft.item.Item;
import net.minecraft.registry.Registries;
import net.minecraft.registry.Registry;
import net.minecraft.util.Identifier;

public class TechnoCraftEngineering implements ModInitializer {
    public static final Item CUSTOM_ITEM = Registry.register(
            Registries.ITEM,
            new Identifier("technocraft_engineering", "custom_item"),
            new Item(new Item.Settings())
    );

    @Override
    public void onInitialize() {
    }
}

```
バージョンによっては以下のように書く

```java
public class ExampleMod implements ModInitializer {

    // an instance of our new item
    // for versions below 1.20.4
    public static final Item CUSTOM_ITEM = new Item(new FabricItemSettings());
    // for versions since 1.20.5
    public static final Item CUSTOM_ITEM = new Item(new Item.Settings());

}

```

## アイテムに機能を追加する

```java
// CustomItem.java

package com.technocraft_engineering;

import net.minecraft.entity.player.PlayerEntity;
import net.minecraft.item.Item;
import net.minecraft.item.ItemStack;
import net.minecraft.sound.SoundEvents;
import net.minecraft.util.Hand;
import net.minecraft.util.TypedActionResult;
import net.minecraft.world.World;

public class CustomItem extends Item {
    public CustomItem(Settings settings) {
        super(settings);
    }


    @Override
    public TypedActionResult<ItemStack> use(World world, PlayerEntity playerEntity, Hand hand) {
        // プレイヤーがアイテムを使ったときの処理
        // ここでは羊毛を壊す音を再生する
        playerEntity.playSound(SoundEvents.BLOCK_WOOL_BREAK, 1.0F, 1.0F);
        return TypedActionResult.success(playerEntity.getStackInHand(hand));
    }
}

```

```java
// TechnoCraftEngineering.java

package com.technocraft_engineering;

import net.fabricmc.api.ModInitializer;
import net.minecraft.item.Item;
import net.minecraft.registry.Registries;
import net.minecraft.registry.Registry;
import net.minecraft.util.Identifier;

public class TechnoCraftEngineering implements ModInitializer {
    public static final Item CUSTOM_ITEM = Registry.register(
            Registries.ITEM,
            new Identifier("technocraft_engineering", "custom_item"),
            // new Item(new Item.Settings())
            // ここでCustomItemを使う
            new CustomItem(new Item.Settings())
    );
    
    @Override
    public void onInitialize() {
    }
}

```

### アイテムのスタックサイズを変更する

```java

package com.technocraft_engineering;

import net.fabricmc.api.ModInitializer;
import net.minecraft.item.Item;
import net.minecraft.registry.Registries;
import net.minecraft.registry.Registry;
import net.minecraft.util.Identifier;

public class TechnoCraftEngineering implements ModInitializer {
    public static final Item CUSTOM_ITEM = Registry.register(
            Registries.ITEM,
            new Identifier("technocraft_engineering", "custom_item"),
            new CustomItem(new Item.Settings().maxCount(16)) // ここでスタックサイズを変更する
    );

    @Override
    public void onInitialize() {
    }
}
```

### 燃料や堆肥になるものを作る

* `FuelRegistry` 燃焼として登録する
* `CompostingChanceRegistry ` 堆肥として登録しコンポスターで使えるようにする

```java
package com.technocraft_engineering;

import net.fabricmc.api.ModInitializer;
import net.fabricmc.fabric.api.registry.FuelRegistry;
import net.minecraft.item.Item;
import net.minecraft.registry.Registries;
import net.minecraft.registry.Registry;
import net.minecraft.util.Identifier;

public class TechnoCraftEngineering implements ModInitializer {
    public static final Item CUSTOM_ITEM = Registry.register(
            Registries.ITEM,
            new Identifier("technocraft_engineering", "custom_item"),
//            new Item(new Item.Settings())
            new CustomItem(new Item.Settings().maxCount(16))
    );

    @Override
    public void onInitialize() {
        // 燃料として登録
        FuelRegistry.INSTANCE.add(CUSTOM_ITEM, 300);
    }
}
```


### アイテムタブグループを追加する

```java
// TechnoCraftEngineering.java

package com.technocraft_engineering;

import net.fabricmc.api.ModInitializer;

import net.fabricmc.fabric.api.itemgroup.v1.FabricItemGroup;
import net.fabricmc.fabric.api.registry.FuelRegistry;
import net.minecraft.item.Item;
import net.minecraft.item.ItemGroup;
import net.minecraft.item.ItemStack;
import net.minecraft.registry.Registries;
import net.minecraft.registry.Registry;
import net.minecraft.text.Text;
import net.minecraft.util.Identifier;

public class TechnoCraftEngineering implements ModInitializer {
    public static final Item CUSTOM_ITEM = Registry.register(
            Registries.ITEM,
            new Identifier("technocraft_engineering", "custom_item"),
            new CustomItem(new Item.Settings().maxCount(16))
    );

    private static final ItemGroup ITEM_GROUP = FabricItemGroup.builder()
            .icon(() -> new ItemStack(CUSTOM_ITEM))
            .displayName(Text.translatable("itemGroup.technocraft_engineering.custom_group"))
            .entries((context, entries) -> {
                entries.add(CUSTOM_ITEM);
            })
            .build();

    @Override
    public void onInitialize() {
        FuelRegistry.INSTANCE.add(CUSTOM_ITEM, 300);
        Registry.register(
                Registries.ITEM_GROUP,
                new Identifier("technocraft_engineering", "test_group"),
                ITEM_GROUP
        );
    }
}
```

```java
// CustomItem.java

package com.technocraft_engineering;

import net.minecraft.entity.player.PlayerEntity;
import net.minecraft.item.Item;
import net.minecraft.item.ItemStack;
import net.minecraft.sound.SoundEvents;
import net.minecraft.util.Hand;
import net.minecraft.util.TypedActionResult;
import net.minecraft.world.World;

public class CustomItem extends Item {
    public CustomItem(Settings settings) {
        super(settings);
    }

    @Override
    public TypedActionResult<ItemStack> use(World world, PlayerEntity playerEntity, Hand hand) {
        playerEntity.playSound(SoundEvents.BLOCK_WOOL_BREAK, 1.0F, 1.0F);
        return TypedActionResult.success(playerEntity.getStackInHand(hand));
    }
}

```

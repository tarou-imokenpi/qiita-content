---
title: minecraft プラグイン チュートリアル
tags:
  - ''
private: true
updated_at: ''
id: null
organization_url_name: null
slide: false
ignorePublish: true
---
# プラグイン チュートリアル


## プラグインの作成
これがプラグインの基本的な構造です

`MyPlugin.java`というクラスを作成し、JavaPluginを継承することでプラグインを作成することができます。(このファイルのクラス名は自由です)

```java
import org.bukkit.plugin.java.JavaPlugin;

public class MyPlugin extends JavaPlugin {

    @Override
    public void onEnable() {
        // プラグインが有効化されたときに実行されるコード
        getLogger().info("MyPluginが有効になりました！");
    }

    @Override
    public void onDisable() {
        // プラグインが無効化されたときに実行されるコード
        getLogger().info("MyPluginが無効になりました！");
    }
}

```
## イベントの登録
イベントとは、プレイヤーがログインしたときやブロックが破壊されたときなど、サーバー内で発生するアクションのことです

特に重要なのはメソッドに`@EventHandler`アノテーションを付けること

`@EventHandler`アノテーションを付けることで、そのメソッドがイベントを処理するメソッドとして認識されます。

```java
import org.bukkit.event.Listener;
import org.bukkit.event.EventHandler;
import org.bukkit.event.player.PlayerJoinEvent;

public class MyListener implements Listener {

    @EventHandler
    public void onPlayerJoin(PlayerJoinEvent event) {
        event.getPlayer().sendMessage("サーバーへようこそ！");
    }
}

```
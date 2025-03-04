# **如何创建并定义一个自定义领袖（Leader）**

创建一个新的 **自定义领袖**（Leader），并正确定义其特性、技能、背景图像和外交信息等内容。我们将基于 XML 代码编写，并按照游戏的结构一步步完成。 

---

### 1. **创建文件夹**：

在项目目录下，新建 `Leader.xml`，用于定义我们的领袖，我们创建一个名为 **"E R Q"** 的自定义领袖。  

### **2. 定义领袖及其特性**

```xml
<Types> 
    <Row Type="LEADER_ERQ" Kind="KIND_LEADER"/> 
    <Row Type="TRAIT_LEADER_ERQ_WORLD_HARMONY" Kind="KIND_TRAIT"/> 
</Types> 
```

- `LEADER_ERQ`：定义了新的领袖类型。
- `TRAIT_LEADER_ERQ_WORLD_HARMONY`：定义了该领袖的 **专属特性**。

---

### **3. 绑定领袖到游戏**

```xml
<Leaders> 
    <Row LeaderType="LEADER_ERQ" 
    Name="LOC_LEADER_ERQ_NAME" 
    InheritFrom="LEADER_DEFAULT" 
    Sex="Male"/> 
</Leaders>
```

- `InheritFrom="LEADER_DEFAULT`：继承默认领袖属性。
- `Sex="Male"`：性别设置为男性。

---

### **4. 设定领袖的外交对话**

```xml
<LeaderQuotes> 
    <Row LeaderType="LEADER_ERQ" Quote="LOC_DIPLO_FIRST_MEET_LEADER_ERQ_ANY"/> 
</LeaderQuotes>
```

- `LOC_DIPLO_FIRST_MEET_LEADER_ERQ_ANY`：用于 **首次会面** 时的外交台词（需在 `Text.xml` 里补充）。

---

### **5. 设定领袖特性详情**

```xml
<Traits> 
    <Row TraitType="TRAIT_LEADER_ERQ_WORLD_HARMONY" 
    Name="LOC_TRAIT_LEADER_ABILITY_NAME" 
    Description="LOC_TRAIT_LEADER_ABILITY_DESCRIPTION"/> 
</Traits>
```

- `LOC_TRAIT_LEADER_ABILITY_NAME`：该领袖的特性名称。
- `LOC_TRAIT_LEADER_ABILITY_DESCRIPTION`：该领袖的特性描述。

---

### **6. 绑定领袖特性**

```xml
<LeaderTraits> 
    <Row LeaderType="LEADER_ERQ" TraitType="TRAIT_LEADER_ERQ_WORLD_HARMONY"/> 
</LeaderTraits>
```

- 绑定 `TRAIT_LEADER_ERQ_WORLD_HARMONY` 使其在`Leader`ERQ上生效。

---

### **7. 设定加载界面信息**

```xml
<LoadingInfo> 
    <Row LeaderType="LEADER_ERQ" 
    ForegroundImage="ICON_LEADER_ERQ" 
    BackgroundImage="ICON_BACKGROUND_LOADING.dds" 
    PlayDawnOfManAudio="1" 
    EraText="" 
    LeaderText="LOC_LOADING_INFO_LEADER_ERQ"/> 
</LoadingInfo>
```

- `PlayDawnOfManAudio`：是否播放游戏内的语音（从水下的....）
- `ForegroundImage="ICON_LEADER_ERQ"`：领袖头像图片。
- `BackgroundImage="ICON_BACKGROUND_LOADING.dds"`：加载界面背景图片。
- `LeaderText`：领袖的文本

---

### **8. 设定外交界面背景**

```xml
<DiplomacyInfo> 
    <Row Type="LEADER_ERQ" BackgroundImage="DIPLOMACY_BACKGROUND"/> 
</DiplomacyInfo>
```

- `BackgroundImage="DIPLOMACY_BACKGROUND"`：外交界面的背景图。

---

### **9. 设定领袖特性修饰符**

```xml
<TraitModifiers> 
    <Row TraitType="TRAIT_LEADER_ERQ_WORLD_HARMONY" ModifierId="TRAIT_CITY_WONDER_PRODUCTION_ERQ"/> 
    <Row TraitType="TRAIT_LEADER_ERQ_WORLD_HARMONY" ModifierId="TRAIT_BUILDER_WONDER_PERCENT_ERQ"/> 
</TraitModifiers>
```

- `TRAIT_CITY_WONDER_PRODUCTION_ERQ`：提高 **奇观生产力** 的修饰符。
- `TRAIT_BUILDER_WONDER_PERCENT_ERQ`：允许 **建造者加速奇观建造** 的修饰符。

---

### 10. 具体修饰符定义

```xml
<Modifiers> 
    <!-- 提高 10% 奇观生产力 --> 
    <Row ModifierId="TRAIT_CITY_WONDER_PRODUCTION_ERQ" ModifierType="MODIFIER_PLAYER_CITIES_ADJUST_WONDER_PRODUCTION"/> 
    <!-- 让建造者可以加速奇观建造 15% --> 
    <Row ModifierId="TRAIT_BUILDER_WONDER_PERCENT_ERQ" ModifierType="MODIFIER_PLAYER_ADJUST_UNIT_WONDER_PERCENT"/> 
</Modifiers>
```

- `MODIFIER_PLAYER_CITIES_ADJUST_WONDER_PRODUCTION`：调整城市奇观生产力的修饰符。
- `MODIFIER_PLAYER_ADJUST_UNIT_WONDER_PERCENT`：调整单位对奇观建造的贡献。

---

### **11. 设定修饰符参数**

```xml
<ModifierArguments> 
    <!-- 提高 10% 奇观生产力 --> 
    <Row ModifierId="TRAIT_CITY_WONDER_PRODUCTION_ERQ" Name="Amount" Value="80"/> 
    <!-- 让建造者可以加速奇观建造 15% --> 
    <Row ModifierId="TRAIT_BUILDER_WONDER_PERCENT_ERQ" Name="UnitType" Value="UNIT_BUILDER"/> 
    <Row ModifierId="TRAIT_BUILDER_WONDER_PERCENT_ERQ" Name="Amount" Value="15"/> 
</ModifierArguments>`
```

- `Value="80"`：这个数值没有确定，但是缺失加速了奇观的基础建造速度
- `UNIT_BUILDER`：指定 **建造者** 单位能加速奇观建造。
- `Amount="15"`：加速奇观建造 **15%**。

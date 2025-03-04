# 《文明VI》亚洲文明MOD编写指南

## 1. 简介

如何定义一个新的文明——亚洲文明（CIVILIZATION_ASIA），并为其添加特性、领袖、城市名称、公民名称、起始地形偏好等。

## 2. XML文件结构

在《文明VI》的MOD开发中，XML文件用于定义游戏内的各种数据结构，如文明、领袖、特性、修正器等。

`Asia.xml`的结构如下：

- **Types**：定义文明及其相关特性。
- **Civilizations**：定义文明的基本信息。
- **CivilizationLeaders**：绑定文明与领袖。
- **Traits**：定义文明的特性。
- **CivilizationTraits**：将特性绑定到文明。
- **TraitModifiers**：为文明的特性添加修正器。
- **Modifiers**：具体定义修正器的类型。
- **ModifierArguments**：设定修正器的参数。
- **CityNames**：定义文明的城市名称。
- **CivilizationCitizenNames**：定义公民名称。
- **StartBiasFeatures**：定义起始地形偏好。
- **StartBiasResources**：定义起始资源偏好。

## 2. 定义文明与特性

```xml
<Types>
    <Row Type="CIVILIZATION_ASIA" Kind="KIND_CIVILIZATION"/>
    <Row Type="TRAIT_CIVILIZATION_ASIA_HARMONY" Kind="KIND_TRAIT"/>
</Types>
```

## 3. 文明详情（Civilizations）

```xml
<Civilizations>
    <Row CivilizationType="CIVILIZATION_ASIA"
         Name="LOC_CIVILIZATION_ASIA_NAME"
         Description="LOC_CIVILIZATION_ASIA_DESCRIPTION"
         Adjective="LOC_CIVILIZATION_ASIA_ADJECTIVE"
         StartingCivilizationLevelType="CIVILIZATION_LEVEL_FULL_CIV"
         RandomCityNameDepth="20"
         Ethnicity="ETHNICITY_ASIAN"/>
</Civilizations>
```

- `CivilizationType`：文明的唯一标识符。
- `Name`、`Description`、`Adjective`：文明的本地化文本。
- `StartingCivilizationLevelType`：决定文明的复杂度。
- `RandomCityNameDepth`：随机城市名称的数量。
- `Ethnicity`：定义文明的民族特征。

## 4. 绑定领袖（CivilizationLeaders）

```xml
<CivilizationLeaders>
    <Row CivilizationType="CIVILIZATION_ASIA" LeaderType="LEADER_ERQ" CapitalName="LOC_CITY_NAME_BEIJING"/>
</CivilizationLeaders>
```

- `LeaderType`：绑定的领袖。
- `CapitalName`：默认首都城市名称。

## 5. 定义文明特性（Traits）

```xml
<Traits>
    <Row TraitType="TRAIT_CIVILIZATION_ASIA_HARMONY"
         Name="LOC_TRAIT_CIVILIZATION_ABILITY_NAME"
         Description="LOC_TRAIT_CIVILIZATION_ABILITY_DESCRIPTION"/>
</Traits>
```

- `TraitType`：特性的唯一标识。
- `Name`、`Description`：本地化文本。

## 6. 绑定特性到文明（CivilizationTraits）

```xml
<CivilizationTraits>
    <Row CivilizationType="CIVILIZATION_ASIA" TraitType="TRAIT_CIVILIZATION_ASIA_HARMONY"/>
</CivilizationTraits>
```

**民族共和（TRAIT_CIVILIZATION_ASIA_HARMONY）**：

- 贸易路线提供额外的粮食（+5）、金币（+5）和信仰（+5）。

- `TraitType`：绑定的特性。

## 7. 定义修正器（Modifiers）

```xml
<Modifiers>
        <Row ModifierId="MODIFIER_CIVILIZATION_TRADE_FOOD" ModifierType="MODIFIER_PLAYER_ADJUST_TRADE_ROUTE_YIELD"/>
        <Row ModifierId="MODIFIER_CIVILIZATION_TRADE_GOLD" ModifierType="MODIFIER_PLAYER_ADJUST_TRADE_ROUTE_YIELD"/>
        <Row ModifierId="MODIFIER_CIVILIZATION_TRADE_FAITH" ModifierType="MODIFIER_PLAYER_ADJUST_TRADE_ROUTE_YIELD"/>
</Modifiers>
```

- `ModifierId`：修正器的唯一标识。
- `ModifierType`：修正器的类型。

此处为名族共和的举例说明

- 贸易路线提供额外的粮食（+5）、金币（+5）和信仰（+5）。

## 8. 设定修正器参数（ModifierArguments）

```xml
<ModifierArguments>
        <Row ModifierId="MODIFIER_CIVILIZATION_TRADE_GOLD" Name="YieldType" Value="YIELD_GOLD"/>
        <Row ModifierId="MODIFIER_CIVILIZATION_TRADE_GOLD" Name="Amount" Value="5"/>
</ModifierArguments>
```

示例为商路提供金币加成

- `YieldType`：收益类型，如金币、粮食。
- `Amount`：收益数值。

## 9. 设定起始地形偏好（StartBiasFeatures）

```xml
<StartBiasFeatures>
    <Row CivilizationType="CIVILIZATION_ASIA" FeatureType="FEATURE_FOREST" Tier="1"/>
    <Row CivilizationType="CIVILIZATION_ASIA" FeatureType="FEATURE_JUNGLE" Tier="1"/>
</StartBiasFeatures>
```

- 亚洲文明偏好森林（FEATURE_FOREST）和丛林（FEATURE_JUNGLE），这使其在森林和丛林地区更容易生成起始城市。

## 10. 设定起始资源偏好（StartBiasResources）

```xml
<StartBiasResources>
    <Row CivilizationType="CIVILIZATION_ASIA" ResourceType="RESOURCE_TOBACCO" Tier="1"/>
    <Row CivilizationType="CIVILIZATION_ASIA" ResourceType="RESOURCE_SPICES" Tier="1"/>
    <Row CivilizationType="CIVILIZATION_ASIA" ResourceType="RESOURCE_INCENSE" Tier="1"/>
</StartBiasResources>
```

- 亚洲文明偏好香料（RESOURCE_SPICES）、烟草（RESOURCE_TOBACCO）和熏香（RESOURCE_INCENSE）。这些资源能提高其综合发育和文化发展。

## 11. 定义城市名称（CityNames）

```xml
<CityNames>
    <Row CivilizationType="CIVILIZATION_ASIA" CityName="LOC_CITY_NAME_BEIJING"/>
    <Row CivilizationType="CIVILIZATION_ASIA" CityName="LOC_CITY_NAME_SHANGHAI"/>
</CityNames>
```

## 12. 定义国民名称 （CivilizationCitizenNames）

```xml
<CivilizationCitizenNames>
    <Row CivilizationType="CIVILIZATION_ASIA" CitizenName="LOC_CITIZEN_ASIA_1"/>
    <Row CivilizationType="CIVILIZATION_ASIA" CitizenName="LOC_CITIZEN_ASIA_2"/>
    <Row CivilizationType="CIVILIZATION_ASIA" CitizenName="LOC_CITIZEN_ASIA_3" Female="1"/>
    <Row CivilizationType="CIVILIZATION_ASIA" CitizenName="LOC_CITIZEN_ASIA_4"/>
</CivilizationCitizenNames>
```

若国民性别为女则需额外定义`Female="1"`。

# 如何创建并定义一个自定义区域（District）

创建一个新的特色区域（District），并正确定义其特性、修饰符、产出、前置科技等。我们将基于 XML 代码编写，并按照游戏的结构一步步完成。 

在项目目录下，新建 `Districts.xml`，它将用于定义我们的区域编写 Districts.xml下面，我们创建一个名为 "亚洲贸易中心"（Asian Trade Center ）的特色区域。

---

### **1. 定义新区域**

```xml
<GameData> 
    <Types> 
        <Row Type="DISTRICT_ASIAN_TRADE_CENTER" Kind="KIND_DISTRICT"/> 
        <Row Type="TRAIT_DISTRICT_ASIAN_TRADE_CENTER" Kind="KIND_TRAIT"/> 
    </Types> 
</GameData>
```

- `DISTRICT_ASIAN_TRADE_CENTER`：定义了新的区域类型。
- `TRAIT_DISTRICT_ASIAN_TRADE_CENTER`：定义为文明的特性。

---

### **2. 绑定到特定文明**

```xml
<CivilizationTraits> 
    <Row CivilizationType="CIVILIZATION_ASIA" TraitType="TRAIT_DISTRICT_ASIAN_TRADE_CENTER"/> 
</CivilizationTraits>
```

这意味着该区域只会对 `CIVILIZATION_ASIA`文明 可用。

---

### **3. 区域特性的声明**

```xml
<Traits> 
    <Row TraitType="TRAIT_DISTRICT_ASIAN_TRADE_CENTER" Name="LOC_DISTRICT_ASIAN_TRADE_CENTER_NAME" Description="LOC_DISTRICT_ASIAN_TRADE_CENTER_DESCRIPTION"/> 
</Traits>
```

这里，我们定义了：

- `Name`：特性的本地化名称（需要在 你自己定义 的`Text.xml` 里补充）。
- `Description`：区域的详细说明（需要在 你自己定义 的`Text.xml` 里补充）。

---

### **4. 定义区域属性**

```xml
<Districts> 
    <Row DistrictType="DISTRICT_ASIAN_TRADE_CENTER" 
    Name="LOC_DISTRICT_ASIAN_TRADE_CENTER_NAME" 
    Description="LOC_DISTRICT_ASIAN_TRADE_CENTER_DESCRIPTION" 
    TraitType="TRAIT_DISTRICT_ASIAN_TRADE_CENTER" 
    PrereqTech="TECH_CURRENCY" 
    PlunderType="PLUNDER_GOLD" 
    PlunderAmount="50" 
    AdvisorType="ADVISOR_GENERIC" 
    Cost="30" 
    CostProgressionModel="COST_PROGRESSION_NUM_UNDER_AVG_PLUS_TECH" 
    CostProgressionParam1="40" 
    Maintenance="1" 
    RequiresPlacement="true" 
    RequiresPopulation="true" 
    CityStrengthModifier="2"/> 
</Districts>
```

| 参数                                                                | 作用              |
| ----------------------------------------------------------------- | --------------- |
| `DistrictType="DISTRICT_ASIAN_TRADE_CENTER"`                      | 区域的唯一 ID        |
| `Name="LOC_DISTRICT_ASIAN_TRADE_CENTER_NAME"`                     | 本地化名称           |
| `Description="LOC_DISTRICT_ASIAN_TRADE_CENTER_DESCRIPTION"`       | 本地化描述           |
| `TraitType="TRAIT_DISTRICT_ASIAN_TRADE_CENTER"`                   | 绑定区域的特性         |
| `PrereqTech="TECH_CURRENCY"`                                      | 需要研究“货币”科技后才能解锁 |
| `PlunderType="PLUNDER_GOLD"`                                      | 掠夺时奖励金币         |
| `PlunderAmount="50"`                                              | 掠夺时获得 50 金币     |
| `AdvisorType="ADVISOR_GENERIC"`                                   | 顾问类型            |
| `Cost="30"`                                                       | 初始建造成本          |
| `CostProgressionModel="COST_PROGRESSION_NUM_UNDER_AVG_PLUS_TECH"` | 成本随游戏进程增长       |
| `CostProgressionParam1="40"`                                      | 成本增长参数          |
| `Maintenance="1"`                                                 | 维护费用为 1 金币/回合   |
| `RequiresPlacement="true"`                                        | 需要在地图上放置        |
| `RequiresPopulation="true"`                                       | 需要足够人口才能建造      |
| `CityStrengthModifier="2"`                                        | 使城市战斗力提高 2 点    |

### **5. 给予该区域“大人物点数”**

```xml
<District_GreatPersonPoints> 
    <Row DistrictType="DISTRICT_ASIAN_TRADE_CENTER" 
    GreatPersonClassType="GREAT_PERSON_CLASS_MERCHANT" 
    PointsPerTurn="1"/> 
</District_GreatPersonPoints>
```

- 该区域`DISTRICT_ASIAN_TRADE_CENTER`每回合提供1点大商人`GREAT_PERSON_CLASS_MERCHANT`点数。

---

### **6. 设定相邻加成**

```xml
<District_Adjacencies> 
    <Row DistrictType="DISTRICT_COMMERCIAL_HUB" 
    YieldChangeId="ASIAN_TRADE_CENTER_GOLD"/> 
</District_Adjacencies>
<Adjacency_YieldChanges> 
    <Row ID="ASIAN_TRADE_CENTER_GOLD" 
    Description="LOC_DISTRICT_ASIAN_TRADE_CENTER_GOLD" 
    YieldType="YIELD_GOLD" 
    YieldChange="3" 
    TilesRequired="1" 
    AdjacentDistrict="DISTRICT_ASIAN_TRADE_CENTER"/> 
</Adjacency_YieldChanges>`
```

- `AdjacentDistrict="DISTRICT_ASIAN_TRADE_CENTER"`：对应的区域变量
- `YieldType="YIELD_GOLD"`：相邻的 **商业中心** 区域会获得额外 **3**`(YieldChange)`金币

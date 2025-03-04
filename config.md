# 如何配置自定义文明及领袖

配置自定义文明与领袖，使其能够正确加载 **文明图标、能力、特色区域** 等内容，并在迭起兴衰（Rise and Fall）DLC 中使用。

---

## **1. 创建文件**

新建 `config.xml`，用于定义 **文明、领袖及其特色区域**。

---

## **2. 编写 `Config.xml`**

### **2.1 配置自定义文明**

```xml
<GameData>
    <!-- 配置迭起兴衰 -->
    <Players>
        <Row CivilizationAbilityDescription="LOC_TRAIT_CIVILIZATION_ABILITY_DESCRIPTION"
             CivilizationAbilityIcon="ICON_CIVILIZATION_ASIA"
             CivilizationAbilityName="LOC_TRAIT_CIVILIZATION_ABILITY_NAME"
             CivilizationIcon="ICON_CIVILIZATION_ASIA"
             CivilizationName="LOC_CIVILIZATION_ASIA_NAME"
             CivilizationType="CIVILIZATION_ASIA"
             LeaderAbilityDescription="LOC_TRAIT_LEADER_ABILITY_DESCRIPTION"
             LeaderAbilityIcon="ICON_LEADER_ERQ"
             LeaderAbilityName="LOC_TRAIT_LEADER_ABILITY_NAME"
             LeaderIcon="ICON_LEADER_ERQ"
             LeaderName="LOC_LEADER_ERQ_NAME"
             LeaderType="LEADER_ERQ"
             PortraitBackground="ICON_PORTRAIT_BACKGROUND"
             Domain="Players:Expansion2_Players"/>
    </Players>
</GameData>
```

- `CivilizationType="CIVILIZATION_ASIA"`：定义亚洲文明。
- `LeaderType="LEADER_ERQ"`：绑定 **E R Q** 作为亚洲文明的领袖。
- `CivilizationAbilityName="LOC_TRAIT_CIVILIZATION_ABILITY_NAME"`：文明的 **特色能力名称**。
- `LeaderAbilityName="LOC_TRAIT_LEADER_ABILITY_NAME"`：领袖的 **特色能力名称**。
- `CivilizationIcon="ICON_CIVILIZATION_ASIA"`：文明的 **图标**。
- `LeaderIcon="ICON_LEADER_ERQ"`：领袖的 **头像**。
- `PortraitBackground`：侧边框中的背景图
- `Domain`：游戏版本
  
  | Domain                     | 适用范围         |
  | -------------------------- | ------------ |
  | Players:StandardPlayers    | 适用于基础版（无DLC） |
  | Players:Expansion2_Players | 适用于《迭起兴衰》DLC |
  | Players:Expansion3_Players | 适用于《风云变幻》DLC |

---

## **3. 绑定特色区域**

```xml
<PlayerItems> 
<!-- 亚洲文明特色区域 --> 
    <Row Domain="Players:Expansion2_Players" 
        CivilizationType="CIVILIZATION_ASIA" 
        LeaderType="LEADER_ERQ" 
        Type="DISTRICT_ASIAN_ACADEMIC_CENTER" 
        Name="LOC_DISTRICT_ASIAN_ACADEMIC_CENTER_NAME" 
        Description="LOC_DISTRICT_ASIAN_ACADEMIC_CENTER_DESCRIPTION" 
        Icon="ICON_DISTRICT_ASIAN_ACADEMIC_CENTER" SortIndex="20"/>
     <Row Domain="Players:Expansion2_Players" 
        CivilizationType="CIVILIZATION_ASIA" 
        LeaderType="LEADER_ERQ" 
        Type="DISTRICT_ASIAN_CULTURAL_CENTER" 
        Name="LOC_DISTRICT_ASIAN_CULTURAL_CENTER_NAME" 
        Description="LOC_DISTRICT_ASIAN_CULTURAL_CENTER_DESCRIPTION" 
        Icon="ICON_DISTRICT_ASIAN_CULTURAL_CENTER" SortIndex="30"/> 
    <Row Domain="Players:Expansion2_Players" 
        CivilizationType="CIVILIZATION_ASIA" 
        LeaderType="LEADER_ERQ" 
        Type="DISTRICT_ASIA_FINANCIAL_CENTER" 
        Name="LOC_DISTRICT_ASIA_FINANCIAL_CENTER_NAME" 
        Description="LOC_DISTRICT_ASIA_FINANCIAL_CENTER_DESCRIPTION" 
        Icon="ICON_DISTRICT_ASIA_FINANCIAL_CENTER" SortIndex="40"/> 
</PlayerItems>
```

- 绑定 **亚洲文明** 的 **特色区域**。
- `Type="DISTRICT_ASIAN_ACADEMIC_CENTER"`：国立学术中心。
- `Type="DISTRICT_ASIAN_CULTURAL_CENTER"`：文化中心。
- `Type="DISTRICT_ASIA_FINANCIAL_CENTER"`：金融中心。
- `SortIndex="20/30/40"`：控制显示顺序。

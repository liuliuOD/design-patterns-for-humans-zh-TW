![Design Patterns For Humans](https://cloud.githubusercontent.com/assets/11269635/23065273/1b7e5938-f515-11e6-8dd3-d0d58de6bb9a.png)

---

🎉 設計模式簡化版入門指南 🎉（該專案為 [`design-patterns-for-humans`](https://github.com/kamranahmedse/design-patterns-for-humans) 的繁中版，並加上個人見解以期提升吸收效率）

---

# 常用翻譯對照表
|中文|英文|
|:-|:-|
|物件|object|
|實例|instance|
|類別|class|
|方法|method|
|建構子|constructor|
|函式、函數|function|
|模擬|mock|
|耦合|couple|
|解耦合|decouple|
|封裝|encapsulate|
|客戶端|client|
|物件導向程式|object-oriented programming (OOP)|
|反模式|anti-pattern|

# 查找表
|[創建型設計模式 (Creational Design Patterns)](#創建型設計模式-creational-design-patterns)|[結構型設計模式 (Structural Design Patterns)](#結構型設計模式-structural-design-patterns)|[行為型設計模式 (Behavioral Design Patterns)](#行為型設計模式-behavioral-design-patterns)|
|:-|:-|:-|
|[簡單工廠模式 (Simple Factory)](#-簡單工廠模式-simple-factory)|[轉接器（適配器）模式 (Adapter)](#-轉接器（適配器）模式-adapter)|[責任鏈模式 (Chain of Responsibility)](#-責任鏈模式-chain-of-responsibility)|
|[工廠方法模式 (Factory Method)](#-工廠方法模式-factory-method)|[橋接模式 (Bridge)](#-橋接模式-bridge)|[命令模式 (Command)](#-命令模式-command)|
|[抽象工廠模式 (Abstract Factory)](#-抽象工廠模式-abstract-factory)|[組合模式 (Composite)](#-組合模式-composite)|[迭代器模式 (Iterator)](#-迭代器模式-iterator)|
|[生成器（建造者）模式 (Builder)](#-生成器（建造者）模式-builder)|[裝飾器（裝飾者）模式 (Decorator)](#-裝飾器（裝飾者）模式-decorator)|[中介者模式 (Mediator)](#-中介者模式-mediator)|
|[原型模式 (Prototype)](#-原型模式-prototype)|[外觀模式 (Facade)](#-外觀模式-facade)|[備忘錄模式 (Memento)](#-備忘錄模式-memento)|
|[單例模式 (Singleton)](#-單例模式-singleton)|[輕量（享元）模式 (Flyweight)](#-輕量（享元）模式-flyweight)|[觀察者模式 (Observer)](#-觀察者模式-observer)|
||[代理模式 (Proxy)](#-代理模式-proxy)|[訪問者模式 (Visitor)](#-訪問者模式-visitor)|
|||[策略模式 (Strategy)](#-策略模式-strategy)|
|||[狀態模式 (State)](#-狀態模式-state)|
|||[模板方法模式 (Template Method)](#-模板方法模式-template-method)|

# 介紹

設計模式是對於頻繁出現的問題，所產生的解決方案。 **也是針對特定問題，該如何處理的準則。** 設計模式並非如函式庫、套件包等隨插即用的魔法工具；相反地，設計模式是對於特定情境下產生的特定問題，經過眾人嘗試各種解法後，概括出的準則。

> 設計模式是針對頻繁出現的問題，該如何處理的準則。

**維基百科說：**
> 在軟體工程的領域，設計模式是在給定情境下的軟體設計中，對於頻繁發生的問題，所衍生出的可複用解決方案的準則。它並不是能直接轉換成程式碼或機械碼的最終設計。而是一個解決問題的描述或模板，適用於各式不同的情境下。

# ⚠️ 注意

- 設計模式並非能解決所有問題的萬靈丹。
- 在不適合使用設計模式的情境下執意使用，會讓問題更嚴重。
- 一定要記住，設計模式是用於**解決問題**，而非**找出問題**，切勿過度使用。
- 在正確的情境下使用正確的設計模式，能受盡好處；相反，則會對程式碼帶來無盡災難。

> 請注意，以下的程式碼範例，都是使用 PHP-7，但是這並不應該成為你學習的障礙，因為各個語言的核心概念皆是殊途同歸。

# 設計模式的類型

- [創建型設計模式 (Creational Design Patterns)](#創建型設計模式-creational-design-patterns)
- [結構型設計模式 (Structural Design Patterns)](#結構型設計模式-structural-design-patterns)
- [行為型設計模式 (Behavioral Design Patterns)](#行為型設計模式-behavioral-design-patterns)

## 創建型設計模式 (Creational Design Patterns)

簡單來說：
> `創建型設計模式`主要用於如何實例化一個物件或一組相關的物件。

**維基百科說：**
> 在軟體工程中，`創建型設計模式`是用於處理物件創建的機制，試圖以最適合當下情境的方法來創建物件。物件創建的基本形式可能會造成設計問題，或是對整體設計增加額外的複雜度。`創建型設計模式`藉由某種方式來控制物件創建，以此解決前述的問題。

* [簡單工廠模式 (Simple Factory)](#-簡單工廠模式-simple-factory)
* [工廠方法模式 (Factory Method)](#-工廠方法模式-factory-method)
* [抽象工廠模式 (Abstract Factory)](#-抽象工廠模式-abstract-factory)
* [生成器（建造者）模式 (Builder)](#-生成器（建造者）模式-builder)
* [原型模式 (Prototype)](#-原型模式-prototype)
* [單例模式 (Singleton)](#-單例模式-singleton)

### 🏠 簡單工廠模式 (Simple Factory)
--------------
以現實生活為例：
> 想像你正在蓋一棟房子，而現在你正需要幾扇門。你可以穿上工作服，帶上木頭、膠水、釘子和所有一切自造門所需的工具，然後開始幹活造門；或是你輕鬆地打通電話給工廠，讓他們把做好的門送過來，完全不需要先了解門如何製造，也不必經歷過程中的一切混亂。

簡單來說：
> `簡單工廠模式`只單純創建一個實例給`客戶端`，而不需對其暴露任何實例化過程中的邏輯。

**維基百科說：**
> 在`物件導向程式`中，工廠是用於創建其他物件的物件。正式一點說明，工廠是一個函式，能藉由呼叫方法，回傳一個具有不同原型或類別的物件，而這個被呼叫的方法通常是 **`"new"`**。

**程式範例：**

首先，我們有一個 `Door` 介面，實作如下：
```php
interface Door
{
    public function getWidth(): float;
    public function getHeight(): float;
}

class WoodenDoor implements Door
{
    protected $width;
    protected $height;

    public function __construct(float $width, float $height)
    {
        $this->width = $width;
        $this->height = $height;
    }

    public function getWidth(): float
    {
        return $this->width;
    }

    public function getHeight(): float
    {
        return $this->height;
    }
}
```

接著，我們實現 `DoorFactory`，用途是創建 `WoodenDoor` 實例並將其返回：
```php
class DoorFactory
{
    public static function makeDoor($width, $height): Door
    {
        return new WoodenDoor($width, $height);
    }
}
```

最後，可以如下的方式使用：
```php
// Make me a door of 100x200
$door = DoorFactory::makeDoor(100, 200);

echo 'Width: ' . $door->getWidth();
echo 'Height: ' . $door->getHeight();

// Make me a door of 50x100
$door2 = DoorFactory::makeDoor(50, 100);
```

**何時使用？**

當創建一個物件的流程，並不只是賦值而是還包含一些邏輯時，此時將整個流程包裝在專門的工廠中，而非在專案裡四處重複相同的程式碼，就是該模式的一種適用情境。

### 🏭 工廠方法模式 (Factory Method)
--------------

以現實生活為例：
> 以招募經理的工作為例，不可能將所有職位的面試都交給同一個人執行。他必須根據開放的職位，將面試步驟交派給不同人。

簡單來說：
> `工廠方法模式`提供一種方法，將實例化的邏輯交派給子類別。

**維基百科說：**
> 在基於類別的程式設計中，`工廠方法模式`是無需指定要創建物件的特定類別，而能處理創建對象的一種`創建型設計模式`。是藉由呼叫`工廠方法`來創建實例，而不需要調用`建構子`。實際作法可以是提前在介面中指定並交由`子類別（衍生類別）`實現；或是先在`父類別（基礎類別）`中實作，再由`子類別`決定是否要`覆寫 (override)`。

**程式範例**

以我們上面提到的招募經理為例。

首先，我們有一個 `Interviewer` 介面，實作如下：
```php
interface Interviewer
{
    public function askQuestions();
}

class Developer implements Interviewer
{
    public function askQuestions()
    {
        echo 'Asking about design patterns!';
    }
}

class CommunityExecutive implements Interviewer
{
    public function askQuestions()
    {
        echo 'Asking about community building';
    }
}
```

現在來創建我們的 `HiringManager` 類別：
```php
abstract class HiringManager
{

    // Factory method
    abstract protected function makeInterviewer(): Interviewer;

    public function takeInterview()
    {
        $interviewer = $this->makeInterviewer();
        $interviewer->askQuestions();
    }
}

```

現在任何`子類別`都可以藉由繼承 `HiringManager`，來回傳特定的 `Interviewer` 實例：
```php
class DevelopmentManager extends HiringManager
{
    protected function makeInterviewer(): Interviewer
    {
        return new Developer();
    }
}

class MarketingManager extends HiringManager
{
    protected function makeInterviewer(): Interviewer
    {
        return new CommunityExecutive();
    }
}
```

最後，可以如下的方式使用：
```php
$devManager = new DevelopmentManager();
$devManager->takeInterview(); // Output: Asking about design patterns

$marketingManager = new MarketingManager();
$marketingManager->takeInterview(); // Output: Asking about community building.
```

**何時使用？**

對於那些在類別中，存在部分通用的處理流程，但實際需要的`子類別`必須透過運行時動態決定；或者說，當客戶端不清楚它需要哪個特定的子類別時。

### 🔨 抽象工廠模式 (Abstract Factory)
----------------

以現實生活為例：
> 擴展我們在`簡單工廠模式`的門範例。基於你的需求，你可以從木門店取得木門、鐵門店取得鐵門或是從對應的店取得塑膠門。另外，你也可能需要一個擁有不同類型專業能力的人來幫助安裝對應的門，例如：木門需要木匠、鐵門需要焊工等。你可以看到，當前門之間存在一種依賴關係，木門需要木匠、鐵門需要焊工等。

簡單來說：
> 一個集結複數工廠的工廠：將個別獨立但彼此之間存在關聯 / 相依性的工廠集結在一起的工廠，但不需要指定它們具體的類別。

**維基百科說：**
> `抽象工廠模式`提供一個方式，將複數個各自獨立卻又擁有共同主題的工廠封裝在一起，但不需要指定它們具體的類別。

**程式範例**

接下來將上面提到關於門的範例轉換為程式碼。

首先，我們定義一個 `Door` 介面並基於此進行實作：
```php
interface Door
{
    public function getDescription();
}

class WoodenDoor implements Door
{
    public function getDescription()
    {
        echo 'I am a wooden door';
    }
}

class IronDoor implements Door
{
    public function getDescription()
    {
        echo 'I am an iron door';
    }
}
```

接著，我們有適合每種門的安裝專家：
```php
interface DoorFittingExpert
{
    public function getDescription();
}

class Welder implements DoorFittingExpert
{
    public function getDescription()
    {
        echo 'I can only fit iron doors';
    }
}

class Carpenter implements DoorFittingExpert
{
    public function getDescription()
    {
        echo 'I can only fit wooden doors';
    }
}
```

現在，我們有能用於創建一系列相關物件的抽象工廠，例如：木門工廠會創建木門和木門的安裝專家、鐵門工廠會創建鐵門和鐵門的安裝專家：
```php
interface DoorFactory
{
    public function makeDoor(): Door;
    public function makeFittingExpert(): DoorFittingExpert;
}

// Wooden factory to return carpenter and wooden door
class WoodenDoorFactory implements DoorFactory
{
    public function makeDoor(): Door
    {
        return new WoodenDoor();
    }

    public function makeFittingExpert(): DoorFittingExpert
    {
        return new Carpenter();
    }
}

// Iron door factory to get iron door and the relevant fitting expert
class IronDoorFactory implements DoorFactory
{
    public function makeDoor(): Door
    {
        return new IronDoor();
    }

    public function makeFittingExpert(): DoorFittingExpert
    {
        return new Welder();
    }
}
```

最後，可以如下的方式使用：
```php
$woodenFactory = new WoodenDoorFactory();

$door = $woodenFactory->makeDoor();
$expert = $woodenFactory->makeFittingExpert();

$door->getDescription();  // Output: I am a wooden door
$expert->getDescription(); // Output: I can only fit wooden doors

// Same for Iron Factory
$ironFactory = new IronDoorFactory();

$door = $ironFactory->makeDoor();
$expert = $ironFactory->makeFittingExpert();

$door->getDescription();  // Output: I am an iron door
$expert->getDescription(); // Output: I can only fit iron doors
```

你可以看到 `WoodenDoorFactory` 封裝了 `Carpenter` 和 `WoodenDoor`，而 `IronDoorFactory` 則是封裝 `IronDoor` 和 `Welder`。因此能幫助我們確保每個創建的門，不會得到錯誤的安裝專家。

**何時使用？**

當存在相互關聯的依賴，且包含較複雜的創建邏輯時。

### 👷 生成器（建造者）模式 (Builder)
--------------------------------------------

以現實生活為例：
> 想像你正在 Hardee 的餐廳，而且點了一份名為「Big Hardee」的特別餐，而店員*沒有問任何問題*就正確地將餐點送上桌，這就是一個`簡單工廠模式`的範例。但是某些情況下，創建邏輯中可能包含更多步驟。例如：你想要一份客製化的 Subway 套餐，可以選擇麵包的種類、你喜歡的醬汁類型、起司種類等。此時就輪到`生成器模式`出場了。

簡單來說：
> `生成器模式`允許你在避免`建構子`污染的情況下創建一個物件的不同變體。當一個物件存在多種變體，或是創建物件包含許多的步驟時，特別適用。

**維基百科說：**
> `生成器模式`是一種物件創建的軟體設計模式，目的在解決`伸縮建構子反模式 (telescoping constructor anti-pattern)` 問題。

補充說明：什麼是`伸縮建構子`？

我們都曾經看過如下範例的`建構子`：
```php
public function __construct($size, $cheese = true, $pepperoni = true, $tomato = false, $lettuce = true)
{
}
```

你可以看到`建構子`的參數數量，可以很輕易超過一手之數，並且變得難以理解參數的使用範圍。再加上這個參數列表，會在你未來想增加更多可選項時，持續成長。而這就是`伸縮建構子`問題。

**程式範例**

理智的替代方案就是使用`生成器模式`。

首先，我們實做 `Burger`：
```php
class Burger
{
    protected $size;

    protected $cheese = false;
    protected $pepperoni = false;
    protected $lettuce = false;
    protected $tomato = false;

    public function __construct(BurgerBuilder $builder)
    {
        $this->size = $builder->size;
        $this->cheese = $builder->cheese;
        $this->pepperoni = $builder->pepperoni;
        $this->lettuce = $builder->lettuce;
        $this->tomato = $builder->tomato;
    }
}
```

接下來，輪到`生成器`：
```php
class BurgerBuilder
{
    public $size;

    public $cheese = false;
    public $pepperoni = false;
    public $lettuce = false;
    public $tomato = false;

    public function __construct(int $size)
    {
        $this->size = $size;
    }

    public function addPepperoni()
    {
        $this->pepperoni = true;
        return $this;
    }

    public function addLettuce()
    {
        $this->lettuce = true;
        return $this;
    }

    public function addCheese()
    {
        $this->cheese = true;
        return $this;
    }

    public function addTomato()
    {
        $this->tomato = true;
        return $this;
    }

    public function build(): Burger
    {
        return new Burger($this);
    }
}
```

最後，可以如下的方式使用：
```php
$burger = (new BurgerBuilder(14))
                    ->addPepperoni()
                    ->addLettuce()
                    ->addTomato()
                    ->build();
```

**何時使用？**

當一個物件可能有多種變體，而且要避免`伸縮建構子`問題時，可以使用`生成器模式`。和`工廠模式`的主要差異在於：`工廠模式`適用於創建步驟只有一個時；`生成器模式`則適合多個創建步驟時使用。

### 🐑 原型模式 (Prototype)
------------

以現實生活為例：
> 還記得 Dolly 嗎？那隻被克隆的羊！我們不會深入細節，但關鍵點在於克隆。

簡單來說：
> 藉由克隆創建一個基於已存在物件的新物件。

**維基百科說：**
> `原型模式`是軟體開發中，`創建型設計模式`的一種。它用在當*新的*被創建物件的類型，取決於一個*已*創建的原型實例時。通過克隆`原型`實例來產生新對象。

簡單來說，`原型模式`讓你能創建一個已存在物件的`複製體`，並根據你的需求做修改，避免從頭開始創建實例和設定的過程中可能碰到的麻煩。

**程式範例**

在 PHP 中可以簡單地使用 `clone` 方法：
```php
class Sheep
{
    protected $name;
    protected $category;

    public function __construct(string $name, string $category = 'Mountain Sheep')
    {
        $this->name = $name;
        $this->category = $category;
    }

    public function setName(string $name)
    {
        $this->name = $name;
    }

    public function getName()
    {
        return $this->name;
    }

    public function setCategory(string $category)
    {
        $this->category = $category;
    }

    public function getCategory()
    {
        return $this->category;
    }
}
```

接著，可以如下的方式使用：
```php
$original = new Sheep('Jolly');
echo $original->getName(); // Jolly
echo $original->getCategory(); // Mountain Sheep

// Clone and modify what is required
$cloned = clone $original;
$cloned->setName('Dolly');
echo $cloned->getName(); // Dolly
echo $cloned->getCategory(); // Mountain sheep
```

你也能使用魔術方法 `__clone` 來改變克隆行為。

**何時使用？**

當需要一個和已存在物件相似的物件時，或是當創建的成本比起克隆更為昂貴時，就適用`原型模式`。

### 💍 單例模式 (Singleton)
------------

以現實生活為例：
> 一個國家同時只能有一個總統。任何行動都是由同一個總統進行。在這裡總統就是一個`單例模式`。

簡單來說：
> 確保一個特定類別的物件，只有被創建一次。

**維基百科說：**
> 在軟體工程中，`單例模式`是將一個類別的實例化，限制為同一個物件的軟體設計模式。尤其適用於需要`只有一個物件`來協調整個系統操作時。

`單例模式`事實上被視為一個`反模式`，應該避免過度使用它。它不一定是壞的，也有一些有效地使用案例，但應該被小心使用，因為其在你的應用中引入一個全域狀態，造成對`單例`進行改動時，可能意外的影響其他區塊，並帶來除錯上的困難。其它缺點則在於會讓程式過度`耦合`，讓`模擬`單例時遭遇困難。

**程式範例**

要創建`單例`，必須將`建構子`設為私有、禁止克隆、禁止擴展，並創建一個`靜態變數 (static variable)`來保存實例：
```php
final class President
{
    private static $instance;

    private function __construct()
    {
        // Hide the constructor
    }

    public static function getInstance(): President
    {
        if (!self::$instance) {
            self::$instance = new self();
        }

        return self::$instance;
    }

    private function __clone()
    {
        // Disable cloning
    }

    private function __wakeup()
    {
        // Disable unserialize
    }
}
```

接著，可以如下的方式使用：
```php
$president1 = President::getInstance();
$president2 = President::getInstance();

var_dump($president1 === $president2); // true
```

## 結構型設計模式 (Structural Design Patterns)
==========================

簡單來說：
> `結構型設計模式`主要關注於`物件複合 (object composition)`，或者說是`實體 (entity)`間如何相互使用。而另一種解釋是，它們解決的是「如何構建軟體元件？」這個問題。

**維基百科說：**
> 在軟體工程中，`結構型設計模式`是通過確定`實體 (entity)`間關聯性的簡單方式，來簡化設計的一類設計模式。

* [轉接器（適配器）模式 (Adapter)](#-轉接器（適配器）模式-adapter)
* [橋接模式 (Bridge)](#-橋接模式-bridge)
* [組合模式 (Composite)](#-組合模式-composite)
* [裝飾器（裝飾者）模式 (Decorator)](#-裝飾器（裝飾者）模式-decorator)
* [外觀模式 (Facade)](#-外觀模式-facade)
* [輕量（享元）模式 (Flyweight)](#-輕量（享元）模式-flyweight)
* [代理模式 (Proxy)](#-代理模式-proxy)

### 🔌 轉接器（適配器）模式 (Adapter)
-------

以現實生活為例：
> 假設你的記憶卡裡有一些照片，現在你需要將它們傳輸到電腦裡。為了傳輸照片，你需要某種轉接器來連接記憶卡和電腦。在這個例子中，讀卡機就是一個轉接器。
> 另一個例子是電源轉接器，三孔的插頭無法使用兩孔的插座，需要使用電源轉接器讓兩者相容。
> 再一個例子則是翻譯員，將一個人說的話翻譯給另一個人。

簡單來說：
> `轉接器模式`讓你用轉接器包裝一個本來不兼容的物件，使其兼容於另一個類別。

**維基百科說：**
> 在軟體工程中，`轉接器模式`是一種允許使用已存在類別的介面，作為另一個類別介面的軟體設計模式。常被用於使已存在的類別兼容其他類別，而不需要改動原始碼。

**程式範例**

假設有一個遊戲，其中有一個狩獵獅子的獵人。

首先，我們有一個 `Lion` 介面，所有類型的獅子都必須實作它：
```php
interface Lion
{
    public function roar();
}

class AfricanLion implements Lion
{
    public function roar()
    {
    }
}

class AsianLion implements Lion
{
    public function roar()
    {
    }
}
```

而 `Hunter` 的 `hunt` 函式，預期傳入的參數都要實作 `Lion` 介面：
```php
class Hunter
{
    public function hunt(Lion $lion)
    {
        $lion->roar();
    }
}
```

現在我們要在遊戲中加入一個 `WildDog`，讓獵人除了獅子也可以狩獵它。但是我們不能直接這樣做，因為野狗有一個不同的介面。為了讓其兼容我們的獵人，必須創建一個兼容的`轉接器`：
```php
// This needs to be added to the game
class WildDog
{
    public function bark()
    {
    }
}

// Adapter around wild dog to make it compatible with our game
class WildDogAdapter implements Lion
{
    protected $dog;

    public function __construct(WildDog $dog)
    {
        $this->dog = $dog;
    }

    public function roar()
    {
        $this->dog->bark();
    }
}
```

現在 `WildDog` 可以透過 `WildDogAdapter` 被我們的遊戲使用：
```php
$wildDog = new WildDog();
$wildDogAdapter = new WildDogAdapter($wildDog);

$hunter = new Hunter();
$hunter->hunt($wildDogAdapter);
```

### 🚡 橋接模式 (Bridge)
------

以現實生活為例：
> 假如你有一個包含不同頁面的網站，而且你想要允許使用者改變主題。你會怎麼做？對每個頁面的每個主題創建複數個複製體？還是你會只創建單獨的主題並根據使用者各自的偏好進行加載？`橋接模式`讓你能做到第二種。

![With and without the bridge pattern](https://cloud.githubusercontent.com/assets/11269635/23065293/33b7aea0-f515-11e6-983f-98823c9845ee.png)

簡單來說：
> `橋接模式`是偏向於組合而非繼承的設計模式。它將實作的細節由一個階層式結構，推送到另一個具有獨立階層式結構的物件中。

**維基百科說：**
> `橋接模式`是一種軟體工程的設計模式，目的在「將`抽象 (abstract)`和實作`解耦合`，使兩者間可以獨立變化」。

**程式範例**

以我們上面提到的網頁為例。

這裡有一個 `WebPage` 的階層式結構：
```php
interface WebPage
{
    public function __construct(Theme $theme);
    public function getContent();
}

class About implements WebPage
{
    protected $theme;

    public function __construct(Theme $theme)
    {
        $this->theme = $theme;
    }

    public function getContent()
    {
        return "About page in " . $this->theme->getColor();
    }
}

class Careers implements WebPage
{
    protected $theme;

    public function __construct(Theme $theme)
    {
        $this->theme = $theme;
    }

    public function getContent()
    {
        return "Careers page in " . $this->theme->getColor();
    }
}
```

和單獨的 `Theme` 階層式結構：
```php

interface Theme
{
    public function getColor();
}

class DarkTheme implements Theme
{
    public function getColor()
    {
        return 'Dark Black';
    }
}
class LightTheme implements Theme
{
    public function getColor()
    {
        return 'Off white';
    }
}
class AquaTheme implements Theme
{
    public function getColor()
    {
        return 'Light blue';
    }
}
```

接著，可以如下的方式使用：
```php
$darkTheme = new DarkTheme();

$about = new About($darkTheme);
$careers = new Careers($darkTheme);

echo $about->getContent(); // "About page in Dark Black";
echo $careers->getContent(); // "Careers page in Dark Black";
```

### 🌿 組合模式 (Composite)
-----------------

以現實生活為例：
> 每個組織都是由員工組成。員工各自又有相同特性，如：有薪水、有特定責任、可能需要 / 不需要對某人匯報、有 / 沒有下屬等。

簡單來說：
> `組合模式`讓`客戶端`用統一的方法對待各自獨立的物件。

**維基百科說：**
> 在軟體工程中，`組合模式`是一個分區設計模式。`組合模式`描述一組物件被視為一個物件的實例。組合的目的是將物件組合成樹狀結構，以表示`單一和群體階層 (part-whole hierarchies)`。實作`組合模式`能讓`客戶端`統一處理單個物件和組合物件。

**程式範例**

以上面提到的員工為例。

我們有不同的員工類型：
```php
interface Employee
{
    public function __construct(string $name, float $salary);
    public function getName(): string;
    public function setSalary(float $salary);
    public function getSalary(): float;
    public function getRoles(): array;
}

class Developer implements Employee
{
    protected $salary;
    protected $name;
    protected $roles;
    
    public function __construct(string $name, float $salary)
    {
        $this->name = $name;
        $this->salary = $salary;
    }

    public function getName(): string
    {
        return $this->name;
    }

    public function setSalary(float $salary)
    {
        $this->salary = $salary;
    }

    public function getSalary(): float
    {
        return $this->salary;
    }

    public function getRoles(): array
    {
        return $this->roles;
    }
}

class Designer implements Employee
{
    protected $salary;
    protected $name;
    protected $roles;

    public function __construct(string $name, float $salary)
    {
        $this->name = $name;
        $this->salary = $salary;
    }

    public function getName(): string
    {
        return $this->name;
    }

    public function setSalary(float $salary)
    {
        $this->salary = $salary;
    }

    public function getSalary(): float
    {
        return $this->salary;
    }

    public function getRoles(): array
    {
        return $this->roles;
    }
}
```

接著，我們有一個包含多種不同類型員工的組織：
```php
class Organization
{
    protected $employees;

    public function addEmployee(Employee $employee)
    {
        $this->employees[] = $employee;
    }

    public function getNetSalaries(): float
    {
        $netSalary = 0;

        foreach ($this->employees as $employee) {
            $netSalary += $employee->getSalary();
        }

        return $netSalary;
    }
}
```

接著，可以如下的方式使用：
```php
// Prepare the employees
$john = new Developer('John Doe', 12000);
$jane = new Designer('Jane Doe', 15000);

// Add them to organization
$organization = new Organization();
$organization->addEmployee($john);
$organization->addEmployee($jane);

echo "Net salaries: " . $organization->getNetSalaries(); // Net Salaries: 27000
```

### ☕ 裝飾器（裝飾者）模式 (Decorator)
-------------

以現實生活為例：
> 想像你經營一家提供多種服務的汽車服務商店。現在你怎麼計算要請款的帳單？你選擇一種服務，並動態加入所提供服務的價格，直到取得最終成本。在這裡每種服務都是一個`裝飾器`。

簡單來說：
> `裝飾器模式`藉由將它們包裝到`裝飾器`類別的一個物件中，來讓你在運行時動態改變一個物件的行為。

**維基百科說：**
> 在`物件導向程式`中，`裝飾器模式`是一個設計模式，允許行為被加入（靜態或動態地）到獨立的物件中，而不影響相同類別中其他不同物件的行為。`裝飾器模式`對於`單一責任定律 (Single Responsibility Principle)`很有用，它允許在具有唯一關注區域的類別間劃分功能。

**程式範例**

我們以咖啡作為範例。

首先，我們有一個 `Coffee` 介面和一個實作該介面的 `SimpleCoffee` 類別：
```php
interface Coffee
{
    public function getCost();
    public function getDescription();
}

class SimpleCoffee implements Coffee
{
    public function getCost()
    {
        return 10;
    }

    public function getDescription()
    {
        return 'Simple coffee';
    }
}
```

我們想讓程式碼具備可擴展性，以在需要時對其進行修改。

接著，讓我們創建一些`裝飾器`：
```php
class MilkCoffee implements Coffee
{
    protected $coffee;

    public function __construct(Coffee $coffee)
    {
        $this->coffee = $coffee;
    }

    public function getCost()
    {
        return $this->coffee->getCost() + 2;
    }

    public function getDescription()
    {
        return $this->coffee->getDescription() . ', milk';
    }
}

class WhipCoffee implements Coffee
{
    protected $coffee;

    public function __construct(Coffee $coffee)
    {
        $this->coffee = $coffee;
    }

    public function getCost()
    {
        return $this->coffee->getCost() + 5;
    }

    public function getDescription()
    {
        return $this->coffee->getDescription() . ', whip';
    }
}

class VanillaCoffee implements Coffee
{
    protected $coffee;

    public function __construct(Coffee $coffee)
    {
        $this->coffee = $coffee;
    }

    public function getCost()
    {
        return $this->coffee->getCost() + 3;
    }

    public function getDescription()
    {
        return $this->coffee->getDescription() . ', vanilla';
    }
}
```

現在，來做杯咖啡吧：
```php
$someCoffee = new SimpleCoffee();
echo $someCoffee->getCost(); // 10
echo $someCoffee->getDescription(); // Simple Coffee

$someCoffee = new MilkCoffee($someCoffee);
echo $someCoffee->getCost(); // 12
echo $someCoffee->getDescription(); // Simple Coffee, milk

$someCoffee = new WhipCoffee($someCoffee);
echo $someCoffee->getCost(); // 17
echo $someCoffee->getDescription(); // Simple Coffee, milk, whip

$someCoffee = new VanillaCoffee($someCoffee);
echo $someCoffee->getCost(); // 20
echo $someCoffee->getDescription(); // Simple Coffee, milk, whip, vanilla
```

### 📦 外觀模式 (Facade)
----------------

以現實生活為例：
> 怎麼讓電腦開機？你可能會說：「按下電源鍵！」。這只是電腦對外提供的一個簡單介面，而電腦對內實際上需要做一大堆事情來達到目的。這個簡單介面（電源鍵）和複雜子系統（內部的開機流程）之間的聯繫就是`外觀模式`。

簡單來說：
> `外觀模式`為複雜的子系統提供了一個簡單的介面。

**維基百科說：**
> `外觀模式`提供一個簡單的介面，用於操作一個更大型的程式碼，如：函式庫。

**程式範例**

以我們上面提到的電腦為例。

首先，需要實作 `Computer` 類別：
```php
class Computer
{
    public function getElectricShock()
    {
        echo "Ouch!";
    }

    public function makeSound()
    {
        echo "Beep beep!";
    }

    public function showLoadingScreen()
    {
        echo "Loading..";
    }

    public function bam()
    {
        echo "Ready to be used!";
    }

    public function closeEverything()
    {
        echo "Bup bup bup buzzzz!";
    }

    public function sooth()
    {
        echo "Zzzzz";
    }

    public function pullCurrent()
    {
        echo "Haaah!";
    }
}
```

接著創建 `ComputerFacade`：
```php
class ComputerFacade
{
    protected $computer;

    public function __construct(Computer $computer)
    {
        $this->computer = $computer;
    }

    public function turnOn()
    {
        $this->computer->getElectricShock();
        $this->computer->makeSound();
        $this->computer->showLoadingScreen();
        $this->computer->bam();
    }

    public function turnOff()
    {
        $this->computer->closeEverything();
        $this->computer->pullCurrent();
        $this->computer->sooth();
    }
}
```

接著，可以如下的方式使用：
```php
$computer = new ComputerFacade(new Computer());
$computer->turnOn(); // Ouch! Beep beep! Loading.. Ready to be used!
$computer->turnOff(); // Bup bup buzzz! Haah! Zzzzz
```

### 🍃 輕量（享元）模式 (Flyweight)
---------

以現實生活為例：
> 你曾經在路邊攤買過手搖飲嗎？他們通常會做比你點的量更多的茶，然後把剩下的留給其他顧客，以節省資源，如：瓦斯。`輕量模式`就是關於共享的一種實現。

簡單來說：
> `輕量模式`就是透過與類似物件，盡可能共用最多內容，來達到最小化記憶體用量和計算花費。

**維基百科說：**
> 在電腦程式設計中，`輕量模式`是一個軟體設計模式。`輕量模式`是一種最小化記憶體用量的物件，藉由和其他相似物件盡可能多的共用資料，以在大量使用物件時節省記憶體。當簡單的重複操作，會累積使用到超過允許的記憶體總量時，這就是一個讓你能使用大量物件的方式。

**程式範例**

以上面提到的茶為例子。

首先，我們要實作 `KarakTea` 和 `TeaMaker`：
```php
// Anything that will be cached is flyweight.
// Types of tea here will be flyweights.
class KarakTea
{
}

// Acts as a factory and saves the tea
class TeaMaker
{
    protected $availableTea = [];

    public function make($preference)
    {
        if (empty($this->availableTea[$preference])) {
            $this->availableTea[$preference] = new KarakTea();
        }

        return $this->availableTea[$preference];
    }
}
```

接下來，我們實作一個負責接受訂單和提供服務的 `TeaShop` 類別：
```php
class TeaShop
{
    protected $orders;
    protected $teaMaker;

    public function __construct(TeaMaker $teaMaker)
    {
        $this->teaMaker = $teaMaker;
    }

    public function takeOrder(string $teaType, int $table)
    {
        $this->orders[$table] = $this->teaMaker->make($teaType);
    }

    public function serve()
    {
        foreach ($this->orders as $table => $tea) {
            echo "Serving tea to table# " . $table;
        }
    }
}
```

接著，可以如下的方式使用：
```php
$teaMaker = new TeaMaker();
$shop = new TeaShop($teaMaker);

$shop->takeOrder('less sugar', 1);
$shop->takeOrder('more milk', 2);
$shop->takeOrder('without sugar', 5);

$shop->serve();
// Serving tea to table# 1
// Serving tea to table# 2
// Serving tea to table# 5
```

### 🎱 代理模式 (Proxy)
-------------------

以現實生活為例：
> 你使用過門禁卡來開門嗎？有多種選項能達到開門這個目的，例如：可以使用門禁卡或是透過指紋解鎖來通過安全檢查。門的主要功能就是打開，但`代理`為其加上了一些功能。讓我用以下的程式碼範例來更好的解釋它。

簡單來說：
> 使用`代理模式`能讓一個類別代表另一個類別的功能。

**維基百科說：**
> `代理模式`最常見的用途，是用於訪問其他介面的類別。`代理模式`是一個包裝器或是`中介 (agent)`物件，被`客戶端`呼叫來訪問幕後提供服務的真實物件。使用`代理模式`，可以簡單地轉發到真實物件，或是能提供額外的邏輯。`代理模式`可以提供額外的功能，如：在真實物件上的操作是資源密集型時提供快取；或是對真實物件操作前，進行先決條件的確認。

**程式範例**

以我們上面提到的安全門為例。

首先，定義 `Door` 介面和實作 `LabDoor`：
```php
interface Door
{
    public function open();
    public function close();
}

class LabDoor implements Door
{
    public function open()
    {
        echo "Opening lab door";
    }

    public function close()
    {
        echo "Closing the lab door";
    }
}
```

然後，我們有一個`代理`確保任意門的安全性：
```php
class SecuredDoor implements Door
{
    protected $door;

    public function __construct(Door $door)
    {
        $this->door = $door;
    }

    public function open($password)
    {
        if ($this->authenticate($password)) {
            $this->door->open();
        } else {
            echo "Big no! It ain't possible.";
        }
    }

    public function authenticate($password)
    {
        return $password === '$ecr@t';
    }

    public function close()
    {
        $this->door->close();
    }
}
```

接著，可以如下的方式使用：
```php
$door = new SecuredDoor(new LabDoor());
$door->open('invalid'); // Big no! It ain't possible.

$door->open('$ecr@t'); // Opening lab door
$door->close(); // Closing lab door
```

另一個例子是`資料映射 (data-mapper)`的實現。比如：最近我使用該模式，為 MongoDB 實現一個`物件資料映射 (ODM)`，其中我使用到魔術方法 `__call()` 來編寫一個`代理`，其包裝了 mongo 類別的調用。所有方法調用都被`代理`到原始的 mongo 類別，而且檢索到的結果以原樣回傳，但是在 `find` 和 `findOne` 的情況下，資料被映射到所需的類別物件，而使回傳的物件並不是 `Cursor`。

## 行為型設計模式 (Behavioral Design Patterns)
==========================

簡單來說：
> `行為型設計模式`關注物件之間的責任分配。和`結構型設計模式`的差異點在於，`行為型設計模式`不只指定結構，也定義彼此間消息傳遞 / 溝通的模式。而另一種解釋是，它們協助回答「如何在軟體元件中運行一個行為？」這個問題。

**維基百科說：**
> 在軟體工程中，`行為型設計模式`是識別物件之間，常見通訊模式並實現這些模式的設計模式。通過這樣做，模式增加了執行這類通訊的靈活性。

* [責任鏈模式 (Chain of Responsibility)](#-責任鏈模式-chain-of-responsibility)
* [命令模式 (Command)](#-命令模式-command)
* [迭代器模式 (Iterator)](#-迭代器模式-iterator)
* [中介者模式 (Mediator)](#-中介者模式-mediator)
* [備忘錄模式 (Memento)](#-備忘錄模式-memento)
* [觀察者模式 (Observer)](#-觀察者模式-observer)
* [訪問者模式 (Visitor)](#-訪問者模式-visitor)
* [策略模式 (Strategy)](#-策略模式-strategy)
* [狀態模式 (State)](#-狀態模式-state)
* [模板方法模式 (Template Method)](#-模板方法模式-template-method)

### 🔗 責任鏈模式 (Chain of Responsibility)
-----------------------

以現實生活為例：
> 舉例：你的帳戶設定了 3 種付款方式（A, B, C），每種方式都有不同金額。A 有 100 USD、B 有 300 USD、C 有 1000 USD，付款的優先度設置順序為 A -> B -> C。你試著購買 210 USD 的東西。在`責任鏈模式`下，首先 A 會被檢查是否足以付款，如果可以則付款成立且鏈被中斷。如果不行則請求會轉移到 B 並進行和 A 相同的流程，請求會持續被轉移，一直到找到適當的處理程序。在這裡 A, B, C 是鏈的連接，而且整個過程都是`責任鏈`。

簡單來說：
> `責任鏈模式`能夠構建一個物件鏈。當請求進入鏈的其中一端時，會持續從一個物件轉移到下一個物件，直到找到適當的處理程序為止。

**維基百科說：**
> 在物件導向設計中，`責任鏈模式`是一個包含命令物件的來源和一系列處理物件的設計模式。每一個處理物件包含定義它可以處理的命令物件類型的邏輯；剩下的命令物件則被傳遞給鏈中的下一個處理物件。

**程式範例**

以我們上面的帳號為例。

首先，我們有基本的 `Account` 類別，包含連接帳戶的邏輯，還有一些帳戶物件：
```php
abstract class Account
{
    protected $successor;
    protected $balance;

    public function setNext(Account $account)
    {
        $this->successor = $account;
    }

    public function pay(float $amountToPay)
    {
        if ($this->canPay($amountToPay)) {
            echo sprintf('Paid %s using %s' . PHP_EOL, $amountToPay, get_called_class());
        } elseif ($this->successor) {
            echo sprintf('Cannot pay using %s. Proceeding ..' . PHP_EOL, get_called_class());
            $this->successor->pay($amountToPay);
        } else {
            throw new Exception('None of the accounts have enough balance');
        }
    }

    public function canPay($amount): bool
    {
        return $this->balance >= $amount;
    }
}

class Bank extends Account
{
    protected $balance;

    public function __construct(float $balance)
    {
        $this->balance = $balance;
    }
}

class Paypal extends Account
{
    protected $balance;

    public function __construct(float $balance)
    {
        $this->balance = $balance;
    }
}

class Bitcoin extends Account
{
    protected $balance;

    public function __construct(float $balance)
    {
        $this->balance = $balance;
    }
}
```

現在，讓我們以上面定義的連接 (`Bank`, `Paypal`, `Bitcoin`) 來準備鏈：
```php
// Let's prepare a chain like below
//      $bank->$paypal->$bitcoin
//
// First priority bank
//      If bank can't pay then paypal
//      If paypal can't pay then bit coin

$bank = new Bank(100);          // Bank with balance 100
$paypal = new Paypal(200);      // Paypal with balance 200
$bitcoin = new Bitcoin(300);    // Bitcoin with balance 300

$bank->setNext($paypal);
$paypal->setNext($bitcoin);

// Let's try to pay using the first priority i.e. bank
$bank->pay(259);

// Output will be
// ==============
// Cannot pay using bank. Proceeding ..
// Cannot pay using paypal. Proceeding ..:
// Paid 259 using Bitcoin!
```

### 👮 命令模式 (Command)
-------

以現實生活為例：
> 一個通用的例子是在餐廳裡點餐。`你 (Client)` 詢問`服務生 (Invoker)` 要`帶走一些食物 (Command)`，而服務生簡單地將請求轉達給`主廚 (Receiver)`，主廚知道要煮什麼以及怎麼煮。
> 另一個例子是，`你 (Client)` 用`遙控器 (Invoker)` `打開 (Command)` `電視 (Receiver)`。

簡單來說：
> 允許你將行為封裝在物件中。`命令模式`背後的關鍵概念，在於提供從`客戶端`到`接收者 (Receiver)``解耦合`的方式。

**維基百科說：**
> 在`物件導向程式`中，`命令模式`是一種`行為型設計模式`。其中一個物件被用於`封裝`執行操作，或是在之後觸發事件所需的所有資訊。這些資訊包含方法名稱、擁有該方法的物件和該方法參數的值。

**程式範例**

首先，我們有一個`接收者 (Receiver)`，負責實現可以執行的每個動作：
```php
// Receiver
class Bulb
{
    public function turnOn()
    {
        echo "Bulb has been lit";
    }

    public function turnOff()
    {
        echo "Darkness!";
    }
}
```

接著，我們有一個 `Command` 介面，每個命令都必須實作它，和一些命令的實作：
```php
interface Command
{
    public function execute();
    public function undo();
    public function redo();
}

// Command
class TurnOn implements Command
{
    protected $bulb;

    public function __construct(Bulb $bulb)
    {
        $this->bulb = $bulb;
    }

    public function execute()
    {
        $this->bulb->turnOn();
    }

    public function undo()
    {
        $this->bulb->turnOff();
    }

    public function redo()
    {
        $this->execute();
    }
}

class TurnOff implements Command
{
    protected $bulb;

    public function __construct(Bulb $bulb)
    {
        $this->bulb = $bulb;
    }

    public function execute()
    {
        $this->bulb->turnOff();
    }

    public function undo()
    {
        $this->bulb->turnOn();
    }

    public function redo()
    {
        $this->execute();
    }
}
```

接下來，則是`調用者 (Invoker)`，`客戶端`將與其互動以處理任意`命令 (Command)`：
```php
// Invoker
class RemoteControl
{
    public function submit(Command $command)
    {
        $command->execute();
    }
}
```

最後，來看看如何使用：
```php
$bulb = new Bulb();

$turnOn = new TurnOn($bulb);
$turnOff = new TurnOff($bulb);

$remote = new RemoteControl();
$remote->submit($turnOn); // Bulb has been lit!
$remote->submit($turnOff); // Darkness!
```

`命令模式`也可以被用於實作一個基於事務的系統。你可以在執行命令時保持歷史紀錄。如果最終命令執行成功，則一切正常；否則只要迭代歷史紀錄，並在所有已執行的命令上執行 **undo** 即可。

### ➿ 迭代器模式 (Iterator)
--------

以現實生活為例：
> 一台老式收音機是`迭代器模式`最好的例子，使用者可以從某個頻道開始，然後使用下一個或上一個的按鈕，來瀏覽相應的頻道。
> 另一個例子是 MP3 播放器或是電視，你一樣可以使用下一個或上一個的按鈕，來瀏覽相應的頻道、音樂或電台，也就是說，它們都提供了一個介面，來瀏覽相應的頻道、音樂或電台。

簡單來說：
> `迭代器模式`提供一個方式來使用物件元素，而不需要暴露底層實現的細節。

**維基百科說：**
> 在`物件導向程式`中，`迭代器模式`是一種透過迭代器遍歷容器並使用其元素的設計模式。`迭代器模式`將容器和演算法`解耦合`；在某些案例中，演算法必須基於特定容器，因此無法被`解耦合`。

**程式範例**

要在 PHP 中實作`迭代器模式`非常簡單，只需要使用 `Standard PHP Library (SPL)` 即可。

以我們上面的廣播電台為例。

首先，實作一個 `RadioStation` 類別：
```php
class RadioStation
{
    protected $frequency;

    public function __construct(float $frequency)
    {
        $this->frequency = $frequency;
    }

    public function getFrequency(): float
    {
        return $this->frequency;
    }
}
```

接著，實現`迭代器`：
```php
use Countable;
use Iterator;

class StationList implements Countable, Iterator
{
    /** @var RadioStation[] $stations */
    protected $stations = [];

    /** @var int $counter */
    protected $counter;

    public function addStation(RadioStation $station)
    {
        $this->stations[] = $station;
    }

    public function removeStation(RadioStation $toRemove)
    {
        $toRemoveFrequency = $toRemove->getFrequency();
        $this->stations = array_filter($this->stations, function (RadioStation $station) use ($toRemoveFrequency) {
            return $station->getFrequency() !== $toRemoveFrequency;
        });
    }

    public function count(): int
    {
        return count($this->stations);
    }

    public function current(): RadioStation
    {
        return $this->stations[$this->counter];
    }

    public function key()
    {
        return $this->counter;
    }

    public function next()
    {
        $this->counter++;
    }

    public function rewind()
    {
        $this->counter = 0;
    }

    public function valid(): bool
    {
        return isset($this->stations[$this->counter]);
    }
}
```

接著，可以如下的方式使用：
```php
$stationList = new StationList();

$stationList->addStation(new RadioStation(89));
$stationList->addStation(new RadioStation(101));
$stationList->addStation(new RadioStation(102));
$stationList->addStation(new RadioStation(103.2));

foreach($stationList as $station) {
    echo $station->getFrequency() . PHP_EOL;
}

$stationList->removeStation(new RadioStation(89)); // Will remove station 89
```

### 👽 中介者模式 (Mediator)
========

以現實生活為例：
> 一個常見的例子會是，當你和某個人用手機通話時，會有一個網路商介在你和對方之間，而你的對話會通過網路商轉送給對方，而非直接送達。在這個情況下，網路商就是`中介者`。

簡單來說：
> `中介者模式`增加一個`第三方物件（中介者）`來控制兩個物件之間的互動。`中介者模式`有助於降低類別之間溝通的`耦合`程度。因為現在類別不需要知道彼此實作的細節。

**維基百科說：**
> 在軟體工程中，`中介者模式`定義了一個物件，它`封裝`一組物件間的互動方式。由於這個模式能改變程式的執行行為，因此被視為是一種`行為型設計模式`。

**程式範例**

這裡將以一個最簡單的聊天室作為範例，包含一個`聊天室 (中介者)`、一群互相傳送訊息的使用者。

首先，我們來實作`聊天室`：
```php
interface ChatRoomMediator 
{
    public function showMessage(User $user, string $message);
}

// Mediator
class ChatRoom implements ChatRoomMediator
{
    public function showMessage(User $user, string $message)
    {
        $time = date('M d, y H:i');
        $sender = $user->getName();

        echo $time . '[' . $sender . ']:' . $message;
    }
}
```

接著，則是使用者：
```php
class User {
    protected $name;
    protected $chatMediator;

    public function __construct(string $name, ChatRoomMediator $chatMediator) {
        $this->name = $name;
        $this->chatMediator = $chatMediator;
    }

    public function getName() {
        return $this->name;
    }

    public function send($message) {
        $this->chatMediator->showMessage($this, $message);
    }
}
```

接著，可以如下的方式使用：
```php
$mediator = new ChatRoom();

$john = new User('John Doe', $mediator);
$jane = new User('Jane Doe', $mediator);

$john->send('Hi there!');
$jane->send('Hey!');

// Output will be
// Feb 14, 10:58 [John]: Hi there!
// Feb 14, 10:58 [Jane]: Hey!
```

### 💾 備忘錄模式 (Memento)
-------

以現實生活為例：
> 以`計算機 (Originator)`為例，當你進行一些計算後，上一個計算結果會被存在`記憶體 (Memento)`中，讓你可以取得結果，或是透過一些`操作按鍵 (Caretaker)`，將狀態恢復。

簡單來說：
> `備忘錄模式`是獲取和儲存物件當前狀態，以便後續能順利恢復狀態的一種方法。

**維基百科說：**
> `備忘錄模式`是一種軟體設計模式，它提供物件恢復到先前狀態的能力（透過`回滾 (rollback)`做到`撤銷 (undo)`）。

通常在你需要提供某些`撤銷`功能時很有用處。

**程式範例**

以文字編輯器作為範例，它會定期保存工作狀態，讓你在需要時可以將狀態恢復到某個特定時間點。

首先，我們實作一個 `EditorMemento` 類別，能夠保存編輯器狀態：
```php
class EditorMemento
{
    protected $content;

    public function __construct(string $content)
    {
        $this->content = $content;
    }

    public function getContent()
    {
        return $this->content;
    }
}
```

然後，實作 `Editor` 類別 (Originator)，它將會使用 `EditorMemento` (Memento) 物件：
```php
class Editor
{
    protected $content = '';

    public function type(string $words)
    {
        $this->content = $this->content . ' ' . $words;
    }

    public function getContent()
    {
        return $this->content;
    }

    public function save()
    {
        return new EditorMemento($this->content);
    }

    public function restore(EditorMemento $memento)
    {
        $this->content = $memento->getContent();
    }
}
```

接著，可以如下的方式使用：
```php
$editor = new Editor();

// Type some stuff
$editor->type('This is the first sentence.');
$editor->type('This is second.');

// Save the state to restore to : This is the first sentence. This is second.
$saved = $editor->save();

// Type some more
$editor->type('And this is third.');

// Output: Content before Saving
echo $editor->getContent(); // This is the first sentence. This is second. And this is third.

// Restoring to last saved state
$editor->restore($saved);

$editor->getContent(); // This is the first sentence. This is second.
```

### 😎 觀察者模式 (Observer)
--------

以現實生活為例：
> 一個不錯的例子是，求職者訂閱某些求職網站，當有符合條件的工作機會發布時，他們就會收到通知。

簡單來說：
> `觀察者模式`定義了一種物件之間的依賴關係，因此當一個物件的狀態發生改變時，該物件的所有依賴者都會收到通知。

**維基百科說：**
> `觀察者模式`是一種軟體設計模式，一個`物件 (Subject)`維護一組它的`依賴者 (Observer)`名單，當有任何狀態改變時，透過呼叫這些依賴物件的方法來自動通知它們。

**程式範例**

以上面的求職者為例。首先，我們需要實作 `JobPost`, `JobSeeker` 類別，讓一個求職者在職缺發布時收到通知：
```php
class JobPost
{
    protected $title;

    public function __construct(string $title)
    {
        $this->title = $title;
    }

    public function getTitle()
    {
        return $this->title;
    }
}

class JobSeeker implements Observer
{
    protected $name;

    public function __construct(string $name)
    {
        $this->name = $name;
    }

    public function onJobPosted(JobPost $job)
    {
        // Do something with the job posting
        echo 'Hi ' . $this->name . '! New job posted: '. $job->getTitle();
    }
}
```

然後，是求職者會訂閱的求職網站：
```php
class EmploymentAgency implements Observable
{
    protected $observers = [];

    protected function notify(JobPost $jobPosting)
    {
        foreach ($this->observers as $observer) {
            $observer->onJobPosted($jobPosting);
        }
    }

    public function attach(Observer $observer)
    {
        $this->observers[] = $observer;
    }

    public function addJob(JobPost $jobPosting)
    {
        $this->notify($jobPosting);
    }
}
```

接著，可以如下的方式使用：
```php
// Create subscribers
$johnDoe = new JobSeeker('John Doe');
$janeDoe = new JobSeeker('Jane Doe');

// Create publisher and attach subscribers
$jobPostings = new EmploymentAgency();
$jobPostings->attach($johnDoe);
$jobPostings->attach($janeDoe);

// Add a new job and see if subscribers get notified
$jobPostings->addJob(new JobPost('Software Engineer'));

// Output
// Hi John Doe! New job posted: Software Engineer
// Hi Jane Doe! New job posted: Software Engineer
```

### 🏃 訪問者模式 (Visitor)
-------

以現實生活為例：
> 假設有人到杜拜旅遊，他們需要一個方式（如：簽證）來進入杜拜。抵達後，他們不需要取得權限或任何複雜的步驟，就能夠在杜拜境內四處參觀。`訪問者模式`讓你做到相同的事情，它幫助你添加地點，這樣就能讓其他人隨意參觀而不需任何複雜步驟。

簡單來說：
> `訪問者模式`讓你在不修改物件的情況下，將操作加入其中。

**維基百科說：**
> 在`物件導向程式`和軟體工程中，`訪問者模式`是一個將演算法和操作的物件結構分開的方法。這種分開的一種實際結果，是能在現有的物件結構中加入新的操作，而不需要改變它們的結構。這是遵循`開閉原則 (open/closed principle)`的一種方式。

**程式範例**

讓我們舉一個動物園作為例子，這裡有許多不同種類的動物，而我們需要讓它們發出聲音。

首先，定義 `Animal` (受訪者 visitee), `AnimalOperation` (訪問者 visitor) 介面：
```php
// Visitee
interface Animal
{
    public function accept(AnimalOperation $operation);
}

// Visitor
interface AnimalOperation
{
    public function visitMonkey(Monkey $monkey);
    public function visitLion(Lion $lion);
    public function visitDolphin(Dolphin $dolphin);
}
```

然後，來進行動物們的實作：
```php
class Monkey implements Animal
{
    public function shout()
    {
        echo 'Ooh oo aa aa!';
    }

    public function accept(AnimalOperation $operation)
    {
        $operation->visitMonkey($this);
    }
}

class Lion implements Animal
{
    public function roar()
    {
        echo 'Roaaar!';
    }

    public function accept(AnimalOperation $operation)
    {
        $operation->visitLion($this);
    }
}

class Dolphin implements Animal
{
    public function speak()
    {
        echo 'Tuut tuttu tuutt!';
    }

    public function accept(AnimalOperation $operation)
    {
        $operation->visitDolphin($this);
    }
}
```

讓我們實作`訪問者 (visitor)`：
```php
class Speak implements AnimalOperation
{
    public function visitMonkey(Monkey $monkey)
    {
        $monkey->shout();
    }

    public function visitLion(Lion $lion)
    {
        $lion->roar();
    }

    public function visitDolphin(Dolphin $dolphin)
    {
        $dolphin->speak();
    }
}
```

接著，可以如下的方式使用：
```php
$monkey = new Monkey();
$lion = new Lion();
$dolphin = new Dolphin();

$speak = new Speak();

$monkey->accept($speak);    // Ooh oo aa aa!    
$lion->accept($speak);      // Roaaar!
$dolphin->accept($speak);   // Tuut tutt tuutt!
```

我們也可以透過為動物創建繼承，來簡單實現上面的操作，但在未來想為動物加入新的操作時，就需要修改動物類別中的程式碼。但是只要使用`訪問者模式`，我們就不需要改變它們。例如：我們想要對動物增加`跳躍`的行為，可以很容易的透過增加一個新的`訪問者`來實現：
```php
class Jump implements AnimalOperation
{
    public function visitMonkey(Monkey $monkey)
    {
        echo 'Jumped 20 feet high! on to the tree!';
    }

    public function visitLion(Lion $lion)
    {
        echo 'Jumped 7 feet! Back on the ground!';
    }

    public function visitDolphin(Dolphin $dolphin)
    {
        echo 'Walked on water a little and disappeared';
    }
}
```

使用方式則如下：
```php
$jump = new Jump();

$monkey->accept($speak);   // Ooh oo aa aa!
$monkey->accept($jump);    // Jumped 20 feet high! on to the tree!

$lion->accept($speak);     // Roaaar!
$lion->accept($jump);      // Jumped 7 feet! Back on the ground!

$dolphin->accept($speak);  // Tuut tutt tuutt!
$dolphin->accept($jump);   // Walked on water a little and disappeared
```

### 💡 策略模式 (Strategy)
--------

以現實生活為例：
> 以排序為例，我們一開始實作`泡沫排序 (bubble sort)`，但隨著資料量增加造成排序速度越來越慢。為了解決這個問題，我們決定改為實現`快速排序 (quick sort)`。但現在雖然在大量資料集的情況下，`快速排序`演算法的表現很好，一但碰到小型資料集，就會出現很慢的情況。為了處理這個問題，我們實作了一個策略：對於小資料集，使用`泡沫排序`；而對於大資料集，則使用`快速排序`。

簡單來說：
> `策略模式`允許你根據不同情境，切換演算法或是策略。

**維基百科說：**
> 在電腦程式設計中，`策略模式`是一種`行為型軟體設計模式`，它允許一個演算法的行為，能在執行時被動態選擇。

**程式範例**

以我們上面提到的情境為例。

首先，我們有 `SortStrategy` 介面和不同策略的實作：
```php
interface SortStrategy
{
    public function sort(array $dataset): array;
}

class BubbleSortStrategy implements SortStrategy
{
    public function sort(array $dataset): array
    {
        echo "Sorting using bubble sort";

        // Do sorting
        return $dataset;
    }
}

class QuickSortStrategy implements SortStrategy
{
    public function sort(array $dataset): array
    {
        echo "Sorting using quick sort";

        // Do sorting
        return $dataset;
    }
}
```

然後，是我們的`客戶端`，它將能使用任意策略：
```php
class Sorter
{
    protected $sorter;

    public function __construct(SortStrategy $sorter)
    {
        $this->sorter = $sorter;
    }

    public function sort(array $dataset): array
    {
        return $this->sorter->sort($dataset);
    }
}
```

接著，可以如下的方式使用：
```php
$dataset = [1, 5, 4, 3, 2, 8];

$sorter = new Sorter(new BubbleSortStrategy());
$sorter->sort($dataset); // Output : Sorting using bubble sort

$sorter = new Sorter(new QuickSortStrategy());
$sorter->sort($dataset); // Output : Sorting using quick sort
```

### 💢 狀態模式 (State)
-----

以現實生活為例：
> 想像你正在使用某個繪畫應用程式，你選擇畫筆來開始畫畫。現在，畫筆會基於選擇的顏色改變行為，如：你選擇紅色，它就畫出紅色；若選擇藍色，則畫出藍色等。

簡單來說：
> `狀態模式`讓你能在狀態改變時改變一個類別的行為。

**維基百科說：**
> `狀態模式`是一種`行為型軟體設計模式`，以`物件導向`的方式實做一個狀態機。在`狀態模式`中，透過將每個獨立的狀態實作為`狀態模式`介面的`子類別 (derived class)`，並透過`調用 (invoke)`由模式的父類別所定義的方法，來實現狀態轉換。
> `狀態模式`可以被解釋為一種`策略模式`，可以藉由調用被定義在模式介面中的方法，來切換當前的策略。

**程式範例**

我們以文字編輯器為例，它讓你能改變輸入的文字狀態，如：你選擇了粗體，則接下來輸入的字將會變成粗體格式，若選擇斜體，則輸入變成斜體格式等。

首先，我們有 `WritingState` 介面和一些狀態的實作：
```php
interface WritingState
{
    public function write(string $words);
}

class UpperCase implements WritingState
{
    public function write(string $words)
    {
        echo strtoupper($words);
    }
}

class LowerCase implements WritingState
{
    public function write(string $words)
    {
        echo strtolower($words);
    }
}

class DefaultText implements WritingState
{
    public function write(string $words)
    {
        echo $words;
    }
}
```

之後則是編輯器：
```php
class TextEditor
{
    protected $state;

    public function __construct(WritingState $state)
    {
        $this->state = $state;
    }

    public function setState(WritingState $state)
    {
        $this->state = $state;
    }

    public function type(string $words)
    {
        $this->state->write($words);
    }
}
```

接著，可以如下的方式使用：
```php
$editor = new TextEditor(new DefaultText());

$editor->type('First line');

$editor->setState(new UpperCase());

$editor->type('Second line');
$editor->type('Third line');

$editor->setState(new LowerCase());

$editor->type('Fourth line');
$editor->type('Fifth line');

// Output:
// First line
// SECOND LINE
// THIRD LINE
// fourth line
// fifth line
```

### 📒 模板方法模式 (Template Method)
---------------

以現實生活為例：
> 假如我們正在蓋一棟房子，建造的步驟可能像這樣：
> - 準備房子的地基
> - 蓋牆壁
> - 加上屋頂
> - 加上其他樓層

> 這些步驟的順序將永遠不能被改變，如：你不可能在建好牆壁之前蓋屋頂等，但每個步驟都能夠被修改，例如：牆壁的材質可以改成木頭、聚酯纖維或是石頭。

簡單來說：
> `模板方法模式`定義了一個演算法被實現的骨架，但是將具體步驟的實作推延到子類別中。

**維基百科說：**
> 在軟體工程中，`模板方法模式`是一種`行為型設計模式`，它在一個操作中定義了演算法的程式骨架，並將某些步驟推延到子類別中。它允許重新定義演算法中的某些步驟，而不需要改變演算法的結構。

**程式範例**

假如我們有一個構建工具，能協助我們測試、錯誤檢測、構建、產生構建報告，如：程式碼覆蓋率報告、錯誤檢測報告等，並在測試伺服器上部署我們的服務。

首先，我們有 `Builder` 類別，指定要構建演算法的骨架：
```php
abstract class Builder
{

    // Template method
    final public function build()
    {
        $this->test();
        $this->lint();
        $this->assemble();
        $this->deploy();
    }

    abstract public function test();
    abstract public function lint();
    abstract public function assemble();
    abstract public function deploy();
}
```

接下來，我們繼續實作：
```php
class AndroidBuilder extends Builder
{
    public function test()
    {
        echo 'Running android tests';
    }

    public function lint()
    {
        echo 'Linting the android code';
    }

    public function assemble()
    {
        echo 'Assembling the android build';
    }

    public function deploy()
    {
        echo 'Deploying android build to server';
    }
}

class IosBuilder extends Builder
{
    public function test()
    {
        echo 'Running ios tests';
    }

    public function lint()
    {
        echo 'Linting the ios code';
    }

    public function assemble()
    {
        echo 'Assembling the ios build';
    }

    public function deploy()
    {
        echo 'Deploying ios build to server';
    }
}
```

接著，可以如下的方式使用：
```php
$androidBuilder = new AndroidBuilder();
$androidBuilder->build();

// Output:
// Running android tests
// Linting the android code
// Assembling the android build
// Deploying android build to server

$iosBuilder = new IosBuilder();
$iosBuilder->build();

// Output:
// Running ios tests
// Linting the ios code
// Assembling the ios build
// Deploying ios build to server
```

## 🚦 Wrap Up Folks

And that about wraps it up. I will continue to improve this, so you might want to watch/star this repository to revisit. Also, I have plans on writing the same about the architectural patterns, stay tuned for it.

## 👬 Contribution

- Report issues
- Open pull request with improvements
- Spread the word
- Reach out with any feedback [![Twitter URL](https://img.shields.io/twitter/url/https/twitter.com/kamranahmedse.svg?style=social&label=Follow%20%40kamranahmedse)](https://twitter.com/kamranahmedse)

## License

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)

Pack pack = new Pack(1000, 5000, 5);
Pack.System(pack);

class Pack
{
    private static int maxWeight, maxVolume, maxCount;
    static private int currentWeight, currentVolume, currentCount;

    static InventoryItem item = new InventoryItem();

    static InventoryItem[] BagItems = new InventoryItem[]
        {item};

    public Pack(int weight, int volume, int count)
    {
        maxWeight = weight;
        maxVolume = volume;
        maxCount = count;
    }
    public int MaxWeight {get => maxWeight;}
    public int MaxVolume{get => maxVolume;}
    public int MaxCount{get => maxCount;}
    public int CurrentWeight {get => currentWeight;}
    public int CurrentVolume { get => currentVolume; }
    public int CurrentCount { get => currentCount; }

    public static void System(Pack pack)
    {
        while (pack.Add(item))
        {
            Console.WriteLine
                (
                $"Pack is currently at {currentCount}/{maxCount} items, " +
                $"{currentWeight}/{maxWeight} weight, and " +
                $"{currentVolume} / {maxVolume} volume."
                );

            Console.WriteLine("What do you want to add?");
            Console.WriteLine("1 - Sword");
            Console.WriteLine("2 - Shield");
            Console.WriteLine("3 - Armor");
            Console.WriteLine("4 - Bow");
            Console.WriteLine("5 - Spell");
            Console.WriteLine("6 - Cloak");
            int userInput = Convert.ToInt32(Console.ReadLine());

            if (userInput == 1)
            {
                item = new Sword();
                BagItems.Append(item);
                currentCount++;
                currentWeight += item.Weight;
                currentVolume += item.Volume;
            }
            else if (userInput == 2)
            {
                item = new Shield();
                BagItems.Append(item);
                currentCount++;
                currentWeight += item.Weight;
                currentVolume += item.Volume;
            }
            else if (userInput == 3)
            {
                item = new Armor();
                BagItems.Append(item);
                currentCount++;
                currentWeight += item.Weight;
                currentVolume += item.Volume;
            }
            else if (userInput == 4)
            {
                item = new Bow();
                BagItems.Append(item);
                currentCount++;
                currentWeight += item.Weight;
                currentVolume += item.Volume;
            }
            else if (userInput == 5)
            {
                item = new Spell();
                BagItems.Append(item);
                currentCount++;
                currentWeight += item.Weight;
                currentVolume += item.Volume;
            }
            else if (userInput == 6)
            {
                item = new Cloak();
                BagItems.Append(item);
                currentCount++;
                currentWeight += item.Weight;
                currentVolume += item.Volume;
            }
            else
            {
                Console.WriteLine("Error");
                continue;
            }
        }
        Console.WriteLine("YOU ARE over encumbered!!");

        Console.WriteLine
        (
        $"Pack is currently at {currentCount}/{maxCount} items, " +
        $"{currentWeight}/{maxWeight} weight, and " +
        $"{currentVolume} / {maxVolume} volume."
        );

    }

    public bool Add(InventoryItem item)
    {
        if(CurrentCount >= MaxCount)
        {
            return false;
        }
        if(CurrentVolume >= MaxVolume)
        {
            return false;
        }
        if (CurrentWeight >= MaxWeight)
        {
            return false;
        }
        else
        {
            return true;
        }
    }

}
class InventoryItem
{
    private int volume;
    private int weight;

    public InventoryItem()
    {

    }
    public InventoryItem(int v, int w)
    {
        this.weight = w;
        this.volume = v;
    }

    public int Volume
    {
        get => volume;
        set => volume = value;
    }

    public int Weight
    {
        get => weight;
        set => weight = value;
    }
}

class Sword : InventoryItem{public Sword() : base(5, 10){}}
class Shield : InventoryItem { public Shield() : base(55, 100) { } }
class Armor : InventoryItem { public Armor() : base(555, 1500) { } }
class Bow : InventoryItem { public Bow() : base(3, 12) { } }
class Spell : InventoryItem { public Spell() : base(1, 5) { } }
class Cloak : InventoryItem { public Cloak() : base(2, 2) { } }

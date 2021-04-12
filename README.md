using System;

namespace DUNGEON_Pascal_Mangold
{
    class Program
    {
        static void Main(string[] args)
        {
            while (true)
            {
                int hp = 3;
                int simple = 5;
                int normal = 7;
                int difficult = 10;
                int insane = 30;
                int difficulty;
                int input;
                int doinput;
                int direction;
                int desicion;
                int again;
                int xp = 0;
                int lvl = 1;
                int diflvl = 50;
                int gold = 0;
                int items = 0;
                string[] progress = new string[31];

                if (hp == 0)
                {
                    Console.WriteLine("U died, noob");
                    break;
                }
                Console.WriteLine("Set ur difficulty!\n| 1 Simple | 2 Normal | 3 Difficult | 4 Insane |");
                input = Convert.ToInt32(Console.ReadLine());
                if (input == 1)
                {
                    difficulty = simple;
                }
                else if (input == 2)
                {
                    difficulty = normal;
                }
                else if (input == 3)
                {
                    difficulty = difficult;
                }
                else
                {
                    difficulty = insane;
                }
                for (int j = 1; j <= difficulty; j++)
                {
                    Random randomizer = new Random();
                    Console.WriteLine("-----------Room: " + j + " -----------\n");
                    int encounter = randomizer.Next(1, 11);
                    Console.WriteLine("HP: " + hp + " XP: " + xp + " Lvl: " + lvl + " Gold: " + gold + " Items: " + items);
                    if (encounter <= 8)
                    {
                        Console.WriteLine("\nAPPROACHING MONSTER\n         __\n       _|  |_\n     _|      |_\n    |  _    _  |\n    | |_|  |_| |\n _  |  _    _  |  _\n|_|_|_| |__| |_|_|_|\n  |_|_        _|_|\n    |_|      |_|\n\nWhat du you want to do?\n| 1 ATTACK | 2 RUN |");
                        doinput = Convert.ToInt32(Console.ReadLine());
                        int winChance = randomizer.Next(1, 101);
                        int fleeChance = randomizer.Next(1, 3);
                        if (doinput == 1)
                        {
                            if (winChance <= diflvl)
                            {
                                Console.WriteLine("\nU WON heroic against the monster! U are a HERO [...] atleast for now. (+1HP)(+50XP)(+2GOLD)");
                                hp++;
                                xp += 50;
                                gold += 2;
                            }
                            else
                            {
                                Console.WriteLine("\nU stabbed the tree behind the monster! (-1HP)");
                                hp--;
                            }
                        }
                        else
                        {
                            if (fleeChance == 1)
                            {
                                Console.WriteLine("\nU escaped successfully! (+1HP)(+50XP)");
                                hp++;
                                xp += 50;
                            }
                            else
                            {
                                Console.WriteLine("\nU didnt escaped. (-1hp)");
                                hp--;
                            }
                        }
                        progress[j] = "Monster";
                        if (hp == 0)
                        {
                            Console.WriteLine("\nU died, NOOB. Next time try RUSH B!");
                            break;
                        }
                    }
                    else if (encounter == 9)
                    {
                        string[] treasure = new string[] { "a shoe", "a jar of dirt", "ur moms underwear", "ET the Game" };
                        int a = randomizer.Next(0, 4);
                        Console.WriteLine("TREASURE\nU found " + treasure[a] + ". (+100XP)(+4GOLD)");
                        xp += 100;
                        gold += 4;
                        progress[j] = "Treasure";
                    }
                    else
                    {
                        Console.WriteLine("NOTHING\nU sit in a room with a penny, a tissue and a chip. \n[...] Ur having fun... ");
                        progress[j] = "Nothing";
                    }

                    // lvl 1 -> 100xp
                    // lvl 2 -> 200xp
                    // ...
                    if (xp >= lvl * 100)
                    {
                        Console.WriteLine("+++ LEVEL UP! +++");
                        lvl++;
                        diflvl++;
                    }

                    Console.WriteLine("\nA merchant appears!\nDo u want to buy one Item for 2 Gold? (1 YES) (2 NO)\nU currently have " + gold + " Gold.");
                    desicion = Convert.ToInt32(Console.ReadLine());
                    int b = randomizer.Next(0, 4);
                    string[] item = new string[] { "a slippery sword", "slimy slime shotgun", "a squishy cat", "panties for ur head" };
                    if (desicion == 1)
                    {
                        if (gold >= 2)
                        {
                            Console.WriteLine("U bought ... " + item[b] + ".");
                            gold -= 2;
                            items++;
                            diflvl += 2;
                        }
                        else
                        {
                            Console.WriteLine("U tried to scam the merchant. U fool hes also a magician!\n*A FIREBOLT HIT u in the NUTS* (-1HP)");
                            hp--;
                        }
                    }
                    Console.WriteLine("\nWanna go (1) Left, (2) through the Middle or (3) Right?");
                    direction = Convert.ToInt32(Console.ReadLine());
                    switch (direction)
                    {
                        case 1:
                            {
                                Console.WriteLine("U go left.");
                                break;
                            }
                        case 2:
                            {
                                Console.WriteLine("U go through the middle.");
                                break;
                            }
                        default:
                            {
                                Console.WriteLine("U go right.");
                                break;
                            }
                    }
                }
                Console.WriteLine("\n------------------------------\nStats: HP: " + hp + " XP: " + xp + " Lvl: " + lvl + " Gold: " + gold + " Items: " + items + ".\nUr progession was:");
                for (int j = 1; j <= difficulty; j++)
                {
                    Console.WriteLine("Room: " + j + " - " + progress[j]);
                }
                Console.WriteLine("------------------------------\n");
                Console.WriteLine("Wanna play (1) again or (2) not?");
                again = Convert.ToInt32(Console.ReadLine());
                if (again != 1)
                {
                    break;
                }
            }
        }
    }
}

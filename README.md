# Pathfinder ACG Characters

This data is used for the Pathfinder CT ACG app available on [Android](https://play.google.com/store/apps/details?id=com.pathfinder.rotr&hl=en) and [IOS](https://itunes.apple.com/au/app/pathfinder-ct-acg/id922422511?mt=8). It has been created with the data found on the [paizo pdf character sheets]( http://paizo.com/products/btpy914x/discuss%26page%3D2%3FCommunity-Use-Package-Pathfinder-Adventure-Card-Game-Character-Sheets)

## What has been done
**Rise of the Runelords**  

- [x] Deck List
- [ ] Tup Promotional Character
- [x] All Rise of the Runelords Base Set Characters
- [x] All Rise of the Runelords Add-On Characters

**Skull & Shackles**

- [x] Deck List
- [ ] Fleet Card (Not Doing yet: Requires Unique Entry)
- [x] Ranzak Promotional Character
- [x] All Skull & Shackles Base Set Characters
- [x] All Skull & Shackles Add-On Characters

**Wrath of the Righteous**

- [x] Deck List
- [ ] Champions of Mendev Card (Not Doing yet)
- [ ] Redemption Card (Not Doing yet: Requires Unique Entry)
- [x] Ekkie Promotional Character
- [x] All Wrath of the Righteous Base Set Characters
- [x] All Wrath of the Righteous Add-On Characters

**Class Decks**  
- [x] All Alchemist Characters
- [x] All Barbarian Characters
- [x] All Bard Characters
- [x] All Cleric Characters
- [x] All Druid Characters
- [x] All Fighter Characters
- [x] All Goblins Burn! Characters
- [x] All Goblins Fight! Characters
- [x] All Gunslinger Characters
- [x] All Inquisitor Characters
- [x] All Monk Characters
- [x] All Oracle Characters
- [x] All Paladin Characters
- [x] All Ranger Characters
- [x] All Rogue Characters
- [ ] All Sorcerer Characters
- [x] All Witch Characters
- [ ] All Wizard Characters

## Naming Conventions

**Base Games and their Expansions** use an acronym of the game name followed by the data. The data for the base game and its expansions are all entered and are split between characters and cards.

As an example for the Rise Of The Runelords  
rotr-characters.json  
rotr-cards.json  

**Class Decks** are written with cd- followed by the full name of the Deck name then finished with -characters. For now the cards are also entered into the characters json file.

As an example for Bards Class deck  
cd-bard-characters.json  

## Json Data structure

### Core Data Structure
For any json data file there needs to be the following keys in the file.

**Base Game** data Structure  
characters.json
```
{
    "characters": {
        "character-name": {
        }
    }
}
```
cards.json
```
{
    "cards": [
        {
            "name": "Card Name",
            "expansion": "Number/Name of Expansion"
        }
    ]
}
```

**Class Deck** data Structure

```
{
    "characters": {
        "character-name": {
        }
    }
    "cards": [
        {
            "name": "Card Name",
            "expansion": "Number/Name of Expansion"
        }
    ]
}
```
### Character Data Structure
A sample is provided below of a character. Here is a breakdown of some things that may not make sense.

**Numbers and Key Names**

- `diceNo` \- The ID of the Dice to be used as base (list of ids below)
- `modAmt` \- Amount of modifiers to show (If a strength allows up to +3 on the character sheet put 3)
- For hand size the `desc` key is the starting hand size amount
- `startAmt` \- The starting amount value
- `basic` is for the entry of the default character before a role is chosen

**Dice List**  
The list of dice, currently found in Base Character json files. This will be moved to a new file eventually. 

Note: First ID starts at 0 (so for a d6 the diceNo value would be 1)
```
{	
	"dice": [
    	"d4",
    	"d6",
    	"d8",
    	"d10",
        "d12"
    ]
}
```
**Proficieny Checkboxes**  
These are the checkboxes used to display what the character is proficient with. Please make sure with each checkbox you increment the id number. (`profbox1` is the first checkbox and `profbox2` is the second)

If the character is proficient on a character by default add `checked disabled=\"disabled\"` this will check the box and prevent the user from unchecking it.

Please make sure the `id=\"profbox1\"` and `for=\"profbox1\"` match and are exactly the same for the prestige/role classes. This effects the display on the app and can be confusing if a user selects a role and the checkboxes change.
```
<input id=\"profbox1\" type=\"checkbox\" checked disabled=\"disabled\"/><label for=\"profbox1\">Light Armors</label>
```
**Power Checkboxes**
These are the checkboxes displayed in the power section. Please make sure with each checkbox you increment the id number. ( so `powbox1` is the first checkbox and `powbox1` is the next checkbox added.

Please make sure the `id=\"powbox1\"` and `for=\"powbox1\"` match and are exactly the same for the prestige/role classes. This effects the display on the app and can be confusing if a user selects a role. New power checkboxes after a role is chosen may appear before the original checkboxes in power descriptions.
```
<input id=\"powbox1\" type=\"checkbox\" /><label for=\"powbox1\"></label>
```
**Sample Character Entry**
```
{  
   "amiri":{  
      "name":"Amiri",
      "class":"Female Human Barbarian",
      "description":"Amiri is a fierce tribal warrior from the rugged clans of the north. She claimed her oversized bastard sword as a trophy after single-handedly wiping out a band of frost giants. When she returned to her people, she discovered her raid had been meant to be a suicide mission—a punishment for consistently one-upping her tribe’s male warriors in battle. In a rage, she slaughtered her traitorous comrades, then forsook her homeland to make her own place in the world.",
      "favcard":"Weapon",
      "skills":[  
         {  
            "name":"strength",
            "diceNo":5,
            "modAmt":4
         },
         {  
            "name":"dexterity",
            "diceNo":2,
            "modAmt":3
         },
         {  
            "name":"constitution",
            "diceNo":3,
            "modAmt":4,
            "bonus":[  
               {  
                  "name":"Fortitude: Constitution +2"
               }
            ]
         },
         {  
            "name":"intelligence",
            "diceNo":1,
            "modAmt":1
         },
         {  
            "name":"wisdom",
            "diceNo":2,
            "modAmt":1,
            "bonus":[  
               {  
                  "name":"Survival: Wisdom +2"
               }
            ]
         },
         {  
            "name":"charisma",
            "diceNo":2,
            "modAmt":2
         }
      ],
      "powers":{  
         "basic":[  
            {  
               "name":"Hand Size",
               "desc":4,
               "modAmt":1
            },
            {  
               "name":"Proficient",
               "desc":[  
                  "<input id=\"profbox1\" type=\"checkbox\" checked disabled=\"disabled\"/><label for=\"profbox1\">Light Armors</label>",
                  "<input id=\"profbox2\" type=\"checkbox\"/><label for=\"profbox2\">Heavy Armors</label>",
                  "<input id=\"profbox3\" type=\"checkbox\" checked disabled=\"disabled\"/><label for=\"profbox3\">Weapons</label>"
               ]
            },
            {  
               "name":"",
               "desc":"You may bury a card to add 1d10 to your Strength or Constitution check, or to your check to defeat a barrier that has the Lock, Obstacle, or Trap trait. (<input id=\"powbox1\" type=\"checkbox\" /><label for=\"powbox1\"></label>Then you may draw a card.) If it is your exploration, but it is not the first exploration of your turn, add an additional 1d6."
            },
            {  
               "name":"",
               "desc":"At the end of your turn (<input id=\"powbox2\" type=\"checkbox\" /><label for=\"powbox2\"></label>or when your location closes), you may move."
            }
         ],
         "unstoppable force":[  
            {  
               "name":"Hand Size",
               "desc":4,
               "modAmt":1
            },
            {  
               "name":"Proficient",
               "desc":[  
                  "<input id=\"profbox1\" type=\"checkbox\" checked disabled=\"disabled\"/><label for=\"profbox1\">Light Armors</label>",
                  "<input id=\"profbox2\" type=\"checkbox\"/><label for=\"profbox2\">Heavy Armors</label>",
                  "<input id=\"profbox3\" type=\"checkbox\" checked disabled=\"disabled\"/><label for=\"profbox3\">Weapons</label>"
               ]
            },
            {  
               "name":"",
               "desc":"You may bury a card to add 1d10 (<input id=\"powbox3\" type=\"checkbox\" /><label for=\"powbox3\"></label>+1) (<input id=\"powbox4\" type=\"checkbox\" /><label for=\"powbox4\"></label>+2) to your Strength or Constitution check, or to your check to defeat a barrier that has the Lock, Obstacle, or Trap trait. (<input id=\"powbox1\" type=\"checkbox\" /><label for=\"powbox1\"></label>Then you may draw a card.) If it is your exploration, but it is not the first exploration of your turn, add an additional 1d6 (<input id=\"powbox5\" type=\"checkbox\" /><label for=\"powbox5\"></label>1d8)."
            },
            {  
               "name":"",
               "desc":"At the end of your turn (<input id=\"powbox2\" type=\"checkbox\" /><label for=\"powbox2\"></label>or when your location closes), you may move. (<input id=\"powbox6\" type=\"checkbox\" /><label for=\"powbox6\"></label>If you do, you may then examine the top card of your location deck.)"
            },
            {  
               "name":"",
               "desc":"<input id=\"powbox7\" type=\"checkbox\" /><label for=\"powbox7\"></label>When you defeat a barrier, you may examine the top card (<input id=\"powbox8\" type=\"checkbox\" /><label for=\"powbox8\"></label>or top 3 cards) of your location deck. You may put any examined boons on the bottom of the location deck. (<input id=\"powbox9\" type=\"checkbox\" /><label for=\"powbox9\"></label>Then you may explore your location.)"
            },
            {  
               "name":"",
               "desc":"<input id=\"powbox10\" type=\"checkbox\" /><label for=\"powbox10\"></label>When you acquire a boon on your turn, you may immediately recharge it to explore your location."
            }
         ],
         "immovable object":[  
            {  
               "name":"Hand Size",
               "desc":4,
               "modAmt":2
            },
            {  
               "name":"Proficient",
               "desc":[  
                  "<input id=\"profbox1\" type=\"checkbox\" checked disabled=\"disabled\"/><label for=\"profbox1\">Light Armors</label>",
                  "<input id=\"profbox2\" type=\"checkbox\"/><label for=\"profbox2\">Heavy Armors</label>",
                  "<input id=\"profbox3\" type=\"checkbox\" checked disabled=\"disabled\"/><label for=\"profbox3\">Weapons</label>"
               ]
            },
            {  
               "name":"",
               "desc":"You may bury a card to add 1d10 to your Strength or Constitution check, or to your check to defeat a barrier that has the Lock, Obstacle, or Trap trait. (<input id=\"powbox1\" type=\"checkbox\" /><label for=\"powbox1\"></label>Then you may draw a card.) If it is your exploration, but it is not the first exploration of your turn, add an additional 1d6."
            },
            {  
               "name":"",
               "desc":"At the end of your turn (<input id=\"powbox2\" type=\"checkbox\" /><label for=\"powbox2\"></label>or when your location closes), you may move (<input id=\"powbox3\" type=\"checkbox\" /><label for=\"powbox3\"></label>or you may recharge a card)."
            },
            {  
               "name":"",
               "desc":"<input id=\"powbox4\" type=\"checkbox\" /><label for=\"powbox4\"></label>When you would be moved, you may choose not to move."
            },
            {  
               "name":"",
               "desc":"<input id=\"powbox5\" type=\"checkbox\" /><label for=\"powbox5\"></label>Add 1d6 to your check to close a location (<input id=\"powbox6\" type=\"checkbox\" /><label for=\"powbox6\"></label>or your check when it is not your turn.)"
            },
            {  
               "name":"",
               "desc":"<input id=\"powbox7\" type=\"checkbox\" /><label for=\"powbox7\"></label>When you acquire a boon, you may recharge it to recharge a random card from your discard pile (<input id=\"powbox8\" type=\"checkbox\" /><label for=\"powbox8\"></label>or draw a card)."
            },
            {  
               "name":"",
               "desc":"<input id=\"powbox9\" type=\"checkbox\" /><label for=\"powbox9\"></label>When a bane deals damage to you before you act, reduce that damage by 3."
            }
         ]
      },
      "cardslist":[  
         {  
            "name":"weapon",
            "startAmt":5,
            "modAmt":3
         },
         {  
            "name":"spell",
            "startAmt":0,
            "modAmt":0
         },
         {  
            "name":"armor",
            "startAmt":2,
            "modAmt":2
         },
         {  
            "name":"item",
            "startAmt":3,
            "modAmt":2
         },
         {  
            "name":"ally",
            "startAmt":2,
            "modAmt":1
         },
         {  
            "name":"blessing",
            "startAmt":3,
            "modAmt":2
         }
      ]
   }
}
```

## Disclaimer:
This data uses trademarks and/or copyrights owned by Paizo Inc., which are used under Paizo's Community Use Policy. We are expressly prohibited from charging you to use or access this content. This data is not published, endorsed, or specifically approved by Paizo Inc. For more information about Paizo's Community Use Policy, please visit paizo.com/communityuse. For more information about Paizo Inc. and Paizo products, please visit paizo.com.

===============================================================================
22nd of October 2020 - Snufkin Custom Zombies A19 - Stable) and back compatible
===============================================================================

Here are a few changes which restore functionality of the A18 build by replacing old values with their latest equivelant where possible and tweaking settings to offer greater stability.

In order of finding them in the console as warnings or game breakers.
-------------------------------
1. Juggernaut Zombie Issue (x2)
-------------------------------
- entityclasses.xml
entity_class name="Zombie_Template"

Changed the following property to a comment for the time being as this is causing the Juggernaut Zombie to sink below the ground surface by one block and cause a looping 'NullReferenceException'

<!--property name="AvatarController" value="AvatarZombieUMAController" /-->

Based on forum posts, this appears to be an area of contention as this property appears to have been removed from the game. The Juggernaut continues to function with it removed.

- items.xml
item name="JuggernautProjectile"

Changed the following property to a comment for the time being as this can cause potential issues when a player is being attacked while inside a building in a confined space as the Juggernaut is on the outside. It can lead to debris passing through solid walls. The explosion particle has changed from vehicle debris to the standard rocket blast.

<!--property name="Explosion.ParticleIndex" value="4"/-->
<property name="Explosion.ParticleIndex" value="5"/>
-----------------------------
2. Scorcher Zombie Issue (x2)
-----------------------------
- entityclasses.xml
entity_class name="zombieScorcher"

Changed the following property to a comment and updated it to the new property to avoid looping 'NullReferenceException'

<!--property name="Mesh" value="Zombies/zombieStandardDemolitionRagdoll"/-->
<property name="Mesh" value="#Entities/Zombies?Zombies/zombieStandardDemolitionRagdoll.prefab"/>

This is identical beyond the change in formatting.

- items.xml
name="ammoProjectileScorcher"

Changed the following property to a comment and updated it to an alternative particle effect to avoid looping audio at the point of origin when the first instance of a projectile was triggered.

<!--property name="Meshfile" value="particleeffects/p_onFire"/-->
<property name="Meshfile" value="particleeffects/p_fire_small"/>
-------------------------------------
3. Buff Health Issue - ParasiteAttack
-------------------------------------
- buffs.xml
buff name="ParasiteAttack"

Crude edit but changed the following property to a comment for the time being as this appears to be causing a buffs.xml failure and the file will not load.

<!--passive_effect name="HealthMaxModifierOT" operation="base_subtract" value="1"/-->

These properties had also been removed from the original buffs.xml file and no longer appear to be part of the game and this just updates the mod to be identical.
------------------------
4. Zombie Template Issue
------------------------
- entityclasses.xml
entity_class name="Zombie_Template"

Changed the following property to a comment and updated it to the new property to avoid looping 'NullReferenceException'

<!--property name="Mesh" value="Zombies/zombie01Ragdoll" /-->
<property name="Mesh" value="#Entities/Zombies?Zombies/zombie01Ragdoll.prefab"/>

This is identical beyond the change in formatting.
--------------------
5. Geist Issues (x2)
--------------------
- entityclasses.xml
entity_class name="zombieGeist"

Changed typo from Geits to Geist and associated items.xml partners. Purely cosmetic as they all associated under the same typo anyway.

- items.xml
name="ammoProjectileGeist"

Changed the following property to a comment and updated it to an alternative particle effect to avoid looping audio at the point of origin when the first instance of a projectile was triggered.

<!--property name="Meshfile" value="particleeffects/p_electric_shock"/-->
<property name="Meshfile" value="particleeffects/p_electric_shock_small"/>
--------------------------------------------------------
6. Archon Issues (x3) (Special Overlay without Archtype)
--------------------------------------------------------
- entityclasses.xml
entity_class name="ZombieArchon"

Changed the following property to a comment and updated it to the new property to avoid looping

NullReferenceException: Object reference not set to an instance of an object
  at EntityAlive.Update () [0x00134] in <b96846cfb0544c2da3579e57837d9053>:0
 
(Filename: <b96846cfb0544c2da3579e57837d9053> Line: 0)

<!--property name="ReplaceMaterial1" value="entities/zombies/materials/rad_eye"/-->
<property name="ReplaceMaterial1" value="#Entities/Zombies?Zombies/Materials/rad_eye.mat"/>

This is identical beyond the change in formatting.

- items.xml
name="ammoProjectileArchon"

Changed the following property to a comment and updated it to an alternative particle effect to avoid mesh warnings when the projectile is active.

<!--property name="Meshfile" value="particleeffects/p_onFire"/-->
<property name="Meshfile" value="particleeffects/p_fire_small"/>

- items.xml
<item name="meleeHandArchon">

Melee settings were tweaked with the following properties as the close proximity melee attacks were inconsistent. This change brings Archon more in line with Geist.

<property name="Range" value="1.75"/>
---------------------------------------------------
7. Banshee Issue (Special Overlay without Archtype)
---------------------------------------------------
- entityclasses.xml
entity_class name="zombieBanshee"

Changed the following property to a comment and updated it to the new property to avoid looping 'NullReferenceException'

<!--property name="Mesh" value="Zombies/zombieStandardScreamerRagdoll"/-->
<property name="Mesh" value="#Entities/Zombies?Zombies/zombieStandardScreamerRagdoll.prefab"/>

This is identical beyond the change in formatting.
---------------
8. Bomber Issue
---------------
- items.xml
item name="BomberProjectile"

Changed the following property to a comment for the time being as this can cause potential issues when a player is being attacked while inside a building in a confined space as the Bomber is on the outside. It can lead to debris passing through solid walls. The explosion particle has changed from vehicle debris to the standard rocket blast.

<!--property name="Explosion.ParticleIndex" value="4"/-->
<property name="Explosion.ParticleIndex" value="6"/>
===============================================================================
Summary on testing so far - Able to use without crashing or locking up YES / NO
===============================================================================
1. Archon - YES / No warnings after changing particle effects on projectile. 'The boss is here',

2. Banshee - YES / No warnings at all so far. Clear cut.

3. Scorcher - YES / No warnings or audio issues after changing particle effects on projectile. 'Toasty'.

4. Bomber - YES / No warnings at all so far. Blastastic.

5. Cowhead - YES / No warnings at all so far. Mooooover and a shaker.

6. Geist - YES / No warnings or audio issues after changing particle effects on projectile. 'A little shocker'.

7. Juggernaut - YES / No warnings after changing particle effects on projectile. I have a 'soft spot' for Juggernaut as he's the first one to be updated.

8. Mantis - YES / No warnings at all so far. Far out.

9. Parasite - YES / No warnings at all so far. 'Suckulent.'

10. Scarecrow - YES / Has an odd death spin animation which remains as a character trait. Pimpking.

11. Undertaker - YES / No warnings at all so far. Bone shakingly good.

12. Wendigo - YES / No warnings at all so far. Flies like the wind.

13. Wrestler - YES / No warnings at all so far. Just wants to be hugged.

14. Siren - YES / Warnings about audio effect but still audible. Wants someone to listen.

15. Psycho - YES / No warnings at all so far. Wants to play tag.

=====
NOTES
=====
A) The Psycho appears to be a character that may have been removed. He was able to spawn without issue and has been added to the group which spawns in the Pine Forest at night: <entitygroup name="ZombiesPineForestNight"> at a slightly higher probability than the Mantis who is also in that group. He looks like a psychotic doctor in his robes waiting for victims to venture into the forest.

He hasn't been added to the Blood Moon spawn group to create a little bit of suspense. Be on the look out for him as he'll be watching you.

B) There is one other character who did not appear in any spawn group. This is a special character who Snufkin originally intended for a Spanish event server. However, this is a very likeable and functional character, and after some testing, is right at home in the desert at night. He is also special because he uses a naming format which is similar to regular zombies and not the custom zombies. If you want to add the Wrestler to your own desert group, or any other group, here is the appropriate command to add to your entitygroups.xml:

<entity name="zombieWrestler" prob="0.01" /> 

Please be careful to note the 'z' is lowercase.

============
INSTALLATION
============
For players and server hosts who have never installed a mod before.
If you've never installed a mod before it is necessary to create a mod folder in the main directory or in an area suggested by your server host if they have modified the installation. Simply make a new folder called Mods (with a capital M to reflect standard nomenclature). If you drag the mod folder directly out of the zipped file it can be placed directly into the Mods folder and the game will look in there as you launch your World. If you allow your unzip function to extract the folder, it may make another unnecessary folder and place the mod inside it. This will not be recognised by the game/server if you place it in the Mods folder like this. Please take it out of the extra folder level. The top layer will be a single folder and in the second layer you will see a ModInfo.xml file with or without additional folders depending on the mod. This will become elementary once you've launched a few mods.

- If you want Snufkin's Custom Zombies to spawn during a Blood Moon then there is nothing to change unless you want to tweak the frequency and probability (entitygroups.xml in the Config folder).

- If you don't want Snufkin's Custom Zombies to spawn during a Blood Moon then make a backup of your entitygroups.xml file and replace it with the entitygroups_nobloodmoon.xml file in the top folder. Naturally, that needs to be renamed to entitygroups.xml. 

Does this Mod need to be installed in the server/client host? = YES
Do players also need to install this Mod? = NO

The magic of this mod is that is only needs to be installed in the server/person who has launched the main environment that others join. It is a technical work of art. Enjoy.

=======
CREDITS
=======
Apart from Snufkin who created this mod, there are so many names to mention because it was a real community effort from modders and server administrators. You can see the history and contributors in the forum thread at 7daystodie.com. Advice for things like Archon melee damage and appropriate effects alternatives were golden.

https://community.7daystodie.com/topic/17992-snukfins-server-side-zsombies/
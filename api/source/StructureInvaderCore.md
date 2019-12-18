# StructureInvaderCore

<img src="img/invaderCore.png" alt="" align="right" />

This NPC structure is a control center of NPC Strongholds, and also rules all invaders in the sector. It spawns NPC defenders of the stronghold, refill towers, repairs structures. 
While it's alive, it will spawn invaders in all rooms in the same sector. It also contains some valuable resources inside, which you can loot from its ruin if you destroy the structure.

An Invader Core has two lifetime stages: deploy stage and active stage. When it appears in a random room in the sector, it has `ticksToDeploy` property,
public ramparts around it, and doesn't perform any actions. While in this stage it's invulnerable to attacks (has `EFFECT_INVULNERABILITY` enabled). When the `ticksToDeploy` timer is over, it spawns structures around it and starts
spawning creeps, becomes vulnerable, and receives `EFFECT_COLLAPSE_TIMER` which will remove the stronghold when this timer is over.  

An active Invader Core spawns level-0 Invader Cores in neighbor rooms. These lesser Invader Cores are spawned
near the room controller and don't perform any activity except reserving/attacking the controller. One Invader Core can spawn up to 10 lesser Cores
during its lifetime. 

<table class="table gameplay-info">
    <tbody>
    <tr>
        <td><strong>Hits</strong></td>
        <td>100,000</td>
    </tr>
    <tr>
        <td><strong>Deploy time</strong></td>
        <td>5,000 ticks</td>
    </tr>
    <tr>
        <td><strong>Active time</strong></td>
        <td>80,000 ticks with 10% random variation</td>
    </tr>
    <tr>
        <td><strong>Lesser cores spawn interval</strong></td>
        <td>
            <b>Stronghold level 1</b>: 4000 ticks<br>
            <b>Stronghold level 2</b>: 3500 ticks<br>
            <b>Stronghold level 3</b>: 3000 ticks<br>
            <b>Stronghold level 4</b>: 2500 ticks<br>
            <b>Stronghold level 5</b>: 2000 ticks<br>
        </td>
    </tr>
    
    
    </tbody>
</table>

{% page inherited/OwnedStructure.md %}


{% api_property level 'number' %}
                                                                
The level of the stronghold. The amount and quality of the loot depends on the level.

{% api_property ticksToDeploy 'number' %}
                                                                                                                
Shows the timer for a ot yet deployed stronghold, undefined otherwise. 

# City Simulator rules

Service is new City Simulator. The city is a living creature: it born, it grows, it dies. This simulator is very simple one: there are city inhabitants that need food and dwelling, but they could produce resources or build houses. If they don’t have enough food or place to live, people leave the City. In this simple simulation, one round is one day. Only 3 actions are available in one day. At the end of each day Simulator update state of the City(amount of people, wood, food, etc.)
You start the simulation with:
- 10 inhabitants,
- 3pcs of woods,
- 20 pcs of  food
- 5 houses

## Goal
Have as many inhabitants as possible in a one year (365 days).

## Entities
### City
Have as many inhabitants as possible in a one year (365 days).
The main object in a simulation. Each time user run simulator, a new city created. The city includes all of the other entities as its’ parameters. Let's imagine, that by default each city has a storehouse, where you can find all resources that currently available in the City.

### Person(People)
The city inhabitant. You have info only about people who live in a current city. Each person needs at least 1 unit of food. People could work to produce different assets: produce wood, produce food, build a house. A person could be in two modes: ‘busy’ and ‘free’. When a person produces something he switches to the ‘busy’ mode. One person could participate only in one action during one day. When a person has not enough food or don’t have a place to live he leaves the city.

### Wood
Wood is one of the main assets. You can use wood to build a house: you need 3 pieces per house. When the building of house begins, 3 pieces of wood will be removed from your storage. The only source of wood - city inhabitants who produce wood.

### Simulator
The active system that managed the city. During each day it performs set of actions. At the end of each day, it changed city parameters according to actions and rules.

### Food
Food is one of the main assets. You need at least one unit of food per person. If there is not enough food for people they leave the city, so at the end of the day, there will be at least one unit food per person. The only source of food - city inhabitants who produce food. At the end of the day, people eat all the food they can. An amount of food corresponding to amount of people will be removed from storage at the end of the day.

### House
People not only need food but also a place to live in. Two people at maximum could live in one house. This mean than one house has two rooms to live in. If there is free space to live then new inhabitants appear in the city next day: one person per one available room.

## Actions
#### Produce food
This action adds 1.5 food units/person to the city storage.

#### Produce wood
This action adds 1 wood unit/person to the city storage.

#### Build a house
This action builds 1 house per 2 people involved in construction.

## Rules
- The day starts with adding new assets that were produced on the previous day.
- When day starts, new people arrive at the city
- When all new people and resources added, then simulator applies actions.
- When all actions are applied, then the day is finished.
- At the end of the day, all used resources removed from city storage and people leave the city if they don’t have enough food or place to live.
- Simulation stops after 365 days
- Actions are chosen based on strategy, provided by the user. Nobody allowed to change strategy during simulation. The user should provide strategy before the simulation began.
- The strategy is a function that returns set of actions based on current City state.


# Sugarscape Constant Growback model with Traders

## Summary

This is Epstein & Axtell's Sugarscape model with Traders, a detailed description is in Chapter four of
*Growing Artificial Societies: Social Science from the Bottom Up.* (1996). The code is broadly broken into sections of
resource classes, trader class, model class and then data analysis. 

### To Run

Any notebook can be run by pressing the Google Colab button in its respective session or downloading and running on your
local machine but requires [Jupyter]([https://www.codecademy.com/article/setting-up-jupyter-notebook)  


### The Model: 

The model class serves as a manager that instantiates the agents, landscape, scheduler and datacollector, and manages
the interactions and sequencing of the agents.  

### The Agents: 

- **Sugar**:  Sugar agents grow back at one unit per time step and can be harvested and traded by the trader agents. Sugar
is unequally distributed across the landscape with sugar hills in the upper left and lower right of the space.
- **Spice**: Spice agents grow back at one unit per time step and can be harvested and traded by the trader agents. Spice
is unequally distributed across the landscape with spice hills in the upper right and lower left of the space.
- **Traders**: Trader agents have the following attributes: (1) metabolism for sugar, (2) metabolism for spice, (3) vision,
  (4) initial sugar endowment and (5) initial spice endowment. The traverse the landscape harvesting sugar and spice and 
trading with other agents. If they run out of sugar or spice then they are removed from the model. 

The trader agents traverse the landscape according to rule **M**:
- Look out as far as vision permits in the four principal lattice directions and identify the unoccupied site(s).
- Considering only unoccupied sites find the nearest position that produces the most welfare using the Cobb-Douglas function.
- Move to the new position
- Collect all the resources (sugar and spice) at that location
(Epstein and Axtell, 1996, p. 99)

The traders trade according to rule **T**: 
- Agents and potential trade partner compute their marginal rates of substitution (MRS), if they are equal *end*.
- Exchange resources, with spice flowing from the agent with the higher MRS to the agent with the lower MRS and sugar 
flowing the opposite direction.
- The price (p) is calculated by taking the geometric mean of the agents' MRS.
- If p > 1 then p units of spice are traded for 1 unit of sugar; if p < 1 then 1/p units of sugar for 1 unit of spice
- The trade occurs if it will (a) make both agent better off (increases MRS) and (b) does not cause the agents' MRS to 
cross over one another otherwise *end*.
- This process then repeats until an *end* condition is met. 
(Epstein and Axtell, 1996, p. 105)

The model demonstrates several Mesa concepts and features:
 - MultiGrid
 - Multiple agent types (traders, sugar, spice)
 - Dynamically removing agents from the grid and schedule when they die
 - Data Collection at the model and agent level
 - Batchrunner (i.e. parameter sweeps)

### Additional Resources

This code generally matches the code in the [Mesa-Example repository](https://github.com/projectmesa/mesa-examples) in the
sugarscape_g1mt folder.  

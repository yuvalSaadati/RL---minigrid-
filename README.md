# Reinforcements Learning - solving minigrid environment

## Analyzing the Environment

The environments in our project are characterized as **Markov Decision Processes (MDP)** due to their adherence to the fundamental components of an MDP framework: state representation, action space, transition probabilities, rewards, and policy formulation.

### Episodic Nature

The environment exhibits an episodic structure, where each task is defined by clear objectives that the agent must accomplish. For instance, in environments featuring a key, the agent's objective is to locate and collect the key, use it to unlock a door, and finally navigate to a specified goal position. Conversely, in an empty environment, the sole goal is to reach a predefined goal state. Episodes commence with the agent in an initial state and conclude upon successful attainment of the goal state.

The episodic design enables reinforcement learning agents to iteratively learn and adapt based on the outcomes of completed episodes. By interacting with the environment across multiple episodes, agents can:

- Learn optimal strategies for key collection, obstacle navigation, and goal achievement.
- Adjust their policies (e.g., action-selection strategies) in response to rewards and penalties accrued during episodes.
- Explore various approaches and refine behavior through trial and error over time.

### Discrete Actions and States

Actions within our environments are discrete, tailored to the specific task requirements:

- **Empty Environment**: Actions include moving upwards, downwards, or forwards.
- **Environment with Key**: Actions expand to include movement and additional functionalities like picking up items and toggling objects.

States are also discrete and contain pertinent information specific to each environment. Our environments are fully observable, meaning agents have complete visibility of the entire environment grid at any given moment.

## State Representation and Environment Dynamics

The agent's position and direction are critical components of the state representation, similar to the considerations in the empty environment. From each unique position and direction, the agent must select the optimal action based on its current state. Additionally, the inclusion of door and key positions in the state is essential because these positions are randomized in each environment run, influencing the agent's decisions.

For example:
- If the door is closed, the agent may use a toggle action when facing the door directly.
- Conversely, if the door is open, the agent prioritizes moving forward or to the right over using the toggle action.
- Repeatedly opening and closing the door for additional rewards incurs a penalty.
- Once the door has been opened, the agent avoids moving left or using the toggle action.

To standardize training and evaluation, fixed positions for the key and door are established to evaluate optimal algorithms and hyperparameters. During training, door and key positions are set in each epoch to ensure consistent learning across all possible configurations. Testing is conducted using random key and door positions.

## Reward Shaping

### Left Action:
- Penalty of -20 if the door is opening; otherwise, -5. The left action is rarely chosen by the agent.

### Right Action:
- 10 points if the agent faces an open door directly.
- 0 points if the door is open but the agent isn't in front of it.
- -1 point otherwise.

### Forward Action:
- Severe penalty of -100 points if a wall blocks the agent's path.
- 5 points if the agent faces an open door.
- 2 points otherwise. The forward action yields the highest reward in challenging scenarios due to its frequent necessity.

### Toggle Action:
- 100 points if the agent carries the key and the door is open.
- -1 point otherwise.

### Pickup Action:
- 100 points for successfully picking up the key.
- -100 points otherwise.

These reward dynamics shape the agent's learning process and strategy in the environment, emphasizing optimal decision-making and goal achievement.

---

## Running the Project

## Setting Up Environment Parameters

To get started with the project, follow these steps:

1. Clone this repository to your local machine:

   ```bash
   git clone [https://github.com/yourusername/your-repository.git](https://github.com/yuvalSaadati/RL---minigrid-.git)
   
### Training the Agent

To train the agent with the best hyperparameters:

1. Run the `checkingTheBestHyperparameter.py` script, specifying the desired algorithm.
2. Follow the instructions in the script comments to execute the training process.

### Testing and Evaluation

To test the trained agent and evaluate performance:

1. Load the saved Q-table from `Q_table.json` using the `loadingQTable` function.
2. Run the `avgNumOfSteps` function to calculate the average number of steps required to complete the task.



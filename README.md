# Reinforcements Learning - solving minigrid environment

# Reinforcement Learning Project

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

---

## Running the Project

### Setting Up Environment Parameters

1. Clone this repository to your local machine.
2. Install the necessary dependencies by running `pip install -r requirements.txt`.
3. Open the project directory in your preferred IDE or text editor.

### Training the Agent

To train the agent with the best hyperparameters:

1. Navigate to the `src` directory.
2. Run the `checkingTheBestHyperparameter.py` script, specifying the desired algorithm.
3. Follow the instructions in the script comments to execute the training process.

### Testing and Evaluation

To test the trained agent and evaluate performance:

1. Load the saved Q-table from `Q_table.json` using the `loadingQTable` function.
2. Run the `avgNumOfSteps` function to calculate the average number of steps required to complete the task.

---

Feel free to incorporate this content into your `README.md` file on GitHub. You can enhance the formatting and details further based on your project's specific requirements and context.

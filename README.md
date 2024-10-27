# Reinforcement Learning Project

## Overview
This project implements reinforcement learning agents to manage and optimize power flow in electrical networks using the Grid2Op environment, with a focus on maintaining reliable electricity distribution while satisfying N-1 safety conditions. The implementation uses DQN (Deep Q-Network) and Proximal Policy Optimization (PPO) with various improvements to the base model, demonstrating the effects of different observation spaces, action types, and normalization strategies on agent performance in power grid management tasks.


## Project Structure
The main folder contains the notebooks for the DQN and PPO models respectively. Each approach has a sub-folder containing the saved models that are discussed in the report and another sub-folder for the training reward graphs. 

## Model Configurations
Below are the parameter configurations for training the models. But, in the case of just using models that are already trained in order to save time, you can go to the Model Evaluation section.

### Available Models
#### PPO
1. **Baseline Model**
   - Observation type: full
   - Action type: full_discrete
   - Normalization: false

2. **Improvement 1**
   - Observation type: full
   - Action type: box
   - Normalization: false

3. **Improvement 2**
   - Observation type: reduced
   - Action type: box
   - Normalization: true
   - Additional hyperparameters:
     - Learning rate: 0.0009
     - Entropy coefficient: 0.003

#### DQN
1. **Baseline Model**
   - Observation type: part
   - Action type: part_discrete
   - Normalization: false

2. **Improvement 1**
   - Observation type: part
   - Action type: full_discrete
   - Normalization: false

3. **Improvement 2**
   - Observation type: part
   - Action type: full_discrete
   - Normalization: true

## Usage Instructions

### Environment Setup
The modelimplementation builds the environment using three key parameters:
- `obs_type`: Defines the observation space configuration
- `act_type`: Specifies the action space type
- `normalise`: Enables/disables observation normalization

### Model Evaluation
To evaluate the pre-trained models:

1. Load the desired model from the `PPO_saved_models` or `DQN_saved_models` directory
2. Ensure the environment configuration matches the model's training parameters:

```python
# Example for PPO Baseline model
env = Gym2OpEnv(
    obs_type="full",
    act_type="full_discrete",
    normalise=False
)
```

### Results Visualization
Training results for each model configuration can be found in the `PPO_reward_images`  or `DQN_reward_images` directory.

## Important Notes
- When loading a pre-trained model, ensure that the environment configuration exactly matches the original training parameters
- The PPO Improvement 2 model uses specific hyperparameters that must be maintained for proper functionality
- Training visualizations are stored separately for each model variant for comparison purposes

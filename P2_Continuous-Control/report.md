## DDPG Algorithm - Reacher Continuous Control
### Learning Algorithm
The Learning algorithm used in this project is a modification of the implementation used in the [pendulum environment](https://github.com/udacity/deep-reinforcement-learning/tree/master/ddpg-pendulum).

DPG is a policy based learning algorithm in which the agent will learn from the nonprocessed observation spaces without knowing the environment. In contrast to a DQN which learns directly through a gradient method which estimates the weights of the optimal policy. 

DDPG employs an Actor-Critic model in which the Critic model learns the state-value function and uses this to determine how the Actor's policy model should change. The Actor learns from the continuous space without the needs for many data samples since it can rely on the critic to give it feedback on good and bad actions.

However, stability could be a problem with this approach. You can end up with a model that learns well and crashes after a few episodes. To mitigate these, there are several techniques that can be employed like, Gradient Clipping, Soft Target Update, Twin local/ target networks, and Replay Buffer. Reply Buffer is most critical as it allows the DDPG agent to learn offline by gathering experiences collected from the environment agents and sample experiences from a large memory buffer across experiences.

### Model Architecture
The Udacity provided DDPG code in PyTorch was used and adapted for this 20 agent environment.

The algorithm uses two deep neural networks (actor-critic) with the following struture:
- Actor    
    - Hidden: (input, 256)  - ReLU
    - BatchNormalization: (256)
    - Hidden: (256, 256)    - ReLU
    - Output: (256, 4)      - TanH   # action_size=4

- Critic
    - Hidden: (input, 256)              - ReLU
    - BatchNormalization: (256)
    - Hidden: (256 + action_size, 256)  - ReLU
    - Output: (256, 1)                  - Linear


### Hyperparameters
    - BUFFER_SIZE = int(1e6)  # replay buffer size
    - BATCH_SIZE = 128         # minibatch size
    - GAMMA = 0.99            # discount factor
    - TAU = 1e-3              # for soft update of target parameters
    - LR_ACTOR = 1e-4         # learning rate of the actor
    - LR_CRITIC = 1e-4        # learning rate of the critic
    - WEIGHT_DECAY = 0.0      # L2 weight decay

## Results 

The model was able to achieve the goal with 188 episodes.

Episode 1	Score: 0.21	Windowed Average Score: 0.21

Episode 2	Score: 0.10	Windowed Average Score: 0.15

Episode 3	Score: 0.10	Windowed Average Score: 0.14

Episode 4	Score: 0.73	Windowed Average Score: 0.28

Episode 5	Score: 0.00	Windowed Average Score: 0.23

Episode 6	Score: 0.64	Windowed Average Score: 0.30

Episode 7	Score: 0.06	Windowed Average Score: 0.26

Episode 8	Score: 0.55	Windowed Average Score: 0.30

Episode 9	Score: 0.64	Windowed Average Score: 0.34

Episode 10	Score: 0.22	Windowed Average Score: 0.32

Episode 11	Score: 0.92	Windowed Average Score: 0.38

Episode 12	Score: 0.65	Windowed Average Score: 0.40

Episode 13	Score: 0.28	Windowed Average Score: 0.39

Episode 14	Score: 0.25	Windowed Average Score: 0.38

Episode 15	Score: 0.08	Windowed Average Score: 0.36

Episode 16	Score: 0.40	Windowed Average Score: 0.36

Episode 17	Score: 0.26	Windowed Average Score: 0.36

Episode 18	Score: 0.26	Windowed Average Score: 0.35

Episode 19	Score: 1.19	Windowed Average Score: 0.40

Episode 20	Score: 1.03	Windowed Average Score: 0.43

Episode 21	Score: 1.63	Windowed Average Score: 0.49

Episode 22	Score: 0.81	Windowed Average Score: 0.50

Episode 23	Score: 1.41	Windowed Average Score: 0.54

Episode 24	Score: 1.67	Windowed Average Score: 0.59

Episode 25	Score: 2.11	Windowed Average Score: 0.65

Episode 26	Score: 1.86	Windowed Average Score: 0.69

Episode 27	Score: 2.75	Windowed Average Score: 0.77

Episode 28	Score: 1.84	Windowed Average Score: 0.81

Episode 29	Score: 2.40	Windowed Average Score: 0.86

Episode 30	Score: 1.36	Windowed Average Score: 0.88

Episode 31	Score: 2.18	Windowed Average Score: 0.92

Episode 32	Score: 6.38	Windowed Average Score: 1.09

Episode 33	Score: 1.98	Windowed Average Score: 1.12

Episode 34	Score: 2.43	Windowed Average Score: 1.16

Episode 35	Score: 3.85	Windowed Average Score: 1.24

Episode 36	Score: 3.11	Windowed Average Score: 1.29

Episode 37	Score: 2.58	Windowed Average Score: 1.32

Episode 38	Score: 2.61	Windowed Average Score: 1.36

Episode 39	Score: 1.89	Windowed Average Score: 1.37

Episode 40	Score: 4.36	Windowed Average Score: 1.44

Episode 41	Score: 4.56	Windowed Average Score: 1.52

Episode 42	Score: 3.94	Windowed Average Score: 1.58

Episode 43	Score: 5.25	Windowed Average Score: 1.66

Episode 44	Score: 3.17	Windowed Average Score: 1.70

Episode 45	Score: 4.50	Windowed Average Score: 1.76

Episode 46	Score: 1.73	Windowed Average Score: 1.76

Episode 47	Score: 3.98	Windowed Average Score: 1.81

Episode 48	Score: 3.97	Windowed Average Score: 1.85

Episode 49	Score: 4.28	Windowed Average Score: 1.90

Episode 50	Score: 3.95	Windowed Average Score: 1.94

Episode 51	Score: 7.43	Windowed Average Score: 2.05

Episode 52	Score: 4.63	Windowed Average Score: 2.10

Episode 53	Score: 12.28	Windowed Average Score: 2.29

Episode 54	Score: 6.21	Windowed Average Score: 2.36

Episode 55	Score: 6.78	Windowed Average Score: 2.44

Episode 56	Score: 3.87	Windowed Average Score: 2.47

Episode 57	Score: 4.54	Windowed Average Score: 2.51

Episode 58	Score: 11.11	Windowed Average Score: 2.65

Episode 59	Score: 3.68	Windowed Average Score: 2.67

Episode 60	Score: 8.02	Windowed Average Score: 2.76

Episode 61	Score: 8.95	Windowed Average Score: 2.86

Episode 62	Score: 4.88	Windowed Average Score: 2.89

Episode 63	Score: 9.74	Windowed Average Score: 3.00

Episode 64	Score: 2.92	Windowed Average Score: 3.00

Episode 65	Score: 7.05	Windowed Average Score: 3.06

Episode 66	Score: 12.32	Windowed Average Score: 3.20

Episode 67	Score: 10.74	Windowed Average Score: 3.32

Episode 68	Score: 7.27	Windowed Average Score: 3.38

Episode 69	Score: 7.95	Windowed Average Score: 3.44

Episode 70	Score: 8.20	Windowed Average Score: 3.51

Episode 71	Score: 16.31	Windowed Average Score: 3.69

Episode 72	Score: 8.43	Windowed Average Score: 3.76

Episode 73	Score: 10.28	Windowed Average Score: 3.85

Episode 74	Score: 7.22	Windowed Average Score: 3.89

Episode 75	Score: 7.59	Windowed Average Score: 3.94

Episode 76	Score: 9.46	Windowed Average Score: 4.01

Episode 77	Score: 14.16	Windowed Average Score: 4.14

Episode 78	Score: 6.85	Windowed Average Score: 4.18

Episode 79	Score: 9.93	Windowed Average Score: 4.25

Episode 80	Score: 8.87	Windowed Average Score: 4.31

Episode 81	Score: 7.47	Windowed Average Score: 4.35

Episode 82	Score: 8.83	Windowed Average Score: 4.40

Episode 83	Score: 13.74	Windowed Average Score: 4.52

Episode 84	Score: 21.31	Windowed Average Score: 4.72

Episode 85	Score: 5.32	Windowed Average Score: 4.72

Episode 86	Score: 13.20	Windowed Average Score: 4.82

Episode 87	Score: 10.05	Windowed Average Score: 4.88

Episode 88	Score: 9.64	Windowed Average Score: 4.94

Episode 89	Score: 29.49	Windowed Average Score: 5.21

Episode 90	Score: 19.85	Windowed Average Score: 5.37

Episode 91	Score: 15.59	Windowed Average Score: 5.49

Episode 92	Score: 17.41	Windowed Average Score: 5.62

Episode 93	Score: 25.42	Windowed Average Score: 5.83

Episode 94	Score: 11.62	Windowed Average Score: 5.89

Episode 95	Score: 13.58	Windowed Average Score: 5.97

Episode 96	Score: 13.61	Windowed Average Score: 6.05

Episode 97	Score: 15.28	Windowed Average Score: 6.15

Episode 98	Score: 33.26	Windowed Average Score: 6.42

Episode 99	Score: 20.89	Windowed Average Score: 6.57

Episode 100	Score: 23.43	Windowed Average Score: 6.74

Episode 101	Score: 26.52	Windowed Average Score: 7.00

Episode 102	Score: 25.11	Windowed Average Score: 7.25

Episode 103	Score: 7.76	Windowed Average Score: 7.33

Episode 104	Score: 22.96	Windowed Average Score: 7.55

Episode 105	Score: 20.61	Windowed Average Score: 7.76

Episode 106	Score: 24.22	Windowed Average Score: 7.99

Episode 107	Score: 25.57	Windowed Average Score: 8.25

Episode 108	Score: 15.79	Windowed Average Score: 8.40

Episode 109	Score: 24.82	Windowed Average Score: 8.64

Episode 110	Score: 20.65	Windowed Average Score: 8.85

Episode 111	Score: 26.53	Windowed Average Score: 9.10

Episode 112	Score: 30.85	Windowed Average Score: 9.40

Episode 113	Score: 35.20	Windowed Average Score: 9.75

Episode 114	Score: 21.92	Windowed Average Score: 9.97

Episode 115	Score: 30.15	Windowed Average Score: 10.27

Episode 116	Score: 21.03	Windowed Average Score: 10.48

Episode 117	Score: 29.55	Windowed Average Score: 10.77

Episode 118	Score: 30.28	Windowed Average Score: 11.07

Episode 119	Score: 33.43	Windowed Average Score: 11.39

Episode 120	Score: 27.54	Windowed Average Score: 11.66

Episode 121	Score: 28.06	Windowed Average Score: 11.92

Episode 122	Score: 37.79	Windowed Average Score: 12.29

Episode 123	Score: 25.60	Windowed Average Score: 12.53

Episode 124	Score: 28.41	Windowed Average Score: 12.80

Episode 125	Score: 27.04	Windowed Average Score: 13.05

Episode 126	Score: 35.72	Windowed Average Score: 13.39

Episode 127	Score: 27.87	Windowed Average Score: 13.64

Episode 128	Score: 30.97	Windowed Average Score: 13.93

Episode 129	Score: 28.19	Windowed Average Score: 14.19

Episode 130	Score: 24.45	Windowed Average Score: 14.42

Episode 131	Score: 27.40	Windowed Average Score: 14.67

Episode 132	Score: 20.08	Windowed Average Score: 14.81
Episode 133	Score: 36.37	Windowed Average Score: 15.15

Episode 134	Score: 38.23	Windowed Average Score: 15.51

Episode 135	Score: 35.78	Windowed Average Score: 15.83

Episode 136	Score: 34.62	Windowed Average Score: 16.14

Episode 137	Score: 38.00	Windowed Average Score: 16.50

Episode 138	Score: 34.38	Windowed Average Score: 16.82

Episode 139	Score: 35.37	Windowed Average Score: 17.15

Episode 140	Score: 33.03	Windowed Average Score: 17.44

Episode 141	Score: 35.80	Windowed Average Score: 17.75

Episode 142	Score: 39.00	Windowed Average Score: 18.10

Episode 143	Score: 39.28	Windowed Average Score: 18.44

Episode 144	Score: 32.08	Windowed Average Score: 18.73

Episode 145	Score: 36.25	Windowed Average Score: 19.05

Episode 146	Score: 37.97	Windowed Average Score: 19.41

Episode 147	Score: 30.60	Windowed Average Score: 19.68

Episode 148	Score: 39.53	Windowed Average Score: 20.03

Episode 149	Score: 38.07	Windowed Average Score: 20.37

Episode 150	Score: 39.51	Windowed Average Score: 20.73

Episode 151	Score: 27.30	Windowed Average Score: 20.92

Episode 152	Score: 35.77	Windowed Average Score: 21.24

Episode 153	Score: 39.29	Windowed Average Score: 21.51

Episode 154	Score: 32.37	Windowed Average Score: 21.77

Episode 155	Score: 33.59	Windowed Average Score: 22.04

Episode 156	Score: 24.54	Windowed Average Score: 22.24

Episode 157	Score: 31.60	Windowed Average Score: 22.51

Episode 158	Score: 33.21	Windowed Average Score: 22.73

Episode 159	Score: 22.17	Windowed Average Score: 22.92

Episode 160	Score: 34.72	Windowed Average Score: 23.19

Episode 161	Score: 33.72	Windowed Average Score: 23.43

Episode 162	Score: 35.29	Windowed Average Score: 23.74

Episode 163	Score: 32.85	Windowed Average Score: 23.97

Episode 164	Score: 36.02	Windowed Average Score: 24.30

Episode 165	Score: 31.79	Windowed Average Score: 24.55

Episode 166	Score: 33.55	Windowed Average Score: 24.76

Episode 167	Score: 11.05	Windowed Average Score: 24.76

Episode 168	Score: 34.40	Windowed Average Score: 25.03

Episode 169	Score: 39.44	Windowed Average Score: 25.35

Episode 170	Score: 37.60	Windowed Average Score: 25.64

Episode 171	Score: 37.55	Windowed Average Score: 25.86

Episode 172	Score: 38.22	Windowed Average Score: 26.15

Episode 173	Score: 35.19	Windowed Average Score: 26.40

Episode 174	Score: 29.94	Windowed Average Score: 26.63

Episode 175	Score: 36.11	Windowed Average Score: 26.91

Episode 176	Score: 26.83	Windowed Average Score: 27.09

Episode 177	Score: 30.98	Windowed Average Score: 27.26

Episode 178	Score: 28.16	Windowed Average Score: 27.47

Episode 179	Score: 28.02	Windowed Average Score: 27.65

Episode 180	Score: 36.35	Windowed Average Score: 27.93

Episode 181	Score: 37.22	Windowed Average Score: 28.22

Episode 182	Score: 38.55	Windowed Average Score: 28.52

Episode 183	Score: 36.00	Windowed Average Score: 28.74

Episode 184	Score: 34.32	Windowed Average Score: 28.87

Episode 185	Score: 35.69	Windowed Average Score: 29.18

Episode 186	Score: 36.81	Windowed Average Score: 29.41

Episode 187	Score: 39.63	Windowed Average Score: 29.71

Episode 188	Score: 39.48	Windowed Average Score: 30.01

Environment solved in 188 episodes!	tWindowed Average Score: 30.01

![Training](https://github.com/nitink12/DeepReinforcementLearningNanoDegree/blob/master/P2_Continuous-Control/images/training.png)


## future improvements
1. Continue training for a few more iterations
2. Improve the DDPG alogorithm by applying Priority Experience Replay.
3. Solving the Version 2 of the environment with 20 identical agents

[//]: # (Image References)

[image1]: https://user-images.githubusercontent.com/10624937/43851024-320ba930-9aff-11e8-8493-ee547c6af349.gif "Trained Agent"
[image2]: https://user-images.githubusercontent.com/10624937/43851646-d899bf20-9b00-11e8-858c-29b5c2c94ccc.png "Crawler"


# Project 2: Continuous Control

### Introduction

For this project, you will work with the [Reacher](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Learning-Environment-Examples.md#reacher) environment.

![Trained Agent][image1]

In this environment, a double-jointed arm can move to target locations. A reward of +0.1 is provided for each step that the agent's hand is in the goal location. Thus, the goal of your agent is to maintain its position at the target location for as many time steps as possible.

The observation space consists of 33 variables corresponding to position, rotation, velocity, and angular velocities of the arm. Each action is a vector with four numbers, corresponding to torque applicable to two joints. Every entry in the action vector should be a number between -1 and 1.

### Distributed Training

For this project, we will provide you with two separate versions of the Unity environment:
- The first version contains a single agent.
- The second version contains 20 identical agents, each with its own copy of the environment.  

The second version is useful for algorithms like [PPO](https://arxiv.org/pdf/1707.06347.pdf), [A3C](https://arxiv.org/pdf/1602.01783.pdf), and [D4PG](https://openreview.net/pdf?id=SyZipzbCb) that use multiple (non-interacting, parallel) copies of the same agent to distribute the task of gathering experience.  

### Solving the Environment

Note that your project submission need only solve one of the two versions of the environment. 

#### Option 1: Solve the First Version

The task is episodic, and in order to solve the environment,  your agent must get an average score of +30 over 100 consecutive episodes.

#### Option 2: Solve the Second Version

The barrier for solving the second version of the environment is slightly different, to take into account the presence of many agents.  In particular, your agents must get an average score of +30 (over 100 consecutive episodes, and over all agents).  Specifically,
- After each episode, we add up the rewards that each agent received (without discounting), to get a score for each agent.  This yields 20 (potentially different) scores.  We then take the average of these 20 scores. 
- This yields an **average score** for each episode (where the average is over all 20 agents).

The environment is considered solved, when the average (over 100 episodes) of those average scores is at least +30. 

### Getting Started

1. Download the environment from one of the links below.  You need only select the environment that matches your operating system:

    - **_Version 1: One (1) Agent_**
        - Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Linux.zip)
        - Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher.app.zip)
        - Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Windows_x86.zip)
        - Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Windows_x86_64.zip)

    - **_Version 2: Twenty (20) Agents_**
        - Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Linux.zip)
        - Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher.app.zip)
        - Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Windows_x86.zip)
        - Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Windows_x86_64.zip)
    
    (_For Windows users_) Check out [this link](https://support.microsoft.com/en-us/help/827218/how-to-determine-whether-a-computer-is-running-a-32-bit-version-or-64) if you need help with determining if your computer is running a 32-bit version or 64-bit version of the Windows operating system.

    (_For AWS_) If you'd like to train the agent on AWS (and have not [enabled a virtual screen](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md)), then please use [this link](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Linux_NoVis.zip) (version 1) or [this link](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Linux_NoVis.zip) (version 2) to obtain the "headless" version of the environment.  You will **not** be able to watch the agent without enabling a virtual screen, but you will be able to train the agent.  (_To watch the agent, you should follow the instructions to [enable a virtual screen](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md), and then download the environment for the **Linux** operating system above._)
 

### Instructions for setting up environment in AWS

1. First submit a ticket with amazon for a rate limit increase of all P and G instances in the region you will be using. Udacity provided a link for how you can build and configure your own compute instance; However the repository readme says their documentation is out of date and the no longer use it. Provided are 2 links: first the repository/documentation in question, and second the link to the amazon machine image which I am recommending the rate increase to use.
 [repo](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md)
 [AMI aws link](https://aws.amazon.com/marketplace/pp/B077GCH38C)
 
2. Once your request has been approved go to the AWS link above to create the EC2 compute instance you will be using. **Note: before doing this you must create a SSH key pair which can be done in the EC2 console. The Key pair link can be found in the console under Network & Security -> Key Pairs.**

3. after you have created your key and created the EC2 instance we will want to SSH into it. The following links provides you with detailed instructions for doing this with putty as well as mac + openshh. 
[Connecting to Your Linux Instance from Windows Using PuTTY](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/putty.html)
[Connect from Mac or Linux Using an SSH Client](https://docs.aws.amazon.com/quickstarts/latest/vmlaunch/step-2-connect-to-instance.html)

4. Now that you have access to the environment we want to connect to a jupyter notebook. Since we have SSH'ed into the machine we have to perform an extra step to access it via the browser on our loca machine.
- setup a password to access jupyter 
```
(ec2-instance)$ jupyter notebook password
Enter password: 
Verify password: 
[NotebookPasswordApp] Wrote hashed password to /home/ubuntu/.jupyter/jupyter_notebook_config.json
```
- next start the jupyter notebook. **NOTE: we use nohup at the beggining and & at the end to stop the server from being killed if you logout.**
```
(ec2-instance)$ nohup jupyter notebook --no-browser --port=8888
nohup: ignoring input and appending output to 'nohup.out'
```
- finally we create an SSH tunnel connection from the EC2 instance to your local machine.
```
(my-machine)$ ssh -i my-private-key.pem -N -f -L localhost:8888:localhost:8888 user-name@remote-hostname
```


# Report 

### Learning Algorithm

For this Project I used the standard DQN. For network arctitecture, a simple target network was used to prevent the model from chasing "moving target" Q values, and an experience replay that was sampled randomly to further learn from previous action state combinations. The neural networks themselves were rudimentary at best, they are 3 layer fully connected linear layers using rectified linear unit activation functions. For hyperparameters I used the following:

| Name                     |  value                   |
:-------------------------:|:-------------------------:
 Buffer Size               |  1e6
 Batch Size                | 128
 Initial Epsilon           | 1.0
 Minimum Epsilon           | 0.01
 Epsilon Decay             | 1e-6
 max number of episodes    | 2000, actual: ~180
 max timesteps per episode | 1000
 Tau                       | 1e-3
 Gamma                     | 0.95
 actor learning rate       | 1e-4
 critic learning rate      | 1e-3
 network update rate       | every 20 episodes
 number of network updates | 10 updates


I regret using this algorithm because it burned up all of my workspace GPU time, and cost me about a day of compute time on AWS. I knew the oscillations would be attrocious; However, I did not account for the compute time required to train a DQN. I [read](https://medium.com/@parsa_h_m/deep-reinforcement-learning-dqn-double-dqn-dueling-dqn-noisy-dqn-and-dqn-with-prioritized-551f621a9823) that there were far fewer oscillations with the double DQN and the dueling DQN, but they did not as effectively maximize the Q values for which reason I stuck with the DQN. 

###  Plot of Rewards

![](training_episodes.png)

This graph does a great job of illustrating the oscillations I mentioned above and why training the vanilla DQN was so computationally expensive. 

### Ideas for future work

I have a few interests as far as future work goes. First, I would like to try adding adaptive noise to the parameter space as opposed to the action space, I've [](https://openai.com/blog/better-exploration-with-parameter-noise/) that **make smarter** using parameter space noise as opposed to action space noise imporoves model performance and action space exploration. By injecting randomness directly into the parameters of the agent it alters the types of decisions it makes such that they always fully depend on what the agent currently senses. Since this method adds noise to the parameters of the policy, it makes an agent’s exploration consistent across different timesteps, whereas adding noise to the action space leads to more unpredictable exploration which isn’t correlated to anything unique to the agent’s parameters. The second future work I would like to go regarding this problem space is exporing the possibilities of using evolutionary strategies for solving the same problems. This interests me due to the compute resources required to train the reinforcement algorithms, as well as the fact that they are not easily scalable. [This open AI article](https://openai.com/blog/evolution-strategies/) proclaims to have cut down training time of policy based deep RL algorithms by 2 orders of magnitued by using evolutionary strategies and scaling up their computing resources. These evolutionary strategies tout the following No need for backprop, high parallelizability, a smaller set of hyperparameters to optimize, and "structured exploitation".

### (Optional) Challenge: Crawler Environment

After you have successfully completed the project, you might like to solve the more difficult **Crawler** environment.

![Crawler][image2]

In this continuous control environment, the goal is to teach a creature with four legs to walk forward without falling.  

You can read more about this environment in the ML-Agents GitHub [here](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Learning-Environment-Examples.md#crawler).  To solve this harder task, you'll need to download a new Unity environment.  (**Note**: Udacity students should not submit a project with this new environment.)

You need only select the environment that matches your operating system:
- Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Crawler/Crawler_Linux.zip)
- Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Crawler/Crawler.app.zip)
- Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Crawler/Crawler_Windows_x86.zip)
- Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Crawler/Crawler_Windows_x86_64.zip)

Then, place the file in the `p2_continuous-control/` folder in the DRLND GitHub repository, and unzip (or decompress) the file.  Next, open `Crawler.ipynb` and follow the instructions to learn how to use the Python API to control the agent.

(_For AWS_) If you'd like to train the agent on AWS (and have not [enabled a virtual screen](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md)), then please use [this link](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Crawler/Crawler_Linux_NoVis.zip) to obtain the "headless" version of the environment.  You will **not** be able to watch the agent without enabling a virtual screen, but you will be able to train the agent.  (_To watch the agent, you should follow the instructions to [enable a virtual screen](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md), and then download the environment for the **Linux** operating system above._)


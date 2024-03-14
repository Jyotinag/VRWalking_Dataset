# VRWalking_Dataset
![Overview of the Maze Navigation Session](Images/MazeFinal.pdf)
*Figure 1: Overview of the Maze Navigation Session*

We collected the data for our VRWalking dataset while participants navigated virtual mazes via real walking for 15 minutes while concurrently performing multiple cognitive tasks. The purpose of this data collection was to investigate the relationships between cybersickness, working memory, attention, and cognitive load. Figure 1 shows the timeline of the 15 minute session. In the following sections, we provide details of our hypotheses, the virtual environment, the tasks, the study procedure, metrics, and analysis.

### Participants
We utilized 36 of 39 (23 M, 16 F) participants because the 3 removed had incomplete sensor data. The participants were recruited from the local area and had a mean age of 25.67 with a standard deviation of 7.22. The participants came from various demographic backgrounds. Twenty-five of 39 participants said they had previously used VR equipment while 13 had no prior experience of using VR.

### Hypotheses
The primary focus of this data collection was to help determine VR's effects on cybersickness, working memory, physical load, and mental load during multiple cognitive tasks and real walking tasks in a VR maze. Our hypotheses were motivated by effects seen in previous literature, which focused primarily on stationary VR. (see background and related work)
- H1: Participants will have a significant rise in cybersickness levels proportionate to their time in VR.
- H2: Working Memory will decline and physical load, and mental load will increase over time in VR.
%motivate why/how we arrived at the hypotheses
%add some hypotheses about what we think was going to happen with each of the metrics

### Virtual Environment
The virtual environment consisted of a randomly generated maze,  based on a hunt-and-kill algorithm [1] as follows: 1) Build a completely walled maze. 2) Start at the beginning of the previous maze's finish. 3) Hunt in a random direction to find a grid location that has not been visited. 4) Break walls between the platforms until the entire maze has been visited. 
The maze contained high stone walls, stone platforms, a grey sky, and no ceiling. The maze was a 4x4 grid that randomly spawned the trophy, the finish condition that transports the user to the next randomly generated maze (Figure 2 middle), each with a minimum navigation distance of at least half of the maze. This ensures that the user has to explore at minimum half of the maze in order to progress to the next level. Thus, all randomly generated mazes have approximately the same difficulty. The virtual maze occupies 3m x 3m of real space with each platform being about .5m x .5m. 

### Study Tasks
The primary task was navigating mazes for 15 minutes. See figure 2 left for an example of a maze. As described in figure 1, the whole session was divided into one-minute sections where the maze navigation goes on continuously. In each section, for the first 30s the participants navigate the maze and complete tasks, the next 30s the participants continue navigating the maze but instead of going though the attention task they go through a Q\&A session. Each maze contained an average of 4-5 turns and we instructed the user to stay in motion at all times. This task was to be done for the entire duration of 15 minutes unless the participant decided to quit early. We chose 15 minutes as prior literature has shown that most people will have feelings of cybersickness after 10-15 minutes [2].

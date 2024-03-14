# VRWalking_Dataset
![Overview of the Maze Navigation Session](MazeFinal.pdf)
*Figure 1: Overview of the Maze Navigation Session*

We collected the data for our VRWalking dataset while participants navigated virtual mazes via real walking for 15 minutes while concurrently performing multiple cognitive tasks. The purpose of this data collection was to investigate the relationships between cybersickness, working memory, attention, and cognitive load. Figure 1 shows the timeline of the 15 minute session. In the following sections, we provide details of our hypotheses, the virtual environment, the tasks, the study procedure, metrics, and analysis.

### Participants
We utilized 36 of 39 (23 M, 16 F) participants because the 3 removed had incomplete sensor data. The participants were recruited from the local area and had a mean age of 25.67 with a standard deviation of 7.22. The participants came from various demographic backgrounds. Twenty-five of 39 participants said they had previously used VR equipment while 13 had no prior experience of using VR.

### Hypotheses
The primary focus of this data collection was to help determine VR's effects on cybersickness, working memory, physical load, and mental load during multiple cognitive tasks and real walking tasks in a VR maze. Our hypotheses were motivated by effects seen in previous literature, which focused primarily on stationary VR. (see background and related work)
- H1: Participants will have a significant rise in cybersickness levels proportionate to their time in VR.
- H2: Working Memory will decline and physical load, and mental load will increase over time in VR.


### Virtual Environment
The virtual environment consisted of a randomly generated maze,  based on a hunt-and-kill algorithm [1] as follows: 1) Build a completely walled maze. 2) Start at the beginning of the previous maze's finish. 3) Hunt in a random direction to find a grid location that has not been visited. 4) Break walls between the platforms until the entire maze has been visited. 
The maze contained high stone walls, stone platforms, a grey sky, and no ceiling. The maze was a 4x4 grid that randomly spawned the trophy, the finish condition that transports the user to the next randomly generated maze (Figure 2 middle), each with a minimum navigation distance of at least half of the maze. This ensures that the user has to explore at minimum half of the maze in order to progress to the next level. Thus, all randomly generated mazes have approximately the same difficulty. The virtual maze occupies 3m x 3m of real space with each platform being about .5m x .5m. 

### Study Tasks
The primary task was navigating mazes for 15 minutes. See figure 2 left for an example of a maze. As described in figure 1, the whole session was divided into one-minute sections where the maze navigation goes on continuously. In each section, for the first 30s the participants navigate the maze and complete tasks, the next 30s the participants continue navigating the maze but instead of going though the attention task they go through a Q\&A session. Each maze contained an average of 4-5 turns and we instructed the user to stay in motion at all times. This task was to be done for the entire duration of 15 minutes unless the participant decided to quit early. We chose 15 minutes as prior literature has shown that most people will have feelings of cybersickness after 10-15 minutes [2].
### Apparatus
We utilized an HTC-Vive Pro Eye headset to present the virtual maze, boasting a display resolution of 1440 x 1600 per eye and operating at a refresh rate of 90Hz. This headset offered a wide field of view spanning 110 degrees. Audio was delivered through the integrated Vive headphones, and to ensure a seamless VR experience, we configured the HMD with the Vive wireless adapter. Rendering was handled by a computer equipped with the Windows 10 operating system, a 4.35 GHz Intel Core i7 processor, 32 GB DDR3 RAM, and an NVIDIA GeForce RTX 2080 graphics card.

The virtual environment was developed using Unity 3D. Eye-tracking data, including gaze direction and pupil diameter, was captured using the HTC SRanipal SDK and Tobii HTC Vive Devkit. Head tracking was recorded using the SteamVR lighthouse system. To log data efficiently without interrupting the VR simulation, we employed an asynchronous logging module within the Unity software [1].

We utilized the Neulog system to collect heart rate and galvanic skin response data, employing two external modular sensors. Data transmission was facilitated by a Neulog Wi-Fi module for wireless connectivity.

### Procedure

#### Study Introduction
Participants were presented with the informed consent form and provided with an overview of the study activities. They were informed of their right to terminate the study if they felt uncomfortable at any point. Upon signing the consent form, participants completed a background questionnaire comprising initial Simulator Sickness Questionnaire (SSQ), demographic inquiries, and disability-related questions. Subsequently, participants were outfitted with the HTC Vive Pro Eye headset, physiological monitoring equipment, and controllers before proceeding to a tutorial session.

#### Tutorial
Prior to the 15-minute VR session, participants underwent a brief 1-minute virtual tutorial elucidating the tasks they would perform. This tutorial included instructions on operating the handheld controller and responding to the attention task prompts. Participants also received clarity on the questions they would encounter during the maze task through audio instructions delivered via the HMD's headphones. They were tasked with pressing the trigger upon hearing a keyword to familiarize them with the attention task. Additionally, participants navigated their hand to intersect with a 'trophy' object to complete a maze.

#### Maze Navigation
Following the tutorial, participants underwent an eye calibration procedure to ensure accurate interpretation and recording of eye movements. Participants were then presented with the cue word for the attention metric and the first sequence of five randomly generated digits. Upon readiness, participants commenced navigating the maze, with the Q&A session commencing every 30 seconds. During this session, participants responded to Likert scale questions on cybersickness, mental load, and physical load, recited the previously given sequence of five digits, and were presented with a new five-digit number to remember. Maze navigation was performed via real walking, with participants instructed to complete the attention task throughout the session. Upon reaching the end of a maze, participants intersected a maze completion marker with their controller and were teleported to the next maze.

#### Post-experience Questionnaires
Upon completion of the 15-minute session or upon participant request to terminate, participants exited the maze and completed another SSQ and a NASA TLX questionnaire. Participants were compensated with $30 per hour and parking fees at the conclusion of the session.

[1]: https://tinyurl.com/yckknkdw
## Data Collected

We collected the following data for our novel VRWalking dataset:

| Dataset       | Exposure Time    | Eye Tracking | Head Tracking | HR   | GSR  | Locomotion | Cognitive Load | Cybersickness |
|---------------|------------------|--------------|---------------|------|------|------------|----------------|---------------|
| SET\cite{islam2022towards} | 7 Minutes    | Yes          | Yes           | Yes  | Yes  | No         | No             | Yes           |
| **VRWalking** | **15 Minutes**  | **Yes**      | **Yes**       | **Yes** | **Yes** | **Yes**    | **Yes**         | **Yes**       |
| VREED\cite{tabbaa2021vreed} | 1-3 Minutes | Yes          | No            | No   | Yes  | No         | No             | No            |
| GW Dataset\cite{kothari2020gaze} | 5 Minutes | Yes          | Yes           | No   | No   | Yes        | No             | No            |
| EHTask\cite{9664291}       | 150 Seconds | Yes          | Yes           | No   | No   | No         | No             | No            |
| VR.net\cite{wen2024vr}     | 10 Minutes  | Yes          | Yes           | Yes* | No   | Mixed      | No             | Yes           |

'*' represents partially collected

### Attention
During the VR session, participants navigated through the maze while hearing randomly generated words ("Alpha", "Bravo", "Charlie", "Delta", and "Echo") at intervals of 2-3 seconds. Participants were assigned a specific target word at the session's outset and instructed to press a designated button whenever they heard a word that did not match the target. Two performance metrics were derived from this task to evaluate attention\cite{ho2005assessing}:
- **Correct Button Presses**: Represented as a percentile of correctly pressed buttons, denoted as *Attention (Success Rate)*.
- **Reaction Time**: Calculated as the elapsed time between word playback and button press, averaged over one-minute intervals aligned with data collection for FMS, physical load, and mental load.

### Working Memory Load
In addition to the attention task, participants were presented with a sequence of five-digit numbers audibly. During the Q&A session, participants were prompted to recall and repeat the sequence. Working memory load was quantified as the percentile of correctly repeated digits, akin to the digit span test\cite{blackburn1957revised}.

### NASA-TLX
Administered post-navigation task, the NASA-TLX questionnaire assessed workload across six subscales: mental demand, physical demand, temporal demand, performance, effort, and frustration. Each subscale was rated on a scale of 0-100, with higher scores indicating greater workload\cite{hart1988development}.

### Physical Load
Participants rated the physical demand of the task on a scale of 1-10 using a single question from the NASA-TLX, asked once per minute.

### Mental Load
Similar to the Paas scale\cite{sweller2019cognitive}, participants rated the mental demand of the task on a scale of 1-10, asked once per minute.

### Fast Motion Sickness Scale (FMS)
Participants rated their level of cybersickness on a scale of 1-10, asked once per minute\cite{keshavarz2011validating,freiwald2020cybersickness}.

### SSQ
Administered both before and after the VR session, the Simulator Sickness Questionnaire (SSQ) comprised 16 questions, yielding total and subscale scores for nausea, oculomotor symptoms, and disorientation\cite{kennedy1993simulator}.

### Eye Tracking
Utilizing the SRanipal SDK and Tobii eye tracking technology, we captured detailed eye-tracking metrics, including pupil diameter and gaze direction, sampled at 60 Hz.

### Head Tracking
The SteamVR Lighthouse tracking system provided accurate head tracking data, sampled at 60 Hz.

### Physiological Readings
Heart rate (HR) and galvanic skin response (GSR) data were collected using Neulog sensors, sampled at 10 Hz.

### VR Images
Point-of-view video footage of participants within the virtual environment, recorded at a resolution of 1440x1600 and a refresh rate of 90 Hz, was captured for further analysis.


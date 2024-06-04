![An Overview of the Maze Study](Abstract.jpg)
**Figure 1**  
a) Top-down view of a randomly generated virtual maze environment  
b) First-person point of view - a participant grabs the trophy to start another random maze task  
c) Participants physically walked in the real environment to enable virtual environment navigation

## Abstract
Virtual Reality (VR) is quickly establishing itself in various industries, including training, education, medicine, and entertainment, where users are frequently required to carry out multiple complex cognitive and physical activities. For example, consider popular room-scale supported rogue-lite VR games such as Compound, Tea for God, Ancient Dungeon, and In Death, which can require users to concurrently battle enemies, navigate mazes, solve puzzles, and remember quest/mission instructions. At the same time, cybersickness (i.e., motion sickness in VR) and physical and mental fatigue fluctuate. However, the relationship between cognitive activities, physical activities, and familiar feelings of cybersickness is not well understood and thus can be unpredictable for developers.

Researchers have previously provided labeled datasets for predicting cybersickness while users are stationary, but there have been few labeled datasets on cybersickness while users are physically walking. Moreover, it is unclear how walking while cybersick will affect cognitive load, even though room-scale interaction is typical in many VR games. Thus, from 39 participants, we collected head orientation, head position, eye tracking, images, physiological readings from external sensors, and the self-reported cybersickness severity, physical load, and mental load in VR. Throughout the data collection, participants navigated mazes via real walking and performed tasks challenging their attention and working memory.

To demonstrate the dataset's utility, we conducted a case study of training classifiers in which we achieved 95% accuracy for cybersickness severity classification. The noteworthy performance of the straightforward classifiers makes this dataset ideal for future researchers to develop cybersickness detection and reduction models. To better understand the features that helped with classification, we performed SHAP (SHapley Additive exPlanations) analysis, highlighting the importance of eye tracking and physiological measures for cybersickness prediction while walking.

This open dataset can allow future researchers to study the connection between cybersickness and cognitive loads and develop prediction models. This dataset will empower future VR developers to design efficient and effective Virtual Environments by improving cognitive load management and minimizing cybersickness.

## Introduction

Human-computer interaction now has new avenues to explore, thanks to the development of immersive virtual reality technology. From education, healthcare, and industrial training to gaming, these technologies can potentially change several industries[^1][^2][^3]. However, individuals may encounter physiological and psychological difficulties when they immerse themselves in these virtual experiences. In many popular VR experiences, players are required to perform multiple tasks concurrently, some of which are physical and some of which are mental[^4][^5]. For example, consider the popular room-scale VR game Half Life: Alyx, in which players must battle enemies (physical), solve puzzles (mental), and navigate unfamiliar environments (physical and mental). For a developer, finding a balance between mental and physical demands in VR can be a daunting task that currently requires extensive playtesting.

To complicate VR development further, VR devices introduce a unique set of physical and mental hindrances that are arguably less pronounced in traditional gaming. Cybersickness (i.e., also known as Visually Induced Motion Sickness), a syndrome similar to motion sickness but brought on by digital settings, is one such hindrance. The broad use of immersive technologies may be hampered by the discomfort and confusion caused by cybersickness. Unfortunately, there are few comprehensive datasets in the literature that can be used to help predict and combat physical and mental demands on VR users. To address this research gap, this paper provides a novel dataset intended to enable the assessment and prediction of cybersickness, working memory, mental load, physical load, and attention during room-scale VR experiences.

Few prior works have investigated the intersection of cybersickness, cognition, and real walking[^6][^7]. For example, several cybersickness-related works have focused on collecting datasets for cybersickness prediction in VR while users were mostly stationary and did not consider the impact on cognition[^8][^9]. Luong et al.[^10] ran a large lab-in-the-field study with participants who used real-walking to navigate a 20x20 ballroom, but they failed to address the potential impact of cybersickness on cognition. In contrast to the prior work, our approach was to collect cybersickness and cognitive data while participants were physically walking.

Real walking in VR is becoming more commonplace due to off-the-shelf hardware support for room-scale locomotion, wide area navigation, and location-based VR, which can utilize a large amount of physical space[^11]. Suma et al.[^12] pointed out that in scenarios demanding swift and efficient navigation or travel mirroring real-world movements, genuine walking offers benefits over conventional joystick-driven virtual traversal methods. In addition to this, Suma et al. demonstrated dual tasks could serve as valuable indicators for assessing the impact of VR and cybersickness on working memory, attention, and cognitive load. Although many studies have shown that cybersickness is often reported as lower during real walking tasks[^13] compared to stationary tasks, cybersickness can still be present in real walking tasks[^14]. Thus, cybersickness during real walking tasks may still affect user experience, task performance, and potentially cognitive load.

As a case study to demonstrate the utility of the dataset, we have evaluated the accuracy of several deep-learning models in classifying cybersickness as most of the currently available datasets are focused on multimodal cybersickness prediction[^8]. Additionally, we have conducted SHAP (SHapley Additive exPlanations) explainable-AI analysis to identify the primary features utilized by the deep learning models. In short, our contribution includes:

- **VRWalking** - A novel open dataset including VR images, eye-tracking, head-tracking, Heart Rate (HR), Galvanic Skin Response (GSR), cybersickness, mental load, physical load, working memory, and attention for participants navigating a maze via real walking inside a VE. See figure \ref{fig:teaser}.
- **Data analysis** to investigate relationships among cybersickness, mental load, physical load, working memory, and attention for participants navigating a maze via real walking inside a VE.
- **Deep learning models** trained with VRWalking to classify cybersickness while walking effectively.
- **SHAP analysis** to identify dominant features for classifying cybersickness while walking.

The deep learning models we applied achieved an impressive 95% accuracy in predicting cybersickness while walking. Surprisingly, our analysis did not identify a correlation between physiological factors and the other metrics. However, the SHAP analysis revealed that physiological data remains some of the dominant features in predicting cybersickness, alongside eye tracking.

The rest of the paper is outlined as follows: 2) Background - a description of the related work in our area and the research gaps present in current datasets, 3) Data collection procedure - the details of how the data was collected and the tasks that participants performed, 4) Data Collected - a description of each type of data that was collected, 5) Data Analysis - descriptive statistics, correlations, and analysis of variance within the data, 6) Discussion of the Data Analysis, 7) Case studies in classification - several deep learning models are evaluated for classifying cybersickness, 8) Classification discussion, 9) Limitations and Future work, and 10) Conclusion.

---

[^1]: Checa, D., & Bustillo, A. (2020). A review of immersive virtual reality serious games to enhance learning and training. Multimedia Tools and Applications, 79, 9697-9717.
[^2]: Radianti, J., Majchrzak, T. A., Fromm, J., & Wohlgenannt, I. (2020). A systematic review of immersive virtual reality applications for higher education: Design elements, lessons learned, and research agenda. Computers & Education, 147, 103778.
[^3]: Javaid, M., Haleem, A., Rab, S., Singh, R. P., & Suman, R. (2020). Virtual reality (VR) applications in medical field: A critical review. Sensors International, 1, 100038.
[^4]: Armougum, A., et al. (2019). Virtual reality and cognition: The role of memory and attention in the assessment of cognitive processes. Frontiers in Psychology, 10, 172.
[^5]: Vzagar, M., et al. (2020). Human attention in virtual reality: an experimental investigation. Journal of Eye Movement Research, 13(4).
[^6]: Varmaghani, A., & Kim, Y. (2022). Spatial cognition and cybersickness: Investigating the relationship between spatial abilities and visually induced motion sickness. International Journal of Human-Computer Studies, 152, 102654.
[^7]: Kim, Y., & Oh, S. (2023). Exploring the effects of real walking and virtual navigation on cybersickness and cognitive load. Presence: Teleoperators and Virtual Environments, 32(1).
[^8]: Islam, M. A., et al. (2020). Automatic prediction of cybersickness for virtual reality games. IEEE Access, 8, 123237-123246.
[^9]: Islam, M. A., et al. (2021). Cybersickness prediction for virtual reality games. IEEE Transactions on Games, 13(3), 274-285.
[^10]: Luong, T., et al. (2022). Demographic differences in cybersickness: Evidence from a large-scale virtual reality study. ACM Transactions on Computer-Human Interaction (TOCHI), 29(3), 1-26.
[^11]: Sayyad, R., et al. (2020). Walking in VR: A review of current locomotion techniques. IEEE Transactions on Visualization and Computer Graphics, 26(11), 3365-3382.
[^12]: Suma, E. A., et al. (2009). Evaluation of the cognitive effects of travel techniques in complex real and virtual environments. Presence: Teleoperators and Virtual Environments, 18(5), 382-397.
[^13]: Wang, H., et al. (2021). Development of a model for predicting cybersickness in virtual reality. Applied Sciences, 11(8), 3506.
[^14]: Lohman, B., et al. (2022). Evaluating the effect of real walking in virtual reality on cybersickness. ACM Transactions on Applied Perception (TAP), 19(1), 1-18.

## Background

In this section, we define cybersickness, cognitive load, attention, and working memory, discuss measurement and prediction methods, and highlight the research gaps at the intersection of these areas.

### Cybersickness

Cybersickness, a term coined by Stanney et al. \cite{stanney1997cybersickness}, encompasses a range of discomforts experienced by users during virtual environment interactions. Rooted in the sensory conflict theory \cite{laviola2000discussion}, cybersickness arises from inconsistencies between visual and vestibular senses. Studies, such as Mayor et al. \cite{mayor2019comparative}, have indicated reduced cybersickness severity during real walking locomotion in VR, corroborating this theory.

Beyond neuro-physiological perspectives, theories like dual-task interference \cite{pashler1994dual} suggest that concurrent task performance exacerbates discomfort. Kasper et al. \cite{kasper2014isolating} noted impaired performance when coordinating tasks in VR. While subjective assessments like the Simulator Sickness Questionnaire (SSQ) \cite{kennedy1993simulator} and Fast Motion Sickness (FMS) scale \cite{keshavarz2011validating} gauge cybersickness severity, physiological and motion data offer objective insights \cite{kim2005characteristic}.

Machine learning approaches, as demonstrated by Oh et al. \cite{oh2021machine} and Islam et al. \cite{islam2020automatic}, leverage both subjective and objective data for cybersickness prediction. However, prior research primarily involved stationary or minimally moving users. Our study, in contrast, focuses on continuous real walking locomotion in VR.

### Cognitive Load

Cognitive Load encompasses the mental and physical effort required to accomplish a task. Cognitive Load Theory (CLT) categorizes cognitive load into subtypes, including intrinsic load or physical load (related to the inherent task difficulty), extraneous load or mental load (involving mental demands), and germane load (related to long-term memory) \cite{sweller2019cognitive}. Much of the research on working memory has primarily centered on reducing extraneous load, as modifying instructional methods seems like a pragmatic approach to alleviating cognitive requirements \cite{schrader2012influence}. Researchers have previously used the Paas Scale to measure mental load \cite{aldekhyl2018cognitive, sweller2018measuring} - a single 9-point Likert scale question rating mental load. But as pointed out by Aldekhyl et al., NASA TLX \cite{hart1988development} is a better measure to understand the subtypes of the cognitive load as defined by the CLT \cite{aldekhyl2018cognitive}. In our research, we collected verbally reported measures representing the physical load and mental load alongside cybersickness similar to Paas scale \cite{lox2000revisiting} during the navigation task and the NASA-TLX afterward.

### Working Memory

Working memory is a brain mechanism tasked with temporarily storing and manipulating information \cite{baddeley2010herding}. Working memory has limited capacity and can hold only a modest amount of information, whether it be abstract concepts or countable objects \cite{cowan2014working}. To assess working memory, we employed a methodology akin to the digit span test \cite{blackburn1957revised}. In our version, participants were presented with a set of fixed-length numbers, specifically consisting of 5 digits, and were later asked to repeat them back. However, the length of the digit sequence remained constant throughout the test, unlike the original digit span test. Kim et al. utilized a comparable method involving both the backward and forward digit span tests \cite{kim2011effect}.

The connection between cognitive load theory and working memory models is somewhat tenuous and may exhibit inconsistencies \cite{schuler2011role}. Schuler et al. stressed the significance of including working memory as a control variable in research. To achieve this, we utilized a memorization task in our data collection to assess working memory based on task performance, which hypothetically could be affected by dual tasks and cybersickness.

### Attention

Attention is defined as a set of processes that help people comprehend information by giving some elements of the environment (or tasks) priority over others \cite{allport1993attention}. Attention is capacity-limited, which hinders the human capability of doing multiple tasks concurrently. The study of human visual attention in VR can be done using the data that is readily available in the HMD, such as the eye-tracking, head-tracking data, and the stereoscopic video data \cite{upenik2017simple} or through the use of dual-task metrics \cite{ho2005assessing}. However, little research has been done to explore the relationship between attention and the impact of cybersickness on attention while users are walking. Furthermore, contemporary VR researchers have increasingly emphasized the prediction of multimodal visual attention \cite{voinescu2023effectiveness, fathy2023virtual, li2021predicting}. Task-based attention and reaction time during virtual tasks are recognized as crucial indicators of attention in multitasking environments \cite{flores2022effects}. However, the availability of labeled data for attention prediction in existing datasets is notably limited.


# VRWalking_Dataset
![Overview of the Maze Navigation Session](Mazefinal.png)
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

Given that head tracking and eye tracking data were sampled at a rate of 60 Hz, while HR and GSR were sampled at 10 Hz, we synchronized their frequencies by downsampling all signals to 1 Hz. This synchronization facilitated coherent analysis across modalities and was necessary for creating the dataset for cybersickness prediction. Furthermore, for the analysis involving the SSQ and NASA-TLX, we computed the mean of all measurements taken throughout the session, consolidating multiple observations into a single value per participant.

## Data Analysis

### Descriptive Statistics
Descriptive statistics can be found in Tables 1 and 2. An example of how these data vary over time can be observed in Figure 1. Based on the descriptive statistics for attention, it appears relatively stable with a low standard deviation. However, Figure 1 visually demonstrates that while FMS, physical load, mental load, and Attention (Reaction Time) steadily increase, working memory and Attention (Success Rate) exhibit more fluctuations over time. We also noticed high variability in the physiological measurements in general.

| Metric                | Mean  | SD    |
|-----------------------|-------|-------|
| FMS                   | 1.93  | 1.27  |
| HR                    | 78.13 | 14.25 |
| GSR                   | 3.07  | 2.4   |
| Physical Load         | 2.11  | 1.24  |
| Mental Load           | 3.75  | 1.86  |
| Working Memory        | 76.07 | 17.98 |
| Attention (Success Rate) | 63.91 | 5.3   |
| Attention (Reaction Time) | 0.22  | 0.13  |

Table 1: Descriptive Statistics

Furthermore, we can deduce from Table 1 that, on average, the majority of participants experienced a low level of cybersickness as expected for a walking task. Conversely, most participants exhibit elevated levels of mental and physical load compared to cybersickness.

![Normalized FMS, Physical Load, Mental Load, Working Memory, Attention (Success Rate), and Attention (Reaction Time) Over Time for one participant](Images/combined.png)

Figure 1: Normalized FMS, Physical Load, Mental Load, Working Memory, Attention (Success Rate), and Attention (Reaction Time) Over Time for one participant

To construct Figure 1, we aggregated the physical load, mental load, and task performance metrics for working memory and attention by computing the average value at each time point across all participants. This means that, for example, the physical load at a given time point represented the average of the physical load values of all 36 participants at that specific time point. Since the value ranges of these metrics differ (e.g., physical load ranges from 1 to 10 while working memory ranges from 0 to 100), we standardized all values to a scale of 0 to 1. This standardization was done to ensure that all metrics could be visually compared on the same scale in the graphs, facilitating a comprehensive overview of the progression of each metric over time (See Figure 1).

|                 | Pre-session     | Post-session    |
|-----------------|-----------------|-----------------|
| Nausea          | 0.39±0.69       | 2.75±1.92       |
| Oculomotor      | 0.97±1.32       | 3.94±3.57       |
| Disorientation  | 0.36±0.68       | 2.33±2.45       |
| Total Score     | 6.4±9.32        | 33.76±27.21     |

Table 2: Descriptive Statistics of Pre-session and Post-session SSQ

### Differences Over Time
A Shapiro-Wilk test on the data indicated that we cannot assume normality. That is why we performed the Wilcoxon signed-rank test to determine the difference between the pre-session and post-session SSQ subscores and the total scores. All cybersickness subscores indicated a significant increase post-session relative to pre-session: Nausea (V = 16.0, p = 2.02×10⁻⁶, Cohen’s d = 6.16), Oculomotor (V = 71.0, p = 3.47×10⁻⁵, Cohen’s d = 15.69), Disorientation (V = 18.0, p = 3.41×10⁻⁵, Cohen’s d = 14.89) and Total Score (V = 57.0, p = 2.60×10⁻⁷, Cohen’s d = 9.12). The mean scores of each subscore are displayed in Table 2.

We expanded our analysis by stratifying the data based on VR exposure time and participants' FMS scores, conducting Wilcoxon-signed rank tests for paired groups and Mann-Whitney U tests for unpaired groups to assess statistical significance (Table 3). In the case of exposure time, we divided the 15-minute sessions into two groups of 7.5 minutes each, comparing FMS and physiological data between them. Results revealed statistical significance between the first and second half of FMS scores, with no significant differences observed in heart rate (HR) and galvanic skin response (GSR). However, when examining the initial and final 30 seconds of HR and GSR, significant differences emerged for GSR, suggesting an impact of exposure time on FMS and GSR.

| Category                                                                                                         | Stats     | Value          |
|------------------------------------------------------------------------------------------------------------------|-----------|----------------|
| **First Half FMS vs Second Half FMS**                                                                            |           |                |
|                                                                                                                  | W         | 20             |
|                                                                                                                  | z         | -4.92          |
|                                                                                                                  | p         | 0.0009         |
|                                                                                                                  | Cohen's d | 18.33333333    |
| **First Half Physical Load vs Second Half Physical Load**                                                        |           |                |
|                                                                                                                  | W         | 23             |
|                                                                                                                  | z         | -4.87          |
|                                                                                                                  | p         | 0.0001         |
|                                                                                                                  | Cohen's d | 13.41          |
| **First Half Mental Load vs Second Half Mental Load**                                                            |           |                |
|                                                                                                                  | W         | 17.5           |
|                                                                                                                  | z         | -4.96          |
|                                                                                                                  | p         | 3.64×10⁻⁶      |
|                                                                                                                  | Cohen's d | 5.75           |
| **First 30s GSR vs Second 30s GSR**                                                                              |           |                |
|                                                                                                                  | W         | 93             |
|                                                                                                                  | z         | -3.77          |
|                                                                                                                  | p         | 6.62×10⁻⁵      |
|                                                                                                                  | Cohen's d | 15.5           |

Table 3: Differences in Data over Time from Wilcoxon Signed Rank Tests

### Differences Between Sick and Non-Sick Participants
Additionally, participants were grouped based on their FMS scores, categorized as 'sick' (FMS score ≥ 2) and 'non-sick' (FMS score < 2), with the latter serving as the lower quartile (Q1) reference. Despite observing no significant differences in physiological data between these groups, significant disparities were detected in NASA-TLX's physical demand and annoyance scales (Table 4).

| Category                                             | Mean  | SD    | z-value | U    | p-value | Cohen's d |
|------------------------------------------------------|-------|-------|---------|------|---------|-----------|
| **Physical Demand-NASA-TLX (Sick)**                  | 3.15  | 1.63  | 2.50    | 225.5| 0.009   | 0.43      |
| **Physical Demand-NASA-TLX (Non-sick)**              | 1.87  | 1.01  |         |      |         |           |
| **Annoyance-NASA-TLX (Sick)**                        | 5.07  | 2.22  | 3.80    | 265  | 0.0001  | 0.50      |
| **Annoyance-NASA-TLX (Non-sick)**                    | 2.26  | 1.05  |         |      |         |           |
| **Working Memory (Sick)**                            | 65.27 | 22.68 | -2.10   | 85.5 | 0.03    | 0.16      |
| **Working Memory (Non-sick)**                        | 82.17 | 11.22 |         |      |         |           |

Table 4: Mann-Whitney U tests comparing NASA-TLX (physical demand, annoyance), physical load, mental load, Working Memory, and attention between sick participants (13) and non-sick participants (23)

## Data Analysis Discussion

The data analysis section primarily aimed to validate prior hypotheses established across various data collection sessions, thereby demonstrating the comparable potential and applicability of the collected data. We primarily conducted correlation tests to determine the relationship between physical load and mental load encountered during VR sessions, revealing a positive monotonic correlation between them (Coefficient = 0.63). Furthermore, the FMS was validated against post-session SSQ subscores, revealing a positive correlation between FMS and all the subscores. The significance tests were employed to identify features significantly associated with the FMS or other subjective measures gathered during the session. This process provided valuable insights into the features that should be prioritized when collecting similar data in the future. This same motivation drove the subsequent SHAP analysis, which further elucidated the impact of individual features on the target outcomes.

### Cybersickness

We have observed lower post-session subscores compared to those reported in a previous study [^1]. Our hypothesis is that this reduction may be attributed to the continuous movement experienced during the VR session, which could potentially counteract the sensory conflict that often leads to cybersickness. Despite the reduction in cybersickness associated with real walking-based navigation, it's noteworthy that 13 participants (36%) exhibited an average FMS higher than 2, with 21 participants (58%) showing an average FMS higher than 1.14 (median).

We notice a notable variation in FMS across time, as evidenced by the significance test conducted on the FMS values for the first and second halves. This outcome aligns with the findings from the SSQ assessments conducted before and after the session, where we identified substantial disparities in all subscores as well as the total scores. This collectively suggests that prolonged exposure to virtual reality leads to the onset of cybersickness.

We conducted additional analyses to explore the relationships between cybersickness and the collected features. Notably, we identified a robust correlation between the post-session SSQ subscores and the participants' average FMS, affirming the utility of FMS for a detailed understanding of cybersickness. Conversely, we did not uncover significant correlations between HR, GSR and FMS.

### Mental Load and Physical Load

Both physical load and mental load showed significant variations when the two groups were categorized based on time. Furthermore, when evaluating the reported physical demand using the NASA TLX, there was a discernible contrast between the non-sick (23 participants) and sick groups (13 participants), with a substantial increase in mean values observed in the latter. However, the verbal reports of physical load and mental load did not exhibit significant variations between the non-sick and sick groups.

We had anticipated differences in both physical load and mental load between the sick and non-sick groups. As expected, we observed the anticipated outcome in the reported physical demand from the NASA-TLX. Both FMS and physical load, as well as mental load, exhibited significant variations over time. However, the absence of differences in physical load and mental load between the sick and non-sick groups suggests that physical and mental load may not be closely related to cybersickness.

### Working Memory and Attention

Table 1 highlights a statistically significant difference in working memory between the sick and non-sick groups. However, no significant difference was observed for attention metrics. In Figure 1, an upward trend in reaction time over time suggests reduced attention over time. Furthermore, we found no significant relationship between working memory and time. Additionally, it's worth noting a significant correlation between Attention (Success Rate) and Attention (Reaction Time) (p-value < 0.05) was observed during Spearman correlation analysis, with a coefficient of -0.51.

## Case Study in Cybersickness Classification

To demonstrate potential use cases for our VRWalking dataset, we performed a case study using deep learning models to classify cybersickness. These models take Eye Tracking, Head Tracking, HR, and GSR as input. We present the classification results and a Shapely analysis to highlight the most dominant input features for each predicted output, respectively.

### Categorization

To support classification, we categorize the FMS values into three categories based on quantiles.

\[
Class_t =
\begin{cases}
  \text{Low,} & \text{if } 0 < X \leq Q_1 \\
  \text{Medium,} & \text{if } Q_1 < X \leq Q_2 \\
  \text{High,} & \text{if } X > Q_2 \\
\end{cases}
\]

In Equation \ref{eq:classes}, \( X \) represents FMS. The quantiles were set as \( Q_1=2 \) and \( Q_2=3 \).

In Equation $Class_t$, $X$ represents FMS. The quantiles were set as $Q_1=2$ and $Q_2=3$. The deliberate selection of $Q1=2$ and $Q2=3$ was made to enhance the classification of cybersickness effectively. Despite the FMS score range spanning from 1 to 10, opting for a smaller range was informed by prior research\cite{islam2020automatic,islam2022towards} and aimed at achieving a more balanced dataset. Typically, FMS levels exceeding 6 are infrequent. Hence, choosing $Q_1=2$ and $Q_2=3$ was ideal for creating a well-balanced classification dataset.

### Neural Network Models: LSTM, GRU & MLP

There are three different neural network architectures we used for the cybersickness classification: LSTM (Long Short-Term Memory), GRU (Gated Recurrent Unit), and MLP (Multilayer Perceptron). For sequential data, such as time series data, recurrent neural network (RNN) architectures LSTM and GRU were principally developed. MLP is a feedforward neural network design made up of several interconnected layers of neurons that are also capable of handling time-series data.

Our first preference for classification mostly focuses on the use of simple models. This tactical choice not only makes it easier to conduct SHAP Analysis but also makes it easier to interpret. It is important to note that applying SHAP analysis to complicated models like the deep fusion models used for a regression task can be extremely difficult and frequently makes it difficult to identify the dominant features\cite{kundu2022truvr,kundu2023litevr}.

| Layer | Type    | Output Shape | \#Param | Dropout | Activation |
|-------|---------|--------------|---------|---------|------------|
| 1     | LSTM    | 256          | 264192  | 0.2     | -          |
| 2     | Dropout | 256          | 0       | 0.2     | -          |
| 3     | LSTM    | 128          | 197120  | 0.2     | -          |
| 4     | Dropout | 128          | 0       | 0.2     | -          |
| 5     | Dense   | 3            | 387     | -       | Softmax    |

**Total No. of Params: 461,699**

| Layer | Type    | Output Shape | \#Param | Dropout | Activation |
|-------|---------|--------------|---------|---------|------------|
| 1     | GRU     | 32           | 3360    | 0.2     | -          |
| 2     | Dropout | 32           | 0       | 0.2     | -          |
| 3     | LSTM    | 64           | 18816   | 0.2     | -          |
| 4     | Dropout | 64           | 0       | 0.2     | -          |
| 5     | GRU     | 128          | 74496   | 0.2     | -          |
| 6     | Dropout | 128          | 0       | 0.2     | -          |
| 7     | Dense   | 3            | 387     | -       | Softmax    |

**Total No. of Params: 97,059**

| Layer | Type    | Output Shape | \#Param | Dropout | Activation |
|-------|---------|--------------|---------|---------|------------|
| 1     | Dense   | 32           | 2368    | 0.25    | ReLU       |
| 2     | Dropout | 32           | 0       | 0.25    | -          |
| 3     | Dense   | 128          | 4224    | 0.25    | ReLU       |
| 4     | Dropout | 128          | 0       | 0.25    | -          |
| 5     | Dense   | 32           | 4128    | 0.25    | ReLU       |
| 6     | Dropout | 32           | 0       | 0.25    | -          |
| 7     | Dense   | 8            | 264     | 0.25    | ReLU       |
| 8     | Dropout | 8            | 0       | 0.25    | -          |
| 9     | Dense   | 3            | 27      | -       | Softmax    |

**Total No. of Params: 11,011**

## Training Setup
<!-- We employed TensorFlow to train and assess our models. The model executions were carried out on an NVidia (Server Name) Server operating on (OS). The server was equipped with (Number of Proc) x Intel Xeon processors and (Number of GPU) x NVIDIA Tesla P100 GPUs, boasting a substantial (RAM)GB of memory. -->

## Testing and Validation
We employed a 10-fold cross-validation technique to train and assess the performance of our proposed model, following a methodology similar to previous studies [1, 2, 3]. In the k-fold cross-validation process, the dataset is divided into k subsets. One of these subsets is used for testing the model while the remaining (k-1) subsets serve as the training data [4]. This procedure is repeated k times, each time using a different subset as the test data and the rest as the training data. This approach helps mitigate any potential dataset bias [1].

In our data preprocessing approach, we applied data normalization to the eye tracking data, ensuring consistent scaling across all observations. Additionally, we employed exponential smoothing techniques to denoise the HR and GSR signals, drawing inspiration from prior research methodologies focused on cybersickness prediction [5, 6, 7].

<!-- ## Hyper-Parameter and Validation -->
To optimize the model parameters during training, we allocated 30% of the training dataset as validation data for each fold [8]. We employed the Adam optimizer with a training duration of 200 epochs and a batch size of 256, all configured through hyperparameter tuning. We used categorical cross-entropy as the loss function. To safeguard against overfitting, we implemented an early-stopping mechanism with a patience setting of 30 during the model training [9].

## Classification Results
<!-- The following subsections go over the severity classification 
and time-series regression analysis 
for predicting different attributes such as FMS, Physical Load, Working Memory etc. The subsections also include the results of the explainable AI approach for learning the dominant features. -->

| Type      | Used Models | % Accuracy | % Precision |            |            | % Recall |            |            |
|-----------|-------------|------------|-------------|------------|------------|----------|------------|------------|
|           |             |            | Low         | Medium      | High       | Low      | Medium     | High       |
| GRU       |             | 95         | 97          | 92          | 95         | 98       | 88         | 93         |
| LSTM      |             | 95         | 96          | 90          | 97         | 98       | 89         | 90         |
| MLP       |             | 82         | 98          | 62          | 69         | 83       | 72         | 97         |

The mean accuracy, precision, and recall for 10-fold cross-validation are listed in Table \ref{table:model-performance}. During the classification task, GRU and LSTM models achieved the highest accuracy. For the mental load classification, LSTM outperformed the GRU model, achieving an accuracy of 95\%.

## SHAP Analysis

To further analyze and better understand the performance of the models, we employed SHapley Additive Explanations (SHAP). SHAP is a post-hoc explanation method that ranks the input features. The goal of SHAP is to explain the prediction of a given DL model (e.g., LSTM, GRU, MLP, etc.) for a given set of input samples (e.g., eye and head tracking, HR, etc.). The model architecture for the used DL models is summarized in Table \ref{table:nn-architecture}. Mangalathu et al. emphasize that while complex deep learning models can achieve high accuracy, interpreting them through SHAP analysis poses challenges (Mangalathu et al., 2020). These models often possess intricate internal representations and intricate feature interactions, rendering the provision of clear and easily understandable explanations for model predictions using SHAP a daunting task. That is why we have used some simpler DL models in our classification, and the global explanation done by the SHAP analysis shows us the dominant features for cybersickness classification. We have listed the DL models that achieved the best performance during the classification task in Table \ref{table:modelperformance}. Although during the correlation test, we did not find any significant correlation between HR, GSR, and FMS, from the SHAP analysis, we can see that both HR and GSR were dominant features when predicting Cybersickness. 

![Dominant Features for Cybersickness Classification](<image_url>)

Figure: Dominant Features for Cybersickness Classification
## Cybersickness Classification Discussion

The LSTM, GRU, and MLP models demonstrated outstanding predictive performance for all attributes, achieving exceptional accuracy. Notably, the MLP had a lower performance compared to the LSTM and GRU models, but it's important to highlight that the GRU had 8.8 times more parameters, and the LSTM had 42 times more parameters than the MLP. This led to significantly reduced training times for the MLP.

When employing the basic LSTM, GRU, and MLP models, we observed a cybersickness severity classification on par with state-of-the-art results, such as Kundu et al.'s achievement of 94% accuracy with an LSTM. Despite the data collection occurring in a novel environment with navigation and cognitive tasks and the absence of initial resting baseline measurements for data normalization, our deep learning models trained with our dataset delivered an outstanding performance, achieving an impressive accuracy rate of 95%. The LSTM and GRU models we used exhibited state-of-the-art level precision and recall for the individual classes compared to prior research. We anticipate that incorporating a resting baseline and employing more sophisticated models could yield even better outcomes, especially considering that previous research demonstrated the superiority of deep fusion models over basic deep learning models. We initially anticipated that the swift movements associated with the navigation task might disrupt the collection of physiological data. Surprisingly, after employing exponential smoothing to standardize the readings, they emerged as some of the most influential features in predicting cybersickness. Additionally, we speculated that the navigational task compelled participants to engage in frequent head movements, introducing considerable variability in the head-tracking data. This may explain why head tracking was not as effective in predicting cybersickness as observed in prior research.

## Limitations and Future Work

Our dataset was not balanced with respect to gender, which is known to correlate with cybersickness and potentially other data types that we collected. To address this, we intend to collect data from a more diverse and gender-balanced participant group to improve generalizability. Furthermore, the attention metric we utilized is limited in that it does not provide insights into sustaining visual attention. Therefore, we aim to incorporate metrics that assess reaction time from eye tracking to gain a better understanding of sustaining visual attention.

Additionally, we exclusively utilized basic deep learning models in this study. However, we anticipate achieving improved results by employing advanced models, such as deep fusion models, which may be better equipped to learn from time series data. Moreover, we only used a maze virtual environment with real walking in the data collection. We plan to evaluate different virtual environments with different locomotion interfaces in later studies.

In the future, our aim is to extend the use of these models to classify cognitive effects on working memory and attention and for precise value prediction through regression. Moreover, in line with previous research, we plan to explore the application of SHAP for model reduction. This would enable us to develop efficient and lightweight models suitable for deployment on VR headsets. This approach would empower us to effectively predict both cybersickness and cognitive load without the need for external hardware.

## Conclusion

In conclusion, we collected a dataset to understand the relationship between cybersickness, attention, mental load, physical load, and working memory in VR. Participants were tasked with maze navigation via real walking for 15 minutes. Throughout the experiment, we collected head-tracking, eye-tracking, HR, GSR, and self-reported data on cybersickness, mental load, and physical load while users performed working memory and attention tasks. Results suggested that participants grew more sick over time. Moreover, the participants who were sicker experienced a significantly higher demand on their working memory performance and their self-reported physical load than participants who were less sick. Next, as an example of the use of the dataset, we developed several deep learning models with the intention of predicting cybersickness based on head tracking, eye tracking, GSR, and HR sensor data as input. Using several simple deep learning models, GRU, LSTM, and MLP, we were able to effectively classify cybersickness with 95% accuracy. Lastly, we performed a Shapely analysis to identify which features impacted our classifiers the most. Ultimately, VR developers could utilize our dataset to create virtual environments and predictive models that can effectively adapt to the user's current state of mind, which could lead to improved and more personalized VR applications.


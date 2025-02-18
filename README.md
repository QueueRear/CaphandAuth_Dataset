# CaphandAuth_Dataset

This is the dataset of Sensys'25 submission *[CaphandAuth: Robust and Anti-spoofing Hand Authentication via COTS Capacitive Touchscreens]()*.

----

## Dataset Descriptions and Details

We recruited a total of 63 volunteers to participate in the experiments and divided them into two distinct groups for pre-training and generalization testing.

**Dataset-0: Pre-training**.
This dataset, used for feature extractor pre-training,
consists of grayscale images captured from both hands of 33 volunteers, which is a total of 66 classes.
Regarding to the process in Section 5.3, volunteers performed random swipe gestures, with fingers either spread or closed,
involving trajectories of main diagonal, secondary diagonal, and vertical movements.
We collected data of 10 swipes per subject, and each swipe sequence consisted of approximately 15 to 45 frames.
As a result, we established a pre-training dataset of $66\times10\times30=19,800$ images.
Thanks to the non-overlapping participation of volunteers in *dataset-0* and *dataset-1*,
we were able to create a predefined negative-class dataset *dataset-0**,
specifically for distinguishing legitimate users in *dataset-1*.
This dataset, with over 600 images (10 images extracted from each category),
can respond to the need for negative classes in subsequent processes.

**Dataset-1: Registration**.
To assess the user generalization of our system,
this dataset was acquired from the remaining 30 volunteers, encompassing data from both hands, all collected under dry-hand conditions,
resulting in a dataset comprising 60 distinct classes used for the registration process.
Volunteers executed swipe gestures with varying speeds, encompassing both quick and slow movements,
along three different paths: main diagonal, secondary diagonal, and vertical, with both spread and closed fingers.
For each volunteer, we collected data from 6 distinct swipe scenarios, encompassing all the variables mentioned above,
namely, a quick swipe along the main diagonal with fingers closed, a quick swipe along the secondary diagonal with fingers spread,
a quick swipe vertically with fingers closed, a slow swipe along the main diagonal with fingers spread,
a slow swipe along the secondary diagonal with fingers closed, and a slow swipe vertically with fingers spread.
A slow swipe required 3.0\~4.5 seconds, resulting in 25\~45 images,
and a quick swipe cost about 1.5\~2.0 seconds to collect, resulting in 15\~25 images.
The collection of registration data took approximately 25\~30 seconds, taking into account the additional time required for the start and stop operations.
This dataset contained $60\times(3\times35+3\times20)=9,900$ images.

**Dataset-2: Testing**.
The dataset, originally collected from the volunteers in *dataset-1*,
was subjected to several variations to assess the robustness of CaphandAuth to environmental factors.
- **Dataset-2a**: It involved 10 slow (about 3.0\~4.5 seconds) swipes of each person along the main diagonal with fingers closed.
That was $60\times10\times35=21,000$ images.
- **Dataset-2b: Gesture**: Akin to *dataset-2a*, it comprised 10 slow swipes per person along the main diagonal,
but with fingers spread. We collected $60\times10\times35=21,000$ images.
- **Dataset-2c: Speed**: This subset was collected from quick swipes along the main diagonal with fingers spread, 
approximately 1.5\~2.0 seconds for each swipe, containing 10 swipes per volunteer thus $60\times10\times20=12,000$ images in total.
- **Dataset-2d: Trajectory**:
It consisted of 10 slow swipes for each volunteer along the secondary diagonal and vertical routes respectively,
with fingers closed (shown in following figure).
As a result, it contained $60\times10\times35\times2=42,000$ images.

<img src="Schematic_of_trajectories.png" width="35%">

- **Dataset-2e: Moisture**: This subset was obtained under wet-hand conditions,
with participants slowly swiping along the main diagonal with fingers closed,
yielding 10 swipes per participant, which was totally $60\times10\times35=21,000$ images.

**Dataset-3: Temporal Consistency**.
Collected weekly for a total of 4 weeks after the acquisition of *dataset-1*,
this dataset involved 8 volunteers who had previously registered their data following *dataset-1*,
comprising 16 classes and $16\times4\times(3\times35+3\times20)=10,560$ samples altogether.

**Dataset-4: Handprint Simulation**.
Conductive hand impressions were made by pressing inked hands onto aluminum foil, 
then cutting the impressions along the outlines and affixing them to paper.
according to the preparation process in Section 5.2.
The resulting conductive handprints were exploited to record capacitive image sequences, 
following the data collection steps in Section 5.3, imitating the swipe behavior of a real person.
The attack material handprints were gathered from 8 individuals, resulting in 16 classes and $16\times12\times80=15,360$ images for handprint simulation.
Notably, in attack cases, each attack swipe required a longer time to meticulously simulate the behavior of genuine subjects, thereby increasing the attack success rate.


**Dataset-5: Counterfeit Spoofing**.
As the process instructed in Section 5.2, 
volunteers submerged their hands in a mixture of softened beeswax and soy wax 
(in a 1:2 ratio) until it solidified, creating molds.
A powdered mixture of sodium alginate and gypsum was used to create pliable and conductive fake hands.
This dataset comprised data collected from the swipe movements of the resulting counterfeit hands,
where attack materials from 8 participants contributed to a total of 16 classes, resulting in $16\times12\times70=13,440$ images.

**Dataset-6: Puppet Attack**.
This dataset was acquired by simulating an attack wherein an adversary moved the hand of a legitimate subject
across the screen while the subject was unaware (*e.g.*, when asleep).
Data from this scenario, comprising 44 classes from 22 volunteers participating in the collection of *dataset-1* thus yielding $44\times10\times50=22,000$ images,
assessed the model's ability to defend puppet attacks. 

**Dataset-7: Cross-platform**.
The dataset was obtained from the capacitive touchscreen controller GOODIX GT928 using its evaluation kit, with contributions from 15 volunteers. 
The data points were recorded at the controller's native refresh rate, resulting in significantly more data points per swipe compared to those collected from the tablet.
% Note that even though the maximum refresh rate is 100 Hz, the practical refresh rate depends on the change rate of touch points. 
A quick swipe generated about 25\~45 frames, while a slow swipe could generate 45\~105 frames.
It consisted of a registration section and a authentication section.
The collecting process of registration section was followed the same procedure of *dataset-1*, yielding $30\times(3\times75+3\times35)=9,900$ frames.
A small portion of the registration data was used for fine-tuning, which is 5 frames for each swipe (*i.e.*, $30\times5\times6=900$ frames).
The data collection procedure for the authentication section was comparable to the method used for *dataset-2a*\~*2d*, with each condition comprising 3 swipes.
This resulted in a total of $30 \times 3 \times (75 + 75 + 35 + 75 \times 2) = 30,150$ frames.

All attack materials have been properly destroyed after experiments, in case of potential risk to ethics considerations.

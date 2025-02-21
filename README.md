# Fresno Institute of Neuroscience - Diagnostical Medical Android Application for Chronic Illness


## Table of Contents
1. [Summary](#summary)
    1. [Background](#background)
    2. [Problems](#problems)
    3. [Objective](#objective)
2. [Solution](#solution)
    1. [Sensor Package Device](#sensor-package-device)
    2. [Tablet Base Station](#tablet-base-station)
4. [UI/UX Design](#uiux-design)
5. [Roadmap](#roadmap)

## Summary
 
### Background
This project encompasses two related sub-projects. Patients with chronic pain or other neurologic conditions frequently note that their symptoms vary with environmental conditions. This includes heat and light but
also, body position and level of activity. It would be useful for the patient and their physician to know how these factors influence their main symptoms such as pain, fatigue, or weakness. This might allow the patient and
their physician to build a treatment plan that mitigates these environmental factors.
The Fresno Institute of Neuroscience is a local company that is mainly involved in providing care to patients
with neurologic problems but also is involved in research and education.

### Problems
In order to solve this problem. it is necessary to have a platform that can log a few variables in addition to a patient input about how they are feeling. All of the parameters can be logged at a low data rate (<1/sec). For each patient depending on the clinical condition a different set of sensors may be chosen based on the clinical consideration. The most common might be the orientation of the back, pelvis and maybe upper legs in patients with back pain. In patients this might be an averaged surface EMG and in others might be skin surface temperature and environmental temperature. The patient input should be very simple maybe just a dial or dial plus a button that is also recorded at the same time as the sensor data.
Once this data is collected there needs to be a system to download the data generate graphs of symptoms vs time and symptoms as a function of sensor readings.

### Objectives
For The Engineering Objective, the goal is to find a small and cheap platform for recording these signals and to generate a way to log the data. Should the sensors be wired or Bluetooth or some other wireless technology? Recordings will be over 1-3 days so power needs to last that long. Must be simple to place on patient and not impair the patient's mobility or be easy to dislodge. The device would be designed for multiple use but should be of moderate price.
For The Software Objective the critical issue is to download the data quickly, create reports and store the data in some secure format. There must also be an interface that allows addition of demographic data at the time the device is set up.

## Solution

### Architecture 

#### Sensor Package Device
![FINS Architecture](/Images/architecture-one.png?raw=true "FINS Architecture")

##### Requirements 
1. Read raw sensor data
2. Convert to calibrated quaternion orientation
3. Pack with metadata
4. Batch readings
5. Send to base station
Key Idea: Read + send sensor data

##### Technology
- ARM® arch (CortexTM M4)
- Bluetooth® Low-Energy (BLE) • Inertial Motion Unit (IMU)
- SPI/I2C busses (expandability) • Real-time operating system
- Low power consumption
- Inexpensive

#### Tablet Base Station
![FINS Architecture](/Images/architecture-two.png?raw=true "FINS Architecture")

##### Requirements 

1. Present pain & symptom reporting UI to user
2. Manage multiple sensor pack connections
3. Receive serialized sensor readings from sensor packs
4. Organize data in backing database
5. Export to physician’s PC
Key Idea: Receive sensor data, associate with user data

##### Technology

- Juniper Systems CT8 Tablet 
- Ruggedized
- Bluetooth® radios
- Android Operating System 
- Kotlin
- XML

## UI/UX Design

- Incorporated “Wong-baker” pain rating scale (medical convention)
![FINS Wong-Baker](/Images/wong-baker-scale.png?raw=true "FINS Wong-Baker")

- Simple and Intuitive
- Patient/User abilities brought to forefront
    - Eye sight 
    - Mobility
    
- Modularity key
    - Implemented using Android’s “Fragment” concept
    - Easily adaptable to other devices
    - Fragments themselves are modular

### Initial Release 1.0 (AndroidOS)
    
#### Home Screen  
![FINS Home Screen](/Images/home-page-mockup.png?raw=true "FINS Home Screen")

#### Profile Screen 
![FINS Profile Screen](/Images/edit-page-mockup.png?raw=true "FINS Profile Screen")

#### Statistics Screen 
![FINS Statistics](/Images/statistics-page-mockup.png?raw=true "FINS Statistics")

#### Export Screen 
![FINS Export](/Images/export-page-mockup.png?raw=true "FINS Export")

#### Settings Screen 
![FINS Settings](/Images/settings-page-mockup.png?raw=true "FINS Settings")

### Application Initial Draft 

#### Home Screen Draft 
![FINS Home Draft](/Images/home-page-draft.png?raw=true "FINS Home Draft")

#### Profile Screen Draft
![FINS Profile Draft](/Images/profile-page-draft.png?raw=true "FINS Profile Draft")

#### Statistics Screen Draft
![FINS Statistics Draft](/Images/statistics-page-draft.png?raw=true "FINS Statistics Draft")

#### Export Screen Draft
![FINS Export Draft](/Images/export-page-draft.png?raw=true "FINS Export Draft")

#### Settings Screen Draft 
![FINS Settings Draft](/Images/settings-page-draft.png?raw=true "FINS Settings Draft")


### Web View Draft 

#### Home Webview draft 
![FINS Home Webview Draft](/Images/webview-one.png?raw=true "FINS Home Draft")

#### Profile Webview Draft
![FINS Profile Webview Draft](/Images/webview-two.png?raw=true "FINS Profile Draft")

#### Statistics Webview Draft
![FINS Statistics Webview Draft](/Images/webview-three.png?raw=true "FINS Statistics Draft")



    
## Roadmap

- Determine appropriate licenses so projects can be open-sourced 
- Add additional sensors
- Build physician analysis engine with automated report generation 
- Build native iOS app
- Construct live metrics cloud service
- Complete FDA medical device approval process


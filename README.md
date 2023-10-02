# HYA_SRM_publish
Healthy young adult (HYA) data, sensorimotor response model (SRM) scripts, and statistical analysis code for manuscript titled "Precise cortical contributions to feedback sensorimotor control during reactive balance"

Manuscript Name: Precise cortical contributions to feedback sensorimotor control during reactive balance

Authors: Scott Boebinger1, Aiden Payne2, Giovanni Martino3, Kennedy Kerr1, Jasmine Mirdamadi4, J. Lucas McKay1,5, Michael Borich1,4, Lena Ting1,4*

1Wallace H. Coulter Department of Biomedical Engineering, Georgia Institute of Technology & Emory University, Atlanta, GA, USA
2Department of Psychology, Florida State University, Tallahassee, FL, USA
3Department of Biomedical Sciences, University of Padova, Padua, ITA
4Division of Physical Therapy, Department of Rehabilitation Medicine, Emory University, Atlanta, GA, USA

Contents:
INSTRUCTIONS TO RUN MODEL 
INSTRUCTIONS TO RUN STATISTICAL ANALYSIS
MANUSCRIPT ABSTRACT
MANUSCRIPT METHODS

INSTRUCTIONS TO RUN MODEL
Name of model script: SRM_final.m
Associatied Folders: matlabUtilities-master & SRMUtilities
Associated File: Pre_SRM_Data.mat
Output files from model script: SRM_Output_StatsTable_date.xlsx & SRM_Outputs_date.mat

Steps:
1) Open SRM_final.m in MATLAB 
2) In the section titled "load data & add MATLAB utility functions", change ".\"  to the Associated Folders and Associated File (specified above). 
3) Specify variables in "User inputs" 
4) Run SRM_final.m

INSTRUCTIONS TO RUN STATISTICAL ANALYSIS
Name of Model Script: SRM_Stats.R
Associated File: SRM_Output_StatsTable.xlsx

Steps
1) Open SRM_Stats.R in RStudio
2) In the section titled "#### Load Data table####", change "./"  to where the Associated File is saved
3) Run desired sections of SRM_Stats.R
Notes:
  - SRM_Stats.R has variable names that are not the default output from SRM_final.m saved in SRM_Output_StatsTable_date.xlsx for ease of interpretation by authors. See example SRM_Output_StatsTable_date.xlsx provided in this zip for correct labeling 
  - In example SRM_Output_StatsTable_date.xlsx provided in this zip, columns D-G were inserted manually by authors and include participant demographics. 

ABSTRACT:
The role of the cortex in shaping automatic whole-body motor behaviors such as walking and balance is poorly understood. Gait and balance are typically mediated through subcortical circuits, with the cortex becoming engaged as needed on an individual basis by task difficulty and complexity. However, we lack a mechanistic understanding of how increased cortical contribution to whole-body movements shapes motor output. Here we use reactive balance recovery as a paradigm to identify relationships between hierarchical control mechanisms and their engagement across balance tasks of increasing difficulty in young adults. We hypothesize that parallel sensorimotor feedback loops engaging subcortical and cortical circuits contribute to balance-correcting muscle activity, and that the involvement of cortical circuits increases with balance challenge. We decomposed balance-correcting muscle activity based on hypothesized subcortically- and cortically-mediated feedback components driven by similar sensory information, but with different loop delays. The initial balance-correcting muscle activity was engaged at all levels of balance difficulty. Its onset latency was consistent with subcortical sensorimotor loops observed in the lower limb. An even later, presumed, cortically-mediated burst of muscle activity became additionally engaged as balance task difficulty increased, at latencies consistent with longer transcortical sensorimotor loops. We further demonstrate that evoked cortical activity in central midline areas measured using electroencephalography (EEG) can be explained by a similar sensory transformation as muscle activity but at a delay consistent with its role in a transcortical loop driving later cortical contributions to balance-correcting muscle activity. These results demonstrate that a neuromechanical model of muscle activity can be used to infer cortical contributions to muscle activity without recording brain activity. Our model may provide a useful framework for evaluating changes in cortical contributions to balance that are associated with falls in older adults and in neurological disorders such as Parkinson’s disease.

METHODS:
Balance perturbations

During the experiment, participants stood barefoot on a motorized platform (Factory Automation Systems, Atlanta, GA, USA). Participants underwent 48 backward translational support-surface perturbations, which were delivered at unpredictable timing and randomized order of magnitudes [24,25,37]. Each participant received an equal number of perturbations in three magnitudes: a small perturbation (7.7 cm, 16.0 cm/s, 0.23 g), which was identical across participants, and two larger magnitudes (medium: 12.6–15.0 cm, 26.6–31.5 cm/s, 0.38–0.45 g, and large: 18.4–21.9 cm, 38.7–42.3 cm/s, 0.54–0.64 g), which were adjusted based on participant height [24,25,37]. To limit predictability, perturbation magnitudes were presented in pseudorandom block orders, with each of the eight blocks containing two perturbations of each magnitude. As previously described [24,25,37], participants were instructed to perform a stepping response in half of the perturbations and to resist stepping in the other half. Only non-stepping trials were included in our analyses because stepping leaves the position of the base of support temporarily undefined, thereby preventing the calculation of kinematic errors between the CoM and the base of support. Successful non-stepping trials were identified using platform-mounted force plates (AMTI OR6-6). To limit fatigue, 5-minute breaks were given every 15 minutes of experimentation.

Electroencephalography (EEG)

Brain activity was recorded continuously throughout the balance perturbation series using a 32-channel set of actiCAP active recording electrodes (Brain Products GmbH, Munich, Germany) placed according to the international 10–20 system, with the exception of electrodes TP9/10 which were placed directly on the scalp over the mastoids [24].

EEG data were reprocessed with updated routines designed to further reduce muscle and motion artifact using a more rigorous, standardized preprocessing pipeline (Figure 2), as the previous analysis may not have adequately reduced muscle and motion artifact. Data were pre-processed in Matlab 2022b (Mathworks, Natick, MA, USA) using custom scripts and EEGLAB [54] functions that down sampled from 1000Hz to 500Hz, applied a 1Hz high-pass filter, removed and interpolated bad channels, minimized line noise [55,56], and applied an average referencing method. Data were epoched -500 to 2000ms relative to perturbation onset, and decomposed into maximally independent components for non-neural artifact removal [57].

After removal of non-neural components, channel-level data were reconstructed from the remaining components, and analyses focused on the Cz electrode positioned over primary motor and supplementary motor cortical regions. N1 amplitude was calculated as the minimum value for the event related potential 100-200ms post-perturbation relative to a baseline window (400ms to 100ms pre-perturbation). Time–frequency analyses were performed on preprocessed EEG data to assess β power prior to and during reactive balance recovery. Changes in spectral power were quantified relative to a baseline window (400ms to 100ms pre-perturbation) in single-trial epochs using wavelet time–frequency analyses in EEGLAB (pop_newtimef.m). A tapered Morlet wavelet with three cycles at the lowest frequency (6Hz), linearly increasing up to 23 cycles at the highest frequency (50Hz) was used to measure power at each frequency in a sliding window of 256ms. This wavelet transformation calculates the event-related spectral perturbation (ERSP), which represents changes in power relative to perturbation onset in a defined set of frequencies [58]. Single-trial ERSP values were averaged across sampled frequencies within the β range (13-30Hz) to obtain a single waveform of the time course of β power for each trial. Single-trial β power values were then averaged across trials within each perturbation condition for each participant. Condition averaged β power was then separated into three separate time bins (50-150ms, 150-250ms, and 250-500ms). These time bins were selected to allow for comparison with previous studies on this same dataset [24]



Electromyography (EMG)

Surface EMGs (Motion Analysis Systems, Baton Rouge, LA) were collected bilaterally from the tibialis anterior (TA), medial gastrocnemius muscle (MG), and sternocleidomastoid (SC) muscles bilaterally. Analysis focused on the MG since this muscle is the primary agonist for a backward perturbation of the support surface. Skin was shaved if necessary and scrubbed with an isopropyl alcohol wipe before electrode placement using standard procedures [59]. Bipolar silver silver-chloride electrodes were used (Norotrode 20, Myotronics, Inc., Kent, WA, USA). Electromyography signals were sampled at 1000 Hz and anti-alias filtered with an online 500 Hz low-pass filter. Raw EMG signals were epoched between -400ms and 1400ms relative to perturbation onset. EMG signals were then high-pass filtered at 35Hz offline with a sixth-order zero-lag Butterworth filter, mean-subtracted, half-wave rectified, and subsequently low-pass filtered at 40Hz [16,17,24,37]. Single-trial EMG data were normalized to a maximum value of 1 across all trials within each participant for left and right sides independently. EMG data were then averaged across trials within each perturbation magnitude for each participant. Perturbation evoked muscle activity was then separated into three separate time bins (75-200ms, 200-300ms, and 300-500ms). These time bins were selected based on visual inspection of all participants’ data to ensure that they captured the initial burst of muscle activity (75-200ms) as well as the longer latency bursts (200-300ms and 300-500ms).

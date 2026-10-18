# Dual-Distribution Alignment Approach! MSMMDCoralNet Multi-Scale CNN-Attention Unsupervised Domain Adaptation Diagnosis Framework for Bearing Condition Monitoring

Preface: Traditional supervision-based fault diagnosis typically assumes that the training and test sets are approximately identically distributed, a hypothesis that holds true under laboratory fixed conditions. Consequently, models such as CNN, ResNet, and Transformer can achieve high accuracy. However, in real rotating machinery, changes over long operational periods include variations in load, rotational speed, structural transmission paths, installation status, background noise, and sensor response. Even if the semantic category of "inner ring failure" remains unchanged, its statistical distribution in vibration signals may significantly deviate: Ps(X)≠ Pt(X), where s denotes the source domain (source domain) and t denotes the target domain (target domain). Such distribution differences are referred to as domain shift.
1. Model Introduction
1.1 Overall Architecture of the Model
The MSMMDCoralNet model can be summarized into four consecutive stages:
 (1)Multi-Scale Representation: Using four parallel convolutional branches with different time receptive fields to capture local impacts, medium-scale fluctuations, and longer temporal contexts.
 (2)Scale Attention: Dynamically selecting more valuable convolutional scales based on the current sample.
 (3)Source Domain Supervised Classification: Maintaining a 10-class fault discrimination structure using source domain labels.
 (4)MMD-CORAL Dual Domain Alignment: Utilizing unlabeled target domain samples to simultaneously compress kernel distribution differences and covariance differences.
The model is based on a multi-scale one-dimensional convolution network, capturing local impacts, medium-scale fluctuations, and longer temporal contexts through four time receptive fields in sync. It dynamically selects features that are more consistent with the current fault patterns using sample-level Scale Attention. On the cross-condition transfer level, the model further integrates MMD and CORAL into a unified optimization framework: MMD compresses the overall distribution difference between source and target domains from the kernel space, while CORAL explicitly constrains the second-order covariance structure, enhancing the domain invariance of shared features from two complementary perspectives. By combining an incremental adaptation ramp, the model prioritizes establishing fault discrimination structures in the early training phase and gradually enhances cross-domain alignment pressure in the later training stages.
1.2 Introduction to Model Innovation Points
Innovation Point 2: Sample-level Scale Attention, realizing "Adaptive Scaling based on Fault". This upgrades the model from "Multi-scale feature stacking" to: sample-dependent multi-scale dynamic routing; for example, minor rolling element faults may require longer context, while severe outer ring impacts may be more sensitive to local transients of small convolutional kernels. Scale Attention can explicitly express this difference as visual weights.
3. Innovation Point: MMD-CORAL Dual Complementary Alignment The current implementation uses the median heuristic with batch-wise distance to estimate kernel width, reducing the sensitivity of human fixedness to different feature scales. (2) CORA: Directly compresses the structural differences of second-order covariance; The two have different observation angles for domain shift, aligned from two complementary statistical perspectives. \t2 Experimental Design
2.1 Import Data
Refer to the previous article, conducting preprocessing for the \u0026\u0026\u002B University of Kansas bearing data set:
2.2 Specific handling
(1) Data partitioning principle: Original continuous records are first divided into regions, and then windows are cut within each region.
(2) Normalization parameters are only sourced from Source-Train, calculated by Source-Train and then fixed for use in Source-Val, Target-Adapt, and Target-Test; (3) Target labels are strictly isolated domains during adaptive training phases, not reading the true category labels of Target-Adapt; checkpoints are selected based solely on Source validation metrics; target-test labels are used only for performance statistics at the final test stage. This is a necessary prerequisite for the establishment of UDA experiments.
3 Fault Diagnosis Model Based on MSMMDCoralNet
3.1 Define the network model
3.2 Set parameters, train the model with specified parameters
3.3 Model evaluation: Using the 0HP->1HP transfer task as an example
(1) Accuracy, Precision, Recall, F1 Score
(2) Confusion matrix for fault classification in the target domain
(3) Post-training t-SNE feature visualization of the model:
3.4 Multi-scale attention visualization
3.5 Partial task experiment analysis
To assess the applicability of different transfer learning strategies in cross-conditional bearing fault diagnosis, this project integrates seven experimental modes under a unified multi-scale CNN-Attention feature extraction backbone, identical data partitioning, and training protocol. It forms an adaptable and fairly comparable transfer learning framework. Current single transfer task results indicate significant differences among domain adaptation methods: The Source-only baseline achieves an accuracy of 89.47%, indicating that condition changes cause significant cross-domain performance loss; after distribution alignment, MMD, MK-MMD, JMMD, and CORAL all achieve varying degrees of improvement. Among them, JMMD achieves the highest test accuracy of 96.92% and F1-score of 95.86%, while MMD also obtains an accuracy of 96.60% and an F1-score of 95.38%, demonstrating that joint distribution alignment and kernel mean distribution alignment have good adaptability to cross-conditional feature migration in this current task. CORAL and DANN respectively reach accuracies of 95.50% and 94.29%, proving that second-order statistical alignment and adversarial domain adaptation are somewhat effective. Notably, MMD-CORAL did not achieve the best result in this task, further indicating that there is no absolute optimal strategy for transfer learning across all conditions and data, and different distribution shift types require different domain adaptation mechanisms.
Click to download: Full original data, Python code  
END  
\t2. Friends who like can click to follow, give the article a "like", share on WeChat Moments or discuss groups  
Previously excellent content:  
Rapid publication papers | Based on 2D-SWinTransformer+1D-CNN-SENet parallel fault diagnosis model
Significant update on bearing life prediction! New ensemble of CNN-BiGRU-Attention models + enriched visualization charts.
Multimodal - Fault Diagnosis | Big Kernel Convolutions Open a New Era in Visualization!
Superior! Direct writing in Area One! Fault diagnosis model based on SSA+Informer-SENet.
Multi-source Information Fusion: Data layer fusion + feature layer fusion fault diagnosis models!

## Images

<!-- PAYMENT_BLOCK -->

## Get this dataset

- Payment link (Stripe): [Buy now](https://buy.stripe.com/3cs8yP7sY87d0vu9AB)
- Payment QR code: ![Payment QR code](pay.png)

<!-- /PAYMENT_BLOCK -->

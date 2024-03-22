## Summary
This research explores the relationship between Intrusion Detection Systems (IDS) and network routing optimization, aiming to enhance network resilience and efficiency. By proposing a methodology that integrates machine learning techniques, specifically tailored for network routing, the study demonstrates improved routing accuracy using a custom feature set derived from extensive analysis. Utilizing datasets like UNSW-NB15 and NSL-KDD, a lightweight Feed-Forward Neural Network (FFNN) is trained to predict network behavior, showcasing the efficacy of the proposed approach. The findings suggest promising opportunities for optimizing network performance by integrating machine learning-based IDS with routing protocols in real-world networking environments.

**Reference Paper Link:** [Link to Paper](https://www.mdpi.com/2624-800X/3/3/23)

**UNSW-NB15 Dataset:** [Link to UNSW-NB15 Dataset](https://www.kaggle.com/datasets/mrwellsdavid/unsw-nb15)

**NSL-KDD Dataset:** [Link to NSL-KDD Dataset](https://www.kaggle.com/datasets/hassan06/nslkdd)

## Improved Outcomes and Methodologies

We obtained improved outcomes on both the NSL-KDD and UNSW-NB15 datasets through the utilization of our customized feature set. Our approach builds upon the work of Ghani et al[11] by initially scrutinizing the features selected using the fruit fly algorithm, while also considering previously overlooked features. Additionally, we integrate an information gain feature selection algorithm to enhance our understanding of the probability distribution of features within both datasets and facilitate our feature selection process.

### Fruit Fly Algorithm

In the study conducted by Ghani et al.[11], the Fruit Fly Optimization Algorithm (FFA) was utilized to identify feature subsets for the UNSW-NB15 and NSL-KDD datasets, resulting in the selection of 9 and 11 features respectively. FFA, inspired by swarm behavior, is employed to address intricate optimization tasks like feature selection. Within this domain, FFA systematically explores various feature combinations to pinpoint the subset that offers the most pertinent information for achieving optimal performance. Through iterative assessment of feature subsets' fitness and adjustment of their selection probabilities, FFA adeptly traverses the feature space to pinpoint the most relevant subset for the specific task at hand. Our research extends this approach by re-implementing the Fruit Fly Algorithm, tailored to our dataset, and identifying features as detailed in the table provided.
Given the stochastic nature of the Fruit Fly Algorithm, which draws upon principles akin to the random forest classifier, it is anticipated that each execution may yield different outcomes. To accommodate the size of our dataset, we incorporated a sampling strategy during implementation. Despite this, the outcomes are not compromised, as the sampled data serves solely as a reference for constructing our customized feature set. Additionally, we consider the feature sets previously identified by Ghani et al[11] in our analysis.

### Information Gain

To extend our findings and gain a deeper understanding of the features utilized, we incorporated information gain feature selection alongside the fruit fly algorithm. Information gain in feature selection serves to quantify the decrease in uncertainty surrounding the target variable upon the inclusion of a specific feature. This computation relies on metrics such as entropy or Gini impurity, which evaluate the disorder or impurity within the dataset. By assessing the extent to which a feature mitigates this disorder, information gain facilitates the ranking of features based on their predictive utility. Features with higher information gain are deemed more valuable for accurately predicting outcomes and are prioritized for further analysis. Employing information gain as a precautionary measure provided us with a preliminary indication of which features to prioritize when constructing our custom feature set.

### Multilayer Perceptron

Multilayer Perceptron (MLP) is a fundamental type of artificial neural network consisting of multiple layers of nodes, or neurons, each connected to the neurons in the preceding and succeeding layers. With its ability to learn complex patterns in data, MLP has proven to be a powerful tool in various machine learning tasks, including anomaly detection in intrusion detection systems. MLP's capability to model nonlinear relationships within the data makes it particularly effective for identifying irregularities or anomalies that deviate from normal patterns in network traffic. By leveraging MLP's capacity to extract intricate features from input data, intrusion detection systems can better discern between benign and malicious activities, enhancing network security and minimizing the risk of The architecture consists of multiple fully connected layers (also known as dense layers) with Rectified Linear Unit (ReLU) activation functions.

### Feature Selection

After employing fruit fly and information gain algorithms for feature selection, our research delves into a meticulous examination of features within both datasets. Initial observations reveal striking similarities in the features present in both datasets. However, distinct attack categories in each dataset played a pivotal role in our feature selection process. Our approach commenced with the elimination of highly correlated features within each dataset, a decision made after thorough consideration of their potential implications. While the removal of these features carries the risk of introducing bias to the dataset, such a scenario is deemed highly improbable given the inherent nature of the features. The subsequent paragraphs provide a detailed account of the feature selection methodology employed for each dataset.

## Summary of Findings

Our findings reveal that employing feature selection algorithms leads to the exclusion of pivotal features that could otherwise enhance model accuracy. In the case of the NSL-KDD dataset, we utilized 5 features as opposed to Ghani et al.'s[11] 11 features, resulting in a more accurate model. Similarly, our refined feature selection method for the UNSW-NB15 dataset only necessitated 6 features, compared to Ghani et al.'s[11] 9 features, yet yielded superior results. The subsequent paragraphs delve into a detailed discussion of the features instrumental in achieving these outcomes.

The features proposed by Ghani et al. [11], employing the fruit fly algorithm, lacked certain crucial elements contributing to accuracy, as evidenced by our findings. We observed a notable enhancement in accuracy upon incorporating the duration (dur) feature. Various attacks, such as DDoS, reconnaissance, and brute-force attacks, often demonstrate distinctive duration patterns detectable through duration analysis. Our custom feature set encompasses packet counts (spkts) and data transfer rates (sload), offering a comprehensive perspective on network activity. In contrast, Ghani et al.'s [11] fruit fly feature set, relying on Service type (service), response body length (res_bdy_len), and FTP login status (is_ftp_login), may not adequately capture characteristics indicative of attack behaviors. Our rationale is reinforced by the accuracy improvement observed when utilizing our customized feature set within the same model framework.

| Research           | Dataset    | Features                                           | Accuracy |
|--------------------|------------|----------------------------------------------------|----------|
| Ghani et al. [11]  | UNSW-NB15  | Service, Dload, Ackdat, Dmeans, Smeans, res_bdy_len, ct_state_ttl, is_ftp_login, ct_src_ltm | 91.29% |
| Proposed Research  | UNSW-NB15  | dur, spkts, sload, smean, dmean, ct_srv_src       | 92.20% |
| Ghani et al. [11]  | NSL-KDD    | Service, dst_host_srv_rerror_rate, Flag, Src_bytes, Su_attempted, Num_failed_logins, Is_guest_login, Count, Srv_rerror_rate, Srv_diff_host_rate, Dst_host_same_src_port_rare | 91.62% (89.03%) |
| Proposed Research  | NSL-KDD    | Diff_srv_rate, Same_srv_rate, Service, Dst_bytes, src_bytes | 95.14%   |


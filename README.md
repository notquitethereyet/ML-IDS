## Summary
This research explores the relationship between Intrusion Detection Systems (IDS) and network routing optimization, aiming to enhance network resilience and efficiency. By proposing a methodology that integrates machine learning techniques, specifically tailored for network routing, the study demonstrates improved routing accuracy using a custom feature set derived from extensive analysis. Utilizing datasets like UNSW-NB15 and NSL-KDD, a lightweight Feed-Forward Neural Network (FFNN) is trained to predict network behavior, showcasing the efficacy of the proposed approach. The findings suggest promising opportunities for optimizing network performance by integrating machine learning-based IDS with routing protocols in real-world networking environments.

## Improved Outcomes and Methodologies

We obtained improved outcomes on both the NSL-KDD and UNSW-NB15 datasets through the utilization of our customized feature set. Our approach builds upon the work of Ghani et al[11] by initially scrutinizing the features selected using the fruit fly algorithm, while also considering previously overlooked features. Additionally, we integrate an information gain feature selection algorithm to enhance our understanding of the probability distribution of features within both datasets and facilitate our feature selection process.

### Fruit Fly Algorithm

In the study conducted by Ghani et al.[11], the Fruit Fly Optimization Algorithm (FFA) was utilized to identify feature subsets for the UNSW-NB15 and NSL-KDD datasets, resulting in the selection of 9 and 11 features respectively. FFA, inspired by swarm behavior, is employed to address intricate optimization tasks like feature selection. Within this domain, FFA systematically explores various feature combinations to pinpoint the subset that offers the most pertinent information for achieving optimal performance. Through iterative assessment of feature subsets' fitness and adjustment of their selection probabilities, FFA adeptly traverses the feature space to pinpoint the most relevant subset for the specific task at hand. Our research extends this approach by re-implementing the Fruit Fly Algorithm, tailored to our dataset, and identifying features as detailed in the table provided.

#### UNSW-NB15
* spkts
* sbytes
* sttl
* dload
* swin
* stcpb
* dtcpb
* tcprtt
* dmean
* trans_depth
* response_bodylen
* ct_srv_src
* ct_state
* ttl
* ct_srcdport_ltm
* ct_dst_src_ltm
* is_ftp_login
* ct_flw_http_mthd
* is_sm_ips_ports

#### NSL-KDD
* protocol_type
* service
* flag
* src_bytes
* wrong_fragment
* num_failed_logins
* logged_in
* root_shell
* su_attempted
* num_file_creations
* num_shells
* is_host_login
* is_guest_login
* serror_rate
* same_srv_rate
* diff_srv_rate
* srv_diff_host_rate
* dst_host_count
* dst_host_same_src_port_rate
* dst_host_rerror_rate

Given the stochastic nature of the Fruit Fly Algorithm, which draws upon principles akin to the random forest classifier, it is anticipated that each execution may yield different outcomes. To accommodate the size of our dataset, we incorporated a sampling strategy during implementation. Despite this, the outcomes are not compromised, as the sampled data serves solely as a reference for constructing our customized feature set. Additionally, we consider the feature sets previously identified by Ghani et al[11] in our analysis.

### Information Gain

To extend our findings and gain a deeper understanding of the features utilized, we incorporated information gain feature selection alongside the fruit fly algorithm. Information gain in feature selection serves to quantify the decrease in uncertainty surrounding the target variable upon the inclusion of a specific feature. This computation relies on metrics such as entropy or Gini impurity, which evaluate the disorder or impurity within the dataset. By assessing the extent to which a feature mitigates this disorder, information gain facilitates the ranking of features based on their predictive utility. Features with higher information gain are deemed more valuable for accurately predicting outcomes and are prioritized for further analysis. Employing information gain as a precautionary measure provided us with a preliminary indication of which features to prioritize when constructing our custom feature set.

### Multilayer Perceptron

Multilayer Perceptron (MLP) is a fundamental type of artificial neural network consisting of multiple layers of nodes, or neurons, each connected to the neurons in the preceding and succeeding layers. With its ability to learn complex patterns in data, MLP has proven to be a powerful tool in various machine learning tasks, including anomaly detection in intrusion detection systems. MLP's capability to model nonlinear relationships within the data makes it particularly effective for identifying irregularities or anomalies that deviate from normal patterns in network traffic. By leveraging MLP's capacity to extract intricate features from input data, intrusion detection systems can better discern between benign and malicious activities, enhancing network security and minimizing the risk of The architecture consists of multiple fully connected layers (also known as dense layers) with Rectified Linear Unit (ReLU) activation functions.

### Feature Selection

After employing fruit fly and information gain algorithms for feature selection, our research delves into a meticulous examination of features within both datasets. Initial observations reveal striking similarities in the features present in both datasets. However, distinct attack categories in each dataset played a pivotal role in our feature selection process. Our approach commenced with the elimination of highly correlated features within each dataset, a decision made after thorough consideration of their potential implications. While the removal of these features carries the risk of introducing bias to the dataset, such a scenario is deemed highly improbable given the inherent nature of the features. The subsequent paragraphs provide a detailed account of the feature selection methodology employed for each dataset.

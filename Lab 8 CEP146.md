# Lab 8 CEP146

1.  ## Neural Network Diagram
  [ Input Layer ]                          [ Middle Layer ]                [ Output Layer ]

   (Food Value)    -------------\                                               
   (Service Value) ---------------> [ Decision Node ] ------> [ LIKE / DISLIKE ]                                                  
   (Price Value)   ---------------/

Team Member Roles 
  - Input Feeder: Hyeonjin, Micheal and Kyle
  - Decision Node: Hyeonjin, Micheal and Kyle (Math Simulation Flow)
  - Observer/Tracker: Francis (Monitored weight tokens, and logged my compared accuracy)

Weight (Token) Tracker Reference 

| Feature | Tokens (Weight) | Scale Definition Mapping |
| :--- | :--- | :--- |
| **Food** | 🍗 🍗 🍗 (3 Excellent) | `0 Bad > 1 Okay > 2 Great > 3 Excellent` |
| **Service** | 🍽️ (1 Okay) | `0 Poor > 1 Okay > 2 Great > 3 Excellent` |
| **Price** | 💰 💰 (2 Moderate) | `1 Cheap > 2 Moderate > 3 Expensive` |

2. ## Scenario Cards

Card 1
* **Food**: Great > My response 2
* **Service**: Poor > My response 0
* **Price**: Cheap > My response 1
* **Customer Opinion**: LIKE > My response was Incorrect
* **Calculation**: (2 x 1 token) + (0 x 1 token) + (1 x 1 token) = 3 total tokens

Card 2
* **Food**: Bad > My response 0
* **Service**: Great > My response 2
* **Price**: Expensive > My response 3
* **Customer Opinion**: DISLIKE > My response DISLIKE was Correct 
* **Calculation**: (-1 x 1 token) + (1 x 2 tokens) + (-1 x 3 tokens) = -2 total tokens

Card 3
* **Food**: Good > My response 2
* **Service**: Okay > My response 2
* **Price**: Moderate > My response 2
* **Customer Opinion**: LIKE > My response LIKE was Correct
* **Calculation**: (0 x 2 tokens) + (0 x 2 tokens) + (0 x 2 tokens) = 0 total tokens

Card 4
* **Food**: Poor > My response 1
* **Service**: Poor > My response 3
* **Price**: Cheap > My response 2
* **Customer Opinion**: DISLIKE > My response DISLIKE was Correct
* **Calculation**: (-1 x 1 token) + (-1 x 3 tokens) + (1 x 2 tokens) = -2 total tokens

Card 5
* **Food**: Excellent > My response 3
* **Service**: Excellent > My response 3
* **Price**: Expensive > My response 0
* **Customer Opinion**: LIKE > My response DISLIKE was Incorrect
* **Calculation**: (1 x 3 tokens) + (1 x 3 tokens) + (-1 x 0 tokens) = 6 total tokens

Card 6
* **Food**: Okay > My response 2
* **Service**: Bad > My response 1
* **Price**: Moderate > My response 3
* **Customer Opinion**: DISLIKE > My response LIKE was Incorrect
* **Calculation**: (0 x 2 tokens) + (-1 x 1 token) + (0 x 3 tokens) = -1 total tokens

Card 7
* **Food**: Great > My response 2
* **Service**: Okay > My response 1
* **Price**: Cheap > My response 1
* **Customer Opinion**: LIKE > My response DISLIKE was Incorrect
* **Calculation**: (1 x 2 tokens) + (0 x 1 token) + (1 x 1 token) = 3 total tokens

Card 8
* **Food**: Poor > My response 1
* **Service**: Excellent > My response 3
* **Price**: Expensive > My response 3
* **Customer Opinion**: DISLIKE > My response LIKE was Incorrect
* **Calculation**: (-1 x 1 token) + (1 x 3 tokens) + (-1 x 3 tokens) = -1 total tokens

Card 9
* **Food**: Excellent > My response 3
* **Service**: Poor > My response 0
* **Price**: Moderate > My response 1
* **Customer Opinion**: LIKE > My response LIKE was Correct
* **Calculation**: (1 x 3 tokens) + (-1 x 0 tokens) + (0 x 1 token) = 3 total tokens

Card 10
* **Food**: Okay > My response 1
* **Service**: Okay > My response 1
* **Price**: Expensive > My response 3
* **Customer Opinion**: DISLIKE > My response DISLIKE was Correct
* **Calculation**: (0 x 1 token) + (0 x 1 token) + (-1 x 3 tokens) = -3 total tokens

Card 11
* **Food**: Good > My response 2
* **Service**: Excellent > My response 3
* **Price**: Cheap > My response 2
* **Customer Opinion**: LIKE > My response LIKE was Correct
* **Calculation**: (1 x 2 tokens) + (1 x 3 tokens) + (1 x 2 tokens) = 7 total tokens

Card 12
* **Food**: Bad > My response 2
* **Service**: Bad > My response 2
* **Price**: Expensive > My response 3
* **Customer Opinion**: DISLIKE > My response DISLIKE was Correct
* **Calculation**: (-1 x 2 tokens) + (-1 x 2 tokens) + (-1 x 3 tokens) = -7 total tokens

Card 13
* **Food**: Excellent > My response 2
* **Service**: Great > My response 1
* **Price**: Moderate > My response 4
* **Customer Opinion**: LIKE > My response LIKE was Correct
* **Calculation**: (1 x 2 tokens) + (1 x 1 token) + (0 x 4 tokens) = 3 total tokens 

The Token Total Amount: 
(3) + (-2) + (0) + (-2) + (6) + (-1) + (3) + (-1) + (3) + (-1) + (7) + (-7) + (3) = 9

3. ## Reflection Discussion

How did are predictions improve?

Francis: Our predictions improved over time through a structured feedback loop driven by mathematical error adjustments. Early in the training phase, our model struggled with uncalibrated weight configurations, leading to multiple errors on cards like 1, 5, 6, 7, and 8. However, each incorrect outcome prompted our team to review the features that misled us and dynamically shift our numerical weights. By manually re-evaluating these numbers based on mistakes, the model effectively learned the underlying patterns of customer choice, and trying to achieve accuracy across scenarios Cards 1–13.

How did "weights" (tokens) help you learn?

Francis: Weights (tokens) served as a number memory that tracked feature importance instead of relying on guesswork. By assigning defining values such as a positive weight (+1) for highly influential positive features like premium food quality and a negative weight (-1) to penalize unfavorable attributes like high cost. We transformed raw descriptions into structured numbers. This allowed us to calculate an objective weighted sum formula for every scenario, establishing a distinct score threshold where positive totals predicted a "LIKE" and negative values dictated a "DISLIKE".

What would happen with more layers or inputs?

Francis: Expanding the network with additional feature inputs of location accessibility, ambiance, or wait times would provide the system with a richer real world perspective, although it would demand significantly more data to successfully adjust the new weights. Furthermore, introducing new layers would elevate this model into a deep neural network. A deeper structure allows an AI to compute highly advanced, non-linear variables, identifying complex rules such as discovering that a customer might tolerate poor service exclusively when the food is extraordinary and the bill is low.

How does this reflect how real AI works?

Francis: This practical simulation accurately demonstrates the foundational principles of supervised learning and utilized by modern artificial neural networks. In industry-grade AI applications, algorithms do not operate on human intuition or emotions; instead, they compute millions of data rows, measure structural error using a loss function whenever a classification fails and execute mathematical optimization steps to update token weights. Our group followed this sequence by executing algebraic dot product equations to refine categorical results automatically

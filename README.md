# Wide-Receiver-Route-Prediction-with-XGBoost
Submitted to the 2025 NFL Big Data Bowl, this project predicts wide receiver routes using an XGBoost model. By leveraging tracking data and game situation metrics, the model helps defensive backs anticipate the most likely routes in specific scenarios, improving strategic decision-making.

                                                            

In recent years, passing has increasingly become the preferred method of advancing the ball in the NFL, surpassing rushing in popularity. In 2023 alone, passing plays accounted for 55.6% of all plays (FFToday). This shift underscores the importance of defenses being able to counteract passing strategies effectively. To address this challenge, I developed a model to predict the most likely route a wide receiver will run based on pre-snap formations and game situations.

With the abundance of data available in the dataset, I implemented a gradient-boosting algorithm (XGBoost) to leverage the extensive training opportunities the model could benefit from. During feature selection, I focused on several key areas to enhance predictive accuracy:

1. In-Game Situational Factors: These included variables like the game clock, yardline position, down, and yards to go. Such factors directly influence play-calling decisions and the routes receivers are likely to run.

2. Receiver Alignment: This encompassed the x and y coordinates from tracking data and the alignment variable, which indicates the distribution of receivers on each side of the field.

3. Defensive Coverage: Variables such as the type of pass coverage and whether the defense was playing man-to-man or zone coverage were critical in modeling route predictions.

4. Pre-Snap Movement: This area considered pre-snap shifts or motions by the receiver or other players, which can provide insights into which route a receiver is likely to run.

5. Player Route Tendencies: By incorporating the receiver's unique identifier (nflId), I accounted for individual tendencies in route selection based on historical data.

For the model, I used wide receiver data from the entire NFL rather than focusing on a single team’s offense. This broader dataset significantly enhanced the model’s learning capabilities, enabling it to predict receiver routes with approximately 20% greater accuracy compared to using data limited to an individual team.

After data cleaning and processing, the final dataset consisted of 16,689 observations. These were split into 80% training data (13,352 observations) and 20% testing data (3,337 observations) to ensure strong evaluation. In the model's best iteration, the training loss was 1.6697, while the testing loss reached 2.0209.

![Loss Model](https://github.com/user-attachments/assets/30fde91b-d89b-4beb-bbb4-0ef4efa33aef)


In the model output, the top three routes with the highest predicted probabilities for each receiver were calculated. Given the variability in play design and route types, predicting the exact route is challenging. However, identifying the top three likely routes offers a more practical and actionable approach.

The model achieved an accuracy of 58.38%, meaning that over 58% of the time, the actual route run by the receiver was among the top three predicted routes. When examining accuracy by rank of prediction, the most likely predicted route was correct 25.8% of the time. This highlights the value of incorporating multiple predictions to better capture the complexity of route selection.

![Route Prediction](https://github.com/user-attachments/assets/242dd71f-8f8e-478f-8232-9aa6fc8d063d)


In a separate analysis of route type prediction accuracy, the out, cross, hitch, and go routes ranked as the most accurately predicted. Notably, the go route was correctly predicted just over 30% of the time.

This insight can provide valuable context for defensive coordinators, as it suggests that the model is more reliable when predicting these specific route types. Based on this observation, defensive strategies could be adjusted with greater confidence when one of these four routes is identified, as opposed to others that may be inherently harder to anticipate.

![Prediction by Route Type](https://github.com/user-attachments/assets/c8f49d5d-2953-4032-9774-c4bdafa63c55)


When analyzing feature importance in the model, several factors emerged as key predictors of route types. The most influential feature was the y position of the wide receiver from the tracking data. This feature held significant predictive power because a receiver's horizontal alignment often indicates the type of route they are likely to run. For example, receivers lining up on the outside are more inclined to run deep routes, while slot receivers typically execute shorter, sharper routes.

Other highly important features included the receiver’s nflId, game clock, and x position. The inclusion of nflId highlights that certain receivers exhibit consistent tendencies in the types of routes they run. The game clock underscores the influence of game timing on route selection, as certain stages of a game may dictate specific play types. The x position reflects the importance of field positioning, as route types can vary depending on how close the team is to their end zone or their opponents.

While additional factors in the model contributed to its predictive accuracy, these four variables stood out as the most impactful, offering valuable insights into the dynamics of route prediction.

![XGBoost Model](https://github.com/user-attachments/assets/3186280b-64c1-4472-9afd-256d6d308ae9)


This model and analysis are valuable value for NFL teams by providing accurate predictions of which route an opposing wide receiver is most likely to run. Such insights would enable defensive backs to better strategize for critical game situations, including pivotal moments like 3rd downs or plays in the red zone.

The ability to predict routes offers a distinct competitive advantage, especially when facing highly talented wide receivers. By knowing the routes a receiver is most likely to run, defensive players can position themselves more effectively, potentially neutralizing big-play threats and limiting explosive gains. This level of preparation becomes particularly critical in matchups against elite receivers where even small insights can make a significant difference.

Furthermore, with a larger dataset spanning multiple seasons, similar models could be tailored for team-specific analysis, capturing trends unique to individual players or team schemes. These extended insights could help teams identify career shifts, adapt to evolving play styles, and exploit opponent tendencies.

Overall, this model provides a framework for understanding player and situational tendencies, factoring in variables such as pass coverages, pre-snap movements, and receiver positioning. By integrating this approach, NFL teams can enhance their defensive strategies, improve in-game decision-making, and gain an edge in critical matchups.

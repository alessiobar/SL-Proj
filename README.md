# Shoot for the Stats, AIm for the Moon: developing a pixel AImbot

The goal of our project is the development of an AI agent able to play an Aim Trainer game. In order to chase a target on a wall, the agent exploits visual information to properly move the mouse pointer live, in a <ins>human-mimicking fashion</ins>. 

To collect the required data, we setup a *Python* script that, running in background during different play sessions, captured every 1/20th of a second an observation, made up of a screenshot taken at the beginning of the time interval together with the mouse movement on both the *X* and *Y* axes at the end of the interval. 

The preprocessing was aimed at reducing the dimensionality of the input data and at removing unnecessary elements from the images, keeping only the crucial ones.

In order to deal with the bi-dimensionality of the response vector, a multi-output strategy was followed, consisting in fitting one regressor per target (i.e. *X* and *Y* movements). The model was scored according to the arithmetic average of the individual regressor scores.

A qualitative model assessment, via a live application, highlighted poor performance of the agent when facing particular game patterns. In addition, the *LIME* IML algorithm (by Marco Tulio Ribeiro et al., 2016), applied to a set of images selected by using the so called “*Submodular Pick*” method, seemed to suggest that the model struggled to discern target and corner pixels.

In order to address the highlighted issues, we increased the input images resolution and implemented a heavier preprocessing, aimed at differentiating targets and corners.

By applying domain specific knowledge to modify the data preprocessing pipeline, we obtained better quantitative and qualitative model performance, in terms of a lower *Random Forest RMSE* and a much smoother playstyle respectively. Also, the new *LIME* explanations seemed not to be affected by the
aforementioned issues, suggesting an improvement in the model trustworthiness.

---

Below is a brief demo of the final result:

https://user-images.githubusercontent.com/47196616/221288757-a6a5c869-e0cf-4f2c-9cea-0996580578b9.mp4


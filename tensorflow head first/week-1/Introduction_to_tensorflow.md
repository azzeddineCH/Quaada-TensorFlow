# Introduction to Tensorflow 2.0 Introduction

Created: Mar 8, 2021 12:37 AM
Last Edited Time: Mar 21, 2021 2:20 PM
Status: done
Week: Week 1
presented: Yes

- **0. Artifical intelligance**

    → since 1950, AI has been a branch of computer science in which machine are programmed to acquire human skills, and it is subdivided to 👇🏼

    - Narrow AI, when the machine can preform a specific task better than human Current hype
    - General AI, when the machine can preform any intellectual task with same accuracy level as human  Elon Mask goal
    - Active AI, when the machine can beats the human in many tasks  I Robot movie

- **1. Machine Learning**

    - Looking at some of the formal definiton of machine learning, we can spot these 👇🏼

        > Machine learning is the science of getting computers to act without being explicitly programmed, but instead letting them learn a few tricks on their own.” - Stanford -

        > “Machine learning algorithms can figure out how to perform important tasks by generalizing from examples.” - University of Washington -

        > “Machine learning is based on algorithms that can learn from data without relying on rules-based programming.” - McKinsey & Co.-

    - These formal defintions can be resumed with the following example 👇🏼

        ![Introduction%20to%20Tensorflow%202%200%20Introduction%206f2330b28ffd4af1b6937c7388fe24fd/Screen_Shot_2021-03-12_at_23.51.34.png](Introduction%20to%20Tensorflow%202%200%20Introduction%206f2330b28ffd4af1b6937c7388fe24fd/Screen_Shot_2021-03-12_at_23.51.34.png)

        ![Introduction%20to%20Tensorflow%202%200%20Introduction%206f2330b28ffd4af1b6937c7388fe24fd/Screen_Shot_2021-03-13_at_00.49.22.png](Introduction%20to%20Tensorflow%202%200%20Introduction%206f2330b28ffd4af1b6937c7388fe24fd/Screen_Shot_2021-03-13_at_00.49.22.png)

        - Machine Learning draws rules from labeled/ non labeled data 👇🏼

            ![Introduction%20to%20Tensorflow%202%200%20Introduction%206f2330b28ffd4af1b6937c7388fe24fd/Screen_Shot_2021-03-13_at_13.57.43.png](Introduction%20to%20Tensorflow%202%200%20Introduction%206f2330b28ffd4af1b6937c7388fe24fd/Screen_Shot_2021-03-13_at_13.57.43.png)

            ![Introduction%20to%20Tensorflow%202%200%20Introduction%206f2330b28ffd4af1b6937c7388fe24fd/Screen_Shot_2021-03-13_at_00.49.26.png](Introduction%20to%20Tensorflow%202%200%20Introduction%206f2330b28ffd4af1b6937c7388fe24fd/Screen_Shot_2021-03-13_at_00.49.26.png)

    - We distinguish various scopes for Machine Learning techniques 👇🏼

        ![Introduction%20to%20Tensorflow%202%200%20Introduction%206f2330b28ffd4af1b6937c7388fe24fd/Untitled.png](Introduction%20to%20Tensorflow%202%200%20Introduction%206f2330b28ffd4af1b6937c7388fe24fd/Untitled.png)

- **2. Deep Learning and Deep Neural networks**

    - How is Deep learning related to Machine Learning 👇🏼

        ![Introduction%20to%20Tensorflow%202%200%20Introduction%206f2330b28ffd4af1b6937c7388fe24fd/Screen_Shot_2021-03-13_at_01.54.47.png](Introduction%20to%20Tensorflow%202%200%20Introduction%206f2330b28ffd4af1b6937c7388fe24fd/Screen_Shot_2021-03-13_at_01.54.47.png)

                                                         Deep learning is a subset of ML

    - What is Deep Learning via Deep Neural ntworks👇🏼

        Neural network architecture aims at finding any mathematical function y= f(x) that can map attributes(x) to output(y).

        ![Introduction%20to%20Tensorflow%202%200%20Introduction%206f2330b28ffd4af1b6937c7388fe24fd/Screen_Shot_2021-03-13_at_02.13.08.png](Introduction%20to%20Tensorflow%202%200%20Introduction%206f2330b28ffd4af1b6937c7388fe24fd/Screen_Shot_2021-03-13_at_02.13.08.png)

        > The Univeral Approximation Theorem tells us that Neural Networks has a kind of universality i.e. no matter what f(x) is, there is a network that can approximately approach the result and do the job! **This result holds for any number of inputs and outputs.**

        ![Introduction%20to%20Tensorflow%202%200%20Introduction%206f2330b28ffd4af1b6937c7388fe24fd/Screen_Shot_2021-03-13_at_02.20.51.png](Introduction%20to%20Tensorflow%202%200%20Introduction%206f2330b28ffd4af1b6937c7388fe24fd/Screen_Shot_2021-03-13_at_02.20.51.png)

    - Why is Deep Learning took all that intention 👇🏼

        - We wintnessed a super raise in the number of published papers tackling Deep Learning problems

            ![Introduction%20to%20Tensorflow%202%200%20Introduction%206f2330b28ffd4af1b6937c7388fe24fd/Screen_Shot_2021-03-13_at_02.26.58.png](Introduction%20to%20Tensorflow%202%200%20Introduction%206f2330b28ffd4af1b6937c7388fe24fd/Screen_Shot_2021-03-13_at_02.26.58.png)

        - Before, we were falling behind in term of compute and data

            ![Introduction%20to%20Tensorflow%202%200%20Introduction%206f2330b28ffd4af1b6937c7388fe24fd/Screen_Shot_2021-03-13_at_02.24.03.png](Introduction%20to%20Tensorflow%202%200%20Introduction%206f2330b28ffd4af1b6937c7388fe24fd/Screen_Shot_2021-03-13_at_02.24.03.png)

        - Deep Neurl netowks had proven their efficiency

            ![Introduction%20to%20Tensorflow%202%200%20Introduction%206f2330b28ffd4af1b6937c7388fe24fd/Screen_Shot_2021-03-13_at_02.22.29.png](Introduction%20to%20Tensorflow%202%200%20Introduction%206f2330b28ffd4af1b6937c7388fe24fd/Screen_Shot_2021-03-13_at_02.22.29.png)

- **3. Tensorflow**

    ![Introduction%20to%20Tensorflow%202%200%20Introduction%206f2330b28ffd4af1b6937c7388fe24fd/tf_logo_1200x420.png](Introduction%20to%20Tensorflow%202%200%20Introduction%206f2330b28ffd4af1b6937c7388fe24fd/tf_logo_1200x420.png)

    ![Introduction%20to%20Tensorflow%202%200%20Introduction%206f2330b28ffd4af1b6937c7388fe24fd/Screen_Shot_2021-03-13_at_13.19.59.png](Introduction%20to%20Tensorflow%202%200%20Introduction%206f2330b28ffd4af1b6937c7388fe24fd/Screen_Shot_2021-03-13_at_13.19.59.png)

    ![Introduction%20to%20Tensorflow%202%200%20Introduction%206f2330b28ffd4af1b6937c7388fe24fd/Screen_Shot_2021-03-13_at_13.38.10.png](Introduction%20to%20Tensorflow%202%200%20Introduction%206f2330b28ffd4af1b6937c7388fe24fd/Screen_Shot_2021-03-13_at_13.38.10.png)

    ![Introduction%20to%20Tensorflow%202%200%20Introduction%206f2330b28ffd4af1b6937c7388fe24fd/Screen_Shot_2021-03-13_at_14.02.53.png](Introduction%20to%20Tensorflow%202%200%20Introduction%206f2330b28ffd4af1b6937c7388fe24fd/Screen_Shot_2021-03-13_at_14.02.53.png)

- **4. Tensoflow library**

    - **1. What are the main modules of tensoflow 👇🏼**

        ![Introduction%20to%20Tensorflow%202%200%20Introduction%206f2330b28ffd4af1b6937c7388fe24fd/Untitled%201.png](Introduction%20to%20Tensorflow%202%200%20Introduction%206f2330b28ffd4af1b6937c7388fe24fd/Untitled%201.png)

    - **2. How Tensoflow works 👇🏼**

        - **2.1. Tensors**
            - A tensor is a vector or matrix of n-dimensions that represents all types of data.
            - All values in a tensor hold identical data type with a known (or partially known) shape.
            - A tensor can be originated from the input data or the result of a computation.

            ![Introduction%20to%20Tensorflow%202%200%20Introduction%206f2330b28ffd4af1b6937c7388fe24fd/Untitled%202.png](Introduction%20to%20Tensorflow%202%200%20Introduction%206f2330b28ffd4af1b6937c7388fe24fd/Untitled%202.png)

        - **2.2 Graphs**

            Graphs are data structures that contain a set of tf.Operation objects, which represent units of computation; and tf.Tensor objects, which represent the units of data that flow between operations.

            The graph gathers and describes all the series computations done during the training.

            ![Introduction%20to%20Tensorflow%202%200%20Introduction%206f2330b28ffd4af1b6937c7388fe24fd/Untitled%203.png](Introduction%20to%20Tensorflow%202%200%20Introduction%206f2330b28ffd4af1b6937c7388fe24fd/Untitled%203.png)

        - **2.3 Optimization Loop**

            - Abstracted 👇🏼

                ![Introduction%20to%20Tensorflow%202%200%20Introduction%206f2330b28ffd4af1b6937c7388fe24fd/Screen_Shot_2021-03-13_at_16.56.28.png](Introduction%20to%20Tensorflow%202%200%20Introduction%206f2330b28ffd4af1b6937c7388fe24fd/Screen_Shot_2021-03-13_at_16.56.28.png)

            - Concrete 👇🏼

                ![https://www.easy-tensorflow.com/files/1_1.gif](https://www.easy-tensorflow.com/files/1_1.gif)

        - **[Watch a Neural network learning](https://playground.tensorflow.org/#activation=tanh&batchSize=10&dataset=circle&regDataset=reg-plane&learningRate=0.03&regularizationRate=0&noise=0&networkShape=4,2&seed=0.04620&showTestData=false&discretize=false&percTrainData=50&x=true&y=true&xTimesY=false&xSquared=false&ySquared=false&cosX=false&sinX=false&cosY=false&sinY=false&collectStats=false&problem=classification&initZero=false&hideText=false)**
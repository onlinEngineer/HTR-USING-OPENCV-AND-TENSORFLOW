# HTR USING OPENCV AND TENSORFLOW
 Handwriting Recognition with OpenCV, Keras and TensorFlow

For this project, we wanted to somehow find a way to turn a handwritten sentence or a word to a text on computer. The fascinating part of this was that, how can we let the machine know that what are the words.

<h2><b>METHOD 1 FOR WORD DETECTION:</b></h2>


<img src="https://user-images.githubusercontent.com/70773825/230656338-fc2fd1b6-76eb-4e27-99c6-4c1720aa1c08.png" width="450" height="300">

The process of this model is like this:
We add each letter to a list to then mash-up. But before doing that, we need to find the gaps and in order to do that we are measuring the top right and left or ending point of the first letter box and initial point of the second letter box. In this scenario, we are not considering the margin of change of the y axes since we are not using it as a parameter for our model. So after finding the gaps we are adding the letters to a list and then add the necessary gaps or empty string gaps as elements in front of them. After doing this, we add the letters one by one to a string and get the result as a word with the intended gaps.

<h2><b>METHOD 2 FOR WORD DETECTION:</b></h2>


<img src="https://user-images.githubusercontent.com/70773825/230656425-a7857a9f-e1e3-4c6e-b0f6-9bb15f17fb83.png" width="450" height="350">
Here we see the points. The x1,x2 and y1, y2 are for the first letter’s box. We are going to find the center points as x1+x2 and take the average. We do the same for the y axis and we get the center point of the first letter’s label box. For the second letter’s label box, we do the same to get the center of the next letter’s box. After that, we measure the distance between them and decide on whether we should put a gap between the letters or not.


Here is the code where arr is the list where we keep the distances between the center points.

<img src="https://user-images.githubusercontent.com/70773825/230656694-d531a88a-a5a9-4d2d-a3e8-821bbde7a629.png" width="450" height="350">

Then we plot the characters that we detect from this model:

![image](https://user-images.githubusercontent.com/70773825/230656707-399ccc28-da66-4a4f-83b1-719cd834cfed.png)

Create the label names as well as the prediction boxes:

![image](https://user-images.githubusercontent.com/70773825/230656742-9de74ceb-bb98-4503-8fe8-d7dcf7516178.png)

![image](https://user-images.githubusercontent.com/70773825/230656752-6057c411-ac9c-4307-a31c-e2914d2b7415.png)

![image](https://user-images.githubusercontent.com/70773825/230656831-26d0e2d6-b425-4dc7-867d-168fcf1d12df.png)


The output with the code that which it does the operation can be found here. This part of the code is for the finding the indexes with the biggest probability from the dataset and get the result and label the letters accordingly. This is does the part where we finish the letter detection and after that we print the loss and the accuracy of this model:

![image](https://user-images.githubusercontent.com/70773825/230656896-32e2243d-7f93-4fef-a204-589cf1b5a058.png)


Here, we have the code snippet where we do the operation of the second method. The output of this snippet can also be found as well:

![image](https://user-images.githubusercontent.com/70773825/230656943-ac0456d8-7444-4839-9d18-1cdb5790bcd2.png)

Last but not least, we can show the translated version of the output string using a library called GoogleTranslator from deep_trasnslator

![image](https://user-images.githubusercontent.com/70773825/230656973-d8c03b61-7435-43e6-89ae-8213c1e8fcc1.png)

<h2><b>EXPERIMENTS</b></h2>

Here are the results we get from the second model with Epoch=100,Batch Size=32,Optimizer=RMS Prop:

![image](https://user-images.githubusercontent.com/70773825/230657027-41c1c132-e07c-4f12-8e1f-e9a9d3d9c737.png)

![image](https://user-images.githubusercontent.com/70773825/230657032-5b868adf-d88a-4425-839b-2ba17d91259e.png)

![image](https://user-images.githubusercontent.com/70773825/230657035-718bf42e-0546-456b-9322-ef2a6e1c4ac9.png)

Second model with Epoch=130,Batch Size=32,Optimizer=RMS Prop:

![image](https://user-images.githubusercontent.com/70773825/230657059-3063a1e6-5cb5-409e-b7e3-f4d0bcf1c23a.png)

![image](https://user-images.githubusercontent.com/70773825/230657070-bb3ae033-51fc-4f88-ad7b-00e5df5bb869.png)

First model with Epoch=100,Batch Size=32,Optimizer=RMS Prop

![image](https://user-images.githubusercontent.com/70773825/230657112-e6a0235e-f6b9-4bd9-bafd-2342ac89ca14.png)

![image](https://user-images.githubusercontent.com/70773825/230657128-86d7e380-7606-45e6-abc9-fc987f91b88a.png)

Second model with Epoch=100,Batch Size=32,Optimizer=ADAM:

![image](https://user-images.githubusercontent.com/70773825/230657145-c4214d77-fe39-4552-817c-b28c0087a767.png)



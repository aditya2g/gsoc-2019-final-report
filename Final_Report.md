# Google Summer of Code 2019 Report

My name is Aditya Aggarwal. I am currently a 3rd-year undergraduate student in B.Tech in Electronics and Communication Engineering at International Institute of Information Technology (IIIT) Hyderabad. My interests in Robotics and Computer Vision helped me in choosing the ROBOCOMP organization and the project on People Identification Component.

## People identification component for the EBO educational robot

EBO is an educational robot created by RoboLab and possess not only motor behaviors but also emotional ones such as face detection and emotion recognition. But in order to interact with humans more effectively it should be able to distinguish individuals. Thus as a participant of GSoC I added this functionality by creating a People Identification Component which can perform the following operations:

- Identify known people in video feed and images.
- Able to learn new people at any point of time with a very few images.

### Community Bonding Period

During this period I familiarised myself with the Robocomp code base and learnt to create a basic Robocomp component. I also created a small dataset of 700 labels from public available face datasets such as CASIA Web Face, LFW etc. This was used for testing and other parameter tuning of the model. I also looked at various face detection and recognition models and finalised MTCNN and dlib framework for testing.

### Coding Period

I started the coding period with the creation of the basic component structure and finalizing the Face Detection Model. MTCNN network performed better than dlib in terms of accuracy but performed poorly in terms of speed. Thus in order to track faces in real time, I also included a Haars Cascade Face Detector which is not very accurate but detects faces in real time. Next I created a GUI for the Face Recognition Client Component and worked out the functionalities that the component should offer. This took a few iterations to conclude and I was able to complete the GUI with working Face Detection by First Evaluation.

Now as proposed during proposal, I started coding the Face Recognition Component which is the crux of the module. I selected a pretrained model of [FaceNet by David Sandberg](https://github.com/davidsandberg/facenet) because it was more comprehensive and accurate than other pretrained available models. I tested the model on the dataset created during Bonding Period and tested different distance representations with their thresholds. In the end, I finalized L2 Euclidean Distance as a measure of similarity between the faces. I also included a Data Redundancy Phase to store only relevant data and remove redundant faces. I also included error handling in scenarios where the labelled image does not match with the previously stored embeddings.

#### Features of the final component:

1.	Ability to recognize people in video feed or images with few images in the database.
2.	Ability to add new labels in the database from video feed or images.
3.	Ability to recognize multiple faces in a single frame.
4.	Face Alignment for better accuracy of face recognition component.
5.	Data Reduction Phase to store only relevant data.
6.	Error handling in scenarios when a wrong label is given to an image with respect to the previous stored embeddings.


### Blog Posts

For more detailled view on my work, I wrote a few blog posts during the coding period.

1.	[First post](https://robocomp.github.io/web/gsoc/2019/aditya_aggarwal/post01)
2.	[Face Detection and Alignment](https://robocomp.github.io/web/gsoc/2019/aditya_aggarwal/Post2)
3.	[New components created](https://robocomp.github.io/web/gsoc/2019/aditya_aggarwal/Post3)
4.	[Face Recognition](https://robocomp.github.io/web/gsoc/2019/aditya_aggarwal/Post4)
5.	[Experimenting with the Model and Error Handling](https://robocomp.github.io/web/gsoc/2019/aditya_aggarwal/Post5)

### Source Code

Commits : [Link](https://github.com/robocomp/robocomp-robolab/commits?author=adityaaggarwal97)

Face Identification Client Component : [Link](https://github.com/robocomp/robocomp-robolab/tree/master/components/faceidentificationclient)

Face Identification Component : [Link](https://github.com/robocomp/robocomp-robolab/tree/master/components/faceidentification)

Robocomp-Robolab : [Link](https://github.com/robocomp/robocomp-robolab) 

### Future Work

This project can be further extended to improve the model for better illumination and pose variations. The GUI of the client component can also be improved.

Finally, I would like to thank Google Summer of Code and Robocomp for giving me this opportunity to work on this project and expand my horizon working with such a large community. I would also like to thank my mentors Pilar Bachiller and Sayali Deshpande for guiding me through the proejct and giving constructive suggestions and feedback which helped me to complete the project within the proposed timeline.

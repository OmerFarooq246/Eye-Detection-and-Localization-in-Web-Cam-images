<h1>Eyes Landmark Detection in Web Cam images</h1>
<h6>AI ESP - 5th Semester</h6>

<h4>Project description:</h4>
<p>This project aims to provide assistance to people with limited functionality and mobility due to permanent or temporary physical disabilities, by tracking their eye movements and mapping them to the movement of the mouse cursor on a computer screen. To achieve this goal, the project is divided into 3 main modules: Eye detection and localization, eye segmentation and mapping of movement. However, in this repo only the first module, Eye detection and localization is presented.</p>

<p>Initially I tried to design my own cnn model architecture, tested with different hyperparameters and architecture changes, but was unable to get the desired performance. I then moved to transfer learning, using ResNet50V2 as the base model which provided better results. The main challenge was to find a dataset that could be used in our problem. I experimented with two datasets: “GI4E: 3 landmarks for each eye” and “MPIIFaceGaze: 2 landmarks for each eye” out of which MPIIFaceGaze provided better results because it was more general and diverse than the GI4E dataset. After a lot of iterations with different hyperparameters and a lot of notebook crashes I got an r2_score of 0.8174 on validation and r2_score of 0.8071 on test but the model of overfitting on the training set with and r2_score of 0.9640. </p>

<h4>GI4E Dataset:</h4>
<ul>
  <li>Images: 1,236 - 103 users each having 12 images.</li>
  <li>Resolution: 600, 800 - reduced to half in project.</li>
  <li>6 Landmarks: Two corners and one pupil for each eye.</li>
</ul>

<h4>MPIIFaceGaze Dataset:</h4>
<ul>
  <li>Total 213,659 images 15 participants, every 10 mins collected 20 random gaze points.</li>
  <li>Selected Images: 1,037 - 10 images from 7 days of 15 users.</li>
  <li>Resolution: 720, 1280 - reduced to half in project.</li>
  <li>7 Landmarks: Gaze point on screen, two corners of each eye, two corners of lips.</li>
</ul>

<h4>Best Results of Transfer Learning on MPIIFaceGaze Dataset:</h4>
<table>
  <tr>
    <th>Metrics</th>
    <th>Train</th>
    <th>Validation</th>
    <th>Test</th>
  </tr>
  <tr>
    <td>r2_score</td>
    <td>0.9640</td>
    <td>0.8174</td>
    <td>0.8071</td>
  </tr>
  <tr>
    <td>MeanSquareLoss</td>
    <td>1080.1866</td>
    <td>3328.8447</td>
    <td>3663.0830</td>
  </tr>
</table>

<h4>Loss Plot:</h4>
<img width=850 src="https://github.com/OmerFarooq246/Eye-Detection-and-Localization-in-Web-Cam-images/assets/110720771/191baa34-1b8a-40f5-8daf-a4dc5ece6d3f">

<p><b>Transfer Learning - Xavier initialization</b> in the notebook displays the best results.</p>

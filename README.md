# How it works
![Alt text](https://img.youtube.com/vi/ihEWYwGL_jQ/0.jpg)](https://www.youtube.com/watch?v=ihEWYwGL_jQ&feature=youtu.be)
# CHATBOT-Cough detection and automated response

## RNN noise reduction 
![alt text](https://github.com/kishorkuttan/Covid-19-chatbot-using-IBM-cloud-and-deep-learning/blob/master/rnn_noise_reduction.png?raw=true)

* Ref: https://github.com/xiph/rnnoise
* Ref: https://github.com/cpuimage/rnnoise
* Ref: https://blog.csdn.net/dakeboy/article/details/88039977


## build librnnoise & rnnoise_demo with CMake

```
mkdir build
cd build
cmake ..
make
```

copy the file "rnnoise_demo" from "/build/bin/" to the main directory

download the weight file from https://drive.google.com/file/d/1BV2OSIuuwg6hx-22Q1ApayeWlf45AhmO/view?usp=sharing
and move it the "models" directory
## Edit the IBM credentials

1. Find the Assistant service in your IBM Cloud Dashboard Services.
2. Click on your Watson Assistant service and then click on Launch Watson Assistant.
3. Use the left sidebar and click on Assistants. Create an assistant.
4. Select the Dialog skill card and click Next.
5. Select the Import skill tab.
6. Click the Choose JSON File button and choose the data/covid_ai_chatbot_skill.json file in your cloned repo.
7. Click import
8. Go back to the Skills page (use the left sidebar).
9. Look for the created skill.
10. Click on the three dots in the upper right-hand corner of the card and select View API Details.
Copy the skill ID(workspace id). Go to your assitant click on the three dots in the upper right-hand corner and select settings and open API details note down the Assistant id( for android application ), assistant URL Save it for the next step.
11. Go to IBM functions and create an action with python 3.7 
12. Open function_action.py and copy-paste it in the Code section. Click on Parameters and add Parameter with Parameter name as "link" and Parameter Value as " https://api.covid19india.org/state_district_wise.json ".
13.
```
cp sample.env .env
```


## install anaconda python
```
conda create -n sound pip python=3.6
conda activate sound
pip install -r requirements.txt
```

## Run

```
python detail_live.py
```
## Principle
* CONVOLUTIONAL NEURAL NETWORK(CNN) WITH KERAS USING TENSORFLOW BACKEND

1. Collected sound data: https://voice.mozilla.org/en/datasets, https://urbansounddataset.weebly.com/urbansound8k.html, https://github.com/hernanmd/COVID-19-train-audio/tree/master/not-covid19-coughs

2. Used transfer learning on the VGG-16 architecture Pre-trained on YouTube-8M for audio recognition

3. Save the keras model and used for real-time prediction

# CHATBOT - Flask
![alt text](https://github.com/kishorkuttan/Covid-19-chatbot-using-IBM-cloud-and-deep-learning/blob/master/flask_chatbot.png?raw=true)

```
python app.py
```
and go to 127.0.0.1:1880 from your browser

# CHATBOT-Node-Red
![alt text](https://github.com/kishorkuttan/Covid-19-chatbot-using-IBM-cloud-and-deep-learning/blob/master/node-red.png?raw=true)

follow this tutorial https://developer.ibm.com/tutorials/create-a-voice-enabled-covid-19-chatbot-using-node-red/
and import flows.json from folder "node-red app"

# CHATBOT-Android application
![alt text](https://github.com/kishorkuttan/Covid-19-chatbot-using-IBM-cloud-and-deep-learning/blob/master/Android_demo_app.jpg?raw=true)

## Install app-debug.apk

# Integrating with Automation Anywhere
![alt text](https://github.com/kishorkuttan/Employees-health-check-chatbot-using-IBM-Watson-Automation-Anywhere-and-AI-/blob/master/Screenshot from 2020-06-04 11-08-33.png?raw=true)

Combine the result from the app/program interface(Many of the health queries & results can be pushed to our API) and upload it to a RESTful API endpoint. We can call the end point in our AA and do rest of the automation like health analysis.

# ROS-ChatBot

## Project Overview
The user can interact with AIML either by text chatting or speech. The speech recognition node will not do speech recognition. Instead, it will receive the converted text from a speech recognition system and input it to the AIML server.  


## Project Structure

### aiml_server
This ROS node loads AIML files from the database and saves them into brain files. It subscribes to ```/chatter```(std_msgs/String) topic. The string data from the ```/chatter``` topic is the input of the AIML interpreter. The response from the AIML interpreter is published through the ```/response``` (std_msgs/String) topic.

### aiml_client
This ROS node waits for user input and once the node gets the input, it will publish it to the ```/chatter``` topic 

### aiml_tts_client
The AIML server publishes the response to the ```/response``` topic. The ```tts``` client node will subscribe to this topic and convert it to speech.

### aiml_speech_recognition_client
This node will subscribe to the output from the speech recognition system and publish it to the ```/chatter``` topic.

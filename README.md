# Agentic_Ai
# Description
The Travel Planner Agent is an AI-powered assistant designed to simplify and personalize the process of travel planning. Built using IBM Cloud Lite and IBM Granite foundation models, it helps users discover destinations, create customized itineraries, and receive intelligent recommendations for transport, accommodation, and activities. By understanding user preferences, budget, and travel constraints, the agent generates real-time, optimized travel plans. It also integrates weather updates, local insights, and smart alerts to ensure a smooth and enjoyable travel experience from start to finish.
import requests

# Tech 
1. IBM Cloud Lite

2. IBM Cloud Watsonx AI Studio

3. IBM Cloud Watsonx AI runtime

4. IBM Granite Foundation Models

   
# Code Snippet
# NOTE: you must manually set API_KEY below using information retrieved from your IBM Cloud account (https://dataplatform.cloud.ibm.com/docs/content/wsj/analyze-data/ml-authentication.html?context=wx)
API_KEY = "<your API key>"
token_response = requests.post('https://iam.cloud.ibm.com/identity/token', data={"apikey": API_KEY, "grant_type": 'urn:ibm:params:oauth:grant-type:apikey'})
mltoken = token_response.json()["access_token"]

header = {'Content-Type': 'application/json', 'Authorization': 'Bearer ' + mltoken}

# NOTE:  manually define and pass the array(s) of values to be scored in the next line
payload_scoring = {"messages":[{"content":"","role":""}]}

response_scoring = requests.post('https://us-south.ml.cloud.ibm.com/ml/v4/deployments/ab068d3b-461e-43a6-baa5-1726b021518e/ai_service_stream?version=2021-05-01', json=payload_scoring,
 headers={'Authorization': 'Bearer ' + mltoken})

print("Scoring response")
try:
    print(response_scoring.json())
    
except ValueError:
    print(response_scoring.text)
except Exception as e:
    print(f"An unexpected error occurred: {e}")

    
![travel2](https://github.com/user-attachments/assets/80cf8808-5ffc-47d7-a53c-fc36889c2c9f)
![WhatsApp Image 2025-08-02 at 23 50 17_5469ff9d](https://github.com/user-attachments/assets/b61d59a2-4086-4a89-8116-758177e8d852)
![WhatsApp Image 2025-08-02 at 23 25 06_034859af](https://github.com/user-attachments/assets/ff459290-312b-4c4a-ae10-5dd8f01f31db)
<img width="1776" height="842" alt="image" src="https://github.com/user-attachments/assets/881fd526-1579-4065-953d-600a1dd42710" />





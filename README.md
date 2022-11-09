# AI5_Arcon_ASL_Menu
### AI5 Group6 Project - Arcon ASL Menu

### Problem Definition- <br>
The basic ideology behind this project was to make any customer-based utility service more friendly for the people who are disabled (deaf and mute specifically)
Since they are taught sign – language as an alternative to the standard way of interacting with others to overcome the barriers of communication, a lot of them face problems in the day–to–day life like ordering food at a “Drive-thru” or having a conversation with an attendant who is oblivious to their predicament and whose incompetence might be a bit irritating for the person who is disabled.

### Proposed Solution: ARCON ASL MENU APP<br>
Upload an ASL gesture and the app will identify it and recommend you the food to be ordered (For eg. if a person wants to have a burger, he can upload the image of 'B' gesture in ASL language and the app would show predicted alphabet as well as the food suggested) in order to help both the customer and the retailer to have a better engagement whilst having a conversation.

### Solution Architecture-
<img width="950" alt="image" src="https://user-images.githubusercontent.com/70897069/200838915-ef7b321b-ce7d-4f9b-b7c7-f0be3cefdc6e.png">

### Technical Architecture-
<img width="950" alt="image" src="https://user-images.githubusercontent.com/70897069/200819980-3502e1d1-1b2f-4f3c-80df-30961b308c26.png">

### Implementation Details-
Setup 2 containers - <br>
1. api-service container
3. frontend-simple container

<b> Implemented Container Architecture </b>

![image](https://user-images.githubusercontent.com/70897069/200830289-d41fae8f-2f64-477d-bfc4-ea6e94677bb4.png)

<b>1. API Service Container:<br></b>
Exposes port 9000 from the container to the outside for the api server. It
<ul>
  <li> Downloads the best model from GCP bucket using the json file in secrets folder and stores it in the persistent_folder.</li>
  <li> Uses the best model to predict the ASL gesture of the input image (image uploaded by the user).</li>
</ul>

<b>API Service Container running locally at http://localhost:9000/docs</b>

<img width="960" alt="API_Server_Local_9000" src="https://user-images.githubusercontent.com/70897069/200832231-382d07e5-94dd-401f-925b-ad5070a94031.png">

Trying out predict, uploading image of 'B' ASL gesture to get the prediction label:

<img width="960" alt="API_Server_Local_9000_Predict" src="https://user-images.githubusercontent.com/70897069/200833278-8db2a5ed-321f-48c7-946c-3588ffb003dd.png">

<b>2. Frontend App Container:<br></b>
Simple frontend app that uses basic HTML & Javascript. Exposes port 8080 from the container to the outside for the web server.


<b>Frontend App Container (Predict Page) running locally at http://localhost:8080/predict.html</b><br>
When 'VIEW MENU' button on predict.html page is clicked, it takes to menu.html page for user to have a look at menu.

<img width="960" alt="Frontend_predict" src="https://user-images.githubusercontent.com/70897069/200834767-aeb78aa6-f53c-4825-a7c1-4e49ed958bac.png">



<b>Frontend App Container (Menu Page) running locally at http://localhost:8080/menu.html</b><br>
When 'Order Now!' button on menu.html page is clicked, it takes to predict.html page for user to upload ASL gesture and get the prediction and suggeted food.

<img width="960" alt="Frontend_menu" src="https://user-images.githubusercontent.com/70897069/200834853-2c19862b-e414-4280-bbfe-5084412c0fc8.png">


<b> Prediction Example ON 'B' ASL gesture image</b>
  
<img width="960" alt="Frontend_prediction_B" src="https://user-images.githubusercontent.com/70897069/200834915-50305de7-b87d-418e-a880-2ddbcabfef5d.png">


  
  

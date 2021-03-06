# Restaurant Chat Bot

Purpose of this project is to build a conversational chatbot for a food startup
FOODIE(Assumption).

The main purpose of the bot is to help users discover restaurants quickly and
efficiently and to provide a good restaurant discovery experience.

## Notes:
- Foodie works only in Tier 1 and Tier 2 cities in India.
- It provides only following cuisine preferences - Chinese, American, Italian,
  South Indian and North Indian.
- It offers budget in 3 categories:
    - Lesser than Rs. 300
    - Rs. 300 to 700
    - More than 700
- In the chat window, it displays top 5 restaurants found in a location
  asked by users. In sorted order on a scale of 1-5, 5 being the highest.
- It sends top 10 restaurants over email.


## Technical
### Operating System:
This project is built on Mac OSX development environment, if you are using
Mac OSX for testing, it should work directly. If in case did not work, please
retrain the module by running the command - rasa train.

For Windows, make sure requirement.txt matches and train the module.

## What’s inside this Restaurant Chat Bot Project?

This project contains training data and the main files needed to build/run
an restaurant bot on your machine.

The `restaurant-chatbot` consists of the following files:

- **custom** Contains all the logic required to achieve as per the specification.
    - fetch_restaurant.py: It has logic on fetching restaurants details from
      Zomato API based of location, cuisine, rating and minimum and maximum amount
      provided by users and returns top restaurants in a sorted order (descending)
      on an average Zomato user rating (on a scale of 1-5, 5 being the highest)

    - verify_location.py: It verifies if the location entered by the user is part
      of Tier 1 and Tier 2 cities and if it is being served by Zomato.

    - send_email.py: It manages generating html data and sending top 10 restaurants
      details to user if requested.

    - email_template.j2 - Jinja2 template for generating html data, rendered by
      email function in send_email code.

    - locations.txt: Contains names of all Tier 1 and Tier 2 cities.

    - zomatopy.py: Contains all Zomato api functions to fetch restaurants data.

- **data/nlu.md** contains training examples for the NLU model  
- **data/stories.md** contains training stories for the Core model  
- **actions.py** contains some custom actions
- **config.yml** contains the model configuration
- **domain.yml** contains the domain of the assistant  
- **endpoints.yml** contains the webhook configuration for the custom action  
- **policy.py** contains a custom policy


## How to use this project?

Make sure to install all required packages mentioned in requirement.txt

Refer the below path to setup Rasa:
[Setup](https://github.com/raviboodher/Restaurant-Chatbot/blob/master/installation-notes.txt).

To train your restaurant bot, execute
```
rasa train
```
This will store a zipped model file in `models/`.


You can start an action server with following command
```
rasa run actions

```

To chat with the bot on the command line, run
```
rasa shell
```
For more information about the individual commands, please check out.
[documentation](http://rasa.com/docs/rasa/user-guide/command-line-interface/).

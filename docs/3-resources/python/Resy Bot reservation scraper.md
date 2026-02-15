[[python]]
[[bots]]
[[resy reservations]]


https://www.toolpioneers.com/post/restaurant-reservation-automation-bot-retool-workflows

Restaurant Reservation Automation Bot with Retool Workflows for a Concierge Services Company

A white glove service company was tired of manually reserving tables for a large base of customers at the best fine dining restaurants in the United States. We built a game changing solution for them: an automated bot that books restaurant reservations using Retool and the RESY API. Let's dive into how it works.

![[Pasted image 20260215065715.png]]

### Step 1: Obtaining the RESY API Key

  

To start, you need an API key from RESY. This requires creating an account on RESY. Once logged in, open the console log, interact with any API endpoint, and locate the authorization header. Here, you'll find your much-needed API key.

  

## Step 2: User Input Collection

  

User preferences are gathered through an Excel sheet. This includes:

- Party size
    
- Desired day
    
- Venue ID
    
- Preferred time (preferred time within specified time interval)
    
- Minimum time slot (starting of the specified time interval)
    
- Maximum time slot (ending of the specified time interval)
    

Latitude and longitude are set as default parameters (0,0).

  

  

## Step 3: Time Preferences

  

Users indicate their minimum and maximum time slots, representing the range within which they wish to book a table. The "preferred time" is the specific time slot desired within this range. If the preferred time isn't available, the bot selects the next available slot within the specified interval.

  

## Step 4: The Cron Job

  

The bot operates on a cron job set to run every five minutes. It retrieves user inputs from the Excel sheet and starts processing.

  

## Step 5: Fetch Venue Details

  

A GET request fetches venue details, yielding multiple config IDs. These IDs represent different reservation time slots, which are parsed using regex.

  

![](https://static.wixstatic.com/media/cc867e_665a1edf67824529aa0ab46b3f9577ff~mv2.jpg/v1/fill/w_1430,h_790,al_c,q_85,usm_0.66_1.00_0.01,enc_avif,quality_auto/cc867e_665a1edf67824529aa0ab46b3f9577ff~mv2.jpg)

  

## Step 6: Filtering Time Slots

  

A JavaScript query block filters all available reservation slots, matching them with user-defined minimum and maximum times. It then returns the config ID for the slot closest to the preferred time.

  

![](https://static.wixstatic.com/media/cc867e_475bc04c519441aabdca39e69c7abbce~mv2.jpg/v1/fill/w_1430,h_788,al_c,q_85,usm_0.66_1.00_0.01,enc_avif,quality_auto/cc867e_475bc04c519441aabdca39e69c7abbce~mv2.jpg)

  

## Step 7: Booking Process

  

Upon obtaining the correct config ID, the bot hits a new endpoint to fetch a booking token. This token is essential for the next step.

  

## Step 8: Making the Reservation

  

The bot sends a POST request as form data, carrying the booking token and other necessary data. This step either confirms or denies the reservation.  

![](https://static.wixstatic.com/media/cc867e_111b912108004b74a4d62ed5a50cb0b6~mv2.jpg/v1/fill/w_1430,h_732,al_c,q_85,usm_0.66_1.00_0.01,enc_avif,quality_auto/cc867e_111b912108004b74a4d62ed5a50cb0b6~mv2.jpg)

  

## Step 9: Updating the Excel Sheet

If the reservation is successful, the bot updates the Excel sheet, and the cron job for the particular reservation request stops, while reservation requests for other clients happen parallelly.  

## **Conclusion**

  

This automation bot built using Retool workflows, significantly streamlines the process of making restaurant reservations. By efficiently handling user preferences and navigating through the RESY API, it ensures a hassle-free booking experience. Perfect for those who love dining out but dislike the tedious reservation process!  

Remember, this bot is a sophisticated tool that requires some technical know-how, especially in terms of API interaction and cron job setup. Nonetheless, its efficiency and effectiveness make it a valuable asset for regular diners and restaurant enthusiasts alike
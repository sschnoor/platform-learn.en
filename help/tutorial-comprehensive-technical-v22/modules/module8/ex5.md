---
title: Adobe Journey Optimizer - External Weather API, SMS Action & more - Design a trigger-based Customer Journey
description: Adobe Journey Optimizer - External Weather API, SMS Action & more - Design a trigger-based Customer Journey
kt: 5342
audience: Data Engineer, Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
exl-id: 46aa9a27-ec2e-4118-ac12-0bc44c5e0ad2
---
# 8.5 Design a trigger-based journey

In this exercise, you'll create a journey by making use of Adobe Journey Optimizer.

Login to Adobe Journey Optimizer by going to [Adobe Experience Cloud](https://experience.adobe.com). Click **Journey Optimizer**.

![ACOP](../module7/images/acophome.png)

You'll be redirected to the **Home**  view in Journey Optimizer. First, make sure you're using the correct sandbox. The sandbox to use is called `--aepSandboxId--`. To change from one sandbox to another, click on **PRODUCTION Prod (VA7)** and select the sandbox from the list. In this example, the sandbox is named **AEP Enablement FY22**. You'll then be in the **Home** view of your sandbox `--aepSandboxId--`.

![ACOP](../module7/images/acoptriglp.png)

In the left menu, go to **Journeys** and click **Create Journey** to start creating your Journey.

![Demo](./images/jocreate.png)

You should first name your journey.

As a Name for the journey, use `--demoProfileLdap-- - Geofence Entry Journey`. In this example, the journey name is `vangeluw - Geofence Entry Journey`. No other values must be set at this moment. Click **OK**.

![Demo](./images/joname.png)

On the left side of your screen, have a look at **Events**. You should see your previously created event in that list. Select it, then drag and drop it on the journey canvas. Your journey then looks like this:

![Demo](./images/joevents.png)

Next, click on **Orchestration**. You now see the available **Orchestration** capabilities. Select **Condition**, then drag and drop it on the Journey Canvas.

![Demo](./images/jo2.png)

You now have to define three conditions:

- It's colder than 10° Celsius
- It's between 10° and 25° Celsius
- It's warmer than 25° Celsius

Let's define the first condition.

## Condition 1: Colder than 10° Celsius

Click on the **Condition**.  Click on **Path1** and edit the name of the path to **Colder than 10 C**. Click on the **Edit** icon for the expression of Path1.

![Demo](./images/jo5.png)

You'll then see an empty **Simple Editor** screen. Your query will be a bit more advanced, so you'll need the **Advanced Mode**. Click **Advanced Mode**.

![Demo](./images/jo7.png)

You'll then see the **Advanced Editor** which allows code entry.

![Demo](./images/jo9.png)

Select the below code and paste it in the **Advanced Editor**.

`#{--demoProfileLdap--WeatherApi.--demoProfileLdap--WeatherByCity.main.temp} <= 10`

You'll then see this.

![Demo](./images/jo10.png)

In order to retrieve the temperature as part of this condition, you need to provide the city in which the customer currently is.
The **City** needs to be linked to the dynamic parameter `q`, just like we saw previously in the Open Weather API Documentation.

Click the field **dynamic val: q** as indicated in the screenshot.

![Demo](./images/jo11.png)

You then need to find the field that contains the current city of the customer in one of the available Data Sources.

![Demo](./images/jo12.png)

You can find the field by navigating to `--demoProfileLdap--GeofenceEntry.placeContext.geo.city`.

By clicking that field, it will be added as the dynamic value for the parameter `q`. This field will be populated by for instance the geolocation-service that you've implemented in your mobile app. In our case we will simulate this with the admin console of the demo website. Click **OK**.

![Demo](./images/jo13.png)

## Condition 2: Between 10° and 25° Celsius

After having added the first condition, you'll see this screen. Click **Add Path**.

![Demo](./images/joc2.png)

Double click on **Path1** and edit the path name to **Between 10 and 25 C**. Click the **Edit** icon for the expression this path.

![Demo](./images/joc6.png)

You'll then see an empty **Simple Editor** screen. Your query will be a bit more advanced, so you'll need the **Advanced Mode**. Click **Advanced Mode**.

![Demo](./images/jo7.png)

You'll then see the **Advanced Editor** which allows code entry.

![Demo](./images/jo9.png)

Select the below code and paste it in the **Advanced Editor**.

`#{--demoProfileLdap--WeatherApi.--demoProfileLdap--WeatherByCity.main.temp} > 10 and #{--demoProfileLdap--WeatherApi.--demoProfileLdap--WeatherByCity.main.temp} <= 25`

You'll then see this.

![Demo](./images/joc10.png)

In order to retrieve the temperature as part of this Condition, you need to provide the city in which the customer currently is.
The **City** needs to be linked to the dynamic parameter **q**, just like we saw previously in the Open Weather API Documentation.

Click the field **dynamic val: q** as indicated in the screenshot.

![Demo](./images/joc11.png)

You then need to find the field that contains the current city of the customer in one of the available Data Sources.

![Demo](./images/jo12.png)

You can find the field by navigating to `--demoProfileLdap--GeofenceEntry.placeContext.geo.city`. By clicking that field, it will be added as the dynamic value for the parameter **q**. This field will be populated by for instance the geolocation-service that you've implemented in your mobile app. In our case we will simulate this with the admin console of the demo website. Click **OK**.

![Demo](./images/jo13.png)

Next, you'll add the 3rd condition.

## Condition 3: Warmer than 25° Celsius

After having added the second condition, you'll see this screen. Click **Add Path**.

![Demo](./images/joct2.png)

Double click on Path1 to change the name to **Warmer than 25 C**. 
Then click on the **Edit** icon for the expression this path.

![Demo](./images/joct6.png)

You'll then see an empty **Simple Editor** screen. Your query will be a bit more advanced, so you'll need the **Advanced Mode**. Click **Advanced Mode**.

![Demo](./images/jo7.png)

You'll then see the **Advanced Editor** which allows code entry.

![Demo](./images/jo9.png)

Select the below code and paste it in the **Advanced Editor**.

`#{--demoProfileLdap--WeatherApi.--demoProfileLdap--WeatherByCity.main.temp} > 25`

You'll then see this.

![Demo](./images/joct10.png)

In order to retrieve the temperature as part of this Condition, you need to provide the city in which the customer currently is.
The **City** needs to be linked to the dynamic parameter **q**, just like we saw previously in the Open Weather API Documentation.

Click the field **dynamic val: q** as indicated in the screenshot.

![Demo](./images/joct11.png)

You then need to find the field that contains the current city of the customer in one of the available Data Sources.

![Demo](./images/jo12.png)

You can find the field by navigating to ```--demoProfileLdap--GeofenceEntry.placeContext.geo.city```. By clicking that field, it will be added as the dynamic value for the parameter **q**. This field will be populated by for instance the geolocation-service that you've implemented in your mobile app. In our case we will simulate this with the admin console of the demo website. Click **OK**.

![Demo](./images/jo13.png)

You now have three configured paths. Click **Ok**.

![Demo](./images/jo3path.png)

As this is a journey for learning purpose, we'll now configure a couple of actions to showcase the variety of options marketeers now have to deliver messages.

## Send messages for path Colder than 10° Celsius

For each of the temperature contexts, we'll attempt to send an SMS Message to our customer. We can only send an SMS if we have a Mobile Number available for a customer, so we'll first have to verify that we do.

Let's focus on **Colder than 10 C**.

![Demo](./images/p1steps.png)

Let's take another **Condition** element and drag it as indicated in the screenshot below. We'll verify if for this customer, we have a mobile number available.

![Demo](./images/joa1.png)

As this is just an example, we are only configuring the option where the customer has a mobile number available. Add a label of **Has mobile?**.

Click on the **Edit** icon for the Expression for the **Path1** path.

![Demo](./images/joa2.png)

In the Data Sources shown on the left, navigate to **ExperiencePlatform.ProfileFieldGroup.profile.mobilePhone.number**. You're now reading the mobile phone number directly from Adobe Experience Platform's Real-time Customer Profile.

![Demo](./images/joa3.png)

Select the field **Number**, then drag and drop it to the Condition Canvas.

Select the operator **is not empty**. Click **Ok**.

![Demo](./images/joa4.png)

You'll then see this. Click **OK** again.

![Demo](./images/joa6.png)

Your journey will then look like this. Click on **Actions** as indicated in the screenshot.

![Demo](./images/joa8.png)

Select the action **Message**, then drag and drop it after the condition you just added.

![Demo](./images/joa9.png)

Click the **Edit** icon to select your message.

![Demo](./images/joa10.png)

You'll then see this. Select the message `--demoProfileLdap-- - Weather <10` and click **Select**.

![Demo](./images/joa10a.png)

You'll now see your completed action. Click **Ok**.

![Demo](./images/joa17.png)

In the left menu, go back to **Actions**, select the Action `--demoProfileLdap--TextSlack`, then drag and drop it after the **Message** action.

![Demo](./images/joa18.png)

Go to **Action Parameters** and click the **Edit** icon for the parameter `TEXTTOSLACK`.

![Demo](./images/joa19.png)

In the popup-window, click **Advanced Mode**.

![Demo](./images/joa20.png)

Select the below code, copy it and paste it in the **Advanced Mode Editor**. Click **Ok**.

`"Brrrr..." + #{ExperiencePlatform.ProfileFieldGroup.profile.person.name.firstName} + " It's freezing. 20% discount on Jackets today!"`

![Demo](./images/joa21.png)

You will see your completed action. Click **Ok**.

![Demo](./images/joa22.png)

In the left menu, go to **Orchestration**, select **End**, then drag and drop **End** after the `--demoProfileLdap--TextSlack` action.

![Demo](./images/joa23.png)

## Send messages for path Between 10° and 25° Celsius

For each of the temperature contexts, we'll attempt to send an SMS Message to our customer. We can only send an SMS if we have a mobile number available for a customer, so we'll first have to verify that we do.

Let's focus on **Between 10 and 25 C** path.

![Demo](./images/p2steps.png)

Let's take another **Condition** element and drag it as indicated in the screenshot above. We'll verify if for this customer, we have a mobile number available.

![Demo](./images/jop1.png)

As this is just an example, we are only configuring the option where the customer has a mobile number available. Add a label of **Has mobile?**.

Click on the **Edit** icon for the Expression for the **Path1** path.

![Demo](./images/joa2p2.png)

In the Data Sources shown on the left, navigate to **ExperiencePlatform.ProfileFieldGroup.profile.mobilePhone.number**. You're now reading the mobile phone number directly from Adobe Experience Platform's Real-time Customer Profile.

![Demo](./images/joa3.png)

Select the field **Number**, then drag and drop it to the Condition Canvas.

Select the operator **is not empty**. Click **Ok**.

![Demo](./images/joa4.png)

You'll then see this. Click **Ok**.

![Demo](./images/joa6.png)

Your journey will then look like this. Click on **Actions** as indicated in the screenshot.

![Demo](./images/jop8.png)

Select the action **Message**, then drag and drop it after the condition you just added.

![Demo](./images/jop9.png)

Click the **Edit** icon to select your message.

![Demo](./images/jop10.png)

You'll then see this. Select the message `--demoProfileLdap-- - Weather 10-25` and click **Select**.

![Demo](./images/jop10a.png)

You'll now see your completed action. Click **Ok**.

![Demo](./images/jop17.png)

In the left menu, go back to **Actions**, select the Action `--demoProfileLdap--TextSlack`, then drag and drop it after the **Message** action.

![Demo](./images/jop18.png)

Go to **Action Parameters** and click the **Edit** icon for the parameter `TEXTTOSLACK`.

![Demo](./images/joa19.png)

In the popup-window, click **Advanced Mode**.

![Demo](./images/joa20.png)

Select the below code, copy it and paste it in the **Advanced Mode Editor**. Click **Ok**.

`"What nice weather for the time of year, " + #{ExperiencePlatform.ProfileFieldGroup.profile.person.name.firstName} + " 20% discount on Sweaters today!"`

![Demo](./images/jop21.png)

You will see your completed action. CLick **Ok**.

![Demo](./images/jop22.png)

In the left menu, go to **Orchestration**, select **End**, then drag and drop **End** after the `--demoProfileLdap--TextSlack` action.

![Demo](./images/jop23.png)

## Send messages for path Warmer than 25° Celsius

For each of the temperature contexts, we'll attempt to send an SMS Message to our customer. We can only send an SMS if we have a Mobile Number available for a customer, so we'll first have to verify that we do.

Let's focus on **Warmer than 25 C** path.

![Demo](./images/p3steps.png)

Let's take another **Condition** element and drag it as indicated in the screenshot above. You'll verify if for this customer, you have a mobile number available.

![Demo](./images/jod1.png)

As this is just an example, we are only configuring the option where the customer has a mobile number available. Add a label of **Has mobile?**.

Click on the **Edit** icon for the Expression for the **Path1** path.

![Demo](./images/joa2p3.png)

In the Data Sources shown on the left, navigate to **ExperiencePlatform.ProfileFieldGroup.profile.mobilePhone.number**. You're now reading the mobile phone number directly from Adobe Experience Platform's Real-time Customer Profile.

![Demo](./images/joa3.png)

Select the field **Number**, then drag and drop it to the Condition Canvas.

Select the operator **is not empty**. Click **Ok**.

![Demo](./images/joa4.png)

You'll then see this. Click **OK**.

![Demo](./images/joa6.png)

Your journey will then look like this. Click on **Actions** as indicated in the screenshot.

![Demo](./images/jod8.png)

Select the action **Message**, then drag and drop it after the condition you just added.

![Demo](./images/jod9.png)

Click the **Edit** icon to select your message.

![Demo](./images/jod10.png)

You'll then see this. Select the message `--demoProfileLdap-- - Weather >25` and click **Select**.

![Demo](./images/jod10a.png)

You'll now see your completed action. Click **Ok**.

![Demo](./images/jod17.png)

In the left menu, go back to **Actions**, select the Action `--demoProfileLdap--TextSlack`, then drag and drop it after the **Messages** action.

![Demo](./images/jod18.png)

Go to **Action Parameters** and click the **Edit** icon for the parameter `TEXTTOSLACK`.

![Demo](./images/joa19.png)

In the popup-window, click **Advanced Mode**.

![Demo](./images/joa20.png)

Select the below code, copy it and paste it in the **Advanced Mode Editor**. Click **Ok**.

`"So warm, " + #{ExperiencePlatform.ProfileFieldGroup.profile.person.name.firstName} + "! 20% discount on swimwear today!"`

![Demo](./images/jod21.png)

You will see your completed action. Click **Ok**.

![Demo](./images/jod22.png)

In the left menu, go to **Orchestration**, select **End**, then drag and drop **End** after the `--demoProfileLdap--TextSlack` action.

![Demo](./images/jod23.png)

Your journey is now fully configured. Click **Publish**.

![Demo](./images/jodone.png)

Click **Publish** again.

![Demo](./images/jopublish1.png)

Your journey is now published.

![Demo](./images/jopublish2.png)

In the next exercise, you'll be able to test your Journey.

Next Step: [8.6 Update your Data Collection property and test your Journey](./ex6.md)

[Go Back to Module 8](journey-orchestration-external-weather-api-sms.md)

[Go Back to All Modules](../../overview.md)

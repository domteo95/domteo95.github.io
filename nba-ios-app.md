---
theme: jekyll-theme-minimal
layout: default
title: "NBA Players iOS app "
permalink: /nba-ios-app/
---
# iOS Mobile App NBA Players Project using Xcode and Swift 

![](https://img.shields.io/badge/swift-6.0-red)
![](https://img.shields.io/badge/platform-iOS-gray)
![](https://img.shields.io/badge/Xcode-12-green)
![](https://img.shields.io/badge/License-MIT-blue.svg)

More detailed overview and run through of how to use this app and its various features can be found in this YouTube [video](https://www.youtube.com/watch?v=xEQHiAIzgE8). 


## Overview of Project

I made this iOS app as a huge fan of basketball and the NBA as well as a past participant in numerous fantasy basketball leagues. At times, I would be curious about the stats of various NBA players but with the exception of searching it on Google, for example 'Lebron James stats', it was rather troublesome to use the ESPN, NBA or fantasy app to search for simple information. Furthermore, these apps and websites often provide too much information which can be overwhelming. 

This app is made for casual NBA fans as well as a complementary app to current fantasy Basketball apps in allowing players to search for NBA players' key statistics and to keep track of certain players. 

<p align="center">
  <img src="/assets/img/nba-ios/overview.gif" width="60%" height="60%" />
</p>

**Instructions on how to run the app:** download the entire `app` folder and open it in Xcode. Select the device (eg iPhone 11 Pro Max) and run it by clicking the play button and you'll be able to play around with the app on the simulator. 


## Features 
As can be seen in the storyboard picture below, there's 3 main scenes which are also represented in the 3 tabs found at the bottom of the app - **NBA Players**, **Favorite Players** and **Injured Players**. Each tab should also have their own icon above the title of the tab and clicking on it will allow the user to switch between the different use cases as will be explained.

<p align="center">
  <img src="/assets/img/nba-ios/storyboard.png" style="width: 75%; height: 75%"/>
</p>

### NBA Players
The following are a list of features that users can enjoy under the 'NBA Players' tab. 

* Should have hundreds of different NBA players listed in rows, provided by an external API
* Each cell should contain the Player's name and Team's name as well as the player's image. If the image is not there, it means that the player is very new to the NBA and has yet to take their picture. 
* When swiping from right to left, users should be able to see a yellow star appear, when users can click on the yellow star to indicate that they want that specific player to appear on their Favorite Player's List. 

<p align="center">
  <img src="/assets/img/nba-ios/yellow-star.png" style="width: 75%; height: 75%"/>
</p>

* When swiping from left to right, users should be able to see a white cross on a red background appear, when users can click on the cross to indicate that they want that specific player to appear on their Injured Player's List. 

<p align="center">
  <img src="/assets/img/nba-ios/red-cross.png" style="width: 75%; height: 75%"/>
</p>

* Clicking on any player's cell should bring you to the detail view which contains their image and statistics - points, rebounds and assists per game. 

<p align="center">
  <img src="/assets/img/nba-ios/detail-view.png" style="width: 75%; height: 75%"/>
</p>


* Clicking on the top right bar button button should allow users to change the sorting from name to points per game or vice versa. The text on the button should be opposite of what it's currently being sorted by. 

<p align="center">
  <img src="/assets/img/nba-ios/points.png" style="width: 75%; height: 75%"/>
</p>


### Search Bar
Using the search bar function found at the top of the screen in the 'NBA Players' tab.

* Should be able to search for a player's name or team name and the list will be updated to reflect the results. 
* There should be a scope right underneath the search bar where users can select one of the following options, "Both", "Player's Name" or "Team's Name". The default option is "Both". The search result will then change according to which option was selected.

<p align="center">
  <img src="/assets/img/nba-ios/search-player.png" style="width: 75%; height: 75%""/>
</p>

*Search by Players' Name*

<p align="center">
  <img src="/assets/img/nba-ios/search-team.png" style="width: 75%; height: 75%"/>
</p>

*Search by Teams' Name*

### Favorite Players
* If user has swiped from right to left and clicked on the yellow star, that player should appear in the 'Favorite Players' tab with their name and team name. 

<p align="center">
  <img src="/assets/img/nba-ios/favorite-players.png" style="width: 75%; height: 75%"/>
</p>

* Clicking on one of the players in this list should lead you to another detail view, this time with more stats. Includes points, rebounds, assists, steals, blocks, minutes per game and player efficiency rating along with their picture. 

<p align="center">
  <img src="/assets/img/nba-ios/favorite-players-detail.png" style="width: 75%; height: 75%"/>
</p>

* Players in the Favorite Players list should be a Core Data entity, which means that even after reloading the app, the players that appeared on this list should continue to be on this list. 
* Swiping from right to left should allow users the option to delete that specific player from their Favorite Players list. 

<p align="center">
  <img src="/assets/img/nba-ios/favorite-players-delete.png" style="width: 75%; height: 75%"/>
</p>

### Injured Players
* If user has swiped from left to right and clicked on the white cross on red background, that player should appear in the 'Injured Players' tab with their name as well as the date that they were added to this list. 

<p align="center">
  <img src="/assets/img/nba-ios/injured-players.png" style="width: 75%; height: 75%"/>
</p>

* Players in this list are also a Core Data entity hence should have same properties as the players in the Favorite Players list. 
* Swiping from right to left should allow users the option to delete that specific player from their Injured Players list.

